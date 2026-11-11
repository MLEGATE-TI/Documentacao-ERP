# Carga dos Anexos Recebidos: IN RFB 2.333, Lei 10.485/2002 e IN RFB 2.324 — Documento 190

*Você enviou em 09/11/2026, sem mensagem, o DOU de 10/07/2026 com a IN 2.333 (com os Anexos I e II), a Lei 10.485/2002 compilada (com os Anexos I e II) e o DOU de 05/05/2026 com a IN 2.324 (com o Anexo Único). Li como resposta à Q189-5. Este documento lê os anexos, propõe a carga e o desenho e faz as perguntas. É **proposta**: **nada foi alterado no dicionário** (revisão 34: 1.135 entidades e 12.739 campos).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **Anexo I da IN 2.333 (motivos de suspensão do CNPJ).** São **21 incisos**, e o inciso XVI tem 4 alíneas: **24 valores**. Hoje o motivo é texto livre. Proponho carregar a lista como domínio com vigência a partir de **10/07/2026** e ligar cada motivo à situação cadastral por **1 entidade filha pequena, com 4 campos**, porque uma inscrição pode ser suspensa por mais de um motivo (Q190-1).
- **Anexo II da IN 2.333 (documentos e orientações por natureza jurídica).** É a lista do que a Receita pede para inscrever e alterar cada tipo de entidade. É atendimento na Receita; **proponho não carregar** (Q190-2).
- **Anexos I e II da Lei 10.485/2002.** O Anexo I tem **51 códigos** (5 com Ex da Tipi) e o Anexo II tem **15 itens**, cada um com restrição de uso ("próprio para" certas máquinas). Servem a **duas regras**: a suspensão do IPI (art. 4º, parágrafo único, da Lei 10.485 e IN 2.324) e o regime de PIS/Cofins dos arts. 3º e seguintes (alíquotas de 1,65% e 7,6%, de 2,3% e 10,8% e de 0%, e retenção na fonte). Proponho **uma lista só**, com **66 linhas provisórias**, no lugar do valor `ipi_suspensao_lei_10485` que eu tinha proposto na Q189-3 (Q190-3).
- **Anexo Único da IN 2.324 (requerimento do registro).** É um formulário de identificação e declaração; todos os dados já existem no cadastro do participante e na habilitação. **Sem campo novo** (Q190-4).
- **Duas portarias vieram na mesma página do DOU.** A **Portaria RFB 703/2026** fixa a jurisdição dos contribuintes do **Confia** por carteira setorial e cita a **IN RFB 2.295/2025**, que parece ser o ato do Confia que a Q187-3 pedia (Q190-6). A Portaria RFB 702/2026 trata do órgão de julgamento de recurso de devedor contumaz; sem mudança.
- **Uma lacuna que apareceu:** a **retenção na fonte do art. 3º, § 3º, da Lei 10.485** (0,1% de PIS e 0,5% de Cofins, quinzenal) não está no dicionário. Proponho desenhar depois, com o contador (Q190-5).
- **Contagem:** este documento propõe **1 entidade e 4 campos**; com os 3 campos do documento 189, a revisão 34 iria a **1.136 entidades e 12.746 campos** se tudo for aprovado.

# 2. O que recebi e como li

| Arquivo | O que é | Como li |
|---|---|---|
| IN RFB 2.333/2026 (DOU 10/07/2026, seção 1, p. 102 e 103) | Substitui os Anexos VI e VIII da IN 2.119 e revoga o art. 57 | Texto e **Anexo I inteiro**. O **Anexo II** é uma tabela longa de várias colunas que o PDF desmonta ao extrair; li o que a tabela é e **não a transcrevi** |
| Lei 10.485/2002 compilada (Planalto, impressa em 09/11/2026) | PIS/Cofins de máquinas, veículos e autopeças; suspensão do IPI (art. 4º altera o art. 5º da Lei 9.826) | Lei inteira e os dois anexos. O texto avisa que "não substitui o publicado no DOU de 4.7.2002" |
| IN RFB 2.324/2026 (DOU 05/05/2026, p. 64) | Suspensão do IPI | Mesmo texto do documento 189; li o **Anexo Único** e o art. 13 |

A mesma página do DOU da IN 2.333 traz ainda a Portaria RFB 702/2026 e a Portaria RFB 703/2026 (seção 6).

# 3. Anexo I da IN 2.333: motivos de suspensão do CNPJ

