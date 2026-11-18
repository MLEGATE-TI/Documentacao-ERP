# Consolidação da Revisão 53 — Documento 242

*Você escreveu "consolidar". Li como no D-N603: **as recomendações do documento 241 valem como aprovadas** (Q241-2 a Q241-8). A Q241-1 é pedido de material (nada a aplicar); a Q239-4 ("Não agora") e a Q232-9 seguem abertas. **Se não era isso que você queria aprovar, me diga que eu desfaço** (a revisão 52 está guardada). Nada além do documento 241 entrou.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 52** | **Revisão 53** | **Diferença** |
|---|---|---|---|
| Entidades | 1.242 | **1.242** | 0 (nenhuma entidade nova) |
| Campos | 14.439 | **14.448** | +9, todos opcionais |
| Valores novos de enumeração (em campos) | — | **4** | `ccg_gtin`, `por_nsu_unico`, `por_chave`, `monofasia_diferenca_biocombustivel` |
| Campos de referência (FK) | 3.703 | 3.703 | 0 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 |
| Tabelas físicas (DDL) | 1.508 | 1.508 | 0 |
| Chaves estrangeiras (DDL) | 3.969 | 3.969 | 0 |
| Índices (DDL) | 4.060 | 4.060 | 0 |
| Comentários (DDL) | 12.180 | **12.189** | +9 |
| Comandos do T-SQL | 21.718 | **21.727** | +9 |
| Chaves opcionais que esperam a onda de destino | 87 | 87 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Revisão dos módulos | Fase 0 98, Contabilidade & Fiscal 70 | Fase 0 **99**, Contabilidade & Fiscal **71** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.508 tabelas, 12.189 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Id** | **Decisão (recomendação do documento 241)** | **Onde ficou no dicionário** |
|---|---|---|
| Q241-2 | Consulta de GTIN no CCG (`consGTIN`): o GTIN vai em `Chave_Consultada` e o retorno (`tpGTIN`, `xProd`, `NCM`, `CEST`) em `Mov_Consulta_Cadastro_Externo_Campo` | Valor `ccg_gtin` em `Mov_Consulta_Cadastro_Externo.Fonte` (Fase 0); **0 campos** |
| Q241-3 | Eventos Suframa 990900 e 990910: `PINe`, `locVistoria` e `postoVistoria`; `dVistoria` em `Data_Hora_Fato` e `xHistorico` em `Justificativa` | **+3 campos** em `Mov_Dfe_Evento`: `Numero_Pin_E` (código até 9), `Local_Fato` e `Posto_Fato` (texto) |
| Q241-4 | Resposta do Fisco à prorrogação (411500 a 411503): `statPrazo`, código da justificativa por item; `statCancPedido` em `Indicador_Aceite` e `justStatus` do cancelamento em `Codigo_Motivo` | **+2 campos**: `Mov_Dfe_Evento.Prazo_Cumprido` (booleano) e `Mov_Dfe_Evento_Item.Codigo_Justificativa_Status` (código até 1); `Justificativa_Status` passa a guardar só o `justStaOutra` |
| Q241-5 | (a) data e hora do hash dos eventos 110130 e 110192; (b) distribuição de DF-e por NSU único e por chave; `cUFAutor` sai da UF da filial | **+2 campos**: `Mov_Dfe_Evento.Data_Hora_Hash` e `Mov_Dfe_Distribuicao.Chave_Consultada` (código 44); `Modo_Consulta` ganha `por_nsu_unico` e `por_chave` |
| Q241-6 | Diferença do biocombustível (`gpBioDiferenca`) | Valor `monofasia_diferenca_biocombustivel` em `Tipo_Complemento` (Contabilidade & Fiscal): `Quantidade` = `qBCBioComb`, `Valor` = `vIBSDiferenca` ou `vCBSDiferenca`; **0 campos** |
| Q241-7 | IBS monofásico ad valorem com UF e município (só guardar o que chega) | **+2 campos** em `Mov_Apuracao_Tributo_Item_Complemento`: `Percentual_Municipio` e `Valor_Municipio`; `Percentual` e `Valor` ficam para a UF; a CBS usa só os atuais |
| Q241-8 | Três acertos de texto | `Numero_Pagamento`: 1 a 990 no esquema (o grupo repete de 1 a 99 vezes); `Cnpj_Recebedor` e `Cnpj_Base_Psp`: opcionais na tabela, obrigatórios no Motor; `Valor` do complemento cita `vTribRegCBS`; **0 campos** |

