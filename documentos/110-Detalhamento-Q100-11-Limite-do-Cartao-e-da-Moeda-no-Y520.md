# Detalhamento da Q100-11: Limite de R\$ 120.000 do Cartão e da Moeda no Y520 — Documento 110

> **Consolidado na revisão 22 (26/10/2026, documento 113).** A sua decisão de 26/10/2026 ("vai, com a forma real": todo pagamento ou recebimento com não residente vai ao Y520, de qualquer valor, e o limite de R\$ 120.000 é só conferência no ERP) entrou no dicionário: **saiu o valor `abaixo_do_limite`** de `Mov_Ecf_Y520_Linha.Situacao`, e os dois campos opcionais que este documento propunha (`Total_Forma_Tipo` e `Limite_Aplicado`) **não entraram**. O parâmetro `limite_cartao_exterior_anual` continua, para a conferência. Ficam com o contador a Q110-11 (informar mais que o manual exige) e a conferência do valor. As contagens abaixo ("revisão 21") são as de quando o documento foi escrito.

*Você pediu para detalhar a Q100-11 do documento 100: o limite de R\$ 120.000 vale para cartão e moeda, abaixo dele não se informa, a partir dele informa-se a forma com o detalhe? Reli o manual da ECF (leiaute 12, edição de 23/07/2026) e o desenho do documento 100. **Achei três pontos que a regra 7 do documento 100 não resolve** (seção 3), um deles com efeito direto no indicador do registro 0020. É uma proposta de desenho: **nada foi alterado no dicionário** (revisão 21: 920 entidades, 9.973 campos). Só entra depois das suas respostas e do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026 · Versão 9 (26/10/2026)

# 0. Sua resposta de 23/10/2026 e o que ela muda (versões 2 a 8)

*Você respondeu à Q100-11 em duas mensagens. Registro abaixo o que entendi, o que o manual da ECF diz sobre isso (reli o registro Y520 na edição de 23/07/2026, leiaute 12) e **uma divergência entre a sua regra e o leiaute** que precisa da sua decisão. **Nada foi alterado no dicionário** (revisão 21 segue: 920 entidades, 9.973 campos).*

**O que você disse**

1. "Sempre guardar o tipo de pagamento": **em todo pagamento ou recebimento se guarda a modalidade** (a forma do Y520).
2. "Não precisa limitar no mês a mês": o teste não é mensal.
3. No **final do ano**, se a **soma superar R\$ 120.000, por destinatário e país**, os registros saem **detalhados por modalidade** (a modalidade entra na chave); **se não superar, a modalidade fica em branco**.

**O que fica entendido (vale para a próxima consolidação)**

| Ponto | Leitura |
|---|---|
| Guardar a modalidade em toda baixa | **Já é assim.** A forma é obrigatória na baixa de título de não residente (regra 10 do documento 100, Q103-8) e nasce na classificação. Sem campo novo. |
| Teste mês a mês | **Descartado.** A leitura C da seção 3.3 sai. |
| Período do teste | **Anual e fixo**, sobre a soma do ano (leitura A da seção 3.3). **Respondido em 23/10/2026 (Q110-2a):** não se proporcionaliza; só importa na geração do bloco. A leitura B (proporcional aos meses) e o exemplo 3 das seções 3.3, 4 e 8 ficam superados. |
| Em que nível se soma | **Por destinatário (participante) e país**, no ano. Isso **substitui** a proposta da Q110-1 (por forma e tipo, somando todos os países e naturezas). Entendi que recebido e pago continuam separados, mas você não disse isso; confirmo na Q110-10. |

**O que o manual diz e não bate com a regra "modalidade em branco"** (registro Y520, edição de 23/07/2026)

