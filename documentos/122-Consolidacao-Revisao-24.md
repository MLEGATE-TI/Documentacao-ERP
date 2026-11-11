# Consolidação da Revisão 24 — Documento 122

*Relatório do que entrou no dicionário com o seu "aplicar tudo que está pendente para aplicar e consolidar" de 26/10/2026, do que ficou de fora e de como conferi. A revisão 24 aplica o que você respondeu **e cujos campos você viu**: as respostas dos documentos 93 e 96 (Q93 e Q96, que estavam sem registro por erro meu), a moeda estrangeira do título e da baixa (Q101-1, Q101-8 a Q101-8g, documentos 119 a 121) e a regra do adiantamento em moeda (Q101-10, só como texto). Entram **3 entidades, 2 campos novos e 1 valor de domínio**, mais o texto de 20 campos em 11 entidades. O que não foi respondido, ou cujo campo você ainda não viu, **não altera o dicionário**; a lista está no documento 38.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

| | Revisão 23 | Revisão 24 | Diferença |
|---|---:|---:|---:|
| Entidades | 922 | 925 | **+3** |
| Campos | 9.998 | 10.033 | **+35** |
| Campos de referência (FK) | 2.685 | 2.696 | **+11** |
| Referências genéricas | 50 | 50 | 0 |
| Valores de `Cad_Classe_Sistema.Dominio` | 273 | 274 | **+1** (`indicador_aliquota_csll_ecf`) |
| Entidades mestres (identidade e versão) | 186 | 186 | 0 |
| Campos com texto alterado | | | **20**, em 11 entidades |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.108 / 2.871 / 2.943 / 8.054 | 1.111 / 2.882 / 2.954 / 8.087 | +3 / +11 / +11 / +33 |
| Comandos T-SQL lidos pelo analisador | 14.977 | 15.035 | +58 |
| Linhas da carga das tabelas dinâmicas da ECF | 4.475 | 4.486 | +11 |

Dos 35 campos novos, 33 estão nas três entidades novas e 2 em entidades que já existiam (`Mov_Titulo_Baixa.Valor_Arredondamento_Com_Sinal` e `Mov_Apuracao_Irpj_Csll.Base_Estimativa`).

Auditoria: **0 achados** na primeira passada. **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.111 tabelas, 2.882 chaves estrangeiras e 8.087 comentários conferidos no banco. O T-SQL foi só lido pelo analisador (sqlglot), sem erro de leitura; não foi executado num SQL Server.

Módulos alterados: Fase 0 (revisão 72), Contas a Pagar/Receber (20) e Contabilidade & Fiscal (42). Tesouraria não mudou e fica na revisão 11.

# 2. Como li o "consolidar"

Você escreveu "aplicar tudo que está pendente para aplicar e consolidar". Mantive a regra do projeto: entra o que você respondeu **e cujos campos você já viu**. Onde a resposta pedia uma leitura minha, ela está abaixo; **se alguma estiver errada, diga e eu corrijo na revisão 25**.

- **Q93 e Q96 entram** (D-N365 e D-N366): você respondeu em 22/10/2026 e eu não tinha registrado (documento 118, seção 9). Os campos das três entidades novas já tinham sido apresentados nos documentos 93, 96 e 118.
- **"Sim para três" (Q101-8f1, 8f2 e 8f3)** foi lido como **sim às três**: o campo de arredondamento está aprovado, acima de R$ 0,04 a baixa não é confirmada e o valor do campo é lançado no lote numa conta de resultado parametrizada (D-N364).
- **"0,04 centavos"** (Q101-8b) foi lido como **R$ 0,04**, para mais ou para menos, sem percentual, e como **parâmetro** com esse valor de partida, e não como constante.
- **Q101-8d** (sem aprovação do banco, o item fica pendente e não há baixa) foi lida como cobrindo também o retorno que vem sem a taxa do contrato.
- **Q101-8e** (desconto e juros em moeda, convertidos pela taxa de câmbio) foi lida como a **taxa da baixa**, a do contrato de câmbio ou, sem contrato, a de referência; a variação cambial incide só sobre o valor baixado.
- **Q101-1 ("seguir com todas as sugestões")** foi lida como a recomendação do documento em cada pergunta; **a precisão de 8 casas** foi aplicada só à cotação da série (`Mov_Serie_Cotacao_Valor.Valor`), e não como decisão geral do mapa de precisão numérica.
- **Q101-10** (reavaliar o adiantamento em moeda todo mês, a sua escolha depois da pergunta de esclarecimento) entra **só como regra escrita** no campo de moeda do crédito. A entidade do documento 120 **não entra**, porque você não respondeu à Q101-10a a Q101-10c.
- **Q93-2:** a leitura `M350(344)` está aplicada na linha M350A 171. A M350R 345 também está com o número da tabela faltando (`M(170)`), mas **a leitura `M350(344)` não serve para ela** (a linha 344 já está na fórmula); a leitura por simetria é `M350(170)`, que é minha e você não confirmou. **Deixei a M350R 345 como publicada** e registrei na pendência da carga (seção 5; pergunta Q122-1 no documento 38).

