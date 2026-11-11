# Contabilidade como origem de PIS/Cofins, ISS fixo da SUP, cadastro de modelos, prazos, recibo e hash das escriturações e subvenções — Documento 46

*Desenho das respostas de Alberto de 12/10/2026 aos documentos 35, 36, 38 e 44: registros da EFD-Contribuições que nascem da contabilidade, recolhimento do ISS fixo trimestral das sociedades uniprofissionais, cadastro de modelos de documento fiscal, calendário de prazos de opção, Integra Contador com contingência manual, recibo e hash das escriturações SPED e subvenções para investimento. Nada altera o dicionário.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Oito respostas suas entram aqui (sete pedem desenho e uma confirma o desenho que já existia). Este documento reúne as oito, porque várias se apoiam no mesmo mecanismo: parâmetro com vigência, sem valor fixo no código.

(1) **Contabilidade como origem de base de PIS/Cofins.** Você observou que registros da EFD-Contribuições nascem da contabilidade (aplicações financeiras e outros). O Guia Prático v1.35 confirma: o F100 é o registro das demais receitas e dos créditos sem nota fiscal, e traz `COD_CTA`; o M110 e o M510 ajustam crédito; o Bloco I trabalha por conta contábil. O dicionário já guarda o lançamento, o saldo e o rendimento da aplicação, mas **não liga a conta contábil ao registro fiscal**. O desenho propõe um mapa de conta para papel na EFD, a geração automática com ajuste manual (sua escolha), a rastreabilidade até o lançamento e uma conciliação do período. São 4 entidades novas (seção 3).

(2) **SUP e ISS fixo trimestral (Q-6 do documento 35).** Você respondeu que sim, por tipo de empresa, com a sociedade uniprofissional entrando como tipo. Proponho o **regime de ISS por empresa e município**, com vigência, a tabela de valores por profissional e a apuração trimestral. São 5 entidades novas (seção 4).

(3) **Cadastro de modelos (Q-1 do documento 35).** O COD_MOD da nota de serviço na EFD é 03, mas outros podem surgir. O cadastro de modelos substitui o domínio `modelo_documento_fiscal` e guarda o código de cada obrigação como parâmetro com vigência. São 2 entidades novas (seção 5). **A tabela 4.1.1 que o projeto carregou (versão 7, 39 modelos) não traz o 03 nem um código de NFS-e**; é o caso que o cadastro resolve, mas a fonte do 03 precisa ser conferida.

(4) **Prazos de opção e cancelamento (D-N40).** Você respondeu sim, porque cada decisão influencia o cálculo do imposto e dos créditos. **`Cad_Obrigacao_Acessoria` hoje só tem código, descrição e vigência; não guarda data de prazo.** O dicionário já tem `Cad_Regra_Vencimento` e o documento 43 propõe `Cad_Obrigacao_Prazo_Entrega`; o desenho reaproveita os dois, com 4 alterações, e cria só a situação do prazo por empresa (seção 6). É 1 entidade nova.

(5) **Integra Contador (P-18).** Considerar a contratação, mas o ERP gera relatório de conferência e preenchimento manual quando o serviço estiver fora do ar. Nenhuma entidade nova: 2 campos e uma regra (seção 7).

(6) **Recibo e hash das escriturações SPED (G-11).** Guardar o recibo de envio e o hash para a retificação. `Mov_Escrituracao_Arquivo` (documento 33) já tem hash e recibo; faltam 5 campos para a retificação funcionar com a ECD e a ECF, e nenhuma entidade nova (seção 8). Os blocos X, Y e W da ECF **não** foram respondidos.

(7) **Subvenções para investimento, Lei 14.789/2023 (G-12).** Você respondeu que se aplica à Mlegate. Proponho 2 entidades novas (o ato e a habilitação; a apuração do crédito por período) e o aproveitamento de `Mov_Credito_Fiscal` e do LALUR já existentes (seção 9).

(8) **DES-IF sem API (P-DESIF-3).** Você respondeu que o pacote da Prefeitura não traz API e que o envio é por arquivo. Isso confirma o desenho do documento 39 (gerar, assinar e registrar o protocolo; envio manual no portal) e fecha a pergunta. Nenhuma entidade nova (seção 8.4).

São **14 entidades novas** e 19 alterações em entidades existentes ou propostas, a entrar no recount único da revisão 3. Há **10 decisões, D-N96 a D-N105** (seção 12); sete delas já têm direção sua e pedem só a confirmação do detalhe.

# 2. O que você respondeu

| Data | Pergunta ou tema | Sua resposta | Onde entra |
|---|---|---|---|
| 12/10/2026 | EFD-Contribuições: registros com origem na contabilidade | Aplicações financeiras e outros são base de PIS e Cofins e nascem da contabilidade. Geração automática com ajuste manual. Entram: receitas financeiras, outras receitas e ganhos, créditos sem nota fiscal e ajustes de base | Seção 3 |
| 12/10/2026 | Q-6 (doc 35): SUP e ISS fixo trimestral | Sim, desenhar por tipo de empresa; a SUP entra como tipo. Escolha: regime de ISS por empresa e município | Seção 4 |
| 12/10/2026 | Q-1 (doc 35): COD_MOD da NFTS | O COD_MOD de nota de serviço é 03, mas podem aparecer outros; tem de ser cadastro de modelos, parametrizado pelo tipo de modelo. Escolha: substitui o domínio atual. **O tipo de documento do Reinf (R-2010) ficou sem resposta** | Seção 5 |
| 12/10/2026 | D-N40 (doc 36): prazos em `Cad_Obrigacao_Acessoria` | Sim, guardar, porque cada decisão influencia o cálculo do imposto e dos créditos | Seção 6 |
| 12/10/2026 | P-18 (doc 38): Integra Contador | Considerar a contratação, com relatórios de conferência e preenchimento manual se o serviço estiver fora do ar | Seção 7 |
| 12/10/2026 | G-11 (doc 38): arquivo, recibo e retificação das escriturações SPED; blocos X, Y e W da ECF | Guardar o recibo de envio e salvar o hash para eventual retificação. **Os blocos X, Y e W não foram respondidos** | Seção 8 |
| 12/10/2026 | P-DESIF-3 (doc 38): há webservice ou API da DES-IF? | O pacote da Prefeitura não traz, não existe API; o envio é por arquivo | Seção 8.4 |
| 12/10/2026 | G-12 (doc 38, item 12): subvenções para investimento (Lei 14.789/2023), efeito no LALUR e na ECF | Aplica-se à Mlegate: sim | Seção 9 |

# 3. Contabilidade como origem de base de PIS/Cofins

## 3.1 O que o Guia diz

O Guia (versão 1.35, de 18/06/2021) descreve no F100 as operações que não cabem nos registros próprios dos Blocos A, C, D e F: receitas financeiras, JCP recebido, aluguéis, outras receitas operacionais ou não operacionais sem documento fiscal, despesas de aluguel e de arrendamento mercantil, armazenagem, consórcio, importação por DI e crédito presumido do transporte de carga. No F100, receita com tributação leva `IND_OPER` 1, receita sem incidência ou alíquota zero leva 2, e custo ou despesa com crédito leva 0; só as operações com crédito precisam constar. O `COD_PART` é opcional na receita (o Guia cita as receitas financeiras de várias instituições, que o contribuinte pode consolidar com a descrição no campo 19) e obrigatório no crédito. O `COD_CTA` é obrigatório desde 11/2017, salvo a pessoa jurídica dispensada de escrituração contábil (lucro presumido com livro caixa). O M400/M410 e o M800/M810 consolidam as receitas sem contribuição por natureza da receita **e conta contábil** (a chave do M410 é `NAT_REC` + `COD_CTA` + `DESC_COMPL`). O M110 e o M510 ajustam o crédito (códigos da tabela 4.3.8), e o I200/I300 detalham receita e dedução por conta no Bloco I.

