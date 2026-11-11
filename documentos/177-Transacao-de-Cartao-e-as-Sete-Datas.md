# Transação de cartão e as sete datas — Documento 177

*Responde à sua resposta C176-4 (05/11/2026): a operação com cartão tem sete datas, e você escolheu, nas duas perguntas que fiz, uma **entidade nova de transação de cartão** com **as sete datas, cada uma com origem nas existentes**. Este documento desenha o que essa escolha pede e substitui a leitura que eu tinha dado à C176-4 (usar a data de pagamento da nota, `dPag`).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O 1601 informa o cartão de crédito e de débito pela **data da autorização** (FAQ da Receita 17.6.1.5, resposta de AL, CE, PB e RN, e regra geral: cartão garantido pela competência). O dicionário só tinha a `dPag` da nota (`Mov_Nota_Fiscal_Saida_Pagamento.Data_Pagamento`), que é a data do pagamento declarada na nota e não a da autorização pelo banco emissor. A diferença importa: a venda parcelada em 10 vezes é **uma** autorização e dez créditos, e o 1601 informa o valor total na data da autorização, sem olhar as parcelas.

Das sete datas que você listou, **três já têm casa** e quatro não. Nada é gravado duas vezes:

| Data | O que significa | Onde fica |
|---|---|---|
| Venda | Dia em que o cliente fez a compra | `Mov_Nota_Fiscal_Saida.Data_Emissao` quando há nota; `Data_Venda` da transação só quando **não** há nota |
| Autorização | O banco emissor aprovou e reservou o limite | **Campo novo** `Data_Autorizacao` |
| Captura | A venda foi registrada para cobrança | **Campo novo** `Data_Captura` |
| Fechamento do lote | O dia ou período de vendas foi enviado para processamento | **Campo novo** `Data_Fechamento_Lote` |
| Prevista de repasse | A operadora programou o depósito do valor líquido | `Mov_Titulo.Data_Vencimento` do título da parcela (sem campo) |
| Crédito / liquidação | O dinheiro caiu na conta | A data da baixa, pela mesma regra do Y520 (documento 111): `Data_Ocorrencia` do retorno bancário na baixa automática e `Data_Baixa` na manual (sem campo) |
| Fatura do cliente | A compra entra na fatura do consumidor (não é a data em que o lojista recebe) | **Campo novo** `Data_Fatura_Cliente` |

**Três achados.**

1. **A `dPag` da nota não serve para o 1601 de cartão.** Ela fica como está (é "tal como emitido"), mas o 1601 passa a ler `Data_Autorizacao` da transação. A minha leitura anterior ("a `dPag`, até haver outra fonte") está **substituída**.
2. **A transação é um fato à parte da nota e da baixa.** Uma autorização pode pagar várias notas (o carrinho de uma venda com mais de uma nota), e gera várias baixas (uma por parcela). Por isso a ligação é pelos dois lados: o pagamento da nota e a baixa apontam a transação.
3. **A data de crédito não precisa de campo.** O documento 111 (Q111-1, sua resposta de 26/10/2026) já fixou que a data da operação é a do dinheiro: a do retorno bancário na baixa automática, a da baixa na manual. É a mesma data que a transação precisa.

| Assunto | Quantidade |
|---|---|
| Entidade nova | `Mov_Transacao_Cartao`, 14 campos |
| Campos novos em entidades existentes | 2 (`Mov_Nota_Fiscal_Saida_Pagamento`, `Mov_Titulo_Baixa`) |
| Avisos do Motor | 3 |

# 2. Regras que segui

Valem as dos documentos 156 a 176. Em especial: sem valor padrão escondido; o ERP avisa e nunca bloqueia; **o ERP só registra** (o que se deriva não se grava); o dado entra "tal como emitido"; participante é `Cad_Participante` (a instituição de pagamento é um participante, como na seção 5.3 do documento 176).

# 3. Entidade nova: `Mov_Transacao_Cartao`

Uma linha por **autorização** do cartão (crédito, débito ou loja). Não tem vigência (é fato). Campos:

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Transacao_Cartao` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | A filial que realizou a venda (a titular do contrato com a credenciadora). Quem informa o 1601 não é esta, e sim a titular da conta bancária onde o dinheiro cai (D-N484). |
| `ID_Participante_Credenciadora` | referência (Cad_Participante) | A credenciadora ou instituição de pagamento que liquida a transação: o `COD_PART_IP` do 1601 quando o recebimento é por cartão. |
| `Tipo_Cartao` | enumeração {credito, debito, loja} | Crédito, débito ou cartão de loja (private label), como o FAQ 17.6.1.1 lista. |
| `Bandeira` | código (2), opcional | Bandeira da operadora (tabela da NF-e). |
| `Numero_Autorizacao` | código (até 128) | O número que o emissor devolveu na autorização. Mesmo conteúdo de `cAut` da nota, mas **da operadora**. |
| `Numero_Nsu_Transacao` | código (até 20), opcional | O NSU da transação. |
| `Numero_Parcelas` | número | Quantidade de parcelas (1 para débito e crédito à vista). |
| `Valor_Bruto` | número | Valor total da transação, **sem considerar as parcelas** (é o valor que o 1601 informa, FAQ 17.6.1.5). |
| `Data_Venda` | data, opcional | Dia da compra. **Só quando não há nota** (venda sem documento, adiantamento): com nota, a data sai da nota e o campo fica vazio, para não gravar duas vezes. |
| `Data_Autorizacao` | data | Quando o banco emissor aprovou a transação e reservou o limite. **É a data que o 1601 usa** para cartão de crédito e de débito. |
| `Data_Captura` | data, opcional | Quando a venda foi registrada para cobrança; pode ser depois da venda (venda futura ou recorrente). |
| `Data_Fechamento_Lote` | data, opcional | Fechamento do dia ou do período de vendas enviado para processamento. |
| `Data_Fatura_Cliente` | data, opcional | Quando a compra entra na fatura do consumidor. Não é data de recebimento do lojista; serve à conciliação e ao tratamento de reclamação, não ao 1601. |

## 3.1 Ligações nas entidades existentes

| Entidade | Campo novo | Descrição |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Pagamento` | `ID_Transacao_Cartao` (referência, opcional) | A transação que pagou este grupo de pagamento da nota. Vazio quando a forma de pagamento não é cartão. Várias notas podem apontar a mesma transação. |
| `Mov_Titulo_Baixa` | `ID_Transacao_Cartao` (referência, opcional) | A transação cujo crédito (uma parcela) esta baixa liquidou. Vazio quando o recebimento não é cartão. |

