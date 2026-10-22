# Reunião com a chefia: ajustes da V1 e piloto de terceirizados — 21/10/2026

**Origem:** reunião de apresentação da V1 à chefia da STC em 21/10/2026, com Enzo e Guilherme. O
registro se baseia em duas transcrições automáticas entregues pelo responsável pelo projeto: uma
colada na conversa e outra gerada pela chefia a partir da gravação, que identifica quem falou.
Inclui também a conversa do responsável com o Thiago, que conduz as coletas na STC, no mesmo dia.
**Status:** decisões de produto confirmadas pelo responsável; implementação não iniciada. As
transcrições são evidência e não foram incorporadas ao acervo.

## Decisões e encaminhamentos

1. **O piloto passa a ser terceirizados.** Licitação deixa de ser o objeto piloto porque, segundo
   a chefia, esse dado chega por sistema, e não por coleta manual. O MT-0018 e a SINFRA saem do
   piloto. O primeiro objeto passa a ser o de trabalhadores terceirizados (MT-0015), a partir das
   informações que o Thiago já coleta. Estagiários (MT-0016) vem depois. A implantação segue um
   objeto de cada vez, para corrigir o conceito cedo se algo não funcionar.
2. **Destinatárias.** As destinatárias possíveis de todos os objetos são os órgãos da lista do
   portal do governo: 73 órgãos ativos em 21/10/2026, conforme a
   [cópia datada](../mapeamentos/orgaos-portal-ma-2026-10-21.md). Em terceirizados, o Tesauro diz
   "Por UG, caso haja contrato". Por isso nenhuma UG vem marcada: a STC escolhe a cada coleta, a
   partir do levantamento de contratos que o Thiago está fazendo.
3. **Tesauro com máximo e mínimos.** A Alessandra revisa o Tesauro objeto por objeto, conforme
   cada um for implantado, alinhando os metadados à prática da coleta. Os metadados do Tesauro
   passam a ser o máximo que a STC pode pedir. Uma coluna nova marca os mínimos, que são só os
   essenciais. A revisão começa por terceirizados. O objetivo é reduzir o que a UG precisa
   preencher.
4. **Homologação no ambiente da STC.** A TI da STC (Paulo) já criou o repositório no GitLab e
   separou a porta da homologação. A equipe sobe a V1 com os ajustes abaixo e testa com o objeto
   de terceirizados. A coleta de terceirizados de outubro de 2026 pode servir de teste pelo Agiliza.
5. **Conversa com quem coleta.** A chefia pediu que a proposta fosse apresentada ao Thiago. O
   responsável conversou com ele no mesmo dia, e os ajustes abaixo saíram dessa conversa.
6. **Terceirizados no Tesauro revisado.** O responsável enviou, no mesmo dia, a linha do objeto
   Trabalhador terceirizado (MT-0015) com a coluna nova de mínimos.
   - **Coleta:** manual, pelo Maranhão Transparente, no tema Pessoal. Destinatária: "Por UG, caso
     haja contrato".
   - **Máximo, 12 metadados:** Nome da Empresa, CNPJ da Empresa, Número do Contrato, Objeto do
     Contrato, Nome do Trabalhador, Função, Unidade de Lotação, Quantidade de Trabalhadores, Valor
     Contratual Global, Exercício, Data de Atualização e Órgão.
   - **Mínimos, 6 metadados:** Número do Contrato, Nome do Trabalhador, Função, Unidade de Lotação,
     Data de Atualização e Órgão.
   - **Atualidade:** 180 dias (PNTP 26, item 6.5). Normativo complementar: LAI, art. 8º, e LC
     131/2009.
   - **Orientação do Tesauro:** enviar quando houver intermediação por contrato administrativo
     formal; é vedado divulgar CPF, endereço ou dados pessoais sensíveis do trabalhador; a
     identificação da empresa e do contrato é obrigatória; não confundir com Servidor público ativo
     (MT-0014).
   - **A conferir com a Alessandra:**
     - a orientação torna obrigatória a identificação da empresa, mas os mínimos não incluem Nome
       da Empresa nem CNPJ;
     - os mínimos incluem Órgão, que a STC já conhece pela UG que responde.

