# Lista de funcionalidades técnicas

**Versão:** 7.0  
**Data:** 2026-09-10  
**Referência normativa:** versão 7.0 de
[`regras-de-negocio.md`](regras-de-negocio.md)

Este documento descreve o contrato-alvo da plataforma. Responsabilidades humanas e permissões
estão em [`perfis-e-permissoes.md`](perfis-e-permissoes.md).

## 1. Fronteira técnica

A plataforma organiza ciclos, coletas, contribuições, campos diretos, arquivos, prazos e histórico;
disponibiliza o modelo XLSX cadastrado quando for o item principal; controla capacidades; oferece
consulta do Gabinete; apoia decisões humanas; e registra auditoria.

A plataforma não substitui o SEI, edita o Tesauro externo, valida veracidade automaticamente,
unifica planilhas, correlaciona linha↔anexo nem decide questões institucionais abertas.

## 2. Modelo conceitual

```text
Objeto de transparência
├── Tesauro como carga inicial e proveniência
├── Catálogo operacional editável, auditável e versionado
│   └── Modelo XLSX oficial do objeto fixo
└── Ciclo
    ├── Snapshot global publicado
    ├── Estado explícito aberto/encerrado
    ├── Lista ordenada de números SEI + datas
    ├── Link único
    └── Coleta institucional por UG
        ├── Toggle focal imutável após publicação
        ├── Prazo derivado do último número SEI, ressalvada P-048
        ├── Até duas prorrogações de 5 dias úteis
        ├── Adjuntas e contribuições
        ├── Solicitações operacionais
        └── Histórico institucional
```

## 3. Entidades esperadas

### 3.1 Objeto

- ID, código, nome, tema e classificação manual/automatizada;
- tipo, campos, uploads, cadência, formato, fonte e UGs mapeadas;
- versões do modelo XLSX oficial quando o objeto for fixo;
- histórico auditável de alterações no catálogo importado.

### 3.2 Ciclo

- um objeto e tipo fixo ou variável;
- snapshot versionado do catálogo;
- lista ordenada de números SEI com data de registro;
- UGs e toggle focal de cada uma;
- link estável, estado, datas e histórico de publicação/reiteração;
- indicador derivado “com número SEI” × “sem número SEI”.

### 3.3 Coleta institucional

- ciclo, UG e toggle focal;
- ponto focal opcional e papel derivado do toggle;
- prazo normal, primeira e segunda prorrogações;
- contribuições, solicitações, estado e histórico autorizado.

### 3.4 Adjunta

- ID local, UG, nome, origem e estado ativo.

### 3.5 Atribuição

Relação única entre pessoa, adjunta e coleta. A mesma pessoa pode possuir várias atribuições.

### 3.6 Contribuição

- atribuição e requisitos efetivos;
- XLSX oficial e uploads no objeto fixo;
- campos diretos e/ou uploads no objeto variável;
- não ocorrências, estado e histórico de correções;
- conferência focal somente no modo ligado;
- validação STC e eventos.

### 3.7 Caixa de anexo

- requisito, rótulo, obrigatoriedade, arquivos vigentes e log de substituições.

### 3.8 Solicitação operacional

Tipos:

- prorrogação;
- indicação de outro responsável.

Cada solicitação registra autor, data, motivo, estado, responsável pela decisão e resultado. O
roteamento passa pelo focal somente quando o toggle da UG estiver ligado.

## 4. Capacidades por módulo

### 4.1 Catálogo

- consumir metadados de objetos manuais e automatizados;
- excluir os oito automatizados da criação manual enquanto P-047 estiver aberta;
- pesquisar, agrupar por tema e manter seleção canônica;
- editar objeto, campo, anexo, UG e associação objeto↔UG com valores anterior e novo;
- armazenar e versionar modelos XLSX oficiais dos objetos fixos;
- manter proveniência entre Tesauro externo, importação e edição local;
- tratar o Catálogo do Agiliza como fonte operacional depois da carga inicial;
- tratar o mapeamento como oficial no fixo e referencial no variável;
- fazer edições valerem somente para ciclos novos.

### 4.2 Criação do ciclo

