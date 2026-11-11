# Consolidação da Revisão 34 — Documento 186

*Relatório do que entrou no dicionário com o seu "consolidar" de 09/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava no dicionário**: o B3 (documento 158, D-N478), a transação de cartão (documento 177, D-N485), o núcleo da ECD (documento 183, D-N495), o desenho do documento 184 (D-N496 e D-N498) e a carga de cClass da NFGás (Q184-14).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 33 | Revisão 34 | Diferença |
|---|---|---|---|
| Entidades | 1.107 | 1.135 | +28 |
| Campos | 12.406 | 12.739 | +333 |
| Campos de referência (FK) | 3.242 | 3.337 | +95 |
| Entidades mestres | 217 | 224 | +7 |
| Referências genéricas | 61 | 61 | 0 |
| Domínios de `Cad_Classe_Sistema` | 334 | 340 | +6 |
| Tabelas físicas (DDL) | 1.324 | 1.359 | +35 |
| Chaves estrangeiras (DDL) | 3.459 | 3.561 | +102 |
| Índices (DDL) | 3.547 | 3.652 | +105 |
| Comentários (DDL) | 10.268 | 10.561 | +293 |
| Comandos do T-SQL | 18.599 | 19.134 | +535 |
| Entidades com FK que espera a onda de destino | 75 | 79 | +4 |

**28 entidades novas** (312 campos) e **14 existentes alteradas** (21 campos novos), distribuídas assim:

| Documento | Entidades novas | Campos nelas | Campos novos em existentes | Entidades existentes alteradas |
|---|---|---|---|---|
| 183 (núcleo da ECD) | 2 | 25 | 3 | 4 (3 com campo novo e `Cad_Participante_Inscricao`, com 5 valores novos) |
| 184 (moeda funcional, subcontas, plano, histórico, relacionamento, bloco K) | 15 | 118 | 5 | 2 |
| 177 (transação de cartão) | 1 | 14 | 2 | 2 |
| 158 (B3: compras governamentais, ZFM e ALC) | 10 | 155 | 9 | 4 (mais o texto do calendário, só no documento 10) |
| cClass da NFGás (Q184-14) | 0 | 0 | 2 | 1 |
| Domínios e habilitações | 0 | 0 | 0 | 1 (`Cad_Classe_Sistema`) |
| **Total** | **28** | **312** | **21** | **14** |

Os 25 campos do documento 183 incluem os 4 que o documento 184 acrescenta a `Mov_Ecd_Periodo`: a entidade entrou com **20 campos**, e não com 16. Os 118 do documento 184 são só das suas 15 entidades. O DDL tem 7 tabelas a mais pelos 7 mestres novos (identidade e versão).

# 2. O que entrou, por documento

## 2.1 Documento 183 e documento 184 (ECD, leiaute 9)

| Onde | Mudança |
|---|---|
| `Mov_Ecd_Periodo` (20 campos) | A identificação da ECD de um arquivo (forma de escrituração, número de ordem, natureza do livro, situação no início do período, encerramento do exercício, arquivamentos, grande porte, tipo da ECD, moeda funcional, descentralizada, plano referencial, motivo e termo da substituição) **mais** `ID_Plano_Empresa`, `Indicador_Mudanca_Plano_Contas`, `ID_Ecd_Periodo_Anterior` e `Indicador_Escrituracao_Consolidada`, que o documento 184 pediu. |
| `Mov_Ecd_Documento_Complementar` (5) | Os arquivos do J800. |
| `Cad_Empresa_Responsavel`, `Cad_Conta_Contabil_Referencial`, `Cad_Estrutura_Demonstrativo_Linha` | `Codigo_Cvm_Auditor`, `ID_Valor_Centro_Custo` e `Referencia_Nota_Explicativa`. |
| `Cad_Participante_Inscricao.Tipo_Inscricao` | Cinco valores: `bacen`, `susep`, `cvm`, `antt` e `tse`. |
| Moeda funcional | `Mov_Saldo_Contabil_Base` (9 campos) e três campos em `Mov_Lancamento`: `Valor_Moeda_Nacional`, `Valor_Funcional_Em_Reais` e `Taxa_Conversao_Reais`. |
| Subcontas e razão auxiliar | `Cad_Subconta_Contabil` (mestre, 9), `Mov_Agio_Composicao` (7), `Mov_Item_Subconta` (11) e `Mov_Subconta_Movimento` (12). O AVP só se registra, sem cálculo. |
| Plano de contas | `Cad_Plano_Contas_De_Para` (10, o I157) e `Finalidade` {individual, consolidado} em `Cad_Plano_de_Contas`. |
| Histórico e relacionamento | `Cad_Historico_Padrao` (mestre, 8) e `ID_Historico_Padrao` em `Mov_Lancamento` (o `Historico` passa a ser o complemento); `Cad_Participante_Relacionamento` (mestre, 8; a vigência da versão é o período do relacionamento). |
| Bloco K | `Cad_Conta_Consolidada_Mapa` (mestre, 9) e seis entidades de movimento: `Mov_Ecd_Consolidacao_Empresa` (9), `_Evento` (5), `_Evento_Participante` (5), `_Saldo` (6), `_Saldo_Parte` (4) e `_Eliminacao` (6). |
| Habilitação por empresa | Três valores novos em `modulo_fiscal_opcional`: `ecd_moeda_funcional`, `ecd_subcontas_ras` e `ecd_consolidada`. Sem lista de empresas (Q184-3, 5 e 11): a opção fica pronta para quando for preciso. |

