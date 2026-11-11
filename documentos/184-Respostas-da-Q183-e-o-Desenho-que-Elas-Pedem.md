# Respostas da Q183 e o Desenho que Elas Pedem: Documento 184

*Registra as respostas de Alberto ao documento 183 (09/11/2026) e desenha o que elas exigem: segundo conjunto de valores da moeda funcional, subcontas da Lei 12.973 com o razão auxiliar (RAS), sucessão do plano de contas com o I157, histórico padronizado, relacionamento com o participante e o bloco K da ECD consolidada. Nada foi aplicado ao dicionário (revisão 33); entra no próximo "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. As suas respostas e como as li

Todas as dez perguntas foram respondidas. As leituras abaixo são minhas e ficam como **leituras a confirmar** (perguntas Q184-1 a Q184-14 na seção 10).

| Pergunta | Sua resposta | Como li | Efeito |
|---|---|---|---|
| **Q183-1** | "Sim" | O núcleo da seção 4.1 do documento 183 está aprovado: `Mov_Ecd_Periodo`, `Mov_Ecd_Documento_Complementar`, três campos novos e cinco valores em `Tipo_Inscricao` | Entra no próximo "consolidar" (previstos 1.109 entidades e 12.430 campos) |
| **Q183-2** | "Sim" | A Mlegate entrega o **diário geral (G)**, sem I012 e I015 no arquivo G | Ver a seção 3.5: o arquivo do razão auxiliar (livro Z) leva I012 e I015, derivados |
| **Q183-3** | "Sim a empresas que usam outra moeda" | Há empresa com moeda funcional diferente do real: desenho o segundo conjunto de valores | Seção 2 |
| **Q183-4** | "Sim tem empresa que tem goodwill e aVP" | Desenho o I053 e o RAS com a tabela completa de naturezas | Seção 3 |
| **Q183-5** | "Sim pode mas o I157 é para quando muda o plano de contas até de um ano para outro, e no caso da mudança no meio de um período são enviados 2 sped's..." | A mudança de plano vale entre anos e no meio do período; no meio do período saem **duas ECD**: a do plano antigo e a do plano novo, que começa na data da implantação e leva o de-para do I157 | Seção 4 |
| **Q183-6** | "Sim pode ter histórico padrão" | Histórico padronizado (I075 e `COD_HIST_PAD` do I250) | Seção 5 |
| **Q183-7** | "Tem que ter um local para cadastro destas informações com vigência" | Cadastro do relacionamento com o participante (0180) com vigência. **Não falou do `COD_PART` por partida**: mantive a minha recomendação, **não** | Seção 6 |
| **Q183-8** | "Pode ter bloco K" | O grupo pode fazer escrituração consolidada: desenho o bloco K. **Não falou do 0020**: a escrituração descentralizada continua desligada (`Indicador_Escrituracao_Descentralizada` falso) | Seção 7 |
| **Q183-9** | "Sim" | Mantido: data de encerramento do exercício social e grande porte informados na ECD, com aviso | Valia o campo já proposto no documento 183 |
| **Q183-10** | "sim" | Os 12 avisos do Motor da seção 5 do documento 183 ficam **registrados, sem programar** | Mais os avisos da seção 9 deste documento |

# 2. Moeda funcional: o segundo conjunto de valores (Q183-3)

## 2.1 O que a ECD exige

Com `IDENT_MF = S` (manual, item 1.23), os campos de sempre dos registros I155, I157, I200, I250, I310 e I355 levam os valores **em moeda nacional**, a base que a ECF usa. Os valores da contabilidade em **moeda funcional, convertida para reais**, vão em campos adicionais declarados no I020 (sete campos nomeados pelo manual: `VL_SLD_INI_MF`, `VL_DEB_MF`, `VL_CRED_MF`, `VL_SLD_FIN_MF`, `VL_LCTO_MF`, `VL_DC_MF`, `VL_CTA_MF`, com os indicadores D e C). Os dois conjuntos são em reais e **podem ser diferentes**: no exemplo do manual, o empréstimo em dólar gera variação cambial passiva na contabilidade nacional e nenhum lançamento na funcional, e a máquina fica ao custo histórico na nacional e é convertida pela taxa de fechamento na funcional. Por isso **não basta um segundo saldo**: o lançamento tem dois valores.

## 2.2 O que o dicionário tem hoje

