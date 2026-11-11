# Detalhamento da Q100-9: Conta no Exterior e as Formas 4 e 5 do Y520 — Documento 105 (versão 2)

> **Registro, sem campo (documento 108, revisão 21); vale o documento 106.** As contagens abaixo são as de quando o documento foi escrito.

*Você pediu para detalhar a Q100-9 do documento 100: marcar a conta como "no exterior" para sugerir as formas 4 (depósito em conta no exterior) e 5 (recursos mantidos no exterior)? Ao reler o dicionário para responder, achei **dois problemas na minha própria proposta** (seção 3): o campo estava no lugar errado, e o cadastro de bancos não aceita banco estrangeiro. É uma proposta de desenho: **nada foi alterado no dicionário** (revisão 20: 915 entidades, 9.878 campos). Só entra depois das suas respostas e do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

# Atualização da versão 2 (22/10/2026): as suas respostas

- **Q105-1:** **sim**, há cliente com conta da empresa no exterior. Isso afasta a opção A (nada).
- **Q105-2 ("que indicador?"):** era o campo `Eh_Conta_Exterior` da opção B, uma marca na conta contábil. **Ele deixou de existir**: com o cadastro do banco estrangeiro (Q105-4), o ERP **deduz** que a conta é do exterior pelo país da instituição. A opção B fica **superada**.
- **Q105-3:** sem contrato de câmbio, **vale a taxa que o operador do financeiro digita do pagamento**. **Aplicado** nos documentos 100 (versão 13) e 101 (versão 4), sem campo novo.
- **Q105-4:** o cadastro de banco estrangeiro **entra agora** (opção C). Desenhado no **documento 106**, com as perguntas Q106-1 a Q106-5.
- **Contagem deste documento:** **0 campos** (o indicador saiu do documento 100 e não entrou em outro lugar). O texto abaixo, das seções 1 a 8, é o **registro do raciocínio da versão 1**; vale o documento 106.

# 1. Resumo

- **O que a Q100-9 decide:** só a **sugestão** da forma. A forma já é **obrigatória na baixa** e **confirmada no pagamento** (Q103-8), então o ERP nunca fica sem forma. O ganho de marcar a conta é o ERP **acertar sozinho** a forma 4 ou 5 quando o dinheiro entra ou sai por conta da empresa no exterior.
- **Problema 1 (lugar do campo):** o documento 100 propunha o campo em `Cad_Conta_Bancaria`. Mas a **baixa não aponta para a conta bancária**: aponta para a **conta contábil** (`Mov_Titulo_Baixa.ID_Conta_Contabil`, tipo Banco, Caixa ou Aplicação). Para achar a conta bancária a partir da baixa seria preciso o caminho inverso, e uma conta contábil pode nem ter conta bancária.
- **Problema 2 (banco estrangeiro):** `Cad_Conta_Bancaria` exige uma instituição de `Cad_Instituicao_Financeira`, cuja identidade é o **ISPB** (8 posições, "toda instituição participante do SPB tem"). **Banco estrangeiro não tem ISPB.** Agência (até 5) e conta (até 20) também são medidas brasileiras, e **não há IBAN nem SWIFT** em lugar nenhum do dicionário. Hoje a conta da empresa no exterior **não consegue ser cadastrada como conta bancária**.
- **Recomendação:** **opção B**, 1 campo opcional **na conta contábil** (`Eh_Conta_Exterior`), que **substitui** o campo proposto em `Cad_Conta_Bancaria` (o total do documento 100 não muda). Sem cadastro bancário completo do exterior por enquanto (opção C fica registrada como lacuna).
- **Pergunta que só você responde (Q105-1):** algum cliente da Mlegate tem ou terá conta no exterior? Se não, a opção A (nada) basta.

# 2. O que o manual pede (formas 4 e 5)

