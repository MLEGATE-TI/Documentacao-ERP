# Desenho do Bloco 1 de combustíveis e usina: livro de movimentação, bombas, bicos, leituras e produção da usina (registros 1300 a 1391 e C171) — Documento 218

*Responde à Q167-6 ("Fica para depois, em bloco próprio", 05/11/2026) e à D-N482, que reservou para este documento o C171 (`Mov_Nota_Fiscal_Entrada_Item_Tanque`). Você escolheu desenhar o Bloco 1 em 12/11/2026 ("próximo passo"). Parte do texto completo dos registros 1300 a 1391 e do C171 no Guia Prático EFD-ICMS/IPI 3.2.4 (atualização de 30/07/2026), que li inteiro, e de pesquisa sobre o Ajuste SINIEF 14/2025. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar". **Versão 2 (12/11/2026)**: acrescenta a seção 14 (cadeia usina, distribuidor, posto e grande consumidor; venda por nota ou por cupom) e incorpora a Cartilha do Posto Revendedor da ANP (7ª edição, maio de 2026) que você enviou. **Versão 2.1 (12/11/2026)**: incorpora o texto da Resolução ANP 884/2022 com o Anexo, que você pediu para eu ler (seções 14.5 a 14.7). **Versão 2.2 (12/11/2026)**: você enviou a Resolução 884 como saiu no Diário Oficial e a página do DOU com a Solução de Consulta Cosit nº 223/2023; o texto oficial **confere com as cópias que eu tinha lido** (14.5 e 14.7) e a solução de consulta entra na seção 14.8. Nenhum campo muda e nenhum aviso entra; só o texto do A22 ganharia uma citação, se você aprovar a Q218-18.*

> **Situação em 16/11/2026:** aprovado nas Q218-1 a Q218-17 (D-N581) e **consolidado na revisão 44** do dicionário (documento 219, D-N585). Ficam abertas a Q218-18, a Q218-8 (só o Ajuste SINIEF 14/2025 e o 01/92) e as perguntas à equipe (Q218-E1 a E9).

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

O Bloco 1 de combustíveis é o **Livro de Movimentação de Combustíveis (LMC) dentro da EFD-ICMS/IPI**: o posto informa, dia a dia e produto a produto, quanto tinha, quanto recebeu, quanto vendeu pelos contadores das bombas e quanto mediu no tanque no fim do dia. A diferença entre o que deveria haver (estoque escritural) e o que se mediu é a perda ou o ganho do dia. A usina de açúcar e álcool tem um registro parecido, mais simples: a produção e o estoque do dia por produto (1390 e 1391).

Antes de desenhar, conferi o que o dicionário já tem. **Tem pouco, mas o essencial para ligar tudo**: a nota de saída já leva o bico, a bomba, o tanque e o encerrante inicial e final de cada abastecimento (campos `Combustivel_*` do item); o catálogo de códigos estaduais já tem a tabela 5.8 da usina (`cod_prod_usinas`, 39 linhas); `Cad_Local_Estoque` guarda o estoque por local; o produto já liga ao código da ANP; e o desenho do C171 está pronto desde o documento 175 (4 campos), mas **nunca entrou** por causa da referência ao tanque. Falta tudo o que é do posto por natureza: o cadastro do tanque, da bomba, do lacre e do bico, a medição diária por tanque, a leitura diária por bico (com intervenção do técnico) e a produção diária da usina.

O desenho acrescenta **9 entidades novas (107 campos)**, **2 valores novos** em `modulo_fiscal_opcional` (a habilitação por empresa, nenhum ligado) e nenhuma alteração em entidade existente. O 1300, o 1390 e todos os totais **não viram entidade**: saem somados dos registros de baixo.

| Peça | O que o Guia pede | O que o dicionário já tinha | O que este documento acrescenta |
|---|---|---|---|
| **Tanque** (1310, 1370, C171) | Número, capacidade, estoque do dia, medição física | Só o código do tanque na nota de saída | `Cad_Lmc_Tanque` e `Mov_Lmc_Tanque_Dia` |
| **Bomba, lacre e bico** (1350, 1360, 1370) | Série, fabricante, modelo, tipo de medição; lacres; bico ligado a tanque e produto | Só o código do bico e da bomba na nota de saída | `Cad_Lmc_Bomba`, `Cad_Lmc_Bomba_Lacre` e `Cad_Lmc_Bico` |
| **Venda por bico** (1320) | Leitura inicial e final do contador, aferição, intervenção do técnico | O encerrante de cada item da nota de saída | `Mov_Lmc_Bico_Leitura` e `Mov_Lmc_Bomba_Intervencao` |
| **Entrada por tanque** (C171) | Em que tanque entrou cada item da nota de entrada e quantos litros | Nada (o desenho do documento 175 não entrou) | `Mov_Nota_Fiscal_Entrada_Item_Tanque`, já com referência ao tanque |
| **Usina** (1390, 1391) | Produção, estoque, perdas, mel residual e resíduos por produto e por dia | A tabela 5.8 em `Cad_Efd_Codigo_Estadual` | `Mov_Usina_Producao_Dia` |
| **Habilitação** (0000.IND_COMB e IND_USINA) | Só quem tem posto ou usina informa | `modulo_fiscal_opcional` (valores `efd_*`, `ecd_*` e `ipi_*`; o `efd_combustivel_c165` cobre só o C165) | `efd_combustivel_lmc_1300` e `efd_usina_1390` |

**Nove achados que você precisa ler.**

1. **Há uma norma nova que pode ter tornado o bloco obrigatório.** O **Ajuste SINIEF 14/2025** (04/07/2025, publicado em 08/07/2025) acrescentaria o item VIII, "livro de movimentação de combustíveis", ao § 3º da cláusula primeira do Ajuste SINIEF 2/2009, com efeitos a partir de **01/09/2025**. **Li o texto só em site não oficial** (normasbrasil) e em notas de secretarias estaduais; não li o ato no CONFAZ nem no Diário Oficial. Pelas notas do RS e do ES, a EFD passa a substituir o LMC para fins estaduais, **mas a obrigação junto à ANP continua**. Pergunto ao contador (C335) quais UF exigem e desde quando.
2. **A norma do LMC da ANP mudou: é a Resolução ANP nº 884/2022, lida no Diário Oficial.** O Guia cita a Portaria DNC nº 26/1992, que a 884 revogou (art. 7º). Li o **texto completo, com o Anexo**, primeiro em duas cópias de sites não oficiais (LegisWeb e Brasil Postos) e depois no texto do **Diário Oficial da União** (edição 171, seção 1, página 62, de 08/09/2022) que você enviou, impresso do site da Imprensa Nacional (a página ressalva que "não substitui o publicado na versão certificada"); o texto oficial **confere com as cópias**. A cartilha da ANP (maio de 2026), o relatório da Consulta Pública 04/2022 e a Agenda Regulatória 4.22 que você enviou confirmam o número. O LMC é do **revendedor varejista**, diário, por produto; o limite de **0,6%** é sobre o **estoque físico** e se mede pelo **campo 8 do Anexo (perdas e ganhos, um saldo líquido do produto)**; as justificativas vão em Observações. **Nada foi preenchido de memória.** O desenho traz o limite como **campo que o posto preenche** (`Limite_Variacao_Percentual`) e o aviso A22, sem valor escondido; o que o texto não diz (o estoque de abertura ou o de fechamento) vai ao contador (C336, C349).
3. **O dia é a unidade, e o tanque é a menor peça.** O 1300 (por produto e por dia) é a **soma** dos 1310 (por tanque), e o Guia exige que a soma do estoque físico dos tanques seja igual ao do 1300. Por isso **só o tanque é gravado por dia**; o produto é somado na geração. Isso evita que os dois números divirjam.
4. **O volume de vendas do livro vem do contador da bomba, não da nota.** O 1320 usa a leitura do encerrante no começo e no fim do dia, menos a aferição. A nota de saída leva o encerrante de cada abastecimento, então o ERP **sugere** a leitura a partir das notas (primeiro encerrante inicial e último final do dia), mas quem vale é a leitura informada. A diferença entre a venda por nota e a venda por contador fica como aviso.
5. **A intervenção do técnico quebra o dia em trechos.** Para cada intervenção na bomba, o 1320 abre um registro novo, com os dados da intervenção, até a próxima intervenção ou o fim do dia. O contador que passa do valor máximo também gera **dois** registros. Guardei **uma linha por trecho** (`Sequencia_Dia`), e a divisão pelo valor máximo é feita na geração.
6. **Tanques interligados viram um só.** Quando não dá para saber qual tanque alimentou um bico, o Guia manda somar os tanques e informar um único 1310 com o número de um deles, o mesmo que o 1370 cita. O cadastro do tanque ganha o campo do **tanque representante**.
7. **O Guia tem três pontos que se contradizem ou ficam sem fórmula.** (a) O campo `MOT_INTERV` do 1320 é descrito como "nome da empresa responsável pela intervenção", que parece cópia do campo seguinte; (b) o 1391 aparece como ocorrência 1:1 numa tabela e 1:N em outra; (c) o Guia não dá a fórmula da perda e do ganho, nem diz como se calcula o estoque do início do dia. Escrevi a leitura mais natural, **marcada como minha**, e levei ao contador (C337, C338, C342, C348).
8. **O cupom fiscal já é documento de saída no dicionário, e o distribuidor já tem papel; faltavam os cruzamentos.** O cupom (SAT, CF-e-ECF e ECF) fica em `Mov_Nota_Fiscal_Saida` com itens, como a NF-e e a NFC-e; por isso a comparação entre o contador da bomba e as vendas (A11) e a leitura sugerida passam a valer para qualquer canal. O distribuidor (compra da usina, revende ao posto ou ao grande consumidor) se declara pela autorização ANP que o dicionário já tem; a seção 14 acrescenta **seis avisos** e **nenhuma entidade nova** para ele (A22 a A27).
9. **O Anexo da 884 pede três coisas que a primeira versão não tinha** (seção 14.7): a **transferência de produto entre tanques** (sem ela o escritural por tanque fica errado), na **troca de encerrante** o volume do substituído, o do novo e o número do relatório de manutenção, e o **valor das vendas em reais** (campo 10), que o EFD não tem. Proponho **5 campos novos** (Q218-15 e Q218-16) e a folha do LMC como **relatório**, sem entidade (Q218-17).

# 2. Regras que segui

Valem as dos documentos 156, 157, 150 e 175 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória com `Situacao_Dado = provisorio` até o contador validar; o ERP avisa e nunca bloqueia, D-N284; habilitação por empresa sem nenhum módulo ligado por padrão; "O ERP só registra"; nomes em português com sublinhado). Mais estas:

1. **Só se grava o que a pessoa ou a bomba informa.** O que é soma ou diferença (1300, volume disponível, volume de vendas por trecho) sai na geração. A exceção são os números do **fechamento do dia por tanque**, que se gravam no momento em que o dia é fechado, porque o livro fechado não pode mudar sozinho se uma nota de entrada for corrigida depois (D-N284: o ERP avisa).
2. **Uma linha por trecho, não por registro.** O 1320 pode sair em dois registros (contador que zera); no dicionário há uma linha só, e a geração divide.
3. **O tanque tem identidade própria e vigência.** O número do tanque (até 3 posições) é o que a nota de saída, o 1310, o 1370 e o C171 citam. O cadastro é versionado: o tanque pode mudar de produto sem perder o histórico.
4. **O que a nota já leva não vira campo novo.** Bico, bomba, tanque e encerrante do item da nota de saída ficam como estão; o ERP só confere com o cadastro.
5. **Produto da usina pela tabela 5.8 que já existe.** O 1390 não tem entidade: é a lista dos produtos que têm 1391 no período.
6. **Uma leitura minha é sempre dita como minha** e vai ao contador.
7. **Só desenho o que o cliente usa** (D-N68). Não sei se a Mlegate ou algum cliente tem posto ou usina; você pediu o desenho, então ele sai, **toda a habilitação desligada** e a pergunta ao seu time na Q218-E1.

# 3. O que os textos pedem

**Quem informa.** O 1300 é para o **comércio varejista de combustíveis** (posto revendedor), com `0000.IND_COMB = S` (movimentação e/ou estoque no período). O 1390 e o 1391 são das **usinas de açúcar e álcool** (`0000.IND_USINA = S`) e só valem para períodos de apuração **posteriores a julho de 2012**. O 1350, o 1360 e o 1370 são obrigatórios se existir 1300. O GNV não tem previsão no livro.

**1300, movimentação diária de combustíveis.** Um registro por produto (`COD_ITEM`, do 0200) e por data de fechamento, "independentemente de ocorrerem intervenções"; não pode haver dois com o mesmo produto e a mesma data. Campos: estoque no início do dia (`ESTQ_ABERT`, informado "mesmo que tenha ocorrido intervenção posterior"), volume recebido (`VOL_ENTR`, dos C171), volume disponível (04 + 05), volume total das saídas (soma dos 1320), estoque escritural (06 − 07), perda, ganho e estoque de fechamento (`FECH_FISICO`). Tudo em litros, três decimais.

**1310, por tanque.** Mesmos campos do 1300, mais o número do tanque (`NUM_TANQUE`, 3 posições) e a capacidade (`CAP_TANQUE`, até 6 dígitos, sem decimais). Não pode haver dois com o mesmo número de tanque. O volume recebido deve ser o dos C171 do dia, por tanque, e **a soma do estoque físico dos 1310 tem de ser igual ao estoque físico do 1300**. Tanques **interligados** ou que passam por um filtro único somam-se como se fossem um, e `NUM_TANQUE` leva o número de um deles, o mesmo que o 1370 referencia.

