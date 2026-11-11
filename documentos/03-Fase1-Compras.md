**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 1 · MÓDULO 2**

**Compras**

*Pedido de compra (produto ou serviço), cotação com aprovação por item,
contrato de fornecimento contínuo, aprovação, vínculo com o orçamento,
nota fiscal de entrada via Motor de Regras, devolução e recusa de
recebimento*

*Revisão 27 --- consolidação da revisão 31 do dicionário (documentos 150, 157, 170 e 173, com as respostas de Alberto de 04/11/2026): 2 entidades existentes alteradas; data do fato gerador no item da nota de entrada e ligação da devolução de compra ao ajuste da operação (documento 157, Q157-1 e Q157-2).*

*Revisão 26 --- consolidação da revisão 30 do dicionário (documentos 156, 161, 164 e 168 e a Q138-3, com as respostas de Alberto de 03/11/2026): 2 entidades existentes alteradas; Finalidade credito e debito, Escriturada_Como_Saida e a quantidade zero na nota de entrada (documento 168, G2), e Valor_Desconto_Condicional_Item no item (documento 156, Q156-13).*

*Revisão 25 --- consolidação da revisão 29 do dicionário (documentos 138, 140, 152, 153, 155, 162, 163 e 165, com as respostas de Alberto de 29/10/2026 e de 03/11/2026): 1 entidades existentes alteradas; Chave_Dfe_Pagamento_Antecipado e Numero_Item_Pagamento_Antecipado no item da nota de entrada (documento 165, Q165-7).*

*Revisão 24 --- consolidação da revisão 19 do dicionário (documento 90 aprovado por Alberto em 21/10/2026 e decisões do documento 91 respondidas): 1 entidades existentes alteradas; texto da nota de entrada com crédito presumido por categoria (D-N280, documento 90).*

*Revisão 23 --- consolidação da revisão 16 do dicionário (documentos 80 e 82, decisões D-N236 a D-N240 e D-N243 a D-N248, aprovadas por Alberto em 19/10/2026): 1 entidades existentes alteradas; série "0" quando a nota não tem série e regra da NFTS na nota de entrada (documentos 80 e 82, D-N240 e D-N247).*

*Revisão 22 --- consolidação da revisão 7 do dicionário (documentos 59, 60 e 61; decisões D-N140 a D-N147 e D-N154 a D-N160, aprovadas por Alberto em 13/10/2026): 1 entidades existentes alteradas. O dicionário passa de 857 para 874 entidades.*

*Revisão 21 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 2 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 20 --- Achado R-7 da revisão final cruzada (documento 30,
04/10/2026), construída junto com a revisão 50 da Fase 0:
Mov_Cotacao_Proposta.ID_Proponente passa a ser declarado como referência
genérica, conforme Tipo_Proponente (Cad_Participante ou Cad_Pre_Cadastro),
o padrão que o texto já citava; sem mudança de estrutura.*

*Revisão 19 --- ajuste de texto pelo Bloco 4 (Fase 0, revisão 46;
Contabilidade & Fiscal, revisão 18): Serie de Mov_Nota_Fiscal_Entrada
passa de 3 para 5 posições, como pede a EFD-Reinf. A nota de entrada é a
origem dos fatos do R-2010 (serviço tomado com retenção de INSS) e do
R-2055 (aquisição de produção rural), na seção 21 de Contabilidade &
Fiscal.*

*Revisão 18 --- ajuste de texto pelo Bloco 3 (Fase 0, revisão 45):
referência a Cad_Regua_Aprovador_Escopo trocada por Cad_Usuario_Escopo
(Fase 0, seção 13), que a substitui.*

*Revisão 17 --- construída junto com a revisão 43 da Fase 0 (Bloco 2,
fiscal): campos fiscais do cabeçalho e do item da nota de entrada
(modelo e situação do documento, finalidade, natureza da operação,
consumidor final, indicador de presença, protocolo de autorização,
modalidade de frete, rateio de desconto, frete, seguro e outras despesas
por item, origem da mercadoria, CEST, Ex da TIPI, GTIN, cBenef e
cTribNac), local da operação por linha do pedido e da nota (local no
contratante, endereço, Cad_Local_Operacao, critério do local, município
de incidência do IBS e do ISS), habilitação REIDI/REPES e situação da
suspensão nas linhas de destinação, e o empreendimento imobiliário no
item do pedido e da nota.*

*Revisão 16 --- construída junto com a revisão 42 da Fase 0: tipo lógico
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

*Revisão 15 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; campos compostos desmembrados na nota fiscal de
entrada (número e série; datas de emissão e de entrada), no item de
pedido (período do serviço), na renegociação e na devolução; chaves
primárias das destinações e do item de proposta de cotação; chave de
acesso de 44 caracteres (CNPJ alfanumérico).*

*Revisão 14 --- patch pontual pedido pela consolidação de Contas a
Pagar/Receber: Mov_Pedido_Parcela (seção 2) deixa de apontar para uma
\"Fase futura\" --- a liquidação real já está construída (Fase 2); e
nova nota (seção 6) fecha a referência cruzada entre o valor da nota
fiscal de entrada e o valor do título quando há retenção na fonte ou
split payment do IBS/CBS. Nenhuma estrutura nova*

*Revisão 13 --- nova seção transversal de fechamento de período (Fase 0,
seção 10, revisão 37): o bloco \"compras\" trava toda criação/alteração
de Mov_Pedido e de Mov_Nota_Fiscal_Entrada datada numa competência
fechada para a Filial correspondente --- comportamento de aplicação
junto de cada entidade (seções 2 e 6), sem campo novo. Compras também
ganhou o único ponto de VALIDAÇÃO DE PENDÊNCIA do dicionário: não fecha
período com nota fiscal de entrada ainda em conferência de qualidade
pendente (seção 7)*

*Revisão 12 --- Cad_Contrato_Fornecimento e
Cad_Contrato_Fornecimento_Valor (seção 4) aposentados: duplicavam o
conceito de contrato de fornecimento contínuo já coberto pelo módulo
Fase 6 Gestão de Contratos, unificado nesta rodada para atender cliente
e fornecedor no mesmo cadastro (Cad_Gestao_Contrato), por decisão
explícita de Alberto --- construído junto com a revisão 3 daquele
documento*

*Revisão 11 --- item rejeitado na inspeção de entrada passa a
classificar Condicao no novo motor transversal do Estoque
(rejeitado/reparar/descartar), mesmo mecanismo usado por Expedição*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o segundo módulo da Fase 1 --- Compras --- no
mesmo formato usado no módulo de Planejamento & Orçamento: função e
dados juntos, entidade por entidade, sempre referenciando os motores
transversais da Fase 0 (Cad_Participante, Cad_Filial,
Cad_Produto_Servico, Cad_Destinacao, Cad_Motor_Regra,
Cad_Regua_Aprovacao) e o módulo de Planejamento & Orçamento
(Cad_Orcamento_Item, Mov_Compromisso_Orcamentario) em vez de
redefini-los.

A Revisão 3 incorporou a segunda rodada de comentários seus sobre a
Revisão 2: cotação com N itens e aprovação por item (não a cotação
toda-ou-nada), rateio quantitativo (produto) ou por fator (serviço)
entre destinações --- em vez de percentual único ---, conta contábil
sobrescrevível numa nota sem pedido, recusa de recebimento e devolução
de compra, prazo de entrega e encadeamento de pedidos quando um é
cancelado. As revisões 4 e 5 foram pequenos patches pedidos pelo módulo
de Estoque: Valor_Credito_Tributario na nota de entrada (crédito de
imposto em bonificação) e a possibilidade de o recebimento físico se
amarrar direto na nota quando não há pedido. Cabe a você continuar
corrigindo com a realidade da Mlegate e de seus clientes, no mesmo ritmo
de revisão comentário-a-comentário: vá comentando o que estiver errado
ou faltando, e no final me avise para consolidar.

Fica FORA desta revisão, por decisão de escopo (não por esquecimento):
requisição de compra interna (o pedido pode nascer direto, ou a partir
de uma cotação --- ver seção 3); a conferência FÍSICA da mercadoria no
depósito (contagem, endereçamento) depende do módulo de Estoque --- mas
a conferência fiscal/financeira entre nota e pedido, e a inspeção de
QUALIDADE (seção 7), já são função deste módulo, independente do
Estoque; e compras internacionais/importação. Este módulo cobre
aquisição nacional em geral --- produto ou serviço, pontual ou contínua
--- do pedido (ou contrato) à nota fiscal de entrada, com aprovação,
vínculo orçamentário, devolução e recusa. Adicionado nesta revisão:
quando a nota fiscal de entrada não tem pedido (ver seção 6), o item
ainda pode precisar entrar fisicamente no estoque --- nesse caso, o
módulo de Estoque amarra o recebimento físico direto na linha da nota
(Mov_Nota_Fiscal_Entrada_Item), não só na linha do pedido, garantindo
que toda entrada física continue rastreável até o documento de origem.

2\. Pedido de Compra

O pedido de compra é dirigido a um fornecedor (Cad_Participante, Fase 0
--- nenhum cadastro novo é necessário) e emitido por uma filial
específica (Cad_Filial, Fase 0). Cada linha do pedido pode se ratear
entre mais de uma Destinação (Cad_Destinacao, Fase 0) ---
quantitativamente para produto, por fator para serviço (ver
Mov_Pedido_Item_Destinacao) --- e, opcionalmente, referenciar uma linha
específica do orçamento (Cad_Orcamento_Item, módulo de Planejamento &
Orçamento) para consumir o compromisso orçamentário correspondente.

Mov_Pedido

O cabeçalho do pedido de compra --- de produto ou de serviço,
indiferente à estrutura (a distinção vem do Cad_Produto_Servico
referenciado em cada linha).

*Vigência: não --- é o registro de um evento (o pedido); Status é o
próprio ciclo de vida, não uma nova vigência.*

  -------------------------------- --------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**             **Descrição / regra**

  **ID_Pedido**                    *identificador*             ---

  **ID_Filial**                    *referência (Cad_Filial)*   A filial que está comprando.

  **ID_Participante_Fornecedor**   *referência                 O fornecedor --- mesmo cadastro único do
                                   (Cad_Participante)*         Fase 0, sem nenhuma tabela nova.

  **ID_Pedido_Origem**             *referência (Mov_Pedido,    Preenchido quando este pedido nasce para
                                   opcional)*                  substituir outro que foi cancelado (ex.:
                                                               depois de uma recusa de recebimento não
                                                               resolvida, ver seção 8) --- normalmente
                                                               para um fornecedor diferente. Permite
                                                               reconstruir a cadeia completa até o
                                                               pedido efetivamente atendido, útil para
                                                               auditoria e para entender atraso
                                                               acumulado do processo.

  **Data_Pedido**                  *data*                      ---

  **Status**                       *enumeração {rascunho,      \"recebido\" cobre tanto o recebimento
                                   em_aprovacao, aprovado,     físico (produto) quanto o
                                   enviado, recebido,          aceite/conclusão administrativa
                                   cancelado}*                 (serviço) --- a conferência quantitativa
                                                               de mercadoria e a inspeção de qualidade
                                                               (seção 7) são registros à parte que
                                                               podem condicionar esta transição.

  **ID_Instancia_Aprovacao**       *referência                 A instância de aprovação do pedido ---
                                   (Mov_Aprovacao_Instancia,   reaproveitando a régua do Fase 0 (ver
                                   opcional)*                  seção 5).

  **ID_Condicao_Pagamento**        *referência                 Adicionado nesta revisão (6), pedido
                                   (Cad_Condicao_Pagamento,    para manter simetria com o módulo Fase 1
                                   opcional)*                  CRM & Vendas: só uma SUGESTÃO de
                                                               parcelamento, usada para pré-popular
                                                               Mov_Pedido_Parcela --- o comprador pode
                                                               mudar valores e datas livremente depois,
                                                               conforme negociação com o fornecedor
                                                               (fidelidade ao valor real, nunca
                                                               recalcular a partir da condição).
  -------------------------------- --------------------------- ----------------------------------------

