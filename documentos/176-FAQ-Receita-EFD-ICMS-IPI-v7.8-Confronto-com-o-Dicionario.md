# Respostas da Receita: o FAQ da EFD-ICMS/IPI v7.8 contra o dicionário — Documento 176

*Responde ao seu envio de 05/11/2026 (`Perguntas Frequentes - 7.8.pdf`, 132 páginas, versão de 08/10/2026). Li o FAQ inteiro e conferi cada resposta com o dicionário (revisão 31) e com os documentos 167, 168, 172 e 175. O que a Receita responde, confirma ou corrige está aqui; o que depende de você está na seção 10.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O FAQ é o documento oficial de perguntas e respostas da Receita sobre a EFD-ICMS/IPI. Ele não traz leiaute novo: explica como preencher o que o Guia Prático (versão 3.2.4, de 30/07/2026) já define. Por isso o resultado do confronto é de **ajuste fino**, não de desenho novo. A parte grande do FAQ é o Bloco K (a seção 16, mais da metade das 132 páginas), e o dicionário já tinha entidade para todos os registros dele.

**Dez achados que você precisa ler.**

1. **O 1601 não nasce da nota, nasce do dinheiro (responde a Dúvida 4 do documento 167).** O registro é financeiro: informa o que transitou por instituição financeira, instituição de pagamento ou marketplace, mesmo sem nota, mesmo antes da nota (adiantamento) e inclusive depósito de dinheiro e cheque. A origem que o documento 167 tinha (`Mov_Nota_Fiscal_Saida_Pagamento`) cobre só a venda com nota. A origem certa é a **baixa do título recebido**, e hoje a baixa não guarda a instituição por onde o dinheiro passou. Proponho três campos na baixa, um campo no cadastro de instituição e uma tabela de regras por UF (seção 5).
2. **A Receita só dá a regra de reconhecimento do 1601 para algumas UFs.** Para AL, CE, PB e RN vale a competência (data da autorização do cartão, do Pix, da emissão do boleto, da compensação do cheque); para as demais a resposta geral é "cartão pela competência e o resto pelo caixa". MG e SC têm respostas próprias sobre quem informa e sobre factoring. Para as outras UFs o FAQ não diz nada. Pelo princípio de não ter padrão escondido, a tabela por UF sai com carga provisória só dessas linhas e o ERP avisa nas outras (seção 5.4).
3. **O valor líquido da NT 2026.008 não entra na EFD.** O item 19.2 confirma: `VL_DOC` do C100 continua sendo o `vNF`, `VL_MERC` o `vProd` e `VL_ITEM` do C170 o `vProd` do item (I11), todos **brutos**. Os campos `Valor_Total_Liquido` e `Valor_Unitario_Liquido` das notas (revisão 3) não alimentam a EFD. O 19.3 diz o mesmo para CT-e, NF3e, NFCom, BP-e e NFGás. E o 19.1 repete que CBS, IBS e IS **não são apurados** na EFD-ICMS/IPI.
4. **O C130 vale também na entrada.** A Receita diz que nota conjugada (mercadoria e serviço) autorizada pelo Fisco estadual é escriturada "tanto na tomada quanto na prestação". O documento 175 criou a extensão só para a nota de saída. Passa a pai genérico (seção 4.1). O DF fica de fora: usa o Bloco B.
5. **O C171 é só do varejo de combustíveis e vem junto com o Bloco 1 (1300).** Isso o põe no bloco que você deixou para depois (Q167-6). Sai do documento 175. O C165, ao contrário, **não** é de posto: o FAQ diz que posto não o apresenta e o Guia 3.2.4 o reserva às distribuidoras, refinarias e revendedoras, só na saída (seção 4.2).
6. **O C178 não é preenchido na prática e o `COD_ENQ` do C170 fica vazio.** O FAQ diz as duas coisas. O Guia diz "não preencher" para o `COD_ENQ`. O campo `ID_Classe_Enquadramento_Ipi` (CL_ENQ) do documento 175 passa a ser opcional sem habilitação (seção 4.3).
7. **A fatura do C140 vai com o valor original, sem rateio.** Quando uma fatura cobre várias notas, cada nota leva o valor inteiro da fatura. O valor do título **não sai** de `Mov_Titulo` (que guarda a parcela da nota), então a extensão do C140 ganha um campo (seção 4.4).
8. **Bloco K: tudo o que o FAQ descreve já tem entidade; saem nove avisos e dois ajustes.** O principal: quando o estabelecimento não controla por ordem de produção, `COD_DOC_OP`, `DT_INI_OP` e `DT_FIN_OP` saem em branco. O dicionário hoje imprime o número interno da ordem. Falta um indicador no perfil fiscal da filial (seção 7).
9. **A dúvida D10 do documento 167 (`COD_INS_SUBST` do K275) não se fecha.** Conferi no Guia 3.2.4: o K235 e o K255 mandam **não preencher** desde 01/01/2022, mas o K275 ainda diz que o campo é informado quando há substituição, só para as origens 1 e 2. O FAQ não ajuda: as respostas sobre substituição de insumo são de antes de 2022, e a própria Receita anotou na versão 7.2 que o 0210 deixou de existir em janeiro de 2022 (o documento 167 e o Guia falam de 2023 em alguns trechos). Fica aberta, com pergunta ao contador (C176-5).
10. **A Receita ainda não publicou a tabela de enquadramento legal do IPI.** O FAQ diz para informar o campo vazio enquanto não sair. O dicionário não precisa de nada: `ID_Enquadramento_Ipi` (cEnq, 3 dígitos) é da NF-e e não vai para o C170.

