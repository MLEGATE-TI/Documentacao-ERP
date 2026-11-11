# EFD-Contribuições a partir do Guia Prático v1.35 — Documento 44

*Leitura do Guia Prático da EFD-Contribuições (versão 1.35, de 18/06/2021), do roteiro do lucro presumido e de 36 tabelas do Portal do SPED contra o dicionário e os documentos 10, 14, 32, 33, 34, 36, 37, 38, 39, 40, 41, 42 e 43. Registro por registro e campo por campo. Propostas de desenho; nada foi alterado no dicionário.*

Mlegate · Alberto Beyeler · Outubro de 2026

*Revisão de 18/10/2026: ECF, SAT-CF-e e MFE (`Cad_Equipamento_Fiscal`, `Mov_Ecf_Reducao_Z` e `Mov_Ecf_Reducao_Z_Tributo`) passam da onda 2 para a onda 1, como a D-N93 aplicou na revisão 3 do dicionário. Ficam 29 entidades na revisão 3 e 6 na onda 2. Nenhum conteúdo do dicionário muda: o texto deste documento é que estava atrasado.*

# 1. Resumo

O Guia tem **203 registros e 1.712 campos**. distribuídos em seis grupos de blocos (0. A e 9; C; D. I e P; F; M; 1). Classifiquei cada campo em seis classes: 344 já estão cobertos pelo dicionário. 577 são derivados do que o ERP já grava (nota. item. título. ativo. apuração). 244 existem só no arquivo (REG. contadores. totais). 27 já têm lugar numa proposta dos documentos 33 a 43. 125 pedem campo novo em entidade existente e 395 pedem entidade nova.

A conclusão é a que o desenho já previa: **o arquivo é gerado, não digitado**. A maior parte dos Blocos A, C e D sai de `Mov_Nota_Fiscal_Saida`, `Mov_Nota_Fiscal_Entrada` e seus itens, e todo valor de PIS e Cofins sai de `Mov_Apuracao_Tributo_Item`; as consolidações (C180, C190, C400, C490, C860 e parecidas) são agrupamentos. O que falta é pouco e concentrado: o **resultado do período** (Bloco M), o **controle de créditos, retenções e processos** que atravessa períodos (Bloco 1 e partes do F) e os dados que não existem em nenhum outro lugar do ERP (operações diversas do F100, ativo do F120, estoque de abertura, equipamentos fiscais, Bloco I).

Cada bloco foi analisado separadamente e as propostas se sobrepunham. Consolidei tudo antes de escrever: das 36 entidades que as seis análises propuseram restaram **35** (duas do Bloco 1 foram absorvidas pelo Bloco M e uma filha por CST foi acrescentada), das quais **29 entram na revisão 3 e 6 ficam na onda 2** (nicho, só com cliente; as três do varejo legado, ECF, SAT-CF-e e MFE, subiram para a revisão 3 pela D-N93). Há ainda **62 linhas de campo novo** em entidades existentes (57 na onda 1), **19 domínios novos** e 5 ampliações de domínio.

Seis achados pesam mais que o resto:

1. **O Bloco M precisa de uma estrutura só para PIS e Cofins.** M100/M500, M200/M600, M210/M610 e os demais pares são idênticos; um campo `ID_Imposto` evita duplicar nove tabelas e repetir as regras de fechamento. Em 2027, a mesma estrutura serve para retificar períodos antigos.
2. **Versão, status e fechamento têm um dono só:** `Mov_Efd_Contribuicoes_Periodo`. Antes, três análises propunham o seu próprio controle de versão (período, Bloco M e CPRB). Fechada a escrituração, nada muda; retificar cria a versão seguinte e marca a anterior como substituída. É o que permite reproduzir o valor original dentro dos 5 anos de decadência.
3. **O critério de escrituração decide quais registros nascem.** O roteiro do lucro presumido de 2013 mostra que a opção por caixa gera F500 e F525, a competência consolidada gera F550, e só a opção "detalhada" (valor 9 do Guia de 2021) gera os Blocos A, C, D e F por documento. Por isso `Criterio_Escrituracao_Cumulativo` fica no perfil fiscal, com vigência, e o gerador o consulta.
4. **Os registros extemporâneos (1101, 1102, 1200, 1210, 1220, 1501, 1502, 1600, 1610 e 1620) não devem ser gerados.** O próprio Guia diz que o PVA os recusa para períodos a partir de 08/2013, porque desde a IN RFB 1.387/2013 se retifica a escrituração do período. A proposta é gerar só a retificadora; o mapeamento fica para importar histórico.
5. **O Guia é de 2021.** Conferi o que a tabela oficial mais nova já mostra ser posterior a ele: NFCom (modelo 62) nos D500 e D600, motivos 101 a 103 do 0120 (Perse), CNPJ alfanumérico, leiaute 006 do arquivo, códigos 10 a 12 de ajuste (2026) e três tabelas de 09/2026. **Falta a versão atual do Guia** (seção 12).
6. **As tabelas do Portal corrigem o documento 43 em 20 pontos.** O mais importante: `COD_DETALHAM` é o detalhamento da CPRB (Tabela 5.1.2), não do ajuste de base; as colunas P e R de `OUTROS_ALIQ_DIFER` são contribuição e crédito, não cumulativo e não cumulativo; e três tabelas do Portal (4.3.11, 4.3.13 e 4.3.16) estão à frente dos arquivos que o documento 43 tomou como fonte vigente.

Proponho 10 decisões, **D-N83 a D-N92**, na seção 13. As revisões dos documentos 40 (NFCom), 41 (NFS-e) e 43 (tabelas) seguem nos próprios documentos.

# 2. Fontes lidas

| Fonte | O que é | Uso |
|---|---|---|
| Guia Prático da EFD-Contribuições, versão 1.35 | 18/06/2021, 433 páginas. Leiaute dos 203 registros, regras de preenchimento e as tabelas externas 4.x, 5.x e 7.x | Base do documento: lido registro por registro, com os campos, os tamanhos, a obrigatoriedade e as observações |
| Roteiro de escrituração do lucro presumido (`contr.pdf`) | PVA 2.04, 2013. Passo a passo da escrituração de PJ no regime cumulativo | Mostra o que cada opção do 0110 gera; resolve a leitura do critério de escrituração (seção 3) |
| Tabelas 4.3.3 a 4.3.18, 5.1.1 e 7.1.1 a 7.1.4 | 19 documentos .doc e 17 planilhas do Portal do SPED | Conferência contra os 86 arquivos do documento 43 (seção 10) |
| CFOP × operações geradoras de créditos | Planilha "Tabela I": 89 CFOP em 5 grupos | Confirma `CFOP_CREDITO` (idêntico) e esclarece `CFOP_DEVOLUCAO_VENDA` |
| Correlação DACON × EFD-Contribuições | Linhas das fichas do DACON e os registros da EFD que as substituem | Só serve à migração de histórico do DACON; não cria entidade (seção 10) |
| Dicionário (543 entidades) e documentos 10, 14, 32 a 43 | Modelo atual e propostas pendentes | Conferência de cada nome de entidade e de campo citado |

**Limite da leitura.** O Guia é de 06/2021. O que mudou depois dele aparece como "depende da versão atual do Guia" (seção 12) e não foi tratado como regra. As tabelas do Portal de 09/2026 sustentam parte dessas mudanças, mas só as tabelas, não o texto dos registros.

# 3. O que o Guia pede e como o ERP responde

A regra de leitura é a mesma do dicionário: nada é digitado para o arquivo. Cadastros têm vigência e são lidos na data final do período; valores de tributo vêm de `Mov_Apuracao_Tributo_Item`, uma linha por tributo, e o arquivo junta PIS e Cofins pelo mesmo item; consolidações são agrupamentos; e só o que decide algo no período (rateio, opção de uso do crédito, ajuste, saldo) é gravado e congelado no fechamento. Por bloco:

**Blocos 0, A e 9** (33 registros, 207 campos). O Bloco 0 é quase todo cadastro já existente, gerado só para o que o arquivo cita (empresa, estabelecimentos, participantes, itens, unidades, plano de contas, centros de custo). O Bloco A nasce da NFS-e, que o ERP emite e recebe (docs 33, 35 e 41); a NFS-e emitida pelo próprio tomador conta como serviço contratado. O Bloco 9 é contagem. O que não existe: o retrato mensal (receita por classe do 0111, receita da CPRB do 0145, parcela que não é receita bruta do 0900), o telefone do participante e a atividade preponderante do 0000.

