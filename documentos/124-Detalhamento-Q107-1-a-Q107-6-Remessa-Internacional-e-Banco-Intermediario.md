# Detalhamento da Q107-1 a Q107-6: a remessa internacional e o banco intermediário — Documento 124

> **Aprovado por Alberto em 27/10/2026 ("sim aprovo", D-N371, documento 14).** Li como sim às seis perguntas do documento 107 e aos sete pontos novos deste documento, inclusive o campo `Taxa_Cambio_Contrato_Previo` (+1 campo); se a aprovação era só de parte, diga qual. **Nada foi aplicado ao dicionário**: entra na revisão 25 depois do seu "consolidar" (929 entidades e 10.096 campos com o que já espera). Onde o texto abaixo diz "sem resposta", vale esta nota.

> *(Texto de antes da aprovação:)* **Sem resposta às Q107-1 a Q107-6 e nada aplicado.** O dicionário continua na **revisão 24** (925 entidades e 10.033 campos); a revisão 25 (928 entidades e 10.074 campos) ainda espera o seu "consolidar". Este documento **não substitui** o documento 107: mostra como a remessa ao exterior funciona de ponta a ponta com o que já foi decidido **depois** dele (revisões 21 a 24) e traz **sete pontos novos** (Q107-1a a Q107-6a) que achei ao detalhar. Onde o documento 107 e este divergem, vale este, se você aprovar.

*Detalhamento pedido por Alberto em 27/10/2026 ("detalhar Q107-1 a Q107-6"). As leituras de norma, de prática bancária e de contabilidade são minhas e **não foram conferidas** no texto oficial nem com o banco do cliente.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **A proposta continua a mesma:** 1 entidade nova (`Mov_Remessa_Bancaria_Item_Exterior`, uma linha por item de remessa que vai ao exterior), 3 campos no dado bancário do fornecedor (banco intermediário) e 3 campos no retorno do banco (contrato de câmbio, taxa e valor em reais). Total **1 entidade e 21 campos**, mais 1 valor novo em `Forma_Lancamento` (`transferencia_internacional`).
- **O que mudou desde o documento 107** (seção 3): o documento 107 foi escrito em 22/10/2026, antes das decisões sobre a baixa em moeda (revisões 21 a 24). Duas regras dele precisam de ajuste: **o valor em reais do retorno não vira `Valor_Pago_Reais`** (que é calculado pelo ERP; o valor do retorno serve para **conferir** contra o extrato, com a tolerância de R$ 0,04), e a ordem só existe quando **o banco do favorecido está no exterior**, e não sempre que o participante é não residente.
- **Sete pontos novos**, todos com recomendação: um campo opcional a mais na ordem (taxa do contrato fechado antes), a ordem ao exterior numa remessa só dela, a conferência do valor em reais contra o extrato, o que entra no valor em reais do retorno, quando a ordem existe, a sugestão de `Responsavel_Tarifas` pelo histórico, e a trava da natureza do título depois que a ordem sai.
- **Contagem se tudo for aprovado como recomendo:** 1 entidade e **22 campos** (os 21 do documento 107 mais 1 do ponto Q107-1a). Sobre a revisão 24: **926 entidades e 10.055 campos**; somada à revisão 25 prevista: **929 entidades e 10.096 campos** (os totais do documento 107, 921 e 9.992, partiam da revisão 20 e estão superados).

# 2. As perguntas do documento 107 e a situação

| Nº | Pergunta | Recomendação do documento 107 | Situação |
|---|---|---|---|
| **Q107-1** | A ordem ao exterior fica numa **entidade própria**, uma linha por item de remessa (15 campos)? | Sim | Sem resposta |
| **Q107-2** | O **retorno** traz o contrato de câmbio, a taxa e o valor em reais (3 campos), e a baixa automática os usa, com o operador podendo corrigir? | Sim | Sem resposta; **ajustada** na seção 5 |
| **Q107-3** | A **forma do Y520** é deduzida da moeda da ordem e confirmada na tela ao gerar a remessa? | Sim; o contador confirma as formas 1 e 2 | Sem resposta; **ajustada** na seção 5 |
| **Q107-4** | `Responsavel_Tarifas` é **obrigatório e sem valor padrão** do ERP? | Sim | Sem resposta |
| **Q107-5** | O **banco intermediário** fica só no dado bancário do **fornecedor** e na ordem? | Sim | Sem resposta |
| **Q107-6** | A **natureza do câmbio** da ordem é sempre a do título? | Sim | Sem resposta; **ponto novo** (Q107-6a) |

