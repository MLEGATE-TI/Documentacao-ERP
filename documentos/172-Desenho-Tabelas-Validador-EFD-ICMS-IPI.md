# Desenho das tabelas estaduais e nacionais do validador da EFD-ICMS/IPI — Documento 172

*Resposta ao seu envio de 04/11/2026: as tabelas do validador da EFD-ICMS/IPI, enviadas em 13 lotes, mais a sua confirmação de que **RR não tem tabela no validador**. Este documento fecha o item P43-04 do documento 43 (códigos de ajuste e demais tabelas por UF), parte do P43-05 (para que servem a tb14 e a tb13957) e a Q167-5 no que toca à tabela 5.7, para as UFs que a trazem. Valem as suas respostas de 04/11/2026 às quatro perguntas de desenho (Q172-1 a Q172-4, seção 10.1). **Nada entra no dicionário agora; tudo vai no próximo "consolidar".***

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

Li **as 197 tabelas distintas** (recebi 204 arquivos: seis do RN vieram de novo, idênticos, e um do AM veio duplicado). São 160 arquivos em 26 UFs (**RR não tem**) e 37 de uso nacional: GENERICA (4), GLOBAL (14), CARDOC (3), CLASCONS (5), IPI (5) e ST (6). Medi tudo por script antes de desenhar: **42.679 linhas lidas em todas as versões, 35.421 nas versões mais novas e 31.212 chaves "UF + código" distintas.** Não achei nenhuma sobreposição de vigência nem fim anterior ao início em nenhum arquivo.

O desenho acrescenta **4 entidades novas (46 campos)**, altera **6 existentes** (8 campos novos, 3 campos que mudam de regra e 4 que mudam de destino) e abre **4 domínios novos** em `Cad_Classe_Sistema`. Nenhuma tabela nacional é carregada duas vezes: as de GLOBAL são das mesmas famílias do documento 43 (CFOP versão 14 e municípios versão 20 coincidem com as que ele já trata; o CEST traz as mesmas 1.038 linhas vigentes) e entram só na **conferência**.

**Sete achados que você precisa ler.**

1. **A versão mais nova do arquivo sempre contém a mais antiga.** Há 14 pares de versões (CE, ES, GO ×2, MT, PI, PR, RJ, RS ×3, SC ×3). Comparei linha a linha: nenhuma chave some; a versão nova só **fecha datas de fim** de linhas que estavam abertas ou **acrescenta códigos**. Por isso a regra de carga é simples: a mais nova substitui, e o fim de uma linha pode mudar.
2. **O código do ajuste da apuração decodifica sem exceção.** Nas 10.626 linhas de UF, o 3º caractere é a apuração (0 própria, 1 ST, 2 Difal, 3 FCP) e o 4º é o tipo de ajuste (0 a 5 e 9). Isso preenche `Tipo_Apuracao` e `Natureza` da `Cad_Icms_Codigo_Ajuste` **sem escrever nada à mão**. O que o arquivo **não diz** é se o código é da 5.1.1 (E111) ou da 5.3 (C197): `Tabela_Origem` fica vazia até o contador classificar (sua resposta à Q172-3).
3. **O código de receita não traz a obrigação nacional.** Dos 1.935 códigos de receita, só **703 (36%)** têm um único termo reconhecível no texto (ICMS-ST, Difal, multa, juros, parcelamento etc.); **1.041 (54%) não têm nenhum** (por exemplo "ICMS Normal", "OP. INTERNA/MADEIRA EM TORA") e 191 têm mais de um. A lista de cada UF também mistura o que não é ICMS da apuração (IPVA, ITCD, IRRF, taxas, receitas patrimoniais). Por isso a classificação em obrigação e em natureza **não vem do arquivo**; o desenho dá o campo e deixa a classificação para a pessoa (seção 6).
4. **A "informação adicional" (5.2) de ES e DF é, na prática, o catálogo de benefícios fiscais**: "Isenção do ICMS — Art. 5º do RICMS/ES…", com o código no formato UF + 6 dígitos (o mesmo do cBenef). Mas **AL tem 2.304 códigos que são parcelas** ("Prodesin, parcela: 25 de 01"), e RJ, RS, SC e PR usam o campo para outras coisas. Não dá para tratar tudo como cBenef; as duas listas ficam separadas, com ligação opcional (sua resposta à Q172-1).
5. **1.256 linhas têm vigência de um dia** (início igual ao fim) em todas as versões lidas (**1.065** só nas mais novas). O MT concentra 793 (**723 entraram de uma vez na versão 115, todas de 01/01/2025**), o GO tem 106, o RJ 88 e o RS 77. No RS, linhas abertas em 01/01/2025 na versão 93 aparecem fechadas no mesmo dia na 105, o que parece cancelamento. Não corrijo nada: carrego como veio, com aviso (Q172-2).
6. **O mesmo código muda de significado ao longo do tempo**: 3.066 códigos em 89 tabelas têm mais de um texto (1.038 deles são o CEST, cujo texto é só um aviso). Por isso a chave é **código + início da vigência**, nunca o código sozinho.
7. **Há linhas de teste da própria fonte**: RO tem `TESTE_ED` e `TESTE_EC` (benefícios) e o RS tem cinco linhas "exclusivo para teste da Receita Estadual — não usar" (fevereiro a abril de 2024). São 7 linhas; proponho não carregá-las (Q172-5).

# 2. Regras que segui

Valem as dos documentos 156, 157, 150, 170 e 171 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória; "O ERP só registra"; avisa e nunca bloqueia; D-N68). Mais estas:

1. **A chave de cada linha é a tabela, a UF, o código e o início da vigência.** A UF vem do arquivo (o nome diz), nunca do prefixo do código.
2. **A versão mais nova do arquivo substitui a anterior** (achado 1). As versões lidas ficam em `Mov_Carga_Tabela_Oficial`, como no documento 43.
3. **Só decodifico o que o arquivo dá sem dúvida**: apuração e natureza do código do ajuste (achado 2) e a letra C ou D do ajuste de IPI. Base legal, percentual, remissão entre códigos e vencimento ficam no texto, **sem extração por script** (Q172-3).
4. **Toda linha carregada sai `provisorio`** com `ID_Instancia_Aprovacao` vazio, até o contador validar a tabela da UF (área `validacao_dado_legal`, como nos documentos 170 e 171).
5. **Cada aviso da carga vai por extenso em `Alerta_Carga`** (vigência de um dia, texto truncado, aspas ou tabulação no texto) **e no relatório de conferência**. O aviso nunca bloqueia.
6. **O texto vai exatamente como veio**: 838 linhas têm espaço sobrando e 20 de ES têm aspas ou tabulação; o ERP preserva e avisa, não "limpa".
7. **UF sem tabela própria: o ERP avisa e pede o código** (Q172-4). A GENERICA entra como tabela nacional, com `ID_Estado` vazio, e **só vale para todas as UFs nos códigos que o Guia define assim** (por exemplo `UF099999`).
8. **Nada nacional entra duas vezes.** Onde a tabela do validador é a mesma de um arquivo do documento 43, a carga **confere** (versão, linhas vigentes) e lista a diferença.

# 3. O que li

