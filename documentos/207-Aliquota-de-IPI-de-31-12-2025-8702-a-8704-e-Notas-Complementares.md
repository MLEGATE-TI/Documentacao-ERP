# Alíquota de IPI de 31/12/2025 das posições 8702 a 8704 e as Notas Complementares: carga provisória da `Al` da Lei 9.826 — Documento 207

> **O que este documento faz.** Na Q205-4 você aprovou que eu preparasse, em documento próprio, a **tabela da alíquota de IPI de 31/12/2025** das posições 8702 a 8704, como carga provisória da `Al` do crédito presumido da Lei 9.826 (documento 202). Li o **Decreto 12.549/2025** que você enviou (Anexos I a V) e a Tipi que você enviou antes. A tabela está no Anexo A (**85 linhas**: 56 códigos de NCM e 29 destaques "Ex"). Ao montá-la achei que **uma tabela por NCM não basta**: as Notas Complementares NC (87-13) e NC (87-14), em vigor até 31/12/2026, mudam a alíquota **veículo a veículo** (propulsão, eficiência, potência, desempenho estrutural e reciclabilidade). Por isso o documento também propõe **onde o ERP guarda a `Al` calculada para cada ficha de veículo**.
>
> **Resposta (11/11/2026, D-N566):** "Q207-1 a Q207-6 - Seguir com as recomendações" (a Q207-7 já estava respondida, D-N565). O documento está **aprovado inteiro**; as recomendações "sim, provisório" das Q207-1 (carga de 85 linhas) e Q207-6 (`Al` zero da versão sustentável) valem como provisórias. **Ainda não aplicado ao dicionário**: entra no próximo "consolidar".

> **Nada foi aplicado ao dicionário.** Ele está na revisão 41 (1.201 entidades e 13.801 campos). Este documento só vale com a sua resposta às Q207-1 a Q207-6 (a Q207-7 foi respondida em 11/11/2026: a Receita não publica outra Tipi).

*Fontes: Decreto 12.549, de 10/07/2025 (arts. 1º a 8º; Anexos I, II, III, IV e V; texto do Planalto, impresso em 10/11/2026), que você enviou, **e o texto do DOU de 11/07/2025, edição 129, seção 1, página 1 (três PDFs, impressos em 11/11/2026), que você enviou depois**; Tipi 2022 com atualizações até o ADE RFB 1/2026 (posições 87.02 a 87.08 e as Notas Complementares NC 87-1 a NC 87-12), que você enviou em 10/11/2026 (**e em planilha, "TIPI 2022 - Atualizada ADE 001-2026.xlsx", enviada em 11/11/2026: a coluna "Tipi enviada" das 85 linhas confere com ela, sem diferença; a planilha só traz a tabela, sem as Notas Complementares**); documentos 202, 204 e 205 e o dicionário na revisão 41.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **A alíquota que vale em 31/12/2025 é a do Decreto 12.549, e não a da Tipi enviada.** O decreto altera as posições 87.03 e 87.04 (e seus "Ex") e produz efeitos desde **01/11/2025** (art. 8º, II; só o art. 4º e a NC (87-15) valem desde a publicação, **11/07/2025**, art. 8º, I). Na 87.03 ele fixa **6,30%** em 19 códigos (a Tipi enviada mostra 5,27%, 9,78% e 18,81%); na 87.04 fixa 0%, 3,90% e 6,50% por destaque. A **87.02 não foi alterada**: a alíquota vem da Tipi (16,25%, 6,5% e 0%).
- **O Anexo A tem 85 linhas.** 47 vêm do decreto (34 mudam a Tipi e 13 repetem o valor dela) e 38 vêm da Tipi enviada (87.02, os códigos de 87.04 que o decreto não tocou e o código 8703.10.00). Duas linhas da Tipi, os "Ex 01" dos códigos 8703.23.10 e 8703.23.90, **ficam de fora** porque o decreto não os cita e a alíquota deles (9,78%) seria maior que a nova geral (Q207-3, C304).
- **A `Al` não é uma alíquota por NCM.** A NC (87-13) (87.03) e a NC (87-14) (87.04), "até 31 de dezembro de 2026", **somam à alíquota-base cinco ajustes** (propulsão, eficiência energética, potência, desempenho estrutural e reciclabilidade), com piso de 0%. Os mesmos ajustes já estão no dicionário (`Cad_Is_Veiculo_Ajuste`, 62 linhas de IPI de 01/11/2025 a 31/12/2026, documento 204) e os dados de cada veículo estão em `Cad_Veiculo_Versao`. A NC (87-15) **zera** o IPI da versão sustentável registrada no MDIC.
- **Efeito na fórmula da Lei 9.826** (`CP = V × Al × (1 − Al) × F`): o fator `Al × (1 − Al)` vale **0,0590** com a base de 6,30% e valia **0,1527** com os 18,81% da Tipi antiga, ou seja, **61% menos** crédito para a mesma base. Com a NC (87-15) a `Al` é zero e **o crédito do veículo é zero**. Um exemplo completo está no Anexo C.
- **Proposta:** **1 entidade nova**, `Mov_Aliquota_Ipi_Veiculo` (21 campos, 7 de referência), que guarda a `Al` de cada ficha de veículo na data de referência (alíquota-base, os cinco ajustes, a nota complementar aplicada e o resultado); **1 valor novo** (`calculada_pelo_motor`) em `Origem_Aliquota_Ipi` de `Mov_Credito_Automotivo_Apuracao_Ncm`, cuja descrição passa a dizer que a linha é **por NCM e por `Al`**; a **carga provisória de 85 linhas** nas tabelas que já existem (`Cad_Classificacao_Mercadoria.Aliquota_Ipi` e `Cad_NCM_Ex_Tipi`); 6 regras e 6 avisos do Motor. Nenhum campo novo em entidade existente e nenhum domínio novo.
- **O que não está fechado:** as NC (87-7) a (87-12) da Rota 2030 foram revogadas pelo art. 7º, mas o parágrafo único manda continuar aplicando as reduções "enquanto não vigorar a revogação"; li que **não somam** com os critérios da NC (87-13) (que já os absorvem) e **pergunto ao contador** (C303 a C307).
- **Contador:** 5 perguntas novas, C303 a C307 (documento 188, Parte 19).