*Comportamento de aplicação (não é um campo novo de dados): antes de
aceitar a criação ou alteração de um Mov_Pedido, o sistema consulta
Cad_Periodo_Fechamento_Filial (mecanismo transversal da Fase 0, seção
10) pela combinação Bloco=\"compras\" + Filial (ID_Filial acima) +
competência derivada de Data_Pedido --- na ausência de uma linha com
Status=aberto para essa combinação (regime fail-closed: nenhuma
combinação é tratada como aberta por omissão), a operação é bloqueada.
Diferente de Vendas, onde o pedido/cotação não compromete valor algum
até o atendimento, aqui o próprio pedido já gera compromisso
orçamentário na aprovação (seção 5) --- por isso o gate age já na
criação/alteração do pedido, não só no lançamento da nota fiscal de
entrada (seção 6).*

Mov_Pedido_Parcela

Adicionado nesta revisão (6), pedido para manter simetria com o módulo
Fase 1 CRM & Vendas: o parcelamento REAL deste pedido --- pode nascer
pré-populado a partir de Cad_Condicao_Pagamento_Parcela quando
ID_Condicao_Pagamento estiver preenchido, mas o valor e a data de cada
parcela aqui são sempre campos explícitos, editáveis pelo comprador a
qualquer momento antes da liquidação (Fase 2 --- Contas a Pagar/Receber,
seção 2, construído nesta consolidação; corrigido nesta revisão 14, que
ainda apontava para uma \"Fase futura\"), nunca recalculados a partir do
percentual do template.

*Vigência: não --- vigência não se aplica; alterações antes da
liquidação sobrescrevem o próprio registro, sem histórico de
renegociação nesta v1 (mesmo tratamento dado a outros campos livremente
editáveis antes da conclusão do pedido).*

  --------------------- ----------------- --------------------------------------------
  **Campo**             **Tipo lógico**   **Descrição / regra**

  **ID_Parcela**        *identificador*   ---

  **ID_Pedido**         *referência       ---
                        (Mov_Pedido)*     

  **Numero_Parcela**    *número*          1, 2, 3\... --- a ordem da parcela dentro do
                                          pedido.

  **Valor_Parcela**     *número*          O valor real desta parcela --- explícito,
                                          nunca derivado de
                                          Cad_Condicao_Pagamento_Parcela.Percentual,
                                          que é só a sugestão inicial.

  **Data_Vencimento**   *data*            A data real de vencimento negociada ---
                                          explícita, nunca derivada de
                                          Cad_Condicao_Pagamento_Parcela.Prazo_Dias,
                                          que é só a sugestão inicial.
  --------------------- ----------------- --------------------------------------------

Mov_Pedido_Item

Uma linha do pedido --- um produto ou serviço pontual
(ID_Produto_Servico já cobre os dois, Fase 0), sua quantidade e valor.
Aquisição contínua --- contrato de serviço ou fornecimento recorrente
--- não passa por aqui, tem seu próprio cadastro (seção 4).

*Vigência: não.*

  ----------------------------- ---------------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**                    **Descrição / regra**

  **ID_Item**                   *identificador*                    ---

  **ID_Pedido**                 *referência (Mov_Pedido)*          ---

  **ID_Item_Cotacao**           *referência (Mov_Cotacao_Item,     O item de cotação que originou esta
                                opcional)*                         linha, quando existir (ver seção 3) ---
                                                                   no nível do item, e não do pedido,
                                                                   porque itens de uma mesma cotação podem
                                                                   ter vencedores diferentes e acabar em
                                                                   pedidos diferentes.

  **ID_Produto_Servico**        *referência (Cad_Produto_Servico)* Pode ser atualizado enquanto o pedido
                                                                   não estiver Status=recebido, no caso de
                                                                   substituição de produto acordada com o
                                                                   fornecedor após uma recusa de
                                                                   recebimento (seção 8) --- sem tabela de
                                                                   histórico da troca nesta v1 (ver Notas).

  **Quantidade**                *número*                           Para serviço, normalmente 1 (ou uma
                                                                   contagem que fizer sentido, ex.: nº de
                                                                   horas) --- o que importa para um serviço
                                                                   pontual costuma ser o período de
                                                                   execução, não uma entrega física.

  **Valor_Unitario**            *número*                           ---

  **Valor_Total**               *número*                           Campo próprio, não recalculado a partir
                                                                   de Quantidade × Valor_Unitario (mesmo
                                                                   princípio de fidelidade ao valor real
                                                                   --- ver seção 6).

  **Data_Inicio_Servico**       *data, opcional*                   Preenchidos só quando o
                                                                   Cad_Produto_Servico referenciado é
                                                                   Tipo_Item=servico --- o período de
                                                                   execução do serviço, quando fizer
                                                                   sentido (um serviço pontual pode não ter
                                                                   período, só uma data de entrega).
                                                                   Desmembrado na revisão 15.

  **Data_Fim_Servico**          *data, opcional*                   ---

  **Data_Entrega_Prevista**     *data, opcional*                   O prazo combinado com o fornecedor para
                                                                   este item --- editável enquanto o pedido
                                                                   não estiver Status=recebido; é o que se
                                                                   renegocia quando o fornecedor substitui
                                                                   produto/prazo depois de uma recusa
                                                                   (seção 8). Comparado com a data real de
                                                                   aceite
                                                                   (Mov_Nota_Fiscal_Entrada.Data_Entrada)
                                                                   para avaliar atraso.

  **ID_Orcamento_Item**         *referência (Cad_Orcamento_Item,   O vínculo com o orçamento (módulo de
                                opcional)*                         Planejamento & Orçamento) --- quando
                                                                   preenchido, a aprovação deste pedido
                                                                   gera um Mov_Compromisso_Orcamentario
                                                                   contra esta linha (ver seção 5). Vazio
                                                                   para compras sem controle orçamentário
                                                                   linha a linha.

  **Local_Na_Contratante**      *booleano*                         Adicionado na revisão 17 (Bloco 2).
                                                                   Padrão sim. Sim = o local é o endereço
                                                                   do contratante; não = o local está em
                                                                   ID_Local_Operacao.

  **ID_Endereco_Contratante**   *referência                        Adicionado na revisão 17 (Bloco 2). A
                                (Cad_Participante_Endereco,        versão do endereço do contratante usada;
                                opcional)*                         preenchida quando Local_Na_Contratante =
                                                                   sim.

  **ID_Local_Operacao**         *referência (Cad_Local_Operacao,   Adicionado na revisão 17 (Bloco 2).
                                opcional)*                         Obrigatória quando Local_Na_Contratante
                                                                   = não; vazia quando = sim.

  **ID_Empreendimento**         *referência                        Adicionado na revisão 17 (Bloco 2). O
                                (Cad_Empreendimento_Imobiliario,   empreendimento a que a compra, a venda
                                opcional)*                         ou o crédito pertence. Vazio na maior
                                                                   parte das empresas, que não têm
                                                                   empreendimento.
  ----------------------------- ---------------------------------- ----------------------------------------

Mov_Pedido_Item_Destinacao

O vínculo entre uma linha do pedido e a(s) Destinação(ões)
contábil/fiscal que ela carrega (Cad_Destinacao, Fase 0) --- associação
N:N, permitindo ratear uma única linha entre mais de uma destinação
(ex.: uma compra dividida entre dois centros de custo ou dois projetos),
sempre de forma quantitativa para produto ou por fator para serviço ---
nunca por percentual único, que pode gerar valor fisicamente quebrado
num produto (ex.: 5 unidades em 30/40/30% não fecha em unidades inteiras
nem em frações com sentido).

*Vigência: não.*

  ------------------------------- ------------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                       **Descrição / regra**

  **ID_Pedido_Item_Destinacao**   *identificador*                       Adicionado na revisão 15 (chave primária
                                                                        declarada).

  **ID_Item**                     *referência (Mov_Pedido_Item)*        ---

  **ID_Destinacao**               *referência (Cad_Destinacao)*         ---

  **Quantidade**                  *número, opcional*                    Preenchido quando o item é produto --- a
                                                                        fração da Quantidade do item (mesma
                                                                        unidade de medida, aceita decimal ---
                                                                        ex.: 0,3kg/0,7kg de 1kg) atribuída a
                                                                        esta destinação. A soma das quantidades
                                                                        de uma mesma linha deve fechar na
                                                                        Quantidade total do item.

  **Fator**                       *número, opcional*                    Preenchido quando o item é serviço ---
                                                                        peso relativo (ex.: 0,3 e 0,7) usado
                                                                        para ratear o Valor_Total entre
                                                                        destinações, em vez de percentual
                                                                        inteiro (0--100), evitando
                                                                        arredondamento forçado a pontos
                                                                        percentuais.

  **ID_Habilitacao**              *referência                           Adicionado na revisão 17 (Bloco 2).
                                  (Cad_Habilitacao_Regime_Especial,     Preenchido quando essa parcela do item
                                  opcional)*                            será aplicada em projeto habilitado.

  **ID_Situacao_Suspensao**       *referência (Cad_Classe_Sistema,      Adicionado na revisão 17 (Bloco 2).
                                  domínio =                             Suspensa, convertida em alíquota zero ou
                                  situacao_suspensao_regime_especial,   revertida (tributo recolhido com juros e
                                  opcional)*                            multa por descumprimento). Preenchida
                                                                        quando há habilitação. No REIDI, a
                                                                        conversão vem depois da incorporação ou
                                                                        utilização do bem na obra; no REPES,
                                                                        depois de cumprida a condição de
                                                                        exportação.

  **Data_Conversao**              *data, opcional*                      Adicionado na revisão 17 (Bloco 2).
                                                                        Quando a suspensão virou alíquota zero
                                                                        ou foi revertida.
  ------------------------------- ------------------------------------- ----------------------------------------

3\. Cotação

Cotar não é o mesmo que comprar de quem já é fornecedor. Igual ao que já
vale do lado de vendas/CRM (ainda não especificado, mas já referenciado
nos documentos anteriores) --- nem todo mundo cotado vira, de fato,
fornecedor. Por isso a cotação reaproveita o mesmo mecanismo de
Cad_Pre_Cadastro/Mov_Pre_Cadastro_Conversao do Fase 0: cotar com uma
empresa que ainda não é Cad_Participante não obriga a cadastrá-la por
completo --- só o proponente vencedor (Escolhida=true) é efetivamente
convertido.

Mov_Cotacao

O cabeçalho do processo de cotação --- pode envolver um ou vários itens
(ver Mov_Cotacao_Item) e pode ou não terminar em um ou mais Mov_Pedido.

*Vigência: não.*

  ------------------ ----------------- ----------------------------------------
  **Campo**          **Tipo lógico**   **Descrição / regra**

  **ID_Cotacao**     *identificador*   ---

  **ID_Filial**      *referência       ---
                     (Cad_Filial)*     

  **Data_Cotacao**   *data*            ---

  **Status**         *enumeração       \"encerrada\" quando todo item da
                     {aberta,          cotação tiver um vencedor definido (ver
                     encerrada,        Mov_Cotacao_Proposta_Item.Escolhida) ---
                     cancelada}*       a aprovação pode ser parcial, item a
                                       item, não precisa ser tudo-ou-nada da
                                       cotação inteira.
  ------------------ ----------------- ----------------------------------------

Mov_Cotacao_Item

Um item sendo cotado dentro do processo --- é aqui, não no cabeçalho,
que mora o produto/serviço, exatamente para suportar uma cotação com N
itens.

*Vigência: não.*

  ------------------------ ------------------------ ----------------------------------------
  **Campo**                **Tipo lógico**          **Descrição / regra**

  **ID_Item_Cotacao**      *identificador*          ---

  **ID_Cotacao**           *referência              ---
                           (Mov_Cotacao)*           

  **ID_Produto_Servico**   *referência              ---
                           (Cad_Produto_Servico)*   

  **Quantidade**           *número*                 A quantidade sendo cotada deste item.
  ------------------------ ------------------------ ----------------------------------------

Mov_Cotacao_Proposta

O cabeçalho da proposta de um fornecedor (já cadastrado ou ainda não
efetivado) dentro da cotação --- o valor efetivamente proposto é por
item (ver Mov_Cotacao_Proposta_Item).

*Vigência: não.*

  --------------------- ------------------- -----------------------------------------------
  **Campo**             **Tipo lógico**     **Descrição / regra**

  **ID_Proposta**       *identificador*     ---

  **ID_Cotacao**        *referência         ---
                        (Mov_Cotacao)*      

  **Tipo_Proponente**   *enumeração         Diz qual cadastro ID_Proponente referencia ---
                        {participante,      mesmo padrão de referência genérica já usado em
                        pre_cadastro}*      Mov_Aprovacao_Instancia.Origem_Tipo/ID_Origem
                                            (Fase 0).

  **ID_Proponente**     *referência         ---
                        genérica,           
                        conforme            
                        Tipo_Proponente     
                        (Cad_Participante   
                        ou                  
                        Cad_Pre_Cadastro)*  

  **Prazo_Entrega**     *número (dias),     O prazo proposto para o conjunto cotado por
                        opcional*           este fornecedor.
  --------------------- ------------------- -----------------------------------------------

Mov_Cotacao_Proposta_Item

O valor proposto por um fornecedor para um item específico da cotação, e
quem venceu aquele item --- é aqui que a aprovação acontece, item a
item.

*Vigência: não.*

  --------------------- ------------------------ ----------------------------------------
  **Campo**             **Tipo lógico**          **Descrição / regra**

  **ID_Proposta**       *referência              ---
                        (Mov_Cotacao_Proposta)   
                        --- chave primária       
                        (composta)*              

  **ID_Item_Cotacao**   *referência              ---
                        (Mov_Cotacao_Item) ---   
                        chave primária           
                        (composta)*              

  **Valor_Proposto**    *número*                 ---

  **Escolhida**         *booleano*               Só a combinação proposta+item vencedora
                                                 tem Escolhida=true. A aprovação é por
                                                 item, não pela cotação inteira --- itens
                                                 de uma mesma cotação podem ser atendidos
                                                 por fornecedores diferentes (aprovação
                                                 total ou parcial). Quando o vencedor de
                                                 um item é Tipo_Proponente=pre_cadastro,
                                                 isso dispara o mesmo
                                                 Mov_Pre_Cadastro_Conversao do Fase 0,
                                                 promovendo-o a Cad_Participante (classe
                                                 fornecedor) --- os demais cotados,
                                                 vencedores ou não em outros itens,
                                                 permanecem como pré-cadastro, sem poluir
                                                 o cadastro definitivo.
  --------------------- ------------------------ ----------------------------------------

4\. Contratos de Fornecimento Contínuo

Esta seção cobria o contrato de fornecimento contínuo --- serviço
contínuo (ex.: limpeza) ou fornecimento contínuo de produto (ex.:
energia elétrica, materiais de limpeza/higiene com consumo previsível)
--- o que os unia não era ser produto ou serviço, era ter cobrança
recorrente, com valor sujeito a reajuste periódico, em vez de um pedido
pontual.

Nesta revisão (12), as entidades Cad_Contrato_Fornecimento e
Cad_Contrato_Fornecimento_Valor foram APOSENTADAS: a consolidação
identificou uma duplicação de cadastro de contrato entre este módulo e o
módulo Fase 6 --- Gestão de Contratos, construído depois e que já cobre
o mesmo conceito de forma mais completa --- cliente OU fornecedor no
mesmo cadastro, preço por item, entregável por etapa. Por decisão
explícita de Alberto: não faz sentido ter dois módulos de gerenciamento
de contrato, tem que ser um único que atenda as duas frentes.

O contrato de fornecimento contínuo agora nasce em Cad_Gestao_Contrato
(Fase 6), na posição Contratante --- a Mlegate como quem adquire, papel
derivado da classe do participante (fornecedor, Cad_Participante_Classe,
Fase 0), nunca um campo de papel próprio nesta entidade.

Dois campos migraram para lá: ID_Filial (referência Cad_Filial, Fase 0)
e Forma_Compromisso (enumeração {integral, mensal}) --- ambos só
preenchidos quando o contrato está na posição Contratante. Confirmado
por Alberto: no caso de venda não há compromisso orçamentário --- só na
aquisição ---, então em contrato de venda (posição Contratado) esses
campos ficam vazios e não geram compromisso orçamentário algum.

A aprovação do contrato em si também deixou de reaproveitar a régua de
Origem_Tipo=pedido_compra deste módulo: Cad_Gestao_Contrato ganhou sua
própria instância de aprovação na criação (novo campo
ID_Instancia_Aprovacao, referência a Mov_Aprovacao_Instancia, Fase 0),
com Origem_Tipo=contrato_aquisicao quando a Mlegate está na posição
Contratante --- o caso que interessa a este documento de Compras (o
reajuste/valor do contrato passou a usar o mecanismo próprio de
Cad_Gestao_Contrato --- Modelo_Valor, Valor_Fixo,
ID_Serie_Cotacao_Reajuste, Periodicidade_Reajuste --- e
Cad_Gestao_Contrato_Item quando o preço é quebrado por produto/serviço).

*Ver Fase 6 --- Gestão de Contratos, seção 2, para o desenho completo do
cadastro do contrato.*

5\. Aprovação e Compromisso Orçamentário

A aprovação do pedido reaproveita a régua de aprovação inteira do Fase 0
(Cad_Regua_Aprovacao, Cad_Regua_Faixa, Cad_Regua_Aprovador,
Cad_Usuario_Escopo), sem nenhuma estrutura nova --- só um novo gatilho:
Mov_Aprovacao_Instancia.Origem_Tipo = pedido_compra, uma pequena
extensão pontual ao dicionário Fase 0, no mesmo espírito de
aprovacao_orcamento --- já incorporada na revisão 9. A instância
resultante fica referenciada em Mov_Pedido.ID_Instancia_Aprovacao.

No momento em que o pedido é aprovado, cada Mov_Pedido_Item que tiver
ID_Orcamento_Item preenchido gera um Mov_Compromisso_Orcamentario (já
definido no módulo de Planejamento & Orçamento): Origem_Tipo =
pedido_item, ID_Origem = o próprio ID_Item deste pedido. Isso fecha a
suposição que ficou em aberto nas Notas daquele módulo --- o vínculo
entre o compromisso e sua origem real. O compromisso permanece
Status=aberto até a nota fiscal de entrada correspondente ser lançada
(Status=baixado) ou o pedido ser cancelado (Status=cancelado).

O compromisso orçamentário do contrato de fornecimento contínuo passou a
ser gerado pela aprovação do próprio Cad_Gestao_Contrato (Fase 6 ---
Gestão de Contratos, seção 2 e 3), usando Origem_Tipo=contrato_aquisicao
--- mesmo comportamento de Forma_Compromisso{integral,mensal} de antes,
só que o campo e o gatilho agora vivem lá, junto com o cadastro único de
contrato.

Quando um pedido é cancelado (Status=cancelado) --- por exemplo depois
de uma recusa de recebimento não resolvida, ver seção 8 --- o(s)
Mov_Compromisso_Orcamentario gerado(s) por ele são estornados. Um
eventual novo pedido, normalmente para outro fornecedor, entra no fluxo
normal de aprovação e gera seu próprio compromisso; ele só referencia o
pedido cancelado via ID_Pedido_Origem (seção 2) para fins de
rastreabilidade --- não há vínculo automático de saldo entre os dois
compromissos.

6\. Nota Fiscal de Entrada e o Motor de Regras

A nota fiscal de entrada registra o documento fiscal do fornecedor,
casada (quando existir) com o pedido que a originou. A tributação de
entrada --- quais créditos de IBS/CBS a empresa tem direito a se
apropriar, por exemplo --- é decidida pelo Motor de Regras
(Cad_Motor_Regra, Fase 0), reaproveitando a mesma estrutura genérica já
usada para o esquema de nota de serviço: critérios em linha
(Cad_Motor_Regra_Criterio, ex.: fornecedor, produto), resultado também
em linha (Cad_Motor_Regra_Resultado, o CST/cClassTrib decidido).
Confirmado por Alberto na consolidação da Fase 0 (revisão 24): a regra
concreta usa TRÊS critérios combinados --- fornecedor +
produto_servico + cfop --- nunca um campo estático de sugestão no
cadastro do produto, mesmo quando a variação na prática é pequena.

Princípio geral, válido para toda nota fiscal (e que deve valer também
para a futura nota fiscal de saída, no módulo de CRM & Vendas): o
sistema nunca recalcula um valor fiscal --- sempre usa o valor tal como
está na nota. Quantidade × Valor_Unitário pode divergir do valor real do
item por causa de dízimas/arredondamento do emissor; por isso
Valor_Total é sempre um campo próprio, preenchido com o que está na
nota, nunca derivado. O mesmo vale no cabeçalho:
Mov_Nota_Fiscal_Entrada.Valor_Total é o valor total tal como emitido,
não a soma recalculada dos itens. Qualquer conferência entre valor
informado e valor recalculado serve só como alerta de divergência para o
usuário --- nunca substitui o valor guardado.

*Cross-referenciado nesta revisão (14): Valor_Total desta nota é o que
nasce como Mov_Titulo.Valor_Titulo (Contas a Pagar/Receber, seção 2, via
Mov_Pedido_Parcela quando houver parcelamento) --- mas o valor de fato
pago ao fornecedor pode ser menor, por retenção na fonte que a própria
Mlegate faz ao pagar, ou por split payment do IBS/CBS na baixa: nenhuma
estrutura nova aqui, só a referência cruzada --- ver Contas a
Pagar/Receber, seções 3 e 11 daquele documento (Mov_Titulo_Retencao,
Fase 2 --- Contabilidade & Fiscal, seção 11).*

Mov_Nota_Fiscal_Entrada

O cabeçalho da nota fiscal de entrada.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Nota** | *identificador* | --- |
| **ID_Pedido** | *referência (Mov_Pedido, opcional)* | Casamento com o pedido que originou a compra --- vazio para compras sem pedido formal (ex.: despesas pequenas, cartão corporativo) ou para a nota recorrente de um Cad_Gestao_Contrato (Fase 6). |
| **ID_Contrato** | *referência (Cad_Gestao_Contrato, Fase 6 --- Gestão de Contratos, opcional)* | Casamento com o contrato (Fase 6), quando a nota corresponde a uma cobrança de contrato de fornecimento contínuo (posição Contratante). |
| **ID_Participante_Fornecedor** | *referência (Cad_Participante)* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | A filial que recebeu a nota. |
| **Numero** | *código (até 15)* | Identificação fiscal da nota, conforme emitida pelo fornecedor. Desmembrado na revisão 15. |
| **Serie** | *código (até 5)* | Revisão 19 (Bloco 4): passou de 3 para 5 posições, porque o campo serie da EFD-Reinf aceita até 5 caracteres (nota fiscal, fatura ou Recibo Provisório de Serviço). Revisão 16 (documento 82, D-N247): o R-2010 e o R-2020 pedem série de 1 a 5 posições e "0" (zero) quando o documento não tem série; nota sem série (fatura, Recibo Provisório de Serviço ou outro documento) grava 0. |
| **Chave_Acesso** | *código (até 50)* | Adicionado nesta revisão (6), pedido por Alberto como princípio geral: toda referência a nota fiscal no dicionário precisa carregar a chave de acesso da NFe --- identifica o documento nacionalmente (DV mod 11). Alterado na revisão 3: tipo atualizado. |
| **Data_Emissao** | *data* | A data de emissão pelo fornecedor. Desmembrado na revisão 15. |
| **Data_Entrada** | *data* | A data de entrada na empresa --- pode ser diferente da emissão, relevante para prazo de escrituração. |
| **Valor_Total** | *número* | O valor total tal como emitido na nota --- nunca recalculado a partir da soma dos itens (ver princípio acima). |
| **Status** | *enumeração {lancada, recusada, cancelada}* | \"recusada\" quando a nota chegou mas não foi aceita no recebimento --- ver seção 8. Nesse caso não baixa compromisso orçamentário nem gera movimento de estoque, mas fica registrada para consulta e para avaliar prazo/atraso do fornecedor. |
| **Motivo_Recusa** | *texto, opcional* | Preenchido só quando Status=recusada. |
| **ID_Usuario_Responsavel** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (8), pedido pela consolidação: quem decidiu Status=recusada/cancelada nesta nota --- ao lado de Motivo_Recusa, dá também o QUEM, não só o porquê, para fins de auditoria/responsabilização da decisão. |
| **ID_Modelo_Documento** | *referência (Cad_Modelo_Documento_Fiscal)* | Alterado na revisão 3 (documento 43). Modelo do documento fiscal (55, 57, 65, NFS-e e demais), do cadastro de modelos; o código de cada obrigação (COD_MOD da EFD e outros) vem de Cad_Modelo_Documento_Fiscal_Codigo. Adicionado na revisão 17 (Bloco 2); apontava o domínio modelo_documento_fiscal (tabela 4.1.1) até a revisão 3. |
| **ID_Situacao_Documento** | *referência (Cad_Classe_Sistema, domínio = situacao_documento_fiscal)* | Adicionado na revisão 17 (Bloco 2). Tabela 4.1.2 --- regular, cancelado, denegado, inutilizado, complementar, extemporâneo e demais. |
| **Finalidade** | *enumeração {normal, complementar, ajuste, devolucao, substituicao, credito, debito}* | Adicionado na revisão 17 (Bloco 2). finNFe. Revisão 7 (documento 60, D-N141): substituicao, finalidade de substituição da NFCom e da NFAg recebidas (hoje só a nota de saída tinha). Revisão 30 (documento 168, seção 3.2, G2; Q168-1, "finalidade própria"): credito e debito, que a nota de saída já tinha; a nota de crédito por redução de valores ou quantidades (COD_SIT 09 do C100, exceção 12 a partir de 01/01/2027) entra com a finalidade credito. |
| **Natureza_Operacao** | *texto* | Adicionado na revisão 17 (Bloco 2). natOp. Revisão 19 (D-N280): a nota de entrada emitida pelo adquirente vale para qualquer compra que exija a emissão, com o mesmo fluxo da D-N71 e da D-N23; só mudam os parâmetros: se gera crédito presumido e com qual coeficiente por ano e categoria (arts. 247 e 253 do Decreto 12.955/2026, Cad_Credito_Presumido_Categoria). A nota que não gera crédito presumido emite do mesmo jeito e só não abre o crédito. |
| **Indicador_Consumidor_Final** | *booleano* | Adicionado na revisão 17 (Bloco 2). Na nota, porque no leiaute é por operação. O padrão vem do indicador da IE do destinatário (não contribuinte = consumidor final). |
| **ID_Indicador_Presenca** | *referência (Cad_Classe_Sistema, domínio = indicador_presenca)* | Adicionado na revisão 17 (Bloco 2). indPres. |
| **Protocolo_Autorizacao** | *código (até 16), opcional* | Adicionado na revisão 17 (Bloco 2). Vazio até a autorização (saída) ou quando o documento não é eletrônico. Revisão 7 (documento 60): passa de até 15 para até 16 posições, como já está em Mov_Nota_Fiscal_Saida e Mov_Documento_Fiscal (a NFCom tem 16). |
| **Data_Hora_Autorizacao** | *data/hora, opcional* | Adicionado na revisão 17 (Bloco 2). |
| **ID_Modalidade_Frete** | *referência (Cad_Classe_Sistema, domínio = modalidade_frete)* | Adicionado na revisão 17 (Bloco 2). modFrete: emitente, destinatário, terceiros, sem frete. |
| **Data_Hora_Saida_Entrada** | *data/hora* | Adicionado na revisão 17 (Bloco 2). Prazo de escrituração e DIFAL. |
| **ID_Documento_Fiscal** | *referência (Mov_Documento_Fiscal, opcional)* | Novo na revisão 3 (documento 33). O documento fiscal (chave, protocolo, status, XML) desta nota recebida; vazio na nota não eletrônica. D-N1: Chave_Acesso, Protocolo_Autorizacao e Data_Hora_Autorizacao continuam aqui como cópia gravada. Revisão 16 (documento 80, D-N240): quando a nota de entrada nasce de uma NFTS emitida pela Mlegate (Mov_Nfts), aponta o documento fiscal da NFTS (Papel = emitido). Numero recebe o Numero_Nfts, Data_Emissao a data de emissão da NFTS e Serie, quando o leiaute da NFTS a tem, a série informada, ou 0 se não tem. Provisório até a confirmação do contador (Q80-1). |
| **Data_Previsao_Entrega** | *data, opcional* | Novo na revisão 3 (documento 34). ide/dPrevEntrega: data de previsão de entrega ou disponibilização do bem (RTC); o evento 112150 a atualiza. |
| **ID_Tipo_Nota_Debito** | *referência (Cad_Classe_Sistema, domínio = tipo_nota_debito), opcional* | Novo na revisão 3 (documento 34). ide/tpNFDebito: tipo da nota de débito (finalidade 6), 8 tipos na NF-e; na NFS-e valem só 01 a 06. |
| **ID_Tipo_Nota_Credito** | *referência (Cad_Classe_Sistema, domínio = tipo_nota_credito), opcional* | Novo na revisão 3 (documento 34). ide/tpNFCredito: tipo da nota de crédito (finalidade 5), 6 tipos na NF-e; na NFS-e valem só 01 e 05. |
| **Escriturada_Como_Saida** | *booleano, opcional* | Revisão 30 (documento 168, seção 3.2, G2, Q168-1; D-N460 e D-N461): Verdadeiro na nota de crédito de redução emitida por terceiro: a EFD a registra com IND_OPER 1 (saída) e IND_EMIT 1. Só preenchido na finalidade credito. |
| **Indicador_Intermediador** | *enumeração {sem_intermediador, plataforma_terceiros}, opcional* | Novo na revisão 3 (documento 34). ide/indIntermed: operação sem intermediador (site ou plataforma própria) ou em site ou plataforma de terceiros (marketplace, delivery). |
| **ID_Participante_Intermediador** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 34). infIntermed/CNPJ: intermediador da transação; obrigatório quando Indicador_Intermediador = plataforma_terceiros. |
| **Identificador_Cadastro_Intermediador** | *código (até 60), opcional* | Novo na revisão 3 (documento 34). infIntermed/idCadIntTran: identificador do vendedor cadastrado no intermediador. |
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
| **ID_Participante_Transportadora** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 34). transp/transporta: transportadora (CNPJ ou CPF, nome, IE, endereço) como participante. |
| **ID_Entidade_Ligada** | *referência (Cad_Entidade_Ligada_Reinf, opcional)* | Novo na revisão 3 (documento 44). SCP a que a nota pertence (A100 e 0035). |
| **Indicador_Pagamento** | *enumeração {a_vista, a_prazo, outros}* | Novo na revisão 3 (documento 44). Indicador de pagamento da nota de entrada (C100.IND_PGTO); na saída o equivalente é Indicador_Prazo de Mov_Nota_Fiscal_Saida_Pagamento (doc 33). |
| **Valor_Abatimento_Nao_Tributado** | *número, opcional* | Novo na revisão 3 (documento 44). Valor do abatimento não tributado e não comercial (C100.VL_ABAT_NT). |
| **Subserie** | *código (até 3), opcional* | Novo na revisão 3 (documento 44). Subsérie do documento, nos modelos legados (C395 e C500). |

