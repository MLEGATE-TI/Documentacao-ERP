# Reavaliação mensal do adiantamento em moeda estrangeira (Q101-10) — Documento 120

> **Respostas de 27/10/2026 (documento 123, D-N368):** Q101-10a **sim** (entidade `Mov_Credito_Reavaliacao`, 15 campos, entra na revisão 25); Q101-10b: **todo crédito em moeda estrangeira** é reavaliado, não só o adiantamento financeiro (o campo `ID_Credito` e a regra 1 mudam; ver Q123-2); Q101-10c **sim**, vale o valor contabilizado da última reavaliação. **Q123-2 (27/10/2026): sim**, a `Taxa_Cambio` do crédito passa a ser obrigatória em todo crédito em moeda estrangeira.
>
> **Situação na revisão 24 (26/10/2026, documento 122).** A regra "reavaliar o adiantamento em moeda todo mês" entrou como texto de `Mov_Credito.ID_Moeda_Credito`. **A entidade `Mov_Credito_Reavaliacao` não entrou:** as Q101-10a a Q101-10c seguem sem resposta (documento 38).

*Desenho para aprovação, a partir da sua resposta de 26/10/2026 à Q101-10: "Sim, é calculada a variação cambial", que você esclareceu como **reavaliar o adiantamento em moeda todo mês** (e não só na aplicação contra o título). Isso **muda a regra 6 do documento 101**, que dizia que o adiantamento não era reavaliado. Proposta, nada consolidado: o dicionário só muda depois da sua aprovação dos campos e do "consolidar" (revisão 24). Os nomes de campo abaixo são meus. As leituras de norma são minhas e não foram conferidas no texto oficial.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Decisão sua (26/10/2026):** o adiantamento em moeda estrangeira é **reavaliado no fim de cada mês**, como o título, e a variação cambial é lançada (D-N361, documento 14). O documento 101 propunha o contrário (regra 6 e Q101-10).
- **O que falta desenhar:** onde gravar a reavaliação do adiantamento. Hoje a `Mov_Titulo_Reavaliacao` só aponta para título (`ID_Titulo` obrigatório), e nada guarda a reavaliação de um `Mov_Credito`.
- **Proposta:** **uma entidade nova**, `Mov_Credito_Reavaliacao`, com **15 campos**, no mesmo molde da `Mov_Titulo_Reavaliacao`. Sem campo novo em `Mov_Credito` nem em `Mov_Credito_Aplicacao`. O lançamento da variação reaproveita `Mov_Lote_Lancamento.Origem_Tipo` = `variacao_cambial`.
- **Efeito na aplicação do adiantamento** (regra 6 do documento 101): o valor efetivo deixa de ser o `Valor_Pago_Reais` da data do envio e passa a ser o **valor contabilizado do crédito** na última taxa. Isso evita contar a variação duas vezes.
- **O Y520 não muda:** o adiantamento continua indo ao Y520 pelo `Valor_Pago_Reais` da data em que o dinheiro saiu.
- **Ponto que o contador precisa confirmar:** o que conheço do CPC 02 é que adiantamento a fornecedor por bens ou serviços é **item não monetário**, que em regra **não se reavalia**. A sua decisão é outra, e o ERP segue a sua. **Não li o CPC 02 inteiro** (documento 112, limites); a confirmação do contador entra na seção 2.2 do documento 38.

# 2. Suas respostas e como as li

| Pergunta | Sua resposta | Como leio |
|---|---|---|
| **Q101-10** (documento 101): "O adiantamento em moeda não é reavaliado (item não monetário) e a variação só aparece quando ele é aplicado contra o título?" | "Sim, é calculada a variação cambial", esclarecida na pergunta de 26/10/2026 como **"Reavaliar todo mês"** | A resposta à pergunta, tal como escrita, ficou ambígua (o "sim" confirmaria o contrário). Perguntei, e você escolheu reavaliar todo mês. **Respondida: reavaliar** |

