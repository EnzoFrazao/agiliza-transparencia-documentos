# STC Agiliza — Compêndio das Entrevistas de Levantamento

> **Documento de trabalho · junho/2026.** Objetivo: reunir **tudo o que foi abordado nas reuniões** para (1) entender **todos os problemas possíveis** e (2) **validar as soluções** propostas. Tem duas naturezas, claramente separadas:
>
> - **Bloco A — Registro das reuniões (fatos):** o que foi efetivamente dito nas quatro entrevistas internas da STC — **Thiago**, **Matheus**, **Fernando** e **Talita** — cada uma com seção própria; mais o **apêndice do PNTP**, a **síntese cruzada** e o **alerta estratégico SIMONI × Tesauro**.
> - **Bloco B — Diagnóstico e recomendações (a validar):** análise de causa raiz, riscos, lacunas, arquitetura em camadas, MVP e roadmap. É **proposta**, não decisão — derivada das reuniões mas ainda **não validada com a STC**. As divergências com os fatos do projeto estão sinalizadas.
>
> Entrevistas ainda pendentes: **órgãos externos** (quem responde na ponta), **Fernando (Secretaria Adjunta da Fazenda)** e **Camila (Secretaria Adjunta da Educação)**. As decisões em aberto só serão fechadas na **reunião de consolidação com toda a STC**, depois dessas conversas.

---

## Como ler este documento

Dentro de cada entrevista, os pontos vêm agrupados por tema. Na síntese final, cada achado é marcado como:

- **[confirmado]** — valida algo que já tínhamos;
- **[novo]** — apareceu agora;
- **[muda]** — altera o que estava registrado;
- **[em aberto]** — decisão pendente para a reunião de consolidação.

As grafias seguem as transcrições de áudio e devem ser conferidas antes de uso formal. Grafias já confirmadas: **Thiago**, **Matheus/Mateus**, **SIMONI**, **Bitrix**, **Sinfra**, **Cegov/Segov**, **SEGEP**, **SiconV**, **Tema 3**, **IN** (Instrução Normativa), **PNTP**, **Atricon**, **Talita de Oliveira Fontinelle**, **Leandro**, **Andrey/André**, **Stéferson**. A confirmar: **BB Pago**.

---

# 1. Entrevista — Thiago (operacionaliza o processo / SEI)

> Thiago foi entrevistado junto com Matheus. Esta seção concentra o que é atribuível a ele (fluxo real, SEI, numeração, identificação do respondente). Pontos conjuntos aparecem marcados como *(Thiago + Matheus)*.

## 1.1. Papel
Thiago operacionaliza o processo de coleta e é a referência sobre como o SEI é usado na prática. É o chefe imediato da Talita (aparece como observador nas tarefas dela no Bitrix).

## 1.2. O fluxo real de hoje (as-is), passo a passo
O caso usado como exemplo foi o de **terceirizados**:

1. A STC monta uma **minuta de ofício no SEI** contendo um **link para um formulário** (hoje um Google Forms) e, dentro do formulário, um **modelo de planilha padrão** para download.
2. A minuta sobe ao **gabinete do secretário**, que dispara um **ofício circular** às unidades gestoras (UGs) alvo.
3. As UGs **baixam o modelo, preenchem e fazem upload** de volta no formulário — **ou** respondem por outros meios (e-mail, WhatsApp, planilha própria, despacho no próprio SEI), fora do padrão.
4. A equipe **consolida manualmente** muitas respostas numa base única e **"traduz"** o que veio fora do padrão; quando não dá para traduzir, a informação se perde.
5. Para saber **quem respondeu, quem disse "não tenho" e quem não respondeu**, é preciso **cruzar manualmente** o formulário com os despachos do SEI.

Ponto-chave: hoje o canal é especificamente **Google Forms + planilha-padrão**, e o **ofício circular passa pelo gabinete do secretário** — o que tira da equipe de transparência o controle sobre o disparo.

## 1.3. Como o SEI funciona internamente (e por que atrapalha)
- O processo no SEI cresce por **"despacho sobre despacho"**: cada resposta/movimentação vira um novo despacho, e o processo incha até ficar difícil localizar a informação relevante.
- O jeito "certo" de organizar seria **processo-mãe com processos-filhos relacionados** — mas isso **não é praticado**.
- **Desencontro SEI ↔ ciclo:** quem recebe o SEI dentro do órgão **nem sempre é quem tem o dado**, o que quebra o fluxo (é exatamente o problema que as duas portas de entrada tentam resolver).
- O **SEI é vigente desde dez/2024** — é recente, o que ajuda a explicar por que muita coisa ainda é manual.

## 1.4. Numeração SEI
- O ciclo **pode ser criado e enviado sem número**; a numeração é **inserida/editada depois**.
- O **link do ciclo costuma viajar dentro do SEI** (é ali que o respondente recebe o acesso, substituindo o link do formulário).

## 1.5. O problema da apuração por conta contábil *(caso concreto do Thiago)*
Em um ciclo de **transferências voluntárias**, Thiago filtrou corretamente as UGs certas (as que pagam via conta de **"adiantamento"**), montou a lista certa e a enviou pronta. Mesmo assim, **o gabinete ignorou a lista e disparou para todas as UGs**. É o exemplo concreto de que **"o mapeamento existe, mas não é respeitado no disparo"** — mapear não basta; o disparo precisa obedecer ao mapeamento.

## 1.6. A tensão central: identificação do respondente *(Thiago, ponto forte)*
Thiago tem uma **restrição forte** contra deixar o respondente se auto-identificar selecionando a UG numa **lista suspensa**: na prática a pessoa **erra a seleção** e vincula a resposta ao **órgão errado** (o caso real citado: respondeu como "IMA" sendo "IMA Sul"; ou marcou Cegov sendo Sinfra). Isso gera justamente o trabalho investigativo de rastrear de quem é a resposta — que o projeto quer eliminar.

A solução que ganhou tração na conversa (e que reaparece reforçada na entrevista da Talita):
- O **ponto focal é cadastrado pela STC** (um ou mais por órgão).
- O **ponto focal cadastra quem vai responder** → o respondente já entra **pré-vinculado à UG certa**, sem selecionar nada numa lista.
- Onde houver auto-identificação, que seja por **lógica de texto** (a pessoa escreve "sinfra" e o sistema resolve), não por dropdown.

## 1.7. Dois requisitos que nasceram da fala do Thiago
- **Registrar a resposta negativa** ("não temos terceirizados") como estado próprio — hoje não se distingue "não respondeu" de "respondeu que não tem", e isso obriga ao cruzamento manual SEI × Forms.
- **Metadados obrigatórios travam o envio** — não se pode submeter terceirizado sem lotação e função preenchidas (campos que hoje chegam em branco).

## 1.8. O recebimento "padrão" *(Thiago + Matheus)*
O recebimento padrão idealizado é uma **planilha Excel**, mas **na prática os dados nem sempre chegam em planilha** (vêm PDF, imagem, texto). Daí a tensão entre restringir formato e transformar formato.

---

# 2. Entrevista — Matheus (termômetro operacional / coleta)

> Matheus dá a visão de quem sente o retrabalho no dia a dia. Importante: **Matheus está sendo deslocado para a área de TI**, o que deixa a operação de coleta concentrada na Talita (com o Andrey/André).

