# Desenho dos programas de apoio aos combustíveis por período: subvenção, devolução de tributo e redução temporária — Documento 171

*Complementa o documento 170, a partir da sua resposta de 04/11/2026: "Q170-1 a Q170-10 - Sim para Todos", com o alerta de que **combustíveis podem ter subsídios por período, e nesse período a tributação é diferente da dos outros combustíveis**. O documento 170 está aprovado e entra no próximo "consolidar"; este documento 171 fecha o que o alerta pede. **Nada entra no dicionário agora.***

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

Os subsídios existem de fato em 2026 e têm exatamente a forma que você descreveu: **valor por litro (ou por quilograma), por combustível, com período, alterado por ato**. Os textos da LC 214 e do Decreto 12.955 não falam deles (procurei "subvenção" e "subsídio" nos três textos e só achei usos sem relação com combustíveis), então a base deste desenho são **notícias, o resumo do Senado sobre a MP 1.363 e o comunicado do Ministério da Fazenda**. **Não li o texto de nenhuma medida provisória, portaria ou decreto do programa.** Por isso nenhum valor entra na carga (Anexo A mostra só o que li, para conferência).

O desenho acrescenta **5 entidades novas (75 campos)**, altera **1 existente** (2 campos novos) e cria 1 valor novo de critério do Motor.

**Seis achados que você precisa ler.**

1. **Há dois mecanismos diferentes, e o dicionário tratava só de um.** (a) **Tributação diferente por período**: a alíquota do tributo zerada ou reduzida por prazo (PIS/Cofins do diesel foi zerado até 31/05/2026; o do QAV e o do biodiesel tiveram a desoneração prorrogada). Isso **já cabe no dicionário**: é uma linha com vigência na tabela de alíquotas (PIS/Cofins por unidade, que já existe, e a `Cad_Aliquota_Combustivel` do documento 170 para a CBS). (b) **Subvenção**: dinheiro que a União paga ao produtor ou importador por unidade vendida, com a obrigação de dar o mesmo valor de desconto ao comprador. Isso **não existia** no dicionário (a `Cad_Subvencao_Investimento` é de outra natureza: incentivo de investimento recebido de ente público).
2. **O valor muda por ato e por período.** Só do diesel, li cinco valores ao longo de 2026: R$ 0,32 (MP 1.340), R$ 0,80 nacional e R$ 1,20 importado (MP 1.349), R$ 1,12 (MP 1.363) e R$ 2,12 (R$ 1,12 mais R$ 1,00 da Portaria MF 2.813, mantido pela Portaria MF 2.946, de 25/09/2026). A MP 1.363 permite ao Ministro mudar o valor a cada dois meses, com 15 dias de aviso. **Por isso o valor é parâmetro com vigência, nunca campo do combustível.**
3. **No regime específico a base é a quantidade, então o desconto no preço não muda a base da CBS** (nem a do PIS/Cofins por unidade e a do ICMS ad rem). **Essa é leitura minha**: não achei nenhuma norma que diga como o desconto da subvenção entra na base, e levo ao contador (Q171-C2).
4. **O beneficiário tem obrigações que o ERP precisa registrar**: aderir por termo, dar o desconto exato, destacá-lo na NF-e e requerer o pagamento à ANP, que paga em até 30 dias. Desenhei adesão, item e requerimento (seção 7), mas **só entram no consolidar quando houver cliente beneficiário** (Q171-3, D-N68).
5. **Não achei se a subvenção continua em 2027.** O desenho funciona nos dois casos: sem programa vigente, nenhuma linha de valor existe e o ERP não calcula subvenção.
6. **Houve também "devolução de tributo" (cashback):** em 1º/06/2026 um desconto de R$ 0,35 no diesel A, pago como devolução do imposto de refinarias e importadores, compensou a volta do PIS/Cofins. Modelei como terceiro tipo de apoio (`devolucao_de_tributo`), porque a mecânica de pagamento difere (a MP 1.358, que o criou, não li).

# 2. Regras que segui

Valem as dos documentos 156, 157, 150 e 170 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória; "O ERP só registra"; avisa e nunca bloqueia; D-N68: entidade de regime só quando há cliente). Mais estas:

