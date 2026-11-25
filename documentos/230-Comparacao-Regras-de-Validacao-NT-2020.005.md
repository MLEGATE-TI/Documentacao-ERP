# Comparação das Regras de Validação da NT 2020.005 v1.20 com o Dicionário — Documento 230

*Você pediu "comparar as regras de validação da NT 2020.005" depois da revisão 47. Li as 16 regras do detalhamento (seção 4 da NT, versão 1.20, junho de 2021) e conferi cada uma contra o dicionário na revisão 47 (`Cad_Dfe_Parametro_Regra`, `Cad_Dfe_Codigo_Retorno`, `Cad_Dfe_Evento_Tipo`, `Cad_Dfe_Evento_Combinacao`, `Cad_CFOP`, `Cad_Cest` e as entidades da nota). **Situação em 16/11/2026: aplicado na revisão 48** (documento 231, D-N599), com as Q230-1 a Q230-5 lidas como Sim e os ajustes das normas novas. O texto abaixo é a proposta como foi escrita; a nota seguinte traz o que mudou na consolidação.*

Mlegate · Alberto Beyeler · Novembro de 2026

**Revisão 2 (16/11/2026): consolidação.** Ao aplicar o documento na revisão 48 conferi as normas novas que você enviou e quatro afirmações mudaram: (1) as **27 linhas viraram 36** (as 2 de São Paulo da 3B08-100 saíram, porque a NT 2023.002 v1.02 riscou a observação de São Paulo e desativou o serviço de inutilização em AC, BA e SP desde 11/11/2026; entraram 6 linhas de serviço ativo, 2 de autorização assíncrona proibida desde 05/04/2027, 1 de lote de NFC-e com 1 nota e 2 do IBS e CBS no total); (2) os **23 códigos viraram 28** (19 distintos: entram o 126, o 129 e o 998); (3) a linha da **GAP03a-3** (rejeição 452) vale só até 04/04/2027, e a NT 2023.002 não cita a regra; (4) o **W16-10** convive com o IBS e CBS no total (fonte de terceiros). Não mudaram a NA15-10, a NA17-10, a 1C17-50, a 5E17-10, a N12-70 e a N12-80. As Q230-1 a Q230-5 saem do documento 38; ficam a Q231-1 a Q231-3. Detalhe no documento 231.*

# 1. Resumo

A NT 2020.005 v1.20 traz **16 regras de validação** (mais a regra I08-90, que saiu desta versão e está na NT 2020.006, que não comparei). O resultado da comparação:

| Destino | Regras | O que faz |
|---|---|---|
| Linhas de `Cad_Dfe_Parametro_Regra` | 8 regras (NA15-10, NA17-10, W16-10, N12-70, N12-80, 3B08-100, I05c-10 e GAP03a-3) | **27 linhas** com fórmula, lista, tolerância ou limite, todas com início em 04/10/2021 (produção da NT) e a rejeição de referência |
| Carga de `Cad_Dfe_Codigo_Retorno` | as 16 regras | **23 linhas** (16 códigos) dos modelos 55 e 65, com o texto oficial da própria NT |
| Eventos que impedem o cancelamento | 4P15-30 e 4P15-34 | 6 tipos de evento, 6 combinações e **1 valor novo** em `Cad_Dfe_Evento_Combinacao.Resultado` |
| Já coberto, sem dado novo | ZD01-10, ZD02-10, ZD07-10, 1C17-50, 5E17-10 e B00 | A estrutura atual atende; a regra é de código (validar o CNPJ, exigir o responsável técnico) ou é da SEFAZ (cadastro centralizado, mensagem SOAP) e o ERP só trata o retorno |

**Dois achados que não são regra:** (1) a **identidade de `Cad_Dfe_Parametro_Regra` é só (`Codigo_Regra`, `Ambiente`)**; o modelo e a UF ficam na versão. Isso não deixa a mesma regra valer para o modelo 55 e para o 65, nem ter uma linha nacional e outra de São Paulo, e só comporta o que o documento 40 pediu (G56, G110, G138 e as 11 regras facultativas da NFCom, por UF) com um código diferente para cada UF. A Q230-2 propõe corrigir; (2) na importação, `Mov_Nota_Fiscal_Saida_Item_Importacao_Adicao.Numero_Adicao` é obrigatório, mas a NT diz que **não se informa na DUImp**, e `Tipo_Declaracao` não tem a **DIRE** que o campo `nDI` lista (Q230-5).

A mudança estrutural total é pequena: **1 valor de enumeração** (Q230-3), **1 campo que passa a opcional** e **1 valor de enumeração** (Q230-5) e, se você aprovar a Q230-2, **2 campos que passam a fazer parte da identidade** de `Cad_Dfe_Parametro_Regra`. O número de entidades (1.240) e de campos (14.398) não muda; o resto é carga.

# 2. Como o dicionário trata uma regra de validação

