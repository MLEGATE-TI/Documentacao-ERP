# Marketplace e plataformas digitais: responsabilidade pelo IBS e pela CBS e vínculo plataforma-fornecedor (bloco B7) — Documento 212

> **O que este documento faz.** Você escolheu desenhar o **B7 (marketplace)** e deixar o **PSP** de fora: o prestador de serviço de pagamento e o split continuam adiados para janeiro de 2028 (D-N282 e D-N391). Li os artigos da LC 214 que tratam da plataforma digital (art. 22, com a redação da LC 227, art. 23 e arts. 95 a 97), o que o Decreto 12.955 repete para a CBS (arts. 20, 21, 59, 72, 105, 115 e 172 a 178) e o que o dicionário já tem. Desenhei **três entidades novas, seis campos novos em uma entidade existente, dois valores novos de enumeração e duas linhas de parâmetro**. A responsabilidade da plataforma **não é do cadastro, é da operação**; por isso o vínculo guarda só o que dura (a opção e a anuência) e a operação guarda a responsabilidade.
>
> **Nada foi aplicado ao dicionário.** Ele está na revisão 40 (1.198 entidades e 13.738 campos). Este documento só vale com a sua resposta às Q212-1 a Q212-13.

*Fontes: LC 214/2025, texto compilado do Planalto impresso em 10/11/2026 (com as marcas da LC 227/2026): arts. 22, 23, 26 (§ 10), 32 (§§ 2º e 2º-A), 64 (§ 5º, VIII e IX) e 95 a 97; Decreto 12.955/2026, texto atualizado com o Decreto 13.075/2026: arts. 20, 21, 25 (§ 14), 28 e 32 (só as remissões), 59 (§ 2º), 72, 105 (§ 1º), 115 (VII) e 172 a 178. Dicionário: revisão 40; documentos 70, 94, 115, 116, 159 e 176. **Não li** o ato conjunto da RFB e do CGIBS que o art. 22 manda editar, o regulamento do IBS do Comitê Gestor, nenhuma nota técnica de leiaute de documento fiscal com plataforma e a legislação aduaneira do regime de tributação simplificada.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **A plataforma digital responde pelo tributo em quatro situações do caput e por duas opções.** Pelo caput do art. 22, ela responde **solidariamente com o adquirente e em substituição ao fornecedor** quando o fornecedor está no exterior (inciso I), e **solidariamente com o fornecedor residente no País** quando ela não presta as informações do § 5º (II, "a"), quando o fornecedor é contribuinte e não emite documento fiscal (II, "b") ou quando a operação não é registrada em documento fiscal (II, "c"). Pelas opções, com **anuência do fornecedor**, ela pode **emitir os documentos em nome dele e pagar** (§ 12) ou **ser substituta tributária** (§ 13: emitir, apurar e pagar).
- **Plataforma é quem intermedeia e controla pelo menos um destes elementos: cobrança, pagamento, termos e condições ou entrega** (§ 1º). Quem só dá acesso à internet, só presta serviço de pagamento autorizado pelo Banco Central, só faz publicidade ou só busca e compara fornecedores **sem cobrar pelas vendas** não é plataforma (§ 2º). Sem controle de nenhum elemento na operação, **não há responsabilidade** (§ 11).
- **A responsabilidade muda de operação para operação**, e por isso mora na operação (`Mov_Plataforma_Operacao`): depende de a plataforma controlar um elemento naquela operação, de o fornecedor estar no exterior ou no País, de ser contribuinte, de ter emitido o documento, de a plataforma ter prestado a informação e de ter havido a opção. O documento 70 propôs **três** valores de responsabilidade; a D-N524 mostrou que eles não cobrem a substituição tributária. A enumeração proposta tem **oito** valores (Anexo B).
- **Dois lados, uma entidade de vínculo.** A empresa do ERP pode ser **a plataforma** ou **a fornecedora que vende por ela**. Nos dois casos ela precisa saber se a plataforma optou por emitir e pagar: a plataforma para emitir e pagar, o fornecedor para **não emitir o documento duas vezes**. `Cad_Participante_Plataforma_Fornecedor` serve aos dois lados pelo campo `Papel_Empresa`. O terceiro lado, o adquirente, entra só na operação (diferença de alíquota de referência, art. 23, parágrafo único).
- **A diferença de alíquota de referência é registrada, não calculada à parte.** Quando a plataforma paga pela alíquota de referência (§ 15), a diferença é **paga pelo fornecedor** (alíquota incidente maior) ou **devolvida** (menor). O mesmo desenho vale para o recolhimento no câmbio de quem não se inscreveu (art. 23, parágrafo único), em que a diferença é do **adquirente ou importador**. Uma linha por imposto (CBS e IBS) guarda o valor devido, o pago e a diferença.
- **O split fica de fora, como você decidiu.** A exclusão de responsabilidade pela diferença (§ 7º) depende de o split ser possível e de a plataforma prestar a informação; por isso a operação tem **dois marcadores** (`Split_Disponivel` e `Informacao_Split_Prestada`). O ERP **não calcula nem segrega** valor de split.
- **Proposta:** 3 entidades novas (57 campos, 14 deles de referência), 6 campos novos em `Cad_Empresa_Perfil_Fiscal`, 2 valores novos de enumeração (`plataforma_digital` e `importador` em `Cad_Participante_Classe.Classe`), 2 linhas de parâmetro (o prazo de 30 dias e os 25% do nanoempreendedor), 12 regras provisórias de texto (Anexo A) e 13 avisos do Motor.
- **Contador:** 9 perguntas novas, C287 a C295 (documento 188, Parte 17).

# 2. O que li

| Fonte | O que li | O que tirei |
|---|---|---|
| LC 214, art. 22 (caput e §§ 1º a 15) | O artigo inteiro, na redação da LC 227 (os §§ 8º e 9º estão revogados) | As hipóteses de responsabilidade, o conceito de plataforma, as exclusões, as informações, o split, a exclusão de responsabilidade pela diferença, os débitos, as duas opções, o prazo de 30 dias e a alíquota de referência |
| LC 214, art. 23 | Caput e parágrafo único | A plataforma se inscreve no regime regular; quem no exterior não se inscreve tem o tributo segregado no câmbio, pela alíquota de referência, e a diferença é do adquirente ou do importador |
| LC 214, arts. 64 (§ 5º, VIII e IX), 95, 96 e 97 | Os dispositivos | A plataforma responde pela importação e pela remessa internacional feitas por seu intermédio; o destinatário da remessa é solidário se o fornecedor não se inscreveu ou o tributo não foi pago |
| LC 214, art. 26, § 10 | O parágrafo | Para o enquadramento como nanoempreendedor, a receita bruta do prestador de transporte ou entrega, mesmo intermediado por plataforma, é **25%** do valor bruto mensal |
| LC 214, art. 32 (§§ 2º e 2º-A) | Só as passagens que citam a plataforma | A plataforma informa ao prestador de pagamento as operações feitas por seu intermédio (split); o recebedor pode optar por não transmitir, caso em que o documento fiscal traz o vínculo com a transação |
| Decreto 12.955, arts. 20 e 21 | Os dois artigos inteiros | Repete o art. 22 e o art. 23, parágrafo único, só para a **CBS**, com a numeração dos parágrafos deslocada (Anexo C). **Não repete** o § 3º (dispensa de inscrição do fornecedor no exterior que opera só por plataforma inscrita) nem o § 11 (sem responsabilidade sem elemento essencial) |
| Decreto, arts. 59 (§ 2º), 115 (VII) e 105 (§ 1º) | Os dispositivos | O documento de ajuste e o documento da operação são emitidos pela plataforma quando ela opta pela substituição; a obrigação de emitir alcança a plataforma que emite em nome do fornecedor; a inscrição no CNPJ alcança a plataforma domiciliada no exterior |
| Decreto, arts. 72 e 172 a 178 | Os dispositivos | A importação por plataforma e a remessa internacional; o fallback do courier e do correio quando a plataforma não adere a programa de conformidade (art. 175, II) |
| Dicionário, revisão 40 | `Cad_Participante_Classe`, `Cad_Participante_Qualificacao_Cbs` (B2), `Cad_Participante_Modelo_Intermediacao` (B5), `Mov_Documento_Fiscal`, `Mov_Cbs_Ajuste_Operacao`, `Mov_Nota_Fiscal_Saida` e `Mov_Nota_Fiscal_Entrada` (campos de intermediador), `Mov_Titulo_Baixa` (campos do 1601), `Cad_Empresa_Perfil_Fiscal`, `Cad_Parametro_Legal_Ibs_Cbs` | O que já existe e o que falta (seção 3) |