| Assunto | Alteração | Quantidade |
|---|---|---|
| Entidade nova | `Cad_Efd_1601_Regra_Uf` | 1 entidade, 12 campos |
| Entidades existentes com campo novo | `Mov_Titulo_Baixa`, `Cad_Instituicao_Financeira`, `Cad_Filial_Perfil_Fiscal` | 3 entidades, 5 campos |
| Entidades do documento 175 alteradas | `Mov_Nota_Fiscal_Fatura_Comercial` (+1 campo), C130 (vira genérica, +1 campo), C171 (sai) | 3 entidades |
| Valores novos em domínio | `bloco_destino_baixa` (+1), `Motivo_Reclassificacao` (+4), habilitação C165 (texto) | 5 valores |
| Avisos novos do Motor | Bloco K (9), 1601 (2), C420 (1), C197 (1), C500 (1) | 14 avisos |

# 2. O que o FAQ é e quanto pesa

O FAQ é resposta da Receita, e o próprio texto lembra que "considerando as especificidades das legislações de cada UF" a segurança jurídica vem da consulta à UF. Em vários pontos aparecem respostas separadas de MG, SP, SC, AL, CE, PB e RN. Regra que segui: **o que a Receita responde sem citar UF vale para todas e entra no dicionário; o que é resposta de uma UF vira parâmetro por UF, com carga provisória e aprovação do contador.**

A versão 7.8 (08/10/2026) alterou só a seção 19 (reforma tributária): atualizou o 19.1 e incluiu o 19.2 e o 19.3. O resto do FAQ é texto de versões de 2013 a 2025. Isso importa para o Bloco K: boa parte das respostas fala em "0210", registro que a própria Receita registrou como extinto desde janeiro de 2022. Usei essas respostas só para as regras que não dependem do 0210.

# 3. O que o FAQ confirma e já está no dicionário

Conferi cada resposta com o dicionário. Estas **batem** e não pedem nenhuma alteração.

| Seção do FAQ | O que a Receita diz | Onde está no dicionário |
|---|---|---|
| 16.3.1.20 e 16.3.1.2 | Quem só informa saldo escriturado usa K010 opção 2 (restrito a saldos); atacadista e equiparado informam K200, K220, K270/K275/K280 | `Cad_Filial_Perfil_Fiscal.Tipo_Leiaute_Bloco_K` (simplificado, completo, restrito_saldos) e `Cad_Bloco_K_Exigencia_Registro` |
| 16.3.1.6, 16.3.1.13, 16.3.1.17 | Estoque próprio em poder de terceiro é IND_EST 1; em recinto alfandegado, o participante é o próprio informante | `Mov_Saldo_Estoque.Propriedade` e `ID_Participante_Proprietario` |
| 16.3.1.9 e 16.3.1.14 | Estoque zero não precisa ser informado | `Mov_Saldo_Estoque` (o Motor não gera K200 de saldo zero) |
| 16.4 (K220) | Um K220 por item de destino; o tipo do item pode mudar; troca de código obriga o K220 | `Mov_Estoque_Reclassificacao` (origem, destino, quantidade de cada lado) |
| 16.5.1.2 e 16.5.1.3 | OP aberta sai com `DT_FIN_OP` em branco e se repete até concluir, desde que haja apontamento | `Mov_Ordem_Producao_Apontamento.Encerrada` |
| 16.5.1.1 | OP reaberta em outro período é nova OP | `Mov_Ordem_Producao` (nova ordem; não reabre a anterior) |
| 16.10 (K210/K215) | Desmontagem não é industrialização; o destino sempre sai no K215 | `Mov_Producao_Desmontagem` e `Mov_Producao_Desmontagem_Destino` |
| 16.11 (K260/K265) | Reprocesso mantém o código; K260 sem K265 é aceito | `Mov_Producao_Reprocesso` e `Mov_Producao_Reprocesso_Item` (opcional) |
| 16.12 e 11.9.3.1 | Fator de conversão do 0220; código genérico de uso e consumo leva 0220 com fator 1 para cada unidade | `Cad_Produto_Servico_Conversao_Unidade` |
| 16.13 (K270/K275/K280) | Correção de período anterior; K280 corrige o K200, não o inventário | `Mov_Producao_Correcao` (K270, K275, K280 numa entidade com `Tipo_Registro_Correcao`) |
| 11.16.1.1 | Duas Reduções Z no mesmo ECF após intervenção: dois C405 | `Mov_Ecf_Reducao_Z` com `Contador_Reinicio_Operacao` e `Contador_Reducao_Z` |
| 11.15.1.1 | Perfil do contribuinte decide os filhos do C400 | `Cad_Filial_Perfil_Fiscal.ID_Perfil_Efd` |
| 19.1 | IBS, CBS e IS não são apurados na EFD | Documento 167 (já assumido) |
| 17.6.1.2 | O 1601 tem dois participantes: a instituição que pagou e o intermediador | `COD_PART_IP` e `COD_PART_IT` do documento 167 (agora com origem nova, seção 5) |

# 4. O que o FAQ muda no documento 175

## 4.1 C130: pai genérico, entrada e saída

**O que o FAQ diz (11.6.1.1 e 11.6.2.1).** Devem ser informadas na EFD as notas autorizadas pelo Fisco estadual que tratam de mercadoria e serviço (notas conjugadas), e quando houver destaque de ISSQN, IRRF ou previdência o C130 é preenchido. A nota conjugada deve ser escriturada "tanto na tomada quanto na prestação". Nota de serviço de município não entra, e os contribuintes do DF não preenchem o C130 (usam o Bloco B).

**Ajuste.** `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms` passa a se chamar `Mov_Nota_Fiscal_Servico_Nao_Icms`, com `Origem_Tipo` mais `ID_Nota` no lugar de `ID_Nota` da saída (regra 4 do documento 175: pai genérico quando a regra vale em entrada e saída). Um campo a mais (de 7 para 8). Valores como o documento traz, nunca recalculados. O Motor não gera o C130 para estabelecimento do DF (a UF vem de `Cad_Filial`; sem campo novo).