# 3. O que mudou desde o documento 107

| Tema | O documento 107 dizia | O que vale hoje | Efeito |
|---|---|---|---|
| **Valor em reais na baixa automática** (regra 4) | A baixa copia `Taxa_Cambio_Ocorrencia` e `Valor_Reais_Ocorrencia` para `Taxa_Cambio` e `Valor_Pago_Reais` | `Valor_Pago_Reais` é **calculado** pelo ERP, com um só arredondamento: (valor baixado − desconto + juros) × taxa. O dinheiro que o banco movimentou é conferido contra `Valor_Financeiro`; a diferença de até **R$ 0,04** fica em `Valor_Arredondamento_Com_Sinal`; acima disso a baixa **não é confirmada** (documento 121, Q101-8b e Q101-8f; revisão 24) | **Muda a regra 4**: só a **taxa** é copiada; o valor em reais do retorno é **conferência** (ponto Q107-2a) |
| **Retorno sem a taxa** (regra 5) | A baixa fica "pendente de taxa" e nada trava o retorno | Sem aprovação do banco ou sem a taxa do contrato, o item **fica pendente e não gera baixa** (Q101-8d). A área de inconsistências (`Mov_Processo_Inconsistencia`, Q113-11, aprovada; entra na revisão 25) passa a mostrá-lo | Igual na substância; o texto diz "sem baixa" |
| **Quando a natureza é obrigatória** | Obrigatória na entrada do título de não residente (Q103-2) | Vale para pagamento ou recebimento com não residente, **inclusive em reais** (Q103-10) | A ordem sempre tem natureza a copiar |
| **Forma do Y520** | Deduzida da moeda da ordem | Há **três fontes** da forma: conta da empresa no exterior (formas 4 e 5, documento 106), forma prevista no título e histórico do participante, além da ordem | Falta a **ordem de precedência** (ponto Q107-3a) |
| **Data do Y520** | Não tratada | É a `Data_Ocorrencia` do retorno ligado à baixa (Q111-1) | Na ordem ao exterior, é a data em que o banco registra o câmbio e a saída do dinheiro |
| **Contagem** | 921 entidades e 9.992 campos (base: revisão 20) | Revisão 24: 925 entidades e 10.033 campos | Atualizada na seção 6 |

# 4. Como funciona, passo a passo

1. **Título.** O fornecedor do exterior é participante não residente. O título nasce em moeda estrangeira, com a natureza da operação (obrigatória) e a taxa estimada (documento 119). O dado bancário do fornecedor traz banco (SWIFT), IBAN, roteamento e, se houver, o banco intermediário (documento 106 e seção 4.2 do documento 107).
2. **Remessa.** O financeiro inclui o título numa remessa de pagamento. Como o banco do favorecido está **no exterior**, o item sai com `Forma_Lancamento` = `transferencia_internacional` e o ERP exige a **ordem ao exterior** (a linha da entidade nova). A tela mostra: moeda e valor da ordem, banco, SWIFT, IBAN, intermediário, **natureza** (copiada do título), **forma do Y520** (deduzida) e `Responsavel_Tarifas` (a escolher). Gerar a remessa é "o momento do pagamento" (Q103-8): sem forma, natureza e responsável pelas tarifas, a remessa não é gerada.
3. **Banco.** O ERP **não envia mensagem SWIFT**: o banco executa a ordem, fecha o câmbio e devolve o retorno. O plugin do banco traduz o que o ERP guarda para o que o banco aceita (arquivo, API ou portal; o canal real **não verifiquei**, seção 9).
4. **Retorno.** Traz, na ocorrência aceita: o **número do contrato de câmbio**, a **taxa do contrato** e o **valor em reais debitado pelo câmbio**. O IOF e as tarifas, quando vêm, entram nos campos que já existem.
5. **Baixa automática.** Nasce do retorno aceito: `Valor_Baixado` na moeda do título, `Taxa_Cambio` = taxa do retorno, `Valor_Pago_Reais` **calculado**. O ERP confere o valor em reais do retorno contra `Valor_Financeiro`: até R$ 0,04 de diferença fica em `Valor_Arredondamento_Com_Sinal`; acima, o item fica pendente na área de inconsistências até alguém corrigir a taxa.
6. **Y520.** A classificação nasce `classificada` com a **forma** e a **natureza** da ordem e a referência = número do contrato (documento 100, regras 1 e 10). A data é a da ocorrência do retorno.
7. **Variação cambial.** Lançada no lote da baixa, como no documento 121: a diferença entre o saldo contabilizado (última taxa) e o valor pela taxa do contrato.

