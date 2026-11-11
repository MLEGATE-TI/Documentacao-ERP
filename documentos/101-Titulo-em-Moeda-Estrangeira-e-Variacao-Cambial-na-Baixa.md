# Título em Moeda Estrangeira e Variação Cambial na Baixa — Documento 101 (versão 4)

> **Atualização da revisão 24 (26/10/2026, documento 122, D-N360 a D-N364).** As respostas às Q101-1, Q101-8 (e 8a a 8g) e Q101-10 entraram no dicionário **como texto** dos campos de `Mov_Titulo`, `Mov_Titulo_Baixa`, `Mov_Titulo_Reprogramacao_Item` e `Mov_Credito`, mais o campo novo `Mov_Titulo_Baixa.Valor_Arredondamento_Com_Sinal` e a precisão de 8 casas na cotação da série. **A regra 5 (desconto e juros) e a regra 6 (adiantamento) deste documento mudaram:** desconto e juros em moeda são convertidos pela taxa da baixa e ficam fora da variação cambial; o adiantamento em moeda é reavaliado todo mês. A entidade da reavaliação do adiantamento (documento 120) **não entrou**, porque as Q101-10a a Q101-10c estão sem resposta.

> **Consolidado na revisão 21 (23/10/2026, documento 108), exceto a seção 4.3 sobre crédito aplicado e encontro de contas (Q101-3b, sem resposta).** As contagens abaixo são as de quando o documento foi escrito. As Q101-1, Q101-5 e Q101-8 entraram no dicionário com a marca "confirmar".

*Proposta de desenho, que nasce da sua resposta à Q100-18 (documento 100): "tem que ter o que tem que pagar em moeda; pode ter uma coluna do valor convertido em reais para referência; a moeda no contas a pagar e receber tem que ser informada; o valor em reais é estimado e o efetivo só se sabe no fechamento do câmbio". A versão 2 incorporou as suas respostas às Q101-2, Q101-3 e Q101-4; a **versão 3** (22/10/2026) incorpora as respostas sobre o **adiantamento**, a **variação cambial no fim do mês** e a **renegociação na moeda de origem**; a **versão 4** (22/10/2026) incorpora a resposta Q105-3 (taxa digitada também nas formas sem contrato de câmbio). É um relatório e uma proposta: **nada foi alterado no dicionário**. Só entra depois das suas respostas e do seu "consolidar", com a lista de campos que você tiver visto.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Princípio que as suas respostas fixam:** **tudo que abate um título em moeda estrangeira é lançado na moeda do título**: a baixa, a renegociação, o adiantamento e a compensação. O real entra **no fechamento do câmbio**, pela taxa que quem paga digita. A estimativa em reais do título é só referência.
- **Variação cambial em duas etapas (Q101-4, respondida):** no **fim de cada mês**, o saldo dos títulos em moeda **não compensados** é reavaliado pela taxa de fechamento do mês, e a variação vai ao resultado. Na **quitação**, o ajuste final é a diferença entre a última taxa em que o saldo ficou contabilizado e a **taxa do fechamento do câmbio**, que é "o que saiu da empresa". Para isso proponho **uma entidade nova**, `Mov_Titulo_Reavaliacao` (13 campos).
- **Adiantamento em moeda:** o adiantamento (`Mov_Credito`, tipo `adiantamento_financeiro`) ganha moeda, taxa e o valor pago em reais, como a baixa. Ele é o **pagamento** que vai para o Y520 (documento 100); a aplicação dele contra o título **não é novo pagamento**.
- **Renegociação (Q101-7, respondida):** **sempre na moeda de origem**, sem mudar de moeda.
- **Total deste documento:** **1 entidade nova e 22 campos**: 4 em `Mov_Titulo`, 2 em `Mov_Titulo_Baixa`, 3 em `Mov_Credito` e 13 na entidade nova.
- **O Y520** depende destes campos só para títulos e adiantamentos em moeda estrangeira.
- **Perguntas:** 7 abertas (seção 9).

