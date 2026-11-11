# Conferência de Cinco Normas: IN RFB 2.324, 2.308, 2.333, 2.119 e LC 225 — Documento 189

*Você enviou em 09/11/2026, sem mensagem, as normas abaixo e, perguntado, escolheu "conferir as cinco contra o dicionário". Este documento diz o que cada uma traz, o que o dicionário (revisão 34: 1.135 entidades e 12.739 campos) já cobre e o que falta. É **proposta**: **nada foi alterado no dicionário**. Só entra depois das suas respostas e do seu "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **IN 2.119/2022 (CNPJ) com as INs 2.333 e 2.340 e 2.345 já incorporadas.** O art. 9º lista as **cinco situações cadastrais** (ativa, suspensa, inapta, baixada e nula); o dicionário deixava esses valores "a conferir". O **art. 51** trata a inidoneidade das notas de emitente **inapto ou baixado** para o IRPJ, a CSLL, o IPI, o PIS e a Cofins, com datas de início próprias e uma exceção para quem comprova o pagamento; o dicionário só tem a regra da CBS e do IBS (art. 121 do Decreto 12.955), que é **outra** e vale **na data de emissão**. Proposta: 3 campos (Q189-2).
- **IN 2.333/2026.** Troca os Anexos VI (motivos de suspensão por inconsistência cadastral) e VIII (documentos e orientações) da IN 2.119 e revoga o art. 57, que deixava a Cocad alterar os anexos por ato próprio. **Os dois anexos são PDFs que não vieram**; sem eles não consigo carregar a lista de motivos (Q189-5).
- **IN 2.324/2026 (suspensão do IPI).** Cinco hipóteses de suspensão (arts. 2º a 19). O dicionário tem a estrutura (habilitação com número do ato, situação da suspensão, texto da nota, lista legal por NCM) mas **não tem** o registro da pessoa jurídica preponderantemente exportadora, a extinção da suspensão do art. 18 nem as listas da Lei 10.485. Proposta sem entidade nem campo novo: 6 valores de domínio (Q189-3).
- **IN 2.308/2026 (Repetro-Industrialização).** Muda as condições de habilitação (art. 4º, § 1º, da IN 1.901). O Repetro é **gancho** desde a Q94-5; proponho que continue assim e registro o que a norma exige para quando você marcar o perfil (Q189-4).
- **LC 225/2026.** É a mesma lei que você enviou em 03/11 e que sustenta os documentos 140, 185 e 187. **Conferi contra esta cópia as citações do dicionário listadas abaixo: conferem.** Duas observações sem campo novo (seção 6).

# 2. O que recebi e como li

| Norma | Data e publicação | Assunto | Como li |
|---|---|---|---|
| IN RFB 2.324 | 24/04/2026, DOU de 05/05/2026 | Suspensão do IPI (art. 5º da Lei 9.826/1999 e art. 29 da Lei 10.637/2002); revoga a IN 948/2009, o art. 1º da IN 1.364/2013 e o art. 2º da IN 1.424/2013 | Inteira. O Anexo Único (formulário do registro) é PDF e **não veio** |
| IN RFB 2.308 | 24/02/2026, DOU de 27/02/2026 | Altera a IN 1.901/2019 (Repetro-Industrialização) | Inteira (um artigo, que muda o art. 4º, § 1º) |
| IN RFB 2.333 | 30/06/2026, DOU de 10/07/2026 | Troca os Anexos VI e VIII da IN 2.119 e revoga o art. 57 | Inteira; **os Anexos I e II dela são PDFs que não vieram** |
| IN RFB 2.119 | 06/12/2022, DOU de 08/12/2022; visão multivigente até a IN 2.345 | CNPJ | Li os capítulos de formato, situações, efeitos e inidoneidade (arts. 2º, 9º, 10, 37, 38 e 48 a 51) e os anexos citados; **não li** os demais títulos (inscrição, alteração, baixa a pedido, procedimentos) nem os anexos em PDF |
| LC 225 | 08/01/2026; cópia impressa em 27/01/2026 ("este texto não substitui o publicado no DOU de 9.1.2026") | Código de Defesa do Contribuinte | Li os arts. 7º a 13, 28, 36, 40, 48 e 58 e os títulos de todos os capítulos; os arts. 41 a 47 estão nos documentos 185 e 187; não li com atenção os arts. 49 a 55 (alterações do Código Penal e de outras leis) |