**1320, volume de vendas.** Um registro por bico; sem intervenção, os campos de intervenção (`NR_INTERV`, `MOT_INTERV`, `NOM_INTERV`, `CNPJ_INTERV`, `CPF_INTERV`) ficam vazios. A cada intervenção na bomba abre-se um novo registro "com os valores totalizados desde a intervenção até uma próxima intervenção ou o fim do dia". O contador que atinge o valor máximo gera dois registros: o primeiro vai da leitura inicial ao máximo; o segundo começa em **zero** e vai à leitura final. A leitura final menos (leitura inicial mais aferição) dá o volume de vendas do bico (`VOL_VENDAS`).

**1350, 1360 e 1370.** O 1350 lista as bombas "pertencentes ao varejista": série, fabricante (até 60), modelo e tipo de medição (0 analógico, 1 digital). O 1360 traz um registro para cada lacre existente na bomba (número até 20 e data de aplicação). O 1370 traz os bicos da bomba: número (3 posições), produto e tanque. O tanque que **não está ligado a bico** (só reservatório) entra com número de bico **990 em diante**.

**1390 e 1391, usina.** O 1390 dá o produto (`COD_PROD`) pela tabela 5.8 da UF do declarante, ou pela genérica se a UF não tiver. O 1391, filho do 1390, detalha o dia: data, insumo esmagado (toneladas), estoque inicial, quantidade produzida, entrada por transformação (anidro de hidratado ou o contrário), outras entradas, perda (evaporação em litros, quebra de peso em kg), consumo, saída para transformação, saídas, estoque final, mel residual (estoque inicial, produção, utilização, e o álcool ou açúcar produzido do mel), observação, insumo (`COD_ITEM`), tipo de resíduo (01 bagaço, 02 DDG, 03 WDG, 04 DDG + WDG) e as quantidades de resíduo. Não pode haver dois 1391 com o mesmo insumo na mesma data. Álcool em litros, açúcar em quilogramas.

**C171, armazenamento de combustíveis.** Só na **entrada** (códigos 01 e 55), para as empresas do varejo de combustíveis: o tanque e a quantidade armazenada (maior que zero), por item, conforme o LMC (Ajuste SINIEF 01/92). Um item pode ir a mais de um tanque, mas **não pode repetir o mesmo tanque no mesmo documento**.

**O que a norma de fora diz.** Fonte secundária, não lida no original: o Ajuste SINIEF 14/2025 incluiria o LMC entre as obrigações da EFD a partir de 01/09/2025. O LMC foi instituído pela **Resolução ANP nº 884/2022**, lida no texto do **Diário Oficial da União** (edição 171, seção 1, página 62, de 08/09/2022) que você enviou, impresso do site da Imprensa Nacional (a página ressalva que "não substitui o publicado na versão certificada"), depois de lida em duas cópias não oficiais; o texto confere com a cartilha da ANP (maio de 2026). O que a 884 pede está na seção 14.5 e o Anexo, campo a campo, na 14.7; a Solução de Consulta Cosit nº 223/2023 sobre as perdas de até 0,6%, na 14.8.

# 4. O que o dicionário já tem e o que falta

| Peça | O que faz | O que falta |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item.Combustivel_Numero_Bico`, `_Numero_Bomba`, `_Numero_Tanque`, `_Encerrante_Inicial` e `_Encerrante_Final` | O encerrante de cada abastecimento, como a NF-e exige | Ligar o número ao cadastro do tanque, da bomba e do bico; nada muda no item |
| `Cad_Local_Estoque` e `Mov_Estoque_Movimento_Item` | Estoque por local, com origem e destino | Ligar o tanque a um local (opcional), para comparar o escritural do livro com o saldo do estoque |
| `Mov_Inventario` | Inventário do período | Nada: o primeiro dia do livro pode partir dele, informado à mão |
| `Cad_Produto_Anp` e `Cad_Produto_Servico_Dados_Produto.ID_Produto_Anp` | O produto aponta para o código da ANP | Nada: é daqui que o ERP descobre se o produto é combustível |
| `Cad_Efd_Codigo_Estadual` (tabela `cod_prod_usinas`, 39 linhas) | O `COD_PROD` do 1390 por UF e a genérica | Nada: o 1391 aponta para esta tabela |
| `Mov_Nota_Fiscal_Entrada` e `Mov_Nota_Fiscal_Entrada_Item` | A nota de entrada, com `Data_Entrada` e a quantidade do item | O tanque de cada item (C171) |
| `Cad_Empresa_Modulo_Opcional` (domínio `modulo_fiscal_opcional`) | Habilita por empresa e por filial cada bloco opcional | Dois valores novos (seção 9) |
| `Cad_Equipamento_Fiscal` | ECF, SAT, MFE e terminal de NFC-e | Nada: não serve à bomba (exige modelo de documento fiscal) |
| `Mov_Ordem_Producao` e filhos | Produção com fases, itens e apontamentos | Nada para a usina: não tem esmagamento, mel residual, anidro e hidratado nem resíduos (Q218-E4) |

# 5. Cadastros do posto

Os quatro cadastros descrevem a **ilha de abastecimento**: o tanque guarda o combustível, a bomba tem bicos, cada bico puxa de um tanque e a bomba leva lacres. Ficam na Contabilidade & Fiscal, ao lado de `Cad_Equipamento_Fiscal`. O número do tanque e o do bico são os que a nota de saída, o 1310, o 1320 e o 1370 citam.

## 5.1 `Cad_Lmc_Tanque`

*Tipo: cadastro do usuário (sem carga). Mestre: não. Vigência: sim. Campos: 14.*

O tanque tem número (até 3 posições), capacidade e o combustível que guarda. O produto está no tanque, e **não no bico**: o produto do bico é o do tanque a que ele está ligado, e o 1370 repete esse valor na geração. Quando o posto troca o produto de um tanque, nasce uma versão nova; as leituras antigas continuam apontando para o mesmo tanque.

**Tanques interligados** (1310, observação do Guia): o campo `ID_Lmc_Tanque_Representante` aponta o tanque que representa o grupo. Vazio, o tanque vale por si. Na geração, os tanques do grupo se somam em um único 1310 com o número do representante, e o 1370 cita esse número.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Tanque` | identificador | --- |
| `ID_Lmc_Tanque_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Lmc_Tanque_Versao). ID_Lmc_Tanque é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Filial` | referência (Cad_Filial) --- identidade | O posto (estabelecimento) a que o tanque pertence. |
| `Numero_Tanque` | código (até 3) --- identidade | NUM_TANQUE. O número que a nota de saída (`Combustivel_Numero_Tanque`), o 1310, o 1370 e o C171 usam. Único por filial. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico) | O combustível que o tanque guarda (vira o COD_ITEM do 1300 e do 1370). O produto tem de ter `ID_Produto_Anp`; senão o ERP avisa. |
| `ID_Local_Estoque` | referência (Cad_Local_Estoque), opcional | O local de estoque que representa o tanque. Preenchido, o ERP compara o estoque escritural do livro com o saldo do local no fim do dia e só avisa. |
| `Capacidade_Litros` | número | CAP_TANQUE: capacidade de armazenagem em litros (até 6 dígitos, sem decimais). No grupo de tanques interligados, a capacidade do 1310 é a soma dos tanques do grupo (leitura minha, C340). |
| `ID_Lmc_Tanque_Representante` | referência (Cad_Lmc_Tanque), opcional | Só nos tanques interligados: o tanque cujo número representa o grupo no 1310 e no 1370. Vazio quando o tanque vale por si. |
| `Data_Inicio_Uso` | data | Quando o tanque entrou em operação no posto. |
| `Data_Cessacao` | data, opcional | Quando saiu de uso. Depois dela, o ERP não espera medição diária. |
| `Limite_Variacao_Percentual` | número, opcional | O limite de variação do estoque físico, em percentual, acima do qual o ERP avisa (A22). **O ERP não preenche valor**: a Resolução 884 (art. 5º) fala em 0,6% do **estoque físico** e mede a variação pelo campo 8, **por produto**; o ERP compara o saldo líquido do produto com esse percentual do estoque físico de fechamento, **leitura minha** (C349). O limite fica no tanque porque o cadastro é do tanque; o do produto é o menor valor preenchido. Vazio: sem aviso. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada (por exemplo, troca do produto do tanque). |

## 5.2 `Cad_Lmc_Bomba`

*Tipo: cadastro do usuário (sem carga). Mestre: não. Vigência: sim. Campos: 13.*

A bomba medidora do posto, como o 1350 pede. Não uso `Cad_Equipamento_Fiscal` porque ele exige modelo de documento fiscal (ECF, SAT, MFE, NFC-e), que a bomba não tem.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Bomba` | identificador | --- |
| `ID_Lmc_Bomba_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Lmc_Bomba_Versao). ID_Lmc_Bomba é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Filial` | referência (Cad_Filial) --- identidade | O posto a que a bomba pertence. |
| `Numero_Serie` | texto --- identidade | SERIE: número de série da bomba. O Guia não fixa o tamanho. |
| `Numero_Bomba` | código (até 3), opcional | O número da bomba no posto, o que a nota de saída leva em `Combustivel_Numero_Bomba` (nBomba). Serve para o ERP conferir a nota com o cadastro; o 1350 não o usa. A relação entre este número e a série vai ao contador (C341). |
| `Fabricante` | texto (até 60) | FABRICANTE. |
| `Modelo` | texto | MODELO. O Guia não fixa o tamanho. |
| `Tipo_Medicao` | enumeração {analogica, digital} | TIPO_MEDICAO: 0 analógico, 1 digital. |
| `Data_Inicio_Uso` | data | Quando a bomba entrou em operação. |
| `Data_Retirada` | data, opcional | Quando saiu do posto. Depois dela, a bomba deixa de sair no 1350. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 5.3 `Cad_Lmc_Bomba_Lacre`

*Tipo: fato com datas (sem vigência). Mestre: não. Vigência: não. Campos: 5.*

O 1360 pede "um registro para cada lacre existente na bomba": número e data de aplicação. A data de remoção é necessária para saber quais lacres existiam em cada período.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Bomba_Lacre` | identificador | --- |
| `ID_Lmc_Bomba` | referência (Cad_Lmc_Bomba) --- identidade | A bomba lacrada. |
| `Numero_Lacre` | código (até 20) --- identidade | NUM_LACRE. |
| `Data_Aplicacao` | data | DT_APLICACAO: quando o lacre foi aplicado. |
| `Data_Remocao` | data, opcional | Quando o lacre foi retirado. Vazia enquanto o lacre existe. O Guia não trata a remoção; leitura minha: o 1360 sai para o lacre que existiu em algum dia do período (C345). |

## 5.4 `Cad_Lmc_Bico`

*Tipo: cadastro do usuário (sem carga). Mestre: não. Vigência: sim. Campos: 9.*

