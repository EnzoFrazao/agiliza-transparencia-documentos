# Levantamento de requisitos — Agiliza Transparência

**Versão:** 6.0
**Data:** 2026-09-01
**Fontes normativas:** [`contextoSTC.md`](contextoSTC.md) e
[`decisoes/2026-08-31-reuniao-apresentacao-agiliza.md`](decisoes/2026-08-31-reuniao-apresentacao-agiliza.md)

## 1. Objetivo

Especificar o comportamento esperado da plataforma para criação de ciclos, distribuição de
coletas institucionais, contribuições por adjunta, conferência pela UG e validação pela STC.

Esta versão preserva os IDs históricos sempre que o requisito continua válido. Os requisitos da
reunião de 31/08 começam em RF-090. Requisitos superados não definem comportamento; são listados no
histórico.

## 2. Escopo

### 2.1 Incluído

- criação e publicação automática de ciclo para um objeto;
- objeto fixo ou variável;
- modelo XLSX oficial e versionado para objeto fixo;
- campos diretos e uploads para objeto variável, sem XLSX;
- UGs oficiais travadas no objeto fixo e seleção explícita no variável;
- uma coleta institucional por UG;
- distribuição entre adjuntas e respondentes;
- contribuições separadas;
- caixas de anexos;
- coordenação focal opcional por UG e envio direto à STC no modo padrão;
- validação humana pela STC;
- não ocorrência;
- prorrogação 5+5 e redirecionamento;
- histórico e estados.
- extrato macro filtrado para pessoa autorizada da STC, com formato final ainda pendente.

### 2.2 Excluído desta especificação de MVP

- edição do Tesauro externo;
- integração automática com SEI;
- unificação automática de planilhas;
- correlação automática anexo↔linha;
- IA para validar veracidade;
- ranking;
- regras definitivas de sigilo;
- comportamento definitivo de envio atrasado;
- reextração automática do catálogo após nova versão do Tesauro.
- integração automática, abertura ou preenchimento do SEI;
- exportação de arquivos, conteúdo de respostas, nomes de respondentes ou logs individuais no
  extrato macro.

## 3. Requisitos funcionais

### 3.1 Catálogo, ciclo e publicação

**RF-001 — Consumir objetos do Tesauro**
O sistema deve usar o Tesauro como carga inicial e preservar sua proveniência. A criação do ciclo
não edita o Tesauro externo; depois da carga, o Catálogo do Agiliza é a fonte operacional.

**RF-002 — Aplicar o mapeamento conforme o tipo de objeto**
No objeto fixo, o sistema deve tratar o mapeamento oficial como fonte das UGs destinatárias. No
objeto variável, deve exibir fontes e possíveis responsáveis sem selecionar UGs automaticamente.

**RF-003 — Criar ciclo de coleta**
O Servidor STC deve criar um ciclo para exatamente um objeto, informando título, destinatários e
configuração admitida para o tipo de objeto. O número SEI não é obrigatório na criação.

**RF-005 — Associar números SEI**
O ciclo deve manter uma lista ordenada de números SEI, com data de registro e eventos formais
vinculados. O prazo corrente deriva do número mais recente.

**RF-043 — Gerar XLSX para objetos fixos e variáveis — SUPERADO**
Não implementar. Somente objeto fixo usa modelo XLSX oficial; objeto variável usa campos diretos
e/ou uploads conforme RF-091 a RF-093.

**RF-046 — Publicar um link do ciclo**
O ciclo deve possuir link compartilhável para acesso dos pontos focais e respondentes, sem
expor dados de outra UG.

**RF-050 — Organizar o catálogo por tema**
O seletor de campos deve usar acordeões na ordem das abas do Tesauro, busca global, contador de
seleção e indicação de campos-base bloqueados.

**RF-051 — Manter seleção canônica de campo**
Um campo presente em mais de um tema deve conservar um único estado de seleção por ID.

**RF-081 — Publicar automaticamente**
Ao finalizar a criação, o sistema deve publicar o ciclo de forma idempotente, gerar link e uma
coleta institucional por UG, sem gate de aprovação. O ciclo fixo referencia a versão do modelo
oficial; o variável não gera XLSX.

