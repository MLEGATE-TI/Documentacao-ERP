# Desenho do BP-e (modelo 63) a partir dos schemas das NT 2026.001, 2026.002, 2026.004 e 2026.005 — Documento 164

> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 28** (995 entidades, 10.844 campos). Este documento lê os quatro pacotes de schemas do BP-e que você enviou em 03/11/2026, compara com o dicionário e propõe o desenho do **Bilhete de Passagem Eletrônico, modelo 63**. As decisões de modelagem seguem as do CT-e (documento 42, D-N66 a D-N72) e as da NFCom.

*Lidos por inteiro: os quatro pacotes de schemas (NT 2026.001 vínculo de pagamento v1.01b corrigida; NT 2026.002 RTC 1.01; NT 2026.004 RTC 1.01; NT 2026.005 RTC Simples Nacional 1.00), 29 XSD cada um. Também usei o texto do Decreto 12.955/2026 que você colou em 03/11/2026. **Não li** o texto de nenhuma NT do BP-e, o MOC, o DABPE nem a tabela de meios de pagamento (seção 12).*

Mlegate · Alberto Beyeler · 3 de novembro de 2026

# 1. Resumo

- **O BP-e tem três leiautes de dados, não um.** O pacote traz o `BPe` (rodoviário, aquaviário e ferroviário, 233 linhas folha), o `BPeTA` (**aéreo**, 194) e o `BPeTM` (**transporte metropolitano**, 173), todos com `mod` 63, mais oito eventos, a consulta de situação e a consulta de status do serviço. O aéreo e o metropolitano **não são variações do rodoviário**: o aéreo troca viagem por voo e aeroporto, e o metropolitano não tem passageiro, tem **contadores de catraca por viagem** (`nContInicio`, `nContFim`, `qPass`).
- **O dicionário não tem nenhuma entidade de BP-e.** O que existe cobre bem o resto: nota de saída, participante, pagamento, compra governamental, referência de documento, contingência, vínculo de pagamento (110300), evento genérico e a tributação por item. **Faltam** os dados próprios da passagem (viagem, passageiro, componentes do valor, poltrona, bagagem) e a viagem do metropolitano.
- **Proposta, igual à do CT-e (D-N67):** o BP-e emitido é uma **nota de saída modelo 63 com um item de serviço** (no metropolitano, um item por trecho `det`) mais a entidade própria **`Mov_Bpe`**. O comprador é o cliente da nota; o passageiro é dado do bilhete.
- **Achado importante: os códigos colidem entre modais e entre modelos.** O mesmo código significa coisas diferentes: `tpComp` 06 é "serviço de venda integrada" no rodoviário e "bagagem" no aéreo; `tpDesconto` 10 a 13 mudam inteiros; `tpViagem` 01 é "extra" no rodoviário e "regular internacional" no aéreo; e a forma de pagamento do BP-e tem **tabela própria** (PIX é 06, contra 17 da NF-e). Também os eventos 110115, 110116 e 110117 são **outros eventos** no BP-e (não embarque, alteração de poltrona, excesso de bagagem) e no MDF-e (inclusão de DF-e, pagamento da operação, confirmação do serviço). Os domínios do desenho são **por modal e por modelo** (seção 7).
- **Contagem proposta: +7 entidades e +86 campos** se você aprovar os três leiautes (seção 11). Só o rodoviário, aquaviário e ferroviário com os eventos: **+4 entidades e +57 campos**.
- **A NT 2026.005 do BP-e traz o evento do Simples e o cancelamento dele com código diferente do da NF-e:** no BP-e o cancelamento é **412141**; na NF-e, a NT 2026.005 diz 110001 (documento 163). Pergunta Q164-8.

# 2. Fontes lidas

| Fonte | O que contém | Uso |
|---|---|---|
| NT 2026.001, vínculo de pagamento, v1.01b corrigida (pacote de schemas) | Base: BPe, BPeTA, BPeTM, 6 eventos (cancelamento, não embarque, alteração de poltrona, excesso de bagagem, vínculo e cancelamento do vínculo), consultas | Linha de base da comparação |
| NT 2026.002, RTC 1.01 | Acrescenta suframa (`ISUFEmit`), ALC/ZFM (`gALCZFMCBS`), `refDFeAnt` da compra governamental e `pDevTrib` | Comparado com a anterior |
| NT 2026.004, RTC 1.01 | Acrescenta `gMultaJuros`, `vBPLiq` (valor líquido sem tributos) em todos os leiautes e `indFornecimento` no metropolitano | Comparado com a anterior |
| NT 2026.005, RTC Simples Nacional 1.00 | Acrescenta `tpRegimeIBSCBS` no emitente, `gTribSN` no item e no total, e os eventos `evTributacaoSN` (412140) e `evCancTribSN` (412141) | Leiaute vigente (base da classificação) |
| Decreto 12.955/2026 (texto colado em 03/11/2026) | Arts. 12, 13, 113, 114, 124, 131, 135, 140 a 145, 233, 414 a 416, 439 e outros | Regras de negócio (seção 9) |

**Comparação entre pacotes.** Medi por caminho de elemento, não por texto de arquivo (os arquivos diferem por quebra de linha). Entre a NT 2026.001 e a 2026.002 entram 50 caminhos novos; entre a 2026.002 e a 2026.004, 11 novos e 1 removido (do imposto seletivo, que não é do BP-e); entre a 2026.004 e a 2026.005, 25 novos e dois arquivos de evento.

# 3. O leiaute: três raízes e oito eventos