Três lugares, cada um para um tipo de regra, e foi assim que classifiquei:

| Tipo de regra | Onde mora | Exemplo |
|---|---|---|
| Depende de prazo, limite, tolerância, lista ou fórmula, e muda sem mudar o leiaute | `Cad_Dfe_Parametro_Regra`, com vigência e a rejeição de referência | CT-e: `CTE-CANCELAMENTO-PRAZO`; MDF-e: `MDFE-NAO-ENCERRADO-EMITENTE`; BP-e: `BPE-VTOTDFE-FORMULA` |
| É o código de retorno que a autoridade devolve | `Cad_Dfe_Codigo_Retorno`, com a ação padrão | E2243 do ADN (carga 47) |
| Depende do que já aconteceu com o documento (um evento anterior) | `Cad_Dfe_Evento_Tipo` e `Cad_Dfe_Evento_Combinacao` | cancelamento depois de manifestação, na NFS-e |
| É conferência de formato ou de dígito, ou consulta que só a autoridade faz | Código do ERP e do Motor de Regras, sem tabela | dígito verificador do CNPJ, assinatura, consulta ao cadastro centralizado |

A NF-e (modelos 55 e 65) **ainda não tem nenhuma linha** em `Cad_Dfe_Parametro_Regra` nem em `Cad_Dfe_Codigo_Retorno`: as cargas até a 47 trouxeram CFOP, CST, NCM, ANP, GTIN, mistura de combustíveis, os códigos da NFS-e Via e os do ADN, mas **não a tabela de rejeições da NF-e**. Os 23 códigos desta NT são só os que ela cita; a tabela completa do Anexo I do MOC não está no meu ambiente (seção 8).

# 3. As 16 regras, uma a uma

Legenda: **Obrig.** = a UF tem de aplicar; **Facult.** = a UF decide. O modelo é o da NT (55 = NF-e, 65 = NFC-e). "Msg" é o código da rejeição.