## 3.2 O que o dicionário tem e o que falta

| Peça | Situação | Lacuna |
|---|---|---|
| `Mov_Lancamento`, `Mov_Lote_Lancamento`, `Mov_Saldo_Contabil` | Existem. O lançamento tem conta, débito ou crédito, valor, competência (`ID_Periodo_Referencia`) e tipo (o encerramento é distinguido). O saldo é gravado de novo na reabertura (`Data_Hora_Geracao`) | Nenhuma entidade lê o lançamento para gerar valor fiscal |
| `Mov_Conta_Contabil_Evento` (rendimento de aplicação) e o doc 10, seção 12 | O rendimento vira item de apuração com `Origem_Tipo` = `evento_conta_financeira`, **sempre em regime cumulativo e sem crédito** | A premissa é fixa; o regime da empresa e a vigência não participam |
| `Cad_Conta_Bancaria.ID_Conta_Contabil_Aplicacao` e `ID_Instituicao_Financeira` | Ligam a conta de aplicação à instituição | Servem de base para consolidar por instituição |
| `Mov_Operacao_Fiscal_Diversa` (doc 44, entidade 15) | Proposta como "receita ou custo com crédito **sem nota**", com `Origem_Tipo` e `ID_Lote` | Descreve a operação, mas não diz como ela nasce da contabilidade |
| Motor de Regras com critério `conta_contabil` (doc 44, seção 8) | Proposto | Resolve CST, alíquota, base do crédito e natureza da receita por conta, com vigência e regime |
| `Mov_Apuracao_Pis_Cofins_Ajuste` (doc 44, entidade 27) | Proposta: ajuste de crédito, de base e de contribuição | Sem origem contábil |
| `Mov_Receita_Deducao_Setorial` e `Cad_Conta_Contabil_Receita_Deducao_Efd` (Bloco I) | Onda 2 (D-N89) | Usarão o mesmo mapa de papéis |

## 3.3 Desenho

A regra do dicionário continua: **o tributo não é calculado fora do Motor de Regras.** O mapa de conta diz só *o que a conta é para a EFD* e *como o valor é lido do lançamento*. A tributação (CST, alíquota, base de crédito, natureza da receita) sai do Motor, pelo critério `conta_contabil` combinado com o regime do perfil fiscal, e fica gravada no item de apuração.

### Cad_Conta_Contabil_Papel_Efd (nova, com vigência)

O papel que cada conta contábil analítica tem na EFD-Contribuições.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Conta_Papel_Efd` e `ID_Conta_Papel_Efd_Versao` | identificadores | Convenção da Fase 0 |
| `ID_Conta` | referência (`Cad_Conta_Contabil`), identidade | Conta analítica (a sintética agrupa; o Guia aceita a sintética no `COD_CTA`, mas o valor nasce da analítica) |
| `Papel_Efd` | enumeração {receita_financeira, outra_receita, credito_sem_nota, ajuste_base, ajuste_credito, receita_deducao_setorial}, identidade | As quatro origens que você escolheu mais o Bloco I (onda 2). Uma conta pode ter mais de um papel |
| `ID_Natureza_Operacao_Diversa` | referência (`Cad_Classe_Sistema`, domínio `natureza_operacao_fiscal_diversa`), opcional | Receita financeira, JCP, aluguel, receita não operacional e outras (domínio do doc 44) |
| `Modo_Valor` | enumeração {credito_menos_debito, debito_menos_credito, somente_credito, somente_debito} | Como o valor sai de `Operador_DC` dos lançamentos. Receita costuma ser crédito menos débito; despesa com crédito, o contrário |
| `Agrupar_Por` | enumeração {conta, conta_instituicao_financeira, conta_participante, lancamento} | Granularidade do registro gerado. Aplicação financeira: conta e instituição |
| `ID_Codigo_Ajuste` | referência ao catálogo de códigos de ajuste do documento 43 (tabela 4.3.8 e a de ajuste de base), opcional | Só nos papéis de ajuste |
| `Exige_Participante` | booleano | Verdadeiro em `credito_sem_nota`: o `COD_PART` é obrigatório no F100 de crédito |
| `Permite_Ajuste_Manual` | booleano | Padrão verdadeiro (sua escolha) |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | Vigência |

### Mov_Efd_Geracao_Contabil (nova)

Cada execução da geração para um período, para saber *de que estado da contabilidade* o fiscal nasceu.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Geracao` | identificador | |
| `ID_Periodo_Efd` | referência (`Mov_Efd_Contribuicoes_Periodo`) | Período do doc 44 (D-N83 e D-N94) |
| `Numero_Execucao` | número | Sequência dentro do período |
| `Data_Hora_Geracao` | data/hora | |
| `ID_Usuario` | referência, opcional | Vazio quando automática |
| `Data_Hora_Ultimo_Saldo_Lido` | data/hora | O maior `Data_Hora_Geracao` de `Mov_Saldo_Contabil` que a execução viu; é o que denuncia a reabertura da contabilidade |
| `Quantidade_Operacoes` | número | Registros gerados |
| `Situacao` | enumeração {vigente, substituida, desatualizada, com_erro} | |
| `Observacao` | texto, opcional | |

### Mov_Efd_Origem_Contabil (nova)

A ponte entre o registro fiscal e os lançamentos que o formaram. É o que permite abrir o F100 de aplicação financeira e ver cada lançamento.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Origem_Contabil` | identificador | |
| `ID_Geracao` | referência (`Mov_Efd_Geracao_Contabil`) | |
| `Destino_Tipo` | enumeração {operacao_fiscal_diversa, apuracao_ajuste, receita_deducao_setorial} | |
| `ID_Destino` | referência genérica | O registro fiscal gerado |
| `ID_Lancamento` | referência (`Mov_Lancamento`) | |
| `Valor_Considerado` | número | O valor do lançamento que entrou, com o sinal do papel |

### Mov_Efd_Conciliacao_Contabil (nova)

A conferência de cada conta de receita ou de crédito entre o que a contabilidade registrou e o que a EFD escriturou, gravada no fechamento do período (imutável depois dele, como os outros dados do período fechado, doc 44 seção 9).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Conciliacao` | identificador | |
| `ID_Periodo_Efd` | referência (`Mov_Efd_Contribuicoes_Periodo`) | |
| `ID_Conta` | referência (`Cad_Conta_Contabil`) | |
| `Valor_Contabil` | número | Movimento da conta na competência (lançamentos, sem o encerramento) |
| `Valor_Escriturado_Notas` | número | Itens de nota com essa conta em `ID_Conta_Contabil` (campo do doc 44, seção 7) |
| `Valor_Escriturado_Diversas` | número | Operações diversas e ajustes da conta |
| `Valor_Excluido` | número | Parcela justificada fora da base (exemplo: receita não ligada à atividade, IPI, ICMS-ST) |
| `Valor_Diferenca` | número | Gravado no fechamento, nunca recalculado |
| `Situacao` | enumeração {conciliada, diferenca_justificada, com_diferenca} | |
| `Justificativa` | texto, opcional | Obrigatória em `diferenca_justificada` |
| `ID_Usuario` | referência | |

## 3.4 Fluxo de geração

(1) **Seleção.** Para o período (empresa, SCP, competência), o ERP lê os lançamentos das contas com papel vigente em `Cad_Conta_Contabil_Papel_Efd`, pela competência do lançamento (`ID_Periodo_Referencia`) e **sem** os de encerramento (`ID_Tipo_Lancamento`). O estorno entra pelo próprio débito e crédito.

