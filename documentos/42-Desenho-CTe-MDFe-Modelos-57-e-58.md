# Desenho do CT-e e do MDF-e, modelos 57 e 58, com a NT 2026.004 — Documento 42

*Análise dos leiautes oficiais do MDF-e (modelo 58, schemas 3.00b e MOC) e do CT-e (modelos 57, 67 e 64, schemas 4.00 com a NT 2026.004 de IBS e CBS) que Alberto enviou, contra o dicionário e contra o que os documentos 33 a 41 já tinham proposto. Propostas de ajuste, nada consolidado: o dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Li os três pacotes de schemas do MDF-e 3.00b (NT 2024.001, 2024.002 e 2025.001), o MOC 3.00b (Visão Geral e Anexo I), o DAMDFE, o pacote de schemas do CT-e 4.00 (NT 2026.004, RTC 1.00 com 47 XSD), o MOC 4.00 e a própria NT 2026.004, e comparei campo a campo com o dicionário e com a classificação dos documentos 33 e 34. São 355 linhas folha do MDF-e e 1.270 do CT-e (CT-e 57 com o Simplificado, CT-e OS, GTV-e, os modais e os eventos).

No MDF-e, **25 linhas já estão cobertas** pelo dicionário, 83 por propostas dos documentos 33 e 34, 34 são derivadas, 74 ficam só no XML e **139 são lacunas** (67 campos novos e 72 que pedem entidade nova). No CT-e, **440 estão cobertas**, 224 por propostas, 121 derivadas, 270 só no XML e **215 são lacunas** (84 campos novos e 131 em entidade nova). Pouco do MDF-e está coberto porque o dicionário não tem nada de manifesto: o que existe é a proposta A.5 do documento 33.

**Uma correção ao que se supunha.** `Mov_Cte`, `Mov_Mdfe` e as demais entidades da seção A.5 do documento 33, e também `Mov_Documento_Fiscal`, `Mov_Dfe_Evento` e o framework, são propostas ainda não consolidadas: o `model.json` tem 543 entidades e nenhuma de CT-e, MDF-e ou DF-e. Quando este documento diz "proposta dos docs 33/34", é isso. O desenho que proponho trata o CT-e emitido como nota de saída (com um item de serviço) mais `Mov_Cte`, o CT-e recebido como nota de entrada mais `Mov_Cte`, e o MDF-e fora das notas, só com `Mov_Mdfe` e filhas, ligado à Expedição. São **16 entidades novas**, 22 ajustes a entidades existentes ou propostas, 12 domínios novos e 35 parâmetros com vigência, além de três correções à proposta do documento 33: o CT-e não tem "anulação", o CIOT é do MDF-e e o CST do ICMS é por item.

**Datas que pesam.** A NT 2026.004 entra em homologação em 13/10/2026 e em produção em 16/11/2026: valores líquidos, fim da EPEC e da FS-DA, contingência offline e o evento de crédito presumido do tomador. A nova estrutura do CT-e Simplificado entra em 16/11/2026 e 14/12/2026. A NT se contradiz em três pontos que o desenho registra sem resolver (datas do ICMS previsto, fórmula do total do documento e redação do evento 211110). Em ambos os leiautes, prazo, alíquota, data e lista são parâmetro com vigência (`Cad_Dfe_Parametro_Regra`), nunca código.

Faltou material: o Anexo I do MOC do CT-e, os pacotes anteriores de schemas e os textos das NTs do MDF-e (seção 2). Por isso o histórico de versões é medido só no MDF-e (seção 5). Proponho as **decisões D-N66 a D-N72** (seção 11). Nada foi alterado no dicionário.

# 2. Fontes lidas

| Fonte | Versão e data | O que contém | Uso neste documento |
|---|---|---|---|
| Schemas do MDF-e 3.00b, pacote da NT 2024.001 | PL_MDFe_300b_NT012024_v1.02; 41 XSD | Leiaute do MDF-e antes das duas NTs seguintes. Não há pacote anterior a este | Linha de base da comparação de versões (seção 5) |
| Schemas do MDF-e 3.00b, pacote da NT 2024.002 | PL_MDFe_300b_NT022024_1.02; 41 XSD | Acrescenta a prestação parcial e amplia `xSolic` | Comparado com o pacote da NT 2024.001 |
| Schemas do MDF-e 3.00b, pacote da NT 2025.001 | PL_MDFe_300b_NT012025_1.04 (a pasta interna chama-se "1.05"); 41 XSD | CNPJ alfanumérico e ajustes do pagamento, do vale-pedágio, do produto predominante e do aquaviário | Leiaute vigente: base da classificação campo a campo (355 linhas) |
| MOC do MDF-e 3.00b, Visão Geral | Agosto de 2022; 82 páginas | Serviços, contingência, uso indevido, eventos (tabela 3.7.1 e capítulo 6), QR Code, regras por evento | Regras de negócio e prazos da seção 4; todos os prazos viram parâmetro |
| MOC do MDF-e 3.00b, Anexo I (leiaute e regras de validação) | Agosto de 2022; 45 páginas | Todas as regras de validação com código de rejeição (grupos F, G, K) | Regras de negócio e prazos da seção 4 |
| DAMDFE (documento Word) | Datado "agosto (2021)"; 119 linhas | Impressão do manifesto | Só como referência de impressão; não cria campo |
| Schemas do CT-e 4.00, pacote da NT 2026.004 (RTC 1.00) | PL_CTe_400_NT2026.004 RTC_1.00; 47 XSD | CT-e (57), CT-e OS (67), GTV-e (64), CT-e Simplificado, os sete leiautes de modal (rodoviário, rodoviário OS, aéreo, aquaviário, ferroviário, dutoviário e multimodal) e 14 eventos | Base da classificação campo a campo (1.270 linhas) |
| MOC do CT-e 4.00, Visão Geral | Agosto de 2022; 102 páginas (anterior às NTs da reforma) | Serviços, contingência, tabela 3.7.1 de eventos, capítulos 12 e 13 (CFOP e campos impedidos de carta de correção) | Eventos e prazos do CT-e (seções 3 e 6) |
| NT 2026.004 do CT-e, Reforma Tributária do Consumo | Versão 1.00, setembro de 2026; 16 páginas | Valores líquidos, ICMS previsto, alíquotas de transição, vTotDFe, fim da EPEC e da FS-DA, emissão offline, estrutura do CT-e Simplificado e evento 211110 | Seção 6 inteira |
| Pacote de evento "Insucesso do CT-e" (pasta bt) | Evento_InsucessoCTe_PL_v1.01 | Eventos 610190 e 610191, registrados no ambiente nacional sobre o CT-e | Documento 38 já os deixa adiados; aqui só conferidos |
| Pacote de evento "Registro de Passagem Automático originado no MDF-e" (pasta bt) | Evento_RegPasAutoMDFe_PL_v1.01 | Evento 510630 | Documento 38 já o deixa adiado; o MOC do MDF-e lista o 510620 (conflito na pendência Q-13) |

**Material que não chegou.** Cada item abaixo limita uma parte da análise e consta também na aba "Pendências" da planilha.

| Nº | O que faltou | O que há no lugar | Efeito |
|---|---|---|---|
| F-1 | Anexo I do MOC do CT-e (leiaute e regras de validação campo a campo) | Não foi enviado. As regras do CT-e que conheço vêm da Visão Geral, da NT 2026.004 e dos schemas; as dos grupos de documentos, do ICMS e das validações por modal não foram vistas | Regra de negócio do CT-e fica incompleta; a classificação de campos não depende dele |
| F-2 | Schemas do CT-e anteriores ao pacote da NT 2026.004 e as NTs do CT-e anteriores | Só há um pacote do CT-e | Não foi possível fazer a comparação de versões do CT-e; só o histórico do MDF-e (seção 5) tem diferenças medidas |
| F-3 | Pacote do MDF-e anterior à NT 2024.001 e os textos das três NTs do MDF-e | Só os schemas das três NTs chegaram | A NT 2024.001 não pode ser descrita por diferença (é a linha de base); o motivo de cada mudança é inferido do próprio schema |
| F-4 | Schemas de envio, retorno e distribuição DF-e do CT-e | O pacote do CT-e traz recepção do CT-e, eventos e consultas, mas não a distribuição | Recepção do CT-e emitido por terceiro (frete comprado) fica sem a mensagem de distribuição lida; ver Q-12 |
| F-5 | Tabela de crédito presumido (cCredPres) | **Resolvida em parte.** A planilha `IT 2025.002 v.1.70 - cCredPres.xlsx` (13 códigos, com marca para NF-e, NFC-e, CT-e e NFS-e) chegou em 05/10/2026 no pacote da NFCom (documento 40). Falta só conferir se coincide com o Anexo IV citado pela NT 2026.004 do CT-e, que não foi lido | O catálogo `Cad_Credito_Presumido_Ibs_Cbs` pode ser carregado com os 13 códigos e as vigências da planilha; o ERP valida localmente as regras 1061 a 1071 |
| F-6 | Tabelas do MOC do MDF-e (embarcações, portos, terminais) e a tabela de cClassTrib aplicável ao CT-e | Não foram enviadas | Aquaviário fica fora da primeira onda; cClassTrib do CT-e reaproveita `Cad_Cclasstrib` e `Cad_Cclasstrib_Documento` |
| F-7 | Lista de CFOP aceitos no CT-e (capítulo 12 do MOC) conferida com a NT de CFOP de 2026 | O MOC de 2022 traz a lista; a NT de CFOP não foi enviada | A lista vai para carga com vigência, e não para o código (Q-11) |

# 3. Framework: como entram os modelos 57, 58, 64 e 67

O framework dos documentos 33 e 34 já atende qualquer modelo por cadastro: um modelo novo é uma linha em `Cad_Classe_Sistema` (domínio `modelo_documento_fiscal`), uma versão em `Cad_Dfe_Leiaute`, uma ou mais linhas em `Cad_Autoridade_Fiscal_Atendimento` e a configuração do emitente em `Cad_Dfe_Emitente_Configuracao`. O que a D-N6 deixa para quando houver cliente e leiaute oficial é só a entidade de conteúdo; para o CT-e e o MDF-e o leiaute oficial chegou e o documento 33 já propôs o conteúdo (A.5). A D-N1 (chave e protocolo no Documento Fiscal e na nota) vale para o CT-e emitido e recebido, e a D-N51 (tipo de autorizador no protocolo) vale com as posições da tabela abaixo: a chave do CT-e e do MDF-e tem 44 posições e não carrega o site do autorizador.

Duas regras guiam o desenho: regra legal é parâmetro com vigência e nunca código; e o ERP não limita o tipo de cliente (o evento 211110, por exemplo, vale para qualquer tomador de transportador autônomo ou MEI, e não só para um perfil de empresa).

| Item do framework | CT-e 57 | CT-e OS 67 | GTV-e 64 | MDF-e 58 |
|---|---|---|---|---|
| Linha em `Cad_Classe_Sistema` (domínio `modelo_documento_fiscal`) | 57 (inclui o CT-e Simplificado, que tem raiz própria e `tpCTe` 5 e 6) | 67 | 64 | 58 |
| Raiz do XML e versão do leiaute em `Cad_Dfe_Leiaute` | `CTe` e `CTeSimp`; 4.00 (NT 2026.004, RTC 1.00) | `CTeOS`; 4.00 | `GTVe`; 4.00 | `MDFe`; 3.00 (MOC 3.00b), pacote da NT 2025.001 |
| Autoridade em `Cad_Autoridade_Fiscal_Atendimento` | SEFAZ da UF do emitente, ou SVRS e SVSP (SEFAZ Virtual) quando a UF delega; contingência pela SVC-RS (tpEmis 7) e SVC-SP (tpEmis 8) | Igual ao 57 | Igual ao 57 (tpEmis só 1 e 2) | Ambiente Nacional (SVRS) único; não há roteamento por UF |
| Prefixo do protocolo (1 posição, D-N51) | 1 normal, 2 alternativo, 3 SEFAZ Virtual-RS, 5 SEFAZ Virtual-SP, 7 SVC-RS, 8 SVC-SP | Igual ao 57 | Igual ao 57 | 9 Ambiente Nacional, 2 site alternativo |
| Formas de emissão em `Tipo_Emissao` | 1 normal, 2 contingência offline, 3 regime especial NFF, 7 e 8 SVC. A NT 2026.004 elimina 4 (EPEC) e 5 (FS-DA) e aceita o 2 de imediato | 1, 2, 7, 8 | 1 e 2 | 1 normal, 2 contingência offline, 3 NFF |
| Processo de emissão (`procEmi`) | 0 aplicativo do contribuinte, 3 aplicativo do SEBRAE, 4 PAA | 0 e 3 (no CT-e OS o 3 é "aplicativo do Fisco" no schema; Q-9) | Não existe no GTV-e | 0 e 4 (PAA); o 4 entrou na NT 2025.001 |
| Contingência em `Mov_Dfe_Contingencia` | Offline: 168 h para transmitir; atraso maior só é aceito se emitido em offline (cStat 150) | Igual | Igual | Offline: 168 h (MOC, cap. 11); mesma chave e mesmo `cMDF`; o MOC recomenda pular um número |
| Série em `Cad_Serie_Documento_Fiscal` | Zero para série única | Igual | Igual | Faixa 920 a 969 reservada a pessoa física com inscrição estadual (F69 e F70, rej. 232 e 233) |
| Certificado e assinatura em `Cad_Dfe_Emitente_Configuracao` | Certificado do emitente; NFF e PAA: ver abaixo | Igual | Igual | Certificado do emitente; NFF e PAA: ver abaixo |
| Chave de acesso | 44 posições; CNPJ alfanumérico `[0-9]{6}[A-Z0-9]{12}[0-9]{26}` | Igual | Igual | Igual (NT 2025.001) |

**Nota Fiscal Fácil (`tpEmis` 3).** Quem assina e transmite é a SVRS com o e-CNPJ dela: no CT-e valem as regras A08, A09, A10 e E04 (rejeições 900, 906, 904 e 901) e no MDF-e as regras A08 e A09 (rejeições 900 e 904). O ERP do emitente não assina esses documentos e `Cad_Dfe_Emitente_Configuracao` não exige certificado para eles. Várias regras do MDF-e abrem exceção para `tpEmis` 3 (F81, F85 a F88, F91 a F93 e F110: duplicidade, não encerramento, seguro e situação do RNTRC), por isso `Tipo_Emissao` precisa distinguir o valor.

**Provedor de Assinatura e Autorização, PAA (`procEmi` 4).** O grupo `infPAA` identifica o provedor. O PAA atende pessoa física e MEI, que se vinculam ao provedor no portal DFe da SVRS pelo gov.br; o evento gerado por PAA obriga a SEFAZ a conferir a situação do CNPJ no cadastro MEI. O evento de prestação em desacordo (610110) pode ser assinado com o certificado da SVRS/PROCERGS quando o tomador está identificado pelo gov.br (regra E03, exceção 2). O ERP guarda o processo de emissão e o CNPJ do provedor, mas não implementa a assinatura do PAA.

