# Desenho dos Campos das Decisões Pendentes da Revisão 17 — Documento 90

*Proposta de campos para as decisões que Alberto já tomou mas cujos documentos só dão o nome da entidade e uma estimativa de tamanho (D-N269 e D-N278, D-N280 e D-N281, D-N283, D-N284, D-N285 a D-N290, D-N295 e D-N296, D-N301 a D-N303). Aprovado por Alberto em 21/10/2026 (Q90-1 a Q90-6) e consolidado na revisão 19 (documento 95). O texto abaixo é o da proposta; três diferenças: a Q90-1 virou a entidade própria Cad_Credito_Presumido_Categoria (D-N334), no lugar dos dois campos em Cad_Credito_Presumido_Ibs_Cbs; a Q90-3 ficou com os 13 campos; e a conta final é de 8 entidades novas e 99 campos nelas, mais 15 campos novos em entidades existentes (e 1 que saiu, o do modo de composição noturna) e 5 domínios novos. Os nomes e as listas abaixo são minhas, não suas, e valem como rascunho para você corrigir.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Na consolidação da revisão 17 (documento 89) deixei de fora estas decisões porque nenhum documento trouxe a lista de campos que você tenha visto. Em vez de inventá-los dentro do dicionário, escrevi aqui a proposta completa, entidade por entidade, para você aprovar, corrigir ou recusar. Conta total: **7 entidades novas** (`Cad_Lista_Legal_Item`, `Cad_Taxa_Depreciacao_Cbs`, `Mov_Agencia_Turismo_Repasse`, `Mov_Auto_Infracao`, `Cad_Regra_Operacao_Equiparada_Cbs`, `Cad_Esocial_Ocorrencia` e `Mov_Esocial_Evento_Ocorrencia`) com 89 campos, e **8 campos novos em entidades existentes** (6 da D-N285 a D-N290, 2 da D-N280 e D-N281), mais 4 domínios novos em `Cad_Classe_Sistema` e textos. Se tudo for aprovado, o dicionário iria de 907 para 914 entidades e de 9.760 para 9.857 campos.

Seguem as regras do projeto: valores legais (percentuais, limites, vigências) são **parâmetros com vigência**, nunca código; o ERP **não limita o tipo de cliente**; a carga de tabelas oficiais entra com `Situacao_Dado` provisória até o contador validar; e toda entidade nova segue os padrões da Fase 0 (mestre com identidade e versão, ou tabela de janela de vigência, e o trio `Vigencia_Inicio`, `Vigencia_Fim` em 31/12/9999 e `Motivo_Vigencia`).

Convenção das tabelas: **Tipo lógico** como nos documentos 01 e 10; "opcional" quando pode ficar vazio.

# 2. Lista legal por NCM e NBS (D-N269, D-N278, D-N295, D-N296)

## 2.1 `Cad_Lista_Legal_Item`

Cada linha é um item de uma lista legal por NCM ou NBS, com vigência: anexos do Decreto 12.955/2026 (Repetro, GNL, Reporto, bens de capital do art. 196, art. 197), anexos da LC 214/2025 e as listas do Imposto Seletivo e do IPI. É mestre (identidade e versão) porque a linha da operação aponta para o item que o Motor sugeriu e o usuário confirmou, como na habilitação do REIDI. Chave de negócio: tipo da lista, anexo, NCM ou NBS e restrição.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------------|-------------------------------------|-------------------------------------|
| **ID_Lista_Legal_Item** | *identificador* | Identidade do item. |
| **ID_Lista_Legal_Item_Versao** | *identificador da versão* | Chave da versão, padrão da Fase 0. |
| **ID_Tipo_Lista** | *referência (Cad_Classe_Sistema, domínio = tipo_lista_legal) --- identidade* | Qual lista: repetro, gnl, reporto, bem_capital_art196, bem_capital_art197, imposto_seletivo, ipi e as que vierem; domínio aberto. |
| **Codigo_Anexo** | *código (até 30) --- identidade* | Anexo e tabela de origem (por exemplo "Anexo IV, Tabela I"). |
| **ID_Classificacao_Mercadoria** | *referência (Cad_Classificacao_Mercadoria, opcional)* | NCM em qualquer nível (capítulo, posição, subposição, item). Exatamente um entre este campo e `ID_NBS` é obrigatório. |
| **ID_NBS** | *referência (Cad_NBS, opcional)* | NBS, para os serviços (D-N296); o `ID_Servico_Tributacao` (lista da LC 116) segue só no ISS. |
| **Grupo_Item** | *código (até 30), opcional* | Grupo do item dentro do anexo, quando houver alíquota ou tratamento diferente por grupo. |
| **Restricao_Tecnica** | *texto, opcional* | Potência, capacidade, "exceto" e outras restrições técnicas do texto do anexo. O Motor só sugere; o usuário confirma na linha da operação. |
| **ID_Destinacao** | *referência (Cad_Destinacao, opcional)* | Destinação do bem para a qual a linha vale (D-N278). Vazio: vale para qualquer destinação. |
| **ID_Aliquota** | *referência (Cad_Aliquota, opcional)* | D-N278: alíquota própria do item (suspensão, alíquota zero ou reduzida; também a do IS e do IPI, D-N295). Vazio: busca geral da D-N199. Com alíquota ligada, vale a versão vigente na data do fato. |
| **Eh_Excecao** | *booleano* | Verdadeiro quando a linha é "exceto" (retira o NCM da lista). Padrão falso. Inclui a exceção da Zona Franca de Manaus na lista do IS e do IPI (D-N295). |
| **Fundamento_Legal** | *texto* | Norma, anexo e linha de onde veio. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga dos anexos sai provisória até a conferência com o Diário Oficial e a validação do contador. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | A validação. |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *(padrão da Fase 0)* | Janela da versão. |

