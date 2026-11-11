# Tabela do ISS fixo da SUP 2026 e API de Débitos CBS: Leitura e Cruzamento — Documento 55

*Dois materiais que Alberto enviou em 12/10/2026: o PDF "Sociedades Uniprofissionais: Base de cálculo e ISS a pagar (2026)" e a página do leiaute da API de Débitos CBS (`docs.receitafederal.gov.br/apuracao-cbs/debito.html`, com a lista de endereços de débitos, pagamentos e situação). Documento de proposta e controle: nada foi alterado no dicionário. O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N130 e D-N131 (tabela do ISS fixo da SUP e API de Débitos da CBS), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

**Tabela da SUP 2026.** Fecha a pendência P46-06 só em parte: traz os valores de 2026 e não a série desde 2004. A conta do próprio PDF confere (156 linhas: o ISS trimestral é a base mensal vezes a alíquota vezes 3, com diferença de no máximo 1 centavo). O ponto que muda o desenho: a faixa da tabela é de **quantidade de profissionais habilitados**, e não de receita, como o documento 46 supôs ao ler a página da Prefeitura. `Cad_Iss_Fixo_Tabela` não tem campos para isso. Proposta **D-N130** (seção 3).

**API de Débitos CBS (leiaute v1.1).** Confirma o desenho do espelho da CBS (`Mov_Cbs_Apuracao_Espelho_Conta`) quase por inteiro, com três lacunas: o domínio das origens do débito tem 13 códigos e o dicionário tem 8; três datas e o NI do consumidor não têm campo; e **não existe entidade para o tíquete** (o documento 36 dizia que cabia nos campos de controle da integração, mas o modelo não tem nenhum). Proposta **D-N131** (seção 5).

Somando os documentos 53, 54 e 55, a revisão 5 teria **842 entidades** (837 mais 5 novas) e 11 alteradas **sem** as decisões D-N106 a D-N117, que ainda não estão no dicionário (correção no documento 56, seção 2: com elas, o total passa de 20 alteradas).

# 2. A tabela da SUP 2026: o que o PDF traz

**Fonte.** O arquivo é a impressão de uma planilha ("Consolidado 2026 revisado atualizado fw 27_02_26.xlsx", impresso em 27/02/2026, com um autor pessoa física nas propriedades). O texto não identifica a Prefeitura nem cita lei ou portaria. Trato como **fonte secundária**: a carga entra provisória e o DUC ou o contador confirmam.

**Conteúdo.** 24 códigos de serviço do regime especial da sociedade uniprofissional, 156 linhas:

| Grupo | Códigos | Alíquota | Forma |
|---|---|---|---|
| Engenharia, agronomia, arquitetura e geologia | 01546\*, 01547, 01548, 01549, 01627\*, 01628, 01629 | 5% | 7 faixas de profissionais |
| Auditoria, contador e economistas | 03433, 03620, 03700 | 5% | 7 faixas |
| Advocacia, uso restrito | 03380 | 5% | Valor único por profissional |
| Saúde: medicina e biomedicina, análises clínicas, enfermagem, fisioterapia, fonoaudiologia, terapia ocupacional, obstetrícia, odontologia, ortóptica, próteses, psicologia, veterinária e zootecnia | 04111, 04154, 04359, 04430, 04502, 04553, 04677, 04731, 04901, 05096, 05142, 05410 | 2% | 7 faixas |
| Medicina, uso restrito | 04112 | 2% | Valor único por profissional |

\* Os códigos 01546 e 01627 aparecem como "encerrado em 31/12/2025", e as outras linhas dos mesmos grupos (01547 a 01549 e 01628, 01629) seguem vigentes.

As 7 faixas são de **profissionais habilitados**: até 5, de 6 a 10, de 11 a 20, de 21 a 30, de 31 a 50, de 51 a 100 e a partir de 101. A mesma base mensal vale para todos os códigos; só a alíquota muda.

