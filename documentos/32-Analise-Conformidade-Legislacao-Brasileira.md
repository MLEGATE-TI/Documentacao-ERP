# Análise de Conformidade com a Legislação Brasileira — Documento 32

*Confronto do dicionário de dados (Fase 0 revisão 50, Folha & RH 20, Contabilidade & Fiscal 21, CRM & Vendas 16, Compras 20, Produção 14, Portal do Cliente 3) com as obrigações fiscais, contábeis, previdenciárias e trabalhistas brasileiras, em 04/10/2026. Não altera o dicionário. Documento de análise para decisão de Alberto.*

Mlegate · Alberto Beyeler · Outubro de 2026

*Atualização de 04/10/2026: as três perguntas da seção 8 foram respondidas por Alberto (Simples Nacional entra no escopo; a emissão será do próprio ERP, em módulo independente; clientes com ICMS, IPI, ICMS-ST e imóveis). O desenho resultante está no documento 33.*

# 1. Resumo

A pergunta foi se o sistema atende SPED, Reinf e eSocial, se falta algo, se atende Lucro Real, Lucro Presumido, Simples Nacional e ME, e como está a emissão de nota pelo sistema nacional (NF-e para produtos, NFS-e Nacional para serviços). A resposta curta é esta.

**O que está forte.** EFD-Reinf (36 entidades, os 23 eventos do leiaute 2.1.2b), eSocial (módulo Folha & RH com 105 entidades, alinhado à NT S-1.3 de julho/2026), DCTFWeb e MIT, extinção da DIRF (coberta por S-1210/S-2501 e R-4010/R-4020), IRPJ/CSLL com LALUR parte A e B, presunção e arbitramento (Lucro Real, Lucro Presumido e Arbitrado), PIS/COFINS cumulativo e não-cumulativo, ECD (plano referencial, Bloco J, signatários, NIRE), identificação da ECF (sócios, Y600, retenções) e toda a camada de IBS/CBS da reforma tributária (cronograma, CST, cClassTrib, DeRE, regime unificado ou híbrido, ZFM, split payment). A tributação **por item de nota** é rica: CST, cClassTrib, NCM, NBS, CEST, GTIN, benefício fiscal (cBenef), código de tributação nacional do serviço (cTribNac) e local de incidência do ISS e do IBS.

**O que falta, em ordem de importância.**

1. **O ciclo de emissão e recepção dos documentos fiscais eletrônicos.** O dicionário guarda muito bem *o que a nota diz* (tributos, itens, chave, protocolo), mas não tem as estruturas de *como a nota nasce e vive*: série e numeração, ambiente, tipo de emissão e contingência, lote e recibo, eventos (cancelamento, carta de correção, inutilização, manifestação do destinatário, eventos do IBS/CBS), XML autorizado, DPS da NFS-e Nacional. A nota tem só dois status (emitida, cancelada). Esse é o ponto mais sensível, porque os prazos de IBS/CBS no documento fiscal já estão correndo (seção 6).
2. **Grupos obrigatórios da NF-e que não aparecem no cabeçalho:** documentos referenciados (devolução, complementar, ajuste), pagamento (detPag), intermediador, informações complementares, importação e exportação, responsável técnico.
3. **SPED Fiscal (EFD ICMS/IPI):** os documentos (Bloco C) e o perfil estão bem cobertos, mas não há apuração periódica do ICMS/IPI (Bloco E), códigos de ajuste e obrigações a recolher, nem CIAP (Bloco G).
4. **Simples Nacional, ME e MEI como regime da própria empresa.** O sistema reconhece o regime do *parceiro* (cliente ou fornecedor optante) e o CSOSN, mas a apuração do DAS, o PGDAS-D, o Fator R, os Anexos I a V e a DEFIS estão **fora de escopo por decisão registrada** (documento 10, seção 7). Não há atributo de porte (ME, EPP, demais). Isso depende de uma resposta sua (seção 8).
5. **Pontos de menor urgência:** escrituração periódica do IBS/CBS (leiaute oficial ainda não fechado), registros consolidados da EFD-Contribuições e de PIS/COFINS sobre o ativo, blocos X, Y e W da ECF, controle de arquivo e recibo das escriturações SPED, subvenções para investimento (Lei 14.789/2023) e DIMOB.

