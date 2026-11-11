# Entrada de NFGas (76) e NF3e (66), conferência de NFAg (75) e NFCom (62) e NT 2026.005 SN do CT-e — Documento 165

> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 28** (995 entidades, 10.844 campos). Este documento lê os pacotes de schemas e os MOCs que você enviou em 03/11/2026 e propõe: (1) o desenho da **entrada** da NFGas e da NF3e; (2) a conferência da NFAg e da NFCom contra as NT 2026.001, 2026.002, 2026.004 e 2026.005; (3) o efeito da **NT 2026.005 do CT-e (Simples Nacional)**. Pelo D-N141, as quatro notas de utilidade e comunicação são **só de entrada**; o desenho de emissão fica como reserva.

*Lidos por inteiro: os pacotes de schemas da NFGas (versões 1.00d a 1.01a corrigida, NT 2026.002 e NT 2026.004), da NF3e (NT 2026.002 e NT 2026.004), da NFAg (1.00j, NT 2026.001, NT 2026.002 e NT 2026.004) e da NFCom (NT 2026.002, NT 2026.004 e NT 2026.005 SN); os MOCs da NFGas (visão geral 1.00g, anexo I e DANFGas) e da NFAg (visão geral 1.00l, anexo I e DANFAG); o PDF da NT 2026.005 do CT-e. **Não li** o texto de nenhuma NT de NFAg, NFGas, NF3e e NFCom (só vieram schemas e MOCs), o MOC da NF3e nem o da NFCom (seção 12).*

Mlegate · Alberto Beyeler · 3 de novembro de 2026

# 1. Resumo

- **A entrada de NFGas e NF3e cabe no padrão que já existe.** O dicionário já tem, para a entrada de utilidades, o ponto de serviço (`Cad_Ponto_Servico_Utilidade`), a nota de utilidade (`Mov_Nota_Fiscal_Utilidade`), a fatura (`Mov_Nota_Fiscal_Entrada_Fatura`) e a referência de documento (`Mov_Nota_Fiscal_Entrada_Referenciada`). O que falta são os dados próprios de cada modelo: **tarifa, bandeira, medição e contrato** (e, na energia, o **sistema de compensação, o SCEE**).
- **Proposta, igual à da NFCom e da NFAg (D-N67 e D-N141):** a nota recebida é uma **nota de entrada com itens**, mais uma **extensão 1:1** por modelo (`Mov_Nfgas_Entrada` e `Mov_Nf3e_Entrada`) e entidades-filha para os grupos que se repetem.
- **Total proposto: 15 entidades novas e 159 campos** (142 em entidades novas e 17 em entidades existentes). A NFGas tem 6 entidades e 54 campos; a NF3e, 9 entidades e 88 campos.
- **NFAg:** o dicionário foi desenhado sobre as versões 1.00b a 1.00d. As NT 2026.001, 2026.002 e 2026.004 trazem **faturamento agregado e agregador** (`tpFat` 4 e 5), pagamento antecipado, ISUF, e o item líquido. **Faltam 4 campos** em entidades existentes e valores novos em domínios; o vínculo de pagamento (110300) já está coberto pelo genérico.
- **NFCom:** só a **NT 2026.005 SN** é novidade; ela não cria campo. Falta apenas o `gPagAntecipado` no item, coberto pelos 2 campos comuns da seção 7.
- **CT-e, NT 2026.005 SN:** **nenhum campo novo.** O regime do Simples é derivado, a tributação `gTribSN` vai para o complemento do item e o evento 412140 reaproveita `Mov_Dfe_Evento_Simples_Item` (documento 163). Há datas e uma regra nova (seção 9).
- **Achados importantes:** (a) a finalidade 3 da NF3e (**"normal com ajuste"**) está **descontinuada** no schema, mas o schema ainda traz o grupo de ajuste; (b) o **MOC da NFAg 1.00l está atrás do schema** (não cita `tpFat` 4 e 5) e o **MOC da NFGas** tem uma inconsistência sobre o `tpFat` (seção 12); (c) os motivos de substituição **mudam por modelo**: NFGas 01 a 06, NF3e 01 a 05, NFAg 01 a 09.

# 2. Fontes lidas

| Fonte | O que li | O que não li |
|---|---|---|
| NFGas (76) | Schemas 1.00d a 1.01a corrigida, NT 2026.002 RTC 1.01 e NT 2026.004 RTC 1.01; MOC visão geral 1.00g, anexo I e DANFGas 1.00a | Texto das NT 2026.001, .002 e .004; tabela de classificação de item do gás |
| NF3e (66) | Schemas 1.00a das NT 2026.002 e 2026.004 | MOC, anexos, DANF3e e texto das NT; tabela de classificação de item da energia |
| NFAg (75) | Schemas 1.00j, NT 2026.001 (vínculo de pagamento 1.01 corrigida), 2026.002 e 2026.004; MOC visão geral 1.00l, anexo I e DANFAG | Texto das NT |
| NFCom (62) | Schemas NT 2026.002, 2026.004 e 2026.005 SN | MOC e texto das NT |
| CT-e | NT 2026.005 SN v1.00 (PDF) | Schemas desta NT |

Onde o MOC e o schema divergem, **valeu o schema** e a divergência foi para a seção 12.

# 3. O leiaute, em uma tabela

