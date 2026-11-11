# Consolidação da Revisão 32 — Documento 178

*Relatório do que entrou no dicionário com o seu "consolidar" de 05/11/2026, do que ficou de fora e de como conferi. A revisão 32 aplica o que você aprovou, com o escopo **"Também 175 e 176 completos"**: o documento **172** (tabelas do validador da EFD-ICMS/IPI), o **175** (lacunas setoriais G15 a G19 da EFD-ICMS/IPI, sem o Bloco 1 de combustíveis) e o **176** (o FAQ da Receita da EFD-ICMS/IPI v7.8 contra o dicionário), este último com as respostas C176-1 a C176-3, C176-6, `COD_INS_SUBST` e C130. Ficam de fora o documento 158 (B3) e o 177 (transação de cartão), sem resposta.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 31 | Revisão 32 | Diferença |
|---|---|---|---|
| Entidades | 1.075 | 1.107 | **+32** (todas na Contabilidade & Fiscal: 27 na onda 3 e 5 na onda 4) |
| Campos | 12.071 | 12.404 | **+333** (290 nas entidades novas e 43 em 22 existentes; nenhum removido) |
| Campos de referência (FK) | 3.142 | 3.241 | **+99** |
| Referências genéricas | 58 | 61 | **+3** |
| Valores de `Cad_Classe_Sistema.Dominio` | 327 | 334 | **+7** (9 domínios novos e 2 que saem) |
| Entidades mestres (identidade e versão) | 211 | 217 | **+6** (`Cad_Icms_Beneficio_Ajuste_Codigo`, `Cad_Icms_Informacao_Adicional_Codigo`, `Cad_Efd_Codigo_Estadual`, `Cad_Iss_Df_Valor_Uniprofissional`, `Cad_Efd_Giaf_Campo` e `Cad_Efd_1601_Regra_Uf`) |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.286 / 3.353 / 3.441 / 9.965 | 1.324 / 3.458 / 3.546 / 10.266 | +38 / +105 / +105 / +301 |
| Chaves estrangeiras que esperam a onda de destino | 74 | 75 | +1 |
| Comandos T-SQL lidos pelo analisador (sqlglot) | 18.046 | 18.595 | +549 (38 + 105 + 105 + 301, exatamente) |
| Carga de partida (provisória) | pacote `Carga31` | pacote `Carga32` | ver seção 3.5 |

Aritmética conferida: 1.075 + 32 = 1.107 entidades; 12.071 + 333 = 12.404 campos (290 + 43); 3.142 + 99 = 3.241 campos de referência; 211 + 6 = 217 mestres, que viram 1.107 + 217 = 1.324 tabelas físicas.

Auditoria: **0 achados em aberto** depois de uma correção (a primeira passada achou 1 ponto; seção 6). **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.324 tabelas, 3.458 chaves estrangeiras e 10.266 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 80), Compras (28), Estoque (18), CRM & Vendas (23), Contas a Pagar/Receber (26) e Contabilidade & Fiscal (50). **As 32 entidades da Contabilidade & Fiscal estão no anexo da seção 46 do documento 10.**

# 2. Como li o "consolidar"

Você escolheu "Também 175 e 176 completos". O que entrou é o que está aprovado ou que li como aprovado; as perguntas ao contador e à equipe seguem abertas, e o que depende delas entra **com a leitura provisória** que o documento de origem indicava.