**Bloco C** (48 registros, 447 campos). C100 e C170 saem da nota e do item. Os processos referenciados (C111, C188, C198, C489, C499, C509, C609, C830, C890) saem de uma estrutura só (seção 5). A opção entre escrituração individualizada e consolidada é por filial e grupo de documento (C010). A única parte sem dado de origem no ERP é o varejo legado: Redução Z (C405) e os totais por item (C481 e C485), que entram na revisão 3 junto com o equipamento fiscal (ECF, SAT-CF-e, MFE), por haver cliente que os usa (Q-C-9, D-N93).

**Blocos D, I e P** (40 registros, 287 campos). O Bloco D sai de notas de transporte e comunicação: D100 e D200 de `Mov_Cte` (doc 42), D500 e D600 das notas de comunicação (modelos 21 e 22 e, a conferir, NFCom 62 do doc 40). O Bloco I (receita e dedução por conta contábil de instituições financeiras, seguradoras e assemelhadas) não tem nada no ERP e vira duas entidades de onda 2. O Bloco P (CPRB) está quase todo em `Mov_Reinf_Cprb_Apuracao`, `Mov_Reinf_Cprb_Ajuste` e `Cad_Cprb_Atividade`; falta a receita bruta total do estabelecimento.

**Bloco F** (26 registros, 256 campos). F500 a F569 são agrupamentos de `Mov_Apuracao_Tributo_Item` (no caixa, rateando a baixa do título); F600 vem de `Mov_Titulo_Retencao`; F120 e F130 de `Cad_Ativo_Imobilizado` e da depreciação. O peso das entidades novas está em F100, F120/F130, F150, F700 e, no nicho, F205/F210 (imobiliário) e F800 (sucessão).

**Bloco M** (33 registros, 272 campos). É a consolidação do período, na visão da empresa (A, C, D e F são por estabelecimento). O ERP já calcula tudo por item e guarda o crédito em `Mov_Credito_Fiscal`; falta gravar o resultado: totais, uso parcial do crédito, retenção deduzida, ajustes, diferimento, saldo transportado e o vínculo ao MIT, à DCTFWeb e ao DARF. M400/M410 e M800/M810 não ganham entidade: são agrupamento por CST, natureza da receita e conta.

**Bloco 1** (23 registros, 243 campos). Guarda estados que atravessam períodos: saldo de crédito (1100, 1500), saldo de retenção (1300, 1700), processos (1010, 1011, 1020, 1809) e ajustes de base (1050). Os saldos são fórmula sobre todos os períodos (regra do documento 10: saldo nunca é armazenado), e o Jurídico já tem processo, juízo e suspensão (`Cad_Processo`, `Mov_Processo_Juizo`, `Mov_Processo_Suspensao`).

# 4. Panorama por bloco

| Bloco | Registros | Campos | Coberto | Derivado | Só no arquivo | Já proposto (docs 33 a 43) | Campo novo | Entidade nova |
|---|---|---|---|---|---|---|---|---|
| Blocos 0, A e 9 | 33 | 207 | 65 | 48 | 50 | 9 | 12 | 23 |
| Bloco C | 48 | 447 | 83 | 214 | 49 | 8 | 54 | 39 |
| Blocos D, I e P | 40 | 287 | 51 | 101 | 49 | 8 | 37 | 41 |
| Bloco F | 26 | 256 | 82 | 84 | 35 | 0 | 9 | 46 |
| Bloco M | 33 | 272 | 2 | 19 | 34 | 0 | 0 | 217 |
| Bloco 1 | 23 | 243 | 61 | 111 | 27 | 2 | 13 | 29 |
| Total | 203 | 1712 | 344 | 577 | 244 | 27 | 125 | 395 |

"Entidade nova" conta o campo do Guia cuja origem é uma das entidades propostas na seção 6; no Bloco M são 217 de 272 porque o resultado do período é todo gravado no fechamento (cada campo é calculado do que existe e congelado). A lista campo a campo, com o destino de cada um, está nas abas "Registros" e "Campos" do anexo.

# 5. Sobreposições entre blocos e a estrutura única adotada

Seis análises independentes propuseram estruturas parecidas para o mesmo problema. A tabela mostra o que cada uma propunha e o que fica.

| Tema | Propostas dos blocos | Estrutura adotada |
|---|---|---|
| Versão, status e fechamento | Período (Bloco 0), cabeçalho do Bloco M e período da CPRB (Bloco P) tinham cada um o seu `Numero_Versao`, `Status` e `Hash_Fechamento` | `Mov_Efd_Contribuicoes_Periodo` é o único dono. `Mov_Apuracao_Pis_Cofins` (por tributo), `Mov_Cprb_Estabelecimento_Periodo` e as entidades de onda 2 do D e do I guardam só `ID_Periodo`. Identidade da empresa e da SCP também fica no período. |
| Ajuste de base de cálculo (M215, M615, 1050) | Bloco M: `Mov_Apuracao_Pis_Cofins_Ajuste` com `Alvo_Ajuste`; Bloco 1: `Mov_Ajuste_Base_Pis_Cofins` e filha por CST; doc 43: catálogo `Cad_Ajuste_Base_Pis_Cofins` | Um só movimento: `Mov_Apuracao_Pis_Cofins_Ajuste` (Alvo_Ajuste = base_calculo). O 1050 é o agrupamento de M215 e M615 por data de referência, código e filial; a parcela por CST vira a filha `Mov_Apuracao_Pis_Cofins_Ajuste_Cst`. As duas entidades do Bloco 1 caem. O catálogo do doc 43 fica como está. |
| Processo referenciado (todos os x111, x139, x509 e semelhantes) | Bloco A: `ID_Processo_Fundamento` no item; Bloco C: `ID_Processo` no item e nas Reduções Z; Bloco F: `Mov_Apuracao_Processo_Referenciado`; Bloco I: `ID_Processo` no lançamento | `Mov_Apuracao_Processo_Referenciado` (genérica, com `Origem_Tipo`, `ID_Origem`, `ID_Processo` e `ID_Efeito_Tributario`). Os campos `ID_Processo` e `ID_Processo_Fundamento` dos itens saem: um item pode ter mais de um processo, e o registro do Guia se repete. O ajuste do Bloco M mantém `ID_Processo` próprio, porque o M215 tem um só documento. |
| Critério de escrituração (0110.IND_REG_CUM) | `Criterio_Escrituracao_Cumulativo` (Bloco 0) e `Criterio_Escrituracao_Pis_Cofins` (Bloco F) | `Criterio_Escrituracao_Cumulativo` em `Cad_Empresa_Perfil_Fiscal`, com vigência. |
| Método de apropriação do crédito (0110.IND_APRO_CRED) | `Metodo_Apropriacao_Credito_Comum` (Bloco 0) e `Metodo_Apropriacao_Credito` (Bloco M) | `Metodo_Apropriacao_Credito_Comum` no mesmo lugar. |
| Campos novos de `Mov_Credito_Fiscal` | Bloco 1: 7 campos; Bloco F: 4; Bloco M: 3, com nomes diferentes para o mesmo conteúdo (`Competencia_Origem`, `Competencia_Credito`, `Competencia_Apuracao`) | Oito campos e uma ampliação do enum `Origem` (seção 7), com um nome para cada conteúdo. |
| Natureza da retenção | `natureza_retencao_pis_cofins` (Bloco 1) e `natureza_retencao_pis_cofins_fonte` (Bloco F) | Um domínio: `natureza_retencao_pis_cofins`. |
| Opção por individualizada ou consolidada (C010) e parâmetros do 0110 | O Bloco C sugeriu fundir `Cad_Efd_Contribuicoes_Opcao_Escrituracao` com os parâmetros do 0110 | Não fundir. O 0110 é por empresa e anual; a opção do C010 é por filial e por grupo de documento, com vigência própria. |
| Catálogo de informações complementares (0450) | Bloco 0 e Bloco C | Uma entidade: `Cad_Informacao_Complementar_Fiscal`. |
| Complemento de nota de utilidade | Bloco C (energia, água e gás) e Bloco D (comunicação) | Uma entidade: `Mov_Nota_Fiscal_Utilidade`, com o escopo estendido às notas de comunicação. |

# 6. Entidades novas