**Uma ressalva de leitura.** O dicionário é um modelo de dados. A *geração* dos arquivos (SPED, Reinf, eSocial) e a *comunicação* com a Receita, as SEFAZ e as prefeituras são camadas de aplicação, que a decisão de projeto manda tratar como framework/plugin (documento 14, seção 21). Por isso a análise separa duas perguntas: o dado necessário existe? E a estrutura que registra o que foi transmitido e o que voltou existe? Para Reinf, eSocial, DCTFWeb e MIT a resposta é sim para as duas. Para NF-e, NFS-e e SPED Fiscal/Contribuições/ECD/ECF, só para a primeira, em graus diferentes.

# 2. Escopo, método e ressalvas

O método foi: (1) levantar a legislação e os cronogramas vigentes em 04/10/2026; (2) pesquisar no modelo normalizado (539 entidades, 4.963 campos) e nos 30 documentos Markdown, entidade por entidade e termo por termo; (3) classificar cada obrigação em Coberto, Parcial, Lacuna, Fora de escopo ou Plugin; (4) priorizar. A ausência de uma lacuna foi **verificada** (busca por nome de campo e por termo nos documentos), não presumida.

Estas classificações significam: **Coberto** — o dado e a estrutura de registro existem. **Parcial** — existe parte; a seção diz o que falta. **Lacuna** — não há estrutura no dicionário. **Fora de escopo** — decisão registrada de não modelar. **Plugin** — a obrigação é comunicação ou geração de arquivo, que a arquitetura entrega ao framework, sem tabelas próprias no núcleo.

Quatro ressalvas. Primeira: este documento não é parecer jurídico nem contábil; as conclusões devem ser confirmadas com a contabilidade e o jurídico da Mlegate. Segunda: parte dos prazos vem de fontes secundárias (portais de notícia e de software house), porque a consulta aos portais oficiais (Portal Nacional da NF-e, SPED, CGSN) não foi possível nesta pesquisa (parte das páginas recusou a leitura automática e as consultas que pediam aprovação de acesso não foram aprovadas a tempo); as datas estão marcadas na seção 6 com o grau de confirmação. Terceira: onde o leiaute oficial (XSD, manual) não foi lido campo a campo, a seção diz "a conferir"; não afirmo que um campo falta sem ter verificado a sua ausência no dicionário. Quarta: as lacunas de segmento (NFC-e, MDF-e, DIMOB e outras) dependem do que a Mlegate e seus clientes operam; marquei como condicionais.

# 3. Matriz — emissão e recepção de documentos fiscais eletrônicos

