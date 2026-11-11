# Desenho do B5: regimes setoriais da CBS (bares e restaurantes, cooperativa, locação por temporada e agência de turismo) — Documento 150

*Terceiro dos seis desenhos que você liberou com o reenvio da LC 214, da LC 227 e do Decreto 12.955 (Q161-4), na ordem que você escolheu (156, 157, 150, 158, 159 e 160). Responde à Q148-5 (bares e restaurantes é o próximo desenho), à Q148-15 (modelo de relação com agência e plataforma) e à Q94-4 (onde fica o tipo de serviço da agência). **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O B5 do documento 94 reunia os regimes setoriais que a LC 214 trata em capítulos próprios. Antes de desenhar, conferi o que o dicionário já tem para cada um. **O dicionário já cobre mais do que parecia**: o Motor de Regras escolhe o código de tributação e o percentual de redução vive em `Cad_Cclasstrib`; a base especial já tem catálogo (`Cad_Regra_Base_Calculo_Cbs`) e linhas por item (`Mov_Apuracao_Tributo_Item_Base_Especial`); a dedução da agência já tem `Mov_Agencia_Turismo_Repasse`; o regime específico e a listagem da cooperativa já existem; o hotel e o TEF foram consolidados na revisão 27. Por isso este documento desenha **só o que falta**.

O desenho acrescenta **5 entidades novas (71 campos)** e altera **11 existentes**, com **17 campos novos**, 2 valores novos em enumerações existentes e 3 grupos de valores de domínio (seção 8). Tudo na Contabilidade & Fiscal.

| Regime | O que a lei diz | O que o dicionário já tinha | O que este documento acrescenta |
|---|---|---|---|
| **Bares e restaurantes** (LC, arts. 273 a 276; Decreto, arts. 396 a 401) | Redução de 40%; crédito vedado ao adquirente; gorjeta e valores de plataforma saem da base se segregados e dentro do limite de 15%; sem segregação, a base é o total (§ 4º) ou o regime geral (art. 398) | Catálogo de base especial, linhas por item, Motor de Regras, hotel com o mesmo regime | Limite da exclusão (cinco colunas na regra, três na linha), conferência do repasse da gorjeta, fornecimento sob contrato |
| **Cooperativa** (LC, arts. 271 e 272; Decreto, arts. 391 a 395) | Alíquota zero entre associado e cooperativa optante; o associado transfere crédito até o menor de dois limites, com nota de débito específica | Regime específico, associados, listagem, créditos e taxas de depreciação | Transferência de crédito (`Mov_Cooperativa_Transferencia_Credito`), tipo da cooperativa, associado fora do regime regular, tipo de envio da listagem |
| **Locação por temporada** (LC, art. 253; Decreto, art. 410) | Locação de imóvel residencial por até 90 dias ininterruptos segue as regras da hotelaria | Só a locação de longo prazo, mensal | `Mov_Locacao_Temporada` e `Cad_Locacao_Temporada_Regra` |
| **Agência de turismo** (LC, arts. 288 a 291; Decreto, arts. 417 a 420) | Dedução do repasse na intermediação; sem dedução no fornecimento direto; crédito do adquirente | Repasse, conferência de valor e câmbio | `Tipo_Servico_Agencia` (Q94-4) e o modelo de relação com a agência (Q148-15) |

**Seis achados que você precisa ler.**

1. **A numeração do Decreto não é a da LC.** Cooperativa: LC, arts. 271 e 272 = Decreto, arts. 391 a 395. Bares e restaurantes: LC, arts. 273 a 276 = Decreto, arts. 396 a 401. Locação de temporada: LC, art. 253 = Decreto, art. 410. Agência: LC, arts. 288 a 291 = Decreto, arts. 417 a 420. Cito sempre os dois.
2. **O limite de 15% da gorjeta tem três pontos que o texto não resolve** (sobre o quê se mede, o que acontece com o excesso e como o § 3º rateia). Modelei os três como **parâmetros com vigência** e carreguei uma leitura conservadora e provisória; o contador decide (Q150-C1 a Q150-C3). Nenhum percentual ou regra fica escondido no código.
3. **O repasse da gorjeta ao empregado é fato de folha, não de nota.** A exclusão da base depende dele (art. 399, § 1º, I, a), mas o ERP de vendas não o enxerga. Criei uma conferência mensal que **avisa, não bloqueia**; a exclusão da base não espera por ela.
4. **A LC 227 incluiu a locação de temporada na receita e na contagem de imóveis dos limites da pessoa física** (LC, art. 253, § 2º). O dicionário já tinha `Mov_Locacao_Limite_Pf`; o texto dele passa a dizer isso, sem campo novo. O Decreto repete no art. 410, § 1º (a pessoa física é contribuinte do regime regular se atender ao art. 382).
5. **A LC limita a transferência de crédito da cooperativa mais do que o Decreto.** O art. 272, parágrafo único, da LC diz que a transferência alcança **apenas os bens e serviços usados na produção do que o associado fornece à cooperativa**; o art. 394 do Decreto não repete a frase e usa só os dois limites dos §§ 1º a 3º. Carrego a leitura do Decreto como provisória e pergunto ao contador (Q150-C7).
6. **Q140-7 (`Cad_Aliquota_Combustivel`) não é deste desenho.** O B5 do documento 94 e a Q148-5 só falam de bares e restaurantes e hotelaria; combustíveis é regime monofásico. Mantive a linha de pendência e pergunto na Q150-11.

# 2. Regras que segui

Valem as dos documentos 156 e 157 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória com `Situacao_Dado = provisorio` até o contador validar; o ERP avisa e nunca bloqueia; extensão 1:1 para o que a minoria usa; nomes em português com sublinhado; prefixo `Valor_` só em número, referência, texto e enumeração). Mais estas:

1. **O percentual de redução fica em `Cad_Cclasstrib`.** Os 40% de bares e restaurantes, da hotelaria e da locação de temporada não aparecem em nenhuma tabela nova: o Motor escolhe o cClassTrib e o percentual vem dele (D-N426, Q148-13). Este documento não inventa código de classificação tributária; as regras do Motor são cadastro do usuário e do contador.
2. **Cito sempre "LC, art. X" e "Decreto, art. Y".**
3. **O ERP só registra o que não se deriva.** Limite, parcela da gorjeta, teto da transferência de crédito, dias de ocupação e enquadramento saem de cálculo; guardo o valor calculado só quando um evento posterior pode mudá-lo e o cálculo precisa se repetir sem ambiguidade.
4. **Reaproveito o padrão de `Mov_Apuracao_Tef`** para o que depende de decisão: `Status` {calculada, pendente_decisao, confirmada}, com a pendência escrita por extenso.
5. **Uma leitura minha é sempre dita como minha.** Onde o texto não decide, a coluna e a pergunta dizem; a carga sai provisória.


# 3. Bares e restaurantes (LC, arts. 273 a 276; Decreto, arts. 396 a 401)

## 3.1 O que o texto pede

O regime vale para a alimentação e as bebidas **não alcoólicas** preparadas e manipuladas no próprio estabelecimento de bares, restaurantes, lanchonetes, pastelarias, padarias, casas de chá, de sucos, de doces e salgados, cafeterias e sorveterias (Decreto, art. 396). A alíquota tem redução de 40% (art. 400) e o adquirente não toma crédito (art. 401).

Ficam **fora do regime** e seguem o regime geral (art. 397): a alimentação para pessoa jurídica sob contrato, ainda que não formalizado, classificada nas posições 1.0301.31.00, 1.0301.32.00 e 1.0301.39.00 da NBS ou fornecida por empresa de CNAE 5620-1/01; o produto comprado de terceiros e não preparado no estabelecimento; e a bebida alcoólica, ainda que preparada no local.

O documento fiscal precisa **segregar** o que é do regime e o que é do regime geral; sem segregação, o valor total vai para o regime geral (art. 398, parágrafo único).

