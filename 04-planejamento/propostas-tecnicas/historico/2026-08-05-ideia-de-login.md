# Ideia de login — autenticação do Agiliza (CPF + Sanctum + RLS)

> **Status:** proposta de desenho para discussão (2026-08-05). Não é diretriz de implementação
> aprovada — é o registro da ideia de login para alinhar com o time de backend e com a ATI.
> Nada de código/protótipo foi alterado.

## Contexto

Hoje o Agiliza é **só front-end** (Next.js), com autenticação **simulada em memória**
(`SessionProvider` reseta ao recarregar). O backend da STC (**Laravel + PostgreSQL**) ainda
será construído, e esta é a primeira decisão de arquitetura "de verdade": **como fazer o login**.

Direção desta ideia:
- **Identificador primário = CPF** (direção aprovada nos docs §31.4 / P-030).
- **Espinha = Laravel Sanctum + PostgreSQL RLS** (conselho a validar; análise abaixo).
- **Fator de identidade = o login/base do SEI (CPF+senha), operado pela ATI** — pedir uma API à
  ATI para validar/alimentar o Agiliza. Como o SEI **já autentica por CPF+senha**, reaproveitar
  essa identidade é natural.

> **Escopo:** o backend Laravel/Postgres fica **fora deste repositório**. Este documento
> **propõe** um contrato; ele **não** deve ser codificado no front até estar alinhado com a ATI
> e com o time de backend. "Nenhum endpoint inventado no front" continua valendo.

### Partes envolvidas na identidade

- **ATI — Agência Estadual de Tecnologia da Informação do Maranhão.** Opera o **SEI**, incluindo
  seu **banco de dados e o login** (que também usa **CPF + senha**). É de quem pediríamos a API
  para validar/alimentar a identidade do Agiliza.
- **Antônio — STI (área de TI interna da STC).** Ponto da STC para **infraestrutura/Keycloak** e
  para coordenar o alinhamento com a ATI. (A **STI** é a superintendência de TI *dentro* da STC; a
  **ATI** é a agência estadual *externa* que opera o SEI — não confundir as duas.)

---

## Princípios que guiam o desenho

- **RLS é ortogonal.** Row-Level Security resolve *autorização de dados* e entra em **qualquer**
  cenário de identidade (Sanctum hoje, Keycloak amanhã). Adotar desde já.
- **Autorização real é server-side.** Os guards do front são **só UX** (o próprio código admite).
  Quem barra de verdade é Laravel (ação) + RLS (linha).
- **CPF não é segredo.** CPF é *identificador*, nunca senha. O *fator* (senha/OTP/SEI) é separado,
  e a base serve para **identificar + vincular à UG**, não como prova de identidade.
- **SEI: canal formal, mas fonte de identidade legítima.** O link do ciclo continua viajando pelo
  SEI e **nada volta automaticamente ao SEI**. Ler a *identidade* da base da ATI é fluxo de
  entrada (inbound) — não fere essa trava.
- **Costura preservada.** Toda troca de provedor acontece atrás do `AuthPort`
  (`frontend/src/application/access/port.ts`): as telas, os guards e o formato da sessão não mudam.

---

## Por que Sanctum + RLS (análise resumida)

**São camadas diferentes** — não competem entre si:

| Peça | Camada | Responde |
|---|---|---|
| **Laravel Sanctum** | Autenticação | "Quem é você?" (sessão via cookie httpOnly / token) |
| **PostgreSQL RLS** | Autorização no banco | "Quais *linhas* você pode ver/alterar?" |
| **Keycloak** (docs §22) | Identidade (auth++) | Autenticação com SSO/federação/MFA |

- **RLS encaixa forte aqui** porque as travas duras são de **isolamento por tenant**: sem acesso
  cruzado entre UGs; conteúdo "restrito" só para autor + focal da mesma UG + STC; RNF-001
  ("restringir por perfil, UG, coleta e contribuição"). RLS impõe isso **no banco** — mesmo que uma
  query esqueça o `where ug_id`, a linha de outra UG **não sai**. Defesa em profundidade + bônus de
  minimização de acesso para LGPD.
- **Sanctum encaixa** porque é first-party (front Next.js + API Laravel), agnóstico ao identificador
  (CPF vira o "username"), e o **cookie httpOnly** resolve o "recarregar desloga" com boa postura de
  XSS. Bônus: **signed URLs nativos do Laravel** cobrem exatamente o "link assinado, com validade e
  escopo" do ciclo (§11).

**O que Sanctum não dá** (por isso a decisão Keycloak fica *aberta*): federação da base como fonte
de identidade, SSO entre sistemas da STC, MFA e admin console prontos. Com Sanctum, a integração com
a ATI é **código Laravel seu**.

---

## As duas leituras da mesma espinha

O build de curto prazo é **idêntico** nas duas; a diferença é só uma fase futura opcional.