| Raiz | Modal | Linhas folha | O que tem de próprio |
|---|---|---|---|
| `BPe` | 1 rodoviário, 3 aquaviário, 4 ferroviário | 233 | Localidade de origem e destino, passageiro, viagens (percurso, serviço, acomodação, poltrona, plataforma), travessia aquaviária (tipo e situação do veículo), componentes do valor, ICMS completo, partilha do ICMS, IBS/CBS, pagamento, vínculo de pagamento, TAR, `boardPassBPe` |
| `BPeTA` | 2 aéreo | 194 | Tipo de compra (normal, múltiplo/fretamento, vinculado ao múltiplo), número do bilhete IATA, voo, companhia, aeroportos, retenção previdenciária (`vINSSRet`, só no múltiplo), substituição com 8 tipos; **sem ICMS** |
| `BPeTM` | metropolitano (tpBPe 4) | 173 | Competência, CFOP, `indFornecimento`, viagens por equipamento contador, trechos com contadores, quantidade de passagens, componentes por categoria de passageiro, totais |

**Em todos:** identificação, emitente, comprador opcional, agência opcional, compra governamental, multa e juros, pagamento (`pag`, 1 a 10), vínculo de pagamento (`pgtoVinc`, até 99), autorizados a baixar o XML (até 10), informações adicionais, responsável técnico, QR Code e assinatura.

**Eventos do schema:**

| Código | Evento | Dados próprios |
|---|---|---|
| 110111 | Cancelamento | `nProt`, `xJust` (15 a 255) |
| 110115 | Não embarque | `nProt`, `xJust` |
| 110116 | Alteração de poltrona | `nProt`, `poltrona` |
| 110117 | Excesso de bagagem | `nProt`, `qBagagem`, `vTotBag` e o grupo **IBS/CBS completo** do serviço de bagagem, com `vTotDFe` |
| 110300 | Vinculação do pagamento | `nProt`, `pgto` (já coberto, `Mov_Dfe_Vinculo_Pagamento`) |
| 110301 | Cancelamento da vinculação | `nProt`, `nProtVincPgto` (já coberto) |
| 412140 | Tributação do Simples Nacional (fisco) | Por item (1 a 990) e totais; **mesma estrutura do evento da NF-e** do documento 163 |
| 412141 | Cancelamento da tributação do Simples | `nProt`, `nProtEvTribSN` |

O evento 110116 não diz **qual viagem** muda de poltrona (não há `nViagem`). O `indFornecimento` do metropolitano diz que o indicador "dispensa o evento de confirmação de embarque", mas **o pacote não tem esse evento** (Q164-E3).

# 4. Cobertura por área

Classifiquei **por área**, não linha a linha em planilha como no documento 42 (seção 12).

| Área | Linhas (BPe / BPeTA / BPeTM) | Situação | Destino |
|---|---|---|---|
| Identificação (`ide`) | 24 / 26 / 22 | Coberta em grande parte; 4 a 6 campos novos | `Mov_Documento_Fiscal`, `Mov_Nota_Fiscal_Saida`, `Mov_Bpe`, `Mov_Dfe_Contingencia` |
| Emitente | 21 / 17 / 21 | **Coberta** (`Cad_Filial`, endereço, inscrições); TAR é +1 campo; `tpRegimeIBSCBS` derivado (Q163-1) | `Cad_Filial_Perfil_Fiscal` |
| Comprador | 17 / 17 / não tem | **Coberta** pelo participante | `Mov_Nota_Fiscal_Saida.ID_Participante_Cliente` |
| Agência | 14 / 14 / não tem | **Coberta** pelo participante; +1 campo de ligação | `Mov_Bpe.ID_Participante_Agencia` |
| Substituição | 2 / 2 / não tem | **Coberta** pela referência do documento, com valores novos | `Mov_Nota_Fiscal_Saida_Referenciada` |
| Passagem e passageiro | 14 / 10 / não tem | Lacuna: campos novos | `Mov_Bpe` |
| Viagem | 13 / ver abaixo / não tem | Lacuna: entidade nova | `Mov_Bpe_Viagem` |
| Valores (`infValorBPe`) | 10 / ver abaixo / não tem | Valor e desconto no item da nota; componentes em entidade nova | `Mov_Nota_Fiscal_Saida_Item`, `Mov_Bpe_Componente` |
| ICMS e partilha | 31 / não tem / por trecho | **Coberta** pela apuração por item | `Mov_Apuracao_Tributo_Item`, `Mov_Apuracao_Tributo_Item_Complemento` |
| IBS e CBS | 51 / incluído / por trecho | **Coberta** (documento 41, D-N72) | Idem |
| Pagamento (`pag`) | 13 / incluído / não tem | Coberta em parte: **+7 campos** | `Mov_Nota_Fiscal_Saida_Pagamento` |
| Vínculo de pagamento | 5 / incluído / 5 | **Coberta** | `Mov_Dfe_Vinculo_Pagamento` |
| Viagens do metropolitano | não tem / não tem / 86 + 21 de totais | Lacuna: 3 entidades; totais derivados | `Mov_Bpe_Tm_*` |
| Autorizados, informações adicionais, responsável técnico, QR Code, assinatura | 12 / 12 / 10 | Coberta ou só no XML | `Mov_Nota_Fiscal_Saida_Autorizado_Xml`, `Mov_Documento_Fiscal` |

No aéreo, viagem, valores, impostos e pagamento somam **94 linhas** em um só bloco do schema (o grupo de valores é uma escolha dentro do `infBPe`); no desenho o aéreo usa as mesmas entidades do rodoviário.

