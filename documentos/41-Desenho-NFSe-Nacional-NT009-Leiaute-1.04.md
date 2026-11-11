# Desenho da NFS-e Nacional com a NT 009 e o leiaute 1.04.01 — Documento 41

*Análise do novo leiaute da NFS-e Nacional (Nota Técnica SE/CGNFS-e nº 009, Anexo VI v1.04.01 e Anexo VII v1.03.00, que Alberto enviou) contra o dicionário e contra o que o documento 34 já tinha proposto sobre o leiaute v1.01. Propostas de ajuste, nada consolidado: o dicionário só muda depois do seu "consolidar". Revisão 2 em 11/10/2026, com o pacote de schemas de 27/07/2026.*

Mlegate · Alberto Beyeler · Outubro de 2026

# Revisão 2 — pacote de schemas de 27/07/2026 (11/10/2026)

Chegou o pacote `esquemas-nfse-rtc-v1-01-20260727` (10 arquivos: DPS, NFSe, evento, pedido de registro de evento, CNC, tipos simples, complexos, de eventos e de CNC, e xmldsig). **Ele não traz o leiaute 1.04 da NT 009.** É o leiaute 1.01 (Anexo I de 09/02/2026) com CNPJ alfanumérico e correções de padrão: o atributo `versao` só aceita 1.00 ou 1.01; os 416 caminhos da NFS-e são iguais aos 416 do Anexo I v1.01; contra o Anexo VI v1.04.01 (450 linhas) há 306 em comum, 110 que só o XSD tem e 144 que só o Anexo VI tem; faltam todos os nomes-chave da NT 009. Já estão nele o que as NTs 007 e 009 pedem de `tpRetPisCofins` (0 a 9), CNPJ alfanumérico, `xDescServ` de 2.000 posições e `cMotivo` de 2 dígitos. **Nenhuma das 15 dúvidas (Q-1 a Q-15) se resolve por ele, e nenhuma das 9 entidades da seção 12 cai.** Esta revisão não altera o dicionário.

## O que mudou contra o pacote de 09/02/2026

Oito arquivos são idênticos; mudam só `tiposSimples` (18 tipos, todos por padrão regex) e o DOCTYPE do xmldsig. Campos novos ou removidos: nenhum; ocorrências, enumerações e tamanhos: nenhuma mudança. O CNPJ passa a `[0-9A-Z]{14}` (7 caminhos da NFS-e, `CNPJAutor` nos eventos e o CNPJ do CNC); ids e chaves ganham `tpInsc` e letras. A série da DPS no pacote de 09/02 rejeitava qualquer valor (`^` e `$` são literais em XSD; testado) e agora aceita 00000 a 89999. O fuso de `dhEmi` foi corrigido e `xDescServ` e `xOutInf` não podem ser só espaços. Continuam **ausentes dos dois XSD**: `finNFSe` fora de `IBSCBS` e com 1 e 2, `tpNFSeDebito` e `Credito`, `vAjusteBC` e `tpAjusteBC`, `gIBSCBSAjuste`, `gLocacao`, `gUnidImob`, `gAjusteBCLocImoveis`, `bensMoveis`, `condominios`, `gPgtoVinc`, `gPagAntecipado`, `gEstornoCred`, `regApIBSCBSSN`, `gTribSN`, `nDUIMP` e `nDUE`. O XSD ainda tem `IBSCBS/finNFSe` só com 0, `vDedRed` e `gReeRepRes` separados, `nDI` e `nRE`, `opSimpNac` de 1 a 3 e `cIndOp` obrigatório com 6 dígitos.

## Dúvidas Q-1 a Q-15

Nenhuma resolvida. Parciais: Q-9 (confirma o caminho antigo de `dest` e `nDI`/`nRE`), Q-10 (o `tpDedRed` 9 já está no XSD desde 09/02/2026, então "novo" vale só contra o texto do Anexo I), Q-13 (o esquema publicado ainda é o 1.01) e Q-14 (o XSD só exige 6 dígitos em `cIndOp`). Q-2 (limite), Q-3 (sinal), Q-5 (caminho) e Q-8 (digitação) não se resolvem, porque os campos não existem no XSD.

## Campos

Dos 416 caminhos do XSD: nenhuma lacuna nova e 3 a confirmar (`nDFSe`, CAEPF do prestador e `tpRetPisCofins`). As 35 lacunas da seção 11 estão todas fora do XSD, ainda não exigidas. Falta o inverso: **7 itens (10 campos) do XSD vigente sem lugar no desenho 1.04** (`cVerifNFSeMun`, `modNFS`, `serieNFS`, CAEPF e IM do fornecedor, `endExt` do imóvel e `nDI`/`nRE`). `Mov_Nfse_Dps` cobre os 30 campos que o documento liga a ele e os domínios conferem com o XSD; o valor 4 de `opSimpNac` não cabe no XSD.

## Efeito nas decisões

| Decisão | Efeito |
|---|---|
| D-N58, D-N61 e D-N62 | Não mudam. |
| D-N59 (ajuste de base) | O catálogo guarda código e grupo de origem do v1.01; decidir se a entidade guarda os 5 campos legados (`vDedRed`, `gReeRepRes` separados, `nDI`, `nRE` e a verificação municipal). |
| D-N60 (comércio exterior) | Precisa de `nDI` e `nRE` legados enquanto o XSD for o 1.01. |
| D-N63 (NFS-e de ajuste) | `finNFSe` só aceita 0 no XSD vigente: o ajuste fica bloqueado pelo schema. |
| D-N64 (datas e Simples) | `Cad_Dfe_Leiaute` separa a versão do XML, a do XSD e a do Anexo VI; definir o que enviar em `opSimpNac` 4. |
| D-N65 (desenhar sobre o Anexo VI) | Para **validar XML** vale o XSD 1.01; o Anexo VI continua sendo a base do desenho. |

## Correções ao texto deste documento

1. Seção 10: os eventos mudaram (o texto diz que não).
2. `xOutInf` não muda de lugar.
3. `xDescServ` e `cMotivo` já estavam no XSD.
4. `indFinal` nunca saiu.
5. "Leiaute 1.04" não é versão de XML: o `versao` do XML só aceita 1.00 e 1.01.
6. A série da DPS: o pacote anterior rejeitava qualquer série (defeito do padrão), o atual aceita 00000 a 89999.

## Dúvidas novas (N-1 a N-11)

N-1: quando sai o XSD do leiaute 1.04, qual será o `versao` e o que o ADN aceita de DPS hoje e a partir de 01/10/2026? N-2: `TSChaveNFSe` usa 6 + 14 + 30 e o Id usa 9 + 14 + 27; o padrão rejeita chave com letra no 12º caractere do CNPJ (não usar o XSD para validar chave). N-3: `TSIdNumEvento` caiu de 59 para 56 posições; o teste rejeita 59. N-4: `TSData` ainda aceita vírgula no mês. N-5: `chNFSeRej` é numérico no Anexo VI, mas a chave pode ter letras (gravar como texto de 50). N-6: série 90000 a 99999 e 00000 (reservadas ou inválidas?). N-7: o que enviar em `opSimpNac` e `regApTribSN` para o optante pendente (valor 4). N-8: emitir ajuste ou comércio exterior no 1.01 exige 10 campos que o desenho 1.04 descarta. N-9: o XSD permite 1.000 `docDedRed` mais 1.000 de `gReeRepRes`, o Anexo VI unifica em 1.000. N-10: tamanhos do XSD e do Anexo divergem (`xNome` 300 contra 150, fone do emitente, `pTotTrib`, `pAliqAplic`, `tpBM`); usar o menor. N-11: os tipos 1, 3 e 4 de `tpDedRed` são descontinuados no Anexo VI e o XSD 1.01 os aceita. Detalhe no anexo; decisão **D-N92** do documento 44.

# 1. Resumo

A NT 009 (04/06/2026) reorganiza a DPS e a NFS-e em oito pontos: CNPJ alfanumérico, notas de ajuste de IBS/CBS, fusão dos grupos de dedução e de reembolso num só (`vAjusteBC`), evoluções para o Simples Nacional, a volta do `indFinal`, a reestruturação do imóvel (locação, unidades e ajustes), os bens móveis e a vinculação do pagamento. Li a NT, o Anexo VI (7 abas) e o Anexo VII e comparei as 450 linhas do leiaute novo com as 416 do v1.01 e com a classificação do documento 34.

Das 450 linhas, **139 já estão cobertas** pelo dicionário, **142 estão cobertas por propostas do documento 34**, 19 são derivadas (a nota calcula, o ERP não grava), 16 ficam só no XML, 96 são agrupadores sem dado próprio, 3 ficam a confirmar e **35 são lacunas novas**. As lacunas se concentram em locação de imóveis, bens móveis, condomínios, Simples Nacional, comércio exterior e nas NFS-e de ajuste (seção 11). Em relação ao v1.01, 64 linhas são novas, 80 mudaram de lugar, 42 mudaram de conteúdo e 264 ficaram iguais; 111 caminhos do v1.01 deixaram de existir (movidos, renomeados, substituídos ou removidos).

A tabela de indicador de operação (`cIndOp`) vai de 26 códigos para 40 (18 novos e 4 removidos); o documento 34 tinha previsto recarregar 27, mas o Anexo C v1.01 tem 26. As regras de negócio passam de 428 para 478 códigos E: 80 novos e 30 removidos, e 137 dos 398 que ficaram tiveram o texto alterado. Há ainda 71 regras vivas sem código definitivo (EXXX).

**Uma correção ao que se supunha.** `Mov_Nfse_Dps`, `Mov_Nfse_Comercio_Exterior`, `Mov_Nfse_Atividade_Evento`, `Cad_Dfe_Leiaute` e as demais entidades de NFS-e dos documentos 33 e 34 são propostas ainda não consolidadas: não existem no `model.json`. Quando este documento diz que algo está "coberto por proposta do doc 34", é isso. Proponho **9 entidades novas** (uma delas renomeia a do P-9 do documento 34) e campos novos em 12 entidades já existentes ou propostas, com as **decisões D-N58 a D-N65** (seção 14). Nada foi alterado no dicionário.

# 2. Fontes lidas