## Exemplo (valores ilustrativos)

Título a pagar de **US$ 8.000,00** a um fornecedor na Alemanha, contabilizado na última taxa a **5,10** (R$ 40.800,00). Ordem gerada em 10/11, com `Responsavel_Tarifas` = dividido. O banco fecha o câmbio a **5,19876543** (taxa com 8 casas).

| Passo | Conta | Resultado |
|---|---|---|
| Ordem (`Mov_Remessa_Bancaria_Item_Exterior`) | Moeda US$; valor US$ 8.000,00; natureza copiada do título; SWIFT, IBAN e país do banco; tarifas = dividido | Linha única do item |
| Retorno | Contrato nº (informado pelo banco); taxa 5,19876543; valor do câmbio em reais **R$ 41.590,13** | |
| `Valor_Pago_Reais` (calculado) | 8.000 × 5,19876543 = 41.590,12344, arredondado | **R$ 41.590,12** |
| Conferência com o extrato | 41.590,13 − 41.590,12 | **+ R$ 0,01**, dentro da tolerância: grava `Valor_Arredondamento_Com_Sinal` = +0,01 e a baixa é confirmada |
| Variação cambial | 41.590,12 − 40.800,00 | **R$ 790,12** (perda, lançada no lote) |
| Y520 | Valor = R$ 41.590,12 (sem retenção neste exemplo); forma 1; natureza e referência da ordem | A diferença de R$ 0,01 **não entra** |

**Se a taxa viesse errada** (por exemplo, 5,1987 em vez de 5,19876543): 8.000 × 5,1987 = R$ 41.589,60; a diferença para o extrato é de R$ 0,53, **acima de R$ 0,04**: a baixa **não é confirmada** e o item fica pendente até a taxa ser corrigida.

**O que "dividido" quer dizer** (fonte na seção 9): a fonte diz só que a tarifa é dividida entre as duas partes. A minha leitura é que o remetente paga a tarifa do banco dele e o favorecido arca com as do lado dele, recebendo o valor líquido; "remetente" paga todas e "favorecido" arca com todas. O ERP **só registra a escolha**; o efeito no valor que o fornecedor recebe é do banco.

# 5. As seis perguntas, uma a uma

## Q107-1. Entidade própria para a ordem ao exterior

**O que decide:** onde ficam SWIFT, IBAN, roteamento, país, natureza, tarifas e intermediário da ordem.

| Opção | Como fica | Efeito |
|---|---|---|
| **A (recomendada)** | Entidade nova, uma linha por item de remessa ao exterior, 15 campos | O item de remessa (33 campos, quase todos "só quando cobrança" ou "só quando pagamento") não ganha mais 15 campos opcionais; a regra "o item ao exterior exige a linha" fica explícita |
| **B** | 15 campos opcionais direto no item | Menos uma tabela, mas o item passa a 48 campos, e a maioria fica vazia em todo pagamento nacional |

**Os 15 campos e de onde vêm** (cópia do que foi transmitido, como já é no item):

| Campo | Origem da cópia |
|---|---|
| `ID_Item_Remessa` (única), `ID_Moeda` | O item; a moeda do título |
| `ID_Natureza_Operacao_Cambial` | O título (Q107-6) |
| `Codigo_Swift_Favorecido`, `Nome_Banco_Favorecido`, `ID_Pais_Banco_Favorecido` | `Cad_Instituicao_Financeira` do banco do favorecido |
| `Iban_Favorecido`, `Codigo_Roteamento_Favorecido` | `Cad_Participante_Dados_Bancarios` |
| `Endereco_Favorecido` | O endereço do participante, em texto único |
| `Responsavel_Tarifas` | Escolhido ao gerar (Q107-4) |
| `Codigo_Swift_Intermediario`, `Codigo_Roteamento_Intermediario`, `Conta_Intermediaria` | O dado bancário do fornecedor (Q107-5) |
| `Numero_Contrato_Cambio_Previo` | Digitado, só quando o câmbio foi fechado antes da ordem |

