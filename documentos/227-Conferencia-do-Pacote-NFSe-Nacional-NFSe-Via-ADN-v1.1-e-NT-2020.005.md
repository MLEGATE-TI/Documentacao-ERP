# Conferência do Pacote da NFS-e Nacional, a NFS-e Via, o ADN v1.1 e a NT 2020.005 da NF-e — Documento 227

*Você enviou o pacote da NFS-e Nacional (oito manuais, os anexos A a V, dois pacotes de schemas), os schemas da NFS-e Via e a Nota Técnica 2020.005 da NF-e, sem texto, e escolheu o "documento 227 completo". Conferi tudo contra o dicionário (revisão 46) e contra os documentos 34 e 41. **O achado principal é a NFS-e Via**, que o documento 34 deixou fora do escopo e agora tem schema; o resto confirma o que já estava desenhado, com uma mudança real no ADN (consulta por procuração). **Situação em 16/11/2026: aplicado na revisão 47** (documento 229, D-N597), depois das suas respostas (Q227-1 a Q227-5, D-N595) e do "consolidar". O texto abaixo é o desenho como foi proposto; a revisão 3, logo abaixo, traz o que a consolidação corrigiu.*

Mlegate · Alberto Beyeler · Novembro de 2026

**Revisão 2 (16/11/2026): leitura da NT 010.** Depois de aprovar as Q227-1 a Q227-5 (D-N595) você pediu "ler o NT 010". A NT 010 não estava no ambiente, então li a versão oficial publicada no portal da NFS-e do Comitê Gestor (SE/CGNFS-e nº 010, versão 1.00, de **11/09/2026**) e o **Manual para Emissão da NFS-e Via v1.0**. **A NT 010 é curta: traz só duas mudanças**, o código 6 ("Sem cobrança") em `modPagamento` (leiaute da NFS-e Via v1.01) e o leiaute do evento de **manifestação do adquirente**. Os dois confirmam o que o schema já dizia (domínio de `modPagamento` com 6 valores, os 9 motivos de rejeição, `xMotivoRejeita` de 15 a 55 caracteres), **não mudam o desenho aprovado** e respondem em parte ao limite da seção 9. O que ainda falta (como o adquirente recebe a nota, prazos, tributação, chave, cronograma, erros) está em documentos que **não** li: Manual v1.02, Anexo IV (planilha de leiautes e regras) e os guias de API. Ver a seção 3.6.

**Revisão 3 (16/11/2026): consolidação.** Ao aplicar o desenho na revisão 47 conferi quatro afirmações deste documento e três estavam imprecisas: (1) **não há linha nova de `Cad_Modelo_Documento_Fiscal`**: o modelo `NFSE_VIA` já entrou na `Carga45`; os eventos da `Carga47` usam esse modelo; (2) **`Cad_Cclasstrib_Modelo` não trazia "fora do escopo"**: só `Aplica_Nfse_Via` em `Cad_Indicador_Operacao` trazia, e o texto saiu; (3) os **15 códigos do ADN** tiveram o texto oficial lido no Manual v1.1 (estava no ambiente); o **E2243** diz "o CNPJ informado na consulta deve ter o mesmo CNPJ base", o que **não** é a "outra raiz" que a seção 4 escreveu e não combina com a consulta mediante procuração do mesmo manual (a dúvida virou a Q228-2); (4) o motivo do cancelamento (2, serviço não prestado) e o da substituição (1, erro na emissão) vêm do schema, e os eventos levam assinatura. O valor "recibo de passagem veicular" em `Origem_Dados_Entrada` (seção 3.6) **não foi aplicado**: não foi aprovado (Q229-2). A Q227-4 ficou como a seção 5 a descreveu: os 8 campos foram buscados por nome no modelo e nenhum existia.

# 1. Resumo