## 2.1. Papel
"Termômetro operacional" da coleta: acompanha gargalos, retrabalho e o uso cotidiano do SIMONI; participava da consolidação manual das respostas.

## 2.2. A raiz do problema: ausência de sistemas centralizados
- Tirando **orçamentário/financeiro** e **folha de pagamento**, a gestão da informação no Estado é **pulverizada e manual**.
- **Faltam sistemas centralizados** (por exemplo, de RH e de obras) — essa ausência é a **raiz da carga manual** de coleta.
- Exemplo do próprio projeto: a administração central, via **SEGEP**, **não tem registro de que os bolsistas FAPEMA atuam na STC** — um caso concreto da falta de gestão centralizada de informação no Estado.

## 2.3. Referência do "ideal": SiconV
Matheus citou o **SiconV** (sistema federal de convênios) como exemplo do que seria um fluxo bem estruturado de coleta/prestação — um norte do que o Estado não tem internamente.

## 2.4. O Bitrix
- O **Bitrix** é o **gestor de tarefas** da equipe (produto de mercado, tipo Bitrix24): visão **Kanban**, **bate-papo por tarefa**, observadores, histórico/linha do tempo, listas de verificação, Gantt.
- É a ferramenta onde a tarefa de atualização é aberta e acompanhada; ela é **sincronizada com o SIMONI** (detalhado na seção da Talita).

## 2.5. O caso Sinfra como modelo de sucesso *(princípio de design forte)*
A coleta de **obras** com a Sinfra é o caso de sucesso citado:
- Levou **cerca de um ano de negociação** e **"apadrinhamento de cima"** (alinhamento chefe a chefe) para destravar.
- Só funcionou quando, em vez de criar um processo novo, a STC **recortou o processo que a Sinfra já fazia** — aproveitou um **planilhão que já existia** e apenas filtrou as colunas necessárias.
- Princípio que decorre disso: **não criar processo novo; recortar o processo existente.** A adesão é muito maior quando a coleta se encaixa no que o órgão já produz.

## 2.6. Diagnóstico operacional
O gargalo não está na ferramenta de planejamento (que funciona), e sim no **retrabalho da segunda metade** do processo: receber, traduzir e consolidar respostas fora do padrão. (Esse diagnóstico é o mesmo que a Talita aprofunda.)

---

# 3. Entrevista — Fernando (STC · visão estratégica / gestão / auditoria)

> Fernando dá a leitura estratégica e institucional. A tese central dele organiza boa parte do projeto.

## 3.1. Papel
Visão estratégica e de gestão da informação/auditoria. Tem histórico com a cultura de transparência (ministrou formações sobre o tema).

## 3.2. A tese central: o gargalo é cultura, não tecnologia
- A maior barreira é o **comprometimento e a consciência dos órgãos**: a transparência ainda é vista como **demanda externa**, não como responsabilidade de quem detém a informação ("a informação é do órgão; a STC é só o canal").
- **Ferramenta tecnicamente boa não basta sem adesão** — experiências anteriores já faziam tratamento de campos vazios e devolução, e ainda assim perderam força por falta de envolvimento dos órgãos.
- Há **descontinuidade institucional**: trocas de governo/secretariado renovam equipes (majoritariamente comissionadas) e fazem o conhecimento e os processos se perderem — o que dificulta sustentar papéis fixos no longo prazo.

## 3.3. Princípios de design que decorrem da tese
1. **Fricção mínima** — como a cultura ainda não sustenta o processo, ele precisa ser fácil, dinâmico e pouco propício a erro, para não gerar retrabalho nem afastar quem responde.
2. **Recortar o processo que o órgão já faz**, em vez de criar um novo.
3. **Simplicidade** — quanto mais simples, maior a chance de sucesso e menor o custo de implantação.
4. **Estímulo cultural** — o **ranking** é tratado como instrumento de adesão, com possível **exposição pública** (com cautela).

## 3.4. A figura do ponto focal e a base institucional
- Fernando aponta a existência de uma **Instrução Normativa (IN) já redigida** que formaliza a figura do **agente de transparência / ponto focal**, com **titular e substituto** e **termo de ciência** de responsabilidade (envio, prazos, veracidade e integridade).
- Sugere **ancorar o ponto focal em estruturas que já existem em todos os órgãos** (como a ouvidoria, que tem responsável formal).
- O ponto focal **fixo é viável dentro de um mandato**; o risco está nas trocas de gestão.
- A IN deve ser recuperada com **Stéferson/Alessandra**. *(Atenção: a Talita relativiza isso — ver o conflito registrado na seção 4 e na síntese.)*

## 3.5. Tema 3 e a reestruturação do Tesauro
- A adaptação ao **Tema 3** (dicionário do governo federal) é tratada como **obrigatória** para interoperabilidade — a plataforma deve **editar o Tesauro**, que reflete no Tema 3, sem "fechar" o Tesauro dentro do código.
- O Tesauro atual precisa de **revisão e enxugamento**: tem campos/colunas a mais que geram confusão; o ideal é cada campo representar de fato o que diz.

## 3.6. Maturidade histórica da coleta
A coleta evoluiu junto com as ferramentas disponíveis (papel → e-mail → SEI, este recente, de dez/2024). Esse histórico ajuda a explicar por que ainda há tanto processo manual.

## 3.7. Sobre o mapeamento de órgãos (não estático)
Fernando cravou que o **mapeamento de órgãos por objeto não pode ser estático**. O caso central é **obras**: historicamente centralizadas na **Sinfra**, mas que por decreto passaram a incluir a **Cegov** (e há obras próprias de outras pastas). A composição muda por ato normativo, então o sistema precisa permitir incluir/remover órgãos na criação do ciclo.

---

# 4. Entrevista — Talita (operação / SIMONI)

> A entrevista mais densa até aqui. A Talita é **quem de fato executa** o cadastramento, a coleta e o tratamento dos dados. Ela apresenta o SIMONI e o Bitrix por dentro, valida o modelo do respondente e levanta o questionamento estratégico mais importante (SIMONI × Tesauro).

## 4.1. Papel e posição no fluxo
- Atua na **coleta dos dados manuais**; seu contato é **direto com os pontos focais das UGs**.
- Entrega na fase de **armazenamento** (o Drive da equipe); a partir daí a **STI** (equipe de tecnologia) joga tudo no **Portal da Transparência**.
- Participou de migrações de itens de **manual para automático**.
- Com a saída do Matheus para a TI, **a operação fica concentrada nela** (com o Andrey/André) — risco real de ponto único.

## 4.2. Como começa a coleta: Bitrix + SIMONI
- O processo inicial **resume-se a abrir uma tarefa no Bitrix** (gestor de tarefas), atrelada ao **SIMONI** (repositório/monitor).
- O **Bitrix** registra incidente, ações de contingência, falhas, documentação, evolução da tarefa e procedimentos — garantindo **rastreabilidade e continuidade**.
- O **SIMONI** valida a tarefa e indica **quem é o ponto focal naquela UG** para a coleta.
- Vínculo prático: abre-se a tarefa no Bitrix → copia-se o link → cadastra-se um **chamado** no SIMONI com **número e link do Bitrix**. Quem quiser acompanhar clica e vai direto ao Bitrix.
- Esse **par Bitrix↔SIMONI (planejamento/agendamento) é intuitivo e funciona** — foi usado "sem muito treinamento".
- O **SIMONI foi desenvolvido pelo Leandro**; o problema atual é só técnico (faltou um responsável de banco depois que o dev geral saiu; há "bugsinhos").