| Fonte | Versão e data | O que contém | Uso neste documento |
|---|---|---|---|
| NT SE/CGNFS-e nº 009 (PDF) | Versão 1.0, 04/06/2026, 12 páginas | Oito atualizações (2.1 a 2.8) com as tabelas de campos alterados. Diz que o cronograma de implantação será publicado depois | Fonte do porquê de cada mudança; confrontada com o Anexo VI |
| Anexo VI, leiaute das RN do RTC (planilha) | v1.04.01 | 7 abas: LEIAUTE DPS_NFS-e - RT (450 linhas), RN DPS_NFS-e (832 linhas na aba), AJUSTE_BC_REPERCUSSÃO, NFS-e_AJUSTE_LEIAUTE (430 linhas de matriz), RN_RECEPCAO_DPS, EXPORTACAO_EMISSÃO_NFS-e e MUN.INCID_INFO.SERV. | Base da classificação campo a campo e das regras |
| Anexo VII, indicador de operação (planilha) | v1.03.00 | 40 códigos de `cIndOp` com flags por documento e local de incidência do IBS na NFS-e | Seção 8 |
| Anexo I, leiaute v1.01 (planilha) | v1.01, 09/02/2026 | 416 linhas de leiaute e 428 códigos de regra | Base de comparação |
| Anexo C, indicador de operação (planilha) | v1.01 | 26 códigos de seis dígitos | Base de comparação |
| Documentos 33, 34, 35 e 36 do Project e `model.json` | Revisões de outubro de 2026 | Propostas de NFS-e, DF-e e Simples; dicionário com 543 entidades | Cobertura e vocabulário |

**Fora do escopo, já recebidos.** A NT 010 e o Anexo VI do guia de manifestação do adquirente tratam da NFS-e Via (rodovias), que o documento 34 deixou fora do escopo; não foram usados. A NT 2026.009 (CFOP) e a IT 2025.002 v1.70 não foram relidas aqui; usei só as tabelas de CST e de classificação tributária e os domínios `tpNFDebito` e `tpNFCredito` que já estavam extraídos.

Duas fontes divergem em número de versão: a NT cita o Anexo VI v1.04.00 e o Anexo VII v1.02.00, e os arquivos recebidos são v1.04.01 e v1.03.00 (pendência Q-1). Tratei os arquivos recebidos como os valendo.

**O PDF da NT 009 chegou duas vezes.** O arquivo `nt-009-se-cgnfse-v1-0-1.pdf`, que chegou depois, traz no próprio texto "Versão 1.0", de 4 de junho de 2026, com 12 páginas (o metadado do PDF é de 05/06/2026). O "1" a mais está só no nome do arquivo. O texto, extraído com `pdftotext -layout`, é idêntico, linha a linha, ao que eu já tinha usado, e não há outro PDF da NT 009 para comparar: nada mudou no desenho por causa dele. A NT 007 (07/02/2026) também foi consultada, só para a linhagem das versões dos anexos e para o `tpRetPisCofins`. O que a NT 009 diz sobre prazos é pouco: o CNPJ alfanumérico vale "a partir de julho de 2026" e o cronograma de implantação "será publicado nas próximas semanas", sem data. Ela não traz datas de obrigatoriedade do IBS/CBS (a 01/10/2026 da E0855 e a 01/11/2026 da E0163 vêm só do Anexo).

**Conferência.** Um script confirmou que todo nome de entidade e de campo existente citado aqui consta do `model.json`, que as entidades de NFS-e, DF-e e Simples que não constam são propostas dos documentos 33 a 36, que os números deste texto são os da planilha `Anexo_NFSe_NT009_vs_Dicionario.xlsx` (450 campos, 111 removidos, 80 e 30 regras, 157 linhas sem código, 40 códigos de `cIndOp`) e que o texto não tem marcador de pendência em aberto. Lido de verdade, aba por aba, com datas e códigos copiados das planilhas.

# 3. O que mudou do v1.01 para o v1.04.01

A tabela agrupa as 450 linhas por tema. A coluna "Situação" diz se o efeito no dicionário já está coberto, se está coberto por proposta do documento 34 ou se é lacuna nova (proposta deste documento). A NT 009 descreve os temas 1 a 8; o tema 12 (PIS, COFINS e CSLL) vem da NT 007, e os temas 9, 10, 11 e 13 aparecem só no Anexo VI, sem explicação em NT recebida (pendência Q-9).

| Tema | O que mudou | Efeito no dicionário | Situação |
|---|---|---|---|
| 1. CNPJ alfanumérico (NT 2.1) | 6 campos `CNPJ` passam de numérico (N) para caractere (C): emitente, prestador, tomador, intermediário, destinatário e fornecedor do ajuste. Os novos `CNPJReceb` e `CNPJBasePSP` já nascem como caractere | `Cad_Participante.Documento_Principal` já aceita CNPJ alfanumérico. Os campos de terceiros dentro de entidades filhas (fornecedor do ajuste, recebedor do pagamento) seguem como texto de 14 posições | Coberto |
| 2. Notas de ajuste de IBS/CBS (NT 2.2) | `finNFSe` sai de `IBSCBS` e passa a 0 regular, 1 crédito e 2 débito; entram `tpNFSeDebito` (01 a 06), `tpNFSeCredito` (01 e 05) e o grupo `gIBSCBSAjuste`; 28 linhas passam de 1-1 para 0-1 (a maioria para caber as notas de ajuste e o Simples); nova aba NFS-e_AJUSTE_LEIAUTE | Finalidade e tipos de nota de débito e de crédito já foram propostos no P-1 do documento 34 (NF-e). Falta o valor de IBS e CBS a ajustar (2 campos) | Coberto por proposta do doc 34; lacuna nova (2 campos) |
| 3. Fusão de `vDedRed` e `gReeRepRes` em `vAjusteBC` (NT 2.3) | Os dois grupos viram um só, com `pAjusteBCISSQN`, `vAjusteBCISSQN` e até 1.000 documentos (`docAjusteBC`); `tpDedRed` e `tpReeRepRes` viram `tpAjusteBC` com 13 tipos vigentes e 3 descontinuados; `vCalcDR` vira `vCalcAjusteBCISSQN`, `vCalcReeRepRes` vira `vCalcAjusteBCIBSCBS`, `vCalcDedRedIBSCBS` vira `vCalcAjusteBCLocImoveis`; as fórmulas do `vBC` mudam | A entidade única do P-9 do documento 34 passa a se chamar `Mov_Nfse_Ajuste_Bc_Documento` e a finalidade vira o catálogo `Cad_Nfse_Tipo_Ajuste_Bc` (seção 5) | Coberto por proposta do doc 34, com ajustes |
| 4. Simples Nacional (NT 2.4) | `opSimpNac` ganha o valor 4 (optante pendente); entram `regApIBSCBSSN` (1, 2 ou 3), `cAtvSN` (07 a 14 e 90), `vReceitaBrutaSN` e o grupo `gTribSN` (alíquotas e valores de IBS e CBS pelo SN); `vIBSTot`, `gIBSUFTot`, `gIBSMunTot`, `pCredPresCBS`, `vCredPresCBS` e `vCBS` passam a 0-1 | Lacuna nova em 6 campos de entrada e de retorno; `vReceitaBrutaSN` é derivado (seção 7) | Lacuna nova |
| 5. `indFinal` volta (NT 2.5) | Reinserido na DPS (uso ou consumo pessoal, art. 57 da LC 214). No v1.01 vinha marcado como descontinuado | `Mov_Nota_Fiscal_Saida.Indicador_Consumidor_Final` já existe | Coberto |
| 6. Imóveis (NT 2.6) | `imovel` ganha `cMun`, `gLocacao`, `gUnidImob` (até 99 unidades) e `gAjusteBCLocImoveis` (nome novo do `gDedRedIBSCBS`); `vServ`, `vDescIncond` e `vDescCond` seguem fórmulas próprias no subitem 99.03 | Unidades, parcelas de ajuste e 5 campos de locação: lacuna nova; o imóvel e o redutor social já existem no dicionário (seção 6) | Lacuna nova; imóvel coberto |
| 7. Bens móveis (NT 2.7) | `gLocBensMoveis` vira `bensMoveis` e passa a aceitar até 1.000 bens (subitem 99.04.01) | `Mov_Nfse_Bem_Movel_Locado` (3 campos de lacuna) | Lacuna nova |
| 8. Vinculação do pagamento (NT 2.8) | Grupo `gPgtoVinc` com até 99 pagamentos (número, identificador da transação, meio, CNPJ do recebedor e CNPJ base do PSP) | É o mesmo grupo da NF-e (P-13 do documento 34): `Mov_Dfe_Vinculo_Pagamento` | Coberto por proposta do doc 34 |
| 9. Destinatário fora de `IBSCBS` (só no Anexo) | `indDest` e o grupo `dest` (22 linhas) saem de `IBSCBS` e vão para a raiz da DPS, no mesmo nível de `toma` | Só mudam de caminho; o mapeamento para o participante e o endereço continua igual | Coberto |
| 10. Comércio exterior (só no Anexo) | `nDUIMP` (15) e `nDUE` (14) substituem `nDI` e `nRE`; entram `nFatura`, `vFatura` e `nContCambio`; `mdPrestacao` ganha o valor 5; `tpMoeda` deve existir na tabela do Banco Central; `vAjusteBCIBSCBSComExt` entra na base do IBS/CBS; `atvEvento` ganha `cMun` | Lacuna nova em 5 campos, em entidades que o documento 34 propôs | Lacuna nova |
| 11. Condomínios (só no Anexo) | Grupo `condominios` para o subitem 99.05: até 20 cobranças com detalhamento (até 20 por cobrança, 38 tipos) e até 10 descontos | Três entidades condicionais (seção 6) | Lacuna nova |
| 12. PIS, COFINS e CSLL | `tpRetPisCofins` aceita 1 e 2 só enquanto o IBS/CBS não for obrigatório (01/10/2026); `vRetCSLL` passa a somar as contribuições retidas conforme o tipo; o `CST` perde uma nota interna | Domínio com vigência (já previsto no documento 34); o mapeamento da retenção ficou a confirmar | Coberto; 1 campo a confirmar |
| 13. Retorno e pequenos ajustes | `verCalcIBSCBS` novo; `xOutInf` muda de lugar (agora em `infNFSe`, 2.000 posições); `xDescServ` de 1.000 para 2.000; `cMotivo` da substituição com 2 dígitos; o DV do `id` segue válido com CNPJ alfanumérico | Só `verCalcIBSCBS` é lacuna; o resto cabe nos campos existentes ou só vai no XML | Coberto; 1 lacuna |
| 14. Regras e tabelas | 80 regras novas, 30 removidas, 137 com texto alterado; `cIndOp` com 40 códigos | Seções 8 e 9 | Proposta |