| Faixa de profissionais | Base de cálculo mensal por profissional | ISS trimestral por profissional a 5% | ISS trimestral por profissional a 2% |
|---|---|---|---|
| Até 5 | R$ 2.413,62 | R$ 362,04 | R$ 144,81 |
| De 6 a 10 | R$ 6.048,39 | R$ 907,25 | R$ 362,90 |
| De 11 a 20 | R$ 12.096,79 | R$ 1.814,51 | R$ 725,80 |
| De 21 a 30 | R$ 24.193,60 | R$ 3.629,04 | R$ 1.451,61 |
| De 31 a 50 | R$ 36.290,39 | R$ 5.443,55 | R$ 2.177,42 |
| De 51 a 100 | R$ 48.387,19 | R$ 7.258,07 | R$ 2.903,23 |
| A partir de 101 | R$ 72.580,80 | R$ 10.887,12 | R$ 4.354,84 |
| Valor único (03380 e 04112) | R$ 2.656,48 | R$ 398,47 | R$ 159,38 |

**Conferência.** Li as 156 linhas por script. Em todas, o ISS trimestral é a base mensal vezes a alíquota vezes 3, com diferença de no máximo 1 centavo (algumas linhas parecem truncadas e não arredondadas, como R$ 159,38 contra 159,39). Isso mostra que o valor trimestral é **derivável** da base, e que a Prefeitura guarda os dois.

**Observação, sem conclusão.** As bases das faixas seguem a proporção de 1; 2,5; 5; 10; 15; 20 e 30 sobre cerca de R$ 2.419,36 (a primeira faixa mostra R$ 2.413,62, que é um pouco menor que esse valor). Pode ser um multiplicador legal por tamanho da sociedade. O cabeçalho diz "por profissional", e o dicionário já calcula `Valor_Devido` como quantidade de profissionais vezes o valor por profissional. **Pergunta para o contador, com o DUC aberto:** o valor da faixa multiplica a quantidade de profissionais, ou a faixa já é o total?

# 3. D-N130: a tabela do ISS fixo por faixa de profissionais

O que existe hoje em `Cad_Iss_Fixo_Tabela` (documento 46): município, serviço municipal, **faixa de receita** (inicial e final), valor por profissional, periodicidade, índice, ato legal, situação do dado e vigência. A tabela de São Paulo não usa receita. Proposta, sem entidade nova:

| Campo | Tipo | Regra |
|---|---|---|
| `Faixa_Profissionais_Inicial` | número, opcional | Primeira quantidade de profissionais da faixa (1, 6, 11, 21, 31, 51, 101) |
| `Faixa_Profissionais_Final` | número, opcional | Última quantidade da faixa; vazio na faixa aberta (a partir de 101) |
| `Base_Calculo_Mensal` | número, opcional | Base mensal por profissional da tabela (R$ 2.413,62 na primeira faixa) |
| `Aliquota` | número, opcional | 5 ou 2 |
| `Valor_Unico_Por_Profissional` | booleano | Verdadeiro nos códigos 03380 e 04112: sem faixa de profissionais |
| `Uso_Restrito` | booleano | Verdadeiro nos mesmos dois códigos; o PDF não explica o que significa (a perguntar ao contador) |

`Valor_Por_Profissional` continua sendo o valor trimestral, gravado como veio na tabela. `Faixa_Receita_Inicial` e `Faixa_Receita_Final` ficam vazios na carga de São Paulo; outros municípios podem usá-los. `ID_Servico_Municipal` passa a ser preenchido em São Paulo, porque o código define a alíquota e a linha. `Mov_Iss_Fixo_Apuracao` não muda: a apuração guarda a linha usada (`ID_Iss_Fixo_Tabela`), a quantidade do trimestre e o valor por profissional gravado.

**Carga.** 142 linhas vigentes de 01/01/2026 a 31/12/2026 (20 códigos com 7 faixas e os 2 de valor único), `Situacao_Dado` = provisório, `Indice_Reajuste` = IPCA, `Ato_Legal` = Lei 13.701/2003 e o arquivo de 27/02/2026. Os dois códigos encerrados (01546 e 01627) entram **só como código com fim de vigência em 31/12/2025**, sem as 14 linhas de valores de 2026, porque a tabela é de 2026 e eles acabaram antes (o motivo de o PDF ainda listar valores para eles fica para o contador).

