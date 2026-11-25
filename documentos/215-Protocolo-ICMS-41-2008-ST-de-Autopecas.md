# ST de autopeças: o Protocolo ICMS 41/2008 e as variações por UF que o modelo precisa aceitar — Documento 215 (nova versão)

> **O que este documento faz.** Na primeira versão li o **Protocolo ICMS 41/2008** e propus 3 entidades. Você respondeu que o ICMS é estadual, que o ERP tem de respeitar a regra de **todos** os estados, e mandou os RICMS de MG, SP e PB, o RICMS-MT (índice de correspondência), o RICMS-BA e a página de regime especial de MS. Depois disse: **"temos que desenhar somente as variações que tem por estado; depois damos as cargas nas tabelas, mas o modelo tem que aceitar estas variações por estado"**. Esta versão faz isso. Li o que consegui de **MG, SP, PB, RJ, PA, MA, PI, AP, AL, PR, AM, DF, RR e BA**; **AC, AM e DF li depois, em 12/11/2026**; do **MT** só li uma resposta de consulta (a SEFAZ-MT não entrega o texto do Anexo X). Das leituras saíram **18 variações** (seção 4.2), e delas, **7 entidades novas, 6 campos novos em 2 entidades existentes, 4 domínios abertos novos, 18 regras e 18 avisos** do Motor, e **16 perguntas ao contador**.
>
> **Não há carga de UF neste documento.** Os números que li (MVAs, prazos, listas) estão no **Anexo B como quadro de referência**, com o grau da fonte, para a carga por UF depois. **Nada foi aplicado ao dicionário.** Ele está na revisão 42 (1.206 entidades e 13.895 campos). Você já aprovou as Q215-1 a Q215-4 (D-N571); a Q215-6 também foi aprovada (D-N573); falta só a Q215-5.

> **Atualização de 12/11/2026 (D-N572).** Depois da aprovação, li no navegador do app o **RICMS/AC** (Decreto 8/1998, até o Decreto 11.947/2026), o **RICMS/AM** (Decreto 20.686/99, versão multivigente), o **RICMS/DF** (Decreto 18.955/97, Caderno I do Anexo IV, item 28), a **Resolução SEFA 20/2017 do PR** e a **Resposta à Consulta 18/2024 da SEFAZ-MT**; o **Anexo 1 do RICMS/BA** eu já tinha lido. **O modelo aprovado não mudou, não há carga de UF e nada foi aplicado ao dicionário.** Mudaram o Anexo B (AC, AM, DF, MT, PR e BA), a descrição do PA (achado 19) e a lista de perguntas (C321 reescrita, C323 nova e a Q215-6). **Resultado principal:** o MT **não implementou** a MVA de fidelidade de 36,56% do Protocolo 41/08; DF, AC, AM e PR aplicam 36,56% e 71,78%; os percentuais do PA são MVA ajustada, e não antecipação.

*Fontes: Protocolo ICMS 41/2008 (texto do CONFAZ consolidado até o Protocolo 93/26); RICMS/MG 2023, Anexo VII, na página oficial da Fazenda de MG (consolidado até o Decreto 49.301, de 27/10/2026); RICMS/SP, arts. 313-O e 313-P, Portaria SRE 34/2026 e Portaria SRE 16/23 (Fazenda SP); Anexo 05 do RICMS/PB, versão de 05/02/2025 (SEFAZ-PB); RICMS/BA (Decreto 13.780/2012, texto de 29/12/2020, enviado por você); Anexo I do Livro II do RICMS/RJ, Anexo X do RICMS/PR, Anexo 4.5 do RICMS/MA e Anexo XXXII do RICMS/AL (cópias de terceiros); Decreto 3.637/2024 e Decreto 2.588/2022 do Pará; Decreto 13.076/2008 do PI, Resolução Administrativa 25/2012 do MA (Anexo 4.41), Decretos 1.517/2008 e 145/2009 do AP, Portaria SF 198/2008 do DF e Decreto 99.605/2024 de AL (portais jurídicos privados); Consulta 7/2021 do AM; Consulta 2/2015 da SEFAZ-RR; Protocolos ICMS 97/10 e 129/10 (cópias de portais privados, truncadas); Despacho Confaz 43/2026 (DOU de 15/09/2026). Dicionário: revisão 42. Documento 209, com o Convênio ICMS 142/18.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **A ST de autopeças não é uma regra: é uma família de regras por UF.** O Protocolo 41/08 diz como o remetente retém, mas cada UF muda **o acordo que usa** (41/08, 97/10, nenhum), **a MVA** (36,56% e 71,78%; 26,50% e 40%; 33,08% e 59,60%; IVA-ST de 47,19% e 72,15%; alíquota fixa de 10,79% sobre a nota de entrada), **a lista de itens** (por NCM ou por CEST, com numeração própria), **a ordem dos preços da base**, **a alíquota interna usada**, **o prazo e a guia**, **as hipóteses em que a ST não se aplica** e **os regimes especiais** do contribuinte.
- **O que o Protocolo 97/10 acrescenta.** Ele é um segundo protocolo de autopeças, com 18 UFs no preâmbulo (AC, AL, AP, BA, GO, MA, MT, PA, PB, PR, PE, PI, RJ, RN, RR, SC, SE e TO); **SP não é signatária**. Os RICMS de BA, MA, PA, PB e RJ citam os **dois**. O 129/10 (só PE e SP) e o 22/08 (SP e CE) foram **revogados** pelos Protocolos 96/26 e 94/26 e o 41/08 perdeu SP pelo 93/26, tudo com efeitos de **01/10/2026**; SP revogou também o Anexo XIV da Portaria CAT 68/19 e a Portaria SRE 16/23 (Portaria SRE 34/2026).
- **Os valores mudam por UF e por data.** Os percentuais do PI e do AP (26,50% e 40%) e do MA (33,08% e 59,60%) vêm de atos de 2008 e 2012, **provavelmente superados**. O Protocolo 93/26 manda AL, BA, MT, PR e PI usarem a MVA da legislação interna. O ERP não pode gravar "36,56 e 71,78" como regra do protocolo; tem de gravar o percentual **por UF, por perfil do remetente, por CEST quando a UF der por item, e por vigência**.
- **O que o modelo passa a aceitar:** acordo de origem por UF (com prioridade quando o item está em dois acordos); método de cálculo por UF; MVA por perfil, por CEST e por alíquota interestadual (a tabela ajustada que PB, RJ, PI e MA publicam); ordem e condição dos preços da base; definição da alíquota interna; tratamento do remetente do Simples; prazo, guia e parcelas por tipo de operação; hipóteses de não aplicação por UF, com efeito (afasta ou mantém); lista de itens por UF e por acordo; adicional de fundo; fonte e lugar da publicação.
- **Proposta:** 7 entidades novas (`Cad_Icms_St_Acordo_Regra`, `Cad_Icms_St_Uf_Mva`, `Cad_Icms_St_Uf_Base_Criterio`, `Cad_Icms_St_Uf_Recolhimento`, `Cad_Icms_St_Uf_Nao_Aplicacao`, `Cad_Icms_St_Lista_Item` e `Mov_Icms_St_Base_Calculo_Item`), 3 campos em `Cad_Autopecas_Perfil`, 3 em `Cad_Filial_Regime_Icms`, 4 domínios abertos, 18 regras, 18 avisos. **Sem carga de UF.**
- **O que não li e pesa:** o Anexo X do RICMS-MT e a Portaria 195/2019, os valores do Anexo 1 do RICMS-BA (li, mas não transcrevi), o regulamento atual de ST do PR, o Decreto 90.309/2023 de AL, os textos oficiais dos Protocolos 97/10, 93/26, 94/26 e 96/26, e a versão atual de PI, AP e MA. Nada disso trava o desenho; trava a carga.

# 2. O que li

| Fonte | Grau | O que li | Para quê |
|---|---|---|---|
| Protocolo ICMS 41/2008 (CONFAZ) | Oficial, lido inteiro | Cláusulas 1ª a 7ª, parágrafos e redações anteriores | O texto-base e a história das UFs |
| RICMS/MG 2023, Anexo VII (Fazenda de MG) | Oficial, lido em partes | Parte 1 (arts. 1 a 20, 57 a 92), Parte 2 item 1 (autopeças) | MVA 71,78% na lista, art. 71 (montadora), arts. 18 e 20, art. 73 (uso automotivo), art. 74 (dia 9) |
| RICMS/SP, arts. 313-O e 313-P; Portarias SRE 16/23 e 34/2026 (Fazenda SP) | Oficial; 313-P e partes só por resumo | Caput e §§ do 313-O, a base da SRE 16/23, a revogação da SRE 34/26 | Saída de SP em 01/10/2026, IVA-ST, não aplicação a fabricante |
| Anexo 05 do RICMS/PB, versão de 05/02/2025 | Oficial, lido inteiro | Capítulo 1 (CEST 01, 89 itens) | Tabela com MVA ajustada por alíquota, lista por CEST |
| RICMS/BA (Decreto 13.780/2012), texto de 29/12/2020 | Texto enviado por você; desatualizado | Arts. 289, 290, 291, 292 e 295 | §§ 14 a 16 e 21, Simples, GNRE por protocolo |
| Anexo I do Livro II do RICMS/RJ | Cópia de terceiro, sem data | Item 7 (autopeças) | MVA por fidelidade, ajustada por alíquota, lista 7.1 a 7.132 |
| Anexo X do RICMS/PR (CEST) | Cópia de terceiro | Seção I, itens 1.0 a 128.0 e 999.0 | Lista de CEST (não traz MVA nem prazo) |
| Decretos 3.637/2024 e 2.588/2022 do Pará | Cópia da Assembleia (3.637) e de terceiro (2.588, parcial) | Art. 713-D, anexos de ST e de antecipação | Protocolos 41/08 e 97/10, antecipação na entrada |
| Decreto 13.076/2008 do PI e RA 25/2012 do MA (Anexo 4.41) | Portal privado, lidos até o item 38 e o item 55 | Arts. 1º a 6º e tabelas | MVAs de 2008 e 2012, prazo interno do PI, itens por protocolo no MA |
| Decretos 1.517/2008 e 145/2009 do AP; Portaria SF 198/2008 do DF | Portal privado | Seção de autopeças e estoque | Estoque na entrada da ST (12 parcelas, código 1837) |
| Decreto 99.605/2024 de AL | Portal privado, lido inteiro | Credenciamento de atacadistas de peças para motos | Alíquota fixa sobre a nota de entrada |
| Protocolos ICMS 97/10 e 129/10 | Cópias de portais privados, truncadas | Cláusulas 1ª a 8ª e início do Anexo | Segundo acordo de autopeças, definições da ALQ intra |
| Consulta 7/2021 do AM; Consulta 2/2015 da SEFAZ-RR | Portal privado; oficial | Íntegras | AM manda aplicar o agregado de convênio ou protocolo; RR: uso não automotivo fora da ST |
| Página de regime especial da SEFAZ-MS | Oficial, lida no navegador do app | Carta de serviço | Regime especial de obrigação acessória, prazo de 6 meses, renovação automática |
| RICMS/AC (Decreto 8/1998, até o Decreto 11.947/2026), Título VII, Anexo I, Tabela I, item 2 | Oficial (PDF da SEFAZ-AC, lido no navegador, autorizado por você) | Tabela de autopeças, 2.1 em diante, MVA original e ajustada por alíquota | MVA 36,56% e 71,78% e ajustada com interna de 17% |
| RICMS/AM (Decreto 20.686/99, versão multivigente), Anexo II-A, itens 1 a 4 | Oficial (SILT) | Tabela de autopeças e histórico do art. 15 (§§ 10 a 14, revogados em 27/04/2015) | MVA 36,56% e 71,78% desde 01/01/2016 |
| RICMS/DF (Decreto 18.955/97), Caderno I do Anexo IV, itens 23 (revogado) e 28 | Oficial (Receita do DF) | Subitens 28.1 a 28.18, lista com CEST, notas | Base, MVA ajustada, prazo do dia 9, MVA do destino para MT, PR, PI, RS e SP |
| Resolução SEFA 20/2017 do PR, art. 5º (atualizada até a Resolução 928/2018) | Oficial, mas só até 2018 | Seção V, autopeças | MVA original 36,56% e 71,78% |
| Resposta à Consulta 18/2024 da SEFAZ-MT (DOE de 15/02/2024) | Oficial, em cópia de terceiro (Normas Brasil) | Íntegra | MVA minorada do 41/08 não implementada no MT; artigos 5º e 6º do Anexo X; Portaria 195/2019 |
| Anexo 1 do RICMS/BA, item 1.0 (2026) | Oficial, lido no navegador | Listas de UFs dos Protocolos 41/08 e 97/10 e MVA ajustada | Alíquota interna de 20,5% na conta |
| Documento 209 e dicionário, revisão 42 | Projeto | `Cad_Aliquota`, `Cad_Icms_Obrigacao_Recolher`, `Cad_Filial_Regime_Icms`, `Cad_Cest`, `Cad_Classificacao_Mercadoria`, `Mov_Inventario_Item_Complemento_St` e `Cad_Autopecas_Perfil` | O que existe e o que falta |