## 4.3. O SIMONI é todo baseado no PNTP
- **Todos os itens cadastrados no SIMONI seguem o PNTP** (Programa Nacional de Transparência Pública — ver Apêndice A).
- O Portal passa por **três avaliações anuais**; a principal é o **PNTP**, que concede o **Selo Diamante** — certificação muito valorizada pelo secretário e pelo governador (o Estado já o conquistou algumas vezes).
- O PNTP classifica os itens em **essenciais, obrigatórios e recomendados**; os **obrigatórios** (da ordem de ~124 itens, número que varia por ciclo) são os priorizados, porque são os que "tiram da briga" pela certificação.
- **Todo ano sai uma nova cartilha** do PNTP; a STC atualiza o SIMONI **item a item** com base nela: descrição minuciosa, **periodicidade** e prioridade de cada item.
- A **periodicidade vem do PNTP**, não é arbitrária. Exemplos citados: **despesa = a cada 30 dias**; **prestadores de saúde = quinzenal**.
- Os itens **manuais** a Talita cadastra no SIMONI; os **automatizados** a STI implementa direto no banco.

## 4.4. O SIMONI por dentro (telas)
Estrutura observada nas telas:
- **Dashboard:** três estados — **Itens Atualizados** (verde, ~52 / 80%), **Atualização Próxima** (amarelo, ~6 / 9,2%), **Atrasados** (vermelho, ~7 / 10,8%).
- **Lista de itens:** ID, item, responsável, seção, **data da última** e **da próxima atualização**, status e ações (**Detalhes** / **Chamado**).
- **Tabelas de apoio (quase um esquema de metadados):**
  - **Tipo de Processo:** Automatizado, Manual-BD, Manual-CMS, Manual-Cód, Manual-DA, Manual-GoogleDrive, "Manual-BD ou Automatizada com tratamento" (inativa), Testar Link.
  - **Tipo de Responsável:** **STR** (transparência — área da Talita), **STI** (tecnologia), **Ambos**.
  - **Tipo de Dado:** Arquivo PDF, Dados, Informações, Link, Planilha.
  - **Tipo de Fonte:** ~35 fontes (AGE, CBMMA, CGU, DETRAN, DPEMA, E-OUV, E-SIC, EMSERH, FAMEM, Google Analytics, …) — de onde vem cada informação.
  - **Seções:** ~46, agrupadas em "Cinza" (Acesso a Serviços, Controle, Gestão Fiscal, Informações Gerais, Informações Institucionais, Legislação) e "Dados Abertos" (Gestão Fiscal, Orçamento, Pessoal…).
- **Detalhe de um item** (ex.: "Ordens Bancárias por Lote – Listas de Beneficiários"): seção, nome, responsável (STR), fonte, tipo de processo (Manual-GoogleDrive), tipo de dado (Arquivo PDF), última/próxima atualização, **frequência** (30), **prazo necessário** (30), **instruções de Coleta** (inclusive a lista de UGs a notificar) e **Processo de Validação** detalhado (consolidar PDFs no ilovepdf, salvar no Drive em pasta padrão, preencher planilha com campos como Código SIGEF, Nº da Nota de Empenho, Nº da Ordem Bancária, Nome do Programa, Nº de Beneficiários, Lista de Beneficiários). **Há também um "Help de Atualização".**
- **Maranhão Transparente** (protótipo) aparece no menu do SIMONI, e o SIMONI aparece no menu do Maranhão Transparente — **os dois já se referenciam**.

> **Implicação:** cada item do SIMONI já é, na prática, **um "objeto com todos os seus metadados" mais as instruções de coleta e de validação**. Isso é a base do questionamento estratégico (seção 4.11 e Alerta no fim).

## 4.5. O Bitrix por dentro (telas)
Tarefa ("Big Numbers" / atualização de números mensais de acesso): título, descrição, responsável, prazo, status (Pendente / Em andamento / Concluída), criado, **projeto** ("Portal da Transparência"), etapa, **observadores** (ex.: Thiago), **bate-papo da tarefa**, histórico/linha do tempo, e a opção de **vincular ao SIMONI** (cadastrar chamado/tarefa com número e link do Bitrix).

## 4.6. A necessidade da Talita
- Poder **visualizar todos os itens como vê no SIMONI**: quando um item está a, por exemplo, **7 dias do vencimento**, o SIMONI dá um **alerta amarelo**.
- A partir do alerta, ela **entra em contato com o ponto focal da UG**, prepara **memorando** e/ou **Forms**, e faz a **cobrança**.
- **Transferências realizadas** é uma cobrança **ampla** (quase todas as UGs); exige montar a cobrança **secretaria por secretaria**, o que toma muito tempo.

## 4.7. O gargalo, reposicionado
- A **primeira parte** (planejamento/agendamento = Bitrix + SIMONI) **já funciona e é intuitiva**.
- O problema é a **segunda parte**: a **devolutiva/validação** das secretarias — "algo muito manual ainda".
- Frase-chave: **"não seria substituir o Bitrix nem o SIMONI; é resolver essa segunda parte."** A intuição é **reduzir o retrabalho manual constante** de receber e padronizar.

## 4.8. Cultura e dificuldade de resposta
- O tempo de resposta varia muito: secretarias mais atuantes (ex.: Sefaz, Egma) respondem rápido; **acordos/parcerias** podem demorar **meses**; uma mesma secretaria responde bem num processo e some no seguinte.
- A dificuldade é **mais cultural que técnica**: servidores mais antigos têm dificuldade com o processo via Forms (preencher online, subir no Drive); há **necessidade de capacitação**.
- Padrão recorrente: a equipe faz **passo a passo**, valida com um teste rápido ("recebeu? ok"), e mesmo assim **lá na frente o processo trava**.
- Onde há **pessoas mais novas** no setor, costuma funcionar (o chefe delega a quem tem mais facilidade); onde não há suporte de TI, emperra.
- Quando faltam respostas, o **secretário precisa instigar de secretário para secretário** ("só falta vocês").
- A **resposta negativa** é necessária para **validar o processo**: é preciso ter o "não temos" registrado, não só ausência.

## 4.9. O caso obras (sucesso via pressão de pares)
A planilha de obras das adjuntas era um **estresse mensal** (cada um mandava num formato e numa data; sempre ficava um pendente). O que destravou foi criar um **grupo de WhatsApp entre os gestores** das adjuntas de obras (Sinfra, Segov), gerando **pressão de pares** ("fulano já mandou, eu me sinto pressionado a mandar"), mais um **fluxo definido chefe a chefe** (alinhamento via Stéferson). Resultado: **"obras está redondo"**. As demais cobranças (transferências, despesas) seguem soltas.

## 4.10. Formato de envio e IA
- A Talita **apoia transformar o formato com IA**: o envio seria **por etapas**, e **cada etapa aceitaria qualquer formato, transformando-o** no padrão; com a IA fazendo isso, "o formato que vocês querem receber já não precisa existir", indo direto para a verificação de ortografia.
- Contexto político interno: a **chefia é muito atuante em TI** e **rejeita** a ideia de "baixar o padrão"/restringir formato ("não estamos mais no tempo dos primórdios").
- Ressalva dela própria: "depende muito do formato que esse filtro vai vir" — há conteúdo (convênios, termos) que é **texto/PDF e não se converte** em planilha.
- Reforço visual: investir no **visual e didático** ("eles não leem"); menos texto, mais etapas claras.

