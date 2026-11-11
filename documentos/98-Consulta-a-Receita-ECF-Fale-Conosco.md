# Consulta à Receita Federal sobre a ECF — Perguntas Prontas para o Fale Conosco — Documento 98

*Relatório de apoio: reúne as dúvidas que o desenho do cálculo da ECF (documento 93) não consegue resolver só com o manual e a planilha das tabelas dinâmicas. Cada pergunta traz o texto pronto para colar, a evidência exata (registro, tabela, linha, fórmula, página) e o motivo de a resposta importar. **O envio é seu**: nada foi enviado à Receita, e o documento não altera o dicionário.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- São **7 perguntas** (mais uma **8ª**, do P130, acrescentada em 28/10/2026, seção 3.8, e uma **9ª**, do teste do `SE` na P200 26 e na P400 21, acrescentada em 29/10/2026, seção 3.9), ordenadas da que mais bloqueia o cálculo para a que menos bloqueia. Cinco vêm de **erros ou lacunas das fórmulas da planilha** (perguntas 1 a 3, 5 e 7); duas vêm de **regras do manual que se contradizem** (perguntas 4 e 6). As perguntas 1 e 2 cobrem erros de digitação e de sintaxe; a pergunta 7 (percentual 0,348 em vez de 0,384) foi achada na conferência das tabelas do lucro presumido.
- As fontes são o **Manual de Orientação do Leiaute 12 da ECF** (atualização de julho/2026, Anexo ao Ato Declaratório Executivo Cofis nº 02/2026, 622 páginas) e a **planilha das tabelas dinâmicas** (versão de 24/09/2026). Os números de página abaixo são os do manual.
- A pergunta que o documento 93 previa sobre as linhas N630A 27 e 28 (dentro ou fora do imposto a pagar) **saiu da lista**: o texto das próprias orientações da planilha já responde (seção 5).
- **Correção de rótulo:** a primeira versão deste documento (entregue horas antes) chamava T181 de "lucro presumido" e U182 de "lucro arbitrado". Conferido na planilha: o bloco **T** é o **lucro arbitrado** (T120, T150, T170, T181), o bloco **U** é **imunes e isentas** (U180, U182) e o **lucro presumido** é o bloco **P** (P200, P300, P400, P500). Esta versão traz os rótulos certos e acrescenta as linhas do P500.
- Para cada pergunta há a **leitura que o ERP adotará enquanto a Receita não responder**. Nada disso muda o dicionário: são parâmetros com vigência, e a resposta só ajusta o valor.

# 2. Como enviar

