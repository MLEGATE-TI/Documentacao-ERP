# Detalhamento da Q101-1: título em moeda estrangeira, os quatro campos e a taxa estimada — Documento 119

> **Aplicado na revisão 24 (26/10/2026, documento 122, D-N360).** Entrou o texto dos quatro campos de moeda do título, a taxa estimada editável até o primeiro movimento, o título novo da renegociação com a taxa herdada e as 8 casas decimais em `Mov_Serie_Cotacao_Valor.Valor` (no DDL, `numeric(19,8)` por exceção no gerador). Sem entidade nem campo novo.

> **Respondido por Alberto em 26/10/2026 (D-N360, documento 14): "seguir com todas as sugestões e a precisão de 8 casas".** Li como a recomendação de cada pergunta (Q101-1, Q101-1a a Q101-1d) e, na Q101-1e, como **8 casas decimais em `Mov_Serie_Cotacao_Valor.Valor`**. Nada foi aplicado: entra na revisão 24, quando você mandar consolidar. Se a sua intenção foi outra em alguma das perguntas, me diga.

*Detalhamento pedido por Alberto em 26/10/2026 ("detalhar Q101-1"). Os quatro campos entraram no dicionário na revisão 21 (D-N346, documento 108) com a marca "confirmar". Este documento mostra o que a Q101-1 pergunta, como os campos funcionam hoje, e **cinco pontos que achei ao detalhar** (Q101-1a a Q101-1e). **Nada foi alterado no dicionário.** As recomendações valem só depois do seu "sim"; as leituras de norma e de prática de mercado são minhas e não foram conferidas no texto oficial.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **A pergunta.** O título a pagar ou a receber em moeda estrangeira ganha **quatro campos** (moeda, valor na moeda, taxa estimada e data da taxa), e o `Valor_Titulo` passa a ser, nesses títulos, o **valor estimado em reais**. A taxa estimada vem **da série de cotações** na data da emissão e é **editável** (documento 101, seção 4.1).
- **O que já existe.** Os quatro campos estão em `Mov_Titulo` desde a revisão 21. Se você responder "sim", **nada muda no dicionário**: sai só a marca "confirmar".
- **O que eu achei ao detalhar** (cinco pontos, seção 6): (a) título que nasce de parcela de pedido ou de empréstimo em reais, e o "valor negociado, nunca recalculado"; (b) qual data a `Data_Taxa_Estimada` guarda quando a emissão cai em dia sem cotação; (c) até quando a taxa pode ser editada; (d) a taxa do título novo da renegociação; (e) a precisão de 4 casas decimais da série de cotações.
- **Sem campo novo.** Nenhuma das recomendações cria campo; as respostas mudam só o texto de algumas descrições e a precisão de um campo no DDL.

# 2. A pergunta, como está no documento 101

> **Q101-1.** Os 4 campos no título (moeda, valor na moeda, taxa estimada, data da taxa) e a nova descrição do `Valor_Titulo` (valor estimado em reais nos títulos em moeda)? A taxa estimada vem **da série** na data da emissão, editável? *Recomendação: sim; data da emissão por padrão.*

Ela nasce da sua resposta à Q100-18 (documento 100): "tem que ter o que tem que pagar em moeda; pode ter uma coluna do valor convertido em reais para referência; a moeda no contas a pagar e receber tem que ser informada; o valor em reais é estimado e o efetivo só se sabe no fechamento do câmbio". Os quatro campos são a "coluna em reais para referência" e a moeda que você pediu.

# 3. O que o dicionário tem hoje em `Mov_Titulo`

| Campo | Tipo lógico | Tipo no DDL (PostgreSQL) | Regra hoje |
|---|---|---|---|
| `ID_Moeda_Titulo` | referência a `Cad_Moeda`, opcional | bigint | A moeda em que o título é pago ou recebido. **Vazio = moeda funcional da empresa**, como todos os títulos de hoje. Informada por quem lança o título |
| `Valor_Titulo_Moeda` | número, opcional | numeric(19,4) | Quanto se deve **na moeda do título**. Obrigatório quando a moeda difere da funcional. É o valor **real** do título |
| `Taxa_Estimada` | número, opcional | numeric(15,8) | A taxa que estima o valor em reais e contabiliza o título no nascimento. Obrigatória quando a moeda difere da funcional. Sugerida da série na `Data_Taxa_Estimada`, **editável** |
| `Data_Taxa_Estimada` | data, opcional | date | O dia da taxa estimada (por padrão a `Data_Emissao`). Na renegociação, o dia da renegociação |
| `Valor_Titulo` (campo que já existia) | número | numeric(19,4), obrigatório | Continua em **reais**; nos títulos em moeda é o **valor estimado**: `Valor_Titulo_Moeda` × `Taxa_Estimada`, arredondado pelas casas da moeda funcional |