**Busca (D-N278 e D-N199):** NCM mais específica (ou NBS), data da operação e destinação; com `ID_Aliquota` preenchido usa essa alíquota; sem ela, a busca geral. Os Anexos I a XV da LC 214 **não vieram**: sem eles o enquadramento por NCM nasce vazio. A carga provisória de cerca de mil linhas do decreto sai do texto que você colou, com a marca de provisória.

**D-N295 e D-N296 (texto, sem campo novo):** a alíquota do Imposto Seletivo e do IPI vem do item (NCM ou NBS) que aponta para `Cad_Aliquota`; `extincao_ipi` segue sem linha; `inicio_is` segue provisório, com pendência de alíquota enquanto não houver alíquota ligada. Em aberto com o contador: art. 454 da LC 214, lista de exceções do IPI e alíquota específica por unidade.

## 2.2 `Cad_Taxa_Depreciacao_Cbs`

Tabela de depreciação do decreto (258 linhas). Tabela de janela de vigência (sem identidade separada); chave de negócio: NCM mais `Vigencia_Inicio`.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|-------------------------------|------------------------------------|---------------------------------|
| **ID_Taxa_Depreciacao_Cbs** | *identificador* | Chave da linha. |
| **ID_Classificacao_Mercadoria** | *referência (Cad_Classificacao_Mercadoria) --- identidade* | NCM do bem, em qualquer nível. |
| **Descricao_Bem** | *texto* | Descrição do bem como no anexo. |
| **Percentual_Anual** | *número* | Taxa anual de depreciação (parâmetro com vigência). |
| **Vida_Util_Anos** | *número, opcional* | Vida útil em anos, quando o anexo a traz. |
| **Fundamento_Legal** | *texto* | Anexo e linha de origem. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Provisória até a conferência. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | A validação. |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *(padrão da Fase 0)* | Janela da linha. |

# 3. Nota de entrada e crédito presumido (D-N280 e D-N281)

A D-N280 diz que a nota emitida pelo adquirente vale para qualquer nota de entrada, com o mesmo fluxo da D-N71 e da D-N23; só mudam os parâmetros: se gera crédito presumido e com qual coeficiente por ano e categoria (arts. 247 e 253). A D-N281 confirma que o ressarcimento é permitido ao produtor rural e vedado ao transportador autônomo e aos resíduos.

**Proposta (2 campos em `Cad_Credito_Presumido_Ibs_Cbs`, que já é mestre com vigência, uma linha de código `cCredPres` por versão):**

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---------------------------|------------------|-------------------------------------------------------|
| **Coeficiente_Credito_Presumido** | *número, opcional* | Coeficiente do crédito presumido da categoria (arts. 247 e 253 do Decreto 12.955/2026), como parâmetro: cada ano é uma versão do código, com a sua `Vigencia_Inicio`. Vazio quando o código não usa coeficiente (o percentual vem do documento). |
| **Permite_Ressarcimento** | *booleano, opcional* | Verdadeiro para o produtor rural; falso para o transportador autônomo e os resíduos (D-N281). Vazio: não definido, e o ressarcimento não é oferecido. |

