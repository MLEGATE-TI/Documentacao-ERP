# Desenho do B3: compras governamentais e Zona Franca de Manaus e áreas de livre comércio — Documento 158

*Quarto dos seis desenhos que você liberou com o reenvio da LC 214, da LC 227 e do Decreto 12.955 (Q161-4), na ordem que você escolheu (156, 157, 150, 158, 159 e 160). Responde à fila do B3 do documento 94. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar". Você enviou o MCASP (11ª edição) para ajudar; a seção 3.2 diz o que ele muda e o que não muda.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O B3 do documento 94 reunia dez nomes: o redutor e a regra das compras governamentais e, para a Zona Franca de Manaus (ZFM) e as áreas de livre comércio (ALC), a regra, o produto, o cronograma, a área e seus municípios, o internamento, a importação com suspensão e as ocorrências da Suframa, mais o saldo e a expiração do crédito presumido. Antes de desenhar, conferi o que o dicionário já tem. **Já existem** o grupo de compra governamental na nota (`Mov_Nota_Fiscal_Saida_Compra_Governamental`), o número do processo Suframa por item, o código de tipo de crédito presumido da ZFM, o crédito por item (`Mov_Credito_Presumido_Zfm`), o calendário de transição, as inscrições (inclusive a da Suframa em `Cad_Participante_Inscricao`), a habilitação em regime especial e as quatro hipóteses de acréscimo da ZFM e das ALC (doc. 157, nº 25 a 28). Por isso o documento desenha **só o que falta**.

O desenho acrescenta **10 entidades novas (155 campos)** e altera **5 existentes**, com **9 campos novos**, mais **20 valores de domínio** em `Cad_Classe_Sistema` (seção 6). Tudo na Contabilidade & Fiscal.

| Parte | O que a lei diz | O que o dicionário já tinha | O que este documento acrescenta |
|---|---|---|---|
| **Compras governamentais** (LC, arts. 370 a 372 e 472 a 473; Decreto, arts. 439 a 443 e 601) | O produto da CBS e do IBS vai ao ente contratante: as alíquotas dos outros entes vão a zero e a do ente comprador sobe à soma; o redutor do Senado reduz as alíquotas; há janelas de transição de 2026 a 2033 | O grupo na nota (tipo de ente, redutor, tipo de operação) e o fato gerador no pagamento (doc. 157) | `Cad_Regra_Compra_Governamental` (42 linhas: 6 tipos de ente em 7 janelas), duas marcas na nota (presencial e dispensa de licitação), o redutor como parâmetro do calendário |
| **ZFM e ALC: cadastro** (LC, arts. 440, 442, 458 a 460; Decreto, arts. 433 a 437) | Habilitação por inscrição na Suframa (comércio e serviços) ou com projeto técnico-econômico aprovado (indústria); sete áreas | Inscrição Suframa no cadastro do participante; habilitação em regime especial | `Cad_Area_Incentivada` (7) e seus municípios (12), `Cad_Habilitacao_Suframa`, `Cad_Habilitacao_Suframa_Produto`, `Mov_Habilitacao_Suframa_Ocorrencia` |
| **ZFM e ALC: benefícios** (LC, arts. 443 a 455 e 461 a 468; Decreto, arts. 528 a 542) | Alíquota zero na venda para a área, suspensão na importação, créditos presumidos de IBS e de CBS, IBS de 70% na entrada, fator de transição de 2029 a 2032 | Crédito por item e a série do fator no calendário | `Cad_Zfm_Alc_Regra` (23 linhas), `Mov_Zfm_Credito_Ibs_Periodo` e a extensão do crédito por item para aquisição e importação |
| **ZFM e ALC: controle** (Decreto, arts. 543 a 550) | Internamento em 120 dias (210 com prorrogação), evento da Suframa, desembaraço no destino; suspensão de 48 meses na importação, com conversão em isenção | Hipóteses de acréscimo 25 a 28 | `Mov_Zfm_Alc_Internamento` e `Mov_Zfm_Alc_Importacao_Suspensao` |

**Oito achados que você precisa ler.**

1. **A numeração do Decreto não é a da LC, e o Decreto só trata da CBS.** Compras: LC, arts. 472 e 473 = Decreto, arts. 442 e 439. ZFM: LC, arts. 443 a 452 = Decreto, arts. 528 a 533. ALC: LC, arts. 461 a 468 = Decreto, arts. 536 a 540. Tudo o que é IBS (a alíquota zero do IBS, os créditos de IBS, a incidência de 70%) está **só na LC**: o regulamento do IBS, do Comitê Gestor, não está no Project. Cito sempre os dois e marco `so_lc` onde só a LC fala.
2. **O fator de transição do art. 474 da LC vale só para três créditos** (os dos arts. 447, 449 e 465, de 7,5% e 13,5%), e não para os créditos da produção (arts. 450 e 467). O dicionário ligava `percentual_credito_zfm` (100% até 2028; 90%, 80%, 70% e 60% de 2029 a 2032; 100% em 2033) ao crédito da produção, `Mov_Credito_Presumido_Zfm`. Isso reduziria por engano o crédito da indústria incentivada. Corrijo o texto e passo o fator para os créditos de aquisição (seção 5.5).
3. **O dicionário não tinha o crédito de aquisição nem o de importação para revenda.** `Mov_Credito_Presumido_Zfm` nasce de uma nota de **saída** de estabelecimento aprovado. Os créditos dos arts. 444, 447, 449, 462 e 465 nascem na **entrada** do adquirente habilitado. Estendo a entidade com a origem do crédito e o item de entrada, e ligo cada crédito a `Mov_Credito_Fiscal`, que já guarda a data de apropriação e o último dia de uso (os cinco anos dos arts. 452 e 468, parágrafo único). É o "saldo e expiração" que o documento 94 pedia.
4. **O crédito de IBS da produção (LC, art. 450, §§ 1º e 6º) não é por nota.** O percentual (55%, 75%, 90,25% ou 100%) incide sobre o **saldo devedor do IBS do período**, por grupo de percentual, e a LC 227 acrescentou a transferência de até três dias úteis para o saldo a recuperar. Um valor por item de nota estaria errado. Criei `Mov_Zfm_Credito_Ibs_Periodo` (por empresa, competência e percentual) e deixei o valor por item só para a CBS. O IBS depende do Comitê Gestor, e todo esse desenho é provisório (Q158-9).
5. **A CBS das compras governamentais não segue a mesma janela do IBS.** A LC (art. 372) manda o regime de destinação ao ente comprador valer para o **IBS desde 2027** e para a **CBS só em proporções de 10%, 20%, 30% e 40% de 2029 a 2032, e por inteiro a partir de 2033** (de 2027 a 2028 a CBS fica fora). O Decreto (art. 441, §§ 1º e 2º) repete as janelas, mas só para Estados e Municípios; a LC não distingue o ente. A carga segue a LC para todos os entes e pergunto ao contador (Q158-C1). Com a CBS parcial, a soma que sobe para o ente comprador precisa de uma leitura minha (Q158-C2; exemplo na seção 3.4).
6. **O redutor das compras governamentais não tinha onde morar.** O documento 94 previa `Cad_Redutor_Compra_Governamental`, mas o redutor é um número por ano fixado por **resolução do Senado** no ano anterior (Decreto, art. 601, § 1º): cabe no calendário de transição, que já guarda séries anuais com vigência. Não criei tabela. **A carga fica sem valor**: a Resolução ainda não consta dos documentos que tenho, e uma proposta do TCU (44,16% para 2027, com CBS de 11,3%) só chegou por fonte secundária e depende do Senado. O Motor avisa quando falta (Q158-2).
7. **O texto do grupo da nota cita o artigo errado.** `Percentual_Redutor` diz "art. 473 da LC 214", mas o redutor é do **art. 472**; o art. 473 é a destinação do produto. É correção de texto, sem campo novo.
8. **O MCASP não muda o desenho.** A 11ª edição (e as portarias que a aprovam) trata do lado do ente comprador (empenho, liquidação, pagamento e a contabilidade patrimonial); **não há CBS nem IBS nela**. O desenho aqui é do lado do **fornecedor** (quem emite a nota). O lado comprador fica fora até haver cliente ente público (D-N68; Q158-12).

# 2. Regras que segui

Valem as dos documentos 156, 157 e 150 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória com `Situacao_Dado = provisorio` até o contador validar; o ERP avisa e nunca bloqueia; nomes em português com sublinhado; prefixo `Valor_` só em número, referência, texto e enumeração; o que se deriva não se guarda). Mais estas:

1. **Cito sempre "LC, art. X" e "Decreto, art. Y".** Onde só a LC fala, a linha traz `so_lc`.
2. **Mestre só onde outra tabela aponta para a versão aplicada.** Por isso são mestres a regra de compra governamental, a área incentivada e a regra de ZFM e ALC; as demais tabelas de cadastro usam janela de vigência.
3. **O ERP só registra.** O internamento, a suspensão e o crédito não bloqueiam a emissão da nota; o ERP calcula prazos, avisa e guarda o que o Fisco, a Suframa e o usuário informam. O valor oficial do IBS é o do Comitê Gestor.
4. **Guardo o valor calculado só onde uma mudança de vigência reescreveria a história** (prazo do internamento, saldo devedor e crédito do período). O resto sai de cálculo.
5. **Uma leitura minha é sempre dita como minha** e vai ao contador; a carga sai provisória.

# 3. Compras governamentais (LC, arts. 370 a 372 e 472 a 473; Decreto, arts. 439 a 443 e 601)

## 3.1 O que o texto pede

1. **Destinação do produto** (LC, art. 473; Decreto, art. 439). Nas aquisições da administração direta, das autarquias e das fundações, a arrecadação do IBS e da CBS vai por inteiro ao ente contratante. A União zera o IBS dos outros entes e sobe a CBS à soma de IBS e CBS; o Estado zera a CBS e o IBS municipal e sobe o IBS estadual; o Município zera a CBS e o IBS estadual e sobe o IBS municipal; o Distrito Federal zera a CBS e sobe o IBS distrital. Tudo depois do redutor do art. 472.
2. **Exceção** (LC, art. 473, § 2º; Decreto, art. 439, § 2º): não vale para a aquisição que, **ao mesmo tempo**, é presencial e dispensada de licitação.
3. **Consórcio público** (LC, art. 473, § 4º; Decreto, art. 439, § 3º): equipara-se ao município da sede, o documento sai em nome do consórcio e a arrecadação vai aos entes integrantes na proporção do financiamento, que o consórcio informa ao CGIBS. O Comitê Gestor do IBS recebe o mesmo tratamento (LC, art. 473, § 6º; Decreto, art. 439, § 5º).
4. **Importação** do ente, direta ou por conta e ordem, segue o mesmo regime (LC, art. 473, § 3º; Decreto, art. 440).
5. **Fato gerador no pagamento** (Decreto, art. 439, § 6º), já desenhado no documento 157 (`compra_ente_publico`).
6. **Redutor** (LC, art. 472; Decreto, arts. 442, 443 e 601). Desde 01/01/2027 as alíquotas caem de modo uniforme na proporção do redutor fixado por resolução do Senado, no ano anterior, até 2033; de 2034 em diante vale o nível de 2033. Não vale para a compra presencial dispensada de licitação, para a sujeita a alíquota nacionalmente uniforme e para a do Simples Nacional ou do MEI (LC, art. 472, parágrafo único; Decreto, art. 442, § 1º). O edital deve considerar o redutor na formação de preços (Decreto, art. 442, § 2º).
7. **Transição** (LC, art. 372; Decreto, art. 441). Em 2026 o regime não vale. A partir de 2027 vale por inteiro para o IBS. Para a CBS, não vale de 2027 a 2028, vale em 10%, 20%, 30% e 40% de 2029 a 2032 e por inteiro desde 2033.