## 4.11. Convênios/parcerias: retrabalho de arquivos
Em convênios/parcerias, chegam **muitos arquivos**, que precisam ser **renomeados um a um** no padrão do Drive antes de irem para a base. Era trabalho de Talita + Matheus; com a saída do Matheus, recai sobre Talita + Andrey.

## 4.12. Validação da Opção (a) — ponto focal cadastra o respondente
A Talita descreveu, espontaneamente, exatamente o modelo da **opção (a)**:
- O **ponto focal** entra **autenticado** (login), tem **hierarquia maior**, **monitora** informações/notificações/andamento, e **cadastra quem vai responder** (só nome, e-mail e senha padrão).
- **Enquanto o ponto focal não cadastra o respondente, este não acessa o ciclo nem vê dado nenhum.** Depois de cadastrado, o respondente acessa **sem passar por identificação**, porque o vínculo à UG já foi feito por quem o cadastrou — **evitando o erro de selecionar a UG errada**.
- Sobre o link: o respondente acessa **pelo link recebido no SEI**, e **"talvez possa receber até por e-mail"**.

**A sacada do "bloqueio inicial":** hoje as planilhas têm bloqueio no **preenchimento dos empenhos/transferências**, mas **não têm o bloqueio inicial** (a parte em que a pessoa se identifica/vincula à UG). O modelo novo cria esse **bloqueio inicial** (pré-vínculo pelo ponto focal), que **filtra e converte**. Sem ele, "até a pessoa que não tem conhecimento tecnológico se tocar, já enviou no lugar de outra UG". Por isso ela considera que isso **reduz uma parte significativa** do retrabalho — e que deixar a própria pessoa se identificar **"teria os mesmos erros do Forms; só mudaria o visual"**.

## 4.13. O ponto focal ainda não existe formalmente (conflito a reconciliar)
- A Talita afirma que, **na prática, não há ponto focal definido**: "não tem, infelizmente". Falta **amparo jurídico/legislativo**, e **ninguém quer ser o ponto focal** ("a gente fica jogando de um para o outro; troca a pessoa e recomeça").
- Para ela, é **"o ponto de maior discussão"**: vai exigir **estratégia com as chefias** das outras secretarias para que as pessoas se voluntariem.
- **Isso conflita com o Fernando**, que mencionou uma **IN já redigida** formalizando o agente de transparência. Reconciliar: a IN existe mas não foi promulgada? está em rascunho? a Talita não foi informada? O **modelo (opção a, duas portas) depende** de existir ponto focal estável e respaldado — o desenho ela aprova; o que falta é a **base institucional e a adesão**.

## 4.14. Integração com o portal (parcial)
A integração com o Portal da Transparência tende a ser **parcial**: itens de **e-SIC** e **ouvidoria** se ligam ao **portal de dados abertos**, não ao da transparência; são **poucos itens** (uns 6–7) que não vêm diretamente.

## 4.15. O questionamento estratégico: SIMONI × Tesauro
Este é o ponto mais importante que a Talita levanta (detalhado no **Alerta** ao final):
- O **SIMONI já tem todos os itens**, item a item, **editáveis**, com periodicidade, fonte, responsável, coleta e validação.
- O **Tesauro** "basicamente transformou cada item em um objeto e colocou numa planilha".
- Integrar **SIMONI e Tesauro separadamente** seria **trabalho redobrado** ("a gente vai integrar uma planilha que já tem todos os itens; só mudou 'item' para 'objeto'").
- O **retrabalho de re-cadastrar tudo recai sobre ela** (sozinha, com o Andrey).
- Ela **não participou do projeto do Tesauro** (criado pela Alessandra, vencedor de um evento interno; veio "como ferramenta de IA para facilitar processos") e **não conhece o objetivo central** dele. Alessandra faz **projetos estratégicos**, não a coleta/validação/monitoramento.
- Recomendação dela: **pensar em integralização** — "integrar o SIMONI já integra o Tesauro"; o caso seria **reestruturar o SIMONI**, não duplicar. E ela pediu explicitamente que **a equipe dê sua opinião** com base no que viu.

## 4.16. Próximos passos sugeridos pela Talita
- Ir **presencialmente** ver o fluxo Bitrix↔SIMONI funcionando na prática (cadastramento de item, detalhamento, baixa).
- Ela enviaria o **resumo do PNTP** com os níveis de prioridade dos itens (base do cadastramento do SIMONI).

---

# Apêndice A — O PNTP (Programa Nacional de Transparência Pública)

> O PNTP é a base de tudo no SIMONI: define **quais itens existem**, **com que periodicidade** e **com que prioridade**. Entendê-lo é entender de onde vem a estrutura semântica real da coleta.

## A.1. O que é
O **PNTP** é uma iniciativa **coordenada pela Atricon, com o TCU e o TCE-MT** (apoio de IRB, Abracom, CNPTC, Conaci), **criada em 2022**, com o objetivo de **padronizar, orientar, estimular, induzir e fiscalizar a transparência ativa** dos órgãos públicos em todo o país (União, Estados, DF, Municípios e estatais).

## A.2. As três frentes
1. **Levantamento Nacional de Transparência Pública** — avaliação periódica e coordenada dos portais.
2. **Radar da Transparência Pública** — portal público que divulga os índices por órgão.
3. **Mês da Transparência Pública** — 18 de novembro, ações de estímulo.

## A.3. Como o portal é avaliado
- A avaliação se dá por uma **Matriz de Critérios**, organizada em **dimensões** (Receita, Despesa, Licitações, Contratos, RH, SIC, Ouvidoria, etc.). O número de critérios **varia por ciclo e por tipo de órgão** (foi ~124 em ciclos anteriores; ~176 no ciclo 2025; ~181 no ciclo 2026).
- Cada critério é classificado por **exigibilidade**:
  - **Essenciais** — informações de execução orçamentária/financeira (LRF). **Falhar um único essencial impede o órgão de receber transferências voluntárias e contratar operações de crédito**, e faz perder a certificação mesmo com índice alto.
  - **Obrigatórios** — exigidos expressamente por lei.
  - **Recomendados** — boas práticas, não exigidas em lei.
- Cada critério é checado por **itens de verificação**: **disponibilidade**, **atualidade** (informação de no máximo **30 dias** na consulta), **série histórica** (pelo menos **3 anos**), **gravação de relatórios** (download editável) e **filtro de pesquisa**.
- A avaliação é registrada no sistema oficial (**Sistema Avalia**), marcando "atende / não atende" com link de evidência.

## A.4. Selos e faixas
O índice (0–100%) define a faixa: **Diamante (95–100%)**, **Ouro (85–94%)**, **Prata (75–84%)**, e abaixo Elevado, Intermediário, Básico, Inicial, Inexistente. Para Diamante/Ouro/Prata exige-se **100% dos essenciais + acima de 75% do total**. No ciclo 2025, foram **mais de 10 mil portais avaliados** e ~2,9 mil certificados, dos quais **998 com Selo Diamante** — o que mostra o peso do selo que o Maranhão persegue.

