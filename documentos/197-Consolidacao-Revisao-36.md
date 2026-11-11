# Consolidação da Revisão 36 — Documento 197

*Relatório do que entrou no dicionário com o seu "consolidar" de 10/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava no dicionário** depois da revisão 35: do documento 159 as Q159-1 a Q159-3 e Q159-5 a Q159-9 (D-N525), do documento 196 as Q196-1 a Q196-11 (D-N526, que fecham Q159-4, Q159-10 e Q159-11) e a D-N523 (Q194-1, Q194-3, Q194-4 e Q194-5).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 35 | Revisão 36 | Diferença |
|---|---|---|---|
| Entidades | 1.138 | 1.144 | +6 |
| Campos | 12.769 | 12.860 | +91 |
| Campos de referência (FK) | 3.345 | 3.365 | +20 |
| Entidades mestres | 224 | 228 | +4 |
| Referências genéricas | 61 | 61 | 0 |
| Domínios de `Cad_Classe_Sistema` | 344 | 353 | +9 |
| Tabelas físicas (DDL) | 1.362 | 1.372 | +10 |
| Chaves estrangeiras (DDL) | 3.569 | 3.593 | +24 |
| Índices (DDL) | 3.660 | 3.684 | +24 |
| Comentários (DDL) | 10.587 | 10.669 | +82 |
| Comandos do T-SQL | 19.179 | 19.319 | +140 |
| Entidades com FK que espera a onda de destino | 79 | 79 | 0 |

**6 entidades novas** (77 campos) e **6 existentes alteradas** (14 campos novos em 4 delas; `Cad_Classe_Sistema` e `Cad_Produto_Servico` mudam só em valor de domínio e em texto), distribuídas assim:

| Decisão | Entidades novas | Campos nelas | Campos novos em existentes |
|---|---|---|---|
| Q159-2 (ordem de aplicação do art. 7º-A) | 1 (`Cad_Instituto_Beneficio_Ordem`) | 10 | 2 (`Cad_Cclasstrib`) |
| Q159-3 (consulta e contencioso) | 3 (`Mov_Processo_Consulta_Tributaria` 16, `Mov_Processo_Uniformizacao` 11 e `Cad_Parametro_Legal_Ibs_Cbs` 12) | 39 | 0 |
| Q159-5 (PNCT) | 1 (`Cad_Programa_Conformidade_Beneficio`) | 13 | 0 |
| Multas (Q196-1 a Q196-5, opção A+) | 0 | 0 | 9 (`Mov_Auto_Infracao`) |
| Imposto Seletivo pelo NCM (Q196-8, Q196-9, Q196-11) | 1 (`Cad_Is_Hipotese_Base`) | 15 | 3 (`Cad_NCM_Imposto_Seletivo` 1 e `Mov_Apuracao_Tributo_Item` 2) |
| Q159-1, Q159-6 a Q159-9, Q196-6 e D-N523 | 0 | 0 | 0 (só texto) |
| **Total** | **6** | **77** | **14** |

Quatro das seis entidades novas têm vigência e viram duas tabelas no DDL (mestres): `Cad_Instituto_Beneficio_Ordem`, `Cad_Parametro_Legal_Ibs_Cbs`, `Cad_Programa_Conformidade_Beneficio` e `Cad_Is_Hipotese_Base`. Por isso as 6 entidades dão 10 tabelas.

# 2. O que entrou, por decisão

## 2.1 Ordem de aplicação do art. 7º-A (Q159-2)

- **`Cad_Instituto_Beneficio_Ordem`** (10 campos): a ordem em que os cinco institutos do art. 7º-A se aplicam (redução a zero, suspensão com conversão em alíquota zero, isenção, diferimento e redução de alíquota distinta); o menor número prevalece. Carga de 5 linhas, provisória.
- **`Cad_Cclasstrib`:** `ID_Instituto_Beneficio` e `Admite_Cumulacao_Reducao`, para o cClassTrib dizer a qual instituto pertence e se admite acumular com redução.