**Texto (sem campo):** `Mov_Nota_Fiscal_Entrada` diz que a nota de entrada emitida pelo adquirente vale para qualquer compra que exija a emissão; nota que não gera crédito presumido emite do mesmo jeito e só não abre o crédito.

**Pergunta Q90-1.** As categorias (produtor rural, resíduos, bens usados, transportador autônomo) correspondem **uma a uma** a códigos `cCredPres` de `Cad_Credito_Presumido_Ibs_Cbs`? Se sim, os dois campos acima bastam. Se não (uma categoria atravessa vários códigos), a alternativa é uma tabela de janela `Cad_Credito_Presumido_Categoria` (categoria, coeficiente, ressarcimento, vigência), o que passa de 2 campos para 1 entidade nova.

# 4. Agência de turismo (D-N283)

## 4.1 `Mov_Agencia_Turismo_Repasse`

Repasse documento a documento (art. 418 do Decreto 12.955/2026). A base da agência é o valor da operação menos os repasses **conferidos**; repasse que não passa na conferência não entra na dedução. Lida sem a condição "se houver cliente" (o ERP não limita o tipo de cliente).

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|-------------------------|---------------------------|------------------------------------------------|
| **ID_Agencia_Turismo_Repasse** | *identificador* | Chave do repasse. |
| **ID_Documento_Fiscal_Agencia** | *referência (Mov_Documento_Fiscal)* | Documento da operação da agência. |
| **ID_Documento_Fiscal_Fornecedor** | *referência (Mov_Documento_Fiscal)* | Documento do fornecedor intermediado. |
| **Valor_Repassado** | *valor monetário* | Valor repassado ao fornecedor, na moeda do documento da agência. |
| **Valor_Declarado_Fornecedor** | *valor monetário* | Valor declarado no documento do fornecedor. |
| **ID_Moeda** | *referência (Cad_Moeda, opcional)* | Moeda estrangeira do repasse, quando houver. |
| **Valor_Moeda_Estrangeira** | *valor monetário, opcional* | Valor em moeda estrangeira. |
| **Taxa_Cambio** | *número, opcional* | Taxa de fechamento do Banco Central do dia anterior à emissão (art. 418, § 2º, III). |
| **Data_Taxa_Cambio** | *data, opcional* | Data da taxa (o dia anterior à emissão). |
| **Coincide_Valor** | *booleano* | Calculado: o valor deduzido coincide com o declarado no documento do fornecedor (§ 2º, I). |
| **Documento_Referencia_Agencia** | *booleano* | Calculado: o documento do fornecedor referencia o da agência (§ 2º, II). |
| **Situacao_Conferencia** | *enumeração {conferido, divergente}* | Conferido só com as duas condições e a taxa certa. |
| **Valor_Deduzido** | *valor monetário* | Valor que entra na dedução da base: igual a `Valor_Repassado` quando conferido; zero quando divergente. |

Treze campos, mais do que o "cerca de 8" do documento 86, porque contei a moeda, a taxa e as duas conferências. Se preferir enxuto, saem `Valor_Moeda_Estrangeira`, `Data_Taxa_Cambio` e as duas conferências calculadas (ficando só a situação).

# 5. Auto de infração e procedimento fiscal (D-N284)

## 5.1 `Mov_Auto_Infracao`

O ERP só registra, sem calcular exposição a multa (arts. 557 a 578). Ligado ao processo do Jurídico.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|----------------|-----------------------------------|-------------------------------------------------|
| **ID_Auto_Infracao** | *identificador* | Chave do registro. |
| **ID_Empresa** | *referência (Cad_Empresa)* | Empresa autuada. |
| **ID_Processo** | *referência (Cad_Processo, opcional)* | Processo do Jurídico a que o auto se liga, quando houver. |
| **Tipo_Registro** | *enumeração {auto_infracao, procedimento_fiscal}* | O que é registrado. |
| **Numero_Auto** | *código (até 60)* | Número do auto ou do procedimento. |
| **Data_Auto** | *data* | Data do auto. |
| **Orgao_Autuante** | *texto, opcional* | Quem autuou. |
| **Prazo_Resposta** | *data, opcional* | Prazo de defesa ou de resposta. |
| **Resultado** | *texto, opcional* | Resultado, quando houver. |
| **Data_Inclusao** | *data/hora* | Quando foi registrado no ERP; preenchida pelo sistema, não alterável. |
| **Situacao** | *enumeração {ativo, encerrado}* | Ativo ou encerrado. |
| **Data_Encerramento** | *data, opcional* | **Obrigatória** se encerrado e **vazia** se ativo; o ERP rejeita encerrado sem data e ativo com data. |

