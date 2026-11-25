# Desenho do Estoque Proativo (motor nº 44) — Documento 251 (versão 5)

*Você pediu o estoque proativo em paralelo ao motor de envio bancário. Este documento é o desenho, **aplicado ao dicionário na revisão 57** (documento 255) depois do seu «consolidar» de 23/11/2026: **1.268 entidades e 14.928 campos**. **Versão 2 (23/11/2026):** refiz os números sobre a **revisão 56** (o motor de envio bancário, documento 250, já entrou na revisão 56 e o estoque proativo ficou de fora, como você escolheu). **Versão 3 (23/11/2026):** você respondeu **Q251-1 a Q251-7** (seguir a recomendação na 1, 2, 4, 5 e 7; **mudou a regra do empenho na 3** e **a da prioridade na 6**). O que mudou: o empenho da produção nasce quando a **OP entra na fila de produção** (e não na liberação da OP), a prioridade segue **venda, produção e demais áreas, e dentro da produção a posição na fila**, e, como **o dicionário não tem fila de produção**, o desenho ganha **uma entidade nova** (`Mov_Ordem_Producao_Fila`, 11 campos) e perde o campo `Prioridade` da reserva. **Agora são 3 entidades novas e +57 campos** (1.268 entidades e 14.928 campos). **Versão 4 (23/11/2026):** você respondeu a **Q251-8** (**seguir a recomendação**): a OP entra no fim da fila da filial quando é aberta, uma fila por filial, o perfil de produção troca a ordem (motivo opcional; o ERP guarda quem e quando) e só a última troca fica guardada. **Não há mais pergunta aberta** neste documento; o desenho não mudou de tamanho (3 entidades e 57 campos). **Versão 5 (23/11/2026):** você escreveu **«consolidar»** e o desenho **entrou na revisão 57** (documento 255); o DDL foi executado em PostgreSQL 16, sem erro. O que é interpretação minha está marcado como "leitura minha".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **O problema:** hoje o ERP só sabe o físico. A reserva existe apenas para a venda (`Mov_Estoque_Reserva`, nascida do orçamento aceito), a produção não compromete material (o documento 246 deu ao motor nº 44 "parcial 50%"), e não há mínimo, segurança, prazo de reposição nem alerta. As suas decisões de 04/09 (documento 14) pedem tudo isso: mínimo e segurança por produto, compra automática dentro da régua de aprovação, disponível = físico menos reservado, painéis de estoque crítico, de produção ("o material já está separado antes da fase começar?") e do vendedor.
2. **Uma só estrutura de comprometimento:** o empenho da produção e a reserva da venda passam a ser **a mesma tabela** (`Mov_Estoque_Reserva`), com duas origens possíveis (a entrega programada da venda ou o item da ordem de produção). É a sua recomendação da Q246-4, e é o que mantém o disponível como conta única: físico (só condição "disponível") menos reservas ativas.
3. **Três entidades novas:** a **política de reposição** por produto (`Cad_Estoque_Politica_Reposicao`, com vigência, **20 campos**), a **sugestão de reposição** (`Mov_Estoque_Sugestao`, **19 campos**), que registra cada vez que o ERP propõe comprar, produzir ou transferir, e o que foi decidido, e a **fila de produção** (`Mov_Ordem_Producao_Fila`, **11 campos**, versão 3), onde cada OP tem uma **posição** que o operador pode trocar.
4. **Campos novos em tabelas existentes:** **5** em `Mov_Estoque_Reserva` (origem OP, lote, vencimento, encerramento e motivo; a origem de venda passa a ser opcional; **não há campo de prioridade**, ela é derivada da origem e da posição na fila) e **2** em `Mov_Ordem_Producao_Item` (componente substituído e motivo).
5. **O que não vira tabela:** o disponível, o "a receber", a necessidade líquida, os alertas e os painéis são **leituras derivadas**; os avisos usam o domínio aberto de notificações (cinco valores novos, que são dados).
6. **Nada é emitido sozinho:** a compra automática cria só um **pedido em rascunho**, que entra na régua de aprovação como qualquer pedido (`Mov_Pedido.Status = rascunho`).
7. **Total (aplicado na revisão 57):** **+3 entidades (1.268) e +57 campos (14.928)**. **Sem pergunta nova ao contador.**
8. **Para você:** as **Q251-1 a Q251-8 estão respondidas** (seção 6); **não há pergunta aberta**. **Aplicado na revisão 57** (seção 9).

