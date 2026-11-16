# Tabelas do Portal da NF-e e da Receita, NT 2023.01 e atos da NBS — Documento 221

*Você respondeu "Q218-18 - Sim" e enviou 22 arquivos (a NT 2023.01 em perguntas e respostas e 21 tabelas do Portal da NF-e e da Receita) e, depois, 12 PDFs sobre a NBS. Li tudo, conferi contra o dicionário (revisão 44) e as cargas anteriores e gerei as cargas que o dicionário comporta; o que não tem entidade virou **proposta** com pergunta. **Nada foi aplicado ao dicionário.** O aviso A22 já entrou no desenho do documento 218; a resposta "Sim" da Q218-18 só o confirma.*

> **Situação em 16/11/2026:** as propostas deste documento foram **aprovadas** (D-N588; Q220-1, Q220-5 e Q221-1 a Q221-13) e **consolidadas na revisão 45** (documentos 222 e 223, D-N589). As cargas foram refeitas na pasta `Carga45-20261116`, que substitui os arquivos de NBS, cClassTrib, CFOP e unidades das cargas citadas aqui. O texto abaixo fica como histórico.

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| Arquivo recebido | Destino | Resultado |
|---|---|---|
| IT 2025.002 v1.71, cClassTrib e CST | `Cad_Cst`, `Cad_Cclasstrib`, `Cad_Cclasstrib_Modelo` | **18 CST** (36 linhas, uma por tributo), **173 cClassTrib**, **2.941 marcas** de modelo (173 × 17); responde a Q220-4 |
| IT 2025.002 v1.70, cCredPres | `Cad_Credito_Presumido_Ibs_Cbs` | **13 linhas** |
| IT 2023.002 v2.00 e v2.10, CFOP | `Cad_CFOP` | **619 CFOP**; as duas versões têm as mesmas marcas; a v2.10 acrescenta Título e Descrição |
| Municípios (arquivo 250210) | `Cad_Municipio` | **5.571** em 27 UFs |
| Países da NF-e (NT 2018.003 v1.01) | `Cad_Pais` | **261 códigos** (aba `cPais_2`) |
| Unidades comerciais (2016) e uTrib (IT 2024.001 v2.40) | `Cad_Unidade_Medida` | **68 unidades** |
| Códigos de produto ANP (18/11/2024) | `Cad_Produto_Anp` | **1.031 códigos**, 120 sem descrição |
| NCM x uTrib de 01/02/2026 e de 01/10/2026 | `Cad_Classificacao_Mercadoria.Unidade_Estatistica` | **10.516 NCM** (confere 100% com os itens do Portal) |
| Meios de pagamento (04/03/2026) e bandeiras | `Cad_Classe_Sistema` | domínio `forma_pagamento_dfe` com **23 valores**; `meio_pagamento_vinculo_dfe` confirmado; bandeiras (28) em proposta |
| Combustíveis monofásicos, pBio obrigatório, FCP por UF, prefixo GS1, tipo e espécie de veículo, regime especial (PR), CNPJ alfa, lista de serviços (LC 116), alíquota da CBS | sem entidade | **propostas** (seção 4) |
| NT 2023.01, perguntas e respostas (22/05/2023) | documentos 170 e 218 | seção 5: **três lacunas** no dicionário |
| 12 PDFs de atos da NBS | Q220-3 | seção 6: a **NBS 2.0 continua vigente**; resta confirmar qual é o PDF |

A carga está na pasta `CargaPortalNFe-20261116` (zip do mesmo nome), com LEIA-ME, ordem de carga, registro das cargas e o hash dos 22 arquivos. A carga da NCM e da NBS (documento 220) foi **reemitida** só para trocar o texto da vigência da NBS (seção 6); os dados não mudaram.

# 2. As cargas