Doze campos (você falou em 8 a 10). Reabrir um auto encerrado, se algum dia for preciso, é ação à parte, com motivo, na trilha de auditoria; não incluí. Sem catálogo de multas nem redução no pagamento, que dependem de atos posteriores.

# 6. Brindes, bonificações, doações e retiradas (D-N285 a D-N290)

## 6.1 `Cad_Regra_Operacao_Equiparada_Cbs`

Regras por tipo de operação aplicadas pelo Motor, com vigência (tabela de janela; chave: tipo mais `Vigencia_Inicio`). Onde o decreto restringe, vale o decreto como parâmetro.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------------|-------------------------------------|-------------------------------------|
| **ID_Regra_Operacao_Equiparada** | *identificador* | Chave da linha. |
| **ID_Tipo_Operacao_Equiparada** | *referência (Cad_Classe_Sistema, domínio = tipo_operacao_equiparada) --- identidade* | brinde, bonificacao, doacao, amostra_gratis, retirada_socio e parte_relacionada. |
| **Tributa** | *booleano* | Se a operação é tributada. |
| **ID_Efeito_Credito** | *referência (Cad_Classe_Sistema, domínio = efeito_credito_operacao)* | nenhum, estorno ou anulacao_opcional. |
| **ID_Criterio_Base** | *referência (Cad_Classe_Sistema, domínio = criterio_base_operacao, opcional)* | valor_mercado ou preco_aquisicao; vazio quando não há base. A base presumida do brinde no preço de aquisição vem do seu texto e não foi conferida no decreto. |
| **Exige_Registro_No_Documento** | *booleano* | Bonificação: só não incide se consta do documento fiscal da operação principal e não depende de fato futuro (art. 5º, § 2º, I). Sem o registro o Motor trata como tributada. |
| **Restringe_Contribuinte_Regime_Regular** | *booleano* | Retirada por sócio: só vale para sócio que não seja contribuinte do regime regular (art. 5º, III). |
| **Fundamento_Legal** | *texto* | Artigo e inciso. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | A validação. |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *(padrão da Fase 0)* | Janela da linha. |

Carga proposta (a conferir com o contador): brinde (tributa, base no preço de aquisição, sem efeito no crédito), bonificação (tributa só sem registro no documento), doação (não tributa salvo se o bem permitiu crédito ao doador; valor de mercado ou anulação de créditos, art. 6º, VIII e § 2º), retirada por sócio (tributa, estorno do crédito, só sócio fora do regime regular) e amostra grátis (não tributa, com os requisitos do art. 6º, § 4º).

## 6.2 Campos em entidades existentes (6)

**No item de saída (`Mov_Nota_Fiscal_Saida_Item`, 5 campos):**

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|------------------|-------------------------------------|---------------------------------------------|
| **Tipo_Onerosidade** | *enumeração {oneroso, nao_oneroso, equiparado}, opcional* | Decidido pelo Motor a partir da regra e da vinculação do participante (D-N285). |
| **Opcao_Doacao_Cbs** | *enumeração {tributar, anular_creditos}, opcional* | Na doação, a opção do art. 6º, § 2º. Sem opção a doação fica pendente e **não emite** (nada assumido). Não se aplica às operações do art. 5º, I, III e IV, nem ao FAR (§ 3º). |
| **Origem_Opcao_Doacao** | *enumeração {cadastro_participante, perguntado}, opcional* | De onde veio a opção: do cadastro do participante ou da pergunta ao usuário (D-N286). |
| **ID_Usuario_Confirmacao** | *referência (Cad_Usuario, opcional)* | Quem respondeu à pergunta; exige a ação `aprovar` (D-N287). |
| **Data_Hora_Confirmacao** | *data/hora, opcional* | Quando respondeu. |