- **A forma é campo obrigatório**, com valores válidos de 1 a 6. **Em branco o programa da ECF não aceita**; o campo `FORMA` é obrigatório ("Sim") e a chave do registro é `TIP_EXT + PAIS + FORMA + NAT_OPER`.
- **Não existe destinatário no Y520.** O texto manda informar "os valores consolidados por país, conforme registrado na apuração contábil". Somar por destinatário e país é, então, um critério do ERP; o arquivo continua por país, forma e natureza.
- **O limite de R\$ 120.000, no texto do manual, decide se o cartão e a moeda são informados**, não se a modalidade é detalhada. Câmbio, transferência em reais e depósito ou recursos no exterior entram **sem limite e sempre com a forma** (seção 2 deste documento).

Ou seja: o que você descreve funciona **dentro do ERP** (a modalidade guardada em cada baixa, e o contador vendo o total consolidado por destinatário e país e se passou de R\$ 120.000). **Para o arquivo**, com a forma obrigatória, uma linha "sem modalidade" não tem onde ir. Não sei se a Receita aceita outra leitura; **não consegui ver isso no manual**.

**Duas formas de fechar (preciso da sua escolha)**

| Opção | Como fica | Efeito no dicionário |
|---|---|---|
| **A. Regra do ERP só para conferência (recomendada)** | O ERP guarda a modalidade em toda baixa e mostra ao contador, por destinatário e país, a soma do ano e se passou de R\$ 120.000. **O arquivo segue o manual**: a forma sempre preenchida; cartão e moeda só vão ao Y520 quando o limite é atingido. Nenhuma linha sai com forma em branco. | Nenhum campo novo além dos dois opcionais da seção 5, que passariam a guardar o total **por destinatário e país**. |
| **B. Forma em branco no arquivo** | Abaixo do limite, a linha do Y520 sairia sem forma. **O programa da ECF recusaria** (campo obrigatório). Só faria sentido se a Receita ou o contador confirmassem outra forma de informar. | Forma da linha passaria a ser opcional e a chave do consolidado teria de aceitar vazio. **Não recomendo** sem a confirmação. |

**Perguntas novas desta versão**

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q110-9** | Opção **A** (regra do ERP só de conferência; arquivo segue o manual, forma sempre preenchida) ou **B** (forma em branco no arquivo)? | A |
| **Q110-10** | O teste de R\$ 120.000 é feito **por destinatário e país**, **recebido e pago separados**? Ou, como o texto do manual sugere, **por país** (todos os destinatários) e por forma? **Para o contador** confirmar. | **Respondida em 23/10/2026: usar a recomendação.** Seguir o que você disse (destinatário e país) no ERP; o contador confirma o que vale para o arquivo |
| **Q110-2a** | **Para o contador:** em ECF de menos de 12 meses, o limite de R\$ 120.000 vale fixo ou proporcional aos meses? | **Respondida em 23/10/2026: não proporcionalizar**; vale a soma do ano, e o teste só se faz na geração do bloco. |

**Sua escolha na Q110-9 (23/10/2026): opção A.** A regra do limite por destinatário e país é **só conferência dentro do ERP**: o ERP guarda a modalidade em toda baixa e mostra ao contador, por destinatário e país, a soma do ano e se passou de R\$ 120.000. **O arquivo segue o manual**: a forma sempre preenchida (1 a 6) e cartão e moeda só no Y520 quando o limite é atingido. **Nenhuma linha sai com forma em branco**, e a forma do consolidado continua obrigatória e parte da chave. Sem campo novo além dos dois opcionais da seção 5 (Q110-6, ainda aberta), que passariam a guardar o total por destinatário e país. **Nada foi alterado no dicionário**; entra na consolidação que você pedir.

**Situação das perguntas do documento (seção 8) depois da sua resposta:** **Q110-1** substituída pela Q110-10; **Q110-2** respondida (anual, sem teste mensal), com o detalhe na Q110-2a; **Q110-9** respondida (opção A); **Q110-10** respondida em 23/10/2026 ("usar a recomendação": no ERP o teste é por destinatário e país, recebido e pago separados; ao contador resta confirmar o que vale para o arquivo); **Q110-2a** respondida em 23/10/2026 (limite fixo, soma do ano, teste só na geração do bloco; fica sem efeito o aviso a 80% durante o ano proposto na seção 4); **Q110-3** respondida em 23/10/2026 (passou do limite, vai o total, com todos os itens); **Q110-4 a Q110-8** seguem **abertas**. Cuidado com a **Q110-7** (texto para a Receita): se você aprovar, a pergunta 9 do documento 98 precisa incluir também (e) se a forma pode ficar em branco e (f) se o limite é por destinatário. O envio continua sendo seu.

