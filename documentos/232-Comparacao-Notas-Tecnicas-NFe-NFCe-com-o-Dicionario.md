# Comparação das Notas Técnicas da NF-e e da NFC-e (e dos manuais e esquemas enviados) com o Dicionário — Documento 232 (revisão 2)

*Você enviou, entre 17/11/2026 e a mensagem "Todas as notas técnicas enviadas", as notas técnicas da NF-e e da NFC-e, a LC 227/2026, os manuais e os pacotes de esquemas XML, e escolheu "Comparar tudo com o dicionário" e "Comparar todas as versões" da NT 2025.002. Li o que dá para ler por inteiro, montei a linha do tempo da NT 2025.002 (v1.00 a v1.53) e a cadeia dos esquemas (PL_010b a PL_010h), conferi cada ponto contra o dicionário na revisão 48 (mais o que o D-N600 já aprovou) e separei o que é carga, o que é campo novo e o que já estava coberto. **Situação em 17/11/2026: aplicado na revisão 49** (documento 233, D-N603), com as Q232-1 a Q232-11 lidas como Sim. O texto abaixo é a proposta como foi escrita; a nota seguinte traz o que mudou na consolidação.*

Mlegate · Alberto Beyeler · Novembro de 2026

**Revisão 2 (17/11/2026), depois da sua mensagem sobre o MOC.** Você disse que o MOC que existe é o 7.0 (novembro de 2020) e que ele foi reformado por notas técnicas. Aceitei: **o Anexo I do MOC 7.0 mais as NT recebidas é a base**, e não peço mais o "Anexo I do MOC atual" nem a NT 2020.006. Reconstruí o texto em vigor da W16-10, da GAP03a-3 e da I08-90 (seção 4.1) e quatro coisas mudaram em relação à primeira versão: (1) a fórmula do total da NF-e (W16-10) leva o ICMS monofásico sujeito a retenção (`vICMSMonoReten`) desde 30/03/2023 e a exceção 3 foi trocada pela exceção 4 desde 01/07/2024, e as linhas do documento 230 estavam sem isso; (2) o IBS, a CBS e o IS **não entram no `vNF`**: entram no total do item (`vItem`) e num campo à parte, `vNFTot`, e as duas linhas `NFE-VNF-FORMULA-IBSCBS` da carga 48, que vieram de resumos de terceiros, saem e entram 9 linhas com o texto oficial; (3) a GAP03a-3 (rejeição 452) vale também para a NF-e (modelo 55) desde 13/10/2025; (4) a I08-90 está no MOC 7.0 e não está na carga. Perguntas novas: **Q232-10 e Q232-11**. A Q232-9 ficou só com os eventos 420110 a 420170 e a Q231-3 está encerrada.

**Revisão 3 (17/11/2026): consolidação.** Ao aplicar o documento na revisão 49 corrigi cinco contagens e um fato: (1) o cBenef são **66 linhas** (e não 69), porque a regra N12-97 é do modelo 55 só e as células "55/65" de GO, PR e RJ viram uma linha; (2) as linhas novas de regra são **103** (e não 107): a exceção 7 (CST 51 interna) estava contada na Q232-1 e nas 17 de CFOP, e o cBenef perdeu 3; a `Cad_Dfe_Parametro_Regra` fica com **137** linhas (e não 141); (3) os códigos de retorno novos são **37** (e não 31), contados por modelo e código (a Carga48 tinha 28 e a Carga49 tem 65); (4) as linhas novas de tipo de evento são **48** (e não 47), porque o 110300 vale também para o modelo 65 (NT 2026.006 v1.01); (5) o evento **112110 está definido** na NT 2025.002 v1.53 (a seção 7 dizia que não); só os eventos 420110 a 420170 seguem sem definição (Q232-9). A Q231-1 foi encerrada pela Q232-10 (d). Detalhes no documento 233.

# 1. Resumo

A comparação achou **três grupos de coisa**: o que fecha pontos que ficaram provisórios nos documentos 230 e 231, o que falta como carga (regras e códigos) e o que falta como estrutura (poucos campos e uma entidade). O resto já estava coberto.

