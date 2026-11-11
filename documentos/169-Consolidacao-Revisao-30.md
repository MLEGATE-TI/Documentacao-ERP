# Consolidação da Revisão 30 — Documento 169

*Relatório do que entrou no dicionário com o seu "consolidar" de 04/11/2026, do que ficou de fora e de como conferi. A revisão 30 aplica **só o que você aprovou** (o mesmo escopo da revisão 29): os documentos **156** (arts. 5º, 57 e 12 da LC 214), **164** (BP-e, modelo 63) e **168** (lacunas G1 a G14 da EFD-ICMS/IPI), a Q161-1 e a Q161-2 e a correção de texto da Q138-3. Entram **28 entidades novas (342 campos)**, **102 campos novos em 30 entidades existentes** (37 alteradas ao todo), 19 domínios novos e as cargas de partida do pacote `Carga30`. O documento 157 ficou de fora (Q157-1 a Q157-14 sem resposta).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 29 | Revisão 30 | Diferença |
|---|---|---|---|
| Entidades | 1.020 | 1.048 | **+28** |
| Campos | 11.162 | 11.606 | **+444** (342 nas entidades novas e 102 em 30 existentes) |
| Campos de referência (FK) | 2.928 | 3.032 | **+104** |
| Referências genéricas | 55 | 58 | **+3** (`Mov_Valor_Mercado_Apuracao.ID_Item_Origem`, `Mov_Apuracao_Tributo_Item_Base_Especial.ID_Origem` e `Mov_Nota_Iss_Df_Complemento.ID_Nota`) |
| Valores de `Cad_Classe_Sistema.Dominio` | 303 | 322 | **+19** |
| Entidades mestres (identidade e versão) | 198 | 200 | **+2** (`Cad_Bloco_K_Exigencia_Registro` e `Cad_Utilidade_Classificacao_Efd`) |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.218 / 3.126 / 3.204 / 9.162 | 1.248 / 3.232 / 3.313 / 9.561 | +30 / +106 / +109 / +399 |
| Chaves estrangeiras que esperam a onda de destino | 69 | 70 | +1 (`Mov_Uso_Consumo_Pessoal_Item.ID_Item_Nota_Entrada`, onda 4) |
| Comandos T-SQL lidos pelo analisador (sqlglot) | 16.711 | 17.355 | +644 (30 + 106 + 109 + 399, exatamente) |
| Carga de partida (provisória) | pacote `Carga29` | pacote `Carga30` | ver seção 3.5 |

Aritmética conferida: 1.020 + 28 = 1.048 entidades; 11.162 + 444 = 11.606 campos (342 + 102); 2.928 + 104 = 3.032 campos de referência; 198 + 2 = 200 mestres, que viram 1.048 + 200 = 1.248 tabelas físicas.

Auditoria: **0 achados em aberto** depois de duas correções (a primeira passada achou 4 pontos; seção 6). **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.248 tabelas, 3.232 chaves estrangeiras, 3.313 índices e 9.561 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 78), Estoque (17), Compras (26), CRM & Vendas (21), Produção (16) e Contabilidade & Fiscal (48). **As 28 entidades novas estão na Contabilidade & Fiscal** (anexo da seção 44 do documento 10).

# 2. Como li o "consolidar"

Você já tinha escolhido "Só o que você aprovou". Entra o que está aprovado e **sem pergunta aberta sobre o campo**; o que espera resposta fica de fora. As perguntas ao contador seguem abertas, então o que depende delas **entra com a leitura provisória** que o documento de origem já indicava.