| Arquivo | Linhas | O que tem de importante |
|---|---|---|
| `Cad_Cst_IBS_CBS_18_codigos_x_2_tributos` | 36 | os 18 CST, uma linha para a CBS e outra para o IBS (Q221-1); `Familia` vazia (a IT não define família) |
| `Cad_Cclasstrib_173` | 173 | aponta o CST pela linha da CBS; segue a regra da Q161 (`Indicador_Mono_Dif` vazio; `Indicador_Grupo_Biocombustivel_Diferenca` e `Codigo_Anexo_Tecnico` preenchidos) |
| `Cad_Cclasstrib_Modelo_173x17_AGUARDA_MODELOS` | 2.941 | **não carregar ainda**: `Cad_Modelo_Documento_Fiscal` não tem dados; a coluna `Indicador_Modelo_IT` troca por `ID_Modelo_Documento` pelo mapa proposto |
| `Cad_Credito_Presumido_Ibs_Cbs_13` | 13 | percentuais e reduções de transição vão **como texto publicado** (colunas `_TEXTO`), porque a planilha mistura número, fórmula e texto de lei |
| `Cad_CFOP_619` | 619 | `Indicador_Combustivel` = sim para `indComb` 1 ou 2 (63 CFOP); valor bruto na última coluna (Q221-6) |
| `Cad_Municipio_5571`, `Cad_Pais_NFe_261`, `Cad_Unidade_Medida_68` | 5.571, 261, 68 | ver seção 3, itens 11 a 13 |
| `Cad_Produto_Anp_1031` | 1.031 | códigos do Portal; descrição e datas da tabela SPED GLOBALANP v16 (908 códigos) |
| `Cad_Classificacao_Mercadoria_NCM_Unidade_Estatistica_10516` | 10.516 | atualiza a NCM da carga do documento 220 (Q221-8) |
| `Cad_Classe_Sistema_forma_pagamento_dfe_23_valores` | 23 | `tPag`, com vigência de cada código |
| `Cad_Classe_Sistema_meio_pagamento_vinculo_dfe_atualiza_6_valores` | 6 | tira o "provisório até a tabela nacional" dos códigos 15, 17, 18, 20, 23 e 24 |

# 3. O que a conferência achou

**CST e cClassTrib**

(1) **O CST de IBS/CBS tem 18 códigos, não 19.** A seção de `Mov_Apuracao_Tributo_Item.ID_Cst` do documento 10 fala em "um CST próprio de 19 códigos". A tabela da v1.71 tem 18 (000, 010, 011, 200, 220, 221, 222, 400, 410, 510, 515, 550, 620, 800, 810, 811, 820, 830). Corrijo o texto na consolidação (Q221-1 inclui o aceite).

(2) **Os códigos novos das v1.50 a v1.70 estão todos na tabela:** conferi 000005, 000006, 200054 a 200056, 400003, 400004 e 550024 a 550029, que o documento 220 dizia não existirem em carga nenhuma. A tabela tem 173 classificações, todas com início em 01/01/2026; os cClassTrib `220001`, `220002` e `220003` têm **fim em 01/01/2026**, o mesmo dia do início (vigência de um dia, "inclusão de fim de vigência" da v1.71). Distribuição por CST: 200 (56), 410 (38), 550 (29), 820 (9), 620 (7), 000 (6), 011 (5), 221 (4), 400 (4), 811 (3), 220 (3), 010 (2), 800 (2) e um cada em 222, 510, 515, 810 e 830.

(3) **O `620003` (monofásica com responsabilidade de retenção de tributos por terceiros) vem sem nenhuma marca de grupo monofásico** (`ind_gMonoPadrao`, `ind_gMonoReten` e `ind_gMonoRet` zerados), embora o CST 620 exija o grupo monofásico. Pode ser erro da tabela; pergunto à Receita (C358). O `620007` (perecimento no regime monofásico) também não tem marca, o que é coerente com o evento.

(4) **Duas colunas da tabela não têm campo.** O **Tipo de Alíquota** tem cinco valores (sem alíquota 89, padrão 64, uniforme setorial 8, fixa 7, uniforme nacional de referência 5) e **não existe** em `Cad_Cclasstrib` (Q221-2). A coluna **ANEXO** vem em dois formatos: 33 classificações com o anexo técnico de 5 posições (ZXXXY) e **19 só com o número do anexo da LC 214 (1 a 15)**, que não cabe em `Codigo_Anexo_Tecnico` (código de 5); essas ficam vazias e o número vai ao arquivo de conferência (Q221-3).

(5) **Redução diferente entre IBS e CBS:** só o `200025` (serviços de educação do ProUni): IBS 60%, CBS 100%. As outras 172 têm o mesmo percentual nos dois tributos (112 sem redução, 26 com 100%, 23 com 60%, 5 com 40%, 3 com 30% e as demais com 70% ou 80%).

