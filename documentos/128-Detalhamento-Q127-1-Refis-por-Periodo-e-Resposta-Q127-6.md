# O Refis por período na ECF (Q127-1), a norma do caixa e a resposta sobre o adiantamento de clientes (Q127-6) — Documento 128

> **Resposta de 27/10/2026 registrada (Q127-6); nada foi aplicado ao dicionário.** Ele continua na **revisão 24** (925 entidades e 10.033 campos). A revisão 25 segue prevista em **929 entidades e 10.099 campos**; as propostas ainda não aprovadas somam **930 e 10.115** (931 e 10.125 com a Q125-1) (**10.118 e 10.128 com o documento 129**, resposta da Q108-1). Este documento detalha a **Q127-1** (você pediu "detalhar Q127-1"), **corrige o documento 127** onde ele contraria o que li, e registra a sua resposta sobre o adiantamento. As perguntas novas são a **Q128-1 a Q128-7**.

# 1. Resumo

- **A minha recomendação da Q127-1 ("vale o `Optante_Refis` do último dia do trimestre") estava incompleta e a retiro.** O manual da ECF diz que, na **exclusão** do Refis, o imposto passa a ser apurado pelo lucro real **a partir do trimestre seguinte ao da exclusão**. Com o último dia, uma exclusão em agosto tiraria o trimestre inteiro do Refis, e o manual diz o contrário.
- **O Refis tem dois grãos na ECF:** o **trimestre** (regime: `FORMA_TRIB_PER`, `IND_RED_ISEN`, `IND_PART_EXT`) e o **mês** (os registros **Y680** e **Y681**, que o manual manda preencher "para os meses em que esteve submetida ao programa"). Uma data de corte só não serve aos dois.
- **Proposta:** `Optante_Refis` com vigência de **datas exatas** (do ingresso à exclusão), sem estrutura nova; o **trimestre** é de Refis se a empresa foi optante em **algum dia** dele; os **meses** do Y680 saem do mesmo período; o `0010.OPT_REFIS` fica **S se houver Refis em algum trimestre do ano** (leitura, com aviso) até o contador responder.
- **O Y680 e o Y681 não estão desenhados** (o documento 88 os deixou fora porque o perfil não tinha o `OPT_REFIS`). O Y681 é **mensal**, com 17 linhas por mês, e o dicionário só tem a apuração **por trimestre**. Proponho **+1 campo** (`Mes_Competencia`, seção 6.5) em `Mov_Ecf_Apuracao_Linha_Valor`.
- **No arquivo de teste (documento 126):** `OPT_REFIS` = S o ano todo, **Y680 dos 12 meses** e **204 linhas de Y681 (12 × 17), todas com valor 0,00**, embora o arquivo tenha receita. O Refis, sozinho, **não** trouxe P130, P230 nem `IND_RED_ISEN` = S.
- **Q127-6 respondida:** o adiantamento de clientes, em caixa, **não entra na apuração do IRPJ e da CSLL ao ser recebido**, só **no primeiro faturamento**, quando é baixado contra o adiantamento e tributado **nessa data**. Para IBS e CBS, **é tributado pelas alíquotas da empresa**. Isso confirma a regra do **art. 223, § 2º, da IN RFB 1.700/2017** (e do P&R 035) e **derruba a linha do adiantamento do documento 127** (seção 3).
- **A IN RFB 1.700/2017:** li o **texto original de 16/03/2017** (as 32 páginas do Diário Oficial que você enviou). O art. 223, § 2º, **confirma a sua resposta da Q127-6** e traz um ponto a mais (**a entrega ou a conclusão antes do faturamento**, Q128-7); o art. 224 prende a CSLL em caixa ao IRPJ em caixa. O **art. 223-A** e as **alterações posteriores a 2017 não estão** nesse texto (seção 4).

# 2. Resposta recebida e como li

