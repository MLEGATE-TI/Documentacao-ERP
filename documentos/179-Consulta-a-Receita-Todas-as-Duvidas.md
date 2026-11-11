# Consulta à Receita Federal — Todas as Dúvidas, Reescritas — Documento 179

*Reescreve a consulta do documento 98 e reúne, num só lugar, **tudo o que o desenho do dicionário precisa que a Receita esclareça**: as nove perguntas da ECF que já existiam, mais as que surgiram depois (Y520, Refis, lucro presumido, EFD-ICMS/IPI e reforma tributária). Cada pergunta traz o texto pronto para colar, o que se pede de resposta e a leitura que o ERP adota enquanto a Receita não responde. **O envio é seu**: nada foi enviado à Receita, e este documento não altera o dicionário.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

São **26 perguntas** em quatro blocos, mais um anexo com o que **não** é da Receita:

| Bloco | Perguntas | Assunto | Canal sugerido |
|---|---|---|---|
| A | 1 a 10 | ECF: erros e lacunas da planilha das tabelas dinâmicas e do manual (leiaute 12) | Fale Conosco, Empresa, SPED, ECF |
| B | 11 a 16 | ECF: Y520, Refis, lucro presumido e regime de caixa | Fale Conosco, Empresa, SPED, ECF (as 15 e 16 podem pedir outro canal; ver a seção 2) |
| C | 17 a 20 | EFD-ICMS/IPI: tabelas do validador, Guia Prático e registro 1601 | Fale Conosco, Empresa, SPED, EFD ICMS/IPI (confira o nome na página) |
| D | 21 a 26 | Reforma tributária: transição de 2026, cadastro, redução de 0,1 ponto e bônus de adimplência da CSLL | Canal da Receita para a reforma tributária (confira na página) |

**Mudanças em relação ao documento 98.**

1. As perguntas **1 a 9** seguem como estavam, com o texto enxugado (sem as tabelas de evidência, que ficam no documento 98).
2. A **pergunta 10** (divergências herdadas das fórmulas, da Q139-1) entra **só como rascunho**: o texto das fórmulas está na planilha do leiaute 12, que **não está no meu ambiente**. Falta a planilha para fechá-la (Q179-3).
3. As perguntas **11 a 26** são novas. Vêm das listas do documento 38: as que o contador deixou em aberto e que só a Receita responde, e as que a conferência das tabelas do validador e do FAQ deixou sem fonte.
4. Cada pergunta traz **a leitura adotada**: o que o ERP faz até a resposta chegar. Nenhuma delas muda campo do dicionário; a resposta só ajusta parâmetro com vigência ou regra do Motor.

**O que não vai para a Receita** (SEFAZ de cada UF, ENCAT, Comitê Gestor do IBS, contador) está no anexo, seção 5.

# 2. Como enviar

- **Canal da ECF:** Fale Conosco da Receita, área Empresa, SPED, ECF (https://www.gov.br/receitafederal/pt-br/canais_atendimento/fale-conosco/empresa/sped/ecf). O formulário costuma pedir identificação do contribuinte e um assunto; confira o nome exato das opções na hora do envio.
- **Uma pergunta por protocolo** funciona melhor: a resposta vem mais objetiva e cada uma pode ser acompanhada separadamente. As perguntas 1, 2 e 3 também podem ir juntas (mesma planilha).
- **Peça sempre o fundamento** (artigo da norma, ou previsão de correção da planilha com a data), para registrar a vigência no ERP.
- **Orientação, e não consulta formal.** Pelo que conheço, o Fale Conosco dá orientação e não substitui a consulta formal sobre a interpretação da legislação tributária, que tem rito próprio. As perguntas de **leiaute, validação e preenchimento** (blocos A, B1 a B3 e C) são do tipo que o Fale Conosco responde. As de **interpretação da lei** (15, 16 e o bloco D) talvez peçam consulta formal; **o contador decide o canal** (Q179-2). Não conferi o rito da consulta formal nesta sessão.
- **Anexe** a linha da planilha ou o trecho do manual, se o formulário permitir. Cada pergunta já traz a fórmula ou o trecho transcrito, então o texto vale sozinho.

**Ordem de envio recomendada** (da que mais bloqueia o cálculo à que menos bloqueia): 3, 1, 2, 7, 4, 5, 6, 8, 9; depois os blocos B, C e D, na ordem em que aparecem.

# 3. Perguntas

## Bloco A — ECF: planilha das tabelas dinâmicas e manual (leiaute 12)

*Fontes: Manual de Orientação do Leiaute 12 da ECF (atualização de julho/2026, Anexo ao Ato Declaratório Executivo Cofis nº 02/2026, 622 páginas) e planilha das tabelas dinâmicas (versão de 24/09/2026). As páginas citadas são as do manual. Competência da Cofis (IN RFB 2.004/2021, art. 4º).*

### Pergunta 1 — Referência `M(344)` e `M(170)` nas linhas M350A 171 e M350R 345

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Bloqueia o cálculo:** sim, a base da CSLL antes da compensação de base negativa.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as linhas 171 do M350A e 345 do M350R têm as fórmulas `M350(169) - M350(170) + M(344)` e `M350(343) - M350(344) + M(170)`. As referências `M(344)` e `M(170)` estão sem o número da tabela, diferente de todas as outras referências do M350. Nas linhas equivalentes do M300 (M300A 171 e M300R 345) a referência vem completa, `M300(344)` e `M300(170)`. Pergunto: (1) a intenção é `M350(344)` e `M350(170)`, ou seja, a compensação da base negativa do próprio período da outra atividade (rural e geral), espelhando o M300? (2) Se for, a planilha será corrigida e em qual versão? (3) Enquanto isso, o PVA da ECF calcula essas linhas com qual referência?

**Resposta pedida:** confirmar a referência correta e a data da correção da planilha.

**Leitura adotada:** `M350(344)` e `M350(170)`, espelhando o M300.

### Pergunta 2 — Fórmulas com `FIM_SE` ou parênteses que não fecham (N660 3, N600 24 e 36, P200 25210 a 25250, P300 9)

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Bloqueia o cálculo:** sim, a CSLL apurada da estimativa e as linhas do adicional da LC 224/2025.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), a fórmula da linha 3 do registro N660 ("CSLL Apurada") tem três `SE` e apenas dois `FIM_SE`: `SE (N660(2) <= 0) ENTAO 0 SENAO SE (0020.IND_ALIQ_CSLL() = "1") ENTAO N660(2) * 0,09 SENAO SE (0020.IND_ALIQ_CSLL() = "3") ENTAO N660(2) * 0,20 SENAO N660(2) * 0,15 FIM_SE FIM_SE`. É a única com blocos SE/FIM_SE desbalanceados (a linha 2 do N670 tem três e três). Conferindo a planilha também achamos parênteses que não fecham: N600 24 e N600 36 (um `)` a mais no final), P200 25210 a 25250 (por exemplo `(P200(2)/P200("25.110"))*P200("25.200"))*0,016 *0,1`, com um `)` a mais) e P300 9 (a condição do `SE` está sem parênteses e a expressão tem 25 `(` e 23 `)`). Pergunto: (1) no N660 3 falta um `FIM_SE` no final, sem outra mudança de lógica? (2) Nas demais linhas, a intenção é remover o `)` a mais (N600 24 e 36), abrir o `(` que falta antes de `P200(2)/...` (P200 25210 a 25250) e fechar os parênteses do P300 9? Podem indicar a fórmula correta de cada uma? (3) A planilha será corrigida e em qual versão?