*Revisão 7 --- campos alterados: Protocolo_Autorizacao; valores de enumeração novos: Finalidade (+substituicao).*

*Revisão 3 --- campos novos (documento 33): ID_Documento_Fiscal; campos novos (documento 34): Data_Previsao_Entrega, ID_Tipo_Nota_Debito, ID_Tipo_Nota_Credito, Indicador_Intermediador, ID_Participante_Intermediador, Identificador_Cadastro_Intermediador, Informacoes_Complementares, Informacoes_Fisco, Numero_Nota_Empenho, Numero_Pedido_Compra, Numero_Contrato, ID_Estado_Saida_Pais, Local_Exportacao, Local_Despacho, ID_Indicador_Operacao, Safra_Cana, Competencia_Cana, Quantidade_Total_Mes_Cana, Quantidade_Total_Anterior_Cana, Quantidade_Total_Geral_Cana, Valor_Fornecimentos_Cana, Valor_Total_Deducoes_Cana, Valor_Liquido_Fornecimentos_Cana, ID_Participante_Transportadora; campos novos (documento 44): ID_Entidade_Ligada, Indicador_Pagamento, Valor_Abatimento_Nao_Tributado, Subserie; campos alterados (documento ?): Chave_Acesso; campos alterados (documento 43): ID_Modelo_Documento.*

