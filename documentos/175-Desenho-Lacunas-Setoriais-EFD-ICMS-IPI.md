# Desenho das lacunas setoriais da EFD-ICMS/IPI (G15 a G19), sem o Bloco 1 de combustíveis — Documento 175

*Responde às suas decisões de 05/11/2026 sobre os documentos 167 e 172: as lacunas setoriais entram **todas** (Q167-2), por habilitação da empresa; as tabelas oficiais que faltam são **carregadas** (Q167-5); o Bloco 1 de combustíveis e usina (1300 a 1391) **fica para um bloco próprio** (Q167-6). **Nada entra no dicionário agora**: tudo vai no seu próximo "consolidar". A base é o Guia Prático da EFD-ICMS/IPI, versão 3.2.4 (30/07/2026), lido registro por registro.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

As lacunas G15 a G19 do documento 167 reuniam os registros da EFD-ICMS/IPI que só certos negócios escrituram: exportação, crédito de ICMS controlado fora da apuração, valores agregados por município, energia, documentos em papel, DCTA, GIAF (G15); cupom, Redução Z, Convênio 115 e resumo do SAT (G16); campos do Bloco C que faltavam (G17); bilhetes, comunicação e conhecimento em papel no Bloco D (G18); e dois cadastros (G19). Antes de desenhar, conferi cada registro contra o dicionário da revisão 31. **O documento acrescenta 28 entidades novas (235 campos)** e altera **11 existentes** (**30 campos novos**), mais **5 domínios novos** (47 valores) em `Cad_Classe_Sistema` e **13 valores** de habilitação por empresa (seção 10).

| Lacuna | Assunto | Entidades novas | Campos novos nelas |
|---|---|---|---|
| G15 | Bloco 1 sem combustíveis e usina (1100 a 1110, 1200 a 1210, 1400, 1500 a 1510, 1700 a 1710, 1800, 1960 a 1980) | 8 | 67 |
| G16 | Cupom, Redução Z, Convênio ICMS 115/03 e resumo do SAT | 8 | 75 |
| G17 | Bloco C: C105, C112, C130, C140, C165, C171, C173, C178 e C179 | 8 | 51 |
| G18 | Bilhetes de passagem, comunicação na saída e conhecimento em papel (D160 a D162, D300 a D420, D500 a D530, D695 a D697) | 4 | 42 |
| G19 | Cadastros: 0220 e H010 (só alterações) | 0 | 0 |

**Nove achados que você precisa ler.**

1. **A tabela 5.1.2 é a da CPRB, e o documento 172 a citou errado.** Você disse que ela preenche o P100 e o P110. Confirmei no documento 43: `COD_DETALHAM` é a Tabela 5.1.2 do Guia da EFD-Contribuições (detalhamento da CPRB, P110, cinco linhas) e já tem desenho. O Guia da EFD-ICMS/IPI v3.2.4 **não tem Bloco P e não tem tabela 5.1.2**. O catálogo de ajustes de benefício do validador (`AJ_BENEF_INCENTIVO`, 3.376 linhas) que o documento 172 chamou de "5.1.2" **não tem número no Guia**. A correção é só de texto (seção 9.4; Q175-7).
2. **O Bloco 1 de combustíveis e usina (1300 a 1391) ficou de fora, como você decidiu**, e com ele o que depende dele: `Mov_Nota_Fiscal_Entrada_Item_Tanque` guarda o tanque por **código** até esse bloco ser desenhado (Q175-E4).
3. **Os indicadores do registro 1010 não se guardam.** São derivados: o 1010 diz se o estabelecimento tem exportação, crédito, combustível e os demais, e isso sai de existir ou não o registro correspondente no mês. Só entra a habilitação por empresa, que decide **se o ERP gera** o registro.
4. **O ICMS da Redução Z não estava em lugar nenhum.** `Mov_Ecf_Reducao_Z_Tributo` só tem PIS e Cofins. O registro C420 (totalizadores parciais) e o C490 (analítico por CST, CFOP e alíquota) precisam de entidade. O C490 não se deriva de documentos, porque a fonte é a Redução Z, e o CST e o CFOP de cada totalizador dependem do cadastro do produto **no dia**; guardar evita reescrever a história.
5. **O C591 (FCP) já sai por derivação.** O documento 167 disse que não havia campo; havia: `Mov_Apuracao_Tributo_Item_Parcela_Icms` guarda o FCP por item. Corrijo o documento 167 (Anexo C).
6. **A identidade de `Cad_Utilidade_Classificacao_Efd` (documento 168) estava curta.** O grupo de cClass da NF3e 085 e o 087 alimentam **cinco** campos do C500 (`VL_FORN`, `VL_SERV_NT`, `VL_TERC`, `ENER_INJET`, `OUTRAS_DED`). A identidade passa a ser documento, grupo **e** campo de destino. A carga é só a da NF3e, que o Guia descreve; **a da NFGás não tem fonte** (seção 9.2).
7. **A GIAF é só de Pernambuco.** Os registros 1960, 1970, 1975 e 1980 são exclusivos de contribuintes daquele Estado (Guia, seção 3). Entram como catálogo de 36 campos, com habilitação `efd_giaf_pe`, e o valor de cada campo é informado.
8. **O registro 1400 (valores agregados por município) não é calculável pelo ERP.** O Guia traz a tabela de itens, mas **não a regra** de cada UF (de que CFOP e produto vem o valor, e se o município conta pela origem ou pelo destino). O valor é informado, com um campo que reserva o cálculo para quando o contador trouxer a regra (Q175-C1).
9. **A tabela 4.4.6 (totalizadores da Redução Z, 21 padrões de código) passa a ser carregada**, no catálogo de códigos estaduais do documento 172 (`Cad_Efd_Codigo_Estadual`, sem UF). A decisão antiga do documento 43 ("legado, reavaliar se o desenho passar a gerar C300 a C495") fica revogada: o desenho passa a gerar o C420. O catálogo vai de 1.226 para **1.247 linhas** (seção 9.1).

# 2. Regras que segui

Valem as dos documentos 156 a 172 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória com `Situacao_Dado = provisorio` e `ID_Instancia_Aprovacao` até o contador validar; o ERP avisa e nunca bloqueia; nomes em português com sublinhado; mestre só onde outra tabela aponta para a versão aplicada; lado comprador só quando há cliente, D-N68). Específicas deste documento:

1. **O ERP só registra.** O que se deriva de notas, apurações e inventários não se grava: o 1105 e o 1110 saem do item da nota de exportação, o 1500 da nota de saída de energia, o C591 do FCP do item, o H005 da soma dos itens do inventário, o 1010 dos registros do mês. **Grava-se o que uma mudança futura reescreveria** (o C490, o C420, o 1800) **e o que não tem outra fonte** (o 1400 e a GIAF, o 1700).
2. **O dado entra "tal como emitido".** Os valores de IRRF e previdência do C130, a fatura do C140 e o documento de arrecadação do C112 são os que o documento traz; o ERP não os recalcula.
3. **Habilitação por empresa, sem padrão escondido.** Cada conjunto de registros só é gerado para a empresa que o tem em `Cad_Empresa_Modulo_Opcional` (domínio `modulo_fiscal_opcional`, seção 10). Quem não habilita nada não gera nenhum.
4. **Pai genérico quando a regra vale em entrada e saída** (`Origem_Tipo` mais `ID_Nota`), como em `Mov_Nota_Observacao_Lancamento`.
5. **Extensão 1:1 quando o dado é só de um tipo de nota** (C130, C165, C179) e **filho 1:N quando se repete** (C171, C173, C112).
6. **Uma leitura minha é sempre dita como minha** e vai ao contador.

# 3. G15: Bloco 1 sem combustíveis e usina

## 3.1 O que o texto pede e o que o dicionário já tinha

O Guia (Bloco 1) lista os registros abaixo. A coluna da direita diz o que já existe e o que falta; o detalhe de cada registro está no Anexo B.

| Registro | O que é | Já existia | O que falta |
|---|---|---|---|
| 1100, 1105, 1110 | Exportação: declaração, nota e nota de origem (exportação indireta) | `Mov_Nota_Fiscal_Saida_Item_Exportacao` (chave, RE, data de embarque) e o evento de averbação da DU-E | A declaração em si (`IND_DOC`, `DT_DE`, `DT_RE`, `CHC_EMB`, `DT_CHC`, `TP_CHC`, país) e o vínculo da nota à declaração; a nota de origem sem chave (modelos 01, 1B e 04) |
| 1200, 1210 | Controle de créditos de ICMS fora da apuração | `Mov_Credito_Fiscal` e `Mov_Credito_Fiscal_Aplicacao` (saldo, apropriação, aplicação) | O código da tabela 5.1.1 do crédito, o código do tipo de utilização (tabela 5.5), o documento da baixa, `CRED_RECEB` |
| 1400 | Valores agregados por município (índice de participação) | Nada | A entidade inteira; a tabela de itens (5.9.1 e 5.9.2) já está na carga do documento 172 |
| 1500, 1510 | Energia elétrica na saída interestadual | A nota de saída (modelo 06) e o item | `IND_REC` (receita própria ou de terceiros) e o participante por item |
| 1700, 1710 | Documentos fiscais em papel utilizados e cancelados | `Cad_Serie_Documento_Fiscal` (série e numeração) | A faixa mensal, o tipo de dispositivo e o número da autorização |
| 1800 | DCTA (transporte aéreo) | Nada | O demonstrativo (quatro entradas; o resto é cálculo) |
| 1960, 1970, 1975, 1980 | GIAF 1, 3 e 4 (só Pernambuco) | Nada | O catálogo de campos e o valor de cada um |

**Como ficam as ligações.** A nota de exportação (`Mov_Nota_Fiscal_Saida_Item_Exportacao`) passa a apontar para `Mov_Exportacao_Declaracao`; por ela o 1105 (nota por declaração) e o 1110 (nota de origem) saem **por derivação**, sem entidade própria. Na exportação indireta o item aponta a nota de origem recebida com fim específico (`ID_Nota_Fiscal_Entrada`), o que cobre as notas sem chave, onde `Chave_Nota_Exportacao` não existe.

## 3.2 Entidade nova: `Mov_Exportacao_Declaracao`