| | NFGas (76) | NF3e (66) |
|---|---|---|
| Faturamento | `tpFat`: 1 normal, 2 agregado, 3 agregador | Normal e substituição (`finNF3e` 1 e 2); **3 = ajuste, descontinuada** |
| Cliente | `instalacao` (id da instalação, cliente, tipo, classe, contrato, GPS, roteiro) | `acessante` (id de acesso, cliente, **tipo de acesso 0 a 8**, classe, **subclasse**, fase, **grupo de tensão 01 a 14**, **modalidade tarifária 01 a 10**, GPS, roteiro) |
| Contratado | `gVolContrat` (até 20) em m³ | `gGrContrat` (até 20) em kW ou kWh, com posto tarifário |
| Medição | `gMed` (até 99): medidor ou conversor, leituras, tipo de medidor | `gMed` (até 20): medidor, datas; os valores lidos ficam **no item** |
| Item | `gNormal` (item, tarifa, fatores de correção, taxa) ou `gAgregadora` | `NFdet` (1 a 13) com `det`: item, **tarifa TE/TUSD, bandeira**, medição por grandeza, ajuste |
| Energia | — | `gSCEE`: geradoras e saldos de crédito por posto |
| Substituição | `gSub`: chave ou **NF em papel** (CNPJ, série, número, competências, hash do convênio 115) | `gSub`: chave ou **NF modelo 06**; `gJudic` para nota separada judicialmente |
| Fatura | `gFat` (obrigatória no normal e no agregador; vedada no agregado) | `gFat` (obrigatória) |
| Outros | `gAgencia`, `gHistCons`, `infAdic` | `gANEEL` (`gHistFat`), `infAdic` |

Os eventos (cancelamento, vínculo de pagamento 110300 e 110301, Simples 412140 e 412141) já são genéricos em `Mov_Dfe_Evento` e `Cad_Dfe_Evento_Tipo` (chaveados por modelo e código); entram só como **linhas de carga** (seção 8).

# 4. Como a entrada se liga ao dicionário

| Dado da nota recebida | Onde fica | Estado |
|---|---|---|
| Emitente, destinatário, chave, datas, totais, tributos (ICMS, PIS, COFINS, IBS, CBS) | `Mov_Documento_Fiscal`, `Mov_Nota_Fiscal_Entrada` e `Mov_Apuracao_Tributo_Item` | Existe |
| Item (produto, quantidade, valor, valor líquido) | `Mov_Nota_Fiscal_Entrada_Item` (já tem valor unitário e total líquidos) | Existe |
| Fatura e código de barras | `Mov_Nota_Fiscal_Entrada_Fatura` | Existe |
| Referência a nota substituída, papel e judicial | `Mov_Nota_Fiscal_Entrada_Referenciada` | **+5 campos e 2 valores** |
| Vínculo de pagamento (110300) | `Mov_Dfe_Vinculo_Pagamento` | Existe |
| Compra governamental | `Mov_Nota_Fiscal_Entrada_Compra_Governamental` | Existe |
| Unidade consumidora ou instalação | `Cad_Ponto_Servico_Utilidade` e `Cad_Ponto_Servico_Identificador` | **+6 campos** |
| Classe, fase, tensão, faixa de consumo | `Mov_Nota_Fiscal_Utilidade` (já tem `Tipo_Ligacao`, `Grupo_Tensao`, `ID_Faixa_Consumo`) | Mapear às tabelas SPED 4.4.x (Q165-E4) |
| Dados próprios do modelo | **Entidades novas desta proposta** | **Novo** |

# 5. NFGas (modelo 76): entidades e campos propostos

## 5.1 `Mov_Nfgas_Entrada` (8 campos)

Extensão 1:1 da nota de entrada modelo 76. *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada** | identificador | --- |
| **ID_Nota_Fiscal_Entrada** | referência (`Mov_Nota_Fiscal_Entrada`), única | A nota a que a extensão pertence |
| **ID_Ponto_Servico_Utilidade** | referência (`Cad_Ponto_Servico_Utilidade`), opcional | A instalação (`instalacao`). **Opcional**, porque é opcional na nota agregadora (`tpFat` 3). Casada pelo `idInstalacao` |
| **Codigo_Cliente** | texto (até 20), opcional | `idCodCliente`: o código do cliente na distribuidora |
| **Identificador_Instalacao** | texto (até 15), opcional | `idInstalacao` como veio, para casar com o ponto quando ele ainda não existe |
| **ID_Tipo_Faturamento** | enumeração {normal, agregado, agregador} | `ide/tpFat`. Domínio `tipo_faturamento_nfgas` |
| **ID_Municipio_Fato_Gerador** | referência (`Cad_Municipio`), opcional | Município do fato gerador do documento (`ide/cMunFG`, quando o schema o traz) |
| **Tipo_Pagamento_Antecipado** | enumeração, opcional {nao_continuado, continuado, abatimento} | `ide/tpPagAnt` (1, 2 e 3). Com `abatimento`, os itens citam a nota antecipada (seção 7) |

## 5.2 `Mov_Nfgas_Entrada_Item` (14 campos)

Dados do item que não cabem no item comum. Uma linha por item. *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada_Item** | identificador | --- |
| **ID_Item** | referência (`Mov_Nota_Fiscal_Entrada_Item`), única | O item comum |
| **ID_Classificacao_Item** | referência (`Cad_Classificacao_Item_Utilidade`), opcional | `cClass`: 7 dígitos, da tabela de classificação de item do gás (validada por regra de validação). A tabela não veio (Q165-12) |
| **ID_Origem_Quantidade** | enumeração (domínio `origem_quantidade_nfgas`, 1 a 8) | `indOrigemQtd`: média, medido, contratada, residual estimado, residual medido e os demais do schema |
| **Fator_Poder_Calorifico** | decimal, opcional | `fatorPCS`. Se informado, multiplica o valor unitário; deve ser maior que zero |
| **Fator_Correcao_Ptz** | decimal, opcional | `fatorPTZ` |
| **Fator_Correcao_Pressao** | decimal, opcional | `fatorP` |
| **Fator_Correcao_Temperatura** | decimal, opcional | `fatorT` |
| **Indicador_Devolucao** | booleano | `indDevolucao` = 1: devolução do valor do item |
| **Percentual_Taxa_Regulatoria** | percentual, opcional | `pTaxa`, do grupo de taxa da agência reguladora |
| **Valor_Taxa_Regulatoria** | valor, opcional | `vTaxa` |
| **Valor_Total_Documento_Agregado** | valor, opcional | Só na nota agregadora (`tpFat` 3): `gAgregadora/vTotDFe` da nota agregada que o item cita. A soma é **conferida** contra o total da nota |
| **Chave_Nota_Anterior** | chave (44), opcional | `det/@chNFGasAnt`: a nota agregada de onde o item vem (agregadora) |
| **Numero_Item_Anterior** | inteiro, opcional | `det/@nItemAnt` |

