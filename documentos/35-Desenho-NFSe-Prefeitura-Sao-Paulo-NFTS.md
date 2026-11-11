# Desenho da NFS-e da Prefeitura de São Paulo (RPS, NFTS e guia de ISS) — Documento 35

*Análise dos arquivos oficiais da Prefeitura de São Paulo que Alberto enviou (Web Service da NFS-e v3.3.9, Web Service da NFTS v3.1, manuais do prestador pessoa jurídica v6.2 e pessoa física v5.1 e a planilha do novo layout) contra o dicionário. Propostas de ajuste, nada consolidado: o dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

O sistema paulistano de NFS-e é um canal à parte da NFS-e Nacional: tem Web Service próprio (SOAP), numeração por RPS, regras de ISS do município de São Paulo e uma nota que não existe no padrão nacional, a **NFTS** (nota emitida pelo tomador ou pelo intermediário). A decisão D-N2 manteve os "demais contribuintes" nesse sistema, então o ERP precisa falar com os dois canais.

Conferi **121 grupos de campos** do leiaute v3.3.9 (versão 1, com ISS, e versão 2, com IBS/CBS) contra o dicionário e o documento 33: 39 já cobertos, 39 cobertos pelas entidades novas do documento 33, 8 derivados, 6 só no XML, **22 lacunas** e 7 a confirmar. As lacunas são poucas e concentradas: carga tributária, valor total recebido, retenção de PIS, COFINS e CSLL, obra (CEI, matrícula e encapsulamento), multa e juros, guia de ISS, crédito do tomador, opção do Simples, indicador de operação e o catálogo de serviços do município. Os 253 códigos de erro e 22 de alerta do manual dão a carga inicial de `Cad_Dfe_Codigo_Retorno`.

**Quatro avisos.**

Primeiro: **os manuais paulistanos não citam a migração**, mas a fonte oficial confirma as datas. O PJ v6.2 e o PF v5.1 não mencionam emissor nacional, ADN ou DPS e ainda descrevem o autônomo e o Simples emitindo no sistema paulistano. A página da Secretaria Municipal da Fazenda de 13/08/2026 ("Uso do Emissor Nacional da NFS-e") diz que o Emissor Nacional é obrigatório para **profissionais liberais e autônomos desde 03/08/2026** e para **empresas do Simples Nacional desde 01/11/2026** (data adiada de 01/09/2026 pela Resolução CGSN nº 191, de 04/08/2026; base: Resolução CGSN nº 189, de 23/04/2026), inclusive com opção pendente, em discussão administrativa ou sob impedimento. Depois dessas datas o sistema paulistano serve **só para consulta e emissão retroativa**. A página não trata de RPS, NFTS, ISS retido, guia ou DAMSP, e uma notícia anterior da mesma Prefeitura (19/05/2026) ainda trazia 01/08 e 01/09: vale a página de agosto. A única migração que os manuais descrevem é a do **MEI**, vedado no sistema paulistano desde **01/09/2023** (só emite NFS-e Padrão Nacional quando o tomador tem CNPJ). Falta o texto da Resolução CGSN nº 189 e o da nº 191 (o DOU e o LegisWeb não abriram para mim).

Segundo: como a Mlegate é tomadora com CNPJ, **ela já recebe NFS-e Nacional de MEI hoje**, e não só a partir de 2027 como o documento 33 sugere. Isso antecipa a recepção pelo ADN.

Terceiro: o documento 33 deixou a **NFTS fora do desenho** (§9). É lacuna real para Compras: quando o prestador não emite nota e o serviço é tributado em São Paulo, quem emite é a Mlegate, e o ISS retido entra na guia mensal.

Quarto: a **versão 2 (IBS/CBS) do sistema paulistano ainda é restrita**. Só vale para serviços com fato gerador a partir de 01/01/2026, não é permitida para o Simples até 31/12/2026, e na NFTS só se aplica à tributação W (importação de serviço). O manual do Web Service informa que o ambiente do layout 2 estava com **apenas o serviço de teste** disponível (atualização de 13/11/2025). Desenhei para os dois layouts, mas o layout 2 depende de nova leitura quando a Prefeitura o liberar.