A base é o valor da operação de fornecimento (art. 399). **Saem da base** (§ 1º): (I) a gorjeta do fornecimento de alimentação no regime, desde que (a) seja repassada integralmente ao empregado, sem prejuízo do que o empregador retiver por determinação legal, e (b) não passe de 15% do valor total do fornecimento de alimentação e de bebidas; (II) os valores não repassados ao bar ou restaurante pelo serviço de entrega e intermediação de pedidos por plataforma digital. A exclusão exige que gorjeta e valores da plataforma estejam **segregados** no documento (§ 2º); o percentual se calcula pela relação entre o fornecimento no regime e o valor total da operação (§ 3º); sem segregação, a base é o valor total do fornecimento no regime (§ 4º). **A LC só tem as exclusões e o teto** (art. 274, parágrafo único); a segregação, o rateio do § 3º e o § 4º são do Decreto, e as linhas de carga correspondentes levam `Origem_Regra = decreto` e vão ao contador.

## 3.2 O que o dicionário já tem

| Peça | O que faz |
|---|---|
| `Cad_Regra_Base_Calculo_Cbs` | Uma linha por componente da base, com `Efeito_Na_Base` {integra, exclui, substitui, reduz_percentual, …}, `Percentual_Reducao` e as marcas `Exige_Constar_No_Documento_Fiscal` e `Exige_Sem_Evento_Posterior`. Serve ao desconto incondicional e ao reembolso |
| `Mov_Apuracao_Tributo_Item_Base_Especial` | A linha filha da apuração, com `Valor_Ajuste` com sinal (positivo integra, negativo exclui) e `ID_Regra_Base_Calculo` |
| Motor de Regras | Escolhe `id_cst_ibs_cbs` e `id_classtrib` por critérios (NBS, CNAE do item, cliente) |
| Documento 148 (hotel) | O hotel usa as mesmas regras de bares e restaurantes e a nota sem item próprio gera aviso |

**O que falta**, em quatro pontos: (1) o dicionário não sabe de **limite**: nenhuma linha da base especial tem teto; (2) não há **componente** para a gorjeta nem para o valor da plataforma; (3) o Motor não tem como dizer, no resultado, "este item é um componente da base" (ele só devolve código de tributação, alíquota e destinação); (4) nada confere o **repasse ao empregado**. O art. 397, I (alimentação a pessoa jurídica sob contrato) também não tem critério: o CNAE do emitente e a marca "sob contrato" não existem como critério do Motor.

## 3.3 Desenho

**Componentes.** Dois valores novos no domínio `componente_base_calculo_ibs_cbs`: `gorjeta_bar_restaurante` e `intermediacao_plataforma_pedido`. O usuário ou o PDV lança cada um como item próprio da nota (a segregação do § 2º); o Motor reconhece o item e devolve o novo resultado `componente_base_calculo`, e o ERP gera a linha de base especial.

**Limite.** Cinco colunas novas em `Cad_Regra_Base_Calculo_Cbs` (sobre o quê se mede, qual percentual, se rateia pelo § 3º, o que acontece com o excesso, e se exige repasse); três colunas novas em `Mov_Apuracao_Tributo_Item_Base_Especial` (o valor informado, o teto calculado e a situação do limite). A leitura provisória carregada é: o teto é 15% do valor total do fornecimento de alimentação e de bebidas **do documento** (`total_alimentacao_e_bebidas`); a gorjeta entra na conta pela **parcela** do § 3º (fornecimento no regime dividido pelo valor total da operação, com a gorjeta); se passa do teto, **todo o valor integra a base** (`todo_valor_integra`), a leitura literal de "desde que não exceda". A outra leitura possível (`so_excesso_integra`) fica a um valor de enumeração de distância.

**Fornecimento sob contrato.** `Indicador_Fornecimento_Sob_Contrato` na nota de saída (o usuário marca; art. 397, I diz "ainda que não formalizado", então o contrato não é prova), mais três critérios novos do Motor (`cnae_do_emitente`, `tipo_pessoa_do_destinatario`, `fornecimento_sob_contrato`). O critério de NBS já existe.

**Repasse da gorjeta.** `Mov_Gorjeta_Repasse_Periodo` (seção 3.5): um registro por estabelecimento e mês que confere a gorjeta cobrada, a retida por lei e a repassada. Avisa; não bloqueia.

## 3.4 Exemplo calculado

Nota de um restaurante com alimentação preparada no local de R$ 1.000,00 (regime), uma bebida alcoólica de R$ 200,00 (regime geral) e gorjeta segregada de R$ 120,00. Valor total do fornecimento de alimentação e bebidas: R$ 1.200,00; valor total da operação com a gorjeta: R$ 1.320,00; teto de 15%: R$ 180,00; relação do § 3º: 75,76%.

| Caso | Gorjeta | Dentro do teto? | Parcela da gorjeta que cabe ao regime | Exclusão (`Valor_Ajuste`) | Base do regime |
|---|---|---|---|---|---|
| 1. Dentro do teto, repassada | R$ 120,00 | Sim | R$ 90,91 | −R$ 90,91 | R$ 1.000,00 |
| 2. Acima do teto, `todo_valor_integra` | R$ 250,00 | Não (teto R$ 180,00) | R$ 172,41 | R$ 0,00 | R$ 1.172,41 |
| 3. Acima do teto, `so_excesso_integra` (outra leitura) | R$ 250,00 | Não | R$ 172,41 | −R$ 124,14 | R$ 1.048,28 |

No caso 2 o aviso `acima_do_limite` aparece na linha da base especial e o ERP não exclui nada. No caso 3 a exclusão chega ao teto proporcional e o excesso integra. A base do regime sai de R$ 1.000,00 de alimentação mais a parcela da gorjeta, menos a exclusão. **Esta é uma leitura minha** (Q150-C1 e Q150-C3); os números acima saem do mesmo cálculo que o ERP faria.

## 3.5 Entidade nova: `Mov_Gorjeta_Repasse_Periodo`

O fato que prova uma das duas condições da exclusão da gorjeta (art. 399, § 1º, I, a): a gorjeta cobrada no mês pelo estabelecimento, o que a empresa reteve por determinação legal e o que repassou aos empregados. É conferência: o ERP registra e avisa, e a exclusão da base não depende dela (o repasse é fato de folha, não de nota). Um registro por estabelecimento e mês.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Gorjeta_Repasse` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) --- identidade | O estabelecimento que cobrou a gorjeta. |
| `Competencia` | competência --- identidade | O mês. |
| `Valor_Gorjeta_Cobrada` | número | Calculado e armazenado: soma dos itens de gorjeta das notas de saída do mês (o item cujo resultado do Motor é o componente `gorjeta_bar_restaurante`). |
| `Valor_Gorjeta_Excluida_Base` | número | Calculado e armazenado: soma das exclusões aplicadas nas linhas filhas da regra da gorjeta. Fica abaixo da cobrada quando o limite não foi cumprido. |
| `Valor_Retido_Por_Lei` | número, opcional | Informado: o que o empregador reteve por determinação legal, que o art. 399, § 1º, I, a, ressalva do repasse integral. A norma que fixa a retenção não está no Project; o contador a indica (Q150-C2). |
| `Valor_Repassado_Empregados` | número, opcional | O total repassado aos empregados no mês. |
| `Origem_Repasse` | enumeração {informado_pelo_usuario, folha}, opcional | `folha` só quando a Folha tiver rubrica de gorjeta (Q150-E3); até lá, informado. |
| `Valor_Diferenca` | número, opcional | Calculado: cobrada menos retida por lei menos repassada. Vazio enquanto faltar dado. |
| `Situacao_Repasse` | enumeração {sem_dado, conferido, divergente} | `conferido` com diferença zero; `divergente` gera aviso ao contador, nunca bloqueio. |
| `ID_Usuario_Informante` | referência (Cad_Usuario), opcional | Quem informou o repasse. |
| `Observacao` | texto, opcional | --- |


## 3.6 Mudanças em entidades existentes (bares e restaurantes)

**`Cad_Regra_Base_Calculo_Cbs`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Percentual_Limite_Exclusao` | número, opcional | O teto da exclusão, em percentual: 15 na gorjeta (art. 399, § 1º, I, b). Vazio nos componentes sem teto. |
| `Base_Do_Limite` | enumeração {fornecimento_no_regime, total_alimentacao_e_bebidas}, opcional | Sobre o que o teto se mede. Provisório na gorjeta: `total_alimentacao_e_bebidas`, a leitura literal de "valor total do fornecimento de alimentação e de bebidas" (Q150-C1). |
| `Rateia_Pela_Proporcao_Do_Regime` | booleano, opcional | Verdadeiro: só a parcela da gorjeta que cabe ao fornecimento do regime entra na conta, pela relação do § 3º (fornecimento no regime dividido pelo valor total da operação, com a gorjeta). Provisório: verdadeiro (Q150-C3). |
| `Excesso_Sobre_Limite` | enumeração {todo_valor_integra, so_excesso_integra}, opcional | O que acontece quando passa do teto. Provisório: `todo_valor_integra`, a leitura literal da condição "desde que não exceda" (Q150-C1). |
| `Exige_Repasse_Aos_Empregados` | booleano, opcional | Verdadeiro na gorjeta (art. 399, § 1º, I, a): o ERP confere `Mov_Gorjeta_Repasse_Periodo` e avisa, sem bloquear. |