| Obrigação | Situação | O que o dicionário tem | O que falta |
|---|---|---|---|
| NF-e (modelo 55), dados fiscais do item | Coberto | Mov_Nota_Fiscal_Saida_Item: CFOP, CST, cClassTrib, NCM, CEST, Ex-TIPI, GTIN, NBS, cBenef, SUFRAMA, origem, desconto/frete/seguro/outras; tributos por item em Mov_Apuracao_Tributo_Item (ICMS, ST, DIFAL, FCP, IPI, PIS/COFINS, IBS, CBS, IS) | Conferir campo a campo contra as NTs 2025.002 v1.52, 2026.002, 2026.007, 2026.008 e 2026.010 (valores líquidos de IBS/CBS, crédito presumido, ZFM) |
| NF-e, cabeçalho | Parcial | Chave (44), número, série, modelo, situação, finalidade, natureza da operação, consumidor final, presença, modalidade do frete, protocolo e data/hora de autorização | Tipo de operação (entrada ou saída), documentos referenciados (obrigatório em devolução, complementar e ajuste), pagamento (detPag), intermediador, informações complementares e ao fisco, locais de retirada e entrega, importação (DI/DUIMP, adições), exportação (UF e local de embarque), responsável técnico, autorizados a baixar o XML |
| Ciclo de vida da nota | **Lacuna** | Status {emitida, cancelada} na saída; Cad_Documento_Complemento com tipo {cancelamento, evento_adicional} (só GED) | Estados (digitação, assinada, transmitida, autorizada, rejeitada, denegada), cancelamento com justificativa e protocolo, carta de correção, inutilização de faixa, contingência, eventos do IBS/CBS (ex.: crédito presumido, ator interessado), um registro por evento com sequência, protocolo e XML |
| Série e numeração | **Lacuna** | Número e série no cabeçalho | Cadastro de séries por filial, modelo e ambiente com próximo número; controle de saltos e inutilização |
| Ambiente e tipo de emissão | **Lacuna** | Cad_Certificado_Digital (A1/A3, validade, guarda); Mov_Reinf_Lote tem Ambiente | Ambiente (produção ou homologação), tipo de emissão (normal, contingência SVC/offline), versão do leiaute, CSC e identificador do CSC (NFC-e) |
| XML e DANFE | Parcial | Cad_Documento e Cad_Documento_Vinculo (GED com retenção legal) | Vínculo explícito do XML autorizado e do XML de retorno à nota, com hash e prazo de guarda; geração do DANFE é plugin |
| Recepção de NF-e e CT-e (compras) | Parcial | Mov_Nota_Fiscal_Entrada (chave, protocolo, status, motivo de recusa); decisão de entrada sempre ancorada em XML | Distribuição DF-e por NSU, manifestação do destinatário (ciência, confirmação, desconhecimento, não realizada) e seu evento; campos do CT-e (modal, origem e destino, tomador) para o Bloco D |
| NFS-e Nacional, dados do serviço | Coberto | cTribNac (ID_Servico_Tributacao), NBS, correlação entre códigos municipal e nacional, local da operação e critério (LC 214/2025), município de incidência do ISS e do IBS, empreendimento | Conferir contra o leiaute nacional vigente (Anexo I e XSD): imunidade, suspensão da exigibilidade, retenção do ISSQN e responsável, benefícios municipais, dedução e redução, obra |
| NFS-e Nacional, ciclo de emissão | **Lacuna** | Mesmo cabeçalho da nota; mesma entidade recebe NF-e, CT-e e NFS-e | DPS (identificador, série e número da DPS, distinto do número da NFS-e), emitente (prestador, tomador ou intermediário), ambiente, integração ao ADN, eventos (cancelamento, substituição, manifestação), nota substituída |
| NFC-e (modelo 65) | Lacuna condicional | Modelo previsto na tabela 4.1.1 | CSC, QR Code, contingência offline, pagamento. Só se a Mlegate ou seus clientes vendem a consumidor presencial |
| CT-e e MDF-e emitidos | Lacuna condicional | Expedição tem Tipo_Execucao_Transporte {veículo próprio, transportadora}; frete é tratado como compra (CT-e recebido) | Emissão de MDF-e para transporte próprio interestadual e de CT-e próprio, se aplicável (confirmar com o fiscal) |
| NFCom, BP-e, NF3e e demais DF-e | Fora do núcleo | Cad_Obrigacao_Acessoria é cadastro aberto | NFCom entra no cronograma de 01/10/2026; só afeta a Mlegate se operar telecomunicações |
| Certificado digital | Coberto | Cad_Certificado_Digital e Cad_Certificado_Digital_Uso, com substituto e aviso de vencimento | Nada a acrescentar no núcleo |

**Leitura.** A decisão de projeto é emitir XML por um framework que fala com a Receita, as SEFAZ e as prefeituras (documento 14, seção 8), mas esse framework **não tem hoje nenhuma entidade de apoio**: não há cadastro de integração por autoridade fiscal, nem fila ou log de transmissão para notas. Reinf e eSocial têm lote, evento, retorno e recibo; NF-e e NFS-e não têm. Recomendo um módulo próprio, "DF-e: Emissão e Recepção", espelhando o padrão de Mov_Reinf_Lote, Mov_Reinf_Evento e Mov_Esocial_Evento (seção 7, G-01 a G-05).

# 4. Matriz — SPED e escriturações

