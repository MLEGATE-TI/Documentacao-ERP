**ERP — ESPECIFICAÇÃO TÉCNICA · FASE 2 · MÓDULO 6**

**Tesouraria**

*Conta bancária, extrato, conciliação, remessa/retorno bancário (CNAB, API, Open Finance), painel de gestão de caixa, aging, devedores duvidosos e régua de cobrança*

*Revisão 15 --- consolidação da revisão 59 do dicionário (documento 250, versão 44 (D-N680, D-N688 e D-N689: meio de transmissão no canal, layout por carteira e convênio de folha em parâmetro, aprovados por Alberto)): 2 entidades existentes alteradas; o campo Meio_Transmissao no canal da conta (portal_manual, host_a_host, api, van) e o campo Layout_Cnab na carteira, que troca o layout padrão da conta (documento 250, Q250-67 e Q250-63).*

*Revisão 14 --- consolidação da revisão 58 do dicionário (documento 250, versão 34 (D-N666 e D-N675: boleto com ou sem Pix em parâmetro global e débito veicular do Bradesco)): 1 entidade nova (anexo, seção 16); 2 entidades existentes alteradas; o parâmetro global do boleto com ou sem Pix (`Cad_Cobranca_Parametro`, com vigência) e o valor `debito_veicular` em `Produto` da matriz de capacidades e do canal da conta (documento 250, D-N666 e D-N675).*

*Revisão 13 --- consolidação da revisão 56 do dicionário (documento 250, versão 16 (D-N639 a D-N658: motor de envio bancário para qualquer banco, pelas recomendações; sem o estoque proativo do documento 251)): 15 entidades novas (anexo, seção 15); 5 entidades existentes alteradas; o motor de envio bancário para qualquer banco: 15 entidades novas (driver, capacidades, canal, webhook, mensagem, histórico, mapa de ocorrências, DDA, Pix Automático, dados de tributo e de cobrança do item e certificados dos bancos) e 53 campos novos na remessa, no item de remessa, no retorno, no item de retorno e no extrato (documento 250).*

*Revisão 12 --- consolidação da revisão 25 do dicionário (documentos 94, 99, 107, 116, 120, 123 a 129 e 132, com as respostas de Alberto de 26 e 27/10/2026): 1 entidades novas (anexo, seção 14); 3 entidades existentes alteradas; a ordem de pagamento ao exterior, o retorno com contrato, taxa e valor do câmbio e o indicador da conta bancária (documentos 124 e 129).*

*Revisão 11 --- consolidação da revisão 23 do dicionário (documentos 113 e 114, com as respostas de Alberto de 26/10/2026 (Q113-6 e Q114-1 a Q114-4)): 1 entidades existentes alteradas; valor boleto na forma de lançamento da remessa bancária (documento 113).*

*Revisão 10 --- consolidação da revisão 22 do dicionário (documentos 110, 111 e 112, com as respostas de Alberto de 26/10/2026): 1 entidades existentes alteradas; texto da conciliação bancária para a diferença em dinheiro do encontro de contas (documento 111).*

*Revisão 9 --- consolidação da revisão 21 do dicionário (documentos 100 a 106, com as respostas de Alberto de 22/10/2026): 1 entidades existentes alteradas; IBAN, código de roteamento e moeda da conta bancária; agência e número da conta opcionais fora do Brasil (documento 106).*

*Revisão 8 — construída junto com a revisão 42 da Fase 0: tipo lógico "código (n)" definido por Alberto — todo campo que identifica algo (inscrição, documento, agência, conta, número e série de nota, matrícula, código oficial) é caractere, nunca numérico: os zeros à esquerda fazem parte do código, e o padrão pode passar a aceitar letras ou mudar de tamanho, como aconteceu com o CNPJ alfanumérico. Campos revistos: Agencia, Agencia_Favorecido, Carteira_Cobranca, Chave_Pix, Chave_Pix_Favorecido, Codigo_Banco_Favorecido, Codigo_Barras, Conta_Favorecido, Convenio_Cobranca, Digito_Agencia, Digito_Conta, Documento_Banco, Nosso_Numero, Numero_Conta.*

*Revisão 7 — Bloco 1 (fundação) da validação geral do dicionário pedida por Alberto, construído junto com a revisão 41 da Fase 0 — vigência explícita em todas as tabelas com o trio Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros mestres referenciados; Cad_Conta_Bancaria passa a referenciar Cad_Instituicao_Financeira (Fase 0) em vez do código do banco em texto livre.*

*Revisão 6 — mecanismo transversal de fechamento de período (Fase 0, seção 10, revisão 37): a execução do pagamento (remessa, seção 5, e a baixa automática gerada pelo retorno bancário, seção 6) passa a respeitar o bloco de fechamento "tesouraria" — o MESMO bloco, não um bloco coordenado, que trava Mov_Titulo e Mov_Titulo_Baixa no documento Fase 2 Contas a Pagar/Receber (revisão 9 daquele documento, mesma consolidação), ainda que essas duas entidades estejam fisicamente cadastradas lá: nenhum pagamento pode ser executado com data dentro de uma competência já fechada, para a mesma Filial, naquele bloco*

*Revisão 5 — ciclo "consolidar": remessa de pagamento passa a cobrir a folha de verdade, pedido por Alberto — Mov_Remessa_Bancaria ganha ID_Tipo_Servico_Lote (fornecedor/salário/tributo, códigos CNAB 20/30/22); Mov_Remessa_Bancaria_Item ganha Forma_Lancamento=cartao_salario/codigo_barras, Codigo_Barras (Segmento O, tributo) e Tipo_Conta_Favorecido (conta-salário x corrente/poupança, Fase 0 revisão 30) — construído junto com a consolidação de Folha & RH (revisão 5) e Contas a Pagar/Receber (revisão 8)*

*Revisão 4 — ciclo "consolidar": confirmação, sem mudança estrutural, de que ID_Autorizacao_Api/Status_Autorizacao_Api já cobre de forma genérica o fluxo Pay by Bank; Revisão 3 — canais de transmissão CNAB/API/Open Finance, conta bancária com poupança, tela de consistência do retorno, notificação da régua, bandas de aging configuráveis, sugestão de devedor duvidoso e integração do bloqueio de crédito em CRM & Vendas, a pedido de Alberto*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o sumário e pressione F9 (ou clique com o botão direito e escolha "Atualizar campo").*

1\. Introdução

Este documento especifica o módulo de Tesouraria, no mesmo formato usado nos cinco módulos já entregues (Planejamento & Orçamento, Compras, Estoque, CRM & Vendas, Contas a Pagar/Receber): função e dados juntos, entidade por entidade, sempre referenciando os motores transversais da Fase 0 (Cad_Participante, Cad_Grupo_Economico, Cad_Conta_Contabil, Cad_Classe_Sistema, Cad_Empresa, Cad_Usuario) e o módulo que este documento estende diretamente — Contas a Pagar/Receber (Mov_Titulo, Mov_Titulo_Baixa, Limite de Crédito) — em vez de redefini-los.

"Vamos para o próximo passo", a instrução que abriu esta especificação, foi respondida escolhendo Tesouraria entre as duas opções que o próprio documento de Contas a Pagar/Receber deixava em aberto (seção 1 daquele documento: "Fica, portanto, como gancho explícito para quando esses dois módulos forem detalhados" — referindo-se a Tesouraria e Contabilidade & Fiscal) — Alberto confirmou Tesouraria. Segue exatamente a ordem do Documento Analítico original (Fase 2, junto de Contas a Pagar/Receber e Contabilidade & Fiscal).

O Documento Analítico descreve o módulo assim: "Funciona como painel de gestão, não como tela puramente operacional: tem visão prospectiva (o que vence nos próximos dias) e retrospectiva (o que ficou pendente de dias anteriores) — nunca apenas o dia corrente. Sugere aplicação financeira para sobra de caixa, sem impor, e não há parâmetro fixo de caixa mínimo — fica a critério do gestor com base na informação em tela. A régua de cobrança escala deliberadamente do gentil ao definitivo: um aviso discreto próximo do vencimento, uma notificação de pendência pouco depois do atraso, e só além de um número configurável de dias o bloqueio de novas vendas e a zeragem do limite de crédito — sempre com alerta cruzado para Vendas, Gestor de Vendas e Financeiro, porque cobrança nunca é assunto isolado da Tesouraria." Dependências declaradas: "Depende de: Contas a Pagar/Receber, bancos (API/CNAB) \| Alimenta: Contabilidade, painel de gestão executivo."

Este documento reaproveita, sem redefinir, o que os módulos anteriores já prepararam especificamente para este momento: Cad_Conta_Contabil.ID_Tipo_Conta=Banco (Fase 0, ver mapTable daquele documento) — cada conta bancária de fato (seção 2, abaixo) associa-se a uma ou mais dessas contas contábeis; Mov_Titulo e Mov_Titulo_Baixa (Contas a Pagar/Receber, seções 2 e 3) — o painel de gestão (seção 7) é uma consulta sobre eles, não uma tabela nova, e a conciliação bancária (seção 4) e a baixa automática por remessa/retorno bancário (seção 6) geram/casam registros neles sem mudar sua estrutura; e Limite de Crédito por Grupo Econômico/CNPJ Raiz/individual (Contas a Pagar/Receber, seção 6) — a régua de cobrança (seções 9 e 10) soma-se a ele como um segundo gatilho de bloqueio, independente, sem alterar aquela fórmula, agora integrado de fato em CRM & Vendas (seção 10).

*Assunção de escopo desta revisão, explícita para sua confirmação: este documento cobre a movimentação bancária de fato que Contas a Pagar/Receber deliberadamente deixou de fora (extrato, conciliação, remessa/retorno bancário, cadastro físico de conta bancária) e a régua de cobrança que o Documento Analítico atribui a este módulo. NÃO cobre: a integração de execução automática (rotina agendada que efetivamente dispara o aviso/notificação/bloqueio) — fica, como de costume neste dicionário, a critério da camada de aplicação; nem o cálculo de rendimento/perda de aplicação financeira em si (Mov_Conta_Contabil_Evento, já especificado em Contas a Pagar/Receber, seção 9).*

A Revisão 3 incorpora uma extensa sequência de comentários de Alberto sobre a Revisão 2, ao longo de várias rodadas — resumidos abaixo por tema, com o detalhe de cada um nas seções correspondentes:

- Canal de transmissão: Mov_Cnab_Remessa/Retorno e seus itens passam a se chamar Mov_Remessa_Bancaria/Mov_Retorno_Bancario (nome canal-neutro), com um novo campo Canal_Transmissao {arquivo_cnab, api, open_finance} e rastreio do provedor técnico de integração (ex.: Celcoin) via ID_Provedor_Integracao — seções 5 e 6.

- Conta bancária: a mesma chave banco+agência+conta passa a poder representar até três contas contábeis simultâneas — corrente, poupança e aplicação — seção 2.

- Extrato: refinamento da origem de importação para incluir a API de Dados Cadastrais e Transacionais do Open Finance, e critério explícito de sugestão automática de classificação — seção 3.

- Retorno bancário: mesmo detalhamento de valores (principal, desconto, abatimento, multa, juros, IOF) já usado na remessa, e uma tela de consistência estruturada para tratar ocorrências sem remessa correspondente — seção 6.

- Painel de gestão: bandas de aging configuráveis por empresa, com personalização individual por usuário — seção 7.

- Devedores duvidosos: sugestão automática a partir do aging, com efetivação sempre manual — seção 8.

- Régua de cobrança: canal de notificação explícito (CRM + e-mail, via o novo cadastro de e-mails do participante em Fase 0) e integração de fato do gatilho de bloqueio dentro de Mov_Cotacao_Venda (CRM & Vendas), sempre no nível de grupo econômico — seções 9 e 10.

*Dois patches em módulos já entregues acompanham esta revisão, fechando ganchos que vinham desde a Revisão 2 deste documento: Contas a Pagar/Receber (Mov_Titulo_Baixa ganha origem CNAB/manual) e CRM & Vendas (integração do bloqueio de crédito/cobrança dentro da cotação de venda) — ambos detalhados nas seções 6, 10 e 11.*

2\. Conta Bancária

Fase 0 já previa, desde antes de qualquer módulo financeiro existir, que Cad_Conta_Contabil.ID_Tipo_Conta=Banco restringiria "a escolha de conta numa baixa financeira" — mas aquela entidade é o registro CONTÁBIL da conta (plano de contas, CTA, saldo). Falta o registro BANCÁRIO de fato: agência, número, banco, dados de cobrança. Esta seção fecha essa lacuna com uma extensão da identidade bancária física — cada conta bancária real do dia a dia É uma Cad_Conta_Bancaria (agência, número, banco) mais os dados operacionais abaixo.

Comentário de Alberto sobre a Revisão 2: a mesma chave banco+agência+conta pode representar, ao mesmo tempo, conta corrente, poupança E aplicação — não apenas corrente+aplicação, como a Revisão 2 assumia. A separação contábil em si já era garantida pela estrutura existente desde antes deste documento — Mov_Lancamento sempre referencia UMA Cad_Conta_Contabil específica, e o saldo de cada uma já é apurado de forma independente por Cad_Conta_Contabil.ID_Tipo_Conta. O que faltava era só a Cad_Conta_Bancaria conseguir apontar para as TRÊS pontas contábeis que podem compartilhar a mesma identidade bancária, não só duas — por isso o vínculo, nesta revisão, passa a três, todos opcionais (a estrutura não impõe qual deles é obrigatório, já que uma conta pode existir só para aplicação vinculada a outra agência/conta, por exemplo). O campo Tipo_Conta_Bancaria {corrente, poupanca}, que a Revisão 2 mantinha como modalidade bancária da conta, fica redundante com essa mudança — assumia um único tipo por linha de Cad_Conta_Bancaria, o que deixou de ser verdade; é removido nesta revisão, e o tipo de cada ponta passa a ser inferido diretamente por qual(is) vínculo(s) estão preenchidos.

Cad_Conta_Bancaria

Os dados bancários operacionais de uma conta — agência, número, banco, e os parâmetros necessários para cobrança (convênio/carteira) e para arquivos CNAB. Pode amarrar até três contas do plano de contas (Cad_Conta_Contabil): corrente, poupança e aplicação, cada uma independente, todas opcionais estruturalmente.

*Vigência: sim — mesmo tratamento de vigência de Cad_Conta_Contabil, do qual esta entidade é uma extensão direta.*

|                                 |                                                                        |                                                                                                                                                                                                                                                                                                                         |
|---------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Conta_Bancaria** | *identificador* | — |
| **ID_Conta_Bancaria_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Conta_Bancaria_Versao). ID_Conta_Bancaria é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Conta_Contabil_Corrente** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco, opcional)* | O vínculo contábil do lado conta corrente. Deixou de ser obrigatório nesta revisão (3): uma Cad_Conta_Bancaria que representa só uma poupança ou só uma aplicação vinculada a outra conta, por exemplo, pode não ter lado corrente — regra de negócio (pelo menos um dos três vínculos preenchido), não estrutural. |
| **ID_Conta_Contabil_Poupanca** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Banco, opcional)* | Adicionado nesta revisão (3), a pedido de Alberto: a mesma chave banco+agência+conta pode ter, além da corrente, um saldo de poupança sob sua própria conta contábil. |
| **ID_Conta_Contabil_Aplicacao** | *referência (Cad_Conta_Contabil, ID_Tipo_Conta = Aplicação, opcional)* | Preenchido quando esta mesma agência/conta também movimenta uma aplicação financeira vinculada — o saldo em aplicação fica, contabilmente, numa Cad_Conta_Contabil própria (Aplicação), separada da corrente e da poupança, mas identificada pela mesma Cad_Conta_Bancaria física. |
| **ID_Filial** | *referência (Cad_Filial)* | A filial titular da conta, perante o banco. |
| **ID_Instituicao_Financeira** | *referência (Cad_Instituicao_Financeira, Fase 0)* | Substitui o antigo Codigo_Banco em texto livre (revisão 7): o banco pelo cadastro do BACEN — código COMPE e ISPB. |
| **Agencia** | *código (até 5), opcional* | Revisão 21 (D-N351, documento 106): opcional; obrigatória quando a instituição é brasileira. |
| **Digito_Agencia** | *código (1), opcional* | — |
| **Numero_Conta** | *código (até 20), opcional* | Revisão 21 (D-N351, documento 106): opcional; obrigatório quando a instituição é brasileira. No exterior vale o número ou o IBAN (um dos dois). |
| **Digito_Conta** | *código (até 2), opcional* | — |
| **Iban** | *código (34), opcional* | Revisão 21 (D-N351): O IBAN da conta, quando o país usa. |
| **Tipo_Identificador_Conta** | *enumeração {agencia_numero, iban}* | Revisão 25 (D-N377 e D-N379 a D-N381, documento 129, Q129-1, Q129-3 e Q129-8, respondidas por Alberto em 27/10/2026): como a conta é identificada: por agência e número ou pelo IBAN. Obrigatório. Na carga das contas atuais, agencia_numero. No Brasil, agência e número são obrigatórios e identificam sempre; o IBAN, opcional, representa a mesma conta, e iban como principal em instituição brasileira **bloqueia**. Fora do Brasil o campo diz qual é o principal: com agencia_numero, Numero_Conta é obrigatório; com iban, o Iban é obrigatório. Conferência de aviso do IBAN brasileiro (29 posições: BR, 2 dígitos de controle, ISPB de 8, agência de 5 sem dígito, conta de 10 com dígito, tipo de conta e titular) contra o ISPB da instituição, a agência e o número. A unicidade (mesmo IBAN, ou mesma instituição, agência e número, na mesma vigência) é conferida pela camada de integração em cada identificador preenchido. |
| **Codigo_Roteamento** | *código (20), opcional* | Revisão 21 (D-N351): O identificador local do banco ou agência, quando o país usa: ABA nos EUA, BSB na Austrália, sort code no Reino Unido, entre outros. Um campo só, porque cada país usa um só tipo. |
| **ID_Moeda_Conta** | *referência (Cad_Moeda), opcional* | Revisão 21 (D-N351): A moeda da conta. Vazio vale a moeda funcional da empresa. Serve para avisar quando o título está em outra moeda (Q106-4). |
| **Convenio_Cobranca** | *código (até 20), opcional* | Código do convênio de cobrança junto ao banco — exigido para gerar remessa de cobrança (seção 5) nesta conta. |
| **Carteira_Cobranca** | *código (até 20), opcional* | Código da carteira de cobrança associada ao convênio. |
| **Layout_Cnab** | *enumeração {240, 400}, opcional* | O layout usado nos arquivos de remessa/retorno desta conta quando Canal_Transmissao=arquivo_cnab (seção 5) — vazio quando a conta só opera por API/Open Finance. |
| **Chave_Pix** | *código (até 77), opcional* | — |
| **Data_Encerramento** | *data, opcional* | Quando preenchida, a conta está encerrada para novas baixas/remessas, mas seu histórico (extrato, conciliação, remessas/retornos já processados) permanece consultável — nenhum Status separado, mesma filosofia de "nunca armazenar o que é derivável": conta ativa é, simplesmente, Data_Encerramento nula ou futura. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 21 --- campos novos: Iban, Codigo_Roteamento, ID_Moeda_Conta; campos alterados: Agencia, Numero_Conta.*

*Revisão 25 --- campos novos: Tipo_Identificador_Conta.*

3\. Extrato Bancário

O registro literal do que o banco informa ter movimentado em uma conta — via arquivo de retorno CNAB, API bancária, API de Open Finance, ou lançado manualmente quando nenhuma automação está disponível. Fidelidade ao valor real, mesma filosofia de todo o dicionário: esta linha nunca é editada para "corrigir" o que o banco informou — uma divergência é tratada na conciliação (seção 4), nunca reescrevendo o extrato.

Mov_Extrato_Bancario

Uma linha de movimento bancário, como informado pelo próprio banco.

*Vigência: não — é o registro de um evento externo (o que o banco informou), nunca editado depois de importado; a classificação é preenchida à parte, sem alterar os demais campos.*

|                                   |                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------------|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Linha_Extrato** | *identificador* | — |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | — |
| **Data_Movimento** | *data* | A data em que o banco processou o movimento — não necessariamente a data de importação deste registro no sistema. |
| **Tipo** | *enumeração {credito, debito}* | Mesma lógica já usada em Mov_Conta_Contabil_Evento e Mov_Titulo (Contas a Pagar/Receber): puramente estrutural, decide o sinal do Valor. |
| **Valor** | *número* | Sempre positivo — o sinal vem de Tipo, nunca do próprio valor. |
| **Historico_Banco** | *texto* | A descrição literal enviada pelo banco — texto livre, nunca reinterpretado ou editado por este sistema. |
| **Documento_Banco** | *código (até 30), opcional* | O identificador que o próprio banco atribui ao movimento (nosso número, código de transação, id de PIX), quando informado. |
| **Origem_Importacao** | *enumeração {cnab_retorno, api_banco, api_open_finance, manual}* | Como esta linha chegou ao sistema. api_open_finance, adicionado nesta revisão (3): a linha veio da API de Dados Cadastrais e Transacionais do Open Finance (extrato/saldo em near-real-time, defasagem regulatória de até 5 minutos), diferente de api_banco (API proprietária do próprio banco onde a Mlegate já tem conta) e de cnab_retorno (arquivo em lote). |
| **ID_Retorno_Item** | *referência (Mov_Retorno_Bancario_Item, opcional)* | Preenchido quando Origem_Importacao=cnab_retorno — de qual item do arquivo de retorno (seção 6) esta linha de extrato nasceu. |
| **Data_Importacao** | *data/hora* | Quando este registro entrou no sistema — pode ser bem depois de Data_Movimento, em importação em lote; em near-real-time quando Origem_Importacao=api_open_finance ou api_banco. |
| **ID_Classificacao** | *referência (Cad_Classe_Sistema, domínio = tipo_classificacao_extrato, opcional)* | Muitas vezes só o Historico_Banco (texto livre do banco) não permite identificar do que se trata a linha — este campo dá uma categoria de triagem (ex.: tarifa, pix_recebido, pix_enviado, ted, boleto_pago, rendimento, emprestimo, transferencia_entre_contas, outro), independente/anterior à conciliação (seção 4, o vínculo estrutural com o registro interno específico). Domínio aberto, mesmo padrão de Cad_Classe_Sistema já usado no resto do dicionário. |
| **Tipo_Classificacao** | *enumeração {automatica, manual}, opcional* | Automática quando o sistema sugere a classificação reaproveitando o Motor de Regras (Fase 0) — ver critério abaixo —, manual quando um usuário classifica diretamente. |
| **ID_Participante_Classificacao** | *referência (Cad_Participante, opcional)* | Quem confirmou a classificação — preenchido mesmo quando Tipo_Classificacao=automatica, porque Alberto foi explícito que a classificação automática precisa de validação do operador, não é aplicada sem revisão humana. |
| **Data_Classificacao** | *data, opcional* | — |
| **Codigo_Lancamento_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O código do lançamento como o banco manda (o `codigoLancamento` do Bradesco tem 5 posições; a FAQ de tributos cita 907 tributos, 978 gás, 982 água, 983 luz e 984 telefone). O mapa de ocorrências (R10) o traduz em tipo de lançamento; sem mapa, alerta |
| **Saldo_Apos_Lancamento** | *número, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O saldo da conta logo depois do lançamento, como o banco devolve; serve para conferir o extrato importado, linha a linha, contra o saldo do banco |
| **Situacao_Lancamento** | *enumeração {definitivo, do_dia, futuro, em_processamento}, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Valor `em_processamento` na 7: {definitivo, do_dia, futuro, em_processamento}: o extrato do Bradesco traz D-1 e o histórico (definitivos) e também o **D0** e os **lançamentos futuros** (provisórios); vazio = definitivo (R49). `em_processamento` é o tipo 3 do extrato do BB (R57) |
| **Categoria_Febraban_Lancamento** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, extrato em CNAB 240 v5, campo E012: a categoria padrão FEBRABAN do lançamento, de 3 dígitos: débitos 101 a 122 e créditos 201 a 223 (por exemplo 120 e 209, transferência interbancária; 223, crédito de Pix por QR Code). Serve à conciliação entre bancos sem depender do texto do histórico (R103) |
| **Documento_Contrapartida** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O CPF ou CNPJ da outra parte do lançamento, quando o banco informa (BB: até 15 posições, com o indicador de pessoa física ou jurídica); serve à conciliação por pagador |
| **Codigo_Banco_Contrapartida** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O banco da outra parte (BB: o código de compensação, e também o ISPB) |
| **Agencia_Contrapartida** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A agência da outra parte |
| **Conta_Contrapartida** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A conta da outra parte, com o dígito (BB: até 20 posições mais o dígito); o ERP guarda como veio, sem validar |
| **Identificador_Unico_Transacao** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O identificador único da transação (BB: até 64 posições; no Pix, o `E2eid`, de 32). `Documento_Banco` tem 30 posições e **não comporta** o `E2eid`; este campo evita cortá-lo e casa a linha do extrato com o Pix do retorno |

