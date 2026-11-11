# Tabelas externas do SPED: EFD-Contribuições e EFD ICMS/IPI — Documento 43

*Leitura das 86 tabelas externas oficiais que Alberto enviou (76 da EFD-Contribuições e 10 da EFD ICMS/IPI) contra o dicionário e os documentos 10, 14, 32, 33, 34, 36, 37 e 38. Propostas de carga e de ajuste; nada foi alterado no dicionário. Revisão 2 em 11/10/2026, com o Guia Prático v1.35 e as tabelas do Portal.*

Mlegate · Alberto Beyeler · Outubro de 2026

# Revisão 2 — Guia Prático v1.35 e tabelas do Portal (11/10/2026)

Chegaram o **Guia Prático da EFD-Contribuições (versão 1.35, 18/06/2021)**, o roteiro do lucro presumido (PVA 2.04, 2013) e **36 tabelas do Portal do SPED** (19 .doc e 17 .xls: 4.3.3 a 4.3.18, 5.1.1, 7.1.1 a 7.1.4, CFOP × operações geradoras de créditos e a correlação DACON × EFD-Contribuições). Esta revisão corrige o que o documento deduzia pelo conteúdo e fecha parte das pendências. O desenho completo da EFD-Contribuições a partir do Guia está no **documento 44**. Esta revisão não altera o dicionário e substitui, onde houver conflito, o texto das seções 1 (item 5, "dois arquivos parecem atrasados"), 2, 4, 5, 6, 7, 8, 11, 12 e 13 a seguir.

## O que fica fechado

O mapeamento arquivo para tabela do Guia (**P43-01**) está fechado para 75 dos 86 arquivos; restam sem número ANP, BENEFICIOS_FISCAIS, CFOP_DEVOLUCAO, CFOP_DEVOLUCAO_VENDA, CFOP_RECEITA, CONSUMO_TELECOM, DATA_LIMITE_ENTREGA, IND_DED_DIV, MENSAGENS_USUARIO, PRAZO_DECADENCIA e TIPO_CT. **P43-02** reduz-se a `OBRIGA_DET` (sem definição), à expansão literal das letras P/R, P/N e S/N (só por inferência) e à confirmação do contador. **P43-05** (tb1316, tb14, tb13957) e **P43-14** (indicadores de CFOP) não mudam: o material novo não os trata. **P43-08** muda: a tabela 4.3.11 de 16/09/2026 também termina o óleo diesel (código 102) em 31/05/2026, então a lacuna está na fonte oficial, não no arquivo.

## As 21 tabelas do Portal contra os arquivos

| Tabela | Arquivo | Material do Portal | Situação | Resumo |
|---|---|---|---|---|
| 4.3.3 | CST_PIS | Tabela II CST-PIS (sem data) | igual | Mesmos 33 códigos. |
| 4.3.4 | CST_COFINS | Tabela III CST-Cofins (sem data) | igual | Mesmos 33 códigos. |
| 4.3.5 | CS_APUR | 4.3.5 (sem data) | igual | Mesmos 14 códigos; o 70 (RET) existe nos dois e não no Guia v1.35. |
| 4.3.6 | TIPO_CRED | 4.3.6 atualizada em 15/12/2022 | equivalente com diferenças | Tabela nova não lista 199/299/399 (no arquivo terminam em 31/03/2023); textos diferentes em 106/206/306 e 107/207/307; o arquivo guarda 106/206/306 em três versões (a do meio dura um dia, 11/03/2022). |
| 4.3.7 | BC_CRED | 4.3.7 v1.0.2, 02/03/2023 | equivalente com diferenças | Textos novos nos códigos 11 (amortização e depreciação de edificações) e 13 (inclusive créditos presumidos sobre receitas); código 14 renomeado para transporte de cargas com prestador PF/PJ optante pelo Simples (o arquivo tem as duas versões, divisão em 22/12/2022). |
| 4.3.8 | AJ_CONTRIB_CRED | 4.3.8 v1.0.3, 01/04/2026 | equivalente | Códigos 10, 11 e 12 (redução linear de incentivos, LCP 224/2025, IN RFB 2.305/2025, desde 01/04/2026) já estão no arquivo. Códigos 07 a 09: texto "Ajuste da CPRB: ..." na tabela e início 01/12/2011 (arquivo 01/01/2011). Código 25 (ICMS destacado em documento fiscal complementar): na tabela inicia em 01/12/2011 e não tem fim; no arquivo inicia em 01/01/2002 e termina em 31/12/2018. |
| 4.3.9 | ALIQ_AGRO_FRIGO | 4.3.9 atualizada em 17/01/2023 | igual | Códigos, vigências e alíquotas idênticos (conferido por linha do tempo). Diferem só os textos de NCM (a tabela traz as exceções por extenso). |
| 4.3.10 | PROD_MONO_ALIQ_DIFER | 4.3.10 sem data e sem versão no título | igual, com 4 divergências | Linha do tempo igual em 189 de 193 códigos. Ver diferenças. |
| 4.3.11 | PROD_MONO_ALIQ_UNID | 4.3.11 v1.34, 16/09/2026 | tabela mais nova | Linhas de 2026 que o arquivo não tem: gasolina, querosene, biodiesel e etanol. Ver diferenças. |
| 4.3.12 | PROD_ST | 4.3.12 atualizada em 17/11/2014 | equivalente | Na tabela os códigos 401 a 409 só remetem a 4.3.10/4.3.11; o arquivo traz alíquotas em 401 e 402. |
| 4.3.13 | PROD_ALIQ_ZERO | 4.3.13 v1.36, 16/09/2026 | tabela mais nova | Código novo 226 (etanol combustível, 10/09 a 09/10/2026) e prorrogação do biodiesel 220/229 até 31/07/2026. |
| 4.3.14 | OPER_COM_ISENCAO | 4.3.14 atualizada em 28/04/2026 | equivalente | Tabela traz 401, 402 e 403 (eventos Fifa, desde 01/2011) que o arquivo não tem; o 904 (23/04/2026) está nos dois. |
| 4.3.15 | OPER_SEM_INCIDENCIA | 4.3.15 v1.02 | igual | Mesmos 10 códigos; só o 902 (carbono) começa em 01/12/2024 na tabela e 11/12/2024 no arquivo. |
| 4.3.16 | OPER_COM_SUSPENSAO | 4.3.16 v1.19, 17/09/2026 (REDATA) | tabela mais nova | Código novo 322 (REDATA, desde 15/09/2026, Art. 11-C da Lei 11.196/2005 pela Lei 15.504/2026). |
| 4.3.17 | OUTROS_ALIQ_DIFER | 4.3.17 atualizada em 18/06/2024 (REIQ) | equivalente | Mesmos códigos e alíquotas nas linhas comuns; o arquivo tem a mais os créditos 401 a 419. |
| 4.3.18 | COD_AJUS_BASE_CALCULO_CONTRIB | 4.3.18 v1.02 | equivalente | Mesmos 7 códigos; a tabela não tem a coluna OBRIGA_DET. |
| 5.1.1 | COD_ATIVIDADE | 5.1.1 para períodos a partir de 01/09/2018 (planilha 511-CD_1) | subconjunto mais antigo | A planilha tem 275 códigos, todos no arquivo, com as mesmas alíquotas vigentes. O arquivo é superior: guarda o histórico desde 2011 e os códigos de NCM de 8 dígitos. |
| 7.1.1 | RECEITAS | CPIADE_1 (sem data) | equivalente com diferenças | Mesmos 89 códigos de 5 caracteres; datas de início e fim diferem em 67 (ver diferenças). |
| 7.1.2 | DEDUÇÕES | TABELA_1_5 (sem data) | equivalente com diferenças | Mesmos 75 códigos de 5 caracteres; datas diferem em 70. |
| 7.1.3 | RECEITAS_GRUPO100 a 600 | TABELA_1 (28/08/2017); TABELA_1_1 a _4 (10/02/2014); CPIADE_1_1 (25/07/2023) | equivalente com diferenças | Grupos 100 e 600 iguais; grupos 200, 300, 400 e 500 trazem códigos de 2013 a mais. O grupo 700 de receitas não tem planilha. |
| 7.1.4 | DEDUCOES_GRUPO000 a 800 | TABELA_1_6 a _13 e CPIADE_1_2 (grupo 100 atualizada em 22/05/2014) | equivalente com diferenças | Mesmos códigos de 2014 em diante; planilhas trazem 2 códigos a mais no grupo 200 e 9 no grupo 700 (até 31/12/2013). |

Três tabelas do Portal estão **à frente dos arquivos** (4.3.11 v1.34 e 4.3.13 v1.36, de 16/09/2026, e 4.3.16 v1.19, de 17/09/2026): gasolina, querosene, biodiesel e etanol de 2026, o código 226 da 4.3.13 (etanol combustível, de 10/09 a 09/10/2026) e o código 322 da 4.3.16 (REDATA, desde 15/09/2026). Hoje (11/10/2026) as janelas de gasolina e etanol já terminaram e as alíquotas normais voltaram em 10/10/2026. A diferença linha a linha está na aba "Diferenças das tabelas" do anexo do documento 44.

## Correções a este documento

| Item | Linhas do doc 43 | Correção | Prioridade |
|---|---|---|---|
| Fonte das tabelas e limite da leitura (P43-01) | 56, 374, 595, 605, 629 (V5) | Reescrever: o Guia Prático v1.35 (18/06/2021) e as tabelas do Portal do SPED chegaram; o mapeamento arquivo para tabela está fechado em mapa_arquivos. Fechar P43-01 (restam sem número: ANP, BENEFICIOS_FISCAIS, CFOP_DEVOLUCAO, CFOP_DEVOLUCAO_VENDA, CFOP_RECEITA, CONSUMO_TELECOM, DATA_LIMITE_ENTREGA, IND_DED_DIV, MENSAGENS_USUARIO, PRAZO_DECADENCIA, TIPO_CT). Colocar a lista oito mais um de 374 como: 4.3.10 PROD_MONO_ALIQ_DIFER, 4.3.11 PROD_MONO_ALIQ_UNID, 4.3.12 PROD_ST, 4.3.13 PROD_ALIQ_ZERO, 4.3.14 OPER_COM_ISENCAO, 4.3.15 OPER_SEM_INCIDENCIA, 4.3.16 OPER_COM_SUSPENSAO, 4.3.17 OUTROS_ALIQ_DIFER e, em OPER_CREDITO, 4.3.9 ALIQ_AGRO_FRIGO. | alta |
| COD_DETALHAM vira detalhamento da CPRB, não do ajuste de base | 103, 206, 436 | COD_DETALHAM é a Tabela 5.1.2 do Guia (Código de Detalhamento da CPRB), usada no registro filho P110 para detalhar valores agregados do P100. Renomear o domínio para tipo_detalhamento_cprb (5 linhas: documento fiscal, item/produto/serviço, NCM, cliente, outros critérios) e tirar a referência dele de Cad_Ajuste_Base_Pis_Cofins. O detalhamento do ajuste de base (M215/M615) é livre: NUM_DOC e DESCR_AJ_BC. | alta |
| Alíquotas P e R de OUTROS_ALIQ_DIFER (P43-02) | 133, 140, 606 | Hipótese refutada. P = alíquota da contribuição devida na venda (colunas Contribuição PIS e Cofins da 4.3.17); R = alíquota do crédito (colunas Crédito PIS e Cofins). Prova: código 901 só tem crédito (1,2375 e 5,7), como o Guia descreve a subcontratação de transporte; 913 só tem contribuição. Trocar Perfil_Aliquota {unico, p, r} por {unico, contribuicao, credito}. | alta |
| IND_ATIV (P43-02) | 111, 420 | Descrição: 01 instituições financeiras e assemelhadas; 02 seguradoras; 03 previdência complementar; 04 capitalização; 05 planos de assistência a saúde; 06 mais de uma das anteriores. O domínio indicador_atividade_receita_deducao deve guardar as seis descrições. Cada receita ou dedução só vale se o IND_ATIV do I010 está na lista da linha. | alta |
| IND_AJUSTE, TIPO_DEDUC, IND_OUTROS (P43-02) | 225, 420 | TIPO_DEDUC: G = dedução geral (I100 campo 04) e E = específica (campo 05), sem exceção nos 80 códigos. IND_AJUSTE: P e N lidos como ajuste positivo e negativo (as 37 linhas N são as classes xx98 Ajustes Negativos); inferência, não está escrito. IND_OUTROS: S marca as linhas "Outros/Outras"; inferência. | alta |
| OBRIGA_DET (P43-02) | 206, 606 | Continua sem definição. Só o código 21 passa de N para S (01/04/2019). Leitura provável: obriga a informar o detalhamento (NUM_DOC e DESCR_AJ_BC) no M215/M615. Manter como pendência, e o campo sem o texto sobre tipo de detalhamento. | alta |
| Grupos 100 e 700 de GRUPOS_RECEITAS com a mesma descrição (defeito de arquivo) | 420, 632 (V8) | Não é defeito: o Guia diz que o IND_ATIV 01 validava o grupo 700 de receitas até 31/12/2013 (opcional) e que, a partir de 01/01/2014, as receitas do sistema financeiro passam para o grupo 100 (7.1.1 e 7.1.2). O 700 é a codificação antiga do 100. | alta |
| Grupo 800 de deduções fora de GRUPOS_DEDUCOES | 411, 632 (V8) | Defeito do arquivo, confirmado: a planilha 7.1.4 (CPIADE_1_2) traz o grupo 800 (securitização de créditos), que o Guia v1.35 também não lista; D0804 vale desde 04/08/2022. A numeração dos grupos é diferente entre receitas e deduções (receitas 600 = securitização; deduções 600 = planos de saúde, 700 = cooperativas de crédito, 800 = securitização). | alta |
| Vigências das tabelas 7.1.x | 418 | As planilhas dizem 31/12/2013 (início 01/08/2013, transmissão opcional); o arquivo diz 31/01/2014 em 24 receitas e 8 deduções, com início em 01/01/2013 ou 01/01/2014. Guardar a vigência do arquivo e registrar a divergência. Os códigos de detalhe de 08/2013 a 12/2013 que só existem nas planilhas (10 de receita e 11 de dedução) não entram na carga, pois o arquivo não os traz. | média |
| Bebidas frias em 4.3.10 ou 4.3.11 (V7) | 374, 398, 631 | Os dois estão certos, por período: até 30/04/2015 a pauta por unidade de medida (grupos 800 e 900, código de 6 dígitos = código de 3 dígitos + grupo de 3) está na 4.3.11; desde 01/05/2015 a tributação é em percentual sobre a receita (arts. 24 a 28 da Lei 13.097/2015) na 4.3.10, e a 4.3.11 só guarda a pauta mínima 611 a 681. O Guia M410 fala em NAT_REC de tamanho 003; o arquivo traz 6 dígitos. | média |
| Códigos 401 a 409 de PROD_ST (4.3.12) | 133, 374 | Na tabela 4.3.12 os códigos 401 a 409 são remissão para a 4.3.10 (404, 405, 406, 409) ou a 4.3.11 (401, 402, 403, 407, 408). As alíquotas de 401 e 402 do arquivo repetem as de 112 e 113 da 4.3.11. Não carregar alíquota própria para 401 a 409: guardar só a remissão. | média |
| Óleo diesel sem linha vigente (P43-08) | 399, 612 | Parte errada: a tabela 4.3.11 v1.34 de 16/09/2026 também acaba o óleo diesel 102 em 31/05/2026. A lacuna é da fonte oficial, não do arquivo. Rebaixar a ação: perguntar a Receita ou ao contador qual alíquota vale desde 01/06/2026. Para DATA_LIMITE_ENTREGA a pendência segue igual. | alta |
| Tabelas mais novas que os arquivos | 399, 612, D-N80 | Três tabelas do Portal (4.3.11 v1.34 de 16/09/2026, 4.3.13 v1.36 de 16/09/2026, 4.3.16 v1.19 de 17/09/2026) estão a frente dos arquivos: gasolina, querosene, biodiesel e etanol de 2026, etanol 226 e REDATA 322. Na rotina D-N80, comparar também a versão da tabela (1.36 no caso da 4.3.13; o Guia recebido é o 1.35) e não só a versão do cabeçalho do arquivo (versão=50); os números não coincidem. | alta |
| CFOP_CREDITO e Cad_CFOP_Uso_Efd_Contribuicoes (D-N76, P43-14) | 78, 426, 618, 647 | A planilha Tabela I confirma CFOP_CREDITO (89 CFOP, mesma base). CFOP_DEVOLUCAO_VENDA (16) = 14 CFOP do grupo 12 mais 1553 e 2553; CFOP_DEVOLUCAO (43) não cruza com a planilha. O efeito da devolução de venda depende do regime: no não cumulativo gera crédito (NAT_BC_CRE 12), no cumulativo reduz a base (M215/M615 com os códigos 01 e 02 da 4.3.18 quando de período anterior; CST 99 no documento). Ajustar a descrição do uso devolucao_venda (hoje "reduz receita"). P43-14 não muda: a planilha não tem indicadores. | alta |
| Faixas de consumo (Cad_Faixa_Consumo_Sped) | 171 a 194 | Números do Guia: energia 4.4.5, água 4.4.2 e gás 4.4.3 (campo COD_CONS do C600); CONSUMO_TELECOM não tem número no texto (4.4.4 só por exclusão). CLASSIFICACAO_ITEM é a 4.4.1 (Ato COTEPE 09/2008, D601/D605). | média |
| Pendência P43-02 sobre P e R, IND_ATIV e TIPO_DEDUC | 606 | Reduzir a pendência a: OBRIGA_DET (sem definição), expansão literal das letras P/R, P/N e S/N (só por inferência) e a confirmação do contador. | média |
| P43-05 (tb1316, tb14, tb13957) | 609 | Sem mudança: o material novo só trata EFD-Contribuições. | baixa |
| Versões de leiaute (VERSOES_LEIAUTE) e Numero_Leiaute | 481 a 491 (seção 7.3), 301 a 317 | A coluna VERSÃO do arquivo (101 em todas as linhas) não é a versão do leiaute. O Guia 3.1.1 traz: 001 = 1.00 (ADE Cofis 31/2010); 002 = 1.01 e depois 2.00; 003 = 2.01A; 004 = 3.0.0; 005 = 3.1.0; 006 = 3.2.0. Carregar Numero_Leiaute do Guia e tratar o 101 como dado do arquivo sem significado conferido. O arquivo começa em 002 (falta o 001) e o 002 começa em 01/01/2011, enquanto o Guia diz 01/04/2011. | média |
| Domínios de natureza de ação judicial, processo administrativo e dispensa de entrega | 102 a 110 (seção 4.3) | Fonte: registros 1010 (campo 05), 1020 (campo 05) e 0120 (campo 03). O Guia v1.35 lista 1010: 01 a 09 e 99 (os códigos 12 a 17 e 19 entram com o leiaute 006, de 01/2020, segundo o item 3.1.1, mas o arquivo os começa em 01/01/2017); 1020: 01 a 06 e 99; 0120: 01 a 07 e 99. O arquivo tem 101, 102 e 103 (Perse, desde 01/05/2024) em MOTIVO_DISPENSA_ENTREGA, que são posteriores ao Guia. | média |
| CS_APUR (código 70) | 122 | A tabela 4.3.5 nova e o arquivo trazem o código 70 (RET), que o Guia v1.35 não lista. Carregar como está nos dois e anotar que é posterior ao Guia. | baixa |