# 3. O que o dicionário já tem

| Peça | Entidade | Uso no B7 |
|---|---|---|
| Intermediador na nota | `Mov_Nota_Fiscal_Saida` e `Mov_Nota_Fiscal_Entrada`: `Indicador_Intermediador` (`sem_intermediador` ou `plataforma_terceiros`), `ID_Participante_Intermediador` e `Identificador_Cadastro_Intermediador` | **É a origem natural** da linha de operação: quando a nota diz que houve plataforma de terceiros, o Motor propõe a linha (Q212-8) |
| Intermediador na baixa | `Mov_Titulo_Baixa.ID_Participante_Intermediador` e `ID_Participante_Instituicao_Pagamento` (revisão 32, D-N482 e D-N484) | É o 1601 da EFD-ICMS/IPI; **não muda**. O B7 não toca a baixa |
| Qualificação do participante | `Cad_Participante_Qualificacao_Cbs` (B2, 20 campos) | A **inscrição da plataforma no regime regular** (art. 23) é a qualificação com `Indicador_Contribuinte_Cbs` = `contribuinte_regime_regular`; o B7 só lê e avisa. A condição do fornecedor (contribuinte, regime favorecido) também vem daqui e do cadastro do participante |
| Classe do participante | `Cad_Participante_Classe.Classe` (enumeração extensível) | A Q116-3 aprovou `plataforma_digital` e `importador` como classes; **nenhum dos dois está no dicionário** (a classe tem 8 valores, sem eles) |
| Documento fiscal | `Mov_Documento_Fiscal` (40 campos): `ID_Filial` (emitente quando `Papel` = `emitido`) e `ID_Participante_Emitente` | Serve ao documento emitido pela plataforma em nome do fornecedor **sem campo novo** (5.6 e Q212-7) |
| Ajuste da operação | `Mov_Cbs_Ajuste_Operacao.Papel_Emitente_Documento` (`adquirente`, `fornecedor` ou `plataforma_digital`) | **Já cobre** o documento de ajuste emitido pela plataforma (Decreto, art. 59, § 2º); não muda |
| Modelo de intermediação | `Cad_Participante_Modelo_Intermediacao` (B5): `comissao`, `repasse_revenda` ou `taxa_servico_propria` | **É outra coisa**: é como o prestador remunera o intermediário (a agência de turismo), para a base do serviço. Não diz quem paga o tributo. Os dois podem coexistir na mesma operação, sem ligação entre eles |
| Perfil fiscal da empresa | `Cad_Empresa_Perfil_Fiscal` (21 campos, com vigência) | Recebe 6 campos (5.3). Há precedente: `Sujeita_Tef_Saf` e `Atividade_Principal_Family_Office` |
| Parâmetros legais | `Cad_Parametro_Legal_Ibs_Cbs` (12 campos, com código e vigência) | Recebe 2 linhas de carga (prazo de 30 dias e 25% do nanoempreendedor) |
| Imposto | `Cad_Imposto` (9 campos) | A linha de tributo da operação aponta CBS ou IBS |
| Conferência com a Plataforma da CBS | `Mov_Cbs_Apuracao_Espelho_Conta` (32 campos) | A linha de tributo guarda `ID_Espelho_Conta`, como as outras entidades da CBS |
| Título | `Mov_Titulo` (22 campos) | A diferença pode gerar título a pagar ou a receber |
| Split | `Mov_Titulo_Baixa.Valor_Tributo_Split` e `Canal_Split` | Adiado (D-N282). O B7 só põe dois marcadores |

# 4. Achados e leituras minhas

