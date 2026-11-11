# Integra Contador (Serpro): Estrutura das Chamadas, Catálogo de Serviços e Cenários MIT, DCTFWeb e PGMEI — Documento 57 (revisão 2)

*Materiais que Alberto enviou em 13/10/2026: a página de introdução da API Integra Contador na loja de APIs do Serpro (seções 1 a 7, lida com a ferramenta de leitura de páginas) e, na revisão 2 (seções 8 a 10), os textos colados das páginas de cenários de demonstração do MIT, da DCTFWeb e do PGMEI. As páginas de cenários não puderam ser lidas pela ferramenta (o site bloqueia a leitura automática); Alberto colou o texto. Não altera o dicionário (837 entidades); as decisões D-N134 a D-N139 aguardam o "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N134 a D-N139 (Integra Contador), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

A página é só a **introdução técnica** da API: a URL base, os cinco caminhos de serviço e o formato do corpo da requisição. Ela **não traz** o Catálogo de Serviços (a lista de sistemas, códigos de serviço e versões), a autenticação, o formato das respostas, os códigos de erro nem os limites de uso. Esses pontos ficam em outras páginas que ainda não li.

O dicionário já tem o canal do Integra Contador (D-N3 e D-N103): `Cad_Integra_Contador_Configuracao`, `Canal_Envio` no Simples e no MIT, `Canal_Retorno` na DCTFWeb e o registro de tentativas em `Mov_Simples_Transmissao`. O cruzamento mostra **duas lacunas**:

1. Toda chamada exige o tipo de operação, o código do sistema, o código do serviço e a versão do sistema. O dicionário guarda só um enum solto de serviço no Simples (`Servico`, 4 valores) e **nada disso** em MIT e DCTFWeb.
2. O autor do pedido pode ser o contratante, um procurador ou o próprio contribuinte. A configuração só prevê a procuração do e-CAC, sem dizer quem assina o pedido.

Alberto respondeu as duas (seção 5): catálogo de serviços com vigência (D-N134) e papel do autor do pedido na configuração (D-N135).

**Revisão 2 (seções 8 a 10).** Os cenários do MIT, da DCTFWeb e do PGMEI trazem 14 serviços com código real, um sexto caminho (`/Transmitir`) que a página inicial não lista, e vários detalhes que contradizem a página inicial ou entre si. Resultado: o catálogo recebe 14 linhas provisórias (D-N136), o tipo de operação vira domínio extensível (D-N137), nasce um registro genérico das chamadas (D-N138) e MIT e DCTFWeb ganham os campos que a API exige (D-N139). PGMEI não ganha campos agora: as páginas não mostram o sentido do indicador de benefício nem a resposta da dívida ativa.

# 2. O que a página diz

| Ponto | Conteúdo da página |
|---|---|
| URL base | `https://gateway.apiserpro.serpro.gov.br/integra-contador/v1/` (a versão `v1` faz parte do caminho) |
| Ambiente de demonstração | Existe uma API "trial", marcada como apenas para demonstração |
| Caminhos | `/Apoiar` (serviços de apoio), `/Consultar`, `/Declarar` (entrega de declarações), `/Emitir` (comprovantes, guias e documentos de arrecadação) e `/Monitorar` (eventos de monitoração). Qual serviço usa qual caminho está no Catálogo de Serviços |
| Padrões | REST/JSON, HTTPS, método POST, camelCase, UTF-8 |
| `contratante` | `numero` (CNPJ com dígito verificador, sem máscara) e `tipo` (somente 2, CNPJ) |
| `autorPedidoDados` | Quem faz o pedido: o contratante, um procurador ou o contribuinte. `numero` aceita CPF (`tipo` 1) ou CNPJ (`tipo` 2) |
| `contribuinte` | CPF (`tipo` 1) ou CNPJ (`tipo` 2) de quem é objeto da operação ou da consulta |
| `pedidoDados` | `idSistema`, `idServico`, `versaoSistema` e `dados`; `dados` é uma **string JSON escapada** com os parâmetros do sistema acionado (exemplo da página: `cnpjBasico`, `pa` e `dataConsolidacao`) |

# 3. Cruzamento com o dicionário

