# Perfis, fluxos, telas e estados — catálogo do produto

Este documento apresenta capacidades do produto completo. O recorte executável da V1 mínima é
definido pelas Sprints 9–14 do backlog ativo e pelos documentos em
[`funcionalidades/`](funcionalidades/README.md).

## Escopo

| Recorte | Perfis e capacidades |
| --- | --- |
| **V1 mínima** | Administrador/STC e Respondente no pedido contextual; identificação mínima, objeto fixo ou variável, upload/XLSX, envio, consulta e download pela STC. |
| **MVP completo — A definir** | Ponto focal, Gabinete, registro e comunicação manual pelo SEI, prazo, prorrogação, validação humana, correção, auditoria, Histórico e encerramento. Essas capacidades não integram a V1 mínima. |

## Perfis do catálogo

### Servidor STC

- cria, publica, acompanha e encerra ciclos;
- mantém o catálogo importado;
- decide solicitações, devolve e valida contribuições;
- registra números SEI, copia o link e copia o texto do processo somente com a capacidade
  `sei-link-texto`; altera Catálogo e diretório de UGs somente com `catalogo-e-ugs`;
- sem `catalogo-e-ugs`, continua vendo integralmente Catálogo e UGs em modo somente leitura;
- exporta o histórico **sem depender de capacidade** (D-01, 02/09);
- visualiza o histórico autorizado de todas as UGs.

Não existem perfis internos separados de Analista e Especialista no contrato vigente.

### Ponto focal — MVP completo, A definir

- com toggle ligado, coordena a UG: **convida** adjuntas e respondentes por e-mail — quem recebe
  se autocadastra (D-08) —, confere contribuições, encaminha **prorrogação** e conclui o conjunto
  institucional;
- com toggle desligado, apenas observa respostas, logs e histórico da UG, sem bloquear o fluxo;
- pode contribuir por uma adjunta, preservando a dupla atuação identificada.

### Respondente

- acessa a contribuição atribuída ou se identifica pelo link, **sem depender do toggle** — o
  condicionante *“quando o modo direto permitir”* foi retirado em 02/09 (D-16, divergência C-14);
- quando a planilha oficial é obrigatória, baixa e devolve esse modelo; anexos complementares são
  opcionais;
- quando não há planilha oficial obrigatória, envia ao menos um upload, que pode ser uma planilha
  complementar ou outro arquivo; campo direto sozinho não conclui o envio;
- solicita **prorrogação** pelo caminho definido pelo toggle; edição e redirecionamento saíram
  em 02/09 (D-12 e D-09);
- corrige somente sua contribuição e pode declarar ausência total no modo direto;
- confirma as não ocorrências detectadas automaticamente antes do envio parcial.

### Gabinete — MVP completo, A definir

**Perfil de leitura do MVP completo; não integra a V1 mínima.**

- acessa **todos os ciclos**, em andamento e encerrados, e as respostas;
- **baixa as respostas de qualquer UG** e **extrai o histórico**;
- tem painel próprio com cartões simples de contagem: ciclos criados, coletas respondidas,
  coletas não respondidas;
- **não altera nada:** não valida, não devolve, não edita, não registra SEI, não cria ciclo.

As telas existem desde 2026-09-03 no snapshot. Alcance e download foram confirmados em 05/09;
retenção, LGPD, descarte e tempo de disponibilidade (`P-012/P-039`) continuam bloqueando dados
reais.

## Fluxo resumido do ciclo — MVP completo

As etapas de SEI, prazo, prorrogação, validação e encerramento abaixo permanecem **A definir** e
não ampliam a V1 mínima.

1. A STC escolhe um objeto fixo ou variável.
2. Configura o ciclo e os toggles focais por UG.
3. Publica diretamente, gerando snapshot, link e uma coleta por UG; o XLSX existe somente para
   objeto fixo e deriva do modelo oficial do Catálogo.
4. O ciclo pode receber respostas antes do SEI, mas o prazo ainda não corre.
5. Servidor autorizado registra o primeiro ou novo número SEI.
6. Cada UG passa a ter prazo de cinco dias úteis e até duas extensões de cinco dias.
7. A STC monitora, decide solicitações, corrige e valida contribuições.
8. O ciclo é encerrado manualmente; validação fecha cada resposta.

## Fluxo resumido da coleta — MVP completo

Coordenação focal, ausência total, não ocorrência parcial, correção, validação e auditoria são
capacidades do MVP completo ainda fora da V1 mínima.

1. O toggle define se o caminho é direto ou coordenado pelo focal.
2. Respondentes recebem contribuições separadas por adjunta.
3. A obrigatoriedade da planilha principal vem do modelo oficial cadastrado. Quando ela existe,
   anexos são complementares e opcionais; sem ela, a contribuição exige ao menos um upload.