`Mov_Lancamento.Valor_Moeda_Funcional` está **na moeda funcional da empresa** (dólar, no exemplo), e `Mov_Saldo_Contabil` e `Mov_Saldo_Contabil_Dimensao` também. O CTA (`Cad_Conta_Contabil.ID_Tipo_Movimento_CTA` e `ID_Tipo_Saldo_CTA`, `Mov_Lancamento_CTA`) converte a investida para a investidora. Nada guarda o valor em reais pela regra nacional nem o valor funcional já convertido para reais. Em empresa de moeda funcional real, `Valor_Moeda_Funcional` já é o valor em reais e a ECD usa só ele.

## 2.3 Desenho proposto

**Campos novos em `Mov_Lancamento`** (todos opcionais; só empresa com moeda funcional diferente do real):

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **Valor_Moeda_Nacional** | número, opcional | Valor da partida **reconhecido e mensurado em reais** (IN RFB 1.700, arts. 286 e 287). Vai para `VL_DC` do I250. Pode ser zero onde só a contabilidade funcional tem o fato |
| **Valor_Funcional_Em_Reais** | número, opcional | `Valor_Moeda_Funcional` convertido para reais pela regra societária. Vai para `VL_DC_MF` do I250 |
| **Taxa_Conversao_Reais** | número, opcional | A taxa usada na conversão para reais, para a auditoria do valor. Origem: `Cad_Serie_Cotacao` e `Mov_Serie_Cotacao_Valor` |

Regra do Motor (aviso, nunca bloqueio): em cada lote, débitos e créditos fecham **em cada base** (moeda funcional, valor nacional e valor funcional em reais). `VL_LCTO_MF` do I200 é derivado da soma dos débitos da base funcional em reais.

**Entidade nova `Mov_Saldo_Contabil_Base`** (9 campos): o retrato do saldo da conta, e da abertura por centro de custo, em cada base de mensuração. Não mexo em `Mov_Saldo_Contabil`, que continua na moeda funcional da empresa.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Saldo_Contabil_Base** | identificador | --- |
| **ID_Saldo_Contabil** | referência (Mov_Saldo_Contabil) | A conta, a filial e a competência |
| **ID_Saldo_Contabil_Dimensao** | referência (Mov_Saldo_Contabil_Dimensao), opcional | Preenchido quando o saldo é da abertura por centro de custo (I155 com `COD_CCUS`); vazio quando é da conta |
| **Base_Mensuracao** | enumeração {nacional, funcional_em_reais} | Qual conjunto. **Único por (ID_Saldo_Contabil, ID_Saldo_Contabil_Dimensao, Base_Mensuracao)** |
| **Saldo_Inicial** | número | Com sinal, como `Mov_Saldo_Contabil` (positivo é devedor) |
| **Total_Debitos** | número | --- |
| **Total_Creditos** | número | --- |
| **Saldo_Final** | número | `Saldo_Inicial + Total_Debitos − Total_Creditos` |
| **Saldo_Final_Antes_Encerramento** | número, opcional | Para o I355 (`VL_CTA` e `VL_CTA_MF`) |

**Derivados na geração** (sem entidade): os sete campos do I020, o `IDENT_MF` do 0000 (de `Mov_Ecd_Periodo.Indicador_Moeda_Funcional`), a natureza do livro `RAZAO_AUXILIAR_DAS_SUBCONTAS_MF` quando o RAS é da base funcional, e os campos `_MF` do I157 (seção 4).

**Aviso do Motor:** `Cad_Empresa.ID_Moeda_Funcional` diferente do real e `Indicador_Moeda_Funcional` falso na ECD, ou o contrário.

# 3. Subcontas da Lei 12.973, ágio e AVP, e o razão auxiliar (Q183-4)

## 3.1 O que a ECD pede

O **I053** agrupa a conta principal e as subcontas correlatas (`COD_IDT`, de 6 posições, `COD_CNT_CORR` e `NAT_SUB_CNT`, da tabela de 25 naturezas). A subconta é uma **conta analítica do próprio plano**, ligada a uma única conta principal. O **razão auxiliar das subcontas (RAS)** é o livro **Z** (registros I500 a I555), obrigatório só se a empresa for intimada; o G continua como livro principal. No RAS, cada item (bem, direito, obrigação, ou o item da investida no AVJ reflexo) tem o seu razão, com os saldos do item, da subconta e o lançamento.

## 3.2 Naturezas da subconta: domínio, não entidade