## Entidades propostas que mudam

| Entidade | Ação | O que muda | Decisões afetadas |
|---|---|---|---|
| Cad_Natureza_Receita_Pis_Cofins_Aliquota | alterar | Perfil_Aliquota: enumeração {unico, contribuicao, credito} no lugar de {unico, p, r}. contribuição = colunas P (alíquota devida) e crédito = colunas R (alíquota do crédito) de OUTROS_ALIQ_DIFER. Campo novo Tabela_Guia (texto): 4.3.9 a 4.3.17, para saber de que tabela a linha veio. Campo novo Nota_Aplicacao (texto, opcional): nota de rodapé da tabela, por exemplo "no período de alíquota zero usar CST 06 e o código 226 da 4.3.13". Regra de carga: PROD_ST 401 a 409 são remissão a 4.3.10 e 4.3.11; não carregar alíquota própria (as de 401 e 402 repetem 112 e 113 da 4.3.11). | D-N75 |
| Cad_Natureza_Receita_Pis_Cofins | alterar | Código (até 6): para bebidas frias da 4.3.11, o código é o de 3 dígitos (800 e 900) mais o grupo de 3 dígitos da linha (930 e 001 = 930001). Campo novo opcional Grupo_Pauta (3): guarda o grupo quando o código tem 6 dígitos. | D-N75 |
| Cad_CFOP_Uso_Efd_Contribuicoes | alterar | Uso devolucao_venda: o efeito depende do regime (não cumulativo gera crédito, base 12; cumulativo reduz a base). Trocar a descrição "reduz receita". Campo novo Observacao_Uso (texto, opcional): para 1922 e 2922, o crédito só existe se a mercadoria já foi fabricada. Sem campo de indicadores de CFOP: a planilha não os traz (P43-14 segue aberta). | D-N76 |
| Cad_Ajuste_Base_Pis_Cofins | alterar | Exige_Detalhamento: marcar o significado como não confirmado (provável: obriga NUM_DOC e DESCR_AJ_BC no M215/M615) e tirar a referência ao domínio de detalhamento. A carga mantém as duas versões do código 21 (OBRIGA_DET N e depois S, 01/04/2019). | D-N74 |
| Cad_Classe_Sistema (domínios) | alterar | tipo_detalhamento_ajuste_pis_cofins passa a tipo_detalhamento_cprb (P110, Tabela 5.1.2); o código 00000999 do Guia fica diferente do 00000005 do arquivo. indicador_atividade_receita_deducao: as seis linhas ganham a descrição do Guia (01 a 06). Contagem em D-N74 continua 14 domínios novos. | D-N74 |
| Cad_Receita_Deducao_Pis_Cofins | alterar | Indicador_Ajuste vira enumeração {positivo, negativo}, com Situacao_Dado provisório (inferência das classes xx98 e xx99). Tipo_Deducao confirmado {geral, especifica} (G e E; I100 campos 04 e 05). Aceita_Descricao_Livre (IND_OUTROS) fica como inferência. Campo novo opcional Codigo_Atual (referência ao próprio cadastro): receitas do grupo 700 (sistema financeiro, até 31/12/2013) apontam o equivalente do grupo 100 (desde 01/01/2014). Nota de carga: os códigos de detalhe de 08/2013 a 12/2013 que só estão nas planilhas não entram. | D-N74, D-N79 |
| Cad_Receita_Deducao_Pis_Cofins_Atividade | sem alteração de campos | Sem mudança de campos. | D-N79 |
| Cad_Tabela_Oficial | alterar | Campo novo Numero_Tabela_Guia (texto): 4.3.13, 7.1.3 (grupo 100), "sem número". Campo novo Versao_Guia (texto, opcional): a versão da tabela, por exemplo "1.36" (não é a versão do Guia, que é a 1.35), e a data de publicação em Data_Publicacao_Guia (data, opcional). Os campos Familia_Fonte, Codigo_Tabela_Fonte e Colunas_Esperadas da proposta do doc 43 ficam. | D-N73, D-N80 |
| Mov_Carga_Tabela_Oficial | alterar | Campo novo Origem_Material (enumeração {arquivo_sped, documento_portal, planilha_portal}). A conferência de versão do cabeçalho não vale para .doc e .xls do Portal; a carga deles é manual e a conferência é pela data e versão do título. | D-N80 |
| Cad_Obrigacao_Leiaute_Versao | alterar | Numero_Leiaute vem do Guia 3.1.1 (1.00, 1.01, 2.00, 2.01A, 3.0.0, 3.1.0, 3.2.0), e não da coluna VERSÃO do arquivo (101 em todas as linhas). A identidade passa a ser Codigo_Versao_Arquivo mais Numero_Leiaute, porque o código 002 tem duas versões (1.01 e 2.00). Campo novo opcional Ato_Instituidor (texto): ADE Cofis 31/2010, 34/2010, 20/2012, 82/2018. | D-N77 |
| Cad_Cprb_Atividade | alterar | ID_Classificacao: 318 códigos de COD_ATIVIDADE (612 linhas) são a posição de 4 dígitos completada com 0000 (02030000 = 02.03); a carga deve ligar esses a classificação de 4 dígitos, e não a um subitem de 8 dígitos. | D-N78 |
| Cad_Faixa_Consumo_Sped | sem alteração de campos | Sem mudança de campos. | D-N79 |

## CFOP e DACON

A planilha "Tabela I" confirma `CFOP_CREDITO` (89 CFOP em 5 grupos, **idêntico** ao arquivo, inclusive a base de cada um); `CFOP_DEVOLUCAO_VENDA` (16) é igual a 14 CFOP do grupo 12 mais 1553 e 2553; `CFOP_DEVOLUCAO` (43) não cruza com a planilha. Regra do Guia (M105 e M505): o PVA só considera CST 50 a 66 e CFOP da tabela, e não consolida transferências entre estabelecimentos; o CFOP 1922 e 2922 só gera crédito se a mercadoria já foi fabricada. Na correlação DACON × EFD, as linhas 01 a 13 dos créditos têm a mesma numeração e os mesmos nomes de `NAT_BC_CRE`; só serve à migração de histórico, e não cria entidade.

## Dúvidas novas

| Dúvida | Por quê | Quem responde |
|---|---|---|
| O que é OBRIGA_DET? | Não está definido no Guia nem na tabela 4.3.18 nova; só o código 21 e S desde 01/04/2019. | Receita Federal ou contador |
| Qual é a expansão literal das letras P e R (OUTROS_ALIQ_DIFER), P e N (IND_AJUSTE) e S e N (IND_OUTROS)? | As leituras contribuição/crédito, positivo/negativo e linha-outros são inferências dos dados; nenhuma fonte escreve a letra. | Receita Federal (PVA) ou contador |
| Qual alíquota do óleo diesel (4.3.11, código 102) vale desde 01/06/2026? | A tabela de 16/09/2026 acaba em 31/05/2026 e as correntes 106 seguem a 62,61 e 288,89. | Contador ou Receita |
| As janelas de 2026 (gasolina e etanol de 10/09 a 09/10/2026, querosene até 31/07/2026, biodiesel até 31/07/2026) são finais? | A tabela as traz como linhas fechadas; hoje (11/10/2026) as de gasolina e etanol já acabaram; o biodiesel 110 tem fim digitado como 31/07/2028. | Contador |
| Qual dos dois está certo na 4.3.10: código 004 (fim 30/04/2015 ou 31/10/2017), 150 a 152 em 2022 (fim 31/03/2022 ou 31/12/2022; o 150 do arquivo termina em 01/03/2022) e o 152 duplicado até 31/12/2027? | Tabela e arquivo divergem; a tabela 4.3.10 não traz data nem versão no título. | Contador |
| Qual é o COD_DETALHAM correto para "outros critérios": 00000999 (Guia) ou 00000005 (arquivo)? | Divergência entre o Guia v1.35 e o arquivo v1. | Receita Federal |
| Qual é o significado da coluna VERSÃO (101) de VERSOES_LEIAUTE? | Todas as linhas trazem 101, o Guia traz 1.00 a 3.2.0. | Receita Federal |
| O que fazer com as linhas de OUTROS_ALIQ_DIFER que a tabela 4.3.17 não traz (créditos 401 a 419, 903 a 909 com P igual a R)? | A tabela nova de 18/06/2024 omite o que o arquivo guarda; o arquivo divide o 901 em 22/12/2022. | Contador |
| O código 25 (ICMS destacado em documento fiscal complementar) segue vigente? | A tabela 4.3.8 nova o traz com início 01/12/2011 e sem fim; o arquivo o encerra em 31/12/2018 e inicia em 01/01/2002; o código 25 também existe na 4.3.18 (COD_AJUS_BASE_CALCULO_CONTRIB). | Receita Federal |
| R0304020 (planilha) e R0306020 (arquivo) e R0403040 e R0403050 são o mesmo código? | Mesmo texto com número diferente nas planilhas 7.1.3 e no arquivo; R0301010 com data em número de série; R0401010, R0402010 e R0404010 com fim 31/12/2103. | Receita Federal |
| Qual vigência vale para 7.1.1 e 7.1.2: 01/08/2013 a 31/12/2013 (planilha) ou 01/01/2013 e 31/01/2014 (arquivo)? | Divergência de 24 receitas e 8 deduções. | Contador |
| Onde o PVA usa CFOP_DEVOLUCAO (43) e CFOP_DEVOLUCAO_VENDA (16)? | Não estão no Guia nem na planilha de CFOP; só CFOP_CREDITO tem fonte. | Receita Federal (PVA) |
| IND_DED_DIV, TIPO_CT e CONSUMO_TELECOM tem número de tabela no Guia? | Não citados no texto do Guia v1.35 pesquisado; 4.4.4 só por exclusão. | Receita Federal |
| Até quando os arquivos do Portal ficam atrás das tabelas em .doc e .xls? | As tabelas 4.3.11, 4.3.13 e 4.3.16 (16 e 17/09/2026) já trazem dados que os arquivos não têm. | Alberto (fonte da carga) |
| A carga deve aceitar o CS_APUR 70 (RET), posterior ao Guia v1.35? | Está na tabela 4.3.5 nova e no arquivo. | Contador |
| O NAT_REC de tamanho 003 no M410 do Guia convive com os códigos de 6 dígitos de bebidas frias? | O Guia v1.35 diz 003; o arquivo traz 6 dígitos para os grupos 800 e 900, encerrados em 30/04/2015. | Receita Federal |
| P43-05: onde se aplicam tb1316, tb14 e tb13957? | O material novo é só da EFD-Contribuições. | Guia da EFD ICMS/IPI |

