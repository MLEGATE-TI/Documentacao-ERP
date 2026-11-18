# Desenho da Depreciação do Ativo — Documento 247 (versão 6)

*Você escreveu "vamos desenhar a depreciação que é simples", pediu **n tipos de depreciação** correndo em paralelo, com **contabilização por tipo**, e enviou a **IN RFB 1.700/2017** pedindo a **acelerada** das usinas de cana e da química. Na **versão 6** entrou o **Anexo III da IN 1.700**, que você enviou em texto (documento 248). Na **versão 5** você aprovou as **Q247-11 a Q247-14** ("seguir com as recomendações") e respondeu as **C369 a C371**; antes, na versão 4, tinha aprovado as Q247-1 a Q247-10, respondido as C365 a C368 e pediu para **considerar a redução ao valor recuperável (CPC 01), a reavaliação e outras acelerações incentivadas**; os parâmetros passaram a ser **por grupo de bem** e o desenho ganhou as **pausas de depreciação**. O desenho está **todo aprovado**, mas **nada foi aplicado ao dicionário** (revisão 54): ele só muda com o seu "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **A empresa cadastra quantos tipos de depreciação quiser** (fiscal, gerencial, acelerada, incentivada, de gestão etc.), e cada ativo corre todos os tipos que o **grupo de bem** (a classe do ativo) tem, **ao mesmo tempo e de forma independente**: cada tipo tem vida útil, valor residual e saldo próprios.
2. **Quem decide é o grupo de bem.** É na linha do grupo que se diz quais tipos valem, a vida útil e o residual de cada um, e **qual tipo é o fiscal principal** (e qual é o gerencial principal). Mesmo numa empresa química, um grupo pode ter acelerada e outro não.
3. **Cada tipo decide se lança na contabilidade**, e as contas saem do Motor de Regras (tipo, grupo e centro de custo). O F120 da EFD-Contribuições lê o **tipo marcado como fiscal principal do grupo**, seja ele normal, por turnos ou incentivado.
4. **Estrutura aprovada: 5 entidades novas e 51 campos** (48 nas entidades e 3 no ativo): o catálogo de tipos, os parâmetros por grupo e por ativo, o **ajuste de valor** (impairment e reavaliação) e as **pausas de depreciação**. Revisão 54: 1.243 entidades e 14.460 campos; depois: **1.248 e 14.511**.
5. **Uma regra de cálculo para todos os tipos:** a quota do mês é o saldo depreciável dividido pelos meses que faltam; **cota cheia no mês**, começando no mês da data de início da depreciação do cadastro do ativo, e **sem contar os meses de pausa**.
6. **Carga inicial de 4 tipos, editável:** gerencial (lança), fiscal, acelerada por turnos e acelerada incentivada rural (art. 260 da IN 1.700). **Outras acelerações** entram como tipos novos, sem mudar estrutura.
7. **Para você:** nenhuma pergunta nova; o Anexo III chegou (Q247-10 c respondida) e virou o documento 248, já aprovado (Q248-1 a Q248-6). **Para o contador:** C365 a C371 respondidas por você, a confirmar por ele. O próximo passo é o seu "consolidar".

# 2. O que foi decidido nesta rodada

| Item | Decisão | Onde está no desenho |
|---|---|---|
| Q247-1 a Q247-10 | **Aprovadas** com as recomendações (D-N634) | Seção 6 |
| Q247-10 (c) | **Respondida:** você enviou o Anexo III da IN 1.700 em texto (D-N636) | Documento 248 |
| Q247-11 a Q247-14 | **Aprovadas** com as recomendações (D-N635): ajuste de valor, só registra o valor informado, pausas, outras acelerações como tipos novos sem carga | 4.7, 4.8 e 4.9 |
| C369 | "Sim fica parada": a pausa vale também para a depreciação **fiscal** (o bem parado não deprecia) | 4.9 |
| C370 | "Sim correto": tratamento da redução ao valor recuperável e da reavaliação como no documento | 4.8 |
| C371 | "Ok deixe preparado para receber outras, mas não precisa preencher agora" | 4.7 |
| C365 | Quota cheia no mês, usando o parâmetro "depreciar a partir de" do cadastro do ativo | R3 (4.3) |
| C366 | O crédito de PIS e Cofins usa o tipo fiscal; se o fiscal for o por turnos, é esse, e o crédito fica proporcional a ele | 4.5 |
| C367 | "Sim, correto": acelerada por turnos sem lançamento contábil, diferença na Parte B, coeficientes 1,5 e 2,0, bem usado e bem de pequeno valor | 4.1 e 4.2 |
| C368 (a) e (b) | Parâmetros **por grupo de bem**; na química, itens com acelerada e itens sem | 4.2 |
| C368 (c) | F120 pela base marcada como fiscal, incentivada ou não | 4.5 |
| C368 (d) | Quota integral a partir do mês de início da depreciação; o bem pode ser comprado e usado meses depois; **a depreciação pode ser pausada** | R3 e R11 (4.3) |
| Pedido novo | Considerar **redução ao valor recuperável (CPC 01)**, **reavaliação** e **outras acelerações incentivadas** | 4.1, 4.7 e 4.8 |

