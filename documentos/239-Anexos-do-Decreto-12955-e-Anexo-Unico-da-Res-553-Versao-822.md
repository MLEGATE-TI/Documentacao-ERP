# Anexos do Decreto 12.955/2026 e Anexo Único da Res. Gecex 553/2024 na versão da Res. 822 — Documento 239

*Você respondeu "Q238-1 (recomendo Sim) - Seguir com a recomendação" e enviou o Decreto 12.955/2026 (Diário Oficial de 30/04/2026), as Res. Gecex 822, 785, 708, 813 e 645, as páginas do MDIC (Lessin e ACE-14), a apresentação sobre a ZFM, a página da PGFN e as NT 2026.007, 2026.008 e 2025.002. **Nada foi aplicado ao dicionário** (você ainda não escreveu "consolidar"): este documento registra a decisão, entrega a Carga239 e traz três perguntas novas.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Assunto** | **Resultado** |
|---|---|
| Q238-1 (uma linha por chave em `Cad_Lista_Legal_Item`) | **Aprovada** (D-N618). Aplicada na Carga239; a Carga26 (LC 214 e IS) passa de 708 para 606 linhas na hora da consolidação (Carga238, já entregue) |
| Anexo Único da Res. 553/2024 | Obtive a **versão atual**: a Res. Gecex 822/2025 (DOU de 02/12/2025, **em vigor em 01/02/2026**) tem 7.189 NCM. Em relação à lista original de 2024: **+60 e −27** NCM. A Carga239/03 tem **7.188 linhas** e substitui a Carga51/02 (7.128) |
| Listas do Decreto 12.955 (Repetro, GNL, Reporto, arts. 196 e 197) | Eram as listas que a equipe não tinha. **738 itens viraram 373 chaves e 369 linhas** de carga (Carga239/01) |
| Depreciação (Anexo I do decreto, art. 48, § 1º) | **208 linhas** (Carga239/02); a chave atual do dicionário não comporta o NCM 3926.90 (duas taxas) nem as linhas sem NCM: **Q239-2** |
| NCM que não existem mais na tabela de 16/11/2026 | 14 no decreto, 2 na lista da 822 e 28 na lista original de 2024 ficam fora: **Q239-3** |
| ACE-14, ZFM, NT, PGFN | Sem efeito no dicionário (seção 6) |

# 2. Decisão: Q238-1 aprovada (D-N618)

Fica a regra: **uma linha por chave** (tipo da lista, anexo, NCM, NBS, registro na Anvisa, `Numero_Ex`); quando vários itens do mesmo anexo têm a mesma chave, todos os itens vão no `Fundamento_Legal` ("itens 2, 29 e 30"), as descrições em `Descricao_Item` e as restrições em `Restricao_Tecnica`. A Carga239 já usa a regra: os 738 itens do decreto reduziram-se a 373 chaves (111 chaves repetidas, 476 itens reunidos; arquivo de conferência `Decreto_12955_chaves_repetidas_111.csv`). **Não há mudança de dicionário** por causa da Q238-1.

# 3. Res. Gecex 553/2024: o Anexo Único atual

**Cadeia de alterações do Anexo Único** (cada ato foi lido no Diário Oficial):

| Ato | Publicação | Vigor | NCM no Anexo | Entraram | Saíram |
|---|---|---|---|---|---|
| Res. Gecex 553/2024 (original) | 14/02/2024 | 14/02/2024 | 7.156 | — | — |
| Res. Gecex 645/2024 | 20/09/2024 | 01/10/2024 | 7.129 | 51 | 78 |
| Res. Gecex 785/2025 | 01/09/2025 | 01/10/2025 | 7.185 | 56 | 0 |
| **Res. Gecex 822/2025** | 02/12/2025 | **01/02/2026** | **7.189** | 5 | 1 |