## Ajustes da criação de ciclo

Valem para a V1 operacional, que passa a usar a tela de criação em cinco passos mostrada na
reunião. Hoje essa tela faz parte do protótipo, com dados demonstrativos.

1. **Ordem dos passos:** Escolha como preparar → Identifique o ciclo → Defina o conteúdo →
   Escolha as UGs → Revise e publique.
2. **Objeto fixo com informações editáveis.** Os metadados mínimos vêm marcados. A STC pode
   acrescentar outros, até o máximo do Tesauro, e retirar os marcados, até restar um. O cartão
   "Conteúdo solicitado" da revisão também acrescenta e retira informações, como a montagem do
   objeto variável.
3. **Objeto fixo com UGs editáveis.** As UGs do mapeamento vêm marcadas, e a STC pode tirar ou
   acrescentar UGs.
4. **Planilha-modelo gerada por coleta.** Na publicação, o sistema gera a planilha com as
   informações escolhidas. Duas coletas do mesmo objeto com escolhas diferentes têm planilhas
   diferentes, e cada resposta é conferida contra a planilha da sua coleta.
5. **Arquivo nas observações.** Além do texto, a STC pode anexar um arquivo de orientação, que a
   UG vê e baixa.
6. **Links depois de publicar.** O link de cada UG só existe depois da publicação. Ao publicar,
   uma janela mostra os links para copiar.
7. **Número SEI em destaque.** Continua um número SEI por ciclo, valendo para todas as UGs. A lista
   de ciclos deve mostrar com clareza se o ciclo já tem número SEI ou se está pendente.

## Outros temas da reunião

- **Portal novo.** A STC desenvolve um novo portal da transparência. Ele se organiza por eixos de
  governo (gestão pública, pessoal, emendas parlamentares, contas e resultados) e do cidadão (saúde,
  educação, segurança, habitação, programas sociais, entre outros); por agrupamentos (órgão,
  município, fornecedor, servidor, parlamentar, programa); e por temas. A princípio o Agiliza não
  muda e continua fazendo a coleta. Ficam no radar:
  - correlacionar o Tesauro com o portal;
  - acrescentar a informação de município às planilhas quando couber, para permitir esse filtro
    depois;
  - traduzir o que o Agiliza coleta para o modelo do portal.

  A chefia pediu que o responsável conheça a arquitetura da informação do portal novo.
- **Dados estruturados.** A chefia quer evoluir da guarda de arquivos para dados estruturados
  extraídos das planilhas, mesmo sem conferir o conteúdo. O momento não foi fixado (`agiliza-stc`
  P-011).
- **IA.** A Alessandra retomou a ideia de coleta com fricção mínima: a UG envia o que tiver, no
  formato que tiver, e a IA extrai e padroniza as informações no modelo da STC. A chefia vê isso
  como evolução futura, que precisa de base histórica. O encaminhamento foi validar primeiro o
  fluxo atual com quem usa. Depois, a equipe apresenta à chefia uma proposta de arquitetura
  (modelo local, pago ou combinado), com infraestrutura e custo. Isso reabre a direção "a IA
  verifica e não transforma", registrada no §28 do [contexto](../contexto.md) (P-001). Nada foi
  decidido.
- **Catálogo editável.** Editar o catálogo pelo Agiliza depende do Tesauro revisado e vem depois
  dele.
- **Equipe.** Emanuel Jovito atua como tech lead. A Clarice ainda precisa se desligar do vínculo
  atual. Como contratos de bolsa de outro programa foram descontinuados, a chefia pediu que se
  confirme com a FAPEMA a situação do acordo de cooperação técnica antes desse desligamento. O
  Guilherme vai pedir essa confirmação ao professor Sérgio, coordenador executivo que acompanha o
  processo na FAPEMA.

## Detalhes da reunião