| Fonte | O que traz | Efeito no dicionário |
|---|---|---|
| **Schemas da NFS-e Via v1.01** (zip "atualizado": NFSeVia, EventoVia, ProcNFSeVia, ProcEventoVia e três tipos) | Documento de passagem em via com pedágio: 21 campos próprios (placa, categoria do veículo, sentido, praça, quilometragem, modalidade de passagem e de pagamento), valores fixos de serviço e quatro eventos (cancelamento, cancelamento por substituição, manifestação do adquirente com aceite e com rejeição) | **Novo.** Proponho desenhar só o lado do adquirente: 1 entidade, 3 domínios, 4 tipos de evento e 11 motivos (Q227-1 e Q227-3) |
| **Manual do ADN v1.1** (03/11/2026) | O `GET /DFe/{NSU}` ganha a consulta do próprio contribuinte, por CNPJ do mesmo CNPJ base e **mediante procuração**; resposta com `TipoConsulta`; erros E2243 a E2247 | **Lacuna real:** `Mov_Dfe_Distribuicao` não guarda de quem é a consulta nem a procuração (Q227-2) |
| **NT 2020.005 v1.20** (06/2021) | Campos que a NF-e 4.00 já tem: `cBarra`, `cBarraTrib`, ICMS-ST desonerado, FCP diferido e efetivo, `indSomaPISST` e `indSomaCOFINSST` | Não achei no dicionário (Q227-4); falta confirmar contra a planilha do documento 34, que não está neste ambiente |
| **XSD da NFS-e Nacional v1.01 (09/02/2026)** e Anexos I a V | Mesmo conteúdo que o documento 41 já analisou; o pacote de 09/02 é o **antigo**, superado pelo de 27/07/2026 | Nada muda. As dúvidas Q-1 a Q-15 do documento 41 continuam abertas (Q227-5) |
| **NT 2013/005 v1.10 e v1.22** (reenvio) | `pot` do `veicProd` só em CV | Fecha a C258 com fonte oficial do layout 3.10 (seção 6) |
| Demais manuais | Versões já conhecidas ou cópias idênticas (seção 2) | Nada |

# 2. Fontes lidas

| Arquivo | Versão e data | Situação |
|---|---|---|
| `schemas_v1-01_atualizado.zip` | NFS-e Via v1.01; 8 XSD | **Novo.** Não existe no pacote de 09/02 nem no de 27/07 |
| `nfse-esquemas_xsd-v1-01-20260209.zip` | NFS-e Nacional v1.01 de 09/02/2026 (pastas 1.00 e 1.01) | **Antigo**: `TSCNPJ` só aceita `[0-9]{14}` e a série da DPS tem o padrão quebrado. O de 27/07/2026 (documento 41, revisão 2) corrige os dois |
| Anexo I (DPS e NFS-e) | v1.01, 09/02/2026 | 416 linhas de leiaute e 428 códigos de regra: **os mesmos números** do documento 41 |
| Anexo II (pedido de registro de evento) | v1.01, 22/01/2026 | 16 tipos de evento da NFS-e |
| Anexos III (CNC), IV (ADN), V (painel municipal) | v1.00, 16/12/2025 | Sem mudança. O Anexo IV traz os erros E2215, E2230, E2240 e E2241, mas **não** os E2243 a E2247 |
| Anexo A (municípios e países), B (NBS e lista nacional), C (cIndOp) | v1.00 de 10/12/2025; v1.01 de 22/01/2026; v1.01 | O Anexo C tem **26 códigos** de seis dígitos, os mesmos do documento 41 |
| Manual do ADN | **v1.1, 03/11/2026**; o arquivo sem versão no nome é a v1.0 de 12/02/2026 | **v1.1 é nova**: ver seção 4 |
| Manual dos Contribuintes (Emissor Público Nacional) v1.2 e Manual dos Municípios (Emissor Público e CNC) v1.2 | v1.0 de 17/03/2025 e 25/03/2025, com revisões de outubro de 2025 | Já conhecidos |
| Manual da emissão por decisão administrativa ou judicial | v1.0, 26/01/2026; **enviado duas vezes** (mesmo hash) | A nota sai com `cStat` 102 e o contribuinte envia a NFS-e completa. `Mov_Nfse_Decisao` já cobre a decisão cadastrada pelo município; não conferi campo a campo |
| NT 2020.005 (regras de validação da NF-e) | v1.20, 06/2021 | Seção 5 |
| NT 2013/005 | v1.10 (2014) e v1.22 (2015); a v1.22 já era conhecida (mesmo hash) | Seção 6 |

**A NT 010 e o manual da NFS-e Via não estavam neste ambiente** na primeira versão deste documento; a revisão 2 (16/11/2026) os leu no portal oficial (seção 3.6). O que continua de fora: o guia de manifestação do adquirente citado no documento 41, o Manual v1.02, o Anexo IV e os guias de API.

# 3. NFS-e Via

## 3.1 O que o schema diz