São **35**, todas conferidas contra o `model.json` e contra os documentos 33 a 43 (nenhum nome colide). "Vig." indica entidade de cadastro com vigência; as demais são movimento e não têm. Os campos de cada uma estão na aba "Entidades propostas" do anexo.

| Nº | Entidade | Registros | Vig. | Onda | O que guarda |
|---|---|---|---|---|---|
| 1 | `Mov_Efd_Contribuicoes_Periodo` | 0111, 0120, 0145, 9900, M001, M990 | não | 1 | Retrato mensal da empresa (ou da SCP) e dono único de versão, status e fechamento de toda a escrituração; guarda a receita por classe (0111), a receita para a CPRB (0145) e o mês sem dados (0120). Um período tem vários arquivos em `Mov_Escrituracao_Arquivo` (D-N94). |
| 2 | `Mov_Efd_Contribuicoes_Periodo_Bloco` | 0900 | não | 1 | Receita total e parcela que não é receita bruta, por bloco (A, C, D, F, I e 1), congeladas para o 0900. |
| 3 | `Cad_Participante_Telefone` | 0100 | sim | 1 | Telefones do participante, com vigência (0100); serve também a outros leiautes. |
| 4 | `Cad_Efd_Contribuicoes_Opcao_Escrituracao` | C010, C100, C170, C175, C180, C190, C380, C400… | sim | 1 | Opção por filial e grupo de documento: individualizada ou consolidada (C010.IND_ESCRI); decide entre C100/C170 e C180/C190, C400 e C490, C800 e C860. |
| 5 | `Cad_Informacao_Complementar_Fiscal` | C110, C500 | não | 1 | Catálogo de informações complementares (0450). |
| 6 | `Mov_Nota_Fiscal_Informacao_Complementar` | C110, C500 | não | 1 | Informações complementares por nota (C110 e COD_INF do C500). |
| 7 | `Cad_Equipamento_Fiscal` | C400, C800, C860 | sim | 1 | ECF, SAT-CF-e, MFE e terminal de NFC-e, com vigência (C400, C800, C860). |
| 8 | `Mov_Ecf_Reducao_Z` | C405, C481, C485, C490 | não | 1 | Redução Z do equipamento (C405). |
| 9 | `Mov_Ecf_Reducao_Z_Tributo` | C481, C485, C489, C490, C491, C495, C499 | não | 1 | PIS e Cofins por item e CST da Redução Z (C481, C485 e base do C490). |
| 10 | `Mov_Nota_Fiscal_Utilidade` | C500, C600 | não | 1 | Complemento 1:1 da nota de energia, água, gás e comunicação (C500, C600, D500, D600). |
| 11 | `Mov_Receita_Comunicacao_Complementar` | D600, D601, D605 | não | 2 | Receita de comunicação sem nota no período: a faturar, pré-paga, de terceiros e exclusões (D600, D601, D605). |
| 12 | `Cad_Conta_Contabil_Receita_Deducao_Efd` | I100, I200, I300 | sim | 2 | Mapeia conta contábil para código de receita ou dedução, CST e regra de leitura do saldo, com vigência (I100 a I300). |
| 13 | `Mov_Receita_Deducao_Setorial` | I100, I199, I200, I299, I300, I399 | não | 2 | Linha de receita ou dedução por filial, período, código, CST e conta (Bloco I: instituições financeiras, seguradoras e assemelhadas). |
| 14 | `Mov_Cprb_Estabelecimento_Periodo` | P100, P200 | não | 1 | Receita bruta total do estabelecimento no período, base do P100 e do P200. |
| 15 | `Mov_Operacao_Fiscal_Diversa` | F100, F111 | não | 1 | Receita ou custo com crédito sem nota nos Blocos A, C e D: JCP, aluguel sem nota, arrendamento, consórcio, importação por DI (F100). |
| 16 | `Cad_Ativo_Direito_Credito_Pis_Cofins` | F120, F129, F130, F139 | sim | 1 | Direito de crédito do bem do ativo: base, gênero, utilização, origem, parcela excluída e parcelamento, com vigência (F120, F130). |
| 17 | `Mov_Credito_Estoque_Abertura` | F150 | não | 1 | Estoque na data do ingresso no regime não cumulativo; crédito em parcelas via Mov_Credito_Fiscal (F150). |
| 18 | `Mov_Evento_Sucessao_Empresarial` | F800 | não | 2 | Incorporação, fusão e cisão; os créditos transferidos viram Mov_Credito_Fiscal (F800). |
| 19 | `Mov_Credito_Imobiliario_Unidade` | F205, F210, F211 | não | 2 | Controle mensal do crédito por unidade vendida, tributo e tipo de custo, incorrido ou orçado (F205, F210, F211). |
| 20 | `Mov_Apuracao_Processo_Referenciado` | A111, C111, C188, C198, C489, C499, C509, C609… | não | 1 | Estrutura única de processo referenciado: liga qualquer linha de apuração, nota ou operação a Cad_Processo (todos os x111, x139, x509 e semelhantes). |
| 21 | `Mov_Deducao_Contribuicao_Diversa` | F700 | não | 1 | Deduções que não são crédito do regime não cumulativo (F700). |
| 22 | `Mov_Contribuicao_Cooperativa_Recolhida` | F600 | não | 2 | Contribuição recolhida por cooperativa ou a ela retida, só se houver cooperativa entre os clientes (F600, D-N39 do documento 36). |
| 23 | `Mov_Apuracao_Pis_Cofins` | M001, M200, M600, M990 | não | 1 | Resultado consolidado do período por tributo (M200 e M600): totais não cumulativo e cumulativo, créditos descontados, retenções, deduções e total a recolher; versão e fechamento vêm do período. |
| 24 | `Mov_Apuracao_Pis_Cofins_Item` | M210, M610, M211, M611, M350 | não | 1 | Contribuição apurada por código (M210, M610, M211, M611 e M350, Pasep sobre a folha). |
| 25 | `Mov_Apuracao_Pis_Cofins_Credito` | M100, M500 | não | 1 | Crédito do período por tipo (M100 e M500): origem, disponível, opção de uso, descontado e saldo transportado. |
| 26 | `Mov_Apuracao_Pis_Cofins_Credito_Base` | M105, M505 | não | 1 | Composição do crédito por natureza da base e CST (M105 e M505), com o rateio gravado. |
| 27 | `Mov_Apuracao_Pis_Cofins_Ajuste` | 1050, M110, M215, M220, M510, M615, M620 | não | 1 | Ajuste de crédito, de base ou de contribuição num só lugar (M110, M510, M215, M615, M220, M620); também é a fonte do 1050. |
| 28 | `Mov_Apuracao_Pis_Cofins_Ajuste_Detalhe` | M115, M515, M225, M625 | não | 1 | Detalhamento dos ajustes (M115, M515, M225, M625), com ligação opcional ao item de apuração de origem. |
| 29 | `Mov_Apuracao_Pis_Cofins_Debito` | M205, M605 | não | 1 | Débito por regime e código de receita (M205 e M605), ligado ao MIT, à DCTFWeb e ao DARF. |
| 30 | `Mov_Apuracao_Pis_Cofins_Diferimento` | M230, M630, M300, M700 | não | 1 | Diferimento e recebimento de receita diferida (M230, M630, M300, M700). |
| 31 | `Mov_Processo_Efeito_Tributario` | 1010, 1011, 1020, 1809, 1050 | não | 1 | Decisão ou ato do processo que muda CST, base, alíquota, crédito ou exigibilidade; elo entre o Jurídico e o cálculo (1010, 1011, 1020, 1809). |
| 32 | `Mov_Apuracao_Tributo_Item_Decisao` | 1011 | não | 1 | CST, base, alíquota e valor conforme a decisão, por item (1011). |
| 33 | `Mov_Titulo_Retencao_Aplicacao` | 1300, 1700 | não | 1 | Consumo da retenção na fonte: dedução, restituição ou compensação (1300, 1700). |
| 34 | `Cad_Tipo_Credito_Pis_Cofins_Utilizacao` | 1100, 1500 | sim | 1 | Quais formas de utilização cada tipo de crédito admite, com vigência (1100, 1500). |
| 35 | `Mov_Apuracao_Pis_Cofins_Ajuste_Cst` | 1050 | não | 1 | Parcela do ajuste de base por CST (VL_AJ_CST01 a 99 do 1050); a soma das parcelas é o valor do ajuste. |

