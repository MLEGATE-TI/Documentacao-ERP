# Desenho das lacunas de uso comum e de 2027 da EFD-ICMS/IPI — Documento 168

*Resposta ao seu "sim, pode desenhar no próximo consolidar" (Q167-1) e ao "sim, controlar no controle de estoque de terceiros" (Q167-3). Este documento desenha as lacunas G1 a G14 do documento 167, entidade por entidade e campo por campo. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O desenho acrescenta **11 entidades novas** e altera **26 existentes** (campos novos, valores novos de enumeração ou descrição corrigida). Nenhum campo é removido e nenhuma entidade muda de módulo. Todas as entidades novas ficam na Contabilidade & Fiscal.

| Lacuna | O que resolve | Entidades novas | Entidades alteradas |
|---|---|---|---|
| G1 | `IND_BENEFICIO` (C197, C597, D197, D737, E111, E220, 1921) | 0 | 3 |
| G2 | Nota de crédito por redução (`COD_SIT` 09 e 10, exceção 12 do C100) | 0 | 3 |
| G3 | Municípios 9999999 e 9999998 | 0 | 2 |
| G4 | Obrigatoriedade separada de entrada e saída | 0 | 1 |
| G5 | ST, FCP e DIFAL por item | 1 | 1 |
| G6 | Ressarcimento e complemento de ST (C176, C180 a C186, 1250, 1255) | 4 | 2 |
| G7 | Processo e histórico nas obrigações a recolher (E116, E250, E316, 1926) | 0 | 1 |
| G8 | Documentos referenciados e ajustes de documento fora do ERP | 0 | 3 |
| G9 | CIAP (G130 de entrada legada e de saída) | 1 | 1 |
| G10 | Bloco K, estoque de terceiros, IPI decendial | 1 | 5 |
| G11 | Rótulos de `Mov_Apuracao_Ipi` | 0 | (mesma de G10) |
| G12 | D130 do CT-e simplificado | 1 | 1 |
| G13 | ISS do DF (B020, B350, B510) | 2 | 2 |
| G14 | C500 campos 39 e 40 (NF3e e NFGás) | 1 | 1 |

Um ponto de atenção: a **G10 muda o que o documento 06 (seção 8.2) diz** sobre o material do encomendante, que hoje fica "deliberadamente fora" do saldo. Com a sua resposta, ele passa a ser controlado no estoque de terceiros, sem valor. A consolidação corrige o texto do documento 06 e o do documento 04, que hoje se contradizem.

# 2. Regras que segui

1. **Parâmetro com vigência, sem valor escondido.** Obrigações que mudam por data (por exemplo, `IND_BENEFICIO` obrigatório a partir de 01/01/2027) ficam em `Cad_Obrigacao_Leiaute_Campo` com vigência, não no código.
2. **Avisos, não bloqueios.** Faltou um campo da EFD, o ERP avisa na geração e não impede o lançamento.
3. **O ERP só registra.** O que a EFD calcula (C190, E110, K200, valores unitários convertidos e valores de entrega do D130) sai por derivação dos dados de origem, sem coluna redundante.
4. **Extensão 1:1 e filho 1:N**, no padrão da D-N67: o campo que só uma minoria de notas usa vai para entidade própria.
5. **Nomes** em português com sublinhado; o prefixo `Valor_` só nos campos número, referência, texto e enumeração (regra H2 da auditoria).
6. **Campos opcionais de ligação**: quando o documento existe no ERP, a referência vale; quando não existe (documento de terceiro ou anterior ao ERP), os campos de identificação ficam preenchidos à mão.
7. **Uma entidade tem um motivo** (Q165 e anteriores): onde a lacuna cabe em campo novo de entidade existente, não crio entidade.

# 3. Desenho por lacuna

## 3.1 G1 — Indicador de benefício (`IND_BENEFICIO`)

O guia 3.2.3 (subseção 16, leiaute 2027) pede o campo nos ajustes de documento (C197, C597, D197, D737) e nos ajustes de apuração (E111, E220 e 1921). Valores: 0 (não compõe o cálculo da repercussão econômica), 1, 2 e 3 (alíneas a, b e c do inciso V do art. 385 da LC 214/2025) e 9 (outra repercussão). É obrigatório quando o **terceiro dígito do código de ajuste não é 9**. O E311 (DIFAL e FCP) não tem o campo.

**Domínio novo** em `Cad_Classe_Sistema.Dominio`: `indicador_beneficio_icms`, com cinco valores: `nao_compoe` (0), `alinea_a` (1), `alinea_b` (2), `alinea_c` (3) e `repercussao_outra` (9). A carga usa a descrição do guia.

**`Cad_Icms_Codigo_Ajuste` (altera; entidade com vigência)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Indicador_Beneficio_Padrao` | referência (`Cad_Classe_Sistema`, domínio = `indicador_beneficio_icms`), opcional | Sugestão do indicador para este código de ajuste. O usuário confirma no lançamento. A sugestão muda por versão (vigência), porque a UF pode reclassificar o código. Vazio nos códigos cujo terceiro dígito é 9 (não exigem o indicador). |

**`Mov_Apuracao_Ajuste` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Indicador_Beneficio` | referência (`Cad_Classe_Sistema`, domínio = `indicador_beneficio_icms`), opcional | IND_BENEFICIO do E111, E220 e 1921 (campo 05). Obrigatório no arquivo a partir de 01/2027 quando o terceiro dígito do código não é 9. Sem valor escondido: o ERP **sugere** o padrão do código e o usuário confirma; sem confirmação, a geração avisa e deixa o campo em branco. |