## 4.2 C165 e C171: o C171 sai, o C165 fica só para distribuidora, refinaria e revendedora

**O que o FAQ diz (11.8.1.1, 11.10.1.1 e 11.10.2.1).** O posto de combustível não apresenta o C165. O C171 é só do comércio varejista de combustíveis, nas entradas, para o volume recebido em litros por item (livro de movimentação de combustíveis); os postos informam também o 1300 e os filhos. Combustível comprado para consumo próprio (usina com posto interno) não leva o C171.

**Ajuste.**

1. `Mov_Nota_Fiscal_Entrada_Item_Tanque` (4 campos) **sai do documento 175**. O C171 depende do tanque do Bloco 1 (1300 a 1391), que você deixou para depois, em bloco próprio (Q167-6). Entra nesse bloco quando ele for desenhado.
2. A habilitação `efd_combustivel_c165` passa de "C165 e C171 (combustíveis, nota)" para "C165 (combustível na nota de saída: distribuidora, refinaria e revendedora; não posto)". O número de valores de habilitação continua 13.
3. A extensão `Mov_Nota_Fiscal_Saida_Combustivel_Transporte` (C165, 6 campos) continua como está.

## 4.3 C178 e COD_ENQ: nada a gerar

**O que o FAQ diz (11.12.1.1 e 11.9.1.1).** Os setores do C178 (cigarros e bebidas quentes) são obrigados à NF-e modelo 55, "este registro não é preenchido na EFD"; foi criado para fabricante ou importador e varejista e atacadista não o apresentam. O `COD_ENQ` do C170: a tabela não foi publicada pela Receita e o campo vai vazio. O Guia 3.2.4 também manda não preencher.

**Ajuste.**

1. `Mov_Nota_Fiscal_Saida_Item.ID_Classe_Enquadramento_Ipi` (CL_ENQ do C178) fica **opcional e sem habilitação**: nenhum bloco depende dele e a carga das 31 linhas (domínio `classe_enquadramento_ipi`) continua provisória. É a opção que não perde nada se a Receita voltar atrás (Q176-7).
2. Regra de geração, sem campo: o Motor deixa o `COD_ENQ` do C170 vazio. `ID_Enquadramento_Ipi` (cEnq da NF-e) **nunca** alimenta esse campo.

## 4.4 C140: valor original da fatura

**O que o FAQ diz (11.7.1.1 a 11.7.1.3).** O leiaute permite um C140 por nota. Havendo mais de um tipo de título, informa-se um registro com `IND_TIT` 99, descrevendo os outros títulos com números e valores, e `VL_TIT` com a soma. Várias notas podem ser consolidadas numa fatura, e nesse caso "para cada nota apresentada no C100, a fatura deve ser informada no registro C140, sempre com o seu valor original, sem nenhum rateio".

**O que o documento 175 tinha.** O valor total do C140 saía de `Mov_Titulo` (um título por parcela). Isso vale quando a fatura é de uma nota só. Na fatura consolidada, o título de cada nota guarda a parte da nota, não o valor original.

**Ajuste.** `Mov_Nota_Fiscal_Fatura_Comercial` ganha `Valor_Titulo_Original` (VL_TIT): o valor da fatura inteira como está no documento. Obrigatório quando a fatura cobre mais de uma nota ou quando o tipo é `outros`; vazio na fatura de uma nota só (o Motor deriva de `Mov_Titulo`, sem divergência). De 6 para 7 campos. Estava descrito como "derivado" e isso era a premissa errada.

## 4.5 C420 e C197: duas regras de validação

1. **C420, `NR_TOT`.** O FAQ (11.15.2.1) diz que, havendo mais de uma carga tributária efetiva com o mesmo totalizador, o código vem no formato `xxTnnnn` (tabela 4.4.6) e o número do totalizador (`NR_TOT`, de 01 a 30) é obrigatório: no exemplo, `01T0700`, `02T0700` e `03T0700`, com `NR_TOT` 01, 02 e 03. Com um totalizador `T0700` único, um só C420. `Mov_Ecf_Reducao_Z_Totalizador.Numero_Totalizador` continua opcional na tabela (os outros padrões não usam), e o Motor **avisa** quando o código segue o padrão `xxTnnnn` e o número vem vazio, ou quando o número vem fora de 01 a 30.
2. **C197.** O FAQ (11.14) diz que só se informa o C197 em UF que publicou a tabela 5.3 do Ato COTEPE. Nas outras, o ajuste vai na apuração (E111, tabela 5.1.1). Regra de geração, sem campo novo: o Motor só gera C197 quando existe a carga da tabela 5.3 da UF em `Cad_Efd_Codigo_Estadual`; sem ela, aviso e ajuste na apuração.

## 4.6 C500: como o FAQ lê os cinco valores

**O que o FAQ diz (11.17).**

1. `VL_FORN` é quantidade vezes preço do kWh ou do m³, com os impostos já incluídos.
2. `VL_DA` (despesas acessórias) recebe os valores, excluído o consumo, sobre os quais incide ICMS ou contribuição.
3. `VL_TERC` recebe tudo o que é receita de terceiros, **inclusive a taxa de iluminação pública**.
4. O campo de informação complementar (campo 23) **só aceita um código**, cuja descrição vai no 0450 e pode juntar mais de uma ocorrência; só as de interesse fiscal.
5. A aquisição de água canalizada (modelo 29) vai no C500 e no C590.

**Conferência.** Os cinco valores já têm origem no mapa de cClass da NF3e (documento 175, anexo). Falta apenas escrever as regras 3 e 4 na descrição dos campos de origem. A taxa de iluminação pública só entra em `VL_TERC` se o grupo de cClass dela estiver no mapa (080, 081, 085, 086 ou 087); se a taxa vier em outro grupo, o Motor avisa. Para o campo 23, o Motor gera **um** código no 0450 e concatena as observações de interesse fiscal no texto dele. Sem campo novo.

