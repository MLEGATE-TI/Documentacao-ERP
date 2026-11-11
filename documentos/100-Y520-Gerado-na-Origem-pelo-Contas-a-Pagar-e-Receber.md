# Y520 da ECF Gerado na Origem pelo Contas a Pagar e a Receber — Documento 100 (versão 14)

> **Consolidado na revisão 21 (23/10/2026, documento 108) e atualizado na revisão 22 (26/10/2026, documento 113).** As contagens e a frase "o dicionário continua na revisão 20" abaixo são as de quando o documento foi escrito. **Revisão 22:** a **Q100-13 está respondida** (documento 111: a data da operação é a em que o dinheiro saiu ou entrou, e o ano é o da ECF cujo período a contém); a **regra 7 está superada** e `abaixo_do_limite` **saiu** da `Situacao` do consolidado (documento 110, decisão de 26/10/2026); e o valor do Y520 parte da **`Base` do tipo da baixa** (regra 2). Os campos e tipos de baixa estão no documento 111.

*Proposta de desenho, em resposta ao seu pedido de mudar a estrutura do Y520: em vez de importar o registro, o ERP **captura os dados no pagamento ou recebimento com não residente** (contas a pagar e a receber) e **gera o Y520 sozinho**. A versão 2 (22/10/2026) incorporou as suas respostas e a **tabela de naturezas do programa da ECF**; a versão 3 incorporou as respostas às Q100-4a, Q100-7, Q100-17 e Q100-18; a **versão 4** (22/10/2026) incorpora a resposta sobre o **adiantamento**. É um relatório e uma proposta: **nada foi alterado no dicionário**. Só entra depois das suas respostas e do seu "consolidar", com a lista de campos que você tiver visto.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **O que você pediu:** quando houver pagamento ou recebimento de empresa que não é do país, o usuário informa na origem o que o Y520 exige, e o ERP junta tudo e gera o registro.
- **O que você respondeu (seção 2):** sim, o Y520 é gerado pelo ERP, **mas o contador pode incluir o que não veio do contas a pagar e receber**, seja por lançamento seja por **importação complementar**, e o ERP precisa **mostrar o que foi gerado e o que foi importado**. O participante não residente e o país (código Siscomex) ficam **no cadastro do participante**. O valor é **o total do pagamento feito**. A tabela de naturezas é a **do programa da ECF** (anexada).
- **O que a tabela mostrou (seção 3):** 675 linhas, 599 códigos de 5 posições, em quatro conjuntos de vigência. **Para a ECF de 2026 valem 139 códigos** (os sem data final, em vigor desde 01/01/2023). O código **10500** do exemplo do manual e o **12005** que li na Circular 3.690 **não estão mais vigentes**: o conjunto atual é outro. Isso confirma a minha leitura de que o Y520 usa só o código de **5 posições**, e mostra que a **Circular 3.690 não é mais a fonte da tabela vigente** (corrijo o que escrevi na versão 1).
- **Pagamento em outra moeda:** "quem for pagar tem que lançar o câmbio", e a taxa é **digitada por ele, do fechamento do câmbio**. Pelas suas respostas no documento 101, o **título** tem a moeda e a **baixa é na moeda do título**; o real sai da **taxa digitada**. Os campos de moeda e câmbio estão **no documento 101** (22 campos e a entidade da reavaliação mensal da variação cambial). O Y520 daqui **depende** deles, mas só para títulos e adiantamentos em moeda estrangeira.
- **Adiantamento (resposta nova):** entra no Y520 **como pagamento, na data em que o dinheiro saiu**; quando é compensado contra o título, o título só leva ao Y520 **o que sobrou a pagar em dinheiro** (regra 14).
- **Total pago:** o que **entrou na conta dele**: valor baixado, menos desconto, mais juros e multa, **menos o imposto retido** (seção 7, regra 2).
- **Quem classifica:** o **financeiro** faz a pré-classificação e o **contador pode corrigir** (seção 6.2).
- **Proposta:** 3 entidades novas (cadastro das naturezas com vigência, classificação por baixa ou adiantamento, linha consolidada do Y520) e 1 campo no participante: **51 campos** (62 com os dois opcionais; o mapa de sugestão ficou com **10 campos**: opção C do documento 102, **sem a faixa de US\$ 50.000**, que você tirou em 22/10/2026). Somados os 22 campos e a entidade do documento 101: **4 entidades e 73 campos** (5 e 84 com os opcionais).
- **Perguntas:** 7 ainda abertas (seção 10), cada uma com a minha recomendação. As respondidas estão marcadas.

# 2. Suas respostas e como as li

