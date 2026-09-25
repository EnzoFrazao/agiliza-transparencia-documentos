# MVP completo — catálogo do backlog ativo

**Fonte:** aba **Lista completa** de `planejamento/backlog-completo.xlsx`.  
**Regra de leitura:** todas as atividades abaixo pertencem ao catálogo do MVP completo. A coluna de
planejamento reproduz o tratamento atual do backlog; ela não equivale a confirmação de entrega.

## Fundação, transição e qualidade

| Atividade | Planejamento atual | Parecer Guilherme |
| --- | --- | --- |
| Consolidar fontes e decisões vigentes da V1 | A definir | sem marcação |
| Criar backlog normativo e planilha operacional por sprint | A definir | sem marcação |
| Aplicar os três handoffs de 31/08 somente no snapshot | A definir | sem marcação |
| Validar visualmente os handoffs em 375, 768, 1024 e 1440 px | A definir | sem marcação |
| Reconciliar o backlog com decisões e telas aprovadas | A definir | sem marcação |
| Inventariar e preparar a migração do ambiente local: interface, API, banco e ferramentas | Sprint 9 | ok |
| Consolidar no repositório canônico guia, backlog, contratos-alvo e specs sanitizadas | Sprint 9 | não |
| Migrar seletivamente interface e API ao repositório canônico e ao único container de aplicação | Sprints 9 e 14 | ok |
| Criar fundação Laravel com PostgreSQL externo e configuração de desenvolvimento compatível com o container único | Sprints 9 e 10 | ok |
| Implementar health check, logs básicos e gate unificado de testes da aplicação | A definir | não |
| Preparar fundação de homologação da aplicação em container único | A definir | não |
| Remover dados fictícios e acessos de demonstração do build de homologação | Sprint 14 | não |
| Fechar segurança, upload, privacidade e retenção mínimas para o piloto | A definir | não |
| Verificar observabilidade, backup, recuperação e rollback em homologação | A definir | não |
| Executar acessibilidade, responsividade, regressão e UAT ponta a ponta | Sprint 14 | não |
| Emitir decisão de prontidão para piloto em homologação | A definir | não |

## Acesso, atores e integração

| Atividade | Planejamento atual | Parecer Guilherme |
| --- | --- | --- |
| Definir contexto de ator controlado e autorização desacoplada do login | Sprint 10 | não |
| Aprovar e implementar o primeiro contrato HTTP real e cliente TypeScript | Sprint 10 | ok |
| Conectar login institucional ao contexto de ator | Sprint 10 | ok |
| Conectar acesso contextual pelo link estável | Sprints 11, 12 e 13 | ok |
| Aplicar isolamento definitivo de perfis, UGs e capacidades | Sprint 10 | ok |
| Convidar respondentes e adjuntas por e-mail institucional | A definir | não |
| Criar atribuição e contribuição separada por pessoa e adjunta | Sprint 12 | ok |
| Aplicar modos direto, focal coordenador e focal observador | A definir | não |
| Operar o Diretório de UGs como consulta contextual | A definir | sem marcação |

## Catálogo, criação e publicação

| Atividade | Planejamento atual | Parecer Guilherme |
| --- | --- | --- |
| Persistir o Catálogo mínimo e as UGs necessárias à publicação | Sprints 11 e 13 | ok |
| Configurar ciclo de objeto variável sem modelo XLSX obrigatório | Sprint 11 | ok |
| Cadastrar e versionar modelo XLSX oficial obrigatório por objeto fixo | Sprint 13 | ok |
| Publicar ciclo de modo atômico e idempotente | Sprints 11 e 13 | ok |
| Publicar sem SEI e congelar toggle focal por UG | A definir | não |
| Integrar Criar Ciclo, Ciclos e Detalhe ao backend | Sprints 11 e 14 | ok |
| Auditar criação e publicação do ciclo | A definir | não |
| Manter e exportar o Catálogo para ciclos futuros | A definir | sem marcação |
| Excluir ciclo sem apagar respostas armazenadas | A definir | sem marcação |

## Coleta, arquivos e entrega

| Atividade | Planejamento atual | Parecer Guilherme |
| --- | --- | --- |
| Receber campos diretos e uploads em objeto variável sem modelo XLSX obrigatório | Sprint 12 | ok |
| Baixar, preencher e enviar o modelo XLSX oficial obrigatório do objeto fixo | Sprint 13 | ok |
| Salvar rascunho e arquivos vigentes em storage desacoplado | Sprints 12 e 13 | não |
| Enviar pacote completo e emitir comprovante auditável | Sprints 12 e 14 | não |
| Integrar painéis e contribuição às APIs da sprint | Sprints 12 e 14 | não |
| Detectar campo direto ou upload ausente em objeto variável antes do envio | Sprints 11 e 12 | ok |
| Validar o modelo XLSX obrigatório do objeto fixo antes do envio | Sprint 13 | ok |
| Confirmar não ocorrências e manter resposta parcial como respondida | A definir | sem marcação |
| Declarar ausência total de informações | A definir | sem marcação |
| Preservar o escopo durante a revisão focal | A definir | sem marcação |

## Tratamento institucional e operação

| Atividade | Planejamento atual | Parecer Guilherme |
| --- | --- | --- |
| Conferir contribuições e encaminhar o conjunto focal à STC | A definir | sem marcação |
| Apresentar pacote e completude para decisão humana da STC | A definir | sem marcação |
| Devolver contribuição ou item específico com um motivo | A definir | sem marcação |
| Corrigir e reenviar somente a contribuição afetada | A definir | sem marcação |
| Persistir o estado do ciclo, validar e permitir reversão controlada | A definir | sem marcação |
| Separar auditoria de ciclo, coleta e respostas | A definir | sem marcação |
| Integrar Validação e Histórico às APIs reais | A definir | sem marcação |
| Registrar números SEI e iniciar ou reiterar o prazo | A definir | sem marcação |
| Operar duas prorrogações separadas de cinco dias úteis | A definir | sem marcação |
| Tratar solicitações de prorrogação pelo modo da UG | A definir | sem marcação |
| Encerrar manualmente coleta e ciclo | A definir | sem marcação |
| Entregar dashboard operacional com unidades e drill-downs explícitos | A definir | sem marcação |
| Completar Histórico e consultas do Gabinete | A definir | sem marcação |
| Copiar link e texto manual para uso no processo SEI | A definir | sem marcação |
| Exportar o filtro atual do Histórico em XLSX macro | A definir | sem marcação |

## Limite do catálogo

O backlog não programa integração automática com o SEI. O fluxo de gestão interna do ciclo apenas
descreve a operação manual possível no produto completo. Funcionalidades marcadas **A definir** não devem ser tratadas
como escopo da V1 mínima.
