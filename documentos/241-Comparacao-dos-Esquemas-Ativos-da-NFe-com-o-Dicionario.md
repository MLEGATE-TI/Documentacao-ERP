# Comparação dos esquemas ativos da NF-e com o dicionário — Documento 241

*Você enviou os esquemas ativos da NF-e (28 arquivos zip) e 12 PDFs, e disse que são todos os ativos da Receita. Li os 251 arquivos XSD, montei o inventário, comparei as cinco versões do leiaute (PL_010d a PL_010h), os eventos, os serviços de consulta e a variante de CNPJ alfanumérico com o dicionário na revisão 52 e com as revisões 48 a 52, e olhei os PDFs. **Resultado: o dicionário já cobre quase tudo.** Achei **8 pontos** (lacunas, divergências de texto e material que falta), que viraram as perguntas Q241-1 a Q241-8. **Nada foi aplicado ao dicionário** (revisão 52 mantida); só aplico quando você escrever "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Assunto** | **Resultado** |
|---|---|
| O que chegou | 28 zips (2 repetidos: o CNPJ alfanumérico e a prorrogação para industrialização), **26 pacotes distintos**, **251 arquivos XSD**; 12 PDFs, dos quais **7 distintos** (5 são cópias idênticas) |
| Leiaute da NF-e (PL_010d a PL_010h) | De 1.055 para 1.130 caminhos (grupos e campos): **+99 e −24** entre a 010d e a 010h. Dos 99 novos, **87 já estão cobertos**; os 12 restantes são o grupo da diferença do biocombustível (Q241-6). A forma ad valorem do monofásico cabe na estrutura atual, com um detalhe aberto (Q241-7), e há três acertos de texto (Q241-8) |
| Eventos | 44 esquemas de evento (43 códigos do documento 232 mais a averbação 790700 já na carga). **Nenhum código novo.** Faltam campos em 4 eventos (Q241-3, Q241-4 e Q241-5) |
| Serviços de consulta | Distribuição de DF-e (v1.01): coberta, com um modo de consulta a acrescentar (Q241-5). Consulta de situação (v4.00 na PL_010d): coberta; a v2.01 do pacote ConSitNFe é antiga. **Consulta de GTIN no CCG: não existe no dicionário** (Q241-2). Consulta de cadastro (CCC) v2.00: coberta |
| CNPJ alfanumérico (NT 2026.004) | Coberto desde a revisão 41; a única diferença nova é o endereço do destinatário (campos de exterior e limites de tamanho) |
| Material que falta | **Pacote de esquemas da NFC-e (modelo 65):** a partir da PL_010g o campo `mod` só aceita 55 (Q241-1). Os esquemas dos eventos 420110 a 420170 continuam sem aparecer (Q232-9 segue aberta) |
| PDFs | Todos são **versões antigas**, já superadas pelas que o dicionário usa (NT 2020.001 v1.60, NT 2023.004 v1.20, NT 2023.005 v1.02, MOC 7.0). Servem só como histórico; nenhum fato novo |
| Contagem se tudo for aprovado | **1.242 entidades** (0), **14.448 campos** (+9), 3.703 referências (0), 374 domínios (0); o DDL ganha 9 comentários |

# 2. O que chegou

## 2.1 Esquemas (XSD)