**Onda 2 (6 entidades).** Ficam desenhadas aqui e fora da revisão 3, como os condomínios (D-N61) e o CT-e (D-N68): `Mov_Receita_Comunicacao_Complementar`, `Cad_Conta_Contabil_Receita_Deducao_Efd`, `Mov_Receita_Deducao_Setorial`, `Mov_Evento_Sucessao_Empresarial`, `Mov_Credito_Imobiliario_Unidade`, `Mov_Contribuicao_Cooperativa_Recolhida`. São o Bloco I, a receita de comunicação sem nota, a contribuição de cooperativa, o crédito imobiliário por unidade e a sucessão empresarial. As três entidades do varejo legado (`Cad_Equipamento_Fiscal`, `Mov_Ecf_Reducao_Z` e `Mov_Ecf_Reducao_Z_Tributo`) eram da onda 2 nesta redação; subiram para a onda 1 e já constam do dicionário na revisão 3 (D-N93, Contabilidade & Fiscal). O ERP não limita o tipo de cliente; por isso o desenho existe e a criação espera o primeiro cliente que precise. Um ponto de atenção: `Mov_Operacao_Imobiliaria` exige o regime de IBS/CBS (Q-F-4) e não serve à venda anterior a 2027.

**Relação com a decadência.** Todas as entidades de movimento do período (as do Bloco M e as de onda 1 do D, F e P) guardam `ID_Periodo`; a retificação cria um período novo, copia o que não mudou e marca o anterior como substituído. Isso vale até o fim da decadência de cada competência, mesmo depois que o PIS e a Cofins forem substituídos pela CBS e pelo IBS.

# 7. Campos novos em entidades existentes

São **62 linhas** (57 de onda 1 e 5 de onda 2), já sem as duplicidades da seção 5. Itens que o Bloco C e o Bloco A propunham em `Mov_Apuracao_Tributo_Item` (`ID_Processo` e `ID_Processo_Fundamento`) saíram.

| Entidade | Campo | Registros | Onda | Observação |
|---|---|---|---|---|
| `Cad_Empresa_Perfil_Fiscal` | `Metodo_Apropriacao_Credito_Comum` | 0110 | 1 | IND_APRO_CRED; vale o ano-calendário; com rateio o 0111 é obrigatório. |
| `Cad_Empresa_Perfil_Fiscal` | `Criterio_Escrituracao_Cumulativo` | 0110 | 1 | IND_REG_CUM; só no cumulativo exclusivo; decide entre F500/F525, F550 e A, C, D e F detalhados. |
| `Cad_Empresa_Perfil_Fiscal` | `ID_Natureza_Pj_Efd` | 0000 | 1 | Geral, cooperativa ou entidade do Pasep sobre a folha. |
| `Cad_Empresa_Perfil_Fiscal` | `ID_Atividade_Preponderante_Efd` | 0000 | 1 | Seis valores; não é o 0/1 da EFD ICMS/IPI. |
| Mov_Escrituracao_Arquivo (doc 33) | `Situacao_Especial` | 0000 | 1 | IND_SIT_ESP. |
| Mov_Escrituracao_Arquivo (doc 33) | `ID_Entidade_Ligada` | 0000, 0035 | 1 | Cada SCP gera uma EFD separada. |
| Mov_Escrituracao_Arquivo (doc 33) | `Criterio_Detalhe_Receita_Recebida` | F525 | 1 | Critério usado para abrir a receita recebida na geração. |
| `Cad_Entidade_Ligada_Reinf` | `Descricao_Objeto` | 0035 | 1 | Objeto da SCP. |
| `Cad_Empresa_Responsavel` | `ID_Participante_Escritorio` | 0100 | 1 | Escritório de contabilidade (PJ). |
| `Cad_Dimensao_Contabil` | `Eh_Centro_Custo` | 0600 | 1 | Marca a dimensão exportada como centro de custo. |
| `Cad_Conta_Contabil` | `ID_Filial_Especifica` | 0500 | 1 | CNPJ_EST do 0500. |
| `Mov_Apuracao_Tributo_Item` | `Classe_Receita_Efd` | 0111 | 1 | Gravada na apuração pelo Motor de Regras e imutável após o fechamento. |
| `Mov_Apuracao_Tributo_Item` | `Compoe_Receita_Bruta` | 0111, 0145, 0900 | 1 | Falso alimenta a parcela "não receita bruta" do 0900. |
| `Mov_Apuracao_Tributo_Item` | `ID_Titulo_Recolhimento` | A120 | 1 | Data de pagamento do PIS/Cofins-Importação. |
| `Mov_Apuracao_Tributo_Item` | `ID_Entidade_Ligada` | 0035 | 1 | SCP a que a operação pertence. |
| `Mov_Apuracao_Tributo_Item` | Origem_Tipo (6 valores novos) | F100, F120, F130, F500, I200, D600 | 1 | Hoje {nota_fiscal_entrada, nota_fiscal_saida, evento_conta_financeira, pagamento_imobiliario}. Os dois últimos valores pertencem à onda 2. |
| `Mov_Nota_Fiscal_Saida` | `ID_Entidade_Ligada` | A100, 0035 | 1 | SCP, mesmo com nota emitida pelo CNPJ da sócia ostensiva. |
| `Mov_Nota_Fiscal_Saida` | `Valor_Abatimento_Nao_Tributado` | C100 | 1 | VL_ABAT_NT. |
| `Mov_Nota_Fiscal_Saida` | `Subserie` | C600 | 1 | Modelos legados. |
| `Mov_Nota_Fiscal_Saida` | `ID_Equipamento_Fiscal` | C800, C860 | 1 | Equipamento SAT, MFE ou ECF emissor. |
| `Mov_Nota_Fiscal_Entrada` | `ID_Entidade_Ligada` | A100, 0035 | 1 | SCP. |
| `Mov_Nota_Fiscal_Entrada` | `Indicador_Pagamento` | C100 | 1 | IND_PGTO na entrada; na saída o equivalente é `Indicador_Prazo` de `Mov_Nota_Fiscal_Saida_Pagamento` (doc 33). |
| `Mov_Nota_Fiscal_Entrada` | `Valor_Abatimento_Nao_Tributado` | C100 | 1 | VL_ABAT_NT. |
| `Mov_Nota_Fiscal_Entrada` | `Subserie` | C395, C500 | 1 | Modelos legados. |
| `Mov_Nota_Fiscal_Entrada_Item` | `ID_Natureza_Operacao` | C170 | 1 | COD_NAT; catálogo 0400. |
| `Mov_Nota_Fiscal_Entrada_Item` | `ID_Conta_Contabil` | C170, C191, C195 | 1 | COD_CTA, obrigatório desde 11/2017. |
| `Mov_Nota_Fiscal_Entrada_Item` | `ID_Natureza_Frete_Efd` | D101, D105 | 1 | IND_NAT_FRT. |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Natureza_Operacao` | C170 | 1 | COD_NAT. |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Conta_Contabil` | C170, C175, C181, C185, C601 | 1 | Conta de receita (COD_CTA). |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Tipo_Receita_Comunicacao` | D600 | 1 | IND_REC; sugestão automática pelos campos da NFCom. |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Classificacao_Item_Utilidade` | D601, D605 | 1 | COD_CLASS (Tabela 4.4.1). |
| `Mov_Nota_Fiscal_Saida_Item_Importacao` | Tipo_Declaracao (valor dsi) | C120 | 1 | COD_DOC_IMP = 1. |
| `Cad_Produto_Servico` | `Codigo_Item` | 0200 e outros | 1 | COD_ITEM; lacuna 1 do doc 37. |
| `Cad_CFOP` | `Indicador_Sem_Movimentacao_Fisica` | C170 | 1 | IND_MOV. |
| `Cad_Processo` | `ID_Origem_Processo_Efd` | x111 e 1010 | 1 | IND_PROC. |
| `Mov_Processo_Juizo` | `ID_Orgao_Administrativo` | 1020, 1809 | 1 | Distingue RFB, DRJ, CARF e outro. |
| `Cad_Filial_Perfil_Fiscal` | `ID_Atividade_Setorial_Bloco_I` | I010 | 2 | IND_ATIV, de 01 a 06; só o Bloco I. |
| `Mov_Reinf_Cprb_Ajuste` | `ID_Origem_Ajuste_Efd` | P210 | 1 | Códigos 07, 08 e 09 da Tabela 4.3.8; o código do Reinf é outro. |
| `Mov_Reinf_Cprb_Ajuste` | `Numero_Documento_Ajuste` | P210 | 1 | O R-2060 não tem. |
| `Cad_Motor_Regra_Resultado` | Tipo_Resultado (2 valores novos) | 0111, 0900 | 1 | A classe da receita sai do Motor de Regras, sem tabela nova. |
| `Cad_Ativo_Imobilizado` | `ID_Item_Nota_Entrada_Origem` | F120, F130 | 1 | Origem, fornecedor, NCM e CST do crédito vêm da nota. |
| `Cad_Empreendimento_Imobiliario` | Estrutura_Juridica (valores novos) | F200 | 2 | Hoje {direta, scp}. |
| `Mov_Operacao_Imobiliaria` | `Situacao_Unidade_Na_Venda` | F200 | 2 | Forma IND_OPER com à vista ou a prazo. |
| `Mov_Operacao_Imobiliaria` | `Numero_Contrato_Venda` | F200 | 2 | Contrato ou documento da venda. |
| `Mov_Apuracao_Imobiliaria` | `Valor_Receita_Financeira_Variacao` | 1800 | 2 | REC_FIN_RET. |
| `Mov_Credito_Fiscal` | `ID_Empresa` | 1100, 1500 | 1 | O crédito manual não tem nota; sem isto não há titular. |
| `Mov_Credito_Fiscal` | `Competencia_Apuracao` | 1100, 1500, M100, F800 | 1 | PER_APU_CRED: competência da operação que gerou o crédito, não a da liquidação (Q-F-3 e Q-1-2). |
| `Mov_Credito_Fiscal` | `ID_Tipo_Credito` | 1100, 1500, M100 | 1 | Tabela 4.3.6; obrigatório quando o imposto é PIS ou Cofins. |
| `Mov_Credito_Fiscal` | Origem (3 valores novos) | F150, F800, F205 | 1 | Hoje {apuracao_automatica, cadastro_manual}; o último valor pertence à onda 2. |
| `Mov_Credito_Fiscal` | `Origem_Credito_Efd` | 1100, 1500, M100 | 1 | IND_CRED_ORI. |
| `Mov_Credito_Fiscal` | `ID_Origem_Evento` | F150, F800, F205 | 1 | Aponta o estoque de abertura, o evento de sucessão ou o crédito por unidade. |
| `Mov_Credito_Fiscal` | `ID_Participante_Cedente` | 1100, 1500 | 1 | CNPJ_SUC; só com Origem_Credito_Efd = sucessao. |
| `Mov_Credito_Fiscal` | `ID_Ato_Societario_Sucessao` | 1100, 1500 | 1 | Cisão, fusão ou incorporação que transferiu o crédito. |
| `Mov_Credito_Fiscal` | `Competencia_Escrituracao` | 1101, 1501 | 1 | Só para importar histórico de crédito extemporâneo (D-N87). |
| `Mov_Credito_Fiscal_Aplicacao` | `ID_Credito_Apurado` | M100, M500 | 1 | Liga o consumo à linha que decidiu o desconto. |
| `Mov_Credito_Fiscal_Aplicacao` | `Forma_Utilizacao` | 1100, 1500 | 1 | Hoje só se distingue a compensação (ID_Perdcomp). |
| `Mov_Credito_Fiscal_Aplicacao` | `ID_Participante_Sucessora` | 1100, 1500 | 1 | Só com transferencia_sucessao. |
| `Mov_Titulo_Retencao` | `ID_Natureza_Retencao_Efd` | F600, 1300, 1700 | 1 | IND_NAT_RET. |
| `Mov_Titulo_Retencao` | `Valor_Retido_Pis_Pasep` | F600 | 1 | Quando a retenção é agregada (código 5952). |
| `Mov_Titulo_Retencao` | `Valor_Retido_Cofins` | F600 | 1 | Idem. |
| Cad_Retencao_Federal_Parametro (doc 37) | `ID_Natureza_Retencao_Efd` | F600 | 1 | Entidade só proposta no doc 37. |
| `Mov_Mit_Debito` | Origem_Tipo (valor apuracao_pis_cofins) | M205, M605 | 1 | O débito nasce da apuração consolidada. |