Todos os textos são a visão do portal Normas da Receita ("este texto não substitui o publicado oficialmente"); para dado legal que vai à carga como `validado`, o contador confere com o DOU (Fase 0, seção 9).

# 3. IN 2.119 e IN 2.333: CNPJ

## 3.1 As cinco situações cadastrais (art. 9º)

O art. 9º diz que a inscrição pode ser **ativa, suspensa, inapta, baixada ou nula**, e o parágrafo único diz que a situação cadastral **não se confunde** com a condição de atividade ou inatividade para fins tributários. O dicionário tem `Cad_Participante_Situacao_Cnpj.ID_Situacao_Cadastral`, ligado ao domínio aberto `situacao_cadastral_cnpj`, cuja descrição diz que "o anexo da IN 2.345 não lista os valores; os iniciais são ativa, suspensa, inapta, baixada e nula, a conferir". **Confere com o art. 9º.** A carga dos cinco valores já pode ser registrada com a norma como fundamento (Q189-1).

## 3.2 Efeitos de cada situação (arts. 48 a 50)

| Situação | Efeitos que a norma lista | Já no dicionário? |
|---|---|---|
| Suspensa (art. 48) | Não obter incentivos fiscais e financeiros; não fazer operações de crédito com recursos públicos; não transacionar com bancos; **não emitir documento fiscal eletrônico** | A emissão é impedida pelo parâmetro `Cad_Dfe_Parametro_Regra.ID_Situacao_Cadastral_Impeditiva` (D-N272, art. 121 do Decreto 12.955), que hoje lista inapta, suspensa, nula e baixada |
| Inapta (art. 49) | Cadin; não participar de concorrência pública; não celebrar convênios e contratos com desembolso público; os mesmos efeitos da suspensão; **não emitir documento fiscal eletrônico** | Só a emissão; o resto é efeito sobre a empresa titular, que o ERP não decide |
| Baixada (art. 50) | Os mesmos efeitos, a partir da data da baixa; perde a validade o certificado e-CNPJ (§ 1º) | Só a emissão |

A **nula** aparece no art. 9º mas não tem artigo de efeitos nesta norma; o dicionário a inclui no impedimento por causa do Decreto 12.955, não da IN. Nada a mudar aqui; o ERP só registra.

## 3.3 Inidoneidade da nota de emitente inapto ou baixado (art. 51): a diferença

**O que a norma diz.** É **inidôneo**, e não produz efeitos tributários em favor de terceiro interessado, o documento emitido por entidade **declarada inapta ou baixada** (caput). Os valores do documento não podem ser: I, deduzidos como custo ou despesa na base do IRPJ e da CSLL; II, deduzidos na base do IRPF; III, usados como crédito não cumulativo de IPI, PIS/Pasep e Cofins; IV, usados para justificar qualquer outra dedução, abatimento, redução, compensação ou exclusão de tributos da RFB (§ 1º).

**Desde quando (§ 2º).** Depende do caso: entidade omissa, a partir da publicação do ADE; irregularidade em comércio exterior, desde a data do fato; inaptidão por inexistência de fato e demais hipóteses dos incisos III a IX do art. 38, a partir da data de produção de efeitos definida no ADE; entidade suspensa por um ano ou mais, a partir da publicação do ADE do art. 46; baixa, a partir da data da baixa informada; baixa de ofício, desde a data dos fatos que a causaram. Baixa a pedido: a partir da data da baixa (§ 3º).

