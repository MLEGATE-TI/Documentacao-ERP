# Detalhamento da Q113-3: Lançamento Contábil do Encontro de Contas — Documento 114

*Você pediu para detalhar a Q113-3 do documento 113: "a baixa de tipo encontro fica sem `ID_Lote`; o lançamento contábil é o do encontro, com a perna do banco?". Reli como o dicionário liga a baixa ao lançamento, o que o documento 101 diz da variação cambial na quitação e o que a revisão 22 gravou no encontro. **A pergunta tem uma parte já respondida (a perna do banco, Q111-13) e uma parte que ficou aberta: o que a baixa de encontro guarda em `ID_Lote`.** Ao montar o exemplo em moeda estrangeira achei mais três pontos que a Q113-3 não cobria (variação cambial, valor novo no domínio do lote e retenção na fonte). É proposta de desenho: **nada foi alterado no dicionário**, que segue na revisão 22.*

Mlegate · Alberto Beyeler · Outubro de 2026 · Versão 2 (26/10/2026)

**Sua resposta (26/10/2026):** "sim, está correto". Li como a **recomendação do documento em cada pergunta**: **Q114-1 opção B**, **Q114-2 sim**, **Q114-3 sim** e **Q114-4 sim** (a retenção é feita no encontro, e o contador confirma). Registrei só no documento 38; o dicionário segue na revisão 22 e recebe isto, sem campo novo, na próxima consolidação.

# 1. Resumo

O lançamento do encontro é **um só**, no `Mov_Titulo_Encontro_Contas.ID_Lote`: baixa a obrigação a pagar, baixa o direito a receber e leva a diferença em dinheiro ao banco ou caixa. Isso você já confirmou (Q111-13, "correto"). O que sobra é o que **cada baixa de tipo encontro** guarda em `Mov_Titulo_Baixa.ID_Lote`, e há três saídas (seção 3). **Recomendo a B**: as duas baixas apontam **o mesmo lote do encontro**. Não cria campo; muda só o texto do campo. Hoje o dicionário diz "vazio" (opção A), que foi leitura minha.

Em título em moeda estrangeira há ainda a **variação cambial realizada** de cada ponta, e o exemplo da seção 4 mostra como ela fecha com a diferença em dinheiro. Há também **1 valor novo** proposto para `Mov_Lote_Lancamento.Origem_Tipo` e **1 ponto de retenção na fonte**, que é do contador. **Total do documento: 0 entidades e 0 campos.**

# 2. O que o dicionário já diz

| Onde | O que diz hoje (revisão 22) |
|---|---|
| `Mov_Titulo_Encontro_Contas.ID_Lote` | O lançamento do encontro: débito da obrigação a pagar, crédito do direito a receber e a perna de banco, caixa ou aplicação com a diferença em dinheiro (`ID_Conta_Contabil`). `Origem_Tipo` do lote = `outro` "nesta v1" |
| `Mov_Titulo_Baixa.ID_Lote` | Nas baixas de tipo encontro fica **vazio**; o lançamento é o do encontro |
| `Mov_Titulo_Baixa.ID_Encontro` | As duas baixas apontam o mesmo encontro |
| `Mov_Titulo_Baixa.Valor_Financeiro` | Zero nas baixas de tipo encontro; o dinheiro é a diferença, que vai ao banco no próprio encontro |
| Documento 101, seção 4, item 5 | Na quitação, o contabilizado é o valor na moeda pela **última taxa contabilizada**, o efetivo é o `Valor_Pago_Reais`, e a diferença é a **variação realizada**, em lote com `Origem_Tipo` = `variacao_cambial` |
| Documento 111, Q111-10 | No Y520, o encontro entra pelo **valor integral** de cada ponta (pago e recebido), com a taxa do encontro |

# 3. O que `Mov_Titulo_Baixa.ID_Lote` guarda numa baixa de encontro

| Opção | Como fica | Vantagem | Risco |
|---|---|---|---|
| **A. Vazio** (o que está no dicionário) | Só o encontro aponta o lote | Cada fato é lançado uma vez e a baixa não aponta nada | Quem sai da baixa para chegar ao lançamento (relatório, auditoria, a linha do Y520 que aponta a baixa) **precisa saber que, neste tipo, o caminho é pelo encontro**. Baixa sem `ID_Lote` pode ser lida como "baixa não contabilizada" |
| **B. O mesmo lote do encontro** (recomendada) | As duas baixas e o encontro apontam **o mesmo lote**, que continua sendo um só | A navegação é igual à das outras baixas: baixa, lote, lançamentos. Nada é lançado duas vezes, porque o lote é um | `ID_Lote` deixa de ser "um lote por baixa". Estornar **uma** baixa de encontro passa a ser estornar o encontro inteiro (as duas baixas e o lote), o que é o certo |
| **C. Um lote por baixa** | Cada baixa tem o seu lote, com uma conta transitória "encontro de contas a compensar" que sempre volta a zero; o encontro leva só o lote da diferença no banco | O Motor de Regras trata a baixa de encontro como as outras | Cria uma conta nova, partidas a mais, e o saldo da transitória fica errado se só uma ponta for estornada |