Campos novos que o documento 34 já cobria por outras notas técnicas e que agora aparecem no leiaute: `indZFMALC`, `indDoacao`, `gEstornoCred` e `gPagAntecipado`. Estão contados como "coberto por proposta do doc 34". A lista completa de caminhos movidos, renomeados e removidos está na aba Removidos da planilha (111 linhas).

# 4. NFS-e de ajuste

A NFS-e de ajuste é uma nota de IBS/CBS que corrige a apuração, sem ser uma nota de serviço comum. Cada tipo está em `finNFSe` (1 crédito, 2 débito) e no tipo correspondente (`tpNFSeCredito` ou `tpNFSeDebito`). A aba NFS-e_AJUSTE_LEIAUTE da planilha diz, campo por campo, o que cada tipo pode informar. Contei as 430 linhas dessa aba:

| Tipo | finNFSe | Rótulo | Equivalente na NF-e | Família | Campos permitidos (de 430) | O que o leiaute permite |
|---|---|---|---|---|---|---|
| Débito 01 | 2 | Transferência de créditos para cooperativas | tpNFDebito 01 | Família A | 90 | Só apuração: prestador, tomador, CST, classificação e valor de IBS e CBS a ajustar |
| Débito 02 | 2 | Anulação de crédito por saídas imunes ou isentas | tpNFDebito 02 | Família A | 76 | Só apuração: prestador, tomador, CST, classificação e valor de IBS e CBS a ajustar |
| Débito 03 | 2 | Débitos de notas fiscais não processadas na apuração | tpNFDebito 03 | Família A | 101 | Só apuração: prestador, tomador, CST, classificação e valor de IBS e CBS a ajustar |
| Débito 04 | 2 | Multa e juros | tpNFDebito 04 | Família B | 292 | Nota completa, com serviço, valores e IBS/CBS; sem o valor de ajuste de IBS e CBS |
| Débito 05 | 2 | Transferência de crédito na sucessão | tpNFDebito 05 | Família A | 90 | Só apuração: prestador, tomador, CST, classificação e valor de IBS e CBS a ajustar |
| Débito 06 | 2 | Pagamento antecipado | tpNFDebito 06 | Família B | 295 | Nota completa, com serviço, valores e IBS/CBS; sem o valor de ajuste de IBS e CBS |
| Crédito 01 | 1 | Multa e juros | tpNFCredito 01 | Família B | 292 | Nota completa, com serviço, valores e IBS/CBS; sem o valor de ajuste de IBS e CBS |
| Crédito 05 | 1 | Transferência de crédito na sucessão | tpNFCredito 05 | Família A | 90 | Só apuração: prestador, tomador, CST, classificação e valor de IBS e CBS a ajustar |

A **família A** (débito 01, 02, 03 e 05 e crédito 05) não leva serviço nem valores do serviço: informa só quem é o prestador (e o tomador, exceto no débito 02), o CST, a classificação e o valor de IBS e de CBS a ajustar (`gIBSCBSAjuste`). A **família B** (débito 04 e 06 e crédito 01) é uma nota completa, com 292 a 295 campos, que não usa `gIBSCBSAjuste`; o ajuste vai no valor do serviço e nas alíquotas. O débito 06 (pagamento antecipado) é o único que aceita desconto. O débito 03 (notas não processadas na apuração) é o único da família A que aceita a referência às NFS-e de origem (`gRefNFSe`, até 99) e o tomador completo.

**Relação com a NF-e.** A NF-e usa `finNFe` 5 (crédito) e 6 (débito), com `tpNFDebito` de 01 a 08 e `tpNFCredito` de 01 a 06 (NT 2025.002). Os rótulos dos oito tipos da NFS-e são os mesmos dos tipos 01 a 06 de débito e 01 e 05 de crédito da NF-e. Ficam só na NF-e os débitos 07 (perda em estoque) e 08 (desenquadramento do Simples) e os créditos 02, 03, 04 e 06. O código do `finNFSe` (1 e 2) **não é** o do `finNFe` (5 e 6): o dicionário deve guardar o significado (crédito ou débito) e traduzir para o dígito de cada modelo na geração do XML, em parâmetro de `Cad_Dfe_Leiaute`.

**Relação com o dicionário e com `Mov_Nfse_Dps`.** O P-1 do documento 34 já propôs `Mov_Nota_Fiscal_Saida.Tipo_Nota_Debito`, `Mov_Nota_Fiscal_Saida.Tipo_Nota_Credito` e os valores crédito e débito em `Mov_Nota_Fiscal_Saida.Finalidade` (hoje {normal, complementar, ajuste, devolucao}). Os mesmos campos servem à NFS-e: a nota guarda a finalidade e o tipo, e `Mov_Nfse_Dps` guarda o resto da DPS. O valor de IBS e de CBS a ajustar (`gIBSCBSAjuste`) entra como 16º tipo de `Mov_Apuracao_Tributo_Item_Complemento` (hoje com 14 tipos no P-4 e um 15º proposto na seção 7). Não precisa de entidade nova (D-N63).

**Quanto confiar na matriz.** A própria NT diz que as regras das notas de ajuste "ainda estão em evolução": as regras estão tachadas na planilha (86 linhas EXXX riscadas, quase todas sobre as notas de ajuste) e a matriz é "um norteador". Além disso, 30 das 430 linhas da matriz usam caminhos que não existem no leiaute novo (22 do destinatário, que saiu de `IBSCBS`; 2 de `CST` e `cClassTrib`, que subiram um nível; 3 de `gIBSCBSAjuste`, que está um nível abaixo no leiaute; 3 de campos antigos como `nDI` e `nRE`). Desenho a estrutura, não a tela: a emissão de nota de ajuste só deve ser liberada quando as regras forem publicadas sem tachado.

Para o ajuste por grupo do leiaute, veja a aba "Ajuste por grupo" da planilha; os 430 campos estão na aba "Ajuste campos".

# 5. Ajuste de base de cálculo

`vAjusteBC` reúne tudo o que reduz a base de cálculo do serviço: o ajuste por percentual (`pAjusteBCISSQN`), por valor (`vAjusteBCISSQN`) e por documentos (`docAjusteBC`, até 1.000 por NFS-e, com 31 campos de dados cada). A aba AJUSTE_BC_REPERCUSSÃO diz o que cada tipo muda em três bases:

| tpAjusteBC | Descrição | Início da vigência | Reduz a BC do ISSQN | Reduz a BC do IBS/CBS | Reduz a receita bruta do SN | Referência legal |
|---|---|---|---|---|---|---|
| 2 | Materiais | 01/01/2022 | Sim | Não | Não | - |
| 5 | Repasse consorciado | 01/01/2022 | Sim | Não | Não | - |
| 6 | Repasse plano de saúde | 01/01/2022 | Sim | Não | Não | - |
| 7 | Serviços | 01/01/2022 | Sim | Não | Não | - |
| 8 | Subempreitada de mão de obra | 01/01/2022 | Sim | Não | Não | - |
| 9 | Profissional parceiro | 01/01/2022 | Sim | Não | Sim | - |
| 99 | Outras deduções exclusivas do ISSQN | 01/01/2022 | Sim | Não | Não | - |
| 101 | Repasses na intermediação de imóveis (...) | 01/01/2026 | Sim | Sim | Sim | LC 214/2025: Art. 255, § 3º |
| 102 | Repasses na intermediação de agências de turismo | 01/01/2026 | Sim | Sim | Sim | LC 214/2025: Art. 12, § 2º, inciso IV |
| 103 | Reembolso de agência de propaganda e publicidade (...) | 01/01/2026 | Sim | Sim | Sim | LC 214/2025: Art. 12, § 2º, inciso IV |
| 104 | Reembolso de agência de propaganda e publicidade. ref serviço de (...) | 01/01/2026 | Sim | Sim | Sim | LC 214/2025: Art. 12, § 2º, inciso IV |
| 105 | Glosa de Serviços de Saúde | 01/01/2026 | Não | Sim | Sim | LC 214/2025: Art. 130, § único |
| 199 | Outros reembolsos . (...) | 01/01/2026 | Sim | Sim | Sim | LC 214/2025: Art. 12, § 2º, inciso IV |

O ajuste por percentual e o por valor valem desde 01/01/2022, só para o ISSQN, e ficam como campos de `Mov_Nfse_Dps` (`Percentual_Ajuste_Bc_Issqn` e `Valor_Ajuste_Bc_Issqn`). Os tipos 1, 3 e 4 do `tpDedRed` foram **descontinuados**: o 1 (alimentação e bebidas) porque o fornecimento já tem documento fiscal próprio e não pode entrar na NFS-e por causa do IBS/CBS; o 3 (produção externa) porque o 103 o descreve melhor; o 4 (reembolso de despesas) porque os reembolsos com efeito no IBS/CBS estão nos tipos 103, 104 e 199. O reembolso que o município admitir fora desses tipos vai no 99, só com efeito no ISSQN. A planilha traz a coluna "Fim" em branco para todos os tipos; mantenho os três descontinuados no catálogo com fim de vigência, para ler notas antigas.

**O ISSQN depende do município.** O asterisco da planilha diz que o ajuste só reduz a base do ISSQN se o município autorizar, no painel administrativo municipal, a dedução por código de serviço e por forma (percentual, valor ou documentos). No ERP isso é o espelho da parametrização municipal (`Cad_Nfse_Aliquota_Servico_Municipal`, do documento 34), com vigência, e não uma regra fixa.

**Catálogo `Cad_Nfse_Tipo_Ajuste_Bc`.** Uma linha por tipo, com vigência: `Codigo`, `Descricao`, três marcas (`Reduz_Base_Issqn`, `Reduz_Base_Ibs_Cbs` e `Reduz_Receita_Bruta_Sn`), `Exige_Documento_Fiscal` (tipos 101, 103, 104 e 199, E0479), `Exige_Descricao` (99 e 199, E0465), `Referencia_Legal` e o período de vigência. Com as três marcas, o ERP decide o que somar em `vCalcAjusteBCISSQN`, em `vCalcAjusteBCIBSCBS` e em `vReceitaBrutaSN` sem comparar códigos no programa; quando o Comitê Gestor criar um tipo, é uma linha nova.

