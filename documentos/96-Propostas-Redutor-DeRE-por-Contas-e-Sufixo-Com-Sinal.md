# Propostas Pendentes de Aprovação: DeRE Mensal por Conta e Ligação Operação × Categoria — Documento 96 (reescrito em 22/10/2026)

> **Aplicado na revisão 24 (26/10/2026, documento 122, D-N366).** Entraram a entidade `Mov_Dere_Linha_Mes` (15 campos), o texto "Tipo NS (numérico com sinal)" na `Descricao` dos 34 campos NS da carga do leiaute (Q96-7), o texto de `Mov_Apuracao_Tributo_Item_Complemento.Codigo_Classificacao` (Q96-8) e o texto de `Cad_Credito_Presumido_Ibs_Cbs.ID_Categoria_Credito_Presumido` (Q96-9; o campo já era opcional desde a revisão 19). Onde o texto abaixo diz que nada está no dicionário, vale esta nota; o que esse documento ainda traz como proposta sem resposta continua no documento 38.

*Este documento foi reescrito depois das suas respostas de 22/10/2026 (Q96-1 a Q96-14). A primeira versão propunha dois cadastros para repartir o valor das contas redutoras da DeRE; as suas respostas mudaram o desenho, e a proposta antiga **saiu**. O que você aprovou com campos já vistos entrou na revisão 20 (documento 97). O que sobra aqui é proposta: **nada abaixo está no dicionário**. Os nomes de entidade e de campo são meus.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Entrou na revisão 20 (documento 97):** o tipo do lançamento contábil em três valores (normal, encerramento e extemporâneo) com a regra do lote (Q96-13 e Q96-14), e o sufixo `Com_Sinal` nos dois campos do ERP na ECF que não têm indicador de natureza (Q96-6).
- **Proposta nova da DeRE (seção 3):** uma entidade mensal única, com uma linha por conta contábil e tipo de informação (valor base ou dedução). Ela substitui as duas entidades que eu tinha proposto. Falta a sua aprovação da lista de campos (Q96-15 a Q96-17).
- **Continua em aberto:** Q96-7 (texto "Tipo NS" na carga), Q96-8 (ligação operação → categoria do crédito presumido) e Q96-9 (categoria opcional), seções 4 e 5.

# 2. O que você decidiu sobre a DeRE

| Pergunta | Sua resposta (22/10/2026) | Efeito |
|-----------------|----------------------------------------------|-------------------------------------|
| Q96-1 | A linha da DeRE aponta um **valor** e a **conta contábil** a que ele se refere. A conta pode ser de resultado, ativo ou passivo, sem restrição pelo tipo. O valor da dedução ou o valor a tributar (valor base) é **informado pelo usuário**. O ERP confere a soma contra o valor da conta e avisa se der diferente, maior ou menor. É sempre a movimentação do período, sem os lançamentos de encerramento. | Desenho da seção 3 |
| Q96-2 | Pode criar a entidade mensal; as informações são sempre de **um período (mês)**. | Entidade por mês |
| Q96-3 | A repartição de uma conta redutora entre contas de receita **perdeu o sentido**. | Sai `Mov_Dere_Deducao_Alocacao` |
| Q96-10 | O usuário informa o `codTrib` na linha, preenchido a partir do mapeamento da conta quando houver. | `ID_Cod_Trib` na linha; saem `Regra_Redutor` e `ID_Redutor` |
| Q96-11 | A conferência é **isolada por tipo**: a soma dos valores base tem de bater com a conta, e a soma das deduções também; não se soma base com dedução. | Duas conferências por conta |
| Q96-12 | A movimentação segue a **natureza da conta** no plano de contas (devedora: débitos menos créditos; credora: créditos menos débitos), sem lançamentos de encerramento, para conta de qualquer tipo. | Fórmula da seção 3.3 |
| Q96-4, Q96-13, Q96-14 | Lançamento com tipo normal, encerramento ou extemporâneo; no extemporâneo, o período a que se refere; o lote tem um só tipo, um só período e uma só data. | **Já na revisão 20** |

# 3. Proposta: entidade mensal única da DeRE

## 3.1 O que muda em relação à primeira versão

- **Sai:** `Mov_Dere_Conta_Redutora_Mes`, `Mov_Dere_Deducao_Alocacao`, os campos `Regra_Redutor` e `ID_Redutor` no mapeamento da conta e o valor novo `encerramento_resultado` no domínio (o domínio já tem `encerramento`, na revisão 20).
- **Fica como está:** `Cad_Redutor_Base_Dere` (o percentual do redutor é parâmetro da lei, com vigência), `Cad_Cod_Trib_Dere` e `Cad_Conta_Contabil_Cod_Trib_Dere`.
- **Entra:** `Mov_Dere_Linha_Mes`, abaixo.

## 3.2 `Mov_Dere_Linha_Mes` (Contabilidade & Fiscal, sem vigência)

Uma linha por empresa, mês, conta contábil, tipo de informação e `codTrib`.