## 5.3 `Mov_Nfgas_Entrada_Item_Tarifa` (8 campos)

Tarifa aplicada por período (`gTarif`, até 20 por item). *Vigência: não* (é dado do documento).

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada_Item_Tarifa** | identificador | --- |
| **ID_Nfgas_Entrada_Item** | referência (`Mov_Nfgas_Entrada_Item`) | O item |
| **Data_Inicio_Tarifa** | data | `dIniTarif` |
| **Data_Fim_Tarifa** | data, opcional | `dFimTarif` |
| **Numero_Ato** | texto (4) | `nAto`: o ato da agência que aprovou a tarifa |
| **Ano_Ato** | inteiro (4) | `anoAto` |
| **ID_Faixa_Prevista_Consumo** | enumeração {fixa, media} | `tpFaixaCons` |
| **Valor_Tarifa_Aplicada** | decimal (9,8) | `vTarifAplic` |

## 5.4 `Mov_Nfgas_Entrada_Medidor` (12 campos)

Equipamentos de medição da nota (`gMed`, até 99). *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada_Medidor** | identificador | --- |
| **ID_Nfgas_Entrada** | referência (`Mov_Nfgas_Entrada`) | A nota |
| **Numero_Medidor** | inteiro (01 a 99) | `@nMed`: o número que os itens usam para citar a medição |
| **Identificacao_Equipamento** | texto (até 20) | `idEqp` |
| **Data_Leitura_Anterior** | data | `dMedAnt`. Na primeira leitura, a data de instalação do hidrômetro ou medidor |
| **Valor_Leitura_Anterior** | decimal (13,4) | `vMedAnt` |
| **Data_Leitura_Atual** | data | `dMedAtu` |
| **Valor_Leitura_Atual** | decimal (13,4) | `vMedAtu` |
| **Data_Proxima_Leitura** | data, opcional | `dMedProx` |
| **Tipo_Equipamento** | enumeração {medidor, conversor} | `tpEqp` |
| **Tipo_Medidor** | enumeração, opcional {turbina, rotativo, diafragma, ultrassonico} | `tpMedidor`. **Só** quando o equipamento é medidor |
| **Descricao_Ponto_Consumo** | texto (até 60), opcional | `descPontoCons` |

## 5.5 `Mov_Nfgas_Entrada_Item_Medicao` (7 campos)

Liga o item à medição e ao volume contratado (`prod/gMedicao`). Só nos itens de origem "medido" (2) e "residual medido" (5). *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada_Item_Medicao** | identificador | --- |
| **ID_Nfgas_Entrada_Item** | referência (`Mov_Nfgas_Entrada_Item`), única | O item |
| **ID_Nfgas_Entrada_Medidor** | referência (`Mov_Nfgas_Entrada_Medidor`) | `gMedicao/nMed` |
| **ID_Nfgas_Entrada_Volume_Contratado** | referência (`Mov_Nfgas_Entrada_Volume_Contratado`), opcional | `gMedicao/nContrat` |
| **Valor_Medido** | decimal (13,4), opcional | `gMedida/vMed` = (leitura atual − anterior) × constante. Em m³. **Conferido**, com aviso |
| **ID_Motivo_Nao_Leitura** | enumeração, opcional {consumidor, distribuidora, independente} | `tpMotNaoLeitura`. Só quando **não houve medida** |
| **Descricao_Motivo_Nao_Leitura** | texto (até 200), opcional | `xMotNaoLeitura` |

## 5.6 `Mov_Nfgas_Entrada_Volume_Contratado` (5 campos)

Volumes contratados (`gVolContrat`, até 20). *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nfgas_Entrada_Volume_Contratado** | identificador | --- |
| **ID_Nfgas_Entrada** | referência (`Mov_Nfgas_Entrada`) | A nota |
| **Numero_Volume_Contratado** | inteiro (01 a 20) | `@nContrat` |
| **ID_Tipo_Volume_Contratado** | enumeração (domínio `tipo_volume_contratado_nfgas`) | `tpVolContrat`: 1 demanda mínima, 2 montante de uso do sistema de distribuição, 3 encargo de capacidade, 4 volume contratado |
| **Quantidade_Contratada_M3** | decimal (13,6) | `qUnidContrat`, em m³ |

# 6. NF3e (modelo 66): entidades e campos propostos