**Uma entidade ou duas.** O P-9 do documento 34 já propôs uma entidade só para as deduções do ISSQN e para os reembolsos do IBS/CBS (`Mov_Nfse_Deducao_Documento`, com o campo Finalidade {deducao_iss, reembolso_ibscbs}) e citava como alternativa a irmã `Mov_Nfse_Reembolso_Documento`. O leiaute novo decide a questão: os dois grupos viraram um só, a estrutura do documento é a mesma e quem diz o efeito de cada linha é o tipo de ajuste, pelas três marcas do catálogo. Proponho **uma entidade, `Mov_Nfse_Ajuste_Bc_Documento`** (nome novo da do P-9), sem o campo Finalidade, que passa a ser derivado do catálogo, e descarto a irmã. A estrutura muda pouco em relação ao P-9: o tipo passa a ser o do catálogo (`ID_Tipo_Ajuste_Bc`, no lugar da Finalidade) e entram o tipo da chave do DF-e (NFS-e, NF-e, CT-e ou outro) e a data de competência do documento, ambos vindos do antigo `gReeRepRes`.

**Fórmulas que mudam** (derivadas, o ERP não grava): a base do ISSQN passa a ser `vServ - descIncond - (vAjusteBCISSQN + vCalcAjusteBCISSQN) - benefício municipal`; a base do IBS/CBS passa a ser `vServ - descIncond - (vCalcAjusteBCIBSCBS ou vCalcAjusteBCLocImoveis) - vISSQN + vAjusteBCIBSCBSComExt`, menos PIS e COFINS até 2026. A fórmula do IBS/CBS no Anexo tem o termo do comércio exterior que a NT não cita (pendência Q-3). A receita bruta do Simples (`vReceitaBrutaSN`) usa o indicador `tpRBSN` da classificação tributária, que o dicionário não guarda (D-N62).

# 6. Locação de imóveis, bens móveis e condomínios

**O que já existe no dicionário.** `Cad_Imovel` (com `Codigo_Cib`, `Numero_Inscricao_Municipal`, `ID_Municipio` e `Uso_Imovel`), `Cad_Local_Operacao` (endereço do local, hoje com `Tipo_Local` {obra, entrega, prestacao_servico, outro}), `Cad_Locacao_Opcao`, `Cad_Redutor_Social_Imobiliario` (R$ 600 por mês na locação residencial) e `Cad_Imovel_Redutor_Ajuste`. **O que é só proposta dos documentos 33 e 34:** `Cad_Locacao_Obrigacao_Emissao` (limites da pessoa física e data de obrigatoriedade, decisão D-N8), `Mov_Locacao_Faturamento`, `Mov_Nfse_Dps` e o valor `imovel` em `Cad_Local_Operacao.Tipo_Local` (P-11 do documento 34). O documento 34 dizia que o leiaute da locação ainda não existia; agora existe no Anexo VI, mas o cronograma de entrada em produção segue sem data na NT.

| Grupo do leiaute | O que informa | Destino proposto | Situação |
|---|---|---|---|
| `imovel/cMun` | Município do imóvel | `Cad_Imovel.ID_Municipio` | Coberto |
| `gLocacao` (5 campos) | Percentual de copropriedade, valor total da operação, descontos totais e data de vencimento original. No subitem 99.03: `vServ = pCopropriedade x vTotOper`; `vDescIncond` e `vDescCond` seguem o mesmo percentual | Campos de `Mov_Nfse_Dps` (`Percentual_Copropriedade`, `Valor_Total_Operacao_Imovel`, `Valor_Desconto_Incondicionado_Total`, `Valor_Desconto_Condicionado_Total`, `Data_Vencimento_Original`) | Lacuna nova |
| `gUnidImob` (até 99) | Inscrição imobiliária fiscal, CIB e endereço de cada unidade; todas com os mesmos atores, o mesmo município e o mesmo percentual de copropriedade | `Mov_Nfse_Unidade_Imobiliaria`, ligada a `Cad_Imovel` (CIB e inscrição) e a `Cad_Local_Operacao` (endereço) | Coberto na origem; entidade filha nova |
| `gAjusteBCLocImoveis` (até 10 por unidade) | Parcelas que saem da base: 01 tributos (IPTU), 02 emolumento, 03 condomínio, 04 redutor social, 99 outras. Os tipos 01 a 03 só valem para as NBS 1.1002.10.00 e 1.1002.20.00; o 04, só para a 1.1002.10.00 | `Mov_Nfse_Unidade_Ajuste_Bc`; a parcela 04 aponta para `Cad_Redutor_Social_Imobiliario` | Lacuna nova |
| `bensMoveis` (até 1.000) | NCM, descrição e quantidade de cada bem locado (subitem 99.04.01) | `Mov_Nfse_Bem_Movel_Locado`, ligada a `Cad_Classificacao_Mercadoria` | Lacuna nova |
| `condominios` (subitem 99.05) | Data de vencimento, até 20 cobranças (6 tipos), detalhamento (38 tipos) e até 10 descontos; a soma das cobranças é o `vServ` | `Mov_Nfse_Condominio_Cobranca`, `Mov_Nfse_Condominio_Desconto` e `Cad_Nfse_Detalhe_Cobranca_Permitido` (combinações permitidas, com vigência) | Lacuna nova, condicional |

As regras de compatibilidade (que tipo de parcela vale para qual NBS, que detalhamento vale para qual cobrança) são **parâmetros com vigência**, nunca código fixo. A vinculação à obrigação de emitir NFS-e do locador continua em `Cad_Locacao_Obrigacao_Emissao` e na D-N8: o leiaute dá o formato da nota, mas não diz quem é obrigado nem desde quando. O roteamento só pela Sefin Nacional (D-N33) agora tem sustentação na regra E0309, que rejeita o compartilhamento de notas 99.03.xx e 99.04.01 (seção 9). Os condomínios (99.05) não aparecem na NT: só no Anexo, e o documento 34 não os previu. O grupo só vale para o subitem 99.05; sugiro desenhar e **não criar as três entidades** até confirmar que a Mlegate ou algum cliente emite nota de condomínio (D-N61).

# 7. Simples Nacional na NFS-e

| Campo | Valores | Tratamento proposto |
|---|---|---|
| `opSimpNac` | 1 não optante; 2 MEI; 3 ME/EPP; **4 optante pendente (novo)** | `Cad_Simples_Opcao.Situacao` (proposta do documento 33) ganha o valor pendente; o ERP preenche o campo pela situação vigente na competência |
| `regApIBSCBSSN` (novo) | 1 IBS e CBS pelo SN; 2 CBS pelo SN e IBS pelo regime regular; 3 IBS e CBS pelo regime regular | `Mov_Nfse_Dps.Regime_Apuracao_Ibs_Cbs_Sn` guarda o que foi declarado. A fonte da decisão é `Cad_Participante_Regime_Ibs_Cbs` ({unificado, hibrido}) mais o excesso de sublimite de `Mov_Simples_Receita_Mensal` |
| `cAtvSN` (novo) | 07 a 14 e 90, na numeração da LC 123, só as atividades que a NFS-e usa | `Mov_Nfse_Dps.ID_Atividade_Simples` (para `Cad_Simples_Atividade`, documento 33). Só com `opSimpNac` 2, 3 ou 4 |
| `vReceitaBrutaSN` (novo) | Derivado: `vServ - descIncond - vCalcAjusteBCIBSCBS - vCalcAjusteBCISSQN` (este só quando vem do tipo 9) | Não grava na nota; alimenta `Mov_Simples_Receita_Mensal`. Vale zero quando o `tpRBSN` da classificação é 0 |
| `gTribSN` (novo) | `pIBSSN`, `vIBSSN`, `pCBSSN` e `vCBSSN` | 15º tipo `ibs_cbs_simples_nacional` de `Mov_Apuracao_Tributo_Item_Complemento` |

**Cruzamento com o regime híbrido.** O documento 36 e `Cad_Participante_Regime_Ibs_Cbs` só conhecem dois regimes: unificado (IBS e CBS dentro do DAS) e híbrido (regime regular, por fora). A DPS tem três. O valor 1 equivale ao unificado e o 3 ao híbrido. O valor 2 (CBS pelo SN e IBS pelo regime regular) não tem par no dicionário: **hipótese a confirmar**, é o caso do excesso do sublimite estadual, em que o IBS sai do DAS mas a CBS fica (decisão D-N64 e pendência Q-12). Para o profissional parceiro (subitens 6.01 e 6.02 com `tpAjusteBC` 9), as regras sem código mandam subtrair o `vCalcAjusteBCISSQN` da receita bruta quando `regApIBSCBSSN` for 1 ou 2, e não subtrair quando for 3.

# 8. Indicador de operação (cIndOp)

O Anexo VII traz **40 códigos** de seis dígitos baseados no art. 11 da LC 214, contra 26 do Anexo C v1.01 (o documento 34 falava em 27; a planilha antiga tem 26). Há 18 códigos novos e 4 removidos (030103, 030104, 050103, 050104). Em dois códigos o local de incidência mudou: o 030102 e o 050102 eram "endereço do adquirente" e agora são "local da prestação, diverso do estabelecimento do fornecedor". Das 40 linhas, 28 valem para a NFS-e, 2 só para a NF-e (010104 e 010105), 1 só para a NFS-e Via (080101) e 9 não estão marcadas para nenhum desses documentos (010201, 010202, 090101, 090102, 110101, 110201, 120101, 130101, 130201).