1. **Escopo.** Entram o documento 172 (Q172-1 a Q172-10, Q172-C1, C4 e C6), o 175 (Q175-1 a Q175-9) e o 176 (Q176-1 a Q176-12). Ficam de fora o 158 (Q158-1 a Q158-13) e o 177 (Q177-1 a Q177-5), sem resposta, e o indicador de atividade rural (Q93-6).
2. **"Completos" foi lido como "Sim" em todas as perguntas abertas dos documentos 175 e 176**, com a recomendação de cada uma: Q175-1 a Q175-9, Q176-11 e Q176-12. **Esta é a leitura que você precisa confirmar.** A parte da Q175-9 que pede a tabela de cClass da NFGás segue aberta: a carga ficou só com a NF3e.
3. **Linhas de teste.** Na Q172-5 você disse "não carregar": as 7 linhas de teste da fonte (RO e RS) ficam fora da carga e listadas no arquivo de registro.
4. **A natureza do código de receita não bate com a medição do documento 172.** Ele dizia 703 de 1.935 códigos com um único termo reconhecível. Não consegui reproduzir a lista de palavras (ela não sobreviveu) e usei uma lista reconstruída: **654 dos 1,935 códigos distintos** (34%) têm um único termo, 1,132 nenhum e 149 mais de um; por linha, 730 das 2.162 recebem a sugestão, e 1.432 ficam vazias. A sugestão é provisória, visível e fica para uma pessoa classificar (Q172-6).
5. **`Tabela_Origem` fica opcional** (Q172-C1, "no momento só a Guia"): o arquivo do validador não separa a tabela 5.1.1 da 5.3, e a carga deixa o campo vazio.
6. **1601 por UF.** A carga tem 7 linhas: AL, CE, PB e RN pela competência da transação; MG e SC pelo cartão na competência e o resto no caixa; PR com `Obrigatorio = falso`. Quem informa (Q176-11): AL, CE, RN e MG `quem_vendeu`, SC `quem_recebeu`; **PB e PR sem valor** (o FAQ não diz e o critério do PR não foi dado, Q176-C8). Por isso `Criterio_Reconhecimento` e `Estabelecimento_Informante` ficaram **opcionais**.
7. **C130 só na saída** (Q176-12): `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms`, 1:1 com a nota, sem pai genérico; o C171 (tanque) não entrou, vai ao Bloco 1 de combustíveis.
8. **`COD_INS_SUBST` não criado** no K235, no K255 e no K275 (D-N483). A descrição do K275 nos documentos 167 e 168 **não foi reescrita** nesses documentos: a decisão está nos documentos 14 e 38.
9. **Domínios.** `tipo_documento_iss_df` (8 valores) entrou como domínio; `tipo_conhecimento_embarque`, pedido pelo 175, **já existia** (documento 43, os mesmos 22 valores) e foi reaproveitado; saem `codigo_informacao_adicional_apuracao_icms` e `motivo_restituicao_complemento_icms_st`, trocados por entidades com UF e vigência.
10. **Avisos do Motor.** Os 18 avisos dos documentos 175 e 176 estão **registrados no anexo do documento 10**; **nenhum está programado**.
11. **Vigência das cargas.** Nas do 172 a vigência vem do arquivo (fim vazio vira 31/12/9999); nas do 175 (GIAF e NF3e) e do 176 (1601) o Guia e o FAQ não a fixam, e a coluna sai vazia para o contador definir.

# 3. O que entrou

## 3.1 Entidades novas (32)

