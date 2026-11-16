# Carga da NCM e da NBS e leitura da IT 2025.002 v1.70 — Documento 220

*Você enviou o link do JSON da NCM (o Portal Único não abriu pelo meu ambiente; você anexou o arquivo), o PDF do Anexo I da NBS 2.0 e o PDF do IT 2025.002 v1.70. Gerei as cargas completas da NCM e da NBS, conferi contra as cargas anteriores e li o IT. **Nada foi aplicado ao dicionário**: as cargas são arquivos, e o que muda na estrutura (hierarquia da NBS) depende da sua resposta na Q220-1.*

> **Situação em 16/11/2026:** as propostas deste documento foram **aprovadas** (D-N588; Q220-1, Q220-5 e Q221-1 a Q221-13) e **consolidadas na revisão 45** (documentos 222 e 223, D-N589). As cargas foram refeitas na pasta `Carga45-20261116`, que substitui os arquivos de NBS, cClassTrib, CFOP e unidades das cargas citadas aqui. O texto abaixo fica como histórico.

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | NCM | NBS |
|---|---|---|
| Fonte | JSON do Portal Único (CLASSIF), Resolução Gecex 926/2026, baixado em 16/11/2026 | PDF do Anexo I da NBS 2.0, **minuta de dezembro de 2018** com alterações de 6.12.18 |
| Linhas do arquivo | 15.157 | 1.211 nós (920 códigos de 9 dígitos, mais a hierarquia) |
| Linhas na carga | **15.428** (15.157 do Portal e 271 posições derivadas) | **920** códigos de 9 dígitos |
| Vigência | início de cada linha como no Portal (de 01/04/2022 a 01/10/2026); fim 31/12/9999 | início **01/01/2019 (leitura minha)**; fim 31/12/9999 |
| Situação do registro | `processada` | `com_pendencia` |
| Hash SHA-256 | 3fb7b068c529… | 68a5103b459d… |

A carga está na pasta `CargaNCM-NBS-20261116` (zip do mesmo nome), com o LEIA-ME e a ordem: nomenclatura, classificação da NCM, NBS, registro das cargas. A NCM tem que entrar **antes** das cargas que citam códigos NCM (Carga40, Carga42 e Carga43). Duas colunas são só de conferência e o carregador as descarta: `Origem_Linha` (NCM) e `Codigo_NBS_Formatado` (NBS).

# 2. NCM

**Níveis carregados (15.428 linhas):** 96 capítulos, 1.228 posições, 1.024 subposições de 5 dígitos, 1.661 de 6, 903 itens de 7 e 10.516 subitens de 8 dígitos. Só o subitem de 8 dígitos é analítico.

**O que o arquivo do Portal faz e eu tive de tratar:**

(1) **271 posições não têm linha própria.** Quando a posição de 4 dígitos tem uma única subposição (por exemplo 0205, que só tem 0205.00.00), o Portal publica só o filho. Sem a posição, o pai do filho viraria o capítulo e a árvore perderia um nível. Criei as 271 posições (`Origem_Linha` = `derivada`), com a descrição do filho único; cada uma foi conferida (tem um e só um filho direto). A lista está em `NCM_posicoes_derivadas_271.csv`. Duas delas, 2203 e 2206, são citadas pela Carga43 do Imposto Seletivo.
(2) **Tags nas descrições** (`<sup>`, `<sub>`, `<i>`) foram convertidas para texto simples.
(3) **Alíquota de IPI e unidade estatística** ficam vazias: o JSON do Portal não traz. Entram pela Carga42 (TIPI) e por outra fonte.
(4) **Sem histórico e sem sucessões**: o arquivo é só a tabela vigente. O IT 2024.001 v2.40 (Q162-E1) tem as sucessões "1 para vários" da v2.30; isso não se deriva deste JSON.

**Conferências:**

- Árvore: códigos únicos, pai é prefixo existente, só a folha de 8 dígitos é analítica (verificado por regra, linha a linha).
- Os **120 códigos NCM citados nas cargas anteriores** (Carga40, Carga42, Carga43 e outras) existem todos; nenhum falta.
- **25 códigos novos em 2026:** os da Resolução Gecex 812/2025 (a partir de 01/02/2026) e da 926/2026 (a partir de 01/10/2026), em `NCM_novos_em_2026.csv`. O **85181020** (outros microfones, sem suporte) começa em 01/10/2026, o que **confirma a metade da Q162-E1** sobre a data; as sucessões continuam sem fonte.

# 3. NBS

**O que o PDF dá:** 5 seções, 26 capítulos (o 16 é "Reservado para possível uso futuro", sem códigos), 101 posições com linha própria, 130 subposições de 6 dígitos, 50 de 7, 10 itens de 8 dígitos e **920 códigos de 9 dígitos**. 45 posições de 4 dígitos não têm linha própria (um só código de 9 dígitos); criei-as só na conferência, como na NCM.

**Três achados:**