# 2. Suas respostas e como as li

| Pergunta | Sua resposta | Como leio | Efeito |
|------------------|---------------------------|---------------------------|---------------------------|
| **Q101-2** | "A baixa do título é feita na moeda do título, e nesta baixa você tem o câmbio para converter para real" | A baixa **não escolhe moeda**: é a do título. Quem baixa digita o valor **na moeda do título** e a **taxa**; o real sai da conta | `Taxa_Cambio` e `Valor_Pago_Reais` na baixa (seção 4.2) |
| **Q101-3** | "As renegociações têm que ser em moeda. Não posso converter uma renegociação com uma empresa do exterior em reais" | A reprogramação, o título novo e os valores reprogramados ficam na **moeda do título** | Só mudam as descrições (seção 4.3) |
| **Q101-7** | "A renegociação sempre em moeda de origem" | O título novo **nasce na mesma moeda**; não há mudança de moeda na renegociação | Resposta fechada; a taxa estimada do título novo é a do dia da renegociação |
| **Q101-4** | "A variação cambial tem que ser feita no final do mês para títulos não compensados, e só vai ser ajustada finalmente na quitação com o fechamento de câmbio, que é o pagamento efetivo e o que saiu da empresa" | **Reavaliação mensal adotada** para título em moeda **com saldo em aberto** no fim do mês; **ajuste final** na quitação pelo câmbio efetivo | Entidade `Mov_Titulo_Reavaliacao` (seção 4.5) e regras 4 a 6 |
| Adiantamento (resposta ao documento 100) | "O adiantamento entra como pagamento e tem que ir para o Bloco Y; quando for compensado, ele reduz o valor pago" | No Y520, o adiantamento conta **na data em que o dinheiro saiu**; quando ele é aplicado contra o título, o título **só leva ao Y520 o que sobrou a pagar em dinheiro** | `Mov_Credito` em moeda (seção 4.4); documento 100, seção 7, regra 14 |

# 3. O que o dicionário já tem e o que falta

| Peça | O que existe | Lacuna |
|-----------------------------|-----------------------------------|-----------------------------------|
| Moeda | `Cad_Moeda` (ISO 4217, casas decimais), `Cad_Empresa.ID_Moeda_Funcional` | Nenhuma |
| Taxa por data | `Cad_Serie_Cotacao` (tipo taxa de câmbio, par de moedas) e `Mov_Serie_Cotacao_Valor` (histórico por data), revisão 35 | Nenhuma |
| Lançamento contábil multimoeda | `Mov_Lancamento`: `ID_Moeda_Origem`, `Valor_Moeda_Origem` e `Valor_Moeda_Funcional` (snapshot) | Nenhuma |
| Variação cambial | Contabilidade, seção 15: `Mov_Lote_Lancamento` com `Origem_Tipo` = `variacao_cambial`, disparada **só na liquidação**, pela diferença entre o valor convertido na origem e na liquidação | Falta o **título** com moeda; falta a **reavaliação do mês**; a taxa de comparação na liquidação passa a ser a **última contabilizada** |
| Critério fiscal das variações | `Cad_Perfil_Empresa.Criterio_Variacao_Monetaria` {caixa, competencia, caixa_oscilacao_cambial} (revisão 19, MIT) | Nenhuma |
| Título | `Mov_Titulo.Valor_Titulo` (um número, sem moeda); saldo em reais | Moeda, valor na moeda e taxa estimada |
| Baixa | `Mov_Titulo_Baixa`: `Valor_Baixado`, `Valor_Desconto`, `Valor_Juros_Multa` em reais | Taxa do câmbio e total pago em reais |
| Adiantamento | `Mov_Credito`: `Origem_Tipo` = `adiantamento_financeiro`, `Data_Credito`, `Valor_Credito`, `ID_Conta_Contabil` (banco); a aplicação é `Mov_Credito_Aplicacao.Valor_Aplicado` | Moeda, taxa e valor pago em reais |
| Reprogramação, aplicação de crédito, encontro de contas | `Valor_Reprogramado`, `Valor_Aplicado` e `Valor_Encontro`, em reais | Só a descrição: passam a ser na moeda do título |
| Pedido, parcela e empréstimo | Nenhum tem moeda | Não proponho mexer agora (Q101-5) |

