# Planilha das Tabelas Dinâmicas do Leiaute 12 (24/09/2026): Conferência da Carga e a Pergunta 10 — Documento 193

*Você enviou, sem mensagem, a planilha "Tabelas_Dinamicas_ECF_Leiaute_12_24_09_2026_AC_2025_SIT_ESP_2026.xlsx". Ela é a parte (1) da **Q179-3**. Li as 77 abas de tabelas (27.844 linhas), comparei com a carga de tabelas dinâmicas do ERP, reconferi as fórmulas das perguntas 1 a 9 do documento 179 e **fechei a pergunta 10**, que era rascunho. É **proposta**: **nada foi alterado no dicionário nem na carga** (revisão 34: 1.135 entidades e 12.739 campos; com os documentos 189 a 192 aprovados, 1.137 e 12.759).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **A carga do ERP confere com a planilha.** As 55 tabelas de cálculo da carga têm 4.477 linhas na planilha e 4.488 na carga; a diferença se explica por três fatos: **13 fórmulas com duas versões** divididas em duas linhas (4.475 mais 13), **1 linha de cabeçalho repetida** na aba `ParteB_Padrao` e **1 linha duplicada** na `P400` linha 20 (seção 3). As fórmulas de todas as linhas conferem, salvo as 13 divisões e a M350A 171, que corrigi de propósito (D-N365).
- **As perguntas 1 a 9 do documento 179 estão certas.** Cada fórmula transcrita nelas aparece na planilha com o mesmo texto, e as contagens (1 `FIM_SE` a menos no N660 3; parênteses a mais ou a menos em 8 linhas) **batem exatamente**. Só a **pergunta 5 cresce**: a planilha usa mais quatro funções que o manual não define (`PERIODO_PRIMEIRO`, `PERIODO_ULTIMO`, `ARRED` e `ANO`).
- **Pergunta 10 fechada, com sete pontos** (seção 5). Ela corrige duas leituras antigas (D-N402): o N610 3 **não é a única** linha com `N500(1)` na condição (são 5 de 22), e as linhas `N660(50)` a `N660(57)` **não existem** no N660.
- **Achado novo (pergunta 28 proposta):** a `P400` linha 20 aparece **duas vezes** na planilha, as duas desde 01/01/2015 e sem fim, uma editável e outra de cálculo, **as duas sem fórmula**. A irmã `P200` linha 24 está certa: editável até 31/12/2025 e de cálculo, com fórmula, desde 01/01/2026.
- **Falta ainda a planilha do leiaute 11** (2025): é ela que traz o texto de 2024 das N620 18, N620 19 e N630A 18 (Q152-4), que **seguem provisórias**. A Q179-3 fica com a parte (2).
- **Perguntas para você:** Q193-1 a Q193-3 (seção 7). Os textos prontos para colar estão no .zip que acompanha este documento.

# 2. O que a planilha trouxe

| Item | Valor |
|---|---|
| Abas | 78: o índice e 77 tabelas |
| Linhas (sem o cabeçalho de cada aba) | 27.844 |
| Abas que são tabelas de cálculo e estão na carga | 55 (4.477 linhas na planilha) |
| Abas fora da carga de linhas | 23: os planos referenciais (`L100A`, `L100B`, `L100C`, `L300A`, `L300B`, `L300C`, `P100A`, `P100B`, `P150A`, `P150B`, `S100`, `S150`, `U100A` a `U100E`, `U150A` a `U150E`) e `PARTEB_PARTEA` |

Os 23 itens fora da carga **não têm fórmula de cálculo**; são listas de contas referenciais e o relacionamento da Parte B. **Não os conferi aqui.**

# 3. A carga contra a planilha

| Ponto | Resultado |
|---|---|
| Linhas só na planilha, entre as 55 tabelas da carga | **Nenhuma** |
| Linhas só na carga | **Nenhuma** (as 126 da `ParteB_Padrao` estão na planilha como 127 linhas, e a 127ª é o cabeçalho repetido) |
| Fórmulas com texto idêntico | **4.333** |
| Fórmulas com duas versões ("Até 31/12/2025" e "A partir de 01/01/2026") divididas na carga | **13** (26 linhas): N610 10, 15 e 50; N620 18, 19 e 26; N630A 17, 18 e 26; N630B 23; N630C 23; P200 26; P400 21 |
| Fórmula corrigida de propósito | M350A 171: `M(344)` virou `M350(344)` (D-N365) |
| Contagem | 4.477 menos 1 (cabeçalho repetido) menos 1 (P400 20 duplicada) mais 13 = **4.488** |

