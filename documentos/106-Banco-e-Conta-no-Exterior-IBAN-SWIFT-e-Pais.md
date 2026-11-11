# Banco e Conta no Exterior: País, SWIFT, IBAN e Moeda — Documento 106 (versão 2)

> **Consolidado na revisão 21 (23/10/2026, documento 108).** O `Codigo_Ispb` deixou de ser identidade e o banco perde a unicidade por ISPB (Q108-1, documento 38). **Q108-1 respondida em 27/10/2026** ("no caso de não ter o ISPB usar o BIC/SWIFT, só precisa ter um indicador"): proposta do campo `Tipo_Identificador` no documento 129. As contagens abaixo são as de quando o documento foi escrito.

*Nasce das suas respostas à Q105-1 (há cliente com conta da empresa no exterior: **sim**) e à Q105-4 (o cadastro de banco estrangeiro **entra agora**). Propõe como o dicionário passa a guardar o **banco e a conta no exterior**, para a conta da empresa e para o dado bancário do fornecedor, e como o ERP **descobre sozinho** que uma baixa saiu de, ou entrou em, conta no exterior (formas 4 e 5 do Y520). É uma proposta: **nada foi alterado no dicionário** (revisão 20: 915 entidades, 9.878 campos). Só entra depois das suas respostas e do seu "consolidar", com a lista de campos que você tiver visto.*

Mlegate · Alberto Beyeler · Outubro de 2026

# Atualização da versão 2 (22/10/2026): as suas respostas

- **Q106-1 a Q106-4: sim.** Ficam aprovados: identidade da instituição por ISPB (Brasil) ou SWIFT (exterior); instituição = banco ou agência no país da conta; IBAN e roteamento separados de agência e número, com agência e número opcionais e obrigatórios só no Brasil; e a moeda da conta.
- **Q106-5: "incluir".** A **remessa internacional** e o **banco intermediário** entram. Desenhados no **documento 107** (1 entidade e 21 campos), com as perguntas Q107-1 a Q107-6.
- **Contagem deste documento:** continua **6 campos, 7 com a moeda da conta**; agora **sem pergunta aberta**. O "Para o contador" da seção 8 segue valendo.

# 1. Resumo

- **Sobre a sua pergunta "que indicador?" (Q105-2):** era o campo `Eh_Conta_Exterior` que eu propunha na conta contábil, uma marca de "esta conta é do exterior". **Com o cadastro do banco estrangeiro, ele deixa de ser necessário**: o ERP deduz que a conta é do exterior pelo **país da instituição** (seção 5). Nada para o usuário marcar, e nada a mais para guardar.
- **O que entra:** **6 campos** em entidades que já existem (7 com a moeda da conta, opcional), **nenhuma entidade nova** e **3 campos existentes que passam a ser opcionais com regra** (`Codigo_Ispb`, `Agencia`, `Numero_Conta`), porque banco e conta estrangeiros não têm ISPB, agência de 5 posições nem número de 20.
- **Como o banco estrangeiro é identificado:** pelo **SWIFT (BIC)**, no lugar do ISPB, e pelo **país**.
- **Como a conta estrangeira é guardada:** pelo **IBAN** (quando o país usa) e por um **código de roteamento local** (quando não, como EUA, Canadá e Austrália), além da agência e do número que já existem.
- **Taxa sem contrato de câmbio (Q105-3, respondida):** vale a taxa que o operador do financeiro digita no pagamento. Já apliquei nos documentos 100 e 101 (seção 6).
- **Custo no dicionário:** com os opcionais, os documentos 100 a 103 e 106 somam **920 entidades e 9.971 campos** (seção 7; com o documento 107, 921 e 9.992).

# 2. As suas respostas e como as li

| Nº | Sua resposta | Como li |
|--------|----------------------------------------|-------------------------------------------|
| Q105-1 | Sim, algum cliente tem ou terá conta no exterior | O dicionário precisa cadastrar a conta no exterior, não só marcar uma conta contábil (opção B do documento 105) |
| Q105-2 | "Que indicador?" | Explicado na seção 1: o indicador some, porque o país da instituição já diz |
| Q105-3 | "Se não tem contrato de câmbio vale a taxa que o operador do financeiro colocar de pagamento" | A `Taxa_Cambio` digitada vale também sem câmbio; **aplicado** nos documentos 100 e 101 |
| Q105-4 | "Entra agora" | A opção C do documento 105 entra: país, SWIFT e IBAN, para a **conta da empresa** e para o **dado bancário do fornecedor**. **Não** li como incluindo a **remessa internacional** (envio do pagamento ao banco por arquivo ou API); pergunto na Q106-5 |

# 3. O que as fontes dizem (para o desenho dos campos)

