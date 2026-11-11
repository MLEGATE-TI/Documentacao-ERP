# Remessa Internacional e Banco Intermediário — Documento 107 (versão 1)

> **Não consolidado na revisão 21 (documento 108): as perguntas Q107-1 a Q107-6 estão sem resposta.** A lista completa de pendências está no documento 38.

> **Aprovado em 27/10/2026 ("sim aprovo", D-N371), junto com os sete pontos do documento 124; entra na revisão 25.** Onde este documento e o 124 divergem, vale o 124.

> **Detalhado em 27/10/2026 no documento 124** (pedido "detalhar Q107-1 a Q107-6"): o documento 124 ajusta a regra 4 (o valor em reais do retorno confere, não vira `Valor_Pago_Reais`), a regra 1 (a ordem só existe com banco do favorecido no exterior) e a contagem (revisão 24 como base), e traz sete pontos novos (Q107-1a a Q107-6a). Onde divergem, vale o documento 124, se você aprovar. Nada foi aplicado.

*Nasce da sua resposta à Q106-5 ("incluir"): a **ordem de pagamento ao exterior** e o **banco intermediário** entram no dicionário. Propõe como o item de remessa de pagamento da Tesouraria passa a carregar a ordem ao exterior, como o retorno do banco devolve o **contrato de câmbio**, a **taxa** e o **valor em reais**, e como isso fecha com o Y520 e com a regra da baixa ("vale o contrato de câmbio"). É uma proposta: **nada foi alterado no dicionário** (revisão 20: 915 entidades, 9.878 campos). Só entra depois das suas respostas e do seu "consolidar", com a lista de campos que você tiver visto.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **O que entra:** 1 entidade nova (`Mov_Remessa_Bancaria_Item_Exterior`, **uma linha por item de remessa que vai ao exterior**, 15 campos), **3 campos** no dado bancário do participante (banco intermediário) e **3 campos** no retorno do banco (contrato de câmbio, taxa e valor em reais). Total **1 entidade e 21 campos**, mais **1 valor novo** na enumeração `Forma_Lancamento` do item (`transferencia_internacional`).
- **A natureza já está no título.** A natureza do câmbio é obrigatória na entrada do título de não residente (Q103-2). A ordem **copia** a natureza do título, e o Y520 usa a mesma.
- **A forma do Y520 fica deduzida e confirmada ao gerar a remessa.** Ordem em **moeda estrangeira**: forma 1 (câmbio). Ordem em **reais** para banco no exterior: forma 2 (transferência internacional em reais). Gerar a remessa é "o momento do pagamento" (Q103-8): a tela mostra forma e natureza, e a baixa não nasce sem elas.
- **O retorno do banco devolve o que vale:** o **número do contrato de câmbio**, a **taxa** e o **valor em reais debitado**. A baixa automática copia a taxa e o valor em reais; o operador só digita quando **não há retorno** (baixa manual), como você decidiu na Q100-17 e na Q105-3.
- **Custo no dicionário:** com os opcionais, os documentos 100 a 103, 106 e 107 somam **921 entidades e 9.992 campos** (seção 8).

# 2. As suas respostas e como as li

| Nº | Sua resposta | Como li |
|--------|----------------------------------------|-------------------------------------------|
| Q106-1 a Q106-4 | Sim | Aprovados: identidade da instituição por ISPB ou SWIFT; instituição = banco ou agência no país da conta; IBAN e roteamento separados de agência e número; moeda da conta (documento 106, versão 2) |
| Q106-5 | "incluir" | A **remessa internacional** e o **banco intermediário** entram agora. Li os dois juntos, porque a pergunta os juntava |

# 3. O que o dicionário tem e o que falta