| **Família** | **Pacote** | **Arquivos XSD** | **Conteúdo** |
|---|---|---|---|
| Leiaute da NF-e | PL_010d v1.03 | 22 | Base: nfe, leiauteNFe v4.00, consulta de situação v4.00, inutilização, retorno de recibo, tipos básicos |
| | PL_010e v1.02 | 5 | Acrescenta indicador do local da operação, grupo de IBS/CBS ajustado e Suframa do emitente |
| | PL_010f v1.04 | 5 | Reorganiza o monofásico em quatro grupos |
| | PL_010g v1.03 | 8 | Vínculo de pagamento, valor líquido, ICMS previsto do pagamento antecipado; **só `mod` = 55** |
| | PL_010h v1.03 | 9 | Simples Nacional no IBS e na CBS, atividade do Simples, evento 412140 |
| CNPJ alfanumérico (NT 2026.004 v1.01) | PL_010d_NT2026.004, PL_Evento, CadConsultaCadastro | 11 + 7 + 4 | Variante da 010d, do envelope de eventos e da consulta de cadastro com o CNPJ alfanumérico |
| Serviços | PL_NFeDistDFe_104 | 5 | Distribuição de DF-e v1.01 (`distDFeInt`, `retDistDFeInt`, `resNFe`, `resEvento`) |
| | ConSitNFe v2.01 | 5 | Consulta de situação antiga (a ativa é a v4.00 da 010d) |
| | PL_ConsultaGTIN v1.00 | 4 | **Consulta de GTIN no CCG (novo serviço)** |
| Eventos | Eventos_RTC | 17 | 112110 a 112150, 211110 a 211150, 212110, 212120, 412120, 412130 e o cancelamento de evento 110001 |
| | Cancelamento (duas versões), substituição, carta de correção, EPEC (55 e NFC-e), ator interessado, entrega, insucesso, manifestação, genérico | 8, 8, 8, 8, 8, 4, 8, 14, 15, 11, 6 | Eventos 110111, 110112, 110110, 110140, 110150, 110130 e 110131, 110192 e 110193, 2102xx e o envelope genérico |
| | Econf, averbação, prorrogação (industrialização), Suframa (vistoria e internalização) | 14, 8, 15, 7 + 7 | 110750 e 110751, 790700, 111500 a 111503 e 411500 a 411503, 990900 e 990910 |

## 2.2 PDFs

| **Arquivo** | **Versão** | **Já tenho versão mais nova?** |
|---|---|---|
| Manual de Orientação do Contribuinte (MOC) | 6.0, setembro de 2015 | Sim: o MOC 7.0 (novembro de 2020), que é a base desde o documento 232 |
| NT 2020.001, manifestação do destinatário (2 cópias iguais) | v1.00, janeiro de 2020 | Sim: v1.60 |
| NT 2020.001 | v1.20, março de 2022 | Sim: v1.60 (prazo de 90 dias, documento 232) |
| NT 2023.004, ECONF (2 cópias iguais) | v1.00, dezembro de 2023 | Sim: v1.20 |
| NT 2023.005, insucesso na entrega (3 cópias iguais) | v1.00, dezembro de 2023 | Sim: v1.02 |
| NT 2021.001, comprovante de entrega (2 cópias iguais) | v1.01, julho de 2022 | **Não tenho outra:** é a versão que o dicionário usa (campos conferidos na seção 5) |
| NT 2010.008, carta de correção | v1.00, setembro de 2010 | Histórica; o esquema do evento 110110 v1.00 é o atual |

Li a capa, o controle de versões e o sumário de cada um, e o histórico de alterações das NT 2020.001. **Não comparei cada regra de validação dessas versões antigas**: as regras em vigor vêm das versões mais novas que já analisei nos documentos 232 e 233.

# 3. Como comparei, e o que isto não prova

Montei um leitor de XSD que resolve tipos, grupos e elementos nomeados e achata cada pacote em caminhos, com cardinalidade, tipo-base, enumeração, padrão, tamanhos, dígitos e valor fixo. Com isso fiz três comparações. **Versões entre si:** diferença de caminhos, enumerações, tamanhos e padrões entre a 010d, 010e, 010f, 010g, 010h e a variante de CNPJ alfanumérico. **Contra o dicionário:** procurei cada tag nova no texto dos campos e nas notas das entidades (`model_r52`) e conferi a decisão registrada (documentos 34, 163, 170, 232 e 234). **Tamanhos:** nos **210 campos** do dicionário que citam o caminho do leiaute, o tamanho declarado bate com o `maxLength` do esquema: **0 divergências**.

**O que a comparação não prova.** (a) Cobertura aqui significa que existe campo ou regra com o mesmo sentido; não revisei a regra de cálculo de cada campo. (b) A cardinalidade (obrigatório ou opcional) foi conferida só nos grupos novos e nos eventos; nos 1.130 caminhos não fiz a conferência campo a campo, porque o dicionário guarda o que a autoridade devolve e a obrigatoriedade condicional fica no Motor. (c) Os esquemas dão a forma, não o significado: o texto de cada NT é que diz quando o campo vale. (d) Não tenho o pacote da NFC-e (Q241-1).