**Linha duplicada na P400 linha 20.** A planilha tem duas linhas com o código 20, as duas com o nome "(-) Resultados Não Tributáveis de Sociedades Cooperativas", as duas com início em 01/01/2015, **sem data final** e **sem fórmula**; uma é do tipo "E" (editável) e a outra "CNA" (cálculo não alterável). A P200 linha 24, equivalente, tem o tipo "E" até 31/12/2025 e o "CNA" desde 01/01/2026 com a fórmula `SE (0030.COD_NAT() = "2143") ENTAO (...)`. **A carga ficou com uma linha só** (editável, de 2015 a 9999), que é a leitura segura. Proponho levar à Receita (pergunta 28).

# 4. As perguntas 1 a 9 do documento 179, reconferidas

| Nº | Assunto | Resultado da conferência |
|---|---|---|
| 1 | M350A 171 e M350R 345 | **Confere:** `M350(169) - M350(170) + M(344)` e `M350(343) - M350(344) + M(170)` |
| 2 | N660 3 e parênteses | **Confere exatamente:** o N660 3 tem 3 `SE` e 2 `FIM_SE`, e é o único; os parênteses não fecham em 8 linhas (N600 24 e 36 com um `)` a mais; P200 25210 a 25250 com um `)` a mais; P300 9 com 25 `(` e 23 `)`) |
| 3 | CSLL só com 1, 3 e 5 | **Confere:** N660 3, N670 2 e P500 2 tratam o 1 e o 3 e põem 15% no resto; T181 6 e U182 2 tratam o 1 e o 5 (e o 3 no ramo anterior a 2021). **As orientações do N670 2 citam 7 e 8**, que a fórmula não trata |
| 4 | 0020, campo 2 | É do manual, não da planilha (documento 192, seção 2) |
| 5 | Funções não definidas | **Confere e cresce:** as sete funções do texto aparecem na planilha; **mais quatro** não estão no manual: `PERIODO_PRIMEIRO` (P200, P300, P400, P500), `PERIODO_ULTIMO` (as mesmas quatro), `ARRED` (P300, P500) e `ANO` (P500) |
| 6 | Y520 | É do manual |
| 7 | P500 18.200 | **Confere:** o terceiro termo usa `0,348`; P200 25250 e P400 20230 usam `0,384` |
| 8 | P130 | **Confere:** o rótulo 73 é "DEMAIS ATIVIDADES"; as linhas 74 a 77 dizem "beneficiado com a redução"; a linha 78 as soma; a orientação da linha 6 cita `P130/68` e as outras oito (15, 24, 33, 42, 51, 60, 69 e 78) citam `P130/78` |
| 9 | P200 26 e P400 21 de 2026 | **Confere:** o `SE` testa a base sem o adicional e o adicional só entra no `ENTAO` |

# 5. Pergunta 10 fechada (substitui o rascunho do documento 179)

**Assunto sugerido:** Leiautes (tabelas dinâmicas). Sete pontos, todos na planilha de 24/09/2026. O que mudou desde o rascunho: a planilha do leiaute 11 não é necessária para estes sete (as N620 18 e 19 e a N630A 18 ficam de fora, seção 6).

