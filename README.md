# Documentação STC

Esta é a biblioteca documental única do Agiliza Transparência. Ela contém material institucional
não técnico, organizado por autoridade e finalidade. Código, specs, prompts e memória técnica
permanecem em `STC/agiliza-transparencia`.

## Estrutura

| Local | Conteúdo e autoridade |
| --- | --- |
| `governanca/` | Única fonte vigente: contexto, regras de negócio, fluxogramas, funcionalidades, perfis, decisões, mapeamentos e tesauros. |
| `levantamento-de-requisitos/entrevistas/` | Entrevistas originais, preservadas como evidência. |
| `levantamento-de-requisitos/fontes-canonicas/` | Fontes institucionais, minutas, requisitos e decisões originais; históricos de 2026-08-13 e 2026-09-01; versões históricas de fluxogramas. Não são vigentes. |
| `planejamento/` | `backlog-completo.xlsx` é o único backlog vigente. `fontes-historicas/` preserva planejamento recebido que não é operacional. |
| `relatorios/FAPEMA/` | Relatórios quinzenais, trimestrais e modelos FAPEMA. |
| `relatorios/documentacao-projeto/` | Relatórios de acompanhamento documental do projeto para a chefia. |

## Documentos vigentes

- [Contexto](governanca/contexto.md)
- [Regras de negócio](governanca/regras-de-negocio.md)
- [Fluxogramas](governanca/fluxogramas/README.md)
- [Funcionalidades](governanca/funcionalidades/README.md)
- [Perfis e permissões](governanca/perfis-e-permissoes.md)
- [Decisões de reunião](governanca/decisoes-de-reunioes/)
- [Backlog completo](planejamento/backlog-completo.xlsx)

## Evidências e histórico

As fontes originais foram classificadas uma única vez por assunto; não há espelho de
`DocumentosAdcionais`. As cópias de 2026-08-13 e 2026-09-01 estão preservadas em `historico/`
porque têm conteúdo diferente das fontes e documentos atuais. Elas servem para rastreabilidade e
nunca substituem `governanca/`.

O [inventário de preservação](INVENTARIO-DE-PRESERVACAO.md) lista cada arquivo, sua natureza,
origem e SHA-256. O relatório de reunião zero e a logo permanecem fora desta biblioteca.

## Limites

Não há specs, código, `node_modules`, prompts de agentes ou memória técnica nesta biblioteca.
Não publicar, enviar ou versionar alterações sem autorização explícita.
