# Sumário

# Consolidação da Revisão 28 — Documento 154

*Relatório do que entrou no dicionário com o seu “consolidar” de 29/10/2026, do que ficou de fora e de como conferi. A revisão 28 aplica **tudo o que você aprovou** (o escopo que você escolheu): as respostas do **documento 152** (mapa da atividade de presunção,* `Mes_Competencia` *do Y681, critério de reconhecimento, natureza cambial do royalty e as regras de texto das Q127-4, Q128-4, Q128-6, Q128-7 e Q139-3) e o **adiantamento de clientes do documento 153** (IBS e CBS no recebimento). Entram **4 entidades novas (45 campos), 4 campos novos em 4 entidades existentes, 2 valores de enumeração novos e o texto de 6 campos em 6 entidades**. O dicionário passa de 991 entidades e 10.795 campos para **995 entidades e 10.844 campos**.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

|                                                            | Revisão 27                    | Revisão 28                    | Diferença                                                                                                              |
|------------------------------------------------------------|-------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Entidades                                                  | 991                           | 995                           | **+4**                                                                                                                 |
| Campos                                                     | 10.795                        | 10.844                        | **+49**                                                                                                                |
| Campos de referência (FK)                                  | 2.849                         | 2.861                         | **+12** (10 nas entidades novas e 2 nas existentes: `ID_Atividade_Presuncao` e `ID_Natureza_Operacao_Cambial_Royalty`) |
| Referências genéricas                                      | 53                            | 54                            | **+1** (`Mov_Credito_Destino_Item.ID_Item_Destino`)                                                                    |
| Valores de `Cad_Classe_Sistema.Dominio`                    | 292                           | 292                           | 0                                                                                                                      |
| Entidades mestres (identidade e versão)                    | 195                           | 196                           | **+1** (`Cad_Adiantamento_Regra_Tributacao`)                                                                           |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.186 / 3.044 / 3.119 / 8.838 | 1.191 / 3.057 / 3.133 / 8.883 | +5 / +13 / +14 / +45                                                                                                   |
| Comandos T-SQL lidos pelo analisador (sqlglot)             | 16.188                        | 16.265                        | +77 (5 + 13 + 14 + 45, exatamente)                                                                                     |
| Carga de partida (provisória)                              | 0                             | 6 + 2 + 1 linhas              | Pacote `Carga28-Adiantamento`                                                                                          |

Dos 49 campos novos, 45 estão nas quatro entidades novas (13 + 13 + 11 + 8) e 4 em entidades que já existiam. Aritmética conferida: 991 + 4 = 995 entidades, 10.795 + 49 = 10.844 campos e 2.849 + 12 = 2.861 campos de referência. As 196 entidades mestres são as 195 de antes mais `Cad_Adiantamento_Regra_Tributacao`.

**Uma diferença de contagem que você precisa saber.** Os documentos 127 e 152 diziam que `Cad_Atividade_Presuncao_Mapa` tinha **12 campos**. A tabela do documento 127 sempre teve **13 linhas** (identificador, empresa, os três prefixos, prioridade, atividade, segregação, observação, situação e os três campos de vigência), e foi essa tabela que apliquei. Por isso o total é **10.844** e não 10.843 (que era a conta do documento 153: 995 entidades e 10.843 campos).

Auditoria: **0 achados em aberto** na primeira passada. **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.191 tabelas, 3.057 chaves estrangeiras e 8.883 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 76), CRM & Vendas (19), Contas a Pagar/Receber (24) e Contabilidade & Fiscal (46). **As quatro entidades novas estão na Contabilidade & Fiscal** (anexo da seção 42 do documento 10), todas na onda 3 do DDL.

# 2. Como li o “consolidar”

Você respondeu “Tudo o que você aprovou (Recomendado)”. Entra o que está aprovado e **sem pergunta aberta sobre o campo**; o que ainda espera resposta fica de fora, só como proposta. As perguntas ao contador (Q153-C1 a Q153-C6, entre outras) seguem abertas, então o que depende delas **entra com a minha leitura provisória**, a que o documento 153 já indicava. Se alguma estiver errada, diga e eu corrijo na revisão 29.