**Resposta pedida:** confirmar que no N660 3 falta só o `FIM_SE` e indicar a fórmula correta das demais linhas.

**Leitura adotada:** falta um `FIM_SE` no final do N660 3, sem outra mudança; nas outras linhas o ERP não carrega a fórmula sozinho e pede revisão do contador.

### Pergunta 3 — Fórmulas da CSLL que não tratam as alíquotas 7 e 8 (12% e 17,5%)

**Assunto sugerido:** Leiautes (tabelas dinâmicas) e Alíquota da CSLL. **Bloqueia o cálculo:** sim, para clientes dos segmentos que mudaram de alíquota.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as fórmulas da CSLL nas linhas N660 3, N670 2, P500 2, T181 6 e U182 2 só tratam os valores de IND_ALIQ_CSLL 1, 3 e 5. As orientações das próprias linhas (N670 2 e T181 6, por exemplo) já listam os códigos 7 (9%/12%) e 8 (15%/17,5%), criados pela LC 224/2025 conforme o manual (item de alterações do leiaute, p. 620), mas a fórmula não tem ramo para 7 nem 8: o valor 7 cai em 15% (N660 3, N670 2 e P500 2) ou em 15%/20% (T181 6 e U182 2), e o 8 também. Já a linha P500 18300 (bloco LC 224/2025) trata o 7 com 9% em T01/2026 e 12% depois, e o 8 com 15% em T01/2026 e 17,5% depois. Pergunto: (1) qual a fórmula correta dessas cinco linhas para os anos-calendário 2026 e 2027, com os códigos 7 e 8, e a regra da P500 18300 (9% ou 15% só em T01/2026) vale também para a estimativa mensal e a apuração anual? (2) Qual o período exato em que passa a valer o 12% (9% até 31/03/2026 e 12% de 01/04/2026, como entendemos) e como a ECF reparte o ano nos meses (A01 a A12) e trimestres (T01 a T04)? (3) Nas linhas T181 6 (arbitrado) e U182 2 (imunes e isentas), a condição `0000.DT_INI() >= "2021-01-01"` não tem data final; para 2022 em diante, uma PJ com código 4 (15%) deve mesmo ter 20% nos trimestres T03 e T04? Se não, a planilha será corrigida e em qual versão? (4) Para 2028 em diante, quais códigos de IND_ALIQ_CSLL valem para cada segmento da Lei 7.689, art. 3º?

**Resposta pedida:** a fórmula correta (ou a previsão de correção e a versão da planilha), mais o início exato do 12% e do 17,5% no ano.

**Leitura adotada:** o ERP **para e avisa** nas cinco linhas quando o contador escolhe 7 ou 8, e espera a resposta do contador. Não calcula com 15% nem com 20%.

### Pergunta 4 — Lista de valores válidos de `IND_ALIQ_CSLL` contra a regra de validação e o texto do campo

**Assunto sugerido:** Leiautes e Mensagens de erro do PVA. **Bloqueia o cálculo:** parcial; o ERP avisa antes de gerar.

**Texto para colar:**

> Prezados, no manual da ECF (leiaute 12, atualização de julho/2026), registro 0020, campo 2 (IND_ALIQ_CSLL), a coluna de valores válidos traz [1;3;4] (p. 81), mas o texto do campo descreve também 7 (9%-12%) e 8 (15%-17,5%), e o quadro de alterações do leiaute (p. 620) diz que o campo criou "duas novas alíquotas transitórias – 12% e 17,5% – para os anos de 2026/27, conforme LC 224/25". A regra REGRA_PREENCHIMENTO_IND_ALIQ_CSSL (p. 92) verifica, para ano da ECF maior ou igual a 2019, se o campo é igual a "1" ou "4", o que gera erro para 3, 7 e 8. Pergunto: (1) quais valores o PVA aceita hoje para cada ano-calendário (2025, 2026, 2027 e 2028 em diante)? (2) Uma instituição com alíquota de 20% (código 3) e uma PJ com a alíquota transitória de 12% ou 17,5% (códigos 7 e 8) devem preencher qual código? (3) A lista de valores válidos e a regra da p. 92 serão atualizadas e em qual versão do leiaute ou do PVA?

**Resposta pedida:** a tabela de valores aceitos por ano-calendário e a previsão de atualização.

**Leitura adotada:** o domínio `indicador_aliquota_csll_ecf` mantém 1, 3, 4, 7 e 8, com a vigência de cada valor como parâmetro e a situação "a confirmar".

### Pergunta 5 — Funções usadas nas fórmulas e sem definição

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Bloqueia o cálculo:** parcial; a leitura foi validada em dois arquivos reais de 2025.

**Texto para colar:**

> Prezados, as fórmulas da planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026) usam as funções T_DRE, DEBITO, CREDITO, MESES_PERIODO, BAL_RED, PERIODO_ATUAL e PERIODO_ANTERIOR, que não encontramos definidas no manual de orientação (atualização de julho/2026) nem em outro documento publicado. Pergunto: (1) existe um documento que descreva essas funções (parâmetros, sinal do retorno, tratamento de saldo zero)? (2) Pela nossa leitura, DEBITO(x) devolve x se x for positivo e 0 caso contrário; CREDITO(x) devolve o módulo do valor se for crédito e 0 caso contrário; T_DRE(x) devolve o saldo no sinal da DRE (débito positivo, crédito negativo); MESES_PERIODO() devolve 3 no trimestre, 1 na estimativa mensal e 12 no ano-calendário; BAL_RED(p) devolve o campo 0010.MES_BAL_RED do mês p. Está correto? (3) Como MESES_PERIODO() se comporta em apuração anual com suspensão ou redução, em início ou encerramento de atividade e em fusão, cisão e incorporação? (4) Em SOMA(N620("20.01";"A01":PERIODO_ANTERIOR())), o intervalo termina no mês anterior ao mês em cálculo, sem incluí-lo?