**Exceção e consequência (§§ 5º a 8º).** O § 1º **não se aplica** se o adquirente ou tomador comprovar o **pagamento do preço e o recebimento dos bens ou a utilização dos serviços** (§ 5º); sem essa comprovação, a entidade fica sujeita ao IRRF do art. 61 da Lei 8.981/1995 sobre o valor pago (§ 6º). A inidoneidade por inaptidão ou baixa **não exclui** as outras formas de inidoneidade nem legitima os documentos emitidos antes das datas do § 2º (§ 7º), e o restabelecimento da inscrição não elide a inidoneidade dos períodos sem existência de fato comprovada (§ 8º).

**Como o dicionário trata hoje.** `Mov_Documento_Fiscal.Situacao_Idoneidade` ({idoneo, nao_idoneo, a_reavaliar}) só existe no documento recebido e marca `nao_idoneo` se o emitente estava em situação impeditiva **na data de emissão** (art. 121 do Decreto 12.955), com os quatro estados do parâmetro (inapta, suspensa, nula, baixada). Isso é a regra da CBS e do IBS. Para os tributos do art. 51 da IN 2.119 as diferenças são:

| Ponto | Regra do dicionário (Decreto 12.955, art. 121) | Art. 51 da IN 2.119 |
|---|---|---|
| Situações que tornam a nota inidônea | Inapta, suspensa, nula e baixada (parâmetro) | **Só inapta e baixada** |
| Data de início | Data de emissão do documento, com a situação vigente nela | **Data definida no ADE** (publicação, fato, produção de efeitos ou baixa, conforme o caso) |
| Efeito | Marca o documento; o crédito não reabre sozinho | Veda dedução (IRPJ, CSLL, IRPF), crédito de IPI, PIS e Cofins e outras reduções |
| Exceção | Correção manual com motivo e fundamento (D-N274 e D-N276) | **Comprovar pagamento e recebimento** (§ 5º); sem comprovação, IRRF do art. 61 da Lei 8.981 (§ 6º) |
| Número do ato e data de início do efeito | Não guarda | O § 2º exige a data do ADE; o dicionário não tem campo para o ato nem para a data |

**Proposta (Q189-2), 0 entidades e 3 campos:**

| **Entidade** | **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|---|
| `Cad_Participante_Situacao_Cnpj` | **Numero_Ato_Declaratorio** | *código (até 40), opcional* | Número do ADE que declarou a suspensão, a inaptidão ou a baixa, como veio da Receita ou digitado pelo contador. |
| `Cad_Participante_Situacao_Cnpj` | **Data_Inicio_Efeito_Inidoneidade** | *data, opcional* | A partir de quando os documentos do participante são inidôneos para os tributos do art. 51 da IN 2.119 (§ 2º). Só para inapta e baixada; digitada pelo contador a partir do ADE (o ERP não calcula, padrão D-N284). |
| `Mov_Documento_Fiscal` | **Situacao_Idoneidade_Federal** | *enumeração {idoneo, inidoneo_art_51, comprovado_pagamento_recebimento}, opcional* | Só no documento recebido. `inidoneo_art_51` quando o emitente era inapto ou baixado e o documento é de data igual ou posterior a `Data_Inicio_Efeito_Inidoneidade`; `comprovado_pagamento_recebimento` quando o usuário com a ação aprovar registra a comprovação do § 5º. O motivo e o fundamento usam o `Motivo_Situacao_Idoneidade` que já existe. |

**Regra do Motor (aviso, não bloqueio):** na apuração do IRPJ e da CSLL (despesa), do IPI, do PIS e da Cofins (crédito), o Motor **avisa** quando o documento está `inidoneo_art_51`; não retira o crédito sozinho (padrão D-N272). O IRRF do § 6º fica como **aviso**, sem cálculo, até o contador dizer o contrário (C216). A regra da CBS e do IBS (`Situacao_Idoneidade`) **não muda**.

