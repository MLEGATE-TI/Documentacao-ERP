# Desenho do B0a: fato gerador, ajuste da operação, acréscimos do art. 27, locação, transição de 2026, documento fiscal e cadastro — Documento 157

*Segundo dos seis desenhos que você liberou com o reenvio da LC 214, da LC 227 e do Decreto 12.955 (Q161-4), na ordem que você escolheu (156, 157, 150, 158, 159 e 160). Cobre o que sobrou do bloco B0a depois do documento 156. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O B0a tinha cinco partes (documento 115). O documento 156 já fez a base de cálculo, o valor de mercado e o uso e consumo pessoal. Este documento faz o resto: **o fato gerador e a antecipação (B0a-1), o ajuste, a devolução e o cancelamento (B0a-3), a transição de 2026 e a redução de 0,1 ponto (B0a-4), a entrega do arquivo ao adquirente e o cadastro da filial (B0a-5)**, mais os acréscimos do art. 27 (que você pôs no B0a na Q115-2), o valor de mercado da locação de imóvel e dois pontos pendentes (Q137-6 e D-N393). Li os textos legais (LC 214 consolidada com a LC 227, e o Decreto 12.955 com as alterações dos Decretos 13.075 e 13.133) e conferi um a um os nomes no dicionário da revisão 29.

O desenho acrescenta **13 entidades novas** e altera **24 existentes** (18 com campos novos, 6 só com valores, cargas ou texto). Nenhum campo é removido, exceto `Valor_Acrescimos` do estorno do estoque de abertura, que o par multa e juros substitui (Q157-6). Tudo fica na Contabilidade & Fiscal.

| Parte | O que a lei diz | O que o dicionário tinha | O que este documento acrescenta |
|---|---|---|---|
| **Fato gerador e antecipação** (LC, art. 10; Decreto, art. 11) | Momento por hipótese; a LC 227 mudou a execução continuada, a alíquota da antecipação, o excesso e o distrato | Só o imobiliário tinha o momento; a data do fato gerador só existia na NFS-e paulistana | Catálogo `Cad_Regra_Fato_Gerador` (12 linhas), a data do fato gerador gravada no item da nota e `Competencia_Debito` na apuração |
| **Ajuste da operação** (Decreto, arts. 57, 59 e 61; LC, art. 47) | Devolução e cancelamento com efeitos por lado e por modalidade de extinção do débito | Nenhuma entidade de ajuste; só o precedente do estoque de abertura | `Mov_Cbs_Ajuste_Operacao`, `Mov_Cbs_Ajuste_Operacao_Efeito` e a matriz `Cad_Cbs_Ajuste_Efeito_Regra` (21 linhas) |
| **Acréscimos do art. 27** (Decreto, art. 27; LC, art. 29) | Multa de 0,33% ao dia até 20% e juros pela Selic mais 1%; **22 artigos** do Decreto remetem a ele | Os números só em texto de descrição | `Cad_Acrescimo_Legal_Cbs` e `Cad_Acrescimo_Legal_Hipotese` (28 linhas) |
| **Locação de imóvel** (Decreto, art. 364; LC, arts. 255 e 256) | Valor de mercado da locação não onerosa ou abaixo do mercado, por percentual do valor de referência | Nada | Parâmetro `Cad_Valor_Mercado_Locacao_Parametro`, valor de referência do imóvel e três colunas na locação |
| **Transição de 2026 e 2027–2028** (LC, arts. 343 a 348; Decreto, arts. 464, 465, 582 a 585) | Dispensa de recolher em 2026; CBS menos 0,1 ponto em 2027 e 2028 | Alíquotas de teste e a carga do calendário | `Mov_Cbs_Transicao_2026_Periodo`, suprimento de omissão no auto, a redução gravada na apuração |
| **Documento fiscal e cadastro** (Decreto, arts. 104 a 108 e 134) | Entrega imediata do arquivo ao adquirente; comunicação de domicílio, venda e encerramento até o último dia útil do mês seguinte | Nada registra que o arquivo foi entregue nem o ato cadastral | `Mov_Documento_Fiscal_Entrega_Xml` e `Mov_Filial_Evento_Cadastral` |
| **Q137-6 e D-N393** (Decreto, arts. 105, § 4º-A, 115, § 3º e 239) | Obrigação de inscrição e de emissão desde 01/01/2027 para a pessoa física contribuinte e o produtor rural pessoa física | Nada | Quatro linhas de calendário e dois catálogos com vigência |

**Seis achados que mudam o que estava escrito antes.**

1. **A numeração do B0a-4 estava errada.** A LC 214 não tem art. 585. A redução de 0,1 ponto da CBS em 2027 e 2028 está no **art. 347 da LC**, e o **art. 585 do Decreto** a reproduz. Citarei sempre os dois.
2. **A LC 227 mudou duas regras que o documento 153 trata pela regra antiga.** Depois da LC 227 a antecipação **maior** que o valor definitivo deixou de ser crédito do contribuinte e segue as regras do pagamento a maior (LC, art. 10, § 4º, II, c; Decreto, art. 11, § 5º, II, c). E o fornecimento que não ocorre (inclusive o distrato) segue as regras do **cancelamento** (LC, art. 10, § 5º; Decreto, art. 11, § 6º e art. 57). O texto do documento 153 sobre o excesso e sobre a devolução do adiantamento precisa de correção, que a consolidação faz (capítulo 10).
3. **O número de artigos do art. 27 é 22, e não "mais de dez".** O documento 70 listava dez; o Decreto tem **22** remissões ao art. 27 (multa e juros) e outros artigos que falam só em "acréscimos legais". O art. 167 que o documento 70 punha na lista é genérico, e o art. 160, § 2º é só juros da Selic.
4. **"Evento cadastral" não existe na lei.** O Decreto usa "ato cadastral" (art. 105, § 5º) e "evento" só no art. 108, II. Li "evento cadastral da filial" como os atos do art. 108 (domicílio principal, venda ou transferência, encerramento ou paralisação). Confirme na Q157-11.
5. **O Decreto não regulamentou a regra dos cinco dias** (LC, art. 10, § 7º): a antecipação que consta como débito no período do fornecimento, se o intervalo for de até cinco dias. Reservo as colunas sem carga; o ERP não presume.
6. **O Decreto 13.075 criou as datas de 01/01/2027 da pessoa física** (art. 105, § 4º-A e art. 115, § 3º). Não existem na LC. É a base da Q137-6 e da D-N393.

# 2. Regras que segui

Valem as do documento 156 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; condições do Motor em colunas; carga provisória com `Situacao_Dado = provisorio` até o contador validar; o Motor sugere e o usuário confirma com `aprovar`, sem bloquear; extensão 1:1 para o que a minoria usa; nomes em português com sublinhado; prefixo `Valor_` só em número, referência, texto e enumeração). Acrescento:

1. **O ERP só registra o que não se deriva.** A base e a alíquota de um ajuste vêm da apuração original e nunca são digitadas; o prazo da entrega do arquivo e o prazo do cadastro saem de parâmetros; o valor total de uma multa de mora sai de principal, vencimento, pagamento e Selic. Guardo uma data ou um valor derivável só quando um evento posterior pode mudá-lo e o cálculo precisa se reproduzir (a data prevista de entrega, pelo evento 112150) ou quando serve para conferir com a Receita.
2. **Sem linha de parâmetro, aviso.** Sem linha vigente do fato gerador, do acréscimo ou do valor de referência o ERP avisa; nunca presume "emissão", nunca presume um percentual.
3. **Cito sempre "LC, art. X" e "Decreto, art. Y".** A numeração dos dois não coincide.
4. **Onde o Decreto vai além da LC**, a linha de carga leva `Origem_Regra = decreto` e vai ao contador, como no documento 156.
5. **Reaproveito o que o documento 156 e o 153 já desenharam.** O estorno do uso pessoal (documento 156, Q156-5) usa a linha de efeito do ajuste (capítulo 4); o adiantamento devolvido (documento 153) liga ao ajuste pela referência `ID_Credito_Ajuste`, sem duplicar campo.

# 3. Fato gerador e fornecimento com pagamento antecipado (B0a-1)

## 3.1 O que o texto pede

A LC, art. 10, diz que o fato gerador ocorre **no momento do fornecimento**, mesmo na execução continuada ou fracionada. O § 1º dá o momento por tipo de operação (transporte iniciado no País: início do transporte; transporte de carga iniciado no exterior: término; demais serviços: término do fornecimento; bem sem documento fiscal idôneo: a constatação; bem apreendido, abandonado ou de leilão: a aquisição). O § 2º diz que a compra da administração direta, das autarquias e das fundações sujeitas ao art. 473 tem o **pagamento** como fato gerador. O Decreto, art. 11, acrescenta o que a LC não traz: define fornecimento de bem material (entrega ou disponibilização) e de bem imaterial (instituição, transferência, cessão, concessão, licenciamento), diz o que é exigibilidade da parcela (art. 11, § 3º, I e § 4º: a data em que se constitui o direito de receber, e com fatura, a data da fatura) e fixa a **data prevista de entrega** informada no documento como a do fornecimento, salvo prova em contrário, e na falta dela a data de emissão (§§ 8º e 9º).

**O que a LC 227 mudou.**

| Dispositivo (LC, art. 10) | Antes | Depois da LC 227 | Efeito |
|---|---|---|---|
| § 3º | Lista de setores (água, saneamento, gás, telecomunicações, internet, energia) cujo fato gerador era "quando se torna devido o pagamento" | Toda operação de execução continuada ou fracionada: vale a primeira entre a exigibilidade da parcela e o pagamento | O catálogo precisa da regra sem lista de setores |
| § 4º, I, a, 2 | Antecipação: alíquota da data do pagamento de cada parcela | A da data da emissão do documento fiscal do pagamento **ou** a do pagamento, a que vier primeiro | Nova coluna de critério da data da alíquota (3.4) |
| § 4º, II, c | Antecipação maior que o definitivo: a diferença vira crédito | Aplicam-se as regras do pagamento indevido ou a maior (Decreto, art. 38) | Corrige o texto do documento 153 |
| § 5º | Sem fornecimento: o fornecedor apropria crédito das parcelas devolvidas | Aplicam-se as regras do cancelamento (Decreto, art. 57) | Capítulo 4 |
| § 6º (novo) | Não havia | A extinção do débito da antecipação permite ao adquirente apropriar crédito | Ligação do crédito ao débito extinto (pergunta Q157-E3 à equipe) |
| § 7º (novo) | Não havia | O regulamento pode permitir que a antecipação conste como débito no período do fornecimento, se o intervalo for de até 5 dias | O Decreto **não** regulamentou; só reserva de colunas (3.4) |
| Art. 3º, § 3º | Não havia | Locação, arrendamento e cessão temporária de bem entram como fornecimento contínuo | Linha de execução continuada |

## 3.2 Entidade nova: `Cad_Regra_Fato_Gerador`

