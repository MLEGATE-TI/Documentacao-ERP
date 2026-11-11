# Bônus da CSLL na Baixa do Título: Respostas da Q140-5 e Desenho — Documento 181

*Registra a resposta de Alberto de 06/11/2026 ao documento 180 e propõe o desenho que ela pede: o bônus é calculado por apuração, a guia entra pelo valor total, a baixa registra o valor pago e o desconto, e o desconto fica guardado para a ECF. **Nada foi aplicado ao dicionário**; entra na próxima consolidação, depois do seu "sim".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. O que você respondeu

> "O cálculo tem que ser feito normalmente pelo período de cada apuração. Vai entrar a guia de pagamento pelo valor total; na baixa tem que fazer a baixa pelo valor pago e indicar o desconto da CSLL; este desconto tem que ser registrado para usar na ECF."

| Pergunta do documento 180 | Como leio a sua resposta | Estado |
|---|---|---|
| **Q140-5a** (quais recolhimentos) | Cada apuração de CSLL calcula o seu bônus, pelo próprio período: estimativa mensal, trimestre e ajuste anual, como na opção A. | **Respondida** |
| **Q140-5c** (como o desconto chega ao pagamento) | Para o ERP, a guia (DARF) entra pelo **valor total**; o desconto aparece **na baixa**. É o desenho do ERP; o que a Receita faz na prática continua na pergunta 26 do documento 179. | **Respondida para o ERP** |
| **Q140-5d** (estimativas no ajuste anual) | Não foi dita. Como a guia e o título ficam pelo valor total, a leitura que segue do seu desenho é a do **valor extinto, o integral** (opção A): a estimativa abate no ajuste o valor total da guia. | **Consequência, a confirmar (Q181-3)** |
| **Q140-6e** (lançamento e ECF) | O desconto **tem que ser registrado para usar na ECF**; o lançamento contábil e a linha da ECF seguem abertos. | **Parcial** |
| Q140-5b, Q140-5e e Q140-6a a Q140-6d | Sem resposta. | Abertas |

# 2. O desenho que a resposta pede

**O que já existe e serve.** O título a pagar da guia nasce pelo valor total (via DCTFWeb, o dicionário já faz assim). A baixa do título (`Mov_Titulo_Baixa`) já tem `Valor_Desconto` ("desconto obtido"), `Valor_Pago_Reais` (o valor pago em reais) e `Valor_Financeiro` (o dinheiro que saiu). O saldo do título é o `Valor_Titulo` menos a soma de `Valor_Baixado`. O bônus (`Mov_Bonus_Adimplencia_Csll`) já liga ao título pago à vista pelo campo `Pago_A_Vista_Ate_Vencimento`.

**O que falta:** ligar o bônus à baixa que deu o desconto, e guardar o valor do desconto realmente dado, para a ECF ler de um lugar só.

**Fluxo proposto, com o exemplo do documento 180** (CSLL a pagar R$ 500.000,00; bônus de 2%, R$ 10.000,00):

1. A apuração confirma a linha de CSLL em R$ 500.000,00 (`Valor_A_Pagar`).
2. O ERP calcula o bônus da **linha** (`Mov_Bonus_Adimplencia_Csll`, situação `calculado`, provisório) e **mostra o valor previsto** na tela do título.
3. A guia entra pelo **valor total**: título de R$ 500.000,00.
4. Na baixa, a Tesouraria paga R$ 490.000,00. A baixa leva **`Valor_Baixado` de R$ 500.000,00** (extingue o título), **`Valor_Desconto` de R$ 10.000,00** e dinheiro de R$ 490.000,00 (`Valor_Financeiro`).
5. O ERP liga a baixa ao bônus, copia o desconto, **confirma** o bônus (situação `confirmado`, quando o contador aprova) e o deixa disponível para a ECF.
6. Se o título foi pago sem desconto (ou depois do vencimento), o bônus vira `perdido`.

**Campos previstos (+2):**

| Entidade | Campo novo | Tipo | Regra |
|---|---|---|---|
| `Mov_Bonus_Adimplencia_Csll` | `ID_Baixa` | referência (`Mov_Titulo_Baixa`), opcional | A baixa em que o desconto foi dado. Vazio até a baixa. Valida: a baixa é de título cuja origem é a guia da CSLL da apuração do bônus. |
| `Mov_Bonus_Adimplencia_Csll` | `Valor_Desconto_Na_Baixa` | número, opcional | Cópia do `Valor_Desconto` da baixa. **É o valor que a ECF usa.** Diferente de `Valor_Bonus_Concedido` (o calculado), gera aviso, não bloqueio: o desconto real é o do pagamento. |