| Pergunta | Sua resposta | Como leio | Efeito no desenho |
|-----|------------------------------------|----------------------------------|--------------------------------|
| Complemento | "Pode importar algum complemento que não está no sistema" | O arquivo importado deixa de ser a fonte do Y520 e passa a **somar** ao que o ERP gerou | O consolidado guarda **três valores** por linha (baixas, lançamento do contador, importado) e a importação de origem (seção 6.3) |
| Pagamento em outra moeda | "Quem for pagar tem que lançar o câmbio para ter a conversão na moeda da empresa"; depois, na Q101-2: "a baixa do título é feita na moeda do título; nesta baixa você tem o câmbio para converter para real" | A baixa é **na moeda do título** e a taxa é digitada na baixa | **Substitui a Q100-10** (versão 1: sem moeda). Os campos ficam no **documento 101** (`Taxa_Cambio` e `Valor_Pago_Reais` na baixa; moeda no título) |
| **Q100-1** | "Sim em sua maioria, porém o contador pode incluir informações que não vieram pelo contas a pagar e receber" | D-N314 superada; o contador também **lança à mão** e **importa** | Lançamento manual aprovado (também responde a **Q100-8**) e importação complementar |
| **Q100-2** | "Usar a importação para complementar, e saber o que foi importado e o que foi gerado" | Importação **soma**, não substitui; cada valor é rastreável à origem | Três colunas de valor no consolidado e aviso quando a chave coincide (possível duplicidade) |
| **Q100-3** | "Sim, tem que estar no cadastro do participante" | Campo explícito de residência no participante | `Condicao_Residencia` em `Cad_Participante` (seção 6.4) |
| **Q100-4** e **Q100-4a** | "O total de pagamento feito"; depois: "Valor − desconto + juros + multa − se tiver retenção. O valor que entrou na conta dele" | O **líquido** que chegou ao beneficiário (ou à conta da empresa, no recebimento) | `Valor_Reais` = valor baixado − desconto + juros e multa − retenções da baixa (regra 2). O contador ainda confirma o tratamento do imposto retido |
| **Q100-5** | "Tabela em anexo" | A carga vem do **arquivo do programa da ECF**, versão 9, e não da Circular | `Cad_Natureza_Operacao_Cambial` com 675 versões (seção 6.1); a Circular deixa de ser a fonte |
| **Q100-11** | "O limite de 120.000 é para não precisar detalhar por modalidade; passando deste valor tem que detalhar a modalidade" | Coincide com o manual para **cartão** e **moeda**: abaixo do limite não se informam | Releio e confirmo na **Q100-11** (seção 7, regra 6) |
| **Q100-12** | "Sim, que tem que estar no cadastro do participante" | O código **Siscomex (3 posições)** do país vem do cadastro do participante | O país da classificação **não se digita**: sai do participante (regra 3) |

# 3. O que a tabela de naturezas mostra (arquivo do programa da ECF, versão 9)

| Item | O que li |
|----------------------|--------------------------------------------------|
| Formato | `Codigo\|DESCRICAO\|DataInicio\|DataFim\|CONTA\|ORDEM`, 675 linhas, texto com codificação do Windows (acentos em ANSI) |
| Códigos | **599 códigos distintos, todos de 5 posições**; 55 aparecem em mais de uma vigência, com a descrição mudando |
| Vigências | Quatro conjuntos: 01/01/2014 a 02/02/2014 (24 linhas); 01/01/2014 a 31/12/2014 (311 linhas); 03/02/2014 a 31/12/2022 (201 linhas); **a partir de 01/01/2023, sem data final (139 linhas)**. A data de 03/02/2014 é a de entrada em vigor da Circular 3.690 |
| Vigentes em 2026 | **139 códigos**, em dez grupos (coluna `CONTA`): "Até US\$ 50.000,00" (9), "Acima de US\$ 50.000,00" por assunto (serviços 31, capitais estrangeiros 14, comércio de bens 13, capitais brasileiros 13, rendas de capitais 8, transferências unilaterais 7, transporte 5, seguros 3) e "Anexo V" (36, operações especiais, arbitragens, interbancárias) |
| Direção (recebido ou pago) | **Não há coluna** de sentido. Só a descrição indica (por exemplo, "Exportação" e "Importação"). Por isso tirei o campo `Sentido` da proposta |
| Código do manual | O exemplo do manual, `10500` (câmbio simplificado simultâneo), existe, mas com vigência **só em 2014** |
| Código da Circular | O `12005` (exportação de mercadorias) que li na Circular 3.690 também **terminou em 31/12/2022** |

**Exemplos reais da tabela vigente em 2026 (código de 5 posições):**

| Código | Descrição | Grupo |
|--------|----------------------------------------------|---------------------------|
| 46002 | Serviços técnicos, profissionais e administrativos — serviços de computação e de informação | Acima de US\$ 50.000,00 — serviços |
| 46112 | Marcas registradas e franquias — cessão | Acima de US\$ 50.000,00 — serviços |
| 47575 | Direitos autorais — cessão ou uso — programas de computador | Acima de US\$ 50.000,00 — serviços |
| 12438 | Importação — pagamento posterior — até 180 dias | Acima de US\$ 50.000,00 — comércio de bens |
| 12122 | Exportação — recebimento posterior — até 360 dias | Acima de US\$ 50.000,00 — comércio de bens |
| 52443 | Investimento direto — dividendos, distribuição de lucros e juros sobre capital próprio | Acima de US\$ 50.000,00 — rendas de capitais |
| 12995 | Compra ou venda de mercadoria | Até US\$ 50.000,00 |