- escolher tipo e objeto;
- no fixo, referenciar modelo oficial, carregar campos, uploads e UGs travados;
- no variável, escolher campos diretos, uploads e UGs, exigindo ao menos um item;
- definir toggle por UG, desligado por padrão;
- publicar sem exigir número SEI;
- gerar link e coletas de forma idempotente, sem gerar XLSX para objeto variável.

### 4.3 Publicação

- finalizar o rascunho sem fila de aprovação ou ajustes;
- publicar atomicamente snapshot, referência do modelo fixo quando aplicável, link e coletas;
- restringir registro de número SEI por permissão;
- indicar ciclos com número pendente;
- acrescentar reiteração sem trocar o link;
- impedir alteração do toggle após a publicação;
- exigir número SEI antes do encerramento manual;
- permitir excluir ciclo publicado, invalidando o link sem apagar respostas já enviadas.

### 4.4 Cadastro da UG

- manter ponto focal opcional, adjuntas e participantes;
- enviar convite por e-mail, autocadastrar convidado/adjunta, compartilhar link, manter múltiplas
  atribuições e remover participante;
- registrar log mínimo e apagar conteúdo conforme a regra vigente.

### 4.5 Acesso

- oferecer entrada do focal, identificação pelo link e convite;
- separar login institucional do acesso contextual e preservar o token do ciclo após autenticação;
- isolar por UG e revogar acesso;
- permitir observação focal sem poderes operacionais no modo desligado;
- oferecer ao Gabinete painel somente leitura sobre todos os ciclos, histórico e download de
  respostas, sem mutações;
- manter método definitivo de vínculo CPF–UG em aberto.

### 4.6 Resposta

- quando a planilha principal for obrigatória, fornecer e receber o modelo XLSX cadastrado, com
  anexos complementares opcionais;
- sem planilha principal obrigatória, fornecer campos aplicáveis e exigir ao menos um upload;
- pré-validar o XLSX fixo sem persistência pelo mesmo validador do envio final;
- não usar mínimo numérico configurável por caixa;
- detectar coluna inteira, campo direto ou upload ausente antes do envio;
- tratar célula isolada vazia como alerta e não como ausência do campo inteiro;
- exigir confirmação e justificativa das não ocorrências detectadas, sem fila de ciência;
- manter resposta parcial como `Respondida` e contabilizar não ocorrências separadamente;
- permitir ausência total pelo caminho do toggle e enviar direto à STC quando desligado.

### 4.7 Coordenação focal

- sempre permitir observação de desfechos, logs e histórico da UG;
- somente no modo ligado: distribuir, confirmar/devolver, tramitar solicitações permitidas,
  declarar ausência total e concluir a coleta;
- nunca remover requisito, gerar XLSX ajustado ou aprovar planilha candidata.

### 4.8 Operação STC

- manter filas por tipo de pendência;
- validar ou devolver contribuição isolada;
- decidir prorrogação e orientar o repasse do link quando a informação estiver em outro setor;
- validar contribuição resolvida por conteúdo válido, não ocorrências confirmadas ou ausência total;
- registrar número SEI e copiar link/texto quando houver `sei-link-texto`;
- dar ciência de não ocorrência e visualizar histórico completo;
- permitir exportação filtrada a todo Servidor STC;
- limitar mutações de Catálogo e UGs a `catalogo-e-ugs` e manter consulta aberta aos demais.
- permitir reversão motivada da validação enquanto o ciclo estiver aberto.

### 4.9 Prazo

- iniciar no registro do último número SEI do ciclo;
- calcular segunda a sexta, sem feriados no MVP;
- controlar no máximo duas prorrogações separadas de cinco dias úteis por UG;
- liberar a segunda somente no último dia útil da primeira extensão;
- restaurar as duas extensões após reiteração;
- manter envio tardio posterior sem automação enquanto P-035/P-036 estiverem abertas.

### 4.10 Histórico

- registrar eventos ordenados, autor, papel, data e contexto;
- guardar valores anterior/novo em edição de catálogo;
- registrar publicação, número SEI, reiteração, correção e validação;
- preservar histórico de arquivos, exclusão de ciclo e remoção conforme as regras vigentes;
- preservar o evento validado quando houver reversão motivada em ciclo aberto;
- separar mudanças estruturais do ciclo das ações da coleta e das respostas;
- exportar visão macro exatamente conforme os filtros ativos, sem arquivos, conteúdo, nomes de
  respondentes ou eventos individuais.

