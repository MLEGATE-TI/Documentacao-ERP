# Desenho Proposto: DES-IF e DeSTDA — Documento 39

*Proposta de desenho (nível de entidade e campos principais) para a Declaração de Instituições Financeiras da Prefeitura de São Paulo (DES-IF) e para a DeSTDA do Simples Nacional na SEFAZ-SP, a partir dos 16 PDFs oficiais e da página da DeSTDA que Alberto enviou em 05/10/2026. Responde a pergunta Q-5 do documento 35. Não altera o dicionário: nada disto entra sem o seu "consolidar".*

*Nota de 12/10/2026 (documento 48): o texto do Ajuste SINIEF 12/2015 chegou e foi lido contra a seção 9 (DeSTDA). O desenho se confirma, com quatro correções propostas (tipo de imposto do consumidor final não contribuinte, escrituração centralizada, canais de recepção e padrão de declaração sem dados), descritas na seção 6 do documento 48. O Manual DeSTDA 2016 da SEFAZ-SP também chegou (seção 6.1 do documento 48): confirma o desenho e não muda as decisões. O leiaute do arquivo (Ato COTEPE 47/15) continua em falta. O texto abaixo não foi reescrito.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Alberto mandou o pacote completo da DES-IF (Manual do Usuário v1.0 de 2017, Modelo Conceitual 3.1 de fevereiro de 2025, FAQ v5 de outubro de 2025 e os 13 anexos da Portaria SF/SUREM nº 9/2025) e a página da DeSTDA. Respondeu às quatro perguntas deste desenho com a recomendação: **modelo nacional com parâmetros por município**, **gerar, assinar e registrar o protocolo**, **contabilidade do ERP como fonte, com importação como alternativa** e, na DeSTDA, **entidades agora e arquivo depois**.

**DES-IF.** É a declaração das instituições financeiras e demais entidades do plano de contas COSIF, estabelecidas em São Paulo, que **substitui a NFS-e** desses contribuintes. Tem três módulos de entrega e um sob demanda: Módulo 3 (plano de contas comentado, tarifas e outros serviços), Módulo 2 (apuração mensal do ISS), Módulo 1 (balancete semestral) e Módulo 4 (partidas dos lançamentos, só quando a Prefeitura pedir). O ERP já tem a maior parte da base: o plano referencial do BACEN (`Cad_Plano_Referencial`), o saldo contábil por conta (`Mov_Saldo_Contabil`), as partidas (`Mov_Lancamento`), o arquivo de escrituração (`Mov_Escrituracao_Arquivo`, documento 33) e o título a pagar (`Mov_Titulo`). A proposta soma **21 entidades novas** (14 cadastros e 7 movimentos), sem tabela de campo por registro do arquivo: o que é regra do município vira parâmetro com vigência, e as tabelas oficiais (COSIF, tarifas, códigos de tributação, mensagens de erro) entram como dado.

**DeSTDA.** É a declaração mensal de ICMS-ST, DIFAL e antecipação dos optantes do Simples Nacional (exceto MEI) com inscrição estadual em São Paulo, até o dia 28 do mês seguinte, enviada pelo aplicativo SEDIF-SN. A página não traz o leiaute. A proposta soma **3 entidades novas** e reaproveita o arquivo de escrituração e a transmissão manual já desenhados; o arquivo para o SEDIF-SN espera o leiaute oficial.

**Total: 24 entidades novas.** O modelo consolidado hoje tem 543 entidades; as propostas dos documentos 33 a 36 ainda não foram consolidadas, e este desenho depende de uma delas (`Mov_Escrituracao_Arquivo`, do documento 33), por isso a contagem final só fecha na revisão 3.

**Duas coisas que você precisa saber antes de ler.** Primeira: **o Módulo 1 do primeiro semestre de 2026 venceu em 01/10/2026** (primeiro dia útil de outubro, regra da IN SF/SUREM nº 14/2023); se houver cliente banco em São Paulo, a entrega já está atrasada, embora o FAQ diga que a multa só é aplicada no decorrer de uma ação fiscal. Segunda: **o pacote não traz webservice**: a entrega é por importação do arquivo assinado (p7s) no portal com e-CNPJ, então o envio fica manual e o ERP controla o ciclo (arquivo, assinatura, protocolo, inconsistências, retificação).