## 2.2 Documento 177 (cartão)

`Mov_Transacao_Cartao` (14 campos, sem vigência) e `ID_Transacao_Cartao` (opcional) em `Mov_Nota_Fiscal_Saida_Pagamento` e em `Mov_Titulo_Baixa`. A data prevista de repasse é o vencimento do título da parcela e a de crédito é a da baixa; nenhuma ganha campo. O 1601 de cartão usa `Data_Autorizacao` e `Valor_Bruto`.

## 2.3 Documento 158 (B3)

| Onde | Mudança |
|---|---|
| Compras governamentais | `Cad_Regra_Compra_Governamental` (mestre, 22 campos); em `Mov_Nota_Fiscal_Saida_Compra_Governamental`, `ID_Regra_Compra_Governamental`, `Indicador_Aquisicao_Presencial` e `Indicador_Dispensa_Licitacao`, e o texto de `Percentual_Redutor` (art. 472, e não 473). |
| ZFM e ALC, cadastro | `Cad_Area_Incentivada` (mestre, 14), `Cad_Area_Incentivada_Municipio` (10), `Cad_Habilitacao_Suframa` (13), `Cad_Habilitacao_Suframa_Produto` (11), `Mov_Habilitacao_Suframa_Ocorrencia` (11) e `Cad_Zfm_Alc_Regra` (mestre, 27). |
| ZFM e ALC, operação | `Mov_Zfm_Alc_Internamento` (16), `Mov_Zfm_Alc_Importacao_Suspensao` (19) e `Mov_Zfm_Credito_Ibs_Periodo` (12). |
| `Mov_Credito_Presumido_Zfm` | +6 campos (`ID_Nota_Fiscal_Entrada_Item`, `Origem_Credito`, `ID_Zfm_Alc_Regra`, `ID_Habilitacao`, `ID_Credito`, `ID_Zfm_Credito_Ibs_Periodo`); `ID_Apuracao_Origem`, `Percentual_Credito_Cbs` e `ID_Calendario` passam a opcionais; texto de `Tipo_Area` e `Percentual_Credito_Ibs` corrigido. |
| `Mov_Credito_Fiscal`, `Cad_Habilitacao_Regime_Especial` | Valor `presumido_zfm_alc` em `Origem`; texto de `ID_Participante_Titular`. |
| `Cad_Calendario_Transicao` | Parâmetro `redutor_compras_governamentais` (sem linhas até a resolução do Senado) e texto do `percentual_credito_zfm`: o fator de 2029 a 2032 vale só para os créditos dos arts. 447, 449 e 465. |

## 2.4 cClass da NFGás (Q184-14)