# 2. Fontes lidas

| Fonte | Versão | Uso |
|---|---|---|
| Manual de utilização do Web Service da NFS-e | 3.3.9 | Operações, leiaute v1 e v2, erros e alertas, assinatura, endereços |
| Planilha auxiliar de campos do novo layout | atual | Campos calculados pelo sistema e obrigatoriedade (divergências com o manual anotadas) |
| Manual do Web Service da NFTS | 3.1 (dez/2025) | Operações e campos da NFTS |
| Manual do prestador pessoa jurídica | 6.2 | Regras de ISS, tributação, retenção, aceite, guia, cancelamento e substituição |
| Manual do prestador pessoa física (autônomo) | 5.1 | Regras do autônomo, isento de ISS |
| Não usados | | Partes de parcelamento (PJ pp. 173–193), créditos IPTU (PJ pp. 141–155, só varrido) e aplicativo móvel (PJ pp. 216–221) |

# 3. Arquitetura do canal paulistano

**Dois serviços SOAP.** `LoteNFe` (síncrono: um método por operação; pedido e retorno na mesma conexão) e `LoteNFeAsync` (assíncrono: o envio devolve um **protocolo GUID de 32 caracteres** e o resultado vem por consulta). Os dois exigem **TLS 1.2 com autenticação mútua** por certificado digital ICP-Brasil com CNPJ (versões antigas de TLS foram desativadas), SOAP 1.2 e mensagem de pedido com no máximo **500 KB**. A assinatura é por RPS (e separada no cancelamento). O endereço antigo do serviço síncrono não comporta a versão 2 e será desativado; o novo (`nfews.prefeitura.sp.gov.br`) comporta as versões 1 e 2, e o assíncrono também.

**Operações síncronas:** envio de RPS, envio de lote de RPS, teste de envio de lote, consulta de NFS-e, consulta de NFS-e recebidas, consulta de NFS-e emitidas, consulta de lote, consulta de informações do lote, cancelamento e consulta de CNPJ. **Assíncronas:** envio de lote, consulta de situação do lote, teste de envio de lote, emissão de guia, consulta de situação da guia e consulta da guia.

**Diferenças em relação aos outros canais do framework de envio:**

1. **Não há NSU.** A consulta de notas recebidas e emitidas é por período e página, não por último NSU. `Mov_Dfe_Distribuicao` ganha um modo "período e página" (sem Maior_Nsu e sem Proxima_Consulta_Permitida).
2. **Lote com opção atômica** (`transacao`): verdadeiro, nenhum RPS vira NFS-e se houver erro; falso, aceita parcial. Vira o campo Transacao_Atomica em `Mov_Dfe_Transmissao`, junto com Periodo_Inicio e Periodo_Fim (o lote tem período de emissão, de no máximo 31 dias nas consultas).
3. **Alertas**: o retorno traz erros e **alertas** (que não rejeitam). `Cad_Dfe_Codigo_Retorno` ganha a natureza "alerta" e a identidade passa a incluir a autoridade e a natureza (o mesmo código numérico pode ter sentidos diferentes por autoridade).
4. **Duas versões do leiaute** (1 = ISS; 2 = IBS/CBS) escolhidas por fato gerador: `Cad_Dfe_Leiaute` com duas linhas para a autoridade paulistana.
5. **O papel do certificado**: o remetente do cabeçalho deve coincidir com o CNPJ do certificado (já coberto por `Mov_Dfe_Transmissao.ID_Certificado`).

# 4. Cobertura do leiaute v3.3.9

Legenda como no documento 34. Aqui a unidade é o grupo de campos (uma linha do leiaute pode reunir vários campos).