Pelo quadro do campo `FORMA` do Y520, que li no manual (leiaute 12, documento 88), a forma **4** é o **depósito em conta no exterior** e só vale para **recebido**; a forma **5** é **recursos mantidos no exterior** e só vale para **pago**. Nos dois casos o dinheiro **não passa pelo contrato de câmbio no Brasil**: o recebimento cai direto numa conta da empresa fora do país, ou o pagamento sai de recursos que a empresa já mantém lá.

**O que isso muda para o ERP:** a baixa de um título com participante não residente, quando o dinheiro entra ou sai por **uma conta da própria empresa no exterior**, é forma 4 (recebido) ou 5 (pago). Nas outras formas (câmbio, transferência em reais, cartão, moeda) a conta usada é brasileira.

# 3. O que o dicionário tem e o que eu errei

| Peça | O que o dicionário tem hoje | Efeito |
|-------------------------|-----------------------------------------|-----------------------------------|
| Conta usada na baixa | `Mov_Titulo_Baixa.ID_Conta_Contabil`: "de onde saiu (pagar) ou para onde entrou (receber) o valor", tipo **Banco, Caixa ou Aplicação** | A baixa conhece a **conta contábil**, não a conta bancária |
| Conta bancária | `Cad_Conta_Bancaria` estende a conta contábil com agência, número, banco, convênio e CNAB; liga **até três** contas contábeis (corrente, poupança, aplicação), todas opcionais | O vínculo vai da conta bancária **para** a contábil, e uma conta contábil pode existir **sem** conta bancária |
| Banco | `Cad_Instituicao_Financeira`: identidade = **ISPB (8)**; COMPE (3) opcional | **Não aceita banco estrangeiro** |
| Número da conta | `Agencia` (até 5), `Numero_Conta` (até 20) | Não comportam IBAN (até 34 posições, pelo padrão ISO 13616, que **não verifiquei** no dicionário nem em fonte nesta sessão: é o que eu conheço) |
| SWIFT / IBAN | Só aparecem como justificativa de campos em `Cad_Pais` e `Cad_Moeda` | **Não existem campos** |
| Dados bancários do participante | `Cad_Participante_Dados_Bancarios`: mesma estrutura (instituição, agência, conta, Pix) | O **fornecedor estrangeiro** também não tem onde guardar IBAN e SWIFT |
| Extrato, conciliação, remessa | Pensados para CNAB, API do banco e Open Finance, todos brasileiros | Uma conta no exterior não teria retorno automático; só extrato manual |

**O que eu errei no documento 100:** pus o indicador em `Cad_Conta_Bancaria` sem checar para onde a baixa aponta. Pelo desenho que está no dicionário, o lugar certo para o ERP **saber, na baixa**, que a conta é do exterior é a **conta contábil**.

**Achado fora do Y520:** a lacuna do banco estrangeiro também afeta o **pagamento** a fornecedor do exterior (o histórico de decisões lista "remessa internacional" entre as modalidades do contas a pagar e receber e da Tesouraria, mas os dados para ela, IBAN e SWIFT, não têm campo). Registro aqui para você decidir (Q105-4); não é do Y520.

# 4. Três opções

## Opção A: não marcar nada

- **Como funciona:** o financeiro escolhe a forma na baixa (obrigatória). A sugestão vem só do histórico do participante e do tipo, como já está na regra 4 do documento 100.
- **Conta no exterior:** se existir, é uma conta contábil de tipo Banco comum, sem cadastro bancário. A baixa funciona hoje.
- **Custo:** **0 campos.**
- **Perde:** o ERP não acerta a forma 4 ou 5 no primeiro lançamento com o participante; erra mais na primeira vez.

## Opção B (recomendada): marcar a conta contábil