## 6.1 `Mov_Nf3e_Entrada` (9 campos)

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada** | identificador | --- |
| **ID_Nota_Fiscal_Entrada** | referência (`Mov_Nota_Fiscal_Entrada`), única | A nota |
| **ID_Ponto_Servico_Utilidade** | referência (`Cad_Ponto_Servico_Utilidade`) | A unidade consumidora (`acessante/idAcesso`) |
| **Codigo_Cliente** | texto (até 20), opcional | `idCodCliente` |
| **Identificador_Acesso** | texto (até 15) | `idAcesso` como veio |
| **ID_Municipio_Fato_Gerador** | referência (`Cad_Municipio`) | `ide/cMunFG` |
| **Tipo_Pagamento_Antecipado** | enumeração, opcional | `ide/tpPagAnt` (1, 2 e 3) |
| **ID_Tipo_Participacao_Scee** | enumeração, opcional | `gSCEE/tpPartComp` (1 a 5): minigeração ou microgeração (uma UC), autoconsumo remoto, geração compartilhada, etc. Vazio quando a nota não participa do SCEE |
| **Chave_Nf3e_Origem_Judicial** | chave (44), opcional | `gJudic/chNF3e`: a NF3e original que foi separada judicialmente. Também vai para a referência de documento (`separada_judicialmente`); aqui fica só a chave para consulta direta |

> A chave de origem judicial **duplica** a referência. Se você preferir só a referência, o campo sai (−1 campo); a Q165-9 pergunta.

## 6.2 `Mov_Nf3e_Entrada_Item` (13 campos)

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Item** | identificador | --- |
| **ID_Item** | referência (`Mov_Nota_Fiscal_Entrada_Item`), única | O item comum |
| **ID_Classificacao_Item** | referência, opcional | `cClass`: tabela de classificação de item da NF3e de energia (não veio) |
| **ID_Origem_Quantidade** | enumeração (domínio `origem_quantidade_nf3e`, 1 a 6) | `indOrigemQtd`: média, medida, contratada, calculada, custo de disponibilidade e o último do schema |
| **Indicador_Preco_Acl** | booleano | `indPrecoACL`: valor declarado na DEVEC (convênio ICMS 77/11). Exige ICMS10 e proíbe o grupo de tarifa |
| **Indicador_Devolucao** | booleano | `indDevolucao` |
| **Valor_Pis_Efetivo** | valor, opcional | `vPISEfet`. O PIS "efetivo" é o que o fornecedor realmente recolheu (Q165-C2) |
| **Valor_Cofins_Efetivo** | valor, opcional | `vCOFINSEfet` |
| **ID_Tipo_Ajuste** | enumeração, opcional | `gAjusteNF3eAnt/tpAjuste` (1 a 4). **Descontinuado** com a finalidade 3; mantido só para notas já recebidas |
| **ID_Motivo_Ajuste** | enumeração, opcional | `motAjuste` (1 a 5) |
| **Chave_Nota_Anterior** | chave (44), opcional | `NFdet/@chNF3eAnt` |
| **Numero_Item_Anterior** | inteiro, opcional | `det/@nItemAnt` |
| **Hash_Nota_Mod6_Anterior** | texto (32), opcional | `NFdet/@mod6HashAnt`: hash do registro da nota modelo 06 anterior |

Os **valores do item anterior** (`detItemAnt`: vItem, qFaturada, vProd, tributos e retenções do item ajustado) **ficam só no XML**: são dado de uma nota que já existe no ERP pela chave.

## 6.3 `Mov_Nf3e_Entrada_Item_Tarifa` (13 campos)

Tarifa homologada e aplicada por período (`gTarif`, até 6 por item).

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Item_Tarifa** | identificador | --- |
| **ID_Nf3e_Entrada_Item** | referência (`Mov_Nf3e_Entrada_Item`) | O item |
| **Data_Inicio_Tarifa** | data | `dIniTarif` |
| **Data_Fim_Tarifa** | data | `dFimTarif` |
| **ID_Tipo_Ato** | enumeração {reh, despacho, ren} | `tpAto` (1 a 3): resolução homologatória, despacho, resolução normativa |
| **Numero_Ato** | texto (4) | `nAto` |
| **Ano_Ato** | inteiro (4) | `anoAto` |
| **ID_Tipo_Tarifa** | enumeração {te, tusd} | `tpTarif` |
| **ID_Posto_Tarifario** | enumeração (domínio `posto_tarifario`, 0 a 7) | `cPosTarif`: único, ponta, fora ponta, intermediário e os demais |
| **ID_Unidade_Medida** | enumeração {kw, kwh} | `uMed` (kW só na TUSD) |
| **Valor_Tarifa_Homologada** | decimal (9,8) | `vTarifHom` |
| **Valor_Tarifa_Aplicada** | decimal (9,8) | `vTarifAplic` |
| **ID_Motivo_Diferenca_Tarifa** | enumeração (01 a 04) | `motDifTarif`: decisão judicial, decisão da distribuidora e os demais. **Aviso** quando a aplicada difere da homologada e o motivo falta |

## 6.4 `Mov_Nf3e_Entrada_Item_Bandeira` (8 campos)

Adicional de bandeira tarifária (`gAdBand`, até 3 por item).

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Item_Bandeira** | identificador | --- |
| **ID_Nf3e_Entrada_Item** | referência (`Mov_Nf3e_Entrada_Item`) | O item |
| **Data_Inicio_Adicional** | data | `dIniAdBand` |
| **Data_Fim_Adicional** | data | `dFimAdBand` |
| **ID_Tipo_Bandeira** | enumeração (domínio `bandeira_tarifaria`, 1 a 5) | `tpBand`: verde, amarela, vermelha patamar 1, vermelha patamar 2, escassez |
| **Valor_Adicional** | decimal (13,10) | `vAdBand`: o adicional pelo consumo faturado |
| **Valor_Adicional_Aplicado** | decimal (13,10) | `vAdBandAplic` |
| **ID_Motivo_Diferenca_Adicional** | enumeração (01 a 04) | `motDifBand` |

