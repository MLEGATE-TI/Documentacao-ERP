# Respostas de 27/10/2026 e o que Entra na Revisão 25 — Documento 123

*Registro das suas respostas de 27/10/2026 às perguntas Q113-4, Q113-5, Q113-8, Q113-9, Q113-11, Q101-3b, Q101-5, Q101-6, Q101-10a a Q101-10c, Q102-5 e Q102-6, das leituras que fiz de cada uma e do que entra no dicionário **quando você mandar consolidar** (revisão 25). **Nada foi aplicado ao dicionário, ao DDL nem à carga:** o dicionário continua na revisão 24 (925 entidades, 10.033 campos). Onde a resposta foi ambígua ou contrariou a minha recomendação, está dito abaixo, com a leitura que adotei; se alguma estiver errada, diga.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Suas respostas e como as li

| Item | Sua resposta | Leitura que adotei |
|---|---|---|
| Q113-4 | "Sim correto" | Para o **título em reais de não residente**, o valor bruto do Y520 é o **total da baixa** (valor baixado menos desconto mais juros e multa), já que `Valor_Pago_Reais` só existe em moeda estrangeira. Era a pergunta que faltava; o caso do título em moeda já estava no dicionário |
| Q113-5 | "Sim" | Aprovada a entidade nova `Cad_Tipo_Baixa_Forma` com os **7 campos** do documento 38 (janela com vigência, única para o grupo), com `Forma_Origem` como referência a `Cad_Classe_Sistema` (domínio aberto `forma_origem_baixa`), como propus, e não a alternativa de um campo dentro de `Cad_Tipo_Baixa` |
| Q113-8 | "Sim" | Aprovados os **2 campos novos** em `Mov_Titulo_Encontro_Contas`: `ID_Participante_Encontro` (quem lançou) e `ID_Participante_Diferenca` (quem recebe ou deposita a diferença) |
| Q113-9 | "Sim pode" | **Leitura com ambiguidade.** A pergunta tinha duas partes (qual regra para participantes diferentes, e se o participante da diferença pode ser um terceiro). Li "sim pode" como **leitura A** (encontro entre **qualquer** par de participantes, com o participante da diferença obrigatório quando há dinheiro) **e** como sim ao terceiro (qualquer participante cadastrado). Se você queria a leitura B (só o mesmo grupo econômico), diga. O jurídico e o contador seguem confirmando a base legal (documento 38, seção 2.2) |
| Q113-11 | "Sim" | Aprovada a entidade `Mov_Processo_Inconsistencia` com os **13 campos** do documento 38 (domínio aberto `processo_automatico`) |
| Q101-3b | "Não pode ser em moedas diferentes, porém tem que colocar a cotação de equivalência entre elas" | **Ambígua.** Perguntei, e você escolheu: **moedas diferentes são aceitas, e o usuário informa a cotação de equivalência entre as duas**. Isso **contraria** a regra do documento 101 (seção 4.3: crédito e título na mesma moeda). Os campos da cotação e da moeda de paridade foram definidos na Q123-1 (seção 5) |
| Q101-5 | "Sim" | A moeda do título é informada por quem lança, em qualquer origem, sem mexer em pedido, parcela, empréstimo e nota (já no dicionário; confirmada) |
| Q101-6 | "Sim, grifado ou em outra cor indicando que é estimado" | O valor em aberto do título em moeda aparece em reais estimados nos relatórios e no fluxo de caixa, **destacado** (grifado ou em outra cor) como estimativa. É regra de tela e de relatório, **sem campo novo** |
| Q101-10a | "Sim" | Aprovada a entidade `Mov_Credito_Reavaliacao` com os **15 campos** do documento 120 (e não a generalização de `Mov_Titulo_Reavaliacao`) |
| Q101-10b | "Se está em outra moeda é sempre calculada a variação cambial e reavaliado" | **Contraria a minha recomendação** (só o adiantamento financeiro). Li como: **todo crédito em moeda estrangeira**, financeiro ou não (bonificação, cashback, crédito tributário), é reavaliado todo mês e tem variação cambial calculada. O documento 120 limitava o campo `ID_Credito` ao adiantamento financeiro; isso muda. Consequências na seção 3 (Q123-2) |
| Q101-10c | "Sim, última variação cambial" | Na aplicação contra o título, o valor efetivo do crédito é o **valor contabilizado** dele, que é o da **última reavaliação**; a diferença entre esse valor e o do título é a variação realizada na aplicação. Li "última variação cambial" como "o saldo depois da última reavaliação mensal" |
| Q102-5 | "Sim" | As 3 linhas de partida do mapa de sugestão seguem como proposta para o contador validar (é carga, não dicionário; o mapa só ganha linhas depois da validação) |
| Q102-6 | "Depende: se existem informações passadas que dão para sugerir, sugere; a sugestão tem que vir sempre da base de conhecimento que o sistema vai gerando" | **Muda a regra 5 do documento 102** ("nota com itens de naturezas diferentes não sugere nada"): a nota com itens de naturezas diferentes **pode sugerir**, item a item, quando houver histórico; sem histórico, não sugere. Toda sugestão vem da base que o sistema forma com o uso. A base é o histórico das classificações confirmadas (Q123-3, seção 5) |