*Revisão 16 --- campos alterados: Serie, ID_Documento_Fiscal.*

*Revisão 19 --- campos alterados: Natureza_Operacao.*

*Revisão 30 --- campos novos: Escriturada_Como_Saida; valores de enumeração novos: Finalidade (+credito, debito).*

*Comportamento de aplicação (não é um campo novo de dados): pelo mesmo
motor transversal da Fase 0 (seção 10), nenhuma Mov_Nota_Fiscal_Entrada
pode ser lançada ou alterada com Data_Entrada dentro de uma competência
já fechada para a Filial (ID_Filial acima) no bloco \"compras\" ---
mesma consulta a Cad_Periodo_Fechamento_Filial e o mesmo regime
fail-closed descritos na seção 2. Compras é o único bloco de todo o
dicionário com uma validação adicional de PENDÊNCIA no próprio momento
do fechamento (e não no lançamento): não é possível fechar o período de
Compras para uma Filial+Competência enquanto existir, naquela
competência+filial, nota fiscal de entrada ainda em conferência de
qualidade pendente --- isto é, com item sujeito a inspeção
(Cad_Produto_Servico.Requer_Inspecao ou herdado por dimensão, seção 7)
que ainda não tenha um Mov_Pedido_Item_Inspecao com Resultado
preenchido. A regra existe porque a inspeção pode reprovar o item depois
que a nota já foi lançada, disparando Mov_Estoque_Condicao (seção 7) ---
o fechamento não deve congelar uma competência com esse desfecho ainda
em aberto.*

*Outro comportamento de aplicação (não um campo novo): no lançamento de
cada nota, o sistema compara Quantidade/Valor_Total dos itens contra o
que está no pedido correspondente --- considerando o ACUMULADO de todas
as notas já lançadas contra o mesmo Mov_Pedido_Item, já que um único
pedido pode ser recebido em várias notas --- e alerta o usuário em caso
de divergência. Esse alerta nunca substitui o valor guardado (mesmo
princípio de fidelidade à nota, acima); serve só para o usuário decidir
se aceita, questiona o fornecedor, ou recusa o recebimento
(Status=recusada, seção 8).*

Mov_Nota_Fiscal_Entrada_Item