| Regra | Msg | Modelo | O que a NT diz | O que o dicionário já tem | Proposta |
|---|---|---|---|---|---|
| I05c-10 | 446 | 55/65 Obrig. | Se o CEST foi informado, rejeitar CEST inexistente na tabela de apoio. **A NT diz que a regra está desabilitada**, à espera da tabela de CEST válidos. | `Cad_Cest` (código de 7 posições, com vigência) e `ID_Cest` no item da nota. | Duas linhas `NFE-CEST-INEXISTENTE-ATIVA` (55 e 65) com valor 0; o ERP confere o item contra `Cad_Cest` e só bloqueia quando o valor passar a 1. Código 446 na carga. |
| N12-70 | 508 | 55 Obrig. | Destinatário não contribuinte (indIEDest = 9): CST só 00, 20, 40, 41 ou 60. Nove exceções (entrada, CST 50 com CFOP de retorno ou remessa, veículo novo, antes de 01/07/2016, CST 30 interestadual com combustível derivado de petróleo, devolução, CST 51 com 4 CFOP, CST 10 interno a critério da UF, CST 30 em energia no ACL). | `Indicador_IE` em `Cad_Participante_Inscricao` (contribuinte, isento, não contribuinte = 1, 2 e 9); `Tipo_Operacao` (tpNF); `Finalidade` = devolução (finNFe 4); `Veiculo_Tipo_Operacao` no item (veicProd); `Cad_CFOP.Indicador_Retorno` e `Indicador_Remessa`; `Cad_Produto_Anp`. idDest é derivado das UF. | 7 linhas de parâmetro (lista de CST permitidos e as exceções que têm valor). As exceções 1 e 3 (entrada, veículo novo) saem dos campos acima, sem valor. **A exceção 4 (antes de 01/07/2016) não entra**: o ERP não emite nota de 2016. O Motor de Regras passa a só sugerir, para destinatário não contribuinte, CST da lista. |
| N12-80 | 529 | 55 Obrig. | Destinatário contribuinte isento de IE (indIEDest = 2): CST 50 e 51 rejeitados. Exceções: CST 50 com CFOP de conserto, de demonstração ou de industrialização por encomenda (esta é a inclusão da NT, item 2.2.4); data anterior a 01/07/2016; CST 51 interno com destinatário CNPJ, a critério da UF; NFA-e. | Os mesmos campos da N12-70. | 5 linhas (vedados, três listas de CFOP e CST 51 interno). A exceção da data e a da NFA-e (nota avulsa emitida no site da SEFAZ) não entram: o ERP não emite nem uma nem outra. |
| NA15-10 | 815 | 55 Obrig. | Com CST 00 e grupo ICMSUFDest, o vICMSUFDest tem de ser ((vBCUFDest × pICMSUFDest) − (vBC × pICMSInter)) × pICMSInterPart, nunca menor que zero, tolerância de R$ 0,01. **Reativação da regra** (item 2.2.5). | O DIFAL está coberto por campos existentes (documento 34: 84 de 85 campos de IPI, II, PIS, COFINS, ISSQN e DIFAL). | 1 linha com a fórmula e a tolerância de R$ 0,01. |
| NA17-10 | 816 | 55 Obrig. | Idem para vICMSUFRemet: ((vBCUFDest × pICMSUFDest) − (vBC × pICMSInter)) − vICMSUFDest, nunca menor que zero, tolerância de R$ 0,01. | Idem. | 1 linha, igual à anterior. |
| W16-10 | 610 | 55/65 Facult. | O total vNF tem de ser o somatório de 14 componentes; os indicadores `indSomaPISST` e `indSomaCOFINSST` decidem se o PIS-ST e a COFINS-ST entram. Exceções: faturamento direto de veículo novo (fórmula sem vST, vFCPST e vIPIDevol), importação (CFOP 3) e nota em que o vICMSDeson não foi subtraído. | `Mov_Apuracao_Tributo_Item.Compoe_Total_Documento` (os dois indicadores, **entrou na revisão 47**); o total é derivado: o ERP calcula e não grava de novo; `Veiculo_Tipo_Operacao` = faturamento_direto. | 6 linhas: a fórmula (55 e 65), a variante do faturamento direto, a exceção da importação e a da desoneração (55 e 65). **A NT não dá tolerância para o W16**; não inventei uma. |
| ZD01-10 | 972 | 55/65 Facult. | Rejeitar nota sem o grupo do responsável técnico; a UF decide; não vale para a NFA-e. | `Cad_Dfe_Emitente_Configuracao.ID_Participante_Responsavel_Tecnico` e `Identificador_Csrt`. | **Sem linha.** O ERP sempre informa o grupo nos modelos 55 e 65, sem perguntar a UF; a pré-validação barra a emissão se a configuração não tiver o responsável técnico. Só o código 972 na carga. |
| ZD02-10 | 973 | 55/65 Facult. | Se o CNPJ do responsável técnico foi informado, rejeitar zeros, nulo ou dígito inválido. | O tipo de CNPJ (inclusive o alfanumérico) e a validação já estão no framework. | **Sem linha.** Validação do dígito é código. Só o código 973 na carga. |
| ZD07-10 | 975 | 55/65 Facult. | Se o grupo do responsável técnico foi informado, exigir `idCSRT` e `hashCSRT`. | `Identificador_Csrt` e `Referencia_Cofre_Csrt` (o segredo fica no cofre; o hash é calculado com o CSRT e a chave da nota). | **Sem linha.** A pré-validação exige o identificador e a referência do cofre. Só o código 975 na carga. |
| 1C17-50 | 307 | 55 Facult. | Em saída interestadual a consumidor final não contribuinte (indFinal = 1 e indIEDest = 9), a SEFAZ consulta o Cadastro Centralizado de Contribuintes do destino e **denega** a nota se o emitente estiver bloqueado (cSitCNPJ = 10). Opcional por UF (Ajuste SINIEF 33/19); não vale para UF não signatária; a v1.20 incluiu indIEDest = 9. | `Mov_Documento_Fiscal.Status` tem `denegado`; `Cad_Dfe_Codigo_Retorno.Natureza` tem `denegado`. **Não há consulta de cadastro** em `Mov_Dfe_Transmissao.Tipo_Servico`. | **Sem linha.** Só o código 307 (natureza denegado, ação nenhuma) e um aviso do Motor ao fiscal. Não desenhei a consulta de cadastro antes da emissão: é da SEFAZ, e o ERP só trata o retorno. Pergunta ao contador: C363. |
| 3B08-100 | 206 | 55/65 Obrig. | Rejeitar número já inutilizado, nos tipos de emissão 1, 6 e 7; em São Paulo (cUF = 35) também nos tipos 2, 4 e 5. A v1.10 tirou o 2, o 4 e o 5 da regra nacional (item 2.2.10), e a v1.20 devolveu a São Paulo. | `Mov_Dfe_Inutilizacao` (série, faixa e status `registrado`); `Cad_Serie_Documento_Fiscal` dá a numeração sequencial do ERP; `Cad_Estado` para a linha de São Paulo. | 4 linhas: a lista nacional e a de São Paulo, para o modelo 55 e para o 65. A numeração é do ERP e só avança, então a conferência é trivial; o valor da lista serve ao Motor de contingência. |
| 5E17-10 | 233 | 55 Obrig. | Se a IE do destinatário foi informada, ela tem de existir no cadastro da UF; para destinatário identificado por CPF (produtor rural), vale o par CPF e IE no Cadastro Centralizado. **Ativação da regra** (item 2.2.11). A NT avisa que algumas UF ainda não cadastraram o CPF. | `Cad_Participante_Inscricao` (IE, UF e `Indicador_IE`) e o CPF do participante já cobrem o par. | **Sem linha.** Só o código 233 (ação corrigir) e um aviso do Motor quando o destinatário tiver CPF e IE. A consulta de cadastro não foi desenhada (ver 1C17-50). |
| 4P15-30 | 939 | 55 Obrig. | Rejeitar o pedido de cancelamento de NF-e com evento de averbação para exportação (790700). | `Cad_Dfe_Evento_Combinacao` (tipo existente × tipo pedido, resultado e código de retorno). | 1 combinação (790700 → 110111) e o tipo 790700 em `Cad_Dfe_Evento_Tipo`, se ainda não existir (seção 6). |
| 4P15-34 | 940 | 55 Obrig. | Rejeitar o cancelamento de NF-e com evento financeiro (990100, 900120, 900140, 900138 ou 900110). Uma nota pode ter vários desses eventos; **permite cancelar se todos tiverem o seu próprio cancelamento**. | Idem. Só que `Resultado` não tem o caso "rejeitado enquanto houver evento sem cancelamento do próprio evento". | 5 combinações e 5 tipos, com **1 valor novo** em `Resultado`: `rejeitado_se_nao_cancelado` (seção 6). |
| B00 | 242 | 55/65 Obrig. | Mensagem SOAP sem o parâmetro `nfeDadosMsg` ou com o namespace errado: rejeição 242, em vez do 999. O mesmo para os demais serviços. | O ERP monta a mensagem; o erro é de implementação. | **Sem linha.** Só o código 242 (ação corrigir): se aparecer, é defeito do driver, não do usuário. |
| GAP03a-3 | 452 | 65 Obrig. | Pedido de resposta assíncrona (indSinc = 0) para lote com uma só NFC-e é rejeitado; o assíncrono só vale com mais de uma nota. | `Cad_Dfe_Emitente_Configuracao.Envio_Sincrono` (por filial, modelo e ambiente) e `Mov_Dfe_Transmissao.Modo`. | 1 linha `NFCE-LOTE-ASSINCRONO-MINIMO-NOTAS` = 2 notas por lote. Com uma nota só, o ERP envia em modo síncrono, mesmo com `Envio_Sincrono` = não. Código 452 na carga (ação reenviar). |

