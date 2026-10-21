# Reunião com a chefia: ajustes da V1 e piloto de terceirizados — 21/10/2026

**Origem:** reunião de apresentação da V1 à chefia da STC em 21/10/2026, com Enzo e Guilherme,
conhecida pela transcrição automática entregue pelo responsável pelo projeto; e conversa do
responsável com o Thiago, que conduz as coletas na STC, no mesmo dia.
**Status:** decisões de produto confirmadas pelo responsável; implementação não iniciada. A
transcrição é evidência e não foi incorporada ao acervo.

## Decisões e encaminhamentos

1. **O piloto passa a ser terceirizados.** Licitação deixa de ser o objeto piloto porque, segundo
   a chefia, esse dado chega por sistema, e não por coleta manual. O MT-0018 e a SINFRA saem do
   piloto. O primeiro objeto passa a ser o de trabalhadores terceirizados (MT-0015), a partir das
   informações que o Thiago já coleta. Estagiários (MT-0016) vem depois. A implantação segue um
   objeto de cada vez, para corrigir o conceito cedo se algo não funcionar.
2. **UGs do piloto.** Serão as que têm contrato de terceirização. O Thiago está levantando essas
   UGs pelos contratos; a lista ainda não foi entregue.
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
- **IA.** A chefia retomou a ideia de coleta com fricção mínima: a UG envia o que tiver, no formato
  que tiver, e a IA extrai e padroniza as informações no modelo da STC. O encaminhamento foi
  validar primeiro o fluxo atual com quem usa. Depois, a equipe apresenta uma proposta de
  arquitetura (modelo local, pago ou combinado), com infraestrutura e custo. Isso reabre a direção
  "a IA verifica e não transforma", registrada no §28 do [contexto](../contexto.md) (P-001). Nada
  foi decidido.
- **Catálogo editável.** Editar o catálogo pelo Agiliza depende do Tesauro revisado e vem depois
  dele.
- **Equipe.** Emanuel Jovito atua como tech lead. A Clarice ainda precisa se desligar do vínculo
  atual. Como contratos de bolsa de outro programa foram descontinuados, a chefia pediu que se
  confirme com a FAPEMA a situação do acordo de cooperação técnica antes desse desligamento.

## Limites

- Substitui o passo 4 da [sequência de 19/10](2026-10-19-apresentacao-v1-e-implantacao-gradual.md)
  (implantação na SINFRA com o MT-0018) e o recorte MT-0018/SINFRA da
  [decisão de 16/10](2026-10-16-recorte-catalogo-v1-e-tesauro.md).
- Revê a regra de que o objeto fixo é imutável no ciclo e usa um modelo XLSX cadastrado, sem gerar
  planilha (§32.1 e §35.3 do [contexto](../contexto.md) e [regras de negócio](../regras-de-negocio.md)).
- Não define os metadados mínimos de terceirizados, a lista de UGs, a data da homologação, quem da
  chefia testa, o formato do retorno, a varredura dos arquivos recebidos, a devolução para
  correção nem a arquitetura de IA.
- O detalhamento técnico dos ajustes está registrado no repositório da aplicação.