---

## 0.2 Decisão de 26/10/2026: todo pagamento ao exterior vai ao Y520, com a forma real (substitui a opção A e as seções 0 e 0.1 onde disserem o contrário)

*Você disse: "no bloco Y520 tem que ir todo o pagamento para o exterior ou recebimento, independente do valor; se tiver pagamento tem que ir; o limite de R\$ 120.000 é para indicar o tipo de pagamento". Perguntei como ficava o cartão de R\$ 40.000 abaixo do limite e você escolheu: **vai, com a forma real**. Nada foi alterado no dicionário.*

**O que fica decidido**
- **Todo pagamento ou recebimento com não residente vai ao Y520**, de qualquer valor, **com a forma que foi guardada na baixa** (cartão = 3, moeda = 6, câmbio = 1 e assim por diante). Não há linha sem forma e não há linha "abaixo do limite" fora do arquivo.
- **O limite de R\$ 120.000 deixa de mudar o que vai ao arquivo.** Continua como **conferência no ERP** (soma do ano por destinatário e país, recebido e pago separados, testada só na geração do bloco; Q110-2a e Q110-10), para o contador ver quem passou do valor do manual.
- **O indicador do 0020** (Q110-4) passa a valer "S" quando **há linha no Y520** do tipo; ou seja, a regra 11 do documento 100 de hoje (existe classificação no ano) **fica como está**, e a correção proposta na seção 0.1 **cai**. O contador continua revisando (Q100-15).

**O que isso muda nas perguntas**

| Pergunta | Situação |
|---|---|
| Q110-3 (total ou excedente) | Já respondida; sem efeito prático, porque todas as linhas vão ao arquivo |
| Q110-4 (indicador só com linhas acima do limite) | **Respondida pela decisão acima**: o indicador acompanha o Y520, que leva tudo |
| Q110-5 (parâmetro próprio da moeda; a moeda liga o indicador) | **Sem efeito**: sem corte no arquivo, não precisa de segundo parâmetro. O `limite_cartao_exterior_anual` (D-N310) fica só para a conferência |
| Q110-6 (guardar total testado e limite aplicado na linha) | **Sem efeito proposto**: a conferência é calculada na tela; os 2 campos opcionais saem da proposta (reentram se você quiser guardar o resultado) |
| Q110-7 (pergunta 9 para a Receita) | **Sem efeito**, a menos que você queira consultar assim mesmo |
| Q110-8 (valor comparado com o limite) | **Sem efeito** para o arquivo; na conferência vale o mesmo valor do Y520 |
| Q110-9 e Q110-10 | Substituídas por esta decisão (o limite é só conferência no ERP) |

**Um ponto para o contador (Q110-11).** O manual manda marcar o indicador por cartão **só a partir de R\$ 120.000** e manda informar no Y520 o cartão e a moeda **só a partir do limite**. Com a sua decisão, o ERP informa também abaixo do limite e, com a linha no arquivo, marca o indicador "S" (é o que o validador exige: linha de um tipo só existe com o indicador "S"). O validador aceita; o que o contador precisa confirmar é que **informar a mais que o manual exige** não traz problema para a empresa. Se ele disser que não convém, o corte do limite volta como parâmetro (a opção "não vai" que você não escolheu).

**Custo no dicionário.** 0 entidades e 0 campos novos. Na próxima consolidação: sai o valor `abaixo_do_limite` da enumeração `Mov_Ecf_Y520_Linha.Situacao` (hoje `{gerada, abaixo_do_limite, substituida}`) e o texto da regra 7 do documento 100 deixa de falar em corte; os 2 campos opcionais da seção 5 **não entram**.