## 3.2 O que o dicionário já tem

`Mov_Nota_Fiscal_Saida_Compra_Governamental` guarda o tipo de ente, o redutor e o tipo de operação (1 a 4) na nota emitida, na recebida e na NF-e ABI. O documento 157 deu o fato gerador no pagamento. **Falta** a regra por tipo de ente e janela, as duas marcas que ligam e desligam a exceção da compra presencial dispensada, e o lugar do percentual do redutor.

**O MCASP.** A 11ª edição, a síntese das alterações e as portarias (STN/MF 2.016/2024; conjuntas STN/SRPC 25 e STN/SOF 26, com a retificação) tratam do plano de contas aplicado ao setor público, do empenho e do pagamento. Procurei CBS e IBS e não há. O que aproveito: o pagamento é o marco do fato gerador (já adotado) e o ente comprador é a administração direta, autarquia ou fundação. O restante é do lado comprador.

## 3.3 Desenho

1. **Uma regra por tipo de ente e janela** (`Cad_Regra_Compra_Governamental`): se a destinação da CBS e a do IBS valem, a proporção da CBS, qual tributo recebe a soma, quais alíquotas vão a zero, se o redutor vale e as exceções. O tipo é o `Tipo_Ente` que a nota já traz. A linha vigente na **data do pagamento** decide. São 42 linhas: 6 tipos em 7 janelas (Anexo A.1).
2. **Duas marcas na nota** (`Indicador_Aquisicao_Presencial` e `Indicador_Dispensa_Licitacao`), porque a exceção exige as duas. O Motor lê as duas juntas no critério `aquisicao_presencial_dispensada`.
3. **O redutor é um parâmetro do calendário**: `redutor_compras_governamentais`, uma linha por ano, tipo `percentual`, fundamento "Resolução do Senado, LC art. 370, Decreto art. 601". Sem linha para o ano, o Motor avisa. A nota continua guardando o percentual que foi aplicado (`Percentual_Redutor`).
4. **A soma que sobe para o ente comprador** não é guardada: sai do cálculo (alíquotas do dia, redutor e proporção da CBS). O ERP guarda o que a nota carrega.

## 3.4 Exemplo calculado (leitura provisória; números hipotéticos)

Compra de R$ 100.000,00 por um **Estado**, com pagamento em **2029**. Alíquotas hipotéticas, só para o exemplo: CBS 9%, IBS estadual 17%, IBS municipal 8%; redutor hipotético de 40%. Em 2029 a CBS segue o regime em 10% (LC, art. 372, parágrafo único, I).

| Passo | Cálculo | Resultado |
|---|---|---|
| Alíquotas depois do redutor (LC, art. 472) | CBS 9 × 0,6; IBS estadual 17 × 0,6; IBS municipal 8 × 0,6 | CBS 5,4%; IBS estadual 10,2%; IBS municipal 4,8% |
| Parte da CBS que segue o regime | 5,4% × 10% | 0,54% |
| Alíquota estadual do IBS depois do regime (LC, art. 473, § 1º, II) | IBS estadual + IBS municipal (que vai a zero) + parte da CBS | 15,54% |
| CBS que continua com a União | 5,4% − 0,54% | 4,86% |
| Tributo total | 15,54% do IBS estadual + 4,86% de CBS | R$ 20.400,00 |

O total (R$ 20.400,00) é igual ao que se pagaria sem o regime depois do redutor: o regime só **muda o destinatário** do produto. **Leitura minha**: com a CBS em parte, a soma é IBS + a parte da CBS que segue o regime, e o resto da CBS continua CBS (Q158-C2).

## 3.5 Entidade nova: `Cad_Regra_Compra_Governamental`

A regra de destinação do produto da CBS e do IBS por tipo de ente comprador e por janela de vigência (LC 214, arts. 372, 472 e 473; Decreto 12.955, arts. 439 a 443): quais alíquotas vão a zero, qual tributo recebe a soma, a proporção da CBS que segue o regime na transição, se o redutor se aplica e as exceções (compra presencial dispensada de licitação, alíquota uniforme, Simples e MEI). Uma linha por tipo de ente e período; vale a linha vigente na data do fato gerador (o pagamento, art. 439, § 6º). 42 linhas de carga provisória (Anexo A).

*Tipo: parâmetro com vigência (carga provisória). Mestre: sim. Vigência: sim. Campos: 22.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Compra_Governamental` | identificador | --- |
| `ID_Regra_Compra_Governamental_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Regra_Compra_Governamental_Versao). A identidade é única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência (Fase 0, seção 2). |
| `Tipo_Ente` | enumeração {uniao, estados, distrito_federal, municipios, consorcio_publico, comite_gestor_ibs} --- identidade | Mesmos valores do grupo da nota (`Mov_Nota_Fiscal_Saida_Compra_Governamental.Tipo_Ente`). Parte da identidade: uma linha vigente por tipo de ente. |
| `Equiparado_A` | enumeração {municipio_sede, consorcio_publico}, opcional | Consórcio público: a aquisição se equipara à do município da sede (LC, art. 473, § 4º, I; Decreto, art. 439, § 3º, I). Comitê Gestor do IBS: recebe o tratamento do consórcio (LC, art. 473, § 6º; Decreto, art. 439, § 5º). Vazio nos demais tipos. |
| `Aplica_Destinacao_Cbs` | booleano | Se, na janela, o regime de destinação da CBS ao ente contratante se aplica (LC, art. 372; Decreto, art. 441). Falso em 2026 e em 2027 e 2028; verdadeiro de 2029 em diante, na proporção de Percentual_Aplicacao_Cbs. |
| `Percentual_Aplicacao_Cbs` | número, opcional | A proporção da CBS que segue o regime na janela: 10, 20, 30 e 40 de 2029 a 2032 (LC, art. 372, parágrafo único; Decreto, art. 441, § 2º) e 100 a partir de 2033. Vazio quando Aplica_Destinacao_Cbs é falso. |
| `Aplica_Destinacao_Ibs` | booleano | Se a destinação integral do IBS se aplica na janela: falso em 2026 e verdadeiro desde 2027 (LC, art. 372, I, a, e II, a). Fonte só a LC; o regulamento do IBS não está no Project. |
| `Tributo_Que_Recebe_O_Total` | enumeração {cbs, ibs_estadual, ibs_municipal, ibs_distrital}, opcional | O tributo cuja alíquota sobe para a soma das alíquotas da CBS e do IBS, depois do redutor (art. 439, § 1º): CBS na União, IBS estadual no estado, IBS municipal no município, IBS distrital no Distrito Federal. |
| `Zera_Cbs` | booleano | A alíquota da CBS vai a zero, na proporção de Percentual_Aplicacao_Cbs (estado, Distrito Federal e município; LC, art. 473, § 1º, II a IV). |
| `Zera_Ibs_Estadual` | booleano | A alíquota estadual do IBS vai a zero (União e município). |
| `Zera_Ibs_Municipal` | booleano | A alíquota municipal do IBS vai a zero (União e estado). |
| `Afasta_Se_Presencial_E_Dispensada` | booleano | Verdadeiro: o regime não se aplica à aquisição que, cumulativamente, é presencial e dispensada de licitação (LC, arts. 472, parágrafo único, I, e 473, § 2º; Decreto, arts. 439, § 2º, e 442, § 1º, I). O Motor lê as duas marcas do grupo da nota. |
| `Aplica_Redutor` | booleano | Se o redutor se aplica na janela: desde 01/01/2027 (LC, art. 472; Decreto, art. 442). O percentual do ano é parâmetro do calendário (`redutor_compras_governamentais`), fixado por resolução do Senado. |
| `Afasta_Redutor_Se_Aliquota_Uniforme` | booleano | Verdadeiro: o redutor não se aplica a aquisição sujeita a alíquota nacionalmente uniforme (LC, art. 472, parágrafo único, II; Decreto, art. 442, § 1º, II). |
| `Afasta_Redutor_Se_Simples_Mei` | booleano | Verdadeiro: o redutor não se aplica a aquisição sujeita ao Simples Nacional ou ao MEI (LC, art. 472, parágrafo único, III; Decreto, art. 442, § 1º, III). |
| `Alcanca_Importacao` | booleano | Verdadeiro: a importação do ente, direta ou por conta e ordem, segue o mesmo regime (LC, art. 473, § 3º; Decreto, art. 440). |
| `Fundamento_Legal` | texto | Artigos da LC e do Decreto que sustentam a linha. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 3.6 Mudanças em entidades existentes (compras governamentais)