**Contingência EPEC e FS-DA.** A NT 2026.004 elimina `tpEmis` 4 e 5 do CT-e, o evento 110113 e o 240160 (a NT escreve "24160"; a tabela 3.7.1 do MOC diz 240160). Eventos desses tipos passam a ser rejeitados com 629. A exceção é a SEFAZ de Minas Gerais, que mantém a redação das regras G103, G215 e G217 e a rejeição 928. O ERP não implementa EPEC nem FS-DA para o CT-e; o valor `epec` do domínio fica para a NF-e.

**Quatro modelos, três famílias de conteúdo.** CT-e, CT-e OS e GTV-e têm cabeçalho, tomador e valores parecidos e compartilham `Mov_Cte`; o MDF-e é um manifesto de carga sem valor fiscal e não é nota. A seção 7 mostra como cada um se liga ao modelo existente.

# 4. MDF-e: campos, eventos e regras de negócio

## 4.1 O que o MDF-e é para o ERP

O manifesto agrupa os documentos de uma viagem (CT-e, NF-e e outros MDF-e) e não tem valor fiscal próprio: não é escriturado, não gera título e não tem item. Por isso **o MDF-e não vira nota**: o conteúdo fica em `Mov_Mdfe` e filhas (proposta A.5 do documento 33, com os ajustes da seção 9), e o dado do documento (chave, protocolo, status, XML) fica em `Mov_Documento_Fiscal`. A ligação com o transporte próprio é `Mov_Expedicao_Saida` (existente), e quando há mais de um modal, `Mov_Expedicao_Trecho`. O tipo de emitente (`tpEmit`) distingue o prestador de serviço de transporte (1), o transportador de carga própria (2) e o prestador que emitirá CT-e globalizado (3); o schema manda preencher 2 para emitentes de NF-e que transportam carga própria. O tipo de transportador (`tpTransp`) é ETC (1), TAC (2) ou CTC (3).

O modal rodoviário concentra o que a Mlegate precisa agora: 72 linhas de RNTRC, vale-pedágio, contratante, pagamento do frete, veículos e condutores. Os modais aéreo, aquaviário e ferroviário somam 38 linhas e ficam só no XML até haver cliente (D-N68), cada um com esboço de entidade na planilha.

## 4.2 Cobertura por área

| Grupo | Área | Linhas | Cob. | Prop. | Der. | XML | Campo | Ent. | Destinos principais |
|---|---|---|---|---|---|---|---|---|---|
| MDF-e: documento | Identificação | 19 | 0 | 9 | 6 | 0 | 4 | 0 | `Mov_Documento_Fiscal`, `Mov_Mdfe`, `Cad_Serie_Documento_Fiscal` |
|  | Percurso e municípios | 5 | 0 | 5 | 0 | 0 | 0 | 0 | `Mov_Mdfe_Municipio`, `Mov_Mdfe_Percurso` |
|  | Emitente | 15 | 15 | 0 | 0 | 0 | 0 | 0 | `Cad_Filial`, `Cad_Participante_Endereco`, `Cad_Participante_Email` |
|  | Modal | 2 | 0 | 0 | 2 | 0 | 0 | 0 | `Mov_Mdfe`, `Cad_Dfe_Leiaute` |
|  | Documentos transportados | 12 | 0 | 2 | 0 | 0 | 10 | 0 | `Mov_Mdfe_Documento` |
|  | Unidades e lacres | 25 | 0 | 0 | 0 | 0 | 0 | 25 | `Mov_Dfe_Unidade_Transporte`, `Mov_Dfe_Lacre` |
|  | Produtos perigosos | 18 | 0 | 0 | 0 | 0 | 0 | 18 | `Mov_Dfe_Produto_Perigoso` |
|  | Seguro | 7 | 0 | 4 | 0 | 0 | 2 | 1 | `Mov_Mdfe_Seguro`, `Mov_Mdfe_Seguro_Averbacao` |
|  | Produto predominante | 10 | 0 | 0 | 0 | 0 | 10 | 0 | `Mov_Mdfe`, `Cad_Classificacao_Mercadoria` |
|  | Totais | 6 | 0 | 2 | 3 | 0 | 1 | 0 | `Mov_Mdfe`, `Mov_Mdfe_Documento`, `Cad_Unidade_Medida` |
|  | Demais grupos | 31 | 6 | 2 | 3 | 18 | 2 | 0 | `Mov_Documento_Fiscal`, `Cad_Dfe_Emitente_Configuracao`, `Mov_Nota_Fiscal_Saida_Autorizado_Xml` |
| MDF-e: modais | Rodoviário: ANTT | 5 | 0 | 1 | 0 | 0 | 1 | 3 | `Mov_Mdfe_Ciot`, `Mov_Mdfe` |
|  | Rodoviário: vale-pedágio | 7 | 0 | 2 | 0 | 0 | 5 | 0 | `Mov_Mdfe_Vale_Pedagio` |
|  | Rodoviário: contratante e pagamento | 26 | 0 | 6 | 0 | 0 | 8 | 12 | `Mov_Mdfe_Pagamento_Frete`, `Mov_Mdfe_Contratante`, `Mov_Mdfe_Pagamento_Componente` |
|  | Rodoviário: veículos | 33 | 4 | 25 | 0 | 0 | 4 | 0 | `Cad_Veiculo_Transporte`, `Cad_Participante`, `Cad_Participante_Inscricao` |
|  | Unidades e lacres | 1 | 0 | 0 | 0 | 0 | 0 | 1 | `Mov_Dfe_Lacre` |
|  | Outros modais (onda 2) | 38 | 0 | 0 | 0 | 38 | 0 | 0 | `Mov_Mdfe_Modal_Aquaviario`, `Mov_Mdfe_Vagao`, `Mov_Mdfe_Modal_Aereo` |
| MDF-e: eventos | Evento: envelope | 30 | 0 | 5 | 7 | 18 | 0 | 0 | `Mov_Dfe_Evento`, `Mov_Documento_Fiscal`, `Cad_Classe_Sistema` |
|  | Evento 110111: cancelamento | 3 | 0 | 1 | 2 | 0 | 0 | 0 | `Cad_Dfe_Evento_Tipo`, `Mov_Documento_Fiscal`, `Mov_Dfe_Evento` |
|  | Evento 110117: confirmação do serviço de transporte | 2 | 0 | 0 | 2 | 0 | 0 | 0 | `Cad_Dfe_Evento_Tipo`, `Mov_Documento_Fiscal` |
|  | Evento 110112: encerramento | 6 | 0 | 0 | 2 | 0 | 4 | 0 | `Mov_Mdfe`, `Cad_Dfe_Evento_Tipo`, `Mov_Documento_Fiscal` |
|  | Evento 110114: inclusão de condutor | 3 | 0 | 2 | 1 | 0 | 0 | 0 | `Mov_Mdfe_Condutor`, `Cad_Dfe_Evento_Tipo` |
|  | Evento 110115: inclusão de DF-e | 7 | 0 | 5 | 2 | 0 | 0 | 0 | `Mov_Mdfe_Municipio`, `Mov_Mdfe_Documento`, `Cad_Dfe_Evento_Tipo` |
|  | Eventos 110116 e 110118: pagamento da operação | 44 | 0 | 12 | 4 | 0 | 16 | 12 | `Mov_Mdfe_Pagamento_Frete`, `Mov_Mdfe_Pagamento_Componente`, `Mov_Mdfe_Pagamento_Parcela` |

Cob. = coberto; Prop. = proposta dos docs 33/34; Der. = derivado; XML = só no XML; Campo = campo novo; Ent. = entidade nova. Os significados estão na seção 8; as 355 linhas campo a campo estão na aba "MDF-e campos".

O bloco **Emitente** (15 linhas) está todo coberto por `Cad_Filial` e pelas tabelas de participante. **Unidades de transporte, lacres e produtos perigosos** somam 44 linhas e viram três entidades genéricas que o CT-e também usa (`Mov_Dfe_Unidade_Transporte`, `Mov_Dfe_Lacre` e `Mov_Dfe_Produto_Perigoso`). O **pagamento do frete** é a maior lacuna: 70 linhas entre o MDF-e e os eventos 110116 e 110118, que viram contratante, CIOT, componentes e parcelas (parcela com ligação opcional ao título a pagar).

## 4.3 Eventos do MDF-e

Os sete eventos do schema foram conferidos, um a um, contra o MOC (capítulo 6 e tabela 3.7.1). Os eventos do Fisco e de terceiros que a tabela lista sem schema (310620, 510620, 310112, 240170 e a família 900120 a 900137 do FAT-e) o ERP só recebe, quando chegam na consulta de situação; ficam como linha do domínio `tipo_evento_dfe`, sem tela. As regras que dependem do estado do manifesto (já cancelado, já encerrado, circulação registrada, carregamento posterior) o ERP verifica antes de enviar, com a rejeição da SEFAZ como confirmação.

| Código | Evento | Quem registra | Situação | Proposta |
|---|---|---|---|---|
| 110111 | Cancelamento | Emitente | Proposta dos docs 33/34 | Mov_Dfe_Evento (Justificativa, Protocolo_Evento); `Mov_Documento_Fiscal.Status` passa a cancelado. Prazo em `MDFE-CANCELAMENTO-PRAZO` |
| 110112 | Encerramento | Emitente (ou terceiro, com `indEncPorTerceiro`) | Campo novo | Mov_Mdfe.Data_Encerramento, ID_Estado_Encerramento, ID_Municipio_Encerramento e Indicador_Encerrado_Por_Terceiro |
| 110114 | Inclusão de condutor | Emitente | Proposta dos docs 33/34 | Mov_Mdfe_Condutor com ID_Dfe_Evento (campo novo) |
| 110115 | Inclusão de DF-e | Emitente | Proposta dos docs 33/34 | Mov_Mdfe_Municipio e Mov_Mdfe_Documento com ID_Dfe_Evento |
| 110116 | Pagamento da operação de transporte | Emitente que contratou o TAC | Entidade nova | Mov_Mdfe_Pagamento_Frete (ID_Dfe_Evento_Origem), Mov_Mdfe_Pagamento_Componente e Mov_Mdfe_Pagamento_Parcela |
| 110117 | Confirmação do serviço de transporte | Contratante (autor 4) | Derivado | Mov_Dfe_Evento com Papel_Autor contratante e ID_Participante_Autor; só é emitido pelo ERP quando a Mlegate é contratante |
| 110118 | Alteração no pagamento do serviço de transporte | Emitente | Entidade nova | Mesmas entidades do 110116; o evento anterior fica preservado (histórico por evento) |
| 310620 | Registro de passagem | Fisco | Só no XML | Evento recebido na consulta; vira linha de domínio `tipo_evento_dfe`, sem tela |
| 510620 | Registro de passagem automático | Outros (ONE) | Só no XML | Idem. O pacote da pasta bt traz o 510630 com outro nome (Q-13) |
| 310112 | Encerramento do Fisco | Fisco (SVRS) | Só no XML | Recebido; atualiza o encerramento do MDF-e (Data_Encerramento) com marca de origem Fisco |
| 240170 | Liberação do prazo de cancelamento | Fisco do emitente (via WS ou Extranet) | Só no XML | Recebido; libera cancelamento fora do prazo em `MDFE-CANCELAMENTO-PRAZO` |
| 900120 a 900137 (900120, 900121, 900134, 900135, 900136, 900137) | FAT-e: cessão de ônus de gravame, pagamento total e baixa de ativo financeiro em garantia, e os cancelamentos | SVBA (autor 9) | Só no XML | Fora do escopo; ficam como linhas de domínio se um dia chegarem pela consulta |

As regras conferidas de cada evento, com os códigos de rejeição, estão na aba "Eventos".

## 4.4 Regras de negócio e prazos

Tudo o que depende de prazo, limite, faixa ou formato vira parâmetro com vigência em `Cad_Dfe_Parametro_Regra` (seção 9), com o código da rejeição como referência. Os valores abaixo foram copiados do MOC 3.00b de agosto de 2022; como o MOC é anterior às NTs de 2024 e 2025, cada prazo precisa ser conferido antes de ativar (Q-18).

| Código da regra | Regra | Valor | Unidade | Rejeição ou fonte | Observação |
|---|---|---|---|---|---|
| MDFE-CANCELAMENTO-PRAZO | Prazo para cancelar o MDF-e depois da autorização | 24 | horas | K04, rej. 220 | Exceção: carregamento posterior sem evento de inclusão de DF-e. O Fisco libera o prazo pelo evento 240170 |
| MDFE-EMISSAO-ATRASO | Atraso máximo da data de emissão em relação à recepção (emissão normal) | 24 | horas | F80, rej. 228 | Só para `tpEmis` 1 |
| MDFE-EMISSAO-FUTURA-TOLERANCIA | Tolerância quando a data de emissão é maior que a de recebimento | 5 | minutos | F79, rej. 212 | Hora local do emissor |
| MDFE-CONTINGENCIA-PRAZO | Prazo para transmitir o MDF-e emitido em contingência offline | 168 | horas | MOC, cap. 11 | Mantém a mesma chave e o mesmo `cMDF` |
| MDFE-CARREGA-POSTERIOR-PRAZO | Prazo para o evento de inclusão de DF-e num MDF-e com carregamento posterior; vencido, o emitente é bloqueado | 168 | horas | F25, rej. 712 | Bloqueia nova emissão do mesmo emitente |
| MDFE-NAO-ENCERRADO-EMITENTE | MDF-e não encerrado há mais de N dias bloqueia o emitente | 30 | dias | F86, rej. 686 | Não vale para `tpEmis` 3 |
| MDFE-NAO-ENCERRADO-PLACA | MDF-e não encerrado há mais de N dias para a placa, com no máximo 2 UF de percurso | 5 | dias | F87, rej. 462 | Modal rodoviário; não vale para `tpEmis` 3 |
| MDFE-USO-INDEVIDO-COTA | Rejeições de bloqueio (462, 610, 611 e 686) permitidas por hora antes da punição | 5 | rejeições por hora | MOC, item 8.3 | Da sexta rejeição em diante, a SEFAZ suprime a chave e o protocolo no retorno |
| MDFE-USO-INDEVIDO-PUNICAO | Duração da punição por uso indevido | 1 | hora | MOC, item 8.3 | Contada a partir da sexta rejeição |
| MDFE-CONSULTA-JANELA | Janela da consulta de situação, contada da emissão | 180 | dias | MOC, item 4.3.3 |  |
| MDFE-CHAVE-ANTIGA | Consulta a chave com mais de N meses de atraso | 6 | meses | G02, rej. 460 |  |
| MDFE-TOLERANCIA-SOMA | Tolerância na soma dos componentes e das parcelas do pagamento | 0,01 | R$ | K11 e K15, rej. 746 e 738; F52 a F66 | Para mais ou para menos |
| MDFE-EVENTO-SEQUENCIA-MAXIMA | Número sequencial máximo do evento, por tipo | 1 ou 1 a 99, conforme o evento | ocorrências | K01, rej. 636; GP12 | Cancelamento, encerramento e pagamento da operação: 1. Inclusão de condutor, inclusão de DF-e, confirmação do serviço e alteração do pagamento: até 99 |
| MDFE-SERIE-PESSOA-FISICA | Faixa de série reservada a pessoa física com inscrição estadual | 920 a 969 | série | F69 e F70, rej. 232 e 233 |  |
| MDFE-PLACA-PADRAO | Padrão da placa do veículo | [A-Z]{3}[0-9][0-9A-Z][0-9]{2} | expressão regular | F89, rej. 646 | Cobre a placa antiga e a Mercosul |
| MDFE-QRCODE-VIGENCIA | Data em que o QR Code passa a ser exigido | a combinar entre Fisco e empresas | data | MOC, cap. 9 | Sem data nas fontes; não grava valor inventado |

