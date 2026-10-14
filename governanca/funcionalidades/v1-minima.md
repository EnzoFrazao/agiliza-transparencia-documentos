# V1 mínima — Sprints 9 a 14

Este documento lista cada atividade granular planejada para a V1 uma única vez. Os critérios de
aceite são os registrados nas respectivas abas do backlog ativo.

## Situação observada em 2026-10-14

O repositório canônico privado
[`Oxygeni-Projetos-Estagiarios/agiliza-stc`](https://github.com/Oxygeni-Projetos-Estagiarios/agiliza-stc)
mantém a fundação e a V1 HTTP em `main` (`60f25d0`, PR #5 mesclado em 2026-10-14). Ela inclui
domínio persistente, rotas `/api/v1`, cliente TypeScript e telas `/v1` para os percursos fixo e
variável.

As evidências registradas no repositório canônico incluem 99 testes PHP e 408 asserções em SQLite
e PostgreSQL isolados, 64 arquivos/685 testes Vitest e dois E2E `/v1`. O PostgreSQL e as migrations
foram exercitados, e o build da imagem `app` do Compose foi verificado; retirada de dados demo,
UAT e homologação não estão concluídos. Fontes
institucionais, levantamento, atas e demais materiais de `documentos/` continuam fora do código.

| Recorte | Status técnico | Integração |
| --- | --- | --- |
| Fundação Laravel/PostgreSQL e container | Em andamento | Base em `main` (`60f25d0`); build da imagem `app` verificado em 2026-10-14 |
| Acesso, publicação, coleta e download V1 | Concluído tecnicamente | `main` (`60f25d0`, PR #5 mesclado) |
| Homologação, UAT e retirada de demos | Em andamento ou planejado | Sem integração de release |

## Pré-requisitos técnicos

| Sprint | Atividade | Critério de aceite resumido | Nó ou critério V1 |
| --- | --- | --- | --- |
| 9 | Inventariar código, banco e ferramentas | Inventário seletivo e fluxo/regras preparados para revisão. | Pré-requisito `B1` |
| 9 | Preparar o repositório canônico | Pacote de transporte sem documentos brutos ou credenciais. | Pré-requisito `B1` |
| 9 | Iniciar o container único | Estrutura inicial da aplicação separada do PostgreSQL. | Pré-requisito `B1` |
| 9 | Iniciar Laravel e a conexão PostgreSQL | Fundação sem segredo versionado e conexão configurável. | Pré-requisito `B2` |
| 9 | Preparar fluxo e regras do backend | Matriz de regras e testes de contrato propostos. | Pré-requisito `B2` |
| 10 | Concluir a fundação Laravel e PostgreSQL | Aplicação persiste dados básicos no PostgreSQL externo. | Pré-requisito `B2` |
| 10 | Criar o primeiro endpoint HTTP | Rota retorna dados reais do backend. | Pré-requisito `B3` |
| 10 | Conectar a primeira tela à API | Tela usa `/api`, sem fixture operacional. | Pré-requisito `B3` |
| 10 | Criar grupos Administrador/STC e Respondente | Grupos possuem ações distintas. | Pré-requisito `B4` |
| 10 | Vincular usuários a UGs e grupos | Respondente não vê pedido de outra UG; o vínculo definitivo pessoa–UG permanece pendente. | Pré-requisito `B4` |

## Caminho variável

| Sprint | Atividade | Critério de aceite resumido | Nó ou critério V1 |
| --- | --- | --- | --- |
| 11 | Carregar um objeto variável e uma UG | STC seleciona objeto variável e uma UG. | `S1` |
| 11 | Criar o formulário da coleta variável | STC configura objeto, destinatário e item. | `S1` → `SV` |
| 11 | Definir upload obrigatório no objeto variável | A coleta explicita a exigência de upload. | `SV` |
| 11 | Publicar a coleta variável | Publicação não deixa estado parcial. | `SPV` |
| 11 | Gerar link único da coleta | Link leva apenas ao pedido publicado. | `SPV` |
| 11 | Conectar criação, lista e detalhe da STC | STC cria, publica e consulta sem ciclo demonstrativo. | `S1` → `SPV` e `SR` |
| 12 | Abrir acesso público pelo link | Link não mostra pedidos de outra UG. | `R1` |
| 12 | Identificar o respondente no acesso inicial | Respondente entra na contribuição correta sem SSO completo. | `R2` |
| 12 | Exibir campos e anexos do objeto variável | Respondente vê somente itens publicados. | `V1` |
| 12 | Guardar o upload variável até o envio | Arquivo persiste no rascunho mínimo. | `V3` |
| 12 | Bloquear envio variável sem arquivo | Campos diretos sem upload não concluem a resposta. | `V4` |
| 12 | Enviar a resposta variável | Resposta e arquivo ficam disponíveis à STC. | `V5` |
| 12 | Exibir e baixar a resposta variável na STC | STC localiza e baixa o arquivo. | `SR` |

## Caminho fixo e fechamento da V1

| Sprint | Atividade | Critério de aceite resumido | Nó ou critério V1 |
| --- | --- | --- | --- |
| 13 | Cadastrar um objeto fixo | Objeto fica disponível para criar coleta. | `SF` |
| 13 | Associar um único XLSX oficial | Modelo fica disponível ao objeto fixo. | `SF` |
| 13 | Criar e publicar a coleta fixa | Coleta tem link e referência ao modelo. | `SF` → `SPF` |
| 13 | Disponibilizar download do XLSX oficial | Respondente baixa o modelo vinculado. | `F1` |
| 13 | Receber o XLSX preenchido | XLSX é selecionado como arquivo principal e permanece no rascunho mínimo até o envio. | `F2` → `F3` |
| 13 | Conferir o XLSX mínimo | Arquivo incompatível é recusado. | `F4` |
| 14 | Enviar a resposta fixa | XLSX enviado fica disponível à STC. | `F5` |
| 14 | Exibir e baixar a resposta fixa na STC | STC localiza e baixa a planilha. | `SR` |
| 14 | Retirar dados demo do caminho variável | Caminho variável não depende de dados demonstrativos. | Critério final do caminho `V1`–`V5` |
| 14 | Retirar dados demo do caminho fixo | Caminho fixo não depende de dados demonstrativos. | Critério final do caminho `F1`–`F5` |
| 14 | Corrigir defeitos bloqueantes | Não há defeito bloqueante nos dois fluxos mínimos. | Critério final dos dois caminhos |

## Fora da V1 mínima

SEI, prazo, prorrogação, focal, ausência total, validação humana, correção, auditoria, Gabinete,
segurança de piloto e homologação continuam no catálogo do MVP completo, mas não são etapas ou
critérios desta V1.
