# Regimes específicos de serviços financeiros, seguro e plano de saúde: o desenho do B4 — Documento 198

> **O que este documento faz.** Você escolheu desenhar o **B4**, o bloco do documento 94 onde nasce a **apuração completa da DeRE** para quem está em regime específico: instituição financeira, seguradora, previdência, capitalização, consórcio, arranjo de pagamento, plano de saúde e os planos funerário e de animais. O documento 96 aprovou só o **valor que o usuário informa** por conta (`Mov_Dere_Linha_Mes`); faltava o que a lei manda calcular: a **aferição mensal da base**, a **base negativa**, as **deduções de cada seção**, a **alíquota fixada em lei**, a **individualização** por segurado, participante, titular e dependente, e o **crédito de quem compra** esses serviços. Eu li as seções I a XVII do Capítulo dos serviços financeiros da LC 214 (arts. 181 a 246, inclusive os artigos novos da LC 227) e o texto correspondente do Decreto 12.955 (arts. 269 a 346), propus onze entidades novas e um catálogo de **92 componentes legais** da base, e anotei três pontos em que o decreto e as decisões que você já tomou **não coincidem**.
>
> **Nada foi aplicado ao dicionário.** Ele continua na revisão 36 (1.144 entidades, 12.860 campos, 3.365 chaves estrangeiras e 353 domínios). A revisão 37, que está em espera pelo seu "consolidar", **não muda** estes números (o documento 160 não cria entidade nem campo). Este documento só entra no dicionário depois das suas respostas à seção 7 e de você mandar "consolidar".

*Fontes: a LC 214/2025 com as alterações da LC 227/2026 (texto consolidado do Planalto, arts. 181 a 246, lidos inteiros) e o Decreto 12.955/2026 (arts. 13, 269 a 346 e 584, lidos inteiros nos trechos citados); o dicionário na revisão 36; os documentos 70, 94, 96 e 116 e as decisões D-N267, D-N272, D-N273, D-N282, D-N284, D-N323 e D-N326. **O leiaute da DeRE (eventos, prazos e pacotes) eu só conheci por fontes secundárias, não oficiais:** não li o manual oficial nem a Tabela 12. Tudo o que vem dessas fontes está marcado como tal.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que achei.** O dicionário tem o **cadastro** (`Cad_Participante_Regime_Especifico`), o **código da Tabela 11** (`Cad_Cod_Trib_Dere`), o **mapeamento de conta** e a **linha mensal informada** (`Mov_Dere_Linha_Mes`), mas **nenhum lugar que diga o que entra na base de cada seção, o que se deduz, qual é a alíquota, nem onde o saldo negativo fica esperando**. O decreto exige tudo isso em lei: a aferição é **mensal** (art. 274), a base negativa pode ser abatida em até **cinco anos** (art. 278), a perda que passa do valor tributável fica de saldo (securitização, faturização e recebíveis), e a seguradora, a entidade de previdência, a sociedade de capitalização e a operadora de saúde têm de **individualizar o valor por pessoa** (arts. 324 e 339).
- **Proposta: 11 entidades novas e 2 campos novos em entidades que já existem.** São **4 cadastros com vigência** (`Cad_Participante_Regime_Base`, `Cad_Componente_Base_Regime`, `Cad_Regime_Aliquota_Soma` e `Cad_Coeficiente_Rateio_Plano_Saude`) e **7 movimentos** (a aferição, o saldo e a sua utilização, a individualização e os dependentes dela, o ativo garantidor e a dedução por documento). Dos oito nomes que o documento 94 listou para o B4, sete viram entidade; `Cad_Regime_Especifico_Parametro` **não é preciso** (o prazo da base negativa vai para `Cad_Parametro_Legal_Ibs_Cbs` e a alíquota para `Cad_Regime_Aliquota_Soma`). O nome `Cad_Deducao_Regime_Especifico`, do documento 70, vira `Cad_Componente_Base_Regime`, porque o catálogo guarda **receitas, deduções e o que não integra a base**, não só deduções.
- **Dois domínios novos** em `Cad_Classe_Sistema`: **`base_regime_especifico`**, com 23 bases de cálculo (as espécies de serviço do art. 182 da LC e do art. 269 do decreto, com o arrendamento dividido em quatro bases, mais o funerário e o de animais), e **`tipo_relacao_dere`**, com 11 papéis de pessoa na DeRE. O domínio de domínios passa de 353 para 355.
- **O catálogo de 92 componentes** (34 receitas, 50 deduções e 8 itens que a lei tira da base) nasce **provisório**, com o artigo da LC e o do decreto em cada linha. Quatro componentes **só o decreto traz** (a LC 214 não os tem) e vão para o contador (C234).
- **Três pontos em que o decreto e o que você decidiu não coincidem** (seção 4, e Q198-3): (a) a **fórmula da base** do art. 274, § 2º, é "por dentro" e não tem redutor, enquanto o dicionário guarda a fórmula da revisão 8 (`(receita − deduções) × redutor`, mantida pela D-N273); (b) em **2026** o art. 584 ainda subtrai o **PIS e a COFINS** da base aferida; (c) na **exportação do seguro** a reversão das deduções é direta, e não proporcional (art. 329, § 1º, II).
- **Perguntas:** Q198-1 a Q198-12 (seção 7), cada uma com recomendação. **Para o contador:** seis perguntas novas, **C233 a C238** (Anexo C), que entram no documento 188.
- **Se você aprovar:** 1.155 entidades (+11), 13.017 campos (+157), 3.404 chaves estrangeiras (+39), 355 domínios (+2), 92 + 14 + 10 linhas de carga e 1 linha de `Cad_Obrigacao_Acessoria` (`DERE`). Os documentos 14 (D-N529) e 38 (seção 1.29) acompanham.

# 2. O que o dicionário já tem para o B4

| Entidade | O que guarda hoje | O que falta para o B4 |
|---|---|---|
| `Cad_Participante_Regime_Especifico` (D-1001) | O regime do participante, com papel principal ou secundário e vigência. O tipo tem `instituicao_financeira`, `plano_saude`, `plano_funerario`, `plano_pet`, `concurso_prognostico`, `emissor_cartao_credito`, `turismo_hotelaria` e outros. | Não tem **seguradora, previdência nem capitalização** (leio como `instituicao_financeira`, seção 5.3) e não diz **em qual base** de cálculo o participante atua. |
| `Cad_Cod_Trib_Dere` (Tabela 11) | O código hierárquico da DeRE (6 a 12 dígitos), com `Tratamento` (tributável, dedutível ou fora do escopo). | Não liga o código ao **componente legal** (qual dedução de qual seção). |
| `Cad_Conta_Contabil_Cod_Trib_Dere` (D-1011) | O mapeamento de conta para `codTrib`, com `Papel_Estimativa` (receita bruta ou dedução) e o tipo de dedução em domínio aberto. | O papel é da **Estimativa da revisão 8**; não diz a base nem o componente da lei. |
| `Cad_Redutor_Base_Dere` | O percentual do redutor por regime, por `codTrib` e por vigência (D-N273). | O decreto **não tem redutor** na aferição (seção 4.2). |
| `Mov_Dere_Linha_Mes` (rev. 24, D-N366) | O valor que o usuário informa por empresa, mês, conta, tipo (base ou dedução) e `codTrib`, com a conferência contra a conta, que **só avisa**. | A **aferição** (a soma por base, a fórmula, o saldo negativo, o débito) e a **individualização**. |
| `Cad_Aliquota` | Alíquotas de CBS e IBS com `Eh_Aliquota_Referencia`, `Eh_Suspensao`, natureza e `Situacao_Dado`. | A **regra da soma** do art. 233 (a lei fixa a **soma**, não cada alíquota) e a **redução sobre a referência** da saúde. |
| `Cad_Parametro_Legal_Ibs_Cbs` | Parâmetros numéricos com vigência e situação do dado. | O prazo de **cinco anos** da base negativa (um parâmetro novo, na carga). |
| `Mov_Escrituracao_Arquivo` | O arquivo de escrituração, o recibo, o hash e o fechamento, por obrigação. | Uma linha de obrigação **DERE** em `Cad_Obrigacao_Acessoria` (hoje não existe). |
| `Cad_Participante_Dependente` e `Mov_Reinf_Rendimento_Plano_Saude` (e as tabelas de dependente e de reembolso) | O lado da **REINF**: titular, dependentes e reembolsos de plano de saúde. | O **valor por pessoa na DeRE** (seção 5.2, `Mov_Dere_Individualizacao`); reaproveito o cadastro de dependente. |
| `Mov_Documento_Fiscal` (`Situacao_Idoneidade_Federal`, D-N272) | O documento fiscal e a situação de idoneidade. | Ligar o documento à **dedução** que ele comprova. |
| `Cad_Participante_Qualificacao_Cbs` (B2) | A qualificação do participante perante a CBS, com `Indicador_Contribuinte_Cbs`. | Nada: é a fonte do campo "o adquirente é do regime regular". |
| `Mov_Apuracao_Tef`, `Mov_Cbs_Apuracao_Espelho` | Precedente de regime específico com apuração própria, e o espelho da apuração mensal da CBS. | Nada: a aferição entrega o débito, e a compensação e o pagamento continuam nesses. |

# 3. O que a lei e o decreto exigem

## 3.1 O que vale para todas as seções

**A aferição é mensal** (Decreto, art. 274, LC 214, art. 300). Nos fornecimentos em que o regulamento **não prevê dedução**, vale a regra geral (art. 13, § 2º: o IBS e a CBS não integram a base). Nos que **preveem dedução**, o art. 274, § 2º, dá a fórmula:

**Base da CBS = [(Faturamento bruto − Deduções previstas) − ISS devido] ÷ (1 + alíquota do IBS + alíquota da CBS)**

O **faturamento bruto** é a receita tributável do período **mais** a CBS e o IBS (o que o fornecedor cobrou do adquirente), e as **deduções previstas** são só as que o regulamento lista. Em **2026**, o art. 584 acrescenta o PIS e a COFINS apurados no período para a seção com dedução como **outra subtração** do numerador. Sem dedução prevista na base, a mesma conta dá o resultado do art. 13, § 2º, então a fórmula serve a todas as bases.

**As deduções valem só para a receita a que estão ligadas** (art. 273, § 3º), só para **operações autorizadas** pelo órgão regulador e dentro dos limites operacionais da legislação própria, e **nunca para despesa administrativa** (art. 276). O que entra na base também inclui, quando a provisão ou a baixa foi deduzida antes, a **reversão de provisões** e a **recuperação de créditos baixados como prejuízo** (art. 273, § 1º). A **despesa de captação** é rateada entre as naturezas de receita das seções III e V, na proporção da receita de cada uma (art. 277).

**Base negativa.** Se a base do mês fica negativa, o contribuinte "poderá deduzir" o valor negativo, **sem atualização**, das bases **positivas** dos períodos seguintes, em até **cinco anos** do último dia útil do período (art. 278 e parágrafo único; no decreto o art. 333 repete a regra para o plano de saúde). A lei diz "poderá": o uso é **opção**, e não automático. Na **securitização, faturização e liquidação antecipada de recebíveis de arranjos** existe outro mecanismo: a **perda no recebimento** que passa do valor tributável do período fica de saldo para os períodos seguintes (LC 214, arts. 193, § 3º, e 219, § 3º), **sem prazo** que eu tenha achado. São dois saldos diferentes, e a seção 4.5 explica por que o dicionário guarda os dois no mesmo lugar.

**Crédito.** Quem está no regime específico apropria crédito nas suas aquisições, **salvo** quando há dedução para o bem ou serviço comprado (art. 279); a apuração do regime não estorna crédito (parágrafo único). É **vedada a dupla dedução e o duplo crédito** (arts. 280 e 335). Do **outro lado**, o adquirente do serviço financeiro toma crédito com base no que o fornecedor informou à Receita e ao CGIBS (LC 214, art. 190; Decreto, art. 275): nas operações remuneradas por **margem**, a "CBS equivalente" ao crédito é calculada por operação e **informada na DeRE**.

**Obrigação acessória.** A entidade presta informação "sobre as operações realizadas, sem prejuízo de um conjunto mínimo" previsto em lei (LC 214, art. 191). O mínimo está nos arts. 324 (seguro, previdência e capitalização) e 339 (saúde), descritos abaixo.

## 3.2 As bases de cálculo, uma a uma

O decreto divide o capítulo em seções por serviço. O quadro resume **quais componentes cada base tem no catálogo** (o detalhe de cada linha, com a condição e o artigo, está no Anexo A). "Sem componente" quer dizer que a base existe no domínio, mas a lei não lista receita nem dedução própria para ela, ou eu não li a seção por inteiro.

| Base (domínio `base_regime_especifico`) | Componentes | O que a lei diz de mais importante |
|---|---|---|
| `credito_cambio_tvm` | 10 | Receita das operações, **sem o principal** no crédito e pela **diferença entre venda e custo** nos títulos. Deduções: captação, despesa de câmbio, perda em títulos, encargo de dívida emitida, perda no recebimento de crédito (a valor de mercado, com as regras do imposto de renda) e assessores e correspondentes (com documento fiscal). Não é receita a operação de crédito entre cooperativa e associado. |
| `securitizacao_faturizacao` | 4 | Deságio e desconto na liquidação antecipada. Deduções: captação, despesa da securitização e **perda no recebimento, com saldo excedente**. |
| `arrend_oper_locacao`, `arrend_oper_alienacao` | 3 e 2 | **Duas bases**, cada uma pela **alíquota do bem** (locação ou venda; imóvel pelo regime específico). Dedução de despesas com documento fiscal, **só na proporção das receitas que não geram crédito ao arrendatário** (art. 295, §§ 1º e 2º). |
| `arrend_fin_parcelas`, `arrend_fin_residual` | 2 e 1 | Parcelas a **valor presente** pela taxa dos encargos financeiros; valor residual garantido pela alíquota da venda do bem, **nunca abaixo do custo** (art. 297, § 3º). A captação só deduz das parcelas. |
| `consorcio` | 2 | Receita **no regime de caixa**; dedução da intermediação com documento fiscal e **individualização do consorciado** quando ele é do regime regular (art. 299, §§ 1º a 3º). |
| `gestao_recursos` | 1 | Totalidade das receitas de gestão e de administração de recursos, **sem dedução prevista** (arts. 302 e 303); o cotista é identificado quando o decreto manda (art. 306). |
| `arranjo_pagamento` | 3 | Remuneração bruta do arranjo e rendimento das contas de pagamento; deduz o **rendimento pago aos titulares das contas** (art. 310, § 5º). |
| `antecipacao_recebivel_arranjo` | 3 | Desconto da antecipação; deduz a **curva DI** pelo prazo e a perda no recebimento, com **saldo excedente** (art. 314). |
| `programa_fidelizacao` | 4 | Art. 219-A da LC 214 (LC 227): os pontos emitidos são a receita; deduz os valores pagos no resgate, o ressarcimento de pontos não utilizados e os pontos usados no fornecimento do próprio emissor (art. 315). |
| `mercado_organizado` | 1 | Valor da operação de fornecimento dos serviços, **sem dedução prevista** (art. 316); o adquirente é identificado conforme o art. 318. |
| `seguro` | 8 | Prêmios e cosseguro aceito **no regime de caixa**; deduz indenização paga (só quando o segurado **não** é do regime regular), restituição, intermediação, cosseguro cedido e a provisão do seguro resgatável (em **base agregada**). |
| `previdencia_complementar` | 11 | Contribuições no regime de caixa, com os rendimentos das aplicações que pagam benefícios **fora da base**, limitados às provisões técnicas (art. 320, § 3º). |
| `capitalizacao` | 9 | Arrecadação em caixa, mais a prescrição e as penalidades; deduz a provisão, os cancelamentos e a intermediação. |
| `plano_saude`, `plano_funerario`, `plano_pet` | 9 cada | A mesma estrutura (o funerário e o pet **remetem** aos arts. 330 a 343): contraprestação em caixa, receita financeira dos ativos garantidores **só na liquidação e na redução das provisões**, e as deduções de custo assistencial, reembolso, restituição, intermediação e administradora. |
| `ativo_virtual` | 1 | Valor do serviço, **sem dedução** (art. 326). |
| `resseguro` | sem componente | **Alíquota zero**, inclusive nos prêmios cedidos ao exterior (LC 214, art. 223, § 4º). |
| `intermediacao_financeira` | sem componente | O valor da operação, pela **mesma alíquota** do serviço intermediado (arts. 325 e 340); o crédito vai para o adquirente que a lei identificar. |
| `fgts`, `protecao_mutualista` | sem componente | Li só em parte o regime do FGTS (art. 308) e **não li** a proteção patrimonial mutualista (LC 227). Entram no domínio para a empresa poder dizer onde atua; o catálogo espera a leitura. |

## 3.3 Seguro, previdência e capitalização

A seguradora, a entidade de previdência (aberta e fechada) e a sociedade de capitalização entregam na DeRE, **no mínimo** (art. 324): a **identificação do segurado**, ou do **estipulante** quando os segurados não são identificados, com o valor do prêmio de cada um; a identificação do **participante** com a contribuição de cada um; e a do **titular, subscritor ou distribuidor** do título com a arrecadação. No **cosseguro** a obrigação é da **seguradora líder**, e no seguro de **apólice coletiva** é do **estipulante** (§ 1º).

A **receita financeira dos ativos garantidores** das provisões técnicas só entra na base **quando o ativo é liquidado ou resgatado** (o rendimento periódico conta como resgate parcial), considerando só o que foi recebido **a partir de 01/01/2027** (art. 319, I, b, e §§ 4º e 5º). No **seguro** ela entra **na proporção** dos prêmios de operações que não geram crédito ao segurado sobre o total dos prêmios. O ativo garantidor é o que está em conta individualizada, junto ao órgão regulador, para o registro de ativos garantidores (§ 4º).

A **indenização** de sinistro só é dedutível quando o segurado **não é contribuinte do regime regular**, só quando **efetivamente paga** no mês (sem provisão nem estimativa), líquida de salvados e ressarcimentos (art. 319, II, a, e § 6º). No cosseguro, o valor recuperado de sinistro entra na proporção do risco assumido por cada seguradora (§ 9º). A **intermediação** só deduz com documento fiscal do intermediário e, quando o segurado é do regime regular, **com a individualização dele na DeRE** (§ 7º); sem ela, a seguradora toma o crédito na parte não deduzida (§ 8º). O seguro **resgatável** deduz a parcela de prêmio que vira provisão, em **base agregada** (§ 10).

## 3.4 Plano de saúde, funerário e de animais

A base (art. 332) tem a contraprestação em caixa e a receita financeira dos ativos garantidores, que só entra quando há, **juntas**, a liquidação ou o resgate **e** a **redução das provisões técnicas** (o total do período contra o do período anterior, na forma da ANS). A dedução é do **custo assistencial** pago no mês: bens e serviços que a operadora adquire direto, **mais os reembolsos** a segurados e beneficiários (§ 5º), com documento fiscal; ficam de fora o fornecimento a alíquota zero (§ 8º) e o reembolso como receita de quem o recebe (§ 7º). A **corresponsabilidade cedida** conta como custo assistencial (§§ 9º e 10).

A operadora entrega na DeRE a **identificação do titular** pessoa física (o detentor principal do vínculo) e os valores de prêmios e contraprestações, **incluindo os dependentes** (art. 339). Nos **planos coletivos em que não há valor por titular**, informa o valor total do contrato, os titulares, a **data de nascimento** deles e dos dependentes, e a alocação segue os **coeficientes de faixa etária** do § 2º, II (0 a 18 anos: 0,17; 19 a 23: 0,21; 24 a 28: 0,25; 29 a 33: 0,29; 34 a 38: 0,33; 39 a 43: 0,38; 44 a 48: 0,42; 49 a 53: 0,50; 54 a 58: 0,67; 59 anos ou mais: 1,00). Nos planos coletivos **por adesão** com administradora de benefícios, a **administradora** responde pela informação (§ 3º). A **autogestão** sem fins lucrativos também entrega a DeRE, e um ato da RFB e do CGIBS pode **dispensá-la**, total ou parcialmente (art. 344, §§ 1º e 2º).

O **crédito do contratante** de plano de saúde para empregados (art. 238, parágrafo único; Decreto, art. 337) é do **lado do tomador** e fica no B0b-2; o B4 só **fornece** a informação que ele precisa (a individualização por titular, com o contratante).

## 3.5 Importação e exportação

**Importação** (LC 214, art. 231; Decreto, art. 328): o serviço financeiro importado paga a mesma alíquota do nacional, com **alíquota zero** quando o importador é do regime regular e teria crédito, e quando é instituição das seções I a V, mantida a dedução da despesa (§ 1º, II e III). Nos serviços **remunerados por margem**, a base leva um **fator de redução** que o ato conjunto da RFB e do CGIBS fixa por espécie de serviço: a **razão entre as deduções e as receitas** das operações no País cujo adquirente **não** é do regime regular nem pessoa jurídica de direito público, medida pela DeRE (§ 5º). Algumas deduções **não entram** nessa conta (as listadas no § 5º, I; no catálogo, é o campo `Considerada_No_Fator_Importacao`). Se a DeRE não estiver disponível, o fator usa outras informações (§ 6º). Para o plano de saúde, o art. 341 repete a ideia, "caso venha a ser permitida a importação".

**Exportação** (LC 214, art. 232; Decreto, art. 329): o serviço prestado a residente no exterior é exportação e fica **imune**. A entidade calcula a **proporção** da receita exportada sobre a receita total da seção e **reverte o efeito das deduções na mesma proporção** (§ 1º, I e III). **No seguro** (art. 269, XI) a reversão é **direta**: reverte-se a dedução das prestações a residentes no exterior (§ 1º, II). As deduções que correspondem à **aquisição de bens e serviços** geram **crédito** no período seguinte, na proporção do que foi revertido (§ 2º). Para o **plano de saúde**, a exportação, se vier a existir, **não é tributável** e as despesas ligadas ao contrato **não são dedutíveis** (art. 342).

## 3.6 A alíquota

Em **2026** a CBS dos serviços financeiros é de **0,9%** (Decreto, art. 480, I; é a alíquota de teste que `Cad_Aliquota` já guarda), e a regra da soma só vale de 2027 em diante. De 2027 a 2033, a lei fixa a **soma** das alíquotas de IBS e CBS dos serviços financeiros: **10,85% em 2027 e 2028; 11,00% em 2029; 11,15% em 2030; 11,30% em 2031; 11,50% em 2032; 12,50% em 2033**, e de **2034 em diante a de 2033** (LC 214, arts. 189 e 233, redação da LC 227). A soma incide sobre o valor **sem IBS, CBS e ISS** (§ 9º), e a CBS e o IBS são divulgados depois (§ 6º), na **proporção das referências** (art. 189, § 2º). Quando o serviço também sofre **ISS**, a soma cai: **2,0 p.p. em 2027 e 2028; 1,8 em 2029; 1,6 em 2030; 1,4 em 2031; 1,2 em 2032** (§ 10; de 2033 em diante a lei não prevê redução). O **resseguro** tem alíquota zero (art. 223, § 4º). O **plano de saúde** e o **funerário** pagam a alíquota de referência de cada ente **reduzida em 60%** (art. 237), e o de **animais domésticos reduzida em 30%** e **sem crédito para o adquirente** (art. 243). No **arrendamento operacional** e no **valor residual** do financeiro, a alíquota é a **do bem** (locação ou venda).

## 3.7 O que sei da DeRE por fonte secundária

O decreto trata a DeRE como obrigação própria (Título II, Capítulo II) mas **não traz o leiaute**. Por fontes **secundárias, não oficiais**, o leiaute tem eventos de **tabelas** (cadastro do participante, mapeamento de conta, ativos garantidores: os D-1001, D-1011 e D-1106 que o dicionário já cita), eventos **periódicos** (aferição e fechamento do mês, com prazo no dia 15 do mês seguinte, segundo essas fontes) e eventos **transacionais** (a partir de 01/01/2027), e um pacote que já passou pelas versões 1.1.0, 1.2.0 e 1.3.0 (esta com o Ato Técnico 6, de 28/09/2026). **Não li o manual oficial nem a Tabela 12.** Por isso as entidades de movimento desta proposta guardam **o que a lei manda saber**, não o formato exato do arquivo; quando você mandar o manual (Q198-12), eu confiro campo a campo e ajusto.

# 4. Achados

**4.1 A fórmula do decreto serve para todas as bases, mas só vale por inteiro para as que têm dedução.** O art. 274, § 1º, separa os fornecimentos **sem** dedução (regra geral do art. 13, § 2º) e **com** dedução (a fórmula "por dentro"). Como a fórmula com dedução igual a zero dá o mesmo resultado da regra geral, o dicionário usa **uma conta só**, e a base sem dedução (ativos virtuais) é um caso particular.

**4.2 O decreto não tem o redutor que o dicionário guarda.** A revisão 8 registrou que a base nos regimes específicos é "flutuante, por margem", com a fórmula `(receita bruta agregada − deduções permitidas acumuladas) × redutor`, e a D-N273 (20/10/2026) **manteve o redutor** como percentual que reduz a base, variável por `codTrib` e por período, e disse que ele "não é trocado pela fórmula por dentro". O decreto (arts. 274, § 2º, e 584) calcula a base **por dentro, sem redutor**; o único **fator de redução** que ele conhece nos serviços financeiros é o da **importação**, por margem presumida, fixado em ato conjunto (art. 328, § 5º; art. 341 para a saúde). **Não mexo no que você decidiu.** A proposta calcula a aferição pelo decreto **ao lado** do redutor, que fica como está, e pergunto duas coisas: a você (Q198-3) se é isso mesmo, e ao contador (C233) se o redutor tem **contrapartida legal** que eu não achei.

**4.3 Em 2026 o PIS e a COFINS saem da base aferida.** O art. 584 (só para 2026, seção com dedução) acrescenta `− PIS − COFINS` ao numerador da fórmula. A D-N273 já tratava a fórmula do art. 584 como "parâmetro anual". Na aferição isso é **um campo** (`Valor_Pis_Cofins_Periodo`), preenchido só em 2026 e zero depois.

**4.4 Na exportação do seguro a reversão é direta.** Nas bases de crédito, câmbio, valores mobiliários, securitização, faturização e nas demais, a reversão é **proporcional** (receita exportada sobre a receita total). No **seguro** o art. 329, § 1º, II, manda reverter **a dedução das prestações a residentes no exterior**, sem proporção. A aferição ganha o campo `Valor_Deducao_Direta_Exportacao`, que só o seguro usa.

**4.5 Base negativa e perda excedente são saldos diferentes e cabem na mesma entidade.** A base negativa (art. 278) dura **cinco anos**, vale para **toda** base e se abate só da **mesma base** (art. 273, § 3º, lido com o art. 278). A perda excedente (LC 214, arts. 193, § 3º, e 219, § 3º) vale **só** para securitização, faturização e recebíveis de arranjos, **sem prazo na lei**. Têm em comum o fato de nascerem de uma aferição e serem abatidos em outra, por valor, sem atualização. Por isso a proposta tem **uma entidade de saldo** com `Tipo_Saldo`, e a data limite só vale para a base negativa.

**4.6 A alíquota de duas bases não é a soma.** O arrendamento operacional e o valor residual do financeiro usam a **alíquota do bem** (art. 201, I, a, b e d). Por isso o arrendamento tem **quatro bases** e `Cad_Regime_Aliquota_Soma` tem a forma `aliquota_do_bem`, em que o Motor lê a alíquota da locação ou da venda do bem e a linha não leva número.

**4.7 O decreto traz quatro componentes que a LC 214 não tem, e a LC revogou um que o decreto ainda cita.** Só o decreto traz: o **fornecimento acessório** das operações de crédito (art. 286, §§ 9º e 10), a **captação** do arrendamento financeiro limitada às parcelas (art. 297, § 4º), e o **excedente de receita financeira sobre as provisões** na previdência (art. 320, § 5º) e na capitalização (art. 323, § 11). Em sentido inverso, a LC 227 **revogou** a dedução da **depreciação** do bem arrendado (art. 201, II, c), mas o decreto ainda diz, no art. 295, § 3º, que ela "implica vedação" do crédito. Vão ao contador (C234).

**4.8 O B4 depende de ligar o `codTrib` ao componente.** A linha mensal que o usuário informa (`Mov_Dere_Linha_Mes`) tem o `codTrib` da Tabela 11, que diz em qual **rubrica da DeRE** o valor entra, mas o dicionário não diz **a qual componente legal** a rubrica corresponde. Sem isso a aferição não sabe se um valor informado é receita, dedução ou item fora da base. A proposta cria o campo opcional `ID_Componente_Base_Regime` em `Cad_Cod_Trib_Dere`; a carga da Tabela 11 é que o preenche.

**4.9 Seguradora e previdência não têm tipo próprio de regime.** `Tipo_Regime_Especifico` tem instituição financeira, saúde, funerário, pet, prognóstico, cartão, turismo e outros, e **não tem seguro, previdência nem capitalização**. A LC 214 trata a seguradora como serviço financeiro (art. 182, XI a XIV). Por **leitura minha**, entram como `instituicao_financeira`, e o que distingue cada uma é a **base** (`Cad_Participante_Regime_Base`). Não acrescento valor ao tipo. Se você preferir um valor por segmento, é uma linha na carga e um texto de campo (Q198-11).

# 5. Proposta

## 5.1 Dois domínios novos

Os dois entram em `Cad_Classe_Sistema` (domínio aberto: valor novo é carga, nunca mudança de estrutura; `Codigo` com até 30 caracteres).

**`base_regime_especifico`** tem **23 valores**, um por base de cálculo da lei: crédito, câmbio e títulos; securitização e faturização; arrendamento operacional (contraprestações e alienação, duas bases); arrendamento financeiro (parcelas e valor residual, duas bases); consórcio; gestão de recursos; arranjos de pagamento; antecipação de recebíveis de arranjos; programas de fidelização; mercados organizados; seguro; resseguro; previdência complementar; capitalização; intermediação; ativos virtuais; FGTS; proteção mutualista; plano de saúde; plano funerário; plano de animais. A lista com o fundamento de cada um está no Anexo B.1. Quando a lei criar outra base, é uma linha de carga.

**`tipo_relacao_dere`** tem **11 valores**, os papéis da pessoa identificada na DeRE: segurado, estipulante, participante de previdência, titular, subscritor e distribuidor de capitalização, titular de plano de saúde, consorciado, cotista de fundo, adquirente de serviço de mercado e tomador de outro serviço financeiro (Anexo B.2).

## 5.2 As onze entidades

| Entidade | Para quê | Vigência | Campos |
|---|---|---|---|
| `Cad_Participante_Regime_Base` | Em quais bases de cálculo do regime o participante atua, com vigência. Uma linha por regime do participante e base. | sim | 9 |
| `Cad_Componente_Base_Regime` | Catálogo legal do que entra na base de cada regime (receita), do que se deduz e do que não integra a base, com as condições de cada item. Substitui o nome Cad_Deducao_Regime_Especifico do documento 70. | sim | 23 |
| `Cad_Regime_Aliquota_Soma` | A regra legal de alíquota do regime, com vigência: a soma de IBS e CBS (art. 233), a redução sobre a referência (saúde, funerário e pet) ou a alíquota zero. | sim | 12 |
| `Cad_Coeficiente_Rateio_Plano_Saude` | Os dez coeficientes por faixa etária que o decreto manda usar para repartir o valor de um plano coletivo sem valor por titular (art. 339, § 2º, II). | sim | 10 |
| `Mov_Regime_Especifico_Afericao` | A aferição mensal de uma base do regime: receitas contra deduções, base negativa, base final e débito de CBS e IBS. Uma linha por empresa, mês e base. | não | 33 |
| `Mov_Regime_Especifico_Saldo_Dedutivel` | O saldo que uma aferição deixa para os meses seguintes: a base negativa (cinco anos, sem atualização) e a perda que passou do valor tributável. | não | 10 |
| `Mov_Regime_Especifico_Saldo_Utilizacao` | O uso de um saldo numa aferição posterior. | não | 7 |
| `Mov_Dere_Individualizacao` | O valor da operação por pessoa que a lei manda informar na DeRE: segurado, participante, titular, cotista, consorciado e outros. Uma linha por empresa, mês, base, pessoa e relação. | não | 20 |
| `Mov_Dere_Individualizacao_Dependente` | Os dependentes do titular na alocação por coeficiente de um plano coletivo. | não | 6 |
| `Mov_Dere_Ativo_Garantidor_Mes` | O ativo que garante a provisão técnica e o que ele rendeu no mês, para a receita financeira tributada na liquidação ou no resgate (evento D-1106, só por fonte secundária). | não | 14 |
| `Mov_Dere_Deducao_Documento` | O documento fiscal que comprova uma dedução do regime, com a pessoa individualizada quando a lei exige. | não | 11 |

Nas quatro com vigência valem as convenções da Fase 0: `ID_X` é a identidade, `ID_X_Versao` a chave da versão, e `Vigencia_Inicio`, `Vigencia_Fim` (31/12/9999 quando em aberto) e `Motivo_Vigencia` fecham cada linha. Nos sete movimentos o que for **calculado** é gravado na própria linha (Q96-17), e o que muda de significado com o tempo (alíquota, o adquirente ser do regime regular) é **gravado no momento**.

### `Cad_Participante_Regime_Base` (Contabilidade & Fiscal, com vigência, 9 campos)

Em quais bases de cálculo do regime o participante atua, com vigência. Uma linha por regime do participante e base.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Regime_Base` | identificador | Chave. |
| `ID_Participante_Regime_Base_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Participante_Regime_Base_Versao). Fase 0, seção 2. |
| `ID_Regime_Especifico` | referência (Cad_Participante_Regime_Especifico) | O regime do participante (D-1001). Identidade, junto com a base. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base de cálculo em que atua. Identidade. Uma seguradora de saúde e vida, por exemplo, tem linhas em seguro, previdência e plano de saúde. |
| `Dispensa_Dere` | enumeração {nenhuma, parcial, total} | Dispensa de entrega da DeRE por ato da RFB e do CGIBS (art. 344, § 2º, para autogestão; outras por ato). Padrão nenhuma. O ERP só avisa. |
| `Fundamento_Dispensa` | texto, opcional | O ato que dispensa. Obrigatório quando a dispensa não é nenhuma (aviso). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Componente_Base_Regime` (Contabilidade & Fiscal, com vigência, 23 campos)

Catálogo legal do que entra na base de cada regime (receita), do que se deduz e do que não integra a base, com as condições de cada item. Substitui o nome Cad_Deducao_Regime_Especifico do documento 70.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Componente_Base_Regime` | identificador | Chave. |
| `ID_Componente_Base_Regime_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Componente_Base_Regime_Versao). Fase 0, seção 2. |
| `Codigo` | código (até 30) --- identidade | Estável, em minúsculas, com o prefixo da base (por exemplo, seg_indenizacao). |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base em que o componente vale. |
| `Descricao` | texto | O que a lei diz, em palavras do dicionário. |
| `Natureza` | enumeração {receita, deducao, nao_integra_base} | Receita compõe a base; dedução a reduz; nao_integra_base é o que a lei tira expressamente da base (rendimentos de aplicações, por exemplo). |
| `Regime_Caixa` | booleano | Entra ou sai só no efetivo recebimento ou pagamento. |
| `Exige_Documento_Fiscal_Idoneo` | booleano | A dedução só vale com documento fiscal idôneo (D-N272). O ERP avisa quando a linha não tem documento. |
| `Exige_Individualizacao_Destinatario` | booleano | Quando o adquirente é contribuinte do regime regular, a dedução depende de ele estar individualizado na DeRE (Decreto, arts. 299, § 2º, 319, § 7º, 323, § 5º, e 325, §§ 2º e 3º). |
| `Limitada_A_Receita_Vinculada` | booleano | A dedução só vale para a receita a que está ligada (Decreto, art. 273, § 3º); vale para todas as deduções, e o campo existe para a carga marcar a exceção, se houver. |
| `Rateio_Por_Natureza_Receita` | booleano | Despesa de captação rateada entre as naturezas de receita (LC 214, art. 202; Decreto, art. 277). |
| `Admite_Saldo_Excedente` | booleano | O que passa do valor tributável do período fica como saldo para os períodos seguintes (LC 214, arts. 193, § 3º, e 219, § 3º). |
| `Base_Agregada` | booleano | Dedução calculada sobre o conjunto da carteira (provisões de seguro resgatável e de previdência). |
| `Restringe_Adquirente_Nao_Regular` | booleano | Vale só para operações cujo adquirente não é contribuinte do regime regular (indenização de seguro; captação e despesa do arrendamento operacional). |
| `Considerada_No_Fator_Importacao` | booleano, opcional | Só nas deduções: se entra no fator de redução da importação de serviço financeiro (Decreto, art. 328, § 5º). Falso nas listadas no inciso I; vazio nas receitas. |
| `Condicao_Texto` | texto, opcional | A condição que o Motor mostra ao usuário (por exemplo, a reversão de provisão só entra se a provisão foi deduzida antes). |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | De onde vem o componente. O que só o Decreto traz vai para o contador. |
| `Fundamento_Legal` | texto | Os artigos, da LC e do Decreto. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Regime_Aliquota_Soma` (Contabilidade & Fiscal, com vigência, 12 campos)

A regra legal de alíquota do regime, com vigência: a soma de IBS e CBS (art. 233), a redução sobre a referência (saúde, funerário e pet) ou a alíquota zero.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regime_Aliquota_Soma` | identificador | Chave. |
| `ID_Regime_Aliquota_Soma_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Regime_Aliquota_Soma_Versao). Fase 0, seção 2. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico), opcional | Vazio: a linha vale para todas as bases de serviço financeiro sem regra própria (art. 189). Preenchido: regra própria da base, que vence a linha geral. |
| `Forma_Fixacao` | enumeração {soma_fixa, reducao_sobre_referencia, aliquota_do_bem} | soma_fixa: a lei fixa a soma de IBS e CBS. reducao_sobre_referencia: a alíquota é a de referência de cada ente menos um percentual. aliquota_do_bem: a base usa a alíquota da locação ou da venda do bem (arrendamento operacional e valor residual); o Motor lê a alíquota do bem, e os números desta linha ficam vazios. |
| `Soma_Aliquotas` | número, opcional | A soma de IBS e CBS, em pontos percentuais, sobre o valor sem IBS, CBS e ISS (art. 233, § 9º). Só em soma_fixa. |
| `Percentual_Reducao_Referencia` | número, opcional | 60 na saúde e no funerário, 30 no pet. Só em reducao_sobre_referencia. |
| `Reducao_Soma_Com_Iss_Pontos` | número, opcional | Pontos percentuais tirados da soma quando o serviço também sofre ISS (art. 233, § 10). Vazio onde a lei não reduz. |
| `Fundamento_Legal` | texto | O artigo que fixa o número. |
| `Situacao_Dado` | enumeração {provisorio, validado} | Provisória até o contador validar; a CBS e o IBS publicados podem diferir (art. 233, § 6º). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Coeficiente_Rateio_Plano_Saude` (Contabilidade & Fiscal, com vigência, 10 campos)

Os dez coeficientes por faixa etária que o decreto manda usar para repartir o valor de um plano coletivo sem valor por titular (art. 339, § 2º, II).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Coeficiente_Rateio` | identificador | Chave. |
| `ID_Coeficiente_Rateio_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Coeficiente_Rateio_Versao). Fase 0, seção 2. |
| `Idade_Inicial` | número | Primeira idade da faixa, em anos completos. |
| `Idade_Final` | número, opcional | Última idade da faixa; vazia na faixa de 59 anos ou mais. |
| `Coeficiente` | número | O coeficiente de alocação (0,17 a 1). |
| `Fundamento_Legal` | texto | Decreto 12.955, art. 339, § 2º, II, alíneas a a j. |
| `Situacao_Dado` | enumeração {provisorio, validado} | Provisório até o contador validar. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Regime_Especifico_Afericao` (Contabilidade & Fiscal, sem vigência, 33 campos)

A aferição mensal de uma base do regime: receitas contra deduções, base negativa, base final e débito de CBS e IBS. Uma linha por empresa, mês e base.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Afericao` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | Identidade. |
| `ID_Periodo_Referencia` | referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade) --- identidade | Identidade. O mês da aferição. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) --- identidade | Identidade. A base de cálculo aferida. |
| `Valor_Faturamento_Bruto` | número | Calculado: soma dos valores base das linhas de receita da base (Mov_Dere_Linha_Mes), como o usuário informou, já com IBS e CBS (Decreto, art. 274, § 2º). |
| `Valor_Deducoes_Previstas` | número | Calculado: soma das deduções da base. Só as deduções do catálogo; a diferença com a conta aparece na conferência da linha. |
| `Valor_Iss_Operacao` | número | O ISS devido no fornecimento, informado pelo usuário. Zero quando a base não sofre ISS. |
| `Valor_Pis_Cofins_Periodo` | número | Só em 2026 (Decreto, art. 584): o PIS e a COFINS apurados no período para a base, que saem do valor aferido. Zero de 2027 em diante. Parâmetro anual (D-N273). |
| `Aliquota_Ibs_Aplicada` | número | Gravada na aferição: a alíquota do IBS do mês (Cad_Aliquota da base, ou a soma do art. 233 repartida pela proporção das referências). |
| `Aliquota_Cbs_Aplicada` | número | Idem, para a CBS. |
| `Valor_Base_Calculo` | número | Calculado: [(Faturamento bruto − receita de exportação) − (deduções − reversão) − ISS − PIS e COFINS (só 2026)] ÷ (1 + alíquota do IBS + alíquota da CBS) (Decreto, arts. 274, § 2º, e 584). Sem dedução prevista na base, o resultado é o do art. 13, § 2º. Pode ficar negativo; não leva Com_Sinal (o sufixo vale só para a ECF, D-N326). Leitura minha da exportação: contador, C233. |
| `Valor_Base_Negativa_Gerada` | número | Calculado: o valor negativo da base do mês, que vira saldo (Mov_Regime_Especifico_Saldo_Dedutivel). Zero quando a base é positiva. |
| `Valor_Saldo_Base_Negativa_Utilizado` | número | Calculado: soma das utilizações de base negativa neste mês. Não passa da base positiva (aviso). |
| `Valor_Perda_Excedente_Gerada` | número | Calculado: a perda de crédito que passou do valor tributável do mês, nas bases que admitem saldo (securitização, faturização e recebíveis de arranjos). |
| `Valor_Saldo_Perda_Utilizado` | número | Calculado: soma das utilizações de perda excedente neste mês. |
| `Valor_Base_Final` | número | Calculado: base do mês menos as utilizações de base negativa e de perda excedente; nunca abaixo de zero. |
| `Valor_Cbs_Debito` | número | Calculado: base final vezes a alíquota da CBS. |
| `Valor_Ibs_Debito` | número | Calculado: base final vezes a alíquota do IBS. |
| `Valor_Receita_Exportacao` | número | Parte da receita que é exportação de serviço financeiro (imune; LC 214, art. 232). |
| `Proporcao_Exportacao` | número | Calculado: receita de exportação sobre a receita total da base. |
| `Valor_Deducao_Direta_Exportacao` | número, opcional | Só na base de seguro: a dedução ligada às prestações a residentes no exterior, informada pelo usuário (Decreto, art. 329, § 1º, II). Vazio nas demais bases, que usam a proporção. |
| `Valor_Reversao_Deducoes_Exportacao` | número | Calculado: nas bases de crédito, câmbio, valores mobiliários, securitização, faturização, arrendamento e demais, as deduções vezes a proporção de exportação; no seguro, a dedução direta. O efeito dessa parte das deduções é revertido (LC 214, art. 232, § 1º; Decreto, art. 329, § 1º). |
| `Valor_Provisoes_Tecnicas_Periodo` | número, opcional | Total das provisões técnicas no fim do período; só nos planos de saúde, para a regra da receita financeira liquidada. |
| `Valor_Provisoes_Tecnicas_Anterior` | número, opcional | Total das provisões técnicas no período imediatamente anterior. |
| `Valor_Total_Individualizado` | número | Calculado: soma de Valor_Operacao das individualizações da base no mês. |
| `Valor_Diferenca_Individualizacao` | número | Calculado: total individualizado menos a receita da base. Só avisa. |
| `Possui_Diferenca_Individualizacao` | booleano | Ligado quando a diferença não é zero e a base exige individualização. |
| `Tem_Parametro_Provisorio` | booleano | Verdadeiro se algum componente ou alíquota usado está provisório. |
| `Situacao` | enumeração {em_elaboracao, calculada, fechada} | fechada é a confissão do valor do débito no fechamento mensal da DeRE. |
| `Data_Hora_Calculo` | data/hora, opcional | Quando o ERP calculou. |
| `ID_Escrituracao_Arquivo` | referência (Mov_Escrituracao_Arquivo), opcional | O arquivo da DeRE que levou esta aferição, com o recibo. |
| `ID_Usuario_Fechamento` | referência (Cad_Usuario), opcional | Quem fechou. |
| `Data_Hora_Fechamento` | data/hora, opcional | Quando fechou. |

### `Mov_Regime_Especifico_Saldo_Dedutivel` (Contabilidade & Fiscal, sem vigência, 10 campos)

O saldo que uma aferição deixa para os meses seguintes: a base negativa (cinco anos, sem atualização) e a perda que passou do valor tributável.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Saldo` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base do saldo; o saldo só abate a mesma base (Decreto, art. 273, § 3º, lido com o art. 278). |
| `Tipo_Saldo` | enumeração {base_negativa, perda_excedente} | base_negativa: Decreto, arts. 278 e 333. perda_excedente: LC 214, arts. 193, § 3º, e 219, § 3º. |
| `ID_Afericao_Origem` | referência (Mov_Regime_Especifico_Afericao) | A aferição que gerou o saldo. |
| `Valor_Original` | número | O valor gerado, sem atualização. |
| `Valor_Utilizado` | número | Calculado: soma das utilizações. |
| `Valor_Saldo` | número | Calculado: original menos utilizado. |
| `Data_Limite_Aproveitamento` | data, opcional | Base negativa: cinco anos a partir do último dia útil do período (parâmetro com vigência). Vazia na perda excedente, que a lei não limita. |
| `Situacao` | enumeração {aberto, esgotado, expirado} | expirado: passou a data limite com saldo. |

### `Mov_Regime_Especifico_Saldo_Utilizacao` (Contabilidade & Fiscal, sem vigência, 7 campos)

O uso de um saldo numa aferição posterior.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Saldo_Utilizacao` | identificador | Chave. |
| `ID_Saldo` | referência (Mov_Regime_Especifico_Saldo_Dedutivel) | O saldo usado. |
| `ID_Afericao_Destino` | referência (Mov_Regime_Especifico_Afericao) | A aferição que abateu o saldo. |
| `Valor_Utilizado` | número | Quanto abateu. Não passa do saldo nem da base positiva (aviso). |
| `Origem_Alocacao` | enumeração {sugerida_mais_antiga, manual} | A lei diz "poderá deduzir"; o ERP sugere o saldo mais antigo primeiro e o usuário pode trocar. |
| `ID_Usuario_Informacao` | referência (Cad_Usuario) | Quem confirmou. |
| `Data_Hora_Informacao` | data/hora | Quando confirmou. |

### `Mov_Dere_Individualizacao` (Contabilidade & Fiscal, sem vigência, 20 campos)

O valor da operação por pessoa que a lei manda informar na DeRE: segurado, participante, titular, cotista, consorciado e outros. Uma linha por empresa, mês, base, pessoa e relação.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Dere_Individualizacao` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | Identidade. |
| `ID_Periodo_Referencia` | referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade) --- identidade | Identidade. O mês. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) --- identidade | Identidade. |
| `ID_Participante` | referência (Cad_Participante) --- identidade | A pessoa identificada. |
| `ID_Tipo_Relacao` | referência (Cad_Classe_Sistema, domínio = tipo_relacao_dere) --- identidade | O papel da pessoa (segurado, titular de plano de saúde e os demais do domínio). |
| `ID_Participante_Contratante` | referência (Cad_Participante), opcional | O estipulante da apólice coletiva ou o contratante do plano coletivo. É por ele que o empregador identifica o crédito do plano de saúde dos empregados (B0b-2). |
| `Numero_Contrato` | código (até 60), opcional | Apólice, contrato, título ou plano. |
| `Papel_Cosseguro` | enumeração {lider, aceitante}, opcional | No cosseguro, quem individualiza é a seguradora líder (Decreto, art. 324, § 1º). Vazio fora do cosseguro. |
| `Valor_Operacao` | número | O prêmio, a contribuição, a arrecadação ou a contraprestação da pessoa no mês. |
| `Valor_Deducao_Vinculada` | número, opcional | A dedução (intermediação) ligada a esta pessoa, quando o componente exige individualização. |
| `Valor_Cbs_Equivalente` | número, opcional | A CBS que corresponde à operação, para o crédito do adquirente (LC 214, art. 190). Vazio quando o adquirente não toma crédito. |
| `Valor_Ibs_Equivalente` | número, opcional | Idem, para o IBS. |
| `Adquirente_Regime_Regular` | booleano | Gravado no momento: o adquirente é contribuinte do regime regular (lido de Cad_Participante_Qualificacao_Cbs e do perfil fiscal). Decide a dedução da intermediação e a indenização do seguro. |
| `Adquirente_Direito_Publico` | booleano | Gravado no momento: pessoa jurídica de direito público (entra na conta do fator de redução da importação, art. 328, § 5º). |
| `Origem_Valor` | enumeração {individual, alocado_por_coeficiente, alocado_proporcional} | Plano coletivo sem valor por titular: alocado_por_coeficiente (faixa etária). Contrato sem individualização: alocado_proporcional. |
| `Data_Nascimento_Considerada` | data, opcional | Gravada na alocação por coeficiente, para a conta poder ser refeita. |
| `ID_Coeficiente_Rateio` | referência (Cad_Coeficiente_Rateio_Plano_Saude), opcional | A faixa usada no titular. |
| `ID_Usuario_Informacao` | referência (Cad_Usuario) | Quem informou. |
| `Data_Hora_Informacao` | data/hora | Quando informou. |

### `Mov_Dere_Individualizacao_Dependente` (Contabilidade & Fiscal, sem vigência, 6 campos)

Os dependentes do titular na alocação por coeficiente de um plano coletivo.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Individualizacao_Dependente` | identificador | Chave. |
| `ID_Dere_Individualizacao` | referência (Mov_Dere_Individualizacao) | A linha do titular. |
| `ID_Dependente` | referência (Cad_Participante_Dependente) | O dependente. A mesma entidade do REINF (Mov_Reinf_Rendimento_Plano_Saude_Dependente). |
| `Data_Nascimento_Considerada` | data | Gravada na alocação. |
| `ID_Coeficiente_Rateio` | referência (Cad_Coeficiente_Rateio_Plano_Saude) | A faixa do dependente. |
| `Valor_Alocado` | número | A parte do valor do contrato que cabe ao dependente. |

### `Mov_Dere_Ativo_Garantidor_Mes` (Contabilidade & Fiscal, sem vigência, 14 campos)

O ativo que garante a provisão técnica e o que ele rendeu no mês, para a receita financeira tributada na liquidação ou no resgate (evento D-1106, só por fonte secundária).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Ativo_Garantidor_Mes` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | Identidade. |
| `ID_Periodo_Referencia` | referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade) --- identidade | Identidade. |
| `ID_Conta_Contabil` | referência (Cad_Conta_Contabil) --- identidade | A conta do ativo. |
| `Identificacao_Ativo` | texto (60) --- identidade | O código do título, do fundo ou da aplicação, como a empresa o identifica. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base cuja provisão o ativo garante (seguro, previdência, capitalização ou plano de saúde). |
| `Valor_Saldo_Inicial` | número | Saldo no começo do mês. |
| `Valor_Rendimento_Periodico` | número | Rendimentos periódicos recebidos; contam como resgate parcial. |
| `Valor_Variacao_Mensal` | número | Variação do valor no mês. |
| `Valor_Principal_Liquidado` | número | Principal liquidado ou resgatado. |
| `Valor_Rendimento_Liquidacao` | número | Rendimento na liquidação ou no resgate. |
| `Valor_Saldo_Final` | número | Calculado: saldo inicial mais variação menos principal liquidado. |
| `Proporcao_Premios_Sem_Credito` | número, opcional | Só na base de seguro: prêmios de operações que não geram crédito ao segurado sobre o total dos prêmios do período (Decreto, art. 319, I, b). Vazio nas demais bases. |
| `Valor_Apurado` | número | Calculado: rendimentos periódicos mais rendimento na liquidação, vezes a proporção no seguro. O usuário leva este valor à linha da DeRE da receita financeira; só avisa se diferente. |

### `Mov_Dere_Deducao_Documento` (Contabilidade & Fiscal, sem vigência, 11 campos)

O documento fiscal que comprova uma dedução do regime, com a pessoa individualizada quando a lei exige.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Dere_Deducao_Documento` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa. |
| `ID_Periodo_Referencia` | referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade) | O mês. |
| `ID_Componente_Base_Regime` | referência (Cad_Componente_Base_Regime) | A dedução do catálogo. |
| `ID_Documento_Fiscal` | referência (Mov_Documento_Fiscal), opcional | O documento que comprova. Vazio quando o comprovante não está no ERP (reembolso a beneficiário); nesse caso vale a descrição. |
| `Descricao_Comprovante` | texto, opcional | O comprovante, quando não há documento no ERP. Obrigatória sem documento (aviso). |
| `Valor_Deduzido` | número | A parte do documento que entra como dedução. |
| `ID_Participante_Destinatario` | referência (Cad_Participante), opcional | Quando o componente exige individualização, o adquirente a quem a dedução se liga. |
| `Documento_Idoneo_No_Registro` | booleano, opcional | Gravado no momento: a situação de idoneidade do documento (Situacao_Idoneidade_Federal). Vazio sem documento. |
| `ID_Usuario_Informacao` | referência (Cad_Usuario) | Quem informou. |
| `Data_Hora_Informacao` | data/hora | Quando informou. |

## 5.3 O que muda em entidades que já existem

| Entidade | Mudança |
|---|---|
| `Cad_Cod_Trib_Dere` | **+ `ID_Componente_Base_Regime`** (opcional): o componente do catálogo a que o `codTrib` pertence. É assim que a linha mensal informada entra na base certa da aferição. |
| `Cad_Aliquota` | **+ `ID_Base_Regime`** (opcional): a base a que a CBS ou o IBS publicado para o regime se aplica. |
| `Cad_Classe_Sistema` | O campo `Dominio` ganha os valores **`base_regime_especifico` e `tipo_relacao_dere`** (texto do campo, sem campo novo). |
| `Cad_Participante_Regime_Especifico.Tipo_Regime_Especifico` | **Só texto:** seguradora, entidade de previdência e sociedade de capitalização entram como `instituicao_financeira` (leitura minha, seção 4.9); a base distingue. |
| `Cad_Redutor_Base_Dere` | **Só texto:** o redutor continua como está (D-N273); o decreto só conhece "fator de redução" na importação (art. 328, § 5º), e a aferição do B4 não usa o redutor (Q198-3). |
| `Cad_Obrigacao_Acessoria` e `Cad_Parametro_Legal_Ibs_Cbs` | **Só carga:** a obrigação `DERE` e o parâmetro `prazo_base_negativa_regime_anos` (cinco anos). |

## 5.4 Como a aferição é calculada

O Motor faz a aferição de uma base, em um mês, nesta ordem. O ERP **calcula, grava e avisa; não bloqueia**.

1. **Junta as linhas do mês.** Lê `Mov_Dere_Linha_Mes` da empresa e do mês (o valor que o usuário informou, Q96-1), chega ao componente pelo `codTrib` (`Cad_Cod_Trib_Dere.ID_Componente_Base_Regime`) e soma as linhas de **receita** em `Valor_Faturamento_Bruto` e as de **dedução** em `Valor_Deducoes_Previstas`. Linha sem componente fica fora da conta e **gera aviso**. As deduções por documento (`Mov_Dere_Deducao_Documento`) entram na mesma soma.
2. **Grava a alíquota.** Lê `Cad_Regime_Aliquota_Soma` da base e do mês (a base própria vence a regra geral) e as alíquotas publicadas em `Cad_Aliquota` (com `ID_Base_Regime`), e grava `Aliquota_Ibs_Aplicada` e `Aliquota_Cbs_Aplicada`. Se a soma das duas não bate com a soma legal, **avisa**. Nas bases `aliquota_do_bem`, lê a alíquota da locação ou da venda do bem. **Em 2026** não há linha de soma: vale a alíquota de teste de `Cad_Aliquota` (CBS 0,9%, Decreto, art. 480, I).
3. **Separa a exportação.** Com `Valor_Receita_Exportacao`, calcula `Proporcao_Exportacao` e `Valor_Reversao_Deducoes_Exportacao` (proporcional; no seguro, a dedução direta informada).
4. **Calcula a base**: `[(faturamento bruto − receita de exportação) − (deduções − reversão) − ISS − PIS e COFINS (só 2026)] ÷ (1 + alíquota do IBS + alíquota da CBS)`. O resultado **pode ser negativo**.
5. **Gera ou usa saldo.** Base negativa vira linha de saldo `base_negativa` com data limite de cinco anos; perda que passa do valor tributável, nas bases que admitem saldo, vira `perda_excedente`. Utilizações de saldo anteriores são abatidas e gravadas em `Mov_Regime_Especifico_Saldo_Utilizacao` (a sugestão é o saldo mais antigo, e o usuário troca).
6. **Fecha a base final** (nunca abaixo de zero) e calcula `Valor_Cbs_Debito` e `Valor_Ibs_Debito`.
7. **Confere a individualização.** Soma `Mov_Dere_Individualizacao` da base e do mês, compara com a receita e liga `Possui_Diferenca_Individualizacao` se houver diferença onde a lei exige individualizar.
8. **Marca o que é provisório.** `Tem_Parametro_Provisorio` fica ligado se algum componente ou alíquota usado ainda não foi validado pelo contador.
9. **Fecha.** `Situacao` passa de `em_elaboracao` a `calculada` e a `fechada`; `fechada` é a **confissão do débito** no fechamento mensal da DeRE, ligada ao arquivo (`ID_Escrituracao_Arquivo`).

## 5.5 Aferição, apuração e pagamento

O B4 entrega o **débito de CBS e de IBS por base e mês**. O que acontece depois **não é do B4**: a compensação com créditos e o pagamento seguem no espelho da apuração (`Mov_Cbs_Apuracao_Espelho`) e na Plataforma, e o split payment só começa em 2028 (D-N282). O ERP **não gera guia própria** de regime específico até um ato dizer como (Q198-10).

# 6. Regras de texto: o que o Motor avisa

Nenhuma regra bloqueia; todas gravam o aviso na linha e mostram a mensagem ao usuário (D-N284 e a decisão de 21/10/2026: "o ERP avisa, não bloqueia").

| # | Regra | Onde avisa |
|---|---|---|
| 1 | Linha mensal da DeRE com `codTrib` sem componente | `Mov_Dere_Linha_Mes` |
| 2 | Dedução que **exige documento fiscal idôneo** sem documento e sem descrição do comprovante | `Mov_Dere_Deducao_Documento` |
| 3 | Dedução de **intermediação** cujo adquirente é do regime regular e não está individualizado (a dedução não vale e o crédito do fornecedor segue a parte não deduzida) | `Mov_Dere_Deducao_Documento` |
| 4 | **Indenização de seguro** dedutível com segurado do regime regular (art. 319, II, a) | `Mov_Dere_Individualizacao` e aferição |
| 5 | Dedução acima da receita **vinculada** (art. 273, § 3º) ou de despesa administrativa (art. 276, texto do componente) | `Cad_Componente_Base_Regime.Condicao_Texto` |
| 6 | Utilização de saldo **maior que o saldo** ou que a base positiva | `Mov_Regime_Especifico_Saldo_Utilizacao` |
| 7 | Saldo de base negativa **passou da data limite** (marca `expirado`) | `Mov_Regime_Especifico_Saldo_Dedutivel` |
| 8 | Soma individualizada **diferente** da receita da base (onde a lei exige individualizar) | aferição |
| 9 | Componente ou alíquota **provisório** usado na aferição | aferição (`Tem_Parametro_Provisorio`) |
| 10 | Participante com regime específico **sem base** em `Cad_Participante_Regime_Base` | cadastro |
| 11 | Dispensa de DeRE **sem fundamento** (ato da RFB e do CGIBS) | `Cad_Participante_Regime_Base` |
| 12 | Mês **de 2027 em diante** sem linha de `Cad_Regime_Aliquota_Soma` para a base | aferição |
| 13 | Soma de `Cad_Aliquota` (IBS e CBS) diferente da soma legal | aferição |
| 14 | Valor residual do arrendamento financeiro **abaixo do custo** de aquisição (art. 297, § 3º) | componente `af_valor_residual` |
| 15 | Reembolso de plano de saúde tratado como **receita** do beneficiário ou com crédito (art. 332, § 7º) | componente `sau_reembolso` |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| Q198-1 | Aprova o **escopo**: desenhar as 23 bases do domínio `base_regime_especifico` (as espécies de serviço do art. 182 e o funerário e o de animais, com o arrendamento em quatro bases), com catálogo de componentes nas 19 que a lei lista e **sem componente** em resseguro (alíquota zero), intermediação (valor da operação), FGTS e proteção mutualista, e **deixando de fora** os concursos de prognósticos e os demais regimes do documento 94? | Sim |
| Q198-2 | A **unidade da aferição** é uma linha por **empresa, mês e base de cálculo** (`Mov_Regime_Especifico_Afericao`), com o plano funerário e o de animais em bases próprias, e não por regime inteiro? | Sim |
| Q198-3 | Calcula a aferição **pelo decreto** (fórmula "por dentro" do art. 274, § 2º, com PIS e COFINS só em 2026, art. 584, e **sem redutor**), **mantendo** `Cad_Redutor_Base_Dere`, `Papel_Estimativa` e a Estimativa da revisão 8 como a D-N273 os deixou, com um texto novo no redutor dizendo que o decreto só tem fator de redução na importação? Se o redutor deve entrar na aferição, em qual passo (seção 5.4)? | Sim; o redutor não entra na aferição até o contador responder a C233 |
| Q198-4 | Aprova o **catálogo** `Cad_Componente_Base_Regime` (23 campos, com vigência, nome que **substitui** o `Cad_Deducao_Regime_Especifico` do documento 70), as **92 linhas provisórias** do Anexo A e o campo `ID_Componente_Base_Regime` em `Cad_Cod_Trib_Dere`? | Sim |
| Q198-5 | Aprova `Cad_Regime_Aliquota_Soma` (as 14 linhas do Anexo B.3, com vigência a partir de **01/01/2027**, que é a data da lei, e não 01/01/2026 como nos parâmetros da ECF) e o campo `ID_Base_Regime` em `Cad_Aliquota`? | Sim |
| Q198-6 | Aprova o **saldo** da seção 4.5: uma entidade (`Mov_Regime_Especifico_Saldo_Dedutivel`) para base negativa e perda excedente, a utilização separada, a **sugestão do saldo mais antigo** com troca manual, e o prazo de **cinco anos** como parâmetro com vigência? | Sim |
| Q198-7 | Aprova a **individualização** (`Mov_Dere_Individualizacao` e a tabela de dependentes), o domínio `tipo_relacao_dere`, os **10 coeficientes** de faixa etária com vigência (`Cad_Coeficiente_Rateio_Plano_Saude`) e o **reaproveitamento** de `Cad_Participante_Dependente`? | Sim |
| Q198-8 | Aprova o **ativo garantidor** por mês (`Mov_Dere_Ativo_Garantidor_Mes`, 14 campos), nascido do evento D-1106, **que só conheço por fonte secundária**? | Sim, e conferir com o manual (Q198-12) |
| Q198-9 | Aprova a **dedução por documento** (`Mov_Dere_Deducao_Documento`), com o documento fiscal ligado quando existe e a **descrição do comprovante** quando não existe no ERP (reembolso de plano de saúde)? | Sim |
| Q198-10 | A **aferição entrega o débito** de CBS e de IBS por base e mês; a compensação, o pagamento e o split ficam no espelho e na Plataforma, e o ERP **não gera guia própria** até um ato mandar? | Sim |
| Q198-11 | Aprova `Cad_Participante_Regime_Base` (em quais bases o participante atua, com a dispensa de DeRE), a leitura de seguradora, previdência e capitalização como `instituicao_financeira` **sem valor novo** no tipo, a linha **`DERE`** em `Cad_Obrigacao_Acessoria` e a ligação aferição → arquivo (`ID_Escrituracao_Arquivo`)? | Sim |
| Q198-12 | Você pode **mandar o manual oficial da DeRE** (pacote 1.3.0, com o Anexo I e as Tabelas 11 e 12) e o **ato conjunto do fator de redução** da importação, para eu conferir o que só conheço por fonte secundária? | Sim, mande; até lá o leiaute fica marcado como secundário |

# 8. O que acontece se você aprovar

| Item | Efeito |
|---|---|
| Entidades | **1.144 → 1.155** (+11, todas em Contabilidade & Fiscal) |
| Campos | **12.860 → 13.017** (+157: 155 nas onze entidades novas e 2 em `Cad_Cod_Trib_Dere` e `Cad_Aliquota`) |
| Chaves estrangeiras | **3.365 → 3.404** (+39) |
| Domínios | **353 → 355** (+2: `base_regime_especifico` e `tipo_relacao_dere`) |
| Valores de domínio | **+34** (23 bases e 11 relações), todos provisórios |
| Carga | **92** componentes, **14** linhas de alíquota, **10** coeficientes, **1** linha de `Cad_Obrigacao_Acessoria` (`DERE`) e **1** de `Cad_Parametro_Legal_Ibs_Cbs` (Anexo B), mais os 34 valores de domínio |
| Textos de campo | `Tipo_Regime_Especifico`, `Cad_Redutor_Base_Dere` e `Cad_Classe_Sistema.Dominio` |
| Ondas, DDL e ER | As onze entidades entram na onda de Contabilidade & Fiscal; as quatro com vigência geram também a tabela `_Versao`; regerados na consolidação |
| Documentos | 14 (D-N529), 38 (seção 1.29) e 188 (C233 a C238, total 238) |

# 9. Limites

- **Li a LC 214 dos arts. 181 a 246 e o decreto dos arts. 269 a 346, mais os arts. 13 e 584.** Li **só em parte** o regime do FGTS (art. 308) e **não li** a proteção patrimonial mutualista; **não li** o regime dos concursos de prognósticos (arts. 347 a 358) nem os anexos do decreto. As quatro bases sem componente esperam essa leitura ou a decisão de que não precisam de catálogo.
- **O leiaute da DeRE é fonte secundária, não oficial** (seção 3.7). Eventos, prazos e pacotes podem mudar. As entidades de movimento guardam o que a lei manda saber, e não o formato exato do arquivo.
- **As marcas dos 92 componentes** (caixa, documento, individualização, rateio, saldo, agregada, adquirente fora do regime regular e fator da importação) **são leitura minha** do texto de cada artigo. O contador valida linha a linha (C234). Nenhuma linha nasce `validado`.
- **A fórmula da exportação é leitura minha.** O art. 329 manda reverter o efeito das deduções na proporção da receita exportada (e no seguro, diretamente), mas **não escreve a fórmula completa** com o ISS e o faturamento bruto (C233).
- **A "sugestão do saldo mais antigo primeiro"** vem de **fonte secundária**, e não do decreto; a lei diz só "poderá deduzir". Por isso a utilização é sempre confirmada pelo usuário.
- **O ERP não recalcula os valores de "caixa" a partir da contabilidade.** Por Q96-1, o usuário informa o valor da receita e da dedução de cada linha, e a aferição **soma o que foi informado**; a conferência contra a conta só avisa.
- **A alíquota é única por base e por mês.** No arrendamento, em que a alíquota é a do bem, bens com alíquotas diferentes exigiriam uma chave a mais (C234, item d).
- **O crédito de quem compra o serviço financeiro** (o B0b-2) e o **cálculo do fator de redução da importação**, que depende de ato conjunto ainda não publicado, **não estão neste desenho**; o B4 só fornece a individualização de que eles dependem.
- **A vigência a partir de 01/01/2027** das alíquotas é leitura minha (a data da lei); os demais parâmetros do dicionário começam em 01/01/2026 por D-N323.
- **As contagens** vêm de um programa sobre o modelo da revisão 36 (1.144 entidades, 12.860 campos, 3.365 chaves, 353 domínios), conferido contra os nomes e os destinos de cada chave; o texto dos artigos eu conferi à mão nos trechos citados.
- **Nada passou por validação do contador.** As seis perguntas C233 a C238 estão no documento 188.

# Anexo A. Os 92 componentes propostos

O arquivo `Cad_Componente_Base_Regime.csv` traz as 20 colunas da carga (condição em texto, as oito marcas em verdadeiro e falso, origem, fundamento, situação provisória e vigência de 01/01/2026 a 31/12/9999). A tabela abaixo traz o essencial. **Origem:** `lei` quando a LC 214 e o decreto dizem o mesmo; `decreto` quando só o decreto traz. As marcas são leitura minha (seção 9).

| Base | Código | Natureza | Descrição | Marcas | Origem | Fundamento |
|---|---|---|---|---|---|---|
| credito_cambio_tvm | `cct_receita_operacao` | receita | Receitas das operações de crédito, câmbio e títulos e valores mobiliários |  | lei | LC 214, arts. 185 e 192, caput e §§ 1º, 5º e 7º; Decreto, arts. 273 e 286, caput e §§ 1º, 5º e 7º |
| credito_cambio_tvm | `cct_receita_acessoria` | receita | Fornecimentos acessórios às operações, inclusive tarifas e comissões previstas em contrato |  | decreto | Decreto, art. 286, §§ 9º e 10 (só o Decreto traz) |
| credito_cambio_tvm | `cct_reversao_provisao` | receita | Reversão de provisões e recuperação de créditos baixados como prejuízo |  | lei | LC 214, art. 186; Decreto, art. 273, § 1º |
| credito_cambio_tvm | `cct_captacao` | deducao | Despesas financeiras com a captação de recursos | rateio, entra no fator | lei | LC 214, arts. 192, I, e 202; Decreto, arts. 286, I e § 2º, e 277 |
| credito_cambio_tvm | `cct_despesa_cambio` | deducao | Despesas de câmbio das operações de câmbio | entra no fator | lei | LC 214, art. 192, II; Decreto, art. 286, II |
| credito_cambio_tvm | `cct_perda_tvm` | deducao | Perdas nas operações com títulos e valores mobiliários | fora do fator | lei | LC 214, art. 192, III; Decreto, art. 286, III |
| credito_cambio_tvm | `cct_encargo_divida` | deducao | Encargos financeiros de instrumentos de dívida emitidos, ainda que no patrimônio líquido | entra no fator | lei | LC 214, art. 192, IV, §§ 3º e 4º; Decreto, art. 286, IV, §§ 3º e 4º |
| credito_cambio_tvm | `cct_perda_credito` | deducao | Perdas no recebimento de créditos, na cessão e em descontos | entra no fator | lei | LC 214, art. 192, V; Decreto, art. 286, V |
| credito_cambio_tvm | `cct_assessor_correspondente` | deducao | Despesas com assessores de investimento, consultores de valores mobiliários e correspondentes do Banco Central | doc. fiscal, fora do fator | lei | LC 214, art. 192, VI; Decreto, art. 286, VI e § 11 |
| credito_cambio_tvm | `cct_cooperativa_associado` | nao_integra_base | Operações de crédito entre cooperativa e associado com recursos próprios ou públicos |  | lei | LC 214, art. 192, § 8º; Decreto, art. 286, § 8º |
| securitizacao_faturizacao | `sf_desconto_liquidacao` | receita | Desconto aplicado na liquidação antecipada |  | lei | LC 214, art. 193, § 1º; Decreto, art. 287, § 1º |
| securitizacao_faturizacao | `sf_captacao` | deducao | Despesas financeiras com a captação de recursos | rateio, entra no fator | lei | LC 214, arts. 193, § 1º, I, e 202; Decreto, arts. 287, § 1º, I, e 277 |
| securitizacao_faturizacao | `sf_despesa_securitizacao` | deducao | Despesas da securitização (emissão, custódia, escrituração, agentes fiduciários, de cobrança e de classificação de risco) | fora do fator | lei | LC 214, art. 193, § 1º, II; Decreto, art. 287, § 1º, II |
| securitizacao_faturizacao | `sf_perda_credito` | deducao | Perdas no recebimento de créditos, na cessão e em descontos | saldo, entra no fator | lei | LC 214, art. 193, §§ 2º e 3º; Decreto, art. 287, §§ 2º e 3º |
| arrend_oper_locacao | `ao_contraprestacao` | receita | Parcelas das contraprestações do arrendamento operacional, com tarifas e comissões | caixa | lei | LC 214, art. 201, I, a; Decreto, art. 295, I |
| arrend_oper_alienacao | `ao_alienacao_bem` | receita | Alienação do bem arrendado | caixa | lei | LC 214, art. 201, I, b; Decreto, art. 295, II |
| arrend_oper_locacao | `ao_captacao` | deducao | Despesas financeiras com a captação usada no arrendamento | adq. fora do regular, entra no fator | lei | LC 214, art. 201, II, a; Decreto, art. 295, § 2º |
| arrend_oper_locacao | `ao_despesa_arrendamento` | deducao | Despesas de arrendamento mercantil operacional, exceto as ligadas diretamente à alienação do bem | doc. fiscal, adq. fora do regular, fora do fator | lei | LC 214, art. 201, II, b; Decreto, art. 295, §§ 1º e 2º |
| arrend_oper_alienacao | `ao_despesa_alienacao` | deducao | Despesas de arrendamento diretamente relacionadas à alienação do bem | doc. fiscal, adq. fora do regular, fora do fator | lei | LC 214, art. 201, II, b; Decreto, art. 295, §§ 1º e 2º |
| arrend_fin_parcelas | `af_contraprestacao` | receita | Parcelas das contraprestações do arrendamento financeiro (receita financeira a valor presente, tarifas e comissões) | caixa | lei | LC 214, art. 201, I, c e parágrafo único, I; Decreto, art. 297, I e § 1º |
| arrend_fin_residual | `af_valor_residual` | receita | Valor residual do bem arrendado (garantido, parcelado ou pago no exercício da opção de compra) | caixa | lei | LC 214, art. 201, I, d e parágrafo único, II e III; Decreto, art. 297, II, §§ 2º e 3º |
| arrend_fin_parcelas | `af_captacao` | deducao | Despesas financeiras com a captação de recursos | rateio, adq. fora do regular, entra no fator | decreto | Decreto, arts. 297, § 4º, e 277, parágrafo único |
| consorcio | `con_receita_administracao` | receita | Tarifas, comissões, taxas, encargos, multas e juros do contrato de consórcio | caixa | lei | LC 214, art. 204; Decreto, art. 299 |
| consorcio | `con_intermediacao` | deducao | Serviços de intermediação de consórcio | doc. fiscal, individ., fora do fator | lei | LC 214, art. 204, § 1º; Decreto, art. 299, §§ 1º a 3º |
| gestao_recursos | `gr_receita_gestao` | receita | Totalidade das receitas de gestão e administração de recursos, inclusive de fundos |  | lei | LC 214, art. 185; Decreto, art. 303 |
| arranjo_pagamento | `arr_remuneracao_bruta` | receita | Valor bruto da remuneração recebida do credenciado, do instituidor ou de outros participantes |  | lei | LC 214, art. 214, § 3º; Decreto, art. 310, § 3º |
| arranjo_pagamento | `arr_rendimento_conta` | receita | Rendimentos da aplicação de recursos disponíveis em contas de pagamento |  | lei | LC 214, art. 214, § 5º; Decreto, art. 310, § 5º |
| arranjo_pagamento | `arr_rendimento_pago_titular` | deducao | Rendimentos pagos aos titulares das contas de pagamento | entra no fator | lei | LC 214, art. 214, § 5º; Decreto, art. 310, § 5º |
| antecipacao_recebivel_arranjo | `ara_desconto` | receita | Desconto aplicado na liquidação antecipada de recebíveis |  | lei | LC 214, art. 219, § 1º; Decreto, art. 314 |
| antecipacao_recebivel_arranjo | `ara_curva_di` | deducao | Valor correspondente à curva de juros futuros da taxa DI, pelo prazo da antecipação | entra no fator | lei | LC 214, art. 219, § 1º; Decreto, art. 314 |
| antecipacao_recebivel_arranjo | `ara_perda_credito` | deducao | Perdas no recebimento de créditos, na cessão e em descontos | saldo, entra no fator | lei | LC 214, art. 219, §§ 2º e 3º; Decreto, art. 314 |
| programa_fidelizacao | `pf_pontos_emitidos` | receita | Valor dos pontos emitidos no período |  | lei | LC 214, art. 219-A, I (LC 227); Decreto, art. 315, I |
| programa_fidelizacao | `pf_pontos_resgatados` | deducao | Valores pagos no resgate dos pontos | entra no fator | lei | LC 214, art. 219-A, I (LC 227); Decreto, art. 315, I |
| programa_fidelizacao | `pf_pontos_nao_utilizados` | deducao | Valores ressarcidos por pontos não utilizados, computados como receita | entra no fator | lei | LC 214, art. 219-A, I (LC 227); Decreto, art. 315, I |
| programa_fidelizacao | `pf_pontos_uso_proprio` | deducao | Pontos usados como contraprestação no fornecimento do próprio emissor | entra no fator | lei | LC 214, art. 219-A, parágrafo único (LC 227); Decreto, art. 315, § 1º |
| mercado_organizado | `mo_valor_operacao` | receita | Valor da operação de fornecimento dos serviços |  | lei | LC 214, art. 220; Decreto, art. 316 |
| seguro | `seg_premio` | receita | Prêmios de seguros e de cosseguros aceitos | caixa | lei | LC 214, art. 223, I, a; Decreto, art. 319, I, a |
| seguro | `seg_receita_garantidor` | receita | Receitas financeiras dos ativos garantidores de provisões técnicas | caixa | lei | LC 214, art. 223, I, b; Decreto, art. 319, I, b e §§ 4º e 5º |
| seguro | `seg_reversao_retida` | receita | Reversão de provisões ou reservas técnicas retida como receita própria |  | lei | LC 214, art. 223, § 3º; Decreto, art. 319, § 3º |
| seguro | `seg_indenizacao` | deducao | Indenizações de sinistros efetivamente pagos, líquidas de salvados e ressarcimentos | caixa, adq. fora do regular, entra no fator | lei | LC 214, art. 223, II, a e § 2º; Decreto, art. 319, II, a e §§ 6º e 9º |
| seguro | `seg_restituicao` | deducao | Restituição de prêmios computados como receita, inclusive por cancelamento | caixa, entra no fator | lei | LC 214, art. 223, II, b; Decreto, art. 319, II, b |
| seguro | `seg_intermediacao` | deducao | Serviços de intermediação de seguros e resseguros | doc. fiscal, individ., fora do fator | lei | LC 214, art. 223, II, c; Decreto, art. 319, II, c e §§ 7º e 8º |
| seguro | `seg_cosseguro_cedido` | deducao | Prêmio das operações de cosseguro cedido | entra no fator | lei | LC 214, art. 223, II, d; Decreto, art. 319, II, d |
| seguro | `seg_provisao_resgatavel` | deducao | Parcelas dos prêmios destinadas à provisão ou reserva técnica de seguro resgatável | agregada, entra no fator | lei | LC 214, art. 223, II, e; Decreto, art. 319, II, e e § 10 |
| previdencia_complementar | `prev_contribuicao` | receita | Contribuições para planos de previdência complementar | caixa | lei | LC 214, art. 224, I, a; Decreto, art. 320, I, a |
| previdencia_complementar | `prev_premio_sobrevivencia` | receita | Prêmios de seguro de pessoas com cobertura por sobrevivência | caixa | lei | LC 214, art. 224, I, b; Decreto, art. 320, I, b |
| previdencia_complementar | `prev_encargo_fundo` | receita | Encargo do fundo pela estruturação e manutenção dos planos | caixa | lei | LC 214, art. 224, I, c; Decreto, art. 320, I, c |
| previdencia_complementar | `prev_reversao_retida` | receita | Reversão de provisões ou reservas técnicas retida como receita própria |  | lei | LC 214, art. 224, § 1º; Decreto, art. 320, § 1º |
| previdencia_complementar | `prev_excedente_ativo` | receita | Receita financeira que passa do limite das provisões, na liquidação ou no resgate |  | decreto | Decreto, art. 320, § 5º (só o Decreto traz) |
| previdencia_complementar | `prev_provisao` | deducao | Parcelas das contribuições e prêmios destinadas à provisão ou reserva técnica | agregada, entra no fator | lei | LC 214, art. 224, II, a; Decreto, art. 320, II, a e § 6º |
| previdencia_complementar | `prev_restituicao` | deducao | Restituição de contribuições e prêmios computados como receita, inclusive cancelamento | entra no fator | lei | LC 214, art. 224, II, b; Decreto, art. 320, II, b |
| previdencia_complementar | `prev_intermediacao` | deducao | Serviços de intermediação de previdência complementar e de seguro de vida com sobrevivência | doc. fiscal, fora do fator | lei | LC 214, art. 224, II, c; Decreto, art. 320, II, c |
| previdencia_complementar | `prev_indenizacao_risco` | deducao | Indenizações das coberturas de risco, nos benefícios efetivamente pagos | entra no fator | lei | LC 214, art. 224, II, d; Decreto, art. 320, II, d |
| previdencia_complementar | `prev_nao_integra_beneficios` | nao_integra_base | Rendimentos das aplicações que pagam aposentadoria, pensão, pecúlio e resgates |  | lei | LC 214, art. 224, §§ 2º e 3º; Decreto, art. 320, §§ 2º e 3º |
| previdencia_complementar | `prev_nao_integra_demais` | nao_integra_base | Demais rendimentos de aplicações financeiras da entidade |  | lei | LC 214, art. 224, § 4º; Decreto, art. 320, § 4º |
| capitalizacao | `cap_arrecadacao` | receita | Arrecadação com os títulos de capitalização | caixa | lei | LC 214, art. 225, I, a; Decreto, art. 323, I, a |
| capitalizacao | `cap_prescricao_penalidade` | receita | Receitas com prescrição e penalidades | caixa | lei | LC 214, art. 225, I, b; Decreto, art. 323, I, b e §§ 9º e 10 |
| capitalizacao | `cap_reversao_retida` | receita | Reversão de provisões ou reservas técnicas retida como receita própria |  | lei | LC 214, art. 225, § 1º; Decreto, art. 323, § 1º |
| capitalizacao | `cap_excedente_ativo` | receita | Receita financeira que passa do limite das provisões, na liquidação ou no resgate |  | decreto | Decreto, art. 323, § 11 (só o Decreto traz) |
| capitalizacao | `cap_provisao` | deducao | Parcelas destinadas à provisão ou reserva técnica, inclusive sorteios a pagar | entra no fator | lei | LC 214, art. 225, II, a; Decreto, art. 323, II, a |
| capitalizacao | `cap_cancelamento` | deducao | Cancelamentos e restituições de títulos computados como receita | entra no fator | lei | LC 214, art. 225, II, b; Decreto, art. 323, II, b |
| capitalizacao | `cap_intermediacao` | deducao | Serviços de intermediação de capitalização | doc. fiscal, individ., fora do fator | lei | LC 214, art. 225, II, c; Decreto, art. 323, II, c e §§ 5º e 6º |
| capitalizacao | `cap_nao_integra_resgate` | nao_integra_base | Rendimentos das aplicações destinadas ao resgate de títulos e aos sorteios |  | lei | LC 214, art. 225, §§ 2º e 3º; Decreto, art. 323, §§ 2º e 3º |
| capitalizacao | `cap_nao_integra_demais` | nao_integra_base | Demais rendimentos de aplicações financeiras da entidade |  | lei | LC 214, art. 225, § 4º; Decreto, art. 323, § 4º |
| ativo_virtual | `av_valor_servico` | receita | Valor da prestação do serviço de ativos virtuais |  | lei | LC 214, art. 229; Decreto, art. 326 |
| plano_saude | `sau_contraprestacao` | receita | Prêmios e contraprestações efetivamente recebidos, com coparticipações, corresponsabilidade assumida, taxas de administração e comissões | caixa | lei | LC 214, art. 235, I, a; Decreto, art. 332, I, a |
| plano_saude | `sau_receita_garantidor` | receita | Receitas financeiras dos ativos garantidores das reservas técnicas, efetivamente liquidadas | caixa | lei | LC 214, art. 235, I, b e § 4º; Decreto, art. 332, I, b e §§ 1º a 3º |
| plano_saude | `sau_custo_direto` | deducao | Custos assistenciais de bens e serviços adquiridos diretamente pela entidade | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a e § 1º, I; Decreto, art. 332, II, a e §§ 5º, I, 6º e 8º |
| plano_saude | `sau_reembolso` | deducao | Reembolsos a segurados e beneficiários por bens e serviços que eles adquiriram | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a, § 1º, II e § 5º; Decreto, art. 332, II, a e §§ 5º, II, 6º e 7º |
| plano_saude | `sau_corresponsabilidade_cedida` | deducao | Corresponsabilidade cedida a outra operadora (serviços a beneficiários de outra, com a assunção do risco) | entra no fator | lei | LC 214, art. 235, §§ 2º e 3º; Decreto, art. 332, §§ 9º e 10 |
| plano_saude | `sau_restituicao` | deducao | Cancelamentos e restituições de prêmios e contraprestações computados como receita | caixa, entra no fator | lei | LC 214, art. 235, II, b; Decreto, art. 332, II, b |
| plano_saude | `sau_intermediacao` | deducao | Serviços de intermediação de planos de saúde | doc. fiscal, fora do fator | lei | LC 214, art. 235, II, c; Decreto, art. 332, II, c |
| plano_saude | `sau_administradora_outras` | deducao | Taxa de administração paga a administradoras de benefícios e valores pagos a outras entidades do art. 234 | fora do fator | lei | LC 214, art. 235, II, d; Decreto, art. 332, II, d |
| plano_saude | `sau_nao_integra_financeira` | nao_integra_base | Receitas financeiras sem vínculo com a alocação de prêmios e contraprestações |  | lei | LC 214, art. 235, § 6º; Decreto, art. 332, § 4º |
| plano_funerario | `fun_contraprestacao` | receita | Prêmios e contraprestações efetivamente recebidos, com coparticipações, corresponsabilidade assumida, taxas de administração e comissões | caixa | lei | LC 214, art. 235, I, a; Decreto, art. 332, I, a (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_receita_garantidor` | receita | Receitas financeiras dos ativos garantidores das reservas técnicas, efetivamente liquidadas | caixa | lei | LC 214, art. 235, I, b e § 4º; Decreto, art. 332, I, b e §§ 1º a 3º (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_custo_direto` | deducao | Custos assistenciais de bens e serviços adquiridos diretamente pela entidade | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a e § 1º, I; Decreto, art. 332, II, a e §§ 5º, I, 6º e 8º (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_reembolso` | deducao | Reembolsos a segurados e beneficiários por bens e serviços que eles adquiriram | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a, § 1º, II e § 5º; Decreto, art. 332, II, a e §§ 5º, II, 6º e 7º (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_corresponsabilidade_cedida` | deducao | Corresponsabilidade cedida a outra operadora (serviços a beneficiários de outra, com a assunção do risco) | entra no fator | lei | LC 214, art. 235, §§ 2º e 3º; Decreto, art. 332, §§ 9º e 10 (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_restituicao` | deducao | Cancelamentos e restituições de prêmios e contraprestações computados como receita | caixa, entra no fator | lei | LC 214, art. 235, II, b; Decreto, art. 332, II, b (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_intermediacao` | deducao | Serviços de intermediação de planos de saúde | doc. fiscal, fora do fator | lei | LC 214, art. 235, II, c; Decreto, art. 332, II, c (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_administradora_outras` | deducao | Taxa de administração paga a administradoras de benefícios e valores pagos a outras entidades do art. 234 | fora do fator | lei | LC 214, art. 235, II, d; Decreto, art. 332, II, d (art. 236, que remete aos arts. 234 a 242) |
| plano_funerario | `fun_nao_integra_financeira` | nao_integra_base | Receitas financeiras sem vínculo com a alocação de prêmios e contraprestações |  | lei | LC 214, art. 235, § 6º; Decreto, art. 332, § 4º (art. 236, que remete aos arts. 234 a 242) |
| plano_pet | `pet_contraprestacao` | receita | Prêmios e contraprestações efetivamente recebidos, com coparticipações, corresponsabilidade assumida, taxas de administração e comissões | caixa | lei | LC 214, art. 235, I, a; Decreto, art. 332, I, a (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_receita_garantidor` | receita | Receitas financeiras dos ativos garantidores das reservas técnicas, efetivamente liquidadas | caixa | lei | LC 214, art. 235, I, b e § 4º; Decreto, art. 332, I, b e §§ 1º a 3º (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_custo_direto` | deducao | Custos assistenciais de bens e serviços adquiridos diretamente pela entidade | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a e § 1º, I; Decreto, art. 332, II, a e §§ 5º, I, 6º e 8º (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_reembolso` | deducao | Reembolsos a segurados e beneficiários por bens e serviços que eles adquiriram | caixa, doc. fiscal, entra no fator | lei | LC 214, art. 235, II, a, § 1º, II e § 5º; Decreto, art. 332, II, a e §§ 5º, II, 6º e 7º (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_corresponsabilidade_cedida` | deducao | Corresponsabilidade cedida a outra operadora (serviços a beneficiários de outra, com a assunção do risco) | entra no fator | lei | LC 214, art. 235, §§ 2º e 3º; Decreto, art. 332, §§ 9º e 10 (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_restituicao` | deducao | Cancelamentos e restituições de prêmios e contraprestações computados como receita | caixa, entra no fator | lei | LC 214, art. 235, II, b; Decreto, art. 332, II, b (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_intermediacao` | deducao | Serviços de intermediação de planos de saúde | doc. fiscal, fora do fator | lei | LC 214, art. 235, II, c; Decreto, art. 332, II, c (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_administradora_outras` | deducao | Taxa de administração paga a administradoras de benefícios e valores pagos a outras entidades do art. 234 | fora do fator | lei | LC 214, art. 235, II, d; Decreto, art. 332, II, d (art. 243, que remete aos arts. 234 a 242) |
| plano_pet | `pet_nao_integra_financeira` | nao_integra_base | Receitas financeiras sem vínculo com a alocação de prêmios e contraprestações |  | lei | LC 214, art. 235, § 6º; Decreto, art. 332, § 4º (art. 243, que remete aos arts. 234 a 242) |

# Anexo B. As cargas

## B.1 Valores novos do domínio `base_regime_especifico` (23)

| Código | Descrição | Fundamento |
|---|---|---|
| `credito_cambio_tvm` | Operações de crédito, de câmbio e com títulos e valores mobiliários | LC 214, art. 182, I a III e art. 192; Decreto 12.955, art. 269, I a III e art. 286 |
| `securitizacao_faturizacao` | Securitização e faturização (factoring) | LC 214, art. 182, IV e V e art. 193; Decreto, art. 269, IV e V e art. 287 |
| `arrend_oper_locacao` | Arrendamento mercantil operacional: contraprestações (alíquota da locação do bem) | LC 214, art. 182, VI e art. 201, I, a; Decreto, art. 295, I |
| `arrend_oper_alienacao` | Arrendamento mercantil operacional: alienação do bem arrendado (alíquota da venda do bem) | LC 214, art. 182, VI e art. 201, I, b; Decreto, art. 295, II |
| `arrend_fin_parcelas` | Arrendamento mercantil financeiro: parcelas das contraprestações | LC 214, art. 182, VI e art. 201, I, c; Decreto, art. 297, I |
| `arrend_fin_residual` | Arrendamento mercantil financeiro: valor residual (alíquota da venda do bem) | LC 214, art. 182, VI e art. 201, I, d; Decreto, art. 297, II |
| `consorcio` | Administração de consórcio | LC 214, art. 182, VII e art. 204; Decreto, art. 299 |
| `gestao_recursos` | Gestão e administração de recursos, inclusive de fundos de investimento | LC 214, art. 182, VIII e art. 207; Decreto, arts. 302 e 303 |
| `arranjo_pagamento` | Arranjos de pagamento | LC 214, art. 182, IX e art. 214; Decreto, art. 310 |
| `antecipacao_recebivel_arranjo` | Liquidação antecipada de recebíveis de arranjos de pagamento | LC 214, art. 219; Decreto, art. 314 |
| `programa_fidelizacao` | Administração de programas de fidelização | LC 214, art. 219-A (LC 227/2026); Decreto, art. 315 |
| `mercado_organizado` | Mercados organizados, infraestruturas de mercado e depositárias centrais | LC 214, art. 182, X e art. 220; Decreto, art. 316 |
| `seguro` | Seguros e cosseguros (ramos elementares e pessoas sem sobrevivência) | LC 214, art. 182, XI e art. 223; Decreto, art. 319 |
| `resseguro` | Resseguros e retrocessão (alíquota zero) | LC 214, art. 182, XII e art. 223, § 4º; Decreto, art. 322 |
| `previdencia_complementar` | Previdência complementar, aberta e fechada, e seguro de pessoas com sobrevivência | LC 214, art. 182, XIII e art. 224; Decreto, art. 320 |
| `capitalizacao` | Capitalização | LC 214, art. 182, XIV e art. 225; Decreto, art. 323 |
| `intermediacao_financeira` | Intermediação de consórcios, seguros, resseguros, previdência e capitalização | LC 214, art. 182, XV, arts. 206, 228 e 240; Decreto, arts. 301, 325 e 340 |
| `ativo_virtual` | Serviços de ativos virtuais | LC 214, art. 182, XVI e art. 229; Decreto, art. 326 |
| `fgts` | Operações relacionadas ao FGTS | LC 214, art. 212; Decreto, art. 308 (lido só em parte) |
| `protecao_mutualista` | Proteção patrimonial mutualista | LC 214, art. 182, XVII (LC 227/2026); regime não lido neste documento |
| `plano_saude` | Planos de assistência à saúde | LC 214, arts. 234 a 242; Decreto, arts. 330 a 343 |
| `plano_funerario` | Planos de assistência funerária | LC 214, art. 236; Decreto, art. 345 |
| `plano_pet` | Planos de assistência à saúde de animais domésticos | LC 214, art. 243; Decreto, art. 346 |

## B.2 Valores novos do domínio `tipo_relacao_dere` (11)

| Código | Descrição | Fundamento |
|---|---|---|
| `segurado` | Segurado identificado na apólice | LC 214, art. 227, I; Decreto, art. 324, I |
| `estipulante` | Estipulante de apólice coletiva, quando os segurados não são identificados | LC 214, art. 227, I; Decreto, art. 324, I e § 1º |
| `participante_previdencia` | Participante de plano de previdência complementar | LC 214, art. 227, II; Decreto, art. 324, II |
| `titular_capitalizacao` | Titular de título de capitalização | LC 214, art. 227, III; Decreto, art. 324, III |
| `subscritor_capitalizacao` | Subscritor de título de capitalização | LC 214, art. 227, III; Decreto, art. 324, III |
| `distribuidor_capitalizacao` | Distribuidor de título de capitalização | LC 214, art. 227, III; Decreto, art. 324, III |
| `titular_plano_saude` | Titular pessoa física de plano de assistência à saúde | LC 214, art. 239; Decreto, art. 339 |
| `consorciado` | Consorciado destinatário da intermediação | Decreto, art. 299, § 2º |
| `cotista_fundo` | Cotista de fundo de investimento (ou distribuidor por conta e ordem) | LC 214, art. 210; Decreto, art. 306 |
| `adquirente_servico_mercado` | Adquirente de serviço de mercado organizado ou infraestrutura | LC 214, art. 222; Decreto, art. 318 |
| `tomador_servico_financeiro` | Tomador de outro serviço financeiro, para o crédito dele | LC 214, art. 190; Decreto, art. 275 |

## B.3 `Cad_Regime_Aliquota_Soma` (14 linhas)

A regra geral (base vazia) vale para toda base de serviço financeiro sem regra própria, de 2027 em diante, com a soma do art. 233. As linhas `aliquota_do_bem` não levam número: o Motor lê a alíquota do bem. Tudo provisório.

| Base | Forma | Soma (p.p.) | Redução sobre a referência (%) | Redução com ISS (p.p.) | Fundamento | Início | Fim |
|---|---|---|---|---|---|---|---|
| (regra geral) | soma_fixa | 10.85 |  | 2.0 | LC 214, art. 233, I e § 10, I | 2027-01-01 | 2028-12-31 |
| (regra geral) | soma_fixa | 11.00 |  | 1.8 | LC 214, art. 233, II e § 10, II | 2029-01-01 | 2029-12-31 |
| (regra geral) | soma_fixa | 11.15 |  | 1.6 | LC 214, art. 233, III e § 10, III | 2030-01-01 | 2030-12-31 |
| (regra geral) | soma_fixa | 11.30 |  | 1.4 | LC 214, art. 233, IV e § 10, IV | 2031-01-01 | 2031-12-31 |
| (regra geral) | soma_fixa | 11.50 |  | 1.2 | LC 214, art. 233, V e § 10, V | 2032-01-01 | 2032-12-31 |
| (regra geral) | soma_fixa | 12.50 |  |  | LC 214, art. 233, VI | 2033-01-01 | 2033-12-31 |
| (regra geral) | soma_fixa | 12.50 |  |  | LC 214, art. 189, II (a partir de 2034, as fixadas para 2033) | 2034-01-01 | 9999-12-31 |
| `arrend_oper_locacao` | aliquota_do_bem |  |  |  | LC 214, art. 201, I, a (alíquota aplicável à locação do bem; imóvel: regime específico da locação) | 2027-01-01 | 9999-12-31 |
| `arrend_oper_alienacao` | aliquota_do_bem |  |  |  | LC 214, art. 201, I, b (alíquota aplicável à venda do bem; imóvel: regime específico da venda) | 2027-01-01 | 9999-12-31 |
| `arrend_fin_residual` | aliquota_do_bem |  |  |  | LC 214, art. 201, I, d (alíquota da venda do bem, imóvel pelo regime específico) | 2027-01-01 | 9999-12-31 |
| `resseguro` | soma_fixa | 0.00 |  |  | LC 214, art. 223, § 4º (alíquota zero, inclusive nos prêmios cedidos ao exterior) | 2027-01-01 | 9999-12-31 |
| `plano_saude` | reducao_sobre_referencia |  | 60.00 |  | LC 214, art. 237; Decreto, art. 336 | 2027-01-01 | 9999-12-31 |
| `plano_funerario` | reducao_sobre_referencia |  | 60.00 |  | LC 214, arts. 236 e 237; Decreto, arts. 336 e 345 | 2027-01-01 | 9999-12-31 |
| `plano_pet` | reducao_sobre_referencia |  | 30.00 |  | LC 214, art. 243; Decreto, art. 346 (sem direito a crédito do adquirente) | 2027-01-01 | 9999-12-31 |

## B.4 `Cad_Coeficiente_Rateio_Plano_Saude` (10 linhas)

Decreto 12.955, art. 339, § 2º, II, alíneas a a j. Vigência a partir de 01/01/2026 (D-N323), provisório.

| Idade inicial | Idade final | Coeficiente |
|---|---|---|
| 0 | 18 | 0.17 |
| 19 | 23 | 0.21 |
| 24 | 28 | 0.25 |
| 29 | 33 | 0.29 |
| 34 | 38 | 0.33 |
| 39 | 43 | 0.38 |
| 44 | 48 | 0.42 |
| 49 | 53 | 0.50 |
| 54 | 58 | 0.67 |
| 59 |  | 1.00 |

## B.5 Outras linhas de carga

| Entidade | Linha |
|---|---|
| `Cad_Obrigacao_Acessoria` | `DERE`: DeRE, declaração de regimes específicos de IBS e CBS; início 01/01/2026 (uso no ERP, não a data legal) |
| `Cad_Parametro_Legal_Ibs_Cbs` | `prazo_base_negativa_regime_anos` = 5 anos; Decreto, arts. 278 e 333, parágrafo único (LC 214, art. 301, por nota do decreto); provisório |

# Anexo C. Perguntas ao contador (C233 a C238)

Estão também no documento 188, que passa a ter 238 perguntas.

**C233 · Decreto 12.955, arts. 274, § 2º, e 584, e LC 214, art. 232 · Aferição mensal: faturamento bruto, ISS, PIS e COFINS de 2026, exportação e o redutor**

*Documento 198, seção 4 (Q198-3)*

O art. 274, § 2º, dá a base da CBS dos serviços com dedução prevista como [(faturamento bruto − deduções previstas) − ISS devido] ÷ (1 + alíquota do IBS + alíquota da CBS), com faturamento bruto igual às receitas tributáveis do período mais a CBS e o IBS. Em 2026 o art. 584 subtrai também o PIS e a COFINS apurados no período para a seção com dedução. O dicionário guarda, desde a revisão 8, a base estimada por outra fórmula, (receita bruta − deduções permitidas) × redutor, e a D-N273 manteve o redutor como percentual que reduz a base.

Pergunta: (a) nas seções em regime de caixa, o "faturamento bruto" é o valor efetivamente recebido, e o ISS e o PIS e a COFINS subtraídos são os do mesmo período? (b) em 2026, quais contribuições entram no "PIS" e na "COFINS" do art. 584 (as apuradas no regime cumulativo, no não cumulativo, ou as duas)? (c) com exportação, a leitura do documento 198 é base = [(faturamento bruto − receita de exportação) − (deduções − deduções revertidas) − ISS] ÷ (1 + alíquota do IBS + alíquota da CBS), com a reversão proporcional à receita exportada (no seguro, direta); confirma? (d) o redutor da DeRE tem contrapartida em lei na aferição que o decreto não mostra, ou ele serve só à estimativa e ao fator de redução da importação do art. 328, § 5º?

Proposta do documento 198 (Q198-3): o ERP calcula a aferição pelo decreto, mantém o redutor e a Estimativa como estão (D-N273) e marca a leitura como provisória; nada aplicado ao dicionário.

**C234 · LC 214, arts. 185 a 233, e Decreto 12.955, arts. 269 a 346 · Catálogo de 92 componentes da base: confirmação e quatro itens que só o decreto traz**

*Documento 198, seção 3.2 e Anexo A (Q198-4)*

O documento 198 propõe um catálogo de 92 componentes (34 receitas, 50 deduções e 8 itens que a lei tira da base), todos provisórios, com as marcas que a lei dá a cada um: regime de caixa, documento fiscal idôneo, individualização do adquirente, rateio por natureza de receita, saldo excedente, base agregada, restrição ao adquirente fora do regime regular e participação no fator de redução da importação. Quatro componentes só o decreto traz, e a LC 214 não: o fornecimento acessório das operações de crédito (art. 286, §§ 9º e 10), a captação do arrendamento financeiro limitada às parcelas (art. 297, § 4º), e o excedente de receita financeira sobre as provisões técnicas na previdência (art. 320, § 5º) e na capitalização (art. 323, § 11). A LC 227 revogou a dedução da depreciação do bem arrendado (art. 201, II, c), mas o decreto ainda diz, no art. 295, § 3º, que a dedução da depreciação implica a vedação do crédito do bem.

Pergunta: (a) o catálogo do Anexo A está completo e correto para as seções que o seu cliente usa? Marque o que falta e o que está errado. (b) os quatro itens que só o decreto traz devem entrar na base e na dedução como o decreto escreve? (c) a depreciação do bem arrendado deixou de ser dedutível ou o decreto ainda a permite? (d) no arrendamento, a alíquota depende do bem; se a empresa arrenda bens com alíquotas diferentes no mesmo mês, a aferição deve ser feita por alíquota (uma linha por classificação do bem) e não por base?

Proposta do documento 198 (Q198-4): a carga sai provisória e a validação do contador troca Situacao_Dado para validado, linha a linha; a divisão por alíquota do bem só entra se você pedir; nada aplicado ao dicionário.

**C235 · LC 214, arts. 223, 235 e 237, e Decreto 12.955, arts. 319 e 332 · Receita financeira dos ativos garantidores: quando entra e em que proporção**

*Documento 198, seção 3.3 e 3.4 (Q198-8)*

No seguro, a receita financeira dos ativos garantidores entra na base na liquidação ou no resgate (o rendimento periódico conta como resgate parcial), só a recebida a partir de 01/01/2027, na proporção dos prêmios de operações que não geram crédito ao segurado sobre o total dos prêmios (art. 319, I, b, e § 5º). No plano de saúde, entra quando há, juntas, a liquidação ou o resgate do ativo e a redução das provisões técnicas, pela diferença entre o total de provisões técnicas do período e o do período anterior, na forma da ANS (art. 332, § 1º). O dicionário guarda o ativo e o rendimento por mês, e o valor que o usuário leva à linha da DeRE.

Pergunta: (a) na proporção do seguro, o "total dos prêmios" é o do mês da liquidação ou o acumulado? (b) o rendimento periódico, que conta como resgate parcial, entra inteiro no mês em que é recebido, mesmo que o ativo continue na carteira? (c) no plano de saúde, qual é o total de provisões técnicas a comparar (as provisões lastreadas por ativo garantidor, na regra da ANS) e o rendimento sobe inteiro quando a diferença é negativa? (d) a receita financeira recebida antes de 01/01/2027 e ainda não resgatada entra quando o ativo for liquidado, ou fica de fora para sempre?

Proposta do documento 198 (Q198-8): o ERP guarda o que o usuário informa e calcula só a proporção do seguro e o saldo do ativo; a regra da liquidação e da redução das provisões fica como aviso até a sua leitura; nada aplicado ao dicionário.

**C236 · Decreto 12.955, arts. 278 e 333, e LC 214, art. 301 · Base negativa: por base ou por empresa, e prazo**

*Documento 198, seção 3.1 e 4.5 (Q198-6)*

O art. 278 diz que a base negativa de um período de aferição pode ser deduzida, sem atualização, das bases positivas dos períodos seguintes, observado o art. 273, § 3º (as deduções só valem para a receita a que estão ligadas), em até cinco anos, contados do último dia útil do período de apuração (parágrafo único). O documento 198 lê que o saldo é de cada base de cálculo e só abate a mesma base.

Pergunta: (a) a empresa que atua em mais de uma base (por exemplo, seguro e previdência) abate o saldo de uma base contra a outra, ou só contra a mesma? (b) o "poderá deduzir" faz do uso uma opção, ou o contribuinte deve abater sempre que houver base positiva? (c) a regra dos cinco anos conta do último dia útil do mês da base negativa? (d) o saldo expirado vira perda definitiva, sem tratamento tributário?

Proposta do documento 198 (Q198-6): o saldo é por empresa e base, o uso é sugerido do mais antigo para o mais novo e o usuário pode trocar, e o prazo de cinco anos é parâmetro com vigência; nada aplicado ao dicionário.

**C237 · LC 214, arts. 193, § 3º, e 219, § 3º · Perda excedente na securitização, na faturização e nos recebíveis de arranjos**

*Documento 198, seção 3.1 e 4.5 (Q198-6)*

A perda no recebimento de créditos, na cessão e em descontos é dedutível a valor de mercado, e a que passa do valor tributável do período fica para os períodos seguintes. A lei não fixa prazo para esse saldo, e o decreto repete o texto sem dizer como o saldo convive com a base negativa do art. 278.

Pergunta: (a) a perda que passa do valor tributável gera base negativa (com os cinco anos) ou é um saldo próprio, sem prazo? (b) o saldo da perda excedente e a base negativa podem existir ao mesmo tempo na mesma base, e qual se abate primeiro? (c) a perda excedente da antecipação de recebíveis de arranjos (art. 219, § 3º) se soma à da securitização, ou são saldos separados?

Proposta do documento 198 (Q198-6): os dois são saldos separados na mesma entidade, com Tipo_Saldo; só a base negativa tem data limite; nada aplicado ao dicionário.

**C238 · LC 214, arts. 235 e 239, e Decreto 12.955, arts. 332 e 339 · Plano de saúde: documento do custo assistencial, reembolso e individualização**

*Documento 198, seção 3.4 (Q198-9)*

A dedução do custo assistencial exige documento fiscal idôneo, inclusive nos reembolsos a segurados e beneficiários (art. 332, § 5º), e o reembolso não é receita de quem o recebe nem dá crédito (§ 7º). O documento do reembolso é do prestador que atendeu o beneficiário, e pode não estar no ERP da operadora. Na DeRE, a operadora individualiza o titular e os dependentes e, nos planos coletivos sem valor por titular, aloca o valor do contrato pelos coeficientes de faixa etária (art. 339, § 2º).

Pergunta: (a) para deduzir o reembolso, a operadora precisa guardar o documento fiscal do prestador (e em que forma), ou basta o comprovante de pagamento ao beneficiário com a descrição do atendimento? (b) a corresponsabilidade cedida e a assumida entram na DeRE por titular ou só no total da operadora? (c) na alocação por coeficientes, o titular que é dependente de outro plano da mesma operadora entra duas vezes? (d) a individualização é por mês de competência ou por mês de recebimento?

Proposta do documento 198 (Q198-7 e Q198-9): o ERP aceita a dedução sem documento no ERP quando o usuário descreve o comprovante, e só avisa; a alocação por coeficiente grava a data de nascimento usada; nada aplicado ao dicionário.