---

## 0.1 Detalhamento da Q110-4: o indicador do 0020 conta só as linhas que vão ao arquivo?

*Você pediu para detalhar a Q110-4 (26/10/2026). Reli os campos 15 e 17 do registro 0020, o texto de abertura do Y520 e as regras de validação (manual do leiaute 12, edição de 23/07/2026). É proposta; **nada foi alterado no dicionário**.*

**O que a pergunta decide.** Como o ERP calcula `IND_REC_EXT` (campo 15) e `IND_PGTO_EXT` (campo 17). Você já respondeu (Q100-15) que **o sistema calcula e o contador revisa**; falta dizer **o que o cálculo conta**.

**O que o manual diz.**
- Câmbio, transferência internacional em reais, depósito em conta no exterior e recursos mantidos no exterior: **qualquer valor** liga o indicador, sem limite.
- Cartão de crédito: só valores iguais ou superiores a R\$ 120.000 (R\$ 10.000 por mês). Os campos 15 e 17 **não citam a moeda**; o texto de abertura do Y520 cita (Q110-5).
- O Y520 só é habilitado com o indicador "S", e duas regras do validador amarram os dois: com o indicador "S" tem de existir Y520 do tipo correspondente (`REGRA_Y520_OBRIGATORIO_R` e `_P`, **erro**), e o Y520 de um tipo só pode existir se o indicador correspondente for "S" (`REGRA_TIP_EXT_PERMITIDO`, **erro**).

**O problema.** Hoje a regra 11 do documento 100 diz que o indicador vale "S" quando existe **qualquer classificação** do tipo no ano. Com a sua decisão de que o arquivo segue o manual (opção A), o cartão abaixo do limite **não vai ao Y520**. Então:

| Situação no ano | Indicador pela regra de hoje | Y520 no arquivo | Resultado no validador |
|---|---|---|---|
| Só R$ 40.000 recebidos por cartão (abaixo do limite) | `IND_REC_EXT` = S | nenhuma linha | **Erro** (`REGRA_Y520_OBRIGATORIO_R`) |
| Só R$ 150.000 recebidos por cartão (acima do limite) | S | linhas de cartão | Ok |
| R$ 40.000 por cartão **e** um câmbio de R$ 5.000 | S | só a linha do câmbio | Ok (o câmbio não tem limite) |
| Nenhum valor do exterior | N | nenhuma | Ok |

**Proposta (o que eu recomendo).** O indicador calculado conta **só as linhas que realmente vão ao arquivo**: vale "S" quando existe, na geração do bloco, ao menos uma linha do tipo que passa para o Y520 (qualquer câmbio, transferência em reais, depósito ou recursos no exterior; cartão e moeda só se o limite foi atingido). Como o limite só é testado **na geração do bloco** (Q110-2a), o indicador também é calculado **nessa hora**, junto com o Y520, e nunca antes. Assim os dois nascem do mesmo cálculo e as duas regras do validador não discordam.

**Com isso, na prática.**
- O indicador e o Y520 saem sempre de acordo entre si, sem depender do contador lembrar de ajustar.
- O contador continua revisando (Q100-15): se ele mudar o indicador à mão e ficar diferente das linhas geradas, o ERP **avisa** (aviso, não bloqueio) que o validador da Receita vai acusar erro.
- O que não muda: os tipos R e P no mesmo arquivo (D-N315 e D-N324), a classificação guardada com a forma em toda baixa e a regra do limite por destinatário e país como conferência no ERP.

**Alternativa (não recomendo).** Manter a regra de hoje (conta toda classificação) e deixar o contador corrigir o indicador quando só houver cartão ou moeda abaixo do limite. Fica dependente de lembrar, e o erro `REGRA_Y520_OBRIGATORIO_R` ou `_P` aparece no validador quando ele esquece.

**O que esta pergunta herda das abertas:** o que vale como limite para o **arquivo** (por país ou por destinatário e país, Q110-10) e se a **moeda** liga o indicador (Q110-5). Mudando a resposta delas, o indicador acompanha, porque sai do mesmo cálculo.

