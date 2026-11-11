# Tributação do veículo por combustível, potência e demais critérios: IS, IPI e art. 149 da LC 214 — Documento 204

> **O que este documento faz.** Você observou que o documento 202 não mostra a diferença de tributação dos veículos conforme o combustível e a potência do motor (D-N539). Você tem razão, e o assunto é maior que o crédito presumido da CBS: o **Imposto Seletivo** dos veículos (MP 1.399/2026, a partir de 02/02/2027), o **IPI** até 31/12/2026 (Decreto 12.549/2025, Notas Complementares NC 87-13, 87-14 e 87-15) e as condições de combustível e cilindrada do **art. 149 da LC 214** (táxi) variam com os mesmos dados do veículo. Li os textos oficiais que você enviou e propus **seis entidades novas**, 8 campos em entidades existentes e 2 domínios.
>
> **Nada foi aplicado ao dicionário.** Ele está na revisão 38 (1.165 entidades e 13.204 campos). Este documento soma a esse total (1.171 entidades e 13.331 campos se você aprovar tudo) e é independente do documento 202; se os dois forem aprovados, a soma é 1.179 entidades e 13.463 campos.

*Fontes: MP 1.399/2026 (texto oficial do DOU de 04/11/2026, com os Anexos I a VI, lido na íntegra nos arts. 1º a 10, 15 a 19 e nos Anexos I, II, III e V), Decreto 12.549/2025 (lido na íntegra, com os Anexos I a V), Decreto 12.435/2025 (Anexo III, itens 16 a 19, reciclabilidade veicular), Lei 14.902/2024 (arts. 2º, 9º, 10 e 11), MP 1.205/2023 (só o início, vigência encerrada: a Lei 14.902 a substituiu), Decretos 4.186/2002 e 8.168/2013 (revogados; só como pista das Notas Complementares 87-2, 88-1, 88-2 e 88-3), LC 214/2025 consolidada com a LC 227/2026 (arts. 149 a 155, 412 a 425 e 454), e os documentos do Projeto 14, 38, 94, 115, 158 e 196 a 202.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que muda de verdade.** A alíquota do Imposto Seletivo do veículo **não é uma por NCM**: é a alíquota-base do Anexo I (6,3% na posição 87.03; 3,9% nos comerciais leves listados) **mais cinco ajustes** lidos da versão do veículo (propulsão, eficiência energética, potência em kW, desempenho estrutural e reciclabilidade), com piso de zero, **multiplicada por 1,21** e, na importação, por mais **1,17**. Combustível e potência são dois dos cinco ajustes: de **−2,0 a +12,0 pontos** na propulsão e de **−2,15 a +6,5 pontos** na potência. O dicionário só tem uma alíquota por NCM em `Cad_NCM_Imposto_Seletivo` e, na nota, cavalos (`Veiculo_Potencia_Cv`), cilindrada e o código de combustível do Denatran: não dá para calcular.
- **O IPI segue a mesma regra até 31/12/2026** (NC 87-13 e 87-14, mesmas tabelas, piso de zero), com IPI zero para a versão sustentável (NC 87-15). **A partir de 01/01/2027 o IPI é reduzido a zero**, salvo o que concorre com a Zona Franca de Manaus (LC 214, art. 454): por isso o IPI do veículo não ganha entidade nova, só 62 linhas na tabela de ajustes com fim em 31/12/2026.
- **O art. 149 da LC 214** dá alíquota zero de IBS e CBS ao automóvel de táxi (só elétrico, ou até 2.000 cm³ com combustível renovável, sistema reversível ou híbrido) e ao de PcD e TEA (preço de até R$ 200.000,00, benefício até R$ 100.000,00). O dicionário tem os limites e os intervalos como parâmetros, mas **não tem o reconhecimento do direito nem a conferência da compra**.
- **Proposta: 6 entidades novas (119 campos), 8 campos em 3 entidades existentes e 2 domínios novos (22 valores).** `Cad_Veiculo_Versao` (27) e `Cad_Veiculo_Versao_Sustentavel` (17); `Cad_Is_Veiculo_Ajuste` (16, 124 linhas de carga); `Mov_Is_Veiculo_Apuracao` (22); `Cad_Beneficio_Veiculo_Reconhecimento` (16) e `Mov_Beneficio_Veiculo_Utilizacao` (21).
- **Dez pontos em que o texto não fecha a conta** foram lidos de um jeito meu e vão ao contador (C256 a C265): o **arredondamento** da alíquota final, o **item 2 da MP contra o item 5 do Decreto** no desempenho estrutural, a **potência** (kW da ficha contra cv da nota), as **posições fora das listas** (8703.10 e 8703.90), a **versão sem CAT** (importação e usado), a **motorização do táxi**, a **obrigação acessória do IS**, as **notas transitórias da Tipi** que não li, o **IPI da Lei 9.826** (liga-se à C252) e a **conversão da MP**.
- **Perguntas:** Q204-1 a Q204-11 (seção 7), cada uma com recomendação. **Para o contador:** C256 a C265 (Anexo D), que entram no documento 188.
- **Se você aprovar:** 1.171 entidades (+6), 13.331 campos (+127), 3.468 campos de referência (+23), 357 domínios (+2), 124 linhas de ajuste, 10 de NCM, 22 de domínio e 4 do catálogo de parâmetros; os documentos 14 (D-N540) e 38 (seção 1.32) acompanham.

# 2. O que as normas dizem

## 2.1 Imposto Seletivo dos veículos (MP 1.399/2026)

Li o texto oficial. A MP entrou em vigor em 04/11/2026, produz efeitos **a partir de 02/02/2027** e vale até o início dos efeitos da lei que o Poder Executivo deve enviar até 31/05/2027 para as alíquotas de 2028 em diante (arts. 15 e 19).

| Assunto | O texto | Onde |
|----------------|----------------------------------------------|--------------------------------------|
| Fórmula | Alíquota final = (alíquota-base do Anexo I + ajustes dos Anexos II ou III) × fator de conversão do Anexo V. O piso do Decreto 12.549 (alíquota não menor que zero) vale por remissão. | Art. 3º, caput, § 1º, I, § 2º, I; Anexos I, II, III e V |
| Alíquota-base | 6,3% na posição 87.03; 3,9% nas posições 8704.21 e 8704.31 e nos códigos 8704.41.00, 8704.51.00, 8704.60.00 e 8704.90.00. | Anexo I |
| Fator de conversão | 1,21 nos veículos; 1,04 nas aeronaves (final 6,8%); 1,20 nas embarcações (final 12,0% nos barcos a motor da 8903.3 e 7,8% nas demais). O decreto pode reduzir o fator até 1,00. | Art. 3º, § 3º; Anexo V |
| Importação | Fator de ajuste de 1,17 (veículos, embarcações e aeronaves), **cumulativo** com o de conversão; base é o valor aduaneiro mais o imposto de importação. | Art. 8º, §§ 1º e 2º |
| Alíquota zero | PcD, TEA e táxi com direito reconhecido pela RFB (LC 214, arts. 153 e 420); veículo com registro de versão sustentável do MDIC que cumpre os critérios do Decreto 12.549; embarcações e aeronaves sustentáveis. | Art. 4º |
| Não incidência | Caminhões (PBT de 3.500 kg ou mais; a picape nunca é caminhão) e veículos, aeronaves e embarcações de uso operacional das Forças Armadas e da segurança pública. | Art. 5º |
| Transitório | Até 31/12/2027: alíquota zero nas notas complementares 87-2, 88-1 (a, b e c) e 89-1 da Tipi e redução de 50% na 88-2. Recebi dois decretos **revogados** com textos antigos dessas notas (Decreto 4.186/2002: NC 88-1 e 88-2, aeronaves; Decreto 8.168/2013: NC 87-2, veículos de habitáculo maior que 6 m³); servem de pista, não do texto atual (Q204-11, C263). | Art. 6º, III |
| Tipi de referência | A do Decreto 11.158/2022. | Art. 2º |