# 2. O que o dicionário já tem

| Peça | O que existe | Limite |
|---|---|---|
| Reserva de venda | `Mov_Estoque_Reserva` (6 campos): entrega programada obrigatória, local, quantidade, data/hora, status {ativa, baixada, cancelada}. Nasce com o orçamento aceito; a NF de saída a baixa | Só a venda pode reservar. A concorrência por saldo é tratada na aplicação (documento 05) |
| Disponível | Consulta derivada: físico menos o que não está na condição "disponível" (`Mov_Estoque_Condicao`, `Mov_Estoque_Bloqueio`). O documento 04 diz que a reserva é "fora deste módulo" | Não desconta empenho de produção |
| Produção | `Mov_Ordem_Producao_Item` (13 campos): componente, quantidade planejada e consumida, movimento de saída. `Mov_Ordem_Producao_Fase` tem `Data_Inicio_Planejada`. O documento 06 prevê liberar material por fase e o movimento de "envio para produção" | Nada reserva o material antes da saída; não há aviso de falta |
| Compras | `Mov_Pedido` (status com `rascunho` e `em_aprovacao`, `ID_Instancia_Aprovacao`) e `Mov_Pedido_Item.Data_Entrega_Prevista`. O documento 03 deixou a requisição interna de compra "não modelada" | Ninguém gera o pedido a partir do estoque |
| Lote e validade | `Cad_Lote_Produto` (5 campos, com `Data_Validade`) | Sem regra de saída (FEFO ou FIFO) nem aviso de vencimento |
| Locais | `Cad_Local_Estoque` com tipo {deposito, loja, producao, transito, terceiros}; `Mov_Saldo_Estoque` (foto mensal) | O local "transito" já serve para transferência entre filiais |
| Avisos | Domínio aberto `tipo_notificacao_sistema` (`Cad_Participante_Email_Tipo_Notificacao`) e as réguas de aprovação (`Cad_Regua_Aprovacao`, `Mov_Aprovacao_Instancia`) | Não há aviso de estoque |
| Mínimo, segurança, prazo de reposição, sugestão | **Nada** (conferi no modelo: nenhum campo com esses nomes nem entidade de empenho, de necessidade ou de sugestão) | — |

# 3. Desenho

## 3.1 Reserva e empenho: a mesma tabela

`Mov_Estoque_Reserva` continua no módulo 05 (leitura minha: manter o nome evita mexer em todos os textos que já a citam; o documento explica que ela cobre também o empenho). Muda assim:

| Campo | Regra |
|---|---|
| `ID_Entrega_Programada` | **Passa a ser opcional** (hoje é obrigatório) |
| `ID_Item_Ordem_Producao` (novo, opcional, referência a `Mov_Ordem_Producao_Item`) | Origem "produção". **Exatamente uma** das duas origens preenchida (regra R3). A reserva de **venda** continua nascendo no aceite do cliente (o dicionário diz «orçamento aceito»; li como o mesmo evento do **pedido aprovado pelo cliente** que você citou) |
| `ID_Lote` (novo, opcional) | O lote reservado, quando a regra de saída do produto exige (FEFO, seção 3.5) |
| `Data_Expiracao` (novo, opcional) | Quando a reserva deixa de valer sem decisão (a de venda herda o prazo da proposta; a de OP não tem) |
| `Data_Hora_Encerramento` (novo, opcional) | Quando saiu de "ativa" |
| `Motivo_Encerramento` (novo, opcional) | Texto: "OP cancelada", "cliente desistiu", "vencida" |
| `Status` | Ganha o valor **`expirada`** (hoje: ativa, baixada, cancelada) |

Resultado: **6 → 11 campos** (versão 3: sem o campo `Prioridade`, que a regra da Q251-6 torna derivada).

