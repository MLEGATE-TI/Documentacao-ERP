# Informes Técnicos de 03/11/2026: meios de pagamento, CFOP, NCM e NF-e ABI — Documento 162

> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 28** (995 entidades, 10.844 campos). Este documento compara com o dicionário os informes técnicos que você enviou em 03/11/2026 com o texto "notas tecnicas". **Atenção:** são **Informes Técnicos (IT)**, e não as Notas Técnicas que faltam (NT 2026.005, 2026.004 v1.01 e as demais do Ato nº 10; veja a Q161-3 do documento 161).

*Lidos por inteiro: IT 2026.001 v1.01 (3 páginas), IT 2024.001 v2.40 (6 páginas), IT 2023.002 v2.10 (5 páginas) e IT 2026.003 v1.00 da NF-e ABI (3 páginas). O IT 2025.002 v1.71 que veio junto é o mesmo já analisado no documento 161. Os ITs descrevem as tabelas, mas **não trazem as tabelas em si** (a planilha de CFOP, a lista de NCM e a Tabela de Códigos da NF-e ABI ficam nos portais). Dicionário conferido pelo DDL e pelos comentários da revisão 28 e pelos documentos 10 e 62 do Projeto.*

Mlegate · Alberto Beyeler · 3 de novembro de 2026

# 1. Resumo

| IT | O que traz | Efeito no dicionário |
|---|---|---|
| **2026.001 v1.01** (meios de pagamento da vinculação) | Seis códigos válidos para `tpMeioPgto`; qualquer outro é rejeitado (1003) | `Mov_Dfe_Vinculo_Pagamento.ID_Meio_Pagamento` dizia "IT ainda não recebida": agora recebida. **Carga de 6 valores e correção de texto**; sem campo |
| **2023.002 v2.10** (CFOP) | Colunas novas `indExcIBSCBS`, `Título` e `Descrição` | **Os campos já existem** (revisão 40). **Corrigir um texto**: o do `Indicador_Exclusivo_Ibs_Cbs` diz outra coisa |
| **2024.001 v2.40** (NCM) | Uma inclusão a partir de 01/10/2026 (85181020) e o histórico desde 2024 | **Só carga** de `Cad_Classificacao_Mercadoria_Versao` |
| **2026.003 v1.00** (NF-e ABI) | Tabela de Códigos v1.01 revoga a v1.00a: nome da modalidade 2, opções do tipo de instrumento e **códigos do tipo de desfazimento** (`evDesfazimAlienac`) | **Lacuna real:** o dicionário não tem o **evento de desfazimento da alienação** nem o estado "desfeita". Proposta: 2 valores de domínio, 1 valor em cada `Status`, sem campo novo |

**Contagem:** este documento **não cria campo nem entidade**; cria valores de domínio e correções de texto (seção 6). A revisão 29 prevista continua em 1.004 entidades e 10.988 campos (10.990 se você aprovar as Q161-1 e Q161-2).

# 2. IT 2026.001 v1.01: tabela de meios de pagamento da vinculação

**O que o IT diz.** As NT 2026.001 (CT-e, BP-e, NF3e, NFCom, NFAg e NFGas) e 2026.006 (NF-e e NFC-e) criaram o grupo de vinculação da transação de pagamento (para o *split payment*). A tag do meio de pagamento só aceita estes códigos, tirados da tabela nacional de meios de pagamento da NF-e:

| Código | Descrição |
|---|---|
| 15 | Boleto |
| 17 | Pix QRCode |
| 18 | TED |
| 20 | PIX chave ou QRCode estático |
| 23 | Pix automático (*) |
| 24 | TEF / booktransfer (*) |

(*) "Novos códigos que serão atualizados na tabela nacional." **Outro código causa a rejeição 1003 (Tipo de Pagamento inválido).** Inclusão de códigos só por nova versão do IT. A v1.00 (abril de 2026 em homologação e maio em produção) trouxe os códigos; a v1.01 só estende o IT a **todos os modelos** (sem nova implantação).

**O que o dicionário tem.** `Mov_Dfe_Vinculo_Pagamento.ID_Meio_Pagamento` (`gPgtoVinc/tpMeioPgto`): "meio de pagamento da Tabela Nacional de Meios de Pagamento (IT 2026.001, **ainda não recebida**: domínio aberto)". Separado dele, `Mov_Nota_Fiscal_Saida_Pagamento.ID_Forma_Pagamento` usa a tabela `tPag` completa da NF-e (a do pagamento da própria nota).

**Leitura minha.** O vínculo aceita **um subconjunto** da tabela `tPag`: os seis códigos acima. Como o IT diz que os códigos novos "serão atualizados na tabela nacional", os códigos 23 e 24 podem ainda não existir no domínio `tPag` do dicionário.