A regra **I08-90** (CFOP de operação interestadual na anulação de serviço de transporte com tomador e prestador na mesma UF) saiu desta versão: a NT diz que está na NT 2020.006. Não a comparei.

# 4. As 27 linhas propostas de `Cad_Dfe_Parametro_Regra`

Todas com `Ambiente` = ambos, `Vigencia_Inicio` = 04/10/2021 (produção da NT v1.20), `Vigencia_Fim` = 31/12/9999 e `Fonte` = "NT 2020.005 v1.20, regra X". `Aplicacao` e a rejeição de referência estão na tabela. **Provisório:** as NT posteriores a 2021 podem ter alterado estas regras (a do W16, por exemplo, mudou com o IBS/CBS); ver a seção 8.

| # | Codigo_Regra | Modelo | Aplicação | Valor numérico | Valor texto | Unidade | Rejeição | Regra da NT |
|---|---|---|---|---|---|---|---|---|
| 1 | `NFE-VICMSUFDEST-FORMULA` | 55 | obrigatoria | 0,01 | ((vBCUFDest × pICMSUFDest) - (vBC × pICMSInter)) × pICMSInterPart; resultado menor que zero vale 0,00; arredondar a 2 casas | R$ (tolerância, para mais e para menos) | 815 | NA15-10 |
| 2 | `NFE-VICMSUFREMET-FORMULA` | 55 | obrigatoria | 0,01 | ((vBCUFDest × pICMSUFDest) - (vBC × pICMSInter)) - vICMSUFDest; resultado menor que zero vale 0,00; arredondar a 2 casas | R$ (tolerância, para mais e para menos) | 816 | NA17-10 |
| 3 | `NFE-VNF-FORMULA` | 55 | facultativa_por_uf |  | vNF = vProd - vDesc - vICMSDeson + vST + vFCPST + vFrete + vSeg + vOutro + vII + vIPI + vIPIDevol + vServ + vPIS do PIS-ST (se indSomaPISST = 1) + vCOFINS da COFINS-ST (se indSomaCOFINSST = 1) | fórmula | 610 | W16-10 |
| 4 | `NFE-VNF-FORMULA` | 65 | facultativa_por_uf |  | vNF = vProd - vDesc - vICMSDeson + vST + vFCPST + vFrete + vSeg + vOutro + vII + vIPI + vIPIDevol + vServ + vPIS do PIS-ST (se indSomaPISST = 1) + vCOFINS da COFINS-ST (se indSomaCOFINSST = 1) | fórmula | 610 | W16-10 |
| 5 | `NFE-VNF-FORMULA-FAT-DIRETO-VEICULO` | 55 | facultativa_por_uf |  | vNF = vProd - vDesc - vICMSDeson + vFrete + vSeg + vOutro + vII + vIPI + vServ + vPIS do PIS-ST (se indSomaPISST = 1) + vCOFINS da COFINS-ST (se indSomaCOFINSST = 1); sem vST, vFCPST e vIPIDevol; só com tpOp = 2 (faturamento direto de veículo novo) | fórmula | 610 | W16-10, exceção 1 |
| 6 | `NFE-VNF-EXC-IMPORTACAO-CFOP` | 55 | facultativa_por_uf |  | 3 | prefixo do CFOP | 610 | W16-10, exceção 2 |
| 7 | `NFE-VNF-TOLERA-SEM-DESONERACAO` | 55 | facultativa_por_uf | 1 |  | indicador (1 = não rejeita) | 610 | W16-10, exceção 3 |
| 8 | `NFE-VNF-TOLERA-SEM-DESONERACAO` | 65 | facultativa_por_uf | 1 |  | indicador (1 = não rejeita) | 610 | W16-10, exceção 3 |
| 9 | `NFE-CST-NAO-CONTRIBUINTE-PERMITIDOS` | 55 | obrigatoria |  | 00;20;40;41;60 | lista de CST do ICMS | 508 | N12-70 |
| 10 | `NFE-CST-NAO-CONTRIBUINTE-EXC-CST50-CFOP` | 55 | obrigatoria |  | 5949;6949 | lista de CFOP | 508 | N12-70, exceção 2 |
| 11 | `NFE-CST-NAO-CONTRIBUINTE-EXC-DEVOLUCAO` | 55 | obrigatoria |  | 50;51 | lista de CST do ICMS | 508 | N12-70, exceção 6 |
| 12 | `NFE-CST-NAO-CONTRIBUINTE-EXC-CST51-CFOP` | 55 | obrigatoria |  | 5123;5922;6123;6922 | lista de CFOP | 508 | N12-70, exceção 7 |
| 13 | `NFE-CST-NAO-CONTRIBUINTE-EXC-CST10-INTERNA` | 55 | facultativa_por_uf |  | 10 | CST do ICMS | 508 | N12-70, exceção 8 |
| 14 | `NFE-CST-NAO-CONTRIBUINTE-EXC-ENERGIA-ACL` | 55 | obrigatoria |  | 27160000 | NCM | 508 | N12-70, exceção 9 |
| 15 | `NFE-ANP-NAO-DERIVADO-PETROLEO` | 55 | obrigatoria |  | 820101001;820101010;810102001;810102004;810102002;810102003;810101002;810101001;810101003;220101003;220101004;220101002;220101001;220101005;220101006;560101001 | lista de códigos ANP | 508 | N12-70, exceção 5 |
| 16 | `NFE-CST-IE-ISENTA-VEDADOS` | 55 | obrigatoria |  | 50;51 | lista de CST do ICMS | 529 | N12-80 |
| 17 | `NFE-CST-IE-ISENTA-EXC-CST50-CONSERTO` | 55 | obrigatoria |  | 1915;1916;2915;2916;5915;5916;6915;6916 | lista de CFOP | 529 | N12-80, exceção 1 |
| 18 | `NFE-CST-IE-ISENTA-EXC-CST50-DEMONSTRACAO` | 55 | obrigatoria |  | 1912;1913;5912;5913 | lista de CFOP | 529 | N12-80, exceção 1 |
| 19 | `NFE-CST-IE-ISENTA-EXC-CST50-INDUSTRIALIZACAO` | 55 | obrigatoria |  | 1901;2901;5901;6901 | lista de CFOP | 529 | N12-80, exceção 1 (inclusão da NT 2020.005, item 2.2.4) |
| 20 | `NFE-CST-IE-ISENTA-EXC-CST51-INTERNA-PJ` | 55 | facultativa_por_uf |  | 51 | CST do ICMS | 529 | N12-80, exceção 3 |
| 21 | `NFE-INUTILIZACAO-TIPOS-EMISSAO` | 55 | obrigatoria |  | 1;6;7 | lista de tpEmis | 206 | 3B08-100 |
| 22 | `NFE-INUTILIZACAO-TIPOS-EMISSAO` | 65 | obrigatoria |  | 1;6;7 | lista de tpEmis | 206 | 3B08-100 |
| 23 | `NFE-INUTILIZACAO-TIPOS-EMISSAO-SP` | 55 | obrigatoria |  | 1;2;4;5;6;7 | lista de tpEmis | 206 | 3B08-100, observação |
| 24 | `NFE-INUTILIZACAO-TIPOS-EMISSAO-SP` | 65 | obrigatoria |  | 1;2;4;5;6;7 | lista de tpEmis | 206 | 3B08-100, observação |
| 25 | `NFE-CEST-INEXISTENTE-ATIVA` | 55 | obrigatoria | 0 |  | indicador (1 = ativa, 0 = desabilitada) | 446 | I05c-10 |
| 26 | `NFE-CEST-INEXISTENTE-ATIVA` | 65 | obrigatoria | 0 |  | indicador (1 = ativa, 0 = desabilitada) | 446 | I05c-10 |
| 27 | `NFCE-LOTE-ASSINCRONO-MINIMO-NOTAS` | 65 | obrigatoria | 2 |  | notas por lote | 452 | GAP03a-3 |