1. **O período é a vigência.** Cada valor por período é uma linha com `Vigencia_Inicio` e `Vigencia_Fim`; mudar o valor é versão ou linha nova. O ERP não renova sozinho: quando o programa acaba sem linha nova, avisa "sem valor vigente".
2. **A tributação diferente não é copiada para a subvenção.** Quem decide o código de tributação (cClassTrib) continua sendo o Motor, pela data e pelo combustível; a subvenção só acrescenta o critério de adesão (seção 8).
3. **Valor derivado não se guarda**, salvo o que um evento posterior pode mudar: guardo o valor por unidade aplicado no item, porque a tabela pode ser corrigida.
4. **Nenhum valor, período ou condição vai escrito no código.** Tudo isso é cadastro.
5. **Uma leitura minha é sempre dita como minha** e vai ao contador.

# 3. O que li sobre 2026 (e o que não li)

Todas as fontes abaixo são secundárias (notícias, resumo do Senado e o comunicado do Ministério da Fazenda); **nenhum texto de lei, medida provisória, portaria ou decreto foi lido**.

| Medida | O que as fontes dizem |
|---|---|
| MP 1.340 (12/03/2026) | Subvenção ao diesel de R$ 0,32 por litro, até 31/05/2026 |
| MP 1.349 (07/04/2026) | Diesel: R$ 0,80 por litro nacional e R$ 1,20 importado (o importado custeado meio a meio com os estados, segundo a notícia); GLP importado, R$ 850 por tonelada; dois meses, prorrogáveis; até 31/05/2026 |
| MP 1.358 (2026) | "Cashback" (devolução do tributo pago), usado primeiro na gasolina; texto não lido |
| MP 1.363 (DOU de 30/05/2026) | Diesel de uso rodoviário, R$ 1,12 por litro, de 01/06/2026 a 31/12/2026; beneficiários: produtores e importadores autorizados pela ANP; adesão por termo, desconto exato no preço, destaque na NF-e, compartilhamento de dados RFB–ANP; a ANP paga em até 30 dias; o Ministro pode interromper ou alterar o valor a cada dois meses, com 15 dias de aviso; quem participa das MPs 1.340 e 1.349 precisa sair delas |
| MP 1.391 (11/09/2026) | Autoriza o Ministério da Fazenda a definir o valor por ato próprio |
| Portarias MF 2.813 e 2.946 | Mais R$ 1,00 por litro (data não lida) e total de R$ 2,12; a de 25/09/2026 mantém os R$ 2,12 e passa a base de 27/09/2026 para a MP 1.391 |
| Tributos federais, 2026 | PIS/Cofins do diesel zerados até 31/05/2026; desconto de R$ 0,35 no diesel A a partir de 01/06/2026; desoneração do QAV e do biodiesel prorrogada (valores não lidos) |
| GLP | Subvenção prorrogada até o fim de julho de 2026; equivale a R$ 11 por botijão de 13 kg (Casa Civil) |
| Portaria conjunta MF/CGIBS nº 14/2026 | Metodologia da CBS de 2027: nos combustíveis cuja alíquota caiu entre março e junho de 2026, a referência é a de fevereiro de 2026 nos meses da redução |

**O que não achei:** os textos das medidas, os Decretos 12.878, 12.930 e 12.995; a periodicidade das renovações (as fontes divergem: 30 dias, dois meses, até 31/12/2026); o valor para o QAV; qualquer efeito da subvenção na nota, na base ou no tributo; e a continuidade em 2027. Os valores das notícias e os da MP 1.363 **não batem entre si**, e preferi o resumo do Senado e o comunicado do Ministério.

# 4. O que o dicionário já tem e o que falta

| Peça | O que faz | O que falta |
|---|---|---|
| `Cad_Natureza_Receita_Pis_Cofins_Aliquota` | PIS/Cofins por percentual ou por unidade (`Forma_Aliquota = por_unidade`), com vigência e a nota "no período de alíquota zero usar CST 06" | Nada: a tributação por período do PIS/Cofins vem da tabela oficial |
| `Cad_Aliquota_Combustivel` (documento 170) | CBS por unidade, com vigência | Marcar a linha temporária e ligá-la ao programa |
| `Mov_Apuracao_Tributo_Item` | Tributo do item, inclusive específico por unidade | Nada |
| `Mov_Nota_Fiscal_Saida_Item.Valor_Desconto_Item` | Desconto do item | Não uso: o desconto da subvenção é de natureza própria e o contador decide como entra na base (Q171-C2) |
| `Cad_Subvencao_Investimento` e `Mov_Subvencao_Investimento_Periodo` | Incentivo de investimento recebido de ente público, com crédito (Lei 14.789) | Outra natureza; a subvenção de custeio ao combustível não cabe nela (Q171-C1) |
| `Cad_Motor_Regra` e filhos | Escolhem o cClassTrib por critérios, com vigência | Um critério novo (adesão) |
| `Mov_Titulo` | Título a receber | A ligação com o requerimento (Q171-E4) |
| Padrão do `Mov_Apuracao_Tef` | `Status` {calculada, pendente_decisao, confirmada} | Nada; reaproveito |