| Grupo do leiaute | Grupos de campos | Coberto | Entidade nova | Derivado | Só no XML | Lacuna | Confirmar |
|---|---:|---:|---:|---:|---:|---:|---:|
| Cabeçalho e mensagem (todas as operações) | 14 | 1 | 7 | 2 | 1 | 3 | 0 |
| RPS (pedido), campos da v1 mantidos na v2 | 39 | 18 | 9 | 1 | 0 | 9 | 2 |
| RPS, complemento da versão 2 (Reforma Tributária) | 12 | 5 | 3 | 0 | 1 | 2 | 1 |
| IBS/CBS declarado pelo emitente (v2) | 15 | 4 | 7 | 1 | 0 | 2 | 1 |
| NFS-e emitida (retorno), campos da v1 | 15 | 5 | 3 | 0 | 2 | 3 | 2 |
| NFS-e emitida (retorno), complemento v2 calculado pela Prefeitura | 9 | 4 | 1 | 2 | 2 | 0 | 0 |
| Campos só da planilha (o sistema calcula; não estão no manual 3.3.9) | 9 | 2 | 5 | 2 | 0 | 0 | 0 |
| Cancelamento, consultas, CNPJ e guia | 6 | 0 | 3 | 0 | 0 | 3 | 0 |
| Autoridade e roteamento | 2 | 0 | 1 | 0 | 0 | 0 | 1 |
| **Total** | **121** | **39** | **39** | **8** | **6** | **22** | **7** |

As lacunas (em campos novos de `Mov_Nfse_Rps`, salvo indicação):

| Lacuna | Proposta |
|---|---|
| Carga tributária (valor, percentual e fonte) | Valor_Carga_Tributaria, Percentual_Carga_Tributaria e Fonte_Carga_Tributaria |
| Valor total recebido (só subitens 10.08, 33.01 e 17.11) | Valor_Total_Recebido |
| Retenção de PIS, COFINS e CSLL (`tpRetencaoPisCofins`, erros 644 a 646) | ID_Retencao_Pis_Cofins_Csll (domínio novo), derivável de `Mov_Titulo_Retencao` quando o ERP calcula a retenção antes |
| Obra: CEI, matrícula e número de encapsulamento (erros 296, 374 a 390, 1229, 1234) | **`Cad_Local_Operacao`** ganha Codigo_Cei e Matricula_Obra_Municipal (a revisão 2 do documento 34 já usa o local de operação para a obra); Numero_Encapsulamento fica em `Mov_Nfse_Rps` |
| Multa e juros cobrados | Valor_Multa e Valor_Juros_Cobrado (o nome Valor_Juros já existe em `Mov_Dctfweb_Darf`) |
| Opção do Simples (5 códigos, só 0 e 4 vivos) | ID_Opcao_Simples_Sp (domínio novo); o domínio do documento 33 (não optante, MEI, ME/EPP) continua e este fica derivado |
| Guia: número e data de quitação (o cancelamento só é possível se a nota não estiver paga nem em guia) | Numero_Guia_Iss e Data_Quitacao_Guia |
| Crédito do tomador (alerta 337: CPF inválido, sem crédito) | Valor_Credito_Tomador |
| Data do fato gerador (define v1 ou v2; para RPS convertido é a data do RPS) | Data_Fato_Gerador |
| Indicador de operação (`cIndOp`) e indicador de destinatário (`indDest`) | Os mesmos campos da NFS-e Nacional (documento 34, P-8 e P-19): ID_Indicador_Operacao no item e Indicador_Destinatario na nota |
| Código de serviço com regras (retenção, tributação fora de SP, obra, imunidade, evento) | **`Cad_Servico_Municipal`** (item 6) |
| Identificador nacional devolvido pela Prefeitura (v2) | Renomear Id_Nacional_Adn para **Chave_Nota_Nacional**: na NFS-e paulistana quem devolve a chave é a Prefeitura, não o ADN |
| Consulta de CNPJ (descobrir o CCM do tomador, erros 219 e 220) | Sem entidade de retorno; resultado preenche `Cad_Participante_Documento_Fiscal` |

