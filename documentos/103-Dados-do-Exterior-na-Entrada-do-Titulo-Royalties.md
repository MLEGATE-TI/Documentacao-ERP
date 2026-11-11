# Dados do Exterior na Entrada do Título (Royalties e Demais Operações com Não Residente) — Documento 103 (versão 9)

> **Q103-6 respondida em 27/10/2026 (D-N374, documento 127): sim, o contador indica a natureza no cadastro de cálculo do royalty e ela fica na origem; a posição do campo é a Q127-5.**
>
> **Consolidado na revisão 21 (23/10/2026, documento 108).** As contagens abaixo são as de quando o documento foi escrito.

*Proposta de desenho, em resposta à sua mensagem de 22/10/2026 sobre royalties: o valor a pagar entra no contas a pagar ou a receber, e por isso **na hora da entrada** o usuário já tem de preencher as informações necessárias. Hoje (documentos 100 e 102) a classificação do Y520 nasce **na baixa**. Este documento move o essencial para a **entrada do título**. **Não altera o dicionário** (revisão 20: 915 entidades, 9.878 campos); as versões 2 e 3 (22/10/2026) incorporam as suas respostas **Q103-1 (sim)**, **Q103-2 (obrigatório)** e **Q103-3 (royalty sem nota entra como avulso; com nota entra pela nota)**, **Q103-5 (a faixa não fica presa ao dólar)**, **Q103-7 (os 3 campos entram)**, **Q103-8 (a forma é obrigatória na baixa, confirmada no momento do pagamento)**, **Q103-2a e Q103-9 ("sim para moeda estrangeira")**; a Q103-4 foi lida como respondida (previsão na entrada, forma definitiva na baixa) e você lembrou que a **data de vencimento é sempre obrigatória**. **Em 22/10/2026 você tirou a faixa de US\$ 50.000**, com o princípio de que **na baixa vale sempre o contrato de câmbio** (o valor efetivo que cai na conta); a regra 3 foi retirada e as perguntas Q103-5 e Q103-5a ficaram sem efeito. O resto segue como proposta.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Como li o que você disse:** o royalty (e qualquer outro pagamento ou recebimento com não residente) é lançado como **título** no contas a pagar ou a receber, **com o valor** (pelo documento 101, na **moeda do título**), e no mesmo momento o usuário informa o que o Y520 vai precisar. A baixa **herda** essas informações, em vez de o financeiro classificar tudo só na hora de pagar. Se eu li errado qual é "esse valor", a Q103-1 corrige.
- **O que muda no desenho:** a **natureza da operação** passa a ser informada **na entrada** do título (com a sugestão do documento 102 já aparecendo ali). A **forma de pagamento** (câmbio, cartão, depósito no exterior e assim por diante) continua sendo definida **na baixa**, porque só se sabe como se paga na hora de pagar; ela pode ser indicada antes, como previsão.
- **O que isso custa:** **3 campos opcionais em `Mov_Titulo`**, nenhuma entidade nova (seção 4).
- **Decidido por você (Q103-2):** a natureza é **obrigatória** na entrada do título de não residente. Isso troca a regra 10 do documento 100 ("nada bloqueia"): **sem natureza o título não é salvo**. Li "obrigatório" como valendo para **qualquer origem** de título, não só o lançamento manual; se for só o manual, a Q103-2a corrige.
- **A forma de pagamento (Q103-8):** é **obrigatória na baixa** e **confirmada no momento do pagamento**. Sem ela a baixa de título de não residente não é confirmada. Só o **restante** (referência, observação) segue sem bloquear.

# 2. O que o dicionário tem hoje sobre royalty

- Existe `Origem_Tipo = royalty_venda` em `Mov_Titulo`: o royalty **de venda**, que nasce de um item de pedido de venda (`ID_Item` de `Mov_Pedido_Venda_Item`), com valor lançado manualmente. É o royalty pago a um beneficiário por causa de uma venda.
- **Não há** origem própria para royalty de **licença de marca, patente, tecnologia ou programa** pago ou recebido do exterior, e **você decidiu que não precisa** (Q103-3): o royalty **normalmente não tem nota** e entra como **`avulso`**; nos **casos especiais em que há nota**, entra pelo contas a pagar da **nota** (`nota_fiscal_entrada`, ou `nota_fiscal_saida` no recebimento). `royalty_venda` continua só para o royalty de venda ligado a pedido.
- A tabela de naturezas da ECF tem os códigos próprios desse tipo de royalty (marcas e franquias `46112`, patentes e tecnologia `46129` e `46136`, direitos autorais e programas `47551` a `47582`), todos no grupo "Acima de US\$ 50.000,00 - Serviços diversos e outros". Os códigos resumidos de serviço (`46978`, `46992`) existem para o contrato de câmbio de valor menor; **quem decide é o contrato**, na escolha do financeiro. O contador confirma **qual código** vale para cada tipo de royalty (Q103-6).

# 3. Como fica o fluxo