# 5. O programa e o valor por período

`Cad_Combustivel_Programa_Apoio` é o cabeçalho: o ato que criou o programa, o tipo de apoio, as obrigações do beneficiário (adesão, desconto exato, destaque), o prazo de pagamento e o aviso prévio de alteração. `Cad_Combustivel_Programa_Valor` guarda **um valor por combustível, por tipo de agente e origem, por período**: é nesta tabela que o diesel pode ter um valor em junho e outro em outubro.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Programa_Apoio` | identificador | --- |
| `ID_Combustivel_Programa_Apoio_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Programa_Apoio_Versao). ID_Combustivel_Programa_Apoio é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `Codigo` | código (até 30) --- identidade | O programa pelo ato que o criou, por exemplo `SUBVENCAO-DIESEL-MP-1363`. |
| `Descricao` | texto | O nome do programa. |
| `Tipo_Apoio` | enumeração {subvencao_por_unidade, devolucao_de_tributo, reducao_temporaria_de_tributo} | `subvencao_por_unidade`: a União paga ao produtor ou importador um valor por litro ou quilograma vendido (o diesel da MP 1.363). `devolucao_de_tributo`: devolve parte do tributo pago (o "cashback" das notícias). `reducao_temporaria_de_tributo`: zera ou reduz a alíquota por período (PIS/Cofins do QAV em 2026); esse tipo **não gera pagamento**, o efeito vive em `Cad_Aliquota_Combustivel` (seção 6). |
| `Ato_Instituidor` | texto | A medida provisória, o decreto ou a portaria que criou o programa. |
| `Orgao_Pagador` | texto, opcional | Quem paga ao beneficiário (a ANP, na MP 1.363). |
| `Exige_Adesao` | booleano | Verdadeiro quando o beneficiário precisa aderir por termo (MP 1.363, art. 3º: adesão e desistência voluntárias). |
| `Exige_Desconto_No_Preco` | booleano | Verdadeiro quando o beneficiário precisa repassar o valor exato da subvenção como desconto no preço de venda (MP 1.363, art. 2º). |
| `Exige_Destaque_Na_Nota` | booleano | Verdadeiro quando o desconto deve aparecer destacado na NF-e (MP 1.363, art. 2º). Qual campo da nota leva o destaque é a Q171-E1. |
| `Veda_Cumulacao_Com_Outros_Programas` | booleano | Verdadeiro quando quem participa de outro programa precisa sair dele para aderir (MP 1.363, art. 5º). O ERP só registra; o aviso lê as adesões ativas. |
| `Prazo_Pagamento_Dias` | número, opcional | Dias entre o protocolo do requerimento e o pagamento (30 na MP 1.363). Parâmetro: o ERP calcula a data prevista e avisa o atraso; não guarda a data. |
| `Aviso_Previo_Alteracao_Dias` | número, opcional | Dias de aviso prévio exigidos para alterar o valor (15 na MP 1.363, segundo o resumo do Senado). Quando o valor novo começa antes disso, o ERP avisa. |
| `Fundamento_Legal` | texto | O artigo do ato. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Programa_Valor` | identificador | --- |
| `ID_Combustivel_Programa_Valor_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Programa_Valor_Versao). ID_Combustivel_Programa_Valor é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) --- identidade | O programa. |
| `ID_Combustivel_Regime` | referência (Cad_Combustivel_Regime) --- identidade | O combustível. O programa pode atingir só um deles (o diesel), e o mesmo combustível pode ter valores diferentes em períodos diferentes. |
| `ID_Tipo_Agente` | referência (Cad_Classe_Sistema, domínio = agente_cadeia_combustiveis), opcional --- identidade | Quem recebe: produtor, refinaria ou importador. Vazio quando o valor vale para todos. |
| `Origem_Produto` | enumeração {nacional, importado, qualquer} --- identidade | Em abril de 2026 o diesel nacional e o importado tinham valores diferentes (notícia; a MP 1.363 usa um valor só). |
| `Valor_Por_Unidade` | número | Reais por unidade de medida do combustível (litro, quilograma ou metro cúbico), com quatro casas. Em `devolucao_de_tributo` é o valor devolvido por unidade; em `reducao_temporaria_de_tributo` a tabela não é usada. |
| `Condicao_Aplicacao` | texto, opcional | O que restringe o valor, por exemplo "diesel de uso rodoviário comercializado". Texto, até o contador dizer como o ERP identifica (Q171-C3). |
| `Ato_Divulgacao` | texto | O ato que fixou ou mudou o valor. |
| `Data_Publicacao` | data | A publicação do ato. Se o valor novo começa antes de `Aviso_Previo_Alteracao_Dias` depois dela, o ERP avisa; não bloqueia. |
| `Origem_Valor` | enumeração {medida_provisoria, decreto, portaria, calculo_provisorio} | Quem fixou o valor. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

