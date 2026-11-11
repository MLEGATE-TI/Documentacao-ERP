# Desenho da NFCom (Modelo 62) contra o Dicionário — Documento 40

*Leitura do pacote da Nota Fiscal Fatura de Serviços de Comunicação Eletrônica que Alberto enviou em 05/10/2026 (sete pacotes de schemas v1.00, NT 2026.004, MOC Anexo II do DANFE-COM e a Instrução Técnica 2025.002 v1.70 com a tabela cCredPres) e o que ele pede do dicionário. Este documento é um relatório: não altera o dicionário. Revisão 2 em 11/10/2026, com o MOC v1.00a.*

Mlegate · Alberto Beyeler · Outubro de 2026

> **Nota de 13/10/2026.** Por decisão de Alberto (D-N141, documento 60), a NFCom e a NFAg ficam só como **entrada**: o desenho de emissão deste documento (`Mov_Nfcom` e entidades filhas) fica como **reserva**, sem uso por ora, e a entrada está no **documento 60**. Os números e as propostas abaixo não mudam.

# Revisão 2 — MOC v1.00a (11/10/2026)

Chegaram o Anexo I (leiaute e regras de validação, 38 páginas) e a Visão Geral (59 páginas) do MOC da NFCom, ambos na versão **1.00a, de janeiro de 2023**. Eles são anteriores a todas as Notas Técnicas do pacote que o documento tomou por base, e por isso só confirmam o leiaute-base: **99 das 326 linhas** (59 da NT 2025.001, 11 da 2026.002, 9 da 2026.004, 7 da 2024.002, 5 da 2024.001, 5 da 2026.001 e 3 do leiaute-base: `indNotaEntrada`, `cPais` e `xPais`) não existem nele. Onde o MOC diverge do schema, vale o schema. A classificação das 326 linhas não mudou de situação (123 cobertas, 69 propostas dos documentos 33 e 34, 44 derivadas, 13 só no XML, 7 de campo novo e 70 de entidade nova); mudam o destino e a condição de algumas. Esta revisão não altera o dicionário e substitui, onde houver conflito, o texto das seções 2, 3, 5 e 10 a seguir.

## Pendências

| Nº | Estado | O que o MOC resolveu |
|---|---|---|
| P40-01 | Parcial | Domínios: `tpFat` 0, 1 e 2; `tpAssinante` 1 a 8 e 99, com a base legal de cada um; `tpServUtil` 1 a 7; `uMed` minuto, MB, GB e UN; `finNFCom` 0, 3 e 4; `motSub` 01 a 05; `tpRessarc` 1, 2 e 99; `tpProc` sefaz, justiça federal e justiça estadual. Abertos: o `motSub` 06 existe na tabela do Anexo e não na descrição; e **a tabela `cClass` não veio** (só a regra de sinal: código iniciado por 5 deduz, por 0 soma). |
| P40-02 | Parcial | Contingência (só off-line, `tpEmis` 2, só para nota normal), prazos e eventos. Não resolvido: URLs dos serviços (só o portal nacional) e nada sobre São Paulo. |
| P40-03 | Aberta | O MOC é anterior ao vínculo de pagamento. |
| P40-04 | Aberta | Não há `vTotDFe` nem IBS/CBS. O `vNF` é o `vProd` menos retenções (G137) e ICMS, PIS e COFINS não são somados: indício a favor da leitura da introdução da NT 2026.004, sem prova. |
| P40-05 | Aberta | Sem a regra 434, sem as regras 409 e 410 e sem `cMunPrinc`. Há G36a e G36b: a UF do terminal tem de ser a UF de autorização. |
| P40-06 | Parcial | Emitente: só o evento 110111. Fisco: 240140, 240150, 240151, 240160, 240161, 240162 e 240170. Consulta de situação definida (180 dias). **Não existe evento de cancelamento por substituição**: substituir é emitir nova nota (`finNFCom` 3) e o Fisco marca a original. Não há distribuição por NSU. |

## Regras de validação

O Anexo I traz **152 regras** (141 obrigatórias e 11 facultativas por UF) e a Visão Geral mais 70, 222 no total. Nenhum cStat coincide com as 15 regras da NT 2026.004: só três tratam da mesma grandeza (1050, 1054 e 365 contra G86, G136 e G137) e as outras 12 são novas. Proponho **35 parâmetros com vigência** em `Cad_Dfe_Parametro_Regra`, entre eles os prazos (atraso de emissão 120 horas, substituição 5 anos, contingência até o fim do primeiro dia útil seguinte, cancelamento 120 horas com texto ambíguo, consulta 180 dias, chave antiga 6 meses, status a cada 3 minutos), os limites (5 minutos de tolerância, R$ 0,05 no item, R$ 0,10 nos tributos, 1.024 KB, 990 itens, limites de ICMS e de `vNF` por UF) e as listas (UF que não aceitam isento: AM, BA, CE, GO, MG, MS, MT, PE, RN, SE e SP; 18 CFOP; URLs de QR Code por UF; tabela `cClass`; municípios; data de obrigatoriedade por UF, G56).