# 5. Como o BP-e se liga ao dicionário

| Fato | Onde fica | Por quê |
|---|---|---|
| Documento (chave, protocolo, status, XML, QR Code) | `Mov_Documento_Fiscal` com modelo 63 em `Cad_Classe_Sistema` (`modelo_documento_fiscal`) | D-N1. Chave de 44 posições com CNPJ alfanumérico (Decreto, art. 124) |
| Bilhete | `Mov_Nota_Fiscal_Saida` (cliente = comprador, `Valor_Total` = `vBP` como emitido, `Indicador_Presenca` = `indPres`) e **um item de serviço** em `Mov_Nota_Fiscal_Saida_Item` (`Valor_Desconto_Item` = `vDesconto`, `Valor_Total_Liquido` = `vBPLiq`) | Como o CT-e (D-N67): reaproveita tributação, título a receber e escrituração |
| Dados do bilhete | **`Mov_Bpe`**, 1:1 com a nota de saída (como `Mov_Nfcom`) | Seção 6.1 |
| Metropolitano | Um **item da nota por trecho** (`det`), como o CT-e Simplificado (documento 42, seção 6.9), com `Mov_Bpe_Tm_Viagem` e `Mov_Bpe_Tm_Trecho` | O ICMS e o IBS/CBS são por `det`, não por documento |
| ICMS, partilha, crédito outorgado, IBS/CBS, Simples | `Mov_Apuracao_Tributo_Item` e `Mov_Apuracao_Tributo_Item_Complemento` | Sem entidade nova (D-N72) |
| Forma de pagamento, cartão, troco | `Mov_Nota_Fiscal_Saida_Pagamento` | `valor_troco` já existe |
| Pagamento vinculado (grupo `pgtoVinc` e eventos 110300 e 110301) | `Mov_Dfe_Vinculo_Pagamento` | Já coberto |
| Compra governamental | `Mov_Nota_Fiscal_Saida_Compra_Governamental` | Já tem `Percentual_Redutor`; o aéreo e o metropolitano não trazem esse campo (fica vazio) |
| Substituição e multa e juros | `Mov_Nota_Fiscal_Saida_Referenciada` | Seção 6.3 |
| Contingência offline (`tpEmis` 2, `dhCont`, `xJust`) | `Mov_Dfe_Contingencia` e `Mov_Documento_Fiscal.Tipo_Emissao` | Só existem `tpEmis` 1 e 2 no BP-e |
| Eventos | `Mov_Dfe_Evento` (com `Cad_Dfe_Evento_Tipo` por modelo 63) e `Mov_Bpe_Evento` | Seção 8 |
| CFOP do metropolitano | `Mov_Nota_Fiscal_Saida_Item.ID_CFOP_Saida` | O leiaute do metropolitano é o único com CFOP |
| `vTotTrib`, `vPgto`, `vTotDFe`, totais do metropolitano, `cUF`, `cDV`, `verProc`, `UFIni`, `UFFim`, `nProt` dos eventos | **Derivados** ou do documento | Derivar, não guardar |

# 6. Entidades e campos propostos

## 6.1 `Mov_Bpe` (29 campos)

Dados do bilhete que não cabem na nota. Uma linha por BP-e, nos três leiautes. *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe** | identificador | --- |
| **ID_Nota_Fiscal_Saida** | referência (`Mov_Nota_Fiscal_Saida`), única | A nota de saída a que o bilhete pertence (relação 1:1) |
| **Modal** | enumeração {rodoviario, aereo, aquaviario, ferroviario} | `ide/modal` (1, 2, 3 e 4). No metropolitano, o modal do leiaute TM (1, 3 ou 4) |
| **Tipo_Bpe** | enumeração {normal, substituicao, transporte_metropolitano} | `ide/tpBPe` (0, 3 e 4) |
| **Tipo_Compra_Aereo** | enumeração, opcional {normal, multiplo_fretamento, vinculado_a_multiplo} | `ide/tpCompra`: só no aéreo. Com `vinculado_a_multiplo`, a chave do BP-e múltiplo vai na referência de documento |
| **ID_Municipio_Inicio_Viagem** | referência (`Cad_Municipio`) | `ide/cMunIni`; a UF de início (`UFIni`) é derivada. **É o local da operação do IBS** (Decreto, art. 12, VI; Q164-10) |
| **ID_Municipio_Fim_Viagem** | referência (`Cad_Municipio`), opcional | `ide/cMunFim`; vazio quando o destino é o exterior |
| **Indicador_Destino_Exterior** | booleano | `ide/UFFim` = "EX": viagem com destino no exterior. Faz o Motor aplicar a regra da base de cálculo internacional (Q164-C2) |
| **Codigo_Localidade_Origem** | código (até 7), opcional | `infPassagem/cLocOrig` (rodoviário, aquaviário e ferroviário) |
| **Descricao_Localidade_Origem** | texto (60), opcional | `infPassagem/xLocOrig` |
| **Codigo_Localidade_Destino** | código (até 7), opcional | `infPassagem/cLocDest` |
| **Descricao_Localidade_Destino** | texto (60), opcional | `infPassagem/xLocDest` |
| **Data_Hora_Embarque** | data e hora, opcional | `infPassagem/dhEmb` (não existe no metropolitano) |
| **Data_Hora_Validade** | data e hora, opcional | `infPassagem/dhValidade` |
| **Numero_Bilhete_Iata** | código (até 20), opcional | `ide/nroBPIATA`: número do bilhete conforme a IATA (aéreo) |
| **Data_Competencia** | data, opcional | `ide/dCompet` (só metropolitano): competência do transporte |
| **Indicador_Fornecimento** | booleano | `ide/indFornecimento` (só metropolitano): BP-e de fornecimento (transporte de colaboradores, tripulação de outra empresa, embarque em até 5 dias da emissão) |
| **ID_Participante_Agencia** | referência (`Cad_Participante`), opcional | Grupo `agencia`: agência, preposto ou terceiro que vendeu o bilhete (nome, CNPJ e endereço vêm do participante) |
| **Nome_Passageiro** | texto (60), opcional | `infPassageiro/xNome` |
| **Cpf_Passageiro** | código (11), opcional | `infPassageiro/CPF` |
| **Tipo_Documento_Passageiro** | enumeração {rg, titulo_eleitor, passaporte, cnh, outros}, opcional | `infPassageiro/tpDoc` (1 a 5) |
| **Numero_Documento_Passageiro** | código (até 20), opcional | `infPassageiro/nDoc` |
| **Descricao_Documento_Passageiro** | texto (100), opcional | `infPassageiro/xDoc`: só quando o tipo é `outros` |
| **Data_Nascimento_Passageiro** | data, opcional | `infPassageiro/dNasc` |
| **Telefone_Passageiro** | código (7 a 12), opcional | `infPassageiro/fone` |
| **Email_Passageiro** | texto (60), opcional | `infPassageiro/email` |
| **ID_Tipo_Desconto** | referência (`Cad_Classe_Sistema`, domínio por modal), opcional | `infValorBPe/tpDesconto`. **O código muda de significado entre o rodoviário e o aéreo** (seção 7) |
| **Descricao_Desconto** | texto (100), opcional | `infValorBPe/xDesconto` |
| **Codigo_Desconto** | código (2 a 20), opcional | `infValorBPe/cDesconto`: código do desconto quando o tipo é "outros" |

