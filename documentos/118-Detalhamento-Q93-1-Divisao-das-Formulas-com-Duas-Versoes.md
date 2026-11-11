# Detalhamento da Q93-1: divisão das fórmulas com duas versões — Documento 118

> **Aplicado na revisão 24 (26/10/2026, documento 122, D-N365).** A carga das tabelas dinâmicas foi regerada com as 11 fórmulas divididas em 22 linhas, de 4.475 para 4.486 linhas, e a M350A 171 corrigida para `M350(344)`. A seção 9 (correção do registro) está superada: o que ela dizia que entraria na revisão 24 entrou, exceto o campo de atividade rural (Q93-6). Seguem abertas Q118-1 a Q118-3.

*Detalhamento pedido por Alberto em 26/10/2026 ("detalhar Q93-1"). A Q93-1 já foi respondida por você em 22/10/2026 (alternativa A, dividir em duas linhas com vigência); este documento mostra o que essa resposta faz, linha por linha, e **não é uma decisão nova**. Nada foi aplicado ao dicionário nem à carga: a divisão entra quando você mandar consolidar (revisão 24). As leituras que faço do texto das fórmulas são minhas, marcadas como tal; o manual da Receita não as explica, e o contador as confirma.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- A planilha da Receita (leiaute 12) traz **11 linhas da cadeia do lucro real** cuja fórmula tem duas versões escritas no mesmo texto: "Até 31/12/2025 …" e "A partir de 01/01/2026 …". A linha vale de 2015 a 9999, e o ERP não consegue executar um texto com duas fórmulas dentro.
- Sua resposta de 22/10/2026 foi **dividir cada uma em duas linhas**, cada qual com a sua vigência: a primeira de 01/01/2015 a 31/12/2025, a segunda de 01/01/2026 a 31/12/9999. São **22 linhas no lugar de 11**.
- **Não há campo novo.** A estrutura que já existe (`Cad_Ecf_Tabela_Dinamica_Linha` com `Vigencia_Inicio`, `Vigencia_Fim` e `Motivo_Vigencia`) comporta a divisão. A carga dessa tabela vai de **4.475 para 4.486 linhas**.
- A divisão é a **única alteração** que a carga faz no que a Receita publicou, e fica registrada no `Motivo_Vigencia`. As fórmulas em si não são alteradas: cada versão é o texto da Receita, sem os rótulos "Até …" e "A partir de …".
- Achei **um ponto novo** ao ler as versões de 2026: a N630A linha 18 cita uma linha `16.001` que não existe na própria tabela (seção 6). Segue a mesma regra da Q93-2: o motor acusa e o contador decide.

# 2. A pergunta e a resposta

**Q93-1 (documento 93, seção 4.1).** As fórmulas com duas versões podem ser tratadas de três jeitos: (A) duas linhas separadas, cada uma com a sua vigência, sem campo novo; (B) uma entidade de fórmula com vigência; (C) o motor lê o texto "Até … A partir de …" na hora de executar. A recomendação era A.

**Resposta (22/10/2026): A.** Registrada na seção 7 do documento 93. O que este documento acrescenta é o detalhe do que muda em cada fórmula e como o motor escolhe a versão.

# 3. As 11 linhas e o que muda em 2026

Todas as 11 estão nas abas N610, N620 e N630 (variantes A, B e C), com vigência original de 01/01/2015 a 31/12/9999. A coluna "o que muda" é a minha leitura do texto das duas versões, sem a norma ao lado; **não executei as versões de 2026** (o teste com os seus dois arquivos de ECF, documento 93 seção 9, cobriu só as versões de 2025).