- Canal: Fale Conosco da Receita, área Empresa, SPED, ECF (https://www.gov.br/receitafederal/pt-br/canais_atendimento/fale-conosco/empresa/sped/ecf).
- O formulário costuma pedir identificação do contribuinte e um assunto. As sugestões de assunto abaixo seguem a lista que a página mostra; confira o nome exato das opções na hora do envio.
- **Uma pergunta por protocolo** funciona melhor: a resposta vem mais objetiva e cada uma pode ser acompanhada separadamente. As perguntas 1, 2 e 3 também podem ir juntas (mesmo assunto, mesma planilha), se você preferir abrir menos protocolos.
- Anexe, se o formulário permitir, a linha da planilha em questão (print ou trecho). Cada pergunta já traz a fórmula transcrita, então o texto vale sozinho.
- Peça sempre a resposta **com o fundamento** (artigo da norma ou previsão de correção da planilha, com a data) para podermos registrar a vigência no ERP.

# 3. As perguntas

## 3.1 Pergunta 1 — Referência `M(344)` e `M(170)` nas linhas M350A 171 e M350R 345

**Assunto sugerido:** Leiautes (tabelas dinâmicas).

**Onde está:** planilha das tabelas dinâmicas, registro M350, vigência de 01/01/2015 sem fim.

| Linha | Descrição | Fórmula como está na planilha |
|---------------|--------------------------|--------------------------------|
| M350A 171 | Base de cálculo antes da compensação de BC negativa de períodos anteriores | `M350(169) - M350(170) + M(344)` |
| M350R 345 | Base de cálculo antes da compensação de BC negativa de períodos anteriores | `M350(343) - M350(344) + M(170)` |

**O que observamos:** todas as outras referências do M350 usam o nome da tabela com o número da linha, como `M350(169)`. Nessas duas linhas aparece `M(344)` e `M(170)`, sem o número 350. As linhas equivalentes do M300 (lucro real) trazem a referência completa: `M300A 171 = M300(169) - M300(170) + M300(344)` e `M300R 345 = M300(343) - M300(344) + M300(170)`.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as linhas 171 do M350A e 345 do M350R têm as fórmulas `M350(169) - M350(170) + M(344)` e `M350(343) - M350(344) + M(170)`. As referências `M(344)` e `M(170)` estão sem o número da tabela, diferente de todas as outras referências do M350. Nas linhas equivalentes do M300 (M300A 171 e M300R 345) a referência vem completa, `M300(344)` e `M300(170)`. Pergunto: (1) a intenção é `M350(344)` e `M350(170)`, ou seja, a compensação da base negativa do próprio período da outra atividade (rural e geral), espelhando o M300? (2) Se for, a planilha será corrigida e em qual versão? (3) Enquanto isso, o PVA da ECF calcula essas linhas com qual referência?

**Resposta pedida:** confirmar a referência correta e a data da correção da planilha.

**Por que importa:** é a base de cálculo da CSLL antes da compensação de base negativa de períodos anteriores. Com a referência incompleta, o ERP não consegue montar a fórmula sem adivinhar. **Leitura adotada enquanto isso:** `M350(344)` e `M350(170)`, espelhando o M300.

## 3.2 Pergunta 2 — Fórmulas com `FIM_SE` ou parênteses que não fecham (N660 3, N600 24 e 36, P200 25210 a 25250, P300 9)

**Assunto sugerido:** Leiautes (tabelas dinâmicas).

**Onde está:** planilha das tabelas dinâmicas, registro N660 (CSLL, estimativa), linha 3 "CSLL Apurada", vigência de 01/01/2015 sem fim.

**Fórmula como está:**

`SE (N660(2) <= 0) ENTAO 0 SENAO SE (0020.IND_ALIQ_CSLL() = "1") ENTAO N660(2) * 0,09 SENAO SE (0020.IND_ALIQ_CSLL() = "3") ENTAO N660(2) * 0,20 SENAO N660(2) * 0,15 FIM_SE FIM_SE`

**O que observamos:** a fórmula abre três blocos `SE` e fecha dois `FIM_SE`. Conferimos todas as fórmulas da planilha (4.475 linhas) e esta é a **única** com os blocos `SE` desbalanceados. A linha equivalente N670 2 tem três `SE` e três `FIM_SE`. Na mesma conferência achamos **parênteses que não fecham** em outras linhas (fora do texto entre aspas):

| Linha | Descrição | Parênteses abertos e fechados |
|---------------|--------------------------|--------------------------------|
| N600 24 | Outras despesas (Lei 6.404/1976, art. 187, IV): `DEBITO((L300(...) + ...)))` | 6 abertos e 7 fechados (um `)` a mais, no fim) |
| N600 36 | Outras receitas: `CREDITO((L300(...) + ...)))` | 6 abertos e 7 fechados (um `)` a mais, no fim) |
| P200 25210 a 25250 | Adicional da receita bruta por percentual (LC 224/2025, cinco linhas): `(P200(2)/P200("25.110"))*P200("25.200"))*0,016 *0,1` | 6 abertos e 7 fechados em cada uma (falta um `(` no início da multiplicação) |
| P300 9 | Redução por reinvestimento: `SE P230(38) <= 0 ENTAO ...` | `SE` sem parênteses na condição e 25 abertos contra 23 fechados |

Nas linhas do P200 e do P300 9, nossa leitura de qual parêntese falta é provável, não certa.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), a fórmula da linha 3 do registro N660 ("CSLL Apurada") tem três `SE` e apenas dois `FIM_SE`: `SE (N660(2) <= 0) ENTAO 0 SENAO SE (0020.IND_ALIQ_CSLL() = "1") ENTAO N660(2) * 0,09 SENAO SE (0020.IND_ALIQ_CSLL() = "3") ENTAO N660(2) * 0,20 SENAO N660(2) * 0,15 FIM_SE FIM_SE`. É a única com blocos SE/FIM_SE desbalanceados (a linha 2 do N670 tem três e três). Conferindo a planilha também achamos parênteses que não fecham: N600 24 e N600 36 (um `)` a mais no final), P200 25210 a 25250 (por exemplo `(P200(2)/P200("25.110"))*P200("25.200"))*0,016 *0,1`, com um `)` a mais) e P300 9 (a condição do `SE` está sem parênteses e a expressão tem 25 `(` e 23 `)`). Pergunto: (1) no N660 3 falta um `FIM_SE` no final, sem outra mudança de lógica? (2) Nas demais linhas, a intenção é remover o `)` a mais (N600 24 e 36), abrir o `(` que falta antes de `P200(2)/...` (P200 25210 a 25250) e fechar os parênteses do P300 9? Podem indicar a fórmula correta de cada uma? (3) A planilha será corrigida e em qual versão?

**Resposta pedida:** confirmar que no N660 3 falta só o `FIM_SE` e indicar a fórmula correta das demais linhas.

**Por que importa:** o ERP lê as fórmulas da planilha como parâmetro. Uma fórmula que não fecha não pode ser carregada sem edição manual, e a edição manual é justamente o risco que o parâmetro com vigência quer evitar. **Leitura adotada:** falta um `FIM_SE` no final do N660 3, sem outra mudança; nas outras linhas o ERP não carrega a fórmula sozinho e pede revisão do contador até a resposta.

## 3.3 Pergunta 3 — Fórmulas da CSLL que não tratam as alíquotas 7 e 8 (12% e 17,5%)

**Assunto sugerido:** Leiautes (tabelas dinâmicas) e Alíquota da CSLL.

**Onde está:** planilha das tabelas dinâmicas, cinco linhas, todas com vigência de 01/01/2015 sem fim.

| Linha | Descrição | O que a fórmula faz com `IND_ALIQ_CSLL` |
|---------------|--------------------------|--------------------------------|
| N660 3 | CSLL apurada (estimativa, lucro real) | `1` aplica 9%; `3` aplica 20%; **qualquer outro valor aplica 15%** |
| N670 2 | CSLL por atividade (estimativa) | Igual: `1` 9%; `3` 20%; **qualquer outro 15%** |
| T181 6 | CSLL apurada (**lucro arbitrado**) | Se `1`, 9%. Senão, para ECF de 2021 em diante: nos trimestres T01 e T02, `5` aplica 20% e **qualquer outro aplica 15%**; em T03 e T04, `5` aplica 25% e **qualquer outro aplica 20%** |
| U182 2 | CSLL apurada (**imunes e isentas**) | Mesma estrutura da T181 6 |
| P500 2 | CSLL apurada (**lucro presumido**) | Para ECF de 2022 em diante: `1` aplica 9%; `3` aplica 20%; **qualquer outro valor aplica 15%** |