1. **Escopo.** Entram o documento 156 (Q156-1 a Q156-15 "Sim", com a sua regra da Q156-8: a variação cambial da **venda** é o valor convertido na data, e a da **baixa** vem da baixa do contas a pagar ou a receber, com a taxa do contrato de câmbio; o dicionário não ganha campo por isso), o documento 164 ("Seguir com todas as recomendações" às Q164-1 a Q164-12), o documento 168 (Q167-1 "sim", Q167-3 "controlar no estoque de terceiros", Q168-1 "finalidade própria", Q168-2 "sim", Q168-3 e Q168-4 "manter", Q168-5 "entra"), a Q161-1 e a Q161-2 e a Q138-3 (correção de texto).
2. **Módulo e onda.** As 28 entidades ficam na **Contabilidade & Fiscal**. Dezoito ficam na onda 3 e **dez na onda 4** do DDL (três do BP-e, os quatro complementos de ST, o CIAP por documento, o item da operação equiparada e a alienação do uso pessoal), porque dependem da nota de saída ou de entrada por chave estrangeira obrigatória.
3. **Mestres.** `Cad_Bloco_K_Exigencia_Registro` e `Cad_Utilidade_Classificacao_Efd` são mestres (`_Versao` e o trio de vigência), como o documento 168 desenhou. As regras do documento 156 têm vigência no padrão de linha (início, fim e motivo).
4. **Domínios.** Entram 19 domínios novos em `Cad_Classe_Sistema` e valores novos em domínios existentes (seção 3.3). Os **códigos** de componentes da base, de métodos e de hipóteses do valor de mercado são **propostas minhas**, porque o documento 156 só os descreve.
5. **BP-e (Q164-1).** Li "seguir com todas as recomendações" como **rodoviário, aquaviário e ferroviário mais o aéreo** agora (obrigatório a partir de 01/12/2026) e o **metropolitano só com cliente** (esboço, D-N68). **Esta é a leitura que você precisa confirmar.**
6. **Material de terceiros (G10).** O K200 e o H010 saem do saldo por propriedade; o custo médio ignora o que não é próprio; o material do encomendante tem movimento **sem valor** e saída física na ordem de industrialização (Q167-3, opção a). Por isso os textos das seções 8.2 do documento 06 e da nota de `Mov_Saldo_Estoque.Propriedade` (documento 04) foram corrigidos.
7. **Q161-1 e Q161-2.** `Indicador_Grupo_Biocombustivel_Diferenca` (booleano) e `Codigo_Anexo_Tecnico` (código de 5 posições, opcional) em `Cad_Cclasstrib`; `Indicador_Mono_Dif` fica marcado "excluído na IT v1.60; sem uso a partir da carga v1.60", **sem ser apagado**.
8. **Documento 157 fora.** Q157-1 a Q157-14 estão sem resposta. O campo `Valor_Acrescimos` do estorno do uso pessoal fica como estava, com a nota "a calcular pelo parâmetro do B0a (documento 157, ainda não consolidado)".

# 3. O que entrou

## 3.1 Entidades novas (28)

| Entidade | Vigência | Campos | Onda | Decisão |
|---|---|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item_Equiparada` | não | 8 | 4 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Criterio_Uso_Preponderante` | sim | 27 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Regra_Uso_Consumo_Pessoal` | sim | 12 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Regra_Uso_Consumo_Pessoal_Codigo` | não | 5 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Uso_Consumo_Pessoal_Item` | não | 21 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Uso_Consumo_Pessoal_Alienacao` | não | 9 | 4 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Regra_Base_Calculo_Cbs` | sim | 16 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Regra_Valor_Mercado` | sim | 13 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Valor_Mercado_Apuracao` | não | 20 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Valor_Mercado_Comparavel` | não | 9 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Apuracao_Tributo_Item_Base_Especial` | não | 7 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Cad_Regra_Conversao_Cambial_Base` | sim | 13 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Energia_Ccee_Liquidacao` | não | 10 | 3 | Documento 156; D-N463 e D-N465 (Q156-1 a Q156-15) |
| `Mov_Bpe` | não | 27 | 4 | Documento 164; D-N462 (Q164-1 a Q164-12) |
| `Mov_Bpe_Viagem` | não | 20 | 4 | Documento 164; D-N462 (Q164-1 a Q164-12) |
| `Mov_Bpe_Componente` | não | 4 | 4 | Documento 164; D-N462 (Q164-1 a Q164-12) |
| `Mov_Bpe_Evento` | não | 4 | 3 | Documento 164; D-N462 (Q164-1 a Q164-12) |
| `Mov_Apuracao_Tributo_Item_Parcela_Icms` | não | 7 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Icms_St_Complemento_Entrada` | não | 13 | 4 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Icms_St_Complemento_Devolucao_Saida` | não | 14 | 4 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Icms_St_Complemento_Saida` | não | 15 | 4 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Icms_St_Complemento_Saida_Entrada` | não | 17 | 4 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Ciap_Movimentacao_Documento` | não | 12 | 4 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Cad_Bloco_K_Exigencia_Registro` | sim (mestre) | 8 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Cte_Simplificado_Prestacao` | não | 9 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Nota_Iss_Df_Complemento` | não | 6 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Mov_Iss_Df_Conta_Cosif` | não | 7 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |
| `Cad_Utilidade_Classificacao_Efd` | sim (mestre) | 9 | 3 | Documento 168; D-N460 e D-N461 (Q167-1, Q167-3, Q168-1 a Q168-5) |

