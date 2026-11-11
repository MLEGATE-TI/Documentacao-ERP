# Cálculo da Cadeia do Lucro Real da ECF (M300, M350 a N670) — Documento 93

> **Aplicado na revisão 24 (26/10/2026, documento 122, D-N365).** Entraram no dicionário as entidades `Mov_Ecf_Apuracao_Linha_Valor` (10 campos) e `Mov_Ecf_Escolha_Contador_Ano` (8 campos; a chave primária ficou `ID_Escolha_Contador_Ano`), o campo `Base_Estimativa` em `Mov_Apuracao_Irpj_Csll` e o valor `indicador_aliquota_csll_ecf` em `Cad_Classe_Sistema.Dominio`; a carga das tabelas dinâmicas foi regerada com as 11 fórmulas divididas (4.486 linhas) e a M350A 171 corrigida para `M350(344)`. **Não entrou:** o campo do indicador de atividade rural (Q93-6, desenho por escrever). Seguem abertas Q93-3b, Q93-7 e Q93-8. A M350R 345 (`M(170)`) ficou como publicada: pergunta Q122-1 no documento 38. Onde o texto abaixo diz "proposta, nada consolidado", vale esta nota.

*Atualizado em 22/10/2026 com as suas respostas (Q93-1, Q93-2, Q93-3, Q93-5 e Q93-6), o teste com os seus dois arquivos de ECF (Q93-4) e o desenho da entidade do indicador da CSLL (seção 5.6). Desenho para aprovação, a partir da sua resposta de 21/10/2026: "o ERP tem que calcular estes blocos". Proposta, nada consolidado: o dicionário e a carga só mudam depois da sua aprovação e do "consolidar" (revisão 19). Os nomes de campo abaixo são meus, não seus. As leituras que faço das funções da planilha estão marcadas como minhas, porque o manual não as define.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Você decidiu três coisas (registradas como **D-N332** e **D-N333** no documento 14):

# 1. O ERP **calcula** os blocos M300, M350 e N630 da ECF. Na pergunta de alcance você escolheu a **cadeia do lucro real**: tudo o que alimenta o IRPJ e a CSLL, de M300 e M350 até N500, N600, N610, N620, N630, N650, N660 e N670 (18 abas, 3.329 linhas, **300 fórmulas**). 2. O cálculo **interpreta a fórmula guardada no cadastro** (`Cad_Ecf_Tabela_Dinamica_Linha`), em vez de ficar programado. Quando a Receita mudar uma alíquota ou uma regra, basta nova carga. 3. O segmento passa a existir também nas abas de linhas M300, M350 e N630 (resposta à Q91-3).

O que descobri ao ler as 300 fórmulas e o que falta decidir:

- A planilha **já traz o cálculo** nas linhas do tipo "cálculo" (299 linhas, 300 com fórmula) numa linguagem própria da Receita (SE/ENTAO/SENAO/FIM_SE, SOMA, referências do tipo `M300(169)`). As outras 2.990 linhas são "editáveis": valores que vêm de lançamento, de importação ou do contador.
- **11 fórmulas trazem duas versões no mesmo texto** ("Até 31/12/2025 … A partir de 01/01/2026 …"), por causa da LC 224/2025. Uma linha só, com vigência 2015 a 9999, não dá para executar sem separar (seção 4, Q93-1).
- **2 fórmulas têm erro de digitação na planilha** (`M(344)` no lugar de `M350(344)`, na M350A linha 171 e na M350R linha 345). A carga não corrige o que a Receita publicou; o motor deve acusar e o contador decide.
- **O manual não define as funções** `T_DRE`, `DEBITO`, `CREDITO` e `MESES_PERIODO` (nem as de período). Minha leitura de cada uma está na seção 3, e **precisa de um arquivo de ECF real com os valores calculados para conferir** (Q93-4).
- O ERP precisa de **uma tabela de valores por linha** da apuração. Hoje só guarda o total por imposto (`Mov_Apuracao_Irpj_Csll_Item`), o que não basta para gerar o M300, o M350 e o N630 linha a linha (seção 5).

# 2. O que entra no cálculo

