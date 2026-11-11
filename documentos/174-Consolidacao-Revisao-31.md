# Consolidação da Revisão 31 — Documento 174

*Relatório do que entrou no dicionário com o seu "consolidar" de 04/11/2026, do que ficou de fora e de como conferi. A revisão 31 aplica **só o que você aprovou** (o mesmo escopo da revisão 30): os documentos **157** (B0a: fato gerador, ajuste da operação, acréscimos do art. 27, locação, transição de 2026, entrega do arquivo e cadastro da filial), **150** (B5: gorjeta, cooperativa, locação por temporada e agência de turismo), **170** (combustíveis: catálogo, alíquota por unidade e autorização da ANP) e **173** (programas de apoio aos combustíveis, que substitui o 171). Entram **27 entidades novas (404 campos no modelo)**, **62 campos novos em 28 entidades existentes** (33 entidades existentes alteradas em campo ou valor; 5 delas só em valores de enumeração ou texto de campo; mais 2 só em texto de descrição), **1 campo removido**, 5 domínios novos e as cargas de partida do pacote `Carga31`. O documento 172 ficou de fora (Q172-5 a Q172-10 sem resposta).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 30 | Revisão 31 | Diferença |
|---|---|---|---|
| Entidades | 1.048 | 1.075 | **+27** (8 em Motores Transversais e 19 na Contabilidade & Fiscal) |
| Campos | 11.606 | 12.071 | **+465** (404 nas entidades novas e 62 em 28 existentes, menos 1 removido) |
| Campos de referência (FK) | 3.032 | 3.142 | **+110** |
| Referências genéricas | 58 | 58 | sem mudança |
| Valores de `Cad_Classe_Sistema.Dominio` | 322 | 327 | **+5** (`modelo_intermediacao`, `hipotese_fato_gerador`, `tipo_ajuste_operacao_cbs`, `hipotese_acrescimo_cbs` e `agente_cadeia_combustiveis`) |
| Entidades mestres (identidade e versão) | 200 | 211 | **+11** (as 8 de combustíveis, `Cad_Locacao_Temporada_Regra`, `Cad_Participante_Modelo_Intermediacao` e `Cad_Participante_Autorizacao_Anp`) |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.248 / 3.232 / 3.313 / 9.561 | 1.286 / 3.353 / 3.441 / 9.965 | +38 / +121 / +128 / +404 |
| Chaves estrangeiras que esperam a onda de destino | 70 | 74 | +4 |
| Comandos T-SQL lidos pelo analisador (sqlglot) | 17.355 | 18.046 | +691 (38 + 121 + 128 + 404, exatamente) |
| Carga de partida (provisória) | pacote `Carga30` | pacote `Carga31` | ver seção 3.5 |

Aritmética conferida: 1.048 + 27 = 1.075 entidades; 11.606 + 465 = 12.071 campos (404 + 62 − 1); 3.032 + 110 = 3.142 campos de referência; 200 + 11 = 211 mestres, que viram 1.075 + 211 = 1.286 tabelas físicas.

Auditoria: **0 achados em aberto** depois de uma correção (a primeira passada achou 1 ponto; seção 6). **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.286 tabelas, 3.353 chaves estrangeiras e 9.965 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 79), Compras (27), CRM & Vendas (22), Contabilidade & Fiscal (49) e Gestão de Contratos (8). **As 19 entidades da Contabilidade & Fiscal estão no anexo da seção 45 do documento 10 e as 8 de combustíveis no anexo da seção 36 do documento 01.**

# 2. Como li o "consolidar"

Você já tinha escolhido "Só o que você aprovou". Entra o que está aprovado e **sem pergunta aberta sobre o campo**; o que espera resposta fica de fora. As perguntas ao contador seguem abertas, então o que depende delas **entra com a leitura provisória** que o documento de origem já indicava.