Pontos a confirmar: o campo `ValorCSLL` tem descrição ambígua (erros 644 e 645 o ligam à retenção de PIS/COFINS); `ValorInicialCobrado` aparece no manual como escolha e na assinatura v2, mas o erro 640 diz que não está mais disponível; `indFinal` tem semântica própria (uso ou consumo pessoal) e pode não ser o mesmo campo "consumidor final" da NF-e; `DataFatoGeradorNFe` não deixa claro se é a data de emissão do RPS ou outra. A planilha ainda marca `PagamentoParceladoAntecipado` como obrigatório, o que diverge do manual: não gravar.

# 5. NFTS

A NFTS é a nota do **tomador** (tipo 1) ou do **intermediário** (tipo 2). Há três hipóteses dadas pelo tipo de documento do prestador: dispensado de documento fiscal, com documento autorizado, ou **sem emissão embora obrigado** (o alerta 418 diz que o ISS deverá ser retido). Na rejeição de uma NFS-e recebida por "erro nas informações" ou por NFTS do mesmo fato gerador, o responsável é levado à emissão da NFTS e o prestador fica impedido de cancelar a nota rejeitada.

**Regras que o ERP precisa conhecer** (códigos de erro do manual): a retenção é do tomador **ou** do intermediário, nunca dos dois (3016, 3111, 2029, 2030); código que não permite retenção pelo intermediário (327); NFTS do intermediário exige CPF ou CNPJ e razão social do tomador (e na NFTS do tomador esse campo não se preenche, erro 1511); MEI não tem ISS retido (419); imunidade não admite retenção (437); autônomo não admite imunidade (438); prestador não pode ser o próprio tomador (431); prestador fora do CPOM implica ISS retido (420 e 473); não cancela NFTS que está em guia (428) nem fora do prazo (324); só cancela NFTS gerada por Web Service (1012).

**Operações** (todas síncronas, lote de 1 a 50): envio de NFTS, envio de lote, teste de envio de lote, consulta de NFTS, consulta de lote, consulta de informações do lote, cancelamento e consulta de emissão (devolve os CCM de um CNPJ e se ele já emite NFS-e). O layout 2 (IBS/CBS) só é obrigatório na tributação W (importação de serviço) a partir de 01/01/2026; as demais tributações usam o layout 1.

**Encaixe em Compras.** A nota de entrada de um prestador que não emite NFS-e dispara a NFTS pela Mlegate: o documento fiscal da NFTS fica com papel "emitido", o ISS retido gera uma retenção do tipo "retido pela Mlegate" e entra na guia mensal (vencimento no dia 10 do mês seguinte; o órgão público informa a data do pagamento efetivo e recolhe até o dia 10 do mês seguinte ao pagamento).

**Entidade nova `Mov_Nfts`** (relação 1:1 com `Mov_Documento_Fiscal`): Tipo_Nfts {tomador, intermediário}, Tipo_Documento_Prestador {dispensado, com documento autorizado, sem documento obrigado}, Numero_Nfts, Codigo_Verificacao, Data_Prestacao, Status {normal, cancelada}, Layout_Versao {1, 2}, ID_Tributacao_Nfts (18 valores), Regime_Tributacao_Prestador {normal ou DAMSP, DAS, MEI}, Iss_Retido_Tomador, Iss_Retido_Intermediario, Descumpre_Aliquota_Minima_Lc157, Data_Pagamento (só órgão público), Discriminacao (até 2.000 caracteres), Codigo_Cno, Matricula_Obra, Chave_Nota_Nacional (v2) e Numero_Lote. O documento do prestador (IM de 8 posições na v1 e 12 na v2, série e número; prestador estrangeiro com NIF na v2) fica em colunas de `Mov_Nfts`, **sem entidade filha**.

# 6. Regras da NFS-e paulistana que mudam o desenho

**Quem emite e como.** Todo prestador com CCM é obrigado a emitir, qualquer que seja a receita; são opcionais o MEI (agora vedado), os profissionais liberais e autônomos, o DIF, o Metrô e uma lista de códigos de diversões públicas. O autônomo é **isento de ISS**: sem valor de ISS, sem retenção, sem crédito, sem guia nem substituição.

