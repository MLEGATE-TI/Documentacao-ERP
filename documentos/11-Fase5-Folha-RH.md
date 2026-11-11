**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 5 · MÓDULO 10**

**Folha & RH**

*Colaborador e vínculo de emprego, verbas e motor de cálculo (mensal,
13º, PLR, pagamento avulso a autônomos), turnos, ponto eletrônico e
banco de horas, férias, migração de bases e históricos, condições de
risco e segurança do trabalho, compliance eSocial (envio de eventos e
caixa de mensagens), transparência salarial (Lei 14.611/2023), categoria
sindical e benefícios, portal do colaborador e tabela salarial*

*Revisão 29 --- consolidação da revisão 38 do dicionário (documentos 200 e 201, com as respostas de Alberto de 10/11/2026): 2 entidades novas (anexo, seção 29); 2 entidades novas do B0b-2 (plano de saúde dos empregados; documento 200).*

*Revisão 28 --- consolidação da revisão 19 do dicionário (documento 90 aprovado por Alberto em 21/10/2026 e decisões do documento 91 respondidas): 2 entidades novas (anexo, seção 28); 3 entidades existentes alteradas; ocorrências do eSocial, indicador da prorrogação noturna e saída do modo de composição da hora extra noturna (documento 90, D-N335 e D-N339).*

*Revisão 27 --- consolidação da revisão 17 do dicionário (documentos 84 a 88, decisões D-N259 a D-N262, D-N264 a D-N266, D-N270 a D-N277, D-N279, D-N291 a D-N294, D-N297 a D-N300, D-N304 a D-N315 e D-N317 a D-N325, aprovadas por Alberto em 20/10/2026): 7 entidades existentes alteradas; parâmetros de jornada por filial, hora extra noturna composta, hora noturna reduzida e hora-aula, cota de pessoa com deficiência derivada e domínios do eSocial (documento 87).*

*Revisão 26 --- consolidação da revisão 15 do dicionário (documento 78, decisões D-N231 a D-N235, aprovadas por Alberto em 19/10/2026): 6 entidades existentes alteradas; sindicato opcional na função, código interno da função, textos de DSR, hora noturna, cota PcD e importação de vínculos (documento 78, D-N233 e D-N234).*

*Revisão 25 --- consolidação da revisão 13 do dicionário (documento 75, decisões D-N215 a D-N224, aprovadas por Alberto em 19/10/2026): 7 entidades novas (anexo, seção 27); 5 entidades existentes alteradas; campos novos do S-2200 no vínculo, no empregador do eSocial e no evento, regra do envio único do S-2200, importação de vínculos igualada ao S-2200, sete entidades novas (anexo) e matrícula única por empregador.*

*Revisão 24 --- consolidação da revisão 12 do dicionário (documento 74, decisões D-N202 a D-N214, aprovadas por Alberto em 19/10/2026): 2 entidades novas (anexo, seção 26); 5 entidades existentes alteradas; função e histórico de função, regra de hora extra com função, hora noturna, tipo_hora_ponto com 7 valores, P-38c (leitura B), multiplicador do valor-hora 5 e limite de faltas do DSR 2.*

*Revisão 23 --- consolidação da revisão 10 do dicionário (documento 69, decisões D-N178 a D-N190, aprovadas por Alberto em 18/10/2026): 5 entidades novas (anexo, seção 25); 3 entidades existentes alteradas. O dicionário passa de 883 para 890 entidades.*

*Revisão 22 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 2 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 21 --- Descanso semanal remunerado e feriado ponte (P-42), por comando "consolidar" de Alberto em 05/10/2026, construída junto com a revisão 51 da Fase 0: quatro entidades novas (Cad_Rh_Tipo_Ausencia, Mov_Rh_Ausencia, Cad_Rh_Parametro_Dsr e Cad_Rh_Feriado_Ponte); Cad_Rh_Verba ganha Reflete_Dsr e ID_Verba_Dsr_Reflexo; Cad_Vinculo_Lotacao ganha ID_Municipio_Trabalho; Cad_Feriado (Fase 0) ganha Natureza e Vale_Descanso_Trabalhista. Base legal: Lei 605/1949 (arts. 5º a 9º), Lei 9.093/1995 (feriados) e o Tema 9 do TST (OJ 394, a partir de 20/03/2023). Seguem em aberto, para o contador: o divisor do valor-hora do mensalista, a origem das horas pagas e a confirmação do limite de duas faltas por semana (Minimo_Faltas_Semana_Perde_Dsr).*

*Revisão 20 --- Correções de nomenclatura da auditoria de 04/10/2026
(documento 29), construída junto com a revisão 49 da Fase 0:
Rh_Declaracao_Transparencia_Salarial e Rh_Plano_Acao_Equidade passam a
Cad_Rh_Declaracao_Transparencia_Salarial e Cad_Rh_Plano_Acao_Equidade
(cadastros com versão e vigência levam o prefixo Cad_, Fase 0, seção 2;
a tabela física da versão passa a
Cad_Rh_Declaracao_Transparencia_Salarial_Versao); campos de referência a
domínio com o prefixo ID_: Cad_Rh_Verba.ID_Categoria_Remuneratoria,
Mov_Rh_Processo_Trabalhista_Contrato.ID_Tipo_Contrato,
Cad_Rh_Beneficio.ID_Tipo_Beneficio (antes Tipo) e
Cad_Rh_Salario_Minimo.ID_Estado (antes UF). Nenhuma entidade nova.*

*Revisão 19 --- Ajustes da Folha da NT 07/2026 do eSocial (documento 28),
construída junto com a revisão 48 da Fase 0: nova
Cad_Vinculo_Horario_Contratual (horário contratual do S-2200 e do
S-2206, com o limite de horas do tempo parcial a partir de 23/11/2026);
Mov_Rh_Ficha_Evento ganha o motivo de afastamento da Tabela 18 e o
infoMesmoMtv do S-2230 (a partir de 26/10/2026); regras datadas de
cargo, CBO e local de trabalho no S-2500; Cad_Rh_Codigo_Incidencia ganha
o tributo pis_pasep e os códigos 23, 24, 27 e 28 do salário-paternidade;
Cad_Rh_Verba ganha ID_Incidencia_Pis_Pasep; Mov_Rh_Folha_Item ganha
Fator_Rubrica; a unidade de pagamento do salário (mensalista e horista)
fica em Cad_Participante_Historico_Salario, na Fase 0.*

*Revisão 18 --- Bloco 5 da validação geral (MIT, DCTFWeb e
recolhimento), construída junto com a revisão 47 da Fase 0, a revisão 19
de Contabilidade & Fiscal e a revisão 13 de Contas a Pagar/Receber:
novas Mov_Esocial_Retorno, Mov_Esocial_Retorno_Cr e
Mov_Esocial_Retorno_Base_Pis_Pasep (os totalizadores S-5011, S-5012 e
S-5501 que alimentam a DCTFWeb); a liquidação da folha deixa de gerar
título de INSS e IRRF retido e lança só a provisão.*

*Revisão 17 --- Bloco 4 da validação geral do dicionário, construída
junto com a revisão 46 da Fase 0, a revisão 18 de Contabilidade & Fiscal
e a revisão 2 da Fase 8 --- Jurídico: novas Cad_Rh_Empregador_Esocial
(S-1000, dados do empregador por vigência) e
Cad_Rh_Empregador_Esocial_Isencao (certificação de entidade
beneficente); Cad_Rh_Estabelecimento_Esocial ganha as regras de raiz de
CNPJ diferente e EFR; Mov_Esocial_Evento.Origem_Tipo ganha
cad_rh_empregador_esocial. A classificação tributária do S-1000 é o
mesmo domínio do R-1000 da Reinf (classificacao_tributaria_contribuinte,
Fase 0), e o rendimento do trabalho declarado no eSocial não gera fato
da Reinf (Contabilidade & Fiscal, seção 21.4).*

*Revisão 16 --- Bloco 3 da validação geral do dicionário (folha e
eSocial, jurídico), construída junto com a revisão 45 da Fase 0 e com o
novo módulo Fase 8 --- Jurídico: tabelas progressivas do INSS e do IRRF
com faixas, vigência e ato legal (Cad_Rh_Tabela_Progressiva, \_Faixa e
Cad_Rh_Parametro_Irrf) e valores iniciais provisórios até a validação de
RH e contador; rubrica alinhada ao S-1010 (Codigo_Rubrica, natureza e
quatro códigos de incidência oficiais em Cad_Rh_Codigo_Incidencia, com
Incide_Inss, Incide_Fgts e Incide_Irrf calculados e armazenados;
ID_Rubrica_Esocial e o domínio rubrica_esocial aposentados);
estabelecimento (S-1005) e lotação tributária (S-1020, com terceiros e
histórico de lotação do vínculo); processo trabalhista completo do
S-2500 e do S-2501 (21 entidades: contrato, observações, remuneração,
mudança de categoria, unicidade, abono, período, trabalho intermitente,
apuração por trabalhador, base, tributo, imposto de renda, advogados,
dedução por dependente, pensão alimentícia e retenção suspensa; 15
acrescentadas na consolidação, depois da conferência com o XSD oficial,
que também corrigiu a remuneração, a origem do processo e a chave do
processo trabalhista), com juízo da decisão apontando para a
movimentação do processo; validação de esquema e certificado em
Mov_Esocial_Evento; Cad_Rh_Escopo_Usuario e
Cad_Rh_Processo_Administrativo_Judicial aposentadas (substituídas por
Cad_Usuario_Escopo e Cad_Processo);
Mov_Rh_Processo_Disciplinar.ID_Processo renomeado
ID_Processo_Disciplinar; Cad_Rh_Pensao_Alimenticia.ID_Processo_Judicial
aponta para Cad_Processo; Cad_Rh_Reajuste_Coletivo.ID_Documento
corrigido para Cad_Documento.*

*Revisão 15 --- construída junto com a revisão 42 da Fase 0: tipo lógico
\"código (n)\" definido por Alberto --- todo campo que identifica algo
(inscrição, documento, agência, conta, número e série de nota,
matrícula, código oficial) é caractere, nunca numérico: os zeros à
esquerda fazem parte do código, e o padrão pode passar a aceitar letras
ou mudar de tamanho, como aconteceu com o CNPJ alfanumérico. Campos
revistos: CPF, Codigo, Matricula, Matricula_Esocial, Numero_Processo,
Numero_Recibo, Sindicato_Cnpj. Competência de Mov_Rh_Folha_Apuracao e
Mov_Rh_Base_Acumulada_Migrada no tipo competência (resíduo do Bloco 1).*

*Revisão 14 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; datas de validade padronizadas para o trio de
vigência (Cad_Rh_Salario_Adicional, Cad_Rh_Tabela_Salarial,
Cad_Rh_Salario_Minimo, Cad_Rh_Limite_Renda_Dependente_Irrf,
Mov_Rh_Beneficio_Adesao_Contribuicao, Mov_Rh_Estabilidade_Provisoria,
Cad_Rh_Pensao_Alimenticia); Cad_Rh_Categoria_Sindical com vigência;
Base_Calculo_Tipo e Parecer_Resultado renomeados; competência na taxa
global de benefício; chaves primárias de nove entidades; CNPJ do
sindicato alfanumérico.*

*Revisão 13 --- migração do controle de período de fechamento da folha
para o mecanismo genérico da Fase 0 (revisão 37), pedida por Alberto
para todos os módulos do dicionário (\"pode migrar para um mecanismo
generalizado porém indicando os blocos e teria que ter para todos os
módulos\"): Cad_Rh_Periodo_Folha (seção 5, revisão 8) é APOSENTADO como
cadastro próprio --- a folha passa a ser a instância
Cad_Bloco_Fechamento.Codigo=\"folha_pagamento\" de
Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial (Fase 0, seção 10),
e Mov_Rh_Folha_Apuracao passa a consultar essa tabela genérica pelo par
Filial+Competência em vez do antigo cadastro dedicado; O COMPORTAMENTO
NÃO MUDA EM NADA --- continua deliberadamente independente do período
contábil (agora simplesmente por serem blocos diferentes,
\"folha_pagamento\" vs \"contabilidade\", sem qualquer relação de
causa/efeito entre eles), continua por filial e continua fail-closed,
mesma regra de sempre (\"o que não está aberto está fechado\", nenhuma
competência sem registro tratada como aberta por omissão) --- só a
estrutura de dados deixa de ser exclusiva da Folha e passa a ser
compartilhada por todos os módulos*

*Revisão 12 --- regime de servidor estatutário (RJU), um segundo regime
de folha em paralelo ao CLT, pedido por Alberto para atender
administração direta/autarquias/fundações públicas, nova seção 20:
categoria de vínculo estatutário/comissionado/temporário
administrativo/inativo; admissão em três etapas
(nomeação/posse/exercício); estágio probatório com avaliações periódicas
e estabilidade automática após homologação (Cad_Rh_Estagio_Probatorio,
distinto de avaliação de desempenho comercial); motivos de vacância
próprios com Aplicavel_Regime; remuneração por subsídio ou
vencimento+vantagens com Fundamento_Legal rastreável; processo
disciplinar/PAD (Mov_Rh_Processo_Disciplinar, distinto de suspensão de
tributos); progressão de carreira por critério legal; e folha de
inativos (aposentados/pensionistas mantidos pela própria folha,
separados dos ativos) --- FGTS isento, previdência RPPS, férias/13º e
jornada reaproveitados sem estrutura nova*

*Revisão 11 --- três ajustes pedidos por Alberto: nova
Cad_Rh_Salario_Adicional + Cad_Rh_Salario_Adicional_Parcela (14º/15º
salário, benefício voluntário ou por convenção coletiva específica, com
parcelamento livre por empresa --- Mov_Rh_Folha_Apuracao ganha
Tipo_Folha=salario_adicional, ID_Salario_Adicional e Numero_Parcela,
seção 5); Cad_Rh_Tabela_Salarial ganha Data_Vigencia_Fim, preenchido
automaticamente ao nascer nova vigência, para agilizar consultas (seção
19); e reajuste coletivo (seção 16) passa a reajustar também os steps da
tabela salarial dos cargos da categoria, no mesmo evento e mesmo
percentual, sujeito ao mesmo piso de salário mínimo (seção 19)*

*Revisão 10 (\"consolidar\") --- rodada extensa de comentários de
Alberto, construída junto com o patch em Fase 0 (revisão 33):
Cad_Rh_Verba_Filial (restrição opcional de verba por filial, seção 5) e
Mov_Rh_Folha_Item.ID_Origem_Ocorrencia (múltiplas ocorrências da mesma
verba por vínculo/apuração, seção 5); nova seção 18, Portal do
Colaborador --- holerite/ponto por autoacesso, pedido de férias com
fluxo de duas etapas (gestor + validação RH, prazo mínimo de
antecedência, urgência com justificativa obrigatória), solicitação de
inclusão de dependente só com validação de RH, e pensão alimentícia com
múltiplos pensionistas simultâneos e redirecionamento por falecimento;
Cad_Participante_Dependente (Fase 0) reformulado por pesquisa extensa de
critérios legais --- IRPF, INSS e salário-família, unificados pela
Tabela 7 do eSocial, com teto de renda de ascendente e regras de
dependente por operadora como parâmetros estruturados;
Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal para empresa
pública/sociedade de economia mista; e nova seção 19, Tabela Salarial
--- cargo × step de valor fixo, quantidade de steps livre por cargo,
grupo ocupacional como classificação*

*Revisão 9 --- uma rodada inteira de comentários de Alberto sobre
transferência, empréstimo e substituição de colaborador, dissídio
coletivo, salário mínimo e benefícios, construída junto com o patch em
Fase 0 (revisão 32): transferência intra-empresa entre filiais
(Cad_Vinculo_Emprego.ID_Filial passa a ser só a filial de admissão,
filial atual derivada de Cad_Participante_Historico_Filial, Fase 0) e
inter-empresa do grupo econômico com continuidade de tempo de serviço
(Cad_Vinculo_Emprego.ID_Vinculo_Origem_Transferencia, novo motivo de
desligamento transferencia_grupo_economico com
Gera_Verbas_Rescisorias=falso); empréstimo temporário entre
departamentos/filiais, com retorno automático
(Tipo_Alocacao/Data_Fim_Prevista, Fase 0); substituição de função com
diferencial salarial fixado explicitamente
(Cad_Participante_Historico_Cargo.Valor_Diferencial, Fase 0, aplicado
por uma verba própria); nova seção 16 --- categoria sindical com
override por cargo, reajuste coletivo escalonado por faixa salarial e
piso de salário mínimo com regional, mecanismo independente do dissídio;
nova seção 17 --- catálogo de benefícios com coparticipação
fixa/percentual distinta por titular/dependente, matching de previdência
privada, e taxa/desconto global da operadora como verba informativa
(Cad_Rh_Verba.Tipo ganha esse terceiro valor) rateada por vidas ou por
valor entre os aderentes*

*Revisão 8 --- três pontos de Cad_Rh_Verba (seção 5) pedidos por
Alberto: (1) amarração por tipo de vínculo --- \"tem verbas que só
incidem sobre estagiario, outras por clt e dai por diante, e tem verbas
que são para mais de um vinculo\" ---, marcação manual verba a verba,
sem restrição quando nenhum tipo é marcado (Cad_Rh_Verba_Tipo_Vinculo);
(2) sequência de cálculo determinada automaticamente pela aplicação a
partir do grafo de dependências entre Formula de verbas, e ARMAZENADA
para não ficar lento (Cad_Rh_Verba.Ordem_Calculo), nunca reprocessada
durante a apuração em si; e (3) controle de período aberto/fechado da
folha, por filial, deliberadamente INDEPENDENTE do período contábil
(Cad_Periodo_Contabil, Fase 0) --- \"como são operadores independentes
estes periodos tem que serem independentes\" ---, fail-closed por
instrução explícita de Alberto: o que não está aberto está fechado,
nenhuma competência sem registro é tratada como aberta por omissão
(Cad_Rh_Periodo_Folha, pré-condição para Mov_Rh_Folha_Apuracao)*

*Revisão 7 --- nova seção 4, Avaliação de Desempenho, pedida por Alberto
depois de ver a entrega da revisão 6 (\"o que senti falta é a parte de
avaliações periódicas de desempenho\"): catálogo de critérios PRÓPRIO
desta seção --- distinto do usado na seleção ---, com Nivel_Pontuacao
{individual, grupo} por critério (Cad_Rh_Criterio_Avaliacao_Desempenho);
ciclos periódicos configuráveis por empresa
(Cad_Rh_Ciclo_Avaliacao_Desempenho); avaliação por vínculo com avaliação
do gestor E autoavaliação do colaborador, mesmo padrão multi-avaliador
já usado na seleção
(Mov_Rh_Avaliacao_Desempenho/Avaliador/Avaliador_Nota); nota de grupo
aplicada de uma vez a todo um departamento
(Mov_Rh_Avaliacao_Desempenho_Grupo_Nota); metas estruturalmente
separadas dos critérios, por colaborador ou por cargo
(Cad_Rh_Meta_Desempenho/Mov_Rh_Meta_Desempenho_Resultado); e uma
pontuação final ponderada por vínculo+ciclo, combinando critérios e
metas pelos pesos de cada catálogo, calculada uma vez e armazenada no
fechamento (Mov_Rh_Avaliacao_Desempenho.Nota_Final_Ponderada)*

*Revisão 6 --- nova seção 2, Recrutamento e Seleção, pedida por Alberto
ao perguntar onde estava a parte de \"contratação\": vaga (Cad_Rh_Vaga,
com cargo agora cadastrado na própria empresa via Cad_Rh_Cargo --- não
mais texto livre --- régua de aprovação sempre opcional, e referência
direta ao compromisso orçamentário de Planejamento & Orçamento, fechando
um gancho do Documento Analítico); candidatura, etapas e avaliação
(Mov_Rh_Vaga_Candidato/Cad_Rh_Etapa_Selecao/Mov_Rh_Vaga_Candidato_Etapa,
com múltiplos avaliadores por etapa --- cada um com parecer e
recomendação próprios --- e lista de critérios pontuados); checklist de
documentos de contratação configurável por empresa, com itens
obrigatórios e opcionais
(Cad_Rh_Checklist_Documento/Mov_Rh_Candidato_Documento); retenção de
dados de candidato sob a LGPD, só com consentimento explícito --- sem
consentimento, eliminação no encerramento do processo ---, prazo
parametrizável por empresa (Cad_Rh_Politica_Retencao_Candidato) e alerta
ao usuário quando configurado acima de 24 meses; separação de equipe
dentro do RH (recrutamento/seleção distinto de folha/treinamento) via
Cad_Usuario_Escopo (restrição do tipo area_rh), com acesso a mais de uma
área por configuração; e Tipo_Vinculo ganhou pro_labore, com processo
seletivo sempre opcional independente do tipo de vínculo --- construído
junto com o patch em Fase 0 (revisão 31:
Cad_Participante_Historico_Cargo migrado para Cad_Rh_Cargo, campos de
consentimento/descarte em Cad_Pre_Cadastro, ID_Vaga_Candidato em
Mov_Pre_Cadastro_Conversao, abertura_vaga em Mov_Aprovacao_Instancia)*

*Revisão 5 --- quatro pontos pedidos por Alberto: abono simples de
falta/atraso pelo gestor, sem régua de aprovação, por haver vários
níveis de gestor independentes (Mov_Rh_Ponto_Abono, seção 6); completude
da rescisão --- prazo legal de pagamento (art. 477 §6º),
TRCT/homologação via GED, Exame Demissional e quitação de banco de horas
na rescisão (Origem_Tipo=quitacao_rescisao); óbito como motivo de
desligamento, com nexo com acidente de trabalho apurado via pesquisa de
eSocial/legislação (CAT original/reabertura/comunicação de óbito,
isenção da multa do art. 477, tratamento de IRRF e FGTS próprios) e
beneficiário do óbito modelado
(ID_Participante_Beneficiario_Obito/Qualificacao_Recebedor,
Cad_Vinculo_Emprego); e a folha passando a gerar título a pagar de
verdade e arquivo bancário real para todas as obrigações que ela apura
--- não só salário, também INSS/FGTS/IRRF --- com a tesouraria
confirmando o fiel depositário em caso de óbito e a visibilidade de RH
sobre pagamentos não processados (seção 14) --- construído junto com o
patch em Fase 0 (revisão 30, conta-salário) e a consolidação de Contas a
Pagar/Receber (revisão 8) e Tesouraria (revisão 5)*

*Revisão 4 --- verificação de compliance com legislação trabalhista
(CLT), Manual de Orientação do eSocial (MOS) e Lei 14.611/2023
(Igualdade Salarial), pedida por Alberto: vínculo (Tipo_Vinculo
estendido com intermitente/safrista/cooperado, prazo determinado
prorrogável/efetivável, teletrabalho x controle de jornada, agente de
integração, aviso prévio, motivo de desligamento com fatores de cálculo,
estabilidade provisória, processo administrativo/judicial); ficha do
colaborador (PCD/cotista e ausência legal justificada como eventos,
responsabilidade INSS em afastamento longo); banco de horas (prazo legal
de compensação com pagamento incondicional); sobreaviso e ambiente de
trabalho (S-1060/S-2240); verbas (média de férias/13º desmembrada,
categoria remuneratória); e nova seção de compliance com a Lei
14.611/2023 --- patch correspondente em Fase 0, revisão 29 (CNAE,
NIRE/Junta Comercial, PAIC/Obra e Medição, responsáveis/contador/sócios,
sexo/cor-raça, indicador de liderança)*

*Revisão 2 --- dez comentários pós-entrega de Alberto incorporados:
matrícula eSocial separada da matrícula interna; histórico de
reprocessamento de folha nunca sobrescrito, com \"último processamento\"
e \"processamento contabilizado\" sempre como consulta; controle de GAP
na apuração de ponto (nunca pareando marcações de dias de referência
diferentes); banco de horas como alternativa a pagar a hora extra,
decidido caso a caso, com saldo sempre derivado e visão por gestor do
colaborador; adiantamento da 1ª parcela do 13º junto com as férias; base
histórica de variáveis (horas extras/comissões) para a média de
férias/13º explicitada na migração; condições de risco ---
insalubridade, periculosidade, agentes ambientais --- por cargo e por
área, sobrepostas, alimentando o eSocial (S-2240) e as verbas
correspondentes automaticamente; adicional noturno derivado da apuração
de ponto; e pagamento avulso a autônomos (RPA) como tipo próprio de
apuração, fora do calendário mensal*

*Revisão 1 --- especificação inicial do módulo, a partir dos comentários
de Alberto: camada de envio ao eSocial genérica e extensível a novos
tipos de evento; caixa de mensagem do eSocial como controle
independente; migração trazendo não só bases acumuladas mas também
histórico real (ex. férias) de um sistema anterior; motor de cálculo
completo incluindo provisões, 13º e uma folha específica de PLR; e ponto
eletrônico como estrutura própria, independente do Timesheet, com
turnos/escalas cruzando a marcação*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o módulo de Folha & RH, no mesmo formato usado
nos nove módulos já entregues: função e dados juntos, entidade por
entidade, sempre referenciando os motores transversais da Fase 0
(Cad_Participante, Cad_Classe_Sistema, Cad_Dimensao_Contabil_Valor,
Cad_Filial, Cad_Regua_Aprovacao, Cad_Usuario) em vez de redefini-los.
Segue a ordem do Documento Analítico (Fase 5, \"Pessoas\") --- Alberto
escolheu este módulo como próximo passo depois de fechar os comentários
pendentes sobre Ativo Imobilizado, Condição do Estoque/Rejeição e rateio
de frete por pedido.

O Documento Analítico já trazia um esboço conceitual desta área,
reaproveitado aqui como ponto de partida: \"O colaborador é um
participante com classe própria dentro do cadastro único, com matrícula
por vínculo --- permitindo desligar e recontratar sem perder o histórico
da pessoa. A ficha do colaborador concentra tudo --- exames, vacinas,
afastamentos, viagens, e agora também acidentes de trabalho --- com cada
tipo de evento mapeado ao código correspondente do eSocial, e um
atributo próprio indicando se o envio deve ser imediato ou pode esperar
o fechamento da folha. Verbas são tipificadas e configuráveis por
fórmula por empresa, com detecção de dependência circular na ordem de
cálculo, e agora carregam também um atributo de origem --- legal ou
interna --- que também governa nível de acesso, sempre por vigência,
nunca por sobrescrita direta. O ponto eletrônico cruza marcações com o
horário contratual para identificar falta/atraso/hora extra, sempre
sugerindo, nunca aplicando automaticamente o preenchimento de lacunas de
marcação.\" Este documento formaliza esse esboço em entidades concretas
e adiciona o que faltava: vínculo de emprego, motor de apuração de
folha, turnos/escalas, férias, migração de sistema anterior e a camada
de compliance eSocial (envio de eventos e caixa de mensagens).

A Fase 0 já continha três placeholders pensados especificamente para
este momento, criados antes de qualquer módulo de RH existir:
Cad_Participante_Classe (classe funcionário),
Cad_Participante_Historico_Cargo/Departamento/Salario e
Cad_Participante_Dependente. Este documento reaproveita as quatro sem
redefini-las --- só patcheia as três primeiras (Fase 0, revisão 27) para
escopá-las por vínculo de emprego, entidade que nasce aqui (seção 3).
Mov_Pre_Cadastro_Conversao (Fase 0, seção 7) também é reaproveitado tal
como está: o evento de conversão de um Cad_Pre_Cadastro em
Cad_Participante já registra o histórico de entrevistas/avaliações que
passa a compor a Ficha do Colaborador (seção 12).

*Assunção de escopo desta revisão, explícita para sua confirmação: este
documento modela a ESTRUTURA de dados de compliance eSocial (evento
genérico, extensível, com status de envio/protocolo, e caixa de mensagem
independente) e da migração (bases acumuladas e histórico trazido de
sistema anterior), mas NÃO modela o layout XML de cada evento eSocial
nem a integração técnica de transmissão em si (protocolo, certificado
digital, ambiente de homologação/produção) --- isso é responsabilidade
de uma camada de aplicação que consome Mov_Esocial_Evento, mesma
filosofia já usada para CNAB/API bancária em Tesouraria. Também não
modela as tabelas de parâmetro legal em si (alíquotas de INSS por faixa,
tabela de IRRF, teto de FGTS) --- ficam como parametrização
(Cad_Rh_Verba.Formula, seção 5), não como estrutura fixa deste
dicionário, porque mudam por lei, não por decisão da Mlegate.*

2\. Recrutamento e Seleção

Nova seção nesta revisão (6), pedida por Alberto ao perguntar onde
estava a parte de \"contratação\" do módulo: até a revisão 5, o único
suporte existente era o par genérico
Cad_Pre_Cadastro/Mov_Pre_Cadastro_Conversao (Fase 0), reaproveitado de
CRM & Vendas, sem nenhum processo estruturado de vaga, candidatura,
entrevista ou checklist de admissão --- e o gancho de aprovação de
contratação com compromisso orçamentário, já citado no Documento
Analítico, nunca havia sido formalizado (registrado como ponto em aberto
nas Notas desde a revisão 4).

Alberto foi explícito em duas condições estruturais para este desenho:
(1) recrutamento/seleção é uma equipe DIFERENTE, dentro do RH, da equipe
de processamento de folha e de treinamento/desenvolvimento --- \"equipes
diferentes\... se fundem em algum momento\" --- resolvido reaproveitando
o mesmo mecanismo de escopo por usuário já existente
(Cad_Usuario_Escopo, seção 14), que ganhou uma dimensão extra
(ID_Area_Rh); um colaborador pode acumular acesso a mais de uma área de
RH, por configuração, sem exigir uma segunda tabela de controle de
acesso; (2) todo candidato aprovado precisa de um checklist de
documentos necessários para contratação --- com os documentos em si
salvos ---, checklist esse configurável por empresa (\"pode ser
maior\... pode ser menor\") e com itens obrigatórios e opcionais.

Vaga e processo seletivo são sempre OPCIONAIS por trás de uma
contratação, independente do Tipo_Vinculo --- Alberto corrigiu uma
suposição inicial minha de que pró-labore normalmente nasceria de
contratação direta: \"posso fazer seleção para um pró-labore, tem
pessoas que vão passar por processo seletivo e outras vão para
contratação direta\". Não há, portanto, amarração estrutural entre tipo
de vínculo e obrigatoriedade de vaga: qualquer Cad_Vinculo_Emprego,
inclusive pro_labore (seção 3), pode nascer com ou sem um
Mov_Rh_Vaga_Candidato por trás.

Cad_Rh_Cargo

O cargo cadastrado na própria empresa --- Alberto foi explícito: \"o
cargo tem que estar cadastrado na folha\". Substitui, nesta revisão, o
texto livre que existia em Cad_Participante_Historico_Cargo (Fase 0)
desde a revisão 27; é definido aqui, antes de Cad_Rh_Vaga, porque toda
vaga referencia um cargo já cadastrado.

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: nome, CBO ou nível de
liderança de um cargo podem ser revisados, nova versão nunca
sobrescreve, preservando o histórico de quem foi classificado sob qual
versão.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Cargo** | *identificador* | --- |
| **ID_Cargo_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Rh_Cargo_Versao). ID_Cargo é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa)* | Cargo é cadastrado por empresa --- mesmo critério já usado em Cad_Rh_Verba: a mesma denominação de cargo pode ter nome, CBO ou nível de liderança diferente entre empresas do mesmo grupo. |
| **Nome** | *texto* | Nome do cargo na empresa --- ex.: \"Analista Fiscal Pleno\". |
| **ID_Cbo** | *referência (Cad_Classe_Sistema, domínio = cbo, opcional)* | Migrado de Cad_Participante_Historico_Cargo (Fase 0, revisão 31) --- o código da Classificação Brasileira de Ocupações correspondente, exigido pelo evento de admissão do eSocial (S-2200). Revisão 13 (documento 75): obrigatório quando o cargo vai no S-2200 (exceto cargo em comissão por nomeação). |
| **Nivel_Lideranca** | *booleano* | Migrado de Cad_Participante_Historico_Cargo (Fase 0, revisão 31) --- verdadeiro quando este cargo, nesta janela de vigência, é de liderança/gerência/chefia, usado pelo relatório de transparência salarial da Lei 14.611/2023 (seção 15). |
| **ID_Categoria_Sindical** | *referência (Cad_Rh_Categoria_Sindical, seção 16, opcional)* | Adicionado nesta revisão (9), pedido pela especificação de dissídio coletivo (seção 16, abaixo): preenchido só quando ESTE cargo tem enquadramento sindical diferente do padrão da filial --- Alberto: \"pode ter um grupo de colaboradores, pela função pode ter um outro sindicato, não é comum mas pode acontecer\". Vazio na grande maioria dos cargos, que seguem o padrão da filial (Cad_Filial.ID_Categoria_Sindical_Padrao, Fase 0); quando preenchido, prevalece sobre o padrão da filial --- mesmo princípio \"mais específico vence o mais genérico\" já usado no Motor de Regras (Fase 0, seção 8). Revisão 15 (D-N233): a função também pode ter enquadramento próprio (Cad_Rh_Funcao.ID_Categoria_Sindical) e, quando tem, prevalece sobre o do cargo. |
| **ID_Grupo_Tabela_Salarial** | *referência (Cad_Rh_Tabela_Salarial_Grupo, seção 19, opcional)* | Adicionado nesta revisão (10), pedido por Alberto (\"podemos ter uma tabela salario, que tem os cargos, e steps salariais\"): classifica este cargo dentro de um grupo ocupacional da tabela salarial da empresa (ex.: executivos/diretoria, administrativo, universitários, operacional) --- vazio quando a empresa não usa tabela salarial, ou quando este cargo específico fica fora dela. A classificação em grupo é só organizacional: os steps e seus valores (Cad_Rh_Tabela_Salarial_Step, seção 19) são definidos por CARGO, não por grupo --- Alberto foi explícito: \"um cargo pode ter 7 steps e outro só 2\". |
| **Fundamento_Legal** | *texto, opcional* | Adicionado nesta revisão (12), da pesquisa sobre servidor estatutário (seção 20): a lei que criou o cargo --- relevante para plano de cargos e carreira de servidor estatutário (ex.: \"Lei Municipal nº X/ano\"), mas campo genérico, não exclusivo do regime estatutário --- qualquer cargo CLT pode preenchê-lo se a Mlegate quiser rastrear a origem legal. |
| **Ativo** | *booleano* | --- |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 13 --- campos alterados: ID_Cbo.*

*Revisão 15 --- campos alterados: ID_Categoria_Sindical.*

Cad_Rh_Vaga

Uma posição em aberto, o ponto de partida do processo seletivo --- ou,
quando não há processo seletivo, apenas o registro do cargo/motivo que
sustenta uma contratação direta.

*Vigência: não --- é um registro de processo, com Status próprio
cobrindo o ciclo de vida; mesmo critério já usado em Cad_Obra (Fase 0).*

  ---------------------------------------- ----------------------------------- ------------------------------------------------------
  **Campo**                                **Tipo lógico**                     **Descrição / regra**

  **ID_Vaga**                              *identificador*                     ---

  **ID_Empresa**                           *referência (Cad_Empresa)*          ---

  **ID_Filial**                            *referência (Cad_Filial, opcional)* ---

  **ID_Departamento**                      *referência                         Mesma dimensão já reaproveitada por
                                           (Cad_Dimensao_Contabil_Valor,       Cad_Participante_Historico_Departamento (Fase 0) e por
                                           dimensão = Departamento)*           Cad_Usuario_Escopo (seção 14).

  **ID_Cargo**                             *referência (Cad_Rh_Cargo)*         Obrigatório --- fecha o gap identificado por Alberto:
                                                                               toda vaga nasce de um cargo já cadastrado, nunca de
                                                                               texto livre.

  **Nome_Vaga**                            *texto*                             Nome livre da vaga (ex.: \"Analista Fiscal Pleno ---
                                                                               Sênior de Impostos Indiretos\") --- confirmado por
                                                                               Alberto como texto livre, distinto do cargo formal em
                                                                               si, que pode ser reaproveitado por várias vagas com
                                                                               nomes de anúncio diferentes.

  **Tipo_Vinculo_Previsto**                *enumeração (mesmo domínio de       O tipo de vínculo previsto para esta vaga, inclusive
                                           Cad_Vinculo_Emprego.Tipo_Vinculo,   pro_labore --- informativo; o Tipo_Vinculo definitivo
                                           seção 3)*                           só se fixa na admissão (Cad_Vinculo_Emprego).

  **Quantidade_Posicoes**                  *número*                            Quantas posições esta vaga cobre --- mesmo raciocínio
                                                                               já citado no Documento Analítico e em
                                                                               Mov_Compromisso_Orcamentario.Quantidade_Comprometida
                                                                               (Fase 1 --- Planejamento & Orçamento): \"uma
                                                                               contratação aprovada consome 1 vaga\".

  **ID_Participante_Gestor_Solicitante**   *referência (Cad_Participante)*     O gestor que solicitou a abertura da vaga.

  **Status**                               *enumeração {aberta, em_selecao,    Decidido pela equipe de recrutamento, nunca derivado
                                           preenchida, cancelada, suspensa}*   automaticamente do andamento das candidaturas (mesmo
                                                                               princípio \"sugere, nunca aplica automaticamente\" já
                                                                               usado em outras máquinas de estado deste dicionário).

  **ID_Instancia_Aprovacao**               *referência                         Origem_Tipo=abertura_vaga (Fase 0, revisão 31). Régua
                                           (Mov_Aprovacao_Instancia, Fase 0,   SEMPRE OPCIONAL --- Alberto foi explícito: \"sim régua
                                           opcional)*                          de aprovação opcional\", nem toda vaga precisa passar
                                                                               por aprovação formal; vazio quando a vaga não exige
                                                                               régua.

  **ID_Compromisso_Orcamentario**          *referência                         Fecha o gancho deixado em aberto desde a revisão 4
                                           (Mov_Compromisso_Orcamentario, Fase (citado nas Notas): aquele módulo já continha um
                                           1 --- Planejamento & Orçamento,     comentário premonitório em Quantidade_Comprometida
                                           opcional)*                          (\"uma contratação aprovada consome 1 vaga contra o
                                                                               Quantidade_Orcada daquele centro de custo/mês\") sem
                                                                               nenhuma entidade de RH que de fato o disparasse ---
                                                                               esta referência é esse disparo.
  ---------------------------------------- ----------------------------------- ------------------------------------------------------

Mov_Rh_Vaga_Candidato

A candidatura de um candidato (Cad_Pre_Cadastro, Origem=rh_candidato) a
uma vaga específica --- relação N:N: o mesmo candidato pode se
candidatar a mais de uma vaga ao longo do tempo, e a mesma vaga recebe
candidaturas de vários candidatos. É movimentação --- o evento de
candidatura --- não cadastro.

*Vigência: não. O status final do candidato NESTA vaga nunca é um campo
armazenado aqui --- é sempre derivado da etapa mais recente em
Mov_Rh_Vaga_Candidato_Etapa, abaixo, mesmo princípio de nunca guardar o
que pode ser derivado já usado em todo o dicionário (ex.: apuração de
falta/atraso, seção 6).*

  ----------------------- -------------------- ----------------------------------------
  **Campo**               **Tipo lógico**      **Descrição / regra**

  **ID_Vaga_Candidato**   *identificador*      ---

  **ID_Vaga**             *referência          ---
                          (Cad_Rh_Vaga)*       

  **ID_Pre_Cadastro**     *referência          ---
                          (Cad_Pre_Cadastro,   
                          Fase 0)*             

  **Data_Candidatura**    *data*               ---
  ----------------------- -------------------- ----------------------------------------

Cad_Rh_Etapa_Selecao

O catálogo, configurável por empresa, das etapas que um processo
seletivo pode ter --- ex.: triagem, entrevista RH, entrevista gestor,
teste técnico, proposta --- extensível sem alterar estrutura, mesmo
padrão catálogo+ocorrência já usado em
Cad_Rh_Tipo_Evento_Ficha/Mov_Rh_Ficha_Evento (seção 12).

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: uma etapa pode ser
descontinuada sem apagar o histórico de processos que já passaram por
ela.*

  --------------------- ----------------- ----------------------------------------
  **Campo**             **Tipo lógico**   **Descrição / regra**

  **ID_Etapa**          *identificador*   ---

  **ID_Etapa_Versao**   *identificador da Chave primária da versão (tabela física
                        versão*           Cad_Rh_Etapa_Selecao_Versao). ID_Etapa é
                                          a identidade, única e referenciada pelas
                                          outras tabelas; cada versão guarda a sua
                                          janela de vigência --- Fase 0, seção 2.

  **ID_Empresa**        *referência       ---
                        (Cad_Empresa)*    

  **Nome**              *texto*           ---

  **Ordem**             *número*          Sequência sugerida das etapas ---
                                          orientativa; nada impede a aplicação de
                                          pular ou repetir uma etapa para um
                                          candidato específico.

  **Ativo**             *booleano*        ---

  **Vigencia_Inicio**   *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**      *data*            Último dia em que esta versão vale
                                          (inclusive). Sempre preenchida:
                                          31/12/9999 quando o fim é indefinido
                                          (versão vigente) --- convenção da Fase
                                          0, seção 2.

  **Motivo_Vigencia**   *texto, opcional* Por que esta versão foi criada.
  --------------------- ----------------- ----------------------------------------

Mov_Rh_Vaga_Candidato_Etapa

A ocorrência de um candidato passando por uma etapa do processo seletivo
--- cabeçalho da etapa; quem efetivamente avalia (podendo ser mais de
uma pessoa) fica em Mov_Rh_Vaga_Candidato_Etapa_Avaliador, abaixo. É
movimentação.

*Vigência: não.*

  ----------------------------- -------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**            **Descrição / regra**

  **ID_Vaga_Candidato_Etapa**   *identificador*            ---

  **ID_Vaga_Candidato**         *referência                ---
                                (Mov_Rh_Vaga_Candidato)*   

  **ID_Etapa**                  *referência                ---
                                (Cad_Rh_Etapa_Selecao)*    

  **Data_Etapa**                *data*                     ---

  **Resultado**                 *enumeração {em_andamento, Decidido pelo RH --- informado pelos
                                aprovado, reprovado,       pareceres individuais de
                                desistencia}*              Mov_Rh_Vaga_Candidato_Etapa_Avaliador,
                                                           abaixo, mas nunca derivado/aplicado
                                                           automaticamente deles: mesmo princípio
                                                           \"sugere, nunca aplica automaticamente\"
                                                           já usado para o ponto eletrônico (seção
                                                           6).

  **Observacao**                *texto*                    ---
  ----------------------------- -------------------------- ----------------------------------------

Mov_Rh_Vaga_Candidato_Etapa_Avaliador

Adicionado nesta revisão, pedido por Alberto: uma etapa (ex.:
entrevista) pode ter mais de um entrevistador, cada um com seu próprio
parecer --- uma linha por avaliador dentro da mesma etapa.

*Vigência: não.*

  --------------------------------------- -------------------------------- ----------------------------------------
  **Campo**                               **Tipo lógico**                  **Descrição / regra**

  **ID_Vaga_Candidato_Etapa_Avaliador**   *identificador*                  ---

  **ID_Vaga_Candidato_Etapa**             *referência                      ---
                                          (Mov_Rh_Vaga_Candidato_Etapa)*   

  **ID_Participante_Avaliador**           *referência (Cad_Participante)*  O entrevistador/avaliador ---
                                                                           colaborador da Mlegate.

  **Parecer**                             *texto*                          O parecer individual deste avaliador.

  **Recomendacao**                        *enumeração {recomenda,          A recomendação individual --- o
                                          recomenda_com_ressalva,          Resultado do cabeçalho da etapa (acima)
                                          nao_recomenda}*                  é decidido pelo RH considerando estas
                                                                           recomendações, nunca calculado
                                                                           automaticamente delas (ex.: maioria,
                                                                           média).
  --------------------------------------- -------------------------------- ----------------------------------------

Cad_Rh_Criterio_Avaliacao

O catálogo, configurável por empresa e opcionalmente por etapa, dos
pontos avaliados numa entrevista --- ex.: comunicação, conhecimento
técnico, fit cultural --- pedido por Alberto (\"lista de pontos
avaliados na entrevista com pontos\"). Mesmo padrão catálogo+ocorrência
de Cad_Rh_Etapa_Selecao, acima.

*Vigência: sim --- mesmo padrão de Cad_Rh_Etapa_Selecao.*

  ------------------------ ------------------------ ----------------------------------------
  **Campo**                **Tipo lógico**          **Descrição / regra**

  **ID_Criterio**          *identificador*          ---

  **ID_Criterio_Versao**   *identificador da        Chave primária da versão (tabela física
                           versão*                  Cad_Rh_Criterio_Avaliacao_Versao).
                                                    ID_Criterio é a identidade, única e
                                                    referenciada pelas outras tabelas; cada
                                                    versão guarda a sua janela de vigência
                                                    --- Fase 0, seção 2.

  **ID_Empresa**           *referência              ---
                           (Cad_Empresa)*           

  **ID_Etapa**             *referência              Vazio = critério aplicável a qualquer
                           (Cad_Rh_Etapa_Selecao,   etapa; preenchido = critério específico
                           opcional)*               daquela etapa (ex.: um critério de
                                                    \"aderência técnica\" só faz sentido na
                                                    etapa de teste técnico).

  **Nome**                 *texto*                  ---

  **Ativo**                *booleano*               ---

  **Vigencia_Inicio**      *data*                   Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*                   Último dia em que esta versão vale
                                                    (inclusive). Sempre preenchida:
                                                    31/12/9999 quando o fim é indefinido
                                                    (versão vigente) --- convenção da Fase
                                                    0, seção 2.

  **Motivo_Vigencia**      *texto, opcional*        Por que esta versão foi criada.
  ------------------------ ------------------------ ----------------------------------------

Mov_Rh_Vaga_Candidato_Etapa_Avaliador_Nota

A nota de um avaliador, num critério específico, dentro de uma etapa ---
a lista de pontos avaliados com pontuação pedida por Alberto. É
movimentação.

*Vigência: não.*

  --------------------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                               **Tipo lógico**                           **Descrição / regra**

  **ID_Vaga_Candidato_Etapa_Avaliador**   *referência                               ---
                                          (Mov_Rh_Vaga_Candidato_Etapa_Avaliador)   
                                          --- chave primária (composta)*            

  **ID_Criterio**                         *referência (Cad_Rh_Criterio_Avaliacao)   ---
                                          --- chave primária (composta)*            

  **Nota**                                *número*                                  Escala definida pela camada de aplicação
                                                                                    (ex.: 1 a 5, 1 a 10) --- não travada
                                                                                    neste dicionário, mesmo critério de
                                                                                    parametrização livre já usado alhures
                                                                                    (ex.: Cad_Rh_Condicao_Risco.Percentual,
                                                                                    seção 13).
  --------------------------------------- ----------------------------------------- ----------------------------------------

*Reaproveitamento de candidato/entrevista entre vagas: confirmado por
Alberto --- \"pode ser que não atenda a vaga atual, mas aparecer outra
vaga que se encaixe, se aproveita da entrevista\". Já estruturalmente
suportado sem campo adicional: Cad_Pre_Cadastro (Fase 0) é um cadastro
de PESSOA, independente de qualquer vaga específica, e
Mov_Rh_Vaga_Candidato é a relação N:N entre pessoa e vaga --- o mesmo
Cad_Pre_Cadastro pode acumular candidaturas (Mov_Rh_Vaga_Candidato) e
entrevistas (Mov_Rh_Vaga_Candidato_Etapa/Avaliador/Nota) a mais de uma
vaga ao longo do tempo, cada conjunto preservado por candidatura,
disponível para consulta quando uma nova vaga surgir.*

Cad_Rh_Checklist_Documento

O catálogo, configurável por empresa, dos documentos necessários para
contratação --- pedido central de Alberto: \"para algumas empresas pode
ser maior e para outras serem menores\", com itens obrigatórios e
opcionais.

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: a lista de documentos
exigidos por uma empresa pode mudar ao longo do tempo, sem invalidar o
checklist já aplicado a uma contratação em andamento.*

  ----------------------------------- ----------------------------------- ----------------------------------------
  **Campo**                           **Tipo lógico**                     **Descrição / regra**

  **ID_Checklist_Documento**          *identificador*                     ---

  **ID_Checklist_Documento_Versao**   *identificador da versão*           Chave primária da versão (tabela física
                                                                          Cad_Rh_Checklist_Documento_Versao).
                                                                          ID_Checklist_Documento é a identidade,
                                                                          única e referenciada pelas outras
                                                                          tabelas; cada versão guarda a sua janela
                                                                          de vigência --- Fase 0, seção 2.

  **ID_Empresa**                      *referência (Cad_Empresa)*          ---

  **Nome_Documento**                  *texto*                             Ex.: RG, CPF, comprovante de residência,
                                                                          carteira de trabalho, diploma, exame
                                                                          admissional, antecedentes.

  **Tipo_Vinculo_Aplicavel**          *enumeração (mesmo domínio de       Vazio = aplicável a qualquer tipo de
                                      Cad_Vinculo_Emprego.Tipo_Vinculo,   vínculo; preenchido = documento
                                      opcional)*                          específico daquele tipo (ex.: um
                                                                          documento societário só faz sentido para
                                                                          pro_labore).

  **Obrigatorio**                     *booleano*                          Confirmado por Alberto: existem
                                                                          documentos obrigatórios e opcionais
                                                                          dentro da mesma lista.

  **Ativo**                           *booleano*                          ---

  **Vigencia_Inicio**                 *data*                              Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                    *data*                              Último dia em que esta versão vale
                                                                          (inclusive). Sempre preenchida:
                                                                          31/12/9999 quando o fim é indefinido
                                                                          (versão vigente) --- convenção da Fase
                                                                          0, seção 2.

  **Motivo_Vigencia**                 *texto, opcional*                   Por que esta versão foi criada.
  ----------------------------------- ----------------------------------- ----------------------------------------

Mov_Rh_Candidato_Documento

A ocorrência de um item do checklist para um candidato específico ---
nasce quando o candidato é aprovado na etapa final do processo seletivo
(ou, em contratação direta, quando a admissão é iniciada). É
movimentação.

*Vigência: não. O arquivo do documento em si reaproveita o GED já
existente (Cad_Documento_Vinculo, Fase 0), sem campo de arquivo
duplicado aqui --- mesmo padrão já usado para RG/CTPS em
Cad_Vinculo_Emprego e para os demais anexos deste módulo (seção 18).*

  ------------------------------- ------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                 **Descrição / regra**

  **ID_Candidato_Documento**      *identificador*                 ---

  **ID_Vaga_Candidato**           *referência                     Quando a contratação vem de processo
                                  (Mov_Rh_Vaga_Candidato)*        seletivo. Em contratação direta (sem
                                                                  vaga), o checklist se liga diretamente
                                                                  ao Cad_Pre_Cadastro do candidato ---
                                                                  mesma tabela, campo alternativo
                                                                  simétrico a ID_Vaga_Candidato.

  **ID_Checklist_Documento**      *referência                     ---
                                  (Cad_Rh_Checklist_Documento)*   

  **Status**                      *enumeração {pendente,          ---
                                  recebido, aprovado, rejeitado}* 

  **ID_Participante_Validador**   *referência (Cad_Participante,  Quem validou/rejeitou o documento
                                  opcional)*                      recebido.

  **Observacao**                  *texto*                         ---
  ------------------------------- ------------------------------- ----------------------------------------

*Comportamento de aplicação --- instanciação do checklist: quando um
candidato é aprovado na etapa final
(Mov_Rh_Vaga_Candidato_Etapa.Resultado=aprovado na última etapa do
processo), a camada de aplicação instancia automaticamente um
Mov_Rh_Candidato_Documento por linha vigente do checklist da empresa
aplicável ao Tipo_Vinculo_Previsto da vaga --- cada item nascendo
Status=pendente. A conversão do candidato em colaborador efetivo
(Mov_Pre_Cadastro_Conversao, Fase 0) fica condicionada, por regra de
aplicação --- não estrutural ---, a todos os itens com
Obrigatorio=verdadeiro estarem Status=aprovado; itens opcionais não
bloqueiam a conversão.*

Cad_Rh_Politica_Retencao_Candidato

A política de retenção de dados de candidato, por empresa, exigida pela
LGPD (Lei 13.709/2018) --- pesquisada nesta revisão junto com o desenho
do processo seletivo. Referenciada por
Cad_Pre_Cadastro.Data_Descarte_Previsto (Fase 0, revisão 31).

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: a política de retenção
pode ser revisada ao longo do tempo, preservando qual versão vigia
quando cada consentimento foi calculado.*

  --------------------- ----------------- ------------------------------------------------------------
  **Campo**             **Tipo lógico**   **Descrição / regra**

  **ID_Politica**       *identificador*   ---

  **ID_Empresa**        *referência       ---
                        (Cad_Empresa)*    

  **Meses_Retencao**    *número*          Parâmetro livre da empresa --- usado apenas quando o
                                          candidato consentiu em permanecer no banco de talentos
                                          (Cad_Pre_Cadastro.Consentimento_Banco_Talentos=verdadeiro,
                                          Fase 0). Alberto foi explícito: o prazo é sempre parâmetro
                                          da empresa, sem piso nem teto travado na estrutura ---
                                          observou que 1 ano pode ser curto (\"muda muita coisa depois
                                          disto\"), sem fixar um valor mínimo obrigatório.

  **Vigencia_Inicio**   *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**      *data*            Último dia em que esta versão vale (inclusive). Sempre
                                          preenchida: 31/12/9999 quando o fim é indefinido (versão
                                          vigente) --- convenção da Fase 0, seção 2.

  **Motivo_Vigencia**   *texto, opcional* Por que esta versão foi criada.
  --------------------- ----------------- ------------------------------------------------------------

*Retenção de dados de candidato (LGPD) --- comportamento de aplicação:
confirmado por Alberto --- \"somente com o consentimento do candidato,
se o candidato conceder manter, se não eliminar\". Enquanto uma
candidatura está em andamento (Mov_Rh_Vaga_Candidato ainda sem Resultado
final em todas as etapas), o processamento dos dados do candidato é
coberto pela execução do próprio processo seletivo, sem exigir
consentimento à parte. Quando esse processo específico se encerra, dois
caminhos: (a) sem consentimento
(Cad_Pre_Cadastro.Consentimento_Banco_Talentos=falso ou nunca
preenchido) --- o descarte/anonimização é disparado pelo EVENTO de
encerramento, sem data agendada; (b) com consentimento --- o dado
permanece no banco de talentos até Data_Descarte_Previsto
(Data_Consentimento + Cad_Rh_Politica_Retencao_Candidato.Meses_Retencao
vigente). Alerta LGPD: pedido explícito de Alberto --- quando o usuário
configura Meses_Retencao acima de 24 (2 anos, a referência de mercado
por analogia à prescrição trabalhista bienal, identificada na pesquisa
desta revisão), a camada de aplicação exibe um alerta informativo, não
bloqueante, sobre o risco de exposição LGPD daquele prazo --- a decisão
final de quantos meses reter continua sendo da empresa, mesmo princípio
\"sugere, nunca aplica automaticamente\" já usado em todo o dicionário.*

3\. Colaborador e Vínculo de Emprego

O colaborador em si não ganha cadastro próprio --- é um Cad_Participante
como outro qualquer, com Cad_Participante_Classe.Classe=funcionário
(Fase 0, já existente). O que faltava era o VÍNCULO: a relação de
emprego específica, com sua própria matrícula, que pode começar e
terminar mais de uma vez para a mesma pessoa (desligamento seguido de
recontratação) sem confundir o histórico de uma janela com o de outra.

Cad_Vinculo_Emprego

Uma relação de emprego específica entre um colaborador
(Cad_Participante, classe funcionário) e a Mlegate --- o \"vínculo\"
citado no Documento Analítico. A mesma pessoa pode ter mais de um
Cad_Vinculo_Emprego ao longo do tempo (desligamento e recontratação),
cada um com sua própria matrícula; nunca mais de um vínculo ATIVO ao
mesmo tempo para o mesmo participante na mesma filial, mas isso é regra
de processo, não travada estruturalmente.

*Vigência: não --- cada registro é uma matrícula própria, de vida única
(admissão até um eventual desligamento); uma recontratação nasce como um
NOVO Cad_Vinculo_Emprego, nunca como reabertura do anterior, preservando
a data de admissão e de desligamento originais.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo** | *identificador* | --- |
| **ID_Participante** | *referência (Cad_Participante, classe funcionário)* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | A filial empregadora --- cada filial carrega seu próprio CNPJ (Fase 0), e é o CNPJ que o eSocial trata como empregador (o evento de tabela de estabelecimentos, S-1005, é por CNPJ). Redefinido nesta revisão (9): passa a representar só a filial de ADMISSÃO deste vínculo (fixa, alimenta o evento S-2200) --- a filial ATUAL de um vínculo ativo é sempre DERIVADA da linha mais recente de Cad_Participante_Historico_Filial (Fase 0, nova nesta revisão), cobrindo a transferência intra-empresa entre filiais sem reescrever este campo nem gerar novo vínculo. |
| **Matricula** | *código (até 30)* | Identificador do vínculo perante a folha --- único por empregador (todas as filiais do mesmo CNPJ raiz), como o eSocial exige (REGRA_VALIDA_MATRICULA; revisão 13, D-N216; antes dizia "único por filial", Q75-1), reiniciado ou não conforme a política da empresa; uma recontratação normalmente ganha matrícula nova, nunca reabre a antiga. Alberto, 19/10/2026: a matrícula vale por período de contratação; a pessoa demitida e recontratada depois tem uma matrícula no primeiro vínculo e outra no segundo (confirma a regra acima; Q75-1). |
| **Matricula_Esocial** | *código (até 30), opcional* | Adicionado por comentário de Alberto: \"normalmente o mesmo número de matrícula do sistema é a mesma do e-social, porém prevendo que podemos ter migração de outro sistema e receber dados diferente precisaria ter a matrícula do e-social.\" Vazio quando Matricula e a matrícula perante o eSocial coincidem (caso normal); preenchido só quando divergem --- tipicamente um vínculo migrado de outro sistema, cuja numeração já foi comunicada ao eSocial antes da virada e não pode mudar. Revisão 13 (documento 75, D-N216): obrigatória na importação de vínculos, mesmo quando igual à Matricula, para os eventos seguintes apontarem para o vínculo certo; no cadastro do ERP continua opcional. Única por empregador (todas as filiais do mesmo CNPJ raiz), não por filial; não pode começar por "eSocial", e vínculo reconhecido por S-2500 ou S-8200 recebe matrícula nova (MOS, itens 28 e 29). |
| **Tipo_Vinculo** | *enumeração {clt, estagio, terceirizado, autonomo, intermitente, safrista, cooperado, outro, pro_labore, estatutario_efetivo, cargo_comissionado, temporario_administrativo, inativo_estatutario}* | Estrutura fixa do próprio mecanismo --- decide, por exemplo, se férias/13º (seções 3 e 6) se aplicam. Ganhou três valores nesta revisão (4), pedidos pela verificação de legislação trabalhista: intermitente (art. 452-A CLT --- convocação esporádica, sem jornada contínua); safrista (contrato de safra, Lei 5.889/1973 --- trabalhador rural por prazo ligado ao ciclo agrícola, regime distinto de intermitente apesar de ambos não terem jornada contínua regular, por isso valores separados); cooperado (TSVE --- trabalhador sem vínculo, cooperativa contratada por prazo determinado, cobrindo o caso concreto de Alberto). Os três, junto de estagio quando aplicável, tipicamente vêm acompanhados de Tipo_Contrato_Prazo=determinado, abaixo. Ganhou também pro_labore nesta revisão (6), pedido pela especificação do processo de Recrutamento e Seleção (seção 3): sócio-administrador/diretor não empregado --- sem FGTS, sem férias/13º por obrigação CLT (a empresa pode pagar por política própria), INSS como contribuinte individual, evento eSocial S-2300 (TSVE) em vez de S-2200; processo seletivo por trás de um vínculo pro_labore é opcional, como para qualquer outro Tipo_Vinculo --- não há amarração estrutural entre tipo de vínculo e obrigatoriedade de vaga. Ganhou quatro valores nesta revisão (12), pedidos por Alberto para o regime de servidor estatutário/RJU (seção 20): estatutario_efetivo, cargo_comissionado, temporario_administrativo e inativo_estatutario --- espelham os códigos 301/302/306 (categoria de trabalhador --- agente público) da tabela do eSocial, distinguindo o servidor de carreira do ocupante só de cargo em comissão, do contratado temporário (arts. 37, IX CF) e do inativo mantido pela própria folha (ver Natureza_Inativo, abaixo). Distinto de empresa pública/sociedade de economia mista, que já é clt comum (ver Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal, abaixo). |
| **Data_Admissao** | *data* | Quando ID_Vinculo_Origem_Transferencia (abaixo) está preenchido, recebe a data de admissão ORIGINAL do vínculo encerrado na empresa de origem, não a data do evento de transferência --- comportamento de aplicação que preserva automaticamente a contagem de tempo de serviço/período aquisitivo de férias/13º, já que todo esse cálculo deriva sempre desta data. Para Tipo_Vinculo=estatutario_efetivo/cargo_comissionado/temporario_administrativo (revisão 12), recebe a data de EXERCÍCIO (Data_Exercicio, abaixo) --- a etapa em que o servidor de fato assume a função ---, não a de nomeação nem a de posse, preservando por igual toda a contagem de tempo de serviço já derivada deste campo no resto do dicionário. Revisão 13 (documento 75): na transferência (tipos 2 a 7 de ID_Tipo_Admissao) ou na mudança de CPF, recebe a data inicial do vínculo no primeiro empregador, como já valia para ID_Vinculo_Origem_Transferencia. |
| **Data_Nomeacao** | *data, opcional* | Adicionado nesta revisão (12), pedido por Alberto para o regime estatutário (seção 20): preenchido só para estatutario_efetivo/cargo_comissionado/temporario_administrativo --- a primeira das três etapas da admissão do servidor público (nomeação → posse → exercício), distinta da admissão CLT em etapa única. |
| **Data_Posse** | *data, opcional* | Adicionado nesta revisão (12): a segunda etapa --- o ato formal de investidura no cargo, com prazo legal de referência de até 30 dias corridos da nomeação (Lei 8.112/90 art. 13 §1º, como referência federal --- cada ente tem estatuto próprio, mas com estrutura geral similar, ver seção 20). Comportamento de aplicação: quando este campo não é preenchido dentro do prazo contado de Data_Nomeacao, a aplicação sinaliza um ALERTA à RH --- nunca um bloqueio estrutural, mesmo princípio \"sugere, nunca aplica automaticamente\" já usado em todo o dicionário. |
| **Data_Exercicio** | *data, opcional* | Adicionado nesta revisão (12): a terceira e última etapa --- o início efetivo do exercício das atribuições do cargo, com prazo legal de referência de até 15 dias corridos da posse (Lei 8.112/90 art. 15 §1º). É esta data que Data_Admissao (acima) recebe para vínculos estatutários. Mesmo comportamento de alerta (não bloqueio) de Data_Posse, acima, contado a partir de Data_Posse. |
| **Data_Desligamento** | *data, opcional* | Vazia enquanto o vínculo está ativo --- mesmo princípio de nunca guardar um Status separado quando a data já resolve a pergunta, já usado em Cad_Conta_Bancaria.Data_Encerramento (Tesouraria) e Cad_Ativo_Imobilizado.Data_Baixa (Fase 0). |
| **ID_Vinculo_Origem_Transferencia** | *referência (Cad_Vinculo_Emprego, autorreferência, opcional)* | Adicionado nesta revisão (9), pedido por Alberto (transferência de colaborador para outra empresa do mesmo grupo econômico --- CNPJ raiz diferente): liga este novo vínculo (na empresa destino) ao vínculo encerrado na empresa de origem. Vazio para admissão normal ou recontratação comum --- nesses casos NÃO há continuidade, tempo de serviço reinicia do zero, mesmo comportamento já descrito para recontratação. Preenchido, ativa a continuidade: tempo de serviço, período aquisitivo de férias, 13º e aviso-prévio contam sem interrupção (Data_Admissao, acima, herda a data original); o FGTS não é sacado, é só transferido entre contas vinculadas (PTC --- Pedido de Transferência de Contas), fora do escopo estrutural deste dicionário. Distingue estruturalmente da transferência intra-empresa entre filiais (Cad_Participante_Historico_Filial, Fase 0), que nunca gera vínculo novo. Pesquisa eSocial: a transferência intra-empresa é tratada como alteração contratual simples (S-2206); a transferência inter-empresa do grupo gera o par desligamento (S-2299, motivo \"transferência\")+admissão (S-2200, tipo \"transferência entre empresas do grupo\") com os atributos de continuidade acima. |
| **ID_Tipo_Admissao** | *referência (Cad_Classe_Sistema, domínio = tipo_admissao_esocial, opcional)* | Revisão 13 (D-N219): tpAdmissao do S-2200: admissão ou o tipo de transferência (sete valores, domínio tipo_admissao_esocial). Obrigatório no celetista. |
| **Origem_Admissao** | *enumeração {normal, acao_fiscal, decisao_judicial}, opcional* | Revisão 13 (D-N219): indAdmissao do S-2200. Obrigatório no celetista. |
| **Numero_Processo_Admissao_Judicial** | *código (20), opcional* | Revisão 13 (D-N219): nrProcTrab: número do processo judicial (20 algarismos). Obrigatório e exclusivo quando a origem é decisão judicial. |
| **Tipo_Contrato_Prazo** | *enumeração {determinado, indeterminado, determinado_por_fato}* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista: cobre contrato de experiência (art. 445, parágrafo único, CLT --- até 90 dias, uma única prorrogação dentro do limite), contrato de safra e qualquer outro vínculo por prazo determinado. Uma prorrogação (ex.: experiência) atualiza Data_Fim_Prevista_Contrato, abaixo, sem criar novo Cad_Vinculo_Emprego; uma efetivação zera Data_Fim_Prevista_Contrato e muda este campo para indeterminado --- em nenhum dos dois casos nasce vínculo novo, é a mesma matrícula continuando, diferente do padrão de recontratação (que sempre gera vínculo novo). Revisão 13 (documento 75, D-N219): determinado_por_fato, para tpContr = 3 do S-2200 (contrato por prazo determinado vinculado à ocorrência de um fato, informado em Objeto_Contrato_Determinado). O valor determinado passa a significar prazo determinado em dias (tpContr = 2). |
| **Data_Fim_Prevista_Contrato** | *data, opcional* | Preenchida só quando Tipo_Contrato_Prazo=determinado --- a data-fim prevista do contrato (experiência, safra, TSVE cooperado), atualizada em cada prorrogação dentro do limite legal do tipo de contrato. |
| **Clausula_Assecuratoria** | *booleano, opcional* | Revisão 13 (D-N219): clauAssec: o contrato por prazo determinado tem cláusula assecuratória do direito recíproco de rescisão antecipada. Obrigatório quando o contrato é determinado (em dias ou por fato). |
| **Objeto_Contrato_Determinado** | *texto (255), opcional* | Revisão 13 (D-N219): objDet: o fato que determina o fim do contrato. Obrigatório e exclusivo quando o contrato é por fato (determinado_por_fato). |
| **Local_Regime_Trabalho** | *enumeração {presencial, teletrabalho, hibrido, externo}* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista (arts. 75-A a 75-E e 62, I, CLT): descreve ONDE o trabalho acontece --- deliberadamente um campo separado de Sujeito_Controle_Jornada/Motivo_Exclusao_Jornada, abaixo, porque teletrabalho não exclui automaticamente o vínculo do controle de jornada (só teletrabalho POR TAREFA exclui, ver abaixo). |
| **ID_Estabelecimento_Esocial_Trabalho** | *referência (Cad_Rh_Estabelecimento_Esocial, opcional)* | Revisão 13 (D-N219): localTrabGeral do S-2200: estabelecimento (CNPJ, CAEPF ou CNO) onde o trabalhador atua. Vazio: o estabelecimento da filial do vínculo. |
| **Descricao_Complemento_Local_Trabalho** | *texto (80), opcional* | Revisão 13 (D-N219): descComp do S-2200: descrição complementar do local de trabalho. |
| **ID_Endereco_Trabalho** | *referência (Cad_Participante_Endereco, opcional)* | Revisão 13 (D-N219): localTempDom do S-2200: endereço de trabalho do doméstico e do temporário. Obrigatório nas categorias 104 e 106 (mesmo padrão do processo trabalhista). |
| **Numero_Processo_Alvara_Judicial** | *código (20), opcional* | Revisão 13 (D-N219): alvaraJudicial/nrProcJud do S-2200: alvará para menor de 14 anos em qualquer categoria, e de 14 a 16 anos em categoria diferente de aprendiz. |
| **Sujeito_Controle_Jornada** | *booleano* | Adicionado nesta revisão (4): falso quando este vínculo está fora do capítulo de duração do trabalho da CLT --- sem ponto obrigatório, sem hora extra, sem banco de horas (seção 7). Quando falso, Motivo_Exclusao_Jornada, abaixo, é preenchido. |
| **Motivo_Exclusao_Jornada** | *enumeração {cargo_confianca, atividade_externa, teletrabalho_tarefa}, opcional* | Preenchido só quando Sujeito_Controle_Jornada=falso: cargo_confianca (art. 62, II --- gestão, gratificação ≥40% do salário do cargo efetivo); atividade_externa (art. 62, I --- incompatibilidade ontológica de fixar horário, ex. vendedor externo); teletrabalho_tarefa (art. 62, III, Lei 14.442/2022 --- só teletrabalho POR PRODUÇÃO OU TAREFA exclui; teletrabalho por jornada, com controle remoto de horário, continua sujeito a ponto/hora extra normalmente, por isso este campo é independente de Local_Regime_Trabalho=teletrabalho). |
| **ID_Agente_Integracao** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista: a instituição intermediária (ex.: CIEE) prevista pela Lei do Estágio (11.788/2008) e pela legislação de aprendizagem --- preenchido só quando Tipo_Categoria_Esocial/contexto indica estágio ou aprendiz. |
| **ID_Categoria_Esocial** | *referência (Cad_Classe_Sistema, domínio = categoria_trabalhador_esocial)* | A categoria do trabalhador exigida pelo evento de admissão do eSocial (S-2200) --- ex.: empregado CLT geral, aprendiz, doméstico, dirigente sindical, entre as demais categorias da tabela oficial. Domínio aberto, mesmo padrão já usado para os demais cadastros oficiais externos deste dicionário. |
| **ID_Regime_Previdenciario** | *referência (Cad_Classe_Sistema, domínio = regime_previdenciario), opcional* | Revisão 13 (D-N219): tpRegPrev do S-2200: rgps (1), rpps (2: RPPS, parlamentares e proteção social dos militares dos Estados e do DF), exterior (3: previdência no exterior) e spsmfa (4: sistema de proteção social dos militares das Forças Armadas). Obrigatório. O regime trabalhista (tpRegTrab) sai da categoria e do tipo de vínculo, sem campo próprio. Revisão 17 (D-N305): vira domínio de Cad_Classe_Sistema (regime_previdenciario: rgps 1, rpps 2, exterior 3, spsmfa 4, cada valor com o código do eSocial), para o eSocial poder ampliar a lista por nota técnica sem mudar o dicionário. |
| **Natureza_Atividade** | *enumeração {urbano, rural}, opcional* | Revisão 13 (D-N219): natAtividade do S-2200. Obrigatório no celetista; a categoria 104 exige urbano e a 102 exige rural. |
| **Data_Opcao_Fgts** | *data, opcional* | Revisão 13 (D-N219): dtOpcFGTS do S-2200. Obrigatória quando o grupo do FGTS é informado. |
| **ID_Motivo_Desligamento** | *referência (Cad_Rh_Motivo_Desligamento, opcional)* | Preenchido só quando Data_Desligamento é preenchida. Passou a referenciar um cadastro próprio nesta revisão (4), em vez do domínio genérico Cad_Classe_Sistema diretamente --- ver Cad_Rh_Motivo_Desligamento, logo abaixo, pedido pela verificação de legislação trabalhista: o motivo passou a carregar, ele mesmo, os fatores que decidem o cálculo da rescisão. |
| **Tipo_Aviso_Previo** | *enumeração {trabalhado, indenizado, descontado, dispensado_cumprimento}, opcional* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista (Lei 12.506/2011): preenchido só quando Data_Desligamento é preenchida. trabalhado/indenizado/dispensado_cumprimento no desligamento por iniciativa da empresa; descontado quando o colaborador pede demissão sem cumprir o aviso --- descontado dele, não pago pela empresa. |
| **Dias_Aviso_Previo** | *número, opcional* | Proporcional ao tempo de serviço (30 dias + 3 por ano completo, até 90), conforme a Lei 12.506/2011 --- preenchido junto de Tipo_Aviso_Previo. |
| **Data_Projecao_Termino** | *data, opcional* | A data de projeção do término do aviso prévio, para fins de contagem de estabilidade/prazo --- preenchida junto de Tipo_Aviso_Previo. |
| **ID_Gestor** | *referência (Cad_Vinculo_Emprego, autorreferência, opcional)* | O vínculo do gestor direto deste colaborador --- vazio quando não há gestor formal mapeado (ex.: o próprio topo da hierarquia). Adicionado para viabilizar a visão de banco de horas do gestor sobre sua equipe (seção 7), mas serve de base para qualquer necessidade futura de hierarquia organizacional, sem entidade própria de organograma nesta revisão. |
| **ID_Evento_Ficha_Origem_Obito** | *referência (Mov_Rh_Ficha_Evento, opcional)* | Adicionado nesta revisão (5), pedido por Alberto: preenchido só quando ID_Motivo_Desligamento aponta para um motivo de óbito --- aponta para o evento de acidente de trabalho (Mov_Rh_Ficha_Evento com Tipo_Cat preenchido, seção 12) que originou a morte, quando aplicável. Vazio para óbito de causa não relacionada ao trabalho; também vazio para qualquer desligamento que não seja por óbito. |
| **ID_Participante_Beneficiario_Obito** | *referência (Cad_Participante, opcional)* | Adicionado nesta revisão (5), pedido por Alberto para modelar o recebedor das verbas rescisórias em caso de óbito do colaborador --- cadastro único, reaproveitando Cad_Participante em vez de uma tabela própria de beneficiário, mesmo princípio \"cadastro único, papéis por contexto\" já usado no resto do dicionário. Preenchido só quando ID_Motivo_Desligamento aponta para um motivo de óbito; é este participante, não o colaborador falecido, que vira o ID_Participante do Mov_Titulo gerado pela rescisão (Contas a Pagar/Receber, seção 18) e do item de remessa bancária correspondente (Tesouraria). |
| **Qualificacao_Recebedor** | *enumeração {dependente_habilitado_inss, herdeiro_por_alvara, inventariante}, opcional* | Adicionado nesta revisão (5), pedido por Alberto (\"a tesouraria tem que confirmar quem foi o fiel depositário deste dinheiro, pois depois a empresa pode ser notificada judicialmente para identificar quem foi que recolheu o dinheiro, que deveria ser o inventariante\"): a que título ID_Participante_Beneficiario_Obito está recebendo --- dependente habilitado perante o INSS (Lei 8.213/91 art. 16, pagamento direto, sem inventário), herdeiro por alvará judicial (small estate, sem inventário formal) ou inventariante (quando há inventário aberto). É esta qualificação, junto do comprovante correspondente (GED, seção 13 da Fase 0), que documenta o fiel depositário do pagamento para uma eventual notificação judicial futura à empresa. |
| **Data_Estabilidade** | *data, opcional* | Adicionado nesta revisão (12), pedido por Alberto para o regime estatutário (seção 20): a data em que este vínculo adquiriu a estabilidade do art. 41 da CF --- preenchida AUTOMATICAMENTE quando Cad_Rh_Estagio_Probatorio.Status (seção 20) do vínculo passa a homologado, mesmo princípio \"calculado mas armazenado\" já usado no dicionário (ex.: Data_Fim_Prevista/vigências). Vazia para qualquer vínculo sem estágio probatório homologado, inclusive CLT. |
| **Modelo_Remuneracao** | *enumeração {verbas_multiplas, subsidio}* | Adicionado nesta revisão (12), pedido por Alberto para o regime estatutário (seção 20): verbas_multiplas é o padrão já usado por todo o resto do dicionário --- várias Cad_Rh_Verba compondo o líquido (seção 5). subsidio é a remuneração por parcela única, vedada por lei a soma de outras verbas (art. 39 §4º CF), salvo as exceções legais expressas (ex.: verbas indenizatórias, quando cabíveis) --- informativo para a camada de aplicação restringir quais verbas adicionais podem coexistir com o subsídio; a validação da exceção em si fica em Cad_Rh_Verba_Tipo_Vinculo (seção 5), sem estrutura nova. |
| **Natureza_Inativo** | *enumeração {aposentadoria, pensao_por_morte}, opcional* | Adicionado nesta revisão (12), pedido por Alberto para cobrir o caso de entes que pagam proventos de inativos diretamente pela folha, sem RPPS próprio instituído (seção 20): preenchido só quando Tipo_Vinculo=inativo_estatutario, distinguindo o próprio servidor aposentado do pensionista por morte. |
| **ID_Vinculo_Origem_Aposentadoria** | *referência (Cad_Vinculo_Emprego, autorreferência, opcional)* | Adicionado nesta revisão (12), mesmo padrão de ID_Vinculo_Origem_Transferencia (acima): liga o vínculo de inativo (Tipo_Vinculo=inativo_estatutario) ao vínculo de trabalho original do servidor, preenchido só quando Natureza_Inativo está preenchido. |

*Revisão 13 --- campos novos: ID_Tipo_Admissao, Origem_Admissao, Numero_Processo_Admissao_Judicial, Clausula_Assecuratoria, Objeto_Contrato_Determinado, Conta_Cota_Pcd, Regime_Previdenciario, Natureza_Atividade, Data_Opcao_Fgts, ID_Estabelecimento_Esocial_Trabalho, Descricao_Complemento_Local_Trabalho, ID_Endereco_Trabalho, Numero_Processo_Alvara_Judicial; campos alterados: Matricula, Matricula_Esocial, Data_Admissao; valores de enumeração novos: Tipo_Contrato_Prazo (+determinado_por_fato).*

*Revisão 15 --- campos alterados: Matricula, Conta_Cota_Pcd.*

*Revisão 17 --- campos que saem: Conta_Cota_Pcd; campos renomeados: Regime_Previdenciario para ID_Regime_Previdenciario.*

Regra do leiaute de importação de vínculos (revisão 13, documento 75, D-N215 a D-N224). Obrigatório na importação é o que o S-2200 exige para a categoria do trabalhador, com a mesma condição. A unidade de pagamento e a matrícula do eSocial são obrigatórias, e o indicador de admissão já enviada ao eSocial também (o recibo do S-2200 original é opcional). Condições principais, aplicadas na importação e no cadastro:

| Condição | Campos exigidos |
|---|---|
| Categoria 104 (doméstico) | Regime trabalhista CLT, regime previdenciário RGPS, natureza urbana, endereço de trabalho; tempo parcial, se houver, só no código de 25 horas |
| Categoria 102 (trabalhador rural) | Natureza da atividade rural |
| Categorias 101, 102, 103, 105, 106, 107, 108 e 111 | Regime previdenciário não pode ser RPPS nem SPSMFA |
| Categoria 103 (aprendiz) com admissão a partir de 22/04/2024 | Contrato por prazo determinado em dias |
| Categoria 106 (temporário) | Grupo do temporário (Cad_Vinculo_Temporario), com hipótese legal, justificativa, estabelecimento do tomador e endereço de trabalho |
| Contrato por prazo determinado (em dias ou por fato) | Cláusula assecuratória; em dias, data de término; por fato, objeto do contrato |
| Regime previdenciário RPPS | Para o estatutário: tipo de plano, teto do RGPS e abono permanência; para o dependente: sexo, se a admissão não é cadastramento inicial |
| Admissão por decisão judicial | Número do processo; matrícula nova criada para o evento quando o vínculo veio de S-2500 ou S-8200 |
| Admissão anterior a 26/10/2026, celetista | infoCota derivado do cadastro de deficiência e de Reabilitado_Inss, sem campo no vínculo (revisão 17, D-N300) |
| Estrangeiro com admissão a partir de 19/07/2021 | Tempo de residência |
| Categoria diferente de 111 | Horas semanais e horário noturno |

Derivados, sem campo próprio: o regime trabalhista (tpRegTrab: 1 celetista, 2 estatutário e legislações específicas) vem da categoria e do tipo de vínculo; o cadIni vem da Data_Admissao contra Cad_Rh_Empregador_Esocial.Data_Inicio_Eventos_Nao_Periodicos; o tpRegJor vem de Sujeito_Controle_Jornada, Motivo_Exclusao_Jornada e Local_Regime_Trabalho; a data-base (dtBase) vem de Cad_Rh_Categoria_Sindical.Data_Base; o CNPJ do sindicato vem da categoria sindical e, sem sindicato representativo, é o do Ministério do Trabalho e Emprego (MOS, item 29.1, 37.115.367/0035-00), por carga de uma categoria "sem sindicato representativo" por empresa, sem campo novo (D-N224, Q75-6); a matrícula anotada por decisão judicial vem de Mov_Rh_Processo_Trabalhista_Contrato.

Cad_Rh_Motivo_Desligamento

Adicionado nesta revisão (4), pedido pela verificação de legislação
trabalhista: o motivo de desligamento deixa de ser um valor solto de
domínio e passa a ser, ele mesmo, um cadastro com os fatores que decidem
o cálculo da rescisão --- cobrindo ao menos sem justa causa, com justa
causa, pedido de demissão, rescisão indireta, acordo mútuo (art. 484-A
CLT) e, desde a revisão 5, óbito.

*Vigência: sim --- os percentuais/regras de um motivo podem mudar por
lei; nova versão nunca sobrescrita, preservando o cálculo de rescisões
já apuradas.*

  -------------------------------------- ------------------------------- ------------------------------------------------------
  **Campo**                              **Tipo lógico**                 **Descrição / regra**

  **ID_Motivo**                          *identificador*                 ---

  **ID_Motivo_Versao**                   *identificador da versão*       Chave primária da versão (tabela física
                                                                         Cad_Rh_Motivo_Desligamento_Versao). ID_Motivo é a
                                                                         identidade, única e referenciada pelas outras tabelas;
                                                                         cada versão guarda a sua janela de vigência --- Fase
                                                                         0, seção 2.

  **Nome**                               *texto*                         Ex.: \"Sem Justa Causa\", \"Justa Causa\", \"Pedido de
                                                                         Demissão\", \"Rescisão Indireta\", \"Acordo Mútuo
                                                                         (art. 484-A)\", \"Óbito\" (adicionado na revisão 5,
                                                                         pedido por Alberto: \"lembrando que o desligamento
                                                                         pode ser por algo natural como morte\"),
                                                                         \"Transferência para Empresa do Grupo Econômico\"
                                                                         (adicionado na revisão 9 --- ver
                                                                         Cad_Vinculo_Emprego.ID_Vinculo_Origem_Transferencia,
                                                                         acima). Cadastro aberto: nesta revisão (12), da
                                                                         pesquisa sobre servidor estatutário/RJU (seção 20), a
                                                                         Mlegate pode cadastrar exemplos próprios do regime
                                                                         estatutário, sem mudança de estrutura --- ex.:
                                                                         \"Exoneração a Pedido\", \"Exoneração de Cargo em
                                                                         Comissão\", \"Demissão (PAD)\" (liga-se ao
                                                                         Mov_Rh_Processo_Disciplinar correspondente, seção 20,
                                                                         quando Penalidade_Aplicada=demissao),
                                                                         \"Aposentadoria\", \"Posse em Cargo Inacumulável\"
                                                                         (art. 37, XVI/XVII CF), \"Readaptação\".

  **ID_Motivo_Esocial**                  *referência                     O código de motivo de desligamento exigido pelo evento
                                         (Cad_Classe_Sistema, domínio =  S-2299 --- domínio aberto, mesmo padrão já usado para
                                         motivo_desligamento_esocial)*   os demais cadastros oficiais externos deste
                                                                         dicionário. Óbito corresponde a código próprio da
                                                                         Tabela 19 do eSocial (motivo de desligamento por
                                                                         falecimento), distinto de sem-justa-causa.
                                                                         Transferência para empresa do grupo corresponde ao
                                                                         código específico de \"transferência\" da mesma tabela
                                                                         (motivo 11).

  **Gera_Verbas_Rescisorias**            *booleano*                      Adicionado nesta revisão (9): falso para óbito (o
                                                                         pagamento vai ao beneficiário/espólio, não é rescisão
                                                                         comum) e para transferência para empresa do grupo
                                                                         econômico (não há rescisão de fato --- o vínculo de
                                                                         origem se encerra só formalmente, com continuidade
                                                                         total preservada no vínculo destino); verdadeiro para
                                                                         os demais motivos. Quando falso, a
                                                                         Mov_Rh_Folha_Apuracao (Tipo_Folha=rescisao)
                                                                         correspondente não gera as verbas normais de rescisão
                                                                         (aviso prévio, saldo de salário, férias proporcionais
                                                                         indenizadas, multa FGTS) --- o FGTS de uma
                                                                         transferência de grupo, por exemplo, é só transferido
                                                                         (PTC), nunca sacado, fora do escopo estrutural deste
                                                                         dicionário.

  **Percentual_Multa_Fgts**              *número*                        Ex.: 40% (sem justa causa/rescisão indireta), 20%
                                                                         (acordo mútuo), 0% (justa causa, pedido de demissão).
                                                                         Óbito: 0% de multa, mas 100% de saque liberado ao
                                                                         beneficiário (Lei 8.036/90 art. 20, IV) --- ver
                                                                         Percentual_Saque_Fgts.

  **Percentual_Saque_Fgts**              *número*                        Ex.: 100% (sem justa causa/rescisão indireta), 80%
                                                                         (acordo mútuo), 0% (justa causa, pedido de demissão),
                                                                         100% (óbito, Lei 8.036/90 art. 20, IV --- saldo de
                                                                         FGTS liberado integralmente ao(s)
                                                                         dependente(s)/sucessor(es)).

  **Aviso_Previo_Aplicavel**             *enumeração {integral,          Acordo mútuo (art. 484-A) reduz o aviso prévio pela
                                         pela_metade, nao_aplicavel}*    metade; os demais motivos aplicam integral ou não
                                                                         aplicável, conforme o caso. Óbito: nao_aplicavel --- o
                                                                         vínculo se extingue no fato, sem aviso prévio a
                                                                         cumprir ou indenizar.

  **Multa_Atraso_Pagamento_Aplicavel**   *booleano*                      Adicionado nesta revisão (5), pedido por Alberto (\"a
                                                                         rescisão tem todas as informações necessárias?\",
                                                                         confirmando os quatro pontos levantados): verdadeiro
                                                                         para a generalidade dos motivos --- dispara a multa do
                                                                         art. 477 §6º CLT (um salário do colaborador) quando o
                                                                         pagamento das verbas rescisórias passa do prazo de até
                                                                         10 dias corridos do término do contrato. Falso para
                                                                         óbito: a jurisprudência não aplica a multa de atraso a
                                                                         este motivo (a mora, quando houver, é tratada como
                                                                         inadimplemento comum, não como a penalidade específica
                                                                         do art. 477), e o prazo de pagamento em si segue
                                                                         contado a partir da comprovação/habilitação do
                                                                         beneficiário, não da data do óbito.

  **Exige_Motivacao_Formal**             *booleano*                      Adicionado nesta revisão (10), da pesquisa sobre
                                                                         empresa pública/sociedade de economia mista (Alberto:
                                                                         \"nossa folha atenderia empresa publicas, que os
                                                                         colaboradores são concursados?\", confirmando \"os
                                                                         dois casos\"): verdadeiro para motivos de desligamento
                                                                         por iniciativa da empresa (sem justa causa, com justa
                                                                         causa) quando o vínculo pertence a uma empresa pública
                                                                         ou sociedade de economia mista --- a Súmula 390 do TST
                                                                         nega a estes empregados a estabilidade do art. 41 da
                                                                         CF (não são servidores estatutários), mas o RE 688.267
                                                                         STF (caso Correios/regime de repercussão geral) exige
                                                                         motivação formal do ato de dispensa, ainda que não
                                                                         haja processo administrativo disciplinar completo.
                                                                         Falso para os demais casos (empresa privada comum,
                                                                         onde a dispensa imotivada permanece livre) e para os
                                                                         motivos que não são iniciativa da empresa (pedido de
                                                                         demissão, óbito, acordo mútuo). Quando verdadeiro, a
                                                                         aplicação exige o preenchimento de um registro de
                                                                         motivação (reaproveitando o GED já usado no resto
                                                                         deste módulo, Cad_Documento_Vinculo, Fase 0 seção 13)
                                                                         antes de permitir o fechamento da
                                                                         Mov_Rh_Folha_Apuracao de rescisão correspondente ---
                                                                         sem entidade nova, mesmo mecanismo já usado para
                                                                         TRCT/homologação, acima. Não cobre o regime de
                                                                         servidor estatutário (administração direta/autarquias,
                                                                         Regime Jurídico Único) --- RESOLVIDO na revisão 12,
                                                                         ver Aplicavel_Regime, abaixo, e seção 20.

  **Aplicavel_Regime**                   *enumeração {clt, estatutario,  Adicionado nesta revisão (12), pedido por Alberto para
                                         ambos}*                         o regime estatutário (seção 20): a que regime este
                                                                         motivo se aplica --- impede um motivo incompatível de
                                                                         ser usado no vínculo errado. Ex.: \"Demissão (PAD)\"
                                                                         só cabe em estatutario (liga-se a um
                                                                         Mov_Rh_Processo_Disciplinar, seção 20); \"Pedido de
                                                                         Demissão\" cabe em ambos; \"Justa Causa\" tipicamente
                                                                         só em clt, já que o desligamento por infração do
                                                                         servidor estatutário segue rito de PAD próprio.
                                                                         Validação de aplicação, não constraint de banco, mesmo
                                                                         critério condicional já usado em todo o dicionário.

  **Vigencia_Inicio**                    *data*                          Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                       *data*                          Último dia em que esta versão vale (inclusive). Sempre
                                                                         preenchida: 31/12/9999 quando o fim é indefinido
                                                                         (versão vigente) --- convenção da Fase 0, seção 2.

  **Motivo_Vigencia**                    *texto, opcional*               Por que esta versão foi criada.
  -------------------------------------- ------------------------------- ------------------------------------------------------

*Prazo legal de pagamento da rescisão (art. 477 §6º CLT): adicionado
nesta revisão (5), em resposta à pergunta de Alberto sobre se a rescisão
tinha todas as informações necessárias. Não ganhou campo próprio em
Mov_Rh_Folha_Apuracao --- o prazo de até 10 dias corridos, contado de
Cad_Vinculo_Emprego.Data_Desligamento (seção 3), e a multa de um salário
em caso de atraso (controlada por
Cad_Rh_Motivo_Desligamento.Multa_Atraso_Pagamento_Aplicavel, acima) são
comportamento de aplicação sobre datas já existentes, não estrutura nova
--- mesmo critério já usado para outros prazos legais derivados neste
dicionário (ex.: Mov_Rh_Banco_Horas_Movimento.Data_Limite_Compensacao,
seção 7). O efetivo pagamento da rescisão segue o mesmo caminho ora
modelado para toda a folha: nasce como Mov_Rh_Folha_Apuracao
(Tipo_Folha=rescisao) e gera Mov_Titulo/remessa bancária (seção 21),
cuja Data_Vencimento (Contas a Pagar/Receber) é o próprio parâmetro que
a aplicação usa para sinalizar o vencimento do prazo do art. 477.*

TRCT e homologação: adicionado nesta revisão (5), mesma pergunta de
Alberto. Não ganha entidade nova --- reaproveita o GED já usado no resto
deste módulo (Cad_Documento/Cad_Documento_Vinculo, Fase 0 seção 13): o
Termo de Rescisão do Contrato de Trabalho gerado e, quando aplicável
(hoje só sindicalmente exigida em poucas categorias, já que a
homologação em sindicato/DRT deixou de ser obrigatória para a
generalidade dos contratos desde a Lei 13.467/2017), o comprovante de
homologação, ficam anexados via Cad_Documento_Vinculo com
Modulo_Destino=\"rh\" apontando para o Cad_Vinculo_Emprego --- mesmo
mecanismo já usado para RG/CTPS (seção 3) e para exame/curso/acidente
(seção 12).

Exame Demissional: adicionado nesta revisão (5), mesma pergunta de
Alberto --- não ganha campo novo, é um valor de exemplo a mais em
Cad_Rh_Tipo_Evento_Ficha (seção 12, mesmo catálogo genérico que já cobre
Exame Admissional e Exame Periódico), registrado como um
Mov_Rh_Ficha_Evento associado ao vínculo antes do fechamento da
rescisão, com laudo anexado via GED como qualquer outro exame.

Quitação de banco de horas na rescisão: adicionado nesta revisão (5),
mesma pergunta de Alberto --- coberto por um novo valor de Origem_Tipo
em Mov_Rh_Banco_Horas_Movimento (seção 7, ver abaixo), não por campo
novo aqui: o saldo de banco de horas na data do desligamento (sempre uma
consulta derivada, nunca armazenado) é debitado por inteiro e convertido
em Mov_Rh_Folha_Item de hora extra dentro da própria
Mov_Rh_Folha_Apuracao de rescisão.

Mov_Rh_Estabilidade_Provisoria

Adicionado nesta revisão (4), pedido pela verificação de legislação
trabalhista: a vigência de uma estabilidade provisória do vínculo ---
gestante (art. 391-A CLT), CIPA (art. 165 CLT), acidentado (art. 118 Lei
8.213/91), entre outras. Alberto foi explícito que a lista de tipos deve
ser EXTENSÍVEL, não uma enumeração fixa fechada.

*Vigência: sim --- é o próprio registro de vigência
(Data_Inicio/Data_Fim), mesmo padrão já usado em
Mov_Rh_Cargo_Condicao_Risco (seção 13).*

  -------------------------- -------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                  **Descrição / regra**

  **ID_Estabilidade**        *identificador*                  ---

  **ID_Vinculo**             *referência                      ---
                             (Cad_Vinculo_Emprego)*           

  **ID_Tipo_Estabilidade**   *referência (Cad_Classe_Sistema, Domínio aberto --- valores iniciais:
                             domínio =                        gestante, cipa_titular, cipa_suplente,
                             tipo_estabilidade_provisoria)*   acidentado, pre_aposentadoria, outro.

  **Vigencia_Inicio**        *data*                           --- Renomeado na revisão 14 (antes
                                                              Data_Inicio).

  **Vigencia_Fim**           *data*                           Vazia enquanto a estabilidade está
                                                              vigente. Renomeado na revisão 14 (antes
                                                              Data_Fim). Sempre preenchida: 31/12/9999
                                                              quando o fim é indefinido (versão
                                                              vigente) --- convenção da Fase 0, seção
                                                              2.

  **Motivo_Vigencia**        *texto, opcional*                Por que esta versão foi criada.
  -------------------------- -------------------------------- ----------------------------------------

*Cad_Rh_Processo_Administrativo_Judicial --- APOSENTADA na revisão 16
(Bloco 3). Guardava o número de um processo referenciado pelos eventos
do eSocial que suspendem o recolhimento (S-1070) e só existia para o
eSocial. O número, as partes e os andamentos passam para Cad_Processo
(Fase 8 --- Jurídico), e o código de suspensão do eSocial passa para
Mov_Processo_Suspensao. Cad_Rh_Pensao_Alimenticia.ID_Processo_Judicial
aponta agora para Cad_Processo. A chave ID_Processo repetida entre esta
entidade e Mov_Rh_Processo_Disciplinar deixa de existir: a segunda passa
a ID_Processo_Disciplinar.*

*Documentos do colaborador --- RG, carteira de trabalho: adicionado por
comentário de Alberto. Sem campo novo aqui: reaproveita o GED da Fase 0
(Cad_Documento/Cad_Documento_Vinculo, seção 11), mesmo mecanismo já
usado por Expedição para foto de inspeção --- um Cad_Documento_Vinculo
com Modulo_Destino=\"rh\" e
Entidade_Relacionada_Tipo/ID_Entidade_Relacionada apontando para este
Cad_Vinculo_Emprego. Documento no nível do VÍNCULO, não do participante,
porque RG e carteira de trabalho anexados dizem respeito a esta
matrícula específica.*

*Patch em Fase 0 (revisão 27), necessário para este módulo existir de
forma consistente: Cad_Participante_Historico_Cargo,
Cad_Participante_Historico_Departamento e
Cad_Participante_Historico_Salario --- os três placeholders já citados
na seção 1 --- ganharam ID_Vinculo. Sem esse campo, o histórico de
cargo/departamento/salário de uma pessoa recontratada misturaria, na
mesma linha do tempo, dados de matrículas diferentes; com ele, cada
Cad_Vinculo_Emprego tem sua própria linha do tempo de
cargo/departamento/salário, começando do zero a cada recontratação.
Cad_Participante_Dependente, ao contrário, permaneceu no nível do
PARTICIPANTE --- o mesmo filho ou cônjuge continua sendo dependente da
pessoa independentemente de qual matrícula está ativa. Ver Fase 0, seção
4 e Notas (revisão 27), para o detalhe completo do patch.*

4\. Avaliação de Desempenho

Nova seção nesta revisão (7), pedida por Alberto depois de ver a entrega
da revisão 6: \"o que senti falta é a parte de avaliações periódicas de
desempenho\". Distinta da avaliação de candidato durante o processo
seletivo (Mov_Rh_Vaga_Candidato_Etapa_Avaliador/Nota, seção 2) --- aqui
o avaliado já é colaborador efetivado (Cad_Vinculo_Emprego, seção 3), e
o ciclo se repete periodicamente ao longo de toda a relação de emprego,
não uma vez só na contratação.

Alberto foi explícito em quatro pontos estruturais: (1) catálogo de
critérios PRÓPRIO desta seção --- não reaproveita
Cad_Rh_Criterio_Avaliacao da seleção, já que os pontos avaliados num
ciclo de desempenho (metas, competências do cargo, indicadores) tendem a
ser diferentes dos avaliados numa entrevista; (2) metas por colaborador
E/OU por função --- uma meta pode ser específica de uma pessoa ou
genérica para todo mundo num cargo; (3) ciclo de avaliação com avaliação
do gestor E autoavaliação do próprio colaborador --- mesmo padrão
multi-avaliador já usado na seleção (seção 2), agora com papéis fixos em
vez de um número livre de entrevistadores; (4) pontuações que podem ser
individuais (por colaborador) ou de grupo (por departamento, aplicada a
todos ali) --- e, por fim, metas e critérios ficam ESTRUTURALMENTE
SEPARADOS, cada um com sua própria pontuação, combinando-se só ao final
numa pontuação ponderada única.

Cad_Rh_Ciclo_Avaliacao_Desempenho

O período periódico de avaliação --- ex.: \"2026 --- Semestre 1\",
\"2026 --- Anual\" --- configurável por empresa, sem periodicidade fixa
travada na estrutura.

*Vigência: não --- cada período é um registro próprio; um novo ciclo é
um novo Cad_Rh_Ciclo_Avaliacao_Desempenho, nunca a edição de um já
encerrado.*

  ----------------- ----------------- ----------------------------------------
  **Campo**         **Tipo lógico**   **Descrição / regra**

  **ID_Ciclo**      *identificador*   ---

  **ID_Empresa**    *referência       ---
                    (Cad_Empresa)*    

  **Nome**          *texto*           ---

  **Data_Inicio**   *data*            ---

  **Data_Fim**      *data*            ---

  **Status**        *enumeração       ---
                    {planejado,       
                    em_andamento,     
                    encerrado}*       
  ----------------- ----------------- ----------------------------------------

Cad_Rh_Criterio_Avaliacao_Desempenho

O catálogo, configurável por empresa, dos critérios avaliados num ciclo
de desempenho --- catálogo PRÓPRIO desta seção, confirmado por Alberto,
distinto de Cad_Rh_Criterio_Avaliacao usado na seleção (seção 2).

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: peso ou nível de
pontuação de um critério pode ser revisado entre ciclos, nova versão
nunca sobrescreve, preservando qual peso vigia quando cada ciclo
anterior foi apurado.*

  ----------------------------------- ----------------- ---------------------------------------------------
  **Campo**                           **Tipo lógico**   **Descrição / regra**

  **ID_Criterio_Desempenho**          *identificador*   ---

  **ID_Criterio_Desempenho_Versao**   *identificador da Chave primária da versão (tabela física
                                      versão*           Cad_Rh_Criterio_Avaliacao_Desempenho_Versao).
                                                        ID_Criterio_Desempenho é a identidade, única e
                                                        referenciada pelas outras tabelas; cada versão
                                                        guarda a sua janela de vigência --- Fase 0, seção
                                                        2.

  **ID_Empresa**                      *referência       ---
                                      (Cad_Empresa)*    

  **Nome**                            *texto*           Ex.: \"Qualidade técnica\", \"Colaboração\",
                                                        \"Cumprimento de prazos\".

  **Nivel_Pontuacao**                 *enumeração       Confirmado por Alberto: um critério pode ser
                                      {individual,      pontuado no nível do colaborador (individual) ou
                                      grupo}*           aplicado de uma vez a todo um departamento (grupo)
                                                        --- decide qual das duas tabelas de nota, abaixo,
                                                        recebe a pontuação deste critério.

  **Peso**                            *número*          O peso deste critério na pontuação final ponderada
                                                        do ciclo (ver
                                                        Mov_Rh_Avaliacao_Desempenho.Nota_Final_Ponderada,
                                                        abaixo).

  **Ativo**                           *booleano*        ---

  **Vigencia_Inicio**                 *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                    *data*            Último dia em que esta versão vale (inclusive).
                                                        Sempre preenchida: 31/12/9999 quando o fim é
                                                        indefinido (versão vigente) --- convenção da Fase
                                                        0, seção 2.

  **Motivo_Vigencia**                 *texto, opcional* Por que esta versão foi criada.
  ----------------------------------- ----------------- ---------------------------------------------------

Mov_Rh_Avaliacao_Desempenho

O cabeçalho da avaliação de um vínculo específico dentro de um ciclo ---
um por combinação vínculo+ciclo.

*Vigência: não --- é movimentação; uma correção depois do fechamento é
tratada como novo ciclo ou ajuste explícito, nunca reescrita silenciosa
da nota já comunicada.*

  ----------------------------- -------------------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**                        **Descrição / regra**

  **ID_Avaliacao_Desempenho**   *identificador*                        ---

  **ID_Ciclo**                  *referência                            ---
                                (Cad_Rh_Ciclo_Avaliacao_Desempenho)*   

  **ID_Vinculo**                *referência (Cad_Vinculo_Emprego)*     ---

  **Nota_Final_Ponderada**      *número, opcional*                     Calculada e ARMAZENADA no fechamento do
                                                                       ciclo para este vínculo --- combina
                                                                       critérios (individuais e de grupo) e
                                                                       metas pelos Pesos vigentes de cada
                                                                       catálogo, mesmo padrão \"calculado uma
                                                                       vez, armazenado\" já usado no dicionário
                                                                       (ex.: Data_Limite_Compensacao, banco de
                                                                       horas): a fórmula exata de composição
                                                                       fica como comportamento de aplicação,
                                                                       mas o resultado comunicado ao
                                                                       colaborador nunca muda silenciosamente
                                                                       se os pesos do catálogo forem revisados
                                                                       depois.
  ----------------------------- -------------------------------------- ----------------------------------------

Mov_Rh_Avaliacao_Desempenho_Avaliador

Uma linha por avaliador dentro do cabeçalho --- confirmado por Alberto:
avaliação do gestor E autoavaliação do próprio colaborador, mesmo padrão
multi-avaliador já usado na seleção
(Mov_Rh_Vaga_Candidato_Etapa_Avaliador, seção 2), aqui com papéis fixos
em vez de número livre de entrevistadores.

*Vigência: não.*

  --------------------------------------- -------------------------------- ----------------------------------------
  **Campo**                               **Tipo lógico**                  **Descrição / regra**

  **ID_Avaliacao_Desempenho_Avaliador**   *identificador*                  ---

  **ID_Avaliacao_Desempenho**             *referência                      ---
                                          (Mov_Rh_Avaliacao_Desempenho)*   

  **Tipo_Avaliador**                      *enumeração {gestor, propria}*   gestor: avaliação feita pelo gestor do
                                                                           vínculo (Cad_Vinculo_Emprego.ID_Gestor).
                                                                           propria: autoavaliação ---
                                                                           ID_Participante_Avaliador, abaixo, é o
                                                                           mesmo participante do próprio vínculo
                                                                           avaliado.

  **ID_Participante_Avaliador**           *referência (Cad_Participante)*  ---

  **Parecer**                             *texto*                          ---
  --------------------------------------- -------------------------------- ----------------------------------------

Mov_Rh_Avaliacao_Desempenho_Avaliador_Nota

A nota de um avaliador, num critério de Nivel_Pontuacao=individual,
dentro do ciclo.

*Vigência: não.*

  --------------------------------------- ----------------------------------------- ---------------------------------------------
  **Campo**                               **Tipo lógico**                           **Descrição / regra**

  **ID_Avaliacao_Desempenho_Avaliador**   *referência                               ---
                                          (Mov_Rh_Avaliacao_Desempenho_Avaliador)   
                                          --- chave primária (composta)*            

  **ID_Criterio_Desempenho**              *referência                               Só critérios com Nivel_Pontuacao=individual
                                          (Cad_Rh_Criterio_Avaliacao_Desempenho)    aparecem aqui.
                                          --- chave primária (composta)*            

  **Nota**                                *número*                                  Escala definida pela camada de aplicação,
                                                                                    mesmo critério de parametrização livre já
                                                                                    usado alhures (ex.:
                                                                                    Mov_Rh_Vaga_Candidato_Etapa_Avaliador_Nota,
                                                                                    seção 2).
  --------------------------------------- ----------------------------------------- ---------------------------------------------

Mov_Rh_Avaliacao_Desempenho_Grupo_Nota

A nota de um critério de Nivel_Pontuacao=grupo --- uma única nota por
ciclo+departamento+critério, aplicada a todos os vínculos daquele
departamento no ciclo, em vez de duplicada por avaliador ou por pessoa.

*Vigência: não. Comportamento de aplicação: ao compor
Nota_Final_Ponderada de um vínculo, a nota de grupo é resolvida cruzando
o departamento vigente do vínculo naquele ciclo
(Cad_Participante_Historico_Departamento) com esta tabela --- sem
duplicar o valor em cada pessoa.*

  ---------------------------- ----------------------------------------- -----------------------------------------
  **Campo**                    **Tipo lógico**                           **Descrição / regra**

  **ID_Grupo_Nota**            *identificador*                           ---

  **ID_Ciclo**                 *referência                               ---
                               (Cad_Rh_Ciclo_Avaliacao_Desempenho)*      

  **ID_Departamento**          *referência (Cad_Dimensao_Contabil_Valor, Mesma dimensão já reaproveitada por
                               dimensão = Departamento)*                 Cad_Participante_Historico_Departamento
                                                                         (Fase 0) e por Cad_Usuario_Escopo (seção
                                                                         14).

  **ID_Criterio_Desempenho**   *referência                               Só critérios com Nivel_Pontuacao=grupo
                               (Cad_Rh_Criterio_Avaliacao_Desempenho)*   aparecem aqui.

  **Nota**                     *número*                                  ---
  ---------------------------- ----------------------------------------- -----------------------------------------

*Metas --- estruturalmente separadas dos critérios, confirmado por
Alberto (\"metas separadas dos outros com pontuações independentes\"):
cada meta tem sua própria realização, sem se misturar com a nota de
nenhum critério; a composição das duas acontece só na pontuação final
ponderada, abaixo.*

Cad_Rh_Meta_Desempenho

Uma meta dentro de um ciclo --- confirmado por Alberto: pode ser
específica de um colaborador ou genérica por função/cargo.

*Vigência: não --- a meta nasce e morre dentro do próprio ciclo, que já
é a unidade de tempo; um novo ciclo tem suas próprias metas, mesmo
quando repete a descrição de uma anterior.*

  ----------------- -------------------------------------- ----------------------------------------
  **Campo**         **Tipo lógico**                        **Descrição / regra**

  **ID_Meta**       *identificador*                        ---

  **ID_Empresa**    *referência (Cad_Empresa)*             ---

  **ID_Ciclo**      *referência                            ---
                    (Cad_Rh_Ciclo_Avaliacao_Desempenho)*   

  **Descricao**     *texto*                                ---

  **Tipo_Alvo**     *enumeração {colaborador, cargo}*      Decide qual dos dois campos abaixo é
                                                           preenchido.

  **ID_Vinculo**    *referência (Cad_Vinculo_Emprego,      Preenchido só quando
                    opcional)*                             Tipo_Alvo=colaborador.

  **ID_Cargo**      *referência (Cad_Rh_Cargo, opcional)*  Preenchido só quando Tipo_Alvo=cargo
                                                           (seção 2) --- todo vínculo classificado
                                                           sob este cargo, na vigência do ciclo,
                                                           herda a mesma meta.

  **Peso**          *número*                               O peso desta meta na pontuação final
                                                           ponderada do ciclo, para cada vínculo a
                                                           que ela se aplica.
  ----------------- -------------------------------------- ----------------------------------------

Mov_Rh_Meta_Desempenho_Resultado

A realização de uma meta para um vínculo específico --- sempre por
vínculo, mesmo quando a meta é de cargo (Tipo_Alvo=cargo), porque cada
pessoa atinge um percentual diferente da mesma meta.

*Vigência: não.*

  ------------------------- --------------------------- ----------------------------------------
  **Campo**                 **Tipo lógico**             **Descrição / regra**

  **ID_Resultado**          *identificador*             ---

  **ID_Meta**               *referência                 ---
                            (Cad_Rh_Meta_Desempenho)*   

  **ID_Vinculo**            *referência                 ---
                            (Cad_Vinculo_Emprego)*      

  **Percentual_Atingido**   *número*                    ---

  **Observacao**            *texto*                     ---
  ------------------------- --------------------------- ----------------------------------------

5\. Verbas e Motor de Cálculo de Folha

Confirmado por Alberto: o motor de cálculo em si faz parte desta
especificação, \"junto com todas as provisões e 13º e também no caso de
ter uma folha específica de PLR\". A unidade de cálculo é a Verba
(Cad_Rh_Verba) --- provento ou desconto, tipificado e configurável por
fórmula por empresa, exatamente como o Documento Analítico já descrevia
--- aplicada dentro de uma Apuração de Folha (Mov_Rh_Folha_Apuracao),
que pode ser de mais de um TIPO, não só a folha mensal padrão.

Cad_Rh_Verba

Uma rubrica de folha --- provento (soma ao líquido) ou desconto
(subtrai) --- tipificada e configurável por empresa, nunca hardcoded
neste dicionário: alíquotas e faixas de INSS/IRRF, por exemplo, mudam
por lei, e ficam dentro de Formula, não como estrutura fixa. Revisão 16
(Bloco 3): as tabelas progressivas do INSS e do IRRF saem de Formula e
viram Cad_Rh_Tabela_Progressiva (mais adiante nesta seção); a verba
passa a declarar o código da rubrica do eSocial e os códigos de
incidência oficiais (Cad_Rh_Codigo_Incidencia).

*Vigência: sim --- mesma vigência de qualquer parâmetro deste
dicionário: uma mudança de Formula ou de alíquota legal nasce como nova
versão, nunca sobrescrita, preservando o cálculo de folhas já fechadas
em períodos anteriores.*

  ---------------------------------- -------------------------------- --------------------------------------------------------
  **Campo**                          **Tipo lógico**                  **Descrição / regra**

  **ID_Verba**                       *identificador*                  ---

  **ID_Verba_Versao**                *identificador da versão*        Chave primária da versão (tabela física
                                                                      Cad_Rh_Verba_Versao). ID_Verba é a identidade, única e
                                                                      referenciada pelas outras tabelas; cada versão guarda a
                                                                      sua janela de vigência --- Fase 0, seção 2.

  **ID_Empresa**                     *referência (Cad_Empresa)*       Verbas são configuráveis por empresa, conforme o
                                                                      Documento Analítico --- a mesma rubrica \"Salário Base\"
                                                                      pode ter fórmula/incidência diferente entre empresas do
                                                                      mesmo grupo, se necessário.

  **Nome**                           *texto*                          Ex.: \"Salário Base\", \"Hora Extra 50%\", \"Vale
                                                                      Transporte\", \"INSS\", \"IRRF\", \"Previdência
                                                                      Complementar\".

  **Tipo**                           *enumeração {provento, desconto, Estrutural --- decide o sinal do valor apurado
                                     informativa,                     (Mov_Rh_Folha_Item.Valor, abaixo), mesmo padrão \"um
                                     informativa_dedutora}*           único motor, direção diferente\" já usado em
                                                                      Mov_Titulo.Tipo, Mov_Extrato_Bancario.Tipo, entre
                                                                      outros. informativo, adicionado na revisão 9 (na revisão
                                                                      16 passa a informativa, no feminino, e ganha
                                                                      informativa_dedutora), pedido por Alberto para o caso de
                                                                      taxa/desconto global cobrado por uma operadora de
                                                                      benefício (seção 17, abaixo --- \"não entra nem como
                                                                      desconto nem como provento, entra como verba de
                                                                      informação\... para contabilizar\"): não soma nem
                                                                      desconta do líquido do colaborador --- fica de fora da
                                                                      soma que Mov_Rh_Folha_Item compõe para o líquido ---,
                                                                      mas gera lançamento contábil normalmente através do
                                                                      mesmo Motor de Regras descrito abaixo, cada verba
                                                                      informativa com sua própria regra (débito/crédito)
                                                                      conforme representa um custo a mais (taxa) ou a menos
                                                                      (desconto). Alterado na revisão 16 (Bloco 3). Antes:
                                                                      provento, desconto, informativo. Mapeia para tpRubr 1 a
                                                                      4. A informativa dedutora entra em Formula como redutora
                                                                      de base (ex.: dedução de pensão na base do IRRF).

  **Origem**                         *enumeração {legal, interna}*    Legal: base fixada por lei (ex.: FGTS sobre remuneração
                                                                      bruta, INSS pela tabela oficial) --- muda quando a
                                                                      legislação muda, sempre por VIGÊNCIA desta mesma
                                                                      entidade, nunca por sobrescrita direta. Interna: regra
                                                                      livre da empresa (ex.: previdência complementar sobre
                                                                      salário líquido). Também governa nível de acesso: um
                                                                      usuário pode ter permissão para alterar só verbas
                                                                      legais, só internas, ou ambas (Cad_Permissao, Fase 0)
                                                                      --- mesmo critério já confirmado no Documento Analítico.

  **Formula**                        *texto*                          Expressão de cálculo, podendo referenciar outras
                                                                      Cad_Rh_Verba pelo próprio ID/Nome (ex.: \"IRRF\"
                                                                      referenciando o resultado de \"Base_Irrf\", que por sua
                                                                      vez desconta \"INSS\" e a dedução de dependentes
                                                                      elegíveis) --- texto livre nesta revisão, sem uma
                                                                      linguagem de fórmula estruturada; a camada de aplicação
                                                                      avalia a expressão e precisa detectar dependência
                                                                      circular ANTES de calcular, exatamente como o Documento
                                                                      Analítico já exigia --- comportamento de aplicação, não
                                                                      validação estrutural deste dicionário. A mesma rotina de
                                                                      análise de dependências resolve Ordem_Calculo, abaixo.

  **Ordem_Calculo**                  *número, opcional*               Adicionado nesta revisão (7), pedido por Alberto: \"o
                                                                      sistema tem que ser inteligente o suficiente para
                                                                      determinar esta sequencia de calculo, e para não ficar
                                                                      lento teria que armazenar esta sequencia\". Calculada e
                                                                      ARMAZENADA pela aplicação, nunca preenchida manualmente
                                                                      --- ao analisar as referências a outras verbas dentro de
                                                                      Formula (acima), a aplicação monta o grafo de
                                                                      dependências entre as verbas da empresa e resolve a
                                                                      ordem topológica de execução, definindo a SEQUÊNCIA em
                                                                      que o motor avalia cada verba dentro de uma apuração
                                                                      (ex.: Base_Irrf antes de Irrf). Recalculada pela
                                                                      aplicação só quando alguma Formula da empresa muda (nova
                                                                      vigência de qualquer verba dela), nunca durante a
                                                                      apuração de folha em si (Mov_Rh_Folha_Apuracao, abaixo)
                                                                      --- que só LÊ esta ordem já pronta, evitando reprocessar
                                                                      o grafo a cada execução de folha; mesmo princípio
                                                                      \"calculado mas armazenado\" já usado no dicionário
                                                                      (Mov_Rh_Banco_Horas_Movimento.Data_Limite_Compensacao,
                                                                      seção 7). A detecção de dependência circular (Formula,
                                                                      acima) é pré-condição da mesma rotina: sem ordem
                                                                      topológica válida, não há Ordem_Calculo a armazenar.

  **Incide_Inss**                    *booleano --- calculado e        Alterados. Passam a ser calculados a partir do código de
                                     armazenado*                      incidência e armazenados; o usuário não edita. O motor
                                                                      de cálculo continua lendo os booleanos, o que evita
                                                                      mexer nas fórmulas.

  **Incide_Fgts**                    *booleano --- calculado e        Alterados. Passam a ser calculados a partir do código de
                                     armazenado*                      incidência e armazenados; o usuário não edita. O motor
                                                                      de cálculo continua lendo os booleanos, o que evita
                                                                      mexer nas fórmulas.

  **Incide_Irrf**                    *booleano --- calculado e        Alterados. Passam a ser calculados a partir do código de
                                     armazenado*                      incidência e armazenados; o usuário não edita. O motor
                                                                      de cálculo continua lendo os booleanos, o que evita
                                                                      mexer nas fórmulas.

  **Codigo_Rubrica**                 *código (30)*                    Adicionado na revisão 16 (Bloco 3). Código da rubrica no
                                                                      eSocial (codRubr), escolhido pela empresa. Identidade
                                                                      dentro da empresa e da tabela de rubricas.

  **Identificador_Tabela_Rubrica**   *código (8)*                     Adicionado na revisão 16 (Bloco 3). ideTabRubr:
                                                                      identifica qual tabela de rubricas do empregador a
                                                                      rubrica integra. Padrão único por empresa.

  **ID_Natureza_Rubrica**            *referência (Cad_Classe_Sistema, Adicionado na revisão 16 (Bloco 3). Tabela 03 do eSocial
                                     domínio =                        (natRubr, 4 dígitos). Domínio, porque é só código e
                                     natureza_rubrica_esocial)*       descrição.

  **ID_Incidencia_Previdenciaria**   *referência                      Adicionado na revisão 16 (Bloco 3). codIncCP.
                                     (Cad_Rh_Codigo_Incidencia,       
                                     tributo =                        
                                     contribuicao_previdenciaria)*    

  **ID_Incidencia_Irrf**             *referência                      Adicionado na revisão 16 (Bloco 3). codIncIRRF.
                                     (Cad_Rh_Codigo_Incidencia,       
                                     tributo = irrf)*                 

  **ID_Incidencia_Fgts**             *referência                      Adicionado na revisão 16 (Bloco 3). codIncFGTS. Vazio
                                     (Cad_Rh_Codigo_Incidencia,       quando a rubrica é de vínculo sem FGTS.
                                     tributo = fgts, opcional)*       

  **ID_Incidencia_Rpps**             *referência                      Adicionado na revisão 16 (Bloco 3). codIncCPRP. Só para
                                     (Cad_Rh_Codigo_Incidencia,       vínculo estatutário.
                                     tributo = contribuicao_rpps,     
                                     opcional)*                       

  **ID_Incidencia_Pis_Pasep**        *referência                      Adicionado na revisão 19 (NT 07/2026). codIncPisPasep
                                     (Cad_Rh_Codigo_Incidencia,       do S-1010. Obrigatório, de forma explícita, quando o
                                     tributo = pis_pasep, opcional)*  empregador vigente tem Tributa_Folha_Pis_Pasep
                                                                      verdadeiro (Cad_Rh_Empregador_Esocial), para a
                                                                      rubrica nunca assumir 00 por omissão (o leiaute
                                                                      presume 00 quando o campo não é informado, e a
                                                                      rubrica esquecida entraria com base zero, sem
                                                                      aviso). Vazio nos demais casos.

  **Sujeita_Teto_Remuneratorio**     *booleano*                       Adicionado na revisão 16 (Bloco 3). tetoRemun: a rubrica
                                                                      entra no cálculo do teto constitucional do setor
                                                                      público.

  **Observacao_Esocial**             *texto, opcional*                Adicionado na revisão 16 (Bloco 3). Obrigatório para a
                                                                      rubrica informativa dedutora a partir de 23/11/2026 (NT
                                                                      07/2026).

  **Compoe_Media_Ferias**            *booleano*                       Verdadeiro quando esta verba é variável e deve entrar na
                                                                      média usada para calcular férias (ex.: hora extra,
                                                                      comissão); falso para verbas fixas. Desmembrado nesta
                                                                      revisão (4) do antigo campo único Compoe_Media_Ferias_13
                                                                      --- Alberto observou que pode existir verba que compõe a
                                                                      base de um dos dois cálculos (férias OU 13º) sem compor
                                                                      o outro, caso raro mas não descartado. A média em si
                                                                      nunca é armazenada --- é sempre uma consulta sobre
                                                                      Mov_Rh_Folha_Item de competências anteriores, filtrando
                                                                      pelas verbas com este campo verdadeiro (seção 9,
                                                                      migração).

  **Compoe_Media_Decimo_Terceiro**   *booleano*                       Mesma lógica de Compoe_Media_Ferias, acima, agora para a
                                                                      base de 13º salário --- independente: uma verba pode ter
                                                                      um dos dois verdadeiro e o outro falso.

  **Reflete_Dsr**                    *booleano*                       Adicionado na revisão 21 (P-42). Verdadeiro quando o
                                                                      total desta verba no mês gera DSR (horas extras
                                                                      habituais, comissão, adicional noturno --- art. 7º da
                                                                      Lei 605, com a Lei 7.415/1985 e a Súmula 172 do TST).
                                                                      Falso nas verbas de salário fixo do mensalista (que já
                                                                      inclui o repouso) e nas verbas de DSR, para não calcular
                                                                      DSR sobre DSR.

  **ID_Verba_Dsr_Reflexo**           *referência (Cad_Rh_Verba,       Adicionado na revisão 21. A verba que recebe o DSR
                                     opcional)*                       calculado sobre esta (ex.: "DSR sobre Hora Extra").
                                                                      Obrigatória quando Reflete_Dsr é verdadeiro; a verba
                                                                      apontada tem Reflete_Dsr falso. Se ela deve compor a
                                                                      média de férias e de 13º é decidido pelos próprios
                                                                      Compoe_Media_Ferias e Compoe_Media_Decimo_Terceiro dela
                                                                      (Tema 9 do TST: a partir de 20/03/2023 o DSR sobre horas
                                                                      extras habituais repercute nessas parcelas).

  **ID_Categoria_Remuneratoria**     *referência (Cad_Classe_Sistema, Adicionado nesta revisão (4), pedido pela verificação de
                                     domínio =                        compliance com a Lei 14.611/2023 (Lei de Igualdade
                                     categoria_remuneratoria_verba,   Salarial): classifica a verba numa taxonomia padronizada
                                     opcional)*                       (ex.: salário_base, gratificacao, comissao, beneficio,
                                                                      hora_extra, adicional, outro), usada para agregar o
                                                                      relatório semestral de transparência salarial por
                                                                      categoria de parcela remuneratória --- domínio aberto,
                                                                      mesmo padrão já usado para os demais domínios deste
                                                                      dicionário.

  **Contabilizavel**                 *booleano*                       Adicionado por comentário de Alberto: a primeira decisão
                                                                      do fluxo contábil de uma verba nova --- o contador
                                                                      classifica se ela gera lançamento (verdadeiro) ou não
                                                                      (falso, ex.: verbas puramente informativas). Só quando
                                                                      verdadeiro fazem sentido as regras contábeis descritas
                                                                      no parágrafo abaixo.

  **Fundamento_Legal**               *texto, opcional*                Adicionado nesta revisão (12), da pesquisa sobre
                                                                      servidor estatutário (seção 20): a lei/artigo que criou
                                                                      esta verba (ex.: uma vantagem específica do plano de
                                                                      carreira de um ente estatutário) --- campo GENÉRICO, não
                                                                      exclusivo de verba estatutária, serve para qualquer
                                                                      verba (inclusive CLT) rastrear seu fundamento legal para
                                                                      fins de auditoria.

  **Vigencia_Inicio**                *data*                           Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                   *data*                           Último dia em que esta versão vale (inclusive). Sempre
                                                                      preenchida: 31/12/9999 quando o fim é indefinido (versão
                                                                      vigente) --- convenção da Fase 0, seção 2.

  **Motivo_Vigencia**                *texto, opcional*                Por que esta versão foi criada.
  ---------------------------------- -------------------------------- --------------------------------------------------------

Cad_Rh_Verba_Tipo_Vinculo

A quais tipos de vínculo uma verba se aplica --- pedido por Alberto: \"a
Cad_Rh_Verba tem que ter uma amarração por tipo de vinculo, pois tem
verbas que só incidem sobre estagiario, outras por clt e dai por diante,
e tem verbas que são para mais de um vinculo\". Marcação manual,
confirmada por Alberto (\"marcação verba a verba\") --- sem hierarquia
ou agrupamento formal entre os tipos de vínculo.

*Vigência: não --- nenhuma linha associada a uma verba significa SEM
restrição, aplica a todos os tipos de vínculo; uma ou mais linhas
restringem a verba só aos tipos marcados ali. Deliberadamente sem
vigência própria, ao contrário de Cad_Rh_Verba: mudar a elegibilidade
por tipo de vínculo não reescreve o histórico de folhas já apuradas
(Mov_Rh_Folha_Item já gravado permanece válido) --- só passa a valer nas
apurações futuras.*

  ------------------ ---------------------------------- ----------------------------------------
  **Campo**          **Tipo lógico**                    **Descrição / regra**

  **ID_Verba**       *referência (Cad_Rh_Verba) ---     ---
                     chave primária (composta)*         

  **Tipo_Vinculo**   *mesma enumeração de               ---
                     Cad_Vinculo_Emprego.Tipo_Vinculo   
                     (seção 3) --- chave primária       
                     (composta)*                        
  ------------------ ---------------------------------- ----------------------------------------

Cad_Rh_Verba_Filial

Adicionado nesta revisão (10), pedido por Alberto (\"tem o vinculo da
verba com uma empresa, pois uma verba pode ser para uma empresa e não
ser usada em outra. e pode ter verbas especificas para uma filial\"): a
quais FILIAIS de uma verba se aplica, dentro da empresa já fixada por
Cad_Rh_Verba.ID_Empresa (acima) --- mesmo padrão \"sem linha = sem
restrição\" de Cad_Rh_Verba_Tipo_Vinculo, agora no nível de filial em
vez de tipo de vínculo, os dois filtros combinando quando ambos estão
preenchidos para a mesma verba.

*Vigência: não --- mesmo critério de Cad_Rh_Verba_Tipo_Vinculo: nenhuma
linha associada a uma verba significa SEM restrição, aplica a todas as
filiais da empresa; uma ou mais linhas restringem a verba só às filiais
marcadas ali. Sem vigência própria, pela mesma razão: mudar o escopo por
filial não reescreve o histórico de folhas já apuradas, só passa a valer
nas apurações futuras.*

  ----------------- ---------------- ----------------------------------------
  **Campo**         **Tipo lógico**  **Descrição / regra**

  **ID_Verba**      *referência      ---
                    (Cad_Rh_Verba)   
                    --- chave        
                    primária         
                    (composta)*      

  **ID_Filial**     *referência      ---
                    (Cad_Filial) --- 
                    chave primária   
                    (composta)*      
  ----------------- ---------------- ----------------------------------------

Cad_Rh_Salario_Adicional

Adicionado nesta revisão (11), pedido por Alberto: o catálogo, por
empresa, de um salário adicional tipo \"14º\"/\"15º\" --- um benefício
voluntário ou fixado por convenção coletiva específica, distinto do 13º
salário, que é obrigação legal geral já modelada à parte (seção 5,
acima) e não passa por este catálogo.

*Vigência: sim --- mesma vigência de qualquer parâmetro deste
dicionário: uma mudança de condições nasce como nova versão, preservando
o cadastro vigente quando cada apuração já fechada
(Mov_Rh_Folha_Apuracao, abaixo) foi calculada.*

  --------------------------------- ---------------------- ----------------------------------------
  **Campo**                         **Tipo lógico**        **Descrição / regra**

  **ID_Salario_Adicional**          *identificador*        ---

  **ID_Salario_Adicional_Versao**   *identificador da      Chave primária da versão (tabela física
                                    versão*                Cad_Rh_Salario_Adicional_Versao).
                                                           ID_Salario_Adicional é a identidade,
                                                           única e referenciada pelas outras
                                                           tabelas; cada versão guarda a sua janela
                                                           de vigência --- Fase 0, seção 2.

  **ID_Empresa**                    *referência            Catálogo por empresa, mesmo critério já
                                    (Cad_Empresa)*         usado em Cad_Rh_Verba: nem toda empresa
                                                           do grupo precisa oferecer o mesmo
                                                           salário adicional.

  **Nome**                          *texto*                Ex.: \"14º Salário\", \"15º Salário\".

  **Numero_Ordem**                  *número, opcional*     Só rótulo organizacional (ex.:
                                                           distinguir o 14º do 15º quando a empresa
                                                           tem mais de um) --- não trava nenhuma
                                                           estrutura de parcelamento, que fica
                                                           inteiramente em
                                                           Cad_Rh_Salario_Adicional_Parcela
                                                           (abaixo).

  **Origem**                        *enumeração            convencao_coletiva: fixado por
                                    {convencao_coletiva,   instrumento coletivo específico da
                                    politica_empresa}*     categoria (distinto do reajuste de
                                                           salário em si, seção 16).
                                                           politica_empresa: benefício voluntário
                                                           da empresa, sem amparo em convenção.

  **Ativo**                         *booleano*             ---

  **Vigencia_Inicio**               *data*                 --- Renomeado na revisão 14 (antes
                                                           Data_Vigencia_Inicio).

  **Vigencia_Fim**                  *data*                 Vazia enquanto este salário adicional
                                                           está vigente --- mesmo padrão de
                                                           vigência já usado em Cad_Rh_Beneficio
                                                           (seção 17). Renomeado na revisão 14
                                                           (antes Data_Vigencia_Fim). Sempre
                                                           preenchida: 31/12/9999 quando o fim é
                                                           indefinido (versão vigente) ---
                                                           convenção da Fase 0, seção 2.

  **Motivo_Vigencia**               *texto, opcional*      Por que esta versão foi criada.
  --------------------------------- ---------------------- ----------------------------------------

Cad_Rh_Salario_Adicional_Parcela

O parcelamento de um Cad_Rh_Salario_Adicional --- livre por empresa, ao
contrário do 13º salário, que a estrutura trava em 1 ou 2 parcelas
fixas: aqui a empresa cadastra quantas parcelas quiser.

*Vigência: não --- detalhe do cadastro acima, mesma vida útil; um
reparcelamento é correção das linhas existentes, não histórico
versionado.*

  ---------------------------------- ----------------------------- ----------------------------------------
  **Campo**                          **Tipo lógico**               **Descrição / regra**

  **ID_Salario_Adicional_Parcela**   *identificador*               ---

  **ID_Salario_Adicional**           *referência                   ---
                                     (Cad_Rh_Salario_Adicional)*   

  **Numero_Parcela**                 *número*                      1, 2, 3\... --- a ordem da parcela
                                                                   dentro do salário adicional.

  **Percentual**                     *número*                      O percentual do valor total pago nesta
                                                                   parcela --- a soma dos percentuais de
                                                                   todas as parcelas de um mesmo
                                                                   Cad_Rh_Salario_Adicional deve fechar
                                                                   100%, validação de aplicação, não
                                                                   constraint de banco, mesmo critério já
                                                                   usado no resto deste dicionário para
                                                                   regras condicionais.

  **Mes_Pagamento**                  *número (1-12)*               O mês de referência do pagamento desta
                                                                   parcela.
  ---------------------------------- ----------------------------- ----------------------------------------

*Diferencial de Substituição --- exemplo de verba, não estrutura
própria: adicionado nesta revisão (9), pedido por Alberto (colaborador
que assume outra função por tempo determinado, com diferencial
salarial). Não ganha entidade nova --- é uma Cad_Rh_Verba comum
(Tipo=provento), cuja Formula aplica o Valor_Diferencial já fixado em
Cad_Participante_Historico_Cargo (Fase 0, revisão 32) enquanto a linha
de Tipo_Alocacao=substituicao daquele histórico estiver vigente para o
vínculo; mesmo padrão de parametrização livre já usado para PLR e para o
adicional de insalubridade/periculosidade (seção 13). Ao vencer a janela
de substituição (nova linha devolvendo ao cargo original), a verba
simplesmente para de ser gerada na apuração seguinte, sem campo de
reversão.*

*Comportamento de aplicação --- contabilização da folha: descrito por
Alberto em duas etapas. Primeiro, na criação de uma verba nova, o
contador classifica se ela contabiliza (Cad_Rh_Verba.Contabilizavel,
acima); se sim, aponta as pernas contábeis. Muitas vezes o código da
verba sozinho não basta para definir a conta --- pode depender de uma
chave mais complexa, como verba+centro de custo ou verba+departamento.
Em vez de uma tabela própria de regra contábil de RH, esta apuração
reaproveita o Motor de Regras (Fase 0, seção 8), mesmo mecanismo já
usado por CRM & Vendas (comissão/preço/royalty em escada) e pela
tributação de IBS/CBS: uma Cad_Motor_Regra de Área de
Negócio=folha_pagamento combina critérios verba_rh e, quando necessário,
departamento (Cad_Motor_Regra_Criterio.Campo, Fase 0, revisão 28) --- a
regra mais específica (verba+departamento) vence a mais genérica (verba
isolada) pela mesma Prioridade já usada em todo o motor ---, resolvendo
dois resultados por perna: conta_contabil_debito e
conta_contabil_credito (Cad_Motor_Regra_Resultado.Tipo_Resultado, Fase
0, revisão 28), cada um apontando o ID_Conta de destino
(Cad_Conta_Contabil). Separadamente, Alberto esclareceu que a abertura
por centro de custo/departamento é propriedade de CONTAS específicas,
não da regra da verba --- nem toda conta contábil exige esse
detalhamento. Por isso essa exigência fica marcada diretamente em
Cad_Conta_Contabil.ID_Dimensao_Abertura_Obrigatoria (Fase 0, revisão
28): quando preenchida, o lançamento gerado nessa conta
(Mov_Lancamento_Dimensao, já existente em Fase 0) exige o valor daquela
dimensão; contas sem essa exigência seguem lançadas só no nível de
conta.*

Cad_Rh_Periodo_Folha (aposentado nesta revisão)

Nesta revisão (13), Cad_Rh_Periodo_Folha foi APOSENTADO como cadastro
próprio: a Fase 0 generalizou o controle de período de fechamento
(revisão 37, seção 10) num mecanismo único reaproveitado por todos os
módulos do dicionário ---
Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial
---, e a Folha & RH passa a ser simplesmente a instância
Cad_Bloco_Fechamento.Codigo=\"folha_pagamento\" dessa estrutura, ao lado
de Contabilidade (\"contabilidade\") e dos demais blocos. O que existia
aqui era, na prática, uma reinvenção independente do mesmo conceito ---
nascido do pedido original de Alberto: \"a folha também tem que ter
controle de periodos abertos, pois não podemos alterar o passado\".

O COMPORTAMENTO NÃO MUDA: continua deliberadamente INDEPENDENTE do
período contábil --- agora simplesmente por serem blocos diferentes
(\"folha_pagamento\" vs \"contabilidade\"), sem qualquer relação de
causa/efeito entre eles ---, por instrução explícita de Alberto: \"as
datas da folha não são as mesmas da contabilidade, pois preciso que a
folha esteja fechada para contabilizar, como são operadores
independentes estes periodos tem que serem independentes\" --- a folha
continua precisando fechar primeiro, com seu próprio calendário, antes
de poder ser contabilizada (Mov_Lote_Lancamento
Origem_Tipo=folha_pagamento, abaixo). Continua por filial, e continua
fail-closed, por instrução explícita de Alberto: nenhuma linha em
Cad_Periodo_Fechamento_Filial para a combinação
Bloco=\"folha_pagamento\"+Filial+Competência é tratada como aberta por
omissão --- o que não está aberto está fechado, mesma regra de sempre.
Só a estrutura de dados deixa de ser exclusiva da Folha e passa a ser a
mesma tabela genérica reaproveitada por todos os módulos.

*Ver Fase 0 --- Dicionário de Dados, seção 10, para o cadastro completo
(Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial)
e para o desenho da cascata Empresa→Filial reaproveitada aqui.*

Mov_Rh_Folha_Apuracao

O cabeçalho de uma apuração de folha --- mensal, 13º (cada parcela),
férias, rescisão, PLR ou pagamento avulso a autônomo. Mais de um
Tipo_Folha existe deliberadamente: a folha de PLR, por exemplo, não
segue o calendário mensal nem a jornada apurada por ponto, mas usa o
mesmo motor de verbas e o mesmo cabeçalho de apuração. Depende de
Cad_Periodo_Fechamento_Filial (Fase 0, seção 10,
Bloco=\"folha_pagamento\") estar com Status=aberto para o par
Filial+Competência --- migrado nesta revisão (13) do antigo cadastro
próprio Cad_Rh_Periodo_Folha (acima), mesmo comportamento: sem isso,
nenhum registro nasce aqui, nem apuração original nem reprocessamento.

*Vigência: não --- é o registro de um evento (a apuração de um
período/tipo específico); uma correção depois de Status=fechada NUNCA
reabre a apuração fechada --- nasce como um novo Mov_Rh_Folha_Apuracao
(Numero_Processamento seguinte, ID_Apuracao_Anterior apontando para o
processamento substituído), preservando os dois lados: o que foi
calculado antes e o que foi recalculado depois, mesmo quando não podem
ser contabilizados no mesmo período.*

  -------------------------- ----------------------------------- --------------------------------------------------------
  **Campo**                  **Tipo lógico**                     **Descrição / regra**

  **ID_Apuracao**            *identificador*                     ---

  **ID_Filial**              *referência (Cad_Filial)*           ---

  **Competencia**            *competência, opcional*             Substitui Competencia_Ano/Competencia_Mes (revisão 15
                                                                 --- resíduo do Bloco 1). Preenchida quando a apuração é
                                                                 mensal.

  **Ano_Referencia**         *número, opcional*                  Só quando a apuração não segue competência mensal
                                                                 (Tipo_Folha = plr ou pagamento_autonomo): o ano-base.
                                                                 Exatamente um dos dois --- Competencia ou Ano_Referencia
                                                                 --- é preenchido.

  **Tipo_Folha**             *enumeração {mensal,                Confirmado por Alberto: a folha de PLR é um tipo próprio
                             decimo_terceiro_primeira_parcela,   de apuração, ao lado da mensal e do 13º --- mesmo motor
                             decimo_terceiro_segunda_parcela,    de Cad_Rh_Verba/Mov_Rh_Folha_Item, cálculo e regra de
                             ferias, rescisao, plr,              elegibilidade específicos ficam de fora deste dicionário
                             pagamento_autonomo,                 (fórmula de PLR é decisão de negócio da empresa, não
                             salario_adicional, inativos}*       estrutura fixa). pagamento_autonomo: adicionado por
                                                                 comentário de Alberto --- pagamento a um vínculo
                                                                 Tipo_Vinculo=autonomo (RPA), tipicamente por serviço
                                                                 prestado, não por um lote mensal de muitos
                                                                 colaboradores; cada RPA nasce como sua própria
                                                                 Mov_Rh_Folha_Apuracao, fora do calendário de fechamento
                                                                 mensal, com um único Mov_Rh_Folha_Item (ou poucos)
                                                                 associado. salario_adicional, adicionado nesta revisão
                                                                 (11): a apuração de uma parcela de
                                                                 Cad_Rh_Salario_Adicional (acima) --- reaproveita o mesmo
                                                                 motor de Cad_Rh_Verba/Mov_Rh_Folha_Item das demais
                                                                 folhas (a fórmula de cálculo em si é livre por empresa,
                                                                 mesmo padrão já usado para PLR), com a elegibilidade
                                                                 (todos os colaboradores, ou só uma
                                                                 categoria/cargo/filial) já resolvida pelos mecanismos
                                                                 existentes de Cad_Rh_Verba_Tipo_Vinculo e
                                                                 Cad_Rh_Verba_Filial, sem campo extra aqui. inativos,
                                                                 adicionado nesta revisão (12), pedido por Alberto para o
                                                                 regime estatutário (seção 20): a apuração de proventos
                                                                 de aposentadoria/pensão
                                                                 (Cad_Vinculo_Emprego.Tipo_Vinculo=inativo_estatutario)
                                                                 para entes que pagam essas verbas diretamente pela
                                                                 folha, sem RPPS próprio instituído --- mesmo mecanismo
                                                                 que já separa pagamento_autonomo do resto, já que cada
                                                                 apuração é sempre de um único Tipo_Folha: inativos nunca
                                                                 se mistura com a folha mensal dos servidores ativos.

  **Status**                 *enumeração {aberta, calculada,     ---
                             fechada, paga}*                     

  **Data_Fechamento**        *data, opcional*                    ---

  **Numero_Processamento**   *número*                            Adicionado por comentário de Alberto: os sistemas
                                                                 tradicionais de folha não guardam histórico de
                                                                 reprocessamento, o que dificulta identificar diferenças
                                                                 numa eventual obrigação de recálculo. Aqui, mais de um
                                                                 Mov_Rh_Folha_Apuracao pode existir para a mesma
                                                                 combinação Filial+Competência+Tipo_Folha --- cada
                                                                 reprocessamento é um NOVO registro, nunca a edição do
                                                                 anterior --- e Numero_Processamento (1, 2, 3\...) ordena
                                                                 essa sequência.

  **ID_Apuracao_Anterior**   *referência (Mov_Rh_Folha_Apuracao, Aponta para o processamento imediatamente anterior desta
                             autorreferência, opcional)*         mesma combinação Filial+Competência+Tipo_Folha, quando
                                                                 este registro é um reprocessamento --- vazio no primeiro
                                                                 processamento (Numero_Processamento=1).

  **Origem_Tipo**            *enumeração {sistema, migracao}*    sistema: apuração calculada por este módulo. migracao:
                                                                 registro histórico trazido do sistema anterior na virada
                                                                 (seção 9) --- mantido só para consulta, nunca
                                                                 recalculado.

  **ID_Salario_Adicional**   *referência                         Adicionado nesta revisão (11): preenchido só quando
                             (Cad_Rh_Salario_Adicional,          Tipo_Folha=salario_adicional --- identifica QUAL salário
                             opcional)*                          adicional está sendo apurado, permitindo apurar 14º e
                                                                 15º separadamente dentro da mesma competência.

  **Numero_Parcela**         *número, opcional*                  Adicionado nesta revisão (11): preenchido só quando
                                                                 Tipo_Folha=salario_adicional --- identifica qual parcela
                                                                 está sendo apurada, referenciando
                                                                 Cad_Rh_Salario_Adicional_Parcela.Numero_Parcela daquele
                                                                 ID_Salario_Adicional.
  -------------------------- ----------------------------------- --------------------------------------------------------

*Comportamento de aplicação --- reprocessamento de folha: \"último
processamento\" e \"processamento contabilizado\" nunca são campos
armazenados, sempre consultas derivadas sobre a mesma combinação
Filial+Competência+Tipo_Folha. Último processamento é o registro com o
maior Numero_Processamento da combinação. Processamento contabilizado é
o registro que de fato gerou lançamento contábil --- via
Mov_Lote_Lancamento com Origem_Tipo=folha_pagamento (Fase 0, revisão
28), ligado a este Mov_Rh_Folha_Apuracao específico por ID_Origem; os
dois podem divergir --- por exemplo, quando um recálculo
(Numero_Processamento=2) precisa ser contabilizado num período diferente
do original, por não ser mais possível lançar retroativamente no período
já fechado da Contabilidade.*

Mov_Rh_Folha_Item

Cada verba calculada para um colaborador dentro de uma apuração --- a
linha de fato da folha.

*Vigência: não --- é o registro de um evento (o resultado do cálculo);
uma correção depois de a apuração fechar é um novo Mov_Rh_Folha_Item
numa apuração de ajuste, nunca a edição do valor original.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Apuracao** | *referência (Mov_Rh_Folha_Apuracao)* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | --- |
| **ID_Verba** | *referência (Cad_Rh_Verba)* | --- |
| **Quantidade** | *número, opcional* | Preenchido quando a verba é medida em quantidade/horas/dias (ex.: horas extras) --- para hora extra, a quantidade normalmente vem cruzando Mov_Rh_Ponto com Cad_Rh_Escala (seção 6). |
| **Fator_Rubrica** | *número, opcional* | Adicionado na revisão 19 (NT 07/2026). fatorRubr do S-1200: o fator ou percentual da rubrica, quando necessário (por exemplo, 50 para o adicional de 50% de hora extra). Maior que zero quando informado. A Quantidade, que já existe, é o qtdRubr (horas, dias ou outra referência), também maior que zero quando informada. Horista (Unidade_Pagamento = hora, Fase 0): o salário-base é Valor_Salario vezes as horas pagas, que vêm na Quantidade (de Mov_Rh_Ponto e do banco de horas). Dia, semana e quinzena seguem o mesmo princípio. O divisor do valor-hora do mensalista (hora extra, desconto por falta em horas, a partir de Cad_Vinculo_Horario_Contratual. Horas_Semanais) e a origem das horas pagas do horista têm desenho desde a revisão 10 (documento 69, D-N179 a D-N183): o divisor é Cad_Vinculo_Horario_Contratual.Horas_Semanais vezes Cad_Rh_Parametro_Jornada.Multiplicador_Semanas_Valor_Hora (valor inicial 5, decisão de Alberto de 19/10/2026, Q69-1; revisão 12, D-N208); as horas pagas do horista vêm do ponto; o excesso do limite semanal tem a decisão registrada em Mov_Rh_Hora_Excedente_Decisao; e o percentual da hora extra vem de Cad_Rh_Regra_Hora_Extra. O cálculo da folha considera horistas; a alimentação inicial dos dados de horista não é agora (D-N179). O DSR do horista e o reflexo sobre variáveis têm desenho próprio desde a revisão 21 (Cad_Rh_Parametro_Dsr, Cad_Rh_Verba.Reflete_Dsr, seção 6). |
| **Base_Calculo** | *número, opcional* | A base sobre a qual Valor foi calculado, quando a verba é percentual (ex.: base de INSS) --- fidelidade ao cálculo feito, nunca recalculada depois. |
| **Valor** | *número* | O valor final da verba nesta apuração, para este colaborador --- sempre positivo, o sinal/efeito vem de Cad_Rh_Verba.Tipo. Quando Tipo=informativo (adicionado nesta revisão 9), este item fica de fora da soma que compõe o líquido do colaborador --- existe só para gerar lançamento contábil (ex.: a fração individual de uma taxa/desconto global de benefício, seção 17) ---, mesmo comportamento de aplicação em toda a apuração, sem campo de exclusão à parte. |
| **ID_Origem_Ocorrencia** | *identificador, opcional* | Adicionado nesta revisão (10), pedido pela modelagem de pensão alimentícia (seção 18 --- Alberto: \"o mesmo contribuinte tenho 2 ou mais pessoas para receberem o pagamento\"): generaliza este item para suportar MAIS DE UMA ocorrência da mesma Cad_Rh_Verba para o mesmo vínculo dentro da mesma apuração --- caso da verba de desconto de pensão alimentícia, lançada uma vez por Cad_Rh_Pensao_Alimenticia vigente (seção 18), não uma vez por verba. Vazio no caso comum (uma verba, um item, por vínculo/apuração); preenchido com o ID da linha de origem (ex.: Cad_Rh_Pensao_Alimenticia.ID_Pensao) quando a mesma verba pode se repetir --- a combinação ID_Apuracao+ID_Vinculo+ID_Verba deixa de ser única sozinha, passa a ser única junto de ID_Origem_Ocorrencia. Mesmo princípio genérico já usado para diferenciar ocorrências de um mesmo tipo dentro de uma coleção, sem duplicar a estrutura da verba em si. |

*Revisão 10 --- campos alterados: Fator_Rubrica.*

*Revisão 12 --- campos alterados: Fator_Rubrica.*

*Provisão contábil de férias e 13º salário: mesmo padrão genérico de
Mov_Lote_Lancamento.Origem_Tipo (Fase 0, revisão 28) já usado por todos
os módulos que geram lançamento contábil --- o domínio ganhou
folha_pagamento (a liquidação de cada Mov_Rh_Folha_Apuracao paga, com um
Mov_Lancamento por perna de conta_contabil_debito/conta_contabil_credito
resolvida pelo Motor de Regras, ver o comportamento de contabilização
acima) e provisao_ferias_decimo_terceiro (o lançamento mensal de
provisão, calculado como fração do período aquisitivo em curso --- seção
8), mesmo critério usado para toda provisão/baixa já modelada neste
dicionário (ex.: provisao_comissao_venda, em CRM & Vendas).*

*Revisão 18 (Bloco 5): a liquidação da folha lança INSS e IRRF retido só
como provisão contábil, com o crédito na conta de provisão de encargos a
recolher (escolhida pelo Motor de Regras, com o critério
natureza_titulo_folha, Fase 0, revisão 47), e não gera título para essas
duas naturezas. Quando chegam o S-5011 e o S-5012, o título nasce no
Contas a Pagar e a reversão da provisão sai contra o a pagar
(Contabilidade & Fiscal, seção 22.4), mesmo padrão da comissão e do
royalty.*

Tabelas progressivas do INSS e do IRRF (revisão 16)

Hoje só existem o salário mínimo e o limite de renda do dependente; as
faixas ficam em fórmula livre dentro de Cad_Rh_Verba, sem vigência. A
proposta separa três coisas: a tabela (qual imposto e como se calcula),
as faixas (com vigência, uma linha por faixa e por ato legal) e os
parâmetros do IRRF que não são faixa (desconto simplificado, dedução por
dependente e a redução da Lei 15.270/2025).

Cad_Rh_Tabela_Progressiva

Nova na revisão 16 (Bloco 3 da validação geral). Uma linha por tabela de
cálculo. Não tem vigência própria: quem muda com o tempo são as faixas.

*Vigência: não --- o que muda é a faixa
(Cad_Rh_Tabela_Progressiva_Faixa).*

  --------------------------- ---------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**              **Descrição / regra**

  **ID_Tabela_Progressiva**   *identificador*              ---

  **ID_Tipo_Tabela**          *referência                  Valores iniciais: inss_empregado,
                              (Cad_Classe_Sistema, domínio irrf_mensal. Outros tributos
                              = tipo_tabela_progressiva)*  progressivos entram como novo valor do
                                                           domínio.

  **Metodo_Calculo**          *enumeração {faixa_marginal, faixa_marginal: cada faixa é aplicada só
                              aliquota_parcela_deduzir}*   sobre a parte do valor que cai nela
                                                           (INSS do empregado).
                                                           aliquota_parcela_deduzir: acha-se a
                                                           faixa do valor total, aplica-se a
                                                           alíquota e subtrai-se a parcela (IRRF
                                                           mensal).

  **Nome**                    *texto*                      ---
  --------------------------- ---------------------------- ----------------------------------------

Cad_Rh_Tabela_Progressiva_Faixa

Nova na revisão 16 (Bloco 3 da validação geral). Uma faixa da tabela,
com o ato legal que a instituiu.

*Vigência: sim --- o INSS muda a cada janeiro; o IRRF muda por ato.
Regra de integridade: as faixas de uma tabela, na mesma data, não têm
buracos nem sobreposição.*

  ---------------------------- ------------------------------ ----------------------------------------
  **Campo**                    **Tipo lógico**                **Descrição / regra**

  **ID_Faixa**                 *identificador*                ---

  **ID_Tabela_Progressiva**    *referência                    ---
                               (Cad_Rh_Tabela_Progressiva)*   

  **Ordem**                    *número*                       Posição da faixa dentro da tabela, da
                                                              menor para a maior.

  **Valor_Inicial**            *número*                       Limite inferior (exclusive na primeira,
                                                              inclusive nas demais, conforme o
                                                              método).

  **Valor_Final**              *número, opcional*             Vazio = última faixa, sem teto. No INSS,
                                                              o Valor_Final da última faixa é o teto
                                                              do salário de contribuição.

  **Aliquota**                 *número*                       Percentual da faixa.

  **Parcela_Deduzir**          *número, opcional*             Só no método aliquota_parcela_deduzir.

  **Ato_Legal**                *texto*                        Portaria, medida provisória ou lei que
                                                              fixou a faixa. Obrigatório para que a
                                                              folha antiga possa ser recalculada e
                                                              conferida.

  **Situacao_Dado**            *enumeração {provisorio,       Fase 0, seção 9 (validação de dados
                               validado}*                     legais provisórios). A carga inicial
                                                              entra como provisória e só passa a
                                                              validada com a aprovação de RH e
                                                              contador.

  **ID_Instancia_Aprovacao**   *referência                    Validação pela régua de aprovação (Fase
                               (Mov_Aprovacao_Instancia,      0, seção 9).
                               opcional)*                     

  **Vigencia_Inicio**          *data*                         Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                         Último dia em que esta versão vale
                                                              (inclusive). Sempre preenchida:
                                                              31/12/9999 quando o fim é indefinido
                                                              (versão vigente) --- convenção da Fase
                                                              0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*              Por que esta versão foi criada.
  ---------------------------- ------------------------------ ----------------------------------------

Cad_Rh_Parametro_Irrf

Nova na revisão 16 (Bloco 3 da validação geral). Parâmetros do IRRF que
não são faixa. Guarda a redução da Lei 15.270/2025, que zera o imposto
até um limite e reduz gradualmente a partir dele até outro limite.

*Vigência: sim --- a carga inicial reproduz a Lei 15.270/2025 (janeiro
de 2026) e sai marcada como provisória; o contador confere os valores
antes da folha real.*

  ---------------------------- --------------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**             **Descrição / regra**

  **ID_Parametro_Irrf**        *identificador*             ---

  **Desconto_Simplificado**    *número*                    Valor do desconto simplificado mensal.

  **Deducao_Dependente**       *número*                    Dedução mensal por dependente elegível.
                                                           Continua valendo com
                                                           Cad_Rh_Limite_Renda_Dependente_Irrf, que
                                                           fica como está.

  **Limite_Reducao_Total**     *número, opcional*          Renda mensal até a qual o redutor zera o
                                                           imposto.

  **Limite_Reducao_Parcial**   *número, opcional*          Renda mensal acima da qual o redutor
                                                           deixa de existir.

  **Redutor_Valor_Fixo**       *número, opcional*          Parte fixa da fórmula do redutor na
                                                           faixa intermediária.

  **Redutor_Coeficiente**      *número, opcional*          Coeficiente multiplicado pela renda na
                                                           fórmula do redutor.

  **Ato_Legal**                *texto*                     ---

  **Situacao_Dado**            *enumeração {provisorio,    Fase 0, seção 9 (validação de dados
                               validado}*                  legais provisórios). A carga inicial
                                                           entra como provisória e só passa a
                                                           validada com a aprovação de RH e
                                                           contador.

  **ID_Instancia_Aprovacao**   *referência                 Validação pela régua de aprovação (Fase
                               (Mov_Aprovacao_Instancia,   0, seção 9).
                               opcional)*                  

  **Vigencia_Inicio**          *data*                      Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                      Último dia em que esta versão vale
                                                           (inclusive). Sempre preenchida:
                                                           31/12/9999 quando o fim é indefinido
                                                           (versão vigente) --- convenção da Fase
                                                           0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*           Por que esta versão foi criada.
  ---------------------------- --------------------------- ----------------------------------------

Como a folha usa: o cálculo do INSS lê a tabela vigente na competência e
aplica o método da tabela; o do IRRF calcula a base (remuneração menos
INSS, dependentes e o maior entre desconto simplificado e deduções
legais), acha a faixa, subtrai a parcela e depois aplica o redutor de
Cad_Rh_Parametro_Irrf. O 13º e as férias usam a mesma tabela vigente no
mês do pagamento. Nada disso fica em Formula de Cad_Rh_Verba: a fórmula
da verba chama a tabela pelo tipo, e a Formula deixa de guardar
constantes legais.

Rubrica e código de incidência do eSocial (revisão 16)

A rubrica do eSocial (S-1010) é a tabela do próprio empregador: o código
é escolhido por ele (até 30 caracteres) e cada rubrica declara a
natureza (Tabela 03) e um código de incidência para a contribuição
previdenciária, o IRRF, o FGTS e, no regime próprio, a contribuição do
RPPS. Antes desta revisão Cad_Rh_Verba tinha três booleanos de
incidência, um tipo com três valores e apontava para um domínio
rubrica_esocial, como se o eSocial fornecesse a lista de rubricas. Ele
não fornece: a rubrica é a verba.

Em Cad_Rh_Verba (acima), Codigo_Rubrica e Identificador_Tabela_Rubrica
identificam a rubrica no S-1010; ID_Natureza_Rubrica aponta para o
domínio natureza_rubrica_esocial (Tabela 03); os quatro códigos de
incidência apontam para Cad_Rh_Codigo_Incidencia; Incide_Inss,
Incide_Fgts e Incide_Irrf passam a ser calculados a partir deles e
armazenados, para o motor de cálculo continuar lendo os booleanos sem
mexer nas fórmulas; e o antigo ID_Rubrica_Esocial é aposentado, junto
com o domínio rubrica_esocial, que nenhum outro campo usava.

Cad_Rh_Codigo_Incidencia

Nova na revisão 16 (Bloco 3 da validação geral). Os códigos oficiais de
incidência (codIncCP, codIncIRRF, codIncFGTS e codIncCPRP) com a leitura
que o cálculo precisa: incide ou não incide. É entidade, e não domínio,
porque cada código carrega um atributo próprio.

*Vigência: sim --- o eSocial cria e encerra códigos por nota técnica (a
NT 07/2026 prevê novos códigos de incidência previdenciária a partir de
14/12/2026). Revisão 19 (NT 07/2026): o Tributo ganha pis_pasep
(codIncPisPasep do S-1010: 00, 11, 12, 91 e 92; os códigos 91 e 92,
incidência suspensa por decisão judicial, só valem com o grupo de
processo, Cad_Processo, Fase 8) e entram quatro linhas novas de
contribuicao_previdenciaria, os códigos 23 e 24 (salário-paternidade
mensal e do 13º, pago pelo empregador) e 27 e 28 (pago pelo INSS), com
Vigencia_Inicio em 14/12/2026, a data mais restritiva até a confirmação
com a nota técnica (P-39). As naturezas de rubrica correspondentes (4052,
4053, 9928 e 9929, início em 01/12/2026) entram por carga em
natureza_rubrica_esocial (Fase 0).*

  --------------------------------- ------------------------------- ----------------------------------------
  **Campo**                         **Tipo lógico**                 **Descrição / regra**

  **ID_Codigo_Incidencia**          *identificador*                 ---

  **ID_Codigo_Incidencia_Versao**   *identificador da versão*       Chave primária da versão (tabela física
                                                                    Cad_Rh_Codigo_Incidencia_Versao).
                                                                    ID_Codigo_Incidencia é a identidade,
                                                                    única e referenciada pelas outras
                                                                    tabelas; cada versão guarda a sua janela
                                                                    de vigência --- Fase 0, seção 2.

  **Tributo**                       *enumeração                     Identidade, junto com Codigo.
                                    {contribuicao_previdenciaria,   
                                    irrf, fgts, contribuicao_rpps,  
                                    pis_pasep}*                     

  **Codigo**                        *código (2) --- identidade*     Como no leiaute: 00, 11, 12, 13...
                                                                    conforme o tributo.

  **Descricao**                     *texto*                         ---

  **Incide**                        *booleano*                      Verdadeiro quando o código faz a rubrica
                                                                    entrar na base do tributo, ainda que só
                                                                    em parte (ex.: só no 13º). Alimenta os
                                                                    booleanos derivados de Cad_Rh_Verba.

  **Restrito_Ao_Tipo_Rubrica**      *enumeração {qualquer,          Alguns códigos só valem para certos
                                    vencimento, desconto,           tipos; o sistema recusa a combinação
                                    informativa,                    inválida.
                                    informativa_dedutora},          
                                    opcional*                       

  **Vigencia_Inicio**               *data*                          Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                  *data*                          Último dia em que esta versão vale
                                                                    (inclusive). Sempre preenchida:
                                                                    31/12/9999 quando o fim é indefinido
                                                                    (versão vigente) --- convenção da Fase
                                                                    0, seção 2.

  **Motivo_Vigencia**               *texto, opcional*               Por que esta versão foi criada.
  --------------------------------- ------------------------------- ----------------------------------------

6\. Turnos, Escalas e Ponto Eletrônico

Alberto foi explícito: o ponto é INDEPENDENTE do Timesheet --- a empresa
pode escolher usar o Timesheet (já existente no dicionário,
reaproveitado por Produção, Gestão de Contratos e PPM) como FONTE para
preencher o ponto, mas as duas estruturas convivem de forma totalmente
independente quando a empresa preferir. O ponto sempre existe como
entidade própria deste módulo; o Timesheet nunca é substituído por ele,
nem o contrário.

Cad_Rh_Turno

Um turno de trabalho --- horário padrão de entrada, saída e intervalo
--- cadastrado uma vez e reaproveitado por quantos colaboradores tiverem
a mesma jornada.

*Vigência: sim --- um turno pode ter sua carga horária redefinida ao
longo do tempo (ex.: mudança de jornada da empresa); a versão vigente na
data da marcação é sempre a usada para apurar falta/atraso/hora extra
daquele dia.*

  ------------------------------- ----------------- ----------------------------------------
  **Campo**                       **Tipo lógico**   **Descrição / regra**

  **ID_Turno**                    *identificador*   ---

  **ID_Turno_Versao**             *identificador da Chave primária da versão (tabela física
                                  versão*           Cad_Rh_Turno_Versao). ID_Turno é a
                                                    identidade, única e referenciada pelas
                                                    outras tabelas; cada versão guarda a sua
                                                    janela de vigência --- Fase 0, seção 2.

  **Nome**                        *texto*           Ex.: \"Comercial 8h-17h\", \"Turno
                                                    Noturno\".

  **Hora_Entrada**                *hora*            ---

  **Hora_Saida**                  *hora*            ---

  **Duracao_Intervalo_Minutos**   *número*          ---

  **Arredondamento_Minutos**      *número,          Adicionado por comentário de Alberto: a
                                  opcional*         granularidade de arredondamento usada ao
                                                    converter hora extra apurada em saldo de
                                                    banco de horas (seção 7) --- sugestão
                                                    inicial de 5 minutos, mas parametrizável
                                                    por turno, não travada no dicionário.
                                                    Vazio equivale a nenhum arredondamento
                                                    (precisão do minuto).

  **Vigencia_Inicio**             *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                *data*            Último dia em que esta versão vale
                                                    (inclusive). Sempre preenchida:
                                                    31/12/9999 quando o fim é indefinido
                                                    (versão vigente) --- convenção da Fase
                                                    0, seção 2.

  **Motivo_Vigencia**             *texto, opcional* Por que esta versão foi criada.
  ------------------------------- ----------------- ----------------------------------------

Cad_Rh_Escala

A atribuição de um turno a um vínculo de emprego específico --- qual
turno vale para qual colaborador, e a partir de quando.

*Vigência: sim --- a escala de um colaborador muda ao longo do tempo
(mudança de turno, revezamento); a versão vigente na data da marcação é
a usada para apurar o esperado daquele dia.*

  ---------------------- ------------------------ ----------------------------------------
  **Campo**              **Tipo lógico**          **Descrição / regra**

  **ID_Escala**          *identificador*          ---

  **ID_Vinculo**         *referência              ---
                         (Cad_Vinculo_Emprego)*   

  **ID_Turno**           *referência              ---
                         (Cad_Rh_Turno)*          

  **Dia_Semana**         *enumeração {segunda,    Vazio quando o mesmo turno vale todos os
                         terca, quarta, quinta,   dias úteis da semana; preenchido quando
                         sexta, sabado, domingo}, a escala varia por dia (ex.:
                         opcional*                revezamento).

  **Natureza_Periodo**   *enumeração              Adicionado nesta revisão (4), pedido
                         {trabalho_efetivo,       pela verificação de legislação
                         sobreaviso}, opcional*   trabalhista (art. 244 §2º CLT, Súmula
                                                  428 TST): vazio/trabalho_efetivo para
                                                  jornada normal; sobreaviso quando o
                                                  colaborador fica em casa, à disposição,
                                                  sem trabalho efetivo, pago a 1/3 do
                                                  salário-hora (Cad_Rh_Verba, seção 5, sem
                                                  tipo de verba novo), escala máxima 24h.
                                                  Domínio aberto o bastante para acomodar
                                                  prontidão no futuro, se necessário. Não
                                                  cobre \"plantão\" como rótulo --- a
                                                  modelagem segue o conteúdo real do
                                                  período, não o nome popular.

  **Vigencia_Inicio**    *data*                   Primeiro dia em que esta versão vale.

  **Vigencia_Fim**       *data*                   Último dia em que esta versão vale
                                                  (inclusive). Sempre preenchida:
                                                  31/12/9999 quando o fim é indefinido
                                                  (versão vigente) --- convenção da Fase
                                                  0, seção 2.

  **Motivo_Vigencia**    *texto, opcional*        Por que esta versão foi criada.
  ---------------------- ------------------------ ----------------------------------------

Mov_Rh_Ponto

Uma marcação de ponto --- entrada, saída, início ou fim de intervalo.

*Vigência: não --- evento; uma marcação incorreta é corrigida por um
novo registro (ajuste manual), nunca editando a marcação original,
preservando a trilha de auditoria.*

  ----------------- -------------------------------- ---------------------------------------------
  **Campo**         **Tipo lógico**                  **Descrição / regra**

  **ID_Marcacao**   *identificador*                  ---

  **ID_Vinculo**    *referência                      ---
                    (Cad_Vinculo_Emprego)*           

  **Data_Hora**     *data/hora*                      ---

  **Tipo**          *enumeração {entrada, saida,     Os dois últimos valores, adicionados nesta
                    inicio_intervalo, fim_intervalo, revisão (4), marcam o acionamento efetivo
                    inicio_acionamento_sobreaviso,   dentro de um período de sobreaviso
                    fim_acionamento_sobreaviso}*     (Cad_Rh_Escala.Natureza_Periodo=sobreaviso,
                                                     seção 6) --- quando o colaborador é de fato
                                                     chamado, essas horas deixam de ser pagas a
                                                     1/3 e viram hora extra normal a partir do
                                                     chamado, calculada pela mesma apuração de
                                                     falta/atraso/hora extra abaixo.

  **Origem_Tipo**   *enumeração {manual,             Como a marcação chegou ao sistema ---
                    relogio_ponto, app, timesheet}*  referência genérica, mesmo padrão já usado em
                                                     todo o dicionário. timesheet: a empresa optou
                                                     por preencher o ponto a partir do apontamento
                                                     já existente em Timesheet
                                                     (Produção/Contratos/PPM), em vez de
                                                     digitar/marcar de novo --- opção da empresa,
                                                     nunca obrigatória.

  **ID_Origem**     *referência genérica, opcional*  Preenchido só quando Origem_Tipo=timesheet: o
                                                     ID do apontamento de Timesheet de origem.
  ----------------- -------------------------------- ---------------------------------------------

*Comportamento de aplicação --- apuração de falta/atraso/hora extra:
para cada dia, o sistema cruza as marcações de Mov_Rh_Ponto do
colaborador com a Cad_Rh_Escala vigente naquele dia (e o Cad_Rh_Turno
associado) para SUGERIR falta, atraso ou hora extra --- nunca aplicar
automaticamente, mesmo princípio já fixado no Documento Analítico
(\"sempre sugerindo --- nunca aplicando automaticamente --- o
preenchimento de lacunas de marcação\"). Quando a empresa não usa ponto
dedicado e opta por Timesheet como única fonte de apontamento de
jornada, a mesma Cad_Rh_Escala/Cad_Rh_Turno seguem se aplicando para
calcular horas esperadas x apontadas, mesmo cruzamento, só com
Mov_Rh_Ponto.Origem_Tipo=timesheet alimentando as marcações em vez de
relógio/app/manual.*

*Comportamento de aplicação --- controle de GAP: adicionado por
comentário de Alberto, para não deixar uma marcação esquecida bagunçar o
dia seguinte. A apuração NUNCA pareia marcações de dias de referência
diferentes --- o dia de referência de uma marcação é sempre determinado
pelo Cad_Rh_Turno vigente (turno noturno, por exemplo, pode atravessar a
meia-noite, mas a marcação continua pertencendo ao dia de início do
turno). Um dia cujas marcações não completam o padrão esperado pela
Cad_Rh_Escala (ex.: entrada sem saída correspondente) fica sinalizado
como PENDÊNCIA (GAP) --- sempre uma consulta derivada, nunca um campo
armazenado, mesmo princípio de nunca guardar o que pode ser derivado já
usado no resto do dicionário. Fechar um GAP é sempre um ajuste manual
(novo Mov_Rh_Ponto, Origem_Tipo=manual) datado dentro do próprio dia
incompleto --- nunca aproveitando a marcação do dia seguinte para fechar
a pendência do anterior.*

*Comportamento de aplicação --- adicional noturno: também derivado da
mesma apuração, não um cadastro próprio. As horas efetivamente
trabalhadas dentro da janela noturna definida por Cad_Rh_Turno geram o
adicional automaticamente a partir do cruzamento de Mov_Rh_Ponto com a
escala, alimentando uma Cad_Rh_Verba própria (seção 5) na apuração de
folha --- mesma lógica de falta/atraso/hora extra, sempre uma regra de
cálculo da apuração de ponto, nunca uma condição cadastrada como
insalubridade/periculosidade (seção 13).*

Abono de falta/atraso: adicionado nesta revisão (5), a partir de
comentário de Alberto --- a base para o gestor abonar falta/atraso do
colaborador, escolhida deliberadamente SIMPLES (\"neste caso um abono
mais simples pois vai ter vários níveis de gestores independentes\"):
sem régua de aprovação em cadeia
(Cad_Regua_Aprovacao/Mov_Aprovacao_Instancia, Fase 0), pois com vários
níveis de gestor independentes uma régua fixa exigiria decidir de
antemão QUAL gestor aprova, o que a estrutura organizacional real desta
empresa não garante. Em vez disso, qualquer gestor com
Cad_Vinculo_Emprego.ID_Gestor apontando (direta ou, por herança da mesma
consulta hierárquica já usada no banco de horas, indiretamente) para o
vínculo do colaborador pode registrar o abono --- um único registro, sem
etapas.

Mov_Rh_Ponto_Abono

O abono de uma falta ou atraso --- a decisão do gestor de que aquela
ocorrência sugerida pela apuração de ponto (seção 6) não deve gerar
desconto nem refletir negativamente na folha ou no DSR.

*Vigência: não --- evento; um abono concedido por engano é corrigido por
um novo registro de estorno, nunca a edição/exclusão do original,
preservando a trilha de quem abonou o quê.*

  --------------------- ------------------------ ----------------------------------------
  **Campo**             **Tipo lógico**          **Descrição / regra**

  **ID_Abono**          *identificador*          ---

  **ID_Vinculo**        *referência              O colaborador cuja falta/atraso está
                        (Cad_Vinculo_Emprego)*   sendo abonado.

  **Data_Abonada**      *data*                   O dia da falta/atraso sugerido pela
                                                 apuração de ponto (seção 6) que este
                                                 abono cobre.

  **Tipo**              *enumeração {falta,      ---
                        atraso}*                 

  **ID_Gestor_Abono**   *referência              Quem concedeu o abono --- validado por
                        (Cad_Vinculo_Emprego)*   aplicação como sendo gestor (direto ou
                                                 hierarquicamente acima) do vínculo
                                                 abonado, via
                                                 Cad_Vinculo_Emprego.ID_Gestor (seção 3);
                                                 não travado estruturalmente aqui, mesmo
                                                 critério de responsabilidade de
                                                 aplicação já usado no resto deste
                                                 dicionário para regras que dependem de
                                                 hierarquia.

  **Motivo**            *texto*                  Texto livre --- ex.: \"atestado médico
                                                 entregue fora do prazo do ponto\",
                                                 \"falha do relógio de ponto reportada
                                                 pelo colaborador\".
  --------------------- ------------------------ ----------------------------------------

*Efeito na apuração: um dia com Mov_Rh_Ponto_Abono correspondente deixa
de ser contado como falta/atraso descontável na apuração de folha (seção
5) e no cálculo de DSR --- sempre pela PRESENÇA do registro de abono,
nunca por um campo de status sobrescrito na apuração original (mesmo
princípio de nunca guardar o que pode ser derivado já usado em todo o
dicionário). Acesso de RH a documentos médicos do colaborador (ex.:
atestado que fundamenta o abono) já está coberto pelo GED reaproveitado
em Mov_Rh_Ficha_Evento (seção 12) --- o abono em si não duplica esse
documento, só referencia o dia; quando o abono se apoia num atestado, o
atestado é anexado como Mov_Rh_Ficha_Evento (tipo \"Atestado Médico\",
já dentro do catálogo genérico de ausência legal justificada citado na
seção 12), e Mov_Rh_Ponto_Abono.Motivo descreve a ligação em texto
livre, sem campo estruturado de referência cruzada nesta revisão.*

*Revisão 21: o abono continua sendo a decisão do gestor, e Mov_Rh_Ausencia classifica as faltas que não foram abonadas (Cad_Rh_Tipo_Ausencia define se descontam o dia e se fazem perder o DSR). O abono prevalece sobre a classificação.*

Cad_Rh_Tipo_Ausencia

Nova na revisão 21 (P-42, descanso semanal remunerado). O catálogo dos tipos de ausência do colaborador e do que cada um provoca na folha: se desconta o dia e se faz perder o descanso semanal remunerado (DSR), art. 6º da Lei 605/1949. Decisão de Alberto (05/10/2026): a regra não fica fixa no sistema; cada empresa define o efeito de cada tipo, inclusive o da falta justificada que a lei não prevê (art. 6º, §1º, alínea b, "a critério da administração do estabelecimento"). Carga inicial editável, uma linha por motivo justificado do art. 6º, §1º (artigo 473 da CLT; ausência justificada pela administração; paralisação por conveniência do empregador; casamento até três dias; acidente do trabalho; doença comprovada), mais "Ponte de feriado" (paralisação por conveniência do empregador, usada por Cad_Rh_Feriado_Ponte) e "Falta injustificada".

*Vigência: sim --- o efeito de um tipo na folha pode mudar por convenção, acordo ou decisão da empresa; a folha de uma competência já fechada continua apurada pela versão da época.*

  ------------------------------------ ---------------------------------- ----------------------------------------------------
  **Campo**                            **Tipo lógico**                    **Descrição / regra**

  **ID_Tipo_Ausencia**                 *identificador*                    ---

  **ID_Tipo_Ausencia_Versao**          *identificador da versão*          Chave primária da versão (tabela física
                                                                          Cad_Rh_Tipo_Ausencia_Versao). ID_Tipo_Ausencia é a
                                                                          identidade, única e referenciada pelas outras
                                                                          tabelas; cada versão guarda a sua janela de vigência
                                                                          --- Fase 0, seção 2.

  **ID_Empresa**                       *referência (Cad_Empresa)*         Tipos de ausência são configuráveis por empresa,
                                                                          como as verbas.

  **Nome**                             *texto*                            Ex.: "Casamento (até 3 dias)", "Doença comprovada",
                                                                          "Acidente de trabalho", "Falta justificada pela
                                                                          empresa", "Ponte de feriado", "Falta injustificada".

  **Fundamento_Legal**                 *texto, opcional*                  O artigo, a cláusula coletiva ou o ato interno que
                                                                          fundamenta o tipo (ex.: "Lei 605/1949, art. 6º, §1º,
                                                                          d").

  **Desconta_Dia**                     *booleano*                         Verdadeiro quando a ausência desconta o dia (ou as
                                                                          horas) trabalhado. Falso nos motivos justificados e
                                                                          na ponte de feriado.

  **Perde_Dsr**                        *booleano*                         Verdadeiro quando a ausência conta para a perda do
                                                                          repouso da semana (art. 6º). Só entra na contagem de
                                                                          Cad_Rh_Parametro_Dsr.Minimo_Faltas_Semana_Perde_Dsr
                                                                          quando verdadeiro e quando não há abono do dia.

  **Exige_Comprovante**                *booleano*                         Verdadeiro quando o tipo pede documento (atestado,
                                                                          certidão). O documento fica em Mov_Rh_Ficha_Evento,
                                                                          pelo GED já reaproveitado.

  **ID_Tipo_Evento_Ficha**             *referência                        O tipo de evento da ficha que equivale a este tipo
                                       (Cad_Rh_Tipo_Evento_Ficha,         de ausência: um evento de afastamento já registrado
                                       opcional)*                         classifica os dias que cobre, sem digitar duas vezes
                                                                          em Mov_Rh_Ausencia.

  **Vigencia_Inicio**                  *data*                             Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                     *data*                             Último dia em que esta versão vale (inclusive).
                                                                          Sempre preenchida: 31/12/9999 quando o fim é
                                                                          indefinido (versão vigente) --- convenção da Fase 0,
                                                                          seção 2.

  **Motivo_Vigencia**                  *texto, opcional*                  Por que esta versão foi criada.
  ------------------------------------ ---------------------------------- ----------------------------------------------------

Mov_Rh_Ausencia

Nova na revisão 21 (P-42). Uma ausência do colaborador num dia, classificada por um tipo de Cad_Rh_Tipo_Ausencia. A apuração de ponto (seção 6) sugere a falta; o RH ou o gestor a classifica aqui. Uma falta sem classificação recebe o tipo padrão de Cad_Rh_Parametro_Dsr (ID_Tipo_Ausencia_Padrao). O abono (Mov_Rh_Ponto_Abono) prevalece sobre a classificação: com abono, o dia não desconta e não faz perder o DSR, qualquer que seja o tipo.

*Vigência: não --- evento; uma classificação incorreta é corrigida por um novo registro de estorno, nunca editando o original, preservando a trilha de auditoria.*

  ------------------------------ ------------------------------------ ------------------------------------------------------
  **Campo**                      **Tipo lógico**                      **Descrição / regra**

  **ID_Ausencia**                *identificador*                      ---

  **ID_Vinculo**                 *referência (Cad_Vinculo_Emprego)*   O colaborador ausente.

  **Data**                       *data*                               O dia da ausência. Para ausências de vários dias, um
                                                                      registro por dia.

  **ID_Tipo_Ausencia**           *referência (Cad_Rh_Tipo_Ausencia)*  A classificação da ausência. A versão vigente na Data
                                                                      é a que vale.

  **Horas_Ausentes**             *número, opcional*                   Horas da ausência parcial (horista ou falta de parte
                                                                      do dia). Vazio = dia inteiro, medido pela escala do
                                                                      dia (Cad_Rh_Escala e Cad_Rh_Turno).

  **ID_Ficha_Evento**            *referência (Mov_Rh_Ficha_Evento,    O documento que fundamenta a ausência (atestado,
                                 opcional)*                           certidão), quando o tipo pede comprovante.

  **ID_Gestor_Registro**         *referência (Cad_Vinculo_Emprego)*   Quem classificou a ausência. Validado por aplicação
                                                                      como gestor do vínculo, mesmo critério do abono.

  **Observacao**                 *texto, opcional*                    Texto livre.
  ------------------------------ ------------------------------------ ------------------------------------------------------

Cad_Rh_Parametro_Dsr

Nova na revisão 21 (P-42). Os parâmetros do descanso semanal remunerado por empresa, com refinamento opcional por categoria sindical (o mais específico vence, mesmo princípio de Cad_Rh_Categoria_Sindical). Decisão de Alberto (05/10/2026): nada é fixo no sistema --- critério de dias úteis, incorporação do DSR ao valor da hora, perda do DSR e forma de pagar o feriado trabalhado são todos parâmetros.

*Vigência: sim --- convenção coletiva e decisão da empresa mudam as regras; a folha fechada continua apurada pela versão da época.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Parametro_Dsr** | *identificador* | --- |
| **ID_Parametro_Dsr_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Rh_Parametro_Dsr_Versao). ID_Parametro_Dsr é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa)* | --- |
| **ID_Categoria_Sindical** | *referência (Cad_Rh_Categoria_Sindical, opcional)* | Vazio: vale para toda a empresa. Preenchido: vale só para os vínculos dessa categoria sindical e prevalece sobre o parâmetro geral. |
| **Criterio_Dias_Uteis** | *enumeração {segunda_a_sabado, segunda_a_sexta}* | Quais dias contam como úteis no divisor do DSR. Valor usual: segunda_a_sabado (o sábado conta como dia útil, salvo se for feriado, segundo o guia do DSR do horista enviado por Alberto); a convenção coletiva pode adotar outro. |
| **Dsr_Incorporado_Hora** | *booleano* | Verdadeiro quando a norma coletiva incorpora o DSR ao valor da hora do horista (Tema 1.046 do STF; jurisprudência do TRT-2 de 2025 e 2026). Nesse caso o motor não gera verba de DSR para o horista. |
| **Percentual_Dsr_Incorporado** | *número, opcional* | Obrigatório e maior que zero quando Dsr_Incorporado_Hora é verdadeiro (ex.: 16,667, que é 1/6). Serve para destacar o DSR dentro do valor da hora no demonstrativo; a verba não identificada tem sido tratada como salário complessivo (Súmula 91 do TST). |
| **ID_Verba_Dsr_Horista** | *referência (Cad_Rh_Verba, opcional)* | A verba que recebe o DSR do horista. Obrigatória quando Dsr_Incorporado_Hora é falso. |
| **ID_Tipo_Ausencia_Padrao** | *referência (Cad_Rh_Tipo_Ausencia)* | O tipo aplicado a uma falta sugerida pela apuração de ponto que ninguém classificou. Normalmente "Falta injustificada". |
| **Minimo_Faltas_Semana_Perde_Dsr** | *inteiro* | Quantas faltas da semana, com tipo Perde_Dsr e sem abono, fazem perder o DSR. Perde-se um DSR por semana, nunca um por falta. Decisão de Alberto (05/10/2026): 2 ou mais faltas na semana anterior. O valor 1 reproduz o art. 6º da Lei 605 (a lei não devolve a remuneração a quem não trabalhou "durante toda a semana anterior", ou seja, uma só falta injustificada já basta). Valor inicial 2, reafirmado por Alberto em 19/10/2026 (revisão 12, D-N208), alterável por empresa e por versão nova com vigência. A fonte do limite de 2 ("regra da Receita") não foi localizada; o 1 continua descrito como leitura do art. 6º da Lei 605. Revisão 15 (D-N234, Q74-6): texto de confirmação que o operador vê antes de descontar o DSR: "Nesta semana o colaborador tem {n} faltas sem abono do tipo perde DSR. Pela regra da empresa (mínimo de {limite} na semana), o descanso remunerado de {data} será descontado: {valor}. Confirmar o desconto?", com as opções confirmar o desconto e abonar as faltas. O texto não cita artigo de lei, porque a fonte do limite de 2 não foi localizada. |
| **Falta_Faz_Perder_Feriado_Da_Semana** | ** | Decisão de Alberto: parâmetro por empresa. Verdadeiro quando a semana com perda de DSR perde também os feriados que caem nela. |
| **Feriado_Trabalhado_Forma** | *enumeração {pagamento_em_dobro, folga_em_outro_dia}* | Forma padrão de compensar o feriado trabalhado (art. 9º da Lei 605: remuneração em dobro, salvo se o empregador determinar outro dia de folga). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 12 --- campos alterados: Minimo_Faltas_Semana_Perde_Dsr.*

*Revisão 15 --- campos alterados: Minimo_Faltas_Semana_Perde_Dsr.*

Cad_Rh_Feriado_Ponte

Nova na revisão 21 (P-42), pedida por Alberto (05/10/2026). O feriado ponte: o dia útil que a empresa decide emendar entre um feriado e o repouso (ex.: feriado na terça-feira, a empresa dá a segunda-feira). A ponte não é feriado legal e é decisão da empresa, por isso não entra em Cad_Feriado. Decisão de Alberto: quando é ponte, não se desconta --- é folga remunerada, sem desconto do dia, sem falta e sem perda de DSR (paralisação por conveniência do empregador, art. 6º, §1º, alínea c, da Lei 605).

*Vigência: não --- cada linha é a decisão de uma ponte, como cada linha de Cad_Feriado é um dia; uma ponte desfeita é cancelada com motivo, nunca excluída.*

  ------------------------------------ ---------------------------------- ----------------------------------------------------
  **Campo**                            **Tipo lógico**                    **Descrição / regra**

  **ID_Feriado_Ponte**                 *identificador*                    ---

  **ID_Empresa**                       *referência (Cad_Empresa)*         A empresa que decidiu a ponte.

  **ID_Feriado**                       *referência (Cad_Feriado)*         O feriado que originou a ponte (ex.: a terça-feira).

  **Data_Ponte**                       *data*                             O dia útil emendado (ex.: a segunda-feira). O
                                                                          sistema avisa, sem bloquear, quando o dia não está
                                                                          entre o feriado e o repouso.

  **ID_Filial**                        *referência (Cad_Filial,           Abrangência. Vazio: todas as filiais.
                                       opcional)*

  **ID_Categoria_Sindical**            *referência                        Abrangência. Vazio: todas as categorias. O feriado
                                       (Cad_Rh_Categoria_Sindical,        de origem continua valendo só para os vínculos cujo
                                       opcional)*                         município de trabalho o contempla.

  **ID_Tipo_Ausencia**                 *referência                        O tipo aplicado ao dia. A carga inicial traz "Ponte
                                       (Cad_Rh_Tipo_Ausencia)*            de feriado". A aplicação recusa um tipo com
                                                                          Desconta_Dia ou Perde_Dsr verdadeiros.

  **Data_Comunicacao**                 *data, opcional*                   Quando a empresa avisou os empregados da ponte.

  **Cancelada_Em**                     *data, opcional*                   Preenchida quando a empresa desfaz a ponte.

  **Motivo_Cancelamento**              *texto, opcional*                  Obrigatório quando Cancelada_Em é preenchida.
  ------------------------------------ ---------------------------------- ----------------------------------------------------

*Comportamento de aplicação --- DSR e feriado ponte (revisão 21, P-42): tudo o que segue é derivado de cadastros e de movimentos, nunca guardado. O valor final de cada verba fica em Mov_Rh_Folha_Item (Quantidade e Base_Calculo).*

*Município de trabalho e feriados: o município de trabalho do vínculo no dia é Cad_Vinculo_Lotacao.ID_Municipio_Trabalho, quando preenchido, ou o município do estabelecimento da lotação; vale também para trabalho externo, teletrabalho e híbrido, que seguem o município em que o vínculo está registrado na empresa (decisão de Alberto). Um dia de Cad_Feriado conta para o vínculo quando Vale_Descanso_Trabalhista é verdadeiro e: a abrangência é nacional; ou é estadual e o estado é o do município de trabalho; ou é municipal e o município é o de trabalho. A Lei 9.093/1995 define os feriados civis (lei federal, data magna do estado, centenário do município) e limita os religiosos a quatro por município, incluída a Sexta-Feira da Paixão; passar de quatro gera aviso, sem bloqueio.*

*Dias de repouso e dias úteis: os dias de repouso do mês vêm da escala do vínculo (Cad_Rh_Escala e Cad_Vinculo_Horario_Contratual.Tipo_Jornada), não necessariamente o domingo (a lei diz "preferentemente aos domingos"); feriado que cai em dia de repouso conta uma vez. Os dias úteis seguem Cad_Rh_Parametro_Dsr.Criterio_Dias_Uteis. A fórmula de uma verba pode usar as variáveis de calendário DIAS_UTEIS_MES, DIAS_REPOUSO_MES e DSR_PERDIDOS_MES, e as semanais TAREFAS_SEMANA e DIAS_TRABALHADOS_SEMANA, todas calculadas pelo motor e nunca armazenadas.*

*Perda do DSR: a semana é a que antecede cada dia de repouso, contada do repouso anterior (de domingo a sábado no caso comum). Perde-se um DSR na semana em que o vínculo tem, sem abono, ao menos Minimo_Faltas_Semana_Perde_Dsr ausências cujo tipo tem Perde_Dsr; nunca mais de um por semana. Se Falta_Faz_Perder_Feriado_Da_Semana é verdadeiro, a semana com perda também perde os feriados que caem nela. Na jornada reduzida, a frequência exigida é a dos dias em que o vínculo tem de trabalhar (art. 6º, §3º), lidos da escala. O abono (Mov_Rh_Ponto_Abono) e o dia de ponte nunca contam como ausência.*

*Horista: DSR = horas normais pagas do mês ÷ dias úteis × (dias de repouso − DSR perdidos) × valor da hora normal, em verba própria (Cad_Rh_Parametro_Dsr.ID_Verba_Dsr_Horista). O bruto do horista já sai com as faltas e os DSR perdidos descontados, então não há desconto adicional na base de INSS, FGTS e IRRF. Com Dsr_Incorporado_Hora verdadeiro, o motor não gera a verba. Um conjunto de exemplos com faltas e sem faltas foi conferido com o guia "DSR - Horista" (Guia Trabalhista) e reproduz seus valores.*

*Reflexo sobre variáveis: cada Cad_Rh_Verba com Reflete_Dsr (horas extras habituais, comissão, adicional noturno) gera o DSR sobre ela, em cálculo separado do salário fixo: total da verba no mês ÷ dias úteis × dias de repouso, na verba indicada em ID_Verba_Dsr_Reflexo (art. 7º, alíneas a e b, da Lei 605, com a redação da Lei 7.415/1985). Evita-se o cálculo de DSR sobre DSR (a verba de reflexo não pode ter Reflete_Dsr). Quanto à média de férias, 13º, aviso prévio e FGTS: pelo Tema 9 do TST (OJ 394 da SBDI-1), a majoração do DSR pelas horas extras habituais trabalhadas a partir de 20/03/2023 repercute nessas parcelas; antes dessa data não repercutia (bis in idem). A inclusão é controlada por Compoe_Media_Ferias e Compoe_Media_Decimo_Terceiro da verba de reflexo, que têm vigência, e o Mov_Rh_Processo_Trabalhista_Apuracao respeita a data.*

*Mensalista e quinzenalista: o repouso já está embutido no salário (art. 7º, §2º) quando o cálculo do salário e dos descontos usa 30 ou 15 diárias; não há verba de DSR sobre o salário fixo. A falta cujo tipo tem Desconta_Dia desconta o dia e, se tem Perde_Dsr e a regra de perda se cumpre, desconta também o repouso, pela Formula da verba de desconto. Tarefeiro e trabalho em domicílio (art. 7º, alíneas c e d): o motor entrega as variáveis semanais (tarefas e dias trabalhados) à Formula; o em domicílio usa a produção da semana dividida por 6.*

*Quem tem DSR: servidores estatutários e funcionários públicos ficam fora (art. 5º, alíneas b e c), o que se configura em Cad_Rh_Verba_Tipo_Vinculo; os domésticos, antes excluídos pela alínea a, foram incluídos pela Lei 11.324/2006 (alínea revogada).*

*Feriado trabalhado e ponte: o feriado trabalhado é pago na forma de Cad_Rh_Parametro_Dsr.Feriado_Trabalhado_Forma (em dobro ou folga em outro dia). O dia de Cad_Rh_Feriado_Ponte, com ponto ou não, nunca é feriado legal: não desconta, não conta como falta, não faz perder DSR, permanece dia útil no divisor e fora dos dias de repouso; quem trabalha nele cumpre jornada normal, sem dobro. Para o horista, as horas da jornada do dia entram como horas normais pagas e compõem a base do DSR. Para o mensalista, nenhum desconto.*

*Continua em aberto com o RH e o contador (P-42): o divisor do valor-hora do mensalista (hora extra e desconto por falta em horas, a partir de Cad_Vinculo_Horario_Contratual.Horas_Semanais), a origem das horas pagas do horista e a confirmação do limite de duas faltas por semana (Minimo_Faltas_Semana_Perde_Dsr).*

7\. Banco de Horas

Adicionado por comentário de Alberto: hora extra pode ser paga ao
colaborador OU compor banco de horas --- \"não necessariamente é um
parâmetro por empresa, as horas extras deste colaborador vai para banco
de horas ou será paga\", decisão tomada caso a caso, a cada ocorrência,
não uma configuração fixa da empresa. Por isso o destino não é um campo
armazenado à parte: é o PRÓPRIO REGISTRO gerado a partir da hora extra
sugerida pela apuração de ponto (seção 6) que decide --- vira um
Mov_Rh_Folha_Item de uma verba de hora extra (quando paga) ou um
Mov_Rh_Banco_Horas_Movimento de crédito (quando vai para o banco), nunca
os dois ao mesmo tempo.

Mov_Rh_Banco_Horas_Movimento

Um movimento de crédito ou débito no banco de horas de um vínculo --- a
hora extra convertida em saldo (crédito) ou o consumo desse saldo como
folga (débito).

*Vigência: não --- evento; o saldo de banco de horas de um vínculo NUNCA
é armazenado --- é sempre uma consulta somando créditos e subtraindo
débitos, mesmo princípio de nunca guardar o que pode ser derivado já
usado em todo o dicionário. Uma correção é um novo movimento de ajuste,
nunca a edição de um movimento já registrado.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Movimento** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | --- |
| **Data** | *data* | --- |
| **Tipo** | *enumeração {credito, debito}* | --- |
| **Origem_Tipo** | *enumeração {hora_extra, consumo_folga, ajuste, pagamento_vencimento, pagamento_solicitado_gestor, quitacao_rescisao}* | hora_extra: crédito originado da apuração de ponto (seção 6), quando o destino escolhido foi banco de horas. consumo_folga: débito quando o colaborador tira folga usando o saldo. ajuste: correção manual, quando necessário. pagamento_vencimento e pagamento_solicitado_gestor, adicionados na revisão 4, pedidos pela verificação de legislação trabalhista (art. 59 §§2º-3º CLT): débito automático quando um crédito passa de Data_Limite_Compensacao sem ser consumido (pagamento_vencimento, gerando Mov_Rh_Folha_Item de hora extra correspondente, incondicionalmente) ou quando o gestor solicita a conversão antecipada, antes do vencimento (pagamento_solicitado_gestor). quitacao_rescisao, adicionado na revisão 5, pedido por Alberto (verificação de completude da rescisão): débito automático de todo o saldo remanescente na data de Cad_Vinculo_Emprego.Data_Desligamento, gerando o Mov_Rh_Folha_Item de hora extra correspondente dentro da própria Mov_Rh_Folha_Apuracao de rescisão --- mesmo efeito de pagamento_vencimento, mas disparado pelo desligamento em vez de pelo prazo de compensação vencer --- referência genérica, mesmo padrão já usado em todo o dicionário. |
| **ID_Origem** | *identificador do registro de origem, opcional* | Conforme Origem_Tipo: referência à apuração de ponto que gerou o crédito, quando Origem_Tipo=hora_extra; vazio para um ajuste sem origem estruturada. |
| **ID_Decisao_Excedente** | *referência (Mov_Rh_Hora_Excedente_Decisao, opcional)* | Novo na revisão 10 (documento 69, D-N182). Preenchida quando Origem_Tipo = hora_extra: a decisão do gestor (ou do RH, sem gestor) que mandou o excesso de horas para o banco. |
| **Horas** | *número* | A quantidade de horas do movimento --- sempre positiva, o sinal vem de Tipo, mesmo padrão já usado em Cad_Rh_Verba.Tipo/Mov_Rh_Folha_Item.Valor (seção 5). |
| **Data_Limite_Compensacao** | *data, opcional* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista: preenchida só quando Tipo=credito --- a data do crédito mais o parâmetro de meses de Cad_Rh_Parametro_Jornada.Prazo_Compensacao_Meses (revisão 10, D-N180; vazio: a empresa não definiu e o sistema não vence créditos) (a CLT permite até 6 meses por acordo individual escrito, ou até 1 ano por convenção/acordo coletivo, art. 59 §§2º-3º), parametrizável (mesmo espírito de Cad_Rh_Turno.Arredondamento_Minutos, seção 6). Passado este prazo sem consumo, o débito de pagamento_vencimento é gerado incondicionalmente. Créditos com este prazo próximo e ainda não consumidos ficam visíveis ao gestor (Cad_Vinculo_Emprego.ID_Gestor, seção 3), que pode agir antes do vencimento --- consulta derivada, sem entidade nova para o alerta em si. |
| **Percentual_Hora_Extra_Origem** | *número, opcional* | Novo na revisão 10 (documento 69, D-N182). Só em crédito: o percentual da hora de origem (50 se a origem era de 50%, 100 se era de 100%), que o pagamento do saldo vencido aplica ao Mov_Rh_Folha_Item.Fator_Rubrica. O pagamento sai na próxima folha depois do vencimento de cada crédito; a alocação do débito aos créditos mais antigos fica em Mov_Rh_Banco_Horas_Consumo. |
| **Observacao** | *texto, opcional* | --- |

*Revisão 10 --- campos novos: ID_Decisao_Excedente, Percentual_Hora_Extra_Origem; campos alterados: Data_Limite_Compensacao.*

*Precisão do banco de horas: adicionado por comentário de Alberto ---
\"no caso de banco de horas inicialmente poderia ter a precisão de 5
minutos.\" O arredondamento não é um valor fixo deste dicionário: vem de
Cad_Rh_Turno.Arredondamento_Minutos (seção 6), aplicado no momento em
que a hora extra sugerida pela apuração de ponto vira um
Mov_Rh_Banco_Horas_Movimento.Horas de crédito --- parametrizável por
turno, para não travar 5 minutos como regra universal caso a Mlegate
precise de outra granularidade no futuro.*

*Acesso --- RH e gestor do colaborador: Alberto foi explícito de que RH
e os gestores dos colaboradores precisam ter acesso à composição e ao
consumo dessas horas. RH já está coberto pelo escopo de
filial/departamento de Cad_Usuario_Escopo (seção 14). Visão do gestor
usa o novo Cad_Vinculo_Emprego.ID_Gestor (seção 3): um gestor enxerga o
banco de horas de todo vínculo cuja ID_Gestor aponte para o seu próprio
ID_Vinculo --- sempre uma consulta pela hierarquia, sem uma nova
entidade de escopo dedicada.*

8\. Férias

Período aquisitivo e gozo, separados em duas entidades --- mesmo padrão
já usado no resto do dicionário para separar o direito que se acumula
(ex.: Cad_Ativo_Imobilizado_Plano_Manutencao) do evento que o consome
(Mov_Ativo_Manutencao).

Mov_Rh_Ferias_Periodo

Um período aquisitivo de férias --- os 12 meses que dão direito a 30
dias de descanso.

*Vigência: não --- cada período aquisitivo é um registro próprio, um por
ciclo de 12 meses do vínculo; o status (aberto, gozado parcial/total,
vencido) nunca é armazenado --- é sempre uma CONSULTA cruzando este
registro com os gozos associados (Mov_Rh_Ferias_Gozo, abaixo), mesmo
princípio de nunca guardar o que pode ser derivado já usado em todo o
dicionário.*

  ---------------------------- ------------------------ ----------------------------------------
  **Campo**                    **Tipo lógico**          **Descrição / regra**

  **ID_Periodo**               *identificador*          ---

  **ID_Vinculo**               *referência              ---
                               (Cad_Vinculo_Emprego)*   

  **Data_Inicio_Aquisitivo**   *data*                   ---

  **Data_Fim_Aquisitivo**      *data*                   ---

  **Data_Limite_Concessao**    *data*                   O prazo legal para conceder o gozo a
                                                        partir do fim do período aquisitivo ---
                                                        informado diretamente nesta revisão, não
                                                        recalculado automaticamente a partir de
                                                        uma regra fixa, para não travar a
                                                        estrutura a um número de meses que pode
                                                        mudar.
  ---------------------------- ------------------------ ----------------------------------------

Mov_Rh_Ferias_Gozo

Um gozo de férias --- total ou parcelado --- referente a um período
aquisitivo específico. Passa a nascer, desde a revisão 10, como uma
SOLICITAÇÃO feita pelo colaborador no Portal do Colaborador (seção 18),
não mais só um lançamento direto do RH --- ver Status e o fluxo de duas
etapas abaixo.

*Vigência: não --- evento; um gozo cancelado (ex.: interrompido por
doença) gera um novo registro negativo/de ajuste, nunca a edição do
original. Uma solicitação rejeitada também não é reaberta --- o
colaborador solicita de novo, gerando um Mov_Rh_Ferias_Gozo próprio.*

  ---------------------------------- -------------------------- ----------------------------------------------------
  **Campo**                          **Tipo lógico**            **Descrição / regra**

  **ID_Gozo**                        *identificador*            ---

  **ID_Periodo**                     *referência                ---
                                     (Mov_Rh_Ferias_Periodo)*   

  **Data_Inicio_Gozo**               *data*                     ---

  **Data_Fim_Gozo**                  *data*                     ---

  **Dias_Gozados**                   *número*                   ---

  **Dias_Abono_Pecuniario**          *número, opcional*         Dias vendidos (\"abono de 1/3\"), quando o
                                                                colaborador optou por converter parte do período em
                                                                pagamento em vez de descanso --- já cobre o
                                                                comentário de Alberto sobre venda de férias.

  **Adiantar_13_Salario**            *booleano, opcional*       Adicionado por comentário de Alberto: verdadeiro
                                                                quando o colaborador solicitou receber a 1ª parcela
                                                                do 13º salário junto com este gozo de férias, em vez
                                                                de esperar o calendário normal de novembro --- opção
                                                                legal distinta, não o
                                                                Tipo_Folha=decimo_terceiro_primeira_parcela regular.

  **ID_Apuracao_13_Adiantado**       *referência                Preenchida quando Adiantar_13_Salario=verdadeiro:
                                     (Mov_Rh_Folha_Apuracao,    aponta para a apuração extraordinária de
                                     opcional)*                 Tipo_Folha=decimo_terceiro_primeira_parcela (seção
                                                                5), gerada fora do calendário normal, na competência
                                                                deste gozo --- a mesma estrutura que já permite mais
                                                                de um processamento por
                                                                Filial+Competência+Tipo_Folha (Numero_Processamento,
                                                                seção 5) comporta essa apuração avulsa sem mudança
                                                                estrutural.

  **Origem_Tipo**                    *enumeração {sistema,      sistema: gozo registrado e apurado por este módulo.
                                     migracao}*                 migracao: gozo histórico trazido do sistema anterior
                                                                na virada (seção 9, exemplo explícito de Alberto)
                                                                --- mantido para consulta e para não conceder de
                                                                novo um período já gozado antes da virada.

  **Status**                         *enumeração {solicitado,   Adicionado nesta revisão (10), pedido por Alberto
                                     aprovado_gestor,           (\"o pedido de férias tem que ser aprovado pelo
                                     confirmado_rh,             gestor\... Apesar da aprovação do Gestor, a equipe
                                     rejeitado_gestor,          da folha que vai fazer a validação final, pois tem
                                     rejeitado_rh, cancelado}*  que ver se é possível fazer o atendimento das
                                                                férias\"): fluxo simplificado de duas etapas --- não
                                                                o motor genérico de Cad_Regua_Aprovacao (Fase 0),
                                                                decisão explícita de Alberto (\"usar o padrão
                                                                simplificado pois tem a questão de tipo de
                                                                aprovadores bem diferente\"). solicitado:
                                                                recém-criado pelo colaborador no portal, aguardando
                                                                o gestor. aprovado_gestor: liberado pelo gestor,
                                                                aguardando a validação final do RH/folha.
                                                                confirmado_rh: os dois \"sins\" reunidos --- só a
                                                                partir daqui o gozo entra de fato na apuração de
                                                                folha (Mov_Rh_Folha_Apuracao Tipo_Folha=ferias,
                                                                seção 5). rejeitado_gestor/rejeitado_rh: negado em
                                                                qualquer uma das duas etapas, com Motivo_Rejeicao
                                                                preenchido (abaixo). cancelado: desistência do
                                                                colaborador antes da confirmação do RH --- depois de
                                                                confirmado_rh, uma mudança já é um novo registro de
                                                                ajuste, mesmo princípio de \"evento, não edição\" já
                                                                usado no restante do módulo. Só um lançamento direto
                                                                do RH (sem passar por solicitado) é o caso de férias
                                                                coletivas ou migração --- ver Origem_Tipo, acima ---
                                                                nesse caso Status nasce diretamente confirmado_rh.

  **ID_Gestor_Aprovacao**            *referência                Adicionado nesta revisão (10): o gestor que decidiu
                                     (Cad_Vinculo_Emprego,      a etapa 1 --- normalmente
                                     opcional)*                 Cad_Vinculo_Emprego.ID_Gestor (seção 3) do
                                                                colaborador solicitante no momento da solicitação,
                                                                preenchido aqui para preservar quem de fato decidiu,
                                                                mesmo que a hierarquia mude depois. Vazio enquanto
                                                                Status=solicitado.

  **Data_Aprovacao_Gestor**          *data, opcional*           Preenchida junto de ID_Gestor_Aprovacao.

  **ID_Participante_Validacao_Rh**   *referência                Adicionado nesta revisão (10): quem da equipe de
                                     (Cad_Participante,         folha/RH decidiu a etapa 2. Vazio enquanto Status
                                     opcional)*                 não chega a aprovado_gestor.

  **Data_Validacao_Rh**              *data, opcional*           Preenchida junto de ID_Participante_Validacao_Rh.

  **Motivo_Rejeicao**                *texto, opcional*          Preenchido só quando Status=rejeitado_gestor ou
                                                                rejeitado_rh.

  **Urgente**                        *booleano*                 Adicionado nesta revisão (10), pedido por Alberto
                                                                (\"no caso de urgencia, por alguma necessidade
                                                                pessoal o colaborador poder sinalizar esta
                                                                urgencia\"): sinaliza um pedido feito abaixo do
                                                                prazo mínimo de antecedência
                                                                (Cad_Rh_Politica_Ferias.Dias_Minimos_Antecedencia,
                                                                abaixo) --- a política mínima não bloqueia a
                                                                solicitação, é só um alerta visual para o gestor/RH
                                                                priorizarem a análise; quem decide se o prazo curto
                                                                é aceitável continua sendo o gestor/RH na aprovação,
                                                                mesmo princípio \"sugere, nunca aplica
                                                                automaticamente\" já usado em todo o dicionário.

  **Justificativa_Urgencia**         *texto*                    Obrigatório quando Urgente=verdadeiro --- instrução
                                                                explícita de Alberto (\"lembre que na urgencia tem
                                                                que ter uma justificativa\"): validação de
                                                                aplicação, não uma restrição estrutural do campo,
                                                                mesmo padrão condicional já usado para
                                                                Cad_Vinculo_Emprego.Data_Fim_Prevista_Contrato
                                                                (obrigatório só quando
                                                                Tipo_Contrato_Prazo=determinado, seção 3). Vazio
                                                                quando Urgente=falso.
  ---------------------------------- -------------------------- ----------------------------------------------------

Cad_Rh_Politica_Ferias

Adicionado nesta revisão (10), pedido por Alberto (\"tera que ter um
parametro de até quantos dias antes da férias é póssivel fazer o
pedido\"): o prazo mínimo de antecedência para solicitar férias, por
empresa.

*Vigência: sim --- mesmo padrão de qualquer parâmetro deste dicionário:
uma mudança de prazo mínimo nasce como nova versão, nunca sobrescrita,
preservando o critério usado nas solicitações já decididas.*

  ------------------------------- ----------------- ----------------------------------------
  **Campo**                       **Tipo lógico**   **Descrição / regra**

  **ID_Politica**                 *identificador*   ---

  **ID_Empresa**                  *referência       ---
                                  (Cad_Empresa)*    

  **Dias_Minimos_Antecedencia**   *número*          Usado pela aplicação para marcar
                                                    automaticamente uma nova solicitação
                                                    como abaixo do prazo mínimo --- não
                                                    bloqueia a criação, só orienta o
                                                    colaborador a marcar Urgente (acima) e
                                                    justificar.

  **Vigencia_Inicio**             *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                *data*            Último dia em que esta versão vale
                                                    (inclusive). Sempre preenchida:
                                                    31/12/9999 quando o fim é indefinido
                                                    (versão vigente) --- convenção da Fase
                                                    0, seção 2.

  **Motivo_Vigencia**             *texto, opcional* Por que esta versão foi criada.
  ------------------------------- ----------------- ----------------------------------------

*Saldo de férias e períodos em aberto no portal do colaborador:
comportamento de aplicação, pedido por Alberto (\"tem que apresentar os
períodos que estão em aberto para poder pedir as férias, ou saldo de
dias de férias\") --- nunca armazenado, sempre uma consulta cruzando
Mov_Rh_Ferias_Periodo (acima) com os Mov_Rh_Ferias_Gozo já confirmados
(Status=confirmado_rh) daquele período, mesmo princípio de nunca guardar
o que pode ser derivado já usado em todo o dicionário. Um período
aquisitivo com saldo é o que fica disponível para nova solicitação na
tela de férias do portal (seção 18).*

9\. Migração --- Bases Acumuladas e Históricos

Alberto foi explícito de que a migração é mais ampla do que um saldo de
abertura consolidado: \"tenho que trazer bases acumuladas para os
cálculos futuros, e tem históricos que têm que serem trazidos, exemplo
de férias entre outros.\" Ou seja, dois tipos de necessidade, ambos
cobertos: (1) BASES ACUMULADAS --- valores consolidados na data de
corte, necessários para continuar corretamente um cálculo que depende do
acumulado do ano (ex.: base de IRRF acumulada, para não recalcular do
zero um imposto progressivo); e (2) HISTÓRICO REAL --- eventos que de
fato aconteceram no sistema anterior e precisam existir aqui para
consulta e para as regras de negócio que dependem deles (ex.: um período
de férias já gozado no sistema anterior, para não conceder de novo).

Mov_Rh_Base_Acumulada_Migrada

Um saldo acumulado, trazido do sistema anterior na virada, necessário
para dar continuidade a um cálculo que depende do que já aconteceu no
ano/período --- não recalculado a partir de eventos individuais, porque
esses eventos, por definição, não existem neste sistema.

*Vigência: não --- é o registro de um evento de migração, ele mesmo; uma
correção do valor migrado é um novo registro de ajuste, nunca a edição
do original, preservando a trilha de que o saldo inicial veio de fora.*

  ---------------------------- ------------------------ ----------------------------------------
  **Campo**                    **Tipo lógico**          **Descrição / regra**

  **ID_Base**                  *identificador*          ---

  **ID_Vinculo**               *referência              Normalmente um vínculo também migrado
                               (Cad_Vinculo_Emprego)*   (ex.: recriado aqui só para preservar a
                                                        matrícula anterior) --- ver nota abaixo.

  **Tipo_Base**                *enumeração {inss, fgts, Extensível --- um novo tipo de base
                               irrf, banco_horas,       acumulada não exige mudança de
                               avos_decimo_terceiro,    estrutura.
                               ferias_dias_saldo,       
                               outro}*                  

  **Competencia_Referencia**   *competência, opcional*  Substitui Competencia_Referencia_Ano/Mes
                                                        (revisão 15).

  **Ano_Referencia**           *número, opcional*       Só quando o tipo de base não é mensal
                                                        (ex.: saldo de banco de horas na data de
                                                        corte). Exatamente um dos dois é
                                                        preenchido.

  **Valor**                    *número*                 ---

  **Data_Migracao**            *data*                   Quando este registro foi trazido para o
                                                        sistema novo --- distinta da competência
                                                        a que o valor se refere.

  **Observacao**               *texto, opcional*        ---
  ---------------------------- ------------------------ ----------------------------------------

*Histórico real migrado (o segundo tipo de necessidade de Alberto): não
ganha uma entidade dedicada --- reaproveita as mesmas entidades já
especificadas neste documento, com Origem_Tipo=migracao já previsto onde
fazia sentido: Mov_Rh_Ferias_Gozo (exemplo explícito de Alberto --- um
gozo de férias do sistema anterior) e Mov_Rh_Folha_Apuracao (uma folha
fechada de um mês anterior à virada, trazida para consulta). O mesmo
princípio se estende, por analogia, a qualquer outro histórico que a
Mlegate precise trazer no futuro (ex.: histórico de afastamento, seção
12) --- o padrão já é genérico o bastante (Origem_Tipo/ID_Origem, ou um
Origem_Tipo próprio de duas pontas como já usado em Mov_Rh_Ferias_Gozo)
para acomodar sem mudança estrutural.*

*Base histórica de variáveis para a média de férias/13º: Alberto
perguntou especificamente onde fica, na migração, o histórico de horas
extras e comissões que compõem a base de previsão (média) de férias e
13º. É o mesmo caminho de Mov_Rh_Folha_Apuracao acima, agora
explicitado: uma folha MENSAL histórica migrada (Origem_Tipo=migracao)
traz consigo seus Mov_Rh_Folha_Item, itemizados por Cad_Rh_Verba ---
incluindo as verbas variáveis marcadas com
Compoe_Media_Ferias=verdadeiro e/ou
Compoe_Media_Decimo_Terceiro=verdadeiro, conforme o cálculo em curso
(seção 5). A média em si nunca é pré-calculada nem armazenada: é sempre
uma consulta somando/tirando a média dessas verbas ao longo do período
aquisitivo ou dos meses que a legislação define, cruzando histórico
migrado e histórico calculado por este sistema da mesma forma, sem
distinção de origem no momento do cálculo.*

*Vínculo migrado: quando o histórico trazido pertence a uma matrícula
que já estava desligada antes da virada (ex.: férias gozadas por um
colaborador que já não trabalha mais na Mlegate), o Cad_Vinculo_Emprego
correspondente também precisa existir aqui --- recriado com
Data_Admissao/Data_Desligamento reais do sistema anterior --- para que
ID_Vinculo do histórico migrado tenha para onde apontar; não é preciso
recriar toda a ficha do colaborador (seção 12) para esse caso, só o
vínculo e o histórico específico sendo trazido.*

10\. eSocial --- Envio de Eventos

Confirmado por Alberto: uma tabela GENÉRICA, que atenda todas as
camadas/tipos de evento do eSocial, com inclusão futura de novos tipos
sem mudança estrutural --- não uma tabela por tipo de evento (o que
exigiria uma nova entidade a cada novo evento que a Receita/eSocial
publicasse). Mesmo princípio de \"cadastro único, papéis por contexto\"
já usado no resto do dicionário (GED, Ativo Imobilizado, Condição do
Estoque): um único Mov_Esocial_Evento, com o tipo específico e o
registro de origem resolvidos por referência genérica.

Mov_Esocial_Evento

Um evento a transmitir (ou já transmitido) ao eSocial --- cobre as
séries de tabela (S-1000), de eventos não periódicos (S-2200 admissão,
S-2206 alteração contratual, S-2299 desligamento, S-2230 afastamento,
S-2210 acidente de trabalho/CAT, S-2220 exame médico/PCMSO, entre
outras), periódicos (S-1200 remuneração, S-1210 pagamentos) e de
exclusão (S-3000) --- sem uma tabela própria para cada um.

*Vigência: não --- evento; uma retificação nasce como um NOVO
Mov_Esocial_Evento vinculado ao original (ID_Evento_Retificado), nunca a
edição do evento já enviado --- mesmo princípio de fidelidade ao que foi
de fato transmitido.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Evento** | *identificador* | --- |
| **ID_Tipo_Evento** | *referência (Cad_Classe_Sistema, domínio = tipo_evento_esocial)* | O código/nome do evento (ex.: S-2200, S-1200, S-2299) --- domínio aberto: a Receita Federal publica um novo evento e a Mlegate só cadastra um novo valor aqui, nunca uma nova tabela. |
| **Origem_Tipo** | *enumeração {cad_vinculo_emprego, mov_rh_folha_apuracao, mov_rh_ficha_evento, condicao_risco, mov_rh_processo_trabalhista, mov_rh_processo_trabalhista_apuracao, cad_rh_empregador_esocial, outro}* | Referência genérica de qual registro deste módulo originou o evento --- mesmo padrão Origem_Tipo/ID_Origem já usado em todo o dicionário (Mov_Aprovacao_Instancia, Mov_Lote_Lancamento, Mov_Estoque_Condicao, entre outros). condicao_risco: adicionado para o evento S-2240 (condições ambientais do trabalho), originado da combinação de condições de cargo/área vigentes para o vínculo (seção 13), não de um evento pontual como os demais. Revisão 16: mov_rh_processo_trabalhista (S-2500) e mov_rh_processo_trabalhista_apuracao (S-2501) acrescentados, para que o envio dos eventos do processo trabalhista fique rastreado como os demais. cad_rh_empregador_esocial: adicionado na revisão 17 (Bloco 4) para o evento S-1000. |
| **ID_Origem** | *identificador do registro de origem, opcional* | Conforme Origem_Tipo: ID_Vinculo (admissão/desligamento/alteração contratual), ID_Apuracao (remuneração/pagamentos, inclusive pagamento_autonomo), ID_Evento_Ficha (afastamento/exame/acidente --- seção 12) ou ID_Vinculo também para condicao_risco (a combinação de condições vigentes é resolvida por consulta a partir do vínculo, seção 13, não por um único registro de origem); vazio para um evento sem origem estruturada neste módulo (Origem_Tipo=outro). |
| **Xml_Evento** | *texto, opcional* | O XML efetivamente montado para envio, quando já gerado --- guardado como registro do que foi de fato transmitido, fidelidade ao valor real, mesmo critério já usado em Mov_Remessa_Bancaria_Item (Tesouraria). |
| **Status** | *enumeração {pendente, enviado, processando, aceito, rejeitado, retificado}* | --- |
| **Evento_Importado** | *booleano* | Revisão 13 (D-N219): Verdadeiro quando o evento foi enviado ao eSocial antes do ERP e entrou por importação: sem XML e sem data de envio do ERP (D-N218). Revisão 15 (D-N234, Q75-4 e Q75-5): divergência entre a unidade de pagamento ou as horas importadas e o eSocial gera aviso ao RH, e o S-2206 só sai com a confirmação dele; o vínculo importado que nunca foi enviado vai por envio direto, sem a confirmação do lote pelo RH (Revisão 19, D-N301): o retorno do eSocial é tratado pelo catálogo Cad_Esocial_Ocorrencia (ocorrência "já existe": o evento passa a aceito como importado e o RH é avisado; os demais erros são corrigidos e reenviados). Antes do primeiro S-2200 de vínculo importado, o ERP consulta o eSocial pelo trabalhador, se o serviço de consulta permitir; achando vínculo com outra matrícula, não envia e manda o caso ao RH com as duas matrículas (D-N303). A conferir no manual do eSocial: o código de "registro já existe", a existência do serviço de consulta e o caminho de correção da matrícula. |
| **Numero_Recibo** | *código (até 40), opcional* | Preenchido quando Status=aceito --- o protocolo devolvido pelo eSocial. Revisão 13 (D-N218): fica vazio quando o evento é importado sem recibo (o recibo do S-2200 original é opcional na importação; sem ele o ERP não retifica o original, mas o S-2206 e os eventos periódicos funcionam, porque se identificam por CPF e matrícula). |
| **Data_Hora_Envio** | *data/hora, opcional* | --- |
| **ID_Evento_Retificado** | *referência (Mov_Esocial_Evento, opcional)* | Autorreferência: preenchida quando este evento é uma RETIFICAÇÃO de um evento anterior --- aponta para o evento original, nunca o sobrescrevendo. |
| **Versao_Leiaute** | *código (10)* | Versão do leiaute do eSocial usada para montar o evento (ex.: S-1.3). |
| **Resultado_Validacao_Esquema** | *enumeração {nao_validado, valido, invalido}* | Evento inválido não passa para o status enviado. |
| **Mensagem_Validacao_Esquema** | *texto, opcional* | Erros do esquema, campo a campo, para o usuário corrigir. |
| **Data_Hora_Validacao** | *data/hora, opcional* | Adicionado na revisão 16 (Bloco 3). |
| **ID_Certificado** | *referência (Cad_Certificado_Digital, opcional)* | Certificado que assinou o envio (Fase 8 --- Jurídico, seção 12). |

*Revisão 13 --- campos novos: Evento_Importado; campos alterados: Numero_Recibo.*

*Revisão 15 --- campos alterados: Evento_Importado.*

*Revisão 19 --- campos alterados: Evento_Importado.*

Envio único do S-2200 (revisão 13, documento 75, D-N217 e D-N218). A matrícula é a chave do contrato e o eSocial recusa o evento se já existir, para o mesmo empregador, trabalhador com a mesma matrícula. O ERP aplica a mesma regra: para cada empregador e matrícula, no máximo um S-2200 original (sem ID_Evento_Retificado) com status pendente, enviado, em processamento ou aceito; o ERP rejeita a geração de um segundo, sem esperar o eSocial recusar. O rejeitado não conta como enviado: fica no histórico e pode ser corrigido e reenviado como novo S-2200 original. Depois do aceite, a mudança do contrato vai por S-2206, e a correção do próprio S-2200 por retificação ou, no caso da categoria errada, por exclusão e novo envio; nunca por novo S-2200 com a mesma matrícula. Vínculo importado já admitido no eSocial: o importador grava uma linha de tipo S-2200, status aceito e Evento_Importado verdadeiro, sem XML e sem data de envio do ERP; o indicador de admissão já enviada é obrigatório e o recibo é opcional. Vínculo importado que nunca foi enviado: o evento fica pendente e o ERP gera o S-2200 uma única vez, com o cadIni pela data de início do empregador. Se a unidade de pagamento ou as horas importadas divergirem do que o eSocial já tem, o ERP avisa o RH, e o S-2206 só sai com a confirmação dele (Q75-4 e Q75-5).

*Atributo de envio imediato x aguarda fechamento da folha, já previsto
no Documento Analítico: não vive em Mov_Esocial_Evento (que é só o envio
em si), e sim em Cad_Rh_Tipo_Evento_Ficha (seção 12) --- o tipo de
evento da Ficha do Colaborador que originou o evento é que decide se o
envio deve ser imediato (ex.: admissão, acidente de trabalho) ou pode
esperar o fechamento da folha (ex.: um evento periódico de
remuneração).*

Estabelecimento e lotação tributária (revisão 16)

O S-1005 descreve cada estabelecimento para a folha (CNAE preponderante,
RAT, FAP, contratação de aprendiz e de pessoa com deficiência, ponto
eletrônico) e o S-1020 descreve cada lotação tributária (onde o
trabalhador está para fins de contribuição: FPAS, terceiros, tipo). O
trabalhador aponta para uma lotação, e ela pode mudar sem mudar o
vínculo.

Revisão 17 (Bloco 4): o S-1000 informa os dados do empregador ao
eSocial, um registro por empresa e por vigência, com iniValid e fimValid
transformados no trio de vigência. Ele não existia no dicionário. As
regras de "só vale se" do leiaute entram na descrição de cada campo e
são validadas pelo motor de regras antes do envio, junto com a validação
de esquema. O indicador indOptRegEletron deixa de ser enviado a partir
de 02/2026; o campo fica só para o histórico. O indicador indSiafi está
no leiaute S-1.3 consolidado até a NT 07/2026, mas ainda não no pacote
XSD de 26/10/2026; o campo existe e só é enviado quando o esquema
vigente o aceitar. O ente federativo responsável é
Cad_Ente_Federativo_Responsavel, da Fase 0 (revisão 46), comum ao S-1000
e ao R-1000 da Reinf.

Cad_Rh_Empregador_Esocial

Nova na revisão 17 (Bloco 4). O S-1000: dados do empregador no eSocial, um por empresa e por
vigência. A inscrição enviada vem do participante da matriz e tem 8
posições (raiz do CNPJ), ou 14 para a administração direta federal
(101-5, 104-0, 107-4, 116-3 e 134-1).

*Vigência: sim --- a classificação tributária, as opções e o EFR mudam
por decisão da empresa ou da lei; o histórico serve à retificação de
períodos passados.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Empregador_Esocial** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa) --- identidade* | --- |
| **Data_Inicio_Eventos_Nao_Periodicos** | *data, opcional* | Revisão 13 (D-N219): A data a partir da qual o empregador deve enviar os eventos não periódicos ao eSocial. Define o cadIni do S-2200: vínculo cujo ingresso é anterior a essa data é cadastramento inicial; igual ou posterior é admissão (D-N223). Obrigatória para quem envia S-2200; quem informa é o contador, por empregador, na implantação (Q75-2). |
| **ID_Classificacao_Tributaria** | *referência (Cad_Classe_Sistema, domínio = classificacao_tributaria_contribuinte)* | classTrib, Tabela 08. Os códigos 21 e 22 exigem inscrição por CPF (não modelado). Para administração pública só valem 80, 85 e 99. |
| **Indicador_Cooperativa** | *enumeração {nao_e, de_trabalho, de_producao, outras}* | indCoop, valores 0 a 3. Só pode ser diferente de 0 se a natureza jurídica for 214-3. |
| **Indicador_Construtora** | *booleano* | indConstr, obrigatório para pessoa jurídica. |
| **Indicador_Desoneracao_Folha** | *enumeração {nao_aplicavel, empresa_enquadrada, municipio_enquadrado}* | indDesFolha, valores 0 a 2. O valor 1 exige classTrib 02, 03 ou 99. O valor 2 só vale para as naturezas 103-1, 106-6, 124-4 e 133-3. |
| **Opcao_Contribuicao_Produtor_Rural** | *enumeração {comercializacao, folha}, opcional* | indOpcCP, só para classTrib 07 ou 21. Vazio significa comercialização. |
| **Micro_Pequena_Empresa** | *booleano* | indPorte. Não vale para classTrib 21 e 22. |
| **Opcao_Registro_Eletronico** | *booleano, opcional* | indOptRegEletron. Não é mais enviado a partir de 02/2026; guardado só para o histórico. |
| **ID_Ente_Federativo_Responsavel** | *referência (Cad_Ente_Federativo_Responsavel, opcional)* | cnpjEFR. Obrigatório e exclusivo quando a natureza jurídica é do grupo 1 (administração pública) da tabela CONCLA (campo Grupo de Cad_Natureza_Juridica). |
| **Forma_Envio_Orgao_Publico** | *enumeração {unificada, nao_unificada}, opcional* | Vem do MOS, item 7.3, e não existe no XSD. Na unificada, o S-1000 de um órgão traz outros CNPJs no S-1005; na não unificada, cada raiz envia o seu S-1000 e o seu fechamento. |
| **Data_Transformacao_Lei_11096** | *data, opcional* | dtTrans11096. Tem de ser posterior a 21/11/2005 e não pode ser futura; não vale para classTrib 21 e 22. |
| **Tributa_Folha_Pis_Pasep** | *booleano* | indTribFolhaPisPasep. |
| **Pertence_Irrf** | *booleano, opcional* | indPertIRRF. Só para as naturezas 126-0, 127-9, 129-5 e 130-9. |
| **Usa_Siafi** | *booleano, opcional* | indSiafi. Só para órgãos federais com as naturezas 101-5, 104-0, 107-4, 110-4, 113-9, 116-3, 125-2, 128-7, 131-7, 134-1, 201-1 e 203-8. |
| **Acordo_Isencao_Multa** | *booleano, opcional* | infoOrgInternacional/indAcordoIsenMulta, só para organismos internacionais. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente). |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 13 --- campos novos: Data_Inicio_Eventos_Nao_Periodicos.*

Cad_Rh_Empregador_Esocial_Isencao

Nova na revisão 17 (Bloco 4). Os dadosIsencao do S-1000 (certificado de entidade beneficente,
como o CEBAS, e similares), um por empresa e por vigência, opcional. A
vigência precisa estar contida na do S-1000.

*Vigência: sim --- o certificado é renovado periodicamente; cada
renovação é uma versão.*

  --------------------------------- ----------------- ----------------------------------------
  **Campo**                         **Tipo lógico**   **Descrição / regra**

  **ID_Isencao**                    *identificador*   ---

  **ID_Empresa**                    *referência       ---
                                    (Cad_Empresa) --- 
                                    identidade*       

  **Ministerio_Ou_Lei**             *texto (70)*      ideMinLei.

  **Numero_Certificado**            *texto (40)*      nrCertif.

  **Data_Emissao_Certificado**      *data*            dtEmisCertif.

  **Data_Vencimento_Certificado**   *data*            dtVencCertif. Gera alerta de vencimento
                                                      pelo mecanismo de notificações.

  **Numero_Protocolo_Renovacao**    *texto (40),      nrProtRenov.
                                    opcional*         

  **Data_Protocolo_Renovacao**      *data, opcional*  dtProtRenov.

  **Data_Dou**                      *data, opcional*  dtDou.

  **Pagina_Dou**                    *número,          pagDou, de 1 a 5 dígitos.
                                    opcional*         

  **Vigencia_Inicio**               *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                  *data*            Último dia em que esta versão vale
                                                      (inclusive). Sempre preenchida:
                                                      31/12/9999 quando o fim é indefinido
                                                      (versão vigente).

  **Motivo_Vigencia**               *texto, opcional* Por que esta versão foi criada.
  --------------------------------- ----------------- ----------------------------------------


Cad_Rh_Estabelecimento_Esocial

Nova na revisão 16 (Bloco 3 da validação geral). Dados do
estabelecimento que o S-1005 exige, um por filial e por vigência. A
filial é um participante (D-2), então a inscrição (CNPJ, CAEPF ou CNO)
vem do participante.
 Revisão 17 (Bloco 4): um estabelecimento com raiz de CNPJ diferente da
do S-1000 tem de pertencer ao mesmo EFR, e essa raiz diferente só pode
enviar o S-1000 e o evento sem movimento; fundos especiais sem
personalidade jurídica que sejam unidade pagadora entram aqui. A
classificação tributária 21 e 22 (pessoa física como empregadora) não é
modelada, porque Cad_Empresa é pessoa jurídica.

*Vigência: sim --- RAT, FAP e CNAE mudam por ano ou por decisão; o
histórico serve à DCTFWeb de períodos passados.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Estabelecimento_Esocial** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | --- |
| **Tipo_Inscricao_Esocial** | *enumeração {cnpj, caepf, cno}* | tpInsc: 1 CNPJ, 3 CAEPF, 4 CNO. O número sai de Cad_Participante_Inscricao ou do documento principal do participante. |
| **ID_Cnae_Preponderante** | *referência (Cad_CNAE)* | cnaePrep, 7 posições. |
| **Aliquota_Rat** | *enumeração {1, 2, 3}* | Alíquota do RAT do estabelecimento, em percentual. |
| **Fap** | *número* | Fator Acidentário de Prevenção, de 0,5000 a 2,0000. |
| **ID_Processo_Suspensao_Rat** | *referência (Mov_Processo_Suspensao, opcional)* | Processo que suspende a exigibilidade do RAT (procAdmJudRat). Ver Fase 8 --- Jurídico, seção 5. |
| **ID_Processo_Suspensao_Fap** | *referência (Mov_Processo_Suspensao, opcional)* | Processo que suspende a exigibilidade do FAP (procAdmJudFap). |
| **ID_Regime_Ponto** | *referência (Cad_Classe_Sistema, domínio = regime_ponto_esocial)* | regPt: não utiliza, manual, mecânico, eletrônico ou outros. Casa com Mov_Rh_Ponto. |
| **Obrigatoriedade_Aprendiz** | *enumeração {dispensado, obrigado, dispensado_por_decisao}* | contApr. Quando por decisão, aponta o processo em ID_Processo_Suspensao_Aprendiz. |
| **ID_Processo_Suspensao_Aprendiz** | *referência (Mov_Processo_Suspensao, opcional)* | --- |
| **Obrigatoriedade_Pcd** | *enumeração {dispensado, obrigado, dispensado_por_decisao}* | contPCD, cota do art. 93 da Lei 8.213/1991. O campo infoCota do S-2200 só vale para admissão anterior a 26/10/2026 (NT 07/2026) e é derivado, sem campo próprio, do cadastro de deficiência (Cad_Participante_Deficiencia) e do Reabilitado_Inss de Cad_Participante_Dados_Pessoa_Fisica: verdadeiro quando há deficiência cadastrada ou reabilitação pelo INSS, sem confirmação do RH (revisão 17, D-N300); depois dessa data não se informa. O ERP não controla a cota, só identifica a deficiência e qual é. |
| **ID_Processo_Suspensao_Pcd** | *referência (Mov_Processo_Suspensao, opcional)* | --- |
| **Substituicao_Patronal_Obra** | *booleano, opcional* | Só para inscrição por CNO. |
| **ID_Cno_Obra** | *referência (Cad_Cno_Obra, opcional)* | Novo na revisão 3 (documento 37). Obra do CNO quando Tipo_Inscricao_Esocial = cno; o número vem de Cad_Cno_Obra. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 3 --- campos novos (documento 37): ID_Cno_Obra.*

*Revisão 13 --- campos alterados: Obrigatoriedade_Pcd.*

*Revisão 17 --- campos alterados: Obrigatoriedade_Pcd.*

Cad_Rh_Lotacao_Tributaria

Nova na revisão 16 (Bloco 3 da validação geral). Lotação tributária do
S-1020, da empresa. Uma lotação pode reunir vários estabelecimentos ou
uma obra.

*Vigência: sim --- FPAS e terceiros mudam por enquadramento.*

  ---------------------------------- -------------------------- ----------------------------------------
  **Campo**                          **Tipo lógico**            **Descrição / regra**

  **ID_Lotacao**                     *identificador*            ---

  **ID_Lotacao_Versao**              *identificador da versão*  Chave primária da versão (tabela física
                                                                Cad_Rh_Lotacao_Tributaria_Versao).
                                                                ID_Lotacao é a identidade, única e
                                                                referenciada pelas outras tabelas; cada
                                                                versão guarda a sua janela de vigência
                                                                --- Fase 0, seção 2.

  **ID_Empresa**                     *referência (Cad_Empresa)  ---
                                     --- identidade*            

  **Codigo_Lotacao**                 *código (30) ---           codLotacao, escolhido pela empresa.
                                     identidade*                

  **ID_Tipo_Lotacao**                *referência                Tabela 10 do eSocial.
                                     (Cad_Classe_Sistema,       
                                     domínio =                  
                                     tipo_lotacao_esocial)*     

  **ID_Filial**                      *referência (Cad_Filial,   Estabelecimento da lotação, quando a
                                     opcional)*                 lotação é o próprio estabelecimento.

  **Tipo_Inscricao_Lotacao**         *enumeração {cnpj, cpf,    Quando a lotação tem inscrição diferente
                                     caepf, cno}, opcional*     do estabelecimento (obra, tomador).

  **Numero_Inscricao_Lotacao**       *código (14), opcional*    CNPJ alfanumérico quando for CNPJ.

  **ID_Fpas**                        *referência                Código do FPAS (3 dígitos).
                                     (Cad_Classe_Sistema,       
                                     domínio = fpas_esocial)*   

  **Tipo_Inscricao_Contratante**     *enumeração {cnpj, cpf},   infoEmprParcial: empresa contratante
                                     opcional*                  quando a lotação é de empreitada
                                                                parcial.

  **Numero_Inscricao_Contratante**   *código (14), opcional*    ---

  **ID_Processo_Suspensao**          *referência                infoProcJud: decisão que altera a
                                     (Mov_Processo_Suspensao,   alíquota de terceiros ou de
                                     opcional)*                 contribuição.

  **Vigencia_Inicio**                *data*                     Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                   *data*                     Último dia em que esta versão vale
                                                                (inclusive). Sempre preenchida:
                                                                31/12/9999 quando o fim é indefinido
                                                                (versão vigente) --- convenção da Fase
                                                                0, seção 2.

  **Motivo_Vigencia**                *texto, opcional*          Por que esta versão foi criada.
  ---------------------------------- -------------------------- ----------------------------------------

Cad_Rh_Lotacao_Terceiros

Nova na revisão 16 (Bloco 3 da validação geral). Os códigos de terceiros
(Sistema S, salário-educação, INCRA) de cada lotação.

*Vigência: sim.*

  --------------------------- ------------------------------ ----------------------------------------
  **Campo**                   **Tipo lógico**                **Descrição / regra**

  **ID_Lotacao_Terceiros**    *identificador*                ---

  **ID_Lotacao**              *referência                    ---
                              (Cad_Rh_Lotacao_Tributaria)*   

  **ID_Codigo_Terceiros**     *referência                    codTercs, 4 posições.
                              (Cad_Classe_Sistema, domínio = 
                              codigo_terceiros_esocial)*     

  **Suspenso**                *booleano*                     Verdadeiro quando a contribuição desse
                                                             terceiro está suspensa por decisão.

  **ID_Processo_Suspensao**   *referência                    Obrigatório quando Suspenso.
                              (Mov_Processo_Suspensao,       
                              opcional)*                     

  **Vigencia_Inicio**         *data*                         Primeiro dia em que esta versão vale.

  **Vigencia_Fim**            *data*                         Último dia em que esta versão vale
                                                             (inclusive). Sempre preenchida:
                                                             31/12/9999 quando o fim é indefinido
                                                             (versão vigente) --- convenção da Fase
                                                             0, seção 2.

  **Motivo_Vigencia**         *texto, opcional*              Por que esta versão foi criada.
  --------------------------- ------------------------------ ----------------------------------------

Cad_Vinculo_Lotacao

Nova na revisão 16 (Bloco 3 da validação geral). Histórico da lotação
tributária de cada vínculo. A lotação entra na admissão (S-2200) e muda
por alteração contratual (S-2206). Substitui a ausência de lotação em
Cad_Vinculo_Emprego.

*Vigência: sim --- janela sem sobreposição por vínculo.*

  ------------------------ ------------------------------ ----------------------------------------
  **Campo**                **Tipo lógico**                **Descrição / regra**

  **ID_Vinculo_Lotacao**   *identificador*                ---

  **ID_Vinculo**           *referência                    ---
                           (Cad_Vinculo_Emprego)*         

  **ID_Lotacao**           *referência                    ---
                           (Cad_Rh_Lotacao_Tributaria)*   

  **ID_Municipio_Trabalho** *referência (Cad_Municipio,    Adicionado na revisão 21 (P-42). O
                           opcional)*                     município onde o vínculo presta serviço
                                                          no período, que decide quais feriados
                                                          municipais e estaduais contam para o
                                                          DSR. Vazio: vale o município do
                                                          estabelecimento da lotação
                                                          (Cad_Rh_Lotacao_Tributaria.ID_Filial).
                                                          Preencher só para obra ou tomador sem
                                                          estabelecimento próprio; o trabalho
                                                          externo, o teletrabalho e o híbrido
                                                          seguem o município em que o vínculo está
                                                          registrado na empresa.

  **Vigencia_Inicio**      *data*                         Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*                         Último dia em que esta versão vale
                                                          (inclusive). Sempre preenchida:
                                                          31/12/9999 quando o fim é indefinido
                                                          (versão vigente) --- convenção da Fase
                                                          0, seção 2.

  **Motivo_Vigencia**      *texto, opcional*              Por que esta versão foi criada.
  ------------------------ ------------------------------ ----------------------------------------

Cad_Vinculo_Horario_Contratual

Nova na revisão 19 (ajustes da Folha, NT 07/2026). O horário contratual de
um vínculo, por vigência, como o S-2200 e o S-2206 o informam: horas
semanais, tipo de jornada, tempo parcial, horário noturno e descrição da
jornada. O S-2200 abre a primeira linha e cada S-2206 abre uma nova, pelo
mesmo padrão de Cad_Vinculo_Lotacao.

*Vigência: sim --- janela sem sobreposição por vínculo.*

  ------------------------ -------------------------------------- ----------------------------------------------
  **Campo**                **Tipo lógico**                        **Descrição / regra**

  **ID_Vinculo_Horario**   *identificador*                        ---

  **ID_Vinculo**           *referência (Cad_Vinculo_Emprego)*     ---

  **Horas_Semanais**       *número, opcional*                     qtdHrsSem: quantidade média de horas da
                                                                  jornada semanal (até 4 dígitos, 2 decimais).
                                                                  Obrigatório quando a categoria é diferente de
                                                                  111 (intermitente); se informado, maior que
                                                                  zero. Pode ser sugerido pela soma da escala
                                                                  (Cad_Rh_Escala e Cad_Rh_Turno), mas o valor
                                                                  contratual é o que vale; se a soma da escala
                                                                  diferir, o sistema avisa, mas não impede.

  **Tipo_Jornada**         *enumeração {doze_por_trinta_e_seis,   tpJornada, valores 2 a 7 e 9. Obrigatório.
                           folga_variavel, folga_fixa_domingo,
                           folga_fixa_exceto_domingo,
                           folga_fixa_outro_dia_com_domingo_periodico,
                           turno_ininterrupto_revezamento,
                           demais}*

  **Tempo_Parcial**        *enumeração {nao_e_tempo_parcial,      tmpParc, valores 0 a 3, como em
                           ate_25_horas, ate_30_horas,            Mov_Rh_Processo_Trabalhista_Contrato. O código
                           ate_26_horas}*                         1 só vale na categoria 104; os códigos 2 e 3
                                                                  não valem na 104.

  **Horario_Noturno**      *booleano, opcional*                   horNoturno: a jornada semanal tem horário
                                                                  noturno, no todo ou em parte. Obrigatório
                                                                  quando a categoria é diferente de 111.

  **Descricao_Jornada**    *texto (999)*                          dscJorn: os dias da semana e os horários
                                                                  contratuais (entrada, saída e intervalos).
                                                                  Obrigatório. Pode ser gerado a partir da
                                                                  escala.

  **Vigencia_Inicio**      *data*                                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*                                 Último dia em que esta versão vale
                                                                  (inclusive). Sempre preenchida: 31/12/9999
                                                                  quando o fim é indefinido (versão vigente) ---
                                                                  convenção da Fase 0, seção 2.

  **Motivo_Vigencia**      *texto, opcional*                      Por que esta versão foi criada.
  ------------------------ -------------------------------------- ----------------------------------------------

*Regras datadas, validadas pelo motor de regras antes do envio (a data de
cada uma é parâmetro, e não código). A data de referência é a maior entre
a admissão e a transferência (S-2200), ou a data da alteração (S-2206),
que é o Vigencia_Inicio da linha. A partir de 23/11/2026, se
Tempo_Parcial = ate_25_horas, Horas_Semanais não passa de 25; se
ate_30_horas, não passa de 30; se ate_26_horas, não passa de 26. A
partir de 23/11/2026, se Tipo_Jornada = doze_por_trinta_e_seis (12 x 36),
Tempo_Parcial tem de ser nao_e_tempo_parcial. Antes de 23/11/2026, valem
só as regras que já existiam (o código 1 só na categoria 104, os códigos
2 e 3 nunca na 104). O Tempo_Parcial do S-2500
(Mov_Rh_Processo_Trabalhista_Contrato) não muda: o S-2500 não leva horas
semanais. As regras de horas acima não se aplicam à categoria
intermitente (111), cujas regras do S-2200 não foram conferidas.*

Processo trabalhista --- S-2500 e S-2501 (revisão 16)

O S-2500 informa ao governo a decisão ou o acordo de uma reclamatória
trabalhista: quem é o reclamante, qual contrato foi reconhecido, o
vínculo, o desligamento e a remuneração de cada período. O S-2501
informa os valores pagos e os tributos que decorrem deles, por período
de apuração. A partir de 01/05/2026 o FGTS dessa origem é recolhido pelo
FGTS Digital (retorno pelo S-5503). Alberto decidiu modelar completo. O
processo em si (número, partes, andamentos) vive no Jurídico; aqui entra
só o que é da folha.

Mov_Rh_Processo_Trabalhista

Nova na revisão 16 (Bloco 3 da validação geral). A parte trabalhista de
um processo, para um trabalhador: os dados do evento S-2500 que só
existem em ação trabalhista ou em demanda de CCP/Ninter. Um processo
pode ter vários trabalhadores, e o mesmo trabalhador pode ter mais de um
S-2500 no mesmo processo (Sequencial_Trabalhador); por isso a chave é
própria e não é compartilhada com Cad_Processo. Número do processo, nome
e data de nascimento do trabalhador (nmTrab, dtNascto, nmSoc) não são
repetidos aqui: saem de Cad_Processo e do participante. Vara, comarca e
órgão também não ficam aqui: o processo pode nascer numa vara e ser
transferido, e essa movimentação está em Mov_Processo_Juizo. Conferido
contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: sim --- o processo tem retificação de sentença e novo acordo;
o S-2500 é enviado de novo (retificação). Uma retificação que atinja
competência já informada em S-2501 exige excluir esse S-2501 antes.*

  ------------------------------------------- ---------------------- ----------------------------------------
  **Campo**                                   **Tipo lógico**        **Descrição / regra**

  **ID_Processo_Trabalhista**                 *identificador*        ---

  **ID_Processo**                             *referência            O processo. Area = trabalhista, ou outra
                                              (Cad_Processo, Fase    área quando a origem é a Justiça Comum.
                                              8)*                    O número (nrProcTrab) vem daqui: 20
                                                                     algarismos nas origens judicial e
                                                                     Justiça Comum, 15 na CCP/Ninter. Com
                                                                     data da sentença a partir de 27/04/2026,
                                                                     o 14º algarismo tem de ser 5 na origem
                                                                     judicial e 4 ou 8 na Justiça Comum.

  **ID_Participante_Trabalhador**             *referência            O trabalhador (CPF, nome, data de
                                              (Cad_Participante)*    nascimento e nome social vêm do
                                                                     participante).

  **Sequencial_Trabalhador**                  *código (3), opcional* ideSeqTrab: número que a empresa atribui
                                                                     quando precisa enviar o mesmo processo
                                                                     em mais de um S-2500 para o mesmo
                                                                     trabalhador. A identificação do evento é
                                                                     CPF do declarante, CPF do trabalhador e
                                                                     número do processo.

  **Origem_Processo**                         *enumeração {judicial, origem: 1 processo judicial trabalhista,
                                              ccp_ninter,            2 demanda submetida à CCP ou ao Ninter,
                                              justica_comum}*        3 processo da Justiça Comum. Na Justiça
                                                                     Comum o tipo de contrato só pode ser 1,
                                                                     7 ou 9.

  **Data_Sentenca_Acordo**                    *data*                 dtSent nas origens judicial e Justiça
                                                                     Comum: data da determinação judicial
                                                                     para cumprir a decisão líquida
                                                                     transitada em julgado, da homologação do
                                                                     acordo, do cumprimento antecipado ou da
                                                                     obrigação de fazer. dtCCP na origem
                                                                     CCP/Ninter: data do acordo. Havendo duas
                                                                     determinações no processo, vale a mais
                                                                     antiga que teve S-2500.

  **ID_Juizo_Decisao**                        *referência            O juízo em que a decisão foi proferida:
                                              (Mov_Processo_Juizo,   o vigente em Data_Sentenca_Acordo. Daí
                                              opcional)*             saem ufVara, codMunic e idVara.
                                                                     Obrigatório nas origens judicial e
                                                                     Justiça Comum; vazio na CCP/Ninter.

  **Valor_Cota_Patronal**                     *número, opcional*     infoPatPrec: valor total da cota
                                                                     patronal sobre a remuneração paga ao
                                                                     trabalhador, que será objeto de
                                                                     requisição autônoma. Obrigatório e
                                                                     exclusivo na origem Justiça Comum.

  **Tipo_Ccp**                                *enumeração {empresa,  tpCCP: 1 CCP no âmbito da empresa, 2 no
                                              sindicato, ninter},    âmbito do sindicato, 3 Ninter. Só na
                                              opcional*              origem CCP/Ninter.

  **ID_Participante_Sindicato_Ccp**           *referência            cnpjCCP: o sindicato representativo do
                                              (Cad_Participante,     trabalhador na CCP ou no Ninter.
                                              opcional)*             

  **ID_Participante_Responsavel_Direto**      *referência            ideResp: o responsável direto
                                              (Cad_Participante,     (empregador de origem), quando o
                                              opcional)*             declarante responde de forma indireta.
                                                                     Nesse caso os contratos são do tipo 6 ou
                                                                     8.

  **Data_Admissao_Responsabilidade_Direta**   *data, opcional*       dtAdmRespDir: admissão no responsável
                                                                     direto, quando o vínculo dele não foi
                                                                     informado ao eSocial.

  **Matricula_Responsabilidade_Direta**       *código (30),          matRespDir: matrícula no responsável
                                              opcional*              direto.

  **Observacao**                              *texto, opcional*      obsProcTrab, até 999 caracteres. Aparece
                                                                     no comprovante do processo trabalhista e
                                                                     não alimenta a CTPS Digital.

  **Vigencia_Inicio**                         *data*                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                            *data*                 Último dia em que esta versão vale
                                                                     (inclusive). Sempre preenchida:
                                                                     31/12/9999 quando o fim é indefinido
                                                                     (versão vigente) --- convenção da Fase
                                                                     0, seção 2.

  **Motivo_Vigencia**                         *texto, opcional*      Por que esta versão foi criada.
  ------------------------------------------- ---------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Contrato

Nova na revisão 16 (Bloco 3 da validação geral). Um contrato de trabalho
tratado na decisão ou no acordo (infoContr), de 1 a 99 por trabalhador:
o tipo de contrato, os indicadores do que a decisão muda, os dados do
vínculo reconhecido, o estabelecimento e os períodos e valores. O grupo
infoCompl do XSD (cargo, função, natureza da atividade e remuneração) só
se aplica quando o vínculo não foi declarado ao eSocial (indContr = N).
Conferido contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab e
evtContProc).

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Contrato_Processo** | *identificador* | --- |
| **ID_Processo_Trabalhista** | *referência (Mov_Rh_Processo_Trabalhista)* | --- |
| **ID_Tipo_Contrato** | *referência (Cad_Classe_Sistema, domínio = tipo_contrato_processo_esocial)* | tpContr, nove valores: 1 vínculo formalizado sem alteração de datas; 2 com alteração da data de admissão; 3 com inclusão ou alteração da data de desligamento; 4 com alteração das duas datas; 5 reconhecimento de vínculo de emprego; 6 trabalhador sem vínculo de emprego ou estatutário (TSVE) sem reconhecimento de vínculo; 7 vínculo formalizado antes do eSocial; 8 responsabilidade indireta; 9 unicidade contratual (inclui reconhecimento de vínculo de quem já foi informado como TSVE). |
| **Vinculo_Informado_Esocial** | *booleano, calculado e armazenado* | indContr: verdadeiro quando o contrato já tem informação em S-2190, S-2200 ou S-2300 do declarante; calculado a partir de ID_Vinculo e guardado porque vai no evento. Deve ser falso no tipo 8, e verdadeiro nos tipos 1 a 4. |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego, opcional)* | O vínculo existente na folha. Vazio quando o contrato é reconhecido só pela decisão. |
| **Matricula** | *código (30), opcional* | matricula: a mesma já declarada no eSocial; num contrato novo, a matrícula criada para o vínculo reconhecido. No servidor público, a do sistema de RH do órgão. |
| **ID_Categoria_Esocial** | *referência (Cad_Classe_Sistema, domínio = categoria_trabalhador_esocial, opcional)* | codCateg (3 dígitos) do contrato. |
| **Data_Inicio_Tsve** | *data, opcional* | dtInicio: início do trabalhador sem vínculo de emprego (TSVE). |
| **Data_Admissao_Original** | *data, opcional* | dtAdmOrig: data de admissão antes da alteração feita pela decisão. No tipo 7 é a informada na GFIP. |
| **Reintegracao** | *booleano, opcional* | indReint: houve reintegração do empregado. |
| **Muda_Categoria** | *booleano* | indCateg: a decisão reconheceu categoria diferente da informada ao eSocial ou à GFIP (as categorias reconhecidas ficam em Mov_Rh_Processo_Trabalhista_Mudanca_Categoria). |
| **Muda_Natureza_Atividade** | *booleano* | indNatAtiv: a decisão reconheceu natureza da atividade diferente da cadastrada. |
| **Muda_Motivo_Desligamento** | *booleano* | indMotDeslig: a decisão reconheceu motivo de desligamento diferente do informado (por exemplo rescisão indireta). |
| **ID_Cargo** | *referência (Cad_Rh_Cargo, opcional)* | Cargo do cadastro, quando existe; nome e CBO saem dele. Sem ele, valem Nome_Cargo e ID_Cbo. |
| **Nome_Cargo** | *texto, opcional* | nmCargo (até 100 caracteres), no infoCompl. Obrigatório quando a categoria é diferente de 901, 903, 904 e 906 e Data_Sentenca_Acordo (origem judicial e Justiça Comum) ou a data do acordo (CCP e Ninter) é igual ou posterior a 26/10/2026 (revisão 19, NT 07/2026). |
| **ID_Cbo** | *referência (Cad_Classe_Sistema, domínio = cbo, opcional)* | codCBO (6 posições) do cargo. Revisão 19: obrigatório quando a categoria é diferente de 901, 903, 904 e 906, sem limite de data. |
| **Nome_Funcao** | *texto, opcional* | nmFuncao (até 100): função de confiança ou cargo em comissão. |
| **ID_Cbo_Funcao** | *referência (Cad_Classe_Sistema, domínio = cbo, opcional)* | CBOFuncao: CBO da função de confiança. |
| **Natureza_Atividade** | *enumeração {urbano, rural}, opcional* | natAtividade: 1 trabalho urbano, 2 rural. Categoria 104 exige urbano e 102 exige rural. |
| **Regime_Trabalhista** | *enumeração {clt, estatutario, servidor_nulo}, opcional* | tpRegTrab (infoVinc): 1 CLT e legislações trabalhistas específicas, 2 estatutário e legislações específicas, 3 contrato de servidor público declarado nulo. |
| **ID_Regime_Previdenciario** | *referência (Cad_Classe_Sistema, domínio = regime_previdenciario), opcional* | tpRegPrev: 1 RGPS, 2 RPPS, regime dos parlamentares e proteção social dos militares, 3 previdência no exterior. Revisão 17 (D-N305, complemento): usa o mesmo domínio de Cad_Vinculo_Emprego (rgps 1, rpps 2, exterior 3, spsmfa 4). A conferir no leiaute do S-2500 se o valor 4 (spsmfa) é aceito nesse evento; o domínio guarda o valor e a validação do evento decide. |
| **Data_Admissao_Reconhecida** | *data, opcional* | dtAdm (infoVinc): data de admissão do trabalhador. |
| **Tempo_Parcial** | *enumeração {nao_e_tempo_parcial, ate_25_horas, ate_30_horas, ate_26_horas}, opcional* | tmpParc: 0 não é tempo parcial, 1 limitado a 25 horas semanais (só categoria 104), 2 limitado a 30 horas, 3 limitado a 26 horas. |
| **Tipo_Duracao_Contrato** | *enumeração {indeterminado, determinado_em_dias, determinado_por_fato}, opcional* | tpContr do grupo duracao: 1 prazo indeterminado, 2 prazo determinado em dias, 3 prazo determinado vinculado a um fato. |
| **Data_Termino_Contrato** | *data, opcional* | dtTerm da duração: término do contrato por prazo determinado. |
| **Clausula_Assecuratoria** | *booleano, opcional* | clauAssec: o contrato por prazo determinado tem cláusula assecuratória do direito recíproco de rescisão antecipada. |
| **Objeto_Contrato_Determinado** | *texto, opcional* | objDet (até 255): objeto que determinou a contratação por prazo determinado (obra, serviço, safra). |
| **ID_Participante_Empregador_Anterior** | *referência (Cad_Participante, opcional)* | sucessaoVinc: o empregador anterior na sucessão. O tipo e o número de inscrição saem do participante (CNPJ, CPF, e CGC ou CEI só se a transferência for até 30/06/1999). |
| **Matricula_Anterior** | *código (30), opcional* | matricAnt: matrícula no empregador anterior. |
| **Data_Transferencia** | *data, opcional* | dtTransf: transferência do empregado para o declarante. |
| **Data_Desligamento** | *data, opcional* | dtDeslig (infoDeslig): último dia trabalhado. |
| **ID_Motivo_Desligamento** | *referência (Cad_Rh_Motivo_Desligamento, opcional)* | mtvDeslig, da Tabela 19 do eSocial. |
| **Data_Projecao_Fim_Aviso_Indenizado** | *data, opcional* | dtProjFimAPI: término projetado do aviso prévio indenizado. |
| **Tipo_Pensao_Alimenticia** | *enumeração {nao_existe, percentual, valor, percentual_e_valor}, opcional* | pensAlim: para retenção do FGTS. 0 não existe, 1 percentual, 2 valor, 3 percentual e valor. |
| **Percentual_Pensao** | *número, opcional* | percAliment. |
| **Valor_Pensao** | *número, opcional* | vrAlim. |
| **Data_Termino_Tsve** | *data, opcional* | dtTerm de infoTerm: fim do trabalhador sem vínculo. |
| **Motivo_Termino_Diretor** | *enumeração {sem_justa_causa, fim_de_mandato, a_pedido, culpa_reciproca_ou_forca_maior, morte, falencia_ou_encerramento, outros}, opcional* | mtvDesligTSV (01 a 06 e 99): obrigatório e exclusivo para a categoria 721, diretor não empregado com FGTS. |
| **Tipo_Inscricao_Local_Trabalho** | *enumeração {cnpj, caepf, cno}, opcional* | localTrabGeral/tpInsc: 1 CNPJ, 3 CAEPF, 4 CNO. Revisão 19 (NT 07/2026), regra do grupo do local de trabalho (Tipo e Numero_Inscricao_Local_Trabalho, Descricao_Complemento_Local_Trabalho e ID_Endereco_Trabalho_Temporario), só quando o grupo infoCompl é enviado (Vinculo_Informado_Esocial = falso). Obrigatório quando a categoria é 1XX, 301, 302, 303, 306, 307, 309, 310, 312 ou 314 e Data_Admissao_Reconhecida é igual ou posterior a 26/10/2026; ou quando a categoria é 2XX, 304, 305, 4XX, 721, 722, 723, 731, 734, 738, 761, 771, 901, 902 ou 906 e Data_Inicio_Tsve é igual ou posterior a 26/10/2026. Proibido nas mesmas categorias com data anterior; não informado nas demais. No local de trabalho geral (tpInsc e nrInsc), não é informado na categoria 104 e é obrigatório nas demais categorias do grupo. |
| **Numero_Inscricao_Local_Trabalho** | *código (14), opcional* | localTrabGeral/nrInsc: o estabelecimento onde o trabalhador exerce as atividades. |
| **Descricao_Complemento_Local_Trabalho** | *texto, opcional* | descComp (até 80). |
| **ID_Endereco_Trabalho_Temporario** | *referência (Cad_Participante_Endereco, opcional)* | localTempDom: endereço de trabalho do doméstico ou do temporário. |
| **ID_Filial** | *referência (Cad_Filial, opcional)* | ideEstab: o estabelecimento da empresa. Vazio quando a inscrição é CAEPF ou CNO. |
| **Tipo_Inscricao_Estabelecimento** | *enumeração {cnpj, caepf, cno}* | ideEstab/tpInsc: 1 CNPJ, 3 CAEPF, 4 CNO. Declarante CNPJ usa 1 ou 4; declarante CPF usa 3 ou 4. |
| **Numero_Inscricao_Estabelecimento** | *código (14), opcional* | ideEstab/nrInsc, preenchido quando a inscrição é CAEPF ou CNO (com CNPJ o número vem da filial). |
| **Competencia_Inicial_Valores** | *competência* | compIni: primeira competência a que se refere o processo ou a conciliação. |
| **Competencia_Final_Valores** | *competência* | compFim: última competência; não pode ser posterior ao mês atual. |
| **Repercussao** | *enumeração {tributaria_fgts_com_rendimentos_s2501, sem_repercussao, so_ir_com_rendimentos_s2501, so_ir_deposito_judicial, tributaria_fgts_deposito_judicial}* | indReperc: 1 repercussão tributária e/ou FGTS com rendimentos informados em S-2501, 2 sem repercussão tributária ou de FGTS, 3 repercussão exclusiva de IR com rendimentos informados em S-2501, 4 exclusiva de IR com pagamento por depósito judicial, 5 tributária e/ou FGTS com pagamento por depósito judicial. |
| **Indenizacao_Substitutiva_Seguro_Desemprego** | *booleano, opcional* | indenSD: houve decisão de pagar indenização substitutiva do seguro-desemprego. |
| **Indenizacao_Substitutiva_Abono** | *booleano, opcional* | indenAbono: houve decisão de pagar indenização substitutiva de abono salarial (os anos-base ficam em Mov_Rh_Processo_Trabalhista_Abono). |
| **ID_Cno_Obra** | *referência (Cad_Cno_Obra, opcional)* | Novo na revisão 3 (documento 37). Obra do CNO quando a inscrição do estabelecimento ou do local de trabalho é CNO. |

*Revisão 3 --- campos novos (documento 37): ID_Cno_Obra.*

*Revisão 17 --- campos renomeados: Regime_Previdenciario para ID_Regime_Previdenciario.*

Mov_Rh_Processo_Trabalhista_Contrato_Observacao

Nova na revisão 16 (Bloco 3 da validação geral). Observações do contrato
(observacoes/observacao), de 0 a 99 por contrato. Alimentam as anotações
gerais da CTPS Digital, sem a checagem da vedação a anotações
desabonadoras do art. 29, § 4º, da CLT: essa avaliação é do empregador.
Conferido contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab e
evtContProc).

*Vigência: não.*

  ---------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**                           **Descrição / regra**

  **ID_Observacao_Contrato**   *identificador*                           ---

  **ID_Contrato_Processo**     *referência                               ---
                               (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **Observacao**               *texto*                                   observacao, até 255 caracteres. Para o
                                                                         que deve ser anotado na CTPS Digital e
                                                                         não tem campo próprio (estimativa de
                                                                         gorjeta, aprendiz em arco ocupacional,
                                                                         determinação judicial).
  ---------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Remuneracao

Nova na revisão 16 (Bloco 3 da validação geral). Remuneração reconhecida
na decisão (grupo remuneracao do S-2500, só quando o vínculo não estava
declarado): data, salário fixo e a unidade dele, de 0 a 99 por contrato.
Corrigido na consolidação: o desenho aprovado a tratava como remuneração
por período de apuração (remunPerApur, que é do S-1200); a remuneração
mês a mês está em Mov_Rh_Processo_Trabalhista_Periodo. Conferido contra
o XSD oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  -------------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**                           **Descrição / regra**

  **ID_Remuneracao_Processo**      *identificador*                           ---

  **ID_Contrato_Processo**         *referência                               ---
                                   (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **Data_Remuneracao**             *data*                                    dtRemun: data a partir da qual a
                                                                             remuneração vale. O salário fixo tem de
                                                                             ser o vigente nessa data.

  **Valor_Salario_Fixo**           *número*                                  vrSalFx: parte fixa da remuneração.

  **Unidade_Salario_Fixo**         *enumeração {hora, dia, semana, quinzena, undSalFixo: 1 por hora, 2 por dia, 3 por
                                   mes, tarefa, somente_variavel}*           semana, 4 por quinzena, 5 por mês, 6 por
                                                                             tarefa, 7 não aplicável, salário
                                                                             exclusivamente variável.

  **Descricao_Salario_Variavel**   *texto, opcional*                         dscSalVar (até 999): como o salário
                                                                             variável ou por tarefa é calculado.
  -------------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Mudanca_Categoria

Nova na revisão 16 (Bloco 3 da validação geral). Categoria e natureza da
atividade reconhecidas ao longo do contrato (mudCategAtiv), de 0 a 99
por contrato. Conferido contra o XSD oficial do leiaute S-1.3.00
(evtProcTrab e evtContProc).

*Vigência: não.*

  -------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                           **Descrição / regra**

  **ID_Mudanca_Categoria**   *identificador*                           ---

  **ID_Contrato_Processo**   *referência                               ---
                             (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **ID_Categoria_Esocial**   *referência (Cad_Classe_Sistema, domínio  codCateg: a categoria reconhecida.
                             = categoria_trabalhador_esocial)*         

  **Natureza_Atividade**     *enumeração {urbano, rural}, opcional*    natAtividade.

  **Data_Mudanca**           *data*                                    dtMudCategAtiv: a partir de quando a
                                                                       nova categoria ou natureza foi
                                                                       reconhecida.
  -------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Unicidade

Nova na revisão 16 (Bloco 3 da validação geral). Vínculos ou contratos
incorporados ao período de unicidade contratual reconhecido pela decisão
(unicContr), de 0 a 99 por contrato. Para o TSVE incorporado, vale a
data de início em vez da matrícula. Conferido contra o XSD oficial do
leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  --------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                           **Descrição / regra**

  **ID_Unicidade_Contrato**   *identificador*                           ---

  **ID_Contrato_Processo**    *referência                               ---
                              (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **Matricula_Incorporada**   *código (30), opcional*                   matUnic: a matrícula cujo vínculo passou
                                                                        a integrar o período de unicidade.

  **ID_Categoria_Esocial**    *referência (Cad_Classe_Sistema, domínio  codCateg do contrato incorporado.
                              = categoria_trabalhador_esocial,          
                              opcional)*                                

  **Data_Inicio_Tsve**        *data, opcional*                          dtInicio do TSVE incorporado.
  --------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Abono

Nova na revisão 16 (Bloco 3 da validação geral). Anos-base da
indenização substitutiva de abono salarial (abono/anoBase), de 0 a 9 por
contrato. Conferido contra o XSD oficial do leiaute S-1.3.00
(evtProcTrab e evtContProc).

*Vigência: não.*

  -------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                           **Descrição / regra**

  **ID_Abono_Processo**      *identificador*                           ---

  **ID_Contrato_Processo**   *referência                               ---
                             (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **Ano_Base**               *código (4)*                              anoBase, de 1900 em diante.
  -------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Periodo

Nova na revisão 16 (Bloco 3 da validação geral). Competência a
competência da decisão (idePeriodo do S-2500), de 0 a 999 por contrato:
bases de contribuição, grau de exposição, bases do FGTS e mudança de
categoria. Conferido contra o XSD oficial do leiaute S-1.3.00
(evtProcTrab e evtContProc).

*Vigência: não.*

  ----------------------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                                 **Tipo lógico**                           **Descrição / regra**

  **ID_Periodo_Processo**                   *identificador*                           ---

  **ID_Contrato_Processo**                  *referência                               ---
                                            (Mov_Rh_Processo_Trabalhista_Contrato)*   

  **Competencia_Referencia**                *competência*                             perRef; entre
                                                                                      Competencia_Inicial_Valores e
                                                                                      Competencia_Final_Valores do contrato.

  **Base_Contribuicao_Mensal**              *número, opcional*                        vrBcCpMensal (baseCalculo): base da
                                                                                      contribuição previdenciária sobre a
                                                                                      remuneração mensal, ainda não declarada.

  **Base_Contribuicao_Decimo_Terceiro**     *número, opcional*                        vrBcCp13: base sobre o 13º salário.

  **Grau_Exposicao**                        *enumeração {nao_enseja, fae_15_anos_12,  grauExp (infoAgNocivo): 1 não enseja
                                            fae_20_anos_9, fae_25_anos_6}, opcional*  aposentadoria especial, 2 aposentadoria
                                                                                      especial aos 15 anos e alíquota de 12%,
                                                                                      3 aos 20 anos e 9%, 4 aos 25 anos e 6%.
                                                                                      Tabela 02 do eSocial.

  **Base_Fgts_Processo**                    *número, opcional*                        vrBcFGTSProcTrab (infoFGTS): base do
                                                                                      FGTS ainda não declarada no SEFIP ou no
                                                                                      eSocial, inclusive a de verba
                                                                                      reconhecida no processo. Obrigatória
                                                                                      quando há infoFGTS.

  **Base_Fgts_Sefip**                       *número, opcional*                        vrBcFGTSSefip: base declarada apenas no
                                                                                      SEFIP e ainda não recolhida.

  **Base_Fgts_Declarada_Anteriormente**     *número, opcional*                        vrBcFGTSDecAnt: base declarada antes no
                                                                                      eSocial e ainda não recolhida.

  **ID_Categoria_Esocial_Mudanca**          *referência (Cad_Classe_Sistema, domínio  codCateg de baseMudCateg: a categoria
                                            = categoria_trabalhador_esocial,          declarada no período.
                                            opcional)*                                

  **Base_Contribuicao_Mudanca_Categoria**   *número, opcional*                        vrBcCPrev: remuneração declarada em GFIP
                                                                                      ou em S-1200 a considerar para fins
                                                                                      previdenciários, no reconhecimento de
                                                                                      mudança de categoria.
  ----------------------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Intermitente

Nova na revisão 16 (Bloco 3 da validação geral). Dias e horas
trabalhados no mês no contrato intermitente (infoInterm), de 0 a 31 por
competência. Conferido contra o XSD oficial do leiaute S-1.3.00
(evtProcTrab e evtContProc).

*Vigência: não.*

  ------------------------------ ---------------------------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**                          **Descrição / regra**

  **ID_Intermitente_Processo**   *identificador*                          ---

  **ID_Periodo_Processo**        *referência                              ---
                                 (Mov_Rh_Processo_Trabalhista_Periodo)*   

  **Dia**                        *número*                                 dia, de 0 a 31.

  **Horas_Trabalhadas**          *código (4), opcional*                   hrsTrab, no formato HHMM.
  ------------------------------ ---------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Apuracao

Nova na revisão 16 (Bloco 3 da validação geral). O S-2501: valores pagos
e tributos decorrentes do processo, por competência do pagamento. O
evento é do processo e admite vários trabalhadores
(Mov_Rh_Processo_Trabalhista_Apuracao_Trabalhador). Data e valor do
pagamento, depósito de garantia e título a pagar são do sistema, não do
leiaute. Conferido contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab
e evtContProc).

*Vigência: não.*

  --------------------------- ---------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                    **Descrição / regra**

  **ID_Apuracao_Processo**    *identificador*                    ---

  **ID_Processo**             *referência (Cad_Processo)*        nrProcTrab: o mesmo número do S-2500.

  **Competencia_Pagamento**   *competência*                      perApurPgto: mês/ano em que é devida a
                                                                 obrigação de pagar a parcela prevista no
                                                                 acordo ou na sentença.

  **Sequencial_Processo**     *código (3), opcional*             ideSeqProc: para enviar o mesmo processo
                                                                 em mais de um S-2501 na mesma
                                                                 competência.

  **Data_Pagamento**          *data*                             ---

  **Valor_Total_Pago**        *número*                           ---

  **ID_Deposito_Garantia**    *referência                        Depósito judicial ou garantia que serviu
                              (Mov_Processo_Deposito_Garantia,   ao pagamento.
                              opcional)*                         

  **ID_Titulo**               *referência (Mov_Titulo,           Título de Contas a Pagar do pagamento.
                              opcional)*                         

  **Status**                  *enumeração {calculada, enviada,   ---
                              fechada}*                          

  **Observacao**              *texto, opcional*                  obs, até 999 caracteres: observação
                                                                 sobre o pagamento da parcela.
  --------------------------- ---------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Apuracao_Trabalhador

Nova na revisão 16 (Bloco 3 da validação geral). Um trabalhador dentro
do S-2501 (ideTrab), de 1 em diante. Reúne as bases (calcTrib), os
códigos de receita do IRRF (infoCRIRRF) e os complementos de imposto de
renda (infoIRComplem). Conferido contra o XSD oficial do leiaute
S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  ----------------------------- ----------------------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**                           **Descrição / regra**

  **ID_Apuracao_Trabalhador**   *identificador*                           ---

  **ID_Apuracao_Processo**      *referência                               ---
                                (Mov_Rh_Processo_Trabalhista_Apuracao)*   

  **ID_Processo_Trabalhista**   *referência                               O S-2500 do trabalhador; daí saem o CPF
                                (Mov_Rh_Processo_Trabalhista)*            (cpfTrab) e o contrato.

  **Data_Laudo_Molestia**       *data, opcional*                          dtLaudo (infoIRComplem): data da
                                                                          moléstia grave atribuída pelo laudo.
  ----------------------------- ----------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Apuracao_Base

Nova na revisão 16 (Bloco 3 da validação geral). Bases e valores devidos
por competência de referência dentro do trabalhador da apuração
(calcTrib), de 0 a 999. As contribuições sociais por código de receita
(infoCRContrib) ficam em Mov_Rh_Processo_Trabalhista_Tributo. Base do
FGTS, valor do FGTS devido, base do IRRF e desconto do trabalhador são
cálculos do sistema, não campos do leiaute; o retorno do FGTS (S-5503)
chega em Mov_Esocial_Mensagem. Conferido contra o XSD oficial do leiaute
S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  --------------------------------------------- ----------------------------------------------------- ----------------------------------------
  **Campo**                                     **Tipo lógico**                                       **Descrição / regra**

  **ID_Apuracao_Base**                          *identificador*                                       ---

  **ID_Apuracao_Trabalhador**                   *referência                                           ---
                                                (Mov_Rh_Processo_Trabalhista_Apuracao_Trabalhador)*   

  **ID_Contrato_Processo**                      *referência (Mov_Rh_Processo_Trabalhista_Contrato,    O contrato a que a base se refere.
                                                opcional)*                                            

  **Competencia_Referencia**                    *competência*                                         perRef: mês de referência das
                                                                                                      informações.

  **Base_Contribuicao_Mensal**                  *número*                                              vrBcCpMensal: obrigatório no leiaute.

  **Base_Contribuicao_Decimo_Terceiro**         *número*                                              vrBcCp13: obrigatório no leiaute (zero
                                                                                                      quando não há).

  **Base_Fgts**                                 *número, opcional*                                    Cálculo do sistema (FGTS Digital).

  **Valor_Fgts_Devido**                         *número, opcional*                                    Cálculo do sistema; o recolhimento é
                                                                                                      feito pelo FGTS Digital.

  **Base_Irrf**                                 *número, opcional*                                    Cálculo do sistema.

  **Valor_Desconto_Contribuicao_Trabalhador**   *número, opcional*                                    Parte da contribuição descontada do
                                                                                                      trabalhador.
  --------------------------------------------- ----------------------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Tributo

Nova na revisão 16 (Bloco 3 da validação geral). Tributos decorrentes da
apuração, um por código de receita: contribuições sociais por
competência (infoCRContrib, dentro do calcTrib) e IRRF (infoCRIRRF,
dentro do trabalhador). Conferido contra o XSD oficial do leiaute
S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  ----------------------------------- ----------------------------------------------------- ----------------------------------------
  **Campo**                           **Tipo lógico**                                       **Descrição / regra**

  **ID_Tributo_Processo**             *identificador*                                       ---

  **ID_Apuracao_Trabalhador**         *referência                                           ---
                                      (Mov_Rh_Processo_Trabalhista_Apuracao_Trabalhador)*   

  **ID_Apuracao_Base**                *referência                                           Preenchido nas contribuições sociais
                                      (Mov_Rh_Processo_Trabalhista_Apuracao_Base,           (infoCRContrib), que pertencem a uma
                                      opcional)*                                            competência; vazio no IRRF.

  **ID_Imposto**                      *referência (Cad_Imposto)*                            ---

  **Codigo_Receita**                  *código (6)*                                          tpCR. Contribuições sociais: código de
                                                                                            receita da Previdência Social e de
                                                                                            outras entidades e fundos, conforme a
                                                                                            legislação da competência. IRRF: 593656,
                                                                                            056152 ou 188951 (este é o IRRF sobre
                                                                                            RRA).

  **Base_Calculo**                    *número, opcional*                                    Cálculo do sistema.

  **Aliquota_Aplicada**               *número, opcional*                                    Cálculo do sistema.

  **Valor_Tributo**                   *número*                                              vrCR: valor do código de receita (no
                                                                                            IRRF, o do rendimento mensal).

  **Valor_Tributo_Decimo_Terceiro**   *número, opcional*                                    vrCR13 do IRRF: valor do 13º salário.
                                                                                            Não se informa quando o código de
                                                                                            receita é 188951.

  **ID_Titulo**                       *referência (Mov_Titulo, opcional)*                   Título a pagar da guia.
  ----------------------------------- ----------------------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Ir

Nova na revisão 16 (Bloco 3 da validação geral). Informações de imposto
de renda de um código de receita do IRRF (infoIR, com rendIsen0561 e
infoRRA): rendimentos tributáveis, isentos, juros de mora, previdência
oficial, rendimentos recebidos acumuladamente e despesas do processo. Os
dependentes de infoIRComplem/infoDep (cpfDep, dtNascto, nome, depIRRF,
tpDep e descrDep) não têm tabela própria: saem de
Cad_Participante_Dependente (CPF, Data_Nascimento, Nome, Elegivel_Irrf,
ID_Tipo_Dependente), e o grupo é gerado quando o dependente ainda não
foi informado ao eSocial; a descrição da dependência (descrDep) é
exigida só para o tipo 99, agregado e outros. Conferido contra o XSD
oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  -------------------------------------------- --------------------------------------- ----------------------------------------
  **Campo**                                    **Tipo lógico**                         **Descrição / regra**

  **ID_Tributo_Processo**                      *referência                             Extensão 1:1 do código de receita do
                                               (Mov_Rh_Processo_Trabalhista_Tributo)   IRRF.
                                               --- chave primária compartilhada*       

  **Valor_Rendimento_Tributavel**              *número, opcional*                      vrRendTrib: rendimento tributável
                                                                                       mensal.

  **Valor_Rendimento_Tributavel_13**           *número, opcional*                      vrRendTrib13: rendimento do 13º com
                                                                                       tributação exclusiva.

  **Valor_Rendimento_Molestia_Grave**          *número, opcional*                      vrRendMoleGrave: rendimento isento por
                                                                                       moléstia grave atestada em laudo.

  **Valor_Rendimento_Molestia_Grave_13**       *número, opcional*                      vrRendMoleGrave13.

  **Valor_Rendimento_Isento_65**               *número, opcional*                      vrRendIsen65: parcela isenta de
                                                                                       aposentadoria para maiores de 65 anos.

  **Valor_Rendimento_Isento_65_13**            *número, opcional*                      vrRendIsen65Dec.

  **Valor_Juros_Mora**                         *número, opcional*                      vrJurosMora: juros de mora pelo atraso
                                                                                       no pagamento de remuneração de emprego,
                                                                                       cargo ou função.

  **Valor_Juros_Mora_13**                      *número, opcional*                      vrJurosMora13.

  **Valor_Rendimento_Isento_Nao_Tributavel**   *número, opcional*                      vrRendIsenNTrib: outros rendimentos
                                                                                       isentos ou não tributáveis.

  **Descricao_Isento_Nao_Tributavel**          *texto, opcional*                       descIsenNTrib (até 60).

  **Valor_Previdencia_Oficial**                *número, opcional*                      vrPrevOficial.

  **Valor_Previdencia_Oficial_13**             *número, opcional*                      vrPrevOficial13.

  **Valor_Diarias**                            *número, opcional*                      vlrDiarias, rendimento isento exclusivo
                                                                                       do código 0561.

  **Valor_Ajuda_Custo**                        *número, opcional*                      vlrAjudaCusto.

  **Valor_Indenizacao_Rescisao_Contrato**      *número, opcional*                      vlrIndResContrato: inclusive PDV e
                                                                                       acidentes de trabalho.

  **Valor_Abono_Pecuniario**                   *número, opcional*                      vlrAbonoPec.

  **Valor_Auxilio_Moradia**                    *número, opcional*                      vlrAuxMoradia.

  **Descricao_Rra**                            *texto, opcional*                       descRRA: rendimentos recebidos
                                                                                       acumuladamente.

  **Quantidade_Meses_Rra**                     *número, opcional*                      qtdMesesRRA.

  **Valor_Custas**                             *número, opcional*                      vlrDespCustas (despProcJud): custas
                                                                                       judiciais.

  **Valor_Honorarios_Advocaticios**            *número, opcional*                      vlrDespAdvogados (despProcJud): total
                                                                                       das despesas com advogados.
  -------------------------------------------- --------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Advogado

Nova na revisão 16 (Bloco 3 da validação geral). Advogados que receberam
honorários (ideAdv, dentro do infoRRA), de 0 a 99. Conferido contra o
XSD oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  ------------------------------ ----------------------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**                     **Descrição / regra**

  **ID_Advogado_Processo**       *identificador*                     ---

  **ID_Tributo_Processo**        *referência                         ---
                                 (Mov_Rh_Processo_Trabalhista_Ir)*   

  **ID_Participante_Advogado**   *referência (Cad_Participante)*     O advogado ou escritório (tpInsc e
                                                                     nrInsc vêm do participante).

  **Valor_Honorario**            *número, opcional*                  vlrAdv.
  ------------------------------ ----------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Deducao_Dependente

Nova na revisão 16 (Bloco 3 da validação geral). Dedução do rendimento
tributável por dependente (dedDepen), de 0 a 999 por código de receita
do IRRF. Conferido contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab
e evtContProc).

*Vigência: não.*

  --------------------------- ---------------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                          **Descrição / regra**

  **ID_Deducao_Dependente**   *identificador*                          ---

  **ID_Tributo_Processo**     *referência                              ---
                              (Mov_Rh_Processo_Trabalhista_Tributo)*   

  **ID_Dependente**           *referência                              cpfDep.
                              (Cad_Participante_Dependente)*           

  **Tipo_Rendimento**         *enumeração {mensal, decimo_terceiro}*   tpRend: 11 remuneração mensal, 12 13º
                                                                       salário.

  **Valor_Deducao**           *número*                                 vlrDeducao: maior que zero e até o valor
                                                                       unitário da dedução por dependente na
                                                                       legislação (fora disso o arquivo é
                                                                       aceito com alerta).
  --------------------------- ---------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Pensao

Nova na revisão 16 (Bloco 3 da validação geral). Beneficiários da pensão
alimentícia com dedução do rendimento tributável (penAlim), de 0 a 99
por código de receita do IRRF. Conferido contra o XSD oficial do leiaute
S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  ---------------------------------- ---------------------------------------- ----------------------------------------
  **Campo**                          **Tipo lógico**                          **Descrição / regra**

  **ID_Pensao_Processo**             *identificador*                          ---

  **ID_Tributo_Processo**            *referência                              ---
                                     (Mov_Rh_Processo_Trabalhista_Tributo)*   

  **ID_Participante_Beneficiario**   *referência (Cad_Participante)*          cpfDep: o beneficiário da pensão; tem de
                                                                              ser dependente cadastrado no eSocial.

  **ID_Pensao**                      *referência (Cad_Rh_Pensao_Alimenticia,  A pensão cadastrada em Folha & RH,
                                     opcional)*                               quando existe.

  **Tipo_Rendimento**                *enumeração {mensal, decimo_terceiro,    tpRend: 11 remuneração mensal, 12 13º
                                     rra, isento_ou_nao_tributavel}*          salário, 18 RRA (obrigatório e exclusivo
                                                                              com o código de receita 188951), 79
                                                                              rendimento isento ou não tributável.

  **Valor_Pensao**                   *número*                                 vlrPensao: maior que zero.
  ---------------------------------- ---------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Retencao_Suspensa

Nova na revisão 16 (Bloco 3 da validação geral). Processo administrativo
ou judicial que suspende a exigibilidade do IRRF (infoProcRet), de 0 a
50 por código de receita do IRRF. O tipo, o número e o código da
suspensão saem de Mov_Processo_Suspensao (S-1070). Conferido contra o
XSD oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  --------------------------- ---------------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                          **Descrição / regra**

  **ID_Retencao_Suspensa**    *identificador*                          ---

  **ID_Tributo_Processo**     *referência                              ---
                              (Mov_Rh_Processo_Trabalhista_Tributo)*   

  **ID_Processo_Suspensao**   *referência (Mov_Processo_Suspensao)*    tpProcRet (1 administrativo, 2
                                                                       judicial), nrProcRet e codSusp. Tem de
                                                                       constar na tabela de processos do
                                                                       S-1070.
  --------------------------- ---------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Retencao_Suspensa_Valor

Nova na revisão 16 (Bloco 3 da validação geral). Valores da retenção não
efetuada ou depositada, por período de apuração (infoValores), de 0 a 2
por processo de suspensão: um mensal e um anual. Conferido contra o XSD
oficial do leiaute S-1.3.00 (evtProcTrab e evtContProc).

*Vigência: não.*

  ------------------------------------- -------------------------------------------------- ----------------------------------------
  **Campo**                             **Tipo lógico**                                    **Descrição / regra**

  **ID_Retencao_Valor**                 *identificador*                                    ---

  **ID_Retencao_Suspensa**              *referência                                        ---
                                        (Mov_Rh_Processo_Trabalhista_Retencao_Suspensa)*   

  **Indicador_Apuracao**                *enumeração {mensal, anual_decimo_terceiro}*       indApuracao: 1 mensal, 2 anual (13º
                                                                                           salário).

  **Valor_Nao_Retido**                  *número, opcional*                                 vlrNRetido: retenção que deixou de ser
                                                                                           efetuada por causa do processo.

  **Valor_Deposito_Judicial**           *número, opcional*                                 vlrDepJud.

  **Valor_Compensado_Ano_Calendario**   *número, opcional*                                 vlrCmpAnoCal.

  **Valor_Compensado_Ano_Anterior**     *número, opcional*                                 vlrCmpAnoAnt.

  **Valor_Rendimento_Suspenso**         *número, opcional*                                 vlrRendSusp.
  ------------------------------------- -------------------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Deducao_Suspensa

Nova na revisão 16 (Bloco 3 da validação geral). Deduções da base do
imposto de renda com exigibilidade suspensa (dedSusp), de 0 a 25 por
valor de retenção. Conferido contra o XSD oficial do leiaute S-1.3.00
(evtProcTrab e evtContProc).

*Vigência: não.*

  ---------------------------- -------------------------------------------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**                                          **Descrição / regra**

  **ID_Deducao_Suspensa**      *identificador*                                          ---

  **ID_Retencao_Valor**        *referência                                              ---
                               (Mov_Rh_Processo_Trabalhista_Retencao_Suspensa_Valor)*   

  **Tipo_Deducao**             *enumeração {previdencia_oficial, pensao_alimenticia,    indTpDeducao: 1 previdência oficial, 5
                               dependentes}*                                            pensão alimentícia, 7 dependentes.

  **Valor_Deducao_Suspensa**   *número, opcional*                                       vlrDedSusp.
  ---------------------------- -------------------------------------------------------- ----------------------------------------

Mov_Rh_Processo_Trabalhista_Deducao_Suspensa_Beneficiario

Nova na revisão 16 (Bloco 3 da validação geral). Dependentes e
beneficiários de pensão de uma dedução suspensa (benefPen), de 0 a 99.
Conferido contra o XSD oficial do leiaute S-1.3.00 (evtProcTrab e
evtContProc).

*Vigência: não.*

  ------------------------------- ------------------------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                                   **Descrição / regra**

  **ID_Beneficiario_Suspenso**    *identificador*                                   ---

  **ID_Deducao_Suspensa**         *referência                                       ---
                                  (Mov_Rh_Processo_Trabalhista_Deducao_Suspensa)*   

  **ID_Dependente**               *referência (Cad_Participante_Dependente)*        cpfDep.

  **Valor_Dependente_Suspenso**   *número, opcional*                                vlrDepenSusp.
  ------------------------------- ------------------------------------------------- ----------------------------------------

Ligação com o resto: Mov_Esocial_Evento.Origem_Tipo ganha
mov_rh_processo_trabalhista e mov_rh_processo_trabalhista_apuracao, para
que o envio do S-2500 e do S-2501 fique rastreado como os demais
eventos. O pagamento passa a ser título em Contas a Pagar com
Origem_Tipo = processo_trabalhista (valor novo em
Mov_Titulo.Origem_Tipo). A provisão da contingência trabalhista sai do
prognóstico (Fase 8 --- Jurídico, seção 3), e o pagamento baixa a
provisão.

Validação de esquema (pedido de Alberto): Mov_Esocial_Evento passa a
guardar a versão do leiaute, o resultado da validação do XML contra o
XSD oficial da versão em vigor, a mensagem de erro campo a campo, a data
e hora da validação e o certificado que assinou o envio. Evento inválido
não passa para o status enviado.

Leiautes conferidos contra o XSD oficial: na consolidação os leiautes do
S-2500 (evtProcTrab) e do S-2501 (evtContProc) do S-1.3.00 foram
comparados campo a campo com os esquemas XSD oficiais, e o grupo de
processo trabalhista foi refeito a partir deles. Mudanças em relação ao
desenho aprovado: o processo trabalhista deixou de ser 1:1 com o
processo (um processo tem vários trabalhadores, e o mesmo trabalhador
pode ter mais de um S-2500); a remuneração do S-2500 (dtRemun, vrSalFx,
undSalFixo), que o desenho tratava como a do S-1200; a origem do
processo (judicial, CCP/Ninter, Justiça Comum); os nove tipos de
contrato; as observações, a mudança de categoria, a unicidade contratual
e o abono como tabelas próprias; as bases por competência, o trabalho
intermitente e as bases do FGTS; e, no S-2501, a camada de trabalhador,
o imposto de renda (rendimentos, moléstia grave, RRA, despesas),
advogados, dedução por dependente, pensão alimentícia e retenção com
exigibilidade suspensa. O esquema depende da versão: o S-2500 e o S-2501
mudaram entre os pacotes de abril e dezembro, e vale o mais recente, de
18/01/2027 (nome do pacote enviado). O XSD não traz a tabela de códigos
da Tabela 19 (motivo de desligamento), da CBO nem dos códigos de receita
das contribuições; esses vêm das cargas oficiais.

11\. eSocial --- Caixa de Mensagens

Confirmado por Alberto: controle INDEPENDENTE do envio de eventos,
\"pois não tem só informações de envios, pode ter outras mensagens de
outras origens\" --- o eSocial devolve avisos, pendências e comunicados
de forma assíncrona, não só a resposta direta a um evento enviado. Por
isso Mov_Esocial_Mensagem é uma entidade separada de Mov_Esocial_Evento,
podendo ou não estar relacionada a um evento específico.

Mov_Esocial_Mensagem

Uma mensagem recebida da caixa postal do eSocial --- retorno de um
evento específico, ou um comunicado/pendência de outra origem, sem
relação com um envio.

*Vigência: não --- evento; o histórico completo da caixa é a soma de
todos os registros já recebidos, nunca apagados, mesmo quando lidos.*

  ----------------------------- ---------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**        **Descrição / regra**

  **ID_Mensagem**               *identificador*        ---

  **Origem_Tipo**               *enumeração            retorno_evento: mensagem associada
                                {retorno_evento,       diretamente a um Mov_Esocial_Evento
                                comunicado, pendencia, específico. comunicado/pendencia/outro:
                                outro}*                mensagens da caixa postal sem relação
                                                       com um envio deste sistema --- mesmo
                                                       domínio de origem genérica, mas aqui
                                                       como enumeração fechada por ser um
                                                       conjunto pequeno e estável dos tipos que
                                                       a própria caixa postal do eSocial
                                                       define.

  **ID_Evento_Relacionado**     *referência            Preenchido só quando
                                (Mov_Esocial_Evento,   Origem_Tipo=retorno_evento.
                                opcional)*             

  **Conteudo**                  *texto*                O texto literal da mensagem, como
                                                       recebido --- fidelidade ao valor real,
                                                       nunca reinterpretado.

  **Data_Hora_Recebimento**     *data/hora*            ---

  **Lida**                      *booleano*             ---

  **Data_Leitura**              *data/hora, opcional*  ---

  **ID_Participante_Leitura**   *referência            Quem marcou a mensagem como lida ---
                                (Cad_Participante,     vazio enquanto Lida=falso.
                                opcional)*             
  ----------------------------- ---------------------- ----------------------------------------

Retornos do eSocial para a DCTFWeb (revisão 18)

O eSocial devolve três totalizadores que alimentam a DCTFWeb. O S-5011
traz as contribuições sociais por código de receita, consolidadas e por
estabelecimento, com o valor suspenso, e as bases do PIS/Pasep sobre a
folha. O S-5012 traz o IRRF por código de receita, mensal e diário
(residentes no exterior). O S-5501 traz os tributos de um processo
trabalhista e alimenta a DCTFWeb de Reclamatória Trabalhista. As bases
de remuneração por lotação e categoria do S-5011 ficam só no XML
guardado: a conciliação desta seção compara apenas os valores por código
de receita.

Decisão de 01/10/2026 (P-15): a liquidação da folha não gera mais título
de INSS nem de IRRF retido; lança só a provisão contábil. O S-5011 e o
S-5012 passam a ser o gatilho do título e da baixa da provisão (Contabilidade & Fiscal, seção 22.4). O FGTS Digital, a pensão alimentícia, o consignado e o líquido do
colaborador não mudam.

Mov_Esocial_Retorno

Nova na revisão 18 (Bloco 5). Um totalizador recebido do eSocial (S-5011, S-5012 ou S-5501).

*Vigência: não.*

  -------------------------------------- -------------------------------------- ----------------------------------------------
  **Campo**                              **Tipo lógico**                        **Descrição / regra**

  **ID_Retorno_Esocial**                 *identificador*                        ---

  **ID_Empresa**                         *referência (Cad_Empresa)*             O empregador (matriz).

  **ID_Tipo_Evento**                     *referência (Cad_Classe_Sistema,       S-5011, S-5012 ou S-5501.
                                         domínio = tipo_evento_esocial)*

  **Indicador_Apuracao**                 *enumeração {mensal, anual_13o}*       indApuracao do S-5011, valores 1 e 2 (XSD de
                                                                                26/10/2026): 2 é a apuração anual do 13º
                                                                                salário. O S-5012 e o S-5501 são sempre
                                                                                mensais.

  **Periodo_Apuracao**                   *competência, opcional*                perApur no formato AAAA-MM, quando a apuração
                                                                                é mensal. Vazio no S-5501, que traz o período
                                                                                de referência por linha, e na apuração anual.

  **Ano_Referencia**                     *número, opcional*                     perApur no formato AAAA, quando
                                                                                Indicador_Apuracao = anual_13o. Exatamente um
                                                                                entre Periodo_Apuracao e Ano_Referencia é
                                                                                preenchido, como em Mov_Rh_Folha_Apuracao.

  **ID_Processo_Trabalhista_Apuracao**   *referência                            Só no S-5501: a apuração do processo
                                         (Mov_Rh_Processo_Trabalhista_Apuracao, trabalhista (nrProcTrab) que o originou.
                                         opcional)*

  **Numero_Recibo_Base**                 *texto (60)*                           nrRecArqBase: o recibo do evento de origem,
                                                                                como veio.

  **ID_Evento_Esocial**                  *referência (Mov_Esocial_Evento,       O evento enviado que originou o totalizador,
                                         opcional)*                             achado pelo recibo.

  **Situacao_Vigencia**                  *enumeração {vigente, substituido}*    substituido quando um totalizador posterior da
                                                                                mesma chave (empresa, tipo de evento,
                                                                                indicador de apuração e período) o substitui,
                                                                                depois da reabertura e do novo fechamento da
                                                                                folha (Contabilidade & Fiscal, seção 22.4.6).

  **ID_Retorno_Anterior**                *referência (Mov_Esocial_Retorno,      O totalizador que este substitui.
                                         autorreferência, opcional)*

  **Existencia_Informacao**              *enumeração {ha_valores,               indExistInfo, valores 1 a 3 (S-5011 e S-5012).
                                         movimento_sem_valores, sem_movimento}*

  **Valor_Desconto_Segurado**            *número, opcional*                     vrDescCP do S-5011 (infoCPSeg): o total
                                                                                descontado dos segurados. Base de comparação
                                                                                com o INSS retido que a folha provisionou.

  **Valor_Contribuicao_Segurado**        *número, opcional*                     vrCpSeg do S-5011: a contribuição do segurado
                                                                                calculada pelo eSocial.

  **Valor_Provisao_Folha**               *número, opcional*                     A provisão de INSS (S-5011) ou de IRRF retido
                                                                                (S-5012) que as folhas contabilizadas da
                                                                                competência lançaram, somada na matriz.
                                                                                Calculada na conciliação, e não digitada.

  **Valor_Diferenca_Provisao**           *número, opcional*                     O valor oficial menos Valor_Provisao_Folha,
                                                                                pela base que a P-31 definir. Diferente de
                                                                                zero (acima da tolerância) marca o retorno
                                                                                como divergente.

  **ID_Lote_Diferenca**                  *referência (Mov_Lote_Lancamento,      O lançamento que levou a diferença para a
                                         opcional)*                             conta de diferença (Contabilidade & Fiscal, seção 22.4.2).

  **Origem_Recebimento**                 *enumeração {consulta_webservice,      Como o totalizador chegou ao ERP.
                                         importacao_manual}*

  **Data_Hora_Recebimento**              *data/hora*                            ---

  **Xml_Retorno**                        *texto*                                O totalizador como recebido, com as bases de
                                                                                remuneração por lotação e categoria.

  **Situacao_Conciliacao**               *enumeração {nao_conferido, conferido, Resultado da comparação com o que a folha
                                         divergente}*                           apurou (Contabilidade & Fiscal, seção 22.6).

  **Data_Hora_Conciliacao**              *data/hora, opcional*                  ---
  -------------------------------------- -------------------------------------- ----------------------------------------------

Mov_Esocial_Retorno_Cr

Nova na revisão 18 (Bloco 5). Um valor por código de receita de um totalizador. O S-5011 e o
S-5501 trazem o nível do contribuinte (infoCRContrib) e, no S-5011, o do
estabelecimento (infoCREstab); o S-5012 traz o IRRF mensal (infoCRMen) e
o diário (infoCRDia).

*Vigência: não.*

  ---------------------------- -------------------------------------- ----------------------------------------------
  **Campo**                    **Tipo lógico**                        **Descrição / regra**

  **ID_Retorno_Cr**            *identificador*                        ---

  **ID_Retorno_Esocial**       *referência (Mov_Esocial_Retorno)*     ---

  **Nivel**                    *enumeração {contribuinte,             infoCRContrib ou infoCREstab.
                               estabelecimento}*

  **ID_Filial**                *referência (Cad_Filial, opcional)*    O estabelecimento (ideEstab) quando Nivel =
                                                                      estabelecimento.

  **Grupo**                    *enumeração                            S-5011: contribuição; S-5012: IRRF; S-5501
                               {contribuicao_previdenciaria, irrf}*   traz os dois (infoCRContrib e infoCRIRRF).

  **Periodicidade**            *enumeração {mensal, diaria}*          Mensal (CRMen) ou diária (CRDia, residente no
                                                                      exterior).

  **Dia_Apuracao**             *número, opcional*                     perApurDia do IRRF diário.

  **Competencia_Referencia**   *competência, opcional*                perRef do S-5501.

  **Codigo_Receita**           *código (6)*                           tpCR, CRMen ou CRDia. Validado contra
                                                                      Cad_Codigo_Receita na data do fato.

  **Valor_Cr**                 *número*                               vrCR, vrCRMen ou vrCRDia: o valor do código de
                                                                      receita.

  **Valor_Cr_Suspenso**        *número, opcional*                     vrCRSusp ou vrSuspCR: a parte com
                                                                      exigibilidade suspensa.

  **ID_Titulo**                *referência (Mov_Titulo, opcional)*    O título a pagar que nasceu desta linha (Contabilidade & Fiscal, seção 22.4). Só as linhas de nível contribuinte com
                                                                      valor maior que zero geram título; o nível
                                                                      estabelecimento serve à conciliação.

  **ID_Lote_Reversao**         *referência (Mov_Lote_Lancamento,      O lançamento que baixou a provisão da folha
                               opcional)*                             contra o contas a pagar (Origem_Tipo =
                                                                      reversao_provisao_encargos_folha).

  **ID_Lote_Estorno**          *referência (Mov_Lote_Lancamento,      O lançamento que estornou a reversão quando o
                               opcional)*                             totalizador foi substituído (Origem_Tipo =
                                                                      estorno_reversao_provisao_encargos_folha,
                                                                      Contabilidade & Fiscal, seção 22.4.6).

  **Tratamento_Retificacao**   *enumeração {integral, complementar,   Como a linha foi tratada quando substituiu
                               sem_alteracao, pagamento_a_maior},     outra: integral (estorno e valor correto
                               opcional*                              integral, Contabilidade & Fiscal, seção 22.4.6), complementar (título só
                                                                      pela diferença, título anterior já pago),
                                                                      sem_alteracao (valor igual) ou
                                                                      pagamento_a_maior (valor menor depois do
                                                                      pagamento: registrado em
                                                                      Mov_Pagamento_A_Maior, Contabilidade & Fiscal, seção 22.5.2).
  ---------------------------- -------------------------------------- ----------------------------------------------

Mov_Esocial_Retorno_Base_Pis_Pasep

Nova na revisão 18 (Bloco 5). A base do PIS/Pasep sobre a folha (basesPisPasep do S-5011),
enviada quando o empregador optou por esse regime (indTribFolhaPisPasep
do S-1000 e do S-5011, em vigor desde janeiro/2025).

*Vigência: não.*

  ------------------------- -------------------------------------- ----------------------------------------------
  **Campo**                 **Tipo lógico**                        **Descrição / regra**

  **ID_Base_Pis_Pasep**     *identificador*                        ---

  **ID_Retorno_Esocial**    *referência (Mov_Esocial_Retorno)*     ---

  **ID_Filial**             *referência (Cad_Filial, opcional)*    O estabelecimento, quando o totalizador a
                                                                   informa por estabelecimento.

  **Valor_Base**            *número*                               vrBcPisPasep.

  **Valor_Base_Suspensa**   *número, opcional*                     vrBcPisPasepSusp.
  ------------------------- -------------------------------------- ----------------------------------------------


12\. Ficha do Colaborador

A \"ficha do colaborador\" que o Documento Analítico descrevia ---
exames, vacinas, afastamentos, viagens e acidentes de trabalho --- não
vira cinco entidades separadas: segue o mesmo princípio genérico já
usado em Mov_Esocial_Evento (seção 10) e em outros motores transversais
deste dicionário (ex.: Mov_Estoque_Condicao). Um único evento de ficha,
tipificado por um catálogo próprio que já carrega o mapeamento ao código
eSocial e o atributo de envio imediato x aguarda fechamento ---
exatamente como o Documento Analítico especificava.

Cad_Rh_Tipo_Evento_Ficha

O catálogo de tipos de evento que podem compor a ficha do colaborador
--- exame, vacina, afastamento, viagem, acidente de trabalho, e qualquer
tipo futuro, sem nova tabela.

*Vigência: sim --- a política de um tipo de evento (ex.: se o envio é
imediato) pode mudar ao longo do tempo, sem afetar como eventos já
registrados no passado foram tratados.*

  ---------------------------- ---------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**        **Descrição / regra**

  **ID_Tipo_Evento**           *identificador*        ---

  **ID_Tipo_Evento_Versao**    *identificador da      Chave primária da versão (tabela física
                               versão*                Cad_Rh_Tipo_Evento_Ficha_Versao).
                                                      ID_Tipo_Evento é a identidade, única e
                                                      referenciada pelas outras tabelas; cada
                                                      versão guarda a sua janela de vigência
                                                      --- Fase 0, seção 2.

  **Nome**                     *texto*                Ex.: \"Exame Admissional\", \"Exame
                                                      Periódico\", \"Exame Demissional\"
                                                      (exemplo explicitado na revisão 5, mesmo
                                                      catálogo genérico, sem campo novo),
                                                      \"Vacina\", \"Afastamento por Doença\",
                                                      \"Viagem a Trabalho\", \"Acidente de
                                                      Trabalho\".

  **ID_Tipo_Evento_Esocial**   *referência            O evento eSocial correspondente (ex.:
                               (Cad_Classe_Sistema,   S-2220 para exame, S-2230 para
                               domínio =              afastamento, S-2210 para acidente de
                               tipo_evento_esocial,   trabalho) --- vazio para um tipo de
                               opcional)*             evento da ficha que não tem
                                                      correspondente estruturado no eSocial
                                                      (ex.: viagem a trabalho, mantida só para
                                                      controle interno).

  **Envio_Imediato**           *booleano*             O atributo citado no Documento
                                                      Analítico: verdadeiro quando este tipo
                                                      de evento deve ser enviado ao eSocial
                                                      assim que registrado (ex.: acidente de
                                                      trabalho, com prazo legal curto), falso
                                                      quando pode esperar o fechamento da
                                                      folha do período.

  **Vigencia_Inicio**          *data*                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                 Último dia em que esta versão vale
                                                      (inclusive). Sempre preenchida:
                                                      31/12/9999 quando o fim é indefinido
                                                      (versão vigente) --- convenção da Fase
                                                      0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*      Por que esta versão foi criada.
  ---------------------------- ---------------------- ----------------------------------------

Mov_Rh_Ficha_Evento

Um evento concreto da ficha de um colaborador --- uma ocorrência
específica de exame, vacina, afastamento, viagem ou acidente.

*Vigência: não --- evento; uma correção (ex.: data de retorno de
afastamento emendada) é um novo registro, nunca a edição do original.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Evento_Ficha** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | --- |
| **ID_Tipo_Evento** | *referência (Cad_Rh_Tipo_Evento_Ficha)* | --- |
| **Data_Evento** | *data* | --- |
| **Data_Fim** | *data, opcional* | Preenchido para eventos com duração (ex.: afastamento, viagem) --- vazio para um evento pontual (ex.: exame, vacina). |
| **Detalhe** | *texto, opcional* | Texto livre nesta revisão para o detalhamento específico de cada tipo (ex.: CID do afastamento, agente causador do acidente, lote da vacina) --- sem campos estruturados dedicados por tipo, ver Notas. |
| **ID_Evento_Esocial** | *referência (Mov_Esocial_Evento, opcional)* | Preenchido quando este evento da ficha gerou um envio ao eSocial (seção 10) --- vazio para um tipo sem correspondente estruturado (ex.: viagem a trabalho). |
| **Data_Inicio_Responsabilidade_Inss** | *data, opcional* | Adicionado nesta revisão (4), pedido pela verificação de legislação trabalhista: para afastamento longo (licença médica) ou acidente de trabalho, marca a partir de quando a responsabilidade deixa de ser da empresa (folha normal, tipicamente os primeiros 15 dias) e passa a ser do INSS (auxílio-doença, art. 60 §3º Lei 8.213/91) --- vazio para afastamento curto ou quando não aplicável. Conecta-se à estabilidade provisória pós-acidente (Mov_Rh_Estabilidade_Provisoria, seção 3, tipo acidentado, 12 meses após a alta, art. 118 Lei 8.213/91). |
| **Houve_Obito** | *booleano* | Adicionado nesta revisão (5), pedido por Alberto (\"verifique no caso de acidente de trabalho que gerou a morte e consequentemente levou ao desligamento\"): preenchido só para eventos de acidente de trabalho (ID_Tipo_Evento correspondente a Acidente de Trabalho/CAT) --- verdadeiro quando o acidente resultou em óbito do colaborador. Falso/vazio para os demais eventos da ficha. |
| **Data_Obito** | *data, opcional* | Preenchida só quando Houve_Obito=verdadeiro --- o campo indCatObito/dtObito da estrutura de CAT do eSocial (S-2210): a data do óbito, que pode ser diferente da data do acidente quando a morte não é imediata. |
| **Tipo_Cat** | *enumeração {original, reabertura, comunicacao_obito}, opcional* | Adicionado nesta revisão (5), pesquisado a pedido de Alberto (\"pode verificar se tem algo diferente no eSocial e na legislação\"): preenchido só para eventos de acidente de trabalho --- reproduz o tipo de CAT da estrutura do eSocial (S-2210). original: a primeira comunicação do acidente. reabertura: agravamento ou reinício de tratamento de um acidente já comunicado. comunicacao_obito: comunicação específica de óbito decorrente de um acidente já comunicado anteriormente --- o eSocial exige que este tipo referencie o evento de CAT original (ID_Evento_Ficha_Origem, abaixo), regra de validação equivalente à REGRA_EVENTO_POSTERIOR_CAT_OBITO do Manual de Orientação do eSocial, que impede comunicar óbito sem uma CAT original ou reabertura prévia. |
| **ID_Evento_Ficha_Origem** | *referência (Mov_Rh_Ficha_Evento, autorreferência, opcional)* | Preenchido só quando Tipo_Cat=reabertura ou comunicacao_obito --- aponta para a CAT original (Tipo_Cat=original) da mesma cadeia de acidente, mesmo princípio de autorreferência já usado em Mov_Esocial_Evento.ID_Evento_Retificado (seção 10) e em Cad_Vinculo_Emprego.ID_Gestor (seção 3). |
| **ID_Motivo_Afastamento_Esocial** | *referência (Cad_Classe_Sistema, domínio = motivo_afastamento_esocial, opcional)* | Adicionado na revisão 19 (NT 07/2026). codMotAfast, Tabela 18 do eSocial. Obrigatório quando o tipo do evento aponta para o S-2230. A ficha continua aceitando eventos sem motivo para os tipos que não vão ao eSocial. |
| **Mesma_Doenca_Afastamento_Anterior** | *booleano, opcional* | Adicionado na revisão 19 (NT 07/2026). infoMesmoMtv do S-2230: o afastamento decorre da mesma doença que gerou o afastamento anterior. Se Data_Evento é igual ou posterior a 26/10/2026, o campo é obrigatório e exclusivo quando o motivo é 01 ou 03 e existe, no mesmo vínculo, outro afastamento anterior com o mesmo motivo dentro de 60 dias; em qualquer outro caso, não é informado. A busca é feita na própria ficha: mesmo vínculo, mesmo motivo e Data_Evento do anterior até 60 dias antes do Data_Evento do novo, ou seja, os 60 dias contam do início do afastamento anterior ao início do novo (leitura B). O leiaute não diz de onde os 60 dias são contados; respostas de Alberto: em 14/10/2026 o início do afastamento é sempre obrigatório e vem do RH, e em 19/10/2026 os 60 dias contam "da data do início do afastamento que o RH deve incluir na base de dados" (revisão 12, D-N207, que encerra a P-38c). Vale para eventos de 26/10/2026 em diante. É declaração do RH: o sistema só cobra o preenchimento e acusa o excesso. |

*Revisão 10 --- campos alterados: Mesma_Doenca_Afastamento_Anterior.*

*Revisão 12 --- campos alterados: Mesma_Doenca_Afastamento_Anterior.*

*Nexo óbito por acidente de trabalho --- desligamento: quando o motivo
de desligamento do colaborador é óbito (Cad_Rh_Motivo_Desligamento,
seção 3) e a causa foi um acidente de trabalho,
Cad_Vinculo_Emprego.ID_Evento_Ficha_Origem_Obito (seção 3) aponta para o
Mov_Rh_Ficha_Evento com Houve_Obito=verdadeiro correspondente --- o
mesmo evento que, via Tipo_Cat=comunicacao_obito/ID_Evento_Ficha_Origem
acima, já está ligado à CAT original perante o eSocial. Dois tratamentos
legais adicionais ficam registrados aqui, sem campo estrutural novo,
pois derivam inteiramente da combinação já modelada (motivo=óbito + nexo
com acidente de trabalho): o IRRF sobre as verbas rescisórias de óbito
por acidente de trabalho segue tratamento tributário próprio (isenção
mais ampla que o óbito comum), e a estabilidade acidentária
(Mov_Rh_Estabilidade_Provisoria, tipo acidentado, seção 3) se extingue
no óbito em vez de se completar --- comportamento de aplicação sobre
entidades já existentes, não estrutura nova.*

*Classificação PCD/cotista: adicionado nesta revisão (4), pedido pela
verificação de legislação trabalhista (art. 93 Lei 8.213/91) --- não é
um campo estático no vínculo, porque um colaborador pode não ser PCD e
passar a ser por algum motivo específico, precisando de data de início.
Novo valor em Cad_Rh_Tipo_Evento_Ficha (\"Classificação PCD/Cotista\",
sem correspondente eSocial estruturado próprio além do S-2200):
Mov_Rh_Ficha_Evento.Detalhe registra o subtipo (pcd, reabilitado,
cotista, e --- quando PCD --- o tipo de deficiência: física, auditiva,
visual, mental, intelectual, múltipla), com laudo anexado via GED (seção
13, mesmo mecanismo já usado para exame/acidente). A classificação
vigente do colaborador é sempre uma CONSULTA sobre o evento mais recente
deste tipo, nunca um campo sobrescrito, mesmo princípio de nunca guardar
o que pode ser derivado já usado no resto do dicionário.*

*Ausência legal justificada: adicionado nesta revisão (4), pedido pela
verificação de legislação trabalhista (art. 473 CLT --- casamento,
óbito, doação de sangue, entre outras) --- novo valor em
Cad_Rh_Tipo_Evento_Ficha (\"Ausência Legal Justificada\"), com
comprovante anexado via GED (seção 13, mesmo mecanismo já usado em
exame/curso/acidente) e reflexo na apuração de ponto/folha (não gera
desconto nem perda de DSR --- comportamento de aplicação a documentar na
camada que consome este dicionário).*

*Documento de base do evento --- curso, treinamento, exame médico:
adicionado por comentário de Alberto (\"cursos, treinamentos poder
associar o documento de base\", e depois \"exames médicos também\").
Mesmo GED da Fase 0 (Cad_Documento/Cad_Documento_Vinculo, seção 11) já
reaproveitado em outros pontos deste módulo --- um Cad_Documento_Vinculo
com Modulo_Destino=\"rh\" e
Entidade_Relacionada_Tipo/ID_Entidade_Relacionada apontando para o
Mov_Rh_Ficha_Evento correspondente, sem campo novo em
Mov_Rh_Ficha_Evento. Vale para qualquer tipo do catálogo
(Cad_Rh_Tipo_Evento_Ficha) que tenha documento de base --- certificado
de curso/treinamento, laudo ou atestado de exame médico, entre outros
--- não só os dois exemplos citados por Alberto.*

13\. Condições de Risco e Segurança do Trabalho

Confirmado por Alberto, em resposta à pergunta sobre segurança do
trabalho e exames médicos no eSocial: exame médico (S-2220/PCMSO) e
acidente de trabalho (S-2210/CAT) já estavam cobertos pela Ficha do
Colaborador (seção 12). Mas Alberto foi além --- \"até a questão de
insalubridade, adicional noturno, periculosidade entre outros\" --- e
esclareceu como as condições de risco se aplicam: \"a questão de risco
está no cargo e também pode estar na área em que ele está atuando. São
condições que acabam se sobrepondo.\" Por isso insalubridade,
periculosidade e agentes ambientais (S-2240) não seguem o padrão de
evento pontual da Ficha do Colaborador --- são condições vigentes,
catalogadas por CARGO e por ÁREA, que se somam para um mesmo
colaborador.

Cad_Rh_Ambiente_Trabalho

Adicionado nesta revisão (4), pedido pela verificação do Manual de
Orientação do eSocial (S-1060/S-2240/S-2241): o AMBIENTE de trabalho ao
qual o colaborador é vinculado --- o eSocial exige essa hierarquia
ambiente→fator de risco→vínculo do trabalhador, distinta de vincular a
condição só ao cargo/área.

*Vigência: sim --- um ambiente pode ser redefinido/desativado ao longo
do tempo; a versão vigente na data do fato gerador é a usada para os
eventos do eSocial.*

  ------------------------ ----------------- ----------------------------------------
  **Campo**                **Tipo lógico**   **Descrição / regra**

  **ID_Ambiente**          *identificador*   ---

  **ID_Ambiente_Versao**   *identificador da Chave primária da versão (tabela física
                           versão*           Cad_Rh_Ambiente_Trabalho_Versao).
                                             ID_Ambiente é a identidade, única e
                                             referenciada pelas outras tabelas; cada
                                             versão guarda a sua janela de vigência
                                             --- Fase 0, seção 2.

  **Codigo**               *código (até 30)* ---

  **Descricao**            *texto*           Ex.: \"Linha de Produção --- Setor A\",
                                             \"Laboratório\", \"Canteiro de Obra\".

  **Vigencia_Inicio**      *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*            Último dia em que esta versão vale
                                             (inclusive). Sempre preenchida:
                                             31/12/9999 quando o fim é indefinido
                                             (versão vigente) --- convenção da Fase
                                             0, seção 2.

  **Motivo_Vigencia**      *texto, opcional* Por que esta versão foi criada.
  ------------------------ ----------------- ----------------------------------------

Cad_Rh_Condicao_Risco

O catálogo de condições de risco/segurança do trabalho --- graus de
insalubridade, periculosidade e agentes ambientais nocivos ---
reaproveitável por cargo e por área, sem redefinir a condição a cada
vínculo.

*Vigência: sim --- o percentual ou a verba associada a uma condição pode
mudar por lei, nova versão nunca sobrescrita, preservando o cálculo de
folhas já fechadas.*

  ------------------------ ---------------------------- ----------------------------------------
  **Campo**                **Tipo lógico**              **Descrição / regra**

  **ID_Condicao**          *identificador*              ---

  **ID_Condicao_Versao**   *identificador da versão*    Chave primária da versão (tabela física
                                                        Cad_Rh_Condicao_Risco_Versao).
                                                        ID_Condicao é a identidade, única e
                                                        referenciada pelas outras tabelas; cada
                                                        versão guarda a sua janela de vigência
                                                        --- Fase 0, seção 2.

  **Nome**                 *texto*                      Ex.: \"Insalubridade Grau Médio\",
                                                        \"Periculosidade\", \"Agente Nocivo ---
                                                        Ruído\".

  **Tipo**                 *enumeração {insalubridade,  ---
                           periculosidade,              
                           agente_ambiental}*           

  **Percentual**           *número, opcional*           O percentual do adicional, quando
                                                        aplicável (ex.: 20% para insalubridade
                                                        grau médio, 30% para periculosidade) ---
                                                        parametrizável, não hardcoded, porque a
                                                        base de cálculo e os percentuais mudam
                                                        por lei/norma regulamentadora, não por
                                                        decisão da Mlegate.

  **ID_Codigo_Esocial**    *referência                  O código de agente nocivo/risco da
                           (Cad_Classe_Sistema, domínio tabela oficial do eSocial correspondente
                           = tipo_evento_esocial,       a esta condição, quando existir ---
                           opcional)*                   domínio aberto, mesmo padrão já usado
                                                        para os demais códigos oficiais deste
                                                        módulo.

  **ID_Verba**             *referência (Cad_Rh_Verba,   A verba que paga o adicional
                           opcional)*                   correspondente a esta condição ---
                                                        quando preenchida, a condição vigente
                                                        para um vínculo (por cargo ou área)
                                                        dispara automaticamente o
                                                        Mov_Rh_Folha_Item dessa verba na
                                                        apuração de folha (seção 5), sem
                                                        lançamento manual.

  **ID_Ambiente**          *referência                  Adicionado nesta revisão (4): quando
                           (Cad_Rh_Ambiente_Trabalho,   preenchida, esta condição está
                           opcional)*                   catalogada especificamente para um
                                                        ambiente de trabalho --- reproduzindo a
                                                        hierarquia ambiente→fator de risco que o
                                                        eSocial (S-2240/S-2241) exige,
                                                        complementar (não substituta) ao vínculo
                                                        por cargo/área abaixo.

  **Vigencia_Inicio**      *data*                       Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*                       Último dia em que esta versão vale
                                                        (inclusive). Sempre preenchida:
                                                        31/12/9999 quando o fim é indefinido
                                                        (versão vigente) --- convenção da Fase
                                                        0, seção 2.

  **Motivo_Vigencia**      *texto, opcional*            Por que esta versão foi criada.
  ------------------------ ---------------------------- ----------------------------------------

Mov_Rh_Vinculo_Ambiente

Adicionado nesta revisão (4): a vigência da associação de um vínculo a
um ambiente de trabalho --- o terceiro eixo da exposição combinada, ao
lado de cargo e área.

*Vigência: não --- é o próprio registro de vigência
(Data_Inicio/Data_Fim), mesmo padrão de
Mov_Rh_Cargo_Condicao_Risco/Mov_Rh_Area_Condicao_Risco, abaixo.*

  ----------------- ----------------------------- ----------------------------------------
  **Campo**         **Tipo lógico**               **Descrição / regra**

  **ID_Registro**   *identificador*               ---

  **ID_Vinculo**    *referência                   ---
                    (Cad_Vinculo_Emprego)*        

  **ID_Ambiente**   *referência                   ---
                    (Cad_Rh_Ambiente_Trabalho)*   

  **Data_Inicio**   *data*                        ---

  **Data_Fim**      *data, opcional*              Vazia enquanto o vínculo está no
                                                  ambiente.
  ----------------- ----------------------------- ----------------------------------------

Mov_Rh_Cargo_Condicao_Risco

A vigência de uma condição de risco para um CARGO (CBO) --- risco é
definido regulatoriamente pelo código oficial da CBO, não pelo cargo
interno da empresa, por isso a referência aqui permanece direta a
Cad_Classe_Sistema (domínio cbo), sem mudança estrutural nesta revisão;
a ponte entre o cargo interno e o CBO passa a ser Cad_Rh_Cargo.ID_Cbo
(seção 2, revisão 6).

*Vigência: não --- é o próprio registro de vigência
(Data_Inicio/Data_Fim); um novo laudo que altera a condição do cargo
fecha este registro (Data_Fim) e abre um novo, nunca editando o período
já vigorado.*

  ----------------- -------------------------- ----------------------------------------
  **Campo**         **Tipo lógico**            **Descrição / regra**

  **ID_Registro**   *identificador*            ---

  **ID_Cbo**        *referência                ---
                    (Cad_Classe_Sistema,       
                    domínio = cbo)*            

  **ID_Condicao**   *referência                ---
                    (Cad_Rh_Condicao_Risco)*   

  **Data_Inicio**   *data*                     ---

  **Data_Fim**      *data, opcional*           Vazia enquanto a condição está vigente
                                               para este cargo.
  ----------------- -------------------------- ----------------------------------------

Mov_Rh_Area_Condicao_Risco

A vigência de uma condição de risco para uma ÁREA/departamento ---
reaproveita a mesma dimensão já usada em
Cad_Participante_Historico_Departamento (Fase 0).

*Vigência: não --- mesmo princípio de Mov_Rh_Cargo_Condicao_Risco acima,
agora por área.*

  --------------------- ------------------------------- ----------------------------------------
  **Campo**             **Tipo lógico**                 **Descrição / regra**

  **ID_Registro**       *identificador*                 ---

  **ID_Departamento**   *referência                     ---
                        (Cad_Dimensao_Contabil_Valor,   
                        dimensão = Departamento)*       

  **ID_Condicao**       *referência                     ---
                        (Cad_Rh_Condicao_Risco)*        

  **Data_Inicio**       *data*                          ---

  **Data_Fim**          *data, opcional*                Vazia enquanto a condição está vigente
                                                        para esta área.
  --------------------- ------------------------------- ----------------------------------------

*Comportamento de aplicação --- exposição combinada: a exposição real de
um vínculo a condições de risco, numa data de referência, NUNCA é
armazenada no vínculo --- é sempre uma consulta que UNE (não escolhe uma
ou outra) as condições vigentes do cargo atual (cruzando
Cad_Participante_Historico_Cargo.ID_Cargo, já escopado por vínculo desde
o patch Fase 0 revisão 27, com Cad_Rh_Cargo.ID_Cbo --- seção 2, revisão
6 --- e daí com Mov_Rh_Cargo_Condicao_Risco), as condições vigentes da
área atual (cruzando
Cad_Participante_Historico_Departamento.ID_Departamento com
Mov_Rh_Area_Condicao_Risco) e, adicionado nesta revisão (4), as
condições catalogadas para o ambiente vigente (cruzando
Mov_Rh_Vinculo_Ambiente com Cad_Rh_Condicao_Risco.ID_Ambiente) ---
exatamente como Alberto descreveu, condições que se sobrepõem, agora
reproduzindo também a hierarquia ambiente→fator de risco→vínculo que o
eSocial exige. Essa consulta combinada alimenta duas coisas: o evento
eSocial S-2240 (Mov_Esocial_Evento, Origem_Tipo=condicao_risco, seção
10) e, quando cada Cad_Rh_Condicao_Risco tem uma ID_Verba associada, o
disparo automático das verbas de insalubridade/periculosidade na
apuração de folha (seção 5) --- sem lançamento manual e sem recadastrar
a condição a cada colaborador do mesmo cargo ou área.*

14\. Acesso e Restrição por Usuário

Dados deste módulo são particularmente sensíveis --- salário
(Cad_Participante_Historico_Salario, Fase 0), saúde
(Mov_Rh_Ficha_Evento, seção 12) --- por isso o mesmo padrão de escopo
por filial/departamento já usado em Estoque (Cad_Usuario_Escopo) é
reaplicado aqui, além do nível módulo+ação já coberto por Cad_Permissao
(Fase 0). A visão do gestor sobre o banco de horas de sua equipe (seção
7) é um recorte à parte, por hierarquia (Cad_Vinculo_Emprego.ID_Gestor),
não por filial/departamento --- as duas formas de recorte convivem, cada
uma resolvendo um tipo de acesso diferente.

*Cad_Rh_Escopo_Usuario --- APOSENTADA na revisão 16 (Bloco 3).
Restringia o recorte de dado de Folha & RH por filial, departamento e
área de RH, mas não tinha vigência. Foi substituída por
Cad_Usuario_Escopo (Fase 0, seção 13), com Modulo = folha_rh: ID_Filial,
ID_Departamento e ID_Area_Rh viram uma linha por valor preenchido (tipos
filial, departamento e area_rh), e a vigência que faltava passa a
existir. O escopo continua distinto da AÇÃO, que é papel de
Cad_Permissao (Fase 0).*

*Controle de campo sensível (ex.: só RH vê salário; só um gestor de
saúde ocupacional vê o Detalhe de um evento de afastamento/acidente)
fica fora do escopo deste dicionário lógico --- mesma filosofia geral do
projeto: a estrutura registra o dado, a camada de aplicação decide quem
enxerga qual campo, dentro do nível módulo+ação que Cad_Permissao já
concede.*

Visibilidade da equipe de folha sobre pagamentos não processados:
adicionado nesta revisão (5), pedido por Alberto (\"a equipe de folha de
pagamento tem que ter acesso dos pagamentos de colaboradores que não
foram processados por algum motivo\"). Nenhum campo novo nasce aqui ---
nem em Folha & RH, nem em Contas a Pagar/Receber, nem em Tesouraria:
\"pagamento não processado\" nunca é um status armazenado, é sempre uma
CONSULTA derivada cruzando três pontos já modelados nesta consolidação
(mesmo princípio de nunca guardar o que pode ser derivado usado em todo
o dicionário): (1) o Mov_Titulo com Origem_Tipo=folha_pagamento (Contas
a Pagar/Receber) ligado à Mov_Rh_Folha_Apuracao/Mov_Rh_Folha_Item que o
originou (ID_Origem, seção 21); (2) se esse título tem saldo em aberto
além da Data_Vencimento (título vencido e não baixado --- o caso mais
simples de \"não processado\"); e (3) se o item de remessa bancária
correspondente (Mov_Remessa_Bancaria_Item, Tesouraria) voltou com status
de rejeição/devolução (ex.: conta encerrada, chave Pix inválida, CPF
divergente) mesmo com o título ainda dentro do prazo --- o caso em que o
pagamento foi de fato tentado, mas não se concretizou. Um usuário de RH
dentro do escopo de Cad_Usuario_Escopo (acima) enxerga essa consulta
filtrada aos vínculos da sua filial/departamento, cruzando ID_Vinculo
(via ID_Origem da apuração) com o mesmo recorte já usado para os demais
dados sensíveis deste módulo --- sem precisar de permissão direta sobre
Contas a Pagar/Receber ou Tesouraria, que continuam com seu próprio
controle de acesso modular (Cad_Permissao, Fase 0) para as demais
funções desses módulos (ex.: RH não passa a poder criar ou baixar
títulos de outra origem, como nota fiscal de fornecedor).

15\. Compliance --- Transparência Salarial e Igualdade (Lei 14.611/2023)

Adicionado nesta revisão (4), pedido pela verificação de compliance com
a Lei nº 14.611/2023 (Lei de Igualdade Salarial e de Critérios
Remuneratórios entre Mulheres e Homens) e o Decreto 11.795/2023:
empresas com 100+ empregados devem enviar semestralmente, pelo Portal
Emprega Brasil, um relatório de transparência salarial comparando
remuneração por sexo, raça/etnia, nacionalidade e faixa etária, a
proporção em cargos de liderança, e um questionário qualitativo
(critérios de promoção, políticas de incentivo) --- com plano de ação
quando houver desigualdade. Os dados transacionais que sustentam o
relatório já estão cobertos por este dicionário --- sexo administrativo
e cor/raça autodeclarada (Cad_Participante, Fase 0), indicador de nível
de liderança no cargo (Cad_Rh_Cargo.Nivel_Lideranca, seção 2 --- migrado
nesta revisão 6 de Cad_Participante_Historico_Cargo, onde vivia como
campo solto desde a revisão 29, para o novo cadastro de cargo da
empresa, referenciado por Cad_Participante_Historico_Cargo.ID_Cargo) e a
taxonomia de categoria remuneratória
(Cad_Rh_Verba.ID_Categoria_Remuneratoria, seção 5) --- mas o questionário
qualitativo e o plano de ação de mitigação não são dados de folha;
ganham entidades leves próprias, fora do motor de cálculo.

Cad_Rh_Declaracao_Transparencia_Salarial

O questionário qualitativo declarado a cada ciclo semestral --- plano de
cargos e salários, políticas de incentivo, critérios de promoção ---
anexado como resposta estruturada mínima, sem replicar o layout exato do
Portal Emprega Brasil (que muda por instrução normativa, fora do escopo
deste dicionário lógico).

*Vigência: sim --- cada semestre gera uma nova declaração, nunca a
edição de uma já enviada.*

  ---------------------------------- ----------------- -----------------------------------------------
  **Campo**                          **Tipo lógico**   **Descrição / regra**

  **ID_Declaracao**                  *identificador*   ---

  **ID_Declaracao_Versao**           *identificador da Chave primária da versão (tabela física
                                     versão*           Cad_Rh_Declaracao_Transparencia_Salarial_Versao).
                                                       ID_Declaracao é a identidade, única e
                                                       referenciada pelas outras tabelas; cada versão
                                                       guarda a sua janela de vigência --- Fase 0,
                                                       seção 2.

  **ID_Empresa**                     *referência       ---
                                     (Cad_Empresa)*    

  **Competencia_Semestre**           *texto*           Ex.: \"2026-1\", \"2026-2\".

  **Possui_Plano_Cargos_Salarios**   *booleano*        ---

  **Criterios_Promocao**             *texto*           Texto livre, respondido pela empresa a cada
                                                       ciclo.

  **Data_Envio**                     *data, opcional*  ---

  **Vigencia_Inicio**                *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                   *data*            Último dia em que esta versão vale (inclusive).
                                                       Sempre preenchida: 31/12/9999 quando o fim é
                                                       indefinido (versão vigente) --- convenção da
                                                       Fase 0, seção 2.

  **Motivo_Vigencia**                *texto, opcional* Por que esta versão foi criada.
  ---------------------------------- ----------------- -----------------------------------------------

Cad_Rh_Plano_Acao_Equidade

O plano de ação de mitigação de desigualdade salarial, exigido quando o
relatório aponta disparidade --- metas e prazos declarados pela empresa.

*Vigência: sim --- uma meta pode ter seu prazo/status atualizado; nova
versão nunca sobrescrita, preservando o histórico do que foi declarado a
cada ciclo.*

  --------------------- -------------------------------------------- ----------------------------------------
  **Campo**             **Tipo lógico**                              **Descrição / regra**

  **ID_Plano**          *identificador*                              ---

  **ID_Declaracao**     *referência                                  O ciclo semestral que originou a
                        (Cad_Rh_Declaracao_Transparencia_Salarial)*  necessidade do plano.

  **Descricao_Meta**    *texto*                                      ---

  **Data_Prazo**        *data*                                       ---

  **Status**            *enumeração {em_andamento, concluido,        ---
                        atrasado}*                                   

  **Vigencia_Inicio**   *data*                                       Primeiro dia em que esta versão vale.

  **Vigencia_Fim**      *data*                                       Último dia em que esta versão vale
                                                                     (inclusive). Sempre preenchida:
                                                                     31/12/9999 quando o fim é indefinido
                                                                     (versão vigente) --- convenção da Fase
                                                                     0, seção 2.

  **Motivo_Vigencia**   *texto, opcional*                            Por que esta versão foi criada.
  --------------------- -------------------------------------------- ----------------------------------------

16\. Categoria Sindical, Dissídio Coletivo e Salário Mínimo

Nova seção nesta revisão (9), pedida por Alberto: \"esta faltando    a
parte de discidio coletivo, que é o reajuste coletivo de salario    de
recuperação salarial\". Verificado que não existia, até esta revi   são,
nenhuma estrutura de sindicato/categoria sindical/convenção colet   iva
neste dicionário --- só menções soltas em prosa (prazo de banco d   e
horas, elegibilidade de PLR), sem nenhuma entidade de reajuste em    massa
por categoria/data-base.

Cad_Rh_Categoria_Sindical

O sindicato/categoria sindical que rege um grupo de vínculos ---
Alberto: \"a empresa normalmente tem um sindicato principal que g   ere a
maioria dos contratos da empresa, mas pode ter um grupo de
colaboradores, pela função pode ter um outro sindicato\". Cadastr   o de
referência, não uma tabela de movimentação.

*Vigência: sim (desde a revisão 14) --- o sindicato representante    muda
por decisão de enquadramento, e uma convenção antiga precisa cont   inuar
apontando para o sindicato da época.*

  ---------------------------------- ----------------- -------------------------------------------
  **Campo**                          **Tipo lógico**   **Descrição / regra**

  **ID_Categoria_Sindical**          *identificador*   ---

  **ID_Categoria_Sindical_Versao**   *identificador da Chave primária da versão (tabela física
                                     versão*           Cad_Rh_Categoria_Sindical_Versao).
                                                       ID_Categoria_Sindical é a identidade,
                                                       única e referenciada pelas outras
                                                       tabelas; cada versão guarda a sua janela
                                                       de vigência --- Fase 0, seção 2.

  **ID_Empresa**                     *referência       ---
                                     (Cad_Empresa)*    

  **Nome**                           *texto*           Ex.: \"Sindicato dos Empregados no
                                                       Comércio de São Paulo\".

  **Sindicato_Nome**                 *texto*           Razão social do sindicato.

  **Sindicato_Cnpj**                 *código (14),     ---
                                     opcional --- CNPJ 
                                     alfanumérico*     

  **Data_Base**                      *data*            O mês/dia de data-base da categoria ---
                                                       quando o dissídio/convenção anual
                                                       normalmente se renova.

  **Vigencia_Inicio**                *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                   *data*            Último dia em que esta versão vale
                                                       (inclusive). Sempre preenchida:
                                                       31/12/9999 quando o fim é indefinido
                                                       (versão vigente) --- convenção da Fase
                                                       0, seção 2.

  **Motivo_Vigencia**                *texto, opcional* Por que esta versão foi criada.
  ---------------------------------- ----------------- ----------------------------------------

*Enquadramento sindical de um vínculo --- comportamento de aplicação,
mesmo princípio \"mais específico vence o mais genérico\" já usado no
Motor de Regras (Fase 0, seção 8): sempre DERIVADO, nunca um campo solto
no vínculo. Primeiro verifica o cargo ATUAL do vínculo
(Cad_Rh_Cargo.ID_Categoria_Sindical, seção 2) --- se preenchido,
prevalece; senão, cai para o padrão da filial ATUAL do vínculo
(Cad_Filial.ID_Categoria_Sindical_Padrao, Fase 0). Explica por que uma
filial em São Paulo e outra no Rio de Janeiro podem ter dissídios
diferentes (sindicato de base territorial distinta) sem exigir nenhum
campo em Cad_Vinculo_Emprego.*

Cad_Rh_Reajuste_Coletivo

O cabeçalho de uma ocorrência de reajuste coletivo de salário ---
convenção coletiva, acordo coletivo ou dissídio propriamente dito
(quando a negociação vai à Justiça do Trabalho); os três têm o mesmo
efeito estrutural sobre a folha, distinguidos só por Tipo_Instrumento.

*Vigência: não --- cada negociação é uma ocorrência própria, datada; uma
renegociação nasce como uma nova linha, nunca a edição de uma já
aplicada.*

  --------------------------- ------------------------------ ----------------------------------------
  **Campo**                   **Tipo lógico**                **Descrição / regra**

  **ID_Reajuste_Coletivo**    *identificador*                ---

  **ID_Categoria_Sindical**   *referência                    A categoria (logo, o escopo de
                              (Cad_Rh_Categoria_Sindical)*   filial/cargo) atingida por este
                                                             reajuste.

  **Data_Base**               *data*                         A data-base efetiva deste reajuste
                                                             específico.

  **Tipo_Instrumento**        *enumeração                    ---
                              {convencao_coletiva,           
                              acordo_coletivo,               
                              dissidio_coletivo}*            

  **ID_Documento**            *referência (Cad_Documento,    O instrumento assinado (CCT/ACT) ou a
                              Fase 0, opcional)*             sentença normativa do dissídio, anexado
                                                             via GED. Corrigido na revisão 16:
                                                             apontava para Cad_Documento_Vinculo, que
                                                             é a ligação, e não o documento; passa a
                                                             apontar para Cad_Documento, como os
                                                             demais campos de documento do
                                                             dicionário.
  --------------------------- ------------------------------ ----------------------------------------

Cad_Rh_Reajuste_Coletivo_Faixa

O detalhe do reajuste --- permite um percentual único (uma única faixa,
sem limites) ou escalonado por faixa salarial, confirmado por Alberto:
\"existem momento que tem definições especificas, por faixas salárias\".

*Vigência: não --- detalhe do cabeçalho acima, mesma vida útil.*

  -------------------------- ----------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**               **Descrição / regra**

  **ID_Faixa**               *identificador*               Adicionado na revisão 14 (chave primária
                                                           declarada).

  **ID_Reajuste_Coletivo**   *referência                   ---
                             (Cad_Rh_Reajuste_Coletivo)*   

  **Valor_Salario_De**       *número, opcional*            Vazio = sem piso da faixa.

  **Valor_Salario_Ate**      *número, opcional*            Vazio = sem teto da faixa --- junto com
                                                           Valor_Salario_De também vazio, cobre o
                                                           caso de percentual único para toda a
                                                           categoria.

  **Percentual**             *número*                      O percentual de reajuste aplicável aos
                                                           salários dentro desta faixa.
  -------------------------- ----------------------------- ----------------------------------------

*Aplicação em massa --- comportamento de aplicação: ao confirmar um
Cad_Rh_Reajuste_Coletivo, o sistema encontra todos os vínculos ATIVOS
cuja categoria sindical derivada (acima) é a deste reajuste; para cada
um, localiza a Cad_Rh_Reajuste_Coletivo_Faixa cujo intervalo
\[Valor_Salario_De, Valor_Salario_Ate\] contém o Valor_Salario atual do
vínculo (ou a faixa sem limites, quando o reajuste é único), aplica o
Percentual sobre esse valor, e insere uma nova linha em
Cad_Participante_Historico_Salario (Fase 0) com
Origem_Alteracao=reajuste_coletivo --- nunca sobrescrevendo o valor
anterior, mesmo padrão de vigência já usado em toda aquela entidade.
Segundo efeito, adicionado nesta revisão (11), no MESMO evento de
confirmação: para cada Cad_Rh_Tabela_Salarial_Step vigente (seção 19)
cujo Cad_Rh_Cargo --- via ID_Grupo_Tabela_Salarial, seção 19 --- tenha a
categoria sindical derivada (cargo, senão filial, mesma regra de
resolução acima) igual à do reajuste, nasce uma nova linha de vigência
do step com o Valor_Step reajustado pelo MESMO percentual da faixa
aplicada aos salários individuais --- nova versão do step, mesmo padrão
de vigência já descrito para Cad_Rh_Tabela_Salarial_Step (seção 19); o
campo Data_Vigencia_Fim que esta revisão acrescenta, com fechamento
automático da linha anterior, é específico do catálogo
Cad_Rh_Tabela_Salarial (seção 19), não do Step. A verificação automática
de piso de salário mínimo (Cad_Rh_Salario_Minimo, acima) passa a valer
também para esses novos Valor_Step, mesma exceção já usada (estágio
fora, aprendiz proporcional);
Cad_Participante_Historico_Salario.Justificativa_Fora_Tabela (Fase 0,
seção 19) continua cobrindo divergência entre salário individual e o
novo Valor_Step.*

Cad_Rh_Salario_Minimo

O piso de salário mínimo vigente --- nacional ou estadual --- pedido por
Alberto: \"ninguem pode receber menos que o salario minimo, exceto menor
aprendiz e estagiario\". Mecanismo deliberadamente INDEPENDENTE do
dissídio coletivo, confirmado por Alberto: \"quando tem aumento no
minimo, se tem alguém abaixo do minimo tem que ser ajustado pelo minimo,
independente do dissidio da empresa\".

*Vigência: sim --- histórico de todos os valores de piso ao longo do
tempo, nunca sobrescrito; o piso aplicável a um vínculo, numa data, é
sempre o maior entre o nacional e o estadual da filial atual do vínculo
vigentes naquela data.*

  ----------------------- ----------------- ----------------------------------------
  **Campo**               **Tipo lógico**   **Descrição / regra**

  **ID_Salario_Minimo**   *identificador*   ---

  **Valor**               *número*          ---

  **Vigencia_Inicio**     *data*            --- Renomeado na revisão 14 (antes
                                            Data_Vigencia_Inicio).

  **ID_Estado**           *referência       Vazio = piso nacional. Preenchido = piso
                          (Cad_Estado,      estadual (Lei Complementar 103/2000),
                          opcional)*        que prevalece sobre o nacional quando
                                            maior --- confirmado por Alberto: \"sim,
                                            tem pisos regionais\".

  **Vigencia_Fim**        *data*            Último dia em que esta versão vale
                                            (inclusive). Sempre preenchida:
                                            31/12/9999 quando o fim é indefinido
                                            (versão vigente) --- convenção da Fase
                                            0, seção 2.

  **Motivo_Vigencia**     *texto, opcional* Por que esta versão foi criada.
  ----------------------- ----------------- ----------------------------------------

*Verificação automática de piso --- comportamento de aplicação: toda vez
que um novo Cad_Rh_Salario_Minimo entra em vigor, o sistema verifica
todos os vínculos ativos cujo Valor_Salario atual fica abaixo do piso
aplicável (o maior entre nacional e estadual da filial atual do vínculo)
e gera um ajuste automático --- nova linha em
Cad_Participante_Historico_Salario (Fase 0) com
Origem_Alteracao=ajuste_salario_minimo, elevando o salário exatamente ao
piso, independente de qualquer dissídio coletivo da empresa. Exceção:
Cad_Vinculo_Emprego.Tipo_Vinculo=estagio fica de fora --- o estágio não
é vínculo empregatício (Lei 11.788/2008), a bolsa pode ser zero.
Aprendiz permanece sujeito ao piso, mas de forma proporcional à jornada
reduzida --- já coberto pela categoria do trabalhador eSocial
(Cad_Vinculo_Emprego.ID_Categoria_Esocial) dentro de Tipo_Vinculo=clt,
sem campo novo aqui.*

Cad_Rh_Limite_Renda_Dependente_Irrf

Adicionado nesta revisão (10), da pesquisa sobre critérios legais de
dependente (Alberto: \"Não deixa pelo RH. E se existir algum parametro
diferente\... deixar isto como parametro\"): o teto de renda anual
PRÓPRIA de um ascendente (pai/mãe/avô/avó/bisavô/bisavó) para que ele
continue elegível como dependente de IRRF --- parâmetro nacional
publicado pela Receita Federal, mesmo padrão de Cad_Rh_Salario_Minimo
(não é por empresa, muda por ato normativo, tipicamente uma vez por
ano).

*Vigência: sim --- histórico de todos os valores ao longo do tempo,
nunca sobrescrito; o teto aplicável numa data é sempre o vigente naquela
data, preservando o cálculo de elegibilidade já feito para
anos-calendário anteriores.*

  --------------------- ----------------- ----------------------------------------
  **Campo**             **Tipo lógico**   **Descrição / regra**

  **ID_Limite**         *identificador*   ---

  **Valor**             *número*          O teto de renda anual do ascendente.

  **Vigencia_Inicio**   *data*            --- Renomeado na revisão 14 (antes
                                          Data_Vigencia_Inicio).

  **Vigencia_Fim**      *data*            Último dia em que esta versão vale
                                          (inclusive). Sempre preenchida:
                                          31/12/9999 quando o fim é indefinido
                                          (versão vigente) --- convenção da Fase
                                          0, seção 2.

  **Motivo_Vigencia**   *texto, opcional* Por que esta versão foi criada.
  --------------------- ----------------- ----------------------------------------

*Elegibilidade de IRRF de ascendente --- comportamento de aplicação:
fecha o ponto que Alberto recusou deixar como julgamento manual da RH.
Cad_Participante_Dependente.Renda_Anual_Declarada (Fase 0, campo
relevante só quando ID_Tipo_Dependente=pai_mae_avo_bisavo) é comparada
automaticamente contra o Cad_Rh_Limite_Renda_Dependente_Irrf vigente na
data --- acima do teto, Elegivel_Irrf (Fase 0) é marcado falso (nova
linha de vigência); dentro do teto e sem outro impeditivo, verdadeiro.
Mesmo mecanismo automático já usado para o corte por idade dos demais
tipos de dependente (Fase 0), sem julgamento manual da RH em nenhum dos
dois casos.*

Mov_Rh_Dependente_Comprovacao_Salario_Familia

Adicionado nesta revisão (10), da pesquisa sobre critérios legais de
dependente --- Alberto: \"incluir estas tabelas\": o Salário-Família
(Lei 8.213/91 art. 65) exige comprovação ANUAL para manter o direito ---
vacinação em dia (dependente até 6 anos) e frequência escolar
(dependente de 7 a 14 anos) ---, condição de PERMANÊNCIA que não existe
nem para IRRF nem para a pensão por morte do INSS.

*Vigência: não --- um registro por ano-referência/tipo de comprovação; a
entrega de um ano não substitui a de outro, cada Ano_Referencia exige a
sua.*

  ---------------------- ------------------------------- ----------------------------------------------
  **Campo**              **Tipo lógico**                 **Descrição / regra**

  **ID_Comprovacao**     *identificador*                 ---

  **ID_Dependente**      *referência                     ---
                         (Cad_Participante_Dependente,   
                         Fase 0)*                        

  **Ano_Referencia**     *número*                        ---

  **Tipo_Comprovacao**   *enumeração {vacinacao,         Vacinação relevante até 6 anos de idade do
                         frequencia_escolar}*            dependente naquele Ano_Referencia; frequência
                                                         escolar, dos 7 aos 14 --- a idade aplicável na
                                                         data é sempre derivada de
                                                         Cad_Participante_Dependente.Data_Nascimento,
                                                         nunca armazenada solta aqui.

  **Data_Entrega**       *data*                          ---
  ---------------------- ------------------------------- ----------------------------------------------

*Comprovação e elegibilidade do salário-família são estruturalmente
independentes: Cad_Participante_Dependente.Elegivel_Salario_Familia
(Fase 0) é determinado só por idade/incapacidade --- critério de
DIREITO, automático, mesmo mecanismo de Elegivel_Irrf, mas com corte em
14 anos em vez de 21/24. A ausência de um registro de comprovação do ano
corrente NÃO muda Elegivel_Salario_Familia --- é motivo distinto de
suspensão de PAGAMENTO (o INSS pode suspender/cobrar de volta o
benefício por falta de comprovação, mesmo com o dependente ainda dentro
da idade elegível); a estrutura só registra a entrega (ou a ausência
dela) da comprovação, a regra de suspensão em si é comportamento de
aplicação, mesmo critério já usado no dicionário para outras regras de
prazo (ex.: banco de horas, seção 7).*

17\. Benefícios

Nova seção nesta revisão (9), pedida por Alberto: \"esta faltando também
os beneficios como plano de saude, vale transporte, odontologia, vale
refeição\". Verificado que não existia, até esta revisão, nenhuma
estrutura de administração de benefícios --- \"Vale Transporte\", por
exemplo, só aparecia como exemplo de NOME de uma Cad_Rh_Verba de
desconto, sem cadastro de plano/adesão/dependentes cobertos;
Cad_Usuario_Escopo (restrição do tipo area_rh) (seção 14) já antecipava
um domínio \"beneficios\" desde a revisão 6, mas nunca havia sido
construído.

Cad_Rh_Beneficio

O catálogo de benefícios oferecidos pela empresa --- plano de saúde,
odontológico, vale-transporte, vale-refeição, vale-alimentação,
previdência privada, seguro de vida, entre outros.

*Vigência: sim --- mesmo padrão de Cad_Rh_Verba: um benefício pode ser
descontinuado sem apagar o histórico de adesões já feitas.*

  ------------------------------- --------------------------------------------- -------------------------------------------------------
  **Campo**                       **Tipo lógico**                               **Descrição / regra**

  **ID_Beneficio**                *identificador*                               ---

  **ID_Beneficio_Versao**         *identificador da versão*                     Chave primária da versão (tabela física
                                                                                Cad_Rh_Beneficio_Versao). ID_Beneficio é a identidade,
                                                                                única e referenciada pelas outras tabelas; cada versão
                                                                                guarda a sua janela de vigência --- Fase 0, seção 2.

  **ID_Empresa**                  *referência (Cad_Empresa)*                    ---

  **Nome**                        *texto*                                       ---

  **ID_Tipo_Beneficio**           *referência (Cad_Classe_Sistema, domínio =    Domínio aberto --- valores iniciais: plano_saude,
                                  tipo_beneficio_rh)*                           odontologico, vale_transporte, vale_refeicao,
                                                                                vale_alimentacao, previdencia_privada, seguro_vida,
                                                                                outro.

  **Modelo_Participacao**         *enumeração {fixo, percentual,                Adicionado a pedido de Alberto: fixo/percentual cobrem
                                  percentual_sobre_contribuicao_colaborador}*   a coparticipação comum (plano de saúde, odontológico);
                                                                                percentual_sobre_contribuicao_colaborador cobre o
                                                                                modelo de MATCHING --- \"o colaborador pode colocar um
                                                                                valor e a empresa participar com um percentual a mais
                                                                                sobre o valor contribuido pelo colaborador\" (ex.:
                                                                                previdência privada), onde o colaborador escolhe
                                                                                livremente quanto contribuir e a empresa contribui um
                                                                                percentual sobre esse valor, não um valor/percentual
                                                                                fixo de cadastro.

  **ID_Participante_Operadora**   *referência (Cad_Participante, opcional)*     A operadora do benefício (seguradora, plano de saúde,
                                                                                gestora de previdência) --- reaproveita o cadastro
                                                                                único
                                                                                (Cad_Participante/Cad_Participante_Classe=fornecedor,
                                                                                Fase 0), mesmo princípio \"cadastro único, papéis por
                                                                                contexto\" já usado em todo o dicionário, em vez de uma
                                                                                tabela própria de operadora.

  **Ativo**                       *booleano*                                    ---

  **Aceita_Dependente**           *booleano*                                    Adicionado nesta revisão (10), da pesquisa sobre
                                                                                critérios legais de dependente: falso para um benefício
                                                                                que cobre só o titular (ex.: seguro de vida em alguns
                                                                                contratos), sem checar
                                                                                Cad_Rh_Beneficio_Regra_Dependente abaixo. Verdadeiro
                                                                                para um benefício que aceita cobertura de dependente
                                                                                --- nesse caso, Cad_Rh_Beneficio_Regra_Dependente
                                                                                define QUAIS dependentes são aceitos.

  **Vigencia_Inicio**             *data*                                        Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                *data*                                        Último dia em que esta versão vale (inclusive). Sempre
                                                                                preenchida: 31/12/9999 quando o fim é indefinido
                                                                                (versão vigente) --- convenção da Fase 0, seção 2.

  **Motivo_Vigencia**             *texto, opcional*                             Por que esta versão foi criada.
  ------------------------------- --------------------------------------------- -------------------------------------------------------

Cad_Rh_Beneficio_Regra_Dependente

Adicionado nesta revisão (10), pedido por Alberto (\"e se existir algum
parametro diferente como disse que dependende da operadora de plano de
saúde deixar isto como parametro\"): quais tipos de dependente uma
operadora/benefício específico aceita cobrir --- LISTA POSITIVA, ao
contrário do padrão \"sem linha = sem restrição\" já usado em
Cad_Rh_Verba_Tipo_Vinculo/Cad_Rh_Verba_Filial (seção 5): aqui é o
oposto, porque cobertura de dependente por um benefício é sempre uma
concessão explícita do contrato da operadora, nunca uma restrição sobre
um padrão permissivo --- cada operadora define contratualmente quem
aceita (achado da pesquisa sobre critérios legais de dependente: plano
de saúde não segue o mesmo limite etário do IRPF, é sempre um caso à
parte).

*Vigência: não --- a presença da linha já é a concessão de cobertura
para aquele tipo de dependente; alterada substituindo/removendo a linha,
sem histórico de vigência formal nesta revisão.*

  ------------------------ -------------------------- ----------------------------------------
  **Campo**                **Tipo lógico**            **Descrição / regra**

  **ID_Beneficio**         *referência                Relevante só quando
                           (Cad_Rh_Beneficio) ---     Aceita_Dependente=verdadeiro, acima.
                           chave primária (composta)* 

  **ID_Tipo_Dependente**   *referência                ---
                           (Cad_Classe_Sistema,       
                           domínio =                  
                           tipo_dependente_esocial,   
                           Fase 0) --- chave primária 
                           (composta)*                

  **Idade_Limite_Anos**    *número, opcional*         Vazio = sem limite de idade próprio
                                                      deste benefício para este tipo de
                                                      dependente (ex.: cônjuge). Preenchido só
                                                      quando a operadora impõe um teto
                                                      contratual --- independente do limite de
                                                      idade do IRPF/salário-família, que não
                                                      se aplica aqui.
  ------------------------ -------------------------- ----------------------------------------

*Validação na adesão: comportamento de aplicação --- ao registrar
Mov_Rh_Beneficio_Adesao_Dependente (abaixo), o sistema só aceita um
dependente cujo Cad_Participante_Dependente.ID_Tipo_Dependente (Fase 0)
esteja cadastrado em Cad_Rh_Beneficio_Regra_Dependente para aquele
benefício e, quando Idade_Limite_Anos estiver preenchido, dentro do
limite --- parametrizável por benefício/operadora, sem regra hardcoded
neste dicionário.*

Cad_Rh_Beneficio_Valor

O histórico de valor/tabela de um benefício --- confirmado por Alberto:
\"pode ter uma participação do colaborador Fixa ou variavel e pode ser
estendida para dependentes, com percentuais e valores diferentes tanto
do cobrado pela operadora quanto da participação\".

*Vigência: sim --- vigência própria: uma renegociação de tabela com a
operadora, ou uma mudança de percentual de participação, nasce como nova
versão, preservando o valor vigente quando cada adesão/desconto já
apurado foi calculado.*

  ----------------------------------------- --------------------- ---------------------------------------------------------------
  **Campo**                                 **Tipo lógico**       **Descrição / regra**

  **ID_Beneficio_Valor**                    *identificador*       ---

  **ID_Beneficio**                          *referência           ---
                                            (Cad_Rh_Beneficio)*   

  **Tipo_Titularidade**                     *enumeração {titular, Confirmado por Alberto que titular e dependente têm
                                            dependente}*          valores/percentuais PRÓPRIOS, não um único valor estendido
                                                                  igualmente.

  **Faixa_Etaria**                          *texto, opcional*     Aplicável tipicamente a plano de saúde/odontológico, cujo custo
                                                                  da operadora varia por idade --- vazio para benefícios sem essa
                                                                  variação (ex.: vale-transporte).

  **Valor_Cobrado_Operadora**               *número*              O valor que a operadora cobra da empresa por esta
                                                                  titularidade/faixa.

  **Valor_Participacao_Colaborador**        *número, opcional*    Preenchido quando Cad_Rh_Beneficio.Modelo_Participacao=fixo.

  **Percentual_Participacao_Colaborador**   *número, opcional*    Preenchido quando Modelo_Participacao=percentual --- percentual
                                                                  sobre Valor_Cobrado_Operadora.

  **Percentual_Match_Empresa**              *número, opcional*    Preenchido só quando
                                                                  Modelo_Participacao=percentual_sobre_contribuicao_colaborador
                                                                  --- o percentual que a empresa contribui sobre o valor de
                                                                  contribuição livre do colaborador
                                                                  (Mov_Rh_Beneficio_Adesao_Contribuicao, abaixo).

  **Vigencia_Inicio**                       *data*                Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                          *data*                Último dia em que esta versão vale (inclusive). Sempre
                                                                  preenchida: 31/12/9999 quando o fim é indefinido (versão
                                                                  vigente) --- convenção da Fase 0, seção 2.

  **Motivo_Vigencia**                       *texto, opcional*     Por que esta versão foi criada.
  ----------------------------------------- --------------------- ---------------------------------------------------------------

Mov_Rh_Beneficio_Adesao

A adesão de um colaborador a um benefício --- mesmo padrão
catálogo+ocorrência já usado em todo o dicionário (ex.:
Cad_Rh_Reajuste_Coletivo, acima).

*Vigência: não --- o registro do período de adesão já é a própria
vigência (Data_Inicio/Data_Fim).*

  ------------------ ------------------------ ----------------------------------------
  **Campo**          **Tipo lógico**          **Descrição / regra**

  **ID_Adesao**      *identificador*          ---

  **ID_Vinculo**     *referência              ---
                     (Cad_Vinculo_Emprego)*   

  **ID_Beneficio**   *referência              ---
                     (Cad_Rh_Beneficio)*      

  **Data_Inicio**    *data*                   ---

  **Data_Fim**       *data, opcional*         Vazia enquanto a adesão está ativa.
  ------------------ ------------------------ ----------------------------------------

Mov_Rh_Beneficio_Adesao_Contribuicao

Relevante só para
Cad_Rh_Beneficio.Modelo_Participacao=percentual_sobre_contribuicao_colaborador
(ex.: previdência privada) --- o valor de contribuição que o colaborador
escolheu, podendo aumentar/reduzir livremente ao longo do tempo.

*Vigência: sim --- vigência própria dentro da adesão; a contribuição da
EMPRESA nunca é armazenada solta, é sempre DERIVADA
(Valor_Contribuicao_Colaborador ×
Cad_Rh_Beneficio_Valor.Percentual_Match_Empresa vigente), mesmo
princípio \"nunca armazenar o que pode ser derivado\" já usado em todo o
dicionário.*

  ------------------------------------ ---------------------------- ----------------------------------------
  **Campo**                            **Tipo lógico**              **Descrição / regra**

  **ID_Adesao_Contribuicao**           *identificador*              Adicionado na revisão 14 (chave primária
                                                                    declarada).

  **ID_Adesao**                        *referência                  ---
                                       (Mov_Rh_Beneficio_Adesao)*   

  **Valor_Contribuicao_Colaborador**   *número*                     ---

  **Vigencia_Inicio**                  *data*                       --- Renomeado na revisão 14 (antes
                                                                    Data_Vigencia_Inicio).

  **Vigencia_Fim**                     *data*                       Último dia em que esta versão vale
                                                                    (inclusive). Sempre preenchida:
                                                                    31/12/9999 quando o fim é indefinido
                                                                    (versão vigente) --- convenção da Fase
                                                                    0, seção 2.

  **Motivo_Vigencia**                  *texto, opcional*            Por que esta versão foi criada.
  ------------------------------------ ---------------------------- ----------------------------------------

Mov_Rh_Beneficio_Adesao_Dependente

Associação N:N entre uma adesão e os dependentes cobertos por ela ---
distinto de Cad_Participante_Dependente.Elegivel_Irrf (Fase 0), que é
sobre dedução de IRRF, não sobre cobertura de benefício.

*Vigência: não --- a presença da linha já é a cobertura; encerrada
removendo a linha (ou datando, se o padrão de auditoria da empresa
exigir manter o registro histórico, decisão de aplicação).*

  ------------------- ------------------------------- ----------------------------------------
  **Campo**           **Tipo lógico**                 **Descrição / regra**

  **ID_Adesao**       *referência                     ---
                      (Mov_Rh_Beneficio_Adesao) ---   
                      chave primária (composta)*      

  **ID_Dependente**   *referência                     ---
                      (Cad_Participante_Dependente,   
                      Fase 0) --- chave primária      
                      (composta)*                     
  ------------------- ------------------------------- ----------------------------------------

*Desconto/custo do colaborador na folha: reaproveita o motor de
Cad_Rh_Verba já existente (seção 5), sem estrutura de cálculo própria
--- uma Cad_Rh_Verba de desconto cuja Formula referencia a adesão e a
coparticipação vigente do vínculo (Mov_Rh_Beneficio_Adesao +
Cad_Rh_Beneficio_Valor, por Tipo_Titularidade de titular e de cada
dependente coberto), mesmo padrão de fórmula dinâmica já usado alhures
(ex. insalubridade, seção 13). Vale-transporte mantém sua regra própria
por lei (desconto limitado ao menor entre 6% do salário e o custo real,
só se solicitado pelo colaborador --- Lei 7.418/1985) --- comportamento
de aplicação sobre a mesma estrutura genérica, sem campo extra.
Operadora do benefício = Cad_Participante (fornecedor); a fatura mensal
da operadora é coberta pelo fluxo já existente de Compras/Contas a Pagar
(Mov_Titulo) --- a conciliação entre a fatura e a soma dos
descontos/custos individuais é comportamento de aplicação/relatório, não
uma entidade nova.*

Mov_Rh_Beneficio_Taxa_Global

Uma taxa administrativa (ou desconto comercial) que a operadora cobra da
empresa como um todo, não por colaborador --- pedido por Alberto: \"as
operadoras de plano de saúde pode cobrar um valor por colaborador e
depois cobrar uma taxa global\... isto também vale quando tem desconto
global\". Cabeçalho de uma ocorrência --- o critério de rateio pode
variar a cada lançamento (\"isto é opcional por numero de vidas ou valor
individual, é uma escolha não fechado\"), por isso não é propriedade
fixa de Cad_Rh_Beneficio.

*Vigência: não --- cada ocorrência de taxa/desconto é um evento próprio,
datado; uma correção nasce como nova linha, nunca a edição da anterior.*

  --------------------- ------------------------ ----------------------------------------
  **Campo**             **Tipo lógico**          **Descrição / regra**

  **ID_Taxa_Global**    *identificador*          ---

  **ID_Beneficio**      *referência              ---
                        (Cad_Rh_Beneficio)*      

  **Competencia**       *competência*            A competência de folha em que esta
                                                 ocorrência é rateada e lançada.
                                                 Substitui o antigo \"Competencia_Ano /
                                                 Competencia_Mes\" (revisão 14).

  **Tipo**              *enumeração {taxa,       taxa: custo adicional cobrado pela
                        desconto}*               operadora. desconto: valor comercial
                                                 devolvido/abatido pela operadora ---
                                                 mesmo mecanismo, direção de lançamento
                                                 contábil oposta, resolvida pela regra
                                                 contábil da verba informativa (seção 5),
                                                 não por este campo.

  **Valor_Total**       *número*                 O valor total informado pela operadora
                                                 nesta ocorrência, antes do rateio.

  **Criterio_Rateio**   *enumeração {por_vidas,  Escolhido a cada ocorrência, não fixo no
                        por_valor_individual}*   benefício. por_vidas: cada colaborador
                                                 aderente conta 1 (titular) + o número de
                                                 dependentes cobertos NAQUELA adesão
                                                 (Mov_Rh_Beneficio_Adesao_Dependente) ---
                                                 \"a pessoa tem ele mais 3 dependentes
                                                 ele conta como 4\".
                                                 por_valor_individual: soma do
                                                 Valor_Cobrado_Operadora vigente do
                                                 titular + o de cada dependente coberto
                                                 (Cad_Rh_Beneficio_Valor, por
                                                 Tipo_Titularidade/Faixa_Etaria) --- \"o
                                                 valor dele mais os dos dependentes\". Em
                                                 ambos os critérios, a contagem/soma de
                                                 dependentes só se aplica quando eles de
                                                 fato fazem parte daquele benefício
                                                 (confirmado por Alberto: \"isto sim se
                                                 os dependentes fazer parte ou não do
                                                 beneficio\") --- sem nenhuma linha em
                                                 Mov_Rh_Beneficio_Adesao_Dependente para
                                                 aquela adesão, o colaborador conta só
                                                 como 1 vida / só o valor do titular,
                                                 nunca um pressuposto de cobertura.
  --------------------- ------------------------ ----------------------------------------

*Rateio e lançamento --- comportamento de aplicação: ao apurar a folha
da competência, o sistema soma as frações de vidas ou de valor (conforme
Criterio_Rateio) de todos os aderentes ATIVOS daquele benefício, calcula
a fração de cada um (vidas ou valor do colaborador ÷ total), e gera um
Mov_Rh_Folha_Item por titular aderente (Tipo=informativo, verba própria
do benefício, seção 5) com o valor de sua fração --- a soma dos itens
gerados bate com Valor_Total. Dependentes nunca recebem item próprio
(não têm vínculo/folha próprios) --- sua fração é sempre absorvida no
item do titular correspondente. Como cada item já carrega o ID_Vinculo
do titular, o departamento aparece automaticamente na contabilização: o
Motor de Regras (Fase 0, seção 8) já resolve conta contábil por
verba+departamento a partir do departamento ATUAL de cada vínculo ---
confirmado por Alberto: \"se distribuimos por colaborador
consequentemente o departamento já herda isto\" ---, sem nenhuma
entidade de rateio por departamento à parte.*

18\. Portal do Colaborador

Nova seção nesta revisão (10), pedida por Alberto: \"esta faltando o
portal do colaborador, onde o mesmo pode visualizar seu holerith e
também fazer o pedido de férias, e o pedido de férias tem que ser
aprovado pelo gestor. No caso do ponto eletronico o colaborador também
tem que visualizar seus pontos.\" Depois estendida para incluir também a
solicitação de inclusão de dependentes. O portal em si é uma camada de
ACESSO, não uma estrutura de dados nova para a maior parte das funções:
holerite e ponto são autoacesso do próprio colaborador sobre dados que
já existem; só férias e dependentes ganham fluxo de
solicitação/aprovação, porque envolvem uma decisão de terceiro antes de
valerem.

*Holerite (autoacesso, sem entidade nova): o colaborador consulta,
dentro do próprio vínculo (Cad_Vinculo_Emprego, seção 3), as
Mov_Rh_Folha_Apuracao/Mov_Rh_Folha_Item (seção 5) já apuradas para ele,
filtradas por competência --- mesma estrutura já usada pela equipe de
folha, só com o recorte de acesso restrito ao próprio ID_Vinculo do
colaborador logado, em vez do escopo por filial/departamento de
Cad_Usuario_Escopo (seção 14). Nenhum campo ou tabela nova: o holerite
em si (layout impresso/PDF) é camada de apresentação sobre dados já
estruturados.*

*Ponto eletrônico (autoacesso, sem entidade nova): mesmo princípio --- o
colaborador consulta seus próprios Mov_Rh_Ponto (seção 6), filtrados
pelo próprio ID_Vinculo, sem acesso aos registros de outros
colaboradores. O gestor já tinha visão da equipe sobre banco de horas
(seção 7); o portal estende o mesmo recorte de acesso --- próprio
vínculo para o colaborador, equipe para o gestor --- ao ponto em si, sem
estrutura nova.*

Mov_Rh_Solicitacao_Dependente

Adicionado nesta revisão (10), pedido por Alberto (\"no portal do
colaborador também tera que ter a opção de adicionar dependentes, com
solicitação de dados do dependente, vinculo e documentos que comprovam
os dependentes\... lembra que quem efetiva a inclusão é a equipe de
rh\"): o colaborador SOLICITA (pré-preenche), a equipe de RH EFETIVA ---
mesmo espírito do pedido de férias abaixo, mas com uma única etapa de
validação, confirmado por Alberto (\"Sim neste caso só passar pelo
RH\"): sem etapa de gestor.

*Vigência: não --- evento; uma solicitação rejeitada não é reaberta, o
colaborador solicita de novo, gerando um novo registro.*

  -------------------------------- ------------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**                 **Descrição / regra**

  **ID_Solicitacao**               *identificador*                 ---

  **ID_Vinculo**                   *referência                     Quem solicita --- o colaborador titular
                                   (Cad_Vinculo_Emprego)*          do futuro dependente.

  **Nome**                         *texto*                         ---

  **Data_Nascimento**              *data*                          ---

  **CPF**                          *código (11), opcional*         Nem todo dependente tem CPF no momento
                                                                   da solicitação (ex.: recém-nascido).

  **ID_Tipo_Dependente**           *referência                     Mesmo domínio eSocial aberto usado por
                                   (Cad_Classe_Sistema, domínio =  Cad_Participante_Dependente (Fase 0) ---
                                   tipo_dependente_esocial, Fase   o colaborador já pré-classifica o
                                   0)*                             vínculo (filho/enteado,
                                                                   cônjuge/companheiro etc.) na
                                                                   solicitação.

  **Status**                       *enumeração {solicitado,        ---
                                   efetivado, rejeitado}*          

  **ID_Participante_Efetivacao**   *referência (Cad_Participante,  Quem da equipe de RH efetivou --- mesmo
                                   opcional)*                      critério de escopo de RH/folha já usado
                                                                   na validação de férias, abaixo.

  **Data_Efetivacao**              *data, opcional*                ---

  **Motivo_Rejeicao**              *texto, opcional*               Preenchido só quando Status=rejeitado.

  **ID_Dependente_Gerado**         *referência                     Preenchido quando Status=efetivado,
                                   (Cad_Participante_Dependente,   ligando a solicitação ao registro
                                   Fase 0, opcional)*              definitivo --- o RH pode
                                                                   ajustar/completar os dados (ex.:
                                                                   Incapaz_Permanente,
                                                                   Renda_Anual_Declarada, seção 4 da Fase
                                                                   0) antes de efetivar; não é cópia
                                                                   automática literal dos dados
                                                                   pré-preenchidos pelo colaborador.
  -------------------------------- ------------------------------- ----------------------------------------

*Documentos comprobatórios do dependente (certidão de nascimento,
casamento, laudo de incapacidade etc.): anexados via
Cad_Documento_Vinculo apontando para esta solicitação --- mesmo
mecanismo de GED já reaproveitado em todo este módulo, sem campo ou
estrutura de anexo dedicada.*

Cad_Rh_Pensao_Alimenticia

Adicionado nesta revisão (10), pedido por Alberto (\"existe a parte de
pensão que é descontada do colaborador e passado para a pensionasta ou
representante legal\... o mesmo contribuinte tenho 2 ou mais pessoas
para receberem o pagamento\"): um registro por pensionista/decisão
judicial --- vigência própria, permitindo 2 ou mais pensionistas
simultâneos para o mesmo colaborador.

*Vigência: sim --- cada decisão/redirecionamento nasce como nova linha
de vigência, nunca sobrescrita, preservando o histórico de descontos já
feitos mesmo quando o pensionista muda.*

  --------------------------------- ----------------------------- ------------------------------------------------------
  **Campo**                         **Tipo lógico**               **Descrição / regra**

  **ID_Pensao**                     *identificador*               ---

  **ID_Vinculo**                    *referência                   O colaborador que paga a pensão.
                                    (Cad_Vinculo_Emprego)*        

  **ID_Participante_Pensionista**   *referência                   Reaproveita o cadastro único --- cobre tanto o
                                    (Cad_Participante)*           pensionista quanto um representante legal, mesmo
                                                                  princípio \"cadastro único, papéis por contexto\" já
                                                                  usado em todo o dicionário.

  **ID_Processo_Judicial**          *referência (Cad_Processo,    A decisão judicial de origem, quando aplicável.
                                    Fase 8 --- Jurídico,          Revisão 16: passa a apontar para Cad_Processo (área
                                    opcional)*                    família ou cível), no lugar do antigo
                                                                  Cad_Rh_Processo_Administrativo_Judicial, aposentado.

  **Modelo_Calculo**                *enumeração {percentual,      ---
                                    valor_fixo}*                  

  **Percentual**                    *número, opcional*            Preenchido quando Modelo_Calculo=percentual.

  **Valor_Fixo**                    *número, opcional*            Preenchido quando Modelo_Calculo=valor_fixo.

  **Base_Calculo_Tipo**             *enumeração                   A prática judicial varia (algumas decisões incidem
                                    {remuneracao_total,           sobre a remuneração total, outras só sobre o salário
                                    salario_base, outro}*         base) --- sem travar um único critério. Renomeado na
                                                                  revisão 14 (antes Base_Calculo): o mesmo nome era
                                                                  usado para o valor numérico da base em
                                                                  Mov_Rh_Folha_Item.

  **Data_Fim_Prevista**             *data, opcional*              Adicionado por Alberto (\"Tem pensionistas que são
                                                                  filhos, que tem data de saída, com isto o RH tem que
                                                                  saber desta data para verificações\"): mesmo padrão já
                                                                  usado em Cad_Participante_Historico_Departamento/Cargo
                                                                  (empréstimo/substituição, Fase 0) e em
                                                                  Mov_Rh_Banco_Horas_Movimento.Data_Limite_Compensacao
                                                                  (seção 7) --- um prazo que sinaliza revisão humana,
                                                                  não um corte automático. Preenchida tipicamente para
                                                                  pensionista filho/menor, quando a decisão judicial já
                                                                  estabelece um termo.

  **Vigencia_Fim**                  *data*                        O fim de vigência REAL desta linha --- vazia enquanto
                                                                  a pensão está ativa. Preenchida pelo RH ao decidir
                                                                  encerrar (data de saída vencida sem prorrogação, ou
                                                                  falecimento do pensionista sem redirecionamento).
                                                                  Renomeado na revisão 14 (antes Data_Fim). Sempre
                                                                  preenchida: 31/12/9999 quando o fim é indefinido
                                                                  (versão vigente) --- convenção da Fase 0, seção 2.

  **ID_Pensao_Origem**              *referência                   Adicionado por Alberto (\"no caso de falecimento do
                                    (Cad_Rh_Pensao_Alimenticia,   pensionista, o RH tera que verificar se esta parte da
                                    autorreferência, opcional)*   pensão será redirecionado para outra pessoa ou será
                                                                  retirada da folha\... não necessariamente um novo
                                                                  beneficiario, pode ser redirecionado para outro
                                                                  pensionista da lista\"): preenchido só quando esta
                                                                  linha nasce como redirecionamento de uma pensão
                                                                  anterior encerrada (por falecimento do pensionista ou
                                                                  outro motivo) --- liga a nova à antiga para
                                                                  rastreabilidade, mesmo princípio já usado em
                                                                  Cad_Vinculo_Emprego.ID_Vinculo_Origem_Transferencia
                                                                  (seção 3) e em Mov_Esocial_Evento.ID_Evento_Retificado
                                                                  (seção 9). O redirecionamento pode ir tanto para uma
                                                                  pessoa NOVA (ID_Participante_Pensionista inédito)
                                                                  quanto para um pensionista JÁ EXISTENTE na lista do
                                                                  mesmo colaborador (aumentando o Percentual/Valor_Fixo
                                                                  dele, numa linha própria) --- os dois casos usam este
                                                                  mesmo mecanismo, sem estrutura distinta. Vazio quando
                                                                  a pensão nasce do zero (primeira decisão judicial para
                                                                  aquele vínculo).

  **Vigencia_Inicio**               *data*                        Primeiro dia em que esta versão vale.

  **Motivo_Vigencia**               *texto, opcional*             Por que esta versão foi criada.
  --------------------------------- ----------------------------- ------------------------------------------------------

*Revisão humana de prazo/óbito --- comportamento de aplicação, sem corte
automático: registros com Data_Fim_Prevista próxima ou já vencida ficam
visíveis à RH (mesmo mecanismo de alerta já usado para o vencimento do
banco de horas, seção 7) para decisão entre ENCERRAR (preenche Data_Fim;
a verba para de ser gerada nas apurações seguintes) ou PRORROGAR (nova
linha de vigência com Data_Fim_Prevista atualizada, mesmo mecanismo
append-only de histórico já usado em todo o dicionário). Falecimento do
PENSIONISTA (diferente do falecimento do colaborador que paga, já
coberto por Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito,
seção 3) não tem alerta automático --- chega à RH por via externa (ex.
certidão de óbito) --- e a mesma decisão se aplica: ENCERRAR ou
REDIRECIONAR (ver ID_Pensao_Origem, acima).*

*Pensão alimentícia na folha e no pagamento: reaproveita a generalização
de Mov_Rh_Folha_Item.ID_Origem_Ocorrencia (seção 5, nova nesta revisão)
--- cada linha vigente de Cad_Rh_Pensao_Alimenticia gera sua própria
ocorrência da verba \"Pensão Alimentícia\" (Cad_Rh_Verba, seção 5)
dentro da mesma apuração do colaborador, permitindo 2+ pensionistas
simultâneos sem conflito de unicidade. No lado de Mov_Titulo (Contas a
Pagar/Receber, Origem_Tipo=folha_pagamento,
Natureza_Titulo_Folha=pensao_alimenticia): estende o mesmo mecanismo já
usado para óbito (seção 3) --- o ID_Participante do título resolve para
Cad_Rh_Pensao_Alimenticia.ID_Participante_Pensionista da ocorrência de
origem (via ID_Origem_Ocorrencia), nunca para o colaborador; cada
pensionista recebe seu PRÓPRIO título e sua própria remessa bancária, na
conta bancária dele (Cad_Participante_Dados_Bancarios, Fase 0 --- já
genérico para qualquer Cad_Participante, sem mudança). Sem alteração
estrutural no documento de Contas a Pagar/Receber --- o mecanismo de
Natureza_Titulo_Folha já previa múltiplas naturezas por apuração desde a
revisão anterior.*

19\. Tabela Salarial

Nova seção nesta revisão (10), pedida por Alberto: \"podemos ter uma
tabela salario, que tem os cargos, e steps salariais onde os salarios
tem que respeitar esta tabela, que pode variar e ser revisada
periodidamente. E se algum cargo estiver fora da tabela precisa ter a
justificativa para isto. Isto é se a empresa optar por utilizar uma
tabela salarial.\" Recurso deliberadamente OPCIONAL, em dois níveis: uma
empresa pode não usar tabela salarial nenhuma; e, mesmo usando, um cargo
específico pode ficar fora de qualquer grupo --- mesmo padrão \"sem
referência = sem restrição\" já usado no resto do dicionário. Estrutura
agnóstica de regime (CLT ou, no futuro, estatutário) --- Alberto
observou que um plano de carreira estatutário é, na prática, esta mesma
estrutura com respaldo legal.

Cad_Rh_Tabela_Salarial

O catálogo de uma tabela salarial, por empresa.

*Vigência: sim --- revisão periódica nasce como nova versão, nunca
sobrescrita, mesmo princípio já usado em
Cad_Rh_Salario_Minimo/Cad_Rh_Beneficio_Valor.*

  ---------------------- ----------------- ----------------------------------------
  **Campo**              **Tipo lógico**   **Descrição / regra**

  **ID_Tabela**          *identificador*   ---

  **ID_Tabela_Versao**   *identificador da Chave primária da versão (tabela física
                         versão*           Cad_Rh_Tabela_Salarial_Versao).
                                           ID_Tabela é a identidade, única e
                                           referenciada pelas outras tabelas; cada
                                           versão guarda a sua janela de vigência
                                           --- Fase 0, seção 2.

  **ID_Empresa**         *referência       ---
                         (Cad_Empresa)*    

  **Nome**               *texto*           ---

  **Vigencia_Inicio**    *data*            --- Renomeado na revisão 14 (antes
                                           Data_Vigencia_Inicio).

  **Vigencia_Fim**       *data*            Adicionado nesta revisão (11): vazia
                                           enquanto esta é a versão vigente da
                                           tabela. Comportamento de aplicação ---
                                           ao nascer uma nova vigência (revisão
                                           periódica da tabela), a aplicação
                                           preenche automaticamente este campo, na
                                           linha anterior, com o dia anterior ao
                                           novo Data_Vigencia_Inicio, evitando uma
                                           subconsulta/window function para achar
                                           \"a próxima linha\" a cada busca. Só
                                           nesta entidade ---
                                           Cad_Rh_Tabela_Salarial_Grupo e
                                           Cad_Rh_Tabela_Salarial_Step (abaixo) não
                                           ganharam o campo equivalente nesta
                                           revisão. Renomeado na revisão 14 (antes
                                           Data_Vigencia_Fim). Sempre preenchida:
                                           31/12/9999 quando o fim é indefinido
                                           (versão vigente) --- convenção da Fase
                                           0, seção 2.

  **Motivo_Vigencia**    *texto, opcional* Por que esta versão foi criada.
  ---------------------- ----------------- ----------------------------------------

Cad_Rh_Tabela_Salarial_Grupo

Adicionado por Alberto (\"A tabela tem que ter os seus grupos, como
exemplo, executivos / diretoria, administrativo, universitarios,
operacional entre outros\"): a classificação ocupacional dentro da
tabela --- organizacional, não dona da escada de steps (ver correção
abaixo).

*Vigência: não --- classificação de referência; uma reorganização de
grupos é correção de cadastro, não histórico versionado.*

  ----------------- --------------------------- ----------------------------------------
  **Campo**         **Tipo lógico**             **Descrição / regra**

  **ID_Grupo**      *identificador*             ---

  **ID_Tabela**     *referência                 ---
                    (Cad_Rh_Tabela_Salarial)*   

  **Nome**          *texto*                     Ex.: \"Executivos/Diretoria\",
                                                \"Administrativo\", \"Universitários\",
                                                \"Operacional\" --- domínio livre da
                                                empresa, texto, não fixo neste
                                                dicionário.
  ----------------- --------------------------- ----------------------------------------

Cad_Rh_Tabela_Salarial_Step

Corrigido durante o desenho por Alberto (\"com um plano de carreira,
cada degrau com um valor exato. E um cargo pode ter 7 steps e outro só
2\"): cada CARGO tem sua própria escada de steps, com a quantidade que
fizer sentido --- os steps pertencem ao cargo, não ao grupo ocupacional
(que fica só como classificação, em
Cad_Rh_Cargo.ID_Grupo_Tabela_Salarial, seção 2). Valor de step FIXO, não
faixa min-máx, confirmado por Alberto.

*Vigência: sim --- mesma vigência da tabela: uma revisão de valores
nasce como nova versão, preservando o valor vigente quando cada
Cad_Participante_Historico_Salario (Fase 0) já apurado foi fixado.*

  ------------------------- ----------------- ----------------------------------------
  **Campo**                 **Tipo lógico**   **Descrição / regra**

  **ID_Step**               *identificador*   ---

  **ID_Step_Versao**        *identificador da Chave primária da versão (tabela física
                            versão*           Cad_Rh_Tabela_Salarial_Step_Versao).
                                              ID_Step é a identidade, única e
                                              referenciada pelas outras tabelas; cada
                                              versão guarda a sua janela de vigência
                                              --- Fase 0, seção 2.

  **ID_Cargo**              *referência       ---
                            (Cad_Rh_Cargo,    
                            seção 2)*         

  **Nivel_Step**            *número*          A posição do degrau na escada daquele
                                              cargo (1, 2, 3\...) --- quantidade livre
                                              por cargo.

  **Valor_Step**            *número*          O valor fixo do salário naquele degrau.

  **Criterio_Progressao**   *texto, opcional* Adicionado nesta revisão (12), da
                                              pesquisa sobre servidor estatutário
                                              (seção 20) --- Alberto observou que um
                                              plano de carreira estatutário
                                              reaproveita esta mesma estrutura com
                                              respaldo legal: o critério legal de
                                              progressão para este degrau, descrito em
                                              texto livre (ex.: \"interstício de 2
                                              anos + avaliação de desempenho
                                              favorável\", \"tempo de serviço, Lei X
                                              art. Y\") --- sem motor automático: a
                                              progressão continua sendo lançada
                                              manualmente pelo RH como uma linha comum
                                              em Cad_Participante_Historico_Salario
                                              (Fase 0), mesma decisão já registrada na
                                              revisão 10 de que não há progressão
                                              automática entre steps.

  **Vigencia_Inicio**       *data*            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**          *data*            Último dia em que esta versão vale
                                              (inclusive). Sempre preenchida:
                                              31/12/9999 quando o fim é indefinido
                                              (versão vigente) --- convenção da Fase
                                              0, seção 2.

  **Motivo_Vigencia**       *texto, opcional* Por que esta versão foi criada.
  ------------------------- ----------------- ----------------------------------------

*Respeito à tabela --- comportamento de aplicação:
Cad_Participante_Historico_Salario (Fase 0) ganhou, nesta revisão,
ID_Step_Tabela_Salarial (referência a este Cad_Rh_Tabela_Salarial_Step,
opcional) e Justificativa_Fora_Tabela (texto, opcional) --- obrigatória
por validação de aplicação (não constraint de banco, mesmo padrão
condicional já usado em todo o dicionário) sempre que o Valor_Salario
lançado diverge do Valor_Step vigente do step indicado, ou quando o
cargo tem tabela vigente (grupo/step cadastrados) mas nenhum step foi
indicado na contratação/reajuste individual. Uso opcional nos dois
níveis já descritos acima: sem ID_Grupo_Tabela_Salarial no cargo, ou sem
nenhum Cad_Rh_Tabela_Salarial cadastrado pela empresa, nenhuma validação
se aplica.*

20\. Regime Estatutário (RJU)

Nova seção nesta revisão (12), pedida por Alberto: um SEGUNDO regime de
folha, em paralelo ao CLT já modelado no restante deste documento ---
não uma extensão pontual do que já existe. Cobre administração direta,
autarquias e fundações públicas com servidores estatutários, regidos
pelo Regime Jurídico Único (RJU) de cada ente --- a Lei 8.112/90 serve
de referência federal ao longo desta seção, mas cada ente (estado,
município) tem seu próprio estatuto, com estrutura geral similar.
Distinto de empresa pública/sociedade de economia mista, que já é CLT
comum --- já coberto pela revisão 10, que acrescentou
Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal (seção 3) para a
exigência de motivação formal de dispensa (Súmula 390 TST/RE 688.267
STF), sem tocar em nenhum ponto desta seção.

Este é o levantamento de 13 frentes registrado nas Notas da revisão 10,
agora desenhado e construído ponto a ponto: categoria do vínculo;
admissão em três etapas; estágio probatório e estabilidade; motivos de
vacância próprios; isenção de FGTS; previdência RPPS; remuneração por
subsídio ou vencimento; férias/13º e jornada reaproveitados; regime
disciplinar/PAD; progressão de carreira por critério legal; e folha de
inativos.

Categoria do vínculo e admissão em três etapas

Cad_Vinculo_Emprego.Tipo_Vinculo (seção 3) ganhou estatutario_efetivo,
cargo_comissionado, temporario_administrativo e inativo_estatutario ---
espelhando os códigos 301/302/306 (categoria de trabalhador --- agente
público) da tabela do eSocial. A admissão do servidor
efetivo/comissionado/temporário administrativo não é um evento único
como na CLT: são três etapas distintas --- Data_Nomeacao (o ato de
nomeação), Data_Posse (investidura formal, prazo legal de referência de
até 30 dias da nomeação) e Data_Exercicio (início efetivo das
atribuições, prazo legal de referência de até 15 dias da posse) --- as
três novas em Cad_Vinculo_Emprego (seção 3). Data_Admissao (campo já
existente, usado em toda contagem de tempo de serviço/período aquisitivo
do dicionário) passa a receber a data de EXERCÍCIO para estes vínculos,
preservando automaticamente todo o cálculo já derivado dali.
Comportamento de aplicação, pedido por Alberto: quando Posse ou
Exercício não são preenchidos dentro do prazo legal contado da etapa
anterior, a aplicação sinaliza um ALERTA à RH --- nunca um bloqueio,
mesmo princípio \"sugere, nunca aplica automaticamente\" já usado em
todo o dicionário.

Cad_Rh_Estagio_Probatorio

O estágio probatório do servidor estatutário --- deliberadamente
SEPARADO de Mov_Rh_Avaliacao_Desempenho (seção 4): aquela seção cobre o
acompanhamento comercial contínuo e periódico ao longo de toda a relação
de emprego CLT; esta entidade cobre o período único, de natureza
jurídica distinta, que precede e condiciona a estabilidade do art. 41 da
CF (3 anos, na referência federal).

*Vigência: não --- um estágio probatório por vínculo; uma prorrogação
atualiza Data_Fim_Previsto e o Status deste mesmo registro, não gera
linha nova, mesmo critério já usado para prorrogação de contrato de
experiência (Cad_Vinculo_Emprego.Tipo_Contrato_Prazo, seção 3).*

  ----------------------- ----------------------- ----------------------------------------
  **Campo**               **Tipo lógico**         **Descrição / regra**

  **ID_Estagio**          *identificador*         ---

  **ID_Vinculo**          *referência             ---
                          (Cad_Vinculo_Emprego,   
                          seção 3)*               

  **Data_Inicio**         *data*                  ---

  **Data_Fim_Previsto**   *data*                  ---

  **Status**              *enumeração             homologado dispara automaticamente
                          {em_andamento,          Cad_Vinculo_Emprego.Data_Estabilidade
                          homologado, exonerado,  (seção 3) --- mesmo padrão \"calculado
                          prorrogado}*            mas armazenado\" já usado no dicionário.
                                                  exonerado cobre a reprovação no estágio
                                                  (distinta de exoneração a pedido ou de
                                                  cargo em comissão, ver
                                                  Cad_Rh_Motivo_Desligamento, seção 3).
                                                  prorrogado cobre a extensão do período
                                                  dentro do limite legal do estatuto do
                                                  ente.

  **Data_Conclusao**      *data, opcional*        Vazia enquanto Status=em_andamento ou
                                                  prorrogado.
  ----------------------- ----------------------- ----------------------------------------

Mov_Rh_Estagio_Probatorio_Avaliacao

A avaliação periódica de um estágio probatório --- quantas forem
exigidas pelo estatuto do ente ao longo do período (ex.: trimestral,
semestral). É movimentação.

*Vigência: não. O documento da avaliação (formulário, ata da comissão)
fica anexado via GED já existente (Cad_Documento_Vinculo, Fase 0, seção
11) --- mesmo mecanismo já usado para TRCT/homologação e para
exame/curso/acidente (seção 12), sem campo de arquivo próprio aqui.*

  ------------------------------- ------------------------------ ----------------------------------------
  **Campo**                       **Tipo lógico**                **Descrição / regra**

  **ID_Avaliacao**                *identificador*                ---

  **ID_Estagio**                  *referência                    ---
                                  (Cad_Rh_Estagio_Probatorio)*   

  **Periodo_Referencia**          *texto*                        O período coberto por esta avaliação
                                                                 dentro do estágio (ex.: \"1º
                                                                 trimestre\", \"2026 --- 2º semestre\")
                                                                 --- livre por ente, mesmo critério de
                                                                 parametrização livre já usado no resto
                                                                 do motor de folha.

  **Data_Avaliacao**              *data*                         ---

  **ID_Participante_Avaliador**   *referência                    ---
                                  (Cad_Participante)*            

  **Parecer_Resultado**           *enumeração {favoravel,        Renomeado na revisão 14 (antes Parecer):
                                  desfavoravel}*                 nas avaliações de candidato e de
                                                                 desempenho, Parecer é o texto livre do
                                                                 avaliador.
  ------------------------------- ------------------------------ ----------------------------------------

Estabilidade

Cad_Vinculo_Emprego.Data_Estabilidade (seção 3) --- data preenchida
AUTOMATICAMENTE quando Cad_Rh_Estagio_Probatorio.Status (acima) do
vínculo passa a homologado, mesmo princípio \"calculado mas armazenado\"
já usado em todo o dicionário (ex.: Data_Fim_Prevista/vigências).

Motivos de vacância próprios

Cad_Rh_Motivo_Desligamento (seção 3) é cadastro aberto --- sem mudança
de schema, a Mlegate cadastra exemplos próprios do regime estatutário:
Exoneração a Pedido, Exoneração de Cargo em Comissão, Demissão (PAD ---
liga-se a Mov_Rh_Processo_Disciplinar, abaixo, quando
Penalidade_Aplicada=demissao), Aposentadoria, Posse em Cargo
Inacumulável (art. 37, XVI/XVII CF) e Readaptação. A entidade ganhou um
campo novo nesta revisão: Aplicavel_Regime, enumeração {clt,
estatutario, ambos} (seção 3) --- impede um motivo incompatível de ser
usado no vínculo errado (ex.: \"Demissão (PAD)\" só cabe em estatutario;
\"Pedido de Demissão\" cabe em ambos, a definir caso a caso pela
Mlegate).

FGTS isento, previdência RPPS, férias/13º e jornada --- já cobertos, sem
estrutura nova

Quatro pontos do levantamento original resolvidos por mecanismos JÁ
EXISTENTES no dicionário, sem nenhuma entidade ou campo novo: (1) FGTS
isento --- a verba de FGTS já pode excluir
estatutario_efetivo/cargo_comissionado/temporario_administrativo via
Cad_Rh_Verba_Tipo_Vinculo (seção 5), mesmo mecanismo de amarração por
tipo de vínculo já construído na revisão 8. (2) Previdência RPPS --- a
contribuição ao Regime Próprio de Previdência Social é só mais uma
Cad_Rh_Verba restrita por Cad_Rh_Verba_Tipo_Vinculo (seção 5) aos tipos
de vínculo estatutário; o evento eSocial S-1202 (Remuneração de servidor
vinculado a RPPS, distinto do S-1200 do regime geral) já cabe dentro do
domínio aberto de Mov_Esocial_Evento.ID_Tipo_Evento (seção 10), sem novo
valor estrutural. (3) Férias/13º --- a parametrização já livre de
Cad_Rh_Verba (seção 5) e a estrutura de período aquisitivo/gozo já
existente (Mov_Rh_Ferias_Periodo/Mov_Rh_Ferias_Gozo, seção 8) são
reaproveitadas sem mudança, cobrindo as regras específicas de férias/13º
de cada estatuto por configuração, não por estrutura nova. (4) Jornada
--- reaproveita Cad_Rh_Turno/Cad_Rh_Escala já existentes (seção 6), com
a parametrização por carreira/cargo que cada ente definir.

Remuneração por subsídio ou vencimento + Fundamento_Legal

Cad_Vinculo_Emprego ganhou Modelo_Remuneracao, enumeração
{verbas_multiplas, subsidio} (seção 3): subsídio é a remuneração por
parcela única, que veda por lei somar outras verbas, salvo exceções
legais expressas. Cad_Rh_Verba ganhou Fundamento_Legal, texto opcional
(seção 5) --- a lei/artigo que criou a verba; campo GENÉRICO, não
exclusivo de servidor estatutário, útil para qualquer verba (inclusive
CLT) rastrear seu fundamento para auditoria. Cad_Rh_Cargo (seção 2)
ganhou o mesmo Fundamento_Legal, agora no nível do cargo --- relevante
para o plano de cargos e carreira estatutário, também genérico.

Mov_Rh_Processo_Disciplinar

O processo disciplinar do servidor estatutário --- sindicância ou
Processo Administrativo Disciplinar (PAD) --- explicitamente DISTINTO de
Cad_Processo (Fase 8 --- Jurídico), que cobre só a suspensão de
recolhimento de tributos (INSS/FGTS/IRRF) de um vínculo, não processo
disciplinar.

*Vigência: não --- um processo por instauração; reabertura (ex.:
anulação e novo PAD) nasce como um novo Mov_Rh_Processo_Disciplinar,
mesmo critério de eventos deste dicionário. Documentos do processo
(portaria, relatório da comissão, defesa) ficam anexados via GED já
existente (Cad_Documento_Vinculo, Fase 0, seção 11), sem campo de
arquivo próprio.*

  ----------------------------- ------------------------------ ----------------------------------------
  **Campo**                     **Tipo lógico**                **Descrição / regra**

  **ID_Processo_Disciplinar**   *identificador*                Renomeado na revisão 16 (antes
                                                               ID_Processo): o nome colidia com a chave
                                                               de Cad_Processo (Fase 8 --- Jurídico). É
                                                               sindicância ou PAD interno, não
                                                               contencioso.

  **ID_Vinculo**                *referência                    ---
                                (Cad_Vinculo_Emprego, seção    
                                3)*                            

  **Tipo**                      *enumeração {sindicancia,      ---
                                pad}*                          

  **Data_Abertura**             *data*                         ---

  **Status**                    *enumeração {em_andamento,     ---
                                arquivado,                     
                                concluido_com_penalidade,      
                                concluido_sem_penalidade}*     

  **Penalidade_Aplicada**       *enumeração {advertencia,      Preenchida só quando
                                suspensao, demissao,           Status=concluido_com_penalidade. Quando
                                cassacao_aposentadoria,        demissao, liga-se ao desligamento do
                                destituicao_cargo_comissao},   vínculo com o motivo \"Demissão (PAD)\"
                                opcional*                      (Cad_Rh_Motivo_Desligamento, acima).

  **Data_Conclusao**            *data, opcional*               ---
  ----------------------------- ------------------------------ ----------------------------------------

Progressão de carreira por critério legal

Cad_Rh_Tabela_Salarial_Step (seção 19) ganhou Criterio_Progressao, texto
opcional --- o critério legal de progressão descrito em texto livre
(ex.: interstício + avaliação, tempo de serviço). Sem motor automático:
a progressão continua sendo lançada manualmente pelo RH em
Cad_Participante_Historico_Salario (Fase 0), mesma decisão já registrada
na revisão 10 de que não há progressão automática entre steps. Alberto
já havia observado, na revisão 10, que um plano de carreira estatutário
é, na prática, esta mesma estrutura de tabela salarial com respaldo
legal --- confirmado aqui: nenhuma entidade nova para carreira, só o
campo de critério.

Folha de inativos

Usa Tipo_Vinculo=inativo_estatutario (acima). Cad_Vinculo_Emprego ganhou
Natureza_Inativo, enumeração opcional {aposentadoria, pensao_por_morte}
(seção 3), e ID_Vinculo_Origem_Aposentadoria, autorreferência a
Cad_Vinculo_Emprego opcional (seção 3, mesmo padrão de
ID_Vinculo_Origem_Transferencia já existente) --- liga o vínculo de
inativo ao vínculo de trabalho original do servidor.
Mov_Rh_Folha_Apuracao.Tipo_Folha (seção 5) ganhou o valor inativos ---
separação automática de ativos e inativos na folha, já que cada apuração
é sempre de um único Tipo_Folha, mesmo mecanismo que já separa
pagamento_autonomo do resto. Contexto de origem: cobre também o caso de
entes que pagam proventos de aposentadoria/pensão diretamente pela
folha, sem RPPS próprio instituído, mantendo-os separados dos ativos.

21\. Como este módulo se conecta com a Fase 0 e outros módulos

  ------------------------------------------------- -------------------------------------------------------- ---------------------
  **Entidade referenciada**                         **Como este módulo usa**                                 **Observação**

  **Cad_Participante (classe funcionário) /         Todo Cad_Vinculo_Emprego (seção 3) referencia um         *Fase 0, sem mudança
  Cad_Participante_Classe**                         Cad_Participante já classificado como funcionário ---    estrutural*
                                                    cadastro único, sem duplicar dados pessoais.             

  **Cad_Participante_Historico_Cargo / Departamento Passam a ser escopados por                               *Fase 0, revisão 27
  / Salario**                                       Cad_Vinculo_Emprego.ID_Vinculo (seção 3), não só por     --- patch em
                                                    participante; agora também a base do cruzamento de       consolidação
                                                    condições de risco por cargo/área (seção 13).            anterior*

  **Cad_Participante_Dependente**                   Permanece no nível do participante; ganhou               *Fase 0, revisão 27
                                                    Elegivel_Irrf, usado pela Formula de verbas de IRRF      --- patch em
                                                    (seção 5).                                               consolidação
                                                                                                             anterior*

  **Cad_Dimensao_Contabil_Valor (dimensão           Reaproveitada por                                        *Fase 0*
  Departamento)**                                   Cad_Participante_Historico_Departamento (Fase 0), por    
                                                    Cad_Usuario_Escopo (seção 14), por                       
                                                    Mov_Rh_Area_Condicao_Risco (seção 13) e agora por        
                                                    Mov_Rh_Avaliacao_Desempenho_Grupo_Nota (seção 4, notas   
                                                    de critério de grupo por departamento) --- mesmo         
                                                    cadastro único de departamento/centro de custo já usado  
                                                    por Produção (Cad_Area_Producao).                        

  **Cad_Filial**                                    Empregador perante o eSocial (Cad_Vinculo_Emprego, seção *Fase 0*
                                                    3) e escopo de apuração de folha (Mov_Rh_Folha_Apuracao, 
                                                    seção 5).                                                

  **Cad_Classe_Sistema (domínios cbo,               Classificam cargo/CBO (Fase 0, agora também usado por    *Fase 0, revisão 27
  categoria_trabalhador_esocial,                    Mov_Rh_Cargo_Condicao_Risco, seção 14), categoria e      --- domínios novos,
  motivo_desligamento_esocial, tipo_evento_esocial; motivo de desligamento do vínculo (seção 5), o tipo de   sem mudança
  rubrica_esocial e tipo_afastamento_esocial        evento/código de risco eSocial (seções 9, 11 e 12) e a   estrutural em
  aposentados na revisão 16 --- ver seção 5)**      rubrica de folha (seção 6).                              Cad_Classe_Sistema*

  **Mov_Pre_Cadastro_Conversao**                    O histórico de entrevistas/avaliações da contratação, já *Fase 0, sem mudança
                                                    registrado na conversão de Cad_Pre_Cadastro em           estrutural*
                                                    Cad_Participante, passa a compor a Ficha do Colaborador  
                                                    (seção 12) por referência, sem duplicar.                 

  **Cad_Regua_Aprovacao / Mov_Aprovacao_Instancia   RESOLVIDO nesta revisão (6): a aprovação de abertura de  *Fase 0, revisão 31
  (Origem_Tipo=abertura_vaga)**                     vaga (Cad_Rh_Vaga.ID_Instancia_Aprovacao, seção 2),      --- novo Origem_Tipo,
                                                    régua sempre opcional --- fecha o gancho de aprovação de construído nesta
                                                    contratação/verba orçamentária citado no Documento       consolidação*
                                                    Analítico, em aberto desde a revisão 4.                  

  **Mov_Compromisso_Orcamentario**                  RESOLVIDO nesta revisão (6):                             *Fase 1 ---
                                                    Cad_Rh_Vaga.ID_Compromisso_Orcamentario (seção 2)        Planejamento &
                                                    referencia diretamente o compromisso orçamentário da     Orçamento, sem
                                                    vaga --- fecha o comentário premonitório (\"uma          mudança estrutural
                                                    contratação aprovada consome 1 vaga contra o             naquele documento*
                                                    Quantidade_Orcada\") que aquele módulo já carregava sem  
                                                    nenhuma entidade de RH que o disparasse.                 

  **Cad_Pre_Cadastro (Consentimento_Banco_Talentos, Campos de retenção de dados de candidato exigidos pela   *Fase 0, revisão 31
  Data_Consentimento, Data_Descarte_Previsto)**     LGPD, referenciando a política por empresa               --- construído nesta
                                                    (Cad_Rh_Politica_Retencao_Candidato, seção 2) para       consolidação*
                                                    calcular o prazo quando há consentimento.                

  **Mov_Pre_Cadastro_Conversao                      Rastreia, quando aplicável, qual candidatura             *Fase 0, revisão 31
  (ID_Vaga_Candidato)**                             (Mov_Rh_Vaga_Candidato, seção 2) originou a conversão a  --- construído nesta
                                                    colaborador --- vazio para contratação direta.           consolidação*

  **Timesheet (Produção / Gestão de Contratos /     Fonte OPCIONAL de marcação de ponto                      *Fase 1 --- Produção;
  PPM)**                                            (Mov_Rh_Ponto.Origem_Tipo=timesheet, seção 6) --- quando Fase 6 ---
                                                    a empresa escolhe essa integração; as duas estruturas    Contratos/PPM (ainda
                                                    são independentes por padrão.                            não especificados
                                                                                                             como documento
                                                                                                             próprio)*

  **Cad_Periodo_Fechamento /                        Controle de período aberto/fechado da folha, por filial  *Fase 0, seção 10,
  Cad_Periodo_Fechamento_Filial                     (Mov_Rh_Folha_Apuracao, seção 5) --- migrado nesta       revisão 37 ---
  (Bloco=\"folha_pagamento\")**                     revisão (13) do antigo cadastro próprio                  mecanismo
                                                    Cad_Rh_Periodo_Folha (seção 5, revisão 8) para o         generalizado; este
                                                    mecanismo genérico da Fase 0. Deliberadamente            módulo migrou para
                                                    independente do Bloco=\"contabilidade\" --- mesma        ele nesta revisão
                                                    estrutura, blocos distintos, sem qualquer relação de     (13)*
                                                    causa/efeito entre eles ---, por instrução explícita de  
                                                    Alberto, já que a folha precisa fechar primeiro, com     
                                                    calendário próprio, antes de poder ser contabilizada.    

  **Mov_Lote_Lancamento**                           Provisão de férias/13º e a liquidação de cada folha      *Fase 0, revisão 28
                                                    (seção 5, inclusive reprocessamentos e                   --- patch em
                                                    pagamento_autonomo) geram lançamento contábil ---        consolidação
                                                    Origem_Tipo folha_pagamento,                             anterior*
                                                    provisao_ferias_decimo_terceiro.                         

  **Cad_Motor_Regra / Cad_Motor_Regra_Criterio /    Resolve a conta contábil de débito/crédito de cada verba *Fase 0, revisão 28
  Cad_Motor_Regra_Resultado**                       (Cad_Rh_Verba.Contabilizavel, seção 5) por critérios     --- patch em
                                                    verba_rh e, quando necessário, departamento --- mesmo    consolidação
                                                    motor já usado por CRM & Vendas e pela tributação de     anterior*
                                                    IBS/CBS.                                                 

  **Cad_Conta_Contabil                              Marca, no nível da conta, quais contas exigem abertura   *Fase 0, revisão 28
  (ID_Dimensao_Abertura_Obrigatoria)**              por centro de custo/departamento no lançamento de folha  --- patch em
                                                    (Mov_Lancamento_Dimensao, já existente).                 consolidação
                                                                                                             anterior*

  **Cad_Documento / Cad_Documento_Vinculo (GED)**   Reaproveitado em três pontos deste módulo, sem campo     *Fase 0, seção 11 ---
                                                    novo: curso/treinamento/exame médico em                  reaproveitado, sem
                                                    Mov_Rh_Ficha_Evento (seção 12); RG/CTPS em               mudança estrutural;
                                                    Cad_Vinculo_Emprego (seção 3); e, no nível de            nota de uso
                                                    Cad_Participante (fora deste módulo), contrato social e  adicionada na revisão
                                                    demais documentos societários do colaborador.            28*

  **Cad_Participante_Dados_Pessoa_Fisica (Sexo,     Campo administrativo de sexo e cor/raça autodeclarada do *Fase 0, revisão 45*
  Cor_Raca)**                                       colaborador, usados pelo relatório de transparência      
                                                    salarial (seção 15) --- cadastrados na extensão de       
                                                    pessoa física do participante, não neste módulo; movidos 
                                                    de Cad_Participante na revisão 45 da Fase 0.             

  **Cad_Participante_Historico_Cargo (ID_Cargo)**   Migrado nesta revisão (6) de três campos soltos (Cargo   *Fase 0, revisão 31
                                                    texto, ID_Cbo, Nivel_Lideranca) para uma única           --- construído nesta
                                                    referência ao novo Cad_Rh_Cargo (seção 2) --- inclusive  consolidação*
                                                    o indicador de nível de liderança usado para calcular a  
                                                    proporção de mulheres em liderança exigida pela Lei      
                                                    14.611/2023 (seção 15).                                  

  **Mov_Titulo (Origem_Tipo=folha_pagamento)**      Adicionado nesta revisão (5): a liquidação de cada       *Fase 2 --- Contas a
                                                    Mov_Rh_Folha_Apuracao paga (seção 5, todo Tipo_Folha --- Pagar/Receber,
                                                    mensal, 13º, férias, rescisão, PLR, pagamento_autonomo)  revisão 8 ---
                                                    passa a gerar título a pagar de verdade, não só          construído nesta
                                                    lançamento contábil --- um Mov_Titulo por                consolidação* Revisão
                                                    Natureza_Titulo_Folha (líquido do colaborador, INSS,     18 (Bloco 5): a
                                                    FGTS, IRRF retido, pensão alimentícia, consignado, entre liquidação deixa de
                                                    outros), todos com ID_Origem apontando para este         gerar título de INSS
                                                    Mov_Rh_Folha_Apuracao/Mov_Rh_Folha_Item. Em caso de      e de IRRF retido e
                                                    óbito, ID_Participante do título resolve para            lança só a provisão
                                                    Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito   contábil; o título
                                                    (seção 3) em vez do colaborador falecido.                nasce na chegada do
                                                                                                             S-5011 e do S-5012,
                                                                                                             com a reversão da
                                                                                                             provisão
                                                                                                             (Contabilidade &
                                                                                                             Fiscal, seção 22.4).
                                                                                                             Pensão alimentícia,
                                                                                                             consignado, FGTS e
                                                                                                             líquido do
                                                                                                             colaborador não
                                                                                                             mudam; o vencimento
                                                                                                             do FGTS passa a vir
                                                                                                             de
                                                                                                             Cad_Regra_Vencimento
                                                                                                             (Fase 0, revisão 47).

  **Mov_Remessa_Bancaria /                          A baixa de Mov_Titulo com Origem_Tipo=folha_pagamento    *Fase 2 ---
  Mov_Remessa_Bancaria_Item**                       passa pelo mesmo mecanismo de remessa bancária já usado  Tesouraria, revisão 5
                                                    para fornecedores --- CNAB/API com tipo de serviço de    --- construído nesta
                                                    lote próprio para folha (salário, tributo com código de  consolidação*
                                                    barras), distinguindo conta-salário de conta corrente do 
                                                    favorecido (Fase 0, revisão 30,                          
                                                    Cad_Participante_Dados_Bancarios.Tipo_Conta).            

  **Cad_Participante_Historico_Filial**             Entidade nova (revisão 9 desta consolidação): a filial   *Fase 0, revisão 32
                                                    ATUAL de um vínculo (seção 3) passa a ser derivada       --- entidade nova,
                                                    daqui, não mais um campo fixo em Cad_Vinculo_Emprego --- construída nesta
                                                    cobre transferência intra-empresa entre filiais;         consolidação*
                                                    empréstimo temporário (Tipo_Alocacao=emprestimo) também  
                                                    vive aqui.                                               

  **Cad_Participante_Historico_Departamento/Cargo   Empréstimo entre áreas (departamento/filial) e           *Fase 0, revisão 32
  (Tipo_Alocacao, Data_Fim_Prevista,                substituição de função com diferencial salarial (cargo)  --- patch construído
  Valor_Diferencial)**                              --- mesmo mecanismo append-only de histórico, com        nesta consolidação*
                                                    retorno automático ao vencer a janela temporária.        

  **Cad_Participante_Historico_Salario              Distingue mudança salarial individual de aplicação em    *Fase 0, revisão 32
  (Origem_Alteracao)**                              massa por reajuste coletivo ou por ajuste automático de  --- patch construído
                                                    piso de salário mínimo (seção 16, acima).                nesta consolidação*

  **Cad_Filial (ID_Categoria_Sindical_Padrao)**     O enquadramento sindical padrão dos vínculos da filial,  *Fase 0, revisão 32
                                                    com override por cargo                                   --- patch construído
                                                    (Cad_Rh_Cargo.ID_Categoria_Sindical, seção 2) ---        nesta consolidação*
                                                    resolve o dissídio coletivo (seção 16).                  

  **Cad_Participante_Dependente (Data_Nascimento,   Reformulado nesta revisão (10), da pesquisa sobre        *Fase 0, revisão 33
  CPF, ID_Tipo_Dependente, Incapaz_Permanente,      critérios legais de dependente: substitui o antigo       --- reformulado nesta
  Cursando_Ensino_Superior_Tecnico,                 Grau_Parentesco fixo pelo domínio eSocial aberto         consolidação*
  Renda_Anual_Declarada,                            (tipo_dependente_esocial); elegibilidade de IRRF e de    
  Elegivel_Salario_Familia)**                       salário-família passam a ser automáticas por             
                                                    idade/incapacidade, cada uma com seu próprio corte       
                                                    etário; renda declarada de ascendente cruza com          
                                                    Cad_Rh_Limite_Renda_Dependente_Irrf (seção 16).          

  **Cad_Participante_Historico_Salario              Liga o histórico salarial ao step da tabela salarial     *Fase 0, revisão 33
  (ID_Step_Tabela_Salarial,                         (seção 19), quando a empresa usa o recurso.              --- patch construído
  Justificativa_Fora_Tabela)**                                                                               nesta consolidação*

  **Cad_Rh_Cargo (ID_Grupo_Tabela_Salarial)**       Classifica o cargo dentro de um grupo ocupacional da     *Fase 5, seção 2 ---
                                                    tabela salarial (seção 19) --- organizacional, não       patch construído
                                                    determina os steps do cargo.                             nesta consolidação*

  **Mov_Titulo                                      Resolve o favorecido do título para                      *Fase 2 --- Contas a
  (Natureza_Titulo_Folha=pensao_alimenticia)**      Cad_Rh_Pensao_Alimenticia.ID_Participante_Pensionista    Pagar/Receber, sem
                                                    (seção 18), via Mov_Rh_Folha_Item.ID_Origem_Ocorrencia   mudança estrutural
                                                    (seção 5) --- mesmo mecanismo já usado para óbito, agora naquele documento*
                                                    suportando 2+ pensionistas simultâneos do mesmo          
                                                    colaborador.                                             

  **Cad_Documento_Vinculo (GED)**                   Reaproveitado nesta revisão para os documentos           *Fase 0, seção 11 ---
                                                    comprobatórios de dependente anexados a                  reaproveitado, sem
                                                    Mov_Rh_Solicitacao_Dependente (seção 18) e para a        mudança estrutural*
                                                    motivação formal de dispensa em empresa pública/SEM      
                                                    (Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal,      
                                                    seção 3) --- mesmo mecanismo já usado no resto do        
                                                    módulo, sem campo novo.                                  

  **Cad_Participante_Dados_Pessoa_Fisica /          Dados pessoais que o S-2200 exige do trabalhador (estado *Fase 0, revisão 45*
  Cad_Participante_Deficiencia /                    civil, grau de instrução, nascimento, deficiência com    
  Cad_Participante_Estrangeiro**                    data de início de cada uma, condição de estrangeiro).    
                                                    Dado de saúde e de origem racial é dado sensível         
                                                    (Cad_Dado_Sensivel).                                     

  **Cad_Usuario_Escopo**                            Substitui Cad_Rh_Escopo_Usuario (seção 14), com Modulo = *Fase 0, revisão 45*
                                                    folha_rh e a vigência que faltava.                       

  **Cad_Processo (Fase 8 --- Jurídico)**            Cad_Rh_Pensao_Alimenticia.ID_Processo_Judicial e         *Fase 8 --- Jurídico,
                                                    Mov_Rh_Processo_Trabalhista apontam para o processo do   revisão 1*
                                                    Jurídico; Cad_Rh_Processo_Administrativo_Judicial foi    
                                                    aposentada. O S-1070 usa Mov_Processo_Suspensao.         

  **Mov_Aprovacao_Instancia                         As faixas do INSS e do IRRF e os parâmetros do IRRF      *Fase 0, revisão 45*
  (Origem_Tipo=validacao_dado_legal)**              entram provisórios e são validados pelo RH e pelo        
                                                    contador antes de fechar a folha real (Fase 0, seção 9). 

  **Cad_Certificado_Digital**                       Mov_Esocial_Evento.ID_Certificado registra o certificado *Fase 8 --- Jurídico,
                                                    que assinou cada envio.                                  revisão 1*

  **Mov_Titulo (Origem_Tipo=processo_trabalhista)** O pagamento de condenação ou acordo trabalhista vira     *Fase 2 --- Contas a
                                                    título a pagar e baixa a provisão.                       Pagar/Receber,
                                                                                                             revisão 12*
  ------------------------------------------------- -------------------------------------------------------- ---------------------

22\. Notas para a sua revisão

Mesma lógica dos documentos anteriores: estas são decisões técnicas que
assumi por conta própria para fechar uma estrutura concreta --- nenhuma
está travada.

-   Este é o primeiro módulo do dicionário dedicado inteiramente a
    compliance com um órgão externo (eSocial) --- segui o mesmo critério
    já maduro no resto do projeto para obrigação acessória (SPED, Reinf,
    DCTFWeb em Contabilidade & Fiscal): a ESTRUTURA de dados e o
    rastreio de envio/retorno são modelados aqui; o leiaute XML de cada
    evento específico, a certificação digital e o ambiente de
    transmissão (homologação/produção) ficam para a camada de aplicação
    --- mesmo padrão já usado para CNAB/API em Tesouraria.

-   Mov_Rh_Ficha_Evento.Detalhe (seção 12) ficou como texto livre nesta
    revisão, cobrindo os cinco tipos de evento (exame, vacina,
    afastamento, viagem, acidente) com uma única estrutura genérica ---
    um evento como acidente de trabalho (CAT, S-2210) tem, na prática,
    campos próprios mais ricos (agente causador, houve afastamento, CID,
    houve óbito) que hoje entram todos dentro de Detalhe; se a Mlegate
    precisar de telas estruturadas por tipo, é uma extensão natural
    (campos específicos por Cad_Rh_Tipo_Evento_Ficha), sem mudar o
    princípio genérico da entidade.

-   Cad_Rh_Verba.Formula (seção 5) ficou como texto livre, sem uma
    linguagem de expressão estruturada nem parser definido neste
    dicionário --- mesmo critério já usado alhures para regra livre não
    estruturada (ex.: Mov_Ordem_Producao_Stakeholder.Papel, Produção). A
    detecção de dependência circular entre verbas, que o Documento
    Analítico já exigia, é responsabilidade da camada de aplicação ao
    avaliar a Formula, não uma validação que a estrutura de dados
    garanta sozinha.

-   PLR (Tipo_Folha=plr, Mov_Rh_Folha_Apuracao, seção 5) reaproveita o
    mesmo motor de Cad_Rh_Verba/Mov_Rh_Folha_Item das demais folhas ---
    a fórmula de elegibilidade e de cálculo do PLR em si (por resultado
    da empresa, por meta individual, por tempo de casa) não foi modelada
    como estrutura própria: fica dentro de Cad_Rh_Verba.Formula, como
    qualquer outra verba, já que cada empresa negocia PLR de forma
    diferente (acordo coletivo, comissão de negociação) e não há um
    padrão único a fixar aqui.

-   Mov_Lote_Lancamento.Origem_Tipo (Fase 0, revisão 28) ganhou
    folha_pagamento e provisao_ferias_decimo_terceiro nesta
    consolidação; a liquidação de pagamento_autonomo (seção 5) segue o
    mesmo gancho (Origem_Tipo=folha_pagamento), sem um valor próprio ---
    é uma Mov_Rh_Folha_Apuracao como outra qualquer para fins contábeis.

-   Cad_Motor_Regra de Área de Negócio=folha_pagamento (seção 5) resolve
    conta_contabil_debito/conta_contabil_credito por critérios verba_rh
    e departamento --- optei por reaproveitar o motor genérico em vez de
    uma nova entidade Cad_Rh_Verba_Regra_Contabil, que chegou a ser
    cogitada; ponto de atenção para sua confirmação: se no dia a dia a
    combinatória de regras por verba+departamento crescer muito, pode
    valer revisitar se uma tabela dedicada, mais rápida de consultar em
    massa no fechamento de folha, compensaria a perda de
    reaproveitamento do motor único.

-   Cad_Rh_Turno.Arredondamento_Minutos (seção 6) assume que o
    arredondamento é uma propriedade do TURNO, não uma configuração
    única da empresa nem do banco de horas em si --- decisão minha, já
    que Alberto só definiu o valor inicial (5 minutos) sem especificar o
    nível de configuração; se a intenção for um único parâmetro por
    empresa, é uma simplificação possível.

-   Cad_Usuario_Escopo (seção 14) cobre o RECORTE de dado
    (filial/departamento), não a AÇÃO --- mesma distinção já usada em
    Cad_Usuario_Escopo (Estoque); controle de campo sensível dentro do
    módulo (ex.: quem vê salário) fica fora deste dicionário lógico,
    camada de aplicação.

-   Aprovação de contratação (verba orçamentária), citada no Documento
    Analítico (\"a contratação de pessoal também empenha verba, e a
    Folha compromete automaticamente os meses seguintes após a
    efetivação da contratação\") não ganhou um Origem_Tipo próprio em
    Mov_Aprovacao_Instancia nesta revisão --- o gancho já existe no lado
    de Planejamento & Orçamento (Mov_Compromisso_Orcamentario), mas o
    EVENTO que dispara esse compromisso a partir de uma admissão
    (Cad_Vinculo_Emprego, seção 3) ainda não foi formalizado; fica como
    ponto de atenção para uma próxima rodada.

-   RESOLVIDO na revisão 4: Cad_Vinculo_Emprego.Tipo_Vinculo (seção 3)
    ganhou intermitente, safrista e cooperado como valores próprios,
    substituindo a nota anterior que os deixava implícitos dentro de
    \"clt\".

-   Mov_Rh_Base_Acumulada_Migrada e o Origem_Tipo=migracao (seção 9) não
    têm, nesta revisão, uma tela de conciliação/validação entre o que
    foi migrado e o que o sistema passa a calcular dali para frente
    (ex.: garantir que a base de IRRF acumulada migrada mais o que o
    sistema novo apura no ano batem com o informe de rendimentos ao
    final do ano-calendário) --- fica como ponto de atenção para quando
    a migração de fato acontecer, não uma lacuna estrutural.

-   RESOLVIDO na revisão 4:
    Mov_Rh_Banco_Horas_Movimento.Data_Limite_Compensacao (seção 7)
    modela o prazo legal de compensação (art. 59 §§2º-3º CLT), com
    débito automático incondicional no vencimento --- substitui a nota
    anterior que deixava isso como decisão de processo não estrutural.
    Quem decide o destino pago x banco de horas de cada hora extra (RH,
    gestor, ou o próprio colaborador) continua sendo decisão de processo
    da Mlegate, não estrutural.

-   Cad_Rh_Condicao_Risco.Percentual (seção 13) fica como valor de
    referência, não uma fórmula --- o cálculo efetivo do adicional (ex.:
    percentual sobre salário mínimo, sobre salário base, ou sobre o
    maior deles, conforme o tipo de condição) é resolvido dentro da
    Formula da Cad_Rh_Verba associada (ID_Verba), mesmo critério de
    parametrização livre já usado no resto do motor de folha.

-   Mov_Rh_Folha_Apuracao.Tipo_Folha=pagamento_autonomo (seção 5)
    reaproveita o mesmo Cad_Vinculo_Emprego/Tipo_Vinculo=autonomo já
    existente --- não modela nota fiscal/recibo (RPA) como documento
    próprio nem a eventual retenção de ISS municipal, que ficam fora do
    escopo deste dicionário de RH (mais próximos de Compras/Contas a
    Pagar, se a Mlegate preferir tratar autônomo como fornecedor de
    serviço em vez de folha).

-   Revisão 4 --- pontos de placement decididos por conta própria, sem
    confirmação explícita de Alberto item a item: Cad_Processo (Fase 8
    --- Jurídico) ficou neste módulo, não em Fase 0, por ser
    especificamente ligado à suspensão de recolhimento de INSS/FGTS/IRRF
    de um vínculo; se a Mlegate precisar do mesmo controle para outros
    tributos fora da folha, vale reavaliar se deveria migrar para Fase
    0/Contabilidade & Fiscal.

-   Cad_Vinculo_Emprego.Motivo_Exclusao_Jornada (seção 3) é uma
    enumeração fechada {cargo_confianca, atividade_externa,
    teletrabalho_tarefa} --- cobre os três casos do art. 62 CLT
    identificados na pesquisa; um enquadramento futuro não previsto
    exigiria extensão do domínio.

-   Cad_Rh_Ambiente_Trabalho e Mov_Rh_Vinculo_Ambiente (seção 13)
    modelam a hierarquia ambiente→fator de risco→vínculo exigida pelo
    eSocial (S-1060/S-2240/S-2241) como um terceiro eixo, somado a cargo
    e área --- não substituem os dois já existentes; se no uso real o
    ambiente sempre coincidir 1:1 com a área/departamento, pode valer
    simplificar para um único eixo numa revisão futura.

-   Cad_Rh_Declaracao_Transparencia_Salarial e Cad_Rh_Plano_Acao_Equidade
    (seção 15) modelam só a estrutura mínima de compliance com a Lei
    14.611/2023 --- não replicam o layout exato do questionário do
    Portal Emprega Brasil (que muda por instrução normativa), mesmo
    critério já usado para eSocial (seção 10) e demais obrigações
    acessórias deste projeto.

-   Revisão 5 --- abono de falta/atraso (Mov_Rh_Ponto_Abono, seção 6):
    deliberadamente sem régua de aprovação, a pedido de Alberto, por
    conta dos vários níveis de gestor independentes; a validação de que
    ID_Gestor_Abono é de fato gestor do vínculo abonado fica com a
    camada de aplicação, consultando Cad_Vinculo_Emprego.ID_Gestor ---
    não travada estruturalmente aqui, mesmo critério já usado para
    outras regras de hierarquia neste dicionário (ex.: visão de banco de
    horas do gestor, seção 7).

-   Revisão 5 ---
    Cad_Rh_Motivo_Desligamento.Multa_Atraso_Pagamento_Aplicavel
    (seção 3) fixa hoje só o caso de óbito como falso; se a Mlegate
    identificar outro motivo de desligamento cuja jurisprudência também
    afaste a multa do art. 477 §6º, é só marcar o campo, sem mudança
    estrutural.

-   Revisão 5 --- Mov_Rh_Ficha_Evento.Tipo_Cat/ID_Evento_Ficha_Origem
    (seção 12) ficaram, como o Detalhe já era antes (revisão 1), campos
    genéricos aplicáveis só a um subconjunto de eventos (acidente de
    trabalho) dentro de uma entidade que cobre cinco tipos --- mesma
    decisão de design já registrada nas Notas da revisão 1: se a Mlegate
    precisar de telas estruturadas por tipo de evento, é extensão
    natural, sem mudar o princípio genérico da entidade.

-   Revisão 5 --- visibilidade de RH sobre pagamento não processado
    (seção 14) foi modelada como consulta derivada cruzando Folha & RH,
    Contas a Pagar/Receber e Tesouraria, sem tabela ou campo de status
    dedicado; se no uso real o volume de folhas grandes tornar essa
    consulta pesada de rodar em tempo real, pode valer revisitar uma
    view materializada ou cache de leitura --- decisão de performance de
    aplicação, não de estrutura.

-   Revisão 5 --- Cad_Vinculo_Emprego.Qualificacao_Recebedor (seção 3)
    cobre os três casos mais comuns de recebimento de verba rescisória
    por óbito (dependente habilitado, herdeiro por alvará,
    inventariante); um caso menos comum (ex.: sucessão testamentária
    litigiosa) cairia hoje em nenhum dos três valores --- ponto de
    atenção para uma extensão futura do domínio, se a Mlegate encontrar
    esse cenário na prática.

-   RESOLVIDO na revisão 6: o evento de aprovação de contratação que
    formaliza o compromisso orçamentário citado no Documento Analítico,
    deixado em aberto desde a revisão 4 ---
    Cad_Rh_Vaga.ID_Instancia_Aprovacao (Origem_Tipo=abertura_vaga, régua
    opcional) e ID_Compromisso_Orcamentario (referência direta a
    Mov_Compromisso_Orcamentario, Planejamento & Orçamento), seção 2.

-   Revisão 6 --- Mov_Rh_Vaga_Candidato_Etapa.Resultado (seção 2) é
    decidido pelo RH considerando os pareceres/recomendações individuais
    de cada avaliador (Mov_Rh_Vaga_Candidato_Etapa_Avaliador), mas não
    há regra estrutural de como essas recomendações se combinam
    (maioria, unanimidade, peso do entrevistador mais sênior) ---
    decisão de processo da Mlegate, não travada aqui, mesmo critério já
    usado para outras decisões que \"sugerem, nunca aplicam
    automaticamente\".

-   Revisão 6 --- Cad_Rh_Politica_Retencao_Candidato.Meses_Retencao
    (seção 2) não tem piso nem teto travado na estrutura, por pedido
    explícito de Alberto (parâmetro livre da empresa); o alerta de LGPD
    acima de 24 meses é só informativo, não bloqueante --- se a Mlegate
    quiser, no futuro, impedir a configuração acima de um teto, é uma
    regra de validação a acrescentar na camada de aplicação, não uma
    mudança estrutural.

-   Revisão 6 --- checklist de documentos de contratação
    (Cad_Rh_Checklist_Documento/Mov_Rh_Candidato_Documento, seção 2): a
    instanciação automática dos itens na aprovação da etapa final e o
    bloqueio de conversão por item obrigatório pendente são descritos
    como comportamento de aplicação, não validação estrutural --- mesmo
    critério já usado para outras regras de negócio deste dicionário que
    dependem de sequência de eventos, não de constraint de banco.

-   Revisão 7 ---
    Cad_Rh_Criterio_Avaliacao_Desempenho.Nota/Mov_Rh_Avaliacao_Desempenho_Avaliador_Nota.Nota
    (seção 4) não têm escala fixa nesta estrutura (ex.: 0-10, 0-100,
    1-5) --- fica como parâmetro de aplicação, mesmo critério já usado
    para Cad_Rh_Criterio_Avaliacao na seleção (seção 2); o que a
    estrutura garante é o Peso por critério/meta e o armazenamento da
    nota, não a régua de pontuação em si.

-   Revisão 7 --- a fórmula exata de composição de
    Mov_Rh_Avaliacao_Desempenho.Nota_Final_Ponderada (seção 4) --- como
    as notas de critério individual, de critério de grupo e o percentual
    de atingimento de meta se combinam num único número, ponderadas
    pelos pesos de Cad_Rh_Criterio_Avaliacao_Desempenho e
    Cad_Rh_Meta_Desempenho --- é comportamento de aplicação descrito,
    não uma fórmula travada na estrutura; mesmo critério já usado para
    Cad_Rh_Verba.Formula (seção 5) e para a elegibilidade de PLR.

-   Revisão 7 --- Tipo_Avaliador em
    Mov_Rh_Avaliacao_Desempenho_Avaliador (seção 4) é uma enumeração
    fechada {gestor, propria}, diferente do modelo de avaliadores em
    número livre já usado na seleção
    (Mov_Rh_Vaga_Candidato_Etapa_Avaliador, seção 2) --- decisão
    deliberada, já que Alberto especificou só avaliação do gestor e
    autoavaliação; se no futuro entrar avaliação 360º (pares,
    subordinados), o domínio do enum precisa de extensão.

-   Revisão 7 --- Mov_Rh_Avaliacao_Desempenho_Grupo_Nota (seção 4) grava
    uma única nota por ciclo+departamento+critério de grupo, sem uma
    linha própria por colaborador --- a aplicação dessa nota de grupo a
    cada vínculo do departamento na composição da Nota_Final_Ponderada
    individual é comportamento de aplicação, não uma cópia armazenada
    por colaborador, mesmo princípio de \"nunca armazenar o que pode ser
    derivado\" já usado no resto do projeto.

-   Revisão 7 --- Cad_Rh_Meta_Desempenho.Tipo_Alvo={cargo} (seção 4)
    permite meta por função em vez de por colaborador nomeado; quando o
    alvo é cargo, Mov_Rh_Meta_Desempenho_Resultado continua sendo
    lançado por vínculo (ID_Vinculo) --- é a aplicação, na hora do
    resultado, que resolve quais vínculos ocupam aquele Cad_Rh_Cargo
    (seção 2) no período do ciclo, não uma referência estrutural direta
    cargo→resultado.

-   Revisão 7 --- a seção 4 foi posicionada logo após Colaborador e
    Vínculo de Emprego e antes de Verbas e Motor de Cálculo de Folha,
    por decisão própria, já que Nota_Final_Ponderada e
    Percentual_Atingido de meta são candidatos naturais a critério de
    elegibilidade de PLR (Cad_Rh_Verba.Formula, seção 5) --- nenhum
    vínculo estrutural entre as duas seções foi criado nesta revisão;
    fica como extensão natural se a Mlegate quiser condicionar PLR a
    desempenho.

-   Revisão 8 --- Cad_Rh_Verba_Tipo_Vinculo (seção 5) foi modelada
    deliberadamente SEM vigência própria, ao contrário de Cad_Rh_Verba
    --- mudar a elegibilidade por tipo de vínculo é uma correção de
    cadastro, não uma mudança de regra de cálculo que precise preservar
    o histórico de folhas já apuradas; decisão própria, sem confirmação
    explícita de Alberto sobre esse ponto específico.

-   Revisão 8 --- Cad_Rh_Verba.Ordem_Calculo é recalculada pela
    aplicação sempre que QUALQUER Formula da empresa muda, não só a da
    verba alterada --- mesmo quando a mudança parece isolada, a ordem
    topológica de todo o grafo de dependências da empresa pode ser
    afetada (uma verba nova pode se inserir no meio de uma cadeia já
    existente); a estrutura não trava a granularidade exata desse
    recálculo (por empresa inteira vs. só o subgrafo afetado), decisão
    de performance de aplicação.

-   Revisão 8 (referência estrutural atualizada na revisão 13) --- o
    controle de período da folha nasce independente do período contábil,
    mas a estrutura não trava nenhuma ORDEM ou dependência entre os dois
    fechamentos (ex.: impedir fechar contabilmente uma competência cuja
    folha ainda está aberta) --- Alberto foi explícito que a folha
    precisa fechar primeiro, mas isso fica como regra de
    processo/aplicação a documentar, não uma validação cruzada garantida
    pela estrutura de dados; ponto que segue válido após a migração da
    revisão 13 para Cad_Periodo_Fechamento_Filial
    (Bloco=\"folha_pagamento\" vs Bloco=\"contabilidade\") --- a
    estrutura genérica também não trava essa ordem entre blocos.

-   Revisão 13 --- a migração de Cad_Rh_Periodo_Folha para o mecanismo
    genérico (Cad_Periodo_Fechamento_Filial, Bloco=\"folha_pagamento\",
    Fase 0 seção 10) é puramente estrutural, sem mudança de regra de
    negócio; um eventual histórico externo que referenciasse o antigo
    ID_Periodo_Folha precisaria ser remapeado para o novo
    ID_Periodo_Filial na migração de dados real --- decisão de
    implementação/carga de dados, não de estrutura deste dicionário.

-   Revisão 9 --- Cad_Rh_Categoria_Sindical (seção 16) foi modelada
    deliberadamente SEM vigência própria --- uma troca de sindicato
    (recadastramento sindical) é evento raro o bastante para ser tratado
    como correção de cadastro, não como histórico versionado; decisão
    própria, sem confirmação explícita de Alberto sobre esse ponto
    específico. Se a Mlegate precisar auditar qual sindicato regia um
    vínculo numa data passada especificamente por troca de
    recadastramento (distinto de mudança de cargo/filial, que já
    preservam a categoria efetiva através de Cad_Rh_Cargo/Cad_Filial
    vigentes à época), é uma extensão futura possível.

-   Revisão 9 --- Cad_Rh_Reajuste_Coletivo_Faixa (seção 16) resolve a
    faixa salarial pelo salário ANTES do reajuste (Valor_Salario vigente
    no momento da aplicação) --- a estrutura não trava o que acontece
    quando um reajuste percentual empurra um salário de uma faixa para a
    seguinte dentro do mesmo evento de aplicação; comportamento de
    aplicação a confirmar com Alberto se a Mlegate tiver esse caso de
    borda na prática.

-   Revisão 9 --- Cad_Rh_Salario_Minimo (seção 16): a proporcionalidade
    do piso para aprendiz (jornada reduzida) não ganhou campo ou fórmula
    própria nesta revisão --- fica inteiramente como comportamento de
    aplicação sobre a jornada contratual do vínculo, mesmo critério de
    parametrização livre já usado no resto do motor de folha; se a
    Mlegate quiser auditar esse cálculo especificamente, pode valer
    registrar a jornada de referência usada em cada ajuste.

-   Revisão 9 --- Mov_Rh_Beneficio_Taxa_Global.Tipo {taxa, desconto}
    (seção 17) é nomenclatura minha para os dois casos que Alberto
    descreveu (\"isto também vale quando tem desconto global\") --- a
    direção efetiva do lançamento contábil fica inteiramente a cargo da
    regra própria de cada verba informativa no Motor de Regras, não
    deste campo; decisão própria de rotulagem, sem confirmação explícita
    de Alberto sobre os nomes.

-   Revisão 9 --- Cad_Rh_Motivo_Desligamento.Gera_Verbas_Rescisorias
    (seção 3) generaliza, para óbito e transferência de grupo econômico,
    um comportamento que antes só existia implícito para óbito (via
    Multa_Atraso_Pagamento_Aplicavel=falso) --- decisão própria de
    tornar explícito e extensível a outros motivos futuros que a Mlegate
    identifique, sem mudança de comportamento para os motivos já
    existentes.

-   Revisão 9 --- a resolução do enquadramento sindical de um vínculo
    (cargo, senão filial, seção 16) é sempre uma consulta em tempo de
    aplicação de reajuste --- não há um campo de categoria sindical
    armazenado diretamente em Cad_Vinculo_Emprego, mesmo princípio
    \"nunca armazenar o que pode ser derivado\" já usado em toda a
    estrutura; se a Mlegate precisar consultar esse enquadramento com
    muita frequência fora do momento de reajuste, pode valer avaliar
    cache de leitura, decisão de performance de aplicação, não de
    estrutura.

-   Revisão 10 --- Mov_Rh_Ferias_Gozo (seção 8) passou a nascer como
    solicitação do colaborador, com fluxo simplificado de duas etapas
    (gestor + RH), por instrução explícita de Alberto de NÃO usar o
    motor genérico Cad_Regua_Aprovacao (Fase 0) --- \"tem a questão de
    tipo de aprovadores bem diferente\". Só férias/dependentes ganharam
    esse fluxo; se no futuro outro processo do portal precisar de
    aprovação, cabe reavaliar se o motor genérico passa a compensar a
    simplicidade do fluxo fixo.

-   Revisão 10 --- Mov_Rh_Solicitacao_Dependente (seção 18) tem só uma
    etapa de validação (RH), confirmado por Alberto;
    ID_Dependente_Gerado liga a solicitação ao registro definitivo, mas
    a estrutura não trava que os dados efetivados sejam idênticos aos
    pré-preenchidos --- o RH pode ajustar, decisão própria já registrada
    no texto da entidade.

-   Revisão 10 --- Cad_Rh_Pensao_Alimenticia.Base_Calculo (seção 18)
    ficou como enumeração aberta de referência {remuneracao_total,
    salario_base, outro}, sem uma fórmula estruturada --- mesmo critério
    já usado para Cad_Rh_Verba.Formula (seção 5); o cálculo efetivo de
    cada pensão é resolvido dentro da Formula da verba de desconto
    correspondente.

-   Revisão 10 --- Mov_Rh_Folha_Item.ID_Origem_Ocorrencia (seção 5) foi
    desenhado de propósito genérico (identificador solto, não uma
    referência tipada a Cad_Rh_Pensao_Alimenticia) para servir, sem
    mudança estrutural, a qualquer necessidade futura semelhante de
    múltiplas ocorrências da mesma verba (ex.: consignado com múltiplos
    contratos/credores) --- decisão própria de generalização, sem
    confirmação item a item de Alberto sobre casos além de pensão
    alimentícia.

-   Revisão 10 --- Cad_Rh_Tabela_Salarial_Grupo (seção 19) ficou como
    classificação organizacional livre (texto), sem lista fechada de
    grupos --- os quatro exemplos de Alberto (executivos/diretoria,
    administrativo, universitários, operacional) são só isso, exemplos;
    a empresa cadastra os grupos que quiser.

-   Revisão 10 --- Cad_Rh_Tabela_Salarial_Step (seção 19) não modela
    progressão automática entre steps (ex.: por tempo de casa ou
    avaliação de desempenho) --- a mudança de step de um colaborador
    nasce como uma linha comum em Cad_Participante_Historico_Salario
    (Fase 0), decisão manual de RH/gestor a cada evento, mesmo critério
    já usado para qualquer alteração salarial individual.

-   Revisão 10 --- Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal
    (seção 3) cobre só o cenário de empresa pública/sociedade de
    economia mista (Súmula 390 TST + RE 688.267 STF); o segundo cenário
    levantado na mesma pesquisa --- administração direta/autarquias com
    servidor estatutário, Regime Jurídico Único --- RESOLVIDO na revisão
    12: nova seção 20, Regime Estatutário (RJU), com as 13 frentes então
    levantadas desenhadas e construídas.

-   Revisão 12 --- Cad_Rh_Estagio_Probatorio.Status (seção 20) não
    trava, na estrutura, quantas avaliações periódicas
    (Mov_Rh_Estagio_Probatorio_Avaliacao) são exigidas antes da
    homologação, nem a regra de como pareceres desfavoráveis levam a
    Status=exonerado --- decisão de processo de cada ente, conforme seu
    próprio estatuto, mesmo critério \"sugere, nunca aplica
    automaticamente\" já usado em todo o dicionário.

-   Revisão 12 --- Cad_Vinculo_Emprego.Modelo_Remuneracao=subsidio
    (seção 20) não modela estruturalmente QUAIS exceções legais permitem
    somar outra verba a um subsídio --- fica como validação de aplicação
    sobre Cad_Rh_Verba_Tipo_Vinculo (seção 5), decisão própria, sem
    confirmação item a item de Alberto sobre a lista de exceções.

-   Revisão 12 --- Mov_Rh_Processo_Disciplinar (seção 20) não liga
    estruturalmente Penalidade_Aplicada=demissao ao
    Cad_Rh_Motivo_Desligamento \"Demissão (PAD)\" correspondente por uma
    referência formal --- a ligação é descrita como comportamento de
    aplicação, mesmo critério já usado alhures para eventos que se
    combinam por regra de negócio, não por constraint de banco (ex.:
    checklist de documentos de contratação, seção 2).

-   Revisão 14 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): datas de validade padronizadas para o
    trio de vigência (Cad_Rh_Salario_Adicional, Cad_Rh_Tabela_Salarial,
    Cad_Rh_Salario_Minimo, Cad_Rh_Limite_Renda_Dependente_Irrf,
    Mov_Rh_Beneficio_Adesao_Contribuicao,
    Mov_Rh_Estabilidade_Provisoria, Cad_Rh_Pensao_Alimenticia);
    Cad_Rh_Categoria_Sindical com vigência; Base_Calculo_Tipo e
    Parecer_Resultado renomeados; competência na taxa global de
    benefício; chaves primárias de nove entidades; CNPJ do sindicato
    alfanumérico. A convenção completa (vigência, identidade + versão,
    sucessão de códigos oficiais, competência, CNPJ alfanumérico, um
    campo por informação, saldos guardados de período fechado, sequência
    de fechamento) vive na Fase 0, seções 2 e 10 (revisão 41).

-   Revisão 15 --- tipo lógico \"código (n)\" definido por Alberto ---
    todo campo que identifica algo (inscrição, documento, agência,
    conta, número e série de nota, matrícula, código oficial) é
    caractere, nunca numérico: os zeros à esquerda fazem parte do
    código, e o padrão pode passar a aceitar letras ou mudar de tamanho,
    como aconteceu com o CNPJ alfanumérico. Campos revistos: CPF,
    Codigo, Matricula, Matricula_Esocial, Numero_Processo,
    Numero_Recibo, Sindicato_Cnpj. Competência de Mov_Rh_Folha_Apuracao
    e Mov_Rh_Base_Acumulada_Migrada no tipo competência (resíduo do
    Bloco 1). Convenção completa na Fase 0, seção 2.6 (revisão 42).

-   Revisão 16 --- tabelas progressivas do INSS e do IRRF com faixas,
    vigência e ato legal (Cad_Rh_Tabela_Progressiva, \_Faixa e
    Cad_Rh_Parametro_Irrf) e valores iniciais provisórios até a
    validação de RH e contador; rubrica alinhada ao S-1010
    (Codigo_Rubrica, natureza e quatro códigos de incidência oficiais em
    Cad_Rh_Codigo_Incidencia, com Incide_Inss, Incide_Fgts e Incide_Irrf
    calculados e armazenados; ID_Rubrica_Esocial e o domínio
    rubrica_esocial aposentados); estabelecimento (S-1005) e lotação
    tributária (S-1020, com terceiros e histórico de lotação do
    vínculo); processo trabalhista completo do S-2500 e do S-2501 (21
    entidades: contrato, observações, remuneração, mudança de categoria,
    unicidade, abono, período, trabalho intermitente, apuração por
    trabalhador, base, tributo, imposto de renda, advogados, dedução por
    dependente, pensão alimentícia e retenção suspensa; 15 acrescentadas
    na consolidação, depois da conferência com o XSD oficial, que também
    corrigiu a remuneração, a origem do processo e a chave do processo
    trabalhista), com juízo da decisão apontando para a movimentação do
    processo; validação de esquema e certificado em Mov_Esocial_Evento;
    Cad_Rh_Escopo_Usuario e Cad_Rh_Processo_Administrativo_Judicial
    aposentadas (substituídas por Cad_Usuario_Escopo e Cad_Processo);
    Mov_Rh_Processo_Disciplinar.ID_Processo renomeado
    ID_Processo_Disciplinar;
    Cad_Rh_Pensao_Alimenticia.ID_Processo_Judicial aponta para
    Cad_Processo; Cad_Rh_Reajuste_Coletivo.ID_Documento corrigido para
    Cad_Documento. Desenho aprovado e histórico do bloco nos documentos
    20 e 22 do Projeto.

23\. Próximo Passo

*Esta Revisão 10 (\"consolidar\") fechou uma rodada extensa de temas
pedidos por Alberto, construída junto com o patch em Fase 0 (revisão
33): (1) Cad_Rh_Verba_Filial (seção 5) --- restrição opcional de verba
por filial, mesmo padrão \"sem linha = sem restrição\" de
Cad_Rh_Verba_Tipo_Vinculo, combinável com ele; (2)
Mov_Rh_Folha_Item.ID_Origem_Ocorrencia (seção 5) --- generaliza o grão
da folha para suportar mais de uma ocorrência da mesma verba por
vínculo/apuração, viabilizando múltiplos pensionistas simultâneos; (3)
nova seção 18, Portal do Colaborador --- holerite e ponto por autoacesso
sem estrutura nova; pedido de férias com fluxo simplificado de duas
etapas (gestor + validação final do RH, Cad_Rh_Politica_Ferias com prazo
mínimo de antecedência, Urgente/Justificativa_Urgencia obrigatória);
solicitação de inclusão de dependente com validação só por RH
(Mov_Rh_Solicitacao_Dependente); e pensão alimentícia com 2 ou mais
pensionistas simultâneos por colaborador, data de saída prevista
sinalizando revisão humana (não corte automático) e redirecionamento por
falecimento do pensionista --- para pessoa nova ou para outro
pensionista já na lista (Cad_Rh_Pensao_Alimenticia); (4)
Cad_Participante_Dependente (Fase 0, revisão 33) reformulado a partir de
pesquisa extensa sobre critérios legais de dependente --- IRPF, INSS e a
terceira base legal independente do salário-família (corte de 14 anos,
comprovação anual de vacinação/frequência escolar), unificadas pela
Tabela 7 do eSocial (novo domínio tipo_dependente_esocial); teto de
renda de ascendente para IRRF como parâmetro nacional
(Cad_Rh_Limite_Renda_Dependente_Irrf, seção 16) e regras de dependente
por operadora de benefício como lista positiva
(Cad_Rh_Beneficio_Regra_Dependente, seção 17), fechando os dois pontos
que Alberto recusou deixar como julgamento manual do RH; (5)
Cad_Rh_Motivo_Desligamento.Exige_Motivacao_Formal (seção 3) --- pequena
extensão para empresa pública/sociedade de economia mista (Súmula 390
TST/RE 688.267 STF), da pesquisa sobre folha para concursados; e (6)
nova seção 19, Tabela Salarial --- recurso opcional por empresa, cargo ×
step com valor fixo por degrau (não faixa), quantidade de steps livre
por cargo, grupo ocupacional como classificação organizacional (não dona
da escada de steps), com justificativa obrigatória quando o salário
diverge da tabela.*

*Revisão 13: migração do controle de período de fechamento da folha para
o mecanismo genérico construído na Fase 0 (revisão 37), a pedido de
Alberto para todos os módulos do dicionário (\"pode migrar para um
mecanismo generalizado porém indicando os blocos e teria que ter para
todos os módulos\"). Cad_Rh_Periodo_Folha (seção 5, revisão 8) é
APOSENTADO como cadastro próprio --- a folha passa a ser a instância
Cad_Bloco_Fechamento.Codigo=\"folha_pagamento\" de
Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial (Fase 0, seção 10),
e Mov_Rh_Folha_Apuracao (seção 5) passa a consultar essa tabela
genérica, pelo par Filial+Competência, em vez do antigo cadastro
dedicado. É uma migração PURAMENTE ESTRUTURAL: nenhuma regra de negócio
muda --- a folha continua deliberadamente independente do período
contábil (agora simplesmente por serem blocos diferentes, sem relação de
causa/efeito entre eles), continua por filial, e continua fail-closed
(nenhuma competência sem registro é tratada como aberta por omissão),
exatamente como pedido por Alberto desde a revisão 8. Menções cruzadas
atualizadas: a entidade em si (seção 5), a dependência de
Mov_Rh_Folha_Apuracao (seção 5), a linha da tabela de conexões com a
Fase 0 (seção 21) e a nota sobre ausência de ordem estrutural entre os
fechamentos de folha e contábil (seção 22) --- todas preservando o
racional histórico de independência já registrado, só corrigindo a
referência estrutural.*

*Revisão 12 (\"Regime Estatutário\"): fechou o ponto sinalizado desde a
revisão 10 --- o regime de servidor estatutário (administração
direta/autarquias/fundações públicas, Regime Jurídico Único), um SEGUNDO
regime de folha em paralelo ao CLT, não uma extensão pontual do que já
existia. Nova seção 20, com as 13 frentes então levantadas desenhadas e
construídas: (1) Tipo_Vinculo (seção 3) ganhou
estatutario_efetivo/cargo_comissionado/temporario_administrativo/inativo_estatutario,
espelhando os códigos 301/302/306 do eSocial; (2) admissão em três
etapas --- Data_Nomeacao/Data_Posse/Data_Exercicio (seção 3), com
Data_Admissao passando a receber a data de Exercício e alerta (não
bloqueio) de prazo legal entre etapas; (3) estágio probatório com
avaliações periódicas, deliberadamente separado da avaliação de
desempenho comercial
(Cad_Rh_Estagio_Probatorio/Mov_Rh_Estagio_Probatorio_Avaliacao, seção
20); (4) Data_Estabilidade (seção 3), preenchida automaticamente ao
homologar o estágio; (5) motivos de vacância próprios do estatutário,
com Aplicavel_Regime {clt, estatutario, ambos}
(Cad_Rh_Motivo_Desligamento, seção 3); (6)/(7)/(9)/(11) FGTS isento,
previdência RPPS/evento S-1202, férias/13º e jornada reaproveitados sem
estrutura nova; (8) remuneração por subsídio ou verbas múltiplas
(Modelo_Remuneracao, seção 3) e Fundamento_Legal genérico em
Cad_Rh_Verba (seção 5); (10) processo disciplinar/PAD como entidade
própria, distinta da suspensão de tributos (Mov_Rh_Processo_Disciplinar,
seção 20); (12) Fundamento_Legal em Cad_Rh_Cargo (seção 2) e
Criterio_Progressao em texto livre em Cad_Rh_Tabela_Salarial_Step (seção
19), sem motor automático --- mesma decisão já registrada na revisão 10;
e (13) folha de inativos ---
Natureza_Inativo/ID_Vinculo_Origem_Aposentadoria (seção 3) e
Mov_Rh_Folha_Apuracao.Tipo_Folha=inativos (seção 5), separando
automaticamente ativos de inativos na apuração.*

*Revisão 9 (mantida abaixo): fechou uma rodada inteira de cinco temas
pedidos por Alberto, construída junto com o patch em Fase 0 (revisão
32): (1) transferência de colaborador entre filiais --- intra-empresa
(Cad_Participante_Historico_Filial, Fase 0, filial atual sempre
derivada) e inter-empresa do mesmo grupo econômico, com continuidade de
tempo de serviço preservada
(Cad_Vinculo_Emprego.ID_Vinculo_Origem_Transferencia; novo motivo de
desligamento transferencia_grupo_economico, sem verbas rescisórias); (2)
empréstimo temporário de colaborador entre departamentos e filiais, com
retorno automático ao vencer (Tipo_Alocacao/Data_Fim_Prevista, Fase 0),
custo caindo naturalmente na área que recebe via Motor de Regras; (3)
substituição de função com diferencial salarial explicitamente fixado,
não recalculado (Cad_Participante_Historico_Cargo.Valor_Diferencial,
Fase 0), aplicado por uma verba própria durante a janela de vigência;
(4) nova seção 16 --- categoria sindical com resolução por cargo/filial,
reajuste coletivo escalonável por faixa salarial e regional, e piso de
salário mínimo (nacional/estadual) como mecanismo automático e
independente do dissídio; (5) nova seção 17 --- catálogo de benefícios
com coparticipação fixa/percentual distinta por titular e dependente,
matching de contribuição para previdência privada, e taxa/desconto
global de operadora como terceira categoria de verba (informativo) que
não afeta o líquido do colaborador, rateada entre os aderentes por vidas
ou por valor, contando titular e dependentes cobertos.*

*Revisão 8 (mantida abaixo): fechou três pontos pedidos por Alberto
sobre Cad_Rh_Verba e a apuração de folha (seção 5): (1) amarração de
cada verba a um ou mais tipos de vínculo, marcação manual verba a verba,
sem restrição por omissão (Cad_Rh_Verba_Tipo_Vinculo); (2) sequência de
cálculo entre verbas determinada pela aplicação a partir do grafo de
dependências de Formula, e ARMAZENADA (Cad_Rh_Verba.Ordem_Calculo) ---
recalculada só quando alguma Formula muda, nunca durante a apuração em
si, evitando reprocessar o grafo a cada execução de folha; e (3)
controle de período aberto/fechado da folha por filial
(Cad_Rh_Periodo_Folha), deliberadamente independente do período contábil
de Fase 0 --- a folha precisa fechar primeiro, com calendário próprio
---, seguindo o princípio fail-closed que Alberto reforçou: ausência de
registro para uma competência é tratada como fechada, nunca como aberta
por omissão.*

*Revisão 7 (mantida abaixo): acrescentou a seção 4, Avaliação de
Desempenho, pedida por Alberto depois de ver a entrega da revisão 6 (\"o
que senti falta é a parte de avaliações periódicas de desempenho\").
Cobre: (1) catálogo próprio de critérios de avaliação, distinto do usado
na seleção, com Nivel_Pontuacao {individual, grupo} por critério
(Cad_Rh_Criterio_Avaliacao_Desempenho); (2) ciclos de avaliação
periódicos configuráveis por empresa, com status {planejado,
em_andamento, encerrado} (Cad_Rh_Ciclo_Avaliacao_Desempenho); (3)
avaliação por vínculo com dois avaliadores de papel fixo --- gestor e o
próprio colaborador (autoavaliação) ---, reaproveitando o padrão
multi-avaliador já usado na seleção
(Mov_Rh_Avaliacao_Desempenho/Avaliador/Avaliador_Nota); (4) pontuação de
critério de grupo lançada uma vez por ciclo+departamento, não por
colaborador (Mov_Rh_Avaliacao_Desempenho_Grupo_Nota); (5) metas
estruturalmente separadas dos critérios, por colaborador nomeado ou por
cargo, cada uma com peso próprio e resultado lançado por vínculo
(Cad_Rh_Meta_Desempenho/Mov_Rh_Meta_Desempenho_Resultado); e (6) uma
nota final ponderada por vínculo+ciclo, combinando critérios e metas
pelos pesos de cada catálogo, calculada uma vez e armazenada no
fechamento do ciclo, nunca recalculada silenciosamente se os pesos do
catálogo mudarem depois
(Mov_Rh_Avaliacao_Desempenho.Nota_Final_Ponderada) --- mesmo padrão
\"calculado mas armazenado\" já usado em
Mov_Rh_Banco_Horas_Movimento.Data_Limite_Compensacao e
Cad_Pre_Cadastro.Data_Descarte_Previsto.*

*Revisão 6 (mantida abaixo): acrescentou a seção 2, Recrutamento e
Seleção, pedida por Alberto ao perguntar onde estava a parte de
\"contratação\" do módulo --- ponto em aberto desde a revisão 4. Cobre:
(1) separação de equipe dentro do RH --- recrutamento/seleção distinto
de folha/treinamento --- via Cad_Usuario_Escopo (restrição do tipo
area_rh), com acesso a mais de uma área por usuário quando configurado;
(2) cargo deixa de ser texto livre --- Cad_Rh_Cargo, cadastro próprio da
empresa, com CBO e indicador de liderança migrados de
Cad_Participante_Historico_Cargo (Fase 0); (3) vaga (Cad_Rh_Vaga) com
régua de aprovação sempre opcional e referência direta ao compromisso
orçamentário de Planejamento & Orçamento, fechando o gancho do Documento
Analítico; (4) candidatura/etapas/avaliação com suporte a múltiplos
avaliadores por etapa, cada um com parecer e recomendação próprios, e
lista de critérios pontuados (Mov_Rh_Vaga_Candidato_Etapa_Avaliador,
Cad_Rh_Criterio_Avaliacao, Mov_Rh_Vaga_Candidato_Etapa_Avaliador_Nota);
(5) reaproveitamento de candidato/entrevista entre vagas, já suportado
estruturalmente pelo cadastro único de pré-cadastro; (6) checklist de
documentos de contratação configurável por empresa, com itens
obrigatórios e opcionais, instanciado automaticamente na aprovação final
(Cad_Rh_Checklist_Documento/Mov_Rh_Candidato_Documento); (7) retenção de
dados de candidato sob a LGPD --- só com consentimento explícito,
eliminação no encerramento do processo sem consentimento, prazo
parametrizável por empresa e alerta ao usuário acima de 24 meses
(Cad_Rh_Politica_Retencao_Candidato); e (8) Tipo_Vinculo ganhou
pro_labore, com processo seletivo sempre opcional, independente do tipo
de vínculo --- construído junto com o patch em Fase 0 (revisão 31).*

*Revisão 5 (mantida abaixo): incorporou quatro rodadas de comentários de
Alberto sobre este módulo, já em conjunto com Fase 0 (revisão 30),
Contas a Pagar/Receber (revisão 8) e Tesouraria (revisão 5): (1) abono
de falta/atraso pelo gestor --- Mov_Rh_Ponto_Abono (seção 6),
deliberadamente simples, sem régua de aprovação, por haver vários níveis
de gestor independentes; (2) completude da rescisão ---
Cad_Rh_Motivo_Desligamento.Multa_Atraso_Pagamento_Aplicavel e o prazo do
art. 477 §6º (seção 3), TRCT/homologação via GED, Exame Demissional como
exemplo em Cad_Rh_Tipo_Evento_Ficha (seção 12) e quitação de banco de
horas na rescisão via
Mov_Rh_Banco_Horas_Movimento.Origem_Tipo=quitacao_rescisao (seção 7);
(3) óbito como motivo de desligamento --- pesquisa de eSocial (CAT
original/reabertura/comunicação de óbito, indCatObito/dtObito,
REGRA_EVENTO_POSTERIOR_CAT_OBITO) e legislação (isenção da multa do art.
477, FGTS 100% liberado, IRRF próprio) incorporada em
Mov_Rh_Ficha_Evento.Houve_Obito/Data_Obito/Tipo_Cat/ID_Evento_Ficha_Origem
(seção 12) e Cad_Vinculo_Emprego.ID_Evento_Ficha_Origem_Obito (seção 3);
e (4) beneficiário do óbito e a folha gerando pagamento de verdade ---
Cad_Vinculo_Emprego.ID_Participante_Beneficiario_Obito/Qualificacao_Recebedor
(seção 3, cobrindo a preocupação de Alberto sobre o fiel depositário do
dinheiro), e a liquidação de TODA folha (não só salário --- também INSS,
FGTS, IRRF, pensão alimentícia, consignado) passando a gerar Mov_Titulo
e remessa bancária real (seção 21), com conta-salário diferenciada (Fase
0, revisão 30) e visibilidade de RH sobre pagamentos não processados
(seção 14).*

*Revisão 4: incorporou a rodada de verificação de compliance pedida por
Alberto --- legislação trabalhista (CLT), Manual de Orientação do
eSocial (MOS) e Lei 14.611/2023 (Igualdade Salarial) --- com patch
correspondente em Fase 0 (revisão 29): Tipo_Vinculo ganhou
intermitente/safrista/cooperado;
Tipo_Contrato_Prazo/Data_Fim_Prevista_Contrato cobrem experiência
prorrogável/efetivável sem novo vínculo; Local_Regime_Trabalho e
Sujeito_Controle_Jornada/Motivo_Exclusao_Jornada separam onde o trabalho
acontece de quando ele sai do controle de jornada (art. 62 CLT);
ID_Agente_Integracao para estágio/aprendiz;
Tipo_Aviso_Previo/Dias_Aviso_Previo/Data_Projecao_Termino (Lei
12.506/2011); Cad_Rh_Motivo_Desligamento como cadastro próprio com
fatores de cálculo; Mov_Rh_Estabilidade_Provisoria e
Cad_Rh_Processo_Administrativo_Judicial como entidades novas;
classificação PCD/cotista e Ausência Legal Justificada como tipos de
evento de ficha, com Data_Inicio_Responsabilidade_Inss para afastamento
longo/acidente; Compoe_Media_Ferias_13 desmembrado em dois campos
independentes; sobreaviso modelado via Cad_Rh_Escala.Natureza_Periodo e
novos Tipo de Mov_Rh_Ponto; Data_Limite_Compensacao e pagamento
incondicional/solicitado no banco de horas;
Cad_Rh_Ambiente_Trabalho/Mov_Rh_Vinculo_Ambiente para a hierarquia de
risco do eSocial; ID_Categoria_Remuneratoria em Cad_Rh_Verba; e a nova
seção 15 de compliance com a Lei 14.611/2023
(Cad_Rh_Declaracao_Transparencia_Salarial, Cad_Rh_Plano_Acao_Equidade), apoiada
em Sexo/Cor_Raca e Nivel_Lideranca adicionados a Fase 0.*

*Pontos que ficam registrados como gancho explícito, não bloqueante: se
a combinatória de regras de contabilização por verba+departamento
crescer muito no dia a dia, vale revisitar se uma tabela dedicada
compensaria a perda de reaproveitamento do Motor de Regras único; como
as recomendações individuais de cada avaliador se combinam no Resultado
da etapa de seleção fica a critério do RH, sem regra estrutural; a
fórmula exata de composição da Nota_Final_Ponderada de desempenho (seção
4) fica descrita como comportamento de aplicação, não travada na
estrutura; se no futuro entrar avaliação 360º, o Tipo_Avaliador fechado
{gestor, propria} da seção 4 precisa de extensão; a estrutura não trava
se o recálculo de Ordem_Calculo (seção 5) roda sobre o grafo inteiro da
empresa ou só o subgrafo afetado, nem a ordem entre o fechamento do
bloco \"folha_pagamento\" (Cad_Periodo_Fechamento_Filial, migrado na
revisão 13 do antigo Cad_Rh_Periodo_Folha) e o fechamento contábil
correspondente, ambas decisões de aplicação/processo; os pontos de
placement listados nas Notas acima
(Cad_Rh_Processo_Administrativo_Judicial, Motivo_Exclusao_Jornada
fechado, e a possível simplificação do eixo de ambiente); e, da revisão
9, a resolução de faixa salarial de reajuste coletivo quando o próprio
reajuste empurra o salário de faixa (seção 16), a proporcionalidade do
piso de aprendiz sem campo próprio (seção 16), e a nomenclatura Tipo
{taxa, desconto} de Mov_Rh_Beneficio_Taxa_Global (seção 17), todos
comportamento de aplicação ou rotulagem própria, sem confirmação item a
item de Alberto; e, desta revisão 10, os pontos listados nas Notas acima
(Mov_Rh_Folha_Item.ID_Origem_Ocorrencia generalizado além de pensão,
Cad_Rh_Tabela_Salarial_Grupo sem lista fechada, ausência de progressão
automática de step, e o escopo de Exige_Motivacao_Formal restrito a
empresa pública/SEM), o regime de servidor estatutário/RJU e a folha de
inativos, à época sinalizados --- RESOLVIDOS na revisão 12 (nova seção
20), com os pontos de aplicação registrados nas Notas acima
(avaliação/homologação do estágio probatório, exceções legais de acúmulo
de verba sobre subsídio, e a ligação de PAD a motivo de desligamento por
comportamento de aplicação).*

*Seguindo a ordem do Documento Analítico, os módulos ainda não iniciados
são Portal do Cliente e Gestão de Contratos/Projetos --- mas, como
sempre neste projeto, a decisão de por onde continuar é sua.*

*Revisão 14 --- Bloco 1 da validação geral consolidado junto com a Fase
0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal)
e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 15 --- tipo lógico \"código\" aplicado junto com a revisão 42
da Fase 0. Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 16 --- Bloco 3 consolidado junto com a Fase 0 (revisão 45) e o
novo módulo Fase 8 --- Jurídico. Pendências: conferir a quantidade de
códigos das tabelas oficiais do eSocial e validar, com RH e contador, as
faixas e os parâmetros provisórios de INSS e IRRF.*

*Revisão 17 --- Bloco 4 consolidado junto com a Fase 0 (revisão 46),
Contabilidade & Fiscal (revisão 18) e a Fase 8 --- Jurídico (revisão 2).
Ficam para um ajuste próprio da Folha, a aprovar por Alberto, as
novidades da NT 07/2026 do eSocial com data marcada: salário-paternidade
a partir de 2027-01 (ainda não no XSD de 26/10/2026), infoMesmoMtv no
S-2230 e fim de infoCota a partir de 2026-10-26, cargo e local de
trabalho no S-2500 a partir de 2026-10-26, limite de horas do tempo
parcial a partir de 2026-11-23 e indTribFolhaPisPasep (PIS sobre
folha).*

*Revisão 18 --- Bloco 5 consolidado junto com a Fase 0 (revisão 47),
Contabilidade & Fiscal (revisão 19) e Contas a Pagar/Receber (revisão
13). Os ajustes da NT 07/2026 do eSocial (salário-paternidade,
infoMesmoMtv, fim do infoCota, cargo no S-2500, horas do tempo parcial)
seguem à espera da aprovação do Alberto, no registro de pendências
(documento 26, P-28), e três deles entram em vigor em 26/10/2026.*

*Revisão 19 --- ajustes da Folha da NT 07/2026 do eSocial (documento 28)
consolidados junto com a Fase 0 (revisão 48), por comando "consolidar" de
Alberto, com as premissas do documento: contagem dos 60 dias do
infoMesmoMtv do término do afastamento anterior ao início do novo (P-38),
códigos 23, 24, 27 e 28 a partir de 14/12/2026 (P-39), todo salário
existente migrado como mês até o RH indicar os horistas (P-41) e regras
de cálculo do horista a definir com o RH e o contador (P-42). Seguem em
aberto: a dedução de salário-paternidade na DCTFWeb (P-40) e a
reconferência dos esquemas quando o pacote XSD posterior a 26/10/2026
existir (P-24). Aplicada no arquivo Markdown do Projeto; o documento
Word e o modelo entidade-relacional dependem dos scripts de geração.*


*Revisão 20 --- correções de nomenclatura da auditoria de 04/10/2026 (documento 29), aplicadas nos arquivos Markdown e nos Word e no modelo ER regerados a partir deles.*


*Revisão 21 --- descanso semanal remunerado e feriado ponte (P-42), consolidados por comando "consolidar" de Alberto em 05/10/2026, junto com a revisão 51 da Fase 0. Aplicada nos arquivos Markdown do Projeto; os documentos Word e o modelo entidade-relacional são regerados a partir deles.*



24\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este documento não ganha entidades novas; as alterações em entidades existentes aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3").



25\. Anexo --- Entidades e domínios da revisão 10 (documento 69)

Revisão 10 do dicionário: este anexo reúne 5 entidades novas das respostas de 14/10/2026 da equipe de TI (documento 69, D-N178 a D-N190), que Alberto aprovou e mandou consolidar em 18/10/2026. As alterações em entidades existentes aparecem nas próprias entidades, com a nota "Revisão 10".

25.1. Parâmetros da jornada e da hora extra (documento 69, D-N180 e D-N183)

Cad_Rh_Parametro_Jornada

Parâmetros da jornada por empresa, com refinamento opcional por categoria sindical: o multiplicador do valor-hora do mensalista (valor-hora = salário cadastral dividido por horas semanais vezes o multiplicador) e o prazo de compensação do banco de horas em meses. Padrão de Cad_Rh_Parametro_Dsr (o mais específico vence). Revisão 17 (D-N293 a D-N299): a linha pode ser também por filial, na ordem filial com categoria, categoria, filial, empresa; ganha a duração da hora noturna reduzida, a duração da hora-aula do professor e, na revisão 19, o indicador da prorrogação da jornada noturna (o modo de composição da hora extra noturna, que a revisão 17 criou, saiu na revisão 19: só vale o cálculo composto). Documento 69, D-N180.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Parametro_Jornada** | *identificador* | --- |
| **ID_Parametro_Jornada_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Rh_Parametro_Jornada_Versao). ID_Parametro_Jornada é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa)* | Empresa a que a regra se aplica. |
| **ID_Filial** | *referência (Cad_Filial, opcional)* | Revisão 17 (D-N293): vazio: a linha vale para a empresa toda; preenchido: só para os vínculos dessa filial, que deve pertencer à empresa da linha (o ERP confere). O campo vale para a linha toda (multiplicador, prazo do banco de horas, horário noturno, duração da hora noturna, prorrogação da jornada noturna e duração da hora-aula). Vale a linha mais específica na data do cálculo, nesta ordem (D-N294, a categoria sindical vence a filial): filial com categoria, categoria, filial, empresa. Duas linhas do mesmo nível não se sobrepõem no tempo. |
| **ID_Categoria_Sindical** | *referência (Cad_Rh_Categoria_Sindical, opcional)* | Vazio: vale para a empresa toda. Preenchido: só para os vínculos dessa categoria, e prevalece sobre a linha da empresa. |
| **Multiplicador_Semanas_Valor_Hora** | *número* | Valor-hora do mensalista = salário cadastral / (Horas_Semanais x este multiplicador). Valor inicial 5 (decisão de Alberto, 19/10/2026, "usual de mercado"; revisão 12, D-N208): dá o divisor usual de mercado, 220 para 44 horas semanais e 200 para 40. Substitui o 4 da resposta de 14/10/2026 (divisor 176). Alterável por empresa e por categoria sindical, por versão nova com vigência. |
| **Prazo_Compensacao_Meses** | *número, opcional* | Prazo do banco de horas em meses. Vazio: a empresa não definiu; o sistema não vence créditos. A CLT admite até 6 meses por acordo individual e até 1 ano por norma coletiva. |
| **Hora_Inicio_Noturno** | *hora, opcional* | Revisão 12 (D-N214): A hora em que começa a hora noturna da empresa (ou da categoria sindical, quando a linha tem categoria). O período pode passar da meia-noite. Preenchido junto com Hora_Fim_Noturno. |
| **Hora_Fim_Noturno** | *hora, opcional* | Revisão 12 (D-N214): A hora em que termina a hora noturna. Os dois campos se preenchem juntos. Vazios, o ponto não classifica hora noturna e grava pendência de parâmetro. O valor é de quem cadastra o parâmetro, sem valor fixo no código: o horário legal varia por atividade e a convenção coletiva pode alterá-lo (a confirmar com o contador). Revisão 15 (D-N234, Q74-12): a janela de início e fim não cobre a prorrogação da jornada noturna depois do fim (Súmula 60, II, do TST); a hora noturna reduzida entra pelo campo Duracao_Hora_Noturna_Minutos (revisão 17, D-N298). A prorrogação entra pelo campo Aplica_Hora_Noturna_Na_Prorrogacao (revisão 19, D-N339, Q87-13). |
| **Duracao_Hora_Noturna_Minutos** | *número, opcional* | Revisão 17 (D-N298): duração, em minutos, da hora noturna computada (padrão 52,5, isto é, 52 min 30 s): cada hora real no período noturno vale 60 / 52,5 = 1,142857 hora computada, e o ponto majora as horas pelo fator. Vazio: sem redução. Não se aplica quando Tipo_Jornada é doze_por_trinta_e_seis (fonte secundária, art. 59-A, parágrafo único). |
| **Minutos_Hora_Aula** | *número, opcional* | Revisão 17 (D-N298): duração, em minutos, da hora-aula do professor (45, 40 ou outra), para converter o tempo de aula em horas-aula. Fica numa linha por filial (D-N299), porque a filial tem a UF, e por categoria sindical quando preciso; sem padrão por UF. Quem tem várias filiais no mesmo estado usa a ação de copiar a linha entre filiais. |
| **Aplica_Hora_Noturna_Na_Prorrogacao** | *booleano* | Revisão 19 (D-N339): verdadeiro quando a jornada noturna que passa do fim do período noturno (depois das 5h, por exemplo) continua sendo computada como noturna nas horas prorrogadas: adicional noturno e hora reduzida valem também nessas horas (Súmula 60, II, do TST). Alberto confirmou em 21/10/2026 que há cliente com jornada noturna prorrogada depois das 5h (Q87-13). Padrão falso, por linha do parâmetro (empresa, filial ou categoria sindical, com vigência). Não se aplica quando Tipo_Jornada é doze_por_trinta_e_seis (fonte secundária, art. 59-A, parágrafo único). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 12 --- campos novos: Hora_Inicio_Noturno, Hora_Fim_Noturno; campos alterados: Multiplicador_Semanas_Valor_Hora.*

*Revisão 15 --- campos alterados: Hora_Fim_Noturno.*

*Revisão 17 --- campos novos: ID_Filial, ID_Modo_Composicao_Noturna, Duracao_Hora_Noturna_Minutos, Minutos_Hora_Aula; campos alterados: Hora_Fim_Noturno.*

*Revisão 19 --- campos novos: Aplica_Hora_Noturna_Na_Prorrogacao; campos que saem: ID_Modo_Composicao_Noturna; campos alterados: ID_Filial, Hora_Fim_Noturno.*

Cad_Rh_Regra_Hora_Extra

Regra, com vigência, do percentual de adicional da hora extra por tipo de hora, que o ponto consulta: geral da empresa, por categoria sindical (convenção) e com exceção por cargo ou por vínculo. Documento 69, D-N183.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Regra_Hora_Extra** | *identificador* | --- |
| **ID_Regra_Hora_Extra_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Rh_Regra_Hora_Extra_Versao). ID_Regra_Hora_Extra é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa. |
| **ID_Categoria_Sindical** | *referência (Cad_Rh_Categoria_Sindical, opcional)* | Convenção a que a regra pertence. Vazio: regra geral da empresa. |
| **ID_Funcao** | *referência (Cad_Rh_Funcao, opcional)* | Revisão 12 (D-N212): Exceção por função: a função do histórico do vínculo (Cad_Vinculo_Historico_Funcao) na data da hora. |
| **ID_Cargo** | *referência (Cad_Rh_Cargo, opcional)* | Exceção por cargo: o cargo do histórico do vínculo na data da hora. Revisão 12 (documento 74, D-N212): deixa de ser "a função da resposta"; a função tem campo próprio (ID_Funcao) e não é o cargo. |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego, opcional)* | Exceção por vínculo. Revisão 12 (D-N212): um nível só por linha. No máximo um entre ID_Vinculo, ID_Funcao, ID_Cargo e ID_Categoria_Sindical; os quatro vazios são a regra geral da empresa, e o ERP rejeita a combinação. |
| **ID_Tipo_Hora** | *referência (Cad_Classe_Sistema, domínio = tipo_hora_ponto)* | Classificação da hora feita pelo ponto, nos sete valores de tipo_hora_ponto: dia_util, descanso_semanal, feriado, noturna, dia_util_noturna, descanso_semanal_noturna e feriado_noturna (revisão 12, D-N213). A noturna é a hora noturna normal (adicional noturno, sem hora extra); os três valores combinados são a hora extra feita em horário noturno. Revisão 17 (D-N297): nos três valores combinados o ERP calcula o multiplicador como (1 + hora extra) x (1 + adicional noturno), no mesmo nível da regra, e esse é o único cálculo: Alberto decidiu em 21/10/2026 que a hora extra noturna é só o cálculo composto (Revisão 19, D-N335, Q87-27; o campo que escolhia entre composto e soma saiu de Cad_Rh_Parametro_Jornada); uma linha combinada com o total informado prevalece sobre o cálculo (é o caminho para a norma coletiva que fixe de outro jeito). A conferência com a Súmula 264 do TST fica com o contador. |
| **Percentual_Adicional** | *número* | Adicional da hora extra em percentual (50, 100 etc.). Parâmetro, nunca fixo no código. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 12 --- campos novos: ID_Funcao; campos alterados: ID_Cargo, ID_Vinculo, ID_Tipo_Hora.*

*Revisão 17 --- campos alterados: ID_Tipo_Hora.*

*Revisão 19 --- campos alterados: ID_Tipo_Hora.*

Busca da regra (revisão 12, documento 74, D-N212). Para uma hora do vínculo V, na data D e do tipo T: a linha vigente em D com o tipo T, no primeiro nível que tiver, nesta ordem: vínculo, função (a do histórico em D), cargo (o do histórico em D), categoria sindical, empresa. Sem linha em nenhum nível, o ponto grava a pendência de regra de hora extra e não calcula. É o princípio "o mais específico vence" do restante do dicionário (por exemplo, Cad_Rh_Parametro_Dsr). A função, o cargo e a categoria sindical são deste vínculo na data; o recálculo de um período antigo usa a função e o cargo daquele dia, e não os de hoje.

25.2. Excesso de horas do horista e banco de horas (documento 69, D-N181 e D-N182)

Mov_Rh_Hora_Excedente_Decisao

Decisão, por ocorrência, do destino do excesso de horas do horista sobre o limite semanal: hora extra paga ou banco de horas, escolhida pelo gestor do vínculo ou, quando o vínculo não tem gestor, pelo RH, com quem decidiu e quando. Documento 69, D-N181.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Decisao** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | O colaborador. |
| **Data** | *data* | O dia da apuração de ponto em que houve o excesso. |
| **Horas** | *número* | Horas do excesso (maior que zero). |
| **ID_Regra_Hora_Extra** | *referência (Cad_Rh_Regra_Hora_Extra)* | A regra de percentual aplicada, resolvida pelo ponto. |
| **Percentual_Origem** | *número* | Percentual da hora de origem (por exemplo 50 ou 100), copiado da regra na data. Vale no pagamento do vencimento. |
| **Destino** | *enumeração {hora_extra_paga, banco_horas}* | O que o decisor escolheu. |
| **Tipo_Decisor** | *enumeração {gestor, rh}* | rh quando o vínculo não tem gestor (ID_Gestor vazio). |
| **ID_Usuario_Decisor** | *referência (Cad_Usuario)* | Quem decidiu. Validado por aplicação: o gestor do vínculo, ou usuário do RH. |
| **Data_Hora_Decisao** | *data/hora* | Quando decidiu. |
| **Observacao** | *texto, opcional* | Texto livre. |

Mov_Rh_Banco_Horas_Consumo

Alocação de cada débito do banco de horas contra os créditos que consome, sempre os mais antigos primeiro, para que cada crédito tenha o seu saldo e o seu vencimento. Documento 69, D-N182.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Consumo** | *identificador* | --- |
| **ID_Movimento_Debito** | *referência (Mov_Rh_Banco_Horas_Movimento)* | O débito (folga, pagamento no vencimento, pagamento pedido pelo gestor ou quitação na rescisão). |
| **ID_Movimento_Credito** | *referência (Mov_Rh_Banco_Horas_Movimento)* | O crédito consumido. A aplicação aloca sempre o mais antigo primeiro. |
| **Horas** | *número* | Horas alocadas (maior que zero; a soma por débito é igual às horas do débito). |

25.3. Confirmação da perda do DSR (documento 69, D-N184)

Mov_Rh_Dsr_Perda_Confirmacao

Confirmação do operador, por colaborador e semana, de que o colaborador perde o descanso semanal remunerado pelo limite de faltas de Cad_Rh_Parametro_Dsr; recusada, o DSR não é descontado. Documento 69, D-N184.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Confirmacao** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | O colaborador. |
| **ID_Parametro_Dsr** | *referência (Cad_Rh_Parametro_Dsr)* | O parâmetro (a versão vigente na semana é a que vale). |
| **Data_Inicio_Semana** | *data* | Primeiro dia da semana do DSR. |
| **Faltas_Consideradas** | *número* | Faltas com tipo que perde o DSR e sem abono, apuradas na semana. |
| **Confirmou** | *booleano* | Verdadeiro: o operador confirmou a perda; falso: recusou, e o DSR não é descontado. |
| **ID_Usuario** | *referência (Cad_Usuario)* | O operador. |
| **Data_Hora** | *data/hora* | Quando confirmou. |



26\. Anexo --- Entidades da revisão 12 (documento 74)

Revisão 12 do dicionário: este anexo reúne 2 entidades novas do documento 74 (D-N202 a D-N214), que Alberto aprovou e mandou consolidar em 19/10/2026. As alterações em entidades existentes aparecem nas próprias entidades, com a nota "Revisão 12".

26.1. Função do colaborador (documento 74, D-N211 a D-N213)

Cad_Rh_Funcao

Função do colaborador, cadastrada por empresa, independente do cargo (Alberto, 19/10/2026: a função não é o cargo). Entra como nível da regra de hora extra (Cad_Rh_Regra_Hora_Extra) e, quando for função de confiança do eSocial, fornece o código do evento. Mesmo padrão de Cad_Rh_Cargo: identidade e versão com vigência. Documento 74, D-N211.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Funcao** | *identificador* | --- |
| **ID_Funcao_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Rh_Funcao_Versao). ID_Funcao é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa: a mesma função pode ter nome ou CBO diferente entre empresas do grupo. |
| **Nome** | *texto* | Nome da função na empresa. |
| **Codigo** | *código (30), opcional* | Código interno da função na empresa, opcional (até 30). Revisão 15 (documento 78, Q74-9, D-N233): o S-2200 não traz código de função; para função de confiança ou cargo em comissão pede o nome (nmFuncao) e o CBO (CBOFuncao), que vêm de Nome e de ID_Cbo. Antes este campo dizia "o código usado no evento". |
| **ID_Cbo** | *referência (Cad_Classe_Sistema, domínio = cbo, opcional)* | CBO da função, quando existe. |
| **ID_Categoria_Sindical** | *referência (Cad_Rh_Categoria_Sindical, opcional)* | Revisão 15 (D-N233): preenchido só quando ESTA função tem enquadramento sindical diferente do do cargo e do padrão da filial (Alberto: "pela função pode ter um outro sindicato", Q74-10). Vazio na grande maioria das funções. Precedência do enquadramento: função, depois cargo (Cad_Rh_Cargo.ID_Categoria_Sindical), depois o padrão da filial; o mais específico vence. |
| **Ativo** | *booleano* | Se a função pode receber novos colaboradores. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 15 --- campos novos: ID_Categoria_Sindical; campos alterados: Codigo.*

Cad_Vinculo_Historico_Funcao

Qual função o vínculo teve em cada período: tabela de janelas de vigência, como Cad_Participante_Historico_Cargo. A regra de hora extra de um dia passado usa a função daquele dia, e o recálculo de um período antigo não pode trocar a regra só porque o colaborador mudou de função depois. O vínculo pode não ter função nenhuma (o histórico não tem linha). Um vínculo tem no máximo uma função vigente por dia. Documento 74, D-N211.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Historico_Funcao** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | O colaborador. |
| **ID_Funcao** | *referência (Cad_Rh_Funcao)* | A função exercida no período. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |



27\. Anexo --- Entidades da revisão 13 (documento 75)

Revisão 13 do dicionário: este anexo reúne 7 entidades novas do documento 75 (D-N215 a D-N224), que Alberto aprovou e mandou consolidar em 19/10/2026. As alterações em entidades existentes aparecem nas próprias entidades, com a nota "Revisão 13".

27.1. Grupos do S-2200 por categoria e vínculo (documento 75, D-N220)

Cad_Vinculo_Estatutario

O grupo infoEstatutario do S-2200 e os campos do servidor, só para vínculo estatutário (1:1 com o vínculo). Sem vigência: a alteração vai pelo S-2206 e fica no evento (Q75-7). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego), chave primária compartilhada* | Extensão 1:1. |
| **ID_Tipo_Provimento** | *referência (Cad_Classe_Sistema, domínio = tipo_provimento_esocial)* | tpProv, onze valores (domínio tipo_provimento_esocial). A data de exercício já é Cad_Vinculo_Emprego.Data_Exercicio. |
| **ID_Tipo_Plano_Rpps** | *referência (Cad_Classe_Sistema, domínio = plano_rpps), opcional* | tpPlanRP, valores 0 a 3. Obrigatório e exclusivo quando o regime previdenciário é RPPS. Revisão 17 (D-N305): vira domínio de Cad_Classe_Sistema (plano_rpps: sem_segregacao 0, fundo_capitalizacao 1, fundo_reparticao 2, mantido_tesouro 3, com o código tpPlanRP do eSocial). |
| **Indicador_Teto_Rgps** | *booleano, opcional* | indTetoRGPS. Obrigatório e exclusivo quando RPPS. |
| **Indicador_Abono_Permanencia** | *booleano, opcional* | indAbonoPerm. Obrigatório e exclusivo quando RPPS. |
| **Data_Inicio_Abono** | *data, opcional* | dtIniAbono. Obrigatória quando há abono e a admissão não é cadastramento inicial; só para provimento 5, 8 ou 10. |
| **Data_Ingresso_Cargo** | *data, opcional* | dtIngrCargo. Só para estatutário com cargo e CBO, e provimento 5, 8 ou 10. |
| **Cargo_Acumulavel** | *booleano, opcional* | acumCargo. Obrigatório quando não é cadastramento inicial e o declarante é ente público. |
| **Data_Inicio_Cessao** | *data, opcional* | cessao/dtIniCessao: início da cessão ou do exercício em outro órgão, para quem continua cedido na data de início dos eventos ou da transferência. |

*Revisão 17 --- campos renomeados: Tipo_Plano_Rpps para ID_Tipo_Plano_Rpps.*

Cad_Vinculo_Temporario

O grupo trabTemporario do S-2200, só para a categoria 106 (1:1 com o vínculo). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego), chave primária compartilhada* | Extensão 1:1. |
| **ID_Hipotese_Legal** | *referência (Cad_Classe_Sistema, domínio = hipotese_legal_temporario)* | hipLeg: 1 necessidade de substituição transitória de pessoal permanente; 2 demanda complementar de serviços. Revisão 17 (D-N305): vira domínio de Cad_Classe_Sistema (hipotese_legal_temporario: substituicao_transitoria 1 e demanda_complementar 2, com o código do eSocial), para o eSocial poder ampliar a lista por nota técnica. |
| **Justificativa_Contratacao** | *texto (999)* | justContr: o fato que justifica a hipótese legal. O prazo precisa ser compatível. |
| **ID_Participante_Tomador** | *referência (Cad_Participante)* | ideEstabVinc: o estabelecimento do tomador (CNPJ ou CPF). Com admissão a partir de 22/04/2024, a raiz do CNPJ difere da do empregador e o CPF difere do empregado. |

*Revisão 17 --- campos renomeados: Hipotese_Legal para ID_Hipotese_Legal.*

Cad_Vinculo_Temporario_Substituido

Até nove trabalhadores substituídos por vínculo temporário (cpfTrabSubst). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Substituido** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Temporario)* | O vínculo temporário. |
| **Cpf_Trabalhador_Substituido** | *código (11)* | cpfTrabSubst: CPF válido, de quem é substituído (pode não ser colaborador do ERP). |

Cad_Vinculo_Aprendiz

O grupo aprend do S-2200, só para a categoria 103 (1:1 com o vínculo). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego), chave primária compartilhada* | Extensão 1:1. |
| **Tipo_Contratacao** | *enumeração {direta, indireta}* | indAprend: direta, pelo estabelecimento que cumpre a cota; indireta, por entidade sem fins lucrativos ou desportiva a serviço do estabelecimento. |
| **ID_Participante_Entidade_Qualificadora** | *referência (Cad_Participante, opcional)* | cnpjEntQual. Obrigatória e exclusiva na contratação direta. |
| **ID_Participante_Contratante_Indireto** | *referência (Cad_Participante, opcional)* | Estabelecimento para o qual a contratação foi feita (tpInsc e nrInsc). Obrigatório e exclusivo na indireta. |
| **ID_Participante_Pratica** | *referência (Cad_Participante, opcional)* | cnpjPrat: onde as atividades práticas são feitas, nos casos de cota alternativa, serviço terceirizado ou prática centralizada em outro estabelecimento. |

Cad_Vinculo_Transferencia

O empregador ou a matrícula anteriores, para os três casos do leiaute (sucessaoVinc, transfDom e mudancaCPF), conforme Cad_Vinculo_Emprego.ID_Tipo_Admissao (1:1). Quando a transferência é entre empresas do próprio ERP, Cad_Vinculo_Emprego.ID_Vinculo_Origem_Transferencia já traz os dados e esta entidade é gerada por derivação. Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego), chave primária compartilhada* | Extensão 1:1. |
| **ID_Participante_Anterior** | *referência (Cad_Participante, opcional)* | O empregador anterior (sucessão) ou o representante anterior da unidade familiar (doméstico), quando é cadastrado. |
| **Tipo_Inscricao_Anterior** | *enumeração {cnpj, cpf, cgc, cei}, opcional* | sucessaoVinc/tpInsc. CGC só vale para transferência até 30/06/1999. |
| **Numero_Inscricao_Anterior** | *código (14), opcional* | Número do empregador anterior (CNPJ ou CNPJ alfanumérico, CPF, CGC ou CEI), do CPF do representante anterior (cpfSubstituido) ou do CPF antigo do trabalhador (cpfAnt), quando não há participante. |
| **Matricula_Anterior** | *código (30), opcional* | matricAnt. Obrigatória na sucessão quando não é cadastramento inicial, e sempre na mudança de CPF; a partir de 22/04/2024 deve ser idêntica à matrícula no empregador anterior. |
| **Data_Transferencia** | *data* | sucessaoVinc/dtTransf, transfDom/dtTransf ou mudancaCPF/dtAltCPF. |
| **Observacao** | *texto (255), opcional* | observacao. |

Cad_Vinculo_Observacao_Contrato

As observações do contrato do S-2200 (até 99). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Observacao** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | O vínculo. |
| **Texto** | *texto (255)* | observacoes/observacao. |

Cad_Vinculo_Treinamento_Capacitacao

Treinamentos, capacitações e exercícios simulados que a Norma Regulamentadora manda anotar no registro de empregados ou na CTPS (até 99; treiCap do S-2200). Documento 75, D-N220.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Vinculo_Treinamento** | *identificador* | --- |
| **ID_Vinculo** | *referência (Cad_Vinculo_Emprego)* | O vínculo. |
| **ID_Treinamento** | *referência (Cad_Classe_Sistema, domínio = treinamento_capacitacao_esocial)* | codTreiCap, Tabela 28 do eSocial. |



28\. Anexo --- Entidades novas da revisão 19 (documento 90)

Revisão 19 do dicionário: ocorrências do retorno do eSocial (documento 90, seção 7, aprovado por Alberto em 21/10/2026).

28.1. Ocorrências do retorno do eSocial no vínculo importado (documento 90, D-N301 a D-N303)

Cad_Esocial_Ocorrencia

Catálogo do tratamento por código de ocorrência do retorno do eSocial, com vigência (D-N301 e D-N302; documento 90, seção 7.1). Tabela de janela; chave: código mais Vigencia_Inicio. A classificação não vai para o código: fica em cadastro. A carga inicial traz só o "já existe" que o manual confirmar e todo o resto como corrigir_e_reenviar, provisória até o RH validar.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Esocial_Ocorrencia** | *identificador* | Chave da linha. |
| **Codigo_Ocorrencia** | *código (até 20) --- identidade* | Código que o eSocial devolve na ocorrência. |
| **Descricao** | *texto* | Descrição da ocorrência. |
| **Tipo_Ocorrencia** | *enumeração {erro, aviso}* | Erro ou aviso, como o eSocial classifica. |
| **Tratamento** | *enumeração {ja_existe, corrigir_e_reenviar, avisar_rh}* | ja_existe: o vínculo já constava no eSocial; o evento passa a aceito como importado (sem XML e sem data de envio do ERP, recibo opcional) e o RH é **sempre avisado** (D-N302). corrigir_e_reenviar: rejeitado, o RH corrige e o ERP reenvia como novo S-2200 original. avisar_rh: vai ao RH (por exemplo, CPF já admitido com outra matrícula, que **não** é "já existe"). |
| **Fundamento** | *texto* | Manual de orientação ou nota técnica do eSocial de onde o código e o tratamento vêm. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Carga inicial só com o "já existe" que o manual confirmar e todo o resto como corrigir_e_reenviar; provisória até o RH validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | A validação. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

Mov_Esocial_Evento_Ocorrencia

Um retorno do eSocial traz várias ocorrências; cada uma é uma linha, com o texto literal (D-N302; documento 90, seção 7.2). O aviso de matrícula diferente mostra a do ERP e a do eSocial, e o RH escolhe entre ajustar a matrícula do ERP e corrigir o eSocial.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Evento_Ocorrencia** | *identificador* | Chave da ocorrência. |
| **ID_Evento** | *referência (Mov_Esocial_Evento)* | Evento a que o retorno pertence. |
| **ID_Esocial_Ocorrencia** | *referência (Cad_Esocial_Ocorrencia, opcional)* | Linha do catálogo; vazio quando o código não consta (o tratamento é então corrigir_e_reenviar). |
| **Codigo_Recebido** | *código (até 20)* | O código como veio. |
| **Texto_Ocorrencia** | *texto* | O texto literal da ocorrência. |
| **Localizacao** | *texto, opcional* | Localização no XML, quando o eSocial informa. |
| **Matricula_Esocial_Informada** | *código (até 30), opcional* | Matrícula que consta no eSocial, quando ele informa; o aviso mostra a do ERP e esta, e o RH escolhe entre ajustar a matrícula do ERP e corrigir o eSocial (D-N302). |
| **Situacao_Tratamento** | *enumeração {pendente, tratada}* | Se o RH já tratou a ocorrência. |
| **ID_Usuario_Tratamento** | *referência (Cad_Usuario, opcional)* | Quem tratou. |
| **Data_Hora_Tratamento** | *data/hora, opcional* | Quando tratou. |
| **Decisao_Matricula** | *enumeração {ajustou_erp, corrigiu_esocial}, opcional* | Escolha do RH nos casos de matrícula diferente. |
| **Data_Hora_Recebimento** | *data/hora* | Quando o retorno chegou. |



29\. Anexo --- Entidades novas da revisão 38 (B0b-2: plano de saúde dos empregados)

Revisão 38 do dicionário (consolidação de 10/11/2026): 2 entidades novas neste módulo (documento 200, D-N533 e D-N534, Q200-8): o acordo coletivo do plano de saúde dos empregados e o crédito de CBS do benefício. O crédito nasce em Mov_Credito_Fiscal com Origem = beneficio_empregado.

29.1. Crédito de quem compra o serviço financeiro, arrendamento, antecipação de recebíveis e plano de saúde dos empregados (B0b-2; documento 200, seção 5.2)

Mov_Rh_Beneficio_Acordo_Coletivo

Revisão 38 (documento 200, seção 5.2; D-N533 e D-N534: Q200-8): O acordo ou a convenção coletiva que obriga a empresa a dar o benefício (plano de saúde), com a vigência e a declaração à RFB. A janela de seis meses depois do fim do acordo sai do parâmetro, e não de um campo.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Acordo_Coletivo** | *identificador* | --- |
| **ID_Beneficio** | *referência (Cad_Rh_Beneficio)* | O benefício, do tipo plano_saude. |
| **Tipo_Instrumento** | *enumeração {acordo_coletivo, convencao_coletiva}* | O instrumento. |
| **Numero_Registro** | *código (até 60), opcional* | O número do registro do instrumento. |
| **Clausula_Compulsoria** | *booleano* | O instrumento traz cláusula compulsória para o plano (Decreto, art. 63, § 1º, VI). Falso: o benefício não dá crédito. |
| **Data_Inicio_Vigencia** | *data* | O primeiro dia de vigência do instrumento. |
| **Data_Fim_Vigencia** | *data, opcional* | O último dia; vazio enquanto vigente. O crédito vale até seis meses depois dele (art. 63, § 5º). |
| **ID_Documento** | *referência (Cad_Documento), opcional* | O instrumento, guardado no GED. |
| **Situacao_Declaracao** | *enumeração {nao_declarado, declarado, rejeitado}* | A declaração à RFB do art. 337, § 2º. O ERP só registra, porque o ato conjunto que a regulamenta não foi publicado. |
| **Data_Declaracao** | *data, opcional* | Quando declarou. |
| **Numero_Protocolo_Declaracao** | *código (até 60), opcional* | O protocolo da declaração. |

Mov_Rh_Beneficio_Credito_Cbs

Revisão 38 (documento 200, seção 5.2; D-N533 e D-N534: Q200-8): O crédito mensal da empresa que paga plano de saúde aos empregados: o que ela pagou, o que descontou da folha, o que a operadora informou e a proporção dos empregados. O valor do crédito sai em Mov_Credito_Servico_Regime_Especifico.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Beneficio_Credito** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa contratante. |
| **ID_Beneficio** | *referência (Cad_Rh_Beneficio)* | O benefício (plano_saude). |
| **Competencia** | *competência* | O mês. |
| **ID_Acordo_Coletivo** | *referência (Mov_Rh_Beneficio_Acordo_Coletivo), opcional* | O instrumento que dá a cláusula compulsória. Sem ele, o ERP avisa que não há crédito. |
| **ID_Participante_Operadora** | *referência (Cad_Participante)* | A operadora ou a administradora de benefícios. |
| **Valor_Premio_Pago_Total** | *número* | O que a empresa pagou à operadora no mês pelo contrato (prêmio e contraprestação). |
| **Valor_Premio_Empregados** | *número* | A parte do pagamento que cobre os empregados titulares e os dependentes deles. O que cobre sócios ou outros fica fora (art. 63, § 1º, VI). |
| **Valor_Descontado_Empregados** | *número* | O que a folha descontou dos empregados no mês (art. 337, I, II e § 1º). |
| **Origem_Desconto** | *enumeração {folha_erp, esocial, documento_fiscal}* | De onde vem o desconto: da folha do ERP, do e-Social por convênio (art. 337, § 3º) ou do documento fiscal da empresa (§ 5º). |
| **Valor_Premios_Entidade_Total** | *número, opcional* | O total de prêmios e contraprestações arrecadados pela operadora no período, informado por ela na DeRE. |
| **Valor_Debito_Cbs_Entidade** | *número, opcional* | O débito de CBS pago pela operadora no período (base do crédito). |
| **Valor_Debito_Ibs_Entidade** | *número, opcional* | O débito de IBS pago pela operadora no período. |
| **Fonte_Informacao_Operadora** | *enumeração {dere_rfb, informado_usuario}* | Se o dado da operadora veio da RFB (§ 4º) ou foi digitado. |
| **Proporcao_Empregados** | *número, opcional* | Calculado: Valor_Premio_Empregados dividido por Valor_Premios_Entidade_Total (art. 337, I, b). |
| **Percentual_Custeio_Empresa** | *número, opcional* | Calculado: o que a empresa suportou (pago menos descontado) sobre o pago (art. 337, II e § 1º). |
| **Dentro_Janela_Acordo** | *booleano* | Calculado: o mês está dentro da vigência do instrumento ou até seis meses depois (art. 63, § 5º). |
| **ID_Documento_Fiscal** | *referência (Mov_Documento_Fiscal), opcional* | O documento fiscal do art. 337, § 5º, com o desconto de cada empregado, quando o e-Social não está disponível. O ato conjunto não saiu; o campo só guarda a referência. |
| **ID_Credito_Servico** | *referência (Mov_Credito_Servico_Regime_Especifico), opcional* | O registro de crédito que o Motor gerou. |
| **Situacao** | *enumeração {calculado, sem_credito}* | sem_credito quando falta acordo com cláusula compulsória, o mês está fora da janela ou a operadora não informou. |
| **Motivo_Sem_Credito** | *texto, opcional* | Por que o crédito é zero. |
