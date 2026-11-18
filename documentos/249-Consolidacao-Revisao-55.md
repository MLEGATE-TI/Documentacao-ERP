# Consolidação da Revisão 55 — Documento 249

*Você escreveu "consolidar". Li como nas últimas consolidações: **tudo o que estava aprovado e sem aplicar**, ou seja, o desenho da depreciação do ativo (documento 247, D-N631 a D-N635) e o das vidas úteis fiscais do Anexo III da IN 1.700 (documento 248, D-N636 e D-N637). **Se não era isso, me diga que eu desfaço** (a revisão 54 está guardada). Antes de aplicar, achei um **erro meu** sobre as "12 linhas" da carga do decreto; ele está na seção 3 e muda uma das suas aprovações.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 54** | **Revisão 55** | **Diferença** |
|---|---|---|---|
| Entidades | 1.243 | **1.249** | +6 (5 em Motores Transversais e 1 em Contabilidade & Fiscal) |
| Campos | 14.460 | **14.529** | +69 (66 nas entidades novas, 3 em `Cad_Ativo_Imobilizado`; o campo renomeado não muda a conta) |
| Campos de referência (FK) | 3.706 | **3.721** | +15 |
| Entidades mestres | 266 | **269** | +3 (as três novas com tabela de versão) |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 (os 4 valores novos do Motor são dado, na Carga55) |
| Tabelas físicas (DDL) | 1.509 | **1.518** | +9 (6 entidades e 3 tabelas de versão) |
| Chaves estrangeiras (DDL) | 3.972 | **3.990** | +18 |
| Índices (DDL) | 4.064 | **4.082** | +18 |
| Comentários (DDL) | 12.200 | **12.263** | +63 |
| Comandos do T-SQL | 21.746 | **21.854** | +108 |
| Chaves opcionais que esperam a onda de destino | 87 | **90** | +3 (a linha do grupo de bem aponta para a tabela fiscal; o ajuste de valor, para a subconta; o ativo, para a taxa da CBS) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Motores Transversais 99, Contabilidade & Fiscal 72 | Motores Transversais **100**, Contabilidade & Fiscal **73** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.518 tabelas, 3.990 chaves estrangeiras, 12.263 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Decisão** | **Onde ficou no dicionário** |
|---|---|
| n tipos de depreciação em paralelo, com contabilização por tipo (D-N631 a D-N633) | **`Cad_Tipo_Depreciacao`** (15 campos, vigência): finalidade, cálculo (linear, por turnos, integral no ano, com multiplicador), residual, ajuste de valor, se lança e o fundamento legal. Carga de 4 tipos: GERENCIAL, FISCAL, ACELERADA e INCENTIVADA_RURAL. `Mov_Ativo_Depreciacao.Tipo_Depreciacao` (lista fixa) vira **`ID_Tipo_Depreciacao`** (referência). |
| A parametrização fica no grupo de bem e o ativo herda (C368, C373) | **`Cad_Ativo_Imobilizado_Classe_Depreciacao`** (12 campos, vigência): uma linha por grupo e tipo, com vida, residual, marca de principal, referência ao anexo (`ID_Taxa_Depreciacao_Fiscal`) e justificativa. **`Cad_Ativo_Imobilizado_Depreciacao_Parametro`** (6 campos): só a exceção por ativo. |
| Início, turnos e CBS no ativo (C365, C367, Q247-7) | `Cad_Ativo_Imobilizado`: **+3 campos**, opcionais: `Data_Inicio_Depreciacao`, `Coeficiente_Turnos` e `ID_Taxa_Depreciacao_Cbs`. |
| Redução ao valor recuperável e reavaliação (Q247-11, Q247-12, C370) | **`Mov_Ativo_Ajuste_Valor`** (11 campos): o ERP só registra o valor informado; a depreciação gerencial recalcula daí para frente. |
| Pausas, inclusive a fiscal (Q247-13, C369) | **`Mov_Ativo_Depreciacao_Pausa`** (6 campos). Sem quota fiscal no mês, sem crédito de PIS e Cofins do bem (leitura minha, o contador confirma). |
| Outras acelerações incentivadas (Q247-14, C371) | Nenhuma estrutura nova: entram como linhas novas de `Cad_Tipo_Depreciacao`; nenhuma carregada. |
| Tabela de vidas úteis fiscais, Anexo III da IN 1.700 (Q248-1 a Q248-3, C372) | **`Cad_Taxa_Depreciacao_Fiscal`** (16 campos, vigência), separada de `Cad_Taxa_Depreciacao_Cbs`. Carga de 222 linhas, provisória (220 do anexo e as notas (1) e (2)). |
| Nota (3) e notas (1) e (2) (Q248-5, Q248-6, C373) | Notas (1) e (2) são linhas com `Condicao_Uso`, escolhidas pelo grupo; o componente sem `Data_Inicio_Depreciacao` não deprecia (só depois de incorporado). |
| F120 e F130 (C366, C368) | `Cad_Ativo_Direito_Credito_Pis_Cofins.ID_Base_Credito` ganha texto: o F120 lê o tipo marcado como **fiscal principal** do grupo. Li o "F200" que você escreveu como F120 (**a confirmar**). |

