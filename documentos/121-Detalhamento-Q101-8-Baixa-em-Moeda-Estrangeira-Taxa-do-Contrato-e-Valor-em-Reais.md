# Detalhamento da Q101-8: a baixa do título em moeda estrangeira, a taxa do contrato de câmbio e o valor em reais — Documento 121

> **Aplicado na revisão 24 (26/10/2026, documento 122, D-N362 a D-N364).** Entrou o campo `Mov_Titulo_Baixa.Valor_Arredondamento_Com_Sinal` e o texto dos campos da baixa em moeda (taxa, desconto, juros, valor em reais e valor financeiro); a tolerância de R$ 0,04 é parâmetro; a conta de resultado do arredondamento é do contador. Onde o texto abaixo diz que nada foi aplicado, vale esta nota. As leituras que apliquei ("sim para três", R$ 0,04, 8d e 8e) estão no documento 38, seção 0.1, para você confirmar.

> **Respondido por Alberto em 26/10/2026 (D-N362, documento 14): Q101-8a sim; Q101-8b tolerância de 0,04 para mais ou para menos, sem percentual; Q101-8c a taxa de referência é obrigatória; Q101-8d sem aprovação do banco o item fica pendente, sem baixa; Q101-8e sim, desconto e juros em moeda convertidos pela taxa de câmbio.** As leituras que fiz de cada resposta estão na seção 6. **Segunda rodada (26/10/2026, D-N363): Q101-8g sim; Q101-8f "deixar em um campo de arredondamento". Terceira rodada (26/10/2026, D-N364): "sim para três", lido como sim às três perguntas Q101-8f1, Q101-8f2 e Q101-8f3** (campo aprovado, baixa não confirmada acima da tolerância, diferença lançada no lote). Nada foi aplicado: entra na revisão 24. Se alguma leitura estiver errada, me diga.

*Detalhamento pedido por Alberto em 26/10/2026 ("detalhar Q101-8"), logo depois da sua resposta: "Sim, quem baixa lança a taxa da moeda, com o contrato de câmbio" (D-N361, documento 14). A Q101-8 está **respondida**; este documento mostra como a baixa funciona, linha por linha, e **cinco pontos que achei ao detalhar** (Q101-8a a Q101-8e). **Nada foi alterado no dicionário**: os campos da baixa já estão nele desde a revisão 21 (D-N346) e só perdem a marca "confirmar" na revisão 24. As leituras de norma e de prática contábil são minhas e não foram conferidas no texto oficial.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **A resposta.** Quem baixa o título em moeda lança, **na moeda do título**, o valor baixado, o desconto e os juros, e **a taxa da moeda, a do contrato de câmbio**. O ERP calcula o total em reais (`Valor_Pago_Reais`). Sem contrato de câmbio (cartão, conta no exterior, recursos mantidos no exterior, moeda), vale a taxa que o operador digita do pagamento (Q105-3). **Sem campo novo.**
- **O que a baixa grava:** a moeda é a do título (a baixa não tem campo de moeda); os valores ficam na moeda do título; a taxa é digitada; o total em reais é calculado e guardado como snapshot.
- **O que eu achei ao detalhar** (seção 6): (a) onde guardar o número do contrato de câmbio; (b) centavos de diferença contra o extrato e erro de digitação da taxa; (c) baixa sem dinheiro (perda, desconto) em título em moeda; (d) baixa automática do retorno bancário, que não traz a taxa; (e) o desconto e os juros em moeda **não são variação cambial**, e o documento 101 os misturava.
- **Nenhuma resposta cria campo.** Mudam só texto de descrição e a regra 5 do documento 101 (Q101-8e).

# 2. A pergunta, a sua resposta e como li

> **Q101-8 (documento 101).** Confirma a leitura da baixa: quem baixa digita **na moeda do título** o valor baixado, o desconto e os juros, e digita a **taxa**; o ERP calcula o total pago em reais (`Valor_Pago_Reais`); `Valor_Baixado`, `Valor_Desconto` e `Valor_Juros_Multa` passam a ser **na moeda do título** quando o título é em moeda? *Recomendação: sim; toda leitura em reais desses campos passa a usar `Valor_Pago_Reais`.*