# 3. O que o dicionário tem hoje

| Peça | O que existe | Lacuna |
|---|---|---|
| Adiantamento em moeda | `Mov_Credito`: `ID_Moeda_Credito`, `Valor_Credito` (na moeda), `Taxa_Cambio` (digitada no envio), `Valor_Pago_Reais` (snapshot do que saiu), `ID_Lote` do lançamento do adiantamento | Nada guarda a reavaliação do mês |
| Aplicação contra o título | `Mov_Credito_Aplicacao.Valor_Aplicado` (na moeda do crédito, que tem de ser a do título) | A diferença de câmbio na aplicação usava `Valor_Pago_Reais` (regra 6 do documento 101) |
| Reavaliação do título | `Mov_Titulo_Reavaliacao` (15 campos): `ID_Titulo`, `ID_Periodo_Fechamento`, `Data_Reavaliacao`, `Saldo_Moeda`, `Taxa_Fechamento`, `ID_Serie`, `Data_Referencia_Taxa`, `Valor_Reais_Anterior`, `Valor_Reais_Novo`, `Variacao_Reais`, `ID_Lote`, `Status`, `ID_Usuario`, `Data_Hora` | Só para título |
| Taxa de fechamento | Série marcada em `Cad_Serie_Cotacao.Uso_Fechamento`, última cotação até o último dia do mês (documento 112, Q112-1 e Q112-2) | Nenhuma: vale a mesma para o adiantamento |

# 4. Proposta: `Mov_Credito_Reavaliacao` (entidade nova, 15 campos)

*Uma linha por adiantamento em moeda e por mês fechado, enquanto o crédito tem saldo disponível. Contabilidade & Fiscal, sem vigência (é um fato). O estorno segue o estorno de lote que já existe (revisão 47).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Credito_Reavaliacao** | identificador | --- |
| **ID_Credito** | referência (`Mov_Credito`) | O adiantamento reavaliado. Só adiantamento em moeda estrangeira (`Origem_Tipo` = `adiantamento_financeiro` e `ID_Moeda_Credito` diferente da moeda funcional), com saldo disponível no fim do mês |
| **ID_Periodo_Fechamento** | referência (`Cad_Periodo_Fechamento`, `ID_Bloco` = contabilidade) | O mês. Crédito e período são únicos |
| **Data_Reavaliacao** | data | O último dia do período |
| **Saldo_Moeda** | número | O saldo disponível **na moeda do crédito** na data: `Valor_Credito` menos as aplicações (`Valor_Aplicado`) até a data |
| **Taxa_Fechamento** | número | A taxa de fechamento do mês, a mesma regra do título: série marcada para o fechamento, última cotação com data até a `Data_Reavaliacao` (PTAX de venda, taxa única; o contador confirma o critério, Q101-9) |
| **ID_Serie** | referência (`Cad_Serie_Cotacao`) | A série de onde a taxa foi lida (guarda o critério daquele mês) |
| **Data_Referencia_Taxa** | data | O dia da cotação lida (pode ser anterior à `Data_Reavaliacao`) |
| **Valor_Reais_Anterior** | número | O saldo em reais **antes**: `Saldo_Moeda` × a taxa em que estava contabilizado (na primeira reavaliação, a `Taxa_Cambio` do envio; depois, a da reavaliação anterior) |
| **Valor_Reais_Novo** | número | O saldo em reais **depois**: `Saldo_Moeda` × `Taxa_Fechamento` |
| **Variacao_Reais** | número | `Valor_Reais_Novo` − `Valor_Reais_Anterior`, com sinal. **Sentido invertido em relação ao título:** no adiantamento que **demos** (`Tipo` = pagar, um direito a receber bens ou serviços), positivo é **ganho**; no que **recebemos** (`Tipo` = receber, uma obrigação), positivo é **perda** |
| **ID_Lote** | referência (`Mov_Lote_Lancamento`) | O lançamento contábil da variação, com `Origem_Tipo` = `variacao_cambial` |
| **Status** | enumeração {efetivada, estornada} | `estornada` quando o período é reaberto e o lote estornado |
| **ID_Usuario** | referência (`Cad_Usuario`) | Quem executou a reavaliação do mês |
| **Data_Hora** | data/hora | Quando |