# 2. O que entra na revisão 25 se você mandar consolidar

| Onde | O que entra | Resposta |
|---|---|---|
| `Cad_Tipo_Baixa_Forma` (**entidade nova**, 7 campos) | De-para entre a forma de pagamento ou recebimento e o tipo da baixa, por sentido, com vigência; domínio novo `forma_origem_baixa` em `Cad_Classe_Sistema`; carga de partida (um tipo por forma, o de-para correspondente) | Q113-5 |
| `Mov_Titulo_Encontro_Contas` (**2 campos novos**) | `ID_Participante_Encontro` e `ID_Participante_Diferenca`; texto: participantes diferentes passam a ser aceitos (leitura A) | Q113-8 e Q113-9 |
| `Mov_Processo_Inconsistencia` (**entidade nova**, 13 campos) | Área de inconsistências, transversal; domínio novo `processo_automatico` | Q113-11 |
| `Mov_Credito_Reavaliacao` (**entidade nova**, 15 campos) | Reavaliação mensal do crédito em moeda; o escopo (todo crédito em moeda) depende da Q123-2 | Q101-10a e 10b |
| `Mov_Credito_Aplicacao.Valor_Aplicado` e texto de `Mov_Credito.ID_Moeda_Credito` | Na aplicação, vale o valor contabilizado do crédito; a variação realizada é a diferença | Q101-10c |
| Texto de `Mov_Titulo_Baixa.Valor_Pago_Reais` e do bloco do Y520 | Título em reais de não residente: valor bruto do Y520 = total da baixa | Q113-4 |
| Regra 5 do documento 102 | Passa a sugerir por item quando há histórico, a partir da base de conhecimento (depende da Q123-3) | Q102-6 |
| Carga do mapa de sugestão | 3 linhas de partida como proposta, `provisorio` até o contador validar | Q102-5 |

**Contagem se tudo entrar (sobre a revisão 24, atualizada com a seção 5):** 928 entidades (+3: `Cad_Tipo_Baixa_Forma`, `Mov_Processo_Inconsistencia` e `Mov_Credito_Reavaliacao`) e 10.074 campos (+41: 7, 13, 15, 2 e os 4 da paridade). As chaves estrangeiras e os domínios eu conto na consolidação.

**O que não entra:** nada do que você respondeu fica de fora; a Q123-1 a Q123-3 foram respondidas no mesmo dia (seção 5).