O passageiro fica **no bilhete** (snapshot), e não em `Cad_Participante` (Q164-3): é pessoa que quase nunca tem cadastro, o dado muda de bilhete para bilhete e o leiaute permite estrangeiro por passaporte. O comprador, quando informado (`comp`, 0 a 1), é participante cadastrado (cliente da nota), com endereço, como em qualquer nota.

## 6.2 `Mov_Bpe_Viagem` (20 campos)

Uma linha por viagem do bilhete (`infViagem`, 1 a n no rodoviário e no aéreo). *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe_Viagem** | identificador | --- |
| **ID_Bpe** | referência (`Mov_Bpe`) | O bilhete |
| **Sequencia** | número | Ordem da viagem no bilhete |
| **ID_Tipo_Viagem** | referência (`Cad_Classe_Sistema`, por modal) | `tpViagem`. Rodoviário: 00 regular, 01 extra. **Aéreo: 00 regular doméstico, 01 regular internacional, 02 não regular doméstico, 03 não regular internacional** |
| **ID_Tipo_Servico** | referência (`Cad_Classe_Sistema`) | `tpServ`. Rodoviário: 1 a 11 (convencional com e sem sanitário, semileito, leito com e sem ar, executivo, semiurbano, longitudinal, travessia, cama, micro-ônibus). Aéreo: 12 comercial e 13 executivo. Sem colisão |
| **ID_Tipo_Acomodacao** | referência (`Cad_Classe_Sistema`) | `tpAcomodacao`. Rodoviário: 1 a 5. Aéreo: 6 comum e 7 conforto. Sem colisão |
| **Tipo_Trecho** | enumeração {normal, trecho_inicial, conexao} | `tpTrecho` (1, 2 e 3) |
| **Data_Hora_Viagem** | data e hora | `dhViagem`: referência da viagem |
| **Data_Hora_Conexao** | data e hora, opcional | `dhConexao`: só quando o trecho é conexão |
| **Codigo_Percurso** | código (até 20), opcional | `cPercurso` (rodoviário) |
| **Descricao_Percurso** | texto (100), opcional | `xPercurso` |
| **Prefixo_Linha** | código (até 20), opcional | `prefixo` |
| **Numero_Poltrona** | código (até 3), opcional | `poltrona`: poltrona, assento ou cabine. O evento 110116 muda este valor |
| **Plataforma** | texto (10), opcional | `plataforma`: plataforma, carro ou barco de embarque |
| **ID_Tipo_Veiculo_Travessia** | referência (`Cad_Classe_Sistema`), opcional | `infTravessia/tpVeiculo` (29 tipos, de motocicleta a "passageiro", e 99 outros); só na travessia aquaviária |
| **Situacao_Veiculo_Travessia** | enumeração, opcional {vazio, carregado, nao_se_aplica} | `infTravessia/sitVeiculo` |
| **Numero_Voo** | código (até 20), opcional | `nroVoo` (aéreo) |
| **Sigla_Companhia_Aerea** | código (até 3), opcional | `SiglaCiaOperVoo`: sigla IATA da companhia que opera o voo |
| **Codigo_Aeroporto_Origem** | código (3 a 4), opcional | `cAeroOrig`: código IATA |
| **Codigo_Aeroporto_Destino** | código (3 a 4), opcional | `cAeroDest` |

## 6.3 `Mov_Bpe_Componente` (4 campos)