- **(1)** **A LC 214 e o Decreto 12.955 dizem a mesma coisa; só mudam a numeração e duas ausências.** O decreto é só da **CBS** e desloca os parágrafos (o § 12 da lei é o § 9º do decreto). Ele **não repete** o § 3º da lei (dispensa de inscrição do fornecedor no exterior que opera exclusivamente por plataforma inscrita) nem o § 11 (sem responsabilidade quando a plataforma não controla elemento essencial; no decreto isso decorre do § 1º, II). A tabela de correspondência está no Anexo C. O **IBS** só tem o texto da LC; o regulamento do Comitê Gestor não está no Projeto.
- **(2)** **A responsabilidade é da operação, não do vínculo.** A mesma plataforma, com o mesmo fornecedor, pode ser responsável numa venda (o fornecedor não emitiu o documento) e não ser em outra (ele emitiu e a plataforma prestou a informação). O vínculo guarda o que **dura**: a opção da plataforma, a anuência do fornecedor, a condição de contribuinte informada pela administração e o identificador do vendedor.
- **(3)** **O documento 70 propôs três valores e a D-N524 já disse que faltava a substituição tributária.** A lei tem seis fundamentos de responsabilidade (os quatro do caput e as duas opções do § 12 e do § 13) e duas ausências de responsabilidade (§ 11 e a operação que não cai em nenhuma hipótese). A enumeração `Responsabilidade_Plataforma` tem **8 valores** (Anexo B).
- **(4)** **A exclusão do § 7º é só da diferença, não do pagamento.** A plataforma que inicia o pagamento, tem split possível e presta as informações dos §§ 5º e 6º **não responde pelas diferenças** entre o recolhido e o devido pelo fornecedor residente no País. Mas pode continuar responsável pelo pagamento (por exemplo, se o fornecedor não emitiu o documento). Por isso a diferença é um campo próprio (`Responde_Por_Diferenca`) e **não** um valor da responsabilidade.
- **(5)** **"Devolvida" no § 15 não diz a quem.** O art. 23, parágrafo único, diz que a diferença é paga pelo **adquirente ou importador** (ou devolvida a ele). O § 15 diz "paga pelo fornecedor" quando a alíquota incidente é maior e "devolvida" quando é menor, **sem dizer a quem**. A linha de tributo tem `Parte_Da_Diferenca` (`fornecedor` ou `adquirente_ou_importador`) para guardar a resposta, e a pergunta vai ao contador (C289).
- **(6)** **"Inclusive de forma consolidada" não tem leiaute.** Os §§ 12, I, e 13, I, permitem documento consolidado; o ato conjunto não está no Projeto. Mantive a decisão da Q159-10 (documento 159): **sem campo agora**. A estrutura aceita o consolidado de graça, porque **várias linhas de operação podem apontar para o mesmo `ID_Documento_Fiscal`**.
- **(7)** **O documento da plataforma em nome do fornecedor cabe em `Mov_Documento_Fiscal` sem campo novo.** `Papel` é `emitido` e `ID_Filial` é a filial da plataforma (quem transmite); `ID_Participante_Emitente`, hoje descrito só para o documento recebido, passa a apontar **o fornecedor em cujo nome o documento sai**. É leitura minha: o leiaute e o certificado de quem assina não foram lidos (C292). Só a descrição do campo muda (Q212-7).
- **(8)** **A condição de contribuinte do fornecedor não inscrito vem da administração.** O § 4º da lei manda o Comitê Gestor e a RFB informarem à plataforma. Não há como o ERP saber isso sozinho; o vínculo guarda `Condicao_Informada_Administracao` e a data, e o Motor avisa quando falta.
- **(9)** **A inscrição da plataforma não precisa de campo novo.** O art. 23 manda inscrever-se no regime regular; isso já é `Cad_Participante_Qualificacao_Cbs` (B2). O B7 avisa quando a empresa é plataforma e não tem a qualificação vigente. Quanto à plataforma ou ao fornecedor **no exterior** que não se inscrevem, o tributo é segregado no câmbio pela alíquota de referência (art. 23, parágrafo único); a operação guarda só o marcador `Recolhido_Pelo_Cambio`.
- **(10)** **A mesma pessoa pode estar em três posições.** A empresa que é plataforma tem o vínculo com cada vendedor; a empresa que vende por plataforma tem um vínculo por plataforma; a empresa que compra de fornecedor por plataforma tem só a operação. O campo `Papel_Empresa` (`plataforma`, `fornecedor`, `adquirente`) distingue as três, no mesmo padrão de `Mov_Cbs_Ajuste_Operacao`.
- **(11)** **Os 25% do nanoempreendedor são parâmetro do B2 que faltava.** O § 10 do art. 26 da lei (art. 25, § 14, do decreto) manda contar como receita bruta **25%** do valor bruto mensal do prestador de transporte privado de passageiros ou de entrega, inclusive com plataforma. Não achei o número em parâmetro nenhum do dicionário; entra como linha de carga (Q212-9).
- **(12)** **A precedência entre fundamentos é leitura minha** (5.4). Quando mais de um fundamento se aplica (o fornecedor não emitiu o documento **e** a plataforma não prestou a informação, por exemplo), a coluna guarda **um** valor, o primeiro da ordem, e o Motor lista os outros no aviso. A ordem vai ao contador (C290).
- **(13)** **A importação e a remessa internacional só entram pela responsabilidade.** O B7 registra que a plataforma responde (art. 64, § 5º, IX, e art. 96) e a diferença do adquirente; o processo da importação é do B1 e o regime de tributação simplificada **não foi lido**. O fallback do art. 175, II, do decreto (courier e correio, quando a plataforma não adere a programa de conformidade) também é do B1.

# 5. Proposta

## 5.1 Como as peças se encaixam

O ERP **só registra, calcula o que a lei fecha e avisa; não bloqueia** (D-N284). A ordem é:

- **(1)** **Há plataforma?** A nota tem `Indicador_Intermediador` = `plataforma_terceiros`, ou o usuário cria a linha. O Motor propõe a linha de `Mov_Plataforma_Operacao` e o usuário confirma.
- **(2)** **Quem é a empresa na operação?** `Papel_Empresa`: plataforma, fornecedor ou adquirente.
- **(3)** **Há vínculo?** O Motor procura `Cad_Participante_Plataforma_Fornecedor` vigente na data: opção, anuência, condição informada.
- **(4)** **Qual o fundamento?** O Motor aplica a ordem do 5.4 e grava `Responsabilidade_Plataforma`; o usuário pode mudar, e `Origem_Responsabilidade` registra quem decidiu.
- **(5)** **Qual o valor?** Uma linha por imposto (`Mov_Plataforma_Operacao_Tributo`): o devido, o pago pela plataforma, a alíquota usada e a diferença.

| Entidade ou campo | Para quê | Vigência | Campos |
|---|---|---|---|
| `Cad_Participante_Plataforma_Fornecedor` (nova) | O vínculo entre a plataforma e o fornecedor: opção, anuência e condição informada | sim | 17 |
| `Mov_Plataforma_Operacao` (nova) | A operação intermediada e a responsabilidade da plataforma nela | não | 27 |
| `Mov_Plataforma_Operacao_Tributo` (nova) | O devido, o pago e a diferença, por imposto | não | 13 |
| `Cad_Empresa_Perfil_Fiscal`: 6 campos | A empresa é plataforma e o que controla | sim (já tem) | 21 para 27 |

## 5.2 As entidades novas

### `Cad_Participante_Plataforma_Fornecedor` (Contabilidade & Fiscal, com vigência, 17 campos)

O vínculo entre uma plataforma e um fornecedor, visto da empresa do ERP. Existe porque a opção do § 12 e do § 13 depende da **anuência do fornecedor** e dura no tempo, e porque o fornecedor precisa saber que a plataforma emite e paga em nome dele. Serve aos dois lados: a empresa que **é** a plataforma e a empresa que **vende por** ela. Não guarda a responsabilidade, que é da operação.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Plataforma_Fornecedor` | identificador | Chave. |
| `ID_Participante_Plataforma_Fornecedor_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Participante_Plataforma_Fornecedor_Versao). Fase 0, seção 2. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | A empresa do ERP: a plataforma ou o fornecedor, conforme `Papel_Empresa`. |
| `Papel_Empresa` | enumeração {plataforma, fornecedor} --- identidade | O lado em que a empresa está neste vínculo. |
| `ID_Participante_Contraparte` | referência (Cad_Participante) --- identidade | A outra ponta: o fornecedor, quando a empresa é a plataforma; a plataforma, quando a empresa é o fornecedor. |
| `Identificador_Na_Plataforma` | código (60), opcional | O código do vendedor cadastrado na plataforma (a nota leva o mesmo dado em `idCadIntTran`; este fica no cadastro). |
| `Condicao_Informada_Administracao` | enumeração {contribuinte, nao_contribuinte}, opcional | LC 214, art. 22, § 4º; Decreto, art. 20, § 3º: a condição do fornecedor residente no País **não inscrito**, informada pela administração à plataforma. Vazia quando o fornecedor está inscrito. |
| `Data_Informacao_Administracao` | data, opcional | Quando a administração informou. |
| `Opcao_Plataforma` | enumeração {nenhuma, emite_e_paga, substituta_tributaria} | `emite_e_paga`: a plataforma emite os documentos em nome do fornecedor e paga o imposto pelo valor da operação (art. 22, § 12). `substituta_tributaria`: emite, apura e paga (§ 13). Padrão `nenhuma`. Vale só para fornecedor residente no País, com anuência. |
| `Data_Anuencia_Fornecedor` | data, opcional | Quando o fornecedor concordou. Obrigatória quando a opção não é `nenhuma`. |
| `ID_Documento_Anuencia` | referência (Cad_Documento), opcional | A anuência do fornecedor. A forma é do ato conjunto, que não li; o ERP guarda e não valida. |
| `Calcula_Por_Aliquota_Referencia` | booleano | A plataforma que optou (§§ 12 a 14) calcula pela alíquota de referência quando não tem a informação das regras do fornecedor (§ 15). A diferença vai em `Mov_Plataforma_Operacao_Tributo`. Padrão falso. |
| `ID_Usuario_Registro` | referência (Cad_Usuario), opcional | Quem registrou. |
| `Fundamento_Legal` | texto, opcional | O artigo ou o ato que sustenta a opção. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