| | Opção 1 — Sanctum+RLS **agora, Keycloak depois** | Opção 2 — Sanctum+RLS **definitivo** |
|---|---|---|
| Fase 0–1 (MVP) | **Igual**: Laravel + Sanctum + RLS + CPF via ATI | **Igual** |
| Fase 2 | Migra a *autenticação* para Keycloak (Laravel vira resource server; RLS e `AuthPort` intactos) | Mantém Sanctum; investe em MFA/recuperação próprios |
| Prós | Fiel ao §22 no futuro; ganha SSO/federação sem retrabalho de telas | Stack mais enxuta; um sistema a menos para operar |
| Contras | Um sistema a mais quando migrar | Diverge do §22; SSO/federação viram trabalho seu (alinhar com a ATI e a STI/Antônio) |

**Recomendação:** construir a Fase 1 já pensando na Opção 1 (a migração fica barata por causa do
`AuthPort` + RLS), mas **sem bloquear**: se na Fase 2 o Keycloak não se justificar, a Opção 2 segue
válida. **A decisão Keycloak-ou-não é adiável.**

---

## Arquitetura alvo (camadas)

1. **Autenticação — Laravel Sanctum (modo SPA/cookie).** Login por **CPF**; o *fator* vem da ATI
   (ver seção seguinte). Endpoints `POST /auth/login`, `GET /auth/me`, `POST /auth/logout`.
2. **Autorização de aplicação — Laravel (Policies/Gates).** Capacidades por perfil
   (`stc-analista` cria ciclo; `stc-especialista` aprova; focal responde/monitora; respondente
   responde a própria coleta). Espelha as regras já em `application/access/use-cases.ts`.
3. **Autorização de dados — PostgreSQL RLS.** Policies por UG + restrito. Contexto do request via
   `SET LOCAL app.user_id / app.ug_id / app.role` **dentro da transação** (cuidado com pool:
   `SET LOCAL`, nunca `SET` puro, sob PgBouncer transaction mode).
4. **Link do ciclo — signed URL do Laravel.** `temporarySignedRoute` (validade + escopo do ciclo)
   é o token de `/acesso/[token]`. Capability token, **não** identidade.
5. **Identidade externa — SEI, operado pela ATI.** Fonte de CPF ↔ servidor ↔ órgão/lotação; o SEI
   já autentica por CPF+senha.

---

## CPF + identidade do SEI (a peça central)

Tudo depende de **o que a ATI consegue expor**. Dois cenários — projetar para os dois:

### Cenário A — Delegação de autenticação (ideal)
A ATI expõe uma **API de validação de credencial** (ou federação/OIDC). O usuário entra no Agiliza
com **o mesmo CPF+senha do SEI**; o Laravel valida contra a ATI e o Sanctum emite a sessão local.
- ✅ Sem senha nova; identidade governamental já confiável; menos PII/segredo sob sua guarda.
- ⚠️ Depende de a ATI oferecer endpoint de *validação* de credencial do SEI (pode não ser OIDC
  pronto — talvez um endpoint próprio).

### Cenário B — Alimentação por roster (contingência)
A ATI expõe **só consulta por CPF** (retorna nome, órgão/lotação, vínculo). O Agiliza usa para
**identificar e auto-vincular a UG**, mas mantém **fator próprio** (senha definida no 1º acesso,
guardada/verificada pelo Sanctum).
- ✅ Não trava esperando SSO; funciona com uma API de leitura simples.
- ⚠️ Roster **não autentica** — a senha continua sendo responsabilidade do Agiliza.

### Fallback de cobertura (vale para A e B)
Quem **não está na base do SEI** (terceirizado, adjunta) entra pelo fluxo **R3 que já existe**:
pré-cadastro pelo ponto focal **ou** autocadastro pelo link com validação (checagem de domínio/UG
já implementada em `registerRespondentBySelf`).

**Pedido concreto à ATI:** priorizar endpoint de **validação de credencial** (Cenário A) e, no
mínimo, endpoint de **consulta por CPF** (Cenário B). Confirmar formato, autenticação da própria
API, SLA e base legal (LGPD).

```mermaid
sequenceDiagram
  actor U as Servidor (CPF)
  participant F as Front (Agiliza)
  participant L as Laravel + Sanctum
  participant A as ATI (login/base do SEI)
  participant DB as Postgres (RLS)
  U->>F: CPF + senha
  F->>L: POST /auth/login (cookie + CSRF)
  alt Cenario A — delegacao
    L->>A: valida CPF + senha
    A-->>L: ok + nome + orgao/lotacao
  else Cenario B — roster + senha propria
    L->>A: consulta CPF
    A-->>L: nome + orgao/lotacao
    L->>L: valida senha local (Sanctum)
  end
  L->>DB: cria sessao; SET LOCAL app.ug_id / app.role
  L-->>F: Set-Cookie httpOnly + {role, ugId, respondentId}
  F->>F: SessionProvider hidrata a sessao
```

---

## Contrato Front ↔ Backend (proposta — a alinhar, não implementar ainda)

Cada método do `AuthPort` atual vira uma chamada HTTP. As **formas de retorno discriminadas
permanecem** (`LoginResult`, `OpenLinkResult`, …) — mas o **perfil passa a ser decidido pelo
backend**, não mais pelo email no cliente.