| Momento | Hoje (documentos 100 e 102) | Proposto neste documento |
|----------------------|----------------------------------|----------------------------------|
| **Entrada do título** | Só moeda e valor (documento 101) | Moeda, valor, **natureza** (com sugestão do mapa) e, se quiser, **forma prevista** e **referência** (contrato ou fatura do exterior) |
| **Sugestão do mapa** | Aparece na baixa | Aparece **na entrada**; na baixa o financeiro **confirma ou troca** pelo que o contrato de câmbio classificou |
| **Baixa** | Nasce a classificação com tudo a preencher | Nasce a classificação (`Mov_Ecf_Operacao_Exterior`) **já preenchida** com os dados do título; a **forma é obrigatória e confirmada no momento do pagamento**; o financeiro pode trocar o resto |
| **Contador** | Corrige quando necessário (Q100-7) | Igual; vê também o que foi informado na entrada |
| **Adiantamento** | Classificado na data do crédito (documento 100, regra 14) | Não passa por título, então **natureza e forma são obrigatórias no próprio lançamento do crédito** (Q103-9) |

# 4. Campos propostos (3, opcionais, em `Mov_Titulo`)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial), opcional* | A natureza da operação, informada na entrada. **Obrigatória** (Q103-2) quando o participante é **não residente**. Tem de estar vigente na data da entrada; na baixa vale a vigente na data final da ECF. |
| **Forma_Pagamento_Exterior_Prevista** | *enumeração {as 6 formas do Y520}, opcional* | A forma que se espera usar. Serve só de ponto de partida para a baixa; a forma real fica na classificação da baixa. |
| **Referencia_Operacao** | *código (40), opcional* | Número do contrato, da fatura ou do documento do exterior. Copiado para a classificação da baixa (`Referencia_Operacao`). Não vai para a ECF. |

Contagem: **0 entidades, 3 campos**. O tipo (`recebido` ou `pago`) sai do `Tipo` do título e o país sai do cadastro do participante (Siscomex, 3 posições), então **não precisam de campo**.

# 5. Regras propostas

- **Regra 1. Quando se aplica (Q103-10).** Só quando o participante do título é **não residente** (`Condicao_Residencia`), **empresa ou pessoa**, e em **qualquer moeda, inclusive pagamento em reais**: o pagamento em reais a não residente também tem de ser classificado. Título de residente não mostra nem exige nada disso.
- **Regra 2. Sugestão na entrada.** Ao escolher o participante e, no caso de nota, os itens, o ERP aplica a regra 2 do documento 102 (histórico do participante primeiro, depois o mapa) e **preenche a natureza sugerida**. A pessoa confirma ou troca. Nunca grava sozinho. **Título avulso** (o caso normal do royalty, Q103-3) **não tem CFOP nem NBS**; a sugestão vem então só do **histórico do mesmo participante** ou de uma linha do mapa com `Origem_Tipo_Titulo = avulso` e o tipo. Para o **primeiro** royalty de cada participante, a pessoa escolhe a natureza na lista; as seguintes já vêm sugeridas.
- **Regra 3. Sem faixa de valor (decisão de 22/10/2026).** O ERP **não calcula faixa** de US\$ 50.000 nem converte moeda para sugerir a natureza. Na entrada vale a sugestão do mapa (código detalhado); **na baixa vale o contrato de câmbio**, e o financeiro confirma ou troca a natureza pelo que o banco classificou, resumido ou detalhado (documento 102, regra 4).
- **Regra 4. Herança na baixa.** A classificação da baixa nasce com `ID_Natureza_Operacao_Cambial` e `Referencia_Operacao` do título e a forma prevista como sugestão da forma. Trocar na baixa **não altera** o título; a classificação guarda o que valeu para o Y520.
- **Regra 5. Parcelas.** Título parcelado (royalty mensal, por exemplo): cada parcela é um título e **herda** a natureza do primeiro; a pessoa preenche uma vez. Cada baixa tem o seu contrato de câmbio e confirma ou troca a natureza.
- **Regra 6. Edição depois de baixado.** Mudar a natureza do título **depois** de haver baixa **não** muda as classificações já criadas; só o contador corrige a classificação, com motivo (documento 100, regra de correção).
- **Regra 7. Valor líquido.** O que vai para o Y520 continua sendo o **líquido pago** à empresa do exterior, depois do imposto retido na remessa (você decidiu em 22/10/2026). O título entra pelo valor contratado; as retenções continuam sendo registradas **na baixa** (`Mov_Titulo_Retencao`), como hoje.
- **Regra 8. Título automático (Q103-2 e Q103-2a).** Título que nasce de nota, pedido, comissão ou empréstimo com participante não residente **também exige a natureza**. Como o título não tem tela própria nesses casos, a **tela de origem** (a nota, o pedido, o empréstimo) pede a natureza antes de gerar o título, já com a sugestão preenchida; a pessoa só confirma. Sem natureza, a origem não gera o título. Você respondeu "sim para moeda estrangeira" (Q103-2a): vale para **qualquer origem**; **quando** a regra dispara foi decidido na Q103-10: participante não residente, em qualquer moeda.
- **Regra 9. Título que já existe.** Se o cadastro do participante **passa a não residente** depois de haver títulos em aberto dele, esses títulos **não são bloqueados**: entram numa lista de **pendências** até a natureza ser informada, e a baixa só é confirmada com ela.
- **Regra 10. Baixa e forma (Q103-8).** Com a natureza sempre presente, a classificação da baixa só falta a **forma**. A forma é **obrigatória**: o financeiro a **confirma na hora do pagamento** (partindo da forma prevista, se houver) e, sem ela, a baixa **não é confirmada**. As formas 4 e 5 respeitam o sentido (4 só no recebimento, 5 só no pagamento, documento 100). Confirmada a baixa, a classificação nasce **`classificada`**; o contador corrige depois, quando necessário.