**Resposta pedida:** a definição de cada função, ou a confirmação das leituras acima e o tratamento dos casos de borda.

**Leitura adotada:** as leituras do próprio texto, testadas contra dois arquivos reais de ECF de 2025 (documento 93, seção 9).

### Pergunta 6 — Regras de obrigatoriedade do registro Y520 que se contradizem

**Assunto sugerido:** Mensagens de erro do PVA e Leiautes. **Bloqueia o cálculo:** não; afeta a geração do arquivo.

**Texto para colar:**

> Prezados, no manual da ECF (leiaute 12, atualização de julho/2026), as regras de validação do registro Y520 (p. 563) dizem: REGRA_Y520_OBRIGATORIO_R: quando 0020.IND_REC_EXT = "S", deve existir Y520.TIP_EXT = "R" e não pode existir Y520.TIP_EXT = "P"; REGRA_Y520_OBRIGATORIO_P: quando 0020.IND_PGTO_EXT = "S", não pode existir Y520.TIP_EXT = "R" e deve existir Y520.TIP_EXT = "P". Para a PJ que recebeu e também pagou valores do exterior no mesmo ano (as duas indicações "S"), as duas regras não podem ser cumpridas ao mesmo tempo. Pergunto: (1) qual o preenchimento correto do Y520 e dos campos IND_REC_EXT e IND_PGTO_EXT nesse caso? (2) A redação das regras será corrigida (por exemplo, retirando o "não existe" do outro tipo) e em qual versão do PVA? (3) A p. 562 diz que o registro é "habilitado" para quem recebeu ou pagou e as regras o tratam como obrigatório com erro: qual vale? (4) Como o PVA se comporta hoje com os dois indicadores em "S"? (5) Ainda no Y520, a regra REGRA_FORMA_PAGTO_INVALIDA (p. 564) diz que gera erro quando TIP_EXT = "P" e FORMA é diferente de "4", ou quando TIP_EXT = "R" e FORMA é diferente de "5", mas o quadro do campo FORMA (p. 563) diz que a forma 4 só vale para "R" e a 5 só para "P", e o exemplo do manual (p. 564) é um "R" com forma 1 (câmbio). O texto correto da regra é "igual a" em vez de "diferente de" (erro quando P usa a forma 4 ou R usa a forma 5)? Em qual versão será corrigida?

**Resposta pedida:** a forma correta de informar recebimento e pagamento no mesmo ano, o texto correto da regra `REGRA_FORMA_PAGTO_INVALIDA` e o comportamento atual do PVA.

**Leitura adotada:** o ERP gera os registros `R` e `P` que existirem nos dados, avisa o contador quando os dois indicadores estão em "S" e não decide sozinho. Na forma de pagamento segue o quadro do campo (4 só para recebimento, 5 só para pagamento) e o exemplo do manual, não a letra da regra.

### Pergunta 7 — Percentual `0,348` em vez de `0,384` na linha P500 18200

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Bloqueia o cálculo:** sim, o tributo pago a maior do lucro presumido na transição da LC 224/2025.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), a linha 18200 do registro P500 ("Base de Cálculo Adicionado a Maior no Trimestre") usa, no terceiro termo, `((P400(5)/P400("20.110"))*P500("18.100"))*0,348 *0,1`. Os outros termos usam 0,12 e 0,32, e as linhas equivalentes (P400 20230 e P200 25250) usam 0,384 para a faixa de 38,4%. Pergunto: (1) o percentual correto é 0,384 (troca de dígitos) ou 0,348 é intencional? (2) Se for erro, a planilha será corrigida e em qual versão? (3) O PVA da ECF já calcula com 0,384?

**Resposta pedida:** confirmar o percentual e a data da correção.

**Leitura adotada:** 0,384, com aviso ao contador.

### Pergunta 8 — P130: linhas 74 a 77 (demais atividades), receita de 38,4% sem linha e orientação da linha 6 citando `P130/68`

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Situação:** o ponto 3 você aprovou (Q134-6); os pontos 1 e 2 aguardam a Q132-5 (se não os aprovar, apague-os do texto antes de enviar). **Bloqueia o cálculo:** não; o ERP avisa.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), registro P130 (Demonstração das Receitas Incentivadas do Lucro Presumido), observamos três pontos. (1) As linhas 74 a 77 pertencem ao bloco "DEMAIS ATIVIDADES" (rótulo da linha 73, e a fórmula da linha 78 as trata como lucro presumido das demais atividades), mas a descrição das quatro linhas diz "beneficiado com a redução do imposto de renda", e a regra de validação do X280 que soma as receitas de reduções (REGRA_RECEITA_REDUCOES) soma as linhas 74 a 77 como receita de reduções. As linhas 74 a 77 são a receita sem benefício (demais atividades), como entendemos, e a descrição e a regra do X280 serão corrigidas? (2) O P130 não tem linha para a receita sujeita ao percentual de 38,4%, mas o P200 linha 10 inclui P200(9)*0,384, e a orientação das linhas P130/6, 15, 24, 33, 42, 51, 60, 69 e 78 diz que a soma dos lucros presumidos deve coincidir com o P200/10. Como deve preencher o P130 a pessoa jurídica com receita a 38,4% (Empresa Simples de Crédito, LC 167/2019) que tem isenção ou redução do imposto? (3) A orientação da linha P130/6 cita "P130/68" na lista de linhas cuja soma deve coincidir com o P200/10, enquanto as orientações das outras oito linhas (15, 24, 33, 42, 51, 60, 69 e 78) citam "P130/78"; a linha 68 é a receita sujeita a 32% do bloco de reinvestimento, e não um lucro presumido. É erro de digitação, e o correto é P130/78? A planilha será corrigida e em qual versão? Pedimos, para os três pontos, a resposta com o fundamento (artigo da norma ou previsão de correção, com a data).

**Resposta pedida:** a natureza das linhas 74 a 77, como preencher o P130 com receita de 38,4% e a correção da orientação da linha 6, com a versão.

**Leitura adotada:** as linhas 74 a 77 são receita sem benefício; a orientação da linha 6 vale com `P130/78`; a receita de 38,4% fica sem linha no P130, com aviso ao contador.

### Pergunta 9 — P200 26 e P400 21 (versões de 2026): o teste do `SE` não inclui o adicional da LC 224/2025