Esta seção registra pontos ditos na reunião que não viraram decisão, mas ajudam a entender as
decisões acima. É registro da conversa, não contrato.

### Portal novo

- **Conceito.** A chefia apresentou o portal novo como uma mudança de conceito, centrada no
  cidadão, que nenhum outro estado adotou. O portal continua atendendo ao que o TCE exige, e já há
  uma proposta de mapeamento para isso.
- **Eixos de governo.**
  - Gestão pública: despesas, receitas, contratos e licitações, em grande parte automatizados.
  - Pessoal: servidores, estagiários e terceirizados.
  - Emendas parlamentares.
  - Contas e resultados.
- **Eixos do cidadão.**
  - Saúde: estabelecimentos, profissionais, medicamentos, e as despesas e contratos da área.
  - Educação: professores e escolas.
  - Segurança: delegacias, efetivo e viaturas.
  - Habitação: unidades entregues e regularização fundiária.
  - Programas sociais: programas e beneficiários.
  - Meio ambiente, entre outros.
- **Agrupamentos.** Ao escolher um agrupamento, a pessoa vê só o que está ligado a ele:
  - um órgão: os temas daquele órgão;
  - um fornecedor: despesas, empenhos, licitações vencidas, contratos e obras;
  - um servidor: remuneração, diárias e vínculos com o Estado;
  - um parlamentar: as emendas e os empenhos ligados a elas.
- **Temas e navegação.** Os temas são o último nível. A navegação mostra eixo, grupo e tema de
  forma mais explicativa que a do portal atual. Segundo a Alessandra, o portal deixa de usar o
  conceito de "jornada", que passa a ser o eixo.
- **Pesquisa.** A pesquisa leva a uma resposta direta: "folha de pagamento" ou "SEDUC", por
  exemplo. Depois, a pessoa pode refinar por órgão, servidor ou tema.
- **Outras áreas.** O portal terá dados abertos, legislação, atendimento e participação social,
  uma área com os itens do PNTP e uma ajuda inteligente em linguagem natural.
- **Município.** Hoje quase nada está estruturado por município. Uma compra grande de um órgão
  (o exemplo foi a SES) não é repartida entre os municípios.
  - O que vem de sistema provavelmente continuará sem esse recorte.
  - O que vem pelo Agiliza pode ganhar uma coluna de município no Tesauro e nas planilhas.
  - O estudo fica para depois, não nesta etapa.
- **Estrutura de dados.** A estrutura do portal terá de mudar, com tabelas de órgão, município e
  fornecedor. A arquitetura da informação precisa ser documentada; hoje está clara só para algumas
  pessoas.
- **Tesauro e portal.** O Tesauro foi construído com base na legislação, não no portal. A chefia
  considerou manter dois Tesauros correlacionados: um da informação, legal, e outro prático, do
  portal.
  - Um objeto pode alimentar vários temas: estagiários está em gestão pública e em pessoal.
  - Pessoal é o tema mais buscado do portal, por isso tem destaque próprio.
- **Coleta e publicação.** Das etapas coleta, validação, armazenamento e publicação, o Agiliza é a
  coleta. O armazenamento do Agiliza terá de se ligar ao do portal para a publicação.

### Planilhas e prática da coleta

- **Menos campos.** Quanto mais campos se pedem, mais difícil é para a UG responder, e a STC vem
  reduzindo o que pede. Por exemplo, transferências recebidas pediam cerca de dez colunas; hoje a
  STC busca os dados no CGF e no Diário Oficial e pede só o link do instrumento.
- **Não pedir o que a STC já sabe.** A planilha não precisa pedir a UG que responde. Se a STC já
  tiver o início e o fim do contrato, ou a empresa, pede só o nome e o setor de lotação.
- **Quem preenche.** Algumas informações são preenchidas pela própria STC, como a data de
  atualização e a fonte oficial; outras, pela UG.
- **Planilhas do Thiago.** São as que o Fernando montou e já estão prontas no controle dele, e
  divergem dos metadados do Tesauro. Por exemplo, a planilha de estagiários não tem instituição de
  ensino nem valor da bolsa.