Catálogo com vigência. Cada linha diz **em que momento** ocorre o fato gerador numa hipótese e **de qual data do registro** o ERP o lê. Não existe hoje; o dicionário só tem o momento do imobiliário (`Cad_Regime_Geral_Imobiliario.Momento_Fato_Gerador`, art. 254 da LC), que **continua onde está** e não é duplicado.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Fato_Gerador` | identificador | |
| `ID_Hipotese_Fato_Gerador` | referência (`Cad_Classe_Sistema`, domínio = `hipotese_fato_gerador`) --- identidade | Domínio novo com 12 valores (Anexo A): bem material, bem imaterial e direito, transporte iniciado no País, transporte de carga iniciado no exterior, demais serviços, bem sem documento idôneo, aquisição em leilão ou licitação, compra de ente público, execução continuada, e as três modalidades de importação de bem material. |
| `Aplica_Ibs`, `Aplica_Cbs` | booleanos | Como na `Cad_Regra_Base_Calculo_Cbs` do documento 156 (Q156-12). O Decreto só regulamenta a CBS; o texto da LC vale para os dois. |
| `Momento_Fato_Gerador` | enumeração {entrega_disponibilizacao, ato_de_cessao, inicio_transporte, termino_transporte, termino_servico, constatacao, aquisicao, pagamento, primeira_entre_exigibilidade_e_pagamento, liberacao_despacho_consumo, liberacao_admissao_temporaria, lancamento_credito_tributario} | O evento. |
| `Fonte_Data` | enumeração {data_previsao_entrega, data_emissao_documento, data_entrega_comprovada, data_inicio_transporte, data_termino_transporte, data_termino_servico, data_ato, data_pagamento, data_emissao_fatura, data_liberacao_aduaneira, data_constatacao, data_aquisicao} | De que data do registro o ERP lê o evento. |
| `Fonte_Data_Subsidiaria` | enumeração (os mesmos valores), opcional | Quando falta a primeira: no bem material, a data de emissão (Decreto, art. 11, § 9º). |
| `Criterio_Exigibilidade` | enumeração {emissao_fatura, medicao_aceita, vencimento_contratual, a_definir}, opcional | Só na execução continuada: o que "constitui o direito de receber" (Decreto, art. 11, § 3º, I e § 4º). Carga `a_definir` até o contador responder (Q157-C4); `a_definir` gera aviso, não presume a fatura. |
| `Origem_Regra` | enumeração {lc, decreto, lc_e_decreto} | Onde o Decreto vai além da LC (fornecimento de bem material e imaterial, exigibilidade, data prevista de entrega) a linha leva `decreto` e vai ao contador. |
| `Fundamento_Legal` | texto | LC e Decreto. |
| `Origem_Valor` | enumeração {texto_expresso, resposta_do_gestor, a_confirmar} | Como em `Cad_Adiantamento_Regra_Tributacao`. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

**Como o Motor escolhe a linha.** Pela natureza do item (bem, serviço, transporte, importação) e pelo modelo do documento. O usuário pode trocar a hipótese, com aviso. **Sem linha vigente para a hipótese, o ERP avisa; não presume "emissão" nem "pagamento".** O fato gerador do imóvel (locação, alienação, administração) fica em `Cad_Regime_Geral_Imobiliario`; a importação de serviço **não** tem linha própria, porque a LC, art. 64, § 5º, I, a e o Decreto, art. 69, I a mandam seguir o momento do fornecimento (bem imaterial, demais serviços, execução continuada), e a linha dessa natureza vale.

## 3.3 A data do fato gerador gravada na nota

Hoje só a NFS-e paulistana grava a data do fato gerador (`Mov_Nfse_Rps.Data_Fato_Gerador`). A alíquota do definitivo (LC, art. 10, § 4º, II, a) e a PTAX (Decreto, art. 13, § 4º, a data é o **dia anterior** ao fato gerador, regra do documento 156) dependem dessa data, e o evento 112150 (data prevista de entrega) a muda depois da emissão. Sem o retrato, o cálculo não se reproduz.

Em `Mov_Nota_Fiscal_Saida_Item` e em `Mov_Nota_Fiscal_Entrada_Item` entram três campos (padrão do `Competencia_Abatimento` e do `Valor_Tributo`: um retrato da época):

| Campo | Tipo | Descrição |
|---|---|---|
| `Data_Fato_Gerador` | data, opcional | A data que o ERP usou. Vazia quando não há linha de regra vigente (e então há aviso). |
| `Criterio_Data_Fato_Gerador` | enumeração (os valores de `Fonte_Data`), opcional | De onde a data veio. Com prova em contrário da data prevista (Decreto, art. 11, § 8º), passa a `data_entrega_comprovada` e o usuário informa a data. |
| `ID_Regra_Fato_Gerador` | referência (`Cad_Regra_Fato_Gerador`), opcional | A versão da regra usada. |

Em `Mov_Apuracao_Tributo_Item` entra **`Competencia_Debito`** (competência, opcional) para IBS e CBS: o período de apuração em que o débito de cada item consta (Decreto, art. 11, § 5º, I, b e II, b; art. 43). Deriva-se de `Data_Fato_Gerador`, mas é gravada pelo mesmo motivo: o evento 112150 mexe na data. A descrição de `Mov_Cbs_Apuracao_Espelho.Periodo` ("os documentos entram por data de emissão", ambiente beta) passa a registrar que o espelho é da Plataforma e que a competência do ERP segue o fato gerador.

## 3.4 Pagamento antecipado: três colunas em `Cad_Adiantamento_Regra_Tributacao`

O documento 153 desenhou a antecipação (D-N435 e D-N436: IBS e CBS no recebimento). O texto da LC e do Decreto confirma o momento, e acrescenta três pontos.

| Coluna nova | Tipo | Descrição |
|---|---|---|
| `Criterio_Data_Aliquota` | enumeração {menor_entre_emissao_documento_e_pagamento, data_pagamento, a_definir}, opcional | A alíquota da antecipação é a vigente na data da emissão do documento fiscal do pagamento ou na do pagamento, **a que vier primeiro** (LC, art. 10, § 4º, I, a, 2; Decreto, art. 11, § 5º, I, a, 2). Carga: `menor_entre_emissao_documento_e_pagamento` nas linhas de CBS e IBS, `texto_expresso`. Vazio nas linhas federais (PIS, Cofins, IRPJ, CSLL), onde não se aplica. O dicionário dizia só "alíquota do local" (Q128-6) e silenciava sobre a data. |
| `Prazo_Maximo_Dias_Ate_Fornecimento` | número, opcional | **Reserva** da regra dos 5 dias (LC, art. 10, § 7º). O Decreto não a regulamentou. Vazio significa que a regra não existe; o ERP não presume. Entra por versão nova da linha quando o regulamento definir. |
| `Periodo_Debito_Antecipacao` | enumeração {periodo_do_pagamento, periodo_do_fornecimento}, opcional | Idem: em que período a antecipação consta como débito, nas hipóteses que o regulamento vier a definir. |

**Duas atualizações de texto e de carga.** (a) Nas duas linhas de CBS e IBS, `Origem_Valor` passa de `resposta_do_gestor` para `texto_expresso` no que toca ao **momento** (o recebimento está no texto: LC, art. 10, § 4º, I; Decreto, art. 11, § 5º, I), e o `Fundamento_Legal` passa a citar também o Decreto, art. 11, § 5º. A `Base_Calculo` continua `resposta_do_gestor` até o contador validar (Q153-C1). (b) A cadeia da competência do documento 153 (data prevista, depois data de saída, depois emissão) vem da cartilha do CG-IBS. O Decreto diz data prevista e, na falta dela, **data de emissão**; "data de saída" não está no texto. Mantenho a cadeia como está e pergunto ao contador (Q157-C2).

**O excesso da antecipação deixou de ser crédito.** O texto de `Mov_Credito_Aplicacao_Tributo` diz que o excesso "é crédito do contribuinte, derivado". Depois da LC 227 (LC, art. 10, § 4º, II, c) aplicam-se as regras do pagamento indevido ou a maior: o Decreto, art. 38, só admite a restituição se a operação **não** gerou crédito ao adquirente e o fornecedor prova ter assumido o encargo. Em `Mov_Credito_Aplicacao_Tributo` entram:

| Campo | Tipo | Descrição |
|---|---|---|
| `Adquirente_Tomou_Credito` | booleano, opcional | A condição do art. 38, I. Sem a marca, o ERP avisa; não bloqueia. |
| `ID_Perdcomp` | referência (`Mov_Perdcomp`), opcional | O pedido de restituição do excesso (`Mov_Perdcomp.Tipo_Documento` já tem `pedido_restituicao`). |

## 3.5 Execução continuada: a data da exigibilidade

Na execução continuada o fato gerador é a primeira data entre a exigibilidade da parcela e o pagamento (LC, art. 10, § 3º). O contrato periódico sem título (`Mov_Gestao_Contrato_Apuracao` com `ID_Titulo` vazio) não tem a data em que o direito de receber se constitui. Em `Mov_Gestao_Contrato_Apuracao` entra **`Data_Exigibilidade`** (data, opcional): a data que o critério da regra (`Criterio_Exigibilidade`: fatura, medição aceita, vencimento contratual) indica. O fato gerador (a menor entre essa data e a primeira baixa, `Mov_Titulo_Baixa.Data_Baixa`) **se deriva**; o retrato fica no item da nota (3.3).

## 3.6 O que não crio, e dois acertos pequenos

- **`Mov_Fornecimento_Antecipacao` não se cria.** O nome vem da fila do documento 94, mas a antecipação já tem entidades: `Cad_Adiantamento_Regra_Tributacao`, `Mov_Credito` (tipo adiantamento), `Mov_Credito_Aplicacao_Tributo` (o abatimento no fornecimento) e `Mov_Credito_Ajuste_Documento` (o adiantamento devolvido). O que faltava são as colunas acima e o ajuste do capítulo 4.
- **Imóvel não oneroso.** O Decreto, art. 363, § 3º, diz que na locação não onerosa o fato gerador é o fornecimento e na administração não onerosa é o término. Em `Cad_Regime_Geral_Imobiliario` entra a coluna **`Momento_Fato_Gerador_Nao_Oneroso`** (enumeração {fornecimento, termino_administracao}, opcional): vazia onde não há regra.
- **Importação de bem material.** A LC, arts. 65 e 67, e o Decreto, arts. 75 e 78, dão três momentos conforme o despacho (liberação para consumo, liberação na admissão temporária, lançamento do crédito tributário). Entram como três linhas do catálogo (Anexo A); o B1 detalha o resto.
- **Nota de saída sem os campos do pagamento antecipado.** Notas de entrada, CT-e, NFCom, NFAg, NFGás e NF3e têm `Tipo_Pagamento_Antecipado` e `Chave_Dfe_Pagamento_Antecipado`; **não achei** na nota de saída. A nota de fornecimento tem de citar a nota da antecipação (NT 2025.002). Depende da NT; peço à equipe conferir (Q157-E2) antes de propor campo.


# 4. Ajuste, devolução e cancelamento da operação (B0a-3)

## 4.1 O que o texto pede

O Decreto, art. 57, trata a **devolução** (desfazimento depois do fornecimento) e o **cancelamento** (antes). A base e a alíquota são as da operação original (Decreto, art. 13, § 6º e art. 18; LC, art. 12, § 7º e art. 17). Quem emite o documento: na devolução, o adquirente se for emitente de documento fiscal, senão o fornecedor; no cancelamento, o fornecedor (art. 57, § 6º). Vedado cancelar operação já **atestada** pelo destinatário (§ 7º). Os efeitos dependem de a operação ter gerado crédito ao adquirente.

**Operação que gerou crédito (art. 57, § 2º).** Sai um documento fiscal no valor devolvido ou cancelado.

- **Adquirente**, nesta ordem: estorna o crédito a apropriar; estorna o crédito apropriado e não utilizado; gera débito do mesmo valor se o crédito já foi apropriado e utilizado.
- **Fornecedor**: estorna a parte do débito ainda não extinta. Na parte já extinta, depende da **modalidade de extinção do art. 26**: pelo split payment (III) recebe transferência em dinheiro; por compensação (I) tem o crédito restabelecido, com a data e as características originais (§ 5º); por pagamento do contribuinte (II) ou do responsável (V) apropria crédito; por recolhimento pelo adquirente (IV) segue o art. 487 (transferência em dinheiro). Se o adquirente já usou o crédito, o fornecedor recebe de volta à medida que o débito for extinto (§ 2º, II, c).

**Operação que não gerou crédito (art. 57, § 3º).** Só o lado do fornecedor, com as mesmas saídas, e condicionado ao art. 38, II (o fornecedor prova ter assumido o encargo ou estar autorizado por terceiro), que pode ser verificado depois (§ 8º, I). Se o adquirente emite documento fiscal, a emissão da devolução supre a autorização (§ 9º). O adquirente do regime regular não tem débito pelo destaque da devolução (§ 8º, II). A Receita transfere o dinheiro em até três dias úteis (§ 4º) e o contribuinte guarda a prova (§ 10).

**Erro na emissão do documento (Decreto, arts. 59 e 61).** O fornecedor emite documento com o valor a reduzir e os efeitos são os mesmos, em outras palavras: no art. 59 o fornecedor restabelece o crédito se a extinção foi por compensação e apropria crédito nas demais modalidades, **sem transferência em dinheiro**. Condiciona-se ao **aceite do adquirente por documento fiscal** (art. 59, § 1º; art. 61, § 2º). Esses dois artigos não têm correspondente na LC (só o gancho do art. 47, § 12). **O texto não trata de desconto posterior ou abatimento sem erro e sem devolução**: o Decreto, art. 13, § 3º, só exclui da base o desconto que consta do documento e não depende de evento posterior. Fica fora do desenho e vai ao contador (Q157-C1).

**O que a LC 227 mudou.** No art. 47 da LC: nova redação do § 8º (devolução e cancelamento com adquirente fora do regime regular: o fornecedor apropria crédito ou estorna débito); **§ 12 novo** (no regime regular, o regulamento disciplina o débito ou estorno do adquirente e o crédito ou estorno do fornecedor); **§ 13 novo** (débito extinto por split: o regulamento pode prever a transferência ao fornecedor em até três dias úteis, e o valor transferido **não** é crédito do fornecedor). O art. 57 do Decreto é a regulamentação disso. No art. 10 da LC, o § 5º (distrato do pagamento antecipado segue o cancelamento) é novo (3.1).

## 4.2 O que o dicionário já tem e o que falta

O dicionário tem `Mov_Devolucao_Compra` e `Mov_Devolucao_Venda` (nota original, data, motivo, documento de devolução), `Mov_Estoque_Abertura_Cbs_Estorno` (o precedente da divisão em três ramos, só para o estoque de abertura), `Mov_Credito_Ajuste_Documento` (o ajuste pendente do adiantamento devolvido, documento 153), `Mov_Apuracao_Tributo_Item_Complemento` (tipos `devolucao_tributo`, `estorno_credito`, `valor_ajuste_ibs_cbs`) e `Mov_Credito_Fiscal` (com `Modalidade_Extincao_Debito` de três valores: `split_payment`, `rad`, `pcont`).

Faltam: (1) uma entidade do **ajuste da operação** e do **efeito por lado**; (2) em `Mov_Credito_Fiscal`, a origem "restabelecimento" e "ajuste da operação" e o status "estornado"; (3) duas das cinco modalidades do art. 26, **compensação (I)** e **pagamento pelo responsável (V)**, que o art. 57 trata de forma diferente; (4) o papel de quem emite, o aceite do adquirente (arts. 59 e 61), a condição do art. 38, II e a prova guardada (§ 10); (5) o ajuste da apuração positivo e negativo (art. 44, § 1º): o `Valor_Ajuste_Apuracao` do estoque de abertura aponta para nada.

## 4.3 Entidade nova: `Mov_Cbs_Ajuste_Operacao`

O cabeçalho do ajuste (uma devolução, um cancelamento ou uma correção de erro). Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Cbs_Ajuste_Operacao` | identificador | |
| `ID_Empresa` | referência (`Cad_Empresa`) | |
| `Papel_Empresa` | enumeração {adquirente, fornecedor} | O lado em que a empresa está nesta operação. |
| `ID_Tipo_Ajuste` | referência (`Cad_Classe_Sistema`, domínio = `tipo_ajuste_operacao_cbs`) | Domínio novo, aberto: `devolucao`, `cancelamento`, `correcao_erro`, `ajuste_acrescimo`. O valor para desconto posterior **não entra** até o contador responder (Q157-C1). |
| `ID_Documento_Fiscal_Original` | referência (`Mov_Documento_Fiscal`) | A operação que se desfaz ou corrige. A base e a alíquota vêm dela, nunca são digitadas. |
| `ID_Documento_Fiscal_Ajuste` | referência (`Mov_Documento_Fiscal`), opcional | O documento do ajuste; vazio até ser emitido. |
| `Papel_Emitente_Documento` | enumeração {adquirente, fornecedor, plataforma_digital} | Quem emite (art. 57, § 6º; na plataforma digital, ela emite: art. 59, § 2º). |
| `Data_Ajuste` | data | |
| `Aceite_Adquirente` | enumeração {nao_exigido, pendente, aceito} | O aceite por documento fiscal dos arts. 59 e 61. |
| `ID_Documento_Fiscal_Aceite` | referência (`Mov_Documento_Fiscal`), opcional | O documento do aceite. |
| `Condicao_Art_38` | enumeração {nao_aplicavel, pendente_verificacao, suprida_pelo_documento_do_adquirente, comprovada} | A condição do art. 38, II, nas operações que não geraram crédito (art. 57, §§ 8º e 9º). |
| `Operacao_Atestada_Destinatario` | booleano, opcional | O art. 57, § 7º veda cancelar operação atestada. O ERP **avisa**; não bloqueia. Qual evento conta como "atestar" vai ao contador (Q157-C6). |
| `ID_Dfe_Evento` | referência (`Mov_Dfe_Evento`), opcional | O evento fiscal do ajuste (112140 no cancelamento de antecipação). |
| `ID_Motivo` | referência (`Cad_Classe_Sistema`, domínio = `motivo_devolucao`), opcional | O motivo. |
| `ID_Documento_Prova` | referência (`Cad_Documento`), opcional | A prova guardada (art. 57, § 10). |
| `ID_Credito_Ajuste` | referência (`Mov_Credito_Ajuste_Documento`), opcional | Liga o adiantamento devolvido do documento 153, sem duplicar campo. |
| `Situacao` | enumeração {calculado, lancado, cancelado} | O mesmo padrão do estorno do estoque de abertura. |

