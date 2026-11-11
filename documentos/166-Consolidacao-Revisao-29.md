# Consolidação da Revisão 29 — Documento 166

*Relatório do que entrou no dicionário com o seu "consolidar" de 03/11/2026, do que ficou de fora e de como conferi. A revisão 29 aplica **só o que você aprovou** (o escopo que você escolheu) e, porque você respondeu "Sim para todas" às Q165-1 a Q165-12 no meio do trabalho, também o **documento 165**. Entram **25 entidades novas (295 campos), 23 campos novos em 9 entidades existentes, 11 domínios novos e valores novos em outros campos de enumeração**. O dicionário passa de 995 entidades e 10.844 campos para **1.020 entidades e 11.162 campos**.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 28 | Revisão 29 | Diferença |
|---|---|---|---|
| Entidades | 995 | 1.020 | **+25** |
| Campos | 10.844 | 11.162 | **+318** (295 nas entidades novas e 23 em nove existentes) |
| Campos de referência (FK) | 2.861 | 2.928 | **+67** |
| Referências genéricas | 54 | 55 | **+1** (`Cad_Obrigacao_Parametro_Valor.ID_Registro_Referencia`) |
| Valores de `Cad_Classe_Sistema.Dominio` | 292 | 303 | **+11** |
| Entidades mestres (identidade e versão) | 196 | 198 | **+2** (o catálogo e os valores dos parâmetros por obrigação) |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.191 / 3.057 / 3.133 / 8.883 | 1.218 / 3.126 / 3.204 / 9.162 | +27 / +69 / +71 / +279 |
| Chaves estrangeiras que esperam a onda de destino | 66 | 69 | +3 |
| Comandos T-SQL lidos pelo analisador (sqlglot) | 16.265 | 16.711 | +446 (27 + 69 + 71 + 279, exatamente) |
| Carga de partida (provisória) | 6 + 2 + 1 linhas | pacote `Carga29` | ver seção 3.5 |

Aritmética conferida: 995 + 25 = 1.020 entidades; 10.844 + 318 = 11.162 campos (295 + 23); 2.861 + 67 = 2.928 campos de referência; 196 + 2 = 198 mestres, que viram 1.020 + 198 = 1.218 tabelas físicas.

Auditoria: **0 achados em aberto** depois de uma correção (a primeira passada achou 1 ponto; seção 6). **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.218 tabelas, 3.126 chaves estrangeiras e 9.162 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 77), Compras (25), CRM & Vendas (20), Contas a Pagar/Receber (25) e Contabilidade & Fiscal (47). **As 25 entidades novas estão na Contabilidade & Fiscal** (anexo da seção 43 do documento 10).

# 2. Como li o "consolidar"

Você escolheu "Só o que você aprovou". Entra o que está aprovado e **sem pergunta aberta sobre o campo**. O que ainda espera resposta fica de fora, só como proposta. As perguntas ao contador seguem abertas, então o que depende delas **entra com a minha leitura provisória**, a que o documento de origem já indicava. Se alguma estiver errada, diga e eu corrijo na revisão 30.