| Entidade | Campo | Mudança |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Compra_Governamental` | `ID_Regra_Compra_Governamental` | **Novo.** Referência (Cad_Regra_Compra_Governamental), opcional: a versão da regra aplicada na data do pagamento. |
| `Mov_Nota_Fiscal_Saida_Compra_Governamental` | `Indicador_Aquisicao_Presencial` | **Novo.** Booleano, opcional. Presencial é uma das duas condições da exceção (LC, art. 473, § 2º). |
| `Mov_Nota_Fiscal_Saida_Compra_Governamental` | `Indicador_Dispensa_Licitacao` | **Novo.** Booleano, opcional. A dispensa de licitação é a outra condição. O ERP só registra; quem informa é o usuário. |
| `Mov_Nota_Fiscal_Saida_Compra_Governamental` | `Percentual_Redutor` | **Texto.** O redutor é do art. 472 da LC e dos arts. 442, 443 e 601 do Decreto; o art. 473 é a destinação do produto. O percentual aplicado vem de `redutor_compras_governamentais` no calendário. |
| `Cad_Calendario_Transicao` | parâmetro `redutor_compras_governamentais` | **Novo valor no domínio `parametro_transicao`.** Tipo `percentual`; `Ano` de 2027 a 2033 (de 2034 em diante vale o de 2033, LC, art. 472, II). **Carga vazia** (Q158-2). |

# 4. Zona Franca de Manaus e áreas de livre comércio: cadastro e catálogo de benefícios (LC, arts. 440 a 470; Decreto, arts. 432 a 442 e 528 a 542)

## 4.1 O que o texto pede

| Benefício | LC | Decreto | Mecanismo |
|---|---|---|---|
| Habilitação | 442 (ZFM), 460 (ALC) | 435, 438 | Inscrição na Suframa; indústria incentivada também com projeto técnico-econômico aprovado |
| Suspensão na importação | 443 (ZFM), 461 (ALC) | 528, 536 | CBS e IBS suspensos; vira isenção em 48 meses (consumo, incorporação, depreciação integral ou permanência no ativo); saída para fora antes da conversão obriga a declarar a CBS com acréscimos |
| Crédito de IBS na importação para revenda | 444, 462 | só LC | 50% da alíquota do IBS na importação, deduzido do IBS devido; recolhe com acréscimos se a revenda falhar |
| Alíquota zero na venda para a área | 445, 463 | 529, 537 | Operação originada fora, com bem industrializado nacional, para habilitado em regime regular ou Simples; inscrição citada no documento; internamento em 120 dias |
| IBS de 70% na entrada | 446, 464 | só LC | IBS cobrado do destinatário, com crédito, quando o bem não vai a indústria incentivada |
| Créditos de aquisição | 447, 449, 465 | só LC | 7,5% (Sul e Sudeste, menos ES) ou 13,5% (demais regiões e ES) do valor da operação; 7,5% no intermediário local; fator de 2029 a 2032 (art. 474) |
| Alíquota zero entre indústrias incentivadas | 448 | 530 | Bem intermediário entregue dentro da ZFM |
| Crédito presumido da produção | 450 (ZFM), 467 (ALC) | 531, 539 | IBS: 55%, 75%, 90,25% ou 100% do saldo devedor do período; CBS: 6% (produtos do art. 454 e ALC) ou 2% (demais, ZFM), sobre o valor da operação |
| Alíquota zero na venda dentro da área | 451, 466 | 532, 538 | CBS zero em venda de bem nacional ou serviço físico a destinatário dentro da área |
| Uso do crédito | 452, 468 | 533, 540 | Compensa só o mesmo tributo, sem ressarcimento; extingue em cinco anos da apropriação |
| Bens fora do regime | 441 | 434 | Armas, fumo, bebidas alcoólicas, automóveis, petróleo e derivados, perfumaria (com exceções) |

## 4.2 O que o dicionário já tem e o que falta

Já existem: `Cad_Participante_Inscricao` (inscrição Suframa), `Cad_Habilitacao_Regime_Especial` (titular, número, situação, vigência), `Numero_Processo_Suframa` na nota, `Codigo_Tipo_Credito_Presumido_Zfm` e `Indicador_Zfmalc` na NFS-e, `Mov_Credito_Presumido_Zfm`, os três eventos de que a Suframa participa (`Papel_Autor` = suframa) e as hipóteses de acréscimo 25 a 28. **Faltam**: o catálogo das áreas e dos municípios; o detalhe da habilitação (área, atividade, projeto e produtos); as ocorrências da Suframa; o catálogo dos benefícios com percentual, base, prazo e fonte; e a lista dos bens fora do regime. Esta seção desenha o cadastro; os movimentos ficam na seção 5.

## 4.3 Desenho

1. **A habilitação continua em `Cad_Habilitacao_Regime_Especial`**, com o valor novo `suframa_zfm_alc` no domínio `tipo_regime_especial_federal`. O detalhe da Suframa entra em extensão 1:1 (`Cad_Habilitacao_Suframa`), porque só a minoria das empresas a tem. A inscrição não se repete: aponta para `Cad_Participante_Inscricao`.
2. **O projeto técnico-econômico aprovado decide o crédito** (LC, art. 450: "nos termos do projeto econômico aprovado"). O produto do projeto, com categoria e marca do art. 454, vive em `Cad_Habilitacao_Suframa_Produto`; o percentual vem de `Cad_Zfm_Alc_Regra`.
3. **O catálogo de benefícios é uma tabela só** (`Cad_Zfm_Alc_Regra`), com um domínio aberto de dez tipos (Anexo A.4). Ela substitui `Cad_Regra_Zfm_Alc_Cbs`, `Cad_Zfm_Alc_Produto_Regra` e `Cad_Cronograma_Transicao_Zfm` do documento 94: a série anual do fator já está no calendário.
4. **Bens fora do regime** (LC, art. 441; Decreto, art. 434): lista legal em `Cad_Lista_Legal_Item`, valor novo `zfm_alc_bens_excluidos` em `tipo_lista_legal`, com a exceção do refino por `Eh_Excecao`. **Carga vazia**: a lista de NCM é do contador (Q158-C9).
5. **A ZFM e as ALC têm regras diferentes onde a lei diz.** Só a ZFM tem a alíquota zero entre indústrias, o crédito do intermediário local e o crédito de IBS da produção; a ALC tem o crédito de CBS da produção só de 6%. A coluna `Tipo_Area` e as 23 linhas de carga (Anexo A.5) dizem isso sem código.

## 4.4 Entidade nova: `Cad_Area_Incentivada`

O catálogo das áreas incentivadas: a Zona Franca de Manaus e as seis áreas de livre comércio (Decreto, arts. 433 e 437; LC, arts. 440 e 459). É mestre porque a habilitação, o internamento e a suspensão da importação apontam para a área. Carga provisória de 7 linhas (Anexo A).

*Tipo: cadastro com vigência (mestre; carga provisória). Mestre: sim. Vigência: sim. Campos: 14.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Area_Incentivada` | identificador | --- |
| `ID_Area_Incentivada_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Area_Incentivada_Versao). |
| `Codigo_Area` | código (até 30) --- identidade | ZFM, ALC-TABATINGA, ALC-GUAJARA-MIRIM, ALC-BOA-VISTA-BONFIM, ALC-MACAPA-SANTANA, ALC-BRASILEIA-EPITACIOLANDIA e ALC-CRUZEIRO-DO-SUL. |
| `Nome` | texto | Nome da área como na lei. |
| `Tipo_Area` | enumeração {zfm, alc} | Decide quais benefícios valem (Cad_Zfm_Alc_Regra.Tipo_Area). |
| `ID_Estado` | referência (Cad_Estado) | O estado da área (cada área de livre comércio fica num só estado). |
| `Norma_Criacao` | texto, opcional | A lei ou o decreto que criou ou regulamentou a área (art. 437). |
| `Data_Fim_Beneficios` | data, opcional | Último dia dos benefícios (art. 92-A do ADCT; Decreto, arts. 432 e 436). A carga traz 31/12/2073, provisório (leitura do documento 10, seção 9). |
| `Fundamento_Legal` | texto | Artigo que lista a área. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 4.5 Entidade nova: `Cad_Area_Incentivada_Municipio`

Os municípios de cada área incentivada, com vigência. A Zona Franca de Manaus compreende parte de Manaus, Rio Preto da Eva e Itacoatiara (art. 433, I); cada área de livre comércio traz os seus. Serve ao Motor para decidir se o endereço do destinatário está dentro da área. Tabela de janela de vigência, sem identidade separada. Carga provisória de 12 linhas.

*Tipo: cadastro com janela de vigência (carga provisória). Mestre: não. Vigência: sim. Campos: 10.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Area_Incentivada_Municipio` | identificador | --- |
| `ID_Area_Incentivada` | referência (Cad_Area_Incentivada) --- identidade | A área. |
| `ID_Municipio` | referência (Cad_Municipio) --- identidade | O município. |
| `Eh_Parcial` | booleano | Verdadeiro quando só parte do município está na área (os três da Zona Franca de Manaus). O endereço dentro da parte demarcada é dado do usuário (Q158-E2). |
| `Fundamento_Legal` | texto, opcional | Artigo ou lei. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 4.6 Entidade nova: `Cad_Habilitacao_Suframa`

O detalhe de Suframa da habilitação (`Cad_Habilitacao_Regime_Especial`, com o novo valor `suframa_zfm_alc` no domínio `tipo_regime_especial_federal`): a área, a atividade habilitada, o número da inscrição específica que a nota do remetente tem de citar (art. 529, § 2º) e o projeto técnico-econômico da indústria incentivada (art. 435, II). A habilitação em si (titular, número, situação) continua no cadastro que já existe. Tabela de janela de vigência. Carga vazia: cadastro do usuário.

*Tipo: extensão 1:1 com janela de vigência (carga vazia). Mestre: não. Vigência: sim. Campos: 13.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Habilitacao_Suframa` | identificador | --- |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) --- identidade | A habilitação de tipo `suframa_zfm_alc`; o titular é o participante habilitado. |
| `ID_Area_Incentivada` | referência (Cad_Area_Incentivada) | A área em que o contribuinte está estabelecido. |
| `Atividade_Habilitada` | enumeração {comercial_servicos, industria_incentivada} | Inciso I (inscrição) ou inciso II (inscrição mais projeto aprovado) do art. 435 e do art. 438. |
| `ID_Participante_Inscricao` | referência (Cad_Participante_Inscricao) | A inscrição específica no cadastro da Suframa (`Tipo_Inscricao` = suframa), que a nota do remetente leva em campo próprio (Decreto, art. 529, § 2º). O número fica no cadastro de inscrições, e não aqui. |
| `Numero_Projeto_Tecnico_Economico` | código (até 30), opcional | O projeto aprovado pelo Conselho de Administração da Suframa. Obrigatório na indústria incentivada. |
| `Data_Aprovacao_Projeto` | data, opcional | Data da aprovação do projeto. |
| `Situacao_Convalidacao` | enumeração {nao_aplicavel, pendente, convalidado} | Projeto aprovado antes da LC: permanece válido para a CBS, desde que o Conselho o convalide nos prazos do ato conjunto da RFB, da Suframa e do CGIBS (art. 435, § 6º, II; art. 438, § 7º, II). |
| `Data_Convalidacao` | data, opcional | Quando o Conselho convalidou. |
| `Fundamento_Legal` | texto, opcional | --- |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 4.7 Entidade nova: `Cad_Habilitacao_Suframa_Produto`

O produto do projeto técnico-econômico aprovado: a NCM, o processo produtivo básico e a categoria que decide o percentual do crédito presumido (art. 531; LC, art. 450). O crédito é "nos termos do projeto aprovado": o percentual depende do produto da habilitação, e não só da NCM. Tabela de janela de vigência. Carga vazia.

*Tipo: cadastro com janela de vigência (carga vazia). Mestre: não. Vigência: sim. Campos: 11.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Habilitacao_Suframa_Produto` | identificador | --- |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) --- identidade | A habilitação da indústria incentivada. |
| `ID_Classificacao_Mercadoria` | referência (Cad_Classificacao_Mercadoria) --- identidade | A NCM do produto no projeto. |
| `Numero_Ppb` | código (até 30), opcional | O processo produtivo básico do produto (art. 435, § 6º, III). |
| `Categoria_Credito_Ibs` | enumeração {bem_consumo_final, bem_capital, bem_intermediario, informatica_ou_estimulo_cem}, opcional | Grupo do art. 450, § 1º, da LC: 55%, 75%, 90,25% e 100% (informática e produtos com crédito estímulo de ICMS de 100% até 2023). O percentual vem de Cad_Zfm_Alc_Regra. |
| `Eh_Produto_Art_454` | booleano | Verdadeiro: crédito presumido da CBS de 6% (produto do art. 454 da LC); falso: 2% (art. 531, § 1º). A lista dos produtos é divulgada pelo Poder Executivo (art. 454, § 3º). |
| `Eh_Sem_Similar_Nacional` | booleano | Verdadeiro: bem sem similar nacional instalado na ZFM, com o tratamento do art. 455 da LC. |
| `Descricao_No_Projeto` | texto, opcional | O produto como o projeto o descreve. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 4.8 Entidade nova: `Mov_Habilitacao_Suframa_Ocorrencia`

As comunicações da Suframa sobre a habilitação (art. 435, § 7º; art. 438, § 8º): bloqueio da inscrição, suspensão do licenciamento de importação, suspensão ou cancelamento dos incentivos de um bem, incentivo auferido indevidamente e descumprimento do processo produtivo básico ou dos compromissos do projeto. O ERP registra e avisa; a situação da habilitação é mudada pelo usuário.

