# Caixa no lucro presumido, atividade de presunção por item e as respostas às Q126, Q102-7 e Q103-6 — Documento 127

> **Respostas de 27/10/2026 registradas (D-N374, documento 14); nada foi aplicado ao dicionário.** Ele continua na **revisão 24** (925 entidades e 10.033 campos). A revisão 25 passa a prever **929 entidades e 10.099 campos** com o que você já aprovou (inclui `Optante_Refis` e `Criterio_Reconhecimento_Receita`, as Q126-2 e Q126-3). Este documento tem duas partes: o que você respondeu e como li (seção 2) e o **desenho novo** que as respostas pedem (seções 3 a 7): a apuração do presumido por **caixa** (Q126-3), a **atividade de presunção de cada item**, a partir dos exemplos que você mandou (Q102-7), e a **natureza do royalty na origem** (Q103-6). Há **seis perguntas** novas (Q127-1 a Q127-6).

*Atualização (documento 128, 27/10/2026): a Q127-1 foi detalhada e substituída pelas Q128-1 a Q128-5; a Q127-6 foi respondida; as seções 2.2, 4.1, 4.2, 4.3 e 7 e a seção 8 foram corrigidas.*

*Documento pedido por suas respostas às Q126-1 a Q126-3 ("Sim ... Q126-3: sim"), à Q102-7 ("não há uma tabela pronta ... segue alguns exemplos de como seriam estes de-paras", com seis planilhas) e à Q103-6. Estende os documentos 99, 102, 103, 125 e 126. As leituras de norma e de prática contábil são minhas e **não foram conferidas** com o contador.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Q126-1, sim:** o lançamento da provisão do IRPJ e da CSLL usa o valor da apuração (soma das linhas arredondadas, igual ao P300 e ao P500). Só texto de regra.
- **Q126-2, sim, com um ponto novo:** o `Optante_Refis` **muda de período para período** (um trimestre optante, outro não). Como o perfil fiscal tem vigência, o campo vale **por data**, e a regra de qual data decide o trimestre foi **revista no documento 128** (o último dia não serve: o manual diz que a exclusão vale a partir do trimestre seguinte; o trimestre é de Refis se houve Refis em algum dia dele). O que vai no `0010.OPT_REFIS` com o ano partido **é ponto do contador** (Q128-2).
- **Q126-3, sim aos dois:** o campo `Criterio_Reconhecimento_Receita` e o detalhamento da receita por caixa, que está na seção 4. **A apuração por caixa não precisa de entidade nova:** a receita sai das **baixas dos títulos a receber** que já existem, repartida entre as atividades pelos itens da nota.
- **O que o dicionário não tem, e a sua resposta à Q102-7 mostra:** **nada liga o item da nota a uma atividade de presunção** (8%, 16%, 32% e assim por diante). Vale para caixa e para competência. Os seus exemplos mostram o desenho: um **de-para por serviço (NBS) ou por CFOP, que varia com o CNAE da empresa**. Proponho **1 entidade nova** (`Cad_Atividade_Presuncao_Mapa`, 12 campos) e **1 campo no item da nota** (seção 5).
- **Q102-7:** lida como **"não há tabela pronta"**, o que **fecha** a pergunta. O mapa do documento 102 (natureza do câmbio) continua **vazio na carga** e aprende pelo histórico, e as suas planilhas são exemplos de **outro** de-para (NBS para a linha do P200), que uso na seção 5.
- **Q103-6, sim:** a natureza do royalty é preenchida **pelo contador no cadastro de cálculo do royalty** e **fica na origem** (o título herda). O dicionário **não tem** um "cadastro de royalty" além da regra do Motor de Regras, então a **posição do campo** é a pergunta Q127-5.
- **Nos seus exemplos, os cálculos batem** (seção 5.1), e **uma linha pede conferência**: transporte rodoviário de **cargas** com **16%** no IRPJ (seção 5.2).

# 2. Respostas e como li