## 2.2 Consulta e contencioso (Q159-3)

- **`Mov_Processo_Consulta_Tributaria`** (16 campos) e **`Mov_Processo_Uniformizacao`** (11): a consulta sobre a legislação (arts. 323-A a 323-F da LC 214, ligada ao `Cad_Processo`) e o recurso especial e os incidentes de uniformização (arts. 323-G a 323-M), com o motivo de ineficácia da consulta em domínio próprio (6 valores). O ERP só registra; o lado do contribuinte, como na D-N68.
- **`Cad_Parametro_Legal_Ibs_Cbs`** (12 campos, mestre): os números da lei que mudam por vigência, com 16 linhas de carga: 4 prazos (15 dias corridos, 10 e 90 dias úteis, 30 dias corridos), 4 do automóvel de PcD e do táxi (R$ 200.000, R$ 100.000, 3 e 2 anos) e 8 reduções de multa do art. 341-H (50, 40, 30 e 20; 60, 50, 40 e 30).

## 2.3 PNCT (Q159-5)

- **`Cad_Programa_Conformidade_Beneficio`** (13 campos, mestre): o que cada programa de conformidade pode dar a quem participa dele, uma linha por programa e tipo de benefício (arts. 471-A a 471-C da LC 214, com 7 tipos de benefício em domínio próprio). O art. 471-C deixa o resto para um ato conjunto do CGIBS e da RFB que ainda não existe, e por isso a carga fica vazia. A participação no PNCT é a linha dessa entidade e do domínio `programa_conformidade`, valor `pnct`; **não há `Participa_Pnct` no cadastro**.

## 2.4 Multas do IBS e da CBS (opção A+, Q196-1 a Q196-5)

- **`Mov_Auto_Infracao`** ganha 9 campos: `ID_Tipo_Penalidade`, `Percentual_Multa_Aplicado` (50, 75, 100 ou 150), `Valor_Penalidade`, `Reincidencia_Especifica`, `Em_Regime_Especial_Fiscalizacao`, `ID_Hipotese_Reducao`, `Percentual_Reducao_Aplicado`, `Valor_Penalidade_Paga` e `Ente_Federativo_Lancamento` (art. 330, § 1º, VII).
- **`tipo_penalidade_ibs_cbs`** com 29 valores (24 de obrigação acessória e 5 de ofício, entre eles `oficio_50_declaracao_correta`, do art. 341-F, § 3º) e **`hipotese_reducao_multa`** com 4 (art. 341-H).
- **Nove avisos do Motor** registrados como texto, sem programar. O ERP só registra o auto de infração; não calcula a multa (D-N284).
- **Não entrou a opção B** (51 campos), como você decidiu.

## 2.5 Imposto Seletivo pelo NCM (Q196-8, Q196-9 e Q196-11)

- **O NCM é a base** (sua regra de 10/11/2026): produto, NCM (`Cad_Classificacao_Mercadoria`), `Cad_NCM_Imposto_Seletivo` (alíquota, tipo e grupo) e `Cad_Is_Hipotese_Base` (contribuinte e base). A linha com grupo vale antes da linha sem grupo.
- **`Cad_Is_Hipotese_Base`** (15 campos, mestre): as 11 combinações de momento do art. 412, contribuinte do art. 424 e base do art. 414, com a base alternativa da importação de fumígenos (a maior entre as duas, art. 434, § 2º-A). Carga de 11 linhas, provisória.
- **`Cad_NCM_Imposto_Seletivo`:** `ID_Grupo_Produto_Is` (7 grupos do art. 409, § 1º) e a descrição de `Tipo_Aliquota`. É a **fonte única de alíquota e grupo dos bens**; a lista legal guarda só a exceção da ZFM. **Corrige a D-N295 apenas para bens**; serviços (Anexo XVII) seguem pelo NBS na lista legal.
- **`Mov_Apuracao_Tributo_Item`:** `ID_Is_Hipotese_Base` e `Valor_Referencia_Informado` (valor de referência informado no item, com aviso quando faltar).
- **`Cad_Produto_Servico.Sujeito_Imposto_Seletivo`** passa a ser derivado do NCM (ou do NBS), com aviso quando o NCM não achar linha. O aviso da embalagem primária de fumígenos e bebidas alcoólicas (art. 409, § 2º) fica como texto, sem campo.
- **MP 1.399/2026:** só por fontes secundárias; nada dela entra na carga até o texto oficial chegar (Q196-10, com você).