**RF-082 — Permitir publicação sem número SEI**
O ciclo deve nascer com a lista de números SEI vazia. Isso não bloqueia publicação, link ou resposta,
mas impede o início do prazo.

**RF-083 — Restringir o registro de número SEI**
Somente Servidor STC com permissão específica de SEI deve registrar ou acrescentar números ao ciclo.

**RF-084 — Indicar situação do SEI no painel**
O painel da STC deve distinguir ciclos com e sem número SEI e oferecer ação compatível com a
permissão da pessoa autenticada.

**RF-085 — Registrar reiteração**
Acrescentar número SEI ao mesmo ciclo deve preservar o link, reiniciar o prazo e restaurar para cada
UG as duas prorrogações de cinco dias úteis.

**RF-086 — Configurar toggle focal por UG**
Cada UG do ciclo deve possuir toggle focal, desligado por padrão e imutável após a publicação. No
objeto fixo, essa é a única configuração editável por UG.

**RF-087 — Permitir observação focal sem intermediação**
Com toggle desligado, o focal cadastrado deve acompanhar respostas, logs e histórico da própria UG,
sem aprovar, devolver, solicitar, concluir ou bloquear o fluxo.

**RF-088 — Manter catálogo importado**
Qualquer Servidor STC deve poder editar objetos, campos, anexos, UGs e associações objeto↔UG do
Catálogo operacional, além dos modelos XLSX oficiais e suas versões, com auditoria de autor, data,
valor anterior e valor novo. A edição só afeta ciclos criados depois dela.

**RF-089 — Criar pedido complementar — SUPERADO**
Não implementar. A validação fecha a resposta; enquanto P-049 estiver aberta, uma demanda nova
sobre resposta validada exige outro ciclo.

**RF-090 — Manter autoridade operacional do Catálogo**
Após a carga inicial do Tesauro, o sistema deve tratar o Catálogo do Agiliza como fonte operacional,
preservar a origem dos dados e impedir que futuras cargas sobrescrevam silenciosamente edições
locais.

**RF-091 — Referenciar modelo oficial do objeto fixo**
O ciclo fixo deve referenciar uma versão do modelo XLSX oficial mantido no Catálogo e disponibilizar
esse mesmo modelo para preenchimento, sem montar ou regenerar sua estrutura na publicação.

**RF-092 — Configurar objeto variável sem XLSX**
O objeto variável deve ser composto por campos preenchidos diretamente no sistema, solicitações de
upload ou ambos. Não deve oferecer download ou envio de planilha de preenchimento.

**RF-093 — Exigir conteúdo mínimo no objeto variável**
A publicação do objeto variável deve exigir pelo menos um item no total. Campo e upload não são
obrigatórios isoladamente.

### 3.2 UGs, adjuntas e participantes

**RF-007 — Gerenciar ponto focal**
Uma UG pode possuir ponto focal. Seu papel no ciclo é observador ou coordenador conforme o toggle
daquela UG.

**RF-009 — Cadastrar respondente pelo ponto focal**
O focal deve informar nome, adjunta e e-mail. O sistema deve criar a atribuição e enviar o link
ao respondente quando o canal estiver disponível.

**RF-010 — Identificar respondente pelo link**
Uma pessoa deve poder se identificar no link, passar pela verificação configurada e receber
acesso imediato à contribuição, sem aprovação prévia do focal.

**RF-052 — Cadastrar adjunta de forma híbrida**
O focal deve escolher uma adjunta existente ou digitar uma nova. A nova adjunta deve passar a
integrar o cadastro da própria UG.

**RF-053 — Permitir múltiplas adjuntas por pessoa**
A mesma conta deve poder manter contribuições separadas para mais de uma adjunta no mesmo ciclo.

**RF-054 — Remover participante com log mínimo**
O focal deve poder remover um respondente. Cadastro ativo, conteúdo e arquivos são excluídos,
mantendo evento com participante, autor e data.

**RF-055 — Permitir contribuição do ponto focal**
O focal pode responder por uma adjunta e confirmar sua própria contribuição, com identificação
explícita dessa dupla atuação.

