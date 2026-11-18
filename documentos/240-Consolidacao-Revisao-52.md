# Consolidação da Revisão 52 — Documento 240

*Você escreveu "consolidar". Entrou **tudo o que você aprovou e ainda não estava aplicado**: a Q238-1 (D-N618) e as Q239-1, Q239-2 e Q239-3 (D-N619), do documento 239, com a Carga52 no lugar das Cargas 238 e 239 (propostas) e da Carga51/02. Nada além disso. **Uma correção minha** (seção 3): o aviso do documento 239 de que o banco "recusaria a segunda linha" de depreciação não vale para o DDL.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 51** | **Revisão 52** | **Diferença** |
|---|---|---|---|
| Entidades | 1.242 | **1.242** | 0 (nenhuma entidade nova) |
| Campos | 14.438 | **14.439** | +1 (`Cad_Taxa_Depreciacao_Cbs.Numero_Item_Anexo`) |
| Campos de referência (FK) | 3.703 | 3.703 | 0 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 |
| Tabelas físicas (DDL) | 1.508 | 1.508 | 0 |
| Chaves estrangeiras (DDL) | 3.969 | 3.969 | 0 |
| Índices (DDL) | 4.060 | 4.060 | 0 (o índice de `Cad_Taxa_Depreciacao_Cbs` continua) |
| Comentários (DDL) | 12.179 | **12.180** | +1 |
| Comandos do T-SQL | 21.717 | **21.718** | +1 |
| Chaves opcionais que esperam a onda de destino | 87 | 87 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Revisão dos módulos | Fase 0 97, Contabilidade & Fiscal 69 | Fase 0 **98**, Contabilidade & Fiscal **70** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.508 tabelas). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Id** | **Decisão aprovada** | **Onde ficou no dicionário** |
|---|---|---|
| Q238-1 | Uma linha por chave em `Cad_Lista_Legal_Item` (tipo, anexo, NCM, NBS, registro na Anvisa, `Numero_Ex`); vários itens do mesmo anexo na mesma chave vão todos no `Fundamento_Legal`, as descrições em `Descricao_Item` e as restrições em `Restricao_Tecnica` | Nota da entidade `Cad_Lista_Legal_Item`; **sem campo novo**. A Carga52/00 traz as linhas de LC 214 e IS já assim (708 → 606) |
| Q239-1 | A lista da Res. Gecex 822 entra com `Vigencia_Inicio` 01/02/2026 e **só a lista vigente** (Q235-4) | Nota da entidade; Carga52/03 (7.188 linhas) |
| Q239-2 | `Numero_Item_Anexo` na chave de negócio de `Cad_Taxa_Depreciacao_Cbs`; `ID_Classificacao_Mercadoria` opcional | **1 campo novo** (número, obrigatório, na identidade); `ID_Classificacao_Mercadoria` agora "opcional --- identidade"; textos de `Descricao_Bem`, `Percentual_Anual`, `Fundamento_Legal` e `Vigencia_Inicio` |
| Q239-3 | Os NCM que não existem na tabela de 16/11/2026 ficam fora da carga e são listados | Carga52/04-conferencia; sem estrutura |
| D-N618 | Lista da Res. 553 trocada pela versão da Res. 822; listas do Decreto 12.955 viram carga | Linha do domínio `tipo_lista_legal` (Fase 0) e nota de `Cad_Lista_Legal_Item` |

# 3. Correção minha e limites do que apliquei

**Unicidade em `Cad_Taxa_Depreciacao_Cbs`.** No documento 239 escrevi que, na chave antiga (NCM mais `Vigencia_Inicio`), "a segunda linha seria recusada". Isso vale para a **chave de negócio** descrita no texto da entidade. O **DDL**, porém, não tem restrição de unicidade nessa tabela: ela é uma janela de vigência sem identidade separada, e o gerador cria só a chave primária e um **índice** (NCM, vigência). A nova chave de negócio (número do item, NCM opcional, `Vigencia_Inicio`) fica, como a antiga, como **regra do Motor e da carga**; se você quiser que o banco a imponha, é outra decisão (a Q239-4, abaixo).