**Quando o empenho nasce (Q251-3, resposta de Alberto, versão 3):** há **dois empenhos**: **(1) venda:** no momento em que o **pedido é aprovado pelo cliente**, o produto já fica reservado; **(2) produção:** no momento em que a **OP entra na fila de produção**, **todos os componentes dela já ficam empenhados** (um empenho por item de componente), com a **data de necessidade = início planejado da fase** do item (`ID_Fase_OP`); se a fase não tem início planejado, a data é a da entrada na fila (leitura minha). O **movimento de saída** (o «envio para a produção» do documento 06) **baixa** o empenho (`Status = baixada`). Se a OP é cancelada ou sai da fila sem produzir, o empenho é encerrado com motivo.

## 3.2 A política de reposição: `Cad_Estoque_Politica_Reposicao` (com vigência, 20 campos)

Um registro por produto e filial (e, se quiser, por local), com a história de cada mudança de parâmetro:

| Campo | Regra |
|---|---|
| `ID_Politica_Reposicao` e `ID_Politica_Reposicao_Versao` | Identificador e chave da versão |
| `ID_Produto_Servico` | O produto (só produtos de estoque) |
| `ID_Filial` | A filial a que a política vale |
| `ID_Local_Estoque` (opcional) | Vazio = soma dos locais "disponíveis" da filial |
| `Estoque_Minimo` (opcional) | O **ponto de pedido**: abaixo dele (já contado o "a receber"), o ERP propõe repor |
| `Estoque_Seguranca` (opcional) | O colchão: abaixo dele (só com o físico disponível) o aviso é **crítico** |
| `Estoque_Maximo` (opcional) | O teto da reposição |
| `Lote_Minimo_Reposicao` e `Multiplo_Reposicao` (opcionais) | Arredondamento da quantidade proposta |
| `Lead_Time_Dias` (opcional) | Prazo informado à mão; se vazio, vale a **média real** lida do histórico (seção 3.4) |
| `Origem_Reposicao` | {compra, producao, transferencia} |
| `ID_Participante_Fornecedor_Padrao` (opcional) | Fornecedor sugerido no rascunho de compra |
| `ID_Filial_Origem_Transferencia` (opcional) | Filial que abastece, quando a origem é transferência |
| `Regra_Saida_Lote` | {fefo, fifo, manual} (seção 3.5) |
| `Dias_Aviso_Validade` (opcional) | Quantos dias antes do vencimento do lote o ERP avisa |
| `Modo_Reposicao` | {somente_sugerir, gerar_rascunho} |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` (opcional) | Vigência padrão do dicionário |

Quem **não** tem política não gera sugestão nem aviso de mínimo (o estoque proativo é **opt-in por produto**, como no documento 14: "produtos de uso contínuo").

## 3.3 A sugestão: `Mov_Estoque_Sugestao` (19 campos)

É o **registro do evento**: cada vez que o ERP propõe uma reposição, nasce uma linha; ela guarda por que, quanto, para quando, o que o usuário decidiu e qual documento saiu dali.

| Campo | Regra |
|---|---|
| `ID_Sugestao` | Identificador |
| `ID_Politica_Reposicao` (opcional) | A política que disparou (vazio quando o gatilho é a falta de material de uma OP) |
| `ID_Produto_Servico`, `ID_Filial`, `ID_Local_Estoque` (opcional) | O que e onde |
| `Tipo_Sugestao` | {compra, producao, transferencia} |
| `Quantidade_Sugerida` | Já com mínimo, máximo, lote mínimo e múltiplo aplicados |
| `Data_Necessidade` | Quando o material faz falta |
| `Data_Limite_Pedido` | Data de necessidade menos o prazo de reposição: **o último dia para pedir** |
| `Motivo` | {abaixo_minimo, abaixo_seguranca, necessidade_producao, necessidade_venda} |
| `Disponivel_No_Calculo` e `A_Receber_No_Calculo` | Os dois números usados na conta, **congelados como evidência do evento** (não são saldo: ninguém lê o disponível daqui; leitura minha, para o usuário ver "por que o ERP sugeriu isso" mesmo depois de o saldo mudar) |
| `Status` | {pendente, aceita, descartada, expirada} |
| `Tipo_Documento_Gerado` e `ID_Documento_Gerado` (opcionais) | Referência genérica ao pedido em rascunho, à OP ou ao movimento de transferência |
| `ID_Usuario_Decisao` (opcional) e `Data_Hora_Decisao` (opcional) | Quem decidiu e quando |
| `Motivo_Decisao` (opcional) | Obrigatório ao **descartar** (R9) |
| `Data_Hora_Geracao` | Quando o ERP gerou |

## 3.4 As leituras (sem campo)

| Leitura | Conta |
|---|---|
| **Disponível** | Físico na condição "disponível" − reservas ativas (venda e empenho). Nunca guardado |
| **A receber** | Itens de pedido de compra abertos (pedido − recebido), OPs abertas do produto acabado e transferências em trânsito (local "transito"), com a data prevista (`Data_Entrega_Prevista`, fim da OP) |
| **Necessidade líquida** | O que falta para chegar ao nível da política: Mínimo (ou Mínimo + Segurança) − (Disponível + A receber) |
| **Prazo médio real** | Média, por produto e fornecedor, de (data do recebimento − data do pedido) nos últimos 12 meses (leitura minha: janela de 12 meses, a ajustar). Alimenta o painel do vendedor ("lead time médio") e vale como prazo quando `Lead_Time_Dias` está vazio |
| **Material da fase** | Para cada fase com início nos próximos N dias: empenho coberto, empenho parcial ou **sem material**; é a resposta do painel de Produção do documento 14 |

## 3.5 Saída de lote (FEFO e FIFO)

`Regra_Saida_Lote` diz como o ERP escolhe o lote **ao reservar**: **FEFO** (vence primeiro, sai primeiro) para quem tem validade, **FIFO** (entrou primeiro, sai primeiro) para o resto, **manual** quando o operador escolhe. A reserva grava o `ID_Lote`; a saída física (`Mov_Estoque_Movimento_Item`) deve usar o mesmo lote ou justificar a troca. O aviso de vencimento usa `Dias_Aviso_Validade` sobre `Cad_Lote_Produto.Data_Validade`. **O ERP avisa; não baixa lote vencido sozinho** (a baixa por perda segue o movimento já existente, com o tratamento fiscal que ele tem).

## 3.6 Substituição de componente na OP (opcional, Q251-7)

Quando falta o componente da estrutura e a produção usa outro equivalente, `Mov_Ordem_Producao_Item` ganha **2 campos opcionais**: `ID_Produto_Servico_Componente_Estrutura` (o componente que a estrutura mestre previa, preenchido só quando houve troca) e `Motivo_Substituicao`. O campo atual `ID_Produto_Servico_Componente` passa a ser, sem ambiguidade, **o que de fato foi usado**. A estrutura mestre (`Cad_Estrutura_Producao_Item`) não muda: a troca é um **desvio da OP**, destacado no painel. **13 → 15 campos.**

## 3.7 Alertas e painéis

Todos são **leituras**; só o envio usa o domínio aberto de notificações, com cinco valores novos (dados, não estrutura): `estoque_abaixo_minimo`, `estoque_abaixo_seguranca`, `material_fase_nao_separado`, `lote_proximo_validade`, `sugestao_reposicao_pendente`. Quem recebe vem do perfil e do escopo do usuário (`Cad_Usuario_Escopo`, tipos "local_estoque" e "produto").

| Painel | Conteúdo |
|---|---|
| Estoque | Itens em quantidade crítica (abaixo da segurança ou do mínimo), sugestões pendentes, lotes perto do vencimento |
| Produção | Sequência das fases e, antes de cada uma começar, se o material já está separado (empenho coberto, parcial ou sem material) |
| Vendedor | Disponível já **sem** o reservado, "a receber" com data e prazo médio de reposição |
| Compras | Sugestões de compra por data limite do pedido, rascunhos gerados aguardando a régua |

## 3.8 A fila de produção: `Mov_Ordem_Producao_Fila` (11 campos, versão 3)

**O dicionário não tem fila de produção:** a OP tem só `Status` {aberta, em_producao, concluida, cancelada} e as fases têm `Ordem_Sequencia`, que é a ordem das fases **dentro** de uma OP. Como o empenho da produção nasce quando a OP **entra na fila** (Q251-3) e a prioridade depende de **quem está na frente** (Q251-6), a fila precisa existir. Estrutura mínima (leitura minha; a Q251-8 confirma o escopo):

| Campo | Regra |
|---|---|
| `ID_Fila_Producao` | Identificador |
| `ID_OP` | A OP (referência a `Mov_Ordem_Producao`) |
| `ID_Filial` | A fila a que a OP pertence (uma fila por filial; Q251-8 b) |
| `Posicao` | Número: 1 é a próxima a ser produzida. O **operador pode trocar** a ordem e as demais se reacomodam |
| `Situacao_Fila` | {na_fila, em_producao, encerrada}: `na_fila` empenha; `em_producao` quando a primeira fase começa; `encerrada` se a OP é concluída ou cancelada |
| `Data_Hora_Entrada` | Quando a OP entrou na fila (nasce o empenho) |
| `Data_Hora_Saida` (opcional) | Quando saiu da fila |
| `Motivo_Saida` (opcional) | Texto (por exemplo, «OP cancelada») |
| `ID_Usuario_Ultima_Reordenacao` (opcional) | Quem trocou a ordem por último |
| `Data_Hora_Ultima_Reordenacao` (opcional) | Quando |
| `Motivo_Reordenacao` (opcional) | Por que o operador trocou (Q251-8 c) |

Uma OP tem **no máximo uma linha ativa** (`na_fila` ou `em_producao`) na fila. Não há agendamento automático por capacidade: a ordem é a do operador (a verificação de conflito de capacidade segue fora, como o documento 06 já diz).

## 3.9 Quem recebe o material quando falta (Q251-6, versão 3)

A cobertura de cada empenho é **calculada na hora** (não gravada): o disponível é distribuído pela ordem da regra R11 (venda, depois produção, depois as demais áreas; dentro da produção, pela posição na fila). Cada empenho aparece como **coberto, parcial ou sem material**. Se a OP **não tem todos os produtos para iniciar uma etapa**, o ERP **avisa o operador** (aviso `material_fase_nao_separado`, na tela da fase e no painel de Produção). Se o operador **troca a ordem da fila**, a cobertura é **recalculada**: o produto vai para quem passou a estar na frente. A reserva de **venda** passa na frente da produção (sua regra): uma venda aprovada depois pode **tirar a cobertura** de uma OP que ainda não retirou o material; o operador é avisado. O que já saiu do estoque (movimento de «envio para a produção») não é afetado.

# 4. Regras

- **R1.** O disponível é **sempre derivado**: físico (condição "disponível") menos reservas ativas. Nenhum saldo disponível ou reservado é gravado (documento 14).
- **R2.** Empenho e reserva de venda são a **mesma tabela e o mesmo mecanismo**, com origens diferentes.
- **R3.** Cada reserva tem **exatamente uma origem**: a entrega programada ou o item de OP. Isso é uma regra de validação (não uma chave estrangeira condicional).
- **R4.** O empenho de venda nasce na **aprovação do pedido pelo cliente**; o de produção, quando a **OP entra na fila de produção**, por item de componente, com data de necessidade igual ao início planejado da fase; é baixado pelo movimento de saída para a produção e encerrado, com motivo, se a OP ou o item for cancelado ou se a OP sair da fila sem produzir (Q251-3, resposta de Alberto).
- **R5.** Os gatilhos comparam **Disponível + A receber** (mínimo) e **Disponível** (segurança), nunca o físico (documento 14, 04/09).
- **R6.** Quantidade sugerida = quanto falta para o **máximo** (se houver; senão, mínimo mais segurança), **arredondada para cima** ao múltiplo e nunca abaixo do lote mínimo (leitura minha).
- **R7.** `Data_Limite_Pedido` = `Data_Necessidade` − prazo de reposição (o informado na política ou, na falta, a média real).
- **R8.** Modo `gerar_rascunho`: o ERP cria um `Mov_Pedido` em **rascunho** (ou a OP em rascunho, ou o movimento de transferência pendente) e liga à sugestão. O pedido só sai pela **régua de aprovação** (`Mov_Pedido.ID_Instancia_Aprovacao`), respeitando o orçamento. **Nenhum documento é emitido, enviado ou aprovado sem decisão humana.**
- **R9.** **Descartar** uma sugestão exige motivo. Uma sugestão pendente cuja condição desapareceu (chegou mercadoria, o saldo subiu) vira **expirada** sozinha; não gera duplicata: **no máximo uma sugestão pendente por produto, filial e tipo**.
- **R10.** Falta de material para uma OP (empenho parcial ou sem material) gera o aviso `material_fase_nao_separado` **ao operador**, **antes de ele iniciar a etapa**, e, se o produto tem política, uma sugestão com motivo `necessidade_producao` e data de necessidade igual ao início da fase (Q251-6, resposta de Alberto).
- **R11.** Quando o disponível não cobre todas as reservas, o atendimento segue esta ordem fixa (Q251-6, resposta de Alberto): **1º venda; 2º produção; 3º demais áreas** (hoje nenhuma outra área reserva: a transferência entre filiais gera movimento em trânsito, R13; se uma área nova reservar, entra como nova origem na classe 3). **Dentro da venda**, a ordem é a data e hora da aprovação do pedido (leitura minha); **dentro da produção**, a **posição da OP na fila de produção** (quem está na frente é atendido primeiro, e **a troca da ordem pelo operador muda a prioridade**); dentro das demais, data e hora da reserva. A prioridade é **derivada** (não há campo).
- **R12.** Reservas de venda vencidas (`Data_Expiracao`) geram aviso ao vendedor; o status `expirada` é gravado quando a reserva é encerrada por vencimento (Q251-5).
- **R13.** Transferência entre filiais: a sugestão com origem `transferencia` gera o movimento com o local "transito"; a nota fiscal de transferência segue os módulos fiscais já desenhados (nada novo aqui).
- **R14.** A política tem **vigência** (a mudança de mínimo fica registrada: quem alterou e a partir de quando), e as sugestões antigas continuam apontando para a política vigente na época.
- **R15.** Estoque proativo é **opt-in por produto**: sem política, o ERP só mostra o disponível (comportamento de hoje).
- **R16.** Cada OP tem **no máximo uma linha ativa** em `Mov_Ordem_Producao_Fila` (R3 vale como regra de validação); a posição é única por fila e a troca da ordem recalcula as posições das demais (versão 3).
- **R17.** A troca da ordem da fila guarda **quem trocou, quando e o motivo** (opcional, Q251-8 c) e **recalcula a cobertura** dos empenhos (R11); nenhum material já retirado do estoque volta por causa da troca (versão 3).

# 5. O que fica fora

| Assunto | Tratamento |
|---|---|
| Planejamento de necessidade de materiais completo (MRP com explosão de estrutura em vários níveis e horizonte de meses) | Fora. O desenho cobre o primeiro nível (componente da OP liberada) e a política por produto. O MRP completo só se você pedir (o documento 06 já tira da fase 1 a capacidade e o prazo sugerido) |
| Previsão de demanda estatística (média móvel, sazonalidade) | Fora. O mínimo é informado; o ERP só dá a **leitura** do consumo real para você revisar o parâmetro |
| Requisição interna de compra (setor pede, compras atende) | Continua "não modelada" (documento 03) |
| Cálculo do lote econômico de compra | Fora; o lote mínimo e o múltiplo são parâmetros |
| Baixa automática de lote vencido | Fora: o ERP só avisa |
| Agendamento automático da fila por capacidade, prazo e recurso | Fora: a fila é **manual** (o operador troca); a capacidade produtiva segue fora, como o documento 06 já tira da fase 1 |
| Reserva de material em estoque de terceiros | Sem desenho especial; o local "terceiros" já existe e segue a mesma reserva |

# 6. Perguntas para você

**Respondidas por Alberto em 23/11/2026** (versão 3; decisão D-N661, seção 8):

| Nº | Pergunta | Resposta |
|---|---|---|
| Q251-1 | **Estrutura única** (liga à Q246-4): empenho e reserva de venda na mesma tabela `Mov_Estoque_Reserva`, com duas origens possíveis? | **Seguir a recomendação:** sim |
| Q251-2 | **Compra automática:** o pedido de reposição nasce em rascunho (entra na régua) para os produtos de uso contínuo, ou o ERP só sugere? | **Seguir a recomendação:** rascunho para uso contínuo; `Modo_Reposicao` deixa cada produto voltar a «somente sugerir» |
| Q251-3 | **Quando o empenho nasce** | **«Tem vários empenhos»:** na **venda**, quando o pedido é aprovado pelo cliente; na **produção**, quando a **OP entra na fila de produção** (todos os componentes já ficam reservados). **Muda a recomendação** (que era: na liberação da OP) e cria a fila (seção 3.8) |
| Q251-4 | **Saída de lote:** FEFO para o que tem validade e FIFO para o resto, por produto? | **Seguir a recomendação:** sim |
| Q251-5 | **Reserva de venda que não é faturada:** deve vencer? | **Seguir a recomendação:** só **avisar** o vendedor; ele renova ou encerra (`expirada`) |
| Q251-6 | **Quem tem prioridade** quando o disponível não cobre tudo? | **Venda, depois produção, depois as demais áreas.** Se a OP não tem todos os produtos para iniciar uma etapa, **avisar o operador**; se o operador troca a fila de fabricação, **a prioridade é de quem está na frente na fila** (R11, seção 3.9). **Muda a recomendação** (que era uma ordem por prioridade informada, data e chegada) |
| Q251-7 | **Substituição de componente na OP:** incluir os 2 campos? | **Seguir a recomendação:** sim |

**Respondida por Alberto em 23/11/2026** (versão 4; decisão D-N662, seção 8):

| Nº | Pergunta | Resposta |
|---|---|---|
| Q251-8 | **A fila de produção (versão 3, seção 3.8):** (a) **como a OP entra na fila**: automaticamente, no **fim da fila**, quando a OP é aberta, ou o PCP a envia? (b) **uma fila por filial** ou por linha, recurso ou máquina? (c) a **troca da ordem** pelo operador exige **motivo**, e quem pode trocar? (d) guardar o **histórico** de cada troca (uma tabela a mais) ou só a **última**? | **Seguir a recomendação:** (a) a OP entra **automaticamente no fim da fila** da filial quando é aberta (sem fila não há empenho, R4); (b) **uma fila por filial** (o recurso entra depois, como campo opcional, se a Mlegate tiver linhas separadas); (c) quem tem o **perfil de produção** troca a ordem, **motivo opcional** (o ERP guarda quem e quando); (d) guardar **só a última troca** nesta fase (o histórico completo fica para uma próxima camada) |

# 7. Para o contador (documento 188)

**Nenhuma pergunta nova (C374 não foi usado).** O empenho e a reserva não mexem em saldo contábil (o item continua no estoque até a saída); a sugestão não gera documento fiscal; as transferências e a baixa de lote vencido seguem os tratamentos já desenhados. Se você quiser **baixa sugerida** de lote vencido, aí sim abrimos a pergunta do estorno de crédito (ICMS, PIS e Cofins) na perda de estoque.

# 8. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N640 (proposta) | Desenhar o estoque proativo: reserva e empenho na mesma estrutura; política de reposição por produto com vigência; sugestão de reposição como registro de evento; disponível sempre derivado; compra automática só em rascunho dentro da régua de aprovação | Pedido de 18/11/2026 ("em paralelo pode fazer o Estoque proativo"), Q246-4, decisões de 04/09 (documento 14) |
| D-N661 | Respostas de Alberto (23/11/2026) às Q251-1 a Q251-7: **seguir a recomendação** nas 1, 2, 4, 5 e 7; **Q251-3:** há vários empenhos: o da venda nasce quando o pedido é aprovado pelo cliente e o da produção quando a OP entra na fila de produção; **Q251-6:** prioridade venda, produção e demais áreas, avisar o operador quando faltar produto para iniciar a etapa, e, se o operador trocar a fila, a prioridade é de quem está na frente. **Efeito no desenho (versão 3):** nova entidade `Mov_Ordem_Producao_Fila` (11 campos); o campo `Prioridade` da reserva sai (derivado); regras R4, R10 e R11 refeitas e R16 e R17 novas. **Aplicado na revisão 57** (documento 255) | Respostas de 23/11/2026 |
| D-N662 | Resposta de Alberto (23/11/2026) à Q251-8: **seguir a recomendação**: a OP entra no fim da fila da filial quando é aberta; uma fila por filial; perfil de produção troca a ordem, com motivo opcional (o ERP guarda quem e quando); só a última troca é guardada. **Efeito no desenho:** nenhum em tamanho (a fila já tinha 11 campos, `Motivo_Reordenacao` opcional); o estoque proativo fica **sem pergunta aberta**. **Aplicado na revisão 57** (documento 255) | Resposta de 23/11/2026 |
| D-N663 | Consolidação da revisão 57 (23/11/2026): o estoque proativo e a fila de produção entram no dicionário: 3 entidades novas, 57 campos, **1.268 entidades e 14.928 campos** | Pedido «consolidar» de 23/11/2026 |

# 9. O que mudou no «consolidar» (revisão 57)

| Medida | Revisão 56 | Revisão 57 |
|---|---|---|
| Entidades | 1.265 | **1.268** (+3: `Cad_Estoque_Politica_Reposicao`, `Mov_Estoque_Sugestao` e `Mov_Ordem_Producao_Fila`) |
| Campos | 14.871 | **14.928** (+20 na política, +19 na sugestão, +11 na fila, +5 em `Mov_Estoque_Reserva` e +2 em `Mov_Ordem_Producao_Item`) |
| Mestres (identidade + versão) | 274 | **275** (a política tem vigência) |
| Chaves tardias | 92 | **93** (confirmado na geração: `Mov_Estoque_Reserva.ID_Item_Ordem_Producao` aponta do módulo 05 para o 06) |
| Campo alterado | — | `Mov_Estoque_Reserva.ID_Entrega_Programada` passa de obrigatório a opcional; `Status` ganha `expirada` |
| Domínios | 376 | 376 (a fila usa enumerações no próprio campo) |
| Dados (não estrutura) | — | 5 valores em `tipo_notificacao_sistema` |

Mudaram também os textos: a Fase 1 Estoque (seção da reserva e do disponível), a Fase 1 CRM e Vendas (seção 6, reserva) e a Fase 1 Produção (a fila de produção e a liberação de material); os documentos 14 (D-N640, D-N661 e D-N662), 38 (Q251-8) e 246 (motor nº 44). A conferência de contagens, o DDL e a auditoria rodam no ensaio de consolidação, como nas revisões anteriores.

# 10. Fontes e limites

**Fontes (o que li, todas do projeto):** documento 14 (decisões de 04/09 sobre estoque proativo e painéis); documentos 03 (Compras), 04 (Estoque), 05 (CRM e Vendas, seção 6), 06 (Produção) e 07 (Expedição); documento 246 (motor nº 44 e Q246-4); o modelo da revisão 56 (campos e domínios conferidos entidade por entidade).

**Limites:**
- **Nenhuma fonte externa** foi consultada: o desenho vem do dicionário e das suas decisões; os parâmetros (janela de 12 meses do prazo médio, arredondamento, regra de quantidade) são **leitura minha** e estão marcados.
- Os nomes das entidades e dos campos são propostas, no padrão do dicionário.
- Não testei o desenho contra dados reais da Mlegate (não há histórico de consumo no projeto); os números do painel dependem dos movimentos reais.
- A regra de "chave tardia" (item de OP) fica para o ensaio de consolidação.