# 2. O que li e o que não foi possível ler

| Fonte | Situação |
|---|---|
| FAQ v5 (outubro de 2025), Manual do Usuário v1.0 (setembro de 2017) e Modelo Conceitual 3.1 (63 páginas) | Lidos inteiros; o leiaute dos registros 0000, 0100, 0200, 0300, 0400, 0410, 0430, 0440 e 1000 está no Modelo Conceitual e não precisou de adivinhação |
| Anexos 1, 2, 4, 6, 7, 8, 9, 10 e 13 | Lidos inteiros (pequenos) |
| Anexos 3 (COSIF), 5 (municípios do IBGE), 11 (mensagens de erro) e 12 (soluções) | Estrutura e amostra conferidas; contagens por programa: **1.432 contas COSIF** (502 de 8 dígitos extintas em 31/12/2024 e 930 de 10 dígitos vigentes desde 01/01/2025), **5.570 municípios**, **357 códigos de mensagem** (113 marcados como excluídos). Não li as 1.600 linhas dos anexos 11 e 12 uma a uma: entram como carga |
| Página da DeSTDA (SEFAZ-SP) | Lida por resumo automático da página: não traz leiaute, manual, penalidades nem a lista de UFs; cita o domínio `sedif.pe.gov.br`, que parece defeito do resumo (o instalador listado é do portal da SEFAZ-SP) e **não foi verificado**; o link do instalador não foi aberto |
| Vídeos tutoriais e o formulário de contabilidade unificada fora de São Paulo | Não consultados |

# 3. DES-IF: a obrigação

| Item | O que a fonte diz | Fonte |
|---|---|---|
| Quem entrega | Instituições financeiras e demais entidades obrigadas pelo BACEN ao COSIF, estabelecidas em São Paulo e constantes da "Relação de Instituições em Funcionamento no País" (ou listagem equivalente), com CCM em funcionamento | FAQ, IN SF/SUREM nº 17/2017 |
| Relação com a NFS-e | A obrigação de entregar a DES-IF **exclui** a emissão de NFS-e (art. 81 do Decreto 53.151/2012); a emissão eventual é facultativa, **vedada a geração de crédito** (art. 86) | FAQ |
| Módulo 3 (informações comuns) | Primeira declaração, até o vencimento do ISS do primeiro mês de incidência do ano (mesmo sem imposto) e sempre que o plano de contas mudar; informa janeiro a dezembro, exceto início ou encerramento | FAQ, Modelo Conceitual |
| Módulo 2 (apuração mensal do ISS) | Até o dia 10 do mês seguinte, ou o próximo dia útil; só depois do Módulo 3 | FAQ |
| Módulo 1 (balancete semestral) | Até o primeiro dia útil de outubro (1º semestre) e de abril (2º semestre) | FAQ, IN SF/SUREM nº 14/2023 |
| Módulo 4 (partidas) | Sob demanda da Administração Tributária, por período ou por conjunto de subtítulos | Manual, Modelo Conceitual |
| Retificação | Até o último dia do mês seguinte ao previsto para a entrega; depois, a qualquer tempo, se não houver ação fiscal nem dívida ativa | FAQ |
| Forma de envio | Arquivo TXT em UTF-8 **sem BOM**, assinado digitalmente em **p7s com conteúdo atachado**, importado no portal com certificado ICP-Brasil A1 ou A3 (e-CNPJ no primeiro acesso); o representante com perfil de consulta não transmite | FAQ, Manual |
| Multas (art. 14 da Lei 13.476/2002, redação da Lei 15.406/2011) | R$ 2.444,27 por declaração entregue fora do prazo; R$ 6.110,69 por declaração não entregue; para dados inexatos ou incompletos, 50% ou 20% do imposto, com mínimos de R$ 148,23 e R$ 71,67 (R$ 71,67 fixo se não houver imposto) | FAQ |
| Arredondamento | São Paulo trunca na segunda casa decimal | FAQ |
| Código COSIF | 10 dígitos desde a incidência 01/2025; 8 dígitos até 12/2024 | FAQ |
| Plano de contas exigido | Grupo 7 do COSIF (e o grupo 8 a critério do município); desde 01/01/2025, também o subtítulo 1.6 e o desdobramento 1.8.1 e as contas TJEO do anexo 13 | FAQ, Modelo Conceitual |