(6) **Marcas de modelo** (quantas classificações cada indicador permite): NF-e 104, NFS-e 73, DUIMP 62, NFC-e 40, NFeABI 19, NFCom 16, NF3e 15, DeRE 13, CT-e 12, CT-e OS 12, NFAg 11, DIR 11, NFGas 10, BP-e 9, BP-e TA 8, BP-e TM 3 e NFS-e Via 1. **Três classificações não permitem nenhum modelo:** `410011` (ouro como ativo financeiro), `410028` (bens imóveis de pessoa física não contribuinte) e `410034` (fundos de investimento). Faz sentido para as duas primeiras, que a NFeABI ou outro documento tratam fora da tabela, e a v1.71 desativou o `410028` para a NFeABI e o `410034` para a DeRE; deixo como veio.

(7) **`ind_DUIMP` é marca de modelo** (a v1.71 o lista ao lado de DeRE e DIR, "criação do indicador ind_DUIMP"), **não** "exige o número da DUIMP". O `Indicador_Duimp` de `Cad_Cclasstrib` tem outro sentido e a tabela não traz coluna para ele: ficou vazio (Q221-5). **DIR continua sem definição no IT** (só ABI e DeRE são definidos): 11 classificações a permitem.

**cCredPres**

(8) Os 13 códigos têm início de CBS em 01/01/2027 (códigos 1 a 7, 10 e 13) e de IBS em 01/01/2027 ou 01/01/2029 (3, 8, 9 e 12). `ind_gIBSCredPres` e `ind_gCBSCredPres` são sim/não no IT ("indica se deve ser preenchido o grupo"); no dicionário o campo tem três valores (`nao_permite`, `permite`, `exige`). Mapeei 1 para `exige` e 0 ou vazio para `nao_permite`; **`permite` não aparece na planilha** (Q221-7). Os cClassTrib da nota referenciada (410014 a 410017, nos códigos 1 a 4) existem todos na tabela; nos códigos 5 a 13 a planilha traz condição em texto, que foi para `Condicao_Nota_Referenciada`.

**CFOP**

(9) Os 619 CFOP têm código único, início de vigência quase sempre em 01/01/2006 (560) e **nenhum com fim**. Os indicadores da v2.00 e da v2.10 são idênticos. **72 CFOP** têm `indExcIBSCBS`. O IT define `indComb` como sim/não ("permitido em operação com combustível ou lubrificante"), mas a tabela usa **0 (556), 1 (16) e 2 (47)**: o 1 reúne armazenagem, retorno e venda a consumidor final (1663, 1664, 5663 a 5667, 6663 a 6665) e compras do exterior (3651 a 3653); o 2 reúne compra, transferência e venda dentro do país (1651 a 1659 e semelhantes). O significado exato não está no IT: C359 e Q221-6.

**NCM x uTrib**

(10) A tabela de **01/10/2026** tem 10.516 NCM, **igual ao conjunto dos 10.516 itens analíticos do Portal**, sem diferença de código, de vigência ou de unidade. A de 01/02/2026 tem 10.520: cinco NCM que **acabaram em 01/10/2026** (59039000, 65061000, 73063000, 74061000 e 84129020) e não tem o 85181020 (novo em 01/10/2026, como já vimos na Q162-E1). A unidade de todos os códigos em comum é a mesma nas duas. Distribuição: KG 7.601, UN 2.461, M2 141, M3 135, PARES 58, TON 43, LT 34, METRO 15, DUZIA 10, QUILAT 9, G 4, 1000UN 4 e MWHORA 1. **A sigla do litro é `LT`** (o exemplo do dicionário diz "L").

**Geografia, unidades e produtos**

(11) **Municípios:** 5.571 em 27 UFs, código de 7 dígitos com o prefixo da UF conferido, sem repetição; o arquivo é de 10/02/2025 e não tem código Siafi. **Países:** a aba `cPais_2` é a completa (264 linhas, 261 códigos); tem **MACEDONIA DO NORTE** e **ESSUATINI**, que a aba `cPais` não tem. Três códigos aparecem com dois nomes (1988 COVEITE e KUWAIT, 4499 MACEDONIA e MACEDONIA DO NORTE, 7544 SUAZILANDIA e ESSUATINI), todos "apenas alteração de nome" sem a data da troca: guardei o nome novo e o antigo no motivo. Doze códigos acabaram em 31/05/2018. **Quinze países de 2017 não têm ligação com o código Siscomex** na Carga32 (lista no arquivo de conferência); a tabela não traz ISO.

