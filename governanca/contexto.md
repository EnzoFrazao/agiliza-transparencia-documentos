# Contexto completo — Projeto Agiliza Transparência (v10.0 — consolidação até 05/09/2026)

> **Leitura vigente (10/09/2026):** este documento preserva contexto e histórico acumulados. O
> contrato por IDs está em
> [`regras-de-negocio.md`](regras-de-negocio.md); aplique primeiro o
> **§35 — Consolidação de 02/09 e 05/09** deste documento. As seções anteriores explicam a evolução
> e não prevalecem quando divergirem do §35 ou de decisão humana datada. A decisão de 31/08 está em
> [`decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md`](decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md).

> **Histórico da versão 9.0 — julho/2026.** Essa versão registrou a apresentação do protótipo e a
> rodada de UGs. Suas formulações sobre perfis Analista/Especialista, gate de aprovação, XLSX para
> objeto variável e declaração manual de não ocorrência foram superadas pelos §§32–34. A íntegra
> anterior está preservada no histórico documental com hash próprio.
>
> **Status da fase:** entrevistas da 1ª rodada **encerradas** (STC: 4; UGs: 5, em 4 órgãos); **DETRAN e PM** ouvidos na sequência (UGs novas). Restam órgãos e a **TI da ouvidoria**, ouvidos **durante o desenvolvimento**. **O protótipo visual do MVP 1.0 está construído** (front-end only, React/TS, auditado e publicado). A fase agora é **validar o MVP/requisitos com a STC e refinar o protótipo**, antes de construir o MVP com backend. O **estado detalhado do protótipo** fica em `andamento_do_prototipo.md` (documento à parte, para não misturar status de implementação com as decisões de produto).

