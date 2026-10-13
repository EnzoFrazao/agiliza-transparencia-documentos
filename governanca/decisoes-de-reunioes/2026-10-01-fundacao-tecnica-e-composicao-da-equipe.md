# Decisões operacionais: fundação técnica e composição da equipe — 01/10/2026

**Status:** decisão operacional interna vigente

## Escopo

Este registro consolida somente os encaminhamentos confirmados para a preparação técnica do
Agiliza. Não altera o escopo funcional da V1, não descreve o ambiente institucional da STC e não
autoriza publicação ou entrega.

## Decisões confirmadas

1. **Composição da equipe.** Clarice substitui Ariel na equipe de desenvolvimento.
2. **Banco de desenvolvimento.** O desenvolvimento usará PostgreSQL desde o início. Isto não
   pressupõe conexão antecipada ao banco institucional da STC.
3. **Evolução do schema.** Tabelas e demais alterações de schema serão criadas e evoluídas por
   migrations executadas pela aplicação. O DBeaver pode ser usado somente para inspeção; não é
   mecanismo de criação ou alteração manual do banco.
4. **Fundação do ambiente.** Guilherme é responsável por preparar a fundação local da aplicação,
   incluindo a containerização e as configurações de ambiente necessárias.
5. **Sequência de trabalho.** A equipe dará continuidade à implementação após a conclusão dessa
   fundação.
6. **Passagem ao ambiente da STC.** Nenhuma versão será enviada ao GitLab ou ao ambiente da STC
   antes de a solução estar completa e pronta para envio.

## Limites atuais

Permanece pendente a execução da fundação pelo responsável técnico. Este registro não confirma a
existência de containers, conexão com ambiente institucional, domínio persistente, API ou
homologação.