*Revisão 56 --- campos novos: Codigo_Lancamento_Banco, Saldo_Apos_Lancamento, Situacao_Lancamento, Categoria_Febraban_Lancamento, Documento_Contrapartida, Codigo_Banco_Contrapartida, Agencia_Contrapartida, Conta_Contrapartida, Identificador_Unico_Transacao.*

*Critério da sugestão automática de classificação, precisado por Alberto nesta revisão: como o extrato traz pouca informação estruturada, a sugestão do Motor de Regras precisa cruzar banco (Cad_Conta_Bancaria.ID_Instituicao_Financeira, via ID_Conta_Bancaria), Historico_Banco (o texto livre) e Tipo (crédito/débito) — o mesmo texto de histórico pode significar coisas diferentes conforme o banco que o emite e conforme o valor for entrada ou saída. Os três campos já existem na estrutura acima; nenhum campo novo foi necessário — é uma regra de configuração do Motor de Regras, não uma mudança de dados.*

4\. Conciliação Bancária

Casar cada linha de extrato (seção 3) com o evento interno correspondente — uma baixa de título, um encontro de contas, um evento de conta financeira (rendimento, perda, tarifa) ou um lançamento manual. Mesmo padrão de referência genérica (Origem_Tipo/ID_Origem) já usado em Mov_Aprovacao_Instancia e Mov_Lote_Lancamento (Fase 0). Uma linha de extrato pode ser casada com mais de um evento interno (ex.: um PIX recebido que liquida três títulos de uma vez) e um mesmo evento interno também pode ser coberto por mais de uma linha de extrato (ex.: mais de um depósito para o mesmo documento) — as duas direções são igualmente reais, não uma mais rara que a outra.

Mov_Conciliacao_Bancaria

O casamento entre uma linha de extrato e um evento interno, total ou parcial.

*Vigência: não — é o registro de um evento; uma conciliação feita errada é desfeita por uma nova linha negativa (ou removendo o vínculo), nunca editando o valor original.*

|                      |                                                                                                        |                                                                                                                                                                                                                                                                                                                                                                                  |
|----------------------|--------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Conciliacao** | *identificador* | — |
| **ID_Extrato** | *referência (Mov_Extrato_Bancario)* | — |
| **Origem_Tipo** | *enumeração {mov_titulo_baixa, mov_titulo_encontro_contas, mov_conta_contabil_evento, mov_lancamento}* | A que tipo de evento interno esta conciliação está ligando o extrato. mov_titulo_encontro_contas cobre o caso de um recebimento único que na prática liquidou parte por baixa e parte por encontro de contas do mesmo participante — a conciliação passa a poder referenciar também o evento de encontro de contas envolvido, não só a baixa residual que de fato tocou o banco. Revisão 22 (D-N353, documento 111): na diferença em dinheiro de um encontro de contas, a linha do extrato é conciliada contra o encontro (Mov_Titulo_Encontro_Contas, que guarda Valor_Diferenca e a conta de banco ou caixa); as baixas de tipo encontro não tocam o banco (Valor_Financeiro zero). |
| **ID_Origem** | *referência genérica* | Conforme Origem_Tipo: ID_Baixa de Mov_Titulo_Baixa (Contas a Pagar/Receber, seção 3); ID_Encontro de Mov_Titulo_Encontro_Contas (Contas a Pagar/Receber, seção 5); ID_Evento de Mov_Conta_Contabil_Evento (Contas a Pagar/Receber, seção 9); ou ID_Lancamento de Mov_Lancamento (Fase 0), para um lançamento manual sem evento financeiro estruturado por trás. |
| **Valor_Conciliado** | *número* | A parte do valor da linha de extrato coberta por este casamento especificamente — permite ratear uma única linha de extrato entre vários eventos internos, ou o inverso. |
| **Data_Conciliacao** | *data* | — |
| **Tipo_Match** | *enumeração {automatico, manual}* | Automático quando o próprio sistema casa por valor e data (ou pela referência que vem do retorno bancário, seção 6); manual quando um usuário faz o casamento à mão. |
| **ID_Participante** | *referência (Cad_Participante, opcional)* | O colaborador que fez a conciliação manual — vazio quando Tipo_Match=automatico. |

*Revisão 22 --- campos alterados: Origem_Tipo.*

*Status de conciliação de uma linha de extrato — fórmula, sem campo próprio, mesma filosofia de "saldo/status nunca armazenado" de todo o dicionário: uma linha está PENDENTE quando a soma de Mov_Conciliacao_Bancaria.Valor_Conciliado contra ela é zero; PARCIALMENTE CONCILIADA quando essa soma é maior que zero e menor que Mov_Extrato_Bancario.Valor; e CONCILIADA quando a soma iguala o valor da linha. Nenhum destes três estados é armazenado — todos calculados no momento da consulta.*

5\. Remessa Bancária (Cobrança e Pagamento)

O envio ao banco — registrando um título a receber para cobrança (boleto/Pix cobrança) ou uma ordem de pagamento a um fornecedor (título a pagar). Cabeçalho e item, mesmo padrão já usado em outras entidades deste dicionário (cotação e seus itens, em CRM & Vendas; empréstimo e suas parcelas, em Contas a Pagar/Receber). Renomeado nesta revisão (3) de Mov_Cnab_Remessa/Item para Mov_Remessa_Bancaria/Item: Alberto confirmou que quer ter todas as informações prontas tanto para atender o arquivo CNAB quanto uma API (Pix API ou Open Finance) a partir da mesma estrutura — quando o motor de envio for construído, ele já deve ter os dados necessários para transmitir por qualquer um dos canais — e pediu um nome genérico que funcione para os dois. **Revisão 56 (documento 250):** o motor de envio foi desenhado e consolidado: cada envio passa pelo **driver** do banco e do canal da conta (`Cad_Banco_Driver` e `Cad_Conta_Bancaria_Canal`), com o histórico em `Mov_Banco_Mensagem` e `Mov_Remessa_Bancaria_Evento`, e a remessa ganha o canal, o estado de processamento, o lote e a chave de idempotência; os dados que só alguns produtos usam ficam em `Mov_Remessa_Bancaria_Item_Cobranca` e `Mov_Remessa_Bancaria_Item_Tributo` (seção 15). Primeiro entram cobrança, recebimento, folha e pagamentos; DDA e Pix Automático estão desenhados e ficam desligados até a fase 2 (R115).

Mov_Remessa_Bancaria

O cabeçalho de um envio ao banco — um arquivo CNAB (lote) ou um agrupador lógico de envios individuais por API/Open Finance.

*Vigência: não — é o registro de um evento (a geração do arquivo ou a abertura do lote de envios por API).*

|                               |                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-------------------------------|------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Remessa** | *identificador* | — |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | — |
| **Tipo** | *enumeração {cobranca, pagamento}* | Cobrança: títulos a receber (Mov_Titulo, Tipo=receber) registrados para o banco cobrar do cliente. Pagamento: títulos a pagar (Mov_Titulo, Tipo=pagar) ordenados ao banco para pagamento a fornecedor. |
| **Canal_Transmissao** | *enumeração {arquivo_cnab, api, open_finance}* | Adicionado nesta revisão (3): decide se Numero_Sequencial_Arquivo/Nome_Arquivo se aplicam (só quando arquivo_cnab) ou se cada item é enviado individualmente em tempo real (quando api ou open_finance, esses dois campos ficam vazios — esta entidade passa a ser só um agrupador lógico por Data_Geracao). Os três valores fazem sentido tanto para Tipo=cobranca quanto para Tipo=pagamento: open_finance cobre tanto a iniciação de pagamento a fornecedor quanto o fluxo "Pay by Bank" de recebimento, em que o próprio cliente autoriza o pagamento à Mlegate no banco dele. |
| **ID_Provedor_Integracao** | *referência (Cad_Classe_Sistema, domínio = tipo_provedor_integracao_bancaria, opcional)* | Adicionado nesta revisão (3), a pedido de Alberto: qual provedor técnico processou este envio, quando não é o banco diretamente — ex.: um agregador/BaaS como a Celcoin, que pode operar como conta digital própria ou como camada de intermediação sobre a conta em banco tradicional. Domínio aberto (celcoin, banco_direto, outro); vazio quando Canal_Transmissao=arquivo_cnab, já que aí o "provedor" é sempre o próprio banco. |
| **Data_Geracao** | *data* | — |
| **Numero_Sequencial_Arquivo** | *número, opcional* | O sequencial exigido pelo layout CNAB do banco — controlado por conta bancária. Só quando Canal_Transmissao=arquivo_cnab. |
| **Nome_Arquivo** | *texto, opcional* | Só quando Canal_Transmissao=arquivo_cnab. |
| **ID_Tipo_Servico_Lote** | *referência (Cad_Classe_Sistema, domínio = tipo_servico_lote_cnab, opcional)* | Adicionado nesta revisão (5), pesquisado a pedido de Alberto ("tem layoutes no CNAB e nas APIs bancárias específicas para pagamento de colaboradores, verificar estas regras"): só quando Tipo=pagamento — o tipo de serviço do lote exigido pelo header de lote do CNAB 240 (campo distinto do tipo de serviço do arquivo), que classifica a NATUREZA do pagamento — fornecedor (código 20), salários (código 30, com suporte específico a crédito em conta e a cartão-salário), diversos (código 98) ou, quando o pagamento é de um tributo com código de barras (INSS, FGTS via GRF/GRRF), tributos (código 22, Segmento O do CNAB, layout distinto do Segmento A/B usado para fornecedor/salário). Domínio aberto, mesmo padrão já usado para os demais códigos oficiais deste dicionário. Um mesmo Mov_Remessa_Bancaria (um lote) reúne itens do mesmo tipo de serviço — a folha gera lotes separados por Mov_Titulo.Natureza_Titulo_Folha (Contas a Pagar/Receber, Fase 5) quando a natureza exige um tipo de serviço de lote diferente (ex.: líquido do colaborador em código 30, INSS/FGTS em código 22), decisão de agrupamento de aplicação, não estrutura nova aqui. |
| **ID_Conta_Bancaria_Canal** | *referência (Cad_Conta_Bancaria_Canal), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O canal usado (opcional, porque a remessa já existente não o tem) |
| **Status** | *enumeração {gerada, aguardando_envio, enviada, recebida_pelo_banco, aguardando_aprovacao_no_banco, aguardando_liberacao, parcialmente_processada, processada, rejeitada, cancelada}* | Revisão 56 (documento 250; D-N639 a D-N658): `aguardando_liberacao` (versão 7 do documento 250) é a espera pela **liberação que o próprio ERP dá por API** (PagBB do BB, R58), diferente de `aguardando_aprovacao_no_banco` |
| **Quantidade_Itens** | *número* | Revisão 56 (documento 250; D-N639 a D-N658): Total de itens |
| **Valor_Total_Remessa** | *número* | Revisão 56 (documento 250; D-N639 a D-N658): Soma dos valores (conferida com o trailer do arquivo) |
| **Data_Hora_Envio** | *data/hora, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Quando saiu |
| **Hash_Arquivo** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Impressão do arquivo, para detectar reenvio |
| **ID_Documento_Arquivo** | *referência (Cad_Documento), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O arquivo gerado (`Cad_Documento`) |
| **Id_Lote_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): BB, PagBB: o identificador do lote como o **cliente** o escolhe e o banco usa em toda consulta e no cancelamento (`idLote`, inteiro). O banco debita **o valor total do lote** de uma vez, por isso é a chave para conciliar essa linha do extrato (R58) |

*Revisão 56 --- campos novos: ID_Conta_Bancaria_Canal, Status, Quantidade_Itens, Valor_Total_Remessa, Data_Hora_Envio, Hash_Arquivo, ID_Documento_Arquivo, Id_Lote_Banco.*

Mov_Remessa_Bancaria_Item

Cada título incluído no envio — de cobrança ou de pagamento, conforme Mov_Remessa_Bancaria.Tipo. Campos pesquisados nos manuais oficiais CNAB 240 (Segmentos P/R para cobrança, A/B/C para pagamento) e, para API, na documentação do Bacen (Pix API) e do Open Finance Brasil — os mesmos conceitos de negócio valem para os dois canais, sem duplicação de campo.

*Vigência: não — é o registro de um evento.*

|                                |                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|--------------------------------|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Remessa** | *identificador* | — |
| **ID_Remessa** | *referência (Mov_Remessa_Bancaria)* | — |
| **ID_Titulo** | *referência (Mov_Titulo)* | O título a receber (cobrança) ou a pagar (pagamento) incluído. |
| **Nosso_Numero** | *código (até 20), opcional* | O identificador que o banco associa a este título assim que o processa — preenchido quando Tipo=cobranca; usado depois para casar automaticamente o item de retorno correspondente (seção 6). Quando Canal_Transmissao=api, o mesmo campo serve como txid (identificador de correlação gerado pelo recebedor, terminologia da API Pix) — mesmo conceito, sem precisar de campo duplicado. |
| **Valor_Principal_Remessa** | *número* | O valor do título/principal enviado ao banco, copiado do saldo em aberto de Mov_Titulo (Contas a Pagar/Receber, seção 2) no momento da geração; fidelidade ao valor real, não recalculado depois. Revisão 25 (D-N371, documento 124, Q107-1 e Q107-1b): quando o item tem ordem ao exterior (Mov_Remessa_Bancaria_Item_Exterior), o valor está na **moeda da ordem**, e não em reais. Uma remessa de pagamento tem só itens ao exterior ou só itens nacionais, e a conta de origem da remessa ao exterior fica em banco brasileiro. |
| **ID_Tipo_Documento_Cobranca** | *referência (Cad_Classe_Sistema, domínio = tipo_documento_cobranca, opcional)* | Só quando Tipo=cobranca: a espécie do título exigida pelo Segmento P do CNAB (ex.: DM/Duplicata Mercantil, NP/Nota Promissória, NS, ME, RC, CT, CS, DS, LC, ND, DD, EC, CPS, BP, outro). Domínio aberto, mesmo padrão já usado no resto do dicionário. Renomeado nesta revisão (3) de tipo_documento_cnab, para nome canal-neutro. |
| **Valor_Desconto_Remessa** | *número, opcional* | Só quando Tipo=cobranca — o desconto concedido se pago até Data_Limite_Desconto, conforme Segmento P. |
| **Data_Limite_Desconto** | *data, opcional* | Só quando Tipo=cobranca. |
| **Valor_Abatimento_Remessa** | *número, opcional* | Só quando Tipo=cobranca — Segmento P. |
| **Codigo_Multa** | *enumeração {nao_registra, valor_fixo, percentual}, opcional* | Só quando Tipo=cobranca — Segmento R do CNAB. |
| **Valor_Percentual_Multa** | *número, opcional* | Só quando Tipo=cobranca e Codigo_Multa≠nao_registra — o valor (em reais) ou o percentual da multa, conforme Codigo_Multa. |
| **Data_Multa** | *data, opcional* | Só quando Tipo=cobranca. |
| **Valor_Juros_Mora_Dia** | *número, opcional* | Só quando Tipo=cobranca — o valor de juros de mora por dia de atraso, conforme Segmento P. |
| **Data_Base_Mora** | *data, opcional* | Só quando Tipo=cobranca — a partir de quando a mora passa a contar, normalmente Data_Vencimento+1. |
| **Valor_IOF_Remessa** | *número, opcional* | Adicionado nesta revisão (3) — só quando Tipo=cobranca: o IOF eventualmente cobrado na operação, conforme Segmento P; já era citado no texto desde a revisão anterior, mas nunca tinha virado campo estrutural. |
| **Codigo_Banco_Favorecido** | *código (3), opcional* | Só quando Tipo=pagamento — Segmento A: o banco do fornecedor/beneficiário do pagamento. Pré-preenchido a partir de Cad_Participante_Dados_Bancarios (Fase 0) — a conta marcada Principal, ou escolhida pelo operador quando há mais de uma — mas continua sendo um campo próprio da remessa (cópia, não referência): o que foi de fato transmitido ao banco fica registrado aqui, mesmo que o cadastro do participante mude depois. Revisão 25 (D-N371, documento 124, Q107-1): no item da ordem ao exterior este campo fica **vazio**, porque banco estrangeiro não tem código de compensação brasileiro; Agencia_Favorecido e Conta_Favorecido recebem a cópia do dado bancário quando existirem, e o IBAN fica na ordem. |
| **Agencia_Favorecido** | *código (até 5), opcional* | Só quando Tipo=pagamento — mesma lógica de pré-preenchimento de Codigo_Banco_Favorecido. |
| **Conta_Favorecido** | *código (até 20), opcional* | Só quando Tipo=pagamento — mesma lógica de pré-preenchimento. |
| **Nome_Favorecido** | *texto, opcional* | Só quando Tipo=pagamento — o nome literal transmitido ao banco no Segmento A, mesmo quando derivável de Mov_Titulo.ID_Participante; fidelidade ao que foi de fato enviado. |
| **ID_Finalidade_Pagamento** | *referência (Cad_Classe_Sistema, domínio = tipo_finalidade_pagamento, opcional)* | Só quando Tipo=pagamento — o código de finalidade DOC/TED exigido pelo Segmento A. Domínio aberto. Renomeado nesta revisão (3) de tipo_finalidade_pagamento_cnab, para nome canal-neutro. |
| **Data_Pagamento** | *data, opcional* | Só quando Tipo=pagamento — a data solicitada ao banco para efetivar o crédito ao favorecido, distinta de Mov_Remessa_Bancaria.Data_Geracao (quando o envio foi gerado/aberto). |
| **Aviso_Favorecido** | *texto, opcional* | Só quando Tipo=pagamento — mensagem/aviso a ser enviado ao favorecido junto do pagamento, Segmento B. |
| **Forma_Lancamento** | *enumeração {credito_conta, doc, ted, pix, cartao_salario, codigo_barras, boleto, transferencia_internacional}, opcional* | Adicionado nesta revisão (3) — só quando Tipo=pagamento: a forma de lançamento do crédito ao favorecido, exigida no cabeçalho do lote (Segmento A) do CNAB 240 de pagamentos. Estrutura fixa do próprio mecanismo, mesmo critério de Codigo_Multa. cartao_salario e codigo_barras, adicionados nesta revisão (5), pesquisados a pedido de Alberto: cartao_salario cobre o crédito em cartão-salário, suportado pelo tipo de serviço de lote 30 (ID_Tipo_Servico_Lote, cabeçalho da remessa, acima) para colaboradores sem conta bancária cadastrada; codigo_barras cobre o pagamento de um tributo por código de barras (INSS via GPS, FGTS via GRF/GRRF), Segmento O do CNAB 240, layout estruturalmente diferente do Segmento A/B usado para fornecedor/salário em conta — ver Codigo_Barras, abaixo. Revisão 23 (D-N357, documento 113, Q113-6, respondida por Alberto em 26/10/2026): boleto é a forma de pagamento de boleto bancário, que no tipo da baixa corresponde à compensação de boleto (Q113-1). Só o valor entra agora. O dado próprio do boleto na remessa (o código de barras ou a linha digitável do título) não foi decidido: Codigo_Barras segue valendo só para o tributo (codigo_barras), e o de-para entre a forma e o tipo da baixa espera a Q113-5. Revisão 25 (D-N371, documentos 107 e 124, Q107-3, respondida por Alberto em 27/10/2026): transferencia_internacional é a ordem ao exterior; exige a linha de Mov_Remessa_Bancaria_Item_Exterior. A forma sugerida segue a precedência do documento 124: conta da empresa no exterior (formas 4 e 5 do Y520, que não passam por remessa), forma prevista no cadastro e, na ordem em moeda estrangeira, a forma 1 do Y520; o operador confirma ao gerar. A ordem só existe quando o banco do favorecido está no exterior (Q107-3a). |
| **Chave_Pix_Favorecido** | *código (até 77), opcional* | Adicionado nesta revisão (3) — só quando Forma_Lancamento=pix: a chave Pix do favorecido (Segmento B), até 99 caracteres conforme manual bancário. |
| **Tipo_Chave_Pix** | *enumeração {telefone, email, cpf_cnpj, aleatoria}, opcional* | Adicionado nesta revisão (3) — só quando Forma_Lancamento=pix: o tipo da chave informada em Chave_Pix_Favorecido, conforme indicador do Segmento B. |
| **Codigo_Barras** | *código (44), opcional* | Adicionado nesta revisão (5), pesquisado a pedido de Alberto — só quando Forma_Lancamento=codigo_barras: a linha digitável/código de barras do tributo a recolher (Segmento O do CNAB 240), substituindo dados de agência/conta do favorecido para este tipo de lançamento — o "favorecido" de um tributo é o próprio código de barras, não uma conta bancária. |
| **Tipo_Conta_Favorecido** | *enumeração {corrente, poupanca, conta_salario}, opcional* | Adicionado nesta revisão (5), pedido por Alberto ("existem tipos de contas específicas para salários que têm taxas diferentes") — só quando Tipo=pagamento e Forma_Lancamento é credito_conta/doc/ted/pix (vazio para codigo_barras, que não tem conta de favorecido): cópia de Cad_Participante_Dados_Bancarios.Tipo_Conta (Fase 0, revisão 30) no momento da geração — mesma lógica de pré-preenchimento/cópia já usada para Codigo_Banco_Favorecido/Agencia_Favorecido/Conta_Favorecido, acima: o que foi de fato transmitido ao banco fica registrado aqui, mesmo que o cadastro do participante mude depois. Distingue conta-salário (isenta de tarifa ao titular, Resolução CMN 3.402/2006) de conta corrente/poupança comum — informação que o próprio arquivo/API de pagamento por vezes exige informar explicitamente (o banco trata o crédito de forma diferente conforme o tipo de conta de destino). |
| **Valor_IR_Retido** | *número, opcional* | Adicionado nesta revisão (3) — só quando Tipo=pagamento: retenção de Imposto de Renda na fonte, conforme Segmento C (retenções e acréscimos), relevante para pagamento a fornecedor de serviço. |
| **Valor_ISS_Retido** | *número, opcional* | Adicionado nesta revisão (3) — só quando Tipo=pagamento — Segmento C. |
| **Valor_INSS_Retido** | *número, opcional* | Adicionado nesta revisão (3) — só quando Tipo=pagamento — Segmento C. |
| **Valor_IOF_Pagamento** | *número, opcional* | Adicionado nesta revisão (3) — só quando Tipo=pagamento — Segmento C. O lançamento contábil da retenção em si fica como gancho para a futura Contabilidade & Fiscal, mesmo padrão já usado para PECLD/devedores duvidosos (seção 8). |
| **ID_Autorizacao_Api** | *texto, opcional* | Adicionado nesta revisão (3) — só quando Canal_Transmissao=open_finance: o identificador de consentimento devolvido pela API, tanto para Tipo=pagamento (a Mlegate autoriza, no próprio banco, uma iniciação de pagamento ao fornecedor) quanto para Tipo=cobranca (o cliente autoriza, no banco dele, um pagamento direto à Mlegate — fluxo "Pay by Bank") — o campo Tipo já indica de qual dos dois fluxos se trata, não precisa de um campo de fluxo separado. |
| **Status_Autorizacao_Api** | *enumeração {aguardando_autorizacao, autorizado, recusado}, opcional* | Adicionado nesta revisão (3) — só quando Canal_Transmissao=open_finance: o estado do consentimento, do lado do banco/pagador — armazenado como veio, porque é um estado externo, não derivado de eventos internos (diferente da filosofia geral de "status nunca armazenado" deste dicionário). |
| **Status_Item** | *enumeração {incluido, enviado, confirmado, rejeitado, pago, devolvido, cancelado}* | Revisão 56 (documento 250; D-N639 a D-N658): {incluido, enviado, confirmado, rejeitado, pago, devolvido, cancelado} |
| **ID_Codigo_Movimento_Remessa** | *referência (Cad_Classe_Sistema, domínio = tipo_movimento_remessa_bancaria), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O comando de cobrança (`Cad_Classe_Sistema`, domínio novo `tipo_movimento_remessa_bancaria`: entrada, baixa, alteração de vencimento, protesto etc.) |
| **Seu_Numero** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Número do documento no sistema do cliente (texto até 25). O banco corta no limite dele: o Itaú aceita **10** e exige o campo quando há protesto; outras fontes falam em 15 a 20. O casamento do retorno usa o nosso número e o `txid`, não este campo (R26) |
| **Txid_Pix** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): `txid` do Pix ligado ao boleto ou ao pagamento |
| **Id_Externo_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O identificador que o banco dá ao título ao registrá-lo e que as instruções seguintes exigem (no Itaú, o `id_boleto`, um UUID de 36 posições; R33) |
| **Id_Location_Pix** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, boleto híbrido: o `idLoc` da **location reservada** antes do registro, para emitir o boleto sem internet na hora (só QR dinâmico com vencimento; R50) |
| **Codigo_Finalidade_Ted** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, TED por API: o código de finalidade da transferência (até 5 posições; a tabela do banco vai de 1 = tributos a 13 = tarifas de convênio e continua, e muda com o tipo de transferência). Leitura minha: o segmento A do CNAB 240 tem o mesmo conceito; conferir no manual |
| **Motivo_Baixa_Pedida** | *enumeração {cancelamento_do_titulo, recebido_por_fora, renegociacao, substituicao_do_boleto, outro}, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Quando o item é um **pedido de baixa**, por que o ERP pede: {cancelamento_do_titulo, recebido_por_fora, renegociacao, substituicao_do_boleto, outro}. O banco só conhece «baixa» (Itaú: movimento 02, pedido de baixa; Celcoin: baixa pedida pelo cedente ou pela destinatária); o motivo fica no ERP, para a contabilidade e para conferir o retorno (R107) |
| **Numero_Lista_Debito** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, Multipag, segmento 5: o número (9 dígitos, só numérico) da **lista de débito**, o grupo de pagamentos que o cliente **autoriza no canal do banco** antes do débito. Uma lista tem **uma modalidade e uma data**, e o número não se repete (R98) |
| **Horario_Debito** | *hora, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Segmento 5: o horário em que o cliente quer o débito do pagamento (6 posições, HHMMSS) |
| **Codigo_Lancamento_Especifico_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Segmento 5: o código (5 dígitos) que o banco usa para **contabilizar** o pagamento; define a mensagem da primeira linha do extrato (R103) |
| **Codigo_Mensagem_Segunda_Linha_Extrato** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Segmento 5: o código (5 dígitos) do histórico complementar da segunda linha do extrato |
| **Codigo_Camara_Ted** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Multipag: a câmara centralizadora da TED e do DOC (018, 700 ou 888, como o banco manda); vem de regra do driver, não de digitação |
| **Valor_Atualizado_Banco** | *número, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O valor total que o banco **calculou na consulta antes de pagar**, já com juros, multa e descontos até a data (Santander: `totalValue`; é o `paymentValue` que a confirmação manda de volta). Fica separado do valor do título: a diferença entre os dois é o que o ERP trata antes de confirmar (R87 e R11) |
| **Tipo_Destino_Ted** | *enumeração {entre_clientes, para_instituicao_financeira}, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Santander, TED por API: {entre_clientes, para_instituicao_financeira}: os dois destinos do banco, `STR0008` (entre contas de clientes) e `STR0006` (para conta de instituição financeira; a mesma escolha que o CNAB faz pela finalidade). O banco exige o campo (R90) |