Decisão no documento 44: **D-N90** (aceitar as correções e carregar manualmente as três tabelas à frente dos arquivos). As D-N73 a D-N80 continuam como estão, com os ajustes acima.

# 1. Resumo

Os 86 arquivos têm 30.469 linhas, das quais 20.207 valem hoje (06/10/2026), 10.261 já terminaram e 1 só começa em 01/01/2027 (leiaute 1.20 da EFD ICMS/IPI). Li todos, juntei os registros partidos em mais de uma linha (descrições de CFOP com quebra interna) e contei cada tabela. Para cada uma, decidi entre cinco destinos.

Das 86 tabelas, **6 já estão cobertas** pelo dicionário, **20 carregam em catálogo que já existe**, **13 viram entrada em tabela genérica** (novos domínios de `Cad_Classe_Sistema`), **40 pedem entidade nova** e **7 são ignoradas** por obsoletas, duplicadas ou vazias. As 40 tabelas de entidade nova alimentam **11 entidades novas** (21 arquivos de receitas e deduções e 5 de NCM com alíquota têm cada grupo a mesma estrutura; a tb1875 vai para a `Cad_Icms_Codigo_Ajuste`, proposta do documento 33; a `Cad_Obrigacao_Decadencia` nasce da regra, não de um arquivo). Há ainda 13 alterações pequenas em entidades que já existem.

O dicionário já tem o mecanismo certo para a carga (`Cad_Tabela_Oficial` e `Mov_Carga_Tabela_Oficial`) e o catálogo certo para as listas pequenas (`Cad_Classe_Sistema`, que já tem vigência e aceita domínio novo sem tabela nova). Por isso a proposta **não cria** a `Cad_Efd_Tabela_Externa` com itens genéricos: ela repetiria os dois.

Cinco achados pesam mais que o resto:

1. **CFOP e municípios vêm em duas versões**, uma em cada SPED, e as do ICMS/IPI são as mais novas (CFOP versão 14 contra 9; municípios 20 contra 10). As listas vigentes de CFOP são iguais (619 códigos) e as de municípios diferem em um código (9999998, só na do ICMS/IPI). Carrega-se só a do ICMS/IPI. Isso resolve o item "tabela de CFOP" da seção 5 do documento 38, no que toca a códigos, textos e vigência.
2. **A identidade da natureza da receita não fecha.** `Cad_Natureza_Receita_Pis_Cofins` usa o código de 3 dígitos como identidade, mas o mesmo código existe em até nove tabelas com sentidos diferentes (93 dos 574 códigos distintos repetem), e há 307 códigos de 6 dígitos de bebidas frias (1.139 linhas). A identidade tem de ser grupo mais código.
3. **O CST do ICMS do arquivo tem 3 dígitos (origem mais CST) e colide com o CSOSN.** Os CSOSN 300, 400 e 500 aparecem encerrados em 31/12/2012, e os mesmos números voltam em 01/01/2013 como origem 3, 4 e 5 com CST 00. O documento 10 os lista como vigentes. É preciso separar origem e CST.
4. **A data limite de entrega da EFD-Contribuições** tem 150 competências (01/2014 a 06/2026), e a regra dos dez dias úteis do segundo mês seguinte, com feriados bancários, acerta 147. As 3 exceções (02, 03 e 04/2020) têm a mesma data e parecem prorrogação. O `DT_FIM` de cada linha é o 31/12 do quinto ano depois do ano do prazo em 150 de 150: é o horizonte de decadência, não o fim da vigência do prazo.
5. **Dois arquivos parecem atrasados.** Não há competência de entrega depois de 06/2026, e o óleo diesel por unidade (código 102) não tem linha vigente depois de 31/05/2026 (situação de 06/10/2026).

Para PIS/Cofins, as fontes divergem sobre o fim da EFD-Contribuições (documento 10: extinção em 2027; documento 32, com fonte secundária: fim da apuração em 31/12/2026; dicionário: fim esperado por volta de 2033, sem confirmação). Não inventei data. A proposta é manter todas as tabelas, com a vigência que o arquivo traz, e parar de atualizar só quando a Receita parar de publicar (seção 10).

Proponho 8 decisões, **D-N73 a D-N80**, na seção 13.

# 2. Fontes lidas

Cada arquivo é um texto com campos separados por `|`, uma linha de cabeçalho com a versão (`versão=N` e as colunas) e datas em `ddmmaaaa`; `DT_FIM` vazio significa sem fim. A tabela agrupa os 86 arquivos pelo grupo do nome. "Vigentes" são as linhas com início até hoje e sem fim ou com fim a partir de hoje.

| Família | Grupo | Arquivos | Linhas | Vigentes | Versões | Menor DT_INI | Maior DT_FIM | O que contém |
|---|---|---|---|---|---|---|---|---|
| EFD ICMS/IPI | TB | 10 | 8.519 | 7.311 | 1 a 21 | 01/01/2009 | 31/12/2026 | CEST, CFOP, município, versões de leiaute, ajustes, receita, obrigação, usina, ECF |
| EFD-Contribuições | RECEITAS_DEDUCOES | 22 | 681 | 628 | 1 a 8 | 01/01/2011 | 01/07/2017 | Receitas, exclusões e deduções por tipo de pessoa jurídica, em quatro níveis |
| EFD-Contribuições | GLOBAL | 23 | 8.496 | 8.315 | 1 a 49 | 01/01/2008 | 31/12/2031 | Tabelas gerais: UF, município, país, CFOP, serviço, modelo, ANP, prazos, leiaute, motivos |
| EFD-Contribuições | OPER_CONTRIB | 11 | 11.949 | 3.238 | 1 a 50 | 01/01/2009 | 31/12/2027 | NCM por tratamento (7 tabelas e "outras"), atividade da CPRB, detalhamento, CFOP de receita |
| EFD-Contribuições | CONSUMO | 5 | 199 | 194 | 1 a 2 | 01/01/2009 | 31/12/2009 | Faixas e classes de consumo de energia, água, gás e comunicação; classificação de item |
| EFD-Contribuições | CST | 4 | 278 | 220 | 1 a 6 | 01/01/2006 | 31/07/2013 | CST de ICMS, IPI, PIS e Cofins |
| EFD-Contribuições | OPER_CREDITO | 4 | 186 | 168 | 2 a 26 | 01/01/2009 | 31/12/2023 | Crédito presumido da agroindústria e CFOP de crédito e devolução |
| EFD-Contribuições | APURACAO | 5 | 87 | 75 | 1 a 7 | 01/01/2002 | 31/03/2023 | Base, tipo e origem de crédito e de ajuste; contribuição apurada |
| EFD-Contribuições | VISAO_DCTF | 2 | 74 | 58 | 4 a 5 | 01/01/2014 | 31/12/2018 | Códigos de receita de PIS/Pasep e Cofins na DCTF |
| Total |  | 86 | 30.469 | 20.207 |  |  |  |  |

A lista completa, com a versão, as colunas, as linhas e as datas de cada uma das 86, está na aba Inventário do anexo.

Outras fontes usadas:

| Fonte | Uso |
|---|---|
| `model.json` (543 entidades) e documento 01 | Conferir o que o dicionário já guarda e os nomes citados |
| Documento 10, seção 18 e `Cad_Cprb_Atividade`, `Cad_Cst`, `Cad_Natureza_Receita_Pis_Cofins` | Natureza da receita, CST, CPRB, vigência de PIS/Cofins |
| Documentos 32, 33, 36 e 38 | Calendário de 2026 e 2027, `Cad_Icms_Codigo_Ajuste` e `Cad_Icms_Obrigacao_Recolher` (propostas), pendências |
| Documento 37 e o resumo da EFD ICMS/IPI | Tabelas externas do Guia da EFD ICMS/IPI (5.1.1, 5.4 e outras) e registros legados C300 a C495 |
| Anexo A da NFS-e nacional (10/12/2025) e lista nacional de serviços (22/01/2026) | Conferir municípios, países e a lista de serviços |

**Limite da leitura.** O documento 37 trata do Guia da EFD ICMS/IPI. Não há manual da EFD-Contribuições entre as fontes, então os números das tabelas do Guia (4.3.x) de cada arquivo são deduzidos pelo conteúdo, e o significado de alguns indicadores (P e R, IND_AJUSTE, IND_ATIV) fica como pendência (P43-01 e P43-02).

**Formato real dos arquivos.** (a) 85 estão em Windows-1252 e só `CFOP_RECEITA` (vazio) em UTF-8; não é ISO-8859-1 estrito, porque aparecem aspas e travessões tipográficos (bytes 0x92, 0x93, 0x94 e 0x96). (b) As descrições do CFOP têm quebra de linha interna: são 637 registros em mais linhas no Contribuições e 648 na tb15236; o leitor junta as linhas contando os separadores. (c) O cabeçalho varia: `versão=N COL1, COL2`, `versão=N cod|desc|dt_ini|dt_fin - Título`, só `versão=N` (tb19, tb131 e tb14) e, em `CONSUMO_TELECOM`, nenhum cabeçalho. (d) Três nomes de arquivo trazem versão diferente da do cabeçalho (energia, enquadramento do IPI, telecom).

**Conferência.** Um script (`valida43.py`) confirmou que todo nome de entidade e de campo existente citado aqui consta do `model.json`; que as entidades dos documentos 33 a 36 que não constam (por exemplo `Cad_Icms_Codigo_Ajuste`) são propostas ainda não consolidadas; que as contagens por decisão do texto são as da planilha; e que o texto não deixa pendência ou decisão sem número.

# 3. O que o dicionário já guarda e o que falta

A tabela diz, por grupo, o que já existe, o que falta e como as tabelas se dividem pelas cinco decisões (J = já coberta, C = carregar em catálogo existente, G = entrada em tabela genérica, E = entidade nova, I = ignorar).

| Grupo | Arquivos | O que já existe no dicionário | O que falta | Decisões |
|---|---|---|---|---|
| Contrib. / APURACAO | 5 | Os domínios `contribuicao_social_pis_cofins` (4.3.5), `tipo_credito_pis_cofins` (4.3.6) e `base_credito_pis_cofins` (4.3.7) em `Cad_Classe_Sistema` | Origem do ajuste (domínio novo) e o ajuste de base com a marca de detalhamento obrigatório | C 3 G 1 E 1 |
| Contrib. / CONSUMO | 5 | Nada | Faixa de consumo com limite, unidade e marca de consolidação; classificação de item | G 1 E 4 |
| Contrib. / CST | 4 | `Cad_Cst` com `ID_Imposto`, `Familia` e `Aplicacao`; domínio `origem_mercadoria` | Separar origem e CST no ICMS; tratar CSOSN 300, 400 e 500 | C 4 |
| Contrib. / GLOBAL | 23 | `Cad_Estado`, `Cad_Municipio`, `Cad_Pais`, `Cad_CFOP`, `Cad_Servico_Tributacao_Nacional`, `Cad_Codigo_Receita` e `_Raiz`, `Cad_Obrigacao_Acessoria`, `Cad_Regra_Vencimento`, domínios `modelo_documento_fiscal` e `enquadramento_ipi` | Produto ANP, benefício de PIS/Cofins, prazo de entrega, versão de leiaute e cinco listas pequenas | J 5 C 4 G 5 E 4 I 5 |
| Contrib. / OPER_CONTRIB | 11 | `Cad_Natureza_Receita_Pis_Cofins` com `_Cst` e `_Classificacao` (NCM de qualquer nível), `Cad_Cprb_Atividade`, `Cad_NCM_Ex_Tipi` | Alíquotas, NCM excluído e Ex da TIPI na natureza; identidade grupo mais código; NCM da CPRB como código | C 5 G 1 E 4 I 1 |
| Contrib. / OPER_CREDITO | 4 | `Cad_CFOP` com `Indicador_Devolucao` e `Indicador_Anulacao` | O uso de cada CFOP no Contribuições e as alíquotas do crédito presumido | E 4 |
| Contrib. / RECEITAS_DEDUCOES | 22 | Nada | Hierarquia de receitas e deduções com atividade, ajuste e tipo | G 1 E 21 |
| Contrib. / VISAO_DCTF | 2 | `Cad_Codigo_Receita` com `Periodicidade` e `Origem_Declaracao` | Só a carga | C 2 |
| ICMS/IPI / TB | 10 | `Cad_CFOP`, `Cad_Cest`, `Cad_Municipio`; `Cad_Icms_Codigo_Ajuste` e `Cad_Icms_Obrigacao_Recolher` como propostas do documento 33 | Versão de leiaute, listas de receita, obrigação, tipo de crédito e usina; ajuste dos códigos do documento 33 | J 1 C 2 G 4 E 2 I 1 |

**Já está resolvido no documento 38.** O item "tabela de CFOP" (seção 5, junto de PL_010g, schema do evento 110300 e IT 2026.001) fica resolvido em códigos, textos e vigência pela tb15236; os indicadores de `Cad_CFOP` continuam pedindo a tabela do Portal da NF-e (P43-14). O item das tabelas externas da EFD ICMS/IPI fica resolvido só em parte: tb1875 traz os códigos genéricos de ajuste (5.1.1) e tb19 a lista de obrigações; faltam os códigos de cada UF e as demais tabelas (P43-04).

# 4. Abordagem proposta

## 4.1 Três caminhos

| Caminho | Como seria | Problema | Veredito |
|---|---|---|---|
| A. Genérica: `Cad_Efd_Tabela_Externa` e `Cad_Efd_Tabela_Externa_Item` | Uma entidade de cabeçalho por tabela e uma de itens com código, descrição, vigência e colunas extras em texto | Repete `Cad_Tabela_Oficial` (cabeçalho e carga) e `Cad_Classe_Sistema` (itens com vigência). As colunas extras em texto perdem tipo e chave estrangeira (NCM, alíquota, CST) | Não |
| B. Uma entidade para cada tabela | 86 entidades | Explode o dicionário: 48 das 86 têm só código, descrição e as duas datas | Não |
| C. Híbrida | Cabeçalho e carga em `Cad_Tabela_Oficial`; lista simples em `Cad_Classe_Sistema`; catálogo que já existe recebe as linhas; entidade específica só onde há atributo, relação ou hierarquia | Exige 14 domínios novos, 11 entidades novas e 13 alterações pequenas | **Sim** |

Das 86 tabelas, 48 têm só quatro colunas (código, descrição e as duas datas); as outras 38 trazem colunas extras (NCM, alíquota, grupo, periodicidade, indicador). As colunas de cada arquivo estão na aba Inventário.

## 4.2 Cabeçalho e carga