**Assunto sugerido:** Leiautes (tabelas dinâmicas) e LC 224/2025. **Situação:** texto aprovado por você (Q135-6). **Bloqueia o cálculo:** não; o ERP segue a fórmula publicada e avisa.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as versões "a partir de 01/01/2026" das linhas P200 26 (base de cálculo do imposto sobre o lucro presumido) e P400 21 (base de cálculo da CSLL) testam, no `SE`, a base sem o adicional da LC 224/2025 e somam o adicional só dentro do `ENTAO`. P200 26: `SE (SOMA(P200(10:21)) - (P200(22) + P200(23) + P200(24) + P200(25) + P200("25.01") + P200("25.02")) > 0) ENTAO (SOMA(P200(10:21)) - (P200(22) + P200(23) + P200(24) + P200(25) + P200("25.01") + P200("25.02")) + SOMA(P200("25.210":"25.250"))) SENAO 0 FIM_SE`. P400 21: `SE (SOMA(P400(6:17)) - SOMA(P400(18:20)) > 0) ENTAO (SOMA(P400(6:17)) + SOMA(P400("20.210":"20.230")) - SOMA(P400(18:20))) SENAO 0 FIM_SE`. Com isso, se a base sem o adicional for zero ou negativa, o resultado é 0 e o adicional positivo não é somado (por exemplo, na P200 26: soma das linhas 10 a 21 = 10.000,00, deduções = 10.500,00 e adicional = 800,00 dão 0; se o teste incluísse o adicional, a base seria 300,00). Pergunto: (1) o teste do `SE` sem o adicional é intencional, de modo que o adicional só entra quando a base sem ele é positiva? (2) Se for intencional, qual o fundamento (artigo da LC 224/2025 ou da regulamentação)? Se não for, a planilha será corrigida e em qual versão? (3) Qual dessas leituras o PVA da ECF aplica hoje na validação da P200 26 e da P400 21?

**Resposta pedida:** se o teste é intencional, o fundamento e como o PVA valida a linha; ou a previsão de correção da planilha, com a versão.

**Leitura adotada:** a fórmula **como publicada** (o adicional é descartado quando a base sem ele não é positiva), com aviso ao contador quando o caso ocorrer.

### Pergunta 10 — Divergências herdadas das fórmulas entre as planilhas de 2025 e 2026 (RASCUNHO: falta a planilha)

**Assunto sugerido:** Leiautes (tabelas dinâmicas). **Situação:** **rascunho incompleto**; não enviar até a Q179-3. Esta pergunta nasce da Q139-1 (documento 139, seção 4).

**O que já sei** (documentos 136 e 139): das 372 fórmulas da planilha de 2025, 364 são iguais às da carga do ERP e 8 diferem. Das sete divergências que o documento 136 apontou, **cinco já estavam na planilha de 2025** (N660 5 a 9, N610 3, N660 12.01, N670 12 e M350R 267), a **N670 21 mudou em 2026** (o ERP a lê como `"20.99"`, com aviso) e a **N610 75.60 é linha nova**. As versões "até 31/12/2025" das N620 18 e 19 e da N630A 18 diferem entre as planilhas de 2025 e 2026 (leitura minha: mudança de regra entre 2024 e 2025).

**O que falta:** a fórmula exata de cada linha, nos dois anos, e **o que a leitura do ERP considera errado** em cada uma. Esse texto vem da planilha, que não está no meu ambiente. Com ela, escrevo a pergunta no formato das anteriores (fórmula transcrita, o que observamos, o que perguntamos).

**Texto para colar:**

> *(a completar com as fórmulas da planilha)* Prezados, comparando as planilhas das tabelas dinâmicas da ECF dos leiautes de 2025 e de 2026 (versão de 24/09/2026), as linhas N660 5 a 9, N610 3, N660 12.01, N670 12 e M350R 267 trazem a mesma fórmula nos dois anos, que nos parece inconsistente com [a descrição da linha / o manual]; a N670 21 mudou em 2026; a N610 75.60 é nova; e as versões anteriores a 31/12/2025 das N620 18 e 19 e da N630A 18 diferem entre as duas planilhas. Pergunto, para cada linha: [fórmula correta / intenção / versão da correção].

**Leitura adotada:** o motor segue a fórmula como publicada e avisa o contador (Q139-2).

## Bloco B — ECF: Y520, Refis, lucro presumido e regime de caixa

*Perguntas novas. Vêm do documento 38 (seção 2.2), onde o contador as tinha como pendência, mas a resposta depende de como a Receita e o PVA tratam o caso. As perguntas 11 a 14 são de preenchimento e validação.*

### Pergunta 11 — Y520: estorno ou devolução em ano diferente do pagamento (`VL_PERIODO` negativo)

**Assunto sugerido:** Leiautes e Mensagens de erro do PVA. **Origem:** Q100-14.

**Texto para colar:**

> Prezados, no registro Y520 da ECF (leiaute 12, manual de julho/2026), quando há estorno ou devolução de um pagamento ou recebimento do exterior em ano-calendário diferente do original, o valor líquido da chave do Y520 do ano do estorno pode ficar negativo. O manual não diz se o campo VL_PERIODO aceita valor negativo. Pergunto: (1) o campo aceita valor negativo, e o PVA valida? (2) Se não aceita, como informar o estorno ocorrido em ano posterior: reduzindo o valor do ano do pagamento original (por ECF retificadora), informando zero, ou de outra forma? (3) Há fundamento (artigo ou orientação) para registrar?

**Resposta pedida:** a forma de informar o estorno em ano diferente e se o campo aceita valor negativo.

**Leitura adotada:** o estorno reduz o pagamento; o ERP avisa quando a soma da chave ficar negativa, sem bloquear.

### Pergunta 12 — Y520: informar mais do que o manual exige

**Assunto sugerido:** Leiautes (Y520). **Origem:** Q110-11.

**Texto para colar:**

> Prezados, no registro Y520 da ECF (leiaute 12, manual de julho/2026), o manual condiciona a informação do cartão e da moeda, e a marcação do indicador do registro 0020 (IND_REC_EXT e IND_PGTO_EXT), ao valor de R$ 120.000,00. Nosso sistema informa todas as operações com o exterior, de qualquer valor, e marca o indicador "S" sempre que há linha no Y520. O PVA aceita o arquivo. Pergunto: (1) informar operações abaixo do corte, com cartão e moeda, é aceito e não traz consequência (malha, intimação, inconsistência)? (2) A marcação do indicador "S" com todas as operações, e não só as acima do corte, está correta? (3) O corte de R$ 120.000,00 é por operação, por chave do Y520 ou por total do ano?

**Resposta pedida:** confirmar que informar a mais é aceito e como o corte se aplica.