| Pergunta | Sua resposta | Como li | O que entra |
|------|------|--------------------------------------------|-----------------------------|
| **Q126-1** | "sim" | O lançamento contábil da provisão do IRPJ e da CSLL usa o **valor da apuração** (soma das linhas arredondadas, o mesmo do P300 e do P500). A conferência da Q99-3 continua só aviso. | Texto da regra da apuração e do lançamento |
| **Q126-2** | "Sim, mas o optante para o Refis ele é por período, um período de optante outro não" | `Optante_Refis` (sim ou não) em `Cad_Empresa_Perfil_Fiscal`, **com vigência por data**; minha primeira leitura era o valor vigente no último dia do período, **retirada no documento 128** (o trimestre é de Refis se houve Refis em algum dia dele; Q128-1) | **+1 campo** (`Optante_Refis`) |
| **Q126-3** | "Sim" | **Sim ao campo** `Criterio_Reconhecimento_Receita` (`caixa` ou `competencia`, obrigatório no presumido) **e ao detalhamento** que prometi: seção 4 | **+1 campo** e o desenho da seção 4 (a aprovar) |
| **Q102-7** | "Não há uma tabela pronta, pois pode ter variações dentro da mesma atividade, dependendo do CNAE principal da empresa. Segue alguns exemplos de como seriam estes de-paras" | **Não existe tabela de NBS para natureza** que sirva de carga. O que você mandou é um exemplo de de-para **NBS para linha do P200**, e **não** de NBS para natureza do câmbio. O mapa do documento 102 fica **sem carga**; a variação por CNAE vale para o de-para do P200 (seção 5) | Nenhum campo; fecha a Q102-7 |
| **Q103-6** | "Sim no cadastro dos Royalties para cálculo tem que indicar a natureza que o contador tem que preencher. Deixar na origem" | Sim: **o contador indica a natureza de cada tipo de royalty** (não existe lista minha) e ela é guardada **na origem do cálculo do royalty**, sem digitar de novo no título. "Cadastro dos Royalties para cálculo" lido como **a regra do Motor de Regras** que resolve o `percentual_royalty` (única estrutura de cálculo de royalty que o dicionário tem) | Posição do campo: **Q127-5** |

## 2.1 Contagem da revisão 25 prevista

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| Revisão 24 | 925 | 10.033 |
| Itens já aprovados (documento 123, Q107 e Q99-5) | +4 | +64 |
| **Q126-2 e Q126-3 (esta rodada)** | 0 | +2 |
| **Revisão 25 prevista** | **929** | **10.099** |

## 2.2 O Refis por período

O perfil fiscal (`Cad_Empresa_Perfil_Fiscal`) **já tem vigência**, então o `Optante_Refis` muda no tempo sem estrutura nova. O que ficava em aberto era **qual data decide o trimestre** e o que vai no `0010.OPT_REFIS`. **Detalhado no documento 128:** o último dia do trimestre **não serve** (o manual diz que a exclusão vale a partir do trimestre seguinte e que o Y680 e o Y681 são **mensais**); a proposta é o trimestre ser de Refis se houve Refis em **algum dia** dele (**Q128-1** a **Q128-5**). A Q127-1 fica **substituída** por elas.

# 3. O que o dicionário tem hoje

| Assunto | O que existe | Limite |
|------------------------|-------------------------------------------------|-----------------------------|
| Critério de caixa do **PIS e da Cofins cumulativos** | `Criterio_Escrituracao_Cumulativo` (`caixa`, `competencia_consolidada`, `competencia_detalhada`) em `Cad_Empresa_Perfil_Fiscal`, com vigência | É o `0110.IND_REG_CUM` da EFD-Contribuições; **não** decide o IRPJ nem a CSLL |
| Critério das **variações monetárias** | `Criterio_Variacao_Monetaria` (`caixa`, `competencia`, `caixa_oscilacao_cambial`) no perfil | Só variação cambial (MIT) |
| Caixa do **Simples Nacional** | `Regime_Apuracao` e `Receita_Recebida_*` na apuração do PGDAS-D | Termina com a Resolução CGSN 190 (D-N106) |
| **Recebimento** do título | `Mov_Titulo_Baixa` (`Data_Baixa`, `Valor_Baixado`, `Valor_Pago_Reais`, tipo da baixa) e, no retorno do banco, `Mov_Retorno_Bancario_Item.Data_Ocorrencia` (a data em que o banco registra o pagamento) | Nada diz que a baixa é "receita" de uma atividade |
| Título → nota | `Mov_Titulo.Origem_Tipo` = `nota_fiscal_saida` e `ID_Origem` = a nota; a nota tem itens com NBS e CFOP | O item **não tem atividade de presunção** |
| Receita por atividade | `Mov_Apuracao_Presuncao_Atividade.Receita_Bruta_Atividade` | **Nenhuma regra de onde o número vem** |
| Percentuais | `Cad_Percentual_Presuncao`, por atividade (domínio `atividade_presuncao`) e vigência, com `Percentual_Irpj` e `Percentual_Csll` | Os valores do domínio **não conferi** (seção 7) |