As 25 naturezas entram como **domínio novo** `natureza_subconta_ecd` em `Cad_Classe_Sistema`, com o número do manual como código: **2 e 3** (TBU, controlada direta e indireta no exterior), **10** goodwill, **11** mais valia, **12** menos valia, **60** AVJ reflexo, **65** AVJ subscrição de capital, **70 a 73** AVJ (vinculada ao ativo ou passivo, depreciação, amortização e exaustão acumuladas), **75 a 78** AVP (os mesmos quatro papéis), **80, 81, 82, 84, 85 e 86** (mais valia, menos valia e goodwill, e as variações, dos estágios anteriores) e **90 a 93** (adoção inicial). A conta principal de cada natureza (participação societária, ativo, depreciação acumulada) é a coluna do manual e entra como regra de validação do Motor, em aviso.

## 3.3 `Cad_Subconta_Contabil` (mestre com vigência, 9 campos)

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Subconta** | identificador | --- |
| **ID_Subconta_Versao** | identificador da versão | Chave da versão (tabela física `Cad_Subconta_Contabil_Versao`) |
| **ID_Conta_Principal** | referência (Cad_Conta_Contabil) | A conta analítica principal do grupo (a conta controlada pelo RAS) |
| **ID_Conta_Subconta** | referência (Cad_Conta_Contabil) | A conta analítica que é a subconta (`COD_CNT_CORR`). **Uma subconta só pertence a um grupo** |
| **Codigo_Grupo** | código (até 6) | `COD_IDT`: identifica o grupo conta e subcontas; único por conta principal |
| **ID_Natureza_Subconta** | referência (Cad_Classe_Sistema, domínio = natureza_subconta_ecd) | A natureza da tabela do manual |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | --- | O trio de sempre |

## 3.4 Ágio: mais valia e goodwill (`Mov_Agio_Composicao`, 7 campos)

`Mov_Agio` guarda só `Valor_Agio` e `Data_Apuracao`. Pela Lei 12.973 e o Decreto-Lei 1.598 (art. 20), o ágio se divide em **mais valia** (e menos valia) dos ativos líquidos e **goodwill**, cada parte com a sua subconta. A entidade nova abre o ágio nessas partes:

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Agio_Composicao** | identificador | --- |
| **ID_Agio** | referência (Mov_Agio) | O ágio apurado |
| **ID_Natureza_Subconta** | referência (Cad_Classe_Sistema, domínio = natureza_subconta_ecd) | Só 10, 11, 12 e, nos estágios anteriores, 80 a 86 |
| **ID_Item_Subconta** | referência (Mov_Item_Subconta), opcional | O item (bem ou direito) a que a mais ou menos valia se refere; vazio no goodwill |
| **Valor_Composicao** | número | Com sinal: mais valia positiva, menos valia negativa |
| **Data_Laudo** | data, opcional | Data do laudo que sustenta a divisão |
| **ID_Documento_Laudo** | referência (Cad_Documento), opcional | O laudo no GED |

Aviso do Motor: a soma da composição difere de `Valor_Agio`.

## 3.5 RAS: item e movimento

**`Mov_Item_Subconta`** (11 campos) é o item do I510, uma linha por item de uma subconta:

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Item_Subconta** | identificador | --- |
| **ID_Subconta** | referência (Cad_Subconta_Contabil) | A subconta (identidade) |
| **ID_Conta_Item** | referência (Cad_Conta_Contabil), opcional | A conta que registra o item (ativo ou passivo), de onde saem `SLD_ITEM_INI` e `SLD_ITEM_FIN` |
| **ID_Valor_Centro_Custo** | referência (Cad_Dimensao_Contabil_Valor), opcional | `COD_CCUS`, quando aplicável |
| **ID_Investida_Detentora** | referência (Cad_Investida), opcional | `CNPJ_INVTD`; só nas naturezas 60 e 65, e diferente do declarante |
| **Codigo_Item_Patrimonial** | código (até 10) | `COD_PATR_ITEM` |
| **Quantidade** | número, opcional | `QTD` |
| **Identificacao_Item** | texto (até 30), opcional | `IDENT_ITEM`: placa, matrícula, série |
| **Descricao_Item** | texto (até 50) | `DESCR_ITEM` |
| **Data_Reconhecimento** | data | `DATA_RECT_INI`; admite 31/12 do ano quando não se sabe a data |
| **Observacao** | texto, opcional | Livre |