Componentes do valor do bilhete (`Comp`, 1 a n). *Vigência: não.* Segue o `Mov_Cte_Componente_Valor`.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe_Componente** | identificador | --- |
| **ID_Bpe** | referência (`Mov_Bpe`) | O bilhete |
| **Tipo_Componente** | enumeração {tarifa, pedagio, taxa_embarque, seguro, taxa_manutencao_rodovia, servico_venda_integrada, bagagem, reserva_assento, transporte_animais, outros} | `tpComp`, **guardado pelo nome, não pelo código**: no rodoviário 06 é "serviço de venda integrada" e no aéreo 06 é "bagagem". O ERP converte para o código do leiaute na emissão |
| **Valor_Componente** | número | `vComp`. A soma dos componentes confere com `vBP` (aviso) |

## 6.4 `Mov_Bpe_Evento` (4 campos)

Dados próprios dos eventos 110116 e 110117, 1:1 com `Mov_Dfe_Evento` (mesmo padrão de `Mov_Cte_Entrega`). *Vigência: não.*

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Dfe_Evento** | referência (`Mov_Dfe_Evento`), identidade | O evento |
| **Numero_Poltrona** | código (até 3), opcional | 110116: a nova poltrona. Atualiza `Mov_Bpe_Viagem.Numero_Poltrona` |
| **Quantidade_Volumes_Bagagem** | número, opcional | 110117, `qBagagem`: volumes carregados |
| **Valor_Servico_Bagagem** | número, opcional | 110117, `vTotBag`: valor do serviço de bagagem (pode ser zero em BP-e de complemento de ICMS). A tributação do serviço (grupo IBS/CBS do evento) vai para `Mov_Apuracao_Tributo_Item` com `Origem_Tipo` = `bpe_evento` |

## 6.5 Metropolitano: `Mov_Bpe_Tm_Viagem` (8 campos), `Mov_Bpe_Tm_Trecho` (9) e `Mov_Bpe_Tm_Componente` (4)

O BP-e metropolitano não vende bilhete a passageiro: **resume a bilhetagem de cada viagem de um coletivo**, com os contadores da catraca. *Vigência: não.*

**`Mov_Bpe_Tm_Viagem`** (`detBPeTM`, 1 a 99: um equipamento contador por linha):

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe_Tm_Viagem** | identificador | --- |
| **ID_Bpe** | referência (`Mov_Bpe`) | O BP-e metropolitano |
| **Identificador_Equipamento_Contador** | número (1 a 999) | Atributo `idEqpCont` |
| **ID_Estado_Inicio_Viagem** | referência (`Cad_Estado`) | `UFIniViagem` |
| **ID_Estado_Fim_Viagem** | referência (`Cad_Estado`), opcional | `UFFimViagem` |
| **ID_Veiculo_Transporte** | referência (`Cad_Veiculo_Transporte`), opcional | O coletivo, quando cadastrado |
| **Placa** | código (7), opcional | `placa` do coletivo (antiga ou Mercosul) |
| **Prefixo_Linha** | código (até 20), opcional | `prefixo` |

**`Mov_Bpe_Tm_Trecho`** (`det`, 1 a 990 por viagem):

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe_Tm_Trecho** | identificador | --- |
| **ID_Bpe_Tm_Viagem** | referência (`Mov_Bpe_Tm_Viagem`) | A viagem |
| **ID_Nota_Fiscal_Saida_Item** | referência (`Mov_Nota_Fiscal_Saida_Item`) | O item da nota que carrega `vBP`, `vBPLiq`, o ICMS e o IBS/CBS do trecho (como o `det` do CT-e Simplificado) |
| **Numero_Viagem** | número (1 a 999) | Atributo `nViagem` |
| **ID_Municipio_Inicio** | referência (`Cad_Municipio`) | `cMunIni` |
| **ID_Municipio_Fim** | referência (`Cad_Municipio`), opcional | `cMunFim` |
| **Contador_Inicio** | código (até 20) | `nContInicio`: leitura da catraca no início |
| **Contador_Fim** | código (até 20) | `nContFim` |
| **Quantidade_Passagens** | número | `qPass`: passagens do trecho. O total do documento é a soma |

**`Mov_Bpe_Tm_Componente`** (`Comp`, 1 a n por trecho: categorias de passageiro):

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Bpe_Tm_Componente** | identificador | --- |
| **ID_Bpe_Tm_Trecho** | referência (`Mov_Bpe_Tm_Trecho`) | O trecho |
| **Nome_Componente** | texto (15) | `xNome`: categoria, por exemplo ISENTOS, VT, CARTAO PRE-PAGO, IDOSOS |
| **Quantidade_Componente** | número (até 5 dígitos) | `qComp` |

Os totais do metropolitano (`qPass`, `vBP`, `vBPLiq`, `ICMSTot` e `IBSCBSTot`) são **somas dos trechos** e não se guardam.

# 7. Alterações em entidades existentes