| Entidade | Módulo | Vigência | Campos | Onda | Decisão |
|---|---|---|---|---|---|
| `Cad_Icms_Beneficio_Ajuste_Codigo` | Contabilidade & Fiscal | sim (mestre) | 12 | 3 | Documento 172; D-N474 e D-N479 (Q172-1 a Q172-10) |
| `Cad_Icms_Informacao_Adicional_Codigo` | Contabilidade & Fiscal | sim (mestre) | 12 | 3 | Documento 172; D-N474 e D-N479 (Q172-1 a Q172-10) |
| `Cad_Efd_Codigo_Estadual` | Contabilidade & Fiscal | sim (mestre) | 12 | 3 | Documento 172; D-N474 e D-N479 (Q172-1 a Q172-10) |
| `Cad_Iss_Df_Valor_Uniprofissional` | Contabilidade & Fiscal | sim (mestre) | 10 | 3 | Documento 172; D-N474 e D-N479 (Q172-1 a Q172-10) |
| `Mov_Exportacao_Declaracao` | Contabilidade & Fiscal | não | 15 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Valor_Agregado_Municipio` | Contabilidade & Fiscal | não | 8 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Documento_Dispositivo_Utilizado` | Contabilidade & Fiscal | não | 9 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Documento_Dispositivo_Cancelado` | Contabilidade & Fiscal | não | 4 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Dcta_Apuracao` | Contabilidade & Fiscal | não | 8 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Cad_Efd_Giaf_Campo` | Contabilidade & Fiscal | sim (mestre) | 13 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Efd_Giaf_Apuracao` | Contabilidade & Fiscal | não | 5 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Efd_Giaf_Valor` | Contabilidade & Fiscal | não | 5 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Ecf_Reducao_Z_Totalizador` | Contabilidade & Fiscal | não | 7 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Ecf_Reducao_Z_Totalizador_Item` | Contabilidade & Fiscal | não | 6 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Ecf_Reducao_Z_Analitico` | Contabilidade & Fiscal | não | 12 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Convenio115_Consolidacao` | Contabilidade & Fiscal | não | 11 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Convenio115_Consolidacao_Analitico` | Contabilidade & Fiscal | não | 14 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Convenio115_Consolidacao_Uf` | Contabilidade & Fiscal | não | 7 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Sat_Resumo_Observacao` | Contabilidade & Fiscal | não | 8 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Sat_Resumo_Ajuste` | Contabilidade & Fiscal | não | 10 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Documento_Arrecadacao` | Contabilidade & Fiscal | não | 11 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Fatura_Comercial` | Contabilidade & Fiscal | não | 7 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Saida_Servico_Nao_Icms` | Contabilidade & Fiscal | não | 7 | 4 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Saida_Combustivel_Transporte` | Contabilidade & Fiscal | não | 6 | 4 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Entrada_Item_Lote` | Contabilidade & Fiscal | não | 4 | 4 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao` | Contabilidade & Fiscal | não | 7 | 4 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Icms_St_Uf_Recolhimento` | Contabilidade & Fiscal | não | 6 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Bilhete_Passagem_Consolidado` | Contabilidade & Fiscal | não | 23 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Bilhete_Passagem_Cancelado` | Contabilidade & Fiscal | não | 3 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Bilhete_Passagem_Municipio` | Contabilidade & Fiscal | não | 8 | 3 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Mov_Nota_Fiscal_Saida_Terminal_Faturado` | Contabilidade & Fiscal | não | 8 | 4 | Documento 175; D-N480 (Q175-1 a Q175-9) |
| `Cad_Efd_1601_Regra_Uf` | Contabilidade & Fiscal | sim (mestre) | 12 | 3 | Documento 176; D-N481 a D-N484 (Q176-1 a Q176-11) |

(A coluna de campos conta o que está no modelo, inclusive identificador, versão e trio de vigência.)

## 3.2 Campos novos em entidades existentes (43, em 22 entidades alteradas)