- **Módulo.** As quatro entidades ficam na **Contabilidade & Fiscal**, como as do TEF da SAF na revisão 27, mesmo as duas que falam de `Mov_Credito` (que mora em Contas a Pagar/Receber). Motivo: o imposto do adiantamento nasce em `Mov_Apuracao_Tributo_Item`, que é fiscal, e a regra de tributação é parâmetro fiscal. Todas ficam na onda 3: as referências delas estão nas ondas 0, 1 e 3.
- **Mestres.** Só `Cad_Adiantamento_Regra_Tributacao` é mestre (`_Versao` e o trio de vigência). `Cad_Atividade_Presuncao_Mapa` tem vigência, mas no padrão de `Cad_Natureza_Operacao_Sugestao` (linha com início, fim e motivo, sem tabela de versão), como o documento 127 desenhou.
- **Carga da regra do adiantamento.** As 6 linhas saem com `Origem_Valor` = `resposta_do_gestor` e `Situacao_Dado` provisório. **Vigência de partida (leitura minha):** 01/01/2027 em CBS e IBS (início do regime) e 01/01/2026 em PIS, Cofins, IRPJ e CSLL (o regime de caixa já existe). Em CBS e IBS a `Base_Calculo` sai `a_definir`, então o imposto do adiantamento fica **pendente** até o contador definir (Q153-C1). Não há linha de competência nem de Simples Nacional, de propósito (Q153-C4).
- `Mes_Competencia`**.** Vai para a identidade da linha do Y681 e fica vazio nas demais linhas. O DDL só gera chave única nas entidades mestres; em `Mov_Ecf_Apuracao_Linha_Valor` (que não é mestre) a identidade fica documentada na descrição, como nas outras entidades que não são mestres.
- **Confirmação da mudança de critério (Q127-4).** Até você responder a Q152-2, a confirmação do usuário fica no histórico geral de auditoria, sem entidade própria.
- **Permissão (Q144-4).** “Decidir conflito de reimportação” é só linha de carga em `Cad_Permissao`, por perfil que você indicar; deixei um modelo no pacote de carga.
- **Q139-3 e Q139-4.** Só texto de regra, no campo `Formula` de `Cad_Ecf_Tabela_Dinamica_Linha`: o motor lê `"20.99"` onde a carga traz `"20:99"` e avisa; uma versão por anocalendário. A carga das fórmulas de 2024 continua esperando a Q152-4.

# 3. O que entrou

## 3.1 Entidades novas (4)

| Entidade                            | Vigência         | Campos | Decisão                                                   |
|-------------------------------------|------------------|--------|-----------------------------------------------------------|
| `Cad_Atividade_Presuncao_Mapa`      | sim (sem versão) | 13     | Documento 127, seção 5.3 (Q127-3); documento 152 (D-N432) |
| `Cad_Adiantamento_Regra_Tributacao` | sim (mestre)     | 13     | Documento 153, seção 4.2 (Q153-2; D-N436 e D-N438)        |
| `Mov_Credito_Destino_Item`          | não              | 11     | Documento 153, seção 4.1 (Q153-1, Q153-4)                 |
| `Mov_Credito_Aplicacao_Tributo`     | não              | 8      | Documento 153, seção 4.3 (Q153-3)                         |

Soma: 13 + 13 + 11 + 8 = **45 campos**. A lista completa, com os campos e as regras, está no anexo da seção 42 do documento 10 e nos documentos 127 e 153.

## 3.2 Campos novos em entidades existentes (4)