(12) **Unidades:** a tabela comercial tem 61 siglas e a uTrib tem 13. **Seis siglas coincidem** (DUZIA, KG, M2, M3, PARES, TON) e **seis pares são a mesma coisa com sigla diferente** (UN e UNID, LT e LITRO, METRO e M, G e GRAMAS, QUILAT e K, MWHORA e MWH). A carga traz as 13 da uTrib mais as 55 comerciais que não repetem a sigla, **sem fundir** (Q221-9).

(13) **ANP:** 1.031 códigos de 9 dígitos, sem repetição. **908 têm descrição na tabela SPED GLOBALANP v16** (e as datas dela), 3 têm só a descrição da tabela monofásica e **120 não têm descrição em fonte nenhuma**; a tabela SPED tem **22 códigos que não estão na lista do Portal**. Os 40 produtos da tabela monofásica estão todos na lista. Sete códigos têm data de fim na SPED.

**Pagamentos**

(14) `tPag` tem **23 códigos** (a planilha lista de 01 a 24 com lacunas, mais 90, 91 e 99); os códigos **23 (PIX automático) e 24 (TEF, book transfer) valem desde 04/05/2026** e o **91 (pagamento posterior) desde 03/11/2025**; os cinco novos de 01/07/2024 são 05, 17, 20, 21 e 22. Os seis códigos do vínculo de pagamento da IT 2026.001 (15, 17, 18, 20, 23 e 24) **estão todos na tabela**, o que confirma o domínio `meio_pagamento_vinculo_dfe` da Q162-1. `Mov_Nota_Fiscal_Saida_Pagamento.Bandeira` guarda só o código de 2 posições: a tabela de **28 bandeiras** (01 Visa a 27 Ticket, mais 99) fica como domínio proposto, para validar o campo.

# 4. As tabelas sem entidade no dicionário

Cada uma está em `07-propostas`, com a pergunta correspondente na seção 7.

(15) **ICMS monofásico por produto ANP** (`Cad_Icms_Monofasico_Ad_Rem_por_Produto_Anp_PROPOSTA`): 40 produtos na tabela atual, **vigente desde 01/01/2026**, em três valores: **R$ 1,17 por litro** (21 produtos: diesel B, B100 e diesel para geração de energia), **R$ 1,57 por litro** (15: gasolina A e C, etanol anidro) e **R$ 1,47 por quilograma** (4: GLP, butano e propano); mais **151 linhas de histórico** com as janelas de vigência (sem buraco nem sobreposição por produto; as janelas começam em 01/05/2023, 01/06/2023, 01/02/2024, 08/05/2024, 03/12/2024, 01/02/2025 e 01/11/2025). A tabela traz também `pBio` (28 produtos) e `origComb`. `Cad_Aliquota_Combustivel` é só de CBS e IBS (documento 170), e o item da nota guarda a alíquota ad rem no complemento; **não há onde guardar a tabela de alíquotas do ICMS**, que o ERP precisa para validar a nota (Q221-10).

(16) **Mistura obrigatória (`pBio`)** (`Cad_Combustivel_Mistura_Obrigatoria_pBio_PROPOSTA`, 23 linhas): hoje a gasolina C comum e aditivada tem **32% de anidro desde 01/08/2026** (30% de 01/08/2025 a 31/07/2026; 27% de 16/03/2015 a 31/07/2025) e a premium, **25%**. O campo `Combustivel_Percentual_Biodiesel` do item existe, mas o percentual obrigatório por produto e data não: sem a tabela o ERP não confere a nota (Q221-10).

(17) **Fundo de Combate à Pobreza por UF** (`Cad_Fcp_Aliquota_por_Uf_PROPOSTA`, 30 alíquotas em 27 UFs): 4 UFs sem FCP (AC, AP, PA e SC), 20 com alíquota fixa de 2% (algumas com mais de uma alíquota possível: AL 1% e 2%, AM 2% e 1,2%, SE 2% e 1%), RJ com máximo de 4% e GO, MT e RR com "máxima 2%, padrão". O dicionário só tem os valores do FCP nos movimentos (DIFAL e ST); falta a tabela de referência (Q221-11).