Aviso (não bloqueio): quando o tipo do ajuste não bate com a data do fornecimento (devolução antes do fornecimento ou cancelamento depois), e quando há confirmação da operação pelo destinatário antes do cancelamento.

## 4.4 Entidade nova: `Mov_Cbs_Ajuste_Operacao_Efeito`

Uma linha por efeito do ajuste, por lado. Sem vigência. **Serve também ao estorno do uso e consumo pessoal** do documento 156 (Q156-5): exatamente um entre `ID_Cbs_Ajuste_Operacao` e `ID_Uso_Consumo_Pessoal_Item` fica preenchido (o mesmo padrão "exatamente um entre estes" de `Mov_Empreendimento_Deducao`).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Cbs_Ajuste_Operacao_Efeito` | identificador | |
| `ID_Cbs_Ajuste_Operacao` | referência (`Mov_Cbs_Ajuste_Operacao`), opcional | |
| `ID_Uso_Consumo_Pessoal_Item` | referência (`Mov_Uso_Consumo_Pessoal_Item`, documento 156), opcional | O estorno do art. 64, §§ 1º e 2º do Decreto. |
| `ID_Apuracao_Origem` | referência (`Mov_Apuracao_Tributo_Item`) | O item de CBS original. |
| `Lado` | enumeração {adquirente, fornecedor} | |
| `Efeito` | enumeração {estorno_credito_a_apropriar, estorno_credito_apropriado_nao_utilizado, debito_por_credito_utilizado, estorno_debito_nao_extinto, transferencia_em_dinheiro, restabelecimento_credito, apropriacao_credito} | O resultado da matriz (4.5). |
| `Modalidade_Extincao_Debito` | enumeração {split_payment, rad, pcont, compensacao, responsavel}, opcional | Como o débito do fornecedor foi extinto, nas linhas do fornecedor (art. 26: I compensação, II pagamento do contribuinte, III split, IV recolhimento pelo adquirente, V pagamento pelo responsável). |
| `Valor_Efeito` | número | |
| `Competencia_Apuracao` | competência | O período em que o efeito entra como ajuste positivo ou negativo (Decreto, art. 44, § 1º). |
| `ID_Credito_Fiscal` | referência (`Mov_Credito_Fiscal`), opcional | O crédito tocado ou criado. |
| `ID_Titulo` | referência (`Mov_Titulo`), opcional | A transferência em dinheiro, quando houver. |
| `Valor_Multa_Mora`, `Valor_Juros_Mora` | números, opcionais | Só no `debito_por_credito_utilizado`, se o contador confirmar os acréscimos do art. 44, § 2º (Q157-C8). |
| `ID_Acrescimo_Legal` | referência (`Cad_Acrescimo_Legal_Cbs`), opcional | A versão do parâmetro usada. |
| `ID_Cbs_Ajuste_Efeito_Regra` | referência (`Cad_Cbs_Ajuste_Efeito_Regra`), opcional | A linha da matriz que deu o efeito. |
| `ID_Espelho_Conta` | referência (`Mov_Cbs_Apuracao_Espelho_Conta`), opcional | Conferência com a Plataforma. |

A soma dos ramos do adquirente tem de fechar com o valor do documento de ajuste; se não fechar, **aviso**. O que se deriva **não** se grava: o efeito de cada parcela (sai da matriz), o prazo de três dias úteis, o valor do fornecedor (vem do documento) e a base e a alíquota.

## 4.5 Entidade nova: `Cad_Cbs_Ajuste_Efeito_Regra`

A matriz do Decreto, art. 57, §§ 2º e 3º, e arts. 59 e 61, como parâmetro com vigência: o Motor lê a matriz e o ERP não esconde a regra no código (a LC 227, art. 47, § 12, diz que o regulamento "poderá" variar). Carga de **21 linhas** provisórias no Anexo B. **Vale a linha mais específica:** a linha com `ID_Tipo_Ajuste` preenchido vence a de tipo vazio (a correção de erro, que só tem as linhas do fornecedor, usa as do adquirente da regra geral).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Cbs_Ajuste_Efeito_Regra` | identificador | |
| `ID_Tipo_Ajuste` | referência (`Cad_Classe_Sistema`, domínio = `tipo_ajuste_operacao_cbs`), opcional | Vazio vale para qualquer tipo (devolução e cancelamento têm a mesma matriz). |
| `Lado` | enumeração {adquirente, fornecedor} --- identidade | |
| `Operacao_Gerou_Credito` | booleano --- identidade | O art. 57, § 2º (gerou) ou § 3º (não gerou). |
| `Parcela` | enumeração {credito_a_apropriar, credito_apropriado_nao_utilizado, credito_utilizado, debito_nao_extinto, debito_extinto} --- identidade | A parcela sobre a qual o efeito incide. |
| `Modalidade_Extincao_Debito` | enumeração {split_payment, rad, pcont, compensacao, responsavel}, opcional --- identidade | Vazio vale para qualquer modalidade. |
| `Efeito` | enumeração (os valores de `Mov_Cbs_Ajuste_Operacao_Efeito.Efeito`) | |
| `Ordem` | número | Nas parcelas do adquirente, a ordem do art. 57, § 2º, I. |
| `Fundamento_Legal` | texto | Decreto e LC. |
| `Origem_Regra` | enumeração {lc, decreto, lc_e_decreto} | Os arts. 59 e 61 são só do Decreto. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

## 4.6 Mudanças em entidades existentes

| Entidade | Mudança |
|---|---|
| `Mov_Credito_Fiscal` | `Origem` ganha `ajuste_operacao` (crédito que o fornecedor apropria) e `restabelecimento` (crédito de volta com a data original); `Status` ganha `estornado`; `Modalidade_Extincao_Debito` ganha `compensacao` e `responsavel`; campo novo **`ID_Cbs_Ajuste_Operacao_Efeito`** (referência, opcional). No restabelecimento, `Data_Apropriacao` é a da original, para preservar o prazo de cinco anos (art. 54). |
| `Mov_Devolucao_Compra` e `Mov_Devolucao_Venda` | Campo novo **`ID_Cbs_Ajuste_Operacao`** (referência, opcional): a devolução física liga ao ajuste fiscal. O documento de devolução pode vir do cliente (nota de entrada) ou ser emitido por nós; quem emite está em `Papel_Emitente_Documento`. |
| `Mov_Estoque_Abertura_Cbs_Estorno` | Campo novo **`ID_Cbs_Ajuste_Operacao_Efeito`** (referência, opcional): o `Valor_Ajuste_Apuracao` passa a apontar para a linha do efeito. O `Valor_Acrescimos` é substituído pelo par multa e juros do capítulo 5. |
| `Mov_Credito_Ajuste_Documento` | Só texto: o cancelamento do adiantamento segue o art. 57 (Decreto, art. 11, § 6º), e o ajuste liga a este registro por `ID_Credito_Ajuste`. |

O **estorno do uso e consumo pessoal** (documento 156) usa a mesma linha de efeito, que guarda a divisão entre crédito não utilizado e utilizado. O art. 64 do Decreto só manda estornar e não detalha os ramos; a divisão em três ramos para o uso pessoal e para o perecimento (art. 48) vai ao contador (Q157-C8), e a carga é provisória.

Domínios novos em `Cad_Classe_Sistema`: `tipo_ajuste_operacao_cbs` (4 valores) e `hipotese_fato_gerador` (12 valores, capítulo 3).


# 5. Acréscimos legais do art. 27

## 5.1 O que o texto pede

O pagamento depois do vencimento (o último dia útil do mês seguinte, art. 45 do Decreto) leva, pelo Decreto, art. 27, § 2º a § 5º (LC, art. 29, §§ 2º a 5º): **(I) multa de mora de 0,33% por dia de atraso**, do dia seguinte ao vencimento até o pagamento (§ 3º), **limitada a 20%** (§ 4º); **(II) juros pela Selic**, do primeiro dia do mês seguinte ao vencimento até o mês anterior ao do pagamento, **mais 1% no mês do pagamento** (§ 2º, II). Os juros incidem também sobre as multas punitivas não pagas (§ 5º, acrescentado pela LC 227). As multas punitivas são calculadas depois dos juros (Decreto, art. 572; LC, art. 341-B) e, até a notificação do lançamento de ofício, a multa de mora **não** se soma quando o tributo já serviu de base à multa punitiva (Decreto, art. 574, parágrafo único). O § 1º (excesso de pagamento devolvido em três dias úteis) e o § 6º (atraso do banco) são prazo, não acréscimo.

A LC 227 **não mexeu** nos §§ 2º a 4º do art. 29 da LC (0,33%, 20%, Selic mais 1%); mexeu no § 1º e acrescentou o § 5º.

**Quem usa.** O Decreto tem **22 artigos** que remetem ao art. 27 (multa e juros), em faixas diferentes, de regimes que não são de comércio exterior (estorno de crédito, plataforma digital, responsável, Zona Franca, áreas de livre comércio, Repetro, Reporto, Reidi, ZPE e outros); outros falam só em "acréscimos legais"; o art. 160, § 2º (admissão temporária) diz só juros da Selic; o art. 446, parágrafo único, **afasta** juros e penalidade (tributo pago conforme resposta de consulta). O Anexo C lista as **28 hipóteses** com a faixa e o termo inicial de cada uma.

## 5.2 O que o dicionário já tem

Nenhum parâmetro do art. 27. Os valores 0,33%, 20% e "Selic mais 1%" aparecem **só em texto de descrição** de `Mov_Estoque_Abertura_Cbs_Estorno.Valor_Acrescimos`. Há parâmetros parecidos, de outra base legal: `Cad_Regra_Ressarcimento_Cbs.Percentual_Juros_Mes_Pagamento` (Decreto, art. 39, § 15: a correção do que o **Fisco** deve) e `Mov_Cbs_Pedido_Ressarcimento.Valor_Correcao_Selic`. As séries mensais já existem (`Cad_Serie_Cotacao`, tipo `indice_financeiro`, `Mov_Serie_Cotacao_Valor`); a Selic é mais uma série. A multa e os juros efetivamente cobrados já são gravados onde a Receita os devolve (`Mov_Cbs_Apuracao_Espelho_Conta`: `Valor_Multa`, `Valor_Juros`, `Valor_Principal`, `Valor_Total` da composição do DARF).

## 5.3 Entidade nova: `Cad_Acrescimo_Legal_Cbs`

Parâmetro com vigência (identidade e versão), uma linha vigente por vez.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Acrescimo_Legal` | identificador | |
| `Percentual_Multa_Mora_Dia` | número | 0,33 (Decreto, art. 27, § 3º). |
| `Percentual_Multa_Mora_Limite` | número | 20 (§ 4º). |
| `ID_Serie_Cotacao_Juros` | referência (`Cad_Serie_Cotacao`) | A série da Selic (acumulada no mês). A fonte e o arredondamento vão ao contador e à equipe (Q157-C7 e Q157-E4). |
| `Meses_Defasagem_Inicio_Juros` | número | 1: os juros contam do primeiro dia do mês seguinte ao vencimento (§ 2º, II). |
| `Percentual_Juros_Mes_Pagamento` | número | 1 (§ 2º, II, parte final). |
| `Juros_Incidem_Sobre_Multa_Punitiva` | booleano | Verdadeiro desde a LC 227 (§ 5º). |
| `Multa_Punitiva_Apos_Juros` | booleano | Verdadeiro: a multa punitiva se calcula depois dos juros (Decreto, art. 572). |
| `Multa_Mora_Afastada_Com_Multa_Punitiva` | booleano | Verdadeiro até a notificação do lançamento de ofício (art. 574, parágrafo único). |
| `Fundamento_Legal` | texto | Decreto, art. 27, §§ 2º a 5º; LC, art. 29, §§ 2º a 5º. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | A vigência inicial provisória é 01/01/2027 (início da cobrança); o contador confirma (Q157-C7). |

**Sem valor padrão escondido:** sem linha vigente, o ERP avisa; não presume 0,33%.

## 5.4 Entidade nova: `Cad_Acrescimo_Legal_Hipotese`

Parâmetro com vigência. Cada módulo (B1, B3, B5, importação) consulta a hipótese em vez de repetir o percentual: é a "condição do Motor como coluna". Carga de **28 linhas** provisórias no Anexo C.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Acrescimo_Legal_Hipotese` | identificador | |
| `ID_Hipotese_Acrescimo` | referência (`Cad_Classe_Sistema`, domínio = `hipotese_acrescimo_cbs`) --- identidade | Domínio novo, aberto, com 28 valores. |
| `Faixa_Acrescimo` | enumeração {multa_e_juros_art_27, somente_juros_selic, acrescimos_genericos, afasta_acrescimos} | O que o artigo manda: M+J do art. 27, só a Selic, "acréscimos legais" sem remeter ao art. 27, ou afasta. |
| `Aplica_Multa`, `Aplica_Juros`, `Aplica_Limite_Multa` | booleanos, opcionais | Derivam da faixa, mas são colunas porque o Motor lê cada uma. Vazios nas linhas de faixa `acrescimos_genericos`, onde o texto diz só "acréscimos legais": o ERP avisa "faixa não definida" até o contador responder (Q157-C7), e não presume multa nem juros. |
| `Termo_Inicial` | enumeração {vencimento_do_debito, fato_gerador, data_operacao, emissao_documento_fiscal, liberacao_declaracao_admissao_ou_registro_exportacao, apropriacao_indevida_ou_exigibilidade, nao_definido_no_texto, nao_se_aplica} | De quando contam os acréscimos. Onde o texto não diz, `nao_definido_no_texto`, com aviso, e o contador responde (Q157-C7). |
| `Fundamento_Legal` | texto | O artigo do Decreto e o da LC. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

## 5.5 Onde o resultado entra

Nas movimentações que calculam acréscimo entra o par **`Valor_Multa_Mora`** e **`Valor_Juros_Mora`** (números, opcionais) e **`ID_Acrescimo_Legal`** (a versão usada, como `ID_Presuncao_Acrescimo` faz no IRPJ). O valor é calculado (deriva de principal, vencimento, pagamento e Selic) e fica gravado **só para conferir com a Receita**. Neste documento o par entra em `Mov_Estoque_Abertura_Cbs_Estorno` (substitui `Valor_Acrescimos`, que não separa os juros sobre multa punitiva) e em `Mov_Cbs_Ajuste_Operacao_Efeito` (capítulo 4). Os documentos do B1, do B3 e do B5 acrescentam o par onde os seus artigos calcularem.