**Sua resposta (26/10/2026):** "Sim, quem baixa lança a taxa da moeda, com o contrato de câmbio." **Como leio:** sim à pergunta inteira. "Com o contrato de câmbio" é **a origem da taxa**: a do contrato fechado para aquele pagamento ou recebimento, o que já era a sua decisão da Q100-17 ("na baixa vale o contrato de câmbio, o valor efetivo"). Não li como pedido de cadastro de contratos de câmbio (o documento 100 o deixou fora; só há a referência da operação, ponto Q101-8a).

# 3. O que o dicionário já tem em `Mov_Titulo_Baixa`

| Campo | Regra hoje |
|---|---|
| `Valor_Baixado` | O valor liquidado, **na moeda do título** quando o título é em moeda; em reais nos demais. Pode ser menor que o saldo (baixa parcial) |
| `Valor_Desconto` | Desconto obtido (pagar) ou concedido (receber) na baixa, **na moeda do título** |
| `Valor_Juros_Multa` | Acréscimo por atraso, **na moeda do título** |
| `Taxa_Cambio` | A taxa do **fechamento do câmbio**, **digitada** por quem paga ou recebe (Q100-17). Sem contrato de câmbio, a que o operador digita (Q105-3). **Obrigatória** quando o título é em moeda; vazia nos demais. A série de cotações só serve de sugestão na tela. Nas baixas de encontro, a mesma taxa nas duas baixas (Q114-2). DDL: `numeric(15,8)` |
| `Valor_Pago_Reais` | (`Valor_Baixado` − `Valor_Desconto` + `Valor_Juros_Multa`) × `Taxa_Cambio`, arredondado pelas casas da moeda funcional. Calculado pelo ERP, guardado como snapshot. É o valor **bruto** da baixa em reais: o da variação cambial final e o do Y520 quando a base do tipo é `valor_bruto` |
| `Valor_Financeiro` | O dinheiro que de fato se movimenta, em reais: igual ao total da baixa em reais no pagamento e no recebimento; **zero** na baixa de tipo encontro. É o que o banco, a conciliação e o Y520 (base `valor_financeiro`) leem |
| Moeda | **Não há campo na baixa**: vale a moeda do título |

# 4. Como a baixa funciona

1. **Quem baixa digita**, na moeda do título, o valor baixado, o desconto e os juros, e a **taxa do contrato de câmbio**. Em baixa manual, quem digita é o operador do financeiro (`ID_Participante_Baixa`, obrigatório na baixa manual).
2. **O ERP calcula** `Valor_Pago_Reais` somando antes e multiplicando depois pela taxa, com **um só arredondamento** no fim, pelas casas da moeda funcional.
3. **A taxa sugerida** na tela vem da série marcada do par de moedas (a mesma do fechamento), na última cotação até a data da baixa. É **sugestão**: quem baixa troca pela do contrato, e o ERP não compara nem corrige.
4. **O saldo do título** cai pelo `Valor_Baixado` na moeda do título; o saldo em reais é sempre derivado (regra 1 do documento 101).
5. **A variação cambial realizada** é lançada em `Mov_Lote_Lancamento` com `Origem_Tipo` = `variacao_cambial` (regra 5 do documento 101): a diferença entre o valor contabilizado da parte quitada, na última taxa contabilizada, e o que saiu da empresa. Ver o ponto Q101-8e sobre o desconto e os juros.
6. **O Y520** (documento 100) lê o `Valor_Pago_Reais` ou o `Valor_Financeiro`, conforme a base do tipo da baixa, menos as retenções. A taxa do contrato é a que dá o valor do Y520.
7. **Estorno** da baixa devolve o valor na moeda ao saldo e estorna a variação (regra 8 do documento 101).

# 5. Exemplo (valores ilustrativos)