| Elemento da chamada | Onde está hoje | Situação |
|---|---|---|
| Contratante (só CNPJ) | `Cad_Integra_Contador_Configuracao.ID_Participante_Contratante` | Cobre; falta a regra de que o contratante é pessoa jurídica |
| Contribuinte (CPF ou CNPJ) | `ID_Empresa` da configuração (a empresa aceita pessoa física desde a revisão 3) e o participante do registro de origem | Cobre |
| Autor do pedido | Só `ID_Procuracao` (e-CAC) | **Lacuna** (D-N135) |
| Tipo de operação (cinco caminhos) | Não existe | **Lacuna** (D-N134) |
| `idSistema`, `idServico`, `versaoSistema` | Não existem | **Lacuna** (D-N134) |
| `dados` (parâmetros) | `ID_Documento_Envio` no GED (Simples) | Cobre; é a prova do que foi enviado |
| Retorno, protocolo e erro | `Protocolo`, `Codigo_Retorno`, `Mensagem_Retorno`, `ID_Documento_Retorno` (Simples); campos próprios em MIT e DCTFWeb | Cobre; o formato real da resposta não foi lido |
| Ambiente | `Ambiente` {producao, homologacao} | Cobre; o "trial" é só para demonstração e fica coberto por homologação |

# 4. Desenho proposto

## D-N134: catálogo de serviços do Integra Contador

Entidade nova **`Cad_Integra_Contador_Servico`**, com vigência (padrão da Fase 0: identidade mais versão, `Vigencia_Fim` sempre preenchida com 31/12/9999). Ela guarda uma linha por serviço do Catálogo do Serpro. É a aplicação do critério geral de Alberto: regra externa que muda entra como parâmetro com vigência, não como código fixo.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Integra_Contador_Servico** | *identificador* | Identidade do serviço. |
| **ID_Integra_Contador_Servico_Versao** | *identificador da versão* | Chave primária da versão. |
| **ID_Tipo_Operacao** | *referência (Cad_Classe_Sistema, domínio = tipo_operacao_integra_contador)* | Caminho da API em que o serviço é chamado. Alterado na revisão 2 (D-N137): era um enum fechado de 5 valores. |
| **Id_Sistema** | *código (até 30)* | Valor de `idSistema` do pedido. |
| **Id_Servico** | *código (até 60)* | Valor de `idServico` do pedido. |
| **Versao_Sistema** | *código (até 10), opcional* | Valor de `versaoSistema` do pedido. Opcional na revisão 2: dois serviços do MIT não a trazem no exemplo da página. |
| **Modulo_Erp** | *enumeração {simples, mei, mit, dctfweb, outros}* | Módulo do ERP que usa o serviço. |
| **Servico_Interno** | *código (até 60)* | Nome do serviço dentro do ERP (por exemplo, o equivalente a `transmitir_declaracao` ou `gerar_das`), para o motor de envio escolher a linha. |
| **Descricao** | *texto* | Descrição do serviço conforme o catálogo. |
| **Exige_Procuracao** | *sim/não, opcional* | Se o serviço só funciona com procuração do contribuinte no e-CAC. Fica vazio na carga: as páginas não dizem. |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *data, data, texto opcional* | Padrão de vigência. |

**Carga inicial: 14 linhas provisórias** (D-N136, seção 8): os serviços das páginas de cenários do MIT, da DCTFWeb e do PGMEI. O Catálogo de Serviços oficial não foi lido; nenhum código foi inventado, e a carga é conferida com o catálogo e o Swagger quando chegarem.

Alterações em entidades existentes:

| Entidade | Mudança |
|---|---|
| `Mov_Simples_Transmissao` | Novo `ID_Integra_Contador_Servico` (referência, opcional; obrigatório quando `Canal` = integra_contador). O enum `Servico` continua como nome interno. |
| `Mov_Mit_Apuracao` e `Mov_Dctfweb_Declaracao` | **Revisão 2:** a referência ao serviço deixa de ficar nessas duas entidades e passa para `Mov_Integra_Contador_Chamada` (D-N138), que registra cada chamada. |

## D-N135: autor do pedido na configuração