(A coluna de campos conta o que está no modelo, inclusive identificador, versão e trio de vigência.)

## 3.2 Campos novos em entidades existentes (102, em 30 das 37 entidades alteradas)

| Entidade | Campos novos | Quais | Outras mudanças |
|---|---|---|---|
| `Cad_Cclasstrib` | 2 | Indicador_Grupo_Biocombustivel_Diferenca, Codigo_Anexo_Tecnico | texto de regra |
| `Cad_Classe_Sistema` | 0 |  | valores de enumeração |
| `Cad_Empresa_Perfil_Fiscal` | 1 | Atividade_Principal_Family_Office | — |
| `Cad_Empresa_Profissional_Habilitado` | 2 | Indicador_Habilitacao, Escolaridade_Efd | tipo, texto de regra |
| `Cad_Filial_Perfil_Fiscal` | 1 | Numero_Tar | — |
| `Cad_Icms_Codigo_Ajuste` | 1 | ID_Indicador_Beneficio_Padrao | — |
| `Cad_Municipio` | 1 | Tipo_Municipio | — |
| `Cad_Obrigacao_Leiaute_Campo` | 2 | Exigencia_Entrada, Exigencia_Saida | texto de regra |
| `Cad_Participante` | 0 |  | texto de regra |
| `Cad_Participante_Qualificacao_Cbs` | 0 |  | texto de regra |
| `Cad_Regra_Operacao_Equiparada_Cbs` | 6 | Alcanca_Valor_Inferior_Mercado, Exige_Credito_Na_Aquisicao, Aplica_Excecao_Preponderancia e mais 3 | texto de regra |
| `Cad_Tipo_Movimento_Estoque` | 1 | Propriedade_Movimento | valores de enumeração |
| `Mov_Apuracao_Ajuste` | 1 | ID_Indicador_Beneficio | — |
| `Mov_Apuracao_Ajuste_Documento` | 7 | ID_Participante, ID_Modelo_Documento, Serie e mais 4 | — |
| `Mov_Apuracao_Ipi` | 4 | Data_Inicio_Periodo, Data_Fim_Periodo, Outros_Debitos, Outros_Creditos | texto de regra |
| `Mov_Apuracao_Iss_Df` | 0 |  | texto de regra |
| `Mov_Apuracao_Obrigacao_Recolher` | 3 | ID_Origem_Processo, Descricao_Processo, Texto_Complementar | tipo, texto de regra |
| `Mov_Apuracao_Tributo_Item` | 1 | Aliquota_St | valores de enumeração |
| `Mov_Ciap_Bem_Item` | 8 | Indicador_Emitente_Documento_Anterior, ID_Participante_Documento_Anterior, ID_Modelo_Documento_Anterior e mais 5 | tipo, texto de regra |
| `Mov_Cte` | 0 |  | texto de regra |
| `Mov_Cte_Componente_Valor` | 2 | Classe_Componente, ID_Cte_Simplificado_Prestacao | — |
| `Mov_Estoque_Abertura_Cbs_Item` | 0 |  | texto de regra |
| `Mov_Estoque_Movimento_Item` | 2 | Propriedade, ID_Participante_Proprietario | — |
| `Mov_Icms_St_Ressarcimento` | 12 | ID_Responsavel_Retencao, Base_Icms_Ultima_Entrada_Unitaria, Aliquota_Icms_Ultima_Entrada e mais 9 | texto de regra |
| `Mov_Icms_St_Ressarcimento_Consolidado` | 4 | Icms_St_Restituicao, Fcp_St_Restituicao, Icms_St_Complemento, Fcp_St_Complemento | texto de regra |
| `Mov_Nfse_Dps` | 3 | Taxa_Cambio_Base, Data_Cotacao_Base, ID_Serie_Cotacao_Base | — |
| `Mov_Nota_Ajuste_Documento` | 1 | ID_Indicador_Beneficio | — |
| `Mov_Nota_Fiscal_Entrada` | 1 | Escriturada_Como_Saida | valores de enumeração |
| `Mov_Nota_Fiscal_Entrada_Item` | 1 | Valor_Desconto_Condicional_Item | texto de regra |
| `Mov_Nota_Fiscal_Entrada_Referenciada` | 9 | ID_Modelo_Documento_Referenciado, Serie_Referenciada, Subserie_Referenciada e mais 6 | — |
| `Mov_Nota_Fiscal_Saida` | 6 | ID_Moeda_Operacao, Valor_Operacao_Moeda, Taxa_Cambio_Base e mais 3 | — |
| `Mov_Nota_Fiscal_Saida_Item` | 1 | Valor_Desconto_Condicional_Item | valores de enumeração, texto de regra |
| `Mov_Nota_Fiscal_Saida_Pagamento` | 7 | Numero_Documento_Pagamento, Descricao_Forma_Pagamento, Descricao_Bandeira e mais 4 | texto de regra |
| `Mov_Nota_Fiscal_Saida_Referenciada` | 9 | ID_Modelo_Documento_Referenciado, Serie_Referenciada, Subserie_Referenciada e mais 6 | valores de enumeração, texto de regra |
| `Mov_Nota_Fiscal_Utilidade` | 2 | Valor_Energia_Injetada, Valor_Outras_Deducoes | texto de regra |
| `Mov_Ordem_Producao_Item` | 1 | Data_Consumo_Terceiro | texto de regra |
| `Mov_Saldo_Estoque` | 0 |  | texto de regra |