# 3. O que o dicionário já tem

| Peça | Onde está | O que faz |
|---|---|---|
| Ativo e grupo de bem | `Cad_Ativo_Imobilizado`, `Cad_Ativo_Imobilizado_Classe` | Data e valor de aquisição, vida útil (do ativo, ou da classe quando vazio), conta de imobilizado, centro de custo, nota de aquisição, componente e bem principal, data da baixa |
| Resultado mensal | `Mov_Ativo_Depreciacao` | Um registro por ativo, base e período, com o tipo; `ID_Lancamento` já é opcional |
| Bases em paralelo | `Mov_Ativo_Depreciacao.ID_Manutencao_Origem` | Manutenção capitalizada deprecia pelo **restante** da vida útil do ativo, com saldo próprio (Fase 0, seção 12) |
| Fechamento | Bloco `ativo_imobilizado` | Mês fechado não recebe nem altera depreciação |
| Moedas | `Mov_Lancamento_CTA` | A réplica do lançamento em cada moeda é automática |
| Contas | Motor de Regras (`Cad_Motor_Regra`, `_Criterio` em domínio aberto e `_Resultado` com `conta_contabil_debito` e `conta_contabil_credito`) | Novos critérios e uma nova área de negócio são linhas de domínio |
| Subcontas (Lei 12.973) | `Cad_Subconta_Contabil`, `Mov_Item_Subconta`, `Mov_Subconta_Movimento` | Já guardam a subconta vinculada ao ativo e a realização por depreciação ou baixa |
| Teste de impairment do ágio | `Mov_Agio_Teste_Impairment` | Valor recuperável informado, perda e lançamento; "o cálculo em si é de aplicação, não de estrutura" |
| Quem lê o resultado | `Cad_Ativo_Direito_Credito_Pis_Cofins` (F120 e F130), `Mov_Cooperativa_Transferencia_Credito`, `Cad_Area_Producao.ID_Ativo_Imobilizado` | F120 e F130 leem a depreciação em `Mov_Ativo_Depreciacao` |
| Tabela do Anexo I da CBS | `Cad_Taxa_Depreciacao_Cbs` (208 linhas provisórias; 210 com a correção da Carga55) | Taxa e vida útil por item e NCM, com vigência |

# 4. Desenho