**Conclusão:** o presumido por caixa seria o **quarto** critério de caixa, e **os três primeiros são decisões diferentes** da mesma empresa. A fonte que li (um artigo, não a norma) diz que, se o IRPJ e a CSLL são apurados por caixa, o PIS e a Cofins também têm de ser (seção 4.1).

# 4. A apuração por caixa (Q126-3)

## 4.1 O critério e suas regras

| Regra | Texto proposto | Origem |
|------|----------------------------------------------|---------------------------|
| 1. Onde mora | `Criterio_Reconhecimento_Receita` em `Cad_Empresa_Perfil_Fiscal` (aprovado, Q126-3) | Sua resposta |
| 2. Vale o ano todo | A opção vale **para o ano-calendário inteiro**. O perfil só aceita **mudar com vigência em 1º de janeiro**; em outra data o ERP **avisa** e não bloqueia (o contador decide) | IN RFB 1.700/2017, art. 214, §§ 1º e 2º (o regime presumido vale o ano de atividade e se manifesta com a primeira quota ou a quota única); que a **escolha de caixa ou competência** é anual vem de uma Solução de Consulta citada por portal, **não do texto que li** (documento 128, seção 4) |
| 3. Coerência | Se `caixa`, o `Criterio_Escrituracao_Cumulativo` deve ser `caixa` quando a empresa é cumulativa exclusiva, e a empresa não pode ficar com um tributo por caixa e outro por competência. O ERP **avisa** quando divergem | **IRPJ e CSLL:** art. 224 (a CSLL só pode usar caixa se o IRPJ usar), então o ERP **bloqueia** CSLL em caixa com IRPJ em competência. **PIS e Cofins:** portal, **aviso** |
| 4. Cópia na apuração | A apuração guarda o critério usado, como já guarda o `Regime_Aplicado`: **`Criterio_Reconhecimento_Aplicado`** em `Mov_Apuracao_Irpj_Csll` (**+1 campo**, a aprovar) | Padrão do dicionário |
| 5. ECF | O `0010.IND_REC_RECEITA` sai do critério: `caixa` = 1, `competencia` = 2 | Manual da ECF (leiaute 12) |

## 4.2 De onde vem a receita por caixa

**Competência (como hoje se pensa):** soma dos itens das notas de saída **emitidas no período**, por atividade, menos devoluções, cancelamentos, IPI e descontos incondicionais.

**Caixa (proposta):** soma das **baixas dos títulos a receber** cuja **data de recebimento** cai no período, por atividade. Cada baixa é ligada, pelo caminho que já existe, a uma **nota** e aos seus **itens** (`Mov_Titulo_Baixa` → `Mov_Titulo` → `Mov_Nota_Fiscal_Saida` → itens), e o valor é **repartido entre as atividades dos itens na proporção do valor de cada item**. O mesmo caminho serve ao **demonstrativo de recebimentos** que o contador usa para provar o número (cada recebimento com a sua nota, como o artigo diz que a norma exige).