**Não confirmado:** o tipo de consolidação do ISS adotado em São Paulo (1 a 4 do Modelo Conceitual). O FAQ diz que há um registro 0440 por código de tributação e que a guia sai no CCM centralizador, o que aponta para o tipo 2, mas não afirma. Fica como parâmetro com vigência, para o contador ou o portal confirmar. As penalidades e as datas acima são **dados com vigência** (valores atualizados por lei), não constantes de código.

# 4. DES-IF: o que o dicionário já tem

| Necessidade da DES-IF | Já existe | Como entra |
|---|---|---|
| Plano de contas do COSIF com vigência, hierarquia e conta superior | `Cad_Plano_Referencial` (Orgao_Regulador `bacen` já previsto) e `Cad_Plano_Referencial_Conta` | Duas edições: COSIF de 8 dígitos (até 12/2024) e COSIF de 10 dígitos (desde 01/2025). A data de criação e a de extinção da conta no anexo 3 viram a vigência da conta |
| Plano de contas interno ligado ao COSIF | `Cad_Conta_Contabil` e `Cad_Conta_Contabil_Referencial` (por empresa, com vigência) | O mapeamento já faz o papel do campo "Conta_COSIF" do registro 0100 |
| Balancete mensal por dependência | `Mov_Saldo_Contabil` (saldo inicial, débitos, créditos, saldo final e saldo antes do encerramento, por filial e competência) | Fonte padrão do registro 0410; a alternativa é importar o balancete de outro sistema (decisão desta rodada) |
| Dependência (agência, posto) | `Cad_Filial` e, para o CCM, `Cad_Participante_Inscricao` (pelo participante da filial; `Cad_Filial_Inscricao` não existe) | A dependência é a filial; o que a DES-IF acrescenta fica em `Cad_Desif_Dependencia` |
| Partidas (Módulo 4 e registro 1000) | `Mov_Lancamento` | Origem de `Mov_Desif_Partida` |
| Município do IBGE | `Cad_Municipio` | Anexo 5 é carga; código 9999999 (exterior) vira indicador, não município |
| Certificado digital e cofre | `Cad_Certificado_Digital` | Assina o p7s |
| Arquivo gerado, recibo, retificação e mensagens do validador | `Mov_Escrituracao_Arquivo` e `Mov_Escrituracao_Arquivo_Ocorrencia` (documento 33) | O TXT, o p7s, o protocolo e as inconsistências ficam aqui, sem entidade nova de transmissão |
| Cadastro das obrigações | `Cad_Obrigacao_Acessoria` (aberto, com vigência) | Cinco linhas novas: DESIF_M1, DESIF_M2, DESIF_M3, DESIF_M4 e DESTDA |
| Guia de pagamento | `Mov_Titulo` | O ISS a recolher vira título a pagar; Tesouraria baixa |
| Tabelas oficiais de código e descrição, sem atributo próprio | `Cad_Classe_Sistema` (domínio aberto, com vigência) | Anexo 8 (tipos de dependência) e os valores fixos do leiaute |

# 5. DES-IF: entidades novas

## 5.1 Cadastros e tabelas oficiais (14)