| Peça | O que existe | Lacuna |
|----------------------|----------------------------------------|----------------------------------|
| Item de remessa de pagamento | `Mov_Remessa_Bancaria_Item`: banco do favorecido (3 posições), agência (até 5), conta (até 20), nome, finalidade DOC ou TED, forma (`credito_conta`, `doc`, `ted`, `pix`, `cartao_salario`, `codigo_barras`), data, retenções, aviso ao favorecido | Sem SWIFT, IBAN, país, moeda da ordem, natureza, tarifas nem banco intermediário |
| Canal | `Canal_Transmissao` {`arquivo_cnab`, `api`, `open_finance`} no cabeçalho | Nada impede a ordem ao exterior; o **canal real** de cada banco **não verifiquei** (seção 7) |
| Retorno do banco | `Mov_Retorno_Bancario_Item`: valor total, principal, desconto, multa, juros, IOF, `ID_Baixa_Gerada` | Sem contrato de câmbio, taxa nem valor em reais |
| Baixa automática | Nasce do retorno, com `Valor_Baixado` = `Valor_Total_Ocorrencia` | Em título em moeda estrangeira, falta a taxa e o total em reais (documento 101) |
| Dado bancário do fornecedor | `Cad_Participante_Dados_Bancarios` com IBAN e roteamento (documento 106) | Falta o banco intermediário |
| Natureza | `Mov_Titulo.ID_Natureza_Operacao_Cambial`, obrigatória para não residente (documento 103) | Nenhuma: a ordem **copia** |

# 4. Proposta de campos

## 4.1 `Mov_Remessa_Bancaria_Item_Exterior` (nova): a ordem ao exterior

*Uma linha por item de remessa de pagamento que vai ao exterior (`Forma_Lancamento` = `transferencia_internacional`). Sem vigência (é um fato). **Cópia do que foi transmitido**, no mesmo critério dos campos do favorecido do item: o que foi enviado fica registrado mesmo que o cadastro mude depois.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Item_Exterior** | *identificador* | --- |
| **ID_Item_Remessa** | *referência (Mov_Remessa_Bancaria_Item), única* | O item a que a ordem pertence. Um item, no máximo uma linha. |
| **ID_Moeda** | *referência (Cad_Moeda)* | A moeda da ordem: a do título. Quando existe esta linha, `Valor_Principal_Remessa` do item está **nesta moeda**. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | Copiada do título (documento 103). A mesma natureza vai ao Y520. |
| **Codigo_Swift_Favorecido** | *código (11)* | O SWIFT do banco do favorecido, copiado de `Cad_Instituicao_Financeira`. Obrigatório. |
| **Iban_Favorecido** | *código (34), opcional* | Copiado do dado bancário do participante. |
| **Codigo_Roteamento_Favorecido** | *código (20), opcional* | Copiado do dado bancário do participante. |
| **Nome_Banco_Favorecido** | *texto* | O nome do banco, como foi transmitido. |
| **ID_Pais_Banco_Favorecido** | *referência (Cad_Pais)* | O país do banco, copiado da instituição. |
| **Endereco_Favorecido** | *texto, opcional* | O endereço do favorecido, como foi transmitido (texto único, copiado do endereço do participante). |
| **Responsavel_Tarifas** | *enumeração {remetente, dividido, favorecido}* | Quem paga as tarifas dos bancos: **OUR** (remetente), **SHA** (dividido), **BEN** (favorecido), o campo "details of charges" da mensagem SWIFT. Escolhido por quem paga, **sem valor padrão do ERP**. |
| **Codigo_Swift_Intermediario** | *código (11), opcional* | O banco intermediário, copiado do dado bancário do participante. |
| **Codigo_Roteamento_Intermediario** | *código (20), opcional* | Idem. |
| **Conta_Intermediaria** | *código (34), opcional* | A conta do favorecido (ou do banco dele) no intermediário. |
| **Numero_Contrato_Cambio_Previo** | *código (40), opcional* | O contrato de câmbio **já fechado antes** da ordem, quando houver. Vazio quando o banco abre o contrato ao executar. |

## 4.2 `Cad_Participante_Dados_Bancarios` (existente): 3 campos novos

*O banco intermediário (correspondente) que o fornecedor do exterior informa para receber.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Instituicao_Intermediaria** *(novo)* | *referência (Cad_Instituicao_Financeira, opcional)* | O banco intermediário. |
| **Codigo_Roteamento_Intermediario** *(novo)* | *código (20), opcional* | O código local do intermediário, quando o país usa (por exemplo, ABA nos EUA). |
| **Conta_Intermediaria** *(novo)* | *código (34), opcional* | A conta no intermediário. |

## 4.3 `Mov_Retorno_Bancario_Item` (existente): 3 campos novos