# 4. Leiaute da NF-e: de PL_010d a PL_010h

## 4.1 O que mudou em cada versão

| **Passo** | **Novos** | **Removidos** | **Alterações** |
|---|---|---|---|
| 010d → 010e | 16 | 1 (`IS/pISEspec`) | Enumerações: `tpImp` 0 a 6, `tpNFCredito` 01 a 06, `tpEnteGov` 1 a 6, `tpOperGov` 1 a 4 |
| 010e → 010f | 59 | 23 (monofásico antigo) | O monofásico sai de um grupo único para **quatro grupos**: `gIBSMonoAdRem`, `gIBSMonoAdValorem`, `gCBSMonoAdRem` e `gCBSMonoAdValorem`, cada um com padrão, retenção, retido anteriormente e diferença do biocombustível; `emit/IE` passa a opcional |
| 010f → 010g | 12 | 0 | `vUnComLiq`, `vProdLiq`, `vProdLiqTot`, `ICMSPrevistoPagtoAntecip`, `gPgtoVinc`; `ide/mod` só 55; tamanhos de CNPJ, CPF, IE e chaves liberados (CNPJ alfanumérico) |
| 010g → 010h | 12 | 0 | `emit/tpRegimeIBSCBS`, `det/prod/cAtivSN`, `gTribSN` no item e no total |
| 010d → 010d_CNPJ | 4 | 0 | `enderDest/UF`, `cPais`, `xPais`, `fone`; `CEP` só 8 dígitos; `xLgr`, `xBairro` e `xMun` do destinatário de 1 a 255 para **2 a 60**; padrão do QR Code aceita CNPJ alfanumérico |

## 4.2 Cobertura das tags novas (010d → 010h)

| **Tag(s) novas** | **Onde o dicionário guarda** | **Situação** |
|---|---|---|
| `ide/cIndOp` | `Id_Indicador_Operacao` na nota (6 dígitos, `Cad_Indicador_Operacao`) | Coberto |
| `gCompraGov/refDFeAnt` (0 a 99 chaves) | `Mov_Nota_Fiscal_Saida_Referenciada` (documento 232) | Coberto |
| `emit/ISUFEmit` | `Cad_Habilitacao_Suframa.ID_Participante_Inscricao` (inscrição Suframa do emitente) | Coberto |
| `enderDest/UF`, `cPais`, `xPais`, `fone` | `Cad_Participante_Endereco` (país por `ID_Pais`) | Coberto; só limites de tamanho (seção 4.4) |
| `IS/adRemIS` (e a saída do `pISEspec`) | `Mov_Apuracao_Tributo_Item.Forma_Tributacao` = `especifica_por_unidade` com `Valor_Especifico_Unidade` | Coberto: é só a troca de nome |
| `gDevTrib/pDevTrib` (IBS UF, IBS município e CBS) | Complemento `devolucao_tributo` (`Percentual`) | Coberto |
| `gALCZFMCBS` (5 tags) | Complemento `aliquota_zero_cbs_zfm` (`Codigo_Classificacao`, `Numero_Processo`, `Percentual`, `Valor`) | Coberto; o texto de `Valor` cita `vTribReg` e não `vTribRegCBS` (Q241-8) |
| `gIBSMonoAdRem` e `gCBSMonoAdRem`: padrão, retenção, retido anteriormente (`qBCMono`, `adRem…`, `v…Mono…`) | Complementos `monofasia_padrao`, `monofasia_retencao`, `monofasia_retida_anteriormente` (`Quantidade`, `Valor_Especifico_Unidade`, `Valor`); alíquota em `Cad_Aliquota_Combustivel` | Coberto. A divisão em IBS e CBS separados cai bem em "uma linha por item e tributo" |
| `gMonoDif` removido na 010f | `Cad_Cclasstrib.Indicador_Mono_Dif` já está marcado como excluído desde a IT v1.60 (D-N465) | Coberto |
| `gIBSMonoAdValorem` e `gCBSMonoAdValorem`: padrão, retenção, retido (`vBCMono`, `pAliqMonoUF`, `pAliqMonoMun`, `pAliqMonoCBS`, `vIBSMonoUF`, `vIBSMonoMun`, `vCBSMono`…) | A forma ad valorem cabe em `Forma_Tributacao` = `ad_valorem` com `Base_Calculo`, `Percentual` e `Valor`, **mas o IBS no monofásico ad valorem traz alíquota e valor de UF e de município, e o complemento tem um só `Percentual` e um só `Valor`** | **Lacuna** (Q241-7) |
| `gpBioDiferenca` (`qBCBioComb`, `vIBSDiferenca`, `vCBSDiferenca`; 4 grupos) | Só a marca `Cad_Cclasstrib.Indicador_Grupo_Biocombustivel_Diferenca`; o documento 161 deixou a regra para quando a NT fosse lida | **Lacuna** (Q241-6) |
| `det/prod/vUnComLiq`, `vProdLiq`, `total/vProdLiqTot` | `Valor_Unitario_Liquido`, `Valor_Total_Liquido` (total derivado) | Coberto |
| `ICMSPrevistoPagtoAntecip/vICMSPrevisto` | Complemento `icms_previsto_pagamento_antecipado` | Coberto |
| `gPgtoVinc` (`nPag`, `idTransacao`, `tpMeioPgto`, `CNPJReceb`, `CNPJBasePSP`) | `Mov_Dfe_Vinculo_Pagamento` | Coberto; dois pontos de texto e de obrigatoriedade (Q241-8) |
| `emit/tpRegimeIBSCBS` | Derivado de `Cad_Simples_Opcao`, `Excesso_Sublimite` da filial e `Cad_Participante_Regime_Ibs_Cbs` (Q163-1) | Coberto, sem campo |
| `det/prod/cAtivSN` | `Mov_Nota_Fiscal_Saida_Item.ID_Atividade_Simples` (Q163-2) | Coberto |
| `gTribSN` no item e no total | Complemento `ibs_cbs_simples_nacional`; o total é derivado | Coberto |