A declaração de exportação concluída no mês, uma linha por registro de exportação (RE) quando há mais de um para a mesma declaração (registro 1100). A nota de saída de exportação liga-se a ela pelo item (`Mov_Nota_Fiscal_Saida_Item_Exportacao.ID_Exportacao_Declaracao`); com isso o 1105 e o 1110 saem por derivação, sem entidade própria. Só existe para quem exporta (habilitação `efd_exportacao_1100`).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 15.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Exportacao_Declaracao` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento efetivo exportador, direto ou indireto. |
| `Competencia` | competência | O mês em que a exportação se concluiu, e em que o 1100 sai (o Guia manda preencher "no mês em que se concluir a exportação"). |
| `Tipo_Documento` | enumeração {declaracao_exportacao, declaracao_simplificada, declaracao_unica} | IND_DOC 0, 1 e 2 (DE, DSE e DU-E). |
| `Numero_Declaracao` | código (até 14) | NRO_DE. A DU-E tem 14 posições; já existe em `Mov_Dfe_Evento_Item.Numero_Due` quando o evento de averbação 790700 foi recebido. |
| `Data_Declaracao` | data | DT_DE. |
| `Natureza_Exportacao` | enumeração {direta, indireta} | NAT_EXP 0 e 1. Na indireta o item da nota traz a nota de origem (1110). |
| `Numero_Registro_Exportacao` | código (até 12), opcional | NRO_RE: obrigatório quando o tipo é declaração de exportação (IND_DOC 0). |
| `Data_Registro_Exportacao` | data, opcional | DT_RE. |
| `Numero_Conhecimento_Embarque` | código (até 18), opcional | CHC_EMB. |
| `Data_Conhecimento_Embarque` | data, opcional | DT_CHC. |
| `Data_Averbacao` | data | DT_AVB. Quando o evento 790700 existe (`Mov_Dfe_Evento_Item.Data_Hora_Averbacao`), a data é copiada dele e o usuário confirma. |
| `ID_Tipo_Conhecimento_Embarque` | referência (Cad_Classe_Sistema, domínio = tipo_conhecimento_embarque) | TP_CHC: AWB, MAWB, HAWB, BL, CRT e os demais 22 códigos do Guia. |
| `ID_Pais_Destino` | referência (Cad_Pais) | PAIS: país de destino da mercadoria, pela tabela do Siscomex (`Cad_Pais`). |
| `ID_Dfe_Evento_Item` | referência (Mov_Dfe_Evento_Item), opcional | O evento de averbação de onde vieram a DU-E e a data, quando existe. |

## 3.3 Entidade nova: `Mov_Valor_Agregado_Municipio`

O valor mensal por município e por item do índice de participação dos municípios (registro 1400), exigido só pela UF que o pede. A tabela de itens (5.9.1 e 5.9.2) é o catálogo `Cad_Efd_Codigo_Estadual` (`cod_item_ipm`, 568 linhas do documento 172); a regra de cálculo de cada UF (de qual CFOP e produto vem o valor, e qual município conta, origem ou destino) **não está no Guia**, então o valor é informado e não calculado (Q175-C1).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 8.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Valor_Agregado_Municipio` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento declarante, ou com inscrição de substituto tributário na UF. |
| `Competencia` | competência | O mês. |
| `ID_Efd_Codigo_Estadual` | referência (Cad_Efd_Codigo_Estadual), opcional | COD_ITEM_IPM quando é código da tabela 5.9.1 (ou 5.9.2, no ST). Exatamente um entre este campo e `ID_Produto_Servico`. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico), opcional | COD_ITEM_IPM quando é o código do item do registro 0200. |
| `ID_Municipio` | referência (Cad_Municipio) | MUN: município de origem ou destino, conforme a regra da UF. |
| `Valor_Agregado` | número | VALOR: valor mensal do município. |
| `Origem_Valor` | enumeração {informado, calculado_pelo_erp} | `informado` hoje. `calculado_pelo_erp` fica reservado para quando o contador trouxer a regra da UF (Q175-C1). |

## 3.4 Entidade nova: `Mov_Documento_Dispositivo_Utilizado`

A faixa de dispositivos autorizados e utilizados na emissão de documentos fiscais em papel no mês (registro 1700), exigida só pela UF que controla a utilização (a UF diz). O número da autorização de impressão (NUM_AUT, até 60 posições) e o tipo do dispositivo não estão em `Cad_Serie_Documento_Fiscal`, que só guarda série e numeração.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 9.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Documento_Dispositivo_Utilizado` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento. |
| `Competencia` | competência | O mês da EFD. |
| `ID_Serie_Documento_Fiscal` | referência (Cad_Serie_Documento_Fiscal) | COD_MOD e SER saem da série. |
| `Subserie` | código (até 3), opcional | SUB do dispositivo autorizado. |
| `ID_Tipo_Dispositivo` | referência (Cad_Classe_Sistema, domínio = tipo_dispositivo_documento_fiscal) | COD_DISP 00 a 05: formulário de segurança (impressor autônomo), FS-DA, formulário de segurança da NF-e, formulário contínuo, blocos e jogos soltos. |
| `Numero_Inicial` | número | NUM_DOC_INI: primeiro número utilizado (12 posições). |
| `Numero_Final` | número | NUM_DOC_FIN: último número utilizado. |
| `Numero_Autorizacao` | código (até 60) | NUM_AUT: número da autorização do dispositivo. |

## 3.5 Entidade nova: `Mov_Documento_Dispositivo_Cancelado`

A faixa cancelada ou inutilizada dentro da faixa utilizada (registro 1710). Os documentos eletrônicos inutilizados ficam em `Mov_Dfe_Inutilizacao`; esta entidade é só para o papel.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 4.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Documento_Dispositivo_Cancelado` | identificador | --- |
| `ID_Documento_Dispositivo_Utilizado` | referência (Mov_Documento_Dispositivo_Utilizado) | A faixa utilizada (1700) que contém a faixa cancelada. |
| `Numero_Inicial` | número | NUM_DOC_INI do 1710. |
| `Numero_Final` | número | NUM_DOC_FIN do 1710. |

## 3.6 Entidade nova: `Mov_Dcta_Apuracao`

O demonstrativo de crédito do ICMS sobre o transporte aéreo (DCTA, registro 1800), um por estabelecimento e mês. Guarda só as **quatro entradas**; o faturamento, o índice de rateio, o crédito e a base apurados e a diferença são cálculo do Motor. A diferença (VL_DIF) vira o estorno de crédito da apuração, ligado em `ID_Apuracao_Ajuste`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 8.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Dcta_Apuracao` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | A empresa de transporte aéreo. |
| `Competencia` | competência | O mês. |
| `Valor_Prestacao_Carga_Tributada` | número | VL_CARGA: valor das prestações de carga (tributado). |
| `Valor_Prestacao_Passageiro_Nao_Tributada` | número | VL_PASS: valor das prestações de passageiros e cargas (não tributado). |
| `Valor_Creditos_Icms` | número | VL_ICMS_ANT: total dos créditos do ICMS. |
| `Valor_Base_Calculo_Icms` | número | VL_BC_ICMS: valor da base de cálculo do ICMS. |
| `ID_Apuracao_Ajuste` | referência (Mov_Apuracao_Ajuste), opcional | O ajuste de estorno de crédito (E111) que recebe a diferença VL_DIF. Vazio até o Motor gerá-lo. |

## 3.7 Entidade nova: `Cad_Efd_Giaf_Campo`

O catálogo dos campos das GIAF 1, 3 e 4 (registros 1960, 1970, 1975 e 1980), **exclusivos de contribuintes de Pernambuco** (Guia, seção 3). Os campos são numerados `G1_01` a `G4_12`, com descrição e sem fórmula no Guia; por isso entram como catálogo com vigência, e o valor de cada um é informado. Carga provisória do Guia (Anexo A.1).

*Tipo: catálogo com vigência (carga provisória). Mestre: sim. Vigência: sim. Campos: 13.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_Giaf_Campo` | identificador | --- |
| `ID_Efd_Giaf_Campo_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Efd_Giaf_Campo_Versao). |
| `Modelo_Giaf` | enumeração {giaf_1_industria, giaf_3_importacao, giaf_4_central_distribuicao} --- identidade | GIAF 1 (1960), GIAF 3 (1970 e 1975) ou GIAF 4 (1980). |
| `Codigo_Campo` | código (até 6) --- identidade | G1_01, G3_T, G4_12 etc., como no Guia. |
| `Descricao` | texto | Como no Guia. |
| `Tipo_Valor` | enumeração {valor, percentual} | `percentual` nos campos que o Guia chama de percentual (G1_01, G3_04, G4_01 e G4_04). |
| `Registro_Efd` | enumeração {r1960, r1970, r1975, r1980} | O registro que traz o campo; o G3_10 a G3_12 saem no 1975, por alíquota. |
| `Ordem` | número | A posição do campo no registro. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 3.8 Entidade nova: `Mov_Efd_Giaf_Apuracao`

Uma GIAF do mês por estabelecimento, modelo e indicador de sub-apuração por tipo de benefício (IND_AP, tabela 4.7.1): é o cabeçalho de 1960, 1970 e 1980. Habilitação `efd_giaf_pe`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 5.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_Giaf_Apuracao` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) --- identidade | O estabelecimento de Pernambuco. |
| `Competencia` | competência --- identidade | O mês. |
| `Modelo_Giaf` | enumeração {giaf_1_industria, giaf_3_importacao, giaf_4_central_distribuicao} --- identidade | Qual GIAF. |
| `ID_Efd_Codigo_Estadual` | referência (Cad_Efd_Codigo_Estadual) --- identidade | IND_AP: a linha de `ind_subap` (49 linhas de PE, documento 172) que o Guia chama de tabela 4.7.1. |

## 3.9 Entidade nova: `Mov_Efd_Giaf_Valor`

