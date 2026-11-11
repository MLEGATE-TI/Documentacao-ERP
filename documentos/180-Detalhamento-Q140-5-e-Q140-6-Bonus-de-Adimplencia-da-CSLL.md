# Detalhamento da Q140-5 e da Q140-6: Bônus de Adimplência da CSLL — Documento 180

*Abre as duas perguntas que ficaram pendentes do documento 140 (LC 225/2026, art. 41) em perguntas menores, cada uma com opções, o efeito no dicionário e uma recomendação. **Nada foi aplicado ao dicionário.** A Q140-5 é do mecanismo (quais recolhimentos, como o desconto chega ao pagamento). A Q140-6 é da contabilidade e da ECF, e a resposta final é do contador; deixo a leitura que recomendo para você levar a ele.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **As duas perguntas não travam nada.** O primeiro bônus só pode existir a partir de abril de 2027 (arts. 40 a 47 em vigor desde 09/04/2026, mais 12 meses de selo; é conta minha do documento 140). Até lá o ERP calcula o bônus, **provisório e sem lançamento contábil automático**, e nada se perde se a resposta demorar.
- **Q140-5** vira cinco perguntas (Q140-5a a Q140-5e). A mais pesada é a **5d**: se o desconto vale para as estimativas mensais, o valor que a estimativa abate no ajuste anual é o valor **extinto** ou o **pago**? Dependendo da resposta, o benefício das estimativas some no ajuste (exemplo na seção 4).
- **Q140-6** vira cinco perguntas (Q140-6a a Q140-6e). A mais pesada é a **6a**: a conta onde o bônus entra. A escolha define se o lucro real precisa de **exclusão na Parte A do e-LALUR** (e na EFD-Contribuições) ou se **nada precisa**, porque o bônus fica abaixo da linha do lucro antes do IRPJ e da CSLL.
- **Minha recomendação em uma frase:** manter o que já está (calcular em toda linha de CSLL paga à vista, provisório, sem lançamento automático), acrescentar **1 campo** ao parâmetro para a regra "quais recolhimentos" deixar de ficar escondida no código, e levar ao contador a leitura de **redução da despesa de CSLL**.
- **O que vai para a Receita:** as perguntas 5a a 5e, mais uma pergunta sobre linha da ECF (6e), estão no texto da **pergunta 26 do documento 179**, que atualizei junto com este documento.

# 2. O que o dicionário já tem sobre o bônus

| Peça | O que está desenhado | Onde |
|---|---|---|
| `Cad_Parametro_Bonus_Adimplencia` | 16 campos, com vigência: 1% inicial, 12 meses mínimos de selo, 1 ponto por período de 12 meses, teto de 3%, limites anuais de R$ 250 mil, R$ 500 mil e R$ 1 milhão, não vale no Simples Nacional. Provisório até o contador validar. **Não tem campo** que diga **quais recolhimentos** valem. | Documento 10, seção 43.4 (revisão 29) |
| `Mov_Bonus_Adimplencia_Csll` | 18 campos. Liga-se à **linha de CSLL** da apuração (`ID_Apuracao_Item`) e ao selo. Calcula percentual, bônus teórico, limite e valor concedido; `Pago_A_Vista_Ate_Vencimento` vem da baixa do título; `Situacao` {calculado, confirmado, perdido}. **Não tem campo** de conta contábil nem de lançamento. | Documento 10, seção 43.4 |
| Linha de CSLL da apuração | `Mov_Apuracao_Irpj_Csll_Item` tem uma linha por tributo; a apuração (`Mov_Apuracao_Irpj_Csll`) pode ser trimestral, **estimativa mensal** ou anual. `Valor_Deducoes` inclui "estimativas já pagas". | Documento 10, apuração de IRPJ e CSLL |
| Provisão contábil | O lançamento da provisão do IRPJ e da CSLL usa o **valor da apuração** (soma das linhas já arredondadas), para a contabilidade e a ECF não divergirem (D-N373). | Documento 10 |
| DARF | O DARF da DCTFWeb entra por `Mov_Dctfweb_Darf` (número, vencimento, valor); se um DARF pago precisa de ajuste, o SISTAD gera outro no mesmo valor. A Tesouraria paga o DARF e a baixa fecha os títulos ligados a ele. | Documento 10, seção 22 |
| Desconto na baixa | `Mov_Baixa_Titulo.Valor_Desconto` já registra "desconto obtido" na baixa de um título a pagar, sem mexer no valor do título; o contador confirma a conta. `Cad_Tipo_Baixa` é cadastro: um tipo novo cabe sem campo novo. | Documento 8 |
| O que a lei diz (leitura do documento 140) | Art. 41: bônus **só para Confia e Sintonia**, **1% de desconto no pagamento à vista** da CSLL até o vencimento, depois de 12 meses de selo, mais 1 ponto por período de 12 meses até 3%; teto por ano do benefício; a parte não aproveitada não passa para outro período (§ 4º); **não entra na base de tributo algum** (§ 5º); não vale no Simples Nacional (§ 6º). | Documento 140, seção 5 |