## 6.5 `Mov_Nf3e_Entrada_Grandeza_Contratada` (6 campos) e `Mov_Nf3e_Entrada_Medidor` (6 campos)

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Grandeza_Contratada** | identificador | --- |
| **ID_Nf3e_Entrada** | referência (`Mov_Nf3e_Entrada`) | A nota |
| **Numero_Contrato** | inteiro (01 a 20) | `@nContrat` |
| **ID_Tipo_Grandeza_Contratada** | enumeração (1 a 4) | `tpGrContrat`: demanda, montante de uso do sistema de distribuição e os demais |
| **ID_Posto_Tarifario** | enumeração (0 a 3) | `tpPosTar` |
| **Quantidade_Contratada** | decimal (13,6) | `qUnidContrat`, em kW ou kWh |

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Medidor** | identificador | --- |
| **ID_Nf3e_Entrada** | referência (`Mov_Nf3e_Entrada`) | A nota |
| **Numero_Medidor** | inteiro (01 a 20) | `@nMed` |
| **Identificacao_Medidor** | texto (até 20) | `idMedidor` |
| **Data_Leitura_Anterior** | data | `dMedAnt` |
| **Data_Leitura_Atual** | data | `dMedAtu` |

## 6.6 `Mov_Nf3e_Entrada_Item_Medicao` (15 campos)

A medição **da NF3e fica no item** (na NFGas fica no medidor). Uma linha por item medido.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Item_Medicao** | identificador | --- |
| **ID_Nf3e_Entrada_Item** | referência (`Mov_Nf3e_Entrada_Item`), única | O item |
| **ID_Nf3e_Entrada_Medidor** | referência (`Mov_Nf3e_Entrada_Medidor`) | `gMedicao/nMed` |
| **ID_Nf3e_Entrada_Grandeza_Contratada** | referência, opcional | `gMedicao/nContrat` |
| **ID_Tipo_Grandeza_Medida** | enumeração (domínio `tipo_grandeza_medida`, 00 a 05) | `tpGrMed`: demanda, demanda reativa, energia ativa, energia ativa injetada e os demais |
| **ID_Posto_Tarifario** | enumeração (0 a 7) | `cPosTarif` |
| **ID_Unidade_Medida** | enumeração {kw, kwh, kvar, kvarh} | `uMed` |
| **Valor_Leitura_Anterior** | decimal (13,4) | `vMedAnt` |
| **Valor_Leitura_Atual** | decimal (13,4) | `vMedAtu` |
| **Fator_Multiplicacao** | decimal (13,6) | `vConst` |
| **Valor_Medido** | decimal (13,4) | `vMed` = (atual − anterior) × constante. **Conferido**, com aviso |
| **Percentual_Perda_Transformacao** | percentual | `pPerdaTran` |
| **Valor_Medido_Apos_Perda_Transformacao** | decimal (13,4) | `vMedPerdaTran` = `vMed` × (1 + perda/100). **Conferido** |
| **Valor_Medido_Apos_Perda_Tecnica** | decimal (13,4), opcional | `vMedPerdaTec` |
| **ID_Motivo_Nao_Leitura** | enumeração, opcional {consumidor, distribuidora, independente} | `tpMotNaoLeitura`. Exclusivo com a medida |

## 6.7 SCEE: `Mov_Nf3e_Entrada_Scee_Geradora` (9 campos) e `Mov_Nf3e_Entrada_Scee_Saldo` (9 campos)

Sistema de compensação de energia (`gSCEE`). A geradora aloca energia a esta unidade; o saldo guarda os créditos por posto.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Scee_Geradora** | identificador | --- |
| **ID_Nf3e_Entrada** | referência (`Mov_Nf3e_Entrada`) | A nota |
| **Identificador_Unidade_Geradora** | texto (até 20) | `idAcessGer` |
| **Potencia_Instalada_Kw** | decimal (5,3) | `vPotInst` |
| **ID_Fonte_Energia** | enumeração (1 a 5) | `tpFonteEnergia`: hidráulica, solar, eólica, térmica, híbrida |
| **Energia_Alocada_Kwh** | decimal (8,3) | `enerAloc` |
| **ID_Posto_Tarifario_Alocada** | enumeração (0 a 3) | `tpPosTar` |
| **Energia_Injetada_Kwh** | decimal (8,3) | `enerInjet` |
| **ID_Posto_Tarifario_Injetada** | enumeração (0 a 3) | `tpPosTarInjet` |

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Nf3e_Entrada_Scee_Saldo** | identificador | --- |
| **ID_Nf3e_Entrada** | referência (`Mov_Nf3e_Entrada`) | A nota |
| **Numero_Tipo_Saldo** | inteiro (1 a 10), opcional | `@nTipoSaldo`: agrupador de saldos múltiplos por posto; vazio no saldo simples |
| **ID_Posto_Tarifario** | enumeração (0 a 3) | `tpPosTar` |
| **Saldo_Anterior_Kwh** | decimal (11,4) | `vSaldAnt` |
| **Creditos_Expirados_Kwh** | decimal (11,4) | `vCredExpirado` |
| **Saldo_Atual_Kwh** | decimal (11,4) | `vSaldAtual` |
| **Creditos_A_Expirar_Kwh** | decimal (11,4) | `vCredExpirar`: a próxima parcela a expirar |
| **Competencia_Expiracao** | competência (AAAAMM) | `CompetExpirar` |

> Os créditos de energia **têm valor econômico**. O ERP só registra; o que o contador faz com o saldo é a Q165-C5.

## 6.8 O que fica só no XML