4. A checagem automática é estrutural; veracidade é decisão humana da STC.
5. Antes do envio parcial, o sistema mostra as não ocorrências detectadas para confirmação e
   justificativa.
6. Ausência total é declarada pelo focal no modo focal e pelo respondente no modo direto.
7. No modo focal, o focal confirma ou devolve antes da STC.
8. No modo direto, envio e correção seguem diretamente entre respondente e STC.
9. Devolução reabre somente a contribuição afetada.
10. Resposta validada aparece em verde e preserva seu registro no Histórico. Com o ciclo aberto, a
    STC pode usar `Reverter validação`, informando motivo; o efeito no prazo ainda está em `P-060`.

## Inventário de telas do snapshot

| Área | Rota | Função visual atual |
| --- | --- | --- |
| Acesso | `/login` | Entrada demonstrativa e escolha de perfil. |
| Acesso | `/acesso/[token]` | Identificação pública e acesso pelo link do ciclo. |
| STC | `/stc/painel` | Visão inicial operacional e atalhos. |
| STC | `/stc/ciclos` | Lista, filtros, estados e resumo dos ciclos ativos. |
| STC | `/stc/ciclos/novo` | Criação e publicação de ciclo fixo ou variável. |
| STC | `/stc/ciclos/[id]` | Detalhe, UGs, versões, SEI, prazo e movimentações. |
| ~~STC~~ | ~~`/stc/ciclos/[id]/nova-versao`~~ | **REMOVIDA em 2026-09-03 (D-07).** A rota, `paths.stcNovaVersao`, o modo "nova versão" do editor e `publishCycleVersion` não existem mais. Ciclo errado é apagado e refeito, por `Excluir ciclo` em `/stc/ciclos`. |
| STC | `/stc/ciclos/[id]/validar` | Contribuição, correção e decisão STC. A ciência saiu (D-13). **O snapshot reabre sem motivo e mantém os cards; o contrato exige `Reverter validação`, motivo e histórico preservado.** |
| STC | `/stc/ugs` | Administração de UGs, focais e vínculos demonstrativos. |
| STC | `/stc/registro` | Catálogo oficial, revisões e ciclos concluídos. |
| STC | `/stc/historico` | Eventos e auditoria autorizada. |
| ~~STC~~ | ~~`/stc/revisao`~~ | **Não é tela:** `redirect(paths.stcPainel)`, seis linhas. Listada aqui para a omissão não ser lida como esquecimento. |
| Ponto focal | `/focal/painel` | Coletas, prazos e prioridades da própria UG. |
| Ponto focal | `/focal/coletas/[id]` | Revisão inicial, distribuição e operação da coleta. |
| Respondente | `/respondente/painel` | Atribuições recentes, urgentes e pendentes. |
| Respondente | `/respondente/contribuicoes/[id]` | Instruções, XLSX, anexos, envio e correção. |
| **Gabinete** | **`/gabinete/painel`** | **CRIADA em 2026-09-03 (D-03):** oito cartões de contagem, leitura apenas, alcance de todos os ciclos. Zero controles na tela. **Não vai a piloto enquanto `P-012` estiver aberta.** |
| **Gabinete** | **`/gabinete/historico`** | **CRIADA em 2026-09-03 (D-03):** 12 filtros, linha do tempo, download da resposta de qualquer UG e extração do histórico. Sem nenhuma ação de escrita. **Não vai a piloto enquanto `P-012` estiver aberta.** |

`/`, `/stc/revisao` e a rota antiga `/respondente/coletas/[id]` são redirecionamentos, não telas
independentes para o Claude Design.

**Autoridade de tela desde 2026-09-02:** as mudanças pendentes de interface estão em
[`contexto.md`](contexto.md), que passa à frente dos
prompts em `CLAUDE_DESIGN_PROMPT_*`. **Nenhuma tela foi alterada naquela rodada.**

## Estados que precisam aparecer como variações

- ciclo: rascunho, publicado aguardando SEI, em andamento e finalizado;
- UG/coleta: aguardando SEI, aberta, encaminhada à STC, ausência total, validada e atrasada;
- contribuição: não iniciada, rascunho, aguardando focal, devolvida, confirmada, aguardando STC,
  em correção, validada, ausência total e removida;
- item da resposta: preenchido, não ocorrência detectada/confirmada ou alerta de incompletude;
- solicitação: aguardando focal, devolvida ao solicitante, pendente na STC, aprovada, recusada ou
  cancelada;
- prazo: normal, primeira extensão, segunda extensão, prorrogado, vencido e sem prazo por falta de
  SEI.

Estados internos diferentes da mesma rota devem ser variações da tela correspondente, não novas
páginas inventadas.