| Entidade | Mudança | Campos | Por quê |
|---|---|---|---|
| `Mov_Nota_Fiscal_Saida_Pagamento` | Campos novos: `Numero_Documento_Pagamento` (`nDocPag`), `Descricao_Forma_Pagamento` (`xPag`), `Descricao_Bandeira` (`xBand`), `Numero_Nsu_Transacao` (`nsuTrans`), `Numero_Nsu_Host` (`nsuHost`), `Numero_Parcelas` (`nParcelas`) e `Informacoes_Adicionais_Cartao` (`infAdCard`) | **+7** | O grupo de pagamento do BP-e traz esses sete, que a NF-e e a NFC-e não usam no dicionário. Conferir se `xPag` já existe (Q164-E2) |
| `Cad_Filial_Perfil_Fiscal` | Campo novo `Numero_Tar` (TAR, Termo de Autorização de Serviço Regular, registro do emitente na ANTT ou na agência estadual, `emit/TAR`), com a vigência do perfil | **+1** | Dado do emitente, com vigência; o bilhete só o copia no XML |
| `Mov_Nota_Fiscal_Saida_Referenciada` | `Tipo_Referencia` ganha `bpe_substituido` (`infBPeSub/chBPe`), `bpe_multa_juros` (`gMultaJuros/chBPeRef`) e `bpe_multiplo` (`infBPeVinculado/chBPeMultiplo`, aéreo) | 0 | A referência de documento já existe |
| `Mov_Nota_Fiscal_Saida_Referenciada.ID_Motivo_Substituicao` | Valores novos para o BP-e: remarcação, transferência, transferência e remarcação, erro de tarifa, erro de tributação, decisão judicial, erro cadastral e outros (`tpSub` 1 a 7 e 9; o rodoviário só usa 1 a 3) | 0 | O campo já guarda o motivo da substituição (NFCom) |
| `Mov_Apuracao_Tributo_Item` | `Origem_Tipo` ganha `bpe_evento` (tributação do excesso de bagagem) | 0 | O evento 110117 tributa um serviço que não é item da nota |
| `Cad_Classe_Sistema` | Valor 63 em `modelo_documento_fiscal`; domínios novos: `tipo_viagem_bpe_rodoviario`, `tipo_viagem_bpe_aereo`, `tipo_desconto_bpe_rodoviario`, `tipo_desconto_bpe_aereo`, `tipo_servico_bpe`, `tipo_acomodacao_bpe`, `tipo_veiculo_travessia_bpe` e `forma_pagamento_bpe` (01 dinheiro, 02 cheque, 03 crédito, 04 débito, 05 vale-transporte, 06 PIX, 99 outros) | 0 | Vocabulário pequeno e fechado pelo schema. **A forma de pagamento do BP-e não é a da NF-e** (PIX é 06, contra 17) |
| `Cad_Dfe_Evento_Tipo` | Linhas do modelo 63: 110111, 110115, 110116, 110117, 110300, 110301, 412140 e 412141 | 0 | O tipo é chaveado por modelo e código; os mesmos códigos já existem no MDF-e com outro sentido |
| `Cad_Dfe_Leiaute` | Linhas do modelo 63: `BPe`, `BPeTA` e `BPeTM`, versão 1.00, com a data de cada NT como vigência | 0 | As datas esperam o texto das NT (Q164-E1) |
| `Cad_Cclasstrib_Documento` | Linhas para o modelo 63 | 0 | Carga; a tabela de cClassTrib do BP-e não veio |
| `Cad_Dfe_Parametro_Regra` | Parâmetros do modelo 63 (seção 9), **sem valor** até chegar o MOC | 0 | Regra legal é parâmetro com vigência |

# 8. Eventos

| Código | Evento | Quem registra | Proposta |
|---|---|---|---|
| 110111 | Cancelamento | Emitente | `Mov_Dfe_Evento` (`Justificativa`); `Mov_Documento_Fiscal.Status` passa a cancelado. O `nProt` do schema é o protocolo da própria autorização e é derivado. Vedar com aviso se houver substituição, vínculo de pagamento ativo ou evento de não embarque (conferir no MOC, Q164-E1) |
| 110115 | Não embarque | Emitente | `Mov_Dfe_Evento` (`Justificativa`) |
| 110116 | Alteração de poltrona | Emitente | `Mov_Bpe_Evento.Numero_Poltrona` |
| 110117 | Excesso de bagagem | Emitente | `Mov_Bpe_Evento` e tributação em `Mov_Apuracao_Tributo_Item` (`bpe_evento`) |
| 110300 e 110301 | Vínculo de pagamento e cancelamento | Emitente | `Mov_Dfe_Vinculo_Pagamento` e `Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado` (já aprovados) |
| 412140 | Tributação do Simples Nacional | **Fisco** | `Mov_Dfe_Evento` com `Papel_Autor` = `fisco` e `Mov_Dfe_Evento_Simples_Item` (documento 163, mesma estrutura; desenho provisório). Aqui o evento vale para o bilhete, e o `nItem` tem de ser 1 (ou o trecho, no metropolitano) |
| 412141 | Cancelamento da tributação do Simples | Fisco | `Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado` aponta para o 412140 (Q164-8) |

O evento do excesso de bagagem **gera receita e imposto novos** depois da emissão: o ERP registra o serviço, a tributação (IBS/CBS; o evento não tem grupo de ICMS) e avisa o contador sobre a escrituração (Q164-C3).

# 9. Regras de negócio e o Decreto 12.955/2026

Leitura do texto colado em 03/11/2026. As regras abaixo ficam no Motor de Regras ou em `Cad_Dfe_Parametro_Regra`, nunca em código fixo.

