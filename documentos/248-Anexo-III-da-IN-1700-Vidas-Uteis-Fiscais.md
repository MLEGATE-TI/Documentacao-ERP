# Anexo III da IN RFB 1.700/2017: a tabela de vidas úteis fiscais — Documento 248 (versão 3)

*Você enviou o **Anexo III da IN RFB 1.700/2017 em texto** (as taxas anuais de depreciação por NCM, que no PDF do Diário Oficial eram imagens) e uma nova cópia da IN, igual à que eu já tinha. Este documento transforma a tabela em **carga e desenho**: uma tabela de referência das vidas úteis fiscais, ligada ao grupo de bem do documento 247. Na conferência com o Anexo I do Decreto 12.955 achei **2 linhas que a carga do decreto deixou de fora** (instalações e edificações). Na **versão 2** você aprovou as **Q248-1 a Q248-6** e respondeu as **C372 e C373**. Na **versão 3**, depois do seu "consolidar", o desenho foi **aplicado ao dicionário na revisão 55** (documento 249) e **corrigi um erro meu**: eu havia dito que eram 12 linhas de falha minha, mas 10 delas foram **decisão sua** (Q239-3: NCM que não existe mais na tabela de 16/11/2026 não entra na carga). A Q248-4 foi aprovada com essa premissa errada; ver a seção 3.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **A tabela está completa:** 220 linhas com vida útil e taxa (de 2 a 25 anos), mais as notas (1) a (3). Inclui as linhas "instalações" (10 anos) e "edificações" (25 anos), que não têm NCM, e a do capítulo 57 inteiro (tapetes).
2. **O Anexo III da IN e o Anexo I do Decreto 12.955 são a mesma lista:** os 220 itens têm a mesma vida útil e a mesma taxa. O decreto, de abril de 2026, reproduz a tabela da IN, o que é um bom sinal de que ela segue em uso.
3. **Falha minha, só em 2 linhas:** a carga do Anexo I do decreto (Carga52, 208 linhas) deixou de fora os itens **1 (instalações, 10 anos, 10%) e 2 (edificações, 25 anos, 4%)**, que têm prazo e taxa no Diário Oficial (a Carga52 leu que não tinham). Outras 10 linhas também não estão nela, mas por **decisão sua** (Q239-3), e **não foram corrigidas** (seção 3). A correção é só carga: 208 para 210 linhas.
4. **Desenho proposto:** uma tabela nova, `Cad_Taxa_Depreciacao_Fiscal` (**16 campos**, com vigência), e **2 campos** na linha do grupo de bem do documento 247 (a referência ao anexo e a justificativa quando a empresa usa outra vida). Total: **+1 entidade e +18 campos**.
5. **Como o ERP usa a tabela:** ao montar o grupo de bem, o ERP procura a linha pelo NCM e **sugere** a vida útil fiscal; se a vida do tipo fiscal for **menor** que a do anexo (taxa maior que a admitida), o ERP **avisa** e pede a justificativa (art. 124, § 1º da IN). Quem decide continua sendo o grupo de bem.
6. **Carga:** 222 linhas (as 220 mais as notas (1) e (2) como linhas com condição de uso), provisórias até o contador confirmar; as 10 linhas de NCM que não existe mais na tabela de 16/11/2026 ficam com a chave de NCM vazia e o código só em texto. Na Carga55: `Cad_Taxa_Depreciacao_Fiscal_222.csv` e `Cad_Taxa_Depreciacao_Cbs_correcao_2.csv`.
7. **Para você:** nenhuma pergunta nova; **confirme** se quer manter as 10 linhas de NCM obsoleto fora da tabela da CBS (como na Q239-3) ou carregá-las com a chave vazia. **Para o contador:** C372 e C373 respondidas por você, a confirmar por ele. Aplicado na **revisão 55** (documento 249): 1.249 entidades e 14.529 campos.

# 2. O que foi recebido e conferido

| Arquivo | O que é | O que fiz |
|---|---|---|
| Anexo III da IN RFB 1.700/2017 (19 páginas, texto) | Impressão do site COSIF (18/11/2026), com a tabela por NCM e as notas (1) a (3). A nota bibliográfica do COSIF é de 13/05/2020 | Extraí por tabela e por posição das palavras (a primeira extração perdeu 5 linhas que quebram de uma página para a outra; refiz) e conferi: **220 linhas com vida útil e taxa, e em todas a taxa é 100 dividido pela vida** |
| IN RFB 1.700/2017 (110 páginas, DOU) | Cópia nova | Comparei com a que eu já tinha: **o texto é idêntico**, só muda a hora da impressão |
| Anexo I do Decreto 12.955/2026 (DOU, que você enviou antes) | A mesma tabela, com os itens numerados de 1 a 258 | Usei como **fonte oficial** para conferir o Anexo III e para conferir a carga do decreto |