**No participante (`Cad_Participante`, 1 campo, na versão, portanto com vigência e histórico):**

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---------------------|--------------------------------------|-----------------------------------------|
| **Regra_Fornecimento_Gratuito_Cbs** | *enumeração {tributar, anular_creditos, equiparado_art5}, opcional* | Tratamento do que se fornece ao participante sem contraprestação, para qualquer tipo de operação (D-N286 e D-N290). `tributar` (valor de mercado) e `anular_creditos` valem só onde a lei dá a opção (art. 6º, § 2º); `equiparado_art5` (sócio, administrador, empregado ou parente do art. 5º, I) tributa pelo valor de mercado, sem opção (art. 6º, § 3º) e sem perguntar. Vazio: não há regra, e o ERP pergunta. Classificar exige a ação `aprovar`, com o fundamento em `Motivo_Vigencia`. Sem consulta ao quadro societário nem à Folha. |

**Sem campo novo (D-N288 e D-N289):** a parte relacionada do art. 5º, IV, da LC 214 usa a `Cad_Participante_Vinculacao` já existente (qualquer tipo diferente de `nao_relacionada` conta; sem linha, o Motor avisa). Se as definições da LC 214 e da Lei 14.596 divergirem, entra um campo dizendo a que lei a linha atende, nunca uma segunda entidade (a leitura de que não divergem é sua e não foi conferida).

**Domínios novos em `Cad_Classe_Sistema.Dominio` (4):** `tipo_lista_legal`, `tipo_operacao_equiparada`, `efeito_credito_operacao`, `criterio_base_operacao`.

# 7. Ocorrências do eSocial no vínculo importado (D-N301 a D-N303)

## 7.1 `Cad_Esocial_Ocorrencia`

Catálogo do tratamento por código de ocorrência, com vigência (tabela de janela; chave: código mais `Vigencia_Inicio`). A classificação não vai para o código: fica em cadastro.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|----------------------------|--------------------------------|----------------------------------------|
| **ID_Esocial_Ocorrencia** | *identificador* | Chave da linha. |
| **Codigo_Ocorrencia** | *código (até 20) --- identidade* | Código que o eSocial devolve na ocorrência. |
| **Descricao** | *texto* | Descrição da ocorrência. |
| **Tipo_Ocorrencia** | *enumeração {erro, aviso}* | Erro ou aviso, como o eSocial classifica. |
| **Tratamento** | *enumeração {ja_existe, corrigir_e_reenviar, avisar_rh}* | `ja_existe`: o vínculo já constava no eSocial; o evento passa a aceito como importado (sem XML e sem data de envio do ERP, recibo opcional) e o RH é **sempre avisado** (D-N302). `corrigir_e_reenviar`: rejeitado, o RH corrige e o ERP reenvia como novo S-2200 original. `avisar_rh`: vai ao RH (por exemplo, CPF já admitido com outra matrícula, que **não** é "já existe"). |
| **Fundamento** | *texto* | Manual de orientação ou nota técnica do eSocial de onde o código e o tratamento vêm. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Carga inicial só com o "já existe" que o manual confirmar e todo o resto como `corrigir_e_reenviar`; provisória até o RH validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | A validação. |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *(padrão da Fase 0)* | Janela da linha. |

## 7.2 `Mov_Esocial_Evento_Ocorrencia`

Um retorno do eSocial traz várias ocorrências; cada uma é uma linha, com o texto literal.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---------------------|-----------------------------------|--------------------------------------------|
| **ID_Evento_Ocorrencia** | *identificador* | Chave da ocorrência. |
| **ID_Evento** | *referência (Mov_Esocial_Evento)* | Evento a que o retorno pertence. |
| **ID_Esocial_Ocorrencia** | *referência (Cad_Esocial_Ocorrencia, opcional)* | Linha do catálogo; vazio quando o código não consta (o tratamento é então `corrigir_e_reenviar`). |
| **Codigo_Recebido** | *código (até 20)* | O código como veio. |
| **Texto_Ocorrencia** | *texto* | O texto literal da ocorrência. |
| **Localizacao** | *texto, opcional* | Localização no XML, quando o eSocial informa. |
| **Matricula_Esocial_Informada** | *código (até 30), opcional* | Matrícula que consta no eSocial, quando ele informa; o aviso mostra a do ERP e esta, e o RH escolhe entre ajustar a matrícula do ERP e corrigir o eSocial (D-N302). |
| **Situacao_Tratamento** | *enumeração {pendente, tratada}* | Se o RH já tratou a ocorrência. |
| **ID_Usuario_Tratamento** | *referência (Cad_Usuario, opcional)* | Quem tratou. |
| **Data_Hora_Tratamento** | *data/hora, opcional* | Quando tratou. |
| **Decisao_Matricula** | *enumeração {ajustou_erp, corrigiu_esocial}, opcional* | Escolha do RH nos casos de matrícula diferente. |
| **Data_Hora_Recebimento** | *data/hora* | Quando o retorno chegou. |

