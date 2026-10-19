# Relatório de andamento do código

Este diretório reúne relatórios para acompanhamento da chefia. Cada relatório deve indicar o
período, as entregas realizadas, evidências de validação, pendências e o repositório da aplicação
correspondente.

## Escopo

A aplicação canônica está em `STC/agiliza-stc/`. O protótipo legado não é a fonte da V1 HTTP; sua
cópia local foi retirada do workspace em 2026-10-19, e o histórico permanece no repositório privado
`EnzoFrazao/agiliza-transparencia`, no GitHub. A documentação institucional vigente fica
nesta raiz `STC/documentos/`; não há repositórios separados de frontend e backend para reportar.

## Saída padrão

O relatório apresenta período, entregas, arquivos principais, evidências executadas, documentação
alterada, pendências e divergências.

Relatórios sob demanda devem ser salvos nesta própria pasta com o padrão
`AAAA-MM-DD-a-AAAA-MM-DD.md`.
## 2026-09-24 — Consolidação da quarentena documental

- Preservado em governanca/decisoes-de-reunioes/ o documento original de resposta à minuta e roadmap de versões, datado de 2026-08-24; ele permanece histórico e não substitui decisões vigentes.
- Descartada a quarentena de organização de 2026-09-10 e os artefatos locais .superpowers, conforme a política de preservação por conteúdo atualizado.
- Recalculados os SHA-256 do inventário para refletir os arquivos físicos atuais, inclusive textos normalizados durante a organização.

## 2026-10-12 — Reconciliação do backlog V1

- Atualizada a planilha operacional `planejamento/backlog-completo.xlsx` sem substituir o planejamento: as abas receberam a separação entre status técnico e integração/evidência.
- Registrada a evidência da V1 HTTP em `origin/fluxos-http-v1` (`0d2d832`), nove commits à frente de `origin/main` e sem commits atrás; a integração em `main` não foi realizada.
- Registrados como em andamento a fundação operacional do container (falha de `npm ci` no build da imagem `app`), a retirada de dados demonstrativos, UAT e homologação.
- Mantido o protótipo legado isolado e sem alegar homologação institucional.

## 2026-10-14 — Pós-merge do PR #5

- Atualizada a planilha operacional e os documentos vigentes para registrar a integração da V1 HTTP em `main` (`60f25d0`, PR #5 mesclado).
- Registrado que `docker compose build app` foi verificado; a falha histórica de `npm ci` não se reproduziu.
- Mantidas como pendentes a retirada de dados demonstrativos, UAT e homologação institucional.

## 2026-10-15 — Ajuste de qualidade integrado

- O PR #6, que trocava `Blob.text()` por `FileReader.readAsText()` no teste de download da V1, foi fechado sem merge.
- O mesmo ajuste, compatível com jsdom 26, entrou em `main` pelo PR #7.

## 2026-10-17 — Recorte do Catálogo e resposta por arquivos livres

- Registrada em `governanca/decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md` a decisão de escopo da V1: só objetos fixos piloto derivados do Tesauro e pedido variável configurado no ato, sem cadastro livre de novos objetos.
- Confirmado o piloto MT-0018 com a SINFRA (UG 531010) como única destinatária.
- Registrada a revisão de 17/10: resposta por arquivos livres, sem "Salvar rascunho", uma resposta por UG e lista de informações no variável. `regras-de-negocio.md`, `v1-minima.md` e `rastreabilidade-backlog.md` passaram a apontar o recorte.

## 2026-10-19 — Atualização pós-PR #11

- Governança atualizada até o PR #12 do repositório canônico (`main` em `c6066b9`):
  - `v1-minima.md`, `rastreabilidade-backlog.md`, `contexto.md`, `regras-de-negocio.md` (versão 8.2) e o DER registram o comprovante em PDF (PR #10) e a preparação para homologação (PR #11, `18c345b`);
  - os fluxos `v1-minima-coleta-e-resposta` e `backend-v1-handoff` refletem a revisão de 17/10, e seus SVGs foram regerados;
  - `contexto.md` §28 marca o objeto-piloto como resolvido e lista as pendências de implantação da V1 para a STC e a TI.
- Atualizadas na planilha `planejamento/backlog-completo.xlsx` as colunas de status e evidência das atividades afetadas. Nomes de atividades e critérios de aceite foram preservados.
- Retirado do acervo `governanca/tesauro/Tesauro_MA_Transparente_v2_3_17_03.xlsx`, versão anterior substituída pelo Tesauro v2.6 (agosto/2026), fonte da carga piloto. A remoção foi decidida pelo responsável em 19/10/2026.
- Incluído no inventário o `relatorio-sintese-outubro.docx`, retrato do projeto até 13/10/2026, sem alteração de conteúdo.
- Removida a cópia local do protótipo legado `STC/agiliza-transparencia/`. Todos os commits já estavam no GitHub. Os stashes e os arquivos locais ignorados foram preservados fora do workspace antes da remoção.
- Recalculados os SHA-256 do inventário.
- Seguem pendentes o ambiente real, a carga operacional do piloto e o UAT com a STC e a SINFRA.

## 2026-10-19 — Encaminhamento da apresentação e da implantação da V1

- Registrado em `governanca/decisoes-de-reunioes/2026-10-19-apresentacao-v1-e-implantacao-gradual.md` o encaminhamento combinado entre Enzo e Guilherme: apresentação da V1 à chefia em 20/10/2026, teste de usabilidade pela chefia na mesma semana, ajustes, implantação na SINFRA com feedback para a versão seguinte e expansão gradual às demais UGs e objetos.
- `governanca/contexto.md` passou a apontar esse encaminhamento no bloco de encaminhamento técnico. O ambiente do teste da chefia e as datas da implantação seguem sem definição.