| Código | Tipo de operação | Local de incidência do IBS (NFS-e) | NF-e | NFS-e | Via | Situação |
|---|---|---|---|---|---|---|
| 010101 | Bem Móvel Material | Estabelecimento do Prestador/Fornecedor | - | S | - | novo |
| 010102 | Bem Móvel Material | Local da Prestação | - | S | - | novo |
| 010103 | Bem Móvel Material | Endereço do Destinatário | - | S | - | novo |
| 010104 | Bem Móvel Material | - | S | - | - | novo |
| 010105 | Bem Móvel Material | - | S | - | - | novo |
| 010106 | Bem Móvel Material | Endereço do Tomador/Adquirente | - | S | - | novo |
| 010201 | Aquisição de veículo automotor terrestre, aquático ou aéreo | - | - | - | - | novo |
| 010202 | Aquisição de veículo automotor em licitação promovida pelo (...) | - | - | - | - | novo |
| 020101 | Operação com bem imóvel, bem móvel imaterial, inclusive (...) | Localidade do Imóvel | - | S | - | existia |
| 020102 | Operação com bem imóvel, bem móvel imaterial, inclusive (...) | Localidade do Imóvel | - | S | - | novo |
| 020201 | Serviço prestado fisicamente sobre bem imóvel | Localidade do Imóvel | - | S | - | existia |
| 020202 | Serviço prestado fisicamente sobre bem imóvel | Localidade do Imóvel | - | S | - | novo |
| 020301 | Serviço de administração e intermediação de bem imóvel | Localidade do Imóvel | - | S | - | existia |
| 020401 | Serviços de locação, sublocação, arrendamento, direito de (...) | Localidade do Imóvel | - | S | - | novo |
| 030101 | Serviço prestado fisicamente sobre a pessoa ou fruído (...) | Estabelecimento do Prestador/Fornecedor | - | S | - | existia |
| 030102 | Serviço prestado fisicamente sobre a pessoa ou fruído (...) | Local da Prestação | - | S | - | significado mudou |
| 040101 | Serviço de planejamento, organização e administração de feiras, (...) | Local do Evento | - | S | - | existia |
| 050101 | Serviço prestado fisicamente sobre bem móvel material | Estabelecimento do Prestador/Fornecedor | - | S | - | existia |
| 050102 | Serviço prestado fisicamente sobre bem móvel material | Local da Prestação | - | S | - | significado mudou |
| 050201 | Serviços portuários | Local da Prestação | - | S | - | existia |
| 060101 | Serviço de transporte de passageiros | Local da Prestação (Início do Transporte) | - | S | - | existia |
| 070101 | Serviço de transporte de carga | Local da Prestação | - | S | - | existia |
| 070102 | Serviço de transporte de carga | Local da Prestação (Local da Retirada) | - | S | - | existia |
| 080101 | Serviço de exploração de via | Localização do Trecho (NFS-e Via) | - | - | S | existia |
| 090101 | Serviço de telefonia fixa e demais serviços de comunicação (...) | - | - | - | - | novo |
| 090102 | Serviço de telefonia fixa e demais serviços de comunicação (...) | - | - | - | - | novo |
| 100101 | Cessão de espaço para prestação de serviços publicitários, em (...) | Endereço do Tomador/Adquirente | - | S | - | existia |
| 100102 | Cessão de espaço para prestação de serviços publicitários, em (...) | Endereço do Destinatário | - | S | - | existia |
| 100201 | Cessão de espaço para prestação de serviços publicitários, em (...) | Endereço do Destinatário | - | S | - | existia |
| 100301 | Demais serviços, em operações onerosas | Endereço do Tomador/Adquirente | - | S | - | existia |
| 100302 | Demais serviços, em operações onerosas | Endereço do Destinatário | - | S | - | existia |
| 100401 | Demais serviços, em operações não onerosas | Endereço do Destinatário | - | S | - | existia |
| 100501 | Demais bens, em operações onerosas | Endereço do Tomador/Adquirente | - | S | - | existia |
| 100502 | Demais bens, em operações onerosas | Endereço do Destinatário | - | S | - | existia |
| 100601 | Demais bens, em operações não onerosas | Endereço do Destinatário | - | S | - | existia |
| 110101 | Operações com abastecimento de água, gás canalizado e energia (...) | - | - | - | - | novo |
| 110201 | Operações com abastecimento de água, gás canalizado e energia (...) | - | - | - | - | novo |
| 120101 | Nas aquisições de energia elétrica realizadas de forma (...) | - | - | - | - | novo |
| 130101 | Operações de transporte dutoviário de gás natural | - | - | - | - | novo |
| 130201 | Operações de transporte dutoviário de gás natural | - | - | - | - | novo |

A coluna "Característica" e o dispositivo legal de cada código estão na aba cIndOp da planilha.

**`Cad_Indicador_Operacao`, com vigência, no lugar do domínio de `Cad_Classe_Sistema`.** A tabela muda a cada versão (quatro códigos saíram e 18 entraram entre o Anexo C v1.01 e o Anexo VII v1.03.00) e leva três marcas por documento (`Aplica_Nfe`, `Aplica_Nfse`, `Aplica_Nfse_Via`) e um local de incidência. Isso é mais do que um domínio de código e descrição: proponho catálogo próprio, com versão por vigência, e os quatro códigos removidos ficam com fim de vigência. `Mov_Nota_Fiscal_Saida_Item.ID_Indicador_Operacao` (P-19 do documento 34) e `Cad_Servico_Tributacao_Nacional_Correlacao.ID_Indicador_Operacao` passam a apontar para ele.

**Regra de derivação do local de incidência.** Cada código traz o local onde o IBS é devido. O catálogo guarda, em `ID_Criterio_Local_Operacao` (domínio `criterio_local_operacao` de `Cad_Classe_Sistema`), a regra aplicável, e o ERP resolve o município (`Mov_Nota_Fiscal_Saida_Item.ID_Municipio_Incidencia_Ibs`) a partir dela: estabelecimento do fornecedor, local da prestação (inclusive início do transporte e local da retirada), endereço do destinatário, endereço do adquirente, localidade do imóvel ou local do evento. O domínio atual só tem cinco valores genéricos; propõe-se estender com os valores abaixo (a aba cIndOp mostra o valor de cada código).

| Local de incidência no Anexo VII | Valor proposto em `criterio_local_operacao` |
|---|---|
| Estabelecimento do Prestador/Fornecedor | estabelecimento_fornecedor |
| Local da Prestação | local_prestacao |
| Endereço do Destinatário | domicilio_destinatario |
| Endereço do Tomador/Adquirente | domicilio_adquirente |
| Localidade do Imóvel | local_imovel |
| Local do Evento | local_evento |
| Local da Prestação (Início do Transporte) | local_prestacao_inicio_transporte |
| Local da Prestação (Local da Retirada) | local_prestacao_retirada |
| Localização do Trecho (NFS-e Via) | trecho_via (NFS-e Via, fora do escopo) |
| - | não usado na NFS-e |

Por esse caminho o critério deixa de ser digitado e passa a ser derivado do código, como o P-19 do documento 34 já queria. Os códigos do Anexo VII sem marca de NF-e nem de NFS-e ficam no catálogo com as três marcas em "não", prontos para outros documentos que usem o art. 11 da LC 214, sem tocar a NFS-e.

# 9. Regras de negócio

Comparei os códigos E da aba RN DPS_NFS-e: 478 na v1.04.01 e 428 na v1.01. **80 códigos são novos e 30 foram removidos**; dos 398 comuns, 137 têm o texto da regra ou da mensagem alterado: 82 são ajustes de redação (erro de digitação, nome de campo trocado), 38 reescrevem a mesma regra e **17 passam a carregar outra regra com o mesmo código** (por exemplo E0455, E0462, E0901 e E0449). O código de erro, portanto, não é chave estável entre versões do leiaute. Além dos códigos, há 157 linhas com código "EXXX" (sem código definitivo): **71 vivas** e 86 tachadas. As tachadas, quase todas sobre as notas de ajuste, a NT diz que estão em evolução. Cinco linhas com código real também estão tachadas (E0446, E0454, E0675, E1529, E1531).

**Regras novas por tema.**

| Tema | Códigos novos | Regra vira parâmetro ou tratamento no dicionário |
|---|---|---|
| Locação de imóveis (subitem 99.03) | 16 | Campo novo Exige_Grupo_Locacao em Cad_Servico_Tributacao_Nacional (vigência); cIndOp 02xxxx e unidades obrigatórias vêm de Cad_Indicador_Operacao; os valores calculados são derivados. |
| IBS/CBS: indicação de tributação | 12 | Campo novo Indicador_Tributacao_Ibs_Cbs (ind_gIBSCBS) em Cad_Cst, com vigência; o serviço de emissão consulta o indicador do CST/cClassTrib e liga ou desliga os grupos de IBS/CBS. Resultado da calculadora guardado como conferência (D-N36). |
| Ajuste de base de cálculo | 11 | Cad_Nfse_Tipo_Ajuste_Bc (flags e vigência) mais o espelho da parametrização municipal (Cad_Nfse_Aliquota_Servico_Municipal, doc 34). A lista de 51 subitens permitidos a ME/EPP no SN (E0451/E0452) vira campo Permite_Ajuste_Bc_Simples em Cad_Servico_Tributacao_Nacional, com vigência. |
| Retenção do ISSQN por vigência | 8 | Cad_Nfse_Retencao_Municipal (pacote opcional do doc 34, D-N19) com vigência de início e fim, regra e exceção por CNPJ/CPF e serviço. É parâmetro do município; o ERP guarda o espelho em cache. |
| Tomador e destinatário: identificação e endereço | 7 | Regra de emissão que depende de ind_gIBSCBS e de indDest; CEP contra município na tabela do IBGE/Correios (Cad_Municipio). |
| Importação de serviço (emitente tomador ou intermediário) | 5 | Regra de emissão sobre Mov_Nfse_Dps.Tipo_Emitente (2 ou 3): sem CNPJ/CPF do prestador, identifica por NIF, tribISSQN = 1. Estrutural do leiaute, sem parâmetro. |
| Substituição de NFS-e | 5 | Campos que não podem mudar na substituição: regra do serviço de emissão sobre Mov_Nfse_Dps (dCompet, cTribNac, cTribMun, local, tomador, valor). Prazo máximo é parâmetro do município (até 2 anos). |
| Bens móveis (99.04.01) | 4 | Campo novo Exige_Grupo_Bens_Moveis em Cad_Servico_Tributacao_Nacional (vigência); NCM validada em Cad_Classificacao_Mercadoria. |
| Atividade de evento (12.13 e 17.10) | 3 | Exige_Grupo_Evento em Cad_Servico_Tributacao_Nacional (P-20 do doc 34); município do evento validado em Cad_Municipio. |
| Compartilhamento municipal por data | 1 | Parâmetro com vigência em Cad_Dfe_Leiaute: Data_Limite_Compartilhamento_Me_Epp = 01/11/2026. Só vale para o ADN (nota compartilhada pelo município); o emissor nacional não aplica. |
| Novos fatos geradores: compartilhamento | 1 | Campo novo Somente_Sefin_Nacional em Cad_Servico_Tributacao_Nacional (vigência) para 99.03.xx e 99.04.01, e roteamento por Cad_Autoridade_Fiscal_Atendimento (D-N33). Rejeição só no ADN. |
| Obrigatoriedade por data | 1 | Parâmetro com vigência em Cad_Dfe_Leiaute: Data_Inicio_Obrigatoriedade_Ibs_Cbs_Nfse = 01/10/2026 (competência igual ou posterior). Nunca fixar a data no código. |
| IBS/CBS: crédito presumido | 1 | Campo novo Indicador_Credito_Presumido_Operacao (ind_gCredPresOper) em Cad_Cclasstrib e tabela de cCredPres (IT 2025.002). |
| Unicidade da NFS-e | 1 | Chave única em Mov_Documento_Fiscal: município emissor, tipo e inscrição do emitente e número da NFS-e. |
| Benefício municipal | 1 | Cad_Nfse_Beneficio_Municipal (pacote opcional do doc 34): tipo do benefício conforme o número parametrizado pelo município. |
| IBS/CBS: local de incidência | 1 | Local de incidência derivado de Cad_Indicador_Operacao (coluna Local_Incidencia_Ibs) e do tipo de emitente (Mov_Nfse_Dps.Tipo_Emitente). |
| Regra riscada na v1.04.01 | 1 | Sem efeito no desenho: a regra aparece riscada no Anexo VI v1.04.01. |
| Diferimento | 1 | Linha de diferimento em Mov_Apuracao_Tributo_Item_Complemento (P-4): vDifMun obrigatório se pDifMun foi informado. |