**O que observamos:**

- As orientações dessas linhas já listam as alíquotas `7 – 9%/12%` e `8 – 15%/17,5%` (em N670 2, T181 6 e outras linhas), mas **a fórmula não tem ramo para 7 nem para 8**. Quem escolher `7` cai em 15% (N660 3, N670 2 e P500 2) ou em 15%/20% (T181 6 e U182 2), e quem escolher `8` também cai em 15% (ou 15%/20%). O 12% e o 17,5% nunca saem da fórmula.
- **Dentro da própria tabela P500 a planilha já trata o 7 e o 8**, só que na linha 18300 ("Tributo Pago a Maior no Trimestre", bloco da LC 224/2025): para o código `7` usa **9% em T01 de 2026 e 12% nos demais períodos**; para o `8` usa **15% em T01 de 2026 e 17,5% nos demais**; o `3` usa 20% e o `4` usa 15%. Ou seja, a P500 diz uma coisa na linha 2 (CSLL apurada) e outra na linha 18300 (tributo a maior), o que reforça a pergunta e dá uma pista da intenção da Receita (12% e 17,5% a partir do segundo trimestre de 2026).
- Nas linhas T181 6 e U182 2, a condição é `0000.DT_INI() >= "2021-01-01"` **sem data final**. Pela nossa leitura, uma PJ com `IND_ALIQ_CSLL = 4` (15%) e ECF de 2026 teria 15% em T01 e T02 e **20% em T03 e T04**, o que nos parece resíduo da regra transitória de 2021 (códigos 5 e 6).
- A alíquota de 12% começa, pela nossa leitura da LC 224/2025 e do art. 3º da Lei 7.689/1988 (a confirmar), em **01/04/2026**. Em 2026 o ano-calendário então mistura 9% (janeiro a março) e 12% (abril em diante). Não encontramos na planilha nem no manual como o código `7` reparte o ano entre os trimestres (T01 a T04) ou entre os meses (A01 a A12).

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as fórmulas da CSLL nas linhas N660 3, N670 2, P500 2, T181 6 e U182 2 só tratam os valores de IND_ALIQ_CSLL 1, 3 e 5. As orientações das próprias linhas (N670 2 e T181 6, por exemplo) já listam os códigos 7 (9%/12%) e 8 (15%/17,5%), criados pela LC 224/2025 conforme o manual (item de alterações do leiaute, p. 620), mas a fórmula não tem ramo para 7 nem 8: o valor 7 cai em 15% (N660 3, N670 2 e P500 2) ou em 15%/20% (T181 6 e U182 2), e o 8 também. Já a linha P500 18300 (bloco LC 224/2025) trata o 7 com 9% em T01/2026 e 12% depois, e o 8 com 15% em T01/2026 e 17,5% depois. Pergunto: (1) qual a fórmula correta dessas cinco linhas para os anos-calendário 2026 e 2027, com os códigos 7 e 8, e a regra da P500 18300 (9% ou 15% só em T01/2026) vale também para a estimativa mensal e a apuração anual? (2) Qual o período exato em que passa a valer o 12% (9% até 31/03/2026 e 12% de 01/04/2026, como entendemos) e como a ECF reparte o ano nos meses (A01 a A12) e trimestres (T01 a T04)? (3) Nas linhas T181 6 (arbitrado) e U182 2 (imunes e isentas), a condição `0000.DT_INI() >= "2021-01-01"` não tem data final; para 2022 em diante, uma PJ com código 4 (15%) deve mesmo ter 20% nos trimestres T03 e T04? Se não, a planilha será corrigida e em qual versão? (4) Para 2028 em diante, quais códigos de IND_ALIQ_CSLL valem para cada segmento da Lei 7.689, art. 3º?

**Resposta pedida:** a fórmula correta (ou a previsão de correção e a versão da planilha), mais o início exato do 12% e do 17,5% no ano.

**Por que importa:** é a linha da CSLL devida de todo cliente nos segmentos que mudaram de alíquota (pagamento, instituições financeiras da LC 105, art. 1º, § 1º, IV, VIII, XI, XII e XIII, e capitalização). Com a planilha como está, o ERP calcularia 15% a quem deveria 12% ou 17,5%. **Leitura adotada enquanto isso:** o ERP **para e avisa** nas cinco linhas quando o contador escolhe 7 ou 8, e espera a resposta do contador (decisão Q93-5b). Não calcula com 15% nem com 20%.

## 3.4 Pergunta 4 — Lista de valores válidos de `IND_ALIQ_CSLL` contra a regra de validação e o texto do campo

**Assunto sugerido:** Leiautes e Mensagens de erro do PVA.

**Onde está:** manual da ECF, registro 0020, campo 2 `IND_ALIQ_CSLL` (páginas 81 e 92) e quadro de alterações do leiaute (página 620).

| Trecho | Página | O que diz |
|---------------|--------|--------------------------------|
| Quadro do campo | 81 | Valores válidos `[1;3;4]`. O texto do campo descreve `1` 9%, `3` 20%, `4` 15%, `7` 9%-12% e `8` 15%-17,5% |
| Regra `REGRA_PREENCHIMENTO_IND_ALIQ_CSSL` | 92 | "Verifica, quando o ano da ECF for maior ou igual a 2019, se o campo 0020.IND_ALIQ_CSLL é igual a '1' (9%) ou '4' (15%)." Gera **erro** |
| Alterações do leiaute | 620 | "Campo IND_ALIQ_CSLL – criação de duas novas alíquotas transitórias – 12% e 17,5% – para os anos de 2026/27, conforme LC 224/25" |