| Destino | O que é | Tamanho |
|---|---|---|
| Fecha ponto provisório | A exceção 7 da N12-70 (agora com o texto completo, que inclui os CFOP 5.906 e 5.907 em operação interna) e a data do IBS/CBS no total do item (a NT 2025.002 v1.53 diz que só soma a partir de 2027) | 1 linha nova e 1 ajustada (Q232-1); a data do IBS/CBS foi revista na seção 4.1 |
| Carga de `Cad_Dfe_Parametro_Regra` | Regras de CFOP da NFC-e e da devolução, com as exceções por UF (RS, ES, SP, AM e CE) | 17 linhas novas (Q232-2) |
| Carga de `Cad_Dfe_Parametro_Regra` | Regras de código de benefício fiscal (cBenef) por UF, com as datas da NT 2019.001 v1.70 | 69 linhas (Q232-3) |
| Carga + 1 campo | Manifestação do destinatário: prazo de 90 dias (Ajuste SINIEF 14/26) e até 2 ocorrências de cada evento conclusivo | 3 linhas de prazo, 5 combinações, 8 códigos de retorno e 1 campo em `Cad_Dfe_Evento_Tipo` (Q232-4) |
| Campos novos | Grupo de pagamento da NF-e e da NFC-e: CNPJ transacional, UF, CNPJ do beneficiário e terminal (NT 2023.004 v1.20) | 4 campos em `Mov_Nota_Fiscal_Saida_Pagamento` (Q232-5) |
| Entidade nova | Detalhe de pagamento do evento ECONF (110750), que não tem onde ficar | 1 entidade, 14 campos (Q232-6) |
| Campo novo | `indDeduzDeson`: o ICMS desonerado deduz do valor do item | 1 campo em `Mov_Apuracao_Tributo_Item` (Q232-7) |
| Carga de `Cad_Dfe_Evento_Tipo` | Catálogo de eventos da NF-e e da NFC-e, que só tem 6 linhas | 47 linhas (43 códigos), provisórias (Q232-8) |
| Carga corrigida pelo MOC 7.0 e pelas NT (revisão 2) | Fórmula do total da NF-e com o ICMS monofásico retido e a exceção 4 (W16-10), total do item e total com IBS/CBS/IS (VB01 e W60), GAP03a-3 também para a NF-e e a I08-90 | 17 linhas novas, 2 que saem da carga 48, 5 encerradas por data e 10 linhas de código de retorno (Q232-10 e Q232-11) |
| Material que falta | NT ou esquema que define os eventos 420110 a 420170 | Q232-9 | Enviar a NT (ou o esquema) que define os eventos **420110 a 420170**? | **Sim**, quando puder |
| Q232-10 | Corrigir o total da NF-e e o total do item (seção 4.1): (a) fórmula W16-10 com o `vICMSMonoReten` desde 30/03/2023 (3 linhas encerradas e 3 novas); (b) exceção 3 encerrada em 30/06/2024 e exceção 4 desde 01/07/2024 (2 + 2 linhas, depende da Q232-7); (c) tirar as 2 linhas `NFE-VNF-FORMULA-IBSCBS` e carregar as 9 linhas de `vItem` e `vNFTot` desde 01/01/2027; (d) **não** estender `Compoe_Total_Documento` ao IBS e à CBS (Q231-1): o campo continua sendo só do `vNF`, e o IBS, a CBS e o IS entram no `vItem` e no `vNFTot` pela regra, não por marca na linha; (e) 8 códigos de retorno novos (1105, 1137, 1004 e 1094, nos modelos 55 e 65)? | **Sim**, provisório. Sem (a) o Motor rejeitaria uma NF-e de combustível com ICMS monofásico retido; sem (c) e (d) o `vNF` de 2027 sairia errado |
| Q232-11 | Acrescentar a linha da GAP03a-3 do modelo 55 desde 13/10/2025 (com o código 452 para o 55) e as 2 linhas da I08-90 (com o código 523)? | **Sim**, provisório. Com 1 nota no lote a NF-e também sai em modo síncrono, e a I08-90 é a pré-validação do CFOP interestadual |

A mudança estrutural total é **1 entidade e 20 campos** (14 da entidade nova e 6 em entidades que já existem). O resto é carga, sem mudar o desenho. O `vItem` e o `vNFTot` não viram campo: são derivados das linhas de tributo, como o total líquido (`vProdLiqTot`).

# 2. O que você enviou

| Grupo | O que chegou | Observação |
|---|---|---|
| Notas técnicas da NF-e e da NFC-e | 45 PDFs, 34 notas distintas (as de 2014 a 2026) | Três PDFs vieram repetidos (v1.52 e v1.34 da NT 2025.002 e o DANFE Tipo 2 da NT 2026.003); a NT 2023.002 e a NT 2025.001 vieram em duas versões cada |
| NT 2025.002 | v1.00, v1.10, v1.34, v1.51, v1.52 e v1.53 | A v1.53 (outubro de 2026) é a mais recente e traz o texto oficial das regras de devolução (VC02) e da soma do item (VB01) |
| Lei | LC 227/2026 | Já estudada no documento 138; não revi |
| Manuais | Manual de Contingência, Manual do Emissor, Manual de Usuários da SVRS, Manual do SVAN, Boas Práticas da NFC-e, Contingência Off-line v2.0, DANFE NFC-e e QR Code, Anexos I a IV e o MOC 7.0 (Anexo I e Visão Geral) | **O MOC 7.0 (novembro de 2020) é o MOC em vigor, reformado por NT** (sua mensagem de 17/11/2026). É a base das regras de validação, com as NT por cima (seção 4.1) |
| Esquemas XML | Cerca de 40 pacotes: PL_009q e PL_010b a PL_010h (NF-e e NFC-e), eventos (cancelamento, CC-e, EPEC, manifestação, ECONF, insucesso, entrega, ator interessado, averbação, prorrogação, Suframa, RTC), consulta de situação, GTIN, distribuição de DF-e e CNPJ alfanumérico | Comparei todas as versões entre si por programa |
| Tabelas | 18 planilhas | **São cópias das que você enviou em 16/11/2026**; não mudou nada |
| Portal da SVRS | 2 páginas em PDF | Só índice de serviços |

**Como li.** Li por inteiro e conferi regra por regra: NT 2023.003 v1.40, NT 2026.009, NT 2019.001 v1.70, NT 2020.001 v1.60, NT 2024.002 (ECONF), NT 2023.004 v1.20, NT 2026.005 e o histórico, os grupos e as regras de devolução e de soma do item da NT 2025.002 v1.53. As demais li pelo controle de versões, pelo resumo e por conferência de palavras-chave contra o dicionário: não é leitura regra por regra, e a seção 11 diz o que isso deixa em aberto.

# 3. NT 2025.002 (IBS, CBS e IS): linha do tempo e esquemas

## 3.1. Versões da NT