**Limite desta leitura:** o texto da LC 225 **não está no meu ambiente agora**; trabalho com a leitura do documento 140 (feita sobre o texto colado) e não reli o artigo para este documento. Também não li o ato da Receita que regulamenta o bônus, se já existir.

# 3. Q140-5: o mecanismo do desconto

## Q140-5a. Quais recolhimentos de CSLL dão direito ao bônus?

A lei diz "desconto no pagamento à vista" da CSLL. Em uma empresa no lucro real anual, a CSLL é recolhida em **estimativas mensais** e no **ajuste anual**; no lucro real trimestral e no presumido, em **cada trimestre**.

| Opção | O que significa | Efeito no dicionário |
|---|---|---|
| **A. Todo recolhimento pago à vista (recomendo)** | Estimativa mensal, trimestre e ajuste anual dão bônus, cada um sobre o seu `Valor_A_Pagar`. | Como está hoje; **1 campo novo** no parâmetro (booleano `Vale_Estimativa_Mensal`) para a regra deixar de ficar escondida no código. Se você preferir não criar o campo, fica como regra de texto. |
| B. Só o recolhimento final | Trimestre e ajuste anual; a estimativa mensal não dá bônus. | O mesmo campo, com valor falso; ou regra de texto. |
| C. Esperar a regra da Receita | O ERP não calcula nada; o bônus fica só como lançamento manual do contador. | Nenhum campo; a rotina de cálculo (seção 5.7 do documento 140) sai da carga. |

**Por que recomendo A:** a lei não limita o desconto à apuração final, e o ERP já tem uma linha de CSLL por apuração. Como a regra "quais recolhimentos" é uma **suposição**, ela deve ser **dado com vigência** (regra do projeto: sem padrão escondido). O custo é 1 campo; se a Receita responder B, basta uma versão nova do parâmetro.

## Q140-5b. O que é "à vista"?

No lucro real trimestral e no presumido, a CSLL do trimestre pode ser paga em **cota única** ou em até **três quotas** mensais (leitura minha da Lei 9.430/1996, art. 5º; **não está nos documentos do projeto e não conferi o texto**). Não sei se a **primeira quota** ou a **cota única** conta como "à vista", nem se o pagamento **depois do vencimento** perde o bônus inteiro (hoje o ERP faz isso: `Valor_Bonus_Concedido` zero e situação `perdido`).

| Opção | O que significa |
|---|---|
| **A. Só a cota única, até o vencimento (recomendo)** | O pagamento em quotas não dá bônus; o ERP avisa quando o título vem de quota. |
| B. Cota única e primeira quota | O bônus vale sobre a quota paga no vencimento. |
| C. Qualquer pagamento integral até o vencimento | Pagar as três quotas de uma vez antes do primeiro vencimento também conta. |