*Segundo o padrão do dicionário, `Variacao_Reais` e os valores em reais seguem a regra do sufixo `Com_Sinal` (D-N344) só onde o campo aceita sinal; aqui o sinal é dado pelo próprio campo, e o nome fica como no título para as duas entidades andarem juntas. **Se você preferir o sufixo, troco.***

**Alternativa A (não recomendo):** em vez de entidade nova, tornar `ID_Titulo` opcional em `Mov_Titulo_Reavaliacao` e acrescentar `ID_Credito`, exatamente um dos dois preenchido. Poupa uma entidade, mas deixa o nome da tabela enganoso, afrouxa a obrigatoriedade do título e mistura, na mesma consulta, o sentido de ganho e perda que são opostos.

# 5. Regras propostas

1. **Quem é reavaliado.** Só o adiantamento **financeiro** em moeda estrangeira com saldo disponível no fim do mês. O crédito não financeiro (bonificação, cashback, crédito tributário) não tem dinheiro enviado e não entra (pergunta Q101-10b).
2. **Fim do mês.** O fechamento do mês passa a executar a reavaliação dos títulos **e** dos adiantamentos. Como na revisão 22, o fechamento **espera a cotação**: sem a taxa da moeda, a reavaliação do mês lista a pendência (área de inconsistências, Q113-11 do documento 38) e não grava.
3. **Crédito totalmente aplicado** não é reavaliado: a parte aplicada já saiu do saldo.
4. **Aplicação contra o título** (muda a regra 6 do documento 101). A parte aplicada sai do saldo do crédito pelo **valor contabilizado dele** na última taxa (a da última reavaliação, ou a `Taxa_Cambio` do envio se ainda não houve reavaliação). Esse valor é comparado com o valor contabilizado da parte do título quitada. A **diferença**, se houver, é a variação cambial realizada na aplicação, em `Mov_Lote_Lancamento` com `Origem_Tipo` = `variacao_cambial`. Quando os dois já foram reavaliados com a mesma taxa no último fechamento, a diferença é zero.
5. **Estorno.** Estornar a aplicação devolve o valor ao saldo do crédito e estorna a variação da aplicação; a reavaliação do mês fechado só se estorna com o período reaberto, como a do título.
6. **Y520.** Sem mudança: o adiantamento vai ao Y520 pelo `Valor_Pago_Reais` da data em que o dinheiro saiu, e a aplicação não é novo pagamento (documento 100, seção 7, regra 14).
7. **Imposto.** No regime de caixa, a parte não realizada da variação precisa ser neutralizada na apuração (adição e exclusão, e o controle na parte B do e-Lalur). **Não verifiquei** se o desenho do lucro real (documento 93) cobre isso; é assunto do contador, e agora alcança o adiantamento também.

# 6. Exemplo (refaz o da seção 6 do documento 101)

Título de **US$ 10.000**, contabilizado a **5,00** (R$ 50.000). **Adiantamento** de **US$ 3.000** pago a **4,90** (saíram R$ 14.700). Valores ilustrativos.