**Esclarecimento sem campo novo:** no item da ordem ao exterior, `Codigo_Banco_Favorecido` (3 posições, código de compensação brasileiro) fica **vazio**, porque banco estrangeiro não tem esse código; `Agencia_Favorecido` e `Conta_Favorecido` (até 5 e até 20) recebem a cópia do dado bancário quando existirem, e o **IBAN** fica na ordem. A validação do documento 107 ("IBAN ou número da conta") continua: o número da conta é o `Conta_Favorecido` do item.

### Q107-1a. Taxa do contrato fechado antes da ordem (ponto novo)

O documento 107 diz (regra 6) que a taxa **não é conhecida na geração da remessa**, porque o câmbio fecha na execução. Mas a ordem tem o campo `Numero_Contrato_Cambio_Previo`: quando **há contrato fechado antes**, a taxa **já é conhecida** na geração. Proposta: **1 campo opcional** na ordem.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **Taxa_Cambio_Contrato_Previo** | *número, opcional, 8 casas* | A taxa do contrato fechado antes, junto de `Numero_Contrato_Cambio_Previo` (obrigatório quando este está preenchido). Serve de **taxa sugerida** na baixa quando o retorno não a traz; quando o retorno traz a taxa, **vale a do retorno** |

**Por que recomendo:** a Q101-8d manda o item ficar pendente quando falta a taxa; com contrato fechado antes, o financeiro já tem a taxa e não precisaria digitá-la de novo. **Se não entrar**, o financeiro digita a taxa na área de inconsistências, como no caso geral.

### Q107-1b. A ordem ao exterior vai numa remessa só dela (ponto novo)

`Valor_Principal_Remessa` do item passa a estar na **moeda da ordem**; os demais itens do cabeçalho estão em reais, e o cabeçalho (`Mov_Remessa_Bancaria`) não guarda total, mas qualquer soma de remessa **misturaria moedas**. O canal e o layout da ordem ao exterior também podem ser outros (seção 9). **Recomendo a regra:** uma remessa de pagamento tem **só itens ao exterior** ou **só itens nacionais**, e a conta de origem da remessa ao exterior é uma conta **em banco brasileiro** (as formas 4 e 5 não passam por remessa; documento 107, seção 6). **Sem campo novo.**

## Q107-2. O retorno traz contrato, taxa e valor em reais

**O que decide:** que dados do câmbio voltam do banco e o que a baixa automática faz com eles.

| Campo do retorno | Regra |
|---|---|
| `Numero_Contrato_Cambio` | Vai para `Referencia_Operacao` da classificação do Y520 (Q101-8a). O título já pode ter o seu próprio, digitado na entrada |
| `Taxa_Cambio_Ocorrencia` | Copiada para `Taxa_Cambio` da baixa (a do contrato, Q100-17 e Q101-8) |
| `Valor_Reais_Ocorrencia` | **Conferência**, não cópia (ponto Q107-2a) |
| `Valor_Total_Ocorrencia` (existente) | Fica **na moeda da ordem** quando o item tem ordem ao exterior; a moeda vem da ordem (o item de retorno não tem campo de moeda) |

### Q107-2a. O valor em reais do retorno confere, não vira `Valor_Pago_Reais` (ponto novo)

O documento 107 mandava copiar `Valor_Reais_Ocorrencia` para `Valor_Pago_Reais`. Hoje esse campo é **calculado** (um só arredondamento no fim) e o dinheiro que o banco movimentou é conferido contra `Valor_Financeiro` (documento 121). **Recomendo:** `Valor_Reais_Ocorrencia` entra na **conferência**: diferença até R$ 0,04, para mais ou para menos, vai para `Valor_Arredondamento_Com_Sinal`; acima, a baixa **não é confirmada** e o item fica pendente (Q101-8f2). Como `Valor_Pago_Reais` não é digitado, "o operador pode corrigir o valor em reais" do documento 107 **cai**: corrige-se só a **taxa**, com motivo. **Sem campo novo; muda o texto do campo e a regra 4 do documento 107.**

### Q107-2b. O que o valor em reais do retorno inclui (ponto novo)

O banco debita da empresa o **câmbio** e, em geral, também **IOF** e **tarifas**. O Y520 trabalha com o total do **pagamento feito** (documento 100, regra 2), e o retorno já tem `Valor_IOF_Ocorrencia`. **Recomendo:** `Valor_Reais_Ocorrencia` é **só o valor do câmbio** (moeda × taxa), **sem IOF nem tarifas**; senão a conferência da Q107-2a falharia em toda ordem com IOF. Se o banco devolver só o **total debitado**, o operador separa na área de inconsistências. O tratamento contábil da tarifa e do IOF continua do contador (documento 107, regra 8).