**RPS.** Numeração sequencial a partir de 1, série de até 5 caracteres por equipamento, 2 vias. A conversão do RPS em NFS-e deve ocorrer até o 10º dia seguinte (até o dia 5 do mês seguinte à prestação, quando o tomador é o responsável tributário). Perder o prazo equivale a não emitir. Conversão retroativa: 4 anos além do corrente para ISS retido, 5 anos para os demais. `Mov_Nfse_Rps` ganha Situacao_Conversao e os prazos viram parâmetro com vigência.

**Uma nota por código de serviço.** Documento do ERP com vários serviços gera um RPS por código (decisão D-N30).

**Tributação e local de incidência.** Local `sp`, `fora_sp` (só nos códigos permitidos, exige município e alíquota digitada) ou exportação. Natureza: normal, imune, isento (exige GBF prévia), isento parcial (alíquota efetiva mínima de 2%) e suspenso (número do processo na discriminação). **Só a natureza normal com incidência em SP e prestador responsável entra na guia.** Isento, imune, suspenso, fora de SP e exportação não geram guia nem crédito. `Mov_Nfse_Rps` ganha Natureza_Operacao e Local_Incidencia.

**Retenção.** O tomador retém se o serviço é tributado em SP e ele é PJ estabelecido em SP, ou se o serviço é tributado fora e ele é PJ. Não há retenção quando o tomador é pessoa física, e os manuais não definem o caso de tomador PF (pergunta Q-3 abaixo). Para o Simples (DAS) com retenção, a alíquota é digitada.

**Cancelamento e substituição.** Cancelar: até 6 meses da emissão e antes do pagamento do ISS; se já há guia, cancelar a guia primeiro; se há ISS retido, quem cancela a guia é o tomador; não cancela nota aceita pelo responsável, em parcelamento ou com serviço não pago. Substituir: até 6 meses do fato gerador; não pode mudar o CNPJ-raiz do tomador, o regime, o CCM ou a data da prestação; não substitui nota com intermediário, nota em guia não quitada ou nota no layout 2. O ISS pago é aproveitado e a diferença segue a tabela do manual. O modelo paulistano de substituição é **diferente do nacional** (documento 34, P-8): `Mov_Nfse_Rps` ganha ID_Nfse_Substituida e ID_Nfse_Substituta (autorreferência).

**Aceite.** A NFS-e recebida com ISS retido é notificada ao responsável (tomador ou intermediário) pelo DEC, com prazo até o último dia do mês seguinte; sem manifestação vale o **aceite tácito**. Rejeitar tem 5 motivos e abre a emissão da NFTS. Entidade nova **`Mov_Nfse_Aceite`**: Tipo_Responsavel, Data_Ciencia, Data_Limite, Situacao {pendente, expresso, tácito, expresso com parcelamento, rejeitada}, Motivo_Rejeicao, ID_Documento_Fiscal_Nfts e a janela de alteração de 180 dias. Liga ao Contas a Pagar: nota com ISS retido não aceita bloqueia o título.

**Guia de ISS.** Vence no dia 10 do mês seguinte e é emitida pelo sistema da NFS-e, **não pelo DAMSP**. Exceções: SUP (sociedade uniprofissional, ISS fixo trimestral, sem retenção e sem crédito), Simples pelo DAS (serviços prestados), DIF, SDPE (diversões públicas) e órgãos públicos. A guia reúne NFS-e emitida, NFS-e recebida com retenção, NFS-e rejeitada e NFTS. Entidades novas **`Mov_Iss_Guia`** (CCM, competência, vencimento, principal, multa, juros, correção, status) e **`Mov_Iss_Guia_Item`** (documento e tipo: NFS-e emitida, NFS-e recebida retida, NFS-e rejeitada, NFTS). A alternativa é especializar `Mov_Apuracao_Obrigacao_Recolher` do documento 33 (decisão D-N27).