## 4.7 C100 e C170: o custo do que não gera crédito

O FAQ (11.13.2.1) diz que o adquirente sem direito a crédito de IPI ou de ICMS-ST **soma** esses valores ao `VL_MERC` do C100 e ao `VL_ITEM` do C170 (compõem o custo) e **não informa** `VL_IPI` e `VL_ICMS_ST` nos C100, C170 e C190. É regra de geração do Motor, sem campo novo (o direito a crédito já existe na apuração). Registro aqui porque contradiz o princípio "tal como emitido" só na aparência: o valor da nota continua guardado como veio; é o arquivo que soma.

# 5. O registro 1601 (instrumentos de pagamento)

## 5.1 O que o FAQ diz

A seção 17.6 é a mais rica do FAQ para o desenho. Em resumo:

1. **O que informar.** O valor total das vendas e prestações **recebidas** pelo declarante, ainda que de outros estabelecimentos do informante, por cartão de débito, crédito, loja (private label), transferência, Pix e demais instrumentos eletrônicos, mais o que o intermediador informa sobre as transações intermediadas. Excluídos estornos, cancelamentos e o que não é da atividade (multa e juros pagos pelo cliente). O total se divide em três campos: incidência de ICMS (`TOT_VS`), de ISS (`TOT_ISS`) e o restante (`TOT_OUTROS`).
2. **Quem é o participante.** Dois: a instituição que recebeu do cliente e repassou (banco, financeira, plataforma digital) e o intermediador da transação (marketplace, app de delivery). Se há intermediador mas o pagamento foi em dinheiro direto ao contribuinte, não se informa. O 1601 é obrigatório sempre que o dinheiro passa por instituição financeira, de pagamento ou marketplace.
3. **O que entra e o que não entra.** Entra: venda no balcão com cartão, Pix ou boleto; delivery que recebe e repassa; troca com complemento pago por terceiro; **depósito em dinheiro ou cheque** recebido por venda ou serviço. Não entra: venda em dinheiro direto ao contribuinte; troca sem complemento ou com complemento em dinheiro; venda pelo site com pagamento direto em dinheiro. Pagamento misto: só o que passou por instituição, e o dinheiro ou cheque só se for depositado (aí entra, com o banco depositante como participante).
4. **Regime.** A EFD é por competência, mas o 1601 é financeiro: "operações de pagamento garantidas (cartão de crédito) informa pela competência e as demais pelo regime de caixa". As respostas de AL, CE, PB e RN são mais específicas (seção 5.4).
5. **Valor.** O bruto, para dar para cruzar com os documentos fiscais; no marketplace que repassa já descontada a comissão, informa-se com a comissão incluída (frete FOB e juros do comprador que não chegam ao vendedor ficam de fora). Fatura de telecom com itens negativos: informa-se o valor pago com os negativos deduzidos.
6. **Valores antecipados** antes do fato gerador, "ainda que antes da emissão da nota fiscal, devem ser declarados".
7. **Quem informa** (matriz que concentra o recebimento): a resposta geral é "o estabelecimento em que está concentrado o recebimento"; AL, CE e RN e MG respondem o contrário: o estabelecimento que realizou a venda, sem importar o contrato centralizado.
8. **Factoring.** Liquidação antecipada do boleto no mês do fato gerador: informa-se o valor da operação, e a factoring é a instituição (`COD_PART_IP`).
9. **Divisão do total.** Resposta específica de telecom, mas que dá a regra geral de classificação do valor: com CST e CFOP diferente de 5933 vai em `TOT_VS`; com CFOP 5933 vai em `TOT_ISS`; sem CST (indicador `indSemCST`, sem CFOP) vai em `TOT_OUTROS`. Co-billing: a operadora local informa em `TOT_OUTROS` o que recebe em nome da de longa distância, e esta informa em `TOT_VS` o que recebe da local.
10. **Dispensa.** Produtor rural informa se a UF obriga.

## 5.2 O que o dicionário tinha, e por que não basta

O documento 167 mapeou o 1601 como derivado: `COD_PART_IP` vinha de `Mov_Nota_Fiscal_Saida_Pagamento.ID_Participante_Credenciadora`, `COD_PART_IT` de `Mov_Nota_Fiscal_Saida.ID_Participante_Intermediador`, e `TOT_VS` e `TOT_ISS` do `Valor_Pagamento` por tipo de nota. Três lacunas aparecem com o FAQ:

1. **Recebimento sem nota ou antes da nota** (adiantamento, depósito, pagamento por Pix sem documento) não está em `Mov_Nota_Fiscal_Saida_Pagamento`. Ele só existe como **baixa de título** (`Mov_Titulo_Baixa`) ou como adiantamento.
2. **A baixa não guarda a instituição.** `Mov_Titulo_Baixa` aponta a conta contábil de entrada do dinheiro (`ID_Conta_Contabil`), não a instituição de pagamento que repassou. Para a baixa por retorno bancário a instituição sai de `Cad_Conta_Bancaria`; para cartão, Pix de intermediador e marketplace ela é um participante que não é a conta onde o dinheiro caiu.
3. **A instituição financeira não é um participante.** `Cad_Instituicao_Financeira` (ISPB, COMPE) não tem ligação com `Cad_Participante`, e o `COD_PART_IP` do 1601 é um código do 0150, ou seja, participante.

O que já existe e serve: o mecanismo `Cad_Tipo_Baixa_Bloco` (documento 111), criado para o Y520 com `Base` igual a `nao_entra`, `valor_financeiro` ou `valor_bruto`, e o domínio aberto `bloco_destino_baixa`, que hoje só tem `y520`. O 1601 é o segundo bloco que o mecanismo previa.