| Entidade | Módulo | Campos novos | Quais | Campos com tipo ou texto alterado |
|---|---|---|---|---|
| `Cad_Classe_Sistema` | Motores Transversais | 0 | — | Dominio |
| `Cad_Instituicao_Financeira` | Motores Transversais | 1 | ID_Participante | — |
| `Cad_Produto_Servico_Conversao_Unidade` | Motores Transversais | 1 | Codigo_Barras | — |
| `Mov_Nota_Fiscal_Entrada_Item` | Compras | 2 | Medicamento_Indicador_Base_Calculo, Medicamento_Tipo_Produto | Valor_Unitario_Liquido, Valor_Total_Liquido |
| `Mov_Inventario_Item` | Estoque | 2 | Texto_Complementar, ID_Conta_Contabil | — |
| `Mov_Estoque_Reclassificacao` | Estoque | 0 | — | Motivo_Reclassificacao |
| `Mov_Nota_Fiscal_Saida` | CRM & Vendas | 6 | Numero_Contador_Cupom_Fiscal, ID_Reducao_Z, ID_Tipo_Assinante, ID_Municipio_Origem_Servico, ID_Participante_Agencia, ID_Nota_Rmd | — |
| `Mov_Nota_Fiscal_Saida_Item` | CRM & Vendas | 6 | Indicador_Receita_Energia, ID_Participante_Receita_Terceiro, Quantidade_Cancelada, Medicamento_Indicador_Base_Calculo, Medicamento_Tipo_Produto, ID_Classe_Enquadramento_Ipi | Valor_Unitario_Liquido, Valor_Total_Liquido |
| `Mov_Titulo_Baixa` | Contas a Pagar/Receber | 3 | ID_Participante_Instituicao_Pagamento, ID_Participante_Intermediador, Classe_Incidencia_1601 | ID_Conta_Contabil |
| `Mov_Credito_Fiscal` | Contabilidade & Fiscal | 1 | ID_Icms_Codigo_Ajuste | Origem, ID_Participante_Cedente |
| `Mov_Credito_Fiscal_Aplicacao` | Contabilidade & Fiscal | 3 | ID_Efd_Codigo_Estadual_Tipo_Utilizacao, Numero_Documento_Baixa, Chave_Documento_Eletronico | — |
| `Cad_Filial_Perfil_Fiscal` | Contabilidade & Fiscal | 1 | Informa_Ordem_Producao_Bloco_K | — |
| `Mov_Nota_Fiscal_Saida_Item_Exportacao` | Contabilidade & Fiscal | 3 | ID_Exportacao_Declaracao, ID_Nota_Fiscal_Entrada, Numero_Memorando_Exportacao | — |
| `Mov_Cte` | Contabilidade & Fiscal | 4 | Numero_Despacho, ID_Tipo_Transporte_Carga, ID_Municipio_Coleta, ID_Municipio_Entrega | — |
| `Mov_Cte_Documento_Transportado` | Contabilidade & Fiscal | 2 | Quantidade_Volumes, Peso_Liquido_Kg | Peso_Kg |
| `Cad_Icms_Codigo_Ajuste` | Contabilidade & Fiscal | 3 | Situacao_Dado, ID_Instancia_Aprovacao, Alerta_Carga | Tipo_Apuracao, Natureza, Tabela_Origem, Indicador_Subapuracao |
| `Cad_Icms_Obrigacao_Recolher` | Contabilidade & Fiscal | 5 | ID_Natureza_Receita, Forma_Recolhimento, Situacao_Dado, ID_Instancia_Aprovacao, Alerta_Carga | ID_Estado, ID_Obrigacao_Recolher, Codigo_Receita |
| `Mov_Apuracao_Informacao_Adicional` | Contabilidade & Fiscal | 0 | — | ID_Codigo_Informacao_Adicional |
| `Mov_Icms_St_Complemento_Devolucao_Saida` | Contabilidade & Fiscal | 0 | — | ID_Motivo_Restituicao_Complemento |
| `Mov_Icms_St_Complemento_Saida` | Contabilidade & Fiscal | 0 | — | ID_Motivo_Restituicao_Complemento |
| `Mov_Icms_St_Complemento_Saida_Entrada` | Contabilidade & Fiscal | 0 | — | ID_Motivo_Restituicao_Complemento |
| `Cad_Utilidade_Classificacao_Efd` | Contabilidade & Fiscal | 0 | — | Campo_Efd_Destino |

## 3.3 Domínios e valores novos

- **9 domínios novos** em `Cad_Classe_Sistema.Dominio`, todos abertos (143 valores): `natureza_receita_icms_uf` (19), `classe_enquadramento_ipi` (31), `selo_controle_ipi` (50), `classificacao_contribuinte_ipi` (10) e `tipo_documento_iss_df` (8), do documento 172; `tipo_dispositivo_documento_fiscal` (6), `tipo_transporte_carga_efd` (7), `tipo_assinante_comunicacao_efd` (6) e `tipo_servico_terminal_efd` (6), do documento 175. Os de IPI entram como catálogo, sem uso até o contador dizer onde se aplicam (Q172-C7).
- **2 domínios que saem:** `codigo_informacao_adicional_apuracao_icms` e `motivo_restituicao_complemento_icms_st`.
- **Valores novos em domínios existentes (carga, sem mudança de estrutura):** `modulo_fiscal_opcional` ganha 13 habilitações por empresa (nenhuma ligada por padrão; o C165 só para distribuidora, refinaria e revendedora) e `bloco_destino_baixa` ganha `efd_1601`.
- **Valores de enumeração novos em campos:** `Mov_Credito_Fiscal.Origem` (`transferencia_icms_recebida`) e `Mov_Estoque_Reclassificacao.Motivo_Reclassificacao` (`deterioracao`, `obsolescencia_reaproveitamento`, `estoque_por_cliente` e `aglutinacao_insumo`).