Cada uma das 86 tabelas ganha uma entrada em `Cad_Tabela_Oficial` (código estável como `sped_contrib_cfop_credito` ou `sped_icms_tb15236`, órgão Receita Federal, `Forma_Atualizacao` ambas, fonte o portal do SPED). Cada carga é uma linha de `Mov_Carga_Tabela_Oficial`, com as contagens de incluídos, alterados e encerrados que o mecanismo já tem. A versão do cabeçalho, o hash, a codificação e as colunas esperadas são campos novos propostos (seção 4.5).

## 4.3 Domínios de `Cad_Classe_Sistema`

Catorze domínios novos, cada um uma lista de código, descrição e vigência. Os valores entram como linhas do domínio, sem tabela nova, e cada linha guarda `ID_Tabela_Oficial` para a carga reconhecer o que é dela e o que o usuário criou.

| Domínio novo | Origem | Linhas no arquivo | Observação |
|---|---|---|---|
| origem_ajuste_pis_cofins | AJ_CONTRIB_CRED | 13 | Origem do ajuste de contribuição ou de crédito. |
| tipo_detalhamento_ajuste_pis_cofins | COD_DETALHAM | 5 | Por documento, por item, por NCM e outros. |
| motivo_dispensa_entrega_efd | MOTIVO_DISPENSA_ENTREGA | 11 | Motivo de dispensa de entrega da escrituração. |
| natureza_acao_judicial_efd | NATUREZA_ACAO_JUDICIAL | 17 |  |
| natureza_processo_administrativo_efd | NATUREZA_PROCESSO_ADM | 7 |  |
| tipo_conhecimento_embarque | TIPO_CT | 22 | AWB, MAWB e outros. |
| tipo_cte_efd | TIPO_CT_E | 12 | Tipo de CT-e e de BP-e; o mesmo código tem versões. |
| classificacao_item_utilidade | CLASSIFICACAO_ITEM | 87 | Código de 4 dígitos; os 2 primeiros agrupam por serviço. |
| origem_deducao_diversa_efd | IND_DED_DIV | 7 |  |
| indicador_atividade_receita_deducao | coluna IND_ATIV (RECEITAS e DEDUCOES) | 6 | Valores 01 a 06; os valores existem no arquivo, a descrição de cada um não (pendência P43-02). |
| obrigacao_icms_recolher | tb19 | 9 | Lista nacional dos códigos de obrigação. |
| tipo_utilizacao_credito_icms | tb14 | 6 | Guarda o código sem o marcador "UF" (01, 21, 41, 61, 81, 99). |
| codigo_receita_icms | tb1316 | 16 | Código de receita de ICMS de 6 dígitos. |
| produto_usina_sucroalcooleira | tb13957 | 5 | Álcool e açúcar da usina. |

Cinco domínios já existem e só recebem linhas:

| Domínio existente | Origem | Linhas |
|---|---|---|
| base_credito_pis_cofins | BC_CRED | 19 |
| tipo_credito_pis_cofins | TIPO_CRED | 34 |
| contribuicao_social_pis_cofins | CS_APUR | 14 |
| modelo_documento_fiscal | MODELOS | 39 |
| origem_mercadoria | CST_ICMS (1º dígito do código) | 9 |

## 4.4 Entidades novas

São 11 entidades. As propostas seguem a convenção do dicionário: prefixo `Cad_`, `ID_X` e `ID_X_Versao` nas que têm vigência, `Vigencia_Inicio` e `Vigencia_Fim` (31/12/9999 quando aberto) e `Motivo_Vigencia`. A regra legal é parâmetro com vigência, tirada do `DT_INI` e do `DT_FIM` do próprio arquivo, nunca código fixo. Os valores legais entram com `Situacao_Dado = provisorio` até o contador validar.

### Cad_Natureza_Receita_Pis_Cofins_Aliquota

Alíquota de PIS e de Cofins que acompanha uma natureza da receita: percentual, ou valor em reais por unidade de medida (monofásico por unidade, bebidas frias), ou o par de alíquotas P e R de "outras operações". Vigência: sim. Origem: PROD_MONO_ALIQ_DIFER, PROD_MONO_ALIQ_UNID, PROD_ST, OUTROS_ALIQ_DIFER, ALIQ_AGRO_FRIGO.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Natureza_Aliquota | identificador |  |
| ID_Natureza_Aliquota_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| ID_Natureza_Receita | referência (Cad_Natureza_Receita_Pis_Cofins) --- identidade |  |
| Perfil_Aliquota | enumeração {unico, p, r} --- identidade | unico: uma só alíquota. p e r: as colunas _P e _R de OUTROS_ALIQ_DIFER; o significado delas é a pendência P43-02. |
| Forma_Aliquota | enumeração {percentual, por_unidade} | Em por_unidade, o valor está em reais por unidade de medida. |
| Aliquota_Pis | número, opcional | ALIQ_PIS (ou ALIQ_PIS_P e ALIQ_PIS_R). A vírgula decimal do arquivo vira ponto; 4 casas. |
| Aliquota_Cofins | número, opcional | ALIQ_COFIN (ou ALIQ_COF_P e ALIQ_COF_R). |
| ID_Unidade_Medida | referência (Cad_Unidade_Medida), opcional | Obrigatória em por_unidade. O arquivo traz o nome: Litro, Metro Cúbico, Unidade, Tonelada. |
| Situacao_Dado | enumeração {provisorio, validado} | A carga inicial sai provisória até o contador validar (mecanismo do Bloco 3, área de aprovação validacao_dado_legal). |
| ID_Instancia_Aprovacao | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Entra provisória: são alíquotas legais. A alíquota do ERP continua vindo de Cad_Aliquota e do motor de regras; esta entidade é o dado da tabela oficial que alimenta a conferência.

### Cad_CFOP_Uso_Efd_Contribuicoes

Para que a EFD-Contribuições usa cada CFOP: gerar crédito (com a base do crédito), devolução de compra (anula crédito), devolução de venda (reduz receita) ou receita. Vigência: sim. Origem: CFOP_CREDITO, CFOP_DEVOLUCAO, CFOP_DEVOLUCAO_VENDA, CFOP_RECEITA (vazia).

| Campo | Tipo | Descrição |
|---|---|---|
| ID_CFOP_Uso | identificador |  |
| ID_CFOP_Uso_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| ID_CFOP | referência (Cad_CFOP) --- identidade |  |
| Uso | enumeração {credito, devolucao_compra, devolucao_venda, receita} --- identidade | Um CFOP pode ter mais de um uso. |
| ID_Base_Credito | referência (Cad_Classe_Sistema, domínio = base_credito_pis_cofins), opcional | Só no uso credito (coluna NAT_BC_CRE). |
| Descricao_Receita | texto, opcional | Coluna desc_receita de CFOP_RECEITA (arquivo vazio hoje). |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Cad_CFOP já tem Indicador_Devolucao e Indicador_Anulacao, que dizem o que o CFOP é. Esta entidade diz o que a EFD-Contribuições faz com ele, e muda por ato próprio, com vigência própria.

### Cad_Faixa_Consumo_Sped

Faixa ou classe de consumo de energia, água, gás e comunicação que decide se o registro da EFD consolida os documentos da faixa ou sai um por documento. Vigência: sim. Origem: CONSUMO_ENERGIA, CONSUMO_AGUA, CONSUMO_GAS, CONSUMO_TELECOM.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Faixa_Consumo | identificador |  |
| ID_Faixa_Consumo_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| Servico | enumeração {energia_eletrica, agua, gas, comunicacao} --- identidade |  |
| Codigo | código (2) --- identidade | Como no arquivo (00 a 99). |
| Descricao | texto | Exatamente como publicada, sem o sufixo de modelos do arquivo de telecomunicações. |
| Perfil_Consumo | texto, opcional | Residencial, comercial/industrial, poder público, outros, quando a descrição diz. |
| Limite_Inferior | número, opcional | Lido da descrição (por exemplo 50,01). |
| Limite_Superior | número, opcional | Lido da descrição; vazio nas faixas "acima de". |
| Unidade_Faixa | enumeração {kwh, reais} | kWh na energia; reais nas demais. |
| Consolida_Documentos | booleano | Verdadeiro quando a descrição começa com "01 registro consolidando". |
| Modelos_Aplicaveis | texto, opcional | Os modelos de documento que vêm depois do ponto e vírgula em CONSUMO_TELECOM (21, 22). |
| Situacao_Dado | enumeração {provisorio, validado} | A carga inicial sai provisória até o contador validar (mecanismo do Bloco 3, área de aprovação validacao_dado_legal). |
| ID_Instancia_Aprovacao | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Os limites e a marca de consolidação são lidos do texto, por isso a carga sai provisória e o texto original fica guardado.

### Cad_Ajuste_Base_Pis_Cofins

Código de ajuste da base de cálculo de PIS/Cofins e se ele exige detalhamento. Vigência: sim. Origem: COD_AJUS_BASE_CALCULO_CONTRIB.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Ajuste_Base | identificador |  |
| ID_Ajuste_Base_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| Codigo | código (2) --- identidade | COD_AJUSTE. |
| Descricao | texto |  |
| Exige_Detalhamento | booleano | OBRIGA_DET: S vira verdadeiro. O tipo de detalhamento (por documento, item, NCM) está no domínio tipo_detalhamento_ajuste_pis_cofins. |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

### Cad_Receita_Deducao_Pis_Cofins

Receitas, exclusões e deduções que a EFD-Contribuições pede para pessoas jurídicas de setores específicos (instituições financeiras, seguradoras, previdência e outros), em quatro níveis: grupo, subgrupo, classe e detalhe. Vigência: sim. Origem: GRUPOS_RECEITAS, GRUPOS_DEDUCOES, SUBGRUPOS_RECEITAS, RECEITAS, DEDUCOES, 7 arquivos RECEITAS_GRUPOxxx e 9 arquivos DEDUCOES_GRUPOxxx.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Receita_Deducao | identificador |  |
| ID_Receita_Deducao_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| Tipo | enumeração {receita, deducao} --- identidade | Códigos de receita começam com R e os de dedução com D; o grupo 200, por exemplo, existe nos dois. |
| Nivel | enumeração {grupo, subgrupo, classe, detalhe} --- identidade | Grupo: 3 dígitos. Subgrupo: 4 caracteres (R020). Classe: 5 (R0201). Detalhe: 8 (R0201010). |
| Codigo | código (até 8) --- identidade |  |
| ID_Pai | referência (Cad_Receita_Deducao_Pis_Cofins), opcional | Detalhe aponta a classe (coluna SUBGRUPO do arquivo); classe aponta o subgrupo de mesmo prefixo de 4 caracteres quando ele existe (37 das 64 classes de receita), senão o grupo (coluna GRUPO). |
| Descricao | texto |  |
| Tipo_Deducao | enumeração {geral, especifica}, opcional | TIPO_DEDUC: G ou E. Só em dedução. |
| Indicador_Ajuste | texto (1), opcional | IND_AJUSTE: P ou N; o significado é a pendência P43-02. |
| Aceita_Descricao_Livre | booleano | IND_OUTROS: S vira verdadeiro (linha "outros", em que o declarante descreve). |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

22 arquivos para uma entidade só. Os níveis se separam pelo tamanho do código e pela tabela de origem.

### Cad_Receita_Deducao_Pis_Cofins_Atividade

Indicadores de atividade (IND_ATIV) a que cada receita ou dedução se aplica. Vigência: não. Origem: coluna IND_ATIV dos arquivos de receita e de dedução.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Receita_Deducao | referência (Cad_Receita_Deducao_Pis_Cofins) --- chave primária (composta) |  |
| ID_Atividade | referência (Cad_Classe_Sistema, domínio = indicador_atividade_receita_deducao) --- chave primária (composta) | Um registro por valor da lista separada por ponto e vírgula (por exemplo 01;06). |

A vigência é a da linha pai.

### Cad_Produto_Anp

Produto da ANP (combustíveis, lubrificantes, petróleo), usado no código ANP do produto. Vigência: sim. Origem: ANP.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Produto_Anp | identificador |  |
| ID_Produto_Anp_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| Codigo | código (9) --- identidade | COD_COMB. |
| Descricao | texto | DESC_AJUR (o nome da coluna no arquivo vem de outra tabela). |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Cad_Produto_Servico_Dados_Produto.Codigo_Anp deixa de ser código solto e passa a ser referência a esta entidade (ver alterações).

### Cad_Beneficio_Fiscal_Pis_Cofins

Benefício fiscal de PIS/Cofins com o CST, a natureza da receita e a informação complementar que ele exige (hoje, o Perse). Vigência: sim. Origem: BENEFICIOS_FISCAIS.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Beneficio_Pis_Cofins | identificador |  |
| ID_Beneficio_Pis_Cofins_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| Codigo | código (3) --- identidade | COD_BEN_FIS. |
| Informacao_Complementar | código (3) --- identidade | INF_COMP (101, 102 e 103 no Perse). |
| Descricao | texto |  |
| ID_Cst_Pis | referência (Cad_Cst) | CST_PIS. |
| ID_Cst_Cofins | referência (Cad_Cst) | CST_COFINS. |
| ID_Natureza_Receita | referência (Cad_Natureza_Receita_Pis_Cofins) | NAT_REC (920). |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Não se mistura com Cad_Beneficio_Fiscal_Icms, que é por UF e de ICMS.

### Cad_Obrigacao_Prazo_Entrega

Data limite de entrega de uma obrigação acessória por competência, como a Receita publica. Quando existe, vale mais que o cálculo de Cad_Regra_Vencimento. Vigência: sim. Origem: DATA_LIMITE_ENTREGA.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Prazo_Entrega | identificador |  |
| ID_Prazo_Entrega_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| ID_Obrigacao | referência (Cad_Obrigacao_Acessoria) --- identidade |  |
| Competencia | data --- identidade | Primeiro dia do mês da competência (MES_ANO 012014 vira 01/01/2014). |
| Data_Limite | data | DATA_LIMIT. |
| Origem | enumeração {arquivo_oficial, regra_calculada, ato_manual} | arquivo_oficial: veio da tabela. regra_calculada: gerada por Cad_Regra_Vencimento onde a tabela não tem a competência. ato_manual: prorrogação digitada. |
| Fundamento_Legal | texto, opcional | O ato da prorrogação, quando houver. |
| Situacao_Dado | enumeração {provisorio, validado} | A carga inicial sai provisória até o contador validar (mecanismo do Bloco 3, área de aprovação validacao_dado_legal). |
| ID_Instancia_Aprovacao | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| Vigencia_Inicio | data | DT_INI como publicado. |
| Vigencia_Fim | data | DT_FIM como publicado. Nos 150 registros do arquivo é 31/12 do quinto ano depois do ano do prazo, ou seja, o horizonte de decadência; ver seção 7. |
| Motivo_Vigencia | texto, opcional | Por exemplo, "prorrogação" quando uma nova data substitui a anterior da mesma competência. |

A competência de 02, 03 e 04/2020 tem a mesma data (14/07/2020), diferente da que a regra dá; o arquivo não cita o ato.