**Proposta (Q162-1), sem campo novo:**

- `ID_Meio_Pagamento` passa a apontar para um domínio próprio, `meio_pagamento_vinculo_dfe`, com os 6 valores e o código oficial em `Codigo`; os códigos 23 e 24 entram **provisórios** até a tabela nacional trazê-los.
- O ERP **avisa** (não bloqueia) quando o usuário escolhe um meio fora da lista, dizendo que a autoridade rejeita com a 1003. É a regra de avisos do dicionário.
- A lista vai para a **carga com vigência**: um novo código só entra quando você enviar a versão nova do IT.

# 3. IT 2023.002 v2.10: tabela de CFOP

| Coluna do IT | Situação do IT | No dicionário (`Cad_CFOP_Versao`) |
|---|---|---|
| `indNFe`, `indComunica`, `indTransp`, `indDevol`, `indRetor`, `indAnula`, `indRemes`, `indComb` | Inalteradas | `Indicador_NFe`, `_Comunicacao`, `_Transporte`, `_Devolucao`, `_Retorno`, `_Anulacao`, `_Remessa`, `_Combustivel`: **cobertas** |
| `indExcIBSCBS` | **Nova na v2.00** (homologação 01/09/2026; **produção 03/11/2026**) | `Indicador_Exclusivo_Ibs_Cbs`: **existe, mas o texto está errado** |
| `Título` e `Descrição` | **Novas na v2.10** (só informativas, sem rejeição) | `Titulo` e `Descricao`: **existem** (revisão 40) |

**Ponto de ajuste (Q162-2), só texto.** A descrição atual de `Indicador_Exclusivo_Ibs_Cbs` diz "verdadeiro quando este CFOP é **de uso exclusivo por contribuintes** do IBS/CBS". O IT diz outra coisa: o indicador marca os CFOP **autorizados na NF-e (modelo 55) emitida por contribuinte exclusivo do IBS/CBS** (NT 2026.007). Um CFOP pode ser de uso geral e, mesmo assim, ter o indicador marcado. Texto novo: "verdadeiro quando o CFOP é permitido na NF-e modelo 55 emitida por contribuinte exclusivo do IBS/CBS (IT 2023.002 v2.00 e NT 2026.007)". Sem mudança de campo.

**Texto de `Titulo` e `Descricao`.** O IT diz que os dois campos são **reprodução literal** do Anexo II do Convênio SINIEF s/nº de 15/12/1970, sem ajuste de redação, e que **só um Ajuste SINIEF muda o texto**; em divergência prevalece o Convênio. Isso reforça a regra do dicionário (carga como publicada). A descrição de `Titulo` na revisão 40 fala em "denominação curta", o que continua certo; acrescento a origem.

**Não resolve:** `Indicador_Cte` cita "conferir com a NT de CFOP de 2026, Q-11". A tabela do IT **não tem coluna de CT-e**; a Q-11 do documento 42 continua aberta.

**Fica faltando a tabela em si** (a planilha de CFOP v2.10 com os valores dos indicadores): sem ela não confiro a carga.

# 4. IT 2024.001 v2.40: tabela de NCM

O IT só registra as alterações da tabela de NCM usada pela NF-e; a v2.40 (setembro de 2026) acrescenta uma linha: a **Resolução Gecex nº 926, de 24/06/2026, inclui o NCM 85181020 a partir de 01/10/2026** (homologação 15/09/2026, produção 01/10/2026). Histórico completo, para conferir a carga:

| Versão | Ato | Vigência | Inclusões | Extinções |
|---|---|---|---|---|
| 1.00 e 1.01 (2024) | Gecex 563 e 561 (19/02/2024) | 01/04, 01/07 e 01/08/2024 | 43 códigos em 01/04/2024 (a v1.01 corrige um erro de digitação na lista); 3 em 01/07/2024 (48119020, 85045010, 85045090); 14 com início em 01/08/2024 (02071411 a 02071439, ajuste de vigência) | 16 códigos em 31/03/2024; 85045000 em 30/06/2024; 02071400 em 31/07/2024 (lista completa no IT) |
| 2.00 | Gecex 607 (13/06/2024) | 01/10/2024 | 15 códigos (32071020, 32071030, 39069051 a 39069069, 73151110, 73151190) | 11 códigos (32071010, 39069041 a 39069049, 73151100) |
| 2.10 | Gecex 641 (19/09/2024) | 02/01/2025 | 07129020 | 07129010 |
| 2.20 | Gecex 771 (25/07/2025) | 01/10/2025 | 23099070, 76129020, 90189097 | nenhuma |
| 2.30 | Gecex 812 (28/10/2025) | 01/02/2026 | 13 códigos (26011220, 29159070, 39072992, 59039010, 59039090, 65061010, 65061090, 73063010, 73063090, 74061010, 74061020, 74061090, 85177120) | 5 códigos (59039000, 65061000, 73063000, 74061000, 84129020) |
| **2.40** | **Gecex 926 (24/06/2026)** | **01/10/2026** | **85181020** | nenhuma |