**Continua faltando.** A série desde 2004 (só importa para períodos passados, se algum cliente precisar) e a tabela de 2027, que a Prefeitura reajusta por IPCA. A pendência P46-06 passa a pedir só isso.

# 4. A API de Débitos CBS: o que a página traz

Leiaute v1.1, endereço na versão 2 da API. Em resumo:

| Ponto | O que a página diz |
|---|---|
| Chamada | POST em `https://api.receitafederal.gov.br/apuracao-cbs/v2/debitos/{cnpj}` (produção) ou `.../apuracao-cbs-prr/v2/debitos/{cnpj}` (produção restrita); CNPJ base de 8 dígitos; cabeçalho `Authorization: Bearer <token>`; corpo com `urlRetorno` (HTTPS pública) |
| Resposta | HTTP 201 com `tiqueteSolicitacao` e `tEASegundos` (tempo estimado para atendimento, em segundos); erros 400, 401, 404 e 500 com `codigoErro` e `mensagemErro` |
| Retorno (webhook) | `tiqueteSolicitacao`, `urlAssinada` e `urlAssinadaExpiraEm`; o arquivo é um JSON |
| Janela | No máximo 8 dias; a primeira consulta devolve desde o dia 1º do mês corrente |
| Arquivo | `ni` (8), `niConsumidor`, `geradoEm`, e por período de apuração (`pa`, mm/aaaa) uma lista de débitos com `origem`, `documento`, `chave` (50), `emissao`, `registro`, `atualizacao` e o grupo `cbs` (`excedente`, `apurado`, `inexigivel`, `suspenso`, `extinto`, `saldoDevedor`, em número 18,2) |
| Origem (13 códigos) | 0 normal; 20, 21 e 22 devolução por PCONT, por RAD e por crédito; 30, 31 e 32 cancelamento de crédito, de RAD e de PCONT; 50 e 51 perecimento no transporte FOB e CIF; 52, 53 e 54 devolução do perecimento CIF por PCONT, por RAD e por crédito; 55 nota de crédito de multa e juros |
| Documento (13 códigos) | 55 NF-e, 57 CT-e, 62 NFCom, 63 BP-e, 64 GTV-e, 65 NFC-e, 66 NF3-e, 67 CT-e OS, 91 NFS-e, 92 NFS-e Via, 93 BP-e TM, 94 DERE, 97 CT-e Simplificado |
| Erro | Só um código de exemplo: APURACAO-001, "Parâmetros inválidos para processamento da solicitação." |

**Inconsistências da própria página** (o Swagger oficial continua em falta): o exemplo do webhook traz a `urlAssinada` malformada; a expiração do payload (26/08/2026) não bate com a embutida na URL (172.800 segundos, com data de 10/09/2026 no trecho final); `documento` aparece como "Tipo/Número" e o domínio só tem tipos; a cardinalidade do grupo `cbs` aparece como "3:7"; a página não define o token. Tratei o leiaute como fonte, e o que ela contradiz fica como pergunta.

**Os endereços que Alberto colou** conferem com `Cad_Autoridade_Fiscal_Servico` (que já tem os tipos `apuracao_cbs_debitos`, `apuracao_cbs_creditos`, `apuracao_cbs_pagamentos`, `apuracao_cbs_recolhimentos` e `apuracao_cbs_situacao`, e os campos `Limite_Diario_Aberturas` e `Janela_Maxima_Dias`). A lista traz débitos, pagamentos e a situação da solicitação (`.../v2/situacao/{tiqueteSolicitacao}`). **Não li** as páginas de pagamentos e da situação: a ferramenta de leitura só abre o endereço que aparece literalmente numa mensagem, e a de débitos foi a única que chegou assim. Se Alberto enviar os dois endereços, leio em seguida.

# 5. D-N131: o que falta no espelho e o controle do tíquete

## 5.1 Cruzamento com `Mov_Cbs_Apuracao_Espelho_Conta`