# 3. Novas perguntas (respondidas em 27/10/2026: ver seção 5)

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q123-1** | **Cotação de equivalência (Q101-3b).** Como os dois itens estão em moedas diferentes, a aplicação do crédito e o encontro de contas precisam guardar a cotação que o usuário informa. Proposta: um campo `Cotacao_Equivalencia` (número, opcional, 8 casas, obrigatório quando a moeda do crédito difere da do título) em `Mov_Credito_Aplicacao`, e o mesmo em `Mov_Titulo_Encontro_Contas`, com a unidade dita no texto (quantas unidades da moeda do título por unidade da moeda do crédito). No encontro, em que moeda fica o `Valor_Encontro` (a do título a pagar, a do a receber ou reais)? Aprova os dois campos, e em que moeda fica o valor do encontro? | Os dois campos; o valor do encontro na moeda do título a pagar, a confirmar com o contador |
| **Q123-2** | **Crédito não financeiro em moeda (Q101-10b).** Pelo documento 101, só o adiantamento financeiro tem `Taxa_Cambio`, obrigatória. Se todo crédito em moeda é reavaliado, o crédito não financeiro em moeda precisa de uma taxa de partida. A `Taxa_Cambio` de `Mov_Credito` passa a ser obrigatória para **todo** crédito em moeda estrangeira? | Sim. O contador confirma o tratamento contábil: pelo que conheço do CPC 02, item não monetário em regra não é reavaliado (leitura minha, não conferida na norma) |
| **Q123-3** | **Base de conhecimento (Q102-6).** A base de conhecimento é o **histórico das classificações já confirmadas** (a natureza que o financeiro confirmou por participante, CFOP e NBS do item), lido pelo sistema para sugerir, **sem entidade nova**? Ou você pensa numa base própria, com campos (por exemplo, contagem de vezes e data da última confirmação)? | Histórico das classificações confirmadas, sem entidade nova: o que o sistema aprende é a natureza mais usada para o mesmo participante e o mesmo CFOP ou NBS |

# 4. Pontos de atenção

- **Q113-9 (leitura A).** O Código Civil, pelo que lembro, pressupõe credor e devedor um do outro para a compensação legal (artigo 368, **não conferido aqui**); entre partes diferentes costuma pedir acordo ou cessão de crédito. O ERP aceita o que você decidiu; a base legal e o tratamento fiscal e contábil são do jurídico e do contador.
- **Q101-10b (crédito não financeiro).** A minha recomendação era só o adiantamento financeiro, porque o crédito não financeiro não tem dinheiro enviado. Segui a sua decisão. A reavaliação cambial de item não monetário é ponto do contador.
- **Q101-3b contraria o documento 101.** A regra de "mesma moeda" saiu; o documento 101 (seção 4.3) e o texto de `Mov_Credito_Aplicacao.Valor_Aplicado` e de `Mov_Titulo_Encontro_Contas.Valor_Encontro` serão ajustados na revisão 25, depois da Q123-1.
- **Q102-6 e as regras do documento 100.** A sugestão continua só **sugerindo**: nunca grava sozinha e nunca bloqueia (regra 10 do documento 100); a natureza só vira classificada quando o financeiro confirma.

# 5. Respostas às Q123-1 a Q123-3 (27/10/2026)

| Item | Sua resposta | Leitura que adotei |
|---|---|---|
| Q123-1 | "Vai ter que definir uma moeda de paridade na hora de colocar o valor de equivalência entre elas; com isto vai ser na moeda selecionada base de paridade" | Na aplicação do crédito e no encontro de contas entre moedas diferentes, o usuário **escolhe a moeda de paridade e informa a cotação de equivalência**, e o valor da aplicação ou do encontro fica **na moeda de paridade**. Como a resposta não dizia se a paridade é uma das duas moedas ou qualquer moeda, perguntei, e você escolheu: **uma das duas moedas dos itens**. Com isso, entram **2 campos em cada uma das duas entidades** (`Mov_Credito_Aplicacao` e `Mov_Titulo_Encontro_Contas`): `ID_Moeda_Paridade` (referência a `Cad_Moeda`, opcional, obrigatório quando as moedas dos itens diferem, só uma das duas moedas) e `Cotacao_Equivalencia` (número, 8 casas, opcional, obrigatório nas mesmas condições). A cotação é **quantas unidades da outra moeda valem uma unidade da moeda de paridade**, e você confirmou em 27/10/2026 com o exemplo do dólar (ver abaixo); o sentido vai no texto do campo. O `Valor_Aplicado` e o `Valor_Encontro` passam a ser **na moeda de paridade**. O seu "sim" à escolha vale como aprovação dos 4 campos (você confirmou a minha leitura em 27/10/2026) |
| Q123-2 | "Sim" | A `Taxa_Cambio` de `Mov_Credito` passa a ser obrigatória para **todo** crédito em moeda estrangeira, financeiro ou não (hoje só no adiantamento financeiro). O contador confirma o tratamento de item não monetário |
| Q123-3 | "Sim" | A base de conhecimento do mapa de sugestão é o **histórico das classificações já confirmadas** (natureza por participante, CFOP e NBS do item), **sem entidade nova**; o que o sistema aprende é a natureza mais usada para o mesmo participante e o mesmo CFOP ou NBS |