(2) **Agrupamento.** Segundo `Agrupar_Por`: aplicação financeira sai uma por conta e instituição, descoberta pela `ID_Conta_Contabil_Aplicacao` de `Cad_Conta_Bancaria`; JCP e crédito de fornecedor saem por participante; o que não tem agrupamento sai por lançamento. A instituição vira o `COD_PART` do F100 (o 0150 já existe no dicionário para qualquer participante).

(3) **Tributação.** O Motor de Regras resolve, por conta, regime do perfil fiscal e data: CST de PIS e de Cofins, alíquota (de `Cad_Aliquota`, pela D-N95), base do crédito, natureza da receita e `NAT_BC_CRED`. Nada disso fica no mapa.

(4) **Gravação.** O ERP cria ou atualiza `Mov_Operacao_Fiscal_Diversa` (receita e crédito) e `Mov_Apuracao_Pis_Cofins_Ajuste` (ajustes), e um item de `Mov_Apuracao_Tributo_Item` com `Origem_Tipo` = `operacao_fiscal_diversa`. Cada registro guarda `Valor_Gerado` (o que veio do razão) e, se o contador alterou, o `Valor` final com justificativa e usuário. As linhas de `Mov_Efd_Origem_Contabil` ligam tudo aos lançamentos.

(5) **Regeração.** Rodar de novo no mesmo período cria a execução seguinte, marca a anterior como `substituida` e **preserva os ajustes manuais** pela chave conta + instituição ou participante + CST + natureza. Ajuste cuja chave desapareceu fica pendente de decisão do contador.

(6) **Consolidações.** As receitas com CST 04 a 09 do F100 alimentam o M400/M410 e o M800/M810, que já são agrupamentos (doc 44, seção 5); o `COD_CTA` do M410 e do M810 vem da conta do item.

(7) **Fechamento.** O período congela com a conciliação gravada. Contabilidade reaberta depois **não muda o período congelado**; só a retificadora, pela regra do doc 44.

## 3.5 As quatro origens que você escolheu

| Origem | Papel | Registro | Como nasce |
|---|---|---|---|
| Receitas financeiras | `receita_financeira` | F100 (`IND_OPER` 1 ou 2); M400/M410 e M800/M810 quando sem incidência | Rendimento de aplicação por instituição; juros recebidos; JCP recebido; variação monetária e cambial conforme o critério do perfil (`Criterio_Variacao_Monetaria`, que já existe) |
| Outras receitas e ganhos | `outra_receita` | F100 | Aluguel sem nota, ganho na alienação de ativo, receita não operacional |
| Créditos sem nota fiscal | `credito_sem_nota` | F100 (`IND_OPER` 0) | Despesa ou encargo com direito a crédito que só existe no razão. O fornecedor sai do lote de origem quando há (título a pagar); se não houver, o contador completa no ajuste manual, e o fechamento fica bloqueado enquanto o `COD_PART` estiver vazio |
| Ajustes de base | `ajuste_base` e `ajuste_credito` | M215/M615 e M110/M510 (e o 1050 como agrupamento) | Conta de exclusão ou de estorno com código de ajuste; vai para `Mov_Apuracao_Pis_Cofins_Ajuste` com `Origem_Ajuste` = `contabil` |

O F120 e o F130 (depreciação e amortização) continuam saindo de `Cad_Ativo_Direito_Credito_Pis_Cofins`, porque a base do crédito de bem do ativo está no cadastro do bem, e não numa conta de resultado. O mapa não os substitui; a conciliação da conta de depreciação é que os confere.

## 3.6 O regime não é fixo

O documento 10 (seção 12) parte de que a receita financeira segue **cumulativa e sem crédito** enquanto PIS e Cofins existirem. Isso vale para parte das empresas. Para a que está no regime não cumulativo, a receita financeira tem tratamento próprio, com alíquotas reduzidas fixadas por decreto (Decreto 8.426/2015, a confirmar pelo contador), e o crédito sobre despesa financeira de certos encargos tem regra própria. Pelo critério que você fixou (regra legal é parâmetro, não código), o desenho **tira a premissa do código**: o Motor escolhe o tratamento pelo regime (`Incidencia_Pis_Cofins` do perfil fiscal), pela conta e pela vigência. Os valores entram com `Situacao_Dado` = provisório, até o contador validar (mecanismo do documento 43).

**Consequência para o documento 10:** a seção 12 passa a descrever só o caso do regime e da vigência que ela cita; o rendimento deixa de usar `Origem_Tipo` = `evento_conta_financeira` para PIS e Cofins e passa a `operacao_fiscal_diversa`. O evento continua existindo no Contas a Pagar e Receber e chega ao fiscal pelo lançamento que ele gera (`Mov_Conta_Contabil_Evento.ID_Lote`). Isso evita contar o rendimento duas vezes (uma por evento e outra pela conta). A alteração do texto do documento 10 só entra depois do seu "consolidar" (D-N100).

## 3.7 Reabertura da contabilidade

Se a contabilidade é reaberta depois da geração, `Mov_Saldo_Contabil.Data_Hora_Geracao` fica maior que `Data_Hora_Ultimo_Saldo_Lido` da execução vigente. O ERP então marca a execução como `desatualizada`, avisa o contador e **bloqueia o congelamento do período** até ele regerar ou aceitar a diferença com justificativa. O campo `Situacao_Geracao_Contabil` de `Mov_Efd_Contribuicoes_Periodo` (seção 8) mostra isso na tela do período.

# 4. ISS fixo trimestral da sociedade uniprofissional (SUP)

## 4.1 Fonte

A página da Prefeitura de São Paulo sobre o ISS das SUP (lida em 12/10/2026) diz: a SUP é a sociedade de profissionais da mesma atividade que prestam o serviço pessoalmente e assumem a responsabilidade profissional; o ISS é **trimestral**, com vencimentos em 10/04 (janeiro a março), 10/07, 10/10 e 10/01; o valor depende do **código do serviço, da faixa de receita fixada em lei e da quantidade de profissionais habilitados**, e é reajustado por IPCA (a página remete a uma tabela de valores desde 2004, que não está no projeto); a guia sai no Demonstrativo Unificado do Contribuinte (DUC), sem remessa pelo correio; a quantidade de profissionais se confere e se recalcula no próprio DUC; a declaração **D-SUP** deve ser entregue de 27/07 a 30/12/2026; quem foge do conceito de SUP paga a alíquota do art. 16 sobre a base do art. 14 da Lei 13.701/2003; podem somar-se a TFE e a TRSS. A página não trata de retenção nem de perda do benefício, e o documento 35 (seção da guia de ISS) já registra "sem retenção e sem crédito"; mantenho isso como parâmetro por município, a confirmar com o contador.

## 4.2 Desenho

O tipo de empresa **não é um valor fixo de `Cad_Empresa`**: o regime de ISS pertence a uma empresa *num município*, muda por ato (enquadramento, desenquadramento, exclusão) e tem vigência. Por isso a SUP entra como valor do regime de ISS, e qualquer município usa o mesmo mecanismo por parâmetro, com São Paulo como o primeiro carregado.

### Cad_Empresa_Regime_Iss (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Empresa_Regime_Iss` e `_Versao` | identificadores | |
| `ID_Empresa` | referência (`Cad_Empresa`), identidade | |
| `ID_Municipio` | referência (`Cad_Municipio`), identidade | Onde o ISS é devido |
| `ID_Regime_Iss` | referência (`Cad_Classe_Sistema`, domínio aberto `regime_iss`) | Valores iniciais: normal, fixo_sociedade_profissionais (SUP), estimativa, simples_nacional, mei, isento_ou_imune, outro |
| `ID_Servico_Municipal` | referência (`Cad_Servico_Municipal`, documento 35), opcional | O código que define o valor no regime fixo |
| `Periodicidade_Recolhimento` | enumeração {mensal, trimestral, anual} | Trimestral na SUP de São Paulo |
| `Admite_Retencao_Na_Fonte` | booleano | Falso na SUP de São Paulo, a confirmar |
| `Admite_Credito_Iss` | booleano | Falso na SUP de São Paulo, a confirmar |
| `Ato_Enquadramento` | texto, opcional | Ato ou processo do enquadramento ou desenquadramento |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