## 3.4 IN 2.333: os anexos e o art. 57

A IN 2.333 troca o **Anexo VI** (tabela de motivos de suspensão por inconsistência cadastral, citada no art. 37, II) e o **Anexo VIII** (tabela de documentos e orientações) e revoga o **art. 57**, pelo qual a Cocad podia editar atos complementares para alterar os anexos. Consequências para o dicionário:

- **Anexo VI:** é a lista fechada de motivos de suspensão do inciso II do art. 37. Hoje `Motivo_Situacao_Cadastral` é texto livre "como veio da Receita". Com a lista, daria para ter o domínio `motivo_suspensao_cnpj` com vigência. **Não tenho a lista** (PDF não enviado): Q189-5 pede os anexos. Sem eles, nada muda.
- **Art. 57 revogado:** a partir de 10/07/2026 a Cocad deixa de poder alterar os anexos por ato próprio. Para o dicionário, a lista de motivos é dado legal com vigência e fundamento (a IN 2.333), carregada como `provisório` até o contador conferir.
- **Anexo VIII** (documentos para os atos cadastrais): fora do escopo do ERP (atendimento na Receita); sem proposta.

## 3.5 Outros pontos da IN 2.119

- **CNPJ alfanumérico (art. 2º, parágrafo único, e Anexo XV):** 14 posições, com previsão de implementação a partir de **julho de 2026** (IN 2.229, de 15/10/2024). O documento 50 já cobre; sem mudança.
- **Art. 38, VIII e IX, na redação da IN 2.340 (24/08/2026):** a inaptidão passa a alcançar também quem incorra em cancelamento, ausência ou indeferimento de **autorização da ANP** para comercializar combustíveis ou operar armazenamento. O dicionário tem `Cad_Participante_Autorizacao_Anp` (situação e motivo); a ligação é só informativa: o ERP pode **avisar** que a autorização cancelada é causa possível de inaptidão. Sem campo novo.
- **Comprovante (art. 10 e Anexo III):** substituído pela IN 2.345; já tratado no documento 56.

# 4. IN 2.324: suspensão do IPI

A norma disciplina o art. 5º da Lei 9.826/1999 e o art. 29 da Lei 10.637/2002. Vigência na publicação (art. 28); não se aplica ao Simples Nacional, nem nas compras, nem nas saídas, nem a estabelecimento equiparado a industrial (art. 25, salvo a hipótese do art. 5º).

| Cap. | Arts. | Quem compra com suspensão | Condição que a norma põe | Dicionário (revisão 34) |
|---|---|---|---|---|
| I | 2º a 5º | Industrial que produz ou monta autopropulsados (84.29, 84.32, 84.33, 87.01 a 87.06 e 87.11 da Tipi) | Produtos dos **Anexos I e II da Lei 10.485/2002**, empregados na produção das peças ou na montagem (art. 4º) | Sem lista dos anexos; falta a carga em `Cad_Lista_Legal_Item` |
| II | 6º a 8º | Fabricante **preponderante** de componentes, chassis, carroçarias, partes e peças para máquinas, implementos e veículos | Declaração do adquirente ao vendedor sob as penas da lei (art. 6º, § 1º); **informação à DRF ou Derat**, sem processo, com recibo de entrega para o desembaraço (arts. 7º e 8º) | Sem registro da informação |
| III | 9º | Fabricante preponderante de partes de aeronaves (Cap. 88) e de bens de TIC (art. 16-A da Lei 8.248) | Idem (declaração e informação) | Idem |
| IV | 10 a 18 | **Pessoa jurídica preponderantemente exportadora** | Exportação **superior a 50%** da receita bruta total de bens e serviços do ano anterior, todos os estabelecimentos, sem impostos sobre a venda (art. 12); **registro prévio por ADE** da DRF ou Derat do estabelecimento matriz, válido para todos os estabelecimentos (arts. 13 e 15); recurso em 10 dias (art. 15, § 2º); cancelamento a pedido ou de ofício, com recolhimento do imposto suspenso e **novo registro só depois de 2 anos** (art. 16, § 7º) | `Cad_Habilitacao_Regime_Especial` guarda o ato (`Numero_Habilitacao`), o titular e a situação, mas o tipo não existe e `Percentual_Minimo_Exportacao` é só do REPES |
| V | 19 | Estabelecimento que elabora produtos dos Caps. 2 a 4, 7 a 12, 15 a 20, 23 (com exceções), 28 a 31 e 64 e alguns códigos | Preponderante (mais de **60%** da receita bruta, art. 21); declaração e informação, como nos Caps. II e III | Idem |
| VII | 21 a 26 | Todos | Nota com a expressão **"Saída com suspensão do IPI"**, com o dispositivo legal, **sem destaque do imposto** (art. 24); crédito do remetente mantido (art. 23); uso só no processo produtivo (art. 22) | `Texto_Nota_Fiscal_Bens` já guarda a frase da habilitação |