| Grupo | Por quê |
|---|---|
| `gProcRef` e `gProc` (processo judicial ou administrativo que altera valores) | Dado de processo; a nota recebida já traz os valores finais. Sem uso fiscal no ERP |
| `gHistCons` (NFGas), `gANEEL/gHistFat` (NF3e) | Histórico de consumo para o consumidor ler; não gera lançamento |
| `gAgencia` (NFGas) e `gContab` | Dados da agência reguladora e de contabilidade do emitente |
| `detItemAnt` da NF3e | Já existe na nota anterior |
| `infAdic`, `autXML`, `gRespTec`, `qrCod`, `ISUFEmit` do emitente | Cabeçalho comum do DF-e |

# 7. Alterações em entidades existentes

| Entidade | Mudança | Campos | Por quê |
|---|---|---|---|
| `Cad_Ponto_Servico_Utilidade` | Campos novos: `ID_Tipo_Acesso` (`tpAcesso` 0 a 8 da NF3e; na NFGas, `tpInstalacao` 1 a 3), `ID_Subclasse_Consumo` (`tpSubClasse`), `ID_Modalidade_Tarifaria` (`tpModTar` 01 a 10), `Nome_Unidade_Consumidora` (`xNomeUC`), `Detalhe_Classe_Consumo` (`xClasse`, classe "outros") e `Numero_Contrato_Fornecimento` (`nContrato`) | **+6** | Dado **da instalação**, que se repete a cada nota; o ponto já guarda tipo de ligação, contrato, GPS e roteiro. Classe, fase e tensão vão para o existente `Mov_Nota_Fiscal_Utilidade` |
| `Mov_Nota_Fiscal_Entrada_Item` | Campos novos `Chave_Dfe_Pagamento_Antecipado` (`gPagAntecipado/chDFePagAnt`) e `Numero_Item_Pagamento_Antecipado` (`nItemPagAnt`) | **+2** | Vale para NFGas, NF3e, NFAg e NFCom (todas têm o `gPagAntecipado`). **Conferir se já existe** (Q165-E1) |
| `Mov_Nfag_Entrada` | Campo novo `Tipo_Pagamento_Antecipado` (`tpPagAnt`) | **+1** | Falta no desenho da NFAg |
| `Mov_Nfag_Entrada_Item` | Campos novos `Valor_Total_Documento_Agregado` (`gAgregadora/vTotDFe`), `Chave_Nota_Anterior` (`@chNFAgAnt`) e `Numero_Item_Anterior` (`@nItemAnt`) | **+3** | Faturamento agregador (`tpFat` 5), igual ao da NFGas |
| `Mov_Nota_Fiscal_Entrada_Referenciada` | Campos novos para a nota **em papel** referenciada: `Modelo_Papel`, `Cnpj_Emitente_Papel`, `Serie_Papel`, `Numero_Papel` e `Competencia_Apuracao_Papel` | **+5** | NFGas e NF3e referenciam nota em papel (`gSub/gNF`), com competências e hash do convênio 115. O campo `Hash_Convenio_115` e a competência de emissão já existem. **Conferir o DDL** (Q165-E1): se já houver esses campos, o total cai |
| `Mov_Nota_Fiscal_Entrada_Referenciada.Tipo_Referencia` | Valores novos `faturamento_agregado` e `separada_judicialmente` | 0 | A NFGas e a NFAg têm nota agregada; a NF3e tem a nota separada judicialmente |
| `Mov_Nota_Fiscal_Entrada_Referenciada.ID_Motivo_Substituicao` | Domínios por modelo: NFGas 01 a 06, NF3e 01 a 05, NFAg 01 a 09 | 0 | O motivo **muda por modelo** (domínio por modelo, como no CT-e e no BP-e) |
| `Mov_Nfag_Entrada.ID_Tipo_Faturamento` (`tipo_faturamento_nfag`) | Valores 4 (agregado) e 5 (agregador) | 0 | O schema da NT 2026.004 os traz; o MOC 1.00l ainda não (Q165-E3) |
| `Cad_Classe_Sistema` | Valores 66 e 76 em `modelo_documento_fiscal` (se ainda não); domínios novos listados nas seções 5 e 6, com os de tarifa e SCEE | 0 | Vocabulário pequeno e fechado pelo schema |
| `Cad_Dfe_Evento_Tipo` | Linhas dos modelos 66 e 76 (110111, 110300, 110301, 412140, 412141) e conferir os do 75 e do 62 | 0 | Tipo chaveado por modelo e código |
| `Cad_Dfe_Leiaute` | Linhas `NFGas`, `NF3e`, `NFAg` e `NFCom` por versão e NT, com as datas como vigência | 0 | As datas esperam o texto das NT (Q165-E5) |
| `Cad_Cclasstrib_Modelo` | Conferir as marcas `indNF3e`, `indNFAg` e `indNFGas` | 0 | Já existem |

# 8. Eventos

| Código | Evento | Quem registra | Proposta |
|---|---|---|---|
| 110111 | Cancelamento | Emitente | `Mov_Dfe_Evento`; vedar com aviso se houver substituição ou vínculo de pagamento ativo |
| 110300 e 110301 | Vínculo de pagamento e cancelamento | Emitente | `Mov_Dfe_Vinculo_Pagamento` e `Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado` (já aprovados) |
| 412140 | Tributação do Simples Nacional | **Fisco** | `Mov_Dfe_Evento_Simples_Item` (documento 163; desenho provisório) |
| 412141 | Cancelamento da tributação do Simples | Fisco | `Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado` aponta para o 412140 |

As NFGas, NF3e e NFAg só tinham, nos schemas, os eventos acima; **os MOCs listam outros eventos** (por exemplo, no faturamento agregador) que ainda precisam de leitura: ficam como pendência (Q165-E2).

# 9. CT-e: NT 2026.005 (Simples Nacional)