| Entidade                       | Campo novo                             | Decisão                                  |
|--------------------------------|----------------------------------------|------------------------------------------|
| `Mov_Ecf_Apuracao_Linha_Valor` | `Mes_Competencia`                      | Documento 128, seção 6.5 (Q128-3)        |
| `Mov_Apuracao_Irpj_Csll`       | `Criterio_Reconhecimento_Aplicado`     | Documento 127, seção 4.1 (Q127-2)        |
| `Mov_Nota_Fiscal_Saida_Item`   | `ID_Atividade_Presuncao`               | Documento 127, seção 5.3 (Q127-3)        |
| `Mov_Pedido_Venda_Item`        | `ID_Natureza_Operacao_Cambial_Royalty` | Documento 127, seção 6 (Q127-5, opção A) |

## 3.3 Valores de enumeração novos

- `Mov_Apuracao_Tributo_Item.Origem_Tipo`: `adiantamento_cliente` (IBS e CBS do recebimento do adiantamento; `ID_Item_Origem` aponta `Mov_Credito_Destino_Item`).
- `Cad_Motor_Regra_Resultado.Tipo_Resultado`: `id_natureza_operacao_cambial` (Q127-5).

## 3.4 Texto de regra alterado

| Onde                                                                                                                    | O que mudou                                                                                                                                                                    | Decisão                          |
|-------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------|
| `Mov_Ecf_Apuracao_Linha_Valor.Mes_Competencia`                                                                          | Y681 zerado aceito e gerado sem aviso; o ERP só avisa quando o importado diverge                                                                                               | Q128-4                           |
| `Mov_Apuracao_Irpj_Csll.Criterio_Reconhecimento_Aplicado` e `Cad_Empresa_Perfil_Fiscal.Criterio_Reconhecimento_Receita` | Na mudança de critério o ERP indica o que ajustar e o usuário confirma; nunca altera a receita por caixa sozinho                                                               | Q127-4                           |
| `Mov_Credito_Aplicacao.Data_Aplicacao`                                                                                  | IBS e CBS no recebimento com o local da operação; PIS e Cofins na emissão da nota; qual nota conta (a de entrega, se for de venda, ou a de faturamento; simples remessa nunca) | Q128-6, Q128-7 (D-N435 a D-N437) |
| `Mov_Titulo.ID_Natureza_Operacao_Cambial`                                                                               | No título `royalty_venda` a natureza vem herdada do item do pedido                                                                                                             | Q127-5                           |
| `Cad_Ecf_Tabela_Dinamica_Linha.Formula`                                                                                 | N670 21 lida como `"20.99"` com aviso; uma versão por anocalendário                                                                                                            | Q139-3, Q139-4                   |
| `Cad_Motor_Regra_Resultado.Tipo_Resultado`                                                                              | Descrição do valor novo                                                                                                                                                        | Q127-5                           |

## 3.5 Cargas (pacote `Carga28-Adiantamento`)

| Carga                                          | Conteúdo                                                                                                                                          |
|------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| `Cad_Adiantamento_Regra_Tributacao` (6 linhas) | CBS e IBS: qualquer regime, recebimento, base `a_definir`. PIS e Cofins: caixa, emissão da nota. IRPJ e CSLL: caixa, aplicação. Todas provisórias |
| `Cad_Atividade_Presuncao_Mapa`                 | **Vazia.** As 17 linhas da sua planilha só entram depois do código NBS                                                                            |
| Catálogo de eventos contábeis (2 linhas)       | Tributo no recebimento e baixa na aplicação, **sem conta** (Q153-C3); o lote sai pendente com aviso                                               |
| `Cad_Permissao` (modelo)                       | “Decidir conflito de reimportação”; você indica o perfil                                                                                          |

# 4. O que ficou de fora