| Grupo | Arquivos | O que é |
|---|---|---|
| 26 UFs (sem RR) | 160 | Ajustes da apuração (5.1.1), ajustes de benefício (5.1.2), informação adicional (5.2), códigos de receita (5.4), tipos de utilização de crédito, itens do IPM, produtos de usina, motivos de restituição do ST e listas de uma UF só (PE, SC, DF) |
| GENERICA | 4 | Modelos nacionais com o prefixo literal `UF` (ajustes, receita, utilização de crédito, usina) |
| GLOBAL | 14 | ANP, CFOP, CEST, municípios, países (duas numerações), UF, tipos de conhecimento e de CT-e, versões de leiaute e outras |
| CARDOC, CLASCONS, IPI, ST | 19 | Modelo e situação do documento, classes de consumo, tabelas de IPI e situação tributária |

**Formato.** Cada arquivo tem uma linha de cabeçalho ("versão=N COD…, DESC…, DT_INI, DT_FIM") e linhas separadas por barra vertical, com datas em DDMMAAAA e fim vazio quando a linha está aberta. **22 arquivos trazem só "versão=N" no cabeçalho, sem os nomes das colunas** (21 com dados e o ENQ_LEGAL_IPI, que está vazio). A codificação é Windows-1252, com **uma exceção**: o terceiro bloco do arquivo de receitas de SP está em UTF-8, então a leitura decide **linha a linha** (UTF-8 primeiro, Windows-1252 se falhar).

**Pares de versões (14).** Em todos a mais nova é superconjunto da mais antiga (achado 1). Exemplos: MT AJ_APUR_DED 109 → 115 (+732 linhas, 5 fins fechados), RS BENEF 92 → 94 (+15, 12 fins fechados), SC INF_ADIC 15 → 21 (+16, 4 fins fechados).

| Tipo de tabela | Arquivos | Linhas (versão mais nova) | Chaves "UF + código" | Linhas de um dia |
|---|---|---|---|---|
| Ajuste da apuração (AJ_APUR_DED) | 33 | 10.657 | 9.081 | 861 |
| Informação adicional (INF_ADIC_APUR) | 25 | 6.831 | 6.177 | 88 |
| Ajuste de benefício (AJ_BENEF_INCENTIVO) | 23 | 3.383 | 3.042 | 68 |
| Código de receita (REC_REF_OBRIGACAO) | 27 | 2.162 | 1.935 | 25 |
| Item do IPM (COD_ITEM_IPM e _ST) | 17 | 568 | 533 | 1 |
| Tipo de utilização de crédito (TP_UTIL_CRED_FISCAIS) | 18 | 257 | 215 | 14 |
| Item da informação de PE (COD_INF_ITEM) | 1 | 196 | 196 | 0 |
| Motivo de restituição do ST (COD_MOT_REST_COMPL_ST) | 7 | 117 | 111 | 0 |
| Subapuração de PE (IND_SUBAP) | 1 | 49 | 49 | 0 |
| Produto de usina (COD_PROD_USINAS) | 6 | 39 | 34 | 0 |
| ISS do DF (4 tabelas) | 4 | 273 | 272 | 0 |
| IPI (5 tabelas) | 5 | 104 | 104 | 0 |
| GLOBAL (14), CARDOC (3), CLASCONS (5), ST (6), mensagens do SC (1) e obrigações a recolher da PB (1) | 30 | 10.785 | 9.463 | 8 |

*(Cada tabela, uma por uma, está no Anexo A. O total de arquivos é 197.)*

# 4. O que o dicionário já tem e o que falta

| Entidade existente | O que ela cobre | O que falta |
|---|---|---|
| `Cad_Icms_Codigo_Ajuste` (documento 10, com os ajustes do documento 43) | Código, descrição, apuração, natureza, tabela de origem, subapuração, sugestão de indicador de benefício (documento 168) | Carga dos 10.657 códigos (31 da GENERICA entre eles) e dos 13 de IPI; `Tabela_Origem` obrigatória, mas o arquivo não a traz; situação do dado |
| `Cad_Icms_Obrigacao_Recolher` | Obrigação nacional (tb19) mais código de receita por UF | A identidade é a obrigação nacional, que **o arquivo de receitas não traz**; falta a UF vazia (genérica) e a natureza |
| `Mov_Apuracao_Informacao_Adicional` | COD_INF_ADIC como referência a um domínio de `Cad_Classe_Sistema` | O domínio não tem UF nem vigência por UF e não comporta 9.000 códigos |
| `Cad_Beneficio_Fiscal_Icms` (cBenef) | Código de benefício por UF com vigência | Não é a lista da 5.2 nem a da 5.1.2 (achado 4) |
| `Mov_Icms_St_Complemento_*` (três entidades) | COD_MOT_REST_COMPL como domínio sem carga (Q167-5) | As 7 UFs que publicam a tabela 5.7 |
| `Cad_Pais`, `Cad_Municipio`, `Cad_CFOP`, `Cad_Cest`, `Cad_Produto_Anp`, `Cad_Estado` | Já recebem as tabelas do documento 43 | Conferência de versão |
| `Cad_Tabela_Oficial` e `Mov_Carga_Tabela_Oficial` | Cadastro de tabelas e controle de cada carga | Nenhuma mudança: as 197 entram como linhas |
| IPM (registro 1400), controle de créditos (1200), produtos de usina | **Nada** (nenhum campo cita IPM ou utilização de crédito) | O registro não está desenhado; a tabela entra como catálogo, sem uso até o desenho do registro (seção 7) |

# 5. Ajustes e informações adicionais

## 5.1 `Cad_Icms_Codigo_Ajuste`: o que muda

A entidade já existe e já aceita `ID_Estado` vazio (códigos genéricos). A carga de **AJ_APUR_DED** (33 arquivos, 26 UFs e a GENERICA) usa os campos que ela tem e acrescenta o que falta:

| Campo | Mudança | Regra |
|---|---|---|
| `Tipo_Apuracao` | carga | 3º caractere do código nas linhas de UF: 0 `icms_proprio`, 1 `icms_st`, 2 `difal`, 3 `fcp`. Nas linhas de IPI (13 códigos, sem UF) é `ipi`. |
| `Natureza` | carga | 4º caractere: 0 `debito`, 1 `estorno_credito`, 2 `credito`, 3 `estorno_debito`, 4 `deducao`, 5 `debito_especial`, 9 `controle_extra_apuracao`. Nos códigos de IPI vem da letra C (crédito) ou D (débito) que o próprio texto traz. |
| `Tabela_Origem` | **passa a opcional** | Fica vazia na carga: o arquivo não distingue 5.1.1 de 5.3 (Q172-3). O contador classifica, e o ERP avisa quando um ajuste de documento (C197) usa código sem classificação. |
| `Situacao_Dado` | **novo** | `provisorio` na carga; `validado` quando o contador aprova a tabela da UF. |
| `ID_Instancia_Aprovacao` | **novo**, opcional | A validação do contador (área `validacao_dado_legal`). |
| `Alerta_Carga` | **novo**, texto opcional | O aviso da carga, por extenso (vigência de um dia, texto truncado, aspas ou tabulação). |

**O que a leitura mostrou nos textos (fica no texto, sem extração).** Há base legal ("Art. 5º do RICMS/00"), percentuais, remissão entre códigos (ES013000 ↔ ES023000), códigos de receita (DF), regras ("obrigatório informar descrição complementar", só em ES, 25 códigos) e remissões a registros ("Registro 1200", 150 códigos, sobretudo RS, GO e AP). Nada disso vira campo (Q172-3).