`Cad_Integra_Contador_Configuracao` ganha:

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **Papel_Autor_Pedido** | *enumeração {contratante, procurador, contribuinte}* | Quem assina o pedido (`autorPedidoDados`). Padrão: contratante. |
| **ID_Participante_Autor_Pedido** | *referência (Cad_Participante, opcional)* | Autor do pedido quando não for o contratante. Aceita pessoa física ou jurídica. |

Regras: `ID_Procuracao` passa a ser obrigatória só quando o papel é `procurador`; o contratante (`ID_Participante_Contratante`) deve ser pessoa jurídica (a página inicial diz que a API só aceita tipo 2; **os exemplos da DCTFWeb usam contratante CPF, tipo 1, então na revisão 2 a regra fica só como aviso, não como bloqueio, até o Swagger confirmar**); o autor com papel `contribuinte` tem de ser o próprio contribuinte da empresa da configuração. A auditoria do ERP não valida se a procuração cobre o serviço (isso é do e-CAC); só avisa quando `Exige_Procuracao` = sim e não há procuração vigente.

# 5. Perguntas e respostas de Alberto (13/10/2026)

| Decisão | Opções apresentadas | Resposta |
|---|---|---|
| D-N134 (serviços) | Catálogo com vigência; catálogo mais registro único de chamadas; só campos soltos; esperar o Catálogo | **Catálogo com vigência** (recomendado) |
| D-N135 (autor do pedido) | Papel na configuração; papel por chamada; não guardar | **Papel na configuração** (recomendado) |

# 6. Impacto na revisão 5 (conta da primeira versão; a revisão 2 atualiza na seção 10)

| Parte da revisão 5 | Entidades novas | Entidades alteradas |
|---|---|---|
| Contagem anterior (documentos 53 a 56) | 6 (837 para 843) | no mínimo 20 |
| Documento 57 (D-N134 e D-N135) | 1 (`Cad_Integra_Contador_Servico`) | 4 (`Cad_Integra_Contador_Configuracao`, `Mov_Simples_Transmissao`, `Mov_Mit_Apuracao`, `Mov_Dctfweb_Declaracao`) |
| **Total** | **7 (837 para 844)** | **no mínimo 24**, a recontar na consolidação (`Mov_Simples_Transmissao` pode coincidir com a alteração da DeSTDA das D-N106 a D-N117) |

Nada foi consolidado. O dicionário continua com 837 entidades.

# 7. Fontes e verificação

**Lido:** a página inicial da documentação da API Integra Contador (URL base, caminhos, corpo da requisição). A leitura devolveu um resumo da página; os campos e valores da seção 2 vêm dele.

**Não lido (pendente):** (ver também a seção 9) o Catálogo de Serviços (sistemas, códigos de serviço, versões e qual caminho cada um usa); a página de autenticação e contratação (como o Serpro entrega o token e se há procuração por serviço); o formato das respostas e os códigos de erro; os limites de uso; o Swagger de demonstração. Peço a Alberto os links dessas páginas.

**Não conferido:** se o corpo da requisição mudou desde que a página foi publicada (a página não traz data).

# 8. Cenários de demonstração: MIT, DCTFWeb e PGMEI (revisão 2)

Alberto colou o texto das páginas de cenários (versão de 10/04/2026) do MIT, da DCTFWeb e do PGMEI. Todas as chamadas usam a API de demonstração (`/integra-contador-trial/v1/`) e dizem que os cabeçalhos `jwt_token` e `autenticar_procurador_token` só são obrigatórios em produção. A lista de sistemas do menu da página tem 25 sistemas: AUTENTICAPROCURADOR, CAIXAPOSTAL, CCMEI, DCTFWEB, DEFIS, DTE, E-PROCESSO, EVENTOSATUALIZACAO, MIT, PAGTOWEB, PARCMEI-ESP, PARCMEI, PARCSN-ESP, PARCSN, PERTMEI, PERTSN, PGDASD, PGMEI, PNRCONTADOR, PROCURACOES, REGIMEAPURACAO, RELPMEI, RELPSN, SICALC e SITFIS. Só MIT, DCTFWeb e PGMEI foram colados.

## 8.1 Os 14 serviços