**O D-N70 (documento 42) precisa de duas extensões:** `ID_Estado` opcional e `Aplicacao` {obrigatoria, facultativa_por_uf}, mais unidade em dia útil. Sem isso não cabem G56, G110 e G138 nem as 11 regras facultativas por UF.

## Entidades: o que muda

As sete entidades da seção 5 ficam; mudam as regras e uma entidade nova entra:

| Entidade | Mudança |
|---|---|
| `Cad_Nfcom_Classificacao_Servico` (nova, **oitava**) | O `cClass` deixa de ser domínio de `Cad_Classe_Sistema` e vira catálogo com vigência: código de 7 dígitos, descrição, `Natureza_Valor` {soma, deducao}, `Indicador_Pre_Pago`, `Indicador_Faturamento_Centralizado`, `Indicador_Cofaturamento`, `Indicador_Ressarcimento` e `Indicador_Tributavel`. O `cClass` dispara as regras G87 a G98 e o grupo de ressarcimento, e as 31 linhas de totais dependem dele e do `indDevolucao`. `Mov_Nfcom_Item.ID_Classificacao_Servico` passa a apontar para ele. |
| `Mov_Nfcom` | Sem campo novo. `Indicador_Pre_Pago` deriva dos itens (G87); `Indicador_Cessao_Meios_Rede` só em nota normal ou de substituição com `tpFat` 0 e dispensa a fatura; `Cnpj_Centralizador` com o mesmo CNPJ-base (G82); os quatro campos de fidelidade são tudo ou nada. `Indicador_Nota_Entrada` e `Tipo_Pagamento_Antecipado` não têm definição no MOC. |
| `Cad_Nfcom_Assinante` | `Codigo_Assinante` com até 30 posições (o MOC diz 15; vale o schema). Contrato e data de início obrigatórios quando `tpFat` for 0 ou 1 (G34a); terminal principal de 7 a 12 dígitos e UF igual à UF de autorização. |
| `Mov_Nfcom_Fatura` | 0 ou 1 por nota: obrigatória com `tpFat` 0 (exceto pré-pago e cessão de meios de rede), proibida em ajuste e cofaturamento; no faturamento centralizado a nota leva `gFatCentral` no lugar. |
| `Mov_Nfcom_Item` | `Cnpj_Operadora_Ld` obrigatório se o `cClass` for de cofaturamento e proibido nos demais (G96 a G98); grupo de ressarcimento só em `cClass` de ressarcimento. |
| `Mov_Nfcom_Item_Processo_Numero` | `Tipo_Processo` ganha o domínio {sefaz, justica_federal, justica_estadual}, de 1 a 10 por item. |
| Fora das sete | Protocolo de **16 posições** (o campo da nota é "até 15"); CFOP opcional no item sem CST (obrigatório com CST, proibido sem, G105a e G105b) e `Cad_CFOP.Indicador_Nfcom` para a lista de 18 CFOP; `finNFCom`: o dicionário já tem normal e ajuste e falta o valor `substituicao` (0, 3 e 4 são código do XML, não valor do domínio); `idOutros` aceita RG, não só NIF, de 2 a 20 posições, sem IE (G24); sete tipos novos de evento do Fisco em `Mov_Dfe_Evento`, e o ERP consulta antes de oferecer o cancelamento (bloqueado se a nota for de substituição ou estiver referenciada por ajuste ou cofaturamento autorizado, L07 a L09). |

## Visão Geral e modelagem nova

O **DANFE-COM é gerado, não gravado**: sempre com QR Code, protocolo com data e hora, e "EMITIDA EM CONTINGÊNCIA" quando for o caso. A **contingência** é só off-line e só para nota normal; a retransmissão mantém a chave e o `cNF`; o QR Code leva o `sign`. O **assinante** é identificado por CNPJ, CPF ou `idOutros`; no `idOutros` a IE vai vazia (há conflito sobre CNPJ com zeros para estrangeiro). **Faturamento centralizado e cofaturamento** o MOC define pelas regras G67 a G98, não por texto: a nota `tpFat` 1 é emitida pelo estabelecimento que presta o serviço, com tributação e sem fatura, apontando o centralizador (mesmo CNPJ-base); o centralizador emite a nota `tpFat` 0 com itens de `cClass` centralizado, sem tributação, cada um referenciando a nota anterior; no cofaturamento a operadora de longa distância emite `tpFat` 2 apontando a nota da operadora local. Os **serviços** do modelo 62 são autorização, consulta de situação, status e evento; não há inutilização nem distribuição por NSU, então `Mov_Dfe_Inutilizacao` e `Mov_Dfe_Distribuicao` não se aplicam ao modelo 62 nesta versão.

## Correções ao texto deste documento