**Fora das perguntas (sem campo, sem decisão):** se o banco do exterior **devolve** a ordem depois de aceita, o operador **estorna a baixa** pelo estorno que já existe (regra 8 do documento 101) e a ordem nova é outro item.

## Q107-3. A forma do Y520 é deduzida e confirmada

**O que decide:** como o ERP sugere a forma ao gerar a remessa. Hoje a forma é obrigatória na baixa e confirmada no momento do pagamento (Q103-8); a dedução só **sugere**.

### Q107-3a. Quando a ordem existe e qual sugestão vale (ponto novo)

**1) Quando existe a ordem.** O documento 107 (regra 1) a exigia para favorecido **não residente**. Mas um título **em reais** de não residente pode ser pago por TED ou Pix a uma conta do não residente **em banco no Brasil** (a Res. BCB 277 trata de contas de não residentes; seção 9): aí não há SWIFT, banco nem país no exterior. **Recomendo:** a ordem existe **somente quando o banco do favorecido está no exterior** (`Cad_Instituicao_Financeira.ID_Pais` diferente do Brasil); o item passa a `transferencia_internacional` por isso. Pagamento a conta de não residente em banco brasileiro segue como **item nacional** (TED ou Pix), com natureza e forma no Y520 do mesmo jeito.

**2) Ordem de precedência da forma sugerida** (a tela sempre deixa trocar, com confirmação):

| Ordem | Fonte | Forma sugerida |
|---|---|---|
| 1ª | Conta da empresa **no exterior** (documento 106, seção 5) | 4 (recebimento) ou 5 (pagamento). Não passa por remessa |
| 2ª | A **ordem ao exterior** (esta) | **1** se a ordem é em moeda estrangeira; **2** se é em reais |
| 3ª | `Forma_Pagamento_Exterior_Prevista` do título | A prevista |
| 4ª | Histórico do mesmo participante e tipo | A última classificada |

**O contador confirma** que ordem em reais para banco no exterior é a forma 2; pelo quadro do manual da ECF que li (documento 88), a forma 2 é "transferência internacional em reais", mas **não conferi como o banco a executa**.

## Q107-4. `Responsavel_Tarifas` obrigatório e sem valor padrão

**O que decide:** quem escolhe o responsável pelas tarifas e se o ERP preenche algo sozinho.

Os três valores do campo (`remetente`, `dividido`, `favorecido`) correspondem aos códigos SWIFT **OUR**, **SHA** e **BEN**. Na mensagem de pagamento em formato ISO 20022, o mesmo campo usa **DEBT**, **SHAR** e **CRED**, nessa ordem, no pagamento (fonte na seção 9). **O ERP guarda o valor em português e o plugin de cada banco faz a tradução**; não acrescento valor sem saber o canal.

### Q107-4a. Sugestão pelo histórico (ponto novo)

Você decidiu na Q102-6 que a sugestão da natureza vem da **base de conhecimento** que o sistema gera, e não de um padrão. **Recomendo o mesmo aqui:** o ERP **sugere** o responsável da **última ordem confirmada do mesmo participante**, quando houver, e o operador **confirma** a cada ordem (continua obrigatório, e sem histórico a tela vem vazia). Isso respeita "sem valor padrão do ERP". **Sem campo novo**: o histórico são as próprias ordens anteriores. **Alternativa:** um campo no cadastro do fornecedor com o responsável habitual (1 campo); não recomendo, porque duplica o histórico e envelhece.

## Q107-5. Banco intermediário só no fornecedor e na ordem

**O que decide:** onde o intermediário é guardado.

| Onde | O que entra |
|---|---|
| `Cad_Participante_Dados_Bancarios` (3 campos novos) | `ID_Instituicao_Intermediaria` (referência, opcional), `Codigo_Roteamento_Intermediario`, `Conta_Intermediaria`. O cadastro é versionado, e o histórico de mudança do intermediário fica nas versões |
| `Mov_Remessa_Bancaria_Item_Exterior` (3 campos, já contados nos 15) | A **cópia**: `Codigo_Swift_Intermediario`, `Codigo_Roteamento_Intermediario`, `Conta_Intermediaria` |
| Conta bancária **da empresa** | **Nada.** O intermediário da empresa só serviria para uma instrução de recebimento, que está fora (documento 107, seção 7) |

