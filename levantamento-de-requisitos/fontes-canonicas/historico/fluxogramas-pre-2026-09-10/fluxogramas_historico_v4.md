# Fluxogramas do Agiliza Transparência

**Versão:** 4.0  
**Data:** 2026-07-30  
**Fonte normativa:** [`contextoSTC.md`](contextoSTC.md)

Os diagramas representam decisões vigentes. Nós tracejados indicam pendências ou processos
provisórios que não devem ser tratados como regra definitiva.

## 1. Criação, aprovação e comunicação do ciclo

```mermaid
flowchart TD
    A["Analista inicia um ciclo"] --> B["Escolhe um único objeto"]
    B --> C{"Objeto fixo ou variável?"}
    C -->|Fixo| D["Carrega campos e anexos-base bloqueados"]
    C -->|Variável| E["Analista seleciona campos e caixas de anexos"]
    D --> F["Consulta referências do mapeamento"]
    E --> F
    F --> G["Analista seleciona explicitamente as UGs"]
    G --> H["Informa processo SEI, comunicação e prazo"]
    H --> I["Envia configuração ao Especialista"]
    I --> J{"Especialista aprova?"}
    J -->|Não| K["Solicita ajustes ao Analista"]
    K --> H
    J -->|Sim| L["Sistema gera XLSX, link e uma coleta por UG"]
    L --> M["STC expede comunicação formal pelo SEI"]
    M --> N["Começa o prazo individual de cinco dias úteis"]
```

## 2. Distribuição da coleta pelo ponto focal

```mermaid
flowchart TD
    A["Ponto focal acessa a coleta institucional"] --> B["Visualiza objeto, prazo e requisitos"]
    B --> C{"Como incluir o responsável?"}
    C -->|Pré-cadastro| D["Informa nome, adjunta e e-mail"]
    D --> E["Sistema cria a contribuição e envia o link"]
    C -->|Link compartilhado| F["Pessoa se identifica e passa pela verificação configurada"]
    F --> G["Sistema cria a contribuição imediatamente"]
    E --> H["Contribuição vinculada à adjunta"]
    G --> H
    H --> I{"A pessoa representa outra adjunta?"}
    I -->|Sim| J["Focal cria outra atribuição separada"]
    I -->|Não| K["Distribuição concluída para essa pessoa"]
    J --> K
```

## 3. Cadastro de adjunta e remoção de respondente

```mermaid
flowchart TD
    A["Focal informa a adjunta"] --> B{"Adjunta já cadastrada?"}
    B -->|Sim| C["Seleciona a adjunta"]
    B -->|Não| D["Digita o nome da nova adjunta"]
    D --> E["Nova adjunta entra no cadastro da UG"]
    C --> F["Vincula respondente"]
    E --> F
    F --> G{"Focal decide remover a pessoa?"}
    G -->|Não| H["Atribuição permanece ativa"]
    G -->|Sim| I["Revoga acesso"]
    I --> J["Exclui cadastro ativo, conteúdo e arquivos"]
    J --> K["Mantém log mínimo com participante, autor e data"]
```

## 4. Contribuição por adjunta

```mermaid
flowchart TD
    A["Respondente abre sua contribuição"] --> B["Baixa o XLSX gerado"]
    B --> C["Preenche os registros da adjunta"]
    C --> D["Envia o XLSX"]
    D --> E["Visualiza uma caixa por anexo obrigatório"]
    E --> F["Envia pelo menos um arquivo em cada caixa"]
    F --> G{"Deseja adicionar mais arquivos à caixa?"}
    G -->|Sim| H["Usa Adicionar mais arquivos"]
    H --> I{"Todas as caixas obrigatórias estão preenchidas?"}
    G -->|Não| I
    I -->|Não| E
    I -->|Sim| J{"Existe campo ou anexo que a adjunta não consegue fornecer?"}
    J -->|Sim| K["Inicia solicitação de edição"]
    J -->|Não| L["Envia a contribuição ao ponto focal"]
```

## 5. Conferência e conclusão institucional

```mermaid
flowchart TD
    A["Contribuição aguarda o ponto focal"] --> B{"Focal confirma?"}
    B -->|Não| C["Devolve ao respondente com justificativa"]
    C --> D["Respondente corrige somente os itens apontados"]
    D --> A
    B -->|Sim| E["Contribuição recebe desfecho confirmado"]
    E --> F{"Todos os participantes têm desfecho?"}
    F -->|Não| G["Focal acompanha contribuições pendentes"]
    G --> A
    F -->|Sim| H["Focal conclui a resposta institucional"]
    H --> I["Contribuições separadas seguem para a STC"]
```

Desfechos aceitos: contribuição confirmada, não ocorrência da adjunta ou remoção formal.

## 6. Validação e correção pela STC

```mermaid
flowchart TD
    A["STC recebe as contribuições separadas"] --> B["Analista ou Especialista abre uma contribuição"]
    B --> C{"Contribuição válida?"}
    C -->|Sim| D["Registra validação e responsável"]
    D --> E{"Todas as contribuições aplicáveis estão concluídas?"}
    E -->|Sim| F["Coleta institucional pode ser encerrada"]
    E -->|Não| G["Mantém as demais contribuições em seus estados"]
    C -->|Não| H["Devolve somente a contribuição ou arquivo afetado"]
    H --> I["Respondente corrige o item"]
    I --> J["Ponto focal confirma novamente"]
    J --> B
```

## 7. Não ocorrência

### 7.1 UG inteira