1. Seção 2 e pendências: o Anexo I e a Visão Geral foram enviados (acima).
2. Seção 3: os eventos são **dez** (três do emitente e sete do Fisco), não três.
3. Seção 5: a finalidade "com os valores 0, 3 e 4" é código do XML; no dicionário entra só o valor `substituicao`; e `Mov_Nfcom_Item.ID_Classificacao_Servico` aponta para o catálogo próprio.
4. Seção 6, NT 2024.002: a substituição já tinha a competência de emissão e o hash do Convênio 115 no leiaute-base; a NT só os estendeu ao cofaturamento e criou o indicador de nota anterior em papel.
5. Seção 4: `idOutros` aceita RG; o protocolo tem 16 posições; o máximo é 990 itens (o schema dizia 9990 até a NT 2024.002); o tempo de contingência é o fim do primeiro dia útil seguinte.
6. D-N57 ("carregar os domínios só com o código até o MOC chegar") está cumprida em parte: os significados já podem ser carregados; só o `cClass` e o `motSub` 06 ficam sem descrição.

## Dúvidas novas (Q-N1 a Q-N11)

Há MOC mais novo ou só os textos das NTs (99 linhas dependem disso)? Alberto pode exportar do portal nacional a tabela `cClass`, as URLs e o WSDL por UF, a tabela de CFOP e a IT DFe 2026.001 (o acesso do ambiente foi bloqueado)? São Paulo autoriza a NFCom sozinho ou pela SEFAZ Virtual RS? "120 horas do mês anterior" (L11) é prazo da autorização ou corte no mês? Divergências internas do MOC: ano da chave 2022 ou 2021, G65 com `tpFat` 1 para "normal", produção em 05 ou 06/2023. Destinatário estrangeiro: CNPJ com zeros ou validado (ER9 contra G22)? Significado de `indNotaEntrada`, `tpPagAnt`, `cMunFG` e `motSub` 06. A Mlegate teria assinantes fora da UF do emitente (G36a e G36b)? O cadastro do assinante é vivo ou cópia do momento da emissão? A inscrição tipo 4 existe em `Cad_Participante_Inscricao` (exceção de G03)? Qual calendário de dias úteis vale para a contingência? Detalhe: abas "Rev2" do anexo e documento 44, decisão **D-N91** (`cClass` como catálogo, UF e marca facultativa no D-N70, schema acima do MOC).

# 1. Resumo

O pacote traz **326 linhas de leiaute** (campos, atributos e grupos, das quais 13 são da assinatura digital). O dicionário já cobre **123** delas, **69** estão cobertas pelas propostas dos documentos 33 e 34 (IBS/CBS por item, substituição, cofaturamento, compra governamental, pagamento antecipado e vínculo com o pagamento), **44** são calculadas na emissão, **13** só existem no XML assinado, **7** pedem campo novo em entidade existente e **70** pedem entidade nova. O modelo 62 é, portanto, um caso de **reaproveitamento**: o que é próprio da telecomunicação (assinante, fatura, ressarcimento, processo referenciado, pontos de fidelidade) cabe em **sete entidades novas**, e o resto entra nas entidades da NF-e de saída que o documento 34 já propôs.

**Cinco pontos que mudam o desenho.** Primeiro, a NFCom é uma **nota de saída** (`Mov_Nota_Fiscal_Saida` e `Mov_Nota_Fiscal_Saida_Item`) com uma extensão 1:1 `Mov_Nfcom`, no mesmo padrão que o documento 42 propõe para o CT-e. Segundo, o **assinante** é o contrato da Gestão de Contratos acrescido de código, tipo, serviço e terminais: vira `Cad_Nfcom_Assinante`, ligado a `Cad_Gestao_Contrato` e a `Cad_Participante`. Terceiro, a **fatura** do documento (competência, vencimento, linha digitável, débito automático e QR Code do PIX) é entidade própria ligada ao título de contas a receber. Quarto, a **NT 2026.004** fixa datas e alíquotas de transição de 2026 a 2028, que devem entrar como parâmetros com vigência (homologação 13/10/2026 e produção 16/11/2026; ICMS previsto do pagamento antecipado em 01/02/2027 e 01/03/2027). Quinto, a Instrução Técnica 2025.002 v1.70 traz **indicadores oficiais** das tabelas de CST e de classificação tributária e o **catálogo de 13 códigos de crédito presumido** (cCredPres), que o dicionário não guarda; a decisão sobre os indicadores já foi proposta no documento 41 (D-N62) e o catálogo de crédito presumido no documento 42, e aqui só aponto o que a NFCom usa.

**O que ficou fora.** *(Superado pela Revisão 2: o Anexo I e a Visão Geral do MOC chegaram em 11/10/2026; o resto do parágrafo vale.)* O **Anexo I do MOC da NFCom** (leiaute e regras de validação, com o significado dos códigos) e a **Visão Geral** não foram enviados. Por isso os domínios do schema (tipo de faturamento, de assinante, de serviço utilizado, unidade de medida, motivo de substituição, tipo de ressarcimento) entram só com o código, e a tabela de classificação do item (`cClass`, sete posições) fica como domínio vazio. Também faltam a IT DFe 2026.001 (meios de pagamento) e as URLs dos serviços.