# 4. Proposta de campos

## 4.1 `Mov_Titulo` (4 campos novos)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|------------------|-----------------------------|-----------------------------------------------------|
| **ID_Moeda_Titulo** | *referência (Cad_Moeda, opcional)* | A moeda em que o título deve ser pago ou recebido. **Vazio = moeda funcional da empresa**, como todos os títulos de hoje, que não mudam. Informada por quem lança o título. |
| **Valor_Titulo_Moeda** | *número, opcional* | Quanto se deve **na moeda do título**. Obrigatório quando a moeda difere da funcional. É o valor **real** do título nesse caso. |
| **Taxa_Estimada** | *número, opcional* | A taxa usada para estimar o valor em reais e para contabilizar o título no nascimento. Obrigatória quando a moeda difere da funcional. Sugerida da série de cotações na `Data_Taxa_Estimada` e **editável**. |
| **Data_Taxa_Estimada** | *data, opcional* | O dia da taxa estimada (por padrão a `Data_Emissao`; Q101-1). Na renegociação, o dia da renegociação. |

**Alteração de descrição, sem campo novo:** `Valor_Titulo` continua em **reais**. Nos títulos em moeda estrangeira passa a ser o **valor estimado**: `Valor_Titulo_Moeda` × `Taxa_Estimada`, arredondado pelas casas da moeda funcional. É a "coluna em reais para referência" que você pediu.

## 4.2 `Mov_Titulo_Baixa` (2 campos novos)

*A baixa de título em moeda estrangeira é lançada **na moeda do título**: `Valor_Baixado`, `Valor_Desconto` e `Valor_Juros_Multa` passam a ser, nesse caso, **na moeda do título** (nos títulos em reais, nada muda).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|-------------------|-------------------|--------------------------------------------------------------|
| **Taxa_Cambio** | *número, opcional* | A taxa do **fechamento do câmbio**, **digitada** por quem paga ou recebe (Q100-17). **Sem contrato de câmbio** (cartão, depósito em conta no exterior, recursos mantidos no exterior, moeda), vale **a taxa que o operador do financeiro digita do pagamento** (Q105-3, 22/10/2026). Obrigatória quando o título é em moeda estrangeira; vazia nos demais. A série de cotações só serve de sugestão na tela. |
| **Valor_Pago_Reais** | *número, opcional* | O total pago ou recebido **em reais**: (`Valor_Baixado` − `Valor_Desconto` + `Valor_Juros_Multa`) × `Taxa_Cambio`, arredondado pelas casas da moeda funcional. Calculado pelo ERP e guardado como snapshot (como `Mov_Lancamento.Valor_Moeda_Funcional`). É **o que saiu da empresa**: o valor da conciliação bancária, da variação cambial final e do Y520 (antes das retenções). |

**A moeda da baixa é a do título**; não há campo de moeda na baixa. O lançamento contábil guarda a moeda e o valor de origem em `Mov_Lancamento`.

## 4.3 Sem campo novo, só nova descrição

| Entidade e campo | Nova descrição |
|-------------------------------------------|---------------------------------------------------------|
| `Mov_Titulo_Reprogramacao_Item.Valor_Reprogramado` | Na moeda do título de origem. O título novo nasce com a **mesma moeda**, `Valor_Titulo_Moeda` igual a este valor, e `Valor_Titulo` em reais é a estimativa pela `Taxa_Estimada` do dia da renegociação |
| `Mov_Credito_Aplicacao.Valor_Aplicado` | Na moeda do crédito, que tem de ser a do título (Q101-3b) |
| `Mov_Titulo_Encontro_Contas.Valor_Encontro` | Na moeda do título (Q101-3b) |
| `Mov_Titulo.Valor_Titulo` | Valor estimado em reais nos títulos em moeda estrangeira (seção 4.1) |

