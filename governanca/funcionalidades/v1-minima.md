# V1 mínima — Sprints 9 a 14

Este documento lista cada atividade granular planejada para a V1 uma única vez. Os critérios de
aceite são os registrados nas respectivas abas do backlog ativo.

**Recorte confirmado em 16/10/2026:** a V1 carrega somente os objetos fixos do piloto derivados
do Tesauro. A coleta variável é configurada no momento do pedido, sem código de objeto próprio.
As linhas históricas de “cadastrar objeto” abaixo não exigem que a STC crie novos
objetos permanentes pela aplicação. Essa ampliação fica após a V1 e deverá partir de atualização do
Tesauro; ver a [decisão de escopo](../decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md).

**Situação em 16/10/2026:** o responsável limitou o MT-0018 piloto à SINFRA (UG 531010)
e aprovou a cópia do XLSX com a confirmação na aba “Orientações”. O manifesto e o modelo
final estão preparados na aplicação; a carga passou em SQLite isolado, mas ainda não foi
executada em base operacional. O Tesauro de origem continua com status “Em validação” e
versão interna divergente; o mapeamento preliminar cita SEAD como **fonte**, sem determinar
destinatárias. A decisão humana define o recorte de uma UG; ver a decisão de escopo.
Os exemplos do `DevelopmentSeeder` não satisfazem o aceite
das linhas de carga/cadastro deste plano. Menções abaixo a campos digitados pelo
respondente estão superadas pelo contrato de respostas somente por arquivos.

**Revisão de 17/10/2026:** o “rascunho mínimo” das linhas V3 e F3 é o arquivo guardado no
servidor assim que o respondente o escolhe; não há botão “Salvar rascunho”. Cada UG envia uma
única resposta, e o primeiro envio encerra o destinatário. No variável, a STC informa na criação
a lista de informações solicitadas. Ver a revisão na
[decisão de escopo](../decisoes-de-reunioes/2026-10-16-recorte-catalogo-v1-e-tesauro.md).

## Situação observada em 2026-10-19

O repositório canônico privado
[`Oxygeni-Projetos-Estagiarios/agiliza-stc`](https://github.com/Oxygeni-Projetos-Estagiarios/agiliza-stc)
mantém a V1 em `main` (`c6066b9`). Depois do PR #5 (`60f25d0`, 14/10), entraram o envio auditável
com comprovante em PDF (PR #10, 16/10) e a preparação para homologação (PR #11, `18c345b`, 19/10):
resposta por arquivos livres, lista de informações no variável, uma resposta por UG, XLSX
tolerante ao Excel e ao LibreOffice, telas em português, conta STC criada por comando e imagem de
produção sem as telas do protótipo.

A imagem de produção foi ensaiada atrás de proxy HTTPS, e a homologação ensaiada nos 11 cenários do
roteiro terminou com 82 verificações OK. Faltam o ambiente real, a carga do piloto em base
operacional e o UAT com a STC e a SINFRA. Comandos e resultados ficam em
`../../../agiliza-stc/specs/testing.md`. Fontes institucionais, levantamento, atas e demais
materiais de `documentos/` continuam fora do código.

| Recorte | Status técnico | Integração |
| --- | --- | --- |
| Fundação Laravel/PostgreSQL e container | Em andamento | Imagem de produção ensaiada atrás de HTTPS em `main` (`18c345b`); ambiente real pendente |
| Acesso, publicação, coleta, download e comprovante V1 | Concluído tecnicamente | `main` (`18c345b`, PR #11 mesclado em 19/10) |
| Homologação, UAT e retirada de demos | Em andamento | Homologação ensaiada; UAT, carga operacional e ambiente real pendentes |

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

Criação de novos objetos e sincronização futura Tesauro–Catálogo, SEI, prazo, prorrogação,
focal, ausência total, validação humana, correção, auditoria, Gabinete,
segurança de piloto e homologação continuam no catálogo do MVP completo, mas não são etapas ou
critérios desta V1.