# 3. O que entrou

| Onde | O que mudou | Decisão |
|---|---|---|
| `Mov_Ecf_Apuracao_Linha_Valor` (**nova**, 10 campos) | O valor de cada linha de tabela dinâmica da ECF por apuração (a cadeia do lucro real): o valor em `Valor_Com_Sinal`, a origem (cálculo, lançamento, manual ou importado), o valor calculado quando o contador altera, e quem alterou, quando e por quê | D-N365, Q93-3 |
| `Mov_Ecf_Escolha_Contador_Ano` (**nova**, 8 campos) | O que o contador escolhe por empresa e ano para o registro 0020 da ECF: o indicador de alíquota da CSLL (`IND_ALIQ_CSLL`, domínio `indicador_aliquota_csll_ecf`) e a quantidade de SCP (`IND_QTE_SCP`). A chave primária se chama `ID_Escolha_Contador_Ano` | D-N365, Q93-5 e Q93-5d |
| `Mov_Dere_Linha_Mes` (**nova**, 15 campos) | A DeRE numa entidade mensal única: uma linha por empresa, mês, conta contábil, tipo de informação (valor base ou dedução) e `codTrib`; o valor é informado pelo usuário e o cálculo da conferência contra a movimentação da conta fica guardado na linha | D-N366, Q96-1 a Q96-3, Q96-10 a Q96-12, Q96-15 a Q96-17 |
| `Cad_Classe_Sistema.Dominio` | Novo valor **`indicador_aliquota_csll_ecf`** (e a linha correspondente no anexo do documento 01) | D-N365, Q93-5 |
| `Mov_Apuracao_Irpj_Csll.Base_Estimativa` (**campo novo**) | Enumeração opcional: `receita_bruta` ou `balancete_reducao`. Texto de `Tipo_Apuracao` ajustado | D-N365, Q93-3 |
| `Mov_Titulo_Baixa.Valor_Arredondamento_Com_Sinal` (**campo novo**) | Número com sinal, opcional: a diferença de até R$ 0,04 entre o extrato e o valor calculado; positivo quando o extrato mostra mais; fora do Y520; a conciliação soma o campo ao `Valor_Financeiro` | D-N363 e D-N364, Q101-8f |
| `Mov_Titulo` (texto de 6 campos) | `Valor_Titulo` (valor estimado em reais), `ID_Moeda_Titulo`, `Valor_Titulo_Moeda`, `Taxa_Estimada` (sugerida da série, editável só até o primeiro movimento), `Data_Taxa_Estimada` (dia da cotação usada) e `Referencia_Operacao` (número do contrato de câmbio). O texto passa a dizer "confirmado" | D-N360 e D-N362, Q101-1 e Q101-8a |
| `Mov_Titulo_Baixa` (texto de 5 campos) | `Valor_Desconto` e `Valor_Juros_Multa` (na moeda do título, convertidos pela taxa da baixa), `Taxa_Cambio` (do contrato; de referência, obrigatória, na baixa sem dinheiro), `Valor_Pago_Reais` (tolerância de R$ 0,04; variação cambial na baixa sem dinheiro) e `Valor_Financeiro` (soma do arredondamento) | D-N361 a D-N364, Q101-8 a Q101-8g |
| `Mov_Titulo_Reprogramacao_Item.Valor_Reprogramado` | Texto: o título novo da renegociação nasce com a taxa em que o saldo antigo estava contabilizado | D-N360, Q101-1d |
| `Mov_Credito.ID_Moeda_Credito` | Texto: o adiantamento em moeda é reavaliado todo mês; a variação cambial é calculada. Sem entidade nova | D-N361, Q101-10 |
| `Mov_Serie_Cotacao_Valor.Valor` | Texto: **8 casas decimais**. No DDL o campo sai como `numeric(19,8)` (exceção no gerador; os demais campos chamados `valor` continuam `numeric(19,4)`) | D-N360, Q101-1e |
| `Cad_Ecf_Tabela_Dinamica_Linha.Formula` | Texto: fórmulas com duas versões em duas linhas por vigência; correção do `M(344)` | D-N365, Q93-1 e Q93-2 |
| `Cad_Obrigacao_Leiaute_Campo.Descricao` | Texto: nos 34 campos NS a descrição começa com "Tipo NS (numérico com sinal)" | D-N366, Q96-7 |
| `Mov_Apuracao_Tributo_Item_Complemento.Codigo_Classificacao` | Texto: a cadeia `cCredPres` não ganha campo novo | D-N366, Q96-8 |
| `Cad_Credito_Presumido_Ibs_Cbs.ID_Categoria_Credito_Presumido` | Texto: categoria opcional (o campo já era opcional desde a revisão 19) | D-N366, Q96-9 |
| Carga da ECF (pacote Carga24-ECF) | 11 fórmulas divididas, 4.475 para 4.486 linhas; M350A 171 corrigida; "Tipo NS" nos 34 campos; pendências do leiaute de 205 para 171 linhas | D-N365 e D-N366 |

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Q93-6** (indicador de atividade rural no perfil) | Você decidiu o campo; **o desenho do campo ainda não foi escrito** e você não o viu | Documento 38, seção 0 |
| **Q93-3b, Q93-7 e Q93-8** (rastro do cálculo, linhas do imposto devido, escopo das linhas editáveis) | Sem resposta | Documento 38 |
| **Q118-1, Q118-2 e Q118-3** (S200 90, linha `16.001` da N630A 18, conferência das fórmulas de 2026 contra a lei) | Sem resposta | Documento 38 |
| **`Mov_Credito_Reavaliacao`** (documento 120, Q101-10a a Q101-10c) | Sem resposta; a regra entrou só como texto | Documentos 120 e 38 |
| **Q113-4, Q113-5, Q113-8, Q113-9 e Q113-11** | Sem resposta ou campos não aprovados | Documento 38 |
| **Documento 116** (qualificação do participante, B2) | Q116-1 a Q116-8 sem resposta | Documentos 116 e 38 |
| Q94-2 a Q94-7, Q99, Q107, Q98 (consulta à Receita, que é sua) e demais | Sem resposta ou com o contador | Documento 38 |