**Extinção da suspensão (art. 18).** Para matérias-primas, produtos intermediários e embalagens comprados por preponderantemente exportadora, a suspensão **se extingue** com: I, a exportação (ou venda a comercial exportadora com fim específico) do produto em que foram usados; II, a venda no mercado interno; III, furto, roubo, inutilização, deterioração ou destruição, ou incorporação a produto que caiu em I ou II. No caso do inciso III há pagamento do IPI com acréscimos (parágrafo único). O dicionário tem o domínio `situacao_suspensao_regime_especial` com **suspensa, convertida em alíquota zero e revertida**, que é a lógica do REIDI e do REPES: **não tem as três extinções do art. 18**.

**Proposta (Q189-3): 0 entidades, 0 campos, 6 valores de domínio e 1 descrição.**

| Domínio ou campo | Mudança |
|---|---|
| `tipo_regime_especial_federal` (+2) | `ipi_pj_preponderantemente_exportadora` (arts. 10 a 17: o `Numero_Habilitacao` guarda o número do ADE; o titular é a pessoa jurídica, com o ADE emitido para o CNPJ do estabelecimento matriz, e a habilitação vale para todos os estabelecimentos) e `ipi_informacao_preponderante` (arts. 6º, 7º, 9º e 19: o número guardado é o do recibo de entrega da informação à DRF ou Derat) |
| `situacao_suspensao_regime_especial` (+3) | `extinta_exportacao`, `extinta_venda_mercado_interno` e `extinta_sinistro` (art. 18, I a III) |
| `tipo_lista_legal` (+1) | `ipi_suspensao_lei_10485` (Anexos I e II da Lei 10.485/2002, arts. 2º, 3º, 6º e 7º); **sem carga** até você enviar os anexos |
| `Cad_Habilitacao_Regime_Especial.Percentual_Minimo_Exportacao` | Só a **descrição**: passa a valer também para a pessoa jurídica preponderantemente exportadora (superior a 50%, art. 12; 60% de preponderância do art. 21 fica como regra de texto). O valor continua parâmetro com vigência |
| Regras de texto (avisos, sem bloqueio) | (a) o Motor **avisa** que a saída com suspensão do IPI exige a frase "Saída com suspensão do IPI" e o dispositivo legal, sem destaque (art. 24); (b) o ERP **avisa** quando o adquirente é optante do Simples Nacional ou equiparado a industrial (art. 25); (c) o ERP **avisa** quando o registro foi cancelado de ofício há menos de 2 anos e há novo pedido (art. 16, § 7º); (d) a venda com suspensão exige o número do ADE e a declaração do adquirente (art. 17), guardados na habilitação do cliente que a linha já referencia (`ID_Habilitacao` em `Mov_Nota_Fiscal_Saida_Item`) |