**Parâmetros parecidos que não misturo:** a proporção de 0,033% por dia da admissão temporária (Decreto, art. 160, § 1º), a multa de 3% ao mês do split (art. 579, II), a correção do ressarcimento pelo Fisco (art. 39, §§ 15 e 17) e a UPF de R$ 200 (art. 573; LC, art. 341-C). A UPF e as multas dos arts. 341-A a 341-H da LC têm decisão própria na Q157-13.

# 6. Valor de mercado da locação de imóvel

## 6.1 O que o texto pede

O Decreto, art. 364, §§ 7º a 10, trata a base nas operações não onerosas ou abaixo do mercado. Para locação, cessão onerosa e arrendamento, sucessivamente: (a) a operação mais recente do próprio fornecedor com partes não relacionadas, em imóvel de características e localização semelhantes; (b) o valor calculado sobre o **valor de referência do Sinter** por "percentual determinado pela autoridade fiscal", com limites mínimo e máximo fixados em ato conjunto da RFB e do CGIBS (§ 8º, II, b). O percentual é revisado periodicamente e pode variar por tipo de imóvel, região e outros critérios (§ 9º). Sem apuração possível, vale o valor do art. 375, § 2º (§ 10). Para os direitos reais, a alínea b do inciso III do § 8º usa parâmetros do ato conjunto "para cada tipo de direito real". O fato gerador na locação não onerosa é o fornecimento (art. 363, § 3º, I), e não o pagamento.

**Só o Decreto regulamenta.** Os arts. 255 e 256 da LC (base da locação e valor de referência) **não foram alterados** pela LC 227 e não têm os §§ 7º a 10. O Decreto também exclui da base o **foro anual e a taxa de ocupação** (art. 364, § 3º, III), que a LC, art. 255, § 2º, não cita, desde que haja "prova inequívoca do pagamento" (§ 4º); benfeitorias e outras contraprestações do locatário **não** se deduzem (§ 2º). Na locação entre partes relacionadas, os limites da pessoa física contam pelo **valor de mercado** (art. 382, § 8º), e a fração ideal conta como imóvel distinto (§ 9º).

## 6.2 O que o dicionário já tem e o que falta

Tem `Cad_Imovel`, `Mov_Locacao_Faturamento` (aluguel, exclusão de IPTU, condomínio e emolumentos, redutor social), `Mov_Locacao_Limite_Pf` e `Cad_Locacao_Obrigacao_Emissao`. **Não tem** valor de referência do imóvel, parâmetro de percentual, nem o foro e a taxa de ocupação. As três entidades de valor de mercado do B0a-2 estão no documento 156; **conferi lá** para não duplicar.

## 6.3 Entidade nova: `Cad_Valor_Mercado_Locacao_Parametro`

Parâmetro com vigência. **Carga vazia** até o ato conjunto sair; sem linha, o ERP avisa e não presume percentual. Mantenho o nome do documento 94 e cubro também os direitos reais pela coluna `Tipo_Operacao`.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Valor_Mercado_Locacao_Parametro` | identificador | |
| `Tipo_Operacao` | enumeração {locacao_cessao_arrendamento, direito_real} --- identidade | A servidão, a cessão de espaço, a permissão de uso e o direito de passagem seguem a locação (Decreto, art. 360, § 2º). |
| `ID_Tipo_Imovel` | referência (`Cad_Classe_Sistema`, domínio existente), opcional --- identidade | O percentual pode variar por tipo (§ 9º). |
| `Uso_Imovel` | enumeração (a do `Cad_Imovel`), opcional --- identidade | |
| `ID_Estado`, `ID_Municipio` | referências (`Cad_Estado`, `Cad_Municipio`), opcionais --- identidade | A região. |
| `Tipo_Direito_Real` | texto, opcional | Só em `direito_real` (o ato conjunto fixa por tipo). |
| `Percentual_Valor_Referencia` | número | |
| `Periodicidade_Percentual` | enumeração {mensal, anual, a_definir} | O texto não diz se o percentual é mensal ou anual. Sem padrão escondido: `a_definir` até o contador responder (Q157-C9). |
| `Percentual_Minimo`, `Percentual_Maximo` | números, opcionais | Os limites do ato conjunto. |
| `Ato_Conjunto` | texto | Número e data do ato. |
| `Fundamento_Legal` | texto | |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

## 6.4 Entidade nova: `Mov_Imovel_Valor_Referencia`

O valor de referência do Sinter é dado publicado, que o ERP **não deriva**; a atualização pelo IPCA (art. 366, § 3º, III) o ERP também não recalcula: guarda o que o Sinter mostra. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Imovel_Valor_Referencia` | identificador | |
| `ID_Imovel` | referência (`Cad_Imovel`) | |
| `Data_Referencia` | data | |
| `Valor_Referencia` | número | |
| `Origem` | enumeração {sinter, impugnacao_deferida} | A impugnação do art. 367 só como origem do valor corrigido. |
| `Situacao_Dado` | enumeração {provisorio, validado} | |

## 6.5 Mudanças em entidades existentes

| Entidade | Mudança |
|---|---|
| `Cad_Regra_Valor_Mercado` (documento 156) | **Duas linhas novas** na carga do Anexo E do documento 156, que passa de 8 para 10: método 9 `percentual_valor_referencia_imovel` (Decreto, art. 364, § 8º, II, b; § 9º) e método 10 `estimativa_valor_imovel` (art. 364, § 10; art. 375, § 2º). O critério (a) já é o método 1 ou 2. |
| `Mov_Valor_Mercado_Apuracao` (documento 156) | Duas colunas novas: **`ID_Valor_Mercado_Locacao_Parametro`** (referência, opcional) e **`ID_Imovel_Valor_Referencia`** (referência, opcional): o percentual e o valor de referência usados. "Características e localização semelhantes" não tem critério numérico: registro manual, com aviso. |
| `Mov_Locacao_Faturamento` | Quatro colunas: **`Valor_Foro_Taxa_Ocupacao`** (número, opcional); **`Comprovacao_Pagamento_Despesas`** (booleano, opcional; aviso se faltar, art. 364, § 4º); **`Valor_Contraprestacao_Nao_Monetaria`** (número, opcional; compõe a base, § 2º); **`ID_Apuracao_Valor_Mercado`** (referência, opcional; a base quando a locação é não onerosa ou abaixo do mercado). O `Valor_Aluguel` pode ser zero na locação gratuita, que passa a ter linha de faturamento para existir o fato gerador "no fornecimento". |
| `Mov_Locacao_Limite_Pf` | Coluna **`Receita_Locacao_Valor_Mercado_Relacionada`** (número, opcional): o valor de mercado da locação entre partes relacionadas, que conta nos limites (art. 382, § 8º). Hoje a `Receita_Locacao` só soma o que foi cobrado. |


# 7. Transição de 2026 e redução de 0,1 ponto em 2027 e 2028 (B0a-4)

## 7.1 O que o texto pede

| Tema | Artigos | O que a norma diz |
|---|---|---|
| CBS em 2026 | LC, art. 346; Decreto, art. 582 | 0,9% sobre os fatos geradores de 2026. |
| IBS em 2026 | LC, art. 343 | 0,1%, só a parcela estadual. A arrecadação vai ao Comitê Gestor e ao fundo de compensação do ICMS: não é assunto do ERP. |
| Como se aplicam em 2026 | LC, art. 348, III; Decreto, art. 582, parágrafo único | Reduzidas na mesma proporção nas operações de alíquota reduzida; aplicadas nos regimes específicos, respeitadas as bases; fora combustíveis e biocombustíveis; não se aplicam ao optante do Simples Nacional. |
| Compensação em 2026 | LC, art. 348, I e II; Decreto, art. 583, I e II | O que for recolhido compensa o PIS e a Cofins do mesmo período; sem débito suficiente, compensa outro tributo federal ou é ressarcido em até 60 dias, mediante requerimento. |
| Dispensa de recolher | LC, art. 348, §§ 1º e 2º; Decreto, art. 464 e art. 583, §§ 1º e 2º | Fica dispensado quem cumprir as obrigações acessórias. O Decreto, art. 464, II, acrescenta quem for **desobrigado** delas (a LC não diz isso). A apuração de 2026 vale como informação (art. 464, § 1º). O PIS e a Cofins seguem devidos por inteiro. |
| Infração em 2026 | LC, art. 348, §§ 3º e 4º (**acrescidos pela LC 227**); Decreto, arts. 464, §§ 3º e 4º, e 583, §§ 3º e 4º | Lavrado auto por descumprir obrigação acessória, o sujeito passivo é intimado a suprir a omissão em **60 dias**; o atendimento extingue a penalidade. |
| Saldo de 2026 | Decreto, art. 465 | O saldo a recuperar em 31/12/2026 é desconsiderado a partir de 2027 e não é ressarcível. |
| CBS em 2027 e 2028 | LC, art. 347; Decreto, art. 585 | A alíquota fixada nos termos do art. 14, I, e §§ 2º e 3º da LC (lei da União ou a referência) **menos 0,1 ponto percentual**, exceto combustíveis do regime específico. |
| Como a redução se aplica | LC, art. 347, § 1º; Decreto, art. 585, § 1º | (I) proporcional à redução, nas operações de alíquota reduzida; (II) também nos regimes específicos, respeitadas as bases. |
| IBS em 2027 e 2028 | LC, art. 344 e parágrafo único | 0,05% estadual e 0,05% municipal; o inciso IV (**LC 227**) trata essas alíquotas como de referência para os arts. 189, § 2º, 485, § 8º, 486, § 13 e 487, § 12. |
| Combustíveis | LC, art. 347, § 2º; Decreto, art. 585, § 2º | Em 2027 e 2028 o IBS recolhido pelo art. 344, parágrafo único, III, pode ser deduzido da CBS a recolher no regime de combustíveis. |

**A unidade da redução.** A LC, art. 347, diz "0,1 (um décimo) ponto percentual". O Decreto, art. 585, diz "um décimo por cento", que é ambíguo. Que é **ponto** percentual confirma o Decreto, art. 425, II, a (TEF): a CBS de 2027 e 2028 é 0,9% quando a base é 1%.

**O que a LC 227 mudou:** acrescentou o art. 344, parágrafo único, IV; o art. 348, §§ 3º e 4º; e os arts. 341-A a 341-H (multas, com "tributo de referência" de 6% da CBS e 12% do IBS em 2026, art. 341-G, § 5º, III). **Não mexeu** nos arts. 343, 346 e 347 (conferi o art. 347 contra o texto do DOU).

## 7.2 O que o dicionário já tem

`Cad_Aliquota` (com vigência, `Eh_Aliquota_Referencia`, natureza efetiva ou teste; as linhas de 2026 são de teste); `Cad_Calendario_Transicao` (`fase_transicao`, `cobranca_efetiva` e a linha `reducao_cbs_art_585`, em pontos percentuais, 0,1 em 2027 e 2028, com a fórmula "na Q70"); `Mov_Apuracao_Tributo_Item` (`Aliquota_Nominal`, `Aliquota_Efetiva`, `ID_Calendario` da fase, sem guardar a redução aplicada); `Mov_Cbs_Apuracao_Espelho` e `Mov_Cbs_Pedido_Ressarcimento`; `Mov_Auto_Infracao` (sem o suprimento do art. 348, § 3º). **Não existe** `Mov_Cbs_Transicao_2026_Periodo` (só estava na fila) nem entidade de penalidades da LC 227.

## 7.3 Entidade nova: `Mov_Cbs_Transicao_2026_Periodo`