| Pergunta | Sua resposta | Como li | O que entra |
|------|------------------------------|----------------------------------------|---------------------------|
| **Q127-6** | "O adiantamento de clientes no regime de caixa para imposto de renda e CSLL ele não entra na apuração do imposto, somente no momento do primeiro faturamento, que será baixado contra o adiantamento nesta data que é tributado. Mas no caso do IBS e CBS ele será tributado pelas alíquotas da empresa" | **IRPJ e CSLL (caixa):** o recebimento do adiantamento **não é receita**; a receita nasce na **aplicação** do adiantamento contra a nota (o "primeiro faturamento"), **na data da aplicação**. Cada aplicação é um fato com data própria (o adiantamento pode cobrir mais de uma nota). **IBS e CBS:** o adiantamento **é tributado**, e a alíquota é a **da empresa**, porque não há item. "Primeiro faturamento" lido como **cada faturamento contra o qual o adiantamento é aplicado**, não só o primeiro | Texto da regra da apuração por caixa (seção 3). **Nenhum campo novo.** O IBS e a CBS do adiantamento: **Q128-6** |

**Ambiguidades que deixo à vista:** (a) "alíquotas da empresa" pode ser a **alíquota padrão do perfil fiscal** ou a **alíquota do local da operação** (no dicionário, a alíquota do IBS e da CBS depende do local, não da empresa); (b) você não disse **quando** o IBS e a CBS incidem sobre o adiantamento (no recebimento, que é a leitura natural de "é tributado", ou na aplicação); (c) a resposta trata de **IRPJ e CSLL**; o **PIS e a Cofins** do adiantamento em caixa não foram tratados.

# 3. Correções do documento 127

| Onde | O que o 127 dizia | O que passa a valer |
|--------------|----------------------------------|---------------------------------------|
| Seção 4.2, linha **Adiantamento de cliente** | Recebido antes da nota, "não tem item, então não tem atividade"; avisa e o contador aloca a atividade (Q127-6, perguntar ao contador) | **O recebimento do adiantamento não conta como receita.** Conta a **aplicação** (`Mov_Credito_Aplicacao`, data em `Data_Aplicacao`) contra o título da nota; a nota **tem itens**, então a atividade vem dos itens, **sem aviso e sem alocação manual**. Fecha a Q127-6 |
| Seção 4.2, linha **Tipo da baixa** | Contam as baixas que extinguem o crédito (dinheiro, encontro de contas, aplicação de crédito) | **Dinheiro** entra na data do recebimento; **aplicação de adiantamento** entra na data da aplicação; o **recebimento do adiantamento** (`Mov_Credito.Data_Credito`) **não** entra. O adiantamento **devolvido** ao cliente nunca foi receita |
| Seção 4.1, regra 2 | "Artigo de portal; não li a norma" | O **art. 214, §§ 1º e 2º**, confirma que a opção pelo **presumido** vale para todo o período de atividade do ano e se manifesta com o pagamento da primeira quota ou da quota única. **O texto não diz** que a escolha entre caixa e competência é anual; isso vem da Solução de Consulta Cosit 88/2019 (citada por um artigo de portal). O ERP mantém o **aviso**, sem bloquear |
| Seção 4.3, caixa para competência | "o artigo que li diz que isso ocorre em dezembro do ano anterior; não li a norma" (e, na regra 3, a coerência com PIS e Cofins) | O **P&R oficial** (pergunta 036, normativo art. 223-A) diz que a pessoa jurídica que passa do caixa para a competência reconhece, **em dezembro do ano-calendário anterior à mudança**, as receitas auferidas e não recebidas. Vale **só entre anos**. A transição por obrigatoriedade do lucro real **no meio do ano** tem regra própria (seção 4). O **art. 223-A não está** no texto de 2017 que li |
| Seção 4.1, regra 3 | "Se caixa, o `Criterio_Escrituracao_Cumulativo` deve ser caixa... o ERP avisa quando divergem" (fonte: portal) | **Art. 224:** a CSLL só pode ficar em caixa se o IRPJ também estiver; o ERP **bloqueia** essa combinação. A ligação com **PIS e Cofins** continua vindo de portal (o texto de 2017 não a traz): **aviso** |
| Seção 4.2, linha **Moeda** | Variação cambial segue o `Criterio_Variacao_Monetaria` | **Art. 215, §§ 27 e 28, e arts. 152 a 155:** liquidação (caixa) como regra; competência por opção, para o ano inteiro; no lucro real a opção é só em janeiro, com DCTF. O campo já existe; se a regra de janeiro vale no presumido: contador |
| Seção 7, limites | "Não li as normas" | **Li o texto original da IN RFB 1.700/2017** (DOU de 16/03/2017); a seção 4 diz o que ele cobre e o que não cobre (art. 223-A e alterações posteriores) |
| Seção 8, **Q127-1** | Recomendação "sim ao último dia" | **Substituída** pela Q128-1 e Q128-2 |
| Seção 8, **Q127-6** | Perguntar ao contador | **Respondida** (seção 2) |

