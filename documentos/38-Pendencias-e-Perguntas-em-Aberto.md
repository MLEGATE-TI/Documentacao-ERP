# Pendências e Perguntas em Aberto — Documento 38 (arquivo único)

**Este é o único arquivo de pendências do projeto** (regra de Alberto, 23/10/2026) e **guarda só o que está em aberto** (pedidos dele de 26/10/2026 e de 12/11/2026): o que já foi respondido ou aplicado saiu daqui e está no documento 14 (histórico de decisões) e nos relatórios de consolidação. **Estado em 16/11/2026** (em 16/11 você enviou 32 respostas parciais do contador, D-N583, e aprovou as Q188-7 a Q188-9, D-N584; resta a Q188-6, seção 1.42): o documento 218 (Bloco 1 de combustíveis e usina, com a cadeia de comercialização, o distribuidor e o Anexo da Resolução 884) foi **aprovado** nas Q218-1 a Q218-17 (D-N581) e **entrou na revisão 44** (documento 219, D-N585; **1.229 entidades e 14.261 campos**), sobre a revisão 43 (documento 217; 1.220 e 14.154); na **versão 2.2** (D-N582) a Resolução 884 foi conferida no Diário Oficial, que você enviou; a **Q218-18** (Solução de Consulta Cosit 223/2023) você respondeu "Sim" em 16/11/2026 (D-N587; o aviso A22 já estava no desenho) e resta a Q218-8, reduzida ao Ajuste SINIEF (seção 0). As **Q188-7 e Q188-8** (D-N584) e as **Q220-1, Q220-5 e Q221-1 a Q221-13** (D-N588) **entraram na revisão 45** (documentos 222 e 223, D-N589; **1.239 entidades e 14.364 campos**), com o desenho em campos escrito por mim no documento 222. Dos documentos 215 e 216, **só a Q215-5 segue aberta** (seção 1.39) e só trava a carga por UF. As perguntas e pendências do contador ficam somente no documento 188 (**359 perguntas**, C1 a C359). Em 16/11/2026 você também enviou o JSON da NCM, o PDF da NBS 2.0 e o IT 2025.002 v1.70: geradas as **cargas da NCM (15.428 linhas) e da NBS (920 códigos, depois refeita com 1.282 nós na `Carga45`)** e lido o IT (documento 220, D-N586). Depois você enviou 22 tabelas do Portal da NF-e e da Receita, a NT 2023.01 e 12 atos da NBS: geradas a **carga do Portal** (18 CST, 173 cClassTrib, 13 cCredPres, 619 CFOP, 5.571 municípios, 261 países, 68 unidades, 1.031 produtos ANP, 10.516 NCM com unidade estatística e 23 formas de pagamento) e as **propostas** do documento 221 (D-N587). Em 16/11/2026 você respondeu "Q220-1 e Q220-5 - sim para duas" e "Q221-1 a Q221-13 - prosseguir com as recomendações" (D-N588): **aprovadas e consolidadas na revisão 45** (documentos 222 e 223, D-N589; carga na pasta `Carga45-20261116`); resta só a definição de **DIR** (seção 0).

Mlegate · Alberto Beyeler · Novembro de 2026

# 0. Envios e materiais que dependem de você

Os outros envios seus estão na seção 3.2.

| Itens | Situação | O que falta |
|---|---|---|
| Q206-10 (11/11/2026) | Aguarda você (a lista de autopeças não produzidas) | O documento 206 entrou na **revisão 40**; a lista de autopeças não produzidas **não tem arquivo consolidado** e a carga ficou **vazia**. Pelas fontes que li (secundárias), a lista está nos Anexos I e II das Resoluções Gecex 284/2021 (redução) e 285/2021 (isenção, com 2% do valor aduaneiro em pesquisa e desenvolvimento); a 368/2022 só traz as regras; a 762/2025 pôs a alíquota em 0%; a 935/2026 deu vencimento a todos os ex-tarifários (lotes de 31/12/2026 a 30/09/2027). **Não consegui ler o texto oficial** (D-N549, D-N550, C286). Falta você enviar os Anexos (planilha do MDIC) ou os links do Diário Oficial |
| Q209-9 e Q215-5 (11 e 12/11/2026) | O Protocolo ICMS 41/2008 foi lido no documento 215; em 12/11/2026 li também o RICMS do AC, do AM e do DF | Os textos oficiais que ainda faltam para a carga por UF: Anexo X do RICMS-MT e Portaria 195/2019, Anexo 1 do RICMS-BA (para transcrever os valores), lista de itens e regulamento atual de ST do RICMS-PR (o PDF da Resolução SEFA 20/2017 de 12/11/2026 é de 2018 e não traz a lista), Decreto 90.309/2023 de AL e os Protocolos 97/10, 93/26, 94/26 e 96/26 em PDF do CONFAZ; Só trava a carga; a linha de retenção do documento 209 ainda espera o código de receita (C278) |
| Q221-5 (16/11/2026) | Você aprovou tirar `Indicador_Duimp` de `Cad_Cclasstrib`, mas **não disse o que é DIR** (11 classificações permitem o modelo DIR no IT 2025.002 v1.71; o IT define só ABI e DeRE) | Diga o que é DIR (leio como declaração de importação de remessa) ou envie o trecho do IT/NT que o define; o modelo DIR **já entrou na carga da revisão 45 com descrição provisória** (`Cad_Modelo_Documento_Fiscal`) |
| Q218-8 (12/11/2026) | Documento 218 (Bloco 1 de combustíveis e usina) **aprovado** nas Q218-1 a Q218-17 (D-N581). A Resolução ANP 884/2022 **chegou em 12/11/2026, no Diário Oficial** (edição 171, p. 62), e confere com as cópias que eu tinha lido (D-N582); o Ajuste SINIEF 14/2025 segue lido só em fonte não oficial | O **Ajuste SINIEF 14/2025** e o **Ajuste SINIEF 01/92** (CONFAZ ou Diário Oficial). Sem pressa; só conferem o que li |
| Q152-4 (29/10/2026; carga) | "sim": carga provisória das três fórmulas de 2024 (N620 18, N620 19 e N630A 18) | A versão "até 31/12/2025" já passou a valer só em 2025 (`Carga29`). **Faltam as três fórmulas de 2024**: o texto delas está na planilha do leiaute 11 que você enviou antes, e ela não está mais no meu ambiente. **Reenvie a planilha do leiaute 11** (é a parte que resta da Q179-3, seção 1.24) e eu preencho as 3 linhas (`PENDENTE_Formulas_2024.csv`) |

# 1. Para você responder

**Em aberto para você:** 1.3 (Q132-5), 1.4 (Q130-1 a Q130-3, Q130-5, Q93-3b, Q93-8 e Q118-1), 1.4a (Q139-1 e Q139-2), 1.5b (Q140-5b, 5d e 5e e Q180-3), 1.13 (desenhos adiados), 1.24 (Q179-1 e Q179-3), 1.28 (Q160-8 e Q160-9, sem efeito no dicionário), **1.39 (Q215-5, documento 215)**, **1.42 (Q188-6, respostas do contador)** e os itens avulsos das seções 1.6 e 1.7. A numeração foi mantida para não quebrar as referências dos outros documentos; as seções sem pergunta aberta saíram.

## 1.3 Documentos 99, 125, 126, 127, 128, 131, 132 e 135: lucro presumido da ECF, caixa, atividade de presunção e Refis (Q132-5)

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q132-5 | Os **pontos 1 e 2** da pergunta 8 da consulta à Receita (documento 98, seção 3.8; arquivo 08 gerado): a regra do X280 trata as linhas 74 a 77 do P130 como redução, mas a fórmula as chama de demais atividades; e o P130 não tem linha de 38,4%, que o P200 10 inclui. O ponto 3 (orientação da linha 6 citando P130/68) você já aprovou na Q134-6 | Sim (o texto está pronto; o envio é seu) |

