# Pontos em aberto para decisão da chefia

**Data da revisão:** 2026-08-13  
**Finalidade:** servir como pauta completa das decisões institucionais ainda necessárias.

Cada item explica o problema, separa o que já foi decidido e apresenta uma pergunta que pode ser
feita diretamente na reunião. Quando houver resposta, o resultado deve ser registrado no
`contextoSTC.md` e nos requisitos afetados, e o item deve ser removido deste arquivo.

## Ordem sugerida para a reunião

1. homologar o fluxo consolidado;
2. decidir o que bloqueia a implementação do MVP;
3. definir prazos, redirecionamentos e cobranças;
4. encaminhar temas que dependem de STI, jurídico ou áreas gestoras;
5. escolher o piloto;
6. deixar ranking e demais evoluções para uma pauta futura, se não houver tempo.

## Prioridade 1 — homologação e decisões que bloqueiam o MVP

### P-041 — Homologação do fluxo institucional consolidado

**Problema:** a chefia homologou perfil único, publicação automática, objeto fixo imutável, toggle
por UG, prazo pelo número SEI e validação como fechamento da resposta. Ainda é necessário consolidar o que permanece
aberto para a homologação operacional completa e para o piloto.

**O que já está definido no levantamento:** há uma coleta institucional por UG, contribuições por
adjunta, uma validação por Servidor STC e dois modos focais. No modo padrão, o respondente opera
diretamente com a STC; no modo ligado, o focal coordena e conclui.

**Pergunta para a chefia:** além das decisões de 2026-08-10, quais pendências deste documento precisam
ser resolvidas antes de homologar o fluxo completo e iniciar o piloto?

**Quem precisa participar:** chefia da STC e responsáveis pelo processo de coleta.

**Impacto se não houver decisão:** a implementação pode avançar por capacidades confirmadas, mas o
piloto e as integrações dependentes das pendências permanecem bloqueados.

### P-030 — Login e verificação do respondente

**Problema:** o autocadastro pelo link depende de confirmar que a pessoa pertence à UG. O
protótipo usa e-mail e senha simulados, mas ainda não existe método institucional aprovado.

**O que já está definido no levantamento:** haverá autocadastro pelo link e pré-cadastro pelo
ponto focal; o respondente poderá atuar em mais de uma adjunta.

**Pergunta para a chefia:** O acesso definitivo será verificado por e-mail institucional, CPF ou
outro identificador, e qual base confirmará o vínculo com a UG?

**Quem precisa participar:** chefia da STC, STI e encarregado de dados.

**Impacto se não houver decisão:** autenticação, cadastro, recuperação de acesso, LGPD e prevenção
de fraude ficam sem contrato definitivo.

**Regra provisória:** manter a autenticação apenas como simulação desacoplada.

### P-013 — Política de upload

**Problema:** já se sabe que cada contribuição terá um XLSX e caixas de anexos obrigatórias, mas
faltam os limites técnicos e os formatos permitidos. Sem esses parâmetros, não é possível
dimensionar armazenamento nem escrever validações e mensagens corretas.

**O que já está definido no levantamento:** cada caixa exige pelo menos um arquivo e aceita mais
de um; um único XLSX reúne todos os campos obrigatórios da contribuição.

**Pergunta para a chefia:** Qual será o tamanho máximo por arquivo e por contribuição, quais
extensões serão permitidas e haverá quantidade máxima de arquivos em cada caixa?

**Quem precisa participar:** chefia da STC, STI e infraestrutura.

**Impacto se não houver decisão:** upload, segurança, armazenamento e critérios de aceite ficam
incompletos.

**Regra provisória:** não fixar valor, extensão ou quantidade máxima no protótipo.

### P-012 — Política e classificação de sigilo

**Problema:** ainda não se sabe se algum objeto do piloto conterá informação sigilosa nem quais
regras de acesso, circulação e retenção deverão ser aplicadas.

**O que já está definido no levantamento:** a plataforma precisa manter rastreabilidade; nenhuma
classificação granular será inventada sem política aprovada.

**Pergunta para a chefia:** Haverá dados sigilosos no MVP; se houver, quais classificações serão
usadas, quem poderá acessá-los e como os arquivos poderão circular?

**Quem precisa participar:** chefia da STC, assessoria jurídica, encarregado de dados e STI.

**Impacto se não houver decisão:** autorização, armazenamento, notificações e conformidade com a
LGPD não podem ser fechados.

### P-022 — Mapeamento oficial entre objetos e UGs