| Obrigação | Situação | O que o dicionário tem | O que falta |
|---|---|---|---|
| EFD ICMS/IPI, Registro 0 e perfil | Coberto | Cad_Filial_Perfil_Fiscal (indicador de atividade, perfil EFD, contribuinte ICMS e IPI, regime de apuração do ICMS); inscrições por UF; Cad_Filial_Regime_Icms; participantes e produtos com tipo de item SPED | Conferir o Guia Prático vigente (versão 3.2.3, fonte secundária) |
| EFD ICMS/IPI, Bloco C (documentos) | Coberto | Notas de entrada e saída com tabela 4.1.1, situação do documento, itens e tributos analíticos por CST, CFOP e alíquota | — |
| EFD ICMS/IPI, Bloco D (transporte) | Parcial | CT-e recebido como compra de frete | Campos do CT-e para D100 e D190 (modal, UF e município de origem e destino) |
| EFD ICMS/IPI, Bloco E (apuração) | **Lacuna** | Tributo por item (Mov_Apuracao_Tributo_Item); DIFAL e FCP no item; Cad_Beneficio_Fiscal_Icms | Apuração **periódica** do ICMS, ICMS-ST por UF, DIFAL/FCP e IPI: débitos, créditos, estornos, saldo credor transportado, ajustes com código (tabela 5.1.1) e obrigações a recolher (tabela 5.4) |
| EFD ICMS/IPI, Bloco G (CIAP) | **Lacuna** | Cad_Ativo_Imobilizado e depreciação | Controle do crédito de ICMS sobre o ativo permanente (parcelas, fator de apropriação, saídas tributadas sobre saídas totais) |
| EFD ICMS/IPI, Bloco H (inventário) | Parcial | Mov_Saldo_Estoque_Valor (alimenta H e K), Mov_Inventario, propriedade da mercadoria (próprio ou em poder de terceiros) | Motivo do inventário (H005) e informações de tributação do item inventariado (H020) |
| EFD ICMS/IPI, Bloco K (produção) | Parcial | Ordem de produção, consumo e apontamentos; saldo de estoque | Conferir K200, K220, K230/K235, K250/K255 e a correção de apontamento (K270, K275) contra o módulo de Produção |
| EFD-Contribuições, tabelas e itens | Coberto | Natureza da receita, CST, tipo e base de crédito, retenções (F600 via Mov_Titulo_Retencao) | — |
| EFD-Contribuições, consolidação | Parcial | Apuração por item; crédito fiscal e sua aplicação (Mov_Credito_Fiscal) | Registros consolidados do período (M100, M200, M500, M600), ajustes, e PIS/COFINS sobre depreciação e aquisição de bens (F100, F120, F130). Válida até 31/12/2026 e depois mantida só para controle de créditos (NT 011/2026, fonte secundária) |
| Escrituração digital do IBS/CBS | Parcial | Cad_Obrigacao_Acessoria já prevê ESCRITURACAO_IBS_CBS (vigência 2026); tributo por item; Mov_Credito_Fiscal; DeRE; split payment | Apuração periódica consolidada (débitos, créditos, ajustes, saldo, recolhimento) e o leiaute oficial, que ainda não foi fechado. Fica em monitoramento |
| ECD | Coberto | Plano referencial, Bloco J (J100, J150), I051, I050, signatários, NIRE, mapeamento conta–bloco, lançamentos | Registro de arquivo gerado, recibo e retificação (G-11) |
| ECF, núcleo | Coberto | IRPJ/CSLL, LALUR parte A e B (Mov_Lalur_*), presunção, retenções como antecipação, quadro societário e Y600 | — |
| ECF, blocos X, Y (exceto Y600) e W | Lacuna a conferir | Y600 existe | Informações econômicas e participações no exterior (X), outras informações (Y) e país a país (W), conforme o perfil da empresa. Leiaute 12.1.0 (fonte secundária) |
| Arquivo, recibo e retificação das escriturações | **Lacuna** | Reinf (Mov_Reinf_Lote), DCTFWeb (Mov_Dctfweb_Declaracao) e MIT (Mov_Mit_Apuracao) têm | Estrutura equivalente para EFD ICMS/IPI, EFD-Contribuições, ECD e ECF: período, versão, hash, retificadora, recibo, resultado do validador |

# 5. Matriz — Reinf, DCTFWeb, eSocial, regimes e demais obrigações