**`Mov_Nota_Ajuste_Documento` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Indicador_Beneficio` | referência (`Cad_Classe_Sistema`, domínio = `indicador_beneficio_icms`), opcional | IND_BENEFICIO do C197, C597, D197 e D737 (campo 09). Mesma regra do campo acima. |

**Parâmetro de obrigatoriedade.** Duas linhas novas de carga em `Cad_Obrigacao_Leiaute_Campo`, com `Vigencia_Inicio` = 01/01/2027: C197 campo 09 e E111 campo 05 (e as quatro equivalentes). Valor de `Valores_Validos` = `0; 1; 2; 3; 9`.

## 3.2 G2 — Nota de crédito por redução (`COD_SIT` 09 e 10)

O que o guia diz: `COD_SIT` 09 é o "documento fiscal emitido com redução de valores ou quantidades" e 10 é a "escrituração extemporânea" do mesmo; a exceção 12 do C100 vale a partir de 01/01/2027 e dispensa a maior parte dos campos (basta REG, `IND_OPER`, `IND_EMIT`, `COD_PART`, `COD_MOD`, `COD_SIT`, `NUM_DOC`, `CHV_NFE` e `DT_DOC`). **A nota de terceiro entra como saída** (`IND_OPER` = 1, `IND_EMIT` = 1); a nota própria entra como entrada. Em 2026 o item pode ter quantidade zero (Ajuste SINIEF 49/2025).

O dicionário já tem `ID_Tipo_Nota_Credito` (tipo da nota de crédito, 6 tipos, um deles a redução de valores) nas duas notas. Faltam a finalidade na nota de entrada e a regra de escrituração. **Este desenho é a minha recomendação para a Q167-4 (finalidade própria); se você preferir só a situação do documento, o G2 encolhe para a primeira linha da tabela 4.1.2.**

| Entidade | Mudança |
|---|---|
| `Cad_Classe_Sistema` (domínio `situacao_documento_fiscal`) | Carga: valores 09 e 10 da tabela 4.1.2, com as descrições do guia. A situação é decidida pelo Motor de Regras: 09 quando a finalidade é crédito e o tipo é redução de valores ou quantidades; 10 quando a escrituração é extemporânea. |
| `Mov_Nota_Fiscal_Entrada.Finalidade` | Valores novos `credito` e `debito` (a nota de saída já os tem). |
| `Mov_Nota_Fiscal_Entrada.Escriturada_Como_Saida` | Novo, booleano, opcional: verdadeiro na nota de crédito de redução **emitida por terceiro** (a EFD a registra com `IND_OPER` 1). Só preenchido na finalidade `credito`. |
| `Mov_Nota_Fiscal_Saida.Escriturada_Como_Entrada` | Novo, booleano, opcional: verdadeiro na nota de crédito de redução **de emissão própria** (a EFD a registra na entrada). |
| `Mov_Nota_Fiscal_Entrada_Item.Quantidade` | Descrição corrigida: a quantidade zero é aceita na nota de crédito de redução (2026); o aviso de "quantidade maior que zero" não dispara nessa finalidade. |

## 3.3 G3 — Municípios sentinela e regra do D100 campo 25

O dicionário diz que o CT-e usa 9999999 (exterior) em `Mov_Cte.ID_Municipio_Envio`, mas `Cad_Municipio` exige os dois primeiros dígitos iguais à UF. A regra da casa (linha de `Cad_Participante_Endereco`) é não cadastrar município estrangeiro, só a sentinela da NF-e. O guia pede também 9999998 (origem do CT-e simplificado, `COD_MUN_ORIG` do D100, campo 24).

**`Cad_Estado`** (carga): uma linha `EX`, com `Codigo_IBGE` 99, nome "Exterior". Sem campo novo.

**`Cad_Municipio` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Tipo_Municipio` | enumeração {municipio, exterior, origem_nao_informada}, opcional | `exterior`: a sentinela 9999999. `origem_nao_informada`: a sentinela 9999998, usada só no `COD_MUN_ORIG` do CT-e simplificado. Vazio nos municípios reais. A regra de integridade do código ignora as sentinelas. |

**`Mov_Cte.ID_Municipio_Envio` (altera só a descrição):** o 9999999 passa a existir como linha de `Cad_Municipio` (e não mais como valor solto).

Carga: duas linhas (9999999 "EXTERIOR" e 9999998 "ORIGEM NÃO INFORMADA — CT-E SIMPLIFICADO"), ambas apontando para o estado `EX`.

**Regra do campo 25 do D100** (`COD_MUN_DEST`): o guia diz para não usar o 9999998 no destino (preencher com o município real ou 9999999 se for exterior) e, a partir de 2027, a validação passa a rejeitá-lo. O campo é obrigatório na entrada dos modelos 57, 63 e 67. Entra como duas linhas de `Cad_Obrigacao_Leiaute_Campo` (D100 campo 24 aceita 9999998 no CT-e simplificado; campo 25 aceita 9999999 e, com vigência a partir de 01/01/2027, deixa de aceitar 9999998), não como código.

## 3.4 G4 — Obrigatoriedade de entrada e de saída

`Cad_Obrigacao_Leiaute_Campo.Eh_Obrigatorio` é um booleano único. A EFD-ICMS/IPI tem colunas separadas de entrada e saída, com "O", "OC", "N" e "não apresentar".

**`Cad_Obrigacao_Leiaute_Campo` (altera; entidade com vigência)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Exigencia_Entrada` | enumeração {obrigatorio, opcional, condicional, nao_apresentar}, opcional | Coluna "Entr." do guia. Vazio quando a obrigação não separa entrada e saída: vale `Eh_Obrigatorio`. |
| `Exigencia_Saida` | enumeração {obrigatorio, opcional, condicional, nao_apresentar}, opcional | Coluna "Saída" do guia. Mesma regra. |

`condicional` é o "OC" do guia (obrigatório se uma condição escrita na validação se cumpre). `Eh_Obrigatorio` continua e passa a ser a resposta para as obrigações que não separam entrada e saída (ECF, ECD, EFD-Contribuições).

## 3.5 G5 — ICMS-ST, FCP e DIFAL por item

O item de apuração (`Mov_Apuracao_Tributo_Item`) guarda um tributo por linha, com base e alíquota próprias. Faltam: (a) a **alíquota do ICMS-ST** (`pICMSST`, usada no C170 e no C176); (b) o **FCP** do item em três versões (próprio, do ST e retido anteriormente), que a NF-e destaca em grupos separados; (c) a **partilha do DIFAL** por item (ICMS de destino, ICMS de remetente e FCP de destino). Sem isso, C101, C170 (campos de ST), C191, D101, D731 e D761 não se montam.

**`Mov_Apuracao_Tributo_Item` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Aliquota_St` | número, opcional | `pICMSST`: alíquota do ICMS retido por substituição, em percentual. Só quando `Responsabilidade_Tributaria` não é operação própria. |