## 3.3 Domínios e valores novos

- **19 domínios novos** em `Cad_Classe_Sistema.Dominio`, todos abertos. Documento 156 (6): `grupo_criterio_uso_preponderante`, `hipotese_uso_consumo_pessoal`, `motivo_inelegibilidade_alienacao_uso_pessoal`, `componente_base_calculo_ibs_cbs`, `metodo_valor_mercado` e `hipotese_valor_mercado`. Documento 164 (8): `tipo_viagem_bpe_rodoviario`, `tipo_viagem_bpe_aereo`, `tipo_desconto_bpe_rodoviario`, `tipo_desconto_bpe_aereo`, `tipo_servico_bpe`, `tipo_acomodacao_bpe`, `tipo_veiculo_travessia_bpe` e `forma_pagamento_bpe`. Documento 168 (5): `indicador_beneficio_icms`, `responsavel_retencao_icms_st`, `motivo_restituicao_complemento_icms_st`, `origem_processo_icms` e `tipo_frete_redespacho`.
- **Valores novos em domínios existentes (carga, sem mudança de estrutura):** `modulo_fiscal_opcional` (`efd_c176`, `efd_c180`, `efd_c181`, `efd_c185`, `efd_c186`, `efd_1250_1255`), `situacao_documento_fiscal` (09 e 10), `modelo_documento_fiscal` (63), `tipo_operacao_equiparada` (`fornecimento_art5_i_a` e `fornecimento_art5_i_b`) e `qualificacao_cbs` (`agente_ccee`).
- **Valores de enumeração novos em campos:** `Finalidade` da nota de entrada (`credito`, `debito`), `Metodo_Valoracao` do tipo de movimento de estoque (`sem_valor`), `Tipo_Referencia` da referência da nota de saída (`bpe_substituido`, `bpe_multa_juros`, `bpe_multiplo`) e `Origem_Tipo` da apuração por item (`bpe_evento`).