O art. 37, II, da IN 2.119 manda suspender a inscrição por inconsistência cadastral; o Anexo I (que passa a ser o Anexo VI da IN 2.119) lista os motivos. Os 24 valores, como proponho carregar (resumidos por mim; o texto integral fica no `Fundamento_Legal`):

| Inciso | Motivo (resumido) |
|---|---|
| I | Omissão da identificação do representante (art. 6º da IN 2.119) |
| II | CPF do representante inexistente ou cancelado, titular falecido, nulo ou suspenso |
| III | Omissão do Quadro de Sócios e Administradores (QSA) |
| IV | Divergência entre o QSA e o quadro do órgão de registro (entidades do Anexo V) |
| V | CPF de integrante do QSA (pessoa física) inexistente, cancelado, nulo ou suspenso |
| VI | CNPJ de integrante do QSA (pessoa jurídica) suspenso, inapto, baixado ou nulo |
| VII | Omissão do ente federativo responsável (administração pública) |
| VIII | Omissão da atividade econômica |
| IX | Divergência entre a atividade econômica informada e a constatada |
| X | Atividade sem autorização do órgão competente |
| XI | Omissão, total ou parcial, de endereço |
| XII | Omissão do capital social ou erro na somatória (entidades obrigadas a informar) |
| XIII | Suspensão do registro ou de ato alterador no órgão de registro |
| XIV | CPF do titular da empresa individual como titular falecido, sem a situação especial de inventário |
| XV | Informações cadastrais inválidas, para burlar ou dificultar a localização ou o contato |
| XVI, a | Termo no nome empresarial ou nome fantasia em desacordo com as normas do DREI |
| XVI, b | Termo que reproduz ou imita nome ou sigla de tributo, órgão ou entidade pública, ou marca notoriamente conhecida |
| XVI, c | Termo com caracteres inespecíficos, fragmentação ou substituições alfanuméricas que impedem a identificação |
| XVI, d | Termo que indica incompatibilidade manifesta e relevante com o tipo societário |
| XVII | E-mail que remete ao nome empresarial ou fantasia de outra entidade |
| XVIII | Incompatibilidade manifesta e relevante entre o CNAE e a natureza jurídica, finalidade, nome ou título do estabelecimento |
| XIX | Uso, sem autorização, de endereço ou telefone de terceiro |
| XX | Incompatibilidade entre a capacidade econômica de integrante do QSA e sua participação no capital |
| XXI | Informação cadastral manifestamente falsa, inconsistente ou contraditória com os documentos constitutivos |

**Dicionário hoje.** `Cad_Participante_Situacao_Cnpj` tem `Motivo_Situacao_Cadastral` (texto "como veio da Receita"). Um campo de texto não guarda **mais de um motivo** nem permite filtrar.

**Proposta (Q190-1): 1 entidade e 4 campos, mais 24 valores de domínio.**

| Item | Mudança |
|---|---|
| Domínio `motivo_suspensao_cnpj` (em `Cad_Classe_Sistema`) | 24 valores, `Situacao_Dado` provisório, vigência a partir de **10/07/2026** (data de publicação, art. 3º da IN 2.333), fundamento "IN RFB 2.333/2026, Anexo I (Anexo VI da IN 2.119), inciso X". A lista antiga do Anexo VI **não veio**: o que a Receita informou antes de 10/07/2026 fica no texto livre |
| Entidade nova `Cad_Participante_Situacao_Cnpj_Motivo` | `ID_Participante_Situacao_Cnpj_Motivo` (identidade); `ID_Participante_Situacao_Cnpj_Versao` (referência à versão da situação que tem o motivo); `ID_Motivo_Suspensao` (referência, domínio `motivo_suspensao_cnpj`); `Texto_Origem` (texto, opcional: como a consulta trouxe o motivo) |
| `Motivo_Situacao_Cadastral` | Continua, como texto de origem da situação; a descrição passa a dizer que o motivo estruturado está na entidade filha |

O ERP **não decide o motivo**: quem liga o texto da Receita a um inciso é o contador ou a carga da consulta, e o ERP **avisa** (sem bloquear) quando a situação é suspensa e não há motivo ligado. Como o art. 37 vale só para suspensão, a entidade filha só é usada nessa situação.

# 4. Anexo II da IN 2.333: documentos e orientações