| Versão | Publicação | O que mudou | Produção |
|---|---|---|---|
| 1.00 e 1.01 | 03/2025 e 04/2025 | Campos de controle e eventos para a apuração | 01/10/2025 (1.01) |
| 1.10 | 06/2025 | Esquema com os campos do IBS, CBS e IS (opcionais); regras; eventos da apuração | 06/10/2025 |
| 1.20 | 07/2025 | Detalhamento do cronograma e novas regras | 06/10/2025 |
| 1.30 a 1.34 | 10/2025 a 12/2025 | Esquema completo, regras, correções; gRed só com alíquota maior que zero (1.33); UB12-10 (início da obrigatoriedade) adiada | 10/11/2025 (1.30), regras de 02/02/2026 |
| 1.35 e 1.36 | 03/2026 e 04/2026 | Ajustes SINIEF 49/25 e 8/26; nota de crédito 06 (retorno por recusa parcial); I08-140, I08-141 e I08-144 | 03/08/2026 |
| 1.40 | 05/2026 | **cIndOp (B25d), refDFeAnt (BB05), ISUFEmit (C22), gALCZFMCBS (UB66a), gDevTrib (cashback), tpEnteGov 5 e 6, tpOperGov 3 e 4**; evento 211110 com novo leiaute; **evento 211120 eliminado**; grupo DFeReferenciado na devolução (VC02-14) | 03/08/2026; VC02-14 em 03/11/2026 |
| 1.50 | 06/2026 | **Reformulação da monofasia dos combustíveis** (sai o diferimento monofásico, entram gMonoPadrao, gMonoReten, gMonoRet e gpBioDiferenca) | 03/11/2026; regras em 16/11/2026 |
| 1.51 | 07/2026 | Alteração de regras (UB13, UB18, UB22, UB26, UB37, UB40, UB45, UB56, UB59, UB64, I08-140, I08-144, VC02-14, VC02-30 e outras) | 05/10/2026 |
| 1.52 | 09/2026 | Correção da VC02-50; VC02-14 passa de 05/10/2026 para 03/11/2026 | 03/11/2026 |
| 1.53 | 10/2026 | Na devolução a chave pode vir no cabeçalho ou no item, com `nItem` opcional; **no cabeçalho a devolução passa a ter uma única ocorrência** (B25-40); alteradas UB12-10, VC02-14, VC02-20, VC02-30, VC02-40, VC02-50, VC03-20 e 3BA02 | 16/11/2026 |

## 3.2. Cadeia dos esquemas (diferenças entre pacotes consecutivos)

| Pacote | NT | O que traz (campos e tipos) |
|---|---|---|
| PL_010b v1.00, v1.20 e v1.30 | 2025.002 | Base do IBS, CBS e IS |
| PL_010d v1.03 | 2026.001 | `infPAA` (CNPJPAA e assinatura do PAA), `procEmi` = 4, `pDif`, `vICMSOp` e `vICMSDif` passam a obrigatórios no diferimento |
| PL_010e v1.02 | 2025.002 v1.40 | `cIndOp`, `ISUFEmit`, `gALCZFMCBS`, `refDFeAnt` (até 99), `refDFe` no grupo de pagamento de antecipação, `TChDFeRTC` e CNPJ alfanumérico (`TCnpjRTC`), `tpEnteGov` 5 e 6, `tpOperGov` 3 e 4, nota de crédito 06, `TRBSN` |
| PL_010f v1.04 | 2025.002 v1.50 | Monofasia reformulada (31 elementos novos, 14 retirados), `vNFTot` deixa de ser opcional no tipo |
| PL_010g v1.03 | NT 2026.006 e 2026.008 | `gPgtoVinc` (vinculação do pagamento), `CNPJBasePSP`, `ICMSPrevistoPagtoAntecip` e `vICMSPrevisto`, `vProdLiq`, `vProdLiqTot` e `vUnComLiq`; evento 110300; eventos 412140 e **420110 a 420170** na lista de eventos canceláveis |
| PL_010h v1.03 | NT 2026.005 | `tpRegimeIBSCBS`, `cAtivSN` e o grupo `gTribSN` (IBS e CBS do Simples Nacional) |

Todos os campos e grupos desta cadeia já estão no dicionário, **exceto os que a seção 6 lista** (pagamento e `indDeduzDeson`) e a lista de eventos canceláveis (seção 7).

# 4. O que fecha as linhas provisórias dos documentos 230 e 231

| Ponto | O que o texto oficial diz | Efeito |
|---|---|---|
| N12-70, exceção 7 (documento 230, seção 8) | NT 2023.003 v1.40: "A regra não se aplica, para o CST 51 (diferimento), nas operações com CFOP 5.123, 5.922, 6.123 e 6.922, **nem nas operações internas (idDest = 1) de retorno de mercadoria depositada em depósito fechado ou armazém geral (CFOP 5.906 ou 5.907)**" | A linha `NFE-CST-NAO-CONTRIBUINTE-EXC-CST51-CFOP` estava certa nos quatro CFOP; falta a segunda parte (Q232-1) |
| Quando o IBS, a CBS e o IS entram no total (Q231-1) (revista na seção 4.1) | NT 2025.002 v1.53, VB01-10 e VB01-20, exceção 1: "Em 2025 e 2026 não somar vIBS, vCBS, vIS, vTotIBSMonoItem e vTotCBSMonoItem" (implementação futura) | O texto do item (VB01) e do total (W60) existe e **não altera o `vNF`**: as duas linhas `NFE-VNF-FORMULA-IBSCBS` estavam erradas e saem (seção 4.1, Q232-10) |
| VC02-14 e a devolução (Q231-2 c) | NT 2025.002 v1.53 traz o texto: devolução exige a chave no cabeçalho (`refNFe`) ou no item (`DFeReferenciado`), nunca nos dois; a v1.53 limitou a uma ocorrência no cabeçalho; CFOP 5.921 e 6.921 ficam fora; produção em 03/11/2026 | O que a Systax dizia está confirmado; o desenho (Q231-2 c) pode partir deste texto |
| Q231-3 (enviar a NT mais recente e o Anexo I atual) | A NT 2025.002 v1.53 chegou; sobre o Anexo I, você disse que o MOC 7.0 é o que existe e foi reformado por NT | Q231-3 **encerrada**: o MOC 7.0 com as NT recebidas é a base (seção 4.1) |

## 4.1. O texto em vigor da W16-10, da GAP03a-3 e da I08-90 (revisão 2)

Base: Anexo I do MOC 7.0 (novembro de 2020), com as NT recebidas por cima. Onde duas NT mexem na mesma regra, vale a mais nova.