| Tabela e linha | O que a linha é | O que muda na versão de 01/01/2026 (leitura minha) |
|---|---|---|
| N610 linha 10 | Isenção (valor derivado do subtotal da linha 9) | O fator passa de 1,00 para 0,90 sobre o subtotal. |
| N610 linha 15 | Isenção (subtotal da linha 14) | O fator passa de 1,00 para 0,9. |
| N610 linha 50 | Redução (subtotal da linha 49) | O fator passa de 0,75 para 0,75 × 0,9. |
| N620 linha 18 | (−) Isenção e redução do imposto, na estimativa mensal | A conta do limite soma de volta nove linhas de dedução (N620 7, 9, 11, 12, 13, 14, 15, 16 e 17) ao imposto antes de comparar com o benefício da N610 linha 76. |
| N620 linha 19 | (−) Redução por reinvestimento, na estimativa mensal | A base soma de volta as mesmas nove deduções, e o valor do reinvestimento (N610 linha 77) entra multiplicado por 0,90 quando é ele que limita. |
| N620 linha 26 | Imposto de renda devido no mês | Soma de volta as mesmas nove deduções ao resultado (as linhas 7 a 20 continuam sendo subtraídas, mas essas nove voltam). |
| N630A linha 17 | (−) Isenção e redução do imposto, lucro real (PJ em geral) | Como a N620 18: soma de volta dez linhas de dedução (N630 6, 8, 10 a 16 e 16.10) antes de comparar com o benefício. |
| N630A linha 18 | (−) Redução por reinvestimento, lucro real (PJ em geral) | Soma de volta as mesmas dez deduções e usa 0,9 × N610 linha 77 como teto. Cita a linha `16.001`, que não existe (seção 6). |
| N630A linha 26 | Imposto de renda a pagar (PJ em geral) | Soma de volta as mesmas dez deduções ao resultado. |
| N630B linha 23 | Imposto de renda a pagar (financeiras) | Soma de volta dez deduções (N630 6, 8 a 15 e 15.10). |
| N630C linha 23 | Imposto de renda a pagar (seguradoras e previdência aberta) | A mesma soma de volta da N630B. |

**Em palavras simples (leitura minha):** nas três linhas da N610, a isenção e a redução de 2026 valem 90% do que valiam (o 0,9 que aparece nas fórmulas). Nas linhas de imposto devido e de limite do benefício (N620 e N630), a versão de 2026 soma de volta ao imposto as deduções de incentivo listadas (cultura, alimentação do trabalhador, audiovisual, fundos da criança e do idoso, desporto, PRONON, PRONAS/PCD, licença-maternidade e paternidade, reciclagem), de modo que elas deixam de reduzir o imposto nesse cálculo. O desenvolvimento tecnológico (N620 10 e N630A 9) não está na lista de soma de volta. **Não verifiquei** qual dispositivo da LC 224/2025 ou da regulamentação gera cada soma de volta; quem confirma é o contador. O ERP não precisa dessa explicação para executar: ele executa o texto da fórmula vigente na data.

# 4. O que a divisão produz

Para cada uma das 11 linhas, a carga grava duas linhas com o mesmo código, o mesmo tipo (`Tipo_Linha`), o mesmo formato e a mesma descrição, mudando só a fórmula e a vigência:

| | Versão 1 | Versão 2 |
|---|---|---|
| `Vigencia_Inicio` | 01/01/2015 | 01/01/2026 |
| `Vigencia_Fim` | 31/12/2025 | 31/12/9999 |
| `Formula` | o texto sob "Até 31/12/2025", sem o rótulo | o texto sob "A partir de 01/01/2026", sem o rótulo |
| `Motivo_Vigencia` | "Linha dividida na carga: a fórmula publicada trazia duas versões (até 31/12/2025 e a partir de 01/01/2026)" | o mesmo texto, indicando a versão de 2026 |

Exemplo, N610 linha 50 (redução): a versão 1 fica `N610(49)*0,75` com vigência até 31/12/2025; a versão 2 fica `N610(49)*0,75*0,9` a partir de 01/01/2026.

**Sobre a vigência inicial da versão 1:** mantive 01/01/2015, a data que a planilha traz para a linha. Isso não diz que a fórmula "até 2025" era igual em 2015 a 2024; diz só que a planilha da Receita não separa esse período, e a carga não inventa o que ela não publica.

**Já existe um caso parecido na carga.** A P200 linha 24 (resultados não tributáveis de cooperativas, lucro presumido) já está em duas linhas, uma de 2015 a 2025 e outra a partir de 2026; foi a própria planilha que as publicou separadas. A divisão das 11 linhas segue o mesmo desenho.

**Quantas linhas:** 4.475 − 11 + 22 = **4.486** na cadeia do lucro real. As duas linhas do lucro presumido do documento 99 (P200 26 e P400 21, ver a seção 5) somam mais duas se você as aprovar na consolidação.

**O que não muda no dicionário:** nenhuma entidade, nenhum campo, nenhum domínio. A divisão acontece na **carga** da tabela, e o dicionário (922 entidades, 9.998 campos) fica igual por causa dela.

# 5. As três linhas fora da cadeia que também têm duas versões

Na mesma tabela de carga há três linhas com o mesmo padrão que **não** estão entre as 11 da cadeia do lucro real:

| Linha | O que é | Onde está tratada |
|---|---|---|
| P200 linha 26 | Base de cálculo do imposto sobre o lucro presumido | Documento 99 (cadeia do lucro presumido da ECF): divisão proposta lá, mesma regra. |
| P400 linha 21 | Base de cálculo da CSLL no lucro presumido | Documento 99, idem. |
| S200 linha 90 | Total de tributos a pagar (TEF e SAF), vigência a partir de 01/01/2021 | **Nenhum documento até agora.** A versão de 2026 soma a linha 55 ao total (`S200(40)+S200(55)`). |

A S200 linha 90 vira a pergunta **Q118-1** (seção 7): ela segue a mesma regra assim que o motor do TEF e SAF entrar.

# 6. Ponto novo: referência a uma linha que não existe

Na versão de 01/01/2026 da N630A linha 18, a fórmula cita `N630("16.001")`. A aba N630A tem as linhas 16, 16.01 a 16.07, 16.10, 16.15 e 16.50, mas **não tem a 16.001**. Pode ser erro de digitação da Receita, parecido com o `M(344)` da Q93-2 e o `FIM_SE` que falta na N660 linha 3 (documento 93, seção 9).

Mantenho como publicado. Como nos outros erros da planilha, o motor **acusa** a linha e **não calcula** até o contador dizer qual é a leitura certa; eu não escolho (não sei se é a 16.01, a 16.10 ou outra) e a carga não corrige o que a Receita publicou. Vira a **Q118-2**.

As outras referências das 11 fórmulas, nas duas versões, existem nas suas tabelas (conferi todas as citações de linha contra a carga).

# 7. Como o motor escolhe a versão (leitura minha)

O motor carrega as linhas vigentes na **data de início do período apurado** (`Competencia_Inicio` da apuração, o `DT_INI` do registro 0000 da ECF). Para o ano-calendário 2025, vale a versão 1; para períodos iniciados a partir de 01/01/2026, a versão 2. Os períodos da ECF (anual, trimestres e meses da estimativa) começam e terminam dentro do ano-calendário; por isso não conheço caso de período que atravesse a virada de 31/12/2025 para 01/01/2026, e se existir é pergunta ao contador. A ECF do ano-calendário 2026 usa a versão 2 inteira.

**Cuidado com a estimativa de 2026:** o mês de janeiro de 2026 começa em 01/01/2026 e usa a versão 2, mesmo que a empresa tenha a ECF do ano 2025 ainda em preparo. A data que decide é a do período apurado, não a data em que o contador gera a ECF.

# 8. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q93-1 | **Respondida em 22/10/2026:** alternativa A. Este documento só detalha. | Entra na revisão 24 (carga de 4.486 linhas). |
| Q118-1 | A S200 linha 90 (TEF e SAF) também é dividida em duas linhas na carga, pela mesma regra, quando o motor do TEF e SAF entrar? | Sim, mesma regra, sem campo novo. Não depende de nada além da sua decisão. |
| Q118-2 | A referência `16.001` da N630A linha 18 (versão de 2026): o contador confirma qual é a linha certa, ou a Receita já corrigiu em planilha mais nova? | O motor acusa a linha e não calcula até a resposta; a carga mantém o texto publicado. |
| Q118-3 | O contador confere as 11 fórmulas de 2026 contra a lei (a soma de volta das deduções e o fator 0,90), já que meu teste só cobriu 2025? | Faz parte da Q93-4 (versões de 2026 não testadas); sem nada novo a desenhar. |

# 9. Estado do que você respondeu em 22/10/2026 (correção do registro)

Ao preparar este detalhe achei **um erro meu de registro**: a seção 1.4 (Q93) e a seção 1.2 (Q96) do documento 38 estavam mostrando como abertas perguntas que você já respondeu em 22/10/2026 (Q93-1, Q93-2, Q93-3, Q93-5, Q93-5b, Q93-5d, Q93-6 e as Q96-1 a Q96-17), porque reconstruí o documento 38 em 23/10 a partir de uma versão anterior. As revisões 21, 22 e 23 do dicionário também **não aplicaram** o que você aprovou nos documentos 93 e 96 (por exemplo, as entidades `Mov_Ecf_Apuracao_Linha_Valor`, com 10 campos, e `Mov_Ecf_Escolha_Contador_Ano`, com 8, e o campo `Base_Estimativa`). Eu não as listei como pendentes de aplicação.

O que está **realmente aberto** da Q93: Q93-3b (rastro do cálculo ou composição pela Parte A), Q93-7 (quais linhas são o imposto devido) e Q93-8 (se o ERP só soma ou também sugere lançamentos). A Q93-4 segue com a confirmação do contador para `CREDITO`, as variantes não testadas e as versões de 2026. As demais estão respondidas e entram na **revisão 24**, se você mandar consolidar. Já corrigi os documentos 38, 113 e 117.