**O que observamos:** as três partes não fecham entre si. A lista de valores válidos é `[1;3;4]`, sem o 7 e o 8, que o próprio texto e o quadro de alterações dizem ter sido criados. A regra de validação aceita só `1` ou `4` a partir de 2019, então o `3` (20%, bancos, previsto na lista) e o `7` e o `8` seriam **erro** no PVA.

**Texto para colar:**

> Prezados, no manual da ECF (leiaute 12, atualização de julho/2026), registro 0020, campo 2 (IND_ALIQ_CSLL), a coluna de valores válidos traz [1;3;4] (p. 81), mas o texto do campo descreve também 7 (9%-12%) e 8 (15%-17,5%), e o quadro de alterações do leiaute (p. 620) diz que o campo criou "duas novas alíquotas transitórias – 12% e 17,5% – para os anos de 2026/27, conforme LC 224/25". A regra REGRA_PREENCHIMENTO_IND_ALIQ_CSSL (p. 92) verifica, para ano da ECF maior ou igual a 2019, se o campo é igual a "1" ou "4", o que gera erro para 3, 7 e 8. Pergunto: (1) quais valores o PVA aceita hoje para cada ano-calendário (2025, 2026, 2027 e 2028 em diante)? (2) Uma instituição com alíquota de 20% (código 3) e uma PJ com a alíquota transitória de 12% ou 17,5% (códigos 7 e 8) devem preencher qual código? (3) A lista de valores válidos e a regra da p. 92 serão atualizadas e em qual versão do leiaute ou do PVA?

**Resposta pedida:** a tabela de valores aceitos por ano-calendário e a previsão de atualização.

**Por que importa:** o ERP oferece ao contador os códigos 1, 3, 4, 7 e 8 (decisão Q93-5, entidade `Mov_Ecf_Escolha_Contador_Ano`). Se o PVA rejeitar 3, 7 ou 8, o ERP precisa avisar antes de gerar o arquivo. **Leitura adotada enquanto isso:** o domínio `indicador_aliquota_csll_ecf` mantém 1, 3, 4, 7 e 8 e a vigência de cada valor fica como parâmetro, com a situação "a confirmar" até a resposta.

## 3.5 Pergunta 5 — Funções usadas nas fórmulas e sem definição

**Assunto sugerido:** Leiautes (tabelas dinâmicas).

**Onde está:** planilha das tabelas dinâmicas, 4.475 linhas. A busca no texto do manual (622 páginas) não encontra definição das funções `T_DRE`, `DEBITO`, `CREDITO` e `MESES_PERIODO`, nem de `PERIODO_ATUAL` (a função `PERIODO_ANTERIOR` aparece uma vez). `BAL_RED` aparece no manual só como o **campo** `0010.MES_BAL_RED` (p. 74), não como função com período no argumento.

| Função | Exemplos na planilha | Nossa leitura | O que falta confirmar |
|---------------|--------------------------|--------------------------|--------------------------|
| `T_DRE(x)` | M300A 2 `T_DRE(L300("3.01") + L300("3.02.01.01.01.01"))` (11 usos) | Converte o saldo da conta do L300 para o sinal da DRE: débito positivo, crédito negativo | Convenção de sinal e tratamento do saldo zero |
| `DEBITO(x)` | N500 1 `DEBITO(M300(175))+DEBITO(M300(349))`; N600 24 (11 usos) | `x` se positivo, senão 0 | Se o resultado é o valor absoluto do débito ou só o positivo |
| `CREDITO(x)` | N600 36 e 37 `CREDITO((L300(...) + ...))` (8 usos) | O espelho de `DEBITO`: o valor positivo do crédito, em módulo | Se devolve módulo ou o valor com sinal |
| `MESES_PERIODO()` | N610 3 e 8, N620 4 `20000 * MESES_PERIODO()` (37 usos) | Número de meses do período de apuração: 3 no trimestre, 1 na estimativa mensal, 12 no ano; é o multiplicador do limite do adicional (R$ 20.000 por mês) | Valor em apuração anual com suspensão, em início e fim de atividade, em fusão, cisão e incorporação |
| `BAL_RED(período)` | N620 1 `SE (BAL_RED(PERIODO_ATUAL()) = "B")` (5 usos) | O valor do campo `0010.MES_BAL_RED` para o mês indicado: `E` (receita bruta), `B` (balanço ou balancete) ou `0` (fora do período) | Confirmação |
| `PERIODO_ATUAL()` e `PERIODO_ANTERIOR()` | N620 20 `SOMA(N620("20.01";"A01":PERIODO_ANTERIOR()))` | O mês ou trimestre em cálculo; o último período fechado antes dele | Se `A01:PERIODO_ANTERIOR()` inclui ou exclui o atual |

**O que observamos:** o ERP reconstruiu o comportamento dessas funções comparando a planilha com **dois arquivos reais de ECF de 2025** (lucro real anual, estimativa mensal, forma de apuração `A`). A leitura bateu: em N620 20, por exemplo, a soma de janeiro até o mês anterior só acumula nos meses de balancete (`B`), e o imposto pago de janeiro e de outubro conferiu com o arquivo. Mas dois arquivos não cobrem os casos de borda.

**Texto para colar:**

> Prezados, as fórmulas da planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026) usam as funções T_DRE, DEBITO, CREDITO, MESES_PERIODO, BAL_RED, PERIODO_ATUAL e PERIODO_ANTERIOR, que não encontramos definidas no manual de orientação (atualização de julho/2026) nem em outro documento publicado. Pergunto: (1) existe um documento que descreva essas funções (parâmetros, sinal do retorno, tratamento de saldo zero)? (2) Pela nossa leitura, DEBITO(x) devolve x se x for positivo e 0 caso contrário; CREDITO(x) devolve o módulo do valor se for crédito e 0 caso contrário; T_DRE(x) devolve o saldo no sinal da DRE (débito positivo, crédito negativo); MESES_PERIODO() devolve 3 no trimestre, 1 na estimativa mensal e 12 no ano-calendário; BAL_RED(p) devolve o campo 0010.MES_BAL_RED do mês p. Está correto? (3) Como MESES_PERIODO() se comporta em apuração anual com suspensão ou redução, em início ou encerramento de atividade e em fusão, cisão e incorporação? (4) Em SOMA(N620("20.01";"A01":PERIODO_ANTERIOR())), o intervalo termina no mês anterior ao mês em cálculo, sem incluí-lo?

**Resposta pedida:** a definição de cada função, ou a confirmação das leituras acima e o tratamento dos casos de borda.

**Por que importa:** é a linguagem de todas as fórmulas. O ERP carrega as fórmulas como parâmetro e precisa saber o que cada função devolve, principalmente `MESES_PERIODO`, que decide o limite do adicional de 10%. **Leitura adotada enquanto isso:** a coluna "Nossa leitura" da tabela, com teste contra os dois arquivos reais (documento 93, seção 9).

## 3.6 Pergunta 6 — Regras de obrigatoriedade do registro Y520 que se contradizem

**Assunto sugerido:** Mensagens de erro do PVA e Leiautes.

**Onde está:** manual da ECF, registro Y520 (páginas 562 a 564), campos `0020.IND_REC_EXT` e `0020.IND_PGTO_EXT` (página 84, campo 17 para o pagamento) e quadro de relação de registros (página 57).

**Texto das regras (página 563):**

- `REGRA_Y520_OBRIGATORIO_R`: "Verifica, quando 0020.IND_REC_EXT igual a 'S', se existe Y520.TIP_EXT igual a 'R' e **não existe** Y520.TIP_EXT igual a 'P'."
- `REGRA_Y520_OBRIGATORIO_P`: "Verifica, quando 0020.IND_PGTO_EXT igual a 'S', se **não existe** Y520.TIP_EXT igual a 'R' e existe Y520.TIP_EXT igual a 'P'."

**O que observamos:** a PJ que **recebeu e pagou** valores do exterior no ano (`IND_REC_EXT = "S"` e `IND_PGTO_EXT = "S"`) precisa, ao mesmo tempo, ter Y520 do tipo `R` sem `P` (primeira regra) e Y520 do tipo `P` sem `R` (segunda regra). **Nenhum arquivo cumpre as duas.** Além disso, a regra `REGRA_TIP_EXT_PERMITIDO` (p. 564) exige que o Y520 `P` só exista com `IND_PGTO_EXT = "S"` e o `R` só com `IND_REC_EXT = "S"`, e a regra `REGRA_FORMA_PAGTO_INVALIDA` (p. 564) diz, ao pé da letra: "Verifica, quando Y520.TIP_EXT igual a 'P', se Y520.FORMA é **diferente de** '4', ou, quando Y520.TIP_EXT igual a 'R', se Y520.FORMA é **diferente de** '5'", e gera **erro**. Isso contradiz o próprio quadro do campo `FORMA` (p. 563), que diz que a forma `4` (depósito em conta do exterior) "só é válida para TIP_EXT = R" e a `5` (recursos mantidos no exterior) "só é válida para TIP_EXT = P", e contradiz o **exemplo do manual** (p. 564), `|Y520|R|1|1|10500|100000,00|`, que é um recebimento (`R`) pela forma `1` (câmbio): pela regra como está escrita, esse exemplo daria erro. Parece troca de "igual a" por "diferente de". A introdução do registro (p. 562) diz que ele "será **habilitado** somente para" quem recebeu ou pagou, e as regras o tratam como **obrigatório** (erro).

**Texto para colar:**

> Prezados, no manual da ECF (leiaute 12, atualização de julho/2026), as regras de validação do registro Y520 (p. 563) dizem: REGRA_Y520_OBRIGATORIO_R: quando 0020.IND_REC_EXT = "S", deve existir Y520.TIP_EXT = "R" e não pode existir Y520.TIP_EXT = "P"; REGRA_Y520_OBRIGATORIO_P: quando 0020.IND_PGTO_EXT = "S", não pode existir Y520.TIP_EXT = "R" e deve existir Y520.TIP_EXT = "P". Para a PJ que recebeu e também pagou valores do exterior no mesmo ano (as duas indicações "S"), as duas regras não podem ser cumpridas ao mesmo tempo. Pergunto: (1) qual o preenchimento correto do Y520 e dos campos IND_REC_EXT e IND_PGTO_EXT nesse caso? (2) A redação das regras será corrigida (por exemplo, retirando o "não existe" do outro tipo) e em qual versão do PVA? (3) A p. 562 diz que o registro é "habilitado" para quem recebeu ou pagou e as regras o tratam como obrigatório com erro: qual vale? (4) Como o PVA se comporta hoje com os dois indicadores em "S"? (5) Ainda no Y520, a regra REGRA_FORMA_PAGTO_INVALIDA (p. 564) diz que gera erro quando TIP_EXT = "P" e FORMA é diferente de "4", ou quando TIP_EXT = "R" e FORMA é diferente de "5", mas o quadro do campo FORMA (p. 563) diz que a forma 4 só vale para "R" e a 5 só para "P", e o exemplo do manual (p. 564) é um "R" com forma 1 (câmbio). O texto correto da regra é "igual a" em vez de "diferente de" (erro quando P usa a forma 4 ou R usa a forma 5)? Em qual versão será corrigida?

