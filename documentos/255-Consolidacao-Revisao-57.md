# Consolidação da Revisão 57 — Documento 255

*Você escreveu **«consolidar»**, depois de responder a **Q251-8**: apliquei ao dicionário o **estoque proativo** (documento 251, versão 5; D-N640, D-N661 e D-N662), com a **fila de produção**, pelas suas respostas. **Três entidades novas e 57 campos.** Decisão registrada como D-N663.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 56** | **Revisão 57** | **Diferença** |
|---|---|---|---|
| Entidades | 1.265 | **1.268** | +3 (2 no Estoque e 1 na Produção) |
| Campos | 14.871 | **14.928** | +57 (50 nas 3 entidades novas, 5 em `Mov_Estoque_Reserva` e 2 em `Mov_Ordem_Producao_Item`) |
| Campos de referência (FK) | 3.764 | **3.780** | +16 |
| Entidades mestres | 274 | **275** | +1 (`Cad_Estoque_Politica_Reposicao`, com vigência) |
| Domínios de `Cad_Classe_Sistema` | 376 | 376 | 0 (5 valores novos em `tipo_notificacao_sistema`, que é dado, vão na Carga57) |
| Tabelas físicas (DDL) | 1.539 | **1.543** | +4 (3 entidades e 1 tabela de versão) |
| Chaves estrangeiras (DDL) | 4.038 | **4.055** | +17 |
| Índices (DDL) | 4.130 | **4.147** | +17 |
| Comentários (DDL) | 12.589 | **12.643** | +54 |
| Comandos do T-SQL | 22.297 | **22.389** | +92 |
| Chaves opcionais que esperam a onda de destino | 92 | **93** | +1 (`Mov_Estoque_Reserva.ID_Item_Ordem_Producao`, do módulo 05 para o 06) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Fase 0 101, Estoque 18, CRM & Vendas 29, Produção 16 | Fase 0 **102**, Estoque **19**, CRM & Vendas **30**, Produção **17** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.543 tabelas, 4.055 chaves estrangeiras, 12.643 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Decisão** | **Onde ficou no dicionário** |
|---|---|
| Reserva de venda e empenho de produção na mesma estrutura (Q251-1) | **`Mov_Estoque_Reserva`** (módulo 05, de 6 para **11 campos**): `ID_Item_Ordem_Producao` (a origem «produção»; exatamente uma das duas origens, R3), `ID_Lote`, `Data_Expiracao`, `Data_Hora_Encerramento` e `Motivo_Encerramento`. `ID_Entrega_Programada` passa a **opcional** e o `Status` ganha **`expirada`**. Não há campo de prioridade: ela é derivada (R11). |
| Quando o empenho nasce (Q251-3) | Venda: na **aprovação do pedido pelo cliente**. Produção: quando a **OP entra na fila de produção**, um empenho por item de componente, com data de necessidade igual ao início planejado da fase (R4). |
| Quem recebe o material quando falta (Q251-6) | Ordem fixa: **venda, produção, demais áreas**; dentro da produção, a **posição na fila** (R11). Se faltar produto para iniciar a etapa, o ERP **avisa o operador**; se o operador trocar a fila, a prioridade é de quem está na frente. Tudo calculado na hora, sem campo. |
| Fila de produção (Q251-8) | **`Mov_Ordem_Producao_Fila`** (11 campos, módulo 06): a OP entra **automaticamente no fim da fila da filial** quando é aberta; **uma fila por filial**; o perfil de produção troca a ordem, **motivo opcional**, e o ERP guarda **quem e quando**, só a **última** troca. |
| Política de reposição por produto | **`Cad_Estoque_Politica_Reposicao`** (20 campos, com vigência): mínimo, segurança, máximo, lote mínimo e múltiplo, prazo, origem, fornecedor padrão, regra de saída de lote (FEFO, FIFO ou manual), aviso de validade e modo (`somente_sugerir` ou `gerar_rascunho`). **Opt-in por produto** (R15). |
| Sugestão de reposição | **`Mov_Estoque_Sugestao`** (19 campos): o registro do evento, com o disponível e o «a receber» **congelados como evidência**, a data limite do pedido, a decisão e o documento gerado. Compra automática só em **rascunho**, dentro da régua de aprovação (R8). |
| Saída de lote (Q251-4) | FEFO para o que tem validade e FIFO para o resto, por produto (`Regra_Saida_Lote`); o ERP **avisa** o vencimento e **não baixa** lote vencido sozinho. |
| Reserva de venda não faturada (Q251-5) | Só **avisa** o vendedor, que renova ou encerra (`expirada`, R12). |
| Substituição de componente na OP (Q251-7) | `Mov_Ordem_Producao_Item` ganha `ID_Produto_Servico_Componente_Estrutura` e `Motivo_Substituicao` (13 para 15 campos). |
| Avisos e painéis | **Leituras, sem campo**; só o envio usa o domínio aberto `tipo_notificacao_sistema`, com **5 valores novos** (dados, na Carga57). |