| Campo | Tipo | Observação |
|---------------------|------------------------------------|-------------------------------------------|
| `ID_Dere_Linha_Mes` | identificador | Chave. |
| `ID_Empresa` | referência (`Cad_Empresa`) | Identidade. |
| `ID_Periodo_Referencia` | referência (`Cad_Periodo_Fechamento`, bloco contabilidade) | Identidade. O mês da DeRE. |
| `ID_Conta_Contabil` | referência (`Cad_Conta_Contabil`) | Identidade. Qualquer tipo de conta: resultado, ativo ou passivo (Q96-1). |
| `Tipo_Informacao` | enumeração {valor_base, deducao} | Identidade. Valor a tributar ou dedução. |
| `ID_Cod_Trib` | referência (`Cad_Cod_Trib_Dere`), opcional | Identidade quando preenchido. Vem do mapeamento `Cad_Conta_Contabil_Cod_Trib_Dere` quando houver, e o usuário confirma ou informa (Q96-10). |
| `Valor_Informado` | número | O valor que o usuário informa e que vai à DeRE. |
| `Valor_Movimentacao_Conta` | número | Calculado: movimentação do mês da conta, pela natureza dela, sem lançamentos de encerramento (seção 3.3). |
| `Valor_Encerramento_Excluido` | número | Calculado: o que o encerramento lançou no mês e foi retirado da movimentação; só para o usuário conferir. |
| `Valor_Total_Informado_Tipo` | número | Calculado: soma de `Valor_Informado` das linhas da mesma empresa, mês, conta e tipo. |
| `Valor_Diferenca_Conferencia` | número | Calculado: `Valor_Total_Informado_Tipo` menos `Valor_Movimentacao_Conta`. Positivo: informou a mais; negativo: informou a menos. |
| `Possui_Diferenca_Conferencia` | booleano | Ligado quando a diferença não é zero. **Só avisa**, não bloqueia a geração (Q96-1 e a decisão de 21/10). |
| `Data_Hora_Conferencia` | data/hora | Quando o ERP calculou a conferência. |
| `ID_Usuario_Informacao` | referência (`Cad_Usuario`) | Quem informou o valor. |
| `Data_Hora_Informacao` | data/hora | Quando informou. |

O campo de diferença pode ficar negativo, mas **não leva** `Com_Sinal`: o sufixo vale só para a ECF (D-N326), e a DeRE é outra obrigação. Se você quiser o sufixo também aqui, é só dizer.

## 3.3 Como a conferência é calculada

# 1. **Movimentação do mês da conta** = soma dos lançamentos da conta no mês (por `Data_Lancamento`), **menos** os lançamentos do tipo `encerramento` (e o estorno de um encerramento, que também é desse tipo). Conta devedora: débitos menos créditos. Conta credora: créditos menos débitos. 2. **Conferência por tipo**, isolada: para cada conta e tipo, a soma dos `Valor_Informado` é comparada com a movimentação da conta. O valor base é conferido sozinho, e a dedução também, sem somar uma na outra. 3. **Diferença:** qualquer diferença, para mais ou para menos, liga o aviso; o usuário decide se envia assim.

## 3.4 Contagem se você aprovar

| | Revisão 20 | Com esta proposta |
|---------------------------|-----------------------------|--------------------------------------------|
| Entidades | 915 | 916 |
| Campos | 9.878 | 9.893 (15 novos) |
| Domínios | 272 | 272 |

# 4. Ligação entre a operação e a categoria do crédito presumido (Q96-8 e Q96-9)

**Como entendo o seu "é a operação da nota que indica qual".** A nota traz o código do crédito presumido (`cCredPres`), hoje em `Mov_Apuracao_Tributo_Item_Complemento.Codigo_Classificacao` (texto). O código é cadastrado em `Cad_Credito_Presumido_Ibs_Cbs` e aponta para a categoria (`ID_Categoria_Credito_Presumido`), e a categoria guarda coeficiente, ressarcimento e vigência. Então **não precisa campo novo na nota**: o Motor lê o código da operação, acha a categoria e aplica. Você confirmou só que a empresa pode ter várias categorias; a ligação 1:1 não foi confirmada.

**Risco que vi no que eu mesmo desenhei.** `ID_Categoria_Credito_Presumido` ficou **obrigatório** no código, e o domínio só tem quatro categorias. A tabela cCredPres tem 13 códigos (01 a 13, IT 2025.002 v1.70). Se algum deles não for de produtor rural, resíduos, bens usados ou transportador autônomo, o campo obrigatório me força a classificar errado. Duas saídas: tornar o campo opcional, ou ampliar o domínio com uma categoria para os demais. Recomendo opcional, porque não vou inventar a categoria dos códigos que não conheço.

# 5. Perguntas para você

| Nº | Pergunta | Recomendação |
|---------|--------------------------------------------------------------|-----------------------------|
| Q96-7 | Escrever "Tipo NS (numérico com sinal)" na `Descricao` dos 34 campos NS da carga do leiaute da ECF, sem mudar o nome do campo do leiaute? | Sim |
| Q96-8 | A ligação operação → código → categoria do crédito presumido (seção 4) é a que você quis? | Sim, sem campo novo na nota |
| Q96-9 | `ID_Categoria_Credito_Presumido` passa a opcional (seção 4)? | Sim |
| Q96-15 | Aprova a entidade `Mov_Dere_Linha_Mes` e os 15 campos da seção 3.2? | Sim |
| Q96-16 | A movimentação do mês conta o lançamento extemporâneo no mês em que ele foi **lançado** (regra da revisão 41: compõe o período aberto) e não no período a que se refere? | Sim, no mês lançado |
| Q96-17 | Guardar o cálculo da conferência na própria linha (movimentação, total, diferença e aviso), como o resto do dicionário faz com valores calculados, em vez de recalcular a cada consulta? | Guardar |

# 6. Limites

Não executei cálculo da DeRE: não há dados de cliente nem apuração desenhada. A apuração completa da DeRE (o que vai ao arquivo, por `codTrib`) continua na fila do documento 94 (bloco B4); esta entidade cobre só o valor informado pelo usuário e a conferência contra a conta. A fórmula da movimentação é a leitura das suas respostas.