**`Mov_Apuracao_Tributo_Item_Parcela_Icms` (nova; filho 1:N do item de apuração)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Apuracao_Tributo_Item_Parcela_Icms` | identificador | --- |
| `ID_Apuracao` | referência (`Mov_Apuracao_Tributo_Item`) | A linha de ICMS do item a que a parcela pertence. |
| `Tipo_Parcela` | enumeração {fcp, fcp_st, fcp_retido_anteriormente, difal_destino, difal_remetente, fcp_destino} | `fcp`: FCP da operação própria (`vFCP`). `fcp_st`: FCP do ST (`vFCPST`). `fcp_retido_anteriormente`: FCP retido em operação anterior (`vFCPSTRet`). `difal_destino`: ICMS devido à UF de destino (`vICMSUFDest`). `difal_remetente`: ICMS devido à UF do remetente (`vICMSUFRemet`; zero desde 2019, mantido pelo guia). `fcp_destino`: FCP da UF de destino (`vFCPUFDest`). |
| `Base_Calculo` | número, opcional | A base da parcela (`vBCFCP`, `vBCFCPST`, `vBCFCPSTRet`, `vBCUFDest`). |
| `Aliquota_Percentual` | número, opcional | A alíquota da parcela (`pFCP`, `pFCPST`, `pFCPSTRet`, `pICMSUFDest`, `pFCPUFDest`). |
| `Aliquota_Interestadual` | número, opcional | `pICMSInter`: alíquota interestadual do DIFAL. Só nas parcelas de DIFAL. |
| `Valor` | número | O valor da parcela, tal como na nota (nunca recalculado). |

**Regras.** (1) Uma linha por `Tipo_Parcela` e por item, no máximo. (2) O C191, o D731 e o D761 somam a parcela por documento; o ERP não guarda total. (3) O campo da EFD que recebe cada parcela é o do registro (por exemplo, `VL_FCP_OP` do C191); o mapa fica nas linhas de `Cad_Obrigacao_Leiaute_Campo`. (4) A parcela `difal_remetente` aceita zero, e a obrigatoriedade dela, depois de 2019, é regra com vigência em `Cad_Obrigacao_Leiaute_Campo`.

## 3.6 G6 — Ressarcimento e complemento de ST

O ressarcimento hoje cobre o C176 do leiaute antigo (`Mov_Icms_St_Ressarcimento`) e uma consolidação genérica (`Mov_Icms_St_Ressarcimento_Consolidado`). O guia 3.2.4 traz os registros C180 e C181 (entradas), C185 e C186 (saídas) e, no Bloco 1, o 1250 e o 1255, todos "a critério da UF". **Todos entram, com habilitação por UF** (`Cad_Empresa_Modulo_Opcional`, do desenho da sua resposta de 05/10/2026).

**`Mov_Icms_St_Ressarcimento` (C176; altera)** — acrescenta os campos que o guia 3.2.4 lista e que faltavam:

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Responsavel_Retencao` | referência (`Cad_Classe_Sistema`, domínio = `responsavel_retencao_icms_st`), opcional | `COD_RESP_RET` (campo 18): 1 remetente direto, 2 remetente indireto, 3 próprio declarante. |
| `Base_Icms_Ultima_Entrada_Unitaria` | número, opcional | `VL_UNIT_BC_ICMS_ULT_E` (12): base unitária do ICMS próprio na última entrada. |
| `Aliquota_Icms_Ultima_Entrada` | número, opcional | `ALIQ_ICMS_ULT_E` (13). |
| `Limite_Base_Unitaria` | número, opcional | `VL_UNIT_LIMITE_BC_ICMS_ULT_E` (14): o menor entre a base e o limite da legislação. |
| `Aliquota_St_Ultima_Entrada` | número, opcional | `ALIQ_ST_ULT_E` (16). |
| `Chave_Nfe_Retencao` | código (até 50), opcional | `CHAVE_NFE_RET` (20): NF-e da retenção do ST. |
| `ID_Participante_Retencao` | referência (`Cad_Participante`, opcional) | `COD_PART_NFE_RET` (21). |
| `Serie_Nfe_Retencao` | código (até 5), opcional | `SER_NFE_RET` (22). |
| `Numero_Nfe_Retencao` | código (até 15), opcional | `NUM_NFE_RET` (23). |
| `Numero_Item_Retencao` | número, opcional | `ITEM_NFE_RET` (24). |
| `Tipo_Documento_Arrecadacao` | enumeração {estadual, gnre}, opcional | `COD_DA` (25). |
| `Numero_Documento_Arrecadacao` | texto, opcional | `NUM_DA` (26). |

**Mantidos como estão:** `Icms_St_Unitario` (`VL_UNIT_ICMS_ULT_E`, 15), `Fcp_St_Unitario` (27) e `ID_Motivo_Ressarcimento` (19). **Derivados:** o `VL_UNIT_RES` (17) é o `Valor_Ressarcimento` dividido pela quantidade; `COD_MOD_ULT_E`, `NUM_DOC_ULT_E`, `SER_ULT_E`, `DT_ULT_E`, `COD_PART_ULT_E`, `VL_UNIT_ULT_E` e `CHAVE_NFE_ULT_E` vêm do item de entrada de origem. O campo `Icms_Proprio_Unitario`, que a entidade já tem, não tem equivalente nominal no guia 3.2.4 (pergunta Q168-3).