Regras de conferência: a unicidade é por `ID_Empresa`, `Papel_Empresa` e `ID_Participante_Contraparte` na vigência; `Data_Anuencia_Fornecedor` é obrigatória quando `Opcao_Plataforma` não é `nenhuma`; `Condicao_Informada_Administracao` só se preenche quando o fornecedor não tem inscrição.

### `Mov_Plataforma_Operacao` (Contabilidade & Fiscal, movimento, 27 campos)

Uma linha por operação intermediada. Guarda quem é quem, o documento fiscal, o fundamento da responsabilidade e o que a lei exige da plataforma naquela operação. Várias linhas podem apontar para o mesmo documento (consolidado).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Plataforma_Operacao` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa do ERP na operação. |
| `Papel_Empresa` | enumeração {plataforma, fornecedor, adquirente} | O lado da empresa. |
| `ID_Participante_Plataforma` | referência (Cad_Participante), opcional | A plataforma. Vazio quando a empresa é a plataforma. |
| `ID_Participante_Fornecedor` | referência (Cad_Participante), opcional | O fornecedor. Vazio quando a empresa é o fornecedor. |
| `ID_Participante_Adquirente` | referência (Cad_Participante), opcional | O adquirente ou destinatário. Vazio quando a empresa é o adquirente ou quando é consumidor sem cadastro. |
| `ID_Participante_Plataforma_Fornecedor` | referência (Cad_Participante_Plataforma_Fornecedor), opcional | O vínculo vigente na data da operação; vazio quando não há. |
| `Identificador_Pedido_Plataforma` | código (60), opcional | O pedido na plataforma; liga a operação à transação de pagamento (LC 214, art. 32, § 2º-A). |
| `Data_Operacao` | data | A data da operação intermediada. |
| `Tipo_Operacao` | enumeração {interna, importacao, remessa_internacional} | Decide a hipótese: fornecedor no exterior é `importacao` ou `remessa_internacional` (art. 22, I; arts. 64, § 5º, IX, e 96). |
| `Valor_Operacao` | número | O valor da operação intermediada, base do pagamento pela plataforma (§ 12, II). |
| `ID_Documento_Fiscal` | referência (Mov_Documento_Fiscal), opcional | O documento fiscal da operação; vazio quando não foi emitido. Vários registros podem apontar o mesmo (documento consolidado, Q159-10). |
| `Emissor_Documento` | enumeração {fornecedor, plataforma_em_nome_do_fornecedor, nao_emitido} | Quem emitiu (Decreto, art. 115, VII). |
| `Data_Devida_Emissao` | data, opcional | A data em que o fornecedor deveria ter emitido; começa os 30 dias do § 14. Só quando o documento não foi emitido pelo fornecedor no prazo. |
| `Fornecedor_Contribuinte` | enumeração {contribuinte_regime_regular, contribuinte_regime_favorecido, contribuinte_nao_inscrito, nao_contribuinte, nao_informado}, opcional | A condição do fornecedor **naquela data**, gravada na operação (lida da qualificação, do regime e da condição informada). Decide o § 10 e o inciso II, "b". |
| `Controla_Elemento_Essencial` | booleano | A plataforma controla ao menos um dos quatro elementos na operação (§ 1º, II). Vem do perfil da empresa; o usuário muda por operação. Falso: § 11. |
| `Responsabilidade_Plataforma` | enumeração {nao_responsavel_sem_elemento_essencial, nao_responsavel_nenhuma_hipotese, solidaria_fornecedor_exterior, solidaria_sem_informacao, solidaria_sem_documento, solidaria_nao_registrada, por_opcao_emissao_e_pagamento, substituta_tributaria} | O **fundamento principal** (Anexo B). O Motor grava pela ordem do 5.4. |
| `Origem_Responsabilidade` | enumeração {calculado_pelo_sistema, informado_pelo_usuario} | Quem decidiu o valor acima. |
| `Responde_Por_Diferenca` | booleano, opcional | Falso quando o § 7º se aplica (split possível e informações prestadas). Só vale para fornecedor residente no País. |
| `Regra_Apuracao_Debito` | enumeração {regras_do_fornecedor, regime_regular, aliquota_referencia}, opcional | Como o débito foi apurado: pelas regras do fornecedor (§ 10, I), pelo regime regular (§ 10, II) ou pela alíquota de referência (§ 15). |
| `Situacao_Informacao_Operacao` | enumeração {nao_exigida, pendente, prestada} | A informação das operações ao Comitê Gestor e à RFB (§ 5º). Sem prazo nem leiaute nas fontes lidas; o padrão é `nao_exigida`. |
| `Split_Disponivel` | booleano, opcional | Marcador: o split é possível na liquidação (§ 7º, I). O ERP **não calcula** split (D-N282). |
| `Informacao_Split_Prestada` | booleano, opcional | Marcador: a plataforma prestou as informações do § 6º. |
| `Sujeito_Passivo_Acrescimos` | enumeração {nao_se_aplica, fornecedor_exclusivamente, plataforma_e_fornecedor} | De quem se exigem os acréscimos e a penalidade por falta de documento: só do fornecedor quando a plataforma emite em 30 dias e paga (§ 14); dos dois nos demais casos de solidariedade. O ERP só registra (D-N284). |
| `Recolhido_Pelo_Cambio` | booleano, opcional | Marcador do art. 23, parágrafo único, I: o imposto foi segregado na remessa pela instituição de câmbio, pela alíquota de referência. |
| `Situacao` | enumeração {calculado, lancado, cancelado} | O mesmo padrão de `Mov_Cbs_Ajuste_Operacao`. |
| `Observacao` | texto, opcional | Os outros fundamentos que também se aplicam, quando há mais de um (achado 12). |

### `Mov_Plataforma_Operacao_Tributo` (Contabilidade & Fiscal, movimento, 13 campos)

Uma linha por imposto (CBS ou IBS) da operação: o devido, o pago pela plataforma e a diferença. A base e a alíquota **nunca são digitadas**: vêm da apuração do documento.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Plataforma_Operacao_Tributo` | identificador | Chave. |
| `ID_Plataforma_Operacao` | referência (Mov_Plataforma_Operacao) --- identidade | A operação. |
| `ID_Imposto` | referência (Cad_Imposto) --- identidade | CBS ou IBS. |
| `Valor_Devido_Na_Operacao` | número | O imposto devido na operação, pelas regras do fornecedor ou do regime regular (`Regra_Apuracao_Debito`). |
| `Valor_Pago_Pela_Plataforma` | número, opcional | O que a plataforma pagou ou segregou, pelo valor e pelas informações da operação. |
| `Percentual_Aplicado` | número, opcional | A alíquota usada no pagamento; a de referência, quando a regra é `aliquota_referencia`. |
| `Valor_Diferenca` | número, opcional | O módulo da diferença entre o devido e o pago; o sentido está em `Sentido_Diferenca`. |
| `Sentido_Diferenca` | enumeração {sem_diferenca, a_pagar, a_devolver} | `a_pagar` quando a alíquota incidente é maior que a de referência; `a_devolver` quando é menor (§ 15; art. 23, parágrafo único). |
| `Parte_Da_Diferenca` | enumeração {fornecedor, adquirente_ou_importador}, opcional | Quem paga ou recebe a diferença. O art. 23 diz adquirente ou importador; o § 15 não diz (C289). |
| `ID_Titulo_Diferenca` | referência (Mov_Titulo), opcional | O título a pagar ou a receber da diferença, quando o usuário o gera. |
| `Situacao_Diferenca` | enumeração {nao_se_aplica, aberta, liquidada, cancelada} | O estado da diferença. |
| `Data_Liquidacao_Diferenca` | data, opcional | Quando a diferença foi paga ou devolvida. |
| `ID_Espelho_Conta` | referência (Mov_Cbs_Apuracao_Espelho_Conta), opcional | A linha da Plataforma da CBS que corresponde a este registro, para a conferência (só CBS; o IBS fica sem espelho até haver o regulamento do Comitê Gestor). |

