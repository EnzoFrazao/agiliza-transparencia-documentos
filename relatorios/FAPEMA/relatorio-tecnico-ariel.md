# Relatório Técnico — Contribuições de Ariel Asafe Durans Rabelo ao Agiliza Transparência

**Projeto:** STC Agiliza / Agiliza Transparência (Secretaria de Transparência e Controle do Maranhão)
**Fontes:** 9 relatórios quinzenais FAPEMA (Sprints 01–09, 25/05 a 25/09/2026) e repositório `EnzoFrazao/agiliza-transparencia` (histórico Git, specs, ADRs)
**Data de elaboração:** 30/09/2026

---

## 1. Resumo executivo

Ariel participou do projeto desde a Sprint 01, tanto na frente de levantamento de requisitos (estudos da stack, entrevistas, reuniões com Unidades Gestoras) quanto, entre **10 e 20/08/2026**, na frente de **desenvolvimento do frontend**, onde autorou **19 commits** (18 como "Ariel Rabelo" e 1 como "Ariel_rabelo27", mesmo e-mail), somando cerca de **41 mil linhas adicionadas e 17 mil removidas** (excluindo lockfiles; inclui ~15 mil linhas do catálogo gerado do Tesauro), das quais ~13 mil em testes.

As contribuições de código concentram-se em cinco frentes:

1. Experiência por perfil (painéis, shell responsivo, navegação e perfil);
2. Aplicação das decisões pós-reunião de 10/08 (perfil único STC, publicação automática, prazo/SEI, toggle focal por UG);
3. Catálogo do Tesauro (normalização de UGs, auditoria de associações, pendências);
4. Painel STC (classificação operacional de ciclos e objeto variável);
5. Não ocorrência por requisito (fluxo completo, depois substituído pela decisão ADR-0012).

Em todas as entregas de código, os commits carregam também a atualização das specs, com change-specs (`CHG-*`) e ADRs, seguindo o protocolo de memória técnica do repositório.

---

## 2. Participação nas sprints (segundo os relatórios quinzenais)

| Sprint | Período | Participação registrada de Ariel |
|---|---|---|
| 01 | 25/05–03/06 | Estudos da stack (PHP/Laravel, PostgreSQL, Docker, Keycloak, GitLab, Tesseract) e ambientação do ambiente de desenvolvimento (com Enzo). 32h (calculado pela lista de frequência; o PDF não traz o total). |
| 02 | 08–19/06 | Entrevistas estruturadas com Thiago (fluxo/SEI), Mateus (SIMONI/operacional) e Fernando (gestão/cultura); estudos da stack. 40h. |
| 03 | 22/06–03/07 | Reuniões de levantamento com UGs externas (SEDUC, SINFRA, SAF, AGEM, SES, SEFAZ), incluindo duas adjuntas da SINFRA; estudos da stack. 32h. |
| 04 | 06–17/07 | Reunião com a Polícia Militar (08/07), visita ao Detran (09/07), reunião na Sede da STC (13/07), reunião com a TI da PM (15/07); prototipação do MVP (responsável registrado: Enzo). |
| 05 | 20–31/07 | Alinhamentos de escopo do MVP, estudos técnicos em paralelo e reunião de planejamento do back-end (31/07). 32h. |
| 06 | 03–14/08 | Refinamento das coletas por perfil e integração da identidade visual/shell responsivo (registrado como "Enzo e Ariel"). 40h. |
| 07 | 17–28/08 | Consta como responsável conjunto (Enzo e Ariel) apenas na reunião do PROCON (26/08, 1h de participação); ausente da entrevista no Corpo de Bombeiros (25/08). A aplicação das alterações da reunião de 10/08 está registrada em nome de Enzo. 29h. |
| 08 | 31/08–11/09 | Reunião na Polícia Civil (01/09, participação restrita); **responsável pelo inventário da ambientação local** (V1-S8-06) de frontend, backend, banco e ferramentas — em andamento. 29h. |
| 09 | 14–25/09 | Não consta como estagiário na identificação nem na lista de frequência do relatório. |

Horas totais registradas de Ariel: S01 32h (calculado), S02 40h, S03 32h, S05 32h, S06 40h, S07 29h, S08 29h; a Sprint 04 não traz total nem lista legível no PDF.