O Anexo II (Anexo VIII da IN 2.119) é uma tabela por **natureza jurídica** (Empresário Individual, sociedades, associações, fundações, consórcios, partidos, condomínios, entidades estrangeiras e outras): para cada uma diz a **data que vale** (registro, transmissão, ato), os **documentos** que acompanham a inscrição e a **base legal** (Código Civil, Lei 6.015, Lei 8.934, Lei 11.107 e outras). Abre com regras sobre o **nome empresarial** (fiel ao ato constitutivo; ME e EPP sem a partícula "ME" ou "EPP"; padrão de nome para os órgãos de partido político).

Isso é o balcão da Receita para inscrever e alterar o CNPJ; o ERP **não faz inscrição**. O que o dicionário já guarda (`Cad_Natureza_Juridica` com vigência) cobre o que o ERP usa. **Proposta (Q190-2): não carregar, sem campo novo.** Se um dia o ERP cadastrar entidade nova para o cliente, o desenho nasce desta tabela.

# 5. Anexos I e II da Lei 10.485/2002

## 5.1 Para que servem

O mesmo par de anexos é citado em **três lugares** da lei:

| Dispositivo | Regra |
|---|---|
| Art. 3º, I e II | Fabricantes e importadores de autopeças dos anexos: PIS 1,65% e Cofins 7,6% nas vendas **para fabricante** dos produtos do art. 1º (ou de autopeças dos anexos para fabricação deles); 2,3% e 10,8% nas vendas a atacadista, varejista ou consumidor |
| Art. 3º, § 2º | **0%** para o atacadista ou varejista que vende esses produtos |
| Art. 3º, §§ 3º a 7º | **Retenção na fonte** de 0,1% (PIS) e 0,5% (Cofins) nos pagamentos de autopeças dos anexos (exceto pneus) feitos por pessoa jurídica fabricante; vale como antecipação; recolhimento até o último dia útil da quinzena seguinte; não se aplica ao optante do Simples nem ao atacadista ou varejista; alcança a industrialização por encomenda |
| Art. 4º, parágrafo único | A suspensão do IPI do art. 5º, § 2º, I, da Lei 9.826 vale **só** para produtos dos anexos destinados à produção dos autopropulsados |

O texto traz em vários artigos a nota "(Vide Lei Complementar nº 214, de 2025) Produção de efeitos": o regime de PIS/Cofins da lei pode ter fim ou mudança pela reforma, e o prazo de cada artigo é matéria do contador (C219).

## 5.2 Anexo I: 51 códigos

Li o anexo em duas colunas e contei **51 linhas** (5 com Ex da Tipi). Ordenei por código para a carga; o anexo não tem ordem. Dois códigos têm nota: 8536.50.90 Ex 01 ("redação dada pelo Decreto nº 6.006, de 2006", e o art. 3º, § 1º, autoriza o Executivo a alterar a relação).

| Nº | NCM (como no anexo) | Nível | Ex da Tipi |
|---:|---|---|---|
| 1 | 68.13 | posição |  |
| 2 | 85.11 | posição |  |
| 3 | 87.07 | posição |  |
| 4 | 87.08 | posição |  |
| 5 | 4016.10.10 | item (NCM completa) |  |
| 6 | 4016.99.90 | item (NCM completa) | Ex 03 e 05 |
| 7 | 7007.11.00 | item (NCM completa) |  |
| 8 | 7007.21.00 | item (NCM completa) |  |
| 9 | 7009.10.00 | item (NCM completa) |  |
| 10 | 7320.10.00 | item (NCM completa) | Ex 01 |
| 11 | 8301.20.00 | item (NCM completa) |  |
| 12 | 8302.30.00 | item (NCM completa) |  |
| 13 | 8407.33.90 | item (NCM completa) |  |
| 14 | 8407.34.90 | item (NCM completa) |  |
| 15 | 8408.20 | subposição |  |
| 16 | 8409.91 | subposição |  |
| 17 | 8409.99 | subposição |  |
| 18 | 8413.30 | subposição |  |
| 19 | 8413.91.00 | item (NCM completa) | Ex 01 |
| 20 | 8414.80.21 | item (NCM completa) |  |
| 21 | 8414.80.22 | item (NCM completa) |  |
| 22 | 8415.20 | subposição |  |
| 23 | 8421.23.00 | item (NCM completa) |  |
| 24 | 8421.31.00 | item (NCM completa) |  |
| 25 | 8431.41.00 | item (NCM completa) |  |
| 26 | 8431.42.00 | item (NCM completa) |  |
| 27 | 8433.90.90 | item (NCM completa) |  |
| 28 | 8481.80.99 | item (NCM completa) | Ex 01 e 02 |
| 29 | 8483.10 | subposição |  |
| 30 | 8483.20.00 | item (NCM completa) |  |
| 31 | 8483.30 | subposição |  |
| 32 | 8483.40 | subposição |  |
| 33 | 8483.50 | subposição |  |
| 34 | 8505.20 | subposição |  |
| 35 | 8507.10.00 | item (NCM completa) |  |
| 36 | 8512.20 | subposição |  |
| 37 | 8512.30.00 | item (NCM completa) |  |
| 38 | 8512.40 | subposição |  |
| 39 | 8512.90.00 | item (NCM completa) |  |
| 40 | 8527.2 | subposição parcial |  |
| 41 | 8536.50.90 | item (NCM completa) | Ex 01 (redação do Decreto 6.006/2006; ver art. 3º, § 1º) |
| 42 | 8539.10 | subposição |  |
| 43 | 8544.30.00 | item (NCM completa) |  |
| 44 | 8706.00 | subposição |  |
| 45 | 9029.20.10 | item (NCM completa) |  |
| 46 | 9029.90.10 | item (NCM completa) |  |
| 47 | 9030.39.21 | item (NCM completa) |  |
| 48 | 9031.80.40 | item (NCM completa) |  |
| 49 | 9032.89.2 | item parcial |  |
| 50 | 9104.00.00 | item (NCM completa) |  |
| 51 | 9401.20.00 | item (NCM completa) |  |

