# Decisões da reunião de apresentação do Agiliza — 31/08/2026

**Consolidada em:** 2026-09-01
**Status:** decisão institucional vigente para o levantamento da V1
**Precedência:** supera os documentos anteriores somente nos pontos expressamente listados

## Autoridade e método

Este registro consolida a reunião de apresentação das telas de 31/08/2026 e as correções expressas
confirmadas depois da reunião. Foram consultadas a minuta gerada por IA, duas transcrições do mesmo
trecho, o levantamento vigente e as confirmações posteriores do responsável pelo projeto.

Minutas e transcrições são evidências, não ordens. Uma afirmação só aparece como decisão quando foi
sustentada pelas fontes e confirmada posteriormente. Composições de layout aprovadas para o
protótipo não viram requisito institucional por este documento.

## Decisões confirmadas

### 1. Autoridade do Catálogo

- O Tesauro fornece a carga inicial e preserva a proveniência do conteúdo recebido.
- Após a carga, o banco do Agiliza é a fonte operacional do Catálogo.
- Alterações posteriores acontecem no próprio sistema, com autoria, auditoria e versionamento.
- A exportação do Catálogo é auxiliar. Editar o arquivo exportado não altera o sistema nem cria
  reimportação implícita.
- Uma futura carga do Tesauro não pode sobrescrever silenciosamente edições locais.

### 2. Objeto fixo

- O Catálogo mantém um modelo XLSX oficial e versionado.
- O ciclo referencia a versão aplicável do modelo; não gera sua estrutura durante a publicação.
- A contribuição oferece o download do modelo, recebe o XLSX preenchido e recebe os uploads
  configurados para o objeto.
- A pessoa pode deixar dados vazios, mas não deve excluir, renomear ou ocultar colunas.

### 3. Objeto variável

- Não existe XLSX de preenchimento para objeto variável.
- A configuração usa campos preenchidos diretamente no Agiliza, solicitações de upload ou ambos.
- Deve existir pelo menos um item no total; campo e upload não são obrigatórios isoladamente.

### 4. Ausência total e não ocorrências parciais

- A ação manual usa exatamente `Declarar ausência de informações`.
- Ausência total significa que a UG não possui nenhuma informação sobre o objeto no período.
- A declaração exige confirmação e justificativa e encerra o restante do formulário.
- Com coordenação focal ativa, declara o ponto focal; no modo direto, declara o respondente.
- O ponto focal consulta o escopo e não remove requisitos nem gera planilha ajustada.
- Não ocorrência parcial não é pré-selecionada manualmente.
- Antes do envio, coluna inteira vazia no XLSX fixo, campo direto vazio ou upload esperado ausente
  gera item detectado para confirmação e justificativa.
- Célula isolada vazia gera alerta de incompletude e não ausência do campo inteiro.
- Resposta parcial permanece `Respondida`; suas não ocorrências são contabilizadas separadamente.

### 5. Validação, Histórico e auditoria

- A Validação apresenta a ausência total ou as não ocorrências da resposta e encaminha a consulta
  do log completo ao Histórico; não duplica uma linha do tempo local.
- O Detalhe do Ciclo concentra mudanças estruturais promovidas pela STC no ciclo.
- O Histórico da coleta concentra as ações da STC, do ponto focal e dos respondentes naquela UG.
- Quando houver várias respostas na mesma coleta, eventos gerais permanecem separados dos eventos
  vinculados a cada resposta.

### 6. Extrato filtrado

- `Exportar filtro atual` usa exatamente o recorte ativo no Histórico.
- A futura entrega é XLSX e possui visão macro por ciclo/coleta e UG.
- O extrato identifica destinação, resposta, ausência total e quantidade de não ocorrências sem
  transformar uma resposta parcial em não respondida.
- O extrato não contém arquivos, conteúdo de planilhas, campos ou anexos, nomes de respondentes,
  textos de log ou eventos individuais.

### 7. Acesso interno e SEI

- Não existe perfil nominal `Thiago`.
- Exportar o extrato e operar as ações manuais de link/texto do processo SEI são capacidades
  específicas do perfil Servidor STC.
- Thiago é o primeiro usuário previsto para receber essas capacidades no piloto.
- A matriz completa de permissões dos servidores STC continua aberta.
- Não existe integração automática com o SEI.

### 8. Portas de entrada

- O login institucional abre o painel correspondente ao perfil identificado.
- O acesso iniciado pelo link estável preserva o ciclo e continua pela identificação de UG,
  adjunta e confirmação, inclusive quando a pessoa já possui cadastro.

## Regras substituídas

| Regra anterior | Regra vigente |
| --- | --- |
| Objeto variável seleciona campos e gera XLSX | Campos diretos e/ou uploads, sem XLSX |
| Todo ciclo gera novo XLSX na publicação | Ciclo fixo referencia modelo oficial; variável não possui XLSX |
| Focal remove itens e aprova planilha candidata | Focal consulta o escopo e pode declarar somente ausência total |
| Pessoa seleciona manualmente cada não ocorrência | Sistema detecta itens ausentes antes do envio e solicita confirmação |
| Não ocorrência compete com resposta enviada | Resposta parcial continua respondida; contagens são independentes |
| Tesauro permanece fonte operacional | Tesauro inicia a carga; Catálogo do Agiliza torna-se operacional |
| Ações exclusivas formam perfil Thiago | Capacidades específicas permanecem dentro de Servidor STC |

## Decisões visuais que não viram contrato

Continuam no âmbito do protótipo, até homologação própria:

- posição, tamanho, cor e composição de cards, gráficos, modais e linhas do tempo;
- nomes `Proposta V1` usados para comparar telas;
- dados e contagens ilustrativas dos mockups;
- escolha de componentes responsivos;
- qualquer interação apresentada apenas para demonstrar aparência.

## Pendências

- modelo, abas, colunas, tipos e formatação do extrato XLSX;
- matriz completa de permissões do perfil Servidor STC;
- reconciliação de futuras cargas do Tesauro com edições locais;
- leitura estrutural, limites e recuperação de falhas do XLSX fixo;
- persistência, justificativas e correção de não ocorrências;
- redação institucional definitiva para o texto do processo SEI;
- identidade e vínculo pessoa–UG;
- destino quando o acesso do ciclo gerar várias contribuições;
- fórmulas e destinos de detalhamento das métricas do Painel STC;
- upload, sigilo, retenção, infraestrutura e integrações externas.

## Documentos consolidados

Esta decisão deve ser refletida em:

- `contexto.md`;
- `regras-de-negocio.md`;
- `perfis-e-permissoes.md`;
- `funcionalidades.md`;
- `fluxogramas.md`;
- `contexto.md`;
- `README.md`.