Regra de conferência: a unicidade é por `ID_Plataforma_Operacao` e `ID_Imposto`.

## 5.3 Campos novos na entidade que já existe

| Entidade | Campo | Tipo | Para quê |
|---|---|---|---|
| `Cad_Empresa_Perfil_Fiscal` | `Eh_Plataforma_Digital` | booleano (padrão falso) | A empresa é plataforma digital (LC 214, art. 22, § 1º). Liga os demais campos e o aviso de inscrição (art. 23) |
| `Cad_Empresa_Perfil_Fiscal` | `Controla_Cobranca` | booleano, opcional | O elemento essencial "cobrança" (§ 1º, II, "a"). Vazio quando não é plataforma |
| `Cad_Empresa_Perfil_Fiscal` | `Controla_Pagamento` | booleano, opcional | "Pagamento" (§ 1º, II, "b") |
| `Cad_Empresa_Perfil_Fiscal` | `Controla_Termos_Condicoes` | booleano, opcional | "Definição dos termos e condições" (§ 1º, II, "c") |
| `Cad_Empresa_Perfil_Fiscal` | `Controla_Entrega` | booleano, opcional | "Entrega" (§ 1º, II, "d") |
| `Cad_Empresa_Perfil_Fiscal` | `Atividade_Unica_Excluida` | enumeração {nenhuma, acesso_internet, servico_pagamento, publicidade, busca_comparacao_sem_cobranca_por_venda}, opcional | A única atividade que, sozinha, **tira** a empresa do conceito de plataforma (§ 2º). Vazio quando não é plataforma |

**Valores e carga** (sem campo novo):

| Entidade | Mudança |
|---|---|
| `Cad_Participante_Classe` | **2 valores novos** em `Classe`: `plataforma_digital` e `importador` (Q116-3; o segundo é do B1 e ficou de fora) |
| `Cad_Parametro_Legal_Ibs_Cbs` | **Carga:** `prazo_emissao_plataforma_dias` = 30 (dias corridos; LC 214, art. 22, § 14; Decreto, art. 20, § 11) e `percentual_receita_nanoempreendedor_plataforma` = 25 (percentual; LC 214, art. 26, § 10; Decreto, art. 25, § 14), ambos provisórios (C287 a C295 e o B2) |
| `Mov_Documento_Fiscal` | **Nenhum campo novo:** só a descrição de `ID_Participante_Emitente` passa a dizer que, no documento emitido pela plataforma, ele aponta o fornecedor em cujo nome o documento sai (Q212-7) |
| `Mov_Cbs_Ajuste_Operacao` | **Nenhuma mudança:** `Papel_Emitente_Documento` já tem `plataforma_digital` |
| `Cad_Participante_Qualificacao_Cbs` | **Nenhuma mudança:** a inscrição da plataforma é a qualificação de regime regular |

## 5.4 Como o Motor decide o fundamento

A ordem é fixa e vale só para `Papel_Empresa` = `plataforma` e `fornecedor`; para o `adquirente`, o Motor só preenche a diferença do art. 23.

| Ordem | Condição | `Responsabilidade_Plataforma` | Fundamento |
|---:|---|---|---|
| 1 | `Controla_Elemento_Essencial` falso | `nao_responsavel_sem_elemento_essencial` | LC 214, art. 22, § 11 |
| 2 | `Tipo_Operacao` é `importacao` ou `remessa_internacional` | `solidaria_fornecedor_exterior` | Art. 22, I; art. 64, § 5º, IX; art. 96 |
| 3 | Fornecedor no País e `Situacao_Informacao_Operacao` diferente de `prestada`, **com informação exigida** | `solidaria_sem_informacao` | Art. 22, II, "a" |
| 4 | Vínculo vigente com `Opcao_Plataforma` = `substituta_tributaria` e anuência registrada | `substituta_tributaria` | Art. 22, § 13 |
| 5 | Vínculo vigente com `Opcao_Plataforma` = `emite_e_paga` e anuência registrada | `por_opcao_emissao_e_pagamento` | Art. 22, § 12 |
| 6 | Fornecedor contribuinte (inscrito ou não) e `Emissor_Documento` = `nao_emitido` | `solidaria_sem_documento` | Art. 22, II, "b" |
| 7 | `ID_Documento_Fiscal` vazio | `solidaria_nao_registrada` | Art. 22, II, "c" |
| 8 | Nenhuma das anteriores | `nao_responsavel_nenhuma_hipotese` | Art. 22, caput (sem hipótese) |

**A ordem entre as linhas 3 a 7 é leitura minha** (achado 12; C290). Quando mais de uma linha se aplica, o Motor grava a primeira, escreve as outras em `Observacao` e mostra todas no aviso.

**Débito (`Regra_Apuracao_Debito`).** Fornecedor residente no País e **inscrito** como contribuinte, no regime regular ou em regime favorecido: `regras_do_fornecedor` (§ 10, I). Nos demais casos: `regime_regular`, com alíquotas, regimes diferenciados e regimes específicos do regime regular (§ 10, II). A `aliquota_referencia` só vale se o vínculo tem `Calcula_Por_Aliquota_Referencia`, falta a informação das regras do fornecedor **e** o fundamento é um dos das linhas 4, 5 e 6 (§ 15, que remete aos §§ 12 a 14).