**Problema:** a matriz da Alessandra é oficial para os objetos fixos, mas continua preliminar para
objetos variáveis e pode conter destinação incorreta.

**O que já está definido no levantamento:** no objeto fixo, as UGs vêm travadas do mapeamento. No
variável, o mapeamento apenas destaca sugestões e nenhuma UG é pré-selecionada.

**Pergunta para a chefia:** Quem validará e manterá a parte variável da matriz e qual processo
corrigirá destinações oficiais equivocadas?

**Quem precisa participar:** chefia da STC, Alessandra e áreas gestoras.

**Impacto se não houver decisão:** a destinação do objeto variável continua dependendo de
conferência manual; o objeto fixo segue a matriz vigente até correção formal.

### P-024 — Versão oficial e divergências do Tesauro

**Problema:** o arquivo recebido em 2026-08-11 se chama
`Tesauro_MA_Transparente_v2_6_agosto_2026.xlsx`, mas a aba de instruções declara v2.5 — julho/2026.
Os quatro objetos antes ausentes agora possuem metadados, porém a divergência de versão permanece.

**Pergunta para a chefia:** Qual arquivo e qual número de versão devem ser considerados oficiais,
e quem autoriza a correção de divergências internas?

**Quem precisa participar:** chefia da STC e SEATRAN.

**Impacto se não houver decisão:** proveniência, futuras importações e manutenção do catálogo
continuam ambíguas.

**Regra provisória:** preservar os XLSX v2.3 e v2.6 recebidos sem corrigir conteúdo e não reextrair o
catálogo até uma tarefa própria confirmar a fonte oficial.

## Prioridade 2 — operação, prazo e responsabilização

### P-034 — Redirecionamento depois de já existirem contribuições

**Problema:** a UG pode indicar que outra unidade é responsável, mas, se já houver planilhas ou
anexos enviados, mover a coleta pode transferir dados para quem não deveria vê-los ou apagar
evidências relevantes.

**O que já está definido no levantamento:** com toggle ligado, o focal indica o possível responsável;
desligado, o respondente envia a indicação diretamente à STC como não ocorrência justificada. A STC
efetiva a troca e a nova UG opera conforme seu toggle.

**Pergunta para a chefia:** Se já houver contribuições, o redirecionamento será bloqueado, os
arquivos permanecerão apenas no histórico da STC ou algum conteúdo será transferido à nova UG?

**Quem precisa participar:** chefia da STC, jurídico/encarregado de dados e STI.

**Impacto se não houver decisão:** privacidade, auditoria e responsabilidade sobre arquivos ficam
indefinidas.

**Regra provisória:** permitir a indicação de outra UG somente antes do primeiro envio.

### P-035 — Duração do período de envio atrasado

**Problema:** o prazo nasce do último número SEI e pode receber duas extensões separadas de cinco dias
úteis. Após a segunda, ainda não foi definido por quanto tempo uma resposta tardia poderá ser recebida.

**Pergunta para a chefia:** Por quantos dias úteis após a prorrogação o envio atrasado poderá ser
aceito?

**Quem precisa participar:** chefia da STC.

**Impacto se não houver decisão:** estados finais, relatórios e encerramento da coleta ficam
ambíguos.

**Regra provisória:** não iniciar automaticamente uma janela de atraso.

### P-036 — Forma de abertura do envio atrasado

**Problema:** além da duração, é necessário saber se a janela posterior às duas extensões ficará
aberta automaticamente ou dependerá de ação de um Servidor STC.

**Pergunta para a chefia:** O envio atrasado ficará disponível para toda UG que não enviou, ou um
Servidor STC deverá reabrir cada coleta individualmente?

**Quem precisa participar:** chefia da STC.

**Impacto se não houver decisão:** permissões, notificações e transições de estado não podem ser
implementadas.

### P-037 — Registro de cobranças e contatos sem resposta

**Problema:** a STC precisa acompanhar tentativas de contato, mas ainda não foi definido o que
constitui uma cobrança, quem a registra e quais informações são obrigatórias.

**Pergunta para a chefia:** Quais tipos de cobrança ou contato devem aparecer no histórico, quem
pode registrá-los e quais dados mínimos devem ser exigidos?

**Quem precisa participar:** chefia e equipe operacional da STC.

**Impacto se não houver decisão:** o acompanhamento fica em observações genéricas, sem indicador
confiável de tentativa de contato.

### P-038 — Relação entre cobrança, prazo e SEI

**Problema:** uma cobrança pode ser apenas operacional ou pode constituir reiteração formal com novo
número SEI. Somente a segunda reinicia prazo e restaura as duas prorrogações.