## 4.1 O catálogo de tipos: `Cad_Tipo_Depreciacao` (com vigência, 15 campos)

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Tipo_Depreciacao` e `ID_Tipo_Depreciacao_Versao` | identificadores | Identidade e versão (padrão da Fase 0, seção 2) |
| `Codigo` | código, único | Ex.: GERENCIAL, FISCAL, ACELERADA |
| `Nome` | texto | Nome que o usuário vê |
| `Finalidade` | enumeração {fiscal, gerencial, outra} | A quem o tipo serve; pode haver vários tipos com a mesma finalidade. **Qual é o principal é decidido no grupo de bem** (4.2) |
| `Tipo_Calculo` | enumeração {linear, linear_com_turnos, integral_no_ano, linear_com_multiplicador} | **Linear:** saldo depreciável dividido pelos meses que faltam. **Com turnos:** quota do tipo-base vezes o coeficiente de turnos do ativo. **Integral no ano:** toda a base no mês de início (incentivada rural, 4.7). **Com multiplicador:** quota do tipo-base vezes o `Multiplicador` do tipo (outras acelerações). Domínio aberto: unidades produzidas entram depois como valor novo |
| `ID_Tipo_Depreciacao_Base` | referência a si mesmo, opcional | Obrigatório nos cálculos com turnos e com multiplicador: o tipo que dá a quota normal |
| `Multiplicador` | número, opcional | Só no cálculo com multiplicador |
| `Usa_Valor_Residual` | booleano | Verdadeiro na gerencial (CPC 27); falso na fiscal |
| `Considera_Ajuste_Valor` | booleano | Verdadeiro na gerencial: a redução ao valor recuperável e a reavaliação (4.8) mudam a base. Falso na fiscal, que segue o custo de aquisição (IN 1.700, art. 123) |
| `Gera_Lancamento` | booleano | Se verdadeiro, cada quota gera lançamento; as contas saem do Motor de Regras (4.4) |
| `Fundamento_Legal` | texto, opcional | A norma do tipo (por exemplo "IN RFB 1.700/2017, art. 260"), para as acelerações incentivadas |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto opcional | Padrão de vigência |

**Carga inicial (4 linhas, editáveis; a empresa liga cada tipo aos grupos que o usam):**

| Código | Finalidade | Cálculo | Residual | Considera ajuste | Lança |
|---|---|---|---|---|---|
| GERENCIAL | gerencial | linear | sim | sim | **sim** |
| FISCAL | fiscal | linear | não | não | não |
| ACELERADA | fiscal | linear com turnos (base: FISCAL) | não | não | não |
| INCENTIVADA_RURAL | fiscal | integral no ano | não | não | não |

## 4.2 Parâmetros por grupo de bem e por ativo

Um tipo **vale para um ativo** quando o grupo dele tem uma linha para o tipo (ou o próprio ativo tem), e a linha do ativo não diz `Aplica` falso. **Sem linha, sem depreciação naquele tipo**: é assim que o terreno não deprecia (IN 1.700, art. 122, parágrafo único). A linha do grupo vale pela **data de início da depreciação do ativo**: bem adquirido na vigência de uma incentivada continua com ela depois que a norma acabar.

| Entidade | Campos | Regra |
|---|---|---|
| `Cad_Ativo_Imobilizado_Classe_Depreciacao` (**com vigência**, 10 campos) | `ID_Ativo_Imobilizado_Classe_Depreciacao` e `_Versao`, `ID_Ativo_Classe`, `ID_Tipo_Depreciacao`, `Vida_Util_Meses` (opcional), `Percentual_Valor_Residual` (opcional), **`Principal`** (booleano), `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | A vida útil e o residual **do grupo para aquele tipo**; vazio na vida útil usa a vida padrão da classe. **`Principal`:** marca, entre os tipos de finalidade fiscal do grupo, **o fiscal principal**, e entre os de finalidade gerencial, **o gerencial principal**. O Motor avisa se o grupo tiver tipo fiscal sem principal ou mais de um. Na química, o grupo das máquinas industriais leva a vida fiscal de **60 meses** (nota 2 do Anexo III) |
| `Cad_Ativo_Imobilizado_Depreciacao_Parametro` (sem vigência, 6 campos) | `ID_Ativo_Imobilizado_Depreciacao_Parametro`, `ID_Ativo`, `ID_Tipo_Depreciacao`, `Aplica` (booleano, padrão verdadeiro), `Vida_Util_Meses` (opcional), `Valor_Residual` (opcional) | Sobrepõe o grupo, para **um ativo e um tipo** (bem usado, prova de taxa diferente pelo art. 124, § 1º, ou bem fora da atividade incentivada: `Aplica` falso, art. 260, § 6º). Revisão de vida útil ou de residual vale daí para frente (R6) |

**Três campos novos no ativo** (`Cad_Ativo_Imobilizado`), todos opcionais:

| Campo | Regra |
|---|---|
| `Data_Inicio_Depreciacao` | É o parâmetro "depreciar a partir de": o mês em que o bem entra em uso (IN 1.700, art. 121, § 2º: instalado, posto em serviço ou em condições de produzir). O bem pode ser comprado e usado meses depois; vazio usa `Data_Aquisicao` |
| `Coeficiente_Turnos` | 1,5 (dois turnos) ou 2,0 (três turnos); vazio é um turno. Só os tipos com cálculo "linear com turnos" o leem. O Motor avisa se o valor for outro |
| `ID_Taxa_Depreciacao_Cbs` | A linha do Anexo I da CBS; o Motor sugere pela NCM da nota de aquisição e o usuário confirma na linha (como na habilitação do REIDI, D-N269) |