| Sistema | `idServico` | Caminho no exemplo | Versão no exemplo | Campos de `dados` no exemplo | Serviço interno proposto |
|---|---|---|---|---|---|
| MIT | ENCAPURACAO314 | /Declarar | 1.0 | PeriodoApuracao (MesApuracao, AnoApuracao), DadosIniciais (SemMovimento, QualificacaoPj, TributacaoLucro, VariacoesMonetarias, RegimePisCofins, ResponsavelApuracao.CpfResponsavel), Debitos por tributo (Irpj, Csll, PisPasep, Cofins, com IdDebito, CodigoDebito, CnpjScp, ValorDebito) | encerrar_apuracao_mit |
| MIT | SITUACAOENC315 | /Apoiar | 1.0 | protocoloEncerramento | consultar_situacao_encerramento_mit |
| MIT | CONSAPURACAO316 | /Consultar | não informada | IdApuracao | consultar_apuracao_mit |
| MIT | LISTAAPURACOES317 | /Consultar | não informada | mesApuracao, anoApuracao, situacaoApuracao (o exemplo usa 3, sob o título "situação encerrada") | listar_apuracoes_mit |
| DCTFWEB | GERARGUIA31 | /Emitir | 1.0 | categoria, anoPA, mesPA, numeroReciboEntrega | gerar_guia_dctfweb |
| DCTFWEB | GERARGUIAANDAMENTO313 | /Emitir | 1.0 | categoria, anoPA, mesPA | gerar_guia_andamento_dctfweb |
| DCTFWEB | CONSRECIBO32 | /Consultar | 1.0 | categoria (aqui numérica, 40), anoPA, mesPA, numeroReciboEntrega | consultar_recibo_dctfweb |
| DCTFWEB | CONSDECCOMPLETA33 | /Consultar | 1.0 | categoria, anoPA, mesPA, numeroReciboEntrega | consultar_relatorio_declaracao_completa_dctfweb |
| DCTFWEB | CONSXMLDECLARACAO38 | /Consultar | 1.0 | categoria, anoPA, mesPA | consultar_xml_declaracao_dctfweb |
| DCTFWEB | TRANSDECLARACAO310 | **/Transmitir** | 1.0 | categoria, anoPA, mesPA, `xmlAssinadoBase64` (o XML da declaração, assinado, em base64) | transmitir_declaracao_dctfweb |
| PGMEI | GERARDASPDF21 | /Emitir | 1.0 | periodoApuracao (AAAAMM, exemplo "201901") | gerar_das_mei_pdf |
| PGMEI | GERARDASCODBARRA22 | /Emitir | 1.0 | periodoApuracao | gerar_das_mei_codigo_barras |
| PGMEI | ATUBENEFICIO23 | /Emitir | 1.0 | anoCalendario, infoBeneficio (lista de periodoApuracao e indicadorBeneficio verdadeiro ou falso) | atualizar_beneficio_mei |
| PGMEI | DIVIDAATIVA24 | /Consultar | 1.0 | anoCalendario | consultar_divida_ativa_mei |

Nenhum exemplo traz a resposta, então formato de retorno, códigos de erro e conteúdo dos "avisos DCTFWeb" (dois cenários do MIT se chamam "resposta sem avisos" e "resposta com avisos") continuam desconhecidos.

## 8.2 Divergências nas próprias páginas

| Ponto | O que as páginas mostram | Tratamento |
|---|---|---|
| Sexto caminho | A transmissão da DCTFWeb chama `/Transmitir`; a página inicial só lista cinco caminhos | Domínio extensível com `transmitir` marcado a confirmar (D-N137) |
| Contratante pessoa física | Os exemplos DCTFWeb de consulta de XML e de transmissão usam contratante, autor e contribuinte com `tipo` 1 (CPF); a página inicial diz que o contratante é só `tipo` 2 | A regra do D-N135 vira aviso, não bloqueio |
| Autor do pedido | Nos dois serviços de consulta do MIT, `autorPedidoDados` vem com `cpfCnpj` em vez de `numero` | Provável erro da página; o conector segue a página inicial até o Swagger |
| `versaoSistema` | Ausente nos dois serviços de consulta do MIT; no PGMEI aparece antes de `idServico` | Campo opcional no catálogo |
| Categoria da DCTFWeb | Texto (`GERAL_MENSAL`, `PF_MENSAL`) na maioria dos serviços e número (40) em `CONSRECIBO32` | O domínio `categoria_dctfweb` ganha o nome usado pela API (D-N139) |
| JSON de exemplo | Vários campos `dados` e blocos do corpo têm vírgulas, chaves e aspas faltando (por exemplo `ENCAPURACAO314`, `ATUBENEFICIO23`) | Os exemplos não servem de leiaute; os campos de `dados` vêm do Swagger |
| Datas dos exemplos | A DCTFWeb usa competência 11/2027 e o PGMEI 01/2019 | Valores de teste; sem efeito no desenho |