1. **Escopo.** Entram os documentos 155 (catálogo de parâmetros), 152 (Q152-2 e Q152-4), 153 (Q153-6 a Q153-15), 140 (B0b-1, Q140-1 a Q140-4), 138 (medicamentos, Q138-8 a Q138-10), 162, 163 e, pela sua resposta no meio do trabalho, o 165. **O documento 165 entrou depois do anúncio inicial do escopo**; eu avisei você na hora.
2. **Módulo e onda.** As 25 entidades ficam na **Contabilidade & Fiscal**. Dez delas ficam na **onda 3** do DDL; as **15 de NFGas e NF3e ficam na onda 4**, porque cada uma depende da nota de entrada (que é da onda 4) por chave estrangeira obrigatória.
3. **Mestres.** Só `Cad_Obrigacao_Parametro_Definicao` e `Cad_Obrigacao_Parametro_Valor` são mestres (`_Versao` e o trio de vigência). As outras têm vigência no padrão de linha com início, fim e motivo, ou não têm vigência.
4. **Opção B da Q155-2.** Os 11 campos de obrigação do perfil fiscal **ficam onde estão** e aparecem na tela do catálogo; a migração é obrigação por obrigação, depois. `Incidencia_Pis_Cofins`, `Forma_Apuracao_Irpj`, `ID_Segmento_Csll` e `Sujeita_Tef_Saf` ficam no perfil. Se você quis a opção A (migrar tudo agora), diga.
5. **`Data_Valor`.** O campo de data do valor do parâmetro se chama `Data_Valor` e não `Valor_Data` como no documento 155: a regra H2 da auditoria só aceita o prefixo `Valor_` em número, referência, texto e enumeração.
6. **Classificação do item de NFGas e NF3e.** O documento 165 apontava para uma entidade que não existe (`Cad_Classificacao_Item_Utilidade`). Entra como **referência a `Cad_Classe_Sistema`**, nos domínios `classificacao_item_nfgas` e `classificacao_item_nf3e`, **sem valores**, porque as tabelas de classificação (`cClass`) não chegaram.
7. **`Mov_Credito_Ajuste_Documento` com 13 campos**: os 12 do documento 153 mais `ID_Dfe_Evento` (Q153-11).
8. **Devolução.** `devolucao_nota_cancelada` e `devolucao_adiantamento` entram juntos em `Mov_Titulo.Origem_Tipo`, porque você confirmou os dois casos (Q153-7 e Q153-8). O rascunho da nota de débito 06 liga por parâmetro (Q153-14), que **substitui** a leitura da Q153-10 (só depois do contador).
9. **Vigências de partida (leitura minha).** `presumido_somente_por_refis`: 01/01/2026. `gera_rascunho_nota_debito_antecipacao` e a nova versão do adiantamento (CBS e IBS, base `valor_recebido_sem_tributo`): 01/01/2027, como a versão anterior. Bônus da CSLL (art. 41 da LC 225): **09/04/2026**, início dos arts. 40 a 47 pela minha conta.
10. **Motivos de substituição** da NFGas (01 a 06) e da NF3e (01 a 05) entram como domínios por modelo, com os **textos como placeholder** até chegar o MOC ou o texto da NT.
11. **Q152-4.** As três linhas da ECF "até 31/12/2025" (N620 18, N620 19 e N630A 18) passam a começar em 01/01/2025. **As três fórmulas de 2024 não foram carregadas**: o texto delas está na planilha do leiaute 11, que não está mais no meu ambiente (seção 4).

# 3. O que entrou

## 3.1 Entidades novas (25)