### Cad_Obrigacao_Leiaute_Versao

Versões do leiaute de cada escrituração e o código que o arquivo leva no registro 0000, com a vigência de cada uma. Vigência: sim. Origem: VERSOES_LEIAUTE, tb17816.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Leiaute_Versao | identificador |  |
| ID_Leiaute_Versao_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| ID_Obrigacao | referência (Cad_Obrigacao_Acessoria) --- identidade | SPED_FISCAL ou SPED_CONTRIBUICOES. |
| Codigo_Versao_Arquivo | código (3) --- identidade | COD_LEI/COD_VER: 002, 003, ... 021. |
| Numero_Leiaute | texto | VERSAO: 1.13, 1.20 ou 101. Não é único: no Contribuições o 101 aparece nos cinco códigos (002 a 006). |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

A versão 1.20 da EFD ICMS/IPI já está cadastrada no arquivo com início em 01/01/2027, sem fim.

### Cad_Obrigacao_Decadencia

Parâmetro do prazo de decadência: quantos anos e contados de quando, por obrigação ou por tributo. Vigência: sim. Origem: nenhuma carga: o arquivo PRAZO_DECADENCIA tem uma linha só, e a regra é inferida de DATA_LIMITE_ENTREGA e entra provisória.

| Campo | Tipo | Descrição |
|---|---|---|
| ID_Decadencia | identificador |  |
| ID_Decadencia_Versao | identificador da versão | Chave primária da versão (convenção da Fase 0, seção 2). |
| ID_Obrigacao | referência (Cad_Obrigacao_Acessoria), opcional |  |
| ID_Imposto | referência (Cad_Imposto), opcional | Vazio quando vale para a obrigação inteira. |
| Anos_Decadencia | número | 5 nos arquivos. |
| Base_Contagem | enumeração {ano_do_prazo_de_entrega, exercicio_seguinte_ao_fato_gerador, data_do_fato_gerador} | A regra observada nos arquivos é ano_do_prazo_de_entrega: 31/12 do quinto ano depois do ano do prazo. |
| Fundamento_Legal | texto, opcional | O contador informa; o arquivo não traz. |
| Situacao_Dado | enumeração {provisorio, validado} | A carga inicial sai provisória até o contador validar (mecanismo do Bloco 3, área de aprovação validacao_dado_legal). |
| ID_Instancia_Aprovacao | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| Vigencia_Inicio | data | Primeiro dia em que esta versão vale (DT_INI da tabela oficial). |
| Vigencia_Fim | data | Último dia em que esta versão vale; 31/12/9999 quando o DT_FIM vem vazio. |
| Motivo_Vigencia | texto, opcional | Por que esta versão foi criada (por exemplo, "correção da fonte, versão 38 para 39"). |

Nasce de D-N77. O documento 10 já fala em 5 anos de decadência para retificar PIS/Cofins depois de 2027.

## 4.5 Alterações em entidades que já existem

São propostas. O `model.json` não foi tocado.

| Entidade | Alteração proposta | Por quê | Tabelas |
|---|---|---|---|
| Cad_Tabela_Oficial | Campos novos: Familia_Fonte (texto: efd_contribuicoes ou efd_icms_ipi), Codigo_Tabela_Fonte (texto: 144, tb15236) e Colunas_Esperadas (texto). | Uma entrada por tabela SPED, com a assinatura de colunas que a carga confere (D-N73). | as 86 |
| Mov_Carga_Tabela_Oficial | Campos novos: Versao_Publicada (texto, do cabeçalho "versão=N"), Hash_Arquivo (texto, SHA-256), Codificacao_Origem (enumeração {utf8, windows_1252}), Linhas_Lidas, Linhas_Vigentes, Linhas_Ausentes (números). | Conferência de versão e de conteúdo; Linhas_Ausentes conta o que sumiu do arquivo novo (D-N80). | as 86 |
| Cad_Classe_Sistema | Dominio ganha 14 valores novos (seção 4.3) e passa a aceitar ID_Tabela_Oficial (referência, opcional) para dizer de qual carga a linha veio. | Listas simples não precisam de entidade própria (D-N74); a origem permite proteger a edição do usuário. | 13 tabelas + IND_ATIV |
| Cad_Natureza_Receita_Pis_Cofins | Codigo passa de código (3) para código (até 6) e a identidade passa a ser ID_Grupo_Natureza mais Codigo. O domínio grupo_natureza_receita ganha 9 valores, um por arquivo de NCM por tratamento. | O código 101 existe em nove tabelas com sentidos diferentes (93 dos 574 códigos repetem) e os produtos de bebidas frias têm 6 dígitos (D-N75). | 9 de OPER_CONTRIB e OPER_CREDITO |
| Cad_Natureza_Receita_Pis_Cofins_Classificacao | Campos novos: Tipo_Vinculo (enumeração {inclui, exclui}) e ID_Ex_Tipi (referência a Cad_NCM_Ex_Tipi, opcional). | NCM_EX lista NCMs excluídos e EX_IPI traz o número do Ex da TIPI (D-N75). | colunas NCM, NCM_EX, EX_IPI |
| Cad_Cprb_Atividade | Campo novo: ID_Classificacao (referência a Cad_Classificacao_Mercadoria, opcional). ID_Nomenclatura fica para a nomenclatura. | Hoje o campo do NCM aponta a nomenclatura (NCM como um todo), não o código; em 10.036 das 10.085 linhas o COD_ATV é o NCM de 8 dígitos. | COD_ATIVIDADE |
| Cad_Regra_Vencimento | Campo novo: ID_Obrigacao (referência a Cad_Obrigacao_Acessoria, opcional). | Hoje a regra só sabe a origem em uma lista fechada (esocial, reinf, mit, das...) e a EFD fica em "outra" (D-N77). | DATA_LIMITE_ENTREGA |
| Cad_Cst | Para o ICMS, Codigo guarda só o CST de 2 dígitos ou o CSOSN de 3, e Familia aceita csosn. A origem (0 a 8) fica no domínio origem_mercadoria, que já existe. | O código de 3 dígitos do arquivo mistura origem e CST e colide com os CSOSN 300, 400 e 500 (D-N78). | CST_ICMS |
| Cad_Municipio | A regra do dígito verificador de Codigo_IBGE passa a avisar, e não a rejeitar, para 9 códigos oficiais que não a cumprem (2201919, 2201988, 2202251, 2611533, 3117836, 3152131, 4305871, 5203939, 5203962). | São municípios reais do IBGE que falham no cálculo (D-N78). | tb16896, MUNICIPIOS |
| Cad_Produto_Servico_Dados_Produto | Codigo_Anp (código de 9) vira ID_Produto_Anp (referência a Cad_Produto_Anp). | Troca o código solto por catálogo conferido, com vigência. | ANP |
| Cad_Cest | Nenhum campo novo. A carga ignora a descrição quando ela é o aviso "Verificar, para o CEST, a descrição vigente...", e a descrição vem do Convênio ICMS 142/18. | 1.038 das 1.038 linhas vigentes têm esse aviso no lugar da descrição. | tb16643 |
| Cad_Icms_Codigo_Ajuste (proposta do documento 33) | ID_Estado passa a opcional (códigos genéricos valem para todas as UFs); Tipo_Apuracao separa difal e fcp (hoje difal_fcp) e Natureza ganha controle_extra_apuracao. | tb1875 traz Difal e FCP em códigos separados desde 01/01/2017 e o código de controle extra-apuração (UF099999). | tb1875 |
| Cad_Icms_Obrigacao_Recolher (proposta do documento 33) | Codigo_Obrigacao vira referência ao domínio obrigacao_icms_recolher; ID_Estado fica só para o Codigo_Receita de cada UF. | tb19 é a lista nacional dos 9 códigos de obrigação; só o código de receita é por UF. | tb19 |

## 4.6 Ligações com o que já existe

| Do arquivo | Para | Como |
|---|---|---|
| CFOP (tb15236) | `Cad_CFOP` | `CFOP` vira `Codigo_CFOP`; `DESC_CFOP` vira `Titulo` (é a denominação curta). A `Descricao` completa e os indicadores não vêm daqui. Os 10 códigos com texto novo desde 01/06/2022 e o 5929 viram versões |
| CFOP de crédito e devolução | `Cad_CFOP_Uso_Efd_Contribuicoes` | Referência a `Cad_CFOP`; `NAT_BC_CRE` aponta o domínio `base_credito_pis_cofins` |
| CST_PIS, CST_COFINS, CST_IPI, CST_ICMS | `Cad_Cst` | Por `ID_Imposto`; a direção (`Aplicacao`) vem da faixa do código, que o arquivo não traz |
| NCM de 2 a 8 dígitos | `Cad_Classificacao_Mercadoria` | O comprimento do código dá o nível (2 capítulo, 4 posição, 5 e 6 subposição, 7 item, 8 subitem) |
| EX_IPI | `Cad_NCM_Ex_Tipi` | `Numero_Ex` com a NCM da linha; combinação que a TIPI não tem vira pendência da carga |
| Naturezas e benefício | `Cad_Natureza_Receita_Pis_Cofins`, `Cad_Beneficio_Fiscal_Pis_Cofins` | O benefício aponta CST e natureza; a natureza 920 (Perse) existe em `PROD_ALIQ_ZERO` com CST 06 no benefício |
| Códigos de receita | `Cad_Codigo_Receita_Raiz` e `Cad_Codigo_Receita` | Raiz de 4 dígitos (F600) e código de 6 (P200, DCTF) |
| Datas limite | `Cad_Obrigacao_Acessoria`, `Cad_Regra_Vencimento`, `Cad_Feriado` | Seção 7 |

# 5. Tabelas de NCM por tratamento

Nove arquivos dizem, por código de natureza da receita, a lista de NCMs a que o tratamento se aplica e, em cinco deles, a alíquota. Oito estão em `OPER_CONTRIB` e correspondem às tabelas 4.3.10 a 4.3.17 que o documento 10 cita (qual arquivo é qual número é a pendência P43-01); o nono, `ALIQ_AGRO_FRIGO`, está em `OPER_CREDITO` e traz alíquotas de crédito presumido.

| Tratamento | Arquivo | Linhas | Códigos | Vigentes | Linhas com NCM | NCMs listados | Linhas com NCM_EX | Linhas com EX_IPI | Alíquota |
|---|---|---|---|---|---|---|---|---|---|
| Monofásico, alíquotas diferenciadas | PROD_MONO_ALIQ_DIFER | 193 | 64 | 60 | 106 | 172 | 1 | 49 | percentual |
| Monofásico, alíquota por unidade | PROD_MONO_ALIQ_UNID | 1.342 | 439 | 43 | 128 | 186 | 0 | 54 | reais por unidade |
| Substituição tributária | PROD_ST | 14 | 14 | 12 | 3 | 3 | 0 | 0 | percentual |
| Alíquota zero | PROD_ALIQ_ZERO | 158 | 118 | 97 | 38 | 85 | 2 | 10 | não |
| Isenção | OPER_COM_ISENCAO | 16 | 16 | 11 | 1 | 27 | 0 | 0 | não |
| Sem incidência | OPER_SEM_INCIDENCIA | 10 | 10 | 10 | 0 | 0 | 0 | 0 | não |
| Suspensão | OPER_COM_SUSPENSAO | 60 | 53 | 43 | 2 | 30 | 1 | 0 | não |
| Outras, alíquotas diferenciadas | OUTROS_ALIQ_DIFER | 66 | 52 | 50 | 0 | 0 | 0 | 0 | percentual (P e R) |
| Crédito presumido agroindústria e frigorífico | ALIQ_AGRO_FRIGO | 38 | 29 | 20 | 18 | 75 | 2 | 0 | percentual |

**Como a tabela é lida.** Cada linha é um código de natureza com sua descrição, a vigência da linha, uma lista de NCMs separados por ponto e vírgula e, às vezes, as alíquotas. A lista aceita códigos de 2 a 8 dígitos, que são capítulo, posição, subposição, item e subitem; o dicionário já guarda NCM em qualquer nível (`Cad_Natureza_Receita_Pis_Cofins_Classificacao`). No conjunto, só 296 das 1.897 linhas trazem NCM; nas demais o tratamento é descrito só por texto e a ligação com o produto fica no cadastro da mercadoria.

**Como alimentam o CST e a alíquota.** O arquivo não traz o CST. O vínculo vem da natureza: `Cad_Natureza_Receita_Pis_Cofins_Cst` liga cada natureza aos CST em que ela é obrigatória (04 a 09, segundo o documento 10). Há uma confirmação no arquivo `BENEFICIOS_FISCAIS`: o Perse tem CST 06 e natureza 920, que está em `PROD_ALIQ_ZERO`. A alíquota entra no ERP em `Cad_Aliquota` e no motor de regras; o valor da tabela oficial serve de conferência e fica em `Cad_Natureza_Receita_Pis_Cofins_Aliquota`, provisório.

**Vigência por NCM e por NCM_EX e EX_IPI.** A vigência é da linha, não de cada NCM: a linha é o conjunto de NCMs que valia naquele período. Para ter vigência por NCM, a carga abre a lista em um registro por NCM, e cada um herda `DT_INI` e `DT_FIM` da linha. Quando a lista muda, a Receita publica uma linha nova com a lista nova, e a carga encerra a antiga. O `NCM_EX` é uma lista de NCMs **excluídos** (só 6 linhas, em `PROD_MONO_ALIQ_DIFER`, `PROD_ALIQ_ZERO`, `OPER_COM_SUSPENSAO` e `ALIQ_AGRO_FRIGO`; em 5 delas são NCMs, como 30039056 excluído do 3003, e a sexta, `PROD_ALIQ_ZERO` 309, traz "01", que parece um Ex na coluna errada) e vira `Tipo_Vinculo = exclui` com a mesma vigência. O `EX_IPI` é o **número do Ex da TIPI** (113 linhas); vira `ID_Ex_Tipi`. Quando a linha tem várias NCMs e um só Ex, o arquivo não diz a qual pertence (17 linhas): a carga o grava em todas e confere contra `Cad_NCM_Ex_Tipi`, e o que a TIPI não tiver vira pendência (P43-10).

**Um exemplo.** O código 112 (álcool) em `PROD_MONO_ALIQ_DIFER` tem, de 01/05/2025 em diante, duas linhas do mesmo período e com as mesmas alíquotas (5,25 e 24,15): uma com as NCMs 2207.10.00 e 2207.20.10 e outras, e outra com a NCM 2208.90.00 e Ex 01. A carga as junta em uma natureza com dois grupos de NCM, um deles com Ex.

**Pontos de atenção.**