## 3.4 Textos corrigidos (sem campo)

1. **Q138-3.** Documento 10, seção 10: o split **simplificado** não dá crédito ao adquirente (LC 214, art. 33, § 7º, II); sem campo até o split voltar (D-N282).
2. **Brinde a preço de aquisição.** Está no **Decreto 12.955, art. 14, § 8º**. A nota "não foi conferida no decreto" de `Cad_Regra_Operacao_Equiparada_Cbs.ID_Criterio_Base` foi trocada; o D-N285 do documento 14 **não** é reescrito (a correção está no D-N467).
3. **Numeração dos artigos.** "Arts. 11, 13 e 57 a 64" dos documentos 94 e 115 é numeração do Decreto (LC art. 12 = Decreto arts. 13 e 14; LC art. 57 = Decreto arts. 62 a 64). A leitura do documento 138 de que o D-N290 conflita com a LC 227 foi substituída.
4. **Material de terceiros.** Documento 06, seção 8.2 (dois textos) e documento 04 (`Mov_Saldo_Estoque.Propriedade`), pelo G10.
5. **IPI.** As descrições de `Ipi_Recolher` (VL_SD_IPI) e de `Saldo_Credor_Transportar` (VL_SC_IPI), que estavam trocadas, foram corrigidas.
6. **`Valor_Credito`** do ressarcimento consolidado de ST agora descreve o VL_CREDITO_ICMS_OP_MOT do 1255; `Valor_Debito` e `Valor_Total` ficam como informativos (Q168-4: "manter").

## 3.5 Cargas (pacote `Carga30`)

| Pasta | Conteúdo |
|---|---|
| `01-art5-art57-art12` | 21 critérios de uso preponderante, 8 linhas da regra de operação equiparada (2 novas), 12 hipóteses do art. 57 e 10 prefixos de NCM, 19 componentes da base, 8 métodos de valor de mercado e 2 regras de conversão cambial. Tudo provisório; a vigência de partida é 01/01/2026 (a confirmar pelo contador), e a linha do ICMS, ISS, PIS e Cofins vai só até 31/12/2032 |
| `02-dominios` | Valores novos de `Cad_Classe_Sistema`: os domínios novos e os valores em domínios existentes. As linhas "a carregar" marcam as tabelas que faltam |
| `03-bpe` | 8 eventos do modelo 63, 3 leiautes (BPe, BPeTA e BPeTM, v1.00, sem datas) e 7 parâmetros **sem valor** |
| `04-efd-icms-ipi` | Estado EX e os dois municípios-sentinela, os campos de 2027 do leiaute (IND_BENEFICIO e D100), 3 tipos de movimento de material de terceiros, a regra para os tipos existentes (`proprio`) e a regra do modelo 76 |
| `05-cclasstrib` | A regra de carga do cClassTrib (Q161-1 e Q161-2) |

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Documento 157 (B0a)**, Q157-1 a Q157-14 | Sem resposta sua | Documento 38, seção 1.15 |
| **BP-e metropolitano** (`Mov_Bpe_Tm_*`) | Esboço sem cliente (D-N68) | Documento 164 |
| **Indicador de atividade rural (Q93-6)** | O desenho como linha do catálogo ainda não foi escrito | Documento 38, seção 0 |
| **Cargas sem tabela oficial** | `motivo_restituicao_complemento_icms_st` (5.7), `Cad_Utilidade_Classificacao_Efd` (cClass), tabelas 5.3 e 5.5 em `Cad_Icms_Codigo_Ajuste` (Q167-5), `Cad_Bloco_K_Exigencia_Registro`, tabelas e cClassTrib do BP-e (Q164-12) | Documento 38, seções 1.13 e 3.2 |
| **Fórmulas de 2024 da ECF (Q152-4)** | A planilha do leiaute 11 continua fora do meu ambiente; **reenvie** | Documento 38, seção 0 e 3.2 |
| **Q167-2, Q167-5 e Q167-6** | Sem resposta sua | Documento 38, seção 1.13 |
| **Perguntas ao contador** (Q156-C1 a Q156-C4, Q164-C1 a Q164-C6 e as demais) | Sem resposta; o desenho entrou com a leitura provisória de cada uma | Documento 38, seção 2 |
| **Desenhos 150 (B5), 158, 159 e 160** | Ainda não escritos | Fila de desenho |