**O que continua com o contador (C217 e C218):** como apurar a preponderância (50% e 60%) e qual código de enquadramento legal do IPI (`enquadramento_ipi`, 3 dígitos) cada hipótese usa na nota.

# 5. IN 2.308: Repetro-Industrialização

A IN 2.308 reescreve o art. 4º, § 1º, da IN 1.901/2019, que fixa o que a pessoa jurídica precisa ter para ser **habilitada** no Repetro-Industrialização:

- **I:** objeto social no contrato ou estatuto e **CNAE** no CNPJ compatíveis com a atividade industrial admitida no regime;
- **II, a:** quem for **fabricante e fornecedor dos produtos finais** (art. 458, § 8º, do Decreto 6.759/2009) apresenta **contrato com ao menos uma pessoa jurídica beneficiária do Repetro ou do Repetro-Sped** que demonstre a obrigação de fabricar, ainda que a fabricação não tenha começado;
- **II, b:** o **fabricante intermediário** apresenta contrato com ao menos uma beneficiária do Repetro-Industrialização **habilitada na condição da alínea "a"**, que demonstre a obrigação de fabricar os produtos que fornecerá a ela.

**Dicionário.** O Repetro está como **gancho** desde a Q94-5 (você respondeu que os oito perfis sem resposta, entre eles o Repetro, "ficam como gancho para futuramente desenhar"). Há, porém, duas peças que já servem: `Cad_Habilitacao_Regime_Especial.ID_Contrato` (hoje "na co-habilitação, o contrato de empreitada") e `ID_Habilitacao_Principal` (hoje a habilitação do titular do projeto). A condição do fabricante intermediário (II, b) tem a **mesma forma** da co-habilitação: depende de um contrato e de uma habilitação principal de outra pessoa jurídica. Quando você marcar o perfil, o desenho é: um valor novo em `tipo_regime_especial_federal`, a condição (a ou b) como texto em `Fundamento_Legal` e as duas referências existentes. **Sem campo novo.**

**Proposta (Q189-4): continuar como gancho.** Nada é criado agora; esta seção fica registrada no documento 14. Se você quiser desenhar o Repetro-Industrialização, a lista legal por NCM do Decreto 12.955 (documento 90, tipo `repetro`) é o outro pedaço.

# 6. LC 225: conferência

**As citações do dicionário conferem com esta cópia.** Conferi: art. 11, § 2º, I, a (R$ 15 milhões e mais de 100% do patrimônio conhecido) e II (4 períodos consecutivos ou 6 alternados em 12 meses); § 7º (parte relacionada de pessoa jurídica baixada ou inapta nos últimos 5 anos, com R$ 15 milhões ou mais); art. 12, III (prazo de 30 dias) e § 5º (casos sem efeito suspensivo); art. 28, § 3º (a exclusão do Confia tem termo inicial na data do fato) e § 7º (readmissão após 2 anos); art. 36, § 3º (o OEA perde as facilitações desde a ciência do processo de exclusão); art. 40, §§ 1º a 3º (selos Confia e Sintonia por 1 ano, OEA por até 4 anos); art. 58 (os arts. 19 a 32 e 40 a 47 em 90 dias da publicação de 09/01/2026, ou seja, **09/04/2026**; o resto na publicação). Os vetos (art. 8º, II, e art. 31, § 2º, I, entre outros) batem com a D-N409.

**Duas observações, sem campo novo:**

1. **Art. 13 (medidas contra o devedor contumaz).** Lista o impedimento de benefícios fiscais, de uso de prejuízo fiscal e base negativa da CSLL para quitar tributos, de licitações e de vínculos com a administração, de recuperação judicial, a **inaptidão do CNPJ** enquanto durar a contumácia, e o rito do art. 23 da Lei 13.988. Pela Q140-2 (D-N447) a contumácia **só é registrada** em `Mov_Condicao_Devedor_Contumaz`; nada muda. A ligação com este documento é o art. 13, II: a contumácia pode levar à inaptidão da inscrição, e então vale o art. 51 da IN 2.119 (seção 3.3).
2. **Art. 48 (Lei 10.522, art. 2º, VI, § 10).** O devedor contumaz passa a constar no **Cadin**, e Estados, DF e Municípios informam a inclusão e a exclusão ao Ministério da Fazenda. O dicionário não guarda o registro no Cadin, nem para a contumácia nem para a inaptidão (IN 2.119, art. 49, I). Proponho **não criar** (o Cadin é do órgão; o ERP só registra).