**`Mov_Icms_St_Complemento_Entrada` (nova; C180)** — filho 1:1 do item da nota de entrada de mercadoria sujeita a ST. Não pode existir junto com o C181 do mesmo item.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Complemento_Entrada` | identificador | --- |
| `ID_Item_Entrada` | referência (`Mov_Nota_Fiscal_Entrada_Item`) | O item (1:1). |
| `ID_Responsavel_Retencao` | referência (`Cad_Classe_Sistema`, domínio = `responsavel_retencao_icms_st`) | `COD_RESP_RET`. |
| `Quantidade_Convertida` | número | `QUANT_CONV` (6 decimais). |
| `ID_Unidade_Conversao` | referência (`Cad_Unidade_Medida`) | `UNID`: a unidade usada em `QUANT_CONV`. |
| `Valor_Unitario_Convertido` | número | `VL_UNIT_CONV`. |
| `Icms_Operacao_Propria_Unitario` | número | `VL_UNIT_ICMS_OP_CONV`: o ICMS próprio que daria crédito no regime comum. |
| `Base_St_Unitaria_Convertida` | número, opcional | `VL_UNIT_BC_ST_CONV` (campo 07 do guia). |
| `Icms_St_Unitario_Convertido` | número | `VL_UNIT_ICMS_ST_CONV`. |
| `Fcp_St_Unitario_Convertido` | número, opcional | `VL_UNIT_FCP_ST_CONV`. |
| `Tipo_Documento_Arrecadacao` | enumeração {estadual, gnre}, opcional | `COD_DA`. |
| `Numero_Documento_Arrecadacao` | texto, opcional | `NUM_DA`. |
| `Codigo_Produto_Fornecedor` | código (até 60), opcional | `COD_PROD` (campo 12, novo no leiaute 2026): o `cProd` do fornecedor para o item. |

**`Mov_Icms_St_Complemento_Devolucao_Saida` (nova; C181)** — devolução de saída de mercadoria com ST; filho do item de entrada.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Complemento_Devolucao_Saida` | identificador | --- |
| `ID_Item_Entrada` | referência (`Mov_Nota_Fiscal_Entrada_Item`) | O item da nota de devolução. |
| `ID_Motivo_Restituicao_Complemento` | referência (`Cad_Classe_Sistema`, domínio = `motivo_restituicao_complemento_icms_st`) | `COD_MOT_REST_COMPL`, tabela 5.7. |
| `Quantidade_Convertida` e `ID_Unidade_Conversao` | número e referência | `QUANT_CONV` e `UNID`. |
| `ID_Item_Saida` | referência (`Mov_Nota_Fiscal_Saida_Item`, opcional) | O item da saída devolvida, quando está no ERP. |
| `ID_Modelo_Documento_Saida` | referência (`Cad_Modelo_Documento_Fiscal`, opcional) | `COD_MOD_SAIDA`, quando a saída não está no ERP. |
| `Serie_Saida`, `Numero_Documento_Saida`, `Chave_Documento_Saida`, `Data_Emissao_Saida`, `Numero_Item_Saida`, `Numero_Fabricacao_Ecf_Saida` | código, número, código, data, número, código, todos opcionais | `SERIE_SAIDA`, `NUM_DOC_SAIDA`, `CHV_DFE_SAIDA`, `DT_DOC_SAIDA`, `NUM_ITEM_SAIDA` e `ECF_FAB_SAIDA`: só quando `ID_Item_Saida` está vazio. |
| `Valor_Unitario_Convertido_Saida` | número | `VL_UNIT_CONV_SAIDA`. |

**`Mov_Icms_St_Complemento_Saida` (nova; C185)** — complemento da nota de saída de mercadoria com ST; filho 1:1 do item de saída.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Complemento_Saida` | identificador | --- |
| `ID_Item_Saida` | referência (`Mov_Nota_Fiscal_Saida_Item`) | O item (1:1). `NUM_ITEM`, `COD_ITEM`, `CST_ICMS` e `CFOP` vêm dele. |
| `ID_Motivo_Restituicao_Complemento` | referência (`Cad_Classe_Sistema`, domínio = `motivo_restituicao_complemento_icms_st`) | `COD_MOT_REST_COMPL`. |
| `Quantidade_Convertida` e `ID_Unidade_Conversao` | número e referência | `QUANT_CONV` e `UNID`. |
| `Valor_Unitario_Convertido` | número | `VL_UNIT_CONV`. |
| `Icms_Unitario_Na_Operacao` | número | `VL_UNIT_ICMS_NA_OPERACAO`. |
| `Icms_Operacao_Propria_Unitario` | número | `VL_UNIT_ICMS_OP_CONV`. |
| `Icms_Operacao_Propria_Estoque_Unitario`, `Icms_St_Estoque_Unitario`, `Fcp_St_Estoque_Unitario` | número | Os valores unitários do estoque (`VL_UNIT_ICMS_OP_ESTOQUE_CONV`, `VL_UNIT_ICMS_ST_ESTOQUE_CONV`, `VL_UNIT_FCP_ICMS_ST_ESTOQUE_CONV`). |
| `Icms_St_Unitario_Convertido`, `Fcp_St_Unitario_Convertido` | número | `VL_UNIT_ICMS_ST_CONV_REST` e `VL_UNIT_FCP_ST_CONV_REST` (restituição). |
| `Icms_St_Complemento_Unitario`, `Fcp_St_Complemento_Unitario` | número | `VL_UNIT_ICMS_ST_CONV_COMPL` e `VL_UNIT_FCP_ST_CONV_COMPL` (complemento). |

**`Mov_Icms_St_Complemento_Saida_Entrada` (nova; C186)** — filho 1:N do C185: as entradas ligadas à saída.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Icms_St_Complemento_Saida_Entrada` | identificador | --- |
| `ID_Icms_St_Complemento_Saida` | referência (`Mov_Icms_St_Complemento_Saida`) | O C185 pai. |
| `ID_Item_Entrada` | referência (`Mov_Nota_Fiscal_Entrada_Item`, opcional) | A entrada, quando está no ERP. |
| `ID_Motivo_Restituicao_Complemento` | referência (domínio = `motivo_restituicao_complemento_icms_st`) | `COD_MOT_REST_COMPL`. |
| `Quantidade_Convertida` e `ID_Unidade_Conversao` | número e referência | `QUANT_CONV` e `UNID`. |
| `ID_Modelo_Documento_Entrada`, `Serie_Entrada`, `Numero_Documento_Entrada`, `Chave_Documento_Entrada`, `Data_Emissao_Entrada`, `Numero_Item_Entrada` | referência, código, código, código, data, número | `COD_MOD_ENTRADA`, `SERIE_ENTRADA`, `NUM_DOC_ENTRADA`, `CHV_DFE_ENTRADA`, `DT_DOC_ENTRADA`, `NUM_ITEM_ENTRADA`: só quando `ID_Item_Entrada` está vazio. |
| `Valor_Unitario_Convertido_Entrada` | número | `VL_UNIT_CONV_ENTRADA`. |
| `Icms_Operacao_Propria_Unitario_Entrada`, `Base_St_Unitaria`, `Icms_St_Unitario_Entrada`, `Fcp_St_Unitario_Entrada` | número | `VL_UNIT_ICMS_OP_CONV_ENTRADA`, `VL_UNIT_BC_ICMS_ST_ENTRADA`, `VL_UNIT_ICMS_ST_CONV_ENTRADA` e `VL_UNIT_FCP_ST_CONV_ENTRADA`. |