O valor de cada campo da GIAF. No 1975 há uma linha por alíquota das importações-base (até quatro), com os campos G3_10 a G3_12.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 5.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_Giaf_Valor` | identificador | --- |
| `ID_Efd_Giaf_Apuracao` | referência (Mov_Efd_Giaf_Apuracao) --- identidade | A GIAF. |
| `ID_Efd_Giaf_Campo` | referência (Cad_Efd_Giaf_Campo) --- identidade | O campo. |
| `Aliquota_Importacao_Base` | número, opcional --- identidade | ALIQ_IMP_BASE do 1975. Obrigatório nos campos G3_10 a G3_12; vazio nos demais. |
| `Valor` | número | O valor informado, ou o percentual quando `Tipo_Valor` é `percentual`. |

As alterações em entidades existentes que servem ao G15 (`Mov_Nota_Fiscal_Saida_Item_Exportacao`, `Mov_Credito_Fiscal`, `Mov_Credito_Fiscal_Aplicacao` e o item de saída, para o 1510) estão na seção 8.

# 4. G16: cupom, Redução Z, Convênio ICMS 115/03 e resumo do SAT

## 4.1 O que o texto pede e o que o dicionário já tinha

O dicionário tem a Redução Z (`Mov_Ecf_Reducao_Z`), o equipamento (`Cad_Equipamento_Fiscal`) e o PIS e a Cofins por totalizador, mas **o ICMS e o ISSQN da Redução Z não estavam em lugar nenhum**. Cada totalizador parcial do C420 tem um código da tabela 4.4.6 (por exemplo, `T1800` é a carga tributária efetiva de 18,00%, e `02T1800` é o totalizador de número 02 com a mesma carga). O Guia manda conferir que o valor acumulado do totalizador é a soma dos valores de operação do C490; o ERP **avisa** quando a conta não fecha.

| Registro | O que é | Onde fica |
|---|---|---|
| C420 | Totalizadores parciais da Redução Z | `Mov_Ecf_Reducao_Z_Totalizador` (nova) |
| C425 | Resumo de itens do movimento diário | `Mov_Ecf_Reducao_Z_Totalizador_Item` (nova) |
| C460, C465, C470 | Cupom fiscal emitido por ECF, número do contador e itens | `Mov_Nota_Fiscal_Saida` (modelos 02, 2D e 60) com `ID_Reducao_Z`, `Numero_Contador_Cupom_Fiscal` e, no item, `Quantidade_Cancelada` (seção 8) |
| C490 | Analítico do movimento diário (CST, CFOP, alíquota) | `Mov_Ecf_Reducao_Z_Analitico` (nova) |
| C591 | FCP por item (NF3e e NFGás) | **Derivado** do FCP do item, em `Mov_Apuracao_Tributo_Item_Parcela_Icms` |
| C700, C790, C791, D695 a D697 | Arquivo mestre do Convênio 115/03 | `Mov_Convenio115_Consolidacao`, `_Analitico` e `_Uf` (novas) |
| C895, C897 | Observação e ajuste do resumo diário do SAT | `Mov_Sat_Resumo_Observacao` e `Mov_Sat_Resumo_Ajuste` (novas) |

**Nota modelo 02 (C300 a C395).** O C350 e o C370 (nota individual e itens) já saem de `Mov_Nota_Fiscal_Saida`; o C300 (resumo diário) é derivado delas. **Falta decidir o caso em que só existe o resumo consolidado, sem as notas individuais**, que é o padrão do Convênio 115 (Q175-E1): se existir, cria-se uma consolidação igual à seção 4.5.

## 4.2 Entidade nova: `Mov_Ecf_Reducao_Z_Totalizador`

Os totalizadores parciais da Redução Z (registro C420, e D365 no ECF de bilhete): o ICMS e o ISSQN da Redução Z não estavam em lugar nenhum (`Mov_Ecf_Reducao_Z_Tributo` só tem PIS e Cofins). O código é do padrão da tabela 4.4.6 (Tnnnn, xxTnnnn, Fn, In, Nn, Snnnn, DT, AT, CAN-T e os demais), e o "nnnn" é a carga tributária efetiva em duas casas.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 7.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Reducao_Z_Totalizador` | identificador | --- |
| `ID_Reducao_Z` | referência (Mov_Ecf_Reducao_Z) | A Redução Z do equipamento (de mercadoria ou de bilhete). |
| `ID_Efd_Codigo_Estadual` | referência (Cad_Efd_Codigo_Estadual) | O padrão da tabela 4.4.6 (`tot_parc_redz`, 21 linhas) a que o código obedece. |
| `Codigo_Totalizador` | código (até 7) | COD_TOT_PAR como o equipamento o grava (T1800, 02T1800, F1, I1, S0500, OPNF, DT...). O Motor confere o código contra o padrão e avisa quando não confere. |
| `Numero_Totalizador` | número, opcional | NR_TOT: o número do totalizador quando há mais de um para a mesma situação tributária ou alíquota. |
| `Descricao_Situacao_Tributaria` | texto, opcional | DESCR_NR_TOT: descrição da situação tributária do totalizador. |
| `Valor_Acumulado` | número | VLR_ACUM_TOT: valor acumulado no totalizador, relativo à Redução Z. |

## 4.3 Entidade nova: `Mov_Ecf_Reducao_Z_Totalizador_Item`

O resumo de itens do movimento diário (registro C425): o item, a quantidade e o valor por totalizador. É obrigatório quando o totalizador é Tnnnn, xxTnnnn, Fn, In ou Nn, e não se informa para OPNF nem para cancelamentos (Guia, C425); o item não repete dentro do mesmo totalizador. O PIS e a Cofins do item continuam em `Mov_Ecf_Reducao_Z_Tributo`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 6.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Reducao_Z_Totalizador_Item` | identificador | --- |
| `ID_Reducao_Z_Totalizador` | referência (Mov_Ecf_Reducao_Z_Totalizador) --- identidade | O totalizador (C420) a que o item pertence. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico) --- identidade | COD_ITEM. |
| `Quantidade` | número | QTD: quantidade acumulada do item. Só existia `Quantidade_Base_Calculo`, que é outra coisa. |
| `ID_Unidade_Medida` | referência (Cad_Unidade_Medida) | UNID. |
| `Valor_Item` | número | VL_ITEM: valor acumulado do item. |

## 4.4 Entidade nova: `Mov_Ecf_Reducao_Z_Analitico`

O registro analítico do movimento diário por CST, CFOP e alíquota (C490, e D390 no ECF de bilhete). Não se deriva de documentos: a fonte é a Redução Z, que totaliza por situação tributária, e o CST e o CFOP que classificam cada totalizador dependem do cadastro do produto **no dia**; guardar evita reescrever a história quando o cadastro muda (regra da seção 2).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 12.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Reducao_Z_Analitico` | identificador | --- |
| `ID_Reducao_Z` | referência (Mov_Ecf_Reducao_Z) | A Redução Z. |
| `ID_Cst` | referência (Cad_Cst) | CST_ICMS. |
| `ID_CFOP` | referência (Cad_CFOP) | CFOP. |
| `Aliquota_Icms` | número, opcional | ALIQ_ICMS. |
| `Valor_Operacao` | número | VL_OPR: valor da operação na combinação. |
| `Base_Calculo_Icms` | número | VL_BC_ICMS. |
| `Valor_Icms` | número | VL_ICMS. |
| `Base_Calculo_Iss` | número, opcional | VL_BC_ISSQN: só no D390 (ECF de bilhete). |
| `Aliquota_Iss` | número, opcional | ALIQ_ISSQN: só no D390. |
| `Valor_Iss` | número, opcional | VL_ISSQN: só no D390. |
| `ID_Observacao_Lancamento` | referência (Cad_Observacao_Lancamento_Fiscal), opcional | COD_OBS da combinação (tabela 0460). |

## 4.5 Entidade nova: `Mov_Convenio115_Consolidacao`

A consolidação do arquivo mestre do Convênio ICMS 115/03 por série e faixa de ordem: energia, gás e NF3e (C700, modelos 06, 28 e 66) e comunicação e telecomunicação (D695, modelos 21 e 22). Só o prestador sujeito ao convênio a escritura (habilitação `efd_convenio_115`); as notas individuais **não** ficam na EFD, só o mestre.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 11.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Convenio115_Consolidacao` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento prestador. |
| `Competencia` | competência | O mês da EFD em que o arquivo mestre é escriturado. |
| `ID_Modelo_Documento` | referência (Cad_Modelo_Documento_Fiscal) | COD_MOD: 06, 28 ou 66 (C700); 21 ou 22 (D695). O modelo decide o registro. |
| `Serie` | código (até 4), opcional | SER. |
| `Numero_Ordem_Inicial` | número | NRO_ORD_INI. |
| `Numero_Ordem_Final` | número | NRO_ORD_FIN. |
| `Data_Emissao_Inicial` | data | DT_DOC_INI. |
| `Data_Emissao_Final` | data | DT_DOC_FIN. |
| `Nome_Arquivo_Mestre` | código (até 33), opcional | NOM_MEST: nome do arquivo mestre de documento fiscal. |
| `Chave_Codificacao_Digital` | código (até 32), opcional | CHV_COD_DIG: chave de codificação digital do arquivo mestre (hash de 32 posições). Não é a `Hash_Convenio_115` da nota referenciada. |

## 4.6 Entidade nova: `Mov_Convenio115_Consolidacao_Analitico`

O registro analítico da consolidação (C790 e D696) por CST, CFOP e alíquota. Guardado porque as notas do mestre não estão no ERP: não há de onde derivar.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 14.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Convenio115_Consolidacao_Analitico` | identificador | --- |
| `ID_Convenio115_Consolidacao` | referência (Mov_Convenio115_Consolidacao) | A consolidação. |
| `ID_Cst` | referência (Cad_Cst) | CST_ICMS. |
| `ID_CFOP` | referência (Cad_CFOP) | CFOP. |
| `Aliquota_Icms` | número, opcional | ALIQ_ICMS. |
| `Valor_Operacao` | número | VL_OPR. |
| `Base_Calculo_Icms` | número | VL_BC_ICMS. |
| `Valor_Icms` | número | VL_ICMS. |
| `Base_Calculo_Icms_St` | número, opcional | VL_BC_ICMS_ST: só no C790. |
| `Valor_Icms_St` | número, opcional | VL_ICMS_ST: só no C790. |
| `Base_Calculo_Icms_Outras_Ufs` | número, opcional | VL_BC_ICMS_UF: só no D696. |
| `Valor_Icms_Outras_Ufs` | número, opcional | VL_ICMS_UF: só no D696. |
| `Valor_Reducao_Base_Calculo` | número | VL_RED_BC. |
| `ID_Observacao_Lancamento` | referência (Cad_Observacao_Lancamento_Fiscal), opcional | COD_OBS. |

## 4.7 Entidade nova: `Mov_Convenio115_Consolidacao_Uf`

Os valores por UF da consolidação: ICMS ST por UF nas energias e na NF3e (C791) e ICMS de outras UFs na TV por assinatura via satélite, serviço não medido (D697, Convênio ICMS 52/05).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 7.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Convenio115_Consolidacao_Uf` | identificador | --- |
| `ID_Convenio115_Consolidacao` | referência (Mov_Convenio115_Consolidacao) | A consolidação. |
| `ID_Estado` | referência (Cad_Estado) | UF. |
| `Base_Calculo_Icms` | número, opcional | VL_BC_ICMS do D697. |
| `Valor_Icms` | número, opcional | VL_ICMS do D697. |
| `Base_Calculo_Icms_St` | número, opcional | VL_BC_ICMS_ST do C791. |
| `Valor_Icms_St` | número, opcional | VL_ICMS_ST do C791. |

## 4.8 Entidade nova: `Mov_Sat_Resumo_Observacao`

A observação do lançamento do resumo diário do CF-e-SAT por equipamento (registro C895, filho do C890). O C890 é derivado das notas; a observação não pode ficar na nota porque pertence à combinação de equipamento, dia, CST, CFOP e alíquota.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 8.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Sat_Resumo_Observacao` | identificador | --- |
| `ID_Equipamento_Fiscal` | referência (Cad_Equipamento_Fiscal) | O SAT. |
| `Data_Movimento` | data | O dia do resumo. |
| `ID_Cst` | referência (Cad_Cst) | CST da linha do C890. |
| `ID_CFOP` | referência (Cad_CFOP) | CFOP da linha. |
| `Aliquota_Icms` | número, opcional | Alíquota da linha. |
| `ID_Observacao_Lancamento` | referência (Cad_Observacao_Lancamento_Fiscal) | COD_OBS. |
| `Texto_Complementar` | texto, opcional | TXT_COMPL. |

## 4.9 Entidade nova: `Mov_Sat_Resumo_Ajuste`