(18) **Prefixo GS1** (127 faixas, sem sobreposição; Brasil 789 a 790) para validar o GTIN; **tipo e espécie de veículo** (39 pares, desde 12/03/2020), para o `veicProd`; **padrão do número do processo de regime especial** (só o Paraná, `NNNNN/AAAA`, com a expressão regular); **CNPJ alfanumérico de teste** (35 CNPJ em 9 UFs, todos com os dois dígitos verificadores corretos conforme o cálculo do módulo 11 do alfanumérico; o `PC3D315K000193` aparece no RS e no ES). Os CNPJ de teste não devem entrar como dado de produção: servem de massa de teste (Q221-11).

(19) **Lista de serviços da LC 116** (`cListServ`, 200 subitens de 40 itens): é o que a NF-e traz no grupo de ISS; no dicionário corresponde aos níveis item e subitem de `Cad_Servico_Tributacao_Nacional`, que **ainda não tem nenhuma carga** (a NFS-e Nacional traz o desdobro de 6 dígitos). Ficou como proposta porque `Analitico` depende de qual documento (Q221-11).

(20) **Alíquota da CBS de 2026: 0,9%** (IT 2026.002 v1.00); **2027: "aguarda legislação"**. Confere com `Cad_Aliquota` de 2026 e não gera carga.

# 5. NT 2023.01, perguntas e respostas (versão de 22/05/2023)

São 25 perguntas sobre o ICMS monofásico dos combustíveis (Convênios ICMS 199/22, 15/23 e 19/23) na NF-e e na NFC-e. O que muda para o dicionário:

(21) **Três lacunas.** (a) **`origComb` é repetível:** as perguntas 6 e 16 mandam incluir "tantos registros quantos necessários até totalizar 100%", e no GLP/GLGN o 100% vale em separado para o nacional e para o importado (o exemplo tem três registros nacionais e dois importados); o item da nota tem **um único conjunto** (`Combustivel_Indicador_Importado`, `ID_Estado_Origem_Combustivel` e `Combustivel_Percentual_Origem`), que não comporta o exemplo (Q221-12). (b) **`pRedAdRem` e `motRedAdRem`** (pergunta 11, redução da alíquota ad rem por benefício fiscal): **não existem** no dicionário; a própria NT diz que o tratamento dos benefícios "será disponibilizado", então fica como pergunta sem urgência (Q221-12). (c) A **tabela de alíquota ad rem e de mistura obrigatória** (seção 4) não tem entidade.

(22) **O que o dicionário já cobre.** O complemento do item guarda `qBCMonoRet`, `qBCMonoReten` e `qBCMonoDif` (quantidade), `pDif` (percentual), `vICMSMonoOp` (valor da operação) e a alíquota ad rem diferida; o item guarda `pGLP`, `pGNn`, `pGNi` e `pBio`; `Mov_Apuracao_Tributo_Item.Forma_Tributacao` cobre a alíquota específica por unidade. As regras de preenchimento por CST (02, 15, 53 e 61), os exemplos numéricos (12% de B100 e 27% de EAC, alíquotas R$ 0,9456 e R$ 1,22 de 2023) e o arredondamento da pergunta 20 (**ABNT NBR 5891**, quatro casas: 0,63043152 vira 0,6304 e 0,31516848 vira 0,3152) são regra de cálculo do motor e entram no desenho do documento 218; **confira que os valores do exemplo são de 2023** e que a tabela atual (R$ 1,17, 1,57 e 1,47) já os substituiu.

(23) **Datas e validações da NT:** obrigatória desde **01/05/2023** (diesel, biodiesel e GLP/GLGN) e **01/06/2023** (gasolina e etanol anidro); os campos novos **não foram validados** até 31/08/2023 (pergunta 3); estoques, notas em trânsito, devoluções e retornos de armazenagem passam à sistemática monofásica por similaridade (perguntas 22 a 24). **Esta é a versão de 22/05/2023:** o layout posterior da NF-e pode ter mudado (a própria NT avisa que a gasolina e o etanol anidro entrariam "numa próxima atualização"); não conferi a versão atual.