Outras regras do MOC que o ERP valida antes de enviar, sem parâmetro numérico:

- **Carregamento posterior** (`indCarregaPosterior` 1): um município de carregamento e um de descarregamento, iguais (F21, rej. 703); mesma UF e diferente de EX (F22, 704); só modal rodoviário (F23, 705); só tipo de emitente 2, transporte próprio (F24, 707); sem documentos no ato da emissão (F27, 706); cancelamento vedado depois de incluir DF-e em outro município (K08, 710); encerramento exige inclusão de DF-e (K10, 715).
- **Seguro da carga**: obrigatório no modal rodoviário quando `tpEmit` é 1 ou 3 (F91, rej. 698), com seguradora, apólice e averbação completas (F92, 699) e responsável informado quando for o contratante (F93, 542). A emissão pela Nota Fiscal Fácil dispensa o grupo, a averbação e o responsável.
- **RNTRC**: situação válida (F110, rej. 682), associado ao transportador pelo CNPJ-base (F111, 687) e vinculado à placa de tração (F112, 683). As três são facultativas na tabela do MOC.
- **Placa**: formato `[A-Z]{3}[0-9][0-9A-Z][0-9]{2}` quando as UFs de carregamento e descarregamento diferem (F89, rej. 646).
- **Série**: faixa 920 a 969 reservada a pessoa física com inscrição estadual (F69 e F70, rej. 232 e 233).
- **Tomadores**: o grupo de informações dos tomadores é obrigatório para o prestador de serviço de transporte no modal rodoviário (F94, rej. 578).
- **Soma dos componentes e das parcelas** do pagamento igual ao valor do contrato, com tolerância de R$ 0,01 (K11 e K15, rej. 746 e 738).
- **Nota Fiscal Fácil** (`tpEmis` 3): exceção às regras F81, F85 a F88, F91 a F93 e F110.
- **QR Code**: obrigatório só depois de data a combinar entre Fisco e empresas; a URL é a do portal da SVRS com `chMDFe` e `tpAmb`, mais `sign` na contingência.

# 5. Histórico das três NTs do schema 3.00b

Medi o histórico comparando os três pacotes de schemas entre si (campo, tipo, ocorrência, tamanho, valores e descrição) e os tipos básicos. Deu **52 diferenças de leiaute e 7 de tipos**, todas na aba "Histórico de versões MDF-e". Não há pacote anterior à NT 2024.001 e os textos das NTs não foram enviados, então a NT 2024.001 só pode ser descrita contra o Anexo I do MOC de 2022, e o porquê de cada mudança é inferido do próprio schema (F-3).

| NT | Tamanho da mudança | O que mudou | Impacto no dicionário |
|---|---|---|---|
| NT 2024.001 | Linha de base (pacote anterior não enviado) | Comparado com o Anexo I de 2022, o único campo que o pacote traz a mais é `indEncPorTerceiro` no evento de encerramento (comparação por nome de tag). O motivo de a NT existir não pode ser lido dos schemas | Mov_Mdfe.Indicador_Encerrado_Por_Terceiro |
| NT 2024.002 | 2 campos novos e 1 ampliação (5 diferenças) | Prestação parcial: `indPrestacaoParcial` e o grupo `infNFePrestParcial` (com `chNFe`) no CT-e de cada município de descarregamento. `xSolic` do grupo `infSolicNFF` passa de 2.000 para 8.000 posições, no MDF-e e no evento | Mov_Mdfe_Documento.Indicador_Prestacao_Parcial e linha filha com ID_Mdfe_Documento_Pai |
| NT 2025.001 | 47 diferenças de leiaute e 7 de tipos | CNPJ alfanumérico em todos os campos de CNPJ, nas três chaves, no Id do evento e no QR Code, e remoção de `TCnpjVar`; `TStat` passa a 3 ou 4 dígitos; `procEmi` ganha 4 (PAA); `tpCarga` ganha 12; produto predominante cita a Resolução ANTT 5.867/2020; MMSI no aquaviário; CIOT passa a opcional; `nCompra` vira IDVPO; `tpValePed` fica com 01 e 04; CNPJ do contratante deixa de aceitar valor vazio; pagamento do frete vira pagamento do contrato; `tpComp` ganha 04 (Frete), no MDF-e e nos eventos 110116 e 110118 | Modelo de CNPJ alfanumérico (documento 34); Processo_Emissao; Tipo_Carga; Mov_Mdfe_Vale_Pedagio; Mov_Mdfe_Pagamento_Componente |
| MOC 3.00b (agosto de 2022) | Anterior às três NTs | SOAP Header opcional (homologação em 04/2023 e produção em 06/2023), `nSeqEvento` ampliado a 3 posições e desuso das rejeições 226 e 249 | Sem campo; só configuração do serviço em Cad_Autoridade_Fiscal_Servico |

O ponto de maior consequência é o CNPJ alfanumérico: a chave de 44 posições passa a ser `[0-9]{6}[A-Z0-9]{12}[0-9]{26}` e o CNPJ `[A-Z0-9]{12}[0-9]{2}`, o que obriga a chave de acesso, o CNPJ do participante e da filial e o identificador do evento a aceitar letras (o documento 34 já registra a regra do dígito verificador). A ampliação de `TStat` para 3 ou 4 dígitos importa porque o CT-e da NT 2026.004 já usa códigos de quatro dígitos (1051 a 1071): `Cad_Dfe_Codigo_Retorno.Codigo` precisa caber quatro posições.

# 6. CT-e: eventos, regras de negócio e a NT 2026.004 de IBS e CBS

## 6.1 Os quatro leiautes do CT-e

O pacote 4.00 traz quatro raízes: `CTe` (modelo 57, 401 linhas), `CTeSimp` (CT-e Simplificado, também modelo 57 e `tpCTe` 5 e 6, 271), `CTeOS` (modelo 67, 233) e `GTVe` (modelo 64, 151), mais os sete leiautes de modal e 14 eventos. O cabeçalho, o tomador, o ICMS, o IBS/CBS, a cobrança e as referências são quase iguais nas quatro raízes e saem na mesma classificação; o que muda é o miolo de cada serviço (carga e documentos transportados no 57, pessoas e valores no 67 e 64). O CT-e OS, a GTV-e e os modais não rodoviários ficam na onda 2 (D-N68).