**Não li:** o Anexo X do RICMS/MT (o site da SEFAZ-MT não entrega o texto; só a consulta de 2024), o regulamento atual de ST do PR (só a Resolução SEFA 20/2017, de 2018), a Portaria 195/2019 do MT, o Decreto 90.309/2023 de AL (site em manutenção), os textos oficiais dos Protocolos 97/10, 93/26, 94/26 e 96/26 (só o despacho do DOU), a Portaria CAT 68/19 além do início, a IN SEFA 2/2026 do Pará e a notícia de 2026 do PI. Do RICMS/BA li o item 1.0 do Anexo 1, mas **não transcrevi os valores**: a leitura precisa ser refeita antes da carga.

# 3. O que o dicionário já tem

| Peça | O que faz | O que falta |
|---|---|---|
| `Cad_Cest`, `Cad_Cest_Classificacao`, `Cad_Classificacao_Mercadoria` | O CEST, a NCM e o vínculo entre eles, com vigência | Dizer **qual item cada UF alcança ou exceta**, com a numeração da lista da UF |
| `Cad_Aliquota` (ICMS, `ID_Estado`) | A alíquota interna e interestadual por UF | Nada: a ALQ intra vem daqui; falta dizer **qual definição de alíquota** a UF usa |
| `Cad_Icms_Obrigacao_Recolher` | O código de receita por UF, com vigência | Ligar o código ao **tipo de operação** da ST e à guia |
| `Cad_Filial_Regime_Icms` | O regime especial de ICMS concedido ao estabelecimento, com ato e vigência | Regimes de ST (credenciamento de AL, dispensa de MG) e de **obrigação acessória** (MS), com **prazo e renovação** |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao` | Base de ST na origem ou no destino, repasse, complemento e o dispositivo de inaplicabilidade (209) | A **memória de cálculo**: método, MVA, alíquotas, critério da base |
| `Mov_Inventario_Item_Complemento_St` | O complemento de ST do inventário (Bloco H, motivo 06) | O prazo e as parcelas do **estoque na entrada no regime** (DF, AP) |
| `Mov_Apuracao_Icms_St`, `Mov_Icms_St_Complemento_*` | Apuração mensal, restituição e complemento (EFD) | Nada: a EFD não muda |
| `Cad_Autopecas_Perfil` (209) | Tipo de pessoa, industrial, comercializa o mesmo bem, declaração | O **regime de fidelidade**, o **papel de substituto** e a **autorização do fisco de destino** |
| Regra por UF | Não existe | **Tudo da seção 4.2** |

# 4. O que o texto diz e o que cada UF muda

## 4.1 O texto do Protocolo, dispositivo por dispositivo

| Dispositivo | O que diz | Uso no desenho |
|---|---|---|
| Cláusula 1ª, caput (Prot. 93/26, efeitos de 01/10/2026) | Operações interestaduais com os bens do Anexo II do Convênio 142, exceto seis CESTs, destinadas a 15 UFs: o **remetente** retém e recolhe o ICMS das operações subsequentes | `Cad_Icms_St_Acordo_Regra`, `Cad_Icms_St_Lista_Item`, R1 |
| Cláusula 1ª, § 1º (Prot. 95/22) | Só vale para peças **de uso especificamente automotivo**, adquiridas ou revendidas por indústria ou comércio de veículos, máquinas e equipamentos agrícolas ou rodoviários, **e desde que a mercadoria esteja sujeita à ST nas operações internas do destino** | R1 e aviso 9 |
| Cláusula 1ª, § 2º, I e II | Não se aplica a remessa a estabelecimento industrial e a outro estabelecimento do mesmo titular, desde que não varejista, **salvo se a UF de destino dispuser diferente** | R2 e aviso 4 |
| Cláusula 1ª, § 2º, III e § 2º-A | **Revogados** pelo Protocolo 93/26 (eram: estabelecimento em SP com origem no DF; CEST 01.015.00 com origem ou destino em SP) | Sem regra; só história |
| Cláusula 1ª, § 3º | Aplica-se também à peça para renovação, recondicionamento ou beneficiamento e à de ativo ou uso e consumo, **pelo diferencial de alíquotas** | R3 |
| Cláusula 1ª, §§ 4º e 5º | O regime se estende, **para as saídas subsequentes de todas as peças** (mesmo as excetuadas no caput), ao **fabricante** que vende a distribuidor com índice de fidelidade (Lei 6.729, art. 8º) ou com distribuição exclusiva por contrato de fidelidade, esta **autorizada por acordo com o fisco do destino**; as convenções de marca podem designar outros estabelecimentos | R4 e `Papel_Substituto_St` |
| Cláusula 1ª, § 6º (rótulo "cláusula segunda" na página) | Equipara a fabricante o **atacadista de peças controlado** por fabricante, que opera só com concessionários da rede, por contrato de fidelidade | R4 |
| Cláusula 2ª, caput | Base: preço máximo de venda a varejo fixado por autoridade; na falta, o preço sugerido ao público pelo fabricante ou importador; em ambos, mais o frete se não incluído | R5 |
| Cláusula 2ª, § 1º | Sem esses valores: preço do remetente mais frete, seguro, impostos e encargos, mais a MVA ajustada, pela fórmula; ALQ intra é a alíquota interna **ou a carga efetiva, se menor** | R6 e R7 |
| Cláusula 2ª, § 2º | MVA original: **36,56%** (fidelidade) e **71,78%** (demais casos); valores vigentes desde 01/12/2015 (GO desde 01/04/2015, PI desde 01/07/2015) | R6 |
| Cláusula 2ª, § 4º | Se o frete não puder entrar na base, o **destinatário** recolhe o imposto correspondente, com as MVAs | R13 |
| Cláusula 2ª, § 5º | Destino em ativo imobilizado ou consumo: base é o **preço efetivo**, com frete, seguro, impostos e encargos | R3 e R5 |
| Cláusula 2ª, § 6º (Prot. 93/26, efeitos de 01/10/2026) | Em **AL, BA, MT, PR e PI** a MVA original é a da **legislação interna** dessas UFs | `Cad_Icms_St_Uf_Mva.Origem_Valor` = `legislacao_uf`, R6 |
| Cláusula 2ª, § 7º | Se a ALQ intra é **menor** que a ALQ inter, aplica-se a **MVA original** | R8 |
| Cláusula 2ª, § 8º | A UF do destinatário pode exigir **autorização prévia do fisco** para a MVA de fidelidade (alínea "b") | `Exige_Autorizacao_Fisco_Destino`, R17 e aviso 5 |
| Cláusula 3ª | Imposto retido = diferença entre o calculado na cláusula 2ª e o devido pela **operação própria** | R11 |
| Cláusula 4ª | Recolhimento a favor da UF de destino **até o dia 9 do mês seguinte** à saída | R12 |
| Cláusula 5ª | As UFs signatárias adotam a ST **também nas operações internas**, com as MVAs e o prazo | R14 |
| Cláusulas 6ª e 7ª | Denúncia com 30 dias de antecedência; vigência desde 01/05/2008 | Só história |
## 4.2 O que as leituras por UF mostram: as 18 variações

A coluna "Grau" diz de onde veio: **O** oficial, **T** cópia de terceiro, **S** portal jurídico ou notícia, **E** enviado por você. Onde o ato é de 2008 a 2012, o valor está provavelmente superado e vale só como prova de que a variação existe.

| N | Variação | O que cada UF mostra | Grau | Onde fica no modelo |
|---|---|---|---|---|
| V1 | **Mais de um acordo por UF** | BA (art. 289, § 21), MA (art. 6º do Anexo 4.41), PA (art. 713-D), PB e RJ citam o 41/08 **e** o 97/10; no MA, os itens 1 a 124 vão pelo 41/08 e os itens 1 a 98, 100, 125 e 126 pelo 97/10 | O, T, S | `Cad_Icms_St_Acordo_Regra` (uma linha por acordo e UF, com `Prioridade_Aplicacao`) |
| V2 | **MVA diferente** | 36,56% e 71,78% (MG, PB, RJ e a lista interna do PA); 26,50% e 40% (PI e AP, atos de 2008); 33,08% e 59,60% (MA, 2012); IVA-ST de 47,19% e 72,15% (SP até 30/09/2026); MG, art. 71: 36,56% interna, 46,55% (12% e interna 18%), 59,88% (4% e 18%) e 48,97% (4% e 12%) | O, T, S | `Cad_Icms_St_Uf_Mva` (por UF, perfil, CEST e vigência) |
| V3 | **MVA ajustada publicada em tabela** | PB: 36,56% vira 50,22%, 58,75% e 63,87% (12%, 7%, 4%); 71,78% vira 88,96%, 99,69% e 106,14%; RJ: os mesmos 50,22%, 63,87%, 88,96% e 106,14%; PI e MA: tabelas com interna de 17%; AP: igual ao PI. A conta bate com a fórmula com alíquota interna de 20% (PB e RJ) | O, T, S | `Cad_Icms_St_Uf_Mva` (`Aliquota_Interestadual_Percentual`) |
| V4 | **Método de cálculo diferente** | SP: IVA-ST (Portaria SRE 16/23, até 30/09/2026); AL: alíquota fixa de 10,79% sobre o valor da nota de entrada, no credenciamento de atacadistas de peças de motos (14% em pneus); PA: **nenhum** (os percentuais do PA são MVA ajustada; ver achado 19); a variação de método fica só com SP e AL | O, S | `Cad_Icms_St_Acordo_Regra.ID_Metodo_Calculo` e `Tipo_Percentual` |
| V5 | **Preços da base e ordem** | Protocolo: preço máximo, preço sugerido, preço do remetente com MVA; MT (Anexo X, cap. III): PMPF, preço sugerido, preço praticado com MVA, e nas compras interestaduais o terceiro critério quando for maior que o PMPF; MG: preço fixado por órgão público, PMPF por portaria, preço praticado; AL: valor do documento de entrada; SP: preço praticado com frete, carreto e seguro | O, T, S | `Cad_Icms_St_Uf_Base_Criterio` |
| V6 | **Definição da alíquota interna da fórmula** | 41/08 e BA (art. 289, § 14, III): interna ou carga efetiva, se menor; 97/10: a "praticada pelo contribuinte substituto" no destino; 129/10: a "prevista para as operações substituídas" no destino | O, S | `Cad_Icms_St_Acordo_Regra.Definicao_Alq_Intra` |
| V7 | **Remetente do Simples Nacional** | BA (art. 295, § 3º): vale a MVA original do convênio ou protocolo ou a MVA interna, no lugar da ajustada; MG (art. 20, § 6º): o ajuste não se aplica a microempresa e EPP | O, E | `Cad_Icms_St_Acordo_Regra.Remetente_Simples_Usa` |
| V8 | **Lista de itens própria** | MG: 128 itens mais o 999.0, com CEST 01.xxx e NBM/SH; PB: itens 1.0 a 89.0 (CEST 01.001.00 a 01.089.00); RJ: 7.1 a 7.132, com o 7.131 residual (CEST 01.999.00); PR: CEST 1.0 a 128.0 e 999.0; MA: 126 itens sem CEST; PI: 84 itens sem CEST; AP: Anexo V, 100 itens sem CEST. Parte das listas é por **NCM**, parte por **CEST** | O, T, S | `Cad_Icms_St_Lista_Item` |
| V9 | **Âmbito: interno e interestadual** | MG: item 1.1 vale no interno e nas UFs do protocolo; item 1.2 (seis CEST) só no interno; PI e MA aplicam a ST também na operação interna (cláusula 5ª) | O, S | `Cad_Icms_St_Lista_Item.Ambito`; `Cad_Icms_St_Acordo_Regra.Alcance_Operacao` |
| V10 | **Prazo, guia e parcelas por operação** | Interestadual: dia 9 do mês seguinte (protocolo, MG, PI, MA, AP); interna do PI: dia 15; SP: período de apuração da entrada ou o art. 426-A (duas redações no texto); AL: entrada dia 9 e importação dia 15 do mês seguinte ao desembaraço; BA: GNRE específica para cada convênio ou protocolo (art. 295, § 2º); estoque: 12 parcelas (DF e AP) | O, S | `Cad_Icms_St_Uf_Recolhimento` |
| V11 | **Hipóteses de não aplicação** | MG (art. 18): industrial da mesma mercadoria, retorno ao encomendante, transferência do fabricante exceto para varejista, remessa a industrial como insumo desde que não comercialize a mesma mercadoria, destinatário com regime especial de substituto, item com isenção interna, escala industrial não relevante; **o documento deve indicar o dispositivo** (§ 4º); SP (art. 313-O, § 3º): saída para fabricante de veículo **ou de autopeças**; protocolo, PI, MA e AP: industrial e mesmo titular não varejista; MG (art. 73) e RR (consulta de 2015): uso não automotivo fica fora | O, S | `Cad_Icms_St_Uf_Nao_Aplicacao` (com `Efeito`) |
| V12 | **Autorização do fisco de destino** | Protocolo, cláusula 2ª, § 8º; BA, art. 289, § 21: a MVA original só vale se o destinatário tiver autorização do titular da inspetoria do seu domicílio fiscal | O, E | `Exige_Autorizacao_Fisco_Destino`; `Cad_Autopecas_Perfil` |
| V13 | **Regimes especiais do contribuinte** | MG (art. 73, § 1º): dispensa por regime especial, com percentual mínimo de revenda a estabelecimentos automotivos; MG (art. 72): responsabilidade de concessionárias por regime especial; AL: credenciamento opcional, negável e com exclusão de ofício (arts. 5º e 8º); MS: regime de obrigação acessória, 6 meses, renovação automática, taxa de 5 Uferms | O, S | `Cad_Filial_Regime_Icms` (+ campos e valores de domínio) |
| V14 | **Vigência por UF e acordo** | SP sai do 41/08, do 129/10 e do 22/08 em 01/10/2026 e revoga o Anexo XIV da CAT 68/19; RS sai do 41/08 em 01/11/2024; AL, MT, PR, PI e BA passam à MVA interna (BA em 01/06/2023) | O | A vigência de cada tabela |
| V15 | **Onde a UF publica** | BA publica entradas e saídas de UF e a MVA ajustada no **portal da SEFAZ**, não no regulamento (art. 289, § 16); MT fixa PMPF e MVA por **portaria** (Portarias 195/2019 e 199/2019 citadas no Anexo X); SP define a lista por portaria da CAT | O, T | `Fonte_Publicacao`, `Referencia_Publicacao` |
| V16 | **Adicional de fundo** | AL: FECOEP de 1% no credenciamento (Decreto 99.605, art. 4º, § 3º) | S | `Adicional_Fundo_Percentual` |
| V17 | **Estoque na entrada no regime** | DF: declaração até 31/07/2008, pagamento em até 12 cotas, mínimo de R$ 200,81; AP: 12 parcelas e código de receita 1837 ("ICMS Estoque Remanescente") | S | `Tipo_Operacao` = `estoque_na_entrada_no_regime` e `Numero_Parcelas_Maximo`; o inventário já existe |
| V18 | **Uso, consumo e ativo** | Protocolo, § 3º: ST com diferencial de alíquotas e base no preço efetivo; MT, art. 8º: base é o valor da operação mais o diferencial, com fórmula própria do ICMS ST DIFAL; MG e BA: valor da operação mais a diferença de alíquotas | O, T | `Cad_Icms_St_Uf_Base_Criterio.Tipo_Criterio` e `Cad_Icms_St_Uf_Recolhimento.Tipo_Operacao` |

# 5. Achados e leituras minhas

- **(1) O protocolo fecha a lacuna do 209.** O R15 ("demais casos interestaduais: regra da UF de destino") deixava a ST de reposição sem desenho. O protocolo traz a **lista de UFs, a lista de CESTs, a base, a MVA, a dedução do imposto próprio e o prazo**. Só a MVA de cinco UFs fica fora (item 4).
- **(2) A lista de UFs mudou duas vezes em dois anos.** Na redação do Protocolo 95/22 (de 01/02/2023 a 31/10/2024) a lista incluía **RS e SP**; o 32/24 tirou o RS em 01/11/2024; o 93/26 tirou SP em 01/10/2026. **Nota de saída com data de 2024 ou 2025 para SP ainda está sob o protocolo**; por isso a regra por UF **precisa de vigência**.
- **(3) O texto da página tem um rótulo trocado.** A linha de efeitos do Protocolo 93/26 sobre o caput da cláusula primeira diz "01.10.**24**", mas as redações anteriores dizem "efeitos de 01.11.24 até 30.09.26" e o cabeçalho diz "01.10.26". Adotei **01/10/2026** (C314). O § 6º da cláusula primeira também aparece rotulado "cláusula segunda".
- **(4) Em AL, BA, MT, PR e PI o protocolo manda usar a MVA da legislação interna.** Essas UFs entram na lista de destinos, mas a MVA é a delas. Desde 01/02/2023: **AL, MT, PR e PI** (BA entrou em 01/06/2023, pelo Protocolo 5/23). Sem o regulamento dessas UFs, o ERP **registra** que a MVA é da UF (`Origem_Valor` = `legislacao_uf`) e **avisa** (aviso 3); não inventa percentual. Essa é a segunda parte da Q209-9; os textos dessas UFs são pedidos na Q215-5.
- **(5) A fidelidade tem duas condições diferentes.** O índice de fidelidade da Lei 6.729, art. 8º, vale para **fabricante de veículos automotores**; a distribuição exclusiva por contrato vale para fabricante de **veículos, máquinas e equipamentos agrícolas ou rodoviários** e, pelo § 4º, II, **precisa de autorização** por acordo com o fisco do destino. O § 8º da cláusula segunda deixa a **UF exigir a autorização prévia**. O ERP guarda a autorização como documento (`ID_Documento_Autorizacao_Fisco`) e não a valida.
- **(6) O protocolo não diz a alíquota que se aplica à base.** O texto diz como formar a base e que o imposto é a diferença para a operação própria, mas não diz "alíquota interna". Li como a **alíquota interna do destino (ou a carga efetiva, se menor)**, a mesma ALQ intra da fórmula (C312). O FCP da ST fica para a UF.
- **(7) O ICMS da operação própria entra pelo que a nota destaca.** O ERP não recalcula a operação própria; usa o valor do item.
- **(8) O DF tem história contraditória no cabeçalho.** O cabeçalho diz "Denunciado pelo DF (Despacho 88/08)" e também "adesão do DF com efeitos em data prevista em ato do Poder Executivo (Prot. 5/11)"; o caput lista o DF como destino. Não carreguei nada de UF neste documento; o DF fica para a carga, com a pergunta C308.
- **(9) O Anexo Único do protocolo é história.** Revogado em 01/02/2023; a lista vigente é o Anexo II do Convênio 142. O documento 209 já tem os 130 CESTs do segmento 01. Notas de 2021 a janeiro de 2023 seguem o Anexo Único e **não** foram carregadas (C310).
- **(10) O imposto da ST de ICMS acaba com a transição.** A ST de ICMS sai de cena com a extinção do imposto (2029 a 2033). O desenho não projeta isso; a vigência da regra por UF aceita o fim quando a norma o disser.
- **(11) A ST de autopeças é por UF, não por protocolo.** A mesma peça, vendida para a PB e para o RJ, entra na ST com a mesma MVA de 71,78%, mas a lista, o prazo, a guia e as hipóteses de não aplicação são de cada UF. Gravar só "acordo" e "UF alcançada" (a primeira versão) não bastava.
- **(12) O Protocolo 97/10 existe e a primeira versão não o tinha.** Os RICMS de BA, MA, PA, PB e RJ citam os dois protocolos. O 97/10 não tem SP como signatária e, pelas fontes que li, **não foi revogado** em 2026 (a notícia da Senior não o lista, mas a lista dela é de "destaques").
- **(13) As revogações de 2026 não terminam a ST de autopeças.** O Protocolo 93/26 só exclui SP do 41/08; o 94/26 e o 96/26 revogam protocolos de pares de UFs (SP e CE; SP e PE). SP revogou, por portaria, a lista e a base de cálculo internas. O que SP aplica a partir de 01/10/2026 às autopeças **não aparece em nenhum texto que li** (C318).
- **(14) A tabela de MVA ajustada que a UF publica confere com a fórmula.** Com alíquota interna de 20%: (1 + 0,3656) × (1 − 0,12) ÷ (1 − 0,20) − 1 = 50,22%; (1 + 0,7178) × (1 − 0,04) ÷ (1 − 0,20) − 1 = 106,14%. A tabela existe porque a UF fixou a alíquota interna na conta. O modelo guarda o percentual publicado **e** a alíquota interna usada, e o Motor confere com `Cad_Aliquota`.
- **(15) O prazo interno do PI é diferente do interestadual.** O Decreto 13.076/2008 do PI manda recolher a ST interestadual até o dia 9 e a interna até o dia 15 (art. 5º, redação de 2008). Por isso o prazo é por tipo de operação.
- **(16) A BA mantém parte da regra fora do regulamento.** O art. 289, § 16, diz que as entradas e saídas de UF dos acordos e as MVAs ajustadas são "atualizadas na página da Secretaria da Fazenda". A regra por UF precisa de **fonte e data de publicação por linha** (campos `Fonte_Publicacao` e `Referencia_Publicacao`).
- **(17) AL tem um regime que não usa MVA.** O credenciamento do Decreto 99.605/2024 aplica 10,79% sobre o valor da nota de entrada, para atacadistas de peças de motos (CNAE 4541-2/02), opcional e negável. Cabe em `ID_Metodo_Calculo` e em `Cad_Filial_Regime_Icms`.
- **(18) O que li de PI, AP e MA é de 2008 a 2012 e não vale como valor.** O Decreto 13.076/2008 do PI (efeitos desde 01/06/2008), o Decreto 1.517/2008 do AP, a RA 25/2012 do MA e a Portaria SF 198/2008 do DF (estoque) são atos antigos; o Protocolo 93/26 já diz que o PI usa a MVA interna. Servem como prova das variações e, no Anexo B, como história.

- **(19) Os percentuais do PA são MVA ajustada, e não antecipação.** Com a MVA original de 71,78% e a fórmula do protocolo: (1 + 0,7178) × (1 − 0,12) ÷ (1 − 0,17) − 1 = 82,13% e, com 7%, 92,48% (interna de 17%, decreto de 2022); com interna de 19%, 7% dá 97,23%, 12% dá 86,63% e 4% dá 103,59% (lista de 2024). Os números de 2022 são **os mesmos** da tabela do AC. O PA não é exemplo de método por antecipação; a coluna de cada percentual é a alíquota interestadual (4%, 7%, 12%).
- **(20) O MT não implementou a MVA de fidelidade do Protocolo 41/08.** A Resposta à Consulta 18/2024 diz que a regra do § 2º, I e II, da cláusula 2ª "não foi implementada na legislação mato-grossense", e que ela só alcançaria saída de estabelecimento fabricante. As peças estão na Tabela II do Apêndice do Anexo X; a base segue os arts. 5º e 6º do Anexo X (preço fixado por órgão público; preço sugerido, desde que a tabela seja enviada antes à SEFAZ, RICMS art. 460, §§ 5º e 6º; preço do remetente mais a MVA da Portaria 195/2019 ou, na falta, a do convênio ou protocolo). O DF registra o mesmo para MT, PR, PI, RS e SP: vale a MVA da legislação interna do destino (item 28.17, redação de 2020). Isso cabe no modelo: `Cad_Icms_St_Uf_Mva` por UF e perfil, e `Cad_Icms_St_Uf_Nao_Aplicacao` para a fidelidade.
- **(21) AC, AM, DF e PR repetem os 36,56% e 71,78%.** AC: tabela de 2.1 em diante com ajustada para 12%, 7% e 4% (interna de 17%). AM: Anexo II-A, itens 1 e 2 (lista do 41/08) e 3 e 4 (outras peças), desde 01/01/2016; os §§ 10 a 14 do art. 15 foram revogados em 27/04/2015. DF: item 28 (lista com CEST, protocolos 54/13, 53/11, 5/11 e 41/08, desde 01/06/2011), MVA ajustada pela fórmula com ALQ intra "interna ou carga efetiva, se menor" (28.4), MVA original quando a interna é menor que a interestadual (28.18), substituto interno industrial, importador e atacadista conforme portaria (28.1), prazo até o dia 9 do mês seguinte (28.10) e fidelidade de fabricante de máquinas agrícolas só com autorização do fisco do DF (28.5, I, b). O item 23 do DF (Protocolo 36/04) foi revogado em 2008. PR: Resolução SEFA 20/2017, art. 5º, para os produtos do art. 27 do Anexo X (texto de 2018).
- **(22) A tabela do AC tem um valor que não confere com a fórmula.** Para 36,56% com interestadual de 4% e interna de 17%, a fórmula dá 57,95%; a tabela traz 53,90% (os outros cinco valores conferem). Pode ser erro de digitação do PDF; vai para o contador (C323). O ERP deve carregar o valor publicado e avisar a diferença (aviso de conferência com a fórmula).

# 6. Proposta

## 6.1 Como as peças se encaixam

1. O item de saída (ou de entrada) de peça vai para **`Cad_Icms_St_Acordo_Regra`** pela UF de destino, pela data da nota e pelo tipo de operação. Se a UF tem duas regras (dois acordos), vale a de menor `Prioridade_Aplicacao` cujo item esteja na lista.
2. **`Cad_Icms_St_Lista_Item`** diz se o CEST ou a NCM é alcançado ou excetuado **naquela UF e naquele acordo**.
3. **`Cad_Icms_St_Uf_Nao_Aplicacao`** diz se alguma hipótese afasta (ou mantém) a ST, com a condição.
4. **`Cad_Icms_St_Uf_Base_Criterio`** dá a ordem dos preços da base; **`Cad_Icms_St_Uf_Mva`** dá o percentual por perfil do remetente, por CEST e por alíquota interestadual; **`Cad_Aliquota`** dá a ALQ intra, conforme `Definicao_Alq_Intra`.
5. **`Cad_Icms_St_Uf_Recolhimento`** dá o prazo, a guia, as parcelas e o código de receita por tipo de operação.
6. O Motor calcula e grava a memória em **`Mov_Icms_St_Base_Calculo_Item`**, e o resultado alimenta os campos que já existem.
7. **`Cad_Autopecas_Perfil`** (remetente e destinatário) e **`Cad_Filial_Regime_Icms`** (regimes especiais) dizem quem é o contribuinte.
8. **O ERP nunca bloqueia** (D-N284): sem regra, sem percentual ou com regra provisória, calcula o que a lei fecha e **avisa**.

**Regra de desenho (sua instrução):** o modelo aceita a variação; o dado entra depois, UF por UF, com a fonte e o grau. Variação que ainda não tem campo vai para `Observacao_Regra` e gera o aviso 17, para virar campo quando se repetir.

## 6.2 As entidades novas

### `Cad_Icms_St_Acordo_Regra` (Contabilidade & Fiscal, com vigência, 21 campos)

A regra de ST de autopeças de uma UF de destino em um acordo: o método de cálculo, a definição da alíquota interna, o tratamento do remetente do Simples, a prioridade entre acordos, a autorização do fisco, o adicional de fundo e onde a UF publica. É a cabeça das outras cinco tabelas por UF.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Acordo_Regra` | identificador | Chave. |
| `ID_Icms_St_Acordo_Regra_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Acordo_Regra_Versao). Fase 0, seção 2. |
| `ID_Acordo_St` | referência (Cad_Classe_Sistema, domínio = acordo_st_icms) --- identidade | O instrumento que cria a ST para a UF. Domínio aberto: `protocolo_icms_41_08`, `protocolo_icms_97_10`, `convenio_icms_142_18` e `legislacao_propria_uf`; os acordos que saíram em 2026 entram como valor quando houver carga. |
| `ID_Estado_Destino` | referência (Cad_Estado) --- identidade | A UF de destino a que a regra vale nesta versão. Se a UF sai do acordo, a versão termina; não existe linha de "UF excluída". |
| `Prioridade_Aplicacao` | número | Quando o item está na lista de dois acordos da mesma UF (MA, itens 1 a 98 em 41/08 e 97/10), vale a regra de menor número. Padrão 1. |
| `Alcance_Operacao` | enumeração {interestadual, interna, ambas} | As operações a que a regra vale. O 41/08 estende à operação interna (cláusula 5ª); o PI, a MG e o MA distinguem prazo e lista. |
| `ID_Metodo_Calculo` | referência (Cad_Classe_Sistema, domínio = metodo_calculo_st_uf) | Como a UF calcula: `mva_do_protocolo`, `mva_da_legislacao_uf`, `iva_st_divulgado_pela_uf` (SP até 30/09/2026), `aliquota_fixa_sobre_documento_entrada` (AL) e `percentual_na_antecipacao_entrada` (nenhuma UF conhecida hoje; ver Q215-6). Domínio aberto. |
| `Definicao_Alq_Intra` | enumeração {interna_ou_carga_efetiva_menor, praticada_pelo_substituto_no_destino, prevista_para_operacao_substituida} | O que é a ALQ intra da fórmula: o 41/08 e a BA usam a primeira, o 97/10 a segunda e o 129/10 a terceira. A alíquota vem de `Cad_Aliquota` (ICMS, UF de destino). |
| `Usa_Mva_Original_Se_Alq_Intra_Menor` | booleano | A ALQ intra menor que a ALQ inter leva à MVA original (41/08, cláusula 2ª, § 7º; BA, art. 289, § 15). Padrão verdadeiro. |
| `Remetente_Simples_Usa` | enumeração {mva_ajustada, mva_original, nao_aplica_ajuste} | O que a UF manda usar quando o remetente é do Simples Nacional: a BA usa a MVA original (art. 295, § 3º); MG não aplica o ajuste a microempresa e EPP (art. 20, § 6º do Anexo VII). Padrão `mva_ajustada`. |
| `Exige_Autorizacao_Fisco_Destino` | booleano | A UF exige a autorização prévia para a MVA de fidelidade (41/08, cláusula 2ª, § 8º; BA, art. 289, § 21: autorização do titular da inspetoria do domicílio fiscal do destinatário). Padrão falso. |
| `Adicional_Fundo_Percentual` | número, opcional | O adicional de fundo (FECOEP ou FECP) que a UF soma ao imposto da ST nesta regra, quando a própria regra o fixa (AL: 1% no credenciamento). Vazio quando o fundo vem de `Cad_Aliquota`. |
| `Fonte_Publicacao` | enumeração {regulamento, anexo_do_regulamento, portaria, portal_sefaz, protocolo} | Onde a UF publica o que muda: BA no portal (art. 289, § 16); MT, o PMPF e a MVA por portaria; SP, a lista por portaria da CAT. |
| `Referencia_Publicacao` | texto, opcional | O ato, a portaria ou o endereço da publicação, para o contador conferir. |
| `Observacao_Regra` | texto, opcional | O que a UF faz e não cabe em campo (por exemplo, o adicional de 5,39% do credenciamento de AL). Quem preenche ganha o aviso 17. |
| `Fundamento_Legal` | texto | O artigo e o ato da UF ou do acordo que fixam a regra. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Icms_St_Uf_Mva` (Contabilidade & Fiscal, com vigência, 16 campos)