| Entidade | Vigência | Campos | Onda | Decisão |
|---|---|---|---|---|
| `Cad_Obrigacao_Parametro_Definicao` | sim (mestre) | 20 | 3 | Documento 155; Q155-1 a Q155-5 (D-N441) |
| `Cad_Obrigacao_Parametro_Valor` | sim (mestre) | 18 | 3 | Documento 155; Q155-1 a Q155-5 |
| `Mov_Apuracao_Ajuste_Criterio` | não | 11 | 3 | Documento 152, seção 6 (Q152-2) |
| `Mov_Credito_Ajuste_Documento` | não | 13 | 3 | Documento 153 (Q153-8, Q153-9 e Q153-11; D-N443 a D-N445) |
| `Cad_Empresa_Programa_Conformidade` | sim | 18 | 3 | Documento 140, seção 5 (Q140-1; D-N447) |
| `Mov_Selo_Conformidade` | não | 11 | 3 | Documento 140, seção 5 |
| `Mov_Condicao_Devedor_Contumaz` | não | 17 | 3 | Documento 140, seção 5 (Q140-2: só registra) |
| `Cad_Parametro_Bonus_Adimplencia` | sim | 16 | 3 | Documento 140, seção 5 (Q140-3 e Q140-4) |
| `Mov_Bonus_Adimplencia_Csll` | não | 18 | 3 | Documento 140, seção 5 |
| `Mov_Dfe_Evento_Simples_Item` | não | 11 | 3 | Documento 163 (Q163-3; provisória até o schema do evento 412140) |
| `Mov_Nfgas_Entrada` | não | 8 | 4 | Documento 165 (Q165-1 e Q165-2) |
| `Mov_Nfgas_Entrada_Item` | não | 14 | 4 | Documento 165 |
| `Mov_Nfgas_Entrada_Item_Tarifa` | não | 8 | 4 | Documento 165 (Q165-4) |
| `Mov_Nfgas_Entrada_Medidor` | não | 12 | 4 | Documento 165 |
| `Mov_Nfgas_Entrada_Item_Medicao` | não | 7 | 4 | Documento 165 |
| `Mov_Nfgas_Entrada_Volume_Contratado` | não | 5 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada` | não | 9 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada_Item` | não | 13 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada_Item_Tarifa` | não | 13 | 4 | Documento 165 (Q165-4) |
| `Mov_Nf3e_Entrada_Item_Bandeira` | não | 8 | 4 | Documento 165 (Q165-4) |
| `Mov_Nf3e_Entrada_Grandeza_Contratada` | não | 6 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada_Medidor` | não | 6 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada_Item_Medicao` | não | 15 | 4 | Documento 165 |
| `Mov_Nf3e_Entrada_Scee_Geradora` | não | 9 | 4 | Documento 165 (Q165-5) |
| `Mov_Nf3e_Entrada_Scee_Saldo` | não | 9 | 4 | Documento 165 (Q165-5) |

Soma: as 10 da onda 3 têm 20 + 18 + 11 + 13 + 18 + 11 + 17 + 16 + 18 + 11 = **153 campos**; NFGas, 8 + 14 + 8 + 12 + 7 + 5 = **54**; NF3e, 9 + 13 + 13 + 8 + 6 + 6 + 15 + 9 + 9 = **88**; total **295**.

## 3.2 Campos novos em entidades existentes (23, em 9 entidades)

| Entidade | Campos novos | Decisão |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Atividade_Simples` (1) | Q163-2 |
| `Mov_Credito_Destino_Item` | `ID_Nota_Debito_Antecipacao` (1) | Q153-10 |
| `Mov_Cbs_Pedido_Ressarcimento` | `ID_Selo_Conformidade` (1) | Q140-1 |
| `Cad_Lista_Legal_Item` | `Codigo_Registro_Anvisa`, `ID_Indicacao_Registro`, `Condicao_Comprador` (3) | Q138-8 a Q138-10 |
| `Cad_Ponto_Servico_Utilidade` | tipo de acesso, subclasse, modalidade tarifária, nome da unidade, detalhe da classe e contrato (6) | Q165-3 |
| `Mov_Nota_Fiscal_Entrada_Item` | `Chave_Dfe_Pagamento_Antecipado`, `Numero_Item_Pagamento_Antecipado` (2) | Q165-7 |
| `Mov_Nfag_Entrada` | `Tipo_Pagamento_Antecipado` (1) | Q165-8 |
| `Mov_Nfag_Entrada_Item` | `Valor_Total_Documento_Agregado`, `Chave_Nota_Anterior`, `Numero_Item_Anterior` (3) | Q165-8 |
| `Mov_Nota_Fiscal_Entrada_Referenciada` | `Modelo_Papel`, `Cnpj_Emitente_Papel`, `Serie_Papel`, `Numero_Papel`, `Competencia_Apuracao_Papel` (5) | Q165-9 |

Total: 1 + 1 + 1 + 3 + 6 + 2 + 1 + 3 + 5 = **23**.

## 3.3 Valores de enumeração novos

- **`Cad_Classe_Sistema.Dominio` (+11):** `programa_conformidade`, `classificacao_programa_conformidade`, `motivo_exclusao_programa`, `motivo_cancelamento_selo`, `tipo_documento_ajuste_ibs_cbs`, `indicacao_registro_medicamento`, `meio_pagamento_vinculo_dfe`, `classificacao_item_nfgas`, `classificacao_item_nf3e`, `motivo_substituicao_nfgas` e `motivo_substituicao_nf3e`.
- `Mov_Dfe_Evento.ID_Tipo_Evento`: `412140`, `110001` e `desfazimento_alienacao_abi`.
- `Mov_Titulo.Origem_Tipo`: `devolucao_nota_cancelada` e `devolucao_adiantamento`.
- `Status` de `Mov_Aquisicao_Imovel` e de `Mov_Operacao_Imobiliaria`: `desfeita`.
- `Mov_Nota_Fiscal_Entrada_Referenciada.Tipo_Referencia`: `faturamento_agregado` e `separada_judicialmente`.
- `Mov_Nfag_Entrada.ID_Tipo_Faturamento`: 4 e 5.