**Diferença.** Se a alíquota incidente é maior que a de referência, `a_pagar`; se é menor, `a_devolver` (§ 15). No art. 23, a parte é o adquirente ou o importador; no § 15 a parte é a pergunta C289.

**`Responde_Por_Diferenca`.** Falso quando `Split_Disponivel` e `Informacao_Split_Prestada` são verdadeiros e `Situacao_Informacao_Operacao` é `prestada`, para fornecedor residente no País (§ 7º). Verdadeiro nos demais casos.

**`Sujeito_Passivo_Acrescimos`.** `fornecedor_exclusivamente` quando o fundamento é `solidaria_sem_documento`, a plataforma emitiu o documento em até `prazo_emissao_plataforma_dias` contados de `Data_Devida_Emissao` e pagou (§ 14); `plataforma_e_fornecedor` nos demais fundamentos de solidariedade; `nao_se_aplica` nos outros.

## 5.5 O que o ERP faz em cada papel

| Papel | O que registra | O que avisa |
|---|---|---|
| **Plataforma** | Uma linha por operação intermediada, com o fundamento, o documento (que ela mesma emite, nas opções), o devido e o pago por imposto, a informação do § 5º e a diferença | Falta de vínculo, de anuência, de inscrição, de elemento essencial; prazo de 30 dias; diferença sem título (avisos 1 a 3, 5, 6, 9 a 13) |
| **Fornecedor** | Uma linha por venda feita pela plataforma, com o que a plataforma assumiu (emitir, pagar, substituir) e a diferença a pagar ou a receber | Documento próprio duplicado de operação que a plataforma emite em nome dele (aviso 4); fornecedor não inscrito sem condição informada (aviso 7) |
| **Adquirente** | A linha da importação ou remessa intermediada, com a diferença do art. 23 e o marcador de recolhimento no câmbio | Diferença do adquirente ou importador em aberto (aviso 8) |

## 5.6 Ligações com os outros blocos

- **B1 (comércio exterior).** A importação e a remessa internacional são do B1. O B7 só diz que a plataforma responde e guarda a diferença do adquirente. O fallback do courier (Decreto, art. 175, II) é do B1.
- **B2 (qualificação).** A inscrição da plataforma e a condição do fornecedor vêm de `Cad_Participante_Qualificacao_Cbs`. A linha de carga dos 25% do nanoempreendedor completa o B2.
- **B0a (ajuste da operação).** O documento de ajuste da operação substituída é emitido pela plataforma (Decreto, art. 59, § 2º) e `Papel_Emitente_Documento` já tem o valor.
- **B5 (agência de turismo).** `Cad_Participante_Modelo_Intermediacao` é a remuneração do intermediário do serviço. Não se confunde com o vínculo do B7.
- **Documento 159 (documento consolidado).** A Q159-10 deixou o consolidado sem campo; o B7 mantém, pela ligação de várias operações a um documento.
- **PSP e split.** Adiados (D-N282 e D-N391). O B7 põe só os dois marcadores. O art. 32, § 2º, II, da lei (a plataforma informa o prestador de pagamento) é do módulo do PSP.
- **EFD-ICMS/IPI, registro 1601.** `Mov_Titulo_Baixa.ID_Participante_Intermediador` e `ID_Participante_Instituicao_Pagamento` continuam como estão. A Q176-E2 (a baixa por cartão ou marketplace chega com a credenciadora?) segue aberta com a equipe.
- **Restaurante e bar.** O art. 274, parágrafo único, II, da lei (art. 399, § 1º, II, do decreto) exclui da base os valores não repassados ao restaurante pelo serviço de entrega e intermediação por plataforma; é do B5 (bar e restaurante) e não está neste desenho.

# 6. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|---|---|---|
| 1 | Nota com intermediador sem vínculo cadastrado | `Indicador_Intermediador` = `plataforma_terceiros` e não há vínculo vigente com o participante intermediador |
| 2 | Opção sem anuência | `Opcao_Plataforma` diferente de `nenhuma` e `Data_Anuencia_Fornecedor` vazia |
| 3 | Prazo de 30 dias vencendo ou vencido | `Emissor_Documento` = `nao_emitido`, fornecedor contribuinte, e passaram `prazo_emissao_plataforma_dias` de `Data_Devida_Emissao` (a plataforma perde a limitação do § 14) |
| 4 | Documento duplicado | A empresa é fornecedora, o vínculo tem opção de emitir e a empresa emitiu documento próprio da mesma operação |
| 5 | Plataforma sem elemento essencial | `Eh_Plataforma_Digital` verdadeiro e nenhum `Controla_*` verdadeiro, ou `Atividade_Unica_Excluida` diferente de `nenhuma` |
| 6 | Plataforma sem inscrição no regime regular | `Eh_Plataforma_Digital` verdadeiro e sem `Cad_Participante_Qualificacao_Cbs` vigente com `contribuinte_regime_regular` (art. 23) |
| 7 | Fornecedor não inscrito sem condição informada | Fornecedor residente no País sem inscrição e sem `Condicao_Informada_Administracao` (a plataforma não sabe se ele é contribuinte, § 4º) |
| 8 | Diferença do adquirente ou importador | Operação de importação ou remessa com `Recolhido_Pelo_Cambio` verdadeiro e diferença em aberto |
| 9 | Diferença sem título | `Sentido_Diferenca` diferente de `sem_diferenca`, `Situacao_Diferenca` = `aberta` e `ID_Titulo_Diferenca` vazio |
| 10 | Informação das operações pendente | `Situacao_Informacao_Operacao` = `pendente` (só depois de o ato fixar prazo) |
| 11 | Plataforma responde pela diferença | `Responde_Por_Diferenca` verdadeiro e `Split_Disponivel` ou `Informacao_Split_Prestada` falsos |
| 12 | Fundamento informado diferente do calculado | `Origem_Responsabilidade` = `informado_pelo_usuario` e o Motor calcularia outro valor |
| 13 | Fornecedor em regime favorecido e opção de substituir | `Fornecedor_Contribuinte` = `contribuinte_regime_favorecido` e fundamento `substituta_tributaria` (as regras do Simples dependem da C291) |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| Q212-1 | Aprova a entidade **`Cad_Participante_Plataforma_Fornecedor`** (17 campos) como no 5.2, servindo aos dois lados pelo `Papel_Empresa`? | Sim |
| Q212-2 | Aprova **`Mov_Plataforma_Operacao`** (27 campos) e **`Mov_Plataforma_Operacao_Tributo`** (13 campos) como no 5.2? | Sim |
| Q212-3 | Aprova os **6 campos novos** de `Cad_Empresa_Perfil_Fiscal` (5.3)? | Sim |
| Q212-4 | Acrescenta os valores **`plataforma_digital`** e **`importador`** em `Cad_Participante_Classe.Classe` (Q116-3, que ficaram de fora)? | Sim |
| Q212-5 | Aceita que a responsabilidade fique em **um valor** (o fundamento principal, 8 valores) pela **ordem do 5.4**, com os outros fundamentos em `Observacao`? A ordem é leitura minha e vai ao contador (C290) | Sim, provisório |
| Q212-6 | Aceita os dois **marcadores de split** (`Split_Disponivel` e `Informacao_Split_Prestada`), sem cálculo, compatíveis com o split adiado (D-N282)? | Sim |
| Q212-7 | Aceita que o documento emitido pela plataforma em nome do fornecedor use `Mov_Documento_Fiscal` **sem campo novo**, com `ID_Participante_Emitente` apontando o fornecedor, até o ato e o leiaute saírem? | Sim |
| Q212-8 | Aceita que o Motor **proponha a linha de operação** quando a nota traz intermediador de plataforma de terceiros, e o usuário confirme? | Sim |
| Q212-9 | Aprova as **2 linhas de parâmetro** (30 dias e 25% do nanoempreendedor), ambas provisórias até o contador validar? | Sim |
| Q212-10 | Aceita **IBS e CBS na mesma linha de operação** (uma linha de tributo por imposto), embora só o Decreto da CBS tenha sido lido e o regulamento do IBS esteja ausente? | Sim |
| Q212-11 | Mantém o papel **`adquirente`** (art. 23, parágrafo único, e art. 97), ou deixa só plataforma e fornecedor? | Manter |
| Q212-12 | Aprova os **13 avisos** do Motor (seção 6) e as **12 regras** de texto do Anexo A? | Sim |
| Q212-13 | **Há hoje cliente ou empresa do grupo que opere uma plataforma ou venda por plataforma?** A resposta decide a prioridade da implantação do B7 (como a Q158-E4 fez com a ZFM). | Responder |