Descrições (campo `Descricao`) e `Motivo_Vigencia` seguem o texto de cada linha da NT; a carga as traz.

**Duas leituras minhas:** (a) o valor 0 ou 1 de `NFE-CEST-INEXISTENTE-ATIVA` e de `NFE-VNF-TOLERA-SEM-DESONERACAO` usa `Valor_Numerico` como indicador, o que o campo não proíbe, mas não é o uso de limite ou prazo que os documentos 40 e 42 descrevem; (b) o `Valor_Texto` com várias listas separadas por ponto e vírgula segue o que o campo já diz ("lista de CFOP aceitos").

# 5. Carga dos códigos de retorno (NF-e e NFC-e)

**23 linhas** em `Cad_Dfe_Codigo_Retorno`, com a autoridade `AN_NFE` (os códigos são comuns às SEFAZ; leitura minha, porque a identidade do código inclui a autoridade), `Vigencia_Inicio` = 04/10/2021 e o texto da coluna "Descrição Erro" ou da seção 7 da NT. `Natureza` e `Acao_Padrao` são leitura minha.

| Modelo | Código | Descrição oficial | Natureza | Ação padrão |
|---|---|---|---|---|
| 55 | 446 | Rejeição: Informado CEST inexistente [nItem:999] | rejeitado | corrigir |
| 65 | 446 | Rejeição: Informado CEST inexistente [nItem:999] | rejeitado | corrigir |
| 55 | 508 | Rejeição: CST incompatível na operação com Não Contribuinte [nItem: 999] | rejeitado | corrigir |
| 55 | 529 | Rejeição: CST incompatível na operação com Contribuinte Isento de Inscrição Estadual [nItem: 999] | rejeitado | corrigir |
| 55 | 815 | Rejeição: Valor do ICMS Interestadual para UF de Destino difere do calculado [nItem: 999] (Valor Informado: XXX, Valor Calculado:XXX) | rejeitado | corrigir |
| 55 | 816 | Rejeição: Valor do ICMS Interestadual para UF do Remetente difere do calculado [nItem: 999] (Valor Informado: XXX, Valor Calculado:XXX) | rejeitado | corrigir |
| 55 | 610 | Rejeição: Total da NF difere do somatório dos Valores compõe o valor Total da NF. | rejeitado | corrigir |
| 65 | 610 | Rejeição: Total da NF difere do somatório dos Valores compõe o valor Total da NF. | rejeitado | corrigir |
| 55 | 972 | Rejeição: Obrigatória as informações do responsável técnico | rejeitado | corrigir |
| 65 | 972 | Rejeição: Obrigatória as informações do responsável técnico | rejeitado | corrigir |
| 55 | 973 | Rejeição: CNPJ do responsável técnico inválido | rejeitado | corrigir |
| 65 | 973 | Rejeição: CNPJ do responsável técnico inválido | rejeitado | corrigir |
| 55 | 975 | Rejeição: Obrigatória a informação do identificador do CSRT e do Hash do CSRT | rejeitado | corrigir |
| 65 | 975 | Rejeição: Obrigatória a informação do identificador do CSRT e do Hash do CSRT | rejeitado | corrigir |
| 55 | 307 | Denegação: Emitente bloqueado pela UF de destino, em operação com consumidor final | denegado | nenhuma |
| 55 | 206 | Rejeição: Numeração da NF-e já está inutilizada na Base de Dados da SEFAZ | rejeitado | corrigir |
| 65 | 206 | Rejeição: Numeração da NF-e já está inutilizada na Base de Dados da SEFAZ | rejeitado | corrigir |
| 55 | 233 | Rejeição: IE do destinatário não cadastrada | rejeitado | corrigir |
| 55 | 939 | Rejeição: Pedido de Cancelamento para NF-e com evento de Averbação para Exportação | rejeitado | corrigir |
| 55 | 940 | Rejeição: Pedido de Cancelamento para NF-e com evento Financeiro | rejeitado | corrigir |
| 55 | 242 | Rejeição: Mensagem SOAP inválida | rejeitado | corrigir |
| 65 | 242 | Rejeição: Mensagem SOAP inválida | rejeitado | corrigir |
| 65 | 452 | Rejeição: Solicitada resposta assíncrona para Lote com somente 1 (uma) NFC-e | rejeitado | reenviar |