| Regra | Texto em vigor | Fontes | Efeito na carga |
|---|---|---|---|
| W16-10 (55 e 65, facultativa, rejeição 610) | `vNF` difere de: vProd − vDesc − vICMSDeson + vST + vFCPST + **vICMSMonoReten** + vFrete + vSeg + vOutro + vII + vIPI + vIPIDevol + vServ + vPIS do PIS-ST (se indSomaPISST = 1) + vCOFINS da COFINS-ST (se indSomaCOFINSST = 1). **Exceção 1** (tpOp = 2, faturamento direto de veículo novo): a mesma soma sem vST, vFCPST e vIPIDevol e **com** vICMSMonoReten. **Exceção 2:** importação (CFOP iniciado por 3). **Exceção 4:** não rejeita quando o vICMSDeson do item não foi subtraído do total e o item tem `indDeduzDeson` = 0 ou vazio | MOC 7.0 (14 componentes); NT 2020.005 v1.20 (PIS-ST e COFINS-ST); NT 2023.001 v1.60 (vICMSMonoReten; produção em 30/03/2023); NT 2023.004 v1.20 (exceção 3 trocada pela 4; correção das exceções 1 e 4 na v1.11; regra em produção em 01/07/2024) | As 3 linhas de fórmula do documento 230 ficam **encerradas em 29/03/2023** e entram 3 iguais, com o vICMSMonoReten, **desde 30/03/2023**. As 2 linhas `NFE-VNF-TOLERA-SEM-DESONERACAO` (exceção 3) ficam encerradas em 30/06/2024 e entram 2 linhas da exceção 4, desde 01/07/2024 (Q232-10) |
| VB01-05, VB01-10, VB01-20, W60-05 e W60-10 (NT 2025.002 v1.53; "implementação futura", sem data) | O `vNF` **não muda**: a W16-10 não aparece na v1.53. O IBS, a CBS e o IS entram em `vItem` (VB01-10, 55 e 65, rejeição 1105: a soma do item é vProd − vDesc − vICMSDeson se indDeduzDeson = 1 + vICMSST + vICMSMonoReten + vFCPST + vFrete + vSeg + vOutro + vII + vIPI + vIPIDevol + vServ + vPIS do PIS-ST + vCOFINS da COFINS-ST + vIBS + vCBS + vIS + vTotIBSMonoItem + vTotCBSMonoItem) e no campo novo `vNFTot` (W60-10, rejeição 1094: soma dos `vItem`). VB01-20 (só 55): a soma do item no faturamento direto de veículo, sem vICMSST, vICMSMonoReten, vFCPST e vIPIDevol e sem os dois totais monofásicos. VB01-05 (1137) e W60-05 (1004): `vItem` e `vNFTot` obrigatórios quando existe o grupo de IBS/CBS ou o de totais. **Exceção 1 do VB01-10 e do VB01-20:** em 2025 e 2026 não somar vIBS, vCBS, vIS, vTotIBSMonoItem e vTotCBSMonoItem | NT 2025.002 v1.53 (seção de regras, grupos VB e W) | Saem as 2 linhas `NFE-VNF-FORMULA-IBSCBS` (diziam "vNF = fórmula + vIBS + vCBS", leitura de resumos de terceiros) e entram **9 linhas**: `NFE-VITEM-OBRIGATORIO` (55, 65), `NFE-VITEM-FORMULA` (55, 65), `NFE-VITEM-FORMULA-FAT-DIRETO-VEICULO` (55), `NFE-VNFTOT-OBRIGATORIO` (55, 65) e `NFE-VNFTOT-FORMULA` (55, 65). Início **01/01/2027** (a NT só diz "implementação futura" e que 2025 e 2026 ficam de fora; a data é leitura minha, agora apoiada no texto) |
| GAP03a-3 (rejeição 452, obrigatória) | "Solicitação de resposta assíncrona (indSinc = 0) para lote com somente 1 (uma) NF-e", rejeição "Solicitada resposta assíncrona para Lote com somente 1 (uma) NF-e"; produção em 13/10/2025. A regra **não limita o modelo**: vale para a NF-e e para a NFC-e | NT 2025.001 v1.02 (adiou de 08/09 para 13/10/2025) e v1.03; a regra não está no MOC 7.0. O documento 230 a leu só como regra da NFC-e (NT 2020.005) | A linha do modelo 65 fica (até 04/04/2027, pelo fim da autorização assíncrona da NFC-e). Entra **1 linha do modelo 55 desde 13/10/2025**, sem data final, e o 452 passa a existir também para o 55 (Q232-11) |
| I08-90 (55, facultativa, rejeição 523) | CFOP de operação interestadual (iniciado por 2 ou 6) com a UF do emitente igual à do destinatário e CNPJ ou CPF do emitente diferente do destinatário. **Exceção:** se a UFCons (LA06) foi informada com UF diferente da do emitente, o CFOP iniciado por 2 ou 6 vale | MOC 7.0, item 4.1.3 (NT 2010/004 e NT 2010/010); nenhuma NT recebida a altera | Entram **2 linhas** (regra e exceção) e o código 523 para o 55. Início 01/11/2020, a data do MOC 7.0: a regra é anterior e não achei a data de produção (Q232-11) |
| N12-70, exceção 7 | O MOC 7.0 traz a frase quebrada ("(idDest=1).de retorno de Mercadoria depositada em depósito fechado ou armazém geral (CFOP 5.906 ou 5.907)"); a NT 2023.003 v1.40 a conserta | MOC 7.0 e NT 2023.003 v1.40 | Já tratada na Q232-1 |

**Duas observações.** A tabela da W16-10 na NT 2023.004 v1.20 ainda imprime o texto da exceção 3 ao lado da 4; a própria NT descreve a mudança como "substituir a Exceção 3 pela Exceção 4", e li assim (o PDF só traz texto, sem mostrar o que está riscado). E a NT 2020.005 v1.20, que o documento 230 leu, não está mais comigo nesta sessão: a conferência da GAP03a-3 de 2021 vem do documento 230.