**Leitura adotada:** o ERP informa tudo (decisão sua de 26/10/2026); o corte volta como parâmetro se o contador não concordar.

### Pergunta 13 — Y520: encontro de contas com não residente

**Assunto sugerido:** Leiautes (Y520). **Origem:** Q111-10.

**Texto para colar:**

> Prezados, no registro Y520 da ECF (leiaute 12, manual de julho/2026), quando uma obrigação com pessoa não residente é extinta por compensação (encontro de contas entre um título a pagar e outro a receber do mesmo não residente), sem transferência de recursos, pergunto: (1) a operação entra no Y520 pelo valor integral de cada operação (o pagamento e o recebimento compensados)? (2) Qual FORMA (1 a 6) deve ser informada, já que a tabela do campo FORMA não prevê compensação? (3) A compensação entre títulos de moedas diferentes (moeda de paridade) altera a resposta?

**Resposta pedida:** o tratamento no Y520 do encontro de contas e a FORMA a usar.

**Leitura adotada:** valor integral de cada operação; a FORMA é escolhida pelo usuário na baixa, sem padrão.

### Pergunta 14 — Refis: trimestre de ingresso, ano da exclusão e Y680

**Assunto sugerido:** Leiautes (Refis, 0010 e Y680). **Origem:** Q128-5 e documentos 128 e 132.

**Texto para colar:**

> Prezados, na ECF (leiaute 12, manual de julho/2026), para a pessoa jurídica optante do Refis (0010.OPT_REFIS) no lucro presumido, o manual não esclarece três pontos. (1) Ingresso no meio do trimestre: o trimestre é tratado como de Refis quando a empresa foi optante em algum dia dele, ou só quando foi optante no trimestre inteiro? (2) Ano da exclusão: a ECF do ano em que a empresa é excluída do Refis pode ficar toda no lucro presumido, ou a exclusão, com apuração pelo lucro real no trimestre seguinte, exige a forma de tributação 3 do manual? Como fica o preenchimento de 0010.OPT_REFIS nesse ano? (3) Como o Y680 trata o mês da adesão e o mês da exclusão (esses meses entram na demonstração)?

**Resposta pedida:** a regra de cada ponto, com o fundamento.

**Leitura adotada:** o trimestre é de Refis quando a empresa foi optante em algum dia dele (documento 128); no ano da exclusão a ECF fica toda no presumido, com aviso e orientação para o ano seguinte (regra sua: o regime não muda no meio do ano).

### Pergunta 15 — Lucro presumido: P130, P230, P300 9 e X280

**Assunto sugerido:** Leiautes (tabelas dinâmicas) e Imposto de Renda da Pessoa Jurídica. **Origem:** documentos 125 (seção 6) e 132. **Não repete** a pergunta 8: aqui é a condição de uso e a regra de redução.

**Texto para colar:**

> Prezados, sobre o lucro presumido na ECF (leiaute 12, manual de julho/2026, planilha de 24/09/2026), perguntamos: (1) P130 e P230: a condição para preencher esses registros é a pessoa jurídica ser optante do Refis (`IND_RED_ISEN`/isenção ou redução), ou há outra hipótese de uso? (2) Como informar no P130 os percentuais majorados do lucro presumido pela LC 224/2025 e o percentual de 38,4%? (3) A redução por reinvestimento do P300 linha 9 ainda se aplica? A orientação da linha fala em períodos até 2013. (4) A pessoa jurídica no lucro presumido tem direito à redução de 75% do IRPJ da Sudam e da Sudene? Encontramos orientação de consultoria dizendo que o presumido está excluído do benefício, mas a planilha traz P130 e P230. (5) X280: como a Receita confere as reduções do presumido no X280? O manual só traz a conferência da isenção com a P230 linha 6; as demais reduções (as que o P130 e o P300 informam) têm regra de conferência?

**Resposta pedida:** a regra de cada ponto, com o fundamento (artigo da norma ou orientação do manual).

**Leitura adotada:** o desenho segue o P130 como publicado; o ERP não inventa conferência no X280.

### Pergunta 16 — Regime de caixa no lucro presumido (IN RFB 1.700/2017)

**Assunto sugerido:** Imposto de Renda da Pessoa Jurídica (interpretação). **Origem:** documentos 127 e 128 (seção 4). **Pode exigir consulta formal** (seção 2).

**Texto para colar:**

> Prezados, no lucro presumido com opção pelo regime de caixa (IN RFB 1.700/2017, arts. 214, 215, 223 e 224 e 152 a 155), perguntamos: (1) Qual é a data do recebimento que reconhece a receita: a do pagamento pelo cliente ou a do crédito na conta da empresa? (2) Quais tipos de baixa contam como recebimento: o encontro de contas (compensação) e o recebimento por cartão contam, e em qual data? (3) Retenções na fonte, juros e multa recebidos, e valores em moeda estrangeira: como entram no caixa? (4) Na entrega do bem ou do serviço antes do faturamento (art. 223, § 2º, "o que primeiro ocorrer"), a receita é reconhecida na entrega mesmo sem recebimento ou nota? (5) A versão consolidada da IN (com o art. 223-A e as alterações posteriores) mudou algum desses pontos? (6) Qual é a regra de janeiro e da DCTF para a variação cambial no lucro presumido?

**Resposta pedida:** a resposta de cada ponto, com o artigo.

**Leitura adotada:** o ERP segue o desenho do documento 127 como proposta; na mudança de critério ele só indica o que deveria ser ajustado e o usuário confirma (Q127-4).

## Bloco C — EFD-ICMS/IPI

*Perguntas novas, da conferência das 197 tabelas do validador (documento 172), do Guia Prático v3.2.4 (documentos 167 e 175) e do FAQ v7.8 (documento 176). Só entraram aqui as que a Receita (SPED) responde; as que dependem da SEFAZ de cada UF estão no anexo.*

### Pergunta 17 — Tabelas do validador: ajustes, benefícios, tabela 5.7 e IPI

**Assunto sugerido:** Leiautes e Tabelas externas (EFD ICMS/IPI). **Origem:** Q172-C2, C3, C5 e C7.

**Texto para colar:**