O bico liga uma bomba a um tanque (1370). O número do bico (até 3 posições) é o que o 1320 e a nota de saída citam. O `Valor_Maximo_Contador` é o valor em que o contador do bico volta a zero; sem ele o ERP não sabe dividir o 1320 quando o contador passa do máximo.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Bico` | identificador | --- |
| `ID_Lmc_Bico_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Lmc_Bico_Versao). ID_Lmc_Bico é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Lmc_Bomba` | referência (Cad_Lmc_Bomba) --- identidade | A bomba a que o bico está ligado (pai do 1370). |
| `Numero_Bico` | número --- identidade | NUM_BICO (3 posições). O ERP o trata como único por filial, porque o 1320 só cita o número do bico (leitura minha, C341). Os números de 990 em diante são reservados ao tanque sem bico (seção 7). |
| `ID_Lmc_Tanque` | referência (Cad_Lmc_Tanque) | O tanque que abastece o bico. O produto do bico é o do tanque. |
| `Valor_Maximo_Contador` | número, opcional | A maior leitura que o contador do bico mostra antes de voltar a zero. Vazio: o ERP não divide o 1320 e avisa quando a leitura final é menor que a inicial. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada (por exemplo, bico ligado a outro tanque). |

# 6. Movimento diário do posto

## 6.1 `Mov_Lmc_Tanque_Dia`

*Tipo: fato diário. Mestre: não. Vigência: não. Campos: 17.*

Uma linha por tanque e por dia. É a **única** peça do livro que se grava por dia. O que a pessoa (ou a automação da pista) informa é o **estoque físico de fechamento** medido no tanque (e o de abertura, só no primeiro dia). O resto, no dia aberto, o ERP calcula na tela e na geração; **no fechamento do dia, grava-se o resultado**, para o livro fechado não mudar sozinho.

*Leitura minha, que o contador confirma (C337, C338):* o estoque do início do dia é o físico do fechamento do dia anterior; a perda é o escritural menos o físico quando o físico é menor, e o ganho é o físico menos o escritural quando o físico é maior. O Guia não dá essas duas fórmulas.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Tanque_Dia` | identificador | --- |
| `ID_Lmc_Tanque` | referência (Cad_Lmc_Tanque) --- identidade | O tanque. |
| `Data_Fechamento` | data --- identidade | DT_FECH: a data do fechamento da movimentação. Tem de estar entre `DT_INI` e `DT_FIN` do 0000 do período em que sai. |
| `Volume_Estoque_Abertura` | número | ESTQ_ABERT: estoque no início do dia, em litros (3 decimais), "mesmo que tenha ocorrido intervenção posterior". Herdado do físico do dia anterior; digitado no primeiro dia (pode partir do inventário) ou numa correção. |
| `Volume_Fechamento_Fisico` | número | FECH_FISICO: o volume medido no tanque no fim do dia, em litros. Informado. |
| `Origem_Dado` | enumeração {digitacao, automacao_pista, importacao} | De onde veio a medição. |
| `Volume_Entrada` | número, opcional | VOL_ENTR. Calculado: soma dos C171 do tanque cuja nota de entrada tem `Data_Entrada` neste dia. Gravado só no fechamento do dia. |
| `Volume_Saidas` | número, opcional | VOL_SAIDAS. Calculado: soma dos volumes de venda dos bicos do tanque no dia (1320). Gravado só no fechamento do dia. |
| `Volume_Transferencia_Recebida` | número, opcional | Litros que o tanque recebeu de **outro tanque do mesmo posto** no dia, sem passar pela bomba. É o item que o Anexo da 884 manda anotar em Observações. Informado; **não é entrada nem venda** (seção 14.7, Q218-15). |
| `Volume_Transferencia_Enviada` | número, opcional | Litros que o tanque mandou a outro tanque do posto no dia. Informado (Q218-15). |
| `Volume_Estoque_Escritural` | número, opcional | ESTQ_ESCR. Calculado: abertura mais entrada mais transferência recebida menos transferência enviada menos saídas (leitura minha; o Anexo da 884 define o escritural como o volume disponível menos as vendas e não trata a transferência). Gravado só no fechamento do dia. |
| `Volume_Perda` | número, opcional | VAL_AJ_PERDA. Calculado (leitura minha): escritural menos físico, quando o físico é menor; senão zero. Gravado só no fechamento do dia. |
| `Volume_Ganho` | número, opcional | VAL_AJ_GANHO. Calculado (leitura minha): físico menos escritural, quando o físico é maior; senão zero. Gravado só no fechamento do dia. |
| `Situacao` | enumeração {em_elaboracao, fechado} | `fechado` grava os cinco valores calculados. Mudança posterior de nota de entrada ou de leitura de bico num dia fechado: o ERP avisa e não recalcula sozinho. |
| `ID_Usuario_Fechamento` | referência (Cad_Usuario), opcional | Quem fechou o dia. |
| `Data_Hora_Fechamento` | data/hora, opcional | Quando fechou. |
| `Observacao` | texto, opcional | Texto livre do operador. É o campo "13) Observações" do LMC da ANP: a variação acima do limite do tanque (A22) deve vir justificada aqui. |

O volume disponível (abertura mais entrada) **não se grava**: é soma. O estoque do dia 1300 (por produto) também não: é a soma das linhas dos tanques do produto naquele dia.

## 6.2 `Mov_Lmc_Bomba_Intervencao`

*Tipo: fato. Mestre: não. Vigência: não. Campos: 12.*

A intervenção do técnico credenciado numa bomba (manutenção, troca de peça, lacre rompido). Ela vale para **todos os bicos da bomba**, por isso fica na bomba e as leituras dos bicos apontam para ela. O Guia pede o número da intervenção (do órgão competente ou, na falta, sequencial do declarante), o motivo, o nome do técnico, o CNPJ da empresa de manutenção e o CPF do técnico, estes dois quando houver.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Bomba_Intervencao` | identificador | --- |
| `ID_Lmc_Bomba` | referência (Cad_Lmc_Bomba) --- identidade | A bomba em que houve a intervenção. |
| `Data_Hora_Intervencao` | data/hora --- identidade | Quando a intervenção começou: separa o trecho antes do trecho depois no dia. |
| `Numero_Intervencao` | número | NR_INTERV: número dado pelo órgão competente ou, na falta, um sequencial do posto (leitura minha, C342). |
| `Motivo_Intervencao` | texto (até 50) | MOT_INTERV. O Guia descreve este campo como "nome da empresa responsável", o que parece cópia do campo seguinte (C342). |
| `Nome_Interventor` | texto (até 30) | NOM_INTERV: nome do técnico autorizado pelo INMETRO (pelas unidades estaduais) para manter bombas medidoras. |
| `Cnpj_Empresa_Interventora` | código (14), opcional | CNPJ_INTERV: a empresa do contrato de manutenção, quando houver. |
| `Cpf_Tecnico` | código (11), opcional | CPF_INTERV: o CPF do técnico, ligado ao nome acima. |
| `Volume_Encerrante_Substituido` | número, opcional | O volume marcado no encerrante que saiu, na **troca ou modificação do encerrante** (item 13.3 do Anexo da 884). O 1320 do Guia não pede (Q218-16). |
| `Volume_Encerrante_Novo` | número, opcional | O volume marcado no encerrante novo. A leitura do bico no trecho seguinte parte dele. |
| `Numero_Relatorio_Manutencao` | texto (até 30), opcional | O número do relatório de manutenção da empresa credenciada pelo Inmetro (item 13.3 do Anexo da 884). |
| `Observacao` | texto, opcional | Texto livre. |

## 6.3 `Mov_Lmc_Bico_Leitura`

*Tipo: fato diário (por trecho). Mestre: não. Vigência: não. Campos: 10.*

Uma linha por **trecho** de um bico num dia. Sem intervenção, é uma linha por bico e por dia (`Sequencia_Dia = 1`). A cada intervenção na bomba, os bicos dela ganham um trecho novo, que aponta para a intervenção. A leitura é o que o contador (encerrante) mostra, em litros com 3 decimais. O volume de vendas do trecho **não se grava**: é a leitura final menos (a leitura inicial mais a aferição).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Lmc_Bico_Leitura` | identificador | --- |
| `ID_Lmc_Bico` | referência (Cad_Lmc_Bico) --- identidade | O bico lido. |
| `Data_Leitura` | data --- identidade | O dia a que o trecho pertence. |
| `Sequencia_Dia` | número --- identidade | 1 é o trecho que abre o dia; cada intervenção na bomba abre o seguinte. |
| `ID_Lmc_Bomba_Intervencao` | referência (Mov_Lmc_Bomba_Intervencao), opcional | A intervenção que abriu este trecho. Vazia no trecho 1. Os campos NR_INTERV, MOT_INTERV, NOM_INTERV, CNPJ_INTERV e CPF_INTERV do 1320 saem daqui. |
| `Leitura_Abertura` | número | VAL_ABERT: leitura do contador na abertura do trecho. |
| `Leitura_Fechamento` | número | VAL_FECHA: leitura do contador no fechamento do trecho. Se for menor que a de abertura e o bico tiver `Valor_Maximo_Contador`, o contador voltou a zero e o 1320 sai em dois registros (seção 7). |
| `Volume_Afericao` | número, opcional | VOL_AFERI: volume aferido na bomba, em litros. |
| `Origem_Dado` | enumeração {digitacao, automacao_pista, sugerida_dos_documentos} | De onde veio a leitura. `sugerida_dos_documentos` é a que o ERP propõe a partir dos encerrantes dos documentos de venda (NF-e, NFC-e e o cupom cujo item traga o bico); vale a que a pessoa confirmar. |
| `Observacao` | texto, opcional | Texto livre. |

## 6.4 `Mov_Nota_Fiscal_Entrada_Item_Tanque` (C171)

*Tipo: fato (sem vigência). Mestre: não. Vigência: não. Campos: 4.*

Substitui o desenho da seção 5.6 do documento 175, que nunca entrou: **a diferença é que o tanque agora é referência**, e não código (Q175-E4 previa isso). O item de combustível recebido pode ir a vários tanques; cada linha é um tanque e a quantidade armazenada nele. Só a nota de **entrada** tem C171.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Fiscal_Entrada_Item_Tanque` | identificador | --- |
| `ID_Item_Entrada` | referência (Mov_Nota_Fiscal_Entrada_Item) --- identidade | O item de combustível recebido. |
| `ID_Lmc_Tanque` | referência (Cad_Lmc_Tanque) --- identidade | NUM_TANQUE: o tanque onde o combustível foi armazenado. O Guia não admite o mesmo tanque duas vezes no mesmo documento. |
| `Quantidade_Armazenada` | número | QTDE: quantidade ou volume armazenado, em litros (3 decimais), maior que zero. |

Dois pontos que o Guia deixa em aberto e que vão ao contador: a **data** do volume recebido no livro (o ERP usa a `Data_Entrada` da nota; C339) e o que fazer quando a soma das quantidades do item difere da quantidade da nota (só aviso).

# 7. Como o ERP gera os registros do posto

O ERP só gera estes registros para a filial com `efd_combustivel_lmc_1300` ligado (seção 9). A ordem do arquivo segue o Guia: 1300 (nível 2), 1310 (nível 3), 1320 (nível 4); 1350 (nível 2), 1360 e 1370 (nível 3); C171 no filho do item da nota de entrada.

| Registro | Uma linha por | Como o ERP monta |
|---|---|---|
| **0000.IND_COMB** | Período | `S` quando a filial está habilitada e há `Mov_Lmc_Tanque_Dia` no período (movimentação e/ou estoque); senão `N` (leitura minha, C344). |
| **1300** | Produto e data | Soma dos 1310 do produto no dia: abertura, entrada, saídas, perda, ganho e físico. O volume disponível (abertura mais entrada) e o escritural (disponível menos saídas) saem das somas. `COD_ITEM` é o produto dos tanques; `DT_FECH`, a data do fechamento. |
| **1310** | Tanque (ou grupo de tanques) e data | Uma linha de `Mov_Lmc_Tanque_Dia` por tanque. Nos tanques interligados, as linhas do grupo se somam (inclusive a capacidade) sob o número do tanque representante. `CAP_TANQUE` vem de `Cad_Lmc_Tanque.Capacidade_Litros`. |
| **1320** | Trecho de bico, no 1310 do tanque do bico | Uma linha de `Mov_Lmc_Bico_Leitura`. O volume de vendas é a leitura final menos (a leitura inicial mais a aferição). Os campos de intervenção saem da intervenção ligada ao trecho; no trecho 1 ficam vazios. |
| **1350** | Bomba | As bombas com `Data_Inicio_Uso` até o fim do período e sem `Data_Retirada` antes do início. |
| **1360** | Lacre | Os lacres da bomba que existiram em algum dia do período (leitura minha, C345). |
| **1370** | Bico, na bomba | Os bicos vigentes no período: número, produto (o do tanque) e número do tanque (o do representante, nos interligados). |
| **C171** | Item da nota de entrada e tanque | Uma linha de `Mov_Nota_Fiscal_Entrada_Item_Tanque`; só nas notas de entrada (códigos 01 e 55). |

**Tanque sem bico.** O tanque que só serve de reservatório não aparece em nenhum bico. O Guia manda informá-lo no 1370 com número de bico de **990 em diante**, mas o 1370 é filho de uma bomba. O ERP numera esses tanques 990, 991… e os coloca sob a **primeira bomba** do posto (menor série), **com aviso**. A escolha é minha e vai ao contador (C340).

**Exemplo com números inventados.** Tanque 001 de gasolina comum, 15/11/2026. Abertura 10.000,000 l; entrada de 5.000,000 l (um C171 de uma nota com `Data_Entrada` de 15/11). Bico 001: leitura de 120.000,000 a 123.500,000, aferição de 20,000 l; bico 002: de 80.000,000 a 81.200,000.

| Conta | Valor (litros) |
|---|---|
| Vendas do bico 001: 123.500,000 − (120.000,000 + 20,000) | 3.480,000 |
| Vendas do bico 002: 81.200,000 − (80.000,000 + 0) | 1.200,000 |
| Saídas do tanque (soma dos 1320) | 4.680,000 |
| Disponível: 10.000,000 + 5.000,000 | 15.000,000 |
| Escritural: 15.000,000 − 4.680,000 | 10.320,000 |
| Estoque físico medido no fim do dia | 10.300,000 |
| Perda (escritural − físico, leitura minha) | 20,000 |
| Ganho | 0,000 |

Como há um tanque só de gasolina comum, o 1300 sai com os mesmos números do 1310, e a soma dos físicos dos 1310 (10.300,000) é igual ao físico do 1300, como o Guia exige.

**Contador que volta a zero.** Bico 003 com `Valor_Maximo_Contador` de 999.999,999: leitura inicial 999.500,000 e final 300,000. O ERP gera dois 1320: o primeiro de 999.500,000 a 999.999,999 (vendas 499,999 l) e o segundo de 0,000 a 300,000 (vendas 300,000 l), como o Guia descreve. A aferição, se houver, vai no primeiro (leitura minha, C343).

# 8. Usina de açúcar e álcool

## 8.1 `Mov_Usina_Producao_Dia`

*Tipo: fato diário. Mestre: não. Vigência: não. Campos: 23.*

O 1391 detalha, por produto da usina, por insumo e por dia, o balanço de produção e estoque. Uma linha por dia, produto e insumo. Álcool se mede em **litros** e açúcar em **quilogramas**; o esmagamento e os resíduos, em **toneladas**. O `COD_PROD` vem da tabela 5.8 que já está em `Cad_Efd_Codigo_Estadual` (tabela oficial `cod_prod_usinas`): a da UF da filial, ou a genérica quando a UF não tem a sua.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Usina_Producao_Dia` | identificador | --- |
| `ID_Filial` | referência (Cad_Filial) --- identidade | A usina (estabelecimento). |
| `ID_Efd_Codigo_Estadual` | referência (Cad_Efd_Codigo_Estadual) --- identidade | COD_PROD do 1390: a linha da tabela 5.8 (`cod_prod_usinas`), da UF da filial ou a genérica. |
| `Data_Producao` | data --- identidade | DT_REGISTRO. Não pode passar de `DT_FIN` do 0000, e o Guia só aceita o 1390 em períodos posteriores a julho de 2012. |
| `ID_Produto_Servico_Insumo` | referência (Cad_Produto_Servico) --- identidade | COD_ITEM do 1391: o insumo usado, do 0200. Não pode haver dois 1391 com o mesmo insumo na mesma data (leitura do Guia, C346). |
| `Quantidade_Insumo_Esmagado` | número, opcional | QTD_MOID: insumo esmagado, em toneladas. |
| `Estoque_Inicial` | número | ESTQ_INI: estoque do início do dia (litros no álcool, kg no açúcar). Em princípio é o final do dia anterior (aviso). |
| `Quantidade_Produzida` | número, opcional | QTD_PRODUZ. |
| `Entrada_Transformacao` | número, opcional | ENT_ANID_HID: anidro vindo da transformação do hidratado, ou hidratado vindo do anidro, em litros. Só no álcool. |
| `Outras_Entradas` | número, opcional | OUTR_ENTR: recebido de terceiros, devoluções e outras entradas. |
| `Perda` | número, opcional | PERDA: evaporação (litros) no álcool ou quebra de peso (kg) no açúcar. |
| `Consumo` | número, opcional | CONS: consumo próprio (litros ou kg). |
| `Saida_Transformacao` | número, opcional | SAI_ANI_HID: álcool usado para virar o outro tipo, em litros. Só no álcool. |
| `Saidas` | número, opcional | SAIDAS: total das saídas (litros ou kg). |
| `Estoque_Final` | número | ESTQ_FIN: estoque do fim do dia. |
| `Estoque_Inicial_Mel` | número, opcional | ESTQ_INI_MEL: mel residual no início do dia, em kg. Só no açúcar. |
| `Producao_Mel` | número, opcional | PROD_DIA_MEL: todas as entradas de mel residual (produção e demais), em kg. Só no açúcar. |
| `Utilizacao_Mel` | número, opcional | UTIL_MEL: mel residual usado na produção e demais saídas, em kg. Só no açúcar. |
| `Producao_Do_Mel` | número, opcional | PROD_ALC_MEL: álcool (litros) ou açúcar (kg) produzido a partir do mel residual. |
| `Observacao` | texto, opcional | OBS. |
| `Quantidade_Residuo_Ddg` | número, opcional | QTD_RESIDUO_DDG: resíduo seco de destilaria, em toneladas. |
| `Quantidade_Residuo_Wdg` | número, opcional | QTD_RESIDUO_WDG: resíduo úmido de destilaria, em toneladas. |
| `Quantidade_Residuo_Bagaco` | número, opcional | QTD_RESIDUO_CANA: bagaço de cana, em toneladas. |