O percentual da UF: a MVA, o IVA-ST ou o percentual de antecipação, por perfil do remetente, por CEST e, quando a UF publica a tabela ajustada, por alíquota interestadual.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Uf_Mva` | identificador | Chave. |
| `ID_Icms_St_Uf_Mva_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Uf_Mva_Versao). Fase 0, seção 2. |
| `ID_Icms_St_Acordo_Regra` | referência (Cad_Icms_St_Acordo_Regra) --- identidade | A regra da UF e do acordo a que o percentual pertence. |
| `ID_Perfil_Remetente_St` | referência (Cad_Classe_Sistema, domínio = perfil_remetente_st) --- identidade | O perfil do remetente: `fabricante_indice_fidelidade`, `distribuicao_exclusiva_contrato`, `atacadista_controlado` e `demais`. Domínio aberto: MG (art. 71) trata a montadora com contrato de fidelidade à parte. |
| `ID_Cest` | referência (Cad_Cest), opcional --- identidade | O CEST a que o percentual vale; vazio quando vale para toda a lista da regra. Existe porque a lista de uma UF pode trazer percentual por item. |
| `Tipo_Percentual` | enumeração {mva_st, iva_st, antecipacao_entrada} --- identidade | O que o número é: a MVA do protocolo ou da UF, o IVA-ST (SP) ou o percentual de antecipação na entrada (nenhuma UF conhecida hoje; Q215-6). |
| `Aliquota_Interestadual_Percentual` | número, opcional --- identidade | A alíquota interestadual (4, 7 ou 12) quando a UF publica o percentual já ajustado por alíquota (PB, RJ, PI, MA e MG, art. 71); vazio na linha do percentual original. |
| `Aliquota_Interna_Referencia_Percentual` | número, opcional | A alíquota interna com que a UF calculou o percentual ajustado publicado (17% no PI, MA e AP; 20% na PB e no RJ). O Motor confere com `Cad_Aliquota` e avisa se diferir. |
| `Percentual` | número | O percentual: a MVA, o IVA-ST ou a antecipação original, ou, na linha com alíquota interestadual, o ajustado publicado. |
| `Origem_Valor` | enumeração {protocolo, legislacao_uf, tabela_publicada_uf} | De onde vem o número: o protocolo (36,56 e 71,78), a legislação interna (AL, BA, MT, PR e PI desde 2023) ou a tabela que a UF publica. |
| `Fundamento_Legal` | texto | O artigo, o anexo ou o item da lista que traz o número. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Icms_St_Uf_Base_Criterio` (Contabilidade & Fiscal, com vigência, 14 campos)

A ordem dos preços com que a UF forma a base da ST: cada linha é um critério, com a ordem, a condição de uso e se o frete entra.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Uf_Base_Criterio` | identificador | Chave. |
| `ID_Icms_St_Uf_Base_Criterio_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Uf_Base_Criterio_Versao). Fase 0, seção 2. |
| `ID_Icms_St_Acordo_Regra` | referência (Cad_Icms_St_Acordo_Regra) --- identidade | A regra da UF e do acordo. |
| `Ordem` | número --- identidade | A posição do critério na sequência; o Motor usa o primeiro que tem valor. |
| `Tipo_Criterio` | enumeração {preco_maximo_orgao_publico, pmpf, preco_sugerido_fabricante, preco_praticado_com_encargos_e_mva, valor_documento_entrada, preco_efetivo_ativo_consumo, valor_operacao_mais_diferencial} | O preço da base: o fixado por órgão público, o PMPF, o sugerido pelo fabricante ou importador, o preço do remetente com encargos e MVA, o valor da nota de entrada (AL), o preço efetivo no ativo ou consumo (41/08, cláusula 2ª, § 5º) e o valor da operação mais o diferencial de alíquotas (MT, art. 8º). |
| `Inclui_Frete_Na_Base` | booleano | O frete entra na base. Quando falso e o frete não pode entrar, o destinatário recolhe o imposto do frete (R13). |
| `Condicao_Uso` | enumeração {sempre, somente_se_maior_que_pmpf, somente_interestadual, somente_ativo_consumo} | Quando o critério vale: MT usa o preço praticado com MVA nas compras interestaduais quando o resultado for maior que o PMPF (art. 6º, § 4º). Padrão `sempre`. |
| `Ato_Divulgacao` | texto, opcional | A portaria que divulga o PMPF ou a MVA (MT: Portarias 195/2019 e 199/2019, citadas no Anexo X). |
| `Fundamento_Legal` | texto | O artigo da UF ou do acordo que fixa o critério. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Icms_St_Uf_Recolhimento` (Contabilidade & Fiscal, com vigência, 16 campos)