### 3.3 Coleta institucional e contribuições

**RF-011 — Disponibilizar XLSX em toda contribuição — SUPERADO**
Não implementar como regra geral. A entrada da contribuição depende do tipo: XLSX oficial e uploads
no objeto fixo; campos diretos e/ou uploads no variável.

**RF-014 — Salvar rascunho**
O respondente deve salvar sua contribuição antes do envio.

**RF-015 — Manter contribuições separadas**
Planilhas e anexos de respondentes/adjuntas diferentes devem permanecer separados dentro da
coleta institucional.

**RF-016 — Emitir comprovante e eventos de envio**
Cada envio e reenvio deve gerar registro com autor, data, UG, adjunta e estado.

**RF-056 — Criar uma coleta institucional por UG**
Cada UG destinatária deve possuir uma única coleta institucional no ciclo.

**RF-057 — Criar contribuição por respondente e adjunta**
Cada atribuição deve possuir pacote, estado e histórico próprios.

**RF-058 — Exigir um desfecho por participante**
Com toggle ligado, o focal só pode concluir quando cada atribuição estiver confirmada, em não
ocorrência ou removida formalmente. Com toggle desligado, a STC encerra a coleta.

**RF-059 — Conferir contribuição pelo ponto focal**
Com toggle ligado, o focal deve confirmar ou devolver cada contribuição com justificativa. Com o
toggle desligado, o envio segue diretamente à STC.

**RF-060 — Concluir resposta institucional**
Com toggle ligado, o focal encaminha o conjunto de contribuições da UG à STC. Com toggle desligado,
essa etapa não existe e a STC encerra a coleta.

### 3.4 Planilha, anexos e correções

**RF-020 — Realizar checagem estrutural**
No objeto fixo, o sistema deve verificar modelo, cabeçalhos, ordem, formato e uploads esperados,
sem validar a veracidade. A seleção do XLSX deve executar pré-validação sem persistência pelo mesmo
validador usado novamente no envio final. No variável, deve verificar campos e uploads publicados.

**RF-029 — Aplicar limites de upload quando definidos**
O sistema deve suportar parametrização de tamanho; o valor permanece pendente.

**RF-061 — Aceitar somente o XLSX gerado no MVP**
Cada contribuição de objeto fixo deve devolver o modelo XLSX oficial disponibilizado. Este
requisito não se aplica ao objeto variável.

**RF-062 — Criar caixa por anexo obrigatório**
Cada requisito de anexo deve gerar uma caixa identificada.

**RF-063 — Exigir o mínimo configurado por caixa**
Cada caixa obrigatória deve bloquear a finalização enquanto não atingir sua quantidade mínima;
uma caixa configurada com mínimo três exige pelo menos três arquivos válidos.

**RF-064 — Corrigir somente o item rejeitado**
Se a STC ou o focal apontar um arquivo específico, os demais devem permanecer válidos.

**RF-065 — Manter somente o arquivo vigente**
Após substituição, apenas o arquivo atual deve ficar disponível. O log deve registrar item,
autor, data, solicitação e motivo, sem preservar o binário anterior.

### 3.5 Não ocorrência e edição

**RF-047 — Declarar ausência total de informações**
Com toggle ligado, o focal usa `Declarar ausência de informações` quando a UG não possui nenhuma
informação sobre o objeto no período. Com toggle desligado, a mesma ação pertence ao respondente.
Em ambos os casos, confirmação e justificativa são obrigatórias e o restante do formulário é
encerrado.

**RF-066 — Impedir rejeição da não ocorrência pela STC**
A STC deve registrar a declaração sem oferecer ação de rejeição.

**RF-067 — Declarar manualmente não ocorrência da adjunta — SUPERADO**
Não implementar. Não ocorrências parciais são detectadas conforme RF-095.

**RF-068 — Solicitar edição para remover requisito da coleta — SUPERADO**
Não implementar. Focal e respondente não removem campos, colunas ou uploads do escopo publicado.

**RF-070 — Decidir pedido de remoção de requisito — SUPERADO**
Não implementar no fluxo de não ocorrência. Alterações do Catálogo só alcançam ciclos novos.