Uma linha por empresa e competência de 2026. Sem vigência. O ERP **não grava** o que se deriva (a CBS e o IBS informativos somam-se dos itens com alíquota de teste); grava só o que é decisão ou fato.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Cbs_Transicao_2026_Periodo` | identificador | |
| `ID_Empresa` | referência (`Cad_Empresa`) --- identidade | A matriz (a apuração é centralizada). |
| `Periodo` | competência --- identidade | Um mês de 2026. |
| `ID_Espelho` | referência (`Mov_Cbs_Apuracao_Espelho`), opcional | O espelho do mesmo mês. |
| `Situacao_Dispensa` | enumeração {dispensada_cumpriu_obrigacoes, dispensada_desobrigada, nao_dispensada, a_avaliar} | Decreto, art. 464, I e II; LC, art. 348, § 1º. Decisão de usuário com permissão. **Aviso**, não bloqueio, se marcada "dispensada" com obrigação acessória pendente no período. |
| `ID_Usuario_Decisao`, `Data_Decisao`, `Motivo_Decisao` | referência (`Cad_Usuario`), data, texto | Quem decidiu, quando e por quê. |
| `Valor_Recolhido_Cbs`, `Valor_Recolhido_Ibs` | números, opcionais | Só quando a empresa de fato recolheu (Decreto, art. 583). |
| `Valor_Compensado_Pis_Cofins` | número, opcional | Art. 583, I. |
| `Valor_Compensado_Outro_Tributo` | número, opcional | Art. 583, II, a. |
| `Valor_Ressarcimento_Pedido`, `Data_Pedido_Ressarcimento` | número e data, opcionais | Art. 583, II, b. A data limite (pedido mais 60 dias) se deriva do parâmetro de 7.5. |
| `ID_Perdcomp` | referência (`Mov_Perdcomp`), opcional | O pedido ou a compensação. |
| `ID_Calendario_Fase` | referência (`Cad_Calendario_Transicao`) | A linha `fase_transicao` de 2026 (como `Mov_Apuracao_Tributo_Item.ID_Calendario`). |
| `Fundamento_Legal` | texto | |

**Regra de texto, sem campo:** o saldo de 2026 não passa a 2027 (Decreto, art. 465); o Motor não o leva e `Mov_Cbs_Pedido_Ressarcimento` não aceita período de 2026 para saldo da apuração informativa (aviso). O art. 583 (valor efetivamente pago, ressarcível em 60 dias) e o art. 465 (saldo da apuração informativa, não ressarcível) são lidos como coisas diferentes; confirmo com o contador (Q157-C10).

## 7.4 Suprimento da omissão no auto de infração

Em `Mov_Auto_Infracao` entram quatro colunas (LC, art. 348, §§ 3º e 4º):

| Campo | Tipo | Descrição |
|---|---|---|
| `Regime_Suprimento_2026` | booleano, opcional | O auto é de obrigação acessória descumprida em 2026. |
| `Data_Intimacao_Suprimento` | data, opcional | |
| `Data_Atendimento_Suprimento` | data, opcional | |
| `Penalidade_Extinta` | booleano, opcional | Marcado pelo usuário. O prazo (intimação mais 60 dias) se deriva do parâmetro de 7.5; **aviso** se o atendimento passa do prazo. |

## 7.5 Parâmetros novos em `Cad_Calendario_Transicao`

O `Tipo_Valor` do calendário hoje é {percentual, fator, pontos_percentuais, data, booleano, fase}. Acrescenta-se **`numero`**, para os prazos em dias. Duas linhas novas (Ano = 2026; fim de vigência 31/12/9999; `Situacao_Dado = provisorio`), com valores novos no domínio `parametro_transicao` de `Cad_Classe_Sistema`:

| Código | Valor | Fundamento |
|---|---|---|
| `prazo_ressarcimento_transicao_2026` | 60 dias | Decreto, art. 583, II, b |
| `prazo_suprimento_intimacao_2026` | 60 dias | LC, art. 348, § 3º; Decreto, art. 464, § 3º |

Os percentuais de 6% e 12% do tributo de referência das multas (LC, art. 341-G, § 5º, III) **não entram agora**: só valem quando existir entidade de penalidades (Q157-13).

## 7.6 A redução de 0,1 ponto em 2027 e 2028

**Não crio linha de CBS de 2027 já líquida em `Cad_Aliquota`.** A alíquota fixada (lei ou referência) e a redução são coisas diferentes: a referência pode mudar por resolução do Senado no meio do ano (LC, art. 349, § 2º) sem mexer na redução.

- **Parâmetro.** Mantenho a linha do calendário (pontos percentuais, 0,1 em 2027 e 2028). O código `reducao_cbs_art_585` prende a regra à numeração do Decreto; passa a **`reducao_cbs_transicao`**, com `Fundamento_Legal` "LC 214, art. 347; Decreto 12.955/2026, art. 585".
- **Fórmula.** A lei diz que a redução é proporcional à redução da operação. Com a alíquota padrão P, a redução do cClassTrib r e a da transição t, a alíquota efetiva é **(P menos t) vezes (1 menos r)**; nas operações de alíquota reduzida isso reduz t na mesma proporção (0,1 ponto vira 0,04 quando r = 60%). A ordem de aplicação é indiferente. **Leitura minha**; confirma-se com o contador (Q157-C11).
- **Retrato na apuração.** Em `Mov_Apuracao_Tributo_Item`: **`Reducao_Transicao_Pontos`** (número, opcional; o ponto percentual de fato abatido, na linha da CBS) e **`ID_Calendario_Reducao`** (referência, opcional). Vazios quando não se aplica; sem padrão escondido.
- **Condição do Motor como coluna.** `Cad_Cclasstrib.Aplica_Reducao_Transicao_Cbs` (booleano, preenchido na carga) diz se a classificação recebe a redução; a exceção dos combustíveis do regime específico (LC, arts. 172 a 180; Decreto, arts. 259 a 268) fica nessa coluna **por ora**, e passa ao catálogo do regime quando o B-combustíveis for desenhado. Quais operações são "combustíveis do regime específico" vai ao contador (Q157-C11).
- **IBS de 2027 e 2028.** Conferir na consolidação a carga de `Cad_Aliquota`: estado 0,05 e município 0,05, `Eh_Aliquota_Referencia` verdadeiro, vigência 01/01/2027 a 31/12/2028; em 2026, só a linha estadual (0,1).
- **Proveniência da alíquota.** `Cad_Aliquota` não tem `Fundamento_Legal` nem `Situacao_Dado`. Como a alíquota da CBS pode vigorar provisoriamente pelo cálculo do TCU e depois mudar (LC, art. 349, § 2º), entram **`Fundamento_Legal`** (texto, opcional) e **`Situacao_Dado`** (enumeração {provisorio, validado}, opcional), como já têm os parâmetros do calendário.
- **Dedução do IBS dos combustíveis na CBS** (LC, art. 347, § 2º): decide-se no desenho do regime de combustíveis.

# 8. Documento fiscal e cadastro (B0a-5)

## 8.1 Entrega do arquivo do documento ao adquirente

O Decreto não usa a palavra "XML": fala em "arquivo digital do documento fiscal". O art. 134, I, manda o emitente encaminhar ou disponibilizar o arquivo ao adquirente e ao destinatário **imediatamente** depois do protocolo de autorização de uso; o inciso II manda entregá-lo ao transportador contratado pelo adquirente do serviço **antes** do início da operação. Não vale para a DeRE (§ 1º); nos documentos cuja autorização é o protocolo de resposta (NF-e, CT-e e outros) entrega-se também o protocolo (§ 2º); na NFS-e Via entrega-se ainda o Registro de Passagem Veicular ao usuário do pedágio (§ 3º). **Não há prazo em horas ou dias.** A falta de entrega tem multa de 20 UPF por período de apuração sem intimação e 30 com intimação (LC, art. 341-G, IV; Decreto, art. 577, IV), afastada em mera falha ou erro material (§ 4º). O adquirente deve exigir o documento (Decreto, art. 112, § 1º) e confirmar a operação ou informar desconhecimento, desfazimento ou devolução (LC, art. 341-G, IX); isso já é evento fiscal (`Mov_Dfe_Evento`).

**O dicionário hoje:** guarda o arquivo (`Mov_Documento_Fiscal.ID_Documento_Xml_Autorizado`, no GED), o protocolo, quem pode baixar (`Mov_Nota_Fiscal_Saida_Autorizado_Xml`, que é autXML e **não** é entrega) e os e-mails do participante. **Nada registra** que o arquivo foi enviado, quando, a quem e com quê.

### Entidade nova: `Mov_Documento_Fiscal_Entrega_Xml`

Uma linha por destinatário da entrega. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Documento_Fiscal_Entrega_Xml` | identificador | |
| `ID_Documento_Fiscal` | referência (`Mov_Documento_Fiscal`) | |
| `Papel_Destinatario` | enumeração {adquirente, destinatario, transportador, usuario_pedagio} | |
| `ID_Participante` | referência (`Cad_Participante`), opcional | Vazio no consumidor não identificado. |
| `Forma_Entrega` | enumeração {email, portal_ou_consulta, api_edi, outra} | A lei aceita "disponibilizado": na consulta (portal ou QR), a data de disponibilização basta. |
| `Endereco_Destino` | texto, opcional | O e-mail ou a URL usados. |
| `Data_Hora_Envio` | data/hora, opcional | |
| `Data_Hora_Disponibilizacao` | data/hora, opcional | Quando a forma é por consulta. |
| `Situacao` | enumeração {pendente, enviada, disponibilizada, falha, nao_aplicavel} | |
| `Motivo_Nao_Aplicavel` | texto, opcional | Obrigatório em `nao_aplicavel` (a DeRE, por exemplo). |
| `Incluiu_Protocolo`, `Incluiu_Rpv` | booleanos | Art. 134, §§ 2º e 3º. |
| `Tentativa` | número | |
| `Mensagem_Erro` | texto, opcional | |
| `ID_Documento_Xml` | referência (`Cad_Documento`) | O arquivo entregue (GED). |

O prazo **não** é gravado: deriva-se (autorização mais o parâmetro abaixo).

### Quatro colunas por modelo em `Cad_Modelo_Documento_Fiscal`

O catálogo já tem vigência. Entram quatro booleanos, preenchidos na carga (sem padrão escondido): **`Exige_Entrega_Ao_Adquirente`** (falso na DeRE, art. 134, § 1º), **`Exige_Protocolo_Na_Entrega`** (§ 2º), **`Exige_Rpv_Na_Entrega`** (§ 3º) e **`Exige_Entrega_Ao_Transportador`** (art. 134, II, nos modelos de bens móveis).

### Prazo de alerta

Uma linha em `Cad_Dfe_Parametro_Regra` com `Codigo_Regra` = `DFE-ENTREGA-ARQUIVO-PRAZO`, `Unidade` = minutos e `Valor_Numerico` **vazio na carga**, até você ou o contador escolherem o valor (a lei só diz "imediatamente"). Enquanto vazio, o ERP não avisa atraso e diz que o parâmetro não foi definido (Q157-C12). Aviso, nunca bloqueio.

## 8.2 Cadastro da filial: o "evento cadastral"

O texto legal **não** usa "evento cadastral". O Decreto usa "ato cadastral" (art. 105, § 5º; art. 109, § 5º, II). Os eventos fiscais dos arts. 140 a 145 são de documento, outra coisa. **Leio "evento cadastral da filial" como os atos do Decreto, art. 108** (Q157-11).

**O que o Decreto pede.** O cadastro único é o CPF, o CNPJ e o CIB (art. 104; LC, art. 59, § 1º). Quem é sujeito à CBS e ao IBS se inscreve no CNPJ **antes de iniciar a atividade, por estabelecimento** (art. 105, caput); o estabelecimento é qualquer local físico ou virtual onde há atividade ou armazenagem (art. 106). O art. 108, I, manda atualizar o **domicílio principal** até o último dia útil do mês seguinte à alteração; o art. 108, II, manda comunicar a **venda ou transferência** do estabelecimento e o **encerramento ou paralisação temporária** no mesmo prazo. O art. 107 define o domicílio principal do adquirente: na pessoa jurídica, o local de cada estabelecimento atendido; na pessoa física, a habitação permanente ou, se não houver ou houver mais de uma, o local das relações econômicas mais relevantes. A multa é de 10 UPF por infração (LC, art. 341-G, I a III; Decreto, art. 577, I a III). CNPJ inapto, suspenso, nulo ou baixado impede a emissão (arts. 121 e 122, já em `Cad_Dfe_Parametro_Regra`, D-N272).

**O dicionário hoje:** `Cad_Filial` (o fim da vigência fecha a filial), `Cad_Participante_Endereco`, `Cad_Participante_Situacao_Cnpj`, `Cad_Participante_Inscricao`, `Cad_Regra_Vencimento` e `Mov_Consulta_Cadastro_Externo`. **Faltam** o registro do ato, o prazo e o comprovante da comunicação; a paralisação temporária não cabe na vigência da filial.

### Entidade nova: `Mov_Filial_Evento_Cadastral`

Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Filial_Evento_Cadastral` | identificador | |
| `ID_Filial` | referência (`Cad_Filial`) | |
| `Tipo_Evento` | enumeração {inscricao_cnpj, alteracao_domicilio_principal, venda_estabelecimento, transferencia_estabelecimento, encerramento, paralisacao_temporaria, reativacao} | |
| `Data_Evento` | data | A do fato. |
| `Data_Comunicacao` | data, opcional | Quando foi comunicado. |
| `Meio_Comunicacao` | texto, opcional | |
| `Numero_Protocolo` | texto, opcional | |
| `ID_Documento_Comprovante` | referência (`Cad_Documento`), opcional | |
| `ID_Participante_Sucessor` | referência (`Cad_Participante`), opcional | O adquirente ou o novo titular, na venda ou transferência. |
| `Data_Retomada` | data, opcional | Só na paralisação; vazia significa que continua paralisada. |
| `Situacao_Comunicacao` | enumeração {a_comunicar, comunicado, dispensado_por_ato} | |
| `ID_Usuario_Registro` | referência (`Cad_Usuario`) | |

O prazo se **deriva**: `comunicacao_cadastral` entra como valor novo de `Cad_Regra_Vencimento.Finalidade`, com `Referencia_Fim` = fim do mês, `Meses_Deslocamento` = 1 e `Tipo_Dia` = último dia útil, `Fundamento_Legal` "Decreto, art. 108, I e II" (carga provisória). O aviso de atraso sai da comparação com `Data_Comunicacao`. O `encerramento` fecha a vigência de `Cad_Filial` (o mecanismo já existe); a `paralisacao_temporaria` não fecha. Documento emitido por filial paralisada ou com comunicação em atraso gera **aviso**, nunca bloqueio.

### Domicílio principal em `Cad_Participante_Endereco`

Entra a coluna **`Eh_Domicilio_Principal`** (booleano), e não um novo `Tipo_Endereco`: a pessoa jurídica usa o endereço fiscal de cada estabelecimento (derivável), mas a pessoa física com mais de uma habitação precisa de escolha registrada (art. 107, II). Preenchida sem valor padrão escondido.

## 8.3 A LC 227 no cadastro e no documento fiscal

A LC 227 deu nova redação ao art. 59, § 5º (o Domicílio Tributário Eletrônico passa a ser **unificado** no IBS e obrigatório a toda pessoa jurídica sujeita à inscrição no CNPJ), acrescentou o art. 60, § 7º (o ato conjunto deve permitir **documentos fiscais consolidados**; o Decreto, art. 150, II, diz o mesmo) e os §§ 4º e 5º do art. 58 (gratuidade dos mecanismos mínimos de integração; transações extras podem ser cobradas). O dicionário só tem a caixa postal e-CAC/DTE como origem de comunicação (`Origem_Caixa`); nada a acrescentar agora.

# 9. Início da obrigação da pessoa física e do produtor rural (Q137-6 e D-N393)

## 9.1 O que o texto pede

O Decreto 13.075 (21/07/2026) acrescentou ao Decreto 12.955 dois dispositivos que **não têm equivalente na LC**: o **art. 115, § 3º** (a obrigatoriedade de emitir documento fiscal produz efeitos desde **01/01/2027** para (I) a pessoa física contribuinte ou responsável tributário e (II) o produtor rural pessoa física do art. 239, caput, I e II) e o **art. 105, § 4º-A** (a inscrição no CNPJ da pessoa física, com os mesmos dois grupos e a mesma data). A inscrição da pessoa física vale só para a legislação da CBS e do IBS (art. 105, § 4º): o ERP não a usa em eSocial, Reinf, ECF ou outros tributos.

**O art. 239** (equivale aos arts. 164 a 167 da LC, sem alteração pela LC 227). Não é contribuinte o produtor rural, pessoa física ou jurídica, com receita no ano-calendário **menor que R$ 3.600.000,00** (inciso I) e o produtor rural **integrado** (inciso II). Portanto o inciso II do § 3º alcança a pessoa física **não contribuinte** (abaixo do limite) e a integrada; a pessoa física produtora **acima** do limite é contribuinte e entra no inciso I. O § 3º só trata da pessoa física: para o produtor rural pessoa jurídica, o nanoempreendedor, o transportador autônomo, o condomínio e os demais, a data vem de **ato conjunto** da RFB e do CGIBS (art. 112, caput), que o Decreto não dá. O art. 244 manda o produtor rural e o integrado não contribuintes emitir documento fiscal na saída e se inscrever no cadastro "com indicativo de não contribuinte". A receita do inciso I conta só as vendas da atividade do art. 238, I, exclui o contrato de integração, os bens da produção e a terra nua; o limite é atualizado pelo IPCA em janeiro a partir de 2027 (§ 3º), proporcional aos meses no início da atividade (§ 4º), soma a receita das pessoas jurídicas em que tenha participação (§ 6º); ultrapassado o limite, a pessoa vira contribuinte no segundo mês seguinte, ou em 1º de janeiro se o excesso for de até 20% (§ 8º). O art. 243 trata de quem teve receita de R$ 3,6 milhões ou mais em 2024.

**O dicionário hoje:** nada guarda a data. `Cad_Locacao_Obrigacao_Emissao` é só do aluguel. `Cad_Participante_Qualificacao_Cbs` tem `Indicador_Contribuinte_Cbs`, `Motivo_Condicao` (por limite de receita) e o tipo `produtor_rural`; `Cad_Participante_Inscricao.Tipo_Inscricao` já tem `cnpj_pessoa_fisica` (Q116-5). O limite de R$ 3,6 milhões, a tolerância de 20%, os meses de efeito e a atualização pelo IPCA **não estão em parâmetro algum**.

## 9.2 Desenho

**Quatro linhas em `Cad_Calendario_Transicao`** (`Tipo_Valor` = data, Ano vazio, 01/01/2027, `Situacao_Dado = provisorio`; valores novos em `parametro_transicao`): `inicio_emissao_documento_fiscal_pf_contribuinte` (Decreto, art. 115, § 3º, I), `inicio_emissao_documento_fiscal_produtor_rural_pf` (§ 3º, II), `inicio_cnpj_pessoa_fisica_contribuinte` (art. 105, § 4º-A, I) e `inicio_cnpj_produtor_rural_pf` (§ 4º-A, II). São quatro, e não duas, porque emissão e inscrição são dispositivos diferentes que hoje têm o mesmo dia e podem divergir amanhã.

**Entidade nova: `Cad_Qualificacao_Cbs_Inicio_Obrigacao`.** O Motor precisa saber qual linha vale para quem; a escolha é coluna, não regra escondida no código. Catálogo com vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Qualificacao_Cbs_Inicio_Obrigacao` | identificador | |
| `Tipo_Pessoa` | enumeração {pessoa_fisica, pessoa_juridica} --- identidade | |
| `ID_Tipo_Qualificacao` | referência (`Cad_Classe_Sistema`, domínio = `qualificacao_cbs`), opcional --- identidade | |
| `Indicador_Contribuinte_Cbs` | enumeração (a de `Cad_Participante_Qualificacao_Cbs`), opcional --- identidade | |
| `ID_Calendario_Inicio_Emissao` | referência (`Cad_Calendario_Transicao`), opcional | A data da emissão. Vazia quando depende de ato conjunto (aviso). |
| `ID_Calendario_Inicio_Cnpj` | referência (`Cad_Calendario_Transicao`), opcional | A data da inscrição (D-N393). |
| `Fundamento_Legal` | texto | |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