## 4.4 `Mov_Credito` (3 campos novos): o adiantamento em moeda

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|-----------------|-----------------------------|------------------------------------------------------|
| **ID_Moeda_Credito** | *referência (Cad_Moeda, opcional)* | A moeda do adiantamento. Vazio = moeda funcional. Em adiantamento em moeda, `Valor_Credito` passa a ser **na moeda do crédito**. |
| **Taxa_Cambio** | *número, opcional* | A taxa do fechamento do câmbio do adiantamento, **digitada** (sem contrato de câmbio, a que o operador do financeiro digita do pagamento, Q105-3). Obrigatória quando a moeda difere da funcional e `Origem_Tipo` = `adiantamento_financeiro`. |
| **Valor_Pago_Reais** | *número, opcional* | O que saiu (ou entrou) em reais: `Valor_Credito` × `Taxa_Cambio`. Snapshot, como na baixa. É o valor do Y520 do adiantamento (documento 100). |

## 4.5 `Mov_Titulo_Reavaliacao` (nova): a variação cambial do fim do mês

*Uma linha por título em moeda estrangeira e por mês fechado, enquanto o título tem saldo em aberto. Sem vigência (é um fato). O estorno segue o estorno de lote que já existe (revisão 47).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|-----------------|---------------------------------------|--------------------------------------------|
| **ID_Titulo_Reavaliacao** | *identificador* | --- |
| **ID_Titulo** | *referência (Mov_Titulo)* | O título reavaliado. Só título em moeda estrangeira, com saldo em aberto no fim do mês. |
| **ID_Periodo_Fechamento** | *referência (Cad_Periodo_Fechamento, ID_Bloco = contabilidade)* | O mês. Título e período são únicos (uma reavaliação por título por mês). |
| **Data_Reavaliacao** | *data* | O último dia do período. |
| **Saldo_Moeda** | *número* | O saldo em aberto **na moeda do título** na data (valor do título menos baixas, créditos, encontros, mais reprogramações). |
| **Taxa_Fechamento** | *número* | A taxa de fechamento do mês, lida da série de cotações na `Data_Reavaliacao` (Q101-9). |
| **Valor_Reais_Anterior** | *número* | O saldo em reais **antes**: `Saldo_Moeda` × a taxa em que estava contabilizado (a `Taxa_Estimada` ou a da reavaliação anterior). |
| **Valor_Reais_Novo** | *número* | O saldo em reais **depois**: `Saldo_Moeda` × `Taxa_Fechamento`. |
| **Variacao_Reais** | *número* | `Valor_Reais_Novo` − `Valor_Reais_Anterior`, com sinal: em título a pagar, positivo é **perda**; em título a receber, positivo é **ganho**. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento)* | O lançamento contábil da variação, com `Origem_Tipo` = `variacao_cambial` (seção 15 da Contabilidade). |
| **Status** | *enumeração {efetivada, estornada}* | `estornada` quando o período é reaberto e o lote estornado. |
| **ID_Usuario** | *referência (Cad_Usuario)* | Quem executou a reavaliação do mês. |
| **Data_Hora** | *data/hora* | Quando. |

# 5. Regras propostas