**Efeito no dicionário:** nenhum campo. É regra de texto sobre `Pago_A_Vista_Ate_Vencimento`, que já vem da baixa do título. **Por que recomendo A:** é a leitura mais próxima da letra "à vista" e a mais conservadora (o ERP não promete desconto que a Receita pode negar); o aviso em quota deixa o contador decidir.

## Q140-5c. Como o desconto chega ao pagamento?

A lei só diz "desconto no pagamento à vista". Há três caminhos possíveis, e o ERP depende de qual é o real:

| Opção | O que significa | Como o ERP trata |
|---|---|---|
| **A. DARF com valor menor (recomendo como hipótese)** | O DARF (ou o débito na DCTFWeb) já sai com o desconto. | O título a pagar nasce do débito pelo valor do DARF; o ERP compara o valor do DARF com o `Valor_A_Pagar` da linha e marca a diferença como bônus. A baixa fica com valor pago menor e `Valor_Desconto` com a diferença. |
| B. Pagamento do valor cheio e crédito depois | O contribuinte paga o valor integral e recebe um crédito. | O bônus fica `calculado` até o crédito aparecer; entra o fluxo do PER/DCOMP, que o ERP já tem. |
| C. Outro (por exemplo, abatimento na DCTFWeb sem mudar o DARF) | A Receita define o mecanismo. | Sem desenho até haver ato. |

**Efeito no dicionário:** nenhum campo novo. Na opção A, convém **um tipo de baixa novo** em `Cad_Tipo_Baixa` ("bônus de adimplência"; não movimenta dinheiro além do pago) se o contador quiser separá-lo do desconto comum; é carga, não campo. **Por que A é só hipótese:** não achei o mecanismo em nenhum documento do projeto. Vale a pergunta à Receita (pergunta 26 do documento 179).

## Q140-5d. Valor extinto e o efeito nas estimativas do ajuste anual

Se a estimativa mensal dá bônus (opção A da 5a), o ajuste anual abate **"estimativas já pagas"** (`Valor_Deducoes`). A dúvida: abate o valor que **extinguiu o débito** (o integral, com o bônus) ou o **que saiu do caixa** (o integral menos o bônus)?

| Opção | O que significa | Efeito |
|---|---|---|
| **A. Valor extinto, o integral (recomendo)** | O débito foi quitado pelo valor integral; o bônus é um desconto concedido pela União. | O benefício das estimativas fica de fato com a empresa. |
| B. Valor pago | O ajuste anual abate só o que saiu do caixa. | O bônus das estimativas é devolvido no ajuste anual; o benefício real fica só no ajuste. |

**Efeito no dicionário:** nenhum campo; é regra de texto sobre como `Valor_Deducoes` soma as estimativas (hoje a regra não distingue). O exemplo da seção 4 mostra a diferença em reais. **Por que recomendo A:** é a leitura em que o bônus da estimativa tem efeito prático; se for B, o ERP deve **avisar** que o bônus das estimativas é devolvido no ajuste (para o contador não projetar um ganho que não existe). **Pergunta à Receita.**

## Q140-5e. Data de referência e consumo do limite anual

Dois pontos de data, com a mesma causa: a lei fala em desconto "no pagamento", mas o documento 140 conta os 12 meses de selo e o percentual até o **vencimento** (`Meses_Selo_Mantido`). Como o pagamento à vista é feito até o vencimento, a diferença só aparece na virada dos 12 ou 24 meses. E, com vários recolhimentos no mesmo ano do benefício, a **ordem** em que eles consomem o limite (R$ 250 mil no primeiro ano, por exemplo) muda o valor de cada um.

| Ponto | Opção A (recomendo) | Opção B |
|---|---|---|
| **Data para contar os meses de selo** | Vencimento do tributo (como está). | Data do pagamento. |
| **Ordem de consumo do limite** | Data do pagamento, e a mais antiga consome primeiro. | Data do vencimento. |