| Nº | Linha | Fórmula ou situação na planilha | O que observamos |
|---|---|---|---|
| 1 | N660 5 a 9 | `SE (N600(50) <= 0) ENTAO 0 SENAO SE (0020.IND_ALIQ_CSLL() = "1") ENTAO N600(50) * 0,09 SENAO SE (0020.IND_ALIQ_CSLL() = "3") ENTAO N600(50) * 0,20 SENAO N660(50) * 0,15 FIM_SE FIM_SE FIM_SE` (a linha 5; as 6 a 9 usam 54, 55, 56 e 57) | A condição e os dois primeiros ramos usam o N600; o **último usa o N660**, que **não tem as linhas 50 e 54 a 57**. Na linha 9, a orientação cita `N600/10`, e a fórmula usa `N600(57)` |
| 2 | N610 3, 75.12, 75.52, 75.62 e 75.72 ("Adicional") | A condição é `SE (N500(1) < N600(48))` | As outras **17** linhas "Adicional" (8, 13, 18 ... 73, 75.22, 75.32 e 75.42) usam `M300(175) + M300(349) < N600(48)` |
| 3 | N660 12.01 | Tipo "CNA", **sem fórmula** | O N660 12 soma `N660("12.01";"A01":PERIODO_ANTERIOR())`, então nada alimenta a linha 12 |
| 4 | N670 12 | Tipo "E" (editável), **com fórmula** (`N610(36) * 0,09`, 0,20 ou 0,15) | É a única das **25 linhas editáveis** do N670 com fórmula |
| 5 | N670 21 | `N670(4) - SOMA(N670(6:"20:99"))` | O limite vem com dois-pontos; as outras linhas usam ponto (`"17.99"`, `"20.99"`) |
| 6 | M350R 267 | `SOMA (M350(“181.01”:”266.99”))` | A soma começa em **181.01**, código que **não existe** no M350R (a 181 é rótulo e a primeira linha é a 181.02); o M300R 267 usa `SOMA(M300(182:"266.01"))` e o M350A e o M300A somam de 6 a `"92.99"` |
| 7 | N610 75.60 | `SE (N600(51.4Y00) > 0) ENTAO N600(51.400) SENAO 0 FIM_SE` | O código tem um **Y** e a segunda referência vem sem aspas; a linha existe como 51400 |

**Texto para colar:** está no arquivo `Pergunta-10.txt` do .zip. Ele pergunta, para cada um dos sete pontos, a fórmula correta ou a intenção e, se for erro, a versão em que a planilha será corrigida.

**Leitura adotada enquanto não houver resposta:** o motor segue a fórmula **como publicada** e avisa o contador (Q139-2). Para o ponto 5, o ERP lê `"20.99"` com aviso, como já fazia.

# 6. O que ainda falta da Q179-3

- **Planilha do leiaute 11 (2025):** traz o texto de 2024 das **N620 18, N620 19 e N630A 18** (Q152-4; `PENDENTE_Formulas_2024.csv` continua com as três linhas provisórias). A planilha de 24/09/2026 só traz a versão "até 31/12/2025", que o ERP já usa para 2025. Sem a do leiaute 11, **não consigo dizer o que mudou entre 2024 e 2025** nessas três linhas, e por isso elas **não entram** na pergunta 10.
- **Tabelas do leiaute 11:** a planilha de 2024 tem as 372 fórmulas que o documento 139 usou; se você tiver o arquivo, basta enviá-lo.

# 7. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q193-1** | Aprovar o texto fechado da **pergunta 10** (sete pontos, seção 5) para enviar à Receita no lugar do rascunho do documento 179? | **Sim** |
| **Q193-2** | Acrescentar as quatro funções (`PERIODO_PRIMEIRO`, `PERIODO_ULTIMO`, `ARRED` e `ANO`) à **pergunta 5**? | **Sim** |
| **Q193-3** | Incluir a **pergunta 28** (P400 linha 20 duplicada, sem fórmula)? | **Sim** |

Com a Q192-7 aprovada, as perguntas novas ao conjunto do documento 179 são a **27** (registro 0000, documento 192) e a **28** (P400 20, aqui). O envio é seu; nada foi enviado.

# 8. Perguntas para o contador

Nenhuma nova. A confirmação das leituras do motor para as sete linhas da pergunta 10 já está na Q139-2 (documento 188).

# 9. Contagem

**Nenhuma entidade nem campo novo**: este documento só confere a carga e fecha texto de pergunta à Receita. Contagem aprovada inalterada: **1.137 entidades e 12.759 campos** (documentos 189 a 192).

# 10. Limites do que eu li

- Comparei as fórmulas por **texto normalizado** (espaços iguais); não executei nenhuma fórmula. A conferência cobre as **55 tabelas de cálculo**; as 23 abas de planos referenciais e a `PARTEB_PARTEA` **não foram conferidas**.
- As contagens de `SE`, `FIM_SE` e parênteses foram feitas por programa, em **todas** as fórmulas das 55 tabelas; os parênteses dentro de textos com aspas tipográficas contam como estão.
- **Não sei** qual fórmula o PVA aplica de fato, nem se a planilha publicada no Portal já foi corrigida depois de 24/09/2026.
- As leituras "o último ramo do N660 5 a 9 é erro de digitação" e "o código `51.4Y00` é erro de digitação" são **minhas**; a pergunta à Receita as trata como dúvida.
- Nenhuma recomendação foi confirmada pelo contador.
