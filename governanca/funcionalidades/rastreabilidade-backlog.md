# Rastreabilidade — backlog, fluxo e regras

**Recorte vigente de 16/10/2026:** as linhas de Sprint 11/13 sobre carregar ou cadastrar
objetos devem ser aceitas na V1 como disponibilidade do MT-0018 fixo e configuração do
pedido variável no ato, sem código nem cadastro permanente desse objeto. Não há cadastro livre
de novos objetos pela STC. O responsável aprovou MT-0018/SINFRA (UG 531010) para este
piloto e autorizou confirmar a aprovação na aba “Orientações” da cópia final do XLSX.
A carga controlada está preparada, mas não foi executada em base operacional. O Tesauro
de origem ainda diz “Em validação”; `V1-VARIABLE` e o XLSX do seeder são apenas dados de
desenvolvimento. Ver a
[decisão de escopo](../decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md).

Esta matriz preserva o nome de cada atividade da aba **Lista completa**. Quando a atividade possui
recorte nas Sprints 9–14, a terceira coluna aponta a atividade granular correspondente; quando não
possui, mantém **A definir**. Os nós remetem aos três fluxos vigentes.

## Situação técnica em 2026-10-14

O planejamento abaixo não é um registro de release. A V1 de acesso contextual, publicação, coleta
variável/fixa, arquivos, validação estrutural, envio e download está em `main` (`60f25d0`, PR #5
mesclado em 2026-10-14). A fundação Laravel/PostgreSQL foi exercitada e o build da imagem `app` do
Compose foi verificado. O ajuste de compatibilidade do teste de download com jsdom está no PR #6,
ainda em revisão. Homologação, UAT e retirada de dados demo continuam abertos.

## Resumo por capacidade

| Capacidade | Planejamento | Fluxo dominante |
| --- | --- | --- |
| Fundação, transporte, acesso e isolamento | Sprints 9–10; fundação em andamento, acesso concluído tecnicamente | V1 — pré-requisitos |
| Publicação e coleta variável/fixa | Sprints 11–14; concluída tecnicamente na branch V1 | V1 e coleta MVP |
| Coordenação, validação, histórico e operação | A definir | Coleta MVP e gestão interna |
| Qualidade, piloto e homologação | A definir; ajuste do teste jsdom em revisão no PR #6 | Transversal |

## Matriz granular