| Registro | Abas | Linhas | Fórmulas | Papel |
|---------------------------|-------------|------|--------|----------------------------------------------|
| M300 (lucro real, e-Lalur Parte A) | M300A, B, C, R | 1.495 | 28 | Do lucro contábil, somando adições e excluindo exclusões, ao lucro real |
| M350 (base da CSLL, e-Lacs Parte A) | M350A, B, C, R | 1.391 | 24 | O mesmo para a base da CSLL |
| N500 | N500 | 2 | 1 | Base do IRPJ depois da compensação de prejuízos |
| N600 | N600 | 81 | 42 | Lucro da exploração (lê o L300) |
| N610 | N610 | 119 | 118 | Isenção e redução do imposto (é a maior tabela de fórmulas) |
| N620 | N620 | 43 | 17 | IRPJ mensal por estimativa |
| N630 | N630A, B, C | 123 | 47 | IRPJ com base no lucro real |
| N650 | N650 | 2 | 1 | Base da CSLL depois da compensação de base negativa |
| N660 | N660 | 34 | 11 | CSLL mensal por estimativa |
| N670 | N670 | 39 | 11 | CSLL com base no lucro real |

**Cadeia de dependência (lida das referências das fórmulas):** L300 (resultado contábil no plano referencial) → M300 → N500 → N610 e N620 → N630; L300 → M350 → N650 → N660 e N670; N600 (lucro da exploração) alimenta o N610. Fora do escopo desta proposta, e já com fórmula na planilha: lucro presumido (P), TEF e SAF (S), T, U, V, X e Y (207 fórmulas), mais as 6 do L210 (213 fora da cadeia).

# 3. A linguagem das fórmulas

**Como a fórmula chama os dados:**

- `L300("3.01")`, `M300(169)`, `N630(3)`: valor de uma linha de outra tabela (ou da mesma) no período da apuração. O número é o código da linha; entre aspas, um código de conta do plano referencial.
- `SOMA(M300(6:"92.99"))`: soma de um intervalo de linhas. `SOMA(N620("20.01";"A01":PERIODO_ANTERIOR()))` soma a mesma linha em vários períodos (os meses A01 até o anterior).
- `0010.FORMA_TRIB()`, `0010.COD_QUALIF_PJ()`, `0010.FORMA_APUR()`, `0020.IND_ALIQ_CSLL()`, `0000.DT_INI()`: campos dos registros de abertura da ECF.

**Funções e o que acho que fazem** (minha leitura, a confirmar):

| Função | Usos | Leitura |
|------------------------------------------|-----------|-----------------------------------------------|
| `SE … ENTAO … SENAO … FIM_SE`, `E`, `OU`, comparações | 322 | Condicional normal |
| `SOMA(intervalo)` | 84 | Soma de linhas de uma tabela, por intervalo de códigos ou de períodos |
| `MESES_PERIODO()` | 96 | Número de meses do período, para o limite do adicional do IRPJ (R$ 20.000 por mês). **A conferir na estimativa**, onde o período pode ser acumulado desde janeiro |
| `PERIODO_ATUAL()`, `PERIODO_ANTERIOR()` | 8 | Código do período (A00, T01 a T04, A01 a A12) |
| `T_DRE(...)` | 11 | **Não definida no manual.** Leio como a conversão do saldo das contas de resultado para o sinal de lucro (receita positiva, despesa negativa) |
| `DEBITO(x)`, `CREDITO(x)` | 12 e 9 | **Não definidas.** Leio `DEBITO(x)` como "x se for negativo, senão zero" (parte devedora) e `CREDITO(x)` como a parte credora |
| `BAL_RED(período)` | 6 | Indica se o mês foi apurado por balanço ou balancete de redução ("B") ou por receita (estimativa comum) |
| `ARRED`, `CONTAR`, `CASO`, `IGUAL`, `PERIODO_ULTIMO`, `PERIODO_PRIMEIRO` | 0 na cadeia | Aparecem só nas abas fora do escopo (lucro presumido, S, T, U, X, Y); entram com o motor dessas obrigações |

O motor é um interpretador desta linguagem, de ordem pequena (a lista acima cobre as 300 fórmulas da cadeia; contei só as chamadas de função das fórmulas dessas 18 abas), com avaliação por dependência: uma linha só é calculada depois das que ela cita.

# 4. O que a leitura das fórmulas pede decidir

## 4.1 Fórmulas com duas versões (11 linhas)

N610 linhas 10, 15 e 50; N620 linhas 18, 19 e 26; N630A linhas 17, 18 e 26; N630B linha 23; N630C linha 23. Cada uma traz o texto "Até 31/12/2025 …" e "A partir de 01/01/2026 …" na mesma célula, com vigência 2015 a 9999.