**Efeito no dicionário:** nenhum campo. `Meses_Selo_Mantido` e `Valor_Bonus_Ja_Concedido_No_Ano` já existem; só muda a regra que os preenche. **Por que recomendo:** o vencimento é a data que o ERP conhece antes do pagamento (permite mostrar o bônus previsto no título); a ordem de pagamento é a que a lei descreve ("desconto no pagamento"). Se a Receita responder outra coisa, ajusto a regra e o texto da descrição, sem mudar campos. **Pergunta à Receita, de baixa prioridade.**

# 4. Exemplos numéricos

**Exemplo 1: bônus de um trimestre (lucro real trimestral).** Selo desde 01/06/2026; vencimento em 30/06/2028 (25 meses de selo: 2%). CSLL a pagar R$ 500.000,00. Bônus teórico: R$ 10.000,00 (dentro do limite do ano 2, R$ 500 mil). A empresa paga R$ 490.000,00 à vista e o débito de R$ 500.000,00 é extinto (opção A da 5d).

**Exemplo 2: estimativas mensais e ajuste anual (a diferença da Q140-5d).** Empresa com selo há mais de 12 e menos de 24 meses (1%). Doze estimativas de CSLL de R$ 100.000,00 cada, todas pagas à vista (bônus de R$ 1.000,00, pagas R$ 99.000,00): R$ 1.200.000,00 de CSLL das estimativas, R$ 1.188.000,00 de caixa. CSLL anual apurada: R$ 1.500.000,00.

| | Leitura A (abate o valor extinto) | Leitura B (abate o valor pago) |
|---|---|---|
| Estimativas abatidas no ajuste | R$ 1.200.000,00 | R$ 1.188.000,00 |
| CSLL a pagar no ajuste | R$ 300.000,00 | R$ 312.000,00 |
| Bônus no ajuste (1%) | R$ 3.000,00 | R$ 3.120,00 |
| Caixa no ajuste | R$ 297.000,00 | R$ 308.880,00 |
| **Caixa total do ano** | **R$ 1.485.000,00** | **R$ 1.496.880,00** |
| **Bônus efetivo no ano** | **R$ 15.000,00 (1% de R$ 1,5 milhão)** | **R$ 3.120,00 (só o do ajuste)** |

Na leitura B os R$ 12.000,00 de bônus das estimativas voltam no ajuste. (Os números são de exemplo; o percentual e os limites vêm do parâmetro.)

# 5. Q140-6: tratamento contábil e na ECF

**Aviso:** esta é uma pergunta de **contabilidade**; a resposta é do contador. As leituras abaixo são minhas, para você levar a ele com argumentos. O ERP, até a resposta, **não faz lançamento contábil do bônus**.

**Ponto de partida (art. 41, § 5º):** o bônus **não entra na base de tributo algum**. Isso inclui IRPJ e CSLL (lucro real, presumido e arbitrado) e, pela letra, também PIS e Cofins.

## Q140-6a. Em que conta o bônus entra?

No pagamento com bônus, o lançamento é: **débito** na CSLL a pagar (valor integral), **crédito** no banco (valor pago) e **crédito** na conta do bônus (a diferença).

| Opção | Conta do crédito | Efeito na DRE |
|---|---|---|
| **A. Redução da despesa de CSLL (recomendo levar ao contador)** | A mesma conta da despesa (ou provisão) da CSLL. | O bônus reduz a despesa com a CSLL, **abaixo** do resultado antes do IRPJ e da CSLL. |
| B. Outras receitas operacionais | Uma conta de receita. | Entra **acima** do resultado antes do IRPJ e da CSLL. |
| C. Conta própria (por exemplo, "bônus de adimplência fiscal"), de resultado | Uma conta nova, no resultado. | Depende de onde o contador a posicionar (acima ou abaixo do resultado antes dos tributos sobre o lucro). |