# 6. Decisões afetadas

- **Documento 100 (versão 6, já ajustado):** a regra 1 (a classificação nasce na baixa) continua, mas **preenchida a partir do título**; a regra 4 (sugestão) passa a agir na entrada; a regra 10 deixa de dizer "nada bloqueia" para a natureza.
- **Documento 102 (versão 6, já ajustado):** a faixa de valor saiu; o mapa tem 10 campos e o parâmetro do limite foi retirado.
- **Documento 101, Q101-5:** a moeda já é informada por quem lança o título; agora a natureza também é.
- **Nenhum campo existente perde nada** e nenhum domínio muda. Nada na revisão 20 até você mandar "consolidar".

# 7. Não proponho

- Criar origem de título própria para royalty do exterior (`Origem_Tipo` novo): **não é preciso** (Q103-3).
- Pedir a forma de pagamento como **obrigatória** na entrada: ninguém sabe ainda como vai pagar.
- Criar contrato de royalty com cronograma e geração automática de títulos: é outro desenho (gestão de contratos) e você não pediu.
- Calcular o imposto retido do royalty (IRRF, CIDE, PIS e Cofins na importação, ISS): é do contador e já tem lugar na baixa.

# 8. Perguntas

**Respondidas por você (22/10/2026):** Q103-10 (a classificação é obrigatória para pagamento ou recebimento com **empresa ou pessoa não residente, inclusive em reais**), Q103-2a e Q103-9 ("sim para moeda estrangeira": a natureza obrigatória vale para qualquer origem do título e para o adiantamento; o gatilho exato ficou na Q103-10), Q103-8 (a forma de pagamento é obrigatória na baixa e confirmada no momento do pagamento; li também como resposta à Q103-4: a forma pode ser prevista na entrada, mas a que vale é a confirmada na baixa), Q103-1 (o título entra com moeda, valor na moeda e natureza, e a baixa herda), Q103-2 (natureza **obrigatória**) e Q103-3 (royalty sem nota entra como `avulso`; com nota, pela nota; sem origem nova), Q103-5 (a faixa é comparada na moeda do parâmetro, sem prender o título ao dólar) e Q103-7 (os 3 campos entram na próxima consolidação). Sobre a Q103-4, você disse que a **data de vencimento é sempre obrigatória** na entrada e na reprogramação; isso o dicionário já faz (`Data_Vencimento` de `Mov_Titulo`), e a pergunta da **forma prevista** segue aberta.

**Sem efeito (22/10/2026):** Q103-5 e Q103-5a, sobre faixa e conversão de moeda, porque você tirou a faixa. O documento 104 ficou como registro.

**Ainda abertas (1)**

| Nº | Pergunta | Minha recomendação |
|-----|----------------------------------------------------|----------------------------------|
| **Q103-6** | O contador indica qual **natureza** vale para royalties, resumido e detalhado, e quais para cada tipo (marca, patente, programa, direito autoral)? | Perguntar ao contador; entra no mapa do documento 102 |

# 9. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| `Mov_Titulo`: `ID_Natureza_Operacao_Cambial`, `Forma_Pagamento_Exterior_Prevista`, `Referencia_Operacao` | 0 | 3 |
| **Total do documento 103** | **0** | **3** |

Sobre a revisão 20 (915 entidades e 9.878 campos): os documentos 100, 101 e 102 com os opcionais somam **920 entidades e 9.962 campos**; com este documento, **920 e 9.965**. Se o `Codigo_Referencia` do documento 99 também for aprovado, some 1 campo.

# 10. Limites do que eu li

- **Não sei qual das suas frases se refere a "esse valor"**; li como "o valor na moeda do título" (documento 101). A Q103-1 confirma.
- Que o royalty do exterior sem nota entra como `avulso` é **decisão sua** (Q103-3). Não vi um fluxo de royalty do exterior nos documentos.
- Os códigos de natureza citados vêm do arquivo do programa da ECF (versão 9); **não validei** com o contador qual deles se aplica a cada tipo de royalty.