**`Mov_Apuracao_Tributo_Item_Base_Especial`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Valor_Informado` | número, opcional | O valor que o documento traz do componente (a gorjeta ou o valor de plataforma), antes do limite. |
| `Valor_Limite` | número, opcional | O teto calculado pela regra (`Percentual_Limite_Exclusao` sobre a base escolhida). Vazio quando a regra não tem teto. |
| `Situacao_Limite` | enumeração {sem_limite, dentro_do_limite, acima_do_limite}, opcional | `acima_do_limite` gera aviso; o efeito na base vem de `Excesso_Sobre_Limite`. |

**`Cad_Motor_Regra_Resultado`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| Valor novo em `Tipo_Resultado` | `componente_base_calculo` | O item é um componente da base e o `Valor` do resultado é o código do componente (domínio `componente_base_calculo_ibs_cbs`). O ERP gera a linha filha de `Mov_Apuracao_Tributo_Item_Base_Especial`. |

**`Mov_Nota_Fiscal_Saida`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Indicador_Fornecimento_Sob_Contrato` | booleano, opcional | Alimentação a pessoa jurídica sob contrato, ainda que não formalizado (art. 397, I). O usuário marca; o Motor lê (critério `fornecimento_sob_contrato`). Vazio: o Motor trata como falso e avisa quando o cliente é pessoa jurídica. |


# 4. Cooperativa (LC, arts. 271 e 272; Decreto, arts. 391 a 395)

## 4.1 O que o texto pede

A cooperativa **opta** pelo regime específico (Decreto, art. 393): o pedido vale para o ano-calendário inteiro e é irretratável, feito entre 1º de setembro e 31 de outubro do ano anterior (§ 1º) ou, no início de atividade, junto do registro no cadastro, com efeito desde a data do registro (§ 3º). O pedido leva a listagem de associados com identificação e data de admissão (§ 4º); mudanças na listagem são comunicadas (§ 5º). Dentro do regime, a alíquota é **zero** quando o associado fornece à cooperativa de que participa e quando a cooperativa fornece a associado sujeito ao regime regular (art. 391, I e II); vale também entre cooperativas associadas entre si (§ 2º, I) e na venda de bem material de cooperativa de produção agropecuária a associado fora do regime regular, desde que anulados os créditos do bem (§ 2º, II; não vale nos insumos com diferimento, § 3º). Ficam de fora as operações com não associados, com associados fora do regime regular (exceto o § 2º, II), alheias aos objetivos sociais e de uso ou consumo pessoal (art. 392).

O **associado** sujeito ao regime regular pode transferir à cooperativa os créditos das operações antecedentes e os créditos presumidos (art. 394). A transferência só ocorre **depois de concluída a apuração** e fica limitada ao saldo credor (§ 1º, art. 44); entre cooperativas optantes, vai na proporção dos fornecimentos a cada uma (§ 2º); e cada cooperativa recebe, no máximo, a soma dos créditos do período (exceto os do ativo, mais a depreciação do ativo pelas taxas do Anexo I) multiplicada pela proporção dos fornecimentos à cooperativa sobre o total dos fornecimentos do associado (§ 3º). A transferência exige **documento fiscal com débito do tributo**, código de tributação específico e a expressão "Transferência de crédito de tributo nos termos do art. 394 do Regulamento da CBS" na descrição da operação (art. 395). A **LC** (art. 272, parágrafo único) acrescenta que a transferência alcança apenas os bens e serviços utilizados na produção do que o associado fornece à cooperativa; o Decreto não repete a frase (Q150-C7).

## 4.2 O que o dicionário já tem e o que falta

| Peça | Situação |
|---|---|
| `Cad_Participante_Regime_Especifico` (`sociedade_cooperativa`) | Existe. Falta o **tipo** da cooperativa, que decide o art. 391, § 2º, II (produção agropecuária) |
| `Cad_Cooperativa_Associado` | Existe (documento, admissão e saída). Falta saber se o associado **sem cadastro** é do regime regular |
| `Mov_Cooperativa_Listagem_Envio` | Existe. Falta separar a opção anual, a opção no início de atividade e a alteração da listagem (art. 393, § 5º) |
| `Cad_Taxa_Depreciacao_Cbs`, `Mov_Credito_Fiscal_Aplicacao` | Existem (taxas do Anexo I; uso do crédito) |
| Transferência de crédito | **Não existe.** Nenhuma entidade guarda o saldo credor, os dois limites, o rateio entre cooperativas e a nota do art. 395 |
| Qualificação do associado (B2, documento 116) | Existe: o associado é lido de `Cad_Participante_Qualificacao_Cbs` |
| `Mov_Apuracao_Pis_Cofins_Item` | Já tem `ID_Tipo_Cooperativa` (IND_TIP_COOP, domínio `tipo_sociedade_cooperativa`); reaproveito o domínio |

## 4.3 Entidade nova: `Mov_Cooperativa_Transferencia_Credito`