**`Mov_Subconta_Movimento`** (12 campos) é o I550, uma linha por lançamento que mexe no item:

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Movimento_Subconta** | identificador | --- |
| **ID_Item_Subconta** | referência (Mov_Item_Subconta) | O item |
| **ID_Lancamento** | referência (Mov_Lancamento) | A partida da subconta: dela saem `DATA_LCTO`, `NR_LCTO`, `VLR_LCTO` e o indicador |
| **Base_Mensuracao** | enumeração {nacional, funcional_em_reais} | Só importa com moeda funcional (livro `_MF`); sem ela, sempre `nacional` |
| **Saldo_Conta_Inicial** | número | `SLD_ITEM_INI` com sinal (positivo é devedor) |
| **Realizacao_Item** | número, opcional | `REAL_ITEM`: depreciação, alienação, integralização |
| **Saldo_Conta_Final** | número | `SLD_ITEM_FIN` |
| **Saldo_Subconta_Inicial** | número | `SLD_SCNT_INI`: a parcela atribuível ao item |
| **Debito_Subconta** | número | `DEB_SCNT` |
| **Credito_Subconta** | número | `CRED_SCNT` |
| **Saldo_Subconta_Final** | número | `SLD_SCNT_FIN` |
| **Indicador_Adocao_Inicial** | booleano | `IND_ADOC_INI` |

**Derivados na geração:** I500 e I510 (leiaute fixo de 27 colunas, definido pelo manual), I555 (totais), o I030 do livro Z (natureza `RAZAO_AUXILIAR_DAS_SUBCONTAS` ou `_MF`) e o I053 (de `Cad_Subconta_Contabil`).

**A tensão com a Q183-2.** O manual manda o arquivo do livro Z levar o **I012** (livro diário com escrituração resumida) e o **I015** (as contas sintéticas controladas pelo razão) e valida a subconta do I550 contra o I015. Isso **não é o diário auxiliar** que você dispensou na Q183-2: no G continuam fora o I012 e o I015; no Z eles saem **derivados** de `Cad_Subconta_Contabil.ID_Conta_Principal`, sem entidade (pergunta Q184-4).

## 3.6 AVP

O dicionário **não tem** cálculo de ajuste a valor presente (só aparece como valor no retrato da EFD-Contribuições, doc. 44, e como parte do Valor_Titulo em reais do doc. 101). Para o ECD, o AVP entra **como subconta** (naturezas 75 a 78: vinculada ao ativo e as acumuladas) e como lançamento comum. Como "o ERP só registra" (D-N284), **não desenho o cálculo**: a taxa de desconto, o prazo e a apropriação mensal ficam com o contador (Q184-6).

# 4. Mudança do plano de contas e duas ECD (Q183-5)

**Como funciona hoje.** `Cad_Plano_de_Contas_Empresa` tem vigência: um plano novo para a empresa é uma linha nova, em qualquer data. Falta (a) o **de-para** entre as contas do plano antigo e as do novo, que é o I157, e (b) amarrar a ECD ao plano vigente no período dela.

**`Cad_Plano_Contas_De_Para`** (10 campos): uma linha por conta nova que recebe saldo de conta antiga na implantação. Mesmo código no plano antigo e no novo: **sem linha** (e sem I157; a natureza se mantém).

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Conta_De_Para** | identificador | --- |
| **ID_Empresa** | referência (Cad_Empresa) | --- |
| **ID_Plano_Empresa** | referência (Cad_Plano_de_Contas_Empresa) | O plano novo, na empresa (a vigência dele dá a data) |
| **ID_Plano_Empresa_Anterior** | referência (Cad_Plano_de_Contas_Empresa) | O plano antigo |
| **ID_Conta_Anterior** | referência (Cad_Conta_Contabil) | A conta do plano antigo que cede o saldo (`COD_CTA` antiga fica no I157 como origem) |
| **ID_Conta_Nova** | referência (Cad_Conta_Contabil) | A conta do plano novo que recebe |
| **ID_Valor_Centro_Custo** | referência (Cad_Dimensao_Contabil_Valor), opcional | `COD_CCUS` |
| **Data_Implantacao** | data | Primeiro dia do plano novo |
| **Valor_Saldo_Transferido** | número | `VL_SLD_INI` e `IND_DC_INI` (positivo é devedor); em uma conta antiga dividida em várias novas, a parcela de cada |
| **Valor_Saldo_Transferido_Funcional_Em_Reais** | número, opcional | `VL_SLD_INI_MF` e `IND_DC_INI_MF`, só com moeda funcional |

**Campos novos em `Mov_Ecd_Periodo`** (a entidade do documento 183): `ID_Plano_Empresa` (o plano usado no arquivo), `Indicador_Mudanca_Plano_Contas` (`IND_MUDANC_PC`) e `ID_Ecd_Periodo_Anterior` (autorreferência, opcional, para ligar as duas ECD do mesmo exercício). Com mudança no meio do período: a **primeira ECD** vai do início até a **véspera** da implantação, com o plano antigo; a **segunda** começa na `Data_Implantacao`, com o plano novo e o I157. Aviso do Motor: o período do arquivo não coincide com a vigência do plano; I157 faltando onde o código mudou; o saldo inicial do plano novo não fecha com o final do antigo.