## 3.4 Textos corrigidos (sem campo)

1. **Valor líquido da NT 2026.008** (`Valor_Total_Liquido` e `Valor_Unitario_Liquido` das notas de saída e de entrada): **não entra na EFD**, que usa o bruto (FAQ 19.2 e 19.3); IBS, CBS e IS não são apurados na EFD (19.1).
2. **Identidade de `Cad_Icms_Obrigacao_Recolher`:** UF mais código de receita mais início da vigência; a obrigação nacional sai da identidade e fica opcional, porque o arquivo do validador não a traz.
3. **`Cad_Icms_Codigo_Ajuste`:** a apuração e a natureza vêm do 3º e do 4º caractere do código; a conferência da Q172-C2 está no texto de `Indicador_Subapuracao` (o 4º caractere vai de 0 a 5 e 9 nas 10.626 linhas de UF, e não "de 3 a 8").
4. **`Mov_Titulo_Baixa.ID_Conta_Contabil`:** a filial titular da conta bancária informa o 1601 (D-N484).
5. **C130 e K275:** a correção do C130 (só saída; D-N487) e o "decidido: não preencher" do K275 (D-N483) constam nos documentos 14 e 38.

## 3.5 Cargas (pacote `Carga32`)

| Pasta | Conteúdo |
|---|---|
| `01-validador-doc172` | Do validador (197 arquivos, 42.679 linhas lidas, a versão mais nova de cada tabela): ajustes de ICMS (10,670 linhas, 13 delas de IPI), ajustes de benefício (3,376), informação adicional (6,831), códigos de receita (2,162), listas estaduais (1,247, já com a tabela 4.4.6), ISS do DF (4), o registro dos 197 arquivos (versão, linhas, hash SHA-256 e codificação), os tipos de tabela, a ligação de países por nome, o relatório de avisos e as 7 linhas de teste não carregadas |
| `02-lacunas-doc175` | 36 campos da GIAF de Pernambuco e 23 linhas do mapa de classificação da NF3e |
| `03-faq-doc176` | 7 linhas da regra do 1601 por UF e, em texto, a regra de `Cad_Tipo_Baixa_Bloco`, do perfil fiscal e dos motivos de reclassificação |
| `04-dominios` | 157 valores de `Cad_Classe_Sistema` (9 domínios novos, 13 habilitações e `efd_1601`) |

Total: 24,513 linhas (sem o registro dos arquivos, o relatório e a ligação de países). **Avisos da carga** (nunca bloqueiam; o texto vai como veio): vigência de um dia em 1,057 linhas, aspas ou tabulação no texto em 1,690, espaço sobrando em 825 e um texto truncado na fonte (sem a primeira letra). A ligação de países por nome dá 247 pares, 4 só no Bacen e 13 só no Siscomex: é conferência, não carga. **Sem carga:** as 7 linhas de teste, o vínculo entre ajuste de benefício e ajuste da apuração (só por pessoa), a classificação da NFGás e tudo o que depende do documento 177. Como o `Carga31`, é uma **extração direta**: a conversão de nomes de coluna para os campos fica para o script de carga da equipe.

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Documento 158** (B3: compras governamentais e Zona Franca de Manaus) | Q158-1 a Q158-13 sem resposta | Documento 38, seção 1.20 |
| **Documento 177** (transação de cartão e as sete datas) | Q177-1 a Q177-5 sem resposta; muda a leitura do 1601 de cartão (`Data_Autorizacao` no lugar da `dPag`) | Documento 38, seção 1.23 |
| **Bloco 1 de combustíveis e usina** (1300 a 1391, com o C171) | Você pediu um bloco próprio (Q167-6) | Documento 38, seção 1.13 |
| **Tabela de cClass da NFGás** | Sem a tabela; a carga fica vazia, com aviso do Motor | Documento 38, seção 1.21 |
| **Indicador de atividade rural (Q93-6)** | O desenho como linha do catálogo ainda não foi escrito | Documento 38, seção 0 |
| **Perguntas ao contador** (Q172-C2 a C9, Q175-C1 a C8 e Q176-C8) e à equipe (seções 3.11, 3.13 e 3.14) | Sem resposta; o desenho entrou com a leitura provisória de cada uma | Documento 38, seções 2.15, 2.17, 2.18, 3.11, 3.13 e 3.14 |
| **Fórmulas de 2024 da ECF (Q152-4)** | A planilha do leiaute 11 continua fora do meu ambiente; **reenvie** | Documento 38, seção 0 |
| **Desenhos 159 e 160** | Ainda não escritos | Fila de desenho |