**Simples e MEI.** ME e EPP recolhem pelo DAS ou pelo DAMSP (art. 20, §1º, da LC 123); o domínio de perfil do contribuinte em `Cad_Autoridade_Fiscal_Atendimento` ganha sociedade_uniprofissional, simples_damsp e entidade_imune. **Roteamento da D-N2:** a fonte oficial dá um critério por perfil: autônomo (desde 03/08/2026) e optante do Simples (desde 01/11/2026, inclusive com opção pendente ou sob impedimento) emitem pelo Emissor Nacional; o sistema paulistano fica só para consulta e emissão retroativa. Os demais contribuintes seguem no sistema paulistano, como você decidiu. Como o Emissor Nacional também tem o cadastro nacional de contribuintes (CNC), o ERP deve guardar a data de início por contribuinte e deixar o cadastro prevalecer sobre o perfil se divergirem (decisão D-N25). A Resolução CGSN nº 189 veda à ME e à EPP emitir NFS-e em operação sujeita só ao ICMS (segundo a notícia do portal nacional).

**IBS/CBS (layout 2).** Serviços prestados a partir de 01/01/2026; alíquotas simbólicas de 2026 (CBS 0,9% e IBS 0,1%); substituição de nota no layout 2 ainda não existe.

**Créditos de IPTU (Nota do Milhão).** O tomador ganha crédito de 30% do ISS (pessoa física) e de 5% (PJ responsável), com restrições para créditos de 02/03/2017 em diante. Entidade opcional `Mov_Nfse_Credito_Tomador`; recomendo ficar de fora (D-N29).

# 7. Proposta

**Entidades novas (5 recomendadas):**

| Entidade | Vigência | Conteúdo |
|---|---|---|
| `Cad_Servico_Municipal` | sim | Mestre de código de serviço por município, que o dicionário hoje só guarda como texto em `Cad_Produto_Servico_Codigo_Municipal`. Campos: ID_Municipio, Codigo (4 ou 5 dígitos), Descricao, ID_Servico_Tributacao (código nacional), Aliquota_Iss, Aliquota_Iss_Minima, Aliquota_Iss_Maxima, Retencao {não, sim, só fora de SP}, Permite_Tributacao_Fora, Permite_Intermediario, Natureza_Pessoa {física, jurídica}, Caracteriza_Sup, Exige_Cno (códigos 01015, 01023, 01031, 01058, 01090, 01112), Permite_Encapsulamento, Permite_Cei, Permite_Imunidade_Objetiva, Aceita_Atividade_Evento, Regime_Recolhimento {guia da NFS-e, SDPE, DIF, plano de saúde}, vigência e motivo. `Cad_Produto_Servico_Codigo_Municipal` passa a apontar para ele. O manual **não traz a lista com alíquotas** (o sistema exibe a alíquota ao escolher o código) |
| `Mov_Nfts` | não | Item 5 |
| `Mov_Nfse_Aceite` | não | Item 6 |
| `Mov_Iss_Guia` | não | Item 6 |
| `Mov_Iss_Guia_Item` | não | Item 6 |

**Opcionais:** `Cad_Cpom_Situacao` (situação do prestador ou da atividade no Cadastro de Prestadores de Fora do Município; alertas 420 e 473) e `Mov_Nfse_Credito_Tomador`. Com as 103 entidades do documento 33 revisado pelo documento 34, o total passa a **108**; com os dois opcionais, **110**; com o pacote opcional de API e parâmetros municipais do documento 34, **121** (totais de 05/10/2026, sem os documentos 36 e seguintes). Os nomes foram conferidos por script contra o modelo (539 na época; hoje 543, sem colisão), o documento 33 (91) e o conjunto completo do documento 34 (23 entidades).