- **1. Saldo na moeda do título.** O saldo continua a fórmula de hoje (valor do título menos baixas, créditos aplicados e encontros, mais reprogramações), mas **na moeda do título**. Continua **derivado, nunca armazenado**.
- **2. Quitado.** O título em moeda está quitado quando o saldo na moeda chega a zero. O valor em reais pago **não decide** a quitação.
- **3. Valor em aberto em reais (estimado).** Saldo na moeda × taxa do dia da série (ou a última). **Sempre estimativa**, marcada assim nos relatórios, no fluxo de caixa projetado e na carteira. Nunca gravada.
- **4. Reavaliação do fim do mês (variação cambial não realizada).** No fechamento do mês, para cada título em moeda **com saldo em aberto** ("não compensado"), o ERP grava a `Mov_Titulo_Reavaliacao` e gera o lote de `variacao_cambial`. A taxa de partida é a última contabilizada (a `Taxa_Estimada` ou a taxa da reavaliação anterior); **o saldo fica contabilizado na taxa de fechamento**. Título sem saldo (quitado ou todo compensado) **não é reavaliado**.
- **5. Ajuste final na quitação (variação realizada).** Na baixa, o valor contabilizado da parte quitada é `Valor_Baixado` (na moeda) × a **última taxa contabilizada**; o valor efetivo é `Valor_Pago_Reais`, **o que saiu da empresa** (com desconto e juros convertidos). A diferença é a variação cambial **ainda não reconhecida**, em `Mov_Lote_Lancamento` com `Origem_Tipo` = `variacao_cambial`. Assim a soma das reavaliações e do ajuste final é a variação total, **sem contar duas vezes**. Muda a seção 15 da Contabilidade só na **taxa de comparação** (a última contabilizada, no lugar da de emissão).
- **6. Quitação por adiantamento ou outra compensação.** O valor efetivo é o do que **saiu da empresa**: no adiantamento, o `Valor_Pago_Reais` do `Mov_Credito`, na taxa em que o dinheiro foi enviado, proporcional ao `Valor_Aplicado`. A diferença para a última taxa contabilizada do título é a variação realizada na aplicação. O **adiantamento em si não é reavaliado** (é pagamento antecipado de bens ou serviços, que o CPC 02 trata como item não monetário; **a confirmar com o contador**, Q101-10).
- **7. Reprogramação, crédito aplicado e encontro de contas.** Seguem o princípio: **valores na moeda do título**. A reprogramação cria o título novo **na mesma moeda**, com `Taxa_Estimada` do dia. O crédito e o encontro só se aplicam entre itens **da mesma moeda**; entre moedas diferentes, o ERP **bloqueia com aviso** (Q101-3b).
- **8. Estorno de baixa.** Devolve ao saldo o valor na moeda e **estorna a variação cambial** do lote (o estorno de lote já existe, revisão 47).
- **9. Títulos que já existem.** Ficam sem moeda (moeda funcional). Nenhuma carga.
- **10. Y520.** O valor do Y520 (documento 100) é o `Valor_Pago_Reais`, da baixa ou do adiantamento, menos as retenções (que são em reais). Em título em reais, a fórmula é a mesma sem conversão.

# 6. Exemplo: um título em dólar, do início ao fim

Título de US\$ 10.000, lançado com taxa estimada 5,00 (R\$ 50.000, contabilizado a 5,00). Houve um **adiantamento** de US\$ 3.000 pago antes, a 4,90 (saíram R\$ 14.700).

| Momento | O que acontece | Variação cambial |
|------------------|-----------------------------------------|-----------------------------------------|
| Adiantamento | Saem R\$ 14.700 (US\$ 3.000 × 4,90). **Vai para o Y520**. Não é reavaliado | Nenhuma |
| Fim do mês 1 | Saldo em aberto US\$ 10.000 (o adiantamento ainda não foi aplicado). Taxa de fechamento 5,20: R\$ 50.000 → R\$ 52.000 | **Não realizada**: perda de R\$ 2.000 |
| Aplicação do adiantamento | US\$ 3.000 do título compensados. Efetivo = R\$ 14.700. Contabilizado = US\$ 3.000 × 5,20 = R\$ 15.600. Saldo US\$ 7.000 | **Realizada**: ganho de R\$ 900 (a dívida de R\$ 15.600 foi quitada com R\$ 14.700) |
| Fim do mês 2 | Saldo US\$ 7.000, de 5,20 para 5,30: R\$ 36.400 → R\$ 37.100 | **Não realizada**: perda de R\$ 700 |
| Baixa do restante | Câmbio fechado a 5,25: saem R\$ 36.750 (US\$ 7.000 × 5,25). **Vai para o Y520** só este valor | **Realizada**: ganho de R\$ 350 (37.100 contabilizado contra 36.750 efetivo) |