O ajuste que vem da observação do resumo diário do SAT (registro C897). Mesmos campos de `Mov_Nota_Ajuste_Documento`, com o item pelo produto, porque o resumo não tem item de nota. O valor soma direto na apuração (E110 ou sub-apuração) pelas mesmas regras do C197.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 10.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Sat_Resumo_Ajuste` | identificador | --- |
| `ID_Sat_Resumo_Observacao` | referência (Mov_Sat_Resumo_Observacao) | A observação (C895) a que o ajuste pertence. |
| `ID_Codigo_Ajuste` | referência (Cad_Icms_Codigo_Ajuste) | COD_AJ: código da tabela 5.3 da UF. |
| `Descricao_Complementar` | texto, opcional | DESCR_COMPL_AJ. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico), opcional | COD_ITEM. |
| `Base_Calculo_Icms` | número, opcional | VL_BC_ICMS. |
| `Aliquota_Icms` | número, opcional | ALIQ_ICMS. |
| `Valor_Icms` | número, opcional | VL_ICMS: soma direto na apuração quando o ajuste não é só informativo. |
| `Valor_Outros` | número, opcional | VL_OUTROS. |
| `ID_Subapuracao` | referência (Mov_Apuracao_Icms_Subapuracao), opcional | A sub-apuração que recebe o valor quando o quarto caractere do código é 3 a 8. |

# 5. G17: campos do Bloco C que faltavam

## 5.1 O que o texto pede e o que o dicionário já tinha

| Registro | O que é | Onde fica |
|---|---|---|
| C105 | UF do recolhimento do ICMS ST, quando difere da do destinatário | `Mov_Nota_Fiscal_Icms_St_Uf_Recolhimento` (nova) |
| C112 | Documento de arrecadação citado na nota | `Mov_Nota_Fiscal_Documento_Arrecadacao` (nova) |
| C130 | Serviço sem ICMS, IRRF e previdência destacados | `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms` (nova); o ISSQN sai da apuração do item |
| C140, C141 | Fatura comercial e vencimentos | `Mov_Nota_Fiscal_Fatura_Comercial` (nova); os vencimentos já saem de `Mov_Titulo` |
| C165 | Transporte da nota de combustível | `Mov_Nota_Fiscal_Saida_Combustivel_Transporte` (nova) |
| C171 | Armazenamento por tanque na entrada | `Mov_Nota_Fiscal_Entrada_Item_Tanque` (nova) |
| C173 | Medicamento: lote, tipo de base e tipo de produto | `Mov_Nota_Fiscal_Entrada_Item_Lote` (nova) e `IND_MED` e `TP_PROD` no item (seção 8); na saída o lote já existe |
| C178 | Classe de enquadramento do IPI | `ID_Classe_Enquadramento_Ipi` no item de saída (seção 8) |
| C179 | Informações complementares do ICMS ST do item | `Mov_Nota_Fiscal_Saida_Item_St_Informacao` (nova) |

## 5.2 Entidade nova: `Mov_Nota_Fiscal_Documento_Arrecadacao`

O documento de arrecadação citado nas informações complementares da nota (registro C112): guia estadual ou GNRE. Obrigatório quando a nota cita a guia. É referência da nota; **não** substitui a guia do módulo de obrigações, a que se liga quando ela está no ERP.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 11.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Documento_Arrecadacao` | identificador | --- |
| `Origem_Tipo` | enumeração {nota_fiscal_entrada, nota_fiscal_saida} | Direção da nota: o C112 vale em entrada e em saída. |
| `ID_Nota` | referência genérica | A nota de entrada ou de saída, conforme `Origem_Tipo`. |
| `Tipo_Documento_Arrecadacao` | enumeração {estadual, gnre} | COD_DA 0 e 1. |
| `ID_Estado` | referência (Cad_Estado) | UF: a unidade federada beneficiária do recolhimento. |
| `Numero_Documento_Arrecadacao` | código (até 60), opcional | NUM_DA. |
| `Codigo_Autenticacao_Bancaria` | código (até 60), opcional | COD_AUT: código completo da autenticação bancária. |
| `Valor_Documento` | número | VL_DA: valor total do documento (principal, atualização monetária, juros e multa). |
| `Data_Vencimento` | data | DT_VCTO. |
| `Data_Pagamento` | data | DT_PGTO; no ICMS antecipado a recolher, a data do vencimento (regra do Guia). |
| `ID_Apuracao_Obrigacao_Recolher` | referência (Mov_Apuracao_Obrigacao_Recolher), opcional | A guia do módulo de obrigações, quando existe. |

## 5.3 Entidade nova: `Mov_Nota_Fiscal_Fatura_Comercial`

A fatura comercial das notas modelo 01 e 1A (registro C140): o tipo e o número do título de crédito. A quantidade de parcelas e o valor total saem de `Mov_Titulo` (um título por parcela) e o emitente do título sai da nota; os vencimentos (C141) já saem de `Mov_Titulo`. Não é `Mov_Nota_Fiscal_Entrada_Fatura`, que é da NFCom e da NFAg.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 6.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Fatura_Comercial` | identificador | --- |
| `Origem_Tipo` | enumeração {nota_fiscal_entrada, nota_fiscal_saida} | Direção da nota. |
| `ID_Nota` | referência genérica | A nota, conforme `Origem_Tipo`. |
| `Tipo_Titulo_Credito` | enumeração {duplicata, cheque, promissoria, recibo, outros} | IND_TIT 00, 01, 02, 03 e 99. Havendo mais de um tipo de título na fatura, `outros`. |
| `Descricao_Titulo` | texto, opcional | DESC_TIT: obrigatório quando `outros`, com os números e os valores de cada título. |
| `Numero_Titulo` | código (até 60) | NUM_TIT: número ou código identificador do título. |

## 5.4 Entidade nova: `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms`

O serviço sem ICMS e as retenções destacadas na nota de saída (registro C130): o ISSQN sai da apuração do ISS do item (`Mov_Apuracao_Tributo_Item`, imposto ISS); o IRRF e a previdência, **como estão destacados no documento**, não existiam (o ERP guarda a retenção na baixa do título, não o destaque da nota). Valores como emitidos, nunca recalculados.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 7.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Saida_Servico_Nao_Icms` | identificador | --- |
| `ID_Nota` | referência (Mov_Nota_Fiscal_Saida) --- identidade | A nota de saída (1:1, opcional). |
| `Valor_Servico_Nao_Tributado_Icms` | número, opcional | VL_SERV_NT: valor dos serviços sob não incidência ou não tributados pelo ICMS. |
| `Base_Calculo_Irrf` | número, opcional | VL_BC_IRRF. |
| `Valor_Irrf` | número, opcional | VL_IRRF. |
| `Base_Calculo_Previdencia` | número, opcional | VL_BC_PREV. |
| `Valor_Previdencia` | número, opcional | VL_PREV. |

## 5.5 Entidade nova: `Mov_Nota_Fiscal_Saida_Combustivel_Transporte`

Os dados de transporte da nota de combustível (registro C165): passe fiscal, temperatura e motorista. A placa, a UF da placa, o transportador, a hora, os volumes e os pesos já existem na nota; o código de autorização (COD_AUT) é o `Combustivel_Codigo_Codif` do item. Habilitação `efd_combustivel_c165`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 6.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Saida_Combustivel_Transporte` | identificador | --- |
| `ID_Nota` | referência (Mov_Nota_Fiscal_Saida) --- identidade | A nota de saída (1:1, opcional). |
| `Numero_Passe_Fiscal` | código (até 30), opcional | NR_PASSE. |
| `Temperatura_Celsius` | número, opcional | TEMPER: temperatura em graus Celsius usada para o cálculo do volume (uma casa decimal). Não é a `Combustivel_Quantidade_Temperatura_Ambiente` (qTemp), que é uma quantidade. |
| `Nome_Motorista` | texto (até 60), opcional | NOM_MOT. |
| `Cpf_Motorista` | código (11), opcional | CPF do motorista. |

## 5.6 Entidade nova: `Mov_Nota_Fiscal_Entrada_Item_Tanque`

O armazenamento do combustível recebido por tanque (registro C171, exigência do livro de movimentação de combustíveis, Ajuste SINIEF 01/92): o item recebido pode ir a vários tanques. O tanque é por ora um código; vira referência quando o Bloco 1 de combustíveis for desenhado (Q167-6).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 4.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Entrada_Item_Tanque` | identificador | --- |
| `ID_Item_Entrada` | referência (Mov_Nota_Fiscal_Entrada_Item) --- identidade | O item de combustível recebido. |
| `Numero_Tanque` | código (até 3) --- identidade | NUM_TANQUE. |
| `Quantidade_Armazenada` | número | QTDE: quantidade ou volume armazenado no tanque. |

## 5.7 Entidade nova: `Mov_Nota_Fiscal_Entrada_Item_Lote`

O lote do item recebido (para o C173 de medicamentos na entrada: lote, quantidade, fabricação e validade). A saída já tem `Mov_Nota_Fiscal_Saida_Item_Lote`; a entrada só tinha o lote no movimento de estoque. Fabricação e validade saem de `Cad_Lote_Produto`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 4.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Entrada_Item_Lote` | identificador | --- |
| `ID_Item_Entrada` | referência (Mov_Nota_Fiscal_Entrada_Item) | O item recebido. |
| `ID_Lote` | referência (Cad_Lote_Produto) | O lote: LOTE_MED, DT_FAB e DT_VAL. |
| `Quantidade_Lote` | número | QTD_ITEM: quantidade do item no lote. |

## 5.8 Entidade nova: `Mov_Nota_Fiscal_Saida_Item_St_Informacao`

As informações complementares do ICMS ST do item da nota de saída (registro C179): base na origem e no destino, repasse ou dedução, complemento, e a retenção em remessa por substituído. Só existiam a base e o valor retido da operação própria.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 7.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Saida_Item_St_Informacao` | identificador | --- |
| `ID_Item` | referência (Mov_Nota_Fiscal_Saida_Item) --- identidade | O item de saída (1:1, opcional). |
| `Base_Calculo_St_Origem_Destino` | número | BC_ST_ORIG_DEST: base de cálculo do ICMS ST na origem ou no destino, nas operações interestaduais. |
| `Valor_Icms_St_Repasse_Deducao` | número | ICMS_ST_REP: valor do ICMS ST a repassar ou deduzir. |
| `Valor_Icms_St_Complemento` | número, opcional | ICMS_ST_COMPL: valor do ICMS ST a complementar à UF. |
| `Base_Calculo_Retencao_Remessa` | número, opcional | BC_RET: base de retenção em remessa. |
| `Valor_Icms_Retido_Remessa` | número, opcional | ICMS_RET: parcela do imposto retido em remessa promovida por substituído. |

## 5.9 Entidade nova: `Mov_Nota_Fiscal_Icms_St_Uf_Recolhimento`