1. **Escopo.** Entram o documento 157 (Q157-1 a Q157-14 "Sim para todas"), o 150 (Q150-1 a Q150-12 "Sim para todas"), o 170 (Q170-1 a Q170-10 "Sim para Todos") e o 173 (Q173-5 a Q173-11 "sim para todos"; as Q173-1 a Q173-4 já aplicadas no desenho). O 173 **substitui** o 171 (Q171-1 a Q171-8 "Todas sim" valem pelo que o 173 corrigiu). Fica de fora o 172.
2. **A ponta de quem recebe o apoio não entra.** Você aprovou na Q173-8 que o lado de quem recebe (adesão, item, requerimento, entrada e repasse do distribuidor, 66 campos) e o critério do Motor `adesao_programa_do_emitente` só entram **quando houver cliente** (D-N68). Li "só com cliente" como **ainda não**: as cinco entidades ficam desenhadas no documento 173, e o dicionário recebe as cinco de parâmetro. **Esta é a leitura que você precisa confirmar** (e a Q173-E2 pergunta se já existe cliente).
3. **Módulo e onda.** As 8 entidades de combustíveis (catálogo do regime, vínculo com o produto, alíquota por unidade, as quatro do programa de apoio e o imposto de exportação) ficam em **Motores Transversais** (onda 0), porque valem para qualquer empresa e para a apuração; a autorização da ANP, por ser cadastro do participante, fica na **Contabilidade & Fiscal**, como as 18 do B0a e do B5 (onda 3). Se você preferir tudo na Contabilidade & Fiscal, mudo o módulo sem alterar campo.
4. **Mestres.** As entidades com identidade e versão (`_Versao` e o trio de vigência) são as 11 listadas na seção 1. As demais com vigência têm vigência no padrão de linha (início, fim e motivo).
5. **Um campo sai.** `Mov_Estoque_Abertura_Cbs_Estorno.Valor_Acrescimos` sai e entram `Valor_Multa_Mora`, `Valor_Juros_Mora`, `ID_Acrescimo_Legal` e `ID_Cbs_Ajuste_Operacao_Efeito` (Q157-6 e D-N466). Não há dado para migrar: o dicionário ainda não tem banco em produção.
6. **Nome de campo.** O documento 173 chamou de `Valor_E_Maximo` um campo booleano de `Cad_Combustivel_Programa_Valor`. A regra H2 do dicionário não aceita booleano com o prefixo `Valor_` (precedente: `Eh_Valor_Unico_Por_Profissional`, revisão 5), então o campo entrou como **`Eh_Valor_Maximo`**. É só o nome.
7. **Início do art. 27.** A vigência inicial de `Cad_Acrescimo_Legal_Cbs` na carga é 01/01/2027 (início da cobrança); o contador confirma (Q157-C7). A de `Cad_Regra_Base_Calculo_Cbs` da gorjeta e da plataforma também é 01/01/2027 (Q150-C1).
8. **Redução de 0,1 ponto.** O código `reducao_cbs_art_585` virou `reducao_cbs_transicao` e a fórmula gravada em `Mov_Apuracao_Tributo_Item.Reducao_Transicao_Pontos` é a leitura do documento 157: alíquota efetiva = (P − t) × (1 − r); o contador confirma (Q157-C11). A exceção dos combustíveis do regime específico fica em `Cad_Cclasstrib.Aplica_Reducao_Transicao_Cbs` por ora.
9. **As quatro leituras da carga do 173.** Fim do etanol em 15/10/2026; MP 1.391, etanol e MP 1.358 sem fim no cabeçalho; imposto de exportação de 50% até 31/12/2026; média simples do desconto do distribuidor. Todas provisórias e marcadas.

# 3. O que entrou

## 3.1 Entidades novas (27)

