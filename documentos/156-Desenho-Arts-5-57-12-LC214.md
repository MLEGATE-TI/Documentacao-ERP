# Desenho dos arts. 5º, 57 e 12 da LC 214 (com a LC 227): operação equiparada, uso ou consumo pessoal e base de cálculo — Documento 156

*Primeiro dos seis desenhos que você liberou com o reenvio da LC 214, da LC 227 e do Decreto 12.955 (Q161-4). Este documento refaz o 156 perdido e vale como o desenho único dos três artigos que a Q138-4 pedia. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

Li os três artigos **no texto consolidado** da LC 214 (com as marcas da LC 227) e **o que o Decreto 12.955 regulamenta**, e conferi o que o dicionário já tem. O desenho acrescenta **13 entidades novas** e altera **9 existentes** (7 com campos ou valores novos e 2 só de texto). Nenhum campo é removido. Todas as entidades novas ficam na Contabilidade & Fiscal.

| Artigo | O que a LC 227 mudou | O que o dicionário tinha | O que este documento acrescenta |
|---|---|---|---|
| **5º** (operação equiparada) | Inciso I reescrito (alíneas a, b e c, com cônjuges, companheiros e parentes até o 3º grau); §§ 8º, 9º e 10 novos | `Cad_Regra_Operacao_Equiparada_Cbs`, `Tipo_Onerosidade`, regra no participante (D-N285 a D-N290) | "Valor inferior ao de mercado", exceção do uso preponderante, tributação pelo valor de mercado, dois tipos novos de operação, extensão 1:1 do item de saída |
| **57** (uso ou consumo pessoal) | Alínea g nova; inciso II só com bens e serviços **adquiridos**; § 3º, IV, f e h; §§ 4º, 6º e 7º **revogados**; § 9º novo | Só o valor `uso_consumo_pessoal` no estoque de abertura (D-N158 e D-N166) | Catálogo de hipóteses e de critérios, registro por item da aquisição, estorno pelo documento fiscal vinculado, exclusão da base na alienação |
| **12** (base de cálculo) | § 9º novo (energia elétrica multilateral, CCEE) | Cálculo disperso (NFS-e, locação, bem usado); os nomes do B0a-1 e B0a-2 não existem no dicionário | Regra de composição da base, valor de mercado em três entidades, conversão cambial, base especial (derivativo, dação, transporte internacional, alienação), liquidação da CCEE |

**Três achados que mudam o que estava escrito antes.**

1. **A D-N290 não conflita com a LC 227.** O documento 138 leu a D-N290 ("sem vínculo de parentesco") como conflito com os parentes até o 3º grau. A D-N290 diz outra coisa: dispensa **tipos novos de vinculação** e consulta ao quadro societário; ela já cita "parentes" e manda decidir tudo no cadastro do participante. Mantenho a decisão como está (Q156-1).
2. **O brinde a preço de aquisição está no Decreto.** A D-N285 anotou que a base presumida do brinde "não foi conferida". Conferi: o art. 14, § 8º do Decreto diz que o valor de mercado do brinde é o preço de aquisição. O Decreto também define brinde e bonificação (art. 5º, § 1º), definições que a LC não traz.
3. **A numeração do Decreto não segue a da LC.** O art. 57 da LC é regulamentado pelos arts. 62 a 64 do Decreto, e o art. 12 da LC pelos arts. 13 e 14. O art. 57 do **Decreto** trata de devolução e cancelamento, e o art. 12 do **Decreto** trata do local da operação. Quando os documentos 94 e 115 falam do B0a-1 ("arts. 11, 13 e 57 a 64"), são artigos do Decreto. Daqui em diante cito sempre os dois, "LC" e "Decreto".

# 2. Regras que segui

1. **Parâmetro com vigência, sem valor escondido.** Percentuais, prazos e listas da lei (25% de desconto, 31 dias, 50% do transporte internacional, seis meses do plano de saúde) ficam em tabelas com `Vigencia_Inicio` e `Vigencia_Fim`, nunca no código.
2. **As condições do Motor são colunas, não texto livre** (Q90-5).
3. **Carga provisória.** Toda linha de carga entra com `Situacao_Dado = provisorio` até o contador validar, com o artigo da LC e o do Decreto no fundamento.
4. **O Motor sugere e o usuário confirma, sem bloquear** (padrão da Q116-8 e da D-N286/D-N287): classificar como uso pessoal, aplicar a exceção do uso preponderante ou aceitar o valor de mercado exige a confirmação do usuário com a ação `aprovar`, e a falta de dado vira aviso.
5. **O ERP só registra.** O que se deriva (valor total de mercado, valor excluído na alienação) não ganha coluna redundante quando já sai de outros campos; guardo só o que muda por data ou por decisão.
6. **Extensão 1:1 para o que a minoria dos itens usa** (padrão da D-N67).
7. **Uma regra legal, uma tabela.** Os critérios de uso preponderante servem ao art. 57, § 3º e ao art. 5º, § 8º; ficam numa tabela só.
8. **Nomes** em português com sublinhado; o prefixo `Valor_` só nos campos número, referência, texto e enumeração (regra H2 da auditoria).
9. **Onde o Decreto vai além da LC**, a linha de carga traz `Origem_Regra = decreto` e vai para o contador conferir; não escondo a diferença.

# 3. Desenho do art. 5º: operação equiparada

## 3.1 O que o texto pede

O art. 5º da LC 214 diz que o IBS e a CBS **também** incidem sobre: **(I)** fornecimento não oneroso ou a valor inferior ao de mercado de bens e serviços, em três alíneas (a: adquiridos com crédito, para o próprio contribuinte pessoa física, sócios, acionistas, administradores, conselheiros, empregados e seus cônjuges, companheiros e parentes até o 3º grau; b: produzidos ou prestados pelo contribuinte para as mesmas pessoas, menos o próprio contribuinte; c: demais hipóteses da lei); **(II)** brindes e bonificações; **(III)** transmissão a sócio ou acionista que não seja contribuinte do regime regular; **(IV)** demais fornecimentos não onerosos ou a valor inferior ao de mercado a parte relacionada.

A LC 227 acrescentou três regras que o dicionário não tinha: o **§ 8º** (as alíneas a e b não alcançam bens e serviços usados preponderantemente na atividade, pelos critérios do art. 57, § 3º, IV e V), o **§ 9º** (a tributação das alíneas a e b é "em montante equivalente" ao IBS e à CBS sobre o **valor de mercado**) e o **§ 10** (o regulamento dispõe sobre critérios simplificados e opcionais para a **utilização temporária** pelas pessoas físicas). O **§ 7º** (já existente) deixa o regulamento flexibilizar a verificação do valor de mercado entre partes relacionadas, em programas de conformidade.

O Decreto 12.955 repete o art. 5º (com os parágrafos deslocados: o § 2º da LC é o § 3º do Decreto), **define brinde e bonificação** (§ 1º), fixa o valor de mercado do brinde no **preço de aquisição** (art. 14, § 8º) e remete o § 8º aos critérios do art. 63, §§ 1º e 2º. Ele **não regulamenta** o § 7º nem o § 10 da LC: o art. 5º do Decreto termina no § 9º.

## 3.2 O que decidi

**Mantenho a regra no cadastro do participante** (D-N286, D-N287 e D-N290). O campo `Regra_Fornecimento_Gratuito_Cbs` com `equiparado_art5` continua sendo o que diz "este participante é sócio, administrador, empregado ou parente do art. 5º, I". O Motor escolhe a alínea pelo **item**: se o bem foi adquirido com crédito, é a alínea a; se foi produzido ou o serviço foi prestado pelo contribuinte, é a alínea b. As duas alíneas viram dois valores novos no domínio `tipo_operacao_equiparada`, porque a carga de cada uma é diferente (a alínea a exige crédito na aquisição; a b não).

**"Valor inferior ao de mercado" vira um valor novo de `Tipo_Onerosidade`** (`valor_inferior_mercado`) e uma **extensão 1:1 do item de saída**, no padrão da D-N67, porque só uma minoria dos itens é equiparada.

**A exceção do § 8º** usa a tabela de critérios do art. 57 (capítulo 4): o item da extensão aponta o critério aplicado, e o Tipo_Onerosidade volta a `nao_oneroso`.

## 3.3 Entidade nova: `Mov_Nota_Fiscal_Saida_Item_Equiparada` (extensão 1:1 do item de saída)