# 7. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Q189-2: `Cad_Participante_Situacao_Cnpj` (2) e `Mov_Documento_Fiscal` (1) | 0 | 3 |
| Q189-1: carga de 5 valores em `situacao_cadastral_cnpj` | 0 | 0 |
| Q189-3: 6 valores de domínio e 1 descrição | 0 | 0 |
| **Total do documento 189** | **0** | **3** |

Sobre a revisão 34 (1.135 entidades e 12.739 campos): **1.135 entidades e 12.742 campos** se você aprovar tudo. A revisão 34 segue intacta até o "consolidar".

# 8. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q189-1** | Carregar as **cinco situações cadastrais** do art. 9º da IN 2.119 (ativa, suspensa, inapta, baixada, nula) em `situacao_cadastral_cnpj`, com `Situacao_Dado` provisório até o contador conferir com o DOU? | **Sim** |
| **Q189-2** | Criar os **3 campos** da seção 3.3 e o aviso do Motor para a inidoneidade do **art. 51** da IN 2.119 (só inapta e baixada; data do ADE; exceção do § 5º; IRRF do § 6º só como aviso)? A regra da CBS e do IBS não muda. | **Sim** |
| **Q189-3** | Aprovar a suspensão do IPI da IN 2.324 como na seção 4 (**6 valores de domínio**, 1 descrição e 4 avisos, sem entidade nem campo novo), com a carga dos Anexos I e II da Lei 10.485 só quando você enviar os anexos? | **Sim** |
| **Q189-4** | O **Repetro-Industrialização** continua como **gancho** (Q94-5), com a IN 2.308 registrada no documento 14 para o desenho futuro? | **Sim, continua gancho** |
| **Q189-5** | Enviar os PDFs que faltam: **Anexo I e Anexo II da IN 2.333** (motivos de suspensão do CNPJ e documentos), **Anexo Único da IN 2.324** (formulário do registro) e os **Anexos I e II da Lei 10.485/2002**? Sem eles não há carga nem domínio de motivos. | **Enviar** quando puder; nada trava |

# 9. Perguntas para o contador

Entram no **documento 188**, na Parte 6 (C216 a C218), e não aqui (D-N501): **C216**, como o ERP deve tratar o art. 51 da IN 2.119 (IRRF do § 6º, comprovação do § 5º e datas do § 2º); **C217**, como apurar a preponderância exportadora (50%) e produtora (60%) e se o ERP só avisa ou calcula; **C218**, quais códigos de enquadramento legal do IPI valem para cada hipótese de suspensão da IN 2.324.

# 10. Limites do que eu li

- Li os textos do portal Normas da Receita e do Planalto, impressos em 09/11/2026 e 27/01/2026; **não conferi no DOU**.
- **Não li** os anexos em PDF (IN 2.324, IN 2.333 e IN 2.119, Anexos VI, VIII e XV) nem a IN 2.340 e a IN 2.345 em si; só a redação delas como aparece na IN 2.119 multivigente.
- **Não li** os títulos da IN 2.119 sobre inscrição, alteração e baixa a pedido, nem a IN 1.901, nem a Lei 10.485/2002, nem o art. 121 do Decreto 12.955 (cito a regra como o dicionário a descreve).
- Não li o recibo nem os atos da Receita de nenhuma habilitação real; não há dados de cliente.
- O desenho é proposta minha; nenhuma recomendação foi confirmada pelo contador.