| Entidade | Módulo | Vigência | Campos | Onda | Decisão |
|---|---|---|---|---|---|
| `Cad_Regra_Fato_Gerador` | Contabilidade & Fiscal | sim | 16 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Cbs_Ajuste_Operacao` | Contabilidade & Fiscal | não | 17 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Cbs_Ajuste_Operacao_Efeito` | Contabilidade & Fiscal | não | 16 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Cbs_Ajuste_Efeito_Regra` | Contabilidade & Fiscal | sim | 15 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Acrescimo_Legal_Cbs` | Contabilidade & Fiscal | sim | 15 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Acrescimo_Legal_Hipotese` | Contabilidade & Fiscal | sim | 13 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Valor_Mercado_Locacao_Parametro` | Contabilidade & Fiscal | sim | 18 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Imovel_Valor_Referencia` | Contabilidade & Fiscal | não | 6 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Cbs_Transicao_2026_Periodo` | Contabilidade & Fiscal | não | 17 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Documento_Fiscal_Entrega_Xml` | Contabilidade & Fiscal | não | 15 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Filial_Evento_Cadastral` | Contabilidade & Fiscal | não | 12 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Qualificacao_Cbs_Inicio_Obrigacao` | Contabilidade & Fiscal | sim | 12 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Cad_Produtor_Rural_Parametro_Cbs` | Contabilidade & Fiscal | sim | 11 | 3 | Documento 157; D-N466 e D-N469 (Q157-1 a Q157-14) |
| `Mov_Gorjeta_Repasse_Periodo` | Contabilidade & Fiscal | não | 12 | 3 | Documento 150; D-N468 e D-N469 (Q150-1 a Q150-12) |
| `Mov_Cooperativa_Transferencia_Credito` | Contabilidade & Fiscal | não | 21 | 3 | Documento 150; D-N468 e D-N469 (Q150-1 a Q150-12) |
| `Mov_Locacao_Temporada` | Contabilidade & Fiscal | não | 15 | 3 | Documento 150; D-N468 e D-N469 (Q150-1 a Q150-12) |
| `Cad_Locacao_Temporada_Regra` | Contabilidade & Fiscal | sim (mestre) | 13 | 3 | Documento 150; D-N468 e D-N469 (Q150-1 a Q150-12) |
| `Cad_Participante_Modelo_Intermediacao` | Contabilidade & Fiscal | sim (mestre) | 10 | 3 | Documento 150; D-N468 e D-N469 (Q150-1 a Q150-12) |
| `Cad_Combustivel_Regime` | Motores Transversais | sim (mestre) | 19 | 0 | Documento 170; D-N470 e D-N471 (Q170-1 a Q170-10) |
| `Cad_Combustivel_Produto_Vinculo` | Motores Transversais | sim (mestre) | 11 | 0 | Documento 170; D-N470 e D-N471 (Q170-1 a Q170-10) |
| `Cad_Aliquota_Combustivel` | Motores Transversais | sim (mestre) | 19 | 0 | Documento 170; D-N470 e D-N471 (Q170-1 a Q170-10) |
| `Cad_Participante_Autorizacao_Anp` | Contabilidade & Fiscal | sim (mestre) | 13 | 3 | Documento 170; D-N470 e D-N471 (Q170-1 a Q170-10) |
| `Cad_Combustivel_Programa_Apoio` | Motores Transversais | sim (mestre) | 29 | 0 | Documento 173; D-N473 a D-N476 (Q173-1 a Q173-11) |
| `Cad_Combustivel_Programa_Valor` | Motores Transversais | sim (mestre) | 18 | 0 | Documento 173; D-N473 a D-N476 (Q173-1 a Q173-11) |
| `Cad_Combustivel_Programa_Periodo` | Motores Transversais | sim (mestre) | 13 | 0 | Documento 173; D-N473 a D-N476 (Q173-1 a Q173-11) |
| `Cad_Combustivel_Programa_Tributo_Equivalente` | Motores Transversais | sim (mestre) | 13 | 0 | Documento 173; D-N473 a D-N476 (Q173-1 a Q173-11) |
| `Cad_Imposto_Exportacao_Aliquota` | Motores Transversais | sim (mestre) | 15 | 0 | Documento 173; D-N473 a D-N476 (Q173-1 a Q173-11) |

(A coluna de campos conta o que está no modelo, inclusive identificador, versão e trio de vigência.)

## 3.2 Campos novos em entidades existentes (62, em 28 das 33 entidades alteradas)