Uma linha da nota fiscal de entrada, com a tributação decidida pelo
Motor de Regras e o CFOP tratado por conversão.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Nota** | *referência (Mov_Nota_Fiscal_Entrada)* | --- |
| **ID_Pedido_Item** | *referência (Mov_Pedido_Item, opcional)* | Casamento com a linha do pedido, quando existir --- usado para baixar o Mov_Compromisso_Orcamentario correspondente (seção 5) e para o alerta de divergência acumulada acima. |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico)* | --- |
| **Quantidade** | *número* | Revisão 30 (documento 168, seção 3.2, G2): a quantidade zero é aceita na nota de crédito de redução (2026; Ajuste SINIEF 49/2025); o aviso de "quantidade maior que zero" não dispara nessa finalidade. |
| **Valor_Unitario** | *número* | --- |
| **Valor_Total** | *número* | O valor do item tal como está na nota --- não recalculado a partir de Quantidade × Valor_Unitario, que pode divergir por dízimas/arredondamento do emissor. |
| **ID_CFOP_Origem** | *referência (Cad_CFOP, Fase 0)* | O CFOP tal como veio na nota do fornecedor (a saída dele). |
| **ID_CFOP_Entrada** | *referência (Cad_CFOP, Fase 0)* | O CFOP efetivamente usado na entrada da empresa --- pode ser diferente do de origem. Sugerido pelo Motor de Regras (critério=CFOP_Origem, podendo considerar também fornecedor/produto/destinação; resultado=CFOP_Entrada sugerido), mas sempre confirmável/ajustável pelo usuário. |
| **ID_Cst** | *referência (Cad_Cst, Fase 2 --- Contabilidade & Fiscal)* | Renomeado/redirecionado na revisão 7 --- antes ID_CST_IBS_CBS, apontando para o domínio cst_ibs_cbs (aposentado, Fase 0 revisão 23). Decidido pelo Motor de Regras no momento do lançamento --- critérios fornecedor + produto_servico + cfop, confirmados por Alberto na Fase 0 revisão 24 (seção 8 daquele documento); nunca uma sugestão estática de cadastro. |
| **ID_Cclasstrib** | *referência (Cad_Cclasstrib, Fase 2 --- Contabilidade & Fiscal, opcional)* | Renomeado/redirecionado na revisão 7 --- antes ID_ClassTrib, apontando para a extinta Cad_ClassTrib (Fase 0). Idem, decidido pelo Motor de Regras pelos mesmos três critérios; só preenchido quando ID_Cst for de CBS/IBS. |
| **Valor_Credito_Tributario** | *número, opcional* | Adicionado pedido pela especificação do módulo Fase 1 --- Estoque: o valor do crédito de imposto destacado na nota quando o item é recebido em bonificação/amostra grátis --- o produto em si não é pago (o Valor_Total acima reflete a operação sem cobrança), mas o imposto que o emitente pagou na saída pode ser creditado por quem recebe. É este valor, não o Valor_Total do item, que o Estoque usa como referência de valor na entrada por bonificação (Mov_Estoque_Movimento_Item.ID_Valor_Referencia apontando para este campo). |
| **Numero_Processo_Suframa** | *código (até 20), opcional* | Adicionado nesta revisão (7), pedido pela consolidação da Fase 2 Contabilidade & Fiscal (seção 9): a partir de agosto de 2026, a NF-e passa a exigir o número do processo Suframa por item quando a operação envolve a Zona Franca de Manaus/Área de Livre Comércio --- preenchido quando este item entra por remessa nacional com o benefício, ou quando o próprio fornecedor está estabelecido na ZFM/ALC. |
| **ID_Classificacao_NCM** | *referência (Cad_Classificacao_Mercadoria, opcional)* | Renomeado na revisão 42 (antes ID_NCM, para o extinto Cad_NCM) --- código analítico da nomenclatura NCM. Adicionado nesta revisão (6): o NCM tal como veio na nota do fornecedor, congelado no momento da entrada --- não deriva de Cad_Produto_Servico_Dados_Produto.ID_NCM (que tem vigência própria), porque o que o fornecedor declarou na nota pode diferir do NCM do nosso próprio cadastro, e uma correção posterior do cadastro não pode alterar retroativamente o que já foi lançado. |
| **ID_Unidade_Medida** | *referência (Cad_Unidade_Medida, opcional)* | Idem, congelado no momento da entrada. |
| **ID_NBS** | *referência (Cad_NBS, opcional)* | Preenchido quando o item é serviço --- mesma lógica de snapshot do NCM, aplicada ao NBS. |
| **Codigo_Servico_Municipal** | *código (até 20), opcional* | Preenchido quando o item é serviço --- snapshot do código municipal usado na entrada; Cad_Produto_Servico_Codigo_Municipal (Fase 0) pode mudar por atualização da lista do município, sem afetar notas já lançadas. |
| **Descricao_Produto_Servico** | *texto, opcional* | A descrição tal como consta na nota do fornecedor --- não precisa ser idêntica a Cad_Produto_Servico.Descricao, que pode ser renomeada depois sem afetar o que já foi lançado. |
| **ID_Participante_Cliente_Atendido** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (9), pedido pela especificação do módulo Fase 1 Expedição: preenchido quando este item é uma despesa de frete/serviço de transporte (CT-e de uma transportadora) contratada para atender uma entrega específica a um cliente --- marca QUAL cliente foi atendido, para que o BI calcule resultado por cliente incluindo o custo real de frete, distinto do Valor_Frete_Negociado cobrado dele (CRM & Vendas). Vazio para qualquer outra compra que não seja frete atribuível a um cliente específico --- não é um campo genérico de toda nota de entrada, só um gancho pontual para este caso. |
| **Numero_Item** | *número* | Adicionado na revisão 17 (Bloco 2). nItem --- sequencial dentro da nota. |
| **Valor_Desconto_Item** | *número, opcional* | Adicionado na revisão 17 (Bloco 2). Revisão 30 (documento 156, seção 5.7, Q156-13): passa a ser só o desconto incondicional; o condicional fica em Valor_Desconto_Condicional_Item. |
| **Valor_Desconto_Condicional_Item** | *número, opcional* | Revisão 30 (documento 156, seção 5.7, Q156-13; D-N463 e D-N465): O desconto concedido sob condição, que não reduz a base (integra, art. 12, § 1º, III da LC 214). Revisão 30 (documento 156, seção 5.7, Q156-13): Valor_Desconto_Item passa a significar só o incondicional (consta do documento fiscal e não depende de evento posterior, § 3º). Se o leiaute da NF-e não separar os dois, o campo é controle do ERP e não vai no XML (Q156-E1). |
| **Valor_Frete_Item** | *número, opcional* | Adicionado na revisão 17 (Bloco 2). Rateio do frete do cabeçalho. |
| **Valor_Seguro_Item** | *número, opcional* | Adicionado na revisão 17 (Bloco 2). |
| **Valor_Outras_Despesas_Item** | *número, opcional* | Adicionado na revisão 17 (Bloco 2). |
| **ID_Origem_Mercadoria** | *referência (Cad_Classe_Sistema, domínio = origem_mercadoria)* | Adicionado na revisão 17 (Bloco 2). Cópia do produto. |
| **ID_Cest** | *referência (Cad_Cest, opcional)* | Adicionado na revisão 17 (Bloco 2). Cópia. |
| **ID_Ex_Tipi** | *referência (Cad_NCM_Ex_Tipi, opcional)* | Adicionado na revisão 17 (Bloco 2). Cópia. |
| **Gtin** | *código (até 14), opcional* | Adicionado na revisão 17 (Bloco 2). Cópia. |
| **ID_Beneficio_Fiscal_Icms** | *referência (Cad_Beneficio_Fiscal_Icms, opcional)* | Adicionado na revisão 17 (Bloco 2). cBenef --- exigido por várias UFs quando o CST indica isenção, redução ou diferimento. |
| **ID_Servico_Tributacao** | *referência (Cad_Servico_Tributacao_Nacional, opcional)* | Adicionado na revisão 17 (Bloco 2). cTribNac --- só em item de serviço. |
| **Local_Na_Contratante** | *booleano* | Adicionado na revisão 17 (Bloco 2). Padrão sim. Sim = o local é o endereço do contratante; não = o local está em ID_Local_Operacao. |
| **ID_Endereco_Contratante** | *referência (Cad_Participante_Endereco, opcional)* | Adicionado na revisão 17 (Bloco 2). A versão do endereço do contratante usada; preenchida quando Local_Na_Contratante = sim. |
| **ID_Local_Operacao** | *referência (Cad_Local_Operacao, opcional)* | Adicionado na revisão 17 (Bloco 2). Obrigatória quando Local_Na_Contratante = não; vazia quando = sim. |
| **ID_Criterio_Local_Operacao** | *referência (Cad_Classe_Sistema, domínio = criterio_local_operacao, opcional)* | Adicionado na revisão 17 (Bloco 2). Só nas notas. A regra aplicada: entrega do bem, domicílio do adquirente, local do imóvel, local da prestação, entre outras. |
| **ID_Municipio_Incidencia_Ibs** | *referência (Cad_Municipio, opcional)* | Adicionado na revisão 17 (Bloco 2). Só nas notas. O município de destino do IBS, e, por ele, a UF. |
| **ID_Municipio_Incidencia_Iss** | *referência (Cad_Municipio, opcional)* | Adicionado na revisão 17 (Bloco 2). Só nas notas. Na NFS-e de saída, o cLocIncid devolvido pelo ambiente nacional. |
| **ID_Empreendimento** | *referência (Cad_Empreendimento_Imobiliario, opcional)* | Adicionado na revisão 17 (Bloco 2). O empreendimento a que a compra, a venda ou o crédito pertence. Vazio na maior parte das empresas, que não têm empreendimento. |
| **ID_Unidade_Tributavel** | *referência (Cad_Unidade_Medida, opcional)* | Novo na revisão 3 (documento 34). det/prod/uTrib: unidade tributável, que pode diferir da comercial (NCM com unidade de medida própria). |
| **Quantidade_Tributavel** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/qTrib: quantidade tributável (0 a 4 decimais). |
| **Valor_Unitario_Tributavel** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vUnTrib: valor unitário de tributação (até 10 decimais). |
| **Gtin_Tributavel** | *código (até 14), opcional* | Novo na revisão 3 (documento 34). det/prod/cEANTrib: GTIN da unidade tributável, diferente de Gtin (cEAN); a NT 2021.003 valida os dois contra o Cadastro Centralizado (grupo V a partir de 01/09/2027). |
| **Indicador_Bem_Movel_Usado** | *booleano, opcional* | Novo na revisão 3 (documento 34). det/prod/indBemMovelUsado: fornecimento de bem móvel usado (RTC). |
| **Numero_Pedido_Cliente** | *código (até 15), opcional* | Novo na revisão 3 (documento 34). det/prod/xPed: pedido de compra do cliente, para controle do B2B. |
| **Item_Pedido_Cliente** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/nItemPed: número do item do pedido de compra do cliente. |
| **Numero_Fci** | *código (até 36), opcional* | Novo na revisão 3 (documento 34). det/prod/nFCI: número de controle da Ficha de Conteúdo de Importação. |
| **Indicador_Doacao** | *booleano, opcional* | Novo na revisão 3 (documento 34). det/imposto/IBSCBS/indDoacao: a operação do item é de doação (decidido pelo tpDoacao do cClassTrib). |
| **Informacoes_Adicionais_Item** | *texto, opcional* | Novo na revisão 3 (documento 34). det/infAdProd: informações adicionais do produto (até 500 posições). |
| **Percentual_Devolvido** | *número, opcional* | Novo na revisão 3 (documento 34). det/impostoDevol/pDevol: percentual da mercadoria devolvida. |
| **Valor_Ipi_Devolvido** | *número, opcional* | Novo na revisão 3 (documento 34). det/impostoDevol/IPI/vIPIDevol: valor do IPI devolvido. |
| **Valor_Unitario_Liquido** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vUnComLiq (NT 2026.008): valor unitário líquido, sem IBS, CBS e Imposto Seletivo. Produção em 03/11/2026. |
| **Valor_Total_Liquido** | *número, opcional* | Novo na revisão 3 (documento 34). det/prod/vProdLiq (NT 2026.008): valor total líquido do item; o total da nota (vProdLiqTot) é derivado. |
| **ID_Indicador_Operacao** | *referência (Cad_Indicador_Operacao, opcional)* | Novo na revisão 3 (documento 34). IBSCBS/cIndOp: indicador da operação de fornecimento (6 dígitos; tabela do Anexo C, 27 códigos); o critério de local de operação passa a derivado dele. |
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
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, opcional)* | Novo na revisão 3 (documento 44). Conta contábil analítica do item (COD_CTA), obrigatória na EFD desde 11/2017. |
| **ID_Natureza_Frete_Efd** | *referência (Cad_Classe_Sistema, domínio = natureza_frete_efd, opcional)* | Novo na revisão 3 (documento 44). Natureza do frete (D101 e D105.IND_NAT_FRT). |
| **Chave_Dfe_Pagamento_Antecipado** | *código (44), opcional* | Revisão 29 (documento 165, seção 7, Q165-7): gPagAntecipado/chDFePagAnt: a chave do DF-e do pagamento antecipado citado pelo item; vale para NFGas, NF3e, NFAg e NFCom. Conferido no dicionário da revisão 28: o campo não existia (Q165-E1). |
| **Numero_Item_Pagamento_Antecipado** | *número, opcional* | Revisão 29 (documento 165, seção 7, Q165-7): nItemPagAnt: o número do item do DF-e do pagamento antecipado. |
| **Data_Fato_Gerador** | *data, opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): A data que o ERP usou. Vazia quando não há linha de regra vigente (e então há aviso). |
| **Criterio_Data_Fato_Gerador** | *enumeração {data_previsao_entrega, data_emissao_documento, data_entrega_comprovada, data_inicio_transporte, data_termino_transporte, data_termino_servico, data_ato, data_pagamento, data_emissao_fatura, data_liberacao_aduaneira, data_constatacao, data_aquisicao}, opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): De onde a data veio. Com prova em contrário da data prevista (Decreto, art. 11, § 8º), passa a data_entrega_comprovada e o usuário informa a data. |
| **ID_Regra_Fato_Gerador** | *referência (Cad_Regra_Fato_Gerador), opcional* | Revisão 31 (documento 157, seção 3.3, Q157-1; D-N466 e D-N469): A versão da regra usada. |