# 8. Domínios novos e ampliados

**19 domínios novos** em `Cad_Classe_Sistema` (sem tabela nova, no padrão do D-N74):

| Domínio | Valores | Registros | Onda |
|---|---|---|---|
| `natureza_pj_efd_contribuicoes` | 00 geral; 01 cooperativa; 02 entidade do Pasep só sobre a folha | 0000 | 1 |
| `indicador_atividade_efd_contribuicoes` | 0 industrial ou equiparado; 1 prestador de serviços; 2 comércio; 3 PJ dos §§ 6º, 8º e 9º do art. 3º da Lei 9.718/1998; 4 imobiliária; 9 outros | 0000 | 1 |
| `origem_processo_efd` | 1 Justiça Federal; 3 Receita Federal; 9 outros | x111 | 1 |
| `indicador_pagamento_documento` | 0 à vista; 1 a prazo; 2 outros | C100 | 1 |
| `grupo_documento_opcao_efd` | nfe_vendas; nfce_vendas; nfe_aquisicoes; nota_consumidor_02; ecf; cfe_sat | C010 | 1 |
| `tipo_equipamento_fiscal` | ecf; sat_cfe; mfe; terminal_nfce | C400, C800 | 1 |
| `natureza_frete_efd` | 0 a 5 e 9, conforme a Tabela do D101 | D101, D105 | 1 |
| `tipo_receita_comunicacao_efd` | 0 a 9 do D600 | D600 | 1 |
| `regra_valor_conta_receita_deducao_efd` | creditos_menos_debitos; debitos_menos_creditos; soma_creditos; soma_debitos | I100 a I300 | 2 |
| `natureza_operacao_fiscal_diversa` | receita_financeira, JCP, aluguel, receita não operacional e outras | F100 | 1 |
| `genero_bem_ativo_efd` | 01 a 06 e 99 | F120 | 1 |
| `utilizacao_bem_ativo_efd` | 1 produção; 2 serviços; 3 locação; 9 outros | F120 | 1 |
| `parcelamento_credito_ativo_efd` | 1 integral; 2 12 meses; 3 24 meses; 4 48 meses; 5 6 meses; 9 outra | F120 | 1 |
| `natureza_retencao_pis_cofins` | 01 a 05, 99 e 51 a 55, 59 do 1300 e do F600 | F600, 1300 | 1 |
| `indicador_composicao_receita_recebida` | 01 clientes; 02 administradora de cartão; 03 título; 04 documento fiscal; 05 item; 99 outros | F525 | 1 |
| `tipo_unidade_imobiliaria_efd` | 01 a 05 e 99 | F205 | 2 |
| `tipo_sociedade_cooperativa` | 01 a 07 | M211 | 1 |
| `natureza_credito_diferido` | 01 alíquota básica; 02 diferenciada; 03 por unidade; 04 crédito presumido da agroindústria | M230 | 1 |
| `orgao_processo_administrativo` | rfb; drj; carf; outro | 1020, 1809 | 1 |

**Ampliações de domínio existente ou proposto:**

| Domínio | Acréscimo |
|---|---|
| `tipo_declaracao_importacao` | + dsi (doc 33 tem di e duimp) |
| `modelo_documento_fiscal` | + 98 (NFS-e municipal) e 99 (outros documentos), só para F500, F550 e 1900 |
| `area_negocio_regra` | + classificacao_receita_efd_contribuicoes |
| `campo_criterio_regra` | + cst_pis_cofins, conta_contabil, contribuicao_social |
| `Cad_Motor_Regra_Resultado.Tipo_Resultado` | + classe_receita_efd, compoe_receita_bruta |

Os domínios `natureza_acao_judicial_efd`, `natureza_processo_administrativo_efd`, `motivo_dispensa_entrega_efd`, `indicador_atividade_receita_deducao` e `tipo_detalhamento_cprb` (antes `tipo_detalhamento_ajuste_pis_cofins`) já constam do documento 43 e só ganham as descrições e as correções da seção 10.

# 9. Regras de geração, fechamento e retificação