*Revisão 23 --- valores de enumeração novos: Forma_Lancamento (+boleto).*

*Revisão 25 --- campos alterados: Valor_Principal_Remessa, Codigo_Banco_Favorecido; valores de enumeração novos: Forma_Lancamento (+transferencia_internacional).*

*Revisão 56 --- campos novos: Status_Item, ID_Codigo_Movimento_Remessa, Seu_Numero, Txid_Pix, Id_Externo_Banco, Id_Location_Pix, Codigo_Finalidade_Ted, Motivo_Baixa_Pedida, Numero_Lista_Debito, Horario_Debito, Codigo_Lancamento_Especifico_Banco, Codigo_Mensagem_Segunda_Linha_Extrato, Codigo_Camara_Ted, Valor_Atualizado_Banco, Tipo_Destino_Ted.*

6\. Retorno Bancário e Baixa Automática

O que o banco informa de volta sobre cada envio (ou sobre movimentos que nem passaram por remessa, como um Pix avulso) — liquidação, rejeição, entrada confirmada, entre outros, conforme o código de ocorrência que o próprio banco define, ou um evento de webhook individual quando o canal é API/Open Finance. Renomeado nesta revisão (3) de Mov_Cnab_Retorno/Item para Mov_Retorno_Bancario/Item, mesmo critério da remessa (seção 5). **Revisão 56 (documento 250):** o retorno guarda o código **como o banco mandou** e a ocorrência que o ERP entendeu pelo mapa (`Cad_Banco_Ocorrencia_Mapa`, seção 15), inclusive o **motivo da baixa**: só o pagamento baixa o título, e a baixa sem pagamento (caducidade, cancelamento, protesto) encerra a cobrança e mantém o título em aberto (R107 e R108).

Mov_Retorno_Bancario

O cabeçalho de um retorno recebido do banco — um arquivo CNAB (lote) ou o agrupador lógico de um evento de webhook individual (API/Open Finance).

*Vigência: não — é o registro de um evento (o recebimento do arquivo ou do evento de webhook).*

|                            |                                                                                          |                                                                                                                                                                                                                                           |
|----------------------------|------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Retorno** | *identificador* | — |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | — |
| **Canal_Transmissao** | *enumeração {arquivo_cnab, api, open_finance}* | Adicionado nesta revisão (3), mesmo critério do cabeçalho de remessa (seção 5): quando api ou open_finance, cada "retorno" corresponde a um evento de webhook individual em tempo real, não um arquivo em lote processado periodicamente. |
| **ID_Provedor_Integracao** | *referência (Cad_Classe_Sistema, domínio = tipo_provedor_integracao_bancaria, opcional)* | Mesmo campo e mesmo critério do cabeçalho de remessa (seção 5) — qual provedor técnico processou este retorno. |
| **Data_Recebimento** | *data* | — |
| **Nome_Arquivo** | *texto, opcional* | Só quando Canal_Transmissao=arquivo_cnab. |
| **ID_Conta_Bancaria_Canal** | *referência (Cad_Conta_Bancaria_Canal), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O canal |
| **ID_Banco_Mensagem** | *referência (Mov_Banco_Mensagem), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A mensagem que trouxe o retorno |
| **Hash_Arquivo** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Impressão do arquivo, para recusar o mesmo retorno duas vezes |
| **ID_Documento_Arquivo** | *referência (Cad_Documento), opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O arquivo recebido (`Cad_Documento`) |

*Revisão 56 --- campos novos: ID_Conta_Bancaria_Canal, ID_Banco_Mensagem, Hash_Arquivo, ID_Documento_Arquivo.*

Mov_Retorno_Bancario_Item

Cada ocorrência informada pelo banco.

*Vigência: não — é o registro de um evento.*

|                                 |                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|---------------------------------|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Retorno** | *identificador* | — |
| **ID_Retorno** | *referência (Mov_Retorno_Bancario)* | — |
| **ID_Item_Remessa** | *referência (Mov_Remessa_Bancaria_Item, opcional)* | Casado pelo Nosso_Numero/txid, quando o banco o devolve; nulo quando a ocorrência não é casável automaticamente (ex.: um crédito avulso sem remessa correspondente) — ver tela de consistência, abaixo. |
| **Tipo_Ocorrencia** | *enumeração {aceito, rejeitado, informativo}* | Puramente estrutural, decide como o sistema trata a ocorrência (ex.: se entra na fila de reenvio) independente do código específico — mesmo padrão "um único motor, direção diferente" já usado em Mov_Titulo.Tipo, Mov_Conta_Contabil_Evento.Tipo e Mov_Extrato_Bancario.Tipo. |
| **ID_Codigo_Ocorrencia** | *referência (Cad_Classe_Sistema, domínio = tipo_ocorrencia_retorno_bancario)* | O código de ocorrência do banco (liquidado, rejeitado, baixado, entrada confirmada, entre outros) — domínio aberto, um novo código bancário é um novo valor cadastrado, nunca uma mudança de estrutura. A classificação detalhada/textual; Tipo_Ocorrencia (acima) é a estrutural. Renomeado nesta revisão (3) de tipo_ocorrencia_cnab — o domínio já existia desde a revisão 20 do Fase 0, renomeado agora para nome canal-neutro, coerente com o resto desta revisão; ver Notas (seção 12). |
| **Motivo_Rejeicao** | *texto, opcional* | Preenchido quando Tipo_Ocorrencia=rejeitado: a descrição literal do motivo que o banco informou (fidelidade ao valor real, texto livre do banco), para apoiar a decisão de reenvio. |
| **Data_Ocorrencia** | *data* | A data em que o banco registra o evento (ex.: data do pagamento pelo sacado), distinta de Mov_Retorno_Bancario.Data_Recebimento (quando o retorno chegou à Mlegate). |
| **Valor_Total_Ocorrencia** | *número* | Renomeado nesta revisão (3) de Valor_Ocorrencia — o valor total informado pelo banco para esta ocorrência; pode diferir de Mov_Remessa_Bancaria_Item.Valor_Principal_Remessa (ex.: pagamento com desconto ou com juros/multa de atraso). Revisão 25 (D-N371, documento 124, Q107-2): quando o item tem ordem ao exterior, o valor fica **na moeda da ordem**; a moeda vem da ordem, porque o item de retorno não tem campo de moeda. |
| **Valor_Principal_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3), a pedido de Alberto — mesmo detalhamento já usado na remessa (seção 5), agora também no retorno: o componente principal do valor efetivamente liquidado, quando o banco discrimina. |
| **Valor_Desconto_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3) — o desconto efetivamente aplicado, quando informado pelo banco. |
| **Valor_Abatimento_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3) — o abatimento efetivamente aplicado, quando informado. |
| **Valor_Multa_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3) — a multa efetivamente cobrada, quando informada. |
| **Valor_Juros_Mora_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3) — os juros de mora efetivamente cobrados, quando informados. |
| **Valor_IOF_Ocorrencia** | *número, opcional* | Adicionado nesta revisão (3) — o IOF efetivamente cobrado, quando informado. |
| **Numero_Contrato_Cambio** | *código (40), opcional* | Revisão 25 (D-N371, documento 124, Q107-2, respondida por Alberto em 27/10/2026): só quando o retorno é de uma ordem ao exterior: o contrato de câmbio que o banco informa. Vai para Referencia_Operacao da classificação do Y520 (Q101-8a). |
| **Taxa_Cambio_Ocorrencia** | *número, opcional (8 casas)* | Revisão 25 (D-N371, documento 124, Q107-2): a taxa efetivamente cobrada, a **do contrato**. A baixa automática a copia para Mov_Titulo_Baixa.Taxa_Cambio; o operador pode corrigi-la, com motivo. Sem a taxa (o banco não devolve), vale a Taxa_Cambio_Contrato_Previo da ordem, se houver; senão o item fica pendente na área de inconsistências até o operador digitar. |
| **Valor_Reais_Ocorrencia** | *número, opcional* | Revisão 25 (D-N371, documento 124, Q107-2, Q107-2a e Q107-2b): o valor **do câmbio** debitado em reais (moeda × taxa), **sem IOF e sem tarifas**. Só **confere** com o extrato: diferença de até R$ 0,04, para mais ou para menos, vai para Mov_Titulo_Baixa.Valor_Arredondamento_Com_Sinal; acima, a baixa não é confirmada. Não vira Valor_Pago_Reais, que é calculado. Se o banco devolver só o total debitado, o operador separa o câmbio na área de inconsistências. |
| **E2eid** | *texto, opcional* | Adicionado nesta revisão (3) — só quando Canal_Transmissao=api ou open_finance: o identificador técnico da transação no SPI (Sistema de Pagamentos Instantâneos), devolvido pela API quando a cobrança é paga. |
| **ID_Baixa_Gerada** | *referência (Mov_Titulo_Baixa, opcional)* | Preenchido quando Tipo_Ocorrencia=aceito e o código de ocorrência representa liquidação efetiva: o sistema gera automaticamente uma Mov_Titulo_Baixa (Contas a Pagar/Receber, seção 3) para o título casado, com Origem_Tipo=automatica_cnab (ver Contas a Pagar/Receber, seção 3, patch desta revisão). Vazio para rejeições e para ocorrências informativas que não liquidam nada. |
| **ID_Participante_Tratamento** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (3): preenchido quando um operador resolve manualmente, pela tela de consistência (abaixo), um item que não casou automaticamente. |
| **Data_Tratamento** | *data, opcional* | Adicionado nesta revisão (3) — junto de ID_Participante_Tratamento. |
| **Tipo_Tratamento** | *enumeração {baixa_manual, reclassificado, descartado}, opcional* | Adicionado nesta revisão (3): o que foi feito para tratar o item — baixa_manual quando o operador gerou uma Mov_Titulo_Baixa manual (Origem_Tipo=manual) para ele; reclassificado quando o valor era, na verdade, outra coisa (ex.: rendimento/tarifa, via Mov_Conta_Contabil_Evento); descartado quando o item não correspondia a nada e foi simplesmente arquivado. Estrutura fixa do próprio mecanismo, mesmo critério de Codigo_Multa/Tipo_Ocorrencia — não domínio aberto. |
| **Codigo_Bruto_Banco** | *código (até 30)* | Revisão 56 (documento 250; D-N639 a D-N658): O código como o banco mandou, antes de traduzir (texto até 30; o webhook do Itaú manda palavras como `BAIXA_OPERACIONAL`, de 17 posições) |
| **Id_Externo_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O identificador do título ou do pagamento no banco (API) |
| **Codigo_Canal_Pagamento** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Por onde o pagador pagou, como o banco manda (código de até 3 posições). No webhook do Bradesco são os valores de 1 a 9, entre eles 4 = Pix e 8 = DDA; os significados dos demais não constam nos arquivos e ficam no mapa de ocorrências (R10) |
| **Codigo_Banco_Recebedor** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O banco que recebeu o pagamento (código de 3 posições; no Bradesco, 237 também quando o pagamento foi por Pix) |
| **Hora_Ocorrencia** | *hora, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A hora da ocorrência, que o webhook traz (o Bradesco manda data e hora do pagamento; o Pix manda o horário). Serve para ordenar eventos do mesmo dia e conferir com o extrato |
| **Numero_Autenticacao_Bancaria** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O número que o banco dá ao pagamento efetivado (o Bradesco, no tributo e na conta de consumo: 9 posições, "usado nos comprovantes"); é o que prova o pagamento junto ao órgão e entra no comprovante |
| **Motivo_Baixa** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O motivo da baixa, **copiado do mapa** no momento do retorno (mesmo domínio de `Cad_Banco_Ocorrencia_Mapa`). Fica no item para que uma troca futura do mapa não reescreva o que o banco disse (R107) |
| **Codigo_Complementar_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): O código complementar como o banco mandou (Itaú: agência cobradora 7744, 7788, 7777 ou 9999, R109) |
| **Motivos_Bruto_Banco** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, cobrança 400: até **5 motivos** de 2 posições que acompanham a ocorrência, guardados como vieram. Na ocorrência 28 (débito de tarifas) o motivo diz **qual** tarifa (R104) |
| **Valor_Tarifa_Banco** | *número, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A tarifa cobrada na ocorrência. Na cobrança 400 do Bradesco o registro traz **só a primeira** tarifa; o total se confere com o extrato (R104) |
| **Credito_Disponivel** | *booleano, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, cobrança 400: {sim, nao}: se o crédito do pagamento já está **disponível** ou ainda **indisponível** para a empresa (motivos 00 e 15 do retorno). Alimenta o fluxo de caixa, junto com `Data_Credito` |
| **Codigo_Liquidacao_Pix** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): Bradesco, Pix recebimentos em CNAB 750: o código de liquidação do Pix (2 posições, de 01 a 05), como o banco manda; o mapa de ocorrências traduz (R102) |
| **Revisao_Cobranca_Pix** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): CNAB 750: a **revisão** da cobrança Pix (4 dígitos), que muda quando a cobrança é alterada e deve casar com a que o ERP enviou |
| **Codigo_Forma_Pagamento** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): BB: **como** o pagador pagou, separado do canal: 1 espécie, 2 débito em conta, 3 cartão de crédito e 4 cheque, como o banco manda (o webhook do BB traz `formaPagamento` e `canalLiquidacao`, e os dois juntos dizem como o boleto foi liquidado). Código bruto de até 3 posições; a tradução vai ao mapa (R10) |
| **Data_Credito** | *data, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): A data em que o banco **credita** o valor ao beneficiário (`dataCredito` no webhook do BB; no CNAB, a data de crédito do segmento U). É a data que o fluxo de caixa e a conciliação com o extrato usam, diferente de `Data_Ocorrencia` (quando o pagamento aconteceu) |
| **Documento_Portador** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): BB: o CPF ou CNPJ de **quem pagou** o boleto (`identidadePortador`), que pode não ser o cliente do título (um terceiro, a matriz); serve à conciliação e à auditoria |
| **Nome_Portador** | *texto, opcional* | Revisão 56 (documento 250; D-N639 a D-N658): BB: o nome de quem pagou (`nomePortador`) |

*Revisão 25 --- campos novos: Numero_Contrato_Cambio, Taxa_Cambio_Ocorrencia, Valor_Reais_Ocorrencia; campos alterados: Valor_Total_Ocorrencia.*

*Revisão 56 --- campos novos: Codigo_Bruto_Banco, Id_Externo_Banco, Codigo_Canal_Pagamento, Codigo_Banco_Recebedor, Hora_Ocorrencia, Numero_Autenticacao_Bancaria, Motivo_Baixa, Codigo_Complementar_Banco, Motivos_Bruto_Banco, Valor_Tarifa_Banco, Credito_Disponivel, Codigo_Liquidacao_Pix, Revisao_Cobranca_Pix, Codigo_Forma_Pagamento, Data_Credito, Documento_Portador, Nome_Portador.*

*Tela de consistência, a pedido de Alberto: todo item de retorno que não tem referência em Contas a Pagar/Receber deve cair numa tela para tratamento manual do operador. Mesmo padrão "nenhuma entidade nova para a tela em si" já usado no painel de gestão e no aging (seção 7): a tela é uma CONSULTA sobre Mov_Retorno_Bancario_Item filtrando ID_Item_Remessa nulo e/ou ID_Baixa_Gerada nulo. Um item está pendente na tela enquanto Data_Tratamento for nula — mesma filosofia "status nunca armazenado, sempre derivado" do resto do dicionário —, e o que foi decidido fica registrado em Tipo_Tratamento, para que casos parecidos no futuro já possam ser tratados de forma consistente. Reaproveitar o Motor de Regras para sugerir automaticamente o tratamento (por analogia ao critério já definido para o extrato, seção 3 — banco e o código de ocorrência que o banco informou) é um caminho natural, mas não foi confirmado por Alberto nestes termos; fica como observação técnica, não como estrutura decidida.*

*Reenvio: um item rejeitado não gera nenhum vínculo estrutural novo — o reenvio é só um NOVO Mov_Remessa_Bancaria_Item (numa remessa posterior, inclusive por outra Cad_Conta_Bancaria/banco) para o mesmo Mov_Titulo; o histórico de tentativas já fica rastreável naturalmente por múltiplas linhas de remessa ao longo do tempo para o mesmo título, sem precisar amarrar explicitamente a nova tentativa à rejeitada. Histórico de transmissões multi-banco, a pedido de Alberto (ex.: enviado ao Itaú, rejeitado, reenviado ao Bradesco, processado, baixado): já 100% suportado sem entidade nova, porque tanto Mov_Remessa_Bancaria quanto Mov_Retorno_Bancario carregam seu próprio ID_Conta_Bancaria — o banco de cada tentativa de envio e o banco de cada retorno são sempre conhecidos independentemente. O histórico completo é uma consulta: todas as linhas de Mov_Remessa_Bancaria_Item e Mov_Retorno_Bancario_Item associadas ao mesmo Mov_Titulo, ordenadas por data, cada uma com seu próprio banco/canal — sem precisar de uma tabela de histórico dedicada.*