**Em `Mov_Ativo_Depreciacao`:** o campo `Tipo_Depreciacao` (lista fixa) vira `ID_Tipo_Depreciacao` (referência ao catálogo); o registro continua único por ativo, base, tipo e período.

## 4.3 O cálculo do mês (regra do Motor, sem campo)

| Nº | Regra |
|---|---|
| R1 | Para cada ativo, em cada mês aberto, para cada tipo que vale para o ativo e para cada base (a aquisição e cada manutenção capitalizada), o Motor gera um registro de `Mov_Ativo_Depreciacao`. Os tipos correm **em paralelo e sem depender uns dos outros**, salvo os que leem um tipo-base (turnos e multiplicador) |
| R2 | **Vida útil** do ativo no tipo, na ordem: o parâmetro do ativo, a linha do grupo e, por último, a vida padrão (`Cad_Ativo_Imobilizado.Vida_Util_Meses` ou `Vida_Util_Padrao_Meses` da classe). A linha do grupo é a vigente na data de início da depreciação do ativo |
| R3 | **Cota cheia no mês** (sem proporção por dia; IN 1.700, art. 123, § 2º): o primeiro mês é o da `Data_Inicio_Depreciacao`. O mês da **baixa** fica para o documento da baixa do ativo (Q247-8); até lá, sem quota no mês da baixa |
| R4 | **Saldo depreciável** = base, mais a soma dos ajustes de valor (só nos tipos com `Considera_Ajuste_Valor`, 4.8), menos o valor residual (só nos tipos com `Usa_Valor_Residual`), menos o que o tipo já depreciou naquela base. O residual vem do parâmetro do ativo, ou do percentual do grupo sobre a base, ou zero |
| R5 | **Meses que faltam** = vida útil em meses menos os **meses já depreciados** (meses com quota; os meses de pausa não contam). A manutenção capitalizada usa os meses que faltam do ativo |
| R6 | **Quota** = saldo depreciável dividido pelos meses que faltam, em centavos; no último mês a quota é o saldo inteiro, sem sobra de arredondamento. **Revisão** de vida útil, de residual ou ajuste de valor vale daqui para frente (a fórmula já faz o ajuste), e os meses fechados não mudam |
| R7 | **Cálculo com turnos ou com multiplicador:** quota do tipo-base vezes o `Coeficiente_Turnos` do ativo (turnos) ou o `Multiplicador` do tipo, limitada ao que falta do custo; sem coeficiente, o tipo por turnos não gera quota para o ativo. Tipo-base e tipo acelerado somados nunca passam do custo |
| R8 | **Fechamento:** mês fechado não gera nem altera quota; correção é lançamento de ajuste, não reescrita (como já está na Fase 0) |
| R9 | O Motor **sugere** a vida útil fiscal quando o bem tem linha no Anexo III da IN RFB 1.700/2017, e o contador confirma; a tabela está no **documento 248** (`Cad_Taxa_Depreciacao_Fiscal`, 222 linhas), ligada ao grupo de bem pela linha do tipo fiscal |
| R10 | **Cálculo integral no ano:** no mês de início, a quota é toda a base menos o que o tipo já depreciou; nos meses seguintes, zero |
| R11 | **Pausa:** os meses de uma pausa (4.9) **não geram quota** nos tipos afetados, a vida útil **não corre** nesses meses (R5) e o valor não pago **não é recuperado** depois (IN 1.700, art. 121, § 6º) |

## 4.4 Contabilização por tipo

Para cada registro de um tipo com `Gera_Lancamento` verdadeiro, o Motor pede ao **Motor de Regras** as contas, com a área de negócio `depreciacao_ativo` e três critérios (linhas novas no domínio aberto, sem mudar a estrutura):

| Critério | Exemplo |
|---|---|
| `tipo_depreciacao` | O tipo GERENCIAL usa a despesa X; um tipo de gestão para um investidor usa a conta Y |
| `classe_ativo` | Máquina de produção vai para custo; equipamento de informática vai para despesa administrativa |
| `centro_custo_ativo` | O centro de custo do ativo (`ID_Dimensao_Contabil_Valor_Centro_Custo`) vai na dimensão do lançamento; assim a depreciação de uma máquina de produção entra no custo da área |