| Entidade | Módulo | Campos novos | Quais | Outras mudanças |
|---|---|---|---|---|
| `Cad_Adiantamento_Regra_Tributacao` | Contabilidade & Fiscal | 3 | Criterio_Data_Aliquota, Prazo_Maximo_Dias_Ate_Fornecimento, Periodo_Debito_Antecipacao | — |
| `Cad_Aliquota` | Motores Transversais | 2 | Fundamento_Legal, Situacao_Dado | — |
| `Cad_Calendario_Transicao` | Contabilidade & Fiscal | 0 |  | valores de enumeração |
| `Cad_Cclasstrib` | Contabilidade & Fiscal | 1 | Aplica_Reducao_Transicao_Cbs | — |
| `Cad_Classe_Sistema` | Motores Transversais | 0 |  | valores de enumeração |
| `Cad_Cooperativa_Associado` | Contabilidade & Fiscal | 1 | Sujeito_Regime_Regular_Cbs | — |
| `Cad_Modelo_Documento_Fiscal` | Motores Transversais | 4 | Exige_Entrega_Ao_Adquirente, Exige_Protocolo_Na_Entrega, Exige_Rpv_Na_Entrega, Exige_Entrega_Ao_Transportador | — |
| `Cad_Motor_Regra_Resultado` | Motores Transversais | 0 |  | valores de enumeração |
| `Cad_Participante_Endereco` | Motores Transversais | 1 | Eh_Domicilio_Principal | — |
| `Cad_Participante_Regime_Especifico` | Contabilidade & Fiscal | 1 | ID_Tipo_Cooperativa | — |
| `Cad_Produto_Servico` | Motores Transversais | 1 | Tipo_Servico_Agencia | — |
| `Cad_Regime_Geral_Imobiliario` | Contabilidade & Fiscal | 1 | Momento_Fato_Gerador_Nao_Oneroso | — |
| `Cad_Regra_Base_Calculo_Cbs` | Contabilidade & Fiscal | 5 | Percentual_Limite_Exclusao, Base_Do_Limite, Rateia_Pela_Proporcao_Do_Regime e mais 2 | — |
| `Cad_Regra_Vencimento` | Motores Transversais | 0 |  | valores de enumeração |
| `Mov_Apuracao_Tributo_Item` | Contabilidade & Fiscal | 4 | Competencia_Debito, Reducao_Transicao_Pontos, ID_Calendario_Reducao, ID_Aliquota_Combustivel | — |
| `Mov_Apuracao_Tributo_Item_Base_Especial` | Contabilidade & Fiscal | 3 | Valor_Informado, Valor_Limite, Situacao_Limite | — |
| `Mov_Apuracao_Tributo_Item_Complemento` | Contabilidade & Fiscal | 2 | Data_Incidencia_Monofasica, Valor_Limite_Credito | valores de enumeração, texto de regra |
| `Mov_Auto_Infracao` | Contabilidade & Fiscal | 4 | Regime_Suprimento_2026, Data_Intimacao_Suprimento, Data_Atendimento_Suprimento, Penalidade_Extinta | — |
| `Mov_Cbs_Apuracao_Espelho` | Contabilidade & Fiscal | 0 |  | texto de regra |
| `Mov_Cooperativa_Listagem_Envio` | Contabilidade & Fiscal | 3 | Tipo_Envio, Tipo_Opcao, Data_Inicio_Efeito | — |
| `Mov_Credito_Aplicacao_Tributo` | Contabilidade & Fiscal | 2 | Adquirente_Tomou_Credito, ID_Perdcomp | — |
| `Mov_Credito_Fiscal` | Contabilidade & Fiscal | 1 | ID_Cbs_Ajuste_Operacao_Efeito | valores de enumeração |
| `Mov_Credito_Fiscal_Aplicacao` | Contabilidade & Fiscal | 1 | ID_Transferencia_Credito | valores de enumeração |
| `Mov_Devolucao_Compra` | Compras | 1 | ID_Cbs_Ajuste_Operacao | — |
| `Mov_Devolucao_Venda` | CRM & Vendas | 1 | ID_Cbs_Ajuste_Operacao | — |
| `Mov_Estoque_Abertura_Cbs_Estorno` | Contabilidade & Fiscal | 4 | Valor_Multa_Mora, Valor_Juros_Mora, ID_Acrescimo_Legal, ID_Cbs_Ajuste_Operacao_Efeito | campo removido |
| `Mov_Gestao_Contrato_Apuracao` | Gestão de Contratos | 1 | Data_Exigibilidade | — |
| `Mov_Locacao_Faturamento` | Contabilidade & Fiscal | 4 | Valor_Foro_Taxa_Ocupacao, Comprovacao_Pagamento_Despesas, Valor_Contraprestacao_Nao_Monetaria, ID_Apuracao_Valor_Mercado | — |
| `Mov_Locacao_Limite_Pf` | Contabilidade & Fiscal | 1 | Receita_Locacao_Valor_Mercado_Relacionada | texto de regra |
| `Mov_Nota_Fiscal_Entrada_Item` | Compras | 3 | Data_Fato_Gerador, Criterio_Data_Fato_Gerador, ID_Regra_Fato_Gerador | — |
| `Mov_Nota_Fiscal_Saida` | CRM & Vendas | 1 | Indicador_Fornecimento_Sob_Contrato | — |
| `Mov_Nota_Fiscal_Saida_Item` | CRM & Vendas | 4 | Tipo_Servico_Agencia, Data_Fato_Gerador, Criterio_Data_Fato_Gerador, ID_Regra_Fato_Gerador | — |
| `Mov_Valor_Mercado_Apuracao` | Contabilidade & Fiscal | 2 | ID_Valor_Mercado_Locacao_Parametro, ID_Imovel_Valor_Referencia | — |