**Os 99 novos:** 87 cobertos e 12 sem estrutura (os 12 caminhos de `gpBioDiferenca`: 4 grupos de 3). A forma ad valorem do monofásico (Q241-7) está entre os 59 da 010e → 010f; seus campos cabem no complemento, com a ressalva da divisão UF e município, e por isso a contei como coberta em estrutura e aberta em detalhe.

## 4.3 Enumerações e tamanhos

As cinco enumerações que mudaram entre a 010d e a 010h já estão no dicionário: `tpImp` = 6 (DANFE Simplificado Tipo 2, NT 2026.002), `tpNFCredito` com 6 tipos, `tpEnteGov` de 1 a 6, `tpOperGov` de 1 a 4 e `mod` = 55. Os 37 tamanhos que mudaram são, na maior parte, a retirada do limite de 14 e 44 posições de CNPJ, CPF, IE e chaves (CNPJ alfanumérico), sem efeito no modelo (revisão 41).

## 4.4 Endereço do destinatário (CNPJ alfanumérico)

No esquema de CNPJ alfanumérico, `enderDest/xLgr`, `xBairro` e `xMun` ficam de **2 a 60** caracteres (antes 1 a 255) e o CEP só com 8 dígitos. O dicionário guarda `Logradouro`, `Bairro` e a cidade como texto sem tamanho. **Sem campo novo:** a validação de tamanho é do Motor, antes da assinatura. Registro aqui só para que a regra não passe batida.

# 5. Eventos

## 5.1 Códigos

O conjunto de esquemas traz **44 esquemas de evento**: os 43 códigos do documento 232 (47 linhas do catálogo, Q232-8, aplicada na revisão 49) mais o 790700 (averbação), que já estava na carga. **Nenhum código novo e nenhum código do catálogo sem esquema**, com duas observações:

- O **211120** aparece na lista do cancelamento de evento (`e110001`), mas não tem esquema próprio; o documento 232 já o tinha como eliminado.
- Os códigos **420110 a 420170** só aparecem na lista do `e110001` das PL_010g e PL_010h. Nenhum esquema os define, apesar de você ter dito que o conjunto é o ativo inteiro. **A Q232-9 continua aberta.** Leitura minha: os esquemas ainda não foram publicados.

## 5.2 Campos do detalhe do evento (`detEvento`)

Conferi os campos de cada evento. Os campos genéricos (`cOrgaoAutor`, `tpAutor`, `verAplic`) são do cabeçalho do evento e saem de `Papel_Autor`, da UF da autoridade e da versão da aplicação. Os de domínio próprio estão em `Mov_Dfe_Evento`, `Mov_Dfe_Evento_Item`, `Mov_Dfe_Evento_Pagamento`, `Mov_Dfe_Evento_Adquirente` e `Mov_Dfe_Evento_Simples_Item`. Ficaram **quatro pontos sem lugar**:

| **Evento** | **Campos no esquema** | **No dicionário** | **Pergunta** |
|---|---|---|---|
| 990900 e 990910 (vistoria e internalização na Suframa) | `PINe` (1 a 9 dígitos), `dVistoria`, `locVistoria` (5 a 60), `postoVistoria` (5 a 60), `xHistorico` (1 a 1.024) | `dVistoria` cabe em `Data_Hora_Fato` e `xHistorico` em `Justificativa`; **`PINe`, `locVistoria` e `postoVistoria` não têm campo** | Q241-3 |
| 411500 a 411503 (resposta do Fisco à prorrogação) | `statPrazo` (0 ou 1), `respPedido`, `statPedido`, `justStatus` (1 a 8, ou 1 a 5 no cancelamento), `justStaOutra` (até 1.000), `statCancPedido` | `statPedido` em `Situacao_Pedido_Item`; `idPedido` em `ID_Evento_Referenciado`; **`statPrazo` não existe**; `Justificativa_Status` mistura o código e o texto livre | Q241-4 |
| 110130 e 110192 (entrega e insucesso) | `dhHashComprovante` e `dhHashTentativaEntrega` (opcionais): data e hora da geração do hash | `Hash_Comprovante` existe; **a data e hora do hash não** | Q241-5 |
| 110750 (ECONF) e 110300 (vínculo) | `detPag` completo; `gPgto` com `CNPJReceb` e `CNPJBasePSP` | Cobertos (`Mov_Dfe_Evento_Pagamento` e `Mov_Dfe_Vinculo_Pagamento`); ver Q241-8 | Q241-8 |

Os demais eventos (cancelamento, substituição, carta de correção, EPEC 55 e NFC-e, ator interessado, manifestação, comprovante de entrega, averbação e os da RTC, inclusive o 412140) estão cobertos. O EPEC da NFC-e traz só `vICMS` (sem `vST`). Os dados do EPEC (destinatário, valor da nota, ICMS) não ficam no evento: saem da própria nota (leitura minha).

# 6. Serviços de consulta

| **Serviço** | **Esquema** | **Dicionário** | **Situação** |
|---|---|---|---|
| Distribuição de DF-e | `distDFeInt` v1.01: `tpAmb`, `cUFAutor`, CNPJ ou CPF, e três modos: `distNSU/ultNSU`, `consNSU/NSU`, `consChNFe/chNFe`; retorno com `ultNSU`, `maxNSU`, `docZip` (NSU e schema), `resNFe` e `resEvento` | `Mov_Dfe_Distribuicao` e `_Nsu` guardam `Ultimo_Nsu`, `Maior_Nsu`, o NSU de cada documento e o retorno; `Modo_Consulta` tem só `por_nsu` e `por_periodo_pagina` | Coberto, **faltam os modos de consulta por NSU único e por chave** (Q241-5) |
| Consulta de situação | v4.00 (PL_010d): `consSitNFe`, `retConsSitNFe` com protocolo, eventos | Coberto (documentos 34 e 232) | A v2.01 do pacote ConSitNFe é antiga e não muda nada |
| Inutilização | `inutNFe` v4.00: ano, CNPJ, modelo, série, número inicial e final, `xJust` | `Mov_Dfe_Inutilizacao` (série, faixa, justificativa, protocolo); o ano sai da data do pedido | Coberto |
| Consulta de cadastro (CCC) | `consCad` v2.00 com CNPJ alfanumérico | `Mov_Consulta_Cadastro_Externo`, `Fonte` = `contribuinte_icms` (revisão 50) | Coberto |
| **Consulta de GTIN no CCG** | `consGTIN` (GTIN de 6 a 14 dígitos) e `retConsGTIN`: `tpGTIN` (8, 12, 13 ou 14), `xProd` (2 a 500), `NCM`, `CEST` (até 3) | **Nada.** O dicionário tem o GTIN no produto e o prefixo GS1, mas não a consulta ao cadastro | **Lacuna** (Q241-2) |