**Conferência com o documento 10.** O campo `Indicador_Subapuracao` diz "quarto caractere do código (3 a 8)". **Nas 10.626 linhas de UF o 4º caractere vai de 0 a 5 e 9** e é o tipo do ajuste; o documento 10 e a tabela não batem. Não mexo no campo e levo ao contador (C2).

## 5.2 `Cad_Icms_Beneficio_Ajuste_Codigo` (nova): ajuste de benefício (5.1.2)

Catálogo da AJ_BENEF_INCENTIVO: 23 arquivos, **3.383 linhas** e 3.042 chaves, **todas no formato UF + 8 dígitos**. Os textos dos códigos de SP citam o artigo do RICMS; o DF repete as hipóteses da 5.1.1 com outros códigos. **O vínculo entre o código de benefício e o ajuste da 5.1.1 não está no arquivo e não se deduz do código**; fica em campo opcional, preenchido por pessoa.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_Beneficio_Ajuste_Codigo` | identificador | --- |
| `ID_Icms_Beneficio_Ajuste_Codigo_Versao` | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| `ID_Estado` | referência (Cad_Estado) --- identidade | A UF do arquivo. |
| `Codigo` | código (10) --- identidade | O código como a UF o publica. Mais o início da vigência, a chave de cada versão. |
| `Descricao` | texto | Como veio, sem limpeza. |
| `ID_Icms_Codigo_Ajuste` | referência (Cad_Icms_Codigo_Ajuste), opcional | O ajuste da 5.1.1 a que o benefício se liga. **Só preenchido por pessoa.** |
| `Situacao_Dado` | enumeração {provisorio, validado} | `provisorio` na carga. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Alerta_Carga` | texto, opcional | O aviso da carga. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale (DT_INI). |
| `Vigencia_Fim` | data | Último dia (inclusive); 31/12/9999 quando o DT_FIM vem vazio. |
| `Motivo_Vigencia` | texto, opcional | Por exemplo "fim fechado pela versão 94 do arquivo". |

## 5.3 `Cad_Icms_Informacao_Adicional_Codigo` (nova): informação adicional (5.2)

Catálogo da INF_ADIC_APUR: 25 arquivos, **6.831 linhas** e 6.177 chaves, todas em UF + 6 dígitos. É o que o E115 (e o 1925) chama de COD_INF_ADIC. **Três comportamentos diferentes**: em ES e DF é o catálogo de benefícios fiscais (ES999999, DF890000 e DF890001 são "outros"); no AL são 2.304 códigos de parcela ("Prodesin, parcela: 01 de 02"); nas demais UFs mistura valores de controle e benefícios. A entidade guarda **só o código e o texto**, com ligação opcional ao cBenef.

Os campos são os da `Cad_Icms_Beneficio_Ajuste_Codigo`, trocando o último campo de ligação:

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_Informacao_Adicional_Codigo` | identificador | --- |
| `ID_Icms_Informacao_Adicional_Codigo_Versao` | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| `ID_Estado` | referência (Cad_Estado) --- identidade | A UF do arquivo. |
| `Codigo` | código (8) --- identidade | O código como a UF o publica; com o início da vigência, a chave. |
| `Descricao` | texto | Como veio. |
| `ID_Beneficio_Fiscal_Icms` | referência (Cad_Beneficio_Fiscal_Icms), opcional | O cBenef correspondente, **só quando uma pessoa liga**. Nenhuma ligação por igualdade de código. |
| `Situacao_Dado` | enumeração {provisorio, validado} | `provisorio` na carga. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Alerta_Carga` | texto, opcional | O aviso da carga. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia (inclusive); 31/12/9999 quando em aberto. |
| `Motivo_Vigencia` | texto, opcional | Por que a versão foi criada. |

**Alteração em `Mov_Apuracao_Informacao_Adicional`:** `ID_Codigo_Informacao_Adicional` deixa de apontar para o domínio de `Cad_Classe_Sistema` e passa a apontar para esta entidade. O domínio `codigo_informacao_adicional_apuracao_icms` sai da lista.

# 6. Códigos de receita (5.4): `Cad_Icms_Obrigacao_Recolher`

27 arquivos (26 UFs mais a GENERICA), **2.162 linhas** e 1.935 chaves. O formato do código varia por UF: SP e ES "NNN-N", TO e MS e GO 3 dígitos, a maioria 4 dígitos, AL 5 ou 6, PI e CE 6, **SC 9 dígitos**, GENERICA 6. **No SC o vencimento vem escrito no texto** (por exemplo "venc. dia 10"); fica no texto, e o contador diz se vira parâmetro (C6).

**A entidade existente tem a obrigação nacional (tb19, nove valores) na identidade; o arquivo de receitas não a traz** (achado 3). Mudanças:

| Campo | Mudança | Regra |
|---|---|---|
| `ID_Estado` | **passa a opcional** | Vazio nos 16 códigos da GENERICA (códigos nacionais de 6 dígitos, como "100013 ICMS Comunicação"). |
| `ID_Obrigacao_Recolher` | **sai da identidade e passa a opcional** | Vazio na carga. A identidade passa a ser **UF + `Codigo_Receita` + início da vigência**. |
| `ID_Natureza_Receita` | **novo**, referência (Cad_Classe_Sistema, domínio `natureza_receita_icms_uf`), opcional | O que a receita é. Ver abaixo. |
| `Forma_Recolhimento` | **novo**, enumeração {por_apuracao, por_operacao}, opcional | Só quando o texto diz "por Apuração" ou "por Operação". |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Alerta_Carga` | **novos** | Como na seção 5.1. |

**Domínio novo `natureza_receita_icms_uf`** (19 valores): `icms_normal`, `icms_st`, `difal`, `fcp`, `antecipacao`, `importacao`, `simples_nacional`, `divida_ativa`, `parcelamento`, `autuacao_fiscal`, `autorregularizacao`, `multa`, `juros`, `taxa`, `ipva`, `itcd`, `irrf`, `receita_patrimonial` e `outra`. A lista é aberta, como todo domínio.

**Como a natureza é preenchida.** Por palavra no texto, **só nas 703 receitas com um único termo reconhecível**, e a sugestão sai `provisorio` e visível (a pessoa confirma ou troca). As outras 1.232 ficam **vazias** até alguém classificar. Não há classificação por palavra para "ICMS Normal": ela não tem palavra-chave, e o desenho não cria regra para ela (Q172-6).

**Obrigações nacionais (tb19).** `OBR_ICMS_RECOL` (GLOBAL e PB) tem 9 linhas e **é a tb19 que o documento 43 já trata**; entra só na conferência.

# 7. Listas pequenas por UF: `Cad_Efd_Codigo_Estadual` (nova)

Sete tipos de tabela têm **menos de 600 linhas** cada, são por UF e **não têm onde ficar**: o domínio de `Cad_Classe_Sistema` não tem UF. O documento 43 não criou uma entidade genérica de tabelas externas porque ela repetiria `Cad_Tabela_Oficial` e `Cad_Classe_Sistema`; **aqui o caso é outro**: o que falta é a UF, e uma entidade só para todas as listas pequenas por UF evita sete entidades quase iguais.

| Tabela | Arquivos | Linhas | Para que serve |
|---|---|---|---|
| TP_UTIL_CRED_FISCAIS | 18 | 257 | Tipo de utilização do crédito fiscal (registro 1200), do modelo nacional UF01 Dedução, UF21 Compensação, UF41 Transferência, UF61 Restituição, UF81 Estorno e UF99 Outros, mais os tipos de cada UF (BA 18, MG 27, RJ 58, RS 34). É a **tb14** do P43-05 (o nome "ajustes" enganava). |
| COD_ITEM_IPM e COD_ITEM_IPM_ST | 17 | 568 | Itens do índice de participação dos municípios (registro 1400). Os códigos vão de "1001" (AL) a nomes de 40 caracteres (MG) e até "AAA 9.9" com espaço (RN). |
| COD_PROD_USINAS | 6 | 39 | Produtos de usina (álcool hidratado, anidro, açúcar etc.), com vigência por UF. É a **tb13957** do P43-05. |
| COD_MOT_REST_COMPL_ST | 7 | 117 | Motivo da restituição ou complementação do ICMS-ST (tabela 5.7): MG, MS, PA, RJ, RO, RS e SE. |
| COD_INF_ITEM | 1 | 196 | Informação do item de PE. |
| IND_SUBAP | 1 | 49 | Subapuração de PE ("sub-apuração 02 (Uso exclusivo Central de Distribuição)"). |

As tabelas de ISS do DF não entram aqui: têm tratamento próprio (seção 8).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_Codigo_Estadual` | identificador | --- |
| `ID_Efd_Codigo_Estadual_Versao` | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| `ID_Tabela_Oficial` | referência (Cad_Tabela_Oficial) --- identidade | Qual das sete tabelas (`tp_util_cred_fiscais`, `cod_item_ipm`, `cod_prod_usinas`, `cod_mot_rest_compl_st`, `cod_inf_item`, `ind_subap`). |
| `ID_Estado` | referência (Cad_Estado), opcional --- identidade | A UF; vazio na GENERICA. |
| `Codigo` | código (40) --- identidade | Como a UF publica; com o início da vigência, a chave. |
| `Descricao` | texto | Como veio. |
| `Situacao_Dado` | enumeração {provisorio, validado} | `provisorio` na carga. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Alerta_Carga` | texto, opcional | O aviso da carga. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia (inclusive); 31/12/9999 quando em aberto. |
| `Motivo_Vigencia` | texto, opcional | Por que a versão foi criada. |

**Alteração nas três entidades `Mov_Icms_St_Complemento_Devolucao_Saida`, `_Saida` e `_Saida_Entrada`:** `ID_Motivo_Restituicao_Complemento` deixa de apontar para o domínio `motivo_restituicao_complemento_icms_st` e passa a apontar para esta entidade (tabela `cod_mot_rest_compl_st`). **Isso resolve a Q167-5 só nas 7 UFs que publicam a tabela**; nas demais o ERP continua avisando. O campo `COD_MOT_REST_COMPET` do 1255 (`Mov_Icms_St_Ressarcimento_Consolidado.ID_Motivo_Ressarcimento`) **não muda** até o contador dizer se usa a mesma tabela (C5).

**IPM, controle de créditos (1200) e usinas: tabela sem registro.** Nenhum campo do dicionário cita IPM ou utilização de crédito; o desenho dos registros 1200, 1400 e das usinas é dos blocos setoriais do documento 167 e **não faz parte deste documento**. As listas entram como catálogo, `provisorio`, sem uso até esse desenho (D-N68).

# 8. ISS do DF, IPI e tabelas nacionais

## 8.1 ISS do DF (4 tabelas)

| Tabela | Linhas | Destino |
|---|---|---|
| ISS_UNIPROF | 4 | **`Cad_Iss_Df_Valor_Uniprofissional` (nova, abaixo).** O arquivo traz o valor **no campo de descrição, com vírgula decimal** ("297,04" em 2019 a "358,42" em 2022), cada ano numa linha, com código DF2019 a DF2022. Guardar como texto seria guardar número como descrição. |
| TAB_ISS_DF | 201 | Lista de serviços da LC 116 na versão do DF. **Confere com a lista do documento 41 (NFS-e Nacional)** e não vira entidade: o código 1105 entra em 21/09/2021 (201 linhas, todas vigentes), e a carga lista qualquer código que a NFS-e Nacional não tenha. |
| TAB_DOC_ISS | 8 | Tipos de documento do ISS do DF. Entra no domínio existente de documento fiscal de ISS se houver correspondência; sem ela, em `Cad_Classe_Sistema` (domínio `tipo_documento_iss_df`). |
| TAB_CONTA_ISS_DF | 60 | Contas COSIF do B350, que o documento 168 (G13) já trata em `Mov_Iss_Df_Conta_Cosif`. A carga confere a conta informada com a lista. |

**`Cad_Iss_Df_Valor_Uniprofissional` (nova, 10 campos).** Valor fixo anual do ISS por profissional, da sociedade uniprofissional do DF. Parâmetro com vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Iss_Df_Valor_Uniprofissional` | identificador | --- |
| `ID_Iss_Df_Valor_Uniprofissional_Versao` | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| `ID_Estado` | referência (Cad_Estado) --- identidade | O DF. |
| `Valor_Por_Profissional` | número | O valor do ano, **em número** (a vírgula do arquivo vira ponto na carga; os valores lidos são 297,04 em 2019, 307,05 em 2020, 323,02 em 2021 e 358,42 em 2022). |
| `Situacao_Dado` | enumeração {provisorio, validado} | `provisorio` na carga. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Alerta_Carga` | texto, opcional | O aviso da carga. |
| `Vigencia_Inicio` | data | 01/01 do ano (DT_INI). |
| `Vigencia_Fim` | data | 31/12 do ano (DT_FIM). |
| `Motivo_Vigencia` | texto, opcional | Por que a versão foi criada. |

A relação entre este valor e `Mov_Apuracao_Iss_Df.Valor_Iss_Recolher_Unico` não está no arquivo; **o ERP não calcula um a partir do outro** e a equipe diz se há interesse (E2).

## 8.2 IPI (5 tabelas, 104 linhas)

| Tabela | Linhas | Destino |
|---|---|---|
| AJ_APUR_IPI | 13 | **`Cad_Icms_Codigo_Ajuste`** com `Tipo_Apuracao = ipi` e `ID_Estado` vazio. Fecha o P43-04 no que toca aos ajustes de IPI. O texto traz "Estorno de débito; C; montante do débito…", e a letra C ou D dá a `Natureza`. |
| CL_ENQ_IPI | 31 | Domínio novo `classe_enquadramento_ipi` em `Cad_Classe_Sistema` (classes I, II, III-M…, com NCM e artigo do Decreto 4.544/2002 no texto). |
| SELO_CONT_IPI | 50 | Domínio novo `selo_controle_ipi` (relógios, bebidas etc., com a cor do selo no texto). |
| CLASS_CONTRIB_IPI | 10 | Domínio novo `classificacao_contribuinte_ipi` (00 Industrial — Transformação, 01 Beneficiamento, 02 Montagem…). |
| ENQ_LEGAL_IPI | 0 | **Vazia**: só o cabeçalho. Fica registrada em `Cad_Tabela_Oficial`; os códigos de enquadramento legal (cEnq) continuam sem fonte. |

O uso dos três domínios novos nos registros da EFD **não está no dicionário**; entram como catálogo, sem uso, até o contador dizer onde se aplicam (C7).

## 8.3 Tabelas nacionais: só conferência

| Tabela | Linhas | O que a carga faz |
|---|---|---|
| CFOP (v14) | 648 (619 vigentes) | Confere com a tb15236 do documento 43 (mesma versão e mesmo número de vigentes). |
| COD_CEST (v18) | 2.185 (1.038 vigentes) | Confere com a tb16643. **Os 1.038 textos vigentes são o aviso "Verificar, para o CEST, a descrição vigente…"**, como no documento 43; a descrição vem do Convênio ICMS 142/18. |
| MUNICIPIOS (v20) | 5.578 (5.573 vigentes, com os dois códigos não municipais) | Confere com a tb16896 (versão 20). Os códigos 9999998 (CT-e simplificado) e 9999999 (Exterior) **não são municípios** e ficam fora de `Cad_Municipio`, como no documento 43; a conferência usa os 5.571 restantes. |
| ANP (v16) | 981 (916 vigentes) | Confere com `Cad_Produto_Anp`. |
| PAISES (v10) e PAIS_SISCOMEX (v13) | 251 e 261 | **Duas numerações.** O Bacen tem 4 dígitos (132 = Afeganistão) e o Siscomex 3 (13 = Afeganistão), sem coluna comum. **Ligo as duas por nome, normalizado**; o par sai `provisorio` e o que não tem par fica sem Siscomex (Q172-8). Responde ao P43-06. |
| UF_COD_SIG e UF_SIG_NOM | 27 e 27 | Confere com `Cad_Estado` (código IBGE, sigla e nome). |
| VERSOES_LEIAUTE (v19) | 18 (1 aberta) | Confere com as versões de leiaute do documento 43 (`Cad_Obrigacao_Leiaute`). |
| GEN_ITEM_MERC_SERV | 100 | Tipo de item (00 Serviço, 01 Animais vivos…), o mesmo do documento 43. |
| TP_CONHEC_TRANS e TP_CT_E | 22 e 13 | Domínios que o documento 43 já trata. `TP_CT_E` (versão 6, 13 linhas, 6 vigentes) reabre o código 0 em 01/01/2018 com o texto "CT-e ou BP-e Normal" e fecha o 2 (anulação de débito) em 31/12/2024; o código 3 muda de texto três vezes. |
| CARDOC: MOD_DOC (41), COD_SIT (12), IND_EMIT (2) | 55 | Modelo do documento e situação do documento. Conferência com os domínios existentes. |
| CLASCONS: 5 tabelas | 210 | Classes de consumo de água, gás, comunicação e energia (faixas). O documento 43 já trata o consumo de telecomunicação (CONSUMO_TELECOM); a carga confere o que coincide, código a código, e lista a diferença (E3). Água, gás e energia não tinham arquivo antes. |
| ST: SIT_TRIB_PIS, COFINS, IPI, ICMS, ICMS_A e ICMS_B | 310 | Ver 8.4. |
| TOT_PARC_REDZ | 21 | Totalizadores parciais da redução Z (ECF), a **tb131 já tratada como legado** no documento 43. Não carrega. |
| COD_MSG_PRE_VALIDACAO (SC) | 60 | Mensagens do pré-validador do SC ("Arquivo enviado é nulo ou está vazio."). Sem função no ERP, como a MENSAGENS_USUARIO do documento 43. Fica registrada em `Cad_Tabela_Oficial` e não carrega. |

## 8.4 Situação tributária (ST)

O **composto de ICMS** (SIT_TRIB_ICMS, 200 linhas, 140 códigos) junta a origem da mercadoria (0 a 8) e a tributação (CST ou CSOSN) em três dígitos. **O dicionário já separa os dois** (`Cad_Cst.Codigo` com 2 dígitos ou os 3 do CSOSN; origem em domínio próprio; D-N78 do documento 43); por isso **nada do composto é carregado** e ele serve para conferir. Três achados:

- **O 102 e o 202 passam a valer como CSOSN e como composto** (origem 1 + CST 02 e origem 2 + CST 02, monofásico de combustíveis) a partir de 01/04/2023; o 300, o 400 e o 500 mudam de significado em 01/01/2013 (de Simples para origem + CST 00). Como o composto não é carregado, não há colisão na chave `(ID_Imposto, Codigo)` de `Cad_Cst` (D-N78 e P43-12 do documento 43).
- **Os textos de origem 4 (processo produtivo básico) trazem um sufixo de ano da lei que sobe de linha em linha** (erro da fonte); a carga não usa esse texto.
- **A tabela A (origem, versão 2) vai de 0 a 7: não tem a origem 8 e mantém o texto antigo da origem 3 ("superior a 40%", sem o limite de 70%); a tabela B (tributação, versão 1.0) não tem os CST 02, 15, 53 e 61.** O composto tem a origem 8 (800 a 890) e esses quatro CST (002, 015, 053 e 061); é mais completo que as duas. A carga confere o `Cad_Cst` e o domínio de origem contra o composto e lista as lacunas.

SIT_TRIB_PIS e SIT_TRIB_COFINS **têm os mesmos códigos e vigências** (37 linhas, 33 vigentes cada) e diferem só na grafia de alguns textos (hífen, maiúscula, "Não-Tributada"); SIT_TRIB_IPI tem 14 códigos. Todos conferem com `Cad_Cst` do documento 43.

# 9. O que entra no próximo "consolidar"

**4 entidades novas (46 campos).**

| Entidade | Tipo | Campos | Vigência | Módulo | Capítulo |
|---|---|---|---|---|---|
| `Cad_Icms_Beneficio_Ajuste_Codigo` | parâmetro por UF (carga provisória) | 12 | sim | Contabilidade & Fiscal | 5 |
| `Cad_Icms_Informacao_Adicional_Codigo` | parâmetro por UF (carga provisória) | 12 | sim | Contabilidade & Fiscal | 5 |
| `Cad_Efd_Codigo_Estadual` | parâmetro por UF (carga provisória) | 12 | sim | Contabilidade & Fiscal | 5 |
| `Cad_Iss_Df_Valor_Uniprofissional` | parâmetro do DF (carga provisória) | 10 | sim | Contabilidade & Fiscal | 5 |

**6 entidades alteradas.**

| Entidade | O que muda |
|---|---|
| `Cad_Icms_Codigo_Ajuste` | `Situacao_Dado`, `ID_Instancia_Aprovacao` e `Alerta_Carga` novos; `Tabela_Origem` passa a opcional |
| `Cad_Icms_Obrigacao_Recolher` | `ID_Estado` opcional; `ID_Obrigacao_Recolher` sai da identidade e passa a opcional (identidade: UF + `Codigo_Receita`); `ID_Natureza_Receita`, `Forma_Recolhimento`, `Situacao_Dado`, `ID_Instancia_Aprovacao` e `Alerta_Carga` novos |
| `Mov_Apuracao_Informacao_Adicional` | `ID_Codigo_Informacao_Adicional` passa a apontar para `Cad_Icms_Informacao_Adicional_Codigo` |
| `Mov_Icms_St_Complemento_Devolucao_Saida`, `Mov_Icms_St_Complemento_Saida` e `Mov_Icms_St_Complemento_Saida_Entrada` | `ID_Motivo_Restituicao_Complemento` passa a apontar para `Cad_Efd_Codigo_Estadual` |

**4 domínios novos em `Cad_Classe_Sistema`** (abertos): `natureza_receita_icms_uf` (19 valores), `classe_enquadramento_ipi` (31), `selo_controle_ipi` (50) e `classificacao_contribuinte_ipi` (10). O domínio `codigo_informacao_adicional_apuracao_icms` sai da lista.

**Cargas provisórias (todas `Situacao_Dado = provisorio`, com fonte "validador da EFD-ICMS/IPI, versão N do arquivo"):**

| Carga | Linhas (versão mais nova) |
|---|---|
| Ajustes da apuração (UF e GENERICA) e de IPI | 10.670 |
| Ajustes de benefício | 3.383 menos as 5 de teste do RS e as 2 de RO que ficam fora (Q172-5): **3.376** |
| Informação adicional | 6.831 |
| Códigos de receita (UF e GENERICA) | 2.162 |
| Listas pequenas por UF (seção 7) | 1.226 |
| ISS do DF (valor por profissional) | 4 |
| Domínios de IPI | 91 |

**Regra D-N68 aplicada.** Nenhuma entidade deste documento é de regime com cliente: são tabelas que o ERP lê para gerar a EFD, e entram todas. A única exceção são os **registros 1200, 1400 e de usina**, que não estão desenhados (seção 7).

**A carga é feita uma vez por versão do arquivo.** Cada versão nova do validador (o PVA publica atualizações) é uma nova carga em `Mov_Carga_Tabela_Oficial` e aplica a regra 2 da seção 2.

# 10. Perguntas

## 10.1 Respondidas por você em 04/11/2026 (viram decisão no consolidar)

| Nº | Pergunta | Sua resposta | Como apliquei |
|---|---|---|---|
| Q172-1 | Informação adicional (5.2) e benefício (cBenef): uma lista ou duas? | **Duas entidades novas por UF**, ligadas por campo opcional | `Cad_Icms_Beneficio_Ajuste_Codigo` (seção 5.2) e `Cad_Icms_Informacao_Adicional_Codigo` (seção 5.3), com `ID_Beneficio_Fiscal_Icms` opcional (seção 5) |
| Q172-2 | Linhas com vigência de um dia (1.065 nas versões mais novas) | **Carregar como veio, com aviso** | Achado 5; o aviso vai em `Alerta_Carga` e no relatório de conferência |
| Q172-3 | O que decodificar por script | **Só a apuração e a natureza** | Regra 3 da seção 2: base legal, percentual, remissão e vencimento ficam no texto |
| Q172-4 | UF sem tabela no validador (RR) | **Avisar e pedir o código** | Regra 7 da seção 2 |

## 10.2 Para você confirmar (recomendação em cada uma)

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q172-5 | As **7 linhas de teste da própria fonte** (RO `TESTE_ED` e `TESTE_EC`; RS011522, RS021900, RS23002106, RS25002106 e RS53002113, vigentes de 01/02 a 30/04/2024) entram? | **Não carregar.** Ficam no registro da carga (`Mov_Carga_Tabela_Oficial`) com o motivo "linha de teste da fonte", visíveis no relatório, para a decisão ser auditável. |
| Q172-6 | A natureza do código de receita (19 valores do domínio `natureza_receita_icms_uf`) é sugerida por palavra no texto? | **Sim, só nas 703 receitas com um único termo reconhecível**, como `provisorio`. As outras 1.232 ficam vazias até alguém classificar. Não há classificação em lote por palavra para o resto. |
| Q172-7 | Abro os três domínios de IPI (classe de enquadramento, selo de controle e classificação do contribuinte) como catálogo, sem uso por enquanto? E as tabelas nacionais (GLOBAL, CARDOC, CLASCONS, ST) só conferem? | **Sim às duas.** O uso dos domínios nos registros da EFD espera o contador (C7); as nacionais não entram duas vezes. |
| Q172-8 | Países: ligar o Bacen (4 dígitos) ao Siscomex (3) **por nome normalizado**, `provisorio`? | **Sim.** O que não tem par fica sem o código Siscomex e entra no relatório; a ligação por código precisa de uma fonte que traga os dois na mesma linha (P43-06 continua aberta nesse ponto). |
| Q172-9 | `Cad_Efd_Codigo_Estadual` (12 campos) guarda as sete listas pequenas por UF, e as três entidades de complemento do ST passam a apontar para ela? | **Sim.** Evita sete entidades quase iguais; o tipo da lista é o campo `ID_Tabela_Oficial`, que entra na identidade. O `COD_MOT_REST_COMPET` do registro 1255 não muda até o contador responder C5. |
| Q172-10 | `Cad_Iss_Df_Valor_Uniprofissional` (nova, 10 campos) para o valor anual por profissional do DF, e o domínio `tipo_documento_iss_df`? | **Sim.** O valor entra como número (a vírgula do arquivo vira ponto) e o ERP não o usa em cálculo (E2). |

## 10.3 Para o contador

| Nº | Pergunta | Por que importa |
|---|---|---|
| C1 | Qual ajuste da apuração é da 5.1.1 (E111) e qual é da 5.3 (C197)? Existe regra pelo 4º caractere ou só por tabela do Guia? | `Tabela_Origem` fica vazia até lá; sem ela o ERP só avisa quando um ajuste de documento usa código não classificado. |
| C2 | O documento 10 diz que `Indicador_Subapuracao` é "o 4º caractere, de 3 a 8"; nas 10.626 linhas de UF o 4º caractere vai de 0 a 5 e 9 e é o tipo do ajuste. Qual vale? | Não mexi no campo; os dois não batem. |
| C3 | Onde se informa o código da tabela 5.1.2 (ajuste de benefício), e o validador traz alguma regra de uso? | O arquivo só traz o catálogo. |
| C4 | As 793 linhas de um dia do MT (723 de 01/01/2025 acrescentadas de uma vez na versão 115) são legítimas ou erro da SEFAZ? E as 77 do RS fechadas no mesmo dia em que estavam abertas na versão 93? | Carregam como vieram, com aviso; a resposta decide se o aviso some. |
| C5 | O `COD_MOT_REST_COMPET` do registro 1255 usa a mesma tabela 5.7 dos sete estados que trazem `COD_MOT_REST_COMPL_ST`? | Decide se o 1255 também aponta para `Cad_Efd_Codigo_Estadual`. |
| C6 | No SC o vencimento vem escrito no texto do código de receita ("venc. dia …"). Posso ler esse dia, ou fica só no texto? | Hoje fica só no texto (Q172-3). |
| C7 | Onde se aplicam a classe de enquadramento, o selo de controle e a classificação do contribuinte de IPI na EFD? | Os três domínios ficam como catálogo, sem uso. |
| C8 | As remissões entre códigos (por exemplo ES013000 ↔ ES023000) devem virar ligação entre registros? | Hoje ficam no texto. |
| C9 | Em AL, os 2.304 códigos de "Prodesin, parcela n de m" são um código por parcela. Esse volume é esperado? | Entram como vieram; o volume infla `Cad_Icms_Informacao_Adicional_Codigo`. |

## 10.4 Para a equipe

| Nº | Pergunta | Por que importa |
|---|---|---|
| E1 | Há um arquivo de cBenef (por exemplo o da NF-e) para comparar com os códigos de ES e DF da informação adicional? | Confirma a ligação opcional da Q172-1 e dá a conferência. |
| E2 | Há interesse em relacionar o valor por profissional do DF ao ISS fixo do DF? | Sem interesse, o valor só é guardado. |
| E3 | Conferir os códigos de energia, água e gás (CLASCONS) com a fonte do documento 43: quem confere a diferença? | A carga só lista. |
| E4 | Em que UFs a Mlegate tem clientes? (repete a Q171-E2) | Pela D-N68, o que é só de um regime entra quando há cliente; aqui a lista decide quais tabelas de UF o contador valida primeiro. |
| E5 | Como o validador novo chega à equipe (download manual do PVA, pacote do portal)? | Define a rotina de recarga e o aviso de "tabela mais nova disponível". |

# 11. Limites

- **Li o conteúdo dos 197 arquivos, mas não o Guia Prático da EFD-ICMS/IPI.** O número das tabelas do Guia (5.1.1, 5.1.2, 5.2, 5.3, 5.4, 5.7) vem do que o documento 43 e o documento 10 já trazem; a ligação de cada arquivo do validador a uma tabela do Guia é **minha leitura**, confirmada só pelo contador (C1 a C3).
- **A classificação do código de receita em natureza e obrigação vem de palavras no texto** e só vale para 703 de 1.935 códigos (achado 3). O restante exige uma pessoa.
- **Não desenhei** os registros 1200 (controle de crédito de ICMS) e os de usina; as listas de IPM, de utilização de crédito e de usina entram como catálogo, sem o registro que as usa (seção 7).
- **22 arquivos não trazem os nomes das colunas** (21 com dados, mais o vazio ENQ_LEGAL_IPI). Os de dados foram lidos pela posição (código, texto, início, fim), que é a das tabelas que trazem o nome; não há como confirmar pela fonte.
- **O validador muda** (os arquivos trazem versão); o que li é a versão de 04/11/2026. Cada recarga é uma nova carga, com a regra 2 da seção 2.
- **Não consultei nenhuma SEFAZ**: o significado dos códigos é o texto do arquivo.

# Anexo A. As 49 tabelas do validador, uma por uma

Cada linha é um **tipo de tabela**; os 197 arquivos estão agrupados por tipo. "Linhas" é a soma das versões mais novas de cada UF; "vigentes" são as linhas sem fim.

| Tabela | Arquivos | UFs | Linhas (mais nova) | Vigentes | Destino |
|---|---|---|---|---|---|
| `AJ_APUR_DED` | 33 | 26 UF + GENERICA | 10.657 | 6.333 | Cad_Icms_Codigo_Ajuste (carga provisória) |
| `INF_ADIC_APUR` | 25 | 19 UF | 6.831 | 3.020 | Cad_Icms_Informacao_Adicional_Codigo (nova) |
| `MUNICIPIOS` | 1 | GLOBAL | 5.578 | 5.573 | Conferência (tb16896, documento 43) |
| `AJ_BENEF_INCENTIVO` | 23 | 21 UF | 3.383 | 1.629 | Cad_Icms_Beneficio_Ajuste_Codigo (nova) |
| `COD_CEST` | 1 | GLOBAL | 2.185 | 1.038 | Conferência (tb16643, documento 43) |
| `REC_REF_OBRIGACAO` | 27 | 26 UF + GENERICA | 2.162 | 1.467 | Cad_Icms_Obrigacao_Recolher (alterada) |
| `ANP` | 1 | GLOBAL | 981 | 916 | Conferência (Cad_Produto_Anp) |
| `CFOP` | 1 | GLOBAL | 648 | 619 | Conferência (tb15236, documento 43) |
| `COD_ITEM_IPM` | 16 | 16 UF | 567 | 475 | Cad_Efd_Codigo_Estadual (nova) |
| `PAIS_SISCOMEX` | 1 | GLOBAL | 261 | 258 | Cad_Pais: ligação por nome (provisória) |
| `TP_UTIL_CRED_FISCAIS` | 18 | 17 UF + GENERICA | 257 | 190 | Cad_Efd_Codigo_Estadual (nova) |
| `PAISES` | 1 | GLOBAL | 251 | 249 | Cad_Pais: ligação por nome (provisória) |
| `TAB_ISS_DF` | 1 | 1 UF | 201 | 201 | Conferência com a lista da NFS-e Nacional (documento 41) |
| `SIT_TRIB_ICMS` | 1 | ST | 200 | 140 | Conferência (composto; não carrega) |
| `COD_INF_ITEM` | 1 | 1 UF | 196 | 196 | Cad_Efd_Codigo_Estadual (nova) |
| `COD_MOT_REST_COMPL_ST` | 7 | 7 UF | 117 | 111 | Cad_Efd_Codigo_Estadual (nova) |
| `GEN_ITEM_MERC_SERV` | 1 | GLOBAL | 100 | 100 | Conferência (documento 43) |
| `CL_ITENS_ENG_COM_TELECOM` | 1 | CLASCONS | 90 | 90 | Conferência (CONSUMO_TELECOM, documento 43) |
| `COD_MSG_PRE_VALIDACAO` | 1 | 1 UF | 60 | 52 | Não carrega; só registro |
| `TAB_CONTA_ISS_DF` | 1 | 1 UF | 60 | 59 | Conferência (Mov_Iss_Df_Conta_Cosif, documento 168) |
| `SELO_CONT_IPI` | 1 | IPI | 50 | 50 | Domínio selo_controle_ipi |
| `IND_SUBAP` | 1 | 1 UF | 49 | 49 | Cad_Efd_Codigo_Estadual (nova) |
| `MOD_DOC` | 1 | CARDOC | 41 | 39 | Conferência (domínios de documento) |
| `COD_PROD_USINAS` | 6 | 5 UF + GENERICA | 39 | 31 | Cad_Efd_Codigo_Estadual (nova) |
| `SIT_TRIB_COFINS` | 1 | ST | 37 | 33 | Conferência (Cad_Cst) |
| `SIT_TRIB_PIS` | 1 | ST | 37 | 33 | Conferência (Cad_Cst) |
| `CL_CONS_COMUN_TELECOM` | 1 | CLASCONS | 35 | 35 | Conferência (CONSUMO_TELECOM, documento 43) |
| `CL_CONS_GAS` | 1 | CLASCONS | 34 | 8 | Conferência |
| `CL_ENQ_IPI` | 1 | IPI | 31 | 31 | Domínio classe_enquadramento_ipi |
| `UF_SIG_NOM` | 1 | GLOBAL | 27 | 27 | Conferência (Cad_Estado) |
| `UF_COD_SIG` | 1 | GLOBAL | 27 | 27 | Conferência (Cad_Estado) |
| `CL_CONS_AGUA` | 1 | CLASCONS | 26 | 26 | Conferência |
| `FAIXA_CONS_ENG_ELET` | 1 | CLASCONS | 25 | 8 | Conferência |
| `TP_CONHEC_TRANS` | 1 | GLOBAL | 22 | 22 | Conferência (documento 43) |
| `TOT_PARC_REDZ` | 1 | GLOBAL | 21 | 21 | Não carrega (legado ECF. tb131); só registro |
| `OBR_ICMS_RECOL` | 2 | 1 UF + GLOBAL | 18 | 18 | Conferência com o domínio obrigacao_icms_recolher (tb19) |
| `VERSOES_LEIAUTE` | 1 | GLOBAL | 18 | 1 | Conferência (versões de leiaute, documento 43) |
| `SIT_TRIB_IPI` | 1 | ST | 14 | 14 | Conferência (Cad_Cst) |
| `AJ_APUR_IPI` | 1 | IPI | 13 | 13 | Cad_Icms_Codigo_Ajuste (Tipo_Apuracao ipi) |
| `TP_CT_E` | 1 | GLOBAL | 13 | 6 | Conferência (documento 43) |
| `COD_SIT` | 1 | CARDOC | 12 | 7 | Conferência (domínios de documento) |
| `SIT_TRIB_ICMS_A` | 1 | ST | 11 | 8 | Conferência (origem) |
| `SIT_TRIB_ICMS_B` | 1 | ST | 11 | 11 | Conferência (Cad_Cst) |
| `CLASS_CONTRIB_IPI` | 1 | IPI | 10 | 10 | Domínio classificacao_contribuinte_ipi |
| `TAB_DOC_ISS` | 1 | 1 UF | 8 | 8 | Domínio tipo_documento_iss_df |
| `ISS_UNIPROF` | 1 | 1 UF | 4 | 0 | Cad_Iss_Df_Valor_Uniprofissional (nova) |
| `IND_EMIT` | 1 | CARDOC | 2 | 2 | Conferência (domínios de documento) |
| `COD_ITEM_IPM_ST` | 1 | 1 UF | 1 | 1 | Cad_Efd_Codigo_Estadual (nova) |
| `ENQ_LEGAL_IPI` | 1 | IPI | 0 | 0 | Vazia: só registro em Cad_Tabela_Oficial |
| **Total** | **197** | | **35.421** | | |

# Anexo B. Matriz UF × tipo de tabela

Cada célula é o número de linhas da versão mais nova; "·" = a UF não enviou o arquivo; "(2)" = a UF enviou duas versões. **RR não tem arquivo nenhum.** Estão fora da matriz as tabelas de uma só UF (COD_INF_ITEM e IND_SUBAP, de PE, e as do DF) e as nacionais.

| UF | AJ | INF | BEN | REC | IPM | CRED | RESTST | USIN |
|---|---|---|---|---|---|---|---|---|
| AC | 84 | 63 | 34 | 38 | 39 | · | · | · |
| AL | 209 | 2.304 | 194 | 188 | 76 | · | · | 9 |
| AM | 298 | 67 | 56 | 359 | · | · | · | · |
| AP | 100 | 99 | 23 | 8 | · | 10 | · | · |
| BA | 273 | 19 | · | 91 | 52 | 18 | · | · |
| CE | 188 (2) | · | · | 44 | · | · | · | · |
| DF | 202 | 540 | 106 | 21 | · | · | · | · |
| ES | 127 | 289 (2) | 99 | 164 | 31 | · | · | · |
| GO | 846 (2) | 345 (2) | 138 | 41 | · | 13 | · | · |
| MA | 186 | · | 99 | 13 | 7 | 1 | · | · |
| MG | 184 | 8 | 193 | 130 | 7 | 27 | 8 | 5 |
| MS | 144 | · | 57 | 40 | · | 5 | 5 | · |
| MT | 1.450 (2) | 351 | 95 | 80 | · | 7 | · | 5 |
| PA | 106 | · | 160 | 268 | 47 | · | 4 | · |
| PB | 127 | 45 | 62 | 70 | · | 7 | · | 5 |
| PE | 3.056 | · | · | 32 | 8 | 6 | · | · |
| PI | 474 (2) | 67 | · | 29 | 11 | 11 | · | · |
| PR | 478 | 538 (2) | 7 | 30 | 7 | 14 | · | 10 |
| RJ | 321 | 720 (2) | 141 | 32 | 193 | 58 | 7 | · |
| RN | 590 | 2 | 198 | 61 | 22 | 13 | · | · |
| RO | 153 | · | 289 | 108 | · | 7 | 9 | · |
| RS | 288 (2) | 731 (2) | 949 (2) | 53 | 6 | 34 | 74 | · |
| SC | 353 (2) | 612 (2) | 311 (2) | 84 | 26 | · | · | · |
| SE | 61 | 1 | 92 | 41 | · | 14 | 10 | · |
| SP | 158 | · | 80 | 102 | 13 | 6 | · | · |
| TO | 170 | 30 | · | 19 | 22 | · | · | · |
| GENERICA | 31 | · | · | 16 | · | 6 | · | 5 |

AJ = AJ_APUR_DED; INF = INF_ADIC_APUR; BEN = AJ_BENEF_INCENTIVO; REC = REC_REF_OBRIGACAO; IPM = COD_ITEM_IPM; CRED = TP_UTIL_CRED_FISCAIS; RESTST = COD_MOT_REST_COMPL_ST; USIN = COD_PROD_USINAS.
# Anexo C. Avisos e higiene da carga

Tudo abaixo é **aviso**: a linha carrega como veio, com o texto em `Alerta_Carga` e no relatório de conferência, exceto as 7 de teste (Q172-5).

| Aviso | Quantas | Onde | Tratamento |
|---|---|---|---|
| Vigência de um dia (início = fim) | 1.065 nas versões mais novas (1.256 em todas as lidas) | MT 793, GO 106, RJ (informação adicional) 88, RS (informação adicional) 77, outras | Carrega com aviso (Q172-2); C4 pergunta ao contador |
| Linha de teste da fonte | 7 | RO `TESTE_ED`, `TESTE_EC`; RS011522, RS021900, RS23002106, RS25002106, RS53002113 | **Não carrega**; registro da carga com o motivo (Q172-5) |
| Texto truncado | 1 | TO, `TO450002` ("ARCELA SUJEITA…", sem a primeira letra) | Preserva e avisa |
| Aspas ou tabulação no texto | 20 | ES | Preserva e avisa |
| Espaço sobrando no texto | 838 | várias UFs | Preserva e avisa |
| Código com mais de um texto ao longo do tempo | 3.066 códigos em 89 tabelas (1.038 são o CEST, cujo texto é só um aviso) | maiores: GO e MT (ajuste da apuração), AM (receita), PR, RN, PE, RS | Chave = código + início da vigência |
| Formato de data fora de DDMMAAAA | 0 | --- | --- |
| Vigências sobrepostas ou fim anterior ao início | 0 | --- | --- |
| Arquivo reenviado idêntico | 6 (RN) e 1 (AM) | --- | Contado uma vez; os 204 recebidos viram 197 |
| UF sem nenhum arquivo | 1 (RR) | --- | O ERP avisa e pede o código (Q172-4) |
| Arquivos sem nome de coluna | 22 | ver seção 3 | Lidos pela posição |
| Terceiro bloco do arquivo de receitas de SP em UTF-8 | 1 | SP | Leitura linha a linha (UTF-8 primeiro, Windows-1252 se falhar) |