# 4. A IN RFB 1.700/2017: o texto lido

**O que li:** as **32 páginas do Diário Oficial de 16/03/2017** (a publicação original da norma, que você enviou em dois lotes), com os arts. 59, 119, 152 a 155, 214 a 225 e 236. **O que isso não cobre:** as alterações **posteriores** a 2017. O **art. 223-A**, por exemplo, **não está** nesse texto; o que sei dele vem do P&R oficial (pergunta 036). Se algum dispositivo abaixo foi alterado depois, a versão consolidada decide.

| Dispositivo (texto de 2017) | O que diz | Efeito no desenho |
|------------------|------------------------------------|--------------------------|
| **Art. 215, § 9º** | O lucro presumido e o resultado presumido são determinados **pelo regime de competência ou de caixa** | Base do `Criterio_Reconhecimento_Receita` (Q126-3) |
| **Art. 214, §§ 1º a 3º** | A opção pelo **presumido** vale para **todo o período de atividade do ano-calendário**; manifesta-se com o pagamento da **primeira quota ou da quota única** do primeiro período (quem inicia a atividade a partir do 2º trimestre, a do período do início) | Vale para o **regime**; o texto que li **não diz** que a escolha entre caixa e competência é anual (isso vem de uma Solução de Consulta citada por um artigo de portal) |
| **Art. 214, §§ 4º e 5º** | A pessoa jurídica resultante de incorporação ou fusão obrigada ao lucro real não opta pelo presumido, **salvo** se a incorporadora estava no Refis antes do evento | É a única menção ao Refis na norma; o resto vem da Lei 9.964/2000 (via manual da ECF) |
| **Art. 223, caput e § 1º** | Quem adota o caixa e mantém o **Livro Caixa** indica nele, em registro individual, a **nota fiscal de cada recebimento**; quem tem escrituração contábil controla os recebimentos em **conta específica**, com a nota em cada lançamento | **Demonstrativo de recebimentos** do documento 127, seção 4.2 |
| **Art. 223, § 2º** | Valores recebidos **adiantadamente**, por venda de bens ou direitos ou prestação de serviços, são receita **do mês em que se der o faturamento, a entrega do bem ou do direito ou a conclusão dos serviços, o que primeiro ocorrer** | Base da Q127-6. **Entrega ou conclusão antes do faturamento: Q128-7** |
| **Art. 223, § 3º** | Os valores recebidos, **a qualquer título**, do adquirente ou contratante contam como recebimento do preço, **até o limite** do preço | O que passa do preço (juros, multa) não é receita do preço; o contador diz onde entra (127, seção 4.2) |
| **Art. 223, § 4º** | Computar a receita em **período posterior** ao devido sujeita ao IRPJ e à CSLL com **juros de mora e multa** (de mora ou de ofício) | Justifica o **aviso** do ERP quando uma baixa cai no período errado |
| **Art. 224** | A CSLL por resultado presumido **só pode usar o regime de caixa se o IRPJ também usar** | Regra de coerência **IRPJ e CSLL** (127, regra 3): o ERP **bloqueia** CSLL em caixa com IRPJ em competência. A ligação com PIS e Cofins **não está** neste artigo (vem de portal) |
| **Art. 215, §§ 27 e 28; arts. 152 a 155** | A variação cambial dos direitos e obrigações entra na base **na liquidação** (caixa); **à opção**, pela **competência**, **para o ano-calendário inteiro**. No texto do lucro real (art. 153), a opção vale para IRPJ, CSLL, PIS e Cofins juntos, só em **janeiro** (ou no mês do início da atividade) e é **comunicada na DCTF**; voltar ao caixa no meio do ano só com **elevada oscilação cambial** (arts. 155 e 156) | O dicionário **já** tem `Criterio_Variacao_Monetaria` (caixa, competência, caixa por oscilação cambial). Se a regra de janeiro e da DCTF vale também no presumido (o § 28 só diz "todo o ano-calendário"): **contador** |
| **Art. 221, parágrafo único** e **art. 222, parágrafo único** | O IRPJ e a CSLL **retidos na fonte** sobre receitas que integraram a base são **deduzidos** do devido | Apoia a leitura de que a retenção **conta como recebida** (a receita da base é o valor cheio) |
| **Art. 216** | Rendimentos de renda fixa e ganhos de renda variável entram **na alienação, resgate ou cessão** | Não passam pela receita por caixa do documento 127 |
| **Arts. 219 e 220 (com o art. 119)** | Mudança do **real para o presumido**: soma-se o que estava diferido; do **presumido para o real**: o valor justo entra na base do presumido | Fora do desenho; contador |
| **Art. 223-A** | **Não está** no texto de 2017. Pelo P&R oficial (pergunta 036): caixa para competência = reconhece-se em **dezembro do ano anterior** a receita auferida e não recebida; mudança **no meio do ano** por obrigação do lucro real tem regra própria (recalcula o período anterior, paga a diferença sem multa e sem juros) | Seção 4.3 do documento 127 |