*Revisão 3 --- campos novos (documento 34): ID_Unidade_Tributavel, Quantidade_Tributavel, Valor_Unitario_Tributavel, Gtin_Tributavel, Indicador_Bem_Movel_Usado, Numero_Pedido_Cliente, Item_Pedido_Cliente, Numero_Fci, Indicador_Doacao, Informacoes_Adicionais_Item, Percentual_Devolvido, Valor_Ipi_Devolvido, Valor_Unitario_Liquido, Valor_Total_Liquido, ID_Indicador_Operacao, Codigo_Tipo_Credito_Presumido_Zfm, Numero_Recopi, Veiculo_Tipo_Operacao, Veiculo_Chassi, Veiculo_Codigo_Cor, Veiculo_Descricao_Cor, Veiculo_Potencia_Cv, Veiculo_Cilindrada_Cc, Veiculo_Peso_Liquido, Veiculo_Peso_Bruto, Veiculo_Numero_Serie, Veiculo_Codigo_Combustivel, Veiculo_Numero_Motor, Veiculo_Capacidade_Tracao, Veiculo_Distancia_Eixos, Veiculo_Ano_Modelo, Veiculo_Ano_Fabricacao, Veiculo_Tipo_Pintura, Veiculo_Codigo_Tipo, Veiculo_Codigo_Especie, Veiculo_Vin_Remarcado, Veiculo_Condicao, Veiculo_Codigo_Marca_Modelo, Veiculo_Codigo_Cor_Denatran, Veiculo_Lotacao, Veiculo_Restricao, Medicamento_Registro_Anvisa, Medicamento_Motivo_Isencao, Medicamento_Preco_Maximo_Consumidor, Arma_Tipo, Arma_Numero_Serie, Arma_Numero_Cano, Arma_Descricao, Combustivel_Codigo_Anp, Combustivel_Descricao_Anp, Combustivel_Percentual_Glp, Combustivel_Percentual_Gas_Natural_Nacional, Combustivel_Percentual_Gas_Natural_Importado, Combustivel_Valor_Partida, Combustivel_Codigo_Codif, Combustivel_Quantidade_Temperatura_Ambiente, ID_Estado_Consumo_Combustivel, Combustivel_Cide_Base, Combustivel_Cide_Aliquota, Combustivel_Cide_Valor, Combustivel_Numero_Bico, Combustivel_Numero_Bomba, Combustivel_Numero_Tanque, Combustivel_Encerrante_Inicial, Combustivel_Encerrante_Final, Combustivel_Percentual_Biodiesel, Combustivel_Indicador_Importado, ID_Estado_Origem_Combustivel, Combustivel_Percentual_Origem; campos novos (documento 44): Natureza_Operacao, ID_Conta_Contabil, ID_Natureza_Frete_Efd.*

*Revisão 29 --- campos novos: Chave_Dfe_Pagamento_Antecipado, Numero_Item_Pagamento_Antecipado.*

*Revisão 30 --- campos novos: Valor_Desconto_Condicional_Item; campos alterados: Valor_Desconto_Item, Quantidade.*

*Revisão 31 --- campos novos: Data_Fato_Gerador, Criterio_Data_Fato_Gerador, ID_Regra_Fato_Gerador.*

*Comportamento de aplicação (não é um campo novo de dados): toda vez que
o usuário confirma ou corrige a sugestão de ID_CFOP_Entrada, essa
confirmação/correção deve realimentar a regra correspondente em
Cad_Motor_Regra --- é assim que o sistema \"aprende com o tempo\", sem
exigir que a tabela de conversão de CFOP seja pré-configurada
manualmente por completo desde o início.*

Mov_Nota_Fiscal_Entrada_Item_Destinacao

O vínculo entre uma linha da nota fiscal e a(s) Destinação(ões)
contábil/fiscal --- só obrigatório preencher quando a nota não tem
pedido de origem (ID_Pedido_Item vazio, acima): sem pedido, não há de
onde herdar destinação/conta, então quem lança a nota precisa amarrar
aqui. Quando há pedido, a destinação já está definida em
Mov_Pedido_Item_Destinacao e esta tabela fica dispensável.

*Vigência: não.*

  ----------------------------- ------------------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**                       **Descrição / regra**

  **ID_Nota_Item_Destinacao**   *identificador*                       Adicionado na revisão 15 (chave primária
                                                                      declarada).

  **ID_Item**                   *referência                           ---
                                (Mov_Nota_Fiscal_Entrada_Item)*       

  **ID_Destinacao**             *referência (Cad_Destinacao)*         ---

  **Quantidade**                *número, opcional*                    Mesmo critério de
                                                                      Mov_Pedido_Item_Destinacao (seção 2):
                                                                      preenchido quando o item é produto.

  **Fator**                     *número, opcional*                    Idem: preenchido quando o item é
                                                                      serviço.

  **ID_Conta_Contabil**         *referência (Cad_Conta_Contabil,      Por padrão a conta vem de
                                opcional)*                            Cad_Destinacao.ID_Conta_Contabil;
                                                                      preenchido aqui, o usuário sobrescreveu
                                                                      pontualmente a conta padrão daquela
                                                                      destinação para esta nota.

  **ID_Habilitacao**            *referência                           Adicionado na revisão 17 (Bloco 2).
                                (Cad_Habilitacao_Regime_Especial,     Idem, para a nota sem pedido. Com
                                opcional)*                            pedido, herda da destinação do pedido.

  **ID_Situacao_Suspensao**     *referência (Cad_Classe_Sistema,      Adicionado na revisão 17 (Bloco 2).
                                domínio =                             Idem, para a nota sem pedido.
                                situacao_suspensao_regime_especial,   
                                opcional)*                            

  **Data_Conversao**            *data, opcional*                      Adicionado na revisão 17 (Bloco 2).
                                                                      Idem.
  ----------------------------- ------------------------------------- ----------------------------------------

Campos fiscais do documento, local da operação e habilitação em regime
especial (revisão 17)

Hoje a mesma entidade recebe NF-e, CT-e de frete e NFS-e sem distinguir
o modelo, e a situação se resume a lançada, recusada e cancelada. Os
campos abaixo entram dos dois lados, simetricamente (o padrão já adotado
entre Compras e CRM & Vendas). O Status que existe hoje continua sendo o
andamento interno da nota; a Situacao_Documento é a situação fiscal.

Por decisão de Alberto, o pedido pergunta onde o serviço vai ser
prestado ou o material entregue, linha a linha. O exemplo dele: uma
empresa de Sorocaba contrata uma empresa de Suzano para fazer uma obra
em Andradas; a nota indica o comprador (Sorocaba) e o local da prestação
(Andradas). O contratante da compra é o estabelecimento do CNPJ do
pedido (ID_Filial), que pode ser a matriz ou uma filial, cada uma com o
seu endereço. Se o local não é o do contratante, o usuário escolhe um
local já cadastrado (Cad_Local_Operacao, Fase 0) ou cadastra na hora; se
o local é uma obra, o código da obra e o CIB são obrigatórios. A regra
do art. 11 da LC 214 aplicada é resolvida pelo Motor de Regras, e o
município de incidência do IBS e do ISS fica gravado na nota. O
empreendimento imobiliário (Cad_Empreendimento_Imobiliario,
Contabilidade & Fiscal) é opcional no item do pedido e da nota, para a
apuração por empreendimento e para negar o crédito onde o regime
especial o veda.

REIDI e REPES não são atributo do comprador nem do fornecedor:
acompanham a destinação, isto é, onde o produto ou serviço vai ser
aplicado, e essa destinação é decidida no pedido, linha a linha. Por
isso a habilitação (Cad_Habilitacao_Regime_Especial, Fase 0) fica na
linha de destinação do pedido e da nota sem pedido, escolhida pelo
usuário entre as habilitações vigentes do comprador, e o Motor de Regras
valida e sugere a suspensão. Cad_Destinacao não muda. A linha guarda
também a situação da suspensão até a conversão em alíquota zero.

7\. Inspeção de Qualidade na Entrada

Independente da conferência quantitativa (que depende do módulo de
Estoque, fora de escopo aqui --- ver seção 1), a inspeção de QUALIDADE
já entra neste módulo, porque ela pode condicionar o próprio
encerramento do pedido de compra. Se a empresa optar por exigir inspeção
para um produto/serviço, o pedido (ou a linha) só pode ser dado como
concluído depois do aval da qualidade.

Mov_Pedido_Item_Inspecao

O registro de uma inspeção de qualidade sobre uma linha de pedido
recebida.

*Vigência: não.*

  ------------------------------ --------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**       **Descrição / regra**

  **ID_Inspecao**                *identificador*       ---

  **ID_Item**                    *referência           ---
                                 (Mov_Pedido_Item)*    

  **Data_Inspecao**              *data*                ---

  **ID_Participante_Inspetor**   *referência           Quem inspecionou --- mesmo cadastro
                                 (Cad_Participante)*   único do Fase 0 (um colaborador, por
                                                       exemplo).

  **Resultado**                  *enumeração           ---
                                 {aprovado,            
                                 reprovado}*           

  **Observacao**                 *texto, opcional*     ---
  ------------------------------ --------------------- ----------------------------------------

A exigência de inspeção usa o mesmo padrão de herança-com-sobreposição
já usado para CST_IBS_CBS_Sugerido (Fase 0):
Cad_Produto_Servico_Dimensao_Valor.Requer_Inspecao dá o padrão por
família (ou outra dimensão de agrupamento), e
Cad_Produto_Servico.Requer_Inspecao, quando preenchido, sobrescreve
explicitamente o herdado para aquele produto/serviço específico ---
ambos incorporados no Fase 0, revisão 9. Uma linha de Mov_Pedido_Item só
conta como efetivamente recebida quando (a) o item não requer inspeção,
ou (b) requer e tem um Mov_Pedido_Item_Inspecao com Resultado=aprovado.