Uma linha por item de saída que o Motor tratou como operação equiparada, ou que seria e foi liberado pela exceção do § 8º. Fica na Contabilidade & Fiscal. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Item` | referência (`Mov_Nota_Fiscal_Saida_Item`) --- identidade | A chave é a do item (1:1). |
| `ID_Regra_Operacao_Equiparada` | referência (`Cad_Regra_Operacao_Equiparada_Cbs`) | A linha da regra, na versão que valia na data da operação. Dela vêm o tipo (brinde, bonificação, alínea a ou b, retirada por sócio, parte relacionada) e o critério da base. |
| `Valor_Praticado` | número | O que foi cobrado pelo item (zero quando não oneroso). Serve para comparar com o valor de mercado e identificar o "valor inferior". |
| `ID_Apuracao_Valor_Mercado` | referência (`Mov_Valor_Mercado_Apuracao`), opcional | O valor de mercado aplicado (§ 9º do art. 5º). Obrigatório quando a regra pede base em valor de mercado ou em preço de aquisição. Sem ele, a geração **avisa** e a operação fica pendente, sem bloquear. |
| `Bonificacao_Sem_Evento_Posterior` | booleano, opcional | Só para bonificação: o desconto em bens consta do documento fiscal e não depende de evento posterior (art. 5º, § 1º, I da LC; § 2º, I do Decreto). Sem o registro, a regra trata como tributada. |
| `ID_Criterio_Uso_Preponderante` | referência (`Cad_Criterio_Uso_Preponderante`), opcional | Preenchido quando a exceção do § 8º foi aplicada. Só aceita critério com `Aplica_Art5_Par8 = verdadeiro`. |
| `ID_Usuario_Confirmacao` | referência (`Cad_Usuario`), opcional | Quem confirmou a exceção ou o valor de mercado. Exige a ação `aprovar` (D-N287). |
| `Data_Hora_Confirmacao` | data/hora, opcional | Quando confirmou. |

## 3.4 Alterações em entidades existentes

**`Cad_Regra_Operacao_Equiparada_Cbs` (altera; entidade com vigência)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Alcanca_Valor_Inferior_Mercado` | booleano | A regra vale também quando o fornecimento é a valor inferior ao de mercado (inciso I e inciso IV), e não só quando é gratuito. |
| `Exige_Credito_Na_Aquisicao` | booleano | O bem só entra se a aquisição permitiu crédito (inciso I, alínea a, e inciso III). O Motor lê isso do crédito do item. |
| `Aplica_Excecao_Preponderancia` | booleano | A regra admite a exceção do § 8º (só as alíneas a e b do inciso I). |
| `Tributa_Se_Aliquota_Especifica` | booleano | O § 1º, II diz que o bem em bonificação com alíquota específica por unidade de medida continua tributado, mesmo constando do documento. Verdadeiro na bonificação. |
| `Permite_Dispensa_Verificacao_Conformidade` | booleano | Gancho do § 7º: o regulamento **poderá** flexibilizar a verificação do valor de mercado entre partes relacionadas em programas de conformidade. Nasce `falso`, porque o Decreto não regulamentou. |
| `Prazo_Maximo_Dias` | número, opcional | Amostra grátis de serviço ou bem imaterial: período máximo de 31 dias corridos (Decreto, art. 6º, § 4º, II). Achei ao ler o art. 6º; o campo evita um valor legal no código. |

O domínio `tipo_operacao_equiparada` ganha os valores `fornecimento_art5_i_a` e `fornecimento_art5_i_b`. O campo `Fundamento_Legal` passa a trazer **os dois artigos** (por exemplo, "LC 214, art. 5º, § 1º, I; Decreto 12.955, art. 5º, § 2º, I"), porque a numeração difere. A carga completa está no Anexo B.

**`Mov_Nota_Fiscal_Saida_Item` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `Tipo_Onerosidade` | enumeração {oneroso, nao_oneroso, equiparado, valor_inferior_mercado}, opcional | Valor novo `valor_inferior_mercado`: o item tem valor, mas abaixo do valor de mercado, para participante com regra `equiparado_art5` ou parte relacionada. O Motor compara `Valor_Praticado` com o valor de mercado apurado. |

**`Cad_Participante` (altera só o texto)**

A descrição de `Regra_Fornecimento_Gratuito_Cbs` passa a dizer que `equiparado_art5` cobre as **alíneas a e b** do inciso I (a LC 227 inclui cônjuges, companheiros e parentes até o 3º grau), que a categoria do beneficiário fica no `Fundamento` em texto (D-N290), que a exceção do § 8º é decidida no item, e que a tributação é pelo valor de mercado (§ 9º), sem opção e sem perguntar.

## 3.5 O que o art. 5º deixa sem desenho

- **§ 7º (flexibilização por programa de conformidade):** só o gancho `Permite_Dispensa_Verificacao_Conformidade`, com carga `falso`.
- **§ 10 (critérios simplificados para utilização temporária por pessoa física):** o Decreto não regulamentou. Não crio campo; entra como pendência (seção 7).
- **Alínea c do inciso I ("demais hipóteses previstas na lei"):** não precisa de valor próprio; cada hipótese tem a sua regra.

# 4. Desenho do art. 57: uso ou consumo pessoal

## 4.1 O que o texto pede

A LC 214 (art. 57) lista o que é de **uso ou consumo pessoal**: joias, pedras e metais preciosos; obras de arte e antiguidades; bebidas alcoólicas; derivados do tabaco; armas e munições; bens e serviços recreativos, esportivos e estéticos; e, desde a LC 227, os **bens e serviços relacionados** à aquisição ou manutenção desses bens (alínea g). Também são de uso pessoal os bens e serviços **adquiridos** pelo contribuinte e fornecidos de forma não onerosa ou a valor inferior ao de mercado ao próprio contribuinte pessoa física, a sócios, acionistas, administradores, conselheiros, empregados e seus cônjuges, companheiros e parentes até o 3º grau (inciso II). Entram ainda, "entre outros", o imóvel residencial e o veículo com o que se relaciona a eles (§ 1º) e, no *family office*, os bens e serviços de gestão (§ 2º). O § 5º veda o crédito.

**O que a LC 227 tirou ou moveu.** O inciso II falava em bens "adquiridos **ou produzidos**"; agora só fala em **adquiridos**. O bem produzido pelo contribuinte e dado a sócio ou empregado passou para o art. 5º, I, b, que só tributa (capítulo 3). A LC 227 **revogou o § 4º** (pessoa física sem relação com a atividade), **o § 6º** (débito equivalente ao crédito tomado, com acréscimos) e **o § 7º** (débito proporcional ao tempo de vida útil na utilização temporária). Criou o **§ 9º**: quem aliena bem que não permitiu crédito na aquisição pode excluir da base o valor de aquisição, até o valor da alienação, se identificar o bem sem dúvida.

**O que o Decreto traz** (arts. 62 a 64): repete a lista, **acrescenta critérios para serviços** recreativos, esportivos e estéticos (art. 62, parágrafo único, IV), acrescenta a **locação** ao imóvel residencial e ao veículo (art. 63, § 3º), dá **seis meses após o fim do acordo coletivo** para o plano de saúde de empregados (art. 63, § 5º), fixa os **critérios de preponderância do § 3º, V da LC** (art. 63, § 2º, I a IV, com o inciso V delegado a ato conjunto da RFB e do CGIBS) e regulamenta o **estorno**: documento fiscal **vinculado ao de aquisição**, com o valor da CBS e a **pessoa física destinatária** (art. 64, § 1º), e, se não for possível identificar a aquisição, ordem cronológica a partir da mais recente (art. 64, § 2º). O Decreto não diz que o dado de identificação é o CPF, não fixa prazo e não define modelo ou evento do documento; isso depende dos arts. 112 e 116 e de ato conjunto.

Os §§ 4º, 6º e 7º revogados **não são citados** em nenhum texto do dicionário (conferi o D-N158, o D-N166 e o estoque de abertura), então a revogação não obriga a corrigir nada. O que a LC 227 revogou no § 4º reaparece, em parte, no art. 4º, § 6º do Decreto: a pessoa física contribuinte, em bens e serviços "não relacionados ao desenvolvimento de sua atividade econômica", sujeita-se às regras dos não contribuintes. Trato como uma hipótese à parte (linha 12 da carga, Anexo C) e deixo para o contador (Q156-10).

## 4.2 Entidade nova: `Cad_Criterio_Uso_Preponderante` (catálogo com vigência)

Um catálogo só serve aos dois artigos: o art. 57, § 3º (o que **não** é uso pessoal por ser preponderante na atividade) e o art. 5º, § 8º (a exceção da equiparação). Fica na Contabilidade & Fiscal. **Tem vigência.** A carga proposta tem **21 linhas** (Anexo A), das quais 13 têm base na própria LC (os incisos I a III e IV do § 3º, com o detalhe do Decreto) e 8 só no Decreto (os três critérios de serviços recreativos, esportivos e estéticos e os cinco do § 2º do art. 63, que a LC remete ao regulamento).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Criterio_Uso_Preponderante` | identificador | Chave da linha. |
| `Codigo_Criterio` | código (10) --- identidade | `UP-01` a `UP-21` na carga inicial. |
| `ID_Grupo_Criterio` | referência (`Cad_Classe_Sistema`, domínio = `grupo_criterio_uso_preponderante`) | `bem_art57_i` (§ 3º, I a III), `beneficio_empregado` (§ 3º, IV; Decreto, art. 63, § 1º), `criterio_regulamento` (§ 3º, V; Decreto, art. 63, § 2º) e `servico_recreativo` (Decreto, art. 62, parágrafo único, IV). Domínio aberto, com vigência. |
| `Descricao` | texto | O que o critério diz, em palavras do dicionário. |
| `Tipo_Item_Alcancado` | enumeração {bem, servico, ambos} | |
| `Aplica_Art57_Par3` | booleano | O critério exclui o item do uso pessoal do art. 57. |
| `Aplica_Art5_Par8` | booleano | O critério vale também para a exceção do § 8º do art. 5º. Só os grupos de benefício a empregado e de critério do regulamento (a LC remete aos incisos IV e V do § 3º). |
| `Exige_Comercializacao_Ou_Insumo` | booleano | O bem é comercializado ou usado na fabricação de bens a comercializar (§ 3º, I, e I do parágrafo único do art. 62). |
| `Exige_Atividade_Preponderante_Do_Adquirente` | booleano | A atividade preponderante do adquirente é a do bem ou serviço (empresa de segurança; prestador do mesmo serviço). O Motor lê o CNAE da empresa e o usuário confirma. |
| `Exige_Uso_Exclusivo_No_Estabelecimento_Do_Cliente` | booleano | Usado exclusivamente em estabelecimento físico pelos clientes. |
| `Exige_Fornecimento_Oneroso_A_Clientes` | booleano | Serviço fornecido onerosamente aos clientes (Decreto, art. 62, parágrafo único, IV, b). |
| `Exige_Uso_No_Estabelecimento_Do_Contribuinte` | booleano | Disponibilizado no estabelecimento do contribuinte (alimentação, saúde, creche). |
| `Exige_Durante_Jornada` | booleano | Durante a jornada de trabalho. |
| `Exige_Acordo_Ou_Convencao_Coletiva` | booleano | Decorre de acordo ou convenção coletiva (o Decreto, no plano de saúde, diz "cláusula compulsória"). |
| `Meses_Apos_Fim_Acordo` | número, opcional | Janela depois do fim do acordo (6, no plano de saúde; Decreto, art. 63, § 5º). |
| `Exige_Oferta_A_Todos_Empregados` | booleano | Benefício educacional oferecido a todos, com diferenciação permitida só a favor dos de menor renda ou maior núcleo familiar. |
| `Exige_Compatibilidade_Funcao_E_Quantidade` | booleano | As características e a quantidade do bem são compatíveis com as funções do empregado (veículo, informática, comunicação, transporte, telefonia, dados). |
| `Percentual_Desconto_Maximo` | número, opcional | Desconto especial a pessoas do inciso II do caput: até 25% (Decreto, art. 63, § 2º, IV, b). |
| `Exige_Preco_Nao_Inferior_Custo` | booleano | Revenda de bem material: preço não inferior ao custo de aquisição (Decreto, art. 63, § 2º, IV, a). |
| `Credito_Igual_Debito_Fornecedor` | booleano | O crédito do adquirente é igual ao débito do fornecedor, apurado e extinto no regime específico de planos de saúde ou de serviços financeiros (plano de saúde e vales). Liga ao B0b-2 e ao B4. |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | De onde vem o critério. O que só o Decreto traz vai para o contador. |
| `Fundamento_Legal` | texto | Os dois artigos, LC e Decreto. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória. |
| `ID_Instancia_Aprovacao` | referência (`Mov_Aprovacao_Instancia`), opcional | A validação. |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto opcional | Convenção da Fase 0 (31/12/9999 quando em aberto). |

**Ato conjunto.** O inciso V do § 2º do art. 63 do Decreto manda listar outros critérios em ato conjunto da RFB e do CGIBS. O catálogo aceita a linha nova sem alterar a tabela (`Origem_Regra = ato_conjunto`); **não há carga** até o ato existir.

## 4.3 Entidades novas: `Cad_Regra_Uso_Consumo_Pessoal` e `Cad_Regra_Uso_Consumo_Pessoal_Codigo`

**`Cad_Regra_Uso_Consumo_Pessoal`** guarda as **hipóteses** do art. 57 (12 linhas na carga, Anexo C). **Tem vigência.**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Uso_Consumo_Pessoal` | identificador | Chave da linha. |
| `ID_Hipotese_Uso_Pessoal` | referência (`Cad_Classe_Sistema`, domínio = `hipotese_uso_consumo_pessoal`) --- identidade | joias, obras de arte, bebidas alcoólicas, derivados do tabaco, armas e munições, recreativos, esportivos e estéticos, relacionados (alínea g), fornecido a pessoa do inciso II, imóvel residencial, veículo, *family office* e pessoa física contribuinte fora da atividade. Domínio aberto. |
| `Tipo_Item_Alcancado` | enumeração {bem, servico, ambos} | |
| `Classifica_Por` | enumeração {codigo_ncm_nbs, destinatario, natureza_do_bem, perfil_da_empresa} | Como o Motor reconhece a hipótese: pelos códigos do filho (alíneas a a f), pelo destinatário (inciso II), pelo tipo de bem (imóvel e veículo) ou pelo perfil (*family office*). |
| `Admite_Excecao_Preponderancia` | booleano | A hipótese admite os critérios do catálogo (§ 3º). |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | |
| `Fundamento_Legal` | texto | LC e Decreto. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