## 8.3 O XML de exemplo da transmissão

O `xmlAssinadoBase64` do serviço de transmissão é um XML de verdade. Decodifiquei o começo (até a categoria) para comparar com `Mov_Dctfweb_Declaracao`: raiz `ProcDctf` (namespace `http://www.serpro.gov.br/dctf/v1`), `ConteudoDeclaracao`, `DctfXml` de tipo `DctfXml_v3`, versão `3.0`, e o bloco `A000-DadosIdentificadoresContribuinte` com `nomeContribuinte`, `tipoInscContrib` (2), `inscContrib`, `perApuracao` (`062022`), `clasTrib` (21), `indRetificacao` (2), `numRecibo`, `indOrgEstrang` (0), `indConteudo` (1), `indZerada` (1) e `categoriaDCTF` (50). Depois vêm os blocos A005 (cadastro), A008 (contato), A030 (deduções da Lei 9.711), A050 (créditos tributários apurados) e a assinatura XML (SHA-256, certificado X.509). O que isso confirma e o que levanta:

| Ponto | Conferência |
|---|---|
| `perApuracao` | No exemplo tem 6 posições, MMAAAA (`062022`). O dicionário dizia que o formato exato dependia do primeiro XML real; esta amostra indica MMAAAA. Continua a confirmar com um XML real, porque os dados de teste são fictícios |
| `indRetificacao`, `numRecibo`, `indZerada`, `categoriaDCTF` | Mapeiam para `Indicador_Retificacao`, `Numero_Recibo_Anterior` (na retificadora), `Sem_Movimento` e `ID_Categoria` |
| `categoriaDCTF` 50 com `categoria` `PF_MENSAL` | Indício de que 50 é a categoria Geral PF; e `CONSRECIBO32` com 40 no mesmo recibo e competência de `GERAL_MENSAL` indica 40 = Geral. O manual não dizia qual código é qual; os dois indícios vêm de dados de teste, então **não carrego o nome da API até um XML real confirmar** |
| `clasTrib`, `indOrgEstrang`, `indConteudo` | Não têm coluna em `Mov_Dctfweb_Declaracao`; ficam no `Xml_Retorno` importado. Conferir com o esquema de saída (documento 43) quando o primeiro XML real chegar. Sem decisão nova |
| Assinatura | O fluxo é: consultar o XML (`CONSXMLDECLARACAO38`), assinar com o e-CNPJ e transmitir (`TRANSDECLARACAO310`). `ID_Certificado` (que assinou a transmissão) já existe |

# 9. Decisões da revisão 2

Alberto respondeu as quatro perguntas como recomendado (13/10/2026).

## D-N136: carga provisória de 14 serviços em `Cad_Integra_Contador_Servico`

As 14 linhas da seção 8.1, com `Modulo_Erp` = mit, dctfweb ou mei (PGMEI é o DAS-MEI), tipo de operação conforme o caminho do exemplo, `Versao_Sistema` = 1.0 (vazia nos dois serviços do MIT que não a trazem), `Exige_Procuracao` vazio e fonte "páginas de cenários trial, 10/04/2026". Provisória, passa pela validação de dados legais provisórios e é conferida com o Catálogo de Serviços e o Swagger.

## D-N137: tipo de operação como domínio extensível

Novo domínio `tipo_operacao_integra_contador` em `Cad_Classe_Sistema`, com 6 valores: apoiar, consultar, declarar, emitir, monitorar e transmitir (este a confirmar). `Cad_Integra_Contador_Servico.ID_Tipo_Operacao` aponta para ele no lugar do enum fechado do D-N134.

## D-N138: registro genérico das chamadas