**Resposta pedida:** a forma correta de informar recebimento e pagamento no mesmo ano, o texto correto da regra `REGRA_FORMA_PAGTO_INVALIDA` e o comportamento atual do PVA.

**Por que importa:** o ERP gera o Y520 a partir dos pagamentos e recebimentos internacionais cadastrados (câmbio, TIR, contas de não residentes). Sem a regra certa, o ERP pode gerar um arquivo que o PVA rejeita, ou deixar de gerar o registro de uma empresa que precisa dele. **Leitura adotada enquanto isso:** o ERP gera os registros `R` e `P` que existirem nos dados, avisa o contador quando os dois indicadores estão em "S" e não toma decisão sozinho. Na forma de pagamento, o ERP segue o quadro do campo (4 só para recebimento, 5 só para pagamento) e o exemplo do manual, não a letra da regra.

## 3.7 Pergunta 7 — Percentual `0,348` em vez de `0,384` na linha P500 18200

**Assunto sugerido:** Leiautes (tabelas dinâmicas).

**Onde está:** planilha das tabelas dinâmicas, registro P500 (CSLL, lucro presumido), linha 18200 "Base de Cálculo Adicionado a Maior no Trimestre" (bloco LC 224/2025, vigência de 01/01/2026 sem fim).

**O que observamos:** a linha usa três percentuais de presunção da CSLL em três termos somados. Os dois primeiros são `0,12` e `0,32`. O terceiro termo vem escrito `((P400(5)/P400("20.110"))*P500("18.100"))*0,348 *0,1`. O percentual de presunção da faixa de 38,4% é `0,384`, como na linha P400 20230 (`*0,384*0,1`) e na P200 25250 (`*0,384 *0,1`). Parece troca de dígitos (`0,348` em vez de `0,384`).

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), a linha 18200 do registro P500 ("Base de Cálculo Adicionado a Maior no Trimestre") usa, no terceiro termo, `((P400(5)/P400("20.110"))*P500("18.100"))*0,348 *0,1`. Os outros termos usam 0,12 e 0,32, e as linhas equivalentes (P400 20230 e P200 25250) usam 0,384 para a faixa de 38,4%. Pergunto: (1) o percentual correto é 0,384 (troca de dígitos) ou 0,348 é intencional? (2) Se for erro, a planilha será corrigida e em qual versão? (3) O PVA da ECF já calcula com 0,384?

**Resposta pedida:** confirmar o percentual e a data da correção.

**Por que importa:** a linha alimenta o "tributo pago a maior" (P500 18300 e 18500) do lucro presumido na transição da LC 224/2025, para quem tem receita bruta na faixa de 38,4%. **Leitura adotada enquanto isso:** 0,384, com aviso ao contador.

## 3.8 Pergunta 8 — P130: linhas 74 a 77 (demais atividades), receita de 38,4% sem linha e orientação da linha 6 citando `P130/68`

**Assunto sugerido:** Leiautes (tabelas dinâmicas).

**Situação (28/10/2026):** o **ponto 3** foi aprovado por você (Q134-6, documento 134). Os **pontos 1 e 2** vêm do documento 132 (Q132-5), **ainda sem resposta**: se você não os aprovar, apague-os do texto antes de enviar.

**Onde está:** planilha das tabelas dinâmicas, aba P130, vigência de 01/01/2015 sem fim; manual da ECF, registro X280.

| Ponto | O que observamos |
|---|---|
| 1 | As linhas 74 a 77 são do bloco "DEMAIS ATIVIDADES" (rótulo da linha 73; a fórmula da linha 78 as trata como lucro presumido das demais atividades), mas a descrição das quatro linhas diz "beneficiado com a redução do imposto de renda", e a regra do X280 que soma receitas de reduções (`REGRA_RECEITA_REDUCOES`) soma as linhas 74 a 77 como receita de reduções |
| 2 | O P130 não tem linha de 38,4%, e o P200 linha 10 inclui `P200(9)*0,384`; a orientação diz que a soma dos lucros presumidos do P130 coincide com o P200/10 |
| 3 | A orientação da linha P130/6 cita `P130/68` na lista das linhas cuja soma deve coincidir com o P200/10; as orientações das **outras oito linhas** (15, 24, 33, 42, 51, 60, 69 e 78) citam `P130/78`. A linha 68 é a receita a 32% do bloco de reinvestimento |

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), registro P130 (Demonstração das Receitas Incentivadas do Lucro Presumido), observamos três pontos. (1) As linhas 74 a 77 pertencem ao bloco "DEMAIS ATIVIDADES" (rótulo da linha 73, e a fórmula da linha 78 as trata como lucro presumido das demais atividades), mas a descrição das quatro linhas diz "beneficiado com a redução do imposto de renda", e a regra de validação do X280 que soma as receitas de reduções (REGRA_RECEITA_REDUCOES) soma as linhas 74 a 77 como receita de reduções. As linhas 74 a 77 são a receita sem benefício (demais atividades), como entendemos, e a descrição e a regra do X280 serão corrigidas? (2) O P130 não tem linha para a receita sujeita ao percentual de 38,4%, mas o P200 linha 10 inclui P200(9)*0,384, e a orientação das linhas P130/6, 15, 24, 33, 42, 51, 60, 69 e 78 diz que a soma dos lucros presumidos deve coincidir com o P200/10. Como deve preencher o P130 a pessoa jurídica com receita a 38,4% (Empresa Simples de Crédito, LC 167/2019) que tem isenção ou redução do imposto? (3) A orientação da linha P130/6 cita "P130/68" na lista de linhas cuja soma deve coincidir com o P200/10, enquanto as orientações das outras oito linhas (15, 24, 33, 42, 51, 60, 69 e 78) citam "P130/78"; a linha 68 é a receita sujeita a 32% do bloco de reinvestimento, e não um lucro presumido. É erro de digitação, e o correto é P130/78? A planilha será corrigida e em qual versão? Pedimos, para os três pontos, a resposta com o fundamento (artigo da norma ou previsão de correção, com a data).

