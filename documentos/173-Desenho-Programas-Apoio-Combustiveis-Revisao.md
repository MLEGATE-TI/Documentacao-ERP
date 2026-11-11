# Revisão dos programas de apoio aos combustíveis com os textos oficiais: valores, períodos, repasse do distribuidor, MP 1.358, etanol e imposto de exportação — Documento 173

*Revisa o documento 171 a partir dos textos que você mandou (MPs 1.340, 1.349, 1.358, 1.363 e 1.391; Decretos 12.878, 12.930 e 12.995; Portaria MF 2.946) e das suas respostas de 04/11/2026: "Q171-1 a Q171-8 - Todas sim" e as quatro respostas do Q173 (Q173-1: uma linha por programa aplicado; Q173-2: só o que vem de texto oficial, provisório; Q173-3: entidade nova de período; Q173-4: escopo com repasse do distribuidor, MP 1.358 como tipo próprio, etanol e imposto de exportação). **Este documento 173 substitui as listas de campos do 171**; o 171 continua valendo no que não é alterado aqui. **Nada entra no dicionário agora.***

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

Li os textos que você enviou e eles mudam o desenho do 171 em pontos que importam. O 171 nasceu de notícias; agora cada valor, prazo e período tem artigo. O resultado é um desenho menor em conceitos e maior em campos: **5 entidades novas (59 campos)**, **5 entidades do 171 alteradas (de 75 para 95 campos)**, 2 valores novos no domínio de agentes, 2 linhas novas em `Cad_Imposto` e **cargas provisórias que saem só de texto oficial** (seção 12).

**Oito achados que você precisa ler.**

1. **A MP 1.358 não é "cashback".** Ela autoriza uma subvenção **equivalente aos valores de PIS/Pasep, Cofins e Cide-Combustíveis** deduzidos do preço da gasolina e do PIS/Pasep e Cofins deduzidos do preço do diesel de uso rodoviário, com valor e período fixados por ato do Ministro (que não recebi). O 171 errou ao chamá-la de devolução de tributo e a tirei do domínio. Ela vira tipo próprio (`subvencao_equivalente_a_tributo`), como você pediu.
2. **Há três mecânicas de apuração, não uma.** (a) **Valor fixo por litro** sobre a quantidade vendida: MP 1.363, MP 1.391 e o etanol. (b) **Preço de referência (PR) e preço de comercialização (PC) com conta gráfica por base regional**: MP 1.340, MP 1.349 e o GLP; aqui o valor por unidade é um **teto diário de crédito** (R$ 0,32; R$ 1,20), e quem calcula a subvenção é a ANP, não uma multiplicação no item. (c) **Equivalência a tributos**: MP 1.358. O 171 só conhecia a primeira.
3. **O R$ 0,80 não é "diesel nacional".** É um **acréscimo para os produtores**, de 07/04 a 31/05/2026 (MP 1.340, art. 1º-A, e Decreto 12.930, art. 15). O R$ 1,20 é do **importador**, para diesel destinado a estados que aderiram (R$ 0,60 da União e R$ 0,60 do estado), e é pago **em acréscimo** aos R$ 0,32 (MP 1.349, art. 16, parágrafo único). A distinção é por **quem recebe**, não pela origem do produto; por isso troquei `Origem_Produto` por `Papel_Beneficiario`.
4. **O R$ 2,12 não é "1,12 mais 1,00" no texto.** A Portaria MF 2.946 diz que o valor unitário é **R$ 2,12 por litro de diesel A** na MP 1.391, por 30 dias a partir de 27/09/2026 (até 26/10/2026), prorrogável por igual período. A prorrogação de 26/10 que as notícias citam não está em texto que recebi, e a **Portaria MF 2.813** (que a 2.946 altera) também não.
5. **Os prazos não são todos os mesmos.** Aviso prévio para mudar o valor: 15 dias (MP 1.363), 10 dias (MP 1.391; sem aviso no primeiro período, § 7º) e 5 dias com carência de 15 (etanol). Pagamento: 30 dias do requerimento (MP 1.358, 1.363 e etanol) ou **último dia útil do mês seguinte ao período** (MP 1.340 e 1.349, pelo Decreto 12.930). Adesão com efeito desde o primeiro dia do período se entregue até o 5º dia útil (MP 1.340 e 1.363) ou o 10º (MP 1.391).
6. **O destaque na NF-e já tem texto para o diesel da MP 1.363.** O Decreto 12.995, art. 5º, II, exige no campo **Informações complementares** a frase "Essa operação teve um desconto correspondente ao valor da subvenção de R$ [0,00]/litro de óleo diesel de uso rodoviário, nos termos do disposto na Medida Provisória nº 1.363, de 30 de maio de 2026, e no Decreto nº 12.995, de 8 de junho de 2026". Isso responde a Q171-E1 só para esse programa; nos outros o texto manda "indicar o valor do desconto" sem dizer o campo.
7. **O distribuidor tem obrigação própria** (Decreto 12.930, art. 11, redação do Decreto 12.974): receber o desconto destacado na NF-e do produtor ou importador, **consolidar o desconto médio por litro** e repassá-lo ao próximo elo na NF-e até acabar o volume subvencionado, com declaração e termo de acesso à ANP. Desenhei duas entidades para isso (seção 8).
8. **Há imposto de exportação novo:** 12% sobre óleos brutos de petróleo (NCM 2709) e 50% sobre o diesel de uso rodoviário (NCM 2710.19.21) enquanto durar a subvenção da MP 1.340 (art. 10 e art. 12). O dicionário não tinha tabela para isso (seção 11).

# 2. Regras que segui

Valem as dos documentos 156, 157, 150, 170 e 171 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória; "O ERP só registra"; avisa e nunca bloqueia; D-N68: entidade de quem recebe a subvenção só quando há cliente). Mais estas:

1. **Só entra na carga o que está em texto oficial que li.** Onde a fonte é notícia, a linha não entra. Onde o texto remete a um ato que não recebi, o campo fica vazio e a pendência é escrita.
2. **O valor fica na unidade do ato.** O GLP é R$ 850,00 **por tonelada** no texto; guardo 850,0000 com a unidade `tonelada`, e a conversão para o quilograma do catálogo é conta no momento do item (valor derivado não se guarda). Isso responde à Q171-C7.
3. **O período do ato é cadastro.** O Decreto 12.878 define 20 períodos e o 12.995, 14; nenhuma data vai no código.
4. **Uma leitura minha é sempre dita como minha** (marcada "leitura minha") e vai ao contador ou à equipe.
5. **Li os decretos pelos textos consolidados do Planalto**, que trazem as redações dadas pelos Decretos 12.883, 12.942, 12.974 e 12.992; esses quatro não vieram em arquivo próprio.

# 3. O que li (e o que continua faltando)

| Ato | O que o texto diz | Para o dicionário |
|---|---|---|
| MP 1.340 (12/03/2026) e Decreto 12.878 (13/03/2026) | Subvenção de R$ 0,32/l ao diesel de uso rodoviário de 12/03 a 31/12/2026, para produtores, importadores e distribuidores que importam; limite total de R$ 10 bilhões (art. 2º); apuração por **PR e PC** regionais com **conta gráfica**; crédito diário limitado a R$ 0,32/l; períodos de apuração (art. 2º do Decreto); PIS/Cofins sobre a receita da subvenção compensados pela conta gráfica (art. 3º, § 3º, II, e art. 8º); declaração até 5 dias úteis depois do período; pagamento até o último dia útil do mês seguinte (redação do Decreto 12.930). Acréscimo de R$ 0,80/l **só para produtores**, 07/04 a 31/05/2026 (art. 1º-A). Imposto de exportação: 12% (NCM 2709) e 50% (NCM 2710.19.21) | Programa, valor, período, imposto de exportação |
| MP 1.349 (07/04/2026) e Decreto 12.930 (15/04/2026) | Regime Emergencial de Abastecimento Interno. Subvenção de R$ 1,20/l ao **importador** de diesel destinado a estados que aderiram (R$ 0,60 União, R$ 0,60 estado, retido do FPE), de 07/04 a 31/05/2026, prorrogável por dois meses; limite de R$ 4 bilhões (R$ 2 bilhões dos estados); paga em acréscimo aos R$ 0,32; **PC = PR − R$ 1,20 − R$ 0,32**; dupla habilitação permitida. **GLP importado: até R$ 850,00 por tonelada**, entregas de 01/04 a 31/07/2026 (redações dos Decretos 12.942 e 12.992), limite de R$ 660 milhões, sete períodos | Programas, valor, período |
| MP 1.358 (13/05/2026) | Subvenção equivalente a PIS/Pasep, Cofins e Cide-Combustíveis da gasolina e a PIS/Pasep e Cofins do diesel de uso rodoviário; valor fixado por ato do Ministro; vigência de dois meses do ato, prorrogável; pagamento não pode superar o ônus dos tributos; ANP paga em até 30 dias; o Planalto marca "Vigência encerrada" | Tipo próprio e entidade de equivalência |
| MP 1.363 (30/05/2026) e Decreto 12.995 (08/06/2026) | R$ 1,12/l de diesel de uso rodoviário, de 01/06 a 31/12/2026; 14 períodos quinzenais; adesão por termo (Anexo I), com efeito desde o 1º dia do período se entregue até o 5º dia útil; Ministro muda o valor ou interrompe ao fim de cada período de dois meses, **com 15 dias de aviso**; desconto exato no preço e frase na NF-e; ANP paga em 30 dias do requerimento, com Selic sobre o atraso; quem estava nas MPs 1.340 ou 1.349 precisa pedir interrupção (Anexo III); certidão de regularidade enquanto não houver ato conjunto RFB–ANP | Programa, valor, período, destaque |
| MP 1.391 (11/09/2026) e Portaria MF 2.946 (25/09/2026) | Subvenção a produtores e importadores de diesel e correntes para uso rodoviário; vigência de até 30 dias do ato do Ministro, prorrogável por igual período; períodos mensais; aviso de 10 dias (dispensado no primeiro período); adesão com efeito desde o 1º dia se entregue até o 10º dia útil. **Valor: R$ 2,12 por litro de diesel A**, 30 dias a partir de 27/09/2026 | Programa, valor |
| Decreto 13.119 (16/09/2026), etanol | Subvenção de **R$ 0,2519/l de etanol hidratado** a produtores e cooperativas de produtores de biocombustíveis para consumo final, por 30 dias da publicação; Ministro pode mudar o valor depois de 15 dias da publicação, com 5 dias de aviso; adesão, períodos e apuração por ato da ANP (não recebido); ANP paga em até 30 dias; base na LC 235/2026 (art. 2º, §§ 5º e 6º) e no Decreto 13.116 (não recebido). **Li o texto pela página do Senado**, que avisa não substituir o DOU | Programa, valor |