**Ciclo de vida.** O período nasce `calculado`, passa a `congelado` quando o arquivo é gerado e assinado, e vira `substituido` quando uma retificadora o substitui. Fechado, nada muda: nem o 0111, o 0145 e o 0900, nem as linhas do Bloco M. A retificadora de período fechado reproduz o valor original e só altera o que a retificação mudou.

**Integridade do Bloco M** (regras de fechamento, não de digitação): a soma dos ajustes é igual ao total do registro pai; a soma de M105 é igual ao campo de base de M100; a soma dos débitos é igual ao total a recolher; o saldo transportado é igual aos créditos menos as aplicações. A mesma estrutura de PIS e Cofins permite escrever cada regra uma vez.

**Crédito.** O crédito de PIS e Cofins segue a competência da aquisição (campo `Competencia_Apuracao`), e não a data da liquidação que dispara `Mov_Credito_Fiscal` hoje. Para PIS e Cofins o crédito deve nascer na competência da operação; a regra de nascimento na liquidação continua valendo para CBS e IBS. Isto precisa da confirmação do contador (Q-F-3, Q-1-2).

**Classificação da receita.** A classe usada no 0111 e no 0900 (tributada, não tributada, exportação, cumulativa; receita bruta ou não) sai do Motor de Regras (`Cad_Motor_Regra_Resultado`), é gravada no item na apuração e fica imutável após o fechamento. Não há tabela nova. O Guia dá os conceitos e não uma tabela; exportação indireta e serviço com ingresso de divisas dependem de CFOP e de dado de comércio exterior (Q-0A9-1).

**Contribuições e créditos extemporâneos.** Não são gerados (D-N87). Quem precisar do histórico importa pelo mapeamento: `Competencia_Escrituracao` marca o crédito extemporâneo e o DARF (multa, juros e data) já está em `Mov_Dctfweb_Darf`.

**Exclusão do ICMS da base.** Não é ajuste: é a `Base_Calculo_Efetiva` de cada item, regra do Motor com vigência, condicionada por empresa ao processo e ligada a `Mov_Processo_Efeito_Tributario` (Q-1-11). O Bloco 1 só registra o efeito.

**SCP.** Cada SCP gera uma escrituração separada, assinada com o certificado da sócia ostensiva; por isso `ID_Entidade_Ligada` está nas notas, na apuração e no arquivo, e a identidade do período inclui a SCP.

**Fim da EFD-Contribuições.** As fontes divergem (documento 10: extinção em 2027; documento 32, com fonte secundária: a EFD vale até 31/12/2026 e depois só para retificação e controle de créditos; dicionário: fim esperado por volta de 2033). Não inventei data. O desenho serve aos dois cenários, porque a estrutura sobrevive para retificar períodos dentro dos 5 anos (Q-M-1, P43-11). O registro 0208 (bebidas frias, extinto em 05/2015) não é gerado.

# 10. As tabelas do Portal contra o documento 43

O mapeamento arquivo para tabela do Guia, que o documento 43 deduzia pelo conteúdo, está **fechado para os 75 arquivos que têm número** (P43-01); restam sem número 11 (ANP, BENEFICIOS_FISCAIS, CFOP_DEVOLUCAO, CFOP_DEVOLUCAO_VENDA, CFOP_RECEITA, CONSUMO_TELECOM, DATA_LIMITE_ENTREGA, IND_DED_DIV, MENSAGENS_USUARIO, PRAZO_DECADENCIA e TIPO_CT). Das 21 tabelas do Portal comparadas com os arquivos, 5 são iguais, 5 equivalentes, 7 equivalentes com diferenças, 1 é subconjunto mais antigo e **3 estão à frente dos arquivos**:

| Tabela | Versão do Portal | O que traz a mais |
|---|---|---|
| 4.3.11 (produtos por unidade de medida, CST 03 e 04) | 1.34, 16/09/2026 | Gasolina, querosene, biodiesel e etanol de 2026 (janelas de alíquota reduzida) |
| 4.3.13 (alíquota zero, CST 06) | 1.36, 16/09/2026 | Código 226 (etanol combustível, 10/09 a 09/10/2026) e prorrogação do biodiesel 220/229 até 31/07/2026 |
| 4.3.16 (suspensão, CST 09) | 1.19, 17/09/2026 | Código 322 (REDATA, desde 15/09/2026, art. 11-C da Lei 11.196/2005 pela Lei 15.504/2026) |

As 20 correções ao documento 43, com as linhas afetadas, estão na revisão 2 dele. As que mudam entidade proposta: `Cad_Natureza_Receita_Pis_Cofins_Aliquota` (`Perfil_Aliquota` passa a {unico, contribuicao, credito}, mais `Tabela_Guia` e `Nota_Aplicacao`; PROD_ST 401 a 409 são só remissão), `Cad_Natureza_Receita_Pis_Cofins` (bebidas frias: código de 3 dígitos mais grupo de 3 dígitos, `Grupo_Pauta`), `Cad_CFOP_Uso_Efd_Contribuicoes` (o efeito da devolução de venda depende do regime), `Cad_Ajuste_Base_Pis_Cofins` (`COD_DETALHAM` sai; `OBRIGA_DET` sem definição), `Cad_Receita_Deducao_Pis_Cofins` (`IND_AJUSTE`, `TIPO_DEDUC`, `Codigo_Atual` do grupo 700 para o 100), `Cad_Tabela_Oficial` e `Mov_Carga_Tabela_Oficial` (número e versão do Guia, `Origem_Material`), `Cad_Obrigacao_Leiaute_Versao` (o 101 não é versão do leiaute: o Guia traz 1.00, 1.01, 2.00, 2.01A, 3.0.0, 3.1.0 e 3.2.0), `Cad_Cprb_Atividade` (318 códigos de 4 dígitos completados com zeros).

**Resolvido e ainda aberto.** P43-02 fica reduzido a `OBRIGA_DET`, à expansão literal das letras P/R, P/N e S/N (só por inferência) e à confirmação do contador. P43-05 e P43-14 não mudam (o material novo não os trata). P43-08 muda: o óleo diesel por unidade (4.3.11, código 102) também acaba em 31/05/2026 na tabela oficial de 16/09/2026; a lacuna é da fonte, não do arquivo.

**Correlação DACON × EFD.** As linhas 01 a 13 dos créditos do DACON têm a mesma numeração e os mesmos nomes de `NAT_BC_CRE`; a migração de histórico pode usar o número da linha como natureza (conferindo pelo nome). Linha 14 é M105, 15 é M100 e 22 e 23 são M110/M510. Nas receitas, o vínculo com as tabelas 4.3.10 a 4.3.17 não está escrito na planilha (é inferência). Como o DACON foi extinto, não há entidade nova.

# 11. Os outros materiais enviados

Chegaram junto o MOC da NFCom (Anexo I e Visão Geral, v1.00a), o Anexo I do MDF-e v3.00b (duplicado de um que já estava aqui; removi a cópia) e os schemas da NFS-e nacional (pacote de 27/07/2026). Eles revisam os documentos 40 e 41 e foram registrados nas revisões 2 deles:

- **NFCom (documento 40).** O MOC é de 01/2023, anterior a todas as NTs: serve ao leiaute-base (99 das 326 linhas são posteriores a ele). Resolve em parte P40-01, P40-02 e P40-06; não resolve P40-03, P40-04 e P40-05. Traz 152 regras de validação (141 obrigatórias e 11 facultativas por UF), 10 eventos (não três) e um conjunto de 35 parâmetros com vigência. Muda o destino do `cClass`, que vira catálogo próprio (a oitava entidade).
- **NFS-e (documento 41).** O pacote de 27/07/2026 **não traz o leiaute 1.04 da NT 009**: é o 1.01 (Anexo I de 09/02/2026) com CNPJ alfanumérico e correções de padrão. Nenhuma das 15 dúvidas (Q-1 a Q-15) se resolve por ele; as 9 entidades do desenho não caem. Há 7 itens (10 campos) do XSD vigente sem lugar no desenho 1.04 e 6 correções ao texto do documento 41.

# 12. Dúvidas e dependências

Os seis blocos levantaram **83 dúvidas** e a revisão das tabelas, mais 17; todas estão na aba "Dúvidas" do anexo, com o tratamento provisório adotado. As que decidem desenho:

| Nº | Dúvida | Tratamento provisório |
|---|---|---|
| Q-0A9-1 | Como classificar cada linha de receita em tributada, não tributada, exportação ou cumulativa, e quais receitas não são receita bruta? O Guia dá os conceitos, mas não uma tabela. Exportação indireta (venda a comercial exportadora) e serviço com ingresso de divisas dependem de CFOP e do dado de comércio exterior. | Regras no Motor de Regras (CST, CFOP, conta, contribuição apurada), com vigência, gravadas em Classe_Receita_Efd e Compoe_Receita_Bruta; carga inicial provisória até o contador validar (mecanismo de validação do Bloco 3). |
| Q-0A9-2 | O 0145 diz que a receita bruta é 'sem o ajuste a valor presente' (campos 3 a 5) e a observação final manda 'considerar os valores destacados a título de AVP'. O 0111 manda incluir o AVP. Qual vale no 0145? | Guardar os dois valores no retrato mensal; gerar o 0145 sem AVP e o 0111 com AVP, e registrar a escolha para o contador confirmar. |
| Q-0A9-3 | IND_REG_CUM: no lucro presumido, a opção por caixa ou competência vale o ano todo? Qual a relação com o regime do IRPJ? O roteiro de 2013 só traz as opções 1 (F500) e 2 (F550); o valor 9 (detalhada, Blocos A, C, D e F) é do Guia de 2021. | Campo no perfil fiscal com vigência, sem bloqueio automático de troca; derivar o padrão da opção de caixa do IRPJ presumido quando existir; o contador confirma. |
| Q-C-1 | Chave_Acesso é obrigatória nas notas, mas os modelos 01, 1B, 04, 02, 2D, 2E, 06, 28 e 29 não têm chave. Entrada e saída aceitam esses modelos? | Tornar Chave_Acesso condicional ao modelo (parâmetro por modelo em Cad_Classe_Sistema) e exportar 44 posições. |
| Q-C-2 | A Mlegate ou seus clientes escrituram NF-e/NFC-e e ECF de forma consolidada (C180, C190, C490) ou individualizada? A opção muda por filial e por período? | Parâmetro com vigência por filial e grupo de documento; padrão individualizada; consolidados gerados por agrupamento. |
| Q-C-9 | Algum cliente do ERP usa ECF, SAT-CF-e ou MFE? ECF foi descontinuado e o SAT está em retirada em várias UFs. | Modelar as três entidades (Cad_Equipamento_Fiscal, Mov_Ecf_Reducao_Z, Mov_Ecf_Reducao_Z_Tributo) sem tela nem geração, no mesmo padrão da decisão D-N79 do doc 43; serve à retificação de períodos antigos. **Resposta de 11/10/2026: sim, há cliente.** Aplicado pela D-N93: as três entidades estão no dicionário (revisão 3), na onda 1. |
| Q-DIP-3 | A NFCom (modelo 62) substitui os modelos 21 e 22 e não consta do Guia 1.35 nos D500 e D600. O Guia atual aceita 62 nesses registros e com que regras? | Gerar o 62 como o 21/22 (tabela 4.1.1 do doc 43, versão 7). A conferir com versão atual do Guia. |
| Q-DIP-13 | O desenho do R-2060 (Mov_Reinf_Cprb_Apuracao) não guarda a receita bruta total do estabelecimento (vlrRecBrutaTotal), que o P100 também pede. Aceita a entidade nova Mov_Cprb_Estabelecimento_Periodo? | Entidade nova; corrigir o doc 10 quando o Reinf for revisado. |
| Q-DIP-18 | Correspondência entre os 11 códigos de ajuste do Reinf e os códigos da Tabela 4.3.8 (07, 08, 09 e outros) para o P210. | Sugerir 07, 08 e 09 onde há equivalente e 05 (outras situações) nos demais; contador confirma. |
| Q-F-2 | Regime de caixa (F500/F525): como ratear a baixa entre itens e tributos da nota quando o título tem juros, multa, desconto, adiantamento (Mov_Credito) anterior à nota ou devolução depois do recebimento? Juros recebidos são receita financeira (F100) ou parte da base? | Ratear Valor_Baixado (sem juros e multa) na proporção do valor dos itens; juros e multa vão para F100 como receita financeira; adiantamento reconhecido no recebimento, sem repetir na nota. |
| Q-F-3 | Mov_Credito_Fiscal nasce na liquidação financeira (doc. 10, rev. 3) e vale também para PIS/Cofins. A EFD-Contribuições apropria o crédito na competência da aquisição (nota, depreciação, 1/12 do estoque), não no pagamento. Os dois modelos coexistem? | Competencia_Credito (campo novo) guarda a competência do fato gerador do crédito; a liquidação continua controlando saldo e aplicação. |
| Q-F-4 | Mov_Operacao_Imobiliaria exige ID_Regime_Geral_Imobiliario (IBS/CBS) e o custo está por empreendimento, não por unidade. Como registrar vendas anteriores a 2027 (PIS/Cofins, inclusive para retificação) e qual o critério de rateio do custo à unidade (área, valor, fração ideal)? | Tornar o regime opcional para fato gerador anterior ao início de IBS/CBS; ratear por Cad_Imovel.Area_M2 até o contador definir. |
| Q-F-5 | A retenção agregada (código 5952, CSLL+Cofins+PIS) é guardada num só Valor_Retido. O F600 pede PIS e Cofins separados: dividir pelos percentuais do código ou exigir a separação na baixa? | Campos novos Valor_Retido_Pis_Pasep e Valor_Retido_Cofins; preencher pela proporção 0,65/3,00 quando agregado, com revisão manual. |
| Q-M-1 | Futuro do Bloco M. Os documentos 10, 32 e 43 divergem sobre o fim da EFD-Contribuições como escrituração de apuração (31/12/2026, 2027 ou 2033) e nenhuma data é oficial (P43-11). A apuração por contribuição precisa continuar viva para retificar períodos na decadência. | As entidades são de movimento e valem para qualquer período fechado; a geração do arquivo fica atrás de Cad_Obrigacao_Acessoria (vigência) e a retificação atrás de Cad_Obrigacao_Decadencia. Nada é desligado por data fixa. |
| Q-M-2 | Rateio e tipo de crédito do item. Mov_Apuracao_Tributo_Item tem um só ID_Tipo_Credito, mas os CST 53 a 56 e 63 a 66 geram até três M100 (grupos 100, 200 e 300) a partir do mesmo item. A apropriação direta exige dados de custeio por tipo de receita. | O item guarda o tipo do grupo do CST; a divisão por tipo fica em Mov_Apuracao_Pis_Cofins_Credito_Base (Percentual_Rateio e Origem_Rateio). Na apropriação direta o contador informa a parcela. Contador valida; |
| Q-M-3 | Débito do M205/M605 e DCTF. O Guia fala do código da Ficha Débitos da DCTF; o dicionário tem MIT e DCTFWeb, mas não tem a DCTF antiga. Períodos até 12/2024 (a conferir) não têm Mov_Mit_Debito. O Pasep sobre a folha segue por eSocial/DCTFWeb e o M350 não tem registro de a recolher. | Debito.ID_Debito_Mit e ID_Debito_Dctfweb são opcionais; em período anterior ao MIT guarda-se só código e valor. Folha: Regime_Incidencia = folha_salarios, ligado ao débito do eSocial. |
| Q-1-2 | Mov_Credito_Fiscal nasce na liquidação financeira e só é usado com Status=confirmado (doc 10, regra do IBS/CBS). Para PIS/Cofins não cumulativo o crédito segue a competência da operação (Leis 10.637/10.833) e não há plataforma que confirme. A regra vale também para PIS/Cofins? | Para PIS/Cofins, criar o crédito na competência da operação (Competencia_Apuracao) e tratá-lo como confirmado por parâmetro com vigência; o gatilho do IBS/CBS fica só para IBS/CBS. |
| Q-1-4 | Registros extemporâneos (1101, 1102, 1200, 1210, 1220, 1501, 1502, 1600, 1610, 1620) são recusados pelo PVA para PA a partir de 08/2013. Gerar algum deles? | Não gerar; tratar o esquecido por retificação do período (até 5 anos, Cad_Obrigacao_Decadencia, doc 43) e manter só o mapeamento para importar histórico. A conferir com versão atual. |
| Q-1-7 | A retenção agregada (código 5952: PIS, Cofins e CSLL) está em Mov_Titulo_Retencao como uma linha (agregado_csll_cofins_pis). O 1300 e o 1700 precisam de PIS e Cofins separados. | Abrir a linha agregada por tributo pelas alíquotas vigentes (parâmetro) ao gerar o EFD; ou gravar três linhas. Decidir com Alberto. |