| Ponto | Proposta |
|----------------------|----------------------------------------------|
| **Data** | A do **recebimento**: `Data_Ocorrencia` do retorno (baixa automática) ou `Data_Baixa` (manual). `Data_Baixa` na baixa automática é a do **processamento** e pode cair no trimestre seguinte (retorno de sexta, processado na segunda); por isso **não** vale nesse caso. O contador confirma se vale a data do pagamento pelo sacado ou a do crédito |
| **Valor** | O **principal** da baixa, em reais. Juros e multa **não** são receita da atividade: o art. 223, § 3º, conta o que o cliente paga, a qualquer título, como recebimento do preço **até o limite do preço**; o contador diz onde entra o excedente (linhas de "demais receitas", Q99-2). A retenção na fonte **conta como recebida** (os arts. 221 e 222, parágrafos únicos, deduzem do devido o imposto retido sobre receita que integrou a base, o que pressupõe a receita pelo valor cheio); leitura minha |
| **Baixa parcial** | Proporcional: cada parcela recebida reparte-se entre as atividades da nota pela mesma proporção |
| **Tipo da baixa** | Contam as baixas que **extinguem o crédito**: **dinheiro**, na data do recebimento, e **aplicação de adiantamento** (`Mov_Credito_Aplicacao`), na `Data_Aplicacao` (resposta da Q127-6, documento 128). O **recebimento do adiantamento** (`Mov_Credito.Data_Credito`) **não** conta. Estorno entra com sinal negativo, na data do estorno. O contador confirma o encontro de contas |
| **Moeda** | Título em moeda: o principal convertido pela taxa **da baixa**; a diferença para o valor contabilizado é variação cambial e segue o `Criterio_Variacao_Monetaria` (já no perfil). Pelo art. 215, §§ 27 e 28, e arts. 152 a 155, a variação entra **na liquidação** (caixa), ou pela **competência** se a empresa optar, para o ano inteiro; no texto do lucro real a opção é só em janeiro e vai na DCTF (se vale no presumido: contador) |
| **Adiantamento de cliente** | **Respondida (Q127-6, 27/10/2026):** o recebimento **não entra** na apuração do IRPJ e da CSLL; entra no **faturamento em que é aplicado**, na data da aplicação, e a atividade vem dos **itens da nota**. Substitui o aviso e a alocação manual que eu propunha. IBS e CBS do adiantamento: documento 128, Q128-6 |
| **Receita que não vem de nota** | Rendimentos, juros, JCP e outros: **não** passam por aqui. Seguem a Q99-2 (contas mapeadas ao P150) |

## 4.3 Mudança de critério

- **Competência para caixa (início do ano):** o recebimento de nota **já tributada por competência** em ano anterior **não pode** entrar de novo. O ERP **exclui** do caixa os recebimentos de títulos de nota emitida **antes** do início do critério caixa, e o contador confirma (risco de pagar duas vezes).
- **Caixa para competência (início do ano):** a receita **auferida e não recebida** em 31/12 passa a ser tributada; o **P&R oficial** (pergunta 036, art. 223-A) diz que isso ocorre **em dezembro do ano-calendário anterior** à mudança; se a mudança for **no meio do ano por obrigação do lucro real**, a receita auferida e não recebida entra no período anterior, com recálculo e pagamento da diferença sem multa e sem juros (documento 128, seção 4). O ERP **propõe o valor** pelos títulos a receber em aberto, **como já faz** na transição do Simples (D-N209), e o contador confirma. **O art. 223-A não está no texto de 2017 que li** (vem do P&R). O art. 223, § 4º, diz que receita computada em período posterior ao devido paga IRPJ e CSLL com juros e multa; por isso a transição **avisa**.

# 5. Atividade de presunção por item (Q102-7 e os seus exemplos)

## 5.1 O que você mandou e o que conferi