# 5. Pontos de atenção

- **A onda 0 tem 177 entidades** (eram 177), 1,806 campos e 400 chaves estrangeiras; a **onda 3 tem 551 entidades** (eram 524), 6,624 campos e 1,610 chaves; a **onda 4 tem 123** (eram 118), por causa de cinco entidades de nota fiscal que exigem a nota de entrada.
- **A natureza do código de receita** (seção 2, item 4) é a leitura mais fraca desta carga: a lista de palavras é reconstruída, e a contagem não bate com a do documento 172. Se você preferir carga vazia, é só descartar a coluna.
- **Tabela de cada arquivo do Guia** (`Cad_Tabela_Oficial`): a ligação de cada um dos 197 arquivos a uma tabela do Guia é leitura minha, a confirmar pelo contador (C1 a C3).
- **Avisos do Motor** (18): registrados, não programados; a equipe decide quando.
- **Documentos de desenho 167, 168 e 176** não foram reescritos para as correções de texto (K275 e C130); valem as decisões dos documentos 14 e 38.
- **Documentos 172, 175, 176 e este relatório** seguem só em Word (o Projeto está cheio). O que entrou no dicionário está nos documentos 01, 03, 04, 05, 08 e 10; os documentos 14, 29, 31 e 38 foram atualizados no Projeto, e o modelo ER em Word foi regerado.
- **Numeração.** O número 177 continua com as Q177-1 a Q177-5 abertas; o 158, com as Q158-1 a Q158-13.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 32 entidades (290 campos no modelo), 43 campos novos em 22 entidades existentes e nenhum removido; nenhuma entidade mudou de módulo. As entidades novas são 4 do documento 172, 27 do 175 e 1 do 176.
- **Auditoria:** a primeira passada achou **1 ponto**: F1 (`Mov_Nota_Fiscal_Fatura_Comercial`, filha de pai genérico que ninguém aponta; aceita na lista, como as demais). Fechou com **0 achados em aberto**; nenhuma das outras 31 entidades novas ficou isolada.
- **DDL:** gerado nos dois dialetos (1.324 tabelas, 3.458 chaves estrangeiras, 3.546 índices e 10.266 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e as contagens do banco (tabelas, chaves estrangeiras e comentários) batem com as do gerador.
- **T-SQL:** 18.595 comandos lidos por analisador de sintaxe (sqlglot), sem erro; o aumento de 549 comandos é exatamente 38 tabelas, 105 chaves estrangeiras, 105 índices e 301 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos.
- **Carga32:** gerada por script a partir dos 197 arquivos do validador (cada arquivo com versão, hash e codificação registrados) e dos anexos dos documentos 175 e 176. As quantidades batem com as do documento 172 (3.383 de benefício menos 7 de teste; 6.831 de informação adicional; 2.162 de receita; 1.226 mais 21 de listas estaduais).
- **Limites:** nada foi validado pelo contador. A natureza do código de receita, a ligação dos arquivos às tabelas do Guia, a vigência de partida de parte das cargas e as leituras de "Sim" da seção 2 são minhas.
