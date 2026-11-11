**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 1 · MÓDULO 1**

**Planejamento & Orçamento**

*Ciclo orçamentário, orçamento por conta e dimensão, e o gatilho de
desvio já previsto na régua de aprovação do Fase 0*

*Revisão 8 --- ajuste de texto pelo Bloco 3 (Fase 0, revisão 45):
referência a Cad_Regua_Aprovador_Escopo trocada por Cad_Usuario_Escopo
(Fase 0, seção 13), que a substitui.*

*Revisão 7 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; origem do compromisso orçamentário desmembrada;
chave primária de Cad_Orcamento_Item_Dimensao.*

*Revisão 6 --- correção decorrente da revisão geral de módulos pedida
por Alberto: sete referências stale ao nome aposentado
Cad_Periodo_Contabil (Fase 0, revisão 37 renomeou para
Cad_Periodo_Fechamento) nunca tinham sido atualizadas neste documento,
apesar do bloco \"planejamento_orcamento\" em si já usar corretamente o
mecanismo novo desde a revisão 4 --- bug de consolidação encontrado na
auditoria cruzada, corrigido em todas as ocorrências (Introdução,
Cad_Exercicio_Orcamentario, os três ID_Periodo_Referencia, a tabela de
conexões e as Notas)*

*Revisão 5 --- fecha o ponto em aberto da revisão 4: quando o orçamento
é consolidado (Cad_Orcamento.ID_Filial vazio, \"fica tudo na matriz\"),
a checagem do bloco \"planejamento_orcamento\" não cascateia para filial
nenhuma --- consulta Cad_Periodo_Fechamento diretamente no nível Empresa
(Fase 0), já que o orçamento em si nunca tem granularidade de filial
nesse modo; o \"consumo\" (execução orçamentária real) é sempre a
somatória das filiais, derivada, sem checagem de fechamento própria*

*Revisão 4 --- comportamento do mecanismo transversal de fechamento de
período (Fase 0, seção 10) para o bloco \"planejamento_orcamento\":
protege só o passado (Cad_Orcamento_Item_Mes de competência já fechada
não pode ser alterado), sem travar o módulo inteiro como os demais
blocos de Fase 1/2/5/6; o restante do orçamento (novas versões, meses
futuros) segue livre para elaboração e revisão normal, decisão
confirmada por Alberto*

*Revisão 3 --- chave orçamentária configurável, efeito caixa
(competência vs. desembolso) e descrição de versão*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o primeiro módulo da Fase 1 --- Planejamento &
Orçamento --- no mesmo formato usado no dicionário de dados da Fase 0,
mas com uma diferença deliberada: aqui função e dados vêm juntos,
entidade por entidade, porque este módulo não é um motor transversal, é
um consumidor de negócio dos motores transversais. Ele referencia
Cad_Empresa, Cad_Filial, Cad_Conta_Contabil, Cad_Dimensao_Contabil,
Cad_Periodo_Fechamento (bloco=\"contabilidade\" --- corrigido na revisão
6, era citado aqui pelo nome aposentado Cad_Periodo_Contabil),
Cad_Produto_Servico, Cad_Participante, Cad_Grupo_Economico e
Cad_Regua_Aprovacao em vez de redefini-los --- exatamente como o
\"Próximo passo\" da Fase 0 previu.

A Revisão 3 incorporou a segunda rodada de comentários seus --- chave
orçamentária configurável, efeito caixa do orçamento (competência vs.
desembolso) e descrição de versão. Esta é a Revisão 4: descreve, no
próprio texto (seção 2), o comportamento do mecanismo transversal de
fechamento de período (Fase 0, seção 10, revisão 37) para o bloco
planejamento_orcamento --- convite deixado na revisão 13 do módulo de
Compras para que cada módulo já entregue registrasse o que
especificamente o fechamento do seu bloco trava. Aqui o comportamento é
deliberadamente diferente do padrão adotado pelos demais módulos:
fechamento protege só o passado, não trava o módulo inteiro. Cabe a você
continuar corrigindo com a realidade da Mlegate e de seus clientes, no
mesmo ritmo de revisão comentário-a-comentário usado na Fase 0: vá
comentando o que estiver errado ou faltando, e no final me avise para
consolidar.

Fica FORA deste rascunho, por decisão de escopo (não por esquecimento):
orçamento de investimento com fluxo de aprovação de projeto plurianual
(Capex plurianual) e qualquer integração com planejamento estratégico de
longo prazo --- ficam para quando o módulo de Gestão de
Contratos/Projetos for especificado. Orçamento de receita por produto,
família, cliente, grupo de clientes e região JÁ está coberto aqui, na
seção 2.

2\. O Orçamento --- Ciclo, Elaboração e Revisão

O orçamento nasce como rascunho, passa por aprovação --- reaproveitando
a mesma Régua de Aprovação do Fase 0, sem nenhuma estrutura nova --- e
fica vigente por um exercício. Pode ser revisado quantas vezes forem
necessárias ao longo do exercício: cada revisão gera uma VERSÃO NOVA e
passa pela mesma aprovação, nunca edita a versão anterior. O histórico
de todo orçamento que já valeu em algum momento (o original e cada
revisão) fica preservado, mesmo depois de substituído --- é o mesmo
padrão de vigência-por-substituição já usado em Cad_Regua_Aprovacao no
Fase 0. Pode ser feito por empresa (consolidado) ou por filial
específica, e o exercício em si não precisa ser o ano-calendário.

Cad_Exercicio_Orcamentario

O ciclo orçamentário de uma empresa --- nem sempre é o ano-calendário:
pode ser um ano gerencial deslocado (ex.: abril a março, para uma
empresa cujas vendas se concentram em dezembro/janeiro/fevereiro), ou
uma safra de duração variável (4 a 8 meses, cruzando anos-calendário).
Datas, não números de ano, são o que sustentam essa flexibilidade ---
este cadastro é independente de Cad_Periodo_Fechamento (Fase 0,
bloco=\"contabilidade\", sempre calendário, usado para SPED e apuração
de resultado --- corrigido na revisão 6: o nome aposentado
Cad_Periodo_Contabil ainda aparecia aqui, sem acompanhar a generalização
da Fase 0 revisão 37): um define o ciclo gerencial, o outro o período
fiscal/regulatório.

*Vigência: não --- cada exercício é o registro de um ciclo específico já
definido; um novo ciclo é um novo registro, não uma edição deste.*

  ------------------ ----------------- ----------------------------------------
  **Campo**          **Tipo lógico**   **Descrição / regra**

  **ID_Exercicio**   *identificador*   ---

  **ID_Empresa**     *referência       ---
                     (Cad_Empresa)*    

  **Rotulo**         *texto*           Ex.: \"Exercício 2025/2026\", \"Safra
                                       2025/2026\".

  **Data_Inicio**    *data*            ---

  **Data_Fim**       *data*            Junto com Data_Inicio, sustenta qualquer
                                       duração e qualquer mês de início ---
                                       inclusive um ciclo mais curto ou mais
                                       longo que 12 meses.
  ------------------ ----------------- ----------------------------------------

Cad_Orcamento

O orçamento de um exercício (Cad_Exercicio_Orcamentario), para uma
empresa ou uma filial específica. Cada revisão é um novo registro (nova
versão), nunca uma edição do anterior --- e passa pela mesma aprovação
da régua do Fase 0, cuja instância fica referenciada aqui para rastrear
quem aprovou.

*Vigência: sim --- cada revisão é uma nova versão (novo ID_Orcamento),
nunca uma edição da versão anterior; é o próprio mecanismo de histórico
de revisão orçamentária.*

  ---------------------------- ------------------------------- -------------------------------------------------
  **Campo**                    **Tipo lógico**                 **Descrição / regra**

  **ID_Orcamento**             *identificador*                 Chave própria de cada versão --- não é
                                                               reaproveitada entre revisões.

  **ID_Orcamento_Versao**      *identificador da versão*       Chave primária da versão (tabela física
                                                               Cad_Orcamento_Versao). ID_Orcamento é a
                                                               identidade, única e referenciada pelas outras
                                                               tabelas; cada versão guarda a sua janela de
                                                               vigência --- Fase 0, seção 2.

  **ID_Empresa**               *referência (Cad_Empresa)*      ---

  **ID_Filial**                *referência (Cad_Filial,        Quando vazio, é o orçamento consolidado da
                               opcional)*                      empresa como um todo; quando preenchido, é o
                                                               orçamento de uma filial específica. Os dois modos
                                                               não coexistem para o mesmo Exercício --- é uma
                                                               escolha operacional da empresa, não imposta pela
                                                               estrutura.

  **ID_Exercicio**             *referência                     O ciclo orçamentário coberto --- não
                               (Cad_Exercicio_Orcamentario)*   necessariamente o ano-calendário.

  **Versao**                   *número*                        1 para o orçamento original; incrementa a cada
                                                               revisão aprovada.

  **Descricao_Resumida**       *texto*                         Ex.: \"Orçamento 2026 --- revisão de outubro após
                                                               queda de vendas\". Dá contexto imediato a quem
                                                               está comparando versões, sem precisar abrir o
                                                               detalhe.

  **Descricao_Detalhada**      *texto longo*                   O racional completo da versão --- o que mudou e
                                                               por quê em relação à anterior. Junto com
                                                               Descricao_Resumida, é o que dá ao usuário
                                                               controle real sobre o que compõe cada versão do
                                                               orçamento, além do Status/Versao numéricos.

  **Status**                   *enumeração {rascunho,          Entre todas as versões de uma mesma Empresa (e
                               em_aprovacao, aprovado,         Filial, quando aplicável) e Exercício, só uma
                               substituido, encerrado}*        pode estar com Status=aprovado a qualquer momento
                                                               --- essa é o orçamento vigente, o que
                                                               efetivamente direciona a empresa; \"substituido\"
                                                               marca a versão anterior no momento em que uma
                                                               revisão é aprovada; \"encerrado\" marca o fim do
                                                               próprio exercício.

  **ID_Instancia_Aprovacao**   *referência                     A instância de aprovação (régua do Fase 0,
                               (Mov_Aprovacao_Instancia,       Origem_Tipo=aprovacao_orcamento) que aprovou esta
                               opcional)*                      versão --- o aprovador em si vem de
                                                               Mov_Aprovacao_Decisao.ID_Participante_Aprovador
                                                               associado a essa instância. Preenchido quando
                                                               Status muda para aprovado.

  **Data_Aprovacao**           *data/hora*                     Quando Status passou para aprovado.

  **Vigencia_Inicio**          *data*                          Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                          Último dia em que esta versão vale (inclusive).
                                                               Sempre preenchida: 31/12/9999 quando o fim é
                                                               indefinido (versão vigente) --- convenção da Fase
                                                               0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*               Por que esta versão foi criada.
  ---------------------------- ------------------------------- -------------------------------------------------

Cad_Orcamento_Chave

Define, para uma versão específica do orçamento, quais chaves analíticas
estão ativas --- o usuário escolhe isso no início da elaboração daquela
versão, e a partir daí Cad_Orcamento_Item só aceita preencher as chaves
aqui listadas. Resolve o fato de que as quebras analíticas variam de
empresa para empresa: uma empresa que orça só por conta simplesmente não
cria nenhuma linha aqui; outra que quebra por produto e cliente ativa só
essas duas.

*Vigência: não --- é definida uma vez, no início da elaboração daquela
versão; mudar a chave orçamentária no meio normalmente implica numa nova
versão, mesma lógica de Cad_Orcamento.*

  ------------------ ------------------------- ----------------------------------------
  **Campo**          **Tipo lógico**           **Descrição / regra**

  **ID_Chave**       *identificador*           ---

  **ID_Orcamento**   *referência               ---
                     (Cad_Orcamento)*          

  **Tipo_Chave**     *enumeração {produto,     Qual quebra analítica está ativa nesta
                     familia_produto, cliente, versão do orçamento.
                     grupo_economico,          
                     dimensao}*                

  **ID_Dimensao**    *referência               Preenchido só quando Tipo_Chave=dimensao
                     (Cad_Dimensao_Contabil,   --- identifica QUAL dimensão está ativa
                     opcional)*                (ex.: Centro de Custo, Planta, Região),
                                               já que pode haver mais de uma dimensão
                                               configurada ao mesmo tempo.
  ------------------ ------------------------- ----------------------------------------

Cad_Orcamento_Item

A regra de orçamento para uma conta contábil --- e, quando aplicável,
produto/cliente/dimensão --- dentro de uma versão específica de
Cad_Orcamento. Inclui o Balizador, que decide como o saldo se comporta
mês a mês. Os valores mensais em si ficam em Cad_Orcamento_Item_Mes,
logo abaixo: separar os dois evita repetir o Balizador (e as demais
chaves analíticas) em 12 linhas idênticas por ano.

*Vigência: não --- pertence a uma versão imutável do orçamento; a
correção é uma nova versão (Cad_Orcamento), não uma edição deste item.*

  --------------------------------------- -------------------------------------- ----------------------------------------
  **Campo**                               **Tipo lógico**                        **Descrição / regra**

  **ID_Item**                             *identificador*                        ---

  **ID_Orcamento**                        *referência (Cad_Orcamento)*           ---

  **ID_Conta_Contabil**                   *referência (Cad_Conta_Contabil)*      Só contas analíticas fazem sentido aqui;
                                                                                 a Natureza da própria conta (Fase 0) já
                                                                                 distingue receita/despesa/custo/ativo,
                                                                                 sem precisar de um campo novo neste
                                                                                 módulo.

  **Balizador**                           *enumeração {mensal, periodo}*         \"mensal\": o valor de cada mês é um
                                                                                 teto isolado --- o que não for usado não
                                                                                 passa para o mês seguinte (ex.: mão de
                                                                                 obra). \"periodo\": o valor se acumula
                                                                                 ao longo do exercício, podendo ser
                                                                                 antecipado ou postergado de um mês para
                                                                                 o outro sem ferir o orçamento (ex.: uma
                                                                                 compra planejada que desloca de mês). É
                                                                                 regra desta VERSÃO do orçamento, não
                                                                                 característica fixa da conta --- um
                                                                                 orçamento de outro exercício pode
                                                                                 classificar a mesma conta de outro
                                                                                 jeito.

  **ID_Produto_Servico**                  *referência (Cad_Produto_Servico,      Preenchido só se Tipo_Chave=produto
                                          opcional)*                             estiver ativo em Cad_Orcamento_Chave
                                                                                 para este orçamento. Para orçamento de
                                                                                 receita quebrado por produto específico.

  **ID_Produto_Servico_Dimensao_Valor**   *referência                            Preenchido só se
                                          (Cad_Produto_Servico_Dimensao_Valor,   Tipo_Chave=familia_produto estiver
                                          opcional)*                             ativo. Para quebra por
                                                                                 família/classe/marca --- reaproveita o
                                                                                 mesmo sistema de níveis de produto já
                                                                                 definido no Fase 0.

  **ID_Participante**                     *referência (Cad_Participante,         Preenchido só se Tipo_Chave=cliente
                                          opcional)*                             estiver ativo. Para quebra por cliente
                                                                                 específico.

  **ID_Grupo_Economico**                  *referência (Cad_Grupo_Economico,      Preenchido só se
                                          opcional)*                             Tipo_Chave=grupo_economico estiver
                                                                                 ativo. Para quebra por grupo de
                                                                                 clientes.
  --------------------------------------- -------------------------------------- ----------------------------------------

Cad_Orcamento_Item_Dimensao

O vínculo entre um item do orçamento e os valores de dimensão contábil
que ele carrega --- mesmo padrão N:N de Mov_Lancamento_Dimensao (Fase
0). Só se aplica quando pelo menos um Tipo_Chave=dimensao estiver ativo
em Cad_Orcamento_Chave para este orçamento. Permite chave composta (ex.:
Planta e Centro de Custo ao mesmo tempo, cada uma sua própria linha
aqui) sem exigir uma combinação fixa pré-cadastrada. Região entra aqui
também, se a empresa configurar \"Região\" como uma
Cad_Dimensao_Contabil --- sem precisar de campo dedicado.

*Vigência: não --- mesmo raciocínio do item: pertence a uma versão
imutável do orçamento.*

  ----------------- -------------------------------- ----------------------------------------
  **Campo**         **Tipo lógico**                  **Descrição / regra**

  **ID_Item**       *referência (Cad_Orcamento_Item) ---
                    --- chave primária (composta)*   

  **ID_Dimensao**   *referência                      ---
                    (Cad_Dimensao_Contabil) ---      
                    chave primária (composta)*       

  **ID_Valor**      *referência                      ---
                    (Cad_Dimensao_Contabil_Valor)*   
  ----------------- -------------------------------- ----------------------------------------

Cad_Orcamento_Item_Mes

O valor orçado --- e, quando aplicável, a quantidade orçada --- de um
item do orçamento, mês a mês. Separado do cabeçalho (Cad_Orcamento_Item)
porque o Balizador e as demais chaves valem para o item inteiro; só o
valor muda de mês para mês.

*Vigência: não --- mesmo raciocínio do cabeçalho: pertence a uma versão
imutável do orçamento.*

  --------------------------- --------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**             **Descrição / regra**

  **ID_Item_Mes**             *identificador*             ---

  **ID_Item**                 *referência                 ---
                              (Cad_Orcamento_Item)*       

  **ID_Periodo_Referencia**   *referência                 O mês orçado, sempre em calendário ---
                              (Cad_Periodo_Fechamento,    para que orçado e realizado
                              Fase 0,                     (Mov_Lancamento, Fase 0) sejam sempre
                              bloco=\"contabilidade\")*   comparáveis período a período, mesmo
                                                          quando o exercício gerencial
                                                          (Cad_Exercicio_Orcamentario) não é o
                                                          ano-calendário. Corrigido na revisão 6
                                                          --- o nome aposentado
                                                          Cad_Periodo_Contabil ainda aparecia
                                                          aqui.

  **Valor_Orcado**            *número*                    ---

  **Quantidade_Orcada**       *número, opcional*          Para quando o orçamento controla
                                                          quantidade, não só valor --- ex.: número
                                                          de contratações permitidas naquele mês
                                                          naquele centro de custo, não apenas o
                                                          valor da folha. Vazio quando não se
                                                          aplica.
  --------------------------- --------------------------- ----------------------------------------

*Comportamento de aplicação (não é um campo novo de dados), adicionado
na revisão 4: diferente dos demais módulos deste dicionário --- Compras,
Produção, Expedição, Vendas e Tesouraria --- que travam a
criação/alteração de qualquer movimento datado numa competência fechada
do seu bloco, bloqueando o módulo inteiro (regime fail-closed sobre
Cad_Periodo_Fechamento_Filial, mecanismo transversal da Fase 0, seção
10), aqui o bloco \"planejamento_orcamento\" protege só o PASSADO. Antes
de aceitar uma alteração em Cad_Orcamento_Item_Mes, o sistema consulta o
status de fechamento pela competência derivada de ID_Periodo_Referencia
(o mês orçado acima) --- só bloqueia a alteração quando essa competência
estiver fechada; mesmo regime fail-closed dos demais módulos, a ausência
de uma linha aberta também é tratada como fechada. Para uma competência
aberta ou futura, a alteração segue totalmente livre, sem qualquer
restrição adicional: o restante do orçamento --- novas versões
(Cad_Orcamento), novos itens, meses à frente --- não é afetado. Não
existe aqui o conceito de \"módulo travado\" nem de \"não entra nada
novo\" que vale para os demais módulos de Fase 1: orçamento é
planejamento prospectivo, não execução transacional, e fechar o passado
não pode impedir que a empresa continue orçando o futuro. Decisão
confirmada explicitamente por Alberto: \"o planejamento e orçamento,
período fechado não mexe, só da data para frente\". Consistente com esse
formato, não há aqui validação de pendência no próprio fechamento (o
único ponto do dicionário com essa checagem, até agora, é Compras,
revisão 13) --- o conceito não se aplica a um bloco cuja trava é só uma
proteção pontual do passado, não um encerramento geral do período.*

*Revisão 5 --- nível da checagem, resolvido: Alberto confirmou que
Planejamento & Orçamento \"é consolidado, fica tudo na matriz, e o
\'consumo\' do orçamento fica na somatória as filiais\" --- ou seja,
Cad_Orcamento praticamente sempre opera no modo consolidado (ID_Filial
vazio), nunca por filial individual nesta empresa. Nesse modo, a
checagem de fechamento NÃO cascateia para Cad_Periodo_Fechamento_Filial
(diferente de todos os outros blocos deste dicionário, que sempre
consultam o nível filial) --- consulta Cad_Periodo_Fechamento
diretamente no nível Empresa (Fase 0, seção 10), porque o orçamento em
si nunca tem granularidade de filial para checar. Quando,
excepcionalmente, Cad_Orcamento.ID_Filial vier preenchido (orçamento de
uma filial específica, ainda suportado pela estrutura), a checagem volta
a cascatear normalmente para Cad_Periodo_Fechamento_Filial daquela
filial, mesmo padrão dos demais blocos. O \"consumo\" --- a execução
orçamentária real (seção 4, Compromisso e Realizado) --- é sempre a
somatória do que aconteceu em cada filial, um valor DERIVADO (nunca
armazenado, mesmo princípio de todo o dicionário) a partir dos
lançamentos/documentos de cada filial; ele não tem, e não precisa ter,
uma checagem de fechamento própria --- quem está fechado é o orçamento
(Cad_Orcamento_Item_Mes) no nível em que ele existe, não a soma que o lê
depois.*

3\. Efeito Caixa --- Orçamento por Competência vs. Desembolso

O orçamento modelado até aqui (Cad_Orcamento_Item_Mes) é por
competência/regime contábil --- o valor no mês em que a despesa é
reconhecida, o mesmo regime usado por Mov_Lancamento e exigido pelo SPED
Contábil. Mas toda despesa também gera um efeito caixa, que pode cair em
meses completamente diferentes: o 13º salário e as férias são
provisionados mês a mês, mas o 13º desembolsa concentrado em
novembro/dezembro e as férias só desembolsam quando o funcionário
efetivamente tira a folga; uma compra de imobilizado pode ser paga em N
parcelas, no ritmo que o usuário definir (mensal, a cada dois meses, ou
qualquer outro). Não existe uma relação fixa entre o mês da competência
e o mês do desembolso --- pode ser vários meses de provisão concentrando
num desembolso só, ou um único evento se desdobrando em várias parcelas.

Cad_Orcamento_Item_Desembolso

O cronograma de desembolso projetado de um item do orçamento ---
desacoplado da distribuição por competência em Cad_Orcamento_Item_Mes. O
usuário lança quantas linhas quiser, em quaisquer meses e valores; o
sistema não impõe nenhuma periodicidade. Dá, junto do orçamento por
competência, uma projeção de fluxo de caixa.

*Vigência: não --- mesmo raciocínio dos demais itens: pertence a uma
versão imutável do orçamento.*

  --------------------------- --------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**             **Descrição / regra**

  **ID_Desembolso**           *identificador*             ---

  **ID_Item**                 *referência                 ---
                              (Cad_Orcamento_Item)*       

  **ID_Periodo_Referencia**   *referência                 O mês do desembolso projetado ---
                              (Cad_Periodo_Fechamento,    independente do(s) mês(es) de
                              Fase 0,                     competência do mesmo item em
                              bloco=\"contabilidade\")*   Cad_Orcamento_Item_Mes. Corrigido na
                                                          revisão 6 --- o nome aposentado
                                                          Cad_Periodo_Contabil ainda aparecia
                                                          aqui.

  **Valor_Desembolso**        *número*                    ---
  --------------------------- --------------------------- ----------------------------------------

Quando existir um módulo de Tesouraria/Contas a Pagar (ainda não
especificado), o desembolso REAL vai ser comparado contra esta projeção
--- o mesmo papel que Mov_Lancamento já cumpre hoje comparado contra o
orçado por competência.

4\. Compromisso e Realizado --- Acompanhamento Orçamentário

O orçamento não é comparado só contra o que já foi lançado contabilmente
(Mov_Lancamento, Fase 0) --- também precisa considerar o que já foi
COMPROMETIDO mas ainda não virou lançamento: um pedido de compra
aprovado, por exemplo, consome orçamento no momento em que é aprovado,
não só quando a nota fiscal chega e é lançada semanas depois. Sem isso,
dois pedidos aprovados no mesmo dia --- cada um dentro do limite
individualmente --- poderiam estourar o orçamento juntos sem que o
sistema percebesse até o lançamento contábil de ambos.

Mov_Compromisso_Orcamentario

Um compromisso assumido contra uma linha do orçamento. Hoje o gatilho
mais óbvio é um pedido de compra aprovado (módulo Compras, ainda a ser
especificado), mas a estrutura é genérica o suficiente para qualquer
transação futura que precise reservar orçamento antes do lançamento
contábil. É movimentação (evento), não cadastro.

*Vigência: não --- é o registro de um evento pontual (compromisso
assumido); a mudança de Status é o próprio ciclo de vida do compromisso,
não uma nova vigência.*

  ----------------------------- --------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**             **Descrição / regra**

  **ID_Compromisso**            *identificador*             ---

  **ID_Orcamento_Item**         *referência                 A regra do orçamento (conta + chaves
                                (Cad_Orcamento_Item)*       analíticas) que este compromisso
                                                            consome.

  **ID_Periodo_Referencia**     *referência                 O mês em que o compromisso foi assumido
                                (Cad_Periodo_Fechamento,    --- usado junto do Balizador do item
                                Fase 0,                     para decidir se o saldo disponível a
                                bloco=\"contabilidade\")*   checar é só deste mês ou acumulado do
                                                            exercício até aqui. Corrigido na revisão
                                                            6 --- o nome aposentado
                                                            Cad_Periodo_Contabil ainda aparecia
                                                            aqui.

  **Origem_Tipo**               *texto*                     O tipo da transação de origem.
                                                            Desmembrado na revisão 7.

  **ID_Origem**                 *referência genérica*       A transação de origem (ex.: item de
                                                            pedido de compra, fora do escopo deste
                                                            documento até o módulo de Compras ser
                                                            especificado) --- mesmo padrão de
                                                            referência genérica já usado em
                                                            Mov_Aprovacao_Instancia.ID_Origem (Fase
                                                            0).

  **Valor_Comprometido**        *número*                    ---

  **Quantidade_Comprometida**   *número, opcional*          Simétrico a Quantidade_Orcada --- ex.:
                                                            uma contratação aprovada consome 1 vaga
                                                            contra o Quantidade_Orcada daquele
                                                            centro de custo/mês.

  **Status**                    *enumeração {aberto,        \"baixado\" quando a origem vira
                                baixado, cancelado}*        lançamento contábil (o valor passa a
                                                            contar como realizado, não mais como
                                                            comprometido); \"cancelado\" quando a
                                                            origem é cancelada antes de virar
                                                            lançamento.
  ----------------------------- --------------------------- ----------------------------------------

5\. Desvio Orçamentário e a Régua de Aprovação

O saldo disponível de um item de orçamento, num determinado mês, depende
do Balizador definido em Cad_Orcamento_Item: se \"mensal\", é só o
Valor_Orcado (e Quantidade_Orcada) daquele mês em
Cad_Orcamento_Item_Mes, menos o comprometido+realizado daquele mesmo mês
--- o que sobra não passa para o mês seguinte. Se \"periodo\", é a soma
do Valor_Orcado (e Quantidade_Orcada) de todos os meses do exercício até
o mês corrente, menos o comprometido+realizado acumulado no mesmo
intervalo --- o que sobra continua disponível nos meses seguintes, mesmo
que o gasto real tenha sido antecipado ou postergado em relação ao mês
originalmente orçado.

Um desvio nesse saldo dispara uma instância de aprovação ---
reaproveitando a régua de aprovação inteira do Fase 0
(Cad_Regua_Aprovacao, Cad_Regua_Faixa, Cad_Regua_Aprovador,
Cad_Usuario_Escopo), sem nenhuma estrutura nova: o Fase 0 já previu esse
gatilho explicitamente (Mov_Aprovacao_Instancia.Origem_Tipo =
desvio_orcamento) e o próprio ID_Valor_Dimensao_Origem da instância já
existe para casar o desvio com o aprovador responsável por aquele centro
de custo.

A aprovação do PRÓPRIO orçamento (elaboração ou revisão), antes de
qualquer execução, usa um gatilho distinto:
Mov_Aprovacao_Instancia.Origem_Tipo = aprovacao_orcamento --- uma
pequena extensão pontual que incorporei ao dicionário Fase 0 (agora
revisão 8). A instância resultante fica referenciada em
Cad_Orcamento.ID_Instancia_Aprovacao, de onde se chega a quem aprovou
(Mov_Aprovacao_Decisao.ID_Participante_Aprovador).

6\. Como este módulo se conecta com a Fase 0

Referência rápida do que este módulo consome do dicionário Fase 0 ---
nunca redescrito aqui, só referenciado por chave estrangeira.

  -------------------------------------- ------------------------------------- --------------------------
  **Entidade da Fase 0**                 **Como este módulo usa**              **Observação**

  **Cad_Empresa / Cad_Filial**           Dono do orçamento                     *---*
                                         (Cad_Orcamento.ID_Empresa /           
                                         ID_Filial).                           

  **Cad_Conta_Contabil**                 Cada item orçado aponta para uma      *---*
                                         conta; a Natureza da conta já filtra  
                                         receita/despesa/custo/ativo.          

  **Cad_Dimensao_Contabil /              Orçamento por Centro de Custo,        *Mesmo padrão N:N de
  Cad_Dimensao_Contabil_Valor**          Planta, Região ou outra dimensão      Mov_Lancamento_Dimensao*
                                         configurada --- chave composta via    
                                         Cad_Orcamento_Item_Dimensao.          

  **Cad_Produto_Servico /                Quebra do orçamento de receita por    *---*
  Cad_Produto_Servico_Dimensao_Valor**   produto específico ou por             
                                         família/classe/marca.                 

  **Cad_Participante /                   Quebra do orçamento de receita por    *---*
  Cad_Grupo_Economico**                  cliente específico ou por grupo de    
                                         clientes.                             

  **Cad_Periodo_Fechamento               Mês orçado (Cad_Orcamento_Item_Mes),  *Sempre calendário, mesmo
  (bloco=\"contabilidade\")**            para comparar com o mês realizado.    quando o Exercício não é*
                                         Corrigido na revisão 6 --- esta linha 
                                         citava o nome aposentado              
                                         Cad_Periodo_Contabil, sem acompanhar  
                                         a generalização da Fase 0 revisão 37. 

  **Cad_Regua_Aprovacao (+               Aprova tanto o orçamento em si quanto *Reaproveitada sem mudança
  Faixa/Aprovador/Escopo)**              o desvio durante a execução.          estrutural*

  **Mov_Aprovacao_Instancia**            Origem_Tipo ganhou                    *Extensão já incorporada
                                         aprovacao_orcamento na revisão 7 do   ao Fase 0*
                                         Fase 0, além do já existente          
                                         desvio_orcamento.                     

  **Mov_Lancamento**                     Fonte do valor realizado, para        *---*
                                         comparar contra o orçado.             

  **Cad_Usuario / Cad_Perfil /           Quem edita/aprova cada orçamento é,   *Novo motor transversal
  Cad_Permissao**                        em última instância, controlado pelo  --- ainda sem detalhamento
                                         motor de usuários e permissões do     fino de tela por módulo*
                                         Fase 0 (revisão 8).                   
  -------------------------------------- ------------------------------------- --------------------------

7\. Notas para a sua revisão

Mesma lógica da Fase 0: estas são decisões técnicas que assumi por conta
própria para fechar uma estrutura concreta --- nenhuma está travada.

-   Orçamento cobre operacional (receita/despesa/custo) e investimento
    (ativo) igualmente, sem distinção estrutural --- a distinção vem só
    da Natureza da conta referenciada, não de um campo Tipo_Orcamento
    separado.

-   Revisão orçamentária sempre gera uma versão NOVA inteira
    (Cad_Orcamento) --- não modelei revisão parcial (só alguns itens
    revisados, resto copiado) como uma operação distinta; replicar os
    itens não revisados na nova versão resolve isso na prática, mas pode
    ser incômodo operacionalmente. Fica como ponto de atenção.

-   Mov_Compromisso_Orcamentario assume que a origem do compromisso
    (ex.: pedido de compra) sabe se referenciar a uma linha específica
    do orçamento (Cad_Orcamento_Item) --- como o módulo de Compras ainda
    não foi especificado, esse vínculo é uma suposição a confirmar
    quando Compras for detalhado.

-   Cad_Exercicio_Orcamentario é cadastro novo deste módulo, sem
    equivalente no Fase 0 --- cobre o exercício gerencial customizável
    (não necessariamente calendário), mantendo Cad_Periodo_Fechamento
    (Fase 0, bloco=\"contabilidade\", sempre calendário --- corrigido na
    revisão 6, citava aqui o nome aposentado Cad_Periodo_Contabil) como
    a referência para comparar com o realizado e para o SPED Contábil.

-   Balizador (mensal/periodo) é regra da VERSÃO do orçamento
    (Cad_Orcamento_Item), não característica fixa da conta --- a mesma
    conta pode ter Balizador diferente em orçamentos de exercícios
    diferentes.

-   Cad_Orcamento_Chave nasceu porque as quebras analíticas variam de
    empresa para empresa --- nem toda empresa quer orçar por
    produto/cliente/dimensão, algumas orçam só por conta. Em vez de
    deixar as quatro chaves de Cad_Orcamento_Item soltas e opcionais sem
    controle, o usuário define no início da elaboração da versão quais
    chaves valem, e o preenchimento dos itens fica travado nisso ---
    evita inconsistência entre linhas do mesmo orçamento (algumas com
    cliente preenchido, outras sem, por descuido).

-   Cad_Orcamento_Item_Desembolso cobre o efeito caixa do orçamento
    (seção 3), em paralelo ao orçamento por competência já modelado ---
    sem Balizador próprio nesta versão, já que o conceito de
    mensal/período é de competência; fica como ponto de atenção se fizer
    sentido um controle de teto também sobre o caixa projetado.

-   Descricao_Resumida/Descricao_Detalhada em Cad_Orcamento dão contexto
    textual do que mudou de uma versão para outra, além do Status/Versao
    numéricos --- não substituem nenhum campo existente, são aditivos.

-   Não modelei Capex plurianual de projeto nem integração com
    planejamento estratégico de longo prazo --- fica para quando o
    módulo de Gestão de Contratos/Projetos for especificado, se fizer
    sentido estender aqui.

-   Revisão 4: o bloco planejamento_orcamento passou a descrever, no
    próprio texto (seção 2), o comportamento do mecanismo transversal de
    fechamento de período (Fase 0, seção 10) --- decisão de Alberto de
    que aqui o fechamento protege só o passado (Cad_Orcamento_Item_Mes
    de competência já fechada), sem travar o módulo inteiro como os
    demais blocos de Fase 1/2/5/6.

-   Revisão 5 --- RESOLVIDO o ponto em aberto da revisão 4 (qual Filial
    usar na checagem quando o orçamento é consolidado): Alberto
    confirmou que este orçamento é sempre consolidado na matriz, com o
    consumo somando as filiais --- a checagem de fechamento passa a ser
    feita no nível Empresa (Cad_Periodo_Fechamento, Fase 0) quando
    Cad_Orcamento.ID_Filial estiver vazio, sem cascatear para
    Cad_Periodo_Fechamento_Filial; só cascateia normalmente se um dia
    existir um Cad_Orcamento específico de uma filial (ID_Filial
    preenchido) --- caso hoje não usado na prática, mas que a estrutura
    continua suportando. Nenhum campo novo --- é só a regra de qual
    nível da Fase 0 se consulta, documentada na seção 2.

-   Revisão 7 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): origem do compromisso orçamentário
    desmembrada; chave primária de Cad_Orcamento_Item_Dimensao. A
    convenção completa (vigência, identidade + versão, sucessão de
    códigos oficiais, competência, CNPJ alfanumérico, um campo por
    informação, saldos guardados de período fechado, sequência de
    fechamento) vive na Fase 0, seções 2 e 10 (revisão 41).

-   Revisão 8 --- referência a Cad_Regua_Aprovador_Escopo trocada por
    Cad_Usuario_Escopo (Fase 0, seção 13), que a substitui.

8\. Próximo passo

Depois de revisado este módulo, o próximo da Fase 1 é Compras ---
pedido, fornecedor, Destinação por linha (Cad_Destinacao, Fase 0), e o
esquema de nota fiscal via Motor de Regras --- já podendo referenciar
Cad_Orcamento_Item para o vínculo do compromisso orçamentário definido
aqui.

Revisão 4, registrada aqui: Planejamento & Orçamento passou a descrever,
no próprio texto (seção 2), o comportamento do mecanismo transversal de
fechamento de período (Fase 0, seção 10) para o seu bloco ---
planejamento_orcamento ---, atendendo ao convite deixado na revisão 13
do módulo de Compras para que cada módulo já entregue fizesse o mesmo.
Ao contrário de Compras e dos demais módulos de Fase 1/2/5/6, aqui o
fechamento não trava o módulo inteiro: protege só a competência já
fechada de Cad_Orcamento_Item_Mes, deixando o restante do orçamento ---
inclusive novas versões e meses futuros --- livre para elaboração e
revisão normal. Comportamento intencional e específico da natureza deste
módulo (planejamento prospectivo, não execução transacional), confirmado
por Alberto.

Revisão 5, registrada aqui: fechado o único ponto que a revisão 4 tinha
deixado em aberto --- o nível de checagem quando o orçamento é
consolidado. Confirmado por Alberto: este orçamento é sempre feito
consolidado na matriz, com o consumo somando as filiais depois; a
checagem de fechamento passou a consultar Cad_Periodo_Fechamento no
nível Empresa nesse modo, sem cascatear para filial nenhuma.

Revisão 6, decorrente da revisão geral de módulos pedida por Alberto:
sete referências ao nome aposentado Cad_Periodo_Contabil (Introdução,
Cad_Exercicio_Orcamentario, os três ID_Periodo_Referencia de
Cad_Orcamento_Item_Mes/Cad_Orcamento_Item_Desembolso/Mov_Compromisso_Orcamentario,
a tabela de conexões e as Notas) nunca tinham acompanhado a
generalização da Fase 0 revisão 37 (Cad_Periodo_Contabil →
Cad_Periodo_Fechamento) --- corrigidas todas para Cad_Periodo_Fechamento
(bloco=\"contabilidade\"), sem nenhuma mudança de comportamento: o bloco
\"planejamento_orcamento\" em si já consultava o mecanismo certo desde a
revisão 4, só o NOME citado nestas referências estava desatualizado.
Nenhum outro ponto pendente neste módulo no momento.

*Revisão 7 --- Bloco 1 da validação geral consolidado junto com a Fase 0
(revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*