O resultado é `conta_contabil_debito` e `conta_contabil_credito` (já existem). O lote leva `Origem_Tipo` = `depreciacao_ativo_imobilizado`. **Sem regra para a combinação**, a quota sai **sem lançamento e pendente**, com aviso ao contador, e o fechamento do bloco `ativo_imobilizado` não conclui até não restar pendência (Q247-9, aprovada).

## 4.5 Quem lê o resultado

| Consumidor | Lê | Observação |
|---|---|---|
| EFD-Contribuições (F120 e F130) | O tipo **principal de finalidade fiscal do grupo do ativo**, qualquer que seja (normal, por turnos ou incentivado) | Resposta da C366 e da C368 (c): o crédito de PIS e Cofins fica proporcional à quota desse tipo. **Leitura minha:** você escreveu "F200"; o F200 é o registro da atividade imobiliária, e o encargo de depreciação do ativo é o F120. Confirme |
| ECD | Os lançamentos dos tipos que lançam | Já vale pelo `Origem_Tipo` |
| e-Lalur | A diferença entre **cada tipo de finalidade fiscal** e o **principal gerencial**, mais os ajustes de valor (4.8) | Consulta por ativo e período; o contador lança na Parte A ou B (como na Q93-8). A IN 1.700 confirma o caminho: art. 124, §§ 4º e 5º, e art. 260, §§ 1º a 5º |
| Custo da área de produção | Os lançamentos, pelo centro de custo | Sem estrutura nova |
| Crédito do ativo da cooperativa (art. 394 do Decreto 12.955) | A linha do Anexo I que o ativo aponta | Seção 4.6; independe dos tipos |

## 4.6 O Anexo I da CBS e o crédito da cooperativa

`Cad_Taxa_Depreciacao_Cbs` **não** é um tipo de depreciação: é a tabela do art. 48, § 1º, usada só em `Valor_Creditos_Depreciacao_Ativo` (§ 3º, I, "b"). O ativo aponta a sua linha (`ID_Taxa_Depreciacao_Cbs`), e o Motor aplica a regra provisória do documento 188 (C157, parte c): **taxa anual do Anexo I dividida por 12**, sobre o crédito de CBS do bem, até esgotá-lo, só para bens com nota de aquisição (Q247-7, aprovada). A unicidade da tabela (Q239-4) continua "não agora". Não consegui ler o texto do art. 394 nem do art. 48 do Decreto 12.955.

## 4.7 Acelerações incentivadas: usina de cana, química e outras

**Usina de cana (atividade rural).** O art. 260 da IN 1.700 permite depreciar integralmente no ano da aquisição os bens do imobilizado, exceto a terra nua, adquiridos por pessoa jurídica rural para uso na atividade rural. O tipo **INCENTIVADA_RURAL** (cálculo "integral no ano") cobre isso:

| O que a IN diz | Como o desenho cobre |
|---|---|
| A depreciação **normal** fica na escrituração comercial e o **complemento** é exclusão fiscal, controlada na Parte B (art. 260, §§ 1º e 2º) | O tipo gerencial lança; a incentivada guarda a quota integral sem lançar; a **diferença** por ativo é o saldo da Parte B (consulta; o contador lança) |
| Nos períodos seguintes, a depreciação normal contabilizada é **adicionada** e baixa o saldo (§ 3º) | A incentivada fica em zero e a gerencial continua; a diferença cai até zero |
| O total não passa do custo (§ 4º) | Cada tipo tem teto no custo |
| Na alienação o saldo é adicionado (§ 5º); se o bem sai da atividade rural, há adição (§§ 6º e 7º) | O ERP **mostra o saldo**; o contador lança. O bem fora da atividade rural fica fora pelo `Aplica` falso |

Segundo um comentário sobre decisão do CARF (Acórdão 1101-001.476), a agroindústria canavieira verticalizada tem o benefício para os bens usados na atividade rural (base: art. 6º da MP 2.159-70/2001); é **decisão isolada**. Por isso **o grupo de bem decide**: o tipo só vale para os grupos que a empresa ligar a ele.

**Indústria química.** A nota (2) do Anexo III diz que as máquinas, equipamentos e instalações industriais do anexo, **usados na indústria química**, são depreciados em **5 anos, à taxa de 20%**. É a **vida fiscal de 60 meses na linha do grupo** (FISCAL), sem estrutura nova, e só nos grupos de máquinas industriais; os grupos que não têm a regra ficam sem a linha. Se houver acelerada para a química, ela é um tipo ligado ao grupo que a permite (resposta C368 (b)).