| `AuthPort` (hoje) | Endpoint proposto | Quem autoriza |
|---|---|---|
| `login(cpf, senha)` | `POST /auth/login` | ATI (A) ou Sanctum local (B) |
| — (hidratar sessão) | `GET /auth/me` | Sanctum (cookie) |
| `openCollectionViaLink(cycleId)` | `GET /acesso/{signed}` | signed URL + RLS |
| `registerRespondentBySelf(data)` | `POST /coletas/self-register` | validação de UG/domínio |
| `loginRespondentFromCollection(cpf,senha)` | `POST /coletas/login` | Sanctum + RLS |
| `registerRespondentByFocal(...)` | `POST /coletas/pre-cadastro` | Policy: papel focal + UG |
| `respondAsFocal(cycleId)` | `POST /coletas/focal` | Policy: papel focal + UG |
| `registerFocalSignal(...)` | `POST /sinais` | Policy: papel focal + UG |

**Claims/sessão** que o backend devolve e o front guarda (mesma forma da `DemoSession`):
`role` (`stc-analista | stc-especialista | ponto-focal | respondente`), `respondentId`, `ugId`.

---

## Esboço de dados + RLS (a partir do §23 dos docs)

- `usuarios(id, cpf, nome, perfil, orgao_id?, adjunta_id?, ativo)` — CPF como identidade; **sem**
  guardar senha do SEI no Cenário A.
- `orgaos`, `adjuntas`, `setores` — taxonomia de UG para o vínculo.
- Policies RLS principais:
  - **Isolamento por UG:** respondente/focal só enxergam linhas de `ug_id = current_setting('app.ug_id')`.
  - **STC vê tudo:** policy que libera quando `app.role` ∈ perfis STC.
  - **Restrito:** contribuição marcada "restrito" visível a autor + focal da mesma UG + STC (log/auditoria).

---

## O que mudaria no front (quando o contrato existir — não agora)

Nenhuma tela muda; só a fronteira. Arquivos:

- `frontend/src/application/access/port.ts` — `login(email, password)` → `login(cpf, senha)`
  (email como fallback opcional); demais assinaturas mantêm a forma.
- **Novo** `frontend/src/infrastructure/http/http-auth-adapter.ts` — implementa `AuthPort` via
  `fetch` à API Laravel (com `credentials: "include"` para o cookie do Sanctum). Substitui
  `createDemoAuthPort` na composição.
- `frontend/src/infrastructure/session/SessionProvider.tsx` — hidratar de `GET /auth/me`;
  persistência vem do cookie httpOnly (sobrevive ao reload). O formato `DemoSession` continua igual.
- `frontend/src/features/auth/LoginScreen.tsx` — campo **CPF** (máscara + validação); email como
  fallback; remover "acessos rápidos" e `senha-simulada` no build de produção.
- **Aposentar** `identifyLogin` + `stcAccessEmails` em `application/access/use-cases.ts` (o perfil
  passa a vir do backend/token). As regras puras de UG/domínio migram para o Laravel.
- Guards das layouts (`stc | focal | respondente/layout.tsx`) **permanecem** (UX), agora respaldados
  por authz server-side.

---

## Faseamento

- **Fase 0 — agora (sem backend):** fechar o contrato com a **ATI** (Cenário A vs B) e esta ideia.
  Não implementar integração no front.
- **Fase 1 — MVP backend:** Laravel + **Sanctum (cookie)** + Postgres + **RLS**; login por **CPF**
  via ATI (A se possível; senão B); **signed URL** para o link do ciclo; fallback focal/autocadastro;
  adaptador HTTP no front.
- **Fase 2 — evolução:** MFA/OTP, recuperação de conta e a **decisão Keycloak** (migrar a
  autenticação mantendo RLS + `AuthPort`) — o ponto onde Opção 1 e Opção 2 se separam.

---

## Decisões em aberto / dependências

- [ ] **ATI expõe validação de credencial (A) ou só consulta (B)?** Formato, auth da API, SLA.
- [x] **Docs alinhados (§27 e P-030):** **STI/Antônio** = área de TI *interna* da STC (estava certo);
  adicionada a **ATI** (agência estadual *externa*) como dona do login/banco do SEI e fonte de
  identidade candidata. Corrigido no `docs/` e na cópia canônica em `DocumentosAdcionais/`.
- [ ] **LGPD:** base legal para tratar CPF; minimização; auditoria de acesso (RLS ajuda).
- [ ] **Vínculo CPF↔UG** quando o servidor tem múltiplas lotações (docs: pendente com a PM).
- [ ] **Cobertura de terceirizados** fora do SEI: confirmar o fluxo de fallback.
- [ ] **Sanctum cookie:** front e API no mesmo domínio/subdomínio (senão acertar `SameSite`/CORS).
- [ ] **Nomenclatura dos perfis STC** (P-025).

---

## Quando isto virar implementação

É uma decisão de arquitetura duradoura: ao construir, virar **ADR em `specs/`**, refletir em
`specs/system.md` (seção de autenticação) e registrar o handoff em `docs/state.md`.