| Grupo | Área | Linhas | Cob. | Prop. | Der. | XML | Campo | Ent. | Destinos principais |
|---|---|---|---|---|---|---|---|---|---|
| CT-e 57 | Identificação | 31 | 7 | 5 | 13 | 0 | 6 | 0 | `Mov_Documento_Fiscal`, `Mov_Cte`, `Cad_Municipio` |
|  | Tomador | 20 | 18 | 0 | 0 | 0 | 2 | 0 | `Cad_Participante_Endereco`, `Mov_Cte`, `Cad_Participante_Inscricao` |
|  | Compra governamental e pagamento antecipado | 6 | 0 | 5 | 0 | 0 | 1 | 0 | `Mov_Nota_Fiscal_Saida_Compra_Governamental`, `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Cte` |
|  | Complemento | 26 | 0 | 1 | 0 | 0 | 0 | 25 | `Mov_Cte_Complemento`, `Mov_Dfe_Observacao`, `Mov_Cte_Passagem` |
|  | Emitente | 17 | 17 | 0 | 0 | 0 | 0 | 0 | `Cad_Filial`, `Cad_Participante_Endereco`, `Cad_Participante_Inscricao` |
|  | Remetente, expedidor, recebedor, destinatário e tomador | 66 | 66 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Endereco`, `Cad_Participante`, `Cad_Participante_Inscricao` |
|  | Valores da prestação | 5 | 1 | 4 | 0 | 0 | 0 | 0 | `Mov_Cte_Componente_Valor`, `Mov_Nota_Fiscal_Saida`, `Mov_Nota_Fiscal_Saida_Item` |
|  | ICMS | 48 | 38 | 4 | 2 | 0 | 4 | 0 | `Mov_Apuracao_Tributo_Item`, `Cad_Cst`, `Mov_Apuracao_Tributo_Item_Complemento` |
|  | IBS e CBS | 47 | 10 | 37 | 0 | 0 | 0 | 0 | `Mov_Apuracao_Tributo_Item_Complemento`, `Mov_Apuracao_Tributo_Item`, `Mov_Nota_Fiscal_Saida_Item` |
|  | Totais | 1 | 0 | 0 | 1 | 0 | 0 | 0 | sem destino (fica no XML) |
|  | Vínculo com o pagamento | 5 | 0 | 5 | 0 | 0 | 0 | 0 | `Mov_Dfe_Vinculo_Pagamento` |
|  | Carga | 7 | 0 | 5 | 0 | 0 | 2 | 0 | `Mov_Cte`, `Mov_Cte_Carga_Quantidade` |
|  | Documentos transportados | 26 | 0 | 2 | 0 | 0 | 24 | 0 | `Mov_Cte_Documento_Transportado` |
|  | Unidades e lacres | 36 | 0 | 0 | 0 | 0 | 0 | 36 | `Mov_Dfe_Unidade_Transporte`, `Mov_Dfe_Lacre` |
|  | Documentos anteriores | 11 | 0 | 0 | 0 | 0 | 0 | 11 | `Mov_Cte_Documento_Anterior` |
|  | Modal | 2 | 0 | 0 | 2 | 0 | 0 | 0 | `Mov_Cte`, `Cad_Dfe_Leiaute` |
|  | Veículos novos (onda 2) | 6 | 0 | 0 | 0 | 6 | 0 | 0 | `Mov_Cte_Veiculo_Novo` |
|  | Cobrança | 7 | 7 | 0 | 0 | 0 | 0 | 0 | `Mov_Titulo` |
|  | Referências | 5 | 0 | 3 | 0 | 0 | 2 | 0 | `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Cte`, `Mov_Cte_Complemento` |
|  | Demais grupos | 29 | 6 | 2 | 3 | 18 | 0 | 0 | `Mov_Documento_Fiscal`, `Cad_Dfe_Emitente_Configuracao`, `Mov_Nota_Fiscal_Saida_Autorizado_Xml` |
| CT-e OS 67 | Identificação | 28 | 7 | 5 | 13 | 0 | 3 | 0 | `Mov_Documento_Fiscal`, `Mov_Cte`, `Cad_Municipio` |
|  | Tomador | 1 | 1 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Inscricao` |
|  | CT-e OS (onda 2) | 17 | 0 | 0 | 0 | 17 | 0 | 0 | `Mov_Cte_Os`, `Mov_Cte_Os_Documento_Referenciado`, `Mov_Cte_Os_Gtve` |
|  | Compra governamental e pagamento antecipado | 6 | 0 | 5 | 0 | 0 | 1 | 0 | `Mov_Nota_Fiscal_Saida_Compra_Governamental`, `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Cte` |
|  | Complemento | 8 | 0 | 1 | 0 | 0 | 0 | 7 | `Mov_Dfe_Observacao`, `Mov_Cte_Complemento`, `Mov_Nota_Fiscal_Saida` |
|  | Emitente | 16 | 16 | 0 | 0 | 0 | 0 | 0 | `Cad_Filial`, `Cad_Participante_Endereco`, `Cad_Participante_Inscricao` |
|  | Remetente, expedidor, recebedor, destinatário e tomador | 17 | 17 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Endereco`, `Cad_Participante`, `Cad_Participante_Inscricao` |
|  | Valores da prestação | 5 | 1 | 4 | 0 | 0 | 0 | 0 | `Mov_Cte_Componente_Valor`, `Mov_Nota_Fiscal_Saida`, `Mov_Nota_Fiscal_Saida_Item` |
|  | ICMS | 41 | 32 | 3 | 2 | 0 | 4 | 0 | `Mov_Apuracao_Tributo_Item`, `Cad_Cst`, `Mov_Apuracao_Tributo_Item_Complemento` |
|  | Tributos federais (CT-e OS, onda 2) | 5 | 5 | 0 | 0 | 0 | 0 | 0 | `Mov_Apuracao_Tributo_Item`, `Mov_Titulo_Retencao` |
|  | IBS e CBS | 47 | 10 | 37 | 0 | 0 | 0 | 0 | `Mov_Apuracao_Tributo_Item_Complemento`, `Mov_Apuracao_Tributo_Item`, `Mov_Nota_Fiscal_Saida_Item` |
|  | Totais | 1 | 0 | 0 | 1 | 0 | 0 | 0 | sem destino (fica no XML) |
|  | Vínculo com o pagamento | 5 | 0 | 5 | 0 | 0 | 0 | 0 | `Mov_Dfe_Vinculo_Pagamento` |
|  | Modal | 2 | 0 | 0 | 2 | 0 | 0 | 0 | `Mov_Cte`, `Cad_Dfe_Leiaute` |
|  | Referências | 2 | 0 | 2 | 0 | 0 | 0 | 0 | `Mov_Nota_Fiscal_Saida_Referenciada` |
|  | Cobrança | 7 | 7 | 0 | 0 | 0 | 0 | 0 | `Mov_Titulo` |
|  | Demais grupos | 25 | 6 | 2 | 4 | 13 | 0 | 0 | `Mov_Documento_Fiscal`, `Cad_Dfe_Emitente_Configuracao`, `Mov_Nota_Fiscal_Saida_Autorizado_Xml` |
| CT-e Simplificado | Identificação | 26 | 7 | 3 | 11 | 0 | 5 | 0 | `Mov_Documento_Fiscal`, `Mov_Nota_Fiscal_Saida`, `Mov_Cte` |
|  | Compra governamental e pagamento antecipado | 6 | 0 | 5 | 0 | 0 | 1 | 0 | `Mov_Nota_Fiscal_Saida_Compra_Governamental`, `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Cte` |
|  | Complemento | 11 | 0 | 1 | 0 | 0 | 0 | 10 | `Mov_Cte_Complemento`, `Mov_Dfe_Observacao`, `Mov_Cte_Passagem` |
|  | Emitente | 17 | 17 | 0 | 0 | 0 | 0 | 0 | `Cad_Filial`, `Cad_Participante_Endereco`, `Cad_Participante_Inscricao` |
|  | Tomador | 2 | 1 | 0 | 0 | 0 | 1 | 0 | `Mov_Cte`, `Cad_Participante_Inscricao` |
|  | Remetente, expedidor, recebedor, destinatário e tomador | 17 | 17 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Endereco`, `Cad_Participante`, `Cad_Participante_Inscricao` |
|  | Carga | 7 | 0 | 5 | 0 | 0 | 2 | 0 | `Mov_Cte`, `Mov_Cte_Carga_Quantidade` |
|  | CT-e Simplificado (onda 2) | 13 | 2 | 4 | 0 | 7 | 0 | 0 | `Mov_Cte_Item`, `Mov_Nota_Fiscal_Saida_Item`, `Mov_Cte_Item_Documento_Anterior` |
|  | IBS e CBS | 47 | 10 | 37 | 0 | 0 | 0 | 0 | `Mov_Apuracao_Tributo_Item_Complemento`, `Mov_Apuracao_Tributo_Item`, `Mov_Nota_Fiscal_Saida_Item` |
|  | Documentos transportados | 3 | 0 | 1 | 0 | 0 | 2 | 0 | `Mov_Cte_Documento_Transportado` |
|  | Unidades e lacres | 12 | 0 | 0 | 0 | 0 | 0 | 12 | `Mov_Dfe_Unidade_Transporte`, `Mov_Dfe_Lacre` |
|  | Modal | 2 | 0 | 0 | 2 | 0 | 0 | 0 | `Mov_Cte`, `Cad_Dfe_Leiaute` |
|  | Cobrança | 7 | 7 | 0 | 0 | 0 | 0 | 0 | `Mov_Titulo` |
|  | Referências | 2 | 0 | 1 | 0 | 0 | 1 | 0 | `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Cte` |
|  | ICMS | 48 | 38 | 4 | 2 | 0 | 4 | 0 | `Mov_Apuracao_Tributo_Item`, `Cad_Cst`, `Mov_Apuracao_Tributo_Item_Complemento` |
|  | Vínculo com o pagamento | 5 | 0 | 5 | 0 | 0 | 0 | 0 | `Mov_Dfe_Vinculo_Pagamento` |
|  | Totais | 17 | 0 | 0 | 17 | 0 | 0 | 0 | sem destino (fica no XML) |
|  | Demais grupos | 29 | 6 | 2 | 3 | 18 | 0 | 0 | `Mov_Documento_Fiscal`, `Cad_Dfe_Emitente_Configuracao`, `Mov_Nota_Fiscal_Saida_Autorizado_Xml` |
| GTV-e 64 | Identificação | 21 | 7 | 3 | 9 | 0 | 2 | 0 | `Mov_Documento_Fiscal`, `Mov_Nota_Fiscal_Saida`, `Mov_Cte` |
|  | Tomador | 1 | 1 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Inscricao` |
|  | GTV-e (onda 2) | 47 | 0 | 0 | 0 | 47 | 0 | 0 | `Mov_Gtve`, `Mov_Gtve_Especie` |
|  | Complemento | 8 | 0 | 1 | 0 | 0 | 0 | 7 | `Mov_Dfe_Observacao`, `Mov_Cte_Complemento`, `Mov_Nota_Fiscal_Saida` |
|  | Emitente | 15 | 15 | 0 | 0 | 0 | 0 | 0 | `Cad_Filial`, `Cad_Participante_Endereco`, `Cad_Participante_Inscricao` |
|  | Remetente, expedidor, recebedor, destinatário e tomador | 34 | 34 | 0 | 0 | 0 | 0 | 0 | `Cad_Participante_Endereco`, `Cad_Participante`, `Cad_Participante_Inscricao` |
|  | Demais grupos | 25 | 6 | 2 | 4 | 13 | 0 | 0 | `Mov_Documento_Fiscal`, `Cad_Dfe_Emitente_Configuracao`, `Mov_Nota_Fiscal_Saida_Autorizado_Xml` |
| CT-e: modais | Modal rodoviário | 9 | 0 | 1 | 0 | 0 | 0 | 8 | `Mov_Cte_Ordem_Coleta`, `Mov_Cte` |
|  | Outros modais (onda 2) | 74 | 0 | 0 | 0 | 74 | 0 | 0 | `Mov_Cte_Modal_Aereo` |
| CT-e: eventos | Evento: envelope | 16 | 0 | 5 | 6 | 5 | 0 | 0 | `Mov_Dfe_Evento`, `Mov_Documento_Fiscal`, `Cad_Classe_Sistema` |
|  | Demais grupos | 14 | 0 | 0 | 1 | 13 | 0 | 0 | `Mov_Documento_Fiscal` |
|  | Evento: descrição | 14 | 0 | 0 | 14 | 0 | 0 | 0 | `Cad_Dfe_Evento_Tipo` |
|  | Evento 211110: apropriação de crédito presumido | 7 | 0 | 0 | 0 | 0 | 7 | 0 | `Mov_Credito_Fiscal`, `Mov_Dfe_Evento_Item`, `Cad_Credito_Presumido_Ibs_Cbs` |
|  | Evento 110110: carta de correção | 5 | 0 | 0 | 1 | 0 | 4 | 0 | `Mov_Dfe_Evento_Item`, `Cad_Dfe_Evento_Tipo` |
|  | Evento: protocolo | 7 | 0 | 0 | 7 | 0 | 0 | 0 | `Mov_Documento_Fiscal` |
|  | Eventos 110180 e 110181: comprovante de entrega | 8 | 0 | 0 | 0 | 0 | 1 | 7 | `Mov_Cte_Entrega`, `Mov_Dfe_Evento_Item` |
|  | Eventos de cancelamento de evento | 4 | 0 | 0 | 0 | 0 | 4 | 0 | `Mov_Dfe_Evento` |
|  | Evento 110111: cancelamento | 1 | 0 | 1 | 0 | 0 | 0 | 0 | `Mov_Dfe_Evento` |
|  | Evento 110113: EPEC (eliminado) | 15 | 0 | 0 | 0 | 15 | 0 | 0 | sem destino (fica no XML) |
|  | Evento 110170: informações da GTV (onda 2) | 22 | 0 | 0 | 0 | 22 | 0 | 0 | `Mov_Gtve` |
|  | Eventos 110190 e 110191: insucesso de entrega | 9 | 0 | 0 | 0 | 0 | 1 | 8 | `Mov_Cte_Entrega`, `Mov_Dfe_Evento_Item` |
|  | Evento 610110: prestação em desacordo | 2 | 0 | 1 | 1 | 0 | 0 | 0 | `Cad_Dfe_Evento_Tipo`, `Mov_Dfe_Evento` |
|  | Evento 110160: registro multimodal (onda 2) | 2 | 0 | 0 | 0 | 2 | 0 | 0 | sem destino (fica no XML) |
|  | Eventos 110300 e 110301: vínculo de pagamento | 5 | 0 | 5 | 0 | 0 | 0 | 0 | `Mov_Dfe_Vinculo_Pagamento` |

## 6.2 Eventos do CT-e

Os 14 eventos do schema 4.00 foram conferidos contra a tabela 3.7.1 e o capítulo 6 do MOC. O MOC de 2022 não lista 110190, 110191, 110300, 110301 e 211110; os códigos vêm do cabeçalho de cada schema. Entre os eventos do Fisco que o ERP só recebe, os de **marcação** (310610 e 310611) são gerados na autorização do MDF-e e travam o cancelamento do CT-e enquanto houver MDF-e autorizado (rej. 528): o ERP precisa conhecer o vínculo antes de oferecer o cancelamento.

| Modelo | Código | Evento | Quem registra | Situação | Proposta |
|---|---|---|---|---|---|
| CT-e | 110110 | Carta de correção | Emitente | Campo novo | Mov_Dfe_Evento_Item (Grupo_Alterado, Campo_Alterado, Valor_Alterado e Numero_Item_Alterado); condição de uso fixa no catálogo do evento |
| CT-e | 110111 | Cancelamento | Emitente | Proposta dos docs 33/34 | Mov_Dfe_Evento. Prazos em `CTE-CANCELAMENTO-PRAZO` e `GTVE-CANCELAMENTO-PRAZO`. As vedações exigem consultar Mov_Mdfe_Documento e os eventos do próprio CT-e antes de enviar |
| CT-e | 110113 | EPEC (emissão prévia em contingência) | Emitente | Só no XML | Não entra no dicionário |
| CT-e | 110160 | Registros do multimodal | Emitente | Só no XML | Fica no XML até haver cliente (D-N68) |
| CT-e OS | 110170 | Informações da GTV | Emitente | Só no XML | Fica no XML até haver cliente (D-N68) |
| CT-e | 110180 | Comprovante de entrega | Emitente | Entidade nova | Mov_Cte_Entrega (Tipo_Entrega comprovante) e Mov_Dfe_Evento_Item.Chave_Documento |
| CT-e | 110181 | Cancelamento do comprovante de entrega | Emitente | Campo novo | Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado (autorreferência, campo novo) |
| CT-e | 110190 | Insucesso na entrega | Emitente | Entidade nova | Mov_Cte_Entrega (Tipo_Entrega insucesso, motivo em domínio novo) |
| CT-e | 110191 | Cancelamento do insucesso de entrega | Emitente | Campo novo | Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado |
| CT-e | 110300 | Vinculação do pagamento ao DF-e | Emitente | Proposta dos docs 33/34 | Mov_Dfe_Vinculo_Pagamento |
| CT-e | 110301 | Cancelamento da vinculação do pagamento | Emitente | Campo novo | Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado |
| CT-e | 610110 | Prestação do serviço em desacordo | Tomador (autor 6) | Proposta dos docs 33/34 | Mov_Dfe_Evento (Justificativa, Papel_Autor tomador). Prazo em `CTE-DESACORDO-PRAZO` |
| CT-e | 610111 | Cancelamento da prestação em desacordo | Tomador | Campo novo | Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado |
| CT-e | 211110 | Apropriação de crédito presumido | Tomador do serviço prestado por TAC (NFF ou PAA) ou por MEI | Campo novo | Cad_Credito_Presumido_Ibs_Cbs; Mov_Dfe_Evento.Texto_Declaracao; crédito em Mov_Credito_Fiscal e Mov_Dfe_Evento_Item (D-N71) |
| CT-e | 310610 e 310611 | MDF-e autorizado e MDF-e cancelado (marcação no CT-e) | Fisco (Ambiente Nacional do CT-e) | Só no XML | Recebido na consulta; atualiza o vínculo CT-e e MDF-e que o ERP já tem em Mov_Mdfe_Documento |
| CT-e | 310620 e 510620 | Registro de passagem e registro de passagem automático | Fisco | Só no XML | Recebido; sem tela |
| CT-e | 240130, 240131, 240140 | Fisco do emitente: CT-e complementar autorizado e cancelado; CT-e de substituição | Fisco do emitente | Só no XML | Recebidos; reforçam a referência já guardada em Mov_Nota_Fiscal_Saida_Referenciada |
| CT-e | 240160 | Liberação de EPEC | Fisco do emitente | Só no XML | Não entra |
| CT-e | 240170 | Liberação do prazo de cancelamento | Fisco do emitente | Só no XML | Recebido; libera o cancelamento fora do prazo |
| CT-e | 240180 e 240181 | CT-e OS autorizado e cancelado | Fisco do emitente | Só no XML | Recebido; sem tela |
| CT-e | 440130, 440140, 440150, 440160 | Autorizado redespacho, redespacho intermediário, subcontratação e serviço vinculado a multimodal | Fisco da chave relacionada | Só no XML | Recebidos quando outro transportador cita a chave do CT-e da Mlegate; ficam em Mov_Dfe_Evento |
| NF-e | 610190 e 610191 | Insucesso na entrega e cancelamento (registrados sobre a NF-e) | Ambiente Nacional | Só no XML | Continuam adiados (Q-13) |
| NF-e | 510630 | Registro de passagem automático originado no MDF-e | Ambiente Nacional | Só no XML | Continua adiado (Q-13) |

## 6.3 Regras de negócio e prazos do CT-e

| Código da regra | Modelo | Regra | Valor | Rejeição ou fonte |
|---|---|---|---|---|
| CTE-CANCELAMENTO-PRAZO | 57 e 67 | Prazo para cancelar o CT-e | 168 | Evento 110111, rej. 220 |
| GTVE-CANCELAMENTO-PRAZO | 64 | Prazo para cancelar a GTV-e | 45 | Evento 110111, rej. 876 |
| CTE-DESACORDO-PRAZO | 57 | Prazo para o tomador registrar prestação em desacordo (610110) | 45 | Rej. 787 |
| CTE-EMISSAO-ATRASO | 57, 67 e 64 | Atraso máximo da emissão em relação à recepção (G103 e H077) | 168 | G103, H077, rej. 228 |
| CTE-CONSULTA-JANELA | 57 | Janela da consulta de situação | 180 | MOC do CT-e |
| CTE-EVENTO-SEQUENCIA-MAXIMA | 57 e 67 | Número sequencial máximo do evento, por tipo | 1 ou 1 a 20, conforme o evento | O01 de cada evento, rej. 636 |
| CTE-CFOP-ACEITOS | 57 | Lista de CFOP que o CT-e aceita (capítulo 12 do MOC) | 5.351 a 5.360; 5.601 a 5.606; 5.932; 5.949; 6.351 a 6.360; 6.603; 6.932; 6.949; 7.358; 7.949 | MOC do CT-e, cap. 12 |
| CTE-CREDITO-PRESUMIDO-SEQUENCIA | 57 | Número sequencial máximo do evento 211110 | 1 | Regra 01 do evento, rej. 636 |
| CTE-TOLERANCIA-CREDITO-PRESUMIDO | 57 | Tolerância no cálculo do crédito presumido (base vezes percentual) | 0,01 | Regras 10 e 13, rej. 1066 e 1069 |
| CTE-IBS-UF-ALIQUOTA | 57, 67 e 64 | Alíquota do IBS da UF | 0,1% em 2026; 0,05% em 2027 e 2028; depois a de referência ou a específica da UF | Regra 316 (art. 343 e 344 da LC 214/25) |
| CTE-IBS-MUN-ALIQUOTA | 57, 67 e 64 | Alíquota do IBS do Município | 0% em 2026; 0,05% em 2027 e 2028; depois a de referência ou a específica do Município | Regra 321 (art. 343 e 344 da LC 214/25) |
| CTE-CBS-ALIQUOTA | 57, 67 e 64 | Alíquota da CBS | 0,90% em 2026; 2027 a publicar | Regra 326 (art. 346 da LC 214/25) |
| CTE-CBS-ZERO-ZFM | 57, 67 e 64 | Municípios da Zona Franca de Manaus em que a CBS pode ser zero | 1302603 Manaus; 1303569 Rio Preto da Eva; 1301902 Itacoatiara | Regra 326, exceção 2 |
| CTE-CBS-ZERO-ALC | 57, 67 e 64 | Pares de municípios das cinco Áreas de Livre Comércio em que a CBS pode ser zero | 1: Tabatinga. 2: Guajará-Mirim. 3: Boa Vista e Bonfim. 4: Macapá e Santana. 5: Brasileia, Epitaciolândia e Cruzeiro do Sul | Regra 326, exceção 2 |
| CTE-VTOTDFE-FORMULA | 57, 67 e 64 | Fórmula do total do documento (vTotDFe) | 2026: vTPrest. A partir de 2027: vTPrest + vIBS + vCBS | Regra 365 |
| CTE-TOTAL-LIQUIDO | 57, 67 e 64 | Total líquido da prestação confere com a soma dos itens | igualdade | Regra 1054 |
| CTE-ICMS-PREVISTO-VIGENCIA | 57 | Datas do grupo ICMS previsto no pagamento antecipado | hom. 01/02/2027; prod. 01/03/2027 (nota da seção) ou hom. 13/10/2026; prod. 16/11/2026 (cronograma) | Regras 1051 a 1053 |
| CTE-NT2026004-GERAL | 57, 67 e 64 | Primeiro bloco da NT 2026.004 | hom. 13/10/2026; prod. 16/11/2026 | Cronograma da NT, linha 1 |
| CTE-NT2026004-SIMPLIFICADO | 57 (CT-e Simplificado) | Estrutura nova do CT-e Simplificado | hom. 16/11/2026; prod. 14/12/2026 | Cronograma da NT, linha 2 |

O cancelamento do CT-e é vedado quando o CT-e é de substituição (rej. 574), tem CT-e de substituição ou complementar associado (576 e 660), carta de correção (523), MDF-e autorizado (528) ou comprovante de entrega autorizado (862). O ERP consulta essas relações em `Mov_Nota_Fiscal_Saida_Referenciada`, `Mov_Mdfe_Documento` e `Mov_Dfe_Evento` antes de enviar. O capítulo 13 do MOC lista os campos que a carta de correção não pode alterar, e o capítulo 12 a lista de CFOP aceitos; as duas listas vão para carga com vigência (Q-11).

**Nota de 11/10/2026 (D-N95).** As linhas CTE-IBS-UF-ALIQUOTA, CTE-IBS-MUN-ALIQUOTA e CTE-CBS-ALIQUOTA não guardam o valor: apontam para `Cad_Aliquota` e `Cad_Cronograma_Transicao_Tributaria`, que já existem no dicionário. As demais linhas da tabela ficam como estão.

## 6.4 NT 2026.004: cronograma

Em 06/10/2026, a NT tem duas linhas de implantação. A primeira (valores líquidos, exceção de alíquotas em homologação, ajuste do valor total, previsão de ICMS, eliminação da EPEC e da FS-DA, emissão offline e evento 211110) entra em homologação em **13/10/2026** e em produção em **16/11/2026**. A segunda, a nova estrutura do CT-e Simplificado, em **16/11/2026** em homologação e **14/12/2026** em produção. Cada versão do leiaute entra em `Cad_Dfe_Leiaute` com a data de implantação como vigência, e as datas ficam também em `Cad_Dfe_Parametro_Regra` (`CTE-NT2026004-GERAL` e `CTE-NT2026004-SIMPLIFICADO`).

**Conflito de datas (Q-5).** A nota da seção sobre o ICMS previsto diz "homologação em 01/02/2027 e produção em 01/03/2027", mas o cronograma da página 3 põe a previsão de ICMS na primeira linha (13/10/2026 e 16/11/2026). Não sei qual vale; a carga usa a data da seção, marcada "a confirmar", e as regras 1051 a 1053 ficam atrás da vigência.

## 6.5 Campos novos e regras de validação

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| Valor líquido da prestação | vTPrestLiq em vPrest (CT-e e CT-e OS), 0-1, 13v2 | Valor líquido total da prestação SEM tributos | Mov_Nota_Fiscal_Saida_Item.Valor_Total_Liquido (P-14 do documento 34) |
| Valor líquido no CT-e Simplificado | vPrestLiq em det e vTPrestLiq em total, 0-1, 13v2 | Valor líquido da prestação sem tributos, por item e no total | Item: Valor_Total_Liquido; total: derivado |
| Total líquido | cStat 1054 | Total líquido da prestação sem tributos difere do somatório dos itens (vPrestLiq) | Validação local antes de enviar (`CTE-TOTAL-LIQUIDO`) |
| ICMS previsto no pagamento antecipado | gICMSPrevistoPagtoAntecip/vICMSPrevisto em imp/ICMS, 0-1, 13v2 | Valor do ICMS a incidir no momento do fornecimento futuro; informar 0 quando não houver ICMS devido | Mov_Apuracao_Tributo_Item_Complemento (14º tipo do P-4) |

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| Grupo indevido | cStat 1051 | Grupo do ICMS previsto informado indevidamente: DF-e que não é de compra governamental nem de pagamento antecipado | Validação local |
| Grupo indevido | cStat 1052 | Mesma mensagem: `tpPagAnt` diferente de 1 e `tpOperGov` diferente de 4, com o grupo informado | Validação local |
| Grupo obrigatório | cStat 1053 | Grupo DEVE ser informado quando `tpPagAnt` for 1 ou `tpOperGov` for 4 e o grupo não vier | Validação local |
| Alíquota do IBS da UF | cStat 316 | 0,1% em 2026 (art. 343 da LC 214/25); 0,05% em 2027 e 2028 (art. 344); depois a de referência ou a específica da UF. Zero se o cClassTrib tem indicador de tributação regular. Em 2026, a homologação aceita as alíquotas de 2026 e de 2027 | `CTE-IBS-UF-ALIQUOTA` |
| Alíquota do IBS do Município | cStat 321 | 0% em 2026; 0,05% em 2027 e 2028; depois a de referência ou a específica do Município. Mesmas exceções | `CTE-IBS-MUN-ALIQUOTA` |
| Alíquota da CBS | cStat 326 | 0,90% em 2026 (art. 346 da LC 214/25). Exceção 1: tributação regular, zero. Exceção 2: zero na Zona Franca de Manaus (1302603, 1303569, 1301902) e nas cinco ALC. Até a publicação de 2027, usa-se a de 2026 também em homologação | `CTE-CBS-ALIQUOTA`, `CTE-CBS-ZERO-ZFM` e `CTE-CBS-ZERO-ALC` |
| Doação: emitente igual ao tomador | cStat 1055 | Com indDoacao 1, o CNPJ-Base ou CPF do emitente deve ser diferente do tomador | Validação local; campo Indicador_Doacao (P-3) |
| Doação vedada pelo cClassTrib | cStat 1056 | O cClassTrib com indicador que veda doação não admite indDoacao | Indicador no catálogo `Cad_Cclasstrib` (D-N62 do documento 41) |
| Doação exigida pelo cClassTrib | cStat 1057 | O cClassTrib com indicador que exige doação obriga indDoacao | Idem |
| Total do documento | cStat 365 | vTotDFe = vTPrest + vIBS + vCBS. Exceção: em 2026 não somar IBS e CBS; vTotDFe repete vTPrest | `CTE-VTOTDFE-FORMULA`; vTotDFe fica derivado |

**Conflito do total (Q-6).** A introdução da NT diz que o IBS e a CBS já compõem `vTPrest` e "não deverão ser adicionados novamente" ao `vTotDFe`; a regra 365 diz o contrário a partir de 2027 (`vTotDFe = vTPrest + vIBS + vCBS`), e em 2026 `vTotDFe` repete `vTPrest`. Como o ERP deriva o total dos itens, guardo a fórmula por ano como parâmetro (`CTE-VTOTDFE-FORMULA`) e não grava o total; em 2026 a dúvida não tem efeito.

## 6.6 Alíquotas de transição e exceções (regras 316, 321 e 326)

As regras 316, 321 e 326 fixam as alíquotas por ano de emissão (IBS da UF 0,1% em 2026 e 0,05% em 2027 e 2028; IBS do Município 0% em 2026 e 0,05% em 2027 e 2028; CBS 0,90% em 2026) e abrem exceções: tributação regular zera a alíquota; em 2026 a homologação aceita também as de 2027; e a CBS pode ser zero na Zona Franca de Manaus (1302603, 1303569 e 1301902) e nas cinco Áreas de Livre Comércio quando emitente e fato gerador estão em municípios pares da mesma área. Tudo isso é parâmetro com vigência (seis linhas em `Cad_Dfe_Parametro_Regra`); a alíquota de 2027 da CBS e as de IBS de 2029 em diante ainda não foram publicadas (Q-4).

## 6.7 cClassTrib, tributação regular, compra governamental e doação

O grupo de IBS e CBS do CT-e 57 tem 47 linhas: 10 já cobertas por `Mov_Apuracao_Tributo_Item` (CST, cClassTrib, base, alíquota, valor, diferimento e devolução) e as demais pelo `Mov_Apuracao_Tributo_Item_Complemento` do P-4 do documento 34, que já tem tipo para tributação regular (8 linhas em `gTribRegular`), compra governamental (6 em `gTribCompraGov`) e estorno de crédito. Nada disso pede entidade nova: é o mesmo desenho da NFCom e da NFS-e (D-N72). O cClassTrib permitido por documento vem de `Cad_Cclasstrib_Documento`, que precisa ter linhas para os modelos 57, 67 e 64; os indicadores que as regras 1056 e 1057 consultam (doação vedada ou exigida) são os do D-N62 do documento 41. O pagamento vinculado (evento 110300) é o P-13, `Mov_Dfe_Vinculo_Pagamento`. A tabela de cClassTrib do CT-e não foi enviada (Q-14).

## 6.8 Formas de emissão, EPEC e FS-DA

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| Formas de emissão | tpEmis | Deixa de aceitar 4 (EPEC) e 5 (FS-DA); aceita 2 (contingência offline) de imediato; 1, 3, 7 e 8 permanecem | Mov_Documento_Fiscal.Tipo_Emissao e `Mov_Dfe_Contingencia` |
| Contingência: data e justificativa | cStat 586 e 587 (G008, G009, H004, H005) | dhCont e xJust só para contingência offline; texto da regra ainda cita FS-DA | Mov_Dfe_Contingencia (Data_Hora_Inicio e Justificativa) |
| FS-DA | cStat 928 (G008a e H004a) | Rejeita tpEmis 5; exceção para a SEFAZ de Minas Gerais | Sem dado |
| Atraso da emissão | cStat 228 (G103 e H077) | Atraso superior a 168 horas é rejeitado, salvo emitido em offline (cStat 150: autorizado fora de prazo). A redação antiga fica só na SEFAZ MG | `CTE-EMISSAO-ATRASO` |
| QR Code de contingência | cStat 853 e 855 (G215, G217, H131 e H133) | Redação antiga mantida somente na SEFAZ MG | Sem dado |
| Regras do EPEC | G184 a G192 (cStat 720, 640 a 645, 697 e 756) | Excluídas da autorização do CT-e 57 | Sem dado |

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| EPEC e liberação | cStat 629 | EPEC (110113) e Liberação de EPEC (240160) passam a ser rejeitados com "tpEvento inválido" | Sem dado |
| SVC | cStat 530 (N09) | Na SVC só se aceitam EPEC, liberação e cancelamento; a regra ainda cita o EPEC | Sem dado |

O ERP não implementa EPEC nem FS-DA para o CT-e. A forma de emissão offline (`tpEmis` 2) passa a ser aceita de imediato e usa `Mov_Dfe_Contingencia`, com data e justificativa de entrada (regras 586 e 587). A SEFAZ de Minas Gerais mantém a redação antiga (Q-8).

## 6.9 CT-e Simplificado reestruturado

O IBS e a CBS saem do corpo do documento e vão para o item `det`, de modo que cada viagem tenha a sua tributação, e o ICMS continua centralizado. A regra G101a (rej. 370, município de fim igual em todos os itens) é revogada. O novo grupo `total/IBSCBSTot` soma os itens (rej. 348 a 359, 305 e 306). Para o dicionário, cada `det` vira um item da nota de saída e o total é derivado.

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| IBS e CBS no item | det/nItem | Descentraliza imp/IBSCBS para o item `det`, mantendo o ICMS centralizado | Mov_Nota_Fiscal_Saida_Item (um item por det) e Mov_Apuracao_Tributo_Item |
| Revogação | cStat 370 (G101a) | Revoga: "o município de fim da prestação em todos os itens deve ser igual" | Mov_Cte_Complemento guarda o município de destino por item |
| Totais de IBS e CBS | cStat 348 e 349 | IBSCBSTot só deve ser informado se houver IBS/CBS nos itens, e deve se houver | Derivado dos itens |
| Totais do IBS UF | cStat 350, 351, 352 | Diferimento, devolução e valor do IBS UF conferem com a soma dos itens | Derivado |
| Totais do IBS Municipal | cStat 353, 354, 355 | Diferimento, devolução e valor do IBS Municipal conferem com a soma dos itens | Derivado |
| Total do IBS | cStat 356 | vIBS igual a vIBSUF mais vIBSMun | Derivado |
| Totais da CBS | cStat 357, 358, 359 | Diferimento, devolução e valor da CBS conferem com a soma dos itens | Derivado |
| Estorno de crédito | cStat 305 e 306 | Total de IBS e de CBS estornados confere com a soma dos itens | Derivado; item em Mov_Apuracao_Tributo_Item_Complemento |

## 6.10 Evento de apropriação do crédito presumido (211110)

O tomador de serviço de transportador autônomo (TAC) emitido pela Nota Fiscal Fácil ou pelo PAA, ou de MEI, registra o evento para apropriar o crédito presumido de IBS e de CBS. A autorização é exclusiva da SVRS e o sucesso devolve cStat 135. O ERP emite o evento quando a Mlegate é a tomadora (decisão D-N71); o crédito vira linha de `Mov_Credito_Fiscal` com origem no evento. O catálogo `Cad_Credito_Presumido_Ibs_Cbs` é novo e pode ser carregado com os 13 códigos da planilha cCredPres da IT 2025.002 v1.70, enviada junto do pacote da NFCom (F-5).

| Item | Regra ou cStat | O que diz | Destino no dicionário |
|---|---|---|---|
| Autor e modelo | Seção 8 | Gerado pelo tomador do serviço de TAC em CT-e com `tpEmis` 3 ou `procEmi` 4, ou de MEI (CRT 4); modelo 57; exige CT-e autorizado; autorização exclusiva na SVRS | Mov_Dfe_Evento (Papel_Autor tomador) |
| Sequência, cancelamento e substituição | cStat 636, 218 e 664 | Sequência máxima 1; CT-e cancelado; CT-e com substituição associada | Validação local |
| Quem pode | cStat 1060 | Só CT-e emitido por TAC (NFF ou PAA) ou MEI | Validação local sobre Tipo_Emissao, Processo_Emissao e regime do emitente |
| Código de crédito presumido | cStat 1061, 1062, 1063 | Código existente, que aceita apropriação por evento e que é permitido para CT-e | Cad_Credito_Presumido_Ibs_Cbs (indicadores e vigência) |
| Grupo do IBS | cStat 1064, 1065, 1066 | Grupo não permitido, exigido e valor igual à base vezes o percentual, com tolerância de 0,01 | Validação local (`CTE-TOLERANCIA-CREDITO-PRESUMIDO`) |
| Grupo da CBS | cStat 1067, 1068, 1069 | Mesmo para a CBS | Idem |
| Declaração de pagamento | cStat 1070 e 1071 | xDecPag exigida ou vedada conforme o indicador do código; dois literais (com e sem acento) | Mov_Dfe_Evento.Texto_Declaracao |
| Fim do processamento | cStat 135 | Evento homologado devolve 135 | Codigo_Retorno do evento |

A NT tem quatro inconsistências neste evento (Q-7): os grupos se chamam `gCredPresIBS` e `gCredPresCBS` nas regras e `gIBSCredPres` e `gCBSCredPres` no schema; `xDecPag` é 0-1 na NT e 1-1 no schema; a numeração das regras pula de 13 para 17; e a regra 1052 repete a mensagem da 1051. Vale o schema.

# 7. Como o CT-e e o MDF-e se ligam ao dicionário

| Fato | Onde fica no dicionário | Por quê |
|---|---|---|
| CT-e emitido | `Mov_Nota_Fiscal_Saida` (modelo 57 ou 67 em `ID_Modelo_Documento`, tomador em `ID_Participante_Cliente`, `Valor_Total` e `Valor_Frete`), um item de serviço em `Mov_Nota_Fiscal_Saida_Item` (no CT-e Simplificado, um por `det`), `Mov_Cte` com os dados próprios e `Mov_Documento_Fiscal` com chave, protocolo e XML (D-N1). Tributos em `Mov_Apuracao_Tributo_Item` com `Origem_Tipo` nota_fiscal_saida, e título a receber em `Mov_Titulo` | O CT-e é um documento fiscal de venda de serviço; reaproveita tributação, cobrança e escrituração da nota |
| CT-e recebido (frete comprado) | `Mov_Nota_Fiscal_Entrada` mais `Mov_Cte`, que alimenta o Bloco D da EFD. Crédito de IBS e CBS pelo mesmo caminho da nota de entrada | Já era a decisão registrada na Expedição (documento 33) |
| Partes do CT-e | `Cad_Participante` com `_Endereco`, `_Inscricao` (indicador de IE do tomador) e `_Email`; o tomador é um dos cinco papéis e `Mov_Cte.Papel_Tomador` diz qual | As 66 linhas de remetente, expedidor, recebedor, destinatário e tomador do CT-e 57 estão todas cobertas |
| MDF-e | `Mov_Mdfe` e filhas, com `Mov_Documento_Fiscal`; ligado a `Mov_Expedicao_Saida` e, quando há trecho, `Mov_Expedicao_Trecho`. Veículos em `Cad_Veiculo_Transporte`, que se liga a `Cad_Ativo_Imobilizado` quando o veículo é da empresa. Condutor, seguro, vale-pedágio, contratante, CIOT e pagamento em entidades próprias | Manifesto de carga: sem valor fiscal, sem escrituração, sem título |
| Eventos | `Mov_Dfe_Evento` e `Mov_Dfe_Evento_Item`; comprovante e insucesso de entrega em `Mov_Cte_Entrega`; vínculo de pagamento em `Mov_Dfe_Vinculo_Pagamento` | Um registro por evento, como no documento 33 |
| Contingência | `Mov_Dfe_Contingencia` (offline, 168 horas) e `Mov_Dfe_Tarefa` para o reenvio | Sem EPEC nem FS-DA no CT-e |
| CFOP do CT-e | `Cad_CFOP.Indicador_Cte` (campo novo) e o CFOP no item da nota (`ID_CFOP_Saida`) | A lista de CFOP aceitos é carga com vigência (Q-11) |

# 8. O que o dicionário cobre e o que é lacuna

| Situação | Significado |
|---|---|
| Coberto | O dado já tem campo no `model.json` (543 entidades) |
| Proposta dos docs 33/34 | O dado cabe em entidade ou campo que os documentos 33 e 34 propuseram e que ainda não existem |
| Derivado | A autoridade calcula ou devolve e o ERP não grava (descrição fixa do evento, versão do aplicativo, totais) |
| Só no XML | Fica no XML guardado; ou é assinatura, ou é de modelo e modal da onda 2, ou foi eliminado |
| Campo novo | Pede um campo novo numa entidade que existe ou foi proposta |
| Entidade nova | Pede uma entidade nova (as 16 da seção 9) |

| Situação | MDF-e | CT-e | Total |
|---|---|---|---|
| Coberto | 25 | 440 | 465 |
| Proposta dos docs 33/34 | 83 | 224 | 307 |
| Derivado | 34 | 121 | 155 |
| Só no XML | 74 | 270 | 344 |
| Campo novo | 67 | 84 | 151 |
| Entidade nova | 72 | 131 | 203 |
| Total | 355 | 1270 | 1625 |

As **354 lacunas** (139 no MDF-e e 215 no CT-e) se concentram em unidades de transporte e lacres, complemento do CT-e, pagamento do frete, documentos transportados e documentos anteriores. A tabela abaixo mostra quantas linhas de cada leiaute alimentam cada entidade nova.

| Entidade nova | Linhas dos dois leiautes |
|---|---|
| `Mov_Cte_Complemento` | 31 |
| `Mov_Cte_Passagem` | 2 |
| `Mov_Dfe_Observacao` | 16 |
| `Mov_Cte_Documento_Anterior` | 11 |
| `Mov_Cte_Ordem_Coleta` | 8 |
| `Mov_Cte_Entrega` | 15 |
| `Mov_Dfe_Unidade_Transporte` | 54 |
| `Mov_Dfe_Lacre` | 20 |
| `Mov_Dfe_Produto_Perigoso` | 18 |
| `Cad_Dfe_Parametro_Regra` | nenhuma (cadastro de regra) |
| `Cad_Credito_Presumido_Ibs_Cbs` | nenhuma (catálogo) |
| `Mov_Mdfe_Contratante` | 6 |
| `Mov_Mdfe_Ciot` | 3 |
| `Mov_Mdfe_Pagamento_Componente` | 9 |
| `Mov_Mdfe_Pagamento_Parcela` | 9 |
| `Mov_Mdfe_Seguro_Averbacao` | 1 |

Das 344 linhas "só no XML", o motivo é:

| Motivo | Linhas |
|---|---|
| Modelos e modais da onda 2 | 213 |
| Assinatura digital, responsável técnico, PAA e solicitação NFF (já tratados pela infraestrutura) | 116 |
| Eliminado pela NT 2026.004 (EPEC) | 15 |

# 9. Entidades e campos propostos

**16 entidades novas.** Nenhuma colide com as 543 do `model.json` nem com as dos documentos 33 a 41; os nomes foram conferidos por script. Todas são da onda 1; o que é da onda 2 não é proposta: os nomes que aparecem nas tabelas das seções 4 e 6 para esses leiautes (`Mov_Cte_Os`, `Mov_Cte_Os_Documento_Referenciado`, `Mov_Cte_Os_Gtve`, `Mov_Gtve`, `Mov_Gtve_Especie`, `Mov_Cte_Item`, `Mov_Cte_Item_Documento_Anterior`, `Mov_Cte_Veiculo_Novo`, `Mov_Cte_Modal_Aereo`, `Mov_Mdfe_Modal_Aereo`, `Mov_Mdfe_Modal_Aquaviario` e `Mov_Mdfe_Vagao`) são só rótulos de esboço, indicam onde o dado cairia, e ficam na coluna de destino da planilha até haver cliente (D-N68).

| Entidade | Vigência | Para que serve e por que é nova | Campos principais |
|---|---|---|---|
| `Mov_Cte_Complemento` | não | Dados opcionais do CT-e que não cabem no cabeçalho: CT-e globalizado, retirada da mercadoria, características adicionais, funcionário emissor, fluxo, entrega programada e origem e destino do cálculo do frete. Uma linha por CT-e. São 24 elementos raros e opcionais. Em `Mov_Cte` eles viram colunas quase sempre vazias; separados, o cabeçalho continua legível. | ID_Cte (→Mov_Cte, identidade); Indicador_Globalizado; Observacao_Globalizado; Indicador_Retira; Detalhe_Retira; Caracteristica_Adicional_Transporte; Caracteristica_Adicional_Servico; Funcionario_Emissor; Origem_Fluxo; Destino_Fluxo; Rota_Fluxo; Tipo_Periodo_Entrega {sem_data, na_data, ate_a_data, a_partir_da_data, no_periodo}; Tipo_Hora_Entrega {sem_hora, no_horario, ate_o_horario, a_partir_do_horario, no_intervalo}; Data_Programada_Entrega; Data_Inicio_Entrega; Data_Fim_Entrega; Hora_Programada_Entrega; Hora_Inicio_Entrega; Hora_Fim_Entrega; Origem_Calculo_Frete; Destino_Calculo_Frete |
| `Mov_Cte_Passagem` | não | Pontos de passagem previstos do fluxo da carga (`fluxo/pass`), na ordem informada. É repetição (0 a n); não cabe em `Mov_Cte_Complemento`, que tem uma linha por CT-e. | ID_Cte (→Mov_Cte); Sequencia; Descricao_Passagem |
| `Mov_Dfe_Observacao` | não | Observações em pares campo e texto do contribuinte e do fisco (`ObsCont` e `ObsFisco`, até 10 de cada). Serve ao CT-e e também à NF-e, que tem a mesma estrutura. O P-1 do documento 34 guarda um texto único (Informacoes_Complementares, Informacoes_Fisco), mas o CT-e envia pares nomeados e o Fisco pode devolvê-los separados; o par nomeado não cabe num texto sem perder a estrutura. | ID_Documento_Fiscal (→Mov_Documento_Fiscal); Tipo_Observacao {contribuinte, fisco}; Sequencia; Nome_Campo (até 20); Texto (até 160 para o contribuinte e 60 para o fisco) |
| `Mov_Cte_Documento_Anterior` | não | Documentos de transporte anteriores (redespacho e subcontratação): o emitente anterior e o documento, em papel ou CT-e eletrônico. `Mov_Cte_Documento_Transportado` guarda o que a carga leva; este guarda o documento do trecho anterior, que tem outro emitente e outros tipos (códigos 07 a 13 do schema). | ID_Cte (→Mov_Cte); ID_Participante_Emitente_Anterior (→Cad_Participante); Tipo_Documento_Anterior {cte_eletronico, atre, dta, conhecimento_aereo_internacional, carta_porte_internacional, conhecimento_avulso, tif, bl}; Chave_Cte_Anterior; Serie; Subserie; Numero_Documento; Data_Emissao; ID_Documento_Fiscal_Anterior (→Mov_Documento_Fiscal, opcional) |
| `Mov_Cte_Ordem_Coleta` | não | Ordens de coleta associadas ao CT-e rodoviário (`rodo/occ`). Repetição própria do CT-e rodoviário, sem par em nenhuma entidade existente. | ID_Cte (→Mov_Cte); Serie; Numero_Ordem_Coleta; Data_Emissao; ID_Participante_Emitente (→Cad_Participante); Codigo_Interno_Emitente; Telefone_Emitente |
| `Mov_Cte_Entrega` | não | Comprovante de entrega (110180) e insucesso de entrega (110190), com data, recebedor, geolocalização e hash da imagem. As NF-e entregues ficam em `Mov_Dfe_Evento_Item.Chave_Documento`. São dados do fato da entrega, que `Mov_Dfe_Evento` (genérico) não comporta; a imagem em si vai para `Cad_Documento`. | ID_Dfe_Evento (→Mov_Dfe_Evento, identidade); Tipo_Entrega {comprovante, insucesso}; Data_Hora_Entrega; Numero_Tentativa; Motivo_Insucesso {recebedor_nao_encontrado, recusa_do_recebedor, endereco_inexistente, outros}; Justificativa_Motivo (só para outros); Numero_Documento_Recebedor; Nome_Recebedor; Latitude; Longitude; Hash_Entrega; Data_Hora_Hash |
| `Mov_Dfe_Unidade_Transporte` | não | Unidades de transporte (veículo, balsa, vagão e outros) e unidades de carga (contêiner, ULD, pallet) de um documento do CT-e ou do MDF-e, com rateio. Dois níveis na mesma tabela. A estrutura se repete em três lugares do MDF-e (CT-e, NF-e e MDF-e transportados) e em quatro do CT-e (NF, NF-e e outros do CT-e 57, mais a NF-e do Simplificado); uma tabela só evita sete cópias. | ID_Unidade_Transporte; Origem_Tipo {cte_documento, mdfe_documento}; ID_Origem (→Mov_Cte_Documento_Transportado ou →Mov_Mdfe_Documento); ID_Unidade_Transporte_Pai (autorreferência; carga dentro do transporte); Nivel {transporte, carga}; Tipo_Unidade (domínio por nível); Identificacao; Quantidade_Rateada |
| `Mov_Dfe_Lacre` | não | Lacres de uma unidade, do veículo rodoviário ou do documento. Mesma razão: o lacre aparece em 20 caminhos do leiaute. | Origem_Tipo {unidade, documento, rodoviario}; ID_Origem; Numero_Lacre |
| `Mov_Dfe_Produto_Perigoso` | não | Produtos perigosos de um documento transportado pelo MDF-e (número ONU, nome apropriado, classe de risco, grupo de embalagem e quantidades). Repetição por documento, com obrigatoriedade legal de transporte de carga perigosa; o `Origem_Tipo` permite reaproveitar para o CT-e aéreo e aquaviário (onda 2). | Origem_Tipo {mdfe_documento}; ID_Origem (→Mov_Mdfe_Documento); Numero_Onu; Nome_Apropriado_Embarque; Classe_Risco; Grupo_Embalagem; Quantidade_Total_Produto; Quantidade_Tipo_Volume |
| `Cad_Dfe_Parametro_Regra` | sim, histórico | Catálogo das regras de negócio dos DF-e que dependem de prazo, limite, alíquota, data ou lista, cada uma com vigência. Cobre os 35 parâmetros das seções 4 e 6. `Cad_Dfe_Leiaute` tem uma linha por modelo e versão, e os documentos 34 e 41 já puseram nele seis campos de parâmetro. Uma alíquota que muda por ano ou um prazo que muda sem mudar o leiaute não cabe em campo de leiaute; uma tabela de regra com vigência atende sem alterar tabela quando a lei mudar. | ID_Modelo_Documento (→Cad_Classe_Sistema, domínio modelo_documento_fiscal); Codigo_Regra (identidade); Descricao; Valor_Numerico; Valor_Texto; Unidade; Ambiente {producao, homologacao, ambos}; Codigo_Retorno_Referencia (→Cad_Dfe_Codigo_Retorno); Fonte; Vigencia_Inicio; Vigencia_Fim; Motivo_Vigencia |
| `Cad_Credito_Presumido_Ibs_Cbs` | sim, histórico | Catálogo do código de crédito presumido (cCredPres) com os indicadores que as regras 1061 a 1071 consultam. O doc 41 (D-N62) põe só a marca de crédito presumido no `Cad_Cclasstrib`; o código e os indicadores por documento e por evento precisam de tabela própria. Os campos foram deduzidos das regras da NT, e a planilha cCredPres da IT 2025.002 v1.70 (documento 40) confirma e completa a lista: acrescenta o artigo da LC 214/2025, o indicador de dedução (`indDeduzCredPres`), o cClassTrib da nota referenciada, o percentual de redução de transição do IBS, a vigência separada de CBS e de IBS (vários códigos começam em 01/01/2027) e a fórmula de cálculo. Esses campos entram na revisão desta entidade. | Codigo (2, identidade); Descricao; Indicador_Uso_Cte; Indicador_Apropriacao_Por_Evento; Indicador_Credito_Ibs {nao_permite, permite, exige}; Indicador_Credito_Cbs {nao_permite, permite, exige}; Indicador_Declaracao_Pagamento {nao_permite, exige}; Percentual_Referencia_Ibs; Percentual_Referencia_Cbs; Vigencia_Inicio; Vigencia_Fim; Motivo_Vigencia |
| `Mov_Mdfe_Contratante` | não | Contratantes do serviço de transporte (`infContratante`, 0 a n) e o contrato a que se ligam. O `Mov_Mdfe_Pagamento_Frete` do doc 33 tem um contratante só; o leiaute admite vários, e o evento 110117 só aceita autor que conste entre eles (rej. 748). | ID_Mdfe (→Mov_Mdfe); ID_Participante_Contratante (→Cad_Participante; cobre CPF, CNPJ e identificador estrangeiro); Numero_Contrato; Valor_Contrato_Global |
| `Mov_Mdfe_Ciot` | não | CIOT do MDF-e (0 a n), com o responsável. Passou a opcional na NT 2025.001. O CIOT é do MDF-e, não do CT-e: o schema 4.00 do CT-e rodoviário não o tem. O doc 33 o colocou em `Mov_Cte`; o desenho corrige. | ID_Mdfe (→Mov_Mdfe); Numero_Ciot; ID_Participante_Responsavel (→Cad_Participante) |
| `Mov_Mdfe_Pagamento_Componente` | não | Componentes do valor do contrato de frete (vale-pedágio, impostos, despesas, frete e outros), no MDF-e e nos eventos 110116 e 110118. O doc 33 coloca "componentes" dentro de `Mov_Mdfe_Pagamento_Frete`, mas são 1 a n e a soma deve igualar o contrato (rej. 746). | ID_Mdfe_Pagamento_Frete (→Mov_Mdfe_Pagamento_Frete); Tipo_Componente {vale_pedagio, impostos, despesas, frete, outros}; Valor_Componente; Descricao_Componente |
| `Mov_Mdfe_Pagamento_Parcela` | não | Parcelas do pagamento a prazo do frete (número, vencimento e valor), ligadas ao título a pagar quando ele existir. A soma das parcelas deve igualar o contrato (rej. 738) e o vencimento precisa gerar título; a ligação opcional evita duplicar o contas a pagar. | ID_Mdfe_Pagamento_Frete (→Mov_Mdfe_Pagamento_Frete); Numero_Parcela; Data_Vencimento; Valor_Parcela; ID_Titulo (→Mov_Titulo, opcional) |
| `Mov_Mdfe_Seguro_Averbacao` | não | Números de averbação do seguro da carga (`nAver`, 0 a n). O doc 33 tem um Numero_Averbacao único em `Mov_Mdfe_Seguro`; o leiaute aceita vários por apólice. | ID_Mdfe_Seguro (→Mov_Mdfe_Seguro); Numero_Averbacao |

**Campos e valores novos em entidades existentes ou propostas** (22 linhas):

| Entidade | Situação | Mudança | Por que | Decisão |
|---|---|---|---|---|
| `Mov_Cte` | proposta do doc 33 (A.5) | Tipo_Cte sem "anulação": domínio {normal, complemento, substituicao, simplificado, substituicao_simplificado}, com `gtve` quando a onda 2 entrar. Ciot e ID_Cst saem. Campos novos: Papel_Tomador {remetente, expedidor, recebedor, destinatario, outros}; ID_Municipio_Envio; Tipo_Pagamento_Antecipado {pagamento_antecipado, fornecimento_pago_anteriormente}; Indicador_Altera_Tomador; Outras_Caracteristicas_Carga; Valor_Carga_Averbacao | O schema 4.00 só tem `tpCTe` 0, 1 e 3 (57 e 67), 4 (GTV-e), 5 e 6 (simplificado). O CIOT é do MDF-e. O CST do ICMS é por item, em `Mov_Apuracao_Tributo_Item` | D-N67 |
| `Mov_Cte_Documento_Transportado` | proposta do doc 33 (A.5) | Tipo_Documento {nfe, nf_papel, dce, outros}; campos do documento em papel (série, número, emissão, valores, CFOP, peso); Pin_Suframa; Data_Prevista_Entrega | O leiaute admite NF em papel, declaração e outros além da NF-e | D-N67 |
| `Mov_Mdfe` | proposta do doc 33 (A.5) | Mantém ID_Expedicao e ganha ID_Trecho (→Mov_Expedicao_Trecho, opcional). Campos novos: Indicador_Canal_Verde; Indicador_Carrega_Posterior; Tipo_Carga; Descricao_Produto_Predominante; Gtin_Produto_Predominante; ID_Classificacao_Mercadoria; CEP, latitude e longitude do carregamento e do descarregamento (6 campos); ID_Unidade_Medida; Data_Encerramento; ID_Estado_Encerramento; ID_Municipio_Encerramento; Indicador_Encerrado_Por_Terceiro; Codigo_Agendamento_Porto; Informacoes_Complementares; Informacoes_Fisco | O MDF-e liga ao transporte próprio pela Expedição; o trecho diz qual modal e transportadora do trecho. Os demais vêm do `ide`, do `prodPred`, do `tot` e do evento de encerramento | D-N67 |
| `Mov_Mdfe_Documento` | proposta do doc 33 (A.5) | Tipo_Documento ganha `mdfe`; campos novos: Indicador_Reentrega; Indicador_Prestacao_Parcial; Quantidade_Total_Entrega e Quantidade_Parcial_Entrega; Segundo_Codigo_Barras; ID_Mdfe_Documento_Pai (as NF-e entregues numa prestação parcial viram linhas filhas); ID_Dfe_Evento (quando entrou por inclusão de DF-e) | Prestação parcial veio com a NT 2024.002; MDF-e pode transportar MDF-e (`infMDFeTransp`) | D-N67 |
| `Mov_Mdfe_Condutor` | proposta do doc 33 (A.5) | Campos novos: Nome_Condutor; Cpf_Condutor; ID_Dfe_Evento | O condutor do MDF-e não é participante cadastrado (nome e CPF); entra também por evento | D-N67 |
| `Mov_Mdfe_Seguro` | proposta do doc 33 (A.5) | Campo novo: ID_Participante_Responsavel (→Cad_Participante) | O responsável pelo seguro (`infResp`) pode ser o contratante | D-N67 |
| `Mov_Mdfe_Vale_Pedagio` | proposta do doc 33 (A.5) | Numero_Comprovante é substituído por Identificador_Vpo (IDVPO); campos novos: Tipo_Vale_Pedagio {tag, leitura_de_placa}; Categoria_Combinacao_Veicular; ID_Participante_Pagador | A NT 2025.001 trocou o número do comprovante pelo IDVPO e fixou o tipo em 01 e 04 | D-N67 |
| `Mov_Mdfe_Pagamento_Frete` | proposta do doc 33 (A.5) | Campos novos: Indicador_Alto_Desempenho; Valor_Adiantamento; Indicador_Antecipa_Adiantamento; Tipo_Antecipacao_Parcelas {nao_permite, permite, permite_com_confirmacao}; ID_Participante_Dados_Bancarios (→Cad_Participante_Dados_Bancarios: banco, agência e chave PIX); Cnpj_Ipef; Quantidade_Viagens; Numero_Viagem; ID_Dfe_Evento_Origem | Cobre o grupo `infPag` do MDF-e e dos eventos 110116 e 110118 | D-N67 |
| `Cad_Veiculo_Transporte` | proposta do doc 33 (A.5) | Campos novos: Codigo_Interno; Tipo_Proprietario {tac_agregado, tac_independente, outros} | O `tpProp` decide a regra 723 do evento 110116 | D-N67 |
| `Mov_Documento_Fiscal` | proposta do doc 33 (A.2) | Tipo_Emissao ganha `nota_fiscal_facil`. Campo novo: Processo_Emissao {aplicativo_contribuinte, aplicativo_sebrae, aplicativo_fisco, paa}. Em `Cad_Dfe_Emitente_Configuracao`, certificado deixa de ser exigido quando `nota_fiscal_facil` | NFF e PAA mudam quem assina e quais regras valem (seção 3) | D-N69 |
| `Mov_Nota_Fiscal_Saida_Referenciada` | proposta do doc 34 (A.4) | Tipo_Referencia ganha cte_substituido, cte_complementado e cte_multimodal | O CT-e de complemento, substituição e serviço vinculado a multimodal referencia o CT-e original | D-N67 |
| `Mov_Nota_Fiscal_Saida_Autorizado_Xml` | proposta do doc 34 (P-2) | Campo novo opcional: ID_Documento_Fiscal | O CT-e emitido tem `autXML` e a nota de saída do CT-e é a mesma entidade | D-N67 |
| `Mov_Dfe_Evento` | proposta do doc 33 (A.2) | Campos novos: Texto_Declaracao (declaração de pagamento do 211110); ID_Dfe_Evento_Cancelado (autorreferência dos eventos de cancelamento 110181, 110191, 110301 e 610111) | Os cancelamentos apontam para o evento que cancelam, e não para o documento | D-N67 |
| `Mov_Dfe_Evento_Item` | proposta do doc 34 (A.2) | Campos novos: Grupo_Alterado; Campo_Alterado; Valor_Alterado; Numero_Item_Alterado (carta de correção); Chave_Documento (NF-e entregue); Base_Credito_Presumido, Percentual e Valor de IBS e de CBS | A carta de correção, a entrega e o crédito presumido listam itens | D-N67 e D-N71 |
| `Mov_Apuracao_Tributo_Item` | existente | Campo novo opcional: ID_Estado_Devedor (→Cad_Estado) para o `ICMSOutraUF` | A apuração estadual é por UF; o grupo do CT-e não traz a UF (é a UF de início da prestação), então o campo é gravado na emissão | D-N72 |
| `Mov_Apuracao_Tributo_Item_Complemento` | proposta do doc 34 (P-4) | Sem tipo novo: o ICMS previsto é o 14º; tributação regular, compra governamental e estorno de crédito já estavam previstos | A classificação cabe nos 16 tipos dos documentos 34 e 41 | D-N72 |
| `Mov_Credito_Fiscal` | existente | Origem ganha `evento_dfe`; campo novo opcional ID_Dfe_Evento_Origem (→Mov_Dfe_Evento) | O crédito presumido do 211110 não nasce de uma linha de nota de entrada; nasce do evento homologado (cStat 135). Alternativa: registrar como `cadastro_manual` | D-N71 |
| `Cad_CFOP` | existente | Campo novo: Indicador_Cte (booleano) | O CT-e aceita uma lista fixa de CFOP (capítulo 12 do MOC); os indicadores atuais cobrem NF-e e comunicação, não o CT-e | D-N72 |
| Cad_Cclasstrib e Cad_Cst | existentes, com os campos do doc 41 (D-N62) | Sem campo novo; o CT-e usa os mesmos indicadores (`ind_gTribRegular`, `ind_gEstornoCred`, doação) e a tabela `Cad_Cclasstrib_Documento` precisa de linhas para os modelos 57, 67 e 64 | Reaproveita a classificação da NFCom e da NFS-e | D-N72 |
| `Cad_Participante_Documento_Fiscal` | existente | Valor novo no domínio `tipo_documento_fiscal`: rntrc | O RNTRC identifica o transportador e é validado na ANTT (F108 a F113) | D-N67 |
| `Cad_Dfe_Leiaute` | proposta do doc 34 | Linhas novas para CT-e 4.00 (NT 2026.004, RTC 1.00) e MDF-e 3.00 (NT 2025.001) com as datas de implantação da NT como vigência | Cada versão é uma linha; as datas não ficam no código | D-N70 |
| `Cad_Classe_Sistema` | existente | Valores novos em `modelo_documento_fiscal` (57, 58, 64, 67, se faltarem) e em `tipo_evento_dfe` (os códigos da seção 6); 12 domínios novos, listados abaixo | Domínios de pequeno vocabulário seguem o padrão do dicionário | D-N67 |

**Domínios novos** em `Cad_Classe_Sistema` (12), todos de vocabulário pequeno e fechado pelo schema:

| Domínio | Valores | Origem |
|---|---|---|
| tipo_unidade_transporte | 1 rodoviário tração; 2 rodoviário reboque; 3 navio; 4 balsa; 5 aeronave; 6 vagão; 7 outros | MDF-e `tpUnidTransp` e CT-e (o do CT-e tem outro vocabulário e é onda 2) |
| tipo_unidade_carga | 1 contêiner; 2 ULD; 3 pallet; 4 outros | MDF-e `tpUnidCarga` |
| tipo_carga_antt | 01 a 12 (granel sólido, granel líquido, frigorificada, conteinerizada, carga geral, neogranel, perigosas em cinco formas e granel pressurizada) | Resolução ANTT 5.849/2019; o 12 entrou na NT 2025.001 |
| tipo_rodado | 01 truck; 02 toco; 03 cavalo mecânico; 04 van; 05 utilitário; 06 outros | `tpRod` |
| tipo_carroceria | 00 não aplicável; 01 aberta; 02 fechada ou baú; 03 graneleira; 04 porta contêiner; 05 sider | `tpCar` |
| categoria_combinacao_veicular | 02, 04, 06, 07, 08, 10, 11, 12, 13 e 14 (veículo comercial por número de eixos e combinações) | `categCombVeic` |
| tipo_componente_pagamento_frete | 01 vale-pedágio; 02 impostos, taxas e contribuições; 03 despesas; 04 frete; 99 outros | `tpComp`; o 04 entrou na NT 2025.001 |
| tipo_vale_pedagio | 01 TAG; 04 leitura de placa | `tpValePed`; o 02 e o 03 saíram na NT 2025.001 |
| tipo_documento_anterior | cte_eletronico; 07 ATRE; 08 DTA; 09 conhecimento aéreo internacional; 10 carta de porte internacional; 11 conhecimento avulso; 12 TIF; 13 BL | `idDocAntPap/tpDoc` do CT-e |
| tipo_periodo_entrega | 0 sem data; 1 na data; 2 até a data; 3 a partir da data; 4 no período; e os de hora (0 a 4) | `compl/Entrega` do CT-e |
| motivo_insucesso_entrega | 1 recebedor não encontrado; 2 recusa do recebedor; 3 endereço inexistente; 4 outros (exige justificativa) | `tpMotivo` do evento 110190 |
| tipo_antecipacao_parcelas | 0 não permite; 1 permite; 2 permite mediante confirmação | `tpAntecip` |

**Cadastro de regras com vigência.** `Cad_Dfe_Parametro_Regra` guarda os 35 parâmetros das seções 4 e 6 e tem estes campos:

| Campo | Conteúdo |
|---|---|
| ID_Modelo_Documento | Modelo a que a regra se aplica (→ `Cad_Classe_Sistema`, domínio `modelo_documento_fiscal`); uma regra para vários modelos vira várias linhas |
| Codigo_Regra | Identificador estável da regra, como os da tabela acima (identidade, junto com a vigência) |
| Descricao | Texto da regra |
| Valor_Numerico | Valor numérico quando a regra é um limite, prazo, alíquota ou tolerância |
| Valor_Texto | Valor quando é expressão regular, fórmula ou lista |
| Unidade | horas, dias, minutos, meses, ocorrências, percentual, R$, expressão regular |
| Ambiente | Produção, homologação ou ambos (a regra 316 difere nos dois) |
| Codigo_Retorno_Referencia | Rejeição que a SEFAZ devolve (→ `Cad_Dfe_Codigo_Retorno`) |
| Fonte | Documento e regra de origem (MOC, regra G103, NT 2026.004 regra 316...) |
| Vigencia_Inicio, Vigencia_Fim, Motivo_Vigencia | Padrão de vigência do dicionário; a regra nunca é código fixo |

A tabela completa de parâmetros, com valor, unidade, rejeição e observação, está na aba "Parâmetros e prazos" da planilha.

# 10. Pendências

O que ficou sem resposta nas fontes ou que as fontes contradizem. Cada uma tem um tratamento provisório, que não altera o dicionário.

| Nº | Dúvida ou conflito | Onde está | Tratamento proposto |
|---|---|---|---|
| Q-1 | O Anexo I do MOC do CT-e (leiaute e regras de validação campo a campo) não foi enviado | F-1; pasta de materiais | Classifico pelos schemas; as regras de documento transportado, de ICMS e de modal ficam para quando o Anexo chegar |
| Q-2 | Faltam o pacote do MDF-e anterior à NT 2024.001, os schemas do CT-e anteriores ao 4.00 desta NT e os textos das quatro NTs | F-2 e F-3 | Histórico do MDF-e só mede o que os três pacotes mostram; o da NT 2024.001 é só a linha de base |
| Q-3 | A Mlegate ou algum cliente emite CT-e OS, GTV-e, CT-e Simplificado ou usa modal aéreo, aquaviário, ferroviário, dutoviário ou multimodal? | D-N6; documento 33 | Sem resposta, onda 2 só como esboço (D-N68) |
| Q-4 | A alíquota da CBS de 2027 e as de IBS de 2029 em diante ainda não foram publicadas | NT 2026.004, regras 316, 321 e 326 | Parâmetro sem valor até a publicação; em homologação aceita-se a de 2026 |
| Q-5 | As datas do ICMS previsto no pagamento antecipado se contradizem: 13/10/2026 e 16/11/2026 no cronograma, 01/02/2027 e 01/03/2027 na nota da seção 3 | NT 2026.004, páginas 3 e 6 | Carga com a data da seção e marca "a confirmar"; as regras 1051 a 1053 ficam atrás da vigência |
| Q-6 | vTotDFe: a introdução da NT diz que IBS e CBS não se somam de novo ao total; a regra 365 manda somar a partir de 2027 e o campo traz "vTPrest + total do IBS + total da CBS" | NT 2026.004, seções 1 e 5 | Fórmula por ano em parâmetro; em 2026 todas as leituras dão vTPrest, então o conflito só aparece em 2027 |
| Q-7 | Redação do evento 211110 e de regras vizinhas: nomes dos grupos (gCredPresIBS e gCredPresCBS nas regras; gIBSCredPres e gCBSCredPres no schema); xDecPag 0-1 na NT e 1-1 no schema; regras numeradas de 1 a 13 e depois 17 e 18; G008, G009, H004 e H005 com texto truncado; regras 1051 e 1052 com a mesma mensagem | NT 2026.004, seções 3, 6 e 8 | Vale o schema para o nome e a obrigatoriedade; perguntar ao ENCAT se a 1052 deveria ter outra mensagem |
| Q-8 | A tabela de `tpEmis` da NT ainda lista 4 e 5 depois de eliminá-los; a regra N09 (SVC) ainda cita o EPEC; o evento de liberação de EPEC aparece como "24160" | NT 2026.004, seções 6 e 3 | Vale o texto (eliminação); EPEC e FS-DA fora do domínio do CT-e |
| Q-9 | `procEmi` 3 no CT-e é "aplicativo do SEBRAE" no CT-e 57 e no CT-e Simplificado e "aplicativo do Fisco" no CT-e OS | Schemas 4.00 | Domínio `aplicativo_sebrae` e `aplicativo_fisco` separados; confirmar se são o mesmo |
| Q-10 | A tabela 3.7.1 do MOC do CT-e dá modelo 64 aos eventos 240180 e 240181 ("CT-e OS"), que é o 67 | MOC do CT-e, item 3.7.1 | Trato como 67; sem impacto enquanto o CT-e OS for onda 2 |
| Q-11 | A lista de CFOP aceitos no CT-e (capítulo 12 do MOC) é de 2022 e não foi conferida com a NT de CFOP de 2026 | MOC do CT-e, cap. 12; F-7 | Carga com vigência em `Cad_CFOP.Indicador_Cte`; conferir quando a NT de CFOP chegar |
| Q-12 | Não há schema de distribuição DF-e do CT-e, então o ERP não tem como receber CT-e de frete comprado por NSU | F-4 | Recebimento por chave informada ou XML anexado até o schema chegar |
| Q-13 | Eventos 610190 e 610191 (insucesso do CT-e na NF-e) e 510630 (passagem automática originada no MDF-e) seguem adiados; o MOC do MDF-e lista o 510620 e a pasta bt traz o 510630 | Documento 38; pasta bt | Continuam adiados; conferir o código com o ENCAT antes de desenhar |
| Q-14 | Tabelas externas não enviadas: cClassTrib aplicável ao CT-e, embarcações, portos e terminais do MOC do MDF-e, tabela de meios de pagamento do evento 110300 (IT 2026.001) | F-5 e F-6 | Catálogos nascem vazios (o de crédito presumido já tem fonte: a planilha cCredPres); cada um vira carga com vigência quando a tabela chegar |
| Q-15 | A regra N03 do CT-e rejeita eventos em série 890 a 899 (rej. 670) sem dizer o que a faixa significa | MOC do CT-e, regra N03 | Parâmetro `CTE-SERIE-EVENTO-RESERVADA` não criado por falta de significado; perguntar |
| Q-16 | O `vTotTrib` (valor aproximado de tributos) não tem lugar no dicionário | CT-e `imp/vTotTrib` | Derivado, como o doc 34 fez para a NF-e; sem entidade |
| Q-17 | Erros de documentação nos schemas: enumeração duplicada no modal da GTV-e (01, 06, 01, 06); no MDF-e a longitude descrita como "Latitude", `indAntecipaAdiant` com o texto de `indAltoDesemp` e `respSeg` com "22" no texto e valores 1 e 2 na enumeração | Schemas | Vale a enumeração, não o texto; registrado |
| Q-18 | O pacote da NT 2025.001 do MDF-e chama-se "1.04" e a pasta interna "1.05"; o DAMDFE é de agosto de 2021 e o MOC de agosto de 2022; os dois MOCs são anteriores às NTs recentes | Pacotes e MOCs | Uso o schema como verdade e o MOC como contexto; cada prazo do MOC vira parâmetro que se confere antes de ativar |

# 11. Decisões para Alberto

A numeração continua depois da D-N65 do documento 41; as D-N52 a D-N65 ficam reservadas aos documentos da NFCom, da NFS-e e de outros materiais.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N66 | Escopo da primeira onda: o framework dos quatro modelos (57, 58, 64, 67), o MDF-e rodoviário, o CT-e 57 rodoviário emitido e recebido e os eventos que o ERP emite ou recebe (cancelamento, carta de correção, encerramento, inclusão de condutor e de DF-e, pagamento, comprovante e insucesso de entrega, vinculação de pagamento, desacordo e crédito presumido). O restante (CT-e OS, GTV-e, CT-e Simplificado, aéreo, aquaviário, ferroviário, dutoviário e multimodal) fica na onda 2 | **Sim.** O doc 33 já ligava o CT-e e o MDF-e à Expedição, que é rodoviária. A onda 2 reúne 38 linhas do MDF-e e 774 do CT-e (CT-e OS, GTV-e, CT-e Simplificado e os modais), todas já classificadas, com esboço de entidade onde o dado não tem lugar |
| D-N67 | Modelagem: CT-e emitido como nota de saída (`Mov_Nota_Fiscal_Saida` com um item de serviço) mais `Mov_Cte`; CT-e recebido como nota de entrada mais `Mov_Cte`; MDF-e fora das notas (só `Mov_Mdfe` e filhas); as 16 entidades novas (seção 9) e os ajustes às propostas do doc 33 (sem "anulação", CIOT no MDF-e, sem ID_Cst em `Mov_Cte`, IDVPO)? | **Sim.** Reaproveita a tributação por item, o título a receber e a escrituração que a nota já tem; o MDF-e não tem valor fiscal e não vira nota. Os ajustes seguem o schema 4.00 e o MOC |
| D-N68 | Conteúdo da onda 2 (CT-e OS, GTV-e, CT-e Simplificado, modais não rodoviários): desenhar só quando houver cliente da Mlegate e leiaute oficial (D-N6)? Esta rodada já leu os leiautes, então o desenho existe como esboço | Só com cliente. O CT-e Simplificado merece prioridade se algum cliente transportar para um tomador só, porque a NT 2026.004 o reestrutura em 14/12/2026 |
| D-N69 | Domínios de forma e processo de emissão: `Tipo_Emissao` ganha `nota_fiscal_facil`, `epec` continua só para a NF-e e o CT-e não usa EPEC nem FS-DA; `Processo_Emissao` novo {aplicativo_contribuinte, aplicativo_sebrae, aplicativo_fisco, paa}; certificado não exigido em `nota_fiscal_facil` | **Sim.** A NT 2026.004 elimina EPEC e FS-DA no CT-e; NFF e PAA mudam quem assina. O ERP guarda o que aconteceu, sem implementar a assinatura de terceiro |
| D-N70 | Regras que dependem de data, prazo, limite ou lista em `Cad_Dfe_Parametro_Regra`, com vigência, em vez de campos em `Cad_Dfe_Leiaute` ou código fixo: os 35 parâmetros das seções 4 e 6, inclusive as datas da NT 2026.004, as alíquotas de transição, a lista ZFM e ALC e os conflitos Q-5 e Q-6 como parâmetro "a confirmar"? Proponho também mover para lá os parâmetros que os documentos 34 e 41 puseram em `Cad_Dfe_Leiaute` (data do IBS/CBS da NFS-e, compartilhamento ME/EPP) | **Sim** para os 35. Mover os dos documentos 34 e 41 é opcional e só vale se você quiser um lugar único; sem mover, os dois convivem sem conflito. **Esclarecido pela D-N95 (11/10/2026):** as datas dos documentos 34 e 41 passam para `Cad_Dfe_Parametro_Regra`; as alíquotas e o cronograma (CTE-IBS-UF-ALIQUOTA, CTE-IBS-MUN-ALIQUOTA, CTE-CBS-ALIQUOTA) ficam em `Cad_Aliquota` e `Cad_Cronograma_Transicao_Tributaria`, e a regra só aponta para eles |
| D-N71 | Crédito presumido do tomador (evento 211110): o ERP emite o evento quando a Mlegate for tomadora de TAC ou MEI; catálogo `Cad_Credito_Presumido_Ibs_Cbs`; crédito escriturado em `Mov_Credito_Fiscal` com Origem `evento_dfe`. Você já respondeu "tudo, inclusive emissão de eventos de terceiros pelo ERP" (D-N16, D-N18 e D-N23, ainda não consolidadas) | **Sim.** Com o catálogo carregado pela planilha cCredPres, o ERP valida localmente as rejeições 1061 a 1071; sem ele, o evento sai e a SVRS devolve a rejeição. Se preferir não mexer em `Mov_Credito_Fiscal`, registrar como `cadastro_manual` |
| D-N72 | Reaproveitar a classificação da NFCom e da NFS-e para ICMS, IBS/CBS, CST, cClassTrib, pagamento vinculado, doação e crédito presumido, com três ajustes: `Mov_Apuracao_Tributo_Item.ID_Estado_Devedor`, `Cad_CFOP.Indicador_Cte` e `tpPagAnt` em `Mov_Cte.Tipo_Pagamento_Antecipado`? | **Sim.** No CT-e, 440 linhas já estão cobertas e 224 são propostas dos documentos 33 e 34; só os três ajustes são de fato novos |

**Posso consolidar?**