## 3.4 Texto de regra alterado (11 campos em 8 entidades)

`Mov_Apuracao_Irpj_Csll.Criterio_Reconhecimento_Aplicado` (agora aponta o ajuste de critério, Q152-2); `Mov_Credito_Aplicacao_Tributo.Competencia_Abatimento` (competência do débito da nota: data prevista de entrega, depois a de saída, depois a de emissão; Q153-15); `Cad_Adiantamento_Regra_Tributacao.Base_Calculo` (valor recebido sem o tributo); `Cad_CFOP` (`Indicador_Exclusivo_Ibs_Cbs`, título e descrição; Q162); `Mov_Dfe_Vinculo_Pagamento.ID_Meio_Pagamento` (domínio `meio_pagamento_vinculo_dfe`; aviso, sem bloqueio; Q162); `Mov_Parcelamento_Tributario.ID_Origem_Parcelamento` (`confia_art_25` e `sintonia_art_32`); `Cad_Lista_Legal_Item` (tipo de lista `medicamento_art146` e regra "um entre NCM, NBS e registro"; Q138); `Mov_Nota_Fiscal_Entrada_Referenciada.ID_Motivo_Substituicao` (domínios por modelo). Mais o texto do anexo da seção 43 do documento 10 (lista legal e chave de negócio).

## 3.5 Cargas (pacote `Carga29`)

| Carga | Conteúdo |
|---|---|
| `Cad_Obrigacao_Parametro_Definicao` (2 linhas) | `presumido_somente_por_refis` (ECF, booleano, por empresa, sem valor padrão) e `gera_rascunho_nota_debito_antecipacao` (apuração do IBS e da CBS) |
| `Cad_Obrigacao_Parametro_Valor` (modelo, 1 linha) | O rascunho da nota 06 **ligado**, para cada empresa que você indicar (Q153-14). `presumido_somente_por_refis` fica **sem valor** de propósito: vazio é "ninguém respondeu" |
| `Cad_Adiantamento_Regra_Tributacao` (2 versões novas) | CBS e IBS com `Base_Calculo` = `valor_recebido_sem_tributo` (Q153-13); provisórias |
| `Cad_Parametro_Bonus_Adimplencia` (1 linha) | Art. 41 da LC 225: 1% inicial, 12 meses, +1% a cada 12 meses, teto 3%, limites anuais de R$ 250.000, R$ 500.000 e R$ 1.000.000, **não vale para o Simples**; provisória |
| `Cad_Classe_Sistema` (50 valores) | Os valores dos domínios novos e os valores novos dos existentes; provisórios. **Sem valores**: `classificacao_programa_conformidade`, `classificacao_item_nfgas` e `classificacao_item_nf3e` (faltam o ato da RFB e as tabelas de classificação); placeholders nos motivos de substituição |
| `Cad_Permissao` (modelo) | "Parametrizar obrigação" (contador) e a da carga manual da lista de medicamentos do art. 146, com nome a definir |
| ECF: 3 linhas a alterar | N620 18, N620 19 e N630A 18 passam a começar em 01/01/2025 (Q152-4); **as fórmulas de 2024 estão pendentes** (`PENDENTE_Formulas_2024.csv`) |

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Documento 164 (BP-e)**, Q164-1 a Q164-12 | Sem resposta sua | Documento 38, seção 1.11 |
| **Q161-1 e Q161-2** (`Cad_Cclasstrib`) | Sem resposta sua | Documento 38, seção 1.8 |
| **Indicador de atividade rural (Q93-6)** | O desenho como linha do catálogo (regra da Q152-1) ainda não foi escrito | Documento 38, seção 0 |
| **Fórmulas de 2024 da ECF (Q152-4, carga)** | A planilha do leiaute 11 não está mais no meu ambiente; **reenvie** | Documento 38, seção 0 e 3.2 |
| **Desenhos B5, arts. 5º, 57 e 12 (156), B0a, B3 e os 43 artigos da LC 227** | Ainda não escritos; faltam a LC 227 em PDF e o texto do Decreto 12.955 | Documento 38, seção 1.8 (Q161-4) |
| **Tabela `Cad_Aliquota_Combustivel` (Q140-7)** | Espera o B5 | Documento 38, seção 1.5b |
| **Guia Prático da EFD-ICMS/IPI v3.2.4** | Nada aplicado. Sua frase era uma pergunta ("o desenho cobre?"); a conferência registro a registro (documento 167) mostrou que cobre em parte e deixou as lacunas como proposta, com as perguntas Q167-1 a Q167-6 | Documentos 14 (D-N457 e D-N459), 38 (seção 1.13) e 167 |
| **Perguntas ao contador** (Q153-C1 a Q153-C9, Q155-C1, Q162-C1, Q163-C1 a Q163-C3, Q165-C1 a Q165-C5) | Sem resposta; o desenho entrou com a leitura provisória de cada uma | Documento 38, seção 2 |