Título a pagar de **US$ 10.000**, contabilizado a 5,00; no fim do mês anterior o saldo de **US$ 7.000** estava contabilizado a **5,30** (R$ 37.100). Baixa do saldo, com **desconto de US$ 100** e **juros de US$ 50**, câmbio fechado a **5,25** (taxa do contrato).

| Item | Conta | Resultado |
|---|---|---|
| `Valor_Baixado` | US$ 7.000 | Saldo na moeda zera |
| `Valor_Desconto` e `Valor_Juros_Multa` | US$ 100 e US$ 50 | Pago em dólar: 7.000 − 100 + 50 = **US$ 6.950** |
| `Taxa_Cambio` (contrato) | 5,25 | |
| `Valor_Pago_Reais` e `Valor_Financeiro` | 6.950 × 5,25 | **R$ 36.487,50** (o que sai do banco; vai ao Y520) |
| Contabilizado da parte quitada | 7.000 × 5,30 | R$ 37.100,00 |
| Diferença | 37.100,00 − 36.487,50 | **R$ 612,50** |
| **Como separar a diferença (Q101-8e, lida como a sua resposta)** | Desconto convertido pela taxa da baixa: 100 × 5,25 = R$ 525,00 (ganho de desconto). Juros convertidos pela taxa da baixa: 50 × 5,25 = R$ 262,50 (despesa). Variação cambial sobre o valor baixado: 7.000 × (5,30 − 5,25) = **R$ 350,00** (ganho) | 525,00 − 262,50 + 350,00 = **612,50** ✓ |

*Se o desconto e os juros fossem convertidos pela taxa em que o saldo estava contabilizado (5,30), como eu tinha proposto, daria R$ 530,00, R$ 265,00 e variação de R$ 347,50. A sua resposta ("convertidos pela taxa de câmbio") eu leio como a taxa da baixa, a do contrato.*

Sem separar (como dizia o documento 101), os R$ 612,50 inteiros iriam para a variação cambial, e o desconto e os juros ficariam sem conta própria.

# 6. Os cinco pontos e as suas respostas (26/10/2026)

## Q101-8a. Número do contrato de câmbio: **respondida, sim**

Fica em `Referencia_Operacao` (código de 40, "número do contrato, da fatura ou do documento do exterior"), no título e na classificação da baixa (`Mov_Ecf_Operacao_Exterior`), só para o contador achar a operação; não vai para a ECF. **Sem campo novo.**

## Q101-8b. Conferência da taxa: **respondida, com uma leitura minha e uma pergunta nova**

**Sua resposta:** "Diferença neste caso tem que ser de 0,04 centavos para mais ou para menos, não fixar percentual."

**Como leio:**

- **Sai o aviso por percentual** que eu tinha proposto (partida de 10% contra a série). O erro de digitação da taxa passa a ser pego pela conferência contra o extrato.
- A conferência é a do **valor em reais** da baixa contra o extrato: o `Valor_Financeiro` calculado pode diferir do que o banco debitou em **até R$ 0,04, para mais ou para menos**. Li "0,04 centavos" como **R$ 0,04 (quatro centavos)**, e não 0,04 de um centavo (R$ 0,0004); **me diga se foi outro valor**.
- O valor de **0,04 é um parâmetro** do sistema, com esse valor de partida, e não uma constante do programa (regra do projeto para valores que podem mudar).

**Q101-8f, respondida em 26/10/2026:** "deixar em um campo de arredondamento". Ver a proposta do campo logo abaixo.

## Q101-8c. Baixa sem dinheiro: **respondida, contra a minha recomendação**

**Sua resposta:** "Tem que colocar a taxa de referência para baixar, neste caso não tem contrato de câmbio."

**Como leio:** a taxa continua **obrigatória em toda baixa de título em moeda**, inclusive a baixa sem dinheiro (perda, desconto sem pagamento). Como não há contrato de câmbio, a taxa é **uma taxa de referência** que quem baixa digita (com a série de cotações como sugestão, como na Q105-3). **Eu tinha recomendado o contrário** (taxa opcional); a sua resposta prevalece e **o dicionário já está assim** (obrigatória), só o texto de `Taxa_Cambio` passa a dizer "taxa de referência quando não há contrato". **Sem campo novo.**