*A baixa automática nasce como qualquer outra Mov_Titulo_Baixa — mesma tabela, mesmas regras (Contas a Pagar/Receber, seção 3) —, com ID_Conta_Contabil apontando para a conta bancária da remessa/retorno e Valor_Baixado igual a Valor_Total_Ocorrencia. Contas a Pagar/Receber recebe, junto com esta revisão, o patch pendente desde a Revisão 2: Mov_Titulo_Baixa ganha Origem_Tipo {automatica_cnab, manual} e passa a registrar, quando automática, a data de recebimento do retorno separada da data de fato da baixa (que podem divergir), e, quando manual, o usuário responsável — ver Contas a Pagar/Receber, seção 3.*

*Comportamento de aplicação (não é um campo novo de dados), adicionado nesta revisão (6): antes de gerar a Mov_Titulo_Baixa automática a partir de um Mov_Retorno_Bancario_Item aceito (acima), e antes de efetivar qualquer baixa manual (Origem_Tipo=manual) disparada a partir desta Tesouraria, o sistema consulta Cad_Periodo_Fechamento_Filial (mecanismo transversal da Fase 0, seção 10, revisão 37) pela combinação Bloco="tesouraria" + Filial do título associado + competência derivada da data da baixa — regime fail-closed, mesmo critério de Compras e dos demais blocos deste dicionário: nenhuma combinação é tratada como aberta por omissão. É a MESMA trava usada pelo nascimento/alteração de Mov_Titulo e pela própria Mov_Titulo_Baixa no documento Fase 2 Contas a Pagar/Receber (seções 2 e 3 daquele documento, revisão 9) — um único bloco "tesouraria", não dois blocos coordenados, ainda que as duas entidades estejam fisicamente cadastradas naquele documento e a execução do pagamento aconteça fisicamente aqui. Sem checagem de pendência no fechamento (exclusiva do bloco "compras") — um título em aberto aguardando pagamento é o estado normal, não impede fechar a competência de entrada daquele mesmo bloco.*

7\. Painel de Gestão — Fluxo de Caixa, Aging e Empenhos/Orçado

O Documento Analítico é explícito: Tesouraria "funciona como painel de gestão, não como tela puramente operacional" — visão prospectiva (o que vence nos próximos dias) e retrospectiva (o que ficou pendente de dias anteriores), nunca apenas o dia corrente. Esta seção não define tabela nova nenhuma para o fluxo de caixa em si: é inteiramente uma CONSULTA sobre dados que já existem em outros módulos já especificados — Mov_Titulo (Contas a Pagar/Receber), Mov_Compromisso_Orcamentario e Cad_Orcamento_Item_Desembolso (Planejamento & Orçamento), e o saldo corrente de cada Cad_Conta_Contabil do tipo Banco/Caixa/Aplicação (soma de Mov_Lancamento, Fase 0), complementado pelo saldo já conciliado do extrato (seções 3 e 4). A identidade de cada saldo mostrado é sempre resolvida através do vínculo de Cad_Conta_Bancaria com Cad_Conta_Contabil (seção 2), nunca por um cálculo paralelo.

- Grupo A — Efetivo: todo Mov_Titulo (Tipo=receber ou pagar) com saldo em aberto positivo (Contas a Pagar/Receber, seção 2) — já nasceu de nota fiscal ou evento equivalente, com Data_Vencimento exata.

- Grupo B — Empenhado: todo Mov_Compromisso_Orcamentario (Planejamento & Orçamento, seção 4) com Status=aberto — um pedido de compra aprovado consome orçamento e existe aqui ANTES de virar título (Status só muda para baixado quando a nota fiscal chega). A data é aproximada, pelo ID_Periodo_Referencia do compromisso ou, quando disponível via Origem_Tipo/ID_Origem, pela Data_Entrega_Prevista do item de pedido de origem (Compras).

- Grupo C — Orçado: todo Cad_Orcamento_Item_Desembolso (Planejamento & Orçamento, seção 3) dentro da janela de datas consultada — o cronograma de desembolso projetado já descrito desde a especificação original daquele módulo. Cobre qualquer conta orçada, não só compras — inclusive contas de folha de pagamento (ex.: um item orçado de 13º salário com seu próprio cronograma), mesmo antes de Folha & RH (Fase 5) ser especificado.

Nenhum dos três grupos introduz uma entidade nova — Grupo B e C só passam a ser EXIBIDOS no painel de Tesouraria, reaproveitando 100% o que Planejamento & Orçamento já tinha desde a especificação original.

Visão prospectiva (Grupo A): todo título com Data_Vencimento igual ou posterior à data de referência, agrupado por dia/semana à frente — o mesmo agrupamento vale para os Grupos B e C, cada um na sua própria faixa do painel. Visão retrospectiva: o mesmo filtro do Grupo A, mas com Data_Vencimento anterior à data de referência e saldo em aberto ainda positivo — exatamente a definição de "vencido" já formalizada em Contas a Pagar/Receber (seção 2); Grupos B e C, por natureza, não têm visão retrospectiva.

Aging de Contas a Pagar e Receber: o painel agrupa o saldo em aberto do Grupo A (a pagar e a receber) por faixa de dias de atraso, não só por vencido/a vencer — mesmo cálculo de "vencido" já formalizado, só agrupado em faixas em vez de um único bloco. Comentário de Alberto sobre a Revisão 2: as bandas não deveriam ser fixas — variam por empresa que está usando o sistema, e um usuário pode querer personalizar as suas próprias.

Cad_Banda_Aging

Um degrau de faixa de dias de atraso/antecedência em relação a Data_Vencimento — configurável por empresa, com personalização individual opcional por usuário.

*Vigência: sim — mudanças na configuração de bandas ao longo do tempo seguem o mesmo padrão de vigência já usado no resto do dicionário.*

|                             |                                      |                                                                                                                                                                                                                                                                  |
|-----------------------------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo**                   | **Tipo lógico**                      | **Descrição / regra**                                                                                                                                                                                                                                            |
| **ID_Banda**                | *identificador*                      | —                                                                                                                                                                                                                                                                |
| **ID_Empresa**              | *referência (Cad_Empresa)*           | As bandas padrão são configuradas por empresa, não fixas no sistema — cada empresa que usa o sistema define as suas.                                                                                                                                             |
| **ID_Usuario**              | *referência (Cad_Usuario, opcional)* | Vazio: esta é uma banda padrão da empresa, usada por todo mundo. Preenchido: esta é uma personalização daquele usuário específico — quando um usuário tem qualquer banda própria cadastrada, sua visão do aging usa o conjunto dele em vez do padrão da empresa. |
| **Nome**                    | *texto*                              | Rótulo da faixa (ex.: "a vencer", "1-30 dias", "acima de 90").                                                                                                                                                                                                   |
| **Dias_Inicio**             | *número*                             | —                                                                                                                                                                                                                                                                |
| **Dias_Fim**                | *número, opcional*                   | Vazio na última banda de cada conjunto, representando "sem limite superior" (ex.: acima de 90 dias).                                                                                                                                                             |
| **Ordem**                   | *número*                             | A ordem de exibição das bandas no painel, da mais recente/a vencer para a mais atrasada.                                                                                                                                                                         |
| **Sugere_Devedor_Duvidoso** | *booleano, opcional*                 | Adicionado nesta revisão (3), a pedido de Alberto — ver seção 8: marca a(s) banda(s) que disparam uma sugestão (não uma efetivação automática) de classificar o título como devedor duvidoso.                                                                    |
| **Vigencia_Inicio**         | *data*                               | Primeiro dia em que esta versão vale.                                                                                                                                                                                                                            |
| **Vigencia_Fim**            | *data*                               | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2.                                                                                                         |
| **Motivo_Vigencia**         | *texto, opcional*                    | Por que esta versão foi criada.                                                                                                                                                                                                                                  |

*Sugestão de aplicação financeira: o Documento Analítico é igualmente explícito em NÃO impor um parâmetro fixo de caixa mínimo — a sugestão ("há R\$X de sobra projetada para os próximos N dias, considerando o que já está previsto para vencer") é uma comparação entre o saldo consolidado das contas Banco/Caixa e o fluxo prospectivo do Grupo A, apresentada em tela para o gestor decidir; a decisão em si — quanto aplicar, em qual conta de Aplicação (Cad_Conta_Contabil, ID_Tipo_Conta=Aplicação, e agora também referenciável por Cad_Conta_Bancaria.ID_Conta_Contabil_Aplicacao quando for a mesma agência/conta) — continua manual, registrada como uma baixa comum contra a conta de origem e, quando aplicável, um novo saldo na conta de aplicação. Nenhuma estrutura de dados nova para a sugestão em si: é cálculo de apresentação, não persistência.*

8\. Devedores Duvidosos

Um local onde o gestor da Tesouraria possa classificar o que está na carteira a receber como devedor duvidoso.

Mov_Titulo_Classificacao_Duvidoso

O evento de marcar (ou reverter a marcação de) um título a receber como devedor duvidoso — critério e responsabilidade do gestor da Tesouraria, registrado como evento imutável, nunca como edição do título original.

*Vigência: não — é o registro de um evento; o estado atual é sempre derivado, nunca armazenado.*

|                                 |                                            |                                                                                                                                                                                                          |
|---------------------------------|--------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo**                       | **Tipo lógico**                            | **Descrição / regra**                                                                                                                                                                                    |
| **ID_Classificacao**            | *identificador*                            | —                                                                                                                                                                                                        |
| **ID_Titulo**                   | *referência (Mov_Titulo, Tipo=receber)*    | —                                                                                                                                                                                                        |
| **Data_Classificacao**          | *data*                                     | —                                                                                                                                                                                                        |
| **Tipo_Classificacao**          | *enumeração {marcado_duvidoso, revertido}* | Uma reversão é um NOVO registro, nunca uma edição do registro que marcou — mesmo padrão de evento imutável já usado em todo o dicionário (ex.: estorno de baixa).                                        |
| **Motivo**                      | *texto, opcional*                          | —                                                                                                                                                                                                        |
| **ID_Participante_Responsavel** | *referência (Cad_Participante)*            | O gestor da Tesouraria que fez a classificação — inclusive quando a classificação nasceu do aceite de uma sugestão automática (abaixo), o responsável pela decisão final continua sendo registrado aqui. |

Se um título está duvidoso HOJE — fórmula, sem campo próprio: olha o evento mais recente (por Data_Classificacao) para aquele título; se for marcado_duvidoso, está duvidoso; se for revertido, não está. Distinção importante: classificar como duvidoso é diferente da régua de cobrança (seções 9 e 10) — uma é rótulo de risco de crédito/contábil (a base para uma futura provisão para créditos de liquidação duvidosa, PECLD/PDD), a outra é escalada comercial de cobrança; os dois mecanismos podem coexistir sem depender um do outro.

*Sugestão automática, a pedido de Alberto: pode haver sugestão automática de classificar um título como duvidoso a partir do aging, mas nunca efetivação automática — sempre com aceite explícito do usuário que está operando. Mecanismo: quando um título entra numa banda de Cad_Banda_Aging (seção 7) com Sugere_Devedor_Duvidoso=verdadeiro, a tela apresenta um alerta de sugestão — cálculo em tela, não persistido, mesma filosofia de "status nunca armazenado" já usada em todo o dicionário. A classificação em si continua sendo sempre o registro manual de Mov_Titulo_Classificacao_Duvidoso acima, só que agora pode nascer do aceite dessa sugestão em vez de ser iniciada do zero pelo gestor — nenhuma estrutura nova para a classificação em si.*

*O lançamento contábil da provisão para devedores duvidosos em si (PECLD/PDD) fica, como outros pontos fiscais/contábeis deste dicionário, como gancho explícito para a futura Contabilidade & Fiscal — este módulo só registra o evento de classificação (quem, quando, por quê), pronto para aquele módulo futuro consumir e gerar o lançamento correspondente.*

9\. Régua de Cobrança

A escalada descrita no Documento Analítico — "do gentil ao definitivo: um aviso discreto próximo do vencimento, uma notificação de pendência pouco depois do atraso, e só além de um número configurável de dias o bloqueio de novas vendas e a zeragem do limite de crédito" — é, deliberadamente, uma estrutura DIFERENTE de Cad_Regua_Aprovacao/Cad_Regua_Faixa (Fase 0): aquela régua classifica por FAIXA DE VALOR e precisa de um aprovador humano decidir sim/não; esta régua classifica por FAIXA DE TEMPO (dias antes/depois do vencimento) e dispara ações automáticas, sem aprovação humana nenhuma — mais próxima de uma régua de comunicação/escalonamento do que de uma régua de aprovação. Por isso ganha cadastro próprio, em vez de reaproveitar aquele já existente.

Cad_Regua_Cobranca

O cabeçalho da régua de cobrança — na prática, como Cad_Regua_Aprovacao (Fase 0), o sistema opera com uma única régua ativa por empresa, reaproveitada para todo cliente, mas a estrutura permite mais de uma se essa decisão de configuração mudar.

*Vigência: sim — mudanças na régua ao longo do tempo (ex.: prazo mais rígido a partir de certa data) seguem o mesmo padrão de vigência já usado em Cad_Regua_Aprovacao.*

|                              |                            |                                                                                                                                                                                                                 |
|------------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo**                    | **Tipo lógico**            | **Descrição / regra**                                                                                                                                                                                           |
| **ID_Regua_Cobranca**        | *identificador*            | —                                                                                                                                                                                                               |
| **ID_Regua_Cobranca_Versao** | *identificador da versão*  | Chave primária da versão (tabela física Cad_Regua_Cobranca_Versao). ID_Regua_Cobranca é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Empresa**               | *referência (Cad_Empresa)* | —                                                                                                                                                                                                               |
| **Nome**                     | *texto*                    | —                                                                                                                                                                                                               |
| **Vigencia_Inicio**          | *data*                     | Primeiro dia em que esta versão vale.                                                                                                                                                                           |
| **Vigencia_Fim**             | *data*                     | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2.                                                        |
| **Motivo_Vigencia**          | *texto, opcional*          | Por que esta versão foi criada.                                                                                                                                                                                 |

Cad_Regua_Cobranca_Faixa

Um degrau da escalada — o número de dias em relação ao vencimento e a ação disparada quando um título cruza esse degrau.

*Vigência: sim — mesmo padrão de Cad_Regua_Faixa (Fase 0).*

|                            |                                                                          |                                                                                                                                                                                                                                                                                         |
|----------------------------|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Campo**                  | **Tipo lógico**                                                          | **Descrição / regra**                                                                                                                                                                                                                                                                   |
| **ID_Faixa**               | *identificador*                                                          | —                                                                                                                                                                                                                                                                                       |
| **ID_Faixa_Versao**        | *identificador da versão*                                                | Chave primária da versão (tabela física Cad_Regua_Cobranca_Faixa_Versao). ID_Faixa é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2.                                                                            |
| **ID_Regua_Cobranca**      | *referência (Cad_Regua_Cobranca)*                                        | —                                                                                                                                                                                                                                                                                       |
| **Dias_Referencia**        | *número*                                                                 | Negativo = dias ANTES do vencimento (o aviso discreto); positivo = dias DEPOIS do vencimento (notificação de pendência; bloqueio, no degrau configurado por Alberto como "o número configurável de dias" citado no Documento Analítico).                                                |
| **Acao**                   | *enumeração {aviso_vencimento, notificacao_pendencia, bloqueio_zeragem}* | As três ações descritas no Documento Analítico, na ordem em que escalam — estrutural e fechada: são sempre estas três, o que muda é o Dias_Referencia de cada uma.                                                                                                                      |
| **Notifica_Vendas**        | *booleano*                                                               | —                                                                                                                                                                                                                                                                                       |
| **Notifica_Gestor_Vendas** | *booleano*                                                               | —                                                                                                                                                                                                                                                                                       |
| **Notifica_Financeiro**    | *booleano*                                                               | O Documento Analítico é explícito: "cobrança nunca é assunto isolado da Tesouraria" — por isso os três alertas são independentes entre si e tipicamente todos ligados, mas a estrutura permite desligar um deles por degrau, se a Mlegate preferir menos ruído nos avisos mais brandos. |
| **Vigencia_Inicio**        | *data*                                                                   | Primeiro dia em que esta versão vale.                                                                                                                                                                                                                                                   |
| **Vigencia_Fim**           | *data*                                                                   | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2.                                                                                                                                |
| **Motivo_Vigencia**        | *texto, opcional*                                                        | Por que esta versão foi criada.                                                                                                                                                                                                                                                         |

*Canal de notificação, precisado por Alberto nesta revisão: cada alerta acionado (Notifica_Vendas/Notifica_Gestor_Vendas/Notifica_Financeiro) dispara dois canais simultâneos — um indicador visível no CRM & Vendas, no cadastro/tela do cliente, para quem já trabalha dentro do CRM, e o envio de um e-mail, que cobre também o Financeiro, que não necessariamente vive no CRM. O destinatário de cada e-mail é resolvido pelo novo cadastro de e-mails do participante (Cad_Participante_Email/Cad_Participante_Email_Tipo_Notificacao, Fase 0): todo Cad_Participante_Email vinculado ao vendedor/gestor/financeiro do cliente e tagueado com o tipo de notificação correspondente (domínio tipo_notificacao_sistema) recebe o e-mail; um e-mail sem nenhuma tag recebe todas as notificações por padrão. Vendas e Gestor de Vendas resolvem pela cadeia já existente (vendedor principal do cliente e seu superior via Cad_Participante_Historico_Hierarquia_Comercial, CRM & Vendas); Financeiro resolve por um conjunto de e-mails internos da Mlegate tagueados com notificacao_regua_financeiro, sem precisar de um vínculo cliente→participante financeiro específico.*

10\. Execução da Régua de Cobrança e Bloqueio

Mov_Regua_Cobranca_Execucao

O registro de que um título cruzou um degrau da régua e a ação correspondente foi disparada — garante que cada degrau dispara no máximo uma vez por título (idempotência), mesmo que a rotina que verifica a régua rode mais de uma vez ao dia.

*Vigência: não — é o registro de um evento.*

|                   |                                         |                                                                                                                     |
|-------------------|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| **Campo**         | **Tipo lógico**                         | **Descrição / regra**                                                                                               |
| **ID_Execucao**   | *identificador*                         | —                                                                                                                   |
| **ID_Titulo**     | *referência (Mov_Titulo, Tipo=receber)* | A régua de cobrança, pela própria natureza (cobrança de cliente), só se aplica a títulos a receber — nunca a pagar. |
| **ID_Faixa**      | *referência (Cad_Regua_Cobranca_Faixa)* | Qual degrau disparou.                                                                                               |
| **Data_Execucao** | *data*                                  | —                                                                                                                   |

A verificação de qual título cruzou qual degrau é sempre feita comparando Data_Vencimento (mais Dias_Referencia) contra a data corrente e o saldo em aberto do título (Contas a Pagar/Receber, seção 2) — nunca armazenada como um novo Status em Mov_Titulo, mesma filosofia do dicionário inteiro. Um título que é liquidado (baixa, crédito ou encontro de contas) para de escalar naturalmente, porque seu saldo em aberto chega a zero — a régua não precisa de um mecanismo próprio de "parar".

O degrau final (bloqueio_zeragem) e sua relação com o Limite de Crédito já especificado (Contas a Pagar/Receber, seção 6): este documento mantém que a régua de cobrança NÃO sobrescreve o valor configurado de Cad_Participante.Limite_Credito nem de Cad_Grupo_Economico.Limite_Credito — fazer isso destruiria um valor de configuração real e exigiria restaurar manualmente o limite depois que a pendência fosse resolvida. Em vez disso, a régua de cobrança é um SEGUNDO gatilho de bloqueio, independente da fórmula de Exposição_Total × Teto já definida: quando qualquer título a receber de um participante atinge o degrau bloqueio_zeragem, dispara Mov_Aprovacao_Instancia (Fase 0) com Origem_Tipo=bloqueio_regua_cobranca — novo valor deste domínio, adicionado nesta revisão, ao lado de desvio_credito já existente, mesmo motor de régua de aprovação (Cad_Regua_Aprovacao/Mov_Aprovacao_Instancia) usado no resto do dicionário.

*Integração de fato dentro de Mov_Cotacao_Venda (CRM & Vendas), a pedido de Alberto — resolvida nesta revisão, com patch no documento de CRM & Vendas: o bloqueio (por desvio_credito ou por bloqueio_regua_cobranca) é sempre avaliado e aplicado no nível de grupo econômico, não cascateando para CNPJ Raiz/individual como a configuração de limite em si permite. O tratamento em tela depende do canal de origem da cotação (Mov_Cotacao_Venda.Canal_Origem, já existente desde a revisão 4 daquele documento): quando atendimento_vendedor, a pendência é mostrada ao vendedor que está atendendo, para ele decidir; quando autoatendimento, a cotação entra em análise (Status=em_aprovacao) sem atendimento automático — nem aprovação nem recusa sozinha —, cai na fila de cotações sem vendedor atribuído já existente naquele módulo, e um vendedor/gestor assume e decide depois, sem que o motivo do bloqueio seja exposto ao próprio cliente. Ver CRM & Vendas, seção 4, para o detalhe da mudança.*

11\. Conexões com a Fase 0 e Outros Módulos