A 575/2024 foi revogada pela 645; a 785 pela 822. As Res. **708/2025** (14/03/2025) e **813/2025** (30/10/2025, em vigor na publicação) **não mexem no Anexo**: só ampliam as condições do art. 1º (Anexo X da Res. 272, que traz a Lista de Exceções Temporárias do ACE-14, no inciso I, alínea a, e no III; Res. 322 e 323, Anexo I, 780 e 781, nas alíneas e a h do inciso I).

**Correções ao que eu tinha escrito antes** (documentos 236, 237 e 238 e Carga51):

1. A Res. 822 **não** valia desde 01/12/2025: foi publicada em 02/12/2025 e vale desde **01/02/2026**.
2. O art. 1º **não** exige "I a III" juntos: os incisos I, II e III são **alternativas**; o NCM precisa estar no Anexo Único **e** o bem precisa cumprir um deles (I: Imposto de Importação de até 2% por um dos atos listados; II: inexistência de similar nacional atestada e constante da relação do Portal Único; III: alíquota de até 2% pelos Anexos V, VI e X da Res. 272 em elevação gradual).
3. A lista de 2024 (Carga51/02) estava **desatualizada** em 87 NCM.

**Carga239/03** (`Cad_Lista_Legal_Item`, tipo `sem_similar_nacional_senado13`, anexo "Anexo Único"): 7.187 NCM da 822 que existem na tabela de 16/11/2026, mais o **7502.10.10** do art. 3º (enquanto durar a decisão judicial; ele não está no Anexo da 822). Início 01/02/2026 (Q239-1), sem fim, provisório. Dois NCM da 822 (8412.90.20 e 8504.50.00) não existem na tabela e ficam fora (Q239-3). A Carga51/02 sai da consolidação e é trocada por esta.

**O que continua faltando:** a **lista consolidada do art. 2º** (MDIC, "Lista Vigente" de 16/10/2026, em Excel), que traz os itens do inciso I com Ex e é a que o desembaraço usa. Minhas ferramentas não leem esse arquivo. Peço que você o baixe e envie (seção 0 do documento 38). **Sem ele, a lista do dicionário diz só se o NCM pode ser "sem similar"; não diz se o bem concreto cumpre o art. 1º** (o Motor sugere e o usuário confirma, como nas outras listas).

# 4. Decreto 12.955/2026: os anexos viraram carga

O Decreto foi publicado e entrou em vigor em 30/04/2026 (art. 619; algumas exceções em 2027). Li os Anexos I a V no Diário Oficial (páginas 214 a 251) e converti as tabelas:

| Anexo | Dispositivo | Tipo da lista | Itens | Linhas da carga |
|---|---|---|---|---|
| Anexo I | art. 48, § 1º (depreciação) | — (tabela própria, seção 5) | 258 linhas | 208 |
| Anexo II, Tabelas I, III e IV | art. 164 (Repetro) | `repetro` | 256 | 109 |
| Anexo II, Tabela II | art. 164 (GNL) | `gnl` | 325 | 107 |
| Anexo III | art. 186, § 5º (Reporto) | `reporto` | 59 | 55 |
| Anexo IV | art. 196 | `bem_capital_art196` | 17 | 17 |
| Anexo V, Tabelas I e II | art. 197 | `bem_capital_art197` | 81 | 81 |
| **Listas (sem depreciação)** | | | **738** | **369** |

Os cinco valores do domínio `tipo_lista_legal` já existem (D-N269). Os itens vão com a posição de 4 dígitos como o decreto publicou (o NCM "em qualquer nível" já é regra da D-N269). Início 30/04/2026 (Q236-1: entrada em vigor quando o texto fixa), provisório.

**Achado para a equipe:** os arts. 196 e 197 do decreto citam "Tabela I, II e III do Anexo IV"; o Diário Oficial traz os **Anexos IV e V** (o V com duas tabelas). Usei os rótulos do Diário Oficial. Quem ler o artigo deve conferir.

# 5. Depreciação (Anexo I): a chave não comporta duas linhas