**Limite:** **um** banco intermediário por dado bancário. Se algum fornecedor exigir mais de um, **não está coberto**; **não verifiquei** se isso ocorre em pagamento de empresa. O banco intermediário é uma instituição de `Cad_Instituicao_Financeira` (país diferente do Brasil, SWIFT obrigatório), cadastrada uma vez.

## Q107-6. A natureza da ordem é sempre a do título

**O que decide:** de onde vem a natureza da ordem e se pode mudar na remessa.

**Recomendação mantida:** a ordem **copia** a natureza do título e **não a altera**; para mudar, corrige-se o título. A natureza **tem de ir na ordem** porque a classificação da operação em cada natureza é responsabilidade do cliente e o banco a registra no contrato de câmbio (fonte na seção 9; a página que li está marcada como desatualizada).

### Q107-6a. Trocar a natureza do título depois que a ordem saiu (ponto novo)

A ordem é **cópia do que foi enviado**; se a natureza do título muda depois, a ordem e o título **divergem**, e o Y520 nasce da ordem na baixa automática. **Recomendo:** **bloquear** a troca da natureza do título enquanto houver ordem gerada e **não rejeitada**; para trocar, a ordem é cancelada e refeita. A correção **posterior** à baixa continua do contador, na classificação (`Eh_Corrigido_Contador`), que não mexe na ordem. **Sem campo novo.**

# 6. O que muda no dicionário

| Resposta | Efeito | Campos |
|---|---|---|
| **Q107-1: sim** | Entidade `Mov_Remessa_Bancaria_Item_Exterior` com os 15 campos da seção 5; texto de `Valor_Principal_Remessa` (na moeda da ordem quando há ordem) e de `Codigo_Banco_Favorecido` (vazio na ordem ao exterior) | **+1 entidade, +15** |
| Q107-1a | `Taxa_Cambio_Contrato_Previo` na ordem | **+1** |
| Q107-1b | Regra da remessa (só itens ao exterior ou só nacionais; conta de origem no Brasil); sem campo | 0 |
| **Q107-2: sim** | 3 campos em `Mov_Retorno_Bancario_Item` (`Numero_Contrato_Cambio`, `Taxa_Cambio_Ocorrencia`, `Valor_Reais_Ocorrencia`); texto de `Valor_Total_Ocorrencia` (moeda da ordem); regra da baixa automática | **+3** |
| Q107-2a, Q107-2b | Texto de `Valor_Reais_Ocorrencia` e de `Valor_Arredondamento_Com_Sinal`; regra 4 do documento 107 substituída | 0 |
| **Q107-3: sim** | 1 valor novo em `Forma_Lancamento`; regra de sugestão da forma (precedência) | 0 |
| Q107-3a | Quando a ordem existe (banco do favorecido no exterior) e a precedência | 0 |
| **Q107-4: sim** | `Responsavel_Tarifas` (já contado nos 15); Q107-4a é regra de tela | 0 |
| **Q107-5: sim** | 3 campos em `Cad_Participante_Dados_Bancarios` | **+3** |
| **Q107-6: sim** | Natureza copiada; Q107-6a: trava de alteração do título | 0 |

**Contagem** (sobre a revisão 24: 925 entidades e 10.033 campos):

| Cenário | Entidades | Campos |
|---|---|---|
| Documento 107 como escrito (Q107-1, 2, 5) | +1 | +21 → **926 e 10.054** |
| Com a Q107-1a (recomendada) | +1 | +22 → **926 e 10.055** |
| Somado à revisão 25 prevista (928 e 10.074) | | **929 e 10.096** (com Q107-1a) |

A consolidação precisa varrer quem lê as entidades alteradas (remessa e retorno por arquivo CNAB e por API) e o texto da Tesouraria (documento 09, seção 6). O ER ganha 1 entidade com 4 relações (item de remessa, moeda, natureza e país do banco) e 1 relação nova em `Cad_Participante_Dados_Bancarios` (a instituição intermediária).