**Não há entidade para o 1390.** O registro lista os produtos da usina; o ERP o gera a partir dos `COD_PROD` distintos que têm 1391 no período, sem repetir o produto (o Guia proíbe dois 1390 com o mesmo código). Se a usina só tiver estoque num produto sem produção, a pessoa registra a linha do dia com os valores informados (C346).

## 8.2 O que o ERP deriva na geração

O Guia traz o **tipo de resíduo** (`TP_RESIDUO`: 01 bagaço, 02 DDG, 03 WDG, 04 DDG mais WDG) e a **quantidade de resíduo** (`QTD_RESIDUO`) além das três quantidades separadas. As três separadas são o dado; os dois campos saem delas (leitura minha, C348):

| Quantidades informadas | `TP_RESIDUO` | `QTD_RESIDUO` |
|---|---|---|
| Só bagaço | 01 | Bagaço |
| Só DDG | 02 | DDG |
| Só WDG | 03 | WDG |
| DDG e WDG, sem bagaço | 04 | DDG mais WDG |
| Bagaço com DDG ou WDG | **Ambíguo**: o ERP avisa e deixa em branco | --- |

O **balanço** que o ERP confere, só como aviso, é: estoque final = estoque inicial + produzida + entrada por transformação + outras entradas − perda − consumo − saída por transformação − saídas (leitura minha, C347). O Guia não dá a equação.

# 9. Habilitação e domínios

Dois valores novos de `Cad_Empresa_Modulo_Opcional` (domínio `modulo_fiscal_opcional`, aberto), no mesmo molde dos do documento 175. **Nenhum vem habilitado.** A habilitação é por filial (o posto e a usina são estabelecimentos), com vigência.

| Valor | Registros que a habilitação libera | Liga no 0000 |
|---|---|---|
| `efd_combustivel_lmc_1300` | 1300, 1310, 1320, 1350, 1360, 1370 e o C171 (posto revendedor) | `IND_COMB` |
| `efd_usina_1390` | 1390 e 1391 (usina de açúcar e álcool) | `IND_USINA` |

O `efd_combustivel_c165` do documento 175 **continua só no C165** (distribuidora, refinaria e revendedora que emite nota; D-N482). O posto é outro caso. O ERP não liga nenhum valor sozinho nem por padrão: quem tem posto liga o primeiro; quem tem usina liga o segundo.

Nenhum domínio novo em `Cad_Classe_Sistema` além desses dois valores. As enumerações pequenas (`Tipo_Medicao`, `Origem_Dado`, `Situacao`) ficam nos campos.

# 10. Avisos do ERP

O ERP **avisa e nunca bloqueia** (D-N284). Estes são os avisos novos deste desenho.

| Nº | O que o ERP avisa | Quando |
|---|---|---|
| **A1** | Item de combustível sem tanque (C171) | Nota de entrada de filial habilitada, com item cujo produto tem código da ANP e que não tem linha em `Mov_Nota_Fiscal_Entrada_Item_Tanque`. |
| **A2** | Quantidade armazenada diferente da quantidade do item | A soma dos C171 do item difere da quantidade da nota. |
| **A3** | Dia sem medição | Tanque em uso, sem `Mov_Lmc_Tanque_Dia` em dia do período; o 1300 e o 1310 daquele dia ficam de fora. |
| **A4** | Tanque sem combustível | O produto do tanque não tem `ID_Produto_Anp`, ou o tanque não tem produto vigente na data. |
| **A5** | Bico sem tanque, ou tanque diferente | O bico não tem tanque vigente; ou o tanque do bico difere do `Combustivel_Numero_Tanque` da nota de saída. |
| **A6** | Quebra de contador | A leitura de abertura do dia difere da de fechamento do dia anterior no mesmo bico, e não houve intervenção. |
| **A7** | Contador voltou sem máximo | Leitura final menor que a inicial e o bico sem `Valor_Maximo_Contador`. |
| **A8** | Volume de vendas negativo | A aferição é maior que a diferença entre as leituras. |
| **A9** | Estoque de abertura diferente | O de abertura do dia difere do físico do fechamento do dia anterior. |
| **A10** | Escritural diferente do estoque | Com `ID_Local_Estoque` informado, o escritural do livro difere do saldo do local no fim do dia. |
| **A11** | Venda do contador diferente da venda dos documentos | **Por bico e por dia** quando todos os itens do produto no dia trazem o bico; **por produto e por dia** nos demais casos. Soma dos volumes do livro contra a soma das quantidades dos itens de saída de qualquer modelo (NF-e, NFC-e, cupom); com cupom de ECF só pela Redução Z, vale a quantidade dela, **nunca as duas para o mesmo equipamento e dia** (seção 14.3). Só informa a diferença; não há tolerância (C344). |
| **A12** | Dia fechado alterado | Nota de entrada, C171 ou leitura de bico muda depois de `Situacao = fechado`. O ERP não recalcula sozinho. |
| **A13** | Número que a nota cita não existe | Número de tanque, bico ou bomba da nota de saída fora do cadastro. |
| **A14** | Tanque representante inválido | O representante não existe, não está vigente ou aponta para outro grupo. |
| **A15** | 1350 ou 1370 ausente | Há 1300 no período, mas a filial não tem bomba ou bico vigente (o Guia os exige se existir 1300). |
| **A16** | Balanço da usina não fecha | Estoque final diferente da equação da seção 8.2. |
| **A17** | Estoque inicial da usina diferente | O estoque inicial do dia difere do final do dia anterior. |
| **A18** | Campo obrigatório do 1391 sem informação, ou resíduo ambíguo | O ERP **não preenche zero sozinho** (sem valor padrão escondido). |
| **A19** | Campo fora do produto | Mel residual em produto que não é açúcar; entrada ou saída por transformação em produto que não é álcool. |
| **A20** | `COD_PROD` fora da tabela 5.8 | A linha de `Cad_Efd_Codigo_Estadual` não é da UF da filial nem da genérica. |
| **A21** | Dado do Bloco 1 em filial sem habilitação | Existe cadastro, leitura ou C171, mas a filial não tem o módulo ligado; nada sai no arquivo. |
| **A22** | Variação do estoque acima do limite | **Por produto e por dia fechado**, com `Limite_Variacao_Percentual` preenchido: o saldo líquido (estoque físico de fechamento menos escritural, somados os tanques do produto, o campo 8 do Anexo da 884) passa do percentual do estoque físico de fechamento, ou passa sem texto em `Observacao` de algum tanque do produto no dia (seção 14.5). Com a Q218-18 aprovada, o texto do aviso cita a Solução de Consulta Cosit 223/2023 (seção 14.8). |
| **A23** | Habilitação sem a autorização ANP correspondente | `efd_combustivel_lmc_1300` ligado em filial sem autorização vigente de `posto_revendedor`; `efd_combustivel_c165` ligado em filial com autorização de posto ou sem autorização de distribuidor, refinaria ou revendedora; `efd_combustivel_lmc_1300` ligado em filial só com autorização de distribuidor (seção 14.4). |
| **A24** | Posto vende combustível a outro revendedor | Item de saída com código da ANP, emitido por filial com autorização de `posto_revendedor`, para participante com autorização vigente de `posto_revendedor`. A cartilha da ANP veda, "ainda que o outro estabelecimento pertença à mesma pessoa jurídica" (C354). |
| **A25** | Entrada de combustível de emitente sem autorização de fornecedor | Nota de entrada de combustível em filial de posto, cujo emitente não tem autorização vigente de `distribuidor`, `comercializador_etanol`, `produtor_biocombustiveis` ou `transportador_revendedor_retalhista`. A lista é **leitura minha** (C350). |
| **A26** | Venda de combustível sem bico | Item de saída com código da ANP, de filial habilitada ao 1300, sem `Combustivel_Numero_Bico`, em qualquer modelo (NFC-e, cupom ou NF-e). Sem bico, o item não entra na leitura sugerida. |
| **A27** | Tanque de combustível sem bico ligado | Tanque em uso, com produto de código da ANP e sem `Cad_Lmc_Bico` vigente. A cartilha da ANP proíbe tanque não interligado a bomba, salvo óleo usado, desativação protocolada e cisterna de água de chuva; o Guia manda informá-lo com número de bico a partir de 990 (seção 7). |

# 11. O que entra no próximo "consolidar"

**9 entidades novas (107 campos), todas na Contabilidade & Fiscal.**

| Entidade | Tipo | Campos | Vigência | Seção |
|---|---|---|---|---|
| `Cad_Lmc_Tanque` | cadastro do usuário (sem carga) | 14 | sim | 5.1 |
| `Cad_Lmc_Bomba` | cadastro do usuário (sem carga) | 13 | sim | 5.2 |
| `Cad_Lmc_Bomba_Lacre` | fato com datas | 5 | não | 5.3 |
| `Cad_Lmc_Bico` | cadastro do usuário (sem carga) | 9 | sim | 5.4 |
| `Mov_Lmc_Tanque_Dia` | fato diário | 17 | não | 6.1 |
| `Mov_Lmc_Bomba_Intervencao` | fato | 12 | não | 6.2 |
| `Mov_Lmc_Bico_Leitura` | fato diário (por trecho) | 10 | não | 6.3 |
| `Mov_Nota_Fiscal_Entrada_Item_Tanque` | fato (C171) | 4 | não | 6.4 |
| `Mov_Usina_Producao_Dia` | fato diário | 23 | não | 8.1 |

Com isso o dicionário iria de 1.220 para **1.229 entidades** e de 14.154 para **14.261 campos** (soma deste ensaio, sem os outros documentos que ainda esperam o "consolidar").

**Nenhuma entidade existente muda.** Valores novos de domínio:

| Onde | O que entra |
|---|---|
| `modulo_fiscal_opcional` (`Cad_Classe_Sistema`) | 2 valores: `efd_combustivel_lmc_1300` e `efd_usina_1390` (provisórios, nenhum ligado) |

**Cargas:** nenhuma entidade tem carga (são cadastros e movimentos do cliente); só as 2 linhas do domínio.

**Textos que a consolidação corrige.** (1) O documento 175, seção 5.6, descrevia `Mov_Nota_Fiscal_Entrada_Item_Tanque` com o tanque por código; a entidade nasce aqui, com referência ao tanque (Q175-E4 e D-N482). (2) O Anexo F do documento 167 e a cobertura do 175 passam a apontar para o documento 218 nos registros 1300 a 1391 e C171. (3) O documento 38, seção 1.13, perde a linha da Q167-6. **Nada deste documento mexe** nos registros do C165, do Bloco K, nem no Motor de Regras: o Bloco 1 não decide cClassTrib nem cria código de classificação tributária.