A NT 2026.005 do CT-e repete a do NF-e (documento 163) e a do BP-e (documento 164): **não cria campo**.

| Ponto da NT | Tratamento |
|---|---|
| `tpRegimeIBSCBS` | **Derivado** do regime da filial na emissão; sem campo |
| `gTribSN` (no lugar do `gIBSCBS` do emitente Simples) | `Mov_Apuracao_Tributo_Item_Complemento` com o tipo `ibs_cbs_simples_nacional` |
| Evento 412140 (tributação do Simples, pelo Fisco) | `Mov_Dfe_Evento_Simples_Item`: **1 item** para CT-e e CT-e OS; **1 por viagem** no CT-e Simplificado |
| Evento 412141 (cancelamento) | Evento genérico; no NF-e continua 110001 (cada modelo no seu código) |
| Sem `cAtivSN` no CT-e | Nenhum campo de atividade do Simples no CT-e |
| Datas | **26/10/2026** (homologação) e **16/11/2026** (produção) da NT; regras de validação a partir de **16/11/2026** (homologação) e **14/12/2026** (produção) |
| Regra 909 | CT-e complementar com mais de uma chave do mesmo ano e mês: **aviso**, não bloqueio |
| `tpEnteGov` | Regras a partir de 2027 e 2028, em `Cad_Dfe_Parametro_Regra` |
| MEI (CRT 4) | Não tem `IBSCBS` |

**Parâmetros previstos:** `CTE-SN-DATAS`, `CTE-SN-REGRA-909-AVISO` e `CTE-SN-TPENTEGOV-VIGENCIA`, com vigência e **sem valor** até a confirmação das datas (a NT está no PDF, mas os schemas desta NT não vieram).

# 10. Conferência da NFAg e da NFCom

## 10.1 NFAg (75): schema das NT 2026.001, .002 e .004 contra o dicionário

| Ponto do schema | Já coberto? | Ação |
|---|---|---|
| `tpFat` 4 e 5 (agregado e agregador), `gAgregadora` | Não | Valores novos no domínio; +3 campos no item (seção 7) |
| `tpPagAnt` e `gPagAntecipado` | Não | +1 campo na extensão e +2 comuns no item |
| `pgtoVinc` (NT 2026.001, 110300 e 110301) | **Sim**, pelo vínculo genérico | Nenhuma |
| `ISUFEmit` (Suframa) e ALC/ZFM | Sim, por ser do emitente e do item comum | Conferir as marcas |
| `vItemLiq` e `vProdLiq` | **Sim** (o item comum tem valor unitário e total líquidos) | Nenhuma |
| Motivo de substituição 01 a 09 | Parcial | Domínio por modelo |
| Tributação IBS e CBS (NT 2026.002 e .004) | Sim | Nenhuma |

**Divergência:** o MOC da NFAg (1.00l) **não cita** `tpFat` 4 e 5, mas o schema os tem. Valeu o schema (Q165-E3).

## 10.2 NFCom (62): schema das NT 2026.002, .004 e .005 contra o dicionário

Só a NT 2026.005 SN é novidade, e ela **não cria campo** (mesmo tratamento da seção 9 e do documento 163). O `gPagAntecipado` falta no item (`Mov_Nfcom_Entrada_Item`) e é coberto pelos 2 campos comuns. As referências `@chNFComAnt` e `indNFComAntPapelFatCentral` (fatura centralizada em papel) **já têm** `Tipo_Referencia` = `faturamento_centralizado` e `Indicador_Nota_Anterior_Papel`.

# 11. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Revisão 28 (real) | 995 | 10.844 |
| Revisão 29 prevista (documentos 161 e 163, e Q138-8 a Q138-10), sem a Q161-1 e a Q161-2 | 1.005 | 11.003 |
| **NFGas (entrada):** `Mov_Nfgas_Entrada` (8), `_Item` (14), `_Item_Tarifa` (8), `_Medidor` (12), `_Item_Medicao` (7) e `_Volume_Contratado` (5) | +6 | +54 |
| **NF3e (entrada):** `Mov_Nf3e_Entrada` (9), `_Item` (13), `_Item_Tarifa` (13), `_Item_Bandeira` (8), `_Grandeza_Contratada` (6), `_Medidor` (6), `_Item_Medicao` (15), `_Scee_Geradora` (9) e `_Scee_Saldo` (9) | +9 | +88 |
| **Entidades existentes:** ponto de serviço (+6), item de entrada (+2), NFAg extensão (+1), NFAg item (+3), referência de documento (+5) | 0 | +17 |
| **Total deste documento** | **+15** | **+159** |

| Cenário | Entidades | Campos |
|---|---|---|
| Revisão 29 prevista **sem o BP-e** (documento 164) | 1.005 | 11.003 |
| Mais este documento | **1.020** | **11.162** |
| Revisão 29 com o BP-e completo (documento 164, cenário máximo: 1.012 e 11.089) e este documento | **1.027** | **11.248** |

Com a Q161-1 e a Q161-2 aprovadas, somam-se mais 2 campos em todos os cenários. Se a Q165-9 tirar `Chave_Nf3e_Origem_Judicial` e a Q165-E1 mostrar campos já existentes, o total cai.