**Custo no dicionário:** 0 entidades e 0 campos. Muda só o texto da regra 11 do documento 100 e a descrição de `Mov_Ecf_Y520_Linha.Situacao`, na próxima consolidação.

---

# 1. Resumo

- **O que o manual diz.** Câmbio, transferência internacional em reais e depósito ou recursos mantidos no exterior entram no Y520 **sem limite**. **Cartão de crédito** e **moeda** (nacional ou estrangeira, cheques, cheques de viagem) entram **só quando os valores forem iguais ou superiores a R\$ 120.000,00, equivalentes a R\$ 10.000,00 por mês**. A sua frase da Q100-11 ("é para não precisar detalhar; passando do valor tem que detalhar") confere com o texto.
- **O que o desenho de hoje faz.** Parâmetro `limite_cartao_exterior_anual` (R\$ 120.000, provisório, D-N310) e uma situação `abaixo_do_limite` na linha do Y520 consolidado. Mas não diz **o que se soma**, **em que período** nem **o que o limite faz com o indicador** do registro 0020.
- **Três pontos novos:**
  - **Indicador do 0020 (erro de validação).** Pela regra 11 do documento 100, `IND_REC_EXT` e `IND_PGTO_EXT` valem "sim" quando existe qualquer classificação do tipo no ano. Se o cliente só tiver cartão abaixo do limite, o indicador sairia "S", **não haveria linha no Y520**, e a regra `REGRA_Y520_OBRIGATORIO_R` (ou `_P`) do validador geraria **erro**. O indicador precisa contar só o que passa do limite.
  - **O texto do 0020 não cita a moeda.** Nos campos 15 e 17 do registro 0020 o limite aparece **só para cartão**; no texto de abertura do Y520 aparecem **cartão e moeda**. Se um cliente só tiver moeda acima do limite, o manual não deixa claro se o indicador vira "S" (e então o Y520 é habilitado).
  - **Anual ou mensal.** "R\$ 120.000, equivalentes a R\$ 10.000 por mês" pode ser lido como um total anual, como um total proporcional aos meses do período (ECF de período menor que o ano) ou como um teste mês a mês. O manual não diz.
- **Proposta:** limite **por forma e por tipo** (cartão e moeda, recebido e pago, cada um com o seu), somando **todos os países e naturezas**; teste **proporcional aos meses do período** (igual ao anual em ECF de 12 meses); atingido o limite, vai o **total** da forma; indicador conta só linhas acima do limite; **parâmetro próprio para a moeda**; e 2 campos opcionais na linha do Y520 para o contador ver o total testado e o limite usado. A norma de origem do limite eu **não achei**; por isso a leitura vai ao contador e, se você quiser, à Receita (pergunta 9 pronta na seção 8).

# 2. O que o manual diz

| Onde | O que diz (resumo) |
|---|---|
| Registro 0020, campo 15 (`IND_REC_EXT`) | "Sim" para quem **recebeu** de não residentes: valores por **câmbio**, por **transferência internacional em reais**, por **depósito em conta no exterior** (sem limite) e valores por **cartão de crédito** iguais ou superiores a R\$ 120.000, equivalentes a R\$ 10.000 por mês. **Não cita moeda.** |
| Registro 0020, campo 17 (`IND_PGTO_EXT`) | O mesmo para **pagamentos**: câmbio, transferência em reais, recursos mantidos no exterior (sem limite) e cartão com o mesmo limite. **Não cita moeda.** |
| Texto de abertura do Y520 | O registro é habilitado para quem tem os cinco casos, e a lista **inclui moeda**: valores em moeda nacional ou estrangeira, cheques ou cheques de viagem, **convertidos em reais na data de cada operação**, com o mesmo limite de R\$ 120.000, equivalentes a R\$ 10.000 por mês. |
| Y520, campo `VL_PERIODO` | Total recebido ou pago, por país, forma e natureza. O texto manda informar "valores consolidados por país, conforme registrado na apuração contábil". |
| Regras de validação | `REGRA_Y520_OBRIGATORIO_R`: com `IND_REC_EXT` = "S" tem de existir Y520 tipo R e não pode existir tipo P (e o inverso para `_P`). `REGRA_TIP_EXT_PERMITIDO`: o tipo só pode existir se o indicador correspondente for "S". |