## 5.3 Proposta

Princípio mantido: **o 1601 não se grava, é derivado das baixas.** Gravamos só o que a baixa precisa guardar para que a derivação seja possível.

1. **Domínio `bloco_destino_baixa` ganha `efd_1601`.** Cada tipo de baixa diz, por `Cad_Tipo_Baixa_Bloco`, se entra no 1601 e por qual base (`valor_bruto` na maioria, conforme 17.6.1.7). Carga provisória: recebimento por cartão, Pix, TED, boleto, cheque depositado, dinheiro depositado e adiantamento entram; baixa por encontro de contas, compensação, desconto e cancelamento não entram (`nao_entra`).
2. **`Mov_Titulo_Baixa` ganha três campos.**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Instituicao_Pagamento` | referência (Cad_Participante), opcional | COD_PART_IP: a instituição financeira, de pagamento ou plataforma por onde o dinheiro passou. Aviso quando o tipo de baixa entra no 1601 e o campo está vazio. Na baixa por retorno bancário, o Motor propõe a instituição da conta (`Cad_Conta_Bancaria`). |
| `ID_Participante_Intermediador` | referência (Cad_Participante), opcional | COD_PART_IT: o marketplace ou app que intermediou a venda. Na baixa de título de nota de saída, sai da nota (`Mov_Nota_Fiscal_Saida.ID_Participante_Intermediador`); preenchido aqui só quando não há nota. |
| `Classe_Incidencia_1601` | enumeração {icms, iss, outros}, opcional | Em qual dos três campos do 1601 o valor entra (TOT_VS, TOT_ISS, TOT_OUTROS). **Só quando a baixa não tem nota** (adiantamento, depósito, pagamento sem documento). Com nota, o Motor deriva pela regra do item 9 da seção 5.1 (CST, CFOP 5933) e o campo fica vazio, para não gravar o que muda se a nota mudar. |

3. **`Cad_Instituicao_Financeira` ganha `ID_Participante`** (referência a `Cad_Participante`, opcional): o participante (0150) que representa a instituição. Sem ele, o Motor não tem como preencher o `COD_PART_IP` a partir da conta bancária.
4. **Entidade nova `Cad_Efd_1601_Regra_Uf`** (seção 5.4).

## 5.4 A regra por UF

Entidade nova `Cad_Efd_1601_Regra_Uf`, catálogo com vigência, carga provisória (`Situacao_Dado = provisorio`, com `ID_Instancia_Aprovacao`). Campos:

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_1601_Regra_Uf` | identificador | --- |
| `ID_Efd_1601_Regra_Uf_Versao` | identificador da versão | Chave da versão (padrão dos mestres). |
| `ID_Estado` | referência (Cad_Estado) --- identidade | A UF a que a regra se aplica. |
| `Obrigatorio` | booleano | Se a UF obriga a entrega do 1601 (FAQ 17.6.1.9 e 17.6.1.10: o PR desobriga, MG e SC obrigam; produtor rural segue a UF). |
| `Criterio_Reconhecimento` | enumeração {competencia_da_transacao, cartao_competencia_demais_caixa} | Como se escolhe a data do valor: pela transação financeira entre o cliente e o contribuinte, ou pela regra geral do FAQ (cartão de crédito pela competência, o resto pelo caixa). |
| `Estabelecimento_Informante` | enumeração {quem_vendeu, quem_recebeu} | Qual estabelecimento escritura quando o recebimento é centralizado na matriz. |
| `Fonte` | texto | A resposta do FAQ ou a norma da UF que sustenta a linha. |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto | Trio de vigência; fim em 31/12/9999 quando indefinido. |
| `Situacao_Dado` | enumeração {provisorio, validado} | Padrão do dicionário. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A aprovação do contador. |

Carga provisória (só o que o FAQ diz; as demais UFs **não ganham linha** e o Motor avisa):

| UF | Obrigatório | Critério | Quem informa | Fonte |
|---|---|---|---|---|
| AL, CE, PB, RN | sim | competência da transação (cartão na autorização, Pix e TED na transferência, boleto na emissão, cheque na compensação; adiantamento pelo meio usado) | AL, CE e RN: quem vendeu (PB: o FAQ não diz) | FAQ 17.6.1.5 e 17.6.1.9 |
| MG | sim | regra geral do FAQ | quem vendeu, sem duplicar na matriz de outra UF | FAQ 17.6.1.9 |
| SC | sim (a pergunta 17.6.1.9 parte de filial de SC não dispensada) | regra geral do FAQ | a resposta de SC trata só de factoring; vale a regra geral (quem recebeu) | FAQ 17.6.1.6 e 17.6.1.9 |
| PR | não (matriz que concentra o recebimento) | não se aplica | não se aplica | FAQ 17.6.1.9 |

Pergunta de leitura minha, para o contador (C176-2): a linha do PR é a matriz sem obrigação; dela não dá para concluir que o PR dispense o 1601 de todo contribuinte, e por isso ela entra só com a observação do exemplo.

## 5.5 Efeito no documento 167

A linha do 1601 no documento 167 (Anexo C) passa de "COBERTO-DERIVADO, nenhum campo faltando" para "COBERTO-DERIVADO, com os campos desta seção", e a Dúvida 4 se fecha. A Receita também respondeu a segunda parte: o `TOT_OUTROS` tem origem identificada (nota sem CST) e o recebimento sem nota tem a classe na própria baixa.

# 6. Valores brutos, reforma tributária e o que não entra na EFD