# 5. Pontos de atenção

- **A onda 4 pesa agora 118 entidades** (eram 108), 1.428 campos e 441 chaves estrangeiras; a onda 3 tem 505 entidades (eram 487), 6.045 campos e 1.459 chaves.
- **Leitura da Q164-1:** o aéreo entra e o metropolitano não. Se você queria só os três modais terrestres e aquaviário, o aéreo sai (6 campos de `Mov_Bpe` e os domínios `_aereo`).
- **Motivo de substituição do BP-e** entra como valores novos, pelo nome, no mesmo domínio do `ID_Motivo_Substituicao`. Se os códigos colidirem com os da NFCom, divido o domínio por modelo (como no documento 165).
- **Referências genéricas sem campo de tipo:** `Mov_Valor_Mercado_Apuracao.ID_Item_Origem` e `Mov_Apuracao_Tributo_Item_Base_Especial.ID_Origem`, como o documento 156 desenhou.
- **Três entidades novas aparecem como isoladas na auditoria (F1)** de propósito: `Cad_Bloco_K_Exigencia_Registro` e `Cad_Utilidade_Classificacao_Efd` (catálogos lidos por código) e `Mov_Nota_Iss_Df_Complemento` (ligada à nota por referência genérica). Ficam aceitas, como `Cad_Comex_Codigo`.
- **Valores de mercado e base especial** dependem do ato conjunto do art. 14, § 7º, IV do Decreto para a forma definitiva da memória; até lá o ERP registra e avisa.
- **Documentos 156, 157, 164, 167 e 168 e este relatório** seguem só em Word (o Projeto está cheio). O que entrou no dicionário está nos documentos 01, 03, 04, 05, 06 e 10; os documentos 14, 29, 31 e 38 foram atualizados no Projeto.
- **Numeração.** O número 150 continua reservado ao B5.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 28 entidades ({newf} campos) e 102 campos novos em 30 entidades existentes; **nenhum campo foi removido** e nenhuma entidade mudou de módulo. Conferi o número de campos de cada entidade nova contra as tabelas dos documentos 156, 164 e 168 (a do BP-e tem 27, 20, 4 e 4 campos: os dois campos do metropolitano ficaram de fora).
- **Auditoria:** a primeira passada achou **4 pontos**: C1 (`Serie_Documento_Anterior` sem tamanho, que passou a código de 3 posições) e F1 (as três entidades isoladas, aceitas de propósito). Fechou com **0 achados em aberto**.
- **DDL:** gerado nos dois dialetos (1.248 tabelas, 3.232 chaves estrangeiras, 3.313 índices e 9.561 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e as contagens do banco batem com as do gerador.
- **T-SQL:** 17.355 comandos lidos por analisador de sintaxe (sqlglot), sem erro; o aumento de 644 comandos é exatamente 30 tabelas, 106 chaves estrangeiras, 109 índices e 399 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos.
- **Carga30:** gerada por script a partir dos anexos A a E do documento 156 e dos documentos 164 e 168.
- **Limites:** nada foi validado pelo contador. A vigência de partida das cargas, os códigos de domínio novos do documento 156 e as colunas de exigência do leiaute de 2027 são leituras minhas.