**RF-072 — Registrar dispensa manual de requisito — SUPERADO**
Não implementar. Itens ausentes confirmados são registrados automaticamente conforme RF-095.

**RF-094 — Preservar o escopo durante a revisão focal**
O ponto focal deve consultar campos, modelo e uploads esperados sem excluir requisitos, gerar XLSX
ajustado ou aprovar planilha candidata.

**RF-095 — Detectar não ocorrências parciais antes do envio**
O sistema deve detectar coluna inteira vazia no XLSX fixo, campo direto vazio e upload esperado
ausente, apresentar os itens para confirmação e exigir justificativa. Célula isolada vazia deve
gerar alerta de incompletude, não não ocorrência do campo inteiro.

**RF-096 — Manter resposta parcial como respondida**
Uma contribuição enviada com conteúdo válido e não ocorrências confirmadas deve continuar
classificada como `Respondida`, enquanto a quantidade de não ocorrências é contabilizada
separadamente.

### 3.6 Validação da STC

**RF-022 — Validar ou devolver contribuição**
Qualquer Servidor STC deve validar a veracidade ou devolver uma contribuição específica com motivo.
A validação só fica disponível quando o pacote está resolvido por conteúdo válido, não ocorrências
confirmadas ou ausência total válida.

**RF-023 — Reabrir somente a contribuição afetada**
A devolução deve reabrir o pacote do respondente/adjunta sem invalidar as demais contribuições.

**RF-024 — Gerenciar reenvio**
A correção deve retornar ao focal somente quando o toggle da UG estiver ligado; no modo desligado,
ela segue novamente à STC.

**RF-025 — Registrar validador**
Uma única validação deve concluir a análise da contribuição, registrando o Servidor STC responsável.
A resposta validada é imutável e não pode ser reaberta por decisão tardia ou novo número SEI.

**RF-026 — Encerrar coleta institucional**
O sistema deve permitir encerramento manual quando todos os desfechos aplicáveis estiverem
concluídos. Não existe fechamento automático.

### 3.7 Prazos, prorrogação e ausência de envio

**RF-073 — Calcular prazo individual da UG**
O prazo deve ser de cinco dias úteis, iniciado no registro do número SEI na plataforma. No MVP,
dias úteis são segunda a sexta, sem feriados.

**RF-074 — Solicitar prorrogação**
Quem responde deve solicitar a prorrogação com motivo. Com toggle ligado, o focal faz o trâmite; no
modo desligado, o pedido segue diretamente à STC. O pedido afeta somente a UG.

**RF-075 — Decidir prorrogação pelo Servidor STC**
Não deve haver concessão automática. Qualquer Servidor STC pode aprovar no máximo duas extensões
separadas de cinco dias úteis; a primeira é pedida no prazo normal e a segunda somente no último
dia útil da primeira extensão.

**RF-076 — Identificar envio prorrogado**
Envio realizado no prazo estendido deve receber rótulo próprio.

**RF-077 — Classificar ausência ao fim da prorrogação**
Contribuições pendentes devem receber “não enviado”; respostas existentes devem seguir à STC.

O período posterior para envio atrasado depende de decisão e não possui requisito definitivo.

### 3.8 Indicação e troca de UG

**RF-049 — Indicar possível responsável**
Com toggle ligado, o focal informa outra UG ou adjunta possivelmente responsável. Com toggle
desligado, o respondente envia a indicação justificada diretamente à STC.

**RF-078 — Efetivar redirecionamento pela STC**
A indicação deve criar pendência para Servidor STC, que seleciona uma UG cadastrada.

**RF-079 — Atribuir à nova UG**
A nova UG deve receber a coleta conforme seu toggle. O gatilho do prazo quando ela entrar depois do
primeiro número SEI permanece em P-048; provisoriamente, nenhum prazo é iniciado automaticamente no
ato da inclusão.

**RF-080 — Ocultar da UG anterior**
Após efetivação, a coleta deve desaparecer para a UG anterior, preservando o histórico apenas
para a STC.

O comportamento após já existirem contribuições permanece pendente. A regra provisória é
bloquear a indicação após o primeiro envio.