Os cinco critérios dos veículos, com os valores completos, estão no Anexo A. Em resumo: **propulsão** (14 níveis; no Anexo II vai de −2,0 do elétrico a +12,0 do diesel, e no Anexo III de −2,0 a +2,5), **eficiência energética** (−2, −1 ou 0, conforme os itens 2 e 3 do Anexo III do Decreto 12.549), **potência** (11 faixas de −2,15 a +6,5 no Anexo II e 7 faixas de −0,25 a +3,0 no Anexo III), **desempenho estrutural** (−1 ou 0) e **reciclabilidade** (−2, −1 ou 0, itens 17 e 18 do Anexo III do Decreto 12.435).

## 2.2 IPI dos veículos até 31/12/2026 (Decreto 12.549/2025)

As Notas Complementares NC (87-13) (posição 87.03) e NC (87-14) (posição 87.04, com destaques Ex) repetem **os mesmos cinco critérios e os mesmos valores** dos Anexos II e III da MP, com piso de 0%, **até 31/12/2026**. A NC (87-15) zera o IPI da versão sustentável: emissão de até 83 gCO₂/km do poço à roda, reciclabilidade de pelo menos 80%, etapas fabris no País (Processo Produtivo Básico) e categoria subcompacto, compacto, utilitário esportivo compacto ou picape compacta, tudo com registro do MDIC (Decreto, art. 4º). A alíquota-base é a da Tipi (87.03 a 6,30%; 87.04 por Ex entre 0%, 3,9% e 6,5%). **Desde 01/01/2027 as alíquotas do IPI ficam em zero**, exceto para produtos com industrialização incentivada na Zona Franca de Manaus que concorrem com os do restante do País (LC 214, art. 454, e art. 126, III, do ADCT, que o art. 454 cita; não li o texto do ADCT).

## 2.3 IBS e CBS do automóvel de táxi, PcD e TEA (LC 214, arts. 149 a 155, com a LC 227)

Alíquota zero na venda de automóvel de passageiros de fabricação nacional com no mínimo quatro portas, comprado por motorista profissional de táxi ou por pessoa com deficiência física, visual, auditiva, mental severa ou profunda, ou com TEA moderado ou grave. **Táxi:** só automóvel elétrico ou com motor de cilindrada de até 2.000 cm³ movido a combustível de origem renovável, sistema reversível de combustão ou híbrido (art. 149, § 2º, I). **PcD e TEA:** preço ao consumidor de até R$ 200.000,00, benefício limitado ao valor da operação de R$ 100.000,00, limites atualizados todo 1º de janeiro pela Tabela Fipe (art. 149, § 2º, II, e § 6º). Intervalo mínimo de 2 anos no táxi e 3 anos na PcD e no TEA, salvo perda total, furto ou roubo (art. 152). Reconhecimento pelo estado ou Distrito Federal do domicílio e pela RFB (art. 153), com laudo (art. 151). Alienação antes do intervalo obriga o alienante a pagar os tributos dispensados, com multa e juros, salvo seguradora, falecimento do beneficiário e alienação fiduciária (art. 155).

## 2.4 Versão sustentável e MOVER (Lei 14.902/2024)

O art. 11 manda registrar a versão sustentável por marca e modelo; o art. 2º exige os compromissos do programa e o CAT/Renavam; o Decreto 12.549 (art. 4º) exige o requerimento ao MDIC, o ato de registro dos compromissos e o ato do MDIC sobre a comprovação. A MP 1.399 reaproveita o registro: o veículo registrado, que cumpre CO₂, reciclabilidade, etapas fabris e categoria do Anexo II do Decreto, tem IS zero (art. 4º, II). A MP 1.205/2023 está com a vigência encerrada (vide Lei 14.902).

# 3. O que o dicionário já tem

- **`Cad_NCM_Imposto_Seletivo`**: uma alíquota ad valorem ou específica por NCM e `ID_Grupo_Produto_Is`, com vigência. Não guarda fator, nem ajuste, nem tabela de critérios.
- **`Cad_Is_Hipotese_Base`**: hipótese de fato gerador, contribuinte e base (arts. 412, 414 e 424), 11 linhas de carga.
- **`Mov_Apuracao_Tributo_Item`**: `ID_Is_Hipotese_Base`, `Valor_Referencia_Informado`, alíquota nominal e efetiva, memória e referência normativa. É onde o resultado do IS cai.
- **Nota de saída e de entrada**: `Veiculo_Potencia_Cv`, `Veiculo_Cilindrada_Cc`, `Veiculo_Codigo_Combustivel`, `Veiculo_Peso_Bruto`, `Veiculo_Lotacao`, `Veiculo_Codigo_Marca_Modelo`, `Veiculo_Chassi` e outros do XML. **Não há** quilowatts, propulsão, categoria, eficiência, reciclabilidade nem desempenho estrutural.
- **`Cad_Classificacao_Mercadoria.Aliquota_Ipi`** e **`Cad_NCM_Ex_Tipi`**: o IPI da Tipi com vigência. Não guardam as Notas Complementares.
- **`Cad_Participante_Deficiencia`** e **`Cad_Parametro_Legal_Ibs_Cbs`**: o tipo de deficiência do participante, os limites de R$ 200.000,00 e R$ 100.000,00 e os intervalos de 2 e 3 anos do art. 149. **Não há** o reconhecimento do direito, a conferência da compra nem o controle da alienação.
- **`Cad_Veiculo_Transporte`**: o veículo de carga do transporte (placa, RNTRC); **não** é a ficha tributária do veículo vendido.

# 4. Achados e leituras minhas

- **O NCM sozinho não basta no veículo.** Você decidiu que o NCM é a base da segregação do IS (Q196-8). Continua valendo: o NCM dá o grupo, a alíquota-base e os fatores. O que o NCM não dá é a propulsão, os kW e os atestados, que são da **versão** (marca, modelo e versão do CAT). Por isso a ficha da versão é nova e o NCM ganha só o modo `composta_por_versao`.
- **A nota não substitui a ficha.** O XML traz cv, cm³ e o código de combustível do Denatran, que não distingue híbrido leve, completo e recarregável nem diz a norma de medição. A ficha guarda os kW pela norma certa e a nota fica como está; o Motor confere e avisa.
- **Divergência no desempenho estrutural.** A MP (Anexo II, critério 4) manda o benefício a quem "atende ao item 2 do Anexo IV" do Decreto; o Decreto (NC 87-13 e 87-14, critério 4) fala do "item 5". O item 2 lista os requisitos e o item 5 dá a redução a quem cumpre todos os dos Grupos A e B. Li como **a mesma exigência** e guardei um booleano; vai ao contador (C257).
- **Erro de remissão no Decreto.** A NC (87-14), critério 2, diz "ao atende item 3 do Anexo II"; o certo é Anexo III. Li como Anexo III.
- **O arredondamento não está dito para os veículos.** O Anexo V traz a alíquota final com uma casa decimal nas aeronaves e embarcações (6,5 × 1,04 = 6,76 aparece como 6,8) e deixa os veículos como "alíquota-base + ajustes" vezes 1,21, sem final. Por isso `Aliquota_Final_Aplicada` segue um parâmetro por empresa, padrão provisório **sem arredondar** (C256).
- **Posições fora das listas.** A NC (87-13) lista os códigos de 8703.21 a 8703.80, e a MP fala em "posição 87.03". Para 8703.10 e 8703.90 a tabela de propulsão pode não se aplicar (C259). A NC (87-14) lista códigos de 8704 com Ex; a MP lista posições e códigos inteiros.
- **Versão sem CAT.** Importação de veículo usado ou de versão ainda sem código no Renavam não tem como provar os atestados. Padrão provisório: critérios 2, 4 e 5 em "não atende", propulsão e kW informados no item (C260).
- **Caminhão e picape.** O PBT de 3.500 kg decide o caminhão, mas a picape fica de fora do conceito qualquer que seja o peso. A ficha guarda `Eh_Picape` e o PBT; o Motor decide a não incidência.
- **MP não convertida.** A MP vale por prazo constitucional e o art. 19 diz que ela permanece até a lei do art. 15; se perder a eficácia, os efeitos mudam. Toda linha entra provisória e com vigência de fim aberto (C265, Q204-8).
- **O documento 202 não muda de estrutura.** A alíquota `Al` do crédito presumido da Lei 9.826 vem da Tipi por NCM; a Nota Complementar do IPI faz a alíquota variar por versão até 2026 e o IPI é zero em 2027. O que a `Al` deve ser é a C252, agora com a C264.

