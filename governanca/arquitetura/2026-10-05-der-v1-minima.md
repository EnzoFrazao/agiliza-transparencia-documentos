# DER V1 mínima e acesso contextual — 2026-10-05

**Status:** decisão técnica operacional vigente.

## Decisão

O Agiliza manterá o PostgreSQL no schema físico `public`. A organização será feita por módulos
lógicos de identidade, catálogo, publicação, acesso e respostas; schemas físicos distintos só serão
reavaliados se houver múltiplas aplicações, permissões de banco independentes ou integração externa
que justifique esse custo.

O núcleo persistente é `cycle → cycle_version → collection_target`. As fixtures e o fluxo inicial
da V1 usam uma versão e uma UG por ciclo; o modelo aceita destinatários adicionais e versões
posteriores sem alteração estrutural.

O acesso do respondente é contextual: `target_access_grants` liga uma conta a um destinatário
publicado. Isto satisfaz o isolamento da V1 sem supor vínculo institucional duradouro pessoa–UG.
Uma futura `user_unit_memberships` ampliará a autorização, sem substituir concessões contextuais.

## Limites

Keycloak, vínculo institucional definitivo, ponto focal, adjuntas, SEI, prazo, auditoria e validação
humana não são parte deste schema inicial. Arquivos ficam no armazenamento privado da aplicação; o
banco guarda apenas metadados e integridade.

## Autoridade de implementação

O DER e as tabelas executáveis estão em
`agiliza-stc/docs/modelo-de-dados.md` e nas migrations da aplicação. Este registro preserva a
decisão transversal e não replica o contrato de cada coluna.