**Outras acelerações incentivadas (você pediu para considerar).** O catálogo comporta qualquer uma sem mudar estrutura: o tipo diz como calcula (integral no ano, por turnos ou com multiplicador), em que **norma** se baseia (`Fundamento_Legal`) e de qual tipo parte (`ID_Tipo_Depreciacao_Base`); a **linha do grupo** diz a que bens vale e **por qual período de aquisição** (vigência da linha, pela data de início do ativo, 4.2). A IN 1.700 cita a "depreciação acelerada incentivada de que trata o art. 313 do RIR" (art. 200, § 4º; o texto do artigo não está na IN). **Nenhuma outra é carregada** até você ou o contador dizerem qual (C371).

**Limite desta leitura.** No PDF do DOU, o Anexo III (as taxas por NCM) e os Anexos I e II são imagens. O Anexo III chegou depois em texto e está no documento 248; os Anexos I e II da IN seguem não lidos.

## 4.8 Redução ao valor recuperável (CPC 01) e reavaliação

**O que a IN 1.700 diz (fiscal).**

| Assunto | Regra da IN | Efeito no ERP |
|---|---|---|
| Perda por **redução ao valor recuperável** | Só é reconhecida no lucro real **na alienação ou baixa** do ativo, e se não foi revertida; numa unidade geradora de caixa, proporcional ao valor contábil do ativo. A perda é **adicionada na Parte A** no período em que se reconhece e registrada na **Parte B** para a exclusão (art. 129); a **reversão não é computada** (art. 130) | O ERP registra o ajuste e mostra, por ativo, o saldo da Parte B; o contador lança |
| **Valor justo** de ativo (reavaliação) | O ganho não é tributado desde que o aumento fique em **subconta vinculada ao ativo**; é tributado à medida que o ativo se realiza (depreciação, alienação, baixa), e pode ser diferido (arts. 97 e 98). A perda segue a mesma subconta (arts. 102 e 103). Para bem depreciável, a baixa da subconta acompanha a depreciação (art. 89, § 2º; art. 98, § 4º) | O ajuste aponta o item da subconta que o dicionário já tem (`Mov_Item_Subconta`); a parte da quota que realiza a subconta é mostrada em consulta |

**O desenho:** uma entidade nova, **`Mov_Ativo_Ajuste_Valor`** (11 campos), registra cada ajuste do valor contábil do ativo:

| Campo | Regra |
|---|---|
| `ID_Ajuste_Valor` | Identificador |
| `ID_Ativo` | O ativo |
| `Tipo_Ajuste` | {reducao_valor_recuperavel, reversao_reducao_valor_recuperavel, reavaliacao_aumento, reavaliacao_reducao} |
| `Data_Ajuste` | Data do teste, do laudo ou da reavaliação |
| `Valor_Contabil_Antes` | O valor contábil na data (cálculo do Motor, que o usuário confere) |
| `Valor_Referencia` (opcional) | Valor recuperável (teste) ou valor justo (laudo), **como informado**; o ERP não calcula o valor recuperável nem o valor justo, como já é no teste do ágio |
| `Valor_Ajuste` | Valor do ajuste, com sinal |
| `ID_Lancamento` (opcional) | O lançamento, quando o tipo de ajuste lança |
| `ID_Item_Subconta` (opcional) | A subconta que evidencia o ajuste (reavaliação, art. 97) |
| `Codigo_Unidade_Geradora_Caixa` (opcional) | A unidade geradora de caixa do teste (art. 129, § 1º) |
| `Motivo` | Texto livre (indício da perda, laudo) |

**Efeito na depreciação:** nos tipos com `Considera_Ajuste_Valor` (a gerencial), a soma dos ajustes entra no saldo depreciável (R4) e a nova quota **vale daqui para frente** (R6); os tipos fiscais seguem o custo. A **reversão** não pode passar da perda acumulada ainda não revertida (aviso do Motor). O ajuste entra na base da aquisição; o rateio entre a aquisição e as manutenções capitalizadas fica para quando houver caso.

## 4.9 Pausas de depreciação

Uma entidade nova, **`Mov_Ativo_Depreciacao_Pausa`** (6 campos), registra os períodos em que o bem fica sem depreciar:

| Campo | Regra |
|---|---|
| `ID_Pausa` | Identificador |
| `ID_Ativo` | O ativo |
| `ID_Tipo_Depreciacao` (opcional) | O tipo afetado; **vazio é todos os tipos**. Pausa **todos os tipos, inclusive o fiscal** (C369: "sim, fica parada"); o campo só serve para pausar um tipo isolado, se um dia for preciso |
| `Data_Inicio_Pausa` | O primeiro mês sem quota |
| `Data_Fim_Pausa` (opcional) | O último mês sem quota; vazio é pausa em curso |
| `Motivo` | Texto livre (bem parado, em reforma, sem uso) |

Pela C369, a pausa vale também para a **fiscal**: sem quota fiscal no mês, o F120 não tem encargo de depreciação do bem naquele mês e, portanto, **não há crédito de PIS e Cofins dele** (leitura minha: o crédito acompanha a quota; o contador confirma). A regra é a R11: meses inteiros sem quota, vida útil que **não corre** (o fim da vida é adiado) e valor que **não se recupera** depois. O mês fechado não muda (R8): a pausa que começa em mês já fechado só vale dali em diante.

# 5. O que fica fora

| Assunto | Tratamento |
|---|---|
| Baixa do ativo (venda, sucata, perda), o mês da baixa e o saldo da Parte B na alienação | Documento próprio (Q247-8, aprovada); até lá, sem quota no mês da baixa |
| Depreciação por unidades produzidas (km ou horas) | Os contadores existem (`Mov_Ativo_Contador`); entra depois como valor novo de `Tipo_Calculo` (Q247-2, aprovada) |
| Cálculo do valor recuperável e do valor justo | O ERP só registra o valor informado (Q247-12) |
| Arrendamento e direito de uso (CPC 06) | Sem desenho |
| Tabela completa da Receita (Anexo III da IN 1.700) | Resolvida no documento 248 (R9, R12 a R15) |
| Bem de pequeno valor | Direto à despesa pela Destinação na compra (art. 120: R$ 1.200,00 por unidade ou vida útil de até 1 ano, salvo conjunto de bens; Q247-6, aprovada); o limite é parâmetro por empresa com vigência |
| Rateio de ajuste de valor entre a aquisição e as manutenções capitalizadas | Para quando houver caso |

# 6. Perguntas

**Aprovadas por você em 18/11/2026 ("seguir com as recomendações", D-N634):** Q247-1 (4 tipos na carga inicial; só o gerencial lança), Q247-2 (linear e com turnos, sem unidades produzidas), Q247-3 (cota cheia no início e sem quota na baixa; o seu C365 confirma a cota cheia e o início pelo cadastro do ativo), Q247-4 (entidades e campos, agora na forma da seção 9), Q247-5 (contas pelo Motor de Regras), Q247-6 (bem de pequeno valor pela Destinação, limite de R$ 1.200,00), Q247-7 (crédito da cooperativa pelo Anexo I, taxa dividida por 12), Q247-8 (baixa em documento próprio), Q247-9 (quota pendente sem contas) e Q247-10 ((a) química e usina como na seção 4.7; (b) respondida na C368; (c) o Anexo III chegou em texto: documento 248).

**Aprovadas por você em 18/11/2026 ("seguir com as recomendações", D-N635):** Q247-11 (entidade `Mov_Ativo_Ajuste_Valor`, 11 campos, e o campo `Considera_Ajuste_Valor` do tipo), Q247-12 (o ERP só registra o valor recuperável ou o valor justo informado, sem calcular), Q247-13 (pausas de depreciação, `Mov_Ativo_Depreciacao_Pausa`, 6 campos, tipo opcional) e Q247-14 (outras acelerações incentivadas como tipos novos do catálogo, sem carregar nenhuma).

**Novas, para você:** nenhuma neste documento. O Anexo III chegou em 18/11/2026 (Q247-10 c respondida) e o desenho dele está no documento 248, já aprovado (Q248-1 a Q248-6).

# 7. Para o contador (documento 188)

**Respondidas por você em 18/11/2026**, a confirmar pelo contador (documento 188): **C365** (cota cheia no mês, início pelo cadastro do ativo), **C366** (F120 pelo fiscal, inclusive por turnos), **C367** ("sim, correto"), **C368** (grupo de bem; F120 pelo fiscal; cota integral a partir do mês de início; pausas), **C369** ("sim fica parada": a fiscal também pausa), **C370** ("sim correto": tratamento do ajuste de valor) e **C371** ("deixe preparado para receber outras, mas não precisa preencher agora").

