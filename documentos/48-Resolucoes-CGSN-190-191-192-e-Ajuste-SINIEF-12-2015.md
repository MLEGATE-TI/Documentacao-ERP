# Resoluções CGSN nº 190, 191 e 192/2026 e Ajuste SINIEF 12/2015 — Documento 48

*Leitura do texto oficial das três resoluções do Comitê Gestor do Simples Nacional publicadas em 10/08/2026 do texto do Ajuste SINIEF 12/2015 (DeSTDA) e do Manual DeSTDA 2016 da SEFAZ-SP, que Alberto enviou em 12/10/2026, e o que eles pedem do dicionário. Documento de proposta e controle: nada foi alterado no dicionário (829 entidades). O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N106 a D-N113 (Simples Nacional, MEI e DeSTDA), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

Os materiais fecham a pendência mais antiga do Simples Nacional: o texto das Resoluções CGSN nº 190 e nº 191 (o documento 36 só tinha a notícia da Receita) e traz uma terceira, a nº 192. Também chegaram o texto do Ajuste SINIEF 12/2015, base da DeSTDA do documento 39, e o Manual DeSTDA 2016 da SEFAZ-SP, um manual de uso do aplicativo, sem o leiaute.

O desenho que o dicionário já tem acomoda quase tudo, porque faixas, partilha, limites e prazos já são tabelas com vigência. A leitura achou **oito decisões novas** (D-N106 a D-N113, a última com duas partes) em que o dicionário fica curto ou desatualizado, e uma correção de texto nos documentos 36 e 45. O ponto de maior efeito prático é o **fim do regime de caixa a partir de 01/01/2027**: a receita do Simples passa a ser a do faturamento (emissão do documento fiscal), e o dicionário ainda oferece o regime de caixa sem limite de data. O ponto de maior urgência é um **prazo novo: 20/12/2026**, para quem ingressa no Simples em 01/01/2027 confirmar a receita e a folha anteriores à opção (seção 4, D-N110).

A Resolução nº 190 vale em regra a partir de **01/01/2027**; a nº 191 vale a partir de **01/11/2026** quanto à NFS-e Nacional e **revoga a nº 189**; a nº 192 não afeta o ERP.

# 2. O que chegou e o que era repetido

| Material | O que é | Situação |
|---|---|---|
| Resolução CGSN nº 190, de 04/08/2026 (DOU de 10/08/2026, edição extra 149-A, 45 páginas) | Altera a Resolução CGSN nº 140/2018 (IBS e CBS no Simples, faturamento, sublimite, regime regular, MEI) e traz os Anexos I a V de 2027 a 2033 e o Anexo XIII (MEI) | Lida inteira |
| Páginas 1 a 9 do DOU da mesma edição (arquivos "INPDFViewer") | Mesmo texto em duas colunas, mais as Resoluções nº 191 e nº 192 | Lidas; as nº 191 e nº 192 só existem aqui |
| Resolução CGSN nº 191, de 04/08/2026 | Altera os arts. 59 e 79 da nº 140 (NFS-e Nacional obrigatória para ME e EPP) e revoga a nº 189 | Lida |
| Resolução CGSN nº 192, de 04/08/2026 | Altera a Resolução CGSN nº 11/2007 (arrecadação e partilha do DAS pela instituição financeira centralizadora) | Lida; sem efeito no ERP |
| Instrução Normativa Conjunta ICMBio/Ibama nº 2, de 07/08/2026 (duas páginas) | Manejo florestal; está na mesma edição do DOU | Sem relação com o ERP; não usada |
| Ajuste SINIEF 12/2015 (texto colado no chat) | Institui a DeSTDA | Lido; comparado ao documento 39 (seção 6) |
| Manual DeSTDA 2016 (SEFAZ-SP, atualizado em 18/02/2016, 8 páginas) | Manual de uso do aplicativo SEDIF-SN em São Paulo | Lido; confronto na seção 6.1 |
| `contr.pdf`, `Manual Sped.pdf`, MOC da NFCom (Anexo I e Visão Geral v1.00a), Anexo I do MOC do MDF-e v3.00b e esquemas da NFS-e RTC v1.01 | Cópias idênticas a arquivos já enviados | Dez cópias removidas (as quatro últimas chegaram de novo durante o trabalho) |