**Confirmação do sentido da cotação (27/10/2026).** Você respondeu "sim" às duas leituras e deu o exemplo: com o dólar a R$ 5,00, são necessários 5 reais para comprar 1 dólar, e 0,2 dólar para comprar R$ 1,00. Isso vale para as duas escolhas de paridade, e o texto de `Cotacao_Equivalencia` dirá: **se a paridade é o dólar, a cotação é 5,00 (reais por dólar); se a paridade é o real, a cotação é 0,2 (dólares por real)**. A cotação é sempre a quantidade da outra moeda por 1 unidade da moeda de paridade, e quem a informa é o usuário.

**O que isso muda na lista da seção 2:** entram também os 4 campos da paridade (2 em `Mov_Credito_Aplicacao` e 2 em `Mov_Titulo_Encontro_Contas`), o texto de `Valor_Aplicado` e de `Valor_Encontro` (na moeda de paridade), a obrigatoriedade da `Taxa_Cambio` do crédito em moeda e a regra 5 do documento 102 reescrita sobre o histórico das classificações. **Fica para o contador:** como a variação cambial realizada de cada título se apura quando o valor do encontro está na moeda de paridade, que pode ser a de um só dos dois títulos (o documento 114 só trata do encontro em reais ou na moeda dos dois títulos).

# 6. Também entra na revisão 25: a remessa internacional (documentos 107 e 124)

Em 27/10/2026 você aprovou ("sim aprovo") as Q107-1 a Q107-6 e os sete pontos do documento 124. Se você mandar consolidar, entram **+1 entidade** (`Mov_Remessa_Bancaria_Item_Exterior`, 16 campos), **3 campos** em `Cad_Participante_Dados_Bancarios` (banco intermediário), **3 campos** em `Mov_Retorno_Bancario_Item` (contrato, taxa e valor do câmbio em reais) e o valor `transferencia_internacional` em `Forma_Lancamento`, mais os textos de `Valor_Principal_Remessa`, `Codigo_Banco_Favorecido`, `Valor_Total_Ocorrencia`, `Valor_Reais_Ocorrencia` e `Valor_Arredondamento_Com_Sinal`. **Contagem da revisão 25 com tudo o que espera: 929 entidades e 10.096 campos** (928 e 10.074 da seção 2, mais 1 e 22).

# 7. Também entra na revisão 25: o presumido (documentos 99 e 125)

Em 27/10/2026 você respondeu **sim** às Q99-2, Q99-3, Q99-4, Q99-5 e Q99-6 e **não** à Q99-1 (P130 e P230 entram agora). Se você mandar consolidar: **+1 campo** (`Codigo_Referencia` em `Cad_Ecf_Tabela_Dinamica_Linha`, Q99-5) e as regras e textos da apuração do presumido. **Contagem da revisão 25 com tudo o que espera: 929 entidades e 10.097 campos.** A entidade de mapeamento de contas às linhas (`Cad_Ecf_Linha_Mapeamento`, 10 campos) **só entra se você aprovar a Q125-1**; com ela seriam **930 entidades e 10.107 campos**.