Essa entidade é a fonte do **perfil do contribuinte** que o documento 35 já previa em `Cad_Autoridade_Fiscal_Atendimento` (valor `sociedade_uniprofissional`): o perfil de atendimento é derivado dela, e não digitado de novo. É também de onde a emissão da NFS-e tira o regime especial ou o tipo de tributação de cada leiaute, sem digitação.

### Cad_Empresa_Profissional_Habilitado (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Profissional_Habilitado` e `_Versao` | identificadores | |
| `ID_Empresa` | referência (`Cad_Empresa`), identidade | |
| `ID_Participante` | referência (`Cad_Participante`), identidade | O profissional (pessoa física) |
| `ID_Empresa_Socio` | referência (`Cad_Empresa_Socio`), opcional | Quando o profissional é sócio |
| `ID_Conselho` | referência (`Cad_Classe_Sistema`, domínio aberto `conselho_profissional`) | OAB, CRM, CREA, CRC e outros |
| `Registro_Conselho` | código (até 30) | |
| `Presta_Servico_Pessoalmente` | booleano | Requisito do conceito de SUP |
| `ID_Municipio` | referência (`Cad_Municipio`), opcional | Quando a contagem é por município |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | A contagem por trimestre sai das vigências |

### Cad_Iss_Fixo_Tabela (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Iss_Fixo_Tabela` e `_Versao` | identificadores | |
| `ID_Municipio` | referência (`Cad_Municipio`), identidade | |
| `ID_Servico_Municipal` | referência (`Cad_Servico_Municipal`), opcional | Quando o valor depende do código |
| `Faixa_Receita_Inicial`, `Faixa_Receita_Final` | número, opcionais | A faixa fixada em lei |
| `Valor_Por_Profissional` | número | Por período de recolhimento |
| `Periodicidade` | enumeração {mensal, trimestral, anual} | |
| `Indice_Reajuste` | texto, opcional | IPCA, na tabela de São Paulo |
| `Ato_Legal` | texto | Lei 13.701/2003 e o ato do reajuste |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga entra provisória até o contador validar |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

### Mov_Iss_Fixo_Apuracao (nova)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Iss_Fixo_Apuracao` | identificador | |
| `ID_Empresa`, `ID_Municipio` | referências | |
| `Periodo_Inicio`, `Periodo_Fim` | datas | O trimestre |
| `ID_Iss_Fixo_Tabela` | referência (`Cad_Iss_Fixo_Tabela`) | A linha da tabela usada: rastreabilidade |
| `Quantidade_Profissionais` | número | Contagem do trimestre |
| `Valor_Por_Profissional` | número | Gravado, nunca recalculado |
| `Valor_Devido` | número | |
| `Data_Vencimento` | data | Vem do calendário de prazos (seção 6) |
| `Situacao` | enumeração {calculada, guia_emitida, paga, retificada, cancelada} | |
| `Numero_Guia` | código, opcional | O DUC |
| `ID_Titulo` | referência ao título a pagar, opcional | Liga ao Contas a Pagar |
| `Observacao` | texto, opcional | |

### Mov_Iss_Fixo_Apuracao_Profissional (nova)

Os profissionais que entraram na contagem de cada trimestre: `ID_Iss_Fixo_Apuracao`, `ID_Profissional_Habilitado` e `Valor`. Serve à conferência no DUC (o "Detalhar").

## 4.3 Regras

O ISS fixo **não entra** na apuração por nota: a SUP emite a NFS-e sem ISS calculado, e a obrigação nasce do trimestre. Por isso a NFS-e consulta `Cad_Empresa_Regime_Iss` na data da prestação e escolhe o tratamento. O **vencimento** e a janela da **D-SUP** vêm de `Cad_Obrigacao_Prazo_Entrega` (seção 6). A **perda do enquadramento** é uma nova linha de vigência em `Cad_Empresa_Regime_Iss` (regime normal) e dispara alerta, porque passa a valer a alíquota do art. 16 sobre a base do art. 14 da Lei 13.701/2003, parâmetros que entram como o resto dos tributos municipais (D-N19). A TFE e a TRSS ficam fora deste desenho (pendência P46-04).

# 5. Cadastro de modelos de documento fiscal

## 5.1 Situação hoje

O modelo do documento é o domínio `modelo_documento_fiscal` de `Cad_Classe_Sistema`. Dois campos do dicionário apontam para ele (`Mov_Nota_Fiscal_Entrada.ID_Modelo_Documento` e `Mov_Nota_Fiscal_Saida.ID_Modelo_Documento`) e as propostas dos documentos 33 e 42 repetem o apontamento em nove e três linhas (séries, atendimento, leiaute, regra, documento fiscal e outras). O documento 43 carrega o domínio com a tabela 4.1.1, e o documento 44 acrescenta o 98 e o 99 só para F500, F550 e 1900.

## 5.2 Desenho

Seguindo a sua resposta, o modelo passa a ser **entidade própria**, e o código de cada obrigação deixa de ser o código do modelo: é **parâmetro** do modelo ou do *tipo* de modelo, com vigência.

### Cad_Modelo_Documento_Fiscal (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Modelo_Documento` e `_Versao` | identificadores | |
| `Codigo_Interno` | código (até 20), identidade | Estável no ERP; não depende de nenhuma obrigação |
| `Descricao` | texto | |
| `ID_Tipo_Modelo` | referência (`Cad_Classe_Sistema`, domínio aberto `tipo_modelo_documento`) | nota de mercadoria, nota de serviço, transporte, comunicação, energia, água e gás, cupom fiscal, passagem, outro |
| `Eletronico` | booleano | |
| `Possui_Motor_Emissao` | booleano | Verdadeiro nos modelos que o ERP emite (55, 65, 57, 58 e a NFS-e); o 75 (NFAg) é **falso** e o 62 (NFCom) **permanece verdadeiro por reserva**, porque a NFCom e a NFAg são só de entrada (D-N141, documento 60); a diferença entre NF-e e NFC-e continua no motor de emissão (D-N23) |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

### Cad_Modelo_Documento_Fiscal_Codigo (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Modelo_Codigo` e `_Versao` | identificadores | |
| `ID_Modelo_Documento` | referência (`Cad_Modelo_Documento_Fiscal`), opcional | Código específico de um modelo |
| `ID_Tipo_Modelo` | referência (`Cad_Classe_Sistema`, domínio `tipo_modelo_documento`), opcional | Código padrão de todo o tipo. **Um dos dois é obrigatório** (a regra é a do Motor: o modelo vence o tipo) |
| `ID_Obrigacao` | referência (`Cad_Obrigacao_Acessoria`) | EFD-Contribuições, EFD ICMS/IPI, Reinf, DIMOB e outras |
| `Campo_Destino` | código (até 40) | `COD_MOD` na EFD; o tipo de documento no Reinf (R-2010) |
| `Registros_Aplicaveis` | texto, opcional | F500, F550 e 1900, por exemplo |
| `Codigo` | código (até 10) | O valor do arquivo |
| `Fonte` | texto | Tabela e versão, ou "informado por Alberto em 12/10/2026" |
| `Situacao_Dado` | enumeração {provisorio, validado} | |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