**Campos novos em entidades existentes.** `Mov_Dfe_Transmissao` (Transacao_Atomica, Periodo_Inicio, Periodo_Fim); `Mov_Nfse_Rps` (os campos da tabela do item 4, mais Tipo_Rps com a série, Situacao_Conversao, Natureza_Operacao, Local_Incidencia, Tipo_Retencao_Federal e as autorreferências de substituição); `Mov_Nota_Fiscal_Entrada` (status "rejeitada" e os modelos NFS-e paulistana e NFTS no domínio de modelo de documento); `Mov_Titulo` (origem guia_iss e nfts); `Mov_Titulo_Retencao` (ID_Guia_Iss e Responsavel {tomador, intermediário}); `Cad_Participante_Inscricao` (Natureza_Cadastro_Municipal {PJ, autônomo}, Indicador_Sup); `Cad_Autoridade_Fiscal_Servico` (tipos de serviço: envio de NFTS, envio e teste de lote de NFTS, consulta de NFTS, consulta de lote, consulta de informações do lote, cancelamento de NFTS e consulta de emissão); `Cad_Obrigacao_Acessoria` (linhas NFTS_SAO_PAULO, GUIA_ISS_NFSE_SP e SDPE_SP); `Cad_Dfe_Codigo_Retorno` (natureza alerta). Domínios novos em `Cad_Classe_Sistema`: tributacao_nfts, tributacao_nfse_sp, opcao_simples_nfse_sp, retencao_pis_cofins_csll_nfse, natureza_operacao_nfse_sp, local_incidencia_nfse_sp, motivo_rejeicao_nfse, situacao_aceite_nfse e tipo_documento_nfts.

# 8. Contradições com os documentos 33 e 34

1. O documento 33 (§3, item 6) e a D-N2 assumem a migração de autônomos e do Simples para o Emissor Nacional; os manuais não a mencionam, mas a página da Prefeitura de 13/08/2026 a confirma com as datas 03/08/2026 e 01/11/2026 (item 1).
2. O documento 33 (§9) deixa a NFTS fora do desenho (item 5).
3. O documento 33 trata o MEI como novidade de 2027; ele já está vedado no sistema paulistano desde 01/09/2023.
4. O documento 34, P-8 (substituição em `Mov_Nfse_Dps`) vale só para o Nacional; o modelo paulistano tem regras próprias.
5. O documento 33 prevê modo assíncrono e recibo para a NFS-e. No canal paulistano isso existe (LoteNFeAsync, protocolo GUID); no Nacional não. O framework precisa dos dois.
6. A planilha do novo layout diverge do manual em pontos isolados (por exemplo, `PagamentoParceladoAntecipado` obrigatório). Prevalece o manual.

# 9. Decisões e perguntas

A numeração continua a do documento 34 (que vai até D-N24).

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N25 | Migração de autônomos (03/08/2026) e do Simples (01/11/2026) para o Emissor Nacional: **fonte oficial recebida** (página da Prefeitura de 13/08/2026). Rotear por perfil, com data de início por contribuinte e o cadastro nacional (CNC) prevalecendo se divergir | Sim. Mantém o ERP aceitando os dois canais por contribuinte, com o perfil como regra padrão. **Nota (05/10/2026): Alberto disse que São Paulo vai fazer o envio ao sistema nacional (não que o Simples emita só pelo Emissor Nacional); a página da Prefeitura de 13/08/2026 diz o contrário, e ele decidiu que o ERP aceita os dois canais e que o roteamento fica em parâmetro (perfil e data em `Cad_Autoridade_Fiscal_Atendimento`). Nenhuma entidade muda; falta a fonte que confirme qual canal vale para o Simples a partir de 01/11/2026.** |
| D-N26 | NFTS no escopo? A Mlegate emitirá a NFTS (aprova `Mov_Nfts`) ou só registrará as emitidas no portal? | Emitir: a Compras precisa dela quando o prestador não emite nota |
| D-N27 | Guia de ISS: entidades próprias (`Mov_Iss_Guia` e item) ou especializar `Mov_Apuracao_Obrigacao_Recolher`? E o ERP baixa a guia pelo Web Service ou só registra a emitida no portal? | Entidades próprias, com a guia emitida no portal no início |
| D-N28 | Aceite e rejeição de NFS-e recebida com ISS retido (`Mov_Nfse_Aceite`): o ERP faz ou só acompanha o prazo? | Só acompanhar o prazo e registrar o aceite tácito no começo |
| D-N29 | Créditos de IPTU (Nota do Milhão): rastrear no ERP? | Não |
| D-N30 | Documento com vários serviços: gerar um RPS por código de serviço (regra paulistana)? | Sim |
| D-N31 | Ordem de implementação: recepção e manifestação (NFS-e recebida, NFTS, DistDFe) antes da emissão? | Sim, em linha com o corte de 01/11/2026 só para recepção |
| D-N32 | No canal paulistano, usar só o serviço síncrono ou também o lote assíncrono? | Síncrono no começo; o framework já comporta o assíncrono |