**Alternativas:** (A) guardar as duas versões como linhas separadas, cada uma com a sua vigência (a estrutura já permite: a chave da linha tem `Vigencia_Inicio`); (B) criar uma entidade de fórmula com vigência; (C) o motor lê o texto "Até … A partir de …" na execução.

**Recomendação: A**, sem campo novo. A carga divide cada uma dessas 11 linhas em duas (até 31/12/2025 e a partir de 01/01/2026) e marca no `Motivo_Vigencia` que foi dividida porque a fórmula trazia duas versões. É a única alteração que a carga faz no que a Receita publicou, e fica registrada. Resultado: **22 linhas no lugar de 11**, e a carga de linhas passa de 4.475 para 4.486.

**Q93-1.** Aceita a alternativa A?

## 4.2 Erros de digitação na planilha (2 linhas)

M350A linha 171 e M350R linha 345 têm `M(344)` no lugar de `M350(344)`. Mantenho como publicado e o motor **acusa** a linha e **não calcula** até o contador dizer qual é a leitura certa (provavelmente M350(344)).

**Q93-2.** O contador confirma a leitura M350(344), ou a Receita já corrigiu em planilha mais nova?

# 5. O que o dicionário ganha

Hoje existem `Mov_Apuracao_Irpj_Csll` (um registro por período), `Mov_Apuracao_Irpj_Csll_Item` (um por imposto, com base, alíquota, valor, deduções, compensação e valor a pagar) e `Mov_Lalur_Lancamento_Parte_A` (os lançamentos da Parte A). Falta o **valor de cada linha**.

## 5.1 `Mov_Ecf_Apuracao_Linha_Valor` (entidade nova, 10 campos)

Um valor por linha de tabela dinâmica, por apuração. É o que o ERP calcula e o que gera o M300, o M350 e os registros N. *Atualização de 22/10/2026: a tabela abaixo tem 10 campos (o texto de 21/10 dizia 9, por contar `ID_Usuario_Alteracao` e `Data_Hora_Alteracao` como um só). O campo `Valor` passa a se chamar `Valor_Com_Sinal` e `Valor_Calculado` a `Valor_Calculado_Com_Sinal`, pela regra do sufixo (D-N344: sem indicador de natureza, aceita sinal). Falta a composição das linhas, que você pediu guardar (Q93-3): ver a pergunta Q93-3b na seção 7.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------------|----------------------------------|----------------------------------------|
| `ID_Apuracao_Linha_Valor` | identificador | --- |
| `ID_Apuracao_Irpj` | referência (`Mov_Apuracao_Irpj_Csll`) | O período apurado. O código do período da ECF (A00, T01 a T04, A01 a A12) sai de `Tipo_Apuracao` e das competências; não é campo. |
| `ID_Tabela_Linha` | referência (`Cad_Ecf_Tabela_Dinamica_Linha`) | A linha, na versão vigente no período. |
| `Valor_Com_Sinal` | número | O valor da linha. |
| `Origem` | enumeração {calculo, lancamento, manual, importado_ecf} | De onde veio: fórmula, soma dos lançamentos da Parte A, digitado pelo contador, ou importado de uma ECF. |
| `Valor_Calculado_Com_Sinal` | número, opcional | O que a fórmula deu, quando o contador alterou o valor; permite mostrar a diferença. |
| `Eh_Alterado` | booleano | Linha do tipo "cálculo alterável" ou "editável" com valor diferente do calculado. Linha "não alterável" nunca é alterada. |
| `Motivo_Alteracao` | texto, opcional | Obrigatório quando `Eh_Alterado`. |
| `ID_Usuario_Alteracao` e `Data_Hora_Alteracao` | referência (`Cad_Usuario`), opcional; data e hora, opcional | Quem alterou e quando (padrão de confirmação da Fase 0). |

Regra do tipo da linha (já na carga, campo `Tipo_Linha`): **rótulo** (40 linhas) não tem valor; **cálculo não alterável** (150) o ERP calcula e ninguém muda; **cálculo alterável** (149) o ERP calcula e o contador pode mudar, com motivo; **editável** (2.990) vem do lançamento da Parte A ou é digitada. A chave de negócio é a apuração mais a linha.

## 5.2 Campo novo em `Mov_Apuracao_Irpj_Csll`

`Base_Estimativa`, enumeração {receita_bruta, balancete_reducao}, opcional, só para `Tipo_Apuracao = estimativa_mensal`. É o que a função `BAL_RED` lê: hoje o dicionário diz que "estimativa mensal e balancete de suspensão ou redução ficam em estimativa_mensal", sem separar as duas.