Resultado total: o título custou R\$ 14.700 + R\$ 36.750 = **R\$ 51.450**, contra os R\$ 50.000 estimados. A soma das variações no resultado: perda de R\$ 2.000 + ganho de R\$ 900 + perda de R\$ 700 + ganho de R\$ 350 = perda de **R\$ 1.450**, igual à diferença. O Y520 recebe **R\$ 14.700 + R\$ 36.750** e nunca o valor do título em reais.

*Os números são ilustrativos, para conferir a mecânica.*

**Quanto ao imposto.** O regime de reconhecimento das variações cambiais para IRPJ, CSLL, PIS e Cofins é **caixa** (tributa na liquidação) ou **competência** (tributa no período). Pela [IN RFB 1.079/2010](https://www.normaslegais.com.br/legislacao/in_rfb_1079_2010.htm), a regra geral é o regime de caixa, a opção pela competência é da empresa, só em janeiro (ou no início das atividades), vale o ano todo para os quatro tributos, e a troca de competência para caixa no meio do ano só é admitida com oscilação do dólar acima de 10% no mês. O dicionário **já tem** esse critério no perfil da empresa (`Criterio_Variacao_Monetaria`). A reavaliação mensal é contábil; **no regime de caixa**, a parte não realizada precisa ser neutralizada na apuração do imposto (adição e exclusão, e o controle na parte B do e-Lalur). **Não verifiquei** se o desenho do lucro real (documento 93) já cobre isso; é assunto do contador.

# 7. O que isto toca em outros módulos

| Módulo | O que muda |
|------------------------------------|----------------------------------------------------------------|
| Contas a pagar e receber | Os campos do título, da baixa e do adiantamento; saldo, "vencido" e "quitado" leem a moeda; relatórios mostram a moeda e a estimativa em reais |
| Contabilidade | `variacao_cambial` (seção 15) passa a ter a **reavaliação do mês** e a taxa de comparação na liquidação; entidade `Mov_Titulo_Reavaliacao`; fechamento do mês passa a executar a reavaliação |
| Tesouraria | O fluxo de caixa projetado usa o **valor estimado em reais**, marcado como estimativa; a conciliação bancária compara `Valor_Pago_Reais` com o extrato |
| Pedidos, empréstimos, notas fiscais | **Nada muda agora.** O usuário informa a moeda ao lançar o título (Q101-5) |
| ECF (Y520) | Documento 100: usa `Valor_Pago_Reais` da baixa e do adiantamento |
| Lucro real (e-Lalur) | Possível ajuste da variação não realizada no regime de caixa; **não verificado** |

# 8. O que não proponho (para não decidir por você)

- **Moeda no pedido, na parcela, no empréstimo e na nota.** Ficam em reais; o título em moeda nasce de lançamento do usuário.
- **Reavaliação do adiantamento**: não proponho (ver regra 6, a confirmar).
- **Reavaliação do empréstimo em moeda** e demais obrigações: fora deste documento.
- **Contrato de câmbio** como cadastro (corretora, número). Só o campo de referência do documento 100.
- **Hedge, juros em moeda e títulos em duas moedas.** Fora deste documento.
- **O ajuste fiscal da variação não realizada** (documento 93): assunto do contador.

# 9. Perguntas

**Ainda abertas (7)**

| Nº | Pergunta | Minha recomendação |
|-------|----------------------------------------------|----------------------------------------------|
| **Q101-1** | Os 4 campos no título (moeda, valor na moeda, taxa estimada, data da taxa) e a nova descrição do `Valor_Titulo` (valor estimado em reais nos títulos em moeda)? A taxa estimada vem **da série** na data da emissão, editável? | Sim; data da emissão por padrão |
| **Q101-3b** | **Crédito aplicado e encontro de contas** em moeda do título, e só entre itens **da mesma moeda**? (O adiantamento em moeda tem 3 campos novos, seção 4.4.) | Sim, pelo mesmo princípio da renegociação |
| **Q101-5** | A moeda do título é informada **por quem lança**, em qualquer origem (avulso, nota fiscal, empréstimo), **sem** mexer em pedido, parcela, empréstimo e nota? | Sim |
| **Q101-6** | O "valor em aberto" do título em moeda aparece nos relatórios e no fluxo de caixa **em reais estimados, marcado como estimativa**, com a moeda ao lado? | Sim |
| **Q101-8** | Confirma a leitura da baixa: quem baixa digita **na moeda do título** o valor baixado, o desconto e os juros, e digita a **taxa**; o ERP calcula o total pago em reais (`Valor_Pago_Reais`); `Valor_Baixado`, `Valor_Desconto` e `Valor_Juros_Multa` passam a ser **na moeda do título** quando o título é em moeda? | Sim; toda leitura em reais desses campos passa a usar `Valor_Pago_Reais` |
| **Q101-9** | Qual **taxa de fechamento do mês** a reavaliação usa (por exemplo, a PTAX de venda do último dia útil) e de **qual série** de `Cad_Serie_Cotacao`? | **Pergunta ao contador**; a série é parâmetro por moeda |
| **Q101-10** | O **adiantamento em moeda não é reavaliado** (item não monetário) e a variação só aparece quando ele é aplicado contra o título? | Sim, **a confirmar com o contador** (CPC 02) |

**Respondidas por você (22/10/2026):** Q101-2 (a baixa é na moeda do título), Q101-3 (as renegociações são em moeda), Q101-4 (a reavaliação é feita no fim do mês para os títulos não compensados, com ajuste final na quitação pelo câmbio efetivo) e Q101-7 (a renegociação é sempre na moeda de origem). Sobre o adiantamento: entra como pagamento no Y520 e, quando compensado, o título só leva o que sobrou a pagar.

# 10. Contagem

| Item | Entidades | Campos |
|-------------------------------------------------------------------------|---------------|-----------|
| `Mov_Titulo`: moeda, valor na moeda, taxa estimada e data da taxa | 0 | 4 |
| `Mov_Titulo_Baixa`: taxa do câmbio e total pago em reais | 0 | 2 |
| `Mov_Credito`: moeda, taxa do câmbio e total pago em reais | 0 | 3 |
| `Mov_Titulo_Reavaliacao` | 1 | 13 |
| **Total** | **1** | **22** |

O documento 100 passa a ter **3 entidades e 51 campos** na proposta mínima (a classificação ganha o campo do adiantamento). Somados os dois: **4 entidades e 73 campos** (5 e 81 com os opcionais do documento 100). Sobre a revisão 20 (915 entidades e 9.878 campos): **919 entidades e 9.951 campos** (920 e 9.959 com os opcionais). Mudam, só no texto, as descrições dos campos da seção 4.3, de `Valor_Baixado`, `Valor_Desconto`, `Valor_Juros_Multa`, `Valor_Credito` e do saldo em aberto.

# 11. Limites deste documento

- Li a IN RFB 1.079/2010 por resumo da página, não o texto integral, e **não** li o CPC 02. A classificação do adiantamento como item não monetário é o que conheço da norma; **a decisão é do contador**.
- Não verifiquei se o desenho do lucro real (documento 93) já neutraliza a variação cambial não realizada no regime de caixa.
- Não verifiquei todos os relatórios que leem `Valor_Titulo`, `Valor_Baixado`, `Valor_Credito` ou o saldo em reais (carteira, aging, fluxo de caixa, DRE gerencial). A mudança de descrição dos campos **obriga** essas leituras a usar o valor em reais nos itens em moeda; a consolidação precisaria varrer todas.
- O exemplo da seção 6 é aritmético e ilustrativo; confira a contabilização das contas (fornecedores em moeda, variação ativa e passiva) com o contador.
- Nada foi alterado no dicionário. A revisão 21 só nasce depois do "consolidar".