**Consolidação do 1250 e do 1255 — `Mov_Icms_St_Ressarcimento_Consolidado` (altera).** O guia pede, por motivo, cinco valores. O 1250 (totais do período) é a soma dos 1255 e sai por derivação.

| Campo | Tipo | Descrição |
|---|---|---|
| `Valor_Credito` | número | Descrição corrigida: passa a ser o `VL_CREDITO_ICMS_OP_MOT` do 1255 (crédito do ICMS da operação própria no motivo). |
| `Icms_St_Restituicao` | número | `VL_ICMS_ST_REST_MOT`. |
| `Fcp_St_Restituicao` | número | `VL_FCP_ST_REST_MOT`. |
| `Icms_St_Complemento` | número | `VL_ICMS_ST_COMPL_MOT`. |
| `Fcp_St_Complemento` | número | `VL_FCP_ST_COMPL_MOT`. |

`Valor_Debito` e `Valor_Total`, que a entidade já tem, não têm equivalente no guia 3.2.4; ficam como informativos (pergunta Q168-4).

**Domínios novos em `Cad_Classe_Sistema`:** `responsavel_retencao_icms_st` (3 valores) e `motivo_restituicao_complemento_icms_st` (tabela 5.7; a carga depende da tabela, Q167-5; até lá o ERP avisa).

**Habilitação.** Cada registro tem uma linha em `Cad_Empresa_Modulo_Opcional` (domínio `modulo_fiscal_opcional`, um valor por registro: `efd_c176`, `efd_c180`, `efd_c181`, `efd_c185`, `efd_c186`, `efd_1250_1255`), com vigência e por empresa e filial. Cinco valores novos no domínio.

## 3.7 G7 — Processo e histórico nas obrigações a recolher

**`Mov_Apuracao_Obrigacao_Recolher` (altera)** — serve E116, E250, E316 e 1926, que têm os mesmos campos 06 a 10.

| Campo | Tipo | Descrição |
|---|---|---|
| `Numero_Processo` | código (até **60**), opcional | Passa de 15 para 60 posições (`NUM_PROC`). |
| `ID_Origem_Processo` | referência (`Cad_Classe_Sistema`, domínio = `origem_processo_icms`), opcional | `IND_PROC`: 0 SEFAZ, 1 Justiça Federal, 2 Justiça Estadual, 9 outros. Obrigatório quando há `Numero_Processo` (aviso). |
| `Descricao_Processo` | texto, opcional | `PROC`: descrição resumida do processo que embasou o lançamento. Obrigatória quando há `Numero_Processo` (aviso). |
| `Texto_Complementar` | texto, opcional | `TXT_COMPL`: descrição complementar da obrigação. |
| `Mes_Referencia` | competência, opcional | Descrição corrigida: o guia exige o mês de referência (`MES_REF`, formato mmaaaa) em todo arquivo; o ERP avisa quando vazio e não gera valor. |

## 3.8 G8 — Documentos referenciados e ajustes de documento fora do ERP

A chave de acesso basta para documento eletrônico que o ERP não tem **só quando** o leiaute pede nada mais que a chave. C113, C114, C116 e os registros de ajuste de documento (E113, E240, E313 e E531) pedem também modelo, série, número, data e participante. A chave não traz a data de emissão.

**`Mov_Nota_Fiscal_Entrada_Referenciada` e `Mov_Nota_Fiscal_Saida_Referenciada` (alteram, mesmos campos)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Modelo_Documento_Referenciado` | referência (`Cad_Modelo_Documento_Fiscal`), opcional | `COD_MOD` do C113, C114 e C116 (campo de modelo). |
| `Serie_Referenciada` e `Subserie_Referenciada` | código, opcionais | `SER` e `SUB` do C113. |
| `Numero_Referenciado` | código (até 15), opcional | `NUM_DOC` do C113, C114 e C116. |
| `Data_Emissao_Referenciada` | data, opcional | `DT_DOC` do C113, C114 e C116. |
| `ID_Participante_Emitente_Referenciado` | referência (`Cad_Participante`), opcional | `COD_PART` do C113. |
| `Numero_Fabricacao_Ecf` e `Numero_Caixa_Ecf` | código, opcionais | `ECF_FAB` e `ECF_CX` do C114 (cupom referenciado). |
| `Numero_Sat` | código (até 9), opcional | `NR_SAT` do C116. |

Obrigatórios (aviso) quando `ID_Documento_Fiscal_Referenciado` está vazio; ignorados quando o documento está no ERP, porque os dados saem dele.

**`Mov_Apuracao_Ajuste_Documento` (altera)** — para E113, E240, E313 e E531.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante` | referência (`Cad_Participante`), opcional | `COD_PART`. |
| `ID_Modelo_Documento` | referência (`Cad_Modelo_Documento_Fiscal`), opcional | `COD_MOD`. |
| `Serie` e `Subserie` | código, opcionais | `SER` e `SUB`. |
| `Numero_Documento` | código (até 15), opcional | `NUM_DOC`. |
| `Data_Emissao` | data, opcional | `DT_DOC`. |
| `ID_Produto_Servico` | referência (`Cad_Produto_Servico`), opcional | `COD_ITEM`, quando o ajuste é de item de nota que não está no ERP. |

Obrigatórios (aviso) quando `ID_Documento_Fiscal` e `Tipo_Item_Origem` estão vazios.

## 3.9 G9 — CIAP (G130 legado e de saída)

`Mov_Ciap_Bem_Item.ID_Item_Nota_Entrada` é obrigatório; por isso o bem que entrou antes do ERP não tem como ser lançado, e a alienação (G125 com `TIPO_MOV` AT e outros) não tem documento de saída ligado.