**Regras removidas por tema.**

| Tema | Códigos removidos | Substituta na v1.04.01 | Efeito no desenho |
|---|---|---|---|
| Reembolso (IBS/CBS) | 10 | nenhuma | Regra com data (documento anterior a 31/12/2025) deixa de existir; nenhuma data a parametrizar. |
| Dedução/redução do ISSQN | 7 | E0445 | Substituída: mesma regra com vDedRed trocado por vAjusteBC (regime especial de tributação). |
| Retenção do ISSQN | 6 | E0653 a E0665 | Reescrita: a retenção passa a ser regra com vigência parametrizada pelo município (exceções e obrigações por CNPJ/CPF e serviço). |
| Local de incidência e tomador | 2 | nenhuma identificada | A exigência do tomador por cIndOp saiu da lista de códigos antigos (030102, 050102, 030103...). |
| Documento de dedução (chave de NFS-e) | 2 | nenhuma identificada | Sem substituta no Anexo; a conferência da chave (existência e cancelamento) continua como regra do ADN sobre dFeNacional, a confirmar. |
| Imóvel no exterior | 2 | nenhuma | O endereço do imóvel no exterior deixou de existir em gUnidImob. |
| Substituição por rejeição do tomador | 1 | nenhuma | Verificação do evento de rejeição do tomador saiu do bloco. |

**Regras com data ou vigência.** As que dependem de data ou de regime municipal entram como parâmetro com vigência, nunca no programa; as estruturais ficam como regra do serviço de emissão:

| Código | O que diz | Onde fica |
|---|---|---|
| E0855 | É obrigatório declarar as informações de IBS/CBS quando a data de competência for igual ou posterior a **01/10/2026** | `Cad_Dfe_Leiaute`: `Data_Inicio_Obrigatoriedade_Ibs_Cbs_Nfse`, com vigência |
| E0163 | NFS-e de emitente ME/EPP (`opSimpNac` = 3) só pode ser compartilhada pelo município com o ADN se a competência for igual ou menor que **01/11/2026** | `Cad_Dfe_Leiaute`: `Data_Limite_Compartilhamento_Me_Epp`. Vale só para o ADN; o emissor nacional não aplica |
| E0309 | Rejeita o compartilhamento de NFS-e com `cTribNac` 99.03.xx ou 99.04.01 | `Cad_Servico_Tributacao_Nacional.Somente_Sefin_Nacional` (com vigência) e o roteamento da D-N33 |
| E0027, E0086, E0109, E0225 e E0531 | Importação de serviço: se o prestador está no exterior e o local da prestação é no Brasil, o emitente é o tomador ou o intermediário; sem CNPJ ou CPF do prestador, sem nome do tomador (quando o emitente é o tomador) e com `tribISSQN` = 1 | Regra de emissão sobre `Mov_Nfse_Dps.Tipo_Emitente` (2 ou 3). Estrutural do leiaute, sem parâmetro |
| E0653 a E0665 | Retenção do ISSQN proibida ou obrigatória conforme a vigência da regra municipal, o serviço e a exceção por CNPJ ou CPF | `Cad_Nfse_Retencao_Municipal` (pacote opcional do documento 34, D-N19), com início e fim de vigência |

O momento de execução de cada regra (emissor nacional ou ADN, DPS do prestador, do tomador ou por decisão judicial) está na aba "RN novas" da planilha, nas seis colunas de aplicação. As 71 regras vivas sem código estão na aba "RN sem código": o ERP as implementa, mas não consegue carregá-las em `Cad_Dfe_Codigo_Retorno` (D-N65). Os 478 códigos E vão para `Cad_Dfe_Codigo_Retorno` como carga inicial, **por versão do leiaute e com vigência** (o código sozinho não identifica a regra: 17 deles mudaram de sentido).

# 10. Eventos e recepção

Nada novo. A aba RN_RECEPCAO_DPS (17 linhas) só valida o certificado de transmissão (E1200 a E1209), a área de dados (E1225 e E1226) e o tipo de DF-e (E1228, E1229, E1235 e E1242). O texto das regras é igual ao do v1.01, tal como as abas EXPORTACAO_EMISSÃO_NFS-e (117 linhas) e MUN.INCID_INFO.SERV. (341 linhas), que comparei linha a linha depois de normalizar os espaços. O Anexo VI não traz aba de eventos; a NT 009 também não altera os eventos. A classificação de eventos do documento 34 (59 tipos) segue valendo.

# 11. Lacunas versus cobertura

Situação das 450 linhas do leiaute novo:

| Situação | Linhas | Significado |
|---|---|---|
| Coberto | 139 | O dicionário já tem onde gravar |
| Coberto por proposta do doc 34 | 142 | A entidade ou o campo existe como proposta do documento 34, ainda não consolidada |
| Derivado (não grava) | 19 | A nota calcula; o ERP não grava |
| Só no XML | 16 | Descrição, versão e assinatura devolvidas pelo ADN, guardadas com o XML |
| Lacuna nova | 35 | Falta lugar no dicionário e no documento 34 |
| Agrupador (sem dado próprio) | 96 | Grupo ou raiz, sem dado próprio |
| A confirmar | 3 | Falta confirmação da fonte ou do mapeamento |
| Total | 450 |  |

As 35 lacunas novas, por assunto:

| Assunto | Linhas | Destino proposto |
|---|---|---|
| Locação de imóveis (subitem 99.03) | 8 | `Mov_Nfse_Dps` (5 campos novos) e `Mov_Nfse_Unidade_Ajuste_Bc` |
| Locação de bens móveis (subitem 99.04.01) | 3 | `Mov_Nfse_Bem_Movel_Locado` |
| Condomínios (subitem 99.05) | 10 | `Mov_Nfse_Condominio_Cobranca`, `Mov_Nfse_Condominio_Desconto` e `Mov_Nfse_Dps` (data de vencimento) |
| Simples Nacional: IBS e CBS | 6 | `Mov_Nfse_Dps` (regime e atividade) e 15º tipo de `Mov_Apuracao_Tributo_Item_Complemento` |
| Comércio exterior | 4 | `Mov_Nfse_Comercio_Exterior` (3 campos) e `Mov_Nfse_Dps` (ajuste da base) |
| Atividade de evento | 1 | `Mov_Nfse_Atividade_Evento` |
| NFS-e de ajuste (valor de IBS e CBS a ajustar) | 2 | 16º tipo de `Mov_Apuracao_Tributo_Item_Complemento` |
| Retorno: versão da calculadora | 1 | `Mov_Nfse_Dps` |
| Total | 35 |  |

As três linhas a confirmar são `nDFSe` (número do DF-e no ambiente gerador, se vira `Mov_Documento_Fiscal.Nsu` ou outro campo), `CAEPF` do prestador (qual tipo de inscrição em `Cad_Participante_Inscricao`) e `tpRetPisCofins` (mapeamento do domínio 0 a 9 para as retenções em `Mov_Titulo_Retencao`). Um achado fora do leiaute: o dicionário não guarda **nenhum** dos indicadores oficiais das tabelas de CST e de classificação tributária (por exemplo `ind_gRed`, `ind_gDif`, `tpRBSN`, `ind_gEstornoCred`), e 24 linhas de regra da NFS-e citam `ind_gIBSCBS` (ou `ind_IBSCBS`) e `tpRBSN` (D-N62).

# 12. Entidades e campos propostos

Tudo abaixo é proposta. Nada entra no dicionário sem o seu "consolidar".

**Entidades novas** (as nove são nomes novos deste documento; a `Mov_Nfse_Ajuste_Bc_Documento` renomeia a `Mov_Nfse_Deducao_Documento` do P-9):