## A.5. Por que isso importa para o projeto
- A **periodicidade do SIMONI deriva diretamente do PNTP** (ex.: despesa a cada 30 dias; prestadores de saúde quinzenal). O SIMONI reflete a lógica de priorização da matriz.
- O PNTP oferece um **critério externo, legitimado e pronto** (essencial > obrigatório > recomendado; disponibilidade/atualidade/série histórica) que pode **embasar a fórmula do ranking** interno, em vez de inventá-la do zero.
- A "atualidade de 30 dias" do PNTP é a **razão de fundo** da régua de prazos da coleta.

---

# Síntese cruzada das quatro entrevistas

## Confirmados
- **SIMONI = painel de monitoramento de prazos** (atualizado / próximo / vencido); **não coleta**, só avisa; sincronizado com o **Bitrix**. **[confirmado]**
- A **primeira metade** (planejamento via Bitrix+SIMONI) **funciona**; o problema é a **devolutiva/validação** (segunda metade). **[confirmado]**
- **Box edita até enviar o ciclo, depois trava**; ciclo só fecha com todos os boxes; trava no primeiro a responder. **[confirmado]**
- **Mapeamento de órgãos por objeto não é estático** (caso obras: Sinfra↔Cegov por decreto). **[confirmado]**
- **Registrar resposta negativa** como estado próprio. **[confirmado]**
- **Metadados obrigatórios travam o envio**. **[confirmado]**
- **SEI continua como porta de entrada/link**, não como canal de coleta; cresce por despacho sobre despacho. **[confirmado]**
- **Gargalo é cultura, não tecnologia**; princípios: fricção mínima, recortar o processo existente, simplicidade, ranking como estímulo. **[confirmado]**
- **Chatbot fora do escopo** (talvez futuro). **[confirmado]**

## Novos
- **O SIMONI é inteiramente baseado no PNTP** — a periodicidade e a prioridade dos itens vêm da cartilha anual do PNTP. **[novo]**
- **O SIMONI já contém todos os itens com metadados + coleta + validação** (telas confirmam). **[novo]**
- **STR** (transparência/Talita) × **STI** (tecnologia) como tipos de responsável. **[novo]**
- **SIMONI desenvolvido pelo Leandro**; falta responsável técnico de banco (bugs). **[novo]**
- **Convênios** geram retrabalho de renomear arquivos um a um no Drive. **[novo]**
- **Operação concentrada na Talita** com a saída do Matheus para a TI (risco de ponto único). **[novo]**
- **Bloqueio inicial**: o diferencial do modelo novo é vincular a UG **antes** do preenchimento (via cadastro pelo ponto focal). **[novo]**
- **Integração com o portal é parcial** (e-SIC/ouvidoria → dados abertos). **[novo]**
- **Pressão de pares + fluxo chefe a chefe** (caso obras/WhatsApp) como mecanismo cultural que funciona. **[novo · reforça H5]**

## Mudanças / inclinações
- **Identificação do respondente** inclina-se para a **opção (a)** — ponto focal cadastra o respondente, pré-vinculado à UG (validada por Thiago e Talita, com o argumento do bloqueio inicial). Ainda formalmente em aberto. **[em aberto · inclinado]**
- **Formato de envio** inclina-se para **transformar com IA** (Talita + chefia puxam contra restringir). Ainda em aberto, com a ressalva dos conteúdos textuais. **[em aberto · inclinado]**
- **Canal da correção** encaminhado para **canal secundário + plataforma** (evitar poluir o SEI). **[em aberto]**

## Em aberto (para a reunião de consolidação)
1. **Identificação do respondente** — (a) cadastro pelo ponto focal · (b) auto-identificação por texto · (c) híbrido.
2. **Formato de envio** — (a) restringir · (b) transformar com IA · (c) híbrido por tipo de dado.
3. **Canal da correção/devolução** — (a) SEI · (b) canal secundário + plataforma · (c) híbrido.
4. **Integração SIMONI ↔ plataforma** — (a) SIMONI avisa/inicia, separado · (b) monitoramento embutido na plataforma. *(Ver Alerta abaixo — esta pergunta cresceu.)*
5. **Ranking** — métricas, fórmula (possivelmente ancorada no PNTP) e se/como haverá exposição pública.
6. **Validação de veracidade** — quem, na STC, executa, e como difere da verificação.
7. **Base institucional e adesão do ponto focal** — reconciliar a IN (Fernando) com a ausência prática (Talita); definir como criar e respaldar o papel.

## Conflito a reconciliar
**Fernando** afirma existir uma **IN já redigida** formalizando o ponto focal; **Talita** diz que, na prática, **não há ponto focal nem amparo jurídico** e ninguém quer assumir o papel. Como o modelo inteiro (opção a, duas portas) depende de um ponto focal estável e respaldado, isso precisa ser esclarecido com **Stéferson/Alessandra** antes da consolidação.

---

# Alerta estratégico — SIMONI × Tesauro (a maior pergunta da consolidação)

A entrevista da Talita expõe uma questão de fundação do escopo, que precisa de **posição da equipe** antes da reunião:

**O Tesauro é redundante com o SIMONI?**

- O **SIMONI** já é a fonte viva: para cada item, ele guarda nome, seção, fonte, responsável, tipo de processo, tipo de dado, **periodicidade (derivada do PNTP)**, prazo, **instruções de coleta** (inclusive quais UGs) e **processo de validação**. Na prática, é "o objeto com seus metadados" — e ainda com o operacional.
- O **Tesauro/TemaTres** agrega o que o SIMONI **não** tem: a camada **semântica** — padronização de vocabulário e **interoperabilidade com o Tema 3** (dicionário federal). É um dicionário, não um monitor.
- Construir uma **gestão de Tesauro paralela** ao SIMONI implica **trabalho duplicado** (e o retrabalho recai sobre a Talita, hoje sozinha).

**Três interpretações possíveis do "Tesauro" (a confirmar com quem o concebeu):**

- **Interpretação A — catálogo de itens.** Se o Tesauro é "o que é cada item e suas características", isso **já existe no SIMONI** → reconstruir é retrabalho puro.
- **Interpretação B — camada semântica/terminológica.** No sentido técnico de Ciência da Informação (vocabulário controlado, sinônimos, hierarquia de termos, relações entre conceitos), o Tesauro **não compete com o SIMONI: enriquece-o**, fornecendo o vocabulário padronizado que os 60+ órgãos usam de formas diferentes. O próprio nome "Tesauro" (termo formal da área) é indício de que **esta pode ter sido a intenção original** — mas precisa ser confirmado.
- **Interpretação C — rótulo que sobrou.** O nome pode ter "sobrado" de uma fase inicial e o escopo real já ter migrado para gestão de coleta, sem formalização.

> **Ação barata e decisiva:** uma conversa de ~15 min com quem propôs/nomeou o projeto, perguntando direto: *"o Tesauro era para ser um dicionário de termos (semântico) ou um catálogo de itens (operacional)?"*. A resposta muda o escopo. **Ressalva de fato:** a **Alessandra**, que criou o Tesauro, **já foi entrevistada** numa sessão anterior — mas a intenção semântica × operacional **não foi cravada** com ela; é exatamente isso que falta confirmar. (A Talita não participou da concepção e não conhece o objetivo central.)


**As duas leituras possíveis (a decidir na consolidação):**

- **(a) Integrar/reestruturar o SIMONI** como base, e usar o Tesauro só onde acrescenta (camada semântica + Tema 3). Reduz duplicação; aproveita o que já funciona.
- **(b) Manter o Tesauro como motor semântico** e fazer o SIMONI conversar com ele. Preserva a aposta original (interoperabilidade nacional via Tema 3), ao custo de mais trabalho de integração.