# 12. Perguntas

## 12.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q218-1** | Cadastros `Cad_Lmc_Tanque`, `Cad_Lmc_Bomba`, `Cad_Lmc_Bomba_Lacre` e `Cad_Lmc_Bico` como na seção 5 (produto no tanque e não no bico; tanque representante nos interligados; valor máximo do contador no bico)? | Sim |
| **Q218-2** | `Mov_Lmc_Tanque_Dia` como única peça gravada por dia (físico informado; os cinco valores calculados gravados no fechamento do dia; 1300 e volume disponível somados na geração)? | Sim |
| **Q218-3** | `Mov_Lmc_Bico_Leitura` por trecho e `Mov_Lmc_Bomba_Intervencao` na bomba, com a divisão do 1320 pelo contador feita na geração e a leitura sugerida a partir dos encerrantes dos documentos de venda (nota ou cupom)? | Sim |
| **Q218-4** | O C171 como `Mov_Nota_Fiscal_Entrada_Item_Tanque` com referência ao tanque, no lugar do desenho do documento 175, seção 5.6? | Sim |
| **Q218-5** | Usina: `Mov_Usina_Producao_Dia`, o 1390 derivado dos produtos com 1391 e o `COD_PROD` pela tabela 5.8 que já existe em `Cad_Efd_Codigo_Estadual`? | Sim |
| **Q218-6** | Dois valores novos de habilitação (`efd_combustivel_lmc_1300` e `efd_usina_1390`), nenhum ligado por padrão, com `IND_COMB` e `IND_USINA` derivados? | Sim |
| **Q218-7** | Os 27 avisos da seção 10 (21 do desenho original e 6 da seção 14), com o **limite de variação só quando o posto o preencher** (o ERP não traz 0,6% pronto) e sem tolerância na comparação com as vendas, até o contador dizer qual vale? | Sim |
| **Q218-8** | Você me envia o Ajuste SINIEF 14/2025 e o Ajuste SINIEF 01/92 (CONFAZ ou Diário Oficial), para eu conferir o que li de fonte secundária? (A Resolução ANP 884/2022 chegou em 12/11/2026, no Diário Oficial.) | Sim, sem pressa |
| **Q218-9** | Aplico tudo, inclusive Q218-10 a Q218-17, no próximo "consolidar"? | Sim |
| **Q218-10** | A cadeia da seção 14: o papel (usina, distribuidor, posto, grande consumidor) **derivado da autorização ANP**, o canal de venda **derivado do modelo do documento**, **sem entidade nova** para o distribuidor, e a habilitação do C165 como está no documento 175? | Sim |
| **Q218-11** | O campo `Limite_Variacao_Percentual` no tanque e o aviso A22, sem valor preenchido pelo ERP (a Resolução 884 cita 0,6%), com a comparação **por produto e por dia**, como o campo 8 do Anexo? | Sim |
| **Q218-12** | Os Termos de Abertura e de Fechamento do LMC (a cartilha os manda elaborar "conforme tabela do Anexo"; o Anexo da 884 no Diário Oficial não os traz) entram no ERP? | Não, até o contador dizer o modelo (C356) |
| **Q218-13** | O aviso A11 por bico quando todos os itens trazem o bico e por produto nos demais casos, com o cupom contado pelos documentos ou pela Redução Z, **nunca pelos dois**? | Sim |
| **Q218-14** | O vínculo posto-distribuidor (bandeira e origem do combustível na bomba) como cadastro? | Não agora (D-N68); a origem na bomba sai do fornecedor da última entrada |
| **Q218-15** | Dois campos opcionais de **transferência entre tanques** em `Mov_Lmc_Tanque_Dia`, com o escritural do tanque somando a recebida e subtraindo a enviada (item 13 do Anexo da 884)? | Sim |
| **Q218-16** | Três campos opcionais na intervenção da bomba: volume do encerrante substituído, volume do novo e número do relatório de manutenção (item 13.3 do Anexo)? | Sim |
| **Q218-17** | A folha do LMC da ANP (campos 1 a 13 do Anexo) como **relatório** dos mesmos dados, sem entidade nova, com o campo 10 (valor das vendas) somado dos itens vendidos? | Sim |
| **Q218-18** | A perda de até 0,6% da gasolina que a Solução de Consulta Cosit 223/2023 admite como custo (lucro real): o ERP mostra, no relatório do LMC, a perda **dentro e fora do limite** por produto e por dia, **sem campo novo** e **sem adição automática** ao e-Lalur, e o aviso A22 cita a solução de consulta (seção 14.8)? | Sim |

## 12.2 Para o contador

Estas perguntas estão no documento 188, Parte 22 (C335 a C357). Aqui só a lista e o tratamento provisório.

| Nº | Pergunta | Provisório |
|---|---|---|
| **C335** | O Ajuste SINIEF 14/2025 (item VIII do § 3º da cláusula primeira do Ajuste SINIEF 2/2009, efeitos desde 01/09/2025) obriga o posto a informar o 1300 a 1370? Quais UF exigem e desde quando? A obrigação com a ANP continua? | O ERP gera para a filial habilitada, qualquer UF |
| **C336** | Qual norma da ANP vale hoje para o LMC? A Resolução ANP 884/2022, lida no Diário Oficial de 08/09/2022 (edição 171, p. 62; ementa de 05/09/2022; o Anexo cita "8 de setembro"): LMC do revendedor varejista, diário, por produto, com limite de 0,6% do estoque físico e justificativa em "13) Observações". Há alteração posterior? O que o posto faz além de justificar? | Limite só se o posto o preencher; aviso A22 |
| **C337** | Fórmula da perda e do ganho no 1300 e no 1310: escritural menos físico (perda) e físico menos escritural (ganho)? Há outro componente (evaporação, aferição)? O campo 8 do Anexo da 884 é **um saldo líquido por produto** (fechamento menos escritural), e o 1300 tem perda e ganho em dois campos: somar sem compensar entre tanques bate com o campo 8? | Leitura minha, na seção 6.1; o A22 usa o saldo líquido do produto |
| **C338** | O estoque do início do dia é o físico do fechamento do dia anterior? No primeiro dia, parte do inventário ou de outra fonte? | Físico do dia anterior; primeiro dia digitado |
| **C339** | O volume recebido do dia (C171) vale pela `Data_Entrada` da nota ou pela data da descarga? E quando a soma dos C171 do item difere da quantidade da nota? | `Data_Entrada`; só aviso |
| **C340** | Tanques interligados: o 1310 soma abertura, entrada, saídas e físico, e a capacidade (`CAP_TANQUE`) é a soma? O tanque sem bico (990 em diante) fica sob qual bomba? | Soma; sob a primeira bomba, com aviso |
| **C341** | O número do bico é único por estabelecimento ou por bomba (o 1320 só cita o número)? O número da bomba da nota (até 3 posições) tem relação com a série do 1350? | Único por filial; sem relação automática |
| **C342** | Intervenção: o campo `MOT_INTERV` é o motivo (o Guia o descreve como nome da empresa)? Como numerar `NR_INTERV` sem o órgão? O CNPJ e o CPF saem sempre os dois? | Motivo; sequencial do posto; ambos opcionais |
| **C343** | Contador no valor máximo: o primeiro 1320 vai até o valor máximo e o segundo parte de zero; em qual deles vai a aferição? | No primeiro |
| **C344** | Quais produtos entram no 1300 (gasolinas, diesel, etanol, mistura com biodiesel, querosene)? GNV fica de fora? `IND_COMB` sai `S` com movimentação ou estoque? A comparação entre venda do contador e das notas tem tolerância? | Produto com código da ANP; GNV fora; sem tolerância |
| **C345** | 1350 e 1360: bombas e lacres que existiram em algum dia do período, ou os que existem no último dia? Bomba cedida em comodato é "pertencente ao varejista"? | Os que existiram no período |
| **C346** | Usina: o 1390 sai por produto com 1391; o insumo (`COD_ITEM`) é a cana ou o milho? O que sai quando há estoque mas não há produção no produto? Qual `COD_PROD` vale para quem tem tabela 5.8 própria da UF? | Produtos com 1391; insumo é o item usado; UF e depois genérica |
| **C347** | Usina: o balanço de estoque (seção 8.2) está certo? Como lançar a transformação de anidro em hidratado e o mel residual do açúcar? | Equação da seção 8.2, só aviso |
| **C348** | Usina: como derivar `TP_RESIDUO` e `QTD_RESIDUO` das três quantidades (bagaço, DDG e WDG)? O 1391 é 1:1 ou 1:N com o 1390 (o Guia diz as duas coisas)? Campos "O" sem valor saem vazios ou com zero? | Tabela da seção 8.2; vazios com aviso |
| **C349** | O limite de 0,6% do art. 5º da Resolução 884 é sobre o estoque físico de **abertura** ou de **fechamento**? A variação é por produto (como o campo 8 do Anexo) ou por tanque, por dia ou **acumulada** (a minuta falava em "avaliações acumuladas", sem período)? Vale também para o ganho? | Saldo líquido do produto, por dia, sobre o estoque físico de fechamento; perda e ganho; só aviso |
| **C350** | Quem pode fornecer combustível ao posto: a cartilha cita o distribuidor autorizado (item 3) e, na amostra-testemunha, o fornecedor de etanol e o TRR. A usina vende etanol direto ao posto (a Lei 14.292/2022 só li em cartilha estadual)? Há regra por produto (gasolina, diesel, etanol)? | Distribuidor, comercializador de etanol, produtor de biocombustíveis e TRR; só aviso A25 |
| **C351** | Distribuidor: quais obrigações fiscais e da ANP valem, por UF e por produto (EFD C165 e 0206, relatório COTEPE do Convênio ICMS 199/2022 para diesel, biodiesel e GLP, SIMP)? O distribuidor envia dados à ANP por outra norma (a Resolução ANP 729/2018 foi citada pelo IBP na consulta; não li)? | Só C165 e 0206, por habilitação; nenhum registro novo |
| **C352** | Grande consumidor (consumidor final que compra a granel do distribuidor): tem autorização ou registro na ANP, e de que tipo? Com tanque próprio, informa o 1300? | Sem autorização de combustível; fora do 1300 |
| **C353** | Cupom fiscal de combustível (SAT, CF-e-ECF, ECF): quais UF ainda o admitem para combustível, e o leiaute do cupom admite bico e encerrante? A comparação por produto (A11) basta? | A11 por produto, sem tolerância |
| **C354** | A vedação de o posto vender combustível a outro revendedor (cartilha da ANP) tem exceções (venda a distribuidor, devolução, transferência entre filiais)? Quais CFOP ficam fora do aviso A24? | Aviso para qualquer CFOP, só quando o comprador tem autorização vigente de posto |
| **C355** | Transferência de produto entre tanques do posto (item "e.", entre 13.4 e 13.5 do Anexo da 884 no Diário Oficial): entra no 1310 como entrada e saída do tanque, como ajuste, ou fica fora do EFD? O escritural do tanque deve somá-la e subtraí-la? | Dois campos de transferência no tanque; só no escritural por tanque; no produto o efeito é zero |
| **C356** | Termos de Abertura e de Fechamento do LMC: a cartilha da ANP manda elaborar "conforme tabela constante do Anexo" da 884, mas o Anexo do Diário Oficial não os traz. Qual é o modelo, quem assina, e entra no EFD? | Não desenhado |
| **C357** | Solução de Consulta Cosit 223/2023 (perda de até 0,6% da gasolina como custo no lucro real): (a) vale para outros combustíveis (etanol, diesel)? (b) sobre qual base e período se mede o 0,6% (a 884 diz estoque físico e campo 8)? (c) a parte acima do limite é indedutível, ou depende de prova e justificativa, e entra como adição na Parte A do e-Lalur? (d) a solução vale para quem não a consultou? (e) a SC Cosit 76/2021, a que ela é "parcialmente vinculada", muda algo? | Nada automático; relatório com perda dentro e fora do limite (Q218-18) |

## 12.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q218-E1** | Há cliente (ou projeto) com posto revendedor de combustíveis ou com usina de açúcar e álcool? Sem cliente, o desenho fica pronto e **desligado**, como manda a D-N68. |
| **Q218-E2** | Como chegam as leituras dos contadores e a medição dos tanques: automação de pista, planilha ou digitação? `Origem_Dado` aceita as três; confirmar. |
| **Q218-E3** | O posto mede os tanques todos os dias (régua ou sonda) e quem fecha o dia? O fechamento grava os valores calculados; confirmar se o posto fecha por dia ou por mês. |
| **Q218-E4** | A produção da usina vem das ordens de produção (`Mov_Ordem_Producao`) ou é digitada num lançamento próprio? A ordem de produção não tem esmagamento, mel residual, anidro e hidratado nem resíduos. |
| **Q218-E5** | O estoque de combustível do posto é controlado pelo módulo de Estoque (um local por tanque) ou só pelo livro? Isso decide se o `ID_Local_Estoque` do tanque é usado. |
| **Q218-E6** | A nota de saída do posto (NFC-e) já leva bico, bomba, tanque e encerrante em todos os itens de combustível? Sem isso a leitura sugerida a partir das notas não funciona. |
| **Q218-E7** | Os combustíveis do posto têm código da ANP no cadastro do produto (`ID_Produto_Anp`)? Sem ele o ERP não sabe que o item é combustível. |
| **Q218-E8** | Quais modelos de documento os postos clientes usam para vender (NFC-e, SAT ou MFE, CF-e-ECF, ECF)? O PDV grava bico e encerrante no item do cupom? Sem bico no cupom, o ERP só compara por produto (A11). |
| **Q218-E9** | Há cliente que seja **distribuidor** de combustíveis (compra da usina e revende ao posto ou a grande consumidor), ou cliente **grande consumidor** com tanque próprio? O que ele precisa além do C165 e do 0206: bases e tanques, relatório COTEPE, SIMP? Sem cliente, nada se desenha (D-N68). |