# 6. Atos da NBS (Q220-3)

(24) **A NBS 2.0 continua vigente em 16/11/2026, pelo que você enviou.** A **Portaria Conjunta RFB/SCS nº 1.429, de 12/09/2018** aprovou a NBS 2.0 e as NEBS 2.0 e **produz efeitos desde 01/01/2019** (art. 3º); a **nº 2.000, de 18/12/2018** substituiu os Anexos I e II; a **Portaria ME nº 413, de 19/08/2019**, art. 10, manda aplicar a versão 2.0 **da nº 2.000/2018** até novo ato conjunto e revogou a Portaria Interministerial 385/2012 e a nº 1.429/2018; a **Portaria Interministerial MDIC/MF nº 163, de 22/01/2026**, revogou a 413/2019 e criou o **Comitê Gestor da NBS e das NEBS** (CGNBS), que decide por consenso, reúne-se ao menos uma vez por semestre e só altera a nomenclatura por **ato conjunto do Secretário da Receita Federal e do Secretário de Desenvolvimento Industrial, sem delegação** (art. 7º). As resoluções do CGNBS de 22/09/2026, publicadas em 29/10/2026 e **retificadas em 03/11/2026 para nº 1, nº 2 e nº 3** (regimento interno, formulário e o serviço "Propor Alteração na NBS/NEBS" no Gov.br), tratam só de procedimento; **nenhuma altera código**. A Portaria 413 previa revisão anual até 31/10 com efeito em 01/01; a 163/2026 não fixa calendário. Entre os PDFs, **não há ato posterior que mude a NBS**, mas não consultei o DOU de 2019 a 2026 para afirmar que não existe.

(25) **O PDF que você enviou continua sem prova de ser o Anexo I da Portaria 2.000/2018.** Os atos só trazem o Anexo como arquivo anexado ("Anexo I.pdf"), que não veio. O PDF diz "com alterações de 6.12.18", compatível com a data da 2.000/2018 (18/12/2018), mas **não** prova a identidade (Q221-13). A vigência de 01/01/2019 deixa de ser "leitura minha" (tem base normativa), e a carga segue `com_pendencia` só por isso. Os três atos mais antigos (Decreto 7.708/2012, Portaria Conjunta 1.820/2013 e Portaria Interministerial 385/2012) e a Lei 12.546/2011 (arts. 24 a 27) são a origem e a base legal; o Decreto 7.708 (art. 2º) manda adotar a NBS como **nomenclatura única** para serviços, intangíveis e operações que produzam variações no patrimônio.

# 7. Perguntas

Uma resposta por linha; recomendação minha na terceira coluna. As do contador estão no documento 188 (C358 e C359).