Assim, "o 03 da nota de serviço" é **uma linha**: `Campo_Destino` = COD_MOD, `ID_Tipo_Modelo` = nota de serviço, `Codigo` = 03, `Fonte` = sua resposta, `Situacao_Dado` = provisório. Se a RFB trocar o código ou criar outro, é linha nova com vigência. O tipo de documento do Reinf (R-2010) é outra linha, **ainda sem valor** (Q-1, segunda metade, sem resposta): o campo fica vazio e o evento não é gerado sem ele.

## 5.3 O que muda nas outras propostas

Todos os `ID_Modelo_Documento` que apontavam para `Cad_Classe_Sistema` (domínio `modelo_documento_fiscal`) passam a apontar para `Cad_Modelo_Documento_Fiscal`: os dois campos já existentes no dicionário, os nove dos documentos 33, os três do documento 42 e os que os documentos 40, 41, 43 e 44 repetem por nome. O domínio `modelo_documento_fiscal` deixa de existir (o total de domínios do documento 33 cai de 121 para 120, a recontar). A carga do documento 43 passa a ser: 39 modelos para `Cad_Modelo_Documento_Fiscal` e uma linha de `COD_MOD` por modelo em `Cad_Modelo_Documento_Fiscal_Codigo`.

## 5.4 O 03 e a fonte

A tabela 4.1.1 do projeto (`GLOBAL_MODELOS`, versão 7) tem 39 modelos e **não tem 03 nem NFS-e**. O documento 44 cita 98 (NFS-e municipal) e 99 (outros documentos) para F500, F550 e 1900. Registro o 03 como **informado por você**, provisório, e abro a pendência P46-01: qual tabela ou registro usa o 03, e se o 98 do documento 44 vale para os registros que o 03 não cobre.

# 6. Calendário de prazos (D-N40)

## 6.1 O que já existe e o que falta

Conferi o dicionário e o documento 43 antes de desenhar, e o desenho **reaproveita** o que já há:

| Peça | Situação | Serve para |
|---|---|---|
| `Cad_Obrigacao_Acessoria` | No dicionário: só `Codigo`, `Descricao` e vigência. **Não tem data** | A obrigação em si. Cada opção, cancelamento e recolhimento vira uma linha (por exemplo ISS_FIXO_SUP, D_SUP, OPCAO_REGIME_REGULAR_IBS_CBS, CANCELAMENTO_REGIME_REGULAR, OPCAO_COOPERATIVA, HABILITACAO_SUBVENCAO), com vigência. É onde você pediu para guardar |
| `Cad_Regra_Vencimento` | No dicionário: regra de data com `Finalidade` {pagamento, entrega_declaracao}, referência (fim do mês, do trimestre, do decêndio...), meses de deslocamento, dia fixo, mês fixo, dia útil e tratamento de dia não útil | Prazos que seguem uma regra: o ISS fixo da SUP (dia 10 depois do fim do trimestre) é uma linha desta |
| `Cad_Obrigacao_Prazo_Entrega` | Proposta do documento 43 (D-N77, respondida "como recomendado"): data limite publicada por obrigação e competência, que vale mais que a regra | Prazos de data fixa: a janela de opção de 01/09 a 30/09/2026 e o fim de 31/10/2026 das cooperativas |
| `Mov_Obrigacao_Prazo_Empresa` | **Não existe** | A situação do prazo para cada empresa, que acende e apaga o alerta e liga o prazo à decisão tomada |

A recomendação do documento 36 ("sem entidade nova") não funcionava pelo motivo acima, e uma entidade nova só para prazos **repetiria** `Cad_Regra_Vencimento` e `Cad_Obrigacao_Prazo_Entrega`. Por isso a proposta tem **uma entidade nova** e quatro alterações.

## 6.2 Alterações

| Entidade | Alteração | Motivo |
|---|---|---|
| `Cad_Regra_Vencimento` | `Finalidade` ganha `opcao` e `cancelamento_opcao`; `Origem_Declaracao` ganha `iss_fixo_sociedade_profissionais`, `regime_ibs_cbs_simples`, `cooperativa_regime_especifico` e `subvencao_investimento`; campo novo `Dias_Antecedencia_Alerta` (número, opcional) | Prazo de opção e de recolhimento da SUP por regra, com aviso |
| `Cad_Obrigacao_Prazo_Entrega` (doc 43) | `Tipo_Prazo` {entrega, opcao, cancelamento_opcao, habilitacao, outro}, entrando na identidade; `Data_Inicio_Janela` (data, opcional); `Pode_Ser_Prorrogado` (booleano); `Dias_Antecedencia_Alerta` (número, opcional) | Janela de opção (início e fim) e prazo que o órgão pode adiar (cancelamento em 30/11) |
| `Cad_Obrigacao_Acessoria` | Sem campo novo; linhas novas de carga (lista acima) | Guardar as obrigações |
| Domínio `perfil_prazo` | Novo, em `Cad_Classe_Sistema` | Regime, tipo de empresa ou UF a que o prazo se aplica |

### Mov_Obrigacao_Prazo_Empresa (nova)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Prazo_Empresa` | identificador | |
| `ID_Obrigacao` | referência (`Cad_Obrigacao_Acessoria`) | |
| `Origem_Prazo_Tipo` e `ID_Origem_Prazo` | enumeração {regra_vencimento, prazo_entrega} e referência genérica | De onde vem a data: `Cad_Regra_Vencimento` ou `Cad_Obrigacao_Prazo_Entrega` |
| `ID_Empresa` | referência (`Cad_Empresa`) | |
| `ID_Perfil_Aplicavel` | referência (`Cad_Classe_Sistema`, domínio aberto `perfil_prazo`), opcional | Regime, tipo de empresa ou UF; decide a quem o prazo vale |
| `Competencia` | competência, opcional | |
| `Data_Limite` | data | Calculada na criação e gravada |
| `Situacao` | enumeração {pendente, cumprido, perdido, dispensado, nao_aplicavel} | |
| `Decisao` | enumeração {optou, nao_optou, cancelou, manteve, nao_se_aplica}, opcional | Para prazos de opção |
| `Origem_Decisao_Tipo` e `ID_Origem_Decisao` | enumeração e referência genérica, opcionais | O registro que guarda a decisão com vigência: `Cad_Participante_Regime_Ibs_Cbs`, `Cad_Empresa_Regime_Iss`, a opção da cooperativa |
| `ID_Comprovante` | referência (`Cad_Documento`), opcional | Recibo ou comprovante |
| `Data_Cumprimento` | data, opcional | |
| `ID_Usuario` | referência, opcional | |

**O cálculo lê a decisão, não o prazo.** O imposto e o crédito consultam o registro com vigência que a decisão criou (por exemplo, `Cad_Participante_Regime_Ibs_Cbs` para o regime regular de IBS e CBS no Simples). O prazo só garante que a decisão seja tomada; a janela que fecha sem decisão vira `perdido`, e o cálculo segue o regime padrão, com a perda registrada. O alerta é gerado pelo aplicativo a partir de `Mov_Obrigacao_Prazo_Empresa` (não há motor de alertas no dicionário; os tipos de notificação existentes são de e-mail do participante).

## 6.3 Carga inicial