A UF a que o ICMS ST é recolhido quando é diversa da do destinatário (registro C105): combustíveis e lubrificantes, leasing ou faturamento direto, e recusa de recebimento. Para os dois primeiros o Motor **copia** a UF no momento da emissão (UF de consumo do item; local de retirada); só no leasing ela é digitada. Vale em entrada e saída.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 6.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Icms_St_Uf_Recolhimento` | identificador | --- |
| `Origem_Tipo` | enumeração {nota_fiscal_entrada, nota_fiscal_saida} | Direção da nota. |
| `ID_Nota` | referência genérica | A nota (modelo 55), conforme `Origem_Tipo`. |
| `Tipo_Operacao` | enumeração {combustiveis_lubrificantes, leasing_faturamento_direto, recusa_recebimento} | OPER 0, 1 e 2. |
| `ID_Estado` | referência (Cad_Estado) | UF: sigla da UF de destino do ICMS ST. |
| `Origem_Dado` | enumeração {copiado_da_nota, informado} | `copiado_da_nota` quando o Motor copiou a UF de consumo ou do local de retirada. |

# 6. G18: bilhetes, comunicação na saída e conhecimento em papel

## 6.1 O que o texto pede e o que o dicionário já tinha

O bilhete de passagem rodoviário, aquaviário, de bagagem e ferroviário (modelos 13 a 16) é consolidado em D300 (por série e faixa) e, quando reunido num resumo de movimento diário (modelo 18, D400), em D410. A catraca não emite bilhete individual: usa a série 9999 e informa a quantidade de passageiros do dia na faixa final. Por isso a consolidação **é guardada**, e, se cada bilhete for nota de saída, o D300 sai por derivação e a linha não se cria.

| Registro | O que é | Onde fica |
|---|---|---|
| D160, D161, D162 | Conhecimento de transporte em papel: despacho, carga e documentos transportados | Campos novos em `Mov_Cte` e `Mov_Cte_Documento_Transportado` (seção 8) |
| D300, D301, D310, D410, D411, D420 | Bilhetes consolidados, cancelados e município | `Mov_Bilhete_Passagem_Consolidado`, `_Cancelado` e `_Municipio` (novas) |
| D350 a D390 | ECF de bilhete: equipamento, Redução Z, totalizador e analítico | Equipamento e Redução Z já existem; D365 em `Mov_Ecf_Reducao_Z_Totalizador`, D370 em `Mov_Bilhete_Passagem_Municipio`, D390 em `Mov_Ecf_Reducao_Z_Analitico` |
| D400 | Resumo de movimento diário (modelo 18) | `Mov_Nota_Fiscal_Saida` com `ID_Participante_Agencia` (seção 8) |
| D500, D510, D530 | Comunicação e telecomunicação na saída (modelos 21 e 22) | Tipo de assinante na nota e receita de terceiros no item (seção 8); `Mov_Nota_Fiscal_Saida_Terminal_Faturado` (nova) |
| D695, D696, D697 | Convênio 115/03 em comunicação | Seção 4 (`Mov_Convenio115_Consolidacao` e filhas) |

## 6.2 Entidade nova: `Mov_Bilhete_Passagem_Consolidado`

Os bilhetes de passagem (rodoviário 13, aquaviário 14, bagagem 15 e ferroviário 16) **consolidados** por série, faixa, CST, CFOP e alíquota (D300 e D410). Existe porque a catraca não emite bilhete individual (série 9999, a quantidade do dia na faixa final) e porque o resumo pode vir importado; se cada bilhete for nota de saída, o D300 sai por derivação e esta linha não se cria. Com `ID_Nota_Rmd` preenchido é o D410; sem, o D300. Habilitação `efd_bilhete_passagem`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 23.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Bilhete_Passagem_Consolidado` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento. |
| `ID_Nota_Rmd` | referência (Mov_Nota_Fiscal_Saida), opcional | O RMD (modelo 18, D400) que reúne esta linha. Preenchido = D410; vazio = D300. O bilhete do D400 não pode aparecer no D300. |
| `ID_Modelo_Documento` | referência (Cad_Modelo_Documento_Fiscal) | COD_MOD: 13, 14, 15 ou 16. |
| `Serie` | código (até 4) | SER; "9999" quando a catraca conta os passageiros. |
| `Subserie` | código (até 3), opcional | SUB. |
| `Numero_Inicial` | número | NUM_DOC_INI; zero na catraca. |
| `Numero_Final` | número | NUM_DOC_FIN; na catraca, a quantidade diária de passageiros. |
| `Data_Emissao` | data | DT_DOC; no D410 igual à do RMD. |
| `ID_Cst` | referência (Cad_Cst) | CST_ICMS. |
| `ID_CFOP` | referência (Cad_CFOP) | CFOP. |
| `Aliquota_Icms` | número, opcional | ALIQ_ICMS. |
| `Valor_Operacao` | número | VL_OPR. |
| `Valor_Desconto` | número, opcional | VL_DESC. |
| `Valor_Servico` | número | VL_SERV. |
| `Valor_Seguro` | número, opcional | VL_SEG (só no D300). |
| `Valor_Outras_Despesas` | número, opcional | VL_OUT_DESP (só no D300). |
| `Base_Calculo_Icms` | número, opcional | VL_BC_ICMS. |
| `Valor_Icms` | número, opcional | VL_ICMS. |
| `Valor_Reducao_Base_Calculo` | número, opcional | VL_RED_BC (só no D300). |
| `ID_Observacao_Lancamento` | referência (Cad_Observacao_Lancamento_Fiscal), opcional | COD_OBS (só no D300). |
| `ID_Conta_Contabil` | referência (Cad_Conta_Contabil), opcional | COD_CTA (só no D300). |
| `Origem_Dado` | enumeração {catraca, resumo_importado, lancamento_manual} | De onde veio a linha. |

## 6.3 Entidade nova: `Mov_Bilhete_Passagem_Cancelado`

Os bilhetes cancelados da linha consolidada (D301 e D411).

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 3.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Bilhete_Passagem_Cancelado` | identificador | --- |
| `ID_Bilhete_Passagem_Consolidado` | referência (Mov_Bilhete_Passagem_Consolidado) | A linha consolidada. |
| `Numero_Documento_Cancelado` | número | NUM_DOC_CANC. |

## 6.4 Entidade nova: `Mov_Bilhete_Passagem_Municipio`

O complemento por município de origem do serviço (D310, D370 e D420). Pertence a uma linha consolidada (D310 e D420) **ou** a uma Redução Z do ECF de bilhete modelo 2E (D370): exatamente um dos dois pais.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 8.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Bilhete_Passagem_Municipio` | identificador | --- |
| `ID_Bilhete_Passagem_Consolidado` | referência (Mov_Bilhete_Passagem_Consolidado), opcional | O pai no D300 ou no D410. |
| `ID_Reducao_Z` | referência (Mov_Ecf_Reducao_Z), opcional | O pai no ECF de bilhete (D370). |
| `ID_Municipio_Origem` | referência (Cad_Municipio) --- identidade | COD_MUN_ORIG. |
| `Valor_Servico` | número | VL_SERV. |
| `Quantidade_Bilhetes` | número, opcional | QTD_BILH: só no D370. |
| `Base_Calculo_Icms` | número, opcional | VL_BC_ICMS. |
| `Valor_Icms` | número, opcional | VL_ICMS. |

## 6.5 Entidade nova: `Mov_Nota_Fiscal_Saida_Terminal_Faturado`

O terminal faturado das notas de comunicação (21) e telecomunicação (22) de saída (registro D530). Hoje o terminal existe só no pacote da NFCom (`Cad_Nfcom_Assinante`). Habilitação `efd_comunicacao_saida`.

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 8.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Saida_Terminal_Faturado` | identificador | --- |
| `ID_Nota` | referência (Mov_Nota_Fiscal_Saida) | A nota de saída (modelos 21 e 22). |
| `ID_Tipo_Servico_Terminal` | referência (Cad_Classe_Sistema, domínio = tipo_servico_terminal_efd) | IND_SERV: telefonia, comunicação de dados, TV por assinatura, acesso à Internet, multimídia e outros (0 a 4 e 9). Não casa um a um com o `tpServUtil` da NFCom. |
| `Data_Inicio_Servico` | data, opcional | DT_INI_SERV. |
| `Data_Fim_Servico` | data, opcional | DT_FIN_SERV. |
| `Periodo_Fiscal` | competência | PER_FISCAL (MMAAAA, 6 posições). |
| `Codigo_Area` | código (até 4), opcional | COD_AREA: código de área do terminal. |
| `Numero_Terminal` | código (até 12), opcional | TERMINAL. |

**BP-e (modelo 63).** O Guia só pede o D100 com campos reduzidos (sem `COD_PART`, `SUB` e `IND_FRT`). Não verifiquei se `Mov_Cte` aceita o modelo 63; pergunto à equipe (Q175-E2).

# 7. G19: cadastros

Só alterações (seção 8): `Codigo_Barras` na conversão de unidade (0220, `COD_BARRA`), e `Texto_Complementar` e `ID_Conta_Contabil` no item do inventário (H010). O total do H005 por filial é a soma dos itens do inventário e **não se grava**.

# 8. Mudanças em entidades existentes

11 entidades mudam, com **30 campos novos**. As demais mudanças são valores de domínio e textos.

| Entidade | Registros | O que muda |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item_Exportacao` | 1105, 1110 | 3 campos novos |
| `Mov_Credito_Fiscal` | 1200 | 1 campo novo; valor novo `transferencia_icms_recebida` em `Origem` (CRED_RECEB); texto de `ID_Participante_Cedente` passa a cobrir a transferência entre estabelecimentos e a terceiros |
| `Mov_Credito_Fiscal_Aplicacao` | 1210 | 3 campos novos |
| `Mov_Nota_Fiscal_Saida_Item` | 1510, D510, C470, C173, C178 | 6 campos novos |
| `Mov_Nota_Fiscal_Entrada_Item` | C173 | 2 campos novos |
| `Mov_Nota_Fiscal_Saida` | C460, C465, D310, D400, D410, D500 | 6 campos novos |
| `Mov_Cte` | D160, D161 | 4 campos novos |
| `Mov_Cte_Documento_Transportado` | D162 | 2 campos novos; texto de `Peso_Kg` passa a dizer que vale também como PESO_BRT do D162 |
| `Cad_Produto_Servico_Conversao_Unidade` | 0220 | 1 campo novo |
| `Mov_Inventario_Item` | H010 | 2 campos novos |
| `Cad_Utilidade_Classificacao_Efd` | C500 (cClass) | a identidade passa a ser documento, grupo **e** campo de destino (o grupo 085 e o 087 alimentam cinco campos do C500); nenhum campo novo |