1. **Item 19.2.** `VL_DOC` (C100) = `vNF` (W16), `VL_MERC` (C100) = `vProd` (W07), `VL_ITEM` (C170) = `vProd` do item (I11). São os valores brutos, antes da dedução de IBS, CBS e IS que a NT 2026.008 passou a tratar no valor líquido.
2. **Item 19.3.** Nos CT-e, CT-e OS, CT-e Simp, NF3e, NFCom, BP-e e NFGás, os valores de produto, item e serviço continuam sendo o **valor bruto** do documento.
3. **Item 19.1.** CBS, IBS e IS não são apurados na EFD-ICMS/IPI, mas a EFD "segue a correlação dos campos dos documentos fiscais" dos itens 19.2 e 19.3.

**Efeito.** `Mov_Nota_Fiscal_Saida_Item.Valor_Total_Liquido` e `Valor_Unitario_Liquido` (vProdLiq e vUnComLiq, NT 2026.008), e os iguais da entrada, **nunca** alimentam o C100 nem o C170. A descrição desses quatro campos ganha a frase "Não vai para a EFD-ICMS/IPI: o arquivo usa o valor bruto (FAQ 19.2)". É texto de campo; não muda estrutura.

# 7. Bloco K: o que confere e o que muda

O Bloco K do FAQ (seção 16) tem 13 subseções e mais de uma centena de perguntas. Conferi as respostas por registro contra as entidades de produção e de estoque do dicionário. O resultado é favorável: **nenhum registro do Bloco K ficou sem entidade**, e o desenho de Revisão 30 (documento 168) já separa K210/K215, K220, K230/K235, K250/K255, K260/K265, K270/K275/K280 e K290/K300. A seção 3 lista o que bate. O que muda é pouco e está abaixo.

## 7.1 Ajuste 1: ordem de produção em branco quando o estabelecimento não controla por ordem

**FAQ 16.5.1.6.** Quando o estabelecimento não controla o processo por ordem de produção, `DT_INI_OP`, `DT_FIN_OP` e `COD_DOC_OP` do K230 ficam em branco, como diz o Guia. A produção e os insumos continuam informados.

**Dicionário hoje.** `Mov_Ordem_Producao.Codigo_Op_Sped`: "vazio usa o número interno da ordem". Isso imprime um número no `COD_DOC_OP` mesmo para quem não controla por ordem.

**Proposta.** `Cad_Filial_Perfil_Fiscal` ganha `Informa_Ordem_Producao_Bloco_K` (booleano, obrigatório, sem valor padrão; carga provisória pelo contador). Falso: o Motor gera os três campos em branco e agrupa a produção do período por item. Verdadeiro: o comportamento atual. O perfil já tem vigência, então a mudança de política da empresa fica no histórico (Q176-8).

## 7.2 Ajuste 2: motivos da reclassificação (K220)

**FAQ 16.4.1.** Os casos que a Receita manda lançar no K220: item deteriorado que passa a subproduto vendável (16.4.1.21, tipo 05); obsolescência com reaproveitamento como insumo (16.4.1.15); estoque segregado por cliente com código próprio (16.4.1.20); aglutinação de insumos de cores diferentes em um código único (16.4.1.18); reprovação no controle de qualidade, exceto o que vira reprocesso ou desmontagem (16.4.1.23).

`Mov_Estoque_Reclassificacao.Motivo_Reclassificacao` tem três valores: `solicitacao_cliente`, `controle_qualidade` e `outro`. Proponho quatro valores novos: `deterioracao`, `obsolescencia_reaproveitamento`, `estoque_por_cliente` e `aglutinacao_insumo`. O campo é interno (não vai ao arquivo), serve à auditoria; o `outro` continua para o que não couber. Q176-9.

## 7.3 Avisos do Motor (sem campo, sem bloqueio)

O ERP avisa e nunca bloqueia. Nove avisos que o FAQ justifica:

| # | Aviso | FAQ |
|---|---|---|
| 1 | Insumo igual ao produto no mesmo K230/K235 (o PVA rejeita): é reprocesso e vai em `Mov_Producao_Reprocesso` | 16.11.1.4 |
| 2 | Reprocesso em outra fase ou com produto de código diferente: não é K260, é K230/K235 | 16.11.1.5 e 16.11.1.7 |
| 3 | Desmontagem encerrada (`Data_Fim_Os` preenchida) sem item de destino: o K215 é obrigatório até o fim da ordem | 16.10.1.8 |
| 4 | Item tipo 06 (produto intermediário) em estrutura de produção ou consumo: só vai no K200, não no K235/K255 | 16.3.1.3 e 16.3.1.15 |
| 5 | Produção em elaboração informada no K200: ela não é quantificada | 16.3.1.7 e 16.5.1.7 |
| 6 | K270 com origem K220 sem K275 filho, mesmo no leiaute simplificado (exceção da regra de dispensa do K275) | 16.13.1.7 |
| 7 | K280 usado para ajustar diferença entre o K200 e o inventário: o K280 só corrige o K200; a diferença tem de ser rastreada ao K270/K275 ou ao C170/NF-e | 16.13.1.6 |
| 8 | Correção de apontamento conhecida dentro do próprio mês: corrige-se o registro original, não se usa K270 | 16.13.1.1 |
| 9 | Nota de ajuste de inventário com data diferente da data do inventário (a NF-e é emitida com a data de 31/12 para refletir no estoque) | 16.3.1.18 |

Mais três regras de geração, sem aviso: (a) a transferência entre filiais só entra no estoque da filial de destino quando entra no C170, não quando sai no C100 da origem (16.3.1.19); (b) a ordem reaberta em outro período é nova ordem (16.5.1.1, já assim no dicionário); (c) o K200 de quem não teve movimento no mês repete o saldo do mês anterior (16.3.1.11).

Os avisos 4 e 5 ficam em `Mov_Ordem_Producao_Item` e `Mov_Saldo_Estoque`; os outros em `Mov_Producao_*` e `Mov_Estoque_Reclassificacao`. O Motor lê a regra, não grava.