A NFS-e Via é o documento da **exploração de via**: a concessionária emite uma nota por passagem do veículo em uma praça de pedágio. O schema é bem menor que o da NFS-e Nacional: um fornecedor (a concessionária), um serviço e um bloco de valores.

| Grupo | O que guarda |
|---|---|
| Cabeçalho (`infNFSeVia`) | Ambiente, versão da aplicação, situação `cStat` (100 NFS-e Via, 101 substituição, 102 decisão judicial), data da emissão, data da competência (a passagem), `subst` (chave substituída, motivo 03, 04, 06, 07 ou 99) |
| `fornec` | CNPJ (alfanumérico), nome, município do fornecedor |
| `serv` | Local da operação (o **trecho**), a **praça** (código, nome, quilometragem, município), número (13 dígitos) e série (3), e o grupo `explVia` |
| `explVia` | Categoria do veículo (00 a 12 e 99), **sentido** (0 a 359 graus), **placa**, **código de acesso** de 17 caracteres, modalidade de passagem (1 a 5), código do contrato (4) e informação complementar |
| `valores` | Valor do serviço, **modalidade de pagamento** (1 a 6), descontos, ISSQN (base, alíquota, valor), PIS e COFINS e **IBS e CBS** (base, líquido, total, IBS da UF e do município, CBS) |

No schema atual o código de tributação nacional (`220101`), a NBS (`106042100`), o CST do IBS e da CBS (`000`), a classificação (`000002`) e o indicador da operação (`080101`) são **valores fixos**. Eu não interpretei o significado tributário deles: a pergunta vai ao contador (C362).

Os eventos são quatro: `101101` cancelamento (motivo 2), `105102` cancelamento por substituição (motivo 1 e chave da nota substituta), `203202` manifestação do adquirente **com aceite** e `203204` manifestação **com rejeição**. As duas manifestações trazem o tipo de identificação (CPF ou CNPJ), o documento e o nome do adquirente, e a rejeição leva um dos nove códigos (1 a 8 e 99: duplicidade, não ocorrência da passagem, data da passagem etc.).

## 3.2 O que o dicionário já cobre

O dicionário tem a base pronta, porque a NFS-e Via segue o mesmo padrão das demais notas de entrada: `Mov_Documento_Fiscal` (chave de 50 posições, protocolo, substituição, XML), `Cad_Modelo_Documento_Fiscal` (uma linha por modelo), `Cad_Dfe_Evento_Tipo` e `Cad_Dfe_Evento_Motivo` (eventos e motivos com vigência), `Mov_Dfe_Evento` (já tem `Documento_Autor`, `Indicador_Aceite`, `Codigo_Motivo` e `Justificativa`), `Cad_Veiculo_Transporte` (a placa é a identidade) e `Mov_Apuracao_Tributo_Item` (ISSQN, PIS, COFINS, IBS e CBS do item). O dicionário já tinha o valor "NFS-e Via" nas marcas por modelo da classificação tributária (`Cad_Cclasstrib_Modelo`) e `Aplica_Nfse_Via` em `Cad_Indicador_Operacao`, ambos marcados "fora do escopo".

## 3.3 O que falta

A passagem em si: placa, categoria, sentido, praça, trecho, modalidades e código de acesso não têm campo. Proponho **uma entidade de extensão** do documento fiscal, sem repetir o que o documento já tem.

**`Mov_Nfse_Via_Passagem`** (vigência: não): a passagem informada pela concessionária, uma por NFS-e Via.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| `ID_Nfse_Via_Passagem` | identificador | |
| `ID_Documento_Fiscal` | referência (`Mov_Documento_Fiscal`) | A NFS-e Via. O número (13 dígitos), a série (3), a chave e o protocolo ficam no documento fiscal |
| `ID_Veiculo_Transporte` | referência (`Cad_Veiculo_Transporte`, opcional) | Veículo da empresa, achado pela placa; vazio quando a placa não é de veículo cadastrado. É o que permite apropriar o pedágio por veículo e por ativo |
| `Placa` | código (até 10) | `explVia/placa`, como informada |
| `ID_Categoria_Veiculo` | referência (`Cad_Classe_Sistema`, domínio = `categoria_veiculo_via`) | `categVeic`: 00 a 12 e 99 |
| `Sentido_Graus` | número | `sentido`: ângulo a partir do norte, 0 a 359 |
| `Codigo_Acesso_Pedagio` | código (17) | `codAcessoPed`: identifica a nota para o adquirente |
| `ID_Modalidade_Passagem` | referência (`Cad_Classe_Sistema`, domínio = `modalidade_passagem_via`) | `modPassagem`: 1 fluxo livre, 2 manual, 3 automático, 4 semiautomático, 5 outros |
| `ID_Modalidade_Pagamento` | referência (`Cad_Classe_Sistema`, domínio = `modalidade_pagamento_via`) | `modPagamento`: 1 débito, 2 crédito, 3 dinheiro, 4 eletrônico, 5 posterior, 6 sem cobrança |
| `Codigo_Contrato` | código (4) | `codContrato` |
| `Codigo_Praca` | código (7) | `cPracaEmi` |
| `Nome_Praca` | texto (150) | `xPracaEmi` |
| `Km_Praca` | número | `kmPracaEmi`, até 6 decimais |
| `ID_Municipio_Praca` | referência (`Cad_Municipio`) | `cLocEmi`: município da praça |
| `ID_Municipio_Trecho` | referência (`Cad_Municipio`) | `cLocOper`: local da operação, que para a exploração de via é o trecho da concessão |
| `Nome_Trecho` | texto (150) | `xLocOper`: nome do trecho no cadastro da concessionária |
| `Data_Hora_Passagem` | data e hora | `dhCompet` |
| `Situacao_Via` | enumeração {normal, substituicao, decisao_judicial} | `cStat` 100, 101 e 102 |
| `Informacao_Complementar` | texto, opcional | `xInfComp`, até 2.000 posições |
| `Codigo_Motivo_Substituicao` | código (2), opcional | `subst/cMotivo`: 03, 04, 06, 07 ou 99 |
| `Descricao_Motivo_Substituicao` | texto (255), opcional | `subst/xMotivo`; obrigatório no motivo 99 |

São **21 campos e 7 referências** (3 genéricas para `Cad_Classe_Sistema` e 4 diretas). Os valores de ISSQN, PIS, COFINS, IBS e CBS entram pelo item do documento fiscal e pela apuração do item, sem entidade nova; o CNPJ da concessionária vira o `ID_Participante_Emitente` do documento.

**Domínios novos (3):** `categoria_veiculo_via` (14 valores), `modalidade_passagem_via` (5) e `modalidade_pagamento_via` (6).

## 3.4 Eventos

Sem entidade nova. Entram como **cargas**: 1 linha em `Cad_Modelo_Documento_Fiscal` (NFS-e Via; **não li número de modelo oficial**, então o código fica provisório), 4 linhas em `Cad_Dfe_Evento_Tipo` (101101, 105102, 203202, 203204) e 11 linhas em `Cad_Dfe_Evento_Motivo` (cancelamento: 1; substituição: 1; rejeição: 9). Falta um campo: `Mov_Dfe_Evento` tem o documento do autor, mas não o **nome ou razão social** que a manifestação leva (`xRazaoSocial`, 2 a 60 caracteres): `Nome_Autor_Informado`, texto (60), opcional. O tipo de identificação (CPF ou CNPJ) se deduz do tamanho do documento.

## 3.5 Escopo que proponho

Só o **lado do adquirente**: receber a NFS-e Via, manifestar aceite ou rejeição, apropriar o custo por veículo e tomar o crédito do IBS e da CBS se o contador disser que cabe (C362). **Emitir** NFS-e Via (o papel da concessionária) fica fora, como no documento 34. Se algum cliente da Mlegate for concessionária, é um documento próprio.

## 3.6 O que a NT 010 e o manual dizem (revisão 2)

**NT 010 (SE/CGNFS-e, v1.00, 11/09/2026).** Duas atualizações: (a) o leiaute da NFS-e Via passa a **v1.01** com o valor 6 ("sem cobrança") em `modPagamento`, o mesmo que o schema já tem; (b) o leiaute do evento de **manifestação do adquirente** (códigos 203202, aceite, e 203204, rejeição, grupos mutuamente excludentes). O evento leva o tipo de identificação, o CPF ou CNPJ e o nome ou razão social do adquirente (2 a 60 caracteres); a rejeição leva o motivo (1 a 8 e 99) e uma explicação opcional de 15 a 55 caracteres. A nota cita o Manual para Emissão da NFS-e Via v1.02 e a planilha de leiautes e regras "LeiautesRN_ADN-SNNFSeVia_V1.00.04" (Anexo IV), que não li. **Não traz** prazos, quem pode manifestar, efeito da falta de manifestação, regras de validação, erros, cronograma, chave nem tributação.

**Os nove motivos de rejeição** (para a carga de `Cad_Dfe_Evento_Motivo`): 1 NFS-e Via em duplicidade; 2 não ocorrência da passagem do veículo; 3 data da passagem do veículo; 4 categoria do veículo; 5 placa do veículo; 6 valor do serviço; 7 modo de pagamento; 8 valor das deduções; 99 outros.

**Pequenas diferenças entre a NT 010 e o schema** (valem para a carga e para o desenho): a NT descreve o valor 1 de `modPagamento` como "débito **ou pix**" e o schema só como "débito" (a carga leva o texto da NT, com a nota da diferença); o código de motivo da rejeição chama-se `cMotivo` na NT e `cCodMotivoRejeicao` no schema (o dicionário usa `Codigo_Motivo`, sem efeito); `verAplic` do evento é opcional na NT (0-1) e obrigatório no schema (o ERP preenche sempre); o texto da NT tem erros de digitação evidentes ("CNPF", "Manifestaçao") e o tamanho de `CNPJCPF` escrito de dois jeitos (11 ou 14 no aceite, 11 a 14 na rejeição; o schema aceita CPF de 11 ou CNPJ alfanumérico de 14).

**Manual para Emissão da NFS-e Via v1.0** (guia do Portal de Gestão; a versão não tem data). Quem emite é a **concessionária de rodovia** (serviço 220101), com acesso restrito às cadastradas pelo Comitê Gestor. O manual **não define o adquirente**: fala em "usuário" e "tomador do serviço". O usuário recebe um **Recibo de Passagem Veicular (RPV)**, que **não é documento fiscal**, com os dados da passagem (data e hora, via, sentido, praça com código, município e quilômetro, série por equipamento e pista, modalidade da passagem, placa, categoria, número de eixos, valor pago e forma de pagamento, alíquotas e valores de ISS, CBS e IBS) e o link da **consulta pública** do DANFS-e Via, com a chave, por QR code ou endereço. O RPV diz que a **manifestação do tomador** no ambiente da NFS-e Via "pode gerar direito a crédito de impostos, conforme a lei", sem citar a norma. O manual não menciona API para o adquirente, consulta por placa nem distribuição por NSU, e não traz prazos, chave, valores fixos nem erros. A concessionária cadastra no portal o trecho (extensão em km), as praças (localização em km e município) e os municípios de abrangência com a extensão e a alíquota de cada um.

**Efeito no desenho aprovado:** nenhum campo muda. Dois reflexos: (1) como a única entrada documentada para o adquirente é o **RPV com a chave e a consulta pública**, `Origem_Dados_Entrada` de `Mov_Documento_Fiscal` (que já existe) recebe o valor "recibo de passagem veicular" quando o ERP registrar a nota pela chave lida do QR code; **proponho como leitura minha**, a confirmar quando o Manual v1.02 e o Anexo IV chegarem; (2) o RPV traz **número de eixos** e **nome da via**, que o schema da NFS-e Via não tem; não crio campo para eles, porque o dado fiscal é o do XML.

# 4. ADN v1.1: consulta por procuração

A v1.1 do manual (03/11/2026) reescreve o item `GET /DFe/{NSU}` e acrescenta o item 1.1.2 (mensagens de erro). A v1.0 de 12/02/2026 não tinha nem a consulta por procuração nem a lista de erros.

| Tipo de consulta | Como o ADN autoriza | `TipoConsulta` na resposta |
|---|---|---|
| Do próprio contribuinte | Sem `cnpjConsulta` nem `cpfConsulta`: devolve os documentos do titular do certificado | `InscricaoCertificado` |
| Mesmo CNPJ base | `cnpjConsulta` com 14 dígitos e os 8 primeiros iguais aos do certificado: sem procuração | `CnpjBase` |
| Mediante procuração | CNPJ de outra raiz ou CPF diferente do certificado: a inscrição consultada outorga procuração ao titular do certificado, **cadastrada no Portal de Serviços da Receita** | `Procuracao` |

Erros novos: **E2243** (CNPJ de outra raiz), **E2244** (CNPJ e CPF juntos), **E2245** (sem procuração: "Não há procuração da inscrição {0} para a inscrição {1}"), **E2246** e **E2247** (dígito verificador). A lista inclui também E2210 a E2214, E2220, E2230, E2240, E2241 e E999.

**Efeito:** o ERP de um escritório ou de um grupo com mais de uma raiz de CNPJ consulta documentos de outra inscrição. `Mov_Dfe_Distribuicao` tem o último NSU, o modo e o período, mas **não guarda de quem é a consulta, o tipo de autorização nem a procuração**. Sem isso o NSU de duas inscrições se mistura na mesma linha. Proponho 3 campos em `Mov_Dfe_Distribuicao`: `Documento_Consulta` (código até 14, opcional; vazio = próprio contribuinte), `Tipo_Consulta` (enumeração {inscricao_certificado, cnpj_base, procuracao}, opcional) e `ID_Procuracao` (referência `Cad_Procuracao`, opcional, o mesmo cadastro que o Integra Contador já usa). A carga de `Cad_Dfe_Codigo_Retorno` ganha os 15 códigos da seção 1.1.2 do manual (os que ainda não estiverem lá; **não conferi quais já foram carregados**).

# 5. NT 2020.005 (regras de validação da NF-e, v1.20)

A nota (junho de 2021) cria campos e regras para a NF-e 4.00. Os campos já estão no layout que o documento 34 conferiu (923 campos); a diferença é que **não achei por nome nenhum deles no dicionário (revisão 46)**:

| Campo | O que é | Onde caberia |
|---|---|---|
| `cBarra` e `cBarraTrib` (I03a e I12a) | Código de barras diferente do GTIN, da unidade comercial e da tributável (3 a 30 caracteres, sem validação) | `Mov_Nota_Fiscal_Saida_Item`: hoje só `Gtin` e `Gtin_Tributavel` |
| `vICMSSTDeson` e `motDesICMSST` (N33a e N33b) | Valor e motivo do ICMS-ST desonerado, nos grupos 10, 70 e 90 | `Mov_Apuracao_Tributo_Item`: tem `Valor_Desonerado` e `ID_Motivo_Desoneracao_Icms`, **só do ICMS próprio** |
| `pFCPDif`, `vFCPDif` e `vFCPEfet` (N17d a N17f) | FCP diferido (grupo 51): percentual, valor diferido e valor efetivo | `Mov_Apuracao_Tributo_Item`: sem campo de diferimento do FCP |
| `indSomaPISST` e `indSomaCOFINSST` (R07 e T07) | Se o PIS-ST e a COFINS-ST compõem o total da nota | Nenhum; entram na fórmula do total (W16) |

A mesma nota troca `cAgreg` para alfanumérico (o dicionário já tem `Codigo_Agregacao` como código de até 20, sem tipo numérico) e torna a UF da placa opcional (`ID_Estado_Placa` já é opcional). As regras de validação (rejeições novas) vão para `Cad_Dfe_Parametro_Regra` quando a emissão da NF-e for desenhada; **não as comparei uma a uma**.

Proposta (Q227-4): 8 campos novos: 2 em `Mov_Nota_Fiscal_Saida_Item` (`Codigo_Barras_Comercial` e `Codigo_Barras_Tributavel`, código de 3 a 30, opcionais) e 6 em `Mov_Apuracao_Tributo_Item` (`Valor_Desonerado_St`, `ID_Motivo_Desoneracao_St`, `Percentual_Fcp_Diferido`, `Valor_Fcp_Diferido`, `Valor_Fcp_Efetivo` e `Compoe_Total_Documento`, booleano opcional para PIS-ST e COFINS-ST). **Confirmar antes contra a planilha do documento 34**, porque ela pode já ter esses campos nas 37 lacunas ou nos 55 "a confirmar" da área do ICMS.

# 6. C258: a potência do veículo em kW

O reenvio da NT 2013/005 (v1.10, de 2014, e v1.22, de 2015; layout 3.10) fecha a C258 com fonte oficial: o campo J06 `pot` é "Potência Motor (CV)", "potência máxima do motor do veículo em cavalo vapor (CV)", de 1 a 4 caracteres, ocorrência 1-1. A tabela do `veicProd` (J01 a J17) é igual nas duas versões, e não há "kW" em nenhuma delas nem no Manual da NF-e. **O dicionário não muda** (`Veiculo_Potencia_Cv`). Limite: é o layout 3.10; **o XSD e o leiaute vigentes não foram lidos**, porque o site da Receita bloqueia a consulta automática. Isto complementa a seção 4 do documento 226.

# 7. Perguntas para você

| Id | Pergunta | Recomendação |
|---|---|---|
| Q227-1 | Desenhar a NFS-e Via só do lado do adquirente, com `Mov_Nfse_Via_Passagem` (21 campos, seção 3.3), os 3 domínios novos e a carga do modelo, tirando "fora do escopo" de `Aplica_Nfse_Via` e das marcas por modelo? | **Sim**, desenho provisório: tem só o schema, sem a NT 010 nem o guia de manifestação |
| Q227-2 | Acrescentar a `Mov_Dfe_Distribuicao` os campos `Documento_Consulta`, `Tipo_Consulta` e `ID_Procuracao`, e carregar os códigos de retorno E2243 a E2247 do ADN v1.1? | **Sim.** Sem eles o NSU de duas inscrições se mistura |
| Q227-3 | Carregar os 4 eventos da NFS-e Via (101101, 105102, 203202, 203204) e os 11 motivos, e criar `Nome_Autor_Informado` em `Mov_Dfe_Evento` para o nome da manifestação? | **Sim**, junto com a Q227-1 |
| Q227-4 | Abrir os 8 campos da NT 2020.005 (código de barras, ICMS-ST desonerado, FCP diferido e efetivo, composição do total pelo PIS-ST e COFINS-ST)? | **Sim**, depois de eu conferir contra a planilha do documento 34 (que preciso que você reenvie, se quiser que eu confirme agora) |
| Q227-5 | Mandar ao Comitê Gestor da NFS-e as dúvidas críticas do documento 41 (Q-3, sinal de `vAjusteBCIBSCBSComExt`; Q-5, caminho de `gIBSCBSAjuste`; `regApIBSCBSSN` = 2), já que este pacote não resolve nenhuma das Q-1 a Q-15? | **Sim**; redijo o texto, o envio é seu |

Para o contador entra uma pergunta nova no documento 188, a **C362**: na NFS-e Via o IBS e a CBS vêm com CST `000`, classificação `000002` e indicador `080101` fixos; o adquirente (empresa com frota) toma crédito de IBS e CBS do pedágio, e com que condição (uso e consumo, atividade, veículo)?

**Contagens se tudo for aprovado** (somar à revisão 46; a Q226 do documento 226, se também aprovada, soma mais 1 entidade, 9 campos, 5 referências e 1 domínio): entidades 1.239 para 1.240; campos 14.365 para 14.398 (+21, +3, +1, +8); referências 3.682 para 3.691 (+7, +1, +1); domínios 370 para 373; tabelas do DDL 1.505 para 1.506.

# 8. Como será aplicado e conferido

Quando você escrever "consolidar" (revisão 47): aplico o que aprovar pelo mesmo mecanismo das revisões anteriores, regero a extração, a normalização, a auditoria, o DDL (PostgreSQL 16 e T-SQL) e os diagramas, gero a carga (modelo, eventos, motivos, domínios e códigos de retorno) e confiro as contagens da seção 7, a execução do DDL e a auditoria sem achados.

# 9. Limites

- **A NFS-e Via vem dos schemas, da NT 010 (v1.00, 11/09/2026) e do Manual v1.0 do portal**, lidos como texto extraído de páginas do portal oficial (6.588 e 9.180 caracteres, sem o tamanho dos arquivos). **Não li** o Manual v1.02 (manifestação do adquirente), o Anexo IV (planilha de leiautes e regras) nem os guias de API: sem eles não sei **como o adquirente recebe a nota por sistema**, os prazos, o efeito da falta de manifestação, a regra de formação da chave, os erros nem o cronograma. Se você me enviar o Manual v1.02 e a planilha do Anexo IV, fecho esses pontos.
- **Não li o texto dos manuais campo a campo** (só o histórico de versões, o item de consulta e os erros do ADN v1.1; o resumo e os campos-chave da emissão por decisão judicial). A comparação com `Mov_Nfse_Decisao` e com o painel municipal não foi feita.
- **O schema e o leiaute vigentes da NF-e não foram lidos**; as seções 5 e 6 usam a NT 2020.005 e a NT 2013/005.
- **A planilha do documento 34 não está neste ambiente**: as lacunas da seção 5 são por nome de campo no modelo, não por conferência com a planilha.
- **Sem validação do contador:** a C362 é pergunta, não resposta. Nada foi aplicado.