*Tipo: movimento. Mestre: não. Vigência: não. Campos: 11.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Ocorrencia_Suframa` | identificador | --- |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) | A habilitação alcançada. |
| `Tipo_Ocorrencia` | enumeração {bloqueio_inscricao, suspensao_licenciamento_importacao, suspensao_incentivos_bem, cancelamento_incentivos_bem, incentivo_indevido, descumprimento_ppb_ou_compromissos} | Os seis incisos do § 7º do art. 435 (ZFM) e do § 8º do art. 438 (ALC). |
| `Data_Comunicacao` | data | Quando a Suframa comunicou. |
| `Data_Inicio_Efeito` | data | Início do efeito: as administrações suspendem os incentivos (I a III) ou cancelam (IV). |
| `Data_Fim_Efeito` | data, opcional | Fim da suspensão, na regularização. |
| `ID_Classificacao_Mercadoria` | referência (Cad_Classificacao_Mercadoria), opcional | O bem, nas ocorrências de suspensão e cancelamento dos incentivos do bem. |
| `Numero_Comunicado` | código (até 40), opcional | O número do comunicado ou do ato. |
| `ID_Documento` | referência (Cad_Documento), opcional | O arquivo da comunicação. |
| `Situacao_Ocorrencia` | enumeração {vigente, regularizada, cancelada} | --- |
| `Observacao` | texto, opcional | --- |

## 4.9 Entidade nova: `Cad_Zfm_Alc_Regra`

O catálogo dos benefícios da Zona Franca de Manaus e das áreas de livre comércio: uma linha por benefício e, quando o percentual difere, por categoria do produto ou região de origem. Guarda o tributo, a forma, a base e o percentual, os prazos (comprovação do internamento, prorrogação, conversão da suspensão, retorno, expiração do crédito) e se o fator de transição do art. 474 se aplica. Substitui os nomes `Cad_Regra_Zfm_Alc_Cbs`, `Cad_Zfm_Alc_Produto_Regra` e `Cad_Cronograma_Transicao_Zfm` do documento 94. É mestre porque o crédito, o internamento e a suspensão apontam para a linha aplicada. 23 linhas de carga provisória (Anexo A).

*Tipo: parâmetro com vigência (mestre; carga provisória). Mestre: sim. Vigência: sim. Campos: 27.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Zfm_Alc_Regra` | identificador | --- |
| `ID_Zfm_Alc_Regra_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Zfm_Alc_Regra_Versao). |
| `Codigo_Regra` | código (até 40) --- identidade | Por exemplo ZFM-CRED-IBS-PRODUCAO-CONSUMO-FINAL. |
| `ID_Tipo_Beneficio` | referência (Cad_Classe_Sistema, domínio = beneficio_zfm_alc) | Domínio novo, aberto, com 10 valores (Anexo A). |
| `Tipo_Area` | enumeração {zfm, alc} | A área a que a linha se aplica. |
| `Tributo_Alcancado` | enumeração {cbs, ibs, cbs_e_ibs} | Onde a linha vale para os dois, o IBS vem só da LC (Fonte_Normativa). |
| `Forma_Beneficio` | enumeração {suspensao, aliquota_zero, credito_presumido, incidencia_ibs_entrada} | O mecanismo. |
| `Categoria_Produto` | enumeração {bem_consumo_final, bem_capital, bem_intermediario, informatica_ou_estimulo_cem, produto_art_454, demais_produtos}, opcional | Quando o percentual depende do produto. Casa com Cad_Habilitacao_Suframa_Produto. |
| `Regiao_Origem` | enumeração {sul_sudeste_exceto_es, demais_regioes_e_es}, opcional | Origem do bem nos créditos de aquisição (7,5% e 13,5%). |
| `Base_Do_Percentual` | enumeração {valor_operacao, saldo_devedor_ibs_periodo, aliquota_ibs_importacao, aliquota_que_incidiria}, opcional | Sobre o que o percentual incide. |
| `Percentual` | número, opcional | O percentual da lei. Vazio na suspensão e na alíquota zero. |
| `Sujeito_Fator_Transicao_Art_474` | booleano | Verdadeiro nos créditos de aquisição dos arts. 447, 449 e 465 da LC, que de 2029 a 2032 caem a 9/10, 8/10, 7/10 e 6/10. Falso nos créditos da produção (arts. 450 e 467). |
| `Exige_Inscricao_Suframa_No_Documento` | booleano | Verdadeiro: a alíquota zero depende da inscrição do destinatário no documento (arts. 529, § 2º, e 537, § 2º). |
| `Exige_Internamento` | booleano | Verdadeiro: a alíquota zero depende do internamento (arts. 529, § 6º, e 537, § 6º; art. 548). |
| `Prazo_Comprovacao_Dias` | número, opcional | 120 dias da emissão do documento. |
| `Prazo_Prorrogado_Dias` | número, opcional | Até 210 dias, com requerimento justificado antes do vencimento (art. 529, § 7º). |
| `Prazo_Conversao_Meses` | número, opcional | 48 meses, da emissão do documento de importação, para a suspensão virar isenção (art. 528, § 2º). |
| `Prazo_Retorno_Dias` | número, opcional | 180 dias para o retorno do bem que saiu para conserto, revisão e semelhantes (art. 528, § 5º). |
| `Prazo_Utilizacao_Meses` | número, opcional | 60 meses, do primeiro dia do mês seguinte ao da apropriação, para usar o crédito presumido (art. 533, parágrafo único; art. 540). |
| `Permite_Ressarcimento` | booleano | Falso nos créditos presumidos: só compensam o mesmo tributo, sem ressarcimento em dinheiro nem compensação com outro tributo (arts. 533 e 540). |
| `Fonte_Normativa` | enumeração {lc_e_decreto, so_lc} | `so_lc`: só a LC 214 (o regulamento do IBS não está no Project). |
| `Fundamento_Legal` | texto | Artigos da LC e do Decreto. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

# 5. Internamento, importação com suspensão e crédito presumido

## 5.1 O que o texto pede

1. **Internamento** (Decreto, arts. 529, §§ 6º e 7º, 543 a 548). A alíquota zero da venda para a ZFM ou ALC depende do internamento: a Suframa registra o evento de internamento no documento, condicionado ao evento de conclusão do desembaraço do destino. O prazo é de 120 dias da emissão, prorrogável para até 210 com requerimento justificado **antes** do vencimento. Sem o evento no prazo, o fornecedor declara a CBS que seria devida, com acréscimos, pelo **evento de não internamento**. O art. 547 lista cinco casos de não comprovação.
2. **Importação com suspensão** (Decreto, art. 528; LC, art. 443). A suspensão vira isenção em 48 meses da emissão do documento de importação (consumo ou incorporação), ou após a depreciação integral ou 48 meses de permanência no ativo imobilizado, o que ocorrer primeiro. A saída para fora antes da conversão obriga a declarar a CBS suspensa com acréscimos desde a emissão. Seis saídas não obrigam (conserto, revisão, limpeza, recondicionamento, demonstração em feira e industrialização por encomenda), com retorno em 180 dias; a industrialização por encomenda fora da ZFM só se o processo produtivo básico autorizar. A importação de procedência estrangeira depende de licença prévia da Suframa (art. 550).
3. **Crédito presumido** (LC, arts. 444, 447, 449, 450, 452, 465, 467, 468 e 474; Decreto, arts. 531, 533, 539 e 540). Os créditos de aquisição caem a 9/10, 8/10, 7/10 e 6/10 de 2029 a 2032 (art. 474). O crédito da produção não tem esse fator. Todos só compensam o mesmo tributo e expiram em cinco anos do mês seguinte ao da apropriação. O crédito de CBS pode ser apropriado desde a emissão do documento (Decreto, art. 531, § 3º).
4. **Comunicações da Suframa** (Decreto, art. 435, § 7º, e art. 438, § 8º): bloqueio da inscrição, suspensão do licenciamento, suspensão ou cancelamento dos incentivos do bem, incentivo indevido e descumprimento do processo produtivo básico.

## 5.2 Entidade nova: `Mov_Zfm_Alc_Internamento`

O controle do internamento da venda com alíquota zero para a ZFM ou a ALC (Decreto, arts. 543 a 548): o protocolo, o evento de internamento da Suframa, o evento de conclusão do desembaraço do destino e o prazo de 120 dias (210 com prorrogação). Sem o evento de internamento no prazo, o fornecedor declara a CBS que seria devida com os acréscimos do art. 27 pelo evento de não internamento. O ERP registra, calcula o prazo, avisa e nunca bloqueia. Um registro por documento.

*Tipo: movimento (um registro por documento). Mestre: não. Vigência: não. Campos: 16.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Internamento` | identificador | --- |
| `ID_Nota` | referência (Mov_Nota_Fiscal_Saida) --- identidade | O documento fiscal da venda. |
| `ID_Area_Incentivada` | referência (Cad_Area_Incentivada) | A área de destino. |
| `ID_Habilitacao_Destinatario` | referência (Cad_Habilitacao_Regime_Especial), opcional | A habilitação do destinatário, de onde vem a inscrição citada no documento. |
| `ID_Zfm_Alc_Regra` | referência (Cad_Zfm_Alc_Regra) | A linha aplicada (os prazos vêm dela). |
| `Situacao_Internamento` | enumeração {aguardando, internado, nao_internado, prorrogado} | `internado` com o evento da Suframa e o do desembaraço (Decreto, art. 548); `nao_internado` na falta do evento depois do prazo (parágrafo único). |
| `Data_Prazo_Final` | data | Calculado e armazenado: emissão mais o prazo da regra, mais a prorrogação. Fica gravado porque uma mudança de vigência não reescreve a venda já feita. |
| `Data_Requerimento_Prorrogacao` | data, opcional | Requerimento à Suframa, feito antes do vencimento do prazo original (§ 7º). |
| `Numero_Protocolo_Suframa` | código (até 40), opcional | O protocolo eletrônico de ingresso (art. 543). |
| `ID_Dfe_Evento_Internamento` | referência (Mov_Dfe_Evento), opcional | O evento de internamento registrado pela Suframa no documento (art. 548). |
| `ID_Dfe_Evento_Desembaraco` | referência (Mov_Dfe_Evento), opcional | O evento de conclusão do desembaraço das administrações do destino. |
| `ID_Dfe_Evento_Nao_Internamento` | referência (Mov_Dfe_Evento), opcional | O evento de não internamento que o fornecedor registra. |
| `Motivo_Nao_Comprovacao` | enumeração {nao_ingressou, nao_desembaracado_destino, prazo_vencido, descumprimento_etapas, vicio_simulacao_fraude}, opcional | Os cinco casos do art. 547. |
| `Valor_Cbs_Declarado_Nao_Internamento` | número, opcional | Informado: a CBS que seria devida sem a alíquota zero, declarada no evento. Os acréscimos seguem Cad_Acrescimo_Legal_Cbs (hipóteses `zfm_nao_internamento_120_dias` e `alc_nao_internamento`). |
| `Data_Conclusao` | data, opcional | Quando o internamento ou o não internamento fechou o controle. |
| `Observacao` | texto, opcional | --- |

## 5.3 Entidade nova: `Mov_Zfm_Alc_Importacao_Suspensao`

A importação com suspensão da CBS por indústria incentivada (Decreto, arts. 528 e 536), por item: o prazo de 48 meses, a conversão em isenção (consumo ou incorporação no processo produtivo, depreciação integral ou permanência de 48 meses no ativo imobilizado, o que ocorrer primeiro) e a saída para fora da área antes da conversão, que obriga a declarar a CBS suspensa com os acréscimos do art. 27 pelo evento no documento de importação. Seis saídas físicas não obrigam (conserto, revisão, limpeza, recondicionamento, demonstração e industrialização por encomenda), com retorno em 180 dias. O ERP registra e avisa.