São 11 campos no catálogo (com o trio de vigência) e 12 no movimento; o documento 87 estimou "cerca de 14" no conjunto, e a conta real é maior.

## 7.3 Texto, sem campo (D-N301 e D-N303)

`Evento_Importado` (documento 11) perde a exigência da confirmação do lote pelo RH: o vínculo importado que nunca foi enviado vai por envio direto, e o retorno é tratado pelo catálogo. Antes do primeiro S-2200 de vínculo importado, o ERP consulta o eSocial pelo trabalhador, se o serviço de consulta permitir; achando vínculo com outra matrícula, não envia e manda o caso ao RH com as duas matrículas. A divergência de unidade de pagamento ou de horas (Q75-4) continua travando o S-2206 até a confirmação. **A conferir no manual do eSocial:** o código de "registro já existe", a existência do serviço de consulta e o caminho de correção da matrícula.

# 8. Contagem

| Item | Entidades novas | Campos |
|------------------------------------|-----------------|-----------------------------------------------|
| `Cad_Lista_Legal_Item` (2.1) | 1 | 17 (14 próprios e o trio de vigência) |
| `Cad_Taxa_Depreciacao_Cbs` (2.2) | 1 | 11 (8 próprios e o trio) |
| Crédito presumido (3) | 0 | 2 em `Cad_Credito_Presumido_Ibs_Cbs` |
| `Mov_Agencia_Turismo_Repasse` (4) | 1 | 13 |
| `Mov_Auto_Infracao` (5) | 1 | 12 |
| `Cad_Regra_Operacao_Equiparada_Cbs` (6.1) | 1 | 13 (10 próprios e o trio) |
| Brindes, doações e retiradas (6.2) | 0 | 5 em `Mov_Nota_Fiscal_Saida_Item` e 1 em `Cad_Participante` |
| `Cad_Esocial_Ocorrencia` (7.1) | 1 | 11 (8 próprios e o trio) |
| `Mov_Esocial_Evento_Ocorrencia` (7.2) | 1 | 12 |
| **Total** | **7** | **89 em entidades novas e 8 em existentes (97)** |

Quatro domínios novos em `Cad_Classe_Sistema` (`tipo_lista_legal`, `tipo_operacao_equiparada`, `efeito_credito_operacao`, `criterio_base_operacao`). As contas do documento 86 ("19 entidades") e do documento 87 contavam por estimativa; vale esta tabela, que é por campo.

# 9. Perguntas para você

| Nº | Pergunta | Recomendação |
|------|-----------------------------------------------|-----------------------------------------------|
| Q90-1 | As categorias de crédito presumido correspondem uma a uma aos códigos `cCredPres`? (seção 3) | Sim, dois campos em `Cad_Credito_Presumido_Ibs_Cbs`; se não, entidade `Cad_Credito_Presumido_Categoria` |
| Q90-2 | `Cad_Lista_Legal_Item` como mestre (identidade e versão) está bem, ou prefere tabela de janela? | Mestre, porque a operação aponta para o item confirmado |
| Q90-3 | `Mov_Agencia_Turismo_Repasse` com 13 campos, ou a versão enxuta (9 campos)? | Treze: a taxa de câmbio e a conferência são exigência do art. 418 |
| Q90-4 | `Mov_Auto_Infracao` com `Tipo_Registro` (auto ou procedimento) e `Orgao_Autuante`, que você não pediu? | Manter; custam dois campos opcionais |
| Q90-5 | As colunas `Exige_Registro_No_Documento` e `Restringe_Contribuinte_Regime_Regular` na regra de operação equiparada, em vez de texto livre? | Colunas, porque o Motor precisa ler a condição |
| Q90-6 | Posso aplicar tudo isto na revisão 18? | Sim, depois das suas correções |

# 10. Limites

Nenhum campo desta proposta foi visto por você. A carga das regras de operações equiparadas e a dos anexos do decreto dependem do contador; os Anexos I a XV da LC 214 não vieram; o código de "registro já existe" do eSocial e o serviço de consulta por trabalhador não foram conferidos no manual. As leituras de que a bonificação sem registro é tributada, de que a base presumida do brinde é o preço de aquisição e de que as definições de parte relacionada não divergem são suas e não foram conferidas com os textos legais.