**Reposicionamento do esforço que decorre disso:** a gestão (Fluxo 1) e o planejamento (SIMONI/Bitrix) **já funcionam e são intuitivos**. A dor real está no **Fluxo 2 — coleta, devolutiva e validação**. Isso sugere concentrar o esforço de construção no Fluxo 2, e tratar o Fluxo 1 como **integração/reestruturação** do que existe, não como reconstrução.

> A Talita pediu explicitamente que a equipe forme e leve uma **opinião** sobre isso. Não é decisão dos bolsistas sozinhos, mas é preciso chegar à reunião com a pergunta bem formulada e os dois caminhos com prós e contras.

---
---

# BLOCO B — Diagnóstico organizacional e recomendações (a validar)

> **Atenção:** daqui em diante o conteúdo é **análise e proposta**, não registro de fala. Deriva das reuniões, mas **ainda não foi validado com a STC**. Serve para *entender os problemas* e *preparar a validação das soluções* na reunião de consolidação. Onde há conflito com fatos já estabelecidos do projeto, está marcado com **⚠ divergência**.

## B.0. Divergências a ter em mente antes de usar este bloco

- **⚠ Stack.** Este diagnóstico, na origem, sugeria backend em Node.js/Python. **A stack oficial e inegociável do projeto é PHP/Laravel + PostgreSQL + Docker + Keycloak + GitLab + Tesseract** (catálogo SEATRAN/STC). As recomendações técnicas abaixo foram reescritas para respeitar essa stack; ignore qualquer sugestão de outra linguagem.
- **⚠ Ranking.** O diagnóstico recomenda ranking **interno, não público**. O **Fernando (STC)** defendeu **exposição pública** como estímulo cultural. São visões legítimas em conflito — levar as duas à reunião.
- **⚠ Ponto focal / IN.** O diagnóstico trata a formalização do ponto focal como ausente. O **Fernando** afirma existir uma **IN já redigida** (a Talita relativiza o efeito prático). Tratar como "existe no papel, falta vigência/adesão".
- **⚠ Concepção do Tesauro.** O diagnóstico diz que "quem concebeu o Tesauro não foi entrevistado". **A Alessandra foi entrevistada** — o que falta é cravar a intenção semântica × operacional com ela (ver Alerta).
- **⚠ Número de órgãos.** "60+ UGs" é uma referência de ordem de grandeza ainda **a confirmar** com a STC.

---

## B.1. Resumo executivo do diagnóstico

O projeto nasceu como "Tesauro", sob a premissa de que era preciso construir um dicionário estruturado dos objetos de transparência. Essa premissa **não foi cruzada com o inventário de sistemas já existentes** — e o SIMONI já cumpre, ao menos parcialmente, essa função (cadastro, descrição, periodicidade, responsáveis, histórico, alertas, monitoramento e integração com o Bitrix).

A reunião com a Talita expôs uma rachadura na fundação: a pessoa que opera o processo **não entende por que o Tesauro precisa existir ao lado do SIMONI**, e levantou — sem ser provocada — a hipótese de duplicação.

Leitura central: **o objeto do projeto pode estar mal definido, não que o esforço foi perdido.** O problema real é maior que catalogação: a STC depende de **coleta manual, sem padronização, com baixíssima resiliência a troca de pessoas-chave** (a Talita é ponto único de falha). Esse é o problema que vale resolver. Como dicionário de objetos, o Tesauro provavelmente não é a resposta; uma **camada de governança, automação e IA sobre o fluxo de coleta-validação** provavelmente é.

**Recomendação-síntese (a validar):** não construir o Tesauro como catálogo paralelo ao SIMONI; **reposicionar o trabalho como uma camada que se integra ao SIMONI (não o substitui) e respeita o Bitrix (não o recria).** Sujeito à confirmação da intenção original do Tesauro (ver Alerta).

### B.1.1. Nível de confiança e cautela política (importante)

A tese da duplicação é **plausível e bem fundamentada**, mas **ainda não está provada**. O nível de confiança hoje é *"suficiente para investigar com prioridade alta"*, **não** *"suficiente para decidir e comunicar como fato"*.

Por que a distinção importa: comunicar isso como **veredito fechado** para a STC, antes de confirmar com quem concebeu o Tesauro, pode soar como **a dupla de estagiários questionando decisões de servidores mais seniores sem ter ouvido o outro lado** — o que tem **custo político mesmo se a conclusão técnica estiver certa**. Evidências a favor (Talita não vê necessidade; o SIMONI já cobre cadastro/periodicidade/monitoramento) convivem com motivos de cautela (o termo "Tesauro" tem sentido técnico semântico distinto de "catálogo"; a Talita opera, mas não concebeu; decidir escopo com base em uma reunião só é arriscado). **Postura recomendada:** levar como *pergunta bem formulada*, não como sentença.

### B.1.2. Redefinição precisa do problema

O diagnóstico permite separar três coisas que estavam embaralhadas sob o nome "Tesauro":

1. **Catalogação operacional** — *já resolvida pelo SIMONI* (o quê/quando/quem/monitoramento).
2. **Gestão do ciclo de coleta** — *não resolvida por nada hoje*: solicitação → padronização de entrada → validação assistida → notificação → integração com SIMONI/Bitrix. **É a maior lacuna.**
3. **Padronização semântica/terminológica** entre os 60+ órgãos — *possível papel real do Tesauro* (Interpretação B), se for essa a intenção original.

Essa redefinição **não descarta o nome "Tesauro"** — apenas o coloca no lugar certo (camada 3), enquanto o esforço principal de construção vai para a camada 2.

---

## B.2. Diagnóstico organizacional

- **A STC é um hub de coleta, não um produtor de dados.** Ela não gera a maior parte do que publica — recebe de 60+ órgãos/UGs (número a confirmar). Um hub que depende de terceiros sem padronização nem SLA terá sempre baixa previsibilidade, por mais tecnologia que se some do lado da STC.
- **Concentração de conhecimento em uma pessoa.** A Talita centraliza contato com pontos focais, envio, recebimento, validação inicial, tratamento de arquivos, armazenamento e atualização no SIMONI — **bus factor = 1**. Férias/saída/mudança de função travam ou degradam o fluxo. É risco organizacional **independente de qualquer software**.
- **Maturidade desigual entre os órgãos externos.** A "baixa maturidade digital" não é problema técnico da STC — é característica do ecossistema de fornecedores de dados. Define o tipo de solução possível: uma plataforma sofisticada não resolve nada se o ponto focal não tem hábito/capacidade de usá-la. O caso obras (WhatsApp + prazos + responsáveis) prova que a solução que funcionou foi **de processo, não de software**.
- **Governança ainda informal.** Não há evidência de SLA formal, matriz de responsabilidades (RACI) STC×UGs, nem consequência institucional por atraso além do que o PNTP impõe de fora. A governança se apoia em **relacionamento pessoal** (Talita cobrando) mais que em processo.

---

## B.3. Diagnóstico tecnológico

**Já existe e funciona (ou parcialmente):**
- **SIMONI** — catálogo estruturado dos itens, baseado no PNTP: cadastro, descrição, periodicidade, responsáveis, histórico, alertas, monitoramento, rastreabilidade, validação (parcial) e integração com Bitrix.
- **Bitrix** — gestão de tarefas/chamados, com histórico e rastreabilidade. **Proprietário** → customização e integração dependem do que a API/webhooks expõem.