# 5. Histórico padronizado (Q183-6)

**`Cad_Historico_Padrao`** (mestre com vigência, 8 campos): `ID_Historico_Padrao`, `ID_Historico_Padrao_Versao`, `ID_Empresa`, `Codigo` (até 60, `COD_HIST`), `Descricao` (texto, `DESCR_HIST`) e o trio de vigência. **Campo novo em `Mov_Lancamento`:** `ID_Historico_Padrao` (referência, opcional, `COD_HIST_PAD` do I250). O `Mov_Lancamento.Historico` passa a ser o **complemento** (`TXT_COMPL_HIST`). O I075 é derivado dos históricos usados no arquivo.

# 6. Relacionamento com o participante (Q183-7)

**`Cad_Participante_Relacionamento`** (mestre com vigência, 8 campos): `ID_Relacionamento`, `ID_Relacionamento_Versao`, `ID_Empresa` (a declarante), `ID_Participante`, `ID_Tipo_Relacionamento` (referência a `Cad_Classe_Sistema`, domínio novo `relacionamento_ecd` com os 11 códigos do 0180: 01 matriz no exterior, 02 filial no exterior, 03 coligada, 04 controladora, 05 controlada, 06 subsidiária integral, 07 controlada em conjunto, 08 entidade de propósito específico, 09 participante do conglomerado, 10 vinculadas do art. 23 da Lei 9.430, 11 localizada em país de tributação favorecida do art. 24) e o trio de vigência. **A vigência da versão é o período do relacionamento**: `Vigencia_Inicio` vira `DT_INI_REL` e `Vigencia_Fim` (31/12/9999 quando em aberto) vira `DT_FIN_REL` vazio. Mudou a relação, nasce versão nova. O 0150 já sai de `Cad_Participante`; o 0180 sai desta tabela. Aviso do Motor: há `Cad_Participacao_Societaria` e não há relacionamento correspondente.

**O `COD_PART` por partida (I250)** não foi respondido; fica **não** (Q184-9): o participante da partida continua pela origem (lote, nota, título), sem campo em `Mov_Lancamento`.

# 7. Bloco K: escrituração consolidada (Q183-8)

## 7.1 O que o manual pede

O bloco K existe quando `0000.IND_ESC_CONS = S`. Traz o **período consolidado** (K030), as **empresas** do conglomerado (K100, com país, código interno de 4 dígitos, CNPJ básico, nome, percentuais de participação e de consolidação, e as datas de entrada e saída), os **eventos societários** do período (K110: 1 aquisição, 2 alienação, 3 fusão, 4 cisão parcial, 5 cisão total, 6 incorporação, 7 extinção, 8 constituição) e as **empresas envolvidas** (K115, condição 1 sucessora, 2 adquirente, 3 alienante, com o percentual do evento), o **plano de contas consolidado** (K200), o **mapa** das contas de cada empresa para ele (K210) e os **saldos consolidados** (K300: agregado, eliminações e consolidado; K310: parcela de cada empresa; K315: parcela de cada eliminação, com a empresa e a conta de contrapartida).

## 7.2 O que reaproveito

Plano consolidado: **`Cad_Plano_de_Contas` e `Cad_Conta_Contabil`**, com um campo novo **`Finalidade`** em `Cad_Plano_de_Contas` (enumeração {individual, consolidado}). A hierarquia, a natureza e o nível já existem. Empresas e percentuais: `Cad_Investida` e `Cad_Participacao_Societaria`. Eventos: `Mov_Ato_Societario`. Eliminações: `Mov_Lancamento_Consolidacao`. O que **não** existe e é preciso gravar: a empresa do conglomerado **sem plano no ERP** (investida no exterior, p. ex.) tem saldos que só entram por lançamento manual, por isso o K310 é gravado e não calculado.

## 7.3 Entidades novas (7)

**`Cad_Conta_Consolidada_Mapa`** (mestre com vigência, 9 campos; o K210): `ID_Mapa`, `ID_Mapa_Versao`, `ID_Conta_Consolidada` (referência a `Cad_Conta_Contabil`, do plano consolidado), `ID_Investida` (referência a `Cad_Investida`), `Codigo_Conta_Empresa` (texto: o código da conta na empresa, que pode não estar no ERP), `ID_Conta_Empresa` (referência a `Cad_Conta_Contabil`, opcional) e o trio de vigência.