# 8. O que acontece se você aprovar

- **Tudo (Q212-1 a Q212-13):** 3 entidades novas, **63 campos** (57 nas entidades novas e 6 em `Cad_Empresa_Perfil_Fiscal`), **14 campos de referência** (4 + 6 + 4), nenhum domínio novo, 2 valores novos de enumeração e 2 linhas de parâmetro. Sobre a revisão 40: **1.201 entidades, 13.801 campos, 3.568 campos de referência e 360 domínios**; entidades mestres de 244 para 245. São somas minhas, a conferir no "consolidar".
- **Carga:** 2 linhas de parâmetro (provisórias) e 12 regras de texto (Anexo A). Não há carga de vínculo nem de operação: são dados da empresa.
- **Ao contador:** nove perguntas novas, C287 a C295 (documento 188, Parte 17).
- **Se a Q212-1 vier "não":** a empresa fornecedora não sabe se a plataforma emite e paga em nome dela, e o aviso de duplicidade cai; a plataforma perde onde guardar a anuência.
- **Se a Q212-13 vier "não há":** o desenho fica aprovado e a implantação espera cliente, como o PSP.
- **Nada é aplicado antes de "consolidar".**

# 9. Limites

- **Não li:** o **ato conjunto da RFB e do CGIBS** que o art. 22 manda editar (critérios da opção e da anuência, forma do documento consolidado, informações do § 5º e do split); o **regulamento do IBS** do Comitê Gestor; **nota técnica de leiaute** de documento fiscal com plataforma; os **arts. 31 a 35 da LC 214** (split, só as remissões); e o **regime de tributação simplificada** dos arts. 93 a 95 e da legislação aduaneira.
- **Não achei** na LC nem no Decreto o prazo para a plataforma prestar a informação do § 5º. Por isso `Situacao_Informacao_Operacao` tem o padrão `nao_exigida` e o aviso 10 só passa a valer com o ato.
- **A ordem de precedência do 5.4** (linhas 3 a 7) é leitura minha. A lei lista as hipóteses sem dizer qual prevalece.
- **A anuência do fornecedor** é só guardada. O ERP não valida a forma exigida pelo ato conjunto.
- **A mesma regra para IBS e CBS** é suposição: o texto lido para o IBS é só o da LC.
- **O PSP e o split** continuam fora (D-N282 e D-N391): nenhuma entidade de segregação, recolhimento ou tolerância mensal foi desenhada.
- **O `importador`** entra só como valor da classe; o processo da importação é do B1.
- **Nada foi conferido com a Receita nem com o Comitê Gestor**; as leituras são do texto das normas.

# Anexo A. As 12 regras provisórias do Motor

| Regra | Se | Resultado | Fundamento | Vigência |
|---|---|---|---|---|
| R1 | `Controla_Elemento_Essencial` falso | `nao_responsavel_sem_elemento_essencial` | LC 214, art. 22, § 11 | 01/01/2027 |
| R2 | `Tipo_Operacao` é `importacao` ou `remessa_internacional` | `solidaria_fornecedor_exterior`; débito pelo regime regular; `Recolhido_Pelo_Cambio` quando a plataforma ou o fornecedor no exterior não se inscreveu | Art. 22, I e § 10, II; art. 23, parágrafo único; art. 64, § 5º, IX; art. 96 | 01/01/2027 |
| R3 | Fornecedor no País; informação do § 5º exigida e não prestada | `solidaria_sem_informacao` | Art. 22, II, "a" | 01/01/2027 |
| R4 | Vínculo com `substituta_tributaria` e anuência | `substituta_tributaria`; documento emitido pela plataforma; débito pelo § 10, I ou II | Art. 22, § 13 | 01/01/2027 |
| R5 | Vínculo com `emite_e_paga` e anuência | `por_opcao_emissao_e_pagamento` | Art. 22, § 12 | 01/01/2027 |
| R6 | Fornecedor contribuinte; documento não emitido | `solidaria_sem_documento`; se a plataforma emite em 30 dias e paga, acréscimos só do fornecedor | Art. 22, II, "b", e § 14 | 01/01/2027 |
| R7 | Operação sem documento fiscal | `solidaria_nao_registrada` | Art. 22, II, "c" | 01/01/2027 |
| R8 | Nenhuma das anteriores | `nao_responsavel_nenhuma_hipotese` | Art. 22, caput | 01/01/2027 |
| R9 | Débito do fornecedor residente no País inscrito (regular ou favorecido) | `regras_do_fornecedor`; senão `regime_regular`; `aliquota_referencia` se o vínculo permite, falta a informação e o fundamento é R4, R5 ou R6 | Art. 22, §§ 10 e 15 | 01/01/2027 |
| R10 | Alíquota incidente maior ou menor que a de referência | `a_pagar` ou `a_devolver`; parte: fornecedor (§ 15) ou adquirente ou importador (art. 23) | Art. 22, § 15; art. 23, parágrafo único | 01/01/2027 |
| R11 | Split possível, informação do § 6º prestada e do § 5º prestada, fornecedor no País | `Responde_Por_Diferenca` falso | Art. 22, § 7º | 01/01/2027 |
| R12 | Fornecedor sem inscrição e sem condição informada | Aviso 7; débito pelo regime regular | Art. 22, §§ 4º e 10, II | 01/01/2027 |

A vigência de 01/01/2027 é a do início do IBS e da CBS plenos para o regime regular; a Lei 214 já vale desde 2026, mas a responsabilidade da plataforma só tem efeito com a operação tributada (leitura minha).

# Anexo B. Valores das enumerações novas

**`Responsabilidade_Plataforma` (8 valores):**