**Não existe ou é manual:**
- Sem pipeline automatizado de ingestão dos arquivos das UGs.
- Sem padronização de formato de entrada (cada órgão envia como quer).
- Sem validação automática no momento do envio (validação hoje é manual, da Talita).
- Sem dashboard de desempenho por UG.
- Sem notificação automática de pendência (cobrança é manual/pessoal).

**Implicação técnica central:** o SIMONI já fazer cadastro, periodicidade e monitoramento é a informação mais importante deste diagnóstico. Qualquer solução que **recrie esse catálogo do zero está duplicando** capacidade já em produção. O foco deve sair de "criar catálogo" para **"preencher as lacunas que o SIMONI não cobre"**.

---

## B.4. Mapeamento do fluxo atual e fricções

```
[UG / Órgão Externo]
      │ (1) Solicitação (manual, via Talita)
      ▼
[Talita — ponto focal STC]
      │ (2) Espera resposta (sem SLA, alta variabilidade)
      ▼
[Recebimento do arquivo/dado]
      │ (3) Validação inicial manual
      │ (4) Tratamento/reformatação manual
      ▼
[Cadastro/atualização no SIMONI]
      │ (5) Vinculação de tarefa no Bitrix, se necessário
      ▼
[Equipe de TI / STI]
      │ (6) Publicação no Portal da Transparência
      ▼
[Portal da Transparência — público]
```

| Etapa | Fricção | Manual? |
|---|---|---|
| (1) Solicitação | Sem ponto focal estável em várias UGs | Sim |
| (2) Espera | Sem SLA; resposta pode levar semanas/meses | N/A |
| (3) Validação | Depende do julgamento da Talita | Sim |
| (4) Tratamento | Renomear, reorganizar, converter formato | Sim |
| (5) Cadastro SIMONI | Manual, depende da disponibilidade da Talita | Sim |
| (6) Publicação | Depende da STI após validação | Parcial |

**Gargalo estrutural:** um **único caminho sem redundância**, passando por **uma pessoa em 4 das 6 etapas**. É mais relevante que qualquer decisão Tesauro × SIMONI.

---

## B.5. Atores e dependências

| Ator | Papel | Dependência que gera |
|---|---|---|
| **UGs / Órgãos (60+, a confirmar)** | Fonte primária dos dados | Maturidade digital variável; ponto focal instável |
| **Ponto focal por UG** | Interface STC ↔ órgão | Sem padronização de papel; rotatividade alta (a validar) |
| **Talita** | Operação completa (coleta→cadastro) | **Ponto único de falha (bus factor = 1)** |
| **STC (transparência)** | Supervisão; conformidade PNTP | Depende da Talita para execução |
| **STI (tecnologia)** | Publicação no Portal | Depende de dados validados chegarem certos |
| **Dupla de estágio** | Camada de automação/IA complementar | Depende da infra do colega + decisão de escopo |
| **Quem concebeu o Tesauro** | Intenção original | Alessandra entrevistada, mas intenção semântica não cravada |

---

## B.6. Gargalos

1. **Talita como gargalo humano** — 4 de 6 etapas passam por ela.
2. **Ausência de padronização de entrada** — retrabalho sistemático antes de qualquer validação.
3. **Falta de SLA/cobrança automatizada** — cobrança depende de iniciativa humana repetida.
4. **Sobreposição potencial Tesauro × SIMONI** — no melhor caso redundância, no pior duas fontes de verdade divergentes.
5. **Limite de integração com o Bitrix** — proprietário; profundidade de automação depende da API.

---

## B.7. Causa raiz (resumo dos "5 porquês")

- **Baixa taxa de resposta das UGs** → sem SLA nem consequência → sem cobrança automatizada → sem plataforma que centralize solicitação/prazo/lembrete. **Causa raiz: ausência de uma camada digital de gestão do ciclo de coleta com prazos e notificações.**
- **Retrabalho constante (renomear/converter)** → cada UG envia em formato diferente → sem padrão nem ferramenta que o force. **Causa raiz: ausência de canal de entrada padronizado e guiado.**
- **Dúvida sobre o papel do Tesauro** → concebido sem validar se o SIMONI já cobria → levantamento sem inventário de sistemas legados. **Causa raiz: requisitos levantados sem inventário prévio dos sistemas existentes.**

**Causa raiz transversal:** a maior parte das dores (coleta manual, falta de padronização, retrabalho, baixa resposta, dependência de pessoa-chave) **não é causada pela ausência de um Tesauro** — é causada pela ausência de uma **camada de gestão do processo de coleta** (workflow, prazos, padronização de entrada, notificação). Isso é estruturalmente diferente de um dicionário de objetos.

---

## B.8. Riscos

| Risco | Probabilidade | Impacto | Comentário |
|---|---|---|---|
| Construir o Tesauro e descobrir que duplica o SIMONI | Média-Alta | Alto | Já há sinal direto da própria Talita |
| Talita sair sem sucessão/documentação | Média | Alto | Organizacional; independe de TI |
| Bitrix não expor API suficiente | Média | Médio | Validar antes de prometer integração profunda |
| UGs não adotarem por baixa maturidade digital | Alta | Alto | Mitigável com design simples + onboarding ativo |
| IA antes de o processo base estar padronizado | Alta | Médio | IA sobre dado não padronizado tem baixa precisão |
| Projeto da dupla competir com a infra do colega | Média | Alto | Exige fronteira clara entre camadas |
| Descontinuar o Tesauro sem ouvir quem o concebeu | Média | Médio-Alto | Risco político/relacional interno |

---

## B.9. Lacunas do SIMONI = espaço de oportunidade real

O SIMONI cobre o "o quê / quando / quem / acompanhamento / execução de tarefa". O que ele **provavelmente não cobre** (a validar) é onde o projeto da dupla agrega sem duplicar:

1. **Padronização semântica entre termos** usados por UGs diferentes (é aqui que a Interpretação B do Tesauro se realizaria, como glossário/vocabulário controlado).
2. **Canal de entrada estruturado e guiado** para a UG enviar o dado já formatado.
3. **Validação automática** de conteúdo/formato no momento do envio.
4. **Extração assistida por IA** de dados de arquivos não estruturados (PDF/planilha variada).
5. **Indicadores de desempenho por UG** (ranking/score) com visão gerencial.
6. **Engajamento/notificação automática** dos pontos focais.

---

## B.10. Arquitetura proposta (camadas) — respeitando a stack oficial

> Princípio: **nenhuma camada nova duplica responsabilidade de um sistema existente.** A camada de coleta não vira um segundo SIMONI; a de IA não vira um segundo Bitrix; o dashboard consome dados das camadas abaixo, não recria cadastro próprio.

```
┌─────────────────────────────┐
│   CAMADA DE GOVERNANÇA       │  Dashboard · Ranking · KPIs
└──────────────┬──────────────┘
               │ consome
┌──────────────▼──────────────┐
│   CAMADA DE VALIDAÇÃO / IA   │  Extração · Padronização · Validação assistida
└──────────────┬──────────────┘
               │ alimenta / é alimentada
┌──────────────▼──────────────┐
│  CAMADA DE GESTÃO DE COLETA  │  Autenticação UG · Ciclos · Form guiado · Upload · Notificações
└──────────────┬──────────────┘
               │ integra (não substitui)
┌──────────────▼──────────────┐
│  SIMONI (catálogo/monitor)   │  + Bitrix (tarefas)
└──────────────┬──────────────┘
               ▼
        Portal da Transparência
```