| Entidade | Vigência | Para que serve | Campos principais |
|---|---|---|---|
| Cad_Desif_Parametro_Municipio | sim, histórico | Regras de cada município (item 6.6.2 do Modelo Conceitual), no lugar de código fixo. São Paulo entra carregado | ID_Municipio (identidade); Tipos_Consolidacao_Permitidos; Tipo_Arredondamento {arredondado, truncado}; Permite_Iss_Retido_Consolidado; Permite_Iss_Retido_Subtitulo; Contas_Despesa {obrigatorias, vedadas, a_criterio}; Exige_Detalhe_Rateio; Exige_Detalhe_Estorno; Permite_Incentivo_Subtitulo; Percentual_Maximo_Incentivo_Subtitulo; Permite_Incentivo_Consolidado; Percentual_Maximo_Incentivo_Consolidado; Permite_Compensacao; Limite_Compensacao_Valor; Percentual_Maximo_Compensacao_Devido; Percentual_Maximo_Compensacao_A_Pagar; Dia_Entrega_Modulo2; Mes_Entrega_Modulo1_Primeiro_Semestre; Mes_Entrega_Modulo1_Segundo_Semestre; Prazo_Retificacao_Meses; Versao_Leiaute; Multa_Fora_Prazo; Multa_Nao_Entrega |
| Cad_Desif_Instituicao | sim, histórico | A empresa que é declarante em um município: tipo de instituição, início da obrigação, CCM centralizador e certificado | ID_Empresa e ID_Municipio (identidade); ID_Tipo_Instituicao; ID_Filial_Centralizadora; Data_Inicio_Obrigatoriedade; Data_Encerramento; Contabilidade_Unificada_Fora_Do_Municipio; Data_Comunicacao_Contabilidade_Unificada; ID_Certificado (→Cad_Certificado_Digital); Desobrigada_Nfse |
| Cad_Desif_Tipo_Instituicao | sim, histórico | Anexo 2: tipos sujeitos ao COSIF (U, B, D, K, I, F, J, A, C, T, S, W, E, R, L, M, N, H, P, Y, Z) | Codigo (identidade); Descricao; Tabela_Tarifas_Obrigatoria |
| Cad_Desif_Dependencia | sim, histórico | A dependência na DES-IF: o que o registro 0400 pede e a filial não tem | ID_Instituicao; ID_Filial; Codigo_Dependencia (CCM ou código interno); Indicador_Inscricao {inscricao_municipal, codigo_interno}; Cnpj_Proprio (6 últimos dígitos); Tipo_Dependencia (domínio, anexo 8); Endereco; ID_Filial_Unificadora; Contabilidade_Propria; Unificadora_Fora_Do_Municipio; ID_Municipio_Unificadora; Unificadora_No_Exterior |
| Cad_Desif_Conta_Config | sim, histórico | O que o registro 0100 pede além do mapeamento: desdobramento de conta mista, descrição da natureza e código de tributação | ID_Empresa e ID_Conta_Contabil (identidade); Desdobramento_Mista (00 a 99); Nome_Pgcc; Descricao_Natureza (até 600); ID_Codigo_Tributacao; Natureza_Tributaria_Desdobramento |
| Cad_Desif_Conta_Tarifa | sim, histórico | Registro 0200: liga a conta à tarifa bancária e ao valor tabelado | ID_Conta_Config; ID_Tarifa; Valor_Unitario; Valor_Percentual |
| Cad_Desif_Conta_Outro_Servico | sim, histórico | Registro 0300: liga a conta a outro produto ou serviço | ID_Conta_Config; ID_Outro_Servico; Descricao_Complementar |
| Cad_Desif_Conta_Exigida | sim, histórico | Quais contas do COSIF o município exige no plano (Módulo 3) e no balancete (Módulo 1): grupo 7, grupo 8 a critério, subtítulo 1.6, desdobramento 1.8.1 e as TJEO do anexo 13 | ID_Municipio; ID_Codigo_Referencial; Exigida_No_Plano; Exigida_No_Balancete; Motivo {grupo_7, grupo_8_criterio, subtitulo_1_6, desdobramento_1_8_1, tjeo_anexo_13} |
| Cad_Desif_Evento_Contabil | sim, histórico | Anexo 1: eventos das partidas (apropriação de receita, estornos, rateios) | Codigo (identidade); Descricao; Tipo_Partida {credito, debito, ambos} |
| Cad_Desif_Tarifa_Bancaria | sim, histórico | Anexo 9: tabela de tarifas do BACEN | Codigo (identidade); Grupo; Descricao; Periodicidade_Dias (0 = por evento) |
| Cad_Desif_Outro_Servico | sim, histórico | Anexo 10: outros produtos e serviços bancários (série 5101 em diante) | Codigo (identidade); Grupo; Descricao; Exige_Descricao_Complementar |
| Cad_Desif_Codigo_Tributacao | sim, histórico | Anexo 6: código de tributação da DES-IF (9 posições, ex. 01.01.01-000) e o subitem da LC 116/2003 | Codigo (identidade); Descricao; Subitem_Lista_Servicos |
| Cad_Desif_Codigo_Tributacao_Municipio | sim, histórico | Anexo 7: código do município, alíquota e vigência (hoje só São Paulo, 289 linhas) | ID_Municipio; Codigo_Municipio; ID_Codigo_Tributacao; Aliquota; Competencia_Inicio; Competencia_Fim (000000 = em aberto) |
| Cad_Desif_Mensagem | sim, histórico | Anexos 11 e 12: código, tipo (L, F, C, R, T, A), registro, mensagem, motivo e solução de cada erro ou alerta (357 códigos, 113 excluídos). O validador grava o código; o texto vem daqui | Codigo (identidade); Natureza {erro, alerta}; Tipo_Critica {leiaute, formatacao, consistencia_simples, consistencia_relacional, transmissao, malha}; Modulo; Registro; Mensagem; Motivo; Solucao; Campos_Anexar; Excluido |