**Pergunta para a chefia:** Quais cobranças exigem novo número SEI e quais ficam apenas no histórico,
sem efeito sobre prazo ou prorrogações?

**Quem precisa participar:** chefia da STC e responsáveis pelo SEI.

**Impacto se não houver decisão:** a plataforma não pode calcular o efeito jurídico-operacional
de uma cobrança.

**Regra provisória:** cobrança sem novo número SEI não altera prazo; novo número registrado no ciclo
reinicia prazo e prorrogações.

### P-039 — Retenção de arquivos e histórico

**Problema:** já foi decidido que uma correção substitui o arquivo visível e que o binário antigo
não precisa ficar disponível, mas não existe prazo de guarda para o arquivo atual, comprovantes,
logs e metadados da coleta.

**Pergunta para a chefia:** Por quanto tempo devem ser mantidos os arquivos atuais, comprovantes
e registros de auditoria depois do encerramento do ciclo?

**Quem precisa participar:** chefia da STC, arquivo/gestão documental, jurídico e STI.

**Impacto se não houver decisão:** armazenamento, descarte, auditoria e LGPD ficam sem política.

## Prioridade 3 — modelos especiais e preparação do piloto

### P-014 — Obras, contratos e aditivos

**Problema:** obras e áreas afins podem precisar de planilha própria e de relação explícita entre
contrato, aditivo, medição e anexos. O modelo genérico pode perder essa rastreabilidade.

**Pergunta para a chefia:** Obras e contratos terão modelo próprio no MVP e, se tiverem, qual
identificador deverá vincular aditivos, medições e anexos ao contrato de origem?

**Quem precisa participar:** chefia da STC e áreas de obras, contratos e engenharia.

**Impacto se não houver decisão:** esses objetos devem permanecer no fluxo genérico com
conferência manual.

### P-042 — Escopo do piloto

**Problema:** a especificação permite vários objetos e UGs, mas ainda falta escolher uma amostra
controlada para validar cadastro, distribuição, contribuição, conferência e análise sem ampliar
o risco.

**Pergunta para a chefia:** Qual objeto será usado no piloto, quais UGs participarão e quais
adjuntas deverão estar representadas?

**Quem precisa participar:** chefia da STC, gestores do objeto escolhido e pontos focais das UGs.

**Impacto se não houver decisão:** não é possível preparar dados de demonstração, roteiro de
homologação e treinamento direcionados.

## Prioridade 4 — governança e limites do novo contrato

### P-044 — Governança da edição do catálogo

**Problema:** o catálogo importado será editável, enquanto o Tesauro externo continua mantido no
Tema 3. Uma importação futura pode conflitar com ajustes locais auditados.

**Pergunta para a chefia:** Quem responde pela divergência e como uma nova importação deve conciliar,
preservar ou substituir edições locais?

**Impacto se não houver decisão:** implementar edição persistente sem política de reconciliação pode
perder correções ou desalinhar a plataforma da fonte externa.

### P-045 — Mapeamento incorreto sem ponto focal

**Problema:** um objeto fixo usa UGs travadas do mapeamento oficial, mas a UG destinatária pode estar
incorreta e não possuir focal para fazer a indicação.

**Pergunta para a chefia:** Quem pode corrigir a destinação durante o ciclo e qual evidência deve ser
preservada antes de redirecionar ou criar nova coleta?

**Impacto se não houver decisão:** manter a UG errada ou corrigi-la informalmente compromete prazo,
auditoria e responsabilidade.

### P-046 — Visibilidade do ciclo publicado sem número SEI

**Problema:** o link funciona antes do número SEI e o prazo ainda não corre, mas não foi decidido se
as UGs devem descobrir o ciclo pelo painel ou apenas pelo link formalmente encaminhado.

**Pergunta para a chefia:** o ciclo publicado sem número SEI aparece nos painéis das UGs ou fica
acessível somente a quem possuir o link?

**Impacto se não houver decisão:** navegação, notificações e expectativa de prazo permanecem ambíguas.

### P-047 — Objetos automatizados no catálogo editável

**Problema:** oito objetos automatizados aparecem no Registro e continuam fora da criação manual.
Ainda não foi decidido se a manutenção do catálogo pode editar também esses objetos.

**Pergunta para a chefia:** a edição do catálogo alcança os oito objetos automatizados ou somente os
objetos manuais?

**Regra provisória:** manter os oito fora da criação manual e não ampliar seu escopo de edição.