**`Mov_Ciap_Bem_Item` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Item_Nota_Entrada` | referência (`Mov_Nota_Fiscal_Entrada_Item`), **agora opcional** | Obrigatório (aviso) só quando os campos do documento anterior estão vazios. |
| `Indicador_Emitente_Documento_Anterior` | enumeração {proprio, terceiros}, opcional | `IND_EMIT` do G130. |
| `ID_Participante_Documento_Anterior` | referência (`Cad_Participante`), opcional | `COD_PART` do G130. |
| `ID_Modelo_Documento_Anterior` | referência (`Cad_Modelo_Documento_Fiscal`), opcional | `COD_MOD`. |
| `Serie_Documento_Anterior` | código, opcional | `SERIE`. |
| `Numero_Documento_Anterior` | código (até 15), opcional | `NUM_DOC`. |
| `Chave_Documento_Anterior` | código (até 50), opcional | `CHV_NFE_CTE`. |
| `Data_Emissao_Documento_Anterior` | data, opcional | `DT_DOC`. |
| `Numero_Item_Documento_Anterior` | número, opcional | `NUM_ITEM` do G140. |

Todos os campos do documento anterior são obrigatórios (aviso) quando `ID_Item_Nota_Entrada` está vazio.

**`Mov_Ciap_Movimentacao_Documento` (nova; G130 filho do G125)** — documento de saída ou de transferência da movimentação.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Ciap_Movimentacao_Documento` | identificador | --- |
| `ID_Movimentacao` | referência (`Mov_Ciap_Movimentacao`) | A movimentação (`TIPO_MOV` AT, BA, OT e os demais que pedem documento). |
| `ID_Nota_Saida` | referência (`Mov_Nota_Fiscal_Saida`), opcional | O documento, quando a Mlegate emitiu a saída no ERP. |
| `ID_Nota_Entrada` | referência (`Mov_Nota_Fiscal_Entrada`), opcional | O documento, quando é nota de entrada própria. |
| `Indicador_Emitente`, `ID_Participante`, `ID_Modelo_Documento`, `Serie`, `Numero_Documento`, `Chave_Documento`, `Data_Emissao` | enumeração, referência, referência, código, código, código, data | `IND_EMIT`, `COD_PART`, `COD_MOD`, `SERIE`, `NUM_DOC`, `CHV_NFE_CTE`, `DT_DOC`: só quando nenhuma nota está ligada. |
| `Numero_Documento_Arrecadacao` | texto, opcional | `NUM_DA`. |

## 3.10 G10 e G11 — Bloco K, estoque de terceiros e IPI

### Estoque de terceiros no controle de estoque (Q167-3, opção a)

**Decisão.** O material do encomendante em poder da Mlegate (K200 `IND_EST` 1) e o material próprio em poder de terceiros (`IND_EST` 2) passam a ser movimentos de estoque de **propriedade de terceiros**, sem valor, com o participante dono ou possuidor. Isso **substitui** a regra do documento 06 (seção 8.2), que deixava o material do encomendante fora do saldo.

**`Cad_Tipo_Movimento_Estoque` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Metodo_Valoracao` | enumeração, **valor novo** `sem_valor` | O movimento não tem valor: `Valor_Total` é zero e ele não entra no custo médio, no saldo de valor nem na contabilidade. Só para os tipos de material de terceiros. |
| `Propriedade_Movimento` | enumeração {proprio, de_terceiros_em_poder_da_empresa}, **obrigatório** | De quem é o material que o tipo movimenta. A carga dos tipos existentes é `proprio`. A remessa **da Mlegate para terceiros** continua sendo transferência para um local `Tipo = terceiros` (que já tem o participante do operador), e o saldo dela é derivado do local, sem tipo próprio. |

Tipos novos de carga (nomes livres, como os atuais): "Entrada de material de terceiros (remessa para industrialização)", "Consumo de material de terceiros" e "Retorno de material de terceiros".

**`Mov_Estoque_Movimento_Item` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Propriedade` | enumeração {proprio, de_terceiros_em_poder_da_empresa}, obrigatório | Copiado do tipo de movimento no lançamento, e guardado para que a mudança futura do tipo não reescreva o passado. |
| `ID_Participante_Proprietario` | referência (`Cad_Participante`), opcional | O dono do material. Obrigatório (aviso) quando `Propriedade` não é `proprio`. |

**`Mov_Saldo_Estoque` (altera só a descrição e o índice)** — o saldo passa a ser único por local, posição, produto, lote, competência, **propriedade e participante**; os campos `Propriedade` e `ID_Participante_Proprietario` já existem. O K200 e o H010 saem do saldo por propriedade; o custo médio (`Mov_Estoque_Custo_Medio`) ignora tudo o que não é `proprio`.

**`Mov_Ordem_Producao_Item` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Movimento_Estoque_Item_Saida` | referência, opcional | Descrição corrigida: na ordem `industrializacao_terceiro`, o componente do encomendante também tem a saída física (movimento de propriedade de terceiros). Isso dá o `DT_SAÍDA` do K235 por derivação. |
| `Data_Consumo_Terceiro` | data, opcional | `DT_CONS` do K255: data em que o terceiro consumiu o insumo da Mlegate. Obrigatório (aviso) quando `Terceirizado` é verdadeiro. |

### Obrigatoriedade dos registros do K por tipo de leiaute

Hoje a regra "K210, K215, K235, K255 e outros não são exigidos no leiaute simplificado" mora no código. Vira parâmetro.

**`Cad_Bloco_K_Exigencia_Registro` (nova; mestre com vigência)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Bloco_K_Exigencia_Registro` | identificador | --- |
| `ID_Bloco_K_Exigencia_Registro_Versao` | identificador da versão | Chave primária da versão (tabela física `Cad_Bloco_K_Exigencia_Registro_Versao`). |
| `Tipo_Leiaute_Bloco_K` | enumeração {simplificado, completo, restrito_saldos} --- identidade | O tipo do K010 (o mesmo domínio de `Cad_Filial_Perfil_Fiscal.Tipo_Leiaute_Bloco_K`). |
| `Codigo_Registro` | código (4) --- identidade | K210, K215, K230, K235 e os demais. |
| `Exigencia` | enumeração {obrigatorio, dispensado, dispensado_se_quantidade_zero} | A tabela do guia para o K010. `dispensado_se_quantidade_zero` cobre o K230 com quantidade zero. |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto opcional | Padrão da Fase 0. |

### IPI decendial e rótulos do `Mov_Apuracao_Ipi` (G11)