## 5.2 Movimentos (7)

| Entidade | Vigência | Para que serve | Campos principais |
|---|---|---|---|
| Mov_Desif_Declaracao | não | Registro 0000: uma declaração por módulo e competência | ID_Instituicao; ID_Obrigacao (→Cad_Obrigacao_Acessoria); Modulo {1, 2, 3, 4}; Tipo {normal, retificadora}; Competencia_Inicio; Competencia_Fim; Tipo_Consolidacao; ID_Dependencia_Responsavel_Recolhimento; Versao_Leiaute; Tipo_Arredondamento; Origem_Dados {contabilidade_erp, importado}; ID_Escrituracao_Arquivo (→Mov_Escrituracao_Arquivo); Status |
| Mov_Desif_Dependencia | não | Registro 0400 gravado na declaração (retrato da dependência, mais a paralisação do Módulo 2) | ID_Declaracao; ID_Desif_Dependencia; Data_Inicio_Paralisacao; Data_Fim_Paralisacao |
| Mov_Desif_Balancete | não | Registro 0410: balancete analítico mensal por dependência, conta e desdobramento | ID_Declaracao; ID_Dependencia_Declarada; Competencia; Codigo_Conta; Desdobramento; Saldo_Inicial; Debitos; Creditos; Saldo_Final; Codigo_Conta_Superior; Codigo_Cosif; ID_Saldo_Contabil (→Mov_Saldo_Contabil, opcional) |
| Mov_Desif_Apuracao_Subtitulo | não | Registro 0430: receita tributável e ISS por subtítulo | ID_Declaracao; ID_Dependencia_Declarada; Codigo_Subtitulo; Desdobramento; ID_Codigo_Tributacao; Credito_Mensal; Debito_Mensal; Receita_Declarada; Deducao; Descricao_Deducao; Base_Calculo; Aliquota; Incentivo_Fiscal; Descricao_Incentivo; Iss_Retido; Motivo_Nao_Exigibilidade {judicial, administrativa}; Processo_Suspensao |
| Mov_Desif_Iss_Recolher | não | Registro 0440: ISS devido e a recolher, consolidado conforme o tipo de consolidação | ID_Declaracao; ID_Dependencia_Declarada; ID_Codigo_Tributacao; Receita_Consolidada; Deducao_Subtitulo; Deducao_Consolidada; Descricao_Deducao; Base_Calculo; Aliquota; Iss_Devido; Iss_Retido; Incentivo_Subtitulo; Incentivo_Consolidado; Descricao_Incentivo; Valor_A_Compensar; Iss_Recolhido; Motivo_Nao_Exigibilidade; Processo_Suspensao; Iss_A_Recolher; ID_Titulo (→Mov_Titulo) |
| Mov_Desif_Compensacao_Origem | não | Origem do crédito compensado (competência e valor), pagamento a maior de competência anterior | ID_Iss_Recolher; Competencia_Origem; Valor |
| Mov_Desif_Partida | não | Registro 1000: partida de lançamento (Módulo 4 e detalhe de estornos e rateios) | ID_Declaracao; Cnpj_Contabilizacao; ID_Municipio_Contabil; Identificador_Lancamento; Data_Lancamento; Valor_Partida; Codigo_Subtitulo; Tipo_Partida {credito, debito}; ID_Evento; ID_Municipio_Vinculado; Historico; ID_Lancamento_Origem (→Mov_Lancamento) |

# 6. DES-IF: alterações em entidades existentes e dados a carregar

