# Regras de negócio — Agiliza Transparência

**Versão:** 8.3  
**Data:** 2026-10-21  
**Fontes normativas:** decisões de 31/08 em
[`decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md`](decisoes-de-reunioes/2026-08-31-reuniao-apresentacao-agiliza.md)
e consolidação posterior registrada em [`contexto.md`](contexto.md).

**Recorte V1 confirmado em 16/10/2026:** novas respostas usam somente arquivos; os campos
do objeto fixo descrevem o XLSX e não inputs do respondente. O variável exige ao menos um
anexo obrigatório e aceita qualquer formato dentro do limite de tamanho. A V1 carrega
somente objetos piloto derivados do Tesauro após aprovação; não oferece cadastro livre
de novos objetos nem sincronização automática. Ver a
[decisão do Catálogo](decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md)
e o plano técnico `../../agiliza-stc/specs/changes/2026-10-16-respostas-somente-arquivos-v1.md`.
Formulações históricas abaixo sobre campos diretos e cadastro de novos objetos ficam
subordinadas a este recorte na V1.

**Revisão da V1 confirmada em 17/10/2026:** a STC não cria caixas de arquivo nomeadas; o
respondente anexa os arquivos que julgar adequados. Não há “Salvar rascunho”: o arquivo entra na
resposta ao ser escolhido, e o RF-014 continua valendo só para o MVP completo. Cada UG envia uma
única resposta, e o primeiro envio encerra o destinatário. No variável, a STC informa na criação a
lista de informações solicitadas. O envio gera comprovante em PDF com protocolo, “recebido para
conferência”, sem afirmar validação do conteúdo; na V1 isso atende ao RF-016 apenas para o envio
atual, sem reenvio.

**Revisão confirmada em 21/10/2026:** o piloto passa a ser terceirizados, e o objeto fixo deixa de
ser imutável no ciclo. Os metadados do Tesauro são o máximo que a STC pode pedir. Os mínimos vêm
marcados, e a STC acrescenta ou retira informações, até restar uma. As UGs do mapeamento vêm
marcadas, e a STC pode alterá-las. Na publicação, o sistema gera a planilha com as informações
escolhidas, e cada resposta é conferida contra ela. As observações do ciclo aceitam um arquivo de
orientação. Isso revê, na V1, os seguintes pontos:
- §2.1, no trecho do objeto fixo com XLSX oficial;
- §2.2, nos itens “modelo XLSX oficial e versionado” e “UGs oficiais travadas”;
- RF-002, RF-061, RF-081, RF-091 e RF-104;
- RF-086, porque no fixo a chave focal deixa de ser a única configuração editável;
- RN-008, CA-001 e CA-011.

O número SEI continua um por ciclo (RF-005 e RN-002). Ver a
[decisão de 21/10](decisoes-de-reunioes/2026-10-21-reuniao-chefia-ajustes-v1-e-piloto-terceirizados.md).

## 1. Objetivo

Preservar o contrato histórico do produto e declarar, sem ambiguidade, quais partes pertencem à
V1 mínima, ao MVP completo, a uma pendência ou a uma evolução futura.

Esta versão preserva os IDs históricos sempre que o requisito continua válido. Os requisitos da
reunião de 31/08 começam em RF-090. Requisitos superados não definem comportamento; são listados no
histórico.

## 2. Escopo e precedência

1. Decisões humanas datadas e o backlog ativo prevalecem sobre formulações antigas em conflito.
2. A aba **Lista completa** de `planejamento/backlog-completo.xlsx` delimita o MVP completo.
3. As abas **Sprint 9** a **Sprint 14** delimitam a V1 mínima executável.
4. Um requisito abaixo só é exigível na V1 quando a matriz de escopo o marcar como `V1 mínima`.
5. As fontes em `levantamento-de-requisitos/fontes-canonicas/` são evidências preservadas; não são
   uma segunda autoridade vigente.

### 2.1 V1 mínima — incluído

- fundação Laravel/PostgreSQL, primeiro contrato HTTP e cliente TypeScript;
- perfis mínimos Administrador/STC e Respondente, com isolamento contextual pelo pedido da UG,
  sem definir vínculo permanente pessoa–UG;
- catálogo mínimo para o pedido contextual de uma UG, com objeto variável e objeto fixo com XLSX
  oficial; isso descreve o cenário de entrega e não fixa cardinalidade permanente;
- criação, publicação e link contextual de coleta/pedido;
- identificação mínima do respondente no pedido da sua UG;
- resposta variável com upload obrigatório e resposta fixa com XLSX oficial;
- envio, persistência mínima, consulta e download da resposta pela STC;
- comprovante de envio em PDF para o respondente e a STC;
- remoção de dados demonstrativos e correção de defeitos bloqueantes nos dois caminhos.