**Exemplo calculado (valores e datas hipotéticos).** Programa com R$ 1,12 por litro até 30/06 e R$ 2,12 a partir de 01/07. Uma venda de 5.000 l em 30/06 gera 5.000 × 1,12 = 5.600,00 de subvenção; outra de 5.000 l em 01/07 gera 5.000 × 2,12 = 10.600,00. Total do período: 16.200,00. A data da operação escolhe o valor; a data de emissão ou de pagamento não.

**Avisos, nunca bloqueios.** (1) Sem linha de valor vigente na data da operação, o item de combustível que se enquadra no programa fica `pendente_decisao` e o ERP avisa. (2) Valor novo que começa antes de `Aviso_Previo_Alteracao_Dias` contados da publicação: aviso. (3) Linha com vigência que acaba em menos de 15 dias e sem sucessora: aviso de "vence em breve".

# 6. Tributação diferente por período

A pergunta que você fez tem três respostas, uma para cada tributo:

1. **PIS e Cofins (até a extinção em 2027).** O dicionário já tem a tabela por unidade com vigência, e a carga vem da tabela oficial do Guia Prático (documento 43). Um período de alíquota zero é uma linha com vigência e a nota "usar CST 06". **Sem mudança.**
2. **CBS (a partir de 2027).** A `Cad_Aliquota_Combustivel` aceita linha com valor 0 ou reduzido e vigência curta. **Mudança:** dois campos novos, `Carater_Vigencia` (permanente ou temporário) e `ID_Combustivel_Programa_Apoio` (o programa que motivou a linha).
3. **Subvenção.** Não muda tributo algum: é recebida do órgão pagador e acompanha o desconto no preço. Se o contador disser que ela entra na base de algum tributo, a regra é do Motor e a base especial do documento 150 já tem a estrutura (Q171-C2).

**`Cad_Aliquota_Combustivel`**

| Campo | Tipo | Descrição |
|---|---|---|
| `Carater_Vigencia` | enumeração {permanente, temporario} | `temporario` quando a linha vale por um período curto fixado por ato (alíquota zerada ou reduzida por prazo). Serve ao aviso de "vence em N dias" e à leitura do período no relatório; o efeito na conta é só o valor e a vigência da linha. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio), opcional | O programa que motivou a linha temporária (por exemplo, a redução do tipo `reducao_temporaria_de_tributo`). |

**O que o Motor faz com o período.** Para o mesmo combustível, o Motor lê a data da operação e escolhe o cClassTrib: o de alíquota zero dentro do período temporário e o regular fora dele. Nenhuma data fica no Motor: a vigência da regra e a da linha de alíquota decidem. O Motor precisa de um critério novo para o caso em que o tratamento depende de **o emitente ter aderido** ao programa (seção 8).

*Exemplo:* diesel com CBS de R$ 0,3515 por litro vigente a partir de 08/01/2027 e uma linha temporária de valor 0 de 01/03/2027 a 30/04/2027 (hipotética). Venda de 10.000 l em 15/03/2027: CBS = 10.000 × 0 = 0,00 e o item usa o cClassTrib de alíquota zero escolhido pelo Motor. Venda em 02/05/2027: a linha temporária já acabou, e a CBS é 10.000 × 0,3515 = 3.515,00. O ERP avisa em 15/04/2027 (15 dias antes do fim) que a linha temporária vai vencer.

# 7. Lado do beneficiário: adesão, item da nota e requerimento