*A regra `REGRA_Y520_OBRIGATORIO_R` e a `REGRA_Y520_OBRIGATORIO_P`, ao pé da letra, proíbem os dois tipos no mesmo arquivo. Isso já é o ponto aberto do documento 98 (D-N315 e D-N324 mantêm os dois tipos convivendo) e não muda aqui.*

# 3. O que o desenho de hoje não resolve

## 3.1 O indicador do 0020 precisa respeitar o limite

Regra 11 do documento 100: `IND_REC_EXT` calculado = existe classificação de tipo recebido no ano. Exemplo: o cliente só recebeu R\$ 40.000 de cartão de um cliente dos EUA. A linha do Y520 fica `abaixo_do_limite` e não vai ao arquivo; o indicador, porém, sairia "S", e o validador exigiria uma linha do tipo R. **Correção proposta:** o indicador calculado conta só as linhas do consolidado com situação `gerada` (acima do limite, ou de forma sem limite). O contador continua confirmando (Q100-15).

## 3.2 A moeda não aparece no texto do indicador

O limite da moeda só está no texto do Y520. Se o texto do 0020 for completo, um cliente com **só moeda** acima do limite não marcaria o indicador e o Y520 nem seria habilitado. Se o texto do Y520 for o correto, a moeda também liga o indicador. **Eu não decido**: proponho que o ERP **trate a moeda como o texto do Y520 manda** (limite próprio, e conta para o indicador) e deixe a dúvida na pergunta 9 para a Receita; o contador confirma.

## 3.3 O que é o "por mês"

Três leituras possíveis, com o mesmo parâmetro de R\$ 120.000 por ano:

| Leitura | Regra | ECF de 12 meses | ECF de 6 meses (exemplo: R\$ 70.000 de cartão) |
|---|---|---|---|
| A. Anual fixo | Total do período ≥ R\$ 120.000 | Informa se total ≥ 120.000 | Não informa (70.000 < 120.000) |
| B. Proporcional aos meses do período | Total ≥ R\$ 10.000 × meses do período | Igual à A | **Informa** (70.000 ≥ 60.000) |
| C. Mensal | Algum mês com total ≥ R\$ 10.000 | Informa se algum mês passar de 10.000, mesmo com total anual abaixo de 120.000 | Idem |

O texto "equivalentes a R\$ 10.000 por mês" sugere que o mensal é só a mesma medida em outra unidade, o que favorece **A ou B**. A diferença entre as duas só aparece na ECF de período menor que o ano (início ou encerramento de atividade, cisão, situação especial). A C é a mais exigente e a menos provável pelo texto, mas não está descartada.

# 4. Como a geração funcionaria (proposta)

- **Por tipo e forma.** Para cada tipo (recebido ou pago) e para cada forma com limite (cartão e moeda), o ERP soma o `Valor_Reais` das classificações `classificadas` do período da ECF, **líquido de estornos** (Q100-14 ainda aberta), **somando todos os países e todas as naturezas**. As formas 1, 2, 4 e 5 não têm teste.
- **Comparação.** Total da forma e do tipo ≥ limite do período (leitura B: valor anual × meses do período ÷ 12).
- **Resultado.** Se passa, **todas** as linhas daquele tipo e forma (por país e natureza) saem `gerada`, com o **total** de cada uma (não só o excedente). Se não passa, todas saem `abaixo_do_limite` e **não vão ao arquivo**, nem entram no cálculo do indicador.
- **Indicador do 0020.** `IND_REC_EXT` calculado = existe linha `gerada` de tipo R; `IND_PGTO_EXT` = idem para P.
- **Parâmetro.** Hoje o domínio `parametro_ecf` tem `limite_cartao_exterior_anual`. Proponho **um valor novo**, `limite_moeda_exterior_anual`, com a mesma carga de partida (R\$ 120.000, vigência 01/01/2026, provisório), porque o texto lista os dois separadamente e a Receita pode mudar um sem mudar o outro. É 1 valor de domínio, sem campo novo.
- **Para o contador ver.** Na tela do Y520 o ERP mostra, por tipo e forma, o **total do período**, o **limite aplicado** e se passou. Proponho guardar os dois números na linha (seção 5), para a conferência não depender de recalcular.
- **Durante o ano.** A tela de classificação avisa quando o total acumulado do cartão ou da moeda chegar a 80% do limite do período (aviso, não bloqueia; o percentual é parâmetro).