Além destas, **`Mov_Credito_Ajuste_Documento`** e **`Mov_Cbs_Pedido_Ressarcimento`** mudam só no texto de descrição (seção 3.4).

## 3.3 Domínios e valores novos

- **5 domínios novos** em `Cad_Classe_Sistema.Dominio`, todos abertos: `modelo_intermediacao` (3 valores, documento 150), `hipotese_fato_gerador` (12), `tipo_ajuste_operacao_cbs` (4) e `hipotese_acrescimo_cbs` (28), do documento 157, e `agente_cadeia_combustiveis` (13 valores: os 11 do documento 170 e `agente_comercio_exterior` e `cooperativa_produtores_biocombustiveis` do 173).
- **Valores novos em domínios existentes (carga, sem mudança de estrutura):** `componente_base_calculo_ibs_cbs` (`gorjeta_bar_restaurante` e `intermediacao_plataforma_pedido`), `campo_criterio_regra` (9 critérios do documento 150 e 3 do 170) e `parametro_transicao` (`prazo_ressarcimento_transicao_2026`, `prazo_suprimento_intimacao_2026`, os quatro códigos de início da obrigação da pessoa física e do produtor rural, e o código `reducao_cbs_art_585` renomeado `reducao_cbs_transicao`).
- **Valores de enumeração novos em campos:** `Mov_Credito_Fiscal.Origem` (`ajuste_operacao`, `restabelecimento`), `.Status` (`estornado`) e `.Modalidade_Extincao_Debito` (`compensacao`, `responsavel`); `Cad_Motor_Regra_Resultado.Tipo_Resultado` (`componente_base_calculo`); `Mov_Credito_Fiscal_Aplicacao.Forma_Utilizacao` (`transferencia_cooperativa`); `Cad_Calendario_Transicao.Tipo_Valor` (`numero`); `Cad_Regra_Vencimento.Finalidade` (`comunicacao_cadastral`); e `Mov_Apuracao_Tributo_Item_Complemento.Tipo_Complemento` (`monofasia_padrao`, `monofasia_retencao`, `monofasia_retida_anteriormente`).

## 3.4 Textos corrigidos (sem campo)