## 1.4 Documentos 93, 118 e 130: cadeia do lucro real da ECF e alíquotas 7 e 8 da CSLL (Q130-1 a Q130-5)

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q130-1** | Documento 130: de onde vem o texto que você colou sobre as alíquotas 7 e 8 da CSLL (resposta da Receita com protocolo e data, contador, ferramenta de pesquisa ou outra fonte)? A pergunta 3 do documento 98 foi **enviada**? | Informar a origem; se não for da Receita, manter a pergunta 3 na lista de envio |
| **Q130-2** | Mapeamento código × alíquota a partir de 2028: vale o do manual (3 = 20%, 4 = 15%) ou o do texto (3 = 15%, 5 = 20%)? O texto também usa 15% para o código 3 e para o 4 | Aguardar a Receita (perguntas 3 e 4 do documento 98); de 2028 em diante "a confirmar" |
| **Q130-3** | Usar a tabela de 2026 e 2027 (7: 9% até março e 12% depois; 8: 15% e 17,5%) como parâmetro provisório "a confirmar", calculando em vez de parar e avisar (Q93-5b)? As datas por segmento batem com a IN RFB 2.315/2026 (conferida só por um artigo) | Não ainda; só depois da Q130-1 e se a origem for oficial |
| **Q130-5** | T181 6 e U182 2, código 4 de 2022 em diante: o ERP usa 15% em todos os trimestres, com aviso, enquanto a planilha não for corrigida? | Sim, 15% com aviso, e manter a pergunta 3 (3) na consulta |
| Q93-3b | Você pediu "guardar a composição das linhas". É o **rastro do cálculo** (quais linhas e valores formaram cada linha calculada) ou a **composição pelos lançamentos e contas da Parte A**, como nos registros M310 e M312? | Perguntei antes de desenhar |
| Q93-8 | Escopo das linhas editáveis: o ERP só soma os lançamentos da Parte A feitos pelo contador, ou também **sugere** adições e exclusões? | Só soma agora; sugestão vira documento próprio |
| Q118-1 | A S200 linha 90 (TEF e SAF) também é dividida em duas linhas na carga, pela mesma regra da Q93-1, quando o motor do TEF e SAF entrar? (documento 118, seção 5) | Sim, mesma regra, sem campo novo |

**Do contador, no documento 188:** Q93-7 (C8), Q118-2 (C9), Q122-1 (C11) e Q130-4 (C12).

As leituras das funções do manual são minhas; o teste cobriu só as versões de 2025. O leiaute 13 deve mudar fórmulas (por isso ficam no cadastro).

## 1.4a Documento 139: comparação das fórmulas com a planilha do leiaute 11 (Q139-1 e Q139-2)

A planilha que você enviou (Q136-1) traz 372 fórmulas: 364 são iguais às da carga, 8 diferem e nenhuma falta. As 84 que o manual de 2025 não permitia validar são **idênticas às de 2025**. Cinco das sete divergências do documento 136 já estavam na planilha de 2025. **Substituem as Q136-2, Q136-3 e Q136-4** (documento 136, que continua válido como análise).

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q139-1** | Reescrevo a **pergunta 10** da consulta à Receita (documento 98, seção 3.10) com as divergências na forma do documento 139, seção 4 (cinco herdadas de 2025, uma mudada em 2026, uma linha nova) e gero o arquivo 10? O envio é seu | Sim; a Q136-3 fica substituída por esta |
| **Q139-2** | Das divergências herdadas (N660 5 a 9, N610 3, N660 12.01, N670 12 e M350R 267), o motor segue a **fórmula como publicada** e avisa o contador? | Sim, como publicada, com aviso |

## 1.5b Documento 140: bônus da CSLL do Selo Sintonia (Q140-5b, 5d e 5e e Q180-3)

Ficam abertas as Q140-5b, 5d e 5e (vão à Receita pela pergunta 26 do documento 179) e a Q180-3. As Q140-6a a 6e são do contador (documento 188); o ERP não lança o bônus até ele responder.

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q140-5b, 5d e 5e** | "À vista" é só a cota única? As estimativas abatem no ajuste anual o valor total da guia ou o pago? Os meses de selo contam até o vencimento ou o pagamento, e em que ordem o limite anual é consumido? (documento 180, seção 3) | Cota única até o vencimento; valor total da guia; vencimento para os meses e pagamento para a ordem. Vão à Receita pela pergunta 26 do documento 179 |
| **Q180-3** | **Respondida em parte em 09/11/2026:** a IN RFB 2.316/2026 regulamenta o bônus do Selo Sintonia (arts. 12 e 13) e o PDF da **LC 225** (documento 187) traz o texto do art. 41. **Falta só o ato do Confia** (Q187-3) | Enviar, se existir |

**Do contador, no documento 188:** Q140-6a a 6e, com a Q185-C1 (C212).

## 1.6 Itens avulsos

| Item | Situação |
|---|---|
| D-N250 (DeSTDA: Paraíba com `Exigida` falso desde 01/01/2026 pela EFD-OIE; texto do aplicativo nacional) e D-N251 (MEI: efeito do desenquadramento, data-limite de comunicação, percentual do primeiro alerta; o limite do transportador ficou fora pela Q85-4) | Propostas do documento 85 que nunca tiveram decisão nem aplicação e não constam do documento 14. Esperam a sua resposta; **a parte do contador** (qual das duas leituras vale para a Paraíba; critério de contagem do MEI, por caixa ou por emissão) **está no documento 188** (C213 e C214). O texto completo está na cópia do documento 85 na pasta ERP-Revisao26 |
| Q80-5 (quais clientes equiparados existem, desde quando são obrigados e o que já foi entregue) | Sem resposta registrada; o Módulo 2 de outubro da DES-IF venceu em 10/11/2026 e a resposta dá as primeiras linhas de enquadramento |

## 1.7 Das listas antigas (documentos 38 e 45), sem resposta registrada

| Item | Pergunta | Se não responder |
|---|---|---|
| Q-E | Quais clientes são cooperativas e quantos associados cada uma tem? Já optaram pelo regime específico (prazo de 31/10/2026, já vencido)? A listagem de associados sai do ERP? (D-N39 respondida: há cliente cooperativa; faltam quais e quantos) | Entidades sem carga; sem apoio à listagem de 2026 |
| Q-2 | De onde vem a lista de códigos municipais com alíquotas (Lei 13.701/03)? | Sem carga até haver fonte |
| P46-12 | A Mlegate tem subvenção para investimento concedida hoje? Qual ente, ato e empreendimento? | Sem cadastro inicial |
| D-2, D-3, D-4, D-5, D-7, D-8, D-9, D-11 e D-12 (documento 31) | Decisões técnicas: ordem de implementação (corte mínimo ou completa), identificador bigint ou uuid, competência como `date` com CHECK, mapa de precisão numérica, partição das tabelas, ferramenta de migração, tamanho do texto em chave única, nvarchar e framework de acesso a dados em C#. O DDL já segue a recomendação em D-3, D-4, D-9 e D-11, mas **não há resposta sua registrada** | Segue a recomendação |
| P-19 | Diagramas do modelo ER: Mermaid ou imagem PNG? | Sem resposta registrada |
| P-15 a P-17 e P-33 a P-37 | Confirmar as decisões de 01/10/2026 (provisão da folha, cadastros de vencimento, perfil fiscal, retificação do S-5011 e S-5012, retenções e títulos, pagamento a maior) | Valem como decididas |
| G-10 | Escrituração periódica do IBS/CBS: aguardar o leiaute oficial | Reservar `Cad_Obrigacao_Acessoria` |
| D-N8 | NFS-e do aluguel: a Q85-13 deu as datas (pessoa jurídica locadora em 01/12/2026; pessoa física que abrir CNPJ, em 01/01/2027). Falta o conectivo dos limites da pessoa física ("e" ou "ou") | Premissa do documento 33 |

## 1.13 Desenhos adiados ou ainda sem desenho

| Desenho | Situação |
|---|---|
| **Split payment e PSP** | Adiado por você (D-N282); início previsto em janeiro de 2028 |
| **Carga da lista de autopeças não produzidas e linha de retenção do documento 209** | Esperam a Q206-10 (seção 0) e o código de receita (C278) |

## 1.24 Documento 179: a consulta à Receita, reescrita (Q179-1 e Q179-3 abertas)

O documento 179 (D-N489, 05/11/2026) reúne **26 perguntas** prontas para colar no Fale Conosco da Receita (blocos A a D) e, no anexo, o que não é da Receita. Nada foi enviado; o envio é seu.

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q179-1** | Aprova o conjunto das 28 perguntas para envio, na ordem da seção 2 do documento? (Com as Q192-7 e Q193-1 a Q193-3 aprovadas, o conjunto tem **28 perguntas**: a 10 está fechada, a 5 ganhou quatro funções e entraram a 27 e a 28; os textos novos estão no zip do documento 193.) | **Sim**; as que preferir levar ao contador, apague antes de enviar |
| **Q179-3** | **Recebida a planilha do leiaute 12 (24/09/2026), parte (1).** Conferida no documento 193: a carga confere, as perguntas 1 a 9 do documento 179 estão certas e a **pergunta 10 ficou fechada** (sete pontos). **Falta só a (2): a planilha do leiaute 11 (de 2025)**, que traz o texto de 2024 das N620 18, N620 19 e N630A 18 (Q152-4; seguem provisórias em `PENDENTE_Formulas_2024.csv`). Nenhuma outra tabela está pendente para estas perguntas | Reenviar a planilha do leiaute 11 (ou dizer onde está) |

**Do contador, no documento 188:** Q179-2, o canal das perguntas de interpretação (C215). Alberto aprova só o conjunto da Q179-1.

## 1.28 Documento 160: parâmetros das outras obrigações (Q160-8 e Q160-9, abertas; sem efeito no dicionário)

Duas perguntas, **ambas com recomendação "não"**, que não mudam o dicionário em nenhum dos dois sentidos; se você pedir "consolidar" sem respondê-las, leio como a recomendação.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q160-8 | Quer um parâmetro "a empresa entrega esta obrigação" em cada obrigação? | Não agora: depende da C99 e mexe na geração dos prazos |
| Q160-9 | Quer migrar algum campo de classe a para o valor central (opção A da Q155-2) já nesta rodada? | Não: a opção B vale |

Do contador não há pergunta nova: a C99 (documento 188) já pede a lista de parâmetros por obrigação, e as 61 linhas passam a ser a lista que ele confere e completa.

## 1.39 Documento 215, versão 2.1: ST de autopeças e as variações por UF (Q215-5, aberta)

Você pediu que o ERP respeite a regra de cada estado e que se desenhem **só as variações por UF**, com a carga das tabelas depois. Li o Protocolo ICMS 41/2008 e os textos de **MG, SP, PB, RJ, PA, MA, PI, AP, AL, PR, AM, DF, RR e BA** (depois, em 12/11/2026, li também o **RICMS do AC, do AM e do DF**, a Resolução SEFA 20/2017 do PR e uma resposta de consulta do MT; o texto do Anexo X do MT não sai do site da SEFAZ-MT). Saíram **18 variações**: acordo (41/08, 97/10 ou nenhum, com prioridade quando o item está em dois), MVA (36,56% e 71,78%; 26,50% e 40%; 33,08% e 59,60%; IVA-ST de SP; alíquota fixa de AL; antecipação do PA), MVA ajustada publicada em tabela, método de cálculo, ordem dos preços da base, definição da alíquota interna, remetente do Simples, lista de itens por UF (por CEST ou NCM), prazo e guia por tipo de operação, hipóteses de não aplicação, autorização do fisco de destino, regimes especiais, vigência, onde a UF publica, adicional de fundo e estoque na entrada do regime. O modelo passa a aceitá-las com **7 entidades novas** (`Cad_Icms_St_Acordo_Regra`, `Cad_Icms_St_Uf_Mva`, `Cad_Icms_St_Uf_Base_Criterio`, `Cad_Icms_St_Uf_Recolhimento`, `Cad_Icms_St_Uf_Nao_Aplicacao`, `Cad_Icms_St_Lista_Item` e `Mov_Icms_St_Base_Calculo_Item`), **6 campos novos** (3 em `Cad_Autopecas_Perfil` e 3 em `Cad_Filial_Regime_Icms`), 4 domínios abertos, 18 regras e 18 avisos. Sobre a revisão 42: **1.213 entidades, 14.025 campos, 3.615 campos de referência, 364 domínios e 253 mestres** (soma do ensaio, a conferir). Nada foi aplicado.

As **Q215-1 a Q215-4** e a **Q215-6** foram aprovadas e entraram na **revisão 43** (documento 217; D-N571 e D-N573). Fica aberta só a Q215-5. **O que a leitura de 12/11/2026 trouxe (D-N572):** o MT não implementou a MVA de fidelidade de 36,56%; AC, AM, DF e PR aplicam 36,56% e 71,78%; os percentuais do PA são MVA ajustada, e não antecipação; a tabela do AC tem um valor que não confere com a fórmula (C323). O modelo está no dicionário e **não há carga de UF**; ela entra UF por UF, com os textos oficiais:

| Id | Pergunta | Recomendação |
|---|---|---|
| Q215-5 | Quando for dar a carga, envia os textos oficiais que ainda faltam: o Anexo X do RICMS-MT e a Portaria 195/2019, o Anexo 1 do RICMS-BA (para eu transcrever os valores), a lista de itens e o regulamento atual de ST do RICMS-PR (a Resolução SEFA 20/2017, atualizada até a 928/2018, que você enviou em 12/11/2026, confirma 36,56% e 71,78%, mas é de 2018 e não traz a lista de itens), o Decreto 90.309/2023 de AL e os Protocolos 97/10, 93/26, 94/26 e 96/26 em PDF do CONFAZ? (AC, AM e DF já foram lidos.) | Enviar, sem pressa (só trava a carga) |

## 1.42 Documento 188: respostas parciais do contador, de 16/11/2026 (Q188-6)

Você enviou o documento 188 com **32 perguntas respondidas** (D-N583). Em 11 delas a resposta basta; em 16 ela responde só uma parte (o resto fica no próprio bloco, em "Ainda aberto"); em 3 não resolve a pergunta (C9, C13 e C281); e em 4 (C27, C33, C324 e C325) ela divergia do que o ERP tem, o que você decidiu nas Q188-7 a Q188-9. Duas respostas **não aplico**: a C14(f) (dia não útil "postergado") contradiz a regra por tributo do dicionário, e a C249 se contradiz ((a) "fica" e (c) "do IPI não entram"); os dois voltam ao contador como esclarecimento. As respostas coladas de pesquisa (C22(b), C208 e C209) não contam como confirmação por fonte oficial.

**Q188-6 (aplicar as respostas que confirmam ou ajustam sem conflito; 21 perguntas).** Nenhuma cria entidade ou campo; mudam textos, padrões e situação do dado:

| Pergunta | O que muda |
|---|---|
| C6 | Y520 faltando com `IND_PGTO_EXT` = "S": aviso, sem bloqueio; o usuário completa no ERP ou no PVA |
| C7 | Funções e fórmulas de 2026 confirmadas: liberar as linhas paradas pela Q93-4 |
| C8 | Imposto devido transportado: N630A 26 (IRPJ) e N670 21 (CSLL); os outros quatro seguem abertos |
| C10 | 11 fórmulas de 2026 conferidas com a lei: marcar como validadas |
| C11 | M350R 345 lida como `M350(170)`: validada |
| C14 | Vencimentos: valores iniciais validados; IRRF geral dia 20; financeiras dia 20; percentuais por empresa; classificação 85; regra de dia não útil **não** aplicada |
| C20 | Crédito de aquisição: competência = data de entrada da nota; retenção na fonte: liquidação (F600) |
| C21 | Limite de R$ 3,75 milhões: validado para 2026; 2027 pode mudar |
| C22 | ISS fixo da SUP: valor da faixa multiplica a quantidade de profissionais (já é assim no dicionário) |
| C25 | EFD-Contribuições: sem fim por data fixa; no caixa, continua até a última parcela de 2026 recebida |
| C28 | Feriado local não muda o prazo federal (só nacionais) |
| C32 | Notas sem chave são válidas: manter `Chave_Acesso` condicional ao modelo |
| C207 | `ID_Valor_Centro_Custo` do I051 só quando a conta se divide entre linhas referenciais |
| C226 | Bons antecedentes fiscais: sem critério prático; o ERP só registra e avisa |
| C227 | Multa de mora volta a correr após a notificação; juros sobre a multa punitiva confirmados |
| C232 | IS na industrialização por encomenda: o executor não é contribuinte pelo serviço; o IS recai na venda do encomendante |
| C256 | Alíquota do IS do veículo: 4 casas; 1,21 sobre a alíquota exata; 1,17 antes do arredondamento |
| C258 | Potência: kW na ficha, sem derivar do cv (padrão "não deriva" confirmado) |
| C261 | Táxi: motorização lida como etanol, flex, GNV adaptado, híbrido flex ou etanol, até 2.000 cm³; adendo vira aviso |
| C262 | IS: dado de potência e propulsão na nota e no cadastro; efeito em ECD e ECF só pela contabilidade |
| C279 | Autopeças: declaração do comprador basta; vendedor recolhe a diferença; validade obrigatória; destinação mista por item |

| Id | Pergunta | Recomendação |
|---|---|---|
| Q188-6 | Aplicar as respostas da tabela acima? | Sim |

# 2. Para o contador

**Esta seção não guarda mais perguntas.** Por regra de Alberto (09/11/2026, D-N501), **todas as perguntas e pendências do contador ficam somente no documento 188**, com cada pergunta detalhada (de onde vem, texto completo, o que o ERP faz enquanto isso e campos para resposta, data e situação). São **359 perguntas** (C1 a C359). Quando o contador responder, atualizo o 188 e, para o que é de Alberto, esta lista.

| Parte do documento 188 | Assunto | Perguntas |
|---|---|---|
| Parte 1 | ECF, Y520 e cadeia do lucro real | 13 (C1 a C13) |
| Parte 2 | Listas antigas: tributos federais, vencimentos, EFD-Contribuições, DES-IF, DeSTDA e SUP | 29 (C14 a C42) |
| Parte 3 | ECF, presumido, caixa, encontro de contas, moeda estrangeira e adiantamento (documentos 100 a 155) | 57 (C43 a C99) |
| Parte 4 | IBS e CBS, documentos fiscais, EFD-ICMS/IPI, combustíveis e ECD (documentos 144 a 185) | 112 (C100 a C211) |
| Parte 5 | Itens que estavam na seção 1 e são do contador | 4 (C212 a C215) |
| Parte 6 | Documentos 189 a 194: CNPJ, suspensão do IPI, Lei 10.485, Confia (IN RFB 2.295), REIDI, registro 0000 da ECF e IBS do EAC e do B100 | 10 (C216 a C225) |
| Parte 7 | Documentos 159 e 196: consulta, multas, ordem de aplicação, PNCT, documento consolidado e Imposto Seletivo (LC 227) | 7 (C226 a C232) |
| Parte 8 | Documento 198: regimes específicos de serviços financeiros, seguro e plano de saúde (B4) | 6 (C233 a C238) |
| Parte 9 | Documento 200: crédito do tomador do serviço financeiro, arrendamento, antecipação e plano de saúde (B0b-2) | 7 (C239 a C245) |
| Parte 10 | Documento 201: efeito do crédito do tomador na ECD e na ECF, e a dedução da despesa na DeRE do tomador | 2 (C246 e C247) |
| Parte 11 | Documento 202: regime automotivo (mês de fruição, IPI na base, débitos próprios, tratamento contábil, alíquota de IPI, partes e peças, "veículo" na fração e devolução) | 8 (C248 a C255) |
| Parte 12 | Documento 204: tributação do veículo (arredondamento do IS, desempenho estrutural, kW, posições fora das listas, versão sem CAT, táxi, obrigação do IS, notas da Tipi, IPI da Lei 9.826, conversão da MP) | 10 (C256 a C265) |
| Parte 13 | Documento 205: conferência das normas do automotivo (alíquota `Al` de 31/12/2025, condições dos Decretos 10.457 e 7.422 e conflito com o art. 315, numeração das notas da Rota 2030); a C263 ganhou complemento | 3 (C266 a C268) |
| Parte 14 | Documento 206: Programa Mover e Rota 2030 (importação sem ato, multa por requisito, dispêndio mínimo e indicadores, autopeças com multa de 30% ou 100%, excedente do Rota 2030, tratamento do crédito financeiro) | 9 (C269 a C277) |
| Parte 15 | Documento 209: autopeças por destinação (retenção da Lei 10.485, prova da destinação, CST, ST do Convênio 142, IPI e estoque de 2027) | 8 (C278 a C285) |
| Parte 16 | Lista de autopeças não produzidas (norma vigente do regime, Resolução Gecex 284/2021 ou 368/2022, fonte oficial, vigência de cada ex-tarifário, alíquota de 0%, 2% ou isenção) | 1 (C286) |
| Parte 17 | Documento 212: plataformas digitais e marketplace (opção de emitir e pagar, controle de elemento essencial, diferença de alíquota de referência, precedência dos fundamentos, regime favorecido na substituição, documento em nome do fornecedor, informações do § 5º, split e § 7º, dispensa de inscrição do fornecedor no exterior) | 9 (C287 a C295) |
| Parte 18 | Documento 210: material e gênero alimentício na base das retenções (copeiragem e piso de 50%, piso global e combinação dos arts. 117 e 118, prova e custo de aquisição, alimentação e transporte, essencialidade e planilha na IN 1.234, informação na nota pelo prestador, vigência dos pisos) | 7 (C296 a C302) |
| Parte 19 | Documento 207: alíquota de IPI de 31/12/2025 (8702 a 8704) e Notas Complementares (ordem das notas, Ex da Tipi, `Al` por ficha, versão sustentável, outras alterações de 2025) | 5 (C303 a C307) |
| Parte 20 | Documento 215 (nova versão): Protocolo ICMS 41/2008, ST de autopeças e variações por UF (DF, MVA de AL, BA, MT, PR e PI, história anterior a 2023, uso automotivo, alíquota sobre a base, autorização do fisco, efeitos do Prot. 93/26, mesmo titular, operação interna, Protocolo 97/10, SP depois de 01/10/2026, BA, AL, PA e MG) | 16 (C308 a C323) |
| Parte 21 | Documento 216: Imposto Seletivo de bebidas, fumígenos, minerais e prognósticos (álcool etílico e mostos, fumígenos 24.01 e 24.04, valor de referência, IPCA, prognósticos, pequeno produtor, gás natural, minerais, importação, bebidas açucaradas e embalagem primária) | 11 (C324 a C334) |
| Parte 22 | Documento 218: Bloco 1 de combustíveis e usina (Ajuste SINIEF 14/2025, norma da ANP, perda e ganho, estoque de abertura, data do volume recebido, tanques interligados, número do bico e da bomba, intervenção, contador no máximo, produtos do 1300, bombas e lacres, usina: produto, balanço e resíduos; versão 2: limite de 0,6%, fornecedor do posto, distribuidor, grande consumidor, cupom, venda a outro revendedor, versão 2.1: Anexo da 884, transferência entre tanques, termos; versão 2.2: Diário Oficial e SC Cosit 223/2023) | 23 (C335 a C357) |
| Parte 23 | Documento 221: tabelas do Portal da NF-e (`620003` sem marca de grupo monofásico e valores 1 e 2 do `indComb` da tabela de CFOP) | 2 (C358 e C359) |

# 3. Para a equipe e fontes oficiais

| Pendência | Tratamento provisório |
|---|---|
| **Primeira execução do DDL num SQL Server**: o T-SQL foi lido pelo analisador (18.595 comandos na revisão 32, nenhum erro de leitura) e nunca executado | PostgreSQL 16 sem erro |
| **Q163-E1 e Q163-E2** (documento 163): datas da NT 2026.004 da NF-e (teste até 15/06/2026 na v1.01, que era 01/06/2026 na v1.00, e produção 01/07/2026, contra 06/04 e 06/07/2026 do documento 34) e valores dos domínios `tipo_receita_bruta_sn` (0 a 5 e 9) e atividade do Simples (se tem 01 a 04) | Vale a data da v1.01, com vigência; carga como publicada |
| **Q162-E1 e Q162-E2** (documento 162): conferir a carga de NCM contra o histórico do IT 2024.001 v2.40 (a data do NCM 85181020, 01/10/2026, **conferida na carga de 16/11/2026**; faltam as sucessões 1 para vários da v2.30, que o JSON do Portal não traz) e se o domínio `tPag` já tem os códigos 23 (Pix automático) e 24 (TEF / booktransfer) | Carga como publicada na tabela do portal; 23 e 24 provisórios no domínio do vínculo |
| Manual do eSocial: código de retorno de "registro já existe" (D-N301 a D-N303) e o `dtBase` no MOS (D-N304) | Classificação do retorno em catálogo com vigência |
| Carga do leiaute 12 da ECF, extraída do manual por mim: provisória até o contador validar (D-N320); a versão do leiaute (12 ou 13) é decisão do operador do sistema (D-N340) | Carga provisória |
| Ato da RFB que regulamenta Confia, Sintonia, OEA e selos (LC 225, arts. 29 e 47); seções do CCT e do Siscomex Importação, valores das tabelas do Portal que só saem autenticadas (métodos de valoração, acréscimos e deduções, motivos sem cobertura, regimes, fundamentos, recintos; carga pela API na Q144-7; a consulta pública do TTCE pediu CAPTCHA e não foi contornada), PDF de Perguntas e Respostas da NFS-e v1.00 de 08/09/2026 (regra da locação por pessoa física; Q144-8) e Anexos VI v1.03.00 e VII v1.01.00 da NT 007 da NFS-e (documentos 34, 143 e 144) | `ID_Classificacao` do programa fica sem carga; B1 segue o Anexo I da Nota 77, os manuais de 2018 a 2020 (os mais recentes, Q141-8) e as especificações da API lidas nos documentos 143 e 144; os campos de tabelas autenticadas ficam livres até a carga |

## 3.1 Das listas antigas, sem registro de resposta

| Item | Pendência |
|---|---|
| P40-04, P40-05 e Q-5 e Q-6 do documento 42 | Conflito das datas e do total do documento na NT 2026.004 (perguntar à Receita ou ao ENCAT) |
| Q-3, Q-7, Q-12, Q-13 e Q-15 do documento 41 e N-1 a N-11 | NFS-e Nacional: sinal de `vAjusteBCIBSCBSComExt`, `regApIBSCBSSN` = 2, cronograma do leiaute 1.04.01 e o XSD 1.04 |
| Q-N1 a Q-N11 do documento 40 | MOC da NFCom: versão nova, `cClass`, URLs por UF e divergências internas |
| Q-4, Q-8, Q-9, Q-10 e Q-15 do documento 42 | Alíquotas da CBS de 2027 e do IBS de 2029 em diante; inconsistências do MOC e das NTs do CT-e |
| P43-03, P43-06, P43-07 e P43-08 (revista) | Fontes: Convênio ICMS 142/18, tabela de países do Bacen, IBGE; óleo diesel por unidade sem linha depois de 31/05/2026 |
| P-22 | Qual das duas versões da Tabela 01 da Reinf é a mais nova |
| P-01 a P-09, P-24 e P-40 | Primeiro XML real da DCTFWeb (nenhum bloqueia; valor bruto guardado) |
| P-25 a P-27 | Limitações assumidas (declarante pessoa física no eSocial, categoria Aferição/Sero, PER/DCOMP sem transmissão) |
| Q61-x, Q62-x e Q67-x (documentos 61, 62 e 67) | Se algum ficou sem resposta, não consta nos registros que consultei |

## 3.2 Materiais oficiais que ainda não chegaram

Ato COTEPE 47/15 e manual do SEDIF-SN (DeSTDA); Manual do PGDAS-D e do DAS-MEI de 2027 e art. 30 da Resolução CGSN 140; demonstrativo de gastos tributários da LOA 2026; Anexo III antigo da IN RFB 2.119/2022 e lista de valores da situação cadastral do CNPJ; valores trimestrais da TJLP, IN RFB 1.700 (art. 75) e IN RFB 1.037 atual; texto da LC 235/2026; Catálogo de Serviços e Swagger do Integra Contador e páginas de pagamentos e situação da API de Débitos da CBS; Anexo I do MOC da NF-e ABI e NT do DANFE-ABI; NFCom (tabela `cClass`, URLs e WSDL por UF); XSD do leiaute 1.04 da NFS-e; Anexo I do MOC do CT-e; PL_010g, schema do evento 110300 final e IT 2026.001 (meios de pagamento); NT 2026.004 v1.01 do RTC (a v1.01 da NF-e e NFC-e chegou em 03/11/2026, é outra nota), NT 2026.005 das versões CT-e, CT-e OS, NFCom e BP-e, NT 2025.002 v1.53, NT 2026.006 v1.01, NT 2026.007 v1.11 e NT 2026.008 v1.01, e NT 2026.001 da NF-e ABI (a NT 2026.005 da NF-e e a NT 2026.004 v1.00 da NF-e já chegaram, e em 03/11/2026 também os pacotes de schemas do BP-e, sem os textos das NT; nas Q162-4 e Q163-5 você respondeu "sim" e ainda não chegaram), Tabela de Códigos v1.01 da NF-e ABI, planilha de CFOP v2.10 e tabela de NCM em uso, MOC, DABPE e tabela de cClassTrib do BP-e (Q164-12) (Ato nº 10/2026 e ITs de 03/11/2026, documentos 161 e 162; o IT 2026.003 v1.00 já chegou); Guia atual da EFD-Contribuições; **planilha do leiaute 11 da ECF** (as fórmulas de 2024 da N620 18, N620 19 e N630A 18, Q152-4; reenviar);  tabela 4.5.4 da EFD ICMS/IPI (as demais tabelas externas chegaram no documento 172); manual atual do CNO; tabela de códigos de receita do MIT; pacote XSD do eSocial posterior a 26/10/2026 e primeiro XML real da DCTFWeb; série da tabela do ISS fixo desde 2004. Do documento 165: texto das NT 2026.001, .002, .004 e .005 de NFAg, NFGas, NF3e e NFCom e das NT de CT-e (schemas e MOCs vieram, textos não); MOC da NF3e e da NFCom; tabelas de classificação de item (`cClass`) do gás e da energia.

**Dos documentos 170 e 173 (Q170-9 e Q173-E3).** Faltam: a Portaria MF 2.813 e a prorrogação de 26/10/2026; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha da MP 1.391 e do etanol); a LC 235; o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio (hoje só pelas redações do texto consolidado dos outros decretos); e, quando saírem, o ato do QAV e o que valer para 2027.

**Do documento 172:** faltam a versão para comparação do cBenef (Q172-E1) e a forma de chegada do validador novo (Q172-E5).

**Do documento 196 (Q196-10):** falta o ato do chefe do Poder Executivo com a metodologia do valor de referência do Imposto Seletivo (art. 414, § 2º).

**Do documento 198 (Q198-12, você respondeu "seguir", que inclui enviar):** o manual oficial da DeRE (pacote 1.3.0, Anexo I e Tabelas 11 e 12) e o ato conjunto do fator de redução da importação (art. 328, § 5º). Com eles confiro o leiaute dos registros, os `codTrib` da Tabela 11, a Tabela 12 e o evento D-1106 do ativo garantidor.

**Do documento 164 (Q164-12, você respondeu que envia):** o MOC do BP-e, o DABPE, o texto da NT 2026.004 v1.01 e das NT 2026.005 (BP-e) e a tabela de cClassTrib do BP-e.

## 3.3 Novos, dos documentos 100 a 116

| Pendência | Tratamento provisório |
|---|---|
| **Carga das instituições financeiras atuais** com `ID_Pais` = Brasil (o campo agora é obrigatório) | Carga provisória gerada em 28/10/2026 (1.061 instituições ativas, `Cad_Instituicao_Financeira_carga_provisoria.csv`): lista do Banco Central (ativas), STR e Pix, com ISPB e código de compensação. Você disse "só subir as ativas". Faltam três pontos seus: `Vigencia_Inicio` (usei 2000-01-01, as fontes não informam), a chave de `Cad_Pais` no lugar do texto `BRA` e se as cooperativas entram (ISPB pela raiz do CNPJ, só nas que o Pix ou o STR confirmam) |
| **Banco de dados e gerador do DDL** (documento 129): se aceitam índice único que ignora valores vazios (dois índices simples em `Codigo_Ispb` e `Codigo_Swift` dariam a unicidade da instituição no banco) | A camada de integração impede a duplicidade até a TI responder |
| Canal da ordem de pagamento ao exterior de cada banco do cliente (documentos 107 e 124) | Desenho aprovado; o plugin de cada banco trata o canal |
| **Unicidade das janelas e do código do tipo de baixa** (documento 113): o banco aceita duas linhas de `Cad_Tipo_Baixa_Bloco` com o mesmo tipo, bloco e `Vigencia_Inicio` (como nas outras janelas) e o código de `Cad_Tipo_Baixa` | A camada de integração impede |
| **Área de inconsistências** (Q113-11): cada processo automático (retorno bancário, baixa automática, carga da cotação do Banco Central, geração do Y520, importações) precisa gravar nela quando falhar ou depender do usuário, e reprocessar o registro depois do tratamento | A fazer na implementação (`Mov_Processo_Inconsistencia` entrou na revisão 25, documento 133) |
| **Retorno bancário, telas e relatórios de saldo** (fora do dicionário): a baixa automática precisa preencher `ID_Tipo_Baixa` pelo de-para entre a forma e o tipo (Q113-5; sem tipo mapeado, a operação para e pede ao usuário que relacione; no retorno, o item vai para a área de inconsistências, Q113-11; só o perfil de cadastro relaciona); o saldo do título não soma mais `Valor_Encontro`; a conciliação lê `Valor_Financeiro` (documento 113, seção 5) | A fazer na implementação |
| Formato e dígito de controle do IBAN, do SWIFT e do código de roteamento por país: o dicionário só guarda o valor | Sem validação de formato |
| **Código do CNAB e do PIX** (fora do dicionário): tratar `Codigo_Ispb`, `Agencia` e `Numero_Conta` como opcionais, obrigatórios só para instituição brasileira (documento 108, seção 5) | A fazer na implementação |

## 3.4 Novos, do documento 164 (BP-e)

| Pendência | Tratamento provisório |
|---|---|
| **Q164-E1** (equipe): datas das NT do BP-e (homologação e produção) e a marca de 01/12/2026 do BP-e aéreo (documentos 14 e 161); os schemas não trazem data e os textos das NT não vieram | `BPE-NT-DATAS` sem valor; a marca de 01/12/2026 fica como leitura anterior, não confirmada |
| **Q164-E2** (equipe): conferir no DDL se `xPag` e `xBand` já existem em `Mov_Nota_Fiscal_Saida_Pagamento` (os comentários mostram 10 colunas, sem eles) | Contados como novos até a conferência |
| **Q164-E3** (equipe): o `indFornecimento` do BP-e metropolitano diz que dispensa o "evento de confirmação de embarque", que não está nos schemas; ele existe? | Sem desenho |

## 3.5 Novos, do documento 165 (entrada de NFGas e NF3e)

| Pendência | Tratamento provisório |
|---|---|
| **Q165-E1** (equipe): conferir no DDL se já existem os campos de nota antecipada em `Mov_Nota_Fiscal_Entrada_Item` e de nota em papel em `Mov_Nota_Fiscal_Entrada_Referenciada` | Contados como novos até a conferência |
| **Q165-E2** (equipe): eventos dos MOCs da NFGas e da NFAg além de cancelamento, vínculo e Simples: ler e desenhar | Sem desenho |
| **Q165-E3** (equipe): o MOC da NFAg 1.00l não cita `tpFat` 4 e 5 e o MOC da NFGas tem inconsistência sobre o `tpFat` (G47 e G60, obrigatoriedade da `gFat`); confirmar com o autorizador | Vale o schema |
| **Q165-E4** (equipe): mapear classe, fase e tensão às tabelas SPED 4.4.5, 4.4.2 e 4.4.3 usadas em `Mov_Nota_Fiscal_Utilidade` | Domínios por modelo até o mapa |
| **Q165-E5** (equipe): datas das NT de NFAg, NFGas, NF3e, NFCom e CT-e (2026.001, .002, .004 e .005); os schemas não trazem data e os textos não vieram | Sem valor em `Cad_Dfe_Leiaute` e nos parâmetros |

## 3.6 Novos, do documento 156 (arts. 5º, 57 e 12)

**Q156-E1:** o leiaute da NF-e (NT 2025.002 e as seguintes) separa o desconto condicional do incondicional no item? Provisório: se não separar, `Valor_Desconto_Condicional_Item` é controle do ERP e não vai no XML.

## 3.7 Novos, do documento 157 (B0a)

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q157-E1** | Na NFS-e nacional, o campo de competência da DPS basta como data do fato gerador, ou a DPS precisa dos três campos do item da nota? | Só nas notas de produto |
| **Q157-E2** | O leiaute da nota de saída (NF-e e NFS-e) tem o grupo do pagamento antecipado (NT 2025.002; documento 34)? | Sem campo até a conferência |
| **Q157-E3** | Existe ligação entre `Mov_Credito` (tipo pagar) e `Mov_Credito_Fiscal` para o crédito do adquirente na extinção do débito da antecipação (LC, art. 10, § 6º)? Se não, propor `ID_Credito_Origem` em `Mov_Credito_Fiscal`. | Sem campo até a conferência |
| **Q157-E4** | Qual é a fonte da série da Selic (acumulada no mês) para `Cad_Serie_Cotacao`? | Série vazia |

## 3.8 Novos, do documento 150 (B5)

| Nº | Pergunta |
|---|---|
| **Q150-E1** | A Folha terá rubrica de gorjeta repassada ao empregado, para a origem `folha` da conferência (`Mov_Gorjeta_Repasse_Periodo`)? Até lá o repasse é informado. |
| **Q150-E2** | O PDV de bares e restaurantes consegue lançar gorjeta e valor de plataforma como itens próprios da nota (a segregação do art. 399, § 2º)? |
| **Q150-E3** | Há sistema de reservas ou de hospedagem que entregue início e fim da ocupação à locação por temporada, ou o cadastro será feito no ERP? |
| **Q150-E4** | O total de fornecimentos do associado à cooperativa sai da apuração por cClassTrib da nota; confirmar que as notas à cooperativa carregam o cClassTrib da redução do art. 391, I. |
| **Q150-E5** | A conferência da transferência de crédito lê o saldo credor da conta `saldo_credor_periodo_seguinte` do espelho da apuração (`Mov_Cbs_Apuracao_Espelho_Conta`) e a situação `concluida` do período: confirmar que essa conta é o saldo credor do art. 44 e que ela fica disponível quando o período conclui. |
| **Q150-E6** | Agência de turismo (Decreto, art. 420): o cálculo do crédito da agência já deixa de fora o valor que ela deduziu da base (`Valor_Deduzido` em `Mov_Agencia_Turismo_Repasse`), ou precisa de regra? |

## 3.9 Novos, do documento 170 (combustíveis)

| Nº | Pergunta |
|---|---|
| **Q170-E1** | A conversão do volume a 20 °C (Decreto, art. 260, § 2º) já vem feita do PDV ou do sistema do posto? O item tem `Combustivel_Quantidade_Temperatura_Ambiente`; confirmar que `Quantidade_Tributada` recebe a quantidade já convertida. |
| **Q170-E2** | O cadastro de unidades de medida (`Cad_Unidade_Medida`) tem litro, quilograma e metro cúbico com os símbolos do leiaute? A nota de combustível sai com a unidade da seção (art. 261, § 2º). |
| **Q170-E3** | A tabela da ANP (`Cad_Produto_Anp`) já está carregada com vigência? O vínculo da seção 6 depende dela. |
| **Q170-E4** | O exportador de combustíveis mantém o crédito (Decreto, art. 267, § 2º). Não verifiquei se o dicionário já cobre isso nos documentos de exportação: confirmar. |
| **Q170-E5** | A nota de entrada com gMonoRet chega pelo XML? Confirmar que o ERP lê o grupo e grava uma linha de complemento por item e tributo. |
| **Q170-E6** | Há cliente ou fornecedor que seja refinaria, formulador, importador ou distribuidora com mistura de EAC? Isso responde à Q170-8. |

## 3.10 Novos, do documento 173 (programas de apoio aos combustíveis; substituem a seção do 171)

| Nº | Pergunta |
|---|---|
| **Q173-E1** | O destaque do desconto na NF-e fora da MP 1.363: qual campo e qual frase na MP 1.391, no etanol e nos programas anteriores? Só **Informações complementares** com texto livre, ou há campo estruturado em nota técnica? Preciso do leiaute ou da NT. |
| **Q173-E2** | Algum cliente ou fornecedor da Mlegate é produtor, refinaria, importador, **distribuidor** de diesel, GLP ou etanol que adere aos programas? Isso responde à Q173-8 (e à Q171-E2). |
| **Q173-E3** | Mandar os textos que faltam: Portaria MF 2.813 e a prorrogação de 26/10; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha da MP 1.391 e do etanol); a LC 235; o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio; e, quando saírem, o QAV e o que valer para 2027. |
| **Q173-E4** | Método do desconto médio do distribuidor (Decreto 12.930, art. 11, § 1º, IV, redação do 12.974): média do lote, do mês ou do saldo corrente? A ANP tem modelo de planilha (Decreto 12.995, art. 6º)? |
| **Q173-E5** | O distribuidor envia à ANP, a cada 14 dias, volumes e valores médios de compra e de venda (Decreto 12.930, art. 20). O ERP precisa gerar esse relatório? |
| **Q173-E6** | O contas a receber tem tipo de título para a subvenção, com a ANP como órgão pagador? O ERP emitiu notas de diesel, GLP ou etanol em 2026 com desconto de subvenção, e precisamos do histórico? (juntam Q171-E4 e Q171-E6) |

## 3.11 Novos, do documento 172 (tabelas do validador da EFD-ICMS/IPI)

| Nº | Pergunta | Por que importa |
|---|---|---|
| **Q172-E1** | Há um arquivo de cBenef (por exemplo o da NF-e) para comparar com os códigos de ES e DF da informação adicional? | Confirma a ligação opcional da Q172-1 e dá a conferência. |
| **Q172-E2** | Há interesse em relacionar o valor por profissional do DF ao ISS fixo do DF? | Sem interesse, o valor só é guardado. |
| **Q172-E3** | Conferir os códigos de energia, água e gás (CLASCONS) com a fonte do documento 43: quem confere a diferença? | A carga só lista. |
| **Q172-E4** | Em que UFs a Mlegate tem clientes? (repete a Q173-E2) | Pela D-N68, o que é só de um regime entra quando há cliente; aqui a lista decide quais tabelas de UF o contador valida primeiro. |
| **Q172-E5** | Como o validador novo chega à equipe (download manual do PVA, pacote do portal)? | Define a rotina de recarga e o aviso de "tabela mais nova disponível". |

## 3.12 Novos, do documento 158 (B3)

| Nº | Pergunta |
|---|---|
| **Q158-E1** | Os códigos dos eventos fiscais de **internamento**, de **conclusão do desembaraço** e de **não internamento** não estão nos documentos que tenho (vêm de nota técnica). Quando a NT chegar, entram em `Cad_Dfe_Evento_Tipo` com autor `suframa` ou destinatário. Há uma NT em mãos? |
| **Q158-E2** | Manaus, Rio Preto da Eva e Itacoatiara entram só em parte na ZFM (Decreto, art. 433, I). O ERP guarda o município, e não o endereço dentro da parte demarcada. Aceito que o usuário informe a marca `Eh_Parcial` e confirme no cadastro do destinatário? |
| **Q158-E3** | O cadastro de clientes já traz a inscrição Suframa em `Cad_Participante_Inscricao` (`Tipo_Inscricao` = suframa) e a nota já leva o número em campo próprio (Decreto, art. 529, § 2º)? Se não, o cadastro de inscrições é o ponto de entrada. |
| **Q158-E4** | Há hoje cliente na ZFM ou nas ALC? A resposta define a prioridade do internamento e da importação com suspensão na implantação. |

## 3.13 Novos, do documento 175 (lacunas setoriais da EFD-ICMS/IPI)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q175-E1** | A Mlegate (ou algum cliente) recebe nota modelo 02 **só consolidada**, sem as notas individuais? Se sim, criamos uma consolidação como a do Convênio 115. | Não há caso conhecido; fica sem estrutura. |
| **Q175-E2** | `Mov_Cte` aceita o BP-e (modelo 63), sem `COD_PART`, `SUB` e `IND_FRT`? | A verificar. |
| **Q175-E3** | Consequência de Q172-C1 ("só o Guia"): as linhas dos catálogos do validador que o Guia não traz ficam com `Tabela_Origem` do validador. Está correto manter assim? | Sim. |