**Como o dicionário recebe isto.** É **carga**, sem campo: cada código novo é uma linha de `Cad_Classificacao_Mercadoria` com versão a partir da data de início, e cada extinção fecha a `Vigencia_Fim` da versão (o `Tipo_Ato_Inicio` guarda a Resolução Gecex). Regras de tolerância do IT, que ficam como **aviso** (não bloqueio): NF-e que não é de exportação aceita NCM extinto por um prazo (04/11/2024 na v2.00; até 01/02/2026 na v2.30), e **NF-e de exportação não deve usar NCM extinto** depois da data de extinção, por causa da DU-E.

**Leitura minha da sucessão.** Na v2.30, a extinção de 59039000, 65061000, 73063000 e 74061000 parece ter sucessão 1 para vários (cada um ganha um código final 10 e um 90, e o 74061000 também um 20); **conferir pela Resolução**. Esses casos usam `Cad_Classificacao_Sucessao` (tipo "novo_codigo" é 1 para 1; 1 para vários precisa de outro tipo, se o domínio atual não tiver).

**Não confirmei** se a carga atual do dicionário já traz estas alterações: não há carga de NCM no que recuperei. Fica para a equipe conferir (seção 7).

# 5. IT 2026.003 v1.00: NF-e ABI, Tabela de Códigos v1.01

**O que o IT diz** (outubro de 2026). A **Tabela de Códigos da NF-e ABI v1.01** substitui a v1.00a (25/08/2026), que fica **revogada**. Mudanças:

1. **Modalidade 2 (`ide/modOper`):** a descrição passa de "Arrematação, Adjudicação ou Remição" para "**Arrematação Judicial**, Adjudicação ou Remição". A arrematação em **leilão extrajudicial** fica na modalidade 1 ("Alienação em geral"), com IBS e CBS **devidos pelo vendedor ou transmitente**.
2. **Tipo de instrumento (`infOper/tpInstrumento`):** opções alteradas para cobrir mais formas de ato de alienação; saem "Carta de arrematação" e "Carta de adjudicação" (para não confundir com "Auto de arrematação" e "Auto de adjudicação").
3. **Tipo de desfazimento (`evDesfazimAlienac/tpDesfaz`):** códigos **novos**, para o emitente informar se a alienação está sendo desfeita por distrato, decisão judicial, reversão da consolidação da propriedade e outros.

**O que o dicionário tem** (documentos 10 e 62; D-N148 a D-N153):

- `Mov_Nfeabi.ID_Modalidade_Operacao` e `ID_Tipo_Instrumento` apontam para domínios abertos (`modalidade_operacao_abi`, `tipo_instrumento_abi`), "valores do Anexo I, a carregar": **os itens 1 e 2 são só carga**, quando você enviar a tabela v1.01. A regra do leilão extrajudicial (modalidade 1, imposto do vendedor) **não muda o desenho**: o dicionário já guarda quem deve o imposto por `Mov_Operacao_Imobiliaria` e `Alienante_Regime_Regular`.
- Eventos da ABI: só **apropriação de créditos individuais** (`evApropCredIndNFeABI`, `Mov_Dfe_Evento_Adquirente`) e **pagamento de parcela**. **Não existe o evento de desfazimento** (procurei no DDL e nos comentários da revisão 28: nenhum campo nem valor com `desfaz` na ABI).
- `Mov_Aquisicao_Imovel.Status` aceita `recebida`, `conferida`, `lancada` e `cancelada`; `Mov_Operacao_Imobiliaria.Status` aceita só `calculada` e `confirmada`. **Nenhum tem "desfeita".** Hoje o dicionário só sabe **cancelar** a ABI (a aquisição "cancelada" reverte o lançamento e o crédito), o que não é o mesmo que desfazer uma alienação já autorizada.

**Proposta (Q162-3), sem campo novo:**