`Cad_Utilidade_Classificacao_Efd` ganha `Cbs_Zero_Zfm_Alc` e `Fatura_Agregadora` (booleanos, opcionais), e o domínio `classificacao_item_nfgas` recebe os 46 códigos.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Regra_Compra_Governamental` | 42 | 6 tipos de ente em 7 janelas, pelo art. 372 da LC 214 |
| `Cad_Area_Incentivada` | 7 | ZFM e seis ALC; fim dos benefícios em 31/12/2073 (provisório) |
| `Cad_Area_Incentivada_Municipio` | 12 | Município por nome e UF; o `ID_Municipio` sai de `Cad_Municipio` |
| `Cad_Zfm_Alc_Regra` | 23 | 15 da ZFM e 8 das ALC |
| `Cad_Classe_Sistema` (valores novos) | 128 | Seis domínios novos (10 + 25 + 11 + 7 + 6 + 10 valores), valores novos em quatro domínios existentes (1 + 1 + 1 + 7), três habilitações e os 46 códigos de cClass da NFGás |
| `Cad_Utilidade_Classificacao_Efd` (NFGás) | 8 | Mapa do grupo para o campo do C500; inferência minha, o contador valida (Q184-C3) |

Total: **220 linhas em 8 arquivos** (pasta `Carga34`). Ficam sem carga: `redutor_compras_governamentais` (aguarda a resolução do Senado), `zfm_alc_bens_excluidos` (lista de NCM do contador) e os cadastros de habilitação da Suframa (do usuário).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: documentos 158, 177, 183 (núcleo) e 184 e a carga de cClass. O **documento 185** (IN RFB 2.316/2026) **não entrou**: as Q185-1 a Q185-4 seguem sem resposta.
2. **`IND_MUDANC_PC` e `IND_ESC_CONS` viraram campo.** O documento 183 dizia que não viravam; o documento 184, que você aprovou inteiro, os acrescenta. Valeu o 184.
3. **`Indicador_Escrituracao_Descentralizada`** ficou como "informado pelo usuário, sem valor oculto". O texto do documento 183 dizia "falso até a Q183-8", mas a sua resposta à Q183-8 trata do bloco K, e não da descentralizada.
4. **cClass da NFGás:** a continuidade (0 a 3) e as marcas do grupo (valor deduzido, CBS zero, fatura agregadora) **vão no texto da descrição** de cada um dos 46 códigos, porque você aprovou "o indicador como atributo do código" e não há campo para ele. Os grupos 030, 060 e 073 ficam **sem linha** em `Cad_Utilidade_Classificacao_Efd` (a tabela não diz para que campo do C500 vão), então `Fatura_Agregadora` é falso em todas as 8 linhas carregadas e a marca do 060 só consta no texto do código; o Motor avisa.
5. **`Permite_Ressarcimento` = falso em todas as 23 linhas** de `Cad_Zfm_Alc_Regra`, inclusive nas que não são crédito presumido, porque o campo é obrigatório e só o crédito presumido o tem em questão (Decreto 12.955, arts. 533 e 540). Os prazos (120 e 210 dias; 48 meses e 180 dias; 60 meses) seguem o Anexo A.5 do documento 158.
6. **Início de vigência das áreas, dos municípios e das regras da ZFM e ALC fica vazio** na carga ("o contador define"): a lei não fixa um início que eu possa copiar sem inventar. As regras de compra governamental levam as datas das janelas do art. 372.
7. **Os rótulos** dos domínios `tipo_documento_ecd`, `motivo_substituicao_ecd`, `plano_referencial_ecd` e `relacionamento_ecd` vêm do manual da ECD e do documento 184; os da `natureza_subconta_ecd`, da tabela do I053, com a conta principal e o fundamento legal no texto.
8. **`ID_Plano_Empresa` é obrigatório em `Mov_Ecd_Periodo`**: toda ECD tem um plano de contas no período.
9. **Os avisos do Motor continuam registrados e não programados**: 12 do documento 183, 8 novos e os já citados do 184 (seção 9), 3 do 177 e os critérios do 158 (7 valores de `campo_criterio_regra`). O texto das regras está no anexo da seção 47 do documento 10.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto nos documentos | 28 entidades e 312 campos novos (25 + 118 + 14 + 155) e 21 campos novos em existentes: **12.739** campos e **3.337** referências, como previsto (o documento 184 previa 12.557 e 3.295 só com 183 e 184; somando 158, 177 e a cClass, 12.739 e 3.337) |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.359 tabelas, 3.561 chaves estrangeiras e 10.561 comentários; as colunas novas existem em `mov_lancamento` e em `mov_transacao_cartao` |
| T-SQL (analisador sqlglot, oito arquivos) | Lido sem erro; 19.134 comandos. **Não equivale a executar num SQL Server.** |
| Ondas | 27 entidades novas na onda 3 e 1 na onda 4 (`Mov_Zfm_Alc_Internamento`, que exige a nota de saída); 4 chaves opcionais novas esperam a onda de destino |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** Q185-1 a Q185-4 (documento 185), Q179-1 a Q179-3, a planilha do leiaute 11 (Q152-4), o ato do Confia e o texto do art. 41 da LC 225 (Q180-3), e os textos da Portaria MF 3.074/2026 e da conjunta MF/CGIBS 14/2026.
- **Contador:** Q184-C1 a C3 (AVP e conversão cambial, listas, mapa de grupos da NFGás), Q183-C1, Q185-C1, Q158-C* (entre elas a lista de NCM excluídos) e Q140-6.
- **Receita:** Q140-5b, 5d e 5e (pergunta 26 do documento 179).
- **Fila de desenho:** documento 159 (43 artigos da LC 227 e os mal extraídos) e documento 160 (parâmetros das outras obrigações).
- **Indicador de atividade rural** (Q93-6): o desenho da linha do catálogo de parâmetros ainda não foi feito.

# 7. Limites

- A tabela de cClass não traz a fonte (ato ou nota técnica) e o mapa dos grupos para o C500 é inferência minha.
- O texto da LC 225 e a planilha da ECF seguem fora do meu ambiente.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1, 8 e 10 do dicionário seguem na versão anterior no Project e estão atualizados nos Word desta entrega.
