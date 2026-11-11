# Crédito de quem compra o serviço financeiro, o arrendamento, a antecipação de recebíveis e o plano de saúde dos empregados: o desenho do B0b-2 — Documento 200

> **O que este documento faz.** Você escolheu desenhar o **B0b-2**, o lado do **tomador** dos serviços financeiros: o crédito de IBS e de CBS de qualquer cliente que tem empréstimo, leasing de frota, antecipação de cartão ou desconto de duplicatas, e de quem paga plano de saúde aos empregados. O B4 (documento 198, aprovado) desenhou o lado de quem **presta** o serviço e calcula o débito; este documento desenha o lado de quem **toma** e calcula o crédito. Li os artigos da LC 214 e do Decreto 12.955 que dão crédito ao tomador (e os que o vedam), conferi as entidades que o dicionário já tem e propus **oito entidades novas, cinco campos novos em entidades existentes e 28 regras de carga**, sem domínio novo.
>
> **Nada foi aplicado ao dicionário.** Ele continua na revisão 37 (1.155 entidades, 13.017 campos, 3.404 chaves estrangeiras, 61 referências genéricas e 355 domínios). Este documento só entra no dicionário depois das suas respostas à seção 7 e de você mandar "consolidar".

*Fontes: a LC 214/2025 com as alterações da LC 227/2026 (texto consolidado do Planalto, arts. 188 a 238, lidos nos trechos que tratam do tomador) e o Decreto 12.955/2026 consolidado (arts. 62 a 64, 275, 284 a 300, 301, 305, 307, 310 a 318, 319 a 328, 337, 345 e 346, lidos nos trechos citados); o dicionário na revisão 37; os documentos 10, 94, 115, 198 e a D-N529 a D-N532; as decisões D-N273, D-N282, D-N284 e D-N323. **Não li** o ato conjunto da RFB e do CGIBS que diz como o fornecedor informa o crédito, nem o leiaute da DeRE (o manual oficial ainda não chegou, Q198-12).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que achei.** O dicionário já guarda o **empréstimo e as parcelas** (`Mov_Emprestimo`), o **título e a baixa** (o pagamento, que é o regime de caixa que a lei pede), o **crédito escriturável** com os estados da Plataforma (`Mov_Credito_Fiscal`: a apropriar, apropriado, inapropriável) e a **aba de créditos do espelho** (`Mov_Cbs_Apuracao_Espelho_Conta`). Falta o que está **entre o pagamento e o crédito**: a regra que diz se o serviço dá crédito e como se calcula, o **arrendamento**, a **antecipação de recebíveis**, o **registro do cálculo** e o **plano de saúde dos empregados**.
- **O crédito do tomador não é uma conta só; são três mecânicas.** (a) **Cálculo próprio do tomador:** no empréstimo, o crédito incide sobre a despesa financeira paga menos o principal e a Selic sobre o principal (LC 214, art. 194); no desconto, na cessão, na securitização, na faturização e na antecipação de cartão, sobre a parte do deságio que passa da **curva DI** (arts. 196 e 219, § 5º); no arrendamento, sobre a **parcela paga** pela alíquota da receita do arrendador (art. 203). (b) **Valor pago pelo fornecedor:** tarifas, comissões, consórcio, mercado organizado, arranjo de pagamento, ativos virtuais, intermediação e seguro; o crédito é o tributo que o fornecedor informou ter pago, e o ERP **só registra** (art. 190). (c) **Proporção do débito do fornecedor:** o plano de saúde dos empregados (art. 238, parágrafo único) e a capitalização.
- **Proposta: 8 entidades novas e 5 campos novos em entidades que já existem.** São **1 cadastro com vigência** (`Cad_Regra_Credito_Tomador`, o catálogo de 28 regras), **1 cadastro** do contrato (`Cad_Arrendamento_Mercantil`), **6 movimentos** (a parcela do arrendamento, a antecipação e os itens dela, o registro do crédito, o acordo coletivo do benefício e o crédito do plano de saúde). Dos cinco nomes que o documento 94 listou para o B0b-2, todos viram entidade; **três nomes novos** são necessários (o catálogo, os itens da antecipação e o acordo coletivo).
- **Nenhum domínio novo.** O catálogo usa o domínio `base_regime_especifico` do B4 (23 bases) e o valor `tomador_servico_financeiro` de `tipo_relacao_dere`, que o B4 já criou. Entram dois valores em `tipo_emprestimo` (debênture e nota comercial), por carga.
- **O crédito nasce em `Mov_Credito_Fiscal`**, com duas origens novas (`servico_financeiro_tomador` e `beneficio_empregado`) e o mesmo ciclo de estados que o dicionário já usa. O novo `Mov_Credito_Servico_Regime_Especifico` guarda a **memória de cálculo** (o que foi pago, as deduções, a base, as alíquotas gravadas, a proporção do art. 291 e as vedações aplicadas) e liga as duas pontas: o pagamento e o crédito.
- **Seis pontos em que a lei não fecha a conta** e que eu li de um jeito (seção 4): a Selic incide sobre o saldo devedor ou só sobre o principal da parcela; a fórmula da curva DI; a base do crédito do arrendamento financeiro (a parcela inteira ou só os encargos); como o emissor de título sabe quem o detém; a regra de empate da taxa de DI, que o decreto escreve de dois jeitos; e se o crédito existe em 2026. Cada um virou pergunta ao contador, **C239 a C245**.
- **Perguntas:** Q200-1 a Q200-11 (seção 7), cada uma com recomendação. **Para o contador:** sete perguntas novas, **C239 a C245** (Anexo C), que entram no documento 188.
- **Se você aprovar:** 1.163 entidades (+8), 13.169 campos (+152), 3.440 chaves estrangeiras (+36), 28 regras de carga, 2 valores em `tipo_emprestimo` e 1 série de Selic. Os documentos 14 (D-N533) e 38 (seção 1.30) acompanham.

# 2. O que o dicionário já tem para o B0b-2

| Entidade | O que guarda hoje | O que falta para o B0b-2 |
|---------------------------------|---------------------------------|---------------------------------|
| `Mov_Emprestimo` e `Mov_Emprestimo_Parcela` | O contrato (valor, taxa, sistema de amortização, indexador) e cada parcela com **principal e juros previstos**. O título a pagar da parcela nasce com `Origem_Tipo = emprestimo`. | Quem emprestou, se é operação de crédito ou título de dívida (com ou sem oferta pública) e se é referenciado em moeda estrangeira. |
| `Mov_Titulo` e `Mov_Titulo_Baixa` | O título e o **pagamento efetivo** (`Data_Baixa`, `Valor_Baixado`, `Valor_Desconto`). É o regime de caixa da lei. | A origem `arrendamento_parcela`. O deságio da antecipação cabe em `Valor_Desconto`. |
| `Mov_Credito_Fiscal`, `_Aplicacao` e `_Parcela` | O crédito escriturável (`ID_Imposto`), com `Origem`, `Status` (a apropriar, apropriado, inapropriável, utilizado) e `Modalidade_Extincao_Debito`. | Duas origens: o serviço financeiro do tomador e o benefício do empregado. |
| `Mov_Cbs_Apuracao_Espelho_Conta` | A aba de **créditos** da Plataforma, com o estado de apropriação, `Valor_Apurado_Erp` e `Divergencia_Valor`. | Nada novo: é onde o crédito calculado se confere. |
| `Cad_Serie_Cotacao` e `Mov_Serie_Cotacao_Valor` | Séries de índice e de câmbio, com 8 casas decimais. | Marcar a série da **Selic** e os contratos de **DI futuro** (com o vencimento). |
| `Mov_Transacao_Cartao` | A transação de cartão, com as parcelas e a credenciadora. | É o recebível que a antecipação de cartão antecipa. |
| `Cad_Gestao_Contrato` | O contrato geral, com aditivos, garantias e penalidades. | O arrendamento fica ligado a ele, sem repetir o que ele já guarda. |
| `Cad_Rh_Beneficio`, `Mov_Rh_Beneficio_Adesao` e `_Contribuicao` | O benefício (tipo `plano_saude`, `vale_transporte` e outros), a adesão do empregado e a contribuição dele. | O acordo ou a convenção coletiva e o crédito mensal. |
| `Cad_Criterio_Uso_Preponderante` | O critério do uso e consumo pessoal, com `Credito_Igual_Debito_Fornecedor`, `Exige_Acordo_Ou_Convencao_Coletiva` e `Meses_Apos_Fim_Acordo` (6). | É o que liga o benefício ao crédito; o B0b-2 só aponta para ele. |
| B4: `Mov_Dere_Individualizacao`, `Cad_Participante_Regime_Base`, `Cad_Regime_Aliquota_Soma` | A individualização do titular e do contratante (`ID_Participante_Contratante`, `Valor_Cbs_Equivalente`), as bases em que o fornecedor atua e as alíquotas de 2027 em diante. | Nada: o B0b-2 lê o B4. |
| `Cad_Participante_Qualificacao_Cbs` (B2) | A condição do participante na CBS (regime regular, optante) e a qualificação de cooperativa. | Nada: é a fonte da vedação do associado de cooperativa. |

**Nenhuma das cinco entidades que o documento 94 listou existe ainda.** O dicionário não tem `Mov_Credito_Servico_Regime_Especifico`, `Cad_Arrendamento_Mercantil`, `Mov_Arrendamento_Parcela`, `Mov_Antecipacao_Recebivel` nem `Mov_Rh_Beneficio_Credito_Cbs`.

# 3. O que a lei e o decreto exigem

## 3.1 A regra geral

O crédito dos serviços financeiros só existe **nos casos que a lei lista**: é apropriado com base nas **informações que o fornecedor prestou** ao Comitê Gestor e à RFB, na DeRE no decreto, e fica sujeito às regras gerais de crédito (LC 214, arts. 190 e 47 a 56; Decreto, arts. 285 e 47 a 61). Fora das hipóteses expressas dos arts. 194 a 198 da LC (288 a 292 do decreto), **é vedado** (art. 199; Decreto, art. 293). O ERP do tomador, portanto, **não inventa crédito**: para cada serviço, a regra do Anexo A diz se ele existe.

## 3.2 Empréstimo (mecânica a)

O **tomador de operação de crédito** no regime regular, que não esteja ele mesmo no regime específico da seção, toma crédito **pela mesma alíquota** que o fornecedor paga, **sobre as despesas financeiras efetivamente pagas**, no regime de caixa, calculadas assim, **para cada parcela paga**: do valor da parcela tira-se (I) o principal contido nela, conforme a amortização do contrato, e (II) a **Selic** aplicada sobre o principal (a taxa média das compromissadas de um dia útil) (LC 214, art. 194; Decreto, art. 288). Não toma o crédito o **associado de cooperativa de crédito** que exerceu a opção do art. 271, nem o tomador de operação **referenciada em moeda estrangeira** (art. 197; Decreto, art. 284).

## 3.3 Título de dívida (mecânica a)

O **emissor de título de dívida** (debênture, nota comercial) toma o crédito como no empréstimo, **só no período em que o título é detido por contribuinte do regime específico** (LC 214, art. 195; Decreto, art. 289). Se o título é de **oferta pública** regulada pela CVM, o credor tira da base dele o que passa da Selic e o **devedor não toma crédito** (§ 1º). O mesmo vale quando o credor detém o título por fundo exclusivo com 95% de carteira nesses títulos (§ 2º).

## 3.4 Desconto, cessão, securitização, faturização e antecipação (mecânica a)

O **tomador** da cessão de recebíveis, antecipação, desconto, securitização e faturização, no regime regular, toma crédito **sobre a parte do deságio, no momento da liquidação antecipada, no regime de caixa, que passa da curva de juros futuros da taxa DI pelo prazo da antecipação** (LC 214, art. 196; Decreto, art. 290). O decreto manda usar o **contrato de DI futuro de vencimento mais próximo** do vencimento do recebível e, **no empate, a menor taxa** (art. 290, parágrafo único). A antecipação de recebíveis de **arranjos de pagamento** (cartão) tem a mesma conta no art. 219, § 5º, da LC (Decreto, art. 314, § 6º), e o FIDC e os fundos que antecipam são contribuintes quando não são entidade de investimento (§ 6º).

## 3.5 Arrendamento mercantil (mecânica a)

O **arrendatário** no regime regular, fora do regime específico, toma crédito **sobre o valor das parcelas** e do valor residual do bem, **na medida do efetivo pagamento**, pela **mesma alíquota** da receita de arrendamento correspondente (LC 214, art. 203). O decreto separa os dois tipos: no **operacional**, crédito sobre as parcelas e sobre o **valor de alienação do bem**, pela alíquota da locação e da venda (art. 296); no **financeiro**, sobre as parcelas (alíquota dos serviços financeiros) e sobre o valor residual (alíquota da venda do bem) (art. 298). A alíquota do bem imóvel segue o regime específico imobiliário.

## 3.6 Tarifas, comissões e demais serviços (mecânica b)

**Tarifas e comissões** das operações de crédito, câmbio, títulos, securitização e faturização dão crédito **com base nos valores pagos pelo fornecedor**, também para o tomador que está em regime específico, desde que a despesa não seja deduzida da base dele (LC 214, art. 198; Decreto, art. 292). O crédito também existe, sempre com base no tributo que o fornecedor pagou, para quem compra **administração de consórcio** (art. 205), **serviços de mercados organizados** (art. 221), **serviços de arranjo de pagamento** como credenciado (art. 218), **ativos virtuais** (art. 230), **intermediação** de consórcio, seguro e capitalização, quando o fornecedor identifica o adquirente (arts. 206 e 228) e **seguro**, sobre o tributo pago sobre o prêmio (art. 223, § 1º).

## 3.7 Plano de saúde dos empregados e vales (mecânica c)

O adquirente de plano de assistência à saúde **não tem crédito** (LC 214, art. 238; Decreto, art. 337, caput). A exceção é o plano dado aos **empregados e dependentes por cláusula compulsória de acordo ou convenção coletiva**, e vale até **seis meses depois** do fim do instrumento (Decreto, art. 63, § 1º, VI, e § 5º). O crédito é igual ao **débito de CBS que a operadora pagou no período, vezes a proporção entre o prêmio dos empregados titulares e dependentes e o total arrecadado pela operadora**, e **não alcança a parte repassada aos empregados**: com desconto na folha, o crédito é proporcional ao valor que a empresa suporta (art. 337, I, II e § 1º). A empresa **declara à RFB** a condição e o prazo do instrumento (§ 2º); os descontos vêm do **e-Social** (§ 3º) e, se ele não estiver disponível, a RFB informa o crédito máximo pela DeRE da operadora e a empresa **emite documento fiscal** com o desconto de cada empregado (§§ 4º e 5º). O **vale-transporte, o vale-refeição e o vale-alimentação** dão crédito **igual ao débito do fornecedor** apurado e extinto no regime financeiro, observada a disciplina dos arranjos (Decreto, art. 63, § 1º, VII); o decreto não escreve a fórmula.

## 3.8 O que a lei veda

Não dão crédito: o adquirente de **previdência complementar** (LC 214, art. 226; Decreto, art. 321), de **programas de fidelização** (art. 219-A, II), de **gestão de recursos prestada ao investidor** (art. 211), de **plano funerário** (art. 236, que manda aplicar o art. 238) e de **plano de animais domésticos** (art. 243), o emissor de **título de dívida de oferta pública**, e quem **importa** o serviço financeiro que teria crédito no País (alíquota zero, art. 231; Decreto, art. 328, § 1º, II). O **fundo** de investimento e os cotistas não aproveitam crédito dos fornecedores do fundo, salvo o fundo contribuinte do regime regular (art. 209).

## 3.9 A proporção do que o fornecedor pagou

Nos créditos dos arts. 288 a 290 do decreto (empréstimo, título e desconto), o crédito acompanha o que o fornecedor **extinguiu** da CBS dele: **integral** se ele extinguiu tudo ou se a base dele foi zero ou negativa, **proporcional** se extinguiu em parte, **nenhum** se não pagou (art. 291). A informação vem da Plataforma, e o crédito fica **a apropriar** até lá.

# 4. Achados

**4.1 O documento 94 listava cinco nomes; o desenho pede oito.** Faltam o catálogo das regras (sem ele, cada rotina decide sozinha quem tem crédito), os itens da antecipação (o DI e o prazo são por recebível) e o acordo coletivo do plano de saúde (a lei exige o instrumento e a declaração). O `Cad_Arrendamento_Mercantil` ficou com o nome do documento 94 e liga o contrato geral a um tipo e a um bem.

**4.2 A lei não dá crédito de um jeito só.** São três mecânicas (seção 3): a que o tomador **calcula**, a que ele **recebe do fornecedor** e a que sai da **proporção do débito**. Um registro único (`Mov_Credito_Servico_Regime_Especifico`) serve às três, e o catálogo diz qual vale em cada caso (`Forma_Calculo`). Assim, o cliente que só compra seguro e consórcio tem crédito registrado sem cálculo próprio, e o que toma empréstimo tem o cálculo completo.

**4.3 A proporção do art. 291 não tinha onde ficar.** O crédito de empréstimo, título e desconto depende do quanto o fornecedor extinguiu, e essa informação chega **depois** do pagamento. O dicionário já tem o estado "a apropriar" em `Mov_Credito_Fiscal`, mas não o **percentual extinto**. O campo nasce no registro novo. Leitura minha: o art. 291 vale só para os arts. 288 a 290 do decreto, e **não** para o arrendamento (art. 296 e 298) nem para a antecipação de cartão (art. 314, § 6º); o contador confirma (C243).

**4.4 O decreto não diz sobre qual principal a Selic incide.** O art. 194 da LC e o art. 288 do decreto mandam tirar "o montante correspondente à aplicação da taxa Selic sobre o principal", sem dizer se o principal é o **saldo devedor do período** ou só o **principal contido na parcela**, nem de qual data a Selic corre. Li como a **Selic acumulada entre o pagamento anterior (ou a contratação) e este pagamento, aplicada sobre o saldo do principal no início do período**, que é o que dá sentido econômico à dedução (o juro "livre de risco" sobre o que se deve). É leitura minha, marcada provisória (C239). Ligada a ela: a alíquota se aplica **sobre a base** como a lei escreve (literal), e não "por dentro" (C239, item d).

**4.5 A curva DI não tem fórmula e o empate é escrito de dois jeitos.** Os arts. 196 e 219, § 5º, da LC mandam deduzir "o valor correspondente à curva de juros futuros da taxa DI, pelo prazo da antecipação", e o decreto só diz qual contrato usar. Li como o **valor líquido antecipado capitalizado pela taxa DI até o vencimento** (`Valor_Liquido × ((1 + taxa)^(dias úteis ÷ 252) − 1)`), provisório (C242). E o empate de vencimentos é resolvido com a **menor** taxa para o crédito do tomador (art. 290, parágrafo único) e com a **maior** para a dedução do fornecedor (art. 314, § 2º): se o mesmo recebível fosse antecipado por um arranjo, o crédito do tomador e o débito do fornecedor usariam taxas diferentes. É raro, mas vai ao contador (C242, item c).

**4.6 A LC e o decreto não dizem o mesmo no arrendamento.** A LC 214 (art. 203) dá crédito sobre "as parcelas das contraprestações e o valor residual"; o decreto, no **operacional**, acrescenta o **valor de alienação do bem** (art. 296), que a LC não cita. A regra de alienação nasce com `Origem_Regra = decreto` (C241). E há uma diferença de base: o fornecedor do arrendamento **financeiro** tributa só os **encargos financeiros** da parcela, a valor presente (art. 297, § 1º), mas o crédito do tomador fala em "valor das parcelas". Pela leitura literal o crédito incide na parcela inteira, e o crédito passaria do tributo que o fornecedor pagou. Por isso `Mov_Arrendamento_Parcela` guarda os **dois valores** (a parcela e os encargos, quando o arrendador informa) e a pergunta vai ao contador (C241).

**4.7 O emissor de título não sabe quem o detém.** Para o crédito do art. 195 o título precisa estar com contribuinte do regime específico, e para a oferta pública o devedor perde o crédito. O ERP do emissor não vê o detentor (o título circula). O campo `Detentor_Regime_Especifico` vem da Plataforma ou o usuário **confirma**; sem a confirmação, o crédito fica a apropriar (C240).

**4.8 A moeda estrangeira não tira o crédito das tarifas.** O art. 197, II, da LC veda o crédito de juros do empréstimo referenciado em moeda estrangeira, "observado o art. 198", e o decreto diz o mesmo com o art. 292: **tarifas e comissões continuam com crédito** (a regra `cred_tarifa_comissao` não tem a marca de moeda). Hoje `Mov_Emprestimo` **não tem credor nem marca de moeda**, e sem eles o Motor não aplica a vedação; por isso entram dois campos.

**4.9 Plano de saúde: três fontes de dado e uma declaração.** O crédito mistura o **débito da operadora** (vem da RFB), a **proporção dos empregados** (vem da operadora) e o **desconto da folha** (vem do e-Social, da folha do ERP ou de documento fiscal da empresa). O `Mov_Rh_Beneficio_Credito_Cbs` guarda os três, com a origem de cada um, e o `Mov_Rh_Beneficio_Acordo_Coletivo` guarda o instrumento e a declaração à RFB. O ato conjunto que regulamenta a declaração e o documento fiscal do § 5º **não foi publicado**: os campos existem, a emissão espera o ato. O prêmio que cobre **sócios e administradores** fica fora do crédito (o art. 63 só trata de empregados).

**4.10 Os vales não têm fórmula.** O decreto diz "créditos equivalentes aos débitos do fornecedor" e remete aos arranjos, sem dizer como repartir o débito entre as empresas que usam o mesmo emissor. A regra `cred_vale_beneficio` **registra** o que o fornecedor informar, sem cálculo (C244).

**4.11 Em 2026 o fornecedor paga CBS de 0,9%, e a regra de soma só vale de 2027.** O art. 480, I, do decreto fixa a CBS dos serviços financeiros em 0,9% em 2026, mas o crédito do tomador é descrito sem data, e as alíquotas do art. 233 da LC começam em 2027. As regras do catálogo nascem com vigência a partir de **01/01/2027**, como as alíquotas do B4 (Q198-5), e o contador diz se há crédito do tomador em 2026 (C245).

**4.12 Nenhuma decisão anterior muda.** A D-N273 (redutor), a D-N282 (split de 2028) e a D-N323 (parâmetros desde 01/01/2026) ficam como estão: o B0b-2 não lê o redutor, não depende do split e usa 2027 só porque a soma das alíquotas do B4 já usa. O princípio "o ERP avisa e não bloqueia" (D-N284) vale em todas as regras da seção 6.

# 5. Proposta

## 5.1 Nenhum domínio novo

O B0b-2 **usa os domínios que o B4 já criou**: `base_regime_especifico` (23 bases, a base do fornecedor a que cada regra se liga) e `tipo_relacao_dere` (o valor `tomador_servico_financeiro`, que o B4 já tem). Dois valores entram em `tipo_emprestimo`, domínio aberto de `Cad_Classe_Sistema` (valor novo é carga, nunca mudança de estrutura): **`debenture`** e **`nota_comercial`** (Anexo B.2). As novas enumerações são **campos de lista fechada pela lei** (por exemplo, `Forma_Calculo`, `Tipo_Arrendamento`, `Origem_Tipo`) e ficam no texto do campo.

## 5.2 As oito entidades

| Entidade | Módulo | Para quê | Vigência | Campos |
|--------------------------|-----------------|-------------------------------------------|--------|------|
| `Cad_Regra_Credito_Tomador` | Contabilidade & Fiscal | O catálogo legal do crédito de quem compra o serviço do regime específico: para cada situação (empréstimo, título de dívida, desconto, arrendamento, tarifa, plano de saúde dos empregados e as demais), se há crédito, como se calcula e quais vedações valem. Com vigência. | sim | 21 |
| `Cad_Arrendamento_Mercantil` | Contabilidade & Fiscal | O contrato de arrendamento mercantil em que a empresa é a arrendatária (leasing de frota, de equipamentos ou de imóvel): o tipo, o bem, os prazos e o valor residual. Especializa o contrato de Gestão de Contratos. | não | 19 |
| `Mov_Arrendamento_Parcela` | Contabilidade & Fiscal | Cada pagamento do arrendamento: contraprestação, valor residual ou alienação do bem, com o título a pagar. É o que o crédito do arrendatário usa, no regime de caixa. | não | 8 |
| `Mov_Antecipacao_Recebivel` | Contabilidade & Fiscal | A operação em que a empresa recebe antes o que tem a receber (desconto de duplicatas, cessão, factoring, securitização ou antecipação de recebíveis de cartão e outros arranjos): o cessionário, o deságio e as tarifas. | não | 14 |
| `Mov_Antecipacao_Recebivel_Item` | Contabilidade & Fiscal | Cada recebível antecipado: o título ou a parcela de cartão, o valor de face, o líquido, o contrato de DI usado e a parte do deságio que passa da curva DI. O prazo e a taxa ficam gravados para a conta poder ser refeita. | não | 15 |
| `Mov_Credito_Servico_Regime_Especifico` | Contabilidade & Fiscal | O registro único do crédito de quem compra o serviço: a regra usada, o que foi pago, as deduções, a base, as alíquotas gravadas, a proporção do art. 291, as marcas das vedações e o crédito escriturável que nasce em Mov_Credito_Fiscal. | não | 38 |
| `Mov_Rh_Beneficio_Acordo_Coletivo` | Folha & RH | O acordo ou a convenção coletiva que obriga a empresa a dar o benefício (plano de saúde), com a vigência e a declaração à RFB. A janela de seis meses depois do fim do acordo sai do parâmetro, e não de um campo. | não | 11 |
| `Mov_Rh_Beneficio_Credito_Cbs` | Folha & RH | O crédito mensal da empresa que paga plano de saúde aos empregados: o que ela pagou, o que descontou da folha, o que a operadora informou e a proporção dos empregados. O valor do crédito sai em Mov_Credito_Servico_Regime_Especifico. | não | 21 |

Em `Cad_Regra_Credito_Tomador` valem as convenções da Fase 0: `ID_X` é a identidade, `ID_X_Versao` a chave da versão, e `Vigencia_Inicio`, `Vigencia_Fim` (31/12/9999 quando em aberto) e `Motivo_Vigencia` fecham cada linha. Nos sete movimentos e cadastros sem vigência, o que é **calculado** é gravado na própria linha (Q96-17), e o que muda de significado com o tempo (alíquota, o credor estar no regime específico, a condição de cooperativa) é **gravado no momento**.

### `Cad_Regra_Credito_Tomador` (Contabilidade & Fiscal, com vigência, 21 campos)

O catálogo legal do crédito de quem compra o serviço do regime específico: para cada situação (empréstimo, título de dívida, desconto, arrendamento, tarifa, plano de saúde dos empregados e as demais), se há crédito, como se calcula e quais vedações valem. Com vigência.

| Campo | Tipo | Descrição |
|----------------------|---------------------------------------|---------------------------------------|
| `ID_Regra_Credito_Tomador` | identificador | Chave. |
| `ID_Regra_Credito_Tomador_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Regra_Credito_Tomador_Versao). Fase 0, seção 2. |
| `Codigo` | código (até 30) --- identidade | Estável, em minúsculas, com o prefixo cred_ (por exemplo, cred_operacao_credito). |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base de cálculo do fornecedor a que a regra se liga (a mesma lista do B4). |
| `Descricao` | texto | A situação do tomador em palavras do dicionário. |
| `Forma_Calculo` | enumeração {excedente_principal_selic, excedente_curva_di, parcela_pela_aliquota, valor_pago_pelo_fornecedor, proporcao_debito_fornecedor, sem_credito} | Como o crédito nasce. excedente_principal_selic: despesa financeira paga menos o principal e a Selic sobre o principal (LC 214, art. 194). excedente_curva_di: parcela do deságio que passa da curva DI (arts. 196 e 219, § 5º). parcela_pela_aliquota: a parcela paga vezes a alíquota da receita do fornecedor (art. 203). valor_pago_pelo_fornecedor: o crédito é o tributo que o fornecedor informou ter pago (arts. 190, 198, 205, 218, 221 e outros). proporcao_debito_fornecedor: o débito do fornecedor vezes uma proporção (plano de saúde e capitalização). sem_credito: a lei veda. |
| `Regime_Caixa` | booleano | O crédito nasce no efetivo pagamento. |
| `Aplica_Proporcao_Extincao` | booleano | O crédito segue a parte da CBS que o fornecedor extinguiu: integral se a base dele foi zero ou negativa, proporcional se a extinção foi parcial, nenhum se não pagou (Decreto, art. 291). Vale só para empréstimo, título de dívida e desconto. |
| `Veda_Associado_Cooperativa` | booleano | Não dá crédito ao associado de cooperativa de crédito que exerceu a opção do art. 271 (LC 214, art. 197, I; Decreto, art. 284, I). |
| `Veda_Referenciado_Moeda_Estrangeira` | booleano | Não dá crédito a operação de crédito nem a título de dívida referenciados em moeda estrangeira (LC 214, art. 197, II; Decreto, art. 284, II). Tarifas e comissões continuam com crédito (art. 198). |
| `Admite_Tomador_Regime_Especifico` | booleano | O tomador que também está em regime específico pode tomar o crédito (tarifas e comissões, desde que a despesa não seja deduzida da base dele: LC 214, art. 198, parágrafo único). Falso: só quem está fora do regime específico da seção toma o crédito. |
| `Exige_Acordo_Coletivo` | booleano | O crédito depende de acordo ou convenção coletiva com cláusula compulsória (plano de saúde dos empregados: Decreto, art. 63, § 1º, VI). |
| `Exige_Declaracao_Rfb` | booleano | O tomador deve declarar à RFB a condição e o prazo do acordo ou da convenção (Decreto, art. 337, § 2º). |
| `Condicao_Texto` | texto, opcional | A condição que o Motor mostra ao usuário. |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | De onde vem a regra. O que só o Decreto traz vai para o contador. |
| `Fundamento_Legal` | texto | Os artigos, da LC e do Decreto. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Arrendamento_Mercantil` (Contabilidade & Fiscal, sem vigência, 19 campos)

O contrato de arrendamento mercantil em que a empresa é a arrendatária (leasing de frota, de equipamentos ou de imóvel): o tipo, o bem, os prazos e o valor residual. Especializa o contrato de Gestão de Contratos.

| Campo | Tipo | Descrição |
|----------------------|--------------------------------|-----------------------------------------------|
| `ID_Arrendamento_Mercantil` | identificador | Chave. |
| `ID_Filial` | referência (Cad_Filial) | A filial arrendatária. |
| `ID_Participante_Arrendador` | referência (Cad_Participante) | A arrendadora. Se ela está em regime específico (Cad_Participante_Regime_Base) é o Motor que lê; o campo não repete isso. |
| `ID_Contrato` | referência (Cad_Gestao_Contrato), opcional | O contrato geral, quando a empresa o controla em Gestão de Contratos (aditivos, garantias, penalidades). |
| `Numero_Contrato` | código (até 60) | O número do contrato de arrendamento. |
| `Tipo_Arrendamento` | enumeração {operacional, financeiro} | Decide as bases do fornecedor (quatro, no B4) e a regra de crédito do arrendatário (Decreto, arts. 296 e 298). |
| `Natureza_Bem` | enumeração {movel, imovel} | O imóvel tem alíquota própria de locação e de venda, no regime específico imobiliário (LC 214, art. 201, I, a, 1, b, 1 e d, 1). |
| `Descricao_Bem` | texto | O bem arrendado. |
| `ID_Cclasstrib_Bem` | referência (Cad_Cclasstrib), opcional | A classificação tributária do bem, de onde o Motor lê a alíquota de locação e de venda quando o bem não é imóvel (arrendamento operacional e valor residual). |
| `Data_Assinatura` | data | Quando o contrato foi assinado. |
| `Data_Inicio` | data | Início do arrendamento. |
| `Data_Fim_Prevista` | data, opcional | Fim previsto, quando há. |
| `Numero_Parcelas_Contratadas` | número | Quantidade de contraprestações pactuadas. |
| `Valor_Bem_Arrendado` | número, opcional | O custo de aquisição do bem pela arrendadora, quando o contrato o diz (o valor residual tributado não pode ficar abaixo dele, Decreto, art. 297, § 2º, II). |
| `Valor_Residual_Garantido` | número, opcional | O valor residual garantido pactuado no arrendamento financeiro, ainda que parcelado (art. 297, II). |
| `Taxa_Encargos_Financeiros` | número, opcional | A taxa de encargos financeiros do contrato (informativa; o ajuste a valor presente é do arrendador, art. 297, § 1º, I). |
| `Opcao_Compra_Exercida` | booleano | Verdadeiro quando a empresa exerceu a opção de compra (o valor residual pago no exercício é parcela com crédito). |
| `Data_Opcao_Compra` | data, opcional | Quando exerceu a opção de compra. |
| `Situacao` | enumeração {vigente, encerrado, rescindido} | A situação do contrato. |

### `Mov_Arrendamento_Parcela` (Contabilidade & Fiscal, sem vigência, 8 campos)

Cada pagamento do arrendamento: contraprestação, valor residual ou alienação do bem, com o título a pagar. É o que o crédito do arrendatário usa, no regime de caixa.

| Campo | Tipo | Descrição |
|-------------------|--------------------------------------|-------------------------------------------|
| `ID_Arrendamento_Parcela` | identificador | Chave. |
| `ID_Arrendamento_Mercantil` | referência (Cad_Arrendamento_Mercantil) | O contrato. |
| `Numero_Parcela` | número | A ordem do pagamento dentro do contrato (única por contrato e tipo). |
| `Tipo_Pagamento` | enumeração {contraprestacao, valor_residual, alienacao_bem} | contraprestacao: parcela periódica. valor_residual: o pago no exercício da opção de compra (financeiro). alienacao_bem: o valor de alienação do bem no arrendamento operacional (Decreto, art. 296). |
| `Data_Vencimento` | data | O vencimento. |
| `Valor_Parcela` | número | O valor total da parcela, com tarifas e comissões incluídas. |
| `Valor_Encargos_Financeiros` | número, opcional | A parte de encargos financeiros da parcela, quando o arrendador a informa. Serve à leitura alternativa do crédito (C241): o fornecedor tributa só essa parte no arrendamento financeiro (Decreto, art. 297, § 1º). |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título a pagar da parcela (Origem_Tipo = arrendamento_parcela). O pagamento é a baixa dele. |

### `Mov_Antecipacao_Recebivel` (Contabilidade & Fiscal, sem vigência, 14 campos)

A operação em que a empresa recebe antes o que tem a receber (desconto de duplicatas, cessão, factoring, securitização ou antecipação de recebíveis de cartão e outros arranjos): o cessionário, o deságio e as tarifas.

| Campo | Tipo | Descrição |
|-------------------|-----------------------------------------|-----------------------------------------|
| `ID_Antecipacao_Recebivel` | identificador | Chave. |
| `ID_Filial` | referência (Cad_Filial) | A filial que antecipou (a tomadora do serviço). |
| `ID_Participante_Cessionario` | referência (Cad_Participante) | O banco, o factoring, o fundo, a credenciadora ou a instituição de pagamento que antecipou. |
| `ID_Base_Regime` | referência (Cad_Classe_Sistema, domínio = base_regime_especifico) | A base do fornecedor: credito_cambio_tvm (desconto, cessão e antecipação de crédito), securitizacao_faturizacao ou antecipacao_recebivel_arranjo. |
| `Modalidade` | enumeração {desconto_duplicata, cessao_recebivel, factoring, securitizacao, antecipacao_arranjo, outra} | Como a operação é chamada. A base é a que decide a regra de crédito; a modalidade serve à tela e ao relatório. |
| `Numero_Bordero` | código (até 60), opcional | O borderô ou o número da operação no cessionário. |
| `Data_Operacao` | data | A data da liquidação antecipada: é a do crédito, no regime de caixa (LC 214, arts. 196 e 219, § 5º). |
| `Valor_Face_Total` | número | Calculado: a soma do valor de face dos itens. |
| `Valor_Liquido_Recebido` | número | Calculado: a soma do valor líquido dos itens, sem as tarifas. |
| `Valor_Desagio_Total` | número | Calculado: face menos líquido (o deságio ou desconto da operação). |
| `Valor_Tarifas_Comissoes` | número, opcional | Tarifas e comissões cobradas à parte. Dão crédito pela regra cred_tarifa_comissao, com base no que o fornecedor pagou (LC 214, art. 198). |
| `ID_Conta_Contabil` | referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco/Caixa/Aplicação) | Onde o dinheiro entrou. |
| `ID_Documento` | referência (Cad_Documento), opcional | O borderô ou o contrato, guardado no GED. |
| `Situacao` | enumeração {efetivada, estornada} | estornada quando a operação foi desfeita; o crédito é estornado junto. |

### `Mov_Antecipacao_Recebivel_Item` (Contabilidade & Fiscal, sem vigência, 15 campos)

Cada recebível antecipado: o título ou a parcela de cartão, o valor de face, o líquido, o contrato de DI usado e a parte do deságio que passa da curva DI. O prazo e a taxa ficam gravados para a conta poder ser refeita.

| Campo | Tipo | Descrição |
|---------------------|--------------------------------|-----------------------------------------------|
| `ID_Antecipacao_Item` | identificador | Chave. |
| `ID_Antecipacao_Recebivel` | referência (Mov_Antecipacao_Recebivel) | A operação. |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título a receber antecipado (duplicata, boleto). Um dos dois, este ou a transação de cartão. |
| `ID_Transacao_Cartao` | referência (Mov_Transacao_Cartao), opcional | A transação de cartão cuja parcela foi antecipada. |
| `Numero_Parcela_Cartao` | número, opcional | A parcela da transação antecipada, quando o item é de cartão. |
| `ID_Baixa` | referência (Mov_Titulo_Baixa), opcional | A baixa do recebível pela antecipação (tipo de baixa cadastrado pelo usuário; o deságio vai em Valor_Desconto). Vazia até a baixa. |
| `Data_Vencimento_Recebivel` | data | O vencimento original do recebível. |
| `Valor_Face` | número | O valor do recebível. |
| `Valor_Liquido_Antecipado` | número | O valor recebido na antecipação. |
| `Valor_Desagio` | número | Calculado: face menos líquido. |
| `ID_Serie_Di` | referência (Cad_Serie_Cotacao), opcional | A série do contrato de DI futuro cujo vencimento é o mais próximo do vencimento do recebível (Decreto, art. 290, parágrafo único, e art. 314, § 2º). |
| `Taxa_Di_Aplicada` | número, opcional | A taxa do contrato na data da operação, gravada. |
| `Prazo_Dias_Uteis` | número, opcional | O prazo da antecipação, da data da operação ao vencimento. |
| `Valor_Curva_Di` | número, opcional | Calculado: o valor correspondente à curva DI pelo prazo (leitura do documento 200, seção 5.4; C242). Gravado, porque a taxa muda. |
| `Valor_Desagio_Excedente` | número, opcional | Calculado: o deságio menos a curva DI, nunca negativo. É a base do crédito. |

### `Mov_Credito_Servico_Regime_Especifico` (Contabilidade & Fiscal, sem vigência, 38 campos)

O registro único do crédito de quem compra o serviço: a regra usada, o que foi pago, as deduções, a base, as alíquotas gravadas, a proporção do art. 291, as marcas das vedações e o crédito escriturável que nasce em Mov_Credito_Fiscal.

| Campo | Tipo | Descrição |
|--------------------|----------------------------------------|----------------------------------------|
| `ID_Credito_Servico` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa tomadora, titular do crédito. |
| `ID_Regra_Credito_Tomador` | referência (Cad_Regra_Credito_Tomador) | A regra usada; a versão vigente na data do pagamento fica gravada pela data. |
| `Competencia_Apuracao` | competência | A competência do pagamento (regime de caixa). |
| `Origem_Tipo` | enumeração {emprestimo_parcela, arrendamento_parcela, antecipacao_recebivel, titulo_baixa, informacao_fornecedor, beneficio_empregado} | O que gerou o registro. titulo_baixa: a baixa de um título de tarifa, comissão ou serviço. informacao_fornecedor: o crédito veio da Plataforma, sem cálculo próprio. beneficio_empregado: o registro de Mov_Rh_Beneficio_Credito_Cbs. |
| `ID_Origem` | referência genérica | A parcela do empréstimo, a parcela do arrendamento, a antecipação, a baixa ou o crédito do benefício, conforme Origem_Tipo. |
| `ID_Participante_Fornecedor` | referência (Cad_Participante) | O prestador do serviço financeiro, a operadora do plano ou a arrendadora. |
| `ID_Titulo_Baixa` | referência (Mov_Titulo_Baixa), opcional | O pagamento que gerou o crédito. |
| `Data_Pagamento` | data | O dia do efetivo pagamento. |
| `Valor_Pago` | número | O que foi pago: a parcela, o deságio ou a tarifa. Na proporção de débito, o débito do fornecedor. |
| `Valor_Principal_Deduzido` | número, opcional | Calculado, só no empréstimo: o principal contido na parcela paga (LC 214, art. 194, I). |
| `ID_Serie_Selic` | referência (Cad_Serie_Cotacao), opcional | A série da Selic usada na dedução do art. 194, II. |
| `Saldo_Principal_Periodo` | número, opcional | Calculado: o saldo do principal sobre o qual a Selic foi aplicada (leitura do documento 200, seção 5.4; C239). |
| `Percentual_Selic_Periodo` | número, opcional | Calculado: a Selic acumulada no período, em percentual, com 8 casas. |
| `Valor_Selic_Deduzido` | número, opcional | Calculado: a Selic aplicada sobre o principal (art. 194, II). |
| `Valor_Curva_Di_Deduzido` | número, opcional | Só na antecipação: a soma da curva DI dos itens (arts. 196 e 219, § 5º). |
| `Fator_Proporcional` | número, opcional | Só na proporção de débito (plano de saúde): a proporção dos empregados vezes a parte que a empresa custeia. |
| `Valor_Base_Credito` | número | Calculado: a base sobre a qual a alíquota incide, ou o débito do fornecedor na proporção de débito. Zero quando não há crédito. |
| `Aliquota_Cbs_Aplicada` | número, opcional | Gravada no momento: a alíquota da CBS do fornecedor (a mesma devida por ele). |
| `Aliquota_Ibs_Aplicada` | número, opcional | Gravada no momento: a alíquota do IBS do fornecedor. |
| `Valor_Credito_Cbs_Calculado` | número | Calculado: o crédito de CBS antes da proporção do art. 291. |
| `Valor_Credito_Ibs_Calculado` | número | Calculado: o crédito de IBS antes da proporção do art. 291. |
| `Proporcao_Extincao_Debito` | número, opcional | A parte da CBS do fornecedor que foi extinta, em percentual (Decreto, art. 291). Vazia até a Plataforma informar; vazia também onde a regra não aplica a proporção. |
| `Valor_Credito_Cbs_Apropriavel` | número, opcional | Calculado: o crédito de CBS depois da proporção. |
| `Valor_Credito_Ibs_Apropriavel` | número, opcional | Calculado: o crédito de IBS depois da proporção. |
| `Detentor_Regime_Especifico` | booleano, opcional | Só no título de dívida: o detentor do título, no período, é contribuinte do regime específico (LC 214, art. 195). Informado pela Plataforma ou confirmado pelo usuário. |
| `Associado_Cooperativa_Opcao` | booleano | Gravado no momento: o tomador é associado de cooperativa de crédito que exerceu a opção do art. 271 (art. 197, I). |
| `Referenciado_Moeda_Estrangeira` | booleano | Gravado no momento: a operação ou o título é referenciado em moeda estrangeira (art. 197, II). |
| `Tomador_Regime_Especifico` | booleano | Gravado no momento: a empresa está em regime específico da seção (Cad_Participante_Regime_Base). |
| `Motivo_Sem_Credito` | enumeração {regra_veda, cooperativa, moeda_estrangeira, oferta_publica, tomador_regime_especifico, fornecedor_inadimplente, fornecedor_sem_informacao, fornecedor_fora_regime, sem_excedente, fora_vigencia}, opcional | Por que o crédito é zero. fornecedor_fora_regime: o credor ou o prestador não está em regime específico na data, e não há débito do qual nasça crédito. |
| `Origem_Valor` | enumeração {calculado_pelo_erp, informado_pelo_fornecedor, ajustado_pelo_usuario} | Quem fixou o valor. O usuário pode ajustar com motivo; o ERP avisa e não bloqueia. |
| `ID_Espelho_Conta` | referência (Mov_Cbs_Apuracao_Espelho_Conta), opcional | A linha da aba de créditos da Plataforma que corresponde a este registro, para a conferência. |
| `ID_Credito_Fiscal_Cbs` | referência (Mov_Credito_Fiscal), opcional | O crédito de CBS escriturado (Origem = servico_financeiro_tomador ou beneficio_empregado). |
| `ID_Credito_Fiscal_Ibs` | referência (Mov_Credito_Fiscal), opcional | O crédito de IBS escriturado. |
| `Regra_Provisoria` | booleano | Gravado no momento: a regra usada ainda não tinha sido validada pelo contador. |
| `ID_Usuario_Ajuste` | referência (Cad_Usuario), opcional | Quem ajustou o valor. |
| `Motivo_Ajuste` | texto, opcional | Obrigatório quando Origem_Valor = ajustado_pelo_usuario (aviso). |
| `Data_Hora_Calculo` | data/hora | Quando o Motor calculou ou recebeu o valor. |

### `Mov_Rh_Beneficio_Acordo_Coletivo` (Folha & RH, sem vigência, 11 campos)

O acordo ou a convenção coletiva que obriga a empresa a dar o benefício (plano de saúde), com a vigência e a declaração à RFB. A janela de seis meses depois do fim do acordo sai do parâmetro, e não de um campo.

| Campo | Tipo | Descrição |
|---------------------|----------------------------------|---------------------------------------------|
| `ID_Acordo_Coletivo` | identificador | Chave. |
| `ID_Beneficio` | referência (Cad_Rh_Beneficio) | O benefício, do tipo plano_saude. |
| `Tipo_Instrumento` | enumeração {acordo_coletivo, convencao_coletiva} | O instrumento. |
| `Numero_Registro` | código (até 60), opcional | O número do registro do instrumento. |
| `Clausula_Compulsoria` | booleano | O instrumento traz cláusula compulsória para o plano (Decreto, art. 63, § 1º, VI). Falso: o benefício não dá crédito. |
| `Data_Inicio_Vigencia` | data | O primeiro dia de vigência do instrumento. |
| `Data_Fim_Vigencia` | data, opcional | O último dia; vazio enquanto vigente. O crédito vale até seis meses depois dele (art. 63, § 5º). |
| `ID_Documento` | referência (Cad_Documento), opcional | O instrumento, guardado no GED. |
| `Situacao_Declaracao` | enumeração {nao_declarado, declarado, rejeitado} | A declaração à RFB do art. 337, § 2º. O ERP só registra, porque o ato conjunto que a regulamenta não foi publicado. |
| `Data_Declaracao` | data, opcional | Quando declarou. |
| `Numero_Protocolo_Declaracao` | código (até 60), opcional | O protocolo da declaração. |

### `Mov_Rh_Beneficio_Credito_Cbs` (Folha & RH, sem vigência, 21 campos)

O crédito mensal da empresa que paga plano de saúde aos empregados: o que ela pagou, o que descontou da folha, o que a operadora informou e a proporção dos empregados. O valor do crédito sai em Mov_Credito_Servico_Regime_Especifico.

| Campo | Tipo | Descrição |
|--------------------|-------------------------------------|------------------------------------------|
| `ID_Beneficio_Credito` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa contratante. |
| `ID_Beneficio` | referência (Cad_Rh_Beneficio) | O benefício (plano_saude). |
| `Competencia` | competência | O mês. |
| `ID_Acordo_Coletivo` | referência (Mov_Rh_Beneficio_Acordo_Coletivo), opcional | O instrumento que dá a cláusula compulsória. Sem ele, o ERP avisa que não há crédito. |
| `ID_Participante_Operadora` | referência (Cad_Participante) | A operadora ou a administradora de benefícios. |
| `Valor_Premio_Pago_Total` | número | O que a empresa pagou à operadora no mês pelo contrato (prêmio e contraprestação). |
| `Valor_Premio_Empregados` | número | A parte do pagamento que cobre os empregados titulares e os dependentes deles. O que cobre sócios ou outros fica fora (art. 63, § 1º, VI). |
| `Valor_Descontado_Empregados` | número | O que a folha descontou dos empregados no mês (art. 337, I, II e § 1º). |
| `Origem_Desconto` | enumeração {folha_erp, esocial, documento_fiscal} | De onde vem o desconto: da folha do ERP, do e-Social por convênio (art. 337, § 3º) ou do documento fiscal da empresa (§ 5º). |
| `Valor_Premios_Entidade_Total` | número, opcional | O total de prêmios e contraprestações arrecadados pela operadora no período, informado por ela na DeRE. |
| `Valor_Debito_Cbs_Entidade` | número, opcional | O débito de CBS pago pela operadora no período (base do crédito). |
| `Valor_Debito_Ibs_Entidade` | número, opcional | O débito de IBS pago pela operadora no período. |
| `Fonte_Informacao_Operadora` | enumeração {dere_rfb, informado_usuario} | Se o dado da operadora veio da RFB (§ 4º) ou foi digitado. |
| `Proporcao_Empregados` | número, opcional | Calculado: Valor_Premio_Empregados dividido por Valor_Premios_Entidade_Total (art. 337, I, b). |
| `Percentual_Custeio_Empresa` | número, opcional | Calculado: o que a empresa suportou (pago menos descontado) sobre o pago (art. 337, II e § 1º). |
| `Dentro_Janela_Acordo` | booleano | Calculado: o mês está dentro da vigência do instrumento ou até seis meses depois (art. 63, § 5º). |
| `ID_Documento_Fiscal` | referência (Mov_Documento_Fiscal), opcional | O documento fiscal do art. 337, § 5º, com o desconto de cada empregado, quando o e-Social não está disponível. O ato conjunto não saiu; o campo só guarda a referência. |
| `ID_Credito_Servico` | referência (Mov_Credito_Servico_Regime_Especifico), opcional | O registro de crédito que o Motor gerou. |
| `Situacao` | enumeração {calculado, sem_credito} | sem_credito quando falta acordo com cláusula compulsória, o mês está fora da janela ou a operadora não informou. |
| `Motivo_Sem_Credito` | texto, opcional | Por que o crédito é zero. |

## 5.3 O que muda em entidades que já existem

**Cinco campos novos:**

| Entidade | Campo | Tipo | Para quê |
|-----------|------------------|-----------------------------------|-----------------------------------|
| `Mov_Emprestimo` | `ID_Participante_Credor` | referência (Cad_Participante), opcional | O banco, o fundo ou o investidor que emprestou. É por ele que o Motor sabe se o credor está em regime específico. Aviso quando vazio num empréstimo com parcela paga. |
| `Mov_Emprestimo` | `Forma_Captacao` | enumeração {operacao_credito, titulo_divida, titulo_divida_oferta_publica} | Operação de crédito (padrão), título de dívida (debênture, nota comercial) ou título de dívida com oferta pública regulada pela CVM, caso em que o emissor não toma crédito (LC 214, art. 195, § 1º, II). Novos tipos de título entram em ID_Tipo_Emprestimo (domínio aberto). |
| `Mov_Emprestimo` | `Referenciado_Moeda_Estrangeira` | booleano | Operação ou título referenciado em moeda estrangeira: não dá crédito de juros (LC 214, art. 197, II). Padrão falso. |
| `Cad_Serie_Cotacao` | `Uso_Legal_Cbs` | enumeração {selic_diaria, di_futuro}, opcional | Marca a série usada pela lei: a Selic média das compromissadas de um dia (LC 214, art. 194, II) ou um contrato de DI futuro (arts. 196 e 219, § 5º). Vazio nas demais. |
| `Cad_Serie_Cotacao` | `Data_Vencimento_Contrato` | data, opcional | O vencimento do contrato de DI futuro; só quando Uso_Legal_Cbs = di_futuro. O Motor escolhe a série de vencimento mais próximo do recebível. |

**Textos e enumerações** (sem campo novo):

| Entidade | Mudança |
|------------------------------------------------|----------------------------------------------------|
| `Mov_Credito_Fiscal.Origem` | Dois valores novos: **`servico_financeiro_tomador`** e **`beneficio_empregado`**. O crédito nasce na mesma entidade e usa o mesmo ciclo de estados (a apropriar, apropriado, inapropriável, utilizado). |
| `Mov_Titulo.Origem_Tipo` | Valor novo **`arrendamento_parcela`**: a parcela do arrendamento gera título a pagar como a parcela do empréstimo. |
| `Cad_Criterio_Uso_Preponderante.Credito_Igual_Debito_Fornecedor` | **Só texto:** o campo passa a dizer que o cálculo do crédito do plano de saúde está em `Mov_Rh_Beneficio_Credito_Cbs`. |
| `Cad_Classe_Sistema` | **Só carga:** `tipo_emprestimo` ganha `debenture` e `nota_comercial`. |
| `Cad_Arrendamento_Mercantil.ID_Contrato` | **Chave opcional adiada:** o contrato geral é de `Cad_Gestao_Contrato`, da onda de Gestão de Contratos (onda 5); a chave entra quando a onda for gerada. Ela **não** está na contagem da seção 8. |

## 5.4 Como o crédito é calculado

O Motor calcula **por pagamento efetivo** (regime de caixa): o gatilho é a baixa em `Mov_Titulo_Baixa` ou o fechamento do mês do plano de saúde. O ERP **calcula, grava e avisa; não bloqueia**. O passo comum a todas as formas:

- **Passo 1. Acha a regra.** Pelo tipo da origem (empréstimo, título, arrendamento, antecipação, informação do fornecedor, benefício), lê `Cad_Regra_Credito_Tomador` com vigência na data do pagamento. Sem regra, **avisa** e não calcula.
- **Passo 2. Confere as vedações.** Aplica as marcas da regra: tomador **no regime específico** (marca `Admite_Tomador_Regime_Especifico`), associado de **cooperativa** que fez a opção (`Veda_Associado_Cooperativa`, lida de `Cad_Participante_Qualificacao_Cbs`), operação **referenciada em moeda estrangeira** (`Veda_Referenciado_Moeda_Estrangeira`) e **fornecedor fora do regime específico**. Se uma vale, o registro sai com a base zero e `Motivo_Sem_Credito`, que fica visível.
- **Passo 3. Calcula pela forma da regra** (`Forma_Calculo`), como a seguir.
- **Passo 4. Grava as alíquotas** em `Aliquota_Cbs_Aplicada` e `Aliquota_Ibs_Aplicada`, lidas de `Cad_Regime_Aliquota_Soma` do B4 (ou da alíquota do bem), com vigência de 01/01/2027.
- **Passo 5. Aplica a proporção do art. 291**, quando a regra marca `Aplica_Proporcao_Extincao`: o crédito apropriável é o calculado vezes `Proporcao_Extincao_Debito`; enquanto a Plataforma não informa, a proporção fica vazia, o apropriável é zero e o crédito fica **a apropriar**.
- **Passo 6. Grava** o registro em `Mov_Credito_Servico_Regime_Especifico`, cria ou atualiza o crédito em `Mov_Credito_Fiscal` (CBS e IBS, cada um com seu `ID_Imposto`) e liga as duas pontas (`ID_Credito_Fiscal_Cbs` e `ID_Credito_Fiscal_Ibs`).

**Excedente sobre o principal e a Selic** (`excedente_principal_selic`, empréstimo e título de dívida). Na baixa da parcela, lê `Mov_Emprestimo` e `Mov_Emprestimo_Parcela` e o credor (`ID_Participante_Credor`) em `Cad_Participante_Regime_Base`. `Valor_Principal_Deduzido` é o principal da parcela, na proporção do que foi pago. A Selic vem da série marcada `selic_diaria` em `Cad_Serie_Cotacao`: `Saldo_Principal_Periodo` é o saldo do principal no início do período (pagamento anterior ou contratação), `Percentual_Selic_Periodo` a Selic acumulada no período, e `Valor_Selic_Deduzido` é o produto dos dois. **Base** = `máximo(0, (valor pago − principal deduzido) − Selic deduzida)`; **crédito** = base × alíquota. Leitura minha, provisória (C239).

**Excedente sobre a curva DI** (`excedente_curva_di`, desconto, cessão, securitização, factoring e antecipação de cartão). Em cada item da antecipação, o Motor escolhe a série `di_futuro` de **vencimento mais próximo** do recebível e, no empate, a de **menor taxa** (Decreto, art. 290, parágrafo único). `Valor_Curva_Di` = `Valor_Liquido_Antecipado × ((1 + Taxa_Di_Aplicada) ^ (Prazo_Dias_Uteis ÷ 252) − 1)` e `Valor_Desagio_Excedente` = `máximo(0, Valor_Desagio − Valor_Curva_Di)`. O crédito é a **soma dos excedentes** da operação vezes a alíquota. Leitura minha (C242).

**Parcela pela alíquota** (`parcela_pela_aliquota`, arrendamento). Em cada parcela paga (`Mov_Arrendamento_Parcela`), a regra sai de `Tipo_Arrendamento` e `Tipo_Pagamento` (contraprestação, valor residual ou alienação do bem). A alíquota é a da locação, da venda ou dos serviços financeiros, conforme a regra, e o **bem** (`ID_Cclasstrib_Bem`) define a alíquota quando é a do bem. `Valor_Base_Credito` = `Valor_Pago`; o campo `Valor_Encargos_Financeiros` fica gravado e o Motor **avisa** quando o crédito passa da proporção de encargos (C241).

**Valor pago pelo fornecedor** (`valor_pago_pelo_fornecedor`, tarifas, consórcio, mercado organizado, arranjo, ativos virtuais, intermediação, seguro, vales). O ERP **não calcula**: grava o que o fornecedor informou (`Origem_Valor = informacao_fornecedor`, vindo da Plataforma, da DeRE do fornecedor ou do documento fiscal) e o crédito é o valor informado. Sem a informação, o crédito não nasce e há aviso.

**Proporção do débito do fornecedor** (`proporcao_debito_fornecedor`, plano de saúde dos empregados e capitalização). Para o plano de saúde, o cálculo está em `Mov_Rh_Beneficio_Credito_Cbs`: **crédito CBS** = `Valor_Debito_Cbs_Entidade × Proporcao_Empregados × Percentual_Custeio_Empresa`, onde `Proporcao_Empregados` = `Valor_Premio_Empregados ÷ Valor_Premios_Entidade_Total` e `Percentual_Custeio_Empresa` = `(Valor_Premio_Empregados − Valor_Descontado_Empregados) ÷ Valor_Premio_Empregados`. O Motor confere o acordo (`Mov_Rh_Beneficio_Acordo_Coletivo` com `Clausula_Compulsoria`), a **janela** (vigência do instrumento mais seis meses, parâmetro de `Cad_Criterio_Uso_Preponderante`) e o estado da declaração à RFB (**só registrado**, Q200-11). O IBS segue a mesma conta com `Valor_Debito_Ibs_Entidade`.

## 5.5 Crédito, conferência e apropriação

O crédito do B0b-2 **não tem apropriação própria**. Quem aprova, apropria e usa o crédito é `Mov_Credito_Fiscal` e, na Plataforma, a aba de créditos do espelho. O registro novo faz três coisas que o dicionário não fazia: (1) guarda a **memória de cálculo** (o que foi pago, as deduções, a base, as alíquotas, a proporção), que o auditor pede; (2) separa o **calculado** (`Valor_Credito_Cbs_Calculado`) do **apropriável** (`Valor_Credito_Cbs_Apropriavel`, depois da proporção do art. 291); e (3) liga cada crédito ao **pagamento** que o originou. A conferência contra a Plataforma usa `Mov_Cbs_Apuracao_Espelho_Conta` (`ID_Espelho_Conta`): se `Valor_Apurado_Erp` diverge do que a Plataforma apurou, o espelho já grava `Divergencia_Valor`, e o ERP avisa.

# 6. Regras de texto: o que o Motor avisa

Nenhuma regra bloqueia; todas gravam o aviso na linha e mostram a mensagem ao usuário (D-N284: "o ERP avisa, não bloqueia").

| # | Regra | Onde avisa |
|-------|----------------------------------------------------------|-----------------------------------|
| 1 | Baixa de parcela de empréstimo **sem credor** (`ID_Participante_Credor` vazio) | `Mov_Emprestimo` |
| 2 | Crédito de empréstimo ou título **com credor fora de `Cad_Participante_Regime_Base`** (o crédito só existe se o fornecedor está no regime específico) | `Mov_Credito_Servico_Regime_Especifico` |
| 3 | Operação **referenciada em moeda estrangeira** com crédito de juros calculado (art. 197, II) | `Mov_Emprestimo` |
| 4 | Título de dívida **sem confirmação do detentor** | `Mov_Credito_Servico_Regime_Especifico` |
| 5 | Título de **oferta pública** com crédito calculado | `Mov_Emprestimo` |
| 6 | Item da antecipação **sem série de DI** de vencimento próximo | `Mov_Antecipacao_Recebivel_Item` |
| 7 | Empate de vencimentos de DI resolvido pela **menor taxa** (a dedução do fornecedor usaria a maior, C242) | `Mov_Antecipacao_Recebivel_Item` |
| 8 | Crédito de arrendamento **acima da proporção de encargos** informada pelo arrendador | `Mov_Arrendamento_Parcela` |
| 9 | Valor residual do arrendamento financeiro **abaixo do custo** de aquisição (Decreto, art. 297, § 2º, II) | `Cad_Arrendamento_Mercantil` |
| 10 | Crédito de plano de saúde **sem acordo coletivo** registrado, com cláusula não compulsória ou fora da janela de seis meses | `Mov_Rh_Beneficio_Credito_Cbs` |
| 11 | Plano de saúde **sem declaração** à RFB do acordo (o art. 337, § 2º, exige) | `Mov_Rh_Beneficio_Acordo_Coletivo` |
| 12 | Crédito calculado **sem proporção** do art. 291 informada pela Plataforma (fica a apropriar) | `Mov_Credito_Servico_Regime_Especifico` |
| 13 | **Divergência** entre o crédito calculado e o apurado no espelho da Plataforma | `Mov_Credito_Servico_Regime_Especifico` |
| 14 | Regra **provisória** usada no cálculo (nenhuma regra nasce `validado`) | `Regra_Provisoria` |
| 15 | Pagamento com data **anterior a 01/01/2027** em regra que só vale a partir de 2027 (C245) | `Mov_Credito_Servico_Regime_Especifico` |
| 16 | Tomador **em regime específico** com crédito em regra que não o admite | `Mov_Credito_Servico_Regime_Especifico` |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|-----------|-----------------------------------------------------------------------|-----------------|
| Q200-1 | Aprova o **escopo** do B0b-2: as três mecânicas (cálculo próprio, valor pago pelo fornecedor e proporção do débito), as **oito entidades** e os cinco campos novos em entidades existentes, sem domínio novo (usando os do B4), para **qualquer cliente** e não só para quem está no regime específico? | Sim |
| Q200-2 | Aprova o **catálogo** `Cad_Regra_Credito_Tomador` (21 campos, com vigência) e as **28 regras provisórias** do Anexo A, das quais nove são **vedações** (`sem_credito`), que nascem com `Situacao_Dado = provisorio`? | Sim |
| Q200-3 | No **empréstimo**, aprova os três campos novos em `Mov_Emprestimo` (credor, forma de captação e marca de moeda estrangeira), a série **Selic diária** em `Cad_Serie_Cotacao` e o cálculo da seção 5.4 (Selic sobre o saldo do principal no início do período, base zero se negativa, alíquota sobre a base), com os juros de mora **fora** até o contador responder (C239)? | Sim |
| Q200-4 | No **título de dívida**, aprova os dois valores novos em `tipo_emprestimo` (`debenture` e `nota_comercial`), a regra de **oferta pública sem crédito** e o crédito **a apropriar** até a Plataforma ou o usuário confirmar o detentor (C240)? | Sim |
| Q200-5 | No **arrendamento**, aprova `Cad_Arrendamento_Mercantil` e `Mov_Arrendamento_Parcela`, o crédito pela **parcela inteira** (leitura literal da LC 214, art. 203), **com `Valor_Encargos_Financeiros` gravado** e o aviso de excesso, a regra da **alienação** com origem decreto e o valor novo `arrendamento_parcela` em `Mov_Titulo.Origem_Tipo`? | Sim |
| Q200-6 | Na **antecipação de recebíveis**, aprova `Mov_Antecipacao_Recebivel` e os itens, a baixa pelo `ID_Tipo_Baixa` que o usuário escolhe, as séries de **DI futuro** em `Cad_Serie_Cotacao`, a escolha do vencimento mais próximo e da **menor taxa no empate** no crédito do tomador, e a fórmula da curva DI da seção 5.4 como provisória (C242)? | Sim |
| Q200-7 | Aprova o **registro do crédito** `Mov_Credito_Servico_Regime_Especifico` (38 campos): a memória de cálculo, a proporção do art. 291 **só nas regras de empréstimo, título e desconto**, as duas origens novas em `Mov_Credito_Fiscal.Origem` e a conferência pelo espelho da Plataforma (C243)? | Sim |
| Q200-8 | No **plano de saúde dos empregados**, aprova `Mov_Rh_Beneficio_Acordo_Coletivo` e `Mov_Rh_Beneficio_Credito_Cbs`, o cálculo pelo art. 337 com o **desconto da folha do ERP como fonte** (e-Social e documento fiscal como alternativas), o crédito só com acordo compulsório registrado e a janela de seis meses (C244)? | Sim |
| Q200-9 | Os **vales** (transporte, refeição e alimentação) **só registram** o crédito que o fornecedor informar, sem fórmula própria, até o decreto ou o ato dizer como (C244)? | Sim |
| Q200-10 | As 28 regras nascem com vigência a partir de **01/01/2027**, como as alíquotas do B4 (Q198-5), com **aviso** para pagamento anterior, até o contador dizer se há crédito do tomador em 2026 (C245)? | Sim |
| Q200-11 | A **declaração à RFB** e o **documento fiscal da empresa** do art. 337, §§ 2º e 5º, ficam **só registrados** (situação, data, protocolo, ligação ao documento) e a emissão espera o ato conjunto que ainda não foi publicado? | Sim |

# 8. O que acontece se você aprovar

| Item | Efeito |
|---------------------------|-------------------------------------------------------------------------|
| Entidades | **1.155 → 1.163** (+8: seis em Contabilidade & Fiscal e duas em Folha & RH) |
| Campos | **13.017 → 13.169** (+152: 147 nas oito entidades novas e 5 em `Mov_Emprestimo` e `Cad_Serie_Cotacao`) |
| Chaves estrangeiras | **3.404 → 3.440** (+36, uma delas genérica: o `ID_Origem` do registro do crédito, de 61 para 62 referências genéricas) |
| Domínios | **355 → 355** (nenhum novo) |
| Valores de domínio | **+2** em `tipo_emprestimo` (`debenture` e `nota_comercial`) |
| Carga | **28** regras de crédito (nove vedações, 26 de lei e 2 de decreto) e **1** série de Selic, mais os 2 valores de domínio (Anexo B) |
| Textos e enumerações | `Mov_Credito_Fiscal.Origem` (+2), `Mov_Titulo.Origem_Tipo` (+1) e `Cad_Criterio_Uso_Preponderante.Credito_Igual_Debito_Fornecedor` (texto) |
| Ondas, DDL e ER | As oito entidades entram nas ondas de Contabilidade & Fiscal (seis) e Folha & RH (duas); `Cad_Regra_Credito_Tomador` gera também a tabela `_Versao`; regerados na consolidação |
| Documentos | 14 (D-N533), 38 (seção 1.30) e 188 (C239 a C245, total 245) |

# 9. Limites

- **Li a LC 214 nos artigos de crédito do tomador (188 a 243, nos trechos citados) e o decreto nos arts. 62 a 64, 284 a 300, 305 a 328, 337, 345 e 346.** Não li os anexos do decreto nem o regime de crédito presumido, que não trata dos serviços financeiros.
- **O ato conjunto da RFB e do CGIBS** que regulamenta a declaração do acordo coletivo, o documento fiscal da empresa e a informação do crédito pelo fornecedor **não foi publicado**; as entidades guardam o que a lei manda saber, e não o formato do arquivo.
- **Cinco leituras são minhas**: a Selic sobre o saldo do principal (C239), a fórmula da curva DI (C242), a base do arrendamento financeiro (C241), o detentor do título (C240) e o crédito em 2026 (C245). **Todas as 28 regras nascem provisórias**; o contador valida linha a linha.
- **A letra do art. 57, § 3º, IV, da LC 214**, a que o decreto remete nos vales, **não foi conferida** (regra `cred_vale_beneficio`).
- **A alíquota usada no crédito é a do B4** (`Cad_Regime_Aliquota_Soma`, desde 01/01/2027). Se o fornecedor do tomador é um participante cujo regime o ERP não conhece, o crédito não é calculado: vale o que o fornecedor informar.
- **O ERP não calcula o débito do fornecedor.** O plano de saúde e os créditos de valor pago dependem do que a operadora e os demais fornecedores informarem, e o B0b-2 só guarda e confere.
- **A baixa da antecipação** usa o `ID_Tipo_Baixa` que o usuário escolhe; o ERP não decide sozinho se o deságio é perda ou despesa financeira (isso é da contabilidade, Q113-3).
- **Fora deste desenho:** o crédito de **importação** do serviço financeiro, o **fator de redução** (depende de ato conjunto) e os regimes do documento 94 que não são de serviço financeiro.
- **As contagens** vêm de um programa sobre o modelo da revisão 37 (1.155 entidades, 13.017 campos, 3.404 chaves, 355 domínios), conferido contra os nomes e os destinos de cada chave; o texto dos artigos eu conferi à mão nos trechos citados.
- **Nada passou por validação do contador.** As sete perguntas C239 a C245 estão no documento 188.

# Anexo A. As 28 regras propostas

O arquivo `Cad_Regra_Credito_Tomador.csv` traz as colunas da carga (condição em texto, as marcas em verdadeiro e falso, origem, fundamento, situação provisória e vigência de 01/01/2027 a 31/12/9999). A tabela abaixo traz o essencial. **Origem:** `lei` quando a LC 214 e o decreto dizem o mesmo; `decreto` quando só o decreto traz. As marcas são leitura minha (seção 9).

| Base | Código | Descrição | Forma de cálculo | Marcas | Origem | Fundamento |
|-----------|-----------|----------------------|----------|---------------------|---|----------------------|
| credito_cambio_tvm | `cred_operacao_credito` | Tomador de operação de crédito: crédito sobre a despesa financeira efetivamente paga, depois de tirar o principal e a Selic sobre o principal | excedente_principal_selic | caixa, proporção art. 291, veda cooperativa, veda moeda estrangeira | lei | LC 214, arts. 194, 197 e 199; Decreto 12.955, arts. 284, 288 e 291 |
| credito_cambio_tvm | `cred_titulo_divida` | Emissor de título de dívida (debênture, nota comercial) sem oferta pública: crédito como na operação de crédito, só no período em que o título é detido por contribuinte do regime específico | excedente_principal_selic | caixa, proporção art. 291, veda cooperativa, veda moeda estrangeira | lei | LC 214, art. 195, caput; Decreto, art. 289, caput |
| credito_cambio_tvm | `cred_titulo_oferta_publica` | Emissor de título de dívida com oferta pública regulada pela CVM: sem crédito | sem_credito |  | lei | LC 214, art. 195, § 1º, II; Decreto, art. 289, § 1º, II |
| credito_cambio_tvm | `cred_desconto_cessao` | Tomador de desconto, cessão de recebíveis ou antecipação de crédito: crédito sobre a parte do deságio que passa da curva DI pelo prazo da antecipação | excedente_curva_di | caixa, proporção art. 291, veda cooperativa, veda moeda estrangeira | lei | LC 214, arts. 196, 197 e 199; Decreto, arts. 284, 290 e 291 |
| securitizacao_faturizacao | `cred_securitizacao_faturiz` | Tomador de securitização ou de faturização (factoring): crédito sobre a parte do deságio que passa da curva DI | excedente_curva_di | caixa, proporção art. 291, veda cooperativa, veda moeda estrangeira | lei | LC 214, arts. 196, 197 e 199; Decreto, arts. 284, 290 e 291 |
| credito_cambio_tvm | `cred_tarifa_comissao` | Tarifas e comissões das operações de crédito, câmbio, títulos, securitização e faturização: crédito pelo tributo que o fornecedor pagou | valor_pago_pelo_fornecedor | admite regime específico | lei | LC 214, art. 198 e parágrafo único; Decreto, art. 292 e §§ 1º e 2º |
| credito_cambio_tvm | `cred_demais_financeiros_veda` | Demais serviços financeiros dos incisos I a V do art. 182 que a lei não permite expressamente: sem crédito | sem_credito |  | lei | LC 214, art. 199; Decreto, art. 293 |
| credito_cambio_tvm | `cred_importacao_servico` | Serviço financeiro importado: alíquota zero na importação quando o importador teria crédito no País, e sem crédito | sem_credito |  | lei | LC 214, art. 231; Decreto, art. 328, § 1º, II |
| arrend_oper_locacao | `cred_arrend_oper_parcela` | Arrendatário de arrendamento operacional: crédito sobre a parcela da contraprestação paga, pela alíquota da locação do bem | parcela_pela_aliquota | caixa | lei | LC 214, art. 203; Decreto, art. 296 |
| arrend_oper_alienacao | `cred_arrend_oper_alienacao` | Arrendatário de arrendamento operacional: crédito sobre o valor de alienação do bem, pela alíquota da venda | parcela_pela_aliquota | caixa | decreto | Decreto, art. 296 (só o Decreto traz); LC 214, art. 203 |
| arrend_fin_parcelas | `cred_arrend_fin_parcela` | Arrendatário de arrendamento financeiro: crédito sobre a parcela da contraprestação paga, pela alíquota dos serviços financeiros | parcela_pela_aliquota | caixa | lei | LC 214, art. 203; Decreto, art. 298 |
| arrend_fin_residual | `cred_arrend_fin_residual` | Arrendatário de arrendamento financeiro: crédito sobre o valor residual pago, pela alíquota da venda do bem | parcela_pela_aliquota | caixa | lei | LC 214, art. 203; Decreto, art. 298 |
| consorcio | `cred_consorcio_administracao` | Consorciado que compra a administração do consórcio: crédito pelo tributo que a administradora pagou | valor_pago_pelo_fornecedor |  | lei | LC 214, art. 205; Decreto, art. 300 |
| intermediacao_financeira | `cred_intermediacao` | Segurado, titular de capitalização ou consorciado que compra a intermediação: crédito se o fornecedor identificar o adquirente | valor_pago_pelo_fornecedor |  | lei | LC 214, arts. 206 e 228; Decreto, arts. 301, § 2º, e 325, §§ 2º a 4º |
| arranjo_pagamento | `cred_arranjo_credenciado` | Credenciado ou outro destinatário de arranjo de pagamento: crédito sobre a remuneração bruta devida à credenciadora ou a outro participante | valor_pago_pelo_fornecedor |  | lei | LC 214, art. 218; Decreto, arts. 311 a 313 |
| antecipacao_recebivel_arranjo | `cred_antecipacao_arranjo` | Tomador da liquidação antecipada de recebíveis de arranjos (cartão): crédito sobre a parte do desconto que passa da curva DI | excedente_curva_di | caixa | lei | LC 214, art. 219, § 5º; Decreto, art. 314, § 6º |
| programa_fidelizacao | `cred_fidelizacao_veda` | Adquirente de pontos de programa de fidelização: sem crédito | sem_credito |  | lei | LC 214, art. 219-A, II; Decreto, art. 315, II |
| mercado_organizado | `cred_mercado_organizado` | Adquirente de serviços de mercado organizado, infraestrutura de mercado e depositária central: crédito pelo valor pago pelo fornecedor | valor_pago_pelo_fornecedor |  | lei | LC 214, art. 221; Decreto, art. 317 |
| seguro | `cred_seguro_segurado` | Segurado do regime regular: crédito pelo tributo pago sobre o prêmio, depois das deduções identificáveis ao contrato | valor_pago_pelo_fornecedor |  | lei | LC 214, art. 223, §§ 1º e 2º; Decreto, art. 319, §§ 1º e 2º |
| previdencia_complementar | `cred_previdencia_veda` | Adquirente de previdência complementar: sem crédito | sem_credito |  | lei | LC 214, art. 226; Decreto, art. 321 |
| capitalizacao | `cred_capitalizacao` | Adquirente de título de capitalização do regime regular: crédito pela proporção do prêmio pago sobre os débitos extintos pela entidade | proporcao_debito_fornecedor |  | lei | LC 214, art. 225, § 5º; Decreto, art. 323, § 7º |
| gestao_recursos | `cred_gestao_investidor_veda` | Adquirente de gestão e administração de recursos prestada ao investidor (carteira administrada): sem crédito | sem_credito |  | lei | LC 214, art. 211; Decreto, art. 307 |
| ativo_virtual | `cred_ativo_virtual` | Adquirente de serviços de ativos virtuais do regime regular: crédito pelo valor pago pelo fornecedor | valor_pago_pelo_fornecedor |  | lei | LC 214, art. 230; Decreto, art. 327 |
| plano_saude | `cred_plano_saude_empregado` | Empresa que paga plano de saúde aos empregados e dependentes por cláusula compulsória de acordo ou convenção coletiva: crédito igual ao débito da operadora vezes a proporção dos empregados, sobre a parte que a empresa suporta | proporcao_debito_fornecedor | exige acordo, exige declaração | lei | LC 214, art. 238, parágrafo único (com o art. 57, § 3º, IV, f); Decreto, arts. 63, § 1º, VI, e 337 |
| plano_saude | `cred_plano_saude_veda` | Demais adquirentes de plano de assistência à saúde: sem crédito | sem_credito |  | lei | LC 214, art. 238, caput; Decreto, art. 337, caput |
| plano_funerario | `cred_plano_funerario_veda` | Adquirente de plano de assistência funerária: sem crédito (o art. 236 manda aplicar a saúde) | sem_credito |  | lei | LC 214, arts. 236 e 238; Decreto, art. 345 |
| plano_pet | `cred_plano_pet_veda` | Adquirente de plano de saúde de animais domésticos: sem crédito | sem_credito |  | lei | LC 214, art. 243; Decreto, art. 346 |
| arranjo_pagamento | `cred_vale_beneficio` | Empresa que fornece vale-transporte, vale-refeição ou vale-alimentação aos empregados: crédito igual ao débito do fornecedor apurado e extinto no regime financeiro | valor_pago_pelo_fornecedor |  | decreto | Decreto, art. 63, § 1º, VII (a letra do art. 57, § 3º, IV, da LC não conferida) |

# Anexo B. As cargas

## B.1 `Cad_Regra_Credito_Tomador` (28 linhas)

As 28 linhas do Anexo A, todas com `Situacao_Dado = provisorio` e vigência de 01/01/2027 a 31/12/9999. Por forma de cálculo: excedente_principal_selic (2), sem_credito (9), excedente_curva_di (3), valor_pago_pelo_fornecedor (8), parcela_pela_aliquota (4), proporcao_debito_fornecedor (2).

## B.2 Valores novos de `tipo_emprestimo` (2)

| Código | Descrição | Fundamento |
|-------------------|----------------------------------------|----------------------------------------|
| `debenture` | Debênture emitida pela empresa | LC 214, art. 195; Decreto, art. 289 |
| `nota_comercial` | Nota comercial emitida pela empresa | LC 214, art. 195; Decreto, art. 289 |

## B.3 Série nova em `Cad_Serie_Cotacao` (1)

| Nome | Tipo | Fonte | Uso legal | Observação |
|--------------------------|-------------|-----------|----------|-----------------------------------------|
| Selic diária (compromissadas de um dia) | indice_financeiro | banco_central | selic_diaria | LC 214, art. 194, II; Decreto, art. 288, II: taxa média das compromissadas com títulos públicos federais de um dia útil. Criar só se a série ainda não existir. |

As séries de **DI futuro** (`Uso_Legal_Cbs = di_futuro`, com `Data_Vencimento_Contrato`) não vêm na carga: entram pelo cadastro da empresa ou pela fonte de cotação que ela usar.

# Anexo C. Perguntas ao contador (C239 a C245)

Estão também no documento 188, que passa a ter 245 perguntas.

**C239 · LC 214, art. 194, e Decreto 12.955, art. 288 · Crédito do tomador de operação de crédito: principal, Selic e a conta da alíquota**

*Documento 200, seção 4.4 (Q200-3)*

A lei dá ao tomador crédito sobre as despesas financeiras pagas, depois de tirar (I) o principal e (II) o montante da Selic aplicada sobre o principal. O texto não diz sobre qual principal a Selic incide (o saldo devedor do período ou só o principal contido na parcela), de que data a Selic corre, nem se a alíquota se aplica à base como está escrito (o crédito é a base vezes a alíquota) ou "por dentro". O dicionário não tinha como guardar essas escolhas.

Pergunta: (a) a Selic incide sobre o saldo do principal no início do período entre o pagamento anterior (ou a contratação) e este pagamento, acumulada pelos dias úteis do período? (b) o principal da parcela é o que o contrato de amortização (Price, SAC, bullet) separa, e nos contratos sem tabela, o que o banco informar? (c) se a parcela paga menos o principal menos a Selic der negativo, a base é zero, sem aproveitar a diferença nas parcelas seguintes? (d) o crédito é a base vezes a alíquota da CBS e do IBS que o fornecedor paga, sem cálculo por dentro? (e) quando a parcela é paga com atraso, os juros de mora entram na despesa financeira?

Proposta do documento 200 (Q200-3): o ERP calcula como em (a) a (d), grava o saldo, o percentual da Selic e cada dedução na linha, marca a regra como provisória e só avisa; os juros de mora ficam de fora até a sua resposta; nada aplicado ao dicionário.

**C240 · LC 214, art. 195, e Decreto 12.955, art. 289 · Título de dívida: quem o detém e a oferta pública**

*Documento 200, seção 4.7 (Q200-4)*

O emissor de debênture ou de nota comercial só toma o crédito no período em que o título é detido por contribuinte do regime específico, e não toma se o título é de oferta pública regulada pela CVM. O título circula, e o emissor não vê o detentor. O decreto não diz como o emissor prova a condição do detentor, nem se a mudança de detentor no meio do mês divide o crédito do mês.

Pergunta: (a) o emissor depende da informação que a Plataforma der sobre o detentor de cada pagamento, ou pode usar a declaração do agente fiduciário ou do escriturador? (b) se não houver informação, o crédito fica retido, ou o emissor pode tomar por estimativa? (c) se o título muda de mãos entre o fim do período de juros e o pagamento, vale o detentor na data do pagamento? (d) a oferta pública com esforços restritos (CVM 160) conta como oferta pública para o § 1º?

Proposta do documento 200 (Q200-4): o crédito fica a apropriar até a Plataforma ou o usuário confirmar o detentor, vale o detentor na data do pagamento e a oferta de esforços restritos é tratada como oferta pública, só com aviso; nada aplicado ao dicionário.

**C241 · LC 214, art. 203, e Decreto 12.955, arts. 296 a 298 · Arrendamento mercantil: parcela inteira ou encargos, valor residual e alienação**

*Documento 200, seção 4.6 (Q200-5)*

A lei dá ao arrendatário crédito sobre o valor das parcelas e do valor residual, na medida do pagamento, pela alíquota da receita correspondente. O decreto, no arrendamento operacional, acrescenta o valor de alienação do bem (art. 296), e, no financeiro, separa as parcelas (alíquota dos serviços financeiros) do valor residual (alíquota da venda) (art. 298). Mas o fornecedor do arrendamento financeiro tributa só os encargos financeiros da parcela (art. 297, § 1º). Se o crédito do arrendatário incidir na parcela inteira, ele passa do tributo que o fornecedor pagou.

Pergunta: (a) no arrendamento financeiro, o crédito incide sobre a parcela inteira (leitura literal) ou só sobre os encargos financeiros embutidos? (b) o crédito do valor residual usa a alíquota da venda do bem mesmo quando o arrendatário exerce a opção de compra antes do fim do contrato? (c) a alienação do bem no arrendamento operacional, que só o decreto traz, vale para o arrendatário que compra o bem no fim do contrato? (d) para o arrendatário em regime específico ou optante do Simples, o crédito é sempre vedado?

Proposta do documento 200 (Q200-5): o crédito segue a leitura literal (parcela inteira), `Mov_Arrendamento_Parcela` guarda também os encargos informados pelo arrendador e o ERP avisa quando o crédito passa da proporção de encargos; a regra de alienação nasce com origem decreto; nada aplicado ao dicionário.

**C242 · LC 214, arts. 196 e 219, § 5º, e Decreto 12.955, arts. 290 e 314 · Curva DI: fórmula, prazo e empate de vencimentos**

*Documento 200, seção 4.5 (Q200-6)*

O crédito do tomador da cessão, do desconto, da antecipação de recebíveis e da factoring incide sobre o deságio que passa da curva de juros futuros da taxa DI pelo prazo da antecipação. O decreto manda usar o contrato de DI futuro de vencimento mais próximo e, no empate, a menor taxa (art. 290, parágrafo único); para a antecipação de arranjos, a dedução do fornecedor usa a maior (art. 314, § 2º). Nem a lei nem o decreto escrevem a fórmula da curva, a contagem dos dias, nem de qual dia vem a taxa.

Pergunta: (a) o valor da curva DI é o valor líquido antecipado capitalizado pela taxa DI do contrato escolhido, em dias úteis sobre 252 (Valor_Liquido × ((1 + taxa)^(dias úteis ÷ 252) − 1))? (b) a taxa é a de fechamento do dia da operação? (c) no empate, o crédito do tomador usa a menor taxa e o débito do fornecedor a maior, mesmo no mesmo recebível, ou deve haver uma só taxa? (d) quando o prazo é maior que o último vencimento do DI negociado, vale o último contrato? (e) o deságio que passa da curva pode ser negativo (deságio menor que a curva), caso em que o crédito é zero?

Proposta do documento 200 (Q200-6): o ERP aplica (a), (b) e (e), usa a menor taxa no crédito do tomador e a maior na dedução do fornecedor, como cada artigo escreve, e grava a taxa, a série e o prazo em cada recebível; nada aplicado ao dicionário.

**C243 · Decreto 12.955, art. 291 · Proporção do débito que o fornecedor extinguiu: onde vale**

*Documento 200, seção 4.3 (Q200-7)*

O art. 291 diz que o crédito dos arts. 288 a 290 do decreto (empréstimo, título de dívida, desconto e cessão) é integral se o fornecedor extinguiu todo o débito ou se a base dele foi zero ou negativa, proporcional se extinguiu em parte, e nenhum se não pagou. O texto não cita os créditos do arrendamento (arts. 296 e 298) nem o da antecipação de recebíveis de arranjos (art. 314, § 6º).

Pergunta: (a) a proporção do art. 291 vale só para os arts. 288 a 290, como está escrito? (b) o crédito do arrendamento e o da antecipação de cartão não dependem do que o fornecedor extinguiu? (c) quando o fornecedor extingue o débito depois, o tomador apropria a diferença no mês em que a Plataforma informar, sem refazer os meses anteriores? (d) a proporção é por pagamento, por fornecedor ou por mês?

Proposta do documento 200 (Q200-7): a proporção vale só para as regras de empréstimo, título e desconto (Aplica_Proporcao_Extincao), é por pagamento, e a diferença entra no mês da informação; nada aplicado ao dicionário.

**C244 · Decreto 12.955, arts. 63 e 337 · Plano de saúde dos empregados e vales: acordo coletivo, proporção e fórmula**

*Documento 200, seções 4.9 e 4.10 (Q200-8 e Q200-9)*

O plano de saúde dos empregados dá crédito igual ao débito de CBS da operadora vezes a proporção dos empregados, sobre a parte que a empresa suporta, e só enquanto o acordo ou a convenção coletiva vigora e até seis meses depois (art. 63, §§ 1º, VI, e 5º; art. 337). O art. 337 trata da declaração à RFB, dos descontos do e-Social e do documento fiscal da empresa, e remete a ato conjunto não publicado. Para os vales (art. 63, § 1º, VII), o decreto diz apenas que o crédito é equivalente ao débito do fornecedor.

Pergunta: (a) o plano que cobre também sócios e administradores, ou dependentes além do que o acordo prevê, fica fora do crédito pelo prêmio proporcional? (b) quando o acordo coletivo dá o plano mas deixa a escolha da operadora com o empregado (reembolso), há crédito? (c) o prazo de seis meses conta do fim da vigência do instrumento ou da última renovação? (d) a proporção dos empregados é a do mês do crédito ou a do mês de competência do prêmio? (e) para os vales, como o crédito se reparte entre as empresas que compram do mesmo emissor, e há crédito sobre a taxa de administração além do valor carregado?

Proposta do documento 200 (Q200-8 e Q200-9): o plano de saúde é calculado como o art. 337 escreve, só com acordo registrado; sócios e administradores ficam fora; os vales só registram o que o fornecedor informar; nada aplicado ao dicionário.

**C245 · Decreto 12.955, arts. 197, 284 e 480, e LC 214, arts. 271 e 233 · Crédito do tomador em 2026, cooperativa de crédito e moeda estrangeira**

*Documento 200, seções 4.8 e 4.11 (Q200-10)*

Em 2026 a CBS dos serviços financeiros é de 0,9% (art. 480, I), mas a descrição do crédito do tomador não traz data, e a soma de alíquotas do art. 233 começa em 2027. A lei veda o crédito do associado de cooperativa de crédito que exerceu a opção do art. 271 e do tomador de operação referenciada em moeda estrangeira, mas mantém o crédito das tarifas e comissões (art. 198).

Pergunta: (a) o tomador tem crédito de CBS pelos serviços financeiros em 2026, e em qual regra de cálculo? (b) se não tem, o crédito começa em 01/01/2027 mesmo para parcelas de contratos antigos pagas em 2027? (c) o que é "referenciada em moeda estrangeira": a operação em moeda estrangeira, a indexada ao câmbio, ou as duas? (d) o associado de cooperativa que não exerceu a opção do art. 271 tem crédito normal?

Proposta do documento 200 (Q200-10): as regras nascem com vigência a partir de 01/01/2027, a vedação de moeda estrangeira vale para as duas hipóteses de (c), e o ERP avisa; nada aplicado ao dicionário.