# 2. O que li

| Fonte | O que li | O que tirei |
|---|---|---|
| Decreto 12.549/2025, arts. 1º a 8º | O texto inteiro | Altera as alíquotas das posições 87.03 e 87.04 e dos "Ex" (art. 1º); cria o "Ex 01" do código 8704.60.00 (art. 2º, Anexo V, 3,9%); inclui as NC (87-13), (87-14) e (87-15) (art. 3º, com alíquota mínima de 0%); condiciona a NC (87-15) a requerimento, ato de registro dos compromissos e ato do MDIC (art. 4º); revoga as NC (87-4) a (87-12) (art. 7º); efeitos na publicação para o art. 4º e a NC (87-15) e **no primeiro dia do quarto mês seguinte (01/11/2025)** para o resto (art. 8º) |
| Decreto 12.549, Anexo I | A tabela inteira (47 linhas) | 6,30% em 19 códigos de 87.03 (todos de 8703.21.00 a 8703.90.00); em 87.04, 0, 3,90 e 6,50 por código e destaque |
| DOU de 11/07/2025, edição 129 (291 páginas), e o Anexo I isolado | A página 1 (decreto e Anexos) e a procura de outros atos de IPI e das posições 87.02 a 87.04 no resto da edição | **O decreto é o mesmo** do texto do Planalto: artigos, Notas Complementares, Anexos e as 47 linhas do Anexo I, com os mesmos valores (conferi um a um com a tabela de 85 linhas). A edição não traz outro ato sobre IPI nem sobre 87.02 a 87.04; o outro decreto do dia (12.550) é da reserva da Aeronáutica. Isso vale só para a edição do dia, e não para os atos de 2025 inteiro (C307) |
| Decreto 12.549, Anexo II | NC (87-13), (87-14) e (87-15) inteiras | Cinco critérios, os mesmos valores já carregados no documento 204; listas de códigos de cada nota; versão sustentável: até 83 gCO₂/km, reciclabilidade de 80% ou mais, etapas fabris no País e categoria subcompacto, compacto, utilitário esportivo compacto ou picape compacta |
| Decreto 12.549, Anexos III e IV | As definições e as fórmulas CE2 e CE3; o índice de desempenho estrutural | Iguais ao que o documento 205 já conferiu |
| Tipi enviada, posições 87.02 a 87.08 e NC (87-1) a (87-12) | As alíquotas e as notas | A 87.02 (16,25%, 6,5% e 0%), os códigos de 87.04 não alterados pelo decreto e o 8703.10.00 (33,86%); NC (87-1): os "Ex" da 87.02 dependem de manifestação da RFB; NC (87-2): zero para ambulâncias, carros celulares e carros funerários da 87.03; NC (87-3): 6,02% no 8703.22.90 com habitáculo acima de 6 m³, com manifestação da RFB. **A Tipi enviada não incorpora o Decreto 12.549 no capítulo 87** (documento 205, C266) |
| Documentos 202, 204 e 205 | A fórmula, o uso da `Al` e os ajustes de IPI | A `Al` é a de 31/12/2025 "conforme a Tipi, inclusive Notas Complementares" (LC 214, art. 312, II); a `Al` pode ser informada no produto do projeto; `Cad_Is_Veiculo_Ajuste` tem as linhas de IPI de 01/11/2025 a 31/12/2026 |
| Dicionário, revisão 41 | `Cad_Classificacao_Mercadoria`, `Cad_NCM_Ex_Tipi`, `Cad_Veiculo_Versao`, `Cad_Is_Veiculo_Ajuste`, `Cad_Credito_Automotivo_Parametro`, `Cad_Habilitacao_Automotiva_Produto`, `Mov_Credito_Automotivo_Apuracao_Ncm`, `Mov_Nota_Fiscal_Saida_Item` | Ver a seção 3 |

# 3. O que o dicionário já tem

| O quê | Onde | O que falta |
|---|---|---|
| Alíquota de IPI por NCM, com vigência | `Cad_Classificacao_Mercadoria.Aliquota_Ipi` (só em código analítico, com `Vigencia_Inicio` e `Vigencia_Fim`) | A **carga** das posições 8702 a 8704 na versão de 01/11/2025 |
| Alíquota de IPI por destaque "Ex", com vigência | `Cad_NCM_Ex_Tipi` (`Numero_Ex`, `Aliquota_Ipi`) | A carga dos 29 destaques |
| Data de referência da `Al` | `Cad_Credito_Automotivo_Parametro` (tipo `data_referencia_aliquota_ipi`, 31/12/2025) | Nada |
| Os ajustes da NC (87-13) e (87-14) | `Cad_Is_Veiculo_Ajuste` (62 linhas de IPI, 01/11/2025 a 31/12/2026) | Nada: o Motor lê as linhas vigentes na data de referência |
| Os dados do veículo para os cinco critérios | `Cad_Veiculo_Versao` (tecnologia de propulsão, potência em kW, nível de eficiência, desempenho estrutural, nível de reciclabilidade, massa) | Nada |
| A versão sustentável | `Cad_Veiculo_Versao_Sustentavel` (documento 204) | Nada |
| A `Al` no crédito | `Cad_Habilitacao_Automotiva_Produto.Aliquota_Ipi_Referencia` (informada) e `Mov_Credito_Automotivo_Apuracao_Ncm.Aliquota_Ipi_Referencia` (gravada por NCM) | **Onde guardar a `Al` calculada com as Notas Complementares para cada ficha de veículo**, e a regra de que a linha da apuração é por NCM e por `Al` |
| A ficha do veículo no item da nota | `Mov_Nota_Fiscal_Saida_Item.ID_Veiculo_Versao` | Nada |