### 3.9 Histórico e painéis

**RF-017 — Exibir histórico autorizado**
Cada perfil deve visualizar os eventos permitidos no seu âmbito.

**RF-027 — Fornecer painel da STC**
A STC deve acompanhar ciclos, UGs, contribuições, prazos, solicitações e validações.

**RF-028 — Fornecer painel da UG**
O focal deve acompanhar adjuntas, respondentes, desfechos e prazo institucional.

**RF-031 — Auditar ações relevantes**
Criação, publicação, registro de número SEI, reiteração, acesso, envio, correção, não ocorrência,
edição, prorrogação, redirecionamento, exclusão e validação devem gerar eventos.

**RF-039 — Exportar comprovantes e dados autorizados**
Perfis autorizados devem obter comprovantes dos eventos e arquivos vigentes.

**RF-097 — Separar os contextos de auditoria**
O Detalhe do Ciclo deve apresentar mudanças estruturais da STC. O Histórico deve apresentar eventos
da coleta por UG, separar movimentações gerais dos eventos de cada resposta e ser o destino do log
completo aberto pela Validação.

**RF-098 — Exportar o filtro atual do Histórico**
Pessoa autorizada deve poder solicitar XLSX macro com exatamente os filtros ativos, por ciclo/coleta
e UG. O arquivo não deve conter arquivos, conteúdo de resposta, nomes de respondentes ou eventos
individuais. Seu modelo permanece dependente de P-050.

**RF-099 — Restringir extrato e operações manuais de SEI por capacidade**
Exportação filtrada e ações de copiar link/texto para o processo SEI devem depender de capacidades
específicas do perfil Servidor STC. Nenhum perfil nominal deve ser criado para uma pessoa.

**RF-100 — Preservar o contexto da porta de entrada**
O login institucional deve abrir o painel do perfil identificado. A autenticação iniciada pelo link
do ciclo deve preservar o token e continuar pela escolha de UG, adjunta e confirmação.

## 4. Requisitos não funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF-001 | Segurança | Autenticação e autorização devem restringir ação por perfil, UG, coleta e contribuição. |
| RNF-002 | Privacidade | Uma UG não pode visualizar dados de outra, salvo histórico exclusivo da STC. |
| RNF-003 | Auditoria | Eventos relevantes devem ser íntegros, ordenados e atribuídos a um autor. |
| RNF-004 | Rastreabilidade | Decisões e substituições devem ser reconstruíveis sem depender do arquivo anterior. |
| RNF-005 | Usabilidade | O fluxo deve orientar usuários com baixa maturidade digital e explicar bloqueios. |
| RNF-006 | Acessibilidade | Controles devem ter rótulos, foco visível, contraste e operação por teclado. |
| RNF-007 | Responsividade | Painéis e formulários devem funcionar em desktop e telas menores. |
| RNF-008 | Confiabilidade | Envios duplicados e mutações concorrentes devem ser impedidos. |
| RNF-009 | Integrabilidade | Autenticação, e-mail, SEI e armazenamento devem possuir limites substituíveis. |
| RNF-010 | Observabilidade | Falhas de upload, notificação e transição de estado devem ser registradas. |
| RNF-011 | Preservação | Histórico autorizado deve permanecer após troca de gestão ou focal. |
| RNF-012 | Clareza de estado | Estados “normal”, “prorrogado”, “não enviado” e “pendente” devem ser inequívocos. |

## 5. Regras de negócio