**Integrações a validar tecnicamente (com o Antônio/STI):**
- **SIMONI** — idealmente via API ou banco compartilhado para sincronizar item ↔ ciclo; se não houver API, exportação/importação programada como primeira versão.
- **Bitrix** — via webhook/API REST (Bitrix24), para criar/atualizar tarefas a partir de pendências, **sem** recriar o conceito de tarefa.
- **IA** — serviço desacoplado para extração de PDFs/planilhas e padronização textual; **revisão humana obrigatória no MVP**.

**Stack (oficial, a respeitar):** backend **PHP/Laravel**; banco **PostgreSQL** (espelhando minimamente as entidades do SIMONI para não reinventar modelo); front **Tailwind**, com **formulário guiado simples** para pontos focais de baixa maturidade; **Keycloak** para os perfis fixos; **Docker/GitLab**; OCR **Tesseract** + parsing de planilha. ⚠ Não usar Node/Python como base do produto.

**Ponto crítico:** definir com o colega de infra qual sistema é **fonte de verdade** para cada entidade (item, UG, ciclo, tarefa) **antes** de escrever código, para não duplicar dados.

---

## B.11. Estratégias (governança, engajamento, gamificação, IA)

**Governança:**
- **Formalizar SLA de resposta por UG** (ex.: "5 dias úteis"), por ofício/e-mail, **antes** de automatizar a cobrança — automatizar prazo inexistente só gera atrito.
- **RACI simples** entre STC, ponto focal de cada UG e STI.
- **Plano de redundância para a função da Talita** — documentar o procedimento operacional dela (manual simples) reduz o bus factor = 1, independente de software.

**Engajamento das UGs (lição do caso obras):**
- Comunicação **direta e simples** (WhatsApp/e-mail) funciona melhor que depender só de plataforma nova, sobretudo na transição.
- **Clareza de responsável e prazo** importa mais que sofisticação.
- A plataforma deve **automatizar o que hoje é manual no modelo que já funciona** (notificação automática no lugar da mensagem no grupo), não substituir o canal que funciona.
- **Meet them where they are:** notificação via WhatsApp/e-mail que **linka para um formulário simples**, em vez de exigir login em portal complexo.

**Gamificação (com ⚠ divergência sobre exposição pública):**
- Recomendação do diagnóstico: começar **interno e positivo** — ranking visível só para gestores da STC; **selos/reconhecimento** ("UG 100% em dia") em vez de expor o atrasado; testar com 2–3 UGs piloto.
- ⚠ O **Fernando** defende **exposição pública** como estímulo. Decidir na reunião; possível meio-termo: positivo e público para os melhores, sem exposição punitiva dos piores no início.

**IA (ordem de prioridade pelos pontos de maior retrabalho):**
1. **Extração de dados de arquivos não estruturados** (reduz "renomear/reorganizar/converter").
2. **Padronização semântica/terminológica** (aqui mora a função B do Tesauro, como motor de glossário controlado).
3. **Validação inicial de completude/consistência**, sem substituir a validação humana no MVP.
4. **Assistente ao ponto focal** para reduzir idas e voltas por erro de preenchimento.
- **Segurança:** no MVP, a IA **nunca publica direto** no Portal sem revisão humana (custo de erro reputacional/legal alto).

---

## B.12. MVP recomendado, funcionalidades e métricas (a validar)

**MVP mais defensável** (não é o Tesauro original):
> Uma **camada de coleta guiada por UG**, com **notificação automática de prazo** e **integração de escrita básica com o SIMONI** — substituindo a parte mais manual e frágil do fluxo (etapas 1–4), sem recriar nada que o SIMONI ou o Bitrix já fazem.

Por que: resolve dor real e validada; não compete com sistemas existentes; é testável com poucas UGs piloto; cria a base padronizada de que a IA precisa para funcionar bem.

**Funcionalidades prioritárias:** autenticação por UG/ponto focal · abertura de ciclo com prazo · formulário guiado (estruturado, não arquivo livre) · upload com extração assistida por IA (básica no MVP) · notificação automática de prazo (e-mail, idealmente WhatsApp) · sincronização de escrita com o SIMONI · painel de pendências para a Talita.

**Funcionalidades futuras:** dashboard com KPIs por UG · ranking/gamificação · glossário semântico (se confirmada a Interpretação B) · validação automática completa (humano só em exceções) · abertura automática de tarefa no Bitrix a partir de pendência · self-service de indicadores para as UGs · assistente conversacional ao ponto focal.

**Métricas / KPIs sugeridos:**

| KPI | Meta inicial (linha de base a definir) | Frequência |
|---|---|---|
| Tempo médio de resposta por UG | −30% em 6 meses | Mensal |
| % de UGs piloto usando a plataforma | 80% das piloto | Mensal |
| Retrabalho manual da Talita | Redução perceptível no MVP; quantificar depois | Mensal |
| Erros de formato detectados **antes** da publicação | Aumentar (validação funcionando) | Por ciclo |
| Itens essenciais (PNTP) em conformidade | 100% (requisito do Selo Diamante) | Por avaliação PNTP |

---

## B.13. Recomendações finais (a validar na consolidação)

1. **Não construir o Tesauro como catálogo paralelo ao SIMONI** sem antes confirmar a intenção original (semântica × operacional) com quem o concebeu (Alessandra). Decisão de maior impacto, pendente de uma conversa curta.
2. **Reposicionar o trabalho da dupla** como camada de gestão de coleta + IA assistiva sobre SIMONI/Bitrix existentes — não como sistema substituto.
3. **Resolver a dependência da Talita** com documentação de processo, independente de software.
4. **Priorizar padronização de entrada antes de IA sofisticada** — IA rende mais sobre dado já estruturado.
5. **Gamificação com cautela** — começar interno e positivo; reconciliar com a posição do Fernando sobre exposição pública.
6. **Validar tecnicamente o que SIMONI e Bitrix expõem** (com o Antônio/STI) antes de prometer integração no documento formal.
7. **Respeitar a stack oficial** (PHP/Laravel + PostgreSQL + Docker + Keycloak) em qualquer proposta técnica.

---

## B.14. Conclusão estratégica

O projeto não está perdido — está, possivelmente, **mal-nomeado**. A investigação já feita (a reunião com a Talita, a dúvida levantada) é, na prática, o **discovery mais valioso** do projeto até aqui. O caminho mais defensável é tratar isso como **correção de rota**, não fracasso: usar o diagnóstico para confirmar a intenção real do Tesauro com a Alessandra e, então, propor — com segurança técnica e política — a redefinição de escopo para uma **camada de gestão de coleta e IA assistiva** que complementa o SIMONI e respeita o Bitrix.

**Próximo passo concreto:** agendar a conversa de validação da intenção do Tesauro (Alerta / B.13.1) **antes** de qualquer decisão de arquitetura ser tratada como definitiva — e levar à reunião de consolidação tanto o **Bloco A (fatos)** quanto este **Bloco B (proposta)**, deixando claro o que é decisão da STC e o que é recomendação da dupla.
