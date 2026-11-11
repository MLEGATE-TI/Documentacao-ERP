# Plataforma da CBS, Regime Regular do Simples e Cooperativas — Documento 36

*Leitura dos 12 materiais oficiais que Alberto enviou em 05/10/2026 (Resolução CGSN nº 189, manuais do Simples e das cooperativas, Manual RTC, Manual da Plataforma CBS, Apuração Assistida, Glossário e Ambiente Beta) e o que eles pedem do dicionário. Revisão de 06/10/2026 (seção 12): APIs de apuração da CBS na versão 2 e Resoluções CGSN nº 190 e nº 191/2026. Proposta e perguntas: nada foi consolidado. O dicionário só muda depois do seu "consolidar".*

*Nota de 12/10/2026 (documento 48): chegou o texto oficial das Resoluções CGSN nº 190, 191 e 192. A Resolução nº 191 **revoga a nº 189** (seção 3 deste documento) e repete as regras do art. 59 da nº 140 com efeitos a partir de 01/11/2026 (não mais 01/09/2026); as seções 3 e 12.2 foram lidas contra o texto e confirmadas, com os pontos novos (fim do regime de caixa, Anexo XIII do MEI, receitas anteriores à opção até 20/12/2026 e 20/01/2027, declaração assistida) tratados no documento 48. O texto abaixo não foi reescrito.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Os materiais trazem três coisas. A primeira é o **texto oficial da Resolução CGSN nº 189/2026**, que confirma a obrigatoriedade do Emissor Nacional para ME e EPP e traz regras que o desenho ainda não tinha (opção pendente e impedimento também emitem pelo nacional, vedação em operação só de ICMS). A segunda são **dois prazos que já estão correndo**: a opção das cooperativas pelo regime específico fecha em 31/10/2026, e o cancelamento da opção pelo regime regular de IBS/CBS no Simples vai de 02/11 a 30/11/2026, em caráter irretratável. A janela de opção do Simples e do regime regular para 2027 fechou em 30/09/2026. A terceira é a **Plataforma da CBS** (Receita Federal): a Apuração Assistida, a API de débitos, a Calculadora de Tributos e as formas de extinção do débito (Split Payment, RAD, PCONT). Em 2026 ela é simulada, sem pagamento real, mas o ERP precisa de um espelho dela para conferir a própria apuração.

A proposta é pequena: **4 entidades novas** (mais 2 opcionais, se houver cooperativa entre os clientes), campos novos em 4 entidades existentes e 7 decisões (D-N35 a D-N41). O dicionário já tinha `Cad_Participante_Regime_Ibs_Cbs` (regime híbrido do Simples), `Cad_Participante_Regime_Especifico`, `Mov_Credito_Fiscal`, `Mov_Perdcomp` e `Cad_Certificado_Digital`; eles cobrem boa parte do que os manuais descrevem.

# 2. Fontes lidas

| Arquivo | O que é | Uso |
|---|---|---|
| Resolução CGSN nº 189, de 23/04/2026 (DOU de 28/04/2026, p. 52) | Texto oficial; altera os arts. 59 e 79 da Resolução CGSN nº 140/2018 | Obrigatoriedade da NFS-e Nacional para ME e EPP (seção 3) |
| Manual da Opção pelo Regime Regular do IBS e da CBS no Simples Nacional (versão de 18/09/2026) | Passo a passo do portal | Eventos e prazos do regime híbrido (seção 4) |
| Roteiro da Opção pelo Regime Específico, Sociedades Cooperativas (v1.1, 15/09/2026) | Passo a passo, com leiaute do arquivo de associados | Seção 5 |
| Manual RTC (versão I, 13/01/2026), Manual da Plataforma da CBS (maio/2026), Comunicado do Ambiente Beta (v1, 26/12/2025), Apuração Assistida (Primeiros Passos 1 e 2, jul/2025), Glossário RTC (versão III, maio/2026) | Documentação do projeto piloto da CBS | Seção 6 |
| Documento XML de NF-e (14/11/2025, schema PL_010b) | Exemplo com IBS/CBS | Conferência de campos (seção 7) |
| Manual dos Contribuintes, API do Emissor Público Nacional (v1.2, out/2025) | Mesma versão que você já tinha enviado | Sem novidade |