A **data prevista de repasse** é o vencimento do título da parcela (`Mov_Titulo.Data_Vencimento`), e a data de **crédito** é a da baixa, como na seção 1. Nenhuma das duas ganha campo.

# 4. Efeito no 1601 (documento 176)

1. Para cartão de crédito e de débito, o Motor usa `Mov_Transacao_Cartao.Data_Autorizacao` e `Valor_Bruto` (o total da transação, sem parcelas) nas UFs cujo `Criterio_Reconhecimento` é `competencia_da_transacao` (AL, CE, PB e RN). Nas demais, o FAQ só diz que o cartão vai pela competência; o Motor usa a mesma leitura (autorização, total sem parcelas) e avisa até o contador responder a C177-1. Os demais meios seguem a seção 5.4 do documento 176 (Pix e TED na transferência, boleto na emissão, cheque na compensação).
2. A `Data_Autorizacao` define também **em qual mês** o valor entra, mesmo que as parcelas sejam creditadas em outros meses: uma venda de dezembro parcelada em 6 vezes aparece inteira no 1601 de dezembro.
3. `COD_PART_IP` do cartão vem de `ID_Participante_Credenciadora` da transação. A baixa só carrega `ID_Participante_Instituicao_Pagamento` quando o recebimento **não** é por cartão (a seção 5.3 do documento 176 continua valendo para esses casos).
4. A resposta C176-4 do contador deixa de ser pergunta aberta.

# 5. Avisos do Motor (sem bloqueio)

| # | Aviso |
|---|---|
| 1 | Baixa de tipo cartão (ou pagamento de nota com forma cartão) sem transação ligada: o 1601 não tem data de autorização, e o Motor **não usa** a `dPag` nem a data da baixa no lugar dela |
| 2 | `Numero_Autorizacao` da transação diferente do `cAut` da nota |
| 3 | Datas fora da ordem esperada (autorização antes da venda, crédito antes da autorização). A captura e o fechamento do lote podem vir depois do crédito previsto em vendas futuras e recorrentes, e isso **não** gera aviso |

# 6. O que continua como estava

1. `Mov_Nota_Fiscal_Saida_Pagamento.Data_Pagamento`, `Numero_Autorizacao`, `Bandeira` e os demais campos do grupo de pagamento da NF-e e do BP-e (documento 164) ficam como estão: são o que **o documento diz**.
2. O 1601 por Pix, TED, boleto, cheque e depósito segue o documento 176, sem nova entidade.

# 7. Perguntas

## 7.1 Para você, Alberto (Q177-1 a Q177-5)

**Q177-1. A entidade `Mov_Transacao_Cartao` com os 14 campos da seção 3?** Recomendo sim. Alternativa: tirar `Data_Fatura_Cliente`, que não alimenta nenhum bloco fiscal, deixando 13 campos.

**Q177-2. Ligar a transação pelos dois lados: `ID_Transacao_Cartao` no pagamento da nota e na baixa (seção 3.1)?** Recomendo sim. Alternativa: ligar só pela baixa (perde a transação que ainda não foi recebida).

**Q177-3. `Data_Venda` na transação só quando não há nota (seção 3)?** Recomendo sim. Alternativa: sempre gravar (duplica a data da nota e pode divergir).

**Q177-4. A data de crédito sem campo, pela regra do Y520 (retorno bancário na baixa automática, `Data_Baixa` na manual), e a data prevista de repasse como o vencimento do título (seção 1)?** Recomendo sim. Alternativa: campos próprios na transação (duplica baixa e vencimento).

**Q177-5. O 1601 de cartão passa a usar `Data_Autorizacao` e `Valor_Bruto` da transação, no lugar da `dPag` da nota (seção 4)?** Recomendo sim. Alternativa: manter a `dPag` e a transação só para conciliação (o 1601 ficaria com a data que o contador já disse que não é a certa).

## 7.2 Para o contador (C177-1)

**C177-1.** Venda parcelada: o 1601 informa o valor total na data da autorização, sem as parcelas (FAQ 17.6.1.5, resposta de AL, CE, PB e RN). Nas UFs sem resposta, o cartão de crédito parcelado segue a mesma regra ou entra parcela a parcela pela data de crédito?

## 7.3 Para a equipe (E177-1 e E177-2)

**E177-1.** O arquivo da credenciadora (EDI) e o TEF trazem as sete datas, ou só algumas? As datas que faltarem ficam vazias (opcionais), mas o contador precisa saber.

**E177-2.** Uma autorização que paga mais de uma nota é frequente? Se não for, a ligação do pagamento da nota pode virar 1:1 e a transação ganha o `ID_Nota`.