|                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                        |                                                                                                   |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| **Entidade referenciada**                                                                                                                                                                                       | **Como este módulo usa**                                                                                                                                                                                                                                                                                                                                               | **Observação**                                                                                    |
| **Cad_Conta_Contabil (ID_Tipo_Conta = Banco/Aplicação)**                                                                                                                                                        | Cad_Conta_Bancaria (seção 2) estende cada conta bancária física com até três contas do plano de contas — corrente, poupança e aplicação, cada uma opcional, mesma agência/conta.                                                                                                                                                                                       | *Fase 0, sem mudança estrutural*                                                                  |
| **Cad_Classe_Sistema (domínios tipo_ocorrencia_retorno_bancario, tipo_classificacao_extrato, tipo_documento_cobranca, tipo_finalidade_pagamento, tipo_notificacao_sistema, tipo_provedor_integracao_bancaria)** | Classifica código de ocorrência de retorno (seção 6), categoria de linha de extrato (seção 3), espécie do título e finalidade de pagamento (seção 5), tipo de notificação (seção 9) e provedor técnico de integração (seções 5 e 6).                                                                                                                                   | *Fase 0, revisão 22 (proposta) — três domínios renomeados de forma canal-neutra, dois novos*      |
| **Mov_Titulo / Mov_Titulo_Baixa / Mov_Titulo_Encontro_Contas (Contas a Pagar/Receber)**                                                                                                                         | O painel de gestão e o aging (seção 7) consultam Mov_Titulo; a conciliação (seção 4) referencia baixa e encontro de contas; o retorno bancário (seção 6) gera Mov_Titulo_Baixa, agora com Origem_Tipo automatica_cnab/manual.                                                                                                                                          | *Contas a Pagar/Receber, seções 2, 3 e 5 — patch nesta revisão*                                   |
| **Mov_Compromisso_Orcamentario / Cad_Orcamento_Item_Desembolso (Planejamento & Orçamento)**                                                                                                                     | O painel de gestão (seção 7, Grupos B e C) passa a exibir o empenho de pedido de compra e o desembolso orçado, reaproveitando as duas entidades tal como já existiam.                                                                                                                                                                                                  | *Planejamento & Orçamento, seções 3 e 4*                                                          |
| **Limite de Crédito (Cad_Participante/Cad_Grupo_Economico/CNPJ Raiz) + Mov_Cotacao_Venda (CRM & Vendas)**                                                                                                       | A régua de cobrança (seções 9 e 10) soma-se como segundo gatilho de bloqueio (Origem_Tipo=bloqueio_regua_cobranca), sempre no nível de grupo econômico, integrado dentro do ciclo de aprovação da cotação de venda.                                                                                                                                                    | *Contas a Pagar/Receber, seção 6; CRM & Vendas, seção 4 — patch nesta revisão*                    |
| **Cad_Participante_Email / Cad_Participante_Email_Tipo_Notificacao / Cad_Participante_Dados_Bancarios**                                                                                                         | Resolve o destinatário de cada notificação da régua (seção 9) e pré-preenche os dados do favorecido numa remessa de pagamento (seção 5).                                                                                                                                                                                                                               | *Fase 0, revisão 22 (proposta) — entidades novas*                                                 |
| **Cad_Empresa / Cad_Usuario**                                                                                                                                                                                   | As bandas de aging (seção 7) são configuráveis por empresa, com personalização individual por usuário.                                                                                                                                                                                                                                                                 | *Fase 0, sem mudança estrutural*                                                                  |
| **Mov_Conta_Contabil_Evento (rendimento, perda, tarifa)**                                                                                                                                                       | Alvo possível de conciliação bancária (seção 4) quando a linha de extrato é um rendimento/tarifa, não uma baixa de título; também alvo de reclassificação na tela de consistência (seção 6).                                                                                                                                                                           | *Contas a Pagar/Receber, seção 9*                                                                 |
| **Mov_Lancamento / Mov_Lote_Lancamento**                                                                                                                                                                        | Saldo corrente de conta (seção 7) e conciliação de lançamento manual sem evento estruturado (seção 4).                                                                                                                                                                                                                                                                 | *Fase 0*                                                                                          |
| **Mov_Titulo (Origem_Tipo=folha_pagamento, Natureza_Titulo_Folha) (Contas a Pagar/Receber)**                                                                                                                    | Adicionado nesta revisão (5): a remessa de pagamento (seção 5) passa a cobrir também a baixa de título gerado pela folha — líquido do colaborador, INSS, FGTS, IRRF retido, entre outros —, cada natureza podendo exigir um tipo de serviço de lote (ID_Tipo_Servico_Lote, seção 5) e uma forma de lançamento (cartao_salario, codigo_barras) diferentes.              | *Contas a Pagar/Receber, revisão 8 — construído nesta consolidação*                               |
| **Cad_Participante_Dados_Bancarios.Tipo_Conta (conta_salario) / Cad_Vinculo_Emprego / Cad_Rh_Motivo_Desligamento (Fase 0 / Fase 5 — Folha & RH)**                                                               | Tipo_Conta_Favorecido (seção 5) diferencia conta-salário de conta corrente/poupança no item de remessa; em rescisão por óbito, o favorecido do item de pagamento é resolvido a partir de Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito, não do colaborador falecido.                                                                                          | *Fase 0, revisão 30; Fase 5, revisão 5 — construídos nesta consolidação*                          |
| **Cad_Bloco_Fechamento / Cad_Periodo_Fechamento / Cad_Periodo_Fechamento_Filial (Bloco="tesouraria")**                                                                                                          | Adicionado nesta revisão (6): trava a baixa automática (retorno bancário, seção 6) e a baixa manual disparada a partir desta Tesouraria por Filial+competência — o mesmo bloco que trava Mov_Titulo/Mov_Titulo_Baixa em Contas a Pagar/Receber (revisão 9 daquele documento, mesma consolidação), um único bloco de fechamento estendendo-se sobre os dois documentos. | *Fase 0, seção 10, revisão 37; Contas a Pagar/Receber, revisão 9 — construído nesta consolidação* |

12\. Notas e Observações Técnicas

- Este documento se apoia em seis domínios de Cad_Classe_Sistema (Fase 0): tipo_ocorrencia_retorno_bancario, tipo_classificacao_extrato, tipo_documento_cobranca e tipo_finalidade_pagamento (já existentes, renomeados nesta revisão de nomes com "cnab" para nomes canal-neutros — tipo_ocorrencia_retorno_bancario, especificamente, foi criado na revisão 20 do Fase 0 e é o único caso deste dicionário em que um nome de domínio já publicado foi alterado, não só estendido; Alberto confirmou explicitamente que está tudo bem alterar nome já publicado nesta fase de especificação), e dois domínios novos — tipo_notificacao_sistema (seção 9) e tipo_provedor_integracao_bancaria (seções 5 e 6). Todos cadastros abertos, um novo valor nunca exige mudança de estrutura.

- Layout_Cnab {240, 400} (seção 2) e Codigo_Multa {nao_registra, valor_fixo, percentual} (seção 5) ficaram como enumerações fechadas, dentro da própria entidade, em vez de um domínio Cad_Classe_Sistema — mesmo critério já usado em Periodicidade_Taxa (Mov_Emprestimo, Contas a Pagar/Receber): conjuntos pequenos e estáveis, que não crescem com o tempo como os domínios abertos acima. Tipo_Conta_Bancaria {corrente, poupanca}, que seguia o mesmo critério na Revisão 2, foi removido nesta revisão: ficou redundante quando Cad_Conta_Bancaria passou a suportar três vínculos contábeis simultâneos (seção 2) — o tipo de cada ponta passa a ser inferido por qual vínculo está preenchido, não mais um campo próprio.

- Acao {aviso_vencimento, notificacao_pendencia, bloqueio_zeragem} (Cad_Regua_Cobranca_Faixa, seção 9), Tipo_Ocorrencia {aceito, rejeitado, informativo} e Tipo_Tratamento {baixa_manual, reclassificado, descartado} (Mov_Retorno_Bancario_Item, seção 6) também ficaram como enumerações fechadas, e não domínio aberto: são estruturas fixas do próprio mecanismo — diferente de tipo_evento_conta_financeira ou tipo_credito_adiantamento, que são listas de classificação abertas por natureza.

- Origem_Importacao (Mov_Extrato_Bancario, seção 3) ganhou o valor api_open_finance nesta revisão, em vez de um campo novo dedicado a essa origem — revisão do desenho original mostrou que o campo já existente (que decide como uma linha de extrato chegou ao sistema) já cobria exatamente essa pergunta, só faltava o valor específico para a API de Dados Cadastrais e Transacionais do Open Finance.

- Mov_Remessa_Bancaria_Item.Valor_Principal_Remessa (seção 5) é copiado do saldo em aberto no momento da geração — se o título mudar de saldo depois disso, este documento assume que cabe à camada de aplicação decidir se cancela/reemite a remessa; a estrutura de dados não impede um Mov_Retorno_Bancario_Item chegando com Valor_Total_Ocorrencia diferente do Valor_Principal_Remessa original — a baixa gerada (ID_Baixa_Gerada) sempre usa o valor real do retorno, fidelidade ao valor real, nunca o da remessa.

- Mov_Conciliacao_Bancaria (seção 4) não valida estruturalmente que a soma de Valor_Conciliado por linha de extrato não ultrapasse Mov_Extrato_Bancario.Valor, nem que a soma por evento interno não ultrapasse o valor daquele evento — mesma filosofia de todo o dicionário: a estrutura registra o evento, a camada de aplicação garante a consistência.

- O critério de sugestão automática da tela de consistência (seção 6) — banco e código de ocorrência, por analogia ao critério confirmado para o extrato (seção 3) — é uma extensão minha, não uma confirmação literal de Alberto sobre esse ponto específico; fica sinalizado como observação técnica, não como estrutura decidida com a mesma certeza do resto.

- ID_Autorizacao_Api/Status_Autorizacao_Api (Mov_Remessa_Bancaria_Item, seção 5) aplicam-se sempre que Canal_Transmissao=open_finance, em qualquer Tipo — não há um campo separado para indicar se a autorização é de um fluxo de pagamento ou de recebimento porque o próprio campo Tipo (cobranca/pagamento) do cabeçalho já dá essa indicação.

- Nesta revisão (4), Alberto confirmou, na rodada de checagem de pendências do ciclo "consolidar", que o nome ID_Autorizacao_Api/Status_Autorizacao_Api (seção 5) é suficientemente genérico para cobrir também o fluxo de recebimento via Pay by Bank (o cliente autoriza, no banco dele, um pagamento direto à Mlegate) — deixa de ser suposição (ver Revisão 3, seção 13) e passa a ser estrutura confirmada; nenhuma mudança de campo ou de nome foi necessária.

- Revisão 5 — ID_Tipo_Servico_Lote (Mov_Remessa_Bancaria, seção 5) assume que a folha entrega, no nível de aplicação, os títulos já separados por natureza de forma que cada lote de remessa contenha só um tipo de serviço (ex.: um lote código 30 só com líquido de colaboradores, um lote código 22 só com tributos por código de barras) — a estrutura não impede misturar naturezas num mesmo Mov_Remessa_Bancaria, mas o CNAB 240 exige homogeneidade de tipo de serviço por lote; fica como responsabilidade de quem monta a remessa, não como restrição garantida por esta modelagem.

- Revisão 5 — Codigo_Barras (Mov_Remessa_Bancaria_Item, seção 5) ficou como texto livre, sem decompor os campos da linha digitável (banco, moeda, dígito verificador, valor, fator de vencimento) — mesmo critério de fidelidade ao valor real já usado em outros campos deste documento; se a Mlegate precisar validar/decompor a linha digitável antes do envio, é responsabilidade da camada de aplicação.

- Revisão 5 — Tipo_Conta_Favorecido (Mov_Remessa_Bancaria_Item, seção 5) é uma CÓPIA de Cad_Participante_Dados_Bancarios.Tipo_Conta no momento da geração, mesmo critério de fidelidade já usado para Codigo_Banco_Favorecido/Agencia_Favorecido/Conta_Favorecido — se o colaborador trocar de conta-salário para conta corrente depois de uma remessa já enviada, o item já enviado preserva o tipo transmitido naquele momento.

- Revisão 6 — a execução do pagamento (seção 6) passa a respeitar o bloco de fechamento "tesouraria" (Fase 0, seção 10, revisão 37), a mesma trava que Contas a Pagar/Receber aplica a Mov_Titulo/Mov_Titulo_Baixa (revisão 9 daquele documento) — nenhum campo novo, só o comportamento de aplicação descrito na seção 6. Sem checagem de pendência no fechamento, mesmo critério dos demais blocos do dicionário, exceto Compras.

- Revisão 6 — a competência usada no gate da baixa (seção 6) é derivada da data da própria baixa (Data_Baixa/Data_Recebimento_Cnab, Contas a Pagar/Receber seção 3), não da Data_Emissao do título original — um título nascido num mês pode ser baixado num mês seguinte já fechado para "tesouraria", sem que isso reabra ou afete o fechamento do mês de nascimento (bloco/competência avaliados independentemente a cada evento); suposição razoável, não confirmada literalmente por Alberto neste nível de detalhe.

- Revisão 7 — Bloco 1 da validação geral (Relatório de Validação Geral e Desenho do Bloco 1): Cad_Conta_Bancaria passa a referenciar Cad_Instituicao_Financeira (Fase 0) em vez do código do banco em texto livre. A convenção completa (vigência, identidade + versão, sucessão de códigos oficiais, competência, CNPJ alfanumérico, um campo por informação, saldos guardados de período fechado, sequência de fechamento) vive na Fase 0, seções 2 e 10 (revisão 41).

- Revisão 8 — tipo lógico "código (n)" definido por Alberto — todo campo que identifica algo (inscrição, documento, agência, conta, número e série de nota, matrícula, código oficial) é caractere, nunca numérico: os zeros à esquerda fazem parte do código, e o padrão pode passar a aceitar letras ou mudar de tamanho, como aconteceu com o CNPJ alfanumérico. Campos revistos: Agencia, Agencia_Favorecido, Carteira_Cobranca, Chave_Pix, Chave_Pix_Favorecido, Codigo_Banco_Favorecido, Codigo_Barras, Conta_Favorecido, Convenio_Cobranca, Digito_Agencia, Digito_Conta, Documento_Banco, Nosso_Numero, Numero_Conta. Convenção completa na Fase 0, seção 2.6 (revisão 42).

13\. Próximo Passo

*A Revisão 3 fechou todos os ganchos que a Revisão 2 havia deixado explícitos: canal de notificação da régua, tela de consistência para retorno sem remessa correspondente, campo de origem em Mov_Titulo_Baixa (patch em Contas a Pagar/Receber), cadastro de dados bancários do fornecedor (Fase 0), bandas de aging configuráveis, gatilho automático (por sugestão) de devedor duvidoso, e a integração de fato dos gatilhos de bloqueio dentro de Mov_Cotacao_Venda (patch em CRM & Vendas) — além de estender o desenho para cobrir API e Open Finance, ao lado do arquivo CNAB, e o rastreio de provedores técnicos de integração como a Celcoin. A Revisão 4 (ciclo "consolidar") foi só texto: confirmou, sem mudança estrutural, que ID_Autorizacao_Api/Status_Autorizacao_Api (seção 5, seção 12) já serve genericamente ao fluxo Pay by Bank.*

*Esta Revisão 5 (mesmo ciclo "consolidar") conecta a remessa de pagamento à folha (Fase 5 — Folha & RH, via Contas a Pagar/Receber, revisão 8), pedido por Alberto para que o pagamento de colaboradores use de fato os mesmos layouts CNAB/API já existentes, em vez de um mecanismo à parte: Mov_Remessa_Bancaria ganha ID_Tipo_Servico_Lote (seção 5), distinguindo lote de fornecedor (código 20), salário (código 30, com suporte a crédito em conta e a cartão-salário) e tributo por código de barras (código 22, Segmento O); Mov_Remessa_Bancaria_Item ganha as formas de lançamento cartao_salario/codigo_barras, o campo Codigo_Barras correspondente, e Tipo_Conta_Favorecido, que diferencia conta-salário de conta corrente/poupança — cópia de Cad_Participante_Dados_Bancarios.Tipo_Conta (Fase 0, revisão 30, também construída nesta consolidação). Em rescisão por óbito, o favorecido do pagamento já chega resolvido para o beneficiário certo, sem tratamento especial nesta Tesouraria — resolvido inteiramente do lado de Folha & RH/Contas a Pagar/Receber.*

*Ponto que fica como observação, não como gancho bloqueante: o critério de sugestão automática da tela de consistência (seção 6) é uma extensão minha por analogia, não uma confirmação literal — vale revisitar se Alberto notar comportamento diferente do esperado.*

*Esta Revisão 6 conecta este documento ao mecanismo transversal de fechamento de período generalizado na Fase 0 (seção 10, revisão 37): a execução do pagamento — a baixa automática gerada pelo retorno bancário e a baixa manual disparada a partir desta Tesouraria (seção 6) — passa a travar por Filial+competência sob o bloco "tesouraria", o MESMO bloco, não um bloco coordenado, que Contas a Pagar/Receber usa para travar o nascimento/alteração de Mov_Titulo e de Mov_Titulo_Baixa (revisão 9 daquele documento, mesma consolidação): apesar de as duas entidades estarem fisicamente cadastradas naquele documento, a trava é uma só, cobrindo os dois lados do fluxo — entrada de título e execução de pagamento. Sem checagem de pendência no fechamento, por decisão de Alberto — diferente de Compras, o único bloco do dicionário com essa validação — porque um título em aberto aguardando pagamento é o estado normal deste bloco.*

*Seguindo a ordem original do Documento Analítico, o módulo natural seguinte continua sendo Contabilidade & Fiscal (apuração de impostos, SPED, inclusive o tratamento de PIS/COFINS sobre rendimento financeiro, as retenções de IR/ISS/INSS/IOF em pagamento a fornecedor — seção 5 — e o lançamento da provisão para devedores duvidosos — seção 8 —, todos deixados como gancho) — mas, como sempre neste projeto, a decisão de por onde continuar é sua.*

*Revisão 7 — Bloco 1 da validação geral consolidado junto com a Fase 0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal) e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação antes de consolidar.*

*Revisão 8 — tipo lógico "código" aplicado junto com a revisão 42 da Fase 0. Próximos passos combinados com Alberto: Bloco 2 (fiscal) e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação antes de consolidar.*



14\. Anexo --- Entidades novas da revisão 25 (documentos 107 e 124)

Revisão 25 do dicionário: a ordem de pagamento ao exterior, aprovada por Alberto em 27/10/2026.

14.1. Remessa internacional (documentos 107 e 124)

Mov_Remessa_Bancaria_Item_Exterior

A ordem de pagamento ao exterior (D-N371; documentos 107 e 124, Q107-1 a Q107-6 e Q107-1a, 1b, 2a, 2b, 3a, 4a e 6a, aprovadas por Alberto em 27/10/2026 com "sim aprovo"). Uma linha por item de remessa de pagamento que vai ao exterior (Forma_Lancamento = transferencia_internacional); o item de remessa, com 33 campos quase todos "só quando cobrança" ou "só quando pagamento", não ganha mais campos opcionais. Sem vigência (é um fato). **Cópia do que foi transmitido**, no mesmo critério dos campos do favorecido do item: o que foi enviado fica registrado mesmo que o cadastro mude depois. Regras: (1) a ordem só existe quando o banco do favorecido está no exterior, e o item ao exterior exige a linha; (2) validações da geração, que bloqueiam a remessa: SWIFT do favorecido, IBAN ou número da conta, natureza copiada do título, Responsavel_Tarifas escolhido e moeda da ordem igual à do título; avisos sem bloquear: país do SWIFT diferente do país do banco e roteamento ausente em país que costuma exigir; (3) a natureza do câmbio é sempre a do título e **não pode ser trocada** no título enquanto houver ordem gerada e não rejeitada (Q107-6 e 6a); (4) o ERP **sugere** o responsável pelas tarifas pela última ordem do participante e o operador confirma sempre (Q107-4a); (5) a forma do Y520 é deduzida (ordem em moeda estrangeira: forma 1; em reais: forma 2, que o contador confirma) e confirmada na tela ao gerar; (6) a baixa automática nasce do retorno aceito com a taxa do contrato (a do retorno vale sobre a Taxa_Cambio_Contrato_Previo) e a classificação do Y520 nasce classificada, com a forma e a natureza da ordem e a referência = Numero_Contrato_Cambio do retorno; sem taxa, o item fica pendente na área de inconsistências; (7) uma remessa de pagamento tem só itens ao exterior ou só itens nacionais, e a conta de origem da remessa ao exterior fica em banco brasileiro; as formas 4 e 5 do Y520 não passam por remessa; (8) tarifas e IOF do câmbio chegam pelo retorno nos campos que já existem, e o tratamento contábil é do contador; (9) um só banco intermediário por ordem.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Exterior** | *identificador* | --- |
| **ID_Item_Remessa** | *referência (Mov_Remessa_Bancaria_Item), única* | O item a que a ordem pertence. Um item, no máximo uma linha. |
| **ID_Moeda** | *referência (Cad_Moeda)* | A moeda da ordem: a do título. Quando existe esta linha, Valor_Principal_Remessa do item está nesta moeda. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | Copiada do título (documento 103). A mesma natureza vai ao Y520. |
| **Codigo_Swift_Favorecido** | *código (11)* | O SWIFT do banco do favorecido, copiado de Cad_Instituicao_Financeira. Obrigatório. |
| **Iban_Favorecido** | *código (34), opcional* | Copiado do dado bancário do participante. |
| **Codigo_Roteamento_Favorecido** | *código (20), opcional* | Copiado do dado bancário do participante. |
| **Nome_Banco_Favorecido** | *texto* | O nome do banco, como foi transmitido. |
| **ID_Pais_Banco_Favorecido** | *referência (Cad_Pais)* | O país do banco, copiado da instituição. |
| **Endereco_Favorecido** | *texto, opcional* | O endereço do favorecido, como foi transmitido (texto único, copiado do endereço do participante). |
| **Responsavel_Tarifas** | *enumeração {remetente, dividido, favorecido}* | Quem paga as tarifas dos bancos: OUR (remetente), SHA (dividido) ou BEN (favorecido), o campo "details of charges" da mensagem SWIFT. Escolhido por quem paga, **sem valor padrão do ERP**; o ERP sugere pela última ordem do participante e o operador confirma sempre. |
| **Codigo_Swift_Intermediario** | *código (11), opcional* | O banco intermediário, copiado do dado bancário do participante. |
| **Codigo_Roteamento_Intermediario** | *código (20), opcional* | Idem. |
| **Conta_Intermediaria** | *código (34), opcional* | A conta do favorecido (ou do banco dele) no intermediário. |
| **Numero_Contrato_Cambio_Previo** | *código (40), opcional* | O contrato de câmbio **já fechado antes** da ordem, quando houver. Vazio quando o banco abre o contrato ao executar. |
| **Taxa_Cambio_Contrato_Previo** | *número, opcional (8 casas)* | A taxa do contrato fechado antes (Q107-1a), obrigatória quando Numero_Contrato_Cambio_Previo está preenchido. Serve de **taxa sugerida** na baixa quando o retorno não a traz; quando o retorno traz a taxa, **vale a do retorno**. |



15\. Anexo --- Documento 250: motor de envio bancário (entidades novas da revisão 56)

Revisão 56 do dicionário (consolidação de 23/11/2026, pelas recomendações): 15 entidades novas neste módulo, do documento 250 (versão 16; D-N639 a D-N658): o motor de envio bancário (motor nº 35), que serve a qualquer banco por **drivers** (um plugin por banco e canal, como o `Cad_Dfe_Driver` dos documentos fiscais), com a **matriz de capacidades** que mostra ou esconde cada operação, o canal da conta (ambiente e referência ao cofre, nunca o segredo), as carteiras de cobrança cadastradas em cada banco (D-N655), a mensagem e o histórico de cada envio, o mapa de ocorrências (o código do banco vira a ação do ERP, inclusive o **motivo da baixa**), o webhook, o DDA, o Pix Automático, os dados de tributo e de cobrança do item e os certificados de confiança dos bancos. **A carga de drivers e de mapas só vem quando houver o manual de cada banco**; DDA e Pix Automático estão desenhados e ficam desligados na matriz até a fase 2 do produto (R115). Os 53 campos novos de 5 entidades existentes (remessa, item de remessa, retorno, item de retorno e extrato) estão nas próprias entidades, e os 2 domínios novos, na Fase 0.