| ID | Regra |
|---|---|
| RN-001 | `contextoSTC.md` prevalece em qualquer divergência. |
| RN-002 | Um ciclo possui um objeto e uma lista ordenada de números SEI. |
| RN-003 | Uma UG possui uma coleta institucional por ciclo. |
| RN-004 | A distribuição interna não cria novo ciclo, coleta institucional ou SEI. |
| RN-005 | O escopo publicado não é removido durante a coleta; itens ausentes seguem a detecção e confirmação de não ocorrência. |
| RN-006 | Planilhas de objetos fixos e adjuntas diferentes não são unificadas. |
| RN-007 | A plataforma não correlaciona automaticamente anexos às linhas. |
| RN-008 | O mapeamento define as UGs do objeto fixo; no variável, nenhuma UG é pré-selecionada. |
| RN-009 | A classificação manual/automática vem do Tesauro vigente. |
| RN-010 | Objetos sem metadados oficiais não aparecem na criação. |
| RN-011 | O focal conclui somente em UG com toggle ligado; no modo desligado, a STC encerra. |
| RN-012 | Com toggle ligado, o focal declara não ocorrência; desligado, o respondente declara e a STC encerra. |
| RN-013 | A STC não rejeita declaração de não ocorrência. |
| RN-014 | Uma validação de qualquer Servidor STC é suficiente. |
| RN-015 | Uma correção de adjunta não invalida contribuições aceitas. |
| RN-016 | Remoção de participante apaga conteúdo, mantendo log mínimo. |
| RN-017 | Prazo e prorrogação pertencem à coleta institucional da UG. |
| RN-018 | Redirecionamento é executado por Servidor STC, nunca diretamente pela UG. |
| RN-019 | O método definitivo de autenticação permanece pendente. |
| RN-020 | Decisões pendentes não devem ser implementadas como definitivas. |
| RN-021 | Edição do catálogo só afeta ciclos novos; cada ciclo publicado preserva seu snapshot. |
| RN-022 | Validação fecha a resposta; demanda posterior exige outro ciclo enquanto P-049 estiver aberta. |
| RN-023 | Objeto variável não gera nem recebe XLSX; deve possuir campo direto, upload ou ambos. |
| RN-024 | Resposta parcial continua respondida e suas não ocorrências são contadas separadamente. |
| RN-025 | Autorizações específicas pertencem ao perfil Servidor STC e não ao nome de uma pessoa. |

## 6. Critérios de aceite por cenário

### CA-001 — Ciclo publicado

- Dado um ciclo em criação,
- quando um Servidor STC finalizar,
- então o sistema gera o link e uma coleta por UG;
- e, se o objeto for fixo, referencia a versão do modelo XLSX oficial;
- e, se for variável, não gera XLSX;
- e a ausência de número SEI não bloqueia publicação, link, preparação ou envio da contribuição;
  bloqueia somente o início do prazo.

### CA-002 — Distribuição interna

- Dada uma coleta institucional,
- quando o focal cadastrar duas adjuntas e três atribuições,
- então devem existir três contribuições separadas;
- e a coleta institucional deve permanecer única.

### CA-003 — Quantidade mínima da caixa obrigatória

- Dada uma caixa obrigatória configurada com mínimo de três arquivos,
- quando somente dois arquivos tiverem sido enviados,
- então a finalização deve permanecer bloqueada;
- e a STC não pode validar a contribuição incompleta.

### CA-004 — Conferência focal

- Dada uma contribuição enviada,
- quando o toggle da UG estiver ligado e o focal devolver com motivo,
- então somente aquela contribuição reabre;
- e, no modo desligado, envio e correção seguem diretamente à STC.

### CA-005 — Não ocorrência parcial detectada

- Dada uma contribuição com coluna inteira, campo direto ou upload esperado ausente,
- quando o sistema executar a revisão anterior ao envio,
- então o item deve aparecer para confirmação e justificativa;
- e uma célula isolada vazia deve aparecer apenas como alerta de incompletude.

### CA-006 — Não ocorrência institucional

- Dada uma coleta sem contribuição parcial,
- quando o focal ou respondente autorizado usar `Declarar ausência de informações`, confirmar e
  justificar,
- então a coleta encerra;
- e a STC não deve visualizar ação de rejeição.

### CA-007 — Correção pela STC

- Dadas cinco contribuições, quatro válidas e uma incorreta,
- quando a STC devolver a incorreta,
- então apenas ela reabre;
- e as outras quatro permanecem válidas.

### CA-008 — Prorrogação

- Dada uma UG com uma extensão de cinco dias aprovada,
- quando enviar dentro do prazo estendido,
- então o envio é marcado como prorrogado;
- e a segunda extensão só pode ser pedida no último dia útil da primeira.

### CA-009 — Mapeamento