# 3. O que as resoluções dizem

A tabela traz só o que muda o comportamento do ERP; a Resolução nº 190 tem mais de 60 artigos alterados.

| Tema | Regra (artigo da Resolução CGSN nº 140, nova redação) | Efeito no dicionário |
|---|---|---|
| Faturamento | A receita é auferida no faturamento: a emissão do documento fiscal da operação, inclusive venda para entrega futura, e a emissão de documento que altere ou complemente valores, como a nota de débito (art. 2º, §§ 8º, 9º e 9º-A; art. 16, § 1º-A) | Já previsto no documento 36 (seção 12.2). A receita do período vem dos documentos emitidos |
| Regime de caixa | O § 1º do art. 16, o parágrafo único do art. 17, o § 1º do art. 18 e os arts. 19 e 20 foram revogados (art. 8º da Resolução nº 190). As notícias de Fenacon e Guia Tributário dizem que a opção pelo regime de caixa deixa de existir em 2027; o texto revogado não veio nos materiais | Decisão D-N106 |
| IBS e CBS no Simples | Passam à lista de tributos do regime (art. 4º, IX e X); o IPI continua (art. 4º, II) e o ISS e o ICMS convivem com IBS e CBS até 2032 (Anexos) | Já coberto por `Cad_Imposto` (cbs, ibs) e `Cad_Simples_Partilha` |
| Opção pelo Simples | 1 a 30 de setembro, efeito em 1º de janeiro seguinte; cancelável até 30 de novembro; indeferida, 30 dias para regularizar as pendências, com ciência no momento do pedido (art. 6º, §§ 1º a 2º-E) | `Cad_Obrigacao_Prazo_Entrega` e `Mov_Obrigacao_Prazo_Empresa` (documento 46) |
| Regime regular de IBS e CBS | Opção por semestre: 1 a 30 de setembro (efeito em 1º de janeiro) e 1 a 31 de março (efeito em 1º de julho); cancelável até 30 de novembro e 31 de maio; continua nos períodos seguintes salvo renúncia; empresa em início de atividade opta junto com o Simples, com efeito na inscrição do CNPJ (art. 40-D) | Confere com o documento 36 (seção 12.2) e com `Cad_Participante_Regime_Ibs_Cbs`. O DAS passa a deduzir as parcelas de CBS e IBS (art. 22-A): D-N112 |
| Vedação | Quem recebeu ressarcimento de créditos de IBS e CBS no ano-calendário corrente ou no anterior não pode apurar IBS e CBS pelo regime único (art. 40-E) | Regra de validação ao registrar a opção, sem campo novo |
| Sublimite | R$ 3,6 milhões para ICMS, ISS e IBS e, adicionalmente, igual limite para exportação; no início de atividade, R$ 300 mil vezes os meses até o fim do ano, com fração de mês contando como mês completo; tolerância de 20% (arts. 9º e 12) | `Cad_Simples_Limite` já tem sublimite por tributo; falta o valor por mês de atividade: D-N109 |
| Início de atividade | Passa a ser a data de inscrição no CNPJ; empresa em início de atividade é a inscrita até o fim do ano da inscrição (art. 2º, IV e V). Nos dois primeiros meses vale a primeira faixa e o fator "r" de 0,28; do 3º ao 13º mês, a média aritmética multiplicada por 12 (arts. 22 e 26) | O dicionário não guarda a data de inscrição no CNPJ da empresa: D-N113-B |
| Alíquota efetiva | ISS limitado a 5%, e a diferença vai de forma proporcional aos tributos federais e ao IBS da mesma faixa; acima da 5ª faixa, ICMS, ISS e IBS usam a alíquota nominal da 5ª faixa menos a parcela a deduzir sobre o RBT12, vezes o percentual de distribuição (art. 21) | Regra do motor de cálculo; `Cad_Simples_Faixa` e `Cad_Simples_Partilha` guardam os parâmetros |
| Segregação de receita | Exportação, tributação concentrada (monofásica) e substituição ou antecipação de ICMS, IBS e CBS, bens e serviços com IBS e CBS sem ICMS ou ISS, imunidade (art. 25, §§ 1º, 3º, 4º-B, 6º, 8º e 10-A) | `Tipo_Segregacao` só conhece valores de PIS e Cofins: D-N108 |
| PGDAS-D | Declaração assistida pela Receita, pré-preenchida até o dia 10 do mês seguinte, e os dados de IBS e CBS pré-preenchidos só mudam por ajuste nos documentos fiscais (art. 38-A); informações socioeconômicas e fiscais uma vez por ano, de janeiro a março (art. 38-B) | O segundo já está em `Mov_Simples_Declaracao_Anual`; o primeiro: D-N111 |
| Receitas anteriores à opção | Quem ingressa em 01/01/2027, ou vem do MEI, informa a receita e a folha anteriores no módulo "Receitas Anteriores à Opção" do PGDAS-D (arts. 144-D e 144-E) | D-N110; **prazos de 20/12/2026 e 20/01/2027** |
| DAS | Duas casas decimais, arredondamento comum, mínimo de R$ 0,01 (art. 45-A); IBS e CBS do regime único podem ser extintos por split payment ou por recolhimento do adquirente (art. 45-B) | Documento 10 já trata split payment e RAD; sem campo novo |
| Crédito do adquirente | Não optante tem crédito de IBS e CBS nas compras de ME e EPP optante, no montante cobrado pelo regime único; a alíquota do crédito vai no documento fiscal, com a menor alíquota no mês de início de atividade (art. 58, §§ 4º a 6º) | A conferir no conteúdo da nota de entrada (seção 5, item 2) |
| Retenção de ISS | A alíquota retida vai no documento, igual ao percentual efetivo de ISS da faixa; 2% no mês de início de atividade e no seguinte (art. 27) | `Mov_Titulo_Retencao.Aliquota_Aplicada` já recebe a alíquota; sem campo novo |
| Multas | Redução de 90% para MEI e de 60% para ME e EPP nas multas fixas ou mínimas de obrigação acessória, salvo sonegação e falta de pagamento em 30 dias; multa mínima de R$ 50 (arts. 98-A e 118) | Parâmetros do cálculo de multas; sem campo novo |
| MEI | Destaca IBS e CBS nos documentos; NFS-e Nacional obrigatória para serviços e Nota Fiscal Fácil preferencial para mercadorias (arts. 106 a 106-B); valores fixos do Anexo XIII, com ICMS, ISS, CBS e IBS por vigência | D-N107 |
| Anexos I a V | As alíquotas nominais e as parcelas a deduzir seguem as de hoje; a partilha muda a cada ano de 2027 a 2033 (CBS e IBS no lugar de PIS e Cofins, ISS e ICMS caindo, IBS subindo) e em 2033 somem o ISS e o ICMS | Cabem em `Cad_Simples_Partilha`, que tem vigência; carga de dados, não estrutura |
| NFS-e Nacional (nº 191) | ME e EPP usam a NFS-e Nacional, pelo emissor web ou por API; também as com opção pendente ou em discussão e as impedidas pelo sublimite; vedada em operação só de ICMS; vale para todo o país; efeitos a partir de 01/11/2026 | Confere com o documento 36 (seção 3), que citava a nº 189, agora revogada; o texto foi anotado nos documentos 36 e 45 |
| Arrecadação (nº 192) | A instituição financeira centralizadora entrega aos entes e ao CGIBS os dados dos documentos cancelados e recebe da Receita os dados para a partilha | Sem efeito no ERP |