Os códigos de 4 dígitos ou menos precisos (por exemplo 87.08, 8527.2 e 9032.89.2) valem para tudo o que está abaixo; `Cad_Lista_Legal_Item.ID_Classificacao_Mercadoria` já aceita a NCM em qualquer nível.

## 5.3 Anexo II: 15 itens com destino restrito

| Item | NCM | Produto | Próprio(a) para |
|---|---|---|---|
| 1 | 40.09 | Tubos de borracha vulcanizada não endurecida, com acessórios | máquinas e veículos das posições 84.29, 8433.20, 8433.30.00, 8433.40.00, 8433.5 e 87.01 a 87.06 |
| 2 | 84.31 | Partes reconhecíveis como exclusiva ou principalmente destinadas às máquinas | posições 84.29 |
| 3 | 8408.90.90 | Motores | 84.29, 8433.20, 8433.30.00, 8433.40.00 e 8433.5 |
| 4 | 8412.21.10 | Cilindros hidráulicos | 84.29, 8433.20, 8433.30.00, 8433.40.00 e 8433.5 |
| 5 | 8412.21.90 | Outros motores hidráulicos de movimento retilíneo (cilindros) | 84.29, 8433.20, 8433.30.00, 8433.40.00 e 8433.5 |
| 6 | 8412.31.10 | Cilindros pneumáticos | 8701.20.00, 87.02 e 87.04 |
| 7 | 8413.60.19 | Bombas volumétricas rotativas | 84.29, 8433.20, 8433.30.00, 8433.40.00, 8433.5, 8701.20.00, 87.02 e 87.04 |
| 8 | 8414.80.19 | Compressores de ar | 8701.20.00, 87.02 e 87.04 |
| 9 | 8414.90.39 | Caixas de ventilação para veículos autopropulsados | (sem restrição de destino além do próprio texto) |
| 10 | 8432.90.00 | Partes | máquinas das posições 8432.40.00 e 8432.80.00 |
| 11 | 8481.10.00 | Válvulas redutoras de pressão | máquinas e veículos 84.29, 8433.20, 8433.30.00, 8433.40.00, 8433.5 e 87.01 a 87.06 |
| 12 | 8481.20.90 | Válvulas para transmissões óleo-hidráulicas ou pneumáticas | 84.29, 8433.20, 8433.30.00, 8433.40.00 e 8433.5 |
| 13 | 8481.80.92 | Válvulas solenóides | máquinas e veículos 84.29, 8433.20, 8433.30.00, 8433.40.00, 8433.5 e 87.01 a 87.06 |
| 14 | 8483.60.1 | Embreagens de fricção | 84.29, 8433.20, 8433.30.00, 8433.40.00 e 8433.5 |
| 15 | 8501.10.19 | Outros motores de corrente contínua | acionamento elétrico de vidros de veículos autopropulsados |

Cada item vale **só quando próprio para** as máquinas e os veículos da última coluna. O Motor **sugere**; o usuário confirma na linha da operação (a regra da `Restricao_Tecnica`).

## 5.4 Proposta (Q190-3): 66 linhas e nenhum campo novo

`Cad_Lista_Legal_Item` já tem o que precisa. A carga, toda `provisório`:

| Campo | Valor |
|---|---|
| `ID_Tipo_Lista` | `autopecas_lei_10485` (**uma lista só**, usada pelo IPI e pelo PIS/Cofins; substitui o `ipi_suspensao_lei_10485` da Q189-3) |
| `Codigo_Anexo` | "Anexo I" (51 linhas) e "Anexo II, item N" (15 linhas) |
| `ID_Classificacao_Mercadoria` | A NCM em qualquer nível, como no anexo |
| `Restricao_Tecnica` | Anexo I: o **Ex da Tipi**, quando houver ("Ex 03 e 05"). Anexo II: o texto "próprio para" da seção 5.3 |
| `Eh_Excecao` | Falso em todas as linhas (os anexos não têm "exceto") |
| `Fundamento_Legal` | "Lei 10.485/2002, Anexo I (ou Anexo II, item N), cópia compilada do Planalto de 09/11/2026" |
| `Vigencia_Inicio` | **01/11/2002**: o art. 7º da lei dá efeitos a partir do primeiro dia do quarto mês seguinte ao da publicação (4/7/2002). Alterações por decreto (art. 3º, § 1º) ficam para o contador (C219) |
| `ID_Aliquota` | Vazio na carga: a alíquota depende do uso (IPI suspenso, PIS/Cofins do art. 3º), e o Motor busca pela regra geral (D-N199) |

**O que muda no documento 189.** O valor de domínio `ipi_suspensao_lei_10485` sai e entra `autopecas_lei_10485`, para não carregar a mesma lista duas vezes. Os outros cinco valores da Q189-3 ficam como estavam.

**Retenção do art. 3º, § 3º (Q190-5).** Não achei no dicionário a retenção de 0,1% e 0,5% do fabricante (`Cad_Retencao_Federal_Parametro` hoje tem as retenções do Mafon, por órgão pagador, e os campos `Percentual_Pis` e `Percentual_Cofins` serviriam, mas o `Ente_Pagador` não cabe). Proponho **não desenhar agora**: pergunto ao contador (C219) como ele quer ver essa retenção e desenho depois.

# 6. Anexo Único da IN 2.324 e as duas portarias

## 6.1 Requerimento de registro (Anexo Único da IN 2.324)

O formulário "Requerimento de registro para pessoa jurídica preponderantemente exportadora, regime de suspensão do IPI" tem: identificação da pessoa jurídica (CNPJ), endereço, representante legal (nome, CPF e telefone), a declaração de que cumpre o art. 29 da Lei 10.637 e de que está ciente das penas por falsidade, a assinatura e o carimbo de recepção da Receita. O art. 13 lista os documentos que o acompanham: ato constitutivo; relação de sócios e administradores com CPF; relação das pessoas jurídicas sócias com CNPJ; declaração das condições do art. 12 com comprovantes; **relação dos principais fornecedores** (nome, CNPJ, endereço e valor adquirido no ano anterior).

Tudo isso é dado que o ERP **já tem** (participante, endereço, representante, quadro societário) ou é documento que se entrega na Receita. O ERP **só registra** o ADE de concessão no `Numero_Habilitacao` (documento 189). **Proposta (Q190-4): sem campo novo.** A relação de principais fornecedores é um relatório possível sobre as notas de entrada do ano anterior, se você quiser, em outro documento.

## 6.2 Portaria RFB 703/2026: jurisdição do Confia

Fixa que os contribuintes do **Programa de Conformidade Cooperativa Fiscal (Confia)** ficam sob a jurisdição de quatro unidades, conforme a **carteira setorial** do Anexo Único: **DRF Manaus (12 carteiras), DRF Salvador (14), DRF Florianópolis (10) e Deope São Paulo (19)**, num total de **55 carteiras**. Os contribuintes que já estavam na Deinf/SPO e na Demac/RJO ficam onde estão (art. 3º). Cita a **IN RFB 2.295/2025** e os Comitês Permanentes da Portaria RFB 658/2026.

Para o ERP isso é informação de quem atende o contribuinte, não regra de cálculo. **Proposta (Q190-4): não criar campo**; a carteira e a unidade ficam registradas só neste documento e no 14. Se você quiser mostrar ao usuário "sua carteira é X, atendida por Y", é uma tabela de 55 linhas, e eu desenho.

**A IN 2.295/2025 muda a Q187-3.** Perguntei se você tinha o ato da Receita que regulamenta o Confia (LC 225, art. 29). A portaria diz que a regra do programa está na IN 2.295/2025. **Não a li.** Proponho que você a envie (Q190-6) para eu conferir contra o desenho do Confia dos documentos 185 e 187.

