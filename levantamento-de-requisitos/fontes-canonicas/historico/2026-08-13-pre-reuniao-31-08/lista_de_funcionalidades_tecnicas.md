# Lista de funcionalidades técnicas

**Versão:** 5.1  
**Data:** 2026-08-13  
**Referência normativa:** [`contextoSTC.md`](contextoSTC.md), §33 e §32

Este documento descreve o contrato-alvo da plataforma. Responsabilidades humanas estão em
[`lista_de_funcionalidades_gestoras.md`](lista_de_funcionalidades_gestoras.md).

## 1. Fronteira técnica

A plataforma organiza ciclos, coletas, contribuições, arquivos, prazos e histórico; gera e recebe
XLSX; controla permissões; apoia decisões humanas; e registra auditoria.

A plataforma não substitui o SEI, edita o Tesauro externo, valida veracidade automaticamente,
unifica planilhas, correlaciona linha↔anexo nem decide questões institucionais abertas.

## 2. Modelo conceitual

```text
Objeto de transparência
├── Catálogo importado editável e auditável
└── Ciclo
    ├── Snapshot global publicado
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
- campos, anexos, cadência, formato, fonte e UGs mapeadas;
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

- atribuição, XLSX, caixas de anexos e requisitos efetivos;
- não ocorrências, estado e histórico de correções;
- conferência focal somente no modo ligado;
- validação STC e eventos.

### 3.7 Caixa de anexo

- requisito, rótulo, obrigatoriedade, arquivos vigentes e log de substituições.

### 3.8 Solicitação operacional

Tipos:

- edição de campo/anexo;
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
- manter proveniência entre Tesauro externo, importação e edição local;
- tratar o mapeamento como oficial no fixo e referencial no variável;
- fazer edições valerem somente para ciclos novos.

### 4.2 Criação do ciclo

- escolher tipo e objeto;
- no fixo, carregar campos, anexos e UGs travados;
- no variável, escolher livremente campos, anexos e UGs;
- definir toggle por UG, desligado por padrão;
- publicar sem exigir número SEI;
- gerar link, XLSX e coletas de forma idempotente.

### 4.3 Publicação

- finalizar o rascunho sem fila de aprovação ou ajustes;
- publicar atomicamente snapshot, link, XLSX e coletas;
- restringir registro de número SEI por permissão;
- indicar ciclos com número pendente;
- acrescentar reiteração sem trocar o link;
- impedir alteração do toggle após a publicação.

### 4.4 Cadastro da UG

- manter ponto focal opcional, adjuntas e participantes;
- compartilhar link, manter múltiplas atribuições e remover participante;
- registrar log mínimo e apagar conteúdo conforme a regra vigente.

### 4.5 Acesso

- oferecer entrada do focal, identificação pelo link e convite;
- isolar por UG e revogar acesso;
- permitir observação focal sem poderes operacionais no modo desligado;
- manter método definitivo de vínculo CPF–UG em aberto.

### 4.6 Resposta

- fornecer XLSX, caixas obrigatórias, rascunho, envio e correção específica;
- pré-validar o XLSX sem persistência pelo mesmo validador do envio final;
- exigir a quantidade mínima configurada em cada caixa obrigatória;
- permitir não ocorrência e solicitações pelo caminho do toggle;
- enviar contribuição direto à STC quando desligado.

### 4.7 Coordenação focal

- sempre permitir observação de desfechos, logs e histórico da UG;
- somente no modo ligado: distribuir, confirmar/devolver, avalizar solicitações, declarar não
  ocorrência institucional e concluir a coleta.

### 4.8 Operação STC

- manter filas por tipo de pendência;
- validar ou devolver contribuição isolada;
- decidir edição, prorrogação e redirecionamento;
- validar somente contribuição completa e sem pedido de edição aberto;
- registrar número SEI quando houver permissão;
- dar ciência de não ocorrência e visualizar histórico completo.

### 4.9 Prazo

- iniciar no registro do último número SEI do ciclo;
- calcular segunda a sexta, sem feriados no MVP;
- controlar no máximo duas prorrogações separadas de cinco dias úteis por UG;
- liberar a segunda somente no último dia útil da primeira extensão;
- restaurar as duas extensões após reiteração;
- não iniciar prazo automaticamente no ato da inclusão de UG depois do primeiro número SEI enquanto
  P-048 permanecer aberta;
- manter envio tardio posterior sem automação enquanto P-035/P-036 estiverem abertas.

### 4.10 Histórico

- registrar eventos ordenados, autor, papel, data e contexto;
- guardar valores anterior/novo em edição de catálogo;
- registrar publicação, número SEI, reiteração, correção e validação;
- preservar histórico de arquivos, redirecionamento e remoção conforme as regras vigentes.

## 5. Estados conceituais

### 5.1 Ciclo

- `rascunho`;
- `publicado`: link e coletas gerados, número SEI ainda opcional e prazo parado;
- `em andamento`: número SEI registrado e prazo correndo;
- `finalizado`: encerramento sempre manual.

`atrasado` é derivado por UG. “Com número SEI” × “sem número SEI” é dimensão independente do estado.

### 5.2 Coleta institucional

- `aguardando nº SEI`: publicada, respondível, sem prazo correndo;
- `aberta`: prazo iniciado;
- `encaminhada à STC`: somente com toggle ligado após conclusão focal;
- `não ocorrência institucional`: declarada pelo focal ou respondente conforme o toggle;
- `encerrada/validada`: decisão da STC;
- `atrasada`: derivada do prazo.

### 5.3 Contribuição

- `não iniciada` e `rascunho`;
- `aguardando focal`, `devolvida pelo focal` e `confirmada pelo focal`: somente com toggle ligado;
- `aguardando STC`: destino direto no modo desligado;
- `em correção`, `validada`, `não ocorrência da adjunta` e `removida`.

`validada` é estado final da resposta. Nova demanda exige outro ciclo enquanto P-049 estiver aberta.

## 6. Regras técnicas obrigatórias

- Uma contribuição nunca altera outra.
- Publicação do ciclo é idempotente e não depende de aprovação por outro perfil.
- Edição do catálogo não altera ciclo em andamento.
- Mudança de escopo não invalida nem reabre resposta já validada.
- Exceção é auditável e limitada à informação/adjunta solicitante.
- Mutações assíncronas não podem ser duplicadas.
- Troca de arquivo preserva log e remove o binário antigo da consulta.
- O link não permite acesso cruzado entre UGs.
- O frontend não inventa limite de arquivo, sigilo, atraso ou resposta às decisões P-044–P-049.

## 7. Integrações previstas, não contratadas

- autenticação e vínculo CPF–UG;
- e-mail, armazenamento, SEI e calendário oficial de feriados;
- importação futura do Tesauro e reconciliação com edições locais;
- observabilidade.

O formato real de API, banco e mensageria permanece fora desta revisão documental.

## 8. Dados-fonte

- O Tesauro recebido como `v2_6_agosto_2026` declara internamente v2.5 — julho/2026.
- MT-0050, MT-0054, MT-0055 e MT-0056 possuem metadados; P-033 foi encerrada.
- P-024 permanece aberta por divergência de versionamento.
- As contagens extraídas 49/276/484/31/8/41 não mudam até a reextração autorizada.
- O mapeamento é oficial para objetos fixos e preliminar para variáveis.

## 9. Critérios técnicos de qualidade

- domínio distingue ciclo, coleta, contribuição e solicitação;
- regras vivem fora de componentes de interface;
- transições possuem testes comportamentais quando implementadas;
- permissões são verificadas no caso de uso;
- listas, estados e histórico são acessíveis e derivados de eventos;
- fontes mantêm proveniência e decisões pendentes não viram constantes silenciosas.

## 10. Funcionalidades futuras

- correlação automática anexo↔linha, unificação de planilhas, OCR, IA e ranking;
- modelos próprios para obras, sigilo granular e calendário de feriados;
- cobranças automatizadas e integração bidirecional com SEI.