| Momento | Título | Adiantamento | Variação no resultado |
|---|---|---|---|
| Envio do adiantamento | | Contabilizado R$ 14.700. **Vai ao Y520** | Nenhuma |
| Fim do mês 1, taxa 5,20 | R$ 50.000 → R$ 52.000 | **R$ 14.700 → R$ 15.600** (reavaliado, o que muda em relação ao documento 101) | Título: **perda não realizada de R$ 2.000**. Adiantamento: **ganho não realizado de R$ 900** |
| Aplicação dos US$ 3.000 | Parte quitada contabilizada a 5,20 = R$ 15.600. Saldo US$ 7.000 | Parte aplicada contabilizada a 5,20 = R$ 15.600 | **Zero** (os dois a 5,20; no documento 101 esse ganho de R$ 900 só aparecia aqui) |
| Fim do mês 2, taxa 5,30 | Saldo US$ 7.000: R$ 36.400 → R$ 37.100 | (sem saldo, não reavalia) | **Perda não realizada de R$ 700** |
| Baixa do restante, câmbio a 5,25 | Saem R$ 36.750 (US$ 7.000 × 5,25). **Vai ao Y520** | | **Ganho realizado de R$ 350** (37.100 contra 36.750) |

Resultado total: perda de R$ 2.000 + ganho de R$ 900 + zero + perda de R$ 700 + ganho de R$ 350 = **perda de R$ 1.450**, igual à do documento 101 e à diferença entre o que o título custou (R$ 14.700 + R$ 36.750 = R$ 51.450) e o estimado (R$ 50.000). **O total não muda; muda o mês em que o ganho de R$ 900 aparece** (mês 1, e não na aplicação). O Y520 recebe R$ 14.700 e R$ 36.750, como antes.

# 7. O que isto toca em outros documentos e módulos

| Onde | O que muda |
|---|---|
| Documento 101, regra 6 e Q101-10 | Superados por este documento (o adiantamento é reavaliado) |
| Contabilidade | O fechamento do mês reavalia também os adiantamentos; a variação na aplicação compara valores contabilizados |
| Tesouraria e relatórios | O saldo de adiantamento em moeda em reais passa a mostrar o valor contabilizado na última taxa, marcado como estimativa quando não há fechamento recente |
| Documento 38, seção 2.2 | O ponto "adiantamento não reavaliado, CPC 02" vira "adiantamento reavaliado, o contador confirma" |

# 8. Contagem, se aprovado

| Item | Entidades | Campos |
|---|---|---|
| `Mov_Credito_Reavaliacao` | 1 | 15 |
| Sobre a revisão 23 (922 entidades e 9.998 campos) | **923 entidades e 10.013 campos** | |

Mudam, só no texto, as descrições de `Mov_Credito.Valor_Pago_Reais` (deixa de ser o "valor efetivo" da aplicação) e do fechamento do mês. A contagem **não soma** o que você já respondeu e ainda não entrou (documentos 93, 96, 101 e 119), que também espera o "consolidar".

# 9. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q101-10** | **Respondida (26/10/2026): reavaliar o adiantamento em moeda todo mês** (D-N361) | Respondida |
| **Q101-10a** | Aprova a entidade nova `Mov_Credito_Reavaliacao` com os **15 campos** da seção 4 (em vez de generalizar `Mov_Titulo_Reavaliacao`, alternativa A)? | Entidade nova |
| **Q101-10b** | Só o adiantamento **financeiro** em moeda é reavaliado; o crédito não financeiro fica de fora? | Sim |
| **Q101-10c** | Na aplicação contra o título, o valor efetivo do crédito passa a ser o **valor contabilizado** dele (e não o `Valor_Pago_Reais`), e a diferença para o título é a variação realizada (regra 4)? | Sim |
| **Contador** | Confirma a reavaliação do adiantamento em moeda (o que conheço do CPC 02 é item não monetário, em regra não reavaliado) e o efeito fiscal no regime de caixa? | Seção 2.2 do documento 38 |

# 10. Limites

- Não li o CPC 02 inteiro nem a IN RFB 1.079/2010 no texto oficial (documento 112). A classificação do adiantamento como item não monetário é o que conheço; a decisão de reavaliar é sua, e o contador confirma.
- Os números do exemplo são ilustrativos.
- Não verifiquei se há relatórios que leem o saldo do adiantamento em reais; a descrição nova obriga a leitura do valor contabilizado.
- Nada foi alterado no dicionário.