**Posição:** com o texto de 2017, o desenho do caixa (documento 127, seção 4) passa a ter **base na norma** para o livro Caixa, o adiantamento, o limite do preço, a coerência IRPJ e CSLL e a variação cambial. **Continuam sem o texto da norma:** o art. 223-A e **qualquer alteração posterior a 2017**; para esses, vale o P&R oficial e a versão consolidada, que o contador confere.

# 5. O Refis na ECF: o que o manual diz

## 5.1 O campo `OPT_REFIS` (registro 0010, campo 3)

Valores `S` ou `N`. O manual manda assinalar o campo quando a empresa é optante pelo Refis (Lei 9.964/2000) **"e que dele não tenha sido excluída"**; quem só tem o Paes (Lei 10.684/2003) ou outros reparcelamentos **não assinala**. O campo é **um valor por arquivo** (um ano-calendário).

## 5.2 A exclusão e o trimestre

No capítulo sobre optantes pelo Refis, o manual diz que as empresas que só podiam ser tributadas pelo lucro real (receita acima do limite, lucros do exterior, benefício fiscal de isenção ou redução, estimativa mensal e outras) puderam optar pelo presumido **durante o período em que submetidas ao Refis**. Na **exclusão**, o IRPJ e a CSLL passam a ser apurados pelo lucro real **a partir do trimestre-calendário seguinte ao da exclusão**. A regra vale para essas empresas; para a empresa que **poderia** ficar no presumido de qualquer forma, o manual não diz que a exclusão muda o regime.

## 5.3 `FORMA_TRIB` e `FORMA_TRIB_PER`

- `FORMA_TRIB` = **3** (Presumido/Real) descreve, entre outros casos, a empresa que **optou pelo presumido por força do ingresso no Refis e foi excluída durante o ano**, passando ao lucro real.
- A observação de `FORMA_TRIB_PER` trata do caso "**houver opção pelo Refis**" com `FORMA_TRIB` 3 ou 4: o período no real deve ser **só trimestral** (`R`) ou **só anual/estimativa** (`E`).

As regras de validação do `FORMA_TRIB_PER` que dependem do `OPT_REFIS`:

| `FORMA_TRIB` | `OPT_REFIS` | `FORMA_APUR` | Letras aceitas por trimestre |
|----------|----------|----------|----------------------|
| 3 | N | qualquer | 0, P, R |
| 3 | S | A (anual) | 0, E, P |
| 3 | S | T (trimestral) | 0, R, P |
| 4 | N | qualquer | 0, A, P, R |
| 4 | S | A | 0, A, E, P |
| 4 | S | T | 0, A, R, P |
| 5 | qualquer | qualquer | 0, P |