| Artigo | O que diz | O que muda no ERP |
|---|---|---|
| Art. 113, VI | Institui o BP-e, modelo 63, como documento fiscal eletrônico | Modelo 63 em `Cad_Classe_Sistema` |
| Art. 114 | Institui a NFAg 75, a DeRE e a NF-e ABI 77 | Fora deste desenho |
| Art. 124 | A chave de acesso tem CNPJ ou CPF, tipo do documento, ano e mês e número | A chave de 44 posições com CNPJ alfanumérico já está no `Mov_Documento_Fiscal` |
| Art. 131, III | A autorização de uso é o protocolo | `Protocolo_Autorizacao` do documento |
| Arts. 140 a 145 | Eventos fiscais | `Mov_Dfe_Evento`; prazos e vedações são parâmetro, sem valor até o MOC |
| Art. 135, § 1º, VI | Lista o DABPE entre os documentos auxiliares | A representação impressa é o `Mov_Documento_Fiscal.ID_Documento_Impresso`; o `boardPassBPe` (PDF417) fica só no XML |
| Art. 12, VI e § 13 | O local da operação no transporte de passageiros é o **início do transporte**; inclui a bagagem; trechos parciais e modais não importam | `Mov_Nota_Fiscal_Saida_Item.ID_Municipio_Incidencia_Ibs` = `Mov_Bpe.ID_Municipio_Inicio_Viagem`, derivado, com aviso se o usuário mudar (Q164-10). A bagagem do evento 110117 segue o mesmo local |
| Art. 13, § 7º | Na passagem internacional vendida de ida e volta em conjunto, a base de cálculo é **metade** do valor da venda de ida e volta | Regra do Motor com `Indicador_Destino_Exterior`; como dividir em um BP-e com mais de uma viagem é a Q164-C2 |
| Art. 233 | Isenta o transporte público coletivo urbano, semiurbano e metropolitano rodoviário e metroviário | Relevante para o BP-e metropolitano; o cClassTrib vem do catálogo, e o Motor sugere (Q164-C6) |
| Arts. 414 a 416 | Regime específico do transporte coletivo de passageiros: rodoviário, ferroviário e aquaviário intermunicipal e interestadual e aéreo regional com redução de 40%; ferroviário e aquaviário urbano com 100%; regras de crédito | O cClassTrib e a redução vêm do catálogo; o crédito é do lado do adquirente. Q164-C1 |
| Art. 439 | Compras governamentais | `gCompraGov` já está em `Mov_Nota_Fiscal_Saida_Compra_Governamental` |
| Art. 57 | Devolução e cancelamento | Cancelamento (110111) e substituição por BP-e `tpBPe` 3 |
| Art. 619 e Decreto 13.075/2026 | Vigência | As datas do BP-e dependem do texto das NT (Q164-E1) |

**Parâmetros previstos (sem valor):** `BPE-CANCELAMENTO-PRAZO`, `BPE-NAO-EMBARQUE-PRAZO`, `BPE-EMISSAO-ATRASO`, `BPE-CONTINGENCIA-PRAZO`, `BPE-VTOTDFE-FORMULA` (o mesmo conflito do CT-e: o `vTotDFe` é `vBP + IBS + CBS`, mas o `vBPLiq` é "sem tributos"), `BPE-NT-DATAS` (homologação e produção de cada NT) e `BPE-FORNECIMENTO-DIAS` (o texto do `indFornecimento` cita 5 dias entre a emissão e o embarque).

# 10. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Revisão 28 (real) | 995 | 10.844 |
| Revisão 29 prevista antes desta rodada (documentos 161 e 163, sem as Q161-1 e Q161-2) | 1.005 | 11.000 |
| **Q138-8 a Q138-10 (aprovadas hoje)**: 3 campos em `Cad_Lista_Legal_Item` | 0 | +3 |
| Revisão 29 prevista com as Q138 | 1.005 | 11.003 |
| **BP-e rodoviário, aquaviário e ferroviário, com os eventos:** `Mov_Bpe` (25 campos, sem os 2 do aéreo e os 2 do metropolitano), `Mov_Bpe_Viagem` (16 sem os 4 do aéreo), `Mov_Bpe_Componente` (4), `Mov_Bpe_Evento` (4), pagamento (+7), TAR (+1) | +4 | +57 |
| **Aéreo:** `Tipo_Compra_Aereo`, `Numero_Bilhete_Iata` e os 4 campos de voo | 0 | +6 |
| **Metropolitano:** `Data_Competencia`, `Indicador_Fornecimento` e as três entidades `Mov_Bpe_Tm_*` (8, 9 e 4) | +3 | +23 |
| **Total deste documento** | **+7** | **+86** |

| Cenário da revisão 29 | Entidades | Campos |
|---|---|---|
| Sem o BP-e | 1.005 | 11.003 |
| Só rodoviário, aquaviário e ferroviário | 1.009 | 11.060 |
| Mais o aéreo | 1.009 | 11.066 |
| Mais o metropolitano (tudo) | **1.012** | **11.089** |

Com as Q161-1 e Q161-2 aprovadas, somam-se mais 2 campos em todos os cenários.