Seis destes (242, 446, 452, 939, 940 e 307) são os que a seção 7 da NT chama de "novos códigos de rejeição"; os outros dez já existiam e a NT só os cita nas regras. Não sei quais já estão na carga das SEFAZ, porque **nenhuma carga anterior trouxe a tabela de rejeições da NF-e**; se algum já existir, a carga o ignora.

# 6. Eventos que impedem o cancelamento (4P15-30 e 4P15-34)

A estrutura existe: `Cad_Dfe_Evento_Combinacao` guarda "tipo já registrado" × "tipo que se quer registrar", o resultado e o código de retorno. O que falta é o caso da exceção da 4P15-34: o cancelamento é permitido quando **cada** evento financeiro tem o seu evento de cancelamento. Hoje `Resultado` tem {permitido, rejeitado, rejeitado_se_mesmo_autor}. Proponho o valor **`rejeitado_se_nao_cancelado`**: rejeita enquanto existir ao menos um evento do tipo existente sem o evento de cancelamento dele (a ligação já existe em `Mov_Dfe_Evento.ID_Evento_Referenciado`; "evento cancelado" é estado derivado, não se grava).

| Tipo existente (nota 55) | Descrição oficial (NT) | Pedido | Resultado | Rejeição |
|---|---|---|---|---|
| 790700 | Registro de Averbação para Exportação | 110111 (cancelamento) | rejeitado | 939 |
| 990100 | Registro de Cessão de Parcela de Fat-e por IMF | 110111 (cancelamento) | rejeitado_se_nao_cancelado | 940 |
| 900120 | Transferência de Parcela de Fat-e por IMF | 110111 (cancelamento) | rejeitado_se_nao_cancelado | 940 |
| 900140 | Ativação de monitoramento de parcela de Fat-e informada por ESF | 110111 (cancelamento) | rejeitado_se_nao_cancelado | 940 |
| 900138 | Envio de Parcela de Fat-e para Cobrança Judicial | 110111 (cancelamento) | rejeitado_se_nao_cancelado | 940 |
| 900110 | Recebível em Avaliação | 110111 (cancelamento) | rejeitado_se_nao_cancelado | 940 |