> **Encaminhamento técnico (snapshot 2026-10-19):** o repositório canônico privado
> [`Oxygeni-Projetos-Estagiarios/agiliza-stc`](https://github.com/Oxygeni-Projetos-Estagiarios/agiliza-stc)
> mantém a fundação Laravel/Inertia e a V1 HTTP em `main` (`c6066b9`). O código contém domínio
> persistente, PostgreSQL validado por migrations, API, cliente TypeScript e telas `/v1` para
> coleta fixa e variável, com comprovante de envio em PDF (PR #10) e a preparação para homologação
> (PR #11, `18c345b`, 19/10). A imagem de produção e a homologação foram ensaiadas; ambiente real,
> carga operacional do piloto e UAT com a STC e a SINFRA seguem abertos. O estado detalhado está em
> [`funcionalidades/v1-minima.md`](funcionalidades/v1-minima.md). O schema
> continua evoluindo exclusivamente por migrations; não haverá envio ao GitLab ou ao ambiente da
> STC antes de a solução estar completa e pronta. Ver a
> [decisão de 01/10](decisoes-de-reunioes/2026-10-01-fundacao-tecnica-e-composicao-da-equipe.md).
> A V1 será apresentada à chefia em 20/10/2026 e testada por ela na mesma semana. Depois dos
> ajustes, vêm a implantação na SINFRA, com feedback para a versão seguinte, e a expansão gradual
> às demais UGs e objetos; ver o
> [encaminhamento de 19/10](decisoes-de-reunioes/2026-10-19-apresentacao-v1-e-implantacao-gradual.md).

Você está assumindo o desenvolvimento de um projeto real, já iniciado, vinculado à **Secretaria de Transparência e Controle do Estado do Maranhão (STC/MA)**. Existe protótipo visual, documentação, reuniões e entrevistas realizadas e decisões que não devem ser revertidas. Leia tudo com atenção antes de ajudar.

-----

## 0. O QUE MUDOU NESTA VERSÃO (v7.0 → v8.0)

Esta versão aplica as **decisões das duas reuniões com a STC** (uma geral e uma de alinhamento) e as **respostas do cliente** que se seguiram. Ela **fecha o recorte do MVP 1.0**, resolve a maioria das pendências e — em dois pontos — **inverte** direções que estavam apenas inclinadas na v7.0. As transcrições são de áudio; onde algo ainda não fechou, está marcado **[em aberto]** e listado em §28.

1. **Recorte de MVP 1.0 (novo).** Fica explícito o que a **versão 1.0** entrega — provar a **coleta ponta a ponta** — e o que vai para **versões futuras**. Consolidado em §0.1.
2. **SIMONI fora do MVP (inverte a v7.0).** A v7.0 tratava o SIMONI como origem do ciclo e previa integração. **Decisão:** o SIMONI **não será integrado no MVP** — é um **sistema operado à parte**. A **origem do ciclo** passa a ser a STC criando-o **a partir de um mapeamento informação↔órgão** (objetos fixos + informações por órgão) que a **STR/Alessandra** vai montar. Efeito: o risco “SIMONI × Tesauro semântico” **sai do caminho do MVP**. (Atualiza §4, §6, §13, §17, §21, §22, §25.)
3. **Tesauro como fonte externa (fecha P-002).** O Tesauro **permanece** como camada semântica e base de interoperabilidade, **mas é gerido no Tema 3, externamente — a plataforma NÃO terá módulo de edição do Tesauro**. Cai a “Etapa 0 / Gestão do Tesauro na plataforma”. Os **objetos fixos são exportados do Tesauro**. (Atualiza §6, §16, §17, §18, §24.)
4. **Entrada conforme o tipo de objeto; boxes genéricos fora do MVP (fecha P-003).** No objeto
fixo, a UG **baixa, preenche e envia o modelo XLSX oficial** e os uploads configurados. No objeto
variável, preenche **campos diretos e/ou uploads**, sem XLSX. (Atualiza §7, §9, §19, §20, §23.)
5. **Verificação manual pela STC + checagem estrutural (fecha o rumo de P-001).** No MVP a STC **confere o conteúdo manualmente**; o sistema faz apenas **checagem estrutural**: presença dos **anexos obrigatórios** (basta haver upload, mesmo com título diferente) e **conformidade da planilha com o modelo** (estrutura/colunas). **Validação de conteúdo** (ex.: CPF) e **pré-verificação por IA** ficam para o futuro. (Atualiza §7, §8.)
6. **Hierarquia Ciclo × Coleta (novo).** Um **ciclo** é composto por **N coletas**; no MVP, a STC cria o ciclo com **uma coleta**, que funciona como um **formulário (tipo Forms)** — cada respondente faz **sua submissão**. (Atualiza §7, §10, §19, §23.)
7. **Novo ator: respondente técnico / “dono da informação” (fecha P-016 como híbrido).** Além da STC e do **ponto focal**, entra o **respondente técnico** — quem efetivamente detém o dado. **Cadastro híbrido:** o ponto focal pode pré-cadastrar (nome+e-mail) **ou** quem entra pelo link se cadastra (nome/e-mail/telefone/cargo/órgão) + **validação por e-mail** + cria senha; nos próximos acessos, **e-mail + senha**. Flag **“usuário criado pelo próprio usuário”** e **cruzamento órgão selecionado × órgão preenchido**. (Atualiza §9, §10, §11.)
8. **Validação do ponto focal parametrizável (novo, P2).** Ao criar o ciclo, a STC decide (**toggle**) se aquele envio **exige revisão do ponto focal** antes de ir à STC, ou **vai direto**. (Atualiza §7, §10.)
9. **Objeto fixo × variável (novo).** A STC classifica na criação: **fixo** = referencia um modelo
XLSX oficial e versionado do Catálogo; **variável** = usa campos diretos, uploads ou ambos, com ao
menos um item e sem XLSX. (Atualiza §16, §18 e §34.)
10. **Estados do ciclo/coleta explicitados (novo).** Máquina de estados com **resposta negativa** (“não tenho a informação”) e **“não enviado no prazo”** como **estados próprios**. (Atualiza §19.)
11. **Mapeamento informação↔órgão (novo, pré-requisito).** **Não existe hoje** — nem no Tesauro nem no SIMONI de forma fiel à realidade. A **Alessandra vai montá-lo** (item a item). É a **fonte do funil invertido** no MVP. **[Em aberto]** como ele chega (atualização dentro do Tesauro × documento à parte). (Atualiza §15, §16.)
12. **SEI (reafirmação).** O **único elo** SEI↔plataforma é o **link do ciclo anexado ao SEI**. Nada volta ao SEI automaticamente: **fechamento e rejeição** geram, quando muito, **registro manual** da STC no SEI. (Confirma §12.)
13. **Notificação = e-mail no MVP; WhatsApp como próximo passo.** Sem exigir e-mail corporativo; coleta-se telefone. WhatsApp (API) fica para depois. (Atualiza §20.)
14. **Pendências atualizadas (§28).** Resolvidas/direcionadas: P-001, P-002, P-003, P-004/P-006, P-007/P-008, P-015, P-016, P-017, P-018. **Seguem abertas:** coleta = objeto+órgão × objeto+setor; P2 por órgão × por ciclo; resposta negativa por coleta × por linha; forma de chegada do mapeamento.

-----

## 0.1. MVP 1.0 — DECISÕES CONSOLIDADAS DAS REUNIÕES (FONTE ÚNICA)

> Esta seção é o **estado atual** do produto após as reuniões. Onde o restante do documento (redigido antes) divergir, **vale esta seção**.

### Matriz de decisão consolidada
**Código do MVP 1.0: `L1 · R3 · E2 · V1 · T2 · S0 · P2 · O(fixo/variável por ciclo)`**

|Eixo|Decisão|Leitura|
|---|---|---|
|**L1**|Link único por ciclo|Cada ciclo gera um link/hash (tipo Forms), compartilhado entre as UGs e **anexado ao SEI**. Ponto focal entra por **login/painel**; respondente que retorna, por **e-mail+senha**.|
|**R3**|Identificação híbrida|Ponto focal pode pré-cadastrar (nome+e-mail); quem entra pelo link se cadastra (nome/e-mail/telefone/cargo/órgão) + **validação por e-mail** + senha. Flag “usuário criado pelo próprio usuário”; cruzamento órgão selecionado × preenchido.|
|**E2**|Entrada conforme o objeto|Objeto fixo referencia modelo XLSX oficial e uploads configurados; variável usa campos diretos e/ou uploads, sem XLSX.|
|**V1**|Manual (STC) + checagem estrutural|Sistema confere presença de anexos obrigatórios e **estrutura da planilha**; **conteúdo das células = humano**. IA e validação de conteúdo = futuro.|
|**T2**|Tesauro como proveniência|Carga inicial preservada; o **Catálogo do Agiliza** é a fonte operacional posterior e versionada.|
|**S0**|**Sem** integração com o SIMONI|Sistema à parte. Fonte do MVP = **mapeamento** (objetos fixos + informações por órgão) que a Alessandra vai montar.|
|**P2**|Validação do ponto focal **configurável**|**Toggle** na criação do ciclo: exige revisão do ponto focal antes do envio, ou vai direto à STC.|
|**O**|Tipo de objeto **por ciclo**|STC decide: **O-fixo** (modelo XLSX oficial) ou **O-variável** (campos diretos e/ou uploads, sem XLSX). Coexistem.|

### Hierarquia e atores
- **Ciclo × Coleta:** 1 ciclo pede 1 objeto (no MVP) e usa **1 link único** para **todas as UGs**, operando **como um Forms**; cada **coleta** é a **resposta de um respondente** (N por ciclo). Cada UG vê **só as suas** respostas; a STC vê todas.
- **STC** — cria o ciclo/coleta, define objeto/campos/anexos obrigatórios, verifica e aprova/rejeita.
- **Ponto focal** — **1 por órgão** (muda com o governo); **vê o ciclo inteiro** e todas as respostas de todas as coletas do órgão; **pode responder ou apenas monitorar**; quando o toggle P2 está ligado, **dá ciência/consolida** antes de enviar à STC.
- **Respondente técnico / “dono da informação”** — **N por coleta**; **vê apenas as coletas** em que foi adicionado ou às quais chegou pelo link; **não precisa conhecer o conceito de “ciclo”** (para ele é o formulário).

### Objeto fixo × variável
- **Fixo:** referencia modelo XLSX oficial e versionado no Catálogo, além dos uploads configurados.
- **Variável:** a STC configura campos diretos, solicitações de upload ou ambos; deve existir ao
  menos um item e não há planilha de preenchimento.

### Fluxo do MVP (ponta a ponta)
1. STC cria o **ciclo** (uma **coleta**) a partir do **mapeamento**; define objeto/campos e **anexos obrigatórios**; marca o **toggle de validação do ponto focal**; gera o **link** e o anexa ao **SEI**.
2. O SEI é enviado à UG; **qualquer pessoa da UG pode acessar** pelo link.
3. O **respondente técnico** acessa (cadastro na 1ª vez) e responde conforme o tipo: XLSX oficial
   e uploads no fixo; campos diretos e/ou uploads no variável.
4. **Checagem estrutural por tipo**: estrutura do XLSX fixo e presença de campos/uploads esperados.
5. Se o toggle estiver ligado, o **ponto focal revisa/consolida** e envia à STC; senão, a submissão **vai direto**.
6. A **STC verifica** (conteúdo, manual) e **aprova** ou **rejeita com justificativa**; a rejeição **reabre a coleta/o envio** para correção.
7. **Comprovante** de envio; **histórico** encadeado (autor + data). O **fechamento** é registrado na plataforma; qualquer registro no SEI é **manual** da STC.

### Fora do MVP 1.0 (versões futuras)
Chat interno (estilo comentário do Google Docs, **ancorado ao item**); **IA** como pré-verificador de formato; **validação de conteúdo** (ex.: CPF); **ranking**; **dashboard** avançado por UG/desempenho; **gestão avançada de perfis/permissões**; **integrações extras**; **unificação** das planilhas parciais num arquivo único; **correlação anexo↔linha** automática; **WhatsApp** (API); **envio por boxes**.

-----

## 0.3. DECISÕES DA REUNIÃO DE APRESENTAÇÃO DO PROTÓTIPO (v8.0 → v9.0)

> **Seção de maior prioridade.** Reúne o que a **apresentação do protótipo à STC** (Thiago/STR, Talita, André + equipe) e a **rodada de UGs no DETRAN/PM** acrescentaram, mais o **estado real do protótipo** (auditado no código). Onde esta seção divergir do restante do documento — inclusive da §0.1 —, **vale esta**. As decisões da §0.1 (matriz do MVP) continuam valendo no que não for contrariado aqui.

### Contexto da reunião
A STC **viu o protótipo visual** rodando e **validou o fluxo da coleta** (interação com o órgão) como suficiente, com melhorias que virão na execução. O recado central foi que **falta um segundo fluxo**: a **gestão do ciclo** — a camada interna da STC (como o ciclo nasce, é aprovado, migra da demanda para o Agiliza, muda de estado, é monitorado e encerrado). Esse fluxo **ainda não está desenhado nem implementado**. Nas palavras da reunião: “tem o fluxo da plataforma [coleta] e tem o fluxo do ciclo [gestão]”.

### 1. Perfis internos da STC (novo)
O perfil único “STC” **subdivide-se internamente**:
- **Analista/criador** — cria, configura, edita e reenvia ciclos. No protótipo: **Analista STC**.
- **Aprovador/gestor** — revisa a criação, solicita ajustes ou aprova; faz a gestão/aprovação do ciclo. No protótipo: **Especialista STC**.
- Ambos compartilham **Acompanhar ciclos**, **Histórico**, **Registro** e a validação das respostas das UGs.

**⚠ Nomenclatura a confirmar (P-025).** Na reunião apareceram os termos **superintendente/STR** (quem aprova e faz a gestão), **operador** (perfil mais simples, sem telas gerenciais) e **especialista**. O protótipo consolidou tudo em **Analista + Especialista**. A STC precisa confirmar os nomes oficiais e se haverá um terceiro perfil “operador” (mais simples). O **painel gerencial** (quantos ciclos abertos, enviados, atrasados, pendentes de aprovação) foi tratado como **item futuro** (“mais pra frente / não é o MVP”).

### 2. Gate de aprovação do ciclo antes do envio às UGs (novo)
Entre a **criação** e o **envio** há uma **etapa de aprovação obrigatória**. O ciclo nasce **“em preparação/criado”**, vai para **“pendente de aprovação”**, e **só a aprovação** gera as coletas, o link do ciclo e as notificações — e disponibiliza o ciclo às UGs. Enviar para análise **não** cria nada para o órgão. Justificativa da STC: a maturidade da equipe varia, então **alguém precisa aprovar** antes de sair. É **auditável**; o aprovador pode editar/remover UGs ou pedir ajustes ao criador. *(Já implementado no protótipo via `creationStatus`.)*

### 3. Gestão do ciclo como fluxo próprio (novo — a desenhar)
Distinto do fluxo da coleta, o **fluxo de gestão do ciclo** cobre:
- **Origem/migração:** a necessidade nasce no **SIMONI** (rotina) **ou** de forma **avulsa** (ex.: rodada do PNTP, avaliações do TCE/TCU com periodicidades próprias); a STC **importa/registra** e transforma em ciclo. *(SIMONI segue fora do MVP como integração; a migração é conceitual/manual.)*
- **Criação e aprovação** (itens 1 e 2).
- **Estados do ciclo** e **monitoramento** de quem respondeu / não respondeu / declarou não ter.
- **Encerramento**.

Precisa de **fluxograma próprio** — é a maior lacuna documental aberta pela reunião.

### 4. Ciclo de vida do ciclo (novo/refina §19)
- **Estados discutidos:** `criado` → `enviado` → `em andamento` → `atrasado` → `finalizado`. *(No protótipo atual os estados do ciclo são só `em-andamento` / `finalizado` / `sem-envio-no-prazo`, com “atrasada” derivada; o gate de aprovação vive num campo à parte. O ciclo de vida rico acima é alvo de refinamento.)*
- **Encerramento com relatório:** ao encerrar (após o prazo), gerar um **relatório de quem enviou / quem não enviou / quem declarou não ter** — necessidade real da STC para “dar ciência ao chefe” e justificar a cobrança. **Antes** de encerrar, decidir se **reitera**.
- **Múltiplos SEI por ciclo (reiteração):** ao reiterar um prazo, **acrescenta-se outro número de SEI ao mesmo ciclo** — o **mesmo link continua valendo e o prazo é reaberto** (“reiteramos em relação ao ofício anterior”). O **nº do SEI pode ser informado a qualquer momento** (antes ou depois da aprovação/envio) e não trava a criação. *(No protótipo o ciclo tem um único `seiNumber`; reiteração é alvo de refinamento.)*
- **Novo ciclo (recomeço):** quando se abandona o ciclo e recomeça do zero, cria-se um **novo ciclo**, com um **indicador de relação** ao anterior (desmembramento). Reiteração ≠ novo ciclo.
- **Encerramento sempre manual:** **não há encerramento automático** em nenhum momento — quem encerra é sempre a STC. **Backlog (não-MVP):** apenas a **prorrogação de prazo** (a coleta que pediu prorrogação segue “em andamento”; as outras vão para “atrasado”). O fluxo de gestão do ciclo tem de prever a prorrogação.

### 5. “Declaração de não ocorrência” (refina P-021)
A ação vigente é **`Declarar ausência de informações`** e representa ausência total da UG no
objeto e período. Ela aparece depois da consulta ao escopo, exige confirmação e justificativa e
encerra o restante do formulário. Com toggle ligado, o focal declara; no modo direto, o
respondente declara. Ausências parciais são detectadas antes do envio e confirmadas como não
ocorrências, sem seleção manual de requisitos.

### 6. Notificação e WhatsApp (reafirma §20)
**E-mail no MVP**, confirmado. Levantou-se que **enviar** WhatsApp **para** o cliente **tem custo** (recebê-lo não), então a automação de WhatsApp segue como **futuro**, com essa ressalva de custo. O ponto focal costuma ser avisado antes por canal externo (WhatsApp manual), mas a plataforma **notifica por e-mail**.

### 7. Catálogo do Tesauro concretizado (novo/refina §16, §18)
Do arquivo real `Tesauro_MA_Transparente_v2_3_17_03.xlsx`, extraído deterministicamente para o protótipo:
- **49 objetos.** A coluna **Fluxo de Origem** separa **41 manuais** (entram na criação de **objeto fixo**) e **8 automatizados** (`MT-0006/0007/0008/0009/0010/0014/0017/0039`) — que **ficam fora** da criação manual. “Objeto fixo” = objeto manual já catalogado; **não** inclui os automatizados.
- **228 campos canônicos**; **campos disponíveis × campos inicialmente obrigatórios** por objeto (nem todo campo começa marcado).
- **Anexos obrigatórios** mapeados (ex.: MT-0013 Termo de Recebimento; MT-0022 Metas/Riscos Fiscais; MT-0034 Plano de Trabalho); o **Relatório de Prestação de Contas** é obrigatório só “quando disponível”.
- **Caso MT-0049:** 14 campos disponíveis / 10 inicialmente obrigatórios (4 variáveis/condicionais começam desmarcados).
- **UGs não são pré-selecionadas** na criação — o Tesauro **não** contém o mapeamento oficial informação↔órgão (P-022). Presumir UG poderia cobrar o órgão errado.

**Pendências novas do Tesauro:**
- **P-023** — **justificativa de anexo faltante** não destrava o envio no protótipo (comportamento a confirmar).
- **P-024** — **contradições/versionamento do Tesauro:** `MT-0011` e `MT-0049` têm Fluxo de Origem “manual” mas notas de escopo sugerindo automação; o nome do arquivo diz `v2_3` mas as instruções internas dizem **v2.2**; a instrução de sequência (“novos objetos a partir de MT-0049”) contradiz o arquivo, que já traz o MT-0049. Até a STC confirmar, o protótipo segue a coluna **Fluxo de Origem**.

### 8. UGs novas — DETRAN e PM (reafirma §15, §27)
DETRAN e PM foram ouvidos (não estavam no compêndio das UGs). Reconfirmaram **coleta manual**, a **negativa como resposta válida** e a **inexistência do mapeamento informação↔órgão** (a montar). **Fato acionável:** a **PM não responde mais licitações** — passou para uma **adjunta**; a Talita vai **atualizar para parar de cobrar a PM** e cobrar a adjunta. Reforça que o **mapeamento não é estático** e muda com a estrutura dos órgãos.

### 9. Estado do protótipo e próximos passos
O **protótipo visual do MVP 1.0 está construído** (React/TS, front-end only, estado simulado, auditado e publicado no GitHub). Ele cobre o **fluxo da coleta** ponta a ponta, o gate de aprovação e o catálogo do Tesauro. **Não** cobre (ainda) o **fluxo de gestão do ciclo** rico (itens 3 e 4), os **múltiplos SEI**, o **encerramento com relatório** nem a **dupla saída** da não ocorrência. O detalhamento (implementado × simulado × a fazer) está em **`andamento_do_prototipo.md`**. **Próximos passos definidos na reunião:** (1) validar o MVP/requisitos e refinar o protótipo; (2) construir o MVP com backend; (3) elaborar um **plano de trabalho mensal**.

-----

## 0.2. HISTÓRICO — MUDANÇAS DA v7.0 (v6.0 → v7.0)

*Preservado para registro; onde houver conflito, valem as decisões da v8.0 acima.*

Esta versão não altera o levantamento; ela **fecha decisões e corrige divergências** que ficaram entre o v6.0 e o SRS.

1. **Nome do sistema:** de **STC Agiliza** para **Agiliza Transparência**. (A **STC** continua sendo a organização.)
2. **SEI é sempre obrigatório.** Todo ciclo tem processo no SEI; a **plataforma é um caminho paralelo de resposta** — a resposta e a interação ocorrem na plataforma, mas o SEI acompanha sempre. *(Corrige o v6.0, que dizia "correção sem depender do SEI".)*
3. **Canal de comunicação (chat) na plataforma → PENDENTE (P-017).** Deixou de ser decisão fechada / "requisito nº 1". A correção acontece no **mesmo ciclo/processo do SEI** (sem novo despacho); **enquanto não se decide o chat, a via formal é o SEI/e-mail**.
4. **Chatbot → melhoria futura** (pós-desenvolvimento, se houver tempo e necessidade). Não é "fora do escopo" categórico nem requisito atual.
5. **Bitrix → NÃO será implementado** nem integrado. O SIMONI+Bitrix segue como planejamento **atual da STC** (contexto), mas a plataforma não o integra.
6. **Identificação do respondente → REABERTA (P-016).** Duas hipóteses: **(a)** o ponto focal cadastra/pré-vincula o respondente; **(b)** o respondente se identifica sozinho pelo link. A direção anterior era (a), mas voltou a ser pendência (condiciona os requisitos de respondente).
7. **Mudança institucional (ajuste):** o **Fernando (STC) foi transferido de área** (não "saiu de vez"); **Thiago** o substitui. **Alessandra** confirmada — **grafia certa e uma só pessoa** (a mesma da gestão da informação/Tesauro).
8. **Coleta permanece MANUAL.** A plataforma **não se integra aos sistemas internos das UGs nem automatiza a extração** — melhora o **envio manual** do respondente. "Automatizar os objetos manuais" significa automatizar o **ciclo** (disparo/lembrete), não a extração do dado.
9. **Numeração alinhada ao SRS.** Os **requisitos funcionais canônicos** ficam no `SRS_Agiliza_Transparencia_v2` (**RF-001 a RF-040**, agrupados por etapa); as **pendências** seguem **P-001 a P-018**. Este contexto não mantém lista paralela de RFs, para não divergir.

### O que a v6.0 já trouxe (permanece válido)

Panorama; cada item está detalhado ao longo do documento.

1. **Entrevistas das UGs concluídas** — 5 pessoas em 4 órgãos: **Camila (SEDUC)**, **Fernando + equipe (ouvidoria, provável Fazenda)**, **Jaldo (SINFRA/CAGE)**, **Zezé + Joaquim (SINFRA/contratos)** e **Guilherme (SAF)**. **A maturidade varia enormemente** entre órgãos (§3.C, §27).
2. **IA = VERIFICADOR/CHECADOR** (confere presença do que foi pedido + formato e **notifica**; **não transforma** o arquivo). A decisão final é da STC: **verificar × transformar** (§7, §17, §28).
3. **Mapeamento por adjunta/setor** — o erro de destinação ocorre inclusive entre adjuntas de uma mesma secretaria; surge o **contrato compartilhado entre adjuntas** (§15).
4. **Requisitos da ponta:** comprovante/recibo de envio; feedback da STC; salvar rascunho + reenviar; onboarding por mapeamento; volume/ciclos curtos; sigilo/segurança fiscal; capacitação (§20).
5. **Domínio de obras detalhado:** medições (OS manual, captura de nº SEI, duplicidade → Tribunal de Contas), status paralisada × parada × aguardando pagamento; e o modelo de dados de contrato (§15, §18, §19).
6. **Tesauro — alerta bloqueante mantido (P-002):** decidir se é redundante com o SIMONI (usar ou não), com a Alessandra (§17).

> **Heranças mantidas:** dois fluxos; stack PHP/Laravel + PostgreSQL + Docker + Keycloak + GitLab + Tesseract; campos vindos do TemaTres; verificação ≠ validação ≠ publicação; a plataforma é o centro; **duas portas de entrada**; **envio por boxes**; **registrar resposta negativa**; **mapeamento não estático (por adjunta)**; **SEI sempre presente (caminho paralelo)**; **não substituir o SIMONI** (Bitrix fora); escopo termina na validação; ranking por último.

-----

## 1. QUEM É O CLIENTE

**Secretaria de Transparência e Controle do Estado do Maranhão (STC/MA)** — e sua **Secretaria Adjunta de Transparência (SEATRAN)**.

A STC fiscaliza e garante a transparência no uso dos recursos públicos estaduais: coleta, organiza, valida, armazena e publica informações dos órgãos para que cidadãos e gestores acompanhem o uso do dinheiro público. Base legal: Constituição Federal e Lei de Acesso à Informação (Lei nº 12.527/2011).

**Natureza estrutural (confirmada nas entrevistas):** a STC **não produz** a maior parte do que publica — **recebe** de dezenas de UGs externas (ordem de **60+**, a confirmar). É um **hub de coleta e validação**. Isso explica quase todas as dores: um hub que depende de terceiros sem padronização nem SLA terá baixa previsibilidade, por mais tecnologia que se ponha do lado da STC. As entrevistas da ponta confirmaram esse retrato e acrescentaram que **a maturidade das UGs varia muito** (§3.C).

-----

## 2. GOVERNANÇA DO PROJETO

**Instrumento legal:** Acordo de Cooperação Técnica (ACT) nº 08/2026 (013725123) — SEI 2026.11122.00458. Kick-off em maio/2026.

**Programa:** TechX — Formação em Tecnologia Exponencial. Estudantes em squads multidisciplinares, sob mentoria e acompanhamento pedagógico, produzem protótipos, PoCs e soluções aplicáveis, com desenvolvimento/implantação mediante bolsas.

### Três atores

|Ator|Responsabilidade|
|---|---|
|**STC / SEATRAN**|Regras de negócio, homologação e diretrizes de infraestrutura. Apresenta demandas, indica mentor técnico (até 2 sessões mensais de 2h) e ponto focal técnico (2h semanais), disponibiliza dados anonimizados quando necessário, valida requisitos/prioridades, dá feedback e apoia validação/testes/piloto. A escolha do projeto a desenvolver é da STC.|
|**Hub de Inovação (Oxygeni Hub — Universidade CEUMA)**|Mentoria técnica, suporte na stack e qualidade do código. Seleciona estudantes, coordena trilhas, designa mentores, disponibiliza espaço/infra/ferramentas, promove sprints, acompanha técnica e pedagogicamente, elabora relatórios e emite certificação.|
|**Bolsistas (Enzo + Clarice)**|Execução, codificação, integração com o TemaTres e desenvolvimento. Contratação via **FAPEMA**. (A administração central, via **SEGEP**, não tem registro de que os bolsistas atuam na STC — exemplo concreto da ausência de gestão centralizada de informação no Estado.)|

### Interlocutores atuais na STC *(atualizado)*
- **Thiago** — auditor-chefe / engenheiro da auditoria; **substituiu o Fernando** (que foi **transferido de área**). **STR = Talita + Thiago + Alessandra** — a **mesma pessoa** da gestão da informação/Tesauro.
- **Talita** — operação/coleta e SIMONI (principal ponto de contato operacional).
- **Patrick** — contato para dúvidas (junto da Talita).
- **Alessandra** — gestão da informação / Tesauro. **Stéferson** — coordenação/normativo (IN). **Antônio/STI** — infraestrutura. **Leandro** — dev do SIMONI.

### Modelo de trabalho
- **Sprints quinzenais** (início segunda, término sexta da 2ª semana). **Entregável obrigatório:** Relatório Quinzenal. **Entregável funcional** quando aplicável (link/protótipo/preview), com **entrega presencial**.
- **Local:** Oxygeni Hub (CEUMA); presencial na STC quando necessário.
- **Fase:** **transição do levantamento para o desenvolvimento.** Prazo do projeto ~11 meses úteis.

-----

## 3. O PROBLEMA REAL (AS-IS)

Parte da transparência já é automatizada (folha, orçamentário/financeiro), mas uma parcela relevante ainda é **manual**. Hoje **não existe o conceito de "ciclo"** — trata-se cada "necessidade de atualização" manualmente.

### Como funciona hoje (as-is, detalhado pelo Thiago)
1. O **SIMONI** sinaliza objeto por vencer/vencido (monitoramento de prazo).
2. A STC monta **minuta de ofício no SEI** com **link para um formulário** (hoje **Google Forms**) e um **modelo de planilha padrão** para download.
3. A minuta vai ao **gabinete**, que dispara **ofício circular** às UGs alvo.
4. As UGs **baixam, preenchem e sobem** de volta — **ou** respondem por outros meios (e-mail, WhatsApp, planilha própria, despacho no SEI), fora do padrão.
5. A equipe **consolida manualmente** e **"traduz"** o que vem fora do padrão; o que não dá para traduzir se perde.
6. Para saber **quem respondeu / disse "não tenho" / não respondeu**, cruza-se **manualmente** o formulário com os despachos do SEI.
7. Se falta/erra, recontata o órgão — idas e voltas por WhatsApp/e-mail, perdendo a identificação do respondente.

### Os 3 problemas centrais
1. **Múltiplos canais sem controle** — cada órgão responde por onde quer; sem histórico/rastreabilidade.
2. **Retrabalho operacional constante** — horas consolidando planilha por planilha, pedindo correções, reinserindo à mão.
3. **Falta de padronização** — o mesmo dado chega de muitas formas; o modelo frequentemente não é respeitado.

### Problemas adicionais (validados nas entrevistas STC + UGs)
- **"Para quem mandar" nem sempre é claro** e, quando há mapeamento, **nem sempre é respeitado** (caso Thiago — conta de adiantamento: mandou lista filtrada, o gabinete enviou para todas). **A ponta confirma** o disparo "para todos" gerando retrabalho (SEDUC, SAF), e revela que **o erro ocorre até entre adjuntas** de uma mesma secretaria.
- **A comunicação interna do órgão quebra o fluxo:** o pedido chega ao gabinete e é distribuído sem passar pelo setor de transparência (cadeia longa da SEDUC).
- **Sem comprovante de envio:** a UG manda e **não recebe recibo** — "não dá garantia para ninguém" (SEDUC).
- **Comunicação/feedback opacos:** descobrir um erro **demora**; onde há contato humano direto com a STC a dor some, mas **não escala** (SAF com Patrick/Talita).
- **Banco de dados inexistente na origem:** o dado existe mas está **espalhado**; cada pedido vira garimpo (Ouvidoria, SAF). *(Problema interno da UG — fora do escopo; a UG busca e envia.)*
- **O SEI incha** por "despacho sobre despacho"; eletrônico só desde **dez/2024** → histórico difícil de achar. O ideal (processo-mãe/filhos) **não é praticado**.
- **Não se distingue "não respondeu" de "respondeu que não tem"** → registrar a **resposta negativa**.
- **Erro de vínculo de órgão pelo respondente** (caso **IMA/IMA Sul** — Thiago; e "funcionário X seleciona que é da saúde" — SAF) → raiz da opção (a) de identificação.
- **Terceirizados é o objeto mais problemático** — travou "muitas secretarias" (SAF) e é o caso recorrente de campos faltando (Thiago).

### 3.A. Diagnóstico: o gargalo é cultura/estrutura, não tecnologia
- A maior barreira é **comprometimento e consciência dos órgãos** — a transparência é vista como **demanda externa**, não como responsabilidade de quem detém a informação. Outras secretarias "fecham"; a cultura do **"me fala o que fazer que eu faço"** é generalizada.
- **Ferramenta boa não basta sem adesão** — o protótipo anterior já tratava campos e devolvia, mas perdeu força por falta de envolvimento.
- **Descontinuidade institucional:** trocas de governo renovam equipes (comissionadas) e o conhecimento se perde — dificulta papéis fixos.
- **Travas internas** (SAF: quadro insuficiente para comissões, regimento travado na SEAD) explicam por que às vezes o dado não sai — gargalo **administrativo**, não de ferramenta.
- **O playbook de sucesso das obras (evidência forte):** padronização + **data fixa (dia 10)** + **ofício formal "vindo de cima"** + grupo de WhatsApp + **pressão de pares** + um **responsável-modelo** que envia primeiro. Levou obras a "zero atraso".
- **Princípios de design (orientam todo o produto):** **(1) fricção mínima**; **(2) recortar o processo que o órgão já faz**; **(3) simplicidade e didática** ("os órgãos não leem"); **(4) estímulo cultural** (ranking + certificação Diamante).

### 3.B. Risco organizacional: dependência de pessoa-chave (bus factor)
Do lado da **STC**, a operação de coleta concentra-se na **Talita** (4 de 6 etapas passam por ela); com o **Matheus na TI**, concentra ainda mais. Do lado da **ponta**, o sucesso das obras repousa num **operador acima da média** (**Jaldo**, terceirizado da Progen) e, na SAF, numa **relação pessoal** (canal direto com Patrick/Talita). **Nada disso escala.** O produto deve **institucionalizar** o que hoje depende de pessoas específicas (e recomenda-se **documentar o procedimento da Talita**, mitigação que nenhum software substitui).

### 3.C. A maturidade das UGs varia muito *(novo — síntese das entrevistas da ponta)*
- **SEDUC — baixa:** cadeia longa, sem ponto focal, sofre com comunicação, volume e formato.
- **Ouvidoria/Fazenda — média:** controle interno bom, mas **dependente da TI** para consolidar (ICMS 10 anos); formato não é problema (a TI entrega limpo); frequência baixa; dados sigilosos.
- **SINFRA — alta, mas frágil:** processo redondo, porém dependente do Jaldo; domínio de **obras/medições** é o mais complexo.
- **SAF — média:** triagem pelo controle interno; **sem banco organizado**; travas internas.
> **Consequência de produto:** o sistema precisa **servir do extremo desorganizado ao organizado** e comportar **respondente-pessoa e respondente-equipe (TI/terceirizado)**.

-----

## 4. OS DOIS FLUXOS DENTRO DE UM PIPELINE MAIOR

```
GESTÃO DA INFORMAÇÃO  →  [ COLETA  →  VALIDAÇÃO ]  →  ARMAZENAMENTO  →  PUBLICAÇÃO
        (fluxo 1)            (fluxo 2 — escopo)          (fora de escopo)
```

- **Escopo dos bolsistas:** **coleta e validação**. Fechar até a validação "já mata o problema".
- **Acima:** **gestão da informação / gestão do Tesauro** — fluxo próprio, majoritariamente interno.
- **Abaixo:** **armazenamento e publicação** — fora do escopo.

Os dois fluxos **não são fortemente dependentes** e podem amadurecer em paralelo; o Fluxo 1 **dá origem** ao Fluxo 2.

> **Reposicionamento do esforço (Talita):** o planejamento (Bitrix + SIMONI = topo do funil) **já funciona**. A dor está na **segunda metade do Fluxo 2 — devolutiva e validação manual**. Concentrar a construção no Fluxo 2 e tratar o Fluxo 1 como **integração/reestruturação**, não reconstrução (ver Alerta §17).
>
> **Atualização v8.0:** no **MVP 1.0**, o Fluxo 1 **não** integra o SIMONI nem edita o Tesauro na plataforma (§0.1). A origem do ciclo é a STC a partir do **mapeamento informação↔órgão** (§15); o Tesauro é **fonte externa** (§17).

-----

## 5. A DISTINÇÃO INFORMAÇÃO × DADO (CONCEITO OBRIGATÓRIO)

> **A STC não tem necessidade de dados — tem necessidade de informação.**

- **Informação** é o que precisa ser publicado (ex.: "acordos de cooperação", "contratos terceirizados").
- **Dado** são os campos (metadados) que a compõem.
- Caminho: **necessidade de informação → entender o tema → destrinchar em dados (campos)**.

A STC pediu um **glossário interno** (priorizar "informação", reduzir "dado"). "Entender a informação" vem antes de "definir os dados".

-----

## 6. FLUXO 1 — GESTÃO DA INFORMAÇÃO / GESTÃO DO TESAURO

Fluxo **majoritariamente interno** (Tesauro/TemaTres). "Etapa zero": decide se um tema gera ou não um ciclo de coleta. **Exemplos:** emendas parlamentares, acordos de cooperação, BB Pago, terceirizados, estagiários, obras, convênios/transferências voluntárias.

### 6.1. Processo conceitual da STC (contexto — não é o que construímos)
Antes de qualquer dado, a STC **entende a informação** (o que é, de onde vem, temporalidade, quem fornece) e **destrincha em dados** (metadados).

### 6.2. O que será construído no Fluxo 1 (escopo) *(revisto na v8.0)*
> **Decisão das reuniões:** o **Tesauro é fonte externa**, gerido no **Tema 3** — **a plataforma NÃO cria nem edita objetos/metadados do Tesauro** (a antiga “Etapa 2 / Gestão do Tesauro na plataforma” **cai**). No MVP, o Fluxo 1 se resume a **consumir** do Tesauro e a **operar o mapeamento** que a STR vai montar.

**O que a plataforma usa (não gere):**
- **Objetos fixos exportados do Tesauro** — catálogo para a STC montar os ciclos recorrentes.
- **Mapeamento informação↔órgão** (§15) — **não existe hoje**; a **Alessandra vai montá-lo** (item a item), cruzando com o que há no SIMONI. É **pré-requisito do funil invertido** e a **fonte do MVP**. **[Em aberto]** se chega como atualização no Tesauro ou documento à parte.
- **Objetos variáveis** — a STC configura campos diretos e/ou uploads, exige ao menos um item e não
  gera planilha de preenchimento (§18 e §34).

> **Interoperabilidade preservada:** o Tesauro/Tema 3 continua sendo a **camada semântica** que padroniza o vocabulário (o motivo de não abrir mão dele — §17). A plataforma **respeita** essa camada, mas **não a administra**.
>
> *(Histórico da v7.0: previa-se uma “Etapa 2 — Gestão do Tesauro na plataforma”, com criação/edição de objetos refletindo no Tema 3. Descartada nas reuniões: a edição fica no Tema 3.)*

Objetos manuais ≈ **8 a 10** (a confirmar). Só os manuais geram ciclo.

-----

## 7. FLUXO 2 — COLETA E VALIDAÇÃO (PONTA A PONTA)

Fluxo central. Etapas com **dores** (D) e **funcionalidades** (F).

### Etapa 1 — Identificação da necessidade
(a) tema novo → Fluxo 1; (b) atualização → dispara ciclo. A provocação nasce da **STC**, que identifica a necessidade a partir do **mapeamento informação↔órgão** (§15). *(Na v7.0 a provocação vinha do SIMONI; no MVP o SIMONI está fora — §0.1.)*
- **D/F:** automatizar os objetos manuais; automação periódica (reenviar ciclo).

### Etapa 2 — Criação do ciclo *(revisto na v8.0)*
A STC cria o ciclo a partir do **mapeamento** (funil invertido — §16) e classifica o objeto como **fixo** ou **variável** (§18).
- **Objeto fixo:** referencia o modelo XLSX oficial versionado no Catálogo. **Objeto variável:** a
  STC configura campos diretos e/ou uploads, com ao menos um item e sem XLSX.
- **Anexos obrigatórios:** a STC define, por objeto, **quais anexos** são exigidos (ex.: contrato → cópia do contrato + processo licitatório); no upload aparece um **checklist**.
- **Destinatários** pré-selecionados (do mapeamento) e **editáveis** — por **adjunta/setor**. Mantém-se a **flexibilidade** de adicionar órgão fora do mapeamento — o sistema não autoriza, apenas **pergunta se ele fez**.
- **Toggle de validação do ponto focal (P2):** define se o envio **exige revisão do ponto focal** antes de ir à STC. **É por órgão** (P-020): cada UG tem o seu, e **UGs diferentes podem ter toggles diferentes no mesmo ciclo**.
- Escolha de **prazo** e **notificação** (e-mail no MVP).
- **É na aprovação que se libera o link do ciclo**, anexado ao SEI.
*(Na v7.0 a criação partia do TemaTres e previa “optar por não enviar metadado” no envio por boxes; no MVP o envio é por planilha — §0.1.)*

### Etapa 3 — Envio do ciclo (duas portas)
- **Ponto focal:** recebe **notificação** (e-mail) e entra por **login/painel** (Keycloak) — vê o ciclo inteiro.
- **Respondente técnico:** o **link do ciclo** é **anexado ao SEI** e enviado à UG; **qualquer pessoa da UG pode acessar** por ele. Quem não foi pré-cadastrado passa pelo **cadastro** (§10) e segue.

### Etapa 3.5 — Numeração (SEI)
Ciclo pode sair **sem** número; insere/edita depois (histórico). É na trilha B que o link é disponibilizado para o SEI.

### Etapa 4 — Recebimento e envio (órgão) *(revisto na v8.0)*
**Ponto focal:** notificação → login → **visão do ciclo inteiro** (todas as coletas/setores) → **pode responder ou apenas monitorar** → quando o toggle P2 está ligado, **consolida e dá ciência** antes de enviar à STC.
**Respondente técnico:** acessa a **coleta** pelo link do ciclo (cadastro na 1ª vez — §10) e responde
conforme o tipo: XLSX oficial e uploads no fixo; campos diretos e/ou uploads no variável.

**Envio dos dados (conforme o tipo de objeto):**
- **F:** no fixo, **download e upload do modelo XLSX oficial**; no variável, preenchimento de
  **campos diretos e/ou uploads**, sem planilha.
- **F:** **upload dos anexos obrigatórios**, com **checklist** dos exigidos; no MVP **basta haver o upload** (mesmo com título diferente) — a **correlação anexo↔linha** é melhoria futura.
- **F:** **registrar resposta negativa** (“não tenho a informação”) — estado próprio. **[Em aberto]** se por coleta inteira ou por linha (§28).
- **F:** **comprovante/recibo de envio** ao concluir *(requisito forte — SEDUC).*
- **F:** **coleta tipo Forms** — várias submissões; cada resposta é **cadastrada com a identificação do respondente técnico**.
- **F (checagem estrutural):** ao enviar, a plataforma confere a **estrutura do XLSX fixo** e a
  presença dos campos/uploads esperados. Coluna inteira, campo ou upload ausente segue para
  confirmação de não ocorrência; célula isolada vazia gera alerta.
- **Salvar rascunho + reenviar** permanece desejável (validado por SAF/SEDUC).
- **Chatbot / chat = melhoria futura** (§0.1).

> *(Histórico da v7.0 — descartado no MVP: envio por **boxes** — um box por metadado, trava por box, “quem responde primeiro trava o box”, ciclo fecha só com todos os boxes; e **verificador por IA** no envio. Tudo isso passa a **melhoria futura** — §0.1. A decisão “verificar × transformar” ficou resolvida em **verificar**: no MVP a IA nem entra; quando entrar, será **checador**, não conversor.)*

### Etapa 5 — Análise e verificação da STC *(revisto na v8.0)*
A STC **abre o arquivo** e confere **manualmente** o conteúdo; a plataforma já garantiu a **checagem estrutural** (anexos + estrutura da planilha). **Não** é veracidade (isso é a Etapa 6).
- **F:** **Aprovar/Rejeitar** o envio **com justificativa**; a rejeição **reabre a coleta/o envio** (ou a parte daquele setor) e volta ao órgão para correção. *(Na v7.0 rejeitava-se “item a item / reabre só o box”; sem boxes, a reabertura é da coleta/envio.)*
- **F:** **observações encadeadas** com **autor + data** (histórico); a UG vê na tela de correção e **reanexa** o arquivo corrigido.
- **Canal da correção — SEI sempre presente; a plataforma é caminho paralelo.** No SEI, o registro de rejeição/fechamento é **manual** da STC (a plataforma não cria despacho). O **chat** na plataforma é **melhoria futura (P-017)**; a via formal é **SEI/e-mail**. **Notificações: e-mail** (WhatsApp no futuro).

### Etapa 6 — Validação (veracidade)
Etapa **posterior e distinta**: avalia se a **informação é verdadeira**. *(Quem executa, dentro da STC, ainda a definir — §28.)*

### Fim do escopo
Após a validação, o ciclo encerra para os bolsistas. **Armazenamento e publicação** ficam de fora.

-----

## 8. CONCEITO CENTRAL E OS 4 PILARES

> **A plataforma é o centro. Os canais externos são só notificação/porta de entrada.**

|Pilar|Descrição|
|---|---|
|**Centralização**|A plataforma é o ambiente onde os dados são tratados e onde ocorre a resposta. O **SEI acompanha sempre** (caminho paralelo); a **comunicação/correção na plataforma** depende do canal em avaliação (P-017). Canais externos (SEI, e-mail, WhatsApp) e o link único são notificação/porta de entrada.|
|**Fidelidade estrutural**|Campos e fluxos espelham o **vocabulário do TemaTres**. O funil invertido garante que nenhum ciclo seja criado fora da estrutura institucional.|
|**Verificação humana + checagem assistida**|Verificação (formato/ortografia) e validação (veracidade) são **sempre humanas**. A IA **apoia como verificador/checador** (confere presença e formato, notifica) — **não transforma nem aprova/rejeita sozinha**.|
|**Rastreabilidade**|Cada órgão tem acompanhamento individual de status, **comprovante de envio** e histórico completo — tudo encadeado.|

-----

## 9. DECISÕES JÁ TOMADAS — NÃO REVERTER

> **Atualização v9.1:** as decisões vigentes (§34) **prevalecem** sobre os itens abaixo, redigidos
> antes. A entrada depende do tipo de objeto; o SIMONI fica fora; a identificação é contextual; o
> Tesauro preserva a proveniência e o Catálogo do Agiliza é a fonte operacional.

- Verificação e validação são **sempre humanas**; IA **apoia** (verificador/checador).
- A plataforma é o **centro** da resposta; o **SEI acompanha sempre** (caminho paralelo). A **comunicação/correção na plataforma** depende do canal em avaliação (P-017).
- Os campos seguem o **TemaTres**.
- **Escopo = coleta + validação.** Armazenamento e publicação ficam de fora.
- Stack **open-source, on-premise, custo zero** (PHP/Laravel).
- **Duas portas:** ponto focal por **login/painel**; **respondente técnico** pelo **link do ciclo** (anexado ao SEI, acessível a toda a UG). O ponto focal **pode responder ou monitorar** e é o **gerenciador** do ciclo do órgão.
- **Geração de link único por ciclo** (um só para todas as UGs, tipo Forms) **na aprovação do ciclo** (gate).
- **Ponto focal: 1 por órgão** (muda com o governo → **re-cadastro fácil**). **N respondentes técnicos por coleta.** Âncora natural do ponto focal: **controle interno/ouvidoria**. *(A v7.0 admitia mais de um ponto focal; hoje é um.)*
- **Identificação do respondente — RESOLVIDA (R3, híbrida):** ponto focal pré-cadastra **ou** o respondente se cadastra pelo link (validação por e-mail + senha; flag “criado pelo próprio usuário”). Novo ator: **respondente técnico** (§10).
- Autenticação institucional via **Keycloak**.
- **Entrada conforme o tipo de objeto** (§0.1): XLSX oficial e uploads no fixo; campos diretos e/ou
  uploads no variável; **salvar rascunho + reenviar**.
- **Comprovante/recibo de envio** ao concluir.
- **Canal de comunicação (chat) na plataforma — EM AVALIAÇÃO (P-017)**, não é decisão fechada. Se adotado: dúvidas/erros/correções na plataforma, no mesmo ciclo (sem novo despacho). Enquanto isso, via formal = SEI/e-mail. **Notificações: plataforma + e-mail ao responsável.**
- **Registrar resposta negativa** como estado próprio.
- **Mapeamento de órgãos por objeto não é estático** e **desce ao nível de adjunta/setor**.
- **Chatbot = melhoria futura** (pós-desenvolvimento, se houver tempo/necessidade).
- **Ranking** é a **última prioridade** (estímulo cultural; possivelmente público).
- **SEI sempre obrigatório** — todo ciclo tem processo no SEI (porta de entrada/formalização); a **resposta ocorre na plataforma** (caminho paralelo).
- **SIMONI fora do MVP** — sistema à parte, **não integrado**; a fonte é o **mapeamento** (§0.1). **Bitrix não será implementado.** *(A v7.0 previa integrar o SIMONI.)*

> **Ainda em aberto (v8.0 — ver §28):** coleta = **objeto+órgão × objeto+setor**; **P2 por órgão × por ciclo**; **resposta negativa por coleta × por linha**; **forma de chegada do mapeamento** (Tesauro × documento à parte). *(Já resolvidos: formato = verificar; identificação = R3; SIMONI = fora; Tesauro = fonte externa; envio = planilha; chat = futuro.)*

-----

## 10. PERFIS DE USUÁRIO E AS DUAS PORTAS DE ENTRADA

Três perfis: um do lado da STC e **dois do lado do órgão**.

> **Atualização v8.0 (P-016 resolvida):** identificação **híbrida (R3)** — ver Perfil 3. Há **três perfis**: STC, **ponto focal** (1 por órgão) e **respondente técnico** (N por coleta).

> **Atualização v9.0 — o perfil da STC subdivide-se internamente (§0.3.1).** O que abaixo se descreve como “Perfil 1 — STC” passa a ter **dois papéis internos**: um **Analista/criador** (cria, configura, edita e reenvia ciclos) e um **Aprovador/gestor** (revisa a criação, solicita ajustes ou **aprova** — só a aprovação libera o ciclo às UGs; ver o gate em §0.3.2). No protótipo eles se chamam **Analista STC** e **Especialista STC**; a reunião usou também **superintendente/STR**, **operador** e **especialista**. A **nomenclatura oficial e a eventual existência de um terceiro perfil “operador”** (mais simples, sem telas gerenciais) seguem **a confirmar (P-025)**. Ambos compartilham acompanhamento, histórico, registro e a validação das respostas das UGs. O **painel gerencial** é item futuro.

### Perfil 1 — Servidor da STC (solicitante/verificador)
Cria ciclos, monitora status, verifica formato/ortografia item a item, aprova/rejeita, dispara devoluções pelo **canal interno**, edita numeração SEI, acessa histórico/ranking, encaminha para validação. **Cadastra os pontos focais.** Autentica via **Keycloak**.

### Perfil 2 — Órgão / Ponto Focal (fixo dentro de um mandato)
Receptor institucional — **âncora natural: controle interno ou ouvidoria** (estruturas que já fazem triagem/devolutiva, confirmado por Ouvidoria e SAF). **Um por órgão** (muda com o governo), **notificado por e-mail**, entra por **login**, tem **visão do ciclo inteiro** (todas as coletas do órgão), é **gerenciador** do ciclo, **pode responder ou apenas monitorar** e **pode pré-cadastrar respondentes técnicos**. Quando o toggle **P2** está ligado, **consolida e dá ciência** antes do envio à STC.
- **Instabilidade real:** esse responsável **muda com a gestão/eleições** → **re-cadastro fácil** é requisito, não exceção.
- **Base institucional:** existe uma **IN** (agente de transparência, titular+substituto) — recuperar com **Stéferson**; ver conflito abaixo.

### Perfil 3 — Órgão / Respondente técnico (“dono da informação”) *(varia a cada coleta)*
Quem **efetivamente tem o dado** (ex.: o setor financeiro para BB Pago; o setor de compras para contratos; a TI da ouvidoria; um terceirizado da Progen). **Vê apenas as coletas** em que foi adicionado ou às quais chegou pelo link; **não precisa conhecer o conceito de “ciclo”**. **Cadastro híbrido (R3):** pré-cadastrado pelo ponto focal (nome+e-mail) **ou** auto-cadastro pelo link (nome/e-mail/telefone/cargo/órgão) + **validação por e-mail** + **senha**; nos próximos acessos, **e-mail+senha** (não se reidentifica). O sistema **marca “usuário criado pelo próprio usuário”** e **cruza órgão selecionado × preenchido**.

### O conceito do "bloqueio inicial" *(fundamenta a opção a)*
As planilhas de hoje travam o **preenchimento**, mas não têm o **bloqueio inicial** — a parte em que a pessoa se identifica e se vincula à UG. O modelo cria esse bloqueio: o ponto focal cadastra o respondente **pré-vinculado à UG certa**, sem dropdown. Isso **elimina o erro de vínculo** (IMA/IMA Sul; "funcionário X seleciona saúde"). Deixar a pessoa se auto-selecionar por lista "teria os mesmos erros do Forms".

### Conflito a reconciliar (ponto focal) — atualizado
As entrevistas convergiram num retrato mais nuançado: **existe um responsável interno em cada órgão** (SEDUC, SAF descrevem o papel), **mas ninguém quer assumi-lo formalmente** (SINFRA) e **ele muda com a gestão**. Ou seja, não é "existe × não existe", e sim **"existe, porém informal e instável"**. Recuperar a **IN** com Stéferson e desenhar para **troca frequente do responsável**. *(v8.0: a identificação ficou **híbrida (R3)** e surgiu o ator **respondente técnico**; o ponto focal é **um por órgão**.)*

-----

## 11. AUTENTICAÇÃO E ACESSO (DUAS CAMADAS + LINK ÚNICO)

- **Camada 1 — Keycloak/login:** servidores da STC e ponto focal (vínculo permanente).
- **Camada 2 — link do ciclo:** anexado ao **SEI** e acessível a **toda a UG**. O respondente técnico faz **cadastro na 1ª vez** (validação por e-mail + senha) e, depois, entra por **e-mail+senha**. Link **assinado, com validade e escopo** do ciclo; acesso **rastreável e encadeado**. *(A v7.0 tratava o link do ciclo como de uso exclusivo do respondente, sem conta; na v8.0 o respondente técnico cria conta.)*
- **Dissipação e reunificação:** ciclo (ao ponto focal) e link/SEI (à UG) podem chegar a pessoas diferentes, mas **ambos levam à mesma coleta**.

-----

## 12. NUMERAÇÃO SEI E CORRELAÇÃO COM O CICLO

- O **SEI** é o processo eletrônico (externo, desde **dez/2024**). O número nasce nele.
- Ciclo pode ser criado/enviado **sem** número; insere/edita depois (histórico).
- **O link do ciclo viaja pelo SEI** (substitui o antigo link de formulário). É o **único elo** SEI↔plataforma.
- **SEI sempre presente** e acompanha todo o ciclo; a plataforma é o **caminho paralelo de resposta**. A correção ocorre no **mesmo ciclo/processo** (sem novo despacho). Um **canal de comunicação na plataforma** para o vai-e-volta está **em avaliação (P-017)**.
- **Nada volta ao SEI automaticamente:** rejeição/fechamento geram, quando muito, **registro manual** da STC no SEI (a plataforma não cria despacho).
- **Dor central:** correlacionar o andamento do SEI com o ciclo sem desencontro.

-----

## 13. SIMONI E BITRIX — O PLANEJAMENTO ATUAL DA STC (CONTEXTO)

> **Atualização v8.0 — SIMONI FORA DO MVP.** Nas reuniões ficou decidido que o SIMONI **não será integrado** pela plataforma no MVP — é um **sistema operado à parte**. A **origem do ciclo** passa a ser a STC a partir do **mapeamento informação↔órgão** (§15). O conteúdo abaixo permanece como **contexto** do que a STC usa hoje.

> **(Talita):** o par **SIMONI + Bitrix** é o "topo do funil" da STC e **já funciona**. O SIMONI é **muito mais do que um monitor de prazos**. **⚠ O Bitrix NÃO será implementado nem integrado pela plataforma** — fica aqui apenas como contexto do que a STC usa hoje.

### 13.1. SIMONI — painel de monitoramento E catálogo operacional
Desenvolvido pelo **Leandro** (hoje sem responsável de banco dedicado; há "bugsinhos").
- **Função declarada:** monitora prazos — **atualizado / próximo / vencido** (vermelho ao vencer). **Não coleta** — **monitora e avisa** (~7 dias antes).
- **Na prática, cada item já carrega:** ID, nome, **seção**, **fonte**, **responsável** (STR/STI/Ambos), **tipo de processo** (Automatizado / Manual-BD / CMS / Cód / DA / GoogleDrive…), **tipo de dado** (PDF/Dados/Informações/Link/Planilha), **última/próxima atualização**, **frequência/prazo**, **instruções de Coleta** (inclusive **quais UGs notificar**) e um **Processo de Validação** passo a passo. Há um **"Help de Atualização"**.
- **Tabelas de apoio** (quase um esquema de metadados): ~35 **Tipos de Fonte**; ~46 **Seções**; Tipos de Processo; Tipos de Responsável (**STR** = transparência, **STI** = tecnologia).
> **Implicação:** cada item do SIMONI é **"um objeto com todos os seus metadados" + coleta + validação**. Base do Alerta §17.

### 13.2. Bitrix — gestão de tarefas *(contexto; não será implementado)*
Gestor de tarefas (tipo Bitrix24, **proprietário**): título, descrição, responsável, prazo, status, **projeto**, **observadores**, **chat por tarefa**, histórico, Kanban. **Sincronizado com o SIMONI**. **A plataforma não o integrará** — descrição mantida apenas como contexto do planejamento da STC.

### 13.3. Integração com o portal (parcial)
Itens de **e-SIC** e **ouvidoria** ligam-se ao **portal de dados abertos**, não ao da transparência (uns 6–7 itens não vêm direto).

-----

## 14. PNTP — A BASE DE TODOS OS ITENS

O **Programa Nacional de Transparência Pública (PNTP)** é a régua externa que estrutura o SIMONI.
- **O que é:** iniciativa da **Atricon** com **TCU e TCE-MT** (2022) para padronizar/induzir/fiscalizar a transparência ativa. Frentes: **Levantamento Nacional**, **Radar** e **Mês da Transparência** (18/nov).
- **Como avalia:** matriz por dimensões (Receita, Despesa, Licitações, Contratos, RH, SIC, Ouvidoria…). Critérios variam (~124 → ~176/2025 → ~181/2026), cada um **essencial/obrigatório/recomendado**, checados por **disponibilidade, atualidade (máx 30 dias), série histórica (≥3 anos), gravação, filtro**. Registro no **Sistema Avalia**.
- **Essenciais:** execução orçamentária/financeira. **Falhar um essencial impede transferências voluntárias/crédito** e perde a certificação.
- **Selos:** **Diamante 95–100% · Ouro 85–94% · Prata 75–84%**. O Maranhão persegue o **Diamante** (meta do secretário/governador — alavanca de adesão, confirmada pela SINFRA).
> **Por que importa:** a **periodicidade do SIMONI vem do PNTP** (despesa 30 dias; prestadores de saúde quinzenal). Pode **embasar a fórmula do ranking**.

-----

## 15. MAPEAMENTO DE ÓRGÃOS POR OBJETO — NÃO ESTÁTICO (E POR ADJUNTA)

- **Acordos de cooperação** — praticamente todos → ciclo amplo.
- **BB Pago** *(grafia a confirmar)* — só algumas UGs → ciclo restrito.
- **Obras** — historicamente na **Sinfra**, mas por decreto passaram a incluir a **Cegov** (e há obras de outras pastas). A composição muda por ato normativo.
- **Contrato compartilhado entre adjuntas (novo — Zezé):** um mesmo contrato alimenta **mais de uma adjunta** (ex.: R$ 50 mi usado 5–10 por uma, 20 por outra). O modelo precisa **ratear/exibir** isso.

**Conclusão:** o sistema **gere, por objeto, quais órgãos compõem cada ciclo** (todos/alguns), **sem ser estático** e **descendo ao nível de adjunta/setor**. Destinatários pré-selecionados e **editáveis**. Lembrete: **mapear não basta — o disparo precisa respeitar o mapeamento**.

> **Atualização v8.0 (pré-requisito do MVP):** esse **mapeamento informação↔órgão ainda não existe** de forma fiel — o SIMONI traz só algumas indicações e **não reflete a realidade** (ex.: “estagiários” aparece só como SEINC, mas vêm de mais órgãos). A **Alessandra vai montá-lo item a item** no Tesauro; é a **fonte do funil invertido** no MVP. **[Em aberto]** se chega como atualização no Tesauro ou documento à parte. Começa-se pela **informação/objeto**, não pelo órgão.

-----

## 16. LÓGICA DO FUNIL INVERTIDO

1. **Seleção da informação/objeto** — a partir do **mapeamento** (fonte do MVP) e dos **objetos fixos exportados do Tesauro**. Começa-se pela **informação**, não pelo órgão.
2. **Campos e uploads** — no **objeto fixo**, o ciclo referencia o modelo XLSX oficial; no
   **variável**, a STC escolhe campos diretos e/ou uploads, com ao menos um item e sem XLSX.
3. **Configurações finais** — órgãos sugeridos pelo mapeamento (**editáveis, por adjunta/setor**), **toggle de validação do ponto focal (P2)**, prazo/data, notificação (e-mail). **Aqui a configuração do ciclo é enviada para aprovação; quando aprovada, as coletas e o link do ciclo são gerados (o link é anexado ao SEI).**

*(Na v7.0 a fonte era a API do TemaTres e o envio previa “optar por não enviar metadado”; na v8.0 a fonte é o mapeamento e o envio é por planilha — §0.1.)*

-----

## 17. TEMATRES / TEMA 3 — MOTOR SEMÂNTICO E O ALERTA SIMONI × TESAURO

O **TemaTres** é o software indicado pelo **IBICT** para tesauros: **API REST** (JSON/XML), descritores prontos. **Objetivo:** padronizar o vocabulário — o órgão **não "digita o que quer"**, responde com base nos **descritores**. **Tema 3** = dicionário do governo federal, adaptação considerada **obrigatória** pela Alessandra. **Dependência bloqueante:** Fluxo 1 e 2 dependem do **servidor TemaTres entregar os primeiros termos**.

### ⚠ ALERTA ESTRUTURAL — O Tesauro é redundante com o SIMONI? *(a maior pergunta da consolidação)*

> **RESOLVIDO na v8.0.** A STC decidiu **manter o Tesauro** como **camada semântica e base de interoperabilidade** (Tema 3) e **não integrar o SIMONI** no MVP. Portanto: **Tesauro ≠ redundante** — é a leitura **(B) camada semântica**; e a redundância deixa de importar porque o SIMONI sai do caminho. A plataforma **consome** o Tesauro (objetos fixos exportados) e **não o edita**. A conversa com a Alessandra (abaixo) já ocorreu nas reuniões; o texto segue como registro do raciocínio.

- O **SIMONI** já é a **fonte viva** (metadados, periodicidade PNTP, instruções de coleta, validação).
- O **Tesauro/TemaTres** agrega o que o SIMONI não tem: **camada semântica** e **interoperabilidade com o Tema 3**.
- Construir gestão de Tesauro **paralela** ao SIMONI = **trabalho duplicado** (e recai sobre a Talita).

**Quatro leituras do "Tesauro" (a confirmar com a Alessandra):**
- **(A) Catálogo de itens** → **redundante** com o SIMONI.
- **(B) Camada semântica/terminológica** → **enriquece** o SIMONI (vocabulário padronizado que os 60+ órgãos usam de formas diferentes). O nome "Tesauro" sugere que esta pode ter sido a intenção.
- **(C) Rótulo que sobrou** de uma fase inicial.
- **(D) Motor de transformação de formato** *(relato via Enzo da intenção da Alessandra: "captar qualquer arquivo e transformar para o padrão")* → **complementar ao SIMONI** e **ligado ao ponto do formato** (§7). A forma **atual**, porém, é um **catálogo em planilha** (a planilha-modelo da SINFRA "foi criada pelo Tesauro").

> **Ação barata e decisiva:** conversa de ~15 min com a **Alessandra**: *"era para ser um dicionário de termos (semântico), um catálogo (operacional) ou um motor de transformação de formato?"*. **Bloqueante para a arquitetura do Fluxo 1** (e conecta-se ao formato). Levar como **pergunta**, não veredito.

-----

## 18. OS 4 OBJETOS DE TRANSPARÊNCIA — CATEGORIA PESSOAL (REFERÊNCIA)

Itens manuais; **referência concreta** dos metadados (exportados do Tesauro). **Terceirizados é o objeto mais problemático na prática** (SAF/Thiago).

> **Atualização v9.1 — objeto fixo × variável.** A STC classifica cada ciclo na criação. **Fixo:**
> referencia modelo XLSX oficial e versionado no Catálogo, com os uploads configurados.
> **Variável:** contém campos diretos, solicitações de upload ou ambos, exige ao menos um item e não
> gera XLSX.

- **MT-0015 — Trabalhador Terceirizado.** Mensal (até 10º dia útil). XLSX. Vedado CPF/endereço/sensíveis. Campos: Empresa, CNPJ, Nº do Contrato, Objeto, Nome do Trabalhador, Função, Unidade de Lotação, Qtd., Valor Contratual Global, Exercício, Data de Atualização, Fonte Oficial. *(Caso: Função/Lotação em branco → obrigatórios.)*
- **MT-0016 — Estagiário.** Mensal. XLSX. Campos: Nome, Órgão, Unidade, Função, Tipo de Estágio, Instituição, Início/Término, Valor da Bolsa, Exercício, Data de Atualização, Fonte.
- **MT-0040 — Tabela de Cargos e Remuneração.** Sob evento. Formato variável. Campos: Cargo/Função, Nível, Vencimento, Gratificações, Remuneração Total, Base Legal, Vigência, Data de Atualização, Fonte.
- **MT-0041 — Concurso/Processo Seletivo.** Sob evento (inclui PSS/temporária). Campos: Nº do Edital, Modalidade, Cargo, Vagas, Abertura/Encerramento, Situação, Documentos (upload), Link, Data de Atualização, Fonte.

> **Domínio de obras/contratos (SINFRA) — modelagem específica:** **contrato → empenho → OS → medição (via "SAFE") → pagamento**; **aditivos** (prazo/valor) ao longo do tempo; **contrato compartilhado entre adjuntas**; **medições** com planilha licitada + relatório fotográfico; risco de **duplicidade** (OS/medição) → **pagamento em dobro → Tribunal de Contas**.

-----

## 19. STATUS DAS SOLICITAÇÕES / CICLOS

|Status|Cor|Condição|
|---|---|---|
|**Enviada**|Verde|Todos os dados enviados dentro do prazo|
|**Aberta**|Azul|Faltam dados, mas dentro do prazo|
|**Parcial**|Amarelo|Prazo terminou e só parte foi enviada|
|**Não enviada**|Vermelho|Prazo terminou e nada foi enviado|
|**Fechada**|Roxo|Encerrada|

Status em **tempo real**, no histórico (STC e órgão). **“Respondeu que não tem”** (resposta negativa) é estado próprio, distinto de “não enviada”.

> **Atualização v8.0 — máquina de estados (Ciclo × Coleta).** Com a hierarquia nova, há **dois níveis**:
> - **Coleta / envio do respondente técnico:** `pendente` → `preenchendo/rascunho` → `enviado` (aguardando checagem) → `em correção` (rejeitado, reaberto) → `aprovado`. Estados próprios: **`resposta negativa`** (“não tenho a informação”) e **`não enviado no prazo`**.
> - **Ciclo (visão da STC/ponto focal):** agrega as coletas — `ativo/aberto` → `respondido` (há submissões) → `em correção` → `finalizado` (com comprovante). Com o toggle **P2** ligado, há um passo **`aguardando validação do ponto focal`** antes de chegar à STC.
> A tabela de cores acima (nível ciclo) permanece; **[em aberto]** se a **resposta negativa** é por coleta inteira ou por linha (§28).

> **Atualização v9.0 — gate de aprovação e ciclo de vida do ciclo (§0.3.2 e §0.3.4).** **Antes** dos estados operacionais acima, o ciclo passa por um **gate de aprovação da criação**: `aguardando análise` → `ajustes solicitados` (devolvido ao criador) → `aprovado`. Só o **aprovado** gera as coletas e o link do ciclo e entra nos estados operacionais. Além disso, a reunião pediu um **ciclo de vida do ciclo** mais rico (`criado` → `enviado` → `em andamento` → `atrasado` → `finalizado`), com **encerramento gerando relatório** de quem enviou/não enviou/declarou não ter, **múltiplos SEI por reiteração** (mesmo link do ciclo) e **novo ciclo** para recomeços (com relação ao anterior). **Não há encerramento automático** (encerra sempre a STC); só a **prorrogação de prazo** fica no backlog. O **nº do SEI** pode ser informado a qualquer momento. Esse ciclo de vida faz parte do **fluxo de gestão do ciclo** (§0.3.3), ainda a desenhar. *(No protótipo, os estados do ciclo são só `em-andamento`/`finalizado`/`sem-envio-no-prazo`, com “atrasada” derivada; o resto é refinamento.)*

> **Status específicos de obras (SINFRA):** além dos genéricos, o objeto obras precisa distinguir **paralisada** (formal, com ordem de paralisação — ex.: Atins), **parada** (informal — ex.: problema sanitário) e **aguardando pagamento**. E **detectar duplicidade** de OS/medição.

-----

## 20. CAMADA TRANSVERSAL

1. **Histórico e status em tempo real** — todos os ciclos, com filtros; **ver/acessar/acompanhar** o que já foi enviado. É onde se **edita o número SEI** e se acompanha **devolução/reenvio**. Ponto focal vê o histórico do seu órgão; STC vê todos.
2. **Canal de comunicação interno (humano) — EM AVALIAÇÃO (P-017).** Respondente/ponto focal ↔ STC na plataforma, para dúvidas, avisos de erro e correções. É a **demanda nº 1 da ponta**, mas a **adoção na plataforma ainda não é decisão fechada**; enquanto isso, a via formal é o **SEI/e-mail** (o SEI acompanha sempre). **Não é chatbot.**
3. **Comprovante de envio** — recibo ao concluir, para o órgão e registro para a STC.
4. **Notificações** — central para a STC (pendências, inconsistências), **avisos ao ponto focal** (novo ciclo) e **lembretes de prazo**; no MVP por **e-mail** (WhatsApp/API no futuro).
5. **Onboarding por mapeamento** — apresentar a cada órgão **o que a STC precisa dele** (insight da Camila), reduzindo destinação errada.
6. **Feedback da STC** — sinalizar "recebido / faltou X / precisa de mais".
7. **Ranking da Transparência** — painel gamificado, visível para STC e órgão; **estímulo cultural** (pódio por objeto; possível exposição pública, com cautela). **Prioridade: por último.** Fórmula pode ancorar no **PNTP**.
8. **Capacitação/onboarding** — os **cursos mensais da STC funcionam** (SAF); o produto deve ser simples o bastante para apoiá-los.

-----

## 21. ESTADO ATUAL DO PROJETO

- **Protótipo anterior (Maranhão Transparente, Lovable):** referência funcional (login, funil invertido com os 4 objetos, histórico, painel do órgão, tela de resposta, verificação item a item, reenvio, ranking). **Falhou por baixa adesão**, não por tecnologia. Sobre stack antiga.
- **Entrevistas STC (4):** Thiago, Matheus, Fernando, Talita (Alessandra em momento anterior).
- **Entrevistas UGs (5, em 4 órgãos + DETRAN/PM):** Camila/SEDUC, Fernando+equipe/Ouvidoria-Fazenda, Jaldo/SINFRA-CAGE, Zezé+Joaquim/SINFRA-contratos, Guilherme/SAF; **DETRAN e PM** ouvidos na sequência. **1ª rodada encerrada** (restam órgãos + **TI da ouvidoria**, para o desenvolvimento).
- **Pesquisa concluída:** PNTP; leitura das telas de SIMONI/Bitrix.
- **Protótipo visual do MVP 1.0 CONSTRUÍDO** (React/TS, front-end only, auditado e publicado no GitHub) — cobre o fluxo da coleta ponta a ponta, o gate de aprovação e o catálogo do Tesauro. Ver `andamento_do_prototipo.md`.
- **Fase:** **validar o MVP/requisitos com a STC e refinar o protótipo**, antes do MVP com backend.

**Ainda NÃO implementado (rumo ao MVP com backend):** backend real; Keycloak/autenticação; persistência/armazenamento; geração/gestão reais de links; notificações reais (e-mail); correlação SEI↔ciclo; domínio de obras/contratos; testes de usabilidade. **No protótipo, mas simulado:** duas portas, comprovante, checagem estrutural, consumo do catálogo do Tesauro, cadastro híbrido — tudo em estado local. **Decidido mas ainda NÃO no protótipo (refinamento — §0.3):** fluxo de gestão do ciclo, múltiplos SEI/reiteração, encerramento com relatório, dupla saída da não ocorrência. O **mapeamento informação↔órgão** segue inexistente (P-022).

> **Atualização v9.1:** verificador por IA, boxes genéricos, chat interno e integração com o SIMONI
> ficam fora. O foco é a coleta conforme o tipo de objeto, com checagem estrutural e validação
> humana.

-----

## 22. ARQUITETURA TÉCNICA (STACK OFICIAL — OPEN-SOURCE, ON-PREMISE)

**Princípio da economicidade (inegociável):** custo zero de licenciamento; tudo open-source; on-premise. Diretriz: **microsserviços + PostgreSQL + Docker + GitLab + Keycloak**.

```
Backend & Dados   → PHP 8.1/8.2 · Laravel 10/12 · PostgreSQL (padrão v17)
Front-end         → Tailwind CSS (novo, autorizado) · Bootstrap (legados/portal)
Infra / DevOps    → Docker + Portainer · Gateway Traefik v3.6 · GitLab (repo interno)
Segurança         → Keycloak 23 (IAM/SSO) · link/token assinado para respondentes sem conta
OCR / leitura     → Tesseract (imagens) + parsing estruturado (planilhas)
Integração Tesauro→ TemaTres / Tema 3 via API REST (JSON/XML)
Automação         → N8N (Docker). SIMONI e Bitrix **fora do MVP** (não integrados).
```

> **OCR vs parsing:** Tesseract lê **texto** bem, mas é fraco em **estrutura de tabela**. Para XLSX fixo, "conferir se segue o modelo" é **parsing estruturado** (leitura contra schema), não OCR. **Imagem → OCR; planilha → parsing.** No MVP, a checagem é **estrutural** (presença de anexos + conformidade da planilha); o **verificador por IA** (§7) é **melhoria futura**.
> **⚠ Nota:** análises externas sugeriram Node/Python — **ignorar**: a stack é **PHP/Laravel**.
> **⚠ Infra frágil:** o Estado passou por **crise de TI** (portal caiu, plantão de fim de semana). Planejar resiliência/observabilidade no on-premise.

-----

## 23. MODELAGEM DE DADOS (ESBOÇO RELACIONAL — PostgreSQL)

```
usuarios     (id, nome, email, perfil['stc'|'orgao_ponto_focal'], orgao_id?, adjunta_id?, ativo)
orgaos       (id, nome, sigla)
adjuntas     (id, orgao_id, nome)                                                   -- mapeamento desce a este nível
setores      (id, adjunta_id?, orgao_id, nome)
objetos      (id 'MT-xxxx', nome, categoria, ciclo, formato, automatizado bool, fonte_tematres)
metadados    (id, objeto_id, label, tipo, obrigatorio_padrao, descricao)             -- origem: TemaTres
objeto_orgao (objeto_id, orgao_id, adjunta_id?, autorizado bool)                     -- Fluxo 1 (não estático, por adjunta)
ciclos       (id, titulo, objeto_id, criado_por, criado_em, prazo, plataforma_notif,
              numero_sei?, link_token, status, observacoes)                            -- token único e estável por ciclo
ciclo_orgao  (id, ciclo_id, orgao_id, adjunta_id?, status, resposta_negativa bool, respondido_em?)
respondentes (id, ciclo_orgao_id?, orgao_id, tipo['pessoa'|'equipe'], nome, email, cadastrado_por?)
acessos_link (id, ciclo_id, token, respondente_id?, identificacao, criado_em, ultimo_acesso?)
boxes        (id, ciclo_orgao_id, metadado_id, status['pendente'|'rascunho'|'enviado'|
              'verificado'|'rejeitado'|'devolvido'], resposta?, arquivo_url?, captura?,
              verificacao_ia?, enviado_por?, motivo_rejeicao?, travado bool)
comprovantes (id, ciclo_orgao_id, gerado_em, hash)                                   -- recibo de envio
mensagens    (id, ciclo_orgao_id, autor, destino, texto, criado_em, lida)            -- canal interno (P-017, a confirmar)
historico    (id, ciclo_id, acao, autor, timestamp, detalhes)
notificacoes (id, destinatario_id, canal['plataforma'|'email'], tipo, mensagem, lida, criado_em)
ranking      (ciclo_id, orgao_id, pontos, envios, rejeicoes, tendencia)              -- fórmula: ancorar no PNTP
-- domínio de obras/contratos (SINFRA):
contratos    (id, numero, objeto, valor_global, orgao_id)
contrato_adjunta (contrato_id, adjunta_id, valor_uso)                                -- contrato compartilhado
aditivos     (id, contrato_id, tipo['prazo'|'valor'], detalhe, data)
medicoes     (id, contrato_id, numero, valor, os_ref, sei_ref, status_obra['andamento'|
              'paralisada'|'parada'|'aguardando_pagamento'], duplicidade_flag bool)
```

> **Atualização v9.1 do modelo — Ciclo × Coleta + respondente técnico.** Um ciclo tem N coletas e
> um link público estável. A coleta registra o tipo e referencia `modelo_xlsx_versao_id` somente no
> fixo; a resposta variável persiste campos diretos e uploads. Ausência total e não ocorrências
> parciais são registros distintos. O modelo físico definitivo permanece responsabilidade da
> implementação funcional.

> Como o **SIMONI está fora do MVP**, não é preciso espelhar suas entidades agora; ainda assim, definir com a STI qual sistema é **fonte de verdade** por entidade (item, UG, ciclo) antes de evoluções futuras.

-----

## 24. REQUISITOS FUNCIONAIS

> **Fonte vigente de requisitos:** [regras de negócio](regras-de-negocio.md) e o índice de
> [funcionalidades](funcionalidades/README.md), ambos relacionados ao backlog ativo. O
> `SRS_Agiliza_Transparencia_v2` e os mapas de etapas abaixo são evidências históricas e não
> definem o recorte da V1 mínima.

- ~~**Etapa 0 · Edição do Tesauro**~~ — **removida na v8.0** (Tesauro é fonte externa, sem edição na plataforma). RF-001/RF-002 saem do escopo.
- **Etapa 1 · Criação do ciclo:** RF-003, RF-004, RF-005
- **Etapa 2 · Identificação e envio:** RF-007 a RF-016, RF-029 *(RF-009/RF-010 condicionais a P-016)*
- **Etapa 3 · Recebimento e verificação:** RF-020, RF-021, RF-022, RF-040
- **Etapa 4 · Correção e reenvio:** RF-023, RF-024 *(granularidade condicional a P-003)*
- **Etapa 5 · Validação e encerramento:** RF-025, RF-026
- **Domínio de obras e contratos:** RF-032 a RF-035
- **Transversais:** RF-006, RF-017, RF-018, RF-019, RF-027, RF-028, RF-030, RF-031, RF-036, RF-037, RF-038, RF-039

**Reconciliação com a lista antiga deste contexto (o que mudou):**
- O **canal de comunicação** (antes um RF fechado) é agora **pendência P-017** — RF-018/RF-019 dependem dela.
- A **identificação do respondente** é **pendência P-016** — RF-009/RF-010.
- A **transformação de formato** é **condicional a P-001** (verificar × transformar).
- **Autenticação/perfis (RF-038)**, **exportação (RF-039)** e **OCR com confirmação (RF-040)** foram explicitados no SRS.
- **v9.1:** entrada por tipo de objeto; **SIMONI fora**; Tesauro como proveniência e Catálogo como
  fonte operacional; verificação humana + checagem estrutural; ciclo×coleta, respondente técnico e
  toggle focal por UG.


-----

## 25. DIAGNÓSTICO E HIPÓTESE DE REPOSICIONAMENTO (A VALIDAR)

> Hipótese de trabalho, não decisão. Reforçada pelas entrevistas da ponta.

- **Causa raiz transversal:** a maior parte das dores **não vem da ausência de um Tesauro** — vem da **ausência de uma camada de gestão do processo de coleta** (workflow, prazos, padronização de entrada, **comunicação/feedback**, notificação).
- **Problema em 3 partes:** **(1)** catalogação operacional → **já no SIMONI**; **(2)** **gestão do ciclo de coleta + comunicação** → **maior lacuna, não resolvida hoje**; **(3)** padronização semântica → **possível papel real do Tesauro** (interpretação B/D, §17).
- **Lacunas do SIMONI = oportunidade:** canal de entrada guiado; **verificação automática no envio**; **comunicação/feedback na plataforma**; comprovante; indicadores por UG; notificação automática.
- **Hipótese de reposicionamento:** tratar o trabalho da dupla como **camada de gestão de coleta + verificação assistida** que **se integra** ao SIMONI (o **Bitrix não será implementado**) — em vez de recriar o Tesauro como catálogo paralelo. **Condicionado** à conversa com a Alessandra (§17).
- **MVP mais defensável:** **coleta guiada por UG** (duas portas + planilha + comprovante), com **notificação de prazo**, atacando as etapas 1–4 do as-is.

> **Atualização v8.0:** a hipótese central **se confirma** — o valor está na **camada de gestão da coleta** (workflow, comprovante, correção, histórico). Muda a **execução:** **sem integrar o SIMONI** e **sem gerir o Tesauro** na plataforma (ambos externos); a fonte é o **mapeamento** (§0.1).

-----

## 26. IDENTIDADE VISUAL

- **Nome:** Agiliza Transparência. **Posicionamento:** *"Com o Agiliza Transparência, a transparência não espera."*
- **Paleta:** azul escuro #1A3A5C, azul médio #2E75B6, azul claro #D5E8F0, branco, cinza claro.
- **Estilo:** institucional governamental, moderno e limpo. Cards, listas, badges de status, ícones simples. **Visual e didático** ("os órgãos não leem") — menos texto, etapas claras.
- **Cores dos status:** Enviada #1A7A3A · Aberta #185FA5 · Parcial #F0A500 · Não enviada #B71C1C · Fechada #5B21B6.
- **Cores do ranking:** 1º #FAC775/#633806 · 2º #B5D4F4/#0C447C · 3º #C0DD97/#27500A.

-----

## 27. PESSOAS-CHAVE E ENTREVISTAS *(atualizado)*

|Pessoa|Papel|Status|
|---|---|---|
|**Thiago**|Auditor-chefe / engenheiro da auditoria; **substituiu o Fernando**|Entrevistado (operacional/SEI). Caso IMA/IMA Sul; conta de adiantamento; paralisada×parada.|
|**Talita**|Operação/coleta e SIMONI|Entrevistada. Bitrix+SIMONI, PNTP, bloqueio inicial, alerta Tesauro×SIMONI, bus factor.|
|**Matheus**|Coleta → **migrou para a TI**|Entrevistado. Ausência de sistemas centralizados, caso Sinfra, SEGEP×FAPEMA.|
|**Fernando (STC)**|Estratégico/gestão — **transferido de área** (Thiago o substitui)|Entrevistado. Cultura, 4 princípios, IN, ancorar em ouvidorias, Tema 3.|
|**Patrick**|Contato da STC (dúvidas)|Citado pela SAF; **mapear o papel**.|
|**Alessandra**|Gestão da informação / Tesauro|**Conversa pendente e bloqueante:** intenção do Tesauro (semântico × catálogo × transformação — §17).|
|**Stéferson**|Coordenação/normativo|Detém a **IN** do ponto focal; alinhamento chefe a chefe (caso obras).|
|**Antônio / STI**|Infraestrutura (**STI = área de TI interna da STC**)|**A alinhar:** APIs do SIMONI/Bitrix, infra on-premise, Keycloak, segurança do acesso externo.|
|**ATI — Agência Estadual de Tecnologia da Informação do MA**|Identidade externa — opera o **SEI** (login + banco, **CPF+senha**)|**A contatar:** API para **validar credencial** (login do SEI) ou **consultar CPF** (nome/órgão/lotação), alimentando/identificando no Agiliza. *(Agência externa à STC; não confundir com a STI.)*|
|**Leandro**|Dev do SIMONI|Contexto técnico do SIMONI.|
|**Camila**|SEDUC (superintendente)|**Entrevistada.** Comunicação/comprovante, padronizar planilha, onboarding por mapeamento, volume.|
|**Fernando (ouvidoria/Fazenda) + Cláudia**|Ouvidoria|**Entrevistados.** Dependência da TI, formato ok, sigilo. **TI: questionário enviado, aguardando.**|
|**Jaldo**|SINFRA/CAGE (terceirizado Progen)|**Entrevistado.** Playbook de obras, medições, duplicidade, paralisada×parada, formato inviável.|
|**Zezé + Joaquim**|SINFRA/contratos|**Entrevistados.** Modelo de contrato, aditivos, contrato compartilhado, crise de TI.|
|**Guilherme**|SAF (controle interno/ouvidoria)|**Entrevistado.** Opção (a) e erro de UG, canal direto, salvar rascunho, banco não organizado.|

**Método de validação:** com o **órgão**, extrair a dor e **testar o conceito sem explicar**; com a **STC**, confirmar e aprofundar. **Confirmar (residual):** **SAF = Agricultura Familiar**; lotação do Fernando-ouvidoria. *(Resolvidos: Fernando-STC foi transferido de área; a grafia é Alessandra, uma só pessoa.)*

-----

## 28. PENDÊNCIAS E QUESTÕES EM ABERTO

> A fechar na **reunião de consolidação com a STC** e com a **Alessandra/STI**. Numeração alinhada ao SRS (**P-001 a P-018**).

**Legenda:** ✔ resolvida/direcionada na v8.0 · ⏳ segue aberta (próxima reunião).

- ✔ **P-001 — IA: verificar × transformar.** **Resolvido: verificar.** No MVP a verificação é **manual (STC) + checagem estrutural**; a IA (checador de formato) é **futura**. Transformar está descartado.
- ✔ **P-002 — Usar o Tesauro?** **Resolvido: sim, como fonte externa** (Tema 3), **sem edição na plataforma**. Objetos fixos exportados do Tesauro.
- ✔ **P-003 — Método de entrada.** **Resolvido por tipo:** XLSX oficial e uploads no fixo; campos
  diretos e/ou uploads no variável.
- ✔ **P-004 — Login × link.** **Resolvido:** ponto focal por **login/painel**; respondente técnico por **link do ciclo** (anexado ao SEI, acessível a toda a UG) + cadastro.
- ✔ **P-005 — Conta individual × do setor.** **Direcionado:** conta **individual** do respondente técnico (validação por e-mail + senha; flag “criado pelo próprio usuário”). Vários respondentes por coleta.
- ✔ **P-006 — Segurança do link.** **Direcionado:** token/escopo do **ciclo**; respondente cria conta na 1ª vez.
- ✔ **P-007 — Ranking: implementa? público?** **Direcionado: futuro** (fora do MVP).
- ✔ **P-008 — Fórmula do ranking.** **Futuro** (pode ancorar no PNTP).
- ⏳ **P-009 — Prazos e datas fixas.** A definir (data fixa por objeto, à moda do “dia 10” das obras).
- ⏳ **P-010 — Validador de veracidade** (quem executa na STC) — Etapa 6, ainda a definir.
- ✔ **P-011 — Colaboração em tempo real no mesmo box.** **Resolvido: não se aplica** (sem boxes; coleta tipo Forms com N submissões).
- ⏳ **P-012 — Sigilo / segurança fiscal** (dados sensíveis) — a tratar.
- ⏳ **P-013 — Limites de upload** — a definir (anexos por linha podem gerar volume).
- ⏳ **P-014 — Domínio de obras** (medições, duplicidade, paralisada/parada, aditivos, contrato compartilhado) — pós-MVP.
- ✔ **P-015 — Integrações (SIMONI/SEI/TemaTres).** **Resolvido para o MVP: SIMONI fora** (à parte); **SEI** só pelo **link do ciclo anexado**; **Tesauro** consumido como fonte externa. Bitrix fora.
- ✔ **P-016 — Identificação do respondente.** **Resolvido: híbrido (R3)** + ator **respondente técnico**.
- ✔ **P-017 — Chat na plataforma.** **Direcionado: futuro** (estilo comentário do Google Docs, ancorado ao item). Via formal = SEI/e-mail; notificação por e-mail (WhatsApp futuro).
- ✔ **P-018 — Retenção do histórico.** **Direcionado:** guardar **observações/encadeamento** e **provavelmente só o arquivo final** (não toda versão rejeitada).

**Novas pendências das reuniões (a fechar):**
- 🔄 **P-019 — Coleta = objeto+órgão × objeto+setor?** **Avançou (v9.0):** o protótipo e a reunião trabalham com **1 coleta = 1 objeto, por órgão**, com distribuição interna entre setores via ponto focal (link único; vários pedidos = vários ciclos). A questão órgão × setor **não fechou formalmente**, mas a operação está desenhada por-órgão-com-distribuição-interna.
- ✔ **P-020 — Toggle de validação do ponto focal (P2): por órgão × por ciclo?** **DECIDIDO: por órgão.** Cada UG tem o seu; **UGs diferentes podem ter toggles diferentes no mesmo ciclo**. *(O protótipo aplica por ciclo — ajustar para por órgão é refinamento.)*
- 🔄 **P-021 — Resposta negativa: por coleta inteira × por linha/campo?** **Avançou (v9.0):** virou **“Declaração de não ocorrência”** com **duas saídas** (não tem a informação × não tem atualização), pela **coleta**, passando pelo ponto focal (§0.3.5). A **granularidade** linha/campo segue futura/aberta.
- ⏳ **P-022 — Como chega o mapeamento informação↔órgão:** atualização dentro do Tesauro × documento à parte. **Segue aberto** — Alessandra vai montá-lo item a item; DETRAN/PM reforçaram que ele muda (PM licitações → adjunta).

**Pendências surgidas do protótipo/Tesauro (v9.0):**
- ⏳ **P-023 — Justificativa de anexo faltante** não destrava o envio no protótipo — confirmar o comportamento desejado.
- ⏳ **P-024 — Contradições e versionamento do Tesauro:** `MT-0011`/`MT-0049` (fluxo manual × nota de automação); versão do arquivo (`v2_3`) × instruções internas (**v2.2**); instrução de sequência (novos a partir de MT-0049) × arquivo que já traz MT-0049. Até confirmar, segue-se a coluna **Fluxo de Origem**. *(19/10/2026: a v2.3 saiu do acervo, substituída pela v2.6; a divergência de versão persiste nela — nome v2.6 × aba “Instruções” v2.5.)*
- ⏳ **P-025 — Nomenclatura e nº de perfis internos da STC:** confirmar os nomes oficiais (Analista/Especialista × superintendente/STR/operador) e se haverá um terceiro perfil “operador” (mais simples, sem telas gerenciais). Ver §0.3.1.

**Pendências levantadas na revisão do protótipo (v9.0):**
- ✔ **P-026 — Objeto fixo: pode alterar campos obrigatórios? SUPERADO.** O ciclo apenas referencia o
  modelo XLSX oficial e versionado do Catálogo; não monta nem altera sua estrutura.
- ⏳ **P-027 — Objetos automatizados na plataforma:** os 8 automatizados **ficam fora da criação** (consenso); os **metadados/campos obrigatórios** deles entram como **referência/futuro** ou não? *Lean:* manter os metadados no catálogo (baixo custo, referência e futura integração), excluídos da criação — como o protótipo já faz.
- ⏳ **P-028 — Armazenamento (transição protótipo → MVP):** o protótipo guarda **tudo em código/memória**; no MVP, dados transacionais (ciclos, coletas, respostas, arquivos) vão para **banco** (§22-23, Postgres). O **Tesauro** fica em **banco** (importado pelo gerador, atualizável sem redeploy, coerente com “fonte externa/não estática”) ou permanece **versionado em código**? *Lean:* banco para o MVP, com o script de geração virando pipeline de importação.
- ⏳ **P-029 — Sinalização da UG à STC (contestação/encaminhamento):** ao receber um ciclo, a UG poder **sinalizar** que talvez não tenha a informação / **pedir alteração**, e **apontar qual outra UG** tem aquele dado (ex.: pedido foi ao Batalhão 8, mas a informação é do Batalhão 20). O **reencaminhamento à UG correta após uma não ocorrência já está confirmado** (a STC edita o ciclo — ver §0.3.5); **em aberto** fica o **escopo de um canal de sinalização mais amplo** (contestar o pedido em si, fora da não ocorrência) e se ele entra no **MVP**. **Alto valor:** alimenta a correção do mapeamento (P-022/§15).
- ✔ **P-031 — Reaprovação após ajuste da STC: SUPERADO.** Não existe gate por perfil Especialista;
  mudanças estruturais pertencem à auditoria do ciclo e não reabrem respostas validadas.
- ✔ **P-032 — Rejeição de não ocorrência: RESOLVIDO.** A STC registra ciência e não rejeita a
  declaração; persistência, justificativas e correção permanecem em P-053.
- ⏳ **P-030 — Identificação por CPF via API (base de servidores):** usar **CPF** contra uma **base existente de todos os servidores das UGs** (via API) em vez de login e-mail/senha. **Robustece a identificação, reduz fraude de autocadastro e pré-preenche o cadastro.** Evolui P-016 (hoje R3/híbrido) e a autenticação (§11/§22). **Depende de:** confirmar acesso/propriedade da base — concretamente o **login/banco do SEI (CPF+senha), operado pela ATI** (Agência Estadual de TI do MA), com **STI/Antônio** coordenando pela STC —, **LGPD/autorização** e um **fallback** para quem não está na base (terceirizados/adjuntas). *Lean:* perseguir, com Keycloak podendo federar/consumir essa base como fonte de identidade. Desenho detalhado (Sanctum+RLS, CPF, cenários da ATI): `docs/ideia de login.md`.

**Ações operacionais que destravam (não são decisão de produto):**
- ✔ **Escolher o objeto-piloto** — **resolvido em 16/10/2026:** MT-0018 com a SINFRA (UG 531010) como única destinatária; ver a [decisão de escopo](decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md).
- ⏳ **Lista da Alessandra (UGs × objetos fixos)** — é o insumo de P-022; segue pendente e bloqueia a pré-seleção de UGs na criação.
- ✔ **Divergência técnico × levantamento (era ação pendente):** com os dois documentos disponíveis, a divergência foi identificada — sigilo (SRS mantém, técnico removeu), obras (SRS modela, técnico trata como envio por área) e P-012. Ambos estão defasados frente à v8.0/v9.0 e serão **realinhados**.

**Pendências de implantação da V1 (19/10/2026):** perguntas à STC e à TI que não bloqueiam o piloto,
mas precisam de resposta antes do uso real ou da ampliação. Os códigos são os do repositório da
aplicação, em [`agiliza-stc/specs/open-decisions.md`](../../agiliza-stc/specs/open-decisions.md), e
não se confundem com a numeração acima.
- ⏳ **Contas STC de produção** (`agiliza-stc` P-002) — quem pode pedir uma conta e como se recupera o acesso. Hoje a conta é criada por comando técnico.
- ⏳ **Rascunhos de outras pessoas da UG** (`agiliza-stc` P-008) — depois que a UG responde, manter, deixar o dono apagar ou descartar os rascunhos não enviados.
- ⏳ **Hospedagem, operação e cópias de segurança** (`agiliza-stc` P-009) — onde a V1 roda, quem a opera e qual a rotina e a retenção das cópias. Responsáveis esperados: TI da STC e Guilherme.
- ⏳ **Varredura dos arquivos recebidos** (`agiliza-stc` P-010) — se os arquivos das UGs passam por antivírus antes de a STC baixá-los. Hoje não há varredura.
- ⏳ **Dados das planilhas no banco, após a V1** (`agiliza-stc` P-011) — se as linhas dos XLSX enviados entram no banco para consulta e relatório. Hoje ficam guardadas só como arquivo.

> **Dependências/ações que independem de novas UGs:** conversa com a **Alessandra** (P-002); **APIs e infra** com **Antônio/STI** (P-015); **TI da ouvidoria** (questionário — respondente real de vários dados); confirmar nº de objetos manuais (“8 a 10”) e de órgãos (“60+”). *(A IN do ponto focal não será mexida nesta fase.)* *(v8.0: P-002 e o Alerta §17 já resolvidos; a ação-chave com a Alessandra passa a ser **montar o mapeamento informação↔órgão** — P-022.)*


-----

## 29. HIPÓTESES DO PROJETO

- **H1:** Centralizar numa plataforma única reduz o tempo de coleta e conferência.
- **H2:** Campos servidos pelo TemaTres garantem formato/tipo corretos, reduzindo reenvios.
- **H3:** Verificação e validação humanas, com interface clara item a item, preservam a confiabilidade sem comprometer a agilidade.
- **H4:** Fazer o ciclo chegar primeiro ao ponto focal (porta autenticada) e dar ao respondente um link direto (porta leve) **com identificação prévia** reduz a perda de solicitações e o erro de vínculo de UG.
- **H5:** Como o gargalo é cultural, **fricção mínima + recorte do processo existente + comunicação/feedback + estímulo (ranking/certificação)** aumentam a adesão mais que sofisticação técnica. *(O caso obras — padrão + data fixa + ofício + WhatsApp + pressão de pares — é a evidência mais forte.)*
- **H6 (novo):** Como a **maturidade das UGs varia muito**, o sistema só terá adesão ampla se **servir do órgão desorganizado ao organizado** e **reduzir a dependência de pessoas específicas** (heróis/relações pessoais).

-----

## 30. O QUE VOCÊ DEVE SABER PARA AJUDAR

Missão dos bolsistas (~11 meses, bolsa via FAPEMA):

1. **Modelar e construir os dois fluxos** sobre a stack oficial.
2. **Consumir** do **Tema 3/Tesauro** os objetos fixos (fonte externa) — **sem editar** o Tesauro na plataforma. O **Alerta §17 está resolvido** (Tesauro fica; SIMONI fora).
3. **Integrar com Keycloak** (perfis fixos) e prover **acesso por link único + identificação prévia** a respondentes.
4. **Implementar a coleta conforme o tipo de objeto**, com comprovante, verificação estrutural e
   humana, devolução/correção e validação. **Boxes genéricos, chat e IA = futuro.**
5. **Concentrar o esforço na coleta ponta a ponta** (a dor está na devolutiva/validação/comunicação). No MVP, **SIMONI e Bitrix ficam fora** (não integrados) e o **Tesauro é fonte externa**; a origem do ciclo é o **mapeamento** (§0.1).
6. **Expandir para as demais categorias** (incl. o domínio de obras/contratos) quando o escopo estiver fechado.

Respeite sempre:
- Verificação e validação são **humanas**; **IA = verificador/checador** (não transforma nem aprova sozinha).
- **SEI sempre obrigatório**; a plataforma é o **caminho paralelo de resposta** (todo ciclo tem SEI; a resposta ocorre na plataforma). A **comunicação/correção na plataforma** depende do canal em avaliação (**P-017**).
- Os campos seguem o **TemaTres**.
- **Duas portas:** ponto focal por **login/painel** (1 por órgão); **respondente técnico** (N por coleta) pelo **link do ciclo anexado ao SEI (acessível a toda a UG)**, com **cadastro híbrido (R3)**. O ponto focal **pode responder ou monitorar** e **gerencia** o ciclo; **muda com a gestão** (re-cadastro fácil).
- **Envio:** XLSX oficial e uploads no fixo; campos diretos e/ou uploads no variável; **salvar
  rascunho + reenviar**; comprovante; ausência total e não ocorrências parciais detectadas.
- **Mapeamento não é estático** e **desce à adjunta/setor**.
- **SIMONI fora do MVP** (à parte, não integrado); **Bitrix não será implementado**; **Tesauro =
  carga inicial e proveniência**; **Catálogo do Agiliza = fonte operacional posterior**.
- **Fricção mínima + recortar o processo existente + comunicação/feedback** — o gargalo é cultural, e a **maturidade das UGs varia muito**.
- Stack **open-source, on-premise, custo zero (PHP/Laravel)**.
- Escopo termina na **validação**. **Informação ≠ dado.** O **ranking** vem por último.
- **Pontos em aberto (§28):** coleta = objeto+órgão × objeto+setor; **P2** por órgão × ciclo; **resposta negativa** por coleta × linha; **forma de chegada do mapeamento**. *(Já resolvidos: formato = verificar; Tesauro × SIMONI = Tesauro externo + SIMONI fora.)*

-----

## 31. ADENDO DE CONSOLIDAÇÃO DO MVP — 2026-08-01 (PREVALECE SOBRE TRECHOS ANTERIORES EM CONFLITO)

Este adendo preserva o histórico v9.0 e consolida as decisões posteriores para a primeira versão da plataforma. Onde houver conflito, aplicam-se as regras abaixo.

### 31.1. Cardinalidade e versões locais

- Um **ciclo** possui um **modelo-base de coleta**, um **link único** e várias UGs destinatárias.
- Cada UG recebe uma **coleta local**, inicialmente derivada do mesmo modelo-base; a coleta local aceita várias submissões identificadas por autor/setor.
- **Regra superada:** a UG não altera o escopo da coleta. O ciclo conserva o snapshot publicado;
  correções de conteúdo retornam à contribuição sem produzir uma versão local do modelo.
- Submissões já enviadas permanecem preservadas. Somente o requisito modificado fica pendente de complemento.

### 31.2. Papéis e aprovações

- Analista e Especialista visualizam e validam respostas; uma validação é suficiente.
- Ambos podem cadastrar, substituir e desativar ponto focal e adjunta; o ponto focal pode informar uma adjunta ainda não cadastrada, mas não formalizar esse cadastro.
- O ponto focal administra respondentes da sua UG, responde ou monitora e, quando o toggle da UG estiver ligado, encaminha ou devolve uma submissão específica com justificativa.
- O respondente acessa apenas as próprias submissões, corrige a própria resposta e, no modo direto,
  pode declarar ausência total; itens parciais ausentes são detectados pelo sistema.

### 31.3. Não ocorrência, prazo e encerramento

- Ausência total é declarada pelo focal quando o toggle está ligado ou pelo respondente no modo
  direto. Não ocorrências parciais são detectadas antes do envio, confirmadas e justificadas.
- A STC registra ciência e não rejeita a não ocorrência. Sem unidade responsável indicada, ela é catalogada como não ocorrência da informação; com indicação, a STC pode avaliar redirecionamento.
- O prazo é por UG. O envio após o prazo é permitido somente com justificativa obrigatória.
- Reiteração, registro de novo SEI e encerramento são sempre manuais por Analista ou Especialista; não há fechamento automático, inclusive depois de prorrogação.

### 31.4. Acesso, proteção e catálogo

- Uma resposta ou anexo pode ser marcado como **restrito**. Nessa condição, o conteúdo fica visível somente ao respondente autor, ao ponto focal da mesma UG e à STC, com log/auditoria.
- CPF é a direção de autenticação aprovada; a vinculação definitiva CPF–UG continua pendente da etapa de autenticação com a PM.
- O Tesauro é carga inicial e proveniência; depois da carga, o Catálogo do Agiliza é a fonte
  operacional versionada e suas mudanças ocorrem no próprio sistema.
- Somente objeto fixo referencia modelo XLSX oficial. O variável usa campos diretos e/ou uploads,
  exige ao menos um item e não possui XLSX de preenchimento.
- Os objetos MT-0050, MT-0054, MT-0055 e MT-0056 permanecem indisponíveis até a entrega do Tesauro atualizado oficial.

-----

## 32. ADENDO DA REUNIÃO DE APRESENTAÇÃO À CHEFIA — 2026-08-10 (PREVALECE SOBRE O §31, O §0.1 E O §0.3 EM CONFLITO)

Este adendo registra as decisões homologadas pela chefia da STC na apresentação do protótipo. O
histórico anterior permanece para rastreabilidade, mas não define o contrato vigente onde divergir
das regras abaixo. Na matriz do MVP, **P2** passa a significar um toggle por UG, desligado por
padrão, e **O** passa a distinguir objeto fixo imutável no ciclo de objeto variável configurável.

### 32.1. Objeto fixo, mapeamento oficial e catálogo editável

- No objeto fixo, campos, anexos e UGs vêm integralmente do Tesauro e do mapeamento oficial da
  Alessandra. Nada pode ser acrescentado ou removido durante a criação do ciclo.
- No objeto variável, a STC escolhe campos diretos e/ou uploads, com ao menos um item, além das UGs.
- O catálogo importado passa a ser editável por qualquer Servidor STC, com auditoria de autor, data,
  valor anterior e valor novo. A gestão do Tesauro externo continua fora do MVP.
- Cada ciclo guarda o snapshot do catálogo existente na publicação. Uma edição posterior só afeta
  ciclos novos e não regenera XLSX, não reabre contribuições e não altera ciclos em andamento.
- Os oito objetos automatizados permanecem fora da criação manual enquanto a abrangência da edição
  do catálogo não for decidida.

### 32.2. Toggle do ponto focal por UG

- O toggle é definido para cada UG na criação do ciclo, nasce desligado e existe nos objetos fixos e
  variáveis. No objeto fixo, ele é a única configuração permitida por UG.
- O toggle não pode mudar após a publicação. Essa imutabilidade é uma decisão deliberada de
  simplicidade: designações de focal ocorridas durante uma coleta valem somente no ciclo seguinte.
- Desligado, a contribuição segue diretamente à STC. O focal cadastrado é apenas observador, sem
  aprovar, devolver, solicitar, concluir ou bloquear o fluxo; se não houver focal, respondente e STC
  operam diretamente.
- Ligado, o focal cadastra e atribui participantes, confere e devolve contribuições, conclui a
  resposta institucional e faz o trâmite das solicitações antes da STC.
- Sem coordenação focal, o respondente pode declarar ausência total e solicitar prorrogação
  diretamente à STC, com a justificativa exigida. O escopo não é editado pela UG.

### 32.3. Servidor STC, publicação automática e permissão de SEI

- Analista e Especialista deixam de existir como perfis distintos. Há um único perfil interno,
  **Servidor STC**, que cria e edita ciclos, valida respostas e decide solicitações.
- A atuação no SEI é uma permissão específica desse perfil, não um segundo papel. Somente pessoa
  autorizada registra números SEI na plataforma.
- Finalizar a criação publica o ciclo automaticamente, gera o link estável e uma coleta por UG. O
  fixo referencia o modelo XLSX oficial; o variável não gera XLSX. Não existem envio para análise,
  aprovação, ajustes solicitados ou fila de revisão.
- O ciclo pode ser publicado com a lista de números SEI vazia; o link já funciona e as contribuições
  podem ser preparadas e enviadas. A ausência de número impede somente o início do prazo.

### 32.4. Lista de números SEI, prazo e reiteração

- O ciclo guarda uma lista ordenada de números SEI, cada um com data de registro. Um mesmo número
  vale para todas as UGs do ciclo.
- O primeiro registro inicia o prazo de cinco dias úteis. No MVP, dias úteis são segunda a sexta,
  sem feriados.
- Acrescentar outro número representa reiteração: o link não muda, o prazo reinicia e cada UG volta
  a ter duas prorrogações disponíveis.
- O prazo de UG incluída depois do primeiro número SEI permanece em P-048. Provisoriamente, ela não
  herda o prazo corrente ou vencido e nenhum prazo é iniciado automaticamente no ato da inclusão.
- O painel distingue ciclos com e sem número SEI. A forma de exposição às UGs antes do primeiro
  número permanece em aberto.

### 32.5. Prorrogação e pedido complementar

- Cada UG pode receber no máximo duas prorrogações de cinco dias úteis, solicitadas separadamente.
  A segunda só pode ser pedida depois de a primeira ser concedida e vencer; nunca há concessão
  automática ou dez dias de uma só vez.
- Quem responde solicita a prorrogação; com toggle ligado, o focal faz o trâmite. Qualquer Servidor
  STC decide.
- Mudança de escopo não invalida resposta já validada. Para UG que já enviou, a STC pode criar um
  pedido complementar restrito à informação faltante, abrir outro ciclo ou atribuir nova coleta.
- Para UG que ainda não enviou, a configuração nova passa a valer. O pedido complementar é o quarto
  tipo de solicitação operacional e preserva a validação e os arquivos anteriormente aceitos.

## 33. Consolidação posterior ao §32 (13/08/2026)

Este adendo corrige os pontos do §32 refinados durante a implementação e a revisão do handoff.
Nos demais assuntos, o §32 continua vigente.

### 33.1. Validação fecha a resposta

- Não existe pedido complementar no contrato vigente. RF-089, CA-012 e os trechos do §32 que o
  descrevem estão superados.
- A STC valida o pacote da contribuição conforme o tipo: XLSX fixo estruturalmente compatível ou
  campos diretos variáveis, uploads esperados e não ocorrências devidamente justificadas.
- A validação encerra e torna imutável a resposta aceita. Decisão tardia de edição não pode
  reabrir contribuição nem coleta validada.
- Enquanto P-049 estiver aberta, qualquer demanda nova sobre resposta validada exige outro ciclo.

### 33.2. XLSX, anexos e correção antes do fechamento

- No objeto fixo, selecionar o arquivo não conclui a etapa. O XLSX passa por pré-validação sem
  persistência, usando exatamente o mesmo validador executado novamente no envio final.
- Cada caixa obrigatória aplica seu mínimo configurado. Se a caixa pedir três documentos, dois
  arquivos não permitem o envio nem a validação pela STC.
- Antes da validação, a STC pode devolver a contribuição mantendo o prazo restante. A correção
  preserva integralmente o escopo e o modelo publicados.

### 33.3. Prorrogação e reiteração SEI

- A primeira prorrogação de cinco dias úteis pode ser solicitada durante o prazo normal. A segunda
  fica disponível somente no último dia útil da primeira extensão.
- Com toggle desligado, o pedido do respondente vai diretamente à STC. Com toggle ligado, vai ao
  focal, que o encaminha intacto à STC ou o devolve com justificativa para correção. Pedido do
  próprio focal segue diretamente à STC.
- Existe no máximo um pedido pendente por slot e por iteração SEI. Cancelamento libera o slot sem
  apagar o histórico.
- Devolução pela STC preserva o prazo restante. Novo número SEI reinicia cinco dias e restaura os
  dois slots apenas para coletas não validadas.

### 33.4. Fonte do catálogo no protótipo

- O runtime atual foi gerado exatamente do Tesauro v2.3, em conjunto com o mapeamento da Alessandra:
  49 objetos, 276 campos, 484 associações, 31 campos multitema, 41 objetos não automatizados e
  oito automatizados fora da criação manual.
- O Tesauro recebido como v2.6 permanece preservado sem reextração. A divergência entre nome e
  versão interna continua em P-024.

-----

## 34. Registro institucional da reunião de 31/08/2026

As decisões posteriores sobre autoridade operacional do Catálogo, objeto fixo e variável,
ausência total, não ocorrências detectadas, extrato filtrado, auditoria e permissões específicas
estão consolidadas em
[`decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md`](decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md).

Esse registro supera as formulações incompatíveis identificadas em sua matriz de substituição. Os
documentos funcionais vigentes já incorporam a redação consolidada.

-----

## 35. Consolidação das decisões de 02/09 e 05/09

Esta seção substitui formulações incompatíveis das seções anteriores.

### 35.1. Perfis, capacidades e Gabinete

- O perfil interno continua único: **Servidor STC**. Não existem perfis nominais nem a separação
  Analista/Especialista.
- `sei-link-texto` habilita registrar número SEI e copiar link/texto; `catalogo-e-ugs` habilita
  mutações no Catálogo e no diretório de UGs.
- Todo Servidor STC consulta integralmente Catálogo e UGs e exporta o Histórico; apenas as mutações
  dependem de capacidade.
- O **Gabinete** possui painel próprio, somente leitura, sobre todos os ciclos. Pode extrair o
  histórico e baixar respostas de qualquer UG. Sigilo, LGPD, disponibilidade, retenção e descarte
  continuam em P-012/P-039 antes do uso com dados reais.

### 35.2. Participantes, setor responsável e e-mail

- O ponto focal envia link por e-mail; convidado e adjunta entram por autocadastro. O canal estará
  disponível no piloto, mas o provisionamento técnico continua em B-002.
- Não existe redirecionamento entre UGs nem indicação estruturada de outra unidade. Quando outro
  setor da mesma UG possui a informação, o link é repassado. Se nenhum setor possui o dado, a UG
  declara ausência total com justificativa.

### 35.3. Planilhas, Catálogo e snapshots

- Cada objeto possui modelo XLSX oficial cadastrado. O sistema disponibiliza o arquivo e não gera
  sua estrutura.
- Quando a planilha principal é obrigatória, ela basta para o piso e anexos são opcionais. Quando
  não é obrigatória, ao menos um upload é exigido; campo direto sozinho não conclui.
- Todo Servidor STC lê o Catálogo; `catalogo-e-ugs` restringe somente mutação. Alterações aprovadas
  afetam ciclos futuros, preservando snapshots publicados.
- O Catálogo pode ser exportado no formato do Tesauro; revisão pendente bloqueia essa exportação.

### 35.4. Ciclo, validação e histórico

- O ciclo possui estado explícito aberto/encerrado e deve receber número SEI antes do encerramento.
- Ciclo publicado por engano pode ser excluído, invalidando o link; respostas enviadas permanecem
  armazenadas.
- Com ciclo aberto, Servidor STC pode **Reverter validação** com motivo obrigatório. O evento
  validado permanece no Histórico. Ciclo encerrado não reabre, nem por novo número SEI.
- O efeito da reversão sobre prazo e prorrogação continua em P-060. O formato final do extrato
  continua em P-050.

### 35.5. Autoridade

A redação normativa detalhada está na versão 8.1 de
[`regras-de-negocio.md`](regras-de-negocio.md). Os fluxos vigentes estão no índice
[`fluxogramas/README.md`](fluxogramas/README.md); somente P-012/P-039, P-050, P-060 e B-002
permanecem no arquivo de decisões abertas.