Duas cópias idênticas (a página do DOU e o manual da API) foram removidas dos uploads. O XML de exemplo é fictício e os totais não batem com o item (item de R$ 22,90 e total de R$ 25,90): serve para conferir estrutura, não valores.

# 3. Resolução CGSN nº 189/2026

O texto oficial altera o art. 59 da Resolução CGSN nº 140 e entra em vigor em **01/09/2026**.

| Regra | O que diz | Efeito no desenho |
|---|---|---|
| Obrigatoriedade (§ 1º) | A ME ou EPP optante usa **obrigatoriamente** a NFS-e de padrão nacional, pelo emissor web ou por API | Confirma a rota do ERP por API para o cliente do Simples |
| Casos equiparados (§ 1º-A) | Também emite pelo nacional a ME ou EPP com opção pendente ou em discussão administrativa que possa gerar inclusão retroativa, e a que está sob efeito de impedimento (art. 12) | `Cad_Autoridade_Fiscal_Atendimento` ganha o motivo da rota: optante, opção pendente, discussão administrativa ou impedimento |
| Vedação (§ 1º-B) | É vedado à ME e à EPP emitir NFS-e em operação sujeita **apenas** ao ICMS | Regra de validação na emissão: bloquear NFS-e de optante do Simples quando o item for só de ICMS |
| Validade (§ 1º-C) | A NFS-e vale em todo o território nacional e basta para fundamentar e constituir o crédito tributário | Sem campo novo; reforça guardar o XML autorizado |
| Acesso dos entes (§§ 1º-D e 1º-E) | Municípios acessam pelo Painel Municipal e pelo ambiente compartilhado, com requisitos mínimos de segurança | Sem efeito no ERP |

A Resolução **não cita MEI** e **não traz a data de 01/11/2026**: ela fixa 01/09/2026, e a Prefeitura de São Paulo informa que a data do Simples no município foi adiada para 01/11/2026 pela Resolução CGSN nº 191, de 04/08/2026, que ainda não recebi. O documento 35 já usa 01/11/2026 por essa fonte.

# 4. Regime regular do IBS e da CBS no Simples (regime híbrido)

Por padrão, o optante do Simples apura IBS e CBS "por dentro" do DAS. Quem quer recolhê-los "por fora" opta pelo regime regular (híbrido). A opção abre em **setembro e março** de cada ano. Para 2027 a janela foi de 01/09 a 30/09/2026, e o regime começa em 01/01/2027. O cancelamento da opção do 1º semestre de 2027 vai de 02/11/2026 (previsão) a **30/11/2026**, e é irretratável. Quem ainda não é optante do Simples precisa optar primeiro (01/09 a 30/09/2026); mesmo com a opção pendente, pode pedir o regime regular até 30/09/2026.

O histórico do portal mostra, por solicitação: evento (opção, renúncia, inclusão administrativa, inclusão judicial), regime (regular de IBS e CBS, regular só de CBS, ou outros que surjam), data do evento, data de efeito, data do fato motivador (em processo administrativo ou judicial), origem (contribuinte ou de ofício), cancelada, fim do período e comprovante em PDF.

`Cad_Participante_Regime_Ibs_Cbs` já tem Semestre_Referencia, Regime, Data_Opcao, Data_Cancelamento, Bloqueado_Retorno_Ate e vigência. Faltam quatro campos, que proponho acrescentar: **Tipo_Evento** {opcao, renuncia, inclusao_administrativa, inclusao_judicial}, **Origem** {contribuinte, oficio}, **Data_Fato_Motivador** e **Comprovante** (referência do arquivo em PDF). O domínio de Regime passa a aceitar "regular só de CBS". Os prazos (30/09, 30/11 e março) são guardados para gerar alerta (decisão D-N40, respondida em 12/10/2026); como `Cad_Obrigacao_Acessoria` não tem campo de data, entram em `Cad_Regra_Vencimento` e `Cad_Obrigacao_Prazo_Entrega` (documento 46, seção 6), e o cálculo lê o registro da decisão com vigência, não o prazo.