15.1. Núcleo do motor de envio bancário: driver, matriz de capacidades, canal da conta, webhook, mensagem, histórico e mapa de ocorrências (documento 250)

Cad_Banco_Driver

Revisão 56 (documento 250; D-N639 a D-N658): **O driver: um canal de um banco (ou de um agregador).** Espelha o `Cad_Dfe_Driver` (o registro de plugins dos documentos fiscais): cada combinação de **banco e canal** é um plugin com versão e vigência. Trocar a versão do layout ou da API é uma nova versão do registro, não uma alteração de código dos módulos.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Banco_Driver** | *identificador* | --- |
| **ID_Banco_Driver_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Banco_Driver_Versao). ID_Banco_Driver é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **Codigo** | *código (até 40) --- identidade* | Código único do plugin (ex.: CNAB240_COBRANCA_033, API_COBRANCA_001, AGREGADOR_X); campo de identidade |
| **Nome** | *texto* | Nome para tela e log |
| **ID_Instituicao_Financeira** | *referência (Cad_Instituicao_Financeira), opcional* | O banco a que o plugin pertence; vazio no agregador, que atende vários bancos |
| **Tipo_Canal** | *enumeração {cnab_150, cnab_240, cnab_400, cnab_500, cnab_750, api_rest, api_soap, open_finance, agregador}* | `api_soap` (versão 8 do documento 250) é o webservice SOAP/XML da cobrança da Caixa, com envelope XML no lugar do JSON (R62); `cnab_500` (versão 11 do documento 250) é o **PAGFOR** do Bradesco, de 500 posições, que leva o Pix no cabeçalho (R101); `cnab_150` (versão 12 do documento 250) é o CNAB de **150 posições** do Pix Automático da Caixa, trocado por VAN (R110) |
| **Versao_Layout** | *texto, opcional* | A versão do manual ou da API que o plugin implementa (ex.: "Febraban 10.11", "API 2.10.0"); texto livre, porque cada banco numera de um jeito |
| **Versao_Driver** | *texto* | Versão do plugin |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

Cad_Banco_Driver_Capacidade

Revisão 56 (documento 250; D-N639 a D-N658): **A matriz de capacidades: o que cada driver faz.** Cada banco oferece um conjunto diferente de produtos e de formas de retorno (seção 3.8 do documento 250). Em vez de código com "se for o banco X", o ERP lê esta matriz e **mostra ou esconde** a operação (por exemplo, "baixar título" só aparece se o driver da conta tem o produto cobrança).

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Banco_Driver_Capacidade** | *identificador* | --- |
| **ID_Banco_Driver** | *referência (Cad_Banco_Driver)* | O driver |
| **Produto** | *enumeração {cobranca_boleto, boleto_com_pix, cobranca_pix, pagamento, tributo, pix_pagamento, extrato, posicao_cobranca, dda, pix_automatico, validacao_conta, fgts_saldo_rescisorio, debito_veicular}* | {cobranca_boleto, boleto_com_pix, cobranca_pix, pagamento, tributo, pix_pagamento, extrato, posicao_cobranca, dda, pix_automatico, validacao_conta, fgts_saldo_rescisorio, debito_veicular} Revisão 58 (documento 250; D-N675 e R137): novo valor `debito_veicular`, o débito veicular que a Mlegate paga (Bradesco, por API, PR e MG; outro estado por guia com código de barras, pelo produto `tributo`). Um driver à parte; sem canal, o produto fica desligado. Os valores do SISDEB (débito automático) só entram com contrato, na fase 2. |
| **Retorno_Por** | *enumeração {arquivo, webhook, consulta, webhook_e_consulta}* | Como o resultado volta |
| **Ambiente_Teste** | *enumeração {sim, nao, parcial}* | O Itaú tem sandbox no portal (sem certificado, com token de 5 minutos) e a emissão do boleto tem uma etapa `simulacao` que só valida; o Santander tem fontes que divergem (seção 3.5 do documento 250) |
| **Limite_Itens_Por_Mensagem** | *número, opcional* | Teto de itens por chamada ou lote (a Senior cita 100 pagamentos por chamada de Pix; o extrato do Bradesco devolve no máximo 5.000 transações por consulta; o PagBB do BB aceita 500 lançamentos por lote, o retorno do BB por API 10.000 boletos por chamada e o extrato do BB 120 registros por página, no mínimo 30) |
| **Janela_Maxima_Consulta_Dias** | *número, opcional* | O maior período que o banco aceita **numa só consulta** (o extrato do BB: 31 dias; o do Bradesco: 1 ano). O driver divide períodos maiores. É diferente de `Dias_Retroativos_Consulta`, que diz até onde dá para voltar |
| **Liberacao_Do_Lote** | *enumeração {pelo_erp_por_api, pelo_erp_por_arquivo, no_portal_do_banco, nao_exige}, opcional* | {pelo_erp_por_api, pelo_erp_por_arquivo, no_portal_do_banco, nao_exige}: quem dá a **liberação** que o banco pede depois de receber o lote. No PagBB do BB é o próprio cliente, por API, e a liberação não se desfaz (R58); no Itaú e no Bradesco a aprovação pós-autorizada é feita no portal do banco (`aguardando_aprovacao_no_banco`) |
| **Horario_Abertura** | *hora, opcional* | Hora em que o banco começa a aceitar o produto no dia (a TED do Bradesco abre às 06h30 e fecha às 17h, só em dia útil, R47) |
| **Horario_Corte** | *hora, opcional* | Hora limite do dia para o banco processar no mesmo dia |
| **Operacoes_Da_Linha** | *enumeração {todas, registro, alteracao_baixa_consulta}, opcional* | {todas, registro, alteracao_baixa_consulta}: quais operações do produto esta linha cobre, quando o banco dá **janelas diferentes por operação**. Na cobrança por webservice da Caixa o registro vale 24 horas e a alteração, a baixa e a consulta têm horário comercial; o driver cadastra **duas linhas** do mesmo produto. Vazio = todas (R64) |
| **Horario_Corte_Fim_De_Semana** | *hora, opcional* | A hora de fechamento aos sábados, domingos e feriados, quando difere da dos dias úteis (Caixa: 20h, contra 22h nos dias úteis; a abertura é às 8h nos dois casos) (R64) |
| **Periodicidade_Retorno_Minutos** | *número, opcional* | De quanto em quanto tempo o banco publica o retorno **em lote** quando há retorno "online": o do CNAB da Caixa sai a cada 15 minutos, além do consolidado do dia. Define a frequência da consulta do ERP e o que o painel chama de atraso do retorno (R24 e R67) |
| **Intervalo_Minimo_Entre_Chamadas_Segundos** | *número, opcional* | O intervalo mínimo que o driver deixa entre duas chamadas ao banco. O manual do Pix Automático da Caixa **proíbe rajada** de chamadas e a listagem da base sem consentimento do cliente, **sem dar o limite em número**; o valor é do canal e fica configurável, e o driver nunca dispara os itens de uma remessa em paralelo sem espaçamento (R72) |
| **Indisponivel_De** | *hora, opcional* | Início da janela diária em que a API **sai do ar** (a cobrança e o boleto híbrido do Bradesco: 00h00) |
| **Indisponivel_Ate** | *hora, opcional* | Fim dessa janela (03h00 no Bradesco). Dentro dela o driver não envia nem consulta e a fila do ERP espera (R40) |
| **Dias_Maximos_Agendamento** | *número, opcional* | Até quantos dias à frente o banco aceita agendar (a MUFG cita 30 dias corridos; no Pix Automático, 10 dias corridos antes da data, versão 9 do documento 250) |
| **Dias_Minimos_Antecedencia_Agendamento** | *número, opcional* | O mínimo de dias corridos **antes** da data em que o banco aceita receber a instrução de cobrança (Pix Automático: 2; o máximo, 10, fica em `Dias_Maximos_Agendamento`). Fora da faixa o banco rejeita (R79) |
| **Horario_Limite_Cancelamento_Recebedor** | *hora, opcional* | A hora limite, no **dia anterior** à liquidação, para o recebedor cancelar uma cobrança agendada (Pix Automático da Caixa: 22h; o pagador cancela pelo app dele até 23h59 e o ERP só recebe o aviso) (R81) |
| **Confirmacao_Apos_Consulta** | *booleano, opcional* | {sim, nao}: se o produto de pagamento tem **duas etapas**, uma que **consulta e valida** (e devolve os valores atualizados) e outra que **confirma** o pagamento. É assim no Santander (todos os produtos de pagamento) e no tributo e na conta de consumo do Bradesco (`tipoRegistro` 0 e 1). `sim` faz o ERP guardar o valor da consulta, conferir com o título e só então confirmar (R86 e R87). Vazio = uma etapa só |
| **Janela_Sequencia_Arquivo** | *número, opcional* | Bradesco, cobrança em CNAB 400: quantos números **acima** do último o banco aceita no número sequencial da remessa (**10**). Número **menor** que o último **rejeita o arquivo inteiro**; até 10 acima o banco aceita, e os números pulados podem ser usados no mesmo dia. O ERP numera em sequência por canal e nunca reaproveita número (R96) |
| **Cancelamento_Pagamento_Por** | *enumeração {arquivo, api, portal, nao_ha}, opcional* | {arquivo, api, portal, nao_ha}: por onde o ERP **cancela ou altera** um pagamento já enviado. No Multipag do Bradesco é por **arquivo** (exclusão, alteração de valor e de data, bloqueio e liberação, `pelo_erp_por_arquivo` em `Liberacao_Do_Lote`); no Santander a API não traz cancelamento (R97) |
| **Dias_Retroativos_Consulta** | *número, opcional* | Até quantos dias para trás o banco deixa consultar (o Itaú: 2 anos nas consultas de Pix); define até onde dá para recuperar um webhook ou um arquivo perdido (R24). Bradesco: liquidados 60 dias a partir do pagamento; extrato até 10 anos (1 ano por consulta, por desempenho); pagamento de tributo 5 anos. BB: extrato até 5 anos; consulta de baixa operacional até 5 dias depois do pagamento (R56) |
| **Nosso_Numero_Gerado_Por** | *enumeração {banco, empresa}, opcional* | Só nos produtos de cobrança. Onde a empresa numera o título (o Itaú, na carteira 109), o ERP gera o nosso número em sequência por conta e carteira (R25). No BB também é a empresa que numera (20 posições, sequência por convênio; R54) |
| **Validade_Token_Minutos** | *número, opcional* | Quanto tempo vale o token que o banco emite (o Bradesco: 60 minutos; o sandbox do Itaú: 5). O ERP guarda o token e o reutiliza até perto do fim; pedir token a cada chamada pode bloquear a credencial no Bradesco (R39) |
| **Observacao** | *texto, opcional* | Particularidade do banco que não cabe em campo |

*Revisão 58 --- campos alterados: Produto; valores de enumeração novos: Produto (+debito_veicular).*

Cad_Conta_Bancaria_Canal

Revisão 56 (documento 250; D-N639 a D-N658): **O canal da conta: credencial, ambiente e retorno.** Uma conta pode usar canais diferentes por produto (cobrança por API e pagamento por CNAB, por exemplo) e ambientes diferentes (homologação e produção). Segue o padrão do `Cad_Autoridade_Fiscal_Credencial`: **o ERP guarda só a referência ao cofre**, nunca o segredo.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Conta_Bancaria_Canal** | *identificador* | --- |
| **ID_Conta_Bancaria_Canal_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Conta_Bancaria_Canal_Versao). ID_Conta_Bancaria_Canal é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | A conta (`Cad_Conta_Bancaria`) |
| **ID_Banco_Driver** | *referência (Cad_Banco_Driver)* | O plugin usado |
| **Produto** | *enumeração {cobranca_boleto, boleto_com_pix, cobranca_pix, pagamento, tributo, pix_pagamento, extrato, posicao_cobranca, dda, pix_automatico, validacao_conta, fgts_saldo_rescisorio, debito_veicular}* | {cobranca_boleto, boleto_com_pix, cobranca_pix, pagamento, tributo, pix_pagamento, extrato, posicao_cobranca, dda, pix_automatico, validacao_conta, fgts_saldo_rescisorio, debito_veicular} Revisão 58 (documento 250; D-N675 e R137): novo valor `debito_veicular`, o débito veicular que a Mlegate paga (Bradesco, por API, PR e MG; outro estado por guia com código de barras, pelo produto `tributo`). Um driver à parte; sem canal, o produto fica desligado. Os valores do SISDEB (débito automático) só entram com contrato, na fase 2. |
| **Ambiente** | *enumeração {homologacao, sandbox, producao}* | `sandbox` (versão 10 do documento 250) existe porque o Santander lista **três** ambientes na API de pagamentos (sandbox, homologação e produção); o Itaú também tem sandbox (R6) |
| **Tipo_Autenticacao** | *enumeração {nenhuma, oauth_client_credentials, oauth_mtls, jwt_bearer, oauth_senha_internet_banking, consentimento_open_finance, hash_na_mensagem}* | Os sete modos vistos nas fontes (seção 3.5 do documento 250); `nenhuma` é o CNAB por arquivo; `hash_na_mensagem` (versão 8 do documento 250) é o da cobrança da Caixa, em que o ERP calcula um hash SHA-256 que vai dentro do XML e **não há segredo nem token** (R63) |
| **ID_Certificado** | *referência (Cad_Certificado_Digital), opcional* | Certificado (`Cad_Certificado_Digital`) quando o banco exige mTLS. O Itaú pede, no portal oficial, um **certificado dinâmico** ativo para todas as APIs e um certificado mTLS no webhook de Pix (uma fonte secundária diz que o de NF-e não serve); o Santander aceita o A1 da NF-e; o Inter gera o certificado junto com a credencial |
| **Client_Id** | *texto, opcional* | Identificador público da aplicação no banco |
| **Referencia_Cofre_Segredo** | *texto, opcional* | Onde está o segredo (client secret, senha); o ERP não o grava |
| **Escopos** | *texto, opcional* | Escopos pedidos ao banco (o BB recusa o token se o escopo tiver API não habilitada) |
| **Url_Base_Api** | *texto, opcional* | Endereço base da API no ambiente do canal. O Itaú usa endereços diferentes para boleto, Pix e Pix Automático e já avisou que os do Pix mudam; por isso o endereço é dado do canal, não do código |
| **Url_Token_Autenticacao** | *texto, opcional* | Endereço de quem emite o token do banco (o Itaú usa um endereço por produto, por exemplo emissão de boleto e SISPAG, e outro, do portal, no sandbox). O webhook que o banco chama no ERP fica na entidade da seção 4.16 do documento 250 |
| **Codigo_Convenio** | *texto, opcional* | Convênio do canal; vazio = vale o `Convenio_Cobranca` da conta **D-N655:** com carteiras cadastradas (`Cad_Conta_Bancaria_Carteira`), vale a da carteira do título; este campo serve só à conta que não cadastrou carteira. |
| **Data_Expiracao_Credencial** | *data, opcional* | Vencimento da credencial ou do certificado (o do Inter vale 1 ano); alimenta o aviso |
| **Dias_Aviso_Vencimento** | *número, opcional* | Quantos dias antes avisar (mesmo padrão de `Cad_Certificado_Digital`) |
| **Referencia_Cofre_Chave_Aplicacao** | *texto, opcional* | Onde está a **chave da aplicação** que o BB exige em toda chamada (`gw-dev-app-key`, **na URL**; R53). Não é o segredo do token, mas identifica a aplicação e **não pode aparecer em log**; o ERP só guarda a referência ao cofre. Versão 8 do documento 250: na Caixa é o `apikey` do Pix Automático, que vai em **cabeçalho** de toda chamada, ao lado do token (R71) |
| **Codigo_Variacao_Carteira** | *texto, opcional* | A variação da carteira de cobrança (BB: obrigatória no registro, na consulta e no retorno por API; vazio = vale a da conta, que **não tem** esse campo). Convênio e carteira já existem (`Codigo_Convenio` e `Carteira_Cobranca`) **D-N655:** com carteiras cadastradas (`Cad_Conta_Bancaria_Carteira`), vale a da carteira do título; este campo serve só à conta que não cadastrou carteira. |
| **Modalidade_Cobranca** | *enumeração {simples_com_registro, simples_sem_registro, vinculada, descontada, financiada_vendor}, opcional* | A modalidade do convênio no BB: {simples_com_registro, simples_sem_registro, vinculada, descontada, financiada_vendor} (códigos 1, 2, 4, 6 e 8 do BB; o registro pela API só aceita simples e vinculada). Define quais comandos o banco aceita no convênio **D-N655:** com carteiras cadastradas (`Cad_Conta_Bancaria_Carteira`), vale a da carteira do título; este campo serve só à conta que não cadastrou carteira. |
| **Identificacao_Cliente_Http** | *texto, opcional* | O texto que o ERP envia no cabeçalho `User-Agent`. O manual do Pix Automático da Caixa avisa que um `User-Agent` genérico pode ser tratado como robô e bloqueado; o ERP envia um nome próprio e fixo, por canal (R72) |
| **Data_Validacao_Boleto_Impresso** | *data, opcional* | A data em que o banco validou as amostras do boleto que o **ERP imprime** neste convênio (Caixa: de 10 a 20 amostras entregues à agência centralizadora, R74). **Vazio = o ERP não gera o PDF do boleto desse banco para o convênio.** Não vale para o boleto que o próprio banco emite |
| **Padrao_Nome_Arquivo** | *texto, opcional* | O padrão do nome do arquivo que o banco exige (Bradesco: cobrança `CBDDMM??.REM`, PAGFOR `PGDDMMX.REM`; no teste a extensão é `TST` e o retorno vem como `RST`). No mesmo dia **não** se envia dois arquivos com o mesmo nome (R95) |
| **Id_Workspace_Banco** | *texto, opcional* | Santander: o identificador (UUID) do **workspace** no banco, que vai na **URL de toda chamada** de pagamento e de DDA. O workspace reúne a conta de débito principal, as adicionais e as chaves de cada produto (boleto, conta de consumo e tributo, Pix, TED, tributo por campo, DDA); é dado do canal, não da conta (R84) |
| **Meio_Transmissao** | *enumeração {portal_manual, host_a_host, api, van}, opcional* | Revisão 59 (documento 250; Q250-67, D-N680 e R139): Revisão 59 (documento 250; Q250-67, D-N680): **por onde o arquivo ou a chamada vai ao banco**, para o ERP saber se envia sozinho ou se gera o arquivo para o usuário enviar. `portal_manual`: o ERP **gera o arquivo** e o usuário o sobe no portal do banco (Net Empresa/WebTA do Bradesco, Itaú Empresas e o aplicativo web do Itaú para o CNAB 400), e o ERP espera o retorno; `host_a_host`: o ERP **envia e busca sozinho** pelo canal dedicado; `api`: chamada de API do banco; `van`: rede de valor agregado (por exemplo, a Caixa). Vazio = não informado. Cada combinação de layout e meio é **um canal** da conta (R138 e R139). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 58 --- campos alterados: Produto; valores de enumeração novos: Produto (+debito_veicular).*

*Revisão 59 --- campos novos: Meio_Transmissao.*

Mov_Banco_Mensagem

Revisão 56 (documento 250; D-N639 a D-N658): **A mensagem: o registro de tudo que vai e volta do banco.** É a trilha de integração, no padrão de `Mov_Dfe_Transmissao` e `Mov_Dfe_Tarefa`: toda chamada de API, todo arquivo enviado ou recebido e todo webhook viram uma linha. É ela que dá **idempotência** (não enviar duas vezes), **nova tentativa** e **prova** do que o banco respondeu.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Banco_Mensagem** | *identificador* | --- |
| **ID_Conta_Bancaria_Canal** | *referência (Cad_Conta_Bancaria_Canal)* | O canal usado |
| **Direcao** | *enumeração {envio, retorno}* | {envio, retorno} |
| **Tipo_Mensagem** | *enumeração {remessa, retorno_arquivo, registro_titulo, simulacao_titulo, instrucao_titulo, consulta, webhook, pagamento, extrato, dda}* | {remessa, retorno_arquivo, registro_titulo, simulacao_titulo, instrucao_titulo, consulta, webhook, pagamento, extrato, dda} |
| **Chave_Idempotencia** | *texto* | Código único por intenção (ex.: remessa + item + comando); o mesmo envio repetido não gera segunda linha efetiva. Onde o banco tem cabeçalho de idempotência (o `idempotency-key` do SISPAG do Itaú), é este valor |
| **Id_Correlacao_Banco** | *texto, opcional* | O identificador que o banco devolve ou exige. O Itaú exige o `x-itau-correlationID` em toda chamada e quem o gera é o ERP; o Pix usa `txid` e `E2eid` |
| **ID_Remessa** | *referência (Mov_Remessa_Bancaria), opcional* | A remessa de origem, quando houver |
| **ID_Retorno** | *referência (Mov_Retorno_Bancario), opcional* | O retorno gerado, quando houver |
| **Status** | *enumeração {pendente, enviada, aceita, rejeitada, erro_transiente, erro_definitivo, duplicada}* | {pendente, enviada, aceita, rejeitada, erro_transiente, erro_definitivo, duplicada} |
| **Tentativa** | *número* | Número da tentativa |
| **Proxima_Tentativa** | *data/hora, opcional* | Quando tentar de novo (só `erro_transiente`) |
| **Codigo_Retorno** | *texto, opcional* | Código HTTP ou do banco e o texto (2 campos) |
| **Descricao_Retorno** | *texto, opcional* | Código HTTP ou do banco e o texto (2 campos) |
| **Data_Hora_Envio** | *data/hora* | Quando saiu (ou quando chegou, no retorno) |
| **Data_Hora_Resposta** | *data/hora, opcional* | Quando o banco respondeu |
| **ID_Documento_Corpo_Envio** | *referência (Cad_Documento), opcional* | O corpo enviado e o recebido, guardados como documento (`Cad_Documento`, o mesmo destino que `Mov_Dfe_Transmissao` usa para o XML), para auditoria (2 campos) |
| **ID_Documento_Corpo_Retorno** | *referência (Cad_Documento), opcional* | O corpo enviado e o recebido, guardados como documento (`Cad_Documento`, o mesmo destino que `Mov_Dfe_Transmissao` usa para o XML), para auditoria (2 campos) |

Mov_Remessa_Bancaria_Evento

Revisão 56 (documento 250; D-N639 a D-N658): **O histórico de situação da remessa.** A remessa hoje não tem situação. Cada mudança vira uma linha, e o campo `Status` da remessa (seção 4.12 do documento 250) guarda só o valor atual.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Remessa_Evento** | *identificador* | --- |
| **ID_Remessa** | *referência (Mov_Remessa_Bancaria)* | A remessa |
| **Status** | *enumeração {gerada, aguardando_envio, enviada, recebida_pelo_banco, aguardando_aprovacao_no_banco, aguardando_liberacao, parcialmente_processada, processada, rejeitada, cancelada}* | `aguardando_liberacao` (versão 7 do documento 250) é a espera pela **liberação que o próprio ERP dá por API** (PagBB do BB, R58), diferente de `aguardando_aprovacao_no_banco` |
| **Data_Hora_Evento** | *data/hora* | Quando mudou |
| **ID_Participante_Responsavel** | *referência (Cad_Participante), opcional* | Quem causou a mudança (vazio quando foi o retorno do banco) |
| **ID_Banco_Mensagem** | *referência (Mov_Banco_Mensagem), opcional* | A mensagem que causou a mudança |
| **Observacao** | *texto, opcional* | Texto livre |