1. **Excesso da antecipação** (`Mov_Credito_Aplicacao_Tributo`, documento 10): deixa de ser "crédito do contribuinte, derivado". Depois da LC 227, o excesso segue as regras do pagamento indevido ou a maior (LC 214, art. 10, § 4º, II, c; Decreto 12.955, art. 38): a restituição só cabe se a operação não gerou crédito ao adquirente e o fornecedor prova ter assumido o encargo.
2. **Ajuste do adiantamento devolvido** (`Mov_Credito_Ajuste_Documento`): o cancelamento segue o art. 57 do Decreto (art. 11, § 6º).
3. **Espelho da Apuração Assistida** (`Mov_Cbs_Apuracao_Espelho.Periodo`): o espelho é o da Plataforma; a competência do ERP segue o fato gerador.
4. **Pedido de ressarcimento** (`Mov_Cbs_Pedido_Ressarcimento`): o período de 2026 não aceita saldo da apuração informativa (Decreto, art. 465; leitura minha, Q157-C10).
5. **Numeração da redução de 0,1 ponto:** é do **art. 347 da LC 214** e do art. 585 do **Decreto**; a LC não tem art. 585. Corrigidos o documento 10 (código `reducao_cbs_transicao`), o documento 01 (domínio `parametro_transicao`) e os documentos 94 e 115.
6. **Acréscimos do art. 27:** o Decreto tem **22 artigos** que remetem a ele, e não "mais de dez" (documento 115).
7. **Complemento monofásico** (`Mov_Apuracao_Tributo_Item_Complemento`, documento 170): `Quantidade`, `Valor_Especifico_Unidade` e `Valor` passam a cobrir também a base e a alíquota específica da CBS e do IBS monofásicos.

## 3.5 Cargas (pacote `Carga31`)

| Pasta | Conteúdo |
|---|---|
| `01-b0a-doc157` | 12 linhas de fato gerador, 21 da matriz de efeitos do ajuste, 1 do acréscimo do art. 27 e as 28 hipóteses, 3 do início da obrigação (leitura minha), 1 do produtor rural, 6 do calendário (4 datas de início e os 2 prazos de 60 dias), o prazo de entrega do arquivo **sem valor**, 1 do vencimento cadastral, 2 métodos de valor de mercado e as regras de carga das marcas por modelo, do cClassTrib e do calendário |
| `02-b5-doc150` | As 2 linhas novas de `Cad_Regra_Base_Calculo_Cbs` (gorjeta e valor da plataforma) e a regra de `Cad_Locacao_Temporada_Regra` |
| `03-combustiveis-doc170` | 11 linhas do catálogo do regime e 8 da CBS por unidade (Portaria MF 3.074/2026, fonte secundária) |
| `04-programas-doc173` | 7 programas, 7 valores, 45 períodos, 5 equivalências a tributo, 2 do imposto de exportação e 2 linhas de `Cad_Imposto` |
| `05-dominios` | 80 valores de `Cad_Classe_Sistema` (5 domínios novos, valores novos em 3 domínios existentes) |

Ao contrário do `Carga30`, que converti coluna a coluna, o `Carga31` é uma **extração direta dos anexos** dos documentos (as colunas são as dos anexos, com o código de negócio nas referências); o script de carga da equipe faz a conversão. **Sem carga:** `Cad_Valor_Mercado_Locacao_Parametro` (aguarda o ato conjunto), `Cad_Combustivel_Produto_Vinculo` (aguarda a tabela da ANP), `Cad_Participante_Autorizacao_Anp` e `Cad_Participante_Modelo_Intermediacao` (cadastro do usuário), as colunas da regra dos cinco dias (reserva) e o valor do prazo de entrega do arquivo.

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Documento 172** (tabelas do validador da EFD-ICMS/IPI) | Q172-5 a Q172-10 sem resposta | Documento 38, seção 1.19 |
| **Documento 171** | Substituído pelo 173 | Documento 14 |
| **Lado de quem recebe o apoio aos combustíveis** (5 entidades, 66 campos) e o critério do Motor `adesao_programa_do_emitente` | Só com cliente (Q173-8; D-N68) | Documento 173 |
| **Esboço da ponta do produtor de combustíveis** (retenção da CBS do etanol anidro e ressarcimento na mistura) | Esboço, não entra no "consolidar" | Documento 170, seção 13 |
| **Indicador de atividade rural (Q93-6)** | O desenho como linha do catálogo ainda não foi escrito | Documento 38, seção 0 |
| **Perguntas ao contador** (Q157-C1 a C14, Q150-C, Q170-C, Q173-C1 a C8 e a Q171-C5) | Sem resposta; o desenho entrou com a leitura provisória de cada uma | Documento 38, seções 2.11 a 2.14 |
| **Fórmulas de 2024 da ECF (Q152-4)** | A planilha do leiaute 11 continua fora do meu ambiente; **reenvie** | Documento 38, seção 0 |
| **Desenhos 158, 159 e 160** | Ainda não escritos | Fila de desenho |