**A natureza de 12 posições (o que você pediu como exemplo).** Pela Circular 3.690/2013, art. 4º (lida em [normasbrasil.com.br](https://www.normasbrasil.com.br/norma/circular-3690-2013_263044.html)), a natureza completa de uma operação de câmbio tem 12 posições:

| Posições | O que é | Exemplo lido na Circular |
|-------|-------------------------------------------|--------------------------------|
| 1 a 5 | Código da natureza do fato que origina a operação (anexos I a XIII) | **12005** (exportação de mercadorias) |
| 6 e 7 | Natureza do cliente no País (anexo XIV) | **00** (pessoa física domiciliada no País) |
| 8 | Indicador de aval do governo brasileiro (anexo XV) | **N** (ou S) |
| 9 e 10 | Natureza do pagador ou recebedor no exterior (anexo XVI) | *não vi a tabela; fica como "xx"* |
| 11 e 12 | Grupo da operação (anexo XVII) | **90** (outros) |

Natureza completa, no formato de 12 posições: `12005` `00` `N` `xx` `90`, isto é, **1200500Nxx90** (as posições 9 e 10 são ilustrativas). **O Y520 usa só as cinco primeiras: `12005`.** O arquivo do programa da ECF só tem códigos de 5 posições, o que confirma a leitura. Atenção: este exemplo completo é do formato da Circular; **a tabela vigente desde 2023 é outra** e eu **não li** a norma que a trouxe, então não afirmo como ficou a natureza de 12 posições hoje. Para o Y520 isso não importa, porque só o código de 5 posições vai para a ECF.

# 4. Como funciona, passo a passo

| Passo | O que acontece | Quem faz | Fonte no dicionário |
|-----|--------------------------------------------------|----------------|--------------------------|
| 1 | O participante é cadastrado como **não residente**, com país (código Siscomex) | Cadastro | `Cad_Participante` (campo novo e `ID_Pais_Origem`) |
| 2 | O título a pagar ou a receber é lançado, como hoje | Financeiro | `Mov_Titulo` |
| 3 | Na **baixa** de título em moeda estrangeira, quem paga ou recebe informa os valores **na moeda do título** e a **taxa do fechamento do câmbio**; o ERP calcula o total pago em reais | Financeiro | `Mov_Titulo_Baixa` (documento 101) |
| 4 | Ao confirmar a baixa de título de não residente, o ERP cria a **classificação do exterior** "sugerida": tipo, país, data, valor em reais e natureza e forma sugeridas | ERP | entidade nova (seção 6.2) |
| 5 | O **financeiro pré-classifica** (confere e completa natureza e forma, ou exclui, com motivo); o **contador pode corrigir** se necessário | Financeiro e contador | idem |
| 6 | O contador **lança à mão** o que não passa pelo contas a pagar e receber (cartão no exterior, depósito em conta no exterior, recursos mantidos no exterior, operações de outro sistema) | Contador | idem (`lancamento_manual`) |
| 7 | O contador também pode **importar** um bloco Y com Y520 como **complemento**; o ERP guarda e mostra o que veio da importação | Contador | `Mov_Ecf_Importacao_Bloco` e `_Registro` (D-N317) |
| 8 | No fechamento, o contador pede **Gerar Y520**: soma por tipo, país, forma e natureza as três origens, aplica o limite de cartão e moeda e grava as linhas | Contador | entidade nova (seção 6.3) |
| 9 | O ERP sugere `IND_REC_EXT` e `IND_PGTO_EXT` do 0020 pelas mesmas classificações | ERP | `Mov_Ecf_Perfil_Indicador` |
| 10 | O arquivo da ECF sai com os Y520 gerados | ERP | `Mov_Escrituracao_Arquivo` |

# 5. O que o dicionário já tem e o que falta

| Peça do Y520 | O que o dicionário tem hoje | Lacuna |
|----------------------|-------------------------------------------------|--------------------------------------|
| Tipo (R recebido, P pago) | `Mov_Titulo.Tipo` (receber ou pagar) | Nenhuma |
| Valor | `Mov_Titulo_Baixa`: `Valor_Baixado`, `Valor_Juros_Multa`, `Valor_Desconto` | Nenhuma: o total pago é o líquido (regra 2), com as retenções de `Mov_Titulo_Retencao` |
| País | `Cad_Participante.ID_Pais_Origem` e `Cad_Pais` com `Codigo_Siscomex` (3, Brasil = 105) e `Codigo_Bacen` (4); o participante tem vigência (histórico) | Nenhuma: sai do participante. O manual diz "país em que está situada a pessoa que pagou ou foi beneficiária", o que bate com a sua resposta |
| Não residente | Nenhum campo | Campo novo (seção 6.4) |
| Forma (1 a 6) | Nada | Campo na classificação |
| Natureza | Nada | Cadastro novo, carga do arquivo que você enviou |
| **Moeda e câmbio** | `Cad_Moeda` (ISO 4217), `Cad_Serie_Cotacao` e `Mov_Serie_Cotacao_Valor` (taxa de câmbio por data, revisão 35), `Mov_Lancamento` com moeda e valor de origem e valor na moeda funcional, e a variação cambial na liquidação (Contabilidade, seção 15) **já descrevem** o título em moeda estrangeira. Mas **`Mov_Titulo` e `Mov_Titulo_Baixa` não têm moeda nem taxa** | Campos no título e na baixa: **documento 101** |
| Conta no exterior | `Cad_Conta_Bancaria` sem esse conceito; a baixa aponta para a **conta contábil**, não para a bancária; o cadastro de bancos não aceita banco estrangeiro (ISPB) | Só para as formas 4 e 5 (Q100-9, respondida: o ERP **deduz** pelo país da instituição, cadastro de banco estrangeiro no **documento 106**) |
| Consolidação | `Mov_Ecf_Importacao_Registro` guarda linhas **importadas** e imutáveis | Entidade própria para as geradas, com a origem de cada valor |
| Conferência com REINF | `Mov_Reinf_Rendimento` (com `ID_Baixa` e país de residência) | Conferência nova, só aviso |

# 6. Proposta de entidades e campos

## 6.1 `Cad_Natureza_Operacao_Cambial` (nova, mestre com vigência)

*O cadastro dos códigos de natureza do arquivo do programa da ECF. Padrão dos mestres com vigência do dicionário (identidade e versão, como `Cad_Moeda`): o **código** é a identidade e cada mudança de descrição ou de período é uma versão. Carga: 599 identidades e 675 versões. O manual diz que vale o código **vigente na data final da ECF**, porque o registro não tem data; por isso o cadastro tem vigência e a ECF de 2022 usa um conjunto e a de 2026 outro.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|----------------------|------------------------------|------------------------------------------|
| **ID_Natureza_Operacao_Cambial** | *identificador* | A identidade do código. |
| **ID_Natureza_Operacao_Cambial_Versao** | *identificador da versão* | Chave da versão, como nos demais mestres (Fase 0, seção 2). |
| **Codigo_Natureza** | *código (5) --- identidade* | O código de cinco posições, como no Y520 `NAT_OPER`. |
| **Descricao** | *texto* | O texto do arquivo (coluna `DESCRICAO`). |
| **Grupo** | *texto* | A coluna `CONTA` do arquivo (por exemplo, "Anexo V" ou "Acima de US\$ 50.000,00 - Serviços diversos e outros"). Serve para agrupar a lista na tela. |
| **Ordem** | *número* | A coluna `ORDEM`, para mostrar na mesma ordem do programa da ECF. |
| **Vigencia_Inicio** | *data* | A coluna `DataInicio`. |
| **Vigencia_Fim** | *data* | A coluna `DataFim`; 31/12/9999 quando vazia (convenção da Fase 0). |
| **Versao_Tabela_Ecf** | *código (10)* | A versão da tabela de onde veio a linha (no arquivo recebido, 9). |

## 6.2 `Mov_Ecf_Operacao_Exterior` (nova): a classificação de cada pagamento ou recebimento

*Uma linha por pagamento ou recebimento com não residente. Sem vigência (é um fato). A linha criada pelo ERP nasce "sugerida"; o **financeiro** a pré-classifica ("classificada") e só então conta no Y520; o **contador pode corrigir** (resposta à Q100-7).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Operacao_Exterior** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa (parte da chave do consolidado, com o ano). |
| **Ano_Calendario** | *número* | O ano da ECF cujo período (data inicial e final da escrituração) contém a data da operação (Q111-2); o estorno entra pela data do próprio estorno. Operação lançada depois que o Y520 do ano foi gerado: aviso ao contador, sem bloqueio (Q111-3). *(Texto da revisão 22.)* |
| **Origem_Linha** | *enumeração {baixa_titulo, adiantamento, lancamento_manual}* | De onde veio. `adiantamento` é o pagamento ou recebimento antecipado em dinheiro (`Mov_Credito`). `lancamento_manual` é o que o **contador** inclui sem baixa nem adiantamento (resposta à Q100-1). |
| **ID_Baixa** | *referência (Mov_Titulo_Baixa, opcional)* | Obrigatório quando a origem é `baixa_titulo`; vazio nas demais. |
| **ID_Credito** | *referência (Mov_Credito, opcional)* | Obrigatório quando a origem é `adiantamento`, com `Origem_Tipo` = `adiantamento_financeiro` e participante não residente; vazio nas demais. A aplicação do crédito contra um título (`Mov_Credito_Aplicacao`) **não** gera classificação (regra 14). |
| **Tipo_Exterior** | *enumeração {recebido, pago}* | Y520 `TIP_EXT` (R ou P). Da baixa vem do tipo do título e não se altera; no lançamento manual é escolhido. |
| **Data_Operacao** | *data* | A data em que o dinheiro saiu ou entrou (Q111-1): na baixa automática, a `Data_Ocorrencia` do retorno bancário; na manual, a `Data_Baixa`; no adiantamento, a `Data_Credito`; no estorno, a data do estorno; no lançamento manual, informada. *(Texto da revisão 22.)* |
| **ID_Participante** | *referência (Cad_Participante)* | A contraparte no exterior. Da baixa, sai do título. |
| **ID_Pais** | *referência (Cad_Pais)* | Y520 `PAIS`. **Vem do cadastro do participante** (país de origem na data da operação) e não se digita (resposta à Q100-12); o código gravado no arquivo é o Siscomex. Para corrigir, corrige-se o cadastro. |
| **Forma_Pagamento_Exterior** | *enumeração {cambio, transferencia_reais, cartao, deposito_conta_exterior, recursos_mantidos_exterior, moeda_nacional_ou_estrangeira}* | Y520 `FORMA`, valores 1 a 6 nessa ordem. `deposito_conta_exterior` só com recebido; `recursos_mantidos_exterior` só com pago. Sugerida só quando já houve uma classificada para o mesmo participante e tipo. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | Y520 `NAT_OPER`. A lista mostra só os códigos **vigentes na data final da ECF** do ano. |
| **Valor_Reais** | *número* | O **total do pagamento feito**, em reais: o que **entrou na conta do beneficiário** (resposta às Q100-4 e Q100-4a). Nasce da baixa pela fórmula da regra 2; negativo em estorno. |
| **Referencia_Operacao** | *código (40), opcional* | Número do contrato de câmbio, da fatura ou do documento do exterior, só para o contador achar a operação. Não vai para a ECF. |
| **Situacao** | *enumeração {sugerida, classificada, excluida}* | Só `classificada` entra no Y520. `sugerida` é pendência do financeiro. |
| **Motivo_Exclusao** | *texto, opcional* | Obrigatório quando a situação é `excluida`. |
| **ID_Usuario_Classificacao** | *referência (Cad_Usuario, opcional)* | Quem classificou ou excluiu (o financeiro, em regra). |
| **Data_Hora_Classificacao** | *data/hora, opcional* | Quando. |
| **Eh_Corrigido_Contador** | *booleano* | Verdadeiro quando o contador alterou natureza, forma ou valor depois da classificação do financeiro. |
| **ID_Usuario_Correcao** | *referência (Cad_Usuario, opcional)* | O contador que corrigiu. Obrigatório quando `Eh_Corrigido_Contador` é verdadeiro. |
| **Data_Hora_Correcao** | *data/hora, opcional* | Quando. |
| **Motivo_Correcao** | *texto, opcional* | O que mudou e por quê (obrigatório na correção). |
| **ID_Y520_Linha** | *referência (Mov_Ecf_Y520_Linha, opcional)* | A linha consolidada em que esta operação entrou, para ir do total ao pagamento. |
| **Observacao** | *texto, opcional* | Texto livre. |

## 6.3 `Mov_Ecf_Y520_Linha` (nova): o Y520 consolidado, com a origem de cada valor

*Uma linha por empresa, ano, tipo, país, forma e natureza (a chave do manual: `TIP_EXT + PAIS + FORMA + NAT_OPER`). Nova geração não apaga a anterior: as antigas ficam `substituida`. **Cada valor mostra de onde veio** (resposta à Q100-2).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Y520_Linha** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | Parte da chave. |
| **Ano_Calendario** | *número* | Parte da chave. |
| **Numero_Geracao** | *número* | 1, 2, 3 a cada nova geração. Vale a maior. |
| **Tipo_Exterior** | *enumeração {recebido, pago}* | Parte da chave. |
| **ID_Pais** | *referência (Cad_Pais)* | Parte da chave. |
| **Forma_Pagamento_Exterior** | *enumeração (as seis da seção 6.2)* | Parte da chave. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | Parte da chave. |
| **Valor_Baixas** | *número* | Soma de `Valor_Reais` das classificações `classificadas` de origem `baixa_titulo`: **o que o sistema gerou**. |
| **Valor_Manual** | *número* | Soma das `classificadas` de origem `lancamento_manual`: **o que o contador incluiu à mão**. |
| **Valor_Importado** | *número* | O valor do Y520 que veio da **importação complementar** (o da importação validada mais recente do ano, D-N317). |
| **ID_Importacao_Bloco** | *referência (Mov_Ecf_Importacao_Bloco, opcional)* | A importação de onde veio o `Valor_Importado`; vazio quando não há. |
| **Valor_Total** | *número* | A soma dos três. É o `VL_PERIODO` do Y520. |
| **Situacao** | *enumeração {gerada, substituida}* | Revisão 22: o valor `abaixo_do_limite` saiu; todo pagamento com não residente vai ao Y520 (documento 110). |
| **Data_Hora_Geracao** | *data/hora* | Quando foi gerada. |
| **ID_Usuario_Geracao** | *referência (Cad_Usuario)* | Quem mandou gerar. |
| **Observacao** | *texto, opcional* | Texto livre; o ERP escreve aqui o aviso de possível duplicidade. |

## 6.4 Alteração em `Cad_Participante` (1 campo novo)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **Condicao_Residencia** | *enumeração {residente, nao_residente}, opcional* | Resposta à Q100-3: a condição **está no cadastro**. Quando vazio, o ERP **presume** não residente se o endereço principal é de outro país e o participante não tem documento brasileiro, e lista os presumidos para o contador confirmar. Não residente exige `ID_Pais_Origem` preenchido e diferente do Brasil; sem isso a classificação não se conclui (regra 3). O participante tem vigência, então o país vale pela data da operação. |

## 6.5 Moeda e câmbio da baixa: documento 101

*Os campos de moeda e câmbio **saíram deste documento**. Pelas suas respostas (a baixa é na moeda do título; o câmbio converte para reais; a taxa é digitada), a moeda fica no **título** e a baixa ganha só a **taxa do câmbio** e o **total pago em reais** (`Taxa_Cambio` e `Valor_Pago_Reais`, documento 101, seção 4.2).*

O **adiantamento** em moeda (`Mov_Credito`) tem os mesmos campos de moeda, taxa e valor pago em reais (documento 101, seção 4.4).

**O que o Y520 usa:** o `Valor_Pago_Reais` da baixa (em título em moeda estrangeira) ou o total pago em reais (em título em reais), menos as retenções da baixa (regra 2). A taxa digitada é a exceção à regra da revisão 35 (taxa sempre lida da série), **aprovada por você** na Q100-17. **Sem contrato de câmbio** (formas 3, 4, 5 e 6), vale a taxa que o operador do financeiro digita do pagamento (Q105-3, 22/10/2026).

## 6.6 `Cad_Natureza_Operacao_Sugestao` (nova, com vigência; opção C aprovada na Q102-1, sem faixa de valor)

*Um mapa que o contador mantém: "título de tal origem, de tal tipo, de tal CFOP ou NBS, costuma ser tal natureza". Detalhado no **documento 102**. Quando o mapa não tem linha, vale a última natureza classificada para o mesmo participante e tipo.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Natureza_Sugestao** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa, opcional)* | Vazio vale para todas as empresas. |
| **Origem_Tipo_Titulo** | *código (40), opcional* | A origem do título (`Mov_Titulo.Origem_Tipo`). Vazio vale para qualquer origem. |
| **Tipo_Exterior** | *enumeração {recebido, pago}* | Receber ou pagar. |
| **Prefixo_CFOP** | *código (4), opcional* | Começo do CFOP dos itens da nota (por exemplo `3` importação, `7` exportação). Vazio não olha o CFOP. |
| **Prefixo_NBS** | *código (9), opcional* | Começo do NBS do serviço. Vazio não olha o NBS. |
| **Prioridade** | *inteiro* | Menor número vence quando duas linhas servem. |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | A natureza sugerida. |
| **Vigencia_Inicio** | *data* | Início. |
| **Vigencia_Fim** | *data, opcional* | Fim. |

# 7. Regras propostas

- **1. Quando nasce a classificação.** Ao confirmar a baixa de um título, ou ao lançar um adiantamento, cujo participante é **não residente** (campo do cadastro). Não nasce para título de residente. Se o cadastro muda depois, o contador exclui a linha, com motivo. **Desde o documento 103 (Q103-1 e Q103-2):** a natureza é informada **na entrada do título**, e a classificação da baixa nasce **com a natureza e a referência copiadas do título**; a forma é escolhida na baixa.
- **2. Valor (Q100-4 e Q100-4a).** `Valor_Reais` é o **total do pagamento feito**, em reais, o **líquido que chegou à conta do beneficiário** (ou à conta da empresa, no recebimento): `Valor_Baixado` − `Valor_Desconto` + `Valor_Juros_Multa` − a soma de `Valor_Retido` das retenções da baixa (`Mov_Titulo_Retencao`). Em título em moeda estrangeira, os três primeiros estão na moeda do título e vale o `Valor_Pago_Reais` (os três já convertidos pela taxa digitada, documento 101), menos as retenções, que são em reais. Decidido por você (22/10/2026): para empresa no exterior o Y520 leva o **valor líquido pago à empresa**, depois do imposto retido na remessa; não é ponto aberto. A tela mostra a diferença para o valor baixado, e o valor pode ser editado. **Revisão 22 (documento 111):** o ponto de partida depende da `Base` da linha `y520` do tipo da baixa: `valor_financeiro` parte de `Valor_Financeiro`; `valor_bruto` parte de `Valor_Pago_Reais` (em título em reais, do total da baixa) e vale mesmo que a transferência seja reduzida ou zero; `nao_entra` não gera classificação. A dedução das retenções continua.
- **3. País.** Vem do cadastro do participante, código Siscomex, na data da operação. Participante não residente sem país, ou com país Brasil, **não permite classificar** a linha (aviso, sem travar o pagamento).
- **4. Sugestões.** Natureza e forma (Q102-1 e Q102-2): (a) a última classificada para o mesmo participante, tipo e classe do item (mercadoria ou serviço); (b) a linha mais específica do mapa da seção 6.6; (c) vazio. As regras do mapa estão no documento 102. **A sugestão agora aparece na entrada do título** (documento 103), não só na baixa. **O ERP não calcula faixa de valor nem converte moeda para sugerir** (decisão de 22/10/2026): na baixa vale o contrato de câmbio e o financeiro escolhe o código, resumido ou detalhado. A lista de naturezas mostra só os códigos vigentes na data final da ECF.
- **5. Estorno e outros redutores (Q100-14, respondida por Alberto em 23/10/2026).** Estorno de baixa (baixa negativa) cria classificação **negativa** com os mesmos dados da original; o Y520 sai líquido. Vale o princípio dito por você: **estorno, cancelamento ou qualquer outro valor que abata o pagamento é redutor do pagamento** para a indicação no bloco; o **desconto** e o **abatimento** também entram como redutor (o `Valor_Desconto` da baixa já reduz o `Valor_Reais`, regra 2; o ERP não tem campo de abatimento separado, então o abatimento é lançado como desconto).
- **6. Formas inválidas.** O ERP recusa `deposito_conta_exterior` com pago e `recursos_mantidos_exterior` com recebido. A regra `REGRA_FORMA_PAGTO_INVALIDA` da planilha está escrita ao contrário (pergunta 6 do documento 98); o ERP segue o quadro de campos e o exemplo do manual.
- **7. Limite do cartão e da moeda (Q100-11). SUPERADA em 26/10/2026 (documento 110, seção 0.2): todo pagamento ou recebimento com não residente vai ao Y520, com a forma real; o limite de R\$ 120.000 é só conferência no ERP. O texto abaixo é o de antes.** O manual manda informar no Y520 as operações de **câmbio**, **transferência internacional em reais** e **depósito em conta no exterior** **sem limite**, e as de **cartão de crédito** e de **moeda nacional ou estrangeira (inclusive cheques)** só quando os valores são **iguais ou superiores a R\$ 120.000,00 (R\$ 10.000,00 por mês)**. Leio o que você disse da mesma forma: **abaixo do limite não se informa** (nem se detalha a modalidade); **a partir dele, informa-se e detalha-se por forma**. Parâmetro `limite_cartao_exterior_anual` (D-N310), provisório. Abaixo do limite, as linhas do consolidado ficam `abaixo_do_limite`. Dois pontos para o contador: se o limite vale **por forma** (cartão e moeda cada um com o seu, como o texto sugere) e por tipo; e se, atingido o limite, vai o **total** da forma ou só o excedente (leio: o total).
- **8. Geração.** Soma as classificações **classificadas** do ano por tipo, país, forma e natureza (`Valor_Baixas` e `Valor_Manual`), junta o `Valor_Importado` da mesma chave e grava o total. As **sugeridas** são listadas como pendência e não entram. Gerar de novo cria `Numero_Geracao` + 1.
- **9. Importação complementar (Q100-2).** O Y520 do bloco Y importado **soma**. Quando uma chave tem valor gerado ou manual **e** importado, o ERP **avisa possível duplicidade** (o mesmo pagamento pode estar nos dois lugares), sem bloquear. O que é de cada origem fica nas três colunas e na referência à importação.
- **10. O que bloqueia (Q103-2 e Q103-8).** A **natureza** é **obrigatória** na entrada do título de não residente: sem ela o título não é salvo (documento 103, regras 8 e 9 para títulos automáticos e já existentes). A **forma de pagamento** é **obrigatória na baixa** e **confirmada no momento do pagamento**: sem ela a baixa de título de não residente **não é confirmada**. Ao confirmar a baixa com natureza e forma, a classificação nasce **`classificada`** (a confirmação do financeiro é a da baixa) e o contador corrige depois, quando necessário (Q100-7). O que **não** bloqueia é o **resto** (referência, observação): vira aviso. (Antes do documento 103, nada bloqueava.)
- **11. Indicadores do 0020.** `IND_REC_EXT` calculado = existe classificação de tipo recebido no ano; `IND_PGTO_EXT` = idem para pago. O contador confirma ou corrige o indicador (Q100-15; a opção C da Q87-22, que você respondeu "sim"). Os dois tipos convivem (D-N324).
- **12. REINF.** A baixa pode ter `Mov_Reinf_Rendimento` com país de residência no exterior. Aviso informativo: baixa com rendimento no exterior no REINF **sem** classificação Y520, e país diferente entre as duas. O país vem do mesmo cadastro, então só diverge se a baixa tiver outro.
- **13. Quem vê.** Segue as permissões de pagar e receber; classificar, corrigir e gerar seguem o mecanismo de permissões e aprovações existente (Q100-7).
- **14. Adiantamento (resposta de Alberto).** O adiantamento em dinheiro a participante não residente (`Mov_Credito`, `Origem_Tipo` = `adiantamento_financeiro`) gera a classificação **na `Data_Credito`**, com `Valor_Reais` = `Valor_Pago_Reais` do crédito (documento 101, seção 4.4), tipo pago (adiantamento ao fornecedor) ou recebido (adiantamento do cliente). Quando o crédito é aplicado contra um título, **não há nova classificação**: o título leva ao Y520 só a baixa em dinheiro do que sobrou. Exemplo: título de US\$ 10.000, adiantamento de US\$ 3.000 e baixa de US\$ 7.000: o Y520 recebe o adiantamento (na data dele) e a baixa dos US\$ 7.000, **sem contar os US\$ 3.000 duas vezes**. A natureza tem códigos próprios para pagamento e recebimento antecipado (por exemplo, 12407 importação com pagamento antecipado de até 180 dias e 12108 exportação com recebimento antecipado de até 360 dias, na tabela vigente). A devolução ou o cancelamento do adiantamento gera classificação **negativa**, como o estorno (Q100-14, respondida em 23/10/2026). **Exemplo dito por você:** adiantamento pago em 2025 vai ao Y520 de 2025 pelo valor do adiantamento; o pagamento do título em 2026 vai ao Y520 de 2026 pelo **valor transferido**, que é o valor do título menos a compensação do adiantamento (e menos desconto ou abatimento, quando houver). **Natureza e forma são obrigatórias no lançamento do crédito** (Q103-9, "sim para moeda estrangeira"), como no título e na baixa; o **gatilho** é o participante **não residente**, empresa ou pessoa, **em qualquer moeda, inclusive reais** (Q103-10).

# 8. O que isto muda nas decisões anteriores

| Decisão | Efeito |
|---------------------|--------------------------------------------------|
| **D-N314** (Y520 importado; ERP não guarda câmbio) | **Superada** pela sua resposta à Q100-1. A importação continua, **como complemento** (Q100-2). O ERP passa a guardar **moeda e câmbio da baixa**, o que a D-N314 excluía |
| **D-N316** (entidade só do Y520) | Já superada pela D-N317. Volta uma entidade própria, mas **do dado gerado** |
| **D-N317** (guardar todas as linhas importadas) | Continua para todos os registros. A conferência (4) do documento 88 passa a ser entre o total gerado e o importado |
| **D-N315, D-N324** (R com `IND_REC_EXT`, P com `IND_PGTO_EXT`; os dois convivem) | Valem como estão |
| **Q87-22** (sugerir o indicador pelo participante estrangeiro) | Fica mais forte: a sugestão vem das classificações |
| **D-N310** (limite do cartão como parâmetro) | Continua; agora é usado na geração |
| **Revisão 35** (taxa de câmbio sempre lida da série de cotações, "nunca valor digitado solto") | **Exceção aprovada** (Q100-17): na baixa, quem paga **digita** a taxa do fechamento do câmbio; a série vira só sugestão. Os campos estão no documento 101 |
| **Documento 98, pergunta 6** (regras contraditórias do Y520) | Continua valendo; é da planilha da Receita |

# 9. O que não proponho (para não decidir por você)

- **Título em moeda estrangeira**, saldo na moeda, renegociação em moeda e variação cambial: **documento 101**, à parte (versão 3, com as suas respostas), com as perguntas dele. O Y520 de título em moeda **depende** dele; o Y520 de título em reais, não.
- **Contrato de câmbio** (corretora, taxa contratada, número). Só um campo de referência em texto.
- **Os demais registros do bloco Y** e dos blocos X e W: seguem importados (D-N317).
- **A norma que trouxe a tabela de 2023.** Não li; não afirmo qual é.

# 10. Perguntas

**Ainda abertas (5)**

| Nº | Pergunta | Minha recomendação |
|-----|----------------------------------------------------|----------------------------------|
| **Q100-11** | Confirma a leitura da regra 7: o limite só vale para **cartão** e **moeda**, abaixo dele **não se informa**, a partir dele informa-se o **total** da forma com o detalhe; câmbio, transferência em reais e depósito no exterior **sem limite**? Por forma e por tipo? | Sim; por forma e por tipo, **a confirmar com o contador** |
| **Q100-13** | A data da operação para o ano é a **data da baixa**, dentro do período da escrituração da ECF (que pode ser menor que o ano)? | **Respondida em 26/10/2026 (documento 111): sim, a data do pagamento** (dinheiro que saiu ou entrou); aplicada na revisão 22 |
| **Q100-14** | O estorno de baixa, e também a **devolução ou o cancelamento de adiantamento**, geram classificação **negativa**, e o Y520 sai líquido? | **Respondida em 23/10/2026: sim.** Todo valor que abate o pagamento (estorno, cancelamento, devolução de adiantamento, desconto, abatimento) é redutor do pagamento no Y520. |
| **Q100-15** | `IND_REC_EXT` e `IND_PGTO_EXT` calculados passam a vir das classificações, e o contador continua confirmando? | **Respondida em 23/10/2026: sim, o sistema calcula e o contador revisa.** O detalhe de contar só linhas que vão ao arquivo está na Q110-4 (documento 110), ainda aberta. |
| **Q100-16** | Acrescentar ao documento 98 uma **pergunta 8**: o manual cita a Circular 3.690 e o exemplo `10500`, mas a tabela do programa a partir de 2023 não tem esses códigos; qual norma e tabela valem, e o exemplo está desatualizado? | Sim, de baixa prioridade; **não bloqueia** o desenho |

**Respondidas por você (22/10/2026):** Q100-1 (sim, com complemento do contador), Q100-2 (importar como complemento, distinguindo a origem), Q100-3 (campo no cadastro do participante), Q100-4 (total do pagamento feito), Q100-5 (tabela enviada), Q100-8 (o contador inclui à mão), Q100-10 (moeda e câmbio lançados na baixa por quem paga) e Q100-12 (país Siscomex do cadastro do participante).

**Respondida por você no documento 103 (22/10/2026):** Q103-2 (a natureza é obrigatória na entrada do título; regra 10).

**Respondida por você no documento 105 (22/10/2026):** Q100-9 (há cliente com conta da empresa no exterior: sim; o cadastro do banco estrangeiro entra agora, documento 106; **o ERP deduz a conta no exterior pelo país da instituição, sem indicador**).

**Respondida por você no documento 102 (22/10/2026):** Q100-6 (criar o mapa de sugestão: opção C, agora com 10 campos porque a faixa de US\$ 50.000 saiu, com o histórico do participante antes do mapa).

**Respondidas por você na segunda rodada (22/10/2026):** Q100-4a (líquido que entrou na conta do beneficiário: valor baixado − desconto + juros e multa − retenção; **imposto retido na remessa: vale o líquido pago à empresa no exterior, decidido por você**), Q100-7 (o financeiro pré-classifica e o contador corrige), Q100-17 (a taxa é digitada do fechamento do câmbio) e Q100-18 (o título tem moeda, valor na moeda e valor estimado em reais; documento 101).

# 11. Contagem

| Item | Entidades | Campos |
|--------------------|---------|-------|
| `Cad_Natureza_Operacao_Cambial` | 1 | 9 |
| `Mov_Ecf_Operacao_Exterior` | 1 | 24 |
| `Mov_Ecf_Y520_Linha` | 1 | 17 |
| `Cad_Participante`: `Condicao_Residencia` | 0 | 1 |
| `Mov_Titulo_Baixa`: taxa e total pago em reais | 0 | 0 (no documento 101) |
| **Subtotal (proposta mínima)** | **3** | **51** |
| `Cad_Natureza_Operacao_Sugestao` (opção C sem faixa, Q100-6 respondida no documento 102) | 1 | 10 |
| **Total com os opcionais** | **4** | **61** |

Sobre a revisão 20 (915 entidades e 9.878 campos): **918 entidades e 9.929 campos** na proposta mínima deste documento; **919 e 9.939** com os opcionais. **Somado o documento 101** (1 entidade e 22 campos): **919 e 9.951** (920 e 9.961 com os opcionais). Se o `Codigo_Referencia` do documento 99 também for aprovado, some 1 campo. Mudam também, só no texto, a descrição de `Mov_Ecf_Perfil_Indicador.Indicador_Calculado` e a conferência 4 do documento 88. Nenhuma entidade existente perde campo e nenhum domínio muda. A carga de `Cad_Natureza_Operacao_Cambial` (675 versões) sai do arquivo que você enviou, na consolidação.

# 12. Limites deste documento

- A tabela de naturezas foi lida **inteira** (675 linhas), mas eu **não li a norma** que a trouxe em 2023, nem a nova natureza de 12 posições. A descrição de 12 posições vem da Circular 3.690, que valeu até 2022.
- Não li a tabela de países do programa da ECF; usei a sua resposta (Siscomex, do cadastro do participante). Vale conferir um país na primeira geração.
- O imposto retido na remessa está decidido (líquido pago à empresa no exterior). O limite por forma e tipo segue como ponto do contador, não do desenho.
- A correção do contador não guarda o valor anterior do financeiro, só o motivo (Q-nova possível se você quiser o histórico).
- Nada foi alterado no dicionário. A revisão 21 só nasce depois do "consolidar".