*Tipo: movimento (um registro por item). Mestre: não. Vigência: não. Campos: 19.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Importacao_Suspensao` | identificador | --- |
| `ID_Duimp_Item` | referência (Mov_Duimp_Item), opcional | O item da Duimp. Exatamente um entre este e o item da nota de entrada. |
| `ID_Nota_Fiscal_Entrada_Item` | referência (Mov_Nota_Fiscal_Entrada_Item), opcional | O item do documento fiscal de importação. |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) | A habilitação da indústria incentivada importadora. |
| `ID_Area_Incentivada` | referência (Cad_Area_Incentivada) | --- |
| `ID_Zfm_Alc_Regra` | referência (Cad_Zfm_Alc_Regra) | A linha aplicada (prazos de 48 meses e 180 dias). |
| `Numero_Licenca_Suframa` | código (até 30), opcional | A licença prévia da Suframa para a importação de procedência estrangeira (Decreto, art. 550). |
| `Data_Documento_Importacao` | data | A emissão do documento fiscal de importação: de onde correm os 48 meses e os acréscimos. |
| `Valor_Cbs_Suspensa` | número | Informado ou lido da Duimp (`Mov_Duimp_Item_Tributo.Valor_Suspenso`). |
| `Valor_Ibs_Suspenso` | número, opcional | Só pela LC (art. 443); o regulamento do IBS não está no Project. |
| `Situacao_Suspensao` | enumeração {suspensa, convertida_em_isencao, saida_declarada, saida_excecionada, cancelada} | --- |
| `Motivo_Conversao` | enumeração {consumido_ou_incorporado, depreciacao_integral, permanencia_48_meses}, opcional | Os três motivos do § 2º. |
| `Data_Conversao` | data, opcional | --- |
| `ID_Ativo_Imobilizado` | referência (Cad_Ativo_Imobilizado), opcional | O bem no ativo imobilizado, de onde vêm a depreciação integral e a permanência. |
| `Data_Saida_Para_Fora` | data, opcional | A remessa para fora da área antes da conversão. |
| `Motivo_Excecao_Saida` | enumeração {conserto_reparo, revisao, limpeza, recondicionamento, demonstracao_feira, industrializacao_encomenda}, opcional | As seis saídas do § 4º. A industrialização por encomenda fora da área só se o processo produtivo básico autorizar (§ 6º). |
| `Data_Retorno` | data, opcional | Retorno dentro de 180 dias da emissão do documento (§ 5º). |
| `ID_Dfe_Evento_Declaracao` | referência (Mov_Dfe_Evento), opcional | O evento que declara a CBS suspensa com acréscimos no documento de importação (§ 3º). |
| `Observacao` | texto, opcional | --- |

## 5.4 Entidade nova: `Mov_Zfm_Credito_Ibs_Periodo`

A apuração mensal do crédito presumido de IBS da indústria incentivada (LC, art. 450, §§ 1º e 6º): o percentual (55%, 75%, 90,25% ou 100%) incide sobre o saldo devedor do IBS do período de cada grupo, e não sobre cada nota. Uma linha por empresa, competência e percentual. Fonte só a LC 214: o regulamento do IBS não está no Project, e todo o desenho é provisório (Q158-9).

*Tipo: movimento (um registro por empresa, competência e percentual). Mestre: não. Vigência: não. Campos: 12.*

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Zfm_Credito_Ibs_Periodo` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | A indústria incentivada. |
| `Competencia` | competência --- identidade | O mês de apuração. |
| `Percentual_Incentivo` | número --- identidade | O percentual do grupo (art. 450, § 1º). |
| `ID_Zfm_Alc_Regra` | referência (Cad_Zfm_Alc_Regra) | A linha do percentual. |
| `Valor_Saldo_Devedor_Ibs_Grupo` | número | Calculado e armazenado: o saldo devedor do IBS do período dos débitos do grupo, sem o crédito presumido (§ 6º, I). |
| `Valor_Credito_Presumido_Ibs` | número | Calculado e armazenado: o saldo do grupo vezes o percentual. Vale como compensação do IBS do mesmo contribuinte, sem ressarcimento (art. 452). |
| `Valor_Saldo_A_Recuperar` | número, opcional | O saldo a recuperar do período (art. 45, § 3º), quando há (§ 6º, IV). |
| `Valor_Transferido` | número, opcional | O valor dos débitos extintos transferido à indústria, até o limite do saldo a recuperar, em até 3 dias úteis da conclusão da apuração (§ 6º, IV). |
| `Data_Transferencia` | data, opcional | --- |
| `Situacao_Apuracao` | enumeração {calculada, concluida} | `concluida` quando o período fecha no Comitê Gestor do IBS. |
| `Origem_Calculo` | enumeração {calculado_pelo_erp, informado_comite_gestor} | O ERP calcula para conferir; o valor oficial é o do Comitê Gestor. |

## 5.5 Mudanças em entidades existentes (ZFM e ALC)

| Entidade | Campo | Mudança |
|---|---|---|
| `Mov_Credito_Presumido_Zfm` | `ID_Apuracao_Origem` | **Passa a opcional.** Exatamente um entre este e `ID_Nota_Fiscal_Entrada_Item`: o crédito da produção nasce da saída; o de aquisição e o de importação nascem da entrada. |
| `Mov_Credito_Presumido_Zfm` | `ID_Nota_Fiscal_Entrada_Item` | **Novo.** Referência (Mov_Nota_Fiscal_Entrada_Item), opcional: o item de entrada que gerou o crédito de aquisição (arts. 444, 447, 449, 462 e 465 da LC). Na importação, o item do documento de importação. |
| `Mov_Credito_Presumido_Zfm` | `Origem_Credito` | **Novo.** Enumeração {producao, aquisicao_origem_nacional, aquisicao_intermediario_local, importacao_revenda}. Decide quais campos valem e se o fator do art. 474 se aplica (nas duas aquisições, sim; na produção e na importação para revenda, não). |
| `Mov_Credito_Presumido_Zfm` | `ID_Zfm_Alc_Regra` | **Novo.** Referência (Cad_Zfm_Alc_Regra): a linha aplicada, de onde vêm percentual, base e prazo. |
| `Mov_Credito_Presumido_Zfm` | `ID_Habilitacao` | **Novo.** Referência (Cad_Habilitacao_Regime_Especial): a habilitação do titular do crédito. |
| `Mov_Credito_Presumido_Zfm` | `ID_Credito` | **Novo.** Referência (Mov_Credito_Fiscal), opcional: o crédito gerado, com a data de apropriação (`Data_Apropriacao`) e o último dia de uso (`Data_Limite_Utilizacao`, cinco anos). O saldo e as aplicações ficam em `Mov_Credito_Fiscal_Aplicacao`. |
| `Mov_Credito_Presumido_Zfm` | `ID_Zfm_Credito_Ibs_Periodo` | **Novo.** Referência (Mov_Zfm_Credito_Ibs_Periodo), opcional: o período em que o IBS do crédito da produção foi apurado. |
| `Mov_Credito_Presumido_Zfm` | `Percentual_Credito_Cbs` | **Passa a opcional.** Vazio no crédito de aquisição, que é de IBS. |
| `Mov_Credito_Presumido_Zfm` | `ID_Calendario` | **Passa a opcional e o texto muda.** Só os créditos de aquisição (arts. 447, 449 e 465) apontam para a linha `percentual_credito_zfm` do ano; os da produção e da importação para revenda não têm fator. |
| `Mov_Credito_Presumido_Zfm` | `Tipo_Area e Percentual_Credito_Ibs` | **Texto.** "alc cobre só CBS" vale para a produção (art. 467); o crédito de aquisição da ALC é de IBS (art. 465). Na produção da ZFM, `Percentual_Credito_Ibs` é só o grupo do art. 450, § 1º, e o valor do IBS vem do período; `Valor_Credito` por item é a CBS. |
| `Mov_Credito_Fiscal` | `Origem` | **Valor novo** `presumido_zfm_alc`. |
| `Cad_Habilitacao_Regime_Especial` | `ID_Participante_Titular` | **Texto.** Na habilitação de tipo `suframa_zfm_alc`, o titular é o contribuinte inscrito na Suframa, seja vendedor ou comprador. |
| `Cad_Calendario_Transicao` | `percentual_credito_zfm` | **Texto.** O fator de 2029 a 2032 vale só para os créditos dos arts. 447, 449 e 465 (LC, art. 474). Os valores da série não mudam. |

## 5.6 Exemplo calculado (números hipotéticos)

**Crédito de IBS da produção, mês de 2030.** Indústria incentivada com dois grupos de débitos. Grupo de bens de consumo final: saldo devedor do IBS de R$ 200.000,00 antes do crédito (LC, art. 450, § 6º, I); crédito de 55% = R$ 110.000,00. Grupo de bens de capital: saldo de R$ 80.000,00; crédito de 75% = R$ 60.000,00. São **duas linhas** de `Mov_Zfm_Credito_Ibs_Periodo` (percentuais 55 e 75), sem fator (art. 474 não alcança o art. 450). Se um grupo ficar com saldo a recuperar, a transferência vale em até três dias úteis da conclusão da apuração.

**Crédito de aquisição em 2029.** Compra de R$ 100.000,00 de bem industrializado nacional de São Paulo, para empresa habilitada da ZFM no regime regular. Percentual de 7,5% (Sul e Sudeste, menos ES; LC, art. 447, § 1º, I) × fator 9/10 de 2029 (LC, art. 474, I) = 6,75% = **R$ 6.750,00**. Do Pará, o percentual seria 13,5% × 0,9 = 12,15% = **R$ 12.150,00**. Em 2033 o fator deixa de existir: a LC só o prevê de 2027 a 2032 e a série do calendário volta a 100% (Q158-C5 confirma).

# 6. Motor de Regras e domínios

O Motor (`Cad_Motor_Regra`, `_Criterio` e `_Resultado`) escolhe o cClassTrib. Este documento pede **sete critérios novos** e nenhum tipo de resultado novo. Nenhum código de classificação tributária é criado aqui: as regras são cadastro do usuário e do contador, e a carga é provisória.

| Valor novo em `campo_criterio_regra` | O que lê |
|---|---|
| `tipo_ente_comprador` | O `Tipo_Ente` do grupo `gCompraGov` da nota (LC, art. 473, § 1º). |
| `aquisicao_presencial_dispensada` | As duas marcas da nota juntas: aquisição presencial e dispensada de licitação (LC, art. 473, § 2º). |
| `area_incentivada_do_destinatario` | O destinatário está em município de `Cad_Area_Incentivada_Municipio` na data (LC, arts. 445, 451, 463 e 466). |
| `area_incentivada_do_emitente` | O emitente está em município de área incentivada na data (LC, arts. 450, 451, 466 e 467). |
| `habilitacao_suframa_do_destinatario` | O destinatário tem `Cad_Habilitacao_Suframa` vigente e ativa, e o regime dele (regular ou Simples Nacional) é o que a lei pede (LC, arts. 445 e 463). |
| `habilitacao_suframa_do_emitente` | O emitente tem habilitação de indústria incentivada vigente (LC, arts. 448, 450 e 467). |
| `categoria_produto_suframa` | A categoria e a marca do art. 454 em `Cad_Habilitacao_Suframa_Produto` para a NCM do item (LC, arts. 450 e 454). |

