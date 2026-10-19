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

## Evidência de implementação em 2026-10-19

Em `main` (`18c345b`, PR #11), cinco migrations posteriores ao `60f25d0` acrescentaram ao módulo
de publicação e respostas:

- `response_submissions`: evento de recebimento de cada envio, com protocolo, snapshot e SHA-256,
  base do comprovante em PDF (PR #10);
- pedido variável contextual sem objeto do Catálogo, com a orientação geral e a de cada arquivo
  congeladas na publicação;
- `supplementary` em `response_files`, para os “outros arquivos” de qualquer formato;
- `requested_information_snapshot` em `cycle_versions`, com a lista de informações do variável;
- fechamento do destinatário no primeiro envio (`collection_targets.closed_at`), que torna a
  resposta única por UG.

O modelo e a destinatária do MT-0018 (SINFRA, UG 531010) foram aprovados pelo responsável em
16/10 ([decisão de escopo](../decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md)).
A carga controlada está pronta, mas não foi executada em base operacional, e isso não equivale a
homologação institucional. O detalhe das colunas está em `agiliza-stc/docs/modelo-de-dados.md`.

## Limites

Keycloak, vínculo institucional definitivo, ponto focal, adjuntas, SEI, prazo, auditoria e validação
humana não são parte deste schema inicial. Arquivos ficam no armazenamento privado da aplicação; o
banco guarda apenas metadados e integridade.

## Autoridade de implementação

O DER e as tabelas executáveis estão em
`agiliza-stc/docs/modelo-de-dados.md` e nas migrations da aplicação. Este registro preserva a
decisão transversal e não replica o contrato de cada coluna.