**`Mov_Ecd_Consolidacao_Empresa`** (9 campos; o K100): `ID_Ecd_Consolidacao_Empresa`, `ID_Ecd_Periodo` (o arquivo), `Codigo_Empresa` (até 4 dígitos, `EMP_COD`, único no arquivo), `ID_Investida`, `ID_Participacao` (opcional), `Percentual_Participacao` (`PER_PART`), `Percentual_Consolidado` (`PER_CONS`), `Data_Inicio_Empresa` e `Data_Fim_Empresa`. País, CNPJ básico e nome saem de `Cad_Investida`; o indicador `EVENTO` (S ou N) é derivado da existência de evento.

**`Mov_Ecd_Consolidacao_Evento`** (5 campos; o K110): `ID_Evento`, `ID_Ecd_Consolidacao_Empresa`, `Evento` (enumeração {aquisicao, alienacao, fusao, cisao_parcial, cisao_total, incorporacao, extincao, constituicao}), `Data_Evento` (no ano do período) e `ID_Ato_Societario` (opcional).

**`Mov_Ecd_Consolidacao_Evento_Participante`** (5 campos; o K115): `ID_Evento_Participante`, `ID_Evento`, `ID_Ecd_Consolidacao_Empresa` (a envolvida), `Condicao_Participacao` (enumeração {sucessora, adquirente, alienante}) e `Percentual_Evento`. Só para os eventos 1 a 6; a soma dos percentuais do evento não passa de 100.

**`Mov_Ecd_Consolidacao_Saldo`** (6 campos; o K300): `ID_Consolidacao_Saldo`, `ID_Ecd_Periodo`, `ID_Conta_Consolidada`, `Valor_Agregado` (`VAL_AG`), `Valor_Eliminacoes` (`VAL_EL`) e `Valor_Consolidado` (`VAL_CS`), todos com sinal (positivo é devedor).

**`Mov_Ecd_Consolidacao_Saldo_Parte`** (4 campos; o K310): `ID_Saldo_Parte`, `ID_Consolidacao_Saldo`, `ID_Ecd_Consolidacao_Empresa` e `Valor`. A soma das partes é o `Valor_Agregado`.

**`Mov_Ecd_Consolidacao_Eliminacao`** (6 campos; o K315): `ID_Eliminacao`, `ID_Consolidacao_Saldo`, `ID_Ecd_Consolidacao_Empresa` (a empresa da eliminação), `Codigo_Conta_Contrapartida` (texto, `COD_CONTRA`), `Valor` e `ID_Lancamento_Consolidacao` (referência a `Mov_Lancamento_Consolidacao`, opcional, para rastrear a origem). A soma das eliminações é o `Valor_Eliminacoes`.

O K030 sai do período do arquivo, e o K200 do plano consolidado.

**Campo novo em `Mov_Ecd_Periodo`:** `Indicador_Escrituracao_Consolidada` (booleano, `IND_ESC_CONS`). **Avisos do Motor:** o conglomerado no mês 12 (`REGRA_CONGLOMERADO_MES_12`), K115 faltando em evento 1 a 6, evento 7 ou 8 com K115, empresa do K115 fora do K100, conta do K210 fora do K200, agregado diferente da soma das partes.

# 8. Quadro e contagens

| Item | Entidades novas | Campos novos | Campos de referência novos |
|---|---|---|---|
| Moeda funcional: `Mov_Saldo_Contabil_Base` | 1 | 9 | 2 |
| Moeda funcional: 3 campos em `Mov_Lancamento` | 0 | 3 | 0 |
| Subcontas: `Cad_Subconta_Contabil` (mestre) | 1 | 9 | 3 |
| Ágio: `Mov_Agio_Composicao` | 1 | 7 | 4 |
| RAS: `Mov_Item_Subconta` | 1 | 11 | 4 |
| RAS: `Mov_Subconta_Movimento` | 1 | 12 | 2 |
| Plano: `Cad_Plano_Contas_De_Para` | 1 | 10 | 6 |
| Plano: 3 campos em `Mov_Ecd_Periodo` | 0 | 3 | 2 |
| Histórico: `Cad_Historico_Padrao` (mestre) | 1 | 8 | 1 |
| Histórico: 1 campo em `Mov_Lancamento` | 0 | 1 | 1 |
| Relacionamento: `Cad_Participante_Relacionamento` (mestre) | 1 | 8 | 3 |
| Bloco K: `Cad_Conta_Consolidada_Mapa` (mestre) | 1 | 9 | 3 |
| Bloco K: `Mov_Ecd_Consolidacao_Empresa` | 1 | 9 | 3 |
| Bloco K: `_Evento` | 1 | 5 | 2 |
| Bloco K: `_Evento_Participante` | 1 | 5 | 2 |
| Bloco K: `_Saldo` | 1 | 6 | 2 |
| Bloco K: `_Saldo_Parte` | 1 | 4 | 2 |
| Bloco K: `_Eliminacao` | 1 | 6 | 3 |
| Bloco K: `Finalidade` em `Cad_Plano_de_Contas` e `Indicador_Escrituracao_Consolidada` em `Mov_Ecd_Periodo` | 0 | 2 | 0 |
| **Total deste documento** | **15** | **127** | **45** |