# 2. Fontes lidas e o que cada uma permitiu

| Fonte enviada | Versão | Uso |
|---|---|---|
| Schemas `PL_NFCOM_1.00` de sete Notas Técnicas | v1.00 (NT 2023.002 rev 1.01, 2024.001, 2024.002 rev 1.00, 2025.001 RTC 1.14, 2026.001 RTC vínculo de pagamento 1.01, 2026.002 RTC 1.01 e 2026.004 RTC 1.00) | Todos os campos, versão em que cada um entrou e os três eventos |
| Nota Técnica 2026.004 RTC, versão 1.00 (setembro de 2026) | v1.00 | Valores líquidos, ICMS previsto, alíquotas 2026 a 2028, doação, total geral, município do terminal e cronograma |
| MOC NFCom, Anexo II, DANFE-COM | v1.00 | Impressão do documento (conferência dos campos que o DANFE mostra; sem efeito novo no dicionário) |
| IT 2025.002 v1.70 (PDF e planilha cCredPres) | v1.70 | Tabelas de CST, classificação tributária e crédito presumido, com os indicadores por modelo |
| Não enviados | | MOC NFCom Anexo I e Visão Geral; IT DFe 2026.001; schemas de consulta de distribuição |

# 3. Framework e modelo 62

A decisão D-N6 definiu o framework de documentos fiscais eletrônicos (cadastro de modelo, configuração do emitente, autoridade, ambiente, contingência e eventos, desenhado nos documentos 33 e 34) e a D-N51 fixou que o modelo 77 (NF-e ABI) entra só como linha de cadastro mais o campo do site autorizador. A NFCom segue a mesma linha, mas com conteúdo, porque a D-N24 pediu para antecipar NFAg e NFCom e o pacote chegou completo.

| Ponto | Tratamento proposto |
|---|---|
| Modelo | Linha nova `62` no domínio de modelo de documento fiscal de `Cad_Classe_Sistema`, com versão de leiaute 1.00 e as marcas de IBS/CBS por modelo |
| Chave de acesso | 44 posições, como a NF-e: UF, AAMM, CNPJ, modelo, série, número, tipo de emissão, **site do autorizador** (`nSiteAutoriz`) e código numérico, mais o dígito. O CNPJ alfanumérico entra pela mesma regra do documento 34. O campo `Mov_Documento_Fiscal.Site_Autorizador` serve à NFCom e à NF-e ABI |
| Emissão | Sempre síncrona (a autorização devolve o protocolo na própria resposta); contingência `tpEmis` 1 (normal) e 2 (contingência), tratada por `Mov_Dfe_Contingencia` |
| Eventos | Três: 110111 cancelamento, 110300 vinculação do pagamento e 110301 cancelamento da vinculação, todos em `Mov_Dfe_Evento` |
| Documento e extensão | `Mov_Nota_Fiscal_Saida` e `_Item` guardam o comum; `Mov_Nfcom` e `Mov_Nfcom_Item` guardam o que só a NFCom tem |
| Origem do faturamento | O assinante vem de `Cad_Gestao_Contrato`; o consumo do item vem de `Mov_Gestao_Contrato_Consumo` e `Mov_Gestao_Contrato_Medicao`; a fatura gera o título em `Mov_Titulo` |

# 4. Cobertura campo a campo

A tabela mostra as linhas do leiaute por área e por situação. A planilha anexa lista cada uma das 326 linhas com caminho, ocorrência, tipo, domínio, versão em que entrou e destino.

| Área | Linhas | Coberto | Proposta dos docs 33/34 | Derivado | Só no XML | Campo novo | Entidade nova |
|---|---|---|---|---|---|---|---|
| Identificação | 19 | 6 | 1 | 7 | 0 | 1 | 4 |
| Compra governamental e pagamento antecipado | 7 | 0 | 6 | 0 | 0 | 0 | 1 |
| Emitente | 17 | 17 | 0 | 0 | 0 | 0 | 0 |
| Destinatário (assinante) | 19 | 19 | 0 | 0 | 0 | 0 | 0 |
| Assinante | 11 | 0 | 0 | 0 | 0 | 0 | 11 |
| Substituição, cofaturamento e faturamento centralizado | 17 | 0 | 10 | 0 | 0 | 5 | 2 |
| Itens | 21 | 9 | 5 | 0 | 0 | 1 | 6 |
| ICMS | 41 | 37 | 1 | 3 | 0 | 0 | 0 |
| PIS, COFINS, FUST, FUNTTEL e retenções | 19 | 19 | 0 | 0 | 0 | 0 | 0 |
| IBS e CBS | 47 | 10 | 37 | 0 | 0 | 0 | 0 |
| Processo referenciado e ressarcimento | 23 | 0 | 0 | 0 | 0 | 0 | 23 |
| Vínculo com o pagamento | 5 | 0 | 5 | 0 | 0 | 0 | 0 |
| Totais | 31 | 0 | 0 | 31 | 0 | 0 | 0 |
| Fidelidade | 4 | 0 | 0 | 0 | 0 | 0 | 4 |
| Fatura | 19 | 0 | 0 | 0 | 0 | 0 | 19 |
| Demais grupos | 26 | 6 | 4 | 3 | 13 | 0 | 0 |
| **Total** | 326 | 123 | 69 | 44 | 13 | 7 | 70 |