# 3. Leituras minhas e limites do que apliquei

- **Duas leituras minhas, a confirmar:** `Prazo_Cumprido` é verdadeiro quando o `statPrazo` do esquema é 1 (pedido dentro do prazo), e o `statCancPedido` "deferido" vira verdadeiro em `Indicador_Aceite`. Se o MOC ou a NT disser o contrário, é troca de texto, sem mudar o campo.
- **Códigos do `justStatus` (1 a 8):** o campo `Codigo_Justificativa_Status` existe, mas **não li a tabela de significado dos códigos** (a NT da prorrogação); por isso `Cad_Dfe_Evento_Motivo` não ganhou linhas para ela.
- **Biocombustível:** o tipo de complemento guarda a diferença que vem no XML; a regra de quando o grupo é exigido continua na marca `Indicador_Grupo_Biocombustivel_Diferenca` do classificador e o texto da NT sobre o cálculo não foi lido.
- **IBS monofásico ad valorem:** só guarda o que chega (nota recebida e conferência). `Cad_Aliquota_Combustivel` continua só com a alíquota por unidade; não há regra de cálculo ad valorem até haver fonte legal.
- **PIN-e:** `Numero_Pin_E` fica separado do `Pin_Suframa` do CT-e porque o PIN-e é do evento (leitura minha do documento 241).
- **Nenhuma carga nova.** A Carga52 segue como está; não há linhas de carga para os 4 valores novos (são enumerações de campo, não de `Cad_Classe_Sistema`).
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 4. Eventos do Fisco: o que ficou registrado

Você disse que os eventos do Fisco "não podemos usar" e, entre "só não emitir" e "excluir do catálogo", escolheu **só não emitir**. Está no documento 14 (D-N622): o ERP **nunca emite** evento de autor Fisco ou Ambiente Nacional; só recebe e registra, como `Papel_Autor` já descreve. O catálogo de tipos de evento segue o dos esquemas (44, sem código novo).

A **planilha de 50 códigos** que você enviou ("qualquer outro que não está nesta lista não existe") **não foi aplicada**, porque conflita com os esquemas: dos 44 códigos com esquema ela traz só 14 (faltam, por exemplo, 211xxx, 411500 a 411503, 990900 e 990910) e 36 dos 50 códigos dela não têm esquema entre os recebidos. Os 420110 a 420170 também não estão nela; coincidem com códigos de município de Santa Catarina no IBGE, mas o esquema do cancelamento de evento os lista no campo do evento autorizado. A pergunta ficou na **Q232-9** (abaixo).

# 5. O que fica aberto

- **Você:** Q241-1 (pacote de esquemas da NFC-e), Q232-9 (reescrita), Q239-4, Q234-3, a "Lista Vigente" da Res. 553 (art. 2º) e os demais itens do documento 38.
- **Contador:** nada novo (C1 a C364).

| **Id** | **Pergunta** | **Recomendação** |
|---|---|---|
| Q232-9 | Os esquemas ou a planilha de 50 códigos: qual prevalece para o catálogo de eventos? E a NT ou o esquema dos 420110 a 420170? | **Os esquemas prevalecem** (a SEFAZ valida por eles); os sete códigos ficam fora da lista de emissão até haver a NT. Ou envie a fonte da planilha |
| Q241-1 | Enviar o pacote de esquemas ativo da NFC-e (modelo 65)? | **Sim**, quando puder |

Próximos números: D-N623, contador C365, documento 243, Q241-9, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.52.