**Limite:** o texto do Anexo III que você enviou é uma **transcrição do COSIF**, não o texto do Diário Oficial (no PDF do DOU as tabelas são imagens). A conferência com o Anexo I do decreto cobre isso, mas a pergunta se a IN teve alteração depois de 2017 vai ao contador (C372).

# 3. O que a conferência achou

| Comparação | Resultado |
|---|---|
| Anexo III da IN × Anexo I do decreto | **Os mesmos 220 itens**, com a mesma vida útil e a mesma taxa |
| Anexo I do decreto × a carga do dicionário (`Cad_Taxa_Depreciacao_Cbs`, 208 linhas) | **12 linhas não estão na carga, de dois tipos.** **(a) 2 linhas que ficaram de fora por erro de leitura:** itens 1 (instalações, 10 anos, 10%) e 2 (edificações, 25 anos, 4%). **(b) 10 linhas que ficaram de fora por decisão sua (Q239-3):** o NCM não existe mais na tabela vigente de 16/11/2026 (Res. Gecex 926/2026) e a chave estrangeira falharia: itens 20 (4204, correias), 130 (8469, máquinas de escrever), 135 (8470.40, máquinas de contabilidade), 169 (8520, gravadores de dados de voo), 174 a 177 (8524.3, 8524.40, 8524.5 e 8524.60, discos, fitas e cartões), 211 (8903.10, barcos infláveis) e 224 (9009, fotocópia e termocópia) |
| Outras diferenças | Nenhuma. As 208 linhas da carga batem com o decreto |

**A causa das duas linhas é minha:** a Carga52 leu que "instalações" e "edificações" não tinham prazo nem taxa, e o texto do LEIA-ME da carga repetiu isso; o DOU traz os dois. Sem elas, o crédito da cooperativa de uma instalação ou de uma edificação **não encontraria a taxa**. A correção é a carga `Cad_Taxa_Depreciacao_Cbs_correcao_2.csv` (2 linhas, mesmo formato da Carga52, Decreto 12.955/2026, Anexo I, itens 1 e 2, vigência de 30/04/2026, provisória): a tabela passa de 208 para **210** linhas. **Erro que corrijo nesta versão:** nas versões 1 e 2 eu disse que as 12 linhas eram falha minha e propus carregar todas; as 10 de NCM obsoleto foram decisão sua, e **mantive-as fora** da tabela da CBS. Elas estão na tabela fiscal (que guarda o NCM só em texto, com a chave vazia), então a informação não se perde. Se você quiser as 10 também na tabela da CBS, é só dizer: a chave ficaria vazia e o crédito não acharia a taxa pelo NCM.

# 4. Desenho

## 4.1 A tabela `Cad_Taxa_Depreciacao_Fiscal` (com vigência, 16 campos)

Tabela de referência (o dado vem da norma, não da empresa), com o mesmo desenho da tabela do Anexo I da CBS:

| Campo | Regra |
|---|---|
| `ID_Taxa_Depreciacao_Fiscal` e `ID_Taxa_Depreciacao_Fiscal_Versao` | Identificador e chave da versão |
| `Numero_Item_Anexo` (identidade) | O número da linha na carga (1 a 222), na ordem da tabela. Existe porque o **mesmo NCM aparece em duas linhas** (3926.90: correias, 2 anos; artigos de laboratório, 5 anos) |
| `ID_Classificacao_Mercadoria` (opcional) | O NCM, em qualquer nível (capítulo, posição, subposição ou item, como o anexo publica). Vazio nas linhas sem NCM (instalações, edificações e a nota (2)) |
| `NCM_na_Tabela` (opcional) | O código como o anexo publica ("Capítulo 57", "8470.40") |
| `Descricao_Bem` | A descrição da linha, como a norma publica |
| `Descricao_Cabecalho` (opcional) | A descrição da posição "pai", quando a linha é uma subposição ("-Pontes e elementos de pontes" sob "Construções, de ferro fundido..."): 44 linhas |
| `Vida_Util_Anos` | De 2 a 25 anos |
| `Percentual_Anual` | A taxa do anexo (por exemplo 10, 20, 33,3) |
| `Condicao_Uso` (opcional) | Preenchida só nas linhas das notas (1) e (2): "Indústria de vidro", "Indústria química" |
| `Fundamento_Legal` | "IN RFB 1.700/2017, Anexo III, NCM 8470.40" ou "..., Nota (2)" |
| `Situacao_Dado` | Provisório até a conferência; `ID_Instancia_Aprovacao` (opcional) guarda a validação |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` (opcional) | Início em 16/03/2017 (a publicação da IN no DOU); fim em 31/12/9999 |

**Carga proposta:** 222 linhas: 220 do anexo, mais a **nota (1)** (fornos para a indústria de vidro, posição 8417: **3 anos, 33,3%**, no lugar dos 10 anos da linha) e a **nota (2)** (máquinas, equipamentos e instalações industriais do anexo usados na indústria química: **5 anos, 20%**). A distribuição: 148 linhas de 10 anos, 44 de 5 anos, 8 de 4 anos, 6 de 3 anos, 6 de 20 anos, 5 de 25 anos e 5 de 2 anos.

## 4.2 A ligação com o grupo de bem

Na linha `Cad_Ativo_Imobilizado_Classe_Depreciacao` do documento 247 entram **2 campos opcionais** (a linha passa de 10 para 12 campos):

| Campo | Regra |
|---|---|
| `ID_Taxa_Depreciacao_Fiscal` | A linha do anexo que fundamenta a vida útil deste grupo para este tipo. Quem preenche a vida útil continua sendo o grupo: a referência dá a **sugestão e a rastreabilidade** |
| `Justificativa_Vida_Util` | Texto livre (laudo, prova de taxa diferente). Exigida quando a vida do tipo fiscal é menor que a do anexo |

## 4.3 Regras novas (continuam a numeração do documento 247)

| Regra | O que faz |
|---|---|
| R12 | **Busca por NCM:** ao montar a linha do grupo, o Motor procura a linha do anexo pelo NCM do bem (do item da nota de aquisição, `ID_Item_Nota_Entrada_Origem`) do mais específico para o mais geral (item, subposição, posição, capítulo) e **sugere** a vida. Se achar duas linhas (3926.90), mostra as duas. As linhas "instalações" e "edificações" são escolhidas direto pelo grupo. **Terreno não tem linha** (art. 122, parágrafo único) |
| R13 | **Aviso de taxa acima da admitida:** no tipo marcado como fiscal, se a vida útil do grupo for menor que a do anexo (taxa maior), o ERP avisa e exige a `Justificativa_Vida_Util`; **não bloqueia**, porque o art. 124, § 1º admite outra taxa com prova. Não vale para os tipos incentivada e acelerada, que têm regra própria (seção 4.7 do documento 247) |
| R14 | **Notas (1) e (2):** viram linhas com `Condicao_Uso`. Quem escolhe a linha é o **grupo de bem** (um grupo de máquinas de uma indústria química aponta para a nota (2) e usa 60 meses), nunca o ativo isolado, como você disse na C368 e **reforçou na C373**: o que está no grupo "já está classificado", o ativo **herda a parametrização do grupo** e nada disso fica no item, "que dificulta alterações". Leitura minha: a linha por ativo do documento 247 (`Cad_Ativo_Imobilizado_Depreciacao_Parametro`) fica **só para a exceção** (bem usado, bem fora da atividade incentivada), nunca para a regra |
| R15 | **Nota (3), partes e acessórios:** o bem **componente** (`Identificacao_Bem` = componente, com `ID_Ativo_Principal`) **sem `Data_Inicio_Depreciacao` não deprecia** (exceção à regra de usar a data de aquisição); quando o usuário informa a data da incorporação, ele passa a depreciar **pelo restante da vida do bem principal**, como a manutenção capitalizada (documento 247, R1), o que equivale a "integrar a base da quota do principal". **Confirmada na C373 (c):** a parte avulsa só começa a depreciar na incorporação |

## 4.4 A correção da tabela da CBS

As **2 linhas** de `Cad_Taxa_Depreciacao_Cbs` (itens 1 e 2) entram como carga (seção 3). Como a tabela fiscal e a da CBS têm a mesma lista de 220 itens, o Motor da carga compara as duas e avisa se um dia divergirem; as 10 linhas de NCM obsoleto aparecem como diferença conhecida.

# 5. O que fica fora

| Item | Por quê |
|---|---|
| Os Anexos I e II da IN 1.700 | Não foram pedidos e, no PDF do DOU, continuam em imagens |
| Vidas úteis de outros normativos (por exemplo, a IN SRF 162/1998) | A IN 1.700 trouxe a tabela atual |
| Uma tabela única para IRPJ e CBS | É a alternativa da Q248-1; a recomendação é manter separadas |
| Preencher os grupos de bem da Mlegate | Só a empresa sabe os grupos; o ERP sugere a vida e o contador confirma |

# 6. Perguntas

**Aprovadas por você em 18/11/2026 ("seguir com as recomendações", D-N637):** Q248-1 (tabela `Cad_Taxa_Depreciacao_Fiscal` separada da tabela da CBS, 16 campos), Q248-2 (2 campos na linha do grupo de bem e aviso, sem bloqueio, de taxa acima da admitida), Q248-3 (carga das 222 linhas como provisórias, vigência desde 16/03/2017), Q248-4 (correção da carga do Anexo I do decreto: aprovada como "12 linhas, 208 para 220"; **aplicada só às 2 linhas sem NCM, 208 para 210**, porque as outras 10 são decisão sua da Q239-3; ver a seção 3), Q248-5 (nota (3): o componente só deprecia depois de incorporado, pelo restante da vida do principal) e Q248-6 (notas (1) e (2) como linhas com condição de uso, escolhidas pelo grupo de bem).

**Novas, para você:** nenhuma.

# 7. Para o contador (documento 188)

**Respondidas por você em 18/11/2026**, a confirmar pelo contador:

| Id | Sua resposta | Como ficou no desenho |
|---|---|---|
| **C372** | "Correto, pode colocar esta carga provisória" | Carga de 222 linhas, provisória, vigência desde 16/03/2017 (a data foi lida como confirmada junto com a carga) |
| **C373** (a) | A nota (2) fica **no grupo de imobilizado**: o que está no grupo já está classificado; não deixar no item, que dificulta alterações; prever sempre isto no grupo, e quem está no grupo herda a parametrização do grupo | R14: o grupo escolhe a linha da nota; o ativo herda. Não há regra por NCM para dizer o que é "máquina industrial": é o grupo que diz |
| **C373** (b) | "Não se preocupar com isto, deixar parametrizados e definirmos isto no grupo" | Nota (1) (fornos de vidro) é uma linha da tabela; quem usa é o grupo de bem; o ERP não confere o NCM 8417 |
| **C373** (c) | "A parte avulsa só começa a depreciar na incorporação" | R15 confirmada |

Leitura minha a conferir: na C372 você não falou da data de início, e li "correto" como valendo para a carga inteira, inclusive a vigência de 16/03/2017.

# 8. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N637 | Aprovação das **Q248-1 a Q248-6**; respostas às **C372 e C373** (carga provisória; as notas e a parametrização ficam no grupo de bem, que o ativo herda; a parte avulsa só deprecia na incorporação) | "Q248-1 a Q248-6 Seguir com as recomendações", C372 e C373, 18/11/2026 |
| D-N636 | Recebido o Anexo III da IN 1.700 em texto (resolve a Q247-10 (c)); desenho da tabela fiscal de vidas úteis ligada ao grupo de bem; **achada a falha da carga do Anexo I do decreto (2 linhas; as outras 10 eram decisão da Q239-3)**; perguntas Q248-1 a Q248-6 e C372 e C373 | Envio do Anexo III e da IN, 18/11/2026 |

# 9. O que mudou no "consolidar" (revisão 55, documento 249)

**Aplicado em 18/11/2026.** O "consolidar" aplicou o desenho dos documentos 247 e 248 e as cargas (Carga55); o resultado é o do documento 249.


| Medida | Revisão 54 | Com o 247 aprovado | Com o 247 e o 248 |
|---|---|---|---|
| Entidades | 1.243 | 1.248 | **1.249** (+1: `Cad_Taxa_Depreciacao_Fiscal`) |
| Campos | 14.460 | 14.511 | **14.529** (+16 na entidade e +2 na linha do grupo) |
| Cargas | 208 linhas em `Cad_Taxa_Depreciacao_Cbs` | igual | CBS com **210** linhas (+2) e `Cad_Taxa_Depreciacao_Fiscal` com **222** |

# 10. Fontes e limites

**Lido:** o Anexo III da IN RFB 1.700/2017 (transcrição do COSIF), a IN 1.700 (DOU, dois PDFs idênticos) e o Anexo I do Decreto 12.955/2026 (DOU). Conferência: os 220 itens do Anexo III contra o Anexo I do decreto, por NCM, vida útil e taxa; as 12 linhas que não estavam na carga foram conferidas uma a uma no texto do DOU do decreto e, depois, contra a decisão da Q239-3 e o arquivo `NCM_do_decreto_fora_da_tabela_vigente_14.csv` da Carga52, o que separou as 2 falhas das 10 decisões.

**Limites:** o Anexo III é transcrição de um site; uma busca na internet sobre alterações da IN depois de 2017 não achou nada conclusivo, e por isso a pergunta vai ao contador (C372). Cinco linhas quebram de uma página para a outra (7322, 8207, 8460, 8515 e 8705) e tiveram a descrição juntada por posição: a quebra de linha pode diferir do original, sem efeito na NCM, na vida útil e na taxa. O desenho não preenche os grupos de bem da Mlegate.