| Onde | O que muda |
|---|---|
| `Mov_Escrituracao_Arquivo` (documento 33) | Campo novo `ID_Documento_Assinado` (p7s atachado), pois o arquivo assinado é distinto do TXT; domínio de `ID_Obrigacao` ganha os quatro módulos e a DeSTDA |
| `Mov_Escrituracao_Arquivo_Ocorrencia` (documento 33) | Campos novos `Codigo_Mensagem` (→Cad_Desif_Mensagem, quando aplicável) e `Num_Linha`; o erro e o alerta do leiaute citam o número da linha |
| `Cad_Obrigacao_Acessoria` | Cinco linhas novas (DESIF_M1 a DESIF_M4 e DESTDA), com vigência |
| `Cad_Plano_Referencial` | Duas edições bacen: COSIF 8 dígitos e COSIF 10 dígitos; a carga vem do anexo 3 (1.432 contas) |
| `Cad_Classe_Sistema` | Domínios novos: tipo_dependencia_desif (7 valores do anexo 8), tipo_consolidacao_desif (4), motivo_nao_exigibilidade_desif (2), canal de entrega do arquivo (aplicativo SEDIF-SN) |
| Carga inicial | Anexo 2 (21 tipos), 1 (eventos), 6 (274 códigos), 7 (289 linhas de São Paulo), 9 (130 tarifas), 10 (46 outros serviços), 11 e 12 (mensagens) e os parâmetros de São Paulo em `Cad_Desif_Parametro_Municipio` |

# 7. DES-IF: regras de geração e validação

Estas são regras do **gerador e do validador** (código), com os valores variáveis em parâmetro. Nada disto cria campo novo além do que a seção 5 já lista.

| Regra | Origem | Onde vive |
|---|---|---|
| Formato do TXT: um arquivo por módulo, UTF-8 sem BOM, campos separados por barra vertical, multivalor por § e subvalor por £; decimal com vírgula, negativo com traço, sem separador de milhar; datas em aaaammdd; primeira linha é o registro 0000 e o número da linha cresce de 1 em 1 | Modelo Conceitual 6.1 e 6.6.1 | Gerador |
| Cálculo do ISS com duas casas, arredondado ou truncado conforme o município (São Paulo trunca) | Modelo Conceitual 6.6.1; FAQ | `Cad_Desif_Parametro_Municipio.Tipo_Arredondamento` |
| O balancete do ERP usa sinal (positivo devedor); a DES-IF pede débito e crédito em valor absoluto. Nas contas do grupo 7 o saldo final é saldo inicial + crédito − débito; nas contas do grupo 1, saldo inicial + débito − crédito | FAQ (EC011); `Mov_Saldo_Contabil` | Gerador (conversão de sinal) |
| O saldo inicial das contas 7 e 8 é zero na primeira competência de cada semestre (janeiro e julho), e os saldos de junho e dezembro são os acumulados **antes** da apuração do resultado | Modelo Conceitual 6.6.9 (campos 7 e 10) | Gerador, usando `Saldo_Final_Antes_Encerramento`; ver pendência P-DESIF-1 |
| Soma hierárquica: débito, crédito, saldo inicial e saldo final de cada conta igual à soma das filhas imediatas (erro EC027) | FAQ; Modelo Conceitual | Validador |
| Cada conta interna corresponde a uma conta COSIF do mesmo nível, e as filhas a filhas do COSIF; só conta analítica do COSIF pode receber mais de uma conta interna | FAQ | Validador, sobre `Cad_Conta_Contabil_Referencial` |
| Conta mista: subtítulo com lançamentos de natureza tributária distinta recebe desdobramento "01", "02"; as contas sem desdobramento levam "00"; reclassificação usa desdobramento "01" (movimento) e "02" (reclassificação), e o R0430 leva só o movimento do mês | FAQ; Modelo Conceitual | `Cad_Desif_Conta_Config` |
| Módulo 3 antes dos demais; ordem cronológica dentro de um módulo, salvo exigência do Fisco; até 12 declarações vigentes do Módulo 3 por ano, cada uma vigora até a próxima | FAQ; Modelo Conceitual | Validador e `Mov_Desif_Declaracao` |
| Declaração sem movimento tributável: R0430 com ao menos um subtítulo de base zero; sem nenhum R0430, o R0440 sai com código de tributação vazio e alíquota 0,00 | FAQ; Modelo Conceitual 4.2.8.1 | Gerador |
| Guia: o ISS a recolher gera o título; "ISS recolhido" só leva o que foi pago antes da guia; na retificação com diferença, a guia nova sai pela diferença | FAQ | `Mov_Desif_Iss_Recolher` e `Mov_Titulo` |
| O DES-IF só declara serviços **prestados**; o ISS retido pela instituição como tomadora segue pela NFS-e, e a guia de ISS próprio é a única que o portal da DES-IF emite | FAQ | Documento 35 (NFS-e do tomador) |