# 4. O que o dicionário não cobre e as decisões propostas

Cada decisão tem a recomendação indicada; quem não responde segue a recomendação. Nenhuma altera estrutura de forma ampla: são campos novos e valores novos de enumeração.

| ID | O que falta | Proposta | Recomendação |
|---|---|---|---|
| D-N106 | O regime de caixa deixa de existir a partir de 2027 (art. 8º da Resolução nº 190), mas `Cad_Simples_Opcao.Regime_Apuracao` e `Mov_Simples_Apuracao.Regime_Apuracao` aceitam `caixa` sem limite, e `Mov_Simples_Receita_Mensal` guarda a receita recebida do regime de caixa | Sem campo novo: o valor `caixa` fica para competências até 12/2026 e retificações; a validação rejeita `caixa` de 01/2027 em diante. Confirmar com o contador, porque o texto dos artigos revogados não veio | Sim |
| D-N107 | O Anexo XIII traz ICMS, ISS, CBS e IBS fixos do MEI, mas `Cad_Mei_Parametro` e `Mov_Mei_Das` só têm ICMS e ISS | `Valor_Cbs` e `Valor_Ibs` nas duas entidades; a tabela de valores entra como carga com vigência: 2027 e 2028, ICMS 1,00, ISS 5,00, CBS 0,994 e IBS 0,006; 2029, 0,90, 4,50, 1,00 e 0,20; 2030, 0,80, 4,00, 1,00 e 0,40; 2031, 0,70, 3,50, 1,00 e 0,60; 2032, 0,60, 3,00, 1,00 e 0,80; de 2033, só CBS 1,00 e IBS 2,00. O texto não diz se CBS e IBS valem uma vez por MEI ou por atividade: o Manual do DAS-MEI de 2027 diz | Sim, os dois campos |
| D-N108 | `Mov_Simples_Apuracao_Atividade.Tipo_Segregacao` tem `pis_cofins_monofasico`, que acaba com o PIS e a Cofins em 2027, e nenhum valor de IBS e CBS | Valores novos: `ibs_cbs_concentrada`, `ibs_cbs_st_ou_antecipado`, `ibs_cbs_sem_icms` (bens com IBS e CBS sem ICMS, art. 25, § 1º, I-A), `ibs_cbs_sem_iss` (serviços e bens imateriais com IBS e CBS sem ISS, § 1º, X) e `ibs_cbs_imune_ou_reduzido`. O art. 30, citado no art. 25, § 10-A, não veio; a lista final sai dele e do Manual do PGDAS-D de 2027 | Sim, com a lista a conferir |
| D-N109 | `Cad_Simples_Limite.Tipo_Limite` não tem o sublimite mensal do início de atividade (R$ 300 mil por mês, arts. 12 e 24) | Valor novo `sublimite_inicio_atividade_mensal`; o valor é carga com vigência | Sim |
| D-N110 | As informações anteriores à opção (arts. 144-D e 144-E): receita e folha de 12/2025 a 11/2026 até **20/12/2026** e de 12/2026 até **20/01/2027**; sem manifestação, valem os valores que a Receita pré-preencheu (EFD-Contribuições e eSocial) | Sem entidade nova: valor novo `informada_receita_anterior_opcao` na `Origem` de `Mov_Simples_Receita_Mensal` e de `Mov_Simples_Folha_Mensal`; os dois prazos em `Mov_Obrigacao_Prazo_Empresa`. Só interessa a quem ingressa em 01/01/2027 ou vem do MEI | Sim, se houver cliente nessa situação (pergunta P-R4-01) |
| D-N111 | A declaração assistida do PGDAS-D (art. 38-A) não tem lugar: `Mov_Simples_Apuracao` não diz se a declaração foi calculada pelo ERP ou pré-preenchida pela Receita | Campos `Origem_Declaracao` {calculada_erp, assistida_rfb} e `Diferenca_Conferencia` (número, opcional) em `Mov_Simples_Apuracao`, para comparar o ERP com a Receita, no mesmo espírito do espelho da CBS (D-N37) | Sim |
| D-N112 | Quando a empresa opta pelo regime regular, o DAS deduz as parcelas de CBS e IBS (art. 22-A), e `Mov_Simples_Apuracao_Tributo` não mostra o que ficou de fora | Campo `Valor_Deduzido_Regime_Regular` (número, opcional) em `Mov_Simples_Apuracao_Tributo` | Sim |
| D-N113 | **A**: DeSTDA, seção 6 deste documento. **B**: `Cad_Empresa` não guarda a data de inscrição no CNPJ, que a nova redação do art. 2º define como data de início de atividade e da qual dependem a RBT12 proporcional, o sublimite do início de atividade, o fator "r" de 0,28 e o efeito da opção do regime regular de empresa nova (art. 40-D, §§ 3º e 4º) | **A**: ver seção 6. **B**: campo `Data_Inicio_Atividade` (data, opcional) em `Cad_Empresa`, com a data de inscrição no CNPJ | Sim |