# 13. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **O Ajuste SINIEF 14/2025 foi lido só em fonte não oficial** (site de legislação e notas de secretarias estaduais). Não li o ato no CONFAZ nem no Diário Oficial; o que digo sobre efeitos, data e alcance é por essa fonte e vai ao contador (C335).
3. **A Resolução ANP nº 884/2022 foi lida no Diário Oficial, na impressão do site da Imprensa Nacional** (edição 171, seção 1, página 62, de 08/09/2022), que a própria página diz **não substituir a versão certificada**; antes, em duas cópias não oficiais (LegisWeb e Brasil Postos), com o mesmo texto. Conferi com a **Cartilha do Posto Revendedor da ANP** (maio de 2026, oficial, que não substitui a norma) e com a **minuta** do relatório da Consulta Pública 04/2022 e da Agenda Regulatória 4.22 (li as páginas 1 a 16 do relatório, não a carta da AbriLivre, em imagem). O FAQ do LMC no site da ANP, que você indicou, chegou à minha leitura **só em resumo** de ferramenta (data de 04/07/2024, não verificada) e **não o uso como fonte literal**. A Portaria DNC 26/1992 deixa de ser fundamento. O limite é campo do posto (C336, C349).
4. **Não verifiquei, UF por UF, quem exige o 1300 a 1370 nem desde quando.** Pode haver exigência estadual diferente da do Guia.
5. **O Guia não dá as fórmulas** da perda, do ganho, do estoque de abertura e do balanço da usina. As que escrevi são **leitura minha**, só como cálculo e aviso (C337, C338, C347).
6. **O Guia tem pontos que se contradizem** (descrição de `MOT_INTERV`; ocorrência do 1391 como 1:1 e 1:N) e campos "O" cujo vazio o desenho não resolve sozinho (C342, C348). O ERP avisa e não preenche zero.
7. **Não desenhei** o envio do LMC eletrônico à ANP, a guarda do livro físico, nem a ligação do LMC com o estoque além do aviso A10: dependem da norma da ANP; a 884 diz só que os dados vão à ANP "quando notificado" (art. 3º) e que o LMC dos seis últimos meses fica no posto (art. 4º).
8. **Não desenhei** o IBS e a CBS dos combustíveis neste bloco: ficam nos documentos 170 e 173. O Bloco 1 não decide cClassTrib.
9. **Os PDFs do Paraná que você enviou durante o desenho** (Resolução SEFA 20/2017, a seção do RICMS-PR sobre energia elétrica e a do SISCRED) **não tratam do Bloco 1**; estão registrados na D-N577 e afetam só a Q215-5.
10. **As leituras minhas** (fórmulas, data da entrada, tanque sem bico, lacres do período, derivação do resíduo) estão marcadas e vão ao contador; nenhuma vira regra no código.
11. **A 884 não diz qual estoque físico** (abertura ou fechamento) é a base dos 0,6%, nem o período; a minuta falava em "avaliações acumuladas". A base de fechamento, por produto e por dia, é leitura minha (C349).
12. **Não sei se o PDV grava bico e encerrante no cupom**, nem se o leiaute do cupom os admite, nem quais UF ainda aceitam cupom para combustível. O desenho funciona sem bico no cupom (A11 por produto) e pergunta (Q218-E8, C353).
13. **Distribuidor: não desenhei** o relatório do Convênio ICMS 199/2022 (lido só em site não oficial; alcança diesel, biodiesel e GLP/GLGN), a indicação do ICMS monofásico anterior no documento, as bases e tanques do distribuidor nem o envio à ANP pelo SIMP. Dependem de norma que não li e de haver cliente (C351, Q218-E9). O envio de dados dos demais elos da cadeia (Resolução ANP 729/2018, citada numa contribuição do IBP) também não foi lido. A lista de fornecedores aceitos pelo A25 e a venda direta da usina ao posto são leitura minha (C350).
14. **Não desenhei** o controle do tanque de grande consumidor, nem o vínculo posto-distribuidor (bandeira, origem na bomba), nem os termos de abertura e fechamento, nem o boletim de conformidade e a análise de qualidade do recebimento (Q218-12, Q218-14).
15. **O Anexo tem pontos que o texto não resolve:** os termos de abertura e de fechamento, que a cartilha cita e o Anexo do Diário Oficial não traz; o item rotulado "e." entre 13.4 e 13.5 (**está assim também no Diário Oficial**, então não é erro das cópias); a data (a ementa e a assinatura são de 05/09/2022, a publicação é de 08/09/2022 e o cabeçalho do Anexo diz "8 de setembro", o que parece erro do próprio texto). Como o EFD separa perda e ganho e o campo 8 é um saldo só, a conciliação vai ao contador (C337, C356).
16. **A Solução de Consulta Cosit nº 223/2023 foi lida só na página do Diário Oficial de 29/09/2023** que você enviou, e só a parte que cita a 884 (as demais soluções da página estão na seção 14.8, sem desenho). Não li a SC Cosit nº 76/2021, a que ela é parcialmente vinculada. O alcance para outros combustíveis, base e período e o tratamento do que passa de 0,6% são perguntas ao contador (C357); o que escrevi do e-Lalur é leitura minha.

# 14. Versão 2: cadeia de comercialização, canais de venda e o distribuidor

*Pedido seu de 12/11/2026, depois da entrega da primeira versão: "a venda pode ser feita através de nota fiscal ou cupom fiscal" e "tem a figura do distribuidor, que não é nem o posto, nem a usina: compra da usina e revende para o posto, ou para o consumidor final, no caso de grandes consumidores". Esta seção responde aos dois pontos e incorpora a **Cartilha do Posto Revendedor de Combustíveis** da ANP (7ª edição, revisão de maio de 2026), que você enviou e que **li inteira (23 páginas)**, e dois documentos oficiais da ANP que você enviou em seguida: o **Relatório da Consulta e Audiência Públicas nº 04/2022** (22 páginas; li o texto das páginas 1 a 16; as páginas 17 a 22 são a carta da AbriLivre, em imagem, e **não as li**) e o **2º Relatório da Agenda Regulatória 2022-2023** (165 páginas; li só o índice e o item 4.22, que trata do LMC). **Versão 2.2 (12/11/2026):** você enviou a Resolução 884 como saiu no Diário Oficial e a página do DOU com a SC Cosit 223/2023 (14.8). **Versão 2.1 (12/11/2026):** você pediu para ler o Anexo da Resolução ANP 884/2022, e li o **texto completo da norma, com o Anexo**, primeiro em **duas cópias de sites não oficiais** (LegisWeb e Brasil Postos), que na versão 2.2 conferi no Diário Oficial. Nada aqui entra no dicionário agora.*

## 14.1 O que mudou em relação à primeira versão

1. **O cupom fiscal já existe no dicionário como documento de saída.** O cupom do ECF (C460 e C470), o CF-e-ECF (C465) e o CF-e-SAT (C800 e C860) são gravados em `Mov_Nota_Fiscal_Saida` e `Mov_Nota_Fiscal_Saida_Item`, com `ID_Equipamento_Fiscal` e o modelo em `ID_Modelo_Documento`. A Redução Z (C405, C420 e C425) fica em `Mov_Ecf_Reducao_Z*`, com a **quantidade por produto** em `Mov_Ecf_Reducao_Z_Totalizador_Item`. Não é preciso nenhuma entidade nova. O que muda é a **comparação** entre o contador da bomba e as vendas (aviso A11) e a **leitura sugerida**, que passam a valer para qualquer canal (14.3).
2. **O distribuidor não precisa de entidade nova.** O papel dele já se declara em `Cad_Participante_Autorizacao_Anp` (tipo `distribuidor`), o estabelecimento já é participante (`Cad_Filial.ID_Participante`) e a habilitação do C165 já existe (`efd_combustivel_c165`, documento 175). O que faltava eram **avisos que cruzam o papel com a habilitação e com o documento de venda** (14.4).
3. **A norma do LMC deixou de ser só fonte secundária.** A cartilha da ANP diz que o LMC foi instituído pela **Resolução ANP nº 884, de 05/09/2022** e cita o limite de **0,6%** de variação do estoque físico. A Agenda Regulatória (ação 4.22, "Concluída") e o relatório da Consulta Pública 04/2022 dizem que a 884 **revisou a Portaria DNC 26/1992 para a revenda varejista de combustíveis automotivos, sem alterar o mérito**. Logo, **o LMC é do posto**; o distribuidor não tem LMC por essa norma. A Resolução 884 foi lida na versão 2.1 em duas cópias não oficiais e na 2.2 no **Diário Oficial**, com o mesmo texto; o relatório da consulta mostra a **minuta**, e o que vale é o texto final (14.5 e 14.7).
4. **Versão 2.1: o Anexo da 884 acrescenta três pontos ao desenho** (14.7): a transferência entre tanques (`Volume_Transferencia_Recebida` e `_Enviada`), a troca de encerrante (três campos na intervenção da bomba) e a folha do LMC como relatório. Corrige também o aviso A22, que passa a ser **por produto e por dia**, sobre o saldo líquido do campo 8.
5. **Versão 2.2: o Diário Oficial confirma o texto da 884 e a SC Cosit 223/2023 liga a perda de até 0,6% da gasolina ao custo no lucro real** (14.8). Nenhum campo e nenhum aviso novo (o texto do A22 só ganha uma citação, se você aprovar a Q218-18); uma pergunta a você (Q218-18) e uma ao contador (C357).

## 14.2 Quem é quem na cadeia

O desenho trata de cinco papéis. O papel **não é cadastro novo**: sai de `Cad_Participante_Autorizacao_Anp` (autorização vigente na data da operação), e quem não tem autorização de combustível é, para o ERP, consumidor.

| Papel | Compra de | Vende a | Documento de venda | Tipo em `agente_cadeia_combustiveis` | O que a EFD-ICMS/IPI pede |
|---|---|---|---|---|---|
| **Usina ou produtor de etanol** | Cana, milho (insumo) | Distribuidor; **posto diretamente**, no caso do etanol (leitura minha, C350) | NF-e | `produtor_biocombustiveis`, `comercializador_etanol` | 1390 e 1391 (seção 8) |
| **Distribuidor** | Usina, refinaria, importador | Posto revendedor; **grande consumidor** final | NF-e | `distribuidor` | C165 e 0206 (documento 175); **não** informa o 1300, porque o LMC da ANP é da revenda varejista |
| **Posto revendedor** | Distribuidor (e, pela cartilha, fornecedor de etanol e TRR) | Consumidor final | NFC-e, cupom (SAT, CF-e-ECF, ECF) ou NF-e | `posto_revendedor` | 1300 a 1370 e C171 (seções 5 a 7); **não** informa o C165 |
| **Grande consumidor** | Distribuidor | Ninguém (consome) | Recebe NF-e | Sem autorização de combustível | Nada de combustível; **fica fora** do 1300 (leitura minha, C352) |
| **TRR** | Distribuidor | Consumidor final | NF-e | `transportador_revendedor_retalhista` | Só existe no domínio; **não desenhado** neste documento |

Três observações. **Primeira**: o **distribuidor não é a usina nem o posto**; ele compra a granel e revende a granel, **não tem bico** e por isso não tem 1300. O estoque dele fica em `Cad_Local_Estoque`, como o de qualquer produto (Q218-E9 pergunta se isso basta). **Segunda**: o posto **não é obrigado** a ter distribuidor no caminho, porque a cartilha da ANP nomeia o "fornecedor de etanol" ao lado do distribuidor e do TRR. **Terceira**: o grande consumidor que tem tanque próprio não faz LMC de posto; se algum cliente quiser controlar o tanque de consumo, é desenho à parte, que **não fiz** (limite 14 da seção 13).

## 14.3 Canais de venda do posto

O 1320 (volume vendido) sai do **contador da bomba** e **não depende do documento de venda**. O documento só entra em dois lugares: na **leitura sugerida** (`Origem_Dado = sugerida_dos_documentos`) e no **aviso A11**. Por isso o desenho não cria campo de "canal de venda": o canal é **derivado do modelo do documento** (`Cad_Modelo_Documento_Fiscal.ID_Tipo_Modelo`).

| Canal | Onde está no dicionário | Leva bico e encerrante? | Efeito no livro |
|---|---|---|---|
| **NF-e** (55) | `Mov_Nota_Fiscal_Saida` e `_Item` | Sim, nos campos `Combustivel_*` do item | Leitura sugerida por bico; A11 por bico |
| **NFC-e** (65) | `Mov_Nota_Fiscal_Saida` e `_Item` | Sim, nos mesmos campos | Idem |
| **CF-e-SAT** (59), **CF-e-ECF** (60) e **cupom de ECF** (02 e 2D) | `Mov_Nota_Fiscal_Saida` e `_Item`, com `ID_Equipamento_Fiscal` | **Os campos existem no item, mas não conferi se o leiaute do cupom os admite nem se o PDV os grava** (Q218-E8) | Se o item trouxer o bico: igual à NF-e. Se não: **só A11 por produto** |
| **Redução Z do ECF** (C405, C420, C425) | `Mov_Ecf_Reducao_Z*` | Não: só produto e quantidade do dia | **A11 por produto**, e só quando os cupons do equipamento naquele dia **não** estão gravados como documentos |