# 7. Lacunas e divergências

| **#** | **Achado** | **Tipo** | **Pergunta** |
|---|---|---|---|
| 1 | Pacote de esquemas da NFC-e (modelo 65) | Material que falta | Q241-1 |
| 2 | Consulta de GTIN no CCG | Lacuna (serviço novo) | Q241-2 |
| 3 | Campos dos eventos Suframa (`PINe`, local e posto da vistoria) | Lacuna | Q241-3 |
| 4 | Resposta do Fisco à prorrogação (`statPrazo`; código da justificativa) | Lacuna | Q241-4 |
| 5 | Data e hora do hash nos eventos de entrega e insucesso; distribuição por NSU único e por chave | Lacuna | Q241-5 |
| 6 | Diferença do biocombustível no monofásico | Lacuna (a regra dependia da NT) | Q241-6 |
| 7 | Monofásico ad valorem: IBS com UF e município | Lacuna de detalhe | Q241-7 |
| 8 | `Numero_Pagamento` diz 1 a 99 e o esquema aceita até 990; `CNPJReceb` e `CNPJBasePSP` obrigatórios no esquema, opcionais na tabela; texto de `vTribRegCBS` | Divergência de texto | Q241-8 |

Fora essas, **0 divergências de tamanho** (210 campos conferidos) e as 5 enumerações que mudaram entre a 010d e a 010h já estão no dicionário.

# 8. Perguntas para você