**Por que levo A:** (1) o bônus é um desconto sobre a própria CSLL, e a provisão da CSLL já está na despesa de tributos sobre o lucro; (2) em A ele fica **abaixo** da linha em que a ECF do lucro real começa (leitura minha: o lucro líquido antes do IRPJ e da CSLL), logo **não exige exclusão** na Parte A; (3) não toca a receita da EFD-Contribuições, e o § 5º é cumprido sem ajuste. As opções B e C **exigem** os ajustes da 6b e da 6c. Se o contador preferir B ou C por transparência, o ERP aceita (a conta é dado), mas então os ajustes passam a ser obrigatórios.

## Q140-6b. Lucro real: exclusão na Parte A do e-LALUR e do e-LACS

| Se a conta for | Parte A do e-LALUR (IRPJ) e e-LACS (CSLL) |
|---|---|
| A (redução da despesa de CSLL) | Nada: o bônus não está no lucro antes dos tributos sobre o lucro. |
| B ou C (acima da linha) | **Exclusão** do valor do bônus no e-LALUR **e** no e-LACS, no período em que o bônus foi reconhecido, em linha própria de exclusão (a tabela dinâmica do M300 e a do M350). Não conferi a planilha: ela não está no meu ambiente. |

**Efeito no dicionário:** `Mov_Lalur_Lancamento_Parte_A` já aceita exclusão com sinal; ficaria só a regra "o ERP **sugere** a exclusão quando a conta do bônus está acima da linha". Sem campo novo.

## Q140-6c. Lucro presumido, arbitrado e PIS/Cofins

No **lucro presumido** e no **arbitrado** não há e-LALUR: a base é a receita bruta com o percentual de presunção. O bônus **não é receita** do período (§ 5º, "não entra na base"); logo, quando for lançado como receita (B ou C), ele precisa ficar **fora da receita bruta** da apuração. Na **EFD-Contribuições** vale o mesmo, para a receita não entrar na base de PIS e Cofins (o § 5º diz "tributo algum"; a letra é do documento 140).

**Efeito no dicionário:** na opção A, nenhum. Em B e C, o contador teria de cadastrar a conta do bônus como **fora da receita bruta**; o dicionário já tem esse tipo de marca nas contas de receita? Não verifiquei neste documento; entra como ponto de conferência se você escolher B ou C.

## Q140-6d. Quando reconhecer

| Opção | O que significa |
|---|---|
| **A. No pagamento, depois da aprovação do bônus (recomendo)** | O lançamento acontece quando o bônus passa de `calculado` a `confirmado` (o contador aprova, e o título foi pago à vista). |
| B. Na provisão | Reconhecer o bônus esperado quando a CSLL é provisionada. |

**Por que recomendo A:** o bônus só existe se o pagamento for à vista no prazo (art. 41, I); reconhecer antes é antecipar um ganho que a empresa ainda pode perder. Isso é coerente com a decisão D-N373 (a provisão usa o valor da apuração, **sem** o bônus).

## Q140-6e. O que o ERP faz hoje, e o que a ECF pede

| Ponto | Opção A (recomendo) | Opção B | Opção C |
|---|---|---|---|
| **Lançamento contábil** | Nenhum automático; o contador lança à mão (como está). | O ERP **sugere** o lançamento (débito na CSLL a pagar, crédito no banco e na conta do bônus) e o contador confirma. | O ERP lança sozinho. |
| **Campos novos** | Nenhum até o contador responder a 6a. | 2 campos opcionais em `Mov_Bonus_Adimplencia_Csll`: `ID_Conta_Contabil_Bonus` e `ID_Lancamento`. | Os mesmos 2, mais uma regra no motor. |
| **Linha da ECF** | Não sei se o leiaute 12 tem linha para o bônus; **pergunta à Receita** (pergunta 26 do documento 179). | — | — |