**Como o aviso A11 passa a funcionar** (substitui a redação da primeira versão):

1. **Por bico e por dia**, quando **todos** os itens de combustível vendidos naquele produto e naquele dia (de qualquer modelo) trazem `Combustivel_Numero_Bico`: soma dos volumes do bico no livro contra a soma das quantidades dos itens com o mesmo bico.
2. **Por produto e por dia**, nos demais casos: soma dos volumes de todos os bicos do produto contra a soma das quantidades dos itens de saída do produto (código da ANP), de **qualquer modelo**.
3. **Sem contar duas vezes**: se o equipamento tem os cupons do dia gravados como documentos, vale a soma dos itens; se só tem a Redução Z, vale a quantidade de `Mov_Ecf_Reducao_Z_Totalizador_Item`. **Nunca os dois** para o mesmo equipamento e o mesmo dia.
4. O aviso só informa a diferença, **sem tolerância** (C344). Venda por NF-e a pessoa jurídica (posto que vende diesel a granel, por exemplo) entra na soma como qualquer outra.

A **leitura sugerida** (seção 6.3) continua usando só itens que **trazem** bico e encerrantes. Item de cupom sem bico **não gera sugestão**; o ERP avisa (A26) e a leitura vem da automação de pista ou da digitação.

## 14.4 O distribuidor e os avisos que cruzam o papel com o documento

O dicionário **já sabe** quem é o distribuidor (autorização ANP do tipo `distribuidor`), sabe vender para ele e dele comprar (NF-e), e sabe gerar o C165 e o 0206 quando a filial está habilitada (documento 175). Este documento **não cria entidade para o distribuidor**. Acrescenta seis avisos (A22 a A27, seção 10), todos derivados, nenhum grava dado novo:

| Aviso | O que cruza | Fonte da regra |
|---|---|---|
| **A23** | Habilitação contra autorização ANP | Guia: o 1300 é do varejo e o C165 é de distribuidora, refinaria e revendedora, e o posto não o apresenta; cartilha: a revenda exige autorização |
| **A24** | Posto vende combustível a participante com autorização de `posto_revendedor` | Cartilha, vedações, 1º item: o posto não pode vender combustível a outro revendedor, "ainda que o outro estabelecimento pertença à mesma pessoa jurídica" |
| **A25** | Entrada de combustível de emitente sem autorização de fornecedor | Cartilha, item 3 (distribuidor autorizado) e seção da amostra-testemunha (distribuidor, fornecedor de etanol e TRR); a lista de tipos aceitos é **leitura minha** (C350) |
| **A26** | Venda de combustível de posto sem bico no item | Vale para NFC-e, cupom e NF-e (14.3) |

Os outros dois avisos novos (A22 e A27) vêm só da cartilha e estão em 14.5.

**O que não desenhei do distribuidor, e por quê.** (a) O **relatório de movimentação do Convênio ICMS 199/2022** (programa COTEPE, Anexo I-A, mensal), que li **só em site não oficial**, que alcança óleo diesel, biodiesel e GLP/GLGN, e que **não cita** EFD, cupom, etanol nem gasolina. (b) A **indicação do ICMS monofásico anterior** no documento (cláusula 14 do mesmo convênio): o item de saída já tem campos de combustível, mas não conferi se cobrem esse dado, e o assunto é dos documentos 170 e 173. (c) **Bases e tanques do distribuidor** e o seu controle de estoque (`Cad_Lmc_Tanque` é do posto e aponta para a filial do posto). (d) O envio de dados à ANP pelos demais elos da cadeia: uma contribuição do IBP à consulta pública cita a **Resolução ANP nº 729/2018** como o procedimento dos outros elos; **não a li**. Tudo isso depende de norma que não li e de haver cliente distribuidor (D-N68): vai ao contador (C351) e à equipe (Q218-E9).

**Tributação.** A revenda do distribuidor segue o que o documento 170 já desenhou (CBS sem crédito na revenda; o distribuidor só é contribuinte quando importa). Nada muda aqui.

## 14.5 O que a cartilha e a Resolução 884 dizem

A cartilha da ANP **não substitui as leis e os regulamentos**, como ela mesma diz. O texto da **Resolução ANP nº 884/2022** foi lido no texto do **Diário Oficial da União** (edição 171, seção 1, página 62, de 08/09/2022) que você enviou, impresso do site da Imprensa Nacional (a página ressalva que "não substitui o publicado na versão certificada"), e confere, artigo por artigo e campo por campo do Anexo, com as duas cópias não oficiais que eu tinha lido antes, com a cartilha e com o relatório da consulta. **Datas:** a ementa e a assinatura são de 05/09/2022; a publicação é de 08/09/2022; o cabeçalho do Anexo diz "8 de setembro", o que parece erro do próprio texto; a vigência é 03/10/2022 (art. 8º). A alteração posterior, se houver, vai ao contador (C336).

| O que o texto diz | Onde | O que faço |
|---|---|---|
| **Escopo:** o LMC é "documento comprobatório de estocagem e comercialização de combustíveis automotivos pelo **revendedor varejista**"; o registro é **diário**, mesmo sem movimentação | Art. 1º e parágrafo único | Confirma que o LMC é do posto e que o distribuidor não o tem. O dia é a unidade (seção 6) |
| **Conteúdo mínimo:** compras com documento fiscal; vendas com volume **por bico**; estoque; outras entradas e saídas; **preços** de compra e venda. Numeração própria e sequencial de **bombas, tanques e filtros**. Escrituração **eletrônica ou manuscrita** em livro impresso | Art. 2º | Bate com o desenho (bico, tanque, bomba). Os **filtros** não têm cadastro: o Guia só trata de tanques que passam por um filtro único (tanque representante). Os **preços** não são do EFD; ver 14.7 |
| Os dados vão à ANP, digitais ou impressos, **quando notificado** | Art. 3º | **Não desenho** o envio (limite 7) |
| O LMC dos **seis últimos meses** fica no posto, **com a documentação fiscal**, em meio digital ou físico | Art. 4º | **Não desenho** a guarda |
| **Variação do estoque físico acima de 0,6%**, sem comprovação de movimentação, obriga o revendedor a apurar as causas; a variação se mede **pelo campo 8** (perdas e ganhos); as justificativas vão em **Observações** (campo 13.5); sem causa achada, valem as normas técnicas e ambientais; **vazamento ou infiltração**: o tanque é esvaziado e retirado de operação até um profissional ou empresa especializada comprovar que pode voltar | Art. 5º e §§ 1º a 4º | **Aviso A22** e `Limite_Variacao_Percentual` (5.1), **por produto e por dia**, como o campo 8. O texto diz "0,6% do estoque físico" e **não diz qual** (abertura ou fechamento); uso o de fechamento, **leitura minha** (C349). O ERP **não preenche o 0,6% sozinho**. O tanque retirado de operação por vazamento usa `Data_Cessacao` |
| Manter arquivado o LMC da Portaria DNC 26/1992, de modo que, com o LMC novo, **os cinco anos anteriores** estejam cobertos | Art. 6º | **Não desenho** a guarda. **Corrijo a leitura da minuta:** os cinco anos são **do LMC**, não da documentação fiscal |
| Revoga a Portaria DNC 26/1992 e a Resolução ANP 23/2004 | Art. 7º | A Portaria deixa de ser fundamento |
| A cartilha manda elaborar **Termos de Abertura e de Fechamento**, "conforme tabela constante do Anexo"; o FAQ da ANP diz que o representante legal os assina | Cartilha, item 9; FAQ | **O Anexo da 884 no Diário Oficial não traz os termos** (nem as duas cópias que li antes). Não desenho (Q218-12, C356) |
| O posto só fornece combustível por **bomba medidora** aferida pelo Inmetro e mede estoque por **régua** ou equivalente | Cartilha, itens 6 e 7 | Nada novo: é o que o livro pressupõe |
| O posto **não pode ter tanque não interligado a bomba medidora**, salvo óleo usado, desativação protocolada e cisterna de água de chuva | Cartilha, vedações | **Aviso A27**. O Guia manda informar o tanque sem bico com número de bico a partir de 990; o aviso convive com isso |
| O posto **identifica em cada bomba** o nome fantasia, a razão social e o CNPJ do fornecedor; opta por exibir ou não a **marca do distribuidor** (bandeirado ou bandeira branca) | Cartilha, itens 2 e 4 | **Não desenho** o vínculo posto-distribuidor (Q218-14). A origem na bomba é o fornecedor da última entrada, **derivada** da nota |
| Compra de combustível **a granel só de distribuidor autorizado**; recebimento com **Boletim de Conformidade** e análise de qualidade, com recusa do produto fora de especificação | Cartilha, itens 3, 5 e 6 | Aviso A25. O boletim e a análise são controle de qualidade, **fora do escopo** |

**Aviso A22** (variação acima do limite): por **produto e por dia fechado**, o saldo líquido do campo 8 (estoque físico de fechamento menos escritural, somados os tanques do produto) passa do percentual do estoque físico de fechamento, ou passa sem texto em `Observacao` de algum tanque do produto no dia. O limite é o menor valor preenchido entre os tanques do produto, e o ERP avisa quando eles diferem. Só avisa; só roda com o limite preenchido.

## 14.6 O que muda nas outras seções

1. **5.1 `Cad_Lmc_Tanque`**: ganha `Limite_Variacao_Percentual` (14 campos).
2. **6.1 `Mov_Lmc_Tanque_Dia`**: `Observacao` é o campo "13) Observações" do LMC; ganha `Volume_Transferencia_Recebida` e `Volume_Transferencia_Enviada` (17 campos; 14.7, Q218-15).
3. **6.2 `Mov_Lmc_Bomba_Intervencao`**: ganha `Volume_Encerrante_Substituido`, `Volume_Encerrante_Novo` e `Numero_Relatorio_Manutencao` (12 campos; 14.7, Q218-16).
4. **6.3 `Mov_Lmc_Bico_Leitura`**: o valor `sugerida_das_notas` de `Origem_Dado` passa a `sugerida_dos_documentos`.
5. **10 Avisos**: A11 reescrito (14.3); entram **A22 a A27**; o total vai de 21 para **27**.
6. **11, 12 e 13**: contagem (9 entidades, **107 campos**; 1.229 entidades e **14.261 campos**), perguntas Q218-10 a Q218-18, C349 a C357, Q218-E8 e Q218-E9, e limites 11 a 16.

## 14.7 O que o Anexo da Resolução 884 pede e como o desenho responde

O Anexo é o **modelo da folha do LMC por produto**. O documento 218 desenha os dados do **EFD** (registros 1300 a 1391); a folha da ANP usa quase os mesmos dados. Campo a campo:

| Campo do Anexo | O que pede | De onde vem no desenho |
|---|---|---|
| 1 e 2 | Produto da folha e data | `Cad_Lmc_Tanque.ID_Produto_Servico` e `Data_Fechamento` |
| 3 e 3.1 | Estoque de abertura, medido **por um único método**; numeração dos tanques feita pela revenda; 3.1 soma dos tanques do produto | `Volume_Estoque_Abertura` e `Numero_Tanque`. O **método** não tem campo: a **mudança de método** vai em `Observacao` (13.4) |
| 4, 4.1 a 4.4 | Volume recebido, com **número e data do documento fiscal**, tanque da descarga, volume do documento, total e volume disponível (3.1 + 4.3) | C171 (`Mov_Nota_Fiscal_Entrada_Item_Tanque`) e a nota de entrada; o disponível é soma |
| 5, 5.1 a 5.7 | Vendas: tanque, **bico ou bomba**, encerrante de fechamento e de abertura (**sem decimais**), aferições, vendas do bico (5.3 − 5.4 − 5.5), soma do dia | `Mov_Lmc_Bico_Leitura` (`Leitura_Fechamento`, `Leitura_Abertura`, `Volume_Afericao`); calculado. O 1320 do Guia admite decimais; o ERP guarda o que a bomba informa |
| 6 | Estoque escritural (4.4 − 5.7) | `Volume_Estoque_Escritural` |
| 7, 8, 9, 9.1 | Estoque de fechamento (= 9.1); **perdas e ganhos = 7 − 6**, e "se negativo, investigar vazamento"; fechamento físico por tanque | `Volume_Fechamento_Fisico`; **ver o ponto (a) abaixo** |
| 10, 10.1, 10.2 | **Valor das vendas (R$)** = vendas do dia × preço na bomba; acumulado no mês | **Não está no EFD.** Ver o ponto (d) |
| 11 e 12 | Uso do revendedor; uso da fiscalização | Nada |
| 13.1 | Número de tanques, com **capacidades nominais**, e de bicos, na primeira e na última folha de cada combustível | `Cad_Lmc_Tanque.Capacidade_Litros` e `Cad_Lmc_Bico`; relatório |
| 13.2 | Instalação ou retirada de tanques e bicos | `Data_Inicio_Uso` e `Data_Cessacao` do tanque; vigência do bico |
| 13.3 | **Troca ou modificação de encerrante**, com o volume no encerrante substituído e no novo, o CNPJ e o **número do relatório de manutenção** da empresa credenciada pelo Inmetro | `Cnpj_Empresa_Interventora` já existe; **faltam os dois volumes e o número do relatório**: ponto (c) |
| 13.4 | Modificação do método de medição dos tanques | `Observacao` |
| (rotulada "e.") | **Transferência de produto entre tanques** do mesmo revendedor, sem passar pela bomba | Ponto (b) |
| 13.5 | Variações acima de 0,6% do estoque físico, com justificativa | A22 e `Observacao` |
| 13.6 | Outras informações relevantes | `Observacao` |

