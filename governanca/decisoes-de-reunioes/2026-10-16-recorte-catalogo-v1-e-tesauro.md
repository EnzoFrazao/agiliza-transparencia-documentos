# Recorte do Catálogo na V1 e evolução pelo Tesauro — 16/10/2026

**Origem:** confirmação do responsável pelo projeto nesta conversa.
**Status:** decisão de escopo; mecanismo futuro ainda não especificado.

## Decisão

- A V1 usará somente os objetos fixos do piloto derivados do Tesauro e os pedidos variáveis
  configurados no ato da coleta. Não inclui interface ou API para a STC criar novos objetos
  permanentes no Catálogo.
- Os objetos fixos piloto, seus metadados, modelos e destinatárias precisam ser aprovados e
  carregados no ambiente da V1. Os exemplos de desenvolvimento não constituem carga
  institucional; o exemplo variável genérico não define por si só um objeto institucional.
- Esclarecimento do responsável em 16/10: a coleta variável é configurada no momento do
  pedido, sem código nem cadastro permanente de objeto variável. `V1-VARIABLE` e MT-0015
  não devem ser promovidos a objetos institucionais por inferência. A representação técnica
  desse pedido contextual ainda precisa ser alinhada ao banco atual.
- A criação de outros objetos fica para depois da V1. O fluxo desejado começa pela atualização
  do Tesauro e então propaga o novo objeto ao sistema; não é cadastro livre feito apenas na
  interface do Agiliza.

Para novos objetos, esse recorte substitui a expectativa anterior de que toda alteração
posterior à carga inicial começaria diretamente no sistema. Não redefine a edição dos objetos
já existentes.

## Limites e continuidade

- A sincronização Tesauro–Catálogo ainda não foi implementada. Seu gatilho, validações,
  versionamento, auditoria e tratamento de conflitos com edições locais serão definidos na
  atividade pós-V1. Cargas futuras não podem sobrescrever silenciosamente dados operacionais,
  conforme a [decisão de 31/08](2026-08-31-reuniao-apresentacao-agiliza.md).
- Esta decisão restringe à etapa pós-V1 a criação de **novos objetos**. Não define agora como
  editar objetos já existentes; essa distinção precisa ser tratada no desenho da sincronização.
- A planilha `planejamento/backlog-completo.xlsx` mantém seus registros históricos de Sprint;
  o aceite da V1 será lido como disponibilidade dos objetos piloto, não como cadastro de
  objetos novos pela STC. A reconciliação do backlog ativo permanece necessária.

## Situação da carga em 16/10/2026

- O responsável confirmou **SINFRA (UG 531010) como única destinatária do MT-0018 neste
  piloto**. A planilha de procedimentos em Downloads confirma esse par; o mapeamento preliminar
  cita “SIGAA START GOV - SEAD” como **fonte**, sem lista de destinatárias. O recorte de uma UG
  decorre da decisão humana, não de inferência do mapeamento.
- O responsável aprovou o modelo piloto e autorizou registrar a confirmação na aba
  “Orientações”. A cópia final está em `../../../agiliza-stc/database/pilot/mt-0018-licitacao-sinfra.xlsx`,
  SHA-256 `3f752741cc4636cd4a2edbf43bbcc2e0ce7b8ae06f5023870169be046ac90b51`.
  Foi derivada do arquivo criado pelo Codex em 06/10, mudando somente `Orientações!A4`;
  os dez cabeçalhos continuam na ordem do Tesauro. A fixture de desenvolvimento foi preservada.
- A fonte Tesauro ainda marca MT-0018 **Em validação**. Seu nome indica v2.6, mas a aba
  “Instruções” diz v2.5; essa discrepância da fonte não foi alterada pela aprovação do piloto
  e continua para saneamento institucional.
- A aplicação confere o XLSX contra os metadados antes da carga e de cada publicação fixa.
  O manifesto aprovado e a cópia final estão versionados no repositório da aplicação; a carga
  é idempotente e recusa divergências. Os testes a executaram em SQLite isolado. **Nenhuma
  base operacional foi carregada** nesta sessão.
- O pedido variável é criado no ato e sem código permanente. Seu contrato técnico e os
  anexos/instruções específicos continuam pendentes na etapa própria da V1; `V1-VARIABLE` é
  apenas exemplo de desenvolvimento. A homologação integrada em PostgreSQL e Excel/LibreOffice
  permanece para a etapa 6.