**Por que recomendo A:** o primeiro bônus só vem em abril de 2027, a conta depende da resposta do contador (6a), e o projeto já decidiu que o ERP só registra (D-N284). Os 2 campos da opção B custam pouco depois. O texto da pergunta 26 pergunta à Receita se a ECF tem linha própria; se tiver, a regra "o ERP mapeia o bônus" entra com a resposta.

# 6. Quadro-resumo e recomendações

| Nº | Pergunta | Recomendo | Muda o dicionário? | Quem responde |
|---|---|---|---|---|
| **Q140-5a** | Quais recolhimentos dão bônus | A: todo recolhimento pago à vista | +1 campo no parâmetro (ou regra de texto) | Você, depois a Receita |
| **Q140-5b** | O que é "à vista" | A: só a cota única, até o vencimento | Não (regra de texto) | Receita |
| **Q140-5c** | Como o desconto chega ao pagamento | A como hipótese: DARF com valor menor | Não (um tipo de baixa, se quiser) | Receita |
| **Q140-5d** | Valor das estimativas no ajuste anual | A: o valor extinto, o integral | Não (regra de texto) | Receita |
| **Q140-5e** | Data de referência e ordem do limite | A: vencimento para os meses; pagamento para a ordem | Não | Receita (baixa prioridade) |
| **Q140-6a** | Conta do bônus | A: redução da despesa de CSLL | Não | **Contador** |
| **Q140-6b** | Exclusão na Parte A | Nada, se a conta for A | Não | Contador |
| **Q140-6c** | Presumido, arbitrado e PIS/Cofins | Nada, se a conta for A | Não | Contador |
| **Q140-6d** | Quando reconhecer | A: no pagamento, depois da aprovação | Não | Contador |
| **Q140-6e** | Lançamento do ERP e linha da ECF | A: nenhum até o contador responder; perguntar à Receita sobre a linha | Não (2 campos, se for B) | Você e o contador |

**Se você responder "seguir as recomendações":** entra na próxima consolidação **1 campo** em `Cad_Parametro_Bonus_Adimplencia` (`Vale_Estimativa_Mensal`, booleano, valor inicial verdadeiro e `Situacao_Dado` provisória), as regras de texto das 5b, 5d e 5e, e as perguntas à Receita (5a a 5e e a linha da ECF) seguem pela pergunta 26 do documento 179. A contagem passa de 12.404 para 12.405 campos, com as mesmas 1.107 entidades.

# 7. Perguntas para você

**Q180-1.** Aprova as recomendações da Q140-5a a Q140-5e, incluindo o **1 campo novo** (`Vale_Estimativa_Mensal`) em `Cad_Parametro_Bonus_Adimplencia`? Recomendo **sim**. Se preferir **sem campo novo**, a regra da 5a fica só como texto.

**Q180-2.** A Q140-6 fica **com o contador**, e o ERP **não lança** o bônus até ele responder (opção A da 6e)? Recomendo **sim**. Você quer que eu escreva um **resumo de uma página** das opções 6a a 6e para você enviar ao contador?

**Q180-3.** Você tem o **ato da Receita** que regulamenta o bônus (se já saiu) ou o **texto do art. 41 da LC 225**? Com eles releio as hipóteses 5a a 5e; sem eles, as respostas vêm só da Receita.

# 8. Limites

- O texto da LC 225 **não está no meu ambiente**; este documento parte da leitura do documento 140. Não li o ato da Receita que regulamenta o bônus.
- A referência à Lei 9.430/1996, art. 5º (cota única e quotas, Q140-5b) é **conhecimento meu**, sem texto conferido nesta sessão.
- A leitura de que a ECF do lucro real começa no lucro **antes** do IRPJ e da CSLL, e de que a linha de exclusão existe nas tabelas do M300 e do M350, **não foi conferida na planilha** (ela não está no meu ambiente). As opções da Q140-6 são argumentos para o contador, não conclusão contábil.
- Nada foi aplicado ao dicionário (continua na revisão 32: 1.107 entidades e 12.404 campos).
