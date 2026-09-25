# Fluxogramas — Agiliza Transparência

## Autoridade e leitura

Esta pasta é a fonte vigente dos fluxos do produto. Ela usa o backlog ativo em
[`../../planejamento/backlog-completo.xlsx`](../../planejamento/backlog-completo.xlsx) como
referência de planejamento e as decisões consolidadas em
[`../regras-de-negocio.md`](../regras-de-negocio.md) como referência normativa.

O arquivo Mermaid em cada documento é a fonte editável. A pasta
[`imagens/`](imagens/) contém somente as exportações SVG correspondentes.

## Fluxos disponíveis

- [V1 mínima — coleta e resposta](v1-minima-coleta-e-resposta.md): recorte executável das Sprints
  9–14, com seus dois caminhos de resposta.
- [Handoff técnico do backend — V1 mínima](backend-v1-handoff.md): visão de sustentação técnica
  dos dois caminhos V1, sem antecipar contrato HTTP, schema ou pendências do MVP completo.
- [MVP completo — coleta e validação](mvp-completo-coleta-e-validacao.md): fluxo detalhado de
  coleta, resposta, coordenação e validação; distingue o que está planejado do que permanece
  pendente.
- [Gestão interna do ciclo](gestao-interna-do-ciclo.md): preparação, publicação, acompanhamento e
  encerramento institucional. Inclui a comunicação manual com o SEI, sem tratá-la como integração.

## Legenda de escopo

| Marca | Significado |
| --- | --- |
| **V1 mínima** | Entrega prevista nas Sprints 9–14. |
| **MVP completo** | Atividade da aba **Lista completa** do backlog ativo. |
| **Pendente** | Necessita definição, agendamento ou condição externa antes de virar contrato executável. |

Não se deve usar Gestão interna do ciclo nem o fluxo completo para acrescentar à V1 elementos como
SEI, prazo, focal, validação humana, auditoria ou Gabinete sem planejamento explícito.

## Convenções visuais

Os diagramas usam **faixas** para separar responsabilidades e **losangos** para decisões que mudam
o caminho. A cor identifica o papel ou a situação do nó, não uma linha do diagrama: azul para STC,
verde para UG/respondente, roxo para pré-requisito ou fonte externa, amarelo para decisão e cinza
para capacidade planejada ou pendente. Setas tracejadas representam associação, referência ou
encaminhamento que não substitui a sequência principal.