> Observação: os relatórios atribuem muitas atividades de desenvolvimento apenas a "Enzo", mas o histórico Git mostra que o trabalho de Ariel de 10 a 20/08 foi substancial. Sugere-se, se desejado, ajustar a atribuição nos próximos relatórios.

---

## 3. Contribuições técnicas no repositório

### 3.1 Linha do tempo dos commits

| Data | Commit | Descrição | Escala |
|---|---|---|---|
| 10/08 | `7f920e0` (PR #7) | Refinar experiência das coletas por perfil | 24 arq., +2.413/−304 |
| 10/08 | `8abd235` | Logo/navbar (símbolo do Agiliza) | 50 arq., +2.862/−180 |
| 10/08 | `3de7a44` | Unificar navegação e perfil responsivos | 23 arq., +940/−247 |
| 13/08 | `d55e4da` | Aplicar alterações pós-reunião auditadas | 111 arq., +21.345/−13.931 |
| 13/08 | `e35c5fd` | Catálogo: normaliza UGs e audita associações | 21 arq., +1.512/−184 |
| 14/08 | `7035b83`, `e2f2fda`, `1d0c7d1` | Catálogo: pendências, resolução, polaridade | 3 correções sucessivas |
| 14/08 | `c67c460` | STC: classifica ciclos e simplifica objeto variável | 22 arq., +1.221/−220 |
| 20/08 | `c6d8835`, `c4ef753` | STC: UGs pendentes no ciclo; projeção unificada de coletas | 2 correções |
| 20/08 | `b346b28` | Coleta: não ocorrência por requisito | 24 arq., +2.831/−100 |
| 20/08 | `0f76f02`, `a10e418`, `d7e01d7`, `0de4034`, `16e681d`, `95ec9b1` | Endurecimento de invariantes da não ocorrência | 6 commits de correção |
| 20/08 | `6a1ab02` | Consolidação das alterações da branch `pequenas-mudancas` | 26 arq., +3.016/−1.261 |

O trabalho foi integrado ao repositório principal pelo PR #7 (squash, 10/08), pelos PRs #8 (10/08) e #9 (13/08), mesclados por Enzo, e pelo PR #10 (24/08, branch `pequenas-mudancas`), também mesclado por Enzo.

### 3.2 Experiência por perfil e shell responsivo (10/08)

Ref.: `CHG-20260809-profile-collection-refinements`, `CHG-20260810-responsive-shell-profile`.

- Saudação nominal e área de boas-vindas nos painéis do ponto focal e do respondente.
- Aba compacta de urgência no painel do respondente (`Mais recentes` / `Urgentes (n)`), evitando lista duplicada.
- Listas de adjuntas/participantes com inclusão e remoção explícitas; novo `AssignmentRemovalDialog`.
- Reorganização visual do detalhe do ciclo e do estado inicial da validação STC.
- Shell responsivo: navbar que oculta ao rolar para baixo (`useAutoHidingHeader`), drawer de perfil à direita para os quatro papéis (`ProfileDrawer`), navegação STC encaixada em desktop/tablet (252 px) e sobreposta no mobile (`useResponsiveNavigation`).
- Integração do símbolo do Agiliza (login, navbar, favicon).
- Cobertura: testes Jest (direção da navbar, drawer, foco, hero) e Playwright em quatro papéis e larguras de referência, com auditoria Axe e verificação de ausência de overflow.

### 3.3 Decisões pós-reunião de 10/08 (13/08)

Ref.: `CHG-20260811-perfil-unico-e-toggle-por-ug`, `ADR-0006`, `ADR-0007`, `ADR-0008`.

Commit de maior escala (111 arquivos). Implementou, com auditoria contra a minuta de reunião:

- **Perfil único "Servidor STC"** e permissão separada de SEI, substituindo Analista/Especialista e a aprovação de versão (ADR-0006; removidos `cycle-commands`, `cycle-authoring`, `CanonicalCycleReview`).
- **Publicação automática atômica** do ciclo (`cycle-publication.ts`, ~1.100 linhas) gerando link, XLSX e coletas sem aprovação e sem exigir número SEI (o SEI passa a ser apenas gatilho do prazo).
- **Toggle focal por UG** (padrão desligado): modo direto (respondente ↔ STC) ou mediado pelo ponto focal.
- **Prazos:** cinco dias úteis com duas prorrogações, reiteração que reinicia prazo, segunda prorrogação só no último dia útil da primeira.
- **Validação fecha a resposta** (ADR-0008); pedido complementar sem reabertura global (ADR-0007).
- Objeto fixo com campos, anexos e UGs travados; objeto variável configurável; edição auditável do catálogo, valendo apenas para ciclos novos; pré-validação XLSX sem persistência e mínimos de anexos.
- Atualização de seeds demo e regeneração do catálogo do Tesauro (`tesauroData.ts`, ~15 mil linhas geradas por `generate-tesauro-data.py`), com reescrita do conjunto de testes correspondente.
- Reescrita de seis specs de capacidade e da lista de decisões abertas.

### 3.4 Catálogo do Tesauro: UGs, associações e pendências (13–14/08)

Ref.: `CHG-20260813-associacoes-catalogo-e-mapeamento-ug`.

- Normalização em runtime do mapeamento objeto↔UG, mantendo o Tesauro v2.3 (49 objetos, hash preservado): "Por UG" e setores genéricos do próprio órgão passam a significar todas as UGs operacionais.
- Exceções registradas separadamente, de modo que UGs criadas depois entrem em ciclos futuros.
- Gramática de aliases controlada (mesma regra em Python e TypeScript): PGE/UEMA ficam como referências pendentes; SIGEF, PeopleSoft, SIGAA, DOEMA e Legisla nunca são UG; qualificadores como `SEFAZ-MA` resolvem pelo alias registrado.
- Comando atômico de revisão de UGs, campos e anexos, com revisão esperada, ator, instante, justificativa obrigatória e evento imutável de auditoria (`domain/catalog/revisions.ts`).
- Preservação de pendências em edições; resolução na interface apenas quando existir UG cadastrada; **polaridade** `include`/`exclude` (aliases após "exceto"); validação prévia de todas as resoluções antes de alterar estado.
- Interface de manutenção do catálogo (`OfficialCatalogRegistry`) com subabas acessíveis navegáveis por setas.
- Testes do importador Python (`generate_tesauro_data_test.py`) e de infraestrutura protegendo hash e contagens.

### 3.5 Painel STC e objeto variável (14 e 20/08)

Ref.: `CHG-20260814-objeto-variavel-e-painel-stc`.

- **Objeto variável:** cada campo/anexo selecionado gera requisito obrigatório, sem listas paralelas de obrigatoriedade; "Selecionar todos os N campos" por tema; checkbox indeterminado; ID canônico único para campos multitema.
- **Classificação operacional** (`stc-cycle-classification.ts`, função pura): identidade por `originalUgId`, distinguindo pacote completo, correção e pronto para validar; ciclo concluído somente quando todas as contribuições relevantes estão validadas.
- Filtros do painel e projeção de ciclos concluídos no Histórico e no Registro; correções de 20/08 para preservar UGs pendentes e unificar a projeção de coletas atuais.

### 3.6 Não ocorrência por requisito (20/08)

Ref.: `CHG-20260820-requirement-non-occurrence`, `ADR-0009` (escrita depois, em 24/08, por Codex).

- Nova entidade por **requisito**, presa à coleta institucional (não à atribuição), com alcance de toda a UG e sem apagar contribuições irmãs; lote com categoria/justificativa comuns e estados `draft → pending-focal/pending-stc → acknowledged | revoked`.
- Comandos, painel (`RequirementNonOccurrencePanel`, ~660 linhas) e testes (~430 linhas de teste de painel, ~340 de comandos), com autorização nos modos direto e focal, revogação, concorrência e auditoria.
- Configuração efetiva sem os alvos declarados, preservando o snapshot publicado.
- Seis commits de endurecimento no mesmo dia fecharam invariantes: auditoria duplicada por lote, lifecycle tardio, cadeia de não ocorrência e preservação da autoridade do lote.
- **Estado atual:** a ADR-0009 foi **superada pela ADR-0012** (contrato aprovado do snapshot de design); a entidade permanece legível, mas o fluxo manual e a fila de ciência **não integram a V1 aprovada**. O código existe no repositório, mas a funcionalidade não é parte do escopo aprovado.

---

## 4. Qualidade, testes e documentação

- Cerca de **13 mil linhas de testes unitários/comportamentais (fora E2E)** nos commits de Ariel (Jest/RTL comportamental, Playwright e importador Python), em coerência com a estratégia do repositório (gate com typecheck, testes, build e lint).
- Cada commit funcional atualiza `specs/system.md`, `specs/testing.md`, `specs/history.md`, capabilities afetadas e cria change-spec datada, o que preserva a rastreabilidade entre decisão institucional, contrato e implementação.
- Três ADRs (0006, 0007, 0008) nasceram do commit `d55e4da`. A ADR-0009 (não ocorrência) foi redigida por Codex em 24/08 (`8308be2`), documentando a funcionalidade entregue por Ariel em 20/08.

---

## 5. Pontos de atenção e limitações

1. **Transferência de 15–16/09:** o conteúdo da branch de Ariel para a branch pessoal de Enzo (commit `9675a67`, "transfere ajustes do Ariel para revisao") foi auditado e corrigido em `CHG-20260916-correcao-transferencia-ariel`. Foram encontradas regressões: objeto fixo podia reduzir UGs mapeadas, contribuição expunha etapas/ações sem suporte completo, arquivos persistidos não participavam da reedição e o guard de navegação não cobria o histórico do navegador. A correção também atualizou Next 16.3.5 e Sharp 0.35.4. Esse conteúdo (wizard de etapas do ciclo e do respondente, `navigation-guard`, adaptador ExcelJS) foi integrado ao repositório pelo PR #14.
2. **Escopo funcional substituído:** a não ocorrência por requisito (3.6) foi superada pela ADR-0012.
3. **Limitação da atribuição:** a autoria aqui é medida por commits do Git. Diversos commits entre 24/07 e 28/07 e de 08/08 a 24/08 aparecem sob o autor "Codex"; não é possível determinar por essa via se envolveram trabalho de Ariel. Os números acima são, portanto, o piso verificável.
4. **Dependência residual:** dois alertas moderados em `uuid` transitivo do ExcelJS permanecem, com caminho vulnerável não utilizado.
5. **Dados simulados:** autenticação, arquivos e dados permanecem em memória de sessão, e o backend (Laravel/PostgreSQL) ainda não foi iniciado, inclusive o inventário de ambientação local atribuído a Ariel (V1-S8-06), ainda em andamento no relatório da Sprint 08.

---

## 6. Conclusão

Nas três primeiras sprints, Ariel contribuiu com o estudo da stack, entrevistas e reuniões de levantamento com a STC e as UGs. A partir da Sprint 06, passou a entregar código do frontend do MVP: experiência por perfil e shell responsivo, aplicação das decisões pós-reunião com perfil único e publicação automática, catálogo auditável do Tesauro, classificação operacional do Painel STC e o fluxo de não ocorrência por requisito. Todas as entregas vieram acompanhadas de testes e documentação normativa. O trabalho serviu de base para as etapas seguintes do frontend (roteiro do respondente e ajustes visuais V1), mas parte dele passou por correção na transferência de setembro e parte foi substituída por decisão posterior.

---

## 7. Adendo — abrangência da autoria

Os 19 commits autorados por Ariel são o total em todas as branches do repositório (`main` e `alteracoes-front-enzofrazao`), sob dois nomes e o mesmo e-mail. O trabalho dele é maior do que essa contagem, por três motivos:

- **PRs abertos por Ariel (GitHub `Darkzin41`):** #7 (`codex/refino-ux-perfis-coletas`), #8 (`alteracao-logo-navbar`, "atualizar identidade, navegação e revisão focal") e #9 (`alteracoes-pos-reuniao`, "alterações pós-reunião com auditoria"). Os PRs #8 e #9 incluem também commits do autor "Codex" (ex.: `9b04516`, `2cce83d`, `a2bcea5`, `4a33557`, `a052bba`, `7f93c6e`), provavelmente produzidos nas mesmas branches com apoio de agente; o Git não permite confirmar.
- **Transferência feita por Enzo:** o commit `9675a67` (24 arquivos, +5.806/−1.945) traz para a branch pessoal de Enzo ajustes de Ariel (wizard de etapas do ciclo e do respondente, `navigation-guard`, adaptador ExcelJS), corrigidos depois em `32c841f`.
- **PR #10** (aberto por Enzo, `pequenas-mudancas`, "catálogo auditável, painel STC por ciclo e não ocorrência por requisito") contém os commits de Ariel de 14 a 20/08.

---
