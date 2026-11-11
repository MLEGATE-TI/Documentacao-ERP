**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 1 · MÓDULO 4**

**CRM & Vendas**

*Cotação de venda, tabela de preço/comissão/royalty via Motor de Regras,
pedido de venda com histórico de status por item, reserva de estoque,
nota fiscal de saída e devolução de cliente*

*Revisão 22 --- consolidação da revisão 31 do dicionário (documentos 150, 157, 170 e 173, com as respostas de Alberto de 04/11/2026): 3 entidades existentes alteradas; data do fato gerador no item da nota de saída, gorjeta, fornecimento sob contrato e tipo de serviço da agência (documento 150) e ligação da devolução de venda ao ajuste da operação (documento 157).*

*Revisão 21 --- consolidação da revisão 30 do dicionário (documentos 156, 161, 164 e 168 e a Q138-3, com as respostas de Alberto de 03/11/2026): 2 entidades existentes alteradas; Escriturada_Como_Entrada na nota de saída (documento 168, G2), Valor_Desconto_Condicional_Item no item e a taxa de câmbio da base (documento 156).*

*Revisão 20 --- consolidação da revisão 29 do dicionário (documentos 138, 140, 152, 153, 155, 162, 163 e 165, com as respostas de Alberto de 29/10/2026 e de 03/11/2026): 1 entidades existentes alteradas; ID_Atividade_Simples no item da nota de saída (documento 163, Q163-2).*

*Revisão 19 --- consolidação da revisão 28 do dicionário (documentos 127, 152 e 153, com as respostas de Alberto de 29/10/2026): 2 entidades existentes alteradas; ID_Atividade_Presuncao no item da nota de saída e ID_Natureza_Operacao_Cambial_Royalty no item do pedido (documentos 127 e 152).*

*Revisão 18 --- consolidação da revisão 19 do dicionário (documento 90 aprovado por Alberto em 21/10/2026 e decisões do documento 91 respondidas): 1 entidades existentes alteradas; cinco campos de onerosidade e de opção de doação no item da nota de saída (D-N285 a D-N287, documento 90).*

*Revisão 17 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 2 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 16 --- Achado R-7 da revisão final cruzada (documento 30,
04/10/2026), construída junto com a revisão 50 da Fase 0:
Mov_Cotacao_Venda.ID_Solicitante passa a ser declarado como referência
genérica, conforme Tipo_Solicitante (Cad_Participante ou
Cad_Pre_Cadastro), o padrão que o texto já citava; sem mudança de
estrutura.*

*Revisão 15 --- Correções de nomenclatura da auditoria de 04/10/2026
(documento 29), construída junto com a revisão 49 da Fase 0:
Papel_Comissionado passa a ID_Papel_Comissionado em
Mov_Cotacao_Venda_Item_Comissao e Mov_Pedido_Venda_Item_Comissao
(referência a Cad_Classe_Sistema leva o prefixo ID_, Fase 0, seção 2).
Nenhuma entidade nova.*

*Revisão 14 --- ajuste pelo Bloco 4 (Fase 0, revisão 46; Contabilidade &
Fiscal, revisão 18): Serie de Mov_Nota_Fiscal_Saida passa de 3 para 5
posições, como pede a EFD-Reinf; Mov_Nota_Fiscal_Saida_Item ganha
Tipo_Comercializacao_Rural, que alimenta o R-2050. A nota de saída é a
origem dos fatos do R-2020 (serviço prestado com retenção de INSS) e do
R-2050 (comercialização da produção).*

*Revisão 13 --- ajuste de texto pelo Bloco 3 (Fase 0, revisão 45):
referência a Cad_Regua_Aprovador_Escopo trocada por Cad_Usuario_Escopo
(Fase 0, seção 13), que a substitui.*

*Revisão 12 --- construída junto com a revisão 43 da Fase 0 (Bloco 2,
fiscal): campos fiscais do cabeçalho e do item da nota de saída (os
mesmos de Compras: modelo e situação do documento, finalidade, natureza
da operação, consumidor final, presença, protocolo, modalidade de frete,
rateios por item, origem da mercadoria, CEST, Ex da TIPI, GTIN, cBenef e
cTribNac), local da operação por linha do pedido de venda e da nota,
habilitação REIDI/REPES do cliente no item do pedido de venda e da nota
de saída, e o empreendimento imobiliário no item da nota de saída.*

*Revisão 11 --- construída junto com a revisão 42 da Fase 0: tipo lógico
\"código (n)\" definido por Alberto --- todo campo que identifica algo
(inscrição, documento, agência, conta, número e série de nota,
matrícula, código oficial) é caractere, nunca numérico: os zeros à
esquerda fazem parte do código, e o padrão pode passar a aceitar letras
ou mudar de tamanho, como aconteceu com o CNPJ alfanumérico. Campos
revistos: Chave_Acesso, Chave_Acesso_Devolucao,
Codigo_Servico_Municipal, Numero, Numero_Nota_Devolucao,
Numero_Processo_Suframa, Serie, Serie_Nota_Devolucao. O NCM do item da
nota passa a apontar para Cad_Classificacao_Mercadoria (NCM harmonizado,
Fase 0).*

*Revisão 10 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; número e série desmembrados na nota fiscal de
saída e na devolução; chave de acesso de 44 caracteres (CNPJ
alfanumérico).*

*Revisão 9 --- patch pontual pedido pela consolidação de Contas a
Pagar/Receber: fechadas duas referências cruzadas que ficavam como
gancho --- reversão de provisão de comissão/royalty (seção 9), hoje
coberta proporcionalmente por aquele módulo; e valor da nota fiscal de
saída vs. valor do título quando há retenção/split payment (seção 7).
Nenhuma estrutura nova, só as referências que faltavam*

*Revisão 8 --- nova seção transversal de fechamento de período (Fase 0,
seção 10, revisão 37): o bloco \"vendas\" trava toda criação/alteração
de Mov_Nota_Fiscal_Saida datada numa competência fechada para a Filial
correspondente --- comportamento de aplicação junto da entidade (seção
7), sem campo novo. Única exceção de todo o redesenho, confirmada por
Alberto: criar Mov_Pedido_Venda e a cotação de origem (seção 2 e 5)
continua liberado mesmo com o bloco fechado, porque sem atendimento
ainda não afeta fiscal nem valor da empresa --- alterar um pedido já
existente de forma que mude o que seria faturado/entregue segue a mesma
trava do faturamento. Sem validação de pendência neste bloco (exclusiva
de Compras)*

*Revisão 7 --- Mov_Nota_Fiscal_Saida_Item ganha ID_Ordem_Servico_Item,
para faturar assistência técnica sobre máquina própria vendida, patch
pedido pela especificação da Fase 1 Produção*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o módulo de CRM & Vendas, no mesmo formato
usado nos três módulos já entregues da Fase 1 (Planejamento & Orçamento,
Compras, Estoque): função e dados juntos, entidade por entidade, sempre
referenciando os motores transversais da Fase 0 (Cad_Participante,
Cad_Pre_Cadastro, Cad_Motor_Regra, Cad_Regua_Aprovacao,
Cad_Grupo_Economico, Cad_CFOP, Cad_ClassTrib) e os módulos já
especificados (Cad_Produto_Servico, Cad_Destinacao da Fase 0;
Cad_Local_Estoque e a movimentação real de Estoque) em vez de
redefini-los.

Nota de transparência sobre a ordem de especificação: o Documento
Analítico original posiciona CRM & Vendas na Fase 4 do plano de
desenvolvimento, dependente da maturidade de Produção e do módulo
Financeiro (Fases 2 e 3) --- não como o quarto módulo a seguir depois de
Planejamento & Orçamento, Compras e Estoque. Ao encerrar a especificação
de Estoque, sugeri CRM & Vendas como suposição minha, sem confirmação;
ao revisar o Documento Analítico contra essa sugestão, identifiquei a
divergência e perguntei explicitamente a Alberto qual módulo especificar
a seguir, apresentando Contas a Pagar/Receber como a opção alinhada ao
plano original. Alberto optou deliberadamente por CRM & Vendas mesmo
assim. Por continuidade de numeração com os três documentos já entregues
desta mesma leva, este documento leva o rótulo \"Fase 1 · Módulo 4\" ---
é só rótulo de sequência de entrega, não uma reclassificação do módulo
dentro do plano geral, que continua sendo Fase 4.

Consequência direta dessa antecipação: como Contas a Pagar/Receber (Fase
2) e Produção (Fase 3) ainda não existem, este módulo simplifica ou
apenas cria o gancho conceitual para tudo que dependeria deles. Na
revisão 2, dois desses pontos ganharam mais substância, a pedido de
Alberto, depois da entrega da Revisão 1: a condição de pagamento passou
a ter parcelamento real, com valor e data sempre explícitos (seção 2 e
5); e a comissão/royalty estimados passaram a gerar provisão contábil no
nascimento do pedido, além de uma leitura de estimativa pensada para uma
futura Tesouraria (seção 9). Na revisão 3, a escada de comissão passou a
ser gerada automaticamente por uma hierarquia comercial aberta (seção 3
e 9), e o frete ganhou três conceitos separados --- referência de custo,
modalidade de cobrança/valor negociado e valor definitivo na nota fiscal
(seção 2, 5, 7 e 9) ---, junto com a correção de que a transportadora
real é decisão da Expedição/Compras, não de CRM & Vendas. Ainda assim, o
registro financeiro efetivo --- a baixa real de uma parcela como
recebida, a reversão da provisão em obrigação a pagar, o repasse de
comissão/royalty, o custo real pago à transportadora --- continua
dependendo de Contas a Pagar/Receber propriamente dito, que ainda não
foi especificado. Crédito do cliente consolidado (seção 10) e o cálculo
de prazo de entrega por capacidade de Produção continuam só como gancho.
Expedição e Portal do Cliente, módulos irmãos de CRM & Vendas na própria
Fase 4 do plano original, também ficam fora desta revisão --- mas a
entrega programada (seção 2 e 5) já entrega a esses dois módulos futuros
o dado de que vão precisar (data, quantidade, modalidade,
endereço/local, transportadora de referência), só o processo operacional
em si, a transportadora real e o código de rastreio é que não foram
modelados. Na revisão 4, o Portal do Cliente ganhou um primeiro
comportamento concreto do lado de CRM & Vendas: autoatendimento (seção
2, 4 e 9), com lista de preço fixa via Motor de Regras e checagem de
estoque, e uma fila única de cotações para quando o cliente não tem
vendedor principal definido --- todo cliente passou a poder ter um
vendedor principal e um suplente (Fase 0, revisão 15), e a comissão pode
agora variar por canal de origem (atendimento por vendedor vs.
autoatendimento).

Fica FORA desta revisão, por decisão de escopo: o pagamento ou repasse
financeiro EFETIVO de comissão e de royalty ao licenciante (aqui
comissão e royalty são só estimados e provisionados contabilmente --- o
repasse em si depende de Contas a Pagar, ou de Folha & RH quando o
beneficiário tiver vínculo empregatício); o registro financeiro de
contas a receber propriamente dito (a parcela real já é modelada ---
seção 2 e 5 ---, mas a liquidação/baixa em si depende de Contas a
Pagar/Receber); e o processo físico de separação/romaneio/embarque
(Expedição) --- este módulo já sinaliza a previsão de saída programada e
a transportadora responsável (seção 2, 5 e 9), mas não modela o processo
operacional de separação em si. Venda avulsa/balcão e condição de
pagamento com parcelamento real, que na Revisão 1 estavam fora do
escopo, foram incorporadas na revisão 4 a pedido de Alberto (ver seção
2, 5 e 7).

Esta Revisão 5 é um patch pedido pela consolidação (Revisão 3) do módulo
Fase 2 Tesouraria, hoje já especificado: o crédito do cliente (seção
10), que desde a Revisão 1 era só um gancho conceitual, ganha estrutura
real, e os dois gatilhos de bloqueio de Contas a Pagar/Receber e
Tesouraria --- desvio de crédito (exposição × teto) e régua de cobrança
(dias de atraso) --- passam a estar de fato integrados dentro de
Mov_Cotacao_Venda (seção 2 e 4), sempre no nível de grupo econômico, com
tratamento diferente conforme o canal de origem da cotação seja
atendimento por vendedor ou autoatendimento (seção 2, 4 e 9).

2\. Cotação de Venda

Mesma lógica de pré-cadastro já usada em Compras, espelhada: nem todo
prospect cotado vira, de fato, cliente. A cotação de venda reaproveita o
mesmo mecanismo de Cad_Pre_Cadastro/Mov_Pre_Cadastro_Conversao do Fase 0
--- cotar para alguém que ainda não é Cad_Participante não obriga
cadastrá-lo por completo; só quando a cotação é aceita é que a conversão
(quando aplicável) acontece, e é exatamente nesse instante que o pedido
de venda nasce, já confirmado (ver seção 5). Diferente de Compras ---
onde vários fornecedores propõem para um único pedido nosso ---, aqui é
a Mlegate (ou seu cliente, o tenant) quem propõe, a um único solicitante
por cotação.

Fila de cotações, adicionada nesta revisão (4), pedida por Alberto: o
cliente pode registrar um pedido de cotação diretamente no sistema; se
ele não tiver um vendedor principal definido
(Cad_Participante.ID_Participante_Vendedor_Principal, Fase 0 revisão
15), a cotação nasce SEM vendedor e cai numa fila única de solicitações
--- \"a fila é uma só, até para ver se tem algo parado e ninguém tomou
uma ação\" --- de onde qualquer vendedor pode pegar. Quando o cliente já
tem vendedor principal, a cotação nasce direto atribuída a ele (o
suplente, Cad_Participante.ID_Participante_Vendedor_Suplente, pode
assumir a qualquer momento, sem depender de nenhum evento formal de
indisponibilidade). \"Estar na fila\" não é um Status próprio --- é só
ID_Participante_Vendedor vazio com Status=aberta, mesma filosofia de
nunca duplicar em campo derivável o que já é visível pela combinação de
outros campos.

Mov_Cotacao_Venda

O cabeçalho de uma cotação de venda --- dirigida a um cliente já
cadastrado ou a um prospect ainda em pré-cadastro.