O prazo, a guia, as parcelas e o código de receita da ST em uma UF, por tipo de operação.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Uf_Recolhimento` | identificador | Chave. |
| `ID_Icms_St_Uf_Recolhimento_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Uf_Recolhimento_Versao). Fase 0, seção 2. |
| `ID_Icms_St_Acordo_Regra` | referência (Cad_Icms_St_Acordo_Regra) --- identidade | A regra da UF e do acordo. |
| `Tipo_Operacao` | enumeração {interestadual_saida, interna_saida, entrada_antecipacao, importacao, ativo_consumo_diferencial, estoque_na_entrada_no_regime} --- identidade | A operação a que o prazo vale: PI tem prazo diferente para a interna; AL, para a importação; DF e AP, para o estoque na entrada no regime. |
| `Regra_Prazo` | enumeração {dia_do_mes_seguinte, periodo_apuracao_da_entrada, dias_apos_desembaraco, regra_geral_da_uf} | Como o prazo se conta: no dia tal do mês seguinte (protocolo, MG, AP), no período de apuração da entrada (SP, em uma das redações), depois do desembaraço (AL) ou pela regra geral da UF. |
| `Dia_Numero` | número, opcional | O dia (9 ou 15) ou o número de dias. |
| `Guia` | enumeração {gnre, dae, gare, outra} | A guia: a GNRE nas operações interestaduais; DAE, GARE ou outra na interna e na entrada. |
| `Guia_Especifica_Por_Acordo` | booleano | A UF exige GNRE própria para cada convênio ou protocolo (BA, art. 295, § 2º). Padrão falso. |
| `Numero_Parcelas_Maximo` | número, opcional | O número de parcelas do pagamento: 12 no estoque do DF e do AP. Vazio quando à vista. |
| `ID_Icms_Obrigacao_Recolher` | referência (Cad_Icms_Obrigacao_Recolher), opcional | O código de receita da UF para esta operação; vazio até a carga. |
| `Fundamento_Legal` | texto | O artigo e o ato da UF. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Icms_St_Uf_Nao_Aplicacao` (Contabilidade & Fiscal, com vigência, 14 campos)

Uma hipótese em que a UF afasta a ST, ou a mantém quando o acordo a afastaria, com a condição.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Uf_Nao_Aplicacao` | identificador | Chave. |
| `ID_Icms_St_Uf_Nao_Aplicacao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Uf_Nao_Aplicacao_Versao). Fase 0, seção 2. |
| `ID_Icms_St_Acordo_Regra` | referência (Cad_Icms_St_Acordo_Regra) --- identidade | A regra da UF e do acordo. |
| `ID_Hipotese_Nao_Aplicacao` | referência (Cad_Classe_Sistema, domínio = hipotese_nao_aplicacao_st) --- identidade | A hipótese. Domínio aberto: `destinatario_industrial`, `mesmo_titular_nao_varejista`, `destino_fabricante_veiculo_ou_autopecas`, `remessa_industrial_insumo`, `retorno_encomendante`, `destinatario_regime_especial_substituto`, `item_com_isencao_interna`, `escala_industrial_nao_relevante` e `uso_nao_automotivo`. |
| `Efeito` | enumeração {afasta_st, mantem_st} | `afasta_st`: a ST não se aplica; `mantem_st`: a UF "dispõe de forma diferente" (41/08, cláusula 1ª, § 2º) e a ST se aplica mesmo na hipótese. |
| `Condicao_Texto` | texto, opcional | A condição escrita (MG: "desde que o industrial não comercialize a mesma mercadoria"). |
| `Exige_Nao_Comercializar_Mesmo_Item` | booleano | A hipótese só vale se o destinatário industrial não comercializa o mesmo bem (campo `Comercializa_Mesmo_Item` do perfil, documento 209). Padrão falso. |
| `Exige_Indicar_Dispositivo_Na_Nota` | booleano | A UF exige que o documento indique o dispositivo que afasta a ST (MG, art. 18, § 4º). Padrão falso. |
| `Fundamento_Legal` | texto | O artigo e o ato da UF ou do acordo. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Icms_St_Lista_Item` (Contabilidade & Fiscal, com vigência, 16 campos)