Cad_Banco_Ocorrencia_Mapa

Revisão 56 (documento 250; D-N639 a D-N658): **O mapa de ocorrências: o código do banco vira ação do ERP.** O mesmo código tem significado diferente por banco e por versão (o código `BD` é «inclusão efetuada com sucesso» no Bradesco e na Caixa e «pagamento agendado» no SISPAG do Itaú; nos três, o pagamento foi **aceito e ainda não foi pago**, e o ERP não o baixa). O mapa traduz o código que o banco mandou para a **ocorrência padrão** do ERP (`tipo_ocorrencia_retorno_bancario`) e diz o que o ERP faz.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Banco_Ocorrencia_Mapa** | *identificador* | --- |
| **ID_Banco_Ocorrencia_Mapa_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Banco_Ocorrencia_Mapa_Versao). ID_Banco_Ocorrencia_Mapa é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Banco_Driver** | *referência (Cad_Banco_Driver)* | O driver cujo código está sendo traduzido |
| **Tipo_Mensagem** | *enumeração {retorno_cobranca, retorno_pagamento, webhook}* | {retorno_cobranca, retorno_pagamento, webhook} |
| **Codigo_Banco** | *código (até 30)* | O código como o banco manda (texto até 30; pode ser alfanumérico, como `BD`, `ZI`, `5A`, ou uma palavra, como `BAIXA_EFETIVA` e `BAIXA_OPERACIONAL` no webhook do Itaú) |
| **Descricao_Banco** | *texto* | O texto do manual do banco |
| **ID_Codigo_Ocorrencia** | *referência (Cad_Classe_Sistema, domínio = tipo_ocorrencia_retorno_bancario)* | A ocorrência padrão do ERP (`Cad_Classe_Sistema`, domínio `tipo_ocorrencia_retorno_bancario`) |
| **Acao_Erp** | *enumeração {baixar_titulo, confirmar_registro, rejeitar, informativo, lancar_tarifa, reapresentar, alertar, estornar_baixa, encerrar_sem_pagamento}* | `estornar_baixa` (versão 7 do documento 250) desfaz uma baixa já feita, como o código 10 do webhook do BB, o cancelamento da baixa operacional (R56); `encerrar_sem_pagamento` (versão 12 do documento 250) encerra a cobrança **sem pagar** o título: cancelamento, decurso de prazo, baixa pelo banco, protesto ou transferência para desconto. O título continua em aberto e abre tratamento (R107) |
| **Motivo_Baixa** | *enumeração {pagamento, pagamento_em_cartorio, cancelamento_pelo_beneficiario, cancelamento_pelo_pagador, decurso_de_prazo, baixa_pelo_banco, baixa_por_protesto, transferencia_para_desconto, outro}, opcional* | O **motivo** da baixa, quando a ocorrência é de baixa: {pagamento, pagamento_em_cartorio, cancelamento_pelo_beneficiario, cancelamento_pelo_pagador, decurso_de_prazo, baixa_pelo_banco, baixa_por_protesto, transferencia_para_desconto, outro} (domínio `motivo_baixa_titulo_bancario`). Só `pagamento` e `pagamento_em_cartorio` permitem `baixar_titulo`; os demais usam `encerrar_sem_pagamento` (R107) |
| **Codigo_Complementar_Banco** | *texto, opcional* | O código que **complementa** a ocorrência e muda o seu significado, como o banco manda (texto até 30). No Itaú é a **agência cobradora** do retorno de cobrança: 7744 (pedido de baixa do beneficiário), 7788 (baixa automática) e 7777 (baixa pelo banco). A linha do mapa passa a ser a **dupla** código e complemento (R109) |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

Cad_Conta_Bancaria_Canal_Webhook

Revisão 56 (documento 250; D-N639 a D-N658): **O webhook do canal: onde e como o banco avisa o ERP.** Acréscimo da versão 3 do documento 250, a partir da API de boletos do Itaú: o banco cadastra, **por conta e por tipo de aviso**, o endereço do ERP, a forma como o banco se autentica ao chamá-lo e o valor mínimo para avisar. Substitui o campo `Url_Retorno_Webhook` que a versão 2 do documento 250 colocava no canal. Segue o padrão do `Cad_Autoridade_Fiscal_Credencial`: o segredo só no cofre.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Canal_Webhook** | *identificador* | --- |
| **ID_Conta_Bancaria_Canal** | *referência (Cad_Conta_Bancaria_Canal)* | O canal a que o aviso pertence |
| **Tipo_Notificacao** | *enumeração {baixa_efetiva, baixa_operacional, pix_recebido, pix_devolucao, pix_automatico_recorrencia, pix_automatico_solicitacao, pix_automatico_cobranca, outro}* | O Itaú cadastra a baixa efetiva e a operacional em separado; o aviso de devolução de Pix só por pedido ao contato comercial; o Pix Automático tem um webhook para a recorrência e outro para a cobrança |
| **Url_Callback** | *texto* | Endereço HTTPS do ERP que o banco chama; no Itaú não pode ser um endereço IP, e no aviso de Pix o banco acrescenta o sufixo `/pix` ao endereço cadastrado |
| **Tipo_Autenticacao_Callback** | *enumeração {nenhuma, oauth_client_credentials, mtls}* | Como o banco se identifica ao chamar o ERP. No Itaú, o aviso de boleto usa OAuth (o ERP expõe um endereço de token) e o de Pix e os de Pix Automático usam certificado mTLS (o ERP confia na autoridade certificadora do próprio Itaú) |
| **Url_Autenticacao_Callback** | *texto, opcional* | Endereço do ERP onde o banco pega o token antes de chamar (só HTTPS) |
| **Escopo_Callback** | *texto, opcional* | Escopo que o banco pede ao pegar o token |
| **Client_Id_Callback** | *texto, opcional* | O identificador que o ERP deu ao banco para pegar o token |
| **Referencia_Cofre_Callback** | *texto, opcional* | Onde está o segredo que o ERP deu ao banco; o ERP não o grava |
| **Valor_Minimo_Notificacao** | *número, opcional* | Valor abaixo do qual o banco não avisa (no Itaú, o padrão é R$ 0,10; liquidação de valor menor não gera aviso, e a consulta continua sendo a rede de segurança, R24) |
| **Chave_Pix** | *texto, opcional* | A chave Pix a que o webhook de Pix pertence (até 77 posições): no Itaú o cadastro é **por chave**, e só o Pix recebido por chave é avisado |
| **Id_Registro_Banco** | *texto, opcional* | O identificador do cadastro no banco (no Itaú: agência, conta, DAC e o código do tipo de aviso) |
| **Situacao** | *enumeração {pendente_cadastro, aguardando_banco, ativo, inativo, com_erro}* | `aguardando_banco` é a espera depois do envio do certificado público por e-mail, onde o banco cadastra o aviso à mão (o Bradesco leva até 5 dias úteis; R40) |
| **Data_Hora_Cadastro** | *data/hora, opcional* | Quando o banco confirmou o cadastro |

Cad_Conta_Bancaria_Carteira

Revisão 56 (documento 250; D-N639 a D-N658): **As carteiras de cobrança registradas em cada banco.** Pedido de Alberto (23/11/2026): "em todos os bancos tem que abrir para criar o número da carteira; deixar cadastrado para cada banco as carteiras registradas neles". Uma linha por **conta bancária e carteira**, com a variação, o convênio e a modalidade, **criada pelo usuário em qualquer banco**: nada é fixo no ERP nem no driver. O item de cobrança aponta para a carteira (`ID_Carteira_Cobranca`); sem escolha, vale a carteira marcada como padrão da conta. Os campos `Codigo_Convenio`, `Codigo_Variacao_Carteira` e `Modalidade_Cobranca` do canal passam a valer só para a conta que não cadastrou carteira. **Leitura minha:** o convênio mora na carteira (o mesmo banco pode ter vários convênios, um por carteira). Chave de negócio: conta bancária, número da carteira, variação e `Vigencia_Inicio`. **A Caixa (versão 16 do documento 250):** o campo de carteira do CNAB 240 tem 1 posição e o retorno traz o `1` para cobrança simples; o convênio tem 7 posições e **não há campo de variação**; o nosso número leva 2 posições de modalidade mais 15 de identificação.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Conta_Bancaria_Carteira** | *identificador* | --- |
| **ID_Conta_Bancaria_Carteira_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Conta_Bancaria_Carteira_Versao). ID_Conta_Bancaria_Carteira é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | A conta no banco a que a carteira pertence (o banco vem da conta) |
| **Numero_Carteira** | *código (até 10) --- identidade* | O número da carteira como o banco o identifica, escrito pelo usuário; cada banco usa um código e o ERP não os fixa; campo de identidade |
| **Codigo_Variacao_Carteira** | *código (até 10), opcional* | A variação da carteira, quando o banco a exige (o BB) |
| **Codigo_Convenio** | *código (até 20), opcional* | O convênio de cobrança desta carteira, quando o banco trabalha por convênio (BB, Caixa, Bradesco e outros); vazio usa o `Convenio_Cobranca` da conta |
| **Modalidade_Cobranca** | *enumeração {simples_com_registro, simples_sem_registro, vinculada, descontada, caucionada, cessao, financiada_vendor}, opcional* | A modalidade da carteira no banco |
| **Descricao** | *texto, opcional* | Nome para a tela (por exemplo, "Cobrança simples registrada") |
| **Padrao** | *booleano* | Verdadeiro na carteira que vale quando o título não escolhe uma; uma só por conta (aviso do Motor se houver mais de uma) |
| **Situacao_Carteira** | *enumeração {ativa, suspensa, encerrada}* | A situação da carteira no banco; só a ativa recebe título novo |
| **Data_Habilitacao_Banco** | *data, opcional* | Quando o banco habilitou a carteira (conferência com o contrato) |
| **Layout_Cnab** | *enumeração {240, 400}, opcional* | Revisão 59 (documento 250; Q250-63, D-N688 e R150): Revisão 59 (documento 250; Q250-63, D-N688, R150): o layout do CNAB **desta carteira**, quando for **diferente** do padrão da conta. **Vazio = usa o `Layout_Cnab` da conta** (`Cad_Conta_Bancaria`), que é o padrão dos registros novos. Vale só para registros **novos**; o título guarda o layout em que foi registrado (R132). A carteira com layout próprio exige canal ativo daquele layout na conta (`Cad_Conta_Bancaria_Canal`); senão o ERP recusa o registro. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 59 --- campos novos: Layout_Cnab.*

15.2. DDA: boletos que o banco entrega ao pagador (documento 250; desenhado agora, implementado na fase 2 do produto)

Mov_Dda_Titulo

Revisão 56 (documento 250; D-N639 a D-N658): **DDA: o boleto emitido contra a empresa.** O Débito Direto Autorizado entrega ao ERP, antes do vencimento, os boletos emitidos contra o CNPJ da empresa. Serve para o contas a pagar **achar** o título e para **não pagar duas vezes**.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Dda_Titulo** | *identificador* | --- |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | A conta cujo DDA entregou o boleto |
| **ID_Banco_Mensagem** | *referência (Mov_Banco_Mensagem), opcional* | A mensagem de origem |
| **Chave_Titulo** | *texto* | Banco mais o campo livre do código de barras (posições 20 a 44), como na fonte do layout DDA |
| **Codigo_Barras** | *texto, opcional* | Código de barras |
| **ID_Participante_Beneficiario** | *referência (Cad_Participante), opcional* | O fornecedor, quando o CNPJ já está cadastrado |
| **Documento_Beneficiario** | *texto* | CPF ou CNPJ do beneficiário |
| **Nome_Beneficiario** | *texto* | Nome do beneficiário |
| **Data_Vencimento** | *data* | Vencimento |
| **Valor_Nominal** | *número* | Valor |
| **Numero_Documento** | *texto, opcional* | Número do documento do beneficiário |
| **Status** | *enumeração {recebido, vinculado, pago, baixado_pelo_beneficiario, alterado, ignorado}* | {recebido, vinculado, pago, baixado_pelo_beneficiario, alterado, ignorado} |
| **ID_Titulo** | *referência (Mov_Titulo), opcional* | O título a pagar vinculado (`Mov_Titulo`) |
| **Data_Hora_Recebimento** | *data/hora* | Quando o ERP recebeu |
| **Data_Hora_Vinculo** | *data/hora, opcional* | Quando foi vinculado a um título |
| **Identificador_Dda_Banco** | *texto, opcional* | Santander: o identificador do boleto no DDA (`authorizedDirectDebitId`, 17 posições no exemplo) que a consulta de detalhe pede, junto com o código e o CPF ou CNPJ do pagador |
| **Documento_Pagador** | *texto, opcional* | O CPF ou CNPJ de **quem** o boleto foi emitido contra, quando o DDA devolve (o do Santander cobre também os CNPJ agregados, como as filiais). Liga o boleto à filial certa (R15) |
| **Data_Limite_Pagamento** | *data, opcional* | A data limite para pagar, diferente do vencimento (`paymentLimitDate`). Depois dela o banco não aceita o pagamento do boleto |
| **Valor_Minimo** | *número, opcional* | O menor valor aceito, quando o boleto permite pagamento parcial (`minimumValue`) |
| **Codigo_Situacao_Banco** | *texto, opcional* | A situação **como o banco manda** (Santander: aberto a vencer, aberto vencido, agendado, pago, emitido e oculto, mais o código e a descrição do detalhe); o ERP guarda o bruto e o `Status` é a tradução (R10) |

15.3. Pix Automático: recorrência, cobrança e tentativa (documento 250; desenhado agora, implementado na fase 2 do produto)

Mov_Pix_Recorrencia

Revisão 56 (documento 250; D-N639 a D-N658): **Pix Automático: a recorrência autorizada.** Para cobrar mensalidades e parcelas de contrato por débito autorizado pelo cliente. A recorrência nasce "pendente de confirmação" e só aceita cobrança depois de confirmada pelo pagador.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Pix_Recorrencia** | *identificador* | --- |
| **ID_Conta_Bancaria** | *referência (Cad_Conta_Bancaria)* | A conta recebedora |
| **ID_Participante_Pagador** | *referência (Cad_Participante)* | O cliente |
| **ID_Gestao_Contrato** | *referência (Cad_Gestao_Contrato), opcional* | O contrato que gera as cobranças (`Cad_Gestao_Contrato`) |
| **Id_Recorrencia** | *texto* | O identificador de 29 posições do arranjo (padrão "RR", "RN", "CR" ou "CN" + 8 do agente + data + sequencial de 11); o segundo caractere diz se permite nova tentativa |
| **Id_Solicitacao** | *texto, opcional* | Identificador da solicitação de confirmação (29 posições), necessário para cancelar a solicitação enviada ao app do cliente |
| **Jornada** | *enumeração {sem_qr_notificacao_app, qr_so_recorrencia, qr_com_cobranca_imediata, qr_com_pagamento_ou_agendamento, aguardando_definicao}* | As quatro jornadas do guia do BCB, na ordem em que o Itaú as numera (`JORNADA_1` a `JORNADA_4`, mais `AGUARDANDO_DEFINICAO`; a correspondência é leitura minha) |
| **Status** | *enumeração {pendente_confirmacao, aprovada, rejeitada, cancelada, expirada}* | (no Itaú: CRIADA, APROVADA, REJEITADA, CANCELADA e EXPIRADA) |
| **Status_Solicitacao** | *enumeração {criada, enviada, recebida, rejeitada, aceita, expirada, cancelada}, opcional* | A solicitação de confirmação enviada ao app do cliente (jornada sem QR) tem ciclo próprio no Itaú; a recorrência fica `pendente_confirmacao` até a solicitação ser `aceita` |
| **Periodicidade** | *enumeração {anual, semestral, trimestral, mensal, semanal}* | (os mesmos cinco valores da API do Itaú) |
| **Politica_Retentativa** | *enumeração {nao_permite, permite_ate_3_em_7_dias}* | (no Itaú: `NAO_PERMITE` e `PERMITE_3R_7D`) |
| **Valor_Fixo** | *número, opcional* | Quando a parcela é fixa (`valorRec` no Itaú) |
| **Valor_Maximo** | *número, opcional* | Teto autorizado pelo cliente, quando o valor varia |
| **Valor_Minimo_Recebedor** | *número, opcional* | Valor mínimo que o recebedor define quando o valor varia; **a API do Itaú não aceita ao mesmo tempo o valor fixo e o mínimo** (R30) |
| **Chave_Pix_Recebedor** | *texto* | A chave Pix (DICT) da conta que recebe, copiada no envio (até 77 posições): a conta pode ter mais de uma chave e a API pede a usada |
| **Contrato_Vinculo** | *texto* | Número do contrato que a recorrência paga, como foi transmitido (até 35 posições); obrigatório na API do Itaú |
| **Objeto_Vinculo** | *texto* | Descrição do contrato, como foi transmitida (até 35 posições); obrigatória na API do Itaú |
| **Id_Location_Recorrencia** | *texto, opcional* | Identificador numérico da location da recorrência no banco; a API do Itaú pede na criação da cobrança |
| **Data_Inicio** | *data, opcional* | Vigência da recorrência (2 campos) |
| **Data_Fim** | *data, opcional* | Vigência da recorrência (2 campos) |
| **Location** | *texto, opcional* | URL do payload (até 77 posições) |
| **Data_Hora_Criacao** | *data/hora* | Quando o ERP criou |
| **Data_Hora_Confirmacao** | *data/hora, opcional* | Quando o cliente confirmou |
| **Solicitante_Encerramento** | *enumeração {psp_pagador, usuario_pagador, psp_recebedor, usuario_recebedor}, opcional* | Quem cancelou a recorrência (os quatro solicitantes da API do Itaú) |
| **Codigo_Encerramento** | *texto, opcional* | O código bruto do cancelamento ou da rejeição, como o banco mandou (até 4 posições; por exemplo `AP13` a `AP15` na rejeição e `ACCL`, `CPCL`, `DCSD`, `FRUD`, `SLCR` e `SLDB` no cancelamento; o arquivo marca `ERSL` e `PCFD` como obsoletos); a tradução vai ao mapa de ocorrências (R35) |
| **Ispb_Psp_Pagador** | *texto, opcional* | ISPB do banco do cliente (8 posições), que o Itaú entrega na consulta dos dados do pagador; a agência e a conta, do escopo complementar, ficam só no corpo da mensagem (R21) |
| **Motivo_Cancelamento** | *texto, opcional* | Texto livre quando cancelada ou rejeitada |
| **ID_Pix_Recorrencia_Anterior** | *referência (Mov_Pix_Recorrencia), opcional* | A recorrência cancelada que esta substitui. Pela regra geral do convênio da Caixa, **alterar** uma recorrência confirmada (valor, periodicidade, vigência) é **cancelar e criar outra**, que o cliente precisa confirmar de novo; o vínculo guarda a cadeia e impede cobrar nas duas (R82) |

Mov_Pix_Recorrencia_Agendamento

Revisão 56 (documento 250; D-N639 a D-N658): **Pix Automático: cada cobrança da recorrência.** Cada parcela é uma **cobrança** da recorrência, enviada ao banco do cliente entre 2 e 10 dias antes da data. O `txid` identifica a cobrança até a conciliação. **A versão 4 do documento 250 passou o estado para o do Itaú** (criada, ativa, concluída, expirada, rejeitada, cancelada) e tirou daqui a tentativa e o `E2eid`, que agora vivem em `Mov_Pix_Recorrencia_Tentativa` (seção 4.18 do documento 250): a mesma cobrança pode ter até 4 tentativas.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Pix_Agendamento** | *identificador* | --- |
| **ID_Pix_Recorrencia** | *referência (Mov_Pix_Recorrencia)* | A recorrência |
| **ID_Titulo** | *referência (Mov_Titulo), opcional* | O título a receber que esta cobrança quita |
| **Txid** | *texto* | Identificador da cobrança (até 35 posições), usado para cancelar, pedir nova tentativa e conciliar |
| **Data_Prevista_Liquidacao** | *data* | A data da cobrança |
| **Ajuste_Dia_Util** | *booleano, opcional* | {sim, nao}: se a cobrança marcada para um dia que não é útil passa ao dia útil seguinte. No convênio da Caixa o padrão é **sim** e o recebedor pode desligar em cada agendamento (`ajusteDiaUtil` da API do arranjo). Vazio = o padrão do convênio |
| **Valor** | *número* | Valor |
| **Status** | *enumeração {criada, ativa, concluida, expirada, rejeitada, cancelada}* | (os seis estados da cobrança no Itaú) |
| **Solicitante_Encerramento** | *texto, opcional* | Quem cancelou a cobrança, quando cancelada (a lista de solicitantes da cobrança é a mesma da recorrência) |
| **Codigo_Encerramento** | *texto, opcional* | O código bruto do cancelamento ou da rejeição, como o banco mandou (até 4 posições; por exemplo `ACCT`, `BLCK`, `CCLD`, `FAIL`, `OTHR`, `SLBD` e `SLCR` no cancelamento, e 19 códigos na rejeição); a tradução vai ao mapa (R35) |
| **Data_Hora_Status** | *data/hora* | Quando o status mudou pela última vez |

Mov_Pix_Recorrencia_Tentativa

Revisão 56 (documento 250; D-N639 a D-N658): **Pix Automático: cada tentativa de cobrança.** Acréscimo da versão 4 do documento 250, a partir da API completa do Pix Automático do Itaú: a cobrança traz uma **lista de tentativas**, cada uma com tipo, estado, data de liquidação e `endToEndId`. A primeira é a instrução original; a nova tentativa (até 3, em até 7 dias corridos, só com a política `PERMITE_3R_7D`) é um pedido novo sobre a mesma cobrança.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Pix_Tentativa** | *identificador* | --- |
| **ID_Pix_Agendamento** | *referência (Mov_Pix_Recorrencia_Agendamento)* | A cobrança |
| **Numero_Tentativa** | *número* | 1 na instrução original; 2 a 4 nas novas tentativas |
| **Tipo_Tentativa** | *texto* | O código bruto do banco (no Itaú: `AGND`, `NTAG` e `RIFL`; o arquivo não explica os três, Q250-16) |
| **Data_Liquidacao_Prevista** | *data* | A data prevista para esta tentativa |
| **Status** | *enumeração {solicitada, agendada, paga, cancelada, rejeitada, expirada}* | (os seis estados da tentativa no Itaú) |
| **E2eid** | *texto, opcional* | Identificador fim a fim do Pix, quando paga |
| **Codigo_Rejeicao** | *texto, opcional* | O código bruto quando a tentativa é rejeitada; a tradução vai ao mapa (R35) |
| **Data_Hora_Status** | *data/hora* | Quando o status mudou pela última vez |

