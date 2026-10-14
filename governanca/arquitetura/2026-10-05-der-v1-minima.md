# DER V1 mínima e acesso contextual — 2026-10-05

**Status:** decisão técnica operacional vigente.

## Decisão

O Agiliza manterá o PostgreSQL no schema físico `public`. A organização será feita por módulos
lógicos de identidade, catálogo, publicação, acesso e respostas; schemas físicos distintos só serão
reavaliados se houver múltiplas aplicações, permissões de banco independentes ou integração externa
que justifique esse custo.

O núcleo persistente é `cycle → cycle_version → collection_target`. As fixtures usam uma versão por
ciclo; a publicação fixa usa exatamente as UGs cadastradas para o objeto, enquanto a variável
seleciona suas destinatárias na publicação. O modelo aceita versões posteriores sem alteração
estrutural.

Cada objeto fixo terá seu próprio modelo XLSX e um cadastro reutilizável das UGs que devem receber
suas coletas. A publicação usará exatamente essas UGs e preservará a referência ao XLSX utilizado
na versão publicada. O MT-0018 já possui um XLSX piloto derivado do Tesauro e somente SINFRA como
destinatária em carga explícita de desenvolvimento. Esse modelo e mapeamento não são homologados;
os modelos institucionais e o mapeamento completo dos objetos seguem pendentes de validação pela STC.

## Evidência de implementação em 2026-10-14

O modelo descrito está em `main` (`60f25d0`, PR #5 mesclado em 2026-10-14), incluindo publicação,
acesso contextual, rascunho, upload, envio e download. A base PostgreSQL e as migrations foram
exercitadas, e o build da imagem `app` do Compose foi verificado nesta data. A carga
MT-0018/SINFRA continua somente de desenvolvimento e não comprova homologação institucional.

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