**O que está coberto.** O emitente (17 linhas) vem de `Cad_Filial`, `Cad_Participante_Inscricao` e `Cad_Empresa_Perfil_Fiscal`. O destinatário (19 linhas) vem de `Cad_Participante` e `Cad_Participante_Endereco`; quem não tem CNPJ nem CPF usa `Cad_Participante_Documento_Fiscal` com tipo "outros" e NIF (P-18 do documento 34). O ICMS (41 linhas) usa `Mov_Apuracao_Tributo_Item` com CST, benefício fiscal, desoneração, FCP e partilha. PIS, COFINS, FUST e FUNTTEL (19 linhas, com as retenções) usam a mesma entidade, com **FUST e FUNTTEL como linhas novas de `Cad_Imposto`** (dado, não estrutura), e as retenções ficam em `Mov_Titulo_Retencao`.

**O que o documento 34 já propôs e a NFCom reaproveita.** O IBS/CBS por item (47 linhas) entra por `Mov_Apuracao_Tributo_Item` (CST, classificação, base, alíquota e valor) e por `Mov_Apuracao_Tributo_Item_Complemento` (diferimento, devolução, redução, zona de livre comércio, tributação regular, estorno de crédito e compra governamental: P-4). A substituição e o cofaturamento usam `Mov_Nota_Fiscal_Saida_Referenciada` (tipos `substituicao` e `cofaturamento`), a compra governamental usa `Mov_Nota_Fiscal_Saida_Compra_Governamental` (P-2), a nota de antecipação usa `Mov_Nota_Fiscal_Saida_Item_Referencia` (P-3b), o vínculo com o pagamento usa `Mov_Dfe_Vinculo_Pagamento` (P-13) e os autorizados a baixar o XML usam `Mov_Nota_Fiscal_Saida_Autorizado_Xml`. O valor líquido do item (NT 2026.004) usa `Valor_Unitario_Liquido` e `Valor_Total_Liquido` do P-14.

**O que é calculado.** Os 31 campos de totais e os campos da chave, da versão, do QR Code e da UF de emissão não são gravados: saem dos itens e da configuração. Os 13 campos da assinatura digital ficam só no arquivo XML assinado em `Mov_Documento_Fiscal`.

# 5. Entidades e campos propostos

As sete entidades abaixo são novas. Todas são propostas, e as colunas e ligações estão na planilha anexa, na aba "Entidades propostas".

| Entidade | Para que serve | Campos principais |
|---|---|---|
| `Mov_Nfcom` | Extensão 1:1 de `Mov_Nota_Fiscal_Saida`: tipo de faturamento (normal, centralizado ou cofaturamento), indicadores de serviço pré-pago, de cessão de meios de rede e de nota de entrada, tipo de pagamento antecipado, centralizador (CNPJ e UF) e pontos de fidelidade (saldo, resgate e datas) | Tipo_Faturamento, Indicador_Pre_Pago, Indicador_Cessao_Meios_Rede, Indicador_Nota_Entrada, Tipo_Pagamento_Antecipado, Cnpj_Centralizador, Saldo_Pontos, Pontos_Resgatados |
| `Cad_Nfcom_Assinante` | O assinante: código único, tipo, tipo de serviço, contrato e terminal principal (número, UF e município, este último exigido pela NT 2026.004) | Codigo_Assinante, Tipo_Assinante, Tipo_Servico_Utilizado, ID_Gestao_Contrato, Numero_Terminal_Principal, ID_Municipio_Terminal |
| `Cad_Nfcom_Assinante_Terminal` | Terminais adicionais, um por linha | Numero_Terminal, ID_Estado |
| `Mov_Nfcom_Fatura` | Fatura do documento: competência, vencimento, período de uso, linha digitável, débito em conta, endereço de correspondência e QR Code do PIX | Competencia, Data_Vencimento, Linha_Digitavel, Url_Qrcode_Pix, ID_Titulo |
| `Mov_Nfcom_Item` | Extensão 1:1 do item: classificação do serviço, unidade básica de medida, CNPJ da operadora de longa distância e da cobrança de terceiro, validade do crédito, devolução e ressarcimento (tipo, data, processo, protocolo e observação) | ID_Classificacao_Servico, Unidade_Basica_Medida, Cnpj_Cobranca_Terceiro, Tipo_Ressarcimento |
| `Mov_Nfcom_Item_Processo` | Valores do item **sem** a aplicação do processo judicial: quantidade, valor, desconto, ICMS, PIS, COFINS, FCP e, desde a NT 2026.004, base, IBS e CBS | Base_Icms, Valor_Icms, Base_Ibs_Cbs, Valor_Ibs_Uf, Valor_Cbs |
| `Mov_Nfcom_Item_Processo_Numero` | Números dos processos (tipo e número, vários por item) | Tipo_Processo, Numero_Processo |