(1) **`Cad_NBS` não guarda a hierarquia.** Ela tem só o código de 9 dígitos, a descrição e a vigência. `Cad_Lista_Legal_Item` liga a NBS por `ID_NBS`, enquanto a NCM da mesma lista aceita qualquer nível. Se um anexo citar a NBS por posição ou subposição (não conferi isso nos anexos que li), não há onde ligar; e o motor também não tem como subir de um código de 9 dígitos à sua posição ou ao seu capítulo. A NCM resolve isso com nível, pai e analítico em `Cad_Classificacao_Mercadoria`. **Proposta na Q220-1.** Enquanto isso, a hierarquia (1.287 linhas, com as seções) está em `NBS_hierarquia_referencia_nao_carregada.csv` e não entra na carga.
(2) **O PDF é uma minuta de dezembro de 2018**, sem número de portaria e sem data de início. Não sei se a NBS vigente em 2026 é ela, ou se teve revisões (o IBS e a CBS usam a NBS). Por isso a carga está `com_pendencia` e a vigência de 01/01/2019 é provisória. **Q220-3.**
(3) **Qualidade da leitura:** a primeira leitura perdia 10 itens de 8 dígitos (por exemplo 1.0401.11.1 e 1.0901.51.1); corrigi e conferi que todo código de 9 dígitos tem pai existente e que o total (920) não mudou. Amostras e as descrições mais longas foram conferidas à mão; as descrições quebradas em duas linhas e as quebras de página foram tratadas.

# 4. IT 2025.002 v1.70 (tabelas cClassTrib, CST e cCredPres)

O PDF tem 13 páginas, de setembro de 2026: **descreve as colunas das três tabelas e lista o que mudou de versão em versão** (1.10 a 1.70). **Não traz as linhas das tabelas**: elas ficam na planilha e nos serviços do Portal (SVRS e consumo.tributos.gov.br). A v1.70 também **não é a vigente**: o Ato Técnico Conjunto 10/2026 (documento 161) trouxe a v1.71.

**O que o dicionário já cobre** (conferi campo a campo): os indicadores de `cClassTrib` e de CST (`Cad_Cclasstrib`, `Cad_Cst`), as marcas por modelo (`Cad_Cclasstrib_Modelo`), o anexo técnico ZXXXY (`Codigo_Anexo_Tecnico`), `ind_gpBioDiferenca`, `tpRBSN`, `tpDoacao`, `ind_RedutorBC` e as colunas novas de `cCredPres` (`indDecPag`, `indNFe`, `indNFCe`, `indCTe`, `indNFSe`, `pRedTransicaoIBS`) em `Cad_Credito_Presumido_Ibs_Cbs`. As alíquotas padrão da seção 05 (2026: IBS estadual 0,1, municipal 0, CBS 0,9; 2027 e 2028: 0,05 e 0,05, CBS a aguardar) batem com `Cad_Aliquota`.

**O que não está no dicionário:**

(1) **`ind_DIR`** (criado na v1.60; na v1.70 liga e desliga o 410037 e o 200012 e o 200033). O IT o lista entre os indicadores de modelo, ao lado de DeRE e DUIMP, mas **não define a sigla**; leio como a declaração de importação de remessa (combina com os novos 400004, remessas internacionais, e 410037, importação sem incidência). É uma marca por modelo, no padrão da `Cad_Cclasstrib_Modelo`, que **só ganha linha quando o modelo entrar em `Cad_Modelo_Documento_Fiscal`** (hoje o cadastro não tem DIR). O mesmo vale para `ind_DUIMP`, listado como indicador de modelo; o dicionário tem `Indicador_Duimp` em `Cad_Cclasstrib` com outro sentido ("exige o número da DUIMP"). **Q220-2.**
(2) **Os dados.** Nenhuma carga anterior tem as linhas de cClassTrib, CST ou cCredPres (não achei nenhum dos 16 códigos novos das v1.50 a v1.70, como 000005, 000006, 200054 a 200056, 400003, 400004 e 550024 a 550029, em carga alguma). Para carregar preciso da **planilha da v1.71**. **Q220-4.**

# 5. O que continua aberto

| Id | Assunto | Com quem |
|---|---|---|
| Q220-1 | Estender `Cad_NBS` com nível e pai (hierarquia) | Você |
| Q220-2 | `ind_DIR` e `ind_DUIMP` como marcas de modelo | Você |
| Q220-3 | Versão vigente da NBS e data de início | Você |
| Q220-4 | Planilha da tabela cClassTrib v1.71 | Você |
| Q220-5 | Aceitar as posições derivadas (271 da NCM, 45 da NBS) | Você |

# 6. Limites

- Não tive o Portal Único por conexão direta (o proxy recusou e não contornei); trabalhei só com o arquivo que você anexou.
- Não validei a NBS contra uma versão oficial vigente; a carga é de partida.
- Não executei as cargas contra um banco: conferi a estrutura e as regras por script (árvore, unicidade, referências cruzadas com as cargas anteriores).
- Nada foi aplicado ao dicionário (revisão 44, 1.229 entidades e 14.261 campos, sem mudança).