**Resposta pedida:** a natureza das linhas 74 a 77, como preencher o P130 com receita de 38,4% e a correção da orientação da linha 6, com a versão.

**Por que importa:** o ERP deriva as linhas 74 a 77 como receita sem benefício (documento 134) e confere a soma dos lucros contra o P200 10. **Leitura adotada enquanto isso:** as linhas 74 a 77 são receita sem benefício; a orientação da linha 6 vale com `P130/78` (sua resposta de 28/10/2026); a receita de 38,4% fica sem linha no P130, com aviso ao contador.

## 3.9 Pergunta 9 — P200 26 e P400 21 (versões de 2026): o teste do `SE` não inclui o adicional da LC 224/2025

**Assunto sugerido:** Leiautes (tabelas dinâmicas) e LC 224/2025.

**Situação (29/10/2026):** texto aprovado por você (Q135-6, documento 135, seção 8). O arquivo 09 foi gerado; o envio é seu.

**Onde está:** planilha das tabelas dinâmicas (leiaute 12, versão de 24/09/2026), P200 linha 26 e P400 linha 21, na parte "a partir de 01/01/2026".

**O que observamos.** Nas duas linhas, a versão de 2026 faz o teste do `SE` com a base **sem** o adicional da LC 224/2025 e só **depois** soma o adicional dentro do `ENTAO`:

| Linha | Fórmula de 2026 (resumida) |
|---|---|
| P200 26 | `SE (SOMA(P200(10:21)) - (deduções) > 0) ENTAO (SOMA(P200(10:21)) - (deduções) + SOMA(P200("25.210":"25.250"))) SENAO 0 FIM_SE`, com as deduções P200(22), (23), (24), (25), ("25.01") e ("25.02") |
| P400 21 | `SE (SOMA(P400(6:17)) - SOMA(P400(18:20)) > 0) ENTAO (SOMA(P400(6:17)) + SOMA(P400("20.210":"20.230")) - SOMA(P400(18:20))) SENAO 0 FIM_SE` |

Se a base sem o adicional for zero ou negativa, o resultado é 0 e o adicional, mesmo positivo, não é somado. É um caso raro (as deduções teriam de superar o lucro presumido), mas a diferença é imposto a menor ou a maior.

**Texto para colar:**

> Prezados, na planilha das tabelas dinâmicas da ECF (leiaute 12, versão de 24/09/2026), as versões "a partir de 01/01/2026" das linhas P200 26 (base de cálculo do imposto sobre o lucro presumido) e P400 21 (base de cálculo da CSLL) testam, no `SE`, a base sem o adicional da LC 224/2025 e somam o adicional só dentro do `ENTAO`. P200 26: `SE (SOMA(P200(10:21)) - (P200(22) + P200(23) + P200(24) + P200(25) + P200("25.01") + P200("25.02")) > 0) ENTAO (SOMA(P200(10:21)) - (P200(22) + P200(23) + P200(24) + P200(25) + P200("25.01") + P200("25.02")) + SOMA(P200("25.210":"25.250"))) SENAO 0 FIM_SE`. P400 21: `SE (SOMA(P400(6:17)) - SOMA(P400(18:20)) > 0) ENTAO (SOMA(P400(6:17)) + SOMA(P400("20.210":"20.230")) - SOMA(P400(18:20))) SENAO 0 FIM_SE`. Com isso, se a base sem o adicional for zero ou negativa, o resultado é 0 e o adicional positivo não é somado (por exemplo, na P200 26: soma das linhas 10 a 21 = 10.000,00, deduções = 10.500,00 e adicional = 800,00 dão 0; se o teste incluísse o adicional, a base seria 300,00). Pergunto: (1) o teste do `SE` sem o adicional é intencional, de modo que o adicional só entra quando a base sem ele é positiva? (2) Se for intencional, qual o fundamento (artigo da LC 224/2025 ou da regulamentação)? Se não for, a planilha será corrigida e em qual versão? (3) Qual dessas leituras o PVA da ECF aplica hoje na validação da P200 26 e da P400 21?

**Resposta pedida:** se o teste é intencional, o fundamento, e como o PVA valida a linha; ou a previsão de correção da planilha, com a versão.

**Por que importa:** o ERP executa o texto da versão vigente. **Leitura adotada enquanto isso:** a fórmula **como publicada** (o adicional é descartado quando a base sem ele não é positiva), com aviso ao contador quando o caso ocorrer. Nada muda no dicionário.

# 4. Quadro-resumo das perguntas