| Planilha | O que traz | Conferência |
|----------------------------|------------------------------------|----------------------------|
| Natureza, receita, presunção e base (IRPJ e CSLL) | Revenda R$ 1.000.000 (8% e 12%), consultoria R$ 500.000 (32% e 32%), transporte de cargas R$ 300.000 (16% e 12%) | Bases do IRPJ: 80.000 + 160.000 + 48.000 = **288.000** ✓. Bases da CSLL: 120.000 + 160.000 + 36.000 = **316.000** ✓ |
| Linha conceitual do P200 | Receita a 8%, 16% e 32% e as bases | Soma das bases = **288.000** ✓ |
| IRPJ | 288.000 × 15% = 43.200; adicional (288.000 − 60.000) × 10% = 22.800; **66.000** | ✓ (o limite de R$ 60.000 do trimestre é 3 × R$ 20.000) |
| CSLL | 316.000 × 9% = **28.440** | ✓ |
| **NBS, tipo de receita, linha do P200, percentuais, benefício, status e observação** | **17 linhas de serviços e mercadorias** (consultoria, programas, publicidade, engenharia, advocacia, contabilidade, locação de bens móveis, administração e intermediação de imóveis, transporte de cargas e apoio logístico, revenda, industrialização, construção civil com material, serviço público específico, rendimentos de aplicação e JCP) | O código NBS está **"[confirmar]" em todas**; o status é **Proposto** (14) ou **Revisar** (3: construção civil, rendimentos e JCP) |

**Duas coisas que a planilha de NBS mostra:**

1. A **observação fiscal** de quase toda linha é uma **dúvida que só o contador resolve** ("pode ser intermediação", "separar licenciamento", "com material pode ser 8%"). Por isso o de-para **só sugere**, como o mapa do documento 102, e a escolha final é do contador.
2. A **construção civil com material** é **mista** (8% e 32%): "exige segregação analítica da nota e do contrato". O de-para precisa dizer que **uma linha só não basta**.

## 5.2 Uma linha para conferir

A linha **"Transporte rodoviário de cargas"** traz **16% no IRPJ** e 12% na CSLL, e a mesma planilha de natureza usa 16%. Pelo que li, em fonte secundária (um fórum de contadores, **sem o artigo da lei**), **transporte de cargas** é **8%** no IRPJ e **passageiros** é **16%**; a CSLL é 12% nos dois. Como a linha é "Proposto" e o código NBS é "[confirmar]", trato como **ponto para o contador** (item do documento 38, seção 2.2). **Não mudo o seu exemplo.**

## 5.3 Desenho proposto: `Cad_Atividade_Presuncao_Mapa` (nova, com vigência)

O percentual **não** entra no mapa: o mapa só diz **qual atividade**, e `Cad_Percentual_Presuncao` (que já tem `Percentual_Irpj`, `Percentual_Csll` e vigência) dá os números. A **linha do P200** também sai da atividade. Assim, uma lei que muda um percentual não obriga a refazer o mapa. O desenho segue o do documento 102 (`Cad_Natureza_Operacao_Sugestao`: critérios opcionais, prioridade e vigência).

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Atividade_Presuncao_Mapa** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa, opcional)* | Vazio vale para todas as empresas. |
| **Prefixo_Cnae_Principal** | *código (7), opcional* | Começo do **CNAE principal da empresa**: é a variação que você citou. Vazio não olha o CNAE. |
| **Prefixo_NBS** | *código (9), opcional* | Começo do NBS do serviço do item. Vazio não olha o NBS. |
| **Prefixo_CFOP** | *código (4), opcional* | Começo do CFOP do item. Distingue **revenda** de **produção própria** (a diferença que a planilha chama de "distinguir industrialização de prestação de serviço"). Vazio não olha o CFOP. |
| **Prioridade** | *inteiro* | Menor número vence; a linha mais específica deve ter o menor. |
| **ID_Atividade_Presuncao** | *referência (Cad_Classe_Sistema, domínio = atividade_presuncao)* | A atividade sugerida. |
| **Exige_Segregacao** | *booleano* | Verdadeiro nos casos mistos (construção civil com material): o item **não é aceito sem divisão** entre atividades. |
| **Observacao_Fiscal** | *texto, opcional* | A observação da sua planilha ("pode ser intermediação"); aparece para quem confirma. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Padrão da Fase 0, seção 9. Todas as linhas nascem `provisorio` (a coluna "Status" da planilha: Proposto e Revisar). |
| **Vigencia_Inicio** | *data* | Início. |
| **Vigencia_Fim** | *data, opcional* | Fim. |
| **Motivo_Vigencia** | *texto, opcional* | Por que a versão foi criada. |