**`Cad_Regra_Uso_Consumo_Pessoal_Codigo`** (filho 1:N) guarda os códigos NCM ou NBS que o Motor usa para **sugerir** a hipótese.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Codigo` | identificador | |
| `ID_Regra_Uso_Consumo_Pessoal` | referência (`Cad_Regra_Uso_Consumo_Pessoal`) | A hipótese. |
| `Tipo_Codigo` | enumeração {ncm, nbs} | |
| `Prefixo_Codigo` | código (10) | Prefixo do código (capítulo, posição ou código inteiro). |
| `Situacao_Dado` | enumeração {provisorio, validado} | |

A lista de partida está no Anexo C e é **só uma proposta**: capítulos 71, 97 e 93, e posições de bebidas e de tabaco. O contador valida e ajusta (por exemplo, o álcool etílico da posição 22.07) e preenche a lista dos bens e serviços recreativos, esportivos e estéticos, que não tem NCM natural (Q156-C1). O Motor **sugere**; quem classifica é o usuário, com a ação `aprovar`.

## 4.4 Entidade nova: `Mov_Uso_Consumo_Pessoal_Item` (registro por item da aquisição)

Uma linha por item adquirido que o Motor sugeriu ou o usuário classificou, com o resultado, o crédito e o estorno. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Uso_Consumo_Pessoal_Item` | identificador | |
| `ID_Empresa` | referência (`Cad_Empresa`) | O contribuinte. |
| `ID_Item_Nota_Entrada` | referência (`Mov_Nota_Fiscal_Entrada_Item`), opcional | A aquisição, quando a nota está no ERP. |
| `Chave_Dfe_Aquisicao` | código (até 50), opcional | A chave do documento de aquisição, quando a nota não está no ERP. Um dos dois é obrigatório, salvo no estorno por ordem cronológica. |
| `Data_Aquisicao` | data | |
| `ID_Regra_Uso_Consumo_Pessoal` | referência (`Cad_Regra_Uso_Consumo_Pessoal`), opcional | A hipótese do art. 57. |
| `Resultado_Classificacao` | enumeração {uso_consumo_pessoal, preponderante_atividade, a_confirmar} | `a_confirmar` é o estado inicial da sugestão do Motor. |
| `ID_Criterio_Uso_Preponderante` | referência (`Cad_Criterio_Uso_Preponderante`), opcional | Obrigatório quando o resultado é `preponderante_atividade`. |
| `Origem_Classificacao` | enumeração {sugerido_motor, informado_usuario} | |
| `ID_Usuario_Confirmacao` | referência (`Cad_Usuario`), opcional | Exige a ação `aprovar`. |
| `Data_Hora_Confirmacao` | data/hora, opcional | |
| `ID_Participante_Destinatario` | referência (`Cad_Participante`), opcional | A pessoa física destinatária (art. 64, § 1º, II do Decreto). Sem ela, e sendo uso pessoal, a geração **avisa**. |
| `Quantidade` | número, opcional | Para o estorno proporcional. |
| `Credito_Ja_Apropriado` | booleano | Verdadeiro quando o crédito já foi tomado antes da classificação; só então há estorno. |
| `ID_Credito_Fiscal` | referência (`Mov_Credito_Fiscal`), opcional | O crédito a estornar. |
| `Estorno_Por_Ordem_Cronologica` | booleano | Verdadeiro quando não se identifica a aquisição e o valor sai da mais recente para a mais antiga (Decreto, art. 64, § 2º). |
| `Valor_Cbs_Credito_Estornar` | número, opcional | O valor da CBS a estornar (Decreto, art. 64, § 1º, I). |
| `Valor_Ibs_Credito_Estornar` | número, opcional | O do IBS, quando o regulamento do CGIBS vier. |
| `Valor_Acrescimos` | número, opcional | Acréscimos do art. 27, §§ 2º a 4º do Decreto, calculados pelo parâmetro do B0a (documento 157). |
| `ID_Documento_Fiscal_Estorno` | referência (`Mov_Documento_Fiscal`), opcional | O documento fiscal vinculado ao de aquisição. O modelo e o evento **dependem de ato conjunto** (Decreto, arts. 112 e 116). |
| `Status` | enumeração {calculado, lancado, cancelado} | `lancado` quando o estorno entrou na apuração. |

## 4.5 Entidade nova: `Mov_Uso_Consumo_Pessoal_Alienacao` (art. 57, § 9º)