**Leitura:** no **trimestral** o `OPT_REFIS` **não muda** as letras aceitas; só no **anual** (`E` no lugar de `R`). O PVA, portanto, **não obriga** `OPT_REFIS` = N no ano da exclusão, e a descrição do `FORMA_TRIB` 3 **pressupõe** `OPT_REFIS` = S nesse ano.

## 5.4 O que o `OPT_REFIS` libera no registro 0020

- **`IND_RED_ISEN` = S** só é aceito com `OPT_REFIS` = S, qualificação 01 (PJ em geral) e `FORMA_TRIB` **5 ou 7**. No ano da exclusão (`FORMA_TRIB` 3) o `IND_RED_ISEN` **tem de ser N**.
- **`IND_PART_EXT` = S** com presumido (`FORMA_TRIB` 5 ou 7) **só é aceito com `OPT_REFIS` = S**. O manual explica: quem tem lucros, rendimentos ou ganhos de capital do exterior só pode ficar no presumido durante o Refis.
- **Y680 e Y681** são exigidos com `OPT_REFIS` = S para quem **não** é imune nem isento; o **Y682** é o equivalente da imune ou isenta (`FORMA_TRIB` 8 ou 9). A empresa do ERP é do presumido, então o **Y682 fica fora**.

## 5.5 Y680 e Y681

- **Y680:** um registro por **mês** (`MES` 01 a 12, até 12 ocorrências), "o mês das informações de optantes pelo Refis". O `MES` tem de cair no período da escrituração (`0000.DT_INI` a `DT_FIN`).
- **Y681 (filho do Y680):** 17 linhas por mês, da tabela dinâmica (códigos 1 a 17: receita de venda de produtos, de revenda, de unidades imobiliárias, da atividade rural, total de vendas, serviços, devoluções, **receita bruta** (linha de cálculo), as linhas 9 e 10 do lucro real, receitas financeiras, participações societárias, SCP, **locação**, outras operacionais, alienações e não operacionais). Quase todas são **editáveis**; só as linhas 5 e 8 são cálculo. O manual diz que o registro vale **"para os meses em que esteve submetida ao programa (indicados no Y680)"**.

# 6. Proposta

## 6.1 Os dois grãos

| Grão | Para quê | Data que decide |
|--------|------------------------------|--------------------------|
| **Período no programa** (datas exatas) | Os meses do Y680/Y681 | Ingresso e exclusão, como entram em `Cad_Empresa_Perfil_Fiscal.Optante_Refis` com vigência |
| **Trimestre** | Regime e validações do 0010 e do 0020 | Regra da seção 6.2 |

`Optante_Refis` (Q126-2, já aprovado, **+1 campo**) fica com **vigência de datas exatas**: `Vigencia_Inicio` = ingresso, `Vigencia_Fim` = exclusão (ou 31/12/9999). **Sem campo novo**: o `Motivo_Vigencia` guarda o ato.

## 6.2 Regra do trimestre

**O trimestre é "de Refis" quando houve Refis em algum dia dele.** Isso cumpre o manual na exclusão (o trimestre da exclusão ainda é do Refis; o seguinte não). **No ingresso no meio do trimestre**, o manual **não diz** nada; a regra acima é leitura minha (**Q128-1**).

## 6.3 O `0010.OPT_REFIS`

- **S** se houve Refis em **algum trimestre do ano-calendário** do arquivo; **N** se não houve nenhum.
- **Apoio:** a descrição do `FORMA_TRIB` 3 e a observação do `FORMA_TRIB_PER` tratam o ano da exclusão com `OPT_REFIS` = S.
- **Contra:** a frase do campo ("e que dele não tenha sido excluída"), lida ao pé da letra, daria **N** no ano da exclusão. Leio essa frase como **"quem nunca esteve no Refis ou já saiu em anos anteriores, não assinala"**, mas **não está escrito assim**. Ponto do contador (**Q128-2**).
- **Efeito no ERP:** o ERP preenche `S` e **avisa** quando o ano é partido (parte dos trimestres com Refis e parte sem), até o contador responder.