# 7. Perguntas

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q107-1** a **Q107-6** | As seis do documento 107 (seção 2 acima), com os ajustes das seções 3 e 5 | Sim às seis |
| **Q107-1a** | Entra o campo `Taxa_Cambio_Contrato_Previo` (opcional) na ordem, sugerida na baixa quando o retorno não traz a taxa? | Sim |
| **Q107-1b** | A remessa com ordem ao exterior só tem itens ao exterior e sai de conta em banco brasileiro? | Sim |
| **Q107-2a** | `Valor_Reais_Ocorrencia` só **confere** com o extrato (tolerância de R$ 0,04, acima disso a baixa não confirma) e `Valor_Pago_Reais` continua **calculado**; corrige-se só a taxa? | Sim |
| **Q107-2b** | `Valor_Reais_Ocorrencia` é **só o câmbio**, sem IOF nem tarifas? | Sim |
| **Q107-3a** | A ordem só existe quando o **banco do favorecido está no exterior**, e a forma sugerida segue a precedência da seção 5 (conta no exterior, ordem, forma prevista, histórico)? | Sim |
| **Q107-4a** | O ERP **sugere** o responsável pelas tarifas pela última ordem do participante, e o operador **confirma** sempre? | Sim |
| **Q107-6a** | A natureza do título **não pode ser trocada** depois que a ordem sai e não é rejeitada? | Sim |

**Para o contador e para o banco** (fora do desenho; se algum for relevante, vira pergunta depois):

- O **canal** da ordem ao exterior de cada banco do cliente (arquivo, API ou portal).
- Se a **lista de naturezas** que o banco usa no contrato de câmbio é **a mesma** do Y520 (`Cad_Natureza_Operacao_Cambial`, vinda da tabela da ECF). **Não verifiquei**; se forem listas diferentes, o ERP precisaria de um de-para.
- A forma 2 para ordem em reais ao exterior.
- O tratamento contábil da **tarifa** e do **IOF** do câmbio, e o efeito do `Responsavel_Tarifas` no valor que chega ao fornecedor sobre o "total do pagamento feito" do Y520 (o ERP não sabe quanto o banco do favorecido descontou).
- Se algum documento da operação de câmbio (fatura, contrato) precisa ser guardado.

# 8. Pontos que o desenho não faz

- O ERP **não envia SWIFT** nem cadastra contrato de câmbio (só a referência).
- Não há **instrução de recebimento** nem **limite e fracionamento** (documentos 104 e 107).
- Não há campo de **tarifa de câmbio**: tarifa e IOF vêm pelos campos do retorno que já existem.
- Não há **mais de um intermediário**.

# 9. Limites do que li

- Li o documento 107, o dicionário na revisão 24 (remessa, retorno, dados bancários, instituição, conta, título, baixa e classificação do Y520), os documentos 100, 103, 105, 106, 119, 121 e 123 e o histórico.
- **Tarifas.** O significado de OUR, SHA e BEN e a correspondência com os códigos DEBT, SHAR e CRED vêm da [página de documentação da Modern Treasury sobre o responsável pelas tarifas](https://docs.moderntreasury.com/payments/docs/charge-bearer), um fornecedor de pagamentos, e **não da especificação** da mensagem, que **não li**. A página diz que a correspondência é inferida das duas tabelas dela, e que **no ISO 20022 o código muda conforme a direção** (crédito ou débito); usei só a direção de pagamento.
- **Bancos.** A [página do Bradesco sobre ordem de pagamento ao exterior](https://banco.bradesco/html/corporate/solucoes-integradas/comercio-exterior/servicos-on-line/emissao-ordem-pagamento.shtm) descreve um canal online para pessoa física com limite baixo, e diz que contrato e ordem só se concluem após conferência e registro no Banco Central; não trata de empresa, de arquivo, de API nem de intermediário. A [página do Santander](https://www.santander.com.br/comercio-exterior-e-cambio/servicos-internacionais/ordem-de-pagamento-internacional) diz que a contratação é com o gerente e não lista dados, tarifas nem intermediário. **O canal real de cada banco do cliente continua a confirmar.**
- **Norma.** O resumo da [Res. BCB 277 no site Okai](https://okai.com.br/artigo/novidades-da-resolucao-277-do-banco-central-que-trata-da-regulamentacao-do-cambio-no-brasil) diz que o contrato de câmbio passa a ter formato livre com informações mínimas, e que a classificação da natureza é responsabilidade do cliente; a própria página está **marcada como desatualizada** e lista resoluções posteriores que alteraram a norma. **Não li o texto oficial.**
- Nada foi validado pelo contador nem testado com banco.