**Exemplo 1 (12 meses).** Recebido por cartão: R\$ 90.000 dos EUA e R\$ 40.000 do Canadá. Total R\$ 130.000 ≥ R\$ 120.000: as duas linhas saem (EUA 90.000 e Canadá 40.000) e `IND_REC_EXT` = "S".

**Exemplo 2 (12 meses).** Recebido em moeda: R\$ 50.000, sem outra forma. Abaixo do limite: nenhuma linha vai ao arquivo e `IND_REC_EXT` = "N" (se não houver câmbio, transferência ou depósito).

**Exemplo 3 (ECF de 6 meses).** Cartão pago: R\$ 70.000. Leitura A: abaixo, não informa. Leitura B: o limite é R\$ 60.000, informa. A pergunta Q110-2 decide.

# 5. Campos propostos

*Opcionais (Q110-6). O tipo e a forma da linha já existem em `Mov_Ecf_Y520_Linha`.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **Total_Forma_Tipo** | *número, opcional* | O total do período, em reais, da forma e do tipo da linha (somando países e naturezas), no momento da geração. Preenchido só nas formas com limite (cartão e moeda); vazio nas outras. Cada linha da mesma forma e tipo repete o mesmo total. |
| **Limite_Aplicado** | *número, opcional* | O limite em reais usado no teste, já proporcional aos meses do período (valor do parâmetro no período). Vazio nas formas sem limite. Quando o parâmetro mudar de valor, a linha guarda o que valia na geração. |

Contagem: **0 entidades, 2 campos** e **1 valor novo** em `parametro_ecf`. Mudam, só no texto, a regra 7 e a regra 11 do documento 100 e a descrição de `Mov_Ecf_Y520_Linha.Situacao`.

# 6. O que isto muda nas decisões anteriores

| Decisão | Efeito |
|---|---|
| **D-N310** (limite do cartão como parâmetro) | Continua; o parâmetro passa a ter um irmão para a moeda |
| **D-N323** (valores vigentes desde 01/01/2026) | O novo parâmetro nasce com a mesma vigência e também provisório |
| **Regra 7 do documento 100** | Reescrita: limite por tipo e forma, proporcional aos meses, total (não excedente), moeda com parâmetro próprio |
| **Regra 11 do documento 100** | Reescrita: o indicador conta só linhas `gerada` |
| **Q100-15** (indicador calculado e confirmado pelo contador) | Continua; muda só o cálculo |
| **D-N315, D-N324** (os dois tipos convivem) | Valem como estão |

# 7. O que não proponho

- **Bloquear** o pagamento ou a baixa por causa do limite: é aviso, a decisão de informar é do ERP na geração e do contador na revisão.
- **Tratar cada país separadamente** no teste: o texto fala em valores por cartão e em moeda, não por país.
- **Somar recebido e pago** num limite só: o manual traz o limite em cada indicador, o do recebimento e o do pagamento.
- **Decidir o fundamento legal** do limite. Procurei na internet a origem da expressão "equivalentes a R\$ 10.000,00 por mês" (páginas de documentação de ECF e manuais antigos da DIPJ) e **não achei** a norma nem uma explicação de como somar; fico só com o manual da ECF.

# 8. Perguntas