*Só quando o retorno é de uma ordem ao exterior.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **Numero_Contrato_Cambio** *(novo)* | *código (40), opcional* | O contrato de câmbio que o banco informa. Vai para a referência da operação do Y520 (`Referencia_Operacao`). |
| **Taxa_Cambio_Ocorrencia** *(novo)* | *número, opcional* | A taxa efetivamente cobrada, **do contrato**. A baixa automática a copia para `Taxa_Cambio` (documento 101). |
| **Valor_Reais_Ocorrencia** *(novo)* | *número, opcional* | O total **debitado em reais**, o que "cai na conta" (seu princípio da baixa). A baixa automática o copia para `Valor_Pago_Reais` (documento 101). `Valor_Total_Ocorrencia` fica **na moeda da ordem**. |

## 4.4 `Mov_Remessa_Bancaria_Item.Forma_Lancamento`: 1 valor novo

`transferencia_internacional`, na enumeração fechada do item. **0 campos.**

# 5. Regras propostas

- **1. Quando existe a ordem ao exterior.** O item de remessa de pagamento cujo favorecido é participante **não residente**, com forma `transferencia_internacional`, exige a linha da seção 4.1.
- **2. Validações da geração (bloqueiam a remessa):** SWIFT do favorecido preenchido; **IBAN ou número da conta**; natureza copiada do título; `Responsavel_Tarifas` escolhido; moeda da ordem igual à do título. **Avisos, sem bloquear:** país do SWIFT (posições 5 e 6) diferente do país do banco; roteamento ausente em país que costuma exigir.
- **3. Forma do Y520 (Q103-8).** Ordem em moeda estrangeira: **forma 1**; ordem em reais: **forma 2**. A tela de confirmação da remessa mostra **forma e natureza**; o operador confirma ao gerar. É o "momento do pagamento"; sem confirmar, a remessa não é gerada. Pelo quadro do manual que li (documento 88), as formas 1 e 2 são câmbio e transferência internacional em reais; **o contador confirma** que ordem em reais é a forma 2.
- **4. Baixa automática de ordem ao exterior.** Nasce do retorno aceito com `Valor_Baixado` na moeda do título, `Taxa_Cambio` = `Taxa_Cambio_Ocorrencia` e `Valor_Pago_Reais` = `Valor_Reais_Ocorrencia`, e a classificação do Y520 nasce **`classificada`** com a forma e a natureza da ordem e a referência = `Numero_Contrato_Cambio` (documento 100, regras 1 e 10). O operador pode **corrigir** a taxa e o valor em reais com motivo (o extrato do banco manda).
- **5. Retorno sem a taxa** (o banco não devolve): a baixa fica **pendente de taxa** na tela de consistência da Tesouraria (seção 6 do documento 09), e o operador digita (Q105-3). Nada trava o retorno.
- **6. Remessa e câmbio no mesmo dia.** O contrato de câmbio fecha na execução da ordem, então a taxa **não é conhecida na geração da remessa**; por isso `Taxa_Cambio` fica no retorno e não no item.
- **7. Banco intermediário.** Quando preenchido no dado bancário do fornecedor, **vai para a ordem** como cópia (campos da seção 4.1). Vazio vale "sem intermediário".
- **8. Tarifas e IOF do câmbio.** Chegam pelo retorno nos campos que já existem (`Valor_IOF_Ocorrencia` e os demais); não proponho campo novo de tarifa de câmbio. O tratamento contábil da tarifa e do IOF fica para o contador.

# 6. O que continua como está (para você conferir)

- A **forma 5** (recursos mantidos no exterior), a **forma 4** (depósito em conta no exterior) e o cartão **não passam por remessa**: o dinheiro não sai de conta no Brasil. Seguem pelo lançamento da baixa ou do contador, com a forma deduzida pela conta (documento 106, seção 5).
- A **conta de origem da remessa** é a conta bancária brasileira do cabeçalho (`Mov_Remessa_Bancaria.ID_Conta_Bancaria`). Não mudo.
- `Canal_Transmissao` fica {`arquivo_cnab`, `api`, `open_finance`}. Se a ordem ao exterior de algum banco sair em arquivo próprio do banco, o plugin do banco trata (diretriz de arquitetura de plugin por banco). Não acrescento valor sem saber o canal.

# 7. O que eu não sei e o que não proponho