**`Mov_Nota_Fiscal_Saida_Item_Exportacao`** (3 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `ID_Exportacao_Declaracao` | referência (Mov_Exportacao_Declaracao), opcional | A declaração (1100) a que o item pertence. É o que liga a nota ao 1100 e dá o 1105 por derivação. |
| `ID_Nota_Fiscal_Entrada` | referência (Mov_Nota_Fiscal_Entrada), opcional | Na exportação indireta, a nota recebida com fim específico de exportação (1110): cobre as notas sem chave (modelos 01, 1B e 04), em que a `Chave_Nota_Exportacao` não existe. |
| `Numero_Memorando_Exportacao` | código (até 20), opcional | NR_MEMO do 1110. |

**`Mov_Credito_Fiscal`** (1 campo novo; valor novo `transferencia_icms_recebida` em `Origem` (CRED_RECEB); texto de `ID_Participante_Cedente` passa a cobrir a transferência entre estabelecimentos e a terceiros)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_Codigo_Ajuste` | referência (Cad_Icms_Codigo_Ajuste), opcional | COD_AJ_APUR do 1200: o código da tabela 5.1.1 que identifica o crédito controlado fora da apuração (natureza `controle_extra_apuracao`). Obrigatório quando `ID_Imposto` é ICMS e o estabelecimento escritura o 1200. |

**`Mov_Credito_Fiscal_Aplicacao`** (3 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `ID_Efd_Codigo_Estadual_Tipo_Utilizacao` | referência (Cad_Efd_Codigo_Estadual), opcional | TIPO_UTIL do 1210: o tipo de utilização da tabela 5.5 (`tp_util_cred_fiscais`: UF01 dedução, UF21 compensação, UF41 transferência, UF61 restituição, UF81 estorno, UF99 outros e os da UF). |
| `Numero_Documento_Baixa` | código (até 60), opcional | NR_DOC: número do documento usado na baixa do crédito. |
| `Chave_Documento_Eletronico` | código (44), opcional | CHV_DOCe: chave da NF-e, do CT-e ou do CT-e OS usada na baixa. |

**`Mov_Nota_Fiscal_Saida_Item`** (6 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Indicador_Receita_Energia` | enumeração {propria, terceiros}, opcional | IND_REC do 1510 (energia, saída interestadual): 0 receita própria e 1 de terceiros. Domínio próprio: o `ID_Tipo_Receita_Comunicacao` é do D600 e tem sete valores. |
| `ID_Participante_Receita_Terceiro` | referência (Cad_Participante), opcional | COD_PART do 1510 e do D510: o terceiro que recebe a receita. Obrigatório quando a receita é de terceiros. |
| `Quantidade_Cancelada` | número, opcional | QTD_CANC do C470: quantidade cancelada no cupom emitido por ECF. |
| `Medicamento_Indicador_Base_Calculo` | enumeração {preco, margem_valor, lista_negativa, lista_positiva, lista_neutra}, opcional | IND_MED do C173: o tipo de referência da base do ICMS (0 a 4). |
| `Medicamento_Tipo_Produto` | enumeração {similar, generico, etico_ou_marca}, opcional | TP_PROD do C173 (0 a 2). |
| `ID_Classe_Enquadramento_Ipi` | referência (Cad_Classe_Sistema, domínio = classe_enquadramento_ipi), opcional | CL_ENQ do C178: a classe de enquadramento do IPI (5 posições; 31 linhas do documento 172). **Não é** o `ID_Enquadramento_Ipi` (cEnq, 3 dígitos). |

**`Mov_Nota_Fiscal_Entrada_Item`** (2 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Medicamento_Indicador_Base_Calculo` | enumeração {preco, margem_valor, lista_negativa, lista_positiva, lista_neutra}, opcional | IND_MED do C173 na entrada (NF-e de terceiros). |
| `Medicamento_Tipo_Produto` | enumeração {similar, generico, etico_ou_marca}, opcional | TP_PROD do C173 na entrada. |

**`Mov_Nota_Fiscal_Saida`** (6 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Numero_Contador_Cupom_Fiscal` | número, opcional | NUM_CCF do C465: contador de cupom fiscal do CF-e-ECF (modelo 60). |
| `ID_Reducao_Z` | referência (Mov_Ecf_Reducao_Z), opcional | A Redução Z do dia a que o cupom emitido por ECF pertence (C460 filho do C405). Preenchido só nos modelos 02, 2D e 60. |
| `ID_Tipo_Assinante` | referência (Cad_Classe_Sistema, domínio = tipo_assinante_comunicacao_efd), opcional | TP_ASSINANTE do D500 (nota 21 e 22 de saída): comercial/industrial, poder público, residencial, público, semi-público e outros. Não é o `tipo_assinante_nfcom`. |
| `ID_Municipio_Origem_Servico` | referência (Cad_Municipio), opcional | COD_MUN_ORIG do bilhete de passagem (modelos 13 a 16), para o D310 e o D420 quando o bilhete é nota. |
| `ID_Participante_Agencia` | referência (Cad_Participante), opcional | COD_PART do D400: a agência, filial ou posto do resumo de movimento diário (modelo 18). A nota só tinha o cliente. |
| `ID_Nota_Rmd` | referência (Mov_Nota_Fiscal_Saida), opcional | O RMD (modelo 18) que reúne o bilhete (D410). O bilhete do D400 não pode repetir no D300. |

**`Mov_Cte`** (4 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Numero_Despacho` | código (até 30), opcional | DESPACHO do D160: número do despacho, nos conhecimentos em papel (modelos 08 e 8B). |
| `ID_Tipo_Transporte_Carga` | referência (Cad_Classe_Sistema, domínio = tipo_transporte_carga_efd), opcional | IND_CARGA do D161: rodoviário, ferroviário, rodo-ferroviário, aquaviário, dutoviário, aéreo e outros (0 a 5 e 9). Não casa com o `Modal` do CT-e, que não tem "rodo-ferroviário". |
| `ID_Municipio_Coleta` | referência (Cad_Municipio), opcional | COD_MUN_COL do D161 (9999999 no exterior). |
| `ID_Municipio_Entrega` | referência (Cad_Municipio), opcional | COD_MUN_ENTG do D161 (9999999 no exterior). |

**`Mov_Cte_Documento_Transportado`** (2 campos novos; texto de `Peso_Kg` passa a dizer que vale também como PESO_BRT do D162)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Quantidade_Volumes` | número, opcional | QTD_VOL do D162: obrigatório no conhecimento em papel. |
| `Peso_Liquido_Kg` | número, opcional | PESO_LIQ do D162, em quilogramas. |

**`Cad_Produto_Servico_Conversao_Unidade`** (1 campo novo)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Codigo_Barras` | código (até 14), opcional | COD_BARRA do 0220: o código de barras da unidade convertida (a conversão não tinha GTIN próprio). |

**`Mov_Inventario_Item`** (2 campos novos)

| Campo novo | Tipo | Descrição |
|---|---|---|
| `Texto_Complementar` | texto, opcional | TXT_COMPL do H010. |
| `ID_Conta_Contabil` | referência (Cad_Conta_Contabil), opcional | COD_CTA do H010: a conta contábil do item. Sem o campo o dado só se deduzia do lançamento do fechamento de estoque. |

# 9. Tabelas oficiais: o que se carrega (Q167-5) e correções ao documento 172

## 9.1 Tabela 4.4.6 (totalizadores parciais da Redução Z)

Você aprovou carregar as tabelas oficiais que faltam. A 4.4.6 está **no Guia, no fim** (subseção 1.6), e cada linha é um **padrão de código**, não um código fixo: `Tnnnn` (ICMS tributado, "nnnn" é a carga com duas casas), `xxTnnnn` (o mesmo com número de totalizador de 01 a 30), `Snnnn` e `xxSnnnn` (ISSQN), `Fn`, `In`, `Nn` (substituição, isento e não incidência do ICMS), `FSn`, `ISn`, `NSn` (os mesmos do ISSQN), `OPNF`, `DT`, `DS`, `DO`, `AT`, `AS`, `AO`, `Can-T`, `Can-S`, `Can-O` e `IOF`. São **21 padrões**, com vigência desde 01/01/2009. Carrega em `Cad_Efd_Codigo_Estadual` com o domínio `tot_parc_redz`, **sem UF** (vale para todos). O catálogo do documento 172 passa de **1.226 para 1.247 linhas**. O Motor confere o código digitado contra o padrão e **avisa** quando não confere (por exemplo, `T1800` com alíquota 12% no C490).

## 9.2 Mapa de cClass da NF3e para o C500

O Guia diz, campo a campo, de que grupos de cClass cada valor do C500 é a soma. Isso vira o conteúdo de `Cad_Utilidade_Classificacao_Efd` (documento 168), com **23 linhas** (campo e grupo) para **15 grupos** de cClass:

| Campo da EFD | Grupos de cClass | Natureza |
|---|---|---|
| `VL_FORN` (fornecimento) | 060, 061, 062, 063, 064, 065, 085, 087 | soma |
| `VL_SERV_NT` (servico nao tributado) | 070, 084, 085, 087 | soma |
| `VL_TERC` (terceiros) | 080, 081, 085, 086, 087 | soma |
| `ENER_INJET` (energia injetada) | 560, 085, 087 | dedução (subtrai do total) |
| `OUTRAS_DED` (outras deducoes) | 590, 085, 087 | dedução (subtrai do total) |

**Correção ao documento 168.** A identidade da entidade passa a ser **documento + grupo + campo de destino**; antes era só documento e grupo, e os grupos 085 e 087 alimentam todos os cinco campos. Nenhum campo novo. **A tabela de cClass em si (os códigos de item) não está nos arquivos do Project**; só o mapa de grupos vem do Guia. **Na NFGás não há fonte** para o cClass: o Guia só diz, em texto, que `VL_FORN` é o consumo de gás e o serviço de distribuição, `VL_SERV_NT` o que está fora do campo do ICMS, `VL_TERC` o cobrado em nome de terceiros e `OUTRAS_DED` os itens do grupo deduções. A carga da NFGás fica **vazia**, com aviso do Motor (Q175-9).

## 9.3 Domínios novos e demais cargas

| Carga | Linhas | Fonte |
|---|---|---|
| `Cad_Efd_Codigo_Estadual`, domínio `tot_parc_redz` | 21 | Guia, subseção 1.6 |
| `Cad_Efd_Giaf_Campo` | 36 | Guia, registros 1960 a 1980 |
| `Cad_Utilidade_Classificacao_Efd` (NF3e) | 23 | Guia, C500, campos 15, 16, 17, 39 e 40 |
| `Cad_Classe_Sistema`, 5 domínios novos | 47 | Guia (registros 1100, 1700, D161, D500 e D530) |
| `Cad_Classe_Sistema`, valores de `modulo_fiscal_opcional` | 13 | Seção 10 |

Tudo com `Situacao_Dado = provisorio`. Como você decidiu em Q172-C1, **a origem da linha é só o Guia** (campo `Tabela_Origem`); nenhuma outra fonte é consultada por ora.

## 9.4 Correção ao documento 172: a "tabela 5.1.2"

Pelo que você disse e pelo que li no documento 43, a **Tabela 5.1.2 é o detalhamento da CPRB**, do P110, da EFD-Contribuições. O Guia da EFD-ICMS/IPI não tem Bloco P nem essa tabela. No documento 172, a seção 5.2 e o título de `Cad_Icms_Beneficio_Ajuste_Codigo` dizem "5.1.2": **é erro de rótulo**. A entidade, os campos e a carga (3.376 linhas) **não mudam**; só o texto passa a dizer "catálogo de ajustes de benefício do validador (`AJ_BENEF_INCENTIVO`), sem número no Guia v3.2.4". A pergunta Q172-C3 do documento 38 ("onde se informa o código da tabela 5.1.2") fica **respondida pelo seu esclarecimento** para a tabela da CPRB e é reescrita para o catálogo do validador (Q175-7).

# 10. Habilitação por empresa e domínios novos

## 10.1 Habilitação por empresa (`modulo_fiscal_opcional`)

Valores novos de `Cad_Empresa_Modulo_Opcional`, como você aprovou em 05/10. **Nenhum vem habilitado.** A empresa liga cada um, com a vigência.

| Valor | Registros que a habilitação libera | Lacuna |
|---|---|---|
| `efd_exportacao_1100` | 1100, 1105 e 1110 (exportação) | G15 |
| `efd_credito_icms_1200` | 1200 e 1210 (controle de créditos de ICMS) | G15 |
| `efd_valor_agregado_1400` | 1400 (valores agregados, IPM) | G15 |
| `efd_energia_1500` | 1500 e 1510 (energia, saída interestadual) | G15 |
| `efd_documento_utilizado_1700` | 1700 e 1710 (documentos em papel) | G15 |
| `efd_dcta_1800` | 1800 (DCTA, transporte aéreo) | G15 |
| `efd_giaf_pe` | 1960, 1970, 1975 e 1980 (GIAF de Pernambuco) | G15 |
| `efd_cupom_ecf` | C400 a C490 e D350 a D390 (ECF) | G16 |
| `efd_convenio_115` | C700, C790, C791 e D695 a D697 | G16 |
| `efd_sat_resumo_obs` | C895 e C897 (observação do resumo do SAT) | G16 |
| `efd_combustivel_c165` | C165 e C171 (combustíveis, nota) | G17 |
| `efd_bilhete_passagem` | D300 a D420 (bilhetes e RMD) | G18 |
| `efd_comunicacao_saida` | D500, D510 e D530 de saída (modelos 21 e 22) | G18 |

## 10.2 Domínios novos em `Cad_Classe_Sistema`

**`tipo_conhecimento_embarque`** (TP_CHC do 1100, 22 valores): 01 AWB; 02 MAWB; 03 HAWB; 04 COMAT; 06 R. EXPRESSAS; 07 ETIQ. REXPRESSAS; 08 HR. EXPRESSAS; 09 AV7; 10 BL; 11 MBL; 12 HBL; 13 CRT; 14 DSIC; 16 COMAT BL; 17 RWB; 18 HRWB; 19 TIF/DTA; 20 CP2; 91 NÃO IATA; 92 MNAO IATA; 93 HNAO IATA; 99 OUTROS.

**`tipo_dispositivo_documento_fiscal`** (COD_DISP do 1700, 6 valores): 00 Formulário de segurança, impressor autônomo; 01 FS-DA, formulário de segurança para impressão de DANFE; 02 Formulário de segurança, NF-e; 03 Formulário contínuo; 04 Blocos; 05 Jogos soltos.

**`tipo_transporte_carga_efd`** (IND_CARGA do D161, 7 valores): 0 Rodoviário; 1 Ferroviário; 2 Rodo-ferroviário; 3 Aquaviário; 4 Dutoviário; 5 Aéreo; 9 Outros.

**`tipo_assinante_comunicacao_efd`** (TP_ASSINANTE do D500, 6 valores): 1 Comercial/industrial; 2 Poder público; 3 Residencial/pessoa física; 4 Público; 5 Semi-público; 6 Outros.

**`tipo_servico_terminal_efd`** (IND_SERV do D530, 6 valores): 0 Telefonia; 1 Comunicação de dados; 2 TV por assinatura; 3 Provimento de acesso à Internet; 4 Multimídia; 9 Outros.

# 11. O que entra no próximo "consolidar"

**28 entidades novas (235 campos)**, todas na Contabilidade & Fiscal.

| Entidade | Lacuna | Campos | Mestre | Vigência | Seção |
|---|---|---|---|---|---|
| `Mov_Exportacao_Declaracao` | G15 | 15 | não | não | 3.2 |
| `Mov_Valor_Agregado_Municipio` | G15 | 8 | não | não | 3.3 |
| `Mov_Documento_Dispositivo_Utilizado` | G15 | 9 | não | não | 3.4 |
| `Mov_Documento_Dispositivo_Cancelado` | G15 | 4 | não | não | 3.5 |
| `Mov_Dcta_Apuracao` | G15 | 8 | não | não | 3.6 |
| `Cad_Efd_Giaf_Campo` | G15 | 13 | sim | sim | 3.7 |
| `Mov_Efd_Giaf_Apuracao` | G15 | 5 | não | não | 3.8 |
| `Mov_Efd_Giaf_Valor` | G15 | 5 | não | não | 3.9 |
| `Mov_Ecf_Reducao_Z_Totalizador` | G16 | 7 | não | não | 4.2 |
| `Mov_Ecf_Reducao_Z_Totalizador_Item` | G16 | 6 | não | não | 4.3 |
| `Mov_Ecf_Reducao_Z_Analitico` | G16 | 12 | não | não | 4.4 |
| `Mov_Convenio115_Consolidacao` | G16 | 11 | não | não | 4.5 |
| `Mov_Convenio115_Consolidacao_Analitico` | G16 | 14 | não | não | 4.6 |
| `Mov_Convenio115_Consolidacao_Uf` | G16 | 7 | não | não | 4.7 |
| `Mov_Sat_Resumo_Observacao` | G16 | 8 | não | não | 4.8 |
| `Mov_Sat_Resumo_Ajuste` | G16 | 10 | não | não | 4.9 |
| `Mov_Nota_Fiscal_Documento_Arrecadacao` | G17 | 11 | não | não | 5.2 |
| `Mov_Nota_Fiscal_Fatura_Comercial` | G17 | 6 | não | não | 5.3 |
| `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms` | G17 | 7 | não | não | 5.4 |
| `Mov_Nota_Fiscal_Saida_Combustivel_Transporte` | G17 | 6 | não | não | 5.5 |
| `Mov_Nota_Fiscal_Entrada_Item_Tanque` | G17 | 4 | não | não | 5.6 |
| `Mov_Nota_Fiscal_Entrada_Item_Lote` | G17 | 4 | não | não | 5.7 |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao` | G17 | 7 | não | não | 5.8 |
| `Mov_Nota_Fiscal_Icms_St_Uf_Recolhimento` | G17 | 6 | não | não | 5.9 |
| `Mov_Bilhete_Passagem_Consolidado` | G18 | 23 | não | não | 6.2 |
| `Mov_Bilhete_Passagem_Cancelado` | G18 | 3 | não | não | 6.3 |
| `Mov_Bilhete_Passagem_Municipio` | G18 | 8 | não | não | 6.4 |
| `Mov_Nota_Fiscal_Saida_Terminal_Faturado` | G18 | 8 | não | não | 6.5 |

**11 entidades alteradas** (30 campos novos), na seção 8. **5 domínios novos** (47 valores) e **13 valores de habilitação**, na seção 10. **Cargas provisórias:** 21 padrões da 4.4.6, 36 campos de GIAF, 23 linhas do mapa de cClass da NF3e.

**Textos que a consolidação corrige:** o "5.1.2" do documento 172 (seção 9.4); a identidade de `Cad_Utilidade_Classificacao_Efd` (documento 168); o C591 do documento 167, que sai por derivação; o texto de `ID_Participante_Cedente` em `Mov_Credito_Fiscal` e o de `Peso_Kg` em `Mov_Cte_Documento_Transportado`; e a contagem do catálogo do documento 172 (1.226 para 1.247).

# 12. Perguntas

## 12.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q175-1** | G15 sem o Bloco 1 de combustíveis: as 8 entidades novas (exportação, valores agregados, documentos em papel, DCTA e GIAF) e as alterações dos créditos e do item de exportação, como nas seções 3 e 8? | Sim |
| **Q175-2** | G16: totalizador, item e analítico da Redução Z (a nota 02 individual continua derivada), consolidação do Convênio 115 e resumo do SAT, como na seção 4? | Sim |
| **Q175-3** | G17: C105, C112, C130, C140, C165, C171, C173, C178 e C179, como na seção 5? O C165 e o C171 ficam sob a habilitação `efd_combustivel_c165`, **sem** o Bloco 1 de combustíveis. | Sim |
| **Q175-4** | G18: bilhete consolidado (que não se cria se cada bilhete for nota), terminal faturado e campos do conhecimento em papel, como na seção 6? | Sim |
| **Q175-5** | G19: `Codigo_Barras` no 0220 e `Texto_Complementar` e `ID_Conta_Contabil` no H010; o H005 fica derivado? | Sim |
| **Q175-6** | Habilitação por empresa: os 13 valores novos de `modulo_fiscal_opcional` (seção 10), **nenhum ligado por padrão**? | Sim |
| **Q175-7** | A tabela 5.1.2 é a do detalhamento da CPRB (P110), da EFD-Contribuições, e o "5.1.2" do documento 172 é só erro de rótulo do catálogo `AJ_BENEF_INCENTIVO` (sem número no Guia)? Corrijo só o texto? | Sim |
| **Q175-8** | A tabela 4.4.6 (21 padrões) entra em `Cad_Efd_Codigo_Estadual` com o domínio `tot_parc_redz`, sem UF, e o catálogo vai a 1.247 linhas? | Sim |
| **Q175-9** | `Cad_Utilidade_Classificacao_Efd`: identidade com o campo de destino, carga só da NF3e (23 linhas) e NFGás **vazia**, com aviso do Motor? Você tem a tabela de cClass da NFGás? | Sim; se tiver a tabela, mande |

## 12.2 Para o contador

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q175-C1** | Registro 1400: qual é a regra de cada UF (de que CFOP e produto vem o valor, e se o município é o da origem ou o do destino)? O Guia só traz a tabela de itens. | Informado, não calculado; o campo `Origem_Valor` reserva o cálculo. |
| **Q175-C2** | COD_OBS no nível analítico (C190, C320, C390, C590, C790, C850, C890, D190 e os de bilhete e Redução Z): uma observação por combinação de CST, CFOP e alíquota, ou uma por documento? | Por combinação, como o Guia; a nota guarda as observações e o Motor as distribui. |
| **Q175-C3** | DCTA (1800): a diferença apurada (`VL_DIF`) vira o estorno de crédito (E111) da apuração, e o ERP só guarda as quatro entradas? | Sim; o Motor calcula. |
| **Q175-C4** | C112 e C130: o valor é o do documento, sem recálculo (IRRF e previdência destacados na nota)? O C112 liga-se à guia do módulo de obrigações quando ela existe? | Sim, "tal como emitido". |
| **Q175-C5** | C105: o Motor copia a UF do recolhimento do ICMS ST (UF de consumo do item, ou local de retirada) e só no leasing ela é digitada? | Sim. |
| **Q175-C6** | 1200: o código da tabela 5.1.1 é obrigatório em todo crédito controlado fora da apuração, e `CRED_RECEB` é a origem "transferência recebida"? | Sim, com aviso. |
| **Q175-C7** | GIAF de Pernambuco: a GIAF 1, 3 e 4 se preenche só com valores informados (o Guia não traz fórmula)? Existe regra no Manual da Sefaz-PE? | Informado, sem fórmula. |
| **Q175-C8** | Tabela 4.4.6: o Motor deve avisar quando o código do C420 não casa com o padrão e a alíquota do C490? | Sim, só aviso. |

## 12.3 Para a equipe

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q175-E1** | A Mlegate (ou algum cliente) recebe nota modelo 02 **só consolidada**, sem as notas individuais? Se sim, criamos uma consolidação como a do Convênio 115. | Não há caso conhecido; fica sem estrutura. |
| **Q175-E2** | `Mov_Cte` aceita o BP-e (modelo 63), sem `COD_PART`, `SUB` e `IND_FRT`? | A verificar. |
| **Q175-E3** | Consequência de Q172-C1 ("só o Guia"): as linhas dos catálogos do validador que o Guia não traz ficam com `Tabela_Origem` do validador. Está correto manter assim? | Sim. |
| **Q175-E4** | O tanque (C171) fica como código até o Bloco 1 de combustíveis ser desenhado; depois vira referência. Aceito? | Sim. |

# 13. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **O Bloco 1 de combustíveis e usina (1300 a 1391) está fora** (Q167-6). O C165, o C171 e a habilitação `efd_combustivel_c165` entram sem ele.
3. **A regra do registro 1400 por UF não está no Guia.** O valor é informado.
4. **A tabela de cClass da NF3e e qualquer cClass da NFGás não estão nos arquivos.** O mapa de grupos vem do Guia, e a NFGás fica sem carga.
5. **A GIAF não tem fórmulas no Guia.** Os 36 campos entram como catálogo, e os valores são informados.
6. **Não verifiquei** se `Mov_Cte` aceita o BP-e, nem a existência de nota 02 só consolidada (Q175-E1 e E2).
7. **As leituras minhas** (COD_OBS por combinação, `VL_DIF` como estorno, cópia da UF no C105) vão ao contador; nenhuma vira regra no código.

# Anexo A. Cargas provisórias (todas com `Situacao_Dado = provisorio`)

## A.1 `Cad_Efd_Giaf_Campo`: 36 linhas

| Modelo | Registro | Campo | Descrição | Tipo |
|---|---|---|---|---|
| `giaf_1_industria` | 1960 | `G1_01` | Percentual de crédito presumido | percentual |
| `giaf_1_industria` | 1960 | `G1_02` | Saídas não incentivadas de PI | valor |
| `giaf_1_industria` | 1960 | `G1_03` | Saídas incentivadas de PI | valor |
| `giaf_1_industria` | 1960 | `G1_04` | Saídas incentivadas de PI para fora do Nordeste | valor |
| `giaf_1_industria` | 1960 | `G1_05` | Saldo devedor do ICMS antes das deduções do incentivo | valor |
| `giaf_1_industria` | 1960 | `G1_06` | Saldo devedor do ICMS relativo à faixa incentivada de PI | valor |
| `giaf_1_industria` | 1960 | `G1_07` | Crédito presumido nas saídas incentivadas de PI para fora do Nordeste | valor |
| `giaf_1_industria` | 1960 | `G1_08` | Saldo devedor relativo à faixa incentivada de PI após o crédito presumido nas saídas para fora do Nordeste | valor |
| `giaf_1_industria` | 1960 | `G1_09` | Crédito presumido | valor |
| `giaf_1_industria` | 1960 | `G1_10` | Dedução de incentivo da Indústria (crédito presumido) | valor |
| `giaf_1_industria` | 1960 | `G1_11` | Saldo devedor do ICMS após deduções | valor |
| `giaf_3_importacao` | 1970 | `G3_01` | Importações com ICMS diferido | valor |
| `giaf_3_importacao` | 1970 | `G3_02` | ICMS diferido nas importações | valor |
| `giaf_3_importacao` | 1970 | `G3_03` | Saídas não incentivadas de PI | valor |
| `giaf_3_importacao` | 1970 | `G3_04` | Percentual de incentivo nas saídas para fora do Estado | percentual |
| `giaf_3_importacao` | 1970 | `G3_05` | Saídas incentivadas de PI para fora do Estado | valor |
| `giaf_3_importacao` | 1970 | `G3_06` | ICMS das saídas incentivadas de PI para fora do Estado | valor |
| `giaf_3_importacao` | 1970 | `G3_07` | Crédito presumido nas saídas para fora do Estado | valor |
| `giaf_3_importacao` | 1970 | `G3_T` | Dedução de incentivo da Importação (crédito presumido) | valor |
| `giaf_3_importacao` | 1970 | `G3_08` | Saldo devedor do ICMS antes das deduções do incentivo | valor |
| `giaf_3_importacao` | 1970 | `G3_09` | Saldo devedor do ICMS após deduções do incentivo | valor |
| `giaf_3_importacao` | 1975 | `G3_10` | Saídas incentivadas de PI | valor |
| `giaf_3_importacao` | 1975 | `G3_11` | Importações-base para o crédito presumido | valor |
| `giaf_3_importacao` | 1975 | `G3_12` | Crédito presumido nas saídas internas | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_01` | Entradas (percentual de incentivo) | percentual |
| `giaf_4_central_distribuicao` | 1980 | `G4_02` | Entradas não incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_03` | Entradas incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_04` | Saídas (percentual de incentivo) | percentual |
| `giaf_4_central_distribuicao` | 1980 | `G4_05` | Saídas não incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_06` | Saídas incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_07` | Saldo devedor do ICMS antes das deduções do incentivo (PI e itens não incentivados) | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_08` | Crédito presumido nas entradas incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_09` | Crédito presumido nas saídas incentivadas de PI | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_10` | Dedução de incentivo da Central de Distribuição (entradas/saídas) | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_11` | Saldo devedor do ICMS após deduções do incentivo | valor |
| `giaf_4_central_distribuicao` | 1980 | `G4_12` | Índice de recolhimento da central de distribuição | valor |

## A.2 Padrões da tabela 4.4.6: 21 linhas

| Padrão | Nome | Conteúdo |
|---|---|---|
| `Tnnnn` | Tributado ICMS | Carga tributária efetiva em duas casas (T1800 = 18,00%) |
| `xxTnnnn` | Tributado ICMS | xx = nº do totalizador, 01 a 30 (02T1800) |
| `Snnnn` | Tributado ISSQN | Carga efetiva (S0500 = 5,00%) |
| `xxSnnnn` | Tributado ISSQN | xx = nº do totalizador, 01 a 30 |
| `Fn` | Substituição tributária, ICMS | n = nº do totalizador |
| `In` | Isento, ICMS | n = nº do totalizador |
| `Nn` | Não incidência, ICMS | n = nº do totalizador |
| `FSn` | Substituição tributária, ISSQN | n = nº do totalizador |
| `ISn` | Isento, ISSQN | n = nº do totalizador |
| `NSn` | Não incidência, ISSQN | n = nº do totalizador |
| `OPNF` | Operações não fiscais | Soma dos totalizadores de operações não fiscais |
| `DT` | Desconto, ICMS |  |
| `DS` | Desconto, ISSQN |  |
| `DO` | Desconto, operações não fiscais |  |
| `AT` | Acréscimo, ICMS |  |
| `AS` | Acréscimo, ISSQN |  |
| `AO` | Acréscimo, operações não fiscais |  |
| `Can-T` | Cancelamento, ICMS |  |
| `Can-S` | Cancelamento, ISSQN |  |
| `Can-O` | Cancelamento, operações não fiscais |  |
| `IOF` | Imposto sobre operações financeiras | Acrescido ao valor das operações |

## A.3 Mapa de cClass da NF3e: 23 linhas

Está na tabela da seção 9.2 (campo da EFD, grupos e natureza); cada par campo e grupo é uma linha.

# Anexo B. Cobertura registro por registro

| Registro | Situação | Onde fica |
|---|---|---|
| 1010 | Derivado | Os indicadores saem da existência dos registros; só a habilitação por empresa decide se o ERP os gera |
| 1100 | Novo | `Mov_Exportacao_Declaracao` |
| 1105 | Derivado | Item da nota de exportação com `ID_Exportacao_Declaracao` |
| 1110 | Derivado + 2 campos | `ID_Nota_Fiscal_Entrada` e `Numero_Memorando_Exportacao` no item |
| 1200 | Alterado | `Mov_Credito_Fiscal.ID_Icms_Codigo_Ajuste`; valor `transferencia_icms_recebida` |
| 1210 | Alterado | `Mov_Credito_Fiscal_Aplicacao` (3 campos) |
| 1300 a 1391 | Fora (Q167-6) | Bloco próprio de combustíveis e usina |
| 1400 | Novo | `Mov_Valor_Agregado_Municipio` |
| 1500 | Derivado | Nota de saída de energia (modelo 06) interestadual |
| 1510 | Alterado | `Indicador_Receita_Energia` e `ID_Participante_Receita_Terceiro` no item |
| 1700, 1710 | Novo | `Mov_Documento_Dispositivo_Utilizado` e `_Cancelado` |
| 1800 | Novo | `Mov_Dcta_Apuracao` |
| 1960, 1970, 1975, 1980 | Novo | `Cad_Efd_Giaf_Campo`, `Mov_Efd_Giaf_Apuracao` e `_Valor` |
| C105 | Novo | `Mov_Nota_Fiscal_Icms_St_Uf_Recolhimento` |
| C112 | Novo | `Mov_Nota_Fiscal_Documento_Arrecadacao` |
| C130 | Novo | `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms` |
| C140, C141 | Novo e existente | `Mov_Nota_Fiscal_Fatura_Comercial`; vencimentos em `Mov_Titulo` |
| C165 | Novo | `Mov_Nota_Fiscal_Saida_Combustivel_Transporte` |
| C171 | Novo | `Mov_Nota_Fiscal_Entrada_Item_Tanque` |
| C173 | Novo e alterado | `Mov_Nota_Fiscal_Entrada_Item_Lote`; `IND_MED` e `TP_PROD` nos itens |
| C178 | Alterado | `ID_Classe_Enquadramento_Ipi` no item de saída |
| C179 | Novo | `Mov_Nota_Fiscal_Saida_Item_St_Informacao` |
| C300 a C395 | Derivado (individual) | Nota modelo 02 individual; só consolidada: Q175-E1 |
| C420 | Novo | `Mov_Ecf_Reducao_Z_Totalizador` |
| C425 | Novo | `Mov_Ecf_Reducao_Z_Totalizador_Item` |
| C460, C465, C470 | Alterado | `ID_Reducao_Z`, `Numero_Contador_Cupom_Fiscal` e `Quantidade_Cancelada` |
| C490 | Novo | `Mov_Ecf_Reducao_Z_Analitico` |
| C591 | Derivado | `Mov_Apuracao_Tributo_Item_Parcela_Icms` |
| C500 (cClass) | Alterado | `Cad_Utilidade_Classificacao_Efd` (identidade e carga da NF3e) |
| C700, C790, C791 | Novo | `Mov_Convenio115_Consolidacao`, `_Analitico` e `_Uf` |
| C895, C897 | Novo | `Mov_Sat_Resumo_Observacao` e `Mov_Sat_Resumo_Ajuste` |
| D160, D161, D162 | Alterado | `Mov_Cte` (4 campos) e `Mov_Cte_Documento_Transportado` (2 campos) |
| D300, D301, D310, D410, D411, D420 | Novo | `Mov_Bilhete_Passagem_Consolidado`, `_Cancelado` e `_Municipio` |
| D350, D355, D360 | Existente | Equipamento e Redução Z de bilhete |
| D365, D370, D390 | Novo | `Mov_Ecf_Reducao_Z_Totalizador`, `Mov_Bilhete_Passagem_Municipio` e `Mov_Ecf_Reducao_Z_Analitico` |
| D400 | Alterado | `ID_Participante_Agencia` e `ID_Nota_Rmd` em `Mov_Nota_Fiscal_Saida` |
| D500, D510 | Alterado | `ID_Tipo_Assinante` na nota e `ID_Participante_Receita_Terceiro` no item |
| D530 | Novo | `Mov_Nota_Fiscal_Saida_Terminal_Faturado` |
| D695, D696, D697 | Novo | `Mov_Convenio115_Consolidacao` e filhas |
| D100 (BP-e 63) | A verificar | Q175-E2 |
| 0220 | Alterado | `Codigo_Barras` na conversão de unidade |
| H005 | Derivado | Soma dos itens do inventário |
| H010 | Alterado | `Texto_Complementar` e `ID_Conta_Contabil` |