Os seis tipos entram em `Cad_Dfe_Evento_Tipo` (modelo 55) **se ainda não existirem**: o 790700 já aparece no dicionário (`Mov_Dfe_Evento_Item.Numero_Due`), mas não consegui conferir na carga se o domínio `tipo_evento_dfe` tem os cinco códigos de Fat-e. Proposta provisória para os cinco: `Categoria` = outro, `Somente_Recepcao` = sim (chegam pela distribuição; o ERP não os emite), `Autor_Permitido` = terceiro, `Ambiente_Receptor` = ambiente_nacional, sem assinatura. O texto da NT não diz o autor nem o ambiente; é leitura minha. A NT fala só em "cancelamento": **não sei se vale para o 110112** (cancelamento por substituição da NFC-e), então não propus combinação para ele.

# 7. O que a seção 3 da NT (campos) mostrou

A seção 3 lista os campos novos ou alterados. Os do documento 227 (Q227-4) já entraram na revisão 47; conferi o resto:

| Campo da NT | Situação no dicionário |
|---|---|
| `cBarra` e `cBarraTrib` (I03a, I12a) | Entraram na revisão 47 na nota de saída; a nota de entrada e o cadastro do produto esperam a Q229-1 |
| `vICMSSTDeson`, `motDesICMSST`, `pFCPDif`, `vFCPDif`, `vFCPEfet`, `indSomaPISST`, `indSomaCOFINSST` | Entraram na revisão 47 |
| `tpViaTransp` com os valores 8 a 13 | Coberto: `Via_Transporte` tem os 13 valores |
| `nDraw` alfanumérico, de 1 a 20 | Coberto: `Numero_Drawback` é código de até 20 (no item de exportação e na adição) |
| `cAgreg` alfanumérico | Coberto (documento 227: `Codigo_Agregacao` é código) |
| UF da placa opcional (X20 e X24) | Coberto (`ID_Estado_Placa` é opcional) |
| `modBCST` com o valor 6 (valor da operação) nos grupos 70 e 90 | O domínio `modalidade_base_icms_st` é carga e **não pude conferir se o valor 6 está**; entra na carga se faltar |
| `nAdicao` (I26): ocorrência 0-1, "no caso de DUImp esse campo não deverá ser preenchido" | **Lacuna:** `Numero_Adicao` é obrigatório. Passa a opcional (Q230-5) |
| `nDI` (I19): "DI, DSI, DIRE, DUImp" | **Lacuna:** `Tipo_Declaracao` tem {di, duimp, dsi}. Acrescentar `dire` (Q230-5). A sigla DIRE leio como declaração de importação de remessa expressa; pode ser o mesmo que o **DIR** da Q221-5 (IT 2025.002), mas só o IT define, então **não confirma** |
| `adi` com até 999 ocorrências | Sem limite no dicionário; conferência de tamanho é do XML |

# 8. Limites