# 3. O que não entrou

- **Agendamento automático da fila por capacidade, prazo e recurso:** fora; a fila é manual e a capacidade produtiva segue fora, como o documento 06 já dizia.
- **Histórico completo das trocas da fila:** fora nesta fase (só a última troca fica guardada); entra como próxima camada se você quiser.
- **Recurso (linha ou máquina) na fila:** fora; se a Mlegate tiver linhas separadas, entra depois como campo opcional.
- **Baixa automática de lote vencido, requisição interna de compra e lote econômico de compra:** fora (o lote mínimo e o múltiplo são parâmetros).
- **Compra, OP ou transferência emitidas sozinhas:** nada sai sem decisão humana; o modo `gerar_rascunho` cria só rascunho.

# 4. A Carga57

| **Pasta** | **Conteúdo** | **Linhas** |
|---|---|---|
| 01-dominio-notificacao-estoque | `Cad_Classe_Sistema`: 5 valores de `tipo_notificacao_sistema` (`estoque_abaixo_minimo`, `estoque_abaixo_seguranca`, `material_fase_nao_separado`, `lote_proximo_validade` e `sugestao_reposicao_pendente`) | 5 |

As **políticas de reposição** não têm carga: cada uma é cadastrada por produto, filial e local. A fila de produção e as sugestões nascem do uso.

# 5. Leituras minhas e limites do que apliquei

- **Nome mantido:** `Mov_Estoque_Reserva` continua no módulo 05, com o nome de sempre, para não mexer em todos os textos que já a citam; a descrição agora diz que ela cobre também o empenho.
- **Data de necessidade sem início planejado:** se a fase do item não tem início planejado, vale a data de entrada na fila.
- **Disponível e «a receber» congelados na sugestão:** são evidência do evento, não saldo; ninguém lê o disponível dali.
- **Janela de 12 meses** do prazo médio real de reposição, arredondamento da quantidade proposta e a regra de «no máximo uma sugestão pendente por produto, filial e tipo»: parâmetros meus, a ajustar.
- **Dentro da venda,** a ordem de atendimento é a data e hora da aprovação do pedido; dentro das demais áreas, a data e hora da reserva (leitura minha).
- **Percentuais do inventário (documento 246):** não foram revistos com esta aplicação; ficam para o próximo levantamento.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** nenhuma pergunta nova do estoque proativo (Q251-1 a Q251-8 todas respondidas). Seguem abertas as do envio bancário, **por banco**, no documento 254, os **três PDFs da Caixa** bloqueados (Q250-56) e os demais itens do documento 38.
- **Contador:** nada novo (o empenho e a reserva não mexem em saldo contábil); segue a **C374** (reservada: dia 20 do FGTS e multa de 40 por cento, Q250-47).

Próximos números: D-N664, contador C374, documento 252 (FGTS, reservado), documento 256, R128, Q250-61, Q251-9, Q246-9, Q248-7, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.56.