# 8. Efeitos em outros desenhos

| Desenho | Efeito |
|---|---|
| NFS-e (documentos 33 a 35) | O contribuinte obrigado à DES-IF é desobrigado da NFS-e; a emissão eventual não gera crédito (art. 86). `Cad_Desif_Instituicao.Desobrigada_Nfse` alimenta a regra; o crédito do tomador (`Valor_Credito_Tomador`) sai zerado quando o prestador é essa instituição |
| Tesouraria | O ISS a recolher é título a pagar; a diferença de retificação gera título novo |
| Calendário | Entram as quatro obrigações com prazo calculado (dia 10; primeiro dia útil de outubro e de abril; vencimento do ISS de janeiro): documento 38, seção 2 |
| Princípio de Alberto | Nada limita o tipo de cliente: a instituição financeira é uma empresa com `Cad_Desif_Instituicao` ativa; sem essa linha, o módulo não aparece |

# 9. DeSTDA

**O que a página diz (SEFAZ-SP, resumo da página):** declaração mensal de substituição tributária, diferencial de alíquota (ICMS entrada) e antecipação tributária, criada pelo Ajuste SINIEF 12/2015; obrigados: contribuintes paulistas do Simples Nacional (exceto MEI), as microempresas com inscrição estadual em São Paulo e os optantes do Simples de outra UF com inscrição de substituto em São Paulo (IE 800); **dispensa** quando não há valores a declarar no mês; base legal: art. 26 da LC 123/2006, Portaria CAT 23/2016 e Portaria CAT 93/2016 (prorrogação); prazo: até o dia 28 do mês seguinte, ou o primeiro dia útil seguinte; envio pelo aplicativo SEDIF-SN, com login e senha do PFE de pessoa do quadro societário ou contabilista; sem taxa; guias pela GARE e GNRE.

**O que a página não diz:** o leiaute do arquivo ou da digitação no SEDIF-SN, as penalidades, a obrigação nas outras UFs e o calendário de prorrogações. Por isso o desenho é de nível de entidade, sem campo a campo.

| Entidade | Vigência | Para que serve | Campos principais |
|---|---|---|---|
| Cad_Destda_Parametro_Uf | sim, histórico | Regras da DeSTDA por UF, em parâmetro: se a UF exige, prazo, dispensa por valor zero, canal de envio e base legal | ID_Estado (identidade); Exigida; Dia_Entrega; Dispensa_Sem_Valor; Canal {aplicativo_sedif_sn, portal, outro}; Fundamento_Legal; Referencia_Cofre_Credenciais (login do PFE) |
| Mov_Destda_Apuracao_Uf | não | Retrato mensal por filial e UF, por tipo (ST, DIFAL e antecipação), montado dos itens de nota já apurados (`Mov_Apuracao_Tributo_Item`) e não do Bloco E da EFD, que o optante do Simples não escritura | ID_Filial; Competencia; ID_Estado; Tipo {substituicao_tributaria, difal, antecipacao}; Valor_Imposto; Valor_Fcp; ID_Escrituracao_Arquivo (→Mov_Escrituracao_Arquivo); Sem_Valores |
| Mov_Destda_Pagamento | não | Guia que quitou o valor da apuração (GARE ou GNRE), com o título de Tesouraria | ID_Apuracao_Uf; Tipo_Guia {gare, gnre}; Codigo_Receita; Data_Vencimento; Valor; ID_Titulo (→Mov_Titulo) |

Reaproveita: `Mov_Escrituracao_Arquivo` (já cita a DeSTDA no documento 33) para o arquivo, o recibo e a retificação, e `Mov_Simples_Transmissao` para a entrega manual pelo SEDIF-SN, com os valores novos `Origem_Tipo = destda` e `Canal = aplicativo_sedif_sn` (sem entidade nova). O leiaute oficial (Ajuste SINIEF 12/2015 e o manual do SEDIF-SN) falta para gerar o arquivo.