**Outros domínios em `Cad_Classe_Sistema`** (20 valores no total, contando os critérios):

| Domínio | Valores novos |
|---|---|
| beneficio_zfm_alc (domínio novo) | 10 |
| tipo_regime_especial_federal (+ suframa_zfm_alc) | 1 |
| tipo_lista_legal (+ zfm_alc_bens_excluidos) | 1 |
| parametro_transicao (+ redutor_compras_governamentais) | 1 |
| campo_criterio_regra (+ 7 critérios) | 7 |

# 7. O que entra no próximo "consolidar"

**10 entidades novas (155 campos)**, todas na Contabilidade & Fiscal.

| Entidade | Tipo | Campos | Mestre | Vigência | Seção |
|---|---|---|---|---|---|
| `Cad_Regra_Compra_Governamental` | parâmetro por tipo de ente e janela | 22 | sim | sim | 3.5 |
| `Cad_Area_Incentivada` | catálogo das áreas | 14 | sim | sim | 4.4 |
| `Cad_Area_Incentivada_Municipio` | municípios da área | 10 | não | sim | 4.5 |
| `Cad_Habilitacao_Suframa` | extensão 1:1 da habilitação | 13 | não | sim | 4.6 |
| `Cad_Habilitacao_Suframa_Produto` | produto do projeto aprovado | 11 | não | sim | 4.7 |
| `Mov_Habilitacao_Suframa_Ocorrencia` | comunicações da Suframa | 11 | não | não | 4.8 |
| `Cad_Zfm_Alc_Regra` | catálogo dos benefícios | 27 | sim | sim | 4.9 |
| `Mov_Zfm_Alc_Internamento` | controle do internamento | 16 | não | não | 5.2 |
| `Mov_Zfm_Alc_Importacao_Suspensao` | importação com suspensão | 19 | não | não | 5.3 |
| `Mov_Zfm_Credito_Ibs_Periodo` | crédito de IBS por período | 12 | não | não | 5.4 |

**5 entidades alteradas** (9 campos novos; as demais mudanças são valores, textos e campos que passam a opcionais).

| Entidade | O que muda |
|---|---|
| `Mov_Credito_Presumido_Zfm` | 6 campos novos; `ID_Apuracao_Origem`, `ID_Calendario` e `Percentual_Credito_Cbs` passam a opcionais (exatamente um entre `ID_Apuracao_Origem` e `ID_Nota_Fiscal_Entrada_Item`); texto de `Tipo_Area`, `Percentual_Credito_Ibs` e `ID_Calendario` corrigido (seção 5.5) |
| `Mov_Credito_Fiscal` | valor novo `presumido_zfm_alc` em `Origem` |
| `Cad_Habilitacao_Regime_Especial` | valor novo `suframa_zfm_alc` no domínio `tipo_regime_especial_federal` e texto de `ID_Participante_Titular` |
| `Mov_Nota_Fiscal_Saida_Compra_Governamental` | 3 campos novos; texto de `Percentual_Redutor` corrigido (LC, art. 472, e não art. 473) |
| `Cad_Calendario_Transicao` | parâmetro novo `redutor_compras_governamentais` e texto do `percentual_credito_zfm` (o fator do art. 474 vale só para três créditos) |