O item (CEST ou NCM) que um acordo, ou uma UF dentro do acordo, alcança ou exceta, com a numeração da lista da UF. Substitui o `Cad_Icms_St_Acordo_Cest` da primeira versão, que não tinha UF.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Lista_Item` | identificador | Chave. |
| `ID_Icms_St_Lista_Item_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Icms_St_Lista_Item_Versao). Fase 0, seção 2. |
| `ID_Acordo_St` | referência (Cad_Classe_Sistema, domínio = acordo_st_icms) --- identidade | O acordo a que a lista pertence. |
| `ID_Estado_Destino` | referência (Cad_Estado), opcional --- identidade | A UF da lista; vazio quando a lista vale para todas as UFs do acordo (a exceção de seis CEST do 41/08). |
| `ID_Cest` | referência (Cad_Cest), opcional --- identidade | O CEST do item; vazio quando a lista da UF é só por NCM (PI, MA e AP). |
| `ID_Classificacao` | referência (Cad_Classificacao_Mercadoria), opcional --- identidade | A NCM do item, de qualquer nível; vazio quando o item é por CEST. |
| `Condicao` | enumeração {alcancado, excetuado} | `excetuado`: o acordo ou a UF não alcança o item. O Motor trata como alcançado todo CEST do Anexo II do Convênio 142 que não tem linha `excetuado`, salvo UF que tenha lista positiva própria. |
| `Ambito` | enumeração {interestadual, interno, ambos} | Onde a regra vale: MG, item 1.1 (interno e acordo) e 1.2 (só interno). |
| `Numero_Item_Lista` | código (até 20), opcional | O número do item na lista da UF (MG 1.8, RJ 7.8, PB 85.0), para o contador conferir. |
| `Condicao_Texto` | texto, opcional | A ressalva da lista ("exceto os itens do CEST 01.077.00"; "uso especificamente automotivo"). |
| `Fundamento_Legal` | texto | O anexo, o item e o ato. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Icms_St_Base_Calculo_Item` (Contabilidade & Fiscal, sem vigência, 27 campos)

A memória do cálculo da base e do imposto retido de um item sob uma regra de ST: a regra que valeu, o método, o critério da base, o percentual e de onde veio, as alíquotas, a base, o imposto, o vencimento e quem recolhe. Existe para auditoria e para os avisos; o resultado alimenta `Mov_Nota_Fiscal_Saida_Item_St_Informacao` e `Mov_Apuracao_Tributo_Item.Valor_Mva`.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Base_Calculo_Item` | identificador | Chave. |
| `ID_Item_Saida` | referência (Mov_Nota_Fiscal_Saida_Item) | O item de saída. 1:1: um item tem uma memória de ST. |
| `ID_Icms_St_Acordo_Regra` | referência (Cad_Icms_St_Acordo_Regra), opcional | A regra da UF que valeu. Vazio quando o item não está sob regra carregada (aviso 1). |
| `ID_Estado_Destino` | referência (Cad_Estado) | A UF de destino do imposto retido. |
| `Tipo_Operacao` | enumeração {interestadual_saida, interna_saida, entrada_antecipacao, importacao, ativo_consumo_diferencial, estoque_na_entrada_no_regime} | A operação, que escolhe o prazo e a guia em `Cad_Icms_St_Uf_Recolhimento`. |
| `ID_Metodo_Calculo` | referência (Cad_Classe_Sistema, domínio = metodo_calculo_st_uf), opcional | O método da regra, copiado para a memória (a regra pode mudar depois). |
| `Criterio_Base_Aplicado` | enumeração {preco_maximo_orgao_publico, pmpf, preco_sugerido_fabricante, preco_praticado_com_encargos_e_mva, valor_documento_entrada, preco_efetivo_ativo_consumo, valor_operacao_mais_diferencial}, opcional | O critério de `Cad_Icms_St_Uf_Base_Criterio` que formou a base. |
| `Valor_Preco_Referencia` | número, opcional | O preço máximo, o PMPF ou o sugerido, quando o critério é um deles. |
| `Valor_Frete_Acrescido` | número, opcional | O frete somado à base quando não estava no preço. |
| `Valor_Preco_Remetente_Com_Encargos` | número, opcional | O preço do remetente com frete, seguro, impostos e encargos, nos critérios que o usam. |
| `ID_Icms_St_Uf_Mva` | referência (Cad_Icms_St_Uf_Mva), opcional | A linha de percentual que valeu. Vazia quando o método não usa percentual ou quando não há carga (aviso 3). |
| `ID_Perfil_Remetente_St` | referência (Cad_Classe_Sistema, domínio = perfil_remetente_st), opcional | O perfil do remetente que escolheu a linha. |
| `Mva_Original` | número, opcional | O percentual original usado, em percentual. |
| `Aliquota_Interestadual` | número, opcional | A ALQ inter da operação. |
| `Aliquota_Interna_Ou_Carga_Efetiva` | número | A ALQ intra, conforme `Definicao_Alq_Intra` da regra. Vale também para o imposto sobre a base. |
| `Mva_Ajustada` | número, opcional | O resultado da fórmula, ou o ajustado publicado pela UF, em percentual. |
| `Regra_Mva_Aplicada` | enumeração {mva_ajustada, mva_ajustada_tabelada_uf, mva_original_alq_intra_menor, mva_original_remetente_simples}, opcional | Qual regra escolheu o percentual: a fórmula, a tabela da UF, a ALQ intra menor ou o remetente do Simples. |
| `Base_Calculo_St` | número | A base do imposto retido. Copiada para `Base_Calculo_St_Origem_Destino` da informação de ST do item. |
| `Valor_Adicional_Fundo` | número, opcional | O adicional de fundo somado ao imposto (`Adicional_Fundo_Percentual`). |
| `Valor_Icms_Sobre_Base` | número | A base vezes a ALQ intra. |
| `Valor_Icms_Operacao_Propria` | número | O ICMS da operação própria, como destacado na nota. |
| `Valor_Icms_St_Retido` | número | A diferença entre os dois, mais o adicional de fundo. |
| `Data_Vencimento` | data, opcional | A data pela `Regra_Prazo` e `Dia_Numero` da UF. |
| `Recolhe_Destinatario` | booleano | O frete não pôde entrar na base e o destinatário recolhe. Padrão falso. |
| `ID_Apuracao` | referência (Mov_Apuracao_Tributo_Item), opcional | A linha de apuração que recebeu o resultado. |
| `Dados_Provisorios` | booleano | Verdadeiro se a regra, o percentual ou o critério usado está `provisorio`: o relatório avisa. |
| `Memoria_Calculo` | texto | O texto da conta, para auditoria. |