| Código | Quando | Fundamento |
|---|---|---|
| `nao_responsavel_sem_elemento_essencial` | A plataforma não controla nenhum dos quatro elementos na operação | Art. 22, § 11 |
| `nao_responsavel_nenhuma_hipotese` | Nenhuma das hipóteses do caput nem das opções se aplica | Art. 22, caput |
| `solidaria_fornecedor_exterior` | Fornecedor no exterior: solidária com o adquirente e em substituição ao fornecedor | Art. 22, I |
| `solidaria_sem_informacao` | Fornecedor no País; a plataforma não presta as informações do § 5º | Art. 22, II, "a" |
| `solidaria_sem_documento` | Fornecedor contribuinte não emite o documento fiscal no valor da operação | Art. 22, II, "b" |
| `solidaria_nao_registrada` | A operação não é registrada em documento fiscal eletrônico | Art. 22, II, "c" |
| `por_opcao_emissao_e_pagamento` | A plataforma optou, com anuência, por emitir em nome do fornecedor e pagar | Art. 22, § 12 |
| `substituta_tributaria` | A plataforma optou, com anuência, por ser substituta (emitir, apurar e pagar) | Art. 22, § 13 |

**Outras enumerações:**

| Campo | Valores |
|---|---|
| `Opcao_Plataforma` | `nenhuma`, `emite_e_paga`, `substituta_tributaria` |
| `Papel_Empresa` (vínculo) | `plataforma`, `fornecedor` |
| `Papel_Empresa` (operação) | `plataforma`, `fornecedor`, `adquirente` |
| `Tipo_Operacao` | `interna`, `importacao`, `remessa_internacional` |
| `Emissor_Documento` | `fornecedor`, `plataforma_em_nome_do_fornecedor`, `nao_emitido` |
| `Fornecedor_Contribuinte` | `contribuinte_regime_regular`, `contribuinte_regime_favorecido`, `contribuinte_nao_inscrito`, `nao_contribuinte`, `nao_informado` |
| `Regra_Apuracao_Debito` | `regras_do_fornecedor`, `regime_regular`, `aliquota_referencia` |
| `Situacao_Informacao_Operacao` | `nao_exigida`, `pendente`, `prestada` |
| `Sujeito_Passivo_Acrescimos` | `nao_se_aplica`, `fornecedor_exclusivamente`, `plataforma_e_fornecedor` |
| `Sentido_Diferenca` | `sem_diferenca`, `a_pagar`, `a_devolver` |
| `Parte_Da_Diferenca` | `fornecedor`, `adquirente_ou_importador` |
| `Situacao_Diferenca` | `nao_se_aplica`, `aberta`, `liquidada`, `cancelada` |
| `Atividade_Unica_Excluida` | `nenhuma`, `acesso_internet`, `servico_pagamento`, `publicidade`, `busca_comparacao_sem_cobranca_por_venda` |
| `Condicao_Informada_Administracao` | `contribuinte`, `nao_contribuinte` |

# Anexo C. LC 214 e Decreto 12.955: correspondência dos dispositivos

| Tema | LC 214 (com a LC 227) | Decreto 12.955 (só CBS) |
|---|---|---|
| Responsabilidade da plataforma (I e II) | Art. 22, caput | Art. 20, caput |
| Conceito de plataforma e elementos essenciais | Art. 22, § 1º | Art. 20, § 1º |
| Quem não é plataforma | Art. 22, § 2º | Art. 20, § 2º |
| Dispensa de inscrição do fornecedor no exterior que opera só por plataforma inscrita | Art. 22, § 3º | **Não repetido** |
| Condição de contribuinte informada pela administração | Art. 22, § 4º | Art. 20, § 3º |
| Informações das operações ao Comitê Gestor e à RFB | Art. 22, § 5º | Art. 20, § 4º |
| Split quando a plataforma inicia o pagamento | Art. 22, § 6º | Art. 20, § 5º (o § 6º define "disponível") |
| Sem responsabilidade pela diferença | Art. 22, § 7º | Art. 20, § 7º |
| Débito pelas regras do fornecedor ou do regime regular | Art. 22, § 10 | Art. 20, § 8º |
| Sem elemento essencial, sem responsabilidade | Art. 22, § 11 | **Não repetido** (decorre do § 1º, II) |
| Emitir documentos em nome do fornecedor e pagar | Art. 22, § 12 | Art. 20, § 9º |
| Substituta tributária | Art. 22, § 13 | Art. 20, § 10 |
| Prazo de 30 dias e acréscimos só do fornecedor | Art. 22, § 14 | Art. 20, § 11 |
| Alíquota de referência e diferença | Art. 22, § 15 | Art. 20, § 12 |
| Inscrição da plataforma | Art. 23, caput | Art. 105, § 1º |
| Não inscritos no exterior: câmbio e diferença | Art. 23, parágrafo único | Art. 21 |
| Importação por plataforma | Art. 64, § 5º, IX | Art. 72 |
| Remessa internacional | Arts. 95, 96 e 97 | Arts. 172, 173 e 178 |
| Documento emitido pela plataforma | Art. 22, §§ 12, I, e 13, I | Art. 59, § 2º; art. 115, VII |
| Nanoempreendedor, 25% da receita | Art. 26, § 10 | Art. 25, § 14 |

# Anexo D. Perguntas ao contador (C287 a C295, documento 188, Parte 17)

| Id | Assunto |
|---|---|
| C287 | A opção do § 12 do art. 22 (emitir os documentos e pagar): as duas partes são independentes ou formam um pacote? A plataforma pode pagar sem emitir em nome do fornecedor? |
| C288 | O que prova que a plataforma "controla" cobrança, pagamento, termos e condições ou entrega (§ 1º, II) e se o controle vale por operação ou por canal de venda |
| C289 | A diferença "devolvida" do § 15: a quem, por qual meio (compensação, split ou restituição), em que prazo e quem calcula; e se o § 15 vale fora das hipóteses dos §§ 12 a 14 |
| C290 | Quando mais de um fundamento se aplica (caput I, II "a", "b" e "c" e as opções), qual prevalece; e se a plataforma optante que não presta a informação do § 5º continua protegida pelo § 7º |
| C291 | Fornecedor em regime favorecido (Simples, MEI, nanoempreendedor): o que significa apurar "pelas regras do fornecedor" na substituição do § 13 e como a plataforma sabe o enquadramento |
| C292 | Documento emitido pela plataforma em nome do fornecedor: quem consta como emitente, qual certificado assina, o que muda na chave de acesso e como o fornecedor recebe o documento; e o prazo do ato do documento consolidado |
| C293 | Informações do § 5º: leiaute, periodicidade e prazo; como a plataforma identifica o fornecedor que não é contribuinte; e desde quando é exigível |
| C294 | Split e § 7º: enquanto o split não existe para o meio de pagamento (Pix, cartão, boleto), a plataforma responde pela diferença? Como vale a fase gradual do split (Decreto, art. 33) |
| C295 | Fornecedor no exterior dispensado de inscrição por operar só por plataforma inscrita (§ 3º): como se prova o "exclusivamente"; e como isso convive com o recolhimento no câmbio do art. 23, parágrafo único |