**O que continua faltando:** Portaria MF 2.813 e a de prorrogação de 26/10; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha do etanol e da MP 1.391); a LC 235 e o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio; o QAV; e o que valer para 2027. **O Planalto marca "Vigência encerrada" nas MPs 1.340, 1.349, 1.358 e 1.363**; não sei se por conversão em lei, rejeição ou perda de eficácia, e isso vai ao contador (Q173-C5). **Nenhum valor das notícias entra na carga** (R$ 0,35 do diesel A e o resto da lista do 171).

# 4. O que muda em relação ao documento 171

| Ponto do 171 | O que o texto diz | Mudança |
|---|---|---|
| `Tipo_Apoio` = {subvencao_por_unidade, devolucao_de_tributo, reducao_temporaria_de_tributo} | MP 1.358 é equivalência a tributos; a mecânica PR/PC é distinta do valor fixo | Domínio novo: {subvencao_valor_fixo_por_unidade, subvencao_por_preco_de_referencia, subvencao_equivalente_a_tributo, reducao_temporaria_de_tributo}; `devolucao_de_tributo` sai |
| `Origem_Produto` {nacional, importado, qualquer} | O valor depende de **quem** recebe (produtor, importador) | Sai; entra `Papel_Beneficiario` |
| `Valor_Por_Unidade` sempre por litro ou quilograma | GLP é por tonelada; nos programas de PR/PC o valor é teto diário de crédito | `Unidade_Do_Valor` e `Valor_E_Maximo` |
| Aviso prévio 15 dias e pagamento 30 dias para todos | 15 / 10 / 5 dias; 30 dias corridos ou último dia útil do mês seguinte | Campos de prazo por programa |
| `Competencia_Inicio` e `Competencia_Fim` no requerimento | Cada declaração é de um período de apuração definido em decreto | Liga ao período |
| Sem teto do programa | R$ 10 bi (MP 1.340), R$ 4 bi (MP 1.349), R$ 660 mi (GLP) | `Limite_Total_Valor` |
| Q171-E1 (campo da NF-e) | Informações complementares, com frase, na MP 1.363 | Campo e texto no programa |
| Q171-C7 (GLP em tonelada ou quilograma) | R$ 850,00 por tonelada, "até" | Guardo a unidade do ato |
| Sem repasse do distribuidor | Decreto 12.930, art. 11 | Duas entidades novas (seção 8) |
| Sem Cide e sem imposto de exportação | MP 1.358 e MP 1.340 | Linhas em `Cad_Imposto` e entidade de exportação |

# 5. O programa e o valor por período: o que muda

Os dois cadastros do 171 continuam: `Cad_Combustivel_Programa_Apoio` é o cabeçalho e `Cad_Combustivel_Programa_Valor` guarda um valor por combustível e por beneficiário, **por período de vigência**. Os 19 e os 16 campos do 171 ficam, com as exceções abaixo.

## 5.1 `Cad_Combustivel_Programa_Apoio`: 19 campos viram 29

**Campo alterado.** `Tipo_Apoio`: enumeração {`subvencao_valor_fixo_por_unidade`, `subvencao_por_preco_de_referencia`, `subvencao_equivalente_a_tributo`, `reducao_temporaria_de_tributo`}. O primeiro é a multiplicação simples (MP 1.363, MP 1.391, etanol): o ERP calcula quantidade vezes valor. O segundo é a mecânica de PR, PC e conta gráfica (MP 1.340, MP 1.349 e GLP): **o ERP não calcula a subvenção do item**; registra o que a ANP apura (seção 7). O terceiro é a MP 1.358 (seção 9). O quarto não gera pagamento e continua vivendo em `Cad_Aliquota_Combustivel` (documento 171, seção 6).

**Descrições alteradas.** `Aviso_Previo_Alteracao_Dias` passa a valer 15 (MP 1.363), 10 (MP 1.391) ou 5 (etanol, comunicação aos habilitados) e fica vazio nos programas cujo texto não fixa aviso. `Prazo_Pagamento_Dias` só vale em dias corridos ou úteis (30 dias corridos nas MPs 1.358 e 1.363 e no etanol); o campo novo `Unidade_Prazo_Pagamento` diz como ler.

**10 campos novos.**

| Campo | Tipo | Descrição |
|---|---|---|
| `Limite_Total_Valor` | número, opcional | O teto de pagamentos acumulados do programa: R$ 10.000.000.000,00 na MP 1.340 (art. 2º), R$ 4.000.000.000,00 na MP 1.349 (art. 5º) e R$ 660.000.000,00 no GLP (Decreto 12.930, art. 19, § 1º, III, redação do 12.992). Atingido o teto, o programa acaba (MP 1.340, art. 2º, § 1º). O ERP só registra: não conhece o acumulado da União, que a ANP divulga. Mudar o teto é versão nova (o GLP foi de 330 para 660 milhões). |
| `Prazo_Declaracao_Dias_Uteis` | número, opcional | Dias úteis depois do fim do período em que o beneficiário entrega a declaração com preços e volumes das NF-e: 5 (Decreto 12.878, art. 9º, e Decreto 12.995, art. 7º). O ERP calcula a data com `Cad_Feriado` e avisa o vencimento; não guarda a data. |
| `Unidade_Prazo_Pagamento` | enumeração {dias_corridos, dias_uteis, ultimo_dia_util_do_mes_seguinte}, opcional | Como ler `Prazo_Pagamento_Dias`. `ultimo_dia_util_do_mes_seguinte` é o pagamento da MP 1.340 e da MP 1.349 (Decreto 12.878, art. 9º, § 2º, redação do 12.930): a ANP paga até o último dia útil do mês seguinte ao do período, desde que a declaração tenha vindo no prazo; nele `Prazo_Pagamento_Dias` fica vazio. |
| `Atualiza_Atraso_Pela_Selic` | booleano, opcional | Verdadeiro quando o atraso do pagamento é atualizado pela Selic (Decreto 12.995, art. 7º, § 5º; a restituição de valor pago a maior também, art. 9º, parágrafo único). Vazio onde o texto lido não diz. |
| `Dia_Util_Limite_Efeito_Desde_Inicio` | número, opcional | O dia útil do período até o qual a adesão entregue vale desde o primeiro dia dele: 5 (MP 1.340, art. 5º, § 3º; MP 1.363, art. 3º, § 3º) e 10 (MP 1.391, art. 3º, § 3º). Passado esse dia, vale a partir do dia seguinte ao da entrega. O efeito é calculado, não guardado. |
| `Campo_Nota_Destaque` | enumeração {informacoes_complementares, nao_definido_no_ato}, opcional | Onde a NF-e leva o destaque do desconto. `informacoes_complementares` na MP 1.363 (Decreto 12.995, art. 5º, II); `nao_definido_no_ato` onde o texto manda identificar ou indicar o valor sem dizer o campo (MP 1.340, 1.349, 1.358, 1.391 e etanol). Responde à Q171-E1 só para a MP 1.363. |
| `Texto_Modelo_Destaque` | texto, opcional | A frase exigida na nota, com o espaço do valor. Na MP 1.363: "Essa operação teve um desconto correspondente ao valor da subvenção de R$ [0,00]/litro de óleo diesel de uso rodoviário, nos termos do disposto na Medida Provisória nº 1.363, de 30 de maio de 2026, e no Decreto nº 12.995, de 8 de junho de 2026". O ERP compara o texto da nota com o modelo e avisa; não escreve a nota. |
| `Regra_Alteracao_Valor` | texto, opcional | Quando e como o Ministro muda o valor ou interrompe: "ao fim de cada período de dois meses, contado de 01/06/2026" (MP 1.363, art. 3º, § 4º); "ao fim de cada período de vigência" e "sem aviso no primeiro período" (MP 1.391, art. 2º, § 1º, II, e § 7º); "depois de 15 dias da publicação" (etanol, art. 2º, § 3º). Texto, porque a regra é prosa; o aviso em dias fica em `Aviso_Previo_Alteracao_Dias`. |
| `Dias_Carencia_Alteracao` | número, opcional | Dias depois da publicação antes dos quais o Ministro não pode mudar o valor: 15 no etanol (art. 2º, § 3º). Vazio nos demais. |
| `Exige_Repasse_Distribuidor` | booleano | Verdadeiro quando o texto exige que o produtor ou importador comprove à ANP o repasse do desconto ao distribuidor e que o distribuidor o repasse adiante (Decreto 12.930, art. 11, redação do 12.974; MP 1.349, art. 10, § 3º). É o que liga o programa às entidades da seção 8. |

## 5.2 `Cad_Combustivel_Programa_Valor`: 16 campos viram 18

**Campo que sai.** `Origem_Produto`. O valor depende de quem recebe, não de onde o produto vem.

**3 campos novos.**