| Obrigação | Prazo | Onde fica | Situação em 12/10/2026 |
|---|---|---|---|
| Opção pelo Simples e pelo regime regular de IBS e CBS (1º semestre de 2027) | 01/09 a 30/09/2026 | `Cad_Obrigacao_Prazo_Entrega`, tipo opcao | **Fechada** |
| Cancelamento do regime regular de IBS e CBS no Simples (1º semestre de 2027) | 02/11 a 30/11/2026; pode ser prorrogado | `Cad_Obrigacao_Prazo_Entrega`, tipo cancelamento_opcao | Abre no início de novembro |
| Opção pelo regime regular de IBS e CBS (2º semestre de 2027) | 01/03 a 31/03/2027, cancelável até 31/05 | `Cad_Obrigacao_Prazo_Entrega`, dois prazos | Futura |
| Opção das cooperativas (regime específico de IBS e CBS) | 01/09 a 31/10 do ano anterior; para 2027, **31/10/2026** | `Cad_Obrigacao_Prazo_Entrega`, tipo opcao | **Aberta**: 19 dias |
| ISS fixo da SUP, São Paulo | 10/04, 10/07, 10/10 e 10/01 | `Cad_Regra_Vencimento`: fim do trimestre, 1 mês, dia fixo 10 | Próximo: 10/01/2027 (o de 10/10 já passou) |
| D-SUP, São Paulo | 27/07 a 30/12/2026 | `Cad_Obrigacao_Prazo_Entrega`, tipo entrega | **Aberta** |

As datas vêm das fontes oficiais lidas (documentos 35 e 36 e a página da SUP). As do 2º semestre dependem de publicação da CGSN e entram com `Pode_Ser_Prorrogado` verdadeiro. Os prazos são provisórios até o contador validar (`Situacao_Dado`, como o resto do documento 43).

# 7. Integra Contador (P-18)

A configuração por empresa já existe no documento 33 (`Cad_Integra_Contador_Configuracao`), e a empresa sem ela usa o portal. Você decidiu **considerar a contratação e manter sempre a saída manual**. O desenho:

(1) **Contratação.** Continua prevista, por empresa, pela configuração do documento 33. O que falta para o desenho técnico do canal são as páginas do catálogo do Serpro (encerrar apuração do MIT, transmitir declaração, consultar XML); o manual do PGDAS-D não o menciona. Pendência P46-05, com o material faltante.

(2) **Relatório de conferência e de preenchimento.** Para todo serviço que o Integra Contador cobre (PGDAS-D, DAS, DEFIS, DASN-SIMEI, MIT e DCTFWeb), o ERP gera **antes do envio** um relatório com os valores a conferir e, **na falha do canal**, um relatório na ordem dos campos do portal, para digitação. O arquivo é gravado em `Cad_Documento` e ligado à tentativa por `ID_Documento_Envio`, que já existe em `Mov_Simples_Transmissao`.

(3) **Contingência.** Após o limite de tentativas (parâmetro) com `erro_comunicacao`, a tentativa passa a `aguardando_manual`; o usuário digita no portal e registra o recibo (situação `registrada_manual`, que já existe). Dois campos entram: `Motivo_Canal_Manual` {sem_contrato, fora_do_ar, servico_indisponivel_para_a_empresa} em `Mov_Simples_Transmissao` e a situação nova `aguardando_manual`. O MIT e o DCTFWeb já têm entidades próprias de transmissão (documento 15); o mesmo par de campos vale para elas.

(4) **Prazo.** Quando o canal cai perto do vencimento, o alerta de `Mov_Obrigacao_Prazo_Empresa` mostra o prazo e a contingência.

# 8. Recibo e hash das escriturações SPED (G-11)

## 8.1 O que o documento 33 já tem

`Mov_Escrituracao_Arquivo` guarda, para EFD ICMS/IPI, EFD-Contribuições, ECD, ECF, DIMOB e DeSTDA: período, finalidade (original ou substituta), versão do leiaute, arquivo (`ID_Documento_Arquivo`), `Hash`, resultado do validador, `Numero_Recibo`, data e hora da transmissão, `ID_Arquivo_Substituido`, certificado e status. Ou seja, **o recibo e o hash já têm lugar**. Sua resposta confirma que ficam guardados e que o hash serve à retificação.

## 8.2 O que falta para a retificação funcionar

Na retificação da ECD e da ECF, o programa validador pede o recibo (e, no arquivo, o hash) da escrituração anterior. O ERP deve preencher isso sozinho, sem o usuário procurar o recibo antigo. Cinco campos entram em `Mov_Escrituracao_Arquivo`:

| Campo | Tipo | Descrição |
|---|---|---|
| `Hash_Escrituracao` | código (até 64), opcional | O hash que consta do recibo da Receita para a escrituração aceita, distinto do `Hash` do arquivo gerado (cópia do conteúdo no ERP, para detectar alteração). A retificadora usa este |
| `ID_Documento_Recibo` | referência (`Cad_Documento`), opcional | O recibo de entrega em PDF ou XML, como veio da Receita |
| `Data_Hora_Recibo` | data/hora, opcional | Quando a Receita aceitou |
| `Numero_Recibo_Anterior` | código, opcional | Cópia do recibo do arquivo substituído, gravada na criação da retificadora (evita ler o arquivo anterior toda vez) |
| `Hash_Escrituracao_Anterior` | código (até 64), opcional | Idem para o hash |

**Regras.** (a) Um arquivo `transmitido` sem recibo fica `pendente_recibo` e **não pode ser substituído**. (b) A retificadora nasce com `ID_Arquivo_Substituido`, `Numero_Recibo_Anterior` e `Hash_Escrituracao_Anterior` copiados do arquivo aceito mais recente da mesma obrigação, empresa e período. (c) Hash e recibo, depois de gravados, são imutáveis (como o resto do período fechado). (d) Para a DIMOB, o motivo "cancelamento" já previsto no documento 33 continua valendo.

## 8.3 Blocos X, Y e W da ECF

Sem resposta. O documento 32 anotou: Y600 existe no dicionário; os blocos X (informações econômicas e participações no exterior), Y (outras informações) e W (país a país) dependem do perfil da empresa e do leiaute da ECF, e a conferência do perfil de ECF continua em aberto (G-11, segunda metade). Fica como pendência P46-09 e **não entra na revisão 3** sem a sua decisão.

## 8.4 DES-IF: envio só por arquivo (P-DESIF-3)

O canal da DES-IF é **o arquivo**: o ERP gera o arquivo no modelo nacional, assina (p7s), o usuário o envia no portal da Prefeitura e o ERP registra o protocolo e o recibo em `Mov_Escrituracao_Arquivo`. É o que o documento 39 já previa como padrão; agora é decisão sua. Consequências: (a) não há `Cad_Autoridade_Fiscal_Servico` de webservice para a DES-IF, só o endereço do portal como informação; (b) as tentativas de envio não existem, só o registro manual do protocolo (`Status` do arquivo, mais os campos da seção 8.2); (c) se a Prefeitura publicar uma API depois, ela entra como linha de `Cad_Autoridade_Fiscal_Servico`, sem entidade nova. Os campos de recibo e de hash da seção 8.2 valem também para a DES-IF e para a DeSTDA.

# 9. Subvenções para investimento (Lei 14.789/2023) — G-12

## 9.1 O que a fonte diz

Uma fonte secundária lida em 12/10/2026 (Econet Editora, sobre a habilitação) diz: a Lei 14.789/2023 deixou de excluir as subvenções para investimento da incidência de IRPJ, CSLL, PIS e Cofins a partir de 2024, e criou o **crédito fiscal** para compensar em parte; só usa o crédito a pessoa jurídica do **lucro real**, **habilitada** pela Receita Federal (IN RFB nº 2.170, de 02/01/2024, **a conferir; a fonte hesita entre 2023 e 2024**); a alíquota é de 25%; a base são as receitas de subvenção ligadas à implantação ou à expansão do empreendimento, **reconhecidas depois do protocolo do pedido de habilitação**, e só entram as relativas a depreciação, amortização, exaustão ou locação e arrendamento de bens de capital do projeto já computadas na base do IRPJ e da CSLL; os requisitos são subvenção concedida por ente federativo, ato concessivo anterior à implantação ou à expansão e ato com condições e contrapartidas expressas; a habilitação é feita no e-CAC, com cópia do ato e adesão ao Domicílio Tributário Econômico, e exige regularidade fiscal federal; **o crédito deve aparecer na ECF**. O texto não trata de prazos, compensação, ressarcimento, reserva de incentivos nem LALUR. Essas lacunas viram parâmetro e pendência (P46-10 e P46-11), e não valor fixo.