## 2.6 Texto, sem campo

- **Documento consolidado da LC 214 (Q196-6):** nenhum campo; dez pontos para ler o ato e o gatilho que reabre o assunto.
- **Q159-1, Q159-6 a Q159-9:** lista refeita dos 131 artigos e Anexo B (os documentos 159 e 196 guardam o quadro), penalidades do prestador de pagamento no B7, devolução ao turista só com cliente, destino dos artigos em bloco e dos 19 sem desenho e energia elétrica como texto de regra.
- **D-N523 (combustíveis):** as 8 linhas de CBS passam a "texto oficial lido" (Portaria MF 3.074/2026, visão multivigente da RFB, lida em 09/11/2026), com a Portaria Conjunta MF/CGIBS nº 14/2026 no fundamento; início em 08/01/2027 até a C161; nenhuma linha de IBS; nenhum campo para o 90% do IBS do art. 13 da conjunta; fator e percentual como parâmetros com vigência em `Cad_Combustivel_Regime`.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Classe_Sistema` (valores novos) | 80 | 9 domínios novos (5 + 6 + 7 + 29 + 4 + 8 + 5 + 7 + 7 = 78), mais `pnct` em `programa_conformidade` e `is_demais_hipoteses` em `hipotese_valor_mercado` |
| `Cad_Instituto_Beneficio_Ordem` | 5 | incisos I a V do art. 7º-A |
| `Cad_Parametro_Legal_Ibs_Cbs` | 16 | 4 prazos, 4 do automóvel e 8 reduções de multa |
| `Cad_Is_Hipotese_Base` | 11 | 9 sem grupo e 2 de fumígenos (venda e importação) |
| `Cad_Aliquota_Combustivel` (CBS) | 8 | mesmos valores da carga 31, observação nova (D-N523) |

Total: **120 linhas em 5 arquivos de dados e 5 de regra de texto** (pasta `Carga36`; a vigência de partida é 13/01/2026, e os combustíveis começam em 08/01/2027). Ficam sem carga: `Cad_Programa_Conformidade_Beneficio` (até o ato conjunto do art. 471-C), as alíquotas do Imposto Seletivo por NCM e `Cad_Is_Valor_Referencia` (esperam o texto oficial da MP 1.399/2026 e do ato do art. 414, § 2º, Q196-10) e os processos de consulta e uniformização (do usuário).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: ficaram de fora o documento 160 (não desenhado) e o que depende do texto oficial da MP 1.399/2026.
2. **14 códigos de domínio foram abreviados** para caber nos 30 caracteres de `Cad_Classe_Sistema.Codigo`; os documentos 159 e 196 citam os nomes longos. A correspondência está na seção 6.
3. **Módulos:** as três entidades do art. 7º-A, dos parâmetros legais e do PNCT ficam em Contabilidade & Fiscal (onda 3); os dois processos, em Jurídico (onda 2); `Cad_Is_Hipotese_Base`, na Fase 0 (onda 0), ao lado de `Cad_NCM_Imposto_Seletivo`. Se você preferir outro módulo, mudo sem alterar campo.
4. **Q196-6** foi lida como "não preparar o esboço da entidade do documento consolidado": só os dez pontos e o gatilho.
5. **A vigência de partida das cargas novas é 13/01/2026** (publicação da LC 227), provisória; o contador confirma.
6. **Os avisos do Motor continuam registrados e não programados**: os nove das multas, o da embalagem primária (art. 409, § 2º) e o do valor de referência.
7. **Os 16 parâmetros de `Cad_Parametro_Legal_Ibs_Cbs`** vêm do quadro do documento 159, seção 4.2, e o rótulo de cada um é o código sem os sublinhados; o texto da tela é meu.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto nos documentos 159 e 196 | 1.138 + 6 entidades e 12.769 + 77 + 14 campos: **1.144 entidades e 12.860 campos**, como o modelo regerado; 3.365 referências (+20) e 353 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.372 tabelas, 3.593 chaves estrangeiras e 10.669 comentários; as seis tabelas novas e as quatro de versão foram criadas |
| T-SQL (analisador sqlglot, oito arquivos) | Lido sem erro; 19.319 comandos (140 a mais). **Não equivale a executar num SQL Server.** |
| Ondas | `Cad_Is_Hipotese_Base` na onda 0, os dois processos na onda 2 e as outras três na onda 3; nenhuma chave nova espera onda de destino (79, como antes) |
| Carga | 120 linhas; nenhum código de domínio com mais de 30 caracteres; os 14 abreviados estão na seção 6 |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. Códigos de domínio abreviados (limite de 30 caracteres)

| Nome nos documentos 159 e 196 | Código no dicionário |
|---|---|
| `fato_nao_descrito_exata_completamente` | `fato_nao_descrito_exato` |
| `inconstitucionalidade_ou_negativa_aplicacao` | `inconstitucionalidade_negativa` |
| `formulada_apos_procedimento_fiscal` | `consulta_apos_procedimento` |
| `prazo_ampliado_obrigacao_acessoria` | `prazo_ampliado_ob_acessoria` |
| `prioridade_pedido_ressarcimento` | `prioridade_ressarcimento` |
| `flexibilizacao_valor_mercado_partes_relacionadas` | `flex_valor_mercado_parte_rel` |
| `domicilio_principal_nao_atualizado` | `domicilio_nao_atualizado` |
| `software_fiscal_irregular_fornecimento` | `software_fiscal_irregular` |
| `documento_usado_mais_de_uma_vez` | `documento_usado_mais_de_1_vez` |
| `documento_falsificado_ou_extraviado` | `documento_falsificado_extravio` |
| `informacao_comercio_exterior_omitida` | `info_comercio_exterior_omitida` |
| `instalacao_credenciada_zfm_sem_requisito` | `instalacao_zfm_sem_requisito` |
| `fornecimento_ou_pagamento_servico` | `fornecimento_ou_pagto_servico` |
| `imposto_seletivo_demais_hipoteses` | `is_demais_hipoteses` |

# 7. O que continua aberto

- **Você:** o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1 (equipe), as Q179-1 e Q179-3 (parte 2: planilha do leiaute 11, também Q152-4) e a Q93-6 (indicador de atividade rural).
- **Contador:** C1 a C232 do documento 188 (entre elas C226 a C232, dos documentos 159 e 196).
- **Equipe e fontes oficiais:** seção 3 do documento 38; Portaria MF 2.813.
- **Fila de desenho:** documento 160 (parâmetros das outras obrigações).

# 8. Limites

- Os 16 parâmetros e as 11 linhas do Imposto Seletivo vêm dos documentos 159 e 196, que li da LC 214 e da LC 227 (cópias do Planalto de 09 e 10/11/2026); **não conferi no DOU** nem de novo no Planalto.
- A MP 1.399/2026 só foi lida em fontes secundárias; nenhum número dela está na carga.
- Os códigos abreviados e os valores marcados como leitura minha na seção 4 não vêm de norma.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1, 10 e 21 do dicionário e o 197 seguem só nos Word desta entrega.
