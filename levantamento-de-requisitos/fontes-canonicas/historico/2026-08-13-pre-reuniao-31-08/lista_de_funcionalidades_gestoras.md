# Funcionalidades gestoras

**Versão:** 10.1  
**Data:** 2026-08-13  
**Natureza:** responsabilidades institucionais da STC e das UGs

Este documento descreve atividades humanas e institucionais, não componentes técnicos. O §33 e o §32 de
[`contextoSTC.md`](contextoSTC.md) prevalece sobre versões anteriores em conflito.

## 1. Papéis, ponto focal e destinação

### Responsabilidades da STC

- operar com um único perfil interno, **Servidor STC**;
- conceder separadamente a permissão de registrar números SEI;
- manter UGs, adjuntas e pontos focais;
- aplicar o mapeamento oficial aos objetos fixos e confirmar destinatários dos variáveis;
- orientar a ancoragem do focal em controle interno, ouvidoria ou unidade equivalente.

### Responsabilidades do ponto focal

Sempre:

- observar respostas, logs e histórico da própria UG;
- acompanhar prazo e desfechos sem ampliar seu escopo de acesso;
- responder por uma adjunta quando possuir atribuição.

Somente com o toggle da UG ligado:

- cadastrar adjuntas e respondentes, distribuir o pedido e conferir contribuições;
- devolver com justificativa, concluir a resposta institucional e praticar atos em nome da UG;
- tramitar pedidos de edição, prorrogação e indicação de outro responsável.

Com o toggle desligado, o focal é observador e não bloqueia o fluxo. Se não houver focal, a operação
ocorre diretamente entre respondente e STC.

## 2. Formalização, comunicação e cobrança

### Responsabilidades da STC

- finalizar a criação e publicar o ciclo automaticamente;
- gerar o link que será inserido manualmente no SEI;
- registrar uma lista ordenada de números SEI, cada um com data;
- acompanhar UGs em atraso e realizar cobranças administrativas;
- manter a plataforma como canal paralelo, sem substituir o SEI.

### Responsabilidades da UG

- acessar o ciclo pelo link e responder pelos dados e declarações apresentados;
- compartilhar o link somente com responsáveis internos;
- solicitar prorrogação com justificativa quando necessário.

Cobrança sem novo número SEI não muda o prazo. Reiteração formal acrescenta número ao mesmo ciclo,
preserva o link e reinicia prazo e prorrogações.

## 3. Definição do que se coleta

### Responsabilidades da STC

- manter o Tesauro como fonte externa e o catálogo importado como fonte operacional editável;
- auditar edição de objeto, campo, anexo, UG e associação objeto↔UG;
- definir metadados, caixas obrigatórias, cadência e prazo;
- criar objetos variáveis quando houver demanda pontual;
- selecionar o objeto-piloto.

No objeto fixo, campos, anexos e UGs vêm travados do Tesauro e do mapeamento oficial; o toggle focal
por UG é a única configuração do ciclo. No variável, a STC escolhe esses três conjuntos. Ambos geram
XLSX. Edição do catálogo só alcança ciclos novos e não altera snapshots publicados.

## 4. Mapeamento de fontes e UGs

### Responsabilidades da STC

- manter e corrigir a matriz objeto↔UG;
- tratar a matriz como oficial para objetos fixos;
- usar a matriz apenas como referência para objetos variáveis;
- identificar quais fontes representam uma UG real e preencher lacunas “Por UG”.

O mapeamento não altera a classificação manual/automatizada do Tesauro. A governança de divergências
entre catálogo editado, Tesauro e importações futuras permanece em P-044.

## 5. Distribuição e articulação interna da UG

### Responsabilidades do ponto focal com toggle ligado

- escolher ou cadastrar adjunta, cadastrar respondentes e permitir múltiplas adjuntas por pessoa;
- acompanhar identificação pelo link e remover participantes quando necessário;
- garantir desfecho, devolver contribuições e coordenar áreas que compartilham informações.

### Responsabilidades do respondente

- responder apenas no âmbito da adjunta atribuída;
- devolver XLSX estruturalmente correto e preencher as caixas obrigatórias;
- solicitar edição, prorrogação ou redirecionamento pelo caminho definido pelo toggle;
- corrigir itens devolvidos e declarar não ocorrência com justificativa.

Planilhas e arquivos de adjuntas diferentes permanecem separados.

## 6. Verificação, validação e controle

### Responsabilidades do ponto focal com toggle ligado

- conferir, confirmar ou devolver cada contribuição com motivo;
- avalizar solicitações, confirmar a própria contribuição e concluir o conjunto institucional.

### Responsabilidades da STC

- checar formato e completude estrutural e validar a veracidade de forma humana;
- devolver apenas a contribuição ou arquivo com problema e preservar respostas válidas;
- validar somente pacote completo e sem solicitação de edição aberta;
- registrar o Servidor STC que decidiu;
- dar ciência de não ocorrência sem rejeitá-la.

Uma decisão de qualquer Servidor STC basta. IA e OCR permanecem futuras.

## 7. Não ocorrência e alteração do pedido

### Não ocorrência institucional

- exige motivo e justificativa e não pode esconder envio parcial;
- com toggle ligado, é formalizada pelo focal;
- desligado, é declarada pelo respondente diretamente à STC;
- a STC dá ciência e encerra manualmente, sem ação de rejeição.

### Não ocorrência específica e resposta validada

Dispensa de campo ou anexo segue ao focal somente no modo ligado; no modo desligado, segue direto à
STC. Qualquer Servidor STC decide e registra a não ocorrência daquela informação antes da validação.
Resposta validada fica fechada; enquanto P-049 estiver aberta, nova demanda exige outro ciclo.

## 8. Prazos, prorrogação e ausência de envio

### Responsabilidades da STC

- iniciar o prazo de cinco dias úteis no registro do número SEI;
- decidir até duas prorrogações separadas de cinco dias úteis por UG;
- restaurar as duas extensões quando houver reiteração com novo número SEI;
- distinguir envio regular, prorrogado, atrasado e não enviado.

### Responsabilidades da UG

- acompanhar o prazo e solicitar cada extensão com justificativa;
- usar o focal como intermediário somente com toggle ligado.

A segunda extensão só pode ser solicitada no último dia útil da primeira. O envio tardio após as
duas extensões permanece pendente em P-035/P-036.

## 9. Indicação de outro responsável

### Responsabilidades da UG

- com toggle ligado, o focal indica a possível UG ou adjunta;
- desligado, o respondente envia a indicação justificada diretamente à STC;
- a UG não transfere a coleta por conta própria.

### Responsabilidades da STC

- analisar a indicação, selecionar UG cadastrada e preservar o histórico;
- encaminhar segundo o toggle da nova UG e não iniciar prazo automaticamente quando ela entrar
  depois do primeiro número SEI, enquanto P-048 permanecer aberta; reiteração posterior continua
  regida pela lista SEI do ciclo.

Redirecionamento depois de contribuições, mapeamento fixo incorreto e prazo da UG tardia permanecem
em P-034/P-045/P-048.

## 10. Acesso, identificação e sigilo

### Responsabilidades da STC

- decidir o método definitivo de login e verificação;
- definir sigilo, acesso, retenção e circulação de informações;
- manter um perfil Servidor STC e permissões específicas, inclusive a de SEI.

### Responsabilidades da UG

- informar identidade e adjunta corretamente, remover acessos indevidos e respeitar o link;
- responder pelos dados fornecidos.

A direção de autenticação é CPF; vínculo CPF–UG e política de sigilo continuam abertos.

## 11. Ranking e reconhecimento

Ranking, fórmula, publicidade e reconhecimento permanecem fora do MVP.

## 12. Adesão, capacitação e cultura

### Responsabilidades da STC

- realizar onboarding, apresentar o programa e capacitar as UGs;
- explicar objeto, planilha, anexos e responsabilidades;
- produzir apoio e fomentar cultura de transparência.

## 13. Obras, contratos e aditivos

### Responsabilidades atuais

- a UG reúne documentos; a STC confere vínculos e duplicidades;
- adjuntas articulam informações compartilhadas sem unificar arquivos na plataforma.

Modelo próprio e vínculo entre contratos, aditivos, medições e anexos continuam em P-014.

## 14. Fronteira com as funcionalidades técnicas

| Dimensão | Plataforma | Gestão |
|---|---|---|
| Ponto focal | Aplica toggle e permissões | STC/UG designam; focal coordena só no modo ligado |
| Destinação | Trava UGs do fixo; sugere no variável | Servidor STC mantém a matriz |
| SEI | Guarda lista, datas e indicador | Pessoa autorizada registra manualmente |
| Tesauro | Consome fonte externa e mantém catálogo importado | STC governa conteúdo e reconciliação futura |
| Planilha | Gera, recebe e checa estrutura | UG preenche; STC confere |
| Anexos | Organiza caixas e arquivos | STC define exigências |
| Veracidade | Registra decisão | Qualquer Servidor STC valida |
| Prorrogação | Controla duas extensões de 5 dias | Servidor STC decide |
| Não ocorrência | Roteia conforme toggle e registra | Respondente ou focal declara; STC encerra |
| Capacitação | Pode oferecer conteúdo | STC conduz |
| Ranking | Poderá calcular | STC define fórmula e publicidade |

## 15. Pendências gestoras

As decisões ainda abertas estão em [`pontos_em_aberto.md`](pontos_em_aberto.md). Este documento não
atribui regra definitiva a essas questões.