**Depende da versão atual do Guia** (o Guia lido é de 06/2021). Pontos que as análises marcaram:

- **Leiaute do arquivo.** O Guia cita o código 002; a tabela oficial lida no documento 43 traz 006, desde 2020. O texto dos registros 1011, 1050 e M210/M215 (leiaute de 2019 em diante) deve ser conferido.
- **Documentos novos.** NFCom 62 nos D500 e D600 (o Guia só cita os modelos 21 e 22) e o cClass de 7 posições contra o COD_CLASS de 4; DUIMP e NF3e (modelo 66); BP-e 63 e CT-e OS 67; fim da ECF e do SAT-CF-e em várias UFs.
- **Cadastro.** CNPJ alfanumérico (julho de 2026) nos campos numéricos de 14 posições; lista de serviços da LC 116 com as LC 157/2016 e 175/2020 no 0200; dispensa de ECD para o lucro presumido no COD_CTA (IN RFB 1.774/2017).
- **Regras fiscais.** Motivos 101 a 103 do 0120 (Perse, desde 05/2024); reoneração gradual da CPRB (Leis 14.784/2023 e 14.973/2024), que muda o sentido prático de COD_INC_TRIB no 0145; códigos de receita 2985 e 2991 (DCTFWeb e MIT); origens 05 e 06 do F700 (o Guia tem cinco); tipos de crédito 199, 299 e 399, encerrados em 03/2023; códigos 10 a 12 de ajuste (2026); lista de IND_NAT_ACAO (o texto do 1010 diz 01 a 09 e 99, a tabela traz 12 a 19).
- **Reforma Tributária.** PIS e Cofins cessam em 2027 e as regras de IBS e CBS no valor do documento (C100.VL_DOC) não estão no Guia; o Bloco M cita a Ficha Débitos da DCTF, hoje substituída pelo MIT e pela DCTFWeb (Q-M-3).

**Material que falta:** a versão atual do Guia Prático da EFD-Contribuições (com as notas e os ADE de leiaute posteriores a 2021) e o Guia da EFD ICMS/IPI para fechar P43-05. Sem eles, nada acima trava a revisão 3: cada ponto está marcado como parâmetro com vigência.

# 13. Decisões para Alberto

A numeração segue a D-N82 e usa D-N83 a D-N92. Nada é consolidado antes da sua resposta; a revisão 3 reúne as decisões D-N52 a D-N93 (a D-N93 trouxe ECF, SAT-CF-e e MFE para a onda 1), DSR e feriado ponte (Folha, revisão 21) e o que já estava aguardando.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N83 | Período único: `Mov_Efd_Contribuicoes_Periodo` é o único dono de versão, status e fechamento (empresa, SCP, competência, versão); o cabeçalho do Bloco M, o P100 e o resto da escrituração guardam só `ID_Periodo`? | **Sim.** Evita três controles de versão e garante que a retificadora, dentro dos 5 anos, reproduza o original. |
| D-N84 | Bloco M com uma estrutura só para PIS e Cofins (`ID_Imposto`), em 9 entidades, com o 1050 como agrupamento dos ajustes de base e a parcela por CST em `Mov_Apuracao_Pis_Cofins_Ajuste_Cst`? As duas entidades de ajuste do Bloco 1 caem. | **Sim.** Metade das tabelas, regras de fechamento escritas uma vez, e a mesma estrutura serve para retificar períodos antigos depois de 2027. |
| D-N85 | Processo referenciado numa entidade genérica (`Mov_Apuracao_Processo_Referenciado`) mais `Mov_Processo_Efeito_Tributario` para 1010, 1011, 1020 e 1809, sem `ID_Processo` nos itens? | **Sim.** O registro do Guia se repete por documento e o item pode ter mais de um processo; o Jurídico já tem processo, juízo e suspensão. |
| D-N86 | `Mov_Credito_Fiscal` ganha 8 campos e três valores de origem (seção 7), e o crédito de PIS e Cofins nasce na competência da operação, não na liquidação (a regra da liquidação segue para CBS e IBS)? | **Sim**, com confirmação do contador antes da carga (Q-F-3, Q-1-2). Sem isso, o PER_APU_CRED do 1100 e o M100 não fecham. |
| D-N87 | Não gerar os registros extemporâneos (1101, 1102, 1200, 1210, 1220, 1501, 1502, 1600, 1610 e 1620); corrigir período anterior por retificação, e usar o mapeamento só para importar histórico? | **Sim.** O PVA os recusa a partir de 08/2013 (IN RFB 1.387/2013). Menos código e menos risco de dupla contagem. |
| D-N88 | A classe da receita (0111 e 0900) vem do Motor de Regras e é gravada na apuração; o critério de escrituração e o método de apropriação do crédito ficam no perfil fiscal, com vigência? | **Sim.** O Guia não dá tabela; o Motor já decide por CST, conta e contribuição, e a gravação congela o valor no fechamento. |
| D-N89 | Onda 2: as 9 entidades de nicho (esta redação; as três do varejo legado subiram para a onda 1 pela D-N93, restando 6) (ECF e SAT-CF-e, Bloco I, comunicação sem nota, cooperativa no F600, crédito imobiliário por unidade e sucessão) ficam desenhadas no documento 44 e fora da revisão 3, até haver cliente? | **Sim**, como no D-N61 (condomínios) e no D-N68 (CT-e). **Atualização de 11/10/2026:** a Q-C-9 foi respondida "sim, há cliente" que usa ECF, SAT ou MFE; as três entidades de varejo legado entraram na revisão 3 pela D-N93 (aplicada; onda 1) e as outras seis seguem fora, na onda 2. Q-F-4 (imobiliário depende do IBS/CBS) reforça. |
| D-N90 | Tabelas do Portal: aceitar as 20 correções do documento 43 e carregar manualmente as três tabelas à frente dos arquivos (4.3.11 v1.34, 4.3.13 v1.36, 4.3.16 v1.19), com `Origem_Material` e a versão do Guia? | **Sim.** São correções de significado (P/R, COD_DETALHAM, remissão da 4.3.12) e dados novos de 09/2026; a rotina D-N80 passa a comparar também a versão do título do .doc ou .xls. |
| D-N91 | NFCom (documento 40): `cClass` vira catálogo próprio (oitava entidade), o D-N70 ganha UF e marca de regra facultativa, e, onde o MOC v1.00a divergir do schema, vale o schema? | **Sim.** O MOC é de 01/2023, anterior às NTs; 99 das 326 linhas não existem nele. Sem UF e marca facultativa, as regras G56, G110 e G138 não cabem. |
| D-N92 | NFS-e (documento 41): tratar o pacote de 27/07/2026 como leiaute 1.01 com CNPJ alfanumérico; validar XML pelo XSD 1.01 (D-N65); marcar os campos do 1.04 como "sem XSD publicado"; `Cad_Dfe_Leiaute` separa versão do XML, do XSD e do Anexo VI (D-N64)? | **Sim.** O ZIP não traz o 1.04 e nenhuma das 15 dúvidas do documento 41 se resolve por ele; manter os campos do 1.04 no desenho evita retrabalho quando o XSD sair. |
| D-N94 | Escrituração em dois níveis: `Mov_Efd_Contribuicoes_Periodo` guarda o retrato e o fechamento do período e `Mov_Escrituracao_Arquivo` (documento 33) guarda o arquivo gerado, o recibo e a versão do arquivo, ligado ao período (um período, vários arquivos); completa a D-N83? | **Sim** (Alberto, 11/10/2026). |

**Posso consolidar?**

# 14. Conferência

Um script conferiu que (a) a soma das classes de campo por bloco fecha com o total de campos de cada bloco (203 registros e 1.712 campos); (b) nenhum nome de entidade nova existe no `model.json` e nenhum repete nome de outra proposta; (c) toda entidade citada nos campos novos consta do `model.json` ou de uma proposta dos documentos 33 a 43; (d) as contagens do resumo (35 entidades, 26 na onda 1 e 9 na onda 2; 62 linhas de campo novo; 19 domínios) vêm das listas, não de digitação. O Guia e as tabelas foram lidos pelo texto extraído; as 36 tabelas do Portal foram abertas uma a uma e comparadas por linha do tempo (código, início, fim e alíquota) com os arquivos do documento 43.