# 5. Sociedades cooperativas (regime específico)

Fundamento: arts. 271 e 272 da LC 214/2025, arts. 391 a 395 do Decreto nº 12.955/2026 e da Resolução CGIBS nº 6/2026. No regime específico as alíquotas de IBS e CBS ficam reduzidas a zero nas operações que a lei prevê. A opção vale de **01/09 a 31/10** do ano anterior e produz efeito em 1º de janeiro seguinte; para 2027 o prazo final é **31/10/2026**. O deferimento exige a **listagem de associados** com a data de admissão. O arquivo é texto com separador ponto e vírgula: `REG001` (tipo de registro com 6 posições, `NUM_IDENTIFICADOR` com CPF ou CNPJ do associado em 14 posições, `DATA_ADMISSAO` em DDMMAAAA) e `REG099` (totalizador de 6 posições, igual à quantidade de `REG001`). A transmissão é assinada com certificado e gera recibo. A cooperativa pode cancelar a opção até o último dia do prazo.

`Cad_Participante_Regime_Especifico` (Tipo_Regime_Especifico, Papel, vigência) já guarda a opção. Faltam a lista de associados e o controle do envio. Proponho, **só se houver cooperativa entre os clientes** (decisão D-N39), duas entidades: `Cad_Cooperativa_Associado` (com vigência: cooperativa, documento do associado, data de admissão e de saída) e `Mov_Cooperativa_Listagem_Envio` (ano de efeito, quantidade de registros, hash do arquivo, recibo, data de transmissão e situação).

# 6. Plataforma da CBS

O piloto da Reforma Tributária (Receita Federal) opera em ambiente **Beta** (janeiro a dezembro de 2026), com os documentos fiscais reais alimentando a apuração, mas **sem pagamento real**: em 2026 o destaque de CBS (0,9%) e de IBS (0,1%) é declaratório e não soma ao total da nota. O ambiente definitivo vem em 2027. Os pontos que interessam ao ERP:

| Tema | O que os manuais dizem | Cobertura no dicionário e proposta |
|---|---|---|
| Apuração Assistida (AA) | Processa os documentos por data de emissão, a cada 10 minutos. Situação do período: em andamento, período de ajuste (em janeiro/2026, de 01 a 25/02) e concluída. Contas do resultado: débitos, redutores de débitos, créditos apropriados, redutores de créditos apropriados e pagamentos utilizados; o saldo atualizado, o pedido de ressarcimento e o saldo credor para o período seguinte | **Lacuna.** `Mov_Cbs_Apuracao_Espelho` (empresa, período, situação, última sincronização, intenção de ressarcimento) e `Mov_Cbs_Apuracao_Espelho_Conta` (aba, conta, valor), para conferir a apuração do ERP contra a da Receita |
| API de débitos | Três passos: token (`https://api.receitafederal.gov.br/token`, válido por 1 hora, com ClientId e ClientSecret), tíquete (`/rtc/apuracao-cbs/v1/{cnpj}`, com 8 dígitos do CNPJ e webhook; **2 por dia**, erro 429 ao exceder) e download (`/rtc/download/v1/{tiquete}`, **8 por dia**, um acesso por tíquete, arquivo disponível por 24 horas). Em maio/2026 só "Consultar débitos" está disponível; créditos, pagamentos e conclusão ainda não. Os campos do JSON **não constam** | **Lacuna.** `Cad_Autoridade_Fiscal_Credencial` (ClientId e referência do segredo no cofre, nunca o segredo) e `Mov_Cbs_Download` (tíquete, solicitação, download, chamadas consumidas, situação, hash e referência do arquivo bruto). O limite diário entra como campo de `Cad_Autoridade_Fiscal_Servico`. O desenho do JSON espera o leiaute |
| Calculadora de Tributos | Código aberto, **sem API pública hospedada**: o ERP integra pelo componente offline (Docker, JAR com Java 21 ou WSL), com API local em `localhost:8080/api`. Entrada: CST, cClassTrib, NCM ou NBS, local e data do fato gerador. Saída: alíquota, redução, base, CBS, IBS estadual e municipal, memória de cálculo e referência normativa | Campos novos `Memoria_Calculo` e `Referencia_Normativa` na linha de apuração por item (`Mov_Apuracao_Tributo_Item`). O componente é um serviço de `Cad_Autoridade_Fiscal_Servico` do tipo local (decisão D-N36) |
| Extinção do débito | **Split Payment** (separação na liquidação financeira), **RAD** (recolhimento pelo adquirente, vinculado a uma operação, mínimo de R$ 10,00, gera crédito ao adquirente) e **PCONT** (pagamento do contribuinte, aplicado em ordem cronológica). DARF simulado desde 19/05/2026, sem QR Code | Já tratado no documento 10 (RAD e split payment). Ligar o espelho às baixas existentes; sem entidade nova (decisão D-N37) |
| Crédito | Só é apropriado quando o débito do fornecedor é **extinto**; antes é "a apropriar". Estados: a apropriar, apropriado, utilizado, inapropriável. Tipos: básico, presumido, ressarcível e não ressarcível por base legal | `Mov_Credito_Fiscal.Status` ganha esses estados e a modalidade de extinção |
| Ressarcimento e transferência | Pedido na AA gera PER/DCOMP automático; "intenção de ressarcimento" reserva créditos. Excesso de pagamento gera **transferência automática** em até 3 dias úteis, por chave PIX | `Mov_Perdcomp` cobre o pedido. A transferência vira conta do espelho; a conciliação com o extrato bancário seria feita na Tesouraria (a confirmar) |
| Notas que corrigem a apuração | Nota **complementar** (finalidade 2, mesma partes, chave referenciada, só o acréscimo) e **nota de débito** (finalidade 6, tipos 02 anulação de crédito, 04 multa e juros, 06 pagamento antecipado e 07 perda em estoque). Pagamento antecipado é fato gerador. Evento de perecimento, perda, roubo ou furto estorna crédito | Já são lacunas do documento 34 (`tpNFDebito`, `tpNFCredito`, `gPagAntecipado`, eventos de perecimento). Estes manuais confirmam os quatro tipos de débito |
| Simples na AA | Aparece como regime regular, só informativo, sem crédito | Sem efeito |
| Acesso | Login gov.br prata ou ouro; representação por e-CNPJ, representante legal ou procurador digital; "Autorização de Acesso" vale após o aceite e pode ser cancelada | `Cad_Certificado_Digital` já existe; sem campo novo |

# 7. Conferência do XML de exemplo

Li as 128 tags do XML (schema PL_010b, NT 2025.002 v1.30). **Todas** estão na classificação do documento 34: 71 cobertas, 44 derivadas, 4 por entidade nova, 1 só no XML e 8 que já eram lacuna (`tpImp`, `finNFe`, `indIntermed`, `cEANTrib`, `uTrib`, `qTrib`, `vUnTrib` e `infCpl`). O exemplo usa emitente com CRT 2 (excesso de sublimite do Simples), `IBSCBS` com CST 000 e cClassTrib 000001, `IBSCBSTot` e `vNFTot`, e a observação do art. 20, § 1º, da LC 123. Não achei campo novo.

# 8. Decisões que preciso de você

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N35 | Integrar com a API de débitos da Apuração Assistida agora, só em leitura? | Sim, só leitura e espelho. Em 2026 não há pagamento real; o JSON de retorno ainda não tem leiaute publicado |
| D-N36 | Usar o componente oficial da Calculadora? | Como **conferência**: o cálculo principal continua próprio, e o resultado do componente (com a memória de cálculo) é guardado por item para comparar |
| D-N37 | Espelho da AA em entidades próprias (2) ou dentro de `Mov_Credito_Fiscal` e `Mov_Apuracao_Tributo_Item`? | Entidades próprias: as contas da Receita não são as do ERP e precisam ser comparadas |
| D-N38 | Histórico do regime regular do Simples: 4 campos novos em `Cad_Participante_Regime_Ibs_Cbs` ou entidade de evento separada? | 4 campos novos (a entidade já tem vigência) |
| D-N39 | Algum cliente da Mlegate é cooperativa? Se sim, aprova `Cad_Cooperativa_Associado` e `Mov_Cooperativa_Listagem_Envio` | **Respondida em 05/10/2026: sim.** As duas entidades entram na revisão 3. **Prazo: 31/10/2026** |
| D-N40 | Guardar os prazos de opção e cancelamento (30/09, 31/10, 30/11 e março) em `Cad_Obrigacao_Acessoria` para alertar? | **Respondida por Alberto (12/10/2026): sim, guardar, porque cada decisão influencia o cálculo do imposto e dos créditos.** "Sem entidade nova" não funciona: `Cad_Obrigacao_Acessoria` não tem campo de data. O desenho está no documento 46 (seção 6, D-N97): reaproveita `Cad_Regra_Vencimento` e `Cad_Obrigacao_Prazo_Entrega` e cria `Mov_Obrigacao_Prazo_Empresa` |
| D-N41 | DAS avulso e de auto de infração em `Mov_Simples_Das` (Origem, apuração opcional e motivo) ou adiar? | Incluir: são DAS reais que o Contas a Pagar precisa baixar |

# 9. DAS: tipos de emissão (página de serviços do gov.br)

A página "Emitir DAS para pagamento de tributos do Simples Nacional" (gov.br) lista quatro caminhos: o **PGDAS-D** (DAS da apuração mensal), as **Minhas Declarações do Simples Nacional**, o **DAS avulso** (para situações específicas) e o **DAS de Auto de Infração** (infrações lavradas pela Receita Federal). O serviço atende optante do Simples e também quem protocolou **impugnação de exclusão**. A página cobre IRPJ, IPI, CSLL, Cofins, PIS/Pasep, CPP, ICMS e ISS, e não traz formas de pagamento, Pix, segunda via nem juros.

`Mov_Simples_Das` (documento 33) nasce sempre de uma apuração (`ID_Apuracao_Simples`), então **não cobre o DAS avulso nem o de auto de infração**, que não têm apuração do PGDAS-D. Proponho dois campos em `Mov_Simples_Das`: **Origem** {pgdas_d, avulso, auto_infracao} e `ID_Apuracao_Simples` opcional (obrigatório só quando a origem for pgdas_d), mais **Motivo_Avulso** (texto). A situação de quem tem impugnação de exclusão já cabe em `Cad_Simples_Opcao` (Situacao) e na rota do Emissor Nacional (seção 3). Decisão D-N41, abaixo.

# 10. O que ainda falta

1. O texto das **Resoluções CGSN nº 190 e nº 191/2026**. *(06/10/2026: chegou só a notícia da Receita Federal de 11/08/2026, fonte secundária; ver seção 12.)*
2. ~~O leiaute do JSON da API de débitos e o cronograma das demais APIs~~ *(06/10/2026: resolvido pela documentação v2, seção 12; o Swagger oficial continua em falta)*.
3. Os eventos de apuração da AA e os CST além de 000 e 200 (o Beta só processa esses dois).
4. Os Anexos VI e VII da NT 007/2026, o schema da NFCom e o anexo de locação da NFS-e, do documento 34.
5. Divergências a conferir: o Manual RTC fixa o período de ajuste em 01 a 25/02/2026, com conclusão a partir de 26/02, e o Glossário diz 15 dias após o mês; o Comunicado do Beta (de 26/12/2025) cita um "Comunicado Conjunto RFB/CGIBS, de 02/12/2026", provável erro de ano.

# 11. Fontes e verificação

Li os textos extraídos dos PDFs e conferi no original os limites da API (2 tíquetes e 8 downloads por dia, erro 429), os endpoints e as datas do período de ajuste. As entidades propostas foram conferidas por script contra o modelo (539 entidades na época; hoje 543, sem colisão) e contra o documento 33: nenhum nome colide. A Resolução CGSN nº 189 foi lida no texto do DOU. Os resumos da Plataforma da CBS foram feitos por leitura integral dos manuais e conferidos nos pontos acima; o que o texto não diz aparece como "não consta".

# 12. Revisão de 06/10/2026: APIs de apuração da CBS (v2) e Resoluções CGSN nº 190 e nº 191/2026