```mermaid
flowchart TD
    A["Ponto focal informa não ocorrência da UG"] --> B{"Já existe resposta parcial enviada?"}
    B -->|Sim| C["Declaração institucional é bloqueada"]
    C --> D["UG deve tratar contribuições ou exceções específicas"]
    B -->|Não| E["Focal escolhe motivo e escreve justificativa"]
    E --> F["Sistema registra responsabilidade da UG"]
    F --> G["Coleta institucional é encerrada"]
    G --> H["STC visualiza a declaração sem ação de rejeição"]
```

### 7.2 Adjunta

```mermaid
flowchart TD
    A["Respondente declara não ocorrência da adjunta"] --> B["Informa motivo e justificativa"]
    B --> C["Ponto focal confere"]
    C --> D{"Focal confirma?"}
    D -->|Não| E["Devolve para correção"]
    D -->|Sim| F["Contribuição recebe desfecho de não ocorrência"]
    F --> G["Coleta institucional continua com as outras adjuntas"]
```

## 8. Solicitação de edição de campo ou anexo

```mermaid
flowchart TD
    A["Respondente seleciona campo ou caixa de anexo"] --> B["Justifica a impossibilidade"]
    B --> C["Envia ao ponto focal"]
    C --> D{"Focal avaliza?"}
    D -->|Não| E["Pedido volta ao respondente"]
    D -->|Sim| F["Pedido segue ao Analista"]
    F --> G{"Analista aceita?"}
    G -->|Não| H["Mantém requisitos e registra a recusa"]
    G -->|Sim| I["Cria nova versão dos requisitos da contribuição"]
    I --> J["Especialista revisa a mudança de escopo"]
    J --> K{"Especialista aprova?"}
    K -->|Não| L["Solicita ajuste ao Analista"]
    L --> I
    K -->|Sim| M["Remove o item somente daquela adjunta"]
    M --> N["Registra não ocorrência da informação"]
    N --> O["Contribuição volta ao preenchimento no mesmo ciclo e SEI"]
```

## 9. Prorrogação individual da UG

```mermaid
flowchart TD
    A["Ponto focal solicita prorrogação"] --> B["Informa data pretendida e motivo"]
    B --> C["Analista analisa"]
    C --> D{"Aprova?"}
    D -->|Não| E["Mantém o prazo original e registra motivo"]
    D -->|Sim| F["Define novo prazo somente para aquela UG"]
    F --> G{"Prazo superior a cinco dias úteis adicionais?"}
    G -->|Não| H["Aplica extensão padrão"]
    G -->|Sim| I["Registra autorização excepcional do Analista"]
    H --> J["Envio no novo prazo recebe rótulo Envio prorrogado"]
    I --> J
```

## 10. Indicação e troca da UG responsável

```mermaid
flowchart TD
    A["Ponto focal informa possível UG ou adjunta responsável"] --> B["Registra o nome em texto"]
    B --> C{"Já existe contribuição enviada?"}
    C -->|Sim| P["Comportamento pendente de decisão"]
    C -->|Não| D["Coleta sai das pendências da UG"]
    D --> E["Analista identifica uma UG cadastrada"]
    E --> F{"Destino confirmado?"}
    F -->|Não| G["STC registra que não localizou o destino"]
    F -->|Sim| H["STC atribui ao ponto focal da nova UG"]
    H --> I["STC realiza nova comunicação"]
    I --> J["Nova UG recebe cinco dias úteis"]
    J --> K["Novo focal distribui entre suas adjuntas"]

    classDef pending fill:#fff3cd,stroke:#8a6d00,color:#4d3f00,stroke-dasharray:5 5;
    class P pending;
```

Para a UG anterior, a coleta deixa de aparecer. O histórico da troca permanece exclusivo da STC.

## 11. Vencimento, prorrogação e “não enviado”

```mermaid
flowchart TD
    A["Prazo normal termina"] --> B{"UG possui prorrogação aprovada?"}
    B -->|Não| C["Envio fica bloqueado até decisão do Analista"]
    B -->|Sim| D["UG trabalha no prazo prorrogado"]
    D --> E{"Contribuição enviada durante a extensão?"}
    E -->|Sim| F["Registra Envio prorrogado"]
    E -->|Não| G["Fim da prorrogação"]
    G --> H["Contribuições respondidas seguem à STC"]
    G --> I["Pendentes recebem Não enviado"]
    I --> P["Janela de envio atrasado pendente de decisão"]

    classDef pending fill:#fff3cd,stroke:#8a6d00,color:#4d3f00,stroke-dasharray:5 5;
    class P pending;
```

## 12. Cobranças e contatos não respondidos

```mermaid
flowchart TD
    A["STC identifica ausência de resposta"] --> B["STC realiza contato ou cobrança"]
    B --> P1["Tipo de log ainda pendente"]
    B --> P2["Relação com o SEI ainda pendente"]
    B --> P3["Efeito sobre o prazo ainda pendente"]

    classDef pending fill:#fff3cd,stroke:#8a6d00,color:#4d3f00,stroke-dasharray:5 5;
    class P1,P2,P3 pending;
```

O diagrama registra apenas a necessidade operacional. Não define reiteração automática,
reabertura ou novo prazo.

## 13. Visão ponta a ponta

```mermaid
flowchart LR
    A["Analista cria"] --> B["Especialista aprova"]
    B --> C["SEI comunica"]
    C --> D["Focal distribui"]
    D --> E["Adjuntas respondem"]
    E --> F["Focal confere"]
    F --> G["Focal conclui"]
    G --> H["STC valida contribuições"]
    H --> I["Correções isoladas, se necessárias"]
    I --> H
    H --> J["Coleta institucional encerra"]
```