## 9.2 O que o dicionário já tem

O LALUR (`Cad_Lalur_Tabela_Dinamica`, `Mov_Lalur_Lancamento_Parte_A`, `Cad_Lalur_Conta_Parte_B` e `Mov_Lalur_Parte_B_Movimento`) já recebe adição, exclusão e conta da parte B por tabela parametrizada. `Mov_Credito_Fiscal` e `Mov_Credito_Fiscal_Aplicacao` já guardam crédito, status (escriturado, confirmado, glosado) e o uso por compensação (`ID_Perdcomp`). O que falta é **o ato concessivo e a habilitação** e a **apuração do crédito por período**.

## 9.3 Desenho

### Cad_Subvencao_Investimento (nova, com vigência)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Subvencao` e `ID_Subvencao_Versao` | identificadores | |
| `ID_Empresa` | referência (`Cad_Empresa`), identidade | |
| `ID_Participante_Concedente` | referência (`Cad_Participante`) | O ente federativo |
| `Numero_Ato_Concessivo` | código (até 60) | |
| `Data_Ato_Concessivo` | data | Deve ser anterior à implantação ou à expansão |
| `ID_Documento_Ato` | referência (`Cad_Documento`) | Cópia do ato |
| `Descricao_Empreendimento` | texto | |
| `ID_Dimensao_Valor_Projeto` | referência (`Cad_Dimensao_Contabil_Valor`), opcional | Liga ao projeto ou centro de custo que recebe a subvenção (dimensão contábil) |
| `Contrapartidas` | texto | Condições do ato |
| `Data_Protocolo_Habilitacao` | data, opcional | A base só conta receita reconhecida depois dela |
| `Numero_Habilitacao` | código, opcional | |
| `Situacao_Habilitacao` | enumeração {em_preparo, protocolada, deferida, indeferida, cancelada} | |
| `Percentual_Credito` | referência (`Cad_Aliquota`), opcional | A alíquota do crédito como parâmetro com vigência (25% pela fonte) |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

