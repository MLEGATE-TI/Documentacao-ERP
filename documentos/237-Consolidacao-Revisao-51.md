# Consolidação da Revisão 51 — Documento 237

*Você escreveu "consolidar". Entrou **tudo o que você aprovou e ainda não estava aplicado**: as Q235-1 a Q235-7 (documento 235, D-N608 e D-N612) e as Q236-1, Q236-3 e Q236-4 (documento 236, D-N611), com a Carga51 no lugar da Carga236. Nada além disso, **com uma correção minha** (seção 3, Q237-1): a chave única de `Cad_Lista_Legal_Item` só tinha tipo e anexo e o banco recusaria a segunda linha de um mesmo anexo.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 50** | **Revisão 51** | **Diferença** |
|---|---|---|---|
| Entidades | 1.242 | **1.242** | 0 (nenhuma entidade nova) |
| Campos | 14.434 | **14.438** | +4 |
| Campos de referência (FK) | 3.701 | **3.703** | +2 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 (2 valores novos no domínio aberto `tipo_lista_legal`) |
| Tabelas físicas (DDL) | 1.508 | **1.508** | 0 |
| Chaves estrangeiras (DDL) | 3.967 | **3.969** | +2 |
| Índices (DDL) | 4.058 | **4.060** | +2 |
| Comentários (DDL) | 12.175 | **12.179** | +4 |
| Comandos do T-SQL | 21.709 | **21.717** | +8 |
| Chaves opcionais que esperam a onda de destino | 86 | **87** | +1 (`Cad_Produto_Servico_Dados_Produto.ID_Lista_Legal_Item_Ex`, onda 0, aponta para a onda 3) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Revisão dos módulos | Fase 0 96, Contabilidade & Fiscal 68 | Fase 0 **97**, Contabilidade & Fiscal **69** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.508 tabelas). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Id** | **Decisão aprovada** | **Onde ficou no dicionário** |
|---|---|---|
| Q235-1 | Um só tipo, `autopecas_nao_produzidas`; o regime (redução a 2% ou isenção com a contrapartida de 2%) vem da habilitação | Valor novo no domínio aberto `tipo_lista_legal`; texto em `Cad_Lista_Legal_Item.ID_Tipo_Lista` e em `Mov_Autopecas_Importacao_Item.ID_Habilitacao` |
| Q235-2 | `Numero_Ex` e `Descricao_Item` | **2 campos novos** em `Cad_Lista_Legal_Item` (`Numero_Ex`, código até 10, opcional, na identidade; `Descricao_Item`, texto, opcional) |
| Q235-3 e Q236-1 | Fim = "Fim da Vigência" da lista; sem prorrogação automática; sem benefício a partir de 01/01/2027 para o Ex não prorrogado; **início = data de entrada em vigor** quando a resolução fixa uma (545: 01/01/2024; 974: 14/10/2026; 982: 23/11/2026), senão a data do DOU | Texto de `Vigencia_Inicio`, `Vigencia_Fim` e `Fundamento_Legal`; a carga já traz as datas (839 + 190 + 739 linhas pela entrada em vigor) |
| Q235-4 | Só a lista vigente (a de outubro de 2026 com a Res. 982); o histórico de 2020 a 2024 fica de consulta | Texto de `Vigencia_Fim`; Carga51 |
| Q235-5 e Q235-6 | Pleitos de Ex fora do ERP; ENOC, InTec, pegada de carbono e desmontagem esperam a portaria final do Mover | Nota na entidade; **sem estrutura** |
| Q235-7 | O elo do produto com o Ex (D-N608: produto único em `Cad_Produto_Servico`, só atributos) | **2 campos de referência novos:** `Cad_Produto_Servico_Dados_Produto.ID_Lista_Legal_Item_Ex` e `Mov_Autopecas_Importacao_Item.ID_Lista_Legal_Item`, os dois opcionais |
| Q236-3 | Carregar os 7.128 NCM da Res. Gecex 553/2024 com o valor `sem_similar_nacional_senado13`; o Motor só sugere a origem 6 ou 7 | Valor novo no domínio; texto em `ID_Tipo_Lista`; **carga provisória** (seção 5) |
| Q236-4 | ACE 14 (Res. 311/2022, 546/2023 e regras de origem do Decreto 12.515/2025), tabelas do imposto de importação e antidumping: sem desenho por enquanto | Nota na entidade; **sem estrutura** |

O campo `Descricao_Item` guarda o texto da **lista legal**, não um produto da Mlegate: o produto continua um só, em `Cad_Produto_Servico`, produzido ou comprado. Só os dois campos de referência da Q235-7 ligam o produto e a importação ao Ex.

# 3. Correção minha: a chave única de `Cad_Lista_Legal_Item` (Q237-1)

**O que achei.** O DDL gerado desde a revisão 19 tinha `UNIQUE (tipo da lista, anexo)` na identidade de `Cad_Lista_Legal_Item`, porque só esses dois campos estavam marcados como identidade. O texto da entidade descreve outra chave de negócio: **tipo da lista, anexo, NCM (ou NBS ou registro na Anvisa) e restrição**. Com a chave do banco como estava, a **segunda** linha do mesmo anexo seria recusada, e a carga de 11.456 linhas do Ex (todas no Anexo I ou II da mesma lista) não carregaria, nem a do Mover (80 linhas no mesmo anexo).

**O que mudei.** Passaram a ser identidade o NCM, a NBS, o registro na Anvisa e o `Numero_Ex` (os três primeiros opcionais, como o `ID_Estado` de `Cad_Participante_Inscricao`). A restrição técnica **não** entrou (é texto longo, e o gerador a limitaria a 200 caracteres numa chave): o Motor confere a duplicidade por ela na carga.