# 5. Proposta

## 5.1 Domínios novos

- **`tecnologia_propulsao_veiculo`** (14 valores): elétrico, híbridos recarregáveis, completos e leves a flex-fuel/etanol, a gasolina e a diesel, etanol, flex-fuel, gasolina e diesel. Descrição de cada um com a definição da ABNT NBR 16567 (Decreto 12.549, Anexo II).
- **`categoria_veiculo_eficiencia`** (8 valores): as categorias do Anexo III do Decreto 12.549, item 1.

## 5.2 As seis entidades

| Entidade | Para quê | Vigência | Campos |
|-------------------------------|-----------------------------------------------------|---------|-------|
| `Cad_Veiculo_Versao` | A ficha técnica da versão do veículo (marca, modelo e versão do CAT/Renavam): o que a lei usa para graduar o Imposto Seletivo, o IPI até 2026 e as condições do art. | sim | 27 |
| `Cad_Veiculo_Versao_Sustentavel` | O registro de versão sustentável concedido pelo MDIC (Lei 14.902, art. | sim | 17 |
| `Cad_Is_Veiculo_Ajuste` | A tabela dos ajustes de alíquota por critério: as cinco tabelas dos Anexos II e III da MP 1.399 (Imposto Seletivo, desde 02/02/2027) e as das Notas Complementares NC (87-13) e NC (87-14) da Tipi (IPI, até 31/12/2026). | sim | 16 |
| `Mov_Is_Veiculo_Apuracao` | A memória do Imposto Seletivo (ou do IPI até 2026) de um item de veículo: cada ajuste lido, a alíquota inicial, os fatores, a alíquota final e a hipótese de alíquota zero ou de não incidência. | não | 22 |
| `Cad_Beneficio_Veiculo_Reconhecimento` | O direito reconhecido a quem compra automóvel com alíquota zero de IBS e CBS (art. | não | 16 |
| `Mov_Beneficio_Veiculo_Utilizacao` | A compra com o benefício: o item vendido, as condições conferidas (preço máximo, quatro portas, fabricação nacional, motorização do táxi, intervalo mínimo), o valor dispensado de IBS, CBS e IS e, se houver alienação antes do intervalo, o tributo que o alienante deve pagar (art. | não | 21 |

Em `Cad_Veiculo_Versao`, `Cad_Veiculo_Versao_Sustentavel` e `Cad_Is_Veiculo_Ajuste` valem as convenções da Fase 0: `ID_X` é a identidade, `ID_X_Versao` a chave da versão, e `Vigencia_Inicio`, `Vigencia_Fim` (31/12/9999 quando em aberto) e `Motivo_Vigencia` fecham cada linha. Nas outras três, que não têm vigência, o que muda de valor entra como linha nova (apuração, utilização) ou como atualização do registro (situação do reconhecimento).

### `Cad_Veiculo_Versao` (Contabilidade & Fiscal, com vigência, 27 campos)

A ficha técnica da versão do veículo (marca, modelo e versão do CAT/Renavam): o que a lei usa para graduar o Imposto Seletivo, o IPI até 2026 e as condições do art. 149 da LC 214. Liga-se ao produto vendido ou importado; a NCM do produto continua dando o grupo e a alíquota-base.

| Campo | Tipo | Descrição |
|---------------------|---------------------------------------|---------------------------------------|
| `ID_Veiculo_Versao` | identificador | Chave. |
| `ID_Veiculo_Versao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Veiculo_Versao_Versao). Fase 0, seção 2. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico) --- identidade | O produto (veículo) que a empresa fabrica, importa ou revende. A NCM dele dá o grupo do IS (Cad_NCM_Imposto_Seletivo). |
| `Codigo_Marca_Modelo` | código (até 6), opcional | O código de marca e modelo do Denatran/Senatran, o mesmo que a nota leva em `Veiculo_Codigo_Marca_Modelo`. |
| `Codigo_Versao_Cat` | código (até 20), opcional | A versão no CAT/Renavam (Decreto 12.549, Anexo IV, itens 4 e 5: o critério vale para o código de marca/modelo/versão). |
| `Numero_Cat` | código (até 30), opcional | Número do Certificado de Adequação à Legislação de Trânsito. |
| `ID_Categoria_Veiculo_Eficiencia` | referência (Cad_Classe_Sistema, domínio = categoria_veiculo_eficiencia) | A categoria do Anexo III do Decreto 12.549 (item 1), que decide qual fórmula de consumo energético vale (itens 5, 6 e 7). |
| `ID_Tecnologia_Propulsao` | referência (Cad_Classe_Sistema, domínio = tecnologia_propulsao_veiculo) | A fonte de energia e tecnologia de propulsão (critério 1): 14 valores, com as definições da ABNT NBR 16567 (Decreto 12.549, Anexo II). |
| `Potencia_Kw` | número | A potência do sistema de propulsão, em quilowatts, medida pela norma de `Norma_Medicao_Potencia`. Com dois combustíveis vale a mais alta (ISO 1585:2020). |
| `Norma_Medicao_Potencia` | enumeração {iso_1585_2020, unece_r85, gtr_21, metodologia_mdic} | Combustão interna: ISO 1585:2020; elétrico de motor único: UNECE R85; elétrico ou híbrido de motores múltiplos: UN GTR 21 ou metodologia do MDIC. |
| `Cilindrada_Cc` | número, opcional | Cilindrada do motor a combustão, em cm³. Entra na condição do táxi (art. 149, § 2º, I: até 2.000 cm³). |
| `Numero_Portas` | número, opcional | Número de portas, contando a de acesso ao bagageiro (art. 149, caput: no mínimo quatro). |
| `Massa_Ordem_Marcha_Kg` | número, opcional | Massa em ordem de marcha (ABNT NBR ISO 1176), base das fórmulas de consumo máximo CE2 e CE3. |
| `Peso_Bruto_Total_Kg` | número, opcional | Peso bruto total. Decide o caminhão (PBT de 3.500 kg ou mais, MP 1.399, art. 5º, § 1º, I). |
| `Consumo_Energetico_Mj_Km` | número, opcional | Consumo energético medido no ciclo combinado (dado do Ibama), guardado para conferir o nível informado. |
| `Nivel_Eficiencia_Energetica` | enumeração {item_2, item_3, nao_atende} | Atende ao item 2 do Anexo III do Decreto 12.549 (redução de 2 pontos), ao item 3 (1 ponto) ou a nenhum. |
| `Atende_Desempenho_Estrutural` | booleano | Cumpre, de série, todos os requisitos dos Grupos A e B do Anexo IV do Decreto 12.549, com a substituição pelo Grupo C quando regulamentada. A MP fala em "item 2" e o Decreto em "item 5" (C257). |
| `Nivel_Reciclabilidade` | enumeração {item_17_nivel_2, item_18_nivel_1, nao_atende} | Atende ao item 17 (nível 2: um veículo em fim de vida para cada cinco) ou ao item 18 (nível 1: um para cada dez) do Anexo III do Decreto 12.435. |
| `Eh_Picape` | booleano | Picape: compartimento de passageiros ligado de fábrica a área aberta de carga, qualquer que seja o PBT. A picape nunca é caminhão (MP 1.399, art. 5º, § 1º, II). |
| `Uso_Operacional_Forcas_Seguranca` | booleano | Versão com características técnicas para uso operacional exclusivo das Forças Armadas ou dos órgãos de segurança pública (MP 1.399, art. 5º, II e § 2º): o IS não incide. |
| `Documento_Comprovacao` | texto, opcional | Onde está a prova: CAT, laudo do Ibama, atestado do fabricante. |
| `Fundamento_Legal` | texto, opcional | Artigos que sustentam os níveis informados. |
| `Situacao_Dado` | enumeração {provisorio, validado} | Como nos parâmetros legais: a ficha entra provisória até o contador ou o responsável técnico validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Veiculo_Versao_Sustentavel` (Contabilidade & Fiscal, com vigência, 17 campos)

O registro de versão sustentável concedido pelo MDIC (Lei 14.902, art. 11; Decreto 12.549, art. 4º). Dá alíquota zero de IS (MP 1.399, art. 4º, II) e, até 31/12/2026, IPI zero (NC 87-15).

| Campo | Tipo | Descrição |
|-----------------------|---------------------------------------|---------------------------------------|
| `ID_Veiculo_Versao_Sustentavel` | identificador | Chave. |
| `ID_Veiculo_Versao_Sustentavel_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Veiculo_Versao_Sustentavel_Versao). |
| `ID_Veiculo_Versao` | referência (Cad_Veiculo_Versao) --- identidade | A versão registrada. O registro é pedido por marca e modelo (Decreto 12.549, art. 4º, I); aqui fica por versão para a conta do item. |
| `Numero_Registro_Mdic` | código (até 40) | Número do registro concedido pelo MDIC. |
| `Data_Registro` | data | Data do registro. |
| `Numero_Ato_Compromissos` | código (até 40), opcional | O ato de registro dos compromissos do art. 2º, § 2º, da Lei 14.902, exigido pelo art. 4º, II, do Decreto. |
| `Emissao_Co2_Poco_Roda_G_Km` | número | Emissão de CO₂ do poço à roda, em g/km. O limite do Decreto é 83. |
| `Percentual_Reciclabilidade` | número | Reciclabilidade ou reutilização de materiais. O mínimo do Decreto é 80%. |
| `Atende_Etapas_Fabris_Pais` | booleano | Cumpre o Processo Produtivo Básico: estampagem de painéis externos, soldagem, pintura, fabricação de motor e montagem. |
| `Categoria_Sustentavel` | enumeração {subcompacto, compacto, utilitario_esportivo_compacto, picape_compacta, outra} | A categoria exigida pelo Decreto: subcompacto, compacto, utilitário esportivo compacto ou picape compacta. `outra` não dá o benefício. |
| `Situacao_Registro` | enumeração {ativo, suspenso, cancelado} | Só o registro ativo dá o benefício. |
| `Fundamento_Legal` | texto, opcional | Lei 14.902, art. 11; Decreto 12.549, arts. 4º e 6º; MP 1.399, art. 4º, II. |
| `Situacao_Dado` | enumeração {provisorio, validado} | O ato do MDIC sobre o requerimento ainda não está no Projeto (Q204-11). |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Is_Veiculo_Ajuste` (Contabilidade & Fiscal, com vigência, 16 campos)

A tabela dos ajustes de alíquota por critério: as cinco tabelas dos Anexos II e III da MP 1.399 (Imposto Seletivo, desde 02/02/2027) e as das Notas Complementares NC (87-13) e NC (87-14) da Tipi (IPI, até 31/12/2026). Os valores são idênticos; muda o imposto e a vigência.

| Campo | Tipo | Descrição |
|-------------------|-----------------------------------------|-----------------------------------------|
| `ID_Is_Veiculo_Ajuste` | identificador | Chave. |
| `ID_Is_Veiculo_Ajuste_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Is_Veiculo_Ajuste_Versao). |
| `ID_Imposto` | referência (Cad_Imposto, Fase 0) --- identidade | Imposto Seletivo ou IPI. |
| `Tabela_Ajuste` | enumeração {tabela_87_03, tabela_8704} --- identidade | Anexo II da MP (NC 87-13) para a posição 87.03; Anexo III (NC 87-14) para as posições 8704 listadas. |
| `Criterio` | enumeração {propulsao, eficiencia_energetica, potencia, desempenho_estrutural, reciclabilidade} --- identidade | Os cinco critérios. |
| `ID_Tecnologia_Propulsao` | referência (Cad_Classe_Sistema, domínio = tecnologia_propulsao_veiculo), opcional --- identidade | Só no critério propulsão. |
| `Nivel_Chave` | código (até 30), opcional --- identidade | O nível dos critérios de eficiência (`item_2`, `item_3`, `nao_atende`), desempenho estrutural (`atende`, `nao_atende`) e reciclabilidade (`item_17_nivel_2`, `item_18_nivel_1`, `nao_atende`). |
| `Potencia_Ate_Kw` | número, opcional | Limite superior da faixa de potência, inclusive. Vazio na última faixa. |
| `Faixa_Aberta_Superior` | booleano | Verdadeiro na linha "acima de 290 kW", que não tem limite superior. |
| `Ajuste_Pontos` | número | O ajuste, em pontos percentuais (negativo reduz). |
| `Fundamento_Legal` | texto | O anexo e o artigo (por exemplo, "MP 1.399/2026, Anexo II, critério 3"). |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória: a MP precisa ser convertida e o contador valida (C265). |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Is_Veiculo_Apuracao` (Contabilidade & Fiscal, sem vigência, 22 campos)

A memória do Imposto Seletivo (ou do IPI até 2026) de um item de veículo: cada ajuste lido, a alíquota inicial, os fatores, a alíquota final e a hipótese de alíquota zero ou de não incidência. A linha de `Mov_Apuracao_Tributo_Item` guarda o resultado; esta guarda a conta.

| Campo | Tipo | Descrição |
|---------------------|----------------------------------------|----------------------------------------|
| `ID_Is_Veiculo_Apuracao` | identificador | Chave. |
| `ID_Apuracao` | referência (Mov_Apuracao_Tributo_Item) | A linha de apuração do item que recebeu o resultado. |
| `ID_Veiculo_Versao` | referência (Cad_Veiculo_Versao) | A ficha usada, na versão vigente na data do fato gerador. |
| `ID_NCM_Imposto_Seletivo` | referência (Cad_NCM_Imposto_Seletivo) | A linha da NCM que deu a alíquota-base e os fatores. |
| `ID_Veiculo_Versao_Sustentavel` | referência (Cad_Veiculo_Versao_Sustentavel), opcional | O registro usado quando a hipótese é a versão sustentável. |
| `ID_Beneficio_Veiculo_Utilizacao` | referência (Mov_Beneficio_Veiculo_Utilizacao), opcional | A utilização do benefício do art. 149, quando a hipótese é PcD, TEA ou táxi. |
| `Data_Fato_Gerador` | data | Data que escolhe as linhas vigentes. |
| `Operacao` | enumeração {saida_fabricante, importacao} | Na importação entra o fator de ajuste. |
| `Aliquota_Base_Anexo` | número | A alíquota-base do Anexo I (6,3 ou 3,9). |
| `Ajuste_Propulsao` | número | Pontos do critério 1. |
| `Ajuste_Eficiencia` | número | Pontos do critério 2. |
| `Ajuste_Potencia` | número | Pontos do critério 3. |
| `Ajuste_Desempenho_Estrutural` | número | Pontos do critério 4. |
| `Ajuste_Reciclabilidade` | número | Pontos do critério 5. |
| `Aliquota_Inicial` | número | Base mais ajustes, com o piso de zero (Decreto 12.549, art. 3º, parágrafo único, por remissão da MP, art. 3º, § 2º, I). |
| `Fator_Conversao` | número | O fator do Anexo V (1,21 nos veículos). |
| `Fator_Ajuste_Importacao` | número, opcional | O fator do art. 8º (1,17), cumulativo com o de conversão. Vazio na saída do fabricante. |
| `Aliquota_Final_Aplicada` | número | Inicial × conversão × importação, com o arredondamento do parâmetro da empresa (C256). |
| `Potencia_Kw_Usada` | número | A potência que escolheu a faixa, copiada da ficha. |
| `Hipotese_Excecao` | enumeração {nenhuma, aliquota_zero_pcd_tea, aliquota_zero_taxi, aliquota_zero_versao_sustentavel, aliquota_zero_nota_complementar_tipi, reducao_50_nota_complementar_tipi, nao_incide_caminhao, nao_incide_uso_operacional} | Quando diferente de `nenhuma`, a alíquota final é zero (ou 50% na nota 88-2) ou o imposto não incide, e o item guarda o motivo. |
| `Dados_Provisorios` | booleano | Verdadeiro se alguma linha usada está `provisorio`: o relatório avisa. |
| `Memoria_Calculo` | texto | O texto da conta, para auditoria. |

### `Cad_Beneficio_Veiculo_Reconhecimento` (Contabilidade & Fiscal, sem vigência, 16 campos)

O direito reconhecido a quem compra automóvel com alíquota zero de IBS e CBS (art. 149 da LC 214): o táxi, a pessoa com deficiência e a pessoa com transtorno do espectro autista. O mesmo reconhecimento dá alíquota zero de IS (MP 1.399, art. 4º, I). O reconhecimento é pela administração estadual ou distrital do domicílio e pela RFB (art. 153).

| Campo | Tipo | Descrição |
|----------------------|---------------------------------------|---------------------------------------|
| `ID_Beneficio_Veiculo_Reconhecimento` | identificador | Chave. |
| `ID_Participante` | referência (Cad_Participante) | O adquirente beneficiário. |
| `Tipo_Beneficio` | enumeração {taxi, pessoa_com_deficiencia, transtorno_espectro_autista} | O inciso do art. 149. |
| `ID_Deficiencia` | referência (Cad_Participante_Deficiencia), opcional | A deficiência cadastrada, nos dois últimos tipos. |
| `Tipo_Laudo` | enumeração {servico_publico_saude, servico_privado_sus, detran_clinica_credenciada}, opcional | Quem emitiu o laudo (art. 151). Vazio no táxi. |
| `Numero_Laudo` | código (até 40), opcional | Número do laudo. |
| `Data_Laudo` | data, opcional | Data do laudo. |
| `Numero_Autorizacao_Taxi` | código (até 40), opcional | Autorização, permissão ou concessão do poder público ao motorista profissional (art. 149, I). |
| `Numero_Reconhecimento_Rfb` | código (até 40) | O reconhecimento pela RFB (art. 153). |
| `Data_Reconhecimento_Rfb` | data | Data. |
| `ID_Estado_Reconhecimento` | referência (Cad_Estado), opcional | O estado ou o Distrito Federal do domicílio. |
| `Numero_Reconhecimento_Estadual` | código (até 40), opcional | O reconhecimento da administração estadual ou distrital. |
| `Data_Reconhecimento_Estadual` | data, opcional | Data. |
| `ID_Participante_Representante` | referência (Cad_Participante), opcional | Representante legal ou mandatário, solidariamente responsável (art. 149, §§ 4º e 5º). |
| `Situacao` | enumeração {reconhecido, utilizado, cancelado} | `utilizado` depois da compra; o intervalo mínimo é conferido na utilização. |
| `Observacao` | texto, opcional | Livre. |

### `Mov_Beneficio_Veiculo_Utilizacao` (Contabilidade & Fiscal, sem vigência, 21 campos)

A compra com o benefício: o item vendido, as condições conferidas (preço máximo, quatro portas, fabricação nacional, motorização do táxi, intervalo mínimo), o valor dispensado de IBS, CBS e IS e, se houver alienação antes do intervalo, o tributo que o alienante deve pagar (art. 155).

| Campo | Tipo | Descrição |
|----------------------|---------------------------------------|---------------------------------------|
| `ID_Beneficio_Veiculo_Utilizacao` | identificador | Chave. |
| `ID_Beneficio_Veiculo_Reconhecimento` | referência (Cad_Beneficio_Veiculo_Reconhecimento) | O direito usado. |
| `ID_Nota_Fiscal_Saida_Item` | referência (Mov_Nota_Fiscal_Saida_Item), opcional | O item da venda. |
| `ID_Veiculo_Versao` | referência (Cad_Veiculo_Versao) | A versão comprada: dela vêm portas, cilindrada e propulsão. |
| `Data_Aquisicao` | data | Conta o intervalo do art. 152 (2 anos no táxi, 3 anos na PcD e no TEA). |
| `Preco_Venda_Consumidor` | número, opcional | Preço ao consumidor com os tributos que incidiriam sem a redução e sem a adaptação (art. 149, § 2º, II). Só PcD e TEA. |
| `Valor_Operacao` | número | Valor da operação. |
| `Valor_Base_Beneficio` | número | O valor da operação limitado ao teto do benefício (R$ 100.000,00 na PcD e no TEA; `Cad_Parametro_Legal_Ibs_Cbs`). |
| `Atende_Preco_Maximo` | booleano, opcional | Preço de venda até R$ 200.000,00 (PcD e TEA). |
| `Atende_Quatro_Portas` | booleano | No mínimo quatro portas, com a de acesso ao bagageiro. |
| `Atende_Fabricacao_Nacional` | booleano | Automóvel de passageiros de fabricação nacional. |
| `Atende_Motorizacao_Taxi` | booleano, opcional | Elétrico, ou cilindrada até 2.000 cm³ e combustível renovável, sistema reversível ou híbrido (art. 149, § 2º, I). Só táxi. |
| `Atende_Intervalo_Minimo` | booleano | Passou o intervalo desde a compra anterior com o benefício. |
| `Perda_Total_Furto_Roubo` | booleano | Perda total, furto ou roubo do automóvel anterior: o benefício vale a qualquer tempo (art. 152, parágrafo único). |
| `Valor_Ibs_Cbs_Dispensado` | número | IBS e CBS que seriam devidos sem o benefício. |
| `Valor_Is_Dispensado` | número, opcional | IS que seria devido sem a alíquota zero. |
| `Data_Alienacao` | data, opcional | Venda do automóvel pelo beneficiário. |
| `Alienacao_Antecipada` | booleano, opcional | Alienação antes do intervalo, a quem não tem o reconhecimento (art. 155). |
| `Excecao_Alienacao` | enumeração {nenhuma, seguradora_perda_total, falecimento_beneficiario, alienacao_fiduciaria}, opcional | Os casos do art. 155, § 2º, em que não se cobra. |
| `Valor_Tributo_A_Recolher_Alienante` | número, opcional | Os tributos dispensados, atualizados, mais multa e juros (art. 155, caput e § 1º). |
| `Observacao` | texto, opcional | Livre. |


## 5.3 O que muda em entidades que já existem

| Entidade | Campo novo | Para quê |
|--------------------|---------------------------------------|-----------------------------------------|
| `Cad_NCM_Imposto_Seletivo` | `Modo_Aliquota` (enumeração {fixa, composta_por_versao}) | `fixa`: vale `Aliquota_Ad_Valorem` (aeronaves, embarcações). `composta_por_versao`: o Motor monta a alíquota pelos ajustes da ficha do veículo. |
| `Cad_NCM_Imposto_Seletivo` | `Aliquota_Inicial` (número, opcional) | Alíquota-base do Anexo I (veículos) ou inicial do Anexo V (aeronaves e embarcações). |
| `Cad_NCM_Imposto_Seletivo` | `Fator_Conversao` (número, opcional) | Fator do Anexo V (1,21; 1,04; 1,20). |
| `Cad_NCM_Imposto_Seletivo` | `Fator_Ajuste_Importacao` (número, opcional) | Fator do art. 8º (1,17 para veículos, aeronaves e embarcações), cumulativo. |
| `Cad_NCM_Imposto_Seletivo` | `Tabela_Ajuste` (enumeração {tabela_87_03, tabela_8704}, opcional) | Qual tabela de ajustes vale (só nos veículos). |
| `Cad_NCM_Imposto_Seletivo` | `Aliquota_Minima` (número, opcional) | Piso depois dos ajustes (zero). |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Veiculo_Versao` (referência (Cad_Veiculo_Versao), opcional) | A ficha do veículo do item. A nota continua levando os campos do XML (cv, cm³, combustível); o Motor confere kW contra cv e avisa. |
| `Mov_Nota_Fiscal_Entrada_Item` | `ID_Veiculo_Versao` (referência (Cad_Veiculo_Versao), opcional) | Idem, na entrada do importador ou do revendedor. |

`Cad_NCM_Imposto_Seletivo` continua sendo a fonte única da alíquota e do grupo (Q196-8): nos veículos, o `Aliquota_Ad_Valorem` fica vazio e o Motor monta a alíquota; nas aeronaves e embarcações, vale o final publicado. As 10 linhas de carga:

| NCM | Descrição | Modo | Alíquota inicial | Fator de conversão | Final | Tabela |
|--------|-------------------------------------|-------------|-----------|-------------|--------|---------|
| 8703 | Veículos da posição 87.03 | composta por versao | 6,3 | 1,21 | (calculada) | tabela_87_03 |
| 8704.21 | Posição 8704.21 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8704.31 | Posição 8704.31 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8704.41.00 | Código 8704.41.00 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8704.51.00 | Código 8704.51.00 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8704.60.00 | Código 8704.60.00 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8704.90.00 | Código 8704.90.00 | composta por versao | 3,9 | 1,21 | (calculada) | tabela_8704 |
| 8802 | Aeronaves da posição 88.02, exceto o código 8802.60.00 | fixa | 6,5 | 1,04 | 6,8 | --- |
| 8903.3 | Barcos a motor da subposição 8903.3 | fixa | 10 | 1,2 | 12,0 | --- |
| 8903 | Demais embarcações de recreio ou de esporte, a motor, da posição 89.03 (exceto a subposição 8903.3) | fixa | 6,5 | 1,2 | 7,8 | --- |

Observação: nas aeronaves, a 8802.60.00 fica de fora (nave espacial); e na 89.03 as demais embarcações excluem a subposição 8903.3, tratada na linha própria. Uso `Ex_Descricao` onde o corte é parcial.

## 5.4 Como o IS do veículo é calculado

- **1.** O fato gerador é a saída do fabricante ou o desembaraço na importação (arts. 412 e 434 da LC 214); a data escolhe as linhas vigentes.
- **2.** O NCM do item acha a linha de `Cad_NCM_Imposto_Seletivo`. Se `Modo_Aliquota = fixa`, vale a alíquota final publicada e o passo 7 (importação) se aplica. Se `composta_por_versao`, segue.
- **3.** O item aponta a ficha (`ID_Veiculo_Versao`). Sem ficha, o Motor não calcula e devolve pendência (como na alíquota do ISS), exceto no caso do parâmetro de versão sem CAT.
- **4.** Para cada critério o Motor lê a linha de `Cad_Is_Veiculo_Ajuste` da tabela da NCM (`tabela_87_03` ou `tabela_8704`): propulsão pelo domínio da ficha; eficiência, desempenho estrutural e reciclabilidade pelo nível; potência pela primeira faixa cujo limite superior é maior ou igual aos kW da ficha.
- **5.** Alíquota inicial = alíquota-base + soma dos cinco ajustes, **não menor que zero**.
- **6.** Alíquota final = inicial × fator de conversão (1,21) e, na importação, × fator de ajuste (1,17), cumulativos (MP, art. 8º, § 2º).
- **7.** Antes de aplicar, o Motor confere as exceções, na ordem: não incidência (caminhão e uso operacional); alíquota zero do art. 4º (reconhecimento do art. 149, registro de versão sustentável) e das notas transitórias; só então a alíquota final.
- **8.** A base é a do art. 414 (valor de venda; na importação, valor aduaneiro mais imposto de importação), que a Q196-9 já trata.

**Exemplos** (cálculo meu, com os valores do Anexo II; conferir no Anexo A):

| Veículo (87.03) | Conta | Alíquota |
|--------------------------------------------------|-----------------------------------------|---------|
| Gasolina, 100 kW, nenhum atestado | 6,3 + 6,5 (propulsão) + 0,75 (potência) = 13,55; × 1,21 | **16,3955%** |
| Elétrico, 80 kW, eficiência item 2, estrutural sim, reciclabilidade item 17 | 6,3 − 2 − 2 + 0 − 1 − 2 = −0,7, piso zero; × 1,21 | **0%** |
| Flex-fuel, 85 kW, eficiência item 3, estrutural sim, reciclabilidade item 18 | 6,3 + 0 − 1 + 0 − 1 − 1 = 3,3; × 1,21 | **3,993%** |
| O mesmo, importado | 3,3 × 1,21 × 1,17 | **4,6718%** |

## 5.5 IPI até 31/12/2026

A mesma conta, sem o fator de conversão: alíquota da Tipi (`Cad_Classificacao_Mercadoria.Aliquota_Ipi` ou `Cad_NCM_Ex_Tipi`) mais os cinco ajustes das linhas com `ID_Imposto = IPI`, piso zero (Decreto 12.549, art. 3º, parágrafo único); com registro de versão sustentável ativo, a NC (87-15) zera. As linhas de IPI terminam em 31/12/2026; o Motor, depois dessa data, só as lê para operação anterior (retificação de até cinco anos). A partir de 2027 o IPI do veículo é zero (LC 214, art. 454), sem regra nova. O resultado também grava `Mov_Is_Veiculo_Apuracao`, com a linha de apuração do IPI.

## 5.6 Benefício do art. 149

- O **reconhecimento** (`Cad_Beneficio_Veiculo_Reconhecimento`) é cadastrado uma vez por beneficiário e direito; o Motor só o aceita se houver número do reconhecimento da RFB e, quando a administração estadual o exigir, o do estado.
- Na **venda**, `Mov_Beneficio_Veiculo_Utilizacao` guarda as conferências: quatro portas e cilindrada (da ficha), fabricação nacional (da origem do item), preço máximo e teto de R$ 100.000,00 (do parâmetro vigente), motorização do táxi (propulsão da ficha: elétrico, ou cilindrada até 2.000 cm³ e propulsão renovável, reversível ou híbrida) e intervalo desde a compra anterior. Falhou uma conferência, o Motor **não dá a alíquota zero** e avisa; o usuário pode registrar a decisão do responsável.
- Na **alienação** antes do intervalo, a linha guarda a data, a exceção do art. 155, § 2º, e o tributo a recolher pelo alienante.
- O mesmo reconhecimento vale para o IS: a utilização guarda `Valor_Is_Dispensado` e a apuração do IS usa a hipótese `aliquota_zero_pcd_tea` ou `aliquota_zero_taxi`.

## 5.7 Versão sustentável

O registro ativo de `Cad_Veiculo_Versao_Sustentavel` dá IS zero (MP, art. 4º, II) e IPI zero até 2026 (NC 87-15) quando: CO₂ do poço à roda até 83 g/km, reciclabilidade de pelo menos 80%, etapas fabris no País e categoria subcompacto, compacto, utilitário esportivo compacto ou picape compacta. O Motor compara os campos com esses limites (carga como parâmetros legais) e avisa se o registro está ativo mas um limite não é cumprido.

## 5.8 Parâmetros por empresa e documentação (regra do documento 201)

| Parâmetro | Padrão provisório | De onde vem | Efeito documentado |
|------------------------|-------------------------|----------|-----------------------------------------|
| `is_veiculo_arredondamento_casas` | sem arredondar | C256 | Apuração do IS do item; resultado em `Mov_Apuracao_Tributo_Item` |
| `is_veiculo_item_sem_cat` | critérios 2, 4 e 5 em "não atende" | C260 | Idem |
| `is_veiculo_kw_derivado_do_cv` | não deriva (kW da ficha) | C258 | Conferência da nota e da ficha |
| `is_veiculo_tabela_fora_da_lista` | aplica a tabela da posição | C259 | Escolha da tabela de ajustes |

A obrigação em que o IS é declarado ainda não está no Projeto (C262); ECD e ECF ficam sem efeito documentado até lá. As 4 linhas entram no catálogo central com a documentação de efeito, como nos documentos 201 e 202.

# 6. Regras de texto: o que o Motor avisa

- **Ficha ausente:** item de NCM `composta_por_versao` sem `ID_Veiculo_Versao` não calcula e vira pendência.
- **kW e cv:** `Potencia_Kw` × 1,35962 diferente de `Veiculo_Potencia_Cv` da nota em mais de 2%: aviso.
- **Cilindrada:** `Cilindrada_Cc` da ficha diferente de `Veiculo_Cilindrada_Cc` da nota: aviso.
- **Combustível:** código do Denatran da nota incompatível com a propulsão da ficha (por exemplo, diesel na nota e gasolina na ficha): aviso.
- **Linha provisória:** cálculo que usou linha `provisorio` marca `Dados_Provisorios` e entra no relatório de pendências.
- **Atestado sem prova:** nível de eficiência, desempenho ou reciclabilidade diferente de "não atende" sem `Documento_Comprovacao`: aviso.
- **Versão sustentável:** registro ativo com limite não cumprido, ou suspenso e cancelado depois da venda: aviso.
- **Caminhão:** PBT de 3.500 kg ou mais, sem `Eh_Picape`, em posição 8704: o IS não incide; o Motor grava a hipótese e avisa se a NCM é de comercial leve.
- **Art. 149:** condição não cumprida, intervalo menor que o mínimo sem perda total, furto ou roubo, ou limite desatualizado depois de 1º de janeiro: aviso e alíquota normal.
- **IPI depois de 2026:** linha de IPI do veículo usada com fato gerador a partir de 01/01/2027: aviso (zero, art. 454).
- **Fim da MP:** se as linhas de MP forem encerradas sem substituta, o Motor deixa de calcular o IS dos veículos e devolve pendência.

# 7. Perguntas

| Id | Pergunta | Recomendação |
|-----------|-----------------------------------------------------------------------|-----------------|
| Q204-1 | Aprova o **escopo** do documento 204: a tributação do veículo por propulsão, potência e demais critérios no **Imposto Seletivo** (veículos, aeronaves e embarcações dos Anexos I, II, III e V da MP 1.399), no **IPI até 31/12/2026** e nas condições do **art. 149 da LC 214** (táxi, PcD e TEA), com **seis entidades novas**, 8 campos em entidades existentes e 2 domínios? Bebidas, fumígenos e minerais (Anexos IV e VI) ficam para outro documento. | Sim |
| Q204-2 | Aprova a **ficha da versão do veículo** (`Cad_Veiculo_Versao`, 27 campos, com vigência) e o **registro de versão sustentável** (`Cad_Veiculo_Versao_Sustentavel`, 17 campos), com a ficha ligada ao produto e a nota continuando a levar os campos do XML? | Sim |
| Q204-3 | Aprova a **tabela de ajustes** (`Cad_Is_Veiculo_Ajuste`, 16 campos, com vigência) e a **carga provisória de 124 linhas**: 62 do Imposto Seletivo (desde 02/02/2027) e 62 do IPI (de 01/11/2025 a 31/12/2026)? | Sim |
| Q204-4 | Aprova os **6 campos novos** de `Cad_NCM_Imposto_Seletivo` (modo da alíquota, inicial, fator de conversão, fator de importação, tabela e piso) e as **10 linhas provisórias** de NCM (veículos 87.03 e 8704, aeronaves e embarcações), mantendo o NCM como base, como você decidiu na Q196-8? | Sim |
| Q204-5 | Aprova a **apuração do item de veículo** (`Mov_Is_Veiculo_Apuracao`, 22 campos) e a **regra de cálculo** da seção 5.4: base + cinco ajustes, piso de zero, fator 1,21, fator 1,17 na importação, as oito hipóteses de alíquota zero e de não incidência e a memória da conta? | Sim |
| Q204-6 | Aprova o **reconhecimento e a utilização do benefício do art. 149** (`Cad_Beneficio_Veiculo_Reconhecimento`, 16 campos, e `Mov_Beneficio_Veiculo_Utilizacao`, 21), com o intervalo mínimo, o preço máximo, as quatro portas, a motorização do táxi e a alienação antecipada? A alternativa é deixar o art. 149 só nos parâmetros que já existem. | Sim |
| Q204-7 | Aprova `ID_Veiculo_Versao` nos itens da nota de saída e de entrada (2 campos) e o aviso do Motor quando os cavalos da nota (`Veiculo_Potencia_Cv`) não batem com os quilowatts da ficha (1 cv = 0,7355 kW)? | Sim |
| Q204-8 | Aceita a **carga provisória e visível**: toda linha de MP nasce `provisorio`, com o fundamento "MP 1.399/2026", sem fim de vigência, e o relatório do Motor avisa quando um cálculo usa linha provisória, até a MP ser convertida (C265)? | Sim |
| Q204-9 | Aprova os **4 parâmetros por empresa** da seção 5.8 (arredondamento da alíquota, item sem CAT, kW derivado do cv e tabela para posições fora da lista), com padrão provisório, aviso a cada uso e a documentação de efeito da regra do documento 201? | Sim |
| Q204-10 | Mantém o documento 202 **como está** (nada muda nas oito entidades) e trata a alíquota `Al` do crédito presumido (C252, C264) depois que o contador responder? A alternativa é rever o documento 202 antes das suas respostas. | Manter |
| Q204-11 | Envia, quando puder, os textos que **não li**: o texto **atual** das Notas Complementares da Tipi 87-2, 88-1, 88-2 e 89-1 (alíquota zero transitória do art. 6º da MP; os Decretos 4.186/2002 e 8.168/2013 que você enviou foram revogados e só mostram a origem; a 89-1 não veio), o Anexo XVII da LC 214 com as posições, o ato do MDIC sobre o registro de versão sustentável e o Decreto 9.557/2018 (itens que o Decreto 12.549 mantém, art. 7º, parágrafo único)? | Enviar |

# 8. O que acontece se você aprovar

- 1.171 entidades (+6), 13.331 campos (+127: 119 nas seis entidades e 8 nas três existentes), 3.468 campos de referência (+23), 357 domínios (+2, com 22 valores), sobre a revisão 38. Com o documento 202 aprovado, 1.179 entidades e 13.463 campos.
- Carga: 124 linhas de ajuste (todas provisórias), 10 de NCM, 22 de domínio e 4 do catálogo de parâmetros.
- Os documentos 14 (D-N540) e 38 (seção 1.32) acompanham; o documento 188 ganha a Parte 12 (C256 a C265).
- Nada entra no dicionário antes de você responder e pedir "consolidar".

# 9. Limites

- **Não li:** o texto **atual** das Notas Complementares da Tipi 87-2, 88-1, 88-2 e 89-1 (só tenho os textos antigos e revogados da 87-2, da 88-1 e da 88-2, nos Decretos 8.168/2013 e 4.186/2002; da 89-1 não tenho nada), o Anexo XVII da LC 214 (a lista legal), o Decreto 9.557/2018 (itens que o Decreto 12.549 mantém), o ato do MDIC sobre o registro de versão sustentável, o texto do art. 126 do ADCT e a Tipi vigente por código (as alíquotas de IPI de cada código).
- **Fora do escopo:** o IS de bebidas, fumígenos e minerais (Anexos IV e VI da MP) e o valor de referência (art. 414, § 2º). A tabela `Cad_NCM_Imposto_Seletivo` com os campos novos já os comporta; o desenho fica para outro documento.
- **Fórmula do art. 8º, § 4º:** o fator de ajuste vem por imagem no PDF e não foi lido; a MP já traz o valor 1,17 e o decreto pode reduzi-lo.
- **Os cálculos de exemplo** são meus, com os valores dos anexos; a conta oficial é a do contador.
- **O sistema não decide** o enquadramento técnico (eficiência, desempenho estrutural, reciclabilidade): quem informa é o responsável técnico do fabricante ou do importador, com a prova.

# Anexo A. Tabelas de ajuste (valores da MP 1.399, Anexos II e III)

## A.1 Posição 87.03 (Anexo II da MP; NC 87-13 do IPI)

| Critério | Nível | Ajuste (pontos percentuais) |
|----------------------------|----------------------------------------|-------------------------------|
| 1. Propulsão | Elétrico | -2 |
| 1. Propulsão | Híbrido recarregável flex-fuel/etanol | -2 |
| 1. Propulsão | Híbrido completo flex-fuel/etanol | -1,5 |
| 1. Propulsão | Híbrido leve flex-fuel/etanol | -1 |
| 1. Propulsão | Etanol | -0,5 |
| 1. Propulsão | Flex-fuel | 0 |
| 1. Propulsão | Híbrido recarregável gasolina | 2 |
| 1. Propulsão | Híbrido completo gasolina | 3 |
| 1. Propulsão | Híbrido leve gasolina | 4,5 |
| 1. Propulsão | Híbrido recarregável diesel | 3 |
| 1. Propulsão | Híbrido completo diesel | 4 |
| 1. Propulsão | Híbrido leve diesel | 5,5 |
| 1. Propulsão | Gasolina | 6,5 |
| 1. Propulsão | Diesel | 12 |
| 2. Eficiência energética | item 2 | -2 |
| 2. Eficiência energética | item 3 | -1 |
| 2. Eficiência energética | nao atende | 0 |
| 3. Potência | até 55 kW | -2,15 |
| 3. Potência | até 66 kW | -1,75 |
| 3. Potência | até 72 kW | -0,25 |
| 3. Potência | até 85 kW | 0 |
| 3. Potência | até 105 kW | 0,75 |
| 3. Potência | até 132 kW | 1,5 |
| 3. Potência | até 165 kW | 3 |
| 3. Potência | até 200 kW | 3,5 |
| 3. Potência | até 240 kW | 4 |
| 3. Potência | até 290 kW | 6,25 |
| 3. Potência | acima de 290 kW | 6,5 |
| 4. Desempenho estrutural | atende | -1 |
| 4. Desempenho estrutural | nao atende | 0 |
| 5. Reciclabilidade | item 17 nivel 2 | -2 |
| 5. Reciclabilidade | item 18 nivel 1 | -1 |
| 5. Reciclabilidade | nao atende | 0 |


## A.2 Posições 8704 listadas (Anexo III da MP; NC 87-14 do IPI)

| Critério | Nível | Ajuste (pontos percentuais) |
|----------------------------|----------------------------------------|-------------------------------|
| 1. Propulsão | Elétrico | -2 |
| 1. Propulsão | Híbrido recarregável flex-fuel/etanol | -2 |
| 1. Propulsão | Híbrido completo flex-fuel/etanol | -1,5 |
| 1. Propulsão | Híbrido leve flex-fuel/etanol | -1 |
| 1. Propulsão | Etanol | -0,5 |
| 1. Propulsão | Flex-fuel | 0 |
| 1. Propulsão | Híbrido recarregável gasolina | 0,5 |
| 1. Propulsão | Híbrido completo gasolina | 1 |
| 1. Propulsão | Híbrido leve gasolina | 1,75 |
| 1. Propulsão | Híbrido recarregável diesel | 1 |
| 1. Propulsão | Híbrido completo diesel | 1,5 |
| 1. Propulsão | Híbrido leve diesel | 2 |
| 1. Propulsão | Gasolina | 2,25 |
| 1. Propulsão | Diesel | 2,5 |
| 2. Eficiência energética | item 2 | -2 |
| 2. Eficiência energética | item 3 | -1 |
| 2. Eficiência energética | nao atende | 0 |
| 3. Potência | até 85 kW | -0,25 |
| 3. Potência | até 105 kW | 0 |
| 3. Potência | até 132 kW | 0,25 |
| 3. Potência | até 165 kW | 0,5 |
| 3. Potência | até 240 kW | 1 |
| 3. Potência | até 290 kW | 2 |
| 3. Potência | acima de 290 kW | 3 |
| 4. Desempenho estrutural | atende | -1 |
| 4. Desempenho estrutural | nao atende | 0 |
| 5. Reciclabilidade | item 17 nivel 2 | -2 |
| 5. Reciclabilidade | item 18 nivel 1 | -1 |
| 5. Reciclabilidade | nao atende | 0 |


Nos dois anexos: eficiência `item_2` atende ao item 2 do Anexo III do Decreto 12.549 (consumo energético menor ou igual a CE2 = a + b × massa em ordem de marcha, por categoria), `item_3` ao item 3 (CE3); reciclabilidade `item_17_nivel_2` e `item_18_nivel_1` são os itens 17 e 18 do Anexo III do Decreto 12.435.

# Anexo B. Carga (pasta `Carga204`)

- `cad_is_veiculo_ajuste.csv`: 124 linhas (62 de IS com vigência de 02/02/2027 a 31/12/9999; 62 de IPI de 01/11/2025 a 31/12/2026). Todas `provisorio`.
- `cad_ncm_imposto_seletivo_veiculos_aeronaves_embarcacoes.csv`: 10 linhas.
- `dominios.csv`: 22 valores de 2 domínios.
- `LEIA-ME.txt`.

# Anexo C. Documentação dos 4 parâmetros por empresa

Ver a seção 5.8. Efeito: apuração do IS do item (e do IPI até 2026). Obrigação: IS ainda sem obrigação acessória no Projeto (C262); ECD, ECF e DCTFWeb sem efeito documentado.

# Anexo D. Perguntas ao contador (C256 a C265, documento 188, Parte 12)

- **C256** Arredondamento da alíquota final do IS dos veículos: casas decimais, e se o fator 1,21 multiplica a inicial já arredondada.
- **C257** Desempenho estrutural: item 2 (MP) ou item 5 (Decreto) do Anexo IV; substituição do Grupo B pelo Grupo C.
- **C258** Potência: kW da ficha (ISO 1585, UNECE R85, GTR 21) contra os cv da nota; quem atesta e se a nota deve levar kW.
- **C259** Posições 8703.10 e 8703.90 e códigos de 8704 fora das listas: qual tabela vale.
- **C260** Versão sem CAT/Renavam (importação de veículo usado ou sem código): quais critérios valem.
- **C261** Art. 149, § 2º, I: combustível renovável, sistema reversível e híbrido (e a cilindrada do híbrido).
- **C262** Obrigação acessória e escrituração do IS: apuração, recolhimento, nota fiscal.
- **C263** Notas Complementares da Tipi 87-2, 88-1, 88-2 e 89-1: texto atual e alcance (só tenho os textos antigos dos Decretos 4.186/2002 e 8.168/2013, revogados).
- **C264** IPI: a `Al` da Lei 9.826 com as NC 87-13, 87-14 e 87-15 e o fim do IPI em 2027 (liga-se à C252).
- **C265** Conversão da MP 1.399: o que fazer com os cálculos se ela perder a eficácia.