- **IBAN:** "até 34 caracteres alfanuméricos": país (2 letras), dígitos verificadores (2) e a conta do país (até 30). **EUA, Canadá e Austrália não usam IBAN**: os EUA usam o número de roteamento (ABA), o Canadá o número de instituição e trânsito, a Austrália o BSB. ([Wikipedia, IBAN](https://en.wikipedia.org/wiki/International_Bank_Account_Number))
- **SWIFT ou BIC (ISO 9362):** **8 ou 11 caracteres**: banco (4 letras), **país** (2 letras, ISO 3166-1 alfa-2), localidade (2) e agência (3, opcional; "XXX" é a matriz). O país está embutido nas posições 5 e 6. ([Wikipedia, ISO 9362](https://en.wikipedia.org/wiki/ISO_9362))
- **Dados que um pagamento ao exterior costuma pedir** (num formulário de uma universidade americana, só como exemplo): nome, endereço e país do banco, SWIFT, o **identificador local** (BSB 6 dígitos na Austrália, sort code 6 dígitos no Reino Unido, BLZ 8 na Alemanha, IFSC 11 na Índia e outros) e o **IBAN ou número da conta**; o **banco intermediário** (correspondente) é opcional. ([formulário de exemplo](https://www.grant.sc.edu/about/offices_and_divisions/controller/documents/intl_wire_transfer_form_updated.pdf))

Isso explica os tipos escolhidos abaixo: IBAN 34, SWIFT 11, roteamento até 20 (cobre os exemplos acima; o limite é meu e é só de tamanho, não de formato).

# 4. Proposta de campos

## 4.1 `Cad_Instituicao_Financeira` (existente): 2 campos novos e 1 alteração

*Hoje a identidade é o ISPB ("toda instituição participante do SPB tem"). Banco estrangeiro não tem. Proposta: a instituição passa a ser **"o banco, ou a agência do banco, no país onde mantém a conta"**. O Banco do Brasil de Miami, por exemplo, é **um cadastro próprio**, com SWIFT e país EUA, sem ISPB (Q106-2).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Pais** *(novo)* | *referência (Cad_Pais)* | O país onde a instituição (ou a sua agência) opera. **Obrigatório.** Na carga das instituições atuais, Brasil. É o que o ERP usa para saber que a conta é do exterior. |
| **Codigo_Swift** *(novo)* | *código (11), opcional* | O SWIFT ou BIC, de 8 ou 11 posições, guardado como informado. **Obrigatório quando o país não é o Brasil**; opcional para banco brasileiro (útil para câmbio). Aviso quando as posições 5 e 6 não batem com o `Codigo_Iso_Alfa2` do país (a Kosovo é exceção, pois o SWIFT usa "XK", sem código ISO). |
| **Codigo_Ispb** *(alterado)* | *código (8), opcional* | Passa de obrigatório e identidade para **opcional**; **obrigatório quando o país é o Brasil**. A identidade da instituição passa a ser o ISPB (Brasil) **ou** o SWIFT (exterior). |

## 4.2 `Cad_Conta_Bancaria` (existente): 2 campos novos, 1 opcional e 2 alterações

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **Iban** *(novo)* | *código (34), opcional* | O IBAN da conta, quando o país usa. |
| **Codigo_Roteamento** *(novo)* | *código (20), opcional* | O identificador local do banco ou agência, quando o país usa: ABA nos EUA, BSB na Austrália, sort code no Reino Unido, entre outros. Um campo só, porque cada país usa um só tipo. |
| **ID_Moeda_Conta** *(novo, opcional)* | *referência (Cad_Moeda, opcional)* | A moeda da conta. Vazio vale a moeda funcional da empresa. Serve para avisar quando o título está em outra moeda (Q106-4). |
| **Agencia** *(alterado)* | *código (até 5), opcional* | Passa a **opcional**; **obrigatória quando a instituição é brasileira**. |
| **Numero_Conta** *(alterado)* | *código (até 20), opcional* | Passa a **opcional**; **obrigatório quando a instituição é brasileira**. No exterior vale o número **ou** o IBAN (um dos dois). |

## 4.3 `Cad_Participante_Dados_Bancarios` (existente): 2 campos novos

*O fornecedor ou cliente estrangeiro. `ID_Instituicao_Financeira` já existe (opcional) e agora aceita a instituição estrangeira; agência e conta já são opcionais.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **Iban** *(novo)* | *código (34), opcional* | O IBAN da conta do participante no exterior. |
| **Codigo_Roteamento** *(novo)* | *código (20), opcional* | Como em `Cad_Conta_Bancaria`. |

## 4.4 O que não proponho agora

- **Remessa internacional** (`Mov_Remessa_Bancaria_Item` com IBAN e SWIFT do favorecido, como cópia do que foi transmitido): o item de remessa é desenhado para CNAB e API brasileiros (banco de 3 posições, agência de 5). Pergunto na Q106-5.
- **Banco intermediário** (correspondente) e **endereço do banco**: o formulário de exemplo os pede, mas eles pertencem à ordem de pagamento, não ao cadastro.
- **Extrato automático** da conta no exterior: o extrato já aceita o lançamento manual (`Origem_Importacao` = manual); não há Open Finance nem CNAB fora do Brasil.
- **Obrigações da empresa que mantém conta no exterior** (por exemplo, declarar o saldo ao Banco Central): **não li a norma**; é ponto do contador, não do desenho.

# 5. Como o ERP sabe que a conta é do exterior (formas 4 e 5)

- **Caminho:** a baixa tem a **conta contábil** (`Mov_Titulo_Baixa.ID_Conta_Contabil`); a conta bancária que a liga (um dos três vínculos de `Cad_Conta_Bancaria`) tem a **instituição**; a instituição tem o **país**. **País diferente de Brasil: conta no exterior.** Nada é marcado à mão e nada é guardado de novo (o dicionário não guarda o que se deduz).
- **Sugestão da forma na baixa:** título a receber em conta no exterior: **forma 4**; título a pagar de conta no exterior: **forma 5**. Essa sugestão **vale mais** do que a do histórico do participante, e o financeiro confirma no pagamento (Q103-8).
- **Avisos, sem bloquear:** forma 4 ou 5 com conta que não é do exterior; conta no exterior com forma 1, 2, 3 ou 6. O bloqueio que já existe continua (4 só em recebido, 5 só em pago, regra 6 do documento 100).
- **Sem conta bancária cadastrada** para a conta contábil (por exemplo, um caixa): o ERP **não sugere**, o financeiro escolhe a forma. Por isso a conta contábil de um banco no exterior deve ter a sua conta bancária.

# 6. O que já apliquei nos documentos 100 e 101 (Q105-3)

- **Documento 101 (versão 4):** `Taxa_Cambio` da baixa e do adiantamento passam a dizer: do fechamento do câmbio **ou, sem contrato de câmbio** (cartão, depósito em conta no exterior, recursos mantidos no exterior, moeda), **a taxa que o operador do financeiro digita do pagamento**. Sem campo novo.
- **Documento 100 (versão 13):** seção 6.5 com a mesma frase; a Q100-9 sai das abertas; o campo opcional de indicador de conta no exterior sai da contagem (ficou no documento 106, deduzido).
- **Documento 105 (versão 2):** vira registro das respostas; a opção B (indicador na conta contábil) fica superada.

# 7. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| `Cad_Instituicao_Financeira`: `ID_Pais`, `Codigo_Swift` | 0 | 2 |
| `Cad_Conta_Bancaria`: `Iban`, `Codigo_Roteamento` | 0 | 2 |
| `Cad_Participante_Dados_Bancarios`: `Iban`, `Codigo_Roteamento` | 0 | 2 |
| **Subtotal (proposta mínima)** | **0** | **6** |
| `Cad_Conta_Bancaria`: `ID_Moeda_Conta` (opcional, Q106-4) | 0 | 1 |
| **Total com o opcional** | **0** | **7** |
| Alterações de campo existente (`Codigo_Ispb`, `Agencia`, `Numero_Conta`: obrigatório para opcional com regra) | 0 | 0 |

**Totais:** o documento 100 sem o indicador: **919 entidades e 9.939 campos** com os opcionais (eram 9.940); com o documento 101: **920 e 9.961**; com o 103 (3 campos): **920 e 9.964**; com o 106: **920 entidades e 9.970 campos** na proposta mínima e **9.971** com o `ID_Moeda_Conta`. Sobre a revisão 20, **+5 entidades e +93 campos**. O dicionário continua na **revisão 20**.

# 8. Perguntas

**Respondidas (22/10/2026):** Q106-1, Q106-2, Q106-3 e Q106-4 (sim) e Q106-5 (incluir; documento 107). **Nenhuma pergunta aberta neste documento.**

**Para o contador** (fora do desenho): o **valor em reais** do Y520 nas formas 4 e 5, a forma 5 que não aparece nas duas listas da regra 7 do documento 100, e as **obrigações da empresa com conta no exterior**.

# 9. Limites do que eu li

- **Fontes externas lidas hoje:** a página da Wikipedia sobre IBAN, a sobre o ISO 9362 e **um formulário de universidade americana**, usado só como exemplo de campos. **Não li as normas** do IBAN (ISO 13616) nem do BIC (ISO 9362), só o resumo da Wikipedia, nem norma brasileira sobre conta no exterior.
- Os limites de **tamanho** (IBAN 34, SWIFT 11, roteamento 20) cobrem o que li; o de 20 do roteamento é meu e não foi checado país a país.
- O dicionário foi lido nos documentos de Contas a Pagar e Receber, Tesouraria e Fase 0; **não** rodei checagem automática de impacto (por exemplo, quem mais lê `Codigo_Ispb`, `Agencia` e `Numero_Conta`, como a remessa CNAB). A consolidação precisa dessa varredura.
- Nada foi validado pelo contador.