15.4. Dados do item de remessa que só alguns bancos e produtos usam: tributo e cobrança (documento 250)

Mov_Remessa_Bancaria_Item_Tributo

Revisão 56 (documento 250; D-N639 a D-N658): **Item de pagamento de tributo (guia sem título comum).** Os segmentos de tributo do CNAB 240 (N e O) e os pagamentos de tributo por API pedem dados que o item de remessa não tem. **A estrutura é mínima e provisória:** as posições de cada tributo só foram vistas em parte (seção 3.3 do documento 250) e fecham quando você trouxer o manual do banco.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Remessa_Tributo** | *identificador* | --- |
| **ID_Item_Remessa** | *referência (Mov_Remessa_Bancaria_Item)* | O item de remessa a que pertence |
| **Tipo_Tributo** | *enumeração {gps, darf, darf_simples, gare, fgts, dae, outro_com_codigo_de_barras}* | {gps, darf, darf_simples, gare, fgts, dae, outro_com_codigo_de_barras} |
| **Codigo_Receita** | *texto, opcional* | Código da receita |
| **Tipo_Identificacao_Contribuinte** | *enumeração {cnpj, cpf, pis, cei, numero_beneficio, titulo, debcad, referencia}, opcional* | A lista de identificações vista no layout |
| **Identificacao_Contribuinte** | *texto, opcional* | O número do contribuinte |
| **Periodo_Apuracao** | *texto, opcional* | Competência ou período |
| **Numero_Referencia** | *texto, opcional* | Número de referência da guia |
| **Data_Vencimento_Tributo** | *data, opcional* | Vencimento da guia |
| **Valor_Principal_Tributo** | *número* | Principal |
| **Valor_Multa_Tributo** | *número, opcional* | Acréscimos (2 campos) |
| **Valor_Juros_Tributo** | *número, opcional* | Acréscimos (2 campos) |
| **Subtipo_Gare** | *enumeração {icms, itcmd}, opcional* | Santander: {icms, itcmd}: a GARE tem **dois leiautes** na API do Santander, com campos diferentes (a do ICMS pede inscrição estadual e auto de infração; a do ITCMD, o número da declaração, em `Numero_Referencia`). Só vale com `Tipo_Tributo` = `gare` (R91) |
| **Numero_Divida_Ativa_Ou_Etiqueta** | *texto, opcional* | Santander, GARE: o número da inscrição em dívida ativa ou da etiqueta da guia |
| **Numero_Auto_Infracao_Ou_Parcela** | *texto, opcional* | Santander, GARE do ICMS: o número do AIIM, do DEICMEME ou da parcela (o banco aceita um só, até 9 dígitos) |
| **Valor_Acrescimo_Financeiro_Tributo** | *número, opcional* | Santander, GARE: o acréscimo financeiro, que não é juros nem multa |
| **Valor_Honorarios_Advocaticios_Tributo** | *número, opcional* | Santander, GARE: os honorários advocatícios da guia |
| **Receita_Bruta_Acumulada_Tributo** | *número, opcional* | Bradesco, Multipag, DARF Simples, segmento N3: a receita bruta acumulada que o DARF do Simples pede |
| **Percentual_Receita_Bruta_Tributo** | *número, opcional* | DARF Simples, N3: o percentual sobre a receita bruta |
| **Valor_Atualizacao_Monetaria_Tributo** | *número, opcional* | GPS, segmento N1: a atualização monetária, separada de juros e multa |
| **Observacao_Tributo** | *texto, opcional* | Santander: o texto livre da guia (até 30 posições na GARE) |
| **Valor_Outras_Entidades** | *número, opcional* | Valor de outras entidades (GPS) |
| **Identificador_Fgts** | *texto, opcional* | Identificador do recolhimento do FGTS |

Mov_Remessa_Bancaria_Item_Cobranca

Revisão 56 (documento 250; D-N639 a D-N658): **Dados de cobrança do item: protesto, negativação, descontos, juros, bonificação, validade e pagamento divergente.** Acréscimo da versão 3 do documento 250, ampliado na versão 5 do documento 250 com o que o Bradesco pede (15 campos: negativação, prazo em dias úteis, juros em percentual, descontos 2 e 3, bonificação, pagamento parcial e decurso de prazo) na versão 6 do documento 250 com a validade do Pix no boleto híbrido (1 campo) na versão 7 do documento 250 com o que o BB pede (4 campos: tipo de Pix no boleto, location da recorrência, órgão negativador e pagamento depois do vencimento) e na versão 8 do documento 250 com o que a Caixa pede (3 campos) e com os dados do boleto que o banco devolve (5 campos). O item de cobrança do dicionário tem multa, juros, desconto e abatimento, mas **não tem** os dados que o registro do boleto pede além disso: protesto, negativação, data-limite de pagamento, aceitação de valor divergente e mensagens. A API de boleto do Itaú pede todos; o segmento Y-53 do Banrisul (seção 3.2 do documento 250) traz o pagamento divergente. Uma linha por item de cobrança, no padrão de `Mov_Remessa_Bancaria_Item_Exterior` (o item já tem campos demais para receber mais opcionais). **As instruções de cobrança do Itaú** (uma lista de até **4** códigos na emissão; a consulta de detalhe mostra 3) **saem destes campos**: o driver monta a lista e o banco descarta o excedente.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item_Cobranca** | *identificador* | --- |
| **ID_Item_Remessa** | *referência (Mov_Remessa_Bancaria_Item)* | O item de cobrança a que pertence (um item, no máximo uma linha) |
| **Protestar** | *booleano, opcional* | Se o banco deve protestar o título depois do vencimento; no Itaú, o bloco de protesto só vai quando for sim |
| **Dias_Protesto** | *número, opcional* | Dias depois do vencimento para protestar (no Itaú, de 1 a 99); só quando `Protestar` for sim |
| **Negativar** | *booleano, opcional* | Se o banco deve negativar o pagador; fontes secundárias dizem que o Itaú aceita só um entre protesto e negativação (regra do driver) |
| **Data_Limite_Pagamento** | *data, opcional* | Data depois da qual o boleto não pode mais ser pago (no Itaú, no máximo 10 anos; sem data, vale 10 anos) |
| **Tipo_Recebimento_Divergente** | *enumeração {qualquer_valor, faixa_de_valores, nao_aceita, a_partir_do_minimo}, opcional* | O boleto aceita pagamento de valor diferente do calculado? São os quatro códigos do Itaú |
| **Valor_Minimo_Recebimento** | *número, opcional* | Menor valor aceito, quando o tipo pede |
| **Valor_Maximo_Recebimento** | *número, opcional* | Maior valor aceito, quando o tipo pede |
| **Mensagens_Boleto** | *texto, opcional* | Texto impresso no boleto (segmentos R e S do CNAB; no Itaú, uma lista de mensagens) |
| **Texto_Uso_Beneficiario** | *texto, opcional* | Texto livre do beneficiário, devolvido no retorno (25 posições no Itaú; o `controleParticipante` do Bradesco também tem 25 e o banco não o confere) |
| **Dias_Negativacao** | *número, opcional* | Bradesco: dias para negativar, quando `Negativar` for sim. O Bradesco aceita **um** comando de protesto ou de negativação por título, com prazo mínimo de 3 dias corridos ou 1 dia útil na negativação e de 5 corridos ou 3 úteis no protesto, conforme o contrato |
| **Tipo_Dia_Prazo** | *enumeração {corridos, uteis}, opcional* | Bradesco: {corridos, uteis}, a unidade de `Dias_Protesto` e de `Dias_Negativacao` e, na versão 8 do documento 250 (Caixa), dos dias do desconto por antecipação |
| **Tipo_Juros_Mora** | *enumeração {valor_dia, percentual_mes, isento}, opcional* | Bradesco: {valor_dia, percentual_mes, isento}. O item só tinha o valor por dia (`Valor_Juros_Mora_Dia`). Leitura minha: o segmento P do CNAB 240 também traz o código de juros; conferir no manual de cada banco. Valor ou percentual, **nunca os dois** |
| **Percentual_Juros_Mora_Mes** | *número, opcional* | O percentual ao mês, quando `Tipo_Juros_Mora` for `percentual_mes`. O Bradesco calcula o juro diário como valor do título × percentual mensal ÷ 30 |
| **Tipo_Desconto** | *enumeração {valor, percentual, por_dia_antecipacao}, opcional* | {valor, percentual, por_dia_antecipacao}, vale para os três descontos; `por_dia_antecipacao` é o tipo 3 do BB (versão 7 do documento 250) e, na Caixa (versão 8 do documento 250), vem com `Base_Desconto_Antecipacao`. Valor e percentual nunca vão juntos (regra do Bradesco) |
| **Valor_Desconto_2_Remessa** | *número, opcional* | Bradesco, CNAB 240: segmento R: o segundo desconto. O Bradesco aceita até 3, com datas em sequência e a soma menor que o valor do título |
| **Data_Limite_Desconto_2** | *data, opcional* | Até quando vale o segundo desconto; depois da data do primeiro |
| **Valor_Desconto_3_Remessa** | *número, opcional* | O terceiro desconto |
| **Data_Limite_Desconto_3** | *data, opcional* | Até quando vale o terceiro desconto; depois da data do segundo |
| **Valor_Bonificacao_Dia** | *número, opcional* | Bradesco: a redução **por dia** no valor do título até o vencimento, o inverso dos juros (R$ 1,00 por dia num título emitido 20 dias antes dá R$ 20,00 se pago no primeiro dia). Só uma bonificação por título |
| **Percentual_Bonificacao_Dia** | *número, opcional* | A mesma bonificação em percentual ao dia. Valor e percentual nunca vão juntos |
| **Data_Limite_Bonificacao** | *data, opcional* | Até quando vale a bonificação |
| **Permite_Pagamento_Parcial** | *booleano, opcional* | Bradesco: se o boleto aceita pagamento em partes (sim ou não). Para o Itaú, ver `Tipo_Recebimento_Divergente`; o de-para entre os dois é regra do driver |
| **Quantidade_Pagamentos_Parciais** | *número, opcional* | Quantos pagamentos parciais o banco aceita (até 3 posições), só quando `Permite_Pagamento_Parcial` for sim |
| **Dias_Decurso_Prazo** | *número, opcional* | Bradesco, decurso de prazo: dias depois do vencimento em que o título ainda pode ser pago. É a alternativa **em dias** de `Data_Limite_Pagamento`; só vale se o contrato de cobrança estiver com o indicador correspondente zerado. Versão 12 do documento 250: serve também de **prazo de baixa automática** quando `Instrucao_Baixa_Automatica` for `baixar_apos_dias` (Itaú e Santander); é o dia em que a cobrança **caduca** (R108) |
| **Dias_Validade_Pix_Apos_Vencimento** | *número, opcional* | Bradesco, boleto híbrido com QR Code: quantos dias **depois do vencimento** o QR Code do Pix ainda vale (`validadeAposVencimento`, até 4 posições). É regra do **Pix**, separada de `Data_Limite_Pagamento` e de `Dias_Decurso_Prazo`, que valem para o boleto |
| **Tipo_Pix_Boleto** | *enumeração {sem_pix, qr_dinamico, qr_dinamico_recorrencia_numerado_pelo_banco, qr_dinamico_recorrencia_numerado_pelo_cliente, qr_location_recorrencia}, opcional* | BB: o Pix que o boleto leva: {sem_pix, qr_dinamico, qr_dinamico_recorrencia_numerado_pelo_banco, qr_dinamico_recorrencia_numerado_pelo_cliente, qr_location_recorrencia} (os códigos N, S, A, B e C do `indicadorPix`; um caractere inválido vira N **no banco**, por isso o driver só envia estes cinco). No Itaú e no Bradesco o Pix é **outro produto** (R32 e R50); no BB é um campo do registro e também pode ser gerado ou cancelado depois (R54) |
| **Id_Location_Recorrencia_Pix** | *texto, opcional* | BB: o `idLocationRecorrencia`, a location da recorrência (cobrança com vencimento do Pix), só quando o tipo for `qr_location_recorrencia`; fica ao lado de `Id_Location_Pix` do item de remessa |
| **Orgao_Negativador** | *enumeração {serasa, quod}, opcional* | BB: {serasa, quod}, o órgão da negativação (códigos 10 e 11; o registro lista só o 10, a alteração lista os dois). Só quando `Negativar` for sim |
| **Aceita_Pagamento_Apos_Vencimento** | *enumeração {sim, nao, conforme_convenio}, opcional* | BB: {sim, nao, conforme_convenio}: se o boleto pode ser pago depois do vencimento (`indicadorAceiteTituloVencido`). `nao` = só até o vencimento ou o próximo dia útil; `sim` com `Dias_Decurso_Prazo` define os dias corridos (`numeroDiasLimiteRecebimento`); `conforme_convenio` deixa valer o limite do convênio |
| **Tipo_Carteira_Titulo** | *enumeração {simples, caucionada, cessao, descontada}, opcional* | Caixa: {simples, caucionada, cessao, descontada}: a carteira do **título** no registro por webservice (padrão simples). `cessao` exige convênio com garantia de crédito e `descontada`, o produto contratado. Não é a carteira da conta (`Carteira_Cobranca`), que é o código numérico do CNAB |
| **Base_Desconto_Antecipacao** | *enumeração {valor, percentual}, opcional* | Caixa: {valor, percentual}: com `Tipo_Desconto` = `por_dia_antecipacao`, se o desconto por dia é em reais ou em percentual; os dias, corridos ou úteis, ficam em `Tipo_Dia_Prazo`. A Caixa aceita **um** desconto por dia de antecipação por título, ou até três de data fixa |
| **ID_Participante_Sacador_Avalista** | *referência (Cad_Participante), opcional* | Caixa: referência a `Cad_Participante`. O sacador avalista, no boleto de **terceiro habilitado** e no depósito e aporte (grupo próprio do XML da Caixa); no depósito e aporte os dados são os do pagador e **não mudam depois do registro**. A Caixa exige que o CPF ou CNPJ do pagador seja **diferente** do beneficiário (erro 0090); o ERP confere antes de enviar |
| **Linha_Digitavel_Banco** | *texto, opcional* | A linha digitável **como o banco devolveu** no registro e na alteração (Caixa: só vem quando o título está EM ABERTO). O desenho das versões 3 a 7 **não tinha onde guardar** os dados do boleto que o banco devolve, e o boleto impresso, o e-mail e o portal do cliente precisam deles; leitura minha, a conferir nos arquivos dos outros bancos. O ERP guarda como veio e **não recalcula** |
| **Codigo_Barras_Banco** | *texto, opcional* | O código de barras do boleto, como o banco devolveu (44 posições). Não é o `Codigo_Barras` do item de tributo, que é o do documento a pagar |
| **Url_Boleto_Banco** | *texto, opcional* | O endereço do boleto no banco (Caixa: devolvido no registro). Pode expirar; o ERP não o trata como documento, só como atalho |
| **Pix_Copia_E_Cola_Banco** | *texto, opcional* | O texto do Pix "copia e cola" do boleto híbrido (Caixa: `QRCODE`). Guardado como veio, sem interpretar |
| **Url_Qr_Code_Pix_Banco** | *texto, opcional* | O endereço da imagem do QR Code do Pix (Caixa: `URL_QRCODE`) |
| **Condicao_Emissao_Boleto** | *enumeração {banco, cliente}, opcional* | Bradesco, CNAB 400 e 240: {banco, cliente}: quem emite e imprime o boleto. Emitido pelo banco, ele imprime no processo autoenvelopável e entrega pelos Correios, sem comprovante de recebimento; emitido pelo cliente, o arquivo só registra o título (R105) |
| **ID_Carteira_Cobranca** | *referência (Cad_Conta_Bancaria_Carteira), opcional* | D-N655: a carteira registrada no banco em que o título é cobrado (`Cad_Conta_Bancaria_Carteira`, seção 4.20 do documento 250); vazio usa a carteira padrão da conta. Quem cadastrou carteiras escolhe a carteira por aqui; o `Tipo_Carteira_Titulo` segue como o campo que a Caixa pede no registro |
| **ID_Documento_Boleto_Pdf** | *referência (Cad_Documento), opcional* | D-N655: o **PDF do boleto em A4**, no padrão do banco, guardado como documento (`Cad_Documento`). A Mlegate emite o boleto **sempre em PDF A4**, para todos os bancos, e o envia ao cliente por **e-mail ou WhatsApp**; o PDF é o que o ERP gera no padrão do banco ou o que o banco devolve (Caixa: `Url_Boleto_Banco`), e é o mesmo arquivo que o portal do cliente mostra (R123) |
| **Instrucao_Baixa_Automatica** | *enumeração {sem_instrucao, baixar_apos_dias, baixar_apos_365_dias, padrao_do_banco}, opcional* | {sem_instrucao, baixar_apos_dias, baixar_apos_365_dias, padrao_do_banco}: o que o banco faz com o título vencido e não pago. `baixar_apos_dias` usa `Dias_Decurso_Prazo` (Itaú: código de baixa 1 e prazo de 2 posições; Santander: `writeOffQuantityDays`); `baixar_apos_365_dias` é o código 2 do Itaú; `padrao_do_banco` é o que vale sem instrução (Itaú: **120 dias** depois do vencimento) (R108) |

15.5. Certificados de confiança dos bancos (documento 250)

Cad_Banco_Certificado_Confianca

Revisão 56 (documento 250; D-N639 a D-N658): **Os certificados públicos do banco em que o ERP confia.** Versão 6 do documento 250. O Bradesco publica, no portal, os certificados dos seus servidores (e dos que chamam o ERP no webhook), **renova-os periodicamente** e pede que o cliente adicione o novo como confiável **antes** da troca. Esta tabela guarda **só o que é público** (o certificado do banco, nunca o do ERP, que continua em `Cad_Certificado_Digital`, nem chave privada) e alimenta o aviso de vencimento e a lista de confiança do cliente HTTP do driver. Os sete arquivos recebidos na versão 6 do documento 250 têm validades de 16/01/2027 a 07/10/2027 (seção 3.12.2 do documento 250); os 16 do BB, na versão 7 do documento 250, de 27/12/2026 a 19/10/2027 (seção 3.13.2 do documento 250), e acrescentaram dois campos.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Banco_Certificado_Confianca** | *identificador* | --- |
| **ID_Banco_Driver** | *referência (Cad_Banco_Driver)* | O driver (banco e canal) a que o certificado pertence |
| **Ambiente** | *enumeração {homologacao, sandbox, producao}* | {homologacao, sandbox, producao} |
| **Finalidade** | *enumeração {servidor_api, servidor_token, origem_webhook}* | `servidor_api` é o servidor que o ERP chama; `origem_webhook` é o servidor do banco que chama o ERP (leitura minha, a confirmar na Q250-24: o ERP valida quem chama) |
| **Nome_Servidor** | *texto* | O nome do servidor no certificado (ex.: `openapi.bradesco.com.br`, `boletosliquidados.bradesco.com.br`) |
| **Papel_Na_Cadeia** | *enumeração {servidor, intermediario, raiz}* | O banco entrega servidor, autoridade intermediária e raiz, e a cadeia do webhook de cobrança (ICP-Brasil) difere da das demais (GlobalSign e DigiCert) |
| **Emissor** | *texto* | Quem emitiu o certificado (texto) |
| **Impressao_Digital_Sha256** | *texto* | Impressão do certificado, para o ERP saber que é exatamente o que o banco publicou |
| **Valido_Ate** | *data* | Vencimento do certificado; alimenta o aviso |
| **Dias_Aviso_Antes** | *número, opcional* | Quantos dias antes avisar (padrão sugerido: 60; o primeiro vencimento recebido é 16/01/2027). Mesmo padrão de `Dias_Aviso_Vencimento` do canal |
| **Situacao** | *enumeração {ativo, aguardando_troca, substituido, vencido}* | `aguardando_troca` é o certificado novo já publicado, **confiado antes** da data de troca do banco |
| **ID_Documento_Certificado** | *referência (Cad_Documento), opcional* | O arquivo público do certificado (`Cad_Documento`) |
| **Data_Inicio_Uso_Banco** | *data, opcional* | A data em que o **banco** passa a apresentar este certificado, que **não é** a do início da validade dele: os arquivos do BB vêm em pastas "válido a partir de 26/10" e "até 25/10", e o certificado novo já tinha sido emitido em setembro. É esta data que diz quando o antigo deixa de valer na prática; o ERP confia nos dois até lá (R61) |
| **Origem_Da_Cadeia** | *enumeração {autoridade_publica, pki_do_banco}, opcional* | {autoridade_publica, pki_do_banco}: o BB trocou o certificado do webhook de produção, em 04/11/2026, de uma autoridade pública (GeoTrust e DigiCert) para a **autoridade do próprio banco** (AC Banco do Brasil v3), que não consta das listas de confiança dos sistemas; a de homologação já era assim. A raiz do banco entra **só** na lista de quem chama o webhook, nunca na lista geral (R61) |



16\. Anexo --- Documento 250: boleto com ou sem Pix em parâmetro (entidade nova da revisão 58)

Revisão 58 do dicionário (consolidação de 24/11/2026, «consolidar» de Alberto): 1 entidade nova neste módulo, do documento 250 (versão 33; D-N666): o **parâmetro global** que diz se o boleto novo sai com Pix ou sem Pix (R129). O produto `debito_veicular` entrou também nos campos `Produto` da matriz de capacidades e do canal da conta (D-N675, R137).

16.1. Parâmetro global da cobrança: boleto com ou sem Pix (documento 250)

Cad_Cobranca_Parametro

Revisão 58 (documento 250; D-N666 e D-N675): **O parâmetro global do boleto com ou sem Pix.** Resposta de Alberto à Q250-16 (a): a opção de o boleto aceitar Pix ou não é **do usuário e vale para todos os boletos**; não é escolhida boleto a boleto. Um parâmetro global **com vigência** (a mudança fica registrada), sem empresa nem conta (se um dia a Mlegate quiser por empresa ou por conta, entra um campo opcional, como no parâmetro do vencimento do FGTS). Ligado, todo boleto **novo** sai com Pix (produto `boleto_com_pix` do banco); desligado, sai **sem Pix**; os boletos já registrados não mudam (R129). Se a conta ou o banco não tem o canal do boleto com Pix, o boleto sai sem Pix e o ERP avisa, sem nunca deixar de emitir. Os campos técnicos do item de cobrança (`Tipo_Pix_Boleto`, `Pix_Copia_E_Cola_Banco` e `Url_Qr_Code_Pix_Banco`) são preenchidos pelo motor a partir deste parâmetro e da resposta do banco. Chave de negócio: `Vigencia_Inicio`.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Cobranca_Parametro** | *identificador* | --- |
| **ID_Cobranca_Parametro_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Cobranca_Parametro_Versao). ID_Cobranca_Parametro é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **Boleto_Com_Pix** | *booleano* | Verdadeiro: todo boleto **novo** sai com Pix (o produto `boleto_com_pix` do banco). Falso: sai **sem Pix** (R129). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |
