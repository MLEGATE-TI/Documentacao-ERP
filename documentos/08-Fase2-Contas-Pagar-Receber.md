**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 2 · MÓDULO 5**

**Contas a Pagar/Receber**

*Título único (pagar/receber pelo mesmo motor), baixa com saldo em
banco/caixa/aplicação, crédito de cliente/fornecedor (adiantamento,
bonificação e outras origens, com prazo de validade), encontro de
contas, limite de crédito consolidado, reprogramação de título, eventos
de conta financeira (rendimento, perda e tarifas) e empréstimos
bancários*

*Revisão 31 --- consolidação da revisão 40 do dicionário (documentos 204, 206 e 209 e B1 do documento 205, com as respostas de Alberto de 11/11/2026): 1 entidades existentes alteradas; valores novos aporte_mover e recolhimento_mover em Mov_Titulo.Origem_Tipo (documento 206).*

*Revisão 30 --- consolidação da revisão 39 do dicionário (documento 202 e ajuste A1 do documento 205, com as respostas de Alberto de 10/11/2026): 1 entidades existentes alteradas; valor novo devolucao_credito_automotivo em Mov_Titulo.Origem_Tipo (documento 202).*

*Revisão 29 --- consolidação da revisão 38 do dicionário (documentos 200 e 201, com as respostas de Alberto de 10/11/2026): 2 entidades existentes alteradas; valor novo arrendamento_parcela em Mov_Titulo.Origem_Tipo e 3 campos novos em Mov_Emprestimo (documento 200).*

*Revisão 28 --- consolidação da revisão 34 do dicionário (documentos 158, 177, 183 e 184, com as respostas de Alberto de 09/11/2026): 1 entidades existentes alteradas; o vínculo da baixa com a transação de cartão (documento 177).*

*Revisão 27 --- consolidação da revisão 33 do dicionário (documentos 180 e 181, com a resposta de Alberto de 06/11/2026): 1 entidades existentes alteradas; o texto do desconto na baixa de título de guia de CSLL com bônus (documento 181).*

*Revisão 26 --- consolidação da revisão 32 do dicionário (documentos 172, 175 e 176, com as respostas de Alberto de 05/11/2026): 1 entidades existentes alteradas; a instituição de pagamento, o intermediador e a classe de incidência do 1601 na baixa de título (documento 176).*

*Revisão 25 --- consolidação da revisão 29 do dicionário (documentos 138, 140, 152, 153, 155, 162, 163 e 165, com as respostas de Alberto de 29/10/2026 e de 03/11/2026): 1 entidades existentes alteradas; os valores devolucao_nota_cancelada e devolucao_adiantamento na origem do título (documento 153, Q153-6 a Q153-8).*

*Revisão 24 --- consolidação da revisão 28 do dicionário (documentos 127, 152 e 153, com as respostas de Alberto de 29/10/2026): 2 entidades existentes alteradas; texto da aplicação do adiantamento (IBS e CBS no recebimento, PIS e Cofins na emissão da nota, nota que conta; documentos 152 e 153) e da natureza cambial herdada pelo título de royalty.*

*Revisão 23 --- consolidação da revisão 27 do dicionário (documentos 146, 147, 148 e 149, com as respostas de Alberto de 29/10/2026): 2 entidades existentes alteradas; valores guia_tef (origem do título) e estorno_tef (origem da baixa) do TEF da SAF (documentos 147 e 149).*

*Revisão 22 --- consolidação da revisão 26 do dicionário (documentos 116, 134, 135, 142, 143 e 144, com as respostas de Alberto de 28/10/2026): 1 entidades existentes alteradas; três valores novos de origem do título (duimp_tributo, duimp_icms e locacao_pagamento).*

*Revisão 21 --- consolidação da revisão 25 do dicionário (documentos 94, 99, 107, 116, 120, 123 a 129 e 132, com as respostas de Alberto de 26 e 27/10/2026): 2 entidades novas (anexo, seção 18); 4 entidades existentes alteradas; o de-para entre a forma e o tipo da baixa, a reavaliação do crédito em moeda estrangeira, a paridade entre moedas na aplicação do crédito e no encontro de contas, o encontro entre participantes diferentes e o texto do Y520 em reais (documentos 120 e 123).*

*Revisão 20 --- consolidação da revisão 24 do dicionário (documentos 93, 96, 118, 119, 120 e 121, com as respostas de Alberto de 22/10/2026 e de 26/10/2026): 4 entidades existentes alteradas; título, baixa e adiantamento em moeda estrangeira: moeda que prevalece sobre a parcela, taxa estimada e sua data, taxa da baixa, desconto e juros convertidos pela taxa da baixa, campo de arredondamento e adiantamento reavaliado todo mês (documentos 119, 120 e 121).*

*Revisão 19 --- consolidação da revisão 23 do dicionário (documentos 113 e 114, com as respostas de Alberto de 26/10/2026 (Q113-6 e Q114-1 a Q114-4)): 2 entidades existentes alteradas; o encontro de contas passa a ter lote compartilhado pelas duas baixas e pelo encontro, taxa única nas duas baixas (documento 114).*

*Revisão 18 --- consolidação da revisão 22 do dicionário (documentos 110, 111 e 112, com as respostas de Alberto de 26/10/2026): 2 entidades novas (anexo, seção 17); 3 entidades existentes alteradas; tipo da baixa (2 entidades novas), valor financeiro na baixa, encontro de contas lançado como baixas amarradas ao encontro e série e dia da taxa na reavaliação cambial (documentos 111 e 112).*

*Revisão 17 --- consolidação da revisão 21 do dicionário (documentos 100 a 106, com as respostas de Alberto de 22/10/2026): 1 entidades novas (anexo, seção 16); 4 entidades existentes alteradas; título, baixa e adiantamento em moeda estrangeira, natureza e forma na entrada do título e reavaliação do fim do mês (documentos 101 e 103).*

*Revisão 16 --- consolidação da revisão 11 do dicionário (documento 72, decisões D-N191 a D-N201, aprovadas por Alberto em 19/10/2026): ajuste de texto: a referência ao cronograma de transição aponta para o calendário. O dicionário passa de 890 para 888 entidades.*

*Revisão 15 --- consolidação da revisão 5 do dicionário (documento 50, D-N117, aprovada por Alberto em 13/10/2026): a matriz do limite de crédito passa a ser identificada por Cad_Participante.Indicador_Matriz, e não pelo sufixo 0001 do CNPJ (texto do limite de crédito e das decisões da revisão 7). Nenhuma entidade deste módulo mudou.*

*Revisão 14 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 1 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 13 --- Bloco 5 da validação geral (MIT, DCTFWeb e
recolhimento), construída junto com a revisão 47 da Fase 0, a revisão 18
de Folha & RH e a revisão 19 de Contabilidade & Fiscal: Mov_Titulo ganha
três valores de Origem_Tipo (esocial_retorno_cr, dctfweb_darf e
consolidacao_retencoes) e os campos ID_Titulo_Substituto e
ID_Titulo_Complementado; Mov_Titulo_Baixa ganha o valor
vinculacao_dctfweb; inss e irrf_retido deixam de ser gerados pela
folha.*

*Revisão 12 --- Bloco 3 da validação geral do dicionário (folha e
eSocial, jurídico), construída junto com a revisão 45 da Fase 0 e com o
novo módulo Fase 8 --- Jurídico: Mov_Titulo.Origem_Tipo ganha
processo_judicial, processo_trabalhista e distribuicao_lucro, para os
pagamentos que nascem de processo e de distribuição de lucros.*

*Revisão 11 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; a raiz do CNPJ passa a ser os 8 primeiros
caracteres (CNPJ alfanumérico, IN RFB 2.229/2024); saldo de título
continua derivado, confirmado por Alberto --- não faz sentido guardar.*

*Revisão 10 --- ciclo \"consolidar\": nova Reclassificação de Prazo
(seção 8) --- todo título transita de Longo para Curto Prazo pela
passagem do tempo, comparando Data_Vencimento contra
Cad_Empresa.Meses_Limite_Curto_Prazo (novo parâmetro por empresa, Fase 0
revisão 39), com varrimento no fechamento mensal do bloco \"tesouraria\"
e disparo imediato na reprogramação; fechada a referência cruzada
pendente de PIS/COFINS sobre rendimento financeiro (seção 9), que já
está coberta por Contabilidade & Fiscal; e fechada a referência cruzada
de valor do título vs. valor de face da nota (seção 3)*

*Revisão 9 --- mecanismo transversal de fechamento de período (Fase 0,
seção 10, revisão 37): Mov_Titulo e Mov_Titulo_Baixa (seções 2 e 3)
passam a respeitar um único bloco de fechamento,
Cad_Bloco_Fechamento.Codigo=\"tesouraria\" --- o mesmo bloco que trava a
execução do pagamento no documento de Fase 2 Tesouraria, ainda que as
duas entidades estejam fisicamente cadastradas aqui; confirmado por
Alberto (\"sim, extende sobre o conta a pagar e receber\"), não um bloco
\"contas_a_pagar_receber\" à parte. Sem validação de pendência no
fechamento --- exclusiva do bloco \"compras\" --- um título fica em
aberto por natureza até o vencimento/baixa, mesmo princípio universal já
usado nos demais blocos do dicionário*

*Revisão 8 --- ciclo \"consolidar\": Mov_Titulo ganha
Origem_Tipo=folha_pagamento e Natureza_Titulo_Folha (seção 2), pedido
por Alberto --- a liquidação de qualquer folha (Fase 5) passa a gerar
título a pagar de verdade para líquido do colaborador, INSS, FGTS, IRRF
retido, pensão alimentícia e consignado, não só lançamento contábil;
ID_Participante resolve automaticamente para o beneficiário do óbito
quando aplicável; a baixa segue para a remessa bancária real
(Tesouraria)*

*Revisão 7 --- ciclo \"consolidar\": propagação de Limite_Credito por
Propagar_Limite_Credito (Fase 0); aprovação de caixa em lote
(Mov_Aprovacao_Lote, Fase 0); Mov_Credito.Contabiliza_Na_Inclusao;
Mov_Emprestimo.ID_Conta_Contabil ampliado; Mov_Titulo_Baixa.Canal_Split;
reversão de comissão/royalty proporcional confirmada*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o módulo de Contas a Pagar/Receber, no mesmo
formato usado nos quatro módulos já entregues (Planejamento & Orçamento,
Compras, Estoque, CRM & Vendas): função e dados juntos, entidade por
entidade, sempre referenciando os motores transversais da Fase 0
(Cad_Participante, Cad_Grupo_Economico, Cad_Conta_Contabil,
Cad_Regua_Aprovacao, Mov_Lote_Lancamento/Mov_Lancamento) e os módulos já
especificados (Mov_Pedido_Parcela em Compras; Mov_Pedido_Venda_Parcela,
Mov_Pedido_Venda_Item_Comissao e
Mov_Pedido_Venda_Item.Percentual_Royalty_Estimado em CRM & Vendas) em
vez de redefini-los.

Nota de transparência sobre a ordem de especificação, por simetria com
os documentos anteriores: diferente de CRM & Vendas --- antecipado da
Fase 4 por decisão explícita de Alberto ---, este módulo está exatamente
onde o Documento Analítico original o posiciona: Fase 2, a camada
financeira que fecha o ciclo aberto por Compras (Fase 1) e CRM & Vendas
(antecipado). \"Vamos para os próximos passos\", a instrução que abriu a
Revisão 1, foi interpretada como a confirmação para seguir a ordem
original a partir daqui. Por continuidade de numeração com os quatro
documentos já entregues, este leva o rótulo \"Módulo 5\", mas agora
coincide também com a fase correta do plano geral.

O Documento Analítico descreve o módulo assim: \"É um único módulo, não
dois --- o mesmo motor, com direção diferente conforme o fluxo seja de
pagamento ou recebimento. Controla adiantamentos de clientes e
fornecedores, permite encontro de contas quando um fornecedor também é
cliente, e verifica saldo em bancos, caixa e aplicações no momento da
baixa.\" A Revisão 1 seguiu essa definição ao pé da letra: uma única
entidade de título (Mov_Titulo, seção 2) com um campo Tipo {pagar,
receber}, em vez de duas tabelas espelhadas --- mesma filosofia de
cadastro único já usada em todo o dicionário desde o Fase 0.

A Revisão 2 incorporou seis comentários de Alberto sobre a Revisão 1:
(1) o adiantamento passou a cobrir também CRÉDITO DE BONIFICAÇÃO
comercial (não só dinheiro adiantado), consolidável entre filiais do
mesmo fornecedor/cliente por CNPJ raiz (seção 4); (2) o limite de
crédito ganhou uma cascata de três níveis --- Grupo Econômico, depois
CNPJ raiz, depois individual (seção 6); (3) a liquidação parcial de um
título passou a poder reprogramar o saldo restante para um ou mais novos
títulos, de forma rastreável (seção 8); (4) rendimento de aplicação
financeira e taxa bancária passaram a ser registrados, numa única
entidade (seção 9); (5) ficou confirmado --- e reforçado no texto ---
que um único título pode ser liquidado por uma MISTURA de baixa,
adiantamento/bonificação e encontro de contas, cada mecanismo cobrindo
parte do saldo; e (6) Cad_Participante ganhou CNPJ_Raiz (Fase 0, revisão
17), calculado automaticamente pelo sistema, para sustentar os pontos 1
e 2.

Esta Revisão 3 incorpora mais cinco comentários de Alberto sobre a
Revisão 2: (1) a origem do crédito não-financeiro deixou de ser só
bonificação --- vira um domínio aberto (crédito tributário de tributos
pagos a maior compensados futuramente, entre outros), e a entidade foi
renomeada de Mov_Adiantamento para Mov_Credito, mais fiel ao que ela já
cobre (seção 4); (2) um crédito pode ter prazo de validade, tipo
cashback, depois do qual não pode mais ser aplicado mesmo com saldo
(seção 4); (3) Mov_Conta_Contabil_Evento ganhou uma classificação mais
rica --- perda em aplicação (resultado negativo de mercado, que não
cabia nem em rendimento nem em taxa) e taxa de administração passam a
ter espaço próprio, junto com rendimento e tarifa, todos num único
domínio aberto (seção 9); e (4)/(5) um novo módulo de EMPRÉSTIMOS
BANCÁRIOS --- hot money e financiamento de prazo mais longo ---, com
principal e juros separados por parcela para fins de apuração contábil,
reaproveitando o motor de título/baixa já existente para o pagamento
(seção 10).

A Revisão 4 incorporou mais um comentário de Alberto sobre a Revisão 3:
Mov_Emprestimo estava sem a taxa de juros do contrato e os demais dados
necessários para calcular as parcelas. O cabeçalho do empréstimo ganhou
Taxa_Juros, Periodicidade_Taxa, ID_Indexador, Sistema_Amortizacao e
Numero_Parcelas_Contratadas (seção 10) --- dados do CONTRATO, para
referência e auditoria, sem que este módulo passe a calcular parcela
nenhuma a partir deles: os valores reais de cada parcela
(Mov_Emprestimo_Parcela.Valor_Principal_Previsto/Valor_Juros_Previsto)
continuam sendo o dado fiel usado para gerar o título, mesma filosofia
de \"fidelidade ao valor real, nunca recalcular\" de todo o dicionário.

Esta Revisão 5 é um patch pontual, pedido pela consolidação (Revisão 3)
do módulo Fase 2 Tesouraria, já entregue: a baixa precisa ter referência
de origem --- se foi automática pelo retorno bancário, registrar a data
de recebimento do retorno E a data de baixa (que não são necessariamente
a mesma); se foi manual, identificar explicitamente que foi manual e
qual usuário fez. Mov_Titulo_Baixa ganha Origem_Tipo,
Data_Recebimento_Cnab e ID_Participante_Baixa (seção 3) --- nenhuma
outra seção deste documento muda nesta revisão.

Dependências declaradas no Documento Analítico: Cadastro único (Fase 0)
e Fiscal --- XML de entrada e saída (nota fiscal de entrada,
especificada em Compras; nota fiscal de saída, especificada em CRM &
Vendas). Este módulo alimenta, por sua vez, Tesouraria e BI --- nenhum
dos dois ainda especificado. Fica, portanto, como gancho explícito para
quando esses dois módulos forem detalhados: a movimentação bancária de
fato (extrato, conciliação, CNAB, saldo diário consolidado por conta,
cadastro físico de conta bancária) pertence à Tesouraria; este módulo só
reaproveita a estrutura que o Fase 0 já preparava para isso ---
Cad_Conta_Contabil.ID_Tipo_Conta já previa, desde antes da Revisão 1,
restringir a escolha de conta \"numa baixa financeira\" (ver seção 3).

Continua FORA do escopo, por decisão já registrada na Revisão 1: o
repasse financeiro efetivo de comissão/royalty a um beneficiário com
vínculo empregatício, que depende de Folha & RH (ainda não
especificado); e a apuração fiscal sobre a baixa (retenções na fonte,
IRRF/PIS/COFINS/CSLL sobre serviço) e o cálculo efetivo de PIS/COFINS
sobre rendimento financeiro (seção 9) --- ambos dependem de
Contabilidade & Fiscal, também ainda não especificado. O gatilho de
bloqueio de crédito propriamente dito dentro de CRM & Vendas, que ficava
como gancho desde a Revisão 1, foi integrado de fato num patch posterior
àquele documento (junto da consolidação, Revisão 3, do módulo Fase 2
Tesouraria) --- ver seção 6.

2\. Título --- Contas a Pagar e a Receber pelo Mesmo Motor

Um único cadastro de título, com Tipo decidindo a direção --- nunca duas
tabelas espelhadas. O título nasce vinculado ao evento fiscal que o
originou (nota fiscal de entrada ou de saída) e, quando esse evento
tiver um pedido de origem com parcelamento negociado, herda valor e
vencimento reais da parcela do pedido (Mov_Pedido_Parcela em Compras,
Mov_Pedido_Venda_Parcela em CRM & Vendas) --- nunca recalculados, mesma
fidelidade ao valor real usada em todo o dicionário. O nascimento do
título em si NÃO gera lançamento contábil novo: a receita ou despesa já
foi reconhecida pelo lançamento da própria nota fiscal
(Mov_Lote_Lancamento.Origem_Tipo=documento_fiscal, Fase 0) --- o título
é um registro de CONTROLE FINANCEIRO (quando e quanto cobrar ou pagar),
não um evento contábil por si só. Só a baixa (seção 3), a reversão de
provisão (seção 7) e a reprogramação (seção 8) geram lançamento novo.

Mov_Titulo

O título --- a pagar ou a receber, conforme Tipo. Fornecedor
(Tipo=pagar) ou cliente (Tipo=receber) são o mesmo cadastro único de
Cad_Participante; um participante pode ter títulos dos dois tipos ao
mesmo tempo (ex.: fornecedor que também é cliente --- ver Encontro de
Contas, seção 5), suportado pela mesma associação N:N de papéis já
existente (Cad_Participante_Classe, Fase 0).

*Vigência: não --- é o registro de um evento (o nascimento do título); a
liquidação é registrada à parte (seções 3, 4, 5 e 8), sem reescrever
este registro.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Titulo** | *identificador* | --- |
| **Tipo** | *enumeração {pagar, receber}* | A direção do título --- o mesmo motor, mudando só a direção, exatamente como descrito no Documento Analítico. |
| **ID_Filial** | *referência (Cad_Filial)* | A filial que emitiu (saída) ou recebeu (entrada) a nota fiscal de origem. |
| **ID_Participante** | *referência (Cad_Participante)* | O fornecedor (Tipo=pagar) ou o cliente (Tipo=receber) --- mesmo cadastro único do Fase 0. Quando Origem_Tipo=folha_pagamento (adicionado nesta revisão, 8): para Natureza_Titulo_Folha=liquido_colaborador, é o próprio colaborador (Cad_Vinculo_Emprego.ID_Participante, Fase 5) --- exceto quando o desligamento que originou a apuração foi por óbito, caso em que resolve automaticamente para Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito (Fase 5, seção 2), mesmo mecanismo único cobrindo tanto o pagamento normal quanto o caso de óbito, sem campo/regra duplicada aqui. Para as demais naturezas (inss, fgts, irrf_retido, pensao_alimenticia, consignado), é o credor do tributo/obrigação --- INSS, FGTS (Caixa Econômica Federal), Receita Federal, instituição consignatária ou o beneficiário da pensão --- cada um cadastrado como Cad_Participante, mesmo princípio \"cadastro único, papéis por contexto\" já usado em todo o dicionário: não há tabela própria de \"credor de tributo\". |
| **Origem_Tipo** | *enumeração {nota_fiscal_entrada, nota_fiscal_saida, comissao_venda, royalty_venda, reprogramacao, emprestimo, folha_pagamento, processo_judicial, processo_trabalhista, distribuicao_lucro, esocial_retorno_cr, dctfweb_darf, consolidacao_retencoes, avulso, outro, das_simples, das_mei, apuracao_estadual, locacao_repasse, guia_iss, nfts, darf_avulso, parcelamento_tributario, simples_maed, duimp_tributo, duimp_icms, locacao_pagamento, guia_tef, devolucao_nota_cancelada, devolucao_adiantamento, arrendamento_parcela, devolucao_credito_automotivo, aporte_mover, recolhimento_mover}* | Alterado na revisão 3 (documento 37). Acrescenta darf_avulso (ID_Origem aponta Mov_Darf_Avulso), parcelamento_tributario (Mov_Parcelamento_Tributario_Parcela) e simples_maed (Mov_Simples_Maed). Revisão 26 (documentos 142, 143 e 144): duimp_tributo (título de tributo da importação, um por tipo de tributo da Duimp, só quando o débito automático do PCCE está desligado e o despachante repassa; ID_Origem aponta Mov_Duimp_Tributo_Total), duimp_icms (título da guia ou do repasse do ICMS; ID_Origem aponta Mov_Pcce_Icms_Solicitacao) e locacao_pagamento (título a pagar do aluguel em que a empresa é locatária; ID_Origem aponta Mov_Locacao_Pagamento). Revisão 27 (documento 147, Q147-6): guia_tef é a guia mensal única do TEF da SAF, gerada ao confirmar Mov_Apuracao_Tef (ID_Origem aponta a apuração); o título nasce sem vencimento enquanto o ato conjunto da Receita e do Comitê Gestor não definir o prazo. Revisão 29 (documento 153, Q153-6, Q153-7 e Q153-8; D-N441 a D-N443): devolucao_nota_cancelada é o contas a pagar gerado automaticamente quando se cancela uma nota de venda com recebimento em banco ou caixa, pelo montante recebido em banco ou caixa (nunca pelo saldo do crédito; o que foi baixado contra adiantamento volta ao adiantamento, sem título); ID_Origem aponta Mov_Nota_Fiscal_Saida. devolucao_adiantamento é o contas a pagar gerado ao cancelar um adiantamento sem uso que o cliente quer de volta; ID_Origem aponta Mov_Credito, e o ajuste de IBS e CBS fica em Mov_Credito_Ajuste_Documento. Revisão 38 (documento 200, seção 5.3, Q200-5; D-N533 e D-N534): arrendamento_parcela é o título a pagar da parcela do arrendamento mercantil em que a empresa é arrendatária (ID_Origem aponta Mov_Arrendamento_Parcela), como a parcela do empréstimo. Revisão 39 (documento 202, seção 5.3, Q202-8; D-N541): devolucao_credito_automotivo é o título a pagar da devolução do crédito presumido automotivo quando a habilitação é cancelada (LC 214, art. 315; Decreto 12.955, art. 526; ID_Origem aponta Mov_Credito_Automotivo_Devolucao). Revisão 40 (documento 206, seção 5.6; D-N548): aporte_mover é o título a pagar dos aportes ao FNDIT; recolhimento_mover é o título a pagar do recolhimento pelo cancelamento da habilitação. |
| **ID_Origem** | *referência genérica* | Conforme Origem_Tipo: ID_Nota (Mov_Nota_Fiscal_Entrada/Saida); ID_Item_Comissao de Mov_Pedido_Venda_Item_Comissao quando comissao_venda; ID_Item de Mov_Pedido_Venda_Item quando royalty_venda; ID_Reprogramacao de Mov_Titulo_Reprogramacao (seção 8) quando reprogramacao; ID_Emprestimo de Mov_Emprestimo (seção 10) quando emprestimo; ID_Apuracao de Mov_Rh_Folha_Apuracao (Fase 5, seção 3) quando folha_pagamento --- um título por Natureza_Titulo_Folha dentro da mesma apuração, agregando os Mov_Rh_Folha_Item que compõem aquela natureza; vazio quando avulso. Revisão 13: Mov_Esocial_Retorno_Cr (Folha & RH, revisão 18) quando esocial_retorno_cr; Mov_Dctfweb_Darf quando dctfweb_darf; Mov_Retencao_Consolidacao quando consolidacao_retencoes (Contabilidade & Fiscal, revisão 19). |
| **ID_Parcela_Origem** | *referência genérica, opcional* | Presente quando a nota fiscal de origem tem um pedido parcelado por trás: Mov_Pedido_Parcela (Compras) quando Tipo=pagar, ou Mov_Pedido_Venda_Parcela (CRM & Vendas) quando Tipo=receber --- ou, adicionado na revisão 3, Mov_Emprestimo_Parcela (seção 10) quando Origem_Tipo=emprestimo. É daqui que Valor_Titulo e Data_Vencimento são copiados no nascimento --- fidelidade ao valor já negociado, nunca recalculado. Vazio quando Origem_Tipo não for um dos três casos que têm parcela de origem (nota_fiscal_entrada, nota_fiscal_saida, emprestimo) --- inclusive vazio para folha_pagamento, que não tem parcela de origem estruturada da mesma forma (ver Data_Vencimento, abaixo). |
| **Numero_Parcela** | *número, opcional* | A ordem desta parcela dentro do título gerado pela mesma nota (ou pelo mesmo empréstimo) --- copiado de Mov_Pedido_Parcela.Numero_Parcela / Mov_Pedido_Venda_Parcela.Numero_Parcela / Mov_Emprestimo_Parcela.Numero_Parcela quando ID_Parcela_Origem estiver preenchido; 1 (parcela única) quando não houver parcelamento, inclusive para folha_pagamento (cada Natureza_Titulo_Folha é seu próprio título, não uma parcela de outro). |
| **Natureza_Titulo_Folha** | *enumeração {liquido_colaborador, inss, fgts, irrf_retido, pensao_alimenticia, consignado, outro}, opcional* | Adicionado nesta revisão (8), preenchido só quando Origem_Tipo=folha_pagamento: qual obrigação, dentre as que uma folha liquidada gera, este título específico representa --- o líquido a pagar ao colaborador é só uma delas; INSS e FGTS vão para os respectivos órgãos, IRRF retido e pensão alimentícia/consignado vão para a Receita Federal/instituição consignatária/beneficiário da pensão, cada um seu próprio título, nunca somados num único valor. \"outro\" cobre uma obrigação de folha ainda não prevista nesta lista, sem exigir novo valor de domínio para cada caso raro. Revisão 13 (Bloco 5): inss e irrf_retido deixam de ser gerados pela liquidação da folha, que lança só a provisão contábil; os valores permanecem no domínio apenas para os dados migrados. |
| **Valor_Titulo** | *número* | O valor real deste título --- campo explícito, copiado da parcela do pedido, ou da soma Valor_Principal_Previsto + Valor_Juros_Previsto da parcela de empréstimo (seção 10), quando ID_Parcela_Origem estiver preenchido; senão, o Valor_Total da nota, um valor lançado manualmente (avulso, comissão, royalty), o Valor_Reprogramado da parcela reprogramada (seção 8), ou a soma dos Mov_Rh_Folha_Item (Fase 5) da apuração que correspondem a esta Natureza_Titulo_Folha, quando folha_pagamento. Nunca recalculado a partir de outro campo. Revisão 21 (D-N346, documento 101): nos títulos em moeda estrangeira, Valor_Titulo continua em reais e passa a ser o valor estimado (Valor_Titulo_Moeda vezes Taxa_Estimada, arredondado pelas casas da moeda funcional); é a coluna em reais para referência. O valor real do título é Valor_Titulo_Moeda, na moeda do título. Títulos em reais não mudam. Revisão 24 (D-N360, documento 119, Q101-1a, respondida por Alberto em 26/10/2026): quando o título tem moeda estrangeira, **vale a moeda**, em qualquer origem: Valor_Titulo_Moeda é digitado e Valor_Titulo é o valor estimado; a parcela do pedido ou do empréstimo, ou a nota, em reais, só emprestam o número e o vencimento. A frase acima, "nunca recalculado", vale para o título em reais. A tela avisa, sem bloquear, quando o valor estimado difere do valor em reais da origem. |
| **ID_Moeda_Titulo** | *referência (Cad_Moeda), opcional* | Revisão 21 (D-N346): A moeda em que o título deve ser pago ou recebido. **Vazio = moeda funcional da empresa**, como todos os títulos de hoje, que não mudam. Informada por quem lança o título. Revisão 24 (D-N360, Q101-1, respondida: sim): os quatro campos do título em moeda (ID_Moeda_Titulo, Valor_Titulo_Moeda, Taxa_Estimada e Data_Taxa_Estimada) estão confirmados; entram juntos ou ficam vazios. |
| **Valor_Titulo_Moeda** | *número, opcional* | Revisão 21 (D-N346): Quanto se deve **na moeda do título**. Obrigatório quando a moeda difere da funcional. É o valor **real** do título nesse caso. Revisão 24 (D-N360, Q101-1 e Q101-1a): confirmado; ver Valor_Titulo, que passa a ser o valor estimado. |
| **Taxa_Estimada** | *número, opcional* | Revisão 21 (D-N346): A taxa usada para estimar o valor em reais e para contabilizar o título no nascimento. Obrigatória quando a moeda difere da funcional. Sugerida da série de cotações na Data_Taxa_Estimada e **editável**. Revisão 24 (D-N360, Q101-1, Q101-1c e Q101-1d): confirmado. A taxa sugerida vem da série marcada para o par de moedas (Cad_Serie_Cotacao.Uso_Fechamento), na última cotação com data até a Data_Taxa_Estimada. É **editável até o primeiro movimento** do título (baixa, aplicação de crédito, encontro de contas ou reavaliação); depois disso a correção é cancelar o título e lançar outro, ou o contador ajusta por lançamento (regra da camada de integração, sem campo). O **título novo da renegociação nasce com a taxa herdada**: a taxa em que o saldo do título antigo estava contabilizado (a da última reavaliação, ou a Taxa_Estimada do título antigo). A precisão é de 8 casas decimais (numeric(15,8)). |
| **Data_Taxa_Estimada** | *data, opcional* | Revisão 21 (D-N346): O dia da taxa estimada (por padrão a Data_Emissao; Q101-1). Na renegociação, a data da taxa herdada do título antigo (Revisão 24, D-N360, Q101-1d; a revisão 21 dizia o dia da renegociação). Revisão 24 (D-N360, Q101-1b, respondida por Alberto em 26/10/2026): guarda o **dia da cotação usada**, e não o dia pedido (emissão em sábado, 31/10, com cotação de sexta, 30/10, guarda 30/10); quando a taxa é digitada à mão, guarda a data a que ela se refere (padrão: a emissão). Não há campo novo para a série: a taxa é editável e nem sempre há série por trás. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial), opcional* | Revisão 21 (D-N348): A natureza da operação, informada na entrada. **Obrigatória** (Q103-2) quando o participante é **não residente**. Tem de estar vigente na data da entrada; na baixa vale a vigente na data final da ECF. Revisão 28 (documento 127, Q127-5): no título royalty_venda a natureza vem herdada de Mov_Pedido_Venda_Item.ID_Natureza_Operacao_Cambial_Royalty; o financeiro pode trocá-la só com o motivo. |
| **Forma_Pagamento_Exterior_Prevista** | *enumeração {cambio, transferencia_reais, cartao, deposito_conta_exterior, recursos_mantidos_exterior, moeda_nacional_ou_estrangeira}, opcional* | Revisão 21 (D-N348): A forma que se espera usar. Serve só de ponto de partida para a baixa; a forma real fica na classificação da baixa. |
| **Referencia_Operacao** | *código (40), opcional* | Revisão 21 (D-N348): Número do contrato, da fatura ou do documento do exterior. Copiado para a classificação da baixa (Referencia_Operacao). Não vai para a ECF. Revisão 24 (D-N362, documento 121, Q101-8a, respondida: sim): o número do contrato de câmbio também fica aqui, só para o contador achar a operação; sem campo novo. |
| **Data_Emissao** | *data* | A data de nascimento do título --- a Data_Emissao da nota fiscal de origem, ou a data do lançamento/evento que o originou (comissão, royalty, avulso, reprogramação). |
| **Data_Vencimento** | *data* | Copiada de Mov_Pedido_Parcela.Data_Vencimento / Mov_Pedido_Venda_Parcela.Data_Vencimento quando ID_Parcela_Origem estiver preenchido, ou definida na reprogramação (seção 8) quando Origem_Tipo=reprogramacao --- editável depois, mesmo tratamento (renegociação sem histórico próprio; para um histórico rastreável, ver Mov_Titulo_Reprogramacao, seção 8) já dado à parcela do pedido. Para folha_pagamento (adicionado nesta revisão, 8): a data de pagamento definida pela política de folha da empresa (ex.: 5º dia útil do mês seguinte para a folha mensal) para as naturezas correntes, ou o prazo legal do art. 477 §6º CLT (até 10 dias corridos do desligamento, ver Fase 5, seção 2) quando Mov_Rh_Folha_Apuracao.Tipo_Folha=rescisao --- informada diretamente no nascimento do título, não recalculada por este módulo, que não tem conhecimento próprio de calendário de folha ou de prazo trabalhista. Revisão 13 (Bloco 5): para esocial_retorno_cr, dctfweb_darf e consolidacao_retencoes, a previsão sai de Cad_Regra_Vencimento e do calendário de feriados (Fase 0, revisão 47) e é ajustada para o vencimento oficial do DARF quando a declaração é importada. |
| **Status** | *enumeração {aberto, cancelado}* | Cobre só a exceção de cancelamento --- o ciclo normal de liquidação (aberto, baixado parcial, baixado total) nunca é armazenado aqui: é sempre DERIVADO, comparando Valor_Titulo contra a soma de tudo que já liquidou este título, mesma filosofia de \"saldo nunca armazenado\" usada em todo o dicionário (ex.: reserva de estoque, Fase 1). |
| **ID_Titulo_Substituto** | *referência (Mov_Titulo, autorreferência, opcional)* | Adicionado na revisão 13 (Bloco 5). O título que substituiu este quando o S-5011 ou o S-5012 foi retificado e este não tinha baixa (Status = cancelado). |
| **ID_Titulo_Complementado** | *referência (Mov_Titulo, autorreferência, opcional)* | Adicionado na revisão 13 (Bloco 5). O título já pago que este complementa pela diferença, quando a retificação aumenta o valor depois do pagamento (Contabilidade & Fiscal, seção 22.4.6). |

*Revisão 3 --- campos alterados (documento 37): Origem_Tipo.*

*Revisão 21 --- campos novos: ID_Moeda_Titulo, Valor_Titulo_Moeda, Taxa_Estimada, Data_Taxa_Estimada, ID_Natureza_Operacao_Cambial, Forma_Pagamento_Exterior_Prevista, Referencia_Operacao; campos alterados: Valor_Titulo.*

*Revisão 24 --- campos alterados: Valor_Titulo, ID_Moeda_Titulo, Valor_Titulo_Moeda, Taxa_Estimada, Data_Taxa_Estimada, Data_Taxa_Estimada, Referencia_Operacao.*

*Revisão 26 --- valores de enumeração novos: Origem_Tipo (+duimp_tributo, duimp_icms, locacao_pagamento).*

*Revisão 27 --- valores de enumeração novos: Origem_Tipo (+guia_tef).*

*Revisão 28 --- campos alterados: ID_Natureza_Operacao_Cambial.*

*Revisão 29 --- valores de enumeração novos: Origem_Tipo (+devolucao_nota_cancelada, devolucao_adiantamento).*

*Revisão 38 --- valores de enumeração novos: Origem_Tipo (+arrendamento_parcela).*

*Revisão 39 --- valores de enumeração novos: Origem_Tipo (+devolucao_credito_automotivo).*

*Revisão 40 --- valores de enumeração novos: Origem_Tipo (+aporte_mover, recolhimento_mover).*

*Saldo em aberto de um título --- fórmula, sem campo próprio:
Valor_Titulo menos a soma de Mov_Titulo_Baixa.Valor_Baixado (seção 3),
mais a soma de Mov_Credito_Aplicacao.Valor_Aplicado (seção 4), mais a
soma de Mov_Titulo_Reprogramacao_Item.Valor_Reprogramado de qualquer
reprogramação que tenha este título como origem (seção 8) --- as formas de
liquidar (ou encerrar) um título, todas somadas juntas (revisão 22, D-N353:
o encontro de contas deixou de ser uma soma própria; ele gera uma baixa de tipo
encontro em cada título, que já está na soma de Valor_Baixado, e somar também
Mov_Titulo_Encontro_Contas.Valor_Encontro contaria a compensação duas vezes), e
livremente combináveis: Alberto confirmou que um mesmo título pode, por
exemplo, ter parte baixada contra banco e parte aplicada de um
adiantamento, ou parte compensada por encontro de contas e o restante
baixado normalmente --- \"raramente dá zero a zero, a diferença
consequentemente vai para baixa contra banco\". \"Vencido\" também não é
um Status próprio: é Data_Vencimento no passado com saldo em aberto
maior que zero, sempre calculado no momento da consulta.*

*Origem folha_pagamento --- dois momentos, mesmo padrão já usado para
nota fiscal: adicionado nesta revisão (8), pedido por Alberto (\"a folha
bem com o movimento e lança tudo no a pagar, não só salários, INSS, FGTS
entre outros, e na tesouraria vem a baixa\"). O NASCIMENTO de um
Mov_Titulo com Origem_Tipo=folha_pagamento não gera lançamento contábil
novo --- mesmo princípio já estabelecido para nota_fiscal_entrada/saida
(acima): a despesa de pessoal e a obrigação (com o colaborador, com o
INSS, com o FGTS, com a Receita Federal) já foram reconhecidas pelo
lançamento que a própria liquidação da folha gera
(Mov_Lote_Lancamento.Origem_Tipo=folha_pagamento, resolvido pelo Motor
de Regras --- Fase 5, seção 3); o título aqui é, de novo, um registro de
CONTROLE FINANCEIRO (quando e quanto pagar a cada credor), não um evento
contábil por si só. Só a BAIXA deste título (seção 3) gera lançamento
--- a saída de caixa/banco contra a obrigação já reconhecida ---,
exatamente como já acontece para fornecedor.*

*Comportamento de aplicação (não é um campo novo de dados), adicionado
nesta revisão (9): antes de aceitar a criação ou alteração de um
Mov_Titulo, o sistema consulta Cad_Periodo_Fechamento_Filial (mecanismo
transversal da Fase 0, seção 10, revisão 37) pela combinação
Bloco=\"tesouraria\" + Filial (ID_Filial acima) + competência derivada
de Data_Emissao --- na ausência de uma linha com Status=aberto para essa
combinação (regime fail-closed: nenhuma combinação é tratada como aberta
por omissão), a operação é bloqueada. O bloco chama-se \"tesouraria\"
mesmo com Mov_Titulo fisicamente cadastrado neste documento: por decisão
de Alberto, é um único bloco de fechamento que se estende sobre as duas
entidades deste documento (título e baixa, seção 3) e sobre a execução
do pagamento propriamente dita, especificada no documento Fase 2 ---
Tesouraria (seção 6 daquele documento) --- fechar a competência de uma
Filial trava, ao mesmo tempo, o nascimento/alteração de título aqui e a
execução de pagamento lá, sem relação de causa/efeito com o bloco
\"contabilidade\" ou qualquer outro bloco do dicionário. Sem validação
de pendência no fechamento (exclusiva do bloco \"compras\", seção 6
daquele documento) --- um título fica em aberto por natureza até o
vencimento ou a baixa, não fazendo sentido exigir liquidação para fechar
o mês de entrada; mesmo princípio universal já usado nos demais blocos
deste dicionário, o fechado protege só o passado, sem checagem de
pendência antes de fechar.*

3\. Baixa/Liquidação --- Saldo em Banco, Caixa e Aplicação

A baixa é o evento de liquidação financeira propriamente dito ---
dinheiro de fato saindo ou entrando por uma conta de banco, caixa ou
aplicação. Reaproveita, sem qualquer mudança estrutural, o que o Fase 0
já preparava: Cad_Conta_Contabil.ID_Tipo_Conta já trazia, desde a
especificação original, a nota de que serviria para \"restringir a
escolha de conta em telas específicas (ex.: só contas Banco numa baixa
financeira)\". Este dicionário assume que o domínio tipo_conta
(Cad_Classe_Sistema, cadastro aberto) passa a ter também Caixa e
Aplicação como valores cadastrados, ao lado de Banco --- sem exigir
tabela nova. \"Saldo\" da própria conta, pelo mesmo princípio de nunca
armazenar o que pode ser derivado, é sempre a soma dos lançamentos
(Mov_Lancamento) já registrados naquela Cad_Conta_Contabil --- o mesmo
saldo corrente que qualquer conta do plano de contas já expõe, sem
estrutura nova aqui.

Mov_Titulo_Baixa

Um evento de liquidação --- total ou parcial --- de um título. Um mesmo
título pode ter mais de uma baixa (liquidação parcial ao longo do
tempo), combinável com crédito (adiantamento/bonificação/outras origens)
e encontro de contas (seção 2).

*Vigência: não --- é o registro de um evento; uma baixa lançada errada é
estornada por uma nova baixa negativa (ou por uma baixa de estorno),
nunca editada.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Baixa** | *identificador* | --- |
| **ID_Titulo** | *referência (Mov_Titulo)* | --- |
| **Origem_Tipo** | *enumeração {automatica_cnab, manual, vinculacao_dctfweb, estorno_tef}* | Adicionado nesta revisão (5), a pedido de Alberto --- mesmo padrão genérico já usado em Mov_Aprovacao_Instancia, Mov_Lote_Lancamento e Mov_Conciliacao_Bancaria (Tesouraria): estrutura fixa do próprio mecanismo, mesmo critério de Mov_Titulo.Status. \"automatica_cnab\" quando a baixa nasceu do retorno bancário processado automaticamente (Tesouraria, seção 6); \"manual\" quando um usuário deu baixa diretamente neste módulo. Revisão 13 (Bloco 5): vinculacao_dctfweb é a baixa sem movimento de caixa nascida da vinculação na DCTFWeb (dedução de salário-família e salário-maternidade, retenção da Lei 9.711, compensação, suspensão ou exclusão); o Valor_Titulo não é recalculado. Revisão 27 (documento 149, Q149-6 e Q149-15): estorno_tef é a baixa, sem movimento de caixa, do título em aberto da guia do TEF (guia_tef) quando o estorno de uma baixa reduz o mês; só em período aberto, nunca gera título, no padrão de vinculacao_dctfweb. |
| **ID_Tipo_Baixa** | *referência (Cad_Tipo_Baixa)* | Revisão 22 (D-N352): o tipo da baixa (Q111-5). Obrigatório em toda baixa, manual ou automática: na automática (retorno bancário) o ERP preenche o tipo de pagamento ou de recebimento; na manual o usuário escolhe, sem valor padrão. O tipo diz se a baixa movimenta dinheiro (Cad_Tipo_Baixa.Movimenta_Financeiro) e se, e por qual valor, ela entra em cada bloco (Cad_Tipo_Baixa_Bloco; hoje só o Y520). Origem_Tipo continua dizendo o canal (retorno, manual, DCTFWeb); o tipo diz a natureza da baixa. |
| **Data_Baixa** | *data* | Quando Origem_Tipo=automatica_cnab, a data em que a baixa foi de fato processada/lançada no sistema --- pode divergir de Data_Recebimento_Cnab (abaixo), ex.: o retorno bancário chega numa sexta, o processamento roda na segunda. |
| **Data_Recebimento_Cnab** | *data, opcional* | Adicionado nesta revisão (5) --- só quando Origem_Tipo=automatica_cnab: a data em que o retorno bancário chegou à Mlegate, espelhando Mov_Retorno_Bancario.Data_Recebimento (Tesouraria, seção 6) --- mantida separada de Data_Baixa porque as duas não são necessariamente o mesmo dia. |
| **ID_Participante_Baixa** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (5) --- obrigatório quando Origem_Tipo=manual, vazio quando automatica_cnab: o usuário/operador que deu a baixa manualmente, mesmo padrão já usado para ID_Participante_Classificacao e ID_Participante_Tratamento (Tesouraria). |
| **Valor_Baixado** | *número* | O valor real liquidado nesta baixa --- explícito, pode ser menor que o saldo em aberto do título (baixa parcial); fidelidade ao valor real, nunca assume automaticamente o total do título. Revisão 21 (D-N346, documento 101): no título em moeda estrangeira a baixa é lançada na moeda do título, e Valor_Baixado, Valor_Desconto e Valor_Juros_Multa ficam na moeda do título; o total em reais está em Valor_Pago_Reais (taxa digitada em Taxa_Cambio). Nos títulos em reais nada muda. Não há campo de moeda na baixa: vale a moeda do título. |
| **Valor_Desconto** | *número, opcional* | Desconto concedido (Tipo=receber, pagamento antecipado) ou obtido (Tipo=pagar) nesta baixa --- não altera Mov_Titulo.Valor_Titulo original, só registra a diferença entre o valor do título e o efetivamente liquidado. Revisão 24 (D-N362, documento 121, Q101-8e, respondida por Alberto em 26/10/2026): no título em moeda estrangeira o desconto fica na moeda do título e é convertido para reais **pela taxa da baixa** (Taxa_Cambio), a do contrato de câmbio ou a de referência. **Não é variação cambial.** O contador confirma a conta do desconto. Revisão 33 (documento 181, seção 2; D-N491 e D-N492): na baixa de título de guia de CSLL com bônus de adimplência (LC 225, art. 41), a guia entra pelo valor total, Valor_Baixado é o valor total do título e este campo guarda o desconto da CSLL; o dinheiro que saiu é Valor_Financeiro. O bônus (Mov_Bonus_Adimplencia_Csll.ID_Baixa) liga a esta baixa e copia o valor para a ECF. A conta contábil do desconto é ponto do contador (Q140-6a): enquanto ele não responde, o ERP não lança. |
| **Valor_Juros_Multa** | *número, opcional* | Acréscimo por atraso nesta baixa --- mesmo princípio: não altera o Valor_Titulo original. Revisão 24 (D-N362, documento 121, Q101-8e): no título em moeda estrangeira os juros e a multa ficam na moeda do título e são convertidos para reais **pela taxa da baixa** (Taxa_Cambio). **Não são variação cambial.** O contador confirma a conta dos juros. |
| **Taxa_Cambio** | *número, opcional* | Revisão 21 (D-N346): A taxa do **fechamento do câmbio**, **digitada** por quem paga ou recebe (Q100-17). **Sem contrato de câmbio** (cartão, depósito em conta no exterior, recursos mantidos no exterior, moeda), vale **a taxa que o operador do financeiro digita do pagamento** (Q105-3, 22/10/2026). Obrigatória quando o título é em moeda estrangeira; vazia nos demais. A série de cotações só serve de sugestão na tela. Revisão 23 (D-N358, documento 114, Q114-2): nas baixas de tipo encontro de um título em moeda estrangeira, as duas baixas do encontro levam a **mesma taxa**, a do encontro, digitada por quem o lança. Revisão 24 (D-N361 e D-N362, documento 121, Q101-8, Q101-8c e Q101-8d, respondidas por Alberto em 26/10/2026): quem baixa lança a taxa da moeda, com o contrato de câmbio. Em **toda** baixa de título em moeda, inclusive a **sem dinheiro** (perda, desconto sem pagamento), a taxa é obrigatória: sem contrato de câmbio é uma **taxa de referência**, digitada por quem baixa (a série de cotações é só sugestão na tela). Na baixa automática do retorno bancário, o item que o banco **não aprovou** continua pendente e não gera baixa; o retorno sem a taxa do contrato também fica pendente, na tela de consistência do retorno, até quem baixa digitar a taxa. |
| **Valor_Pago_Reais** | *número, opcional* | Revisão 21 (D-N346): O total pago ou recebido **em reais**: (Valor_Baixado − Valor_Desconto + Valor_Juros_Multa) × Taxa_Cambio, arredondado pelas casas da moeda funcional. Calculado pelo ERP e guardado como snapshot (como Mov_Lancamento.Valor_Moeda_Funcional). É o valor **bruto** da baixa, o integral da operação: o da variação cambial final e o do Y520 quando a Base do tipo é valor_bruto (antes das retenções). Revisão 22 (D-N352, documento 111): o dinheiro que saiu da empresa, e o que a conciliação bancária lê, é Valor_Financeiro; na baixa de tipo encontro, Valor_Pago_Reais é o valor integral do título na operação, mesmo com a transferência reduzida ou zero (Q111-10). Revisão 24 (D-N362 e D-N363, documento 121, Q101-8e e Q101-8g, respondidas por Alberto em 26/10/2026): o desconto e os juros entram convertidos pela taxa da baixa e ficam fora da variação cambial, que é a do **valor baixado**: Valor_Baixado × (a taxa em que o saldo estava contabilizado − Taxa_Cambio). Na baixa **sem dinheiro**, com a taxa de referência, a diferença entre o valor contabilizado do saldo e o valor pela taxa de referência também é variação cambial lançada na baixa (Q101-8g). A diferença de centavos contra o extrato fica em Valor_Arredondamento_Com_Sinal. Revisão 25 (D-N367, documento 123, Q113-4, respondida por Alberto em 27/10/2026): no título **em reais** de não residente este campo não existe (só há em moeda estrangeira), e o valor bruto do Y520 é o **total da baixa**: valor baixado menos o desconto mais os juros e a multa. Na baixa automática de ordem ao exterior (D-N371, documentos 107 e 124), este campo continua **calculado**; o valor em reais que o banco devolve (Mov_Retorno_Bancario_Item.Valor_Reais_Ocorrencia) só **confere** contra o dinheiro do extrato, e quem corrige é a taxa, com motivo. |
| **Valor_Financeiro** | *número, opcional* | Revisão 22 (D-N352): o dinheiro efetivamente movimentado por esta baixa, em reais (Q111-8). Pagamento e recebimento: igual ao total da baixa em reais. Baixa de tipo encontro: zero, porque o dinheiro do encontro é a diferença, que vai ao banco ou caixa no próprio encontro (Mov_Titulo_Encontro_Contas). É o que o Y520 lê quando a Base do tipo é valor_financeiro e o valor que a conta de banco ou caixa e a conciliação bancária enxergam. Tipo com Movimenta_Financeiro = sempre exige valor maior que zero; nunca, vazio ou zero; variavel, qualquer um dos dois. Revisão 24 (D-N362 e D-N364, documento 121, Q101-8b e Q101-8f2): a conferência contra o extrato aceita diferença de até R$ 0,04, para mais ou para menos, **sem percentual** (parâmetro do sistema; o aviso por percentual contra a série, que a revisão 21 previa, está cancelado: o erro de digitação da taxa é pego pela conferência contra o extrato). A diferença dentro da tolerância fica em Valor_Arredondamento_Com_Sinal; acima dela a baixa não é confirmada até corrigir a taxa. |
| **Valor_Arredondamento_Com_Sinal** | *número, opcional* | Revisão 24 (D-N363 e D-N364): (documento 121, Q101-8f, Q101-8f1, Q101-8f2 e Q101-8f3, respondidas por Alberto em 26/10/2026; a Q101-8f1 a 8f3 foram respondidas com "sim para três", lido como sim às três) a diferença, em reais, entre o dinheiro que o banco movimentou (o do extrato) e o Valor_Financeiro calculado pelo ERP, numa baixa **com dinheiro** de título em moeda estrangeira. Positivo quando o extrato mostra **mais** dinheiro que o calculado, nos dois sentidos (pagar e receber). O valor absoluto **não passa da tolerância** (parâmetro do sistema, com R$ 0,04 de partida; Alberto escreveu "0,04 centavos", lido como quatro centavos); **acima dela a baixa não é confirmada** até corrigir a taxa. Vazio quando não há diferença e nas baixas de título em reais. A diferença é **lançada no lote da baixa**, numa conta de resultado parametrizada (a conta é do contador), para o razão do banco fechar com o extrato. **Não entra no Y520.** A conciliação bancária compara o extrato com Valor_Financeiro mais este campo. O nome leva Com_Sinal pela regra D-N344. Revisão 25 (D-N371, documento 124, Q107-2a): na baixa de ordem ao exterior, a diferença de até R$ 0,04 entre o valor em reais devolvido pelo banco (Valor_Reais_Ocorrencia, só o câmbio, sem IOF nem tarifas) e o valor calculado vai para este campo; acima da tolerância a baixa não é confirmada e o item fica pendente. |
| **Valor_Tributo_Split** | *número, opcional* | Adicionado na revisão 6, pedido pela consolidação da Fase 2 Contabilidade & Fiscal (seção 10): a parte do valor do título que o operador de pagamento (banco, adquirente de cartão, instituição de boleto/Pix) segrega no ato da liquidação e recolhe direto aos cofres públicos (split payment do IBS/CBS) --- nunca passa pela conta da Mlegate. Valor_Baixado continua fiel ao valor real que de fato bateu na conta; a soma Valor_Baixado + Valor_Tributo_Split + a soma de Valor_Retido de eventuais retenções na fonte (Mov_Titulo_Retencao, Fase 2 --- Contabilidade & Fiscal, seção 11) fecha o valor total liquidado do título. |
| **Canal_Split** | *enumeração {pix, boleto, ted, tef}, opcional* | Adicionado nesta revisão (7), pedido pela consolidação da Fase 2 Contabilidade & Fiscal: preenchido só quando Valor_Tributo_Split (acima) estiver preenchido --- o canal de liquidação pelo qual o split bancário do IBS/CBS foi executado. A adesão ao split payment é restrita a esses quatro canais (sem cartão/voucher/B2C, conforme Ato Conjunto RFB/CGIBS nº 2/2026); o campo é o que permite filtrar/auditar quais baixas passaram pelo mecanismo. |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco/Caixa/Aplicação, opcional)* | De onde saiu (pagar) ou para onde entrou (receber) o valor --- a mesma restrição de tipo de conta já prevista no Fase 0. Revisão 22 (D-N352, documento 111): passa a obrigatório só quando Valor_Financeiro é maior que zero; vazio nas baixas sem dinheiro (perda, desconto, vinculação da DCTFWeb e as de tipo encontro, cujo banco ou caixa fica no próprio encontro). Revisão 32 (documento 176, seção 5.3, resposta C176-3; D-N484): o estabelecimento que informa o 1601 é a filial titular da conta bancária onde o dinheiro caiu (Cad_Conta_Bancaria.ID_Filial, ligada a esta baixa por esta conta contábil), e não a que emitiu a nota; é derivado e não cria campo. O Motor avisa quando a filial da conta difere da filial da nota. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento, opcional)* | O lote de lançamento contábil gerado por esta baixa --- Origem_Tipo=baixa_titulo (Fase 0). Revisão 23 (D-N358, documento 114, Q114-1 opção B, respondida por Alberto em 26/10/2026; a revisão 22 dizia que ficava vazio): nas baixas de tipo encontro aponta o **mesmo lote do encontro** (ID_Lote de Mov_Titulo_Encontro_Contas, com Origem_Tipo = encontro_contas), que inclui a perna de banco ou caixa. As duas baixas e o encontro apontam esse lote, que continua sendo um só: nada é lançado duas vezes, e a navegação da baixa ao lote é a mesma das outras baixas. Estornar uma baixa de encontro estorna o encontro inteiro (as duas baixas, o lote e a variação cambial realizada, se houver). |
| **ID_Encontro** | *referência (Mov_Titulo_Encontro_Contas), opcional* | Revisão 22 (D-N353): a amarração do encontro de contas (Q111-11 e Q111-13). Preenchido nas baixas de tipo encontro e aponta o encontro que as gerou; as duas baixas (a do título a pagar e a do título a receber) apontam o mesmo encontro. Vazio nas demais. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | Preenchido só quando esta baixa (Tipo=pagar) precisou de aprovação da camada extra de caixa (seção 11) --- reaproveitando a régua do Fase 0 (Origem_Tipo=camada_caixa). |
| **ID_Participante_Instituicao_Pagamento** | *referência (Cad_Participante), opcional* | Revisão 32 (documento 176, seção 5.3, Q176-1 e Q176-4; D-N482 e D-N484): COD_PART_IP do 1601: a instituição financeira, de pagamento ou plataforma por onde o dinheiro passou. Aviso quando o tipo de baixa entra no 1601 e o campo está vazio. Na baixa por retorno bancário o Motor propõe a instituição da conta (Cad_Conta_Bancaria). No cartão a credenciadora da transação de cartão pode substituí-lo (documento 177, ainda sem decisão). |
| **ID_Participante_Intermediador** | *referência (Cad_Participante), opcional* | Revisão 32 (documento 176, seção 5.3, Q176-1 e Q176-4; D-N482 e D-N484): COD_PART_IT do 1601: o marketplace ou app que intermediou a venda. Na baixa de título de nota de saída sai da nota (Mov_Nota_Fiscal_Saida.ID_Participante_Intermediador); preenchido aqui só quando não há nota. |
| **Classe_Incidencia_1601** | *enumeração {icms, iss, outros}, opcional* | Revisão 32 (documento 176, seção 5.3, Q176-1 e Q176-4; D-N482 e D-N484): Em qual dos três campos do 1601 o valor entra (TOT_VS, TOT_ISS e TOT_OUTROS). Só quando a baixa não tem nota (adiantamento, depósito, pagamento sem documento). Com nota o Motor deriva pelo CST e pelo CFOP 5933 e o campo fica vazio, para não gravar o que muda se a nota mudar. |
| **ID_Transacao_Cartao** | *referência (Mov_Transacao_Cartao), opcional* | Revisão 34 (documento 177, seção 3; D-N485: Q177-1 a Q177-5): Revisão 34 (documento 177, seção 3.1): a transação cujo crédito (uma parcela) esta baixa liquidou. Vazio quando o recebimento não é cartão. A baixa só carrega `ID_Participante_Instituicao_Pagamento` quando o recebimento **não** é por cartão (documento 176, seção 5.3). |

*Revisão 21 --- campos novos: Taxa_Cambio, Valor_Pago_Reais; campos alterados: Valor_Baixado.*

*Revisão 22 --- campos novos: ID_Tipo_Baixa, Valor_Financeiro, ID_Encontro; campos alterados: Valor_Pago_Reais, ID_Conta_Contabil, ID_Lote.*

*Revisão 23 --- campos alterados: ID_Lote, Taxa_Cambio.*

*Revisão 24 --- campos novos: Valor_Arredondamento_Com_Sinal; campos alterados: Valor_Desconto, Valor_Juros_Multa, Taxa_Cambio, Valor_Pago_Reais, Valor_Financeiro.*

*Revisão 25 --- campos alterados: Valor_Pago_Reais, Valor_Arredondamento_Com_Sinal.*

*Revisão 27 --- valores de enumeração novos: Origem_Tipo (+estorno_tef).*

*Revisão 32 --- campos novos: ID_Participante_Instituicao_Pagamento, ID_Participante_Intermediador, Classe_Incidencia_1601; campos alterados: ID_Conta_Contabil.*

*Revisão 33 --- campos alterados: Valor_Desconto.*

*Revisão 34 --- campos novos: ID_Transacao_Cartao.*

*Tipo da baixa e valores (revisão 22, D-N352 e D-N353; documento 111). Toda baixa leva um tipo (Cad_Tipo_Baixa), cadastrável e único para o grupo, que diz se ela movimenta dinheiro (sempre, nunca ou variável) e, por bloco (Cad_Tipo_Baixa_Bloco, hoje só o Y520), se entra e por qual valor: o dinheiro movimentado (Valor_Financeiro) ou o bruto (Valor_Pago_Reais, o integral da operação). Tipos de partida, a confirmar na implantação: pagamento e recebimento (movimentam; entram no Y520 pelo valor financeiro), perda e desconto (não movimentam; não entram), encontro de contas (variável; entra pelo valor bruto, mesmo com a transferência reduzida ou zero) e vinculação da DCTFWeb (não movimenta). No encontro de contas há uma baixa de tipo encontro em cada título, cada uma pelo valor do seu título, com Valor_Financeiro zero e ID_Encontro apontando o mesmo encontro; a diferença em dinheiro vai ao banco ou caixa no encontro, não numa terceira baixa. Só a baixa que tem dinheiro (Valor_Financeiro maior que zero) pede ID_Conta_Contabil.*

*Rastreabilidade de uma baixa automática até o retorno bancário que a
gerou (qual arquivo/API, qual ocorrência): não duplicada aqui --- já
existe pelo caminho inverso, em
Mov_Retorno_Bancario_Item.ID_Baixa_Gerada (Tesouraria, seção 6),
evitando um campo redundante nos dois sentidos.*

*A verificação de saldo (\"verifica saldo em bancos, caixa e aplicações
no momento da baixa\", Documento Analítico) aplica-se sobretudo a
Tipo=pagar: antes de confirmar uma baixa de pagamento, o saldo corrente
de ID_Conta_Contabil (soma de Mov_Lancamento já lançados nela) precisa
cobrir Valor_Baixado --- uma validação de camada de aplicação, não uma
restrição estrutural (mesmo padrão já usado para outras validações deste
dicionário, ex.: soma de percentuais de comissão). Para Tipo=receber, a
baixa apenas incrementa o saldo da conta; não há saldo a \"verificar\"
antes de receber.*

*Retenção na fonte sobre uma baixa (IRRF/INSS/ISS retido/PIS-COFINS-CSLL
retido/IBS-CBS retido, nos dois sentidos --- a que a Mlegate faz ao
pagar um fornecedor, e a que um cliente órgão público/sociedade de
economia mista faz ao pagar a Mlegate) não é modelada aqui, por decisão
de escopo: vive como entidade própria, Mov_Titulo_Retencao,
referenciando esta mesma Mov_Titulo_Baixa por ID_Baixa --- ver Fase 2
Contabilidade & Fiscal, seção 11. Cross-referenciado nesta revisão (10):
é por causa dessa retenção (e do split payment de Valor_Tributo_Split,
acima) que o valor de fato liquidado por uma baixa pode ser menor que o
valor de face da nota fiscal que deu origem ao título ---
Mov_Titulo.Valor_Titulo (seção 2) nunca muda por isso, continua fiel ao
valor negociado; é a soma Valor_Baixado + Valor_Tributo_Split + soma de
Mov_Titulo_Retencao.Valor_Retido, ao longo de todas as baixas de um
título, que fecha exatamente Valor_Titulo --- fórmula já documentada do
lado de Contabilidade & Fiscal (seção 11 daquele documento), sem
estrutura nova aqui.*

*Comportamento de aplicação (não é um campo novo de dados), adicionado
nesta revisão (9): pelo mesmo bloco \"tesouraria\" descrito na seção 2,
nenhuma Mov_Titulo_Baixa pode ser lançada ou alterada com Data_Baixa
dentro de uma competência já fechada para a Filial do título associado
(ID_Filial de Mov_Titulo, seção 2) --- mesma consulta a
Cad_Periodo_Fechamento_Filial e o mesmo regime fail-closed descritos
acima. Vale tanto para Origem_Tipo=manual (baixa dada diretamente neste
módulo) quanto para Origem_Tipo=automatica_cnab --- esta última, na
prática, é sempre gerada do lado da Tesouraria (retorno bancário, ver
Fase 2 --- Tesouraria, seção 6), que valida o mesmo gate antes de
disparar a baixa: as duas pontas do fluxo --- o nascimento/alteração do
título na seção 2 e a execução do pagamento no documento de Tesouraria
--- respeitam exatamente a mesma trava de competência+filial, porque é o
mesmo bloco de fechamento, não dois blocos coordenados.*

4\. Crédito de Cliente e Fornecedor (Adiantamento, Bonificação e Outras
Origens)

Generalizada na Revisão 2 e novamente nesta Revisão 3, a pedido de
Alberto: além do adiantamento em dinheiro (valor recebido de um cliente
ou pago a um fornecedor antes de qualquer título específico existir),
esta entidade cobre qualquer crédito comercial concedido por uma
transação, sem movimentação bancária --- bonificação foi só o primeiro
exemplo dado por Alberto (\"comprar X toneladas de arroz por R\$W gera
um crédito de bonificação de R\$Y, usado para pagar a próxima compra com
este fornecedor\"); crédito TRIBUTÁRIO (tributos pagos a maior,
compensados futuramente) é outro exemplo dado --- a lista fica aberta
para \"entre outros\". Por isso a entidade foi renomeada nesta revisão
(3) de Mov_Adiantamento para Mov_Credito, mais fiel ao que ela já cobre;
os campos internos já usavam \"Crédito\" desde a Revisão 2
(Data_Credito, Valor_Credito), só o nome da entidade estava atrasado.
Todos os casos nascem como um evento próprio, independente de título, e
só depois são aplicados contra um ou mais títulos reais, total ou
parcialmente (seção 2).

Mov_Credito

O recebimento/pagamento antecipado em dinheiro
(Origem_Tipo=adiantamento_financeiro) OU um crédito comercial nascido de
uma transação (Origem_Tipo=credito_nao_financeiro --- bonificação,
crédito tributário, entre outros, classificados por ID_Tipo_Credito),
ainda sem título específico vinculado.

*Vigência: não --- é o registro de um evento; a aplicação contra título
é registrada à parte, abaixo.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Credito** | *identificador* | Renomeado nesta revisão (3) de ID_Adiantamento. |
| **Tipo** | *enumeração {pagar, receber}* | Crédito dado a um fornecedor (pagar) ou recebido de um cliente (receber) --- mesmo motor de Mov_Titulo, mesma direção dupla. |
| **Origem_Tipo** | *enumeração {adiantamento_financeiro, credito_nao_financeiro}* | Simplificado nesta revisão (3) para ser puramente ESTRUTURAL --- só decide se ID_Conta_Contabil é exigido. \"adiantamento_financeiro\" é dinheiro movimentado antes de existir título. \"credito_nao_financeiro\" (renomeado de \"bonificacao\"/\"outro\") é qualquer crédito comercial sem conta de banco/caixa/aplicação envolvida --- sua natureza específica passou para o novo campo ID_Tipo_Credito, abaixo. |
| **ID_Tipo_Credito** | *referência (Cad_Classe_Sistema, domínio = tipo_credito_adiantamento, opcional)* | Adicionado nesta revisão (3): preenchido só quando Origem_Tipo=credito_nao_financeiro --- classifica a origem específica do crédito (bonificação, crédito tributário, entre outros). Domínio aberto (Fase 0, revisão 18): um novo tipo de crédito não financeiro é um novo valor aqui, nunca uma mudança de estrutura. |
| **ID_Filial** | *referência (Cad_Filial)* | --- |
| **ID_Participante** | *referência (Cad_Participante)* | O fornecedor ou cliente que recebeu/deu o crédito --- a transação que originou o crédito pode ter sido com este participante especificamente, mas a aplicação (abaixo) pode abater título de outra filial da mesma raiz de CNPJ. |
| **Data_Credito** | *data* | A data do adiantamento em dinheiro ou do evento que gerou o crédito não-financeiro. |
| **Valor_Credito** | *número* | O valor total do crédito, explícito, em todos os casos. Revisão 21 (D-N346, documento 101): em adiantamento em moeda estrangeira (ID_Moeda_Credito preenchido) o valor é na moeda do crédito; o total em reais está em Valor_Pago_Reais. |
| **ID_Moeda_Credito** | *referência (Cad_Moeda), opcional* | Revisão 21 (D-N346): A moeda do adiantamento. Vazio = moeda funcional. Em adiantamento em moeda, Valor_Credito passa a ser **na moeda do crédito**. Revisão 24 (D-N361, documento 120, Q101-10, respondida por Alberto em 26/10/2026): o adiantamento em moeda estrangeira é **reavaliado todo mês** e a variação cambial é calculada (a regra 6 do documento 101, que o tratava como item não monetário, está superada). A entidade que guardaria a reavaliação do adiantamento (Mov_Credito_Reavaliacao, documento 120) **ainda não foi aprovada** (Q101-10a a Q101-10c) e **não está no dicionário**. Revisão 25 (D-N368 e D-N370, documentos 120 e 123, Q101-10a, Q101-10b e Q123-2, respondidas por Alberto em 27/10/2026, com a correção de 28/10/2026, D-N396): **todo** crédito em moeda estrangeira, financeiro ou não (bonificação, cashback, crédito tributário), **dado a um fornecedor (Tipo = pagar, um valor a receber) ou recebido de um cliente (Tipo = receber, um valor a pagar)**, é reavaliado todo mês e tem a variação cambial calculada; o resultado fica em Mov_Credito_Reavaliacao (entidade nova desta revisão). **A variação cambial vale para o que a empresa tem a receber e para o que ela deve**: o título a pagar e o a receber em moeda são reavaliados por Mov_Titulo_Reavaliacao, e o crédito dos dois sentidos por Mov_Credito_Reavaliacao. O contador confirma o tratamento de item não monetário. |
| **Taxa_Cambio** | *número, opcional* | Revisão 21 (D-N346): A taxa do fechamento do câmbio do adiantamento, **digitada** (sem contrato de câmbio, a que o operador do financeiro digita do pagamento, Q105-3). Obrigatória quando a moeda difere da funcional e Origem_Tipo = adiantamento_financeiro. Revisão 25 (D-N370, documento 123, Q123-2, respondida por Alberto em 27/10/2026): obrigatória em **todo** crédito em moeda estrangeira, financeiro ou não (antes, só no adiantamento financeiro); no crédito não financeiro é a taxa de partida da reavaliação mensal. |
| **Valor_Pago_Reais** | *número, opcional* | Revisão 21 (D-N346): O que saiu (ou entrou) em reais: Valor_Credito × Taxa_Cambio. Snapshot, como na baixa. É o valor do Y520 do adiantamento (documento 100). |
| **Data_Validade** | *data, opcional* | Adicionado nesta revisão (3), a pedido de Alberto: a data-limite para usar este crédito --- tipo cashback, que precisa ser usado até uma data específica. Nulo quando o crédito não tem prazo (ex.: adiantamento financeiro comum). Um crédito com Data_Validade no passado e saldo disponível positivo está VENCIDO --- calculado no momento da consulta, sem Status próprio para isso (mesma filosofia de \"saldo/status nunca armazenado\" do projeto) --- e não pode mais ser aplicado (ver validação, abaixo). |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco/Caixa/Aplicação, opcional)* | Preenchido só quando Origem_Tipo=adiantamento_financeiro (por onde o dinheiro entrou/saiu); vazio quando Origem_Tipo=credito_nao_financeiro, que não movimenta banco/caixa/aplicação nenhum. |
| **ID_Origem** | *referência genérica, opcional* | Presente quando Origem_Tipo=credito_nao_financeiro --- a nota fiscal ou o pedido que gerou o crédito. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento, opcional)* | O lançamento contábil do crédito em si --- Origem_Tipo=outro (ver Notas), tanto para o adiantamento financeiro (crédito/débito de conta de passivo/ativo de adiantamento contra banco/caixa/aplicação) quanto para o crédito não-financeiro (crédito de uma conta de direito, sem contrapartida em banco). |
| **Status** | *enumeração {aberto, cancelado}* | Mesma filosofia de Mov_Titulo.Status --- aplicado parcial/total é sempre derivado (soma de Mov_Credito_Aplicacao.Valor_Aplicado contra Valor_Credito), nunca armazenado. |
| **Contabiliza_Na_Inclusao** | *booleano, opcional* | Adicionado nesta revisão (7), respondendo ao ponto que ficava aberto sobre o que fazer com o saldo de um crédito vencido não usado: se true, o saldo não aplicado até Data_Validade é baixado automaticamente como perda (novo Mov_Lote_Lancamento.Origem_Tipo=perda_credito_vencido, Fase 0) no momento do vencimento; se false --- o padrão, mais simples --- a expiração continua silenciosa como já modelado (o crédito só para de poder ser aplicado), porque a aplicação do crédito já funciona como desconto direto na duplicata enquanto vigente, sem necessidade de reconhecer perda formal à parte. |

*Revisão 21 --- campos novos: ID_Moeda_Credito, Taxa_Cambio, Valor_Pago_Reais; campos alterados: Valor_Credito.*

*Revisão 24 --- campos alterados: ID_Moeda_Credito.*

*Revisão 25 --- campos alterados: ID_Moeda_Credito, Taxa_Cambio.*

Mov_Credito_Aplicacao

O evento de usar (total ou parcialmente) um crédito --- adiantamento,
bonificação, crédito tributário ou qualquer outra origem --- contra um
título específico --- um mesmo crédito pode ser aplicado contra mais de
um título ao longo do tempo, até esgotar seu valor.

*Vigência: não --- é o registro de um evento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Aplicacao** | *identificador* | --- |
| **ID_Credito** | *referência (Mov_Credito)* | Renomeado nesta revisão (3) de ID_Adiantamento. |
| **ID_Titulo** | *referência (Mov_Titulo)* | O título sendo (parcialmente) liquidado por este crédito. |
| **Data_Aplicacao** | *data* | --- Revisão 25 (D-N375, documento 128, Q127-6, respondida por Alberto em 27/10/2026): para o IRPJ e a CSLL do lucro presumido por caixa, o recebimento de adiantamento de cliente **não** é receita; a receita é reconhecida na aplicação do adiantamento contra o título da nota, nesta data (primeiro faturamento). Revisão 28 (documentos 152 e 153; Q128-6, Q128-7, Q152-3; D-N435 a D-N437): o IBS e a CBS do adiantamento são tributados no recebimento, com a alíquota do local da operação (para o serviço, onde ele é executado), e o que foi pago no recebimento é abatido na aplicação (Mov_Credito_Aplicacao_Tributo); o PIS e a Cofins, no regime de caixa, não são tributados no recebimento: nascem na emissão da nota. A aplicação é feita contra o título da primeira nota de venda (a nota de entrega, se for de venda, ou a de faturamento); a simples remessa nunca conta, e o ERP avisa, sem bloquear, quando se aplica adiantamento contra ela ou quando uma nota de entrega de venda sai sem aplicação. A nota é identificada pelo enquadramento do Motor de Regras (CFOP); não há evento de entrega. |
| **ID_Moeda_Paridade** | *referência (Cad_Moeda), opcional* | Revisão 25 (D-N369 e D-N370, documento 123, Q101-3b e Q123-1, respondidas por Alberto em 27/10/2026): a moeda de paridade da aplicação, quando a moeda do crédito difere da do título: o usuário escolhe uma das duas moedas dos itens. Obrigatório quando as moedas diferem; vazio quando são iguais. |
| **Cotacao_Equivalencia** | *número, opcional (8 casas)* | Revisão 25 (D-N369 e D-N370, documento 123, Q101-3b e Q123-1): a cotação de equivalência entre as duas moedas, informada pelo usuário: a quantidade da **outra** moeda que vale **uma unidade da moeda de paridade**. Exemplo: com o dólar a R$ 5,00, se a paridade é o dólar, a cotação é 5,00 (reais por dólar); se a paridade é o real, a cotação é 0,2 (dólares por real). Obrigatória nas mesmas condições de ID_Moeda_Paridade. |
| **Valor_Aplicado** | *número* | O valor deste crédito usado para liquidar o título indicado --- reduz, por soma, tanto o saldo em aberto do título (seção 2) quanto o saldo disponível do próprio crédito (acima). Revisão 25 (D-N368 a D-N370, documentos 120 e 123, Q101-10c e Q101-3b): na aplicação vale o valor **contabilizado** do crédito, o da última reavaliação mensal (ou o do envio, se ainda não houve reavaliação); a diferença contra o valor do título é a variação cambial realizada. Quando as moedas do crédito e do título diferem, o valor fica **na moeda de paridade** (ID_Moeda_Paridade), com a Cotacao_Equivalencia informada pelo usuário; a regra de mesma moeda do documento 101 (seção 4.3) deixa de valer. |

*Revisão 25 --- campos novos: ID_Moeda_Paridade, Cotacao_Equivalencia; campos alterados: Data_Aplicacao, Valor_Aplicado.*

*Revisão 28 --- campos alterados: Data_Aplicacao.*

*Validação de camada de aplicação, não de estrutura: Mov_Credito.Tipo e
Mov_Titulo.Tipo precisam ser o mesmo. Quanto ao participante ---
resposta de Alberto: \"a princípio fica amarrado ao fornecedor; quando
falo CNPJ raiz, pode ser usado para pagar de uma outra filial\" --- a
exigência não é ID_Participante idêntico, e sim CNPJ_Raiz idêntico entre
Mov_Credito.ID_Participante e Mov_Titulo.ID_Participante
(Cad_Participante.CNPJ_Raiz, Fase 0 revisão 17): um crédito dado por/à
matriz pode abater título de qualquer filial da mesma raiz, e
vice-versa. Só se aplica a participante PJ --- um crédito de
participante PF continua exigindo o mesmo Cad_Participante exato, já que
CPF não tem estrutura de raiz/filial. Adicionado nesta revisão (3): a
aplicação também exige Data_Validade nula OU ainda não vencida na
Data_Aplicacao --- um crédito vencido não pode mais ser aplicado, mesmo
com saldo disponível positivo. A estrutura de dados em si não impede,
por si só, uma aplicação cruzada incorreta ou o uso de um crédito
vencido --- ambas são validações de camada de aplicação.*

5\. Encontro de Contas

Quando um mesmo participante é, ao mesmo tempo, fornecedor e cliente
(Cad_Participante_Classe já suporta as duas classes simultâneas, Fase 0)
--- compensa-se um título a pagar contra um título a receber daquele
participante, em vez de liquidar os dois separadamente por banco/caixa.
É uma das formas de liquidar um título, ao lado da aplicação de crédito
(seção 4) e da reprogramação (seção 8), e desde a revisão 22 (D-N353) é
lançado como baixa: gera uma baixa de tipo encontro em cada título (seção 3),
cada uma pelo valor do seu título, e a entidade abaixo agrupa a operação
inteira (as duas baixas e a diferença em dinheiro que passa por banco ou caixa).

Mov_Titulo_Encontro_Contas

Um evento de compensação entre um título a pagar e um título a receber
do mesmo participante.

*Vigência: não --- é o registro de um evento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Encontro** | *identificador* | --- |
| **ID_Titulo_Pagar** | *referência (Mov_Titulo, Tipo=pagar)* | --- |
| **ID_Titulo_Receber** | *referência (Mov_Titulo, Tipo=receber)* | --- |
| **Data_Encontro** | *data* | --- |
| **ID_Participante_Encontro** | *referência (Cad_Participante)* | Revisão 25 (D-N367 e D-N368, documento 123, Q113-8, respondida por Alberto em 27/10/2026): quem lançou o encontro, preenchido com o usuário logado. As duas baixas de tipo encontro ficam com Origem_Tipo = manual e ID_Participante_Baixa igual a este campo. |
| **ID_Participante_Diferenca** | *referência (Cad_Participante), opcional* | Revisão 25 (D-N367 e D-N368, documento 123, Q113-8 e Q113-9): quem recebe ou deposita a diferença em dinheiro: obrigatório quando Valor_Diferenca é maior que zero e os dois títulos são de participantes diferentes (se a empresa **paga**, quem recebe o depósito; se **recebe**, quem deposita); pode ser um terceiro cadastrado. No encontro com o mesmo participante, o sistema preenche com ele. |
| **ID_Moeda_Paridade** | *referência (Cad_Moeda), opcional* | Revisão 25 (D-N369 e D-N370, documento 123, Q101-3b e Q123-1): a moeda de paridade do encontro, quando os títulos estão em moedas diferentes: uma das duas moedas. Obrigatório quando as moedas diferem. |
| **Cotacao_Equivalencia** | *número, opcional (8 casas)* | Revisão 25 (D-N369 e D-N370, documento 123, Q101-3b e Q123-1): a cotação de equivalência informada pelo usuário: a quantidade da outra moeda que vale uma unidade da moeda de paridade (dólar a R$ 5,00: paridade dólar = 5,00; paridade real = 0,2). Obrigatória nas mesmas condições de ID_Moeda_Paridade. |
| **Valor_Encontro** | *número* | O valor efetivamente compensado entre os dois títulos --- pode ser menor que o saldo em aberto de qualquer um dos dois (encontro parcial); continua sendo a parte compensada (a menor das duas). Revisão 22 (D-N353): o saldo de cada título passa a cair pela baixa de tipo encontro desse título (Mov_Titulo_Baixa.ID_Encontro), cada uma pelo valor do seu título, e não mais por esta soma, para não contar a compensação duas vezes. Revisão 25 (D-N369 e D-N370, documento 123, Q101-3b e Q123-1): quando os títulos estão em moedas diferentes, o valor do encontro fica **na moeda de paridade** (ID_Moeda_Paridade). A apuração da variação cambial de cada título nesse caso é ponto do contador (o documento 114 só trata do encontro em reais ou na moeda dos dois títulos). Revisão 25 (Q113-9, "sim pode", lido como a leitura A): o encontro aceita **qualquer par de participantes**, não só o mesmo; a base legal e o tratamento fiscal e contábil são do jurídico e do contador. |
| **Valor_Diferenca** | *número, opcional* | Revisão 22 (D-N353): a diferença em dinheiro do encontro, em reais: o valor do título a pagar menos o do a receber, em módulo (Q111-11 e Q111-13). Zero ou vazio quando um compensa o outro por inteiro. |
| **Sentido_Diferenca** | *enumeração {pagamos, recebemos}, opcional* | Revisão 22 (D-N353): quem paga a diferença. Obrigatório quando Valor_Diferenca é maior que zero. |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco/Caixa/Aplicação, opcional)* | Revisão 22 (D-N353): o banco, caixa ou aplicação por onde passou a diferença. Obrigatório quando Valor_Diferenca é maior que zero. A conciliação bancária casa a linha do extrato da diferença com este encontro (Mov_Conciliacao_Bancaria, Origem_Tipo = mov_titulo_encontro_contas). |
| **ID_Lote** | *referência (Mov_Lote_Lancamento, opcional)* | O lançamento contábil do encontro (débito da obrigação a pagar, crédito do direito a receber, mais a perna de banco, caixa ou aplicação com a diferença em dinheiro, quando houver: ID_Conta_Contabil, abaixo --- revisão 22, D-N353) --- Origem_Tipo=encontro_contas (revisão 23, D-N358, Q114-3). Revisão 23 (Q114-1, opção B): o lote é compartilhado pelo encontro e pelas suas duas baixas de tipo encontro (Mov_Titulo_Baixa.ID_Lote aponta este mesmo lote). Em título em moeda estrangeira, a variação cambial realizada de cada ponta entra em lote à parte (Origem_Tipo = variacao_cambial), contra o banco, com a mesma taxa nas duas baixas (Q114-2). |

*Revisão 22 --- campos novos: Valor_Diferenca, Sentido_Diferenca, ID_Conta_Contabil; campos alterados: Valor_Encontro, ID_Lote.*

*Revisão 23 --- campos alterados: ID_Lote.*

*Revisão 25 --- campos novos: ID_Participante_Encontro, ID_Participante_Diferenca, ID_Moeda_Paridade, Cotacao_Equivalencia; campos alterados: Valor_Encontro.*

*Lançamento contábil do encontro (revisão 23, D-N358; documento 114, Q114-1 a Q114-4). O encontro tem um lote só, com Origem_Tipo = encontro_contas: débito da obrigação a pagar, crédito do direito a receber e a perna de banco ou caixa com a diferença em dinheiro. As duas baixas de tipo encontro apontam esse mesmo lote. Em título em moeda, a variação cambial realizada entra em lote à parte (variacao_cambial), contra o banco, com a mesma taxa nas duas baixas. Exemplo do documento 114: a pagar de US\$ 100 contabilizado a 4,90 (R\$ 490), a receber de US\$ 80 a 5,10 (R\$ 408), taxa do encontro 5,00: o lote do encontro debita R\$ 490, credita R\$ 408 e R\$ 82 no banco; o lote da variação debita R\$ 10 e R\$ 8 de perda e credita R\$ 18 no banco; o banco recebe 82 + 18 = R\$ 100, igual a Valor_Diferenca, que é o que o extrato mostra. O desenho do lançamento da variação é a leitura do item 5 do documento 101 aplicada ao encontro, não está escrito linha a linha em outro documento. Retenção na fonte: ver Mov_Titulo_Retencao.ID_Baixa. Encontro entre participantes diferentes (Q113-8 e Q113-9) segue sem resposta: não aplicado.*

*O encontro de contas como operação inteira (revisão 22, D-N353; documento 111, Q111-9, Q111-11 e Q111-13). Mov_Titulo_Encontro_Contas é o agrupador: aponta os dois títulos e carrega a diferença em dinheiro com a conta de banco ou caixa; as duas baixas de tipo encontro (Mov_Titulo_Baixa.ID_Encontro) reduzem o saldo de cada título pelo valor dele. Exemplo: a pagar de US\$ 100 e a receber de US\$ 80 do mesmo não residente, câmbio R\$ 5,00: baixa do a pagar por US\$ 100 (R\$ 500), baixa do a receber por US\$ 80 (R\$ 400) e, no banco ou caixa, a diferença de US\$ 20 (R\$ 100, paga); o Y520 recebe pago R\$ 500 e recebido R\$ 400, e os R\$ 100 do banco já estão nos R\$ 500. A trava do período de fechamento vale para as duas baixas e para a perna de banco. Limite: encontro entre títulos de moedas diferentes não foi tratado; a diferença é em reais.*

*Confirmado por Alberto: encontro de contas exige o mesmo CNPJ
(ID_Participante idêntico dos dois lados) --- diferente do crédito de
bonificação (seção 4), que consolida por CNPJ_Raiz, aqui a exigência é o
participante exato, não a raiz. E, na prática, o valor raramente bate
exatamente zero a zero entre os dois títulos: \"a diferença
consequentemente vai para baixa contra banco\" --- ou seja, é comum um
título ter uma parte liquidada por encontro de contas e o restante
liquidado por uma baixa normal (seção 3), exatamente como a fórmula de
saldo em aberto (seção 2) já prevê ao somar as formas de
liquidação juntas (desde a revisão 22, a parte compensada entra pelas baixas de
tipo encontro). Que ID_Titulo_Pagar.ID_Participante seja igual a
ID_Titulo_Receber.ID_Participante não é garantido pela estrutura em si
--- fica, como outras validações deste dicionário, a critério da camada
de aplicação.*

6\. Limite de Crédito e Bloqueio por Grupo Econômico e CNPJ Raiz

O Documento Analítico define a régua: \"o limite de crédito de um
cliente é medido pela exposição total --- saldo a receber em aberto mais
o novo pedido --- e só se recompõe com o recebimento efetivo, nunca com
o simples faturamento. Quando o cliente pertence a um Grupo Econômico, o
bloqueio por inadimplência aplica-se ao grupo inteiro, não apenas ao
CNPJ em atraso, sem exigir consentimento prévio do cliente --- é uma
decisão interna de gestão de risco.\" Esta é a resposta ao gancho
deixado em aberto desde a Revisão 1 de CRM & Vendas (seção 10 daquele
documento).

Exposição_Total, por participante --- fórmula, sem campo/tabela própria:
soma do saldo em aberto (seção 2) de todo Mov_Titulo com Tipo=receber e
Status≠cancelado, mais o valor do novo pedido/cotação sendo avaliado em
CRM & Vendas. A propriedade \"só se recompõe com o recebimento efetivo,
nunca com o simples faturamento\" já é consequência direta do próprio
modelo: a nota fiscal de saída (faturamento) é o que FAZ NASCER o título
--- aumenta a exposição, não reduz; só uma baixa, uma aplicação de
crédito ou um encontro de contas (seções 3 a 5) reduzem o saldo em
aberto e, com ele, a exposição.

O teto contra o qual a Exposição_Total é comparada segue uma cascata de
três níveis, definida nesta revisão (2) a pedido de Alberto: (1) se o
participante pertence a um Grupo Econômico, consolida em
Cad_Grupo_Economico --- teto = Cad_Grupo_Economico.Limite_Credito quando
preenchido, exposição = soma de todos os participantes do grupo; (2) se
NÃO pertence a um Grupo Econômico, consolida por CNPJ_Raiz
(Cad_Participante.CNPJ_Raiz, Fase 0 revisão 17) --- teto = soma do
Limite_Credito de todas as Cad_Participante com a mesma raiz, exposição
= soma de todos os títulos em aberto de todas elas; (3) sem Grupo
Econômico nem outro participante com a mesma raiz, fica só no
Limite_Credito individual do próprio participante. Resposta de Alberto
sobre o nível 2: \"quando ele é colocado no raiz do CNPJ é propagado
para todos os CNPJs, e o limite se torna a soma dos CNPJs da raiz\" ---
ou seja, o valor de Limite_Credito é preenchido uma vez no participante
que é a matriz e propagado automaticamente para o Limite_Credito de cada
filial da mesma raiz; o teto consolidado do nível 2 é então a soma
desses valores propagados. Confirmado por Alberto (revisão 7): CNPJ_Raiz
(Fase 0, revisão 17) já está correto como os 8 primeiros caracteres do
CNPJ (\"caracteres\" desde a revisão 11 --- CNPJ alfanumérico, Fase 0
revisão 41); \"0001\" é a numeração que identifica a matriz dentro da
raiz --- convenção brasileira padrão. Revisão 5 (documento 50, D-N117):
o \"0001\" só indica a matriz na geração do CNPJ, e uma filial pode virar
matriz; por isso a matriz é identificada por
Cad_Participante.Indicador_Matriz, que nasce marcado quando a ordem é
0001, e não mais pelo sufixo. A propagação em si deixou de ser automática nesta revisão:
Cad_Participante.Propagar_Limite_Credito (Fase 0, revisão 24),
preenchido só na matriz, decide se ela propaga --- antes a estrutura
assumia propagação sempre ligada, sem esse controle explícito.

O bloqueio, quando a exposição ultrapassa o teto do nível aplicável,
dispara Mov_Aprovacao_Instancia (Fase 0) com Origem_Tipo=desvio_credito
--- valor já pré-registrado no Fase 0 desde antes deste módulo existir,
especificamente para este gatilho --- reaproveitando a mesma régua
(Cad_Regua_Aprovacao/Cad_Regua_Faixa) usada por todo o resto do
dicionário, sem estrutura de aprovação nova.

*Integração dentro de Mov_Cotacao_Venda (CRM & Vendas) --- resolvida num
patch posterior a este documento, junto da consolidação (Revisão 3) do
módulo Fase 2 Tesouraria, que trouxe um segundo gatilho de bloqueio
paralelo (a régua de cobrança, Origem_Tipo=bloqueio_regua_cobranca, Fase
0): o bloqueio (por desvio_credito ou por bloqueio_regua_cobranca) é
sempre avaliado e aplicado no nível de grupo econômico --- não
cascateando para CNPJ Raiz/individual como a configuração de
Limite_Credito acima permite ---, e o tratamento em tela depende do
canal de origem da cotação (atendimento por vendedor: a pendência é
mostrada a ele, para decidir; autoatendimento: a cotação entra em
análise, sem atendimento automático, sem expor o motivo ao próprio
cliente). Ver CRM & Vendas, seção 4, para o detalhe completo.*

7\. Reversão de Provisão de Comissão/Royalty em Obrigação a Pagar

CRM & Vendas já havia anunciado este exato mecanismo, com as palavras de
Alberto: \"esta estimativa deverá ser lançado na contabilidade como
provisão, e no momento do recebimento efetivo reverter provisão conta
obrigações a pagar, neste momento entra no financeiro.\" Esta seção é
onde isso finalmente ganha estrutura.

Quando um título a receber (Mov_Titulo, Tipo=receber,
Origem_Tipo=nota_fiscal_saida) vinculado a um pedido de venda com
comissão/royalty estimados é liquidado --- por baixa, aplicação de
crédito ou encontro de contas (seções 3 a 5) ---, dois eventos nascem
juntos: (1) um lançamento contábil que reverte a provisão original
(Mov_Lote_Lancamento.Origem_Tipo=reversao_provisao_comissao_venda, Fase
0, revertendo o lote que nasceu com Origem_Tipo=provisao_comissao_venda
no próprio pedido); e (2) um novo Mov_Titulo (Tipo=pagar) para cada
beneficiário --- Origem_Tipo=comissao_venda, ID_Origem=ID_Item_Comissao
de Mov_Pedido_Venda_Item_Comissao, um título por linha da escada --- e,
quando aplicável, Origem_Tipo=royalty_venda, ID_Origem=ID_Item de
Mov_Pedido_Venda_Item, para o licenciante.

*Confirmado por Alberto (revisão 7): a reversão/nascimento da obrigação
a pagar acontece PROPORCIONALMENTE a cada liquidação do título a
receber, não só na liquidação total --- ou seja, uma baixa parcial de
30% do valor do pedido gera, na mesma proporção, 30% da obrigação de
comissão/royalty daquele pedido, permitindo mais de um Mov_Titulo
(Tipo=pagar, mesma Origem_Tipo/ID_Origem) nascendo ao longo do tempo, um
por liquidação parcial recebida. Esta já era a assunção desenhada desde
a revisão original --- a confirmação fecha o ponto que ficava como
gancho no texto.*

O repasse financeiro efetivo desse novo título a pagar --- a um vendedor
autônomo/PJ ou ao licenciante, via baixa deste próprio módulo (seção 3);
a um vendedor com vínculo empregatício, via Folha & RH, ainda não
especificado --- continua fora do escopo: este módulo só garante que a
obrigação nasce corretamente estruturada, pronta para ser liquidada como
qualquer outro título a pagar.

8\. Reprogramação de Título

Nova nesta revisão (2), a pedido de Alberto: \"na baixa de um título,
pode ser baixado um valor parcial e reprogramada outra parte para
pagamento --- falta uma amarração de pagamento parcial e a parte que foi
reprogramada.\" Em vez de simplesmente editar Data_Vencimento do título
original (o que a Revisão 1 permitia, sem rastro do porquê da mudança),
o saldo restante depois de uma liquidação parcial agora pode ser
reprogramado para um ou mais NOVOS títulos, com vínculo explícito de
volta ao título e, quando houver, à baixa que motivou a reprogramação.
Alberto confirmou que o saldo pode ser parcelado em N títulos, não só um
--- o desenho segue o mesmo padrão cabeçalho+item já usado em outras
entidades deste dicionário (ex.: cotação e seus itens, em CRM & Vendas).

Mov_Titulo_Reprogramacao

O cabeçalho do evento de reprogramação --- qual título teve seu saldo
reprogramado, e por quê.

*Vigência: não --- é o registro de um evento.*

  ------------------------ -------------------- ----------------------------------------
  **Campo**                **Tipo lógico**      **Descrição / regra**

  **ID_Reprogramacao**     *identificador*      ---

  **ID_Titulo_Origem**     *referência          O título cujo saldo em aberto foi
                           (Mov_Titulo)*        reprogramado.

  **ID_Baixa**             *referência          A baixa parcial que motivou esta
                           (Mov_Titulo_Baixa,   reprogramação, quando houver --- permite
                           opcional)*           também reprogramação pura, sem nenhum
                                                pagamento, só renegociação de prazo.

  **Data_Reprogramacao**   *data*               ---
  ------------------------ -------------------- ----------------------------------------

Mov_Titulo_Reprogramacao_Item

Cada nova parcela nascida da reprogramação --- um evento de
reprogramação pode gerar mais de um novo título (parcelamento do saldo
reprogramado).

*Vigência: não --- é o registro de um evento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Reprogramacao** | *identificador* | --- |
| **ID_Reprogramacao** | *referência (Mov_Titulo_Reprogramacao)* | --- |
| **ID_Titulo_Novo** | *referência (Mov_Titulo)* | O novo título nascido desta parcela --- Origem_Tipo=reprogramacao (seção 2), com seu próprio Valor_Titulo e Data_Vencimento, definidos nesta reprogramação. |
| **Valor_Reprogramado** | *número* | O valor desta parcela específica --- deve bater com Valor_Titulo do título novo correspondente; a soma de todos os itens de uma mesma reprogramação reduz o saldo em aberto do título de origem (seção 2). Revisão 21 (D-N346, documento 101, seção 4.3): na moeda do título de origem. O título novo nasce com a mesma moeda, com Valor_Titulo_Moeda igual a este valor, e Valor_Titulo em reais é a estimativa pela Taxa_Estimada herdada do título de origem (Revisão 24, D-N360, Q101-1d; a revisão 21 dizia a taxa do dia da renegociação). |

*Revisão 21 --- campos alterados: Valor_Reprogramado.*

*Revisão 24 --- campos alterados: Valor_Reprogramado.*

Reclassificação de Prazo --- Curto Prazo / Longo Prazo

Nova nesta revisão (10), a pedido de Alberto durante a revisão geral de
módulos: \"item 9 não é só a Reprogramação que dispara tem a questão do
tempo, pois tudo que esta em longo prazo vai transitar para curto prazo,
pelo tempo que leva para chegar mais proximo do pagamento\" --- além da
Reprogramação (acima), que já podia mudar Data_Vencimento de um título,
a simples passagem do tempo também precisa mover um título de Longo
Prazo para Curto Prazo no plano de contas, mesmo sem nenhuma
reprogramação acontecer. A classificação em si NUNCA é armazenada --- é
sempre derivada, comparando Data_Vencimento contra a data de hoje mais
Cad_Empresa.Meses_Limite_Curto_Prazo (Fase 0, revisão 39, novo campo,
número de meses, por empresa, a pedido de Alberto: \"o numero de meses
para passar do longo prazo para curto teria que ser um parametro por
empresa\"): Data_Vencimento ≤ hoje + Meses_Limite_Curto_Prazo classifica
como curto prazo; caso contrário, longo prazo --- mesma filosofia de
\"nunca guardar o que pode ser derivado\" de todo o dicionário.

No nascimento do título (seção 2), o Motor de Regras (Fase 0) já
resolve, para o mesmo par conceitual de conta contábil (ex.:
Fornecedores, Clientes, Empréstimos a Pagar), duas contas gêmeas --- uma
de Curto Prazo e uma de Longo Prazo ---, escolhendo entre elas conforme
a classificação derivada acima, avaliada na Data_Emissao; o lançamento
da nota fiscal (Mov_Lote_Lancamento.Origem_Tipo=documento_fiscal) ou da
folha (Origem_Tipo=folha_pagamento) já nasce na conta correta, sem
estrutura nova aqui --- é só um novo critério de resolução dentro do
Motor de Regras já existente (Fase 0), não uma mudança estrutural neste
módulo.

Mov_Titulo_Reclassificacao_Prazo

O evento de mover o saldo de um título entre a conta de Curto Prazo e a
conta de Longo Prazo do mesmo par --- pela passagem do tempo (fechamento
periódico) ou por uma reprogramação que mudou Data_Vencimento (seção 8,
acima).

*Vigência: não --- é o registro de um evento; um título pode ter mais de
uma reclassificação ao longo da vida (ex.: nasce longo prazo, um ano
depois vira curto prazo conforme o tempo passa, sem nenhuma
reprogramação no meio).*

  -------------------------- ------------------------ ------------------------------------------
  **Campo**                  **Tipo lógico**          **Descrição / regra**

  **ID_Reclassificacao**     *identificador*          ---

  **ID_Titulo**              *referência              ---
                             (Mov_Titulo)*            

  **Data_Reclassificacao**   *data*                   ---

  **Direcao**                *enumeração              O sentido da transferência --- decide,
                             {longo_para_curto,       junto com o par de contas gêmeas resolvido
                             curto_para_longo}*       pelo Motor de Regras no nascimento do
                                                      título (acima), de qual conta para qual
                                                      conta o saldo é transferido.

  **Gatilho**                *enumeração              O que disparou esta reclassificação --- o
                             {fechamento_periodico,   varrimento mensal do bloco \"tesouraria\"
                             reprogramacao}*          (fechamento_periodico, abaixo) ou uma
                                                      mudança de Data_Vencimento via
                                                      Mov_Titulo_Reprogramacao (reprogramacao)
                                                      que também mudou a classificação.

  **ID_Lote**                *referência              O lançamento contábil da transferência ---
                             (Mov_Lote_Lancamento)*   Origem_Tipo=reclassificacao_prazo_titulo
                                                      (Fase 0, revisão 39): débito na conta de
                                                      origem, crédito na conta de destino, pelo
                                                      saldo em aberto do título na data da
                                                      reclassificação. Não altera Valor_Titulo
                                                      nem Data_Vencimento do título (seção 2)
                                                      --- o valor e o vencimento continuam os
                                                      mesmos; só a conta contábil onde o saldo
                                                      está classificado muda.
  -------------------------- ------------------------ ------------------------------------------

*Comportamento de aplicação (não é um campo novo de dados): aproveitando
o mesmo ciclo mensal do bloco \"tesouraria\" (seções 2 e 3, revisão 9)
--- no momento em que a competência de uma Filial é fechada
(Cad_Periodo_Fechamento_Filial, Bloco=\"tesouraria\"), antes de travar
novos lançamentos, o sistema varre todos os Mov_Titulo em aberto
(Status=aberto, saldo em aberto \> 0, seção 2) daquela Filial e
recalcula a classificação de cada um contra
Cad_Empresa.Meses_Limite_Curto_Prazo (via Cad_Filial → Cad_Empresa).
Quando a classificação recalculada diverge da classificação implícita no
lançamento mais recente já feito para aquele título --- o lançamento de
nascimento (acima) ou a reclassificação anterior mais recente, o que for
mais novo ---, nasce um novo Mov_Titulo_Reclassificacao_Prazo
(Gatilho=fechamento_periodico). Disparo adicional, fora do ciclo mensal:
quando a Reprogramação (acima) muda Data_Vencimento de um jeito que a
classificação também muda, a reclassificação dispara imediatamente
(Gatilho=reprogramacao), no mesmo momento da reprogramação, sem esperar
o próximo fechamento --- um título recém-reprogramado não fica com a
conta errada até o mês seguinte. Um título totalmente liquidado (saldo
em aberto = 0) sai do varrimento mensal --- mesmo critério de \"aberto\"
já usado no resto deste módulo (seção 2): a reclassificação só existe
enquanto o título ainda tem saldo pendente.*

9\. Eventos de Conta Financeira --- Rendimento, Perda e Tarifas

Nova na Revisão 2, a pedido de Alberto: uma conta de Aplicação rende
juros (receita financeira), que precisam ser registrados --- e,
dependendo do tipo de investimento, esse ganho tem tratamento próprio de
PIS/COFINS (SPED Contribuições). Da mesma forma, uma conta de
Banco/Aplicação sofre taxas (tarifas, TED, DOC, manutenção, IOF), que
também precisam ser lançadas. Alberto confirmou fundir os dois num único
motor --- mesmo espírito de Mov_Titulo (seção 2): um evento acessório
direto na conta, fora do fluxo normal de baixa de título.

Nesta Revisão 3, Alberto apontou um gap: faltava identificar o que é o
evento --- rendimento de aplicação, PERDA em aplicação, tarifas, taxa de
administração, entre outros. \"Perda\" não cabia no Tipo{rendimento,
taxa} anterior --- é resultado negativo de mercado, não uma cobrança
bancária como taxa. Correção: Tipo vira puramente ESTRUTURAL ---
{credito, debito}, só decide o sinal do lançamento contra a conta --- e
a classificação do que é o evento passa para um único campo novo,
ID_Tipo_Evento, substituindo o ID_Tipo_Detalhe de referência dupla
condicional da Revisão 2 (que não tinha espaço para \"perda\" nem era
facilmente extensível).

Mov_Conta_Contabil_Evento

Um evento financeiro lançado direto numa conta de banco/aplicação ---
crédito (ex.: rendimento) ou débito (ex.: perda, tarifa, taxa de
administração) --- sem passar pelo fluxo normal de título e baixa.

*Vigência: não --- é o registro de um evento.*

  ----------------------- -------------------------------- -------------------------------------------
  **Campo**               **Tipo lógico**                  **Descrição / regra**

  **ID_Evento**           *identificador*                  ---

  **ID_Conta_Contabil**   *referência (Cad_Conta_Contabil, A conta que sofreu o evento ---
                          ID_Tipo_Conta =                  rendimento/perda só se aplicam a contas do
                          Banco/Aplicação)*                tipo Aplicação
                                                           (Cad_Conta_Contabil.ID_Tipo_Investimento,
                                                           Fase 0 revisão 17); tarifa/taxa de
                                                           administração se aplicam a Banco ou
                                                           Aplicação.

  **Tipo**                *enumeração {credito, debito}*   Renomeado nesta revisão (3) de {rendimento,
                                                           taxa} para ser puramente ESTRUTURAL --- só
                                                           decide o sinal do lançamento contra a conta
                                                           (rendimento é crédito; perda, tarifa e taxa
                                                           de administração são débito). A natureza do
                                                           evento em si passou para ID_Tipo_Evento,
                                                           abaixo --- mesmo motor, direção diferente,
                                                           mesmo padrão de Mov_Titulo.

  **ID_Tipo_Evento**      *referência (Cad_Classe_Sistema, Adicionado nesta revisão (3), substituindo
                          domínio =                        o ID_Tipo_Detalhe da Revisão 2: classifica
                          tipo_evento_conta_financeira)*   o que é o evento --- rendimento de
                                                           aplicação, perda em aplicação, tarifa
                                                           bancária, taxa de administração, TED, DOC,
                                                           boleto, IOF, outro. Domínio único e aberto
                                                           (Fase 0, revisão 18) --- um novo tipo de
                                                           evento é um novo valor aqui, sem precisar
                                                           de referência condicional a mais de um
                                                           domínio.

  **Data_Evento**         *data*                           ---

  **Valor_Evento**        *número*                         O valor do rendimento apurado, da perda
                                                           apurada, ou da tarifa/taxa cobrada ---
                                                           sempre positivo; o sinal do lançamento vem
                                                           de Tipo, não do valor.

  **ID_Baixa**            *referência (Mov_Titulo_Baixa,   Preenchido só quando Tipo=debito e o evento
                          opcional)*                       está amarrado a um pagamento específico
                                                           (ex.: tarifa de TED cobrada por aquela
                                                           baixa); vazio quando é um evento periódico
                                                           sem transação associada (ex.: manutenção
                                                           mensal, rendimento apurado no período) ou
                                                           quando Tipo=credito.

  **ID_Lote**             *referência                      O lançamento contábil do evento ---
                          (Mov_Lote_Lancamento, opcional)* Origem_Tipo=rendimento_financeiro ou
                                                           taxa_bancaria conforme a natureza do evento
                                                           (Fase 0, revisão 17).
  ----------------------- -------------------------------- -------------------------------------------

*Cad_Conta_Contabil.ID_Tipo_Investimento (Fase 0, revisão 17 ---
classifica a própria conta: CDB, fundo de renda fixa, LCI/LCA,
poupança\...) não muda nesta revisão --- é propriedade da CONTA, não do
evento; permanece a base para decidir o tratamento fiscal do rendimento
apurado nela.*

*O tratamento fiscal do rendimento (se aquele tipo de investimento é
tributado por PIS/COFINS, a que alíquota, em que regime) NÃO é calculado
aqui --- este módulo só garante que o rendimento nasce registrado com
valor, data e o tipo de investimento associado à conta. Corrigido nesta
revisão (8), decorrente da revisão geral de módulos pedida por Alberto
(\"sim rendimentos tem a contra partida em despesa ou receitas
financeiras, e tem que ser apurados separamente e parte destes
rendimentos tem que serem tributados\"): esta nota ainda apontava para
uma \"futura Contabilidade & Fiscal, ainda não especificada\" --- aquele
módulo já foi construído e já cobre exatamente este ponto (Fase 2 ---
Contabilidade & Fiscal, seção 12, PIS/COFINS sobre Rendimento
Financeiro): Mov_Apuracao_Tributo_Item,
Origem_Tipo=evento_conta_financeira, ID_Item_Origem=ID_Evento (acima),
apura o tributo separadamente por evento, com Gera_Credito=falso (regime
cumulativo) e desligamento automático quando o cronograma de transição
extinguir PIS/COFINS (Cad_Calendario_Transicao, parâmetro
fase_transicao, Fase 2 --- Contabilidade & Fiscal, seção 2). A contrapartida contábil do rendimento
em si (crédito na conta de Aplicação, débito ou crédito de resultado
financeiro conforme a natureza do evento) já é resolvida pelo Motor de
Regras no próprio Mov_Lote_Lancamento
(Origem_Tipo=rendimento_financeiro, ID_Lote acima) --- nenhuma estrutura
nova, só a referência cruzada que faltava.*

10\. Empréstimos Bancários

Novo na Revisão 3, a pedido de Alberto: assim como o módulo já cobre
aplicação financeira (dinheiro sobrando investido), falta o lado oposto
--- EMPRÉSTIMOS BANCÁRIOS, quando falta dinheiro e a empresa recorre a
banco. Dois exemplos dados por Alberto: hot money (empréstimo curto) e
empréstimo mais longo (financiamento/capital de giro) --- mesma
estrutura para os dois, a diferença é só classificação
(ID_Tipo_Emprestimo) e quantidade de parcelas. Reaproveita ao máximo o
motor já existente: o pagamento das parcelas de um empréstimo nasce e é
liquidado exatamente como qualquer outro título a pagar (seções 2 e 3),
mesmo padrão cabeçalho+parcela já usado para o pedido de compra e o
pedido de venda. Nesta Revisão 4, Alberto apontou que faltavam a taxa de
juros do contrato e os demais dados para calcular as parcelas --- o
cabeçalho ganhou cinco novos campos, abaixo.

Mov_Emprestimo

O cabeçalho da contratação de um empréstimo bancário --- inclui as
condições contratuais (taxa, indexador, sistema de amortização), para
referência e auditoria.

*Vigência: não --- é o registro de um evento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Emprestimo** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | A filial contratante. |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco/Caixa/Aplicação)* | Ampliado nesta revisão (7) --- antes só Banco: confirmado que o valor contratado também pode cair direto numa conta de Aplicação, mesmo padrão já usado em Mov_Titulo_Baixa (seção 3). |
| **ID_Tipo_Emprestimo** | *referência (Cad_Classe_Sistema, domínio = tipo_emprestimo)* | Classifica o empréstimo --- hot_money, capital_giro, financiamento_longo_prazo, outro. Domínio aberto (Fase 0, revisão 18). Hot money e empréstimo mais longo usam a mesma estrutura; só mudam a classificação e, na prática, quantas parcelas nascem (tipicamente 1 para hot money, N para financiamento mais longo). |
| **Data_Contratacao** | *data* | --- |
| **Valor_Contratado** | *número* | O valor recebido na contratação --- explícito, fidelidade ao valor real. |
| **Taxa_Juros** | *número* | Adicionado nesta revisão (4), a pedido de Alberto: a taxa contratada, explícita --- dado do contrato, para referência/auditoria. |
| **Periodicidade_Taxa** | *enumeração {mensal, anual}* | Adicionado nesta revisão (4): se Taxa_Juros é expressa ao mês (a.m.) ou ao ano (a.a.) --- necessário para interpretar corretamente a taxa contratada. |
| **ID_Indexador** | *referência (Cad_Classe_Sistema, domínio = tipo_indexador_financeiro, opcional)* | Adicionado nesta revisão (4): preenchido quando o empréstimo é pós-fixado (Taxa_Juros é um spread sobre um indexador --- CDI, IPCA, SELIC) e vazio quando é prefixado (taxa fixa, sem indexador). Domínio aberto (Fase 0, revisão 19). |
| **Sistema_Amortizacao** | *enumeração {SAC, Price, Bullet, outro}* | Adicionado nesta revisão (4): o sistema usado para calcular as parcelas --- Bullet (parcela única, principal e juros só no vencimento) é o caso típico de hot money; SAC e Price são os sistemas usuais de financiamento de prazo mais longo. |
| **Numero_Parcelas_Contratadas** | *número* | Adicionado nesta revisão (4): a quantidade total de parcelas pactuada no contrato --- dado do contrato, não necessariamente igual à contagem de Mov_Emprestimo_Parcela já lançadas (ex.: se o empréstimo for renegociado antes de todas as parcelas nascerem). |
| **ID_Lote** | *referência (Mov_Lote_Lancamento, opcional)* | O lançamento contábil do valor recebido --- Origem_Tipo=emprestimo (Fase 0, revisão 18): crédito na conta banco, contrapartida como obrigação (passivo). |
| **ID_Participante_Credor** | *referência (Cad_Participante), opcional* | Revisão 38 (documento 200, seção 5.3; D-N533 e D-N534: Q200-3): O banco, o fundo ou o investidor que emprestou. É por ele que o Motor sabe se o credor está em regime específico. Aviso quando vazio num empréstimo com parcela paga. |
| **Forma_Captacao** | *enumeração {operacao_credito, titulo_divida, titulo_divida_oferta_publica}* | Revisão 38 (documento 200, seção 5.3; D-N533 e D-N534: Q200-3): Operação de crédito (padrão), título de dívida (debênture, nota comercial) ou título de dívida com oferta pública regulada pela CVM, caso em que o emissor não toma crédito (LC 214, art. 195, § 1º, II). Novos tipos de título entram em ID_Tipo_Emprestimo (domínio aberto). |
| **Referenciado_Moeda_Estrangeira** | *booleano* | Revisão 38 (documento 200, seção 5.3; D-N533 e D-N534: Q200-3): Operação ou título referenciado em moeda estrangeira: não dá crédito de juros (LC 214, art. 197, II). Padrão falso. |

*Revisão 38 --- campos novos: ID_Participante_Credor, Forma_Captacao, Referenciado_Moeda_Estrangeira.*

*Taxa_Juros, Periodicidade_Taxa, ID_Indexador, Sistema_Amortizacao e
Numero_Parcelas_Contratadas documentam o CONTRATO, para referência e
auditoria --- mesma filosofia de \"fidelidade ao valor real, nunca
recalcular\" de todo o dicionário. Este módulo não vira uma calculadora
financeira que deriva
Mov_Emprestimo_Parcela.Valor_Principal_Previsto/Valor_Juros_Previsto a
partir desses campos: os valores de cada parcela continuam sendo o dado
fiel usado para gerar o título a pagar, calculados fora deste módulo (ou
pela camada de aplicação, aplicando a taxa e o sistema de amortização
contratados) e só registrados aqui.*

Mov_Emprestimo_Parcela

Cada parcela prevista de pagamento do empréstimo --- principal e juros
separados, por questão contábil e de apuração do que é despesa
financeira, conforme pedido explícito de Alberto.

*Vigência: não --- é o registro de um evento.*

  ------------------------------ ------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**     **Descrição / regra**

  **ID_Parcela_Emprestimo**      *identificador*     ---

  **ID_Emprestimo**              *referência         ---
                                 (Mov_Emprestimo)*   

  **Numero_Parcela**             *número*            A ordem desta parcela dentro do
                                                     empréstimo --- 1 (parcela única) no caso
                                                     típico de hot money.

  **Data_Vencimento_Prevista**   *data*              ---

  **Valor_Principal_Previsto**   *número*            A parte de amortização do passivo nesta
                                                     parcela.

  **Valor_Juros_Previsto**       *número*            A parte de despesa financeira nesta
                                                     parcela. A soma de
                                                     Valor_Principal_Previsto +
                                                     Valor_Juros_Previsto é o valor total da
                                                     parcela --- o mesmo valor que vira
                                                     Mov_Titulo.Valor_Titulo quando esta
                                                     parcela gera o título a pagar (seção 2).
  ------------------------------ ------------------- ----------------------------------------

*O título a pagar de cada parcela (Mov_Titulo, Tipo=pagar,
Origem_Tipo=emprestimo, ID_Parcela_Origem apontando para esta
Mov_Emprestimo_Parcela) representa só o valor TOTAL a pagar e quando ---
ele não separa principal de juros. A separação para fins contábeis
(amortização de passivo vs. despesa financeira) é feita consultando a
Mov_Emprestimo_Parcela de origem no momento de gerar o lançamento
contábil da baixa (seção 3) --- mesmo padrão já usado para outras
origens de título que carregam detalhe que o título em si não guarda
diretamente (ex.: comissão/royalty, seção 7).*

11\. Aprovação --- Camada Extra de Caixa

O Documento Analítico (seção de Planejamento & Orçamento) já mencionava
uma camada extra de aprovação de caixa acima do limite do gestor --- e o
Fase 0 já pré-registrava
Mov_Aprovacao_Instancia.Origem_Tipo=camada_caixa desde antes deste
módulo existir, sem nenhum gatilho real até agora. Este documento
conecta esse gatilho: uma baixa de pagamento (Mov_Titulo_Baixa,
Tipo=pagar via Mov_Titulo) cujo Valor_Baixado cai numa faixa que exige
aprovação extra (Cad_Regua_Faixa, mesma régua reaproveitada em todo o
dicionário) preenche Mov_Titulo_Baixa.ID_Instancia_Aprovacao antes de a
baixa ser efetivada.

*Resolvido nesta revisão (7): o gatilho por BAIXA INDIVIDUAL continua
existindo (um pagamento isolado acima da alçada gera sua própria
Mov_Aprovacao_Instancia), mas a camada de caixa agora também suporta o
caso AGREGADO --- várias baixas aprovadas de uma vez, sob uma única
decisão --- via a nova Mov_Aprovacao_Lote (Fase 0, revisão 24, seção 9):
quando o fluxo de aprovação for por lote, cada Mov_Aprovacao_Instancia
gerada para as baixas daquele agrupamento preenche o mesmo
ID_Lote_Aprovacao; a decisão pode então ser tomada sobre o lote inteiro,
em vez de uma instância de cada vez. Os dois modos (individual e
agregado) coexistem na estrutura; qual deles a Mlegate usa em cada fluxo
é decisão de configuração/camada de aplicação.*

12\. Como este módulo se conecta com a Fase 0, Compras e CRM & Vendas

Referência rápida do que este módulo consome --- nunca redescrito aqui,
só referenciado por chave estrangeira.

  ------------------------------------------------------------------ -------------------------------------------------------- ---------------------------
  **Entidade referenciada**                                          **Como este módulo usa**                                 **Observação**

  **Cad_Participante (+ Cad_Participante_Classe)**                   O fornecedor ou cliente do título/crédito --- a mesma    *Mesmo cadastro único do
                                                                     classe dupla (cliente e fornecedor) é a base do encontro Fase 0*
                                                                     de contas (seção 5).                                     

  **Cad_Participante.Limite_Credito / CNPJ_Raiz /                    O teto e o agrupamento usados na cascata de crédito      *Fase 0, revisões 16, 17 e
  Propagar_Limite_Credito / Cad_Grupo_Economico.Limite_Credito**     (seção 6) e na aplicação de crédito não-financeiro entre 24*
                                                                     filiais (seção 4).                                       

  **Cad_Grupo_Economico (+ Cad_Grupo_Economico_Membro)**             Consolida a exposição de crédito entre participantes do  *Fase 0*
                                                                     mesmo grupo --- nível 1 da cascata (seção 6).            

  **Cad_Filial**                                                     A filial de origem do título/crédito (herda a nota       *---*
                                                                     fiscal ou o lançamento avulso).                          

  **Cad_Conta_Contabil (ID_Tipo_Conta = Banco/Caixa/Aplicação;       A conta de onde sai ou para onde entra o valor de uma    *Fase 0 --- estrutura já
  ID_Tipo_Investimento)**                                            baixa, de um crédito, de um evento de conta financeira,  preparada desde a
                                                                     ou de uma contratação de empréstimo (seções 3, 4, 9 e    especificação original;
                                                                     10).                                                     ID_Tipo_Investimento na
                                                                                                                              revisão 17*

  **Cad_Classe_Sistema (domínios tipo_investimento_financeiro,       Classifica o tipo de investimento da conta (seção 3), a  *Fase 0, revisões 17, 18 e
  tipo_credito_adiantamento, tipo_evento_conta_financeira,           origem do crédito não-financeiro (seção 4), o evento de  19*
  tipo_emprestimo, tipo_indexador_financeiro)**                      conta financeira --- rendimento/perda/tarifa (seção 9)   
                                                                     ---, o tipo de empréstimo e o indexador do empréstimo    
                                                                     pós-fixado (seção 10).                                   

  **Cad_Regua_Aprovacao (+ Mov_Aprovacao_Instancia,                  Aprova a camada extra de caixa numa baixa de pagamento,  *Origem_Tipo=camada_caixa e
  Mov_Aprovacao_Lote)**                                              individual ou em lote (seção 11); fórmula pronta para o  desvio_credito;
                                                                     bloqueio por desvio de crédito (seção 6), já integrada   Mov_Aprovacao_Lote, Fase 0
                                                                     em CRM & Vendas.                                         revisão 24*

  **Mov_Lote_Lancamento / Mov_Lancamento**                           O lançamento contábil da baixa, da reversão de provisão, *Fase 0, revisões 16, 17 e
                                                                     da reprogramação (quando existir), do evento de conta    18*
                                                                     financeira e da contratação de empréstimo.               

  **Mov_Nota_Fiscal_Entrada (Compras)**                              A nota fiscal de entrada --- o evento que faz nascer um  *---*
                                                                     título Tipo=pagar.                                       

  **Mov_Nota_Fiscal_Saida (CRM & Vendas)**                           A nota fiscal de saída --- o evento que faz nascer um    *---*
                                                                     título Tipo=receber.                                     

  **Mov_Pedido_Parcela (Compras)**                                   Fonte de Valor_Titulo/Data_Vencimento reais de um título *Compras, revisão 6*
                                                                     Tipo=pagar, quando a nota tem pedido parcelado de        
                                                                     origem.                                                  

  **Mov_Pedido_Venda_Parcela (CRM & Vendas)**                        Fonte de Valor_Titulo/Data_Vencimento reais de um título *CRM & Vendas, revisão 1*
                                                                     Tipo=receber, quando a nota tem pedido parcelado de      
                                                                     origem.                                                  

  **Mov_Pedido_Venda_Item_Comissao / Mov_Pedido_Venda_Item (CRM &    Origem do novo título Tipo=pagar de comissão/royalty,    *CRM & Vendas, revisão 2 e
  Vendas)**                                                          nascido na reversão da provisão (seção 7).               3*

  **Mov_Rh_Folha_Apuracao / Mov_Rh_Folha_Item (Fase 5 --- Folha &    Adicionado nesta revisão (8): origem do novo título      *Fase 5, revisão 5 ---
  RH)**                                                              Tipo=pagar de folha_pagamento (seção 2) --- um           construído nesta
                                                                     Mov_Titulo por Natureza_Titulo_Folha dentro de cada      consolidação*
                                                                     apuração de folha liquidada, incluindo rescisão (com o   
                                                                     beneficiário do óbito resolvido via                      
                                                                     Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito   
                                                                     quando aplicável).                                       

  **Mov_Remessa_Bancaria_Item (Fase 2 --- Tesouraria)**              A baixa de um título folha_pagamento passa pelo mesmo    *Fase 2 --- Tesouraria,
                                                                     mecanismo de remessa bancária já usado para fornecedor   revisão 5 --- construído
                                                                     (seção 3, Origem_Tipo=automatica_cnab) --- sem estrutura nesta consolidação*
                                                                     nova aqui, a diferenciação de tipo de serviço de lote    
                                                                     (salário x tributo) e de tipo de conta do favorecido     
                                                                     (conta-salário x corrente) fica inteiramente do lado da  
                                                                     Tesouraria.                                              

  **Cad_Bloco_Fechamento / Cad_Periodo_Fechamento /                  Adicionado nesta revisão (9): trava a criação/alteração  *Fase 0, seção 10, revisão
  Cad_Periodo_Fechamento_Filial (Bloco=\"tesouraria\")**             de Mov_Titulo (seção 2) e de Mov_Titulo_Baixa (seção 3)  37 --- construído nesta
                                                                     por Filial+competência --- o mesmo bloco de fechamento   consolidação*
                                                                     que trava a execução do pagamento no documento de Fase 2 
                                                                     Tesouraria, um único bloco estendendo-se sobre os dois   
                                                                     documentos; a partir desta revisão (10) é também o       
                                                                     gatilho do varrimento mensal de Reclassificação de Prazo 
                                                                     (seção 8).                                               

  **Cad_Empresa.Meses_Limite_Curto_Prazo**                           Adicionado nesta revisão (10): o parâmetro, por empresa, *Fase 0, revisão 39*
                                                                     que decide a fronteira entre Curto e Longo Prazo usada   
                                                                     pela Reclassificação de Prazo (seção 8).                 

  **Mov_Lote_Lancamento.Origem_Tipo=reclassificacao_prazo_titulo**   Adicionado nesta revisão (10): o lançamento contábil de  *Fase 0, revisão 39*
                                                                     cada Mov_Titulo_Reclassificacao_Prazo (seção 8).         

  **Mov_Esocial_Retorno_Cr (Folha & RH)**                            Origem do título de INSS e de IRRF (Origem_Tipo =        *Folha & RH, revisão 18*
                                                                     esocial_retorno_cr), que nasce com a reversão da
                                                                     provisão da folha.

  **Mov_Dctfweb_Darf e Mov_Dctfweb_Darf_Item (Contabilidade &        Origem do título do DARF para débitos sem título         *Contabilidade & Fiscal,
  Fiscal)**                                                          anterior, e o vínculo dos itens do DARF com os títulos   revisão 19*
                                                                     que eles quitam.

  **Mov_Retencao_Consolidacao (Contabilidade & Fiscal)**             Origem do título único das retenções consolidadas pelo   *Contabilidade & Fiscal,
                                                                     operador.                                                revisão 19*
  ------------------------------------------------------------------ -------------------------------------------------------- ---------------------------

13\. Notas para a sua revisão

Mesma lógica dos documentos anteriores: estas são decisões técnicas que
assumi por conta própria para fechar uma estrutura concreta --- nenhuma
está travada.

-   Este é o primeiro módulo desta leva que coincide com a Fase original
    do Documento Analítico (Fase 2) --- ver seção 1. Diferente de CRM &
    Vendas, não há divergência de fase para sinalizar aqui.

-   Mov_Titulo unificado (Tipo=pagar/receber numa única entidade) e
    Mov_Conta_Contabil_Evento unificado (Tipo=credito/debito numa única
    entidade, desde a revisão 2 e reclassificado nesta revisão 3) seguem
    o mesmo princípio: um único motor, direção diferente --- ao pé da
    letra da frase do Documento Analítico sobre Mov_Titulo, estendida
    por analogia ao rendimento/perda/taxa a pedido de Alberto.

-   ID_Parcela_Origem (Mov_Titulo, seção 2) assume que cada nota fiscal
    com pedido de origem mapeia suas parcelas 1:1 com as parcelas já
    negociadas no pedido --- um cenário de faturamento parcial em várias
    notas, cada uma cobrindo uma fração diferente das parcelas originais
    do pedido, não foi modelado com precisão; fica como ponto de atenção
    para sua confirmação.

-   Mov_Titulo.Status foi modelado como {aberto, cancelado} apenas, com
    baixado parcial/total sempre derivado (seção 2) --- mesma filosofia
    de \"saldo nunca armazenado\" já usada em outros pontos do
    dicionário. Se a Mlegate preferir um campo de status materializado
    para performance de relatório, é uma otimização de implementação,
    não uma mudança de modelo conceitual.

-   Mov_Titulo_Baixa continua modelado como sempre 1:1 com um único
    título --- pagamento de múltiplos títulos numa única remessa
    bancária não é modelado: cada título liquidado nessa remessa gera
    sua própria linha de Mov_Titulo_Baixa, sem um agrupador estrutural
    entre elas. Se precisar rastrear o agrupamento, é uma extensão
    futura.

-   Mov_Credito (renomeado nesta revisão 3, ex-Mov_Adiantamento) continua usando
    Mov_Lote_Lancamento.Origem_Tipo=outro, diferente da baixa, da
    reversão de provisão, da reprogramação, do evento de conta
    financeira e do empréstimo, que ganharam Origem_Tipo dedicado ---
    não abri um valor próprio para crédito por não ter sido citado com o
    mesmo nível de detalhe contábil; se a Mlegate quiser rastreá-lo
    separadamente nos relatórios contábeis, é uma pequena extensão do
    domínio (Fase 0), mesmo padrão já usado nas demais origens. O encontro
    de contas, que na revisão 22 ainda usava outro, ganhou na revisão 23
    (D-N358, documento 114, Q114-3) o valor próprio encontro_contas.

-   Limite_Credito (Cad_Participante e Cad_Grupo_Economico, Fase 0)
    continua modelado como um valor único e fixo, sem vigência própria
    nem histórico de mudança --- se a Mlegate precisar registrar quando
    e por quem um limite foi alterado, é uma extensão futura no mesmo
    padrão de tabela de histórico já usado em outros cadastros deste
    dicionário.

-   A propagação de Limite_Credito da matriz para as filiais da mesma
    raiz (seção 6) passou a ser condicional, nesta revisão (7), ao novo
    Cad_Participante.Propagar_Limite_Credito (Fase 0, revisão 24) ---
    preenchido só na matriz; a estrutura ainda não impede, por si só,
    que uma filial tenha seu próprio Limite_Credito preenchido
    manualmente e diferente do propagado, isso continua validação de
    camada de aplicação. A convenção de \"participante que é a raiz\"
    (CNPJ terminado em 0001) e a nomenclatura de CNPJ_Raiz foram
    confirmadas por Alberto nesta revisão. Revisão 5 (documento 50,
    D-N117): a matriz passa a ser o participante com
    Cad_Participante.Indicador_Matriz verdadeiro, e não o que termina
    em 0001.

-   O gatilho de desvio_credito (seção 6) foi integrado de fato dentro
    de Mov_Cotacao_Venda (CRM & Vendas) num patch posterior a este
    documento --- ver seção 6.

-   Mov_Titulo_Baixa.Origem_Tipo/Data_Recebimento_Cnab/ID_Participante_Baixa
    (seção 3, revisão 5) foram acrescentados como patch pontual pedido
    pela consolidação do módulo Fase 2 Tesouraria; nenhuma outra
    estrutura deste documento mudou naquela revisão.

-   A reversão de provisão proporcional a cada liquidação parcial
    (seção 7) foi confirmada por Alberto nesta revisão (7) --- deixou de
    ser suposição.

-   Camada extra de caixa (seção 11) passou a suportar também o caso
    agregado nesta revisão (7), via Mov_Aprovacao_Lote (Fase 0,
    revisão 24) --- ver seção 11.

-   Retenções fiscais na baixa (IRRF, PIS/COFINS/CSLL retidos na fonte
    sobre serviço, por exemplo) não foram modeladas --- dependem de
    Contabilidade & Fiscal, ainda não especificado; Valor_Baixado
    (Mov_Titulo_Baixa) assume, por ora, que representa o valor líquido
    efetivamente movimentado pela conta bancária, sem um campo próprio
    para o valor de retenção.

-   Mov_Titulo_Reprogramacao_Item (seção 8) assume que a soma de
    Valor_Reprogramado de todos os itens de uma mesma reprogramação
    sempre fecha exatamente o valor reprogramado do título de origem ---
    não é uma restrição garantida pela estrutura em si, fica como
    validação de camada de aplicação, mesmo padrão já usado em outros
    pontos deste dicionário.

-   Mov_Credito.Contabiliza_Na_Inclusao (seção 4, revisão 7) fechou o
    ponto que ficava aberto sobre o saldo de um crédito vencido: por
    padrão (false) a expiração continua silenciosa, como já modelado;
    com o booleano true, o saldo não aplicado é baixado como perda no
    vencimento.

-   Mov_Conta_Contabil_Evento (seção 9), mesmo com Tipo já puramente
    estrutural nesta revisão 3, não impede por si só que alguém preencha
    Valor_Evento negativo ou associe um ID_Tipo_Evento inconsistente com
    Tipo (ex.: \"perda_aplicacao\" com Tipo=credito) --- fica, como em
    outros pontos deste dicionário, como validação de camada de
    aplicação.

-   Mov_Emprestimo.ID_Conta_Contabil (seção 10) passou a aceitar
    Banco/Caixa/Aplicação nesta revisão (7), não só Banco --- mesmo
    padrão já usado em Mov_Titulo_Baixa. Garantias, covenants e demais
    cláusulas contratuais do empréstimo continuam não modeladas --- fora
    do escopo deste dicionário de dados.

-   Mov_Emprestimo.Numero_Parcelas_Contratadas (seção 10, revisão 4) não
    é garantido pela estrutura em si a bater com a contagem real de
    Mov_Emprestimo_Parcela --- um empréstimo renegociado no meio do
    caminho pode ter menos ou mais parcelas nascidas do que o
    originalmente contratado; fica como validação de camada de
    aplicação, se a Mlegate quiser alertar sobre essa divergência.

-   Sistema_Amortizacao, Taxa_Juros, Periodicidade_Taxa e ID_Indexador
    (Mov_Emprestimo, seção 10, revisão 4) são só DESCRITIVOS --- a
    estrutura não deriva nem confere se o
    Valor_Principal_Previsto/Valor_Juros_Previsto de cada
    Mov_Emprestimo_Parcela realmente corresponde ao que esses campos,
    aplicados, produziriam. Se a Mlegate quiser essa conferência
    automática, é uma extensão futura (uma calculadora de amortização),
    fora do escopo deste dicionário de dados.

-   Revisão 7 (ciclo \"consolidar\") fechou cinco pontos que ficavam em
    aberto e trouxe um patch cross-módulo: Mov_Titulo_Baixa.Canal_Split
    (seção 3), pedido pela consolidação da Fase 2 Contabilidade &
    Fiscal, ao lado do já existente Valor_Tributo_Split.

-   Revisão 8 --- Origem_Tipo=folha_pagamento/Natureza_Titulo_Folha
    (seção 2) assume que a folha entrega um valor JÁ CONSOLIDADO por
    natureza (todo o INSS da apuração num título, todo o FGTS noutro)
    --- não um título por colaborador por verba. Se a Mlegate precisar
    de rastreabilidade por colaborador dentro do título de INSS/FGTS
    consolidado, por exemplo para conciliar com a guia de recolhimento,
    essa quebra deriva de uma consulta juntando o título com os
    Mov_Rh_Folha_Item da mesma apuração e natureza (Fase 5), sem exigir
    um título por colaborador.

-   Revisão 8 --- o texto do Documento Analítico/Revisão 1 (\"o repasse
    financeiro efetivo de comissão/royalty a um beneficiário com vínculo
    empregatício depende de Folha & RH\", seção 1) permanece um gancho
    em aberto: esta revisão conecta Folha & RH a Contas a Pagar/Receber
    para o PRÓPRIO pagamento da folha, mas não resolve o caso de uma
    comissão de venda (seção 7) paga a alguém que também é colaborador
    via o mesmo Mov_Titulo de folha --- os dois fluxos continuam
    paralelos, sem fusão nesta revisão.

-   Revisão 9 --- Mov_Titulo e Mov_Titulo_Baixa passam a respeitar o
    bloco de fechamento \"tesouraria\" (Fase 0, seção 10, revisão 37), o
    mesmo bloco que trava a execução do pagamento no documento de Fase 2
    Tesouraria (revisão 6 daquele documento, mesma consolidação) ---
    nenhum campo novo, só o comportamento de aplicação descrito nas
    seções 2 e 3. Por simetria com Compras (o único bloco com checagem
    de pendência no fechamento), este bloco não verifica pendência
    nenhuma: título em aberto aguardando vencimento/baixa é o estado
    normal, não um impeditivo para fechar a competência de entrada.

-   Revisão 9 --- a competência de Mov_Titulo é derivada de Data_Emissao
    e a de Mov_Titulo_Baixa é derivada de Data_Baixa (seções 2 e 3) ---
    as duas podem cair em meses diferentes para o mesmo título (título
    nasce num mês, baixa acontece noutro), cada uma validada contra o
    período fechado da SUA PRÓPRIA data, não da data do título de
    origem; suposição razoável, não confirmada literalmente por Alberto
    neste nível de detalhe, fica como ponto de atenção.

-   Revisão 10 --- Mov_Titulo_Reclassificacao_Prazo (seção 8) assume que
    o par de contas Curto Prazo/Longo Prazo já existe cadastrado
    (Cad_Conta_Contabil) para cada conta que o Motor de Regras hoje
    resolve de forma única (ex.: uma única conta \"Fornecedores\") ---
    cadastrar essas contas gêmeas é trabalho de implantação/plano de
    contas, fora do escopo deste dicionário de dados, mesmo padrão de
    outras contas resolvidas pelo Motor de Regras em todo o dicionário.

-   Revisão 10 --- o varrimento mensal de Reclassificação de Prazo
    (seção 8) roda por Filial, no momento do fechamento do bloco
    \"tesouraria\" daquela Filial; assume-se que todas as Filiais da
    mesma Empresa fecham essa competência num ritmo próximo o bastante
    para que o parâmetro único Cad_Empresa.Meses_Limite_Curto_Prazo
    continue fazendo sentido --- se a Mlegate tiver Filiais com
    calendários de fechamento muito divergentes entre si, é um ponto de
    atenção para a implantação, não uma mudança de modelo.

-   Revisão 10 --- fechadas duas referências cruzadas que ficavam como
    gancho: o tratamento fiscal do rendimento financeiro (seção 9), que
    já está coberto por Contabilidade & Fiscal (seção 12 daquele
    documento); e a relação entre Valor_Titulo e o valor de face da nota
    fiscal quando há retenção na fonte (seção 3), já coberta pela
    fórmula de Mov_Titulo_Retencao (Contabilidade & Fiscal, seção 11).
    Nenhuma estrutura nova nos dois casos, só a referência que faltava.

-   Revisão 11 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): a raiz do CNPJ passa a ser os 8
    primeiros caracteres (CNPJ alfanumérico, IN RFB 2.229/2024); saldo
    de título continua derivado, confirmado por Alberto --- não faz
    sentido guardar. A convenção completa (vigência, identidade +
    versão, sucessão de códigos oficiais, competência, CNPJ
    alfanumérico, um campo por informação, saldos guardados de período
    fechado, sequência de fechamento) vive na Fase 0, seções 2 e 10
    (revisão 41).

-   Revisão 12 --- Mov_Titulo.Origem_Tipo ganha processo_judicial,
    processo_trabalhista e distribuicao_lucro, para os pagamentos que
    nascem de processo e de distribuição de lucros. Desenho aprovado e
    histórico do bloco nos documentos 20 e 22 do Projeto.

-   Bloco 5, revisão 13: os títulos de INSS, IRRF, retenções e DARF da
    DCTFWeb passam a nascer de três origens novas (esocial_retorno_cr,
    dctfweb_darf e consolidacao_retencoes), e a baixa ganha
    vinculacao_dctfweb, sem caixa. Pagamento a maior não é usado em
    baixa nenhuma: só por PER/DCOMP (Contabilidade & Fiscal, seção
    22.5).

14\. Próximo passo

*Com a Revisão 2, o módulo ganhou generalidade (crédito de bonificação
além do adiantamento financeiro, consolidação por CNPJ raiz),
rastreabilidade (reprogramação explícita de título) e cobertura de
eventos acessórios de conta (rendimento e taxa). A Revisão 3 aprofundou
a generalidade (crédito com origem aberta e prazo de validade; evento de
conta financeira com classificação única cobrindo rendimento, perda e
tarifas) e fechou outro gap do ciclo de caixa: empréstimos bancários, do
lado oposto da aplicação financeira. A Revisão 4 completou o empréstimo
com as condições contratuais que faltavam. A Revisão 5 fechou origem
automática/manual da baixa de título (seção 3). A Revisão 6 trouxe
Valor_Tributo_Split para o split payment do IBS/CBS. A Revisão 7 (ciclo
\"consolidar\") fechou cinco pontos que ficavam deliberadamente em
aberto: reversão de provisão confirmada como proporcional (seção 7);
camada de caixa agora suporta também o caso agregado, via
Mov_Aprovacao_Lote (seção 11); convenção de \"participante raiz\" e
propagação de Limite_Credito confirmadas e tornadas condicionais a
Propagar_Limite_Credito (seção 6); saldo de crédito vencido ganhou
tratamento contábil opcional via Contabiliza_Na_Inclusao (seção 4); e
Mov_Emprestimo.ID_Conta_Contabil passou a aceitar também Caixa/Aplicação
(seção 10) --- mais o patch cross-módulo Canal_Split (seção 3), pedido
pela Fase 2 Contabilidade & Fiscal.*

*Esta Revisão 8 (mesmo ciclo \"consolidar\") fecha o gap explícito
deixado desde a Revisão 1 (seção 1: \"este módulo alimenta, por sua vez,
Tesouraria\"), agora que Folha & RH e Tesouraria também foram
consolidados: Mov_Titulo ganha Origem_Tipo=folha_pagamento e
Natureza_Titulo_Folha (seção 2), pedido por Alberto para que a
liquidação de qualquer folha --- mensal, 13º, férias, rescisão, PLR,
autônomo --- gere título a pagar de verdade para TODAS as obrigações que
ela apura (líquido do colaborador, INSS, FGTS, IRRF retido, pensão
alimentícia, consignado), não só o lançamento contábil já existente
desde a Fase 0 revisão 28. O nascimento do título segue o mesmo padrão
já usado para nota fiscal --- sem lançamento contábil próprio, porque a
obrigação já foi reconhecida pela liquidação da folha --- e a baixa
passa pela remessa bancária já existente (Tesouraria), com o caso de
óbito resolvendo automaticamente o beneficiário (Fase 5) e a
visibilidade de pagamento não processado ficando do lado de RH (Fase 5,
seção 12). Ponto que segue sem conferência automática, por decisão de
escopo: condições contratuais do empréstimo vs. valor de cada parcela
(seção 10/13).*

*Esta Revisão 9 conecta este documento ao mecanismo transversal de
fechamento de período generalizado na Fase 0 (seção 10, revisão 37):
Mov_Titulo e Mov_Titulo_Baixa (seções 2 e 3) passam a travar por
Filial+competência sob um único bloco,
Cad_Bloco_Fechamento.Codigo=\"tesouraria\" --- o mesmo bloco, não um par
de blocos coordenados, que também trava a execução do pagamento no
documento de Fase 2 Tesouraria (revisão 6 daquele documento, construída
na mesma consolidação), ainda que as duas entidades continuem
fisicamente cadastradas aqui. Sem checagem de pendência no fechamento,
por decisão de Alberto --- diferente de Compras, o único bloco do
dicionário com essa validação --- porque um título em aberto por vencer
é o estado normal do bloco, não um impeditivo para fechar a competência
de entrada.*

*Esta Revisão 10 (mesmo ciclo \"consolidar\") fecha os três últimos
pontos da revisão geral de módulos pedida por Alberto sobre este
documento. O principal, ponto 9: título de Longo Prazo transita para
Curto Prazo pela simples passagem do tempo, não só por reprogramação ---
nova Reclassificação de Prazo (seção 8), com o limiar
Meses_Limite_Curto_Prazo como parâmetro por empresa (Fase 0, revisão
39), varrida a cada fechamento mensal do bloco \"tesouraria\" (o mesmo
bloco da Revisão 9, reaproveitado como gatilho natural do ciclo) e
disparada também, de forma imediata, por uma reprogramação que muda a
classificação. Os pontos 8 e 10 eram, na prática, referências cruzadas
pendentes, não estrutura nova: o tratamento fiscal do rendimento
financeiro (seção 9) e a relação entre Valor_Titulo e o valor de face da
nota fiscal quando há retenção (seção 3) já estavam cobertos do lado de
Contabilidade & Fiscal --- faltava só apontar para lá, o que esta
revisão faz. Seguindo a ordem original do Documento Analítico, o módulo
natural seguinte continua sendo Contabilidade & Fiscal (já entregue, em
paralelo a esta consolidação) --- a decisão de por onde continuar é
sempre de Alberto.*

*Revisão 11 --- Bloco 1 da validação geral consolidado junto com a Fase
0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal)
e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 12 --- Bloco 3 consolidado junto com a Fase 0 (revisão 45) e a
Fase 8 --- Jurídico. Sem pendência própria deste módulo.*

*Revisão 13 --- Bloco 5 consolidado junto com a Fase 0 (revisão 47),
Folha & RH (revisão 18) e Contabilidade & Fiscal (revisão 19).*



15\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este documento não ganha entidades novas; as alterações em entidades existentes aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3").



16\. Anexo --- Entidades novas da revisão 21 (documento 101)

Revisão 21 do dicionário: entidade nova do documento 101 (título em moeda estrangeira), com as respostas de Alberto de 22/10/2026.

16.1. Título em moeda estrangeira (documento 101)

Mov_Titulo_Reavaliacao

Variação cambial do fim do mês de cada título em moeda estrangeira com saldo em aberto: uma linha por título e por mês fechado (D-N346; documento 101, seção 4.5). Sem vigência (é um fato). O estorno segue o estorno de lote que já existe.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Titulo_Reavaliacao** | *identificador* | --- |
| **ID_Titulo** | *referência (Mov_Titulo)* | O título reavaliado. Só título em moeda estrangeira, com saldo em aberto no fim do mês. |
| **ID_Periodo_Fechamento** | *referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade)* | O mês. Título e período são únicos (uma reavaliação por título por mês). |
| **Data_Reavaliacao** | *data* | O último dia do período. |
| **Saldo_Moeda** | *número* | O saldo em aberto **na moeda do título** na data (valor do título menos baixas (inclusive as de tipo encontro de contas), créditos, mais reprogramações). |
| **Taxa_Fechamento** | *número* | A taxa de fechamento do mês: a da série marcada para o fechamento (Cad_Serie_Cotacao.Uso_Fechamento), na última cotação com data até a Data_Reavaliacao (sábado, domingo e feriado leem a cotação do último dia útil). Revisão 22 (D-N355, documento 112, Q112-1 e Q112-2): taxa única, a PTAX de venda do Banco Central, para título a pagar e a receber; o contador confirma o critério. |
| **ID_Serie** | *referência (Cad_Serie_Cotacao)* | Revisão 22 (D-N355): a série de cotações da qual a taxa foi lida (Q112-3). Guarda o critério daquele mês, mesmo que o critério mude depois. |
| **Data_Referencia_Taxa** | *data* | Revisão 22 (D-N355): o dia da cotação lida; pode ser anterior à Data_Reavaliacao (como a sexta-feira, 30/10/2026, para o fechamento de sábado, 31/10). Para auditoria. |
| **Valor_Reais_Anterior** | *número* | O saldo em reais **antes**: Saldo_Moeda × a taxa em que estava contabilizado (a Taxa_Estimada ou a da reavaliação anterior). |
| **Valor_Reais_Novo** | *número* | O saldo em reais **depois**: Saldo_Moeda × Taxa_Fechamento. |
| **Variacao_Reais** | *número* | Valor_Reais_Novo − Valor_Reais_Anterior, com sinal: em título a pagar, positivo é **perda**; em título a receber, positivo é **ganho**. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento)* | O lançamento contábil da variação, com Origem_Tipo = variacao_cambial (seção 15 da Contabilidade). |
| **Status** | *enumeração {efetivada, estornada}* | estornada quando o período é reaberto e o lote estornado. |
| **ID_Usuario** | *referência (Cad_Usuario)* | Quem executou a reavaliação do mês. |
| **Data_Hora** | *data/hora* | Quando. |

*Revisão 22 --- campos novos: ID_Serie, Data_Referencia_Taxa; campos alterados: Taxa_Fechamento, Saldo_Moeda.*

*Taxa e série do fechamento (revisão 22, D-N355; documento 112). A série usada é a marcada em Cad_Serie_Cotacao.Uso_Fechamento (no máximo uma série ativa por par de moedas), e a taxa é a última cotação com data até a Data_Reavaliacao; ID_Serie e Data_Referencia_Taxa guardam, em cada reavaliação, a série e o dia da cotação lidos. A carga automática da PTAX do Banco Central, para as moedas que ele divulga, usa campos que já existem (Mov_Serie_Cotacao_Valor.Origem = automatico e Cad_Serie_Cotacao.Fonte = banco_central) e fica na camada de aplicação; a integração não foi testada. Moeda que o Banco Central não divulga: o usuário informa a cotação ou aponta onde pegá-la (Cad_Serie_Cotacao.Referencia_Fonte). Cotação que falta no fechamento: o ERP avisa a pendência (moeda e data) e o fechamento do período espera até a cotação ser alimentada (Q112-4 e Q112-6); não conclui sem reavaliar a moeda nem usa taxa antiga em silêncio. É regra de validação do fechamento, sem campo novo.*



17\. Anexo --- Entidades novas da revisão 22 (documento 111)

Revisão 22 do dicionário: entidades novas do documento 111 (tipo da baixa de título), com as respostas de Alberto de 26/10/2026 (Q111-5, Q111-6, Q111-8, Q111-14 e Q111-15).

17.1. Tipo da baixa (documento 111)

Cad_Tipo_Baixa

Cadastro dos tipos de baixa de título (D-N352; documento 111, Q111-5, Q111-6 e Q111-15). Mestre com vigência (identidade e versão, como Cad_Moeda): um tipo pode ser descontinuado sem apagar o histórico. Cadastrável pelo usuário e único para todo o grupo (sem ID_Empresa). Tipos de partida, a confirmar na implantação: pagamento, recebimento, perda, desconto, encontro de contas e vinculação da DCTFWeb. Não é um domínio de Cad_Classe_Sistema porque o cadastro genérico não tem coluna para o indicador de movimentação financeira. A base por bloco fica em Cad_Tipo_Baixa_Bloco.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Tipo_Baixa** | *identificador* | A identidade do tipo. |
| **ID_Tipo_Baixa_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Tipo_Baixa_Versao). ID_Tipo_Baixa é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **Codigo** | *código (20) --- identidade* | O código do tipo, cadastrado pelo usuário (Q111-6). |
| **Descricao** | *texto* | O nome do tipo, como aparece na tela da baixa. |
| **Movimenta_Financeiro** | *enumeração {sempre, nunca, variavel}* | Se a baixa desse tipo move dinheiro. sempre: o dinheiro entra ou sai (pagamento, recebimento); nunca: não é pagamento nem compensação (perda, desconto, vinculação da DCTFWeb); variavel: compensação entre obrigações, com dinheiro reduzido ou zero (encontro de contas). Diz se a baixa pede conta de banco ou caixa (Mov_Titulo_Baixa.ID_Conta_Contabil, só quando Valor_Financeiro é maior que zero). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

Cad_Tipo_Baixa_Bloco

Uma linha por tipo de baixa e por bloco: diz se a baixa daquele tipo entra no bloco e por qual valor (D-N352; documento 111, Q111-8, Q111-12, Q111-14 opção B e Q111-15). Tabela de janela; chave: tipo de baixa mais bloco mais Vigencia_Inicio. Único para todo o grupo (sem ID_Empresa). Hoje só existe o bloco y520 e o futuro não dá para prever: um bloco novo é uma linha nova por tipo, sem mudar a estrutura. Linhas de partida do bloco y520, a confirmar na implantação: pagamento e recebimento = valor_financeiro; encontro de contas = valor_bruto; perda, desconto e vinculação da DCTFWeb = nao_entra. O que cada bloco novo exigir além da base (data, chave, agrupamento) é desenhado quando ele aparecer.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Tipo_Baixa_Bloco** | *identificador* | Chave da linha. |
| **ID_Tipo_Baixa** | *referência (Cad_Tipo_Baixa) --- identidade* | O tipo de baixa. |
| **ID_Bloco_Destino** | *referência (Cad_Classe_Sistema, domínio = bloco_destino_baixa) --- identidade* | O bloco de destino (o "Bloco" do documento 111; o nome ganhou o prefixo ID_ por ser referência). Hoje só y520; domínio aberto. |
| **Base** | *enumeração {nao_entra, valor_financeiro, valor_bruto}* | Se a baixa desse tipo entra no bloco e por qual valor. nao_entra: não gera linha no bloco; valor_financeiro: entra pelo dinheiro movimentado (Mov_Titulo_Baixa.Valor_Financeiro); valor_bruto: entra pelo valor integral da operação (Mov_Titulo_Baixa.Valor_Pago_Reais, ou, em título em reais, o total da baixa), mesmo que a transferência seja reduzida ou zero. A Base que vale é a da data da operação. É o usuário que decide por tipo, ao cadastrar. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |



18\. Anexo --- Entidades novas da revisão 25 (documentos 120 e 123)

Revisão 25 do dicionário: o de-para entre a forma e o tipo da baixa e a reavaliação mensal do crédito em moeda estrangeira, com as respostas de Alberto de 26 e 27/10/2026.

18.1. De-para entre a forma e o tipo da baixa (documento 123)

Cad_Tipo_Baixa_Forma

O de-para entre a **forma** de pagamento ou recebimento que vem do banco ou da remessa e o **tipo da baixa** (D-N367; documento 123, Q113-5, respondida por Alberto em 27/10/2026, sobre a Q113-1 de 26/10/2026: cada forma tem o seu tipo, TED é TED, PIX é PIX, boleto é compensação de boleto, e por isso tem de haver de-para). Tabela de janela, única para todo o grupo (sem ID_Empresa), como Cad_Tipo_Baixa_Bloco; chave: sentido mais forma mais Vigencia_Inicio. A baixa automática procura o tipo por sentido e forma. A forma é um valor do domínio aberto forma_origem_baixa de Cad_Classe_Sistema, e não uma enumeração fixa, porque a lista cresce; o Forma_Lancamento da remessa continua enumeração. Valores de partida de forma_origem_baixa e do de-para, a confirmar na implantação (um tipo por forma): **pagar**, crédito em conta, DOC, TED, PIX, cartão-salário, boleto (compensação de boleto), tributo por código de barras e transferência internacional; **receber** (lista que Alberto aceitou na Q113-6), boleto, Pix, TED, DOC, cartão, dinheiro e cheque. O usuário cria outras linhas. Forma sem de-para na baixa automática vai para a área de inconsistências (Mov_Processo_Inconsistencia).

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Tipo_Baixa_Forma** | *identificador* | Chave da linha. |
| **ID_Tipo_Baixa** | *referência (Cad_Tipo_Baixa)* | O tipo de baixa que a forma gera. |
| **Sentido** | *enumeração {pagar, receber} --- identidade* | Se a forma é de pagamento ou de recebimento (a mesma forma, por exemplo TED, pode ter tipos diferentes nos dois sentidos). |
| **ID_Forma_Origem** | *referência (Cad_Classe_Sistema, domínio = forma_origem_baixa) --- identidade* | A forma que veio do banco ou da remessa. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

18.2. Reavaliação do crédito em moeda estrangeira (documentos 120 e 123)

Mov_Credito_Reavaliacao

A reavaliação mensal do crédito em moeda estrangeira (D-N361, D-N368 e D-N370; documentos 120 e 123, Q101-10, Q101-10a, Q101-10b e Q123-2, respondidas por Alberto em 26 e 27/10/2026). Uma linha por crédito em moeda e por mês fechado, enquanto o crédito tem saldo disponível; no mesmo molde de Mov_Titulo_Reavaliacao. **Todo** crédito em moeda estrangeira é reavaliado, financeiro ou não, **nos dois sentidos**: o dado a um fornecedor (Tipo = pagar, valor a receber) e o recebido de um cliente (Tipo = receber, valor a pagar), porque a variação cambial vale para o que a empresa tem a receber e para o que ela deve (Q101-10b, contra a minha recomendação, e correção de Alberto de 28/10/2026, D-N396; o contador confirma o tratamento de item não monetário). O débito em título a pagar já é reavaliado por Mov_Titulo_Reavaliacao. Sem vigência (é um fato). O estorno segue o estorno de lote que já existe. O fechamento do mês executa a reavaliação dos títulos e dos créditos e **espera a cotação**: sem a taxa da moeda, a pendência vai para a área de inconsistências e nada é gravado. Crédito totalmente aplicado não é reavaliado. Na aplicação contra o título vale o valor contabilizado do crédito (a última reavaliação), e a diferença contra o título é a variação realizada em Mov_Lote_Lancamento com Origem_Tipo = variacao_cambial (Q101-10c). No regime de caixa, a parte não realizada da variação precisa ser neutralizada na apuração (e-Lalur); não verifiquei se o desenho do lucro real cobre isso, e é assunto do contador. O Y520 não muda: o adiantamento vai pelo Valor_Pago_Reais da data em que o dinheiro saiu.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Credito_Reavaliacao** | *identificador* | --- |
| **ID_Credito** | *referência (Mov_Credito)* | O crédito reavaliado: qualquer crédito em moeda estrangeira (ID_Moeda_Credito diferente da moeda funcional), **dado (Tipo = pagar) ou recebido (Tipo = receber)**, com saldo disponível no fim do mês. |
| **ID_Periodo_Fechamento** | *referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade)* | O mês. Crédito e período são únicos. |
| **Data_Reavaliacao** | *data* | O último dia do período. |
| **Saldo_Moeda** | *número* | O saldo disponível **na moeda do crédito** na data: Valor_Credito menos as aplicações (Valor_Aplicado) até a data. |
| **Taxa_Fechamento** | *número* | A taxa de fechamento do mês, a mesma regra do título: série marcada para o fechamento, última cotação com data até a Data_Reavaliacao (PTAX de venda, taxa única; o contador confirma o critério, Q101-9). |
| **ID_Serie** | *referência (Cad_Serie_Cotacao)* | A série de onde a taxa foi lida (guarda o critério daquele mês). |
| **Data_Referencia_Taxa** | *data* | O dia da cotação lida (pode ser anterior à Data_Reavaliacao). |
| **Valor_Reais_Anterior** | *número* | O saldo em reais **antes**: Saldo_Moeda × a taxa em que estava contabilizado (na primeira reavaliação, a Taxa_Cambio do crédito; depois, a da reavaliação anterior). |
| **Valor_Reais_Novo** | *número* | O saldo em reais **depois**: Saldo_Moeda × Taxa_Fechamento. |
| **Variacao_Reais** | *número* | Valor_Reais_Novo menos Valor_Reais_Anterior, com sinal. **Sentido invertido em relação ao título:** no crédito que a empresa **deu** (Tipo = pagar, um direito a receber), positivo é **ganho**; no que **recebeu** (Tipo = receber, uma obrigação), positivo é **perda**. O nome fica como em Mov_Titulo_Reavaliacao, para as duas entidades andarem juntas. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento)* | O lançamento contábil da variação, com Origem_Tipo = variacao_cambial. |
| **Status** | *enumeração {efetivada, estornada}* | estornada quando o período é reaberto e o lote estornado. |
| **ID_Usuario** | *referência (Cad_Usuario)* | Quem executou a reavaliação do mês. |
| **Data_Hora** | *data/hora* | Quando. |