### 2.2 MVP completo — catálogo de capacidades

Os itens abaixo pertencem ao catálogo, mas seu status de planejamento continua sendo o da aba
**Lista completa** e da [matriz de rastreabilidade](funcionalidades/rastreabilidade-backlog.md).
Itens **A definir** não são contrato executável nem acréscimo à V1.

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
- prorrogação 5+5 e orientação de repasse do link ao setor responsável;
- histórico e estados.
- extrato macro filtrado para pessoa autorizada da STC, com formato final ainda pendente.
- painel de leitura do Gabinete sobre todos os ciclos, com download de respostas e histórico.

Essas capacidades permanecem no produto apenas conforme seu status na matriz abaixo e na aba
**Lista completa**. Sua presença nesta seção não as promove à V1 mínima.

### 2.3 Excluído do MVP atual ou futuro

- edição do Tesauro externo;
- integração automática com SEI;
- unificação automática de planilhas;
- correlação automática anexo↔linha;
- IA para validar veracidade;
- ranking;
- regras definitivas de sigilo;
- comportamento definitivo de envio atrasado;
- reextração automática do catálogo após nova versão do Tesauro.
- exportação de arquivos, conteúdo de respostas, nomes de respondentes ou logs individuais no
  extrato macro da STC; essa restrição não reduz o download integral confirmado para o Gabinete.

## 3. Requisitos funcionais

### 3.0 Matriz de escopo dos IDs preservados