### Mov_Subvencao_Investimento_Periodo (nova)

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Subvencao_Periodo` | identificador | |
| `ID_Subvencao` | referência (`Cad_Subvencao_Investimento`) | |
| `ID_Apuracao_Irpj` | referência (`Mov_Apuracao_Irpj_Csll`) | O período do lucro real |
| `Receita_Subvencao_Reconhecida` | número | Total reconhecido no período |
| `Receita_Subvencao_Elegivel` | número | Parte ligada a depreciação, amortização, exaustão ou locação do bem do projeto e já computada na base |
| `Base_Credito` | número | Gravado, nunca recalculado |
| `Percentual_Aplicado` | número | |
| `Valor_Credito` | número | |
| `ID_Credito` | referência (`Mov_Credito_Fiscal`), opcional | O crédito gerado; a compensação segue por `Mov_Credito_Fiscal_Aplicacao` |
| `ID_Lalur_Lancamento` | referência (`Mov_Lalur_Lancamento_Parte_A`), opcional | A exclusão ou adição correspondente |
| `ID_Lancamento` | referência (`Mov_Lancamento`), opcional | O lançamento contábil da receita |
| `Situacao` | enumeração {calculada, confirmada, glosada} | |
| `Observacao` | texto, opcional | |

## 9.4 Regras

(1) **Só lucro real.** A subvenção só gera crédito se `Regime_Aplicado` da apuração for `lucro_real` e a habilitação estiver `deferida`; sem isso o ERP calcula o valor mas não o confirma.

(2) **Antes do protocolo, nada.** Receita reconhecida **antes** de `Data_Protocolo_Habilitacao` não entra na base.

(3) **Crédito pelo que já existe.** O crédito vira linha de `Mov_Credito_Fiscal` (com `Origem` nova `subvencao_investimento`, `ID_Imposto` = IRPJ) e a utilização por compensação usa `Mov_Credito_Fiscal_Aplicacao` e `Mov_Perdcomp`, já existentes. As regras de prazo, de ressarcimento e de correção ficam como parâmetro com vigência, até o contador confirmar.

(4) **LALUR.** As linhas da parte A que a subvenção exige (exclusão ou adição, e a reserva) entram como linhas de `Cad_Lalur_Tabela_Dinamica`, carregadas pelo contador; o ERP não fixa o código do registro da ECF.

(5) **ECF.** O crédito sai na ECF a partir de `Mov_Subvencao_Investimento_Periodo`; o registro e o bloco entram pela conferência do perfil de ECF (P46-09), sem desenho de arquivo agora.

(6) **Prazo e alerta.** O prazo do pedido de habilitação, se houver, entra em `Cad_Obrigacao_Prazo_Entrega` (seção 6), como o resto dos prazos de opção.

# 10. Alterações em entidades existentes e em propostas

| Entidade | Alteração | Motivo | Seção |
|---|---|---|---|
| `Mov_Operacao_Fiscal_Diversa` (doc 44) | `Origem_Operacao` {manual, contabil_automatica, contabil_ajustada, importacao}; `ID_Conta_Contabil`; `ID_Instituicao_Financeira` (opcional); `Valor_Gerado`; `Justificativa_Ajuste`; `ID_Usuario_Ajuste` | Geração pelo razão com ajuste manual | 3.3 |
| `Mov_Apuracao_Tributo_Item` | `Origem_Tipo` ganha `operacao_fiscal_diversa` (se ainda não estiver nos seis valores do doc 44); `evento_conta_financeira` deixa de ser usado para PIS e Cofins | Evitar contar duas vezes (D-N100) | 3.6 |
| `Mov_Apuracao_Pis_Cofins_Ajuste` (doc 44) | `Origem_Ajuste` {manual, contabil} | Ajuste nascido de conta | 3.5 |
| `Mov_Efd_Contribuicoes_Periodo` (doc 44) | `Situacao_Geracao_Contabil` {atualizada, desatualizada, nao_aplicavel} | Reabertura da contabilidade | 3.7 |
| `Mov_Nota_Fiscal_Entrada` e `Mov_Nota_Fiscal_Saida` | `ID_Modelo_Documento` passa a apontar para `Cad_Modelo_Documento_Fiscal` | Cadastro de modelos | 5.3 |
| Entidades dos documentos 33, 40, 41, 42, 43 e 44 | Mesmo apontamento, onde citam o modelo | Cadastro de modelos | 5.3 |
| `Cad_Autoridade_Fiscal_Atendimento` (doc 35) | Perfil `sociedade_uniprofissional` passa a ser derivado de `Cad_Empresa_Regime_Iss` | Fonte única | 4.2 |
| `Mov_Simples_Transmissao` (doc 33) | `Motivo_Canal_Manual`; situação `aguardando_manual` | Contingência manual | 7 |
| MIT e DCTFWeb (transmissão, doc 15) | Mesmos dois campos | Contingência manual | 7 |
| Domínio `modelo_documento_fiscal` | Sai de `Cad_Classe_Sistema` | Cadastro de modelos | 5.3 |
| Domínios novos | `regime_iss`, `conselho_profissional`, `tipo_modelo_documento`, `perfil_prazo` | | 4, 5, 6 |
| `Mov_Escrituracao_Arquivo` (doc 33) | `Hash_Escrituracao`, `ID_Documento_Recibo`, `Data_Hora_Recibo`, `Numero_Recibo_Anterior`, `Hash_Escrituracao_Anterior`; situação `pendente_recibo` | Retificação com recibo e hash | 8.2 |
| `Mov_Credito_Fiscal` | `Origem` ganha `subvencao_investimento` (hoje {apuracao_automatica, cadastro_manual}) | Crédito da Lei 14.789 | 9.4 |
| `Cad_Lalur_Tabela_Dinamica` | Linhas novas de carga (subvenção), sem campo novo | LALUR da subvenção | 9.4 |
| `Mov_Perdcomp` | Sem alteração; recebe a compensação do novo crédito | | 9.4 |
| `Cad_Regra_Vencimento` | `Finalidade` {opcao, cancelamento_opcao}, `Origem_Declaracao` com 4 valores novos e `Dias_Antecedencia_Alerta` | Prazos de opção e ISS fixo da SUP | 6.2 |
| `Cad_Obrigacao_Prazo_Entrega` (doc 43) | `Tipo_Prazo` (na identidade), `Data_Inicio_Janela`, `Pode_Ser_Prorrogado`, `Dias_Antecedencia_Alerta`; também recebe o prazo de habilitação da subvenção, se houver | Janelas de opção | 6.2 e 9.4 |
| `Cad_Obrigacao_Acessoria` | Sem campo novo; linhas novas de carga | Guardar as obrigações (D-N40) | 6.2 |
| DES-IF (doc 39) | Sem alteração: a pergunta P-DESIF-3 fecha com "não há API" | Seção 8.4 | 8.4 |
| Documento 10, seção 12 | Reescrever depois do "consolidar" (regime e vigência no lugar da premissa fixa) | Seção 3.6 | 3.6 |

# 11. Dúvidas e dependências

| Nº | Dúvida | Quem confirma | Se não responder |
|---|---|---|---|
| P46-01 | Qual tabela ou registro usa o COD_MOD 03 para nota de serviço? O 98 (NFS-e municipal) do documento 44 continua valendo para F500, F550 e 1900? | Alberto ou contador | O 03 entra provisório, como informado; o 98 fica como está |
| P46-02 | Tipo de documento do Reinf (R-2010) da NFTS e da NFS-e | Alberto ou contador | Linha de parâmetro vazia; o evento não é gerado |
| P46-03 | Tratamento de PIS e Cofins da receita financeira por regime (cumulativo e não cumulativo) e crédito sobre despesa financeira | Contador | Parâmetros provisórios; nada é fechado antes da validação |
| P46-04 | TFE e TRSS da SUP entram no recolhimento? | Contador ou Prefeitura | Fora do desenho |
| P46-05 | Páginas do catálogo do Integra Contador (MIT, transmitir declaração, consultar XML) | Alberto | Só o relatório de conferência e a saída manual |
| P46-06 | Tabela de valores do ISS fixo da SUP (São Paulo, desde 2004, reajustada por IPCA) | Alberto | Sem carga; entra quando houver a tabela |
| P46-07 | O crédito sem nota precisa do fornecedor: de onde vem quando o lote não tem título? | Contador | Preenchimento manual obrigatório no ajuste |
| P46-08 | Retenção e crédito de ISS na SUP em outros municípios | Contador | Parâmetro falso por padrão, por município |
| P46-09 | Blocos X, Y e W da ECF: quais o perfil da Mlegate e dos clientes exige (leiaute 12.1.0 a conferir)? | Alberto e contador | Fora da revisão 3 |
| P46-10 | Subvenção: prazo de habilitação, de utilização, regras de compensação e de ressarcimento, e a IN RFB que vale (2.170/2023 ou 2024) | Contador | Parâmetros vazios; o crédito é calculado e não confirmado |
| P46-11 | Subvenção: quais linhas do LALUR e qual registro da ECF recebem a exclusão, a reserva e o crédito | Contador | Sem carga; o contador cadastra as linhas |
| P46-12 | A Mlegate tem subvenção concedida hoje? Qual ente, qual ato, qual empreendimento? | Alberto | Sem cadastro inicial |

# 12. Decisões para Alberto

A numeração segue a D-N95. Nada é consolidado antes da sua resposta.

| Nº | Decisão | Recomendação | Situação |
|---|---|---|---|
| D-N96 | Cadastro de modelos com duas entidades (`Cad_Modelo_Documento_Fiscal` e `Cad_Modelo_Documento_Fiscal_Codigo`, código por modelo ou por tipo de modelo, com vigência) substituindo o domínio `modelo_documento_fiscal`? | **Sim** | Direção sua; falta a confirmação do desenho |
| D-N97 | Prazos de opção e cancelamento: reaproveitar `Cad_Regra_Vencimento` e `Cad_Obrigacao_Prazo_Entrega` (4 alterações) e criar só `Mov_Obrigacao_Prazo_Empresa`, com as obrigações como linhas de `Cad_Obrigacao_Acessoria`? Alternativa: campos de data dentro de `Cad_Obrigacao_Acessoria` (um prazo por linha, sem regra nem janela) | **Reaproveitar e criar uma entidade** | Direção sua ("guardar"); falta a forma |
| D-N98 | SUP e ISS fixo: 5 entidades (regime de ISS por empresa e município, profissionais habilitados, tabela de valores, apuração trimestral e linhas por profissional)? | **Sim** | Direção sua; falta a confirmação do desenho |
| D-N99 | Mapa de conta para papel na EFD (`Cad_Conta_Contabil_Papel_Efd`) e geração com ajuste manual, com a tributação resolvida pelo Motor de Regras e não pelo mapa? | **Sim** | Direção sua; falta a confirmação do desenho |
| D-N100 | O rendimento de aplicação deixa de usar `evento_conta_financeira` para PIS e Cofins e passa a `operacao_fiscal_diversa`, e o documento 10 (seção 12) é reescrito depois do "consolidar"? | **Sim**, para não contar o rendimento duas vezes e deixar o regime como parâmetro | Aberta |
| D-N101 | Conciliação por conta (`Mov_Efd_Conciliacao_Contabil`) gravada no fechamento, com fechamento bloqueado se houver diferença sem justificativa? | **Sim, com bloqueio** (o contador pode justificar) | Aberta |
| D-N102 | Reabertura da contabilidade marca a geração como `desatualizada` e bloqueia o congelamento do período até regerar ou justificar? | **Sim** | Aberta |
| D-N103 | Integra Contador: relatório de conferência antes do envio e relatório de digitação na falha, com `aguardando_manual` após o limite de tentativas (parâmetro)? | **Sim** | Direção sua; falta a confirmação do detalhe |
| D-N104 | `Mov_Escrituracao_Arquivo` ganha 5 campos de recibo e hash e a regra "sem recibo, não retifica" (seção 8)? | **Sim** | Direção sua ("guardar o recibo e salvar o hash"); falta a confirmação dos campos |
| D-N105 | Subvenções: 2 entidades novas (`Cad_Subvencao_Investimento`, `Mov_Subvencao_Investimento_Periodo`) mais `Origem` nova em `Mov_Credito_Fiscal` e linhas no LALUR (seção 9)? | **Sim**, com o contador validando percentual, prazos e linhas | Direção sua ("sim, aplica-se"); falta o detalhe |

**Posso consolidar?**

# 13. Conferência

(a) Nenhum nome de entidade nova existe no `model.json` nem repete nome de outra proposta dos documentos 33 a 45; (b) toda entidade citada existe no `model.json` ou numa proposta dos documentos 33 a 45; (c) as 14 entidades novas são 4 (contabilidade), 5 (SUP), 2 (modelos), 1 (prazos) e 2 (subvenção); o recibo e o hash não criam entidade; (d) as datas da seção 6.2 vêm das fontes lidas e as de novembro e de março estão como prazo de órgão, não como certeza; (e) o documento **não altera** o dicionário; a seção 3.6 deixa registrado o que muda no documento 10 só após a sua resposta. O que não está confirmado e depende de contador ou de fonte está na seção 9.