O produtor ou importador que recebe a subvenção faz três coisas que o ERP precisa registrar: **adere** ao programa (`Cad_Participante_Adesao_Programa`), **dá o desconto** em cada venda (`Mov_Combustivel_Subvencao_Item`) e **requer o pagamento** por período (`Mov_Combustivel_Subvencao_Requerimento`). **Por D-N68, essas três entidades só entram no consolidar quando houver cliente beneficiário** (Q171-3); ficam desenhadas aqui.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Adesao_Programa` | identificador | --- |
| `ID_Participante_Adesao_Programa_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Participante_Adesao_Programa_Versao). ID_Participante_Adesao_Programa é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Participante` | referência (Cad_Participante) --- identidade | Quem aderiu. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) --- identidade | O programa. |
| `Data_Adesao` | data | O dia da adesão. A vigência desta linha é a da adesão. |
| `Data_Desistencia` | data, opcional | O dia em que desistiu. |
| `Numero_Termo` | texto, opcional | O número ou a identificação do termo de adesão. |
| `ID_Documento_Termo` | referência (Cad_Documento), opcional | O arquivo do termo. |
| `Situacao` | enumeração {ativa, desistida, encerrada_pelo_ato} | `encerrada_pelo_ato` quando o programa acaba por prazo. |
| `Observacao` | texto, opcional | Por exemplo, o programa anterior de que o participante saiu para aderir (MP 1.363, art. 5º). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Subvencao_Item` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) | O beneficiário, emitente da nota. |
| `ID_Item` | referência (Mov_Nota_Fiscal_Saida_Item) | O item de combustível da nota. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) | O programa. |
| `ID_Combustivel_Programa_Valor` | referência (Cad_Combustivel_Programa_Valor) | O valor vigente na data da operação (a versão fica guardada em `Valor_Por_Unidade_Aplicado`). |
| `Data_Operacao` | data | A data da operação, que escolhe o valor do período. |
| `Quantidade` | número | A quantidade vendida, na unidade do combustível (a 20 °C nos líquidos). |
| `Valor_Por_Unidade_Aplicado` | número | O valor por unidade que valia na data. Guardado porque a tabela pode ser corrigida depois e a conta precisa dar o mesmo resultado. |
| `Valor_Subvencao_Calculado` | número | Quantidade vezes o valor aplicado. |
| `Valor_Desconto_Concedido` | número, opcional | O desconto que o beneficiário deu ao comprador por causa do programa. Informado: o ERP de vendas não o deriva. Se difere de `Valor_Subvencao_Calculado` e o programa exige o desconto exato, o ERP avisa. |
| `Destacado_Na_Nota` | booleano, opcional | Se o desconto saiu destacado na nota (programa com `Exige_Destaque_Na_Nota`). Vazio enquanto a equipe não responder a Q171-E1. |
| `ID_Combustivel_Subvencao_Requerimento` | referência (Mov_Combustivel_Subvencao_Requerimento), opcional | O requerimento em que o item foi cobrado. |
| `Status` | enumeração {calculada, pendente_decisao, confirmada} | Padrão do `Mov_Apuracao_Tef`: `pendente_decisao` quando falta a adesão, o valor do período ou o destaque, com a pendência escrita por extenso. |
| `Pendencia` | texto, opcional | A pendência, por extenso. |

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Subvencao_Requerimento` | identificador | --- |
| `ID_Empresa` | referência (Cad_Empresa) | O beneficiário. |
| `ID_Combustivel_Programa_Apoio` | referência (Cad_Combustivel_Programa_Apoio) | O programa. |
| `Competencia_Inicio` | data | O primeiro dia do período cobrado. |
| `Competencia_Fim` | data | O último dia do período cobrado. |
| `Valor_Requerido` | número | O valor do requerimento (soma dos itens incluídos; informado, porque o beneficiário pode cobrar só parte). |
| `Numero_Protocolo` | texto, opcional | O protocolo no órgão pagador. |
| `Data_Protocolo` | data, opcional | O dia do protocolo. Com `Prazo_Pagamento_Dias` do programa, o ERP calcula a data prevista e avisa o atraso. |
| `Data_Pagamento` | data, opcional | O dia em que o órgão pagou. |
| `Valor_Pago` | número, opcional | O valor recebido. |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título a receber da subvenção, quando o contas a receber o registra (Q171-E4). |
| `Situacao` | enumeração {em_preparo, protocolado, pago, pago_parcialmente, glosado} | --- |
| `Motivo_Divergencia` | texto, opcional | Por que o valor pago difere do requerido. |

**Exemplo calculado.** Um produtor vende 10.000 l de diesel com valor vigente de R$ 2,12: `Valor_Subvencao_Calculado` = 21.200,00. Se concedeu desconto de 20.000,00, o ERP avisa a diferença de 1.200,00 (o programa exige o desconto exato) e o item continua `calculada`. Se não há adesão ativa do emitente na data, o item fica `pendente_decisao` ("falta adesão ao programa na data da operação") e o requerimento não o inclui. Requerimento protocolado em 05/08/2026, com 30 dias de prazo, tem pagamento previsto até 04/09/2026; passado o dia, o ERP avisa o atraso. Se o órgão pagou menos que o requerido, a situação passa a `pago_parcialmente` e `Motivo_Divergencia` explica.

**O que o ERP não faz.** Não calcula quem tem direito (a ANP e a Receita decidem), não protocola o requerimento e não concilia o pagamento com o extrato: registra, avisa e deixa o título a receber ao contas a receber.

# 8. Motor de Regras

Um critério novo em `campo_criterio_regra`: **`adesao_programa_do_emitente`**, que lê se o emitente tem adesão ativa (`Cad_Participante_Adesao_Programa`) a um programa na data da operação. Serve à regra que escolhe o cClassTrib quando o tratamento do item depende da adesão. O combustível do item já é lido por `combustivel_do_item` (documento 170, seção 10). Nenhum código de classificação tributária é criado.

# 9. O que entra no próximo "consolidar"

**5 entidades novas (75 campos).**

| Entidade | Tipo | Campos | Vigência | Módulo | Capítulo |
|---|---|---|---|---|---|
| `Cad_Combustivel_Programa_Apoio` | parâmetro (carga vazia) | 19 | sim | Motores Transversais | 5 |
| `Cad_Combustivel_Programa_Valor` | parâmetro por período (carga vazia) | 16 | sim | Motores Transversais | 5 |
| `Cad_Participante_Adesao_Programa` | cadastro do beneficiário (carga vazia) | 13 | sim | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Item` | apuração por item de nota | 14 | não | Contabilidade & Fiscal | 7 |
| `Mov_Combustivel_Subvencao_Requerimento` | requerimento e pagamento | 13 | não | Contabilidade & Fiscal | 7 |