## 7.4 O que o FAQ não responde

1. **A UF decide a correção de ordem aberta (16.13.1.4).** A Receita transcreve duas respostas diferentes: Minas Gerais só admite correção **negativa** via K270/K275 em ordem aberta (a positiva vai no K230/K235); São Paulo não recomenda corrigir ordem aberta direto no K230/K235. Não é regra nacional. O dicionário não impede nenhum dos caminhos (o K270 aceita as duas quantidades) e o aviso fica por UF, no contador (C176-6).
2. **Em qual UF o consumo interno exige NF-e.** O FAQ diz "se a legislação estadual permitir". Depende da UF, e isso é parâmetro por UF no documento 172 (`Cad_Efd_Parametro_Uf`), sem ação nova aqui.

# 8. A dúvida D10 do documento 167 (`COD_INS_SUBST` do K275)

O documento 167 tratou o campo como obsoleto porque o 0210 acabou. Conferi com o Guia 3.2.4:

| Registro | Texto do Guia | Situação |
|---|---|---|
| K235 (campo 05) | "informar o código do insumo previsto no 0210 e substituído... **a partir de 01/01/2022 não preencher**" | obsoleto |
| K255 (campo 05) | o mesmo texto | obsoleto |
| K275 (campo 05) | "este campo deverá ser informado quando se estiver escriturando quantidade consumida não apontada em período anterior, e desde que exista a substituição"; só existe nas origens 1 e 2 do K270 | **sem a frase "não preencher"** |

O FAQ (16.2) trata a substituição de insumo em dezenas de respostas, mas todas pressupõem o 0210, que a Receita registrou como extinto. Portanto nem o Guia nem o FAQ dão uma resposta definitiva sobre o K275. Duas leituras: (a) o campo ficou por esquecimento da Receita e permanece sem uso; (b) ainda é exigido nas correções das origens 1 e 2. **Esta é a leitura que o ERP precisa de uma resposta e não tem.** Pergunta ao contador (C176-5). Enquanto isso, o dicionário não cria o campo, e a dúvida D10 permanece aberta, com um aviso a mais na lista do documento 38.

# 9. Correções de texto nos documentos 167 e 175

Para a próxima consolidação, sem alterar o dicionário agora (você aprova na Q176-10):

| Onde | Texto atual | Texto novo |
|---|---|---|
| Documento 167, Anexo C, linha do 1601 | "COBERTO-DERIVADO, nenhum campo" | "COBERTO-DERIVADO, com campos novos na baixa e regra por UF (documento 176, seção 5)" |
| Documento 167, Dúvida 4 | Aberta | Fechada pelo FAQ 17.6 (documento 176) |
| Documento 167, linha do C130 | só a saída | entrada e saída (documento 176, seção 4.1) |
| Documento 175, seção 6.4 | C165 e C171 | só C165; C171 vai ao bloco de combustíveis (documento 176, seção 4.2) |
| Documento 175, habilitação `efd_combustivel_c165` | "C165 e C171 (combustíveis, nota)" | "C165 (combustível na nota de saída: distribuidora, refinaria e revendedora; não posto)" |
| Documento 175, `Mov_Nota_Fiscal_Saida_Item.ID_Classe_Enquadramento_Ipi` | com habilitação | opcional, sem habilitação (documento 176, seção 4.3) |
| Documento 175, `Mov_Nota_Fiscal_Fatura_Comercial` | valor total "sai de Mov_Titulo" | `Valor_Titulo_Original` na fatura consolidada (documento 176, seção 4.4) |
| Documentos 167 e 168, K275 | `COD_INS_SUBST` "obsoleto" | dúvida aberta, com a leitura do Guia (documento 176, seção 8) |
| Descrição de `Valor_Total_Liquido` e `Valor_Unitario_Liquido` (notas de entrada e saída) | sem menção à EFD | "Não vai para a EFD (FAQ 19.2)" |

# 10. Perguntas

## 10.1 Para você, Alberto (Q176-1 a Q176-10)

**Q176-1. O 1601 passa a ser derivado das baixas de título, com `efd_1601` no mecanismo de blocos da baixa (seção 5.3)?** Recomendo sim. Alternativas: manter só a nota como origem (perde adiantamento, depósito e Pix sem nota), ou deixar o 1601 para depois.

**Q176-2. `Cad_Instituicao_Financeira` ganha `ID_Participante` (0150) para o `COD_PART_IP`?** Recomendo sim. Alternativa: o Motor cria o participante da instituição na primeira baixa que precisar, sem cadastro prévio (mais automático, mas cria participante sem conferência).

**Q176-3. Tabela `Cad_Efd_1601_Regra_Uf` com a carga provisória de AL, CE, PB, RN, MG, SC e PR (seção 5.4), e as demais UFs sem linha, com aviso?** Recomendo sim. Alternativa: sem tabela, com regra única (a geral do FAQ) para todas as UFs, o que esconde a diferença de AL, CE, PB e RN.

**Q176-4. `Classe_Incidencia_1601` (icms, iss ou outros) na baixa, preenchida só quando a baixa não tem nota (seção 5.3)?** Recomendo sim. Alternativa: tratar todo recebimento sem nota como `TOT_OUTROS`, que é errado para o adiantamento de venda que vai ter nota de mercadoria.

**Q176-5. C130 vira extensão genérica de entrada e saída (seção 4.1)?** Recomendo sim. Alternativa: manter só a saída e deixar a tomada conjugada para depois.

**Q176-6. O C171 sai do documento 175 e entra no Bloco 1 de combustíveis, e a habilitação do C165 fica "distribuidora, refinaria e revendedora, não posto" (seção 4.2)?** Recomendo sim. Alternativa: manter o C171 com o tanque como código, como estava.