A transferência de crédito do associado à cooperativa (art. 394 do Decreto; art. 272 da LC): o limite do § 1º, o rateio entre cooperativas do § 2º, o teto do § 3º, o valor a transferir e a nota emitida (art. 395). Um registro por associado, cooperativa e mês. Mesmo padrão de `Mov_Apuracao_Tef`: calcula, fica pendente quando falta decisão e só confirma com a nota emitida. O associado é quem apura; a cooperativa recebe pela nota de entrada.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Transferencia_Credito` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | O associado sujeito ao regime regular que transfere o crédito. |
| `ID_Participante_Cooperativa` | referência (Cad_Participante) --- identidade | A cooperativa que recebe, optante do regime específico na competência (Cad_Participante_Regime_Especifico). |
| `Competencia` | competência --- identidade | O período de apuração da CBS a que o crédito se refere. |
| `Status` | enumeração {calculada, pendente_decisao, confirmada, cancelada} | `pendente_decisao` enquanto houver `Pendencia`; `confirmada` com a nota emitida. |
| `Valor_Saldo_Credor_Apuracao` | número | O saldo credor da apuração do período (art. 44), que é o teto do § 1º: lido da conta `saldo_credor_periodo_seguinte` de `Mov_Cbs_Apuracao_Espelho_Conta` (domínio `conta_apuracao_cbs`). A transferência só ocorre depois de concluída a apuração (`Mov_Cbs_Apuracao_Espelho.Situacao_Periodo = concluida`). |
| `Valor_Creditos_Exceto_Ativo` | número | § 3º, I, a: o total de créditos apropriados no período, inclusive os presumidos, menos os do ativo imobilizado. Leitura provisória do Decreto: todos os créditos do período; a restrição do art. 272, parágrafo único, da LC (só os insumos do que foi fornecido à cooperativa) espera o contador (Q150-C7). |
| `Valor_Creditos_Depreciacao_Ativo` | número | § 3º, I, b: a parte dos créditos de bens do ativo correspondente à depreciação do período, pela vida útil e pelas taxas de `Cad_Taxa_Depreciacao_Cbs` (Anexo I). |
| `Valor_Fornecimentos_A_Cooperativa` | número | § 3º, II, a: o que o associado forneceu a esta cooperativa no período, com a redução de alíquota do art. 391, I. |
| `Valor_Fornecimentos_Total_Associado` | número | § 3º, II, b: todos os fornecimentos do associado no período, inclusive os sem a redução. |
| `Valor_Fornecimentos_Cooperativas_Optantes` | número | § 2º: o que o associado forneceu ao conjunto das cooperativas optantes de que participa, no período. |
| `Percentual_Rateio_Cooperativas` | número (7,4) | § 2º: fornecimentos a esta cooperativa divididos pelos fornecimentos ao conjunto das optantes. Igual a 100 quando o associado é de uma cooperativa só. |
| `Percentual_Proporcao_Fornecimento` | número (7,4) | § 3º, II: fornecimentos a esta cooperativa divididos pelos fornecimentos totais do associado. |
| `Limite_Pelo_Rateio` | número | Saldo credor vezes o percentual de rateio (§§ 1º e 2º). |
| `Limite_Pela_Proporcao` | número | Soma dos créditos do § 3º, I, vezes a proporção do § 3º, II. |
| `Valor_A_Transferir` | número | O menor dos dois limites; zero se o saldo credor não é positivo. |
| `Valor_Transferido` | número, opcional | O que o associado decidiu transferir (o art. 394 diz "poderá transferir"); não passa de `Valor_A_Transferir` (aviso). |
| `ID_Nota_Fiscal_Saida` | referência (Mov_Nota_Fiscal_Saida), opcional | A nota com débito do tributo, código de tributação específico e a expressão do art. 395 na descrição da operação. |
| `Pendencia` | enumeração {nenhuma, apuracao_nao_concluida, saldo_nao_apurado, cooperativa_sem_opcao, associado_sem_qualificacao} | O que impede a confirmação. A apuração só confirma com `nenhuma`. |
| `ID_Usuario_Confirmacao` | referência (Cad_Usuario), opcional | Quem confirmou (padrão da Fase 0). |
| `Data_Hora_Confirmacao` | data/hora, opcional | Quando confirmou. |

**Pendências.** `apuracao_nao_concluida` (o § 1º só deixa transferir depois da apuração), `saldo_nao_apurado` (não há saldo credor do art. 44 para o período), `cooperativa_sem_opcao` (a cooperativa não é optante na competência) e `associado_sem_qualificacao` (o associado não é do regime regular pela qualificação do B2). O ERP avisa e deixa a transferência em `pendente_decisao`.

## 4.4 Exemplo calculado

Associado de duas cooperativas optantes (A e B) com saldo credor apurado de R$ 10.000,00; créditos do período exceto os do ativo de R$ 30.000,00 e depreciação do ativo de R$ 2.000,00; fornecimentos de R$ 60.000,00 à A, R$ 20.000,00 à B e R$ 100.000,00 no total (R$ 20.000,00 a quem não é cooperativa).

| Cooperativa | Rateio do § 2º | Limite pelo rateio (saldo × rateio) | Proporção do § 3º, II | Limite pela proporção (R$ 32.000,00 × proporção) | **A transferir** (o menor) |
|---|---|---|---|---|---|
| A | 75,00% | R$ 7.500,00 | 60,00% | R$ 19.200,00 | **R$ 7.500,00** |
| B | 25,00% | R$ 2.500,00 | 20,00% | R$ 6.400,00 | **R$ 2.500,00** |

Com o mesmo associado e **saldo credor de R$ 40.000,00**, o limite pelo rateio sobe (A: R$ 30.000,00; B: R$ 10.000,00) e passa a valer o do § 3º: **A: R$ 19.200,00; B: R$ 6.400,00**. O teto do § 3º é sempre calculado; o do rateio é o que decide quando o saldo credor é pequeno.

## 4.5 Mudanças em entidades existentes (cooperativa)

**`Cad_Participante_Regime_Especifico`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `ID_Tipo_Cooperativa` | referência (Cad_Classe_Sistema, domínio = tipo_sociedade_cooperativa), opcional | Só quando `Tipo_Regime_Especifico` é `sociedade_cooperativa`. O mesmo domínio do IND_TIP_COOP da EFD-Contribuições: `01` (produção agropecuária) liga o regime do art. 391, § 2º, II. |

**`Cad_Cooperativa_Associado`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Sujeito_Regime_Regular_Cbs` | booleano, opcional | Só quando `ID_Participante_Associado` está vazio (o associado tem só o documento): informado pelo usuário. Com participante cadastrado, vale o `Indicador_Contribuinte_Cbs` da qualificação (B2). |