**O que o banco garante hoje:** nada além do tipo. Não há restrição de "os quatro preenchidos juntos ou os quatro vazios" nem de "moeda diferente da funcional": as regras de "obrigatório quando" ficam na camada de integração, como em outros campos do dicionário.

**Onde a taxa estimada é lida depois:** na `Mov_Titulo_Reavaliacao` (o campo `Valor_Reais_Anterior` da primeira reavaliação parte dela) e nos relatórios que mostram o valor em aberto em reais estimados (Q101-6). **Onde ela não entra:** no Y520 e na baixa. O que saiu da empresa é o `Valor_Pago_Reais` da baixa, calculado com a taxa do câmbio digitada no pagamento (documento 100).

# 4. Como os campos funcionam (regras do documento 101, com o detalhe)

1. **Quando o título é em moeda estrangeira.** Quando `ID_Moeda_Titulo` está preenchido e é diferente da moeda funcional da empresa (`Cad_Empresa.ID_Moeda_Funcional`, pela filial do título). Nesse caso os quatro campos são preenchidos juntos. Se quem lança informar a **própria moeda funcional**, o ERP trata como título em moeda funcional e deixa os quatro vazios.
2. **O valor estimado.** `Valor_Titulo` = `Valor_Titulo_Moeda` × `Taxa_Estimada`, arredondado pelas `Casas_Decimais` da moeda funcional. É só referência; o valor real é o da moeda.
3. **Sentido da taxa.** Reais (moeda funcional) **por uma unidade** da moeda do título, o mesmo par `Cad_Serie_Cotacao.ID_Moeda_Origem` (a estrangeira) e `ID_Moeda_Destino` (a funcional). Escrevo isso porque o dicionário só diz "taxa" e o sentido não estava dito.
4. **De onde vem a taxa sugerida.** Da série marcada para o par de moedas (`Cad_Serie_Cotacao.Uso_Fechamento`, em regra a PTAX de venda do Banco Central, documento 112) e a **última cotação com data até a `Data_Taxa_Estimada`** (regra da Q112-2: em sábado, domingo e feriado vale a do último dia útil). A recomendação é usar **a mesma série do fechamento** também aqui, para o título e a reavaliação do mês falarem da mesma taxa; **o contador ainda confirma o critério** (Q101-9). Quando a moeda não tem série marcada, ou não há cotação até a data, a tela **pede a taxa** a quem lança (o título não é gravado sem ela).
5. **Editável.** Quem lança pode trocar a taxa sugerida, por exemplo pela taxa combinada em contrato. A taxa digitada vale como a do título; o ERP não a compara com a série.
6. **Títulos que já existem.** Ficam sem moeda (moeda funcional); nenhuma carga.
7. **Reprogramação.** O título novo nasce na **mesma moeda** (Q101-7, respondida). Ver o ponto da seção 6 (Q101-1d) sobre a taxa dele.
8. **Pedido, parcela, empréstimo e nota fiscal.** Continuam em reais; a moeda é informada na hora de lançar o título (Q101-5, ainda com a marca "confirmar").

# 5. Exemplos (valores ilustrativos)

**Exemplo 1: emissão em dia sem cotação.** Título a pagar de **US$ 10.000**, lançado com `Data_Emissao` de **sábado, 31/10/2026**. Não há PTAX no sábado; vale a de **sexta, 30/10/2026**. Suponha, como valor ilustrativo, PTAX de venda de **5,30**.

| Passo | Resultado |
|---|---|
| Taxa sugerida | 5,30 (cotação de 30/10) |
| `Valor_Titulo` estimado | 10.000 × 5,30 = **R$ 53.000,00** |
| Quem lança troca a taxa por 5,32 (a do contrato) | `Taxa_Estimada` = 5,32; `Valor_Titulo` = **R$ 53.200,00** |
| `Valor_Titulo_Moeda` | **US$ 10.000**, nos dois casos: é o valor real |