**`Mov_Apuracao_Ipi` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Data_Inicio_Periodo` | data | `DT_INI` do E500: início do decêndio ou do mês. Fonte também do `DT_INI` do K100 quando o IPI é decendial. |
| `Data_Fim_Periodo` | data | `DT_FIN` do E500. |
| `Ipi_Recolher` | número | **Descrição corrigida:** é o `VL_SD_IPI` do E520 (saldo devedor a recolher). A descrição atual dizia `VL_SC_IPI`. |
| `Saldo_Credor_Transportar` | número | **Descrição corrigida:** é o `VL_SC_IPI` (saldo credor a transportar). |
| `Outros_Debitos` | número | `VL_OD_IPI`: outros débitos (estornos de crédito), soma dos ajustes de débito. |
| `Outros_Creditos` | número | `VL_OC_IPI`: outros créditos (estornos de débito). |
| `Estornos` | número | **Descrição corrigida:** passa a ser a soma de `Outros_Debitos` e `Outros_Creditos`, só para a leitura; o valor sai das duas colunas novas. |

## 3.11 G12 — D130 do CT-e simplificado

Desde janeiro de 2025 o CT-e simplificado (modelo 57, tipos 5 e 6) tem um D130 **por entrega**. Os valores de cada entrega saem dos componentes do CT-e; falta só a identificação da entrega e a classe do componente.

**`Mov_Cte_Componente_Valor` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Classe_Componente` | enumeração {frete_liquido, sec_cat, despacho, pedagio, outros}, opcional | A classe do guia (`VL_LIQ_FRT`, `VL_SEC_CAT`, `VL_DESP`, `VL_PEDG`, `VL_OUT`). Vazio nos CT-e que não são simplificados. |
| `ID_Cte_Simplificado_Prestacao` | referência (`Mov_Cte_Simplificado_Prestacao`), opcional | A entrega a que o componente pertence. |

**`Mov_Cte_Simplificado_Prestacao` (nova; D130)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Cte_Simplificado_Prestacao` | identificador | --- |
| `ID_Cte` | referência (`Mov_Cte`) | O CT-e simplificado. |
| `ID_Participante_Consignatario` | referência (`Cad_Participante`), opcional | `COD_PART_CONSG`. |
| `ID_Participante_Redespachado` | referência (`Cad_Participante`), opcional | `COD_PART_RED`. |
| `ID_Tipo_Frete_Redespacho` | referência (`Cad_Classe_Sistema`, domínio = `tipo_frete_redespacho`), opcional | `IND_FRT_RED`. |
| `ID_Municipio_Origem` | referência (`Cad_Municipio`) | `COD_MUN_ORIG` (aceita as sentinelas da G3). |
| `ID_Municipio_Destino` | referência (`Cad_Municipio`) | `COD_MUN_DEST`. |
| `Placa_Veiculo` | código (7), opcional | `VEIC_ID`. |
| `ID_Estado_Placa` | referência (`Cad_Estado`), opcional | `UF_ID`. |

`VL_LIQ_FRT`, `VL_SEC_CAT`, `VL_DESP`, `VL_PEDG`, `VL_OUT` e `VL_FRT` (total) são **derivados** dos componentes por classe. O valor da prestação do CT-e continua em `Mov_Cte.Valor_Prestacao`, e o ERP avisa quando a soma das entregas diverge.

## 3.12 G13 — ISS do DF (Bloco B)

**`Mov_Nota_Iss_Df_Complemento` (nova; B020, filho 1:1 da nota)** — o que o B020 pede além do valor contábil.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Iss_Df_Complemento` | identificador | --- |
| `Origem_Tipo` | enumeração {nota_fiscal_entrada, nota_fiscal_saida} | Direção da nota (mesmo padrão de `Mov_Nota_Fiscal_Utilidade`). |
| `ID_Nota` | referência genérica | A nota de serviço. |
| `Valor_Material_Terceiros` | número, opcional | `VL_MAT_TER`. |
| `Valor_Subempreitada` | número, opcional | `VL_SUB`. |
| `Valor_Deducao_Base_Calculo` | número, opcional | `VL_DED_BC`. |

**`Mov_Apuracao_Iss_Df` (altera só as descrições)** — `Valor_Material_Terceiros` (B), `Valor_Subempreitadas` (D) e `Valor_Deducoes_Base` (F) passam a ser **derivados** da soma dos complementos das notas do mês; a digitação direta deixa de ser a regra. Quando a empresa lança só o total (sem as notas), o ERP aceita o valor no próprio campo e avisa que o B470 não se confere com os documentos.

**`Cad_Empresa_Profissional_Habilitado` (altera; B510)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Indicador_Habilitacao` | enumeração {habilitado, nao_habilitado} | `IND_PROF` do B510: o profissional é habilitado (conselho) ou não (empregado). A entidade passa a cobrir os dois; os campos do conselho ficam opcionais para o não habilitado. |
| `Escolaridade_Efd` | enumeração {superior, medio}, opcional | `IND_ESC`: escolaridade do profissional. O `IND_SOC` (sócio ou não) sai de `ID_Empresa_Socio`. |

Os campos `ID_Conselho` e `Registro_Conselho` passam a opcionais quando `Indicador_Habilitacao` é `nao_habilitado`.

**`Mov_Iss_Df_Conta_Cosif` (nova; B350)** — só para a instituição financeira com estabelecimento no DF. Habilitação por `Cad_Empresa_Modulo_Opcional`.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Iss_Df_Conta_Cosif` | identificador | --- |
| `ID_Apuracao_Iss_Df` | referência (`Mov_Apuracao_Iss_Df`) | A apuração do mês. |
| `ID_Conta_Contabil` | referência (`Cad_Conta_Contabil`) | `COD_CTD` e `CTA_ISS` (código e descrição saem da conta). |
| `Codigo_Cosif` | código (8) | `CTA_COSIF`: conta do COSIF a que a conta se subordina. |
| `Quantidade_Ocorrencias` | número, opcional | `QTD_OCOR`. |
| `Codigo_Item_Lista_Servicos` | código (4) | `COD_SERV`. |
| `Observacao_Lancamento` | referência (`Cad_Observacao_Lancamento_Fiscal`), opcional | `COD_INF_OBS`. |

`VL_CONT`, `VL_BC_ISS`, `ALIQ_ISS` e `VL_ISS` são derivados do saldo da conta e da alíquota do item da lista.

## 3.13 G14 — NF3e e NFGás: `ENER_INJET` e `OUTRAS_DED`