**`Mov_Cooperativa_Listagem_Envio`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Tipo_Envio` | enumeração {opcao, alteracao_da_listagem} | `alteracao_da_listagem` é a comunicação do art. 393, § 5º. |
| `Tipo_Opcao` | enumeração {periodo_anual, inicio_de_atividade}, opcional | Só em `opcao`: no período de 1º/09 a 31/10 ou simultânea ao registro (art. 393, §§ 1º e 3º). |
| `Data_Inicio_Efeito` | data, opcional | Só no início de atividade: a data do registro, a partir da qual a opção produz efeito. Nos demais, vale `Ano_Efeito`. |

**`Mov_Credito_Fiscal_Aplicacao`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `ID_Transferencia_Credito` | referência (Mov_Cooperativa_Transferencia_Credito), opcional | A transferência que consumiu o crédito, só com `Forma_Utilizacao = transferencia_cooperativa`. |
| Valor novo em `Forma_Utilizacao` | `transferencia_cooperativa` | O crédito do associado usado na transferência do art. 394. |



# 5. Locação por temporada (LC, art. 253; Decreto, art. 410)

## 5.1 O que o texto pede

A locação, a cessão onerosa ou o arrendamento de **imóvel residencial**, por contribuinte do regime regular, **por período não superior a noventa dias ininterruptos**, segue as mesmas regras dos serviços de hotelaria (Decreto, art. 410; LC, art. 253): redução de 40% e crédito vedado ao adquirente (Decreto, arts. 405 e 407). A pessoa física é contribuinte do regime regular quando atende ao art. 382 (§ 1º), e o fornecedor emite o documento fiscal quando identificada a condição (§ 2º). A LC 227 mexeu nos §§ 1º e 2º do art. 253; o § 2º põe a locação de temporada na receita e na contagem de imóveis dos limites da pessoa física.

## 5.2 O que o dicionário já tem e o que falta

`Mov_Locacao_Faturamento` guarda a locação de longo prazo, uma linha por mês de faturamento, sem data de entrada e saída. `Mov_Locacao_Limite_Pf` apura os limites da pessoa física (art. 382). `Cad_Imovel` tem `Uso_Imovel` {residencial, nao_residencial}. **Faltam**: a ocupação por período (início, fim e dias ininterruptos), o parâmetro dos 90 dias, a ligação da prorrogação com a ocupação anterior e a marca de enquadramento que o Motor lê.

## 5.3 Desenho

Duas entidades: o parâmetro (`Cad_Locacao_Temporada_Regra`, uma linha, com vigência) e o fato (`Mov_Locacao_Temporada`). O **enquadramento** (`Enquadra_Hotelaria`) é calculado: dias não maiores que o máximo, imóvel residencial e locador do regime regular. O Motor lê a marca pelo critério novo `ocupacao_ininterrupta_ate_90_dias` e escolhe o cClassTrib da hotelaria; o ERP não escreve a redução. Sem a marca, vale o regime geral da locação.

**Contagem dos dias.** O texto não diz como se conta. A carga provisória usa `dias_corridos_inclusivos`: de 1º/01 a 31/03 são 90 dias; de 1º/01 a 1º/04, 91. A prorrogação sem interrupção soma: uma ocupação de 1º/01 a 20/02 (51 dias) prorrogada de 21/02 a 31/03 (39 dias) soma 90 e **enquadra**; a de 1º/01 a 1º/04 (91 dias) **não enquadra**. O contador decide a contagem (Q150-C9).

## 5.4 Entidade nova: `Cad_Locacao_Temporada_Regra`

O parâmetro do art. 410 e do art. 253 da LC: o máximo de dias, como contar e o que a locação de temporada segue. Uma linha; mudar o prazo ou o critério é versão nova.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Locacao_Temporada_Regra` | identificador | --- |
| `ID_Locacao_Temporada_Regra_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Locacao_Temporada_Regra_Versao). ID_Locacao_Temporada_Regra é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `Codigo_Regra` | código (até 30) --- identidade | `LOCACAO-TEMPORADA-RESIDENCIAL`. |
| `Dias_Maximo_Ocupacao` | número | 90 (art. 410: "período não superior a noventa dias ininterruptos"). |
| `Criterio_Contagem` | enumeração {dias_corridos_inclusivos, noites} | Provisório: `dias_corridos_inclusivos` (de 1º/01 a 31/03 são 90). O texto não diz como contar (Q150-C9). |
| `Equipara_Hotelaria` | booleano | Verdadeiro: a locação dentro do prazo segue as regras dos serviços de hotelaria (redução de 40%, crédito vedado ao adquirente), lidas pelo Motor. |
| `Conta_Nos_Limites_Pessoa_Fisica` | booleano | Verdadeiro: a locação de temporada entra na receita e na contagem de imóveis dos limites da pessoa física (LC, art. 253, § 2º, incluído pela LC 227). |
| `Fundamento_Legal` | texto | LC 253 e Decreto 410. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 5.5 Entidade nova: `Mov_Locacao_Temporada`

Uma ocupação de imóvel residencial por período curto (art. 410 do Decreto; art. 253 da LC): quem aluga, o imóvel, as datas, os dias de ocupação ininterrupta e o enquadramento nas regras de hotelaria. O dicionário só tinha a locação de longo prazo (`Mov_Locacao_Faturamento`, mensal), sem data de entrada e saída.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Locacao_Temporada` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) | O locador, emitente da nota. |
| `ID_Imovel` | referência (Cad_Imovel) | O imóvel; `Uso_Imovel` residencial (aviso se não for). |
| `ID_Participante_Locatario` | referência (Cad_Participante), opcional | O hóspede ou locatário, quando identificado. |
| `ID_Contrato` | referência (Cad_Gestao_Contrato), opcional | O contrato ou a reserva, quando existe no sistema. |
| `Data_Inicio` | data | O primeiro dia da ocupação. |
| `Data_Fim` | data | O último dia da ocupação. |
| `ID_Ocupacao_Anterior` | referência (Mov_Locacao_Temporada), opcional | A ocupação que esta prorroga sem interrupção, para somar os dias do art. 410 ("ininterruptos"). |
| `Dias_Ocupacao_Ininterrupta` | número | Calculado: os dias desta ocupação mais os das anteriores ligadas, pelo critério de contagem da regra vigente. |
| `ID_Locacao_Temporada_Regra` | referência (Cad_Locacao_Temporada_Regra) | A regra e a versão vigentes na data de início. |
| `Enquadra_Hotelaria` | booleano | Calculado: os dias não passam do máximo da regra, o imóvel é residencial e o locador é do regime regular. Lido pelo Motor (critério `ocupacao_ininterrupta_ate_90_dias`). |
| `Locador_Regime_Regular` | booleano, opcional | Pessoa jurídica: verdadeiro. Pessoa física: pelo resultado de `Mov_Locacao_Limite_Pf` (art. 382). Vazio enquanto não apurado: aviso. |
| `Valor_Total` | número | O valor cobrado pela ocupação. |
| `ID_Nota_Fiscal_Saida` | referência (Mov_Nota_Fiscal_Saida), opcional | A nota emitida. |
| `Status` | enumeração {prevista, em_curso, encerrada, cancelada} | --- |

## 5.6 Mudança em entidade existente

**`Mov_Locacao_Limite_Pf`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Receita_Locacao` | texto | Passa a dizer que inclui a locação de temporada (LC, art. 253, § 2º, e Decreto, art. 410, § 1º); sem campo novo. |

A locação de temporada entra na receita e na contagem de imóveis dos limites da pessoa física pela marca `Conta_Nos_Limites_Pessoa_Fisica` da regra; `Mov_Locacao_Limite_Pf` lê as ocupações encerradas do ano, sem campo novo.

# 6. Agência de turismo (LC, arts. 288 a 291; Decreto, arts. 417 a 420)

## 6.1 O que o texto pede

O serviço da agência é de dois tipos (Decreto, art. 417, § 1º): a **intermediação remunerada** entre prestadores e usuários (passagens, reservas, roteiros, ingressos, excursões, seguros de viagem; § 2º) e o **fornecimento direto** de serviços turísticos. Na intermediação a base é o valor da operação **menos** o que a agência repassa aos fornecedores intermediados; no fornecimento direto, é o valor da operação, sem dedução (art. 418, I e II). O valor da operação inclui o total cobrado do usuário, com a margem e outros acréscimos, e as comissões e incentivos pagos por terceiros (§ 1º). A dedução exige coincidência de valor com o documento do fornecedor, que referencia o da agência, e a conversão da moeda estrangeira pela taxa de fechamento do dia anterior (§ 2º). O adquirente toma crédito da intermediação (art. 419) e a agência toma crédito das aquisições, **menos** o que deduziu da base (art. 420).

## 6.2 O que o dicionário já tem e o que falta

`Mov_Agencia_Turismo_Repasse` já confere o repasse (valor, câmbio, referência do documento) e entrega o `Valor_Deduzido`. **Falta saber, no item da nota, se ele é intermediação ou fornecimento direto**, para que a dedução só valha na intermediação. A Q94-4 perguntou onde esse tipo fica; você respondeu "entra no cadastro" (D-N389) e a pergunta ficou em aberto só quanto a qual cadastro. A leitura que adoto: **no cadastro do produto ou serviço** (`Cad_Produto_Servico`), copiado para o item da nota na emissão e editável. Um pacote que mistura os dois tipos vira dois itens na nota, um de cada tipo (Q150-C10).

**Modelo de relação com a agência ou plataforma (Q148-15, D-N426).** O hotel, o parque ou o prestador se relaciona com cada agência ou plataforma de um de três modos, que você descreveu na Q148-11: **comissão** (o prestador emite a nota ao cliente e a agência emite ao prestador a nota de serviço de intermediação), **repasse ou revenda** (o prestador emite a nota contra a agência, que agrega o seu valor e emite ao consumidor) e **taxa de serviço própria** (receita da agência, sem dedução e sem relação com a nota do prestador). Só o repasse conversa com `Mov_Agencia_Turismo_Repasse`. O modelo é cadastro por participante, com vigência: `Cad_Participante_Modelo_Intermediacao` (seção 6.3), lendo o domínio aberto `modelo_intermediacao` com três valores.

## 6.3 Entidade nova: `Cad_Participante_Modelo_Intermediacao`

Como o prestador se relaciona com cada agência, plataforma ou revendedor que vende o seu serviço (comissão, repasse ou taxa de serviço própria). Resposta à Q148-15 (D-N426): é cadastro, com vigência, e o Motor lê o modelo para decidir quem emite a nota e se há dedução.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Modelo_Intermediacao` | identificador | --- |
| `ID_Participante_Modelo_Intermediacao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Participante_Modelo_Intermediacao_Versao). ID_Participante_Modelo_Intermediacao é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | O prestador (o hotel, por exemplo). |
| `ID_Participante_Intermediario` | referência (Cad_Participante) --- identidade | A agência, a plataforma ou o revendedor. |
| `ID_Modelo_Intermediacao` | referência (Cad_Classe_Sistema, domínio = modelo_intermediacao) | `comissao`, `repasse_revenda` ou `taxa_servico_propria` (carga de 3 valores, seção 7.3). |
| `ID_Contrato` | referência (Cad_Gestao_Contrato), opcional | O contrato que sustenta o modelo, quando existe. |
| `Observacao` | texto, opcional | --- |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 6.4 Mudanças em entidades existentes (agência de turismo)

**`Cad_Produto_Servico`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Tipo_Servico_Agencia` | enumeração {intermediacao, fornecimento_direto}, opcional | Só nos serviços de agência de turismo. Resposta à Q94-4 (D-N389): o campo entra no cadastro, não no repasse. |