Registra a exclusão da base na venda de bem que não permitiu crédito. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Alienacao` | identificador | |
| `ID_Uso_Consumo_Pessoal_Item` | referência (`Mov_Uso_Consumo_Pessoal_Item`) | O bem adquirido sem direito a crédito. |
| `ID_Item_Nota_Saida` | referência (`Mov_Nota_Fiscal_Saida_Item`) | O item da venda. |
| `Identificacao_Bem` | texto | A identificação inequívoca do bem (número de série, chassi, matrícula ou equivalente). O Decreto exige que seja possível identificar sem dúvida. |
| `Valor_Aquisicao` | número | Valor de aquisição do bem. |
| `Valor_Alienacao` | número | Valor da venda. |
| `Valor_Exclusao_Base` | número | O menor entre os dois, gravado (como no bem usado, D-N174). Alimenta a base especial do capítulo 5. |
| `Elegivel` | booleano | Falso quando alguma condição não vale. |
| `ID_Motivo_Inelegibilidade` | referência (`Cad_Classe_Sistema`, domínio = `motivo_inelegibilidade_alienacao_uso_pessoal`), opcional | Obrigatório quando `Elegivel` é falso: `sem_identificacao_inequivoca`, `bem_permitiu_credito` ou `nao_era_uso_pessoal`. |

## 4.6 Outras alterações do capítulo

- **`Cad_Empresa_Perfil_Fiscal`:** campo novo `Atividade_Principal_Family_Office` (booleano, opcional). Verdadeiro quando a atividade principal da sociedade é a gestão de bens e ativos financeiros de pessoas físicas (art. 57, § 2º; Decreto, art. 63, § 4º). Vazio quer dizer que a empresa não declarou. A hipótese de *family office* da carga só vale com ele verdadeiro.
- **`Mov_Estoque_Abertura_Cbs_Item` (só texto):** a descrição de `ID_Motivo_Inelegibilidade` passa a citar o art. 57 **com as alterações da LC 227** e os arts. 62 a 64 do Decreto.

## 4.7 O que o art. 57 deixa sem desenho

- **Rateio de bens de uso misto:** o Decreto usa "preponderantemente" e não prevê rateio. Não crio campo.
- **Prazo do documento fiscal de estorno:** vale a regra geral dos ajustes (Decreto, art. 44, §§ 1º, 2º e 6º). O prazo próprio não existe.
- **Modelo e evento do documento vinculado:** dependem do ato conjunto; o campo `ID_Documento_Fiscal_Estorno` espera.

# 5. Desenho do art. 12: base de cálculo

## 5.1 O que o texto pede

A LC 214 (art. 12) diz que a base é o **valor da operação**, "o valor integral cobrado pelo fornecedor a qualquer título" (§ 1º), com seis parcelas que integram (acréscimos de ajuste, juros e multas, descontos **condicionais**, transporte cobrado, tributos e preços públicos, demais importâncias), e que **não integram** (§ 2º) o próprio IBS e CBS, o IPI, os descontos **incondicionais**, os reembolsos por conta e ordem com documento em nome do terceiro, o ICMS, o ISS, o PIS e a Cofins de 2026 a 2032, e a COSIP. O § 3º define desconto incondicional: o que consta do documento fiscal e não depende de evento posterior. O § 4º manda usar o **valor de mercado** quando falta o valor, o valor é indeterminado, não é em dinheiro ou a operação é entre partes relacionadas (art. 5º, IV). Os §§ 5º a 8º tratam de moeda estrangeira, derivativos fora do mercado, devolução com a mesma base e transporte internacional de passageiros (metade do valor se ida e volta forem vendidas juntas). **A LC 227 acrescentou o § 9º**: na compra de energia elétrica multilateral, a base é a liquidação financeira da CCEE, na participação proporcional dos estabelecimentos. Os incisos V e VI do § 2º **não** foram alterados pela LC 227 (conferi no texto original do DOU).

O Decreto regulamenta o art. 12 nos **arts. 13 e 14**: fixa a taxa de câmbio (PTAX de venda do dólar do dia anterior ao fato gerador, última taxa disponível, regra para outras moedas e para moeda sem cotação; art. 13, § 4º), acrescenta a **dação em pagamento** (art. 13, § 9º, sem equivalente na LC consolidada) e traz o **método do valor de mercado** (art. 14): operações dos últimos três meses com seis critérios de comparação (§ 1º), critérios sucessivos (§ 3º: operações anteriores até um ano, custo mais lucro bruto, custo mais despesas indispensáveis), bolsa (§ 4º), ativo virtual (§ 5º), permuta (§ 6º) e preço de aquisição para o brinde (§ 8º). A **forma simplificada** e a **memória de cálculo** ficam para ato conjunto (§ 7º).

## 5.2 Entidade nova: `Cad_Regra_Base_Calculo_Cbs` (regra de composição da base)

É o `Cad_Regra_Base_Calculo_Cbs` que o B0a-1 prometia. Uma linha por componente da base. **Tem vigência** (a exclusão do ICMS, ISS, PIS e Cofins só vale de 01/01/2026 a 31/12/2032; vira a janela da linha). A carga tem **19 linhas** (Anexo D). Vale para o IBS e a CBS: a lei é a mesma e o Decreto só traz a CBS; a coluna `Aplica_Ibs` deixa o IBS ligado quando o regulamento do CGIBS vier (Q156-12).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Base_Calculo` | identificador | |
| `ID_Componente_Base` | referência (`Cad_Classe_Sistema`, domínio = `componente_base_calculo_ibs_cbs`) --- identidade | Acréscimos de ajuste, juros e multas, desconto condicional, transporte cobrado, tributos e preços públicos, outras importâncias, dação em pagamento, ganho em derivativo, IBS e CBS, IPI, desconto incondicional, reembolso por conta e ordem, tributos da transição, COSIP, transporte internacional, energia da CCEE, alienação de bem sem crédito, valor de mercado e devolução. Domínio aberto. |
| `Efeito_Na_Base` | enumeração {integra, exclui, substitui, reduz_percentual, repete_base_original} | `substitui` é o valor de mercado e a liquidação da CCEE; `reduz_percentual` é a metade do transporte internacional; `repete_base_original` é a devolução (§ 7º). |
| `Percentual_Reducao` | número, opcional | 50, no transporte internacional (§ 8º). |
| `Exige_Constar_No_Documento_Fiscal` | booleano | Desconto incondicional (§ 3º). |
| `Exige_Sem_Evento_Posterior` | booleano | Idem: não depende de evento posterior. |
| `Exige_Documento_Em_Nome_Terceiro` | booleano | Reembolso por conta e ordem (§ 2º, IV). |
| `Aplica_Ibs` | booleano | A linha vale para o IBS. A carga nasce `verdadeiro` onde a LC fala em "IBS e CBS" e `falso` onde só o Decreto fala da CBS. |
| `Aplica_Cbs` | booleano | A linha vale para a CBS. |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | |
| `Fundamento_Legal` | texto | LC (art. 12) e Decreto (arts. 13 e 14). |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como no capítulo 4 | |

## 5.3 Entidades novas: valor de mercado

**`Cad_Regra_Valor_Mercado`** (catálogo com vigência) guarda os **métodos** do Decreto, na ordem em que valem. A carga tem 8 linhas (Anexo E).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Valor_Mercado` | identificador | |
| `ID_Metodo_Valor_Mercado` | referência (`Cad_Classe_Sistema`, domínio = `metodo_valor_mercado`) --- identidade | operações recentes, operações anteriores, custo mais lucro bruto, custo mais despesas, cotação de bolsa, cotação de ativo virtual, valor do bem recebido em permuta e preço de aquisição (brinde). Domínio aberto. |
| `Ordem_Aplicacao` | número | Os critérios do § 3º do art. 14 são **sucessivos**; a ordem é parâmetro. |
| `Periodo_Maximo_Meses` | número, opcional | 3 nas operações recentes (§ 1º); 12 nas anteriores (§ 3º, I, "preferencialmente"). |
| `Exige_Criterios_Comparacao` | booleano | Pede os seis critérios do § 1º: natureza e qualidade, quantidade, condições de pagamento, prazo, mercado geográfico e demais circunstâncias. |
| `Exige_Escrita_Contabil` | booleano | Custo mais lucro bruto "apurado com base na escrita contábil ou fiscal". |
| `Depende_De_Ato_Conjunto` | booleano | Bolsa e ativo virtual: as bolsas e as prestadoras são definidas em ato conjunto (§§ 4º e 5º). |
| `Fundamento_Legal` | texto | LC e Decreto. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

**`Mov_Valor_Mercado_Apuracao`** é a apuração de um valor de mercado, com a memória de cálculo. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Apuracao_Valor_Mercado` | identificador | |
| `ID_Empresa` | referência (`Cad_Empresa`) | |
| `ID_Item_Origem` | referência genérica, opcional | O item da nota, o título ou o documento a que o valor se refere. |
| `ID_Produto_Servico` | referência (`Cad_Produto_Servico`) | |
| `ID_Hipotese_Valor_Mercado` | referência (`Cad_Classe_Sistema`, domínio = `hipotese_valor_mercado`) | falta de valor, operação sem valor determinado, valor não em dinheiro, parte relacionada (art. 5º, IV), fornecimento do art. 5º, I, brinde e permuta. |
| `ID_Regra_Valor_Mercado` | referência (`Cad_Regra_Valor_Mercado`) | O método aplicado. |
| `Data_Referencia` | data | O fato gerador. |
| `Quantidade` | número | O valor total de mercado sai de quantidade vezes o unitário e não é gravado. |
| `Valor_Mercado_Unitario` | número | |
| `Periodo_Amostra_Inicio`, `Periodo_Amostra_Fim` | data, opcionais | O período das operações comparadas. |
| `Valor_Custo_Total` | número, opcional | Custo direto e indireto, nos métodos de custo. |
| `Percentual_Lucro_Bruto` | número, opcional | No método custo mais lucro bruto. |
| `Valor_Despesas_Indispensaveis` | número, opcional | No método custo mais despesas. |
| `Fonte_Cotacao` | texto, opcional | A bolsa ou a prestadora de ativos virtuais. |
| `Criterios_Considerados` | texto, opcional | Quais dos seis critérios do § 1º foram usados. |
| `Memoria_Calculo` | texto, opcional | A memória. **A forma definitiva depende de ato conjunto** (art. 14, § 7º, IV); até lá é texto. |
| `Situacao` | enumeração {calculado, confirmado, substituido} | |
| `ID_Usuario_Confirmacao` | referência (`Cad_Usuario`), opcional | Exige a ação `aprovar`. |
| `Data_Hora_Confirmacao` | data/hora, opcional | |

**`Mov_Valor_Mercado_Comparavel`** (filho 1:N) guarda as operações comparadas.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Comparavel` | identificador | |
| `ID_Apuracao_Valor_Mercado` | referência (`Mov_Valor_Mercado_Apuracao`) | |
| `Origem_Comparavel` | enumeração {operacao_propria, cotacao_externa, informado_usuario} | As operações de **terceiros** ficam na base da administração tributária (art. 14, § 2º); o contribuinte só tem as suas e o que informar. |
| `ID_Documento_Fiscal` | referência (`Mov_Documento_Fiscal`), opcional | A nota da operação própria. |
| `Data_Operacao` | data | |
| `Quantidade` | número | |
| `Valor_Unitario` | número | |
| `Parte_Nao_Relacionada` | booleano | A contraparte não é parte relacionada (a LC compara com "partes não relacionadas"). |
| `Descricao` | texto, opcional | |

**Imóveis** ficam fora: o art. 364 do Decreto (valor de referência do Sinter) é do B0a-2 (`Cad_Valor_Mercado_Locacao_Parametro`, documento 157).

## 5.4 Entidade nova: `Mov_Apuracao_Tributo_Item_Base_Especial`

As parcelas que **não vêm do campo da nota** (valor de mercado, ganho em derivativo, dação em pagamento, metade do transporte internacional, liquidação da CCEE, exclusão da alienação do art. 57, § 9º) entram como linha filha da apuração do item, apontando a regra da base. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Base_Especial` | identificador | |
| `ID_Apuracao_Tributo_Item` | referência (`Mov_Apuracao_Tributo_Item`) | A linha de apuração (item e tributo). |
| `ID_Regra_Base_Calculo` | referência (`Cad_Regra_Base_Calculo_Cbs`) | A regra e a versão aplicadas. |
| `Valor_Ajuste` | número | Com sinal: positivo integra, negativo exclui. |
| `Percentual_Aplicado` | número, opcional | 50, no transporte internacional. |
| `ID_Origem` | referência genérica, opcional | A apuração de valor de mercado, a alienação do art. 57 ou a liquidação da CCEE. |
| `Observacao` | texto, opcional | Para o derivativo e a dação, que não têm entidade de origem no dicionário. O Decreto não fixa critério para dizer que o derivativo está "fora de condições de mercado" (Q156-C4). |