A decisão D-N106 é a única que depende de texto que não chegou. As demais saem do texto da Resolução nº 190 e da DeSTDA do Ajuste SINIEF.

# 5. Conferido sem mudança, e dois pontos a verificar

Conferi contra o dicionário e não achei lacuna em: a receita por emissão do documento (derivada das notas, sem lançamento paralelo), o sublimite por tributo (`Cad_Simples_Limite.ID_Imposto`), as faixas e a partilha por vigência (`Cad_Imposto` já tem IPI, CBS e IBS), o regime regular por semestre (`Cad_Participante_Regime_Ibs_Cbs`, com os quatro campos do documento 35), as informações anuais no PGDAS-D (`Mov_Simples_Declaracao_Anual.Tipo`), o DAS avulso e os demais (`Mov_Simples_Das.Origem`), a retenção de ISS e os prazos de opção e cancelamento (`Mov_Obrigacao_Prazo_Empresa` e `Cad_Obrigacao_Prazo_Entrega`).

Dois pontos a verificar na construção, sem decisão agora: (1) o art. 58, §§ 4º a 6º, dá ao não optante, como a Mlegate nas compras, o crédito de IBS e CBS no valor cobrado pelo regime único, com a alíquota no documento do fornecedor; o item de nota de entrada (`Mov_Nota_Fiscal_Entrada_Item`) tem o valor do crédito, mas não achei um campo para a alíquota que o optante informou; confere com o leiaute da NF-e quando a construção chegar nele. (2) A regra do art. 40-E (vedação do regime único a quem recebeu ressarcimento) depende de `Mov_Perdcomp` e `Mov_Credito_Fiscal` e é só validação.