# 3. Erro meu sobre as "12 linhas" do Anexo I do decreto

Nos documentos 248 (versões 1 e 2) e na D-N636 e D-N637, eu disse que **12 linhas do Anexo I do Decreto 12.955 ficaram de fora da carga da CBS por falha minha**, e você aprovou a Q248-4 ("correção das 12 linhas, 208 para 220") com essa premissa. Ao preparar a carga vi que isso estava **errado para 10 das 12**:

- **Itens 1 e 2 (instalações, 10 anos, 10%; edificações, 25 anos, 4%): falha minha.** Não têm NCM, têm prazo e taxa no Diário Oficial, e a Carga52 leu que não tinham (o LEIA-ME dela repetiu isso). **Entraram:** a tabela `Cad_Taxa_Depreciacao_Cbs` passa de 208 para **210** linhas.
- **Dez itens com NCM que não existe mais na tabela de 16/11/2026 (4204, 8469, 8470.40, 8520, 8524.3, 8524.40, 8524.5, 8524.60, 8903.10 e 9009): decisão sua, Q239-3.** Você aprovou que NCM de lista oficial que não existe mais na tabela não entra na carga, porque a chave estrangeira falharia. **Mantive-as fora** da tabela da CBS. Elas estão na tabela fiscal de vidas úteis, com a chave de NCM vazia e o código só em texto (`NCM_na_Tabela`), então a informação não se perde.

**Você decide:** manter assim (recomendo, coerente com a Q239-3) ou carregar também as 10 na tabela da CBS com a chave vazia (o crédito da cooperativa não acharia a taxa pelo NCM). A correção dos textos está nos documentos 248 (versão 3), 14 (D-N636, D-N637 e D-N638), 38 e 188 (C372).

# 4. A Carga55

| **Pasta** | **Conteúdo** | **Linhas** |
|---|---|---|
| 01-tipos-depreciacao | `Cad_Tipo_Depreciacao`: GERENCIAL (lança), FISCAL, ACELERADA (base FISCAL) e INCENTIVADA_RURAL; vigência desde 16/03/2017 (leitura minha) | 4 |
| 02-vidas-uteis-fiscais | `Cad_Taxa_Depreciacao_Fiscal`: Anexo III da IN 1.700 com as notas (1) e (2); as 10 linhas de NCM obsoleto sem chave; 148 de 10 anos, 44 de 5, 8 de 4, 6 de 3, 6 de 20, 5 de 25 e 5 de 2 | 222 |
| 03-correcao-cbs | `Cad_Taxa_Depreciacao_Cbs`: itens 1 e 2 do Anexo I do decreto (corrige a Carga248 anterior, que propunha 12) | 2 |
| 04-dominios-motor | `Cad_Classe_Sistema`: `depreciacao_ativo` (área) e `tipo_depreciacao`, `classe_ativo` e `centro_custo_ativo` (critérios do Motor de Regras) | 4 |
| 05-conferencia | As 10 linhas do anexo com NCM fora da tabela (não carregar) | 10 |

# 5. Leituras minhas e limites do que apliquei

- **Vigência dos 4 tipos desde 16/03/2017**, a mesma data da tabela fiscal; você não falou de data. Na C372 você não falou da data de início da vigência da tabela fiscal e li "correto" como valendo para a carga inteira.
- **"F200" lido como F120** (depreciação do ativo na EFD-Contribuições). Se for outro registro, é troca de texto.
- **Grupos de bem e regras de conta não foram preenchidos** (C371 e a Q247-9): a empresa liga cada tipo aos grupos; sem regra de conta para o tipo e o grupo, a quota sai sem lançamento e o fechamento do bloco do ativo não conclui.
- **O Anexo III é transcrição do COSIF**, conferida com o decreto no DOU; se a IN teve alteração depois de 2017, o contador diz (C372). Cinco linhas quebram de uma página para a outra e a descrição foi juntada por posição.
- **Unicidade e vigência** das linhas novas (por exemplo, o NCM 3926.90 aparece em duas linhas) são regra do Motor e da carga; o gerador de DDL não cria restrição, como em `Cad_Taxa_Depreciacao_Cbs`.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** as 10 linhas fora da tabela da CBS (seção 3); o "F200 = F120"; a data de início da C372; Q246-2 a Q246-8, Q234-3, Q228-1 e os demais itens do documento 38.
- **Contador:** C365 a C373, respondidas por você, a confirmar.

Próximos números: D-N639, contador C374, documento 250, Q248-7, Q246-9, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.54.