*Registro fotográfico/documental, adicionado na revisão 10: por simetria
com a mesma necessidade identificada na inspeção de saída do módulo de
Expedição --- comprovar a condição do produto no momento da inspeção,
útil sobretudo numa reprovação. Nenhuma entidade nova aqui ---
reaproveita o GED já existente na Fase 0
(Cad_Documento_Classe/Cad_Documento/Cad_Documento_Vinculo, seção 11
daquele documento, revisão 26), com a mesma Cad_Documento_Classe
(\"Registro Fotográfico de Inspeção\") usada em Expedição, e um
Cad_Documento_Vinculo apontando
Entidade_Relacionada_Tipo=mov_pedido_item_inspecao/ID_Entidade_Relacionada=ID_Inspecao.*

*Comportamento de aplicação, adicionado nesta revisão (11), por simetria
com a mesma necessidade em Expedição: um Resultado=reprovado dispara
automaticamente um Mov_Estoque_Condicao (Fase 1 --- Estoque, seção 11)
com Condicao=rejeitado, Origem_Tipo=mov_pedido_item_inspecao --- a
resolução (reparar, voltando a disponível, ou descartar, segregando o
saldo para destruição ou venda como defeituoso) acontece ali, não aqui,
mesmo motor transversal usado por Expedição.*

8\. Devolução e Recusa de Recebimento

Dois eventos distintos, que não devem ser confundidos: a nota pode ser
RECUSADA antes de ser efetivamente aceita --- nunca chega a virar um
recebimento de fato --- ou pode ser aceita e, só depois, gerar uma
DEVOLUÇÃO, total ou parcial, da mercadoria.

Recusa de recebimento

Quando a nota chega com alguma divergência (produto incoerente com o
pedido, quantidade muito fora do combinado, avaria) e não é aceita, isso
não gera nenhuma nota fiscal de devolução --- a mercadoria nunca entrou.
O registro é o próprio Mov_Nota_Fiscal_Entrada com Status=recusada e
Motivo_Recusa preenchido (seção 6): não baixa compromisso, não gera
estoque, mas fica disponível para consulta e para avaliar prazo/atraso
do fornecedor (comparando com Mov_Pedido_Item.Data_Entrega_Prevista,
seção 2).

A recusa abre dois caminhos: o fornecedor pode substituir o produto e
renegociar o prazo dentro do MESMO pedido --- o pedido continua aberto,
ID_Produto_Servico e Data_Entrega_Prevista do item são atualizados
(seção 2), e agora (revisão 8) o histórico dessa renegociação fica
registrado, ver Mov_Pedido_Item_Renegociacao abaixo; ou o pedido pode
ser cancelado (Status=cancelado), e aí um novo pedido --- normalmente
para outro fornecedor --- é criado referenciando o original via
ID_Pedido_Origem (seção 2), preservando a rastreabilidade de toda a
cadeia.

Mov_Pedido_Item_Renegociacao

Adicionado nesta revisão (8), pedido pela consolidação: registra o
EVENTO de renegociação de uma linha de pedido depois de uma recusa --- o
valor anterior de produto/prazo, o novo valor, quem decidiu e quando.
Fecha o ponto que ficava nas Notas desde a revisão 1 (\"assumi que é uma
edição direta em Mov_Pedido_Item, sem guardar histórico do que era
antes\"). É movimentação --- o log de um evento --- não substitui a
edição direta do item (Mov_Pedido_Item continua guardando só o valor
CORRENTE, este registro guarda o histórico de como ele chegou lá).

*Vigência: não --- é, ele próprio, um registro histórico imutável; uma
nova renegociação da mesma linha gera um novo registro, não edita este.*

  ------------------------------------ ------------------------ -------------------------------------------------
  **Campo**                            **Tipo lógico**          **Descrição / regra**

  **ID_Renegociacao**                  *identificador*          ---

  **ID_Item**                          *referência              A linha do pedido renegociada.
                                       (Mov_Pedido_Item)*       

  **ID_Produto_Servico_Anterior**      *referência              Preenchido quando a renegociação trocou o
                                       (Cad_Produto_Servico),   produto/serviço; vazio quando só o prazo mudou.
                                       opcional*                Desmembrado na revisão 15.

  **ID_Produto_Servico_Novo**          *referência              ---
                                       (Cad_Produto_Servico),   
                                       opcional*                

  **Data_Entrega_Prevista_Anterior**   *data, opcional*         Preenchido quando a renegociação mudou o prazo;
                                                                vazio quando só o produto/serviço mudou.
                                                                Desmembrado na revisão 15.

  **Data_Entrega_Prevista_Nova**       *data, opcional*         ---

  **ID_Usuario_Responsavel**           *referência              Quem decidiu/registrou esta renegociação ---
                                       (Cad_Participante)*      mesmo princípio de auditoria de
                                                                Mov_Nota_Fiscal_Entrada.ID_Usuario_Responsavel,
                                                                acima.

  **Data_Renegociacao**                *data*                   ---
  ------------------------------------ ------------------------ -------------------------------------------------

Devolução de compra

Sempre parte de uma nota já aceita (Status=lancada) --- cobre devolução
total ou parcial, dependendo de quais itens/quantidades aparecem em
Mov_Devolucao_Compra_Item.

Mov_Devolucao_Compra

O cabeçalho de uma devolução.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Devolucao** | *identificador* | --- |
| **ID_Nota** | *referência (Mov_Nota_Fiscal_Entrada)* | A nota de entrada original --- precisa ter Status=lancada. |
| **Data_Devolucao** | *data* | --- |
| **ID_Motivo** | *referência (Cad_Classe_Sistema, domínio motivo_devolucao)* | Adicionado nesta revisão (6): o motivo deixou de ser texto livre --- Alberto pediu normatização, mesmo cadastro genérico de domínio já usado em outros pontos do Fase 0. |
| **Motivo_Complemento** | *texto, opcional* | Complemento digitável, para detalhar o caso específico além do motivo normatizado. |
| **Numero_Nota_Devolucao** | *código (até 15), opcional* | A nota fiscal de devolução que a própria empresa emite de volta ao fornecedor --- documento fiscal de saída, fora do escopo deste dicionário além desta referência. Desmembrado na revisão 15. |
| **Serie_Nota_Devolucao** | *código (até 3), opcional* | --- |
| **Chave_Acesso_Devolucao** | *código (44), opcional* | Adicionado nesta revisão: a nota de devolução é ela mesma uma NFe própria, também precisa da chave de acesso. |
| **ID_Cbs_Ajuste_Operacao** | *referência (Mov_Cbs_Ajuste_Operacao), opcional* | Revisão 31 (documento 157, seção 4.6, Q157-2; D-N466 e D-N469): A devolução física liga ao ajuste fiscal. O documento de devolução pode vir do cliente (nota de entrada) ou ser emitido por nós; quem emite está em Mov_Cbs_Ajuste_Operacao.Papel_Emitente_Documento. |

*Revisão 31 --- campos novos: ID_Cbs_Ajuste_Operacao.*

Mov_Devolucao_Compra_Item

Uma linha devolvida --- nunca maior que a quantidade/valor originais da
nota.

*Vigência: não.*

  -------------------------- --------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                   **Descrição / regra**

  **ID_Item**                *identificador*                   ---

  **ID_Devolucao**           *referência                       ---
                             (Mov_Devolucao_Compra)*           

  **ID_Nota_Item**           *referência                       ---
                             (Mov_Nota_Fiscal_Entrada_Item)*   

  **Quantidade_Devolvida**   *número*                          Pode ser menor que a Quantidade do item
                                                               na nota original --- é isso que permite
                                                               devolução parcial.

  **Valor_Devolvido**        *número*                          O valor tal como emitido na nota fiscal
                                                               de devolução --- nunca recalculado a
                                                               partir de Quantidade_Devolvida (mesmo
                                                               princípio de fidelidade à nota, seção
                                                               6).
  -------------------------- --------------------------------- ----------------------------------------

9\. Como este módulo se conecta com a Fase 0 e com Planejamento &
Orçamento

Referência rápida do que este módulo consome --- nunca redescrito aqui,
só referenciado por chave estrangeira.

  ----------------------------------- -------------------------------------- ------------------------------------------
  **Entidade referenciada**           **Como este módulo usa**               **Observação**

  **Cad_Participante**                O fornecedor do pedido, da nota fiscal *Mesmo cadastro único do Fase 0*
                                      de entrada e do contrato; também o     
                                      inspetor.                              

  **Cad_Pre_Cadastro /                Proponente de cotação ainda não        *Mesmo mecanismo já usado do lado de
  Mov_Pre_Cadastro_Conversao**        efetivado como fornecedor; convertido  vendas/RH*
                                      só se vencedor de ao menos um item.    

  **Cad_Filial**                      Quem compra (pedido, contrato) e quem  *---*
                                      recebe (nota fiscal).                  

  **Cad_Produto_Servico**             O item comprado ou contratado ---      *Requer_Inspecao (revisão 9) gate o
                                      produto ou serviço, pontual ou         encerramento do pedido*
                                      contínuo.                              

  **Cad_CFOP**                        O CFOP de origem (nota do fornecedor)  *Novo cadastro, Fase 0 revisão 9*
                                      e de entrada (efetivo) de cada item.   

  **Cad_Destinacao**                  A destinação contábil/fiscal de cada   *Via Mov_Pedido_Item_Destinacao ou
                                      linha do pedido ou da nota --- pode    Mov_Nota_Fiscal_Entrada_Item_Destinacao,
                                      ratear entre mais de uma.              com Quantidade ou Fator*

  **Cad_Conta_Contabil**              A conta contábil de cada destinação.   *Padrão em
                                                                             Cad_Destinacao.ID_Conta_Contabil;
                                                                             sobrescrevível na nota sem pedido*

  **Cad_Regua_Aprovacao (+            Aprova o pedido --- gatilho            *Incorporado no Fase 0, revisão 9*
  Mov_Aprovacao_Instancia)**          Origem_Tipo=pedido_compra.             

  **Cad_Orcamento_Item /              O pedido aprovado gera o compromisso   *Fecha o vínculo deixado em aberto no
  Mov_Compromisso_Orcamentario**      orçamentário                           módulo de Planejamento & Orçamento*
                                      (Origem_Tipo=pedido_item); a nota      
                                      fiscal o baixa.                        

  **Cad_Gestao_Contrato (Fase 6 ---   O contrato de fornecimento contínuo    *Fase 6 --- Gestão de Contratos, revisão 3
  Gestão de Contratos)**              (posição Contratante) --- casado em    (construída em paralelo)*
                                      Mov_Nota_Fiscal_Entrada.ID_Contrato;   
                                      compromisso orçamentário via           
                                      Origem_Tipo=contrato_aquisicao.        

  **Cad_Motor_Regra (+ Cad_Cst,       Decide o CST/cClassTrib de entrada     *Regra confirmada por Alberto na Fase 0,
  Cad_Cclasstrib --- Fase 2)**        (critérios fornecedor +                revisão 24*
                                      produto_servico + cfop) e sugere o     
                                      CFOP de entrada.                       

  **Cad_Condicao_Pagamento (+         Sugestão de parcelamento do pedido --- *Fase 0, revisão 13 --- mesmo cadastro
  Cad_Condicao_Pagamento_Parcela)**   pré-popula Mov_Pedido_Parcela, cujos   usado pelo CRM & Vendas*
                                      valores/datas reais são sempre         
                                      explícitos.                            

  **Cad_Classe_Sistema (domínio       Normatiza o motivo de                  *Fase 0 --- mesmo domínio genérico usado
  motivo_devolucao)**                 Mov_Devolucao_Compra.ID_Motivo.        pelo CRM & Vendas*

  **Cad_Documento /                   O registro fotográfico/documental da   *Fase 0, revisão 26*
  Cad_Documento_Vinculo (GED, Fase    inspeção de entrada, amarrado a        
  0)**                                Mov_Pedido_Item_Inspecao via vínculo   
                                      genérico (seção 7).                    

  **Mov_Estoque_Condicao (Estoque)**  Adicionado nesta revisão (11): uma     *Fase 1 --- Estoque, revisão 9, novo
                                      reprovação na inspeção de entrada      transversal*
                                      (seção 7) dispara Condicao=rejeitado,  
                                      Origem_Tipo=mov_pedido_item_inspecao   
                                      --- mesmo motor transversal usado por  
                                      Expedição.                             
  ----------------------------------- -------------------------------------- ------------------------------------------

10\. Notas para a sua revisão

Mesma lógica dos documentos anteriores: estas são decisões técnicas que
assumi por conta própria para fechar uma estrutura concreta --- nenhuma
está travada.

-   Requisição de compra interna (aprovação de necessidade antes de
    cotar ou comprar) não foi modelada --- se a Mlegate ou seus clientes
    usam esse fluxo como uma etapa formal e separada, é um comentário
    natural para a próxima rodada.

-   Mov_Pedido_Item_Destinacao (e o equivalente na nota fiscal) usa
    Quantidade para produto e Fator para serviço, em vez de um
    Percentual único --- decisão deliberada, para não gerar rateio
    fisicamente sem sentido num produto (unidade quebrada) nem
    arredondamento forçado a pontos percentuais inteiros num serviço.

-   A conferência FÍSICA da mercadoria (contagem, endereçamento no
    depósito) continua dependendo do módulo de Estoque. Já a conferência
    fiscal/financeira --- quantidade/valor da nota vs. pedido, acumulado
    entre várias notas --- é função deste módulo (seção 6); a inspeção
    de QUALIDADE (seção 7) também já está modelada aqui, independente do
    Estoque. Nesta revisão, o módulo de Estoque passou a poder amarrar o
    recebimento físico direto em Mov_Nota_Fiscal_Entrada_Item, para o
    caso de nota sem pedido --- sem mudança estrutural aqui, já que
    ID_Pedido_Item em Mov_Nota_Fiscal_Entrada_Item já era opcional desde
    revisões anteriores.

-   Mov_Nota_Fiscal_Entrada permite ID_Pedido/ID_Pedido_Item/ID_Contrato
    vazios, para cobrir compras sem pedido formal (pequenas despesas,
    cartão corporativo) --- mas isso significa que nem toda nota fiscal
    de entrada baixa um compromisso orçamentário; só as que casam com um
    pedido (ou contrato) que tinha vínculo orçamentário.

-   Prazo/atraso do fornecedor: Data_Entrega_Prevista (Mov_Pedido_Item)
    e o histórico de recusas/devoluções dão a base de dados para medir
    isso, mas nenhum indicador ou relatório de desempenho de fornecedor
    foi modelado ainda --- fica para quando fizer sentido, talvez num
    módulo de BI/relatórios ou um painel dentro do próprio Compras.

-   Mov_Nota_Fiscal_Entrada_Item ganhou Valor_Credito_Tributario nesta
    revisão --- motivado pelo módulo de Estoque, que precisa saber o
    valor do crédito de imposto de uma nota de bonificação separadamente
    do Valor_Total (sem cobrança) do item.

-   Revisão 6 --- pedida pela consolidação do módulo Fase 1 CRM &
    Vendas, para manter simetria entre os dois módulos de ponta (compra
    e venda): Chave_Acesso em Mov_Nota_Fiscal_Entrada; snapshot de
    NCM/Unidade_Medida/NBS/Codigo_Servico_Municipal/Descricao_Produto_Servico
    em Mov_Nota_Fiscal_Entrada_Item, com o mesmo princípio de fidelidade
    ao valor real já usado para o Valor_Total;
    Mov_Devolucao_Compra.Motivo normatizado como ID_Motivo
    (Cad_Classe_Sistema, domínio motivo_devolucao) + Motivo_Complemento
    digitável; Chave_Acesso_Devolucao na nota de devolução; e
    Mov_Pedido.ID_Condicao_Pagamento (sugestão) + nova
    Mov_Pedido_Parcela (valor real por transação), espelhando exatamente
    o par equivalente do CRM & Vendas.

-   Revisão 7 --- pedida pela consolidação da Fase 2 Contabilidade &
    Fiscal: Mov_Nota_Fiscal_Entrada_Item.ID_CST_IBS_CBS/ID_ClassTrib
    foram renomeados para ID_Cst/ID_Cclasstrib e redirecionados para o
    novo pré-cadastro próprio daquele módulo (Cad_Cst/Cad_Cclasstrib,
    seção 6), substituindo o domínio cst_ibs_cbs e a Cad_ClassTrib do
    Fase 0, ambos aposentados; e Numero_Processo_Suframa foi adicionado
    para o item de entrada de estabelecimento na Zona Franca de
    Manaus/Área de Livre Comércio.

-   Revisão 8 (ciclo \"consolidar\") fechou o ponto que ficava aberto
    desde a revisão 1 sobre renegociação pós-recusa sem histórico: nova
    Mov_Pedido_Item_Renegociacao (seção 8), com ID_Usuario_Responsavel;
    Mov_Nota_Fiscal_Entrada também ganhou ID_Usuario_Responsavel (seção
    6), ao lado de Motivo_Recusa. A regra concreta do Motor de Regras
    para CST/cClassTrib de entrada (fornecedor + produto_servico + cfop)
    foi confirmada pela Fase 0 revisão 24 e refletida na descrição de
    ID_Cst/ID_Cclasstrib (seção 6) e na tabela de conexões (seção 9).

-   Revisão 9 --- patch pedido pela especificação do módulo Fase 1
    Expedição: Mov_Nota_Fiscal_Entrada_Item ganhou
    ID_Participante_Cliente_Atendido (seção 6), preenchido só quando o
    item é uma despesa de frete/CT-e atribuível a um cliente específico
    --- confirma a decisão de que \"frete é tratado como uma compra
    normal, nunca um módulo à parte\": o CT-e continua entrando por este
    mesmo Mov_Nota_Fiscal_Entrada, sem nenhuma entidade fiscal nova;
    Expedição só amarra QUAL embarque aquela nota cobre (ver aquele
    módulo, seção 4). Não modelei nenhuma trava que exija este campo
    preenchido quando a nota é de fato de frete (ex.: por NCM/NBS de
    serviço de transporte) --- fica a critério de quem lança.

-   Revisão 10 --- patch pedido pela consolidação do módulo Fase 1
    Expedição: a inspeção de qualidade na entrada (seção 7) ganhou
    registro fotográfico/documental, por simetria com a mesma
    necessidade na inspeção de saída daquele módulo --- reaproveita o
    GED já existente na Fase 0 (seção 11), sem nenhuma entidade nova
    aqui.

-   Revisão 11 --- patch pedido pela consolidação do módulo Fase 1
    Expedição, mesma simetria da revisão anterior: um
    Resultado=reprovado na inspeção de entrada (seção 7) passa a
    disparar Mov_Estoque_Condicao (Fase 1 --- Estoque, seção 11 daquele
    documento, revisão 9) --- a classificação (rejeitado) e a resolução
    (reparar/descartar) vivem inteiramente lá, transversal a Expedição,
    Compras e Produção; nenhuma entidade nova aqui.

-   Revisão 12: Cad_Contrato_Fornecimento e
    Cad_Contrato_Fornecimento_Valor (seção 4) foram aposentados ---
    duplicavam o conceito de contrato já coberto, de forma mais
    completa, pelo módulo Fase 6 Gestão de Contratos (cadastro único
    cliente/fornecedor). Mov_Nota_Fiscal_Entrada.ID_Contrato (seção 6) e
    a aprovação/compromisso orçamentário do contrato (seção 5) foram
    redirecionados para lá.

-   Revisão 13: Compras passou a consumir o mecanismo transversal de
    fechamento de período da Fase 0
    (Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial,
    seção 10 daquele documento, revisão 37) --- bloco \"compras\"
    travando Mov_Pedido (seção 2) e Mov_Nota_Fiscal_Entrada (seção 6)
    por Filial+competência, nenhum campo novo em nenhuma das duas
    entidades, só o comportamento de aplicação descrito junto de cada
    uma. Decisão de Alberto: fechar compras trava tudo datado na
    competência --- nem entra, nem altera --- porque o próprio pedido já
    gera compromisso orçamentário desde a criação (diferente de Vendas,
    onde cotação/pedido não compromete nada até o atendimento). Compras
    também ganhou, nesta revisão, o único ponto de validação de
    pendência do dicionário: o fechamento em si verifica se há nota
    fiscal de entrada com inspeção de qualidade ainda pendente (seção 7)
    na competência+filial antes de permitir fechar --- nenhum outro
    módulo tem essa checagem.

-   Revisão 14 --- duas referências cruzadas fechadas, pedidas pela
    consolidação de Contas a Pagar/Receber (hoje construído):
    Mov_Pedido_Parcela (seção 2) não aponta mais para uma \"Fase
    futura\" --- a liquidação real acontece em Contas a Pagar/Receber,
    seção 2; e uma nova nota (seção 6) esclarece que o valor de fato
    pago numa nota de entrada pode ser menor que Valor_Total, por
    retenção na fonte ou split payment do IBS/CBS na baixa (Contas a
    Pagar/Receber, seções 3 e 11). Nenhuma estrutura nova neste
    documento.

-   Revisão 15 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): campos compostos desmembrados na nota
    fiscal de entrada (número e série; datas de emissão e de entrada),
    no item de pedido (período do serviço), na renegociação e na
    devolução; chaves primárias das destinações e do item de proposta de
    cotação; chave de acesso de 44 caracteres (CNPJ alfanumérico). A
    convenção completa (vigência, identidade + versão, sucessão de
    códigos oficiais, competência, CNPJ alfanumérico, um campo por
    informação, saldos guardados de período fechado, sequência de
    fechamento) vive na Fase 0, seções 2 e 10 (revisão 41).

-   Revisão 16 --- tipo lógico \"código (n)\" definido por Alberto ---
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

-   Revisão 17 --- campos fiscais do cabeçalho e do item da nota de
    entrada (modelo e situação do documento, finalidade, natureza da
    operação, consumidor final, indicador de presença, protocolo de
    autorização, modalidade de frete, rateio de desconto, frete, seguro
    e outras despesas por item, origem da mercadoria, CEST, Ex da TIPI,
    GTIN, cBenef e cTribNac), local da operação por linha do pedido e da
    nota (local no contratante, endereço, Cad_Local_Operacao, critério
    do local, município de incidência do IBS e do ISS), habilitação
    REIDI/REPES e situação da suspensão nas linhas de destinação, e o
    empreendimento imobiliário no item do pedido e da nota. Desenho
    completo no documento Validação do Bloco 2 (documentos/18).

-   Revisão 18 --- referência a Cad_Regua_Aprovador_Escopo trocada por
    Cad_Usuario_Escopo (Fase 0, seção 13), que a substitui.

11\. Próximo passo

Compras, Estoque e CRM & Vendas (este último construído fora da ordem
original, por decisão do Alberto --- ver Fase 0) já estão com uma
primeira modelagem completa. Na época desta Revisão 6, o próximo passo
natural da Fase 1 era Contas a Pagar / Contas a Receber --- que
consumiria, entre outras coisas, a provisão contábil de comissão/royalty
(Mov_Lote_Lancamento.Origem_Tipo=provisao_comissao_venda, Fase 0) e as
parcelas reais já modeladas aqui e no CRM & Vendas (Mov_Pedido_Parcela /
Mov_Pedido_Venda_Parcela); aquele módulo já foi construído desde então
(Fase 2), consumindo exatamente isso.

Revisão 13, registrada aqui: Compras foi o primeiro módulo de Fase 1 a
adotar o mecanismo transversal de fechamento de período (Fase 0, seção
10) e o único, até agora, com validação de pendência no próprio
fechamento (nota fiscal de entrada com inspeção de qualidade pendente,
seção 7). Os demais módulos de Fase 1/2/5/6 já entregues (Estoque, CRM &
Vendas, Planejamento & Orçamento, Expedição, Produção, Contas a
Pagar/Receber, Tesouraria, Contabilidade & Fiscal, Folha & RH, Gestão de
Contratos) ainda precisam da mesma revisão pontual --- cada um
descrevendo, no próprio texto, o que especificamente o fechamento do seu
bloco trava, no mesmo padrão adotado aqui.

*Revisão 14, registrada aqui: patch pontual da mesma consolidação que
entregou Contas a Pagar/Receber --- Mov_Pedido_Parcela (seção 2) parou
de apontar para uma \"Fase futura\" e uma nova nota (seção 6) fecha a
referência cruzada de valor da nota vs. valor do título por
retenção/split payment, nenhuma estrutura nova neste documento.*

*Revisão 15 --- Bloco 1 da validação geral consolidado junto com a Fase
0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal)
e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 16 --- tipo lógico \"código\" aplicado junto com a revisão 42
da Fase 0. Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 17 --- Bloco 2 (fiscal) da validação geral consolidado junto
com a Fase 0 (revisão 43). Próximo passo combinado com Alberto: Bloco 3
(folha e jurídico), com desenho próprio para aprovação antes de
consolidar.*



12\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este documento não ganha entidades novas; as alterações em entidades existentes aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3").