**No item da nota de saída** (`Mov_Nota_Fiscal_Saida_Item`, que também recebe a NFS-e de aluguel): **`ID_Atividade_Presuncao`** (referência, opcional, **+1 campo**), preenchido com a **sugestão do mapa** e **confirmado ou trocado** pelo usuário ou pelo contador. O valor fica **no item** (cópia na emissão, como o NCM e o NBS). Item sem atividade **aparece como pendência** na apuração do presumido, **sem bloquear a emissão**.

**Ordem das fontes (a mesma da Regra 2 do documento 102):** (a) a **última atividade confirmada** para o mesmo produto ou serviço; (b) a **linha do mapa** mais específica vigente na data da emissão; (c) vazio.

**Carga:** o mapa **sai vazio** (a sua resposta: não há tabela, e varia com o CNAE). As **17 linhas** da sua planilha servem de **linhas de partida**, como `provisorio`, **depois** de o contador informar o código NBS (hoje "[confirmar]"). Não carrego nada sem o código. **Q127-3.**

**Rendimentos de aplicação e JCP** (linhas "Revisar"): **não são atividade**. São as "demais receitas" do P200 (Q99-2), que saem das contas mapeadas ao P150. **Não entram no mapa.**

# 6. A natureza do royalty na origem (Q103-6)

**O que o dicionário tem:** o royalty de licenciamento é **calculado pelo Motor de Regras** (`Cad_Motor_Regra`, `Tipo_Resultado` = `percentual_royalty`, critério `licenciamento_produto`), **estimado** no item do pedido (`Percentual_Royalty_Estimado`) e provisionado; no recebimento da venda nasce uma **obrigação a pagar** ao licenciante, que é o título com `Origem_Tipo` = `royalty_venda`. **Não achei** uma entidade de "cadastro de royalty" nem o vínculo entre o produto e o licenciante; por isso **li** o seu "cadastro dos Royalties para cálculo" como essa regra.

**Proposta (opção A, a mais barata):**

- o `Tipo_Resultado` do Motor de Regras ganha o valor **`id_natureza_operacao_cambial`**: o contador cria, **na mesma regra de licenciamento**, a linha que diz qual natureza vale para aquele tipo de royalty (marca, patente, programa, direito autoral), **resumido ou detalhado** conforme o contrato; **0 campos**, 1 valor de domínio;
- o item do pedido guarda a natureza resolvida (**`ID_Natureza_Operacao_Cambial_Royalty`**, opcional, **+1 campo** em `Mov_Pedido_Venda_Item`), na hora em que guarda o percentual estimado;
- o **título `royalty_venda`** nasce com a natureza **herdada** do item (`Mov_Titulo.ID_Natureza_Operacao_Cambial`, que já existe): o financeiro não digita de novo, e pode trocar só com o motivo.

**Opção B:** campo no cadastro do **licenciante** (participante) ou do **produto**. Fica fora porque o dicionário **não tem** esses dois vínculos desenhados, e a natureza depende do **tipo** de royalty, e não só de quem recebe.

**O royalty do exterior sem venda** (Q103-3, entra como `avulso`) **não** passa pelo Motor de Regras: a natureza continua obrigatória na entrada do título, com a sugestão do mapa do documento 102. A sua resposta vale para o royalty **de venda**; se você queria que valesse também para o avulso, **diga**.

# 7. Limites do que li

- **Li** as seis planilhas inteiras. **Não** conferi os códigos NBS (estão "[confirmar]") nem os valores do domínio `atividade_presuncao` do dicionário: o mapa depende de haver **uma atividade para cada par de percentuais** (IRPJ e CSLL) dos seus exemplos (8 e 12; 32 e 32; 16 e 12, e o 8 e 12 do transporte de cargas se for o caso). **Se faltar atividade no domínio, ela entra junto com o mapa.**
- **Li o texto original da IN RFB 1.700/2017** (DOU de 16/03/2017, enviado por você): arts. 214, 215, 216, 219 a 225 e 152 a 155. **Não** li as alterações posteriores (o **art. 223-A** não está nesse texto; vale o P&R oficial) nem a IN SRF 104/1998. A seção 4 segue como **proposta para o contador** (documento 128, seção 4).
- A conferência do transporte de cargas vem de um **fórum**; não é fonte para decidir.
- **Não desenhei** a apuração por competência (só a descrevi para comparar) nem a locação por unidade imobiliária (`Mov_Locacao_Faturamento`): o item da NFS-e de aluguel cobre o caso da empresa do arquivo de teste, mas **não verifiquei** o faturamento que não passa por nota.
- **Nada foi testado em arquivo:** o arquivo do documento 126 é de caixa, mas as linhas editáveis foram lidas do arquivo; ele **não prova** a apuração por caixa do ERP.