| Status | IDs e leitura obrigatória |
| --- | --- |
| **V1 mínima** | RF-010 e RF-100 somente como identificação e link contextual mínimos, associados ao pedido publicado da UG e sem resolver o vínculo definitivo pessoa–UG; RF-081 somente como publicação sem duplicidade; RF-091, RF-092, RF-093, RF-020 e RF-061 somente no recorte mínimo do pedido contextual e checagem mínima; RNF-001, RNF-005, RNF-007 e RNF-008; RN-006 e RN-023; CA-003, CA-013 e CA-016 somente nos limites desta V1. |
| **MVP completo — planejado ou A definir** | Todos os demais RF, RNF, RN e CA não marcados como superados, pendentes ou futuros. Eles permanecem no catálogo da aba **Lista completa**, sem data de entrega implícita. |
| **Pendente** | RF-029; RNF-002, RNF-009, RNF-010, RNF-011 e RNF-012; RN-019, RN-020; CA-015; e qualquer requisito dependente de identidade pessoa–UG, segurança, retenção, infraestrutura, SEI, prazo ou formato final de extrato. |
| **Futuro** | IA, OCR, ranking, integração automática com SEI, unificação de planilhas, correlação automática anexo↔linha, regras definitivas de sigilo, obras especializadas e reextração automática do Tesauro. |
| **Superado** | Os IDs enumerados em [Histórico de requisitos superados](#7-histórico-de-requisitos-superados) não definem comportamento. |

Quando uma linha estiver em mais de uma situação, prevalece a mais restritiva: `superado` >
`pendente` > `MVP completo` > `V1 mínima`.

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
permissão da pessoa autenticada. Ciclo sem número SEI é estado transitório: todo ciclo deve receber
número SEI antes do encerramento.

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
Todo Servidor STC pode visualizar integralmente o Catálogo e o diretório de UGs. Somente quem
detiver a capacidade `catalogo-e-ugs` pode editar objetos, campos, anexos, UGs, associações
objeto↔UG e modelos XLSX oficiais, com auditoria de autor, data, valor anterior e valor novo. A
aprovação pode ser feita pelo próprio autor e só afeta ciclos futuros; snapshots publicados
permanecem imutáveis.

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
Objeto variável nunca usa planilha oficial de preenchimento. Quando for publicado para resposta,
a contribuição deve conter ao menos um upload publicado; campos diretos podem complementar a
resposta, mas não concluem o envio isoladamente.

### 3.2 UGs, adjuntas e participantes

**RF-007 — Gerenciar ponto focal**
Uma UG pode possuir ponto focal. Seu papel no ciclo é observador ou coordenador conforme o toggle
daquela UG.

**RF-009 — Cadastrar respondente pelo ponto focal — SUPERADO em 2026-09-02**
Não implementar. O ponto focal envia o link por e-mail e a pessoa realiza o próprio cadastro,
conforme RF-102.

**RF-010 — Identificar respondente pelo link**
Uma pessoa deve poder se identificar no link, passar pela verificação configurada e receber
acesso imediato à contribuição, sem aprovação prévia do focal.

**RF-052 — Cadastrar adjunta de forma híbrida — SUPERADO em 2026-09-02**
Não implementar como cadastro pelo focal. A adjunta chega pelo autocadastro do convidado, conforme
RF-102.

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

**RF-063 — Exigir o mínimo configurado por caixa — SUPERADO em 2026-09-02**
Não implementar mínimo numérico configurável por caixa. O piso vigente depende da obrigatoriedade
da planilha principal, conforme RF-093.

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
gerar alerta de incompletude, não não ocorrência do campo inteiro. A confirmação é informação
encaminhada à STC, não ato de ciência exigido de terceiro; não existe fila de ciência pendente.

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
Enquanto o ciclo estiver aberto, o Servidor STC pode reverter a validação com motivo obrigatório; o
registro validado permanece no Histórico. Encerrado o ciclo, a resposta validada é imutável, e novo
número SEI não a reabre. O efeito da reversão no prazo permanece em P-060.

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

### 3.8 Orientação quando a informação pertence a outro setor

**RF-049 — Indicar possível responsável — SUPERADO em 2026-09-02**
Não implementar indicação estruturada de outra UG ou adjunta; aplica-se RF-107.

**RF-078 — Efetivar redirecionamento pela STC — SUPERADO em 2026-09-02**
Não implementar. Não existe pendência de redirecionamento.

**RF-079 — Atribuir à nova UG — SUPERADO em 2026-09-02**
Não implementar atribuição decorrente de redirecionamento.

**RF-080 — Ocultar da UG anterior — SUPERADO em 2026-09-02**
Não implementar ocultação decorrente de redirecionamento.

### 3.9 Histórico e painéis

**RF-017 — Exibir histórico autorizado**
Cada perfil deve visualizar os eventos permitidos no seu âmbito. O âmbito do Gabinete é a
totalidade dos ciclos, em andamento e encerrados, sem poder de alteração.

**RF-027 — Fornecer painel da STC**
A STC deve acompanhar ciclos, UGs, contribuições, prazos, solicitações e validações.

**RF-028 — Fornecer painel da UG**
O focal deve acompanhar adjuntas, respondentes, desfechos e prazo institucional.

**RF-031 — Auditar ações relevantes**
Criação, publicação, registro de número SEI, reiteração, acesso, envio, correção, não ocorrência,
edição, prorrogação, exclusão e validação devem gerar eventos.

**RF-039 — Exportar comprovantes e dados autorizados**
Perfis autorizados devem obter comprovantes dos eventos e arquivos vigentes. O Gabinete pode baixar
as respostas de qualquer UG e extrair o histórico, em leitura. Uso com dados reais depende da
política ainda aberta em P-012/P-039.

**RF-097 — Separar os contextos de auditoria**
O Detalhe do Ciclo deve apresentar mudanças estruturais da STC. O Histórico deve apresentar eventos
da coleta por UG, separar movimentações gerais dos eventos de cada resposta e ser o destino do log
completo aberto pela Validação.

**RF-098 — Exportar o filtro atual do Histórico**
Pessoa autorizada deve poder solicitar XLSX macro com exatamente os filtros ativos, por ciclo/coleta
e UG. O arquivo não deve conter arquivos, conteúdo de resposta, nomes de respondentes ou eventos
individuais. Seu modelo permanece dependente de P-050.

**RF-099 — Restringir extrato e operações manuais de SEI por capacidade**
O perfil Servidor STC é único e admite duas capacidades: `sei-link-texto`, que habilita registrar o
número SEI, copiar o link e copiar o texto para o processo; e `catalogo-e-ugs`, que habilita alterar
o Catálogo operacional e o diretório de UGs. A exportação do histórico é disponível a todo Servidor
STC. Nenhum perfil nominal deve ser criado para uma pessoa.

**RF-100 — Preservar o contexto da porta de entrada**
O login institucional deve abrir o painel do perfil identificado. A autenticação iniciada pelo link
do ciclo deve preservar o token e levar diretamente à coleta, continuando pela escolha de UG,
adjunta e confirmação. `/login` é a porta dos painéis e admite o perfil Gabinete.

### 3.10 Requisitos consolidados após 31/08

**RF-101 — Excluir ciclo publicado**
O Servidor STC deve poder excluir ciclo criado por engano, inclusive após receber resposta. O link
deixa de ser válido e o ciclo correto é criado do zero; respostas enviadas permanecem armazenadas.

**RF-102 — Convidar respondente e adjunta por e-mail**
O ponto focal deve poder enviar pelo e-mail institucional um link de autocadastro. Quem recebe
informa os próprios dados e passa a integrar o cadastro da UG. O canal também apoia o repasse do
link ao setor, a notificação do ponto focal e login/identificação. A infraestrutura depende de
B-002.

**RF-103 — Manter estado aberto/encerrado do ciclo**
O ciclo deve ter estado explícito de aberto ou encerrado. O encerramento é manual, conforme RF-026,
e fecha a janela de reversão da validação.

**RF-104 — Cadastrar o modelo XLSX de cada objeto**
Cada objeto do Catálogo deve ter seu modelo XLSX oficial cadastrado. O sistema disponibiliza o
modelo cadastrado; não gera planilha para o respondente.

**RF-105 — Exportar o Catálogo no formato do Tesauro**
O Catálogo deve exportar a base no mesmo formato do Tesauro que a alimentou originalmente. Havendo
mudança pendente de aprovação, a exportação fica bloqueada.

**RF-106 — Fornecer painel do Gabinete**
O Gabinete deve ter painel próprio, em leitura, com contagens de ciclos criados, coletas respondidas
e coletas não respondidas, além de acesso ao histórico com extração.

**RF-107 — Orientar quando a informação é de outro setor**
Quando a UG não detém a informação, a plataforma deve orientar o repasse do link ao setor
responsável. Não havendo o dado em setor nenhum, a UG declara ausência total com justificativa
obrigatória, sem indicar outra UG como detentora.

## 4. Requisitos não funcionais

| ID | Categoria | Requisito |
|---|---|---|
| RNF-001 | Segurança | Autenticação e autorização devem restringir ação por perfil, UG, coleta e contribuição. |
| RNF-002 | Privacidade | Uma UG não pode visualizar dados de outra, salvo histórico e respostas acessíveis à STC e ao Gabinete; uso real pelo Gabinete depende de P-012/P-039. |
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
| RN-001 | Decisões humanas datadas prevalecem nos pontos que alteram o contrato; este levantamento é a consolidação normativa vigente e `contexto.md` preserva contexto e histórico. |
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
| RN-018 | SUPERADA em 2026-09-02: não existe redirecionamento; aplica-se a orientação do RF-107. |
| RN-019 | O método definitivo de autenticação permanece pendente. |
| RN-020 | Decisões pendentes não devem ser implementadas como definitivas. |
| RN-021 | Edição do catálogo só afeta ciclos novos; cada ciclo publicado preserva seu snapshot. |
| RN-022 | A validação pode ser revertida com motivo obrigatório enquanto o ciclo estiver aberto; o evento validado permanece no Histórico e o efeito no prazo depende de P-060. |
| RN-023 | Objeto variável não gera nem recebe XLSX; deve possuir campo direto, upload ou ambos. |
| RN-024 | Resposta parcial continua respondida e suas não ocorrências são contadas separadamente. |
| RN-025 | As capacidades `sei-link-texto` e `catalogo-e-ugs` pertencem ao perfil Servidor STC e não ao nome de uma pessoa. |

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

### CA-003 — Conteúdo mínimo conforme o modelo oficial

- Dada contribuição cuja planilha oficial principal seja obrigatória,
- quando a planilha principal não tiver sido enviada,
- então a finalização deve permanecer bloqueada, ainda que existam anexos;
- e, sem planilha principal obrigatória, a ausência total de uploads também bloqueia;
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
- e o fluxo segue diretamente para a coleta, com escolha de UG, adjunta e confirmação.

### CA-017 — Reversão de validação

- Dada uma resposta validada em ciclo aberto,
- quando Servidor STC solicitar `Reverter validação` com motivo,
- então o registro validado permanece no Histórico e a resposta volta ao estado editável aplicável;
- e, com ciclo encerrado ou sem motivo, a operação é bloqueada.

### CA-018 — Consulta do Gabinete

- Dado usuário do perfil Gabinete,
- quando abrir seu painel ou histórico,
- então pode consultar todos os ciclos e baixar respostas;
- e nenhum controle de mutação fica disponível.

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
- **RF-009 e RF-052:** cadastro pelo focal — superados pelo convite e autocadastro do RF-102.
- **RF-049 e RF-078 a RF-080:** indicação e redirecionamento — superados pela orientação do RF-107.
- **RF-063:** mínimo numérico por caixa — superado pelo piso orientado à planilha principal do
  RF-093.

## 8. Pendências

Os requisitos não definidos estão centralizados em
[`contexto.md`](contexto.md). Este documento não deve atribuir comportamento
definitivo a essas questões.