# 5. Regras que não estão na carga

## 5.1. CFOP da NFC-e e da devolução (Q232-2)

A carga da revisão 48 tem as regras N12-70 e N12-80, mas não as de CFOP. Texto lido nas NT 2023.003 v1.40, 2024.001 v1.10 e 2026.009:

| Linha proposta (`Codigo_Regra`) | Modelo, UF | Valor | Rejeição | Fonte |
|---|---|---|---|---|
| `NFCE-CFOP-PERMITIDOS` | 65, nacional | 5101; 5102; 5103; 5104; 5115; 5405; 5656; 5667; 5910; 5933 | 725 | I08-150; o 5910 entrou na NT 2024.001 v1.10 |
| `NFCE-CFOP-CST-PERMITIDOS` | 65, nacional | 5101; 5102; 5103; 5104; 5115 (CST 00, 20, 40, 41 e 90) | 382 | N12-40 |
| `NFCE-CFOP-CSOSN-PERMITIDOS` | 65, nacional | 5101; 5102; 5103; 5104; 5115 (CSOSN 102, 103, 300, 400 e 900) | 386 | N12a-40 |
| `NFCE-CFOP-EXC-UF` (duas linhas por UF: CFOP e CST) | 65, RS e ES | CFOP 5949 com CST 90 ou CSOSN 900 (RS: integração de meios de pagamento; ES: gorjeta) | 725, 382, 386 | NT 2023.003; ES desde 03/08/2026 |
| idem | 65, SP e AM | CFOP 5949 com CST 40 ou CSOSN 900 (gorjeta); SP desde 21/10/2024, AM desde 05/10/2026 | 725, 382, 386 | NT 2023.003 v1.20 e v1.40 |
| idem | 65, CE | CFOP 5403 e 5405 com CST 90 (Recurso Extraordinário 574.706/PR do STF) | 382, 386 | NT 2023.003 |
| `NFE-CST-NAO-CONTRIBUINTE-EXC-CST90-CE` | 55, CE | CFOP 5403 e 5405 com CST 90 | 508 | N12-70, observação |
| `NFE-DEVOLUCAO-CFOP-EXC-949` | 55, nacional | 1949; 2949, em devolução de venda (finNFe 4) | 327 | I08-140, exceção 1; NT 2026.009, desde 17/09/2026 |
| `NFE-DEVOLUCAO-CFOP-EXC-GAS-NATURAL` | 55, nacional | 5949; 6949, devolução simbólica de gás natural (NCM 27112100, Ajuste SINIEF 22/21) | 327 | I08-140, exceção 2 |
| `NFE-CST-NAO-CONTRIBUINTE-EXC-CST51-INTERNA` | 55, nacional | 5906; 5907, só em operação interna (idDest 1) | 508 | N12-70, exceção 7 (Q232-1) |

**Conta:** 3 + 10 (cinco UF, duas linhas cada) + 1 + 2 + 1 = **17 linhas novas**, todas provisórias, com `Aplicacao` = facultativa_por_uf nas de UF. Quatro códigos novos em `Cad_Dfe_Codigo_Retorno` (725, 382, 386 e 327).

**Duas leituras minhas.** (a) A NT 2023.003 não diz em que versão RS e CE entraram (as versões 1.00 e 1.10 são de julho e setembro de 2023); usei 03/07/2023 para as duas. (b) O resumo da v1.20 dá a produção de SP em 07/10/2024 e o quadro de cronograma em 21/10/2024; usei a data do quadro.

## 5.2. Código de benefício fiscal por UF (Q232-3)

A NT 2019.001 v1.70 define as regras N12-85, N12-86, N12-90, N12-94, N12-97, N12-98, N14a-10, N14a-20 e I05h-10, **facultativas por UF**, e dá numa matriz as UF que as aplicam, as datas e as exceções. O dicionário tem o dado (`Cad_Beneficio_Fiscal_Icms` por UF, com os CST) mas nenhuma linha de regra. O que a matriz diz:

| UF | Regras aplicadas | Linhas (regra × modelo) | Datas (produção) |
|---|---|---|---|
| DF | N12-85, N12-86, N12-94 e N12-98 | 8 | 01/02/2021 (N12-98); as demais em 04/09/2023 (NF-e) e 02/09/2024 (NFC-e) |
| ES | nenhuma | 0 | a matriz diz "não será aplicada" |
| GO | N12-85, 86, 90, 94, 97 e 98 | 12 | 01/07/2023 |
| PR | N12-85, 86, 94, 97 e 98 | 10 | 02/09/2019 (85, 86 e 97), 01/10/2019 (94), 10/08/2020 (98) |
| RJ | N12-85, 86, 90, 94, 97 e 98 | 12 | 01/10/2019 (as cinco primeiras), 10/08/2020 (98) |
| RS | N12-85, 86 e 98 | 6 | 01/10/2019 (85 e 86), 10/08/2020 (98) |
| SC | N12-85, 86, 94, 98, N14a-10 e 20, I05h-10 | 12 | 01/09/2025 (85), 03/11/2025 (86, 94, 98 e I05h), 06/04/2026 (N14a) |
| SP | N12-85, 86, 94, 97 (só NF-e) e 98 | 9 | 06/04/2026 |
| Demais UF | nenhuma | 0 | |

**Total: 69 linhas**, com a rejeição de referência (928, 929, 930, 931, 934, 946, 664, 665 e 666: nove códigos novos) e as exceções facultativas (E2, E3 e E4: devolução, nota de ajuste e entrada) em `Valor_Texto`.