- **Campo:** `Eh_Conta_Exterior` (booleano, opcional) em `Cad_Conta_Contabil`. Vazio vale "não". Substitui o campo proposto em `Cad_Conta_Bancaria`.
- **Como funciona:** na baixa, a conta escolhida já diz se é do exterior. Se for, o ERP sugere **forma 4** quando o título é a receber e **forma 5** quando é a pagar. Essa sugestão **vale mais** do que a do histórico do participante. O financeiro confirma no pagamento (Q103-8).
- **Avisos, sem bloquear:** forma 4 ou 5 escolhida com conta **não** marcada; conta marcada com forma 1, 2, 3 ou 6. O bloqueio que já existe (4 só em recebido, 5 só em pago, regra 6 do documento 100) continua.
- **Custo:** **1 campo.** Total do documento 100 com os opcionais não muda (o campo sai de `Cad_Conta_Bancaria` e entra em `Cad_Conta_Contabil`).
- **Limite:** não cadastra o banco estrangeiro; só marca a conta contábil.

## Opção C: cadastro completo da conta no exterior

- **O que seria:** `Cad_Conta_Bancaria` e `Cad_Instituicao_Financeira` passam a aceitar banco estrangeiro (ISPB deixa de ser obrigatório para estrangeiro, entram país, SWIFT, IBAN), e o mesmo para os dados bancários do participante.
- **Custo:** **mexe em campo existente** (`Codigo_Ispb` é identidade) e acrescenta campos novos; **não detalho a lista** até você dizer que há cliente que precisa, para não desenhar à toa.
- **Quando faz sentido:** cliente que tem **tesouraria** no exterior (extrato, conciliação, saldo) ou que faz **remessa internacional** pelo ERP.
- **Recomendação:** **não agora**; fica como lacuna registrada (Q105-4).

# 5. Um ponto que a conta no exterior revela: taxa sem contrato de câmbio

Pelo princípio que você fixou ("na baixa vale o contrato de câmbio, o valor efetivo"), o documento 101 diz que `Taxa_Cambio` é a taxa do **fechamento do câmbio**, digitada. Nas formas **4 e 5 não há contrato de câmbio** (o dinheiro não passa pelo câmbio no Brasil), e o mesmo vale para **cartão** (3) e **moeda** (6). Nesses casos o "valor efetivo" é o **que o extrato da conta no exterior ou a fatura do cartão mostra**.

**Proposta (Q105-3):** o mesmo campo `Taxa_Cambio` guarda a **taxa efetivamente usada**, digitada por quem paga ou recebe, vendo o extrato ou a fatura. O ERP **não calcula** nem lê série de cotações. Custo: **0 campos**, só a descrição de `Taxa_Cambio` no documento 101 e a seção 6.5 do documento 100 passam a dizer "do fechamento do câmbio **ou, sem câmbio, a efetiva**".

**O que não sei (para o contador, não para o desenho):** qual **valor em reais** o manual da ECF espera no Y520 para as formas 4 e 5 (o do dia da operação, o do extrato). Não encontrei essa regra no que li. Também **não vi** a forma 5 em nenhuma das duas listas da regra 7 do documento 100 (sem limite, e com limite de R\$ 120.000); é um ponto para conferir no manual e com o contador, junto da Q100-11.

# 6. Contagem

**Versão 2:** este documento fica com **0 campos**. A opção B (1 campo na conta contábil) foi **superada**, e o campo opcional do documento 100 em `Cad_Conta_Bancaria` **saiu**. O que entra no dicionário para a conta no exterior está no **documento 106** (6 campos, 7 com a moeda da conta).

# 7. Perguntas

**Respondidas (22/10/2026):** Q105-1 (sim, há cliente com conta no exterior), Q105-2 (sem efeito: o indicador não existe mais, o ERP deduz pelo país da instituição), Q105-3 (vale a taxa que o operador digita do pagamento) e Q105-4 (o cadastro de banco estrangeiro entra agora, documento 106). **Nenhuma pergunta aberta neste documento.**

# 8. Limites do que eu li

- Li o **dicionário** (Contas a Pagar e Receber, Tesouraria e Fase 0) e o **quadro do campo `FORMA`** do manual da ECF pelo documento 88. **Não reli o manual** nesta sessão e **não li** nenhuma norma sobre a declaração de capitais no exterior; não afirmo se a empresa com conta fora tem outras obrigações.
- O tamanho do **IBAN** é conhecimento geral, não verificado agora.
- Nada foi validado pelo contador.