*Vigência: não --- é o registro de um evento (a cotação); Status é o
próprio ciclo de vida, não uma nova vigência.*

  ----------------------------------- -------------------------- -----------------------------------------------------
  **Campo**                           **Tipo lógico**            **Descrição / regra**

  **ID_Cotacao**                      *identificador*            ---

  **ID_Filial**                       *referência (Cad_Filial)*  A filial vendedora.

  **Tipo_Solicitante**                *enumeração {participante, Diz qual cadastro ID_Solicitante referencia --- mesmo
                                      pre_cadastro}*             padrão de referência genérica já usado em
                                                                 Mov_Cotacao_Proposta.Tipo_Proponente/ID_Proponente
                                                                 (Compras), aqui espelhado: lá o proponente cotado era
                                                                 quem nos vendia; aqui o solicitante cotado é para
                                                                 quem vendemos.

  **ID_Solicitante**                  *referência genérica,      ---
                                      conforme Tipo_Solicitante  
                                      (Cad_Participante ou       
                                      Cad_Pre_Cadastro)*         

  **ID_Participante_Vendedor**        *referência                Passou a ser opcional nesta revisão (4) --- vazio
                                      (Cad_Participante,         significa que a cotação está na fila única de
                                      opcional)*                 solicitações, ainda sem vendedor (ver acima). Herdado
                                                                 automaticamente de
                                                                 Cad_Participante.ID_Participante_Vendedor_Principal
                                                                 do cliente quando existir; quando um vendedor pega
                                                                 uma cotação da fila, este campo é preenchido no mesmo
                                                                 momento em que Data_Hora_Atribuicao_Vendedor (abaixo)
                                                                 é registrado.

  **Data_Hora_Atribuicao_Vendedor**   *data/hora, opcional*      Adicionado nesta revisão (4), pedido por Alberto: \"o
                                                                 vendedor pegou um pedido da fila, tem que registrar
                                                                 quem pegou, data e hora\" --- preenchido no momento
                                                                 em que um vendedor pega a cotação da fila. Vazio
                                                                 quando o vendedor já nasce atribuído (cliente com
                                                                 vendedor principal, ou cotação criada diretamente por
                                                                 um vendedor) --- o registro só existe para o evento
                                                                 de retirada da fila.

  **Canal_Origem**                    *enumeração                Adicionado nesta revisão (4), pedido por Alberto:
                                      {atendimento_vendedor,     marca se a cotação nasceu de atendimento por um
                                      autoatendimento}*          vendedor ou de autoatendimento pelo Portal do Cliente
                                                                 (seção 3 e 9) --- mantido mesmo depois que um
                                                                 vendedor é atribuído/assume a cotação, porque pode
                                                                 haver regras de comissão distintas entre os dois
                                                                 canais (\"podemos ter regras destintas de comissões
                                                                 para um atendimento, ou autoatendimento\").

  **Data_Cotacao**                    *data*                     ---

  **Data_Validade**                   *data*                     Prazo de validade da proposta --- depois dela, a
                                                                 cotação passa a Status=expirada se ainda não tiver
                                                                 sido aceita ou recusada.

  **Status**                          *enumeração {aberta,       \"em_aprovacao\" ocorre por até três gatilhos
                                      em_aprovacao, aceita,      independentes (seção 4): desconto além da alçada do
                                      recusada, expirada,        vendedor (nunca no autoatendimento, que usa lista de
                                      cancelada}*                preço fixa); desvio de crédito (exposição × teto,
                                                                 Contas a Pagar/Receber); e bloqueio pela régua de
                                                                 cobrança (dias de atraso, Tesouraria) --- estes dois
                                                                 últimos, adicionados nesta revisão (5), podem ocorrer
                                                                 em QUALQUER canal, inclusive autoatendimento.
                                                                 \"aceita\" é o gatilho que faz nascer o
                                                                 Mov_Pedido_Venda (seção 5) --- não existe um estado
                                                                 intermediário entre cotação aceita e pedido
                                                                 confirmado.

  **ID_Condicao_Pagamento**           *referência                Adicionado nesta revisão, pedido por Alberto ---
                                      (Cad_Condicao_Pagamento,   igual a Compras: só uma SUGESTÃO de parcelamento
                                      Fase 0, opcional)*         (ex.: \"5 vezes\"), usada para pré-popular
                                                                 Mov_Cotacao_Venda_Parcela, abaixo. O vendedor/cliente
                                                                 pode mudar valores e datas livremente depois,
                                                                 conforme negociação --- nunca uma obrigação de seguir
                                                                 a sugestão.
  ----------------------------------- -------------------------- -----------------------------------------------------

Mov_Cotacao_Venda_Parcela

Adicionado nesta revisão, pedido por Alberto: \"o % de pagamento tem que
ser uma referência, mas sempre temos que ter o valor de pagamento\" ---
o parcelamento REAL desta cotação. Pode nascer pré-populado a partir de
Cad_Condicao_Pagamento_Parcela (Fase 0) quando ID_Condicao_Pagamento
estiver preenchido (ex.: dividir o valor total em 5 e sugerir uma
parcela a cada mês), mas o percentual do template é só o ponto de
partida: o valor e a data de cada parcela aqui são sempre campos
explícitos, editáveis pelo vendedor a qualquer momento antes da
aceitação da cotação, nunca recalculados a partir do percentual
sugerido.

*Vigência: não --- vigência não se aplica; alterações antes da aceitação
sobrescrevem o próprio registro, sem histórico de renegociação nesta v1
(mesmo tratamento dado a Mov_Pedido_Parcela em Compras).*

  ------------------------------ ---------------------- --------------------------------------------
  **Campo**                      **Tipo lógico**        **Descrição / regra**

  **ID_Parcela**                 *identificador*        ---

  **ID_Cotacao**                 *referência            ---
                                 (Mov_Cotacao_Venda)*   

  **Numero_Parcela**             *número*               1, 2, 3\... --- a ordem da parcela dentro da
                                                        cotação.

  **Valor_Parcela**              *número*               O valor real desta parcela --- explícito,
                                                        nunca derivado de
                                                        Cad_Condicao_Pagamento_Parcela.Percentual,
                                                        que é só a sugestão inicial.

  **Data_Vencimento_Estimada**   *data*                 A data estimada de vencimento, negociada com
                                                        o cliente --- vira Data_Vencimento
                                                        definitiva em Mov_Pedido_Venda_Parcela
                                                        (seção 5) quando a cotação é aceita, podendo
                                                        ainda ser renegociada depois disso.
  ------------------------------ ---------------------- --------------------------------------------

Mov_Cotacao_Venda_Item

Uma linha da cotação --- o produto/serviço, a quantidade, o valor de
tabela sugerido pelo Motor de Regras e o valor efetivamente proposto.

*Vigência: não.*

  --------------------------------- ------------------------ ----------------------------------------
  **Campo**                         **Tipo lógico**          **Descrição / regra**

  **ID_Item_Cotacao**               *identificador*          ---

  **ID_Cotacao**                    *referência              ---
                                    (Mov_Cotacao_Venda)*     

  **ID_Produto_Servico**            *referência              ---
                                    (Cad_Produto_Servico)*   

  **Quantidade**                    *número*                 ---

  **Valor_Unitario_Tabela**         *número*                 Sugerido pelo Motor de Regras a partir
                                                             da tabela de preço (seção 3) --- ponto
                                                             de partida, não obrigatório de ser
                                                             seguido à risca.

  **Valor_Unitario_Proposto**       *número*                 O valor efetivamente oferecido ao
                                                             solicitante --- pode ser igual, menor
                                                             (desconto) ou, em tese, maior que o de
                                                             tabela. É este valor, não o de tabela,
                                                             que vira
                                                             Mov_Pedido_Venda_Item.Valor_Unitario
                                                             quando a cotação é aceita (fidelidade ao
                                                             valor acordado).

  **Percentual_Desconto**           *número, opcional*       Derivado de Valor_Unitario_Tabela e
                                                             Valor_Unitario_Proposto --- não é a
                                                             fonte do valor (que continua sendo
                                                             Valor_Unitario_Proposto), é o que a
                                                             régua de aprovação (seção 4) compara
                                                             contra a alçada do vendedor.

  **Percentual_Royalty_Estimado**   *número, opcional*       Adicionado nesta revisão --- lacuna da
                                                             Revisão 1 apontada por Alberto (\"lembra
                                                             que também posso ter royalties\"):
                                                             resultado do Motor de Regras (seção 3,
                                                             Tipo_Resultado=percentual_royalty)
                                                             quando o produto é licenciado. É sempre
                                                             uma ESTIMATIVA (seção 9), nunca uma
                                                             obrigação: o valor real de royalty a
                                                             repassar só se confirma no recebimento
                                                             efetivo do cliente.
  --------------------------------- ------------------------ ----------------------------------------

Comissão, aqui, deixou de ser um único percentual do item --- Alberto
apontou que \"posso ter comissões que não é só do vendedor, posso ter do
supervisor, gerente, a comissão pode ter uma escada\". Por isso o
percentual/valor TOTAL de comissão de um item nunca é um campo
armazenado --- é sempre a soma das linhas de
Mov_Cotacao_Venda_Item_Comissao (abaixo) para aquele item, mesma
filosofia de saldo/status nunca armazenado, sempre derivado, já usada em
todo este dicionário (Fase 0 --- Mov_Lancamento; Estoque --- saldo;
seção 5, abaixo --- status do pedido).

Mov_Cotacao_Venda_Item_Comissao

Adicionado na Revisão 1: uma linha de comissão estimada para este item,
por beneficiário/nível --- a escada de comissão. Desde a Revisão 3, a
escada não é mais um conjunto solto de papéis: é gerada automaticamente
a partir da hierarquia comercial do vendedor
(Cad_Participante_Historico_Hierarquia_Comercial, Fase 0 revisão 14) ---
uma linha para o próprio vendedor e uma para cada superior na cadeia,
subindo até não haver mais superior cadastrado, sem limite fixo de
níveis (Alberto: \"pode ter 1 nível, quantos forem necessários\"). Cada
nível tem seu próprio percentual, resolvido separadamente pelo Motor de
Regras (seção 3).

*Vigência: não.*

  ---------------------------------- --------------------------- ----------------------------------------
  **Campo**                          **Tipo lógico**             **Descrição / regra**

  **ID_Item_Comissao**               *identificador*             ---

  **ID_Item_Cotacao**                *referência                 ---
                                     (Mov_Cotacao_Venda_Item)*   

  **ID_Participante_Beneficiario**   *referência                 Quem recebe esta linha de comissão --- o
                                     (Cad_Participante)*         vendedor que executou a venda, ou um de
                                                                 seus superiores na hierarquia comercial;
                                                                 participante, classe funcionário, mesmo
                                                                 cadastro único do Fase 0.

  **ID_Papel_Comissionado**          *referência                 O cargo deste beneficiário nesta linha
                                     (Cad_Classe_Sistema,        da escada. Deixou de ser enumeração fixa
                                     domínio cargo_comercial --- nesta revisão (3): domínio aberto,
                                     Fase 0, revisão 14)*        porque a hierarquia comercial da Mlegate
                                                                 não tem profundidade fixa. Regra
                                                                 importante, pedida por Alberto: a linha
                                                                 do próprio vendedor sempre usa o
                                                                 cargo-base \"vendedor\" do domínio,
                                                                 mesmo que o cargo cadastrado dele seja
                                                                 outro (\"no caso do superintendente ou
                                                                 gerente vender diretamente ele leva o
                                                                 percentual como se fosse vendedor\") ---
                                                                 as linhas seguintes, dos superiores,
                                                                 usam o cargo real de cada um.

  **Percentual_Comissao_Estimado**   *número*                    Resultado do Motor de Regras (seção 3)
                                                                 para este beneficiário/papel --- já
                                                                 considerando a redução proporcional
                                                                 causada por desconto, quando aplicável.
                                                                 É uma estimativa (seção 9): o direito e
                                                                 o valor reais só se confirmam no
                                                                 recebimento efetivo do cliente.
  ---------------------------------- --------------------------- ----------------------------------------

Entrega programada, também pedida por Alberto: \"a entrega pode ser
dividido, e também o comprador pode estimar um prazo de entregas,
exemplo estou comprando 1 tonelada de areais, preciso que seja entregue
0,5t em data X e 0,5t na data Y\" --- substitui o campo único
Prazo_Entrega_Estimado_Dias da Revisão 1 por uma linha por entrega, cada
uma com sua própria data, quantidade, modalidade, destino e
transportadora de referência.

Mov_Cotacao_Venda_Item_Entrega_Programada

Adicionado nesta revisão: uma entrega programada de parte (ou do todo)
da Quantidade de um item da cotação --- a soma das quantidades
programadas de um item deve fechar na Quantidade total do item
(validação de aplicação, ver Notas).

*Vigência: não --- cada linha é um compromisso de entrega específico;
alterações antes da aceitação sobrescrevem o próprio registro, sem
histórico da mudança nesta v1.*

  ----------------------------------------------- ------------------------------ ----------------------------------------
  **Campo**                                       **Tipo lógico**                **Descrição / regra**

  **ID_Entrega_Programada**                       *identificador*                ---

  **ID_Item_Cotacao**                             *referência                    ---
                                                  (Mov_Cotacao_Venda_Item)*      

  **Quantidade_Programada**                       *número*                       A fração da Quantidade total do item
                                                                                 coberta por esta entrega.

  **Data_Entrega_Programada**                     *data*                         A data estimada, informada por quem
                                                                                 cotou --- não calculada a partir de
                                                                                 capacidade de Produção (módulo ainda não
                                                                                 especificado; ver Notas).

  **Modalidade_Entrega**                          *enumeração {retirada_cliente, Adicionado nesta revisão, pedido por
                                                  entrega_endereco_cliente,      Alberto: como a mercadoria chega ao
                                                  entrega_porto,                 destino --- o cliente retira, ou a
                                                  entrega_centro_distribuicao,   Mlegate entrega na porta do cliente, no
                                                  outro}*                        porto, ou num centro de distribuição.

  **ID_Endereco_Entrega**                         *referência                    Preenchido quando Modalidade_Entrega
                                                  (Cad_Participante_Endereco,    exige um endereço de destino
                                                  Fase 0, opcional)*             (entrega_endereco_cliente,
                                                                                 entrega_porto,
                                                                                 entrega_centro_distribuicao) ---
                                                                                 Tipo_Endereco=entrega, valor já previsto
                                                                                 no enum do Fase 0. Vazio quando
                                                                                 Modalidade_Entrega=retirada_cliente.

  **ID_Local_Estoque**                            *referência                    Adicionado nesta revisão, pedido por
                                                  (Cad_Local_Estoque, Fase 1 --- Alberto: \"o vendedor pode escolher a
                                                  Estoque, opcional)*            filial local onde sairá o produto para
                                                                                 fazer a reserva do estoque\" ---
                                                                                 alimenta diretamente a
                                                                                 Mov_Estoque_Reserva desta entrega (seção
                                                                                 6), em vez de o sistema assumir sempre o
                                                                                 local principal da filial (comportamento
                                                                                 da Revisão 1).

  **Local_Entrega_Descricao**                     *texto, opcional*              Complemento livre, quando o endereço
                                                                                 cadastrado não for suficiente para
                                                                                 descrever o destino (ex.: doca
                                                                                 específica no porto).

  **ID_Participante_Transportadora_Referencia**   *referência (Cad_Participante, Renomeado e redefinido nesta revisão (3)
                                                  opcional)*                     --- Alberto corrigiu uma confusão de
                                                                                 papéis: \"o vendedor pode até sugerir
                                                                                 Cad_Produto_Servico_Transportadora,
                                                                                 alguém fará a contratação do
                                                                                 transportador, mas quem faz a definição
                                                                                 é a expedição \[\...\] a área de
                                                                                 compras/expedição quem vai definir a
                                                                                 transportadora\". Este campo deixa de
                                                                                 ser a transportadora que vai de fato
                                                                                 executar o envio --- passa a ser só uma
                                                                                 referência de custo, sugerida a partir
                                                                                 de Cad_Produto_Servico_Transportadora
                                                                                 (Fase 0), usada para estimar o valor de
                                                                                 frete no momento da venda (ver
                                                                                 Valor_Frete_Negociado, abaixo). A
                                                                                 transportadora real, contratada pela
                                                                                 Expedição, pode ser outra --- Alberto:
                                                                                 \"no momento da venda o vendedor pode
                                                                                 até cotar \[\...\] cobrar do cliente uma
                                                                                 entrega, por exemplo via correio, mas no
                                                                                 final foi enviado pelo DHL\". Quem
                                                                                 executa de fato é dado de uma futura
                                                                                 entidade de Expedição (ver Notas, seção
                                                                                 12), fora do escopo deste módulo.

  **Modalidade_Cobranca_Frete**                   *enumeração {sem_cobranca,     Adicionado nesta revisão (3), pedido por
                                                  valor_fixo,                    Alberto: \"o frete pode ser cobrado do
                                                  a_apurar_no_envio}*            cliente ou não, depende da negociação da
                                                                                 venda\" --- sem_cobranca quando o frete
                                                                                 não é repassado ao cliente (embutido no
                                                                                 preço, ou por conta da Mlegate);
                                                                                 valor_fixo quando um valor foi negociado
                                                                                 e deve ser mantido
                                                                                 (Valor_Frete_Negociado, abaixo);
                                                                                 a_apurar_no_envio quando a negociação
                                                                                 prevê que o valor de frete cobrado será
                                                                                 o efetivamente apurado no envio, ficando
                                                                                 variável até lá (Alberto: \"posso ter a
                                                                                 opção, na negociação de vendas, que o
                                                                                 frete será apurado no envio, com isto o
                                                                                 valor do frete fica variável\").

  **Valor_Frete_Negociado**                       *número, opcional*             Adicionado nesta revisão (3), preenchido
                                                                                 só quando
                                                                                 Modalidade_Cobranca_Frete=valor_fixo. É
                                                                                 o valor NEGOCIADO com o cliente --- uma
                                                                                 vez fechado, é mantido, nunca
                                                                                 recalculado a partir do custo real pago
                                                                                 à transportadora (mesmo princípio de
                                                                                 fidelidade ao valor real usado em todo
                                                                                 este dicionário desde Compras): Alberto
                                                                                 foi explícito --- \"o valor do frete
                                                                                 negociado na venda tem que ser mantido;
                                                                                 o que pode mudar é o que vou pagar,
                                                                                 posso ganhar ou perder no frete\". O
                                                                                 custo efetivamente pago à transportadora
                                                                                 é um conceito totalmente separado, de
                                                                                 uma futura Expedição/Contas a Pagar,
                                                                                 fora do escopo deste módulo. Quando a
                                                                                 modalidade é a_apurar_no_envio, não há
                                                                                 valor negociado aqui --- o valor real só
                                                                                 se define depois (ver
                                                                                 Mov_Nota_Fiscal_Saida.Valor_Frete, seção
                                                                                 7, e seção 9).
  ----------------------------------------------- ------------------------------ ----------------------------------------

3\. Tabela de Preço, Comissão e Royalty --- o mesmo Motor de Regras

Nenhuma tabela nova de preço, comissão ou royalty foi criada --- as três
reaproveitam integralmente o Motor de Regras do Fase 0
(Cad_Motor_Regra/Cad_Motor_Regra_Criterio/Cad_Motor_Regra_Resultado),
exatamente como o Documento Analítico descreve: \"tabela de preço e
tabela de comissão compartilham as mesmas dimensões configuráveis de
produto, com prioridade de regra definida pelo gestor \[\...\] e o mesmo
motor calcula royalty de licenciamento\".
Cad_Motor_Regra_Resultado.Tipo_Resultado ganhou valor_preco_unitario e
percentual_royalty na revisão 12 do Fase 0, para acompanhar o
percentual_comissao que já existia; Cad_Motor_Regra_Criterio.Campo
ganhou licenciamento_produto na mesma revisão e papel_comissionado na
revisão 13 --- usado por Mov_Cotacao_Venda_Item_Comissao (seção 2) para
resolver o percentual de cada nível da escada separadamente, sem mudar a
estrutura genérica do motor: continua sendo uma linha de
Cad_Motor_Regra_Resultado por combinação de critérios, agora incluindo o
cargo comercial como mais uma dimensão possível. Na revisão 3, esse
cargo deixou de ser um dos três valores fixos {vendedor, supervisor,
gerente} e passou a apontar para o domínio aberto cargo_comercial
(Cad_Classe_Sistema, Fase 0 revisão 14) --- a Mlegate pode cadastrar
quantos níveis de cargo comercial precisar, cada um com sua própria
regra de percentual aqui, sem exigir mudança de estrutura.

A escada em si, na revisão 3, passou a ser gerada automaticamente pela
hierarquia comercial, não mais montada linha a linha pelo vendedor. Ao
aceitar uma cotação (ou, na prática, já ao calcular a estimativa na
cotação), a aplicação identifica o vendedor responsável e sobe a cadeia
de
Cad_Participante_Historico_Hierarquia_Comercial.ID_Participante_Superior
(Fase 0, revisão 14) --- vigente na DATA da venda, não o cadastro atual
--- gerando uma linha de Mov_Cotacao_Venda_Item_Comissao para o próprio
vendedor e mais uma para cada superior encontrado, até não haver mais
superior (sem limite de níveis: Alberto foi explícito --- \"pode ter 1
nível, quantos forem necessários\"). A linha do vendedor sempre resolve
o percentual pelo cargo-base \"vendedor\" do domínio, mesmo que o cargo
cadastrado dele já seja de nível superior (Alberto: \"no caso do
superintendente ou gerente vender diretamente ele leva o percentual como
se fosse vendedor\") --- as demais linhas da escada usam o cargo real de
cada superior. Cada nível, então, tem seu próprio percentual resolvido
separadamente pelo Motor de Regras, por Campo=papel_comissionado.

Ao adicionar um item na cotação (seção 2), o sistema consulta o Motor de
Regras com os critérios do produto (e, quando cadastrado, do
cliente/grupo) para resolver, na mesma passada ou em regras separadas
--- a estrutura genérica suporta os dois casos sem diferença de schema
---, o preço de tabela (Tipo_Resultado=valor_preco_unitario), a comissão
de cada nível da escada (percentual_comissao, uma resolução por cargo)
e, quando o produto é licenciado, o royalty (percentual_royalty).
Prioridade de regra (Cad_Motor_Regra.Prioridade) decide qual bate
primeiro quando mais de uma se aplica --- mesmo mecanismo
específico-vence-o-genérico já usado em todo o dicionário desde o Fase
0.

*Desconto reduz comissão: quando Valor_Unitario_Proposto (seção 2) fica
abaixo de Valor_Unitario_Tabela, o Percentual_Comissao_Estimado de cada
linha da escada (Mov_Cotacao_Venda_Item_Comissao) é recalculado de duas
formas possíveis, ambas suportadas pela mesma estrutura sem mudança de
schema --- proporcional à redução do valor, ou por um fator tabelado à
parte (uma segunda regra, critério = faixa de percentual de desconto,
resultado = fator de redução da comissão). Qual das duas formas vale
fica a critério de quem cadastra a regra em Cad_Motor_Regra, não é uma
decisão fixa deste dicionário.*

Royalty de licenciamento: calculado sobre Valor_Total do item,
tipicamente resolvido pelo critério licenciamento_produto.

Tanto a comissão (por beneficiário) quanto o royalty resolvidos aqui são
sempre estimativas --- Alberto foi explícito: \"na venda só temos uma
estimativa destes valores, pois a comissão/royalty pode depender do
recebimento efetivo\". O Motor de Regras roda no momento da cotação, mas
o direito efetivo e o valor definitivo só se confirmam quando o cliente
de fato paga. Por isso os campos que guardam esse resultado usam sempre
o sufixo \_Estimado (Percentual_Comissao_Estimado,
Percentual_Royalty_Estimado), nunca \_Resultante ou \_Definitivo ---
nomenclatura corrigida nesta revisão em relação à Revisão 1. Este módulo
só calcula e expõe a estimativa de percentual/valor de royalty e
comissão na cotação e no pedido, e gera a provisão contábil
correspondente (seção 9) --- o repasse financeiro efetivo (ao vendedor,
ao licenciante) fica para quando Contas a Pagar for detalhado (ver seção
9 e seção 12).

Lista de preço fixa do autoatendimento e canal de origem --- dois usos
novos do mesmo motor, nesta revisão (4), sem nenhuma tabela nova:
Alberto foi explícito ao decidir manter tudo num único Motor de Regras
(\"melhor manter em um único motor\"). Uma lista de preço \"para o
mercado em geral\" é simplesmente uma regra de valor_preco_unitario SEM
critério de cliente/grupo_cliente; uma lista \"específica para um
cliente ou grupo econômico\" é a mesma regra, só que COM esse critério
--- a mais específica vence a mais genérica, mecanismo de prioridade que
já existe desde o Fase 0. Da mesma forma, Cad_Motor_Regra_Criterio.Campo
ganhou canal_origem (Fase 0, revisão 15) --- permite uma regra de
percentual_comissao (ou de valor_preco_unitario) diferente conforme
Mov_Cotacao_Venda.Canal_Origem seja atendimento_vendedor ou
autoatendimento (seção 2), porque Alberto foi explícito que \"podemos
ter regras distintas de comissões para um atendimento, ou
autoatendimento\".

4\. Aprovação da Cotação

Diferença deliberada em relação a Compras: lá, o PEDIDO passa por
aprovação depois de criado (Origem_Tipo=pedido_compra). Aqui, o
Documento Analítico é explícito --- \"o pedido de venda nasce, sempre já
confirmado (a aprovação aconteceu no momento da aceitação da cotação)\".
Não existe, portanto, aprovação de Mov_Pedido_Venda: toda a régua se
aplica à COTAÇÃO, antes de ela poder ser aceita.

Reaproveita a régua de aprovação inteira do Fase 0 (Cad_Regua_Aprovacao,
Cad_Regua_Faixa, Cad_Regua_Aprovador, Cad_Usuario_Escopo), sem nenhuma
estrutura nova --- três gatilhos, todos convergindo para o mesmo
Status=em_aprovacao, cada um com seu próprio Origem_Tipo em
Mov_Aprovacao_Instancia (Fase 0): cotacao_venda (desconto além da alçada
do vendedor, patch pontual ao Fase 0 desde a revisão 12); desvio_credito
(exposição × teto, Contas a Pagar/Receber, seção 6 daquele documento); e
bloqueio_regua_cobranca, adicionado nesta revisão (5) --- o degrau final
da régua de cobrança de Tesouraria (seção 10 daquele documento). O valor
comparado contra a faixa de alçada em cotacao_venda é o desconto ---
Percentual_Desconto agregado da cotação, ou o maior entre os itens; os
outros dois não comparam valor contra régua de aprovação --- são
bloqueios diretos, sem faixa de alçada a percorrer.

Como uma cotação pode ter mais de um gatilho ativo ao mesmo tempo (ex.:
desconto pedido E cliente com exposição de crédito estourada), este
documento não usa mais um campo único ID_Instancia_Aprovacao em
Mov_Cotacao_Venda --- ambíguo com mais de uma causa possível, ponto que
a própria Contas a Pagar/Receber já sinalizava como pendente. Em vez
disso, TODA instância de aprovação de uma cotação é encontrada por
consulta: toda Mov_Aprovacao_Instancia com ID_Origem=ID_Cotacao e
Origem_Tipo em {cotacao_venda, desvio_credito, bloqueio_regua_cobranca}
pertence a ela --- mesmo padrão \"nenhuma entidade nova para a
tela/relatório, é uma consulta\" já usado no resto deste dicionário. A
cotação permanece em Status=em_aprovacao enquanto existir qualquer uma
dessas instâncias com Status=pendente.

Fluxo por desconto, atendimento por vendedor
(Canal_Origem=atendimento_vendedor): o vendedor monta a cotação
(Status=aberta); se nenhum item pedir desconto além da própria alçada do
vendedor E não houver bloqueio de crédito/cobrança ativo para o grupo
econômico do cliente (abaixo), ele mesmo pode marcar Status=aceita
diretamente. Se algum item ultrapassar a alçada, ou se houver bloqueio
de crédito/cobrança, Status vai para em_aprovacao --- a pendência é
MOSTRADA ao vendedor que está atendendo, para ele decidir (não é um
bloqueio automático nem oculto). Recusada pelo aprovador, ou pelo
próprio solicitante, o Status vai para recusada --- sem gerar pedido.

Fluxo por desconto, autoatendimento (Canal_Origem=autoatendimento, seção
2 e 9): NUNCA passa pela régua de desconto --- a cotação nasce
pré-preenchida com a lista de preço fixa (seção 3) e, quando há estoque
disponível, não há desconto negociado a avaliar. Diferente da Revisão 4,
porém, o autoatendimento não nasce mais automaticamente com
Status=aceita nesta situação: se houver bloqueio de crédito/cobrança
ativo para o grupo econômico do cliente (abaixo), a cotação entra em
análise (Status=em_aprovacao) mesmo sem desconto nenhum envolvido.

Integração do bloqueio de crédito e de cobrança (Revisão 5)

A pedido de Alberto, os dois gatilhos de bloqueio já definidos em outros
módulos --- desvio de crédito (Contas a Pagar/Receber, seção 6:
exposição total versus teto, cascata de Grupo Econômico/CNPJ
Raiz/individual para efeito de CONFIGURAÇÃO do limite) e régua de
cobrança (Tesouraria, seções 9 e 10: dias de atraso) --- passam a ser de
fato consultados no momento em que uma cotação é avaliada, não só
definidos como fórmula. Três decisões desta revisão:

-   Nível de bloqueio: sempre no grupo económico do cliente, não
    cascateando para CNPJ Raiz/individual como a configuração do
    Limite_Credito em si permite --- simplificação deliberada,
    confirmada por Alberto, distinta da cascata de três níveis usada
    para saber QUAL teto vale.

-   Canal atendimento por vendedor: a pendência (por desvio_credito ou
    bloqueio_regua_cobranca) é só mostrada ao vendedor responsável pela
    cotação, para ele decidir --- nunca um bloqueio automático que
    impede a criação da cotação.

-   Canal autoatendimento: como a cotação pode ser feita pelo próprio
    cliente, expor o motivo do bloqueio a ele poderia gerar
    constrangimento. A cotação simplesmente entra em análise
    (Status=em_aprovacao), sem atendimento automático --- nem aprovação
    nem recusa sozinha. Como o autoatendimento tipicamente não tem
    vendedor atribuído, ela cai na mesma fila única de cotações sem
    vendedor já existente (seção 2 e 4) --- um vendedor ou gestor assume
    e decide depois, sem que o cliente veja o motivo específico do
    bloqueio, só que sua cotação está em análise.

*Nenhuma entidade nova para o bloqueio em si --- reaproveita
inteiramente o motor de régua de aprovação já existente, só com o novo
Origem_Tipo=bloqueio_regua_cobranca (Fase 0) ao lado de desvio_credito.
Ver Tesouraria, seção 10, para o detalhe da régua de cobrança em si.*

Fila de cotações (seção 2): quando a cotação nasce sem
Cad_Participante.ID_Participante_Vendedor_Principal do cliente
preenchido (ou quando o autoatendimento não encontra estoque, ver seção
9), ela fica na fila única, com ID_Participante_Vendedor vazio ---
independente do Status (aberta, ou em_aprovacao se já havia desconto
pedido antes de cair na fila). Um vendedor qualquer pode pegar a cotação
da fila, preenchendo ID_Participante_Vendedor e
Data_Hora_Atribuicao_Vendedor (comportamento de aplicação, não uma nova
régua) --- a partir daí, o fluxo de aprovação segue normalmente, como se
o vendedor tivesse montado a cotação desde o início.

5\. Pedido de Venda

O pedido de venda não tem criação direta neste módulo --- nasce sempre
da aceitação de uma cotação (Mov_Cotacao_Venda.Status=aceita, seção 2 e
4), já confirmado. Diferente de Compras, onde Mov_Pedido.Status era um
único enum de cabeçalho, aqui --- por exigência explícita do Documento
Analítico (\"o status é tracked como histórico completo, por item de
pedido, não um único status agregado\") --- o rastreamento fino vive por
item, num histórico apensável, nunca um campo de status sincronizado à
parte: mesma filosofia de \"nunca armazenado, sempre derivado\" já usada
para saldo em todo este dicionário (Fase 0 --- Mov_Lancamento; Estoque
--- Mov_Estoque_Movimento_Item), aqui aplicada a status em vez de saldo.

Mov_Pedido_Venda

O cabeçalho do pedido de venda --- nasce automaticamente no instante em
que a cotação de origem é aceita.

*Vigência: não --- é o registro de um evento; Status cobre só a exceção
de cancelamento total, não o ciclo normal.*

  ----------------------------- ---------------------- ---------------------------------------------------
  **Campo**                     **Tipo lógico**        **Descrição / regra**

  **ID_Pedido**                 *identificador*        ---

  **ID_Cotacao**                *referência            Obrigatório --- não existe pedido de venda sem
                                (Mov_Cotacao_Venda)*   cotação aceita de origem, diferente de Compras
                                                       (onde o pedido podia nascer sem cotação).

  **ID_Filial**                 *referência            Herdada da cotação.
                                (Cad_Filial)*          

  **ID_Participante_Cliente**   *referência            Sempre um Participante já efetivado neste ponto ---
                                (Cad_Participante)*    a conversão de pré-cadastro (quando
                                                       Mov_Cotacao_Venda.Tipo_Solicitante=pre_cadastro),
                                                       se necessária, já aconteceu no instante da
                                                       aceitação, antes do pedido nascer.

  **Data_Pedido**               *data*                 ---

  **Data_Hora_Confirmacao**     *data/hora*            O próprio momento da aceitação da cotação --- é o
                                                       nascimento do pedido, não um evento posterior.

  **Status**                    *enumeração            Cobre só o cancelamento do pedido INTEIRO (ex.:
                                {confirmado,           cliente desiste antes de qualquer faturamento) ---
                                cancelado}*            o ciclo normal (separação, faturamento
                                                       parcial/total, entrega) é rastreado por item, não
                                                       aqui (ver Mov_Pedido_Venda_Item_Status_Historico,
                                                       abaixo).
  ----------------------------- ---------------------- ---------------------------------------------------

*Comportamento de aplicação --- exceção ao fechamento do bloco
\"vendas\" (seção 7): confirmada por Alberto, esta é a única exceção
deste tipo em todo o redesenho --- CRIAR um Mov_Pedido_Venda (e a
cotação de origem, seção 2) continua liberado mesmo com o bloco
\"vendas\" fechado para a Filial+competência, porque, sem atendimento
ainda, o pedido não afeta fiscal nem valor da empresa (o oposto de
Compras, onde o Pedido de Compra fica travado desde a criação, por já
gerar compromisso orçamentário). A exceção vale só para a criação:
alterar um Mov_Pedido_Venda já existente de um jeito que mude o que
seria faturado/entregue numa competência fechada segue a mesma trava da
nota fiscal de saída (seção 7) --- não é liberação geral de edição.*

Mov_Pedido_Venda_Item

Uma linha do pedido --- copiada da linha de cotação correspondente no
instante do nascimento.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Pedido** | *referência (Mov_Pedido_Venda)* | --- |
| **ID_Item_Cotacao** | *referência (Mov_Cotacao_Venda_Item)* | Sempre preenchido --- a linha de cotação que originou este item. |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico)* | --- |
| **Quantidade** | *número* | --- |
| **Valor_Unitario** | *número* | Copiado de Mov_Cotacao_Venda_Item.Valor_Unitario_Proposto no nascimento --- não editável depois, mesmo princípio de fidelidade ao valor já acordado com o cliente. |
| **Valor_Total** | *número* | Campo próprio, não recalculado a partir de Quantidade × Valor_Unitario --- mesmo princípio de fidelidade ao valor real já usado em Compras (seção 6 daquele documento), que antecipava explicitamente valer também aqui. |
| **Percentual_Royalty_Estimado** | *número, opcional* | Copiado de Mov_Cotacao_Venda_Item.Percentual_Royalty_Estimado no nascimento --- mesma fidelidade ao valor já acordado, usado para calcular a provisão contábil de royalty (seção 9). |
| **ID_Natureza_Operacao_Cambial_Royalty** | *referência (Cad_Natureza_Operacao_Cambial), opcional* | Revisão 28 (documento 127, seção 6, Q127-5; documento 152): a natureza da operação cambial do royalty de venda, resolvida pelo Motor de Regras (Tipo_Resultado = id_natureza_operacao_cambial, na mesma regra de licenciamento) na hora em que o item guarda Percentual_Royalty_Estimado. O título royalty_venda nasce com esta natureza herdada em Mov_Titulo.ID_Natureza_Operacao_Cambial: o financeiro não digita de novo e só troca com o motivo. O royalty do exterior sem venda (avulso) não passa por aqui. |
| **Local_Na_Contratante** | *booleano* | Adicionado na revisão 12 (Bloco 2). Padrão sim. Sim = o local é o endereço do contratante; não = o local está em ID_Local_Operacao. |
| **ID_Endereco_Contratante** | *referência (Cad_Participante_Endereco, opcional)* | Adicionado na revisão 12 (Bloco 2). A versão do endereço do contratante usada; preenchida quando Local_Na_Contratante = sim. |
| **ID_Local_Operacao** | *referência (Cad_Local_Operacao, opcional)* | Adicionado na revisão 12 (Bloco 2). Obrigatória quando Local_Na_Contratante = não; vazia quando = sim. |
| **ID_Habilitacao** | *referência (Cad_Habilitacao_Regime_Especial, opcional)* | Adicionado na revisão 12 (Bloco 2). Habilitação do cliente, informada por ele para essa linha (confirmado por Alberto). |

*Revisão 28 --- campos novos: ID_Natureza_Operacao_Cambial_Royalty.*

Mov_Pedido_Venda_Item_Comissao

Cópia congelada de Mov_Cotacao_Venda_Item_Comissao no nascimento do
pedido --- a escada de comissão, por beneficiário/papel, tal como estava
na cotação aceita. Usada para calcular a provisão contábil de comissão
(seção 9).

*Vigência: não.*

  ---------------------------------- -------------------------- ----------------------------------------
  **Campo**                          **Tipo lógico**            **Descrição / regra**

  **ID_Item_Comissao**               *identificador*            ---

  **ID_Item**                        *referência                ---
                                     (Mov_Pedido_Venda_Item)*   

  **ID_Participante_Beneficiario**   *referência                Copiado da linha de comissão da cotação.
                                     (Cad_Participante)*        

  **ID_Papel_Comissionado**          *referência                Copiado da linha de comissão da cotação.
                                     (Cad_Classe_Sistema,       
                                     domínio cargo_comercial)*  

  **Percentual_Comissao_Estimado**   *número*                   Copiado da linha de comissão da cotação
                                                                --- continua sendo estimativa até o
                                                                recebimento efetivo (seção 9).
  ---------------------------------- -------------------------- ----------------------------------------

Mov_Pedido_Venda_Item_Entrega_Programada

Cópia de Mov_Cotacao_Venda_Item_Entrega_Programada no nascimento do
pedido --- mesmos campos, agora vinculados ao item do pedido. A Reserva
de Estoque (seção 6) nasce uma vez por linha de entrega programada, não
mais uma por item inteiro, refletindo a divisão por data/quantidade
pedida por Alberto.

*Vigência: não --- pode ser editada depois do nascimento do pedido (ex.:
adiar uma data), sempre uma edição direta, sem histórico da mudança
nesta v1, mesmo tratamento dado a outros campos livremente editáveis em
Compras.*

  ----------------------------------------------- ------------------------------ ----------------------------------------
  **Campo**                                       **Tipo lógico**                **Descrição / regra**

  **ID_Entrega_Programada**                       *identificador*                ---

  **ID_Item**                                     *referência                    ---
                                                  (Mov_Pedido_Venda_Item)*       

  **Quantidade_Programada**                       *número*                       Copiada da entrega programada da
                                                                                 cotação.

  **Data_Entrega_Programada**                     *data*                         Copiada da entrega programada da cotação
                                                                                 --- editável depois (ex.: adiar uma data
                                                                                 já confirmada com o cliente).

  **Modalidade_Entrega**                          *enumeração {retirada_cliente, Copiada da entrega programada da
                                                  entrega_endereco_cliente,      cotação.
                                                  entrega_porto,                 
                                                  entrega_centro_distribuicao,   
                                                  outro}*                        

  **ID_Endereco_Entrega**                         *referência                    Copiado da entrega programada da
                                                  (Cad_Participante_Endereco,    cotação.
                                                  Fase 0, opcional)*             

  **ID_Local_Estoque**                            *referência                    Copiado da entrega programada da cotação
                                                  (Cad_Local_Estoque, Fase 1 --- --- alimenta a Mov_Estoque_Reserva desta
                                                  Estoque, opcional)*            entrega (seção 6).

  **Local_Entrega_Descricao**                     *texto, opcional*              Copiado da entrega programada da
                                                                                 cotação.

  **ID_Participante_Transportadora_Referencia**   *referência (Cad_Participante, Copiado da entrega programada da cotação
                                                  opcional)*                     --- apenas a referência de custo usada
                                                                                 na estimativa da venda (ver seção 2); a
                                                                                 transportadora real fica a cargo da
                                                                                 futura Expedição (seção 9 e Notas).

  **Modalidade_Cobranca_Frete**                   *enumeração {sem_cobranca,     Copiado da entrega programada da
                                                  valor_fixo,                    cotação.
                                                  a_apurar_no_envio}*            

  **Valor_Frete_Negociado**                       *número, opcional*             Copiado da entrega programada da cotação
                                                                                 --- mantido tal como negociado
                                                                                 (fidelidade ao valor real, seção 2),
                                                                                 independentemente do que a Mlegate venha
                                                                                 a pagar de fato à transportadora.
  ----------------------------------------------- ------------------------------ ----------------------------------------

Mov_Pedido_Venda_Parcela

Cópia congelada de Mov_Cotacao_Venda_Parcela no nascimento do pedido ---
o parcelamento real deste pedido, editável enquanto não liquidado
(Contas a Receber, Fase 2, ainda não especificado), mesmo tratamento
dado a Mov_Pedido_Parcela em Compras.

*Vigência: não.*

  --------------------- --------------------- ----------------------------------------
  **Campo**             **Tipo lógico**       **Descrição / regra**

  **ID_Parcela**        *identificador*       ---

  **ID_Pedido**         *referência           ---
                        (Mov_Pedido_Venda)*   

  **Numero_Parcela**    *número*              Copiado da parcela da cotação.

  **Valor_Parcela**     *número*              Copiado da parcela da cotação ---
                                              explícito, editável até a liquidação.

  **Data_Vencimento**   *data*                Copiada de Data_Vencimento_Estimada da
                                              parcela da cotação --- passa a ser a
                                              data real negociada, editável até a
                                              liquidação.
  --------------------- --------------------- ----------------------------------------

Mov_Pedido_Venda_Item_Status_Historico

O histórico completo de status de uma linha do pedido --- cada linha
desta tabela é um evento imutável; o status ATUAL de um item é sempre o
registro de Data_Hora mais recente para aquele ID_Item, nunca um campo
separado sincronizado à parte.

*Vigência: não --- é histórico por natureza (cada evento é uma linha
nova, nunca atualizada), mesma filosofia de saldo derivado já usada no
restante do dicionário, aqui aplicada a status.*

  ------------------ ------------------------------------- ----------------------------------------
  **Campo**          **Tipo lógico**                       **Descrição / regra**

  **ID_Historico**   *identificador*                       ---

  **ID_Item**        *referência (Mov_Pedido_Venda_Item)*  ---

  **Status**         *enumeração {confirmado,              O primeiro registro de todo item é
                     aguardando_producao_personalizacao,   sempre confirmado, gerado junto com o
                     em_separacao, faturado_parcial,       nascimento do pedido.
                     faturado_total, entregue,             aguardando_producao_personalizacao,
                     devolvido_parcial, devolvido_total,   adicionado nesta revisão a pedido de
                     cancelado}*                           Alberto (\"pode depender de uma produção
                                                           de produto que ainda não está pronto, ou
                                                           personalização necessária\"), sinaliza
                                                           que a saída programada (acima) não pode
                                                           ser cumprida ainda --- sem modelar o
                                                           processo de produção em si, que continua
                                                           dependendo do módulo de Produção (Fase
                                                           3). faturado_parcial/faturado_total são
                                                           gerados pela nota fiscal de saída (seção
                                                           7); devolvido_parcial/devolvido_total
                                                           pela devolução de cliente (seção 8).

  **Data_Hora**      *data/hora*                           ---

  **Observacao**     *texto, opcional*                     ---
  ------------------ ------------------------------------- ----------------------------------------

*Faturamento/entrega em múltiplas notas: como o Documento Analítico
prevê que \"o pedido pode ser entregue e faturado em múltiplas notas
fiscais ao longo do tempo\", um único Mov_Pedido_Venda_Item pode ser
referenciado por mais de uma linha de Mov_Nota_Fiscal_Saida_Item (seção
7) --- o sistema soma toda a Quantidade já faturada contra aquele item
para decidir se o novo registro de histórico é faturado_parcial ou
faturado_total, mesmo padrão de acumulado já usado em Compras (seção 6
daquele documento) para comparar nota contra pedido.*

*Efeitos coordenados do nascimento do pedido: no mesmo instante em que a
cotação é aceita, além do cabeçalho e das linhas do pedido, o sistema
também congela Mov_Pedido_Venda_Parcela (a partir de
Mov_Cotacao_Venda_Parcela), Mov_Pedido_Venda_Item_Comissao e
Mov_Pedido_Venda_Item_Entrega_Programada (a partir das tabelas
equivalentes da cotação), gera a primeira Mov_Estoque_Reserva de cada
entrega programada (seção 6) e lança a provisão contábil de
comissão/royalty (seção 9) --- tudo na mesma transação de nascimento,
mesmo padrão de efeitos colaterais coordenados por um único evento já
usado na emissão da nota fiscal (seção 7).*

6\. Reserva de Estoque

Conceito novo, deliberadamente deixado em aberto pelo módulo de Estoque
(\"depende do módulo de CRM & Vendas\") e agora modelado aqui como
controle PRÓPRIO --- não como uma extensão de Mov_Estoque_Movimento.
Isso preserva, sem exceção, a fórmula de saldo já fechada em Estoque
(seção 5 daquele documento): o saldo de um produto continua sendo
estritamente a soma de Mov_Estoque_Movimento_Item, nunca considerando
reserva. \"Disponível\", o número que de fato interessa para vender, é
uma leitura COMBINADA entre os dois módulos, calculada em tempo de
consulta --- mesma filosofia de \"nunca armazenado, sempre derivado\" já
usada em todo este dicionário: Disponível = saldo derivado do Estoque
MENOS a soma de Quantidade_Reservada com Status=ativa, para o mesmo
produto e local.

Mov_Estoque_Reserva

Uma reserva de quantidade contra um local de estoque específico ---
reduz o Disponível sem gerar, por si só, nenhum Mov_Estoque_Movimento
real. Nasce por linha de entrega programada, não mais por item inteiro
do pedido (mudança desta revisão): cada entrega programada tem sua
própria data, quantidade e local, e cada uma reserva separadamente.

*Vigência: não.*

  --------------------------- --------------------------------------------- -----------------------------------------------------------------
  **Campo**                   **Tipo lógico**                               **Descrição / regra**

  **ID_Reserva**              *identificador*                               ---

  **ID_Entrega_Programada**   *referência                                   Adicionado nesta revisão, substituindo a referência direta a
                              (Mov_Pedido_Venda_Item_Entrega_Programada)*   Mov_Pedido_Venda_Item da Revisão 1 --- permite refletir a divisão
                                                                            por data/quantidade/local pedida por Alberto (seção 5).

  **ID_Local_Estoque**        *referência (Cad_Local_Estoque, Fase 1 ---    Copiado de
                              Estoque)*                                     Mov_Pedido_Venda_Item_Entrega_Programada.ID_Local_Estoque --- a
                                                                            escolha explícita do vendedor para aquela entrega, não mais um
                                                                            default de \"local principal da filial\" assumido pelo sistema
                                                                            (comportamento da Revisão 1).

  **Quantidade_Reservada**    *número*                                      Copiada de
                                                                            Mov_Pedido_Venda_Item_Entrega_Programada.Quantidade_Programada.

  **Data_Hora_Reserva**       *data/hora*                                   ---

  **Status**                  *enumeração {ativa, baixada, cancelada}*      \"baixada\" quando a saída física real for lançada para esta
                                                                            entrega (Mov_Estoque_Movimento, Origem_Tipo=pedido_venda, seção
                                                                            7) --- a partir daí a quantidade já está refletida no saldo real,
                                                                            e a reserva para de contar no cálculo de Disponível, pelo próprio
                                                                            Status, sem precisar apagar o registro. \"cancelada\" quando o
                                                                            pedido, o item ou a entrega programada específica é cancelada
                                                                            antes de faturar.
  --------------------------- --------------------------------------------- -----------------------------------------------------------------

*Nasce junto com o pedido: a aceitação da cotação, que faz nascer o
Mov_Pedido_Venda (seção 5), gera automaticamente uma Mov_Estoque_Reserva
para cada linha de entrega programada --- o Disponível já cai no
instante da confirmação do pedido, antes de qualquer separação física ou
nota fiscal. Concorrência entre pedidos simultâneos disputando o mesmo
Disponível fica, como em outros pontos deste dicionário (ex.:
Cad_Usuario_Escopo, Fase 0), como validação de camada de aplicação, não
uma restrição garantida pela própria estrutura de dados.*

7\. Nota Fiscal de Saída e Baixa Física

Mesmo princípio de fidelidade ao valor real já enunciado em Compras
(seção 6 daquele documento, que antecipava explicitamente valer aqui): o
sistema nunca recalcula um valor fiscal --- Valor_Total é sempre um
campo próprio, preenchido com o que está na nota, nunca derivado de
Quantidade × Valor_Unitario, por causa de possíveis
dízimas/arredondamento do emissor. A tributação de saída --- CFOP,
CST/cClassTrib do IBS/CBS --- é decidida pelo Motor de Regras, mesma
estrutura genérica já usada na nota fiscal de entrada de Compras.

*Cross-referenciado nesta revisão (9): Valor_Total desta nota é o que
nasce como Mov_Titulo.Valor_Titulo (Contas a Pagar/Receber, seção 2, via
Mov_Pedido_Venda_Parcela quando houver parcelamento) --- mas o valor de
fato recebido do cliente pode ser menor, por retenção na fonte (órgão
público/sociedade de economia mista) ou por split payment do IBS/CBS na
baixa: nenhuma estrutura nova aqui, só a referência cruzada --- ver
Contas a Pagar/Receber, seções 3 e 11 daquele documento
(Mov_Titulo_Retencao, Fase 2 --- Contabilidade & Fiscal, seção 11), e a
nota equivalente do lado de Contas a Pagar/Receber (seção 3 daquele
documento).*

Mov_Nota_Fiscal_Saida

O cabeçalho da nota fiscal de saída.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Nota** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | A filial emitente. |
| **ID_Participante_Cliente** | *referência (Cad_Participante, opcional)* | Alterado na revisão 3 (documento 33). Vazio na NFC-e sem cadastro do consumidor, que usa Documento_Consumidor e Nome_Consumidor. |
| **Numero** | *código (até 15)* | Identificação fiscal da nota emitida. Desmembrado na revisão 10. |
| **Serie** | *código (até 5)* | Revisão 14 (Bloco 4): passou de 3 para 5 posições, porque o campo serie da EFD-Reinf aceita até 5 caracteres (nota fiscal, fatura ou Recibo Provisório de Serviço). |
| **Chave_Acesso** | *código (até 50)* | Adicionado nesta revisão, princípio geral pedido por Alberto: toda referência a nota fiscal no dicionário precisa carregar a chave de acesso da NFe --- identifica o documento nacionalmente (DV mod 11). Alterado na revisão 3: tipo atualizado. |
| **Data_Emissao** | *data* | --- |
| **Valor_Total** | *número* | O valor total tal como emitido --- nunca recalculado a partir da soma dos itens (ver princípio acima). |
| **Valor_Frete** | *número, opcional* | Adicionado nesta revisão (3), pedido por Alberto: o valor de frete definitivo, confirmado no instante da emissão da nota --- cobre tanto a confirmação do que já era valor_fixo negociado na venda (Mov_Pedido_Venda_Item_Entrega_Programada.Valor_Frete_Negociado) quanto a apuração real de frete quando a modalidade era a_apurar_no_envio (Alberto: \"se estima um valor no momento da venda e o valor vai ser apurado realmente na hora do envio, com isto é ajustado na hora da emissão da nota fiscal\"). Vazio quando Modalidade_Cobranca_Frete=sem_cobranca em todas as entregas programadas do pedido faturado por esta nota. |
| **Status** | *enumeração {emitida, cancelada}* | --- |
| **ID_Modelo_Documento** | *referência (Cad_Modelo_Documento_Fiscal)* | Alterado na revisão 3 (documento 43). Modelo do documento fiscal (55, 57, 65, NFS-e e demais), do cadastro de modelos; o código de cada obrigação (COD_MOD da EFD e outros) vem de Cad_Modelo_Documento_Fiscal_Codigo. Adicionado na revisão 12 (Bloco 2); apontava o domínio modelo_documento_fiscal (tabela 4.1.1) até a revisão 3. |
| **ID_Situacao_Documento** | *referência (Cad_Classe_Sistema, domínio = situacao_documento_fiscal)* | Adicionado na revisão 12 (Bloco 2). Tabela 4.1.2 --- regular, cancelado, denegado, inutilizado, complementar, extemporâneo e demais. |
| **Finalidade** | *enumeração {normal, complementar, ajuste, devolucao, credito, debito, substituicao}* | Alterado na revisão 3 (documento 41). finNFe, finNFCom e finNFSe. Valor novo deste documento: substituicao (NFCom finNFCom 3); ajuste atende o finNFCom 4 (ajuste de débito). credito e debito vêm do doc 34 (P-1) e do doc 41 (finNFSe 1 e 2). Os dígitos 0, 3 e 4 (NFCom) e 1 e 2 (NFS-e) são código do XML por modelo, traduzido na geração, e não valor do domínio. |
| **Natureza_Operacao** | *texto* | Adicionado na revisão 12 (Bloco 2). natOp. |
| **Indicador_Consumidor_Final** | *booleano* | Adicionado na revisão 12 (Bloco 2). Na nota, porque no leiaute é por operação. O padrão vem do indicador da IE do destinatário (não contribuinte = consumidor final). |
| **ID_Indicador_Presenca** | *referência (Cad_Classe_Sistema, domínio = indicador_presenca)* | Adicionado na revisão 12 (Bloco 2). indPres. |
| **Protocolo_Autorizacao** | *código (até 16), opcional* | Alterado na revisão 3 (documento 41). Adicionado na revisão 12 (Bloco 2). Vazio até a autorização (saída) ou quando o documento não tem protocolo. Passou de 15 para 16 posições por causa do protocolo da NFCom (posição do site do autorizador). |
| **Data_Hora_Autorizacao** | *data/hora, opcional* | Adicionado na revisão 12 (Bloco 2). |
| **ID_Modalidade_Frete** | *referência (Cad_Classe_Sistema, domínio = modalidade_frete)* | Adicionado na revisão 12 (Bloco 2). modFrete: emitente, destinatário, terceiros, sem frete. |
| **Data_Hora_Saida_Entrada** | *data/hora* | Adicionado na revisão 12 (Bloco 2). Prazo de escrituração e DIFAL. |
| **ID_Documento_Fiscal** | *referência (Mov_Documento_Fiscal, opcional)* | Novo na revisão 3 (documento 33). O documento fiscal (chave, protocolo, status, XML) deste documento de negócio; vazio na nota não eletrônica. Decisão D-N1: Chave_Acesso, Protocolo_Autorizacao e Data_Hora_Autorizacao continuam aqui como cópia gravada na autorização. |
| **Tipo_Operacao** | *enumeração {entrada, saida}* | Novo na revisão 3 (documento 33). Tipo da operação (tpNF). A entidade passa a significar "nota emitida pela empresa", inclusive entrada própria, importação e devolução de compra. |
| **Documento_Consumidor** | *código (até 20), opcional* | Novo na revisão 3 (documento 33). CPF, CNPJ ou identificação de estrangeiro do consumidor na NFC-e sem cadastro de participante. |
| **Nome_Consumidor** | *texto, opcional* | Novo na revisão 3 (documento 33). Nome do consumidor na NFC-e sem cadastro de participante. |
| **ID_Expedicao** | *referência (Mov_Expedicao_Saida, opcional)* | Novo na revisão 3 (documento 33). Expedição de origem da nota, quando houver. |
| **Data_Previsao_Entrega** | *data, opcional* | Novo na revisão 3 (documento 34). ide/dPrevEntrega: data de previsão de entrega ou disponibilização do bem (RTC); o evento 112150 a atualiza. |
| **ID_Tipo_Nota_Debito** | *referência (Cad_Classe_Sistema, domínio = tipo_nota_debito), opcional* | Novo na revisão 3 (documento 34). ide/tpNFDebito: tipo da nota de débito (finalidade 6), 8 tipos na NF-e; na NFS-e valem só 01 a 06. |
| **ID_Tipo_Nota_Credito** | *referência (Cad_Classe_Sistema, domínio = tipo_nota_credito), opcional* | Novo na revisão 3 (documento 34). ide/tpNFCredito: tipo da nota de crédito (finalidade 5), 6 tipos na NF-e; na NFS-e valem só 01 e 05. |
| **Escriturada_Como_Entrada** | *booleano, opcional* | Revisão 30 (documento 168, seção 3.2, G2, Q168-1; D-N460 e D-N461): Verdadeiro na nota de crédito de redução de emissão própria: a EFD a registra na entrada. |
| **Indicador_Intermediador** | *enumeração {sem_intermediador, plataforma_terceiros}, opcional* | Novo na revisão 3 (documento 34). ide/indIntermed: operação sem intermediador (site ou plataforma própria) ou em site ou plataforma de terceiros (marketplace, delivery). |
| **ID_Participante_Intermediador** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 34). infIntermed/CNPJ: intermediador da transação; obrigatório quando Indicador_Intermediador = plataforma_terceiros. |
| **Identificador_Cadastro_Intermediador** | *código (até 60), opcional* | Novo na revisão 3 (documento 34). infIntermed/idCadIntTran: identificador do vendedor cadastrado no intermediador. |
| **ID_Participante_Transportadora** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 34). transp/transporta: transportadora (CNPJ ou CPF, nome, IE, endereço) como participante. |
| **Informacoes_Complementares** | *texto, opcional* | Novo na revisão 3 (documento 34). infAdic/infCpl: informações complementares de interesse do contribuinte (até 5000 posições). |
| **Informacoes_Fisco** | *texto, opcional* | Novo na revisão 3 (documento 34). infAdic/infAdFisco: informações adicionais de interesse do Fisco (até 2000 posições). |
| **Numero_Nota_Empenho** | *código (até 22), opcional* | Novo na revisão 3 (documento 34). compra/xNEmp: nota de empenho de compras públicas (NT 2011/004). |
| **Numero_Pedido_Compra** | *código (até 60), opcional* | Novo na revisão 3 (documento 34). compra/xPed (NF-e) e serv/infoCompl/xPed (NFS-e): pedido, ordem de compra, ordem de serviço ou projeto que autoriza a operação. |
| **Numero_Contrato** | *código (até 60), opcional* | Novo na revisão 3 (documento 34). compra/xCont: contrato de compra pública. |
| **ID_Estado_Saida_Pais** | *referência (Cad_Estado, opcional)* | Novo na revisão 3 (documento 34). exporta/UFSaidaPais: UF de embarque ou de transposição de fronteira na exportação. |
| **Local_Exportacao** | *texto, opcional* | Novo na revisão 3 (documento 34). exporta/xLocExporta: local de embarque ou de transposição de fronteira. |
| **Local_Despacho** | *texto, opcional* | Novo na revisão 3 (documento 34). exporta/xLocDespacho: local de despacho aduaneiro, quando houver. |
| **ID_Indicador_Operacao** | *referência (Cad_Indicador_Operacao, opcional)* | Novo na revisão 3 (documento 34). ide/cIndOp: indicador do local da operação de fornecimento (6 dígitos), obrigatório com o grupo retirada em 010104 e 010105 (NT 2025.002). |
| **Safra_Cana** | *código (até 9), opcional* | Novo na revisão 3 (documento 34). cana/safra: identificação da safra (4 a 9 posições). |
| **Competencia_Cana** | *competência, opcional* | Novo na revisão 3 (documento 34). cana/ref: mês e ano de referência (MM/AAAA). |
| **Quantidade_Total_Mes_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/qTotMes: total do mês, em quilogramas. |
| **Quantidade_Total_Anterior_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/qTotAnt: total anterior, em quilogramas. |
| **Quantidade_Total_Geral_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/qTotGer: total geral, em quilogramas. |
| **Valor_Fornecimentos_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/vFor: valor dos fornecimentos. |
| **Valor_Total_Deducoes_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/vTotDed: valor total das deduções. |
| **Valor_Liquido_Fornecimentos_Cana** | *número, opcional* | Novo na revisão 3 (documento 34). cana/vLiqFor: valor líquido dos fornecimentos. |
| **Indicador_Destinatario** | *enumeração {proprio_tomador, outro_destinatario}, opcional* | Novo na revisão 3 (documento 35). Indicador de destinatário da NFS-e (indDest): o destinatário é o próprio tomador (0) ou outra pessoa informada no grupo dest. Serve à DPS nacional e ao RPS de São Paulo; fica na nota e não na DPS. |
| **ID_Entidade_Ligada** | *referência (Cad_Entidade_Ligada_Reinf, opcional)* | Novo na revisão 3 (documento 44). SCP a que a nota pertence, mesmo emitida pelo CNPJ da sócia ostensiva (A100 e 0035). |
| **Valor_Abatimento_Nao_Tributado** | *número, opcional* | Novo na revisão 3 (documento 44). Valor do abatimento não tributado e não comercial, ex.: desconto incondicional da ZFM (C100.VL_ABAT_NT). |
| **Subserie** | *código (até 3), opcional* | Novo na revisão 3 (documento 44). Subsérie do documento, nos modelos legados (C600). |
| **ID_Equipamento_Fiscal** | *referência (Cad_Equipamento_Fiscal, opcional)* | Novo na revisão 3 (documento 44). Equipamento SAT, MFE ou ECF que emitiu o documento (C800 e C860); entra com D-N93. |
| **ID_Moeda_Operacao** | *referência (Cad_Moeda), opcional* | Revisão 30 (documento 156, seção 5.5, Q156-8; D-N463 e D-N465): A moeda em que a operação foi contratada, quando não é o real. |
| **Valor_Operacao_Moeda** | *número, opcional* | Revisão 30 (documento 156, seção 5.5, Q156-8; D-N463 e D-N465): O valor na moeda estrangeira. |
| **Taxa_Cambio_Base** | *número, opcional* | Revisão 30 (documento 156, seção 5.5, Q156-8; D-N463 e D-N465): A taxa aplicada à base, pela regra acima. |
| **Data_Cotacao_Base** | *data, opcional* | Revisão 30 (documento 156, seção 5.5, Q156-8; D-N463 e D-N465): A data da cotação (o dia anterior ao fato gerador, ou a última disponível). |
| **ID_Serie_Cotacao_Base** | *referência (Cad_Serie_Cotacao), opcional* | Revisão 30 (documento 156, seção 5.5, Q156-8; D-N463 e D-N465): A série usada. |
| **Indicador_Fornecimento_Sob_Contrato** | *booleano, opcional* | Revisão 31 (documento 150, seção 3.6, Q150-3; D-N468 e D-N469): Alimentação a pessoa jurídica sob contrato, ainda que não formalizado (art. 397, I). O usuário marca; o Motor lê (critério fornecimento_sob_contrato). Vazio: o Motor trata como falso e avisa quando o cliente é pessoa jurídica. |

*Revisão 3 --- campos novos (documento 33): ID_Documento_Fiscal, Tipo_Operacao, Documento_Consumidor, Nome_Consumidor, ID_Expedicao; campos novos (documento 34): Data_Previsao_Entrega, ID_Tipo_Nota_Debito, ID_Tipo_Nota_Credito, Indicador_Intermediador, ID_Participante_Intermediador, Identificador_Cadastro_Intermediador, ID_Participante_Transportadora, Informacoes_Complementares, Informacoes_Fisco, Numero_Nota_Empenho, Numero_Pedido_Compra, Numero_Contrato, ID_Estado_Saida_Pais, Local_Exportacao, Local_Despacho, ID_Indicador_Operacao, Safra_Cana, Competencia_Cana, Quantidade_Total_Mes_Cana, Quantidade_Total_Anterior_Cana, Quantidade_Total_Geral_Cana, Valor_Fornecimentos_Cana, Valor_Total_Deducoes_Cana, Valor_Liquido_Fornecimentos_Cana; campos novos (documento 35): Indicador_Destinatario; campos novos (documento 44): ID_Entidade_Ligada, Valor_Abatimento_Nao_Tributado, Subserie, ID_Equipamento_Fiscal; campos alterados (documento 33): ID_Participante_Cliente; campos alterados (documento ?): Chave_Acesso; campos alterados (documento 43): ID_Modelo_Documento; campos alterados (documento 41): Finalidade, Protocolo_Autorizacao.*

*Revisão 30 --- campos novos: ID_Moeda_Operacao, Valor_Operacao_Moeda, Taxa_Cambio_Base, Data_Cotacao_Base, ID_Serie_Cotacao_Base, Escriturada_Como_Entrada.*

*Revisão 31 --- campos novos: Indicador_Fornecimento_Sob_Contrato.*

*Comportamento de aplicação (não é um campo novo de dados): pelo mesmo
motor transversal da Fase 0 (seção 10), nenhuma Mov_Nota_Fiscal_Saida
pode ser lançada ou alterada com Data_Emissao dentro de uma competência
já fechada para a Filial (ID_Filial acima) no bloco \"vendas\" --- mesma
consulta a Cad_Periodo_Fechamento_Filial e o mesmo regime fail-closed
descritos em Compras (seção 6 daquele documento). Diferente de Compras
--- onde o próprio pedido já gera compromisso orçamentário desde a
criação ---, aqui o gate age só na nota fiscal de saída (o faturamento e
a baixa física reais): o pedido de venda e a cotação de origem continuam
liberados para criação mesmo com o bloco fechado (exceção explícita, ver
seção 5). Vendas não tem nenhuma validação adicional de pendência no
fechamento --- esse ponto continua exclusivo de Compras.*

Mov_Nota_Fiscal_Saida_Item

Uma linha da nota fiscal de saída.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Nota** | *referência (Mov_Nota_Fiscal_Saida)* | --- |
| **ID_Item_Pedido** | *referência (Mov_Pedido_Venda_Item, opcional)* | Passou a ser opcional nesta revisão, pedido por Alberto: vazio na venda avulsa/balcão (abaixo), mesmo padrão já usado em Compras (ID_Pedido_Item opcional na nota de entrada). Quando preenchido, um mesmo item de pedido pode ser referenciado por mais de uma nota ao longo do tempo (faturamento parcial, seção 5). |
| **ID_Ordem_Servico_Item** | *referência (Mov_Ordem_Servico_Item, Fase 1 --- Produção, opcional)* | Adicionado nesta revisão (7), pedido pela especificação do módulo Fase 1 Produção: preenchido quando a linha fatura material/mão de obra aplicado numa ordem de serviço técnica sobre máquina própria já vendida (fora de garantia, ou dentro dela com mau uso identificado) --- Produção decide o QUE é faturável (Mov_Ordem_Servico_Item.Faturavel), este campo só amarra a linha faturada à nota que a cobrou. Mutuamente exclusivo, na prática, com ID_Item_Pedido e com a venda avulsa: uma linha de nota nasce de um pedido de venda, de uma ordem de serviço, ou avulsa --- nunca mais de uma origem ao mesmo tempo, mesma disciplina de referência única já aplicada às demais origens deste item. |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico)* | --- |
| **Quantidade** | *número* | Pode ser menor que a Quantidade total do item do pedido --- é isso que permite faturamento parcial. |
| **Valor_Unitario** | *número* | --- |
| **Valor_Total** | *número* | O valor do item tal como está na nota --- não recalculado a partir de Quantidade × Valor_Unitario. |
| **ID_CFOP_Saida** | *referência (Cad_CFOP, opcional)* | Alterado na revisão 3 (documento 41). Sugerido pelo Motor de Regras (critério = produto/cliente/destinação), sempre confirmável/alterável. Opcional porque, na NFCom, o item 'sem CST' (indSemCST) não leva CFOP: obrigatório se há CST, proibido se não há (G105a e G105b). |
| **ID_Cst** | *referência (Cad_Cst, Fase 2 --- Contabilidade & Fiscal)* | Renomeado/redirecionado nesta revisão (6) --- antes ID_CST_IBS_CBS, apontando para o domínio cst_ibs_cbs (aposentado, Fase 0 revisão 23). Decidido pelo Motor de Regras no momento do lançamento, considerando cliente e produto como critério. |
| **ID_Cclasstrib** | *referência (Cad_Cclasstrib, Fase 2 --- Contabilidade & Fiscal, opcional)* | Renomeado/redirecionado nesta revisão (6) --- antes ID_ClassTrib, apontando para a extinta Cad_ClassTrib (Fase 0). Idem, decidido pelo Motor de Regras; só preenchido quando ID_Cst for de CBS/IBS. |
| **Numero_Processo_Suframa** | *código (até 20), opcional* | Adicionado nesta revisão (6), pedido pela consolidação da Fase 2 Contabilidade & Fiscal (seção 9): a partir de agosto de 2026, a NF-e passa a exigir o número do processo Suframa por item quando a venda tem como destino a Zona Franca de Manaus/Área de Livre Comércio. |
| **ID_Classificacao_NCM** | *referência (Cad_Classificacao_Mercadoria, opcional)* | Renomeado na revisão 42 (antes ID_NCM, para o extinto Cad_NCM) --- código analítico da nomenclatura NCM. Adicionado nesta revisão, pedido por Alberto: o NCM tal como declarado na nota emitida, congelado no momento da emissão --- não deriva de Cad_Produto_Servico_Dados_Produto.ID_NCM (que tem vigência própria), porque uma correção posterior do cadastro não pode alterar retroativamente o que já foi emitido. Mesmo princípio de snapshot já usado na nota de entrada de Compras (revisão 6). |
| **ID_Unidade_Medida** | *referência (Cad_Unidade_Medida, opcional)* | Idem, congelado no momento da emissão. |
| **ID_NBS** | *referência (Cad_NBS, opcional)* | Preenchido quando o item é serviço --- mesma lógica de snapshot do NCM, aplicada ao NBS. |
| **ID_Atividade_Presuncao** | *referência (Cad_Classe_Sistema, domínio = atividade_presuncao), opcional* | Revisão 28 (documento 127, seção 5.3, Q127-3; documento 152): a atividade de presunção do item (8%, 16%, 32% e assim por diante, pela tabela Cad_Percentual_Presuncao), para o lucro presumido, em caixa ou competência. Preenchido com a sugestão do mapa (Cad_Atividade_Presuncao_Mapa) e confirmado ou trocado pelo usuário ou pelo contador; o valor fica no item, como cópia na emissão (como o NCM e o NBS). Ordem das fontes: a última atividade confirmada para o mesmo produto ou serviço; a linha do mapa mais específica vigente na data da emissão; vazio. Item sem atividade aparece como pendência na apuração do presumido, sem bloquear a emissão. Vale também para o item da NFS-e de aluguel. |
| **ID_Atividade_Simples** | *referência (Cad_Simples_Atividade), opcional* | Revisão 29 (documento 163, seção 4.1, Q163-2): a atividade do Simples Nacional do item (cAtivSN da NT 2026.005: 01 a 04 e 90), sugerida pela versão vigente de Cad_Produto_Servico_Simples do produto e confirmável pelo usuário; preenchida só quando o emitente é optante do Simples ou tem a opção pendente, vazia nos demais. Segue o padrão de ID_Atividade_Presuncao. Os códigos 01 a 04 e 90 entram na carga de Cad_Simples_Atividade se ainda não existirem. |
| **Codigo_Servico_Municipal** | *código (até 20), opcional* | Preenchido quando o item é serviço --- snapshot do código municipal usado na emissão; Cad_Produto_Servico_Codigo_Municipal (Fase 0) pode mudar por atualização da lista do município, sem afetar notas já emitidas. |
| **Descricao_Produto_Servico** | *texto, opcional* | A descrição tal como consta na nota emitida --- não precisa ser idêntica a Cad_Produto_Servico.Descricao, que pode ser renomeada depois sem afetar o que já foi emitido. |
| **Numero_Item** | *número* | Adicionado na revisão 12 (Bloco 2). nItem --- sequencial dentro da nota. |
| **Valor_Desconto_Item** | *número, opcional* | Adicionado na revisão 12 (Bloco 2). Revisão 30 (documento 156, seção 5.7, Q156-13): passa a ser só o desconto incondicional; o condicional fica em Valor_Desconto_Condicional_Item. |
| **Valor_Desconto_Condicional_Item** | *número, opcional* | Revisão 30 (documento 156, seção 5.7, Q156-13; D-N463 e D-N465): O desconto concedido sob condição, que não reduz a base (integra, art. 12, § 1º, III da LC 214). Revisão 30 (documento 156, seção 5.7, Q156-13): Valor_Desconto_Item passa a significar só o incondicional (consta do documento fiscal e não depende de evento posterior, § 3º). Se o leiaute da NF-e não separar os dois, o campo é controle do ERP e não vai no XML (Q156-E1). |
| **Valor_Frete_Item** | *número, opcional* | Adicionado na revisão 12 (Bloco 2). Rateio do frete do cabeçalho. |
| **Valor_Seguro_Item** | *número, opcional* | Adicionado na revisão 12 (Bloco 2). |
| **Valor_Outras_Despesas_Item** | *número, opcional* | Adicionado na revisão 12 (Bloco 2). |
| **ID_Origem_Mercadoria** | *referência (Cad_Classe_Sistema, domínio = origem_mercadoria)* | Adicionado na revisão 12 (Bloco 2). Cópia do produto. |
| **ID_Cest** | *referência (Cad_Cest, opcional)* | Adicionado na revisão 12 (Bloco 2). Cópia. |
| **ID_Ex_Tipi** | *referência (Cad_NCM_Ex_Tipi, opcional)* | Adicionado na revisão 12 (Bloco 2). Cópia. |
| **Gtin** | *código (até 14), opcional* | Adicionado na revisão 12 (Bloco 2). Cópia. |
| **ID_Beneficio_Fiscal_Icms** | *referência (Cad_Beneficio_Fiscal_Icms, opcional)* | Adicionado na revisão 12 (Bloco 2). cBenef --- exigido por várias UFs quando o CST indica isenção, redução ou diferimento. |
| **ID_Servico_Tributacao** | *referência (Cad_Servico_Tributacao_Nacional, opcional)* | Adicionado na revisão 12 (Bloco 2). cTribNac --- só em item de serviço. |
| **Local_Na_Contratante** | *booleano* | Adicionado na revisão 12 (Bloco 2). Padrão sim. Sim = o local é o endereço do contratante; não = o local está em ID_Local_Operacao. |
| **ID_Endereco_Contratante** | *referência (Cad_Participante_Endereco, opcional)* | Adicionado na revisão 12 (Bloco 2). A versão do endereço do contratante usada; preenchida quando Local_Na_Contratante = sim. |
| **ID_Local_Operacao** | *referência (Cad_Local_Operacao, opcional)* | Adicionado na revisão 12 (Bloco 2). Obrigatória quando Local_Na_Contratante = não; vazia quando = sim. |
| **ID_Criterio_Local_Operacao** | *referência (Cad_Classe_Sistema, domínio = criterio_local_operacao, opcional)* | Adicionado na revisão 12 (Bloco 2). Só nas notas. A regra aplicada: entrega do bem, domicílio do adquirente, local do imóvel, local da prestação, entre outras. |
| **ID_Municipio_Incidencia_Ibs** | *referência (Cad_Municipio, opcional)* | Adicionado na revisão 12 (Bloco 2). Só nas notas. O município de destino do IBS, e, por ele, a UF. |
| **ID_Municipio_Incidencia_Iss** | *referência (Cad_Municipio, opcional)* | Adicionado na revisão 12 (Bloco 2). Só nas notas. Na NFS-e de saída, o cLocIncid devolvido pelo ambiente nacional. |
| **ID_Empreendimento** | *referência (Cad_Empreendimento_Imobiliario, opcional)* | Adicionado na revisão 12 (Bloco 2). O empreendimento a que a compra, a venda ou o crédito pertence. Vazio na maior parte das empresas, que não têm empreendimento. |
| **ID_Habilitacao** | *referência (Cad_Habilitacao_Regime_Especial, opcional)* | Adicionado na revisão 12 (Bloco 2). Herdada do pedido de venda; citada na nota. |
| **Tipo_Comercializacao_Rural** | *enumeração {producao_propria, producao_isenta_lei_13606, entidade_paa, mercado_externo}, opcional* | Adicionado na revisão 14 (Bloco 4). O tipo de comercialização da produção rural do item, que alimenta o R-2050 da EFD-Reinf (Contabilidade & Fiscal, seção 21.3.3): produção própria, produção isenta pela Lei 13.606/2018, venda a entidade do Programa de Aquisição de Alimentos ou mercado externo. Vazio quando o item não é produção rural. |
| **ID_Imovel** | *referência (Cad_Imovel, opcional)* | Novo na revisão 3 (documento 33). O imóvel objeto do item na NFS-e de aluguel e de venda de imóvel. |
| **ID_Unidade_Tributavel** | *referência (Cad_Unidade_Medida, opcional)* | Novo na revisão 3 (documento 34). det/prod/uTrib: unidade tributável, que pode diferir da comercial (NCM com unidade de medida própria). |
| **Quantidade_Tributavel** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/qTrib: quantidade tributável (0 a 4 decimais). |
| **Valor_Unitario_Tributavel** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vUnTrib: valor unitário de tributação (até 10 decimais). |
| **Gtin_Tributavel** | *código (até 14), opcional* | Novo na revisão 3 (documento 34). det/prod/cEANTrib: GTIN da unidade tributável, diferente de Gtin (cEAN); a NT 2021.003 valida os dois contra o Cadastro Centralizado (grupo V a partir de 01/09/2027). |
| **Indicador_Bem_Movel_Usado** | *booleano, opcional* | Novo na revisão 3 (documento 34). det/prod/indBemMovelUsado: fornecimento de bem móvel usado (RTC). |
| **Numero_Pedido_Cliente** | *código (até 15), opcional* | Novo na revisão 3 (documento 34). det/prod/xPed: pedido de compra do cliente, para controle do B2B. |
| **Item_Pedido_Cliente** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/nItemPed: número do item do pedido de compra do cliente. |
| **Numero_Fci** | *código (até 36), opcional* | Novo na revisão 3 (documento 34). det/prod/nFCI: número de controle da Ficha de Conteúdo de Importação. |
| **Indicador_Doacao** | *booleano, opcional* | Novo na revisão 3 (documento 34). det/imposto/IBSCBS/indDoacao: a operação do item é de doação (decidido pelo tpDoacao do cClassTrib). |
| **Tipo_Onerosidade** | *enumeração {oneroso, nao_oneroso, equiparado, valor_inferior_mercado}, opcional* | Revisão 19 (D-N285 a D-N290): Decidido pelo Motor a partir da regra e da vinculação do participante (D-N285). Revisão 30 (documento 156, seção 3.4, Q156-2): valor_inferior_mercado é o item com valor, mas abaixo do valor de mercado, para participante com regra equiparado_art5 ou parte relacionada; o Motor compara Valor_Praticado (em Mov_Nota_Fiscal_Saida_Item_Equiparada) com o valor de mercado apurado. |
| **Opcao_Doacao_Cbs** | *enumeração {tributar, anular_creditos}, opcional* | Revisão 19 (D-N285 a D-N290): Na doação, a opção do art. 6º, § 2º. Sem opção a doação fica pendente e **não emite** (nada assumido). Não se aplica às operações do art. 5º, I, III e IV, nem ao FAR (§ 3º). |
| **Origem_Opcao_Doacao** | *enumeração {cadastro_participante, perguntado}, opcional* | Revisão 19 (D-N285 a D-N290): De onde veio a opção: do cadastro do participante ou da pergunta ao usuário (D-N286). |
| **ID_Usuario_Confirmacao** | *referência (Cad_Usuario, opcional)* | Revisão 19 (D-N285 a D-N290): Quem respondeu à pergunta; exige a ação aprovar (D-N287). |
| **Data_Hora_Confirmacao** | *data/hora, opcional* | Revisão 19 (D-N285 a D-N290): Quando respondeu. |
| **Informacoes_Adicionais_Item** | *texto, opcional* | Novo na revisão 3 (documento 34). det/infAdProd: informações adicionais do produto (até 500 posições). |
| **Percentual_Devolvido** | *número, opcional* | Novo na revisão 3 (documento 34). det/impostoDevol/pDevol: percentual da mercadoria devolvida. |
| **Valor_Ipi_Devolvido** | *número, opcional* | Novo na revisão 3 (documento 34). det/impostoDevol/IPI/vIPIDevol: valor do IPI devolvido. |
| **Valor_Unitario_Liquido** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vUnComLiq (NT 2026.008): valor unitário líquido, sem IBS, CBS e Imposto Seletivo. Produção em 03/11/2026. |
| **Valor_Total_Liquido** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vProdLiq (NT 2026.008): valor total líquido do item; o total da nota (vProdLiqTot) é derivado. |
| **ID_Indicador_Operacao** | *referência (Cad_Indicador_Operacao, opcional)* | Alterado na revisão 3 (documento 41). cIndOp (P-19 do doc 34): passa a apontar para o catálogo Cad_Indicador_Operacao, no lugar do domínio indicador_operacao_nfse de Cad_Classe_Sistema. O critério de local (ID_Criterio_Local_Operacao) deixa de ser digitado e é derivado do código. |
| **Codigo_Tipo_Credito_Presumido_Zfm** | *código (1), opcional* | Novo na revisão 3 (documento 34). det/prod/tpCredPresIBSZFM: classificação para subapuração do IBS na ZFM (0 a 4, NT 2025.002). |
| **Numero_Recopi** | *código (20), opcional* | Novo na revisão 3 (documento 34). det/prod/nRECOPI: número do RECOPI (papel imprensa) (D-N12). |
| **Veiculo_Tipo_Operacao** | *enumeração {outros, venda_concessionaria, faturamento_direto, venda_direta}, opcional* | Novo na revisão 3 (documento 34). veicProd/tpOp: 1 venda concessionária, 2 faturamento direto, 3 venda direta, 0 outros (D-N12). |
| **Veiculo_Chassi** | *código (17), opcional* | Novo na revisão 3 (documento 34). veicProd/chassi: chassi (VIN) do veículo novo. |
| **Veiculo_Codigo_Cor** | *código (até 4), opcional* | Novo na revisão 3 (documento 34). veicProd/cCor: cor do veículo (código da montadora). |
| **Veiculo_Descricao_Cor** | *texto, opcional* | Novo na revisão 3 (documento 34). veicProd/xCor: descrição da cor (até 40). |
| **Veiculo_Potencia_Cv** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/pot: potência máxima do motor em cavalo-vapor. |
| **Veiculo_Cilindrada_Cc** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/cilin: capacidade volumétrica do motor em cm³. |
| **Veiculo_Peso_Liquido** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/pesoL: peso líquido. |
| **Veiculo_Peso_Bruto** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/pesoB: peso bruto. |
| **Veiculo_Numero_Serie** | *código (até 9), opcional* | Novo na revisão 3 (documento 34). veicProd/nSerie: série. |
| **Veiculo_Codigo_Combustivel** | *código (até 2), opcional* | Novo na revisão 3 (documento 34). veicProd/tpComb: tipo de combustível (tabela RENAVAM). |
| **Veiculo_Numero_Motor** | *código (até 21), opcional* | Novo na revisão 3 (documento 34). veicProd/nMotor: número do motor. |
| **Veiculo_Capacidade_Tracao** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/CMT: capacidade máxima de tração em toneladas (4 decimais). |
| **Veiculo_Distancia_Eixos** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/dist: distância entre eixos. |
| **Veiculo_Ano_Modelo** | *código (4), opcional* | Novo na revisão 3 (documento 34). veicProd/anoMod: ano modelo de fabricação. |
| **Veiculo_Ano_Fabricacao** | *código (4), opcional* | Novo na revisão 3 (documento 34). veicProd/anoFab: ano de fabricação. |
| **Veiculo_Tipo_Pintura** | *código (1), opcional* | Novo na revisão 3 (documento 34). veicProd/tpPint: tipo de pintura. |
| **Veiculo_Codigo_Tipo** | *código (até 2), opcional* | Novo na revisão 3 (documento 34). veicProd/tpVeic: tipo de veículo (tabela RENAVAM). |
| **Veiculo_Codigo_Especie** | *código (até 2), opcional* | Novo na revisão 3 (documento 34). veicProd/espVeic: espécie de veículo (tabela RENAVAM). |
| **Veiculo_Vin_Remarcado** | *booleano, opcional* | Novo na revisão 3 (documento 34). veicProd/VIN: R = chassi remarcado, N = normal. |
| **Veiculo_Condicao** | *enumeração {acabado, inacabado, semi_acabado}, opcional* | Novo na revisão 3 (documento 34). veicProd/condVeic: 1 acabado, 2 inacabado, 3 semi-acabado. |
| **Veiculo_Codigo_Marca_Modelo** | *código (até 6), opcional* | Novo na revisão 3 (documento 34). veicProd/cMod: código marca/modelo (tabela RENAVAM). |
| **Veiculo_Codigo_Cor_Denatran** | *código (2), opcional* | Novo na revisão 3 (documento 34). veicProd/cCorDENATRAN: cor segundo o pré-cadastro do DENATRAN (01 a 16). |
| **Veiculo_Lotacao** | *número, opcional* | Novo na revisão 3 (documento 34). veicProd/lota: lotação máxima de passageiros sentados, inclusive o motorista. |
| **Veiculo_Restricao** | *enumeração {nao_ha, alienacao_fiduciaria, arrendamento_mercantil, reserva_dominio, penhor, outras}, opcional* | Novo na revisão 3 (documento 34). veicProd/tpRest: restrição sobre o veículo (0, 1, 2, 3, 4 e 9). |
| **Medicamento_Registro_Anvisa** | *código (até 13), opcional* | Novo na revisão 3 (documento 34). med/cProdANVISA: registro na ANVISA ou o literal ISENTO. |
| **Medicamento_Motivo_Isencao** | *texto, opcional* | Novo na revisão 3 (documento 34). med/xMotivoIsencao: decisão que isenta o medicamento de registro na ANVISA (até 255). |
| **Medicamento_Preco_Maximo_Consumidor** | *número, opcional* | Novo na revisão 3 (documento 34). med/vPMC: preço máximo ao consumidor. |
| **Arma_Tipo** | *enumeração {uso_permitido, uso_restrito}, opcional* | Novo na revisão 3 (documento 34). arma/tpArma: 0 uso permitido, 1 uso restrito. |
| **Arma_Numero_Serie** | *código (até 15), opcional* | Novo na revisão 3 (documento 34). arma/nSerie: número de série da arma. |
| **Arma_Numero_Cano** | *código (até 15), opcional* | Novo na revisão 3 (documento 34). arma/nCano: número de série do cano. |
| **Arma_Descricao** | *texto, opcional* | Novo na revisão 3 (documento 34). arma/descr: descrição completa (calibre, marca, capacidade, funcionamento, comprimento). |
| **Combustivel_Codigo_Anp** | *código (até 9), opcional* | Novo na revisão 3 (documento 34). comb/cProdANP: código de produto da ANP (SIMP). |
| **Combustivel_Descricao_Anp** | *texto, opcional* | Novo na revisão 3 (documento 34). comb/descANP: descrição do produto conforme a ANP (2 a 95). |
| **Combustivel_Percentual_Glp** | *número, opcional* | Novo na revisão 3 (documento 34). comb/pGLP: percentual do GLP derivado do petróleo (cProdANP 210203001). |
| **Combustivel_Percentual_Gas_Natural_Nacional** | *número, opcional* | Novo na revisão 3 (documento 34). comb/pGNn: percentual de gás natural nacional no GLP. |
| **Combustivel_Percentual_Gas_Natural_Importado** | *número, opcional* | Novo na revisão 3 (documento 34). comb/pGNi: percentual de gás natural importado no GLP. |
| **Combustivel_Valor_Partida** | *número, opcional* | Novo na revisão 3 (documento 34). comb/vPart: valor de partida por quilograma, sem ICMS (GLP). |
| **Combustivel_Codigo_Codif** | *código (até 21), opcional* | Novo na revisão 3 (documento 34). comb/CODIF: código de autorização ou registro do CODIF, quando a UF o usa. |
| **Combustivel_Quantidade_Temperatura_Ambiente** | *número, opcional* | Novo na revisão 3 (documento 34). comb/qTemp: quantidade faturada à temperatura ambiente. |
| **ID_Estado_Consumo_Combustivel** | *referência (Cad_Estado, opcional)* | Novo na revisão 3 (documento 34). comb/UFCons: UF de consumo. |
| **Combustivel_Cide_Base** | *número, opcional* | Novo na revisão 3 (documento 34). comb/CIDE/qBCProd: base da CIDE (quantidade comercializada). |
| **Combustivel_Cide_Aliquota** | *número, opcional* | Novo na revisão 3 (documento 34). comb/CIDE/vAliqProd: alíquota da CIDE em reais. |
| **Combustivel_Cide_Valor** | *número, opcional* | Novo na revisão 3 (documento 34). comb/CIDE/vCIDE: valor da CIDE. |
| **Combustivel_Numero_Bico** | *código (até 3), opcional* | Novo na revisão 3 (documento 34). comb/encerrante/nBico: bico utilizado no abastecimento. |
| **Combustivel_Numero_Bomba** | *código (até 3), opcional* | Novo na revisão 3 (documento 34). comb/encerrante/nBomba: bomba a que o bico está ligado. |
| **Combustivel_Numero_Tanque** | *código (até 3), opcional* | Novo na revisão 3 (documento 34). comb/encerrante/nTanque: tanque a que o bico está ligado. |
| **Combustivel_Encerrante_Inicial** | *número, opcional* | Novo na revisão 3 (documento 34). comb/encerrante/vEncIni: valor do encerrante no início do abastecimento. |
| **Combustivel_Encerrante_Final** | *número, opcional* | Novo na revisão 3 (documento 34). comb/encerrante/vEncFin: valor do encerrante no fim do abastecimento. |
| **Combustivel_Percentual_Biodiesel** | *número, opcional* | Novo na revisão 3 (documento 34). comb/pBio: percentual de mistura do biodiesel (B100) no óleo diesel B. |
| **Combustivel_Indicador_Importado** | *booleano, opcional* | Novo na revisão 3 (documento 34). comb/origComb/indImport: 0 nacional, 1 importado. |
| **ID_Estado_Origem_Combustivel** | *referência (Cad_Estado, opcional)* | Novo na revisão 3 (documento 34). comb/origComb/cUFOrig: UF de origem do produtor ou do importador. |
| **Combustivel_Percentual_Origem** | *número, opcional* | Novo na revisão 3 (documento 34). comb/origComb/pOrig: percentual originário para a UF. |
| **Natureza_Operacao** | *texto, opcional* | Novo na revisão 3 (documento 44). Natureza da operação do item (C170.COD_NAT); o 0400 sai dos textos distintos. Substitui o ID_Natureza_Operacao do doc 44 (ver notes). |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, opcional)* | Novo na revisão 3 (documento 44). Conta contábil de receita do item (COD_CTA). |
| **ID_Tipo_Receita_Comunicacao** | *referência (Cad_Classe_Sistema, domínio = tipo_receita_comunicacao_efd, opcional)* | Novo na revisão 3 (documento 44). Tipo de receita de comunicação (D600.IND_REC); sugerido automaticamente pelos campos da NFCom. |
| **ID_Classificacao_Item_Utilidade** | *referência (Cad_Classe_Sistema, domínio = classificacao_item_utilidade, opcional)* | Novo na revisão 3 (documento 44). Classificação do item de serviço de comunicação ou utilidade (D601/D605.COD_CLASS, Tabela 4.4.1). |
| **Tipo_Servico_Agencia** | *enumeração {intermediacao, fornecimento_direto}, opcional* | Revisão 31 (documento 150, seção 6.4, Q150-11; D-N468 e D-N469): Copiado do cadastro na emissão e editável: o serviço da agência de turismo (art. 417, § 1º). Decide a base: com a dedução do art. 418, I, ou sem dedução (art. 418, II). |
| **Data_Fato_Gerador** | *data, opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): A data que o ERP usou. Vazia quando não há linha de regra vigente (e então há aviso). |
| **Criterio_Data_Fato_Gerador** | *enumeração {data_previsao_entrega, data_emissao_documento, data_entrega_comprovada, data_inicio_transporte, data_termino_transporte, data_termino_servico, data_ato, data_pagamento, data_emissao_fatura, data_liberacao_aduaneira, data_constatacao, data_aquisicao}, opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): De onde a data veio. Com prova em contrário da data prevista (Decreto, art. 11, § 8º), passa a data_entrega_comprovada e o usuário informa a data. |
| **ID_Regra_Fato_Gerador** | *referência (Cad_Regra_Fato_Gerador), opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): A versão da regra usada. |

*Revisão 3 --- campos novos (documento 33): ID_Imovel; campos novos (documento 34): ID_Unidade_Tributavel, Quantidade_Tributavel, Valor_Unitario_Tributavel, Gtin_Tributavel, Indicador_Bem_Movel_Usado, Numero_Pedido_Cliente, Item_Pedido_Cliente, Numero_Fci, Indicador_Doacao, Informacoes_Adicionais_Item, Percentual_Devolvido, Valor_Ipi_Devolvido, Valor_Unitario_Liquido, Valor_Total_Liquido, Codigo_Tipo_Credito_Presumido_Zfm, Numero_Recopi, Veiculo_Tipo_Operacao, Veiculo_Chassi, Veiculo_Codigo_Cor, Veiculo_Descricao_Cor, Veiculo_Potencia_Cv, Veiculo_Cilindrada_Cc, Veiculo_Peso_Liquido, Veiculo_Peso_Bruto, Veiculo_Numero_Serie, Veiculo_Codigo_Combustivel, Veiculo_Numero_Motor, Veiculo_Capacidade_Tracao, Veiculo_Distancia_Eixos, Veiculo_Ano_Modelo, Veiculo_Ano_Fabricacao, Veiculo_Tipo_Pintura, Veiculo_Codigo_Tipo, Veiculo_Codigo_Especie, Veiculo_Vin_Remarcado, Veiculo_Condicao, Veiculo_Codigo_Marca_Modelo, Veiculo_Codigo_Cor_Denatran, Veiculo_Lotacao, Veiculo_Restricao, Medicamento_Registro_Anvisa, Medicamento_Motivo_Isencao, Medicamento_Preco_Maximo_Consumidor, Arma_Tipo, Arma_Numero_Serie, Arma_Numero_Cano, Arma_Descricao, Combustivel_Codigo_Anp, Combustivel_Descricao_Anp, Combustivel_Percentual_Glp, Combustivel_Percentual_Gas_Natural_Nacional, Combustivel_Percentual_Gas_Natural_Importado, Combustivel_Valor_Partida, Combustivel_Codigo_Codif, Combustivel_Quantidade_Temperatura_Ambiente, ID_Estado_Consumo_Combustivel, Combustivel_Cide_Base, Combustivel_Cide_Aliquota, Combustivel_Cide_Valor, Combustivel_Numero_Bico, Combustivel_Numero_Bomba, Combustivel_Numero_Tanque, Combustivel_Encerrante_Inicial, Combustivel_Encerrante_Final, Combustivel_Percentual_Biodiesel, Combustivel_Indicador_Importado, ID_Estado_Origem_Combustivel, Combustivel_Percentual_Origem; campos novos (documento 41): ID_Indicador_Operacao; campos novos (documento 44): Natureza_Operacao, ID_Conta_Contabil, ID_Tipo_Receita_Comunicacao, ID_Classificacao_Item_Utilidade; campos alterados (documento 41): ID_CFOP_Saida.*

*Revisão 19 --- campos novos: Tipo_Onerosidade, Opcao_Doacao_Cbs, Origem_Opcao_Doacao, ID_Usuario_Confirmacao, Data_Hora_Confirmacao.*

*Revisão 28 --- campos novos: ID_Atividade_Presuncao.*

*Revisão 29 --- campos novos: ID_Atividade_Simples.*

*Revisão 30 --- campos novos: Valor_Desconto_Condicional_Item; campos alterados: Valor_Desconto_Item; valores de enumeração novos: Tipo_Onerosidade (+valor_inferior_mercado).*

*Revisão 31 --- campos novos: Tipo_Servico_Agencia, Data_Fato_Gerador, Criterio_Data_Fato_Gerador, ID_Regra_Fato_Gerador.*

*Comportamento de aplicação (não é um campo novo de dados): emitir a
nota (Status=emitida) gera, para cada linha COM ID_Item_Pedido
preenchido, um Mov_Estoque_Movimento com Origem_Tipo=pedido_venda e
ID_Origem=ID_Item_Pedido (Estoque, revisão 6) --- a baixa física
propriamente dita ---, muda a(s) Mov_Estoque_Reserva correspondente(s)
para Status=baixada (seção 6), e apensa um novo registro em
Mov_Pedido_Venda_Item_Status_Historico (faturado_parcial ou
faturado_total, conforme o acumulado faturado contra aquele item bata ou
não com a Quantidade total --- seção 5). As três consequências acontecem
juntas, na mesma emissão, sem tabela de orquestração própria --- cada
módulo só reage ao evento pelo mesmo padrão de referência genérica já
usado em todo este dicionário.*

*Venda avulsa/balcão, incorporada nesta revisão a pedido de Alberto
(\"não é necessário abrir um pedido, pode fazer a emissão da nota
diretamente com a inclusão dos itens e baixa do estoque\"): dispensa
cotação e pedido prévios --- a nota fiscal de saída é emitida
diretamente, com os itens incluídos na própria nota e a baixa física
imediata. Quando ID_Item_Pedido está vazio, a baixa gerada em
Mov_Estoque_Movimento usa Origem_Tipo=venda_avulsa (Fase 1 --- Estoque,
revisão 7), ID_Origem=ID_Item (o próprio item da nota) --- sem reserva
de estoque prévia, sem histórico de status por item (não existe
Mov_Pedido_Venda_Item para apensar) e sem comissão/royalty calculados
(não houve cotação para o Motor de Regras resolver): uma venda avulsa é,
por definição, mais simples que o ciclo completo de cotação, e não
deveria ser usada quando esses controles importam.*

Campos fiscais do documento, local da operação e habilitação do cliente
(revisão 12)

Hoje a mesma entidade recebe NF-e, CT-e de frete e NFS-e sem distinguir
o modelo, e a situação se resume a lançada, recusada e cancelada. Os
campos abaixo entram dos dois lados, simetricamente (o padrão já adotado
entre Compras e CRM & Vendas). O Status que existe hoje continua sendo o
andamento interno da nota; a Situacao_Documento é a situação fiscal.

Por decisão de Alberto, o pedido pergunta onde o serviço vai ser
prestado ou o material entregue, linha a linha; no pedido de venda o
contratante é o cliente. Se o local não é o do cliente, o usuário
escolhe um local já cadastrado (Cad_Local_Operacao, Fase 0) ou cadastra
na hora; se o local é uma obra, o código da obra e o CIB são
obrigatórios. Na nota de saída o item copia o local, o critério do art.
11 da LC 214 aplicado pelo Motor de Regras e os municípios de incidência
do IBS e do ISS (na NFS-e, o cLocIncid devolvido pelo ambiente
nacional).

Nas vendas, o raciocínio é o mesmo, na linha: o cliente informa em que
vai aplicar o item e qual habilitação vale. Alberto confirmou que
Mov_Pedido_Venda_Item e Mov_Nota_Fiscal_Saida_Item ganham ID_Habilitacao
(opcional), com o titular igual ao destinatário, para a nota poder citar
a habilitação e suspender a contribuição.

8\. Devolução de Cliente

Mesmo padrão de Compras (seção 8 daquele documento) --- cabeçalho e item
de devolução, referenciando a nota fiscal de saída original. É a
terceira das \"três devoluções\" já citadas desde a revisão 4 do módulo
de Estoque (Produção, Compra, Cliente): fisicamente, gera um
Mov_Estoque_Movimento com Origem_Tipo=movimento_estoque, ID_Origem=o
ID_Movimento da saída original --- mesma auto-referência já usada nas
outras duas, sem nenhuma mudança estrutural adicional no Estoque.

Mov_Devolucao_Venda

O cabeçalho de uma devolução de cliente.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Devolucao** | *identificador* | --- |
| **ID_Nota** | *referência (Mov_Nota_Fiscal_Saida)* | A nota de saída original --- precisa ter Status=emitida. |
| **Data_Devolucao** | *data* | --- |
| **ID_Motivo** | *referência (Cad_Classe_Sistema, domínio motivo_devolucao)* | Adicionado nesta revisão, pedido por Alberto: \"o motivo de devolução tem que ser normatizado, preciso ter um cadastro para isto\" --- o motivo deixou de ser texto livre, mesmo cadastro genérico de domínio já usado em outros pontos do Fase 0, e o mesmo domínio agora também usado por Mov_Devolucao_Compra (revisão 6). |
| **Motivo_Complemento** | *texto, opcional* | Adicionado nesta revisão: \"tem que ter um campo digitável para complemento dos motivos da devolução\" --- complemento livre, para detalhar o caso específico além do motivo normatizado. |
| **Numero_Nota_Devolucao** | *código (até 15), opcional* | O documento fiscal que acompanha a mercadoria devolvida --- fora do escopo deste dicionário além desta referência. Desmembrado na revisão 10. |
| **Serie_Nota_Devolucao** | *código (até 3), opcional* | --- |
| **Chave_Acesso_Devolucao** | *código (44), opcional* | Adicionado nesta revisão: a nota de devolução é ela mesma uma NFe própria, também precisa da chave de acesso. |
| **ID_Cbs_Ajuste_Operacao** | *referência (Mov_Cbs_Ajuste_Operacao), opcional* | Revisão 31 (documento 157, seção 4.6, Q157-2; D-N466 e D-N469): A devolução física liga ao ajuste fiscal. O documento de devolução pode vir do cliente (nota de entrada) ou ser emitido por nós; quem emite está em Mov_Cbs_Ajuste_Operacao.Papel_Emitente_Documento. |

*Revisão 31 --- campos novos: ID_Cbs_Ajuste_Operacao.*

Mov_Devolucao_Venda_Item

Uma linha devolvida --- nunca maior que a quantidade/valor originais da
nota.

*Vigência: não.*

  -------------------------- ------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                 **Descrição / regra**

  **ID_Item**                *identificador*                 ---

  **ID_Devolucao**           *referência                     ---
                             (Mov_Devolucao_Venda)*          

  **ID_Nota_Item**           *referência                     ---
                             (Mov_Nota_Fiscal_Saida_Item)*   

  **Quantidade_Devolvida**   *número*                        Pode ser menor que a Quantidade do item
                                                             na nota original --- devolução parcial.

  **Valor_Devolvido**        *número*                        O valor tal como emitido na nota fiscal
                                                             de devolução --- nunca recalculado a
                                                             partir de Quantidade_Devolvida (mesmo
                                                             princípio de fidelidade à nota, seção
                                                             7).
  -------------------------- ------------------------------- ----------------------------------------

*Uma devolução aceita apensa devolvido_parcial ou devolvido_total em
Mov_Pedido_Venda_Item_Status_Historico (seção 5), pelo mesmo critério de
acumulado já usado para faturamento --- não se aplica a uma venda
avulsa, que não tem Mov_Pedido_Venda_Item para apensar (seção 7).*

9\. Comissão, Royalty e Provisão Contábil

Comissão e royalty, nesta revisão, ganharam registro contábil e
visibilidade financeira, mesmo sem o repasse efetivo ainda modelado (ver
seção 1) --- dois pontos pedidos explicitamente por Alberto depois da
entrega da Revisão 1.

Provisão contábil: no instante em que o pedido de venda nasce
(Mov_Pedido_Venda, seção 5), o total estimado de comissão (soma, por
item, de Mov_Pedido_Venda_Item_Comissao.Percentual_Comissao_Estimado ×
Valor_Total do item, por beneficiário) e de royalty
(Mov_Pedido_Venda_Item.Percentual_Royalty_Estimado × Valor_Total) gera
um lançamento contábil de provisão ---
Mov_Lote_Lancamento.Origem_Tipo=provisao_comissao_venda (Fase 0, revisão
13), ID_Origem=ID_Item de Mov_Pedido_Venda_Item. Alberto confirmou esse
fluxo diretamente: \"esta estimativa deverá ser lançado na contabilidade
como provisão, e no momento do recebimento efetivo reverter provisão
conta obrigações a pagar, neste momento entra no financeiro\". É só o
lançamento de provisão em si (débito de despesa, crédito de provisão)
--- a conta contábil de cada lançamento continua resolvida pela mesma
Cad_Destinacao/Cad_Motor_Regra genéricos do Fase 0, sem estrutura nova
aqui.

Reversão: no momento do recebimento efetivo do cliente, a provisão é
revertida e uma obrigação a pagar nasce --- ao beneficiário da comissão,
ou ao licenciante do royalty. Corrigido nesta revisão (9): este
parágrafo ainda apontava para uma \"Contas a Receber, Fase 2, ainda não
especificada\" --- aquele módulo já foi construído (Fase 2 --- Contas a
Pagar/Receber) e já cobre exatamente este ponto, seção 7 (Reversão de
Provisão de Comissão/Royalty em Obrigação a Pagar): a reversão acontece
PROPORCIONALMENTE a cada liquidação (baixa, aplicação de crédito ou
encontro de contas) do título a receber nascido desta venda, confirmado
por Alberto --- nenhuma estrutura nova aqui, só a referência cruzada que
faltava.

Estimativa para a Tesouraria: a mesma estimativa de comissão/royalty,
por pedido em aberto, precisa aparecer para a Tesouraria como uma
PREVISÃO de contas a pagar --- nunca um contas a pagar efetivo, porque a
obrigação real só nasce no recebimento (acima). Alberto foi explícito
quanto a essa distinção: \"esta informação tem que aparecer na
tesouraria como estimativa de contas a pagar, não efetivamente um a
pagar, mas uma estimativa futura\". Como o módulo de Tesouraria ainda
não foi especificado, este dicionário só deixa o gancho: a mesma leitura
usada para gerar a provisão contábil (soma de
Percentual_Comissao_Estimado/Percentual_Royalty_Estimado × Valor_Total,
por pedido em aberto) é a fonte natural de um futuro painel prospectivo
de Tesouraria --- sem tabela nova aqui, e sem compromisso de layout
desse painel, que é decisão de quando o módulo for especificado.

Autoatendimento --- lista de preço fixa e checagem de estoque:
adicionado nesta revisão (4), pedido por Alberto sobre o autoatendimento
pelo Portal do Cliente (Fase 4, gancho já registrado --- seção 1 e
Notas). Ao criar a cotação pré-preenchida (Canal_Origem=autoatendimento,
seção 2), a aplicação consulta o saldo disponível (Estoque, mesma
leitura derivada já usada em Mov_Estoque_Reserva/saldo, nunca um campo
armazenado à parte) para o produto/local pedido: havendo estoque, a
cotação nasce direto com Status=aceita, sem régua de aprovação (seção
4), e o vendedor é herdado de
Cad_Participante.ID_Participante_Vendedor_Principal do cliente quando
existir --- podendo, mesmo assim, ficar sem vendedor atribuído (a
aprovação/estoque e a atribuição de vendedor são decisões
independentes). Não havendo estoque, Alberto foi explícito: \"cai na
fila, pois precisa ver se vai valer a pena produzir ou comprar\" --- a
cotação fica pendente (Status=aberta) e cai na mesma fila única (seção 2
e 4) SE o cliente não tiver vendedor principal; havendo vendedor
principal, é direcionada a ele mesmo sem estoque (\"quando tem
\[vendedor\], vai ser direcionada ao vendedor\") --- só cai na fila
geral quando não há vendedor nenhum já vinculado ao cliente.

Sinalização para a Expedição: Mov_Pedido_Venda_Item_Entrega_Programada
(seção 5) já carrega, por natureza, a data, a quantidade, o local e a
transportadora de referência para cada saída programada --- o dado que a
Expedição vai precisar quando for especificada, como Alberto pediu
(\"tem que sinalizar para a expedição que isto tem uma previsão de saída
desta mercadoria para as datas programadas na venda\"). Quando o item
depende de produção ainda não concluída ou de personalização, o
histórico de status (Mov_Pedido_Venda_Item_Status_Historico, seção 5)
ganhou nesta revisão o valor aguardando_producao_personalizacao --- um
sinalizador explícito de que a saída programada não pode ser cumprida
ainda, sem modelar o processo de produção em si (que continua dependendo
do módulo de Produção, Fase 3).

Frete --- negociação, estimativa e valor definitivo: a revisão 3 separou
com cuidado três momentos distintos, todos pedidos por Alberto. Na
cotação/pedido (seção 2 e 5), Modalidade_Cobranca_Frete decide se o
frete é cobrado do cliente ou não, e
ID_Participante_Transportadora_Referencia serve só de base de custo para
a estimativa --- nunca a transportadora que vai executar de fato (essa
decisão é da Expedição/Compras, ver Notas). Quando a modalidade é
valor_fixo, Valor_Frete_Negociado é o valor cobrado do cliente, mantido
tal como negociado, independentemente do que a Mlegate vier a pagar de
fato à transportadora real (fidelidade ao valor real, seção 2) --- o que
pode variar é só o CUSTO pago à transportadora, um conceito totalmente
separado, fora do escopo deste módulo. Quando a modalidade é
a_apurar_no_envio, não há valor fechado na venda: o valor real do frete
só se confirma no momento da emissão da nota fiscal de saída, em
Mov_Nota_Fiscal_Saida.Valor_Frete (seção 7) --- o mesmo campo também
registra, para valor_fixo, a confirmação do que já havia sido negociado.

Código de rastreio --- gancho explícito para a Expedição: Alberto foi
explícito que o código de rastreio só existe no momento em que a
mercadoria de fato sai (\"para cada saída da expedição, teria que
colocar o código de rastreio, pois só neste momento que você tem o
código, com isto estaria vinculado ao item/pacote enviado\") --- ou
seja, é um dado que nasce na Expedição, não em CRM & Vendas. Este módulo
não modela Codigo_Rastreio nem a entidade de saída física da Expedição
(algo como Mov_Expedicao_Saida, ainda não especificada); o gancho é a
própria Mov_Pedido_Venda_Item_Entrega_Programada (seção 5), que a futura
Expedição referenciaria para vincular o código de rastreio ao
item/pacote efetivamente enviado, e a transportadora real (distinta da
referência de custo acima) também nasceria nessa futura entidade, não
aqui.

10\. Crédito do Cliente

O Documento Analítico descreve o crédito do cliente consolidado no Grupo
Econômico (Cad_Grupo_Economico, Fase 0) --- exposição total = saldo a
receber em aberto + o novo pedido ---, com bloqueio de inadimplência
aplicado ao grupo inteiro, não só ao participante isolado. Na Revisão 1
deste documento, Contas a Pagar/Receber ainda não existia, e esta seção
era só um GANCHO conceitual, sem estrutura de dados própria. Contas a
Pagar/Receber (Fase 2) e Tesouraria (Fase 2) já foram especificados
desde então --- esta Revisão 5 substitui o gancho pela integração real,
descrita em detalhe na seção 4 (Aprovação da Cotação).

Resumo da estrutura real, hoje: Cad_Participante.ID_Grupo_Economico
(Fase 0) identifica o grupo do cliente; Exposição_Total (soma do saldo
em aberto de Mov_Titulo, Tipo=receber, Contas a Pagar/Receber seção 6) e
o teto configurado (Cad_Grupo_Economico.Limite_Credito ou, na ausência
de grupo, por CNPJ Raiz/individual) definem o gatilho desvio_credito; a
régua de cobrança de Tesouraria (dias de atraso, seções 9 e 10 daquele
documento) define o gatilho bloqueio_regua_cobranca. Os dois convergem
para o mesmo Status=em_aprovacao de Mov_Cotacao_Venda (seção 2 e 4),
sempre avaliados no nível de grupo econômico do cliente. Nenhuma
estrutura de dados nova nesta seção --- é inteiramente reaproveitamento
do que Contas a Pagar/Receber e Tesouraria já definiram, mais o gatilho
novo (Origem_Tipo=bloqueio_regua_cobranca, Fase 0) e o ajuste de fluxo
descritos na seção 4.

11\. Como este módulo se conecta com a Fase 0, Compras e Estoque

Referência rápida do que este módulo consome --- nunca redescrito aqui,
só referenciado por chave estrangeira.

  ------------------------------------------------------- ------------------------------------- ---------------------------------------------------------
  **Entidade referenciada**                               **Como este módulo usa**              **Observação**

  **Cad_Participante**                                    O cliente da cotação/pedido/nota, o   *Mesmo cadastro único do Fase 0*
                                                          vendedor responsável, cada            
                                                          beneficiário da escada de comissão e  
                                                          a transportadora de referência de     
                                                          cada entrega programada.              

  **Cad_Participante.ID_Participante_Vendedor_Principal / O vendedor principal do cliente       *Fase 0, revisão 15 --- campos simples, sem vigência*
  \_Suplente**                                            (herda para uma nova cotação) e o     
                                                          suplente (pode assumir a qualquer     
                                                          momento) --- base para decidir se a   
                                                          cotação nasce atribuída ou cai na     
                                                          fila (seção 2 e 4).                   

  **Cad_Motor_Regra (Campo=canal_origem)**                Permite regra de preço/comissão       *Fase 0, revisão 15*
                                                          distinta entre atendimento por        
                                                          vendedor e autoatendimento (seção 3 e 
                                                          9).                                   

  **Cad_Pre_Cadastro / Mov_Pre_Cadastro_Conversao**       Solicitante de cotação ainda não      *Mesmo mecanismo já usado do lado de Compras*
                                                          efetivado como cliente; convertido só 
                                                          na aceitação.                         

  **Cad_Filial**                                          Quem vende (cotação, pedido) e quem   *---*
                                                          emite (nota fiscal de saída).         

  **Cad_Produto_Servico**                                 O item cotado, vendido e faturado.    *Mesmo cadastro único do Fase 0*

  **Cad_Motor_Regra (+                                    Resolve preço de tabela, a escada de  *Tipo_Resultado=valor_preco_unitario/percentual_royalty e
  Cad_Produto_Servico_Dimensao_Nivel/Valor)**             comissão (por nível de cargo          Campo=licenciamento_produto (Fase 0 rev. 12),
                                                          comercial), o royalty (seção 3), e o  Campo=papel_comissionado (Fase 0 rev. 13)*
                                                          CST/cClassTrib/CFOP de saída (seção   
                                                          7).                                   

  **Cad_Participante_Historico_Hierarquia_Comercial**     O cargo comercial de cada colaborador *Fase 0, revisão 14 --- vigência própria*
                                                          e seu superior imediato, vigente na   
                                                          data da venda --- é o que a aplicação 
                                                          sobe para gerar automaticamente a     
                                                          escada de comissão (seção 3 e 9).     

  **Cad_Classe_Sistema (domínio cargo_comercial)**        Normatiza os níveis de cargo          *Fase 0, revisão 14 --- domínio aberto*
                                                          comercial (vendedor, superintendente, 
                                                          gerente e quantos a Mlegate           
                                                          cadastrar) usados na hierarquia e     
                                                          como critério do Motor de Regras.     

  **Cad_CFOP (Fase 0) / Cad_Cst / Cad_Cclasstrib (Fase 2  O CFOP de saída e o CST/cClassTrib de *Cad_Cst/Cad_Cclasstrib substituem o antigo domínio
  --- Contabilidade & Fiscal)**                           cada item da nota.                    cst_ibs_cbs/Cad_ClassTrib do Fase 0, aposentados na
                                                                                                revisão 23*

  **Cad_Classificacao_Mercadoria (NCM) /                  Snapshot fiscal congelado no item da  *Fase 0 --- mesmo princípio já usado na nota de entrada
  Cad_Unidade_Medida / Cad_NBS**                          nota de saída.                        de Compras*

  **Cad_Regua_Aprovacao (+ Mov_Aprovacao_Instancia)**     Aprova a COTAÇÃO --- nunca o pedido   *Origem_Tipo=cotacao_venda (Fase 0 revisão 12),
                                                          --- por três gatilhos independentes:  desvio_credito (Contas a Pagar/Receber) e
                                                          desconto além da alçada, desvio de    bloqueio_regua_cobranca (Fase 0, revisão 22 ---
                                                          crédito e bloqueio da régua de        Tesouraria)*
                                                          cobrança (seção 4).                   

  **Mov_Titulo / Limite de Crédito (Contas a              A exposição de crédito e o atraso de  *Contas a Pagar/Receber, seção 6; Tesouraria, seções 9 e
  Pagar/Receber) + régua de cobrança (Tesouraria)**       cobrança do cliente, consultados no   10*
                                                          momento da aprovação da cotação       
                                                          (seção 4 e 10).                       

  **Cad_Condicao_Pagamento (+                             Sugestão de parcelamento da cotação   *Fase 0, revisão 13 --- mesmo cadastro usado por Compras*
  Cad_Condicao_Pagamento_Parcela)**                       --- pré-popula                        
                                                          Mov_Cotacao_Venda_Parcela, cujos      
                                                          valores/datas reais são sempre        
                                                          explícitos.                           

  **Cad_Produto_Servico_Transportadora**                  Insumo de aptidão (qual               *Fase 0, revisão 13 --- papel reframeado na revisão 3
                                                          transportadora atende qual produto) e deste módulo*
                                                          base de referência de custo para      
                                                          estimar o frete na venda --- não      
                                                          define a transportadora real, que é   
                                                          decisão da futura Expedição/Compras.  

  **Cad_Participante_Endereco (Tipo_Endereco=entrega)**   O endereço de destino de uma entrega  *Fase 0*
                                                          programada, quando a modalidade exige 
                                                          um endereço.                          

  **Cad_Classe_Sistema (domínio motivo_devolucao)**       Normatiza o motivo de                 *Fase 0 --- mesmo domínio genérico usado por Compras*
                                                          Mov_Devolucao_Venda.ID_Motivo.        

  **Cad_Grupo_Economico**                                 Identifica o grupo do cliente ---     *Fase 0*
                                                          nível em que os dois gatilhos de      
                                                          bloqueio de crédito/cobrança são      
                                                          sempre avaliados (seção 4 e 10).      

  **Cad_Local_Estoque (Estoque)**                         Onde a reserva (seção 6) e a baixa    *Fase 1 --- Estoque*
                                                          física (seção 7) acontecem --- agora  
                                                          escolhido explicitamente por entrega  
                                                          programada; também onde o saldo é     
                                                          consultado na checagem de estoque do  
                                                          autoatendimento (seção 9).            

  **Mov_Estoque_Movimento / Mov_Estoque_Movimento_Item    A baixa física da nota de saída (com  *Origem_Tipo=pedido_venda, venda_avulsa (saída) ou
  (Estoque)**                                             ou sem pedido), e a reentrada física  movimento_estoque (devolução), Estoque revisão 7*
                                                          da devolução.                         

  **Mov_Lote_Lancamento / Mov_Lancamento (Fase 0)**       A provisão contábil de                *Origem_Tipo=provisao_comissao_venda, Fase 0 revisão 13*
                                                          comissão/royalty, gerada no           
                                                          nascimento do pedido (seção 9).       

  **Mov_Ordem_Servico_Item (Produção)**                   Adicionado nesta revisão (7): a linha *Fase 1, construído nesta revisão*
                                                          de material/mão de obra faturável de  
                                                          uma ordem de serviço técnica sobre    
                                                          máquina própria vendida (seção 7).    
  ------------------------------------------------------- ------------------------------------- ---------------------------------------------------------

12\. Notas para a sua revisão

Mesma lógica dos documentos anteriores: estas são decisões técnicas que
assumi por conta própria para fechar uma estrutura concreta --- nenhuma
está travada.

-   Este módulo foi especificado fora da ordem original do Documento
    Analítico (Fase 4 → antecipado para esta leva da Fase 1), por
    decisão explícita de Alberto --- ver seção 1. A maior consequência
    dessa antecipação, o crédito do cliente como só gancho conceitual
    (seção 10), foi resolvida nesta revisão (5), já com Contas a
    Pagar/Receber e Tesouraria especificados. Continuam pendentes: a
    liquidação financeira real de comissão/royalty/parcela (seção 9),
    que depende de Contas a Pagar/Receber; e o prazo de
    entrega/produção, que continua manual, sem capacidade de Produção
    para calculá-lo (abaixo).

-   Data_Entrega_Programada
    (Mov_Cotacao/Pedido_Venda_Item_Entrega_Programada, seções 2 e 5) é
    um campo manual, informado por quem cotou --- o módulo de Produção
    (Fase 3), que ainda não existe, é quem eventualmente teria
    capacidade/agenda para sugerir essa data automaticamente. Quando
    Produção for especificado, este campo pode passar a ser sugerido,
    mantendo a edição manual como sobreposição.

-   A soma das Quantidade_Programada de um item
    (Mov_Cotacao/Pedido_Venda_Item_Entrega_Programada) fechar exatamente
    na Quantidade do item não é uma restrição garantida pela própria
    estrutura de dados --- fica como validação de camada de aplicação,
    mesmo padrão já usado em outros pontos deste dicionário (ex.:
    Mov_Pedido_Item_Destinacao, Compras).

-   Cad_Produto_Servico_Transportadora sugere
    ID_Participante_Transportadora_Referencia, mas não obriga --- quem
    cota pode escolher qualquer Participante cadastrado como
    transportadora de referência, mesmo fora da lista apta para aquele
    produto; bloquear ou não esse caso fica a critério da camada de
    aplicação. Reforçando: este campo nunca representa a transportadora
    que de fato vai executar o envio --- essa decisão pertence à
    Expedição/Compras (seção 9).

-   ID_Papel_Comissionado (Mov_Cotacao/Pedido_Venda_Item_Comissao) deixou
    de ser enumeração fixa nesta revisão (3) e passou a referenciar o
    domínio aberto cargo_comercial (Cad_Classe_Sistema, Fase 0
    revisão 14) --- decisão tomada porque Alberto esclareceu que a
    hierarquia comercial não tem profundidade fixa em três níveis
    (\"pode ter 1 nível, quantos forem necessários\"). Continua sem um
    cadastro próprio de regras de elegibilidade por papel (quem pode
    ocupar cada cargo); se a Mlegate precisar disso, é uma extensão
    futura.

-   A geração automática da escada de comissão (seção 3 e 9), a partir
    de Cad_Participante_Historico_Hierarquia_Comercial, é lógica de
    aplicação, não uma restrição garantida pela estrutura de dados em si
    --- nada impede, na estrutura, que alguém insira manualmente uma
    linha de Mov_Cotacao_Venda_Item_Comissao fora do padrão da
    hierarquia; presumo que a aplicação sempre gera automaticamente e
    não expõe edição manual dessa escada, mas fica como ponto de
    atenção.

-   Cad_Participante_Historico_Hierarquia_Comercial (Fase 0, revisão 14)
    foi modelada como uma tabela de histórico com vigência própria, para
    que a escada de uma venda antiga reflita o cargo/superior vigente na
    data daquela venda, e não o cadastro atual --- uma elaboração minha
    sobre o que foi descrito na conversa (campos simples de
    cargo/superior no cadastro do colaborador), pensada para manter a
    mesma fidelidade histórica já usada em todo este dicionário. Fica
    como ponto de atenção explícito para sua confirmação --- ver a nota
    equivalente no dicionário do Fase 0.

-   A soma das linhas de Mov_Cotacao/Pedido_Venda_Item_Comissao (a
    escada) não é validada estruturalmente contra nenhum teto (ex.: um
    percentual total máximo combinado) --- fica como validação de camada
    de aplicação, mesmo padrão já usado em outros pontos do dicionário.

-   Frete: Modalidade_Cobranca_Frete e Valor_Frete_Negociado (seção 2
    e 5) resolvem a cobrança do cliente e a preservação do valor
    negociado; Mov_Nota_Fiscal_Saida.Valor_Frete (seção 7) resolve o
    valor definitivo na emissão. O que este módulo deliberadamente NÃO
    modela é o custo real pago à transportadora (só a Mlegate paga,
    nunca o cliente) nem a comparação ganho/perda entre o negociado e o
    custo real --- ambos dependem de uma futura Expedição/Contas a
    Pagar, fora do escopo desta revisão.

-   Codigo_Rastreio e a entidade de saída física da Expedição
    (Mov_Expedicao_Saida ou nome equivalente) não existem neste
    dicionário --- só o gancho conceitual (seção 9): quando a Expedição
    for especificada, ela deve referenciar
    Mov_Pedido_Venda_Item_Entrega_Programada para vincular o código de
    rastreio ao item/pacote efetivamente enviado, e é lá também que a
    transportadora real (distinta de
    ID_Participante_Transportadora_Referencia) seria registrada.

-   Mov_Estoque_Reserva passou a nascer por linha de entrega programada,
    não mais por item inteiro do pedido --- uma mudança estrutural desta
    revisão que reflete diretamente o pedido de Alberto para dividir a
    entrega por data/quantidade; o local de reserva agora é sempre o
    escolhido explicitamente pelo vendedor (ID_Local_Estoque da entrega
    programada), sem lógica de sugestão/otimização automática entre
    locais.

-   Comissão e royalty geram provisão contábil no nascimento do pedido e
    uma leitura estimada pensada para uma futura Tesouraria (seção 9)
    --- mas o repasse financeiro efetivo (ao vendedor com vínculo
    empregatício, via Folha & RH; a um vendedor autônomo/PJ ou ao
    licenciante, via Contas a Pagar) continua fora do escopo, dependendo
    de módulos ainda não especificados.

-   Expedição --- separação física, romaneio, execução do transporte ---
    é módulo próprio no Documento Analítico (Fase 4, junto com CRM &
    Vendas e Portal do Cliente) e não foi modelado aqui; este módulo só
    garante que os dados de que a Expedição vai precisar (entrega
    programada, transportadora de referência, sinalização de dependência
    de produção/personalização) já existem (seção 9).

-   Portal do Cliente continua sendo módulo próprio da Fase 4 no plano
    original, não modelado por completo aqui --- mas, nesta revisão (4),
    ganhou um comportamento concreto que atravessa os dois dicionários:
    o autoatendimento (Canal_Origem=autoatendimento, seção 2 e 9), que
    cria uma cotação pré-preenchida direto em CRM & Vendas. O que o
    Portal em si (telas, autenticação do cliente, consulta externa de
    pedido/nota) precisa para existir continua fora do escopo --- este
    módulo só garante que o EVENTO de autoatendimento (cotação
    pré-preenchida, preço fixo, checagem de estoque) já está modelado do
    lado de CRM & Vendas, pronto para o Portal disparar quando for
    especificado.

-   Fila de cotações (seção 2 e 4) é uma fila única e não segmentada,
    por decisão explícita de Alberto (\"até para ver se tem algo parado
    e ninguém tomou uma ação\") --- função de monitoramento tanto quanto
    de distribuição. Este dicionário não modela um painel/relatório de
    fila em si (tempo parado, SLA, escalonamento); só garante o dado
    necessário para construí-lo depois: Mov_Cotacao_Venda com
    ID_Participante_Vendedor vazio e Status=aberta (ou em_aprovacao) é,
    por definição, uma cotação na fila.

-   Cad_Participante.ID_Participante_Vendedor_Principal/\_Suplente (Fase
    0, revisão 15) foram modelados como campos simples, sem vigência ---
    ao contrário de Cad_Participante_Historico_Hierarquia_Comercial
    (comissão), não há aqui o mesmo requisito de fidelidade histórica: o
    vendedor principal/suplente é sempre o vigente NO MOMENTO em que uma
    nova cotação nasce, não precisa refletir quem era o vendedor de um
    cliente numa data passada. Se a Mlegate precisar futuramente de
    histórico de troca de vendedor por cliente (ex.: para métricas de
    carteira), é uma extensão possível sobre este campo.

-   Data_Hora_Atribuicao_Vendedor (Mov_Cotacao_Venda, seção 2) só
    registra QUANDO um vendedor pega a cotação da fila --- não um
    histórico completo de reatribuições (ex.: se a cotação trocar de
    vendedor mais de uma vez, só a atribuição mais recente fica
    registrada, sobrescrevendo a anterior). Se precisar de rastro
    completo de reatribuições, é uma extensão futura (ex.: uma tabela de
    histórico dedicada, mesmo padrão já usado em outros pontos deste
    dicionário).

-   Mov_Cotacao_Venda.Status=em_aprovacao, na causa cotacao_venda
    (desconto), compara o desconto agregado (ou o maior entre os itens)
    contra a alçada do vendedor --- não detalhei qual das duas leituras
    a régua usa por padrão; fica, como outros pontos de configuração
    deste dicionário, a critério de quem cadastra a régua
    (Cad_Regua_Faixa, Fase 0), não uma regra fixa aqui. Nas causas
    desvio_credito e bloqueio_regua_cobranca (revisão 5), não há
    comparação de valor contra faixa --- são bloqueios diretos, sem
    alçada a percorrer.

-   A remoção de Mov_Cotacao_Venda.ID_Instancia_Aprovacao (seção 2,
    revisão 5), substituída por consulta em Mov_Aprovacao_Instancia
    (seção 4), é consistente com a filosofia de \"nunca armazenar o que
    é derivável\" já usada em todo este dicionário, mas é uma mudança de
    padrão em relação à Revisão 4, que tinha esse campo --- sinalizado
    explicitamente porque, diferente de outras simplificações, esta
    troca um campo que já existia por uma consulta, não o contrário.

-   Venda avulsa/balcão (seção 7), incorporada nesta revisão, é
    deliberadamente mais simples que o ciclo completo: sem
    desconto/aprovação (não há cotação), sem comissão/royalty
    calculados, sem reserva prévia. Se a Mlegate precisar de comissão
    numa venda avulsa (ex.: vendedor de balcão também comissionado), é
    uma extensão futura que exigiria reintroduzir parte da estrutura de
    comissão diretamente na nota, fora do escopo desta revisão.

-   Cad_Motor_Regra_Resultado.Tipo_Resultado (valor_preco_unitario,
    percentual_royalty), Cad_Motor_Regra_Criterio.Campo
    (licenciamento_produto, papel_comissionado, canal_origem),
    Cad_Produto_Servico_Transportadora, Cad_Condicao_Pagamento (+
    Parcela) e o domínio motivo_devolucao (Cad_Classe_Sistema) foram
    todos adicionados ou estendidos no Fase 0 (revisões 12, 13 e 15)
    especificamente para este módulo; na revisão 14 do Fase 0 foram
    acrescentados o domínio cargo_comercial e a entidade
    Cad_Participante_Historico_Hierarquia_Comercial; na revisão 15,
    Cad_Participante ganhou
    ID_Participante_Vendedor_Principal/\_Suplente e
    Cad_Motor_Regra_Criterio.Campo ganhou canal_origem --- nenhuma outra
    mudança foi feita no Fase 0 além dessas; Estoque recebeu, nas
    revisões 6 e 7, Origem_Tipo=pedido_venda e Origem_Tipo=venda_avulsa,
    e Compras recebeu, na revisão 6, os mesmos campos de simetria (chave
    de acesso, snapshot fiscal do item, motivo de devolução normatizado,
    parcela real do pedido) --- nenhuma mudança em Compras ou Estoque
    nesta rodada.

-   Revisão 6 --- pedida pela consolidação da Fase 2 Contabilidade &
    Fiscal: Mov_Nota_Fiscal_Saida_Item.ID_CST_IBS_CBS/ID_ClassTrib foram
    renomeados para ID_Cst/ID_Cclasstrib e redirecionados para o novo
    pré-cadastro próprio daquele módulo (Cad_Cst/Cad_Cclasstrib, seção
    6), substituindo o domínio cst_ibs_cbs e a Cad_ClassTrib do Fase 0,
    ambos aposentados; e Numero_Processo_Suframa foi adicionado para o
    item de saída destinado à Zona Franca de Manaus/Área de Livre
    Comércio.

-   Revisão 7 --- pedida pela especificação do módulo Fase 1 Produção:
    Mov_Nota_Fiscal_Saida_Item ganhou ID_Ordem_Servico_Item (seção 7),
    para faturar material/mão de obra de assistência técnica sobre
    máquina própria vendida, fora de garantia ou com mau uso.
    Data_Entrega_Programada (seção 2 e 5) continua manual --- Produção,
    nesta primeira revisão, não modelou agenda/capacidade produtiva para
    sugerir prazo automaticamente (ver Notas do próprio módulo de
    Produção); fica como gancho, não fechado por esta revisão.

-   Revisão 8: CRM & Vendas passou a consumir o mecanismo transversal de
    fechamento de período da Fase 0
    (Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial,
    seção 10 daquele documento, revisão 37) --- bloco \"vendas\"
    travando Mov_Nota_Fiscal_Saida (seção 7) por Filial+competência,
    nenhum campo novo na entidade, só o comportamento de aplicação
    descrito junto dela. Única exceção confirmada por Alberto em todo o
    redesenho: criar Mov_Pedido_Venda e a cotação de origem (seção 2
    e 5) continua liberado mesmo com o bloco fechado, porque sem
    atendimento não há efeito fiscal nem de valor --- o oposto do que
    acontece em Compras, onde o Pedido de Compra fica travado desde a
    criação por já gerar compromisso orçamentário. A exceção vale só
    para CRIAR o pedido/cotação --- alterar um pedido já existente de
    forma que mude o que seria faturado/entregue numa competência
    fechada segue a mesma trava do faturamento. Vendas não ganhou
    validação de pendência no fechamento --- isso continua exclusivo de
    Compras.

-   Revisão 9 --- as duas referências cruzadas fechadas nesta revisão
    (seções 7 e 9) não mudam nenhum campo nem comportamento de CRM &
    Vendas: eram gancho textual apontando para um módulo que, à época da
    Revisão 1/5, ainda não existia (Contas a Pagar/Receber), e que hoje
    já cobre os dois pontos por conta própria.

-   Revisão 10 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): número e série desmembrados na nota
    fiscal de saída e na devolução; chave de acesso de 44 caracteres
    (CNPJ alfanumérico). A convenção completa (vigência, identidade +
    versão, sucessão de códigos oficiais, competência, CNPJ
    alfanumérico, um campo por informação, saldos guardados de período
    fechado, sequência de fechamento) vive na Fase 0, seções 2 e 10
    (revisão 41).

-   Revisão 11 --- tipo lógico \"código (n)\" definido por Alberto ---
    todo campo que identifica algo (inscrição, documento, agência,
    conta, número e série de nota, matrícula, código oficial) é
    caractere, nunca numérico: os zeros à esquerda fazem parte do
    código, e o padrão pode passar a aceitar letras ou mudar de tamanho,
    como aconteceu com o CNPJ alfanumérico. Campos revistos:
    Chave_Acesso, Chave_Acesso_Devolucao, Codigo_Servico_Municipal,
    Numero, Numero_Nota_Devolucao, Numero_Processo_Suframa, Serie,
    Serie_Nota_Devolucao. O NCM do item da nota passa a apontar para
    Cad_Classificacao_Mercadoria (NCM harmonizado, Fase 0). Convenção
    completa na Fase 0, seção 2.6 (revisão 42).

-   Revisão 12 --- campos fiscais do cabeçalho e do item da nota de
    saída (os mesmos de Compras: modelo e situação do documento,
    finalidade, natureza da operação, consumidor final, presença,
    protocolo, modalidade de frete, rateios por item, origem da
    mercadoria, CEST, Ex da TIPI, GTIN, cBenef e cTribNac), local da
    operação por linha do pedido de venda e da nota, habilitação
    REIDI/REPES do cliente no item do pedido de venda e da nota de
    saída, e o empreendimento imobiliário no item da nota de saída.
    Desenho completo no documento Validação do Bloco 2 (documentos/18).

-   Revisão 13 --- referência a Cad_Regua_Aprovador_Escopo trocada por
    Cad_Usuario_Escopo (Fase 0, seção 13), que a substitui.

13\. Próximo passo

*Com a revisão 4, comissão/royalty e condição de pagamento ganharam mais
estrutura (escada de beneficiários, estimativa, provisão contábil,
parcelamento real). A Revisão 5 fechou o gancho de maior consequência da
antecipação deste módulo: o crédito do cliente (seção 10) ganhou
estrutura real, e os dois gatilhos de bloqueio (desvio de crédito e
régua de cobrança) estão de fato integrados dentro da cotação de venda
(seção 2 e 4) --- Contas a Pagar/Receber e Tesouraria, ambos hoje
especificados, deixaram de ser só referência futura. A Revisão 6 fechou
o redirecionamento de CST/cClassTrib para o pré-cadastro da Fase 2
Contabilidade & Fiscal. Esta Revisão 7 fecha uma pequena ponta do módulo
de Produção, hoje especificado (Fase 1, Módulo 8): o faturamento de
ordem de serviço técnica (seção 7). Continuam, deliberadamente, como
gancho: a liquidação financeira real (recebimento do cliente, reversão
da provisão, repasse de comissão/royalty --- seção 9), que ainda depende
do módulo de baixa de Contas a Pagar/Receber; a leitura de capacidade de
produção para sugerir prazo de entrega, que Produção não endereçou nesta
primeira revisão; e o processo operacional de separação/embarque e o
portal do cliente propriamente dito, que dependem de Expedição e Portal
do Cliente, ainda não especificados. Seguindo a ordem do Documento
Analítico, os módulos naturais seguintes são Expedição, Portal do
Cliente e RH & Folha de Pagamento --- mas, como sempre neste projeto, a
decisão final de por onde continuar é sua.*

*Revisão 8, registrada aqui: CRM & Vendas passou a consumir o mecanismo
transversal de fechamento de período (Fase 0, seção 10) --- bloco
\"vendas\", travando a nota fiscal de saída (seção 7) por
Filial+competência, com a única exceção de todo o redesenho (criar
pedido de venda/cotação, seção 2 e 5, continua liberado até o
atendimento). Compras foi o primeiro módulo a adotar o mecanismo
(revisão 13 daquele documento); entre os demais módulos já entregues,
ainda falta a mesma revisão pontual em Estoque, Planejamento &
Orçamento, Expedição, Produção, Contas a Pagar/Receber, Tesouraria,
Contabilidade & Fiscal, Folha & RH e Gestão de Contratos.*

*Revisão 9, registrada aqui: patch pontual da mesma consolidação que
entregou Contas a Pagar/Receber --- as duas referências cruzadas que
ficavam como gancho textual (reversão de provisão de comissão/royalty,
seção 9; valor da nota vs. valor do título por retenção/split, seção 7)
foram fechadas com uma frase apontando para o módulo que hoje já resolve
os dois pontos, sem nenhuma estrutura nova neste documento.*

*Revisão 10 --- Bloco 1 da validação geral consolidado junto com a Fase
0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal)
e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 11 --- tipo lógico \"código\" aplicado junto com a revisão 42
da Fase 0. Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 12 --- Bloco 2 (fiscal) da validação geral consolidado junto
com a Fase 0 (revisão 43). Próximo passo combinado com Alberto: Bloco 3
(folha e jurídico), com desenho próprio para aprovação antes de
consolidar.*



14\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este documento não ganha entidades novas; as alterações em entidades existentes aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3").