| Entidade | Tipo | Finalidade | Campos principais | Decisão |
|---|---|---|---|---|
| `Cad_Indicador_Operacao` | Entidade nova (catálogo com vigência) | Catálogo do indicador da operação (cIndOp) da NFS-e e dos demais documentos que usam o art. 11 da LC 214. Substitui o domínio indicador_operacao_nfse de Cad_Classe_Sistema. | ID_Indicador_Operacao; ID_Indicador_Operacao_Versao; Codigo (6); Tipo_Operacao; Caracteristica_Fornecimento; Local_Fornecimento; Dispositivo_Legal; Observacao; Aplica_Nfe; Aplica_Nfse; Aplica_Nfse_Via; ID_Criterio_Local_Operacao (→ Cad_Classe_Sistema, domínio criterio_local_operacao); Local_Incidencia_Ibs; Vigencia_Inicio; Vigencia_Fim; Motivo_Vigencia | D-N58 |
| `Cad_Nfse_Tipo_Ajuste_Bc` | Entidade nova (catálogo com vigência) | Catálogo dos tipos de ajuste de base de cálculo (tpAjusteBC) com a repercussão em ISSQN, IBS/CBS e receita bruta do Simples. | ID_Tipo_Ajuste_Bc; ID_Tipo_Ajuste_Bc_Versao; Codigo (até 3); Descricao; Reduz_Base_Issqn; Reduz_Base_Ibs_Cbs; Reduz_Receita_Bruta_Sn; Exige_Documento_Fiscal; Exige_Descricao; Referencia_Legal; Vigencia_Inicio; Vigencia_Fim; Motivo_Vigencia | D-N59 |
| `Mov_Nfse_Ajuste_Bc_Documento` | Entidade renomeada e unificada (era Mov_Nfse_Deducao_Documento no doc 34, P-9) | Documentos que justificam o ajuste da base de cálculo (até 1.000 por NFS-e): dedução do ISSQN e reembolso, repasse ou ressarcimento do IBS/CBS numa única linha. | ID_Ajuste_Documento; ID_Nfse_Dps; ID_Tipo_Ajuste_Bc; Descricao_Ajuste; Valor_Total_Documento; Valor_Ajuste_Aplicado; Data_Emissao_Documento; Data_Competencia_Documento; Tipo_Chave_Dfe; Descricao_Tipo_Chave_Dfe; Chave_Dfe; ID_Municipio_Documento_Fiscal; Numero_Documento_Fiscal; Descricao_Documento_Fiscal; Numero_Documento_Nao_Fiscal; Descricao_Documento_Nao_Fiscal; dados do fornecedor (documento, NIF, nome, endereço, telefone, e-mail) | D-N59 |
| `Mov_Nfse_Unidade_Imobiliaria` | Entidade nova | Unidades imobiliárias da operação de locação, cessão onerosa ou arrendamento (até 99 por NFS-e, mesmo município). | ID_Unidade_Nfse; ID_Nfse_Dps; ID_Imovel (→ Cad_Imovel); Codigo_Cib; Inscricao_Imobiliaria_Fiscal; ID_Local_Operacao (→ Cad_Local_Operacao, Tipo_Local = imovel) | D-N60 |
| `Mov_Nfse_Unidade_Ajuste_Bc` | Entidade nova | Parcelas que não integram a base do IBS/CBS na locação, por unidade (tributos, emolumento, condomínio, redutor social e outras). | ID_Unidade_Ajuste; ID_Unidade_Nfse; ID_Tipo_Parcela; Descricao_Parcela; Valor_Parcela | D-N60 |
| `Mov_Nfse_Bem_Movel_Locado` | Entidade nova | Bens móveis objeto de locação (subitem 99.04.01), até 1.000 por NFS-e. | ID_Bem_Locado; ID_Nfse_Dps; ID_Classificacao_Mercadoria (→ Cad_Classificacao_Mercadoria); Descricao_Bem; Quantidade | D-N60 |
| `Mov_Nfse_Condominio_Cobranca` | Entidade nova (condicional) | Cobranças de condomínio (subitem 99.05) e seu detalhamento, numa tabela com dois níveis (cobrança e detalhe). | ID_Cobranca; ID_Nfse_Dps; ID_Cobranca_Pai; Nivel {cobranca, detalhe}; ID_Tipo_Cobranca; ID_Tipo_Detalhe; Descricao_Cobranca; Valor_Cobranca | D-N61 |
| `Mov_Nfse_Condominio_Desconto` | Entidade nova (condicional) | Descontos concedidos nas cobranças de condomínio (até 10). | ID_Desconto; ID_Nfse_Dps; Tipo_Desconto {incondicionado, condicionado}; Valor_Desconto; Descricao_Desconto | D-N61 |
| `Cad_Nfse_Detalhe_Cobranca_Permitido` | Entidade nova (condicional, parâmetro com vigência) | Combinações permitidas entre tipo de cobrança e tipo de detalhamento do condomínio (a regra da nota do leiaute sobre tpDetCobranca). | ID_Detalhe_Permitido; ID_Tipo_Cobranca; ID_Tipo_Detalhe; Vigencia_Inicio; Vigencia_Fim; Motivo_Vigencia | D-N61 |

**Campos e valores novos em entidades já existentes ou propostas:**

| Entidade | Situação | Mudança | Por que | Decisão |
|---|---|---|---|---|
| `Cad_Cst` | existente | Campos novos: Indicador_Tributacao_Ibs_Cbs (ind_gIBSCBS), Indicador_Reducao (ind_gRed), Indicador_Diferimento (ind_gDif), Indicador_Transferencia_Credito (ind_gTransfCred) | Indicadores oficiais da tabela de CST do IBS/CBS (IT 2025.002 v1.70). As regras da NFS-e usam o ind_gIBSCBS para decidir a presença dos grupos de IBS/CBS (E1518, E1524, E1562, E0859, E0960 e outras); os demais indicadores vêm da mesma tabela oficial. | D-N62 |
| `Cad_Cclasstrib` | existente | Campos novos: Indicador_Estorno_Credito (ind_gEstornoCred), Indicador_Tributacao_Regular (ind_gTribRegular), Indicador_Credito_Presumido_Operacao (ind_gCredPresOper), Tipo_Receita_Bruta_Sn (tpRBSN), Tipo_Doacao (tpDoacao), Indicador_Duimp (ind_DUIMP) e as marcas de modelo (indNFe, indNFSe, indNFSeVia e outras) | O dicionário não guarda nenhum indicador oficial (zero ocorrências no modelo). tpRBSN decide vReceitaBrutaSN e gTribSN; ind_gEstornoCred decide o grupo de estorno; tpDoacao decide indDoacao. | D-N62 |
| `Cad_Servico_Tributacao_Nacional` | existente (doc 34 já propôs Regra_Local_Incidencia, Exige_Grupo_Obra e Exige_Grupo_Evento) | Campos novos: Exige_Grupo_Locacao (99.03), Exige_Grupo_Bens_Moveis (99.04.01), Exige_Grupo_Condominio (99.05), Somente_Sefin_Nacional, Permite_Ajuste_Bc_Simples. Códigos novos além dos sete do doc 34: 99.05 (condomínios) | Os campos são parâmetros com vigência (a entidade já tem). Somente_Sefin_Nacional atende E0309 e a D-N33. | D-N60 |
| `Cad_Servico_Tributacao_Nacional_Correlacao` | existente | ID_Indicador_Operacao passa a apontar para Cad_Indicador_Operacao; campo novo ID_Atividade_Simples (cAtvSN: 16.01 → 10; 99.04.01 → 11; 7.02 e 7.05 → 12 ou 13) | As regras de cAtvSN do Anexo ainda estão sem código (EXXX) e ligam o código de serviço à atividade do Simples. | D-N58 |
| `Mov_Nfse_Dps` | proposta do doc 34 (não existe no modelo) | Campos novos: Regime_Apuracao_Ibs_Cbs_Sn, ID_Atividade_Simples, Valor_Ajuste_Bc_Ibs_Cbs_Com_Ext, Percentual_Copropriedade, Valor_Total_Operacao_Imovel, Valor_Desconto_Incondicionado_Total, Valor_Desconto_Condicionado_Total, Data_Vencimento_Original, Versao_Calculadora_Ibs_Cbs. Renomeados: Percentual_Deducao → Percentual_Ajuste_Bc_Issqn; Valor_Deducao → Valor_Ajuste_Bc_Issqn | Soma-se aos 23 campos do P-8 do doc 34 e ao Indicador_Zfmalc da seção 5.1. | D-N60 e D-N64 |
| `Mov_Nfse_Comercio_Exterior` | proposta do doc 34 | Campos novos: Numero_Fatura, Valor_Fatura, Numero_Contrato_Cambio. Numero_Duimp (15) e Numero_Due (14) trocam nDI e nRE. O domínio de Modo_Prestacao ganha o valor 5 (consumo concomitante no país e no exterior) | O valor 5 exige emitir NFS-e regular para a parcela consumida no país, e informar em vServ só a parcela exportada ou importada. | D-N60 |
| `Mov_Nfse_Atividade_Evento` | proposta do doc 34 | Campo novo: ID_Municipio_Evento (→ Cad_Municipio) | Só nos subitens 12.13 e 17.10 e quando o local do evento difere do local da prestação. | D-N60 |
| `Mov_Apuracao_Tributo_Item_Complemento` | proposta do doc 34 (14 tipos) | Dois tipos novos no domínio: ibs_cbs_simples_nacional (15º) e valor_ajuste_ibs_cbs (16º) | O 15º guarda gTribSN (alíquota e valor de IBS e CBS pelo SN); o 16º guarda gIBSCBSAjuste das NFS-e de ajuste. O estorno de crédito (gEstornoCred) já era o tipo estorno_credito. | D-N63 e D-N64 |
| `Mov_Nota_Fiscal_Saida` | existente com proposta do doc 34 (P-1) | Finalidade ganha crédito (finNFSe = 1) e débito (finNFSe = 2); Tipo_Nota_Debito e Tipo_Nota_Credito aceitam, na NFS-e, só 01 a 06 e 01 e 05 | Os mesmos campos do P-1 servem à NF-e e à NFS-e; o subconjunto por modelo vira parâmetro em Cad_Dfe_Leiaute. | D-N63 |
| `Cad_Local_Operacao` | existente | Tipo_Local ganha o valor imovel (já proposto no doc 34); uso para o endereço de gUnidImob | Sem campo novo além do que o doc 34 propôs. | - |
| `Cad_Simples_Opcao` | proposta do doc 33 | Situacao ganha o valor pendente | Atende opSimpNac = 4 (optante pendente). | D-N64 |
| `Cad_Dfe_Leiaute` | proposta do doc 34 | **Pela D-N95 (11/10/2026), as duas datas passam para `Cad_Dfe_Parametro_Regra`; ficam aqui só a versão e a data de início.** Parâmetros novos com vigência: Data_Inicio_Obrigatoriedade_Ibs_Cbs_Nfse (01/10/2026), Data_Limite_Compartilhamento_Me_Epp (01/11/2026), versão do leiaute 1.04.01 e dos anexos (VI v1.04.01, VII v1.03.00) | As datas das RN E0855 e E0163 nunca ficam no código. | D-N64 |

Os mesmos dados, com a ligação e a origem de cada entidade, estão na aba "Entidades propostas" da planilha.

# 13. Pendências

Dúvidas das fontes e itens abertos. Nenhuma trava o desenho; todas têm tratamento provisório. A numeração Q-1 a Q-15 é deste documento.

Reli o PDF da NT 009 que chegou depois (arquivo `nt-009-se-cgnfse-v1-0-1.pdf`) e comparei com cada dúvida. Das 15, **nenhuma ficou resolvida só pela NT**, **5 são conflito entre NT e Anexo** e **10 seguem em aberto** (a NT não trata do assunto ou só o confirma). A coluna "O que a NT diz" mostra o que sustenta cada classificação.