> Prezados, conferindo as tabelas do validador da EFD ICMS/IPI (arquivos SPEDFISCAL de todas as UFs, baixados em novembro de 2026) com o Guia Prático v3.2.4, perguntamos: (1) Nos 10.626 códigos de ajuste de UF da tabela 5.1.1, o 3º caractere vai de 0 a 3 (apuração própria, ST, DIFAL e FCP) e o 4º de 0 a 5 e 9 (tipo do ajuste). Em qual registro e campo da EFD se informa a subapuração, e o 4º caractere tem relação com ela? Encontramos uma indicação de que ele iria "de 3 a 8", que não bate com as tabelas. (2) O validador traz o catálogo AJ_BENEF_INCENTIVO (3.383 códigos, UF mais 8 dígitos), que o Guia não numera. Em qual registro e campo ele é informado, e qual a relação com a tabela 5.1.1? (3) O campo COD_MOT_REST_COMPET do registro 1255 usa a mesma tabela 5.7 de COD_MOT_REST_COMPL_ST? Só sete UFs (MG, MS, PA, RJ, RO, RS e SE) publicam essa tabela no validador: nas demais, como o contribuinte preenche o motivo? (4) As tabelas de IPI do validador (CL_ENQ_IPI, SELO_CONT_IPI, CLASS_CONTRIB_IPI e ENQ_LEGAL_IPI, esta última sem linhas) são usadas em quais registros e campos? Em particular, o CL_ENQ do C178 e o COD_ENQ do C170 usam quais delas?

**Resposta pedida:** o registro e o campo de cada tabela, e o tratamento das UFs sem tabela.

**Leitura adotada:** `Indicador_Subapuracao` sem mudança; o AJ_BENEF_INCENTIVO fica como catálogo, sem ligação ao ajuste da apuração (só por pessoa); a 5.7 só para as 7 UFs que a publicam, com aviso nas demais; os domínios de IPI ficam como catálogo, sem uso; o COD_ENQ do C170 sai sempre vazio.

### Pergunta 18 — Como as tabelas do validador chegam e como o PVA as trata

**Assunto sugerido:** Tabelas externas e Validador (PVA) da EFD ICMS/IPI. **Origem:** Q172-E5, Q172-4 e Q172-2.

**Texto para colar:**

> Prezados, para manter atualizadas as tabelas por UF da EFD ICMS/IPI no nosso sistema, perguntamos: (1) Como as tabelas estaduais chegam ao contribuinte e ao PVA (atualização do próprio PVA, pacote no portal do SPED, outro meio)? Existe um endereço oficial para baixar cada arquivo (nome SPEDFISCAL, UF e tabela) com o número da versão? (2) O validador não traz tabelas de Roraima. Isso significa que RR não publica as tabelas, ou que elas estão em outro pacote? Como o contribuinte de RR preenche os códigos? (3) Cerca de 1.065 linhas das versões mais novas têm vigência de um dia (início igual ao fim). O PVA valida essas linhas normalmente, ou trata como erro de cadastro da UF? (4) Quando a versão nova de uma tabela traz o mesmo código com outro texto, a versão antiga continua válida para períodos já escriturados?

**Resposta pedida:** o canal oficial de atualização e o comportamento do PVA nos casos acima.

**Leitura adotada:** a carga é manual por arquivo (a versão mais nova substitui a anterior e só fecha datas ou acrescenta códigos); UF sem tabela: o ERP avisa e pede o código; vigência de um dia carrega como veio, com aviso.

### Pergunta 19 — Guia Prático: observações, DCTA, C105, 1200 e 4.4.6

**Assunto sugerido:** Leiautes (EFD ICMS/IPI) e Guia Prático. **Origem:** Q175-C2, C3, C4, C5, C6 e C8.

**Texto para colar:**

> Prezados, sobre o Guia Prático da EFD ICMS/IPI v3.2.4 (30/07/2026), perguntamos: (1) COD_OBS nos registros analíticos (C190, C320, C390, C590, C790, C850, C890, D190 e os de bilhete e de Redução Z): informa-se uma observação por combinação de CST, CFOP e alíquota, ou uma por documento? (2) DCTA (registro 1800): a diferença apurada (VL_DIF) é o valor do estorno de crédito (E111) da apuração? (3) C130: os valores de IRRF e de contribuição previdenciária são os destacados no documento, sem recálculo pelo declarante? (4) C105: a UF do recolhimento do ICMS-ST é a UF de consumo do item ou a do local de retirada, e só no leasing ela é informada pelo declarante? (5) Registro 1200: o código da tabela 5.1.1 é obrigatório em todo crédito controlado fora da apuração, e o tipo "CRED_RECEB" corresponde à transferência de crédito recebida? (6) Tabela 4.4.6 (totalizadores parciais da Redução Z): o PVA valida o código do C420 contra o padrão da tabela e a alíquota do C490?

**Resposta pedida:** a resposta de cada ponto, com a página do Guia ou o artigo do Ato COTEPE.

**Leitura adotada:** uma observação por combinação de CST, CFOP e alíquota; a diferença do DCTA vira o estorno de crédito; C130 e C112 "tal como emitido"; o Motor copia a UF do C105 do recolhimento do ICMS-ST; o código da 5.1.1 é obrigatório, com aviso; o aviso do código da 4.4.6 é só aviso.

### Pergunta 20 — Registro 1601: UFs sem resposta, cartão parcelado, estabelecimento que informa e PR

**Assunto sugerido:** Leiautes (EFD ICMS/IPI, registro 1601) e FAQ. **Origem:** Q177-C1, Q176-11 e Q176-C8.

**Texto para colar:**

> Prezados, o FAQ da EFD ICMS/IPI (v7.8, item 17.6.1) responde sobre o registro 1601 (instrumentos de pagamento) para AL, CE, PB, RN, MG e SC, e diz que o PR dispensa algumas empresas. Perguntamos: (1) Para as demais UFs que exigem o 1601, o cartão de crédito parcelado é informado pelo valor total na data da autorização, sem as parcelas (como respondem AL, CE, PB e RN), ou parcela a parcela pela data do crédito? (2) Existe lista oficial das UFs que exigem o 1601 e da regra de reconhecimento de cada uma? (3) Quando o documento é emitido por uma filial e o dinheiro cai na conta bancária de outra filial, qual estabelecimento informa o 1601: o que vendeu (como respondem AL, CE, RN e MG) ou o titular da conta onde o recebimento ocorreu? Na PB e no PR, o FAQ não diz. (4) No PR, qual é o critério que separa as empresas dispensadas das que entregam o 1601 (regime, porte, faturamento, atividade)?

**Resposta pedida:** a regra de cada UF, ou a indicação de onde consultar.

**Leitura adotada:** cartão de crédito pela competência (autorização, valor total), com aviso nas UFs sem resposta; o estabelecimento é o que vendeu em AL, CE, RN e MG e vazio na PB; o PR não gera o 1601, com aviso, até haver o critério.

## Bloco D — Reforma tributária (CBS, IBS, LC 214 e LC 225)