**1 entidade alterada** (2 campos novos).

| Entidade | O que muda |
|---|---|
| `Cad_Aliquota_Combustivel` (documento 170) | `Carater_Vigencia` e `ID_Combustivel_Programa_Apoio` |

**Valor novo em domínio.** `campo_criterio_regra`: `adesao_programa_do_emitente`.

**Cargas provisórias.** **Nenhuma.** As tabelas de programa e de valor ficam vazias até você mandar os textos (Q171-6); o Anexo A lista só o que li.

**Se a Q171-3 disser "sem cliente beneficiário"**, entram só `Cad_Combustivel_Programa_Apoio`, `Cad_Combustivel_Programa_Valor` e a alteração da `Cad_Aliquota_Combustivel` (2 entidades e 2 campos novos).


# 10. Perguntas

## 10.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q171-1** | `Cad_Combustivel_Programa_Apoio` e `Cad_Combustivel_Programa_Valor`: o programa de apoio (subvenção por unidade, devolução de tributo ou redução temporária) e o valor por combustível, tipo de agente e origem, **por período**, com vigência? | Sim |
| **Q171-2** | `Cad_Aliquota_Combustivel` ganha `Carater_Vigencia` e `ID_Combustivel_Programa_Apoio`, e o período de tributação diferente (alíquota zerada ou reduzida por prazo) é uma linha normal de alíquota com vigência curta, sem tabela nova? | Sim |
| **Q171-3** | O lado do beneficiário (`Cad_Participante_Adesao_Programa`, `Mov_Combustivel_Subvencao_Item` e `Mov_Combustivel_Subvencao_Requerimento`) só entra no "consolidar" **quando houver cliente produtor, refinaria, importador ou distribuidor que receba a subvenção** (D-N68)? Existe esse cliente hoje? | Sim, só quando houver cliente |
| **Q171-4** | Motor: o critério novo `adesao_programa_do_emitente` e nenhum código de classificação tributária criado neste documento? | Sim |
| **Q171-5** | **Nenhuma carga** de valor de subvenção até você mandar os textos; o Anexo A é só referência para conferência? | Sim |
| **Q171-6** | Você me envia os textos das MPs 1.340, 1.349, 1.358, 1.363 e 1.391, das Portarias MF 2.813 e 2.946 e dos Decretos 12.878, 12.930 e 12.995, e, quando sair, o ato do QAV e o que valer para 2027? | Sim |
| **Q171-7** | Leitura minha: no regime por unidade (CBS, PIS/Cofins e ICMS ad rem) o desconto da subvenção não muda a base, e o contador confirma antes de qualquer regra (Q171-C2)? | Sim |
| **Q171-8** | Aplico tudo no próximo "consolidar", junto com os documentos 157, 150 e 170? | Sim |