## 5.3 O que o perfil e a apuração já dão às fórmulas (sem campo novo)

| Dado que a fórmula pede | De onde vem |
|-------------------------------------|---------------------------------------------------------------|
| `0010.FORMA_TRIB` | `ID_Forma_Tributacao_Ecf` do perfil (revisão 18) |
| `0010.COD_QUALIF_PJ` | `ID_Segmento_Plano_Referencial` do perfil (revisão 18) |
| `0010.FORMA_APUR` (A ou T) | `Forma_Apuracao_Irpj` do perfil (anual_por_estimativa ou trimestral) |
| `0020.IND_ALIQ_CSLL` (1, 3, 4, 7 ou 8) | **Escolha do contador** para a ECF do ano, guardada na entidade da seção 5.6 (Q93-5, respondida em 22/10/2026). Não há mapeamento automático a partir de `ID_Segmento_Csll` |
| `0000.DT_INI` | `Competencia_Inicio` da apuração |
| `L300(conta)` | Saldo da conta contábil mapeada ao plano referencial (`Cad_Conta_Contabil_Referencial`), no período |

## 5.4 Segmento nas abas de linhas (Q91-3, respondida)

`Cad_Ecf_Tabela_Dinamica.ID_Segmento` (já existe desde a revisão 18) passa a ser preenchido também nas abas M300A, B e C, M350A, B e C e N630A, B e C (PJ em geral, financeiras, seguradoras e previdência aberta). A forma de tributação dessas abas é lucro real e a finalidade não se aplica. As demais abas da cadeia (N500, N600, N610, N620, N650, N660, N670) têm uma só versão e ficam sem segmento. A atividade rural (M300R e M350R) fica para a Q93-6.

## 5.5 Contagem se tudo for aprovado

*Contagem do texto de 21/10/2026, sobre a revisão 18. A contagem sobre a revisão 20 está na seção 5.6.*

| | Revisão 18 | Com este documento |
|------------------------------------|-------------|---------------------------------------------------|
| Entidades | 907 | 908 |
| Campos | 9.765 | 9.775 (9 da entidade nova e 1 em `Mov_Apuracao_Irpj_Csll`) |
| Campos de referência (FK) | 2.627 | 2.630 |
| Linhas da carga de tabelas dinâmicas | 4.475 | 4.486 |

## 5.6 Entidade nova: `Mov_Ecf_Escolha_Contador_Ano` (Q93-5 e Q93-5d)

**O que você decidiu (22/10/2026):** o contador seleciona o `IND_ALIQ_CSLL` do registro 0020 no momento de fazer a ECF do período, porque o indicador pode mudar a cada ano e só nesse momento ele sabe o que preencher. Por isso **não há mapeamento** do segmento para o indicador, e a entidade `Cad_Ecf_Indicador_Aliquota_Csll` que eu tinha proposto saiu. Você aprovou criar a entidade abaixo ("ok gerar esta entidade") e respondeu **sim** à Q93-5d, de modo que o `IND_QTE_SCP` entra nela, informado pelo contador por ano. Como ela passa a guardar mais de um campo do registro 0020, **mudei o nome** de `Mov_Ecf_Indicador_Aliquota_Csll` para `Mov_Ecf_Escolha_Contador_Ano`; o nome é meu e você pode trocar. O padrão é o de `Mov_Ecf_Perfil_Indicador` (uma linha por empresa e ano-calendário). **A lista de campos é minha** e você a vê aqui pela primeira vez.

Contabilidade & Fiscal, sem vigência (é movimento do ano, não parâmetro). Uma linha por empresa e ano-calendário.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------------------|----------------------------------------|
| `ID_Ecf_Indicador_Aliquota_Csll` | identificador | --- |
| `ID_Empresa` | referência (`Cad_Empresa`) | A empresa. Identidade, com o ano. |
| `Ano_Calendario` | número | O ano da ECF. Identidade, com a empresa. |
| `ID_Indicador_Aliquota_Csll` | referência (`Cad_Classe_Sistema`, domínio = `indicador_aliquota_csll_ecf`) | O valor que o contador escolheu para o campo `IND_ALIQ_CSLL` do registro 0020. Domínio fechado com os cinco valores do leiaute 12: 1 (9%), 3 (20%), 4 (15%), 7 (9% e 12%) e 8 (15% e 17,5%), com a alíquota na descrição de cada valor. Os valores 5 e 6 (de 2021) não entram. Código novo da Receita é linha nova do domínio. |
| `Quantidade_Scp` | número, opcional | O que o contador informa no campo `IND_QTE_SCP` do registro 0020: a quantidade total de SCP do sócio ostensivo (3 posições no leiaute). Vazio quando a empresa não é sócia ostensiva de SCP, como nos seus dois arquivos de teste. Sem sinal. |
| `ID_Usuario_Confirmacao` | referência (`Cad_Usuario`) | Quem escolheu (padrão de confirmação da Fase 0). |
| `Data_Hora_Confirmacao` | data/hora | Quando escolheu. |
| `Observacao` | texto, opcional | Motivo da escolha, por exemplo mudança de segmento durante o ano. |