# 5. Pontos de atenção

- **A chave primária de `Mov_Ecf_Escolha_Contador_Ano` se chama `ID_Escolha_Contador_Ano`**, e não o nome que o rascunho do documento 93 usava; é o nome pelo padrão do dicionário.
- **A marca "confirmar" dos campos de moeda.** Os documentos 101 e 119 dizem que a revisão 21 pôs a marca "confirmar" nesses campos, mas no texto da revisão 23 **não achei a palavra** nos campos de `Mov_Titulo` e `Mov_Titulo_Baixa`. Nesta revisão o texto passa a dizer "confirmado" e a regra decidida (Q101-1 e Q101-8); se a marca existir em algum lugar que eu não vi, ela precisa sair.
- **A carga é provisória até o contador validar.** O dividir das 11 fórmulas segue a regra da Q93-1; a conferência das fórmulas de 2026 contra a lei (Q118-3) **não foi feita**. Linhas de outros perfis com duas versões ficam como publicadas: P200 26, P400 21 e S200 90, porque a Q93-1 tratou só das tabelas do Lucro Real (N610, N620 e N630).
- **M350R 345 (pendência nova na carga, Q122-1 no documento 38):** a fórmula publicada é `M350(343) - M350(344) + M(170)`. A leitura por simetria é `M350(170)` (a M350A 171 soma a linha 344 da M350R, e a M350R 345 soma a linha 170 da M350A, porque a numeração do M350 é única entre as abas A e R); basta corrigir a linha se você concordar. **Não corrigi porque a sua confirmação foi só do `M(344)` e esta leitura é minha**.
- **A conta de resultado do arredondamento** (Q101-8f3) é do contador; o campo e a regra existem, a conta não.
- **A tolerância de R$ 0,04** é parâmetro com vigência, como os demais valores legais e técnicos.
- **O gerador do DDL ganhou uma exceção de precisão** (`Mov_Serie_Cotacao_Valor.Valor` em `numeric(19,8)`); o mapa geral de precisão (D-5 do documento 31) não mudou.
- **Doc 31:** na seção da onda 6, o texto dizia "Folha & RH (123)" enquanto a tabela já dizia 129 entidades na onda; **corrigi para 125** (4 dos Motores Transversais e 125 da Folha). Era um defeito de texto de revisões anteriores, sem mudar a estrutura.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois campo a campo. Entraram exatamente 3 entidades (10, 8 e 15 campos), 2 campos novos, 1 valor de domínio e o texto de 20 campos em 11 entidades, todos listados na seção 3. Nenhum campo foi removido e nenhuma entidade mudou de módulo.
- **Auditoria:** 0 achados na primeira passada, sobre os Markdown regerados.
- **DDL:** gerado nos dois dialetos (1.111 tabelas, 2.882 chaves estrangeiras, 2.954 índices e 8.087 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e conferi no banco `mov_serie_cotacao_valor.valor` em `numeric(19,8)` e `mov_titulo_baixa.valor_arredondamento_com_sinal` em `numeric(19,4)`.
- **T-SQL:** 15.035 comandos lidos por analisador de sintaxe, sem erro de leitura. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos, com diagramas novos, porque 11 referências mudaram.
- **Carga da ECF:** regerei primeiro a carga da revisão 19 e comparei linha a linha: as 4.475 linhas antigas continuam todas lá; mudaram só as 11 divididas e a M350A 171. Os arquivos do plano referencial, das contas, das tabelas dinâmicas e da Parte B são idênticos aos da revisão 19; no leiaute só mudou a `Descricao` dos 34 campos NS.
- **Limites:** nada foi validado pelo contador; a conta do arredondamento, a variação cambial da baixa sem dinheiro e as fórmulas de 2026 são dele.