| Obrigação | Situação | O que o dicionário tem | Observação |
|---|---|---|---|
| EFD-Reinf | Coberto | 36 entidades: os 23 eventos do leiaute 2.1.2b (séries R-1000, R-2000, R-4000 e R-9000), lote, retorno, ocorrências, fechamento, espetáculos, CPRB, plano de saúde, rendimentos | Alinhado ao XSD v2.1.2 de 23/09/2026 e ao pacote do CNPJ alfanumérico (documento 24) |
| DCTFWeb e MIT | Coberto | 7 entidades de DCTFWeb (declaração, débito, quota, vinculação, DARF) e 5 de MIT; SISTAD; PER/DCOMP | A DCTF mensal foi substituída pela DCTFWeb/MIT |
| DIRF | Encerrada | Substituída por S-1210/S-2501 (eSocial) e R-4010/R-4020/R-4099 (Reinf) | Cobertura ok |
| Lei 15.270/2025 (IRRF de 10% sobre dividendos acima de R$ 50 mil por mês) | Coberto | Mov_Distribuicao_Lucro (inclui regime de transição), R-4010, DARF 1841-01/02 | Documento 20 |
| eSocial | Coberto | Folha & RH com 105 entidades; Mov_Esocial_Evento, retorno, mensagens, cadastro do empregador e estabelecimento; S-1.3 | NT S-1.3 de 07/2026, com datas de 26/10/2026, 23/11/2026, 14/12/2026 e 18/01/2027 (fonte secundária, a conferir no portal) |
| Lucro Real | Coberto | Apuração trimestral ou anual por estimativa; LALUR A e B; compensação de prejuízo por tributo (Valor_Compensacao_Prejuizo); PIS/COFINS não-cumulativo com créditos; ECD e ECF | Lacuna periférica: subvenções para investimento (Lei 14.789/2023) |
| Lucro Presumido | Coberto | Cad_Percentual_Presuncao e acréscimos, vigência por atividade; PIS/COFINS cumulativo; Cad_Empresa_Perfil_Fiscal.Incidencia_Pis_Cofins {cumulativo, não-cumulativo, ambos} | Presumido com ECF e ECD conforme o caso |
| Lucro Arbitrado | Coberto | Mov_Apuracao_Irpj_Csll.Regime_Aplicado {real, presumido, arbitrado} | — |
| Simples Nacional, ME/EPP, MEI como regime **da empresa** | **Fora de escopo** | Regime_Tributario em Cad_Participante {lucro_real, lucro_presumido, simples_nacional, mei}, com vigência; CSOSN em Cad_Cst; Excesso_Sublimite na filial; ZFM; MIT admite "optante_simples" | Sem DAS, PGDAS-D, RBT12, Anexos I a V, Fator R, partilha, sublimite estadual, DEFIS, DASN-SIMEI e porte (ME, EPP). Ver G-13 e G-14 |
| Simples Nacional como **parceiro** (cliente ou fornecedor optante) | Coberto | Regime IBS/CBS unificado ou híbrido; crédito do adquirente limitado ao valor embutido no DAS do fornecedor; semestres de opção | O documento 10 (seção 7) já registra a regra |
| IBS/CBS, ano de teste de 2026 (CBS 0,9% e IBS 0,1%) | Coberto | Cad_Cronograma_Transicao_Tributaria com percentuais por ano | Atualizar quando houver nova regulamentação |
| DIMOB, DMED | Lacuna condicional | Não há registro | DIMOB aplica-se a quem comercializa, loca ou intermedeia imóveis; há módulo imobiliário no dicionário, então vale confirmar |
| Obrigações estaduais e municipais (GIA, DeSTDA, DIME, declarações do ISS) | Plugin | Cad_Obrigacao_Acessoria aberto, sem entidades de dados | Variam por UF e município; cobrir por linha de cadastro e pelo framework |

# 6. Calendário regulatório relevante (outubro/2026 a março/2027)

As datas abaixo vêm da pesquisa em portais públicos; marquei o grau de confirmação. Onde a fonte oficial não pôde ser lida, está dito.