**Regras:**

# 1. A geração da ECF do ano **sem essa escolha avisa o contador e não escolhe sozinha**. O ERP não preenche o indicador a partir do segmento. 2. Nas linhas em que a fórmula da planilha não cobre o indicador escolhido (7 ou 8 em N660 3, N670 2, T181 6 e U182 2), o ERP **não calcula**: para a linha, avisa e espera o valor do usuário (Q93-5b, respondida). 3. A tela pode mostrar, só como apoio, o segmento do perfil (`ID_Segmento_Csll`) e as alíquotas de `Cad_Aliquota` vigentes no ano. Isso não preenche o campo. 4. Cada fórmula do cadastro que lê `0020.IND_ALIQ_CSLL()` lê o valor desta entidade para a empresa e o ano da escrituração. 5. `ID_Segmento_Csll` continua no perfil fiscal para escolher a linha de `Cad_Aliquota`, o adicional do IRPJ e o limite de compensação de prejuízos. Só deixa de decidir o indicador da ECF. 6. **Q93-5d, respondida: sim.** O `IND_QTE_SCP` (quantidade de SCP do sócio ostensivo), outro campo do 0020 que não é sim/não, entra nesta entidade com a mesma regra (o contador informa por ano). Os 28 indicadores sim/não continuam em `Mov_Ecf_Perfil_Indicador`.

**Contagem se aprovada (sobre a revisão 20):**

| | Revisão 20 | Com esta entidade |
|-------------------------------------|------------------|----------------------------------------------|
| Entidades | 915 | 916 |
| Campos | 9.878 | 9.886 (8 novos) |
| Campos de referência (FK) | 2.654 | 2.657 |
| Domínios | 272 | 273 (`indicador_aliquota_csll_ecf`) |

A contagem não soma as propostas do documento 96 (a entidade da DeRE e as demais), que também aguardam o seu "consolidar".

# 6. Como o cálculo roda

# 1. **Escolher as abas** do período: pelo segmento e pela forma de tributação do perfil vigente (revisão 18), nas versões de leiaute vigentes. 2. **Carregar as linhas vigentes** de cada aba na data do período (as 22 linhas das fórmulas divididas entram pela vigência). 3. **Resolver a ordem** por dependência entre linhas (as referências das fórmulas); uma referência circular é erro de carga. 4. **Calcular**: linhas "editáveis" recebem a soma dos lançamentos da Parte A (ou o valor do contador); linhas de cálculo executam a fórmula; o resultado vai para `Mov_Ecf_Apuracao_Linha_Valor`. 5. **Fechar** o IRPJ e a CSLL: os totais finais das abas N630 e N670 (e N620 e N660 na estimativa) alimentam `Mov_Apuracao_Irpj_Csll_Item`, que gera a provisão e a guia. Quais linhas são o "imposto devido" de cada aba é a Q93-7. 6. **Gerar** os registros M300, M350 e N a partir dos valores, no leiaute da versão.

O cálculo pode ser refeito: um novo cálculo recompõe as linhas do tipo cálculo e **mantém** as alterações do contador (marcadas em `Eh_Alterado`), avisando as linhas cuja fórmula mudou.

# 7. Perguntas para você