Duas leituras minhas a conferir: (a) na C369 li "sim" como a pausa valer também para a fiscal e, por isso, sem crédito de PIS e Cofins do bem no mês parado; (b) na C370 "sim correto" confirma o tratamento do documento, mas **não respondeu** se a Mlegate usa reavaliação e em quais grupos: o ERP fica preparado para os dois casos e nenhum grupo é ligado até você dizer.

# 8. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N631 a D-N633 | Já registradas: desenhar a depreciação, n tipos com contabilização por tipo e a acelerada (IN 1.700) | 18/11/2026 |
| D-N634 | Aprovação das **Q247-1 a Q247-10**; respostas às **C365 a C368**; parâmetros **por grupo de bem** (inclusive o fiscal principal); **pausas de depreciação**; **considerar** redução ao valor recuperável, reavaliação e outras acelerações incentivadas | "Q247-1 a Q247-10 Seguir com as Recomendações", C365 a C368 e "considerar Redução ao valor recuperável (CPC 01) e reavaliação e Outras acelerações incentivadas", 18/11/2026 |

| D-N635 | Aprovação das **Q247-11 a Q247-14**; respostas às **C369 a C371** (pausa vale também para a fiscal; tratamento do ajuste de valor confirmado; catálogo preparado para outras acelerações, sem carga) | "Q247- 11 a Q247-14 Seguir com as recomendações", C369 a C371, 18/11/2026 |

# 9. O que muda no "consolidar"

| Medida | Revisão 54 | Depois (aplicado na revisão 55, documento 249; com o 248: 1.249 entidades e 14.529 campos) |
|---|---|---|
| Entidades | 1.243 | **1.248** (+5: catálogo de tipos, parâmetros por grupo, parâmetros por ativo, ajuste de valor e pausas) |
| Campos | 14.460 | **14.511** (+48 nas entidades novas e +3 no ativo; `Tipo_Depreciacao` só muda de tipo) |
| Comentários do DDL | 12.200 | a conferir no ensaio de consolidação |

Muda também o texto de `Mov_Ativo_Depreciacao.Tipo_Depreciacao` na Fase 0 ("as três depreciações simultâneas... cada uma com seu próprio lançamento"), que passa a dizer que o tipo vem do catálogo e que o lançamento é parâmetro do tipo. O documento 248 acrescenta mais **1 entidade e 18 campos** (1.249 e 14.529 no total). **Está tudo aprovado neste documento:** o "consolidar" aplica as 5 entidades e os 51 campos. O que não entra aqui é a carga das vidas úteis (documento 248) e de outras acelerações incentivadas (nenhuma carregada).

# 10. Fontes e limites

**Fonte oficial lida (IN RFB 1.700/2017, PDF do Diário Oficial que você enviou):** art. 120 (bem de pequeno valor); arts. 121 a 124 (depreciação, bens depreciáveis, quota mensal, taxa e diferença na Parte B); arts. 89, 97, 98, 102 e 103 (subcontas e valor justo); arts. 129 e 130 (teste de recuperabilidade); art. 200, § 4º; art. 260 e §§ 1º a 8º, arts. 266 e 268 (atividade rural) e as notas do Anexo III. **Não li:** as tabelas dos Anexos I e II da IN (imagens no PDF; o Anexo III chegou em texto e está no documento 248), o texto do RIR/2018 (arts. 313 e 317 a 324), o CPC 01 e o CPC 27 (a descrição do impairment e da reavaliação segue o que a IN fiscal pressupõe e o que o dicionário já tem para o ágio) e o art. 6º da MP 2.159-70/2001.

**Fontes secundárias:** o boletim da Lefisc de janeiro de 2025 e o artigo da Tributo Devido sobre a Solução de Consulta Cosit 152/2019 (coeficientes de turnos, bem usado e diferença no Lalur), e um comentário da Tributo Devido sobre o Acórdão CARF 1101-001.476 (agroindústria canavieira; decisão isolada). O art. 394 do Decreto 12.955 não pôde ser lido. A estrutura só guarda vidas úteis, percentuais e coeficientes em campos, e não no código, para o contador e a empresa ajustarem.