**`Mov_Nota_Fiscal_Saida_Item`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `Tipo_Servico_Agencia` | enumeração {intermediacao, fornecimento_direto}, opcional | Copiado do cadastro na emissão e editável: o serviço da agência de turismo (art. 417, § 1º). Decide a base: com a dedução do art. 418, I, ou sem dedução (art. 418, II). |

**Exemplo.** Pacote de R$ 10.000,00 com hospedagem repassada de R$ 6.000,00 e passagem aérea repassada de R$ 2.500,00, ambas conferidas em `Mov_Agencia_Turismo_Repasse`. Item `intermediacao`: base = 10.000,00 − 6.000,00 − 2.500,00 = **R$ 1.500,00**, e a agência não toma crédito dos R$ 8.500,00 deduzidos (art. 420). Se o mesmo valor fosse `fornecimento_direto` (a agência presta o serviço), a base seria **R$ 10.000,00**, sem dedução.

# 7. Motor de Regras e domínios

O Motor de Regras (`Cad_Motor_Regra`, `_Criterio` e `_Resultado`) decide o cClassTrib; os regimes deste documento só pedem **nove critérios novos** e **um tipo de resultado novo**. Nenhum código de classificação tributária é criado aqui: as regras são cadastro do usuário e do contador, com a carga provisória marcada e validada pelo contador (Fase 0, seção 9).

| Valor novo em `campo_criterio_regra` | O que lê |
|---|---|
| `cnae_do_emitente` | O CNAE do emitente na data da operação (art. 397, I: 5620-1/01). |
| `tipo_pessoa_do_destinatario` | Pessoa jurídica ou física (art. 397, I: alimentação a pessoa jurídica sob contrato). |
| `fornecimento_sob_contrato` | A marca `Indicador_Fornecimento_Sob_Contrato` da nota (art. 397, I). |
| `associado_da_cooperativa` | O participante consta em `Cad_Cooperativa_Associado` na data, com a cooperativa optante (art. 391, I e II). |
| `regime_especifico_do_emitente` | O emitente tem `Cad_Participante_Regime_Especifico` vigente (por exemplo, `sociedade_cooperativa`). |
| `regime_especifico_do_destinatario` | O destinatário tem regime específico vigente (por exemplo, o associado que compra da cooperativa). |
| `ocupacao_ininterrupta_ate_90_dias` | A marca `Enquadra_Hotelaria` da locação de temporada (art. 410). |
| `modelo_intermediacao_do_participante` | O modelo vigente em `Cad_Participante_Modelo_Intermediacao` (comissão, repasse ou taxa de serviço própria). |
| `tipo_servico_agencia` | O `Tipo_Servico_Agencia` do item (intermediação ou fornecimento direto; art. 417, § 1º). |

O resultado novo `componente_base_calculo` (em `Cad_Motor_Regra_Resultado.Tipo_Resultado`, seção 3.6) existe porque a gorjeta e o valor da plataforma não escolhem código de tributação: escolhem **o componente da base** a que pertencem. O `Valor` do resultado é o código do componente.

**Domínios novos em `Cad_Classe_Sistema`:** `modelo_intermediacao` (3 valores: `comissao`, `repasse_revenda`, `taxa_servico_propria`) e dois valores novos em `componente_base_calculo_ibs_cbs` (`gorjeta_bar_restaurante` e `intermediacao_plataforma_pedido`). O domínio `tipo_sociedade_cooperativa` já existe (documento da EFD-Contribuições).


# 8. O que entra no próximo "consolidar"

**5 entidades novas (71 campos)**, todas na Contabilidade & Fiscal.

| Entidade | Tipo | Campos | Vigência | Capítulo |
|---|---|---|---|---|
| `Mov_Gorjeta_Repasse_Periodo` | conferência mensal da gorjeta | 12 | não | 3 |
| `Mov_Cooperativa_Transferencia_Credito` | transferência de crédito do associado | 21 | não | 4 |
| `Mov_Locacao_Temporada` | ocupação por período | 15 | não | 5 |
| `Cad_Locacao_Temporada_Regra` | parâmetro (1 linha) | 13 | sim | 5 |
| `Cad_Participante_Modelo_Intermediacao` | cadastro por agência ou plataforma (carga vazia) | 10 | sim | 6 |

**11 entidades alteradas** (17 campos novos; as demais mudanças são valores de enumeração ou texto).

| Entidade | O que muda |
|---|---|
| `Cad_Regra_Base_Calculo_Cbs` | 5 colunas de limite (`Percentual_Limite_Exclusao`, `Base_Do_Limite`, `Rateia_Pela_Proporcao_Do_Regime`, `Excesso_Sobre_Limite`, `Exige_Repasse_Aos_Empregados`); 2 linhas de carga |
| `Mov_Apuracao_Tributo_Item_Base_Especial` | `Valor_Informado`, `Valor_Limite`, `Situacao_Limite` |
| `Cad_Motor_Regra_Resultado` | `Tipo_Resultado` + `componente_base_calculo` |
| `Mov_Nota_Fiscal_Saida` | `Indicador_Fornecimento_Sob_Contrato` |
| `Mov_Nota_Fiscal_Saida_Item` | `Tipo_Servico_Agencia` |
| `Cad_Produto_Servico` | `Tipo_Servico_Agencia` |
| `Cad_Participante_Regime_Especifico` | `ID_Tipo_Cooperativa` |
| `Cad_Cooperativa_Associado` | `Sujeito_Regime_Regular_Cbs` |
| `Mov_Cooperativa_Listagem_Envio` | `Tipo_Envio`, `Tipo_Opcao`, `Data_Inicio_Efeito` |
| `Mov_Credito_Fiscal_Aplicacao` | `ID_Transferencia_Credito`; `Forma_Utilizacao` + `transferencia_cooperativa` |
| `Mov_Locacao_Limite_Pf` | só o texto de `Receita_Locacao` |

**Domínios e valores novos.**

| Onde | O que entra |
|---|---|
| `Cad_Classe_Sistema.Dominio` | `modelo_intermediacao` (3 valores: comissao, repasse_revenda, taxa_servico_propria) |
| `componente_base_calculo_ibs_cbs` | 2 valores: `gorjeta_bar_restaurante` e `intermediacao_plataforma_pedido` |
| `campo_criterio_regra` | 9 valores: `cnae_do_emitente`, `tipo_pessoa_do_destinatario`, `fornecimento_sob_contrato`, `associado_da_cooperativa`, `regime_especifico_do_emitente`, `regime_especifico_do_destinatario`, `ocupacao_ininterrupta_ate_90_dias`, `modelo_intermediacao_do_participante`, `tipo_servico_agencia` |