- **Canal real das ordens ao exterior:** não encontrei, nas páginas que li, como os bancos brasileiros recebem a ordem ao exterior de empresa (arquivo, API ou portal). A página do Bradesco que li trata do **recebimento** e diz que a operação "é formalizada com o fechamento do respectivo contrato de câmbio". **A confirmar com o banco do cliente**: se há layout em arquivo e a API.
- **Tarifas (SHA, BEN, OUR):** o significado vem de um blog de uma corretora de câmbio ([Ebury](https://br.ebury.com/blog/sha-ben-e-our-o-que-e)): quem arca com os custos bancários, escolhido no fechamento do câmbio e visível no comprovante SWIFT. Não li a especificação da mensagem SWIFT; o nome "details of charges" vem dessa página.
- **Documentos exigidos para o contrato de câmbio** (fatura, contrato, comprovação): não proponho campo; o contador diz se algum precisa ser guardado.
- **Mensagem SWIFT pelo ERP** (o ERP não envia SWIFT; quem envia é o banco).
- **Instrução de recebimento** (documento com os dados da conta da empresa para o cliente do exterior pagar): fora.
- **Regra de limite de valor e fracionamento:** fora, como já decidido (documento 104).

# 8. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| `Mov_Remessa_Bancaria_Item_Exterior` (nova) | 1 | 15 |
| `Cad_Participante_Dados_Bancarios`: banco intermediário | 0 | 3 |
| `Mov_Retorno_Bancario_Item`: contrato, taxa e valor em reais | 0 | 3 |
| `Mov_Remessa_Bancaria_Item.Forma_Lancamento`: valor novo | 0 | 0 |
| **Total do documento 107** | **1** | **21** |

**Totais:** documentos 100 a 103 e 106 com os opcionais: **920 entidades e 9.971 campos**; com o 107: **921 entidades e 9.992 campos**. Sobre a revisão 20, **+6 entidades e +114 campos**. Se o `Codigo_Referencia` do documento 99 for aprovado, some 1 campo. A consolidação precisa varrer quem lê as entidades alteradas (remessa e retorno CNAB e API). O dicionário continua na **revisão 20**.

# 9. Perguntas

| Nº | Pergunta | Minha recomendação |
|--------|---------------------------------------------------|-----------------------------------------|
| **Q107-1** | A ordem ao exterior fica numa **entidade própria**, uma linha por item de remessa (15 campos), e não em campos soltos no item de remessa? | Sim: o item é desenhado para CNAB brasileiro e ficaria cheio de campos opcionais |
| **Q107-2** | O **retorno** traz o contrato de câmbio, a taxa e o valor em reais (3 campos), e a baixa automática os copia, com o operador podendo corrigir? | Sim, é o seu princípio ("vale o contrato de câmbio, valor que cai na conta") |
| **Q107-3** | A **forma do Y520 é deduzida** da moeda da ordem (estrangeira: câmbio; reais: transferência em reais) e confirmada na tela ao gerar a remessa? | Sim; **o contador confirma** o significado das formas 1 e 2 |
| **Q107-4** | `Responsavel_Tarifas` (remetente, dividido, favorecido) é **obrigatório e sem valor padrão** do ERP? | Sim, quem paga escolhe |
| **Q107-5** | O **banco intermediário** fica só no dado bancário do **fornecedor** e na ordem, **não** na conta da empresa? | Sim, porque a conta da empresa só serviria para uma instrução de recebimento, que está fora |
| **Q107-6** | A **natureza do câmbio** da ordem é sempre a do título, sem poder mudar na remessa? | Sim; para mudar, corrige-se o título (e a classificação) |

**Para o contador / banco (fora do desenho):** o canal da ordem ao exterior de cada banco do cliente; a forma 2 para ordem em reais; o tratamento contábil da tarifa e do IOF do câmbio; e se algum documento da operação de câmbio precisa ser guardado.

# 10. Limites do que eu li

- Li o **dicionário** (Tesouraria, Contas a Pagar e Receber, Fase 0 e os documentos 100 a 106) e três páginas: o **blog da Ebury** (sobre SHA, BEN e OUR), a **página do Bradesco** sobre ordem de pagamento (que trata de recebimento) e a **Wikipedia** (IBAN e ISO 9362, no documento 106). Não consegui ler a especificação da mensagem SWIFT.
- **Não verifiquei** o canal de nenhum banco, nem se o CNAB padrão tem layout de ordem ao exterior.
- **Não li** a norma do Banco Central sobre o contrato de câmbio; usei só o que a página do banco diz.
- Nada foi validado pelo contador.