## 6.4 As conferências (só aviso, como na Q99-3 e no documento 88)

Com `Optante_Refis` no perfil, entram na tabela da seção 7 do documento 88 (que deixou o Refis fora por falta do campo):

| Conferência | Aviso quando |
|--------------------------|---------------------------------|
| `IND_RED_ISEN` | o indicador é sim e o ano **não** tem Refis, ou a forma de tributação do ano **não** é presumido puro (5 ou 7) |
| `IND_PART_EXT` | o indicador é sim, o regime é presumido e **nenhum** trimestre tem Refis |
| **Y680 e Y681** | o arquivo importado traz meses de Y680 **diferentes dos meses do período no programa**, ou **não traz** Y680 com `OPT_REFIS` = S, ou traz Y680 sem Refis |
| **Exclusão** | a empresa foi excluída e o regime aplicado do **trimestre seguinte** não é o real (**só** quando o contador marcar que ela só podia estar no presumido por causa do Refis; **Q128-5**) |

**Custo:** nenhuma entidade e nenhum campo (texto da regra).

## 6.5 Y680 e Y681 (mensais)

**Y680:** os meses **do período no programa** (`Optante_Refis` = sim em algum dia do mês; leitura, **Q128-3**). Sem armazenar: o ERP gera.

**Y681:** o valor de cada linha, **por mês**. O ERP já tem `Mov_Ecf_Apuracao_Linha_Valor`, mas por **apuração**, e a apuração do presumido é **trimestral**. Duas saídas:

- **A (recomendada):** `Mes_Competencia` (**número 1 a 12, opcional**) em `Mov_Ecf_Apuracao_Linha_Valor`, preenchido **só** nas linhas do Y681; entra na identidade da linha (apuração, linha e mês). **+1 campo.** O contador altera uma linha como já altera as outras (`Eh_Alterado` e `Motivo_Alteracao`).
- **B:** gerar o Y681 sem guardar. O contador **não** consegue corrigir uma linha editável, e o manual a classifica como editável. Não recomendo.

**De onde sai o valor:** do mesmo mecanismo do P130 e do P230 (documento 125), as **contas mapeadas** (`Cad_Ecf_Linha_Mapeamento`, Q125-1, ainda sem resposta), com o movimento do **mês** em vez do trimestre. **Competência ou caixa** segue o critério da empresa (documento 127, seção 4). **Dependência:** se a Q125-1 não for aprovada, o Y681 fica **sem fonte** e o contador digita.

**Observação do arquivo de teste:** o Y681 dos 12 meses está **zerado** apesar da receita do P200. Não sei se é omissão do contador, se o PVA aceita, ou se há outra regra; **Q128-4**.

# 7. O que muda no dicionário (se tudo for aprovado)

| Item | Entidades | Campos |
|--------------------------------------|-----------|--------|
| Revisão 25 prevista (documento 127, sem as propostas pendentes) | 929 | 10.099 |
| Propostas pendentes do documento 127 (Q127-2, Q127-3, Q127-5) | +1 | +15 |
| **`Mes_Competencia` em `Mov_Ecf_Apuracao_Linha_Valor` (Q128-3)** | 0 | **+1** |
| **Total** | **930** | **10.115** |
| Com a entidade de mapeamento do documento 125 (Q125-1) | 931 | 10.125 |

As demais propostas deste documento (regra do trimestre, `OPT_REFIS`, conferências) **não têm campo**.

# 8. Perguntas