| Data | Marco | Efeito no sistema | Confirmação |
|---|---|---|---|
| 29/09/2026 (já passou) e 26/10/2026 | eSocial NT S-1.3 de 07/2026, etapas de leiaute | Folha & RH (documento 28) | Fonte secundária (Senior) |
| 01/10/2026 | NFS-e (maioria dos municípios) e NFCom: destaque de IBS/CBS no documento | Itens de nota de serviço e DPS | Fonte secundária (Receita adiou o cronograma, DGABC) |
| 01/11/2026 | NFS-e Nacional obrigatória para ME e EPP do Simples Nacional (CGSN 191/2026 moveu de 01/09) | Emissão de NFS-e pelos optantes | **Oficial** (gov.br/Receita) |
| 03/11/2026, 01/12/2026, 14/12/2026 | Etapas das NTs 2026.002, .007, .008 e .010 (NF-e e NFC-e com IBS/CBS) | Cabeçalho e itens da NF-e | Fonte secundária (a conferir no Portal Nacional da NF-e) |
| 15/11/2026 | Eventos da DeRE | Eventos de documento (G-01) | Fonte secundária |
| 01/12/2026 | Plataformas e demais marcos do cronograma | Eventos de documento | Fonte secundária |
| 31/12/2026 | Fim da EFD-Contribuições como escrituração de apuração; permanece para controle de créditos | Consolidação PIS/COFINS | Fonte secundária (reformatributaria.com) |
| 01/01/2027 | Destaque obrigatório para optantes do Simples e importações; PGDAS-D absorve a DEFIS | Simples (se no escopo) | Fonte secundária |
| 18/01/2027 e 01/03/2027 | Última etapa do eSocial S-1.3; vigência de NT 2026.x de NF-e | Folha & RH, NF-e | Fonte secundária |

# 7. Lacunas priorizadas e ação recomendada

Cada lacuna é uma **proposta**: nada disto altera o dicionário sem o seu "consolidar", e as estruturas novas seguem as convenções da Fase 0 (prefixos Cad_ e Mov_, ID_, vigência, enumeração fechada pequena inline, referência genérica quando preciso). A prioridade considera prazo legal e dependência.

| Código | Lacuna | Prioridade | Ação recomendada | Depende de |
|---|---|---|---|---|
| G-01 | Ciclo de vida e eventos de DF-e (cancelamento, CC-e, inutilização, manifestação, eventos IBS/CBS), XML autorizado, lote e recibo | **Alta** (prazos 01/10 a 14/12/2026) | Novo módulo "DF-e": Mov_Documento_Fiscal_Transmissao, Mov_Documento_Fiscal_Evento e vínculo do XML ao GED, no padrão do Reinf e do eSocial | Decisão de escopo (seção 8, pergunta 2) |
| G-02 | Série, numeração, ambiente, tipo de emissão e contingência | **Alta** | Cad_Serie_Documento_Fiscal (filial, modelo, série, ambiente, próximo número, vigência) e campos de ambiente e tipo de emissão na transmissão | G-01 |
| G-03 | Grupos obrigatórios da NF-e ausentes: referenciados, pagamento, intermediador, informações complementares, importação e exportação, responsável técnico | **Alta** | Conferir contra o XSD e criar Mov_Documento_Fiscal_Referenciado, _Pagamento e campos de intermediador e informações adicionais | Leitura do XSD vigente |
| G-04 | NFS-e Nacional: DPS, emitente, ADN, eventos, substituição | **Alta** (01/11/2026 para ME/EPP; municípios já aderidos) | Mov_Nfse_Dps e eventos próprios; conferir o Anexo I do leiaute nacional | G-01 |
| G-05 | Cadastro de integração por autoridade fiscal (SEFAZ, ADN, prefeitura, versão de leiaute, endpoints por ambiente) | Alta | Cad_Integracao_Autoridade_Fiscal, materializando o princípio framework/plugin do documento 14 | G-01 |
| G-06 | Apuração periódica do ICMS, ICMS-ST e IPI (Bloco E), com ajustes (5.1.1) e obrigações a recolher (5.4) | **Alta** se a Mlegate for contribuinte de ICMS ou IPI | Mov_Apuracao_Icms_Periodo e correlatas, alimentadas por Mov_Apuracao_Tributo_Item | Perfil fiscal da Mlegate |
| G-07 | CIAP (Bloco G) | Média | Entidades de controle do crédito de ICMS sobre ativo, ligadas a Cad_Ativo_Imobilizado | G-06 |
| G-08 | Blocos H e K: motivo do inventário, informações de tributação, correção de apontamento | Média | Campos adicionais em Mov_Inventario e conferência de Produção contra K200 a K275 | — |
| G-09 | EFD-Contribuições consolidada e PIS/COFINS sobre o ativo | Média (válida até 31/12/2026) | Decidir se vale o esforço antes do fim da escrituração; manter só o controle de créditos depois | — |
| G-10 | Escrituração periódica do IBS/CBS | Média, **monitorar** | Aguardar o leiaute oficial; reservar Cad_Obrigacao_Acessoria e o nome do módulo | Publicação do leiaute |
| G-11 | Arquivo, recibo e retificação das escriturações SPED (EFD, ECD, ECF); blocos X, Y e W da ECF | Média | Mov_Escrituracao_Arquivo (genérico, com referência ao tipo de obrigação) e conferência do perfil de ECF | — |
| G-12 | Subvenções para investimento (Lei 14.789/2023) e seu efeito no LALUR e na ECF | Média (Lucro Real) | Confirmar aplicabilidade e modelar o crédito fiscal | Contabilidade |
| G-13 | Simples Nacional, ME e MEI como regime da própria empresa (DAS, PGDAS-D, RBT12, Anexos, Fator R, DEFIS, DASN-SIMEI) | Definir | Só modelar se você disser que há empresa optante no escopo | Seção 8, pergunta 1 |
| G-14 | Atributo de porte (ME, EPP, demais) e enquadramento de MEI | Baixa a média | Campo com vigência em Cad_Participante ou entidade própria | G-13 |
| G-15 | DIMOB e DMED | Baixa, condicional | Confirmar se a Mlegate ou seus clientes têm operação imobiliária que obrigue | Contabilidade |
| G-16 | NFC-e, MDF-e e CT-e emitidos | Condicional | Incluir no módulo DF-e só se houver operação de varejo presencial ou transporte próprio interestadual | Seção 8 |