**Q101-8g, respondida em 26/10/2026: sim.** Com a taxa de referência na baixa sem dinheiro, a diferença entre o valor contabilizado do saldo (na última taxa) e o valor pela taxa de referência é **variação cambial lançada na baixa**, como na baixa com dinheiro. Muda só o texto de `Valor_Pago_Reais` e a regra do lote; **não verifiquei** que valor em reais cada tipo sem dinheiro espera hoje.

## Q101-8d. Baixa automática: **respondida, com uma leitura minha**

**Sua resposta:** "Se não foi aprovado no banco o item ainda fica pendente, não tem baixa neste caso."

**Como leio:** sem a **aprovação do banco** (o pagamento ou o câmbio não confirmado no retorno), o item **continua pendente e não gera baixa**. Isso cobre também o caso que eu perguntei (retorno sem a taxa do contrato): sem taxa, não há baixa; o item fica pendente na **tela de consistência do retorno bancário**, que já existe, e quem baixa digita a taxa do contrato e dá andamento. A **área de inconsistências** (Q113-11, ainda sem resposta) passa a mostrar o item também, se for aprovada. Se você quis dizer só que o pagamento não aprovado pelo banco não baixa (e a falta da taxa é outro caso), me diga. **Sem campo novo.**

## Q101-8e. Desconto e juros em moeda: **respondida, com uma leitura minha**

**Sua resposta:** "Sim, são em moedas e depois convertidos na moeda da empresa, pela taxa de câmbio."

**Como leio:** o desconto e os juros ficam **na moeda do título** (como já está) e são **convertidos para reais pela taxa da baixa**, a do contrato (ou a de referência, Q101-8c). **Não são variação cambial.** A variação cambial realizada é a do **valor baixado**: `Valor_Baixado` × (taxa em que estava contabilizado − taxa da baixa). É o que mostra o exemplo da seção 5 (R$ 525,00 de desconto, R$ 262,50 de juros e R$ 350,00 de variação). **Diferença em relação à minha proposta:** eu tinha escrito "à taxa contabilizada"; você respondeu "pela taxa de câmbio", e eu leio a da baixa. **Muda a regra 5 do documento 101** (que misturava tudo na variação) e o texto de `Valor_Pago_Reais`. O contador confirma as contas de desconto e juros. **Sem campo novo.**

## Proposta do campo de arredondamento (Q101-8f)

Sua resposta, "deixar em um campo de arredondamento", escolhe guardar a diferença de até R$ 0,04 **num campo**, e não numa conta contábil (a opção B que eu tinha apresentado) nem só como aviso. Isso **cria 1 campo**, **aprovado por você em 26/10/2026 (Q101-8f1, D-N364)**:

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **Valor_Arredondamento_Com_Sinal** (em `Mov_Titulo_Baixa`) | *número, opcional, aceita sinal* | A diferença, em reais, entre o valor que o **banco movimentou** (o do extrato) e o `Valor_Financeiro` **calculado** pelo ERP, numa baixa de título **em moeda estrangeira com dinheiro**. Positivo quando o extrato mostra **mais** dinheiro que o calculado, nos dois sentidos (pagar e receber). O valor absoluto **não passa da tolerância** (parâmetro, R$ 0,04 de partida). Vazio quando não há diferença e nas baixas de título em reais. O nome leva o sufixo `Com_Sinal` pela regra D-N344. |

- **Conciliação:** compara o extrato com `Valor_Financeiro` + `Valor_Arredondamento_Com_Sinal`.
- **Y520:** a diferença **não entra** (centavos); o Y520 segue lendo `Valor_Pago_Reais` ou `Valor_Financeiro`, conforme o tipo da baixa.
- **Contagem, se aprovado:** 0 entidades e 1 campo (sobre a revisão 23: 922 entidades e 9.999 campos, sem somar o que já espera o "consolidar").

**Duas coisas que a sua resposta não fecha:**