**Quatro limites.** (a) O PDF mostra datas riscadas e novas na mesma célula; usei a última de cada célula (leitura minha). (b) O alinhamento das exceções E2 a E4 às colunas é leitura minha, porque o texto da tabela quebra de linha. (c) O código 931 vale para duas regras com mensagens diferentes (N12-88 e N12-94); a identidade do código tem uma descrição só, e usei a da N12-94. (d) A literal "SEM CBENEF", que algumas UF exigem para CST sem benefício, depende da tabela de cada UF (os portais das Fazendas) e não entra.

## 5.3. Manifestação do destinatário (Q232-4)

NT 2020.001 v1.50 e v1.60 (Ajuste SINIEF 43/23 e 14/26):

- **Prazo de 90 dias** da autorização para a manifestação conclusiva (antes eram 180), produção em 01/06/2026; a ciência da emissão tem 10 dias. Hoje o dicionário não tem linha de prazo para o modelo 55 (`Cad_Dfe_Evento_Tipo.Aplica_Prazo_Municipal` só atende a NFS-e).
- **Até 2 ocorrências de cada evento conclusivo** (confirmação, desconhecimento e operação não realizada), vale a última (nSeqEvento de 1 a 2; rejeição 594). Os campos `Sequencia_Evento` e `Numero_Ocorrencia` de `Mov_Dfe_Evento` já aceitam, mas `Cad_Dfe_Evento_Tipo` só diz "evento único" (sim ou não) e o documento 34 descreve a manifestação como "uma por autor". **Falta o limite de ocorrências.**
- A ciência não cabe depois de uma manifestação conclusiva (655); ciência e desconhecimento não cabem em nota cancelada ou denegada (650 e 651); fora do prazo é a rejeição 596; justificativa é obrigatória na operação não realizada (595); a UF do destinatário tem de bater com a do serviço (658); o `tpEmis` da chave tem de ser válido (496).

**Proposta:** (1) **3 linhas de parâmetro** (modelo 55): `NFE-MANIFESTACAO-PRAZO-CONCLUSIVA` com 90 dias desde 01/06/2026, a mesma com 180 dias de 02/05/2022 a 31/05/2026 (data de início é leitura minha, a partir do cronograma da v1.10 e v1.20) e `NFE-MANIFESTACAO-PRAZO-CIENCIA` com 10 dias; (2) **1 campo** `Cad_Dfe_Evento_Tipo.Maximo_Ocorrencias` (número, opcional; vazio vale 1; 2 para 210200, 210220 e 210240); (3) **5 combinações** em `Cad_Dfe_Evento_Combinacao`: ciência (210210) rejeitada se já existe qualquer conclusiva (655), três linhas; ciência e desconhecimento rejeitados com o cancelamento 110111 existente (650 e 651); (4) **8 códigos de retorno** (594, 595, 596, 650, 651, 655, 658 e 496).

# 6. Campos que faltam

## 6.1. Grupo de pagamento da nota (Q232-5)

NT 2023.004 v1.20 (produção imediata): o grupo YA ganhou quatro campos. `Mov_Nota_Fiscal_Saida_Pagamento` tem a forma, o valor, a data, a credenciadora, a bandeira, a autorização e a transação do cartão, **mas não estes**:

| Campo da NT | Tag | Regra | Campo proposto (`Mov_Nota_Fiscal_Saida_Pagamento`) |
|---|---|---|---|
| CNPJ transacional do pagamento | YA03c (`CNPJPag`) | Estabelecimento onde o pagamento foi processado, quando a nota sai de estabelecimento distinto; rejeição 961 se zeros ou dígito inválido | `Cnpj_Transacional`, código (14), opcional |
| UF desse CNPJ | YA03d (`UFPag`) | Obrigatória com o CNPJ transacional | `ID_Estado_Transacional`, referência a `Cad_Estado`, opcional |
| CNPJ do beneficiário do pagamento | YA07a (`CNPJReceb`) | Estabelecimento beneficiário, dentro do grupo de cartões, PIX e boletos; rejeição 796 | `Cnpj_Recebedor`, código (14), opcional |
| Identificador do terminal | YA07b (`idTermPag`) | Terminal em que se fez o pagamento (até 40) | `Identificador_Terminal_Pagamento`, código (40), opcional |

Conferi `Mov_Transacao_Cartao` (documento 177): ela guarda a filial que vendeu, mas não o recebedor nem o terminal. A nota de entrada guarda só o que recebe, e não propus nada nela.

## 6.2. Detalhe de pagamento do evento ECONF (Q232-6)

O evento 110750 (NT 2024.002), enviado por quem recebe o dinheiro (adquirente, instituição de pagamento) e que o ERP só **recebe** (`Somente_Recepcao` = sim, D-N16), traz **de 1 a 100 grupos `detPag`**: indicador de prazo, meio de pagamento, descrição, valor, data, CNPJ e UF do pagamento, CNPJ da instituição, bandeira, autorização e CNPJ e UF do beneficiário. `Mov_Dfe_Evento_Item` e os 12 campos de `Mov_Dfe_Evento` não têm onde guardar isso, e é exatamente o dado que concilia o que o cliente pagou com a nota.

**Proposta:** entidade nova `Mov_Dfe_Evento_Pagamento` (módulo 01, sem vigência), 14 campos: `ID_Dfe_Evento_Pagamento`, `ID_Dfe_Evento` (FK), `Indicador_Prazo`, `ID_Forma_Pagamento` (domínio `forma_pagamento_dfe`, o mesmo da nota), `Descricao_Forma_Pagamento`, `Valor_Pagamento`, `Data_Pagamento`, `Cnpj_Transacional`, `ID_Estado_Transacional` (FK), `Cnpj_Instituicao`, `Bandeira`, `Numero_Autorizacao`, `Cnpj_Recebedor` e `ID_Estado_Recebedor` (FK). O cancelamento (110751) só referencia o protocolo do ECONF, e `ID_Evento_Referenciado` já cobre.

## 6.3. `indDeduzDeson` (Q232-7)