**Campos novos em entidades existentes ou propostas.** `Mov_Documento_Fiscal.Site_Autorizador` (compartilhado com a NF-e ABI); `Mov_Nota_Fiscal_Saida_Referenciada.Competencia_Emissao`, `Hash_Convenio_115` e `Motivo_Substituicao` (seis códigos, o 06 criado pela NT 2026.002); `Mov_Nota_Fiscal_Saida_Item_Referencia.Indicador_Nota_Anterior_Papel`. **Linhas novas de dado:** modelo 62 no domínio de modelos; FUST e FUNTTEL em `Cad_Imposto`; finalidade da nota com os valores 0 (normal), 3 e 4; tipos de referência `substituicao` e `cofaturamento`; e os domínios de `Cad_Classe_Sistema` para tipo de faturamento, de assinante, de serviço utilizado, unidade básica de medida, tipo de processo e de ressarcimento.

# 6. Histórico dos schemas

O schema da NFCom é o mesmo arquivo `nfcom_v1.00.xsd` em sete versões. A tabela mostra o que cada Nota Técnica acrescentou e quantas linhas do leiaute atual entraram em cada uma.

| Nota Técnica | O que trouxe | Linhas que entraram |
|---|---|---|
| NT 2023.002 rev 1.01 | Leiaute base 1.00: identificação, emitente, destinatário, assinante, itens com ICMS, PIS, COFINS, FUST, FUNTTEL, retenções, fatura, totais, substituição, cofaturamento, faturamento centralizado, fidelidade, processo referenciado, ressarcimento, autorizados a baixar o XML, informações adicionais, responsável técnico e QR Code | 230 |
| NT 2024.001 | ICMS90 ganha desoneração, código de benefício e FCP; FCP no processo referenciado | 5 |
| NT 2024.002 | Substituição e cofaturamento com competência de emissão e hash do Convênio 115; indicador de nota anterior em papel no faturamento centralizado | 7 |
| NT 2025.001 (RTC 1.14) | Primeira versão da reforma tributária: grupos de IBS e CBS por item (CST, classificação, IBS UF e município, CBS, diferimento, devolução, redução, tributação regular, crédito presumido, zona de livre comércio), compra governamental e totais de IBS/CBS | 59 |
| NT 2026.001 (vínculo de pagamento 1.01) | Grupo de vínculo com o pagamento (meio de pagamento, recebedor, instituição, número e identificador da transação) e os eventos 110300 e 110301 | 5 |
| NT 2026.002 (RTC 1.01) | Tipo de pagamento antecipado, referência à nota de antecipação, chave do documento anterior da compra governamental, CNPJ de cobrança de terceiro, percentual de devolução do tributo, alíquota e valor efetivos sem redução da zona de livre comércio, inscrição Suframa | 11 |
| NT 2026.004 (RTC 1.00) | Valores líquidos do item e do total, ICMS previsto do pagamento antecipado, IBS e CBS no processo referenciado, município do terminal principal, regras de alíquota 2026 a 2028 e de doação, total geral do documento | 9 |

Essa história importa por um motivo prático: a emissão precisa escolher o schema pela **data de emissão e pelo ambiente**, não por uma versão fixa. O `Cad_Dfe_Leiaute` com vigência (D-N6) já cobre isso; o que a NFCom acrescenta é que **o mesmo número de versão (1.00) tem sete pacotes**, então a chave de vigência é o pacote da Nota Técnica, não só o número do leiaute.

# 7. NT 2026.004 (reforma tributária)

**Cronograma.** Homologação em **13/10/2026** e produção em **16/11/2026** para os valores líquidos do item e do total, o IBS e a CBS no processo referenciado, a regra do total geral e as regras de alíquota. O grupo de **ICMS previsto do pagamento antecipado** (`gICMSPrevistoPagtoAntecip`, regras 1051 a 1053) tem datas próprias: homologação em **01/02/2027** e produção em **01/03/2027**. A obrigatoriedade do município do terminal principal (regra 434) é "implementação futura", sem data.

**Regras com data ou valor que viram parâmetro** (nada disso entra em código):

| cStat | Regra | Data ou valor | Tratamento |
|---|---|---|---|
| 1050 | Valor líquido do item (vProdLiq) difere de vItemLiq x qFaturada | NT 2026.004 | Regra de cálculo da emissão |
| 1051 | Grupo do ICMS previsto no pagamento antecipado informado fora de compra governamental ou pagamento antecipado | Homologação 01/02/2027; produção 01/03/2027 | Validação condicionada a data (parâmetro com vigência) |
| 1052 | Grupo do ICMS previsto informado sem tpPagAnt 1 ou 2 e sem tpOperGov 4 | Homologação 01/02/2027; produção 01/03/2027 | Idem |
| 1053 | Grupo do ICMS previsto ausente quando tpPagAnt é 1 ou 2, ou tpOperGov é 4 | Homologação 01/02/2027; produção 01/03/2027 | Idem |
| 1054 | Total líquido (total/vProdLiq) difere da soma dos itens | NT 2026.004 | Cálculo derivado |
| 316 | Alíquota de IBS da UF: 0,1% em 2026 (art. 343 da LC 214); 0,05% em 2027 e 2028 (art. 344); depois, alíquota de referência ou específica da UF. Zero quando o cClassTrib tem indicador de tributação regular. Em homologação (tpAmb=2) aceita as alíquotas de 2026 e de 2027 | 2026 a 2028 | Parâmetro em Cad_Aliquota e Cad_Cronograma_Transicao_Tributaria |
| 321 | Alíquota de IBS do município: 0% em 2026; 0,05% em 2027 e 2028; depois, alíquota do município. Zero com indicador de tributação regular | 2026 a 2028 | Idem |
| 326 | Alíquota da CBS: 0,90% em 2026 (art. 346 da LC 214). Zero com indicador de tributação regular, ou em zona incentivada (Manaus 1302603, Rio Preto da Eva 1303569, Itacoatiara 1301902, e municípios pares das cinco áreas de livre comércio) quando o cClassTrib permite alíquota zero. Até a publicação da alíquota de referência de 2027 vale a de 2026 | 2026 | Parâmetro; lista de municípios em tabela com vigência |
| 1055 | Doação (indDoacao=1) com destinatário pessoa jurídica de mesmo CNPJ-base do emitente | NT 2026.004 | Validação |
| 1056 | cClassTrib com indicador que veda doação e indDoacao informado | NT 2026.004 | Depende do indicador do cClassTrib (D-N62 do documento 41) |
| 1057 | cClassTrib com indicador que exige doação e indDoacao ausente | NT 2026.004 | Idem |
| 365 | vTotDFe: em 2026 repete vNF; a partir de 2027 é vNF + IBS + CBS (a introdução da NT diz que IBS e CBS já compõem vProd e não devem ser somados de novo: conflito interno do texto) | 2026 e 2027 | Derivado; regra com vigência |
| 434 | Município do terminal principal obrigatório | Regra de implementação futura, sem data | Parâmetro de obrigatoriedade com vigência |
| 409 | Município do terminal principal diverge da UF do terminal | NT 2026.004 | Validação |
| 410 | Município do terminal principal inexistente na tabela do IBGE | NT 2026.004 | Validação |

**Efeito sobre os valores.** A introdução da NT diz que o IBS e a CBS "compõem o vProd" a partir de 2027, e que por isso **não devem ser somados de novo** ao total. A seção 5 da mesma NT, porém, manda calcular `vTotDFe = vNF + IBS + CBS` a partir de 2027 e só repetir `vNF` em 2026. Os dois textos se contradizem; o dicionário não precisa escolher (o total é derivado), mas a regra de cálculo tem de nascer com vigência e ser conferida com o MOC quando ele chegar (pendência P40-04). O documento 42 registrou o mesmo conflito no CT-e (Q-6).

**Valor líquido.** `vItemLiq` e `vProdLiq` guardam o valor do serviço antes dos tributos (`vProdLiq = vItemLiq × qFaturada`; regra 1050) e `total/vProdLiq` a soma (regra 1054). Já estão no P-14 do documento 34.

# 8. IT 2025.002 v1.70: indicadores e crédito presumido

A tabela de classificação tributária da v1.70 traz, para cada CST e cClassTrib, indicadores que dizem **onde o código vale e o que ele exige**: tributação regular, crédito presumido da operação, monofasia padrão, estorno de crédito, tipo de receita bruta do Simples, tipo de doação e a marca de cada modelo (NF-e, NFC-e, CT-e, NFS-e, NFS-e Via, NFCom e NF-e ABI). Para a NFCom, as regras 1056 e 1057 (doação) e as exceções de alíquota zero (tributação regular) dependem desses indicadores, e o dicionário hoje não guarda nenhum. A solução já está proposta no documento 41 (D-N62): campos de indicador em `Cad_Cst` e `Cad_Cclasstrib`, mais as marcas por modelo, com vigência. A NFCom só precisa de **uma linha de marca a mais** (`indNFCom`).

**Novos cClassTrib na v1.70:** 000006, 200055, 200056, 400003, 400004 e 550026 a 550029. Os códigos e a vigência da versão (HML e PROD até 16/10/2026, quando a v1.70 é substituída) entram como dado em `Cad_Cclasstrib`, sem mudança de estrutura.

**Crédito presumido (cCredPres).** A planilha traz **13 códigos** (de 01 a 13), cada um com o artigo da LC 214/2025, se apropria por nota ou por evento, os indicadores de CBS e IBS, as alíquotas (calculada e divulgada por ano, fixa ou efetiva), o cClassTrib da nota referenciada, a vigência separada de CBS e IBS (vários códigos começam em 01/01/2027), a declaração de pagamento (`indDecPag`) e as marcas de modelo (NF-e, NFC-e, CT-e e NFS-e). A segunda aba descreve a base e a fórmula de cada código (valor líquido, valor da operação de aquisição, de venda ou de apuração). O catálogo `Cad_Credito_Presumido_Ibs_Cbs`, proposto no documento 42, **passa a ter fonte**: o documento 42 o dava como vazio por falta do anexo, mas a planilha agora enviada o preenche (o documento 42 já foi corrigido). A NFCom não tem coluna própria na planilha, o que quer dizer que, pelo catálogo, **nenhum código de crédito presumido é apropriado por NFCom** (a conferir no MOC).

# 9. Eventos

| Código | Evento | Schema | Campos | Destino no dicionário |
|---|---|---|---|---|
| 110111 | Cancelamento | evCancNFCom | descEvento, nProt, xJust | Mov_Dfe_Evento (já cobre; só o modelo 62) |
| 110300 | Vinculação do pagamento | evVincPgto | descEvento, nProt, pgto (meio, recebedor, instituição, número e identificador) | Mov_Dfe_Evento e Mov_Dfe_Vinculo_Pagamento (P-13 do documento 34) |
| 110301 | Cancelamento da vinculação do pagamento | evCancVincPgto | descEvento, nProt, nProtVincPgto | Mov_Dfe_Evento (referência ao evento 110300) |

# 10. Pendências

| Código | Pendência | Efeito |
|---|---|---|
| P40-01 | MOC NFCom, Anexo I: leiaute, regras e significado dos códigos (tpFat, tpAssinante, tpServUtil, uMed, finNFCom, motSub, tpRessarc) e tabela de classificação `cClass` | Os domínios entram só com o código; `cClass` fica vazio |
| P40-02 | MOC NFCom, Visão Geral: URLs dos serviços, contingência e prazos | Falta o endereço do modelo 62 em `Cad_Autoridade_Fiscal_Atendimento` |
| P40-03 | IT DFe 2026.001: tabela de meios de pagamento | `tpMeioPgto` fica como código aberto |
| P40-04 | Conflito do texto da NT 2026.004 sobre o total geral (seção 7) | A regra do total nasce com vigência e é conferida com o MOC |
| P40-05 | Data de obrigatoriedade do município do terminal principal (regra 434) | Parâmetro de obrigatoriedade com vigência, sem data |
| P40-06 | Schemas de consulta de distribuição e de cancelamento por substituição | Só os três eventos do pacote entram |

# 11. Decisões para Alberto

Os números D-N52 a D-N57 são deste documento. Os documentos 41 (D-N58 a D-N65), 42 (D-N66 a D-N72) e 43 (D-N73 a D-N80) usam as faixas seguintes.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N52 | A NFCom é nota de saída (`Mov_Nota_Fiscal_Saida` e `_Item`) com extensão 1:1 `Mov_Nfcom` e `Mov_Nfcom_Item`, no mesmo padrão do CT-e (documento 42)? | Sim |
| D-N53 | Criar `Cad_Nfcom_Assinante` e `Cad_Nfcom_Assinante_Terminal`, ligados a `Cad_Gestao_Contrato` e `Cad_Participante`, em vez de campos soltos no participante? | Sim |
| D-N54 | Criar agora as sete entidades da seção 5 (mais a oitava, `Cad_Nfcom_Classificacao_Servico`, da Revisão 2), só como estrutura (sem telas), já que a D-N24 pediu para antecipar a NFCom? | Sim |
| D-N55 | Indicadores da IT 2025.002 v1.70 em `Cad_Cst` e `Cad_Cclasstrib` (D-N62 do documento 41) e crédito presumido em `Cad_Credito_Presumido_Ibs_Cbs` (documento 42), carregado com a planilha cCredPres (13 códigos), com marca `indNFCom`? | Sim |
| D-N56 | Datas e alíquotas da NT 2026.004 (13/10/2026, 16/11/2026, 01/02/2027 e 01/03/2027; IBS UF 0,1%, município 0%, CBS 0,9% em 2026; 0,05% e 0,05% em 2027 e 2028; municípios da zona de livre comércio) como parâmetros com vigência em `Cad_Aliquota`, `Cad_Cronograma_Transicao_Tributaria` e `Cad_Dfe_Leiaute`? | Sim. **Esclarecido pela D-N95 (11/10/2026):** alíquotas e cronograma ficam em `Cad_Aliquota` e `Cad_Cronograma_Transicao_Tributaria`; `Cad_Dfe_Parametro_Regra` guarda a regra de validação e aponta para eles; `Cad_Dfe_Leiaute` guarda só a versão e a data de início |
| D-N57 | Carregar os domínios do schema só com o código até o MOC (Anexo I e Visão Geral) chegar, e atualizar os significados depois? | Sim. Peço o envio do Anexo I, da Visão Geral e da IT DFe 2026.001 |

**Posso consolidar?**