- **Q101-8f2: acima da tolerância (sim, D-N364).** A baixa **não é confirmada** até alguém corrigir a taxa (o campo só aceita a diferença dentro da tolerância).
- **Q101-8f3: contabilização (sim, D-N364).** O campo guarda a diferença, e o razão do banco só fecha com o extrato porque **a diferença também é lançada** no lote da baixa. Recomendo lançar o valor do campo numa **conta de resultado parametrizada** (a conta é do contador), no mesmo lote da baixa. Se você quis só guardar o valor no campo, sem lançar, o razão do banco fica com a diferença de centavos contra o extrato.

# 7. O que muda no dicionário

| Resposta | Efeito |
|---|---|
| **Q101-8: sim** | Nada no dicionário. Sai a marca "confirmar" dos campos da baixa |
| Q101-8a | Só o texto de `Referencia_Operacao` (cita o contrato de câmbio) |
| Q101-8b | Parâmetro da tolerância (R$ 0,04 de partida) e regra da conciliação |
| **Q101-8f** | **1 campo novo** em `Mov_Titulo_Baixa` (`Valor_Arredondamento_Com_Sinal`), aprovado (Q101-8f1); a diferença é lançada no lote numa conta de resultado parametrizada (Q101-8f3); acima da tolerância a baixa não é confirmada (Q101-8f2) |
| Q101-8g | Só o texto de `Valor_Pago_Reais` e a regra do lote da baixa sem dinheiro |
| Q101-8c | Só o texto de `Taxa_Cambio` (taxa de referência quando não há contrato) |
| Q101-8d | Regra da baixa automática e da tela de consistência do retorno; sem campo |
| Q101-8e | Só o texto de `Valor_Pago_Reais`, `Valor_Desconto` e `Valor_Juros_Multa`, e a regra 5 do documento 101 |

# 8. Perguntas

| Nº | Pergunta | Situação |
|---|---|---|
| **Q101-8** | Confirma a leitura da baixa | **Respondida: sim** |
| **Q101-8a** | Número do contrato em `Referencia_Operacao` | **Respondida: sim** |
| **Q101-8b** | Conferência da taxa | **Respondida:** tolerância de R$ 0,04 (leitura minha), sem percentual |
| **Q101-8c** | Baixa sem dinheiro em moeda | **Respondida:** taxa de referência obrigatória |
| **Q101-8d** | Baixa automática sem aprovação do banco ou sem taxa | **Respondida:** item pendente, sem baixa |
| **Q101-8e** | Desconto e juros em moeda | **Respondida:** convertidos pela taxa da baixa, fora da variação |
| **Q101-8f** | Diferença de centavos contra o extrato | **Respondida:** "deixar em um campo de arredondamento" (D-N363) |
| **Q101-8f1** | Aprova o campo `Valor_Arredondamento_Com_Sinal` em `Mov_Titulo_Baixa`, como descrito acima? | **Respondida: sim** (D-N364) |
| **Q101-8f2** | Acima da tolerância a baixa não é confirmada até corrigir a taxa? | **Respondida: sim** (D-N364) |
| **Q101-8f3** | O valor do campo é lançado no lote da baixa numa conta de resultado parametrizada (para o razão do banco fechar com o extrato)? | **Respondida: sim** (D-N364); a conta de resultado é do contador (parâmetro) |
| **Q101-8g** | Na baixa sem dinheiro, a diferença para o valor pela taxa de referência é variação cambial? | **Respondida: sim** (D-N363) |

# 9. Limites

- Li o documento 101, o documento 105 (taxa sem contrato), o documento 100 e o dicionário na revisão 23. **Não executei** nada com dados.
- **Não verifiquei** as contas em que o lote da baixa lança desconto e juros, nem os valores em reais que os tipos sem dinheiro esperam (Q101-8g).
- As leituras de "0,04 centavos" (R$ 0,04), de "taxa de câmbio" (a da baixa) e de "não aprovado no banco" estão marcadas na seção 6.
- Os valores do exemplo são ilustrativos; confira a contabilização com o contador.