Vale a linha mais específica. Para o produtor rural pessoa jurídica, o nanoempreendedor, o transportador autônomo e o condomínio a linha não tem data (depende de ato conjunto), e o ERP avisa.

**Entidade nova: `Cad_Produtor_Rural_Parametro_Cbs`.** Parâmetro com vigência do art. 239.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Produtor_Rural_Parametro` | identificador | |
| `Valor_Limite_Receita` | número | 3.600.000,00 (art. 239, I). |
| `Percentual_Tolerancia_Excesso` | número | 20 (§ 8º). |
| `Meses_Efeito_Excesso` | número | 2: vira contribuinte no segundo mês subsequente. |
| `ID_Serie_Cotacao_Atualizacao` | referência (`Cad_Serie_Cotacao`), opcional | O IPCA, como já faz `Cad_Locacao_Obrigacao_Emissao`. O limite de 2027 ainda não foi divulgado (Q157-C14). |
| `Fundamento_Legal` | texto | |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

A receita apurada do ano e a qualificação resultante já cabem em `Cad_Participante_Qualificacao_Cbs` com `Origem` = `calculado_pelo_sistema`. A Q137-6 ("sim", parâmetro com vigência separado da locação, provisório) fica atendida.


# 10. O que entra no próximo "consolidar"

**13 entidades novas**, todas na Contabilidade & Fiscal.

| Entidade | Tipo | Vigência | Capítulo |
|---|---|---|---|
| `Cad_Regra_Fato_Gerador` | catálogo (12 linhas) | sim | 3 |
| `Mov_Cbs_Ajuste_Operacao` | cabeçalho do ajuste | não | 4 |
| `Mov_Cbs_Ajuste_Operacao_Efeito` | efeito por lado (serve também ao uso pessoal) | não | 4 |
| `Cad_Cbs_Ajuste_Efeito_Regra` | matriz de efeitos (21 linhas) | sim | 4 |
| `Cad_Acrescimo_Legal_Cbs` | parâmetro (1 linha) | sim | 5 |
| `Cad_Acrescimo_Legal_Hipotese` | catálogo (28 linhas) | sim | 5 |
| `Cad_Valor_Mercado_Locacao_Parametro` | parâmetro (carga vazia) | sim | 6 |
| `Mov_Imovel_Valor_Referencia` | valor de referência do Sinter | não | 6 |
| `Mov_Cbs_Transicao_2026_Periodo` | transição de 2026 por empresa e mês | não | 7 |
| `Mov_Documento_Fiscal_Entrega_Xml` | entrega do arquivo ao adquirente | não | 8 |
| `Mov_Filial_Evento_Cadastral` | atos do art. 108 | não | 8 |
| `Cad_Qualificacao_Cbs_Inicio_Obrigacao` | catálogo (3 linhas) | sim | 9 |
| `Cad_Produtor_Rural_Parametro_Cbs` | parâmetro (1 linha) | sim | 9 |

**24 entidades alteradas** (18 com **40 campos novos** e 1 campo que sai; 6 só com valores, cargas ou texto).

| Entidade | O que muda |
|---|---|
| `Mov_Nota_Fiscal_Saida_Item` | `Data_Fato_Gerador`, `Criterio_Data_Fato_Gerador`, `ID_Regra_Fato_Gerador` |
| `Mov_Nota_Fiscal_Entrada_Item` | os mesmos três campos |
| `Mov_Apuracao_Tributo_Item` | `Competencia_Debito`, `Reducao_Transicao_Pontos`, `ID_Calendario_Reducao` |
| `Cad_Adiantamento_Regra_Tributacao` | `Criterio_Data_Aliquota`, `Prazo_Maximo_Dias_Ate_Fornecimento`, `Periodo_Debito_Antecipacao`; `Origem_Valor` e fundamento das linhas de CBS e IBS |
| `Mov_Credito_Aplicacao_Tributo` | `Adquirente_Tomou_Credito`, `ID_Perdcomp`; texto do excesso |
| `Mov_Gestao_Contrato_Apuracao` | `Data_Exigibilidade` |
| `Cad_Regime_Geral_Imobiliario` | `Momento_Fato_Gerador_Nao_Oneroso` |
| `Mov_Cbs_Apuracao_Espelho` | só o texto de `Periodo` |
| `Mov_Credito_Fiscal` | `ID_Cbs_Ajuste_Operacao_Efeito`; `Origem` + 2 valores, `Status` + 1, `Modalidade_Extincao_Debito` + 2 |
| `Mov_Devolucao_Compra` | `ID_Cbs_Ajuste_Operacao` |
| `Mov_Devolucao_Venda` | `ID_Cbs_Ajuste_Operacao` |
| `Mov_Estoque_Abertura_Cbs_Estorno` | `Valor_Multa_Mora`, `Valor_Juros_Mora`, `ID_Acrescimo_Legal`, `ID_Cbs_Ajuste_Operacao_Efeito`; **sai** `Valor_Acrescimos` |
| `Mov_Credito_Ajuste_Documento` | só o texto (o cancelamento do adiantamento segue o art. 57) |
| `Mov_Locacao_Faturamento` | `Valor_Foro_Taxa_Ocupacao`, `Comprovacao_Pagamento_Despesas`, `Valor_Contraprestacao_Nao_Monetaria`, `ID_Apuracao_Valor_Mercado` |
| `Mov_Locacao_Limite_Pf` | `Receita_Locacao_Valor_Mercado_Relacionada` |
| `Mov_Auto_Infracao` | `Regime_Suprimento_2026`, `Data_Intimacao_Suprimento`, `Data_Atendimento_Suprimento`, `Penalidade_Extinta` |
| `Cad_Calendario_Transicao` | `Tipo_Valor` + `numero`; 6 linhas novas; código `reducao_cbs_art_585` renomeado `reducao_cbs_transicao` |
| `Cad_Cclasstrib` | `Aplica_Reducao_Transicao_Cbs` |
| `Cad_Aliquota` | `Fundamento_Legal`, `Situacao_Dado` |
| `Mov_Cbs_Pedido_Ressarcimento` | só o texto (período de 2026 não aceita saldo da apuração informativa) |
| `Cad_Modelo_Documento_Fiscal` | `Exige_Entrega_Ao_Adquirente`, `Exige_Protocolo_Na_Entrega`, `Exige_Rpv_Na_Entrega`, `Exige_Entrega_Ao_Transportador` |
| `Cad_Dfe_Parametro_Regra` | uma linha de carga (`DFE-ENTREGA-ARQUIVO-PRAZO`, valor vazio) |
| `Cad_Regra_Vencimento` | `Finalidade` + `comunicacao_cadastral`; uma linha de carga |
| `Cad_Participante_Endereco` | `Eh_Domicilio_Principal` |

**Alterações ao documento 156 (ainda não aplicado):** duas linhas novas na carga de `Cad_Regra_Valor_Mercado` (de 8 para 10 linhas) e duas colunas em `Mov_Valor_Mercado_Apuracao` (`ID_Valor_Mercado_Locacao_Parametro` e `ID_Imovel_Valor_Referencia`). A consolidação aplica os dois documentos juntos.

**Domínios novos** em `Cad_Classe_Sistema`: `hipotese_fato_gerador` (12 valores), `tipo_ajuste_operacao_cbs` (4) e `hipotese_acrescimo_cbs` (28). **Valores novos** em domínios existentes: `parametro_transicao` (6 códigos novos e 1 renomeado), `Finalidade` de `Cad_Regra_Vencimento` (1).

**Cargas provisórias:** 12 linhas do fato gerador (Anexo A), 21 da matriz de efeitos (Anexo B), 1 do acréscimo do art. 27 e 28 das hipóteses (Anexo C), 3 do início da obrigação da pessoa física e do produtor rural, 1 do limite do produtor rural, 6 do calendário, 1 do prazo de entrega (valor vazio) e 1 do vencimento cadastral. O valor de mercado da locação entra **vazio**. A contagem de comandos do T-SQL e dos scripts de carga é refeita na consolidação.

**Correções de texto que a consolidação faz:** (1) o texto de `Mov_Credito_Aplicacao_Tributo` sobre o excesso da antecipação ("crédito do contribuinte, derivado") passa a citar a LC, art. 10, § 4º, II, c e o Decreto, art. 38 (documento 153); (2) o texto de `Mov_Credito_Ajuste_Documento` passa a citar o Decreto, art. 11, § 6º e o art. 57; (3) os documentos 10, 94 e 115 passam a dizer que a redução de 0,1 ponto é do **art. 347 da LC** (e do art. 585 do **Decreto**), e que os acréscimos do art. 27 têm **22 artigos**, e não "mais de dez"; (4) a descrição de `Mov_Cbs_Apuracao_Espelho.Periodo` registra a diferença entre o espelho da Plataforma e a competência do ERP.

# 11. Perguntas

## 11.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q157-1** | Catálogo `Cad_Regra_Fato_Gerador` (12 linhas), data do fato gerador no item da nota (entrada e saída) e `Competencia_Debito` na apuração; o nome `Mov_Fornecimento_Antecipacao` da fila não se cria? | Sim |
| **Q157-2** | Antecipação: `Criterio_Data_Aliquota` (a menor entre a emissão do documento e o pagamento), reserva sem carga da regra dos 5 dias, e o excesso deixa de ser crédito (`Adquirente_Tomou_Credito` e `ID_Perdcomp`)? | Sim |
| **Q157-3** | `Data_Exigibilidade` no contrato periódico e `Criterio_Exigibilidade` no catálogo, com `a_definir` até o contador responder? | Sim |
| **Q157-4** | Ajuste da operação em três entidades (`Mov_Cbs_Ajuste_Operacao`, `_Efeito` e a matriz de 21 linhas) e as mudanças em `Mov_Credito_Fiscal`, nas devoluções e no estorno do estoque de abertura; a linha de efeito serve também ao uso pessoal do documento 156? | Sim |
| **Q157-5** | Acrescentar `compensacao` e `responsavel` às modalidades de extinção do débito (`rad` e `pcont` ficam como estão)? | Sim |
| **Q157-6** | Acréscimos do art. 27 em `Cad_Acrescimo_Legal_Cbs` e `Cad_Acrescimo_Legal_Hipotese` (28 linhas), a Selic como série, e o par multa e juros no lugar de `Valor_Acrescimos`? | Sim |
| **Q157-7** | Locação de imóvel: parâmetro `Cad_Valor_Mercado_Locacao_Parametro` (carga vazia, com direitos reais pela coluna `Tipo_Operacao`), `Mov_Imovel_Valor_Referencia`, os dois métodos novos no valor de mercado e as colunas na locação? | Sim |
| **Q157-8** | Transição de 2026: `Mov_Cbs_Transicao_2026_Periodo` (só decisão e fato), suprimento de omissão no auto e `numero` no `Tipo_Valor` do calendário com os dois prazos de 60 dias? | Sim |
| **Q157-9** | Redução de 0,1 ponto: sem linha de CBS já líquida; código `reducao_cbs_transicao`; a redução aplicada gravada na apuração; `Aplica_Reducao_Transicao_Cbs` em `Cad_Cclasstrib`; proveniência em `Cad_Aliquota`? | Sim |
| **Q157-10** | Entrega do arquivo ao adquirente: `Mov_Documento_Fiscal_Entrega_Xml`, quatro colunas por modelo e prazo de alerta com valor vazio até você ou o contador definirem? | Sim |
| **Q157-11** | Leio "evento cadastral da filial" como os atos do Decreto, art. 108: `Mov_Filial_Evento_Cadastral`, `comunicacao_cadastral` no vencimento e `Eh_Domicilio_Principal` no endereço? | Sim |
| **Q157-12** | Q137-6 e D-N393: quatro linhas de calendário de 01/01/2027, `Cad_Qualificacao_Cbs_Inicio_Obrigacao` (3 linhas) e `Cad_Produtor_Rural_Parametro_Cbs`? | Sim |
| **Q157-13** | As multas da LC 227 (UPF de R$ 200, arts. 341-A a 341-H) ficam só como aviso de exposição por ora, e a entidade de penalidades vai a um documento próprio depois? | Sim |
| **Q157-14** | Aplico tudo no próximo "consolidar", junto com os documentos 156, 164 e 168? | Sim |

## 11.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q157-C1** | Desconto posterior ou abatimento depois do fornecimento, sem erro e sem devolução: reduz a CBS? Por qual documento? (O Decreto, art. 13, § 3º, só exclui da base o desconto que consta do documento e não depende de evento posterior; os arts. 59 e 61 falam só em erro.) | Sem tipo de ajuste para desconto posterior |
| **Q157-C2** | A cadeia da competência do adiantamento (data prevista, depois **data de saída**, depois emissão) vem da cartilha do CG-IBS; o Decreto, art. 11, §§ 8º e 9º, só diz previsão e emissão. O passo da saída vale? E a base do recebimento (Q153-C1): o art. 13, § 2º, I, exclui da base o montante de IBS e CBS, o que apoia dividir por (1 mais as alíquotas) se o valor pago for o cheio. Confere? | Cadeia como está; base `resposta_do_gestor` |
| **Q157-C3** | Excesso da antecipação (LC, art. 10, § 4º, II, c; Decreto, art. 38): a restituição só vale se a operação não gerou crédito ao adquirente. A antecipação de cliente contribuinte normalmente gera crédito; então o excesso de cliente do regime regular fica sem restituição? Em que prazo? | Aviso, sem decisão |
| **Q157-C4** | Execução continuada (Decreto, art. 11, § 3º, I e § 4º): para a Mlegate, "exigível" é a emissão da fatura, a medição aceita ou o vencimento contratual? | `a_definir` |
| **Q157-C5** | Erro de documento (arts. 59 e 61): o fornecedor, quando o débito foi extinto por split, **apropria crédito** em vez de receber transferência em dinheiro (que o art. 57, § 2º, II, b, 1 prevê na devolução). É isso? Os efeitos do adquirente são os mesmos da devolução? E a nota de crédito de multa e juros (código 55 da Plataforma): em que caso sai? | Matriz como no Anexo B |
| **Q157-C6** | Art. 57, § 7º: qual evento do destinatário conta como "atestar a existência da operação" (confirmação, ciência)? | Só aviso |
| **Q157-C7** | Acréscimos do art. 27: (a) a vigência inicial da linha é 29/04/2026 (Decreto), 13/01/2026 (LC 227) ou 01/01/2027? Valem em 2026? (b) o termo inicial nos artigos que não o dizem (arts. 161, § 17; 186, § 3º; 529, § 6º; 537, § 6º; 96, § 5º) é o fato gerador? (c) a LC, arts. 93, § 7º e 101, diz "multa de mora e Selic" e o Decreto remete ao § 2º inteiro: vale o Decreto? O art. 160, § 2º (só Selic, "sem prejuízo dos demais") tem multa de mora também? (d) qual série da Selic e qual arredondamento; o ERP calcula ou só confere o DARF? (e) o que valem as faixas "acréscimos legais" sem remissão? | Vigência 01/01/2027; faixas genéricas sem multa nem juros presumidos |
| **Q157-C8** | (a) Débito gerado ao adquirente quando o crédito já foi utilizado (art. 57, § 2º, I, c): incidem os acréscimos do art. 44, § 2º? Desde quando? (b) Os três ramos do estorno do adquirente valem também para o uso pessoal (art. 64) e o perecimento (art. 48), que só mandam estornar? | (a) Sem acréscimo; (b) sim, provisório |
| **Q157-C9** | Locação abaixo do mercado: (a) o percentual sobre o valor de referência é mensal ou anual? O art. 364, § 10, manda usar o valor do art. 375, § 2º (estimativa do valor do imóvel): como vira aluguel? (b) Locação entre partes relacionadas nos limites da pessoa física (art. 382, § 8º): entra o valor de mercado apurado pelo ERP ou o informado? Quem comprova "características e localização semelhantes"? (c) Que prova basta para "prova inequívoca do pagamento" (art. 364, § 4º)? | `a_definir`; registro manual com aviso |
| **Q157-C10** | Transição de 2026: (a) quem é "desobrigado" das obrigações acessórias (Decreto, art. 464, II: Simples, MEI, ato conjunto)? A dispensa vale também para o IBS? (b) O art. 583, II, b (ressarcir em 60 dias o que foi recolhido) e o art. 465 (saldo da apuração informativa não ressarcível) são coisas diferentes? | Como lido |
| **Q157-C11** | Redução de 0,1 ponto: (a) a leitura (P menos 0,1) vezes (1 menos r) está certa? Em regime específico com alíquota própria ou específica por unidade, a redução é ponto sobre a alíquota ou sobre a base? (b) Quais operações são "combustíveis do regime específico" (LC, arts. 172 a 180) e ficam fora? A marca vale por cClassTrib, por produto ANP ou por regime da empresa? (c) A CBS de 2027 já foi fixada (resolução do Senado até 31/10/2026) ou vale a do TCU? Qual o valor? | (a) Leitura minha; (b) por cClassTrib; (c) sem linha |
| **Q157-C12** | Entrega do arquivo (Decreto, art. 134, I): qual prazo vale para "imediatamente"? Em contingência, sem protocolo, a entrega ocorre depois da transmissão posterior? No consumidor sem identificação, a disponibilização por QR ou consulta cumpre? A multa de 20 UPF é por período de apuração (e não por documento), o que muda o aviso do ERP? | Sem prazo; aviso por mês |
| **Q157-C13** | Cadastro: (a) o prazo do art. 108 ("último dia útil do mês seguinte") usa o calendário do município da matriz? (b) Na venda ou transferência do estabelecimento, quem comunica? O encerramento da filial com o CNPJ raiz mantido é evento do art. 108, II ou só baixa? (c) Para a pessoa física que passa a emitir em 2027, a chave de acesso usa o CNPJ ou o CPF (art. 124, § 1º, I, aceita os dois)? | Calendário da matriz; ambos os campos |
| **Q157-C14** | Pessoa física e produtor rural: (a) quem é "pessoa física responsável tributário" (arts. 115, § 3º, I e 105, § 4º-A, I)? Qual o prazo de inscrição de quem já atua em 01/01/2027? (b) Qual a data de início do produtor rural pessoa jurídica, do nanoempreendedor, do transportador autônomo e do condomínio? (c) O art. 243 fixa a receita de **2024** para "contribuinte desde 01/01/2026"; a LC, art. 165, § 3º, fala em "ano anterior ao da entrada em vigor". Confere? (d) O limite do art. 239, § 3º, de 2027 já foi divulgado? | Sem data para os do ato conjunto |

## 11.3 Para a equipe

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q157-E1** | Na NFS-e nacional, o campo de competência da DPS basta como data do fato gerador, ou a DPS precisa dos três campos do item da nota? | Só nas notas de produto |
| **Q157-E2** | O leiaute da nota de saída (NF-e e NFS-e) tem o grupo do pagamento antecipado (NT 2025.002; documento 34)? | Sem campo até a conferência |
| **Q157-E3** | Existe ligação entre `Mov_Credito` (tipo pagar) e `Mov_Credito_Fiscal` para o crédito do adquirente na extinção do débito da antecipação (LC, art. 10, § 6º)? Se não, propor `ID_Credito_Origem` em `Mov_Credito_Fiscal`. | Sem campo até a conferência |
| **Q157-E4** | Qual é a fonte da série da Selic (acumulada no mês) para `Cad_Serie_Cotacao`? | Série vazia |

# 12. Limites

- **Foram lidos** nos textos legais os arts. 10 e 11 da LC e 11, 12, 13, 18, 26, 27, 38, 43 a 46, 57, 59, 61, 104 a 108, 112 a 118, 134, 239, 244, 363, 364, 375, 382, 464, 465, 572 a 579, 582 a 585 do Decreto, mais os artigos que eles citam. **Não foram lidos** os regimes que remetem ao art. 27 (B1, B3 e B5): só a remissão, e as hipóteses do Anexo C vão ao documento de cada bloco para o detalhe.
- **Foi conferida** a LC 227 contra o DOU nos arts. 346 e 347 (não alterados), e a numeração do Decreto contra a da LC. **Não foram conferidas** três remissões da coluna "LC" do Anexo C (arts. 96, § 5º; 161, § 9º e 375, § 12 do Decreto): ficam "a conferir".
- **Os documentos 70, 72, 137 e 153 não estão no Project** (o Project está no limite de tamanho). Usei os documentos 10, 14, 38, 94, 115 e 116 e o dicionário da revisão 29. O documento 153 foi lido por meio do que o dicionário e o documento 14 dizem dele.
- **A leitura do dicionário truncou** algumas descrições longas; por isso as colunas novas que tocam descrições existentes (`Mov_Credito_Aplicacao_Tributo`, `Mov_Credito_Fiscal`) devem ser relidas na consolidação.
- **Os valores legais da carga** (0,33%, 20%, 1%, 60 dias, R$ 3,6 milhões, 20%) saíram do texto; o contador valida a carga inteira. O limite do produtor rural para 2027 e a CBS de 2027 **não estão** no que li.
- **O art. 6º, as multas da LC 227 (arts. 341-A a 341-H), o B1, o B2, o B3 e o B5** não estão neste documento.
- **Nenhum campo deste documento foi visto por você.** Os nomes, as listas e as leituras são meus até você responder.


# Anexo A. Carga provisória de `Cad_Regra_Fato_Gerador` (12 linhas)

Todas com `Aplica_Ibs` e `Aplica_Cbs` verdadeiros, `Situacao_Dado = provisorio` e vigência a partir de 01/01/2026 (a LC 227 vale desde 13/01/2026, e a regra do art. 10 já existia). A importação de serviço não tem linha própria (capítulo 3). O imóvel fica em `Cad_Regime_Geral_Imobiliario`.

| Nº | Hipótese | Momento | `Fonte_Data` | `Fonte_Data_Subsidiaria` | `Origem_Regra` | Fundamento |
|---|---|---|---|---|---|---|
| 1 | `bem_material` | `entrega_disponibilizacao` | `data_previsao_entrega` | `data_emissao_documento` | `lc_e_decreto` | LC, art. 10, caput; Decreto, art. 11, § 1º, I e §§ 8º e 9º |
| 2 | `bem_imaterial_direito` | `ato_de_cessao` | `data_ato` |  | `decreto` | Decreto, art. 11, § 1º, II (a LC não traz) |
| 3 | `transporte_inicio_pais` | `inicio_transporte` | `data_inicio_transporte` |  | `lc_e_decreto` | LC, art. 10, § 1º, I; Decreto, art. 11, § 1º, III |
| 4 | `transporte_carga_inicio_exterior` | `termino_transporte` | `data_termino_transporte` |  | `lc_e_decreto` | LC, art. 10, § 1º, II; Decreto, art. 11, § 1º, IV |
| 5 | `servico_demais` | `termino_servico` | `data_termino_servico` |  | `lc_e_decreto` | LC, art. 10, § 1º, III; Decreto, art. 11, § 1º, V |
| 6 | `bem_sem_documento_idoneo` | `constatacao` | `data_constatacao` |  | `lc_e_decreto` | LC, art. 10, § 1º, IV; Decreto, art. 11, § 1º, VI. É lançamento de ofício, fora do ERP; a linha existe para o catálogo ficar completo |
| 7 | `aquisicao_leilao_licitacao` | `aquisicao` | `data_aquisicao` |  | `lc_e_decreto` | LC, art. 10, § 1º, V; Decreto, art. 11, § 1º, VII |
| 8 | `compra_ente_publico` | `pagamento` | `data_pagamento` |  | `lc_e_decreto` | LC, art. 10, § 2º; Decreto, art. 11, § 2º e art. 439, § 6º |
| 9 | `execucao_continuada` | `primeira_entre_exigibilidade_e_pagamento` | `data_emissao_fatura` (conforme `Criterio_Exigibilidade`) | `data_pagamento` | `lc_e_decreto` | LC, art. 3º, § 3º e art. 10, § 3º (LC 227); Decreto, art. 11, §§ 3º e 4º. O ERP toma a menor das duas datas; `Criterio_Exigibilidade` = `a_definir` |
| 10 | `importacao_bem_despacho_consumo` | `liberacao_despacho_consumo` | `data_liberacao_aduaneira` |  | `lc_e_decreto` | LC, arts. 65 e 67; Decreto, arts. 75 e 78 |
| 11 | `importacao_bem_admissao_temporaria` | `liberacao_admissao_temporaria` | `data_liberacao_aduaneira` |  | `lc_e_decreto` | LC, arts. 65 e 67; Decreto, arts. 75 e 78 |
| 12 | `importacao_bem_lancamento_credito` | `lancamento_credito_tributario` | `data_ato` (a do lançamento) |  | `lc_e_decreto` | LC, arts. 65 e 67; Decreto, arts. 75 e 78 (bagagem, extravio, sem declaração) |

# Anexo B. Carga provisória de `Cad_Cbs_Ajuste_Efeito_Regra` (21 linhas)

Tipo vazio vale para devolução, cancelamento e correção de erro, e a linha com tipo preenchido vence a de tipo vazio. Todas com `Situacao_Dado = provisorio`. As linhas 16 a 21 (correção de erro) só têm o lado do fornecedor; o adquirente usa as linhas 1 a 3. A Q157-C5 confirma isso com o contador.

| Nº | `ID_Tipo_Ajuste` | Lado | Gerou crédito | `Parcela` | Modalidade | `Efeito` | Ordem | Fundamento | `Origem_Regra` |
|---|---|---|---|---|---|---|---|---|---|
| 1 | vazio | adquirente | sim | `credito_a_apropriar` | qualquer | `estorno_credito_a_apropriar` | 1 | Decreto, art. 57, § 2º, I | `lc_e_decreto` |
| 2 | vazio | adquirente | sim | `credito_apropriado_nao_utilizado` | qualquer | `estorno_credito_apropriado_nao_utilizado` | 2 | Decreto, art. 57, § 2º, I | `lc_e_decreto` |
| 3 | vazio | adquirente | sim | `credito_utilizado` | qualquer | `debito_por_credito_utilizado` | 3 | Decreto, art. 57, § 2º, I | `lc_e_decreto` |
| 4 | vazio | fornecedor | sim | `debito_nao_extinto` | qualquer | `estorno_debito_nao_extinto` | 1 | Decreto, art. 57, § 2º, II | `lc_e_decreto` |
| 5 | vazio | fornecedor | sim | `debito_extinto` | `split_payment` | `transferencia_em_dinheiro` | 2 | Decreto, art. 57, § 2º, II (art. 26, III) | `lc_e_decreto` |
| 6 | vazio | fornecedor | sim | `debito_extinto` | `compensacao` | `restabelecimento_credito` | 2 | Decreto, art. 57, § 2º, II (art. 26, I) | `lc_e_decreto` |
| 7 | vazio | fornecedor | sim | `debito_extinto` | `pcont` | `apropriacao_credito` | 2 | Decreto, art. 57, § 2º, II (art. 26, II) | `lc_e_decreto` |
| 8 | vazio | fornecedor | sim | `debito_extinto` | `responsavel` | `apropriacao_credito` | 2 | Decreto, art. 57, § 2º, II (art. 26, V) | `lc_e_decreto` |
| 9 | vazio | fornecedor | sim | `debito_extinto` | `rad` | `transferencia_em_dinheiro` | 2 | Decreto, art. 57, § 2º, II (art. 26, IV (art. 487)) | `lc_e_decreto` |
| 10 | vazio | fornecedor | não | `debito_nao_extinto` | qualquer | `estorno_debito_nao_extinto` | 1 | Decreto, art. 57, § 3º | `lc_e_decreto` |
| 11 | vazio | fornecedor | não | `debito_extinto` | `split_payment` | `transferencia_em_dinheiro` | 2 | Decreto, art. 57, § 3º (art. 26, III); condição do art. 38, II | `lc_e_decreto` |
| 12 | vazio | fornecedor | não | `debito_extinto` | `compensacao` | `restabelecimento_credito` | 2 | Decreto, art. 57, § 3º (art. 26, I); condição do art. 38, II | `lc_e_decreto` |
| 13 | vazio | fornecedor | não | `debito_extinto` | `pcont` | `apropriacao_credito` | 2 | Decreto, art. 57, § 3º (art. 26, II); condição do art. 38, II | `lc_e_decreto` |
| 14 | vazio | fornecedor | não | `debito_extinto` | `responsavel` | `apropriacao_credito` | 2 | Decreto, art. 57, § 3º (art. 26, V); condição do art. 38, II | `lc_e_decreto` |
| 15 | vazio | fornecedor | não | `debito_extinto` | `rad` | `transferencia_em_dinheiro` | 2 | Decreto, art. 57, § 3º (art. 26, IV (art. 487)); condição do art. 38, II | `lc_e_decreto` |
| 16 | `correcao_erro` | fornecedor | sim | `debito_nao_extinto` | qualquer | `estorno_debito_nao_extinto` | 1 | Decreto, arts. 59 e 61 | `decreto` |
| 17 | `correcao_erro` | fornecedor | sim | `debito_extinto` | `compensacao` | `restabelecimento_credito` | 2 | Decreto, art. 59 (compensação) | `decreto` |
| 18 | `correcao_erro` | fornecedor | sim | `debito_extinto` | `split_payment` | `apropriacao_credito` | 2 | Decreto, art. 59 (demais modalidades, sem transferência em dinheiro) | `decreto` |
| 19 | `correcao_erro` | fornecedor | sim | `debito_extinto` | `rad` | `apropriacao_credito` | 2 | Decreto, art. 59 (demais modalidades, sem transferência em dinheiro) | `decreto` |
| 20 | `correcao_erro` | fornecedor | sim | `debito_extinto` | `pcont` | `apropriacao_credito` | 2 | Decreto, art. 59 (demais modalidades, sem transferência em dinheiro) | `decreto` |
| 21 | `correcao_erro` | fornecedor | sim | `debito_extinto` | `responsavel` | `apropriacao_credito` | 2 | Decreto, art. 59 (demais modalidades, sem transferência em dinheiro) | `decreto` |

# Anexo C. Carga provisória de `Cad_Acrescimo_Legal_Hipotese` (28 linhas)

Dos 32 dispositivos do Decreto que citam acréscimos, ficam fora quatro que não são hipótese de incidência (art. 24, responsabilidade; art. 51, vedação de crédito sobre os acréscimos; art. 53, I, compensação; art. 227, § 2º, responsabilidade solidária); os arts. 572 e 574, parágrafo único, são booleanos de `Cad_Acrescimo_Legal_Cbs`. "A conferir" quer dizer que o artigo da LC não foi verificado. A faixa "multa e juros" (**M+J**) é o art. 27, § 2º. Os booleanos `Aplica_Multa`, `Aplica_Juros` e `Aplica_Limite_Multa` ficam verdadeiros na faixa M+J (o limite só se há multa), `Aplica_Juros` na faixa só Selic, e vazios nas faixas genéricas e no afastamento. Todas com `Situacao_Dado = provisorio`.

| Nº | Código | Decreto, art. | Assunto | Faixa | Termo inicial | LC |
|---|---|---|---|---|---|---|
| 1 | `local_operacao_informado_errado` | 12, § 6º | Local da operação: o adquirente informou errado | `acrescimos_genericos` | `nao_definido_no_texto` | LC, art. 11, § 6º |
| 2 | `plataforma_pagamento_fornecedor` | 20, § 11 | Plataforma digital que emite em 30 dias e paga: multa e juros só do fornecedor | `multa_e_juros_art_27` | `nao_definido_no_texto` | LC, art. 22, § 14 |
| 3 | `responsavel_pagamento` | 37 | Responsável paga "no que couber" o art. 27 | `multa_e_juros_art_27` | `vencimento_do_debito` | LC, art. 37 |
| 4 | `estorno_credito_periodo_anterior` | 44, § 2º | Estorno de crédito de período anterior (§§ 2º a 4º, sem o § 5º) | `multa_e_juros_art_27` | `apropriacao_indevida_ou_exigibilidade` | LC, art. 45, § 2º |
| 5 | `exportacao_servico_sem_exportar_bem` | 92, § 4º | Exportação de serviço sem exportar o bem | `multa_e_juros_art_27` | `data_operacao` | LC, art. 80, § 4º |
| 6 | `exportacao_nao_comprovada` | 96, § 5º | Exportação não comprovada no prazo | `acrescimos_genericos` | `nao_definido_no_texto` | a conferir |
| 7 | `comercial_exportadora_pagamento_espontaneo` | 97, § 8º | Comercial exportadora: pagamento espontâneo | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 82, § 7º |
| 8 | `agropecuario_in_natura_180_dias` | 99, § 1º | Produto agropecuário in natura, 180 dias | `multa_e_juros_art_27` | `emissao_documento_fiscal` | LC, art. 82, § 12 |
| 9 | `deposito_alfandegado_certificado` | 157, § 1º | Depósito alfandegado certificado | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 29, § 2º (citado) |
| 10 | `admissao_temporaria_pagamento_apos_prazo` | 160, § 2º | Admissão temporária, pagamento depois do prazo (só Selic, "sem prejuízo dos demais") | `somente_juros_selic` | `vencimento_do_debito` | LC, art. 89, § 2º |
| 11 | `drawback_compromisso_nao_cumprido` | 161, § 9º | Drawback: compromissos não cumpridos | `acrescimos_genericos` | `nao_definido_no_texto` | a conferir |
| 12 | `drawback_destinacao_interna` | 161, § 17 | Drawback: destinação interna 30 dias depois do prazo | `multa_e_juros_art_27` | `nao_definido_no_texto` | LC, art. 90, § 5º |
| 13 | `repetro_destinacao_tres_anos` | 164, §§ 11 e 12 | Repetro: destinação em três anos | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 93, §§ 3º e 7º (o § 7º diz "multa de mora e Selic") |
| 14 | `descumprimento_regime_aduaneiro_especial` | 167 | Descumprimento de regime aduaneiro especial | `acrescimos_genericos` | `liberacao_declaracao_admissao_ou_registro_exportacao` | a conferir |
| 15 | `zpe_uso_em_desacordo` | 179, § 3º | ZPE: uso em desacordo | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 99, § 3º |
| 16 | `zpe_venda_mercado_interno` | 181, I e II | ZPE: venda no mercado interno | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 101 (diz "multa de mora e Selic") |
| 17 | `reporto_transferencia_cinco_anos` | 186, § 3º | Reporto: transferência de bens em cinco anos | `multa_e_juros_art_27` | `nao_definido_no_texto` | LC, art. 105, § 3º |
| 18 | `reidi_bem_nao_utilizado` | 187, § 3º | Reidi: bem não usado ou incorporado | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 106, § 3º |
| 19 | `renaval_descumprimento` | 193, § 1º | Renaval | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 107, § 3º |
| 20 | `bens_capital_sem_ativo_imobilizado` | 196, § 2º | Bens de capital (Anexo IV) sem ativo imobilizado | `multa_e_juros_art_27` | `fato_gerador` | LC, art. 109, § 3º |
| 21 | `automovel_pcd_alienado_antes_prazo` | 231, § 1º | Automóvel de pessoa com deficiência alienado antes do prazo | `acrescimos_genericos` | `nao_definido_no_texto` | LC, art. 155, § 1º |
| 22 | `redutor_ajuste_estimado_diferenca` | 375, § 12, I | Redutor de ajuste estimado: diferença a pagar | `acrescimos_genericos` | `nao_definido_no_texto` | a conferir |
| 23 | `consulta_resposta_pagamento_15_dias` | 446, parágrafo único | Tributo pago conforme resposta de consulta (afasta juros e penalidade, 15 dias) | `afasta_acrescimos` | `nao_se_aplica` | LC, art. 323-C (a conferir) |
| 24 | `credito_presumido_cancelamento_habilitacao` | 526, § 1º e 527, II | Crédito presumido devolvido por cancelamento de habilitação (juros "como nos tributos federais") | `acrescimos_genericos` | `fato_gerador` | LC, art. 315, § 2º |
| 25 | `zfm_importado_remetido_para_fora` | 528, § 3º | ZFM: bem importado remetido para fora | `multa_e_juros_art_27` | `emissao_documento_fiscal` | LC, arts. 443 e 445 |
| 26 | `zfm_nao_internamento_120_dias` | 529, § 6º | ZFM: não internamento em 120 dias | `multa_e_juros_art_27` | `nao_definido_no_texto` | LC, arts. 443 e 445 |
| 27 | `alc_importado_remetido_para_fora` | 536, § 3º | Área de livre comércio: bem importado remetido para fora | `multa_e_juros_art_27` | `emissao_documento_fiscal` | LC, arts. 461 e 463 |
| 28 | `alc_nao_internamento` | 537, § 6º | Área de livre comércio: não internamento | `multa_e_juros_art_27` | `nao_definido_no_texto` | LC, arts. 461 e 463 |

# Anexo D. Matriz de cobertura: dispositivo por dispositivo

"Gancho" quer dizer que o dispositivo espera regulamento ou ato e só tem coluna ou linha preparada.

| Dispositivo | O que diz | Onde fica |
|---|---|---|
| LC, art. 10, caput e § 1º | Momento por tipo de operação | `Cad_Regra_Fato_Gerador` (linhas 1 a 8) |
| LC, art. 10, § 3º (LC 227) | Execução continuada: primeira entre exigibilidade e pagamento | Linha 9; `Data_Exigibilidade`; `Criterio_Exigibilidade` |
| LC, art. 10, § 4º, I, a, 2 (LC 227) | Alíquota da antecipação: a menor data | `Criterio_Data_Aliquota` |
| LC, art. 10, § 4º, II, c (LC 227) | Excesso: pagamento a maior | `Adquirente_Tomou_Credito`, `ID_Perdcomp`; correção de texto do documento 153 |
| LC, art. 10, § 5º (LC 227) | Distrato: regras do cancelamento | `Mov_Cbs_Ajuste_Operacao` (tipo `cancelamento`) ligado a `Mov_Credito_Ajuste_Documento` |
| LC, art. 10, § 6º (LC 227) | Crédito do adquirente na extinção do débito | Pergunta Q157-E3 à equipe |
| LC, art. 10, § 7º (LC 227) | Regra dos 5 dias | **Gancho**: `Prazo_Maximo_Dias_Ate_Fornecimento` e `Periodo_Debito_Antecipacao`, sem carga |
| Decreto, art. 11, §§ 1º, 3º, 4º, 8º e 9º | Fornecimento, exigibilidade, data prevista | `Origem_Regra = decreto` na carga; `Fonte_Data` e `Criterio_Data_Fato_Gerador` |
| Decreto, art. 27 (LC, art. 29) | Multa de mora e juros | `Cad_Acrescimo_Legal_Cbs`, `Cad_Acrescimo_Legal_Hipotese` |
| LC, art. 29, § 5º (LC 227) | Juros sobre multa punitiva | `Juros_Incidem_Sobre_Multa_Punitiva` |
| Decreto, art. 57 (LC, art. 47, §§ 8º, 12 e 13) | Devolução e cancelamento | Três entidades do ajuste; matriz de 21 linhas |
| Decreto, arts. 59 e 61 | Erro de documento com redução da CBS | `correcao_erro`; linhas 16 a 21; aceite do adquirente |
| Decreto, art. 38 | Pagamento a maior e condição do encargo | `Condicao_Art_38`; `Adquirente_Tomou_Credito` |
| Decreto, art. 44, §§ 1º e 2º | Ajustes na apuração e estorno de período anterior | `Competencia_Apuracao` do efeito; hipótese de acréscimo 4 |
| Decreto, art. 364, §§ 7º a 10 (LC, arts. 255 e 256) | Valor de mercado da locação | `Cad_Valor_Mercado_Locacao_Parametro` (**gancho**: carga vazia até o ato conjunto); `Mov_Imovel_Valor_Referencia` |
| Decreto, art. 363, § 3º | Imóvel não oneroso | `Momento_Fato_Gerador_Nao_Oneroso` |
| LC, arts. 343 a 348; Decreto, arts. 464, 465, 582 a 585 | Transição de 2026 e redução de 0,1 ponto | `Mov_Cbs_Transicao_2026_Periodo`; parâmetros do calendário; `Reducao_Transicao_Pontos` |
| LC, art. 348, §§ 3º e 4º (LC 227) | Suprimento de omissão em 2026 | Quatro colunas em `Mov_Auto_Infracao` |
| LC, art. 341-G, § 5º, III (LC 227) | Tributo de referência de 6% e 12% em 2026 | **Gancho**: fora até a Q157-13 |
| Decreto, art. 134 | Entrega do arquivo ao adquirente | `Mov_Documento_Fiscal_Entrega_Xml`; quatro colunas por modelo; prazo vazio |
| Decreto, arts. 104 a 108 | Cadastro, domicílio principal, venda e encerramento | `Mov_Filial_Evento_Cadastral`; `Eh_Domicilio_Principal`; vencimento `comunicacao_cadastral` |
| Decreto, art. 105, § 4º-A e art. 115, § 3º (Decreto 13.075) | Início da inscrição e da emissão da pessoa física | Quatro linhas de calendário; `Cad_Qualificacao_Cbs_Inicio_Obrigacao` |
| Decreto, art. 239 (LC, arts. 164 a 167) | Limite do produtor rural | `Cad_Produtor_Rural_Parametro_Cbs` |
| LC, art. 59, § 5º; art. 60, § 7º; art. 58, §§ 4º e 5º (LC 227) | DTE unificado, documentos consolidados, integração | Sem mudança neste documento |