## 10.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q171-C1** | Subvenção recebida pelo produtor ou importador (custeio, por litro vendido): é receita? Entra na base de PIS/Cofins, IRPJ e CSLL? Qual a conta e o tratamento na ECF? Cabe em `Cad_Subvencao_Investimento` ou precisa de tratamento próprio? | Só registro; sem lançamento e sem tributo |
| **Q171-C2** | O desconto dado ao comprador por causa da subvenção entra na base de algum tributo (ICMS ad rem, PIS/Cofins por unidade, CBS por quantidade, IRPJ do comprador)? É desconto incondicional (`Valor_Desconto_Item`)? | Não altera a base; campo próprio, fora do desconto incondicional |
| **Q171-C3** | "Diesel de uso rodoviário comercializado" (MP 1.363): como o ERP identifica o produto na nota (código ANP, CFOP, destinação do comprador)? | `Condicao_Aplicacao` em texto; item pendente até a regra |
| **Q171-C4** | Quem sai de um programa para aderir a outro (MP 1.363, art. 5º): o que acontece com as vendas do período anterior (quem cobra qual valor)? | Adesão nova encerra a anterior no dia; os itens seguem o programa vigente na data |
| **Q171-C5** | 2027: a subvenção continua e se soma à CBS por unidade? A regra da Portaria conjunta 14 (referência de fevereiro de 2026 nos meses de redução) muda a carga da `Cad_Aliquota_Combustivel`? | Não afeta; a carga vem da Portaria MF 3.074 |
| **Q171-C6** | Devolução de tributo ("cashback", MP 1.358 e o R$ 0,35 do diesel A): é crédito, recebimento ou redução do tributo a pagar? Como se registra? | `Tipo_Apoio = devolucao_de_tributo`, mesmo requerimento; sem lançamento |
| **Q171-C7** | GLP importado: o ato fixa por tonelada (R$ 850) e o catálogo usa o quilograma: o valor é convertido (R$ 0,85 por quilograma) e a unidade original fica no ato? | Conversão no cadastro, com o ato citado |
| **Q171-C8** | Valor alterado com menos de 15 dias de aviso (MP 1.363): vale mesmo assim ou só depois do aviso? | Vale na data do ato; o ERP só avisa |
| **Q171-C9** | Subvenção a receber: reconhece-se na venda, no protocolo ou no pagamento? | Título só no protocolo |

## 10.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q171-E1** | Qual campo da NF-e leva o destaque do desconto exigido pela MP 1.363 (`vDesc` do item, informação adicional ou grupo próprio)? Preciso do leiaute ou da nota técnica. |
| **Q171-E2** | Algum cliente ou fornecedor da Mlegate é produtor, refinaria, importador ou distribuidor de diesel ou GLP que adere ao programa? Isso responde à Q171-3. |
| **Q171-E3** | A MP 1.363 autoriza o compartilhamento de dados entre a RFB e a ANP. O ERP precisa exportar algo das notas para o requerimento, ou o órgão lê direto da NF-e? |
| **Q171-E4** | O contas a receber tem tipo de título para a subvenção, com o órgão pagador como participante? Confirmar antes de ligar `ID_Titulo` do requerimento. |
| **Q171-E5** | O PDV de posto mostra o desconto da subvenção no cupom ou na bomba (NFC-e)? Ele já vem do preço, ou o ERP precisa lançá-lo? |
| **Q171-E6** | O ERP já emitiu notas de diesel ou GLP em 2026 com desconto de subvenção? Precisamos do histórico do período? |