# 6. DeSTDA: Ajuste SINIEF 12/2015 contra o documento 39

O documento 39 desenhou a DeSTDA sem ter o Ajuste, apenas com a página da SEFAZ-SP. O Ajuste confirma o desenho e traz quatro correções.

| Ponto do Ajuste | Documento 39 e dicionário | Resultado |
|---|---|---|
| Cláusula primeira, § 4º: quatro tipos de imposto: ST retido como substituto (antecedente, concomitante e subsequente), antecipação nas aquisições interestaduais, ICMS da diferença de alíquota nas aquisições interestaduais de bens fora da antecipação e **ICMS devido nas operações e prestações interestaduais destinadas a consumidor final não contribuinte** | `Mov_Destda_Apuracao_Uf.Tipo` tem `substituicao_tributaria`, `difal` ("entrada") e `antecipacao` | **Falta o quarto tipo**, o ICMS das vendas interestaduais a consumidor final não contribuinte. Proposta: `difal` passa a `difal_entrada` e entra `difal_consumidor_final`. Se o leiaute (Ato COTEPE 47/15) separar os subtipos de ST, o campo de tipo acompanha |
| Cláusula terceira: obrigados são os optantes do Simples, exceto MEI e os estabelecimentos impedidos de recolher ICMS pelo Simples por excesso do sublimite estadual; vale para todos os estabelecimentos, para a UF de origem e para cada UF em que haja inscrição de substituto | `Cad_Destda_Parametro_Uf.Exigida` por UF | Cobre a UF. As duas exceções saem de `Cad_Participante_Porte` e de `Mov_Simples_Receita_Mensal.Excesso_Sublimite`: regra de validação |
| Cláusula terceira, §§ 3º e 4º: a UF pode dispensar ou postergar a exigência, e revogar a dispensa a qualquer tempo | `Exigida` com vigência | Coberto |
| Cláusula quinta: um arquivo por estabelecimento; estabelecimentos da mesma UF com escrituração centralizada por convênio, protocolo ou ajuste entregam um só | `Mov_Destda_Apuracao_Uf.ID_Filial` | **Falta** indicar a escrituração centralizada: campo `Escrituracao_Centralizada` (booleano) em `Cad_Destda_Parametro_Uf` |
| Cláusula sétima, § 2º: gera-se declaração mesmo sem dados quando o contribuinte não informa valor para uma UF no período | `Dispensa_Sem_Valor` por UF | Coberto, com ressalva: o padrão do Ajuste é entregar vazia; a dispensa de São Paulo é regra da UF (página da SEFAZ-SP), então o padrão do campo fica falso |
| Cláusulas nona e décima: validação de leiaute e assinatura antes do envio; recepção pelo aplicativo, por webservice da UF ou pelo programa TED da SEFAZ do Rio Grande do Sul; recibo na recepção, ou a causa da falha | `Canal` {aplicativo_sedif_sn, portal, outro}; `Mov_Escrituracao_Arquivo` e suas ocorrências | Coberto; proposta de dois valores novos em `Canal`: `webservice_uf` e `programa_ted` |
| Cláusula décima primeira: prazo no dia 28 do mês seguinte (dia 20 até 30/09/2016) ou primeiro dia útil | `Dia_Entrega` | Coberto |
| Cláusula décima segunda: retificação por arquivo substitutivo integral, sem arquivo complementar, até o prazo livremente e depois conforme a UF; um arquivo por período e UF | `Mov_Escrituracao_Arquivo.Finalidade` {original, substituta} | Coberto; a regra de "sem complementar" é validação |
| Cláusula primeira, §§ 2º e 3º: assinatura digital ICP-Brasil, dispensada de quem não é obrigado a documento fiscal eletrônico, que usa código de acesso e senha | `ID_Certificado` opcional; `Referencia_Cofre_Credenciais` | Coberto |
| Cláusula décima sexta: quem entrega a DeSTDA não entrega a GIA-ST | Sem campo | Regra para o calendário: não gerar o alerta da GIA-ST para a empresa obrigada à DeSTDA |