| Campo | Tipo | Descrição |
|---|---|---|
| `Papel_Beneficiario` | enumeração {produtor, importador, qualquer} --- identidade | Quem recebe este valor. `produtor` no acréscimo de R$ 0,80 (MP 1.340, art. 1º-A, parágrafo único); `importador` nos R$ 1,20 (MP 1.349, art. 4º); `qualquer` nos demais. Um mesmo agente pode ter dois papéis (dupla habilitação, Decreto 12.930, art. 5º, § 6º). O refinamento por tipo de agente continua em `ID_Tipo_Agente`. |
| `Unidade_Do_Valor` | enumeração {litro, quilograma, tonelada, metro_cubico} | A unidade em que o ato fixa o valor. O GLP é "por tonelada" (MP 1.349, art. 19, § 1º). A conversão para a unidade do catálogo (quilograma no GLP) é feita na conta do item. |
| `Valor_E_Maximo` | booleano, opcional | Verdadeiro quando o valor é um limite: o GLP é "de até" R$ 850,00 por tonelada; o crédito diário da conta gráfica é limitado a R$ 0,32/l (Decreto 12.878, art. 8º, § 6º) e a R$ 1,20/l (Decreto 12.930, art. 8º, parágrafo único). Vazio onde o texto lido não diz (o acréscimo de R$ 0,80). |

**Descrição alterada de `Valor_Por_Unidade`.** Em programa `subvencao_valor_fixo_por_unidade` é o valor que multiplica a quantidade. Em `subvencao_por_preco_de_referencia` é o **limite diário de crédito por unidade** e **não** o valor pago: o valor pago é o saldo da conta gráfica que a ANP apura. Em `subvencao_equivalente_a_tributo` o ato do Ministro fixa o valor, que não recebi; a tabela fica sem linha para a MP 1.358.

**Mudança no `Condicao_Aplicacao`.** Continua texto. Exemplos que agora vêm do ato: "diesel destinado a estado que aderiu à cooperação (MP 1.349, art. 4º)" e "diesel A de uso rodoviário" (Portaria MF 2.946). Quem decide se o produto da nota se enquadra continua sendo a Q171-C3.

# 6. Período de apuração: `Cad_Combustivel_Programa_Periodo` (entidade nova)

O Decreto 12.878 (com o 12.930) define 20 períodos de apuração do diesel; o 12.930 define sete para o GLP; o 12.995 define 14 para a MP 1.363. A declaração, o requerimento e o pagamento são **por período**. O 171 resolvia isso com datas soltas no requerimento. Você escolheu entidade própria (Q173-3).

A vigência desta tabela é a da **definição** (quando o decreto passou a valer), não a do período. Por exemplo, o Decreto 12.930 redefiniu os períodos II a XI do 12.878; a linha vigente é a do texto consolidado, e as linhas antigas **não entram na carga** (seção 14, limite 5).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Programa_Periodo` | identificador | --- |
| `ID_Combustivel_Programa_Periodo_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Programa_Periodo_Versao). ID_Combustivel_Programa_Periodo é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) --- identidade | O programa a que o período se aplica. |
| `Numero_Periodo` | número --- identidade | O número do inciso no decreto (I a XX no 12.878; I a XIV no 12.995). |
| `Data_Inicio_Periodo` | data | Primeiro dia do período de apuração. |
| `Data_Fim_Periodo` | data | Último dia do período de apuração (inclusive). |
| `Ato_Definicao` | texto | O decreto e o inciso que definem o período, por exemplo "Decreto 12.878, art. 2º, II, redação do Decreto 12.930". |
| `Fundamento_Legal` | texto | O artigo da MP que autoriza dividir em períodos (MP 1.340, art. 3º; MP 1.349, art. 6º). |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada, por exemplo "redefinido pelo Decreto 12.930". |

**13 campos.** A data-limite da declaração (5 dias úteis depois do fim) e a data-limite de pagamento **não são guardadas**: saem de `Data_Fim_Periodo`, de `Prazo_Declaracao_Dias_Uteis` e de `Cad_Feriado`. A MP 1.391 e o etanol **não têm períodos na carga**: o texto remete a ato da ANP que não recebi.

*Exemplo calculado.* Período VI do Decreto 12.995 (MP 1.363), de 16/08 a 31/08/2026: a declaração vence 5 dias úteis depois de 31/08, ou seja, **08/09/2026** (contam os dias 01, 02, 03 e 04 e, como 07/09 é feriado nacional, o quinto é o dia 08). Entregue nesse dia, com pagamento em 30 dias corridos da declaração, a data prevista é **08/10/2026**; passado esse dia, o ERP avisa o atraso e, no programa que atualiza pela Selic, mostra o campo `Valor_Atualizacao_Selic` para preenchimento.

# 7. Lado do beneficiário: o que muda na adesão, no item e no requerimento

**Por D-N68 e pela sua resposta à Q171-3, as entidades desta seção só entram no consolidar quando houver cliente produtor, refinaria, importador ou distribuidor que receba a subvenção.** Ficam desenhadas e com as mudanças abaixo.

## 7.1 `Cad_Participante_Adesao_Programa`: 13 campos viram 17

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Papel_No_Programa` | enumeração {produtor, importador, distribuidor_repassador} --- identidade | O papel em que a empresa aderiu. A **dupla habilitação** (produtor e importador no mesmo período) é permitida (Decreto 12.930, art. 5º, § 6º), por isso o papel entra na identidade. `distribuidor_repassador` é quem assina o termo de acesso e a declaração de repasse (seção 8). |
| `ID_Documento_Termo_Acesso` | referência (Cad_Documento), opcional | O termo de acesso do Anexo II (autorização para a ANP consultar as NF-e na Receita). |
| `ID_Documento_Declaracao_Repasse` | referência (Cad_Documento), opcional | A declaração do distribuidor de que repassa a integralidade do desconto aos revendedores (Decreto 12.930, art. 11, § 1º, II). |
| `ID_Combustivel_Programa_Apoio_Interrompido` | referência (Cad_Combustivel_Programa_Apoio), opcional | O programa de que o participante pediu interrupção para aderir a este (MP 1.363, art. 5º; Anexo III). Substitui o uso de `Observacao` para isso. |

**Efeito da adesão e da interrupção são derivados, não guardados.** `Data_Adesao` é o dia da entrega do termo; o primeiro dia de efeito sai dela, do `Dia_Util_Limite_Efeito_Desde_Inicio` do programa e do período (primeiro dia do período se entregue até o 5º ou o 10º dia útil; senão, o dia seguinte). A interrupção produz efeito no período seguinte (MP 1.363, art. 3º, § 7º; Decreto 12.930, art. 6º, § 1º).

## 7.2 `Mov_Combustivel_Subvencao_Item`: 14 campos viram 16

A entidade é, desde o 171, uma linha por **item de nota e programa**; pela sua resposta à Q173-1 isso passa a ser regra: **uma linha por programa aplicado ao item**, com identidade (`ID_Item`, `ID_Combustivel_Programa_Apoio`). Um item de diesel vendido por importador, com destino a estado que aderiu, pode ter duas linhas: a da MP 1.340 (R$ 0,32) e a da MP 1.349 (R$ 1,20), porque a segunda é paga em acréscimo (MP 1.349, art. 16, parágrafo único).

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Origem_Calculo` | enumeração {calculado_por_unidade, informado_da_apuracao_da_anp} | `calculado_por_unidade` nos programas de valor fixo. `informado_da_apuracao_da_anp` nos programas de PR e PC, onde o valor por item não existe: o item só registra o desconto e o destaque; o valor vem da declaração do período (7.3). |
| `Codigo_Base_Regionalizada` | texto, opcional | A base regional do PR e do PC em que o item foi vendido, como a ANP definir (Decreto 12.878, art. 9º). Texto, até receber o ato da ANP. |

**Campo alterado.** `Valor_Subvencao_Calculado` passa a **opcional**: vazio quando `Origem_Calculo = informado_da_apuracao_da_anp`. `Valor_Por_Unidade_Aplicado` fica na **unidade do item** já convertida (no GLP, 850,00 por tonelada vira 0,85 por quilograma) e é guardado porque a tabela pode ser corrigida.

## 7.3 `Mov_Combustivel_Subvencao_Requerimento`: 13 campos viram 15

A declaração e o requerimento de cada período de apuração são a mesma linha. O requerimento passa a apontar o **período**, e não duas datas.

| Mudança | Descrição |
|---|---|
| Saem `Competencia_Inicio` e `Competencia_Fim` | O período vem de `Cad_Combustivel_Programa_Periodo`. |
| Entra `ID_Combustivel_Programa_Periodo` | Referência (Cad_Combustivel_Programa_Periodo). O período da declaração. |
| Entra `Data_Reapresentacao`, data opcional | O dia em que o beneficiário reapresentou a declaração depois de a ANP requisitar esclarecimento (Decreto 12.995, art. 7º, § 2º; Decreto 12.878, art. 9º, § 3º). O pagamento passa a ser devido até o último dia útil do mês seguinte à reapresentação. |
| Entra `Valor_Atualizacao_Selic`, número opcional | A atualização que a ANP pagou por atraso (Decreto 12.995, art. 7º, § 5º). Informado: o ERP não calcula a Selic. |
| Entra `ID_Documento_Certidao_Regularidade`, referência (Cad_Documento) opcional | A certidão de regularidade de tributos federais, dívida ativa e FGTS que condiciona o pagamento enquanto não houver ato conjunto da Receita e da ANP (Decreto 12.995, art. 12, parágrafo único). |
| `Situacao` ganha `em_exigencia` | O domínio fica {em_preparo, protocolado, em_exigencia, pago, pago_parcialmente, glosado}. `em_exigencia`: a ANP requisitou esclarecimento. |

**Nos programas de PR e PC o `Valor_Requerido` é o valor da declaração do período**, a "demonstração do valor da subvenção a receber por dia" (Decreto 12.878, art. 4º, II): informado, porque a conta gráfica é da ANP.

**Saldo devedor com a União.** Se a conta gráfica fecha em crédito para a União, o beneficiário recolhe a diferença em até 15 dias úteis do fim da concessão (Decreto 12.878, arts. 8º, § 2º, e 13). Não criei entidade nem campo para isso: um `Valor_Pago` negativo esconderia a natureza do valor, e a obrigação é a pagar, não a receber. **Quem diz o registro é o contador (Q173-C6)**; até lá o ERP só registra o fato na `Motivo_Divergencia` do requerimento.

# 8. Repasse do distribuidor: duas entidades novas