## 6.3 Campos novos em entidades existentes

| Entidade | Campo | Tipo | Para quê |
|---|---|---|---|
| `Cad_Autopecas_Perfil` | `Regime_Fidelidade_Distribuicao` | enumeração {nenhum, indice_fidelidade_lei_6729_art_8, distribuicao_exclusiva_contrato_fidelidade} | A condição do fabricante que dá a MVA de fidelidade (41/08, cláusula 2ª, § 2º, I, "a" e "b") |
| `Cad_Autopecas_Perfil` | `Papel_Substituto_St` | enumeração {nao_substituto_subsequentes, fabricante_par_4, designado_convencao_marca_par_5, atacadista_controlado_par_6} | Quem retém nas saídas subsequentes de todas as peças, mesmo as excetuadas (cláusula 1ª, §§ 4º a 6º) |
| `Cad_Autopecas_Perfil` | `ID_Documento_Autorizacao_Fisco` | referência (Cad_Documento), opcional | A autorização do fisco de destino (41/08, § 4º, II e § 8º; BA, § 21). O ERP guarda e não valida |
| `Cad_Filial_Regime_Icms` | `Natureza_Regime` | enumeração {tributo, obrigacao_acessoria}, opcional | Distingue o regime de imposto (credenciamento de AL, dispensa de MG) do de obrigação acessória (substituir documento, centralizar escrita, dispensa, do MS). Vazio nas linhas anteriores |
| `Cad_Filial_Regime_Icms` | `Renovacao_Automatica` | booleano, opcional | O regime se renova sozinho se o contribuinte não tem pendência (MS) |
| `Cad_Filial_Regime_Icms` | `Prazo_Meses` | número, opcional | O prazo da concessão, quando a UF o fixa (MS: 6 meses) |

**Valores e domínios** (sem campo novo):