O leiaute do arquivo está no **Ato COTEPE 47/15**, que o Ajuste cita e que não veio. A seção do documento 39 sobre o campo a campo continua aberta até ele chegar.

## 6.1 Manual DeSTDA 2016 (SEFAZ-SP) contra o desenho

O manual é de 18/02/2016 e descreve o aplicativo SEDIF-SN em São Paulo (Portaria CAT 23/2016). Não traz o leiaute nem os campos de cada aba. Foi lido contra o Ajuste e o documento 39, e **não muda nenhuma das decisões propostas**; confirma pontos do desenho e traz regras de uso.

| Ponto do manual | Documento 39 e dicionário | Resultado |
|---|---|---|
| O aplicativo tem três abas: **ST (Substituto Tributário)**, **ICMS Entrada** e **DA – Venda**. A antecipação e o diferencial de alíquota das aquisições (ativo fixo, uso e consumo) ficam na aba de entrada; o diferencial das vendas interestaduais a não contribuintes fica na aba de venda | `Tipo` em `Mov_Destda_Apuracao_Uf` | Confirma a correção D-N113: o tipo do consumidor final não contribuinte é uma aba própria. O manual de 2016 avisa que essa aba estava **suspensa por medida cautelar na ADI 5.464**; a situação atual dessa parte não está nos materiais, então fica como verificação do contador, e o tipo existe no dicionário como parâmetro com vigência por UF |
| A entrada se divide em antecipação **sem encerramento** (só o diferencial de alíquota é recolhido antes) e **com encerramento** (ICMS da cadeia cobrado antecipadamente) | `antecipacao` e `difal` | O dicionário não distingue os dois casos de antecipação. Fica registrado como **dúvida para o leiaute**: se o Ato COTEPE 47/15 separar os dois, o campo `Tipo` ganha o subtipo, como já previsto para a ST |
| A declaração é **por estabelecimento e por inscrição estadual**; só se preenche o mês em que o estabelecimento foi optante; se a empresa mudou de IE em maio, a IE antiga vale até maio e a nova de junho em diante | `ID_Filial` em `Mov_Destda_Apuracao_Uf`; `Cad_Participante_Inscricao` tem `estadual` e `estadual_substituto` com vigência | Coberto: a IE que vale na competência sai da vigência de `Cad_Participante_Inscricao`. É regra de geração: usar a inscrição vigente na competência, e não gerar mês em que a empresa não era optante |
| O cadastro do aplicativo guarda dados cadastrais, responsáveis, contabilistas e as IE de substituto em outras UFs; mudança cadastral só vale se feita pelos trâmites da SEFAZ (Cadesp), nunca só no aplicativo | `Cad_Participante_Inscricao`, `Cad_Participante` e responsáveis já existentes | Coberto; a fonte do cadastro é o ERP, e a mudança no aplicativo não é registro oficial |
| Finalidade do documento: **original** ou **substituto**; conteúdo **com** ou **sem dados informados** (declaração sem movimento) | `Finalidade` {original, substituta}; `Sem_Valores` | Coberto |
| Passos de envio: preencher, "Assinar", "Transmitir", "Iniciar processamento" | `Mov_Escrituracao_Arquivo` e suas ocorrências | Coberto |
| As guias são emitidas no portal da SEFAZ-SP: **GARE** ou **GNRE** | `Mov_Destda_Pagamento.Tipo_Guia` {gare, gnre} | Coberto |
| A substitutiva **repete os dados corretos e corrige os errados** e fica sujeita a homologação posterior | `Finalidade` = substituta | Regra de geração: o arquivo substitutivo leva a declaração inteira, não só a diferença |
| Omissão pode gerar autuação pelo art. 527 do RICMS-SP, processo de cassação por inatividade presumida e pendência para a AIDF | Sem campo | Sem mudança no dicionário; entra no texto do alerta do calendário (consequência do atraso) |
| O manual fixa o prazo no **dia 20** | `Dia_Entrega` | **Desatualizado.** O Ajuste, com a redação vigente desde 01/10/2016, fixa o dia 28. Vale o Ajuste e a legislação de cada UF; o manual é só de 2016 |
| A STDA do ano-base 2015 e a STDA 2016 (até 31/10/2016) | Sem campo | Histórico de 2016, sem efeito no ERP |