**Efeito nos dois bancos.** No **PostgreSQL**, coluna nula nunca colide: a chave só barra linhas iguais em todos os campos preenchidos. No **SQL Server** (o banco inicial, decisão sua registrada no documento 31), nulo vale como valor igual e a chave barra a repetição de (tipo, anexo, NCM) mesmo com a NBS, a Anvisa e o Ex vazios. Por isso o ajuste abaixo.

**Ajuste da carga antiga do Mover.** A carga da revisão 40 (80 linhas, `mover_requisitos_anexo_i`) guardava o número do Ex em `Restricao_Tecnica` ("Ex 01"). Com a chave nova, 4 pares de linhas do mesmo NCM colidiriam no SQL Server. A Carga51 traz **46 ajustes (23 linhas)**: o número do Ex vai para `Numero_Ex` e a restrição fica vazia; as 19 linhas "exceto Ex ..." ficam como estão. Conferi que as 80 linhas ficam sem chave repetida e que a carga da Lei 10.485 (66 linhas) e a de pneus (2) já não repetiam. **Não conferi** as listas do Decreto 12.955 (Repetro, GNL, Reporto, art. 196 e 197), do Imposto Seletivo, do IPI, da ZFM e dos medicamentos do art. 146: não achei carga delas nas pastas que usei; a conferência contra a chave nova fica com a equipe antes da primeira carga.

**Se você preferir outra chave** (por exemplo só NCM e Ex, ou sem a NBS), diga e eu refaço; sem uma chave que inclua o NCM, a carga não carrega.

# 4. A carga (`Carga51-20261118`)

A Carga51 **substitui a Carga236**. Regras e códigos de retorno de NF-e: nada novo, a Carga50 continua valendo. CSV com BOM, separador ";", datas ISO, chaves de negócio. Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `01-lista/Cad_Lista_Legal_Item_autopecas_nao_produzidas_11456.csv` | 11456 | Anexo I 10.260 e Anexo II 1.196; lista do MDIC de outubro de 2026 (10.717) + 739 inclusões da Res. 982; 878 fins alterados para 30/06/2027; início pela entrada em vigor (Q236-1); chave (tipo, anexo, NCM, Ex) sem repetição |
| `01-lista/Mudancas_Res982_2026.csv` | 1617 | só conferência (não carregar) |
| `02-sem-similar/..._senado13_Res553_7128.csv` | 7128 | NCM do Anexo Único da Res. 553/2024; **provisória** (seção 5) |
| `02-sem-similar/NCM_do_Anexo_553_fora_da_tabela_vigente_28.csv` | 28 | NCM encerrados depois de 2024; fora da carga |
| `04-dominios/Cad_Classe_Sistema_tipo_lista_legal_2.csv` | 2 | valores `autopecas_nao_produzidas` e `sem_similar_nacional_senado13` |
| `05-ajustes/Ajustes_em_linhas_ja_carregadas_46.csv` | 46 | o Ex do Mover passa de `Restricao_Tecnica` para `Numero_Ex` (seção 3) |

Ordem de carga: domínio, depois as listas. O `Motivo_Vigencia` das linhas foi reescrito para dizer o que vale (entrada em vigor, ou data do DOU com texto da resolução não lido).

# 5. Limites e leituras minhas

1. **A lista da Res. 553 é a original de 14/02/2024** (7.156 NCM, 7.128 vigentes). Seis alterações (575, 645, 708, 785, 813 e 822) não foram lidas; a lista pode estar desatualizada. A carga fica provisória até chegar o Anexo Único atual e a lista consolidada do art. 2º (pedido na seção 0 do documento 38).
2. **Início da vigência** das resoluções antigas (anteriores à 545, texto não lido): data do DOU, provisória; a resolução pode ter fixado outra data de entrada em vigor.
3. **Vencimento.** 3.071 Ex vencem em 31/12/2026 e dois itens não têm fim. Não li resolução que prorrogue os 3.071: sem ela, o Motor trata a linha como sem benefício a partir de 01/01/2027 (Q235-3).
4. **O vínculo produto–Ex** (`ID_Lista_Legal_Item_Ex`) aponta para a identidade do item e vale em toda versão; que o NCM do produto seja o do item da lista é **conferência do Motor**, não do banco.
5. **`Numero_Ex` é texto:** "2" nas autopeças e "01" no Mover, como cada lista os publica; a comparação é só dentro do mesmo tipo.
6. **Chaves em onda posterior.** `Cad_Produto_Servico_Dados_Produto` (Fase 0, onda 0) aponta para `Cad_Lista_Legal_Item` (onda 3): a chave estrangeira nasce na onda 3, como as outras 86 (o campo é opcional).
7. **T-SQL:** só lido (contagem de comandos), não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** **Q237-1** (confirmar a correção da chave única, seção 3; recomendo **Sim**, seção 1.50 do documento 38); o Anexo Único atual da Res. 553 (ou as Res. 575, 645, 785 e 822) e a lista consolidada do art. 2º; a Q234-3 (qual estabelecimento emite sem IE e desde quando) e os demais itens do documento 38.
- **Contador:** nada novo (C286 e C364 seguem como estão; total C1 a C364).
- **Equipe:** conferir as cargas das outras listas legais contra a chave nova antes da primeira carga (seção 3).

| **Id** | **Pergunta** | **Recomendação** |
|---|---|---|
| Q237-1 | A chave única de `Cad_Lista_Legal_Item` passa a ser tipo da lista, anexo, NCM, NBS, registro na Anvisa e número do Ex (o número do Ex das 23 linhas do Mover sai de `Restricao_Tecnica`, ajuste da Carga51)? | **Sim** |