| Nº | Dúvida | Onde aparece | Como tratei | Situação | O que a NT diz |
|---|---|---|---|---|---|
| Q-1 | Versões: a NT 009 cita o Anexo VI v1.04.00 e o Anexo VII v1.02.00; os arquivos recebidos são v1.04.01 e v1.03.00 | NT 009, seção 1, e nomes dos arquivos | Usei os arquivos recebidos. A sequência é coerente: a NT 007 citava Anexo VI v1.03.00 e Anexo VII v1.01.00, a NT 009 cita v1.04.00 e v1.02.00, e os arquivos de agora são uma revisão menor posterior. Nenhuma NT recebida cita a v1.04.01 nem a v1.03.00 | Conflito entre NT e Anexo | A NT só confirma os números que ela cita; não explica a revisão posterior |
| Q-2 | `gAjusteBCLocImoveis`: a NT diz 0-1000, o Anexo diz 0-10 por unidade | NT 009, seção 2.6, e aba LEIAUTE | Valeu o Anexo (10), que é a revisão mais nova. O limite fica em parâmetro, não no modelo | Conflito entre NT e Anexo | A NT escreve 0-1000 na tabela do grupo e não comenta o número |
| Q-3 | `vBC` do IBS/CBS: o Anexo soma `vAjusteBCIBSCBSComExt` (o nome sugere redução, e o sinal é positivo); a NT não cita o campo nem o termo na fórmula | NT 009, seção 2.3; aba LEIAUTE | Segui o Anexo. Pedir confirmação do sinal e do alcance | Conflito entre NT e Anexo | A fórmula da NT termina em `vISSQN`, sem o termo do comércio exterior |
| Q-4 | `vReceitaBrutaSN`: o asterisco limita `vCalcAjusteBCISSQN` ao tipo 9, mas o campo também soma o ajuste percentual; e o indicador `tpRBSN` não está no dicionário | NT 009, seção 2.4; aba LEIAUTE e regras sem código | Campo derivado; só o cálculo com os indicadores (D-N62) fecha | Em aberto | A NT traz a mesma fórmula e o mesmo asterisco; não explica o percentual nem cita `tpRBSN` |
| Q-5 | `gIBSCBSAjuste`: a NT e a matriz o põem em `IBSCBS/valores/trib/`; a aba LEIAUTE o põe em `IBSCBS/valores/trib/gIBSCBS/` | NT 009, seção 2.2, matriz e aba LEIAUTE | Segui a aba LEIAUTE | Conflito entre NT e Anexo | A NT dá o caminho sem `gIBSCBS` |
| Q-6 | Matriz de ajuste: 30 das 430 linhas usam caminhos antigos; as regras de ajuste estão tachadas (86 linhas) | Aba NFS-e_AJUSTE_LEIAUTE | Estrutura sim, tela não, até sair sem tachado | Em aberto | A NT explica o tachado (regras "em evolução") e a matriz como "norteador"; não fala dos caminhos antigos |
| Q-7 | **71 regras vivas sem código** (EXXX), sobretudo `vReceitaBrutaSN`, `cAtvSN`, `gTribSN`, condomínios e `gEstornoCred` | Aba RN DPS_NFS-e | Implementar a regra e não carregar em `Cad_Dfe_Codigo_Retorno` até o código sair | Em aberto | A NT não trata de códigos de erro |
| Q-8 | Erros de digitação: `vAjuteAplic` (NT) contra `vAjusteAplic` (Anexo); a descrição de `vDescCondTot` na NT diz "incondicionado"; `xTpDesconto` é 1-1 embora a nota fale de "só quando" | NT 009, seções 2.3 e 2.6; aba LEIAUTE | Segui o Anexo, que corrigiu os dois primeiros. A NT não traz o grupo `condominios`, então o terceiro fica sem confirmação | Conflito entre NT e Anexo | Os dois primeiros erros estão no texto da NT; o grupo de condomínios não consta dela |
| Q-9 | Mudanças do Anexo que a NT 009 não descreve: destinatário fora de `IBSCBS`, condomínios, comércio exterior (DUIMP, DUE, fatura, câmbio), `cMun` do evento. A de `tpRetPisCofins` está na NT 007 (07/02/2026) | Aba LEIAUTE; NT 009 e NT 007 | Aceitei como estão. O `tpRetPisCofins` e o `vRetCSLL` ficam explicados pela NT 007; os demais, não há como conferir a intenção | Em aberto | A NT 009 diz que complementa as NTs anteriores, mas não cita nenhum desses itens; a NT 007 só cobre PIS, COFINS e CSLL |
| Q-10 | Vigência: o tipo 9 é novo mas a tabela dá início em 01/01/2022; os tipos 101 a 199 começam em 01/01/2026, e o IBS/CBS só é obrigatório para competências de 01/10/2026 (E0855) | Aba AJUSTE_BC_REPERCUSSÃO e RN | Copiei as datas da tabela e guardo a obrigatoriedade à parte | Em aberto | A NT não traz datas de vigência dos tipos nem a E0855 |
| Q-11 | E0163 (compartilhamento de ME/EPP até 01/11/2026) coincide com a data de migração do Simples para o Emissor Nacional em São Paulo (D-N25 do documento 35). Não sei se há relação | Aba RN; documento 35 | Parâmetro com vigência, sem inferir | Em aberto | A NT não cita a regra nem a data |
| Q-12 | `regApIBSCBSSN` = 2 (CBS pelo SN, IBS regular): sem par no dicionário; minha hipótese é o excesso do sublimite estadual | NT 009, seção 2.4; documento 36 | Campo guarda o declarado; confirmar a hipótese | Em aberto | A NT confirma os três valores e os textos, sem dizer quando vale o 2 |
| Q-13 | Cronograma: a NT diz que será publicado; a E0855 fala em 01/10/2026 e hoje é 06/10/2026, mas não sei se o leiaute 1.04.01 está em produção | NT 009, seção 1 | Tudo atrás de vigência em `Cad_Dfe_Leiaute` | Em aberto | A NT (04/06/2026) diz que o cronograma sai "nas próximas semanas"; a única data dela é o CNPJ alfanumérico, a partir de julho de 2026 |
| Q-14 | `cIndOp`: 9 códigos sem marca de documento; o 030102 e o 050102 mudaram de significado sem aviso na NT | Anexo VII | Carga com marcas em "não" e vigência; conferir quando houver nota emitida com esses códigos | Em aberto | A NT só cita o Anexo VII (base: art. 11 da LC 214) e não comenta códigos |
| Q-15 | 17 códigos de erro comuns às duas versões carregam outra regra na v1.04.01 (E0031, E0034, E0060, E0124, E0125, E0449, E0455, E0460, E0462, E0464, E0470, E0474, E0476, E0901, E0910, E0940 e E1531) | Aba RN DPS_NFS-e, comparada com a v1.01 | Carga de `Cad_Dfe_Codigo_Retorno` por versão do leiaute; a aba RN alteradas da planilha traz o antes e o depois | Em aberto | A NT não trata de códigos de erro |

# 14. Decisões para Alberto

A numeração continua depois da D-N51 (NF-e ABI, documento 34) e pula a D-N52 a D-N57, que ficam reservadas para a NFCom. A leitura do PDF da NT 009 que chegou depois não mudou nenhuma recomendação nem criou decisão nova (não há D-N65A): o texto é o mesmo que já tinha sido usado.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N58 | Indicador de operação (`cIndOp`) como catálogo próprio com vigência, `Cad_Indicador_Operacao`, carregado com os 40 códigos do Anexo VII, com as marcas por documento e o critério de local de incidência? Os 4 removidos ficam com fim de vigência | **Sim.** Substitui o domínio de `Cad_Classe_Sistema` e deixa o critério do local derivado do código |
| D-N59 | Ajuste de base de cálculo: uma entidade de documentos (`Mov_Nfse_Ajuste_Bc_Documento`, nome novo da do P-9) e um catálogo de tipos (`Cad_Nfse_Tipo_Ajuste_Bc`) com as três marcas e a vigência? Abandona a alternativa de duas entidades | **Sim.** O leiaute já fundiu os grupos; mantém os tipos 1, 3 e 4 como encerrados |
| D-N60 | Locação de imóveis, bens móveis e comércio exterior novo: desenhar agora (3 entidades e os campos de `Mov_Nfse_Dps`, `Mov_Nfse_Comercio_Exterior` e `Mov_Nfse_Atividade_Evento`) ou esperar o cronograma? A D-N8 (data de obrigatoriedade e limites da pessoa física) fica como está | Desenhar agora e ativar a emissão só com o cronograma. O leiaute existe, e o custo é de modelo, não de tela |
| D-N61 | Condomínios (subitem 99.05): a Mlegate ou algum cliente emite nota de condomínio? Se sim, aprova as três entidades condicionais | Não criar agora. Manter o desenho deste documento e criar só com cliente |
| D-N62 | Guardar os indicadores oficiais de CST e de classificação tributária (`ind_gRed`, `ind_gDif`, `ind_gTransfCred`, `tpRBSN`, `ind_gEstornoCred` e outros) em `Cad_Cst` e `Cad_Cclasstrib`, com vigência, a partir da IT 2025.002 v1.70? | **Sim.** 24 linhas de regra da NFS-e dependem de `ind_gIBSCBS` e `tpRBSN`; sem os indicadores o ERP não decide quais grupos de IBS/CBS informar nem a receita bruta do Simples |
| D-N63 | NFS-e de ajuste: reaproveitar `Finalidade`, `Tipo_Nota_Debito` e `Tipo_Nota_Credito` do P-1 (guardando o significado, não o dígito do XML) e o 16º tipo de complemento, sem entidade nova e sem tela até as regras saírem sem tachado? | Sim |
| D-N64 | Datas e Simples como parâmetro com vigência: E0855 (01/10/2026) e E0163 (01/11/2026) em `Cad_Dfe_Parametro_Regra`, com `Cad_Dfe_Leiaute` só com versão e data de início (D-N95, 11/10/2026); `opSimpNac` 4 como situação pendente em `Cad_Simples_Opcao`; `regApIBSCBSSN` em `Mov_Nfse_Dps`; 15º tipo de complemento para `gTribSN` | Sim, sem data nem código fixos no programa |
| D-N65 | Desenhar sobre o Anexo VI v1.04.01 apesar das divergências entre NT e Anexo (Q-1 a Q-9) e das 71 regras sem código? Em conflito, vale o Anexo. O código de erro passa a ser carregado por versão do leiaute (Q-15) | Sim. Registrar as dúvidas, perguntar ao Comitê Gestor o que for crítico (sinal de `vAjusteBCIBSCBSComExt`, `regApIBSCBSSN` = 2) e atualizar quando sair a v1.04.02 ou o cronograma |

**Posso consolidar?**