O C500 (campos 39 e 40) soma os itens por **grupo de cClass** (NF3e: 560 e 085 e 087 para a energia injetada, 590 para outras deduções; NFGás: os grupos "deduções"). O dicionário guarda o cClass do item, mas não diz a que campo da EFD cada grupo alimenta (a NFCom já tem esse mapa em `Cad_Nfcom_Classificacao_Servico`).

**`Cad_Utilidade_Classificacao_Efd` (nova; mestre com vigência)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Utilidade_Classificacao_Efd` | identificador | --- |
| `ID_Utilidade_Classificacao_Efd_Versao` | identificador da versão | Chave primária da versão. |
| `Documento` | enumeração {nf3e, nfgas} --- identidade | Qual nota. |
| `Grupo_Classificacao` | código (3) --- identidade | Os três primeiros dígitos do cClass (o grupo). |
| `Campo_Efd_Destino` | enumeração {fornecimento, servico_nao_tributado, terceiros, despesas_acessorias, energia_injetada, outras_deducoes} | O campo do C500 que recebe a soma do grupo (`VL_FORN`, `VL_SERV_NT`, `VL_TERC`, `VL_DA`, `ENER_INJET`, `OUTRAS_DED`). |
| `Natureza_Valor` | enumeração {soma, deducao} | Sinal do item nos totais. |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto opcional | Padrão da Fase 0. |

**`Mov_Nota_Fiscal_Utilidade` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Valor_Energia_Injetada` | número, derivado | `ENER_INJET` (campo 39 do C500): soma dos itens dos grupos com destino `energia_injetada`. |
| `Valor_Outras_Deducoes` | número, derivado | `OUTRAS_DED` (campo 40): soma dos itens dos grupos com destino `outras_deducoes`. |
| `Tipo_Ligacao` e `Grupo_Tensao` | --- | Descrição corrigida: a marca "(a conferir)" sai; são `TP_LIGACAO` (1 monofásica, 2 bifásica, 3 trifásica) e `COD_GRUPO_TENSAO` (código de 2 dígitos da tabela 4.4.3), **só em nota de saída do modelo 06**. |

**Regra da NFGás (modelo 76).** Finalidades só 1 (normal) e 2 (substituição) no C500. Entra como linha de `Cad_Dfe_Parametro_Regra` (que já guarda as regras de validação, com vigência), com aviso quando a nota de entrada do modelo 76 traz finalidade diferente. A carga do mapa `Cad_Utilidade_Classificacao_Efd` depende da tabela cClass (Q165-12, Q167-5); até lá o ERP avisa que `ENER_INJET` e `OUTRAS_DED` não foram calculados.

# 4. Pontos em aberto deste desenho

| Pergunta | O que está desenhado | Alternativa |
|---|---|---|
| **Q168-1 (herda a Q167-4)** Nota de crédito por redução: finalidade própria na nota de entrada e marca de escrituração como saída | O desenho da seção 3.2: valores `credito` e `debito` na finalidade da entrada e dois booleanos | Só a situação do documento (`COD_SIT` 09 e 10), sem finalidade nova. O Motor de Regras decide pela situação |
| **Q168-2** Índice do saldo: acrescentar propriedade e participante à unicidade do `Mov_Saldo_Estoque` | Sim (seção 3.10) | Manter a unicidade atual e distinguir o terceiro por local próprio |
| **Q168-3** `Mov_Icms_St_Ressarcimento.Icms_Proprio_Unitario` não tem campo equivalente no guia 3.2.4 | Mantido, sem uso pelo gerador | Aposentar o campo (nenhum campo foi removido até hoje; só com a sua ordem) |
| **Q168-4** `Valor_Debito` e `Valor_Total` do consolidado de ressarcimento | Mantidos como informativos | Aposentar |
| **Q168-5** B350 (instituição financeira no DF) entra agora ou só quando houver uma | Entra agora, por habilitação (você aprovou "todas as lacunas" em 05/10/2026) | Ficar para quando houver estabelecimento financeiro no DF |

As cinco perguntas **não impedem o consolidar**: o desenho acima já vale com as minhas recomendações, e uma resposta contrária só muda a linha citada.

# 5. O que entra no próximo "consolidar"

- **11 entidades novas:** `Mov_Apuracao_Tributo_Item_Parcela_Icms`, `Mov_Icms_St_Complemento_Entrada`, `Mov_Icms_St_Complemento_Devolucao_Saida`, `Mov_Icms_St_Complemento_Saida`, `Mov_Icms_St_Complemento_Saida_Entrada`, `Mov_Ciap_Movimentacao_Documento`, `Cad_Bloco_K_Exigencia_Registro`, `Mov_Cte_Simplificado_Prestacao`, `Mov_Nota_Iss_Df_Complemento`, `Mov_Iss_Df_Conta_Cosif` e `Cad_Utilidade_Classificacao_Efd`. Dois são mestres com versão (`Cad_Bloco_K_Exigencia_Registro` e `Cad_Utilidade_Classificacao_Efd`).
- **26 entidades alteradas** (lista nas seções 3.1 a 3.13).
- **Domínios novos em `Cad_Classe_Sistema.Dominio`:** `indicador_beneficio_icms`, `responsavel_retencao_icms_st`, `motivo_restituicao_complemento_icms_st`, `origem_processo_icms` e `tipo_frete_redespacho`; mais cinco valores em `modulo_fiscal_opcional` (um por registro de ressarcimento de ST) e dois valores de `situacao_documento_fiscal` (09 e 10).
- **Cargas:** as linhas de `Cad_Obrigacao_Leiaute_Campo` com vigência 2027, o estado `EX` e os dois municípios sentinela, os tipos de movimento de material de terceiros, e a regra do modelo 76 em `Cad_Dfe_Parametro_Regra`.
- **Documentos corrigidos junto:** 06 (seção 8.2) e 04, pela mudança do estoque de terceiros.
- **Fora do consolidar, por falta de tabela oficial** (Q167-5): `motivo_restituicao_complemento_icms_st` (tabela 5.7), `Cad_Utilidade_Classificacao_Efd` (cClass) e as tabelas 5.3 e 5.5 em `Cad_Icms_Codigo_Ajuste`; o ERP avisa nas gerações.

Continuam **sem desenho** (Q167-2, a sua resposta pendente): os blocos setoriais da seção 5.3 do documento 167 (G15 a G19), a Q167-4 já herdada acima e a Q167-6.