| Item                                                          | Por que ficou                                                                          | Onde está                |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------|--------------------------|
| `Presumido_Somente_Por_Refis` (Q152-1)                        | Você ainda não aprovou o campo                                                         | Documento 38, seção 1.3a |
| `Mov_Apuracao_Ajuste_Criterio` (Q152-2, 11 campos)            | Você ainda não aprovou a entidade; até lá a confirmação fica no histórico de auditoria | Documento 38, seção 1.3a |
| **Fórmulas de 2024** (Q152-4, 3 linhas de carga)              | Esperam a sua resposta                                                                 | Documento 38, seção 1.3a |
| `devolucao_adiantamento` em `Mov_Titulo.Origem_Tipo` (Q153-6) | Você ainda não confirmou o título automático da devolução                              | Documento 38, seção 1.3b |
| **Indicador de atividade rural** (Q93-6)                      | O desenho do campo ainda não foi escrito                                               | Documento 38, seção 0    |
| **B0b-1** (LC 225/2026)                                       | Espera a Q140-1                                                                        | Documento 38, seção 1.5b |
| **Bares e restaurantes (B5)**                                 | É o próximo desenho, que você aprovou; ainda não foi escrito                           | Documento 150, reservado |
| **Perguntas ao contador** Q153-C1 a Q153-C6                   | Sem resposta; o desenho entrou com a leitura provisória de cada uma                    | Documento 38, seção 2.2  |
| **Q135-6 (arquivo 09 da consulta à Receita)**                 | Nada no dicionário; o envio é seu                                                      | Documento 98, seção 3.9  |

# 5. Pontos de atenção

- **Onda 3 pesa agora 477 entidades** (eram 473), 5.635 campos e 1.369 chaves estrangeiras. A onda 4 ganhou 2 campos e 2 chaves (`ID_Atividade_Presuncao` e a natureza do royalty). As chaves estrangeiras opcionais que esperam a onda de destino continuam em 66.
- **Sem base, sem imposto.** Enquanto a `Base_Calculo` do IBS e da CBS estiver `a_definir`, nenhum imposto de adiantamento é calculado: a linha nasce `pendente_decisao` e o mês não confirma. O recebimento do dinheiro nunca é bloqueado.
- **Sem local, o ERP sugere.** Sem local ou item, o recebimento é registrado e o ERP sugere o endereço do cliente; o usuário confirma.
- **TEF da SAF.** Para a empresa sujeita ao TEF, o IBS e a CBS do adiantamento entram na apuração do TEF, e este desenho só fornece o item e o local (leitura minha; Q153-C6).
- **Devolução.** O estorno do imposto na devolução (na competência do estorno) está descrito no documento 153, mas o título automático da devolução só entra se você confirmar a Q153-6.
- **Documentos 152 e 153.** Seguem só em Word (o Projeto está cheio); o documento 154 também. O que entrou no dicionário está nos documentos 01, 05, 08 e 10.
- **Numeração.** O número 150 continua reservado ao desenho do B5.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 4 entidades (45 campos) e 4 campos novos em 4 entidades existentes; o tipo ou o texto de 6 campos em 6 entidades mudou (dois valores de enumeração e quatro descrições); **nenhum campo foi removido** e nenhuma entidade mudou de módulo. Conferi as contagens por entidade (13, 13, 11 e 8 campos) contra as tabelas dos documentos 127 e 153 e a soma de 45.
- **Auditoria:** fechou com **0 achados em aberto** já na primeira passada.
- **DDL:** gerado nos dois dialetos (1.191 tabelas, 3.057 chaves estrangeiras, 3.133 índices e 8.883 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro, e as contagens do banco batem com as do gerador.
- **T-SQL:** 16.265 comandos lidos por analisador de sintaxe (sqlglot), sem erro; o aumento de 77 comandos é exatamente 5 tabelas, 13 chaves estrangeiras, 14 índices e 45 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos.
- **Limites:** nada foi validado pelo contador. As leituras de norma do adiantamento (art. 10, § 4º, da LC 214, base do recebimento, abatimento, mês do abatimento, distrato) são minhas e estão nas perguntas Q153-C1 a Q153-C6 do documento 38. A vigência de partida da carga (01/01/2027 em IBS e CBS, 01/01/2026 nos federais) também é leitura minha.