- Dado um objeto variável com campo direto, upload ou ambos e possível fonte mapeada,
- quando o Servidor STC abrir a seleção de UGs,
- então a sugestão pode ser destacada;
- e nenhuma UG fica marcada automaticamente.

### CA-010 — Exclusão de participante

- Dado um respondente com arquivo enviado,
- quando o focal removê-lo,
- então conta, conteúdo e arquivo deixam de existir;
- e a STC conserva apenas o evento mínimo da remoção.

### CA-011 — Objeto fixo imutável

- Dado um objeto fixo com modelo oficial, campos, uploads e UGs,
- quando um Servidor STC configurar o ciclo,
- então o ciclo referencia a versão oficial e esses conjuntos permanecem somente leitura;
- e apenas o toggle focal de cada UG pode ser alterado antes da publicação.

### CA-012 — Pedido complementar — SUPERADO

- Não existe pedido complementar no contrato vigente.
- Uma nova demanda sobre resposta validada exige outro ciclo enquanto P-049 estiver aberta.

### CA-013 — Objeto variável sem planilha

- Dado um objeto variável,
- quando possuir pelo menos um campo direto ou upload e for publicado,
- então a contribuição apresenta somente os itens configurados;
- e nenhuma ação de download ou envio de XLSX é oferecida.

### CA-014 — Resposta parcial contabilizada

- Dada uma contribuição com conteúdo válido e duas não ocorrências confirmadas,
- quando o envio for concluído,
- então a contribuição conta como `Respondida`;
- e as duas não ocorrências permanecem contabilizadas separadamente.

### CA-015 — Extrato do filtro atual

- Dado um Histórico filtrado por ciclo, UG e período,
- quando pessoa autorizada solicitar `Exportar filtro atual`,
- então o futuro XLSX usa exatamente esse recorte macro;
- e não inclui arquivos, conteúdo, nomes de respondentes ou eventos individuais.

### CA-016 — Acesso contextual autenticado

- Dado um acesso iniciado pelo link de um ciclo,
- quando uma pessoa já cadastrada autenticar-se,
- então o token do ciclo permanece ativo;
- e o fluxo continua pela escolha de UG, adjunta e confirmação.

## 7. Histórico de requisitos superados

- **RF-012:** resposta item a item como modelo geral — substituída por XLSX e caixas de anexos.
- **RF-013:** envio por arquivo único genérico — absorvida pelo pacote de contribuição.
- **RF-018:** chat livre — permanece fora do MVP.
- **RF-021:** IA verificadora — futuro.
- **RF-030:** classificação de sigilo — depende da política P-012.
- **RF-032 a RF-035:** detalhes de obras — dependem da decisão P-014.
- **RF-037:** ranking — depende de P-007/P-008.
- **RF-040:** OCR — futuro.
- **RF-004:** acréscimos e UGs livres no objeto fixo — substituído pelo objeto fixo imutável.
- **RF-041:** aprovação antes da publicação — substituída pela publicação automática.
- **RF-042:** perfis Analista e Especialista — substituídos pelo perfil único Servidor STC.
- **RF-044:** toggle opcional em nível de ciclo — substituído pelo toggle por UG do RF-086.
- **RF-045:** reiteração sem regra definida — substituída pela lista de números SEI do RF-085.
- **RF-069:** aval focal obrigatório — passa a depender do toggle da UG.
- **RF-071:** reaprovação de mudança de escopo — não existe sem gate de aprovação.
- **RF-089 e CA-012:** pedido complementar — superados pela regra de que a validação fecha a
  resposta; nova demanda exige outro ciclo enquanto P-049 estiver aberta.
- **RF-011 e RF-043:** XLSX em todos os objetos — superados pelos modos fixo e variável de
  RF-091 a RF-093.
- **RF-067, RF-068, RF-070 e RF-072:** seleção, dispensa ou remoção manual de requisitos —
  superadas pela preservação de escopo e detecção de RF-094 a RF-096.

## 8. Pendências

Os requisitos não definidos estão centralizados em
[`pontos_em_aberto.md`](pontos_em_aberto.md). Este documento não deve atribuir comportamento
definitivo a essas questões.