**Cargas provisórias** (todas com `Situacao_Dado = provisorio` até o contador validar; seção 11, Anexo A):

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Regra_Base_Calculo_Cbs` | 2 novas | Gorjeta (exclui, teto de 15%, rateio pelo § 3º, `todo_valor_integra`, exige repasse e segregação) e valor de plataforma (exclui, sem teto, exige segregação). `Origem_Regra`: `lei` no teto e nas exclusões; `decreto` na segregação e no rateio |
| `Cad_Locacao_Temporada_Regra` | 1 | `LOCACAO-TEMPORADA-RESIDENCIAL`, 90 dias, `dias_corridos_inclusivos`, equipara à hotelaria e conta nos limites da pessoa física |
| `Cad_Classe_Sistema` (`modelo_intermediacao`) | 3 | comissão, repasse ou revenda, taxa de serviço própria |
| `Cad_Classe_Sistema` (`componente_base_calculo_ibs_cbs`) | 2 | gorjeta e valor de plataforma |
| `Cad_Classe_Sistema` (`campo_criterio_regra`) | 9 | Os critérios da seção 7 |
| `Cad_Participante_Modelo_Intermediacao` | 0 | Cadastro do usuário, por agência ou plataforma |

**Textos que a consolidação corrige:** `Mov_Locacao_Limite_Pf.Receita_Locacao` passa a dizer que inclui a locação de temporada (LC, art. 253, § 2º; Decreto, art. 410, § 1º). **Nada deste documento mexe** no TEF, na hotelaria já consolidada (revisão 27) nem em `Cad_Aliquota_Combustivel` (Q150-11).

# 9. Perguntas

## 9.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q150-1** | Bares e restaurantes: cinco colunas de limite em `Cad_Regra_Base_Calculo_Cbs`, três em `Mov_Apuracao_Tributo_Item_Base_Especial`, dois componentes novos e o resultado `componente_base_calculo` no Motor? | Sim |
| **Q150-2** | `Mov_Gorjeta_Repasse_Periodo` como conferência mensal por estabelecimento, que avisa e não bloqueia, com a origem `folha` só quando a Folha tiver rubrica de gorjeta? | Sim |
| **Q150-3** | Fornecimento a pessoa jurídica sob contrato (art. 397, I): `Indicador_Fornecimento_Sob_Contrato` na nota e os critérios `cnae_do_emitente`, `tipo_pessoa_do_destinatario` e `fornecimento_sob_contrato` no Motor? | Sim |
| **Q150-4** | Cooperativa: `Mov_Cooperativa_Transferencia_Credito` com os dois limites, o rateio entre cooperativas e a nota do art. 395, mais `transferencia_cooperativa` e `ID_Transferencia_Credito` no uso do crédito? | Sim |
| **Q150-5** | Cooperativa, cadastro: `ID_Tipo_Cooperativa` no regime específico, `Sujeito_Regime_Regular_Cbs` no associado sem cadastro e `Tipo_Envio`, `Tipo_Opcao` e `Data_Inicio_Efeito` na listagem? | Sim |
| **Q150-6** | Locação por temporada: `Cad_Locacao_Temporada_Regra` (90 dias, parâmetro com vigência) e `Mov_Locacao_Temporada`, e o texto de `Mov_Locacao_Limite_Pf` passa a dizer que a temporada entra nos limites da pessoa física? | Sim |
| **Q150-7** | Q94-4: o `Tipo_Servico_Agencia` fica no **cadastro do produto ou serviço**, copiado para o item da nota na emissão e editável? | Sim |
| **Q150-8** | Q148-15: o modelo de relação com a agência ou plataforma é `Cad_Participante_Modelo_Intermediacao` (por participante, com vigência) mais o domínio `modelo_intermediacao` de três valores? | Sim |
| **Q150-9** | Motor: os nove critérios novos da seção 7 e nenhum código de classificação tributária criado neste documento? | Sim |
| **Q150-10** | A leitura provisória da gorjeta (teto de 15% sobre o total de alimentação e bebidas do documento, parcela pelo § 3º, todo o valor integra se passa do teto) vai como carga provisória até o contador responder? | Sim |
| **Q150-11** | `Cad_Aliquota_Combustivel` (Q140-7) não pertence ao B5 de regimes setoriais (é monofásico); sai da espera do B5 e vira desenho próprio, quando você quiser, na fila? | Sim |
| **Q150-12** | Aplico tudo no próximo "consolidar", junto com o documento 157? | Sim |

## 9.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q150-C1** | Teto de 15% da gorjeta (LC, art. 274, parágrafo único, I, b; Decreto, art. 399, § 1º, I, b): (a) sobre quê se mede (o total do fornecimento de alimentação e bebidas do documento, só o do regime ou o valor total da operação com a gorjeta)? (b) passando do teto, **toda** a gorjeta integra a base ou só o excesso? | (a) total de alimentação e bebidas do documento; (b) todo o valor integra |
| **Q150-C2** | "Valores da gorjeta retidos pelo empregador em virtude de determinação legal" (art. 399, § 1º, I, a): qual norma fixa a retenção e como se comprova? | `Valor_Retido_Por_Lei` informado, sem norma na carga |
| **Q150-C3** | Rateio do § 3º: o percentual se calcula com o **valor total da operação com a gorjeta** no denominador? E a parcela da gorjeta do regime sai da base inteira ou só até o teto? | Denominador com a gorjeta; parcela inteira se dentro do teto |
| **Q150-C4** | A exclusão vale também para a gorjeta de **bebida** do regime, ou só para a de alimentação (a lei diz "gorjeta incidente no fornecimento de alimentação")? | Gorjeta de qualquer item do regime |
| **Q150-C5** | Valores da plataforma (art. 399, § 1º, II): é o que a plataforma retém do restaurante (taxa de entrega e de intermediação)? Quem os segrega no documento do restaurante e como o restaurante os conhece? | Item próprio do documento, informado pelo usuário |
| **Q150-C6** | "Sob contrato, ainda que não formalizado" (art. 397, I): que prova basta (fornecimento recorrente, pedido corporativo, convênio de vale-refeição)? E a pessoa jurídica que come uma vez no restaurante sem contrato fica no regime? | Marca informada pelo usuário; sem contrato, regime específico |
| **Q150-C7** | Cooperativa: (a) a restrição do art. 272, parágrafo único, da LC (só os bens e serviços usados na produção do que o associado fornece à cooperativa) vale além dos limites do art. 394 do Decreto? Como se separa esse crédito? (b) créditos de períodos anteriores e o saldo credor acumulado entram nos limites? (c) o crédito do ativo é a depreciação do mês pelas taxas do Anexo I? | (a) só os limites do Decreto; (b) só os do período; (c) taxa do Anexo I dividida por 12 |
| **Q150-C8** | Transferência de crédito da cooperativa: o valor transferido reduz o saldo credor que o associado leva ao período seguinte? A nota do art. 395 tem a mesma alíquota da operação ou outra? | Reduz o saldo; débito pelo valor transferido |
| **Q150-C9** | Locação por temporada: (a) como se contam os 90 dias (dias corridos inclusivos ou noites)? (b) novo contrato com o mesmo locatário logo depois do primeiro soma os dias? (c) pessoa física que ultrapassa o limite do art. 382 no meio do ano: as ocupações anteriores mudam? | (a) dias corridos inclusivos; (b) soma só se declarado como prorrogação; (c) vale a situação na data de início |
| **Q150-C10** | Agência de turismo: pacote com serviços de intermediação e de fornecimento direto na mesma venda: dois itens, um de cada tipo, com a margem de agregação distribuída? Como a margem entra na dedução? | Dois itens; margem no item de intermediação |

## 9.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q150-E1** | A Folha terá rubrica de gorjeta repassada ao empregado, para a origem `folha` da conferência (`Mov_Gorjeta_Repasse_Periodo`)? Até lá o repasse é informado. |
| **Q150-E2** | O PDV de bares e restaurantes consegue lançar gorjeta e valor de plataforma como itens próprios da nota (a segregação do art. 399, § 2º)? |
| **Q150-E3** | Há sistema de reservas ou de hospedagem que entregue início e fim da ocupação à locação por temporada, ou o cadastro será feito no ERP? |
| **Q150-E4** | O total de fornecimentos do associado à cooperativa sai da apuração por cClassTrib da nota; confirmar que as notas à cooperativa carregam o cClassTrib da redução do art. 391, I. |
| **Q150-E5** | A conferência da transferência de crédito lê o saldo credor da conta `saldo_credor_periodo_seguinte` do espelho da apuração (`Mov_Cbs_Apuracao_Espelho_Conta`) e a situação `concluida` do período: confirmar que essa conta é o saldo credor do art. 44 e que ela fica disponível quando o período conclui. |
| **Q150-E6** | Agência de turismo (Decreto, art. 420): o cálculo do crédito da agência já deixa de fora o valor que ela deduziu da base (`Valor_Deduzido` em `Mov_Agencia_Turismo_Repasse`), ou precisa de regra? |

# 10. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **Não crio código de classificação tributária.** O cClassTrib da cooperativa (200054, IT 2025.002) e os da hotelaria e de bares e restaurantes são cadastro do Motor, validado pelo contador.
3. **Os documentos do restaurante, da cooperativa e da agência continuam sendo emitidos pelo mesmo modelo de nota de saída.** Não há documento fiscal novo.
4. **Os valores de gorjeta, plataforma e repasse são informados.** O ERP de vendas não os deriva; a conferência avisa.
5. **O produtor rural e o limite dele** (B5-rural, documento 116) **ficam fora**: dependem do B2 e de documento próprio.
6. **Q140-7 (`Cad_Aliquota_Combustivel`)** continua pendente (Q150-11).
7. **As leituras minhas** (teto da gorjeta, rateio do § 3º, contagem dos 90 dias, local do tipo de serviço da agência) estão marcadas e vão ao contador; nenhuma vira regra no código.


# Anexo A. Carga provisória (todas com `Situacao_Dado = provisorio`)

## A.1 `Cad_Regra_Base_Calculo_Cbs`: 2 linhas novas

| Campo | Gorjeta | Valor da plataforma |
|---|---|---|
| `ID_Componente_Base` | `gorjeta_bar_restaurante` | `intermediacao_plataforma_pedido` |
| `Efeito_Na_Base` | `exclui` | `exclui` |
| `Percentual_Limite_Exclusao` | 15 | vazio |
| `Base_Do_Limite` | `total_alimentacao_e_bebidas` | vazio |
| `Rateia_Pela_Proporcao_Do_Regime` | verdadeiro | verdadeiro |
| `Excesso_Sobre_Limite` | `todo_valor_integra` | vazio |
| `Exige_Repasse_Aos_Empregados` | verdadeiro | falso |
| `Exige_Constar_No_Documento_Fiscal` | verdadeiro (art. 399, § 2º) | verdadeiro (art. 399, § 2º) |
| `Exige_Sem_Evento_Posterior` | falso | falso |
| `Aplica_Ibs` / `Aplica_Cbs` | verdadeiro / verdadeiro (LC, art. 274: "IBS e CBS") | verdadeiro / verdadeiro |
| `Origem_Regra` | `lei` (exclusão e teto); `decreto` na segregação e no rateio | `lei` (exclusão); `decreto` na segregação |
| `Fundamento_Legal` | LC, art. 274, parágrafo único, I; Decreto, art. 399, § 1º, I, e §§ 2º a 4º | LC, art. 274, parágrafo único, II; Decreto, art. 399, § 1º, II |
| `Vigencia_Inicio` / `Vigencia_Fim` | 01/01/2027 / 31/12/9999 (Q150-C1: o contador confirma o início) | idem |

## A.2 `Cad_Locacao_Temporada_Regra`: 1 linha

`Codigo_Regra` `LOCACAO-TEMPORADA-RESIDENCIAL`; `Dias_Maximo_Ocupacao` 90; `Criterio_Contagem` `dias_corridos_inclusivos`; `Equipara_Hotelaria` verdadeiro; `Conta_Nos_Limites_Pessoa_Fisica` verdadeiro; `Fundamento_Legal` "LC, art. 253 (com os §§ 1º e 2º da LC 227); Decreto, art. 410"; vigência 01/01/2027 a 31/12/9999.

## A.3 `Cad_Classe_Sistema`

`modelo_intermediacao`: `comissao` (Comissão), `repasse_revenda` (Repasse ou revenda), `taxa_servico_propria` (Taxa de serviço própria). `componente_base_calculo_ibs_cbs`: `gorjeta_bar_restaurante`, `intermediacao_plataforma_pedido`. `campo_criterio_regra`: os nove da seção 7.

# Anexo B. Cobertura dispositivo por dispositivo

| Dispositivo | Assunto | Onde está |
|---|---|---|
| LC, arts. 271 e Decreto, art. 391 | Opção e alíquota zero da cooperativa | `Cad_Participante_Regime_Especifico` (+ `ID_Tipo_Cooperativa`); cClassTrib pelo Motor (critérios `associado_da_cooperativa` e `regime_especifico_*`) |
| Decreto, art. 392 | Operações fora do regime | Motor (critérios acima); associado fora do regime regular: `Sujeito_Regime_Regular_Cbs` |
| Decreto, art. 393 | Opção, prazo, listagem | `Mov_Cooperativa_Listagem_Envio` (+ `Tipo_Envio`, `Tipo_Opcao`, `Data_Inicio_Efeito`) e `Cad_Cooperativa_Associado` |
| LC, art. 272 e Decreto, art. 394 | Transferência de crédito | `Mov_Cooperativa_Transferencia_Credito` (os §§ 1º a 3º); a restrição do parágrafo único da LC espera o contador (Q150-C7) |
| Decreto, art. 395 | Nota da transferência | `ID_Nota_Fiscal_Saida` da transferência; expressão na descrição da operação (texto do documento fiscal) |
| LC, art. 273 e Decreto, arts. 396 e 397 | Escopo e exclusões do regime | Motor (NBS, CNAE do emitente, destinatário, marca de contrato) |
| Decreto, art. 398 | Segregação | Já existe: o item sem regra cai no regime geral com aviso (D-N427) |
| LC, art. 274 e Decreto, art. 399 | Base, gorjeta, plataforma | Regra da base especial e linhas por item (capítulo 3); `Mov_Gorjeta_Repasse_Periodo` |
| LC, art. 275 e Decreto, art. 400 | Redução de 40% | `Cad_Cclasstrib` (percentual), escolhido pelo Motor |
| LC, art. 276 e Decreto, art. 401 | Crédito vedado ao adquirente | `Credito_Vedado_Adquirente` (revisão 27) |
| LC, art. 253 e Decreto, art. 410 | Locação por até 90 dias | `Cad_Locacao_Temporada_Regra`, `Mov_Locacao_Temporada`, critério do Motor |
| LC, arts. 288 e Decreto, art. 417 | Agência: tipos de serviço | `Tipo_Servico_Agencia` no produto e no item |
| LC, art. 289 e Decreto, art. 418 | Base e dedução | `Mov_Agencia_Turismo_Repasse` (já existe) e o tipo do item |
| LC, art. 290 e Decreto, art. 419 | Crédito do adquirente | Sem campo novo: o adquirente toma o crédito da intermediação; o cClassTrib e `Credito_Vedado_Adquirente` vêm do Motor |
| LC, art. 291 e Decreto, art. 420 | Crédito da agência, menos o deduzido | Sem campo novo neste documento; **não verifiquei** se o cálculo do crédito da agência já exclui `Mov_Agencia_Turismo_Repasse.Valor_Deduzido`: pergunta à equipe (Q150-E6) |
| Q148-15 e D-N424 | Modelo comissão, repasse ou taxa | `Cad_Participante_Modelo_Intermediacao` |