**Perguntas de confirmação** (sem decisão estrutural):

- **Q-1.** Qual COD_MOD da EFD e qual tipo de documento na Reinf (R-2010) a NFTS usa? Os manuais não dizem. **Respondida em parte por Alberto (12/10/2026): o COD_MOD da nota fiscal de serviço é o 03, mas outros podem aparecer com o tempo; por isso o modelo vira cadastro de modelos, parametrizado pelo tipo de modelo (documento 46, seção 5, D-N96).** O tipo de documento do R-2010 segue sem resposta; a tabela 4.1.1 carregada (versão 7) não traz o 03 (P46-01).
- **Q-2.** De onde vem a lista de códigos municipais com alíquotas (Lei 13.701/03)? O anexo do manual PJ (pp. 232 a 233) traz só três tabelas de código.
- **Q-3.** Tomador pessoa física: os manuais não definem retenção. O ERP deve forçar "ISS retido = não" nesse caso?
- **Q-4.** Prazo de cancelamento da NFTS: o erro 324 indica o prazo, mas o manual do Web Service não o fixa. **Respondida por Alberto (05/10/2026): deixar como parâmetro, porque o prazo pode mudar a cada gestão pública.** O prazo entra nos parâmetros do município com vigência (mesmo mecanismo da D-N19), sem valor fixo no sistema; o erro 324 da Prefeitura continua valendo como trava final.
- **Q-5.** DES-IF, DeSTDA e a declaração mensal não aparecem nos três manuais (só o DIF). **Respondida por Alberto (05/10/2026): ele enviou o pacote oficial da DES-IF (Manual, Modelo Conceitual 3.1, FAQ e 13 anexos) e a página da DeSTDA; o desenho está no documento 39** (DES-IF com modelo nacional e parâmetros por município; DeSTDA com entidades agora e arquivo depois). Contribuinte obrigado à DES-IF é desobrigado da NFS-e, e a emissão eventual não gera crédito ao tomador (art. 81 e 86 do Decreto 53.151/2012).
- **Q-6.** SUP e ISS fixo trimestral: modelar o recolhimento para clientes SUP? **Respondida por Alberto (12/10/2026): sim, desenhado pelo tipo de empresa, com a sociedade uniprofissional entrando como tipo; escolheu o regime de ISS por empresa e município, com vigência (documento 46, seção 4, D-N98).**

# 10. O que ainda falta

O texto das Resoluções CGSN nº 189/2026 e nº 191/2026; o leiaute 2 liberado em produção; a lista de códigos de serviço do município com alíquotas; as declarações municipais além da DES-IF (que veio no documento 39) e da DeSTDA (sem leiaute).

# 11. Fontes e verificação

Os grupos de campos foram classificados lendo o manual v3.3.9 e a planilha (121 grupos) contra o modelo (539 entidades na época; hoje 543) e o documento 33. As regras de NFTS, aceite, guia, cancelamento e substituição vêm dos manuais da NFTS v3.1 e do prestador PJ v6.2 e PF v5.1; conferi diretamente nos manuais que o MEI está vedado no sistema paulistano desde 01/09/2023 e que eles não citam migração de autônomos nem de optantes do Simples; as datas da migração vêm da página da Secretaria Municipal da Fazenda de 13/08/2026. Nenhuma entidade foi criada no dicionário.