| Entidade | Mudança |
|---|---|
| `Cad_Classe_Sistema` | **4 domínios abertos novos:** `acordo_st_icms`, `metodo_calculo_st_uf`, `perfil_remetente_st` e `hipotese_nao_aplicacao_st`, com os valores das descrições acima. **Sem carga de UF** |
| `Cad_Classe_Sistema` (domínio `tipo_regime_icms`) | **6 valores novos**: `credenciamento_substituto_atacadista_pecas` (AL), `dispensa_st_autopecas_regime_especial` (MG, art. 73, § 1º), `acessorio_substituir_modificar_documento`, `acessorio_centralizar_escrita`, `acessorio_periodicidade_diferente` e `acessorio_dispensa_emissao_escrituracao_informacao` (MS) |
| `Cad_Motor_Regra` e filhas | **Carga:** 18 regras (Anexo A), provisórias |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao` | **Nenhum campo novo:** `Base_Calculo_St_Origem_Destino` recebe a base da memória; `Dispositivo_Inaplicabilidade_St` continua valendo para a cláusula nona do Convênio 142 |
| `Cad_Icms_Obrigacao_Recolher` | **Nenhum campo novo:** o código de receita de cada UF entra na carga e `Cad_Icms_St_Uf_Recolhimento` aponta para ele |
| `Mov_Inventario_Item_Complemento_St` | **Nenhum campo novo:** o estoque na entrada no regime reaproveita o complemento; o prazo e as parcelas estão em `Cad_Icms_St_Uf_Recolhimento` |

## 6.4 Exemplos numéricos

As alíquotas abaixo são **hipotéticas** (o protocolo não as fixa); servem só para conferir a fórmula. Preço do remetente R$ 1.000,00, frete R$ 50,00 na nota, base antes da MVA R$ 1.050,00, ICMS da operação própria sobre R$ 1.050,00.

| Caso | MVA original | ALQ inter | ALQ intra | MVA aplicada | Base de ST | ICMS sobre a base | ICMS próprio | Retido |
|---|---|---|---|---|---|---|---|---|
| A. Demais casos, destino com protocolo | 71,78% | 12% | 18% | ajustada, 84,3493% | R$ 1.935,67 | R$ 348,42 | R$ 126,00 | **R$ 222,42** |
| B. Fabricante com fidelidade | 36,56% | 12% | 18% | ajustada, 46,5522% | R$ 1.538,80 | R$ 276,98 | R$ 126,00 | **R$ 150,98** |
| C. Demais casos, origem em UF de 7% | 71,78% | 7% | 18% | ajustada, 94,8237% | R$ 2.045,65 | R$ 368,22 | R$ 73,50 | **R$ 294,72** |
| D. ALQ intra menor que a inter (§ 7º) | 71,78% | 12% | 7% | original, 71,78% | R$ 1.803,69 | R$ 126,26 | R$ 126,00 | **R$ 0,26** |
| E. Preço máximo de varejo fixado de R$ 2.400,00 | não usa | 12% | 18% | não usa | R$ 2.450,00 | R$ 441,00 | R$ 126,00 | **R$ 315,00** |

Na fórmula, o caso A é (1 + 0,7178) × (1 − 0,12) ÷ (1 − 0,18) − 1 = 0,843493. O caso D mostra o efeito do § 7º: sem ele, a MVA ajustada seria 62,54%, a base R$ 1.706,72 e o ICMS sobre a base (R$ 119,47) ficaria abaixo do ICMS próprio (R$ 126,00), com imposto retido negativo.

**F. Tabela publicada pela UF (PB, Anexo 05).** Mesmos R$ 1.050,00 e ICMS próprio de R$ 126,00 (12%). A tabela traz 88,96% para 71,78% com interestadual de 12% e alíquota interna de 20%: base de ST R$ 1.984,08 (1.050 × 1,8896), ICMS sobre a base R$ 396,82, retido **R$ 270,82**. O Motor usa o ajustado publicado (`Regra_Mva_Aplicada` = `mva_ajustada_tabelada_uf`) e confere com a fórmula: bate.

**G. Credenciamento de AL.** Valor do documento de entrada (com IPI, frete e seguros) R$ 1.000,00: imposto da ST R$ 107,90 (10,79%), sem o adicional de fundo. Não há MVA, base de preço nem ajuste: `ID_Metodo_Calculo` = `aliquota_fixa_sobre_documento_entrada` e `Criterio_Base_Aplicado` = `valor_documento_entrada`.

As alíquotas e os valores dos exemplos são **hipotéticos**, só para conferir a conta; os percentuais F e G são os lidos nas fontes da seção 2 e valem como ilustração, não como dado de carga.

# 7. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|---|---|---|
| 1 | UF sem regra de ST carregada | Peça com CEST ou NCM de autopeça e a UF de destino não tem linha vigente em `Cad_Icms_St_Acordo_Regra` na data e na operação da nota |
| 2 | Item fora da lista da UF | O CEST ou a NCM está como `excetuado` em `Cad_Icms_St_Lista_Item`, não está na lista positiva da UF, ou o CEST está vazio (o CEST vai em todo item: Convênio 142, cláusula 20ª) |
| 3 | Percentual da UF sem carga | O método usa percentual e não há linha vigente em `Cad_Icms_St_Uf_Mva` para o perfil do remetente, o CEST e a alíquota interestadual |
| 4 | Hipótese de não aplicação | A regra da UF tem hipótese com `Efeito` = `afasta_st` e o destinatário a cumpre; se `Exige_Indicar_Dispositivo_Na_Nota`, o aviso lembra de indicar o dispositivo |
| 5 | MVA de fidelidade sem autorização | `Regime_Fidelidade_Distribuicao` é `distribuicao_exclusiva_contrato_fidelidade` e `ID_Documento_Autorizacao_Fisco` está vazio, ou a UF exige a autorização |
| 6 | ALQ intra menor que a inter | O Motor aplicou a MVA original (`Usa_Mva_Original_Se_Alq_Intra_Menor`) |
| 7 | Frete fora da base | `Recolhe_Destinatario` verdadeiro: o destinatário recolhe o imposto do frete |
| 8 | UF fora do acordo | O destino saiu do acordo na data da nota (SP em 01/10/2026, RS em 01/11/2024; ES, GO e SC denunciaram): sem regra do acordo; conferir a regra própria da UF |
| 9 | Peça sem uso automotivo comprovado | O § 1º do 41/08 (e MG, art. 73) exige uso especificamente automotivo e o destinatário não tem perfil automotivo |
| 10 | Regra provisória | A regra, o percentual, o critério, o prazo ou a lista usada está `provisorio` |
| 11 | Nota anterior a 01/02/2023 | A data da nota é anterior à redação do Protocolo 95/22: valia o Anexo Único, que não foi carregado |
| 12 | Preço de referência não informado | O critério é `preco_maximo_orgao_publico`, `pmpf` ou `preco_sugerido_fabricante` e `Valor_Preco_Referencia` está vazio |
| 13 | Item em dois acordos da mesma UF | O item está na lista de duas regras da UF (por exemplo, 41/08 e 97/10 no MA): o Motor usou a de menor `Prioridade_Aplicacao` |
| 14 | Remetente do Simples Nacional | A regra tem `Remetente_Simples_Usa` diferente de `mva_ajustada` e o remetente é do Simples: usou a MVA original ou não ajustou |
| 15 | Método especial sem percentual | O método é IVA-ST, alíquota fixa ou antecipação na entrada e a linha de percentual não está carregada |
| 16 | Regime especial ativo | O remetente ou o destinatário tem em `Cad_Filial_Regime_Icms` um regime que dispensa ou altera a ST ou a obrigação acessória (credenciamento de AL, dispensa de MG, regime de MS) |
| 17 | Variação fora de campo | A regra da UF tem `Observacao_Regra` preenchida: a variação ainda não tem campo; conferir a observação e propor o campo |
| 18 | Regra da UF publicada fora do regulamento | `Fonte_Publicacao` é `portal_sefaz` ou `portaria`: conferir a publicação vigente na data da nota (BA, MT e SP) |

# 8. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| Q215-1 | Aprova as **7 entidades novas** como no 6.2: `Cad_Icms_St_Acordo_Regra` (21 campos), `Cad_Icms_St_Uf_Mva` (16), `Cad_Icms_St_Uf_Base_Criterio` (14), `Cad_Icms_St_Uf_Recolhimento` (16), `Cad_Icms_St_Uf_Nao_Aplicacao` (14), `Cad_Icms_St_Lista_Item` (16) e `Mov_Icms_St_Base_Calculo_Item` (27)? | Sim |
| Q215-2 | Aprova os **6 campos novos** em entidades existentes (3 em `Cad_Autopecas_Perfil` e 3 em `Cad_Filial_Regime_Icms`), os **4 domínios abertos** e os **6 valores novos** de `tipo_regime_icms` (6.3)? | Sim |
| Q215-3 | Aprova que **não haja carga de UF neste documento**: o que li fica no Anexo B como referência e a carga entra depois, UF por UF, com a fonte oficial e o grau de cada linha? | Sim |
| Q215-4 | Aprova as **18 regras** (Anexo A) e os **18 avisos** (seção 7) como texto do Motor, sempre sem bloquear (D-N284)? | Sim |
| Q215-5 | Quando for dar a carga, envia os textos oficiais que ainda faltam: o **Anexo X do RICMS-MT** e a **Portaria 195/2019**, o **Anexo 1 do RICMS-BA** (para eu transcrever os valores), o regulamento atual de ST do **RICMS-PR**, o **Decreto 90.309/2023 de AL** e os Protocolos **97/10, 93/26, 94/26 e 96/26** em PDF do CONFAZ? (AC, AM e DF já foram lidos.) | Enviar, sem pressa (só trava a carga) |
| Q215-6 | O domínio `antecipacao_entrada` (em `Tipo_Percentual`) e `percentual_na_antecipacao_entrada` (em `ID_Metodo_Calculo`) ficam como valores previstos mesmo sem UF que os use hoje, já que o PA era o único exemplo e era MVA ajustada? | Manter (domínio aberto, custo zero). **Aprovada em 12/11/2026 (D-N573).** |

# 9. O que acontece se você aprovar

- **Tudo (Q215-1 a Q215-5):** 7 entidades novas e 130 campos (124 nas entidades novas e 6 nas existentes, 3 no perfil de autopeças e 3 no regime de ICMS da filial), 29 campos de referência novos (28 nas entidades novas e 1 no perfil) e 4 domínios abertos novos. Sobre a revisão 42 (1.206 entidades, 13.895 campos, 3.586 campos de referência, 360 domínios e 247 mestres): **1.213 entidades, 14.025 campos, 3.615 campos de referência, 364 domínios e 253 mestres** (as seis entidades com vigência viram mestres). No ensaio com o gerador de DDL: 1.466 tabelas físicas (+13, com as seis tabelas de versão), 3.868 chaves estrangeiras (+35), 3.959 índices (+35) e 11.791 comentários (+123); a auditoria fecha com **0 achados em aberto**; as seis tabelas de cadastro entram na onda 3 (Contabilidade & Fiscal, de 642 para 648 entidades) e `Mov_Icms_St_Base_Calculo_Item`, na onda 4 (de 124 para 125). São somas do ensaio, a conferir no "consolidar".
- **Carga:** 4 domínios com 22 valores (4 de acordo, 5 de método de cálculo, 4 de perfil do remetente e 9 de hipótese de não aplicação), 6 valores novos em `tipo_regime_icms`, 18 regras e 18 avisos do Motor, tudo provisório. **Nenhuma linha de UF** (percentual, lista, prazo ou critério de base): isso entra depois, tabela por tabela, com o Anexo B como referência.
- **Ao contador:** dezesseis perguntas novas, C308 a C323 (documento 188, Parte 20); a Parte 20 da primeira versão (C308 a C316) é substituída por esta.
- **Se a Q215-1 vier "não":** a ST de autopeças segue o R15 do 209 (regra da UF, sem lugar para ela), e o usuário digita a MVA em `Mov_Apuracao_Tributo_Item.Valor_Mva` sem memória do cálculo e sem lugar para as variações por UF.

# 10. Limites

- **MT: só li uma resposta de consulta.** A SEFAZ-MT não entrega o texto do Anexo X pelo navegador e eu não contorno; a Portaria 195/2019 e o PMPF ficam sem leitura. **BA:** li o item 1.0 do Anexo 1, mas os valores não foram transcritos. **AC, AM e DF:** lidos em 12/11/2026 (AC e AM, versão atual; DF, texto compilado); **PR:** só a Resolução SEFA 20/2017, de 2018.
- **O que li de PI, AP, MA e DF é de 2008 a 2012** e as de AL, PR e RJ são cópias de terceiros sem data de atualização. Valem como prova de variação, não como valor para a carga.
- **SP:** não sei o que a UF aplica às autopeças depois de 01/10/2026 (C318). Os arts. 313-O e 313-P foram lidos em parte; o 313-P só por resumo.
- **A BA que li é o texto de 29/12/2020**, anterior à MVA própria de 2023 e ao Decreto 24.540/2026. O Anexo 1 não está no arquivo.
- **Os Protocolos 97/10 e 129/10** foram lidos em cópias truncadas de portais privados; as revogações de 2026, no despacho do DOU (93/26, texto lido) e em notícia da Senior (94/26 e 96/26, por notícia).
- **Dois resumos de leitura automática foram descartados por contradizerem o texto literal** (o do Anexo I do RJ e o do Anexo 05 da PB sobre o item 1.0); usei só o literal.
- **A ALQ intra** e a **ordem dos critérios** em cada UF são, quando não lidas no texto, leitura minha (C312, C322, C323).
- **O imposto da ST de ICMS acaba com a transição** (2029 a 2033). O desenho não projeta isso; a vigência das tabelas por UF aceita o fim quando a norma o disser.

# Anexo A. As 18 regras provisórias do Motor

| Regra | Se | Resultado | Fundamento | Vigência |
|---|---|---|---|---|
| R1 | Operação com peça de autopeça, regra vigente da UF e do tipo de operação em `Cad_Icms_St_Acordo_Regra`, item na lista (`alcancado`, ou CEST do Anexo II sem linha `excetuado`) e nenhuma hipótese de não aplicação cumprida | O **remetente** é o substituto e retém o ICMS das operações seguintes (ou o método da UF se aplica) | Protocolo 41/08, cláusula 1ª, caput e § 1º; regra da UF | conforme a regra da UF |
| R2 | A UF tem hipótese em `Cad_Icms_St_Uf_Nao_Aplicacao` cumprida pelo destinatário | `afasta_st`: a ST não se aplica e o Motor grava o dispositivo; `mantem_st`: a ST se aplica | 41/08, cláusula 1ª, § 2º; MG, art. 18; SP, art. 313-O, § 3º | conforme a regra da UF |
| R3 | Peça para renovação, recondicionamento ou beneficiamento, ou para ativo imobilizado ou uso e consumo | A ST se aplica; no ativo e no consumo vale o diferencial de alíquotas e o critério de base próprio | 41/08, cláusula 1ª, § 3º; cláusula 2ª, § 5º; MT, art. 8º | conforme a regra da UF |
| R4 | Remetente com `Papel_Substituto_St` diferente de `nao_substituto_subsequentes` | Responde pela retenção das saídas seguintes de **todas** as peças do § 1º, mesmo as excetuadas no caput | 41/08, cláusula 1ª, §§ 4º a 6º | 01/02/2023 |
| R5 | A regra tem critérios em `Cad_Icms_St_Uf_Base_Criterio` | O Motor percorre por `Ordem`, respeitando `Condicao_Uso`, e usa o primeiro critério com valor; o frete entra conforme `Inclui_Frete_Na_Base` | 41/08, cláusula 2ª; MT, art. 6º; MG, art. 20 | conforme a regra da UF |
| R6 | O critério usa percentual | Escolhe a linha de `Cad_Icms_St_Uf_Mva` pelo perfil do remetente, pelo CEST (a linha do CEST antes da geral) e pelo `Tipo_Percentual`; se há linha com a alíquota interestadual da operação, usa o ajustado publicado; senão calcula a fórmula | 41/08, cláusula 2ª, §§ 1º e 2º; PB, Anexo 05; RJ, item 7 | conforme a regra da UF |
| R7 | A fórmula da MVA ajustada | ALQ intra pela `Definicao_Alq_Intra` da regra, lida em `Cad_Aliquota` (ICMS, UF de destino), ou a carga efetiva se menor | 41/08, cláusula 2ª, § 1º, III; 97/10; 129/10; BA, art. 289, § 14 | conforme a regra da UF |
| R8 | A ALQ intra é menor que a ALQ inter e `Usa_Mva_Original_Se_Alq_Intra_Menor` é verdadeiro | Usa a MVA original, sem ajuste | 41/08, cláusula 2ª, § 7º; BA, art. 289, § 15 | conforme a regra da UF |
| R9 | O remetente é do Simples Nacional e a regra tem `Remetente_Simples_Usa` diferente de `mva_ajustada` | Usa a MVA original ou não aplica o ajuste | BA, art. 295, § 3º; MG, art. 20, § 6º | conforme a regra da UF |
| R10 | O método da UF não é MVA (IVA-ST, alíquota fixa sobre a nota de entrada, antecipação) | Aplica o percentual da linha correspondente sobre a base do critério, sem ajuste por alíquota, salvo se a linha for ajustada | SP, SRE 16/23; AL, Decreto 99.605, art. 4º | conforme a regra da UF |
| R11 | A base de ST foi formada | Imposto retido = base × ALQ intra, menos o ICMS da operação própria, mais o adicional de fundo, se a regra o fixa | 41/08, cláusula 3ª; AL, art. 4º, § 3º | conforme a regra da UF |
| R12 | Há imposto retido | Vencimento pela `Regra_Prazo` e `Dia_Numero` do `Tipo_Operacao`, com a guia e o código de receita da UF; GNRE específica por acordo quando `Guia_Especifica_Por_Acordo` | 41/08, cláusula 4ª; PI, art. 5º; BA, art. 295, § 2º | conforme a regra da UF |
| R13 | O frete não pode entrar na base | O destinatário recolhe o imposto correspondente, com o percentual | 41/08, cláusula 2ª, § 4º; MG, art. 20, § 1º, II | conforme a regra da UF |
| R14 | Operação interna e `Alcance_Operacao` inclui a interna | ST com o percentual, o prazo e a lista da regra interna | 41/08, cláusula 5ª; PI, art. 5º | conforme a regra da UF |
| R15 | Hipótese da cláusula nona do Convênio 142 (R14 do documento 209) | A inaplicabilidade continua valendo; o dispositivo vai à nota | Convênio 142, cláusulas 9ª e 20ª | sem fim fixado |
| R16 | O item está na lista de duas regras da UF | Vale a regra de menor `Prioridade_Aplicacao`; aviso 13 | MA, art. 6º do Anexo 4.41; BA, art. 289, § 21 | conforme a regra da UF |
| R17 | A UF exige autorização prévia (`Exige_Autorizacao_Fisco_Destino`) e o perfil não tem o documento | A MVA de fidelidade não vale: usa a de `demais`; aviso 5 | 41/08, cláusula 2ª, § 8º; BA, § 21 | conforme a regra da UF |
| R18 | Estoque na entrada no regime (`Tipo_Operacao` = `estoque_na_entrada_no_regime`) | O imposto do estoque segue o prazo, a guia e o número máximo de parcelas da linha; o inventário é o do Bloco H (motivo 06) | DF, Portaria SF 198/2008; AP, Decreto 145/2009 | conforme a regra da UF |

# Anexo B. Quadro de referência para a carga (não é carga)

Os números abaixo **não entram no dicionário neste documento**. Servem à carga futura, UF por UF; cada linha diz o grau da fonte (**O** oficial, **T** terceiro, **S** portal privado) e se está provavelmente superada.

| UF | Acordo e lista | MVA original (fidelidade e demais) | Ajustada publicada | Prazo | Grau e observação |
|---|---|---|---|---|---|
| MG | Anexo VII, Parte 2, item 1 (128 itens e o 999.0): 41/08 em 15 UFs; seis CEST só no interno | 71,78% na lista; art. 71: 36,56% interna, 46,55% (12%/18%), 59,88% (4%/18%), 48,97% (4%/12%) | Fórmula do art. 20, § 5º | Dia 9 do mês seguinte (art. 74) | O; código de receita não achado |
| SP | Art. 313-O (lista da CAT 68/19, Anexo XIV, **revogado em 01/10/2026**) | IVA-ST 47,19% e 72,15% (SRE 16/23, **revogada em 01/10/2026**) | Fórmula do § 2º do art. 1º da SRE 16/23 | Período de apuração da entrada ou art. 426-A (duas redações) | O; a regra posterior a 01/10/2026 não foi encontrada |
| PB | Anexo 05, itens 1.0 a 89.0 (CEST 01.001.00 a 01.089.00), alíquota 20% | 36,56% e 71,78% | 50,22%, 58,75%, 63,87% (fidelidade) e 88,96%, 99,69%, 106,14% (demais), para 12%, 7% e 4% | Não consta no Anexo | O, versão de 05/02/2025 |
| RJ | Anexo I, item 7 (7.1 a 7.132), 41/08 e 97/10 | 36,56% e 71,78% | 50,22% e 63,87% (fidelidade); 88,96% e 106,14% (demais) | Não consta | T, sem data |
| PA | Decreto 3.637/2024, art. 713-D (41/08 e 97/10); itens 42, 56, 63, 85, 90, 105 e 106 | 71,78% na lista interna | **MVA ajustada** (achado 19): 82,13% (12%) e 92,48% (7%) com interna de 17% (2022); 86,63% (12%), 97,23% (7%) e 103,59% (4%) com interna de 19% (2024) | Não consta | O (3.637) e T (2.588); colunas deduzidas pela fórmula, a confirmar (C321) |
| MA | Anexo 4.41, 126 itens sem CEST; 41/08 (itens 1 a 124) e 97/10 (1 a 98, 100, 125, 126) | 33,08% e 59,60% | Tabela com interna de 17% (não transcrita). Pela fórmula: fid. 41,09% (12%) e 49,12% (7%); demais 69,22% e 78,83% | Dia 9 | S, RA 25/2012: provavelmente superada |
| PI | Decreto 13.076/2008, Anexo Único (84 itens sem CEST) | 26,50% e 40% | Tabela com interna de 17% (não transcrita). Pela fórmula: fid. 34,1% (12%) e 41,7% (7%); demais 48,4% e 56,9% | Interestadual dia 9; interna dia 15 | S, 2008: superada (MVA hoje é da legislação interna) |
| AP | Decreto 1.517/2008 (Anexo V, 100 itens sem CEST) | 26,50% e 40% | Igual ao PI | Dia 9 | S, 2008: superada; estoque (Decreto 145/2009): 34,10% e 48,40%, 12 parcelas, código 1837 |
| AL | Decreto 99.605/2024: credenciamento de atacadistas de peças de motos; ST geral no Decreto 90.309/2023 (não lido) | Sem MVA: 10,79% sobre a nota de entrada (14% em pneus); FECOEP 1% | Não se aplica | Entrada dia 9; importação dia 15 do mês seguinte ao desembaraço | S; adicional de 5,39% acima de 20% de saídas para uma mesma empresa |
| BA | RICMS art. 289 (texto de 2020, desatualizado) e **Anexo 1 de 2026, item 1.0**: listas de 15 UFs para o 41/08 e para o 97/10 | MVA da legislação interna desde 01/06/2023; valores não transcritos | MVA ajustada com alíquota interna de 20,5%; valores não transcritos | GNRE específica por protocolo (art. 295, § 2º) | O (Anexo 1, 2026); **reler antes da carga** |
| PR | Resolução SEFA 20/2017, art. 5º (produtos do art. 27 do Anexo X, CEST, itens 1.0 a 128.0 e 999.0) | 36,56% (fidelidade) e 71,78% (demais) | Não consta | Não consta | O, mas só até a Resolução 928/2018; regulamento atual não lido |
| MT | Tabela II do Apêndice do Anexo X; base nos arts. 5º e 6º do Anexo X; MVA pela Portaria 195/2019 ou, na falta, pelo convênio ou protocolo | **Fidelidade de 36,56% não implementada**; MVA da Portaria 195/2019 (não lida) | Não lida | Não consta | O em cópia de terceiro (Consulta 18/2024); Anexo X e portaria não lidos |
| DF | Caderno I do Anexo IV, item 28 (lista com CEST; protocolos 54/13, 53/11, 5/11 e 41/08; desde 01/06/2011); item 23 revogado em 2008; Portaria SF 198/2008 (estoque) | 36,56% (fidelidade, com autorização do fisco do DF para máquinas agrícolas) e 71,78% (demais); MT, PR, PI, RS e SP: MVA do destino (28.17) | Fórmula do 28.4; MVA original se interna < interestadual (28.18) | Até o dia 9 do mês seguinte (28.10); estoque: declaração até 31/07/2008, 12 cotas (ato pontual) | O |
| AC | RICMS Título VII, Anexo I, Tabela I, item 2 (lista de 2.1 em diante); art. 36, I (estoque) e art. 93, II (dia 10), conforme minha leitura anterior | 36,56% e 71,78% | Fidelidade: 44,79% (12%), 53,01% (7%) e 53,90% (4%, **não confere**: a fórmula dá 57,95%); demais: 82,13%, 92,48% e 98,69% (interna de 17%) | Dia 10 (art. 93, II) | O |
| AM | Anexo II-A, itens 1 a 4 (desde 01/01/2016); art. 15, §§ 10 a 14 revogados em 27/04/2015 | 36,56% e 71,78% | Não consta | Não lido | O (multivigente) |
| RR | Consulta de 2015 (uso não automotivo fora da ST) | Não lida | Não lida | Não lida | O; regulamento não lido |

# Anexo C. Perguntas ao contador (C308 a C323, documento 188, Parte 20)

| Id | Assunto |
|---|---|
| C308 | Distrito Federal: o cabeçalho do 41/08 diz "Denunciado pelo DF (Despacho 88/08)" e também "adesão do DF por ato do Poder Executivo (Prot. 5/11)"; o caput lista o DF. A ST do protocolo vale hoje no DF e desde quando? |
| C309 | MVA original da legislação interna de AL, BA, MT, PR e PI para as peças: percentual por CEST ou NCM, por perfil do remetente, e vigência |
| C310 | Notas de 2021 a janeiro de 2023 (Anexo Único, revogado em 01/02/2023) e adesões anteriores: precisam ser carregadas? |
| C311 | "Uso especificamente automotivo" e "sujeita à ST nas operações internas do destino" (§ 1º): quem comprova e como tratar item do Anexo II vendido a quem não é do setor automotivo |
| C312 | A alíquota aplicada à base de ST e o tratamento do FCP da ST em cada UF, e qual definição da ALQ intra vale (interna ou carga efetiva; praticada pelo substituto; prevista para a operação substituída) |
| C313 | Autorização prévia do fisco de destino para a MVA de fidelidade (41/08, cláusula 2ª, § 8º; BA, art. 289, § 21): quais UFs exigem, formato e validade |
| C314 | Efeitos do Protocolo 93/26 e do 85/25: a linha de efeitos do caput diz "01.10.24"; confirmar 01/10/2026 e se o 85/25 (§ 2º-A) deixou efeito |
| C315 | Remessa a outro estabelecimento do mesmo titular não varejista: em que UFs a legislação "dispõe de forma diferente" (§ 2º, II) |
| C316 | Operação interna (cláusula 5ª) em cada UF signatária: adotou a ST de autopeças, com que MVA, prazo (PI: dia 15) e código de receita? |
| C317 | Protocolo 97/10 (e o 129/10, revogado pelo 96/26): quais UFs estão em vigor hoje em cada um, o que o 94/26 e o 96/26 mudam e se a lista de itens do 97/10 ainda é a do Anexo Único ou a do Convênio 142 |
| C318 | SP a partir de 01/10/2026: com o Anexo XIV da Portaria CAT 68/19 e a Portaria SRE 16/23 revogados, a ST de autopeças continua por outra portaria? Qual lista, qual IVA-ST e qual prazo valem (art. 313-O e 313-P)? |
| C319 | BA: o Anexo 1 atual (MVA própria de autopeças desde 01/06/2023, Decreto 24.540/2026), a tabela de MVA ajustada do portal da SEFAZ (art. 289, § 16), a autorização do § 21 e o tratamento do remetente do Simples (art. 295, § 3º) |
| C320 | AL: o credenciamento do Decreto 99.605/2024 (10,79% sobre a nota de entrada, FECOEP de 1% e adicional de 5,39%) se aplica a quais empresas; e qual a ST geral de autopeças do Decreto 90.309/2023 (Anexo I)? |
| C321 | PA: confirmar que os percentuais do decreto de 2022 (92,48% e 82,13%) e da lista de 2024 (103,59%, 97,23% e 86,63%) são a MVA ajustada para 4%, 7% e 12% (interna de 17% e de 19%) e qual coluna é qual; existe alguma antecipação na entrada de autopeças no PA? |
| C322 | MG: remessas de UF fora da lista do item 1.1 (arts. 13 e 15 do Anexo VII), a MVA de montadora do art. 71 por combinação de alíquotas e a dispensa por regime especial do art. 73, § 1º; e, nas demais UFs, a ordem dos preços da base (PMPF, preço sugerido, preço praticado) |
| C323 | AC: a tabela do item 2 traz 53,90% para a MVA de 36,56% com interestadual de 4% e interna de 17%; a fórmula dá 57,95%. Qual vale? E MT: a MVA da Portaria 195/2019 por CEST e a vigência da fidelidade (não implementada) |