- **Normativos.** Eles dizem o que precisa ser transparente (terceirizados, por exemplo), mas não
  fixam os campos. Os campos do Tesauro foram definidos pela equipe e, por isso, podem ser revistos.
- **Planilha pré-preenchida.** A STC pode mandar à UG uma planilha já pré-preenchida.
- **A quem pedir.** Para terceirizados, o Thiago usa o tipo de contrato registrado nas contratações
  para saber quais UGs têm terceirização, e manda o pedido só a elas. Estagiários vão para as
  secretarias que têm convênios.
- **Classificação no Tesauro.** Licitação aparece no Tesauro como não automatizada, mas a chefia
  disse que esse dado vem entre sistemas. A Alessandra disse que pode reclassificá-la como
  automatizada.
- **Fixo pelo formato.** Segundo a chefia, o objeto é fixo por causa do formato da planilha, não
  dos destinatários. Por isso as UGs do objeto fixo podem mudar a cada coleta.

### IA

- **Fricção mínima.** A Alessandra defende desde o início uma ferramenta de fricção zero: o
  servidor envia o que tiver, até um print, e a ferramenta transforma isso nas informações que a
  STC precisa. O motivo é a dificuldade de engajar os órgãos, para quem a coleta é trabalho a mais.
- **Pré-requisitos.** Segundo o Enzo, antes de usar IA é preciso definir um modelo de saída e os
  parâmetros da extração. A chefia concordou que também falta base histórica.
- **O que a IA buscaria.** Segundo o Guilherme, só o que a STC ainda não tem. Por exemplo, numa
  licitação, fonte, UG, objeto, processo, abertura, situação e modalidade já existem do lado da
  STC; a IA buscaria o valor estimado e o link.
- **Arquitetura.** A chefia quer saber se seria um modelo local, um pago ou os dois (o local
  extrai e o pago revisa), e qual a infraestrutura e o custo de cada opção.
- **Fluxo.** Com IA, o pedido à UG continua igual; muda o envio, porque a UG deixa de preencher a
  planilha. No sistema, mudam a geração da planilha e os parâmetros passados à IA.
- **Alcance.** A IA conferiria o conteúdo, não a veracidade.

### Telas mostradas

As telas de criação de ciclo e de lista de ciclos mostradas na reunião são do protótipo, com dados
demonstrativos. A V1 tem telas próprias, mais simples, e são elas que vão para a homologação. A
comparação tela a tela está na auditoria de telas, no repositório da aplicação. A demonstração
publicada para a reunião caiu no meio da apresentação, e o restante foi mostrado na máquina local.

### Material

As duas transcrições automáticas e os prints da criação de ciclo ficaram com o responsável e não
entraram no acervo, por decisão dele. A linha de terceirizados do Tesauro revisado foi transcrita
no item 6 das decisões.

## Limites

- Substitui o passo 4 da [sequência de 19/10](2026-10-19-apresentacao-v1-e-implantacao-gradual.md)
  (implantação na SINFRA com o MT-0018) e o recorte MT-0018/SINFRA da
  [decisão de 16/10](2026-10-16-recorte-catalogo-v1-e-tesauro.md).
- Revê a regra de que o objeto fixo é imutável no ciclo e usa um modelo XLSX cadastrado, sem gerar
  planilha (§32.1 e §35.3 do [contexto](../contexto.md) e [regras de negócio](../regras-de-negocio.md)).
- Não define a data da homologação, quem da chefia testa, o formato do retorno, a varredura dos
  arquivos recebidos, a devolução para correção nem a arquitetura de IA.
- A lista de órgãos tem a sigla EGMA repetida e não traz o código de UG. Esses pontos estão
  registrados na [cópia datada](../mapeamentos/orgaos-portal-ma-2026-10-21.md) e seguem em
  aberto.
- O detalhamento técnico dos ajustes está registrado no repositório da aplicação.