### P-048 — Prazo da UG incluída depois do número SEI

**Problema:** o número SEI é único para o ciclo, enquanto prazo e prorrogações pertencem à coleta de
cada UG. Uma unidade pode entrar depois do primeiro número por redirecionamento ou por inclusão em
nova versão global e, sem regra própria, nascer com prazo já em curso, vencido ou indefinido.

**O que já está definido no levantamento:** a nova UG recebe uma coleta conforme seu toggle; o
primeiro número SEI inicia cinco dias úteis para as coletas então existentes; reiteração reinicia
prazo e prorrogações; prazo e extensões continuam individualizados por UG.

**Pergunta para a chefia:** Uma UG que entra no ciclo depois do registro do número SEI recebe cinco
dias úteis próprios contados da entrada, depende de um número SEI novo ou herda o prazo em curso?

**Quem precisa participar:** chefia da STC, responsáveis pela operação do SEI e equipe responsável
pela gestão das coletas.

**Impacto se não houver decisão:** a implementação pode cobrar imediatamente uma UG recém-incluída,
deixar sua coleta sem vencimento rastreável ou aplicar prorrogações sobre uma data sem fundamento.

**Regra provisória:** no ato da inclusão, não herdar prazo corrente ou vencido e não iniciar prazo
automaticamente para UG incluída depois do primeiro número SEI.

### P-049 — Nova demanda sobre resposta validada

**Problema:** a validação fecha a resposta e o pedido complementar foi retirado do contrato. Ainda
não foi definido se uma nova demanda para a mesma UG poderá abrir outra rodada no ciclo existente
ou se sempre exigirá outro ciclo.

**Pergunta para a chefia:** quando surgir nova informação necessária depois da validação, deve ser
criado outro ciclo ou uma nova rodada formal dentro do ciclo original?

**Quem precisa participar:** chefia da STC, responsáveis pela operação do SEI e equipe responsável
pela gestão das coletas.

**Impacto se não houver decisão:** reabrir a resposta apagaria o sentido da validação; criar uma
rodada sem contrato inventaria estados, prazo e auditoria.

**Regra provisória:** resposta validada permanece fechada e qualquer demanda nova exige outro ciclo.

## Prioridade futura — ranking de transparência

### P-007 — Publicidade do ranking

**Problema:** a finalidade do ranking é estimular transparência, mas a exposição pública pode
produzir efeitos institucionais diferentes de um painel interno.

**Pergunta para a chefia:** O ranking será público, restrito às UGs ou visível somente à STC?

**Quem precisa participar:** chefia da STC e comunicação institucional.

**Impacto se não houver decisão:** regras de acesso e comunicação não podem ser definidas.

**Regra provisória:** ranking fora do MVP.

### P-008 — Cálculo do ranking

**Problema:** ainda não existem critérios, pesos ou tratamento aprovado para atraso, correção,
não ocorrência e qualidade da resposta.

**Pergunta para a chefia:** Quais eventos gerarão pontos ou descontos, com quais pesos e em qual
período de apuração?

**Quem precisa participar:** chefia da STC e áreas técnicas responsáveis pelos indicadores.

**Impacto se não houver decisão:** não existe cálculo defensável nem dados mínimos definidos.

**Regra provisória:** ranking fora do MVP.

## Assuntos já resolvidos que não precisam voltar à pauta

- perfil interno único: Servidor STC, com permissão específica para registrar números SEI;
- validação de veracidade por qualquer Servidor STC, com uma única decisão;
- uma coleta institucional por UG e contribuições separadas por adjunta;
- distribuição e conferência pelo ponto focal somente com toggle ligado;
- envio direto à STC e focal apenas observador no modo desligado;
- ausência específica tratada por solicitação de edição;
- campos e anexos obrigatórios nunca podem ser simplesmente deixados vazios;
- objetos fixos e variáveis geram XLSX;
- catálogo de campos em acordeões pelos temas do Tesauro;
- mapeamento de Alessandra oficial e travado para objeto fixo, apenas referencial no variável;
- correlação anexo↔linha manual e planilhas recebidas separadamente;
- prazo contado em dias úteis;
- prorrogação 5+5 decidida por qualquer Servidor STC;
- primeira prorrogação no prazo normal e segunda somente no último dia útil da primeira;
- validação fecha a resposta; pedido complementar não integra o contrato vigente;
- redirecionamento executado pela STC;
- MT-0050, MT-0054, MT-0055 e MT-0056 recebidos com metadados no Tesauro novo (P-033 encerrada).