Nova entidade **`Mov_Integra_Contador_Chamada`**, no padrão de `Mov_Simples_Transmissao` (que continua como está), usada por MIT, DCTFWeb, PGMEI e pelos serviços que vierem.

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Integra_Contador_Chamada** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | Empresa do contribuinte. |
| **ID_Integra_Contador_Configuracao** | *referência (Cad_Integra_Contador_Configuracao)* | Configuração do canal usada. |
| **ID_Integra_Contador_Servico** | *referência (Cad_Integra_Contador_Servico)* | Serviço chamado (sistema, serviço, versão e caminho). |
| **Origem_Tipo** | *enumeração {apuracao_mit, declaracao_dctfweb, das_mei, declaracao_anual_mei, outro}* | Tipo do registro de origem da chamada. |
| **ID_Origem** | *identificador do registro de origem, opcional* | Registro de origem conforme `Origem_Tipo`; vazio quando é uma consulta sem origem. |
| **Papel_Autor_Pedido** | *enumeração {contratante, procurador, contribuinte}* | Cópia do papel usado na chamada (D-N135). |
| **Canal** | *enumeração {integra_contador, portal_manual}* | Via usada (D-N3 e D-N103). |
| **Motivo_Canal_Manual** | *enumeração {sem_contrato, fora_do_ar, servico_indisponivel_para_a_empresa}, opcional* | Por que a chamada foi pelo canal manual. |
| **Situacao** | *enumeração {enviada, processada, rejeitada, erro_comunicacao, registrada_manual, aguardando_manual}* | Mesma regra de `Mov_Simples_Transmissao`: `aguardando_manual` quando o limite de tentativas com erro de comunicação é atingido. |
| **Tentativa** | *número* | Número da tentativa para a mesma origem e serviço. |
| **Protocolo** | *código (até 60), opcional* | Protocolo devolvido pelo serviço (por exemplo o protocolo de encerramento do MIT). |
| **Codigo_Retorno** | *código (até 20), opcional* | Código de retorno. |
| **Mensagem_Retorno** | *texto, opcional* | Mensagem de retorno. |
| **Data_Hora_Envio** | *data/hora* | Quando a chamada foi feita ou, no canal manual, registrada. |
| **ID_Documento_Envio** | *referência (Cad_Documento, opcional)* | O pedido enviado (incluindo o XML assinado), guardado no GED. |
| **ID_Documento_Retorno** | *referência (Cad_Documento, opcional)* | O retorno ou o recibo (PDF, XML), guardado no GED. |
| **ID_Usuario_Registro** | *referência (Cad_Usuario, opcional)* | Quem registrou à mão a chamada feita no portal. |

## D-N139: campos do MIT, da DCTFWeb e de `Cad_Classe_Sistema` (provisórios)

| Entidade | Mudança |
|---|---|
| `Mov_Mit_Apuracao` | Novos: `Id_Apuracao_Receita` (número, opcional; o `IdApuracao` que a Receita devolve e que a consulta usa); `Protocolo_Encerramento` (código até 60, opcional); `ID_Situacao_Apuracao_Receita` (referência a `Cad_Classe_Sistema`, domínio novo `situacao_apuracao_mit`, opcional; carga: 3 = encerrada, o único valor que as páginas indicam). `Status` ganha `encerramento_enviado` (entre `arquivo_gerado` e `encerrada_no_ecac`). `Referencia_Canal` fica para o canal manual. |
| **`Mov_Mit_Aviso`** (entidade nova, mínima) | `ID_Aviso_Mit`, `ID_Apuracao_Mit`, `ID_Integra_Contador_Chamada` (opcional), `Codigo_Aviso` (código até 20, opcional), `Mensagem_Aviso` (texto) e `Data_Hora_Consulta`. Guarda os avisos da DCTFWeb que a consulta da situação do encerramento devolve; revista quando o formato da resposta chegar. |
| `Mov_Dctfweb_Declaracao` | Novos: `Canal_Transmissao` (enumeração {manual, api_integra_contador}, opcional) e `ID_Documento_Xml_Assinado` (referência a `Cad_Documento`, opcional). `Status` ganha `transmitida_pelo_erp`. `Motivo_Canal_Manual` passa a valer também para a transmissão. |
| `Cad_Classe_Sistema` | Novo campo opcional `Codigo_Externo_Integra_Contador` (código até 40): o valor que a API usa para aquele valor do domínio (por exemplo o nome da categoria da DCTFWeb). **Carga vazia** em `categoria_dctfweb` até um XML real confirmar a correspondência (seção 8.3). |