## 3.14 Novos, do documento 176 (FAQ da Receita sobre a EFD-ICMS/IPI)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q176-E1** | A baixa de título por retorno bancário já traz a instituição do repasse? (para propor `ID_Participante_Instituicao_Pagamento` a partir de `Cad_Conta_Bancaria`) | A verificar. |
| **Q176-E2** | A baixa por cartão ou por marketplace chega com a credenciadora? Hoje ela só está na nota (`Mov_Nota_Fiscal_Saida_Pagamento`). | A verificar. |
| **Q176-E3** | A entrada em estoque por transferência acontece na entrada física da nota (C170 da filial de destino) ou na saída da origem? | Na entrada física (FAQ 16.3.1.19). |
| **Q176-E4** | O Motor distingue produção sem ordem de ordem sem apontamento? (viabilidade da Q176-8) | A verificar. |
| **Q176-E5** | O Motor acha a filial que informa o 1601 pela conta bancária onde o dinheiro caiu: `Mov_Titulo_Baixa.ID_Conta_Contabil` leva à `Cad_Conta_Bancaria` e dela vem `ID_Filial`. Cada conta contábil de banco corresponde a **uma só** conta bancária (corrente, poupança ou aplicação)? | Sim; se não, a baixa precisa apontar a conta bancária. |

## 3.15 Novos, do documento 177 (transação de cartão)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q177-E1** | O arquivo da credenciadora (EDI) e o TEF trazem as sete datas, ou só algumas? | A verificar; as que faltarem ficam vazias (opcionais). |
| **Q177-E2** | Uma autorização que paga mais de uma nota é frequente? | Se não for, o pagamento da nota vira 1:1 e a transação ganha o `ID_Nota`. |

## 3.16 Novos, do documento 159 (consulta, multas, ordem de aplicação e PNCT)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q159-E1** | O `Mov_Processo_Suspensao` usa o indicativo de suspensão do eSocial (`codigo_suspensao_esocial`) e por isso não serve ao IBS e à CBS. Amplia essa entidade com um segundo indicativo ou a suspensão do IBS e da CBS fica dentro das duas entidades novas? | Fica dentro das duas entidades novas, como o documento 159 propõe; muda só se a equipe preferir uma entidade única de suspensão. |

## 3.17 Novos, do documento 218 (Bloco 1 de combustíveis e usina; versão 2)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q218-E1** | Há cliente (ou projeto) com posto revendedor de combustíveis ou com usina de açúcar e álcool? | Não sei; o desenho fica pronto e **desligado** (D-N68), com toda a habilitação desligada. |
| **Q218-E2** | Como chegam as leituras dos contadores e a medição dos tanques: automação de pista, planilha ou digitação? | `Origem_Dado` aceita as três; confirmar. |
| **Q218-E3** | O posto mede os tanques todos os dias (régua ou sonda) e quem fecha o dia? Fecha por dia ou por mês? | Medição diária; o fechamento grava os valores calculados. |
| **Q218-E4** | A produção da usina vem das ordens de produção (`Mov_Ordem_Producao`) ou é digitada num lançamento próprio? | Lançamento próprio: a ordem de produção não tem esmagamento, mel residual, anidro e hidratado nem resíduos. |
| **Q218-E5** | O estoque de combustível do posto é controlado pelo módulo de Estoque (um local por tanque) ou só pelo livro? | O `ID_Local_Estoque` do tanque é opcional; só serve ao aviso A10. |
| **Q218-E6** | A nota de saída do posto (NFC-e) já leva bico, bomba, tanque e encerrante em todos os itens de combustível? | Sim, pelo leiaute; sem isso a leitura sugerida a partir dos documentos não funciona. |
| **Q218-E7** | Os combustíveis do posto têm código da ANP no cadastro do produto (`ID_Produto_Anp`)? | Devem ter; sem ele o ERP não sabe que o item é combustível (aviso A1 e A4). |
| **Q218-E8** | Quais modelos de documento os postos clientes usam para vender (NFC-e, SAT ou MFE, CF-e-ECF, ECF)? O PDV grava bico e encerrante no item do cupom? | Sem bico no cupom, o ERP só compara por produto (A11). |
| **Q218-E9** | Há cliente que seja **distribuidor** de combustíveis, ou cliente **grande consumidor** com tanque próprio? O que ele precisa além do C165 e do 0206 (bases e tanques, relatório COTEPE, envio à ANP)? | Sem cliente, nada se desenha (D-N68); o distribuidor usa `Cad_Local_Estoque`. |

# 4. Prazos de calendário

Estas datas vêm do texto de 11/10/2026 do antigo documento 38 e **não foram reconferidas nas fontes oficiais**. As que já passaram foram retiradas; os itens que dependiam das de 31/10 e 10/11/2026 (Q-E das cooperativas e Q80-5 do DES-IF) continuam na seção 1, sem resposta. Os que dependem de resposta sua ou do contador estão em negrito. Os prazos que só o contador cumpre estão no apêndice A do documento 188.

| Data | O que vence | Quem decide ou age |
|-----------------|------------------------------------------|-----------------------------------------|
| 16/11/2026 | NT 2026.004: produção das regras de IBS/CBS no CT-e, MDF-e e NFCom (conflito de datas registrado: P40-04); **NT 2026.005 v1.00 da NF-e e NFC-e (campos do Simples; documento 163)**, com o evento 412140 sem data | Equipe |
| 23/11/2026 | Limite de horas do tempo parcial (S-2200 e S-2206) | Equipe e RH |
| **até 30/11/2026** | Cancelamento da opção pelo regime regular de IBS/CBS no Simples (a CGSN pode adiar) | Alberto, se houver cliente |
| 01/12/2026 | NFAg, NFGás, NFS-e de plataformas e NF-e ABI; obrigação de NFS-e na locação (Q85-13, MEI locador: pessoa jurídica obrigada em 01/12/2026; pessoa física que abrir CNPJ para emitir, em 01/01/2027) | Alberto |
| 14/12/2026 | CT-e Simplificado reestruturado (só se houver cliente nesse modelo); códigos de incidência do salário-paternidade | Alberto e RH |
| 20/12/2026 | Receita e folha de 12/2025 a 11/2026 de quem ingressa no Simples em 01/01/2027 ou vem do MEI: conferir, alterar ou completar no módulo "Receitas Anteriores à Opção" (Resolução CGSN 190, art. 144-E; condicional a haver cliente nessa situação, P-R4-01) | Alberto e contador |
| 01/01/2027 | Simples e NF-e Importação e Combustíveis no cronograma da Receita; efeitos das Resoluções CGSN 190 e 191 | Alberto |
| 20/01/2027 | Receita e folha de 12/2026 das mesmas empresas do prazo de 20/12/2026 (Resolução CGSN 190, art. 144-E, II) | Alberto e contador |
| 01/02/2027 e 01/03/2027 | NT 2026.004: ICMS previsto no pagamento antecipado, em homologação e em produção (P40-04) | Equipe |
| Janeiro de 2028 | Início previsto do split payment (D-N282, adiado por você) | Alberto |

# 5. Limites desta lista

Esta lista guarda só o que está em aberto, e o que ela diz de fontes e de prazos não foi reconferido nas fontes oficiais, salvo onde o texto o diz. O histórico das respostas, das revisões e das atualizações deste arquivo está no documento 14 e nos relatórios de consolidação (documentos 199, 203, 208, 211, 213, 214, 217 e 219).