## 5.5 Entidade nova: `Cad_Regra_Conversao_Cambial_Base` e campos nos documentos

**`Cad_Regra_Conversao_Cambial_Base`** (parâmetro com vigência) diz como converter o valor em moeda estrangeira para a base.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Regra_Conversao_Cambial` | identificador | |
| `Aplica_Em` | enumeração {operacao_geral, importacao_bens_materiais} | A importação de bens usa a taxa do Imposto de Importação, sem ajuste posterior (Decreto, art. 81); é do B1. |
| `Tipo_Taxa` | enumeração {ptax_venda, taxa_imposto_importacao} | |
| `Defasagem_Dias_Fato_Gerador` | número | -1: o dia imediatamente anterior ao fato gerador (Decreto, art. 13, § 4º, I). |
| `Usa_Ultima_Taxa_Disponivel` | booleano | Na falta de divulgação (inciso II). |
| `Converte_Via_Dolar` | booleano | Moeda sem cotação no País: converte para dólar e depois aplica a regra (inciso IV). |
| `ID_Moeda_Intermediaria` | referência (`Cad_Moeda`), opcional | USD. |
| `Fundamento_Legal` | texto | LC, art. 12, § 5º; Decreto, art. 13, § 4º. |
| `Situacao_Dado`, `ID_Instancia_Aprovacao`, `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | como acima | |

A série de cotação já existe (`Cad_Serie_Cotacao`, tipo taxa de câmbio, fonte Banco Central). O que falta é a nota guardar a taxa usada.

**Variação cambial: onde fica cada parte (regra de Alberto na Q156-8, 04/11/2026).** A nota de saída e a DPS guardam o valor **convertido na data do fato gerador**, pela taxa da regra acima; esse é o valor da venda e o que forma a base. A **variação cambial da venda é esse valor convertido na data**: a nota não calcula nem guarda variação posterior. A variação do **recebimento ou do pagamento** vem da **baixa do contas a pagar e receber**: `Mov_Titulo_Baixa` com a `Taxa_Cambio` do contrato de câmbio (documentos 101 e 121), que lança a variação cambial realizada no lote da baixa. A taxa do contrato **não volta à nota** e **não muda a base** do IBS e da CBS. Sem campo novo por causa desta regra.

**`Mov_Nota_Fiscal_Saida` (altera)**

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Moeda_Operacao` | referência (`Cad_Moeda`), opcional | A moeda em que a operação foi contratada, quando não é o real. |
| `Valor_Operacao_Moeda` | número, opcional | O valor na moeda estrangeira. |
| `Taxa_Cambio_Base` | número, opcional | A taxa aplicada à base, pela regra acima. |
| `Data_Cotacao_Base` | data, opcional | A data da cotação (o dia anterior ao fato gerador, ou a última disponível). |
| `ID_Serie_Cotacao_Base` | referência (`Cad_Serie_Cotacao`), opcional | A série usada. |

**`Mov_Nfse_Dps` (altera)**: `Taxa_Cambio_Base`, `Data_Cotacao_Base` e `ID_Serie_Cotacao_Base`, com a mesma descrição. A DPS já tem `Valor_Servico_Moeda` e a moeda.

## 5.6 Entidade nova: `Mov_Energia_Ccee_Liquidacao` (art. 12, § 9º)

Registra a liquidação financeira da CCEE que serve de base na compra de energia elétrica multilateral. Sem vigência.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Energia_Ccee_Liquidacao` | identificador | |
| `ID_Empresa` | referência (`Cad_Empresa`) | O agente. |
| `ID_Filial` | referência (`Cad_Filial`) | O estabelecimento do agente (ou do representado). |
| `ID_Participante_Representado` | referência (`Cad_Participante`), opcional | O representado, quando o agente atua por outros. |
| `ID_Participante_Ccee` | referência (`Cad_Participante`) | A Câmara de Comercialização de Energia Elétrica. |
| `Competencia` | competência | |
| `Data_Liquidacao` | data | |
| `Valor_Liquidacao_Financeira` | número | O valor apurado pela CCEE. |
| `Percentual_Participacao_Estabelecimento` | número | A participação proporcional do estabelecimento (Decreto, art. 13, § 8º). A base do estabelecimento sai do valor vezes o percentual e não é gravada. |
| `Posicao_Liquidacao` | enumeração {devedora, credora} | O local da operação é o estabelecimento do agente na posição devedora (Decreto, art. 12, § 8º). |

O domínio `qualificacao_cbs` de `Cad_Participante_Qualificacao_Cbs` ganha o valor `agente_ccee` (31º tipo).

## 5.7 Descontos condicionais e incondicionais nas notas

O item da nota de produto (entrada e saída) tem um só `Valor_Desconto_Item`; a NFS-e já separa os dois (`vDescCond` e `vDescIncond`). A lei trata os dois de forma oposta: o incondicional **sai** da base; o condicional **integra**. Proponho um campo novo, **`Valor_Desconto_Condicional_Item`** (número, opcional), em `Mov_Nota_Fiscal_Saida_Item` e em `Mov_Nota_Fiscal_Entrada_Item`: o desconto concedido sob condição, que **não** reduz a base. O `Valor_Desconto_Item` passa a significar só o incondicional (que consta do documento e não depende de evento posterior). Não sei se o leiaute da NF-e separa os dois; se não separar, o campo vira controle do ERP (Q156-E1).

## 5.8 O que o art. 12 deixa sem desenho

- **Derivativo fora de condições de mercado:** só a linha `Observacao` da base especial. Não há critério numérico no Decreto (Q156-C4).
- **Forma simplificada do valor de mercado e a obrigação acessória:** ato conjunto (art. 14, § 7º, III).
- **Valor "notoriamente inferior ao de mercado" (arbitramento, art. 16 do Decreto):** não é art. 12; vai para o B0a.

# 6. O que entra no próximo "consolidar"

**13 entidades novas**, todas na Contabilidade & Fiscal.