# 11. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **Não li nenhum texto de lei, MP, portaria ou decreto do programa.** As fontes são notícias, o resumo do Senado sobre a MP 1.363 e o comunicado do Ministério da Fazenda; as datas e os valores não batem entre si em alguns pontos.
3. **Nenhum valor de subvenção entra na carga.** As tabelas de programa e de valor ficam vazias.
4. **Não trato do tratamento contábil nem tributário da subvenção** (Q171-C1 e Q171-C2). O ERP só registra.
5. **Não achei continuidade da subvenção em 2027.** O desenho funciona com ou sem programa.
6. **As leituras minhas** (o desconto não muda a base por unidade; o título nasce no protocolo; a adesão nova encerra a anterior) estão marcadas e vão ao contador; nenhuma vira regra no código.

# Anexo A. O que li sobre os valores de 2026 (referência para conferência, **sem carga**)

| Programa e ato | Combustível | Valor lido | Período lido | Fonte |
|---|---|---|---|---|
| MP 1.340 (12/03/2026) | Diesel | R$ 0,32 por litro | até 31/05/2026 | Notícias |
| MP 1.349 (07/04/2026) | Diesel nacional | R$ 0,80 por litro | dois meses, até 31/05/2026 | Notícia de 06/04/2026 |
| MP 1.349 (07/04/2026) | Diesel importado | R$ 1,20 por litro | dois meses, até 31/05/2026 | Notícia de 06/04/2026 |
| MP 1.349 (07/04/2026) | GLP importado | R$ 850 por tonelada (R$ 0,85 por quilograma) | dois meses, prorrogados até o fim de julho | Notícias |
| MP 1.363 (30/05/2026) | Diesel de uso rodoviário | R$ 1,12 por litro | 01/06/2026 a 31/12/2026 | Resumo do Senado |
| Portaria MF 2.813/2026 | Diesel | mais R$ 1,00 por litro | data não lida | Comunicado do Ministério da Fazenda |
| Portaria MF 2.946/2026 (25/09/2026) | Diesel | R$ 2,12 por litro no total | a partir de 27/09/2026 (MP 1.391); fim não lido | Comunicado do Ministério da Fazenda |
| Desconto no diesel A | Diesel A | R$ 0,35 por litro (devolução de tributo) | a partir de 01/06/2026 | Notícias |

**Para carregar quando os textos chegarem:** uma linha em `Cad_Combustivel_Programa_Apoio` por ato e uma linha em `Cad_Combustivel_Programa_Valor` por valor e período, com `Origem_Valor` e `Situacao_Dado = provisorio` até o contador validar.

# Anexo B. Cobertura: o que cada fonte pede e onde está

| O que a fonte pede | Onde está |
|---|---|
| Valor por litro ou quilograma, por combustível | `Cad_Combustivel_Programa_Valor.Valor_Por_Unidade` |
| Valor muda por período e por ato | `Vigencia_Inicio` e `Vigencia_Fim`; `Ato_Divulgacao`; `Data_Publicacao` |
| Valores diferentes para nacional e importado | `Origem_Produto` |
| Produtor e importador autorizados pela ANP como beneficiários | `ID_Tipo_Agente` (documento 170, `agente_cadeia_combustiveis`) e `Cad_Participante_Autorizacao_Anp` |
| Adesão por termo, desistência voluntária | `Cad_Participante_Adesao_Programa` |
| Sair do programa anterior para aderir | `Veda_Cumulacao_Com_Outros_Programas` e `Observacao` da adesão |
| Desconto exato no preço de venda | `Mov_Combustivel_Subvencao_Item.Valor_Desconto_Concedido` e o aviso de diferença |
| Destaque do desconto na NF-e | `Destacado_Na_Nota` (campo do leiaute: Q171-E1) |
| Pagamento pela ANP em até 30 dias | `Prazo_Pagamento_Dias`; `Mov_Combustivel_Subvencao_Requerimento` |
| Alteração do valor com 15 dias de aviso | `Aviso_Previo_Alteracao_Dias` e o aviso |
| Zerar ou reduzir tributo por período | `Cad_Aliquota_Combustivel` (linha temporária) e a tabela de PIS/Cofins por unidade, que já existe |
| Devolução de tributo ("cashback") | `Tipo_Apoio = devolucao_de_tributo` |
| Tratamento tributário e contábil da subvenção | **Fora** deste desenho (Q171-C1 e Q171-C2) |
| Continuidade em 2027 | Não achei; o desenho funciona sem programa vigente |