**Mestres:** +4 (`Cad_Subconta_Contabil`, `Cad_Historico_Padrao`, `Cad_Participante_Relacionamento` e `Cad_Conta_Consolidada_Mapa`). **Domínios novos em `Cad_Classe_Sistema`:** `natureza_subconta_ecd` (25 valores) e `relacionamento_ecd` (11 valores). **Cargas:** 36 linhas de domínio.

**Previsão com o núcleo do documento 183** (+2 entidades, +24 campos, +8 campos de referência) **e este documento** (+15 entidades, +127 campos, +45 campos de referência), a partir da revisão 33 (1.107 entidades, 12.406 campos, 3.242 campos de referência, 217 mestres): **1.124 entidades, 12.557 campos, 3.295 campos de referência e 221 mestres**. Referências genéricas continuam 61.

# 9. Avisos novos do Motor (registrados, sem programar)

Os avisos já citados nas seções 2 a 7, mais: (1) subconta sem conta principal, ou principal que não é analítica; (2) natureza da subconta incompatível com a conta principal (coluna "conta principal" do manual); (3) item de subconta sem data de reconhecimento; (4) AVJ reflexo sem investida, ou com investida igual à declarante; (5) RAS pedido sem I015 derivado; (6) histórico padrão fora de vigência no lançamento; (7) o relacionamento do 0180 ainda não tem vigência de fim quando a participação acabou; (8) saldo funcional em reais sem taxa de conversão registrada.

# 10. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q184-1** | Aprova as duas bases (`Valor_Moeda_Nacional`, `Valor_Funcional_Em_Reais` e `Taxa_Conversao_Reais` em `Mov_Lancamento`) e a entidade `Mov_Saldo_Contabil_Base` (seção 2)? | **Sim** |
| **Q184-2** | Quem calcula o valor funcional em reais: o ERP sugere pela série de cotação (taxa do dia para resultado, de fechamento para saldos) e o contador confirma, ou o contador lança o valor? | **O ERP sugere e guarda a taxa; o contador confirma** (aviso, nunca bloqueio) |
| **Q184-3** | Quais empresas do grupo têm moeda funcional diferente do real, e qual moeda cada uma? | **Responder** (a lista habilita e confere `Cad_Empresa.ID_Moeda_Funcional`) |
| **Q184-4** | Aprova `Cad_Subconta_Contabil`, o domínio das 25 naturezas, `Mov_Agio_Composicao`, `Mov_Item_Subconta` e `Mov_Subconta_Movimento` (seção 3), com o I012 e o I015 **só no arquivo do livro Z**, derivados, e o G sem eles? | **Sim** |
| **Q184-5** | Quais subcontas as empresas têm hoje: ágio (mais valia, goodwill), AVJ, AVP, adoção inicial, TBU? Há ágio de antes de 2015 (estágios anteriores, naturezas 80 a 86)? | **Responder**; todas as 25 naturezas entram no domínio |
| **Q184-6** | O AVP: só registrar a subconta e o lançamento (o contador calcula), como na regra "o ERP só registra"? | **Sim, sem cálculo** |
| **Q184-7** | Aprova `Cad_Plano_Contas_De_Para` e os três campos novos de `Mov_Ecd_Periodo`; na mudança no meio do período, a primeira ECD termina na **véspera** da implantação e a segunda começa **na data** com o I157? | **Sim** |
| **Q184-8** | Aprova `Cad_Historico_Padrao` por empresa, com vigência, e `ID_Historico_Padrao` em `Mov_Lancamento` (o texto do lançamento vira complemento)? | **Sim** |
| **Q184-9** | Aprova `Cad_Participante_Relacionamento` (a vigência é o período do relacionamento) e confirma que o `COD_PART` por partida **não** entra? | **Sim, e não ao `COD_PART`** |
| **Q184-10** | Aprova as 7 entidades do bloco K, o `Finalidade` do plano e o `Indicador_Escrituracao_Consolidada` (seção 7)? | **Sim** |
| **Q184-11** | Qual empresa é a declarante da escrituração consolidada (a controladora do grupo)? O grupo tem uma só? | **Responder**; uma por `Cad_Grupo_Societario` |
| **Q184-12** | As empresas do conglomerado que não têm plano no ERP (investida no exterior) têm os saldos digitados no K310 por competência? | **Sim** |
| **Q184-13** | O 0020 (escrituração descentralizada) continua desligado, como li? | **Sim, desligado** |
| **Q184-14** | A tabela de cClass da NFGás (seção 11): aprova a carga dos 46 códigos e dos 2 campos novos? | **Sim** |
| **Q184-C1** | (contador) Regra de conversão da moeda funcional para reais na ECD (CPC 02: taxa da data do fato para o resultado, de fechamento para ativo e passivo, e o patrimônio líquido ao histórico)? | Registrar a regra e deixar o contador validar |
| **Q184-C2** | (contador) Em que naturezas o AVP entra como subconta do I053 (75 a 78 só para ativo imobilizado e intangível, ou também para contas a receber e a pagar)? | A confirmar |
| **Q184-C3** | (contador) O mapa provisório dos grupos da NFGás para os campos do C500 (seção 11)? | Provisório até a validação |