| Nº | Pergunta | Minha recomendação |
|--------|---------------------------------------------------|-----------------------------------------|
| **Q110-1** | O limite vale **por forma** (cartão e moeda, cada um com o seu) e **por tipo** (recebido e pago separados), somando todos os países e naturezas? | Sim |
| **Q110-2** | O teste é **proporcional aos meses do período** da ECF (leitura B, igual ao anual em 12 meses)? Ou **anual fixo** (A), ou **mês a mês** (C)? | B; o contador confirma |
| **Q110-3** | Atingido o limite, vai o **total** da forma (e não só o que passou do limite)? | **Respondida em 23/10/2026: sim.** Passou do limite, detalham-se todos os itens da forma, não só o que passou. |
| **Q110-4** | O indicador do 0020 calculado conta **só linhas acima do limite** (corrige a regra 11 do documento 100)? | Sim |
| **Q110-5** | Criar o parâmetro **`limite_moeda_exterior_anual`**, separado do do cartão, com a mesma carga de partida (R\$ 120.000, provisório)? A moeda **liga o indicador** quando passa do limite (texto do Y520)? | Sim, para as duas |
| **Q110-6** | Guardar na linha do Y520 o **total testado** e o **limite aplicado** (2 campos opcionais, seção 5)? | Sim |
| **Q110-7** | Acrescentar ao documento 98 a **pergunta 9** (texto abaixo) para a Receita? **O envio é seu**: nada foi enviado. | Sim, baixa prioridade; não bloqueia o desenho |
| **Q110-8** | **Para o contador:** o valor comparado com o limite é o mesmo que vai ao Y520 (líquido da retenção, em reais da data da operação)? E o "período" da ECF que tem menos de 12 meses conta meses inteiros ou proporcional aos dias? | Mesmo valor do Y520; meses inteiros |

**Texto pronto para a Receita (pergunta 9 do documento 98, se você aprovar a Q110-7).**

> Na ECF (leiaute 12), os campos 15 (IND_REC_EXT) e 17 (IND_PGTO_EXT) do registro 0020 citam, entre os casos que obrigam a marcar "Sim", valores por cartão de crédito "iguais ou superiores a R\$ 120.000,00, equivalentes a R\$ 10.000,00 por mês", mas não citam valores em moeda; o texto de abertura do registro Y520 cita cartão e também moeda nacional ou estrangeira, cheques e cheques de viagem, com o mesmo limite. Perguntamos: (a) o limite se aplica por forma de pagamento e por tipo (recebido e pago), somando todos os países? (b) o valor de R\$ 120.000,00 é um total anual ou se compara com R\$ 10.000,00 em cada mês? Para ECF de período menor que 12 meses, o limite é proporcional? (c) quem tiver apenas valores em moeda, acima do limite, deve marcar o indicador do 0020? (d) atingido o limite, informa-se o total da forma ou só o excedente?

# 9. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| `Mov_Ecf_Y520_Linha`: `Total_Forma_Tipo`, `Limite_Aplicado` (opcionais) | 0 | 2 |
| `parametro_ecf`: valor `limite_moeda_exterior_anual` | 0 | 0 (1 valor de domínio) |
| **Total do documento 110** | **0** | **2** |

Sobre a revisão 21 (920 entidades e 9.973 campos): **920 entidades e 9.975 campos**. A revisão 21 segue intacta até a consolidação.

# 10. Limites do que eu li

- Li o manual da ECF (leiaute 12, edição de 23/07/2026) nos campos 15 e 17 do 0020 e no registro Y520. **Não li** a norma que criou o limite, nem a Circular 3.690 do Banco Central; a leitura "equivalentes a R\$ 10.000 por mês" é minha e **não foi confirmada** pelo contador nem pela Receita.
- As páginas da internet que consultei não explicam a acumulação (só repetem o texto do manual).
- Não executei nenhum cálculo: não há dados de cliente. Os três exemplos são ilustrativos.
- O aviso a 80% do limite e o percentual são proposta minha, sem fonte.