**As duas linhas sem NCM não entraram na carga.** "Instalações" e "edificações" (Anexo I do decreto) não trazem prazo nem taxa; o campo `ID_Classificacao_Mercadoria` ficou opcional para elas poderem existir, mas a Carga52/02 só traz as **208** linhas com NCM e taxa (arquivo `Anexo_I_linhas_nao_carregadas_40.csv` lista as 40 que ficam de fora: 38 cabeçalhos de grupo e as 2 sem NCM).

**Leituras minhas na carga de depreciação.** O item 214 (prazo de 20 anos) não traz a taxa impressa: calculei 100 ÷ prazo = 5%; o item 156 traz "33,3% em 3 anos" e foi carregado como publicado (33,3). Início 30/04/2026, provisório.

# 4. A carga (`Carga52-20261118`)

A Carga52 **substitui as Cargas 238 e 239 (propostas) e, na lista da Res. 553, a Carga51/02**. As regras e os códigos de retorno de NF-e seguem os da Carga50. CSV com BOM, ";" (a pasta 00 usa "," como a Carga26), datas ISO, chaves de negócio. Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `00-lc214-is/Cad_Lista_Legal_Item_lc214_e_is_sem_repeticao_606.csv` | 606 | LC 214 e Imposto Seletivo da Carga26 (708), uma linha por chave; **substitui** as linhas de LC 214 e IS da Carga26 |
| `01-decreto-12955/Cad_Lista_Legal_Item_decreto_12955_369.csv` | 369 | Repetro 109, GNL 107, Reporto 55, art. 196 17, art. 197 81; início 30/04/2026; 4 chaves do Reporto com NCM fora da tabela ficam fora |
| `02-depreciacao/Cad_Taxa_Depreciacao_Cbs_208.csv` | 208 | Anexo I do decreto (art. 48, § 1º), com `Numero_Item_Anexo`; 10 NCM fora da tabela ficam fora; a coluna `NCM_na_tabela` é só conferência |
| `03-sem-similar-553-res822/..._senado13_Res822_7188.csv` | 7.188 | Anexo Único da Res. 553 na redação da Res. 822 (7.187 NCM) mais o 7502.10.10 (art. 3º); início 01/02/2026; **provisória** |
| `04-conferencia/` (6 arquivos) | — | só conferência, não carregar |

Total carregável: **8.371 linhas** (606 + 369 + 208 + 7.188). Ordem: o domínio `tipo_lista_legal` já tem todos os valores; depois as pastas 00, 01 e 03 (`Cad_Lista_Legal_Item`) e a 02 (`Cad_Taxa_Depreciacao_Cbs`, que precisa do campo novo).

# 5. Limites e o que fica fora

1. **A lista da Res. 553 continua provisória.** Falta a lista consolidada do art. 2º ("Lista Vigente" do MDIC, xlsx de 16/10/2026): sem ela o dicionário diz só se o NCM pode ser "sem similar", não se o bem concreto cumpre o art. 1º (incisos I, II e III são **alternativas**).
2. **ACE-14:** a lista de exceções (Anexo X da Res. 272) não foi obtida; só interessa ao art. 1º, I, a.
3. **Fora da carga:** IPI, ZFM/ALC (lista do contador, Q158-C9) e medicamentos do art. 146; Cargas 35, 40, 51/01 e 51/05 (autopeças, Mover) seguem como estão.
4. **Equipe:** os 14 NCM do decreto que não existem na tabela de 16/11/2026 e o rótulo dos arts. 196 e 197 (o decreto cita as "Tabelas I a III do Anexo IV"; o Diário Oficial traz os Anexos IV e V). A conferência das listas de IPI, ZFM e do art. 146 contra a chave nova segue com a equipe.
5. **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** a "Lista Vigente" da Res. 553 (art. 2º) e a lista do Anexo X da Res. 272 (só se quiser o inciso I, a); **Q239-4** (abaixo); a Q234-3 e os demais itens do documento 38.
- **Contador:** nada novo (C1 a C364).

| **Id** | **Pergunta** | **Recomendação** |
|---|---|---|
| Q239-4 | Pedir ao gerador de DDL uma restrição de unicidade na chave de negócio de `Cad_Taxa_Depreciacao_Cbs` (número do item, NCM e `Vigencia_Inicio`), hoje só garantida pelo Motor e pela carga? Com NCM opcional, no SQL Server o nulo valeria como valor igual (efeito já visto na revisão 51) | **Não agora:** a tabela é pequena e a carga é conferida; decidir quando o Motor de depreciação for desenhado |