# 5. Pontos de atenção

- **A onda 4 pesa agora 108 entidades** (eram 93), 1.232 campos e 389 chaves estrangeiras; a onda 3 tem 487 entidades (eram 477), 5.799 campos e 1.407 chaves. As chaves estrangeiras opcionais que esperam a onda de destino passam de 66 para 69 (as três novas apontam para `Mov_Nota_Fiscal_Saida`, na onda 4: `ID_Nota_Debito_Antecipacao`, `ID_Nota_Fiscal_Saida` do ajuste de critério e `ID_Nota_Ajuste`).
- **O catálogo central é a regra.** Quem tem a permissão "Parametrizar obrigação" altera; todo valor nasce provisório; vazio nunca vira padrão escondido. Os 11 campos de obrigação do perfil continuam onde estão (opção B).
- **NFGas e NF3e são só de entrada**, como a D-N141 manda; a emissão fica como reserva. Várias regras dependem de textos que ainda não chegaram: as NT 2026.001, .002, .004 e .005, o MOC da NF3e e da NFCom e as tabelas de classificação de item. Os parâmetros ficam em `Cad_Dfe_Parametro_Regra` **sem valor**.
- **Medicamentos do art. 146.** O Motor só **sugere** o enquadramento pelo registro da Anvisa e pela qualificação do comprador; o usuário confirma na linha. A lista do ato conjunto (a cada 120 dias) entra por carga manual.
- **Bônus da CSLL.** Só registra e calcula na linha de CSLL paga à vista; a data de início, o tratamento contábil e o mecanismo do desconto dependem do contador e da RFB (Q140-5 e Q140-6).
- **Documentos 152 a 165** seguem só em Word (o Projeto está cheio); o documento 166 também. O que entrou no dicionário está nos documentos 01, 03, 05, 08 e 10.
- **Numeração.** O número 150 continua reservado ao B5; os 156 a 160 aos desenhos da fila.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 25 entidades (295 campos) e 23 campos novos em 9 entidades existentes; o tipo ou o texto de 19 campos em 14 entidades mudou (20 entidades existentes alteradas ao todo); **nenhum campo foi removido** e nenhuma entidade mudou de módulo. Conferi as contagens por entidade contra as tabelas dos documentos 140, 152, 153, 155, 163 e 165 e as somas de 153, 54 e 88.
- **Auditoria:** a primeira passada achou **1 ponto** (D1: o documento 165 apontava para `Cad_Classificacao_Item_Utilidade`, que não existe; passou a referência a `Cad_Classe_Sistema`). Dois ajustes antes da passada: `Valor_Data` virou `Data_Valor` (regra H2) e um erro de digitação em valor de enumeração foi corrigido. Fechou com **0 achados em aberto**.
- **DDL:** gerado nos dois dialetos (1.218 tabelas, 3.126 chaves estrangeiras, 3.204 índices e 9.162 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e as contagens do banco batem com as do gerador.
- **T-SQL:** 16.711 comandos lidos por analisador de sintaxe (sqlglot), sem erro; o aumento de 446 comandos é exatamente 27 tabelas, 69 chaves estrangeiras, 71 índices e 279 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos.
- **Carga29:** gerada por script; as três linhas da ECF vêm da Carga26 com só a data de início alterada.
- **Limites:** nada foi validado pelo contador. A vigência de partida das cargas, os valores do bônus da CSLL e a base do adiantamento no recebimento são leituras minhas. Os códigos `tPag` 23 e 24 são provisórios até a tabela nacional.