O Anexo I do decreto tem **258 linhas**: 38 cabeçalhos de grupo (sem taxa), 2 linhas sem NCM ("instalações" e "edificações"), 10 com NCM que não existe mais na tabela e **208 carregáveis** (taxas 10% por 10 anos: 144; 20% por 5: 41; 25% por 4: 8; 5% por 20: 6; 50% por 2: 4; 4% por 25: 4; 33,3% por 3: 1; a do item 214 não traz a taxa e calculei 100 ÷ prazo).

**Problema (Q239-2):** `Cad_Taxa_Depreciacao_Cbs` tem como chave de negócio **NCM mais `Vigencia_Inicio`** e `ID_Classificacao_Mercadoria` obrigatório. O NCM **3926.90 aparece em dois itens com taxas diferentes** (item 15, correias: 50%; item 16, artigos de laboratório e farmácia: 20%): na chave atual a segunda linha seria recusada. E as duas linhas sem NCM (instalações, edificações) não cabem. A solução é a mesma da Q238-1, na outra tabela.

# 6. O que não muda o dicionário

- **NT 2026.007, 2026.008 e 2025.002**: são versões **anteriores** às que o dicionário já usa (revisões 49 a 51); nada novo.
- **Página da PGFN** (cidadania tributária): sem conteúdo de CBS/IBS que o dicionário use.
- **ACE-14** (página do MDIC): confirma que a Lista de Exceções Temporárias é o **Anexo X da Res. 272/2021** (veículos, ônibus, caminhões, tratores rodoviários, chassis, reboques, carrocerias e cabinas, fora dos BK), instituída pela Res. 708. **A lista em si fica em outro link, que não veio.** Ela só interessa à condição do art. 1º, I, a (Q236-4: ACE-14 sem desenho).
- **Apresentação da ZFM** (CBS e IPI, Decreto 12.955, arts. 443 a 550): resumo didático de importação com suspensão (art. 443/528), internamento com alíquota zero (445/529), bens intermediários (448/530), crédito presumido de 6% e 2% (450/531), operações internas (451/532) e as ALC (461 a 467, 536 a 539). **Não traz lista de NCM**; as regras seguem no documento 158 (Q158-E1 a E4).

# 7. Perguntas novas

| Id | Pergunta | Recomendação |
|---|---|---|
| Q239-1 | A lista da Res. 822 entra com `Vigencia_Inicio` = **01/02/2026** (entrada em vigor da 822) e **sem registrar as versões 2024 a 2025** (só a lista vigente, Q235-4)? A alternativa é 02/12/2025 (data do Diário Oficial) | **Sim** (01/02/2026) |
| Q239-2 | Em `Cad_Taxa_Depreciacao_Cbs`, acrescentar o campo **`Numero_Item_Anexo`** (inteiro) à chave de negócio e tornar `ID_Classificacao_Mercadoria` **opcional**, para guardar o 3926.90 duas vezes e as linhas "instalações" e "edificações" (14.438 → 14.439 campos; a revisão 52 teria 1.242 entidades e 1.508 tabelas) | **Sim** |
| Q239-3 | Os NCM de listas oficiais que **não existem mais** na tabela de 16/11/2026 (Reporto 4, depreciação 10, Res. 553 original 28 e Res. 822 2) ficam **fora da carga** e são listados para a equipe e o contador (a chave estrangeira falharia); ou se mapeia cada um pelo NCM sucessor (Res. Gecex 926/2026)? | **Ficam fora** e listados; o mapeamento exige o texto da correlação |

# 8. Arquivos

A **Carga239** (zip, 9 arquivos, com LEIA-ME): 01-decreto-12955 (369), 02-depreciacao (208, depende da Q239-2), 03-sem-similar-553-res822 (7.188) e 04-conferencia (5 arquivos, não carregar).

# 9. Pendências com você

- **Lista Vigente** da Res. 553 (xlsx do MDIC; seção 0 do documento 38).
- **Lista do Anexo X da Res. 272** (ACE-14): só se quiser o inciso I, a, na lista.
- Q239-1, Q239-2 e Q239-3 (seção 1.50 do documento 38).
- Para a equipe: os 14 NCM fora da tabela (arquivo de conferência) e o rótulo dos arts. 196 e 197.