**Exemplo 2: renegociação.** O título acima fica com saldo de **US$ 7.000** e é reprogramado em **terça, 17/11/2026**. No fechamento de outubro, o saldo foi reavaliado a 5,30 (R$ 37.100). Suponha PTAX de **5,35** no dia 17.

| Taxa do título novo | Saldo contabilizado do título novo | Diferença para o título antigo |
|---|---|---|
| **A do dia da renegociação** (como está no documento 101 e na revisão 21): 5,35 | 7.000 × 5,35 = R$ 37.450 | **R$ 350** sem lançamento que a reconheça (a reprogramação não tem lote, seção 6) |
| **A última contabilizada do título antigo** (recomendação): 5,30 | 7.000 × 5,30 = R$ 37.100 | Nenhuma; a reavaliação do fim do mês leva o saldo à taxa de fechamento |

# 6. Cinco pontos que achei ao detalhar

## Q101-1a. Título que nasce de uma parcela em reais

Hoje o `Valor_Titulo` é **copiado da parcela** do pedido, da parcela do empréstimo ou do valor da nota, e a descrição diz "fidelidade ao valor já negociado, nunca recalculado". A Q101-5 deixa o usuário informar a moeda **em qualquer origem**, e aí `Valor_Titulo` passa a ser `Valor_Titulo_Moeda` × `Taxa_Estimada`, que **não é** o valor da parcela. As duas descrições se contradizem nesse caso.

- **A (recomendação):** vale a moeda. `Valor_Titulo_Moeda` é digitado, `Valor_Titulo` vira o estimado, e a parcela de origem só empresta número e vencimento. A tela **avisa** quando o estimado difere do valor em reais da parcela, sem bloquear.
- **B:** só título **sem parcela de origem** (avulso, comissão, royalty e reprogramação) pode ser em moeda; nota e empréstimo em reais ficam em reais.

## Q101-1b. Que data a `Data_Taxa_Estimada` guarda

No Exemplo 1 a emissão é de sábado, 31/10, e a cotação é de sexta, 30/10. Guardar 31/10 diz o dia **pedido**; guardar 30/10 diz o dia **da cotação lida**. Na reavaliação já existem os dois (`Data_Reavaliacao` e `Data_Referencia_Taxa`, documento 112); no título só existe um campo de data.

- **Recomendação:** guardar **o dia da cotação usada**, para auditar; quando a taxa é digitada à mão, guarda a data a que ela se refere (padrão: a emissão). **Não proponho campo novo para a série**: como a taxa é editável, nem sempre há série por trás, e a reavaliação já guarda a sua.

## Q101-1c. Até quando a taxa estimada pode ser editada

A taxa estimada é a de partida da primeira reavaliação (`Valor_Reais_Anterior`) e a do lançamento do nascimento. Se for trocada **depois** de uma reavaliação, de uma baixa ou de um crédito aplicado, o que já foi contabilizado fica com outra taxa.

- **Recomendação:** editável **até o primeiro movimento** (baixa, aplicação de crédito, encontro de contas ou reavaliação). Depois disso, a correção é cancelar o título (`Status` = cancelado) e lançar outro, ou o contador faz o ajuste por lançamento. Sem campo novo: é regra da camada de integração.

## Q101-1d. Taxa do título novo da renegociação

A revisão 21 diz que a `Data_Taxa_Estimada` do título novo é **o dia da renegociação** (Exemplo 2). Pelo documento 101 (regra 4), o saldo do título novo parte da `Taxa_Estimada`, e o saldo do título antigo estava contabilizado na última taxa dele. Se as duas são diferentes, o valor em reais da dívida muda **sem pagamento**, e `Mov_Titulo_Reprogramacao` **não tem lote contábil** para lançar essa diferença. **Não verifiquei** se a Contabilidade lança algo na renegociação por outro caminho.

- **Recomendação:** o título novo nasce com a **taxa em que o saldo antigo estava contabilizado** (a da última reavaliação, ou a `Taxa_Estimada` do título antigo) e com a data dessa taxa. A reavaliação do fim do mês leva o saldo à taxa de fechamento, que é onde a variação cambial já é reconhecida. Mudaria só o texto de `Taxa_Estimada` e de `Data_Taxa_Estimada`.
- **Alternativa:** manter a taxa do dia, e então o ERP precisa lançar a diferença como variação cambial na renegociação, o que exige **lote na reprogramação** (campo novo, não proposto aqui).

## Q101-1e. Precisão da cotação (respondida: 8 casas)