| Nº | Assunto | Registro ou linha | Tipo da dúvida | Bloqueia o cálculo? |
|----|--------------------|----------------------|------------------|----------------|
| 1 | Referência `M(344)` e `M(170)` | M350A 171, M350R 345 | Erro provável da planilha | Sim, a base da CSLL antes da compensação |
| 2 | `FIM_SE` e parênteses que não fecham | N660 3, N600 24 e 36, P200 25210 a 25250, P300 9 | Erro da planilha | Sim, a CSLL apurada da estimativa e as linhas do adicional da LC 224/2025 |
| 3 | Alíquotas 7 e 8 sem ramo na fórmula, e 20% residual nos trimestres T03 e T04 | N660 3, N670 2, P500 2, T181 6, U182 2 | Lacuna e erro da planilha | Sim, para clientes dos segmentos que mudaram de alíquota |
| 4 | Lista de valores contra a regra | 0020.IND_ALIQ_CSLL | Regras do manual que se contradizem | Parcial: o ERP avisa antes de gerar |
| 5 | Funções sem definição | Todas as fórmulas | Documentação ausente | Parcial: leitura validada em dois arquivos |
| 6 | Obrigatoriedade do Y520 | Y520 | Regras do manual que se contradizem | Não bloqueia o cálculo; afeta a geração do arquivo |
| 7 | Percentual `0,348` | P500 18200 | Erro provável da planilha | Sim, o tributo pago a maior do lucro presumido na transição da LC 224/2025 |
| 8 | Linhas 74 a 77 do P130, receita de 38,4% sem linha e `P130/68` | P130 6, 74 a 77, P200 10, X280 | Erro de digitação e lacuna do manual | Não bloqueia: o ERP avisa |
| 9 | Teste do `SE` sem o adicional da LC 224/2025 | P200 26, P400 21 (versões de 2026) | Dúvida de intenção da fórmula | Não bloqueia: o ERP segue a fórmula publicada e avisa |

# 5. O que não precisa ser perguntado

- **Linhas N630A 27 e 28 e N630B 25 dentro ou fora do imposto a pagar.** O documento 93 previa esta pergunta. A própria planilha responde: as orientações de N630A 28 e N630B 25 dizem que o valor "não deve estar contido no imposto líquido a pagar, devendo ser recolhido em separado do imposto devido" (com base nos Pareceres Normativos CST 57/1979 e 2/1996), e a orientação de N630A 27 manda recolher os juros de mora do imposto postergado em Darf distinto. A linha N630A 29 (crédito fiscal de IRPJ da Lei 14.789/2023) é direito creditório e também fica fora do "a pagar". A fórmula de N630A 26 acompanha: `SOMA(N630(3:4)) - SOMA(N630(6:25))` até 2025 e, a partir de 01/01/2026, soma de volta as linhas 6, 8, 10 a 16 e 16.10 (ajuste da LC 224/2025). **Isso fecha a Q93-7c no texto da planilha, sem consulta**, se você concordar com a leitura.
- **Limite de 30% na compensação de prejuízo fiscal e a exceção rural.** É regra de lei (Lei 9.065/1995, art. 15 e 16), já documentada, e não depende de esclarecimento da Receita.
- **Base normativa da ECF (o link que você enviou).** A página da Receita (Normas Internet) é a **IN RFB nº 2.004/2021**, que dispõe sobre a ECF. Três pontos dela sustentam o que o desenho já faz: o art. 4º diz que o Manual de Orientação do Leiaute (formato, regras de validação, tabelas) é divulgado pela **Cofis por Ato Declaratório Executivo**, o que mostra que as perguntas 1 a 7 são de competência da Cofis; o art. 2º, VI, manda a ECF registrar "os valores a excluir, adicionar ou compensar em exercícios subsequentes, inclusive prejuízo fiscal e base de cálculo negativa da CSLL" (a Parte B do e-Lalur e do e-Lacs, que alimenta a compensação do seu exemplo da Q93-7b); e o art. 7º, § 3º, diz que a ECF retificadora que altera saldos da Parte B obriga a retificar as ECF dos anos seguintes quando necessário, o que o ERP precisa tratar na retificação (não está no desenho do documento 93 e entra como lembrete na lista de pendências). A IN **não traz alíquotas, fórmulas nem regra de preenchimento do `IND_ALIQ_CSLL`**, por isso não responde nenhuma das sete perguntas.

# 6. Perguntas para você (respondidas em 27/10/2026)

- **Q98-1: sim.** Um arquivo de texto simples por pergunta, só com o bloco "Texto para colar" (mais o assunto sugerido e o canal). Gerados em 27/10/2026, em sete arquivos numerados na ordem de envio.
- **Q98-2: "ok".** Lido como confirmação da ordem de envio: perguntas **3 e 1** primeiro (bloqueiam o cálculo), depois **2, 7, 4, 5 e 6**.
- **Q98-3 (redação corrigida): "seguir recomendação".** A redação original ("retirar a pergunta 7 (N630A 27 e 28)") apontava para a pergunta errada: a dúvida do N630A 27 e 28 já havia saído da lista (seção 5) e a pergunta 7 de hoje é o percentual 0,348 da P500 18200. Lido como: **(a)** a dúvida do N630A 27 e 28 **fica fora**, fechada com a leitura da planilha (a Q93-7, das linhas do imposto devido, continua com o contador); **(b)** a pergunta 7 (0,348) **permanece** na lista.

- **Q98-4 (28/10/2026): pergunta 8.** Incluída com o ponto 3 aprovado (Q134-6: "sim tem este erro no manual, considere com o P130/78"); os pontos 1 e 2 aguardam a Q132-5. Arquivo 08 gerado.

- **Q98-5 (29/10/2026): pergunta 9.** Incluída com a aprovação da Q135-6 ("Sim"), com o texto do documento 135, seção 8, e o arquivo 09 gerado (ordem de envio: 9 de 9).

**O envio à Receita continua sendo seu; nada foi enviado.** Neste documento só resta a aprovação dos pontos 1 e 2 da pergunta 8 (Q132-5, no documento 38).