Ficam de fora do desenho, por serem informações de 2016 sobre o aplicativo: o endereço do Posto Fiscal Eletrônico e as telas do SEDIF-SN.

# 7. Prazos novos ou confirmados

| Data | O que vence | Fonte |
|---|---|---|
| 01/11/2026 | NFS-e Nacional obrigatória para ME e EPP (Resolução nº 191); a nº 189 está revogada | Resolução nº 191, art. 3º |
| até 30/11/2026 | Cancelamento da opção pelo Simples e do regime regular do 1º semestre de 2027 (irretratável; a CGSN pode ajustar o prazo) | Resolução nº 190, arts. 6º e 40-D |
| **20/12/2026** | **Receita e folha de 12/2025 a 11/2026 de quem ingressa no Simples em 01/01/2027 (ou vem do MEI): conferir, alterar ou completar no PGDAS-D** | Resolução nº 190, art. 144-E, I |
| 01/01/2027 | Efeitos da Resolução nº 190: IBS e CBS no Simples, faturamento por emissão, fim do regime de caixa, Anexos de 2027 e valores do MEI | Resolução nº 190, art. 9º |
| **20/01/2027** | **Receita e folha de 12/2026 das mesmas empresas** | Resolução nº 190, art. 144-E, II |
| janeiro de cada ano (até o último dia útil) | Opção do MEI já inscrito, com efeito no ano-calendário | Resolução nº 190, art. 102, II |
| 01/03 a 31/03/2027 | Opção pelo regime regular para o semestre de julho (efeito em 01/07/2027); cancelável até 31/05/2027 | Resolução nº 190, art. 40-D |
| 01/09 a 30/09 de cada ano | Opção pelo Simples e pelo regime regular do semestre de janeiro seguinte | Resolução nº 190, arts. 6º e 40-D |
| dia 10 do mês seguinte | Declaração assistida do PGDAS-D, quando a Receita a disponibilizar | Resolução nº 190, art. 38-A |