**Cargas provisórias** (todas com `Situacao_Dado = provisorio` até o contador validar; Anexo A):

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Regra_Compra_Governamental` | 42 | 6 tipos de ente em 7 janelas (2026; 2027 e 2028; 2029; 2030; 2031; 2032; 2033 em diante), pela LC, art. 372, para todos os entes (Q158-C1) |
| `Cad_Area_Incentivada` | 7 | ZFM e seis ALC; fim dos benefícios em 31/12/2073 (Q158-C10) |
| `Cad_Area_Incentivada_Municipio` | 12 | Três municípios da ZFM (parciais) e nove das ALC |
| `Cad_Zfm_Alc_Regra` | 23 | 15 da ZFM e 8 das ALC |
| `Cad_Classe_Sistema` | 20 | Domínio `beneficio_zfm_alc` (10), os três valores de domínio e os 7 critérios do Motor |
| `Cad_Calendario_Transicao` (`redutor_compras_governamentais`) | 0 | Sem valor até a Resolução do Senado (Q158-2) |
| `Cad_Lista_Legal_Item` (`zfm_alc_bens_excluidos`) | 0 | Lista de NCM do contador (Q158-C9) |
| `Cad_Habilitacao_Suframa` e `_Produto` | 0 | Cadastro do usuário |

**Textos que a consolidação corrige:** `Percentual_Redutor` (art. 472, e não 473), `ID_Calendario`, `Tipo_Area` e `Percentual_Credito_Ibs` de `Mov_Credito_Presumido_Zfm`, e `percentual_credito_zfm` no calendário (seção 5.5). **Nada deste documento mexe** nas hipóteses de acréscimo 25 a 28 (documento 157), na NFS-e nem no fato gerador da compra governamental.

# 8. Perguntas

## 8.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q158-1** | Compras governamentais: `Cad_Regra_Compra_Governamental` (42 linhas: 6 tipos de ente em 7 janelas), `Indicador_Aquisicao_Presencial` e `Indicador_Dispensa_Licitacao` na nota e `ID_Regra_Compra_Governamental` no grupo? O redutor e a regra do documento 94 (`Cad_Redutor_Compra_Governamental`) viram uma regra e um parâmetro do calendário, sem a segunda tabela. | Sim |
| **Q158-2** | Redutor das compras governamentais: parâmetro `redutor_compras_governamentais` no calendário (uma linha por ano, de 2027 a 2033), **sem valor na carga** até a Resolução do Senado, com aviso do Motor quando o ano não tem linha? A proposta do TCU (44,16% em 2027) fica fora porque vem de fonte secundária e depende do Senado. | Sim |
| **Q158-3** | Cadastro da ZFM e das ALC: `Cad_Area_Incentivada` (7 linhas), `Cad_Area_Incentivada_Municipio` (12), `Cad_Habilitacao_Suframa`, `Cad_Habilitacao_Suframa_Produto` e o valor `suframa_zfm_alc` na habilitação em regime especial; a inscrição Suframa continua em `Cad_Participante_Inscricao`? | Sim |
| **Q158-4** | `Cad_Zfm_Alc_Regra` (23 linhas, dez tipos de benefício) como catálogo único, no lugar de `Cad_Regra_Zfm_Alc_Cbs`, `Cad_Zfm_Alc_Produto_Regra` e `Cad_Cronograma_Transicao_Zfm` do documento 94? A série do fator continua no calendário. | Sim |
| **Q158-5** | Crédito presumido: `Mov_Credito_Presumido_Zfm` passa a cobrir também a aquisição e a importação para revenda (campos `Origem_Credito` e `ID_Nota_Fiscal_Entrada_Item`) e liga cada crédito a `Mov_Credito_Fiscal` (valor de origem `presumido_zfm_alc`), onde ficam a apropriação, os cinco anos e o saldo? | Sim |
| **Q158-6** | O fator do art. 474 vale só para os créditos dos arts. 447, 449 e 465 (e não para os da produção): corrijo o texto do calendário e de `ID_Calendario`? | Sim |
| **Q158-7** | `Mov_Zfm_Alc_Internamento` (um por documento, com os três eventos e o prazo gravado) e `Mov_Zfm_Alc_Importacao_Suspensao` (por item, com a conversão e as seis saídas que não obrigam)? O ERP registra, calcula o prazo e avisa; nunca bloqueia. | Sim |
| **Q158-8** | `Mov_Habilitacao_Suframa_Ocorrencia` registra as seis comunicações da Suframa e avisa, sem mudar sozinha a situação da habilitação? | Sim |
| **Q158-9** | Crédito de IBS da produção: `Mov_Zfm_Credito_Ibs_Periodo` (por empresa, competência e percentual), sem valor de IBS por item, **tudo provisório** porque o regulamento do IBS (CGIBS) não está no Project? O ERP calcula para conferir; o valor oficial é o do Comitê Gestor. | Sim |
| **Q158-10** | Bens fora do regime (LC, art. 441; Decreto, art. 434): lista legal `zfm_alc_bens_excluidos` em `Cad_Lista_Legal_Item`, carga vazia até o contador mapear as NCM? | Sim |
| **Q158-11** | Motor: os sete critérios novos da seção 6, sem criar código de classificação tributária? | Sim |
| **Q158-12** | O lado **comprador** do ente público (empenho, liquidação, pagamento e a contabilidade pelo MCASP) fica **fora** até haver cliente ente público (D-N68)? O MCASP não traz CBS nem IBS; o ERP desta fase é o do fornecedor. | Sim |
| **Q158-13** | Aplico tudo no próximo "consolidar", junto com os documentos 156 e 159, se já estiverem prontos? | Sim |

## 8.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q158-C1** | Transição da CBS nas compras (LC, art. 372; Decreto, art. 441): a LC vale para **todos os entes**; o Decreto (§§ 1º e 2º) fala só de Estados e Municípios. Para União e Distrito Federal valem as mesmas janelas (CBS fora em 2027 e 2028; 10%, 20%, 30% e 40% de 2029 a 2032; integral desde 2033)? E o IBS da União em 2027 e 2028, com a CBS fora do regime? | Segue a LC para todos os entes |
| **Q158-C2** | Com a CBS só em parte (2029 a 2032): a alíquota que sobe para o ente comprador é o IBS mais a **parte** da CBS que segue o regime, e o resto da CBS continua CBS da União? O redutor incide antes? | Sim, na ordem do exemplo da seção 3.4 |
| **Q158-C3** | Redutor: um percentual único por ano para a CBS e o IBS? O Decreto (art. 601) calcula o de 2027 e 2028 só sobre a CBS, e o de 2033 sobre CBS e IBS. O que vale para o IBS em 2027 e 2028 (o regulamento do IBS é do Comitê Gestor)? | Um percentual por ano para os dois |
| **Q158-C4** | Data que decide a janela: a do **pagamento** (Decreto, art. 439, § 6º). Em pagamento parcelado, cada parcela vale pela sua data? Pagamento antecipado de um ano e nota de outro? | Cada pagamento pela sua data |
| **Q158-C5** | Fator do art. 474: aplica-se só às percentagens dos arts. 447, § 1º, 449, § 1º, e 465, § 1º, e não à incidência de 70% (arts. 446 e 464) nem à importação para revenda (arts. 444 e 462)? E de 2033 em diante o percentual volta ao cheio? | Só os três artigos; cheio desde 2033 |
| **Q158-C6** | Crédito de IBS da produção (art. 450, §§ 1º e 6º): grupo sem saldo devedor no mês dá crédito zero? O saldo a recuperar e a transferência de três dias úteis dependem do Comitê Gestor, e o ERP só confere? | Crédito zero; só confere |
| **Q158-C7** | Crédito de CBS da produção: a apropriação é da emissão do documento (Decreto, art. 531, § 3º) e os cinco anos correm do primeiro dia do mês seguinte à apropriação (art. 533, parágrafo único)? Vale o mesmo para os créditos de IBS? | Sim, para CBS e IBS |
| **Q158-C8** | Internamento: os 120 dias contam em dias corridos da emissão, com prorrogação até 210 (total, e não 210 a mais)? Os acréscimos do art. 27 correm de quando (hipóteses 26 e 28 do documento 157 estão com termo inicial em aberto, Q157-C7)? | Dias corridos; 210 no total; termo em aberto |
| **Q158-C9** | Bens fora do regime (LC, art. 441): quais NCM entram na lista? As exceções do refino (Decreto, art. 434, §§ 1º a 4º) e da perfumaria (posições 33.03 a 33.07) vão como linhas "exceto"? Quem mantém a lista quando o Executivo publicar a lista do art. 454, § 3º? | Sem carga; o contador monta a lista |
| **Q158-C10** | Fim dos benefícios: `31/12/2073` para a ZFM e as ALC (art. 92-A do ADCT; Decreto, arts. 432 e 436) está certo? E o crédito de aquisição e o de importação para revenda valem até lá? | 31/12/2073 para todos |
| **Q158-C11** | Habilitação com projeto aprovado antes da LC: a convalidação (Decreto, art. 435, § 6º, II, e art. 438, § 7º, II) tem prazo fixado no ato conjunto da RFB, da Suframa e do CGIBS? O ERP mostra a situação `pendente` até lá? | `pendente` até o ato |

## 8.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q158-E1** | Os códigos dos eventos fiscais de **internamento**, de **conclusão do desembaraço** e de **não internamento** não estão nos documentos que tenho (vêm de nota técnica). Quando a NT chegar, entram em `Cad_Dfe_Evento_Tipo` com autor `suframa` ou destinatário. Há uma NT em mãos? |
| **Q158-E2** | Manaus, Rio Preto da Eva e Itacoatiara entram só em parte na ZFM (Decreto, art. 433, I). O ERP guarda o município, e não o endereço dentro da parte demarcada. Aceito que o usuário informe a marca `Eh_Parcial` e confirme no cadastro do destinatário? |
| **Q158-E3** | O cadastro de clientes já traz a inscrição Suframa em `Cad_Participante_Inscricao` (`Tipo_Inscricao` = suframa) e a nota já leva o número em campo próprio (Decreto, art. 529, § 2º)? Se não, o cadastro de inscrições é o ponto de entrada. |
| **Q158-E4** | Há hoje cliente na ZFM ou nas ALC? A resposta define a prioridade do internamento e da importação com suspensão na implantação. |

# 9. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **O IBS está só na LC.** O regulamento do IBS (Comitê Gestor) não está no Project; toda linha de IBS marca `so_lc` e a carga é provisória. Se o Comitê Gestor publicar o regulamento, os percentuais, as bases e os prazos do IBS podem mudar sem mudar o desenho.
3. **A Resolução do Senado do redutor não está nos documentos.** A carga do redutor é vazia. O edital que não considerar o redutor é problema do comprador (Decreto, art. 442, § 2º).
4. **A devolução do IBS e da CBS ao turista estrangeiro** (LC, art. 471; ato conjunto do Ministério da Fazenda e do Comitê Gestor) **fica fora**: depende de ato ainda não publicado nos documentos. Vira desenho próprio quando o ato existir.
5. **A contrapartida do Estado do Amazonas** (LC, art. 457: 1,5% do faturamento das indústrias incentivadas, a partir de 2033) **é do Estado**, e não do ERP do fornecedor; não há campo.
6. **A divulgação da lista do art. 454, § 3º, pelo Executivo** ainda não consta; `Eh_Produto_Art_454` é informado.
7. **O lado comprador do ente público** (MCASP) fica fora (Q158-12).
8. **As leituras minhas** (IBS mais a parte da CBS, ordem do redutor, fator só nos três créditos, 120 dias corridos, grupo sem saldo com crédito zero) estão marcadas e vão ao contador; nenhuma vira regra no código.

# Anexo A. Carga provisória (todas com `Situacao_Dado = provisorio`)

## A.1 `Cad_Regra_Compra_Governamental`: 42 linhas (6 tipos de ente × 7 janelas)

As janelas e o que valem em cada uma, iguais para os seis tipos (LC, art. 372; Decreto, art. 441):

| Janela | Início | Fim | Destinação da CBS | Proporção da CBS | Destinação do IBS | Redutor |
|---|---|---|---|---|---|---|
| 2026 | 2026-01-01 | 2026-12-31 | não | — | não | não |
| 2027 e 2028 | 2027-01-01 | 2028-12-31 | não | — | sim | sim |
| 2029 | 2029-01-01 | 2029-12-31 | sim | 10% | sim | sim |
| 2030 | 2030-01-01 | 2030-12-31 | sim | 20% | sim | sim |
| 2031 | 2031-01-01 | 2031-12-31 | sim | 30% | sim | sim |
| 2032 | 2032-01-01 | 2032-12-31 | sim | 40% | sim | sim |
| 2033 em diante | 2033-01-01 | 9999-12-31 | sim | 100% | sim | sim |

O que cada tipo faz, nas janelas em que a destinação vale (LC, art. 473, § 1º):

| Tipo de ente | Equiparado a | Tributo que recebe a soma | Zera a CBS | Zera o IBS estadual | Zera o IBS municipal | Fundamento |
|---|---|---|---|---|---|---|
| União | — | `cbs` | não | sim | sim | LC, art. 473, § 1º, I; Decreto, art. 439, § 1º, I |
| Estados | — | `ibs_estadual` | sim | não | sim | LC, art. 473, § 1º, II; Decreto, art. 439, § 1º, II |
| Distrito Federal | — | `ibs_distrital` | sim | não | não | LC, art. 473, § 1º, IV; Decreto, art. 439, § 1º, IV |
| Municípios | — | `ibs_municipal` | sim | sim | não | LC, art. 473, § 1º, III; Decreto, art. 439, § 1º, III |
| Consórcio público | municipio_sede | `ibs_municipal` | sim | sim | não | LC, art. 473, § 4º; Decreto, art. 439, § 3º |
| Comitê Gestor do IBS | consorcio_publico | `ibs_municipal` | sim | sim | não | LC, art. 473, § 6º; Decreto, art. 439, § 5º |

Nas janelas com destinação, valem também `Afasta_Se_Presencial_E_Dispensada`, `Afasta_Redutor_Se_Aliquota_Uniforme`, `Afasta_Redutor_Se_Simples_Mei` e `Alcanca_Importacao`, todos verdadeiros; em 2026 todos falsos. Em 2027 e 2028 a destinação da CBS é falsa, e as colunas `Zera_Cbs` ficam falsas.

## A.2 `Cad_Area_Incentivada`: 7 linhas

| Código | Nome | Tipo | Estado | Norma |
|---|---|---|---|---|
| `ZFM` | Zona Franca de Manaus | `zfm` | AM | Decreto-Lei 288/1967 (art. 433, I do Decreto) |
| `ALC-TABATINGA` | Tabatinga | `alc` | AM | Lei 7.965/1989 |
| `ALC-GUAJARA-MIRIM` | Guajará-Mirim | `alc` | RO | Lei 8.210/1991 |
| `ALC-BOA-VISTA-BONFIM` | Boa Vista e Bonfim | `alc` | RR | Lei 8.256/1991 |
| `ALC-MACAPA-SANTANA` | Macapá e Santana | `alc` | AP | Lei 8.387/1991, art. 11 |
| `ALC-BRASILEIA-EPITACIOLANDIA` | Brasiléia, com extensão a Epitaciolândia | `alc` | AC | Lei 8.857/1994 |
| `ALC-CRUZEIRO-DO-SUL` | Cruzeiro do Sul | `alc` | AC | Lei 8.857/1994 |

`Data_Fim_Beneficios` = 31/12/2073 em todas, provisório (Q158-C10). Fundamento: LC, arts. 440 e 459; Decreto, arts. 433 e 437.

## A.3 `Cad_Area_Incentivada_Municipio`: 12 linhas

| Área | Município | UF | Parcial |
|---|---|---|---|
| `ZFM` | Manaus | AM | sim |
| `ZFM` | Rio Preto da Eva | AM | sim |
| `ZFM` | Itacoatiara | AM | sim |
| `ALC-TABATINGA` | Tabatinga | AM | não |
| `ALC-GUAJARA-MIRIM` | Guajará-Mirim | RO | não |
| `ALC-BOA-VISTA-BONFIM` | Boa Vista | RR | não |
| `ALC-BOA-VISTA-BONFIM` | Bonfim | RR | não |
| `ALC-MACAPA-SANTANA` | Macapá | AP | não |
| `ALC-MACAPA-SANTANA` | Santana | AP | não |
| `ALC-BRASILEIA-EPITACIOLANDIA` | Brasiléia | AC | não |
| `ALC-BRASILEIA-EPITACIOLANDIA` | Epitaciolândia | AC | não |
| `ALC-CRUZEIRO-DO-SUL` | Cruzeiro do Sul | AC | não |

## A.4 `Cad_Classe_Sistema`

- Domínio `beneficio_zfm_alc` (10 valores): `aliquota_zero_venda_para_area`, `aliquota_zero_intermediario_entre_industrias`, `aliquota_zero_venda_dentro_da_area`, `suspensao_importacao_industria`, `credito_presumido_importacao_revenda`, `incidencia_ibs_entrada_area`, `credito_presumido_aquisicao_origem_nacional`, `credito_presumido_intermediario_local`, `credito_presumido_producao_ibs`, `credito_presumido_producao_cbs`.
- `tipo_regime_especial_federal`: `suframa_zfm_alc`.
- `tipo_lista_legal`: `zfm_alc_bens_excluidos`.
- `parametro_transicao`: `redutor_compras_governamentais`.
- `campo_criterio_regra`: `tipo_ente_comprador`, `aquisicao_presencial_dispensada`, `area_incentivada_do_destinatario`, `area_incentivada_do_emitente`, `habilitacao_suframa_do_destinatario`, `habilitacao_suframa_do_emitente`, `categoria_produto_suframa`.

## A.5 `Cad_Zfm_Alc_Regra`: 23 linhas

| Código | Benefício | Área | Tributo | Forma | Categoria | Origem | Base | % | Fator art. 474 | Fonte | Fundamento |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `ZFM-ALIQ-ZERO-VENDA-PARA-AREA` | `aliquota_zero_venda_para_area` | zfm | cbs_e_ibs | aliquota_zero | — | — | — | — | não | `lc_e_decreto` | LC, art. 445; Decreto, art. 529 |
| `ZFM-ALIQ-ZERO-INTERMEDIARIO-ENTRE-INDUSTRIAS` | `aliquota_zero_intermediario_entre_industrias` | zfm | cbs_e_ibs | aliquota_zero | bem_intermediario | — | — | — | não | `lc_e_decreto` | LC, art. 448; Decreto, art. 530 |
| `ZFM-ALIQ-ZERO-VENDA-DENTRO-DA-AREA` | `aliquota_zero_venda_dentro_da_area` | zfm | cbs | aliquota_zero | — | — | — | — | não | `lc_e_decreto` | LC, art. 451; Decreto, art. 532 |
| `ZFM-SUSP-IMPORTACAO-INDUSTRIA` | `suspensao_importacao_industria` | zfm | cbs_e_ibs | suspensao | — | — | — | — | não | `lc_e_decreto` | LC, art. 443; Decreto, art. 528 |
| `ZFM-CRED-IMPORTACAO-REVENDA-IBS` | `credito_presumido_importacao_revenda` | zfm | ibs | credito_presumido | — | — | aliquota_ibs_importacao | 50 | não | `so_lc` | LC, art. 444, § 1º |
| `ZFM-INCIDENCIA-IBS-ENTRADA-AMAZONAS` | `incidencia_ibs_entrada_area` | zfm | ibs | incidencia_ibs_entrada | — | — | aliquota_que_incidiria | 70 | não | `so_lc` | LC, art. 446, § 1º, III |
| `ZFM-CRED-AQUISICAO-SUL-SUDESTE` | `credito_presumido_aquisicao_origem_nacional` | zfm | ibs | credito_presumido | — | sul_sudeste_exceto_es | valor_operacao | 7,5 | sim | `so_lc` | LC, art. 447, § 1º, I |
| `ZFM-CRED-AQUISICAO-DEMAIS-REGIOES` | `credito_presumido_aquisicao_origem_nacional` | zfm | ibs | credito_presumido | — | demais_regioes_e_es | valor_operacao | 13,5 | sim | `so_lc` | LC, art. 447, § 1º, II |
| `ZFM-CRED-INTERMEDIARIO-LOCAL` | `credito_presumido_intermediario_local` | zfm | ibs | credito_presumido | bem_intermediario | — | valor_operacao | 7,5 | sim | `so_lc` | LC, art. 449, § 1º |
| `ZFM-CRED-PRODUCAO-IBS-CONSUMO-FINAL` | `credito_presumido_producao_ibs` | zfm | ibs | credito_presumido | bem_consumo_final | — | saldo_devedor_ibs_periodo | 55 | não | `so_lc` | LC, art. 450, § 1º, I |
| `ZFM-CRED-PRODUCAO-IBS-BEM-CAPITAL` | `credito_presumido_producao_ibs` | zfm | ibs | credito_presumido | bem_capital | — | saldo_devedor_ibs_periodo | 75 | não | `so_lc` | LC, art. 450, § 1º, II |
| `ZFM-CRED-PRODUCAO-IBS-INTERMEDIARIO` | `credito_presumido_producao_ibs` | zfm | ibs | credito_presumido | bem_intermediario | — | saldo_devedor_ibs_periodo | 90,25 | não | `so_lc` | LC, art. 450, § 1º, III |
| `ZFM-CRED-PRODUCAO-IBS-INFORMATICA` | `credito_presumido_producao_ibs` | zfm | ibs | credito_presumido | informatica_ou_estimulo_cem | — | saldo_devedor_ibs_periodo | 100 | não | `so_lc` | LC, art. 450, § 1º, IV |
| `ZFM-CRED-PRODUCAO-CBS-PRODUTO-ART-454` | `credito_presumido_producao_cbs` | zfm | cbs | credito_presumido | produto_art_454 | — | valor_operacao | 6 | não | `lc_e_decreto` | LC, art. 450, § 2º, I; Decreto, art. 531, § 1º, I |
| `ZFM-CRED-PRODUCAO-CBS-DEMAIS` | `credito_presumido_producao_cbs` | zfm | cbs | credito_presumido | demais_produtos | — | valor_operacao | 2 | não | `lc_e_decreto` | LC, art. 450, § 2º, II; Decreto, art. 531, § 1º, II |
| `ALC-ALIQ-ZERO-VENDA-PARA-AREA` | `aliquota_zero_venda_para_area` | alc | cbs_e_ibs | aliquota_zero | — | — | — | — | não | `lc_e_decreto` | LC, art. 463; Decreto, art. 537 |
| `ALC-ALIQ-ZERO-VENDA-DENTRO-DA-AREA` | `aliquota_zero_venda_dentro_da_area` | alc | cbs | aliquota_zero | — | — | — | — | não | `lc_e_decreto` | LC, art. 466; Decreto, art. 538 |
| `ALC-SUSP-IMPORTACAO-INDUSTRIA` | `suspensao_importacao_industria` | alc | cbs_e_ibs | suspensao | — | — | — | — | não | `lc_e_decreto` | LC, art. 461; Decreto, art. 536 |
| `ALC-CRED-IMPORTACAO-REVENDA-IBS` | `credito_presumido_importacao_revenda` | alc | ibs | credito_presumido | — | — | aliquota_ibs_importacao | 50 | não | `so_lc` | LC, art. 462, § 1º |
| `ALC-INCIDENCIA-IBS-ENTRADA` | `incidencia_ibs_entrada_area` | alc | ibs | incidencia_ibs_entrada | — | — | aliquota_que_incidiria | 70 | não | `so_lc` | LC, art. 464, § 1º, III |
| `ALC-CRED-AQUISICAO-SUL-SUDESTE` | `credito_presumido_aquisicao_origem_nacional` | alc | ibs | credito_presumido | — | sul_sudeste_exceto_es | valor_operacao | 7,5 | sim | `so_lc` | LC, art. 465, § 1º, I |
| `ALC-CRED-AQUISICAO-DEMAIS-REGIOES` | `credito_presumido_aquisicao_origem_nacional` | alc | ibs | credito_presumido | — | demais_regioes_e_es | valor_operacao | 13,5 | sim | `so_lc` | LC, art. 465, § 1º, II |
| `ALC-CRED-PRODUCAO-CBS` | `credito_presumido_producao_cbs` | alc | cbs | credito_presumido | — | — | valor_operacao | 6 | não | `lc_e_decreto` | LC, art. 467; Decreto, art. 539 |

Colunas comuns por tipo de benefício (provisórias; Q158-C5, C7, C8):

| Benefício | Inscrição no documento | Internamento | Prazos |
|---|---|---|---|
| Alíquota zero na venda para a área | sim (Decreto, arts. 529, § 2º, e 537, § 2º) | sim (arts. 529, § 6º, e 548) | 120 dias, até 210 com requerimento antes do vencimento (arts. 529, § 7º, e 537, § 7º) |
| Suspensão na importação | não | não | 48 meses para a conversão; 180 dias para o retorno das saídas excepcionadas (art. 528, §§ 2º e 5º) |
| Créditos presumidos (todos) | não | não | 60 meses de uso (LC, arts. 452 e 468, parágrafo único; Decreto, arts. 533 e 540); sem ressarcimento nem compensação com outro tributo |

# Anexo B. Cobertura dispositivo por dispositivo

| Dispositivo | O que decide | Onde fica |
|---|---|---|
| LC, arts. 370 a 372; Decreto, arts. 441 e 601 | Redutor do Senado e janelas de transição das compras | `redutor_compras_governamentais` (calendário); `Cad_Regra_Compra_Governamental` |
| LC, art. 472; Decreto, arts. 442 e 443 | Redutor e suas exceções | Colunas `Aplica_Redutor` e `Afasta_*` da regra; `Percentual_Redutor` na nota |
| LC, art. 473, §§ 1º a 3º; Decreto, arts. 439, §§ 1º a 2º, e 440 | Destinação por tipo de ente; exceção; importação | `Cad_Regra_Compra_Governamental`; marcas da nota; critério `aquisicao_presencial_dispensada` |
| LC, art. 473, §§ 4º a 6º; Decreto, art. 439, §§ 3º a 5º | Consórcio público e Comitê Gestor | `Equiparado_A`; a proporção entre os entes é do lado comprador (Q158-12) |
| Decreto, art. 439, § 6º | Fato gerador no pagamento | Documento 157 (`compra_ente_publico`) |
| LC, art. 442; Decreto, art. 435 | Habilitação da ZFM | `Cad_Habilitacao_Suframa` (`Atividade_Habilitada`, projeto, convalidação) |
| LC, art. 443; Decreto, art. 528 | Suspensão na importação (ZFM) | `Cad_Zfm_Alc_Regra`; `Mov_Zfm_Alc_Importacao_Suspensao`; hipótese 25 do documento 157 |
| LC, art. 444 | Crédito de IBS na importação para revenda (ZFM) | `Cad_Zfm_Alc_Regra`; `Mov_Credito_Presumido_Zfm` (`importacao_revenda`) |
| LC, art. 445; Decreto, art. 529 | Alíquota zero na venda para a ZFM | `Cad_Zfm_Alc_Regra`; `Mov_Zfm_Alc_Internamento`; hipótese 26 |
| LC, art. 446 | IBS de 70% na entrada no Amazonas | `Cad_Zfm_Alc_Regra` (`incidencia_ibs_entrada`); só LC |
| LC, art. 447 | Crédito de aquisição (ZFM) | `Cad_Zfm_Alc_Regra`; `Mov_Credito_Presumido_Zfm` (`aquisicao_origem_nacional`); fator do calendário |
| LC, art. 448; Decreto, art. 530 | Alíquota zero entre indústrias incentivadas | `Cad_Zfm_Alc_Regra` |
| LC, art. 449 | Crédito do intermediário local | `Cad_Zfm_Alc_Regra`; `Mov_Credito_Presumido_Zfm` |
| LC, art. 450; Decreto, art. 531 | Crédito da produção (IBS por período, CBS por item) | `Cad_Zfm_Alc_Regra`; `Mov_Zfm_Credito_Ibs_Periodo`; `Mov_Credito_Presumido_Zfm` |
| LC, art. 451; Decreto, art. 532 | CBS zero dentro da ZFM | `Cad_Zfm_Alc_Regra`; `Indicador_Zfmalc` na NFS-e (já existe) |
| LC, art. 452; Decreto, art. 533 | Uso do crédito e cinco anos | `Mov_Credito_Fiscal` (`Data_Limite_Utilizacao`); `Cad_Zfm_Alc_Regra.Prazo_Utilizacao_Meses` |
| LC, art. 453; Decreto, art. 534 | Demais operações seguem as regras gerais | Nada a registrar |
| LC, art. 454 | Produtos com IPI reduzido e crédito de 6% | `Cad_Habilitacao_Suframa_Produto.Eh_Produto_Art_454` |
| LC, art. 455 | Bens sem similar nacional | `Eh_Sem_Similar_Nacional` |
| LC, arts. 456 e 457; Decreto, art. 535 | Alíquota de referência; contrapartida do Amazonas | Fora do ERP (limites 5) |
| LC, arts. 458 a 460; Decreto, arts. 436 a 438 | ALC: prazo, áreas e habilitação | `Cad_Area_Incentivada`; `Cad_Habilitacao_Suframa` |
| LC, arts. 461 a 470; Decreto, arts. 536 a 542 | Benefícios das ALC | `Cad_Zfm_Alc_Regra` (8 linhas ALC); `Mov_Zfm_Alc_Internamento`; `Mov_Zfm_Alc_Importacao_Suspensao`; hipóteses 27 e 28 |
| LC, art. 471 | Devolução ao turista estrangeiro | Fora (limites 4) |
| LC, art. 474 | Fator de 2029 a 2032 nos três créditos | `percentual_credito_zfm` no calendário; `Sujeito_Fator_Transicao_Art_474` |
| Decreto, art. 432 | Prazo dos benefícios da ZFM | `Cad_Area_Incentivada.Data_Fim_Beneficios` |
| Decreto, art. 433 | Conceito de ZFM, indústria incentivada, bem intermediário e final | `Cad_Area_Incentivada_Municipio`; `Categoria_Produto` |
| Decreto, art. 434; LC, art. 441 | Bens fora do regime | Lista `zfm_alc_bens_excluidos` (carga vazia) |
| Decreto, arts. 543 a 549 | Internamento, procedimentos e verificações | `Mov_Zfm_Alc_Internamento` (o procedimento do Fisco não é do ERP) |
| Decreto, art. 550 | Licença prévia da Suframa na importação | `Mov_Zfm_Alc_Importacao_Suspensao.Numero_Licenca_Suframa` |
| Decreto, arts. 435, § 7º, e 438, § 8º | Comunicações da Suframa | `Mov_Habilitacao_Suframa_Ocorrencia` |