# 11. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| **Q164-1** | Quais leiautes entram **agora**: rodoviário, aquaviário e ferroviário (4 entidades, 57 campos); **aéreo** (+6 campos); **metropolitano** (+3 entidades, +23 campos)? Pela regra do documento 42 (D-N68), o que não tem cliente fica como esboço | Rodoviário, aquaviário e ferroviário e aéreo agora (63 campos); metropolitano só com cliente |
| **Q164-2** | O BP-e emitido é **nota de saída modelo 63 com um item de serviço** (um item por trecho no metropolitano) mais `Mov_Bpe`, como o CT-e (D-N67)? | **Sim** |
| **Q164-3** | O **passageiro** fica como campos do bilhete (8 campos em `Mov_Bpe`), e não como participante; o **comprador**, quando informado, é participante cadastrado? | **Sim** |
| **Q164-4** | O grupo de pagamento ganha **+7 campos** em `Mov_Nota_Fiscal_Saida_Pagamento` e a forma de pagamento do BP-e usa **domínio próprio** (`forma_pagamento_bpe`: PIX é 06, não 17)? | **Sim** |
| **Q164-5** | A substituição e a multa e juros usam a **referência de documento** (3 valores novos) e o motivo de substituição existente (valores novos), sem campo novo? | **Sim** |
| **Q164-6** | Os domínios que colidem entre modais (`tpComp`, `tpDesconto`, `tpViagem`) são **por modal**, e o componente é guardado **pelo nome**, não pelo código? | **Sim** |
| **Q164-7** | Os eventos do modelo 63 entram em `Cad_Dfe_Evento_Tipo`; `Mov_Bpe_Evento` (4 campos) guarda a poltrona e a bagagem; a tributação da bagagem vai para a apuração com `Origem_Tipo` = `bpe_evento`; o evento do Simples reaproveita `Mov_Dfe_Evento_Simples_Item` (documento 163)? | **Sim** |
| **Q164-8** | O cancelamento da tributação do Simples é **412141** no BP-e (schema) e **110001** na NF-e (NT do documento 163): o ERP registra **cada um no seu modelo**, sem tentar unificar? | **Sim** |
| **Q164-9** | O **TAR** fica no perfil fiscal da filial, com vigência (`Cad_Filial_Perfil_Fiscal.Numero_Tar`, +1 campo)? | **Sim** |
| **Q164-10** | O município de incidência do IBS do item é **derivado do início da viagem** (Decreto, art. 12, VI), com aviso se o usuário mudar? | **Sim** |
| **Q164-11** | Os parâmetros do BP-e (prazos, fórmula do total, datas das NT) entram em `Cad_Dfe_Parametro_Regra` **sem valor** até chegarem o MOC e as NT? | **Sim** |
| **Q164-12** | Você envia o **MOC do BP-e**, o **DABPE**, o texto da **NT 2026.004 v1.01** e das **NT 2026.005 (BP-e)**, e a tabela de **cClassTrib aplicável ao BP-e**? (Soma-se à Q163-5) | **Sim** |

# 12. Para o contador e para a equipe

| Id | Pendência | Tratamento provisório |
|---|---|---|
| **Q164-C1** | **Regime específico do transporte coletivo de passageiros** (Decreto, arts. 414 a 416): quais cClassTrib e que redução (40% ou 100%) o BP-e carrega em cada modal e trecho, e como fica o crédito do comprador? | O Motor sugere pelo catálogo e o usuário confirma; sem cálculo próprio |
| **Q164-C2** | **Base de cálculo internacional** (art. 13, § 7º): metade do valor quando ida e volta são vendidas juntas. Em um BP-e com duas viagens, qual é a base de cada uma e em qual viagem fica o "início do transporte"? | Aviso e preenchimento manual da base |
| **Q164-C3** | **Excesso de bagagem** (110117): a receita e o imposto nascem depois da emissão. Como escriturar (o evento não tem ICMS)? E o `vTotBag` zero em "BP-e de complemento de ICMS"? | Registrar o serviço e a tributação com `Situacao_Dado` provisório |
| **Q164-C4** | **`vTotDFe`**: o schema diz `vBP + IBS + CBS`, mas o `vBPLiq` é "sem tributos". Em 2026 e a partir de 2027, o IBS e a CBS estão dentro do `vBP`? (mesmo conflito do CT-e, Q-6 do documento 42) | Fórmula por ano em parâmetro; o total é derivado |
| **Q164-C5** | **`vINSSRet`** (aéreo múltiplo): onde registrar a retenção previdenciária do BP-e múltiplo (fretamento)? | Retenção na apuração do item, com aviso |
| **Q164-C6** | **Metropolitano e o art. 233** (isenção do transporte coletivo urbano, semiurbano e metropolitano rodoviário e metroviário): o BP-e TM sempre tem CST de isenção? O leiaute ainda traz ICMS e `CFOP` | O Motor sugere; sem regra fixa |
| **Q164-E1** | **Datas das NT do BP-e** e a marca de 01/12/2026 do BP-e aéreo (documentos 14 e 161): **não achei data nos schemas**; os textos das NT não vieram | `BPE-NT-DATAS` sem valor; a marca de 01/12/2026 fica como leitura anterior, não confirmada |
| **Q164-E2** | Conferir no DDL se `xPag` e `xBand` já existem em `Mov_Nota_Fiscal_Saida_Pagamento` (os comentários mostram 10 colunas, sem eles) | Contar como novos até a conferência |
| **Q164-E3** | O `indFornecimento` diz que "dispensa o evento de confirmação de embarque", mas **não há esse evento nos schemas**. Existe, ou é do MOC? | Sem desenho |

# 13. Limites

- **Fonte única: os schemas.** Não li texto de NT, MOC, DABPE nem a tabela de meios de pagamento. Prazos, vedações de cancelamento, regras de rejeição e as datas de cada NT ficam sem valor (Q164-E1).
- **Classifiquei por área,** não linha a linha. As 600 linhas folha (233, 194 e 173) estão contadas por grupo; o aéreo soma viagem, valores, impostos e pagamento em um bloco só (94).
- **Os eventos** foram lidos nos 8 XSD, mas sem o texto do MOC não sei **quem pode registrar** cada um nem em que prazo.
- **O Decreto 12.955** foi lido no texto colado; cito artigos que li, e o contador confere os arts. 414 a 416 e 233 antes de ativar o catálogo.
- **O metropolitano** é o desenho menos seguro: um BP-e resume a bilhetagem da frota, e não sei se algum cliente da Mlegate o emite (Q164-1).
- Nada foi validado pelo contador.