Sem tipo de baixa novo e sem mudança em `Mov_Titulo_Baixa`. O contador pode, se quiser, separar a conta do desconto da CSLL das demais (Q140-6a): a regra seria "a baixa ligada a um bônus usa a conta do bônus".

**Regras do Motor (avisos, nunca bloqueio):**
- Baixa de título de CSLL com `Valor_Desconto` e sem bônus calculado (empresa sem selo, Simples Nacional, menos de 12 meses): aviso "desconto sem bônus previsto".
- Bônus calculado e baixa sem desconto até o vencimento: aviso e situação `perdido`.
- Desconto da baixa diferente do bônus calculado (limite anual, arredondamento): aviso com a diferença.

# 3. O que a ECF vai usar

Você disse que o desconto tem que ser registrado "para usar na ECF". O dicionário passa a ter o valor em `Valor_Desconto_Na_Baixa`, por apuração e por período. **Como a ECF o usa**, hoje não sei: não conferi o leiaute 12 (a planilha não está no meu ambiente). Os caminhos possíveis, que dependem da Q140-6:

| Se o contador escolher | A ECF usa o desconto para |
|---|---|
| Redução da despesa de CSLL (6a, opção A) | Nada no e-LALUR: o bônus fica abaixo do lucro antes dos tributos. O valor serve de conferência (a CSLL contabilizada líquida do bônus contra a CSLL devida). |
| Receita ou conta própria acima da linha (6a, B ou C) | A **exclusão** no e-LALUR e no e-LACS pelo valor do desconto, no período. |
| Linha própria no leiaute, se existir | A linha que a Receita responder (ponto 6 da pergunta 26 do documento 179). |

Nos três casos o **dado de partida é o mesmo** (`Valor_Desconto_Na_Baixa`), por isso o desenho não espera a resposta do contador.

# 4. Quadro de decisões e perguntas

| Item | Decisão |
|---|---|
| Cálculo por apuração | Registrada (Q140-5a). |
| Guia pelo valor total; desconto na baixa | Registrada (Q140-5c, no ERP). |
| +2 campos em `Mov_Bonus_Adimplencia_Csll` | **Proposta**; entra na consolidação depois do seu "sim" (Q181-2). |
| O campo `Vale_Estimativa_Mensal` do documento 180 | **Não é mais necessário** pela sua resposta (todo período calcula). Fica fora, salvo se você quiser a chave (Q181-4). |

# 5. Perguntas para você

**Q181-1.** Na baixa, o **`Valor_Baixado` é o valor total do título (R$ 500.000,00), com o desconto de R$ 10.000,00 e o dinheiro de R$ 490.000,00** (recomendo)? Se "baixar pelo valor pago" quer dizer **`Valor_Baixado` de R$ 490.000,00**, o título fica com **R$ 10.000,00 de saldo** (o saldo é o valor do título menos o valor baixado) e o desconto exigiria uma **segunda baixa**, de tipo próprio, sem dinheiro. As duas leituras guardam o desconto; a primeira é uma operação só, e a Tesouraria e a conciliação bancária leem o dinheiro (`Valor_Financeiro`) igual nas duas.

**Q181-2.** Aprova os **2 campos novos** (`ID_Baixa` e `Valor_Desconto_Na_Baixa`) e as três regras de aviso da seção 2, para a próxima consolidação? Recomendo **sim**.

**Q181-3.** Confirma que, no **ajuste anual**, as estimativas pagas com bônus abatem o **valor total da guia** (e não o valor pago)? Recomendo **sim**; é a consequência do seu desenho. Pergunta à Receita no ponto 4 da pergunta 26 do documento 179.

**Q181-4.** Quer ainda a chave `Vale_Estimativa_Mensal` no parâmetro (para desligar o bônus nas estimativas se a Receita disser que não valem)? Recomendo **não criar agora**: se a Receita disser que não, uma versão nova do parâmetro com o campo entra então.

# 6. Limites

- O texto da LC 225 e a planilha da ECF não estão no meu ambiente; o uso do desconto na ECF depende da Q140-6 e da resposta da Receita.
- A leitura de que a guia da CSLL entra pelo valor total "como o dicionário já faz" é a da seção de DCTFWeb do documento 10 (título nascido do débito e do DARF); não reabri o texto.
- Nada foi aplicado (continua a revisão 32: 1.107 entidades e 12.404 campos; com os 2 campos, previstos 12.406).