- A identidade da natureza é grupo mais código (V1). `PROD_MONO_ALIQ_UNID` mistura 203 linhas de 3 dígitos (132 códigos, naturezas) e 1.139 de 6 dígitos (produtos de bebidas frias por embalagem, como 930001, com alíquota em reais por litro e 1.256 das 1.342 linhas em litro). O documento 10 cita a tabela 4.3.10 para bebidas frias, mas elas estão neste arquivo (V7).
- Há históricos longos: `PROD_MONO_ALIQ_UNID` tem 1.342 linhas e só 43 vigentes, por causa das mudanças de alíquota de combustíveis. O óleo diesel (102) tem a última linha de 12/03/2026 a 31/05/2026, com 0,01 e 0,05 por metro cúbico, e nada depois (P43-08).
- Quatro linhas de `PROD_MONO_ALIQ_DIFER` (códigos 150 a 153, desde 01/03/2026) terminam em 31/12/2026. O Perse (920, em `PROD_ALIQ_ZERO`) termina em 28/02/2027 e o 921 de `OUTROS_ALIQ_DIFER`, em 31/12/2027. São datas do arquivo, guardadas como estão.
- `COD_ATIVIDADE` (CPRB) também é lista de NCM, mas por código: o `COD_ATV` de 8 dígitos é o próprio NCM em 10.036 das 10.085 linhas, e `NCM_ATV` vem vazio em todas. As outras 49 têm código de atividade que começa com zeros (por exemplo 00000100, transporte ferroviário de passageiros). O mesmo código muda de alíquota ao longo do tempo (4.956 códigos em 10.085 linhas; vigentes 2.907), o que `Cad_Cprb_Atividade` já comporta por versão. Falta o campo do NCM como código (V11) e o `Codigo_Receita`, que o arquivo não traz.

# 6. Receitas, deduções, créditos, ajustes e códigos de receita

## 6.1 Receitas e deduções

São 22 arquivos, 21 deles em hierarquia de quatro níveis (o 22º, `IND_DED_DIV`, é lista simples), usada por pessoas jurídicas de setores específicos, segundo `GRUPOS_RECEITAS`: componentes do sistema financeiro (100 e 700), corretoras autônomas de seguros (200), seguradoras, capitalização e previdência privada (300), entidades fechadas de previdência complementar (400), operadoras de plano de saúde (500) e securitização de crédito (600). O dicionário não tem nada equivalente.

| Nível | Arquivos | Código | Linhas |
|---|---|---|---|
| Grupo | GRUPOS_RECEITAS, GRUPOS_DEDUCOES | 3 dígitos (receitas 100 a 700; deduções 000 a 700 na tabela de grupos, e 800 só no arquivo de detalhe) | 15 |
| Subgrupo | SUBGRUPOS_RECEITAS | 4 caracteres (R020) | 15 |
| Classe | RECEITAS, DEDUCOES | 5 caracteres (R0201, D0001) | 184 |
| Detalhe | 7 arquivos RECEITAS_GRUPOxxx e 9 DEDUCOES_GRUPOxxx | 8 caracteres (R0201010) | 460 |

A ligação é pela coluna `SUBGRUPO` dos arquivos de detalhe: ela aponta a classe de 5 caracteres (63 das 64 classes citadas nas receitas existem em `RECEITAS`, e as 65 citadas nas deduções existem em `DEDUCOES`). A classe aponta o subgrupo de mesmo prefixo de 4 caracteres, que existe para 37 das 64 classes de receita, e senão o grupo pela coluna `GRUPO`; em todos os 37 casos o grupo coincide. Os códigos de dedução não têm tabela de subgrupos.

Dos 104 códigos de classe de receita, 65 estão vigentes (grupos 100 a 600) e 39 terminaram em 31/12/2013 ou 31/01/2014 (os 15 do grupo 700 e parte dos grupos 300, 400 e 500), pouco antes de os arquivos de detalhe começarem, em 01/01/2014 em 450 de 460 linhas. A vigência de cada linha é que diz o que vale em cada competência. O grupo 800 de deduções (6 linhas de detalhe) não consta de `GRUPOS_DEDUCOES`: a carga cria o grupo a partir do arquivo de detalhe e registra aviso (V8).

Outras colunas: `IND_ATIV` lista as atividades a que o código se aplica (valores 01 a 06 separados por ponto e vírgula; viram uma linha filha), `IND_AJUSTE` vale P (438 das 460 linhas de detalhe) ou N (22), cujo significado é a pendência P43-02, `IND_OUTROS` marca a linha "outros" (S ou N) e `TIPO_DEDUC` vale G (7 linhas) ou E (73). `IND_DED_DIV` (7 linhas) é lista simples e vira o domínio `origem_deducao_diversa_efd`. Há um defeito de arquivo: os grupos 100 e 700 de `GRUPOS_RECEITAS` têm a mesma descrição (componentes do sistema financeiro).

## 6.2 Natureza do crédito, tipo de crédito e contribuição apurada

Três listas pequenas que o dicionário já tem como domínios: `BC_CRED` (19 linhas, 18 vigentes), `TIPO_CRED` (34 linhas, 25 vigentes) e `CS_APUR` (14 linhas). Entram como linhas dos domínios existentes. O que o arquivo acrescenta é o histórico: os códigos 106, 206 e 306 têm três versões (a do meio dura um dia, 11/03/2022) e os 199, 299 e 399 acabam em 31/03/2023; o código 14 de `BC_CRED` muda de texto em 22/12/2022. Tudo isso é versão, e a carga não pode tratar como duplicata.

Três tabelas de CFOP dizem o que o Contribuições faz com cada código: `CFOP_CREDITO` (89 CFOPs de entrada que geram crédito, cada um com a base `NAT_BC_CRE`), `CFOP_DEVOLUCAO` (43 CFOPs de saída de devolução de compra e anulação de valor) e `CFOP_DEVOLUCAO_VENDA` (16 de devolução de venda). Todos existem na lista de CFOP. Elas viram uma entidade só, `Cad_CFOP_Uso_Efd_Contribuicoes`, e `CFOP_RECEITA` (vazia) cabe nela quando vier com linhas.

## 6.3 Ajustes

Três famílias de ajuste, de naturezas diferentes:

| Tabela | O que é | Destino |
|---|---|---|
| `AJ_CONTRIB_CRED` (13 linhas) | Origem do ajuste de contribuição ou de crédito: ação judicial, processo administrativo, legislação, RTT, estorno; os códigos 10 a 12 (redução linear de incentivos, desde 01/04/2026) são os mais novos | Domínio `origem_ajuste_pis_cofins` |
| `COD_AJUS_BASE_CALCULO_CONTRIB` (7 linhas) | Ajuste da base de cálculo, com `OBRIGA_DET` (exige detalhamento) e vigência desde 2002 | `Cad_Ajuste_Base_Pis_Cofins` |
| `COD_DETALHAM` (5 linhas) | Tipo de detalhamento exigido: documento fiscal, item, NCM, cliente ou outros critérios | Domínio `tipo_detalhamento_ajuste_pis_cofins` |
| tb1875 (31 linhas) | Códigos genéricos de ajuste da apuração do ICMS: `UF` + tipo (0 próprio, 1 ST, 2 Difal, 3 FCP) + natureza (0 outros débitos, 1 estorno de crédito, 2 outros créditos, 3 estorno de débito, 4 dedução, 5 débito especial, 9 controle) + 9999 | `Cad_Icms_Codigo_Ajuste` (documento 33), com os ajustes da seção 4.5 |
| tb14 (6 linhas) | Tipo de utilização de crédito: dedução, compensação, transferência, restituição, estorno, outros | Domínio `tipo_utilizacao_credito_icms` |

A tb1875 mostra que o Difal e o FCP eram um só código em 2016 (os seis `UF20` a `UF25`, de 01/01/2016 a 31/12/2016, encerrados) e passam a ser dois a partir de 01/01/2017 (Difal `UF2x`, FCP `UF3x`); o documento 33 ainda os junta em `difal_fcp` (V4). O código `UF099999` (controle do ICMS extra-apuração) também não está na lista de naturezas do documento 33. A sigla `UF` é marcador: a carga gera o código de cada estado trocando-a pela sigla, ou guarda o genérico sem estado (D-N77 e seção 4.5).

## 6.4 Códigos de receita e DCTF

| Arquivo | Linhas | Código | Destino | Observação |
|---|---|---|---|---|
| COD_REC_F600 | 27 | 4 dígitos (0067, 5952, 6190) | `Cad_Codigo_Receita_Raiz` | Retenção na fonte. Zeros à esquerda preservados, como o dicionário prevê |
| COD_REC_P200 | 8 | 6 dígitos (298501) | `Cad_Codigo_Receita` | CPRB. Periodicidade "Mensal" em 6 e "mensal" em 2 |
| VISAO_DCTF / CONTRIBUICOES_COFINS | 36 | 6 dígitos (585601) | `Cad_Codigo_Receita` | 29 mensais, 5 "Diária" e 2 com "-" |
| VISAO_DCTF / CONTRIBUICOES_PISPASEP | 38 | 6 dígitos (691201) | `Cad_Codigo_Receita` | 33 mensais e 5 "Diária"; o 810908 está sem "SCP" na descrição |
| tb1316 | 16 | 6 dígitos (100013) | Domínio `codigo_receita_icms` | Receita de ICMS; falta confirmar o campo da EFD em que é usada (P43-05) |
| tb19 | 9 | 3 dígitos (000 a 006, 090, 999) | Domínio `obrigacao_icms_recolher` | Lista nacional; o documento 33 passa a apontar para ela |

A carga normaliza a periodicidade para o enum de `Cad_Codigo_Receita` (`mensal`, `diaria`) e deixa vazio quando o arquivo traz "-". `Origem_Declaracao` e `Grupo_Tributo_Mit` não vêm destes arquivos; seguem das outras fontes do documento 10.

# 7. Calendário de entrega, versões de leiaute e decadência

## 7.1 Data limite de entrega

`DATA_LIMITE_ENTREGA` (versão 49) tem uma linha por competência, de 01/2014 a 06/2026: 150 linhas, sem lacuna. Cada linha traz a competência (`MES_ANO`, como 012014), a data limite e um `DT_INI` e `DT_FIM`. O `DT_INI` é sempre 01/01/2019.

**A data é calculável.** A regra é o décimo dia útil do segundo mês seguinte à competência, contando como não úteis os sábados, domingos e os feriados bancários (inclusive Carnaval e Corpus Christi, e o 20 de novembro a partir de 2024). Com ela, 147 das 150 datas batem. Sem contar o Corpus Christi, só 143 batem, o que mostra que ele conta como dia não útil.

| Competência | Data no arquivo | Data pela regra |
|---|---|---|
| 02/2020 | 14/07/2020 | 15/04/2020 |
| 03/2020 | 14/07/2020 | 15/05/2020 |
| 04/2020 | 14/07/2020 | 15/06/2020 |

As três competências têm a mesma data, o que indica prorrogação; o arquivo não cita o ato (P43-09). A regra existe no dicionário: `Cad_Regra_Vencimento` com `Finalidade = entrega_declaracao`, `Referencia_Fim = fim_do_mes`, `Meses_Deslocamento = 2`, `Tipo_Dia = dias_uteis_apos` e `Dias_Uteis_Apos = 10`. Falta ligá-la à obrigação (campo `ID_Obrigacao`).

**Proposta (D-N77).** A data publicada vale mais que o cálculo: `Cad_Obrigacao_Prazo_Entrega` guarda a data de cada competência, com `Origem = arquivo_oficial`; onde não houver linha, o ERP gera a data pela regra e marca `regra_calculada`; uma prorrogação digitada entra como `ato_manual` e vira nova versão da competência. Os dois caminhos entram provisórios até o contador validar.

**O arquivo está atrasado.** Não há competência depois de 06/2026. Em 06/10/2026 já deveriam existir as competências 07, 08 e 09/2026 (P43-08). Até a versão nova chegar, o ERP usa a regra.

## 7.2 Decadência

Em 150 de 150 linhas, o `DT_FIM` é o 31/12 do quinto ano depois do ano da data limite. Para 01/2014, cuja data limite é 18/03/2014, o `DT_FIM` é 31/12/2019. Não é o fim da vigência do prazo (V12): é o horizonte de decadência de cinco anos, que o programa do SPED usa para guardar a linha. Das 150 linhas, 68 ainda estão dentro do horizonte e 82 já terminaram, e 56 vão até 2027 a 2031.

`PRAZO_DECADENCIA` tem uma só linha (competência 01/2012, decadência em 01/01/2018), encerrada por ela mesma (`DT_FIM` = 01/01/2012). Ela é coerente com a regra do `DT_FIM` acima (o prazo de 2012 mais 5 anos vai a 31/12/2017, e a decadência cai no dia seguinte) e não serve como tabela. Por isso a decadência vira parâmetro, `Cad_Obrigacao_Decadencia`: 5 anos, base de contagem `ano_do_prazo_de_entrega`, por obrigação ou tributo, com vigência. O documento 10 já fala em 5 anos de decadência para retificar PIS/Cofins depois de 2027. O fundamento legal e a base de contagem são do contador (P43-13); entra provisório.

## 7.3 Versões de leiaute

| Arquivo | Linhas | Versões | Vigente hoje | Futura |
|---|---|---|---|---|
| `VERSOES_LEIAUTE` (EFD-Contribuições, v6) | 5 | código 002 a 006, versão 101 | código 006, versão 101, desde 01/01/2020, sem fim | — |
| tb17816 (EFD ICMS/IPI, v21) | 20 | código 002 a 021, versões 1.01 a 1.20 | código 020, versão 1.19, de 01/01/2026 a 31/12/2026 | código 021, versão 1.20, a partir de 01/01/2027, sem fim |

No Contribuições o número da versão (101) repete nos cinco códigos de arquivo (002 a 006), por isso `Cad_Obrigacao_Leiaute_Versao` tem `Codigo_Versao_Arquivo` como identidade e `Numero_Leiaute` como texto. A tb17816 já traz a versão 1.20 do SPED Fiscal com início em 01/01/2027: indica, no próprio arquivo, que a EFD ICMS/IPI segue em 2027.

`Cad_Obrigacao_Acessoria` já tem `Vigencia_Inicio` e `Vigencia_Fim` e códigos `SPED_FISCAL` e `SPED_CONTRIBUICOES`. As versões de leiaute, os prazos e a decadência apontam para ela, o que dá o encadeamento obrigação, versão, competência, prazo.

# 8. Itens de consumo e classificação

Os quatro arquivos de consumo decidem como o registro da escrituração é gerado: um registro que consolida os documentos de uma faixa, ou um registro por documento. Têm a mesma forma, código de 2 dígitos e descrição, mas a faixa muda de unidade.

| Arquivo | Linhas | Vigentes | Faixa por | Observações |
|---|---|---|---|---|
| CONSUMO_ENERGIA (v2.0) | 25 | 20 | kWh | Dois espaços de código: 00 a 99 (consumo por faixa; 5 linhas residenciais encerradas em 31/12/2009) e 01 a 08 (classes, desde 01/01/2010); o código 01 existe nos dois |
| CONSUMO_AGUA (v1.0) | 26 | 26 | reais | Residencial e comercial/industrial, de "até R$ 50,00" a "acima de R$ 1.000,01" |
| CONSUMO_GAS (v1.0) | 26 | 26 | reais | Igual à água |
| CONSUMO_TELECOM (sem cabeçalho) | 35 | 35 | reais | A descrição termina em ";21;22" ou ";22": são os modelos a que a linha se aplica, e não fazem parte do texto |

`Cad_Faixa_Consumo_Sped` guarda a descrição como publicada e, ao lado, os valores lidos dela (limites, unidade, marca de consolidação e modelos). Como a leitura é de texto, a carga sai provisória e o contador confere uma amostra. O desenvolvimento de telas e da geração desses registros só começa quando houver cliente que precise (D-N79).

`CLASSIFICACAO_ITEM` (87 linhas, versão 2.0) classifica o item dos documentos de telecomunicação e comunicação (assinatura, habilitação, serviço medido, interconexão e outros; o tipo 06 é energia elétrica) por código de 4 dígitos; os 2 primeiros são o tipo de serviço (01 a 11) e os 2 últimos o item. É lista simples e vira o domínio `classificacao_item_utilidade`.

Duas listas de documentos de transporte seguem o mesmo caminho de domínio: `TIPO_CT` (22 linhas: AWB, MAWB e outros) vira `tipo_conhecimento_embarque`, e `TIPO_CT_E` (12 linhas) vira `tipo_cte_efd`, com o mesmo código em até três versões (0, 3 e 4) e uma versão de um dia (código 4, em 01/10/2024), que a carga não pode tratar como erro. O texto de `TIPO_CT` traz erros de digitação ("NÂO IATA", "MNAO IATA"), que a carga preserva e registra como aviso.

# 9. Tabelas obsoletas ou duplicadas

Sete tabelas não são carregadas. Todas ficam registradas em `Cad_Tabela_Oficial` com a versão lida, para a carga futura reconhecer se mudarem.

| Tabela | Família | Linhas | O que é | Motivo |
|---|---|---|---|---|
| SERVICO | EFD-Contribuições | 193 | Lista de serviços (versão antiga, sem ponto) | Os 193 códigos (101, 102, ...) existem com a mesma descrição em SERVICO_LCP_116, que tem 200 itens e é de 2015. Subconjunto exato; não carregar. |
| CFOP | EFD-Contribuições | 637 | CFOP (versão do SPED Contribuições) | Duplicada pela tb15236 (EFD ICMS/IPI), que é mais nova (versão 14 contra 9) e traz os mesmos 619 códigos vigentes; 12 descrições diferem (11 de conteúdo e 1 só de espaço no fim). Não carregar; ver D-N76. |
| PRAZO_DECADENCIA | EFD-Contribuições | 1 | Prazo de decadência | Uma só linha (competência 01/2012, decadência em 01/01/2018), já encerrada por ela mesma (DT_FIM = 01/01/2012). Serve de exemplo da regra, não de tabela. |
| MUNICIPIOS | EFD-Contribuições | 5.575 | Municípios (versão do SPED Contribuições) | Duplicada pela tb16896 (EFD ICMS/IPI, versão 20 contra 10), que já traz os mesmos 5.572 códigos vigentes e mais o 9999998. Ver D-N76 e o item de municípios. |
| tb131 | EFD ICMS/IPI | 21 | Totalizadores parciais da redução Z (ECF) | 21 linhas, sem fim no arquivo. É a tabela do cupom fiscal emitido por ECF, que o resumo da EFD (documento de apoio ao 37) trata como legado (C300 a C495). Reavaliar se o desenho passar a gerar esses registros. |
| MENSAGENS_USUARIO | EFD-Contribuições | 0 | Mensagens ao usuário do programa validador | Arquivo sem nenhuma linha (só cabeçalho). Não tem função no ERP. |
| CFOP_RECEITA | EFD-Contribuições | 0 | CFOP por tipo de receita | Arquivo vazio: só cabeçalho (e o único em UTF-8). Registrar a versão no controle de cargas e reavaliar quando vier com linhas. |

**Pares e conjuntos que se sobrepõem.** (a) CFOP: as duas listas vigentes são iguais (619 códigos), a do ICMS/IPI é a versão 14 e a do Contribuições a 9; entre as vigentes, 12 descrições diferem (10 pelo texto sobre o MEI desde 01/06/2022, 1 pelo 5929 desde 01/02/2020 e 1 só por espaço no fim, o 2454). (b) Municípios: a tb16896 (v20) traz os 5.570 códigos do anexo A da NFS-e (IBGE), mais o 5101837 (instalado em 2025, segundo o arquivo), o 9999998 (CT-e simplificado) e o 9999999 (Exterior); a do Contribuições (v10) tem o 5101837 e o 9999999. Os códigos 9999998 e 9999999 não são municípios brasileiros e ficam fora de `Cad_Municipio`; o 5101837 não consta do anexo A da NFS-e. As grafias diferem do IBGE em 22 nomes na tb16896 e em 24 na do Contribuições. (c) Serviços: `SERVICO` é subconjunto exato de `SERVICO_LCP_116`, que é a lista de 2015 com 200 subitens (cada um com e sem ponto), todos presentes na lista nacional da NFS-e (201, a mais é 99.01); 19 descrições são abreviadas e a do 15.08 começa com aspas. (d) UF: `UF_CODIGO_SIGLA` e `UF_SIGLA_NOME` se completam (27 linhas cada) e conferem com `Cad_Estado`. (e) Países: 224 dos 250 nomes coincidem com a lista ISO do anexo A da NFS-e, e a conciliação por código precisa de outra fonte (P43-06). (f) Gênero do item (100 linhas) é o capítulo da NCM; `Cad_Classificacao_Mercadoria` já o tem.

**Linhas encerradas.** Das 30.469 linhas, 10.261 já terminaram (DT_FIM anterior a hoje), 20.207 valem e 1 começa em 2027. As tabelas com mais histórico são `COD_ATIVIDADE` (7.178 encerradas, de 10.085), `PROD_MONO_ALIQ_UNID` (1.299, de 1.342) e a tb16643 do CEST (1.147, de 2.185). Esses registros não são lixo: no dicionário viram versões encerradas, e valem para retificar período antigo. A carga não os apaga.

# 10. As tabelas depois da CBS

Três fontes falam do futuro do PIS/Cofins e da EFD-Contribuições, e elas não coincidem: o documento 10 (seção 18) diz que PIS/Cofins se extingue em 2027 e que a natureza da receita continua necessária para retificar períodos dentro dos 5 anos de decadência; o documento 32, com fonte secundária, diz que em 31/12/2026 acaba a EFD-Contribuições como escrituração de apuração e que ela permanece para controle de créditos; e o cadastro de `Cad_Obrigacao_Acessoria` guarda para `SPED_CONTRIBUICOES` um fim esperado por volta de 2033, sem confirmação (P43-11). Não há ato oficial nas fontes, e não inventei data.

Os arquivos dão fatos próprios: o Perse (benefício 060, natureza 920) vale até 28/02/2027; o código 921 de `OUTROS_ALIQ_DIFER` vai até 31/12/2027; 56 competências de `DATA_LIMITE_ENTREGA` têm `DT_FIM` de 2027 a 2031 (que é o horizonte de decadência, V12); a tb17816 traz a versão 1.20 do SPED Fiscal a partir de 01/01/2027.

| Situação | Tabelas | Quais | O que acontece |
|---|---|---|---|
| segue em uso | 13 | ICMS/IPI (menos a tb131), CEST, ANP, CST de ICMS e IPI, tipo de CT-e | Continuam em uso; a EFD ICMS/IPI segue em 2027 (leiaute 1.20) |
| referência geral | 11 | UF, países, municípios, CFOP, serviços, modelos, gênero do item, enquadramento do IPI, tipo de conhecimento | Listas gerais, de uso em várias obrigações; seguem |
| só retificação | 60 | As demais do Contribuições: natureza e NCM, créditos, ajustes, receitas e deduções, códigos de receita e DCTF, consumo, prazos | Continuam necessárias para retificar períodos dentro dos 5 anos (documento 10); a nova escrituração depende de o PIS/Cofins ainda ter apuração |
| legado | 2 | tb131 (ECF) e `MENSAGENS_USUARIO` | Sem uso no desenho |

**Regra proposta (D-N80).** Nenhuma tabela é desativada por data fixa. A vigência de cada linha, publicada no arquivo, decide o que vale em cada competência, e a rotina de atualização de uma tabela do Contribuições só para quando a Receita parar de publicar (a carga detecta isso quando o arquivo deixa de mudar por duas consultas seguidas, e o usuário confirma). As naturezas e as tabelas de NCM continuam consultáveis para retificar.

# 11. Carga inicial e atualização

## 11.1 Formato

- **Delimitador.** `|`, uma linha por registro; cada linha termina com o separador antes de um `DT_FIM` vazio (por exemplo `5300108|Brasília|01012009|`).
- **Cabeçalho.** A primeira linha traz `versão=N` e as colunas. A carga lê quatro formas (colunas com vírgula, colunas com `|` e título, só a versão, nenhuma) e confere as colunas contra `Colunas_Esperadas` de `Cad_Tabela_Oficial`. Coluna a mais ou a menos rejeita a carga.
- **Codificação.** Tentar UTF-8 e, se falhar, Windows-1252 (85 dos 86 são desse tipo). Os arquivos não seguem ISO-8859-1 estrito, como se poderia supor: os bytes 0x92, 0x93, 0x94 e 0x96 são aspas e travessões. A carga grava a codificação detectada.
- **Registros partidos.** Linha cujo número de separadores é menor que o esperado é continuação da anterior (acontece nas descrições do CFOP).
- **Datas.** `ddmmaaaa`; `DT_FIM` vazio vira 31/12/9999. Todas as linhas têm `DT_INI`; as duas tabelas vazias (`CFOP_RECEITA` e `MENSAGENS_USUARIO`) não têm linha nenhuma.
- **Números.** Alíquotas com vírgula decimal ("0,65", "1,0" e "1" para o mesmo valor); a carga converte e guarda o texto original no registro de carga.
- **Normalização.** Periodicidade ("Mensal", "mensal", "Diária", "-"), códigos com e sem ponto (lista de serviços), sufixo de modelos na descrição (telecom) e marcador "UF" (tb1875 e tb14) são tratados na leitura e registrados como aviso.

## 11.2 Ordem

| Passo | O que carrega | Depende de |
|---|---|---|
| 1 | As 86 entradas de `Cad_Tabela_Oficial` | — |
| 2 | `Cad_Obrigacao_Acessoria` (SPED_FISCAL e SPED_CONTRIBUICOES) e `Cad_Feriado` com os feriados bancários | — |
| 3 | UF e países (conferência e carga), municípios (conferência contra o IBGE), CFOP (tb15236), serviços (conferência) | 1 |
| 4 | Domínios de `Cad_Classe_Sistema`: os 5 existentes e os 14 novos | 1 |
| 5 | `Cad_Cst` (PIS, Cofins, IPI e ICMS com a origem separada) | 4 |
| 6 | Naturezas da receita, NCM e alíquotas; `Cad_Cprb_Atividade`; benefício de PIS/Cofins | 3, 4 e 5, e da NCM e do Ex da TIPI já carregados |
| 7 | Códigos de receita (raiz, depois os de 6 dígitos) | 1 |
| 8 | `Cad_Cest` (código, segmento, vigência) | 4 |
| 9 | Versões de leiaute, prazos de entrega e decadência | 2 |
| 10 | Receitas e deduções, faixas de consumo, ajuste de base, produto ANP, uso de CFOP | 3 e 4 |

## 11.3 Versionamento

Cada carga grava em `Mov_Carga_Tabela_Oficial` a `Versao_Publicada` (o N do cabeçalho), o hash, a codificação e as contagens. Cada linha carregada vira uma versão do cadastro de destino, com `Vigencia_Inicio` e `Vigencia_Fim` iguais às do arquivo e `Motivo_Vigencia` dizendo a versão do arquivo ("carga inicial, versão 38"). Os números das versões de hoje estão na aba Inventário.

## 11.4 Quando a vigência de uma linha termina

A linha nunca é apagada. O registro mais antigo vira versão encerrada, com `Vigencia_Fim` igual ao `DT_FIM` do arquivo, e deixa de poder ser usado em documento novo a partir do dia seguinte, mas continua valendo para o que já foi emitido e para a retificação. Quando o fim vem com sucessor (um código novo no lugar do antigo), o vínculo vai para a tabela de sucessão que o cadastro já tem (por exemplo `Cad_CFOP_Sucessao` e `Cad_Cst_Sucessao`). O sistema avisa o usuário dos itens em uso cuja vigência termina dentro de um prazo de antecedência configurável (parâmetro). Os casos reais mais próximos de hoje: o código 102 (óleo diesel) por unidade, encerrado em 31/05/2026; as linhas 150 a 153 de `PROD_MONO_ALIQ_DIFER`, em 31/12/2026; o Perse, em 28/02/2027.

## 11.5 Rotina de atualização com conferência de versão

A rotina é a do mecanismo existente (automática ou por arquivo manual), com estas conferências antes de aplicar:

| Situação encontrada | O que a carga faz | Status |
|---|---|---|
| Versão do cabeçalho maior que a carregada | Compara linha a linha e aplica | processada |
| Versão igual e hash igual | Nada a fazer; registra a consulta | processada |
| Versão igual e hash diferente | Não aplica; o arquivo mudou sem trocar de versão | com_pendencia |
| Versão menor que a carregada | Não aplica | rejeitada |
| Colunas diferentes das esperadas | Não aplica; o leiaute da tabela mudou | rejeitada |
| Linha nova (chave inexistente) | Inclui como versão nova, com a vigência do arquivo | processada |
| Mesma chave e mesmo `DT_INI`, só o texto mudou | Correção: nova versão desde a data da carga, com `Motivo_Vigencia` "correção da fonte" | processada |
| Mesma chave, `DT_FIM` novo | Encerra a versão | processada |
| Linha que existia e sumiu do arquivo | Não apaga; marca para decisão | com_pendencia |
| Linha que o usuário editou à mão | Não sobrescreve; a edição do usuário é a versão mais nova | com_pendencia |
| Início no futuro (por exemplo leiaute 1.20 em 2027) | Grava como versão futura, sem efeito antes da data | processada |

A fonte das tabelas do ICMS/IPI é a página de tabelas externas do portal do SPED (o resumo do Guia cita sped.rfb.gov.br/pagina/show/1578); para o Contribuições a fonte não aparece nos materiais (P43-01). Enquanto a busca automática não existir, a carga é por arquivo manual.

# 12. Pendências e divergências

## 12.1 Pendências

Numeradas P43-n para não colidir com as do documento 38; a numeração definitiva vem na consolidação.

| Nº | Assunto | O que falta | Quem ou onde | Prioridade |
|---|---|---|---|---|
| P43-01 | Guia Prático da EFD-Contribuições | Nenhum manual do Contribuições está entre as fontes: o documento 37 trata da EFD ICMS/IPI. Os arquivos não trazem o número da tabela do Guia (4.3.x) de cada um, e o mapeamento arquivo-tabela feito aqui é pelo conteúdo. | Alberto envia o Guia; confirmo o número de cada tabela e os usos de cada CFOP | Alta |
| P43-02 | Significado dos indicadores do Contribuições | P e R nas alíquotas de OUTROS_ALIQ_DIFER (a hipótese é regime cumulativo e não cumulativo, não confirmada), IND_AJUSTE (P e N), IND_ATIV (01 a 06), TIPO_DEDUC (G e E), IND_OUTROS (S e N) e os valores de OBRIGA_DET. | Guia do Contribuições (P43-01) | Média |
| P43-03 | CEST: descrição e NCM de cada código | tb16643 traz código e vigência, mas as 1.038 descrições vigentes são um aviso, e o arquivo não relaciona CEST a NCM. A carga cobre código, segmento e vigência. | Convênio ICMS 142/18 (anexos por segmento) | Alta |
| P43-04 | Tabelas 5.1.1 por UF e demais tabelas do Guia da EFD ICMS/IPI | tb1875 só tem os códigos genéricos (UF + tipo + natureza + 9999). Faltam os códigos de cada UF e as tabelas 5.2, 5.3, 4.5.4, 5.6, 5.7, 5.8 e 5.9.1 (já pedidas no documento 38). Ajustes de IPI também não constam. | Portal do SPED, tabelas externas da EFD ICMS/IPI | Alta |
| P43-05 | Onde se aplicam tb1316, tb14 e tb13957 | tb1316 é lista de códigos de receita de ICMS (campo de uso não confirmado); tb14 tem o nome "ajustes" mas traz tipos de utilização de crédito; tb13957 lista produtos de usina (provável controle de produção de usina, não confirmado). | Guia da EFD ICMS/IPI | Baixa |
| P43-06 | Países: ligar Bacen, ISO e Siscomex | PAISES (Bacen) tem 250 nomes e só 224 coincidem com a lista ISO do anexo A da NFS-e nacional; os demais diferem na grafia ("ALBANIA, REPUBLICA DA"). Falta fonte que traga os dois códigos na mesma linha. | Tabela de países do Bacen e tabela 6 do eSocial | Média |
| P43-07 | Município 5101837 (Boa Esperança do Norte) | Está nos dois arquivos, com início em 29/01/2025 no Contribuições e em 01/01/2025 no ICMS/IPI, e não está no anexo A de 10/12/2025 da NFS-e nacional. Os 5.570 do anexo estão todos nos arquivos. | IBGE: confirmar a data de instalação | Baixa |
| P43-08 | Arquivos possivelmente atrasados | DATA_LIMITE_ENTREGA não tem competência depois de 06/2026 (hoje é 06/10/2026, faltam 07, 08 e 09/2026) e o óleo diesel (código 102, por unidade) não tem linha vigente depois de 31/05/2026. | Baixar versão mais nova dos dois arquivos | Alta |
| P43-09 | Prorrogação de 2020 | As competências 02, 03 e 04/2020 têm a mesma data limite (14/07/2020); a regra dos dez dias úteis daria 15/04, 15/05 e 15/06. O arquivo não cita o ato. | Contador confirma o ato | Baixa |
| P43-10 | Ex da TIPI sem NCM claro | PROD_ALIQ_ZERO, código 309, traz "01" em NCM_EX (parece um Ex na coluna errada); PROD_MONO_ALIQ_UNID tem 1 linha com EX_IPI e sem NCM; 17 linhas trazem EX_IPI com mais de uma NCM, sem dizer a qual NCM o Ex pertence. | Conferir contra Cad_NCM_Ex_Tipi na carga; levar à Receita se persistir | Média |
| P43-11 | Fim da EFD-Contribuições | O documento 10 cadastra SPED_CONTRIBUICOES com fim esperado por volta de 2033, "sem confirmação"; o documento 32, citando fonte secundária, diz que a escrituração de apuração acaba em 31/12/2026 e fica só o controle de créditos; o documento 10 também diz que PIS/Cofins se extingue em 2027. Nenhuma data é oficial nas fontes. | Ato da Receita; até lá, nenhuma tabela é desativada por data fixa (D-N80) | Média |
| P43-12 | Tratamento dos CSOSN 300, 400 e 500 e do código composto | No arquivo, os três CSOSN terminam em 31/12/2012 e os números passam a significar origem + CST 00; o documento 10 lista os CSOSN como vigentes. Proposta em D-N78. | Contador valida a separação em origem e CST | Alta |
| P43-13 | Regra de decadência | Observada em DATA_LIMITE_ENTREGA (150 de 150): 31/12 do quinto ano depois do ano do prazo. Fundamento legal e base de contagem (D-N77) a validar; entra provisória. | Contador | Média |
| P43-14 | Indicadores do CFOP | Os arquivos trazem código, texto e vigência, mas não os indicadores de Cad_CFOP (NF-e, comunicação, transporte, devolução, retorno, anulação, remessa, combustível, exclusivo IBS/CBS). Eles continuam vindo da tabela de CFOP do Portal da NF-e. | Tabela de CFOP do Portal da NF-e (documento 38, seção 5) | Média |
| P43-15 | Feriados bancários para o cálculo do prazo | A regra dos dez dias úteis só fecha (147 de 150) contando os feriados bancários do Banco Central, inclusive Carnaval e Corpus Christi. Cad_Feriado tem Feriado_Bancario e a carga anual do Bacen; falta confirmar que as datas de 2014 a 2026 estão carregadas. | Conferir a carga de Cad_Feriado | Média |

## 12.2 Divergências achadas nas fontes

| Nº | Assunto | O que divergiu | Fonte | Tratamento |
|---|---|---|---|---|
| V1 | Identidade da natureza da receita | Cad_Natureza_Receita_Pis_Cofins tem Codigo (3) como identidade, mas o mesmo código existe em até nove tabelas (93 dos 574 códigos distintos repetem) e há códigos de 6 dígitos. | Documento 10 e arquivos de NCM por tratamento | Identidade = grupo + código (D-N75) |
| V2 | CST do ICMS com origem embutida | O arquivo CST_ICMS usa 3 dígitos (origem + CST) e reaproveita 300, 400 e 500 do Simples; o documento 10 grava "060" como código do ICMS e lista CSOSN 300, 400 e 500 como vigentes. | Documento 10 e CST_ICMS | Separar origem e CST (D-N78) |
| V3 | Dígito verificador do município | Nove municípios do anexo A do IBGE não cumprem a regra de Cad_Municipio.Codigo_IBGE (2201919, 2201988, 2202251, 2611533, 3117836, 3152131, 4305871, 5203939 e 5203962). | Dicionário e anexo A da NFS-e | Avisar em vez de rejeitar (D-N78) |
| V4 | Códigos de ajuste do ICMS | O documento 33 junta Difal e FCP em Tipo_Apuracao e não prevê o controle extra-apuração (UF099999); tb1875 separa Difal e FCP desde 2017. | Documento 33 e tb1875 | Ajustar a proposta do documento 33 |
| V5 | O que o documento 37 cobre | O documento 37 resume o Guia da EFD ICMS/IPI; não há manual da EFD-Contribuições entre as fontes. | Documento 37 | P43-01 |
| V6 | NCM_EX e EX_IPI | NCM_EX é lista de NCMs excluídos (6 linhas em 4 arquivos) e EX_IPI é o número do Ex da TIPI (113 linhas); em um caso (PROD_ALIQ_ZERO, 309) NCM_EX traz "01", que parece um Ex. | Arquivos de NCM por tratamento | P43-10 |
| V7 | Bebidas frias | O documento 10 cita a tabela 4.3.10 para bebidas frias; no arquivo elas estão em PROD_MONO_ALIQ_UNID, com códigos de 6 dígitos e alíquota em reais por litro. | Documento 10 e PROD_MONO_ALIQ_UNID | D-N75 |
| V8 | Defeitos de arquivo | DCTF PIS 810908 sem "SCP"; GRUPOS_RECEITAS 100 e 700 com a mesma descrição; grupo 800 de deduções fora de GRUPOS_DEDUCOES; COD_REC_P200 com "mensal" e "Mensal"; DCTF com periodicidade "-" e "Diária"; CONSUMO_TELECOM com ";21;22" na descrição e sem cabeçalho; CONSUMO_ENERGIA com dois espaços de código; SERVICO_LCP_116 com cada item duplicado (com e sem ponto) e aspas no 15.08; ANP com coluna DESC_AJUR; CS_APUR com coluna "cod da contribuicao"; nome do arquivo e cabeçalho com versões diferentes em CONSUMO_ENERGIA (4 e 2.0), COD_ENQ (2 e 1.0) e CONSUMO_TELECOM (2 e sem cabeçalho). | Arquivos | Carga normaliza e registra aviso |
| V9 | Duas versões da mesma tabela | CFOP: versão 9 no Contribuições e 14 no ICMS/IPI. Municípios: 10 e 20. Em ambos, a do ICMS/IPI é a mais nova e a do Contribuições não acrescenta nada. | GLOBAL_CFOP x tb15236; GLOBAL_MUNICIPIOS x tb16896 | Carregar só a do ICMS/IPI (D-N76) |
| V10 | Linhas com fim em 2027 ou depois | Perse (PROD_ALIQ_ZERO 920 e BENEFICIOS_FISCAIS 060) até 28/02/2027; OUTROS_ALIQ_DIFER 921 até 31/12/2027; 56 competências de DATA_LIMITE_ENTREGA com DT_FIM em 2027 a 2031. Para PIS/Cofins, o documento 10 diz extinção em 2027. | Arquivos e documento 10 | Guardar a vigência como publicada; P43-11 |
| V11 | ID_Nomenclatura em Cad_Cprb_Atividade | O campo aponta a nomenclatura (NCM como um todo), e COD_ATV é o código NCM de 8 dígitos; NCM_ATV vem vazio nas 10.085 linhas. | Dicionário e COD_ATIVIDADE | Campo ID_Classificacao (D-N78) |
| V12 | DT_FIM de DATA_LIMITE_ENTREGA | Não é o fim da vigência do prazo: é 31/12 do quinto ano depois do ano do prazo em 150 de 150 linhas, ou seja, o horizonte de decadência. | DATA_LIMITE_ENTREGA | D-N77 |

# 13. Decisões para Alberto

A numeração segue a D-N51 e usa D-N73 a D-N80; as D-N52 a D-N72 ficam reservadas a outros documentos.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N73 | Cabeçalho e carga: reaproveitar `Cad_Tabela_Oficial` e `Mov_Carga_Tabela_Oficial` para as 86 tabelas (uma entrada por tabela, com versão publicada, hash e codificação), em vez de criar `Cad_Efd_Tabela_Externa`? | **Sim.** O mecanismo de carga, a proteção da edição do usuário e o status da carga já existem; criar uma segunda estrutura duplicaria. |
| D-N74 | Listas simples de código e descrição (13 tabelas e a coluna IND_ATIV) entram como 14 novos domínios de `Cad_Classe_Sistema`, sem entidade genérica de itens; as tabelas que já têm domínio (BC_CRED, TIPO_CRED, CS_APUR, MODELOS e o 1º dígito de CST_ICMS) só recebem linhas? | **Sim.** `Cad_Classe_Sistema` já tem vigência, extensão sem nova tabela e o padrão de FK por domínio. Entidade própria só onde há atributo, relação ou hierarquia. |
| D-N75 | NCM por tratamento: a identidade da natureza da receita passa a ser grupo mais código (código até 6), `Cad_Natureza_Receita_Pis_Cofins_Classificacao` ganha `Tipo_Vinculo` e `ID_Ex_Tipi`, e as alíquotas vão para `Cad_Natureza_Receita_Pis_Cofins_Aliquota`, provisórias até o contador validar? | **Sim.** Sem isso, o código 101 (nove tabelas) e os 307 códigos de bebidas frias (1.139 linhas) não cabem, e as alíquotas por unidade ficam sem lugar. |
| D-N76 | CFOP: carregar `Cad_CFOP` só pela tb15236 (EFD ICMS/IPI, versão 14), descartar a do Contribuições e guardar os usos do Contribuições em `Cad_CFOP_Uso_Efd_Contribuicoes`? O mesmo vale para municípios (tb16896) e a lista de serviços (a de 2015)? | **Sim.** As listas vigentes de CFOP são idênticas (619 códigos), as de municípios diferem só no 9999998 e a de serviços de 2015 tem os 200 subitens; a do ICMS/IPI é mais nova. Isto resolve o item "tabela de CFOP" da seção 5 do documento 38, no que toca a códigos, textos e vigência; os indicadores seguem pendentes (P43-14). |
| D-N77 | Prazo de entrega e decadência como parâmetros com vigência: `Cad_Obrigacao_Prazo_Entrega` (data publicada por competência, que vale mais que o cálculo), `Cad_Obrigacao_Decadencia` (5 anos, base de contagem) e `Cad_Obrigacao_Leiaute_Versao`, mais o campo `ID_Obrigacao` em `Cad_Regra_Vencimento`? | **Sim.** A regra dos dez dias úteis acerta 147 de 150 competências; as 3 exceções (2020) são prorrogações e entram como `ato_manual`. Tudo provisório até o contador validar. |
| D-N78 | Correções em entidades existentes: CST do ICMS separado em origem (domínio) e CST/CSOSN (`Cad_Cst`); aviso, e não rejeição, no dígito verificador de 9 municípios; `ID_Classificacao` em `Cad_Cprb_Atividade`; `ID_Produto_Anp` no produto; descrição do CEST vinda do convênio? | **Sim.** São correções de colisão (CSOSN 300/400/500) e de tipo de referência, todas sem perda de dado. |
| D-N79 | Criar as 11 entidades novas (alíquota de natureza, uso de CFOP, faixa de consumo, ajuste de base, receita e dedução com sua atividade, produto ANP, benefício de PIS/Cofins, prazo de entrega, versão de leiaute e decadência) já na carga inicial, mas sem tela nem geração de registro até haver cliente que precise? | **Sim.** A carga é barata, a regra legal é parâmetro com vigência e o ERP não limita o tipo de cliente. O que fica de fora é só o desenvolvimento de telas e de registros (receitas e deduções, faixas de consumo). |
| D-N80 | Rotina de atualização: conferir a versão do cabeçalho e o hash antes de aplicar; nunca apagar linha (fim de vigência vira `Vigencia_Fim`); linha que some do arquivo novo vira pendência; nenhuma tabela do Contribuições é desativada por data fixa, e a atualização dela só para quando a Receita parar de publicar? | **Sim.** Mantém o histórico para retificar períodos dentro dos 5 anos (documento 10), respeita a edição do usuário e não depende de data que as fontes ainda não confirmam (P43-11). |

**Posso consolidar?**