## 6.3 Portaria RFB 702/2026

Altera a Portaria RFB 309/2023 (contencioso administrativo): os recursos de quem for **qualificado definitivamente como devedor contumaz** vão às turmas recursais, e o órgão se define pela situação do sujeito passivo **na data do recurso** (art. 2º, § 2º); a qualificação ou o seu afastamento não muda o órgão de recurso já interposto (§ 3º). O dicionário tem `Mov_Condicao_Devedor_Contumaz`; o processo administrativo fiscal não é do ERP. **Sem mudança.**

# 7. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Q190-1: `Cad_Participante_Situacao_Cnpj_Motivo` | 1 | 4 |
| Q190-1: 24 valores de domínio `motivo_suspensao_cnpj` | 0 | 0 |
| Q190-3: 66 linhas de carga em `Cad_Lista_Legal_Item` (troca de nome do valor da Q189-3) | 0 | 0 |
| **Total do documento 190** | **1** | **4** |

Sobre a revisão 34 (1.135 entidades e 12.739 campos): **1.136 entidades e 12.746 campos** se você aprovar os documentos 189 e 190 inteiros (3 campos do 189 e 4 do 190). A revisão 34 segue intacta até o "consolidar". As cargas (24 valores e 66 linhas) não contam como campos.

# 8. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q190-1** | Carregar os **24 motivos** do Anexo I da IN 2.333 como domínio `motivo_suspensao_cnpj` (provisório, a partir de 10/07/2026) e criar a entidade filha `Cad_Participante_Situacao_Cnpj_Motivo` (**4 campos**) para ligar mais de um motivo a cada situação suspensa? | **Sim** |
| **Q190-2** | O **Anexo II da IN 2.333** (documentos por natureza jurídica) fica **fora** do ERP, sem carga? | **Sim, fora** |
| **Q190-3** | Carregar os **Anexos I e II da Lei 10.485** (51 + 15 = 66 linhas, provisórias, vigência 01/11/2002) em **uma lista só**, `autopecas_lei_10485`, no lugar do `ipi_suspensao_lei_10485` da Q189-3? | **Sim** |
| **Q190-4** | O **Anexo Único da IN 2.324** e a **carteira setorial do Confia** (Portaria 703) ficam **sem campo novo**? | **Sim, sem campo** |
| **Q190-5** | A **retenção do art. 3º, § 3º, da Lei 10.485** (0,1% PIS e 0,5% Cofins) fica para ser desenhada depois, com a resposta do contador (C219)? | **Sim, depois** |
| **Q190-6** | Você pode enviar a **IN RFB 2.295/2025** (Confia) e a Portaria RFB 658/2026, para fechar a Q187-3? | **Enviar** quando puder |

# 9. Perguntas para o contador

Entram no **documento 188**, na Parte 6, e não aqui (D-N501): **C219**, sobre a lista da Lei 10.485 (conferência com decretos e Tipi atual, vigência de cada uso até a reforma, relação com a tabela 4.3.10 da EFD-Contribuições e como ver a retenção do art. 3º, § 3º); **C220**, sobre os motivos de suspensão do CNPJ (como a Receita informa o motivo, se vem mais de um e o que vale antes de 10/07/2026).

# 10. Limites do que eu li

- O **Anexo I da IN 2.333** e o **Anexo Único da IN 2.324** vieram do DOU; a **Lei 10.485** é a cópia compilada do Planalto, **não** o DOU, e traz só as alterações que o Planalto registra. Por regra da Fase 0, toda carga sai `provisório` até o contador conferir.
- Não transcrevi o **Anexo II da IN 2.333**: o PDF extrai a tabela em colunas misturadas, e uma transcrição minha poderia trocar a base legal de uma natureza por outra. Li o que ele é e a estrutura.
- Contei os 51 códigos do Anexo I a partir das duas colunas do PDF; a ordem original não é crescente e eu ordenei. Conferi a contagem por página (18 na página 3 e 33 na página 4).
- **Não conferi** se os códigos do anexo existem na Tipi e na NCM atuais, nem decretos que tenham alterado a relação depois de 2006 (art. 3º, § 1º).
- **Não li** a IN 2.295/2025, a Portaria RFB 658/2026 nem o resto do DOU além das duas portarias da mesma página.
- O desenho é proposta minha; nenhuma recomendação foi confirmada pelo contador.