| **Id** | **Pergunta** | **Recomendação** |
|---|---|---|
| Q241-1 | Enviar o **pacote de esquemas ativo da NFC-e** (modelo 65)? A PL_010g e a PL_010h só aceitam `mod` = 55; a NFC-e deve ter pacote próprio ou continuar na PL_010f. Sem ele não consigo conferir QR Code v3, `gPgtoVinc` e os campos de IBS e CBS da NFC-e | **Sim**, quando puder (e informar se a NFC-e segue na PL_010f) |
| Q241-2 | Guardar a **consulta de GTIN no CCG**? Proposta: novo valor `ccg_gtin` em `Mov_Consulta_Cadastro_Externo.Fonte`, o GTIN em `Chave_Consultada` (cabe: até 14) e o retorno (`tpGTIN`, `xProd`, `NCM`, `CEST`) em `Mov_Consulta_Cadastro_Externo_Campo`. **0 campos novos** | **Sim** |
| Q241-3 | Eventos **Suframa 990900 e 990910**: +3 campos em `Mov_Dfe_Evento` (`Numero_Pin_E`, código até 9; `Local_Fato`, texto; `Posto_Fato`, texto); `dVistoria` vai em `Data_Hora_Fato` e `xHistorico` em `Justificativa`. O `PINe` (protocolo de internalização) tem o mesmo formato do PIN que o CT-e já guarda em `Pin_Suframa`; mantenho separado porque o PIN-e é do evento (leitura minha) | **Sim** |
| Q241-4 | **Resposta do Fisco à prorrogação (411500 a 411503):** +1 campo em `Mov_Dfe_Evento` (`Prazo_Cumprido`, booleano, para `statPrazo`) e +1 em `Mov_Dfe_Evento_Item` (`Codigo_Justificativa_Status`, código até 1, para o `justStatus`); `Justificativa_Status` passa a guardar só o `justStaOutra`. Na resposta ao cancelamento do pedido, `statCancPedido` vai em `Indicador_Aceite` (deferido = verdadeiro, leitura minha) e o `justStatus` em `Codigo_Motivo` | **Sim** |
| Q241-5 | **(a)** +1 campo em `Mov_Dfe_Evento` (`Data_Hora_Hash`, data e hora, opcional) para `dhHashComprovante` e `dhHashTentativaEntrega`; **(b)** em `Mov_Dfe_Distribuicao`, +2 valores em `Modo_Consulta` (`por_nsu_unico` e `por_chave`) e +1 campo `Chave_Consultada` (código 44, opcional) para o `consChNFe`. O `cUFAutor` sai da UF da filial, sem campo. **+2 campos** | **Sim** |
| Q241-6 | **Diferença do biocombustível (`gpBioDiferenca`):** +1 valor em `Mov_Apuracao_Tributo_Item_Complemento.Tipo_Complemento` (`monofasia_diferenca_biocombustivel`), com `Quantidade` = `qBCBioComb` e `Valor` = `vIBSDiferenca` ou `vCBSDiferenca`; o percentual obrigatório de comparação vem de `Cad_Combustivel_Mistura_Obrigatoria`. **0 campos novos.** A regra de quando o grupo é exigido segue na marca do classificador; o texto da NT 2025.002 sobre o cálculo ainda não foi lido | **Sim** |
| Q241-7 | **Monofásico ad valorem (010f):** no IBS o esquema traz alíquota e valor da UF e do município. Proposta: +2 campos no complemento (`Percentual_Municipio` e `Valor_Municipio`), com `Percentual` e `Valor` ficando para a UF, e a CBS usando só os campos atuais. Hoje `Cad_Aliquota_Combustivel` só tem alíquota por unidade, então **o dicionário só guarda o que vem no XML** (nota recebida e conferência), sem regra de cálculo ad valorem | **Sim**, só para guardar o que chega; o cálculo fica para quando houver fonte legal |
| Q241-8 | **Três acertos de texto, sem campo:** (a) `Mov_Dfe_Vinculo_Pagamento.Numero_Pagamento`: o `nPag` aceita **1 a 990** (o grupo repete de 1 a 99 vezes); (b) `Cnpj_Recebedor` e `Cnpj_Base_Psp` são **obrigatórios** no esquema da nota e do evento 110300; manter **opcionais na tabela** (guarda o que chega) e obrigatórios na regra do Motor na emissão; (c) o texto de `Valor` do complemento passa a citar `vTribRegCBS` ao lado de `vTribReg` | **Sim** |

## Contagem se tudo for aprovado

| **Medida** | **Revisão 52** | **Com a Q241** |
|---|---|---|
| Entidades | 1.242 | **1.242** (0) |
| Campos | 14.439 | **14.448** (+9: Q241-3 +3, Q241-4 +2, Q241-5 +2, Q241-7 +2) |
| Referências | 3.703 | 3.703 (0) |
| Domínios | 374 | 374 (0; os valores novos são de enumerações dentro das entidades) |
| DDL (comentários e comandos do T-SQL) | 12.180 e 21.718 | +9 e +9 (esperado; confirmo ao consolidar) |

**Para o contador:** nada novo.

# 9. Limites

- **Não recebi texto novo de NT neste envio:** os 12 PDFs são versões antigas. As NT de 2026 e a 2025.002 v1.53 foram lidas nos documentos 163, 170 e 232; os esquemas mostram a forma, não o momento em que cada regra vale.
- Os esquemas dos eventos 420110 a 420170 e o texto do monofásico ad valorem continuam sem fonte.
- A lista de esquemas ativos veio de você; não consegui conferir a página da Receita (o `robots.txt` bloqueia a leitura automática, e respeitei).
- As contagens da seção 4 vêm do leitor de XSD: contam grupos e campos, não folhas, e por isso não se comparam com os 923 campos do documento 34 (que contou a PL_010f de outro modo).

# 10. Em aberto

**Com você:** Q241-1 a Q241-8 (esta lista), Q232-9, Q234-3, Q228-1, Q228-2, Q239-4 e as demais já listadas no documento 38. **Do contador:** nada novo. **Da equipe:** nada novo.