Dois domínios novos em `Cad_Classe_Sistema`: `tipo_operacao_integra_contador` e `situacao_apuracao_mit`.

## PGMEI: sem desenho agora

As páginas do PGMEI mostram só quatro serviços e seus parâmetros. **Atualizar Benefício** manda um indicador verdadeiro ou falso por período de apuração, mas a página não diz qual benefício é nem o que o indicador muda; **Consultar Dívida Ativa** consulta por ano-calendário, sem mostrar o que volta. O dicionário do MEI (`Cad_Mei_Parametro`, `Mov_Mei_Das`, `Mov_Mei_Declaracao_Anual`) não tem campo de benefício nem entidade de dívida ativa. Os quatro serviços entram só no catálogo; os campos esperam o manual do PGMEI e o Swagger. A chamada do DAS-MEI e da consulta já fica registrada em `Mov_Integra_Contador_Chamada` com `Origem_Tipo` = das_mei.

# 10. Impacto na revisão 5 (contagem final do documento 57)

| Parte da revisão 5 | Entidades novas | Entidades alteradas |
|---|---|---|
| Documentos 53 a 56 | 6 (837 para 843) | no mínimo 20 |
| Documento 57, seção 4 (D-N134 e D-N135) | 1 (`Cad_Integra_Contador_Servico`) | `Cad_Integra_Contador_Configuracao`, `Mov_Simples_Transmissao`, `Mov_Mit_Apuracao`, `Mov_Dctfweb_Declaracao` (4) |
| Documento 57, seção 9 (D-N136 a D-N139) | 2 (`Mov_Integra_Contador_Chamada` e `Mov_Mit_Aviso`) | 0 novas (`Mov_Mit_Apuracao`, `Mov_Dctfweb_Declaracao` e `Cad_Classe_Sistema` já contadas) |
| **Total** | **9 (837 para 846)** | **no mínimo 24**, a recontar na consolidação |

Domínios: dois novos em `Cad_Classe_Sistema` (`tipo_operacao_integra_contador` e `situacao_apuracao_mit`), além dos que as outras decisões da revisão 5 criarem. Nada foi consolidado; o dicionário continua com 837 entidades.

# 11. Perguntas e respostas de Alberto (revisão 2, 13/10/2026)

| Decisão | Opções apresentadas | Resposta |
|---|---|---|
| D-N137 (tipo de operação) | Domínio extensível; enum fechado com 6 valores; esperar o Swagger | **Domínio extensível** (recomendado) |
| D-N136 (carga de 14 serviços) | Carga provisória; deixar vazia | **Carga provisória** (recomendado) |
| D-N138 (registro das chamadas) | Entidade genérica; uma por módulo; esperar as respostas | **Entidade genérica** (recomendado) |
| D-N139 (campos do MIT e da DCTFWeb) | Incluir provisório; só o MIT; esperar | **Incluir, provisório** (recomendado) |

# 12. Fontes e verificação da revisão 2

**Lido:** o texto colado por Alberto das páginas "Cenários MIT", "Cenários DCTFWEB" e "Cenários PGMEI" (versão de 10/04/2026) e o começo do XML do serviço de transmissão (decodificado de base64 para a comparação da seção 8.3). As páginas de cenários não puderam ser abertas pela ferramenta de leitura (o site bloqueia a leitura automática) e não tentei outro caminho.

**Não lido (pendente):** o Catálogo de Serviços oficial; o Swagger de cada sistema (campos de `dados`, respostas, códigos de erro e se `/Transmitir` existe); as páginas "Como contratar", "Como autenticar na API" e "Modelos de autenticação" (token, `jwt_token`, `autenticar_procurador_token` e o serviço AUTENTICAPROCURADOR); as páginas dos outros 22 sistemas da lista (entre eles PGDASD, DEFIS, SICALC, PAGTOWEB, PROCURACOES, REGIMEAPURACAO, CAIXAPOSTAL, SITFIS, DTE e os parcelamentos, que o dicionário já cobre em parte).

**Não conferido:** os códigos e os caminhos acima valem para a API de demonstração; os de produção vêm do Swagger.