| Entidade | Tipo | Vigência | Capítulo |
|---|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item_Equiparada` | extensão 1:1 do item de saída | não | 3 |
| `Cad_Criterio_Uso_Preponderante` | catálogo (21 linhas) | sim | 4 |
| `Cad_Regra_Uso_Consumo_Pessoal` | catálogo (12 linhas) | sim | 4 |
| `Cad_Regra_Uso_Consumo_Pessoal_Codigo` | filho 1:N (códigos NCM e NBS) | não | 4 |
| `Mov_Uso_Consumo_Pessoal_Item` | registro por item da aquisição | não | 4 |
| `Mov_Uso_Consumo_Pessoal_Alienacao` | filho da alienação (§ 9º) | não | 4 |
| `Cad_Regra_Base_Calculo_Cbs` | catálogo (19 linhas) | sim | 5 |
| `Cad_Regra_Valor_Mercado` | catálogo (8 linhas) | sim | 5 |
| `Mov_Valor_Mercado_Apuracao` | apuração com memória | não | 5 |
| `Mov_Valor_Mercado_Comparavel` | filho 1:N da apuração | não | 5 |
| `Mov_Apuracao_Tributo_Item_Base_Especial` | filho da apuração do item | não | 5 |
| `Cad_Regra_Conversao_Cambial_Base` | parâmetro (2 linhas) | sim | 5 |
| `Mov_Energia_Ccee_Liquidacao` | liquidação da CCEE | não | 5 |

**9 entidades alteradas.**

| Entidade | O que muda |
|---|---|
| `Cad_Regra_Operacao_Equiparada_Cbs` | seis colunas novas, dois valores novos no domínio do tipo, fundamento com LC e Decreto, duas linhas novas de carga |
| `Mov_Nota_Fiscal_Saida_Item` | valor `valor_inferior_mercado` em `Tipo_Onerosidade`; `Valor_Desconto_Condicional_Item` |
| `Mov_Nota_Fiscal_Entrada_Item` | `Valor_Desconto_Condicional_Item` |
| `Mov_Nota_Fiscal_Saida` | cinco campos de moeda e taxa da base |
| `Mov_Nfse_Dps` | três campos de taxa da base |
| `Cad_Empresa_Perfil_Fiscal` | `Atividade_Principal_Family_Office` |
| `Cad_Participante_Qualificacao_Cbs` | valor `agente_ccee` no domínio `qualificacao_cbs` |
| `Cad_Participante` | só o texto de `Regra_Fornecimento_Gratuito_Cbs` |
| `Mov_Estoque_Abertura_Cbs_Item` | só o texto de `ID_Motivo_Inelegibilidade` |

**Domínios novos** em `Cad_Classe_Sistema`: `grupo_criterio_uso_preponderante`, `hipotese_uso_consumo_pessoal`, `motivo_inelegibilidade_alienacao_uso_pessoal`, `componente_base_calculo_ibs_cbs`, `metodo_valor_mercado` e `hipotese_valor_mercado`. **Valores novos** em domínios existentes: `tipo_operacao_equiparada` (dois) e `qualificacao_cbs` (um).

**Cargas provisórias:** 21 critérios (Anexo A), 8 linhas da regra de operação equiparada (Anexo B, duas novas), 12 hipóteses e a lista de códigos de partida (Anexo C), 19 componentes da base (Anexo D), 8 métodos de valor de mercado (Anexo E) e 2 regras de conversão cambial. A contagem de comandos do T-SQL e dos scripts de carga é refeita na consolidação.

**Correções de texto que a consolidação faz:** (1) a nota "não foi conferida" sobre o brinde a preço de aquisição, na D-N285 e em `Cad_Regra_Operacao_Equiparada_Cbs`, passa a citar o art. 14, § 8º do Decreto; (2) os documentos 94 e 115 passam a dizer que "arts. 11, 13 e 57 a 64" do B0a-1 são do Decreto; (3) a leitura do documento 138 de que a D-N290 conflita com a LC 227 é substituída pela da seção 1.

# 7. Perguntas

*Respondidas "Sim" por Alberto em 04/11/2026 (Q156-1 a Q156-15). Na Q156-8 ele fixou a regra do câmbio da seção 5.5: a variação cambial da venda é o valor convertido na data; a da baixa vem da baixa do contas a pagar e receber, com a taxa do contrato de câmbio. O texto abaixo é o da proposta.*

## 7.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q156-1** | Mantém a D-N290 como está (regra no cadastro do participante, categoria do beneficiário no `Fundamento` em texto, sem entidade de parentesco), agora que a LC 227 nomeia cônjuges, companheiros e parentes até o 3º grau? | Sim |
| **Q156-2** | "Valor inferior ao de mercado" entra como valor novo de `Tipo_Onerosidade` e pela extensão 1:1 `Mov_Nota_Fiscal_Saida_Item_Equiparada`, em vez de campos soltos no item? | Sim |
| **Q156-3** | Um catálogo único de critérios de uso preponderante (`Cad_Criterio_Uso_Preponderante`, 21 linhas provisórias) serve ao art. 57, § 3º e ao art. 5º, § 8º? | Sim |
| **Q156-4** | As hipóteses do art. 57 e os códigos NCM e NBS de partida ficam em duas tabelas com vigência, e o Motor só **sugere** (o usuário confirma com `aprovar`, sem bloqueio)? | Sim |
| **Q156-5** | O estorno do uso pessoal fica em `Mov_Uso_Consumo_Pessoal_Item` (documento fiscal vinculado, ordem cronológica e acréscimos), e a exclusão da base do § 9º em `Mov_Uso_Consumo_Pessoal_Alienacao`; o documento 157 reaproveita em vez de criar outro estorno? | Sim |
| **Q156-6** | A base de cálculo ganha `Cad_Regra_Base_Calculo_Cbs` (19 componentes com vigência) e a linha filha `Mov_Apuracao_Tributo_Item_Base_Especial` para o que não vem da nota? | Sim |
| **Q156-7** | O valor de mercado fica em três entidades (método, apuração e comparáveis), com a memória de cálculo em **texto** até o ato conjunto definir a forma? | Sim |
| **Q156-8** | A conversão cambial da base vira parâmetro (`Cad_Regra_Conversao_Cambial_Base`) e a nota de saída e a DPS guardam a taxa usada? | Sim |
| **Q156-9** | A liquidação da CCEE ganha `Mov_Energia_Ccee_Liquidacao` e o valor `agente_ccee` em `qualificacao_cbs`, mesmo que poucos clientes usem? (o ERP não limita o tipo de cliente) | Sim |
| **Q156-10** | A pessoa física contribuinte fora da atividade (Decreto, art. 4º, § 6º, depois que a LC 227 revogou o § 4º do art. 57) entra como hipótese 12 da carga, provisória, para o contador confirmar? | Sim |
| **Q156-11** | O *family office* entra como campo do perfil fiscal da empresa (`Atividade_Principal_Family_Office`)? | Sim |
| **Q156-12** | As colunas `Aplica_Ibs` e `Aplica_Cbs` em `Cad_Regra_Base_Calculo_Cbs` ficam, para o IBS ser ligado quando o regulamento do CGIBS vier? | Sim |
| **Q156-13** | `Valor_Desconto_Condicional_Item` entra nas notas de entrada e saída, e `Valor_Desconto_Item` passa a ser só o incondicional? | Sim |
| **Q156-14** | O § 7º e o § 10 do art. 5º, o inciso V do § 2º do art. 63 do Decreto e a forma simplificada do valor de mercado ficam como **pendência sem desenho** (só o gancho do § 7º), até o regulamento ou o ato conjunto existir? | Sim |
| **Q156-15** | Posso aplicar tudo isto no seu próximo "consolidar", junto com os documentos 164 e 168? | Sim |

**Duas respostas que li por ação e peço que confirme.** (a) **Q138-4:** li a ordem de trabalho que você escolheu (começar pelo 156) como "sim" ao desenho único dos arts. 5º, 57 e 12 antes do B0a-3. (b) **Q138-7:** os arts. 5º, 6º, 12 e 57 foram relidos direto no texto consolidado, então a reextração desses artigos não é mais necessária; os demais artigos mal extraídos (14, 22, 28, 41, 59, 60, 195, 243 e 271) seguem para o documento 159.

## 7.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q156-C1** | Validar e ajustar a lista de partida de NCM e NBS do art. 57 (capítulos 71, 97 e 93; posições de bebidas e de tabaco) e preencher a dos bens e serviços recreativos, esportivos e estéticos | Lista do Anexo C, provisória |
| **Q156-C2** | O Decreto vai além do texto da LC em três pontos: critérios para **serviços** recreativos, esportivos e estéticos (art. 62, parágrafo único, IV), **locação** de imóvel residencial e de veículo (art. 63, § 3º) e janela de seis meses do plano de saúde (art. 63, § 5º). Valem como estão? | Valem, com `Origem_Regra = decreto` |
| **Q156-C3** | Quando o bem de uso pessoal teve o crédito **estornado** depois, ele "não permitiu a apropriação de crédito" para a exclusão do § 9º? | Não: `bem_permitiu_credito` vale também depois do estorno |
| **Q156-C4** | Qual critério numérico diz que um derivativo está "fora de condições de mercado" (art. 12, § 6º)? | Sem critério; registro manual |

## 7.3 Para a equipe

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q156-E1** | O leiaute da NF-e (NT 2025.002 e as seguintes) separa o desconto condicional do incondicional no item? | Se não separar, `Valor_Desconto_Condicional_Item` é controle do ERP e não vai no XML |

# 8. Limites

- **Li os arts. 5º, 12 e 57 da LC 214 consolidada e os arts. 4º, 5º, 6º, 13, 14, 62, 63 e 64 do Decreto**, mais os artigos que eles citam (44, 48, 81, 112 a 116, 364). Não li as demais regras que dependem deles.
- **O art. 6º** (não incidência) só entrou no que toca ao art. 5º: doação com crédito, amostra grátis e retirada por sócio. O desenho completo do art. 6º, inclusive o novo inciso XII (contribuições associativas), vai para o documento 159.
- **Os Decretos 13.075 e 13.133** alteram o Decreto 12.955, mas nenhuma alteração toca os artigos acima (conferi no texto consolidado).
- **O estorno do uso pessoal** pode virar tipo do ajuste genérico do B0a-3 (documento 157). Se o 157 criar `Mov_Cbs_Ajuste_Operacao`, a consolidação liga as duas, sem duplicar o campo.
- **Os valores legais da carga** (25%, 31 dias, 50%, três e doze meses, seis meses) saíram do texto; o contador valida a carga inteira.
- **Nenhum campo deste documento foi visto por você.** Os nomes e as listas são meus até você responder.

# Anexo A. Carga provisória de `Cad_Criterio_Uso_Preponderante` (21 linhas)

Todas com `Situacao_Dado = provisorio`. "LC" é a LC 214 consolidada; "Dec." é o Decreto 12.955. `Art57` e `Art5§8` são as colunas `Aplica_Art57_Par3` e `Aplica_Art5_Par8`.

| Código | Grupo | O que diz | Tipo | Art57 | Art5§8 | Condições (colunas verdadeiras) | Fundamento | Origem |
|---|---|---|---|---|---|---|---|---|
| UP-01 | bem_art57_i | Bens das alíneas a a d do inciso I (joias, obras de arte, bebidas alcoólicas, tabaco) comercializados ou usados na fabricação de bens a comercializar | bem | sim | não | `Exige_Comercializacao_Ou_Insumo` | LC 57, § 3º, I; Dec. 62, p. único, I | lei |
| UP-02 | bem_art57_i | Armas e munições que cumpram o UP-01 | bem | sim | não | `Exige_Comercializacao_Ou_Insumo` | LC 57, § 3º, II; Dec. 62, p. único, II, a | lei |
| UP-03 | bem_art57_i | Armas e munições usadas por empresas de segurança | bem | sim | não | `Exige_Atividade_Preponderante_Do_Adquirente` | LC 57, § 3º, II; Dec. 62, p. único, II, b | lei |
| UP-04 | bem_art57_i | Bens recreativos, esportivos e estéticos que cumpram o UP-01 | bem | sim | não | `Exige_Comercializacao_Ou_Insumo` | LC 57, § 3º, III; Dec. 62, p. único, III, a | lei |
| UP-05 | bem_art57_i | Bens recreativos, esportivos e estéticos usados exclusivamente em estabelecimento físico pelos clientes | bem | sim | não | `Exige_Uso_Exclusivo_No_Estabelecimento_Do_Cliente` | LC 57, § 3º, III; Dec. 62, p. único, III, b | lei |
| UP-06 | servico_recreativo | Serviços recreativos, esportivos e estéticos adquiridos por quem tem esses serviços como atividade preponderante | serviço | sim | não | `Exige_Atividade_Preponderante_Do_Adquirente` | Dec. 62, p. único, IV, a | decreto |
| UP-07 | servico_recreativo | Serviços recreativos, esportivos e estéticos fornecidos onerosamente aos clientes | serviço | sim | não | `Exige_Fornecimento_Oneroso_A_Clientes` | Dec. 62, p. único, IV, b | decreto |
| UP-08 | servico_recreativo | Serviços recreativos, esportivos e estéticos fornecidos aos clientes exclusivamente no estabelecimento físico do adquirente | serviço | sim | não | `Exige_Uso_Exclusivo_No_Estabelecimento_Do_Cliente` | Dec. 62, p. único, IV, c | decreto |
| UP-09 | beneficio_empregado | Uniformes e fardamentos | bem | sim | sim | nenhuma | LC 57, § 3º, IV, a; Dec. 63, § 1º, I | lei |
| UP-10 | beneficio_empregado | Equipamentos de proteção individual | bem | sim | sim | nenhuma | LC 57, § 3º, IV, b; Dec. 63, § 1º, II | lei |
| UP-11 | beneficio_empregado | Alimentação e bebida não alcoólica disponibilizada no estabelecimento a empregados e administradores durante a jornada | ambos | sim | sim | `Exige_Uso_No_Estabelecimento_Do_Contribuinte`, `Exige_Durante_Jornada` | LC 57, § 3º, IV, c; Dec. 63, § 1º, III | lei |
| UP-12 | beneficio_empregado | Serviços de saúde disponibilizados no estabelecimento durante a jornada | serviço | sim | sim | `Exige_Uso_No_Estabelecimento_Do_Contribuinte`, `Exige_Durante_Jornada` | LC 57, § 3º, IV, d; Dec. 63, § 1º, IV | lei |
| UP-13 | beneficio_empregado | Serviços de creche disponibilizados no estabelecimento durante a jornada | serviço | sim | sim | `Exige_Uso_No_Estabelecimento_Do_Contribuinte`, `Exige_Durante_Jornada` | LC 57, § 3º, IV, e; Dec. 63, § 1º, V | lei |
| UP-14 | beneficio_empregado | Planos de assistência à saúde de empregados e dependentes por acordo ou convenção coletiva (cláusula compulsória, no Decreto); crédito igual ao débito do fornecedor | serviço | sim | sim | `Exige_Acordo_Ou_Convencao_Coletiva`, `Credito_Igual_Debito_Fornecedor`; `Meses_Apos_Fim_Acordo` = 6 | LC 57, § 3º, IV, f; Dec. 63, § 1º, VI e § 5º | lei (prazo: decreto) |
| UP-15 | beneficio_empregado | Vale-transporte, vale-refeição e vale-alimentação; crédito igual ao débito do fornecedor | serviço | sim | sim | `Credito_Igual_Debito_Fornecedor` | LC 57, § 3º, IV, h; Dec. 63, § 1º, VII | lei |
| UP-16 | beneficio_empregado | Benefícios educacionais a empregados e dependentes por acordo ou convenção coletiva, oferecidos a todos (diferenciação a favor dos de menor renda ou maior núcleo familiar) | serviço | sim | sim | `Exige_Acordo_Ou_Convencao_Coletiva`, `Exige_Oferta_A_Todos_Empregados` | LC 57, § 3º, IV, g; Dec. 63, § 1º, VIII | lei |
| UP-17 | criterio_regulamento | Fornecimento por obrigação legal ou regulamentar da legislação trabalhista | ambos | sim | sim | nenhuma | LC 57, § 3º, V; Dec. 63, § 2º, I | decreto |
| UP-18 | criterio_regulamento | Veículo, equipamento de informática e aparelho de comunicação a empregado para atividades estritamente vinculadas às funções | bem | sim | sim | `Exige_Compatibilidade_Funcao_E_Quantidade` | LC 57, § 3º, V; Dec. 63, § 2º, II | decreto |
| UP-19 | criterio_regulamento | Serviços de transporte, telefonia e conexão de dados custeados para empregados em atividades estritamente vinculadas às funções | serviço | sim | sim | `Exige_Compatibilidade_Funcao_E_Quantidade` | LC 57, § 3º, V; Dec. 63, § 2º, III | decreto |
| UP-20 | criterio_regulamento | Fornecimento às pessoas do inciso II, III ou IV do caput a valor inferior ao de mercado por desconto especial, até 25% | ambos | sim | sim | `Percentual_Desconto_Maximo` = 25 | LC 57, § 3º, V; Dec. 63, § 2º, IV, b | decreto |
| UP-21 | criterio_regulamento | Revenda de bem material às mesmas pessoas com preço não inferior ao custo de aquisição | bem | sim | sim | `Exige_Preco_Nao_Inferior_Custo` | LC 57, § 3º, V; Dec. 63, § 2º, IV, a | decreto |

O inciso V do § 2º do art. 63 do Decreto (outros critérios por ato conjunto) **não tem linha** até o ato existir.

# Anexo B. Carga provisória de `Cad_Regra_Operacao_Equiparada_Cbs` (8 linhas, 2 novas)

As linhas existentes (D-N285 a D-N290) ganham as colunas novas; os valores de `Tributa`, `ID_Efeito_Credito`, `ID_Criterio_Base` e as demais colunas anteriores **não mudam**. `Inferior` é `Alcanca_Valor_Inferior_Mercado`; `Créd. aquis.` é `Exige_Credito_Na_Aquisicao`; `Exceção §8` é `Aplica_Excecao_Preponderancia`; `Alíq. esp.` é `Tributa_Se_Aliquota_Especifica`.

| Tipo | Inferior | Créd. aquis. | Exceção §8 | Alíq. esp. | Outras colunas novas | Fundamento (LC; Decreto) |
|---|---|---|---|---|---|---|
| brinde | não | não | não | não | | LC 5º, II; Dec. 5º, § 1º, I e 14, § 8º (base: preço de aquisição) |
| bonificacao | não | não | não | **sim** | `Exige_Registro_No_Documento` já existente | LC 5º, II e § 1º; Dec. 5º, § 1º, II e § 2º |
| doacao | não | não | não | não | | LC 6º, VIII e § 2º; Dec. 6º, § 2º |
| amostra_gratis | não | não | não | não | `Prazo_Maximo_Dias` = 31 | Dec. 6º, § 4º |
| retirada_socio | não | **sim** | não | não | `Restringe_Contribuinte_Regime_Regular` já existente | LC 5º, III; Dec. 5º, III |
| parte_relacionada | **sim** | não | não | não | `Permite_Dispensa_Verificacao_Conformidade` = falso | LC 5º, IV e § 7º; Dec. 5º, IV e 14, IV |
| **fornecimento_art5_i_a** (nova) | **sim** | **sim** | **sim** | não | critério da base: valor de mercado; efeito no crédito: nenhum | LC 5º, I, a, §§ 8º e 9º; Dec. 5º, I, a, §§ 8º e 9º |
| **fornecimento_art5_i_b** (nova) | **sim** | não | **sim** | não | critério da base: valor de mercado; efeito no crédito: nenhum | LC 5º, I, b, §§ 8º e 9º; Dec. 5º, I, b, §§ 8º e 9º |

A linha do brinde passa a dizer, no `Fundamento_Legal`, que o preço de aquisição vem do art. 14, § 8º do Decreto.

# Anexo C. Carga provisória de `Cad_Regra_Uso_Consumo_Pessoal` (12 linhas) e códigos de partida

| Nº | Hipótese | Tipo | Classifica por | Admite exceção | Fundamento (LC; Decreto) | Origem |
|---|---|---|---|---|---|---|
| 1 | joias, pedras e metais preciosos | bem | código NCM | sim | LC 57, I, a; Dec. 62, I | lei |
| 2 | obras de arte e antiguidades de valor histórico ou arqueológico | bem | código NCM | sim | LC 57, I, b; Dec. 62, II | lei |
| 3 | bebidas alcoólicas | bem | código NCM | sim | LC 57, I, c; Dec. 62, III | lei |
| 4 | derivados do tabaco | bem | código NCM | sim | LC 57, I, d; Dec. 62, IV | lei |
| 5 | armas e munições | bem | código NCM | sim | LC 57, I, e; Dec. 62, V | lei |
| 6 | bens e serviços recreativos, esportivos e estéticos | ambos | código NCM ou NBS | sim | LC 57, I, f; Dec. 62, VI | lei |
| 7 | bens e serviços relacionados à aquisição ou manutenção dos bens acima (LC 227) | ambos | natureza do bem | sim | LC 57, I, g; Dec. 62, VII | lei |
| 8 | bens e serviços adquiridos e fornecidos sem ônus ou abaixo do mercado ao contribuinte pessoa física, sócios, acionistas, administradores, conselheiros, empregados e seus familiares até o 3º grau | ambos | destinatário | sim | LC 57, II; Dec. 63, I a IV | lei |
| 9 | imóvel residencial e bens e serviços relacionados a aquisição, locação (decreto) e manutenção | ambos | natureza do bem | sim | LC 57, § 1º, I; Dec. 63, § 3º, I | lei (locação: decreto) |
| 10 | veículo e bens e serviços relacionados a aquisição, locação (decreto) e manutenção, inclusive seguro e combustível | ambos | natureza do bem | sim | LC 57, § 1º, II; Dec. 63, § 3º, II | lei (locação: decreto) |
| 11 | *family office*: bens e serviços relacionados à gestão | ambos | perfil da empresa | não | LC 57, § 2º; Dec. 63, § 4º | lei |
| 12 | pessoa física contribuinte: bens e serviços não relacionados à atividade econômica (regras de não contribuinte) | ambos | destinatário | não | Dec. 4º, § 6º (a LC 227 revogou o § 4º do art. 57) | decreto |

**Códigos de partida (`Cad_Regra_Uso_Consumo_Pessoal_Codigo`), a validar pelo contador (Q156-C1).**

| Hipótese | Tipo | Prefixos propostos |
|---|---|---|
| 1 | NCM | capítulo 71 |
| 2 | NCM | capítulo 97 |
| 3 | NCM | posições 22.03, 22.04, 22.05, 22.06 e 22.08 (decidir o 22.07, álcool etílico) |
| 4 | NCM | posições 24.02 e 24.03 (decidir o 24.01, fumo em bruto) |
| 5 | NCM | capítulo 93 |
| 6 | NCM e NBS | sem lista de partida; o contador preenche |

# Anexo D. Carga provisória de `Cad_Regra_Base_Calculo_Cbs` (19 linhas)

`Vigencia_Inicio` de partida: 01/01/2026 (início da CBS), a confirmar pelo contador. A linha 13 tem janela própria da lei: 01/01/2026 a 31/12/2032.

| Nº | Componente | Efeito | Condições | Fundamento (LC; Decreto) | Origem |
|---|---|---|---|---|---|
| 1 | acréscimos decorrentes de ajuste do valor da operação | integra | | LC 12, § 1º, I; Dec. 13, § 1º, I | lei |
| 2 | juros, multas, acréscimos e encargos | integra | | LC 12, § 1º, II; Dec. 13, § 1º, II | lei |
| 3 | descontos concedidos sob condição | integra | | LC 12, § 1º, III; Dec. 13, § 1º, III | lei |
| 4 | transporte cobrado como parte do valor da operação | integra | | LC 12, § 1º, IV; Dec. 13, § 1º, IV | lei |
| 5 | tributos e preços públicos, inclusive tarifas, incidentes ou suportados pelo fornecedor | integra | | LC 12, § 1º, V; Dec. 13, § 1º, V | lei |
| 6 | demais importâncias cobradas ou recebidas, inclusive seguros e taxas | integra | | LC 12, § 1º, VI; Dec. 13, § 1º, VI | lei |
| 7 | acréscimo na dação em pagamento (valor de mercado do bem recebido acima da dívida) | integra | | Dec. 13, § 9º | decreto |
| 8 | ganho em derivativo contratado fora de condições de mercado | integra | | LC 12, § 6º; Dec. 13, § 5º | lei |
| 9 | IBS e CBS incidentes sobre a operação | exclui | | LC 12, § 2º, I; Dec. 13, § 2º, I | lei |
| 10 | IPI | exclui | | LC 12, § 2º, II; Dec. 13, § 2º, II | lei |
| 11 | descontos incondicionais | exclui | `Exige_Constar_No_Documento_Fiscal`, `Exige_Sem_Evento_Posterior` | LC 12, § 2º, III e § 3º; Dec. 13, § 2º, III e § 3º | lei |
| 12 | reembolsos e ressarcimentos por conta e ordem de terceiros | exclui | `Exige_Documento_Em_Nome_Terceiro` | LC 12, § 2º, IV; Dec. 13, § 2º, IV | lei |
| 13 | ICMS, ISS, PIS/Cofins e PIS/Pasep (transição, 01/01/2026 a 31/12/2032) | exclui | janela própria | LC 12, § 2º, V; Dec. 13, § 2º, V | lei |
| 14 | contribuição do art. 149-A da Constituição (COSIP) | exclui | | LC 12, § 2º, VI; Dec. 13, § 2º, VI | lei |
| 15 | transporte internacional de passageiros, ida e volta vendidas juntas | reduz_percentual | `Percentual_Reducao` = 50 | LC 12, § 8º; Dec. 13, § 7º | lei |
| 16 | energia elétrica multilateral: liquidação da CCEE | substitui | | LC 12, § 9º; Dec. 13, § 8º | lei (LC 227) |
| 17 | alienação de bem que não permitiu crédito (uso pessoal): valor de aquisição, até o valor da venda | exclui | | LC 57, § 9º; Dec. 64, § 3º | lei (LC 227) |
| 18 | valor de mercado nas hipóteses do § 4º do art. 12 | substitui | | LC 12, § 4º; Dec. 14 | lei |
| 19 | devolução ou cancelamento: mesma base da operação original | repete_base_original | | LC 12, § 7º; Dec. 13, § 6º e 18 | lei |

# Anexo E. Carga provisória de `Cad_Regra_Valor_Mercado` (8 linhas)

| Nº | Método | Ordem | Período máximo | Condições | Fundamento (Decreto) |
|---|---|---|---|---|---|
| 1 | operações recentes (do contribuinte e de terceiros) | 1 | 3 meses | `Exige_Criterios_Comparacao` | art. 14, § 1º |
| 2 | operações anteriores, com ajustes | 2 | 12 meses (preferencialmente) | `Exige_Criterios_Comparacao` | art. 14, § 3º, I |
| 3 | custo total mais lucro bruto | 3 | | `Exige_Escrita_Contabil` | art. 14, § 3º, II |
| 4 | custo total mais despesas indispensáveis | 4 | | | art. 14, § 3º, III |
| 5 | cotação de bolsa de mercadorias e futuros (média do fechamento do dia) | 1, na hipótese própria | | `Depende_De_Ato_Conjunto` | art. 14, § 4º |
| 6 | cotação de ativo virtual na data da operação | 1, na hipótese própria | | `Depende_De_Ato_Conjunto` | art. 14, § 5º |
| 7 | valor do bem ou serviço recebido em troca (permuta) | 1, na hipótese própria | | | art. 14, § 6º; art. 4º, § 5º |
| 8 | preço de aquisição do bem ou serviço (brinde) | 1, na hipótese própria | | | art. 14, § 8º |

Os métodos 1 a 4 se aplicam em sequência quando a lei não impõe um só; as hipóteses 5 a 8 têm método próprio. A carga de `Cad_Regra_Conversao_Cambial_Base` tem duas linhas: `operacao_geral` com PTAX de venda do dólar, defasagem de -1 dia, última taxa disponível e conversão via dólar para moeda sem cotação (Decreto, art. 13, § 4º), e `importacao_bens_materiais` com a taxa do Imposto de Importação (Decreto, art. 81), que o B1 usa.

# Anexo F. Matriz de cobertura: dispositivo por dispositivo

"Gancho" quer dizer que o dispositivo espera regulamento e só tem coluna ou linha preparada.

| Dispositivo da LC 214 | O que diz | Onde fica |
|---|---|---|
| Art. 5º, I, a | Fornecimento de bem adquirido com crédito a contribuinte PF, sócios, administradores, empregados e familiares | Regra `fornecimento_art5_i_a`; `Regra_Fornecimento_Gratuito_Cbs` no participante (D-N290) |
| Art. 5º, I, b | Bem ou serviço produzido ou prestado a sócios, administradores, empregados e familiares | Regra `fornecimento_art5_i_b` |
| Art. 5º, I, c | Demais hipóteses da lei | Cada hipótese tem a sua regra; sem valor próprio |
| Art. 5º, II | Brindes e bonificações | Regras `brinde` e `bonificacao`; `Bonificacao_Sem_Evento_Posterior` |
| Art. 5º, III | Transmissão a sócio não contribuinte do regime regular | Regra `retirada_socio` |
| Art. 5º, IV | Fornecimento a parte relacionada | Regra `parte_relacionada`; `Cad_Participante_Vinculacao` (D-N288) |
| Art. 5º, § 1º | Bonificação em documento; bem com alíquota específica | `Bonificacao_Sem_Evento_Posterior`; `Tributa_Se_Aliquota_Especifica` |
| Art. 5º, §§ 2º a 6º | Partes relacionadas | `Cad_Participante_Vinculacao` (D-N288 e D-N289) |
| Art. 5º, § 7º | Flexibilização da verificação do valor de mercado | Gancho: `Permite_Dispensa_Verificacao_Conformidade` |
| Art. 5º, § 8º | Exceção do uso preponderante | `Cad_Criterio_Uso_Preponderante`; `ID_Criterio_Uso_Preponderante` na extensão |
| Art. 5º, § 9º | Tributação pelo valor de mercado | `ID_Apuracao_Valor_Mercado` na extensão; `Mov_Valor_Mercado_Apuracao` |
| Art. 5º, § 10 | Critérios simplificados para uso temporário | **Pendência** (nada no Decreto) |
| Art. 57, I, a a g | Bens e serviços de uso pessoal | `Cad_Regra_Uso_Consumo_Pessoal` (hipóteses 1 a 7) |
| Art. 57, II | Bens adquiridos e fornecidos às pessoas do inciso II | Hipótese 8; `Mov_Uso_Consumo_Pessoal_Item` |
| Art. 57, § 1º | Imóvel residencial e veículo | Hipóteses 9 e 10 |
| Art. 57, § 2º | *Family office* | Hipótese 11; `Atividade_Principal_Family_Office` |
| Art. 57, § 3º, I a V | Uso preponderante na atividade | `Cad_Criterio_Uso_Preponderante`; o inciso V do Decreto (ato conjunto) é gancho |
| Art. 57, § 4º | (revogado) | Hipótese 12, pelo art. 4º, § 6º do Decreto |
| Art. 57, § 5º | Vedação do crédito | `Resultado_Classificacao = uso_consumo_pessoal` deixa o crédito do item vedado |
| Art. 57, §§ 6º e 7º | (revogados) | Estorno pelo art. 64 do Decreto: `Mov_Uso_Consumo_Pessoal_Item` |
| Art. 57, § 8º | Identificação da pessoa física destinatária | `ID_Participante_Destinatario` |
| Art. 57, § 9º | Exclusão da base na alienação | `Mov_Uso_Consumo_Pessoal_Alienacao`; linha 17 da base |
| Art. 12, caput e § 1º | Valor da operação e o que integra | `Cad_Regra_Base_Calculo_Cbs` (linhas 1 a 7) |
| Art. 12, § 2º | O que não integra | Linhas 9 a 14 |
| Art. 12, § 3º | Desconto incondicional | Linha 11; `Valor_Desconto_Condicional_Item` |
| Art. 12, § 4º | Valor de mercado | Linha 18; `Cad_Regra_Valor_Mercado`, `Mov_Valor_Mercado_Apuracao`, `Mov_Valor_Mercado_Comparavel` |
| Art. 12, § 5º | Moeda estrangeira | `Cad_Regra_Conversao_Cambial_Base`; campos na nota de saída e na DPS |
| Art. 12, § 6º | Derivativos fora do mercado | Linha 8; `Mov_Apuracao_Tributo_Item_Base_Especial` |
| Art. 12, § 7º | Devolução com a mesma base | Linha 19 (o efeito na apuração é do B0a-3) |
| Art. 12, § 8º | Transporte internacional de passageiros | Linha 15 (metade do valor) |
| Art. 12, § 9º | Energia elétrica multilateral | Linha 16; `Mov_Energia_Ccee_Liquidacao` |