Alberto enviou três materiais depois deste documento: a notícia do Ministério da Fazenda sobre a nova documentação das APIs de apuração da CBS, a página `docs.receitafederal.gov.br/apuracao-cbs` e a notícia da Receita Federal sobre as Resoluções CGSN nº 190 e nº 191/2026 (publicada em 11/08/2026). Li as duas páginas por WebFetch (resumo do conteúdo, não o Swagger) e o PDF da notícia. O dicionário não foi alterado.

## 12.1 APIs de apuração da CBS, versão 2 (revisa a D-N35)

A versão 2 substitui o desenho de "três passos e dois tíquetes por dia" da seção 6. O que mudou:

| Ponto | Seção 6 (maio/2026) | Documentação v2 (setembro/2026) |
|---|---|---|
| Serviços | Só "Consultar débitos" | **Quatro consultas**: débitos, créditos, pagamentos e recolhimentos. Cronograma: débitos e créditos em outubro/2026; pagamentos e recolhimentos como adquirente em novembro/2026; emissão do DARF de recolhimento do adquirente (RAD) e de pagamento do contribuinte (PCONT) no fim de novembro/2026 |
| Chamada | Token, tíquete e download | **Assíncrona com webhook**: POST com a URL de retorno (HTTPS, validada por HEAD) devolve o tíquete; o processamento leva até 240 minutos; o webhook entrega a URL assinada do arquivo, que fica disponível por 48 horas; há consulta de situação (pendente, em processamento, concluída, erro, com código de erro) |
| Limite | 2 tíquetes e 8 downloads por dia | **4 aberturas por dia** |
| Janela | Não descrita | **8 dias** no máximo por retorno; a primeira consulta devolve desde o dia 1 do mês corrente; o retorno é incremental (só o que mudou desde a última consulta) |
| Acesso | ClientId e ClientSecret | OAuth2 com credenciais do cliente (Client Id e Secret), token Bearer; CNPJ base de 8 dígitos no caminho. Produção em `api.receitafederal.gov.br/apuracao-cbs/v2/...` e ambiente restrito em `/apuracao-cbs-prr/v2/...` |
| JSON | Sem leiaute | **Débitos**: apuração por período com a origem (normal, devolução por PCONT, RAD ou crédito, cancelamentos, perecimento no transporte FOB e CIF e nota de crédito de multa e juros), o documento (55, 57, 62, 63, 64, 65, 66, 67, 91, 92, 93, 94 e 97), a chave e os valores da CBS (apurado, excedente, inexigível, suspenso, extinto e saldo devedor). **Créditos**: apropriação (inapropriável, suspenso, prescrito, a apropriar, apropriado) e utilização (inutilizável, utilizado, restabelecido, não utilizado, com saldo credor e pedido de ressarcimento). **Pagamentos e recolhimentos**: DARF, tipo (contribuinte, adquirente ou split payment) e composição por período, vencimento, chave do documento, principal, multa, juros e total |

**Efeito no desenho.** As duas entidades do espelho propostas na D-N37 (`Mov_Cbs_Apuracao_Espelho` e a linha de débito e crédito) continuam certas, mas agora têm leiaute: a origem do débito, o estado de apropriação do crédito e a composição do DARF viram colunas e domínios, não texto livre. O controle do tíquete (tíquete, situação, código de erro, URL assinada e vencimento da URL) cabe nos campos de controle da camada de integração (documento 31) e não precisa de entidade nova; confirmo isso ao desenhar a consolidação. O limite de 4 aberturas por dia entra como parâmetro com vigência do conector, e a janela de 8 dias como regra de agendamento.

## 12.2 Resoluções CGSN nº 190 e nº 191/2026 (notícia da Receita Federal)

A fonte é secundária: o texto das resoluções continua em falta. A Resolução nº 190 produz efeitos, em regra, a partir de **01/01/2027**; a nº 191 é a que a notícia soma a ela, sem descrever o conteúdo. O que a notícia diz e o que muda no desenho:

| Tema | O que diz | Efeito |
|---|---|---|
| IBS e CBS no Simples | Passam a integrar a lista de tributos do regime; o "Simples híbrido" tira a CBS e o IBS do DAS e os apura pelas regras próprias | Já coberto por `Cad_Participante_Regime_Ibs_Cbs` e pelos campos `regApIBSCBSSN` do documento 41 |
| Prazos de opção para 2027 | Ingresso no Simples: 1º a 30/09/2026, cancelável até 30/11. Regime regular de IBS e CBS no 1º semestre: 1º a 30/09, cancelável até 30/11 (a CGSN pode adiar o cancelamento conforme a publicação da alíquota de referência da CBS). 2º semestre: 1º a 31/03/2027, cancelável até 31/05. A opção continua nos períodos seguintes, salvo renúncia | **A janela de setembro de 2026 já fechou em 30/09.** Falta só o cancelamento (até 30/11/2026). Datas e continuidade como parâmetro com vigência (D-N40) |
| Reconhecimento da receita | O faturamento do Simples passa a seguir a **emissão do documento fiscal** da operação ou da prestação, inclusive entrega futura e documentos que alterem ou complementem valores | A receita bruta do ERP deriva dos documentos emitidos, inclusive das notas complementares e de ajuste; sem lançamento manual paralelo. É o que o documento 41 já faz com `vReceitaBrutaSN` (campo derivado) |
| Receita bruta | Abrange bens materiais e imateriais, direitos e serviços; o IBS e a CBS pagos pelo regime regular **não** entram na receita bruta do Simples. Conceitos de início de atividade, RBT12 e FS12 atualizados | Parâmetro de composição da receita bruta com vigência |
| Sublimite | R$ 3,6 milhões passam a valer também para o IBS (junto com ICMS e ISS); o limite extra de R$ 3,6 milhões para exportação continua; some a referência de R$ 1,8 milhão | Parâmetro com vigência (sem entidade nova); a hipótese do Q-12 do documento 41 (excesso do sublimite estadual) continua sem confirmação |
| Fiscalização | Omissão de receita de origem não identificável: autuação com a maior alíquota. Regras de crédito de ICMS, IBS e CBS do adquirente (LC 123) | Sem entidade nova |
| MEI | Documento fiscal em toda venda de mercadoria e prestação de serviço; NFS-e Nacional para serviço e **Nota Fiscal Fácil** preferencial para mercadoria e certas prestações de transporte | O ERP recebe notas de MEI (crédito presumido do documento 42); a NFF já tem tratamento no documento 34 |
| **DEFIS** | **Deixa de existir como declaração separada**: as informações socioeconômicas e fiscais passam a ser prestadas uma vez por ano, entre janeiro e março, no próprio PGDAS-D | **Responde a dúvida da D-N46.** A DEFIS "campo a campo" vira registro anual dentro da apuração do PGDAS-D, só com o período de janeiro a março; a notícia não diz a partir de que ano-calendário isso vale, então a data fica como parâmetro até o texto da resolução chegar |

## 12.3 Decisões novas

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N81 | Integrar as quatro APIs de apuração da CBS v2 (débitos, créditos, pagamentos e recolhimentos) em leitura, no modelo assíncrono com webhook, OAuth2, limite de 4 aberturas por dia e janela de 8 dias, e desenhar o espelho (D-N37) com as origens, os estados de crédito e a composição do DARF da seção 12.1? A emissão do RAD e do PCONT pelo ERP fica para depois de a API liberar a emissão | **Sim.** Revisa a D-N35 (que previa só débitos e 2 tíquetes por dia). Só leitura e espelho; sem pagamento real em 2026 |
| D-N82 | Tratar as Resoluções CGSN nº 190 e nº 191 como parâmetros com vigência a partir de 01/01/2027 (opções e prazos, receita por emissão do documento, composição da receita bruta, sublimite com IBS) e a DEFIS como registro anual do PGDAS-D (janeiro a março), até o texto das resoluções chegar? | **Sim.** Nada fixo no código; conferir com o texto das resoluções e com o contador quando chegarem |

**Posso consolidar?** (as duas decisões, junto com as D-N35 a D-N41 ainda abertas)