### 4.11 Catálogo e interoperabilidade

- cadastrar e versionar o modelo XLSX oficial de cada objeto;
- aplicar revisão aprovada somente a ciclos futuros;
- exportar o Catálogo no formato do Tesauro de origem;
- bloquear a exportação enquanto houver revisão pendente de aprovação.

## 5. Estados conceituais

### 5.1 Ciclo

- `rascunho`;
- `aberto`: link e coletas gerados; número SEI pode estar pendente e o prazo fica parado;
- `em andamento`: número SEI registrado e prazo correndo;
- `encerrado`: encerramento sempre manual e condicionado à existência de número SEI.

`atrasado` é derivado por UG. “Com número SEI” × “sem número SEI” é dimensão independente do estado.

### 5.2 Coleta institucional

- `aguardando nº SEI`: publicada, respondível, sem prazo correndo;
- `aberta`: prazo iniciado;
- `encaminhada à STC`: somente com toggle ligado após conclusão focal;
- `ausência total`: declarada pelo focal ou respondente conforme o toggle;
- `encerrada/validada`: decisão da STC;
- `atrasada`: derivada do prazo.

### 5.3 Contribuição

- `não iniciada` e `rascunho`;
- `aguardando focal`, `devolvida pelo focal` e `confirmada pelo focal`: somente com toggle ligado;
- `aguardando STC`: destino direto no modo desligado;
- `em correção`, `validada` e `removida`;
- não ocorrências parciais são itens associados à resposta e não substituem seu estado de envio.

`validada` pode ser revertida com motivo enquanto o ciclo estiver aberto; o registro validado
permanece no Histórico. Encerrado o ciclo, a resposta não reabre.

## 6. Regras técnicas obrigatórias

- Uma contribuição nunca altera outra.
- Publicação do ciclo é idempotente e não depende de aprovação por outro perfil.
- Edição do catálogo não altera ciclo em andamento.
- Mudança de Catálogo não altera snapshots publicados.
- O escopo e o modelo publicados não são modificados durante a coleta; ausências são registradas
  sem criar uma versão local do modelo.
- Mutações assíncronas não podem ser duplicadas.
- Troca de arquivo preserva log e remove o binário antigo da consulta.
- O link não permite acesso cruzado entre UGs.
- As capacidades `sei-link-texto` e `catalogo-e-ugs` pertencem ao perfil Servidor STC, não a uma
  pessoa. Exportação do Histórico não depende de capacidade.
- O frontend não inventa limite de arquivo, sigilo, atraso ou resposta às decisões P-044–P-055.

## 7. Integrações previstas, não contratadas

- autenticação e vínculo CPF–UG;
- provisionamento de e-mail, armazenamento, SEI e calendário oficial de feriados;
- importação futura do Tesauro e reconciliação com edições locais;
- observabilidade.

O formato real de API, banco e mensageria permanece fora desta revisão documental.

## 8. Dados-fonte

- O Tesauro recebido como `v2_6_agosto_2026` declara internamente v2.5 — julho/2026.
- MT-0050, MT-0054, MT-0055 e MT-0056 possuem metadados; P-033 foi encerrada.
- P-024 permanece aberta por divergência de versionamento.
- As contagens extraídas 49/276/484/31/8/41 não mudam até a reextração autorizada.
- O mapeamento é oficial para objetos fixos e preliminar para variáveis.
- Depois da carga inicial, o Catálogo do Agiliza é a fonte operacional; reconciliação futura segue
  pendente em P-044.

## 9. Critérios técnicos de qualidade

- domínio distingue ciclo, coleta, contribuição e solicitação;
- regras vivem fora de componentes de interface;
- transições possuem testes comportamentais quando implementadas;
- permissões são verificadas no caso de uso;
- extrato e operações manuais de SEI possuem capacidades separadas;
- listas, estados e histórico são acessíveis e derivados de eventos;
- fontes mantêm proveniência e decisões pendentes não viram constantes silenciosas.

## 10. Funcionalidades futuras

- correlação automática anexo↔linha, unificação de planilhas, OCR, IA e ranking;
- modelos próprios para obras, sigilo granular e calendário de feriados;
- cobranças automatizadas e integração bidirecional com SEI.