Nos programas de PR e PC (MP 1.340 e MP 1.349) o texto não para no produtor ou importador. O **distribuidor** que compra produto subvencionado precisa (Decreto 12.930, art. 11, redação do Decreto 12.974): assinar o termo de acesso (Anexo II) e a declaração de que repassa o desconto; receber o desconto **destacado na NF-e** do produtor ou importador; **consolidar os descontos recebidos para chegar ao desconto médio por litro**; e repassar esse valor médio ao próximo elo, também na NF-e, **até o consumo integral do volume subvencionado**. A fiscalização da ANP considera custos, encargos e tributos, e as obrigações acabam com a interrupção da habilitação, o fim do último período ou o teto (art. 11, §§ 4º a 6º). O descumprimento leva às sanções da Lei 9.847/1999, depois de notificação preliminar.

O dicionário já tem as notas de entrada e de saída; falta guardar **quanto do que entrou era subvencionado, com que desconto, e quanto já foi repassado**. São duas entidades, uma de cada lado, ambas só quando houver cliente distribuidor (Q173-8). A adesão do distribuidor vive em `Cad_Participante_Adesao_Programa` com `Papel_No_Programa = distribuidor_repassador` (seção 7.1).

**`Mov_Combustivel_Subvencao_Entrada_Item`** (9 campos): o item da NF-e de entrada com produto subvencionado e o desconto que veio destacado.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Subvencao_Entrada` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) | O distribuidor, destinatário da nota. |
| `ID_Item` | referência (Mov_Nota_Fiscal_Entrada_Item) | O item de entrada. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) | O programa cujo desconto o fornecedor destacou. Um item pode ter duas linhas (MP 1.340 e MP 1.349). |
| `Quantidade_Subvencionada` | número | A parte do item que é produto subvencionado, na unidade do item (a 20 °C nos líquidos). Pode ser menor que a quantidade da nota. |
| `Desconto_Por_Unidade_Recebido` | número | O desconto por unidade que o fornecedor destacou na nota. Informado: sai do texto da nota do fornecedor. |
| `Origem_Informacao` | enumeração {texto_da_nota, informado} | `texto_da_nota` quando o ERP leu o destaque da NF-e; `informado` quando alguém digitou. |
| `Status` | enumeração {calculada, pendente_decisao, confirmada} | Padrão do `Mov_Apuracao_Tef`. `pendente_decisao` quando falta o programa, o desconto ou a adesão do distribuidor. |
| `Pendencia` | texto, opcional | A pendência, por extenso. |

**`Mov_Combustivel_Subvencao_Repasse_Item`** (9 campos): o item da NF-e de saída que leva o desconto médio ao próximo elo.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Subvencao_Repasse` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) | O distribuidor, emitente da nota. |
| `ID_Item` | referência (Mov_Nota_Fiscal_Saida_Item) | O item de saída. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) | O programa de que o desconto vem. |
| `Quantidade_Repassada` | número | A parte do item que é produto subvencionado repassado. |
| `Desconto_Medio_Por_Unidade_Repassado` | número | O desconto médio por unidade que a nota leva. **Guardado**, porque é o valor da nota emitida e depende do saldo e dos lotes daquele momento. |
| `Destacado_Na_Nota` | booleano, opcional | Se o desconto saiu destacado na nota. Vazio até a equipe responder a Q173-E1. |
| `Status` | enumeração {calculada, pendente_decisao, confirmada} | Padrão do `Mov_Apuracao_Tef`. |
| `Pendencia` | texto, opcional | A pendência, por extenso. |

**O que não é guardado.** O **saldo de volume subvencionado** (soma das quantidades de entrada menos a soma das repassadas, por empresa e programa) e o **desconto médio de referência** (soma de quantidade vezes desconto, dividida pela soma das quantidades) saem das duas tabelas na consulta. **O método de ponderação do texto ("valor médio") não diz** se a média é do lote, do mês ou do saldo corrente; a conta acima é a mais simples e é leitura minha (Q173-E4).

**Avisos, nunca bloqueios.** (1) Repasse que passa do saldo subvencionado: "repasse acima do volume subvencionado recebido". (2) `Desconto_Medio_Por_Unidade_Repassado` diferente da média de referência: aviso com as duas contas. (3) Programa com `Exige_Repasse_Distribuidor` e distribuidor sem adesão ativa no papel `distribuidor_repassador`: aviso. (4) Depois da interrupção da habilitação, do fim do último período ou do teto, os avisos de repasse param (art. 11, § 6º).

*Exemplo calculado (valores e datas hipotéticos).* O distribuidor recebe 100.000 l com desconto de R$ 0,60/l e 50.000 l com desconto de R$ 0,30/l. Desconto médio de referência: (100.000 × 0,60 + 50.000 × 0,30) ÷ 150.000 = 75.000 ÷ 150.000 = **R$ 0,50/l**. Vende 40.000 l subvencionados e a nota leva R$ 0,50/l (`Desconto_Medio_Por_Unidade_Repassado`); o saldo passa a 110.000 l. Se a nota levar R$ 0,40/l, o ERP avisa a diferença de R$ 0,10/l (4.000,00 no item) e o item segue `calculada`.

**Relatório, não campo.** O distribuidor também envia à ANP, a cada 14 dias, volumes adquiridos e vendidos e os valores médios de aquisição e de venda por metro cúbico (diesel) ou por tonelada (GLP), com a diferença (Decreto 12.930, art. 20, redação do 12.974). Tudo isso sai das notas; não criei campo. A Q173-E5 pergunta se o ERP precisa gerar o relatório.

# 9. MP 1.358: tipo próprio e equivalência a tributos

A MP 1.358 autoriza subvenção **equivalente às parcelas deduzidas do preço**: PIS/Pasep, Cofins e Cide-Combustíveis na gasolina e suas correntes; PIS/Pasep e Cofins no diesel de uso rodoviário (art. 1º, § 1º). O valor e o período saem de ato do Ministro, que **não recebi**; o pagamento **não pode superar o ônus** dos tributos aplicáveis (§ 3º); a vigência é de dois meses do ato, prorrogável (§ 4º); a ANP paga em até 30 dias do requerimento (art. 2º, § 2º). O Planalto marca a MP com "Vigência encerrada".

**Tipo próprio.** `Tipo_Apoio = subvencao_equivalente_a_tributo`. O valor por unidade não vem do texto; **a tabela de valor fica sem linha** até o ato chegar. O que o texto dá é **de quais tributos e de quais combustíveis** a subvenção é a equivalência, e isso é o que a nova entidade guarda.

**`Cad_Combustivel_Programa_Tributo_Equivalente`** (13 campos)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Programa_Tributo_Equivalente` | identificador | --- |
| `ID_Combustivel_Programa_Tributo_Equivalente_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Programa_Tributo_Equivalente_Versao). ID_Combustivel_Programa_Tributo_Equivalente é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) --- identidade | O programa. |
| `ID_Combustivel_Regime` | referência (Cad_Combustivel_Regime) --- identidade | O combustível (gasolina ou diesel). |
| `ID_Imposto` | referência (Cad_Imposto) --- identidade | O tributo cuja parcela deduzida a subvenção equivale: PIS, Cofins ou Cide-Combustíveis. |
| `Limita_Pagamento_Ao_Onus` | booleano | Verdadeiro quando o pagamento não pode superar o ônus deste tributo no combustível (MP 1.358, art. 1º, § 3º). O ERP não conhece o ônus de quem recebe; só registra e avisa quando o requerimento pede mais do que o tributo declarado. |
| `Fundamento_Legal` | texto | O artigo do ato. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |
| `Observacao` | texto, opcional | Por exemplo, "gasolina e suas correntes". |

**Cide-Combustíveis entra como imposto.** O dicionário não tinha a Cide (`Cad_Imposto` traz ICMS, IPI, PIS, Cofins, ISS, CBS, IBS e Imposto Seletivo). Entra **uma linha nova em `Cad_Imposto`**: `CIDE-COMBUSTIVEIS`, "Contribuição de Intervenção no Domínio Econômico incidente sobre combustíveis", esfera `federal`, natureza `outro`. **Não desenho alíquota da Cide**: não li texto dela, e o ERP só precisa nomeá-la para a equivalência.

**Carga:** 5 linhas, todas provisórias: gasolina com PIS, Cofins e Cide; diesel com PIS e Cofins.

# 10. Etanol hidratado: Decreto 13.119

O Decreto 13.119 (16/09/2026, regulamenta o art. 2º, §§ 5º e 6º, da LC 235/2026) é um programa de valor fixo e **cabe sem entidade nova**:

1. **Programa.** `Tipo_Apoio = subvencao_valor_fixo_por_unidade`, órgão pagador ANP, adesão exigida, desconto no preço, destaque na NF-e sem campo definido, pagamento em 30 dias corridos, aviso de 5 dias e `Dias_Carencia_Alteracao = 15`.
2. **Valor.** R$ 0,2519 por litro de `EHC`, para todos os beneficiários, de 16/09 a 15/10/2026. O fim é **leitura minha**: o texto diz "trinta dias contados da data de publicação" e a publicação é de 16/09/2026 (edição extra); contando o dia da publicação, o 30º dia é 15/10/2026. A prorrogação não consta do texto.
3. **Beneficiários.** "Produtores e cooperativas de produtores de biocombustíveis destinados ao consumo final autorizados pela ANP". O domínio `agente_cadeia_combustiveis` tem `produtor_biocombustiveis`, mas **não tem a cooperativa**: entra o valor novo `cooperativa_produtores_biocombustiveis` (seção 12).
4. **Sem período na carga.** A adesão, os períodos e a apuração vêm de ato da ANP que não recebi; o programa fica com a tabela de períodos vazia até lá.
5. **Só o etanol hidratado.** O texto não alcança o anidro nem o biodiesel.

O Decreto 13.119 cita o **Decreto 13.116 (09/09/2026)** como base de uma redução de tributação que motiva a subvenção. **Não li o 13.116**; se ele mudar a alíquota do etanol, a mudança entra por `Cad_Aliquota_Combustivel` e pelo PIS/Cofins por unidade, que já existem, e não por este desenho.