# 10. Pendências e perguntas que ficam

| ID | Pendência | Quem resolve | Se não resolver |
|---|---|---|---|
| P-DESIF-1 | A contabilidade do banco encerra o resultado por semestre (obrigação do COSIF) ou por ano? O gerador zera o saldo inicial de janeiro e julho em qualquer caso, mas o saldo final de junho precisa do valor antes da apuração | Contador | O gerador usa `Saldo_Final_Antes_Encerramento` e zera os semestres |
| P-DESIF-2 | Tipo de consolidação do ISS que São Paulo adota (1 a 4) e se há tipos restritos | Contador ou portal DES-IF | Parâmetro aberto; o FAQ sugere o tipo 2 |
| P-DESIF-3 | Há webservice ou API da DES-IF? O pacote não traz | Alberto (respondida em 12/10/2026: não existe API; o pacote da Prefeitura não traz e o envio é através de arquivos) | Resolvida: entrega manual no portal, com protocolo registrado (documento 46, seção 8.4) |
| P-DESIF-4 | Há cliente instituição financeira em São Paulo agora? Se houver, o Módulo 1 do 1º semestre de 2026 venceu em 01/10/2026 e o Módulo 2 de setembro vence em 10/10/2026, que cai em sábado (a segunda é feriado nacional, então a data prática é terça, 13/10, a confirmar no calendário da Prefeitura) | Alberto | Calendário informativo no doc 38 |
| P-DESTDA-1 | Leiaute oficial da DeSTDA: Ajuste SINIEF 12/2015 e manual do SEDIF-SN (a página não traz) | Alberto | Só entidades, sem arquivo |
| P-DESTDA-2 | Quais UFs além de São Paulo exigem a DeSTDA e com qual prazo | Contador | `Cad_Destda_Parametro_Uf` só com São Paulo |
| P-DESTDA-3 | Penalidades da DeSTDA (a página não lista) | Contador | Sem multa calculada |
| P-DESTDA-4 | Conferir o domínio `sedif.pe.gov.br` citado no resumo da página e abrir o instalador do SEDIF-SN | Equipe, em acesso direto | Não afeta o desenho |

# 11. Fontes e verificação

**Oficiais (enviadas por Alberto em 05/10/2026).** Prefeitura de São Paulo, Secretaria Municipal da Fazenda: DES-IF, Manual Prático do Usuário v1.0 (setembro de 2017), Modelo Conceitual versão 3.1 (Anexo Único da Portaria SF/SUREM nº 9, de 05/02/2025), FAQ v5 (outubro de 2025) e os anexos 1 a 13 da mesma portaria. SEFAZ-SP: página "DeSTDA – Declaração do Simples Nacional" (resumo).

**Verificação feita.** Todas as 24 entidades têm nome único e não colidem com as 543 existentes nem com as propostas dos documentos 33 a 38. As referências a `Cad_Plano_Referencial`, `Cad_Conta_Contabil_Referencial`, `Mov_Saldo_Contabil`, `Cad_Filial`, `Cad_Participante_Inscricao`, `Cad_Municipio`, `Cad_Certificado_Digital`, `Mov_Titulo` e `Cad_Obrigacao_Acessoria` foram conferidas no dicionário atual; `Mov_Escrituracao_Arquivo`, `Mov_Escrituracao_Arquivo_Ocorrencia` e `Mov_Simples_Transmissao` existem só como proposta do documento 33. Contagens dos anexos obtidas por programa sobre o texto extraído dos PDFs.

**O que não foi verificado.** O conteúdo linha a linha dos anexos 11, 12, 3 e 5 (entram como carga); o tipo de consolidação adotado por São Paulo; qualquer coisa além do resumo da página da DeSTDA; (a pergunta sobre webservice foi respondida por Alberto em 12/10/2026: não há API, o envio é por arquivo).

# 12. Decisão que falta

**Posso consolidar?** Isso criaria as 24 entidades, as alterações e a carga da seção 6 no dicionário. Como o desenho depende de `Mov_Escrituracao_Arquivo` (documento 33), a consolidação entra junto com a revisão 3 dos documentos 33 a 37; se você preferir tratar a DES-IF e a DeSTDA à parte, o desenho precisa então incluir essa entidade e a de ocorrências, o que soma duas entidades (26).