- **+1 valor** no domínio `tipo_evento_dfe`: `desfazimento_alienacao_abi` (código oficial do evento a carregar com o leiaute; **não está no IT**).
- Os códigos de `tpDesfaz` entram como **motivos** em `Cad_Dfe_Evento_Motivo`, e o `Mov_Dfe_Evento.Codigo_Motivo` já guarda o escolhido (como no cancelamento e na substituição).
- **+1 valor `desfeita`** em `Mov_Aquisicao_Imovel.Status` (reverte o lançamento e o crédito, como a `cancelada`, mas a nota continua válida) e **+1 em `Mov_Operacao_Imobiliaria.Status`** (marca a alienação desfeita, sem apagar a operação).
- O efeito **tributário** do desfazimento (devolução do IBS e da CBS, restabelecimento do redutor de ajuste do imóvel e do crédito do adquirente) **não está no IT**: fica para o contador (Q162-C1). Até lá, o ERP **registra o evento, marca `desfeita` e avisa**, sem recalcular nada sozinho.

**Não tenho:** a Tabela de Códigos v1.01 (os códigos), o schema do evento `evDesfazimAlienac` (campos além de `tpDesfaz`, por exemplo a data e o protocolo da ABI desfeita) nem a NT 2026.001 da ABI ("Ajustes no Leiaute e nas Regras de Validação", citada no Ato nº 10). Sem elas **não desenho campos**, e a Q162-4 pede os três.

# 6. Contagem

| Item | Entidades | Campos | Valores de domínio |
|---|---|---|---|
| Revisão 28 (real) | 995 | 10.844 | |
| Q162-1: domínio `meio_pagamento_vinculo_dfe` | 0 | 0 | +1 domínio com 6 valores |
| Q162-2: textos de `Indicador_Exclusivo_Ibs_Cbs`, `Titulo` e `Descricao` | 0 | 0 | |
| Q162-3: desfazimento da ABI | 0 | 0 | +1 tipo de evento e +2 de `Status` (mais os motivos, em carga) |
| **Total deste documento** | **0** | **0** | |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| **Q162-1** | `ID_Meio_Pagamento` do vínculo de pagamento passa a usar o domínio próprio `meio_pagamento_vinculo_dfe` com os seis códigos do IT 2026.001 (23 e 24 provisórios), e o ERP **avisa** (sem bloquear) quando o meio estiver fora da lista? | **Sim** |
| **Q162-2** | Corrijo o texto de `Indicador_Exclusivo_Ibs_Cbs` (CFOP permitido na NF-e de contribuinte exclusivo, e não "CFOP de uso exclusivo") e acrescento a origem (Anexo II do Convênio SINIEF) em `Titulo` e `Descricao`? | **Sim** |
| **Q162-3** | Aprova o desenho mínimo do desfazimento da alienação na NF-e ABI: valor `desfazimento_alienacao_abi` em `tipo_evento_dfe`, os códigos de `tpDesfaz` como motivos e o valor `desfeita` em `Mov_Aquisicao_Imovel.Status` e `Mov_Operacao_Imobiliaria.Status`, sem campo novo? | **Sim**; os campos do evento esperam o schema |
| **Q162-4** | Você envia: a **Tabela de Códigos da NF-e ABI v1.01**, a **planilha de CFOP v2.10**, a **tabela de NCM** em uso, a **NT 2026.001 da NF-e ABI** e as notas técnicas ainda não recebidas (NT 2026.005 e 2026.004 v1.01, Q161-3)? | **Sim**, começando pela NT 2026.001 da ABI e pela NT 2026.005 |

# 8. Para o contador e para a equipe

| Id | Pendência | Tratamento provisório |
|---|---|---|
| **Q162-C1** | Efeito do desfazimento da alienação (distrato, decisão judicial, reversão da consolidação da propriedade): devolução do IBS e da CBS, redutor de ajuste do imóvel, crédito do adquirente, reflexo contábil | O ERP registra o evento, marca `desfeita` e avisa; não estorna sozinho |
| **Q162-E1** (equipe) | Conferir a carga de NCM do dicionário contra o histórico do IT 2024.001 (seção 4), principalmente o NCM 85181020 a partir de 01/10/2026 e as sucessões 1 para vários da v2.30 | Carga como publicada na tabela do portal |
| **Q162-E2** (equipe) | Conferir se o domínio `tPag` do dicionário já tem os códigos 23 (Pix automático) e 24 (TEF / booktransfer) | Entram como provisórios no domínio do vínculo |

# 9. Limites

- **O que li** são ITs de tabelas; eles dizem **o que mudou**, mas as tabelas (CFOP, NCM, Tabela de Códigos da ABI) **não vieram**: não confiro valores de indicador, só a estrutura e os textos.
- A **data de produção de 03/11/2026** do `indExcIBSCBS` é a do controle de versões do IT 2023.002.
- O **código do evento de desfazimento** e os valores de `tpDesfaz` não estão no IT.
- A leitura da sucessão de NCM da v2.30 é minha, pelo prefixo dos códigos; a Resolução Gecex 812 é que vale.
- Nada foi validado pelo contador.