# 11. Imposto de exportação: `Cad_Imposto_Exportacao_Aliquota` (entidade nova)

A MP 1.340 criou dois impostos de exportação: **12%** sobre óleos brutos de petróleo ou de minerais betuminosos, NCM 2709, sobre o valor total das exportações, que o Comitê-Executivo de Gestão da Câmara de Comércio Exterior pode reduzir (arts. 10 e 11); e **50%** sobre o óleo diesel de uso rodoviário, NCM 2710.19.21, **enquanto perdurar a subvenção do art. 1º** (art. 12, redação da MP 1.349). O dicionário tinha só `Cad_NCM_Imposto_Seletivo`, que é de outro tributo.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Imposto_Exportacao_Aliquota` | identificador | --- |
| `ID_Imposto_Exportacao_Aliquota_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Imposto_Exportacao_Aliquota_Versao). ID_Imposto_Exportacao_Aliquota é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Classificacao_Mercadoria` | referência (Cad_Classificacao_Mercadoria) --- identidade | A NCM, de qualquer nível (vale para os descendentes): 2709 e 2710.19.21. |
| `Descricao_Produto` | texto | O produto como o ato descreve. |
| `Aliquota_Percentual` | número | A alíquota sobre o valor da exportação (12 e 50). |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio), opcional | O programa cuja duração limita a alíquota (a subvenção da MP 1.340 no diesel). |
| `Condicao_Vigencia` | texto, opcional | A condição escrita no ato, por exemplo "enquanto perdurar a subvenção econômica de que trata o art. 1º". |
| `Pode_Ser_Reduzida_Por_Ato` | booleano | Verdadeiro quando o ato permite que um órgão reduza a alíquota (12%: sim; 50%: o texto lido não prevê). |
| `Orgao_Que_Reduz` | texto, opcional | O órgão, quando há: "Comitê-Executivo de Gestão da Câmara de Comércio Exterior" (art. 11). |
| `Fundamento_Legal` | texto | O artigo do ato. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

**15 campos.** Uma linha nova em `Cad_Imposto` (`IE`, "Imposto sobre a Exportação", esfera `federal`, natureza `outro`) nomeia o tributo para quem o referencia depois. **O ERP só registra a alíquota.** Onde incide, quem recolhe e como entra no item de exportação (`Mov_Nota_Fiscal_Saida_Item_Exportacao`) é pergunta ao contador (Q173-C4); não criei campo no item.

**Carga:** 2 linhas provisórias. A de 12% vale de 12/03/2026 e **não tem fim no texto** (31/12/9999). A de 50% vale de 12/03/2026 e termina em 31/12/2026: **leitura minha**, porque o fim da subvenção da MP 1.340 é "limitado a 31 de dezembro de 2026" (art. 1º) e pode vir antes se o teto acabar (art. 2º, § 1º).

# 12. O que entra no próximo "consolidar"

Pela sua resposta à Q171-3, o que é **parâmetro** entra agora; o que é **de quem recebe a subvenção** entra quando houver cliente (D-N68). O 173 **substitui as listas de campos do 171**: as cinco entidades do 171 entram com os campos abaixo, não com os do 171.

**10 entidades: 5 de parâmetro (88 campos) e 5 de quem recebe (66 campos).**

| Entidade | Tipo | Campos | Mudança sobre o 171 | Vigência | Módulo | Capítulo |
|---|---|---|---|---|---|---|
| `Cad_Combustivel_Programa_Apoio` | parâmetro | 29 | de 19 (+10) | sim | Motores Transversais | 5 |
| `Cad_Combustivel_Programa_Valor` | parâmetro por período | 18 | de 16 (+2 líquidos) | sim | Motores Transversais | 5 |
| `Cad_Combustivel_Programa_Periodo` | parâmetro | 13 | **nova** | sim | Motores Transversais | 5 |
| `Cad_Combustivel_Programa_Tributo_Equivalente` | parâmetro | 13 | **nova** | sim | Motores Transversais | 5 |
| `Cad_Imposto_Exportacao_Aliquota` | parâmetro | 15 | **nova** | sim | Motores Transversais | 5 |
| `Cad_Participante_Adesao_Programa` | cadastro do beneficiário | 17 | de 13 (+4) | sim | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Item` | apuração por item de nota | 16 | de 14 (+2) | não | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Requerimento` | requerimento e pagamento | 15 | de 13 (+2 líquidos) | não | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Entrada_Item` | entrada do distribuidor | 9 | **nova** | não | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Repasse_Item` | repasse do distribuidor | 9 | **nova** | não | Contabilidade & Fiscal | 7 |

Contas: parâmetros 29 + 18 + 13 + 13 + 15 = **88**; de quem recebe 17 + 16 + 15 + 9 + 9 = **66**; total **154**, contra 75 do 171. Entidades novas: 13 + 13 + 15 + 9 + 9 = **59**.

**Mantido do 171.** A alteração de `Cad_Aliquota_Combustivel` (`Carater_Vigencia` e `ID_Combustivel_Programa_Apoio`, 2 campos) e o critério novo do Motor, `adesao_programa_do_emitente`, em `campo_criterio_regra`. **Nenhum código de classificação tributária é criado.**

**Valores novos em domínio e linhas novas em tabela de apoio.**

| Onde | O que entra |
|---|---|
| `Cad_Classe_Sistema`, domínio `agente_cadeia_combustiveis` | `agente_comercio_exterior` (Agente de comércio exterior autorizado pela ANP; MP 1.340, art. 1º, § 2º, I) e `cooperativa_produtores_biocombustiveis` (Cooperativa de produtores de biocombustíveis; Decreto 13.119, art. 1º). O domínio passa de 11 para 13 valores. O produtor de derivados de petróleo é a `refinaria`; o distribuidor que importa é o `distribuidor` |
| `Cad_Imposto` | `CIDE-COMBUSTIVEIS` (seção 9) e `IE` (seção 11) |

**Cargas provisórias** (todas com `Situacao_Dado = provisorio`; só o que sai de texto oficial; detalhe no Anexo A):

| Tabela | Linhas |
|---|---|
| `Cad_Combustivel_Programa_Apoio` | 7 programas |
| `Cad_Combustivel_Programa_Valor` | 7 valores |
| `Cad_Combustivel_Programa_Periodo` | 45 períodos (20 da MP 1.340, 4 da MP 1.349 no diesel, 7 do GLP, 14 da MP 1.363) |
| `Cad_Combustivel_Programa_Tributo_Equivalente` | 5 linhas (MP 1.358) |
| `Cad_Imposto_Exportacao_Aliquota` | 2 linhas |
| `Cad_Imposto` | 2 linhas |
| `Cad_Classe_Sistema` | 2 valores |
| **Total** | **70 linhas** |

**Não carrego:** nenhum valor das notícias (inclusive o R$ 0,35 do diesel A); valor da MP 1.358 (ato do Ministro não recebido); prorrogação de 26/10; períodos da MP 1.391 e do etanol (atos da ANP não recebidos); períodos antigos do Decreto 12.878 que o 12.930 redefiniu. As tabelas de quem recebe saem **vazias**.

**Se a Q173-8 disser "sem cliente".** Entram as cinco entidades de parâmetro, a alteração de `Cad_Aliquota_Combustivel`, os domínios, as duas linhas de `Cad_Imposto` e as 70 linhas de carga. As cinco entidades de quem recebe (66 campos) ficam desenhadas.

# 13. Perguntas

## 13.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q173-5** | `Cad_Combustivel_Programa_Apoio` com `Tipo_Apoio` de quatro valores e 10 campos novos (29 no total); `Cad_Combustivel_Programa_Valor` sem `Origem_Produto` e com `Papel_Beneficiario`, `Unidade_Do_Valor` e `Valor_E_Maximo` (18 no total); o domínio de agentes com `agente_comercio_exterior` e `cooperativa_produtores_biocombustiveis`? | Sim |
| **Q173-6** | `Cad_Combustivel_Programa_Periodo` (13 campos), o requerimento apontando o período, e a carga dos 45 períodos do texto vigente (sem os períodos antigos do Decreto 12.878)? | Sim |
| **Q173-7** | Carga provisória de 70 linhas, só de texto oficial, com as quatro leituras minhas marcadas: fim do etanol em 15/10/2026, programas da MP 1.391 e do etanol sem fim no cabeçalho (o fim está no valor), programa da MP 1.358 sem fim e imposto de 50% até 31/12/2026? | Sim |
| **Q173-8** | O lado de quem recebe (adesão com 17 campos, item com 16, requerimento com 15) e o repasse do distribuidor (`Mov_Combustivel_Subvencao_Entrada_Item` e `Mov_Combustivel_Subvencao_Repasse_Item`, 9 campos cada) só entram no consolidar **quando houver cliente** (D-N68)? | Sim, só quando houver cliente |
| **Q173-9** | MP 1.358 como `subvencao_equivalente_a_tributo`, com `Cad_Combustivel_Programa_Tributo_Equivalente` (13 campos, 5 linhas na carga) e a Cide-Combustíveis como linha nova de `Cad_Imposto`, sem alíquota? | Sim |
| **Q173-10** | `Cad_Imposto_Exportacao_Aliquota` (15 campos, 2 linhas) e a linha `IE` em `Cad_Imposto`, sem campo novo no item de exportação até o contador responder a Q173-C4? | Sim |
| **Q173-11** | Aplico tudo no próximo "consolidar", junto com os documentos já aprovados (157, 150, 156, 164, 168 e 170), **substituindo o 171 por este 173**? | Sim |

## 13.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q173-C1** | Subvenção recebida pelo produtor ou importador (custeio, por litro vendido): é receita? Entra na base de PIS/Cofins, IRPJ e CSLL? O Decreto 12.878 trata o PIS/Cofins sobre a receita da subvenção e o compensa pela conta gráfica (art. 3º, § 3º, II, e art. 8º, § 1º): isso confirma que há incidência? Qual a conta e o tratamento na ECF? Cabe em `Cad_Subvencao_Investimento`? (repete a Q171-C1, agora com o artigo) | Só registro; sem lançamento e sem tributo |
| **Q173-C2** | O desconto dado ao comprador por causa da subvenção (Decreto 12.995, art. 5º, I: preço deduzido do valor da subvenção) entra na base de algum tributo (ICMS ad rem, PIS/Cofins por unidade, CBS por quantidade, IRPJ do comprador)? É desconto incondicional? (repete a Q171-C2) | Não altera a base; campo próprio, fora do desconto incondicional |
| **Q173-C3** | Como o ERP identifica "diesel de uso rodoviário" (MPs 1.340, 1.349 e 1.363) e "diesel A de uso rodoviário" (Portaria MF 2.946) na nota: código ANP, NCM 2710.19.21, CFOP ou destinação do comprador? (repete a Q171-C3) | `Condicao_Aplicacao` em texto; item pendente até a regra |
| **Q173-C4** | Imposto de exportação (12% e 50%): fato gerador, base, quem recolhe e onde se registra no item de exportação? O fim do 50% acompanha o fim da subvenção da MP 1.340 ou o fim do teto? | Só a alíquota na tabela; sem campo no item |
| **Q173-C5** | O Planalto marca "Vigência encerrada" nas MPs 1.340, 1.349, 1.358 e 1.363. Isso é conversão em lei, rejeição ou perda de eficácia? O que muda nos valores a pagar e nos decretos (12.878, 12.930, 12.995)? E na MP 1.358, a subvenção equivalente a tributo é receita ou redução de custo? | A carga segue o texto de cada ato; sem tratamento |
| **Q173-C6** | Saldo devedor com a União quando a conta gráfica fecha em crédito para ela (Decreto 12.878, arts. 8º, § 2º, e 13), e a Selic paga ou devida: como se registram? | Só registro na `Motivo_Divergencia` do requerimento |
| **Q173-C7** | Subvenção a receber: reconhece-se na venda, no protocolo ou no pagamento? (repete a Q171-C9) | Título só no protocolo |
| **Q173-C8** | A partir de 27/09/2026 convivem a MP 1.363 (R$ 1,12) e a MP 1.391 (R$ 2,12)? Quem aderiu a uma pode estar na outra? E sair de um programa para entrar em outro: o que acontece com as vendas do período anterior? (junta a Q171-C4) | O item segue o programa com adesão ativa na data; havendo dois, duas linhas |

A Q171-C5 (2027) **continua em aberto**. As Q171-C6 (devolução de tributo), C7 (GLP em tonelada) e C8 (aviso de 15 dias) **ficam respondidas pelo texto**: C6 deixa de existir (a MP 1.358 não é devolução), C7 resolve-se guardando a unidade do ato, e C8 tem regra por programa (15, 10 e 5 dias; sem aviso no primeiro período da MP 1.391).

## 13.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q173-E1** | O destaque do desconto na NF-e fora da MP 1.363: qual campo e qual frase na MP 1.391, no etanol e nos programas anteriores? Só **Informações complementares** com texto livre, ou há campo estruturado em nota técnica? Preciso do leiaute ou da NT. |
| **Q173-E2** | Algum cliente ou fornecedor da Mlegate é produtor, refinaria, importador, **distribuidor** de diesel, GLP ou etanol que adere aos programas? Isso responde à Q173-8 (e à Q171-E2). |
| **Q173-E3** | Mandar os textos que faltam: Portaria MF 2.813 e a prorrogação de 26/10; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha da MP 1.391 e do etanol); a LC 235; o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio; e, quando saírem, o QAV e o que valer para 2027. |
| **Q173-E4** | Método do desconto médio do distribuidor (Decreto 12.930, art. 11, § 1º, IV, redação do 12.974): média do lote, do mês ou do saldo corrente? A ANP tem modelo de planilha (Decreto 12.995, art. 6º)? |
| **Q173-E5** | O distribuidor envia à ANP, a cada 14 dias, volumes e valores médios de compra e de venda (Decreto 12.930, art. 20). O ERP precisa gerar esse relatório? |
| **Q173-E6** | O contas a receber tem tipo de título para a subvenção, com a ANP como órgão pagador? O ERP emitiu notas de diesel, GLP ou etanol em 2026 com desconto de subvenção, e precisamos do histórico? (juntam Q171-E4 e Q171-E6) |

# 14. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **O que li e como.** Li MPs, decretos e portaria nos textos do Planalto e do DOU. O **etanol (Decreto 13.119) li pela página do Senado**, que avisa não substituir o DOU. Os Decretos 12.883, 12.942, 12.974 e 12.992 só pelas redações que o texto consolidado dos outros decretos traz. **Não li:** Portaria MF 2.813, prorrogação de 26/10, ato do Ministro da MP 1.358, atos da ANP, LC 235, Decreto 13.116.
3. **O ERP não calcula a subvenção por PR e PC.** Nesses programas a ANP apura por base regional e por dia, com conta gráfica; o ERP registra a declaração e o pagamento.
4. **Não trato do tratamento contábil nem tributário** da subvenção, do imposto de exportação e da Cide (Q173-C1 a C6). O ERP só registra.
5. **Períodos antigos não entram.** O Decreto 12.930 redefiniu os períodos II a XI do 12.878 e criou os XII a XX; carrego só a redação vigente. Se o contador precisar da redação original para operações de 01/04 a 15/04/2026, a linha antiga entra como versão (a tabela é versionada).
6. **As leituras minhas** estão marcadas e vão ao contador: fim do etanol em 15/10/2026; programas da MP 1.391 e do etanol com fim em aberto no cabeçalho; programa da MP 1.358 com fim em aberto; imposto de exportação de 50% até 31/12/2026; média simples do desconto do distribuidor; `Valor_E_Maximo` vazio no R$ 0,80.
7. **O Planalto marca "Vigência encerrada" em quatro MPs** (1.340, 1.349, 1.358 e 1.363). A carga registra a vigência que o texto de cada ato fixa; o que o encerramento significa é a Q173-C5.
8. **Não achei continuidade em 2027.** O desenho funciona com ou sem programa vigente: sem linha de valor, o ERP avisa "sem valor vigente" e não calcula subvenção.

# Anexo A. Carga provisória (todas com `Situacao_Dado = provisorio`)

Só o que sai de texto oficial que li. Vigência final em 31/12/9999 quando o fim é indefinido (convenção da Fase 0). **Leitura minha** vem marcada.

## A.1 `Cad_Combustivel_Programa_Apoio`: 7 linhas

| `Codigo` | `Tipo_Apoio` | `Ato_Instituidor` | Vigência do cabeçalho | `Limite_Total_Valor` (R$) | Observação |
|---|---|---|---|---|---|
| `SUBVENCAO-DIESEL-MP-1340` | `subvencao_por_preco_de_referencia` | MP 1.340, de 12/03/2026; Decreto 12.878, de 13/03/2026 | 12/03/2026 a 31/12/2026 | 10.000.000.000,00 | Art. 1º e art. 2º da MP |
| `SUBVENCAO-DIESEL-IMPORTADOR-MP-1349` | `subvencao_por_preco_de_referencia` | MP 1.349, art. 4º, de 07/04/2026; Decreto 12.930, de 15/04/2026 | 07/04/2026 a 31/05/2026 | 4.000.000.000,00 | Prorrogável por dois meses por ato (art. 4º, § 5º), que não consta |
| `SUBVENCAO-GLP-IMPORTACAO-MP-1349` | `subvencao_por_preco_de_referencia` | MP 1.349, art. 19; Decreto 12.930, art. 19 (redações dos Decretos 12.942 e 12.992) | 01/04/2026 a 31/07/2026 | 660.000.000,00 | Entregas de 01/04 a 31/07/2026 |
| `SUBVENCAO-TRIBUTOS-MP-1358` | `subvencao_equivalente_a_tributo` | MP 1.358, de 13/05/2026 (retificada em 28/05/2026) | 13/05/2026 a 31/12/9999 (**leitura minha**: o ato do Ministro não veio) | vazio | Valor e período por ato do Ministro (art. 1º, §§ 2º e 4º) |
| `SUBVENCAO-DIESEL-MP-1363` | `subvencao_valor_fixo_por_unidade` | MP 1.363, de 30/05/2026; Decreto 12.995, de 08/06/2026 | 01/06/2026 a 31/12/2026 | vazio | Art. 1º, § 2º |
| `SUBVENCAO-DIESEL-MP-1391` | `subvencao_valor_fixo_por_unidade` | MP 1.391, de 11/09/2026; Portaria MF 2.946, de 25/09/2026 | 11/09/2026 a 31/12/9999 (**leitura minha**: o fim está no valor) | vazio | A vigência é de até 30 dias por ato |
| `SUBVENCAO-ETANOL-HIDRATADO-DEC-13119` | `subvencao_valor_fixo_por_unidade` | Decreto 13.119, de 16/09/2026 (LC 235/2026, art. 2º, §§ 5º e 6º) | 16/09/2026 a 31/12/9999 (**leitura minha**: o fim está no valor) | vazio | Só etanol hidratado |

Demais campos do cabeçalho, por programa (V = vazio):

| `Codigo` | `Orgao_Pagador` | Adesão | Desconto no preço | Destaque na nota | `Campo_Nota_Destaque` | `Veda_Cumulacao` | `Prazo_Pagamento_Dias` e unidade | `Prazo_Declaracao_Dias_Uteis` | `Aviso_Previo_Alteracao_Dias` | `Dias_Carencia_Alteracao` | `Dia_Util_Limite_Efeito_Desde_Inicio` | `Atualiza_Atraso_Pela_Selic` | `Exige_Repasse_Distribuidor` |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| `SUBVENCAO-DIESEL-MP-1340` | ANP | sim | sim | sim | `nao_definido_no_ato` | não | V e `ultimo_dia_util_do_mes_seguinte` | 5 | V | V | 5 | V | sim |
| `SUBVENCAO-DIESEL-IMPORTADOR-MP-1349` | ANP | sim | sim | sim | `nao_definido_no_ato` | não | V e `ultimo_dia_util_do_mes_seguinte` | 5 | V | V | V | V | sim |
| `SUBVENCAO-GLP-IMPORTACAO-MP-1349` | ANP | sim | sim | V (**não li**) | V | não | V | V | V | V | V | V | não |
| `SUBVENCAO-TRIBUTOS-MP-1358` | ANP | sim | sim | sim | `nao_definido_no_ato` | não | 30 e `dias_corridos` | V | V | V | V | V | não |
| `SUBVENCAO-DIESEL-MP-1363` | ANP | sim | sim | sim | `informacoes_complementares` | sim | 30 e `dias_corridos` | 5 | 15 | V | 5 | sim | não |
| `SUBVENCAO-DIESEL-MP-1391` | ANP | sim | sim | sim | `nao_definido_no_ato` | não | V | V | 10 | V | 10 | V | não |
| `SUBVENCAO-ETANOL-HIDRATADO-DEC-13119` | ANP | sim | sim | sim | `nao_definido_no_ato` | não | 30 e `dias_corridos` | V | 5 | 15 | V | V | não |

`Texto_Modelo_Destaque` só na MP 1.363 (frase do Decreto 12.995, art. 5º, II). `Regra_Alteracao_Valor` na MP 1.363, MP 1.391 e etanol (seção 5.1). Nos campos "não" de `Veda_Cumulacao` o texto lido não veda; não é afirmação de que é permitido.

## A.2 `Cad_Combustivel_Programa_Valor`: 7 linhas

| Programa | Combustível | `Papel_Beneficiario` | `Valor_Por_Unidade` | `Unidade_Do_Valor` | `Valor_E_Maximo` | Vigência | `Origem_Valor` | `Data_Publicacao` | Artigo |
|---|---|---|---|---|---|---|---|---|---|
| `SUBVENCAO-DIESEL-MP-1340` | `OLEO_DIESEL` | `qualquer` | 0,3200 | litro | sim | 12/03/2026 a 31/12/2026 | `medida_provisoria` | 12/03/2026 | MP 1.340, art. 1º; Decreto 12.878, art. 8º, § 6º |
| `SUBVENCAO-DIESEL-MP-1340` | `OLEO_DIESEL` | `produtor` | 0,8000 | litro | vazio | 07/04/2026 a 31/05/2026 | `medida_provisoria` | 07/04/2026 | MP 1.340, art. 1º-A (MP 1.349, art. 15); Decreto 12.930, art. 15 |
| `SUBVENCAO-DIESEL-IMPORTADOR-MP-1349` | `OLEO_DIESEL` | `importador` | 1,2000 | litro | sim | 07/04/2026 a 31/05/2026 | `medida_provisoria` | 07/04/2026 | MP 1.349, art. 4º; Decreto 12.930, art. 8º, parágrafo único |
| `SUBVENCAO-GLP-IMPORTACAO-MP-1349` | `GLP` | `qualquer` | 850,0000 | tonelada | sim | 01/04/2026 a 31/07/2026 | `medida_provisoria` | 07/04/2026 | MP 1.349, art. 19, § 1º; Decreto 12.930, art. 19, § 1º |
| `SUBVENCAO-DIESEL-MP-1363` | `OLEO_DIESEL` | `qualquer` | 1,1200 | litro | vazio | 01/06/2026 a 31/12/2026 | `medida_provisoria` | 30/05/2026 | MP 1.363, art. 1º |
| `SUBVENCAO-DIESEL-MP-1391` | `OLEO_DIESEL` | `qualquer` | 2,1200 | litro | vazio | 27/09/2026 a 26/10/2026 | `portaria` | 25/09/2026 | Portaria MF 2.946, arts. 1º, 2º e 4º |
| `SUBVENCAO-ETANOL-HIDRATADO-DEC-13119` | `EHC` | `qualquer` | 0,2519 | litro | vazio | 16/09/2026 a 15/10/2026 (**leitura minha**) | `decreto` | 16/09/2026 | Decreto 13.119, art. 2º |

`Condicao_Aplicacao`: "diesel de uso rodoviário" nas linhas da MP 1.340 e da MP 1.363; "diesel de uso rodoviário destinado a estado ou ao Distrito Federal que aderiu (R$ 0,60 da União e R$ 0,60 do ente)" na MP 1.349; "diesel A de uso rodoviário; prorrogável por igual período" na MP 1.391; "importação de GLP" no GLP; "etanol hidratado combustível" no etanol. `ID_Tipo_Agente` vazio em todas. **Como os valores somam.** O R$ 0,80 é acréscimo ao R$ 0,32 (soma R$ 1,12 ao produtor de 07/04 a 31/05/2026) e o R$ 1,20 é pago em acréscimo ao R$ 0,32 (MP 1.349, art. 16, parágrafo único). A soma é feita pelas linhas de item (seção 7.2: uma linha por programa aplicado), não por campo.

## A.3 `Cad_Combustivel_Programa_Periodo`: 45 linhas

`Situacao_Dado = provisorio`; `Vigencia_Fim` = 31/12/9999. `Vigencia_Inicio` é a data do decreto que deu a redação vigente da linha: 13/03/2026 (período I do Decreto 12.878); 15/04/2026 (períodos II a XX do 12.878 na redação do 12.930, e os quatro da MP 1.349); 30/05/2026 (GLP, redação do Decreto 12.992); 09/06/2026 (MP 1.363; DOU de 09/06/2026). Para os decretos, a data é a do decreto: **a data de publicação no DOU só conferi no Decreto 12.995**.

**A.3.1 MP 1.340, diesel: 20 períodos (Decreto 12.878, art. 2º, redação do Decreto 12.930)**

| Nº | Início | Fim | Ato de definição |
|---|---|---|---|
| I | 12/03/2026 | 31/03/2026 | Decreto 12.878, art. 2º, I (original) |
| II | 01/04/2026 | 06/04/2026 | Decreto 12.878, art. 2º, II, redação do Decreto 12.930 |
| III | 07/04/2026 | 19/04/2026 | Decreto 12.878, art. 2º, III, redação do Decreto 12.930 |
| IV | 20/04/2026 | 30/04/2026 | Decreto 12.878, art. 2º, IV, redação do Decreto 12.930 |
| V | 01/05/2026 | 15/05/2026 | Decreto 12.878, art. 2º, V, redação do Decreto 12.930 |
| VI | 16/05/2026 | 31/05/2026 | Decreto 12.878, art. 2º, VI, redação do Decreto 12.930 |
| VII | 01/06/2026 | 15/06/2026 | Decreto 12.878, art. 2º, VII, redação do Decreto 12.930 |
| VIII | 16/06/2026 | 30/06/2026 | Decreto 12.878, art. 2º, VIII, redação do Decreto 12.930 |
| IX | 01/07/2026 | 15/07/2026 | Decreto 12.878, art. 2º, IX, redação do Decreto 12.930 |
| X | 16/07/2026 | 31/07/2026 | Decreto 12.878, art. 2º, X, redação do Decreto 12.930 |
| XI | 01/08/2026 | 15/08/2026 | Decreto 12.878, art. 2º, XI, redação do Decreto 12.930 |
| XII | 16/08/2026 | 31/08/2026 | Decreto 12.878, art. 2º, XII, redação do Decreto 12.930 |
| XIII | 01/09/2026 | 15/09/2026 | Decreto 12.878, art. 2º, XIII, redação do Decreto 12.930 |
| XIV | 16/09/2026 | 30/09/2026 | Decreto 12.878, art. 2º, XIV, redação do Decreto 12.930 |
| XV | 01/10/2026 | 15/10/2026 | Decreto 12.878, art. 2º, XV, redação do Decreto 12.930 |
| XVI | 16/10/2026 | 31/10/2026 | Decreto 12.878, art. 2º, XVI, redação do Decreto 12.930 |
| XVII | 01/11/2026 | 15/11/2026 | Decreto 12.878, art. 2º, XVII, redação do Decreto 12.930 |
| XVIII | 16/11/2026 | 30/11/2026 | Decreto 12.878, art. 2º, XVIII, redação do Decreto 12.930 |
| XIX | 01/12/2026 | 15/12/2026 | Decreto 12.878, art. 2º, XIX, redação do Decreto 12.930 |
| XX | 16/12/2026 | 31/12/2026 | Decreto 12.878, art. 2º, XX, redação do Decreto 12.930 |

**A.3.2 MP 1.349, diesel do importador: 4 períodos** (os da MP 1.340 que cabem em 07/04 a 31/05/2026, pelo Decreto 12.930, art. 2º)

| Nº | Início | Fim | Ato de definição |
|---|---|---|---|
| III | 07/04/2026 | 19/04/2026 | Decreto 12.930, art. 2º, que remete ao Decreto 12.878, art. 2º, III |
| IV | 20/04/2026 | 30/04/2026 | Decreto 12.930, art. 2º, que remete ao Decreto 12.878, art. 2º, IV |
| V | 01/05/2026 | 15/05/2026 | Decreto 12.930, art. 2º, que remete ao Decreto 12.878, art. 2º, V |
| VI | 16/05/2026 | 31/05/2026 | Decreto 12.930, art. 2º, que remete ao Decreto 12.878, art. 2º, VI |

**A.3.3 MP 1.349, GLP: 7 períodos** (Decreto 12.930, art. 19, § 3º, redações dos Decretos 12.942 e 12.992)

| Nº | Início | Fim | Ato de definição |
|---|---|---|---|
| I | 01/04/2026 | 30/04/2026 | Decreto 12.930, art. 19, § 3º, I |
| II | 01/05/2026 | 15/05/2026 | Decreto 12.930, art. 19, § 3º, II |
| III | 16/05/2026 | 31/05/2026 | Decreto 12.930, art. 19, § 3º, III |
| IV | 01/06/2026 | 15/06/2026 | Decreto 12.930, art. 19, § 3º, IV |
| V | 16/06/2026 | 30/06/2026 | Decreto 12.930, art. 19, § 3º, V |
| VI | 01/07/2026 | 15/07/2026 | Decreto 12.930, art. 19, § 3º, VI |
| VII | 16/07/2026 | 31/07/2026 | Decreto 12.930, art. 19, § 3º, VII |

**A.3.4 MP 1.363, diesel: 14 períodos** (Decreto 12.995, art. 2º)

| Nº | Início | Fim | Ato de definição |
|---|---|---|---|
| I | 01/06/2026 | 15/06/2026 | Decreto 12.995, art. 2º, I |
| II | 16/06/2026 | 30/06/2026 | Decreto 12.995, art. 2º, II |
| III | 01/07/2026 | 15/07/2026 | Decreto 12.995, art. 2º, III |
| IV | 16/07/2026 | 31/07/2026 | Decreto 12.995, art. 2º, IV |
| V | 01/08/2026 | 15/08/2026 | Decreto 12.995, art. 2º, V |
| VI | 16/08/2026 | 31/08/2026 | Decreto 12.995, art. 2º, VI |
| VII | 01/09/2026 | 15/09/2026 | Decreto 12.995, art. 2º, VII |
| VIII | 16/09/2026 | 30/09/2026 | Decreto 12.995, art. 2º, VIII |
| IX | 01/10/2026 | 15/10/2026 | Decreto 12.995, art. 2º, IX |
| X | 16/10/2026 | 31/10/2026 | Decreto 12.995, art. 2º, X |
| XI | 01/11/2026 | 15/11/2026 | Decreto 12.995, art. 2º, XI |
| XII | 16/11/2026 | 30/11/2026 | Decreto 12.995, art. 2º, XII |
| XIII | 01/12/2026 | 15/12/2026 | Decreto 12.995, art. 2º, XIII |
| XIV | 16/12/2026 | 31/12/2026 | Decreto 12.995, art. 2º, XIV |

## A.4 `Cad_Combustivel_Programa_Tributo_Equivalente`: 5 linhas

Programa `SUBVENCAO-TRIBUTOS-MP-1358`; `Limita_Pagamento_Ao_Onus` = verdadeiro; `Fundamento_Legal` "MP 1.358, art. 1º, § 1º e § 3º"; vigência de 13/05/2026 a 31/12/9999.

| Combustível | Tributo (`Cad_Imposto`) | `Observacao` |
|---|---|---|
| `GASOLINA` | PIS | Gasolinas e suas correntes (art. 1º, § 1º, I) |
| `GASOLINA` | COFINS | Gasolinas e suas correntes (art. 1º, § 1º, I) |
| `GASOLINA` | `CIDE-COMBUSTIVEIS` | Gasolinas e suas correntes (art. 1º, § 1º, I) |
| `OLEO_DIESEL` | PIS | Óleo diesel de uso rodoviário (art. 1º, § 1º, II) |
| `OLEO_DIESEL` | COFINS | Óleo diesel de uso rodoviário (art. 1º, § 1º, II) |

## A.5 `Cad_Imposto_Exportacao_Aliquota`: 2 linhas

| NCM | `Descricao_Produto` | `Aliquota_Percentual` | Programa | `Pode_Ser_Reduzida_Por_Ato` | `Orgao_Que_Reduz` | Vigência | Artigo |
|---|---|---|---|---|---|---|---|
| 2709 | Óleos brutos de petróleo ou de minerais betuminosos | 12 | vazio | sim | Comitê-Executivo de Gestão da Câmara de Comércio Exterior | 12/03/2026 a 31/12/9999 | MP 1.340, arts. 10 e 11 |
| 2710.19.21 | Óleo diesel de uso rodoviário (redação da MP 1.349, de 07/04/2026) | 50 | `SUBVENCAO-DIESEL-MP-1340` | não | vazio | 12/03/2026 a 31/12/2026 (**leitura minha**) | MP 1.340, art. 12, redação da MP 1.349, art. 15 |

`Condicao_Vigencia` da segunda linha: "enquanto perdurar a subvenção econômica de que trata o art. 1º". Entre 12/03 e 06/04/2026 o art. 12 dizia só "óleo diesel", sem "de uso rodoviário"; a linha registra a redação vigente e o `Motivo_Vigencia` cita a mudança.

## A.6 `Cad_Imposto`: 2 linhas novas

| `Sigla` | `Nome` | `Esfera` | `Natureza` |
|---|---|---|---|
| `CIDE-COMBUSTIVEIS` | Contribuição de Intervenção no Domínio Econômico incidente sobre combustíveis | `federal` | `outro` |
| `IE` | Imposto sobre a Exportação | `federal` | `outro` |

## A.7 `Cad_Classe_Sistema`: 2 valores novos em `agente_cadeia_combustiveis`

`agente_comercio_exterior` (Agente de comércio exterior autorizado pela ANP) e `cooperativa_produtores_biocombustiveis` (Cooperativa de produtores de biocombustíveis).

# Anexo B. Cobertura: o que cada ato pede e onde está

| Ato e artigo | O que pede | Onde está |
|---|---|---|
| MP 1.340, art. 1º; Decreto 12.878, art. 1º | R$ 0,32/l, de 12/03 a 31/12/2026, para produtores, importadores e distribuidores que importam | `Cad_Combustivel_Programa_Valor`; `Cad_Participante_Autorizacao_Anp` (tipos `refinaria`, `importador`, `distribuidor`, `agente_comercio_exterior`) |
| MP 1.340, art. 1º-A; Decreto 12.930, art. 15 | R$ 0,80/l a mais, só produtores, 07/04 a 31/05 | `Papel_Beneficiario = produtor` |
| MP 1.340, art. 2º; MP 1.349, art. 5º; Decreto 12.930, art. 19 | Tetos de R$ 10 bi, R$ 4 bi e R$ 660 mi | `Limite_Total_Valor` |
| MP 1.340, art. 3º; MP 1.349, art. 6º; Decretos 12.878 e 12.930 (arts. 2º); Decreto 12.995, art. 2º | Períodos de apuração | `Cad_Combustivel_Programa_Periodo` |
| MP 1.340, art. 5º; MP 1.363, art. 3º; MP 1.391, art. 3º | Adesão por termo; efeito desde o 1º dia se entregue até o 5º ou o 10º dia útil; interrupção no período seguinte | `Cad_Participante_Adesao_Programa`; `Dia_Util_Limite_Efeito_Desde_Inicio` (efeito derivado) |
| MP 1.340, art. 6º e art. 7º; Decreto 12.878, arts. 3º, 7º e 8º | PR, PC e conta gráfica por base regional | `Tipo_Apoio = subvencao_por_preco_de_referencia`; `Codigo_Base_Regionalizada`; **o ERP não calcula** |
| Decreto 12.878, art. 9º; Decreto 12.995, art. 7º | Declaração em 5 dias úteis; pagamento; reapresentação | `Prazo_Declaracao_Dias_Uteis`; `Unidade_Prazo_Pagamento`; `Data_Reapresentacao`; requerimento por período |
| Decreto 12.995, art. 7º, § 5º, e art. 9º | Selic sobre o atraso e sobre a restituição | `Atualiza_Atraso_Pela_Selic`; `Valor_Atualizacao_Selic` |
| Decreto 12.995, art. 12 | Certidão de regularidade | `ID_Documento_Certidao_Regularidade` |
| Decreto 12.878, arts. 8º, § 2º, e 13 | Saldo devedor com a União | Q173-C6; sem campo |
| MP 1.340, art. 10; MP 1.349, art. 4º, § 1º | Importador de diesel para estado que aderiu, R$ 0,60 da União e R$ 0,60 do ente | `Condicao_Aplicacao`; valor de R$ 1,20 |
| MP 1.349, art. 16, parágrafo único | R$ 1,20 em acréscimo ao R$ 0,32 | Uma linha de item por programa (Q173-1) |
| MP 1.349, art. 10, § 3º; Decreto 12.930, art. 11 | Repasse do desconto pelo distribuidor, com média por litro na NF-e | `Exige_Repasse_Distribuidor`; entidades da seção 8 |
| Decreto 12.930, art. 20 | Informações do distribuidor à ANP a cada 14 dias | Relatório, sem campo (Q173-E5) |
| MP 1.349, art. 19; Decreto 12.930, art. 19 | GLP até R$ 850/t, entregas de 01/04 a 31/07 | `Unidade_Do_Valor = tonelada`; `Valor_E_Maximo` |
| MP 1.358, art. 1º | Subvenção equivalente a PIS, Cofins e Cide; pagamento limitado ao ônus | `subvencao_equivalente_a_tributo`; `Cad_Combustivel_Programa_Tributo_Equivalente`; `CIDE-COMBUSTIVEIS` |
| MP 1.363, arts. 1º a 5º; Decreto 12.995 | R$ 1,12/l, 14 períodos, adesão, aviso de 15 dias, desconto exato, frase na NF-e, 30 dias, Selic, interrupção das MPs anteriores | Programa, valor, período, `Texto_Modelo_Destaque`, `ID_Combustivel_Programa_Apoio_Interrompido` |
| MP 1.391, arts. 1º a 3º; Portaria MF 2.946 | Valor por ato, 30 dias prorrogáveis, aviso de 10 dias, R$ 2,12 por litro de diesel A | `Regra_Alteracao_Valor`; valor de 27/09 a 26/10/2026 |
| Decreto 13.119, arts. 1º a 5º | R$ 0,2519/l de etanol hidratado, 30 dias, aviso de 5 dias, carência de 15 | Programa e valor; `Dias_Carencia_Alteracao`; `cooperativa_produtores_biocombustiveis` |
| MP 1.340, arts. 10 a 12 | Imposto de exportação de 12% e de 50% | `Cad_Imposto_Exportacao_Aliquota`; `IE` em `Cad_Imposto` |
| MP 1.340, art. 6º, § 3º; MP 1.363, art. 2º | Desconto exato no preço de venda | `Exige_Desconto_No_Preco`; `Valor_Desconto_Concedido` e o aviso de diferença |
| Tratamento tributário e contábil da subvenção | Base de tributos, receita, ECF | **Fora** deste desenho (Q173-C1, C2, C5 e C6) |
| Continuidade em 2027 | Não achei | O desenho funciona sem programa vigente |
