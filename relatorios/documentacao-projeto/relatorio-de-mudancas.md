# Relatório de andamento do código

Este diretório reúne relatórios para acompanhamento da chefia. Cada relatório deve indicar o
período, as entregas realizadas, evidências de validação, pendências e o repositório da aplicação
correspondente.

## Escopo

A aplicação canônica está em `STC/agiliza-stc/`. O protótipo legado permanece isolado em
`STC/agiliza-transparencia/` e não é a fonte da V1 HTTP. A documentação institucional vigente fica
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