**Quatro pontos que o Anexo abre.**

**(a) Perdas e ganhos: saldo líquido na ANP, dois campos no Guia.** O campo 8 do Anexo é **um número só**, fechamento menos escritural, **do produto**. O 1300 do Guia tem **dois** campos (`VAL_AJ_PERDA` e `VAL_AJ_GANHO`). A leitura da primeira versão, que soma perdas e ganhos dos tanques **sem compensar**, dá para o 1300 números diferentes do campo 8 quando um tanque perde e outro ganha. **Não mudo** a fórmula do EFD, que é a única que o Guia permite ler; **o A22 usa o saldo líquido do produto**, como o Anexo. A diferença vai ao contador (C337, C349).

**(b) Transferência entre tanques.** O Anexo manda registrar em Observações a transferência de produto de um tanque a outro sem passar pela bomba. No livro, ela **não é entrada nem venda**; no produto o efeito é zero, mas **por tanque** o escritural (abertura + entrada − saídas) fica errado e gera perda num tanque e ganho no outro. **Proposta (Q218-15):** dois campos opcionais em `Mov_Lmc_Tanque_Dia`, `Volume_Transferencia_Recebida` e `Volume_Transferencia_Enviada`; o escritural do tanque vira abertura + entrada + transferência recebida − transferência enviada − saídas (**leitura minha**). O Guia **não diz** como o 1310 trata a transferência (C355).

**(c) Troca de encerrante.** O 1320 do Guia só tem número, motivo, nome, CNPJ e CPF da intervenção. O Anexo exige, na troca ou modificação do encerrante, o volume do encerrante substituído, o do novo e o número do relatório de manutenção. **Proposta (Q218-16):** três campos opcionais em `Mov_Lmc_Bomba_Intervencao` (`Volume_Encerrante_Substituido`, `Volume_Encerrante_Novo`, `Numero_Relatorio_Manutencao`); a leitura do bico no trecho seguinte parte do encerrante novo.

**(d) A folha da ANP como relatório.** Tudo o que o Anexo pede, menos o campo 10, sai dos dados acima. O **campo 10** (vendas × preço na bomba, e o acumulado do mês) e o inciso V do art. 2º (**preços** de compra e venda) pedem o **preço na bomba por produto e por dia**, que o dicionário não tem. **Proposta (Q218-17):** o ERP produz a folha do LMC da ANP como **relatório dos mesmos dados**, sem entidade nova, e o campo 10 sai da **soma dos valores dos itens vendidos** do produto no dia (**leitura minha**: pode diferir de vendas × preço na bomba por desconto ou arredondamento).

**O que continua sem leitura.** Os termos de abertura e de encerramento (a cartilha os cita no Anexo, o Anexo do Diário Oficial não os traz); o campo 4.3, que o Anexo lista sem nota explicativa (a nota 4.2 trata do volume e a 4.4 do disponível). **O item "e." entre 13.4 e 13.5 está assim no Diário Oficial**, e não é erro das cópias. A impressão do site da Imprensa Nacional não substitui a versão certificada (a própria página diz); o PDF certificado não foi lido.

## 14.8 O que a Solução de Consulta Cosit nº 223/2023 acrescenta

A página do Diário Oficial de 29/09/2023 (edição 187, seção 1, página 122) que você enviou reúne seis soluções de consulta da Cosit. **Só a nº 223, de 22/09/2023, cita a Resolução 884**; as outras cinco estão no fim desta seção.

| O que a solução diz | Onde | O que faço |
|---|---|---|
| As perdas **iguais ou inferiores a 0,6%**, relativas à **evaporação de gasolina**, "nos termos da Resolução ANP nº 884", podem **integrar o custo das mercadorias**, no **lucro real**, para o **IRPJ** e para a **CSLL** (art. 46, V, da Lei 4.506/1964), **sem outro meio de comprovação** | Ementa, nas duas partes (CSLL e IRPJ) | Nenhum campo novo. O ERP já guarda a perda por tanque e por dia (`Volume_Perda`) e compara o saldo do produto com o limite (A22) |
| A Resolução serve de **elemento probatório idôneo** de que a perda decorre da movimentação do combustível e é razoável pela natureza da mercadoria | Ementa | A justificativa em `Observacao` (art. 5º, § 2º) passa a ter também efeito fiscal; **se a Q218-18 for aprovada**, o texto do aviso A22 cita a solução de consulta |
| A solução é "**parcialmente vinculada**" à SC Cosit nº 76/2021 | Ementa | **Não li a 76/2021** (C357) |

**O que a solução não diz.** Não fala do **que passa de 0,6%**, de **outros combustíveis**, do **período** da medição nem de qual estoque é a base. A Resolução 884 diz "estoque físico" e mede pelo campo 8 (saldo do produto no dia); como essa leitura serve ao imposto, **não sei**. Também não li a dedutibilidade no **lucro presumido**, que não depende de custo.

**Leitura minha (Q218-18, C357).** O relatório do LMC mostra, por produto e por dia, a **perda dentro e fora do limite**, para o contador decidir. **Nenhum lançamento automático** e **nenhuma adição automática** ao e-Lalur: o contador diz se a parte acima do limite é indedutível, qual a conta e o código de ajuste (C357). O custo da perda dentro do limite segue o custo da mercadoria que o dicionário já tem (módulo de Estoque e Custo); este documento não o altera.

**As outras cinco soluções da página, que li e não desenhei.** (1) **SC 199/2023** (IPI): a água mineral natural dos Ex 01 e Ex 02 do código 2201.10.00 da Tipi, mesmo com gás carbônico, é **não tributada (NT)**, e o IPI não incide. (2) **SC 208/2023** (PIS e Cofins-Importação): na importação para revenda, o crédito só se ressarce ou compensa se vier da **diferença** entre a alíquota da importação e a da revenda e for apurado **a partir de 01/01/2023** (art. 15, § 2º-A, da Lei 10.865); os créditos anteriores só podem ser aproveitados nos meses seguintes. (3) **SC 218/2023** (obrigações acessórias): a pessoa jurídica que mantém plataforma de transações *peer to peer* de *utility tokens* é *exchange* e informa à Receita as transações próprias e as dos usuários (IN RFB 1.888/2019, arts. 5º e 6º), e quem emite *utility tokens* também informa. (4) **SC 219/2023** (PIS e Cofins): a carta de crédito contemplada de consórcio é documento financeiro e **não gera crédito**, na aquisição e na venda desses títulos. (5) **SC 222/2023** (IRPJ): a baixa contábil de terrenos feita só como ajuste prévio à desestatização de empresa pública federal é **indedutível** e não é perda de capital. **Nenhuma delas toca o desenho deste documento.** Não conferi se o dicionário já cobre cada uma (IN RFB 1.888, o crédito da importação para revenda, a carta de consórcio); se você quiser, verifico e trago como pergunta.

# Anexo A. Cobertura campo a campo

Todos os campos dos registros 1300 a 1391 e do C171 do Guia 3.2.4 têm origem. `REG` é texto fixo e não aparece.

## A.1 Registros 1300 e 1310

| Registro.Campo | De onde sai |
|---|---|
| 1300.COD_ITEM | `Cad_Lmc_Tanque.ID_Produto_Servico` (o código do produto no 0200) |
| 1300.DT_FECH | `Mov_Lmc_Tanque_Dia.Data_Fechamento` |
| 1300.ESTQ_ABERT | Soma de `Volume_Estoque_Abertura` dos tanques do produto |
| 1300.VOL_ENTR | Soma de `Volume_Entrada` (C171 do dia) |
| 1300.VOL_DISP | Abertura mais entrada (calculado na geração) |
| 1300.VOL_SAIDAS | Soma de `Volume_Saidas` (1320 do dia) |
| 1300.ESTQ_ESCR | Disponível menos saídas (calculado na geração) |
| 1300.VAL_AJ_PERDA | Soma de `Volume_Perda` |
| 1300.VAL_AJ_GANHO | Soma de `Volume_Ganho` |
| 1300.FECH_FISICO | Soma de `Volume_Fechamento_Fisico` |
| 1310.NUM_TANQUE | `Cad_Lmc_Tanque.Numero_Tanque` (do representante, nos interligados) |
| 1310.ESTQ_ABERT a FECH_FISICO | `Mov_Lmc_Tanque_Dia` (somados no grupo de interligados); disponível e escritural calculados |
| 1310.CAP_TANQUE | `Cad_Lmc_Tanque.Capacidade_Litros` (somada no grupo) |

## A.2 Registros 1320, 1350, 1360 e 1370

| Registro.Campo | De onde sai |
|---|---|
| 1320.NUM_BICO | `Cad_Lmc_Bico.Numero_Bico` |
| 1320.NR_INTERV | `Mov_Lmc_Bomba_Intervencao.Numero_Intervencao` |
| 1320.MOT_INTERV | `Mov_Lmc_Bomba_Intervencao.Motivo_Intervencao` |
| 1320.NOM_INTERV | `Mov_Lmc_Bomba_Intervencao.Nome_Interventor` |
| 1320.CNPJ_INTERV | `Mov_Lmc_Bomba_Intervencao.Cnpj_Empresa_Interventora` |
| 1320.CPF_INTERV | `Mov_Lmc_Bomba_Intervencao.Cpf_Tecnico` |
| 1320.VAL_FECHA | `Mov_Lmc_Bico_Leitura.Leitura_Fechamento` (ou o valor máximo, no primeiro registro da divisão) |
| 1320.VAL_ABERT | `Mov_Lmc_Bico_Leitura.Leitura_Abertura` (ou zero, no segundo registro da divisão) |
| 1320.VOL_AFERI | `Mov_Lmc_Bico_Leitura.Volume_Afericao` |
| 1320.VOL_VENDAS | Calculado: fechamento menos (abertura mais aferição) |
| 1350.SERIE | `Cad_Lmc_Bomba.Numero_Serie` |
| 1350.FABRICANTE | `Cad_Lmc_Bomba.Fabricante` |
| 1350.MODELO | `Cad_Lmc_Bomba.Modelo` |
| 1350.TIPO_MEDICAO | `Cad_Lmc_Bomba.Tipo_Medicao` (0 analógica, 1 digital) |
| 1360.NUM_LACRE | `Cad_Lmc_Bomba_Lacre.Numero_Lacre` |
| 1360.DT_APLICACAO | `Cad_Lmc_Bomba_Lacre.Data_Aplicacao` |
| 1370.NUM_BICO | `Cad_Lmc_Bico.Numero_Bico` (990 em diante no tanque sem bico) |
| 1370.COD_ITEM | O produto do tanque do bico |
| 1370.NUM_TANQUE | O número do tanque do bico (o do representante, nos interligados) |

## A.3 Registros 1390, 1391 e C171

| Registro.Campo | De onde sai |
|---|---|
| 1390.COD_PROD | `Mov_Usina_Producao_Dia.ID_Efd_Codigo_Estadual` (tabela 5.8) |
| 1391.DT_REGISTRO | `Data_Producao` |
| 1391.QTD_MOID | `Quantidade_Insumo_Esmagado` |
| 1391.ESTQ_INI | `Estoque_Inicial` |
| 1391.QTD_PRODUZ | `Quantidade_Produzida` |
| 1391.ENT_ANID_HID | `Entrada_Transformacao` |
| 1391.OUTR_ENTR | `Outras_Entradas` |
| 1391.PERDA | `Perda` |
| 1391.CONS | `Consumo` |
| 1391.SAI_ANI_HID | `Saida_Transformacao` |
| 1391.SAIDAS | `Saidas` |
| 1391.ESTQ_FIN | `Estoque_Final` |
| 1391.ESTQ_INI_MEL | `Estoque_Inicial_Mel` |
| 1391.PROD_DIA_MEL | `Producao_Mel` |
| 1391.UTIL_MEL | `Utilizacao_Mel` |
| 1391.PROD_ALC_MEL | `Producao_Do_Mel` |
| 1391.OBS | `Observacao` |
| 1391.COD_ITEM | `ID_Produto_Servico_Insumo` |
| 1391.TP_RESIDUO | Derivado das três quantidades (seção 8.2) |
| 1391.QTD_RESIDUO | Derivado das três quantidades (seção 8.2) |
| 1391.QTD_RESIDUO_DDG | `Quantidade_Residuo_Ddg` |
| 1391.QTD_RESIDUO_WDG | `Quantidade_Residuo_Wdg` |
| 1391.QTD_RESIDUO_CANA | `Quantidade_Residuo_Bagaco` |
| C171.NUM_TANQUE | `Mov_Nota_Fiscal_Entrada_Item_Tanque.ID_Lmc_Tanque` (o número do tanque) |
| C171.QTDE | `Mov_Nota_Fiscal_Entrada_Item_Tanque.Quantidade_Armazenada` |