# 8. Perguntas

| # | Pergunta | Recomendação |
|-----|--------------------------------------------------|---------------------------|
| **Q127-1** | **Refis por período:** substituída pelas **Q128-1 a Q128-5** (documento 128): o último dia não serve, o trimestre é de Refis se houve Refis em algum dia dele, e o Y680 e o Y681 são mensais | Ver documento 128 |
| **Q127-2** | **Caixa (seção 4):** aprova as regras 1 a 5 (opção por ano-calendário com aviso, coerência com o PIS e a Cofins, `Criterio_Reconhecimento_Aplicado` em `Mov_Apuracao_Irpj_Csll`, **+1 campo**) e a receita por caixa pelas **baixas** repartidas pelos itens (seção 4.2), com demonstrativo de recebimentos e **sem entidade nova**? | **Sim.** Reaproveita o que existe e deixa o contador provar cada recebimento |
| **Q127-3** | **Mapa da atividade de presunção (seção 5.3):** aprova a entidade `Cad_Atividade_Presuncao_Mapa` (**12 campos**), o `ID_Atividade_Presuncao` no item da nota (**+1 campo**), a ordem das fontes e a carga **vazia**, com as 17 linhas da planilha como linhas de partida **só depois do código NBS**? | **Sim.** O percentual fica em `Cad_Percentual_Presuncao` e o mapa só sugere |
| **Q127-4** | **Mudança de critério (seção 4.3):** o ERP exclui do caixa o recebimento de nota já tributada por competência e propõe o valor da transição pelos títulos em aberto, **com confirmação do contador**? | **Sim** |
| **Q127-5** | **Royalty (seção 6):** a natureza fica no Motor de Regras (valor `id_natureza_operacao_cambial` em `Tipo_Resultado`) e no item do pedido (**+1 campo**), e o título herda? Ou prefere outra posição (licenciante ou produto)? | **Opção A** |
| **Q127-6** | **Adiantamento de cliente em regime de caixa:** **respondida em 27/10/2026** (não entra no IRPJ e na CSLL no recebimento; entra no faturamento em que é aplicado). Ver documento 128, seção 2 | Respondida |

**Não decidi nada** nas seis (a Q127-1 foi substituída e a Q127-6 respondida; ver documento 128). **Para o contador** (entram no documento 38, seção 2.2): o regime de caixa (data de recebimento, tipo de baixa, retenção, juros, mudança de critério), o transporte de cargas a 16%, o Refis (documento 128: ingresso no meio do trimestre, o `0010.OPT_REFIS` no ano da exclusão e os meses do Y680) e o adiantamento de cliente (entrega antes do faturamento).

# 9. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| Revisão 25 prevista (seção 2.1, **já aprovada**) | 929 | 10.099 |
| `Criterio_Reconhecimento_Aplicado` em `Mov_Apuracao_Irpj_Csll` (Q127-2) | 0 | +1 |
| `Cad_Atividade_Presuncao_Mapa` (Q127-3) | +1 | +12 |
| `ID_Atividade_Presuncao` em `Mov_Nota_Fiscal_Saida_Item` (Q127-3) | 0 | +1 |
| `ID_Natureza_Operacao_Cambial_Royalty` em `Mov_Pedido_Venda_Item` e o valor de `Tipo_Resultado` (Q127-5) | 0 | +1 |
| **Com tudo da Q127 aprovado como recomendo** | **930** | **10.114** |
| Mais a entidade de mapeamento do documento 125 (Q125-1, ainda sem resposta) | 931 | 10.124 |

Nada entra no dicionário antes do seu **"consolidar"** e de você ver e aprovar as listas de campos acima.