# 8. O que ainda falta

1. **Manual do PGDAS-D e do DAS-MEI de 2027** (cálculo com IBS e CBS, segregações, valores do MEI por atividade): fecha D-N107 e D-N108.
2. **Art. 30 da Resolução CGSN nº 140** (receitas com imunidade e outros tratamentos de IBS e CBS), citado no art. 25, § 10-A: fecha a lista de D-N108.
3. **Texto dos artigos revogados sobre o regime de caixa** (arts. 16, 17, 18, 19 e 20 da Resolução nº 140, redação anterior): confirma D-N106.
4. **Ato COTEPE 47/15** e o manual **atual** do SEDIF-SN (o de 2016 chegou, mas é de uma versão antiga e sem os campos): leiaute da DeSTDA e situação atual do diferencial de alíquota das vendas a não contribuintes.
5. A Resolução nº 140 consolidada, com a redação que vale a partir de 2027, para conferir o conjunto (as Resoluções nº 190 a 192 só trazem os trechos alterados).

# 9. Perguntas para Alberto

| ID | Pergunta | Se não responder |
|---|---|---|
| P-R4-01 | Algum cliente (ou a própria Mlegate) ingressa no Simples em 01/01/2027, ou sai do MEI para o Simples? Se sim, o prazo de **20/12/2026** vale para ele | Sem apoio específico ao módulo "Receitas Anteriores à Opção"; só o valor de `Origem` e os prazos |
| P-R4-02 | O contador confirma que o regime de caixa acaba mesmo em 2027? (as notícias dizem sim; o texto dos artigos revogados não veio) | Vale o fim do regime de caixa para competências de 01/2027 em diante (D-N106) |

# 10. Fontes e verificação

**Oficiais.** Resoluções CGSN nº 190, 191 e 192, de 04/08/2026 (DOU de 10/08/2026, edição extra 149-A), lidas inteiras. Ajuste SINIEF 12/2015 (texto do CONFAZ, enviado por Alberto) e Manual DeSTDA 2016 da SEFAZ-SP (atualizado em 18/02/2016), lidos inteiros.

**Secundárias, a conferir.** [Fenacon, "Regime de caixa deixará de ser utilizado na apuração do Simples Nacional"](https://fenacon.org.br/noticias/regime-de-caixa-deixara-de-ser-utilizado-na-apuracao-do-simples-nacional/) e [Guia Tributário, 17/08/2026, "Opção pelo regime de caixa será extinta a partir de 2027"](https://guiatributario.net/2026/08/17/simples-nacional-tributacao-pelo-regime-de-caixa-sera-extinto-a-partir-de-2027/) (a segunda só vi no resultado da busca). Elas dizem o que o art. 8º da Resolução nº 190 sugere pelos dispositivos revogados.

**Verificação feita.** Conferi cada entidade e campo citado contra o dicionário de 829 entidades (a lista da seção 4 saiu de uma consulta ao modelo, e as entidades citadas existem). Somei as colunas do Anexo XIII de cada vigência, e os totais batem (7,00; 6,60; 6,20; 5,80; 5,40; 3,00). Os números das duas partilhas e das faixas dos Anexos I a V foram lidos, não conferidos um a um: a carga de dados deve ser feita direto do texto oficial, com conferência por amostra.

**Não verificado.** O conteúdo dos dispositivos revogados da Resolução nº 140, o art. 30, o Manual do PGDAS-D de 2027, o leiaute da DeSTDA e a situação atual do diferencial de alíquota das vendas a não contribuintes (o manual de 2016 cita só a suspensão cautelar da época).