# 5. Pontos de atenção

- **A onda 0 pesa 177 entidades** (eram 169), 1.804 campos e 399 chaves estrangeiras; a **onda 3 tem 524 entidades** (eram 505), 6.347 campos e 1.532 chaves. A onda 4 não mudou (118).
- **Mudança de nome de campo e de módulo** (seção 2, itens 3 e 6): `Eh_Valor_Maximo` e a posição das 8 entidades de combustíveis em Motores Transversais são escolhas minhas; diga se quer diferente.
- **Início da obrigação da pessoa física** (`Cad_Qualificacao_Cbs_Inicio_Obrigacao`): o documento 157 diz "3 linhas de carga" sem listá-las; derivei as três da seção 9.2 (pessoa física contribuinte, produtor rural pessoa física, e a pessoa jurídica sem data por depender de ato conjunto). Leitura minha, a confirmar.
- **Métodos 9 e 10 do valor de mercado** (`Cad_Regra_Valor_Mercado`): o documento 157 dá o nome e o fundamento; a ordem de aplicação e as demais colunas são leitura minha, a conferir com o Anexo E do documento 156.
- **Vigência inicial vazia** nas cargas do fato gerador, da matriz de efeitos e das hipóteses do art. 27: o documento não a fixa; o contador define.
- **Alíquotas de combustíveis:** as 8 linhas de CBS vêm da Portaria MF 3.074/2026 por **fonte secundária** (texto não lido), vigência 08/01/2027; nenhuma linha de IBS.
- **O Planalto marca "Vigência encerrada"** nas MPs 1.340, 1.349, 1.358 e 1.363 (pergunta ao contador, documento 173).
- **Documentos 150, 157, 170, 173 e este relatório** seguem só em Word (o Projeto está cheio). O que entrou no dicionário está nos documentos 01, 03, 05, 10 e 12; os documentos 14, 29, 31, 38, 94 e 115 foram atualizados no Projeto, e o modelo ER em Word foi regerado.
- **Numeração.** O número 172 continua com as Q172-5 a Q172-10 abertas.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 27 entidades ({newf} campos no modelo), 62 campos novos em 28 entidades existentes e 1 campo removido; nenhuma entidade mudou de módulo. As entidades novas são 13 do documento 157, 5 do 150, 4 do 170 e 5 do 173; os campos de cada uma vêm das tabelas dos documentos, mais identificador, versão e vigência quando é mestre ou tem vigência. As alterações em entidades existentes foram comparadas com o modelo da revisão 30 campo a campo (62 acrescentados e 1 removido, em 28 entidades).
- **Auditoria:** a primeira passada achou **1 ponto**: H2 (`Valor_E_Maximo`, booleano com prefixo `Valor_`, que passou a `Eh_Valor_Maximo`). Fechou com **0 achados em aberto**; nenhuma das 27 entidades novas ficou isolada.
- **DDL:** gerado nos dois dialetos (1.286 tabelas, 3.353 chaves estrangeiras, 3.441 índices e 9.965 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e as contagens do banco batem com as do gerador. O cabeçalho dos arquivos de onda, que ainda dizia "revisão 29", passou a dizer revisão 31.
- **T-SQL:** 18.046 comandos lidos por analisador de sintaxe (sqlglot), sem erro; o aumento de 691 comandos é exatamente 38 tabelas, 121 chaves estrangeiras, 128 índices e 404 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos.
- **Carga31:** gerada por script a partir dos anexos dos documentos 157, 150, 170 e 173; os totais de linhas (12, 21, 28, 11, 8, 7, 7, 45, 5 e 2) batem com os dos anexos.
- **Limites:** nada foi validado pelo contador. A vigência de partida de parte das cargas, as 3 linhas do início da obrigação, a ordem dos métodos 9 e 10 do valor de mercado e os códigos de domínio propostos nos documentos de desenho são leituras minhas.