# 4. Achados e leituras minhas

- **(1)** **O decreto só mexe na 87.03 e na 87.04.** O art. 1º diz "posição 87.03 e 87.04 e nos respectivos destaques Ex". A 87.02 (ônibus) fica com a Tipi.
- **(2)** **A alíquota-base mudou em 01/11/2025.** O Anexo I fixa 6,30% nos códigos de 8703.21.00 a 8703.90.00, e na 87.04 muda 34 linhas da Tipi (por exemplo, o Ex 01 do 8704.21.10 passa de 5,2% para 3,9%, e os códigos 8704.31.x passam de 6,5%, 2,6% e 5,2% para 3,9%). O 8703.10.00 (neve e golfe) não está no anexo e segue com 33,86%.
- **(3)** **A `Al` depende do veículo.** As NC (87-13) e (87-14) alteram a alíquota "de acordo com o enquadramento nos critérios", e a LC 214 manda usar a alíquota "inclusive Notas Complementares". Um carro flex de 110 kW que cumpre os itens de eficiência, de desempenho estrutural e de reciclabilidade tem `Al` de 2,80%, e um diesel de mais de 290 kW (códigos 8703.3x), sem nenhuma redução, chega a 24,80% (6,30 mais 12,0 mais 6,5). **Por isso a `Al` é por ficha de veículo.**
- **(4)** **A versão sustentável zera o IPI e zera o crédito.** A NC (87-15) fixa 0% quando o veículo obtém o registro de versão sustentável do MDIC (art. 4º, III, exige um ato do MDIC que ainda não localizei). Com `Al` = 0, `Al × (1 − Al)` = 0 e o crédito presumido da Lei 9.826 daquele veículo é zero (leitura minha da fórmula do documento 202).
- **(5)** **As NC da Rota 2030 estão no limite.** O art. 7º revoga as NC (87-4) a (87-12), com efeito em 01/11/2025 (art. 8º, II). O parágrafo único diz que, "enquanto não vigorar a revogação" das NC (87-7) a (87-12), aplicam-se as reduções dos itens 3 e 4 do Anexo III e do item 6 do Anexo IV do Decreto 9.557. Li assim: em 31/12/2025 as NC (87-4) a (87-12) **já estão revogadas**; as reduções da Rota 2030 estão **dentro** da NC (87-13) (critérios de eficiência, de 2 e 1 ponto, e de desempenho estrutural, 1 ponto), e **somar as duas contaria duas vezes**. É leitura minha (C303).
- **(6)** **Os "Ex 01" de 8703.23.10 e 8703.23.90.** A Tipi enviada traz 9,78% (cilindrada de 1.500 a 2.000 cm³). O Anexo I não os cita, e a base nova de 6,30% é menor. **Não carreguei** as duas linhas: o Motor usa os 6,30% do código (C304).
- **(7)** **A NC (87-2) e a NC (87-3) continuam.** O decreto não as revoga. A NC (87-2) zera ambulâncias, carros celulares e carros funerários; a NC (87-3) fixa 6,02% no 8703.22.90 com habitáculo acima de 6 m³ (com manifestação da RFB), valor **menor** que os 6,30%. Como elas convivem com os critérios da NC (87-13), o decreto não diz (C305). Entram como hipóteses do Motor, com a ordem provisória do item 5.3.
- **(8)** **Um Ex novo.** O art. 2º e o Anexo V criam o "Ex 01" do 8704.60.00 (camionetas, furgões e semelhantes elétricos), com 3,9%.
- **(9)** **A Tipi enviada não serve para 87.03 e 87.04** (já registrado no documento 205). Para a 87.02 e para os códigos de 87.04 que o decreto não cita ela é a única fonte que tenho, e pode haver alteração de 2025 que não vi (C307).
- **(10)** **A linha da apuração tem de ser por NCM e por `Al`.** A fórmula não é linear: somar as bases de veículos com `Al` diferentes e aplicar uma `Al` só dá resultado errado. Hoje `Mov_Credito_Automotivo_Apuracao_Ncm` já grava a `Al`; basta a regra de que há **uma linha para cada par NCM e `Al`**.
- **(11)** **Depois de 31/12/2026.** As NC (87-13) a (87-15) valem "até 31 de dezembro de 2026" e o IPI do veículo cai a zero em 2027, salvo o que concorre com a Zona Franca de Manaus (documento 204, C264). Nada disso altera a `Al`, que é congelada em 31/12/2025.

# 5. Proposta

## 5.1 Como as peças se encaixam

O ERP **só registra, calcula o que a norma fecha e avisa; não bloqueia** (D-N284). A ordem é:

- **(1)** **A carga** põe na tabela de NCM e na de Ex as alíquotas do Anexo A, versão de 01/11/2025 a 31/12/9999, **provisórias** (a marca fica em `Motivo_Vigencia`, porque essas duas tabelas não têm situação do dado).
- **(2)** **O Motor lê a data de referência** (`Cad_Credito_Automotivo_Parametro`, 31/12/2025) e escolhe a versão de NCM e de Ex vigente nessa data: é a **alíquota-base**.
- **(3)** **O Motor aplica as Notas Complementares** à ficha do veículo (`Cad_Veiculo_Versao`) e grava o resultado em `Mov_Aliquota_Ipi_Veiculo`: a alíquota-base, os cinco ajustes, a nota aplicada e a `Al` final.
- **(4)** **A apuração do crédito** (`Mov_Credito_Automotivo_Apuracao_Ncm`) agrupa os itens vendidos por NCM e por `Al` e calcula `V × Al × (1 − Al) × F` em cada grupo.
- **(5)** **Avisos** (seção 6) dizem o que falta.