**Recomendação: B.** Como `Valor_Financeiro` é zero nas duas baixas, o que muda para o resto do ERP é só o texto da regra: "o lote do encontro, compartilhado pelas duas baixas e pelo encontro". Se você prefere a A, nada muda no dicionário.

# 4. Exemplo

**Em reais, mesmo participante.** A pagar de R$ 500 e a receber de R$ 400. Diferença de R$ 100, paga por nós.

| Lançamento do encontro | Débito | Crédito |
|---|---|---|
| Fornecedores a pagar (o título a pagar) | 500 | |
| Clientes a receber (o título a receber) | | 400 |
| Banco | | 100 |

**Em dólar, com variação.** A pagar de US$ 100, contabilizado na última taxa a 4,90 (R$ 490). A receber de US$ 80, contabilizado a 5,10 (R$ 408). A taxa do encontro, digitada por quem o lança, é 5,00. O efetivo é R$ 500 no a pagar e R$ 400 no a receber (é o que vai ao Y520, Q111-10). A diferença é US$ 20 a 5,00, ou R$ 100, paga por nós.

| Lote | Linha | Débito | Crédito |
|---|---|---|---|
| Encontro (contabilizado) | Fornecedores a pagar | 490 | |
| | Clientes a receber | | 408 |
| | Banco (a diferença no contabilizado) | | 82 |
| Variação cambial realizada | Perda no a pagar: efetivo 500 contra contabilizado 490 | 10 | |
| | Perda no a receber: efetivo 400 contra contabilizado 408 | 8 | |
| | Banco (o resto do que saiu) | | 18 |

O banco recebe 82 + 18 = **R$ 100**, igual ao `Valor_Diferenca` do encontro, que é o que o extrato mostra. Este desenho é a **minha leitura** do item 5 do documento 101 aplicada ao encontro; o lançamento exato da variação na baixa comum não está escrito linha a linha em nenhum documento.

# 5. Outros pontos

- **Valor novo no domínio do lote.** `Mov_Lote_Lancamento.Origem_Tipo` já tem `variacao_cambial`, `baixa_titulo` e outros, e o encontro cai em `outro`. Proponho o valor **`encontro_contas`** (1 valor no domínio, sem campo), para o contador achar os lançamentos de encontro e para os relatórios os separarem.
- **Participantes diferentes** (Q113-8 e Q113-9, abertas). Cada ponta do lançamento fica com o participante do seu título, e a perna do banco com o `ID_Participante_Diferenca`. O razão por participante é a confirmar na implementação.
- **Estorno.** Estornar o encontro estorna o lote, as duas baixas e, se houver, a variação realizada; a trava de período vale para tudo isso (já dito no documento 08).
- **Retenção na fonte.** O título a pagar pode ter retenção (IR, CSRF, INSS, ISS), que o dicionário liga à **baixa** (`Mov_Titulo_Retencao.ID_Baixa`). Se a baixa é de encontro, a estrutura aguenta, mas **não está dito** se a retenção acontece no encontro nem de onde sai o valor retido, já que não há dinheiro na baixa. É ponto do contador (seção 7).

# 6. Impacto no dicionário

| Item | Mudança |
|---|---|
| Entidades e campos | **0 e 0** |
| `Mov_Titulo_Baixa.ID_Lote` | Só o texto (se B: "o lote do encontro, compartilhado") |
| `Mov_Titulo_Encontro_Contas.ID_Lote` | Só o texto (cita a variação realizada e o `Origem_Tipo`) |
| `Mov_Lote_Lancamento.Origem_Tipo` | +1 valor, `encontro_contas` (Q114-3) |
| Documentos 08 e 10 | Texto das seções 3 e 5 do 08 e da seção do lote do 10 |

# 7. Perguntas para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q114-1** | O que a baixa de encontro guarda em `ID_Lote`: **A** (vazio, como está), **B** (o mesmo lote do encontro) ou **C** (um lote por baixa, com conta transitória)? | B |
| **Q114-2** | Em encontro de título em moeda, a variação cambial realizada entra **num lote à parte** (`variacao_cambial`), contra o banco, como no exemplo da seção 4, e as **duas baixas levam a mesma taxa**, digitada por quem lança o encontro? | Sim |
| **Q114-3** | Acrescentar o valor `encontro_contas` ao `Origem_Tipo` de `Mov_Lote_Lancamento`? | Sim |
| **Q114-4** | O título a pagar com **retenção na fonte** é retido na baixa de encontro, como em qualquer pagamento, com o contador dizendo de onde sai o valor? Ou o encontro não retém? | Retém, o contador confirma |

**Para o contador.** (a) A compensação é fato gerador da retenção na fonte do título a pagar? (b) A variação realizada do encontro tem o mesmo tratamento fiscal da baixa em dinheiro (regime de caixa ou competência, IN RFB 1.079, documento 101)? (c) O encontro entre participantes diferentes muda algum dos dois (ponto já registrado no documento 38).

# 8. Contagem e limites

**0 entidades e 0 campos.** O dicionário continua em **922 entidades e 9.998 campos** (revisão 22). Não executei nenhum lançamento num sistema: os números da seção 4 são conta de papel, conferidos à mão (490 = 408 + 82; 82 + 18 = 100). Não li de novo a IN RFB 1.079 nem a norma da retenção na fonte para este documento.