# 11. As outras respostas e o material recebido na mesma data

**Q177-1 a Q177-5 ("Sim para todas", 09/11/2026).** A transação de cartão do documento 177 está aprovada: `Mov_Transacao_Cartao` com os **14 campos** (incluindo `Data_Fatura_Cliente`), `ID_Transacao_Cartao` no pagamento da nota e na baixa, `Data_Venda` só sem nota, data de crédito pela regra do Y520 e repasse como o vencimento do título, e o 1601 de cartão com `Data_Autorizacao` e `Valor_Bruto`. **Entra no próximo "consolidar"** (+1 entidade, +16 campos).

**Q158-1 a Q158-13 ("Sim para todas", 09/11/2026).** O documento 158 (B3: compras governamentais, Zona Franca de Manaus e áreas de livre comércio) está aprovado inteiro: 10 entidades novas (155 campos), 5 existentes alteradas (9 campos novos) e 20 valores de domínio; o lado comprador do ente público fica fora (D-N68) e o crédito de IBS da produção fica **provisório** (Q158-9). Pela **Q158-13**, aplica-se **no próximo "consolidar"**.

**Tabela-cClass.xlsx (09/11/2026).** Li como a tabela de cClass da NFGás, que faltava na Q175-9. Tem **46 códigos de 7 dígitos em 11 grupos**: 010 consumo de gás natural (7 códigos), 011 consumo de biometano (7), 020 serviço de distribuição (5), 021 serviços cobráveis (6), 030 cobranças contratuais (5), 060 fatura agregadora (1), 070 demais cobranças (3), 071 acréscimos por mora (3), 072 acréscimos por parcelamento (3), 073 parcelamentos com o principal já tributado (1) e 500 deduções (5). Atributos que **não têm campo**: por grupo, as marcas "valor deduzido" (só o 500), "CBS zero ZFM e ALC" (grupos 021, 070, 073 e 500) e "fatura agregada" (só o 060); por código, o **indicador de continuidade** (0 não se aplica, 1 continuada, 2 não continuada, 3 ambos). No arquivo as colunas de código e de grupo trazem cabeçalhos trocados: usei o conteúdo, e não o rótulo.

**Proposta (Q184-14 e Q184-C3):** (a) carregar os 46 códigos no domínio `classificacao_item_nfgas`; (b) dois campos novos em `Cad_Utilidade_Classificacao_Efd` (`Cbs_Zero_Zfm_Alc` e `Fatura_Agregadora`, booleanos, opcionais) e o indicador de continuidade como atributo do código; (c) o mapa do grupo para o campo do C500, **provisório**: 010, 011 e 020 em fornecimento; 021 e 070 a 072 em despesas acessórias; 500 em outras deduções (dedução); 030, 060 e 073 sem linha, com aviso do Motor. A tabela não diz para qual campo da EFD cada grupo vai: o mapa é **inferência minha**, e o contador valida.

# 12. Limites

O registro I550 e as regras de validação do capítulo 4 do manual foram lidos por amostra; a tabela de eventos e a de condições do K115 estão completas. Não li o texto da IN RFB 1.700 (arts. 286 e 287, 295 a 299): o que digo sobre moeda funcional e adoção inicial vem do manual. A tabela cClass não traz a fonte do arquivo (ato ou nota técnica); a numeração dos grupos e dos códigos é a do arquivo. O cálculo do AVP e a conversão cambial **não** foram desenhados (Q184-6, Q184-C1 e Q184-C2).