**Q176-7. `ID_Classe_Enquadramento_Ipi` (CL_ENQ do C178) fica opcional e sem habilitação (seção 4.3)?** Recomendo sim. Alternativa: tirar o campo e as 31 linhas da carga, já que a Receita diz que o C178 não é preenchido.

**Q176-8. `Cad_Filial_Perfil_Fiscal` ganha `Informa_Ordem_Producao_Bloco_K` (seção 7.1)?** Recomendo sim. Alternativa: sempre imprimir o número interno da ordem, como hoje (arrisca divergir do Guia para quem não controla por ordem).

**Q176-9. `Motivo_Reclassificacao` ganha os quatro valores da seção 7.2?** Recomendo sim. Alternativa: manter os três e deixar tudo o que não for cliente ou qualidade em `outro`.

**Q176-10. Aplicar os ajustes das seções 4 e 6 e as correções de texto da seção 9 na próxima consolidação?** Recomendo sim. Alternativa: aplicar já, em revisão própria (o que fragmenta a consolidação, que já tem os documentos 158, 172 e 175 esperando).

## 10.2 Para o contador (C176-1 a C176-7)

**C176-1.** A leitura de 17.6.1.9 (a matriz do PR que concentra o recebimento está dispensada) vale para toda empresa do PR ou só para o caso do exemplo?

**C176-2.** A linha do PR na carga provisória do 1601 é a leitura correta, ou o PR obriga o 1601 como as outras UFs?

**C176-3.** Para as UFs fora da carga (SP, RJ, RS, PE, DF, BA e as demais): qual o critério de reconhecimento do 1601 e quem informa quando o recebimento é centralizado? O FAQ não diz.

**C176-4.** No cartão de crédito, a data da autorização que o FAQ pede é a `dPag` da nota (`Mov_Nota_Fiscal_Saida_Pagamento.Data_Pagamento`) ou há outra data na transação (arquivo da credenciadora)?

**C176-5.** O K275 ainda exige o `COD_INS_SUBST` nas origens 1 e 2 (Guia 3.2.4) ou o campo ficou sem uso depois do fim do 0210? (seção 8)

**C176-6.** Para as UFs em que a Mlegate atende: ordem de produção aberta aceita correção positiva via K270/K275 ou só pelo K230/K235? (MG e SP respondem de formas diferentes)

**C176-7.** O C130 de entrada (tomada de serviço em nota conjugada) leva os mesmos campos de IRRF e previdência da saída, ou a tomada retém e destaca de outra forma?

## 10.3 Para a equipe (E176-1 a E176-4)

**E176-1.** A baixa de título por retorno bancário já traz a instituição do repasse? (Para propor o `ID_Participante_Instituicao_Pagamento` a partir de `Cad_Conta_Bancaria`.)

**E176-2.** A baixa por cartão ou por marketplace chega com a credenciadora? Hoje ela só está na nota (`Mov_Nota_Fiscal_Saida_Pagamento`).

**E176-3.** A entrada em estoque por transferência acontece na entrada física da nota (C170 da filial de destino), ou na saída da origem? (FAQ 16.3.1.19)

**E176-4.** O Motor consegue distinguir produção sem ordem (aviso 1 e Q176-8) de ordem sem apontamento? Pergunta de viabilidade, não de desenho.

# Anexo A. Campos novos e alterados neste documento

| Entidade | Alteração | Campos |
|---|---|---|
| `Cad_Efd_1601_Regra_Uf` | nova | 12 campos (seção 5.4) |
| `Mov_Titulo_Baixa` | 3 campos | `ID_Participante_Instituicao_Pagamento`, `ID_Participante_Intermediador`, `Classe_Incidencia_1601` |
| `Cad_Instituicao_Financeira` | 1 campo | `ID_Participante` |
| `Cad_Filial_Perfil_Fiscal` | 1 campo | `Informa_Ordem_Producao_Bloco_K` |
| `Mov_Nota_Fiscal_Fatura_Comercial` (doc. 175) | 1 campo | `Valor_Titulo_Original` |
| `Mov_Nota_Fiscal_Servico_Nao_Icms` (antes `..._Saida_...`, doc. 175) | renomeada e 1 campo | `Origem_Tipo` no lugar de `ID_Nota` da saída |
| `Mov_Nota_Fiscal_Entrada_Item_Tanque` (doc. 175) | sai | vai ao Bloco 1 de combustíveis |
| `bloco_destino_baixa` | 1 valor | `efd_1601` |
| `Motivo_Reclassificacao` | 4 valores | seção 7.2 |

# Anexo B. Onde cada achado está no FAQ

| Achado | Seção do FAQ |
|---|---|
| 1601 | 17.6.1.1 a 17.6.1.15 |
| Valor bruto e reforma | 19.1, 19.2 e 19.3 |
| C130 | 11.6.1.1 e 11.6.2.1 |
| C165 e C171 | 11.8.1.1, 11.10.1.1 e 11.10.2.1 |
| C178 e COD_ENQ | 11.12.1.1 e 11.9.1.1 |
| C140 | 11.7.1.1 a 11.7.1.3 |
| C420 e C197 | 11.15.2.1, 11.14.1.1 e 11.14.2.1 |
| C500 | 11.17.1.1 a 11.17.5.1 |
| Custo sem crédito (C100 e C170) | 11.13.2.1 |
| K200 | 16.3.1.1 a 16.3.1.20 |
| K220 | 16.4.1.1 a 16.4.1.23 |
| K230 | 16.5.1.1 a 16.5.1.43 |
| K210/K215 | 16.10.1.1 a 16.10.1.8 |
| K260/K265 | 16.11.1.1 a 16.11.1.7 |
| 0220 | 16.12.1.1 |
| K270/K275/K280 | 16.13.1.1 a 16.13.1.7 |