`Mov_Serie_Cotacao_Valor.Valor` está com **4 casas decimais** no DDL (`numeric(19,4)`), porque o gerador dá essa precisão a todo campo chamado `valor`; `Taxa_Estimada` e as demais taxas têm 8. Para dólar e euro, 4 casas é o que a PTAX publica (conferir no site do Banco Central, como no documento 112); para moeda de **valor unitário pequeno** (por exemplo o iene), 4 casas dão poucos algarismos significativos: **ilustrativo**, 10.000.000 de ienes a 0,0349 contra 0,03487 dá R$ 300 de diferença. **Resposta de 26/10/2026: 8 casas.** Li como a precisão do `Valor` da série (que vale também para as séries de índice, como o IPCA, que usam o mesmo campo); não li como decisão do mapa de precisão numérica inteiro (D-5, documento 31), que segue sem resposta. Varri o dicionário e **não achei outro campo de taxa fora dessa exceção**: os campos de taxa de câmbio se chamam `Taxa_*` e já têm 8 casas. **Efeito:** `numeric(19,8)` no DDL para esse campo, por exceção no gerador; o dicionário não ganha campo, só uma frase na descrição.

# 7. O que muda no dicionário conforme as respostas

| Resposta | Efeito |
|---|---|
| **Q101-1: sim** | Nada no dicionário. Sai a marca "confirmar" dos quatro campos |
| Q101-1a (A) | Só o texto de `Valor_Titulo` e de `Valor_Titulo_Moeda`: a moeda prevalece sobre a parcela, com aviso |
| Q101-1b | Só o texto de `Data_Taxa_Estimada` |
| Q101-1c | Só texto (`Taxa_Estimada`); regra da camada de integração |
| Q101-1d (recomendação) | Só o texto de `Taxa_Estimada` e de `Data_Taxa_Estimada`. A alternativa pede um campo novo na reprogramação |
| Q101-1e (8 casas) | Exceção no gerador do DDL (`Mov_Serie_Cotacao_Valor.Valor` em `numeric(19,8)`) e uma frase na descrição do campo; sem campo novo |

**Sem entidade nova e sem campo novo** em nenhuma das recomendações. **Do lado do DDL**, a equipe pode acrescentar uma restrição de "os quatro campos juntos ou vazios" em `Mov_Titulo`, porque estão na mesma tabela; é detalhe do gerador, não do dicionário.

# 8. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q101-1** | **Respondida (sim, 26/10/2026).** Aprova os 4 campos, a nova descrição do `Valor_Titulo` (estimado em reais nos títulos em moeda) e a taxa sugerida da série na data da emissão, editável? | Sim |
| **Q101-1a** | **Respondida (recomendação, 26/10/2026).** Título com parcela de origem em reais: vale a moeda informada (com aviso quando o estimado difere da parcela), ou só título sem parcela de origem pode ser em moeda? | A: vale a moeda, com aviso |
| **Q101-1b** | **Respondida (recomendação, 26/10/2026).** A `Data_Taxa_Estimada` guarda o dia da **cotação usada** (30/10 no exemplo) ou o dia **pedido** (31/10)? | O dia da cotação usada |
| **Q101-1c** | **Respondida (recomendação, 26/10/2026).** A taxa estimada é editável só até o primeiro movimento do título (baixa, crédito aplicado, encontro ou reavaliação)? | Sim |
| **Q101-1d** | **Respondida (recomendação, 26/10/2026).** O título novo da renegociação nasce com a taxa em que o saldo antigo estava contabilizado, e não com a do dia? | Sim, a taxa herdada |
| **Q101-1e** | **Respondida (26/10/2026): 8 casas decimais** na cotação. A equipe confere a precisão por moeda? | Substituída pela resposta |

# 9. Limites

- Li o documento 101, o dicionário na revisão 23 e o DDL do PostgreSQL. **Não executei** nada com dados.
- O funcionamento da PTAX (quatro consultas, compra e venda, dia útil anterior) vem do documento 112, que o tirou de artigo de blog; **conferir no site do Banco Central**. Os valores dos exemplos são ilustrativos.
- Não verifiquei como a Contabilidade contabiliza o nascimento do título em moeda quando a origem é nota fiscal, nem se a reprogramação lança alguma coisa por outro caminho (Q101-1d).
- O critério da taxa (venda única, e a PTAX como "taxa à vista" do CPC 02) segue com o contador (Q101-9, documento 38, seção 2.2).