Nos grupos do ICMS com desoneração, o campo `indDeduzDeson` diz se o valor do ICMS desonerado (`vICMSDeson`) **deduz** do valor do item (`vProd`). A NT 2025.002 v1.53 usa o indicador na soma do `vItem` (VB01-10 e VB01-20: "(−) vICMSDeson, se indDeduzDeson = 1"). O dicionário tem `Valor_Desonerado` e o motivo, mas não o indicador; sem ele a fórmula do total do item não fecha.

**Proposta:** `Mov_Apuracao_Tributo_Item.Indicador_Deduz_Desoneracao` (booleano, opcional; só nas linhas de ICMS).

# 7. Catálogo de eventos da NF-e e da NFC-e (Q232-8)

`Cad_Dfe_Evento_Tipo` e o domínio `tipo_evento_dfe` foram desenhados no documento 34 (59 tipos), mas **a carga só tem 6 linhas do modelo 55** (as dos eventos financeiros e da averbação, documento 230). Faltam as linhas do catálogo, que a pré-validação do Motor usa (autor permitido, ambiente receptor, efeito, evento único). Com os esquemas e as NT recebidas consigo confirmar **43 códigos** além dos 6 já na carga (47 linhas, porque `Cad_Dfe_Evento_Tipo` tem uma linha por modelo):

| Grupo | Códigos | Modelos | Fonte |
|---|---|---|---|
| Cancelamento, correção e substituição | 110110 (carta de correção), 110111 (cancelamento), 110112 (cancelamento por substituição) | 55; 55 e 65; 65 | Esquemas Evento_CCe, Canc e CancSubst |
| Entrega | 110130, 110131 (comprovante e cancelamento), 110192, 110193 (insucesso e cancelamento) | 55 | NT 2023.005 e esquemas |
| Contingência | 110140 (EPEC) | 55 e 65 | NT 2014.001 v1.41 |
| Ator interessado | 110150 | 55 | NT 2020.007 v1.40 |
| Manifestação | 210200, 210210, 210220, 210240 | 55 | NT 2020.001 v1.60 |
| Prorrogação de ICMS (remessa para industrialização) | 111500 a 111503 (pedido e cancelamento, 1º e 2º prazo) | 55 | Esquema Prorrog_Indust |
| Resposta do Fisco à prorrogação | 411500 a 411503 | 55 | Esquema Prorrog_Indust |
| Suframa | 990900 (vistoria) e 990910 (internalização) | 55 | Esquemas Suframa |
| Conciliação financeira | 110750, 110751 | 55 e 65 | NT 2024.002 |
| Vinculação do pagamento | 110300 | 55 | NT 2026.006 |
| IBS e CBS (RTC) | 112110, 112120, 112130, 112140, 112150, 211110, 211124, 211128, 211130, 211140, 211150, 212110, 212120, 412120, 412130 e o cancelamento genérico 110001 | 55 | NT 2025.002 v1.53 (o 211120 foi eliminado) |
| Simples Nacional (Fisco) | 412140 | 55 | NT 2026.005 |

São 3 + 4 + 1 + 1 + 4 + 4 + 4 + 2 + 2 + 1 + 16 + 1 = **43 códigos** e **47 linhas** (110111, 110140, 110750 e 110751 valem para o 55 e o 65). Para cada uma proponho `Categoria`, `Autor_Permitido`, `Ambiente_Receptor` (SVRS para o ECONF e para os da RTC, que o texto da NT diz; ambiente nacional para a manifestação, que a H07 da NT 2020.001 indica; **o resto fica provisório em `sefaz_uf`, leitura minha**), `Exige_Assinatura` = sim e `Evento_Unico` conforme o texto. Os códigos 112110 e 420110 a 420170 **não aparecem em nenhum documento que tenho**; o domínio `tipo_evento_dfe` tem 81 códigos fora da lista visível e **não consegui conferir se eles estão lá** (incluir se faltarem).

**Achado:** o esquema do cancelamento de evento (`e110001`, PL_010g e PL_010h) aceita **sete códigos que nenhuma NT recebida define: 420110, 420120, 420130, 420140, 420150, 420160 e 420170**. O prefixo 42 é de eventos do Fisco ou de ambiente nacional no padrão da NT 2025.002 (como o 412140), mas isso é palpite; não há texto. Q232-9.

# 8. O que conferi e já está coberto

| Ponto | Onde está no dicionário |
|---|---|
| `tpRegimeIBSCBS` (C21a) e `cAtivSN` (I17d), NT 2026.005 | `Cad_Simples_Opcao.Situacao` (inclui `pendente` e `nao_optante_com_processo`) e `Cad_Participante_Regime_Ibs_Cbs`; derivado, sem campo (documento 163) |
| `ISUFEmit` (C22), NT 2025.002 v1.40 | `Cad_Participante_Inscricao` com `Tipo_Inscricao` = suframa, ligada a `Cad_Habilitacao_Suframa` |
| `refDFeAnt` (BB05) | `Mov_Nota_Fiscal_Saida_Referenciada` (os tipos 2 e 3 exigem a chave do documento anterior) |
| `cIndOp` (B25d), `cAtivSN`, `tpRBSN`, `vProdLiq`, `vICMSPrevisto`, `gPgtoVinc`, PAA, `procEmi` = 4, GTIN grupo V | Revisões 44 a 48 |
| `tpEmis` 9 e `tpImp` 6, autorização com alerta (NT 2026.002) | `Mov_Documento_Fiscal` e `Mov_Dfe_Transmissao_Documento` |
| EPEC v1.41 (NT 2014.001), NFF (NT 2021.002), DANFE simplificado Tipo 2, QR Code v3 (NT 2025.001) | `Mov_Dfe_Contingencia`, `Tipo_Emissao` 3, `Mov_Documento_Fiscal` e `Cad_Dfe_Leiaute` |
| NT 2026.010 (DANFE da reforma, 01/12/2026) | Só leiaute de impressão; os dados já existem |
| Guia de trânsito e receituário (NT 2024.003 v1.10, vários agrotóxicos) | `Mov_Nota_Fiscal_Saida_Agropecuario` |
| Crédito presumido do ICMS do produto (`cCredPresumido`) | `Mov_Apuracao_Tributo_Item_Complemento` |