| Id | Pergunta | Recomendação |
|---|---|---|
| Q221-1 | O CST de IBS/CBS entra em `Cad_Cst` com **duas linhas por código** (CBS e IBS, como o desenho de `Cad_Cst` exige) e `Cad_Cclasstrib.ID_Cst` aponta a linha da **CBS**, com o Motor achando a do IBS pelo mesmo código? E o texto "19 códigos" do documento 10 passa a "18"? | Sim |
| Q221-2 | `Cad_Cclasstrib` ganha `Tipo_Aliquota` (enumeração: sem alíquota, padrão, uniforme setorial, fixa, uniforme nacional de referência), carregada da coluna "Tipo de Alíquota" (89, 64, 8, 7 e 5 classificações)? | Sim |
| Q221-3 | `Cad_Cclasstrib` ganha `Numero_Anexo_Lc_214` (código até 2, 1 a 15) para as 19 classificações que só trazem o número do anexo da LC 214, sem mexer no `Codigo_Anexo_Tecnico`? | Sim |
| Q221-4 | Os 17 indicadores de modelo do IT (NFeABI, NF-e, NFC-e, CT-e, CT-e OS, BP-e, BP-e TA, BP-e TM, NF3e, NFS-e, NFS-e Via, NFCom, NFAg, NFGas, DeRE, DIR e DUIMP) viram **17 linhas de `Cad_Modelo_Documento_Fiscal`**, com `Codigo_Interno` próprio onde não há número oficial (DeRE, DIR, DUIMP, NFS-e, NFS-e Via, NFeABI, NFAg), seguindo o mapa de `07-propostas`; as 2.941 marcas entram depois? Resolve a Q220-2 | Sim |
| Q221-5 | `Indicador_Duimp` de `Cad_Cclasstrib` (hoje "exige o número da DUIMP") **sai**, porque a v1.71 só traz `indDUIMP` como marca de modelo (62 classificações), que fica em `Cad_Cclasstrib_Modelo`? Diga o que é DIR (11 classificações) | Sim; diga o que é DIR |
| Q221-6 | `Cad_CFOP.Indicador_Combustivel` (booleano) passa a **`Tipo_Combustivel`** com os valores 0, 1 e 2 da tabela, até a Receita explicar a diferença (C359)? Hoje a carga marca "sim" para 1 e 2 e guarda o bruto | Sim |
| Q221-7 | `Indicador_Credito_Ibs` e `Indicador_Credito_Cbs` de `Cad_Credito_Presumido_Ibs_Cbs` ficam com **dois valores** (`exige` e `nao_permite`), tirando o `permite`, que a planilha não usa? | Sim |
| Q221-8 | A uTrib da NCM (tabela de 01/10/2026) entra em `Unidade_Estatistica` (10.516 NCM), como unidade provisória, e as 5 NCM extintas em 01/10/2026 ficam só no arquivo de conferência? A tabela diz "uTrib para uso em operações de comércio exterior", que na prática é a unidade estatística | Sim |
| Q221-9 | `Cad_Unidade_Medida` carrega as duas tabelas **sem fundir** (as 13 da uTrib mais as 55 comerciais) e ganha um campo `Origem_Tabela` (comercial ou uTrib de comércio exterior), para o ERP converter `UNID` e `UN`, `LITRO` e `LT` pelo cadastro de conversão? | Sim |
| Q221-10 | Entram duas entidades novas, versionadas: **`Cad_Icms_Monofasico_Aliquota`** (produto ANP, valor ad rem em reais por unidade, unidade, vigência, ato) com as 40 linhas atuais e as 151 do histórico, e **`Cad_Combustivel_Mistura_Obrigatoria`** (produto ANP, percentual de biodiesel ou anidro, vigência), com as 23 linhas? | Sim |
| Q221-11 | Entram como cadastros de referência: **FCP por UF** (30 linhas), **prefixo GS1** (127), **tipo e espécie de veículo** (39), **padrão do processo de regime especial** (PR) e **bandeiras** (28, domínio `bandeira_cartao_dfe`)? O CNPJ alfa vira **massa de teste**, e o `cListServ` espera a carga da NFS-e Nacional | Sim |
| Q221-12 | O item da nota ganha uma tabela filha **`origComb`** (indicador de importação, UF de origem e percentual, em quantas linhas for preciso), em lugar do conjunto único de três campos, e os dois campos `pRedAdRem` e `motRedAdRem` esperam o tratamento dos benefícios (a NT diz que será divulgado)? Vale para entrada e para saída | Sim para a tabela filha; os dois campos esperam |
| Q221-13 | Confirme que o PDF "Anexo I da NBS 2.0 com alterações de 6.12.18" é o **Anexo I da Portaria Conjunta RFB/SCS nº 2.000/2018** (ou envie o anexo publicado), e que a NBS 2.0 segue vigente em 2026. Fecha a Q220-3 | Confirmar |

**Sai da lista:** a Q218-18 (respondida "Sim"), a Q220-3 (o essencial está na seção 6; resta a Q221-13), a Q220-4 (a planilha v1.71 chegou) e a Q220-2 (virou as Q221-4 e Q221-5). Seguem a Q220-1 e a Q220-5.

# 8. O que não fiz

(a) **Não consultei o DOU de 2019 a 2026** para provar que não houve alteração da NBS. (b) **Não validei os dados com o contador:** tudo sai `provisorio`. (c) **Não carreguei as marcas de modelo**, porque o cadastro de modelos está vazio. (d) **Não confirmei a descrição dos 120 códigos ANP sem descrição**: a fonte seria a tabela da ANP (SIMP). (e) **Não conferi se a versão atual da NF-e mudou as regras da NT 2023.01.** (f) **Os dados de municípios são de fev/2025**: vale checar se algum município foi criado ou renomeado depois.