| Atividade macro do backlog | Planejamento atual | Atividade granular / nó do fluxo | Regras aplicáveis |
| --- | --- | --- | --- |
| Consolidar fontes e decisões vigentes da V1 | A definir | Governança; não é etapa de usuário | RN-001, RNF-004 |
| Criar backlog normativo e planilha operacional por sprint | A definir | Governança; não é etapa de usuário | RNF-004 |
| Aplicar os três handoffs de 31/08 somente no snapshot | A definir | Transversal de interface; fora dos fluxos | RNF-005 a RNF-007 |
| Validar visualmente os handoffs em 375, 768, 1024 e 1440 px | A definir | Transversal de interface; fora dos fluxos | RNF-005 a RNF-007 |
| Reconciliar o backlog com decisões e telas aprovadas | A definir | Governança; não é etapa de usuário | RN-001, RNF-004 |
| Inventariar e preparar a migração do ambiente local: interface, API, banco e ferramentas | Sprint 9 | **S9:** Inventariar código, banco e ferramentas → V1:B1 | RN-001, RN-019, RN-020 |
| Consolidar no repositório canônico guia, backlog, contratos-alvo e specs sanitizadas | Sprint 9 | **S9:** Preparar o repositório canônico → V1:B1 | RN-001, RNF-004 |
| Migrar seletivamente interface e API ao repositório canônico e ao único container de aplicação | Sprints 9 e 14 | **S9:** Iniciar o container único; **S14:** retirar dados demo → V1:B1 e critério final | RNF-008 |
| Criar fundação Laravel com PostgreSQL externo e configuração de desenvolvimento compatível com o container único | Sprints 9 e 10 | **S9–10:** Iniciar/concluir Laravel e PostgreSQL → V1:B2 | RNF-008 |
| Implementar health check, logs básicos e gate unificado de testes da aplicação | A definir | Transversal; fora dos fluxos | RNF-010 |
| Definir contexto de ator controlado e autorização desacoplada do login | Sprint 10 | **S10:** Criar grupos; vincular usuários a UGs e grupos → V1:B4 | RNF-001, RN-019, RN-020 |
| Aprovar e implementar o primeiro contrato HTTP real e cliente TypeScript | Sprint 10 | **S10:** Criar endpoint; conectar primeira tela → V1:B3 | RNF-008 |
| Preparar fundação de homologação da aplicação em container único | A definir | Transversal; fora dos fluxos | RNF-009 a RNF-012 |
| Persistir o Catálogo mínimo e as UGs necessárias à publicação | Sprints 11 e 13 | **S11:** Carregar objeto/UG; **S13:** cadastrar objeto fixo → V1:S1 e SF | RF-090, RF-091, RF-092 |
| Configurar ciclo de objeto variável sem modelo XLSX obrigatório | Sprint 11 | **S11:** Criar formulário; definir upload → V1:SV | RF-092, RF-093, RN-023, CA-013 |
| Cadastrar e versionar modelo XLSX oficial obrigatório por objeto fixo | Sprint 13 | **S13:** Associar XLSX oficial → V1:SF | RF-091, RF-104, CA-003 |
| Publicar ciclo de modo atômico e idempotente | Sprints 11 e 13 | **S11/S13:** Publicar coleta variável/fixa → V1:SPV e SPF | RF-081, RNF-008 |
| Publicar sem SEI e congelar toggle focal por UG | A definir | Gestão:P5; contrato pendente | RF-082, RF-086, RN-020 |
| Integrar Criar Ciclo, Ciclos e Detalhe ao backend | Sprints 11 e 14 | **S11:** Conectar criação/lista/detalhe; **S14:** retirar demos → V1:S1, SPV, SPF | RNF-008 |
| Auditar criação e publicação do ciclo | A definir | Coleta MVP:C3; capacidade pendente | RF-031, RNF-003 |
| Convidar respondentes e adjuntas por e-mail institucional | A definir | Coleta MVP:U1/U4; capacidade pendente | RF-102, RNF-009 |
| Criar atribuição e contribuição separada por pessoa e adjunta | Sprint 12 | **S12:** identificar respondente → V1:R2 | RF-010, RF-057, RF-100; RN-019 |
| Receber campos diretos e uploads em objeto variável sem modelo XLSX obrigatório | Sprint 12 | **S12:** exibir campos/anexos; guardar upload → V1:V1–V3 | RF-092, RF-093, RN-023, CA-013 |
| Baixar, preencher e enviar o modelo XLSX oficial obrigatório do objeto fixo | Sprint 13 | **S13:** baixar/receber XLSX → V1:F1–F3 | RF-091, RF-061, CA-003 |
| Salvar rascunho e arquivos vigentes em storage desacoplado | Sprints 12 e 13 | **S12/S13:** guardar arquivo no rascunho → V1:V3 e F3 | RF-014, RF-065 |
| Enviar pacote completo e emitir comprovante auditável | Sprints 12 e 14 | **S12/S14:** enviar resposta → V1:V5 e F5; comprovante ainda sem aceite granular | RF-016, RNF-003 |
| Integrar painéis e contribuição às APIs da sprint | Sprints 12 e 14 | **S12/S14:** exibir e baixar resposta → V1:SR | RNF-008 |
| Aplicar modos direto, focal coordenador e focal observador | A definir | Coleta MVP:U2–U4 e F1–F2 | RF-059, RF-087, RN-011 |
| Preservar o escopo durante a revisão focal | A definir | Coleta MVP:F2; capacidade pendente | RF-094, RN-005 |
| Declarar ausência total de informações | A definir | Coleta MVP:U5–U6 | RF-047, RF-066, CA-006 |
| Detectar campo direto ou upload ausente em objeto variável antes do envio | Sprints 11 e 12 | **S11/S12:** definir upload; bloquear sem arquivo → V1:SV e V4 | RF-093, RN-023, CA-013 |
| Validar o modelo XLSX obrigatório do objeto fixo antes do envio | Sprint 13 | **S13:** conferir XLSX mínimo → V1:F4 | RF-020, RF-061, CA-003 |
| Confirmar não ocorrências e manter resposta parcial como respondida | A definir | Coleta MVP:U9–U10 | RF-095, RF-096, RN-024, CA-005, CA-014 |
| Conferir contribuições e encaminhar o conjunto focal à STC | A definir | Coleta MVP:F1–F2 | RF-059, RF-060, CA-004 |
| Apresentar pacote e completude para decisão humana da STC | A definir | Coleta MVP:S3–S4 | RF-022, RN-014 |
| Devolver contribuição ou item específico com um motivo | A definir | Coleta MVP:S4–S5 | RF-022, RF-064, CA-007 |
| Corrigir e reenviar somente a contribuição afetada | A definir | Coleta MVP:S5 → U8 | RF-023, RF-024, CA-007 |
| Persistir o estado do ciclo, validar e permitir reversão controlada | A definir | Coleta MVP:S4–S6; Gestão:A4–A5 | RF-025, RF-103, RN-022, CA-017 |
| Separar auditoria de ciclo, coleta e respostas | A definir | Coleta MVP:S3/S6/S7 | RF-097, RNF-003 |
| Integrar Validação e Histórico às APIs reais | A definir | Coleta MVP:S3–S7 | RF-017, RF-022, RNF-008 |
| Registrar números SEI e iniciar ou reiterar o prazo | A definir | Gestão:A2–A3 | RF-005, RF-085, RN-002, RN-017 |
| Operar duas prorrogações separadas de cinco dias úteis | A definir | Gestão:A2–A3 | RF-074 a RF-077, CA-008 |
| Tratar solicitações de prorrogação pelo modo da UG | A definir | Gestão:A2–A3; coordenação focal pendente | RF-074, RF-075, RN-011 |
| Encerrar manualmente coleta e ciclo | A definir | Gestão:A4–A6 | RF-026, RF-103 |
| Manter e exportar o Catálogo para ciclos futuros | A definir | Coleta MVP:C1; capacidade pendente | RF-088, RF-105, RN-021 |
| Entregar dashboard operacional com unidades e drill-downs explícitos | A definir | Gestão:A1; capacidade pendente | RF-027, RF-028 |
| Completar Histórico e consultas do Gabinete | A definir | Coleta MVP:S7 | RF-017, RF-106, CA-018 |
| Copiar link e texto manual para uso no processo SEI | A definir | Gestão:E1–E2 | RF-099, RN-025 |
| Operar o Diretório de UGs como consulta contextual | A definir | Coleta MVP:C1/U1; capacidade pendente | RF-002, RF-090 |
| Excluir ciclo sem apagar respostas armazenadas | A definir | Gestão:P2/P5; capacidade pendente | RF-101 |
| Conectar login institucional ao contexto de ator | Sprint 10 | **S10:** criar grupos e vínculo contextual → V1:B4 | RF-010, RNF-001, RN-019 |
| Conectar acesso contextual pelo link estável | Sprints 11, 12 e 13 | **S11/S12/S13:** gerar/abrir link → V1:SPV, SPF e R1 | RF-046, RF-100, CA-016 |
| Aplicar isolamento definitivo de perfis, UGs e capacidades | Sprint 10 | **S10:** vincular usuários a UGs e grupos → V1:B4 | RNF-001, RN-019, RN-020 |
| Exportar o filtro atual do Histórico em XLSX macro | A definir | Coleta MVP:S7; capacidade pendente | RF-098, CA-015 |
| Remover dados fictícios e acessos de demonstração do build de homologação | Sprint 14 | **S14:** retirar dados demo variável/fixo → critério final V1 | RNF-008 |
| Fechar segurança, upload, privacidade e retenção mínimas para o piloto | A definir | Transversal; fora dos fluxos | RNF-001, RNF-002, RNF-009 |
| Verificar observabilidade, backup, recuperação e rollback em homologação | A definir | Transversal; fora dos fluxos | RNF-010, RNF-011 |
| Executar acessibilidade, responsividade, regressão e UAT ponta a ponta | Sprint 14 | **S14:** corrigir defeitos bloqueantes → critério final V1 | RNF-005 a RNF-008 |
| Emitir decisão de prontidão para piloto em homologação | A definir | Transversal; fora dos fluxos | RNF-009 a RNF-012 |

Uma linha **A definir** descreve uma capacidade preservada no MVP completo, mas não autoriza sua
implementação na V1 mínima.