| Item do leiaute | Dicionário (revisão 4) | Lacuna |
|---|---|---|
| `pa` | `Mov_Cbs_Apuracao_Espelho.Periodo` | Nenhuma |
| `origem` (13 códigos) | `ID_Origem_Debito`, domínio `origem_debito_cbs` com 8 valores (`normal`, `devolucao_pcont`, `devolucao_rad`, `devolucao_credito`, `cancelamento`, `perecimento_transporte_fob`, `perecimento_transporte_cif`, `nota_credito_multa_juros`) | **O domínio é menor**: `cancelamento` é um só (a Receita separa 30, 31 e 32), e faltam as 3 devoluções do perecimento CIF (52, 53 e 54) |
| `documento` | `ID_Modelo_Documento` | Os códigos 91, 92, 93 e 94 são numeração da Plataforma, e a carga de `Cad_Modelo_Documento_Fiscal_Codigo` não os tem (confiro ao consolidar) |
| `chave` | `Chave_Documento` (50) | Nenhuma |
| `cbs.*` (6 valores) | `Valor_Cbs_Apurado`, `_Excedente`, `_Inexigivel`, `_Suspenso`, `_Extinto`, `_Saldo_Devedor` | Nenhuma |
| `emissao`, `registro`, `atualizacao` | Nenhum campo | **Faltam 3 datas e horas.** `atualizacao` é a base da leitura incremental e da conferência de "o que mudou" |
| `niConsumidor` | Nenhum campo | **Falta** o NI do consumidor (o adquirente do documento) |
| `ni` | `Mov_Cbs_Apuracao_Espelho.ID_Empresa` | Nenhuma |
| `tiqueteSolicitacao`, `tEASegundos`, `geradoEm`, `urlAssinada`, `urlAssinadaExpiraEm`, `codigoErro`, `mensagemErro` | Só `Cad_Autoridade_Fiscal_Credencial.Url_Retorno_Webhook` | **Falta a entidade do tíquete** (5.2) |

## 5.2 O que proponho

**(a) Domínio `origem_debito_cbs` com 13 valores**, o código numérico da Receita no campo `Codigo` de `Cad_Classe_Sistema` (que já existe): `normal` (0), `devolucao_pcont` (20), `devolucao_rad` (21), `devolucao_credito` (22), `cancelamento_credito` (30), `cancelamento_rad` (31), `cancelamento_pcont` (32), `perecimento_transporte_fob` (50), `perecimento_transporte_cif` (51), `devolucao_perecimento_cif_pcont` (52), `devolucao_perecimento_cif_rad` (53), `devolucao_perecimento_cif_credito` (54), `nota_credito_multa_juros` (55). O valor `cancelamento` sai (substituído pelos três).

**(b) Quatro campos novos em `Mov_Cbs_Apuracao_Espelho_Conta`, todos opcionais:** `Data_Hora_Emissao`, `Data_Hora_Registro` e `Data_Hora_Atualizacao_Receita` (data e hora), e `NI_Consumidor` (código até 14). Mais `ID_Cbs_Solicitacao` (referência à entidade abaixo, para saber de qual retorno veio cada linha).