# 8. Perguntas de escopo para Alberto

1. **Simples Nacional, ME e MEI.** A Mlegate, ou algum cliente do ERP multi-empresa, é optante do Simples Nacional, ME, EPP ou MEI? Se sim, o sistema precisa apurar o DAS e gerar o PGDAS-D (G-13), e o porte vira atributo (G-14). Se não, o que está hoje (reconhecer o optante como parceiro) basta.
2. **Quem emite a nota.** A emissão de NF-e e NFS-e será feita pelo próprio ERP (framework próprio falando com a SEFAZ e com o ADN) ou por um provedor externo plugado? A resposta decide se o módulo "DF-e" guarda o ciclo completo (eventos, XML, lote) ou só o retorno do provedor.
3. **Perfil fiscal.** A Mlegate é contribuinte de ICMS e IPI, tem ativo permanente com crédito de ICMS, ou opera imóveis? Isso decide a prioridade de G-06, G-07 e G-15.

# 9. Fontes e como foi verificado

**Dicionário.** Confronto direto contra o modelo normalizado (539 entidades, 4.963 campos) e os documentos 00, 00b, 01 a 15 e 20 a 31: listagem de entidades fiscais, campos de Mov_Nota_Fiscal_Saida, _Saida_Item e _Entrada, Cad_Certificado_Digital, Mov_Reinf_Lote, Mov_Esocial_Evento, Mov_Dctfweb_Declaracao, Mov_Mit_Apuracao, Cad_Filial_Perfil_Fiscal, Cad_Empresa_Perfil_Fiscal, Cad_Participante e Cad_Ativo_Imobilizado; busca por termos (DPS, ADN, inutilização, cancelamento, referenciado, detPag, intermediador, DANFE, tpEmis, CIAP, Bloco K, porte, DIMOB, subvenção, NSU) com o resultado documentado.

**Legislação e cronogramas (pesquisados em 04/10/2026).** Fonte oficial confirmada: Receita Federal, *Simples Nacional: NFS-e Nacional será obrigatória para ME e EPP a partir de 1º de novembro de 2026* (CGSN 191/2026). Fontes secundárias: portais de informação fiscal e contábil e de software house (Senior, Contábeis, Reformatributaria, DGABC, Tecnospeed, IOB e outros), citados na mensagem de entrega. Os portais oficiais do SPED, do Portal Nacional da NF-e e do CGSN não puderam ser consultados (recusa de leitura automática ou falta de aprovação de acesso); as datas e versões de leiaute que dependem deles estão marcadas "fonte secundária" e devem ser conferidas por quem opera a obrigação.

**O que não foi feito.** Não li os XSD e manuais oficiais campo a campo; as lacunas G-03, G-04 e G-08 incluem essa conferência como primeiro passo. Não validei a aplicabilidade das obrigações condicionais ao negócio da Mlegate (G-12, G-15, G-16).