| Nº | Pergunta | Recomendação |
|-------|------------------------------------------------|---------------------------------------------|
| Q93-1 | **Respondida em 22/10/2026:** dividir a regra, 11 fórmulas em 22 linhas com vigência (alternativa A). | Seção 4.1 |
| Q93-2 | **Respondida em 22/10/2026:** o erro de digitação existe no manual da Receita; a leitura `M350(344)` está confirmada por você. | O motor acusa a linha e segue a sua decisão |
| Q93-3 | **Respondida em 22/10/2026:** aprovada a entidade `Mov_Ecf_Apuracao_Linha_Valor` (10 campos) e o campo `Base_Estimativa`. | Seção 5 |
| Q93-3b | Você pediu "guardar a composição das linhas". É o **rastro do cálculo** (quais linhas e valores formaram cada linha calculada) ou a **composição pelos lançamentos e contas da Parte A**, como nos registros M310 e M312? | Perguntei antes de desenhar |
| Q93-4 | **Teste feito em 22/10/2026** com os seus dois arquivos (seção 9). O contador ainda confirma `CREDITO`, as variantes não testadas e o Y520. | Seção 9 |
| Q93-5 | **Respondida em 22/10/2026:** o contador seleciona o indicador no momento da ECF do período; sem mapeamento automático. | Seção 5.6 |
| Q93-5b | **Respondida em 22/10/2026: sim.** Com o indicador 7 ou 8, as linhas N660 3, N670 2, T181 6 e U182 2 (a fórmula da planilha só trata 1 e 3, e 5 em duas delas, e o resto cairia em 15% ou 20%) **não são calculadas**: o ERP para a linha, avisa e **espera a resposta do usuário** (o valor que o contador informar). | Sem fórmula nova minha; a pergunta à Receita segue com o contador |
| Q93-5d | **Respondida em 22/10/2026: sim.** A entidade (seção 5.6, agora `Mov_Ecf_Escolha_Contador_Ano`, 8 campos) está aprovada e o `IND_QTE_SCP` entra nela, informado pelo contador por ano. | Seção 5.6 |
| Q93-6 | **Respondida em 22/10/2026:** sim, indicador de atividade rural no perfil (campo próprio). | Desenho do campo a escrever |
| Q93-7 | Quais linhas de N630, N670, N620 e N660 são o "imposto devido" que vai para `Mov_Apuracao_Irpj_Csll_Item`? Marcar por parâmetro, e não no programa. | Parâmetro, indicado pelo contador |
| Q93-8 | **Escopo das linhas editáveis:** o ERP só soma os lançamentos da Parte A que o contador faz, ou também **sugere** adições e exclusões a partir das contas (por exemplo, multas e doações não dedutíveis)? A sua decisão cobre o cálculo da cadeia; a geração automática dos lançamentos é outro desenho. | Só soma agora; a sugestão automática vira um documento próprio |

# 8. Limites

Li as 300 fórmulas e as referências entre as abas, mas **não executei nenhuma**. As leituras das funções `T_DRE`, `DEBITO`, `CREDITO` e `MESES_PERIODO` são minhas e podem estar erradas. A planilha de 24/09/2026 é do leiaute 12 (ano-calendário 2025 e situações especiais de 2026); o leiaute 13 deve mudar fórmulas, e é por isso que elas ficam no cadastro. Os totais por aba que alimentam a provisão (Q93-7) precisam do contador. Nada disto foi aplicado ao dicionário, à carga ou ao DDL.

# 9. Teste com dois arquivos de ECF reais (Q93-4, 22/10/2026)

Você mandou dois arquivos de ECF de dezembro de 2025 gerados pelo contador, o segundo com preço de transferência. Executei as fórmulas da variante A (PJ em geral, lucro real, anual por estimativa) que valem em 2025 contra os valores desses arquivos:

- **Resultado:** 424 pontos no arquivo 1 e 289 no arquivo 2 reproduzidos **sem nenhuma diferença**. São as 52 fórmulas da variante A que valem em 2025.
- **Correções da seção 3:** `DEBITO(x)` vale x se for **positivo**, senão zero (eu tinha escrito o contrário); `T_DRE` com débito positivo e crédito negativo, `MESES_PERIODO` e `BAL_RED` (string mensal da `FORMA_APUR_I` do 0010) estão confirmadas; `CREDITO` não foi exercitada.
- **Erro a mais na planilha da Receita:** a N660 linha 3 não tem o `FIM_SE`.
- **Não coberto pelo teste:** N600 e N610 (não estão nos arquivos), atividade rural, financeiras e seguradoras, as versões de 2026 (LC 224), `CREDITO` e `IND_ALIQ_CSLL` diferente de 1 (os dois arquivos têm indicador 1). As linhas editáveis foram tomadas do arquivo, não derivadas da contabilidade.
- **Candidatas ao "imposto devido" (Q93-7):** N620 linha 26 (IRPJ), N660 linha 18 (CSLL), N630A 26, N630B e N630C 23, N670 21, a confirmar pelo contador.