*Perguntas novas, de interpretação do Decreto 12.955/2026 e das LC 214 e 225. **Provavelmente exigem consulta formal** (seção 2). Vêm das perguntas Q157-C10 a C14 e Q140-5 do documento 38.*

### Pergunta 21 — Transição de 2026: quem é "desobrigado" e o ressarcimento

**Assunto sugerido:** Reforma tributária, CBS (obrigações acessórias). **Origem:** Q157-C10.

**Texto para colar:**

> Prezados, sobre a transição de 2026 no Decreto 12.955/2026, perguntamos: (1) Quem é "desobrigado" das obrigações acessórias no art. 464, II (Simples Nacional, MEI, ou ato conjunto)? A dispensa vale também para o IBS? (2) O art. 583, II, b (ressarcir em 60 dias o que foi recolhido) e o art. 465 (o saldo da apuração informativa não é ressarcível) tratam de situações diferentes, ou a primeira exclui o saldo da segunda?

**Resposta pedida:** a resposta com o fundamento.

**Leitura adotada:** como lido no documento 157.

### Pergunta 22 — Redução de 0,1 ponto da CBS em 2026

**Assunto sugerido:** Reforma tributária, CBS (alíquotas). **Origem:** Q157-C11.

**Texto para colar:**

> Prezados, sobre a redução de 0,1 ponto percentual da CBS na transição (LC 214, art. 347; Decreto 12.955, art. 585), perguntamos: (1) A alíquota efetiva é (alíquota padrão menos 0,1 ponto) vezes (1 menos o redutor r)? Em regime específico com alíquota própria ou específica por unidade, a redução é de ponto sobre a alíquota ou sobre a base? (2) Quais operações são "combustíveis do regime específico" (LC 214, arts. 172 a 180) e ficam fora da redução? A marca vale por cClassTrib, por produto da ANP ou por regime da empresa? (3) A alíquota da CBS de 2027 já foi fixada (resolução do Senado até 31/10/2026) ou vale a do TCU? Qual o valor?

**Resposta pedida:** a fórmula, o critério da exceção e a alíquota de 2027.

**Leitura adotada:** (1) leitura minha; (2) por cClassTrib; (3) sem linha de alíquota.

### Pergunta 23 — Entrega do arquivo do documento fiscal (Decreto, art. 134, I)

**Assunto sugerido:** Reforma tributária, documentos fiscais. **Origem:** Q157-C12.

**Texto para colar:**

> Prezados, sobre a entrega do arquivo do documento fiscal (Decreto 12.955/2026, art. 134, I), perguntamos: (1) Qual prazo vale para "imediatamente"? (2) Em contingência, sem protocolo de autorização, a entrega ocorre depois da transmissão posterior? (3) No consumidor sem identificação, a disponibilização por QR Code ou por consulta cumpre a obrigação? (4) A multa de 20 UPF é por período de apuração (e não por documento)?

**Resposta pedida:** a resposta de cada ponto, com o artigo.

**Leitura adotada:** sem prazo fixo; aviso por mês.

### Pergunta 24 — Cadastro: comunicação das alterações (Decreto, art. 108)

**Assunto sugerido:** Reforma tributária, cadastro. **Origem:** Q157-C13.

**Texto para colar:**

> Prezados, sobre a comunicação cadastral do Decreto 12.955/2026, perguntamos: (1) O prazo do art. 108 ("último dia útil do mês seguinte") usa o calendário do município da matriz? (2) Na venda ou transferência do estabelecimento, quem comunica? O encerramento da filial com o CNPJ raiz mantido é evento do art. 108, II ou só baixa? (3) Para a pessoa física que passa a emitir documento fiscal em 2027, a chave de acesso usa o CNPJ ou o CPF (o art. 124, § 1º, I, aceita os dois)?

**Resposta pedida:** a resposta de cada ponto, com o artigo.

**Leitura adotada:** calendário da matriz; ambos os campos aceitos.

### Pergunta 25 — Pessoa física, produtor rural e receita de referência

**Assunto sugerido:** Reforma tributária, contribuintes. **Origem:** Q157-C14.

**Texto para colar:**

> Prezados, sobre a obrigatoriedade para pessoa física e produtor rural (LC 214 e Decreto 12.955/2026), perguntamos: (1) Quem é a "pessoa física responsável tributário" (arts. 115, § 3º, I e 105, § 4º-A, I)? Qual o prazo de inscrição de quem já atua em 01/01/2027? (2) Qual a data de início do produtor rural pessoa jurídica, do nanoempreendedor, do transportador autônomo e do condomínio? (3) O art. 243 fixa a receita de 2024 para o "contribuinte desde 01/01/2026"; a LC 214, art. 165, § 3º, fala em "ano anterior ao da entrada em vigor". Os dois textos conferem? (4) O limite do art. 239, § 3º, de 2027 já foi divulgado?

**Resposta pedida:** a resposta de cada ponto, com o artigo ou o ato.

**Leitura adotada:** sem data para os casos dependentes de ato conjunto.

### Pergunta 26 — Bônus de adimplência da CSLL (LC 225, art. 41)

**Assunto sugerido:** CSLL (LC 225/2026). **Origem:** Q140-5 e Q140-6e (documento 180).

**Texto para colar:**

> Prezados, sobre o bônus de adimplência da CSLL (LC 225/2026, art. 41), que a lei descreve como "desconto no pagamento à vista", perguntamos: (1) O desconto vale para cada recolhimento de CSLL (estimativa mensal, trimestre e ajuste anual) ou só para o da apuração final? (2) O que é "à vista": só a cota única, ou também a primeira quota quando o trimestre é pago em quotas? O pagamento depois do vencimento perde o bônus inteiro? (3) Como o desconto chega ao pagamento: DARF com valor menor, crédito posterior, ou outro meio? (4) Quando a estimativa mensal é paga com o bônus, o ajuste anual abate o valor que extinguiu o débito (o integral) ou o valor efetivamente pago? (5) Os 12 meses de selo e o percentual (1%, 2% e 3%) contam até o vencimento ou até a data do pagamento? Com vários recolhimentos no mesmo ano do benefício, qual a ordem em que eles consomem o limite anual? (6) O leiaute 12 da ECF tem linha própria para o bônus, ou ele não é informado? (7) Há norma da Receita regulamentando o procedimento, e qual?

**Resposta pedida:** a resposta de cada ponto, com o ato ou o artigo.

**Leitura adotada:** o ERP calcula o bônus em toda linha de CSLL paga à vista e mantém a situação provisória até a regra da Receita. O tratamento contábil (Q140-6a a Q140-6d) é do contador e não vai para a Receita; a linha da ECF (Q140-6e) está no ponto (6). O detalhe das opções está no documento 180.