# 12. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| **Q165-1** | NFGas e NF3e entram **só como entrada** (D-N141), com o desenho de emissão como reserva, e as 15 entidades (142 campos) acima? | **Sim** |
| **Q165-2** | O padrão é **nota de entrada + item + extensão 1:1 por modelo** (D-N67), igual à NFCom e à NFAg? | **Sim** |
| **Q165-3** | O ponto de serviço ganha **+6 campos** (tipo de acesso, subclasse, modalidade tarifária, nome da UC, detalhe da classe e contrato), e classe, fase e tensão ficam na nota de utilidade existente? | **Sim** |
| **Q165-4** | **Tarifa, bandeira e medição** são entidades-filha (e não só XML), porque o contador e a conferência de custo precisam delas? | **Sim** |
| **Q165-5** | O **SCEE** vira duas entidades (geradora e saldo), com os créditos como dado econômico? | **Sim** |
| **Q165-6** | Os grupos da seção 6.8 (`gProcRef`, histórico de consumo, agência, `detItemAnt`) **ficam só no XML**? | **Sim** |
| **Q165-7** | O pagamento antecipado (`gPagAntecipado`) vira **+2 campos comuns** em `Mov_Nota_Fiscal_Entrada_Item`, valendo para os quatro modelos? | **Sim** |
| **Q165-8** | A NFAg ganha os **+4 campos** e os valores 4 e 5 em `tipo_faturamento_nfag`? | **Sim** |
| **Q165-9** | A referência de documento ganha os **+5 campos de nota em papel** e os valores `faturamento_agregado` e `separada_judicialmente`; a chave de origem judicial fica **nos dois lugares** (referência e `Chave_Nf3e_Origem_Judicial`, para consulta direta)? | **Sim** (a contagem já inclui o campo; sem ele, −1 campo) |
| **Q165-10** | Os motivos de substituição ficam em **domínio por modelo**, e a finalidade 3 (ajuste) da NF3e é **aceita na entrada com aviso** (descontinuada)? | **Sim** |
| **Q165-11** | O CT-e da NT 2026.005 SN recebe o **mesmo tratamento** do NF-e e do BP-e (sem campo; `gTribSN` no complemento; evento 412140 no `Mov_Dfe_Evento_Simples_Item`)? | **Sim** |
| **Q165-12** | Os parâmetros (datas das NT, regra 909, vigência do `tpEnteGov`) entram em `Cad_Dfe_Parametro_Regra` **sem valor**, e você envia o **texto das NT** de NFAg, NFGas, NF3e, NFCom e CT-e, os **MOCs da NF3e e da NFCom** e as **tabelas de classificação de item** do gás e da energia? (Soma-se à Q164-12) | **Sim** |

# 13. Para o contador e para a equipe

| Id | Pendência | Tratamento provisório |
|---|---|---|
| **Q165-C1** | **Crédito de IBS e CBS quando o emitente é do Simples Nacional sem regime regular:** o XML traz `gTribSN` no lugar do `gIBSCBS`. Qual crédito o adquirente apura nas contas de luz, gás, água e telecomunicação recebidas de um emitente do Simples? | Registrar o `gTribSN` e **não** calcular o crédito; aviso ao usuário |
| **Q165-C2** | **PIS e Cofins "efetivos" da NF3e** (`vPISEfet`, `vCOFINSEfet`): o crédito é sobre o valor destacado ou sobre o efetivo? | Guardar os dois; o Motor usa o destacado até a resposta |
| **Q165-C3** | **Nota em papel referenciada** (modelo 06 ou outro): como escriturar a substituição de uma nota que o ERP nunca recebeu? | Guardar a referência; sem lançamento |
| **Q165-C4** | **Faturamento agregado e agregador** (NFGas e NFAg): quem toma o crédito, a nota agregada ou a agregadora, e o que a soma `vTotDFe` significa na escrituração? | Registrar as duas; o crédito fica em cada item, com aviso de duplicidade |
| **Q165-C5** | **Créditos do SCEE** (saldo, expirados, a expirar): há tratamento contábil ou fiscal do saldo em kWh? | Registrar sem valorar |
| **Q165-E1** | **Conferir o DDL:** se já existem em `Mov_Nota_Fiscal_Entrada_Item` os campos de nota antecipada, e em `Mov_Nota_Fiscal_Entrada_Referenciada` os campos de nota em papel | Contar como novos até a conferência |
| **Q165-E2** | **Eventos dos MOCs** da NFGas e da NFAg (além do cancelamento, vínculo e Simples): ler e desenhar | Sem desenho |
| **Q165-E3** | **MOC da NFAg 1.00l** não cita `tpFat` 4 e 5 e o **MOC da NFGas** tem uma **inconsistência sobre o `tpFat`** (G47 e G60 se contradizem sobre quando a `gFat` é obrigatória): confirmar com o autorizador | Valeu o schema |
| **Q165-E4** | **Mapear classe, fase e tensão** às tabelas SPED 4.4.5, 4.4.2 e 4.4.3 (já usadas em `Mov_Nota_Fiscal_Utilidade`) | Domínios por modelo até o mapa |
| **Q165-E5** | **Datas das NT** de NFAg, NFGas, NF3e e NFCom: **não achei data nos schemas**; os textos não vieram | Sem valor em `Cad_Dfe_Leiaute` e nos parâmetros |

# 14. Limites

- **Só li schemas e MOCs.** O texto das NT de NFAg, NFGas, NF3e e NFCom não veio; as regras de validação, as datas e os prazos ficam sem valor.
- **Não li o MOC da NF3e nem o da NFCom,** nem as tabelas de classificação de item (gás e energia). A lista de valores de alguns domínios (por exemplo, posto tarifário 4 a 7, classes e subclasses) vem do `enum` do schema e **não tem a descrição completa**.
- **A lista de campos das entidades existentes** vem dos comentários do DDL, que só listam as colunas comentadas: a conferência real é a Q165-E1.
- **O desenho de emissão** de NFGas, NF3e, NFAg e NFCom **não foi feito** (D-N141).
- **Nada foi aplicado.** O dicionário segue na revisão 28; a revisão 29 só muda quando você disser "consolidar".