- **A NT é de junho de 2021.** As regras abaixo podem ter sido alteradas por NT posteriores (a W16-10, por exemplo, convive hoje com o IBS/CBS e o valor líquido do item; o documento 34 lista 20 NT lidas, mas só pelos campos e prazos, não regra por regra). O MOC 7.0 e o Anexo I que tenho são de novembro de 2020. **Por isso as 27 linhas são provisórias** e a carga as marca assim.
- **O texto da exceção 7 da N12-70 está quebrado pelo PDF** (a frase "nem nas operações internas (idDest=1).de retorno de Mercadoria depositada em depósito fechado ou armazém geral (CFOP 5.906 ou 5.907)" atravessa a quebra de página). A linha leva só os quatro CFOP que a frase cita antes (5.123, 5.922, 6.123 e 6.922); os 5.906 e 5.907 em operação interna ficam de fora até alguém conferir o texto no Anexo I.
- **Não li o Anexo I do MOC atual nem o schema atual da NF-e** (o Portal da NF-e bloqueia a consulta automática e não contornei). As regras ZD, 1C17, 5E17 e B00 ficaram sem linha por decisão de desenho, não por falta de texto.
- **Sem validação do contador:** a C363 é pergunta, não resposta.
- **Natureza, ação padrão, autor e ambiente dos eventos** são leitura minha (seções 5 e 6).

# 9. Perguntas para você

| Id | Pergunta | Recomendação |
|---|---|---|
| Q230-1 | Carregar as **27 linhas** da seção 4 em `Cad_Dfe_Parametro_Regra` (modelos 55 e 65, com início em 04/10/2021, provisórias até conferir com o MOC atual)? | **Sim.** É carga, sem estrutura nova; sem elas o Motor não valida o CST, o DIFAL nem o total antes da SEFAZ |
| Q230-2 | Corrigir a identidade de `Cad_Dfe_Parametro_Regra`: hoje (`Codigo_Regra`, `Ambiente`); passa a ser (`ID_Modelo_Documento`, `Codigo_Regra`, `Ambiente`, `ID_Estado` opcional), como `Cad_Dfe_Leiaute` já faz com `ID_Autoridade` opcional? Os dois campos sobem da versão para o mestre; entidades, campos e chaves estrangeiras não mudam | **Sim.** Sem isso a mesma regra não vale para o 55 e o 65, nem tem linha nacional e de São Paulo, e as regras por UF da NFCom (documento 40) não cabem. A alternativa é um código por modelo e por UF (`NFCE-...`, `...-SP`), que funciona mas espalha a regra |
| Q230-3 | Acrescentar o valor `rejeitado_se_nao_cancelado` a `Cad_Dfe_Evento_Combinacao.Resultado`, carregar os 6 tipos de evento (se faltarem) e as 6 combinações da seção 6? | **Sim.** É o único jeito de a pré-validação do cancelamento seguir a exceção da 4P15-34 |
| Q230-4 | Carregar os **23 códigos de retorno** da seção 5 com a autoridade `AN_NFE`? | **Sim**, provisório. Se preferir um código por SEFAZ, são 27 vezes mais linhas; não recomendo |
| Q230-5 | Tornar `Mov_Nota_Fiscal_Saida_Item_Importacao_Adicao.Numero_Adicao` opcional (vazio na DUImp) e acrescentar `dire` a `Tipo_Declaracao`? | **Sim.** É o que a NT diz; o campo hoje obriga a inventar um número de adição para a DUImp |

Para o contador entra uma pergunta nova no documento 188, a **C363**: se uma NF-e for denegada com a rejeição 307 (emitente bloqueado pela UF de destino em venda interestadual a consumidor final não contribuinte), qual é o efeito na escrituração e na numeração, e como regularizar o bloqueio na UF?

Se você me enviar o **Anexo I do MOC atual** e a **NT 2020.006**, confiro as linhas contra o texto de hoje e fecho a exceção 7 da N12-70.

# 10. Contagens e como será aplicado

**Contagens se tudo for aprovado** (somar à revisão 47): entidades 1.240 (sem mudança); campos 14.398 (sem mudança); referências 3.691 (sem mudança); domínios 373 (sem mudança); tabelas do DDL 1.506 (sem mudança). Mudam: 1 valor de enumeração em `Cad_Dfe_Evento_Combinacao.Resultado`, 1 valor de enumeração em `Tipo_Declaracao` e 1 campo que passa a opcional (`Numero_Adicao`), e, com a Q230-2, as colunas `id_modelo_documento` e `id_estado` passam da tabela de versão para a do mestre, com a chave única de 2 para 4 colunas.

**Carga48 prevista:** 27 linhas de parâmetro, 23 códigos de retorno, 6 tipos de evento (os que faltarem), 6 combinações. Total: **62 linhas**.

Quando você escrever "consolidar" (revisão 48): aplico o que aprovar pelo mesmo mecanismo das revisões anteriores, regero a extração, a normalização, a auditoria, o DDL (PostgreSQL 16 e T-SQL) e os diagramas, gero a carga e confiro as contagens acima, a execução do DDL e a auditoria sem achados.