| # | Pergunta | Recomendação |
|-----|--------------------------------------------------|---------------------------|
| **Q128-1** | **Regra do trimestre (6.2):** o trimestre é "de Refis" quando a empresa foi optante em **algum dia** dele, com `Optante_Refis` de **datas exatas**? Substitui a recomendação "último dia" da Q127-1 | **Sim.** Cumpre o manual na exclusão. No ingresso no meio do trimestre a regra é leitura minha; o contador confirma |
| **Q128-2** | **`0010.OPT_REFIS` (6.3):** vai **S** se houve Refis em algum trimestre do ano, inclusive no ano da exclusão? | **Sim, com aviso no ano partido,** até o contador responder (**contador**) |
| **Q128-3** | **Y680 e Y681 mensais (6.5):** aprova o `Mes_Competencia` em `Mov_Ecf_Apuracao_Linha_Valor` (**+1 campo**, opção A) e o Y680 gerado com os meses em que a empresa foi optante em algum dia? | **Sim.** O mês da adesão e da exclusão conta como mês no programa (leitura; **contador**) |
| **Q128-4** | **Y681 zerado no arquivo de teste:** o contador sabe se zero é aceito e se é o preenchimento correto? | **Contador.** Enquanto isso o ERP gera os valores das contas mapeadas e **avisa** se o Y681 importado diverge |
| **Q128-5** | **Exclusão e lucro real (6.4):** o ERP avisa quando o regime do trimestre seguinte à exclusão não é o real **apenas** para a empresa que só podia estar no presumido por causa do Refis? Como o ERP sabe disso (um indicador no perfil, ou o contador marca na hora)? | **Contador marca na hora** (sem campo) |
| **Q128-6** | **IBS e CBS do adiantamento (seção 2):** confirma a leitura de que o adiantamento **é tributado no recebimento**, com a **alíquota padrão da empresa**? Ou vale a alíquota do local da operação, como no resto do dicionário? E o PIS e a Cofins do adiantamento em caixa? | **Perguntar** (leituras em aberto). Quando você confirmar, desenho o tratamento em documento próprio; hoje `Mov_Credito` **não tem imposto** |
| **Q128-7** | **Entrega antes do faturamento (seção 4):** o **art. 223, § 2º**, diz que o adiantamento é receita do mês do faturamento, da entrega do bem ou do direito ou da conclusão do serviço, **o que primeiro ocorrer**. Você respondeu "primeiro faturamento". O ERP segue **só a aplicação no faturamento** (sua resposta) ou também a **entrega ou conclusão** quando vier antes (texto da norma)? | **Seguir a norma, se houver evento de entrega ou conclusão no ERP;** sem o evento, o ERP **avisa** quando o faturamento vier depois da entrega. O contador confirma. Hoje o ERP não tem um evento de entrega para essa finalidade |

**Para o contador** (entram no documento 38, seção 2.2): a versão consolidada da IN RFB 1.700/2017 (art. 223-A e alterações posteriores a 2017), a regra de janeiro e da DCTF na variação cambial do presumido, o ingresso no meio do trimestre, o `OPT_REFIS` no ano da exclusão, o mês da adesão e da exclusão no Y680, o Y681 zerado e a entrega antes do faturamento.

# 9. Limites do que li

- **Li o texto original da IN RFB 1.700/2017** (DOU de 16/03/2017), **não** as alterações posteriores nem o **art. 223-A**; para eles, o P&R oficial e a versão consolidada.
- **Não li a Lei 9.964/2000** nem as regras de ingresso e exclusão; só o que o manual diz delas.
- **Não li** as regras da tabela dinâmica do Y681 (arquivo `SPEDECF_DINAMICA_Y681_REGRAS` do programa da Receita); vi só a planilha das tabelas dinâmicas, que dá os códigos e o tipo das linhas.
- **O arquivo de teste é um só** (um ano, uma empresa); o que ele mostra do Refis **não é regra**.
- **Não desenhei** o IBS e a CBS do adiantamento (Q128-6) nem o Y682 (empresa imune ou isenta).
- **Não conferi** na ferramenta da Receita o comportamento do PVA com `OPT_REFIS` = S e Y681 zerado.

# 10. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| Revisão 24 | 925 | 10.033 |
| Revisão 25 prevista (itens já aprovados) | 929 | 10.099 |
| Propostas pendentes (Q127-2, Q127-3, Q127-5, Q128-3) | +1 | +16 |
| **Se tudo for aprovado** | **930** | **10.115** |
| Com a Q125-1 | 931 | 10.125 |