# 9. Perguntas para você

| Id | Pergunta | Recomendação |
|---|---|---|
| Q232-1 | Acrescentar a linha `NFE-CST-NAO-CONTRIBUINTE-EXC-CST51-INTERNA` (CFOP 5.906 e 5.907, só em operação interna) e corrigir a descrição da linha existente, que passa a citar só os quatro CFOP? (A data do IBS e CBS no total saiu desta pergunta e foi para a Q232-10.) | **Sim.** Fecha a exceção 7 |
| Q232-2 | Carregar as **17 linhas** de CFOP da seção 5.1 (NFC-e, exceções por UF e devolução) em `Cad_Dfe_Parametro_Regra`, com os quatro códigos de retorno novos? | **Sim**, provisório. Sem elas o Motor rejeitaria uma NFC-e de gorjeta em SP, ES e AM ou a de meio de pagamento no RS |
| Q232-3 | Carregar as **69 linhas** do cBenef por UF da seção 5.2, com os nove códigos de retorno? | **Sim**, provisório. Sem elas o Motor deixa passar um cBenef que a SEFAZ rejeita |
| Q232-4 | Manifestação: 3 linhas de prazo, 1 campo `Cad_Dfe_Evento_Tipo.Maximo_Ocorrencias`, 5 combinações e 8 códigos de retorno (seção 5.3)? | **Sim.** É o prazo que vale desde 01/06/2026 e a segunda ocorrência |
| Q232-5 | Acrescentar os 4 campos do grupo de pagamento (seção 6.1) a `Mov_Nota_Fiscal_Saida_Pagamento`? | **Sim.** Produção imediata desde out/2024 |
| Q232-6 | Criar `Mov_Dfe_Evento_Pagamento` (14 campos) para o detalhe de pagamento do ECONF (seção 6.2)? | **Sim.** Sem ela o ERP descarta o dado da conciliação |
| Q232-7 | Acrescentar `Indicador_Deduz_Desoneracao` a `Mov_Apuracao_Tributo_Item` (seção 6.3)? | **Sim** |
| Q232-8 | Carregar as **47 linhas** (43 códigos) da seção 7 em `Cad_Dfe_Evento_Tipo`, com os códigos que faltarem em `tipo_evento_dfe`? | **Sim**, provisório; o que o texto não diz fica em `sefaz_uf` |
| Q232-9 | Enviar a NT (ou o esquema) que define os eventos **420110 a 420170**, o **Anexo I do MOC atual** (W16-10, GAP03a-3) e a **NT 2020.006** (regra I08-90)? | **Sim**, quando puder |

Para o contador **não entra pergunta nova**: nada nesta comparação depende de interpretação tributária.

# 10. Contagens e como será aplicado

**Contagens se tudo for aprovado** (somar ao que o D-N600 deixou previsto para a revisão 49: 1.241 entidades, 14.411 campos, 3.696 referências, 374 domínios e 1.507 tabelas): **1.242 entidades** (+1), **14.431 campos** (+20: 4 + 14 + 1 + 1), **3.701 referências** (+5: 1 da Q232-5 e 4 da Q232-6), **374 domínios** (sem mudança) e **1.508 tabelas no DDL** (+1). Carga (com a revisão 2): 1 + 17 + 69 + 3 + 14 + 3 = **107 linhas novas de regra** (Q232-1, 2, 3, 4, 10 e 11), 2 linhas que saem da carga 48, 6 linhas existentes ajustadas (5 encerradas por data na W16-10 e a descrição da exceção 7), 5 combinações, **31 linhas novas de código de retorno** (21 + 10: 1105, 1137, 1004 e 1094 em 55 e 65, mais 523 e 452 no 55) e 47 linhas de tipo de evento. A `Cad_Dfe_Parametro_Regra` da carga 49 teria 36 + 107 − 2 = **141 linhas**.

**Como aplicar.** Só depois do seu "consolidar": a revisão 49 aplica o documento 226 (D-N600), a Q229-1 e este documento. A carga 49 junta as linhas da carga 48 com as novas (CSV com a mesma convenção), e o DDL é testado de novo no PostgreSQL 16.

# 11. Limites

- **Leitura por amostragem em parte das NT:** 2014.002, 2015.001, 2016.003, 2018.005, 2020.004, 2020.007, 2021.002, 2021.003, 2022.002, 2022.005, 2023.001, 2023.002, 2023.005, 2024.001, 2025.001, 2026.001 a 2026.004 e 2026.007 a 2026.008 li pelo controle de versões, pelo resumo e por conferência de palavras-chave; **não é leitura regra por regra**. Se uma delas trouxer regra que o desenho não prevê, pode ter passado.
- **Não li as regras de devolução 3BA02 nem a NA01-20** da NT 2025.002 v1.53 (Q231-2 b) nem os manuais; os esquemas dos eventos eu comparei só nos códigos, não nos campos de cada evento.
- **O texto em vigor da W16-10, da GAP03a-3 e da I08-90 é uma reconstrução** (MOC 7.0 mais NT 2020.005, 2023.001, 2023.004, 2025.001 e 2025.002 v1.53). Se existir outra NT que mexa nelas e que você não enviou, não está aqui. A regra W16-10 vem em conjunto com a exceção 3, que li como substituída (seção 4.1).
- **As datas da matriz da NT 2019.001** vêm de um PDF com datas riscadas; usei a última de cada célula.
- **Nada validado por contador** e **nada carregado em banco**.
- O Project continua perto do limite de tamanho; a gravação dos documentos maiores pode ser recusada, e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