**(c) Entidade nova `Mov_Cbs_Solicitacao`**, sem vigência, uma linha por tíquete:

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Cbs_Solicitacao` | identificador | Chave primária |
| `ID_Empresa` | referência (Cad_Empresa) | CNPJ base consultado |
| `ID_Autoridade_Fiscal_Servico` | referência | Qual consulta: débitos, créditos, pagamentos ou recolhimentos; leva o ambiente (produção restrita ou produção) |
| `ID_Credencial` | referência (Cad_Autoridade_Fiscal_Credencial) | Credencial e `urlRetorno` usadas |
| `Tiquete_Solicitacao` | código (até 100), único | `tiqueteSolicitacao` |
| `Data_Hora_Solicitacao` | data e hora | Quando o ERP abriu a consulta (conta o limite de 4 aberturas por dia) |
| `Tempo_Estimado_Segundos` | número, opcional | `tEASegundos` |
| `ID_Situacao` | referência (Cad_Classe_Sistema, domínio = situacao_solicitacao_cbs) | Domínio aberto: pendente, em processamento, concluída e erro, a confirmar com a página da situação, que não li |
| `Codigo_Erro` e `Mensagem_Erro` | código (até 30) e texto, opcionais | `codigoErro` e `mensagemErro` (APURACAO-001, por exemplo) |
| `Data_Hora_Geracao_Arquivo` | data e hora, opcional | `geradoEm` |
| `Url_Assinada_Expira_Em` | data e hora, opcional | `urlAssinadaExpiraEm`; **a URL assinada em si não é guardada** (é credencial temporária de download) |
| `Data_Hora_Download` | data e hora, opcional | Quando o ERP baixou o arquivo |
| `Hash_Arquivo` | código (até 64), opcional | Conferência do arquivo baixado |
| `Referencia_Arquivo_Bruto` | texto, opcional | Onde o JSON original fica guardado, para auditoria |

`Cad_Autoridade_Fiscal_Servico` já guarda o limite diário e a janela; nada muda lá. Isso **revisa a frase do documento 36** (seção 12.1) de que o controle do tíquete cabe nos campos da camada de integração: o modelo de 837 entidades não tem nenhum campo de tíquete, situação de solicitação ou erro de consulta assíncrona.

# 6. Impacto, perguntas e verificação

| Item | Quantidade |
|---|---|
| Entidades novas por D-N131 | 1: `Mov_Cbs_Solicitacao` |
| Entidades alteradas por D-N130 e D-N131 | 2: `Cad_Iss_Fixo_Tabela` e `Mov_Cbs_Apuracao_Espelho_Conta`; `Cad_Classe_Sistema` já está entre as alteradas do documento 53 (o domínio `origem_debito_cbs` muda de 8 para 13 valores) |
| Documentos 53, 54 e 55 somados (sem D-N106 a D-N117; ver documento 56) | 837 mais 5 novas (3 do documento 53, `Cad_Compensacao_Prejuizo_Parametro` e `Mov_Cbs_Solicitacao`) = **842**; **11 alteradas** (9 do documento 54 mais as 2 acima) |

| Id | Pergunta | Recomendação |
|---|---|---|
| D-N130 | Acrescentar à tabela do ISS fixo a faixa por profissionais, a base mensal, a alíquota e os dois indicadores, e carregar as 142 linhas de 2026 como provisórias? | Sim: a tabela de São Paulo não cabe na faixa de receita |
| D-N131 | Ampliar o domínio da origem do débito para 13 valores, acrescentar as 4 colunas e criar `Mov_Cbs_Solicitacao`? | Sim: o leiaute é fonte oficial e o limite de 4 aberturas por dia exige controle |

**Respostas de Alberto (12/10/2026):** D-N130 e D-N131 como propostos. Nada foi consolidado: o dicionário segue com 837 entidades e a revisão 5 (842 entidades e 11 alteradas só com D-N125 a D-N131; a contagem completa está no documento 56) espera o "consolidar" de Alberto.

**Para o contador (não para Alberto):** o valor da faixa multiplica a quantidade de profissionais? O que é "uso restrito" nos códigos 03380 e 04112? Por que o PDF lista valores de 2026 para os códigos encerrados em 31/12/2025?

**Fontes.** PDF da tabela da SUP (24 códigos e 156 linhas, lidas por texto e conferidas por script); página `apuracao-cbs/debito.html` lida em 12/10/2026 pela ferramenta de leitura de páginas (resumo do conteúdo, não o Swagger); lista de endereços colada por Alberto; `model.json` da revisão 4 (837 entidades), para o cruzamento.

**Conferido por mim.** A conta de todas as linhas da SUP; a ausência de campos de tíquete no modelo (busca em todos os campos); os campos de `Cad_Iss_Fixo_Tabela`, `Mov_Iss_Fixo_Apuracao`, `Mov_Cbs_Apuracao_Espelho_Conta` e `Cad_Autoridade_Fiscal_Servico`.

**Não verificado.** A origem oficial da tabela da SUP (o PDF não a identifica); se o valor da faixa multiplica a quantidade de profissionais; as páginas de pagamentos, créditos, recolhimentos e da situação da solicitação; o Swagger da API; a numeração 91 a 94 na carga de modelos de documento.