## 5.2 A entidade nova

### `Mov_Aliquota_Ipi_Veiculo` (Contabilidade & Fiscal, movimento, 21 campos)

A `Al` de uma ficha de veículo na data de referência, com a conta feita: alíquota-base, ajustes das Notas Complementares e resultado. Uma linha por ficha de veículo (e produto do projeto, quando houver) e por data de referência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Aliquota_Ipi_Veiculo` | identificador | Chave. |
| `ID_Veiculo_Versao` | referência (Cad_Veiculo_Versao) | A ficha do veículo, na versão vigente na data de referência. |
| `ID_Habilitacao_Automotiva_Produto` | referência (Cad_Habilitacao_Automotiva_Produto), opcional | O produto do projeto da Lei 9.826 a que a alíquota serve. |
| `ID_Classificacao` | referência (Cad_Classificacao_Mercadoria) | A NCM analítica da ficha (posição 8702, 8703 ou 8704). |
| `ID_Ex_Tipi` | referência (Cad_NCM_Ex_Tipi), opcional | O destaque "Ex" em que a ficha se enquadra, quando houver. |
| `ID_Credito_Automotivo_Parametro` | referência (Cad_Credito_Automotivo_Parametro) | A linha `data_referencia_aliquota_ipi` que escolheu as versões lidas. |
| `Data_Referencia` | data | A data lida do parâmetro (31/12/2025), copiada para a conta ficar reproduzível. |
| `Aliquota_Base` | número | A alíquota do Ex, se houver, ou da NCM, na versão vigente na data de referência. |
| `Hipotese_Nota_Complementar` | enumeração {nenhuma, nc_87_1_ex_certificado, nc_87_2_zero, nc_87_3_fixada, nc_87_13_14_criterios, nc_87_15_versao_sustentavel} | A Nota Complementar que decidiu a alíquota. `nenhuma`: vale a base. |
| `Ajuste_Propulsao` | número, opcional | Pontos do critério 1 (NC 87-13 ou 87-14). |
| `Ajuste_Eficiencia` | número, opcional | Pontos do critério 2. |
| `Ajuste_Potencia` | número, opcional | Pontos do critério 3. |
| `Ajuste_Desempenho_Estrutural` | número, opcional | Pontos do critério 4. |
| `Ajuste_Reciclabilidade` | número, opcional | Pontos do critério 5. |
| `Aliquota_Apos_Criterios` | número | Base mais os cinco ajustes, com piso de 0 (Decreto 12.549, art. 3º, parágrafo único). Igual à base quando não há critérios. |
| `Aliquota_Referencia_Final` | número | A `Al`: a alíquota que vai para a apuração do crédito. |
| `Origem_Calculo` | enumeração {calculada_pelo_motor, informada_pelo_usuario} | Quem decidiu a `Al`. |
| `ID_Documento_Condicao` | referência (Cad_Documento), opcional | A manifestação da RFB (NC 87-1 e 87-3) ou o registro de versão sustentável do MDIC (NC 87-15). |
| `Dados_Provisorios` | booleano | Verdadeiro se alguma linha lida (carga, ajuste ou ficha) está provisória; o relatório avisa. |
| `Memoria_Calculo` | texto | O texto da conta, para auditoria. |
| `ID_Usuario_Confirmacao` | referência (Cad_Usuario), opcional | Quem confirmou a `Al`. |

Regra de conferência: a unicidade é por `ID_Veiculo_Versao`, `ID_Habilitacao_Automotiva_Produto` e `Data_Referencia`.

## 5.3 Como o Motor calcula a `Al`

A **primeira** condição que vale define a alíquota:

| Ordem | Condição | `Hipotese_Nota_Complementar` | `Al` |
|---|---|---|---|
| 1 | A ficha é versão sustentável com registro do MDIC (NC 87-15) e a NCM está nas listas das NC (87-13) ou (87-14) | `nc_87_15_versao_sustentavel` | 0 |
| 2 | Ambulância, carro celular ou carro funerário da 87.03, com a prova da condição (NC 87-2) | `nc_87_2_zero` | 0 |
| 3 | 8703.22.90 com habitáculo acima de 6 m³ e manifestação da RFB (NC 87-3) | `nc_87_3_fixada` | 6,02 |
| 4 | NCM nas listas da NC (87-13) (8703.21.00 a 8703.80.00) ou da NC (87-14) (87.04, itens listados) | `nc_87_13_14_criterios` | Máximo entre 0 e (base + cinco ajustes de `Cad_Is_Veiculo_Ajuste` do IPI vigentes na data, tabela `tabela_87_03` ou `tabela_8704`) |
| 5 | 8702 com "Ex 01" ou "Ex 02" e manifestação da RFB (NC 87-1) | `nc_87_1_ex_certificado` | A do Ex |
| 6 | Qualquer outro caso (8702 sem Ex, 8703.10.00, 8703.90.00, códigos de 87.04 fora da lista) | `nenhuma` | A base |

A ordem 1, 2 e 3 é **leitura minha** (a mais específica primeiro); o decreto não diz como a NC (87-3) e a NC (87-2) convivem com a NC (87-13) (C305). O Motor **propõe** o Ex e a nota pela ficha e o usuário confirma (nada bloqueia).

## 5.4 Ajustes nas entidades que já existem

| Entidade | Campo | Mudança |
|---|---|---|
| `Mov_Credito_Automotivo_Apuracao_Ncm` | `Origem_Aliquota_Ipi` | Valor novo `calculada_pelo_motor` (a `Al` veio de `Mov_Aliquota_Ipi_Veiculo`). Hoje: `tipi_na_data_referencia` e `informada_no_projeto`. |
| `Mov_Credito_Automotivo_Apuracao_Ncm` | `Aliquota_Ipi_Referencia` | A descrição passa a dizer que a linha é **por NCM e por `Al`**: o Motor soma, em cada linha, as bases dos itens que têm a mesma `Al`. |

**Qual `Al` vale para um item vendido:** (a) a de `Mov_Aliquota_Ipi_Veiculo` da ficha do item (`Mov_Nota_Fiscal_Saida_Item.ID_Veiculo_Versao`) na data de referência; (b) sem ela, a informada no produto do projeto (`Cad_Habilitacao_Automotiva_Produto.Aliquota_Ipi_Referencia`, C252); (c) sem as duas, a da versão de NCM (ou de Ex) vigente em 31/12/2025, **sem** Notas Complementares (e com aviso).

## 5.5 Parâmetro documentado e ligações

- **Parâmetro documentado (documento 201).** Não nasce parâmetro novo. A linha `credito_auto_aliquota_ipi_tipi` (documento 202) passa a registrar que a carga tem 85 linhas, de duas fontes (Decreto 12.549 e Tipi enviada), e a linha `credito_auto_data_referencia_ipi` continua escolhendo a versão.
- **Documento 204.** O Motor reaproveita as 62 linhas de IPI de `Cad_Is_Veiculo_Ajuste`; se o contador mudar um ajuste, muda a `Al`.
- **Documento 202.** A fórmula e o fator `F` não mudam.

# 6. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|---|---|---|
| 1 | Ficha sem dado de critério | `Cad_Veiculo_Versao` sem potência, nível de eficiência, desempenho estrutural ou reciclabilidade: o critério entra com ajuste zero |
| 2 | Item sem ficha de veículo | O item vendido não tem `ID_Veiculo_Versao`: a `Al` é a do produto do projeto ou a da NCM, sem Notas Complementares |
| 3 | Ex não indicado | A NCM tem destaque "Ex" e a ficha não diz qual: vale o código sem Ex |
| 4 | Condição sem documento | NC (87-1), (87-2), (87-3) ou (87-15) escolhida sem `ID_Documento_Condicao` |
| 5 | `Al` zero | `Aliquota_Referencia_Final` = 0: o crédito do veículo é zero |
| 6 | Dados provisórios | `Dados_Provisorios` verdadeiro: a carga, o ajuste ou a ficha ainda não foi validado |

# 7. Perguntas

A Q205-4 está **respondida** (D-N544). As novas começam na Q207-1.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q207-1 | Aprova a **carga provisória de 85 linhas** do Anexo A (56 códigos de NCM em `Cad_Classificacao_Mercadoria.Aliquota_Ipi` e 29 destaques em `Cad_NCM_Ex_Tipi`), versão de 01/11/2025 a 31/12/9999, com a marca "provisório (documento 207)" em `Motivo_Vigencia`? | Sim, provisório |
| Q207-2 | Aprova a leitura de que as **NC (87-4) a (87-12)** (Rota 2030) estão **revogadas** em 31/12/2025 e **não somam** com os critérios da NC (87-13) e (87-14) (C303)? | Sim |
| Q207-3 | Aprova **não carregar** os "Ex 01" de 8703.23.10 e 8703.23.90 (9,78% na Tipi, sem alíquota no Anexo I), de modo que valem os 6,30% do código (C304)? | Sim |
| Q207-4 | Aprova **`Mov_Aliquota_Ipi_Veiculo`** (21 campos), as **6 regras** de cálculo da seção 5.3 e os **6 avisos**, com a ordem provisória das Notas Complementares (C305)? | Sim |
| Q207-5 | Aprova os **2 ajustes** em `Mov_Credito_Automotivo_Apuracao_Ncm` (valor `calculada_pelo_motor` e linha por NCM e por `Al`) e a ordem de escolha da `Al` do item (ficha, produto, NCM)? | Sim |
| Q207-6 | Aceita que a `Al` de uma versão sustentável (NC 87-15) seja **zero** e que, por isso, o crédito daquele veículo seja zero (C306)? | Sim, provisório |
| Q207-7 | Envia, quando puder, a **Tipi consolidada com o Decreto 12.549 incorporado** e confirma se houve outro ato de 2025 sobre 87.02 a 87.04 (C307)? | **Respondida (11/11/2026, D-N565):** não há outra Tipi publicada no site da Receita; a carga fica com o decreto e a Tipi enviada, provisória. A confirmação de outros atos de 2025 fica na C307 |

# 8. O que acontece se você aprovar

- **Tudo (Q207-1 a Q207-6):** **1 entidade nova**, **21 campos** (7 de referência), **1 valor novo** de enumeração em `Mov_Credito_Automotivo_Apuracao_Ncm.Origem_Aliquota_Ipi` e **1 descrição alterada**, nenhum campo novo em entidade existente e nenhum domínio novo. Sobre a revisão 41: **1.202 entidades, 13.822 campos, 3.575 campos de referência e 360 domínios**. **Ensaio feito** (sem entregar nada): a auditoria fechou com **0 achados** e o gerador de DDL deu **1.447 tabelas**, **3.820 chaves estrangeiras, 3.911 índices e 11.599 comentários**. As entidades mestres seguem em 245 e **nenhuma chave opcional nova espera onda de destino** (seguem as 81): todas as referências da entidade nova apontam para a mesma onda ou para uma anterior.
- **Carga:** 85 linhas provisórias (56 de NCM, 29 de Ex), 6 regras e 6 avisos em texto. Arquivo `carga207_aliquota_ipi.csv` com as mesmas linhas do Anexo A.
- **Ao contador:** cinco perguntas novas, C303 a C307 (documento 188, Parte 19).
- **Se a Q207-4 vier "não":** fica só a carga por NCM, e a `Al` vem da versão de NCM ou da informada no produto, **sem** as Notas Complementares; os valores do crédito ficam sobrestimados para os veículos que têm ajuste negativo e subestimados para os que têm ajuste positivo.
- **Nada é aplicado antes de "consolidar".**

# 9. Limites

- **Não li:** a **Tipi consolidada com o Decreto 12.549** (você informou em 11/11/2026 que a Receita não publica outra; a enviada não o incorpora no capítulo 87); o **ato do MDIC** que o art. 4º, III, exige para a versão sustentável; o **Decreto 9.557** além do que o documento 205 conferiu; a **LC 214, art. 312** e o **Decreto 12.955, art. 522** nesta rodada (li-os no documento 202).
- **A `Al` das posições 87.02 e dos códigos de 87.04 que o decreto não cita** vem da Tipi enviada (atualizada até o ADE RFB 1/2026, mas sem o decreto no capítulo 87). Pode haver alteração que não vi (C307).
- **Leituras minhas:** as NC da Rota 2030 revogadas e sem soma (C303); o Ex de 8703.23 fora da carga (C304); a ordem entre NC (87-1), (87-2), (87-3), (87-13) e (87-15) (C305); o crédito zero da versão sustentável (C306).
- **Não conferi a alíquota código por código** com um segundo exemplar do Anexo I: li o do Planalto, em duas colunas, e conferi a contagem (47 linhas).
- **O IPI de 2027** (zero, salvo Zona Franca de Manaus) não entra: a `Al` é a de 31/12/2025.

# Anexo A. Tabela de IPI de 31/12/2025, posições 8702 a 8704 (carga provisória, 85 linhas)

Alíquotas em %. A coluna "Alíquota carregada" é a do decreto, quando ele lista o código, e a da Tipi enviada nos demais casos. "—" quer dizer que a fonte não traz a linha. Versão de 01/11/2025 a 31/12/9999, provisória.

| Código | Destaque | Descrição | Tipi enviada | Decreto 12.549 | Alíquota carregada |
|---|---|---|---|---|---|
| 8702.10.00 |  | Só motor diesel | 16,25 | — | 16,25 |
| 8702.10.00 | Ex 01 | Só motor diesel, habitáculo de 6 a menos de 9 m³ | 6,5 | — | 6,5 |
| 8702.10.00 | Ex 02 | Só motor diesel, habitáculo de 9 m³ ou mais | 0 | — | 0 |
| 8702.20.00 |  | Diesel e elétrico | 16,25 | — | 16,25 |
| 8702.20.00 | Ex 01 | Diesel e elétrico, habitáculo de 6 a menos de 9 m³ | 6,5 | — | 6,5 |
| 8702.20.00 | Ex 02 | Diesel e elétrico, habitáculo de 9 m³ ou mais | 0 | — | 0 |
| 8702.30.00 |  | Centelha e elétrico | 16,25 | — | 16,25 |
| 8702.30.00 | Ex 01 | Centelha e elétrico, habitáculo de 6 a menos de 9 m³ | 6,5 | — | 6,5 |
| 8702.30.00 | Ex 02 | Centelha e elétrico, habitáculo de 9 m³ ou mais | 0 | — | 0 |
| 8702.40.90 |  | Só elétrico, exceto trólebus | 16,25 | — | 16,25 |
| 8702.40.90 | Ex 01 | Só elétrico, exceto trólebus, habitáculo de 6 a menos de 9 m³ | 6,5 | — | 6,5 |
| 8702.40.90 | Ex 02 | Só elétrico, exceto trólebus, habitáculo de 9 m³ ou mais | 0 | — | 0 |
| 8702.90.00 |  | Outros | 16,25 | — | 16,25 |
| 8702.90.00 | Ex 01 | Outros, habitáculo de 6 a menos de 9 m³ | 6,5 | — | 6,5 |
| 8702.90.00 | Ex 02 | Outros, habitáculo de 9 m³ ou mais | 0 | — | 0 |
| 8702.40.10 |  | Trólebus | 0 | — | 0 |
| 8703.10.00 |  | Veículos para neve, campo de golfe e semelhantes | 33,86 | — | 33,86 |
| 8703.21.00 |  | Centelha, até 1.000 cm³ | 5,27 | 6,3 | 6,3 |
| 8703.22.10 |  | Centelha, 1.000 a 1.500 cm³, até 6 pessoas | 9,78 | 6,3 | 6,3 |
| 8703.22.90 |  | Centelha, 1.000 a 1.500 cm³, outros | 9,78 | 6,3 | 6,3 |
| 8703.23.10 |  | Centelha, 1.500 a 3.000 cm³, até 6 pessoas | 18,81 | 6,3 | 6,3 |
| 8703.23.90 |  | Centelha, 1.500 a 3.000 cm³, outros | 18,81 | 6,3 | 6,3 |
| 8703.24.10 |  | Centelha, acima de 3.000 cm³, até 6 pessoas | 18,81 | 6,3 | 6,3 |
| 8703.24.90 |  | Centelha, acima de 3.000 cm³, outros | 18,81 | 6,3 | 6,3 |
| 8703.31.10 |  | Diesel, até 1.500 cm³, até 6 pessoas | 18,81 | 6,3 | 6,3 |
| 8703.31.90 |  | Diesel, até 1.500 cm³, outros | 18,81 | 6,3 | 6,3 |
| 8703.32.10 |  | Diesel, 1.500 a 2.500 cm³, até 6 pessoas | 18,81 | 6,3 | 6,3 |
| 8703.32.90 |  | Diesel, 1.500 a 2.500 cm³, outros | 18,81 | 6,3 | 6,3 |
| 8703.33.10 |  | Diesel, acima de 2.500 cm³, até 6 pessoas | 18,81 | 6,3 | 6,3 |
| 8703.33.90 |  | Diesel, acima de 2.500 cm³, outros | 18,81 | 6,3 | 6,3 |
| 8703.40.00 |  | Híbrido centelha, sem recarga externa | 18,81 | 6,3 | 6,3 |
| 8703.50.00 |  | Híbrido diesel, sem recarga externa | 18,81 | 6,3 | 6,3 |
| 8703.60.00 |  | Híbrido centelha recarregável | 18,81 | 6,3 | 6,3 |
| 8703.70.00 |  | Híbrido diesel recarregável | 18,81 | 6,3 | 6,3 |
| 8703.80.00 |  | Só elétrico | 18,81 | 6,3 | 6,3 |
| 8703.90.00 |  | Outros | 18,81 | 6,3 | 6,3 |
| 8704.10.10 |  | Dumpers fora de rodovia, 85 t ou mais | 0 | — | 0 |
| 8704.10.90 |  | Dumpers fora de rodovia, outros | 0 | — | 0 |
| 8704.21.10 |  | Diesel até 5 t, chassis com motor e cabina | 0 | 0 | 0 |
| 8704.21.10 | Ex 01 | De camionetas, furgões, pick-ups e semelhantes | 5,2 | 3,9 | 3,9 |
| 8704.21.20 |  | Diesel até 5 t, caixa basculante | 0 | 0 | 0 |
| 8704.21.20 | Ex 01 | De camionetas, furgões, pick-ups e semelhantes | 2,6 | 3,9 | 3,9 |
| 8704.21.30 |  | Diesel até 5 t, frigoríficos ou isotérmicos | 0 | 0 | 0 |
| 8704.21.30 | Ex 01 | De camionetas, furgões, pick-ups e semelhantes | 2,6 | 3,9 | 3,9 |
| 8704.21.90 |  | Diesel até 5 t, outros | 0 | 0 | 0 |
| 8704.21.90 | Ex 01 | De camionetas, furgões, pick-ups e semelhantes | 5,2 | 3,9 | 3,9 |
| 8704.21.90 | Ex 02 | Carro-forte para valores | 6,5 | 6,5 | 6,5 |
| 8704.22.10 |  | Diesel 5 a 20 t, chassis com motor e cabina | 0 | — | 0 |
| 8704.22.20 |  | Diesel 5 a 20 t, caixa basculante | 0 | — | 0 |
| 8704.22.30 |  | Diesel 5 a 20 t, frigoríficos ou isotérmicos | 0 | — | 0 |
| 8704.22.90 |  | Diesel 5 a 20 t, outros | 0 | — | 0 |
| 8704.23.10 |  | Diesel acima de 20 t, chassis com motor e cabina | 0 | — | 0 |
| 8704.23.20 |  | Diesel acima de 20 t, caixa basculante | 0 | — | 0 |
| 8704.23.30 |  | Diesel acima de 20 t, frigoríficos ou isotérmicos | 0 | — | 0 |
| 8704.23.40 |  | Chassis articulado para troncos (forwarder), 126 kW ou mais | 3,25 | — | 3,25 |
| 8704.23.90 |  | Diesel acima de 20 t, outros | 0 | — | 0 |
| 8704.23.90 | Ex 01 | Trator florestal (forwarder), exceto 8704.23.40 | 3,25 | — | 3,25 |
| 8704.31.10 |  | Centelha até 5 t, chassis com motor e cabina | 6,5 | 3,9 | 3,9 |
| 8704.31.10 | Ex 01 | De caminhão | 0 | 0 | 0 |
| 8704.31.20 |  | Centelha até 5 t, caixa basculante | 2,6 | 3,9 | 3,9 |
| 8704.31.20 | Ex 01 | Caminhão | 0 | 0 | 0 |
| 8704.31.30 |  | Centelha até 5 t, frigoríficos ou isotérmicos | 2,6 | 3,9 | 3,9 |
| 8704.31.30 | Ex 01 | Caminhão | 0 | 0 | 0 |
| 8704.31.90 |  | Centelha até 5 t, outros | 5,2 | 3,9 | 3,9 |
| 8704.31.90 | Ex 01 | Caminhão | 0 | 0 | 0 |
| 8704.32.10 |  | Centelha acima de 5 t, chassis com motor e cabina | 0 | — | 0 |
| 8704.32.20 |  | Centelha acima de 5 t, caixa basculante | 0 | — | 0 |
| 8704.32.30 |  | Centelha acima de 5 t, frigoríficos ou isotérmicos | 0 | — | 0 |
| 8704.32.90 |  | Centelha acima de 5 t, outros | 0 | — | 0 |
| 8704.41.00 |  | Híbrido diesel até 5 t | 0 | 0 | 0 |
| 8704.41.00 | Ex 01 | Chassis com motor e cabina de camionetas, furgões, pick-ups e semelhantes | 5,2 | 3,9 | 3,9 |
| 8704.41.00 | Ex 02 | Camionetas, furgões, pick-ups e semelhantes com caixa basculante, frigoríficos ou isotérmicos | 2,6 | 3,9 | 3,9 |
| 8704.41.00 | Ex 03 | Outros camionetas, furgões, pick-ups e semelhantes | 5,2 | 3,9 | 3,9 |
| 8704.41.00 | Ex 04 | Carro-forte para valores | 6,5 | 6,5 | 6,5 |
| 8704.42.00 |  | Híbrido diesel, 5 a 20 t | 0 | — | 0 |
| 8704.43.00 |  | Híbrido diesel, acima de 20 t | 0 | — | 0 |
| 8704.43.00 | Ex 01 | Trator florestal (forwarder) | 3,25 | — | 3,25 |
| 8704.51.00 |  | Híbrido centelha até 5 t | 5,2 | 3,9 | 3,9 |
| 8704.51.00 | Ex 01 | Chassis com motor e cabina, exceto de caminhão | 6,5 | 3,9 | 3,9 |
| 8704.51.00 | Ex 02 | Caixa basculante, frigoríficos ou isotérmicos, exceto caminhões | 2,6 | 3,9 | 3,9 |
| 8704.51.00 | Ex 03 | Caminhões e chassis de caminhão | 0 | 0 | 0 |
| 8704.52.00 |  | Híbrido centelha acima de 5 t | 0 | — | 0 |
| 8704.60.00 |  | Só elétrico | 0 | 0 | 0 |
| 8704.60.00 | Ex 01 | Camionetas, furgões, pick-ups e semelhantes (Ex criado pelo Decreto 12.549, art. 2º e Anexo V) | — | 3,9 | 3,9 |
| 8704.90.00 |  | Outros | 0 | — | 0 |

**Fora da carga (Q207-3):** `8703.23.10 Ex 01` e `8703.23.90 Ex 01` (cilindrada de 1.500 a 2.000 cm³; 9,78% na Tipi enviada, sem alíquota no Anexo I).

# Anexo B. Notas Complementares que decidem a `Al`

| Nota | Alcance | Efeito | Condição | Vigência |
|---|---|---|---|---|
| NC (87-1) | "Ex 01" e "Ex 02" de 8702.10.00, .20.00, .30.00, .40.90 e .90.00 | Alíquota do Ex (6,5% ou 0%) | Manifestação da RFB certificando que o veículo cumpre as exigências | Tipi |
| NC (87-2) | Ambulâncias, carros celulares e carros funerários da 87.03 | Zero | Prova da condição | Tipi |
| NC (87-3) | 8703.22.90 com habitáculo acima de 6 m³ | Fixa 6,02% | Manifestação da RFB | Tipi |
| NC (87-13) | 8703.21.00 a 8703.80.00 | Base mais cinco ajustes (piso 0) | Critérios da ficha do veículo | Até 31/12/2026 |
| NC (87-14) | 8704.21.10 Ex 01, 8704.21.20 Ex 01, 8704.21.30 Ex 01, 8704.21.90 Ex 01, 8704.31.10 a .90 (exceto Ex 01), 8704.41.00 Ex 01 a 03, 8704.51.00 (exceto Ex 03) e 8704.60.00 Ex 01 | Base mais cinco ajustes (piso 0) | Critérios da ficha do veículo | Até 31/12/2026 |
| NC (87-15) | Posições 87.03 e 87.04 das NC (87-13) e (87-14) | Zero | Registro de versão sustentável no MDIC (até 83 gCO₂/km, reciclabilidade de 80% ou mais, etapas fabris no País, categoria subcompacto, compacto, SUV compacto ou picape compacta) | Até 31/12/2026 |
| NC (87-4) a (87-12) | Rota 2030 | Revogadas pelo art. 7º do Decreto 12.549 (C303) | — | Revogadas |

Os valores dos cinco critérios estão no Anexo A do documento 204 e na carga de `Cad_Is_Veiculo_Ajuste` (62 linhas de IPI).

# Anexo C. Exemplo

**Carro flex, 8703.23.10, 110 kW**, eficiência no item 2 do Anexo III, cumpre os requisitos do Anexo IV (desempenho estrutural) e reciclabilidade do item 17, base de vendas no mês de R$ 50.000.000,00, ano de 2027 (`F` = 32%):

| Passo | Valor |
|---|---|
| Alíquota-base (Decreto 12.549, Anexo I) | 6,30 |
| Propulsão (flex-fuel) | 0,00 |
| Eficiência (item 2) | −2,00 |
| Potência (acima de 105 e até 132 kW) | +1,50 |
| Desempenho estrutural (atende) | −1,00 |
| Reciclabilidade (item 17) | −2,00 |
| **`Al` final** | **2,80** |
| Crédito = 50.000.000 × 0,028 × 0,972 × 0,32 | **R$ 435.456,00** |

Com a base de 6,30% e sem critérios, o crédito seria R$ 944.496,00; com os 18,81% da Tipi antiga, R$ 2.443.494,24; com a NC (87-15) (`Al` zero), zero.

# Anexo D. Perguntas ao contador (C303 a C307, documento 188, Parte 19)

| Id | Assunto |
|---|---|
| C303 | Rota 2030 em 31/12/2025: as NC (87-4) a (87-12) estão revogadas desde 01/11/2025 (art. 7º e art. 8º, II do Decreto 12.549) ou o parágrafo único do art. 7º mantém as reduções do Decreto 9.557; e, se mantém, elas somam com os critérios da NC (87-13) e (87-14) |
| C304 | "Ex" da Tipi que o Anexo I não cita (8703.23.10 Ex 01 e 8703.23.90 Ex 01, de 1.500 a 2.000 cm³) e os "Ex" de 8704.23.90 e 8704.43.00 (3,25%): continuam valendo em 31/12/2025 |
| C305 | Convivência da NC (87-2) (zero) e da NC (87-3) (6,02%) com os critérios da NC (87-13): qual prevalece e se os critérios se aplicam sobre a alíquota fixada |
| C306 | `Al` por ficha de veículo (com as Notas Complementares) em vez de por NCM, e o crédito zero da versão sustentável (NC 87-15), em ligação com a C252 (a) e (b) |
| C307 | Alterações de 2025 em 87.02 a 87.04 além do Decreto 12.549 (a Tipi enviada não o incorpora), e se a `Al` dos códigos que ele não cita é a da Tipi |