# 4. Quadro-resumo

| Nº | Assunto | Registro, tabela ou norma | Bloqueia? | Decisão que aguarda |
|----|---|---|---|---|
| 1 | `M(344)` e `M(170)` | M350A 171, M350R 345 | Sim | Q93 (cálculo da CSLL) |
| 2 | `FIM_SE` e parênteses | N660 3, N600 24 e 36, P200 25210 a 25250, P300 9 | Sim | Carga da fórmula |
| 3 | Alíquotas 7 e 8 | N660 3, N670 2, P500 2, T181 6, U182 2 | Sim | Q93-5b e Q130-2 |
| 4 | Valores de `IND_ALIQ_CSLL` | 0020 | Parcial | Domínio e vigência |
| 5 | Funções sem definição | Todas as fórmulas | Parcial | Casos de borda |
| 6 | Y520 R e P | Y520 | Não | Geração do arquivo |
| 7 | `0,348` | P500 18200 | Sim | Tributo a maior |
| 8 | P130 | P130 6, 74 a 77, X280 | Não | Q132-5 |
| 9 | Teste do `SE` sem o adicional | P200 26, P400 21 | Não | Fórmula de 2026 |
| 10 | Divergências herdadas | N660, N610, N670, M350R, N620, N630A | Não | Rascunho; falta a planilha |
| 11 | `VL_PERIODO` negativo | Y520 | Não | Q100-14 |
| 12 | Y520 acima do corte | Y520, 0020 | Não | Q110-11 |
| 13 | Encontro de contas com não residente | Y520 FORMA | Não | Q111-10 |
| 14 | Refis | 0010.OPT_REFIS, Y680 | Não | Q128-5 |
| 15 | Presumido: P130, P230, P300 9, X280 | P130, P230, P300, X280 | Não | Documentos 125 e 132 |
| 16 | Caixa no presumido | IN RFB 1.700/2017 | Não | Documento 127 |
| 17 | Tabelas do validador | 5.1.1, AJ_BENEF, 5.7, IPI | Não | Q172-C2, C3, C5, C7 |
| 18 | Chegada das tabelas, RR, vigência de um dia | Validador | Não | Q172-E5 |
| 19 | Guia Prático | COD_OBS, 1800, C130, C105, 1200, 4.4.6 | Não | Q175-C2 a C8 |
| 20 | Registro 1601 | FAQ 17.6.1 | Não | Q177-C1, Q176-11, Q176-C8 |
| 21 a 25 | Reforma tributária | Decreto 12.955/2026 | Não | Q157-C10 a C14 |
| 26 | Bônus da CSLL | LC 225, art. 41 | Não | Q140-5 |

# 5. Anexo: dúvidas que **não** são da Receita

Estas dúvidas aparecem nas listas do documento 38, mas a resposta é de outro órgão. Perguntar à Receita desperdiça um protocolo.

| Dúvida | Quem responde | Onde está |
|---|---|---|
| Registro 1400: de que CFOP e produto vem o valor e se o município é o da origem ou o do destino (Q175-C1) | SEFAZ de cada UF | Documento 38, 2.17 |
| GIAF de Pernambuco: regra de preenchimento dos modelos 1, 3 e 4 (Q175-C7) | SEFAZ-PE | Documento 38, 2.17 |
| Remissões entre códigos do ES (por exemplo ES013000 e ES023000) e os 2.304 códigos de parcela do Prodesin em AL (Q172-C8 e C9) | SEFAZ-ES e SEFAZ-AL | Documento 38, 2.15 |
| Códigos do cBenef a comparar com a informação adicional de ES e DF (Q172-E1) e tabela de cClass da NFGás | ENCAT ou SEFAZ | Documento 38, 3.11 e 1.21 |
| Datas e total do documento na NT 2026.004 (P40-04, P40-05, Q-5 e Q-6 do documento 42) e datas da NT 2026.005 (Q163-E1) | ENCAT | Documento 38, 3.1 e 3.x |
| Crédito de IBS da produção, redutor do IBS em 2027 e 2028 e regulamento do IBS (Q158-9, Q158-C3 e C6) | Comitê Gestor do IBS | Documento 38, 1.20 e 2.16 |
| Convalidação da habilitação anterior à LC (Q158-C11) | Ato conjunto da RFB, da Suframa e do CGIBS (a Suframa responde a parte dela) | Documento 38, 2.16 |
| Guia da SAF: código de receita, vencimento e forma de recolhimento | Ato conjunto da Receita e do Comitê Gestor (aguardar o ato) | Documento 38, 2.5 |
| Tratamento contábil do bônus de adimplência da CSLL (Q140-6), contas e eventos contábeis, CPC 02 e taxas de câmbio | Contador | Documento 38, 2.2 |
| Textos que você ainda precisa enviar: Portaria MF 3.074/2026, Portaria conjunta MF/CGIBS 14/2026, Portaria MF 2.813 e a prorrogação de 26/10/2026, ato do Ministro da MP 1.358, atos da ANP | Você (fontes oficiais) | Documento 38, 3.2 |

# 6. Perguntas para você

**Q179-1.** Aprova o conjunto das **26 perguntas** (a 10 só como rascunho) para envio, na ordem da seção 2? Recomendo **sim**; se alguma você prefere levar ao contador, apague o texto antes de enviar.

**Q179-2.** As perguntas **15, 16 e 21 a 26** são de interpretação da lei. Usar o Fale Conosco (orientação) ou pedir ao contador uma consulta formal? Recomendo que **o contador decida o canal**; os textos servem nos dois.

**Q179-3.** Reenvie a **planilha das tabelas dinâmicas do leiaute 12** (versão de 24/09/2026) e, se tiver, a do leiaute 11. Com ela completo a **pergunta 10** e reconfiro as fórmulas das perguntas 1 a 9, que vieram do documento 98 e **não foram reconferidas agora**.

# 7. Limites

- As perguntas 1 a 9 repetem o documento 98 (versão do Projeto de 22/10/2026 com as seções 3.8 e 3.9). Não reconferi as fórmulas contra a planilha, porque ela não está no meu ambiente.
- As perguntas 11 a 26 são escritas a partir do que está registrado nos documentos 38, 125, 127, 128, 132, 172, 175 e 176. As referências a artigos (IN RFB 1.700/2017, Decreto 12.955/2026, LC 214 e LC 225) são as que os documentos de origem citam; **não reli os textos oficiais** para este documento.
- O caminho do Fale Conosco da EFD ICMS/IPI e o da reforma tributária não foram conferidos; confirme na página.
- Nada foi enviado à Receita.
