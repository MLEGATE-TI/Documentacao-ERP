**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 8 · MÓDULO 14**

**Jurídico**

*Processos judiciais e administrativos, contingências e provisão (CPC
25), depósitos e garantias, suspensão de exigibilidade, perícia,
societário e distribuição de lucros, beneficiário final, LGPD, regras de
uso de equipamentos, certificados digitais e procurações.*

*Revisão 7 --- consolidação da revisão 16 do dicionário (documentos 80 e 82, decisões D-N236 a D-N240 e D-N243 a D-N248, aprovadas por Alberto em 19/10/2026): 1 entidades existentes alteradas; lista de indicativos de suspensão da Reinf (13 valores, sem 06 e 07) e regra por tipo de processo (documento 82, D-N246).*

*Revisão 6 --- consolidação da revisão 12 do dicionário (documento 74, decisões D-N202 a D-N214, aprovadas por Alberto em 19/10/2026): 1 entidades existentes alteradas; texto de ID_Calendario_Limite_Pagamento (Q72-2 respondida).*

*Revisão 5 --- consolidação da revisão 11 do dicionário (documento 72, decisões D-N191 a D-N201, aprovadas por Alberto em 19/10/2026): 1 entidades existentes alteradas. O dicionário passa de 890 para 888 entidades.*

*Revisão 4 --- consolidação da revisão 4 do dicionário (documento 51: LC 224/2025, Mafon 2024 e 2025; decisões D-N118 a D-N124, aprovadas por Alberto em 12/10/2026): 3 entidades novas (anexo, seção 18); 2 entidades existentes alteradas. O dicionário passa de 829 para 837 entidades.*

*Revisão 3 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 2 entidades novas (anexo, seção 17); 4 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 2 --- Bloco 4 da validação geral (EFD-Reinf), construída junto
com a revisão 46 da Fase 0 e a revisão 18 de Contabilidade & Fiscal:
Cad_Processo ganha Autoria_Acao (indAutoria do R-1070). O R-1070 sai de
Cad_Processo, Mov_Processo_Suspensao e Mov_Processo_Juizo sem entidade
nova, e os eventos da Reinf citam só processos e códigos de suspensão
aceitos num R-1070 com vigência que cubra o período.*

*Revisão 1 --- primeira entrega do módulo, construída junto com o Bloco
3 da validação geral do dicionário (Fase 0 revisão 45, Folha & RH
revisão 16, Estoque 14, Gestão de Contratos 7, Contabilidade & Fiscal 17
e Contas a Pagar/Receber 12). Desenho aprovado por Alberto no documento
20 do Projeto.*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Por decisão de Alberto (D-3, opção B), o contencioso vira módulo
próprio, com documento próprio, chamado aqui de Fase 8 --- Jurídico. O
rótulo segue a numeração de entrega dos documentos e não reclassifica o
módulo no plano geral: o Jurídico não depende de fase nova, ele
reaproveita Fase 0 (participante, documento, motor de regras, régua de
aprovação), Contas a Pagar/Receber (depósitos, pagamentos e dividendos
viram título), Contabilidade & Fiscal (provisão, retenção, IRPJ/CSLL) e
Folha & RH (processo trabalhista). Quando qualquer desses módulos
precisa de um dado jurídico, ele aponta para o Jurídico; o inverso nunca
acontece, exceto pelas entidades de Fase 0 que o Jurídico referencia
(Cad_Empresa_Socio e Cad_Empresa_Responsavel).

Este documento leva a mesma estrutura dos demais: função e dados juntos,
entidade por entidade. Ele nasce na revisão 1, junto com a consolidação
deste bloco.

Convenções, as mesmas dos demais documentos: prefixo Cad\_ para cadastro
e Mov\_ para movimentação; identificador com prefixo ID\_; vigência com
Vigencia_Inicio, Vigencia_Fim (31/12/9999 quando o fim é indefinido) e
Motivo_Vigencia; cadastro mestre referenciado por outras entidades com
identidade e versão (Cad_Processo, Cad_Lgpd_Tratamento,
Cad_Politica_Uso_Equipamento e Cad_Procuracao); tabela oficial só de
código e descrição vira domínio de Cad_Classe_Sistema; valor que a lei
muda com o tempo vira parâmetro com vigência, nunca constante no código.

Dados legais provisórios: os parâmetros de distribuição de lucros e de
LGPD (Cad_Distribuicao_Lucro_Parametro e Cad_Lgpd_Parametro) entram na
carga inicial como provisórios (Situacao_Dado = provisorio) e só passam
a validados quando o RH e o contador aprovam pela régua de aprovação da
Fase 0 (área validacao_dado_legal, Fase 0 seção 9). O dado provisório
calcula em simulação; pagar distribuição de lucros com parâmetro
provisório fica bloqueado.

Nota sobre a confiança do texto: o que veio de norma lida inteira está
afirmado; o que veio de resumo de terceiros está marcado como não
confirmado nas Notas (seção 15). Nesses pontos a estrutura está fixada e
os valores são conferidos na carga.

2\. Processos, Partes e Advogados

Um cadastro único de processos, judiciais e administrativos, que serve a
todos os módulos. Substitui Cad_Rh_Processo_Administrativo_Judicial, que
só existia para o eSocial, e dá ao GED, à Reinf, à apuração de IRPJ e
CSLL e ao trabalhista um lugar comum para apontar.

Cad_Processo

O processo judicial ou administrativo. A numeração segue a Resolução CNJ
65/2008 (20 dígitos, NNNNNNN-DD.AAAA.J.TR.OOOO, dígito verificador
módulo 97) nos processos judiciais, o NUP de 17 dígitos nos
administrativos federais, e livre nos demais.

*Vigência: sim --- objeto, valor da causa, situação e responsável mudam;
o número e a empresa não (identidade).*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Processo** | *identificador* | --- |
| **ID_Processo_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Processo_Versao). ID_Processo é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa) --- identidade* | Empresa do grupo que é parte. |
| **Formato_Numero** | *enumeração {cnj, nup, outro} --- identidade* | Diz como validar Numero_Processo. |
| **Numero_Processo** | *código (30) --- identidade* | Só dígitos ou caracteres, sem máscara. cnj: 20 dígitos com dígito verificador módulo 97 validado; nup: 17 dígitos. Substitui o campo de 21 posições de Folha & RH, que não cabia no padrão do CNJ. |
| **Tipo_Processo** | *enumeração {judicial, administrativo, arbitral}* | Alimenta o tipo de processo do S-1070 e do R-1070 (judicial ou administrativo). |
| **ID_Area_Processo** | *referência (Cad_Classe_Sistema, domínio = area_processo)* | trabalhista, tributario, civel, consumidor, ambiental, previdenciario, familia, societario, regulatorio, outro. "familia" cobre a pensão alimentícia. |
| **Polo_Empresa** | *enumeração {ativo, passivo, terceiro_interessado}* | --- |
| **Data_Distribuicao** | *data, opcional* | Distribuição inicial. Onde o processo tramita em cada momento está em Mov_Processo_Juizo (Fase 8 --- Jurídico, seção 3). |
| **Valor_Causa** | *número, opcional* | --- |
| **Objeto** | *texto* | Resumo do que se discute. |
| **Situacao** | *enumeração {em_andamento, suspenso, arquivado_provisoriamente, encerrado}* | --- |
| **Data_Encerramento** | *data, opcional* | --- |
| **Sigiloso** | *booleano* | Processo em segredo de justiça: exige a permissão "ver dado sensível". |
| **ID_Processo_Principal** | *referência (Cad_Processo, autorreferência, opcional)* | Recurso, apenso ou execução ligados ao processo de origem. Recurso com número novo é processo novo apontando para o principal. |
| **ID_Participante_Responsavel** | *referência (Cad_Participante, opcional)* | Responsável interno pelo acompanhamento. |
| **Autoria_Acao** | *enumeração {proprio_contribuinte, terceiro}, opcional* | Adicionado na revisão 2 (Bloco 4). indAutoria do R-1070 da Reinf: a ação é do próprio contribuinte ou de terceiro (outra entidade, empresa ou pessoa) em que o contribuinte é beneficiário. Obrigatório quando o processo alimenta o R-1070. |
| **ID_Origem_Processo_Efd** | *referência (Cad_Classe_Sistema, domínio = origem_processo_efd, opcional)* | Novo na revisão 3 (documento 44). Origem do processo na EFD-Contribuições (x111 e 1010.IND_PROC): Justiça Federal, Receita Federal ou outros. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 3 --- campos novos (documento 44): ID_Origem_Processo_Efd.*

Cad_Processo_Parte

Quem é parte no processo, além da própria empresa.

*Vigência: sim --- a parte entra e sai do processo.*

  ------------------------- ---------------------- ----------------------------------------
  **Campo**                 **Tipo lógico**        **Descrição / regra**

  **ID_Processo_Parte**     *identificador*        ---

  **ID_Processo**           *referência            ---
                            (Cad_Processo)*        

  **ID_Participante**       *referência            ---
                            (Cad_Participante)*    

  **ID_Papel_Processual**   *referência            autor, reu, litisconsorte,
                            (Cad_Classe_Sistema,   terceiro_interessado, assistente,
                            domínio =              perito, testemunha.
                            papel_processual)*     

  **Polo**                  *enumeração {ativo,    ---
                            passivo, neutro}*      

  **Parte_Do_Grupo**        *booleano*             Verdadeiro quando a parte é empresa do
                                                   grupo (Cad_Grupo_Economico).

  **Vigencia_Inicio**       *data*                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**          *data*                 Último dia em que esta versão vale
                                                   (inclusive). Sempre preenchida:
                                                   31/12/9999 quando o fim é indefinido
                                                   (versão vigente) --- convenção da Fase
                                                   0, seção 2.

  **Motivo_Vigencia**       *texto, opcional*      Por que esta versão foi criada.
  ------------------------- ---------------------- ----------------------------------------

Cad_Processo_Advogado

Advogado ou escritório que atua no processo.

*Vigência: sim --- troca de patrono.*

  ---------------------------- ----------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**         **Descrição / regra**

  **ID_Processo_Advogado**     *identificador*         ---

  **ID_Processo**              *referência             ---
                               (Cad_Processo)*         

  **ID_Participante**          *referência             Advogado (pessoa física) ou escritório
                               (Cad_Participante)*     (pessoa jurídica).

  **Tipo_Atuacao**             *enumeração {interno,   ---
                               escritorio_externo,     
                               correspondente}*        

  **Numero_Oab**               *código (até 10),       ---
                               opcional*               

  **ID_Estado_Oab**            *referência             Seccional da OAB.
                               (Cad_Estado, opcional)* 

  **ID_Procuracao**            *referência             Procuração que lhe dá poderes neste
                               (Cad_Procuracao,        processo (Fase 8 --- Jurídico, seção
                               opcional)*              12).

  **ID_Contrato_Honorarios**   *referência             Contrato de honorários, se houver.
                               (Cad_Gestao_Contrato,   
                               opcional)*              

  **Vigencia_Inicio**          *data*                  Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                  Último dia em que esta versão vale
                                                       (inclusive). Sempre preenchida:
                                                       31/12/9999 quando o fim é indefinido
                                                       (versão vigente) --- convenção da Fase
                                                       0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*       Por que esta versão foi criada.
  ---------------------------- ----------------------- ----------------------------------------

O que este cadastro substitui ou liga nos demais módulos:
Cad_Rh_Processo_Administrativo_Judicial (Folha & RH) foi aposentada e o
número passa para cá; Cad_Rh_Pensao_Alimenticia.ID_Processo_Judicial
aponta para Cad_Processo; Mov_Rh_Processo_Disciplinar.ID_Processo passou
a ID_Processo_Disciplinar, porque é sindicância ou PAD interno, e não
contencioso; Cad_Documento_Retencao.Sob_Processo_Judicial (booleano) deu
lugar a ID_Processo, e o sistema calcula a guarda suspensa enquanto o
processo estiver em andamento ou suspenso; Mov_Titulo.Origem_Tipo ganhou
processo_judicial, processo_trabalhista e distribuicao_lucro;
Mov_Lote_Lancamento.Origem_Tipo ganhou os valores de provisão, depósito
e distribuição; Cad_Bloco_Fechamento ganhou o bloco juridico, que trava
criação e alteração de prognóstico, de movimento de depósito e de
deliberação de distribuição de lucros em competência fechada.

3\. Juízo, Andamentos e Prognóstico (CPC 25)

Mov_Processo_Juizo

Onde o processo tramita, com o histórico da movimentação. O processo
pode nascer numa vara e ser transferido para outra (redistribuição,
declínio de competência), ou subir para outra instância em recurso; cada
passagem é uma linha, e a vigente é a que cobre a data. O tribunal, a
vara e a classe processual saíram de Cad_Processo para cá, porque mudam
a cada movimentação.

*Vigência: sim --- a vigência é o período em que o processo esteve
naquele juízo. Regra de integridade: no mesmo processo, um único juízo
por data, sem buracos entre a distribuição e o encerramento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Juizo** | *identificador* | --- |
| **ID_Processo** | *referência (Cad_Processo)* | --- |
| **Instancia** | *enumeração {primeiro_grau, segundo_grau, tribunal_superior, supremo_tribunal_federal, administrativa}* | --- |
| **ID_Tribunal** | *referência (Cad_Classe_Sistema, domínio = orgao_judicial_cnj, opcional)* | Órgão do Judiciário (segmento e tribunal do número CNJ), ou o órgão administrativo. Domínio, com a carga da tabela do CNJ. |
| **ID_Estado** | *referência (Cad_Estado, opcional)* | UF da vara ou do órgão. |
| **ID_Municipio** | *referência (Cad_Municipio, opcional)* | Comarca ou município da vara. |
| **Identificador_Vara** | *código (até 4), opcional* | Código da vara ou do órgão julgador (idVara do eSocial). |
| **Nome_Vara_Ou_Orgao** | *texto, opcional* | Ex.: "3ª Vara do Trabalho de Sorocaba", "2ª Turma". |
| **ID_Classe_Processual** | *referência (Cad_Classe_Sistema, domínio = classe_processual_cnj, opcional)* | Classe na instância, da Tabela Processual Unificada. Muda quando o processo sobe em recurso. |
| **Motivo_Movimentacao** | *enumeração {distribuicao_inicial, redistribuicao, declinio_competencia, remessa_em_recurso, retorno_do_recurso, outro}* | Por que o processo passou a tramitar aqui. A primeira linha é sempre distribuicao_inicial. |
| **ID_Juizo_Anterior** | *referência (Mov_Processo_Juizo, autorreferência, opcional)* | De onde veio. Vazio na distribuição inicial. |
| **ID_Andamento_Origem** | *referência (Mov_Processo_Andamento, opcional)* | O andamento que registrou a remessa ou a redistribuição. |
| **Numero_No_Orgao** | *código (30), opcional* | Número do processo no órgão de destino, quando o recurso recebe numeração própria. O número de Cad_Processo é o de origem. |
| **ID_Orgao_Administrativo** | *referência (Cad_Classe_Sistema, domínio = orgao_processo_administrativo, opcional)* | Novo na revisão 3 (documento 44). Órgão do processo administrativo (1020 e 1809): RFB, DRJ, CARF ou outro. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 3 --- campos novos (documento 44): ID_Orgao_Administrativo.*

Mov_Processo_Andamento

Cada movimento do processo e cada prazo que ele cria.

*Vigência: não --- registra um evento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Andamento** | *identificador* | --- |
| **ID_Processo** | *referência (Cad_Processo)* | --- |
| **Data_Hora_Andamento** | *data/hora* | --- |
| **ID_Tipo_Andamento** | *referência (Cad_Classe_Sistema, domínio = tipo_andamento_processo)* | Movimentos mais usados da TPU do CNJ. |
| **Descricao** | *texto* | --- |
| **ID_Documento** | *referência (Cad_Documento, opcional)* | Peça, decisão ou publicação guardada no GED. |
| **ID_Pericia** | *referência (Mov_Processo_Pericia, opcional)* | Preenchido quando o andamento trata de uma perícia (Fase 8 --- Jurídico, seção 6). |
| **Origem_Andamento** | *enumeração {manual, publicacao, integracao_tribunal}* | --- |
| **Data_Prazo_Fatal** | *data, opcional* | Preenchida quando o andamento abre um prazo. |
| **Data_Prazo_Cumprido** | *data, opcional* | --- |
| **ID_Participante_Responsavel_Prazo** | *referência (Cad_Participante, opcional)* | --- |
| **Tipo_Ciencia** | *enumeração {intimacao, comunicado}, opcional* | Novo na revisão 3 (documento 37). Tipo da ciência do e-Processo: intimação ou simples comunicado. |
| **Natureza_Ciencia** | *enumeração {eletronica, postal, pessoal, edital}, opcional* | Novo na revisão 3 (documento 37). Natureza da ciência; ela se efetiva conforme a natureza (no edital, no fim da validade ou no comparecimento). |
| **Data_Ciencia** | *data, opcional* | Novo na revisão 3 (documento 37). Data da ciência, de onde conta o prazo de manifestação. |
| **Prazo_Manifestacao_Dias** | *número, opcional* | Novo na revisão 3 (documento 37). Prazo para manifestação, em dias contados da ciência; informado pelo ato e nunca fixo. |
| **Situacao_Ciencia** | *enumeração {pendente, efetivada, arquivada}, opcional* | Novo na revisão 3 (documento 37). Situação da ciência: pendente, efetivada ou arquivada. |

*Revisão 3 --- campos novos (documento 37): Tipo_Ciencia, Natureza_Ciencia, Data_Ciencia, Prazo_Manifestacao_Dias, Situacao_Ciencia.*

Mov_Processo_Prognostico

Avaliação do risco de perda, pelo CPC 25, e a decisão da empresa sobre o
tratamento contábil. O sistema sugere pelo CPC 25 (provável: provisão;
possível: divulgação em nota explicativa; remoto: nada), mas quem decide
é a empresa. Só uma avaliação vale por vez (a janela de vigência não se
sobrepõe).

*Vigência: sim --- o prognóstico e o valor estimado mudam ao longo do
processo; o histórico responde à auditoria.*

  ------------------------------- --------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**             **Descrição / regra**

  **ID_Prognostico**              *identificador*             ---

  **ID_Processo**                 *referência (Cad_Processo)* ---

  **Data_Avaliacao**              *data*                      ---

  **ID_Participante_Avaliador**   *referência                 Advogado interno ou externo que emitiu o
                                  (Cad_Participante)*         parecer.

  **Classificacao_Risco**         *enumeração {provavel,      ---
                                  possivel, remoto}*          

  **Valor_Estimado_Perda**        *número, opcional*          ---

  **Base_Estimativa**             *enumeração {laudo_externo, ---
                                  avaliacao_interna,          
                                  valor_causa,                
                                  calculo_pericial, outro}*   

  **Fundamentacao**               *texto*                     ---

  **Tratamento_Sugerido**         *enumeração {provisionar,   Calculado e armazenado pelo CPC 25 a
                                  divulgar_sem_provisao,      partir de Classificacao_Risco: provável
                                  sem_registro}*              = provisionar; possível =
                                                              divulgar_sem_provisao; remoto =
                                                              sem_registro.

  **Tratamento_Contabil**         *enumeração {provisionar,   A decisão da empresa. Começa igual à
                                  divulgar_sem_provisao,      sugestão e pode ser mudada por quem tem
                                  sem_registro}*              alçada.

  **Justificativa_Tratamento**    *texto, opcional*           Obrigatória quando Tratamento_Contabil
                                                              difere de Tratamento_Sugerido. O
                                                              contador e o auditor leem essa
                                                              justificativa; a divergência do CPC 25
                                                              fica visível no relatório de
                                                              contingências.

  **Valor_Provisionado**          *número*                    Igual a Valor_Estimado_Perda quando
                                                              Tratamento_Contabil = provisionar; zero
                                                              nos demais.

  **Valor_Divulgado**             *número*                    Valor a divulgar em nota explicativa
                                                              quando Tratamento_Contabil =
                                                              divulgar_sem_provisao.

  **ID_Lote**                     *referência                 Lançamento da diferença de provisão
                                  (Mov_Lote_Lancamento,       contra a avaliação anterior.
                                  opcional)*                  

  **ID_Instancia_Aprovacao**      *referência                 Mudança de classificação ou de valor
                                  (Mov_Aprovacao_Instancia,   acima do limite da régua de aprovação da
                                  opcional)*                  Fase 0 exige aprovação.

  **Vigencia_Inicio**             *data*                      Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                *data*                      Último dia em que esta versão vale
                                                              (inclusive). Sempre preenchida:
                                                              31/12/9999 quando o fim é indefinido
                                                              (versão vigente) --- convenção da Fase
                                                              0, seção 2.

  **Motivo_Vigencia**             *texto, opcional*           Por que esta versão foi criada.
  ------------------------------- --------------------------- ----------------------------------------

Como a provisão sai: a provisão nasce da decisão da empresa
(Tratamento_Contabil), e não da classificação de risco isolada. Quando a
nova avaliação aumenta o valor provisionado, o lote sai com Origem_Tipo
= provisao_contingencia; quando diminui ou muda para possível ou remoto,
com reversao_provisao_contingencia; a atualização monetária e os juros
da provisão saem como atualizacao_provisao_contingencia. Os três valores
são novos em Mov_Lote_Lancamento.Origem_Tipo. O contador escolhe as
contas de resultado e de passivo no Motor de Regras, como nas demais
provisões da Fase 0; o Jurídico não conhece plano de contas.

4\. Depósitos Judiciais e Garantias

Mov_Processo_Deposito_Garantia

Depósito judicial ou recursal e qualquer garantia oferecida ou tomada no
processo (seguro-garantia, carta de fiança, penhora, bloqueio, caução).
Quando o depósito é integral e suspende a exigibilidade de tributo, é
Mov_Processo_Suspensao que aponta para ele.

*Vigência: não --- o saldo e as mudanças estão em
Mov_Processo_Deposito_Movimento.*

  ----------------------------- ---------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**        **Descrição / regra**

  **ID_Deposito_Garantia**      *identificador*        ---

  **ID_Processo**               *referência            ---
                                (Cad_Processo)*        

  **Tipo_Garantia**             *enumeração            ---
                                {deposito_judicial,    
                                deposito_recursal,     
                                seguro_garantia,       
                                carta_fianca, penhora, 
                                bloqueio_judicial,     
                                caucao, outro}*        

  **Data_Constituicao**         *data*                 ---

  **Valor_Original**            *número*               ---

  **Data_Vencimento**           *data, opcional*       Apólice ou fiança com prazo.

  **ID_Participante_Emissor**   *referência            Seguradora ou banco.
                                (Cad_Participante,     
                                opcional)*             

  **Numero_Documento**          *código (40),          Guia, apólice ou carta de fiança.
                                opcional*              

  **ID_Conta_Bancaria**         *referência            Conta judicial ou conta debitada.
                                (Cad_Conta_Bancaria,   
                                opcional)*             

  **ID_Baixa**                  *referência            Pagamento que originou o depósito,
                                (Mov_Titulo_Baixa,     quando passou por Contas a Pagar.
                                opcional)*             

  **ID_Documento**              *referência            ---
                                (Cad_Documento,        
                                opcional)*             

  **Situacao**                  *enumeração {vigente,  ---
                                levantado,             
                                convertido_em_renda,   
                                substituido,           
                                expirado}*             

  **Data_Encerramento**         *data, opcional*       ---
  ----------------------------- ---------------------- ----------------------------------------

Mov_Processo_Deposito_Movimento

Cada movimento do depósito, que gera lançamento contábil próprio.

*Vigência: não.*

  --------------------------- ----------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                     **Descrição / regra**

  **ID_Deposito_Movimento**   *identificador*                     ---

  **ID_Deposito_Garantia**    *referência                         ---
                              (Mov_Processo_Deposito_Garantia)*   

  **Tipo_Movimento**          *enumeração {constituicao,          ---
                              complemento, atualizacao,           
                              levantamento, conversao_em_renda}*  

  **Data_Movimento**          *data*                              ---

  **Valor**                   *número*                            ---

  **ID_Lote**                 *referência (Mov_Lote_Lancamento,   Origem_Tipo = deposito_judicial
                              opcional)*                          (constituição e complemento),
                                                                  atualizacao_deposito_judicial ou
                                                                  levantamento_deposito_judicial
                                                                  (levantamento e conversão em renda).
  --------------------------- ----------------------------------- ----------------------------------------

5\. Suspensão de Exigibilidade (S-1070, R-1070, LC 224)

O processo pode suspender a cobrança de um tributo por liminar,
depósito, tutela ou sentença (CTN art. 151). O eSocial (S-1070) e a
Reinf (R-1070) pedem que essa suspensão seja cadastrada antes de ser
usada na declaração. Uma entidade só serve às duas obrigações e aos usos
internos: a retenção, o estabelecimento do eSocial, a lotação, a
apuração de IRPJ e CSLL. É a peça que liga o processo à tributação. As
liminares contra a LC 224/2025 usam o mesmo caminho: o Tribunal Regional
Federal decide caso a caso e há ações diretas de inconstitucionalidade
pendentes (7936 e 7982; resultado não confirmado), então o sistema
guarda a decisão e o efeito de cada empresa, sem assumir qual lado
vence.

Mov_Processo_Suspensao

Uma suspensão de exigibilidade que um processo concede sobre um tributo
ou contribuição. A vigência é a da eficácia da decisão.

*Vigência: sim --- a liminar vale de uma data a outra; cassação ou
revogação encerra a vigência. O envio ao eSocial e à Reinf fica em
Mov_Esocial_Evento e no evento da Reinf.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Processo_Suspensao** | *identificador* | --- |
| **ID_Processo** | *referência (Cad_Processo)* | --- |
| **ID_Indicativo_Suspensao** | *referência (Cad_Classe_Sistema, domínio = codigo_suspensao_esocial)* | indSusp: liminar, depósito, tutela antecipada, sentença, acórdão e demais valores (13 valores na Reinf: 01 a 05, 08 a 13, 90 e 92; os códigos 06 e 07 não existem, conferido no leiaute 2.1.2b, R-1070). Processo administrativo aceita só 03, 90 e 92; processo judicial aceita os demais. Mesmo domínio já existente; que o eSocial usa os mesmos 13 valores não foi conferido (revisão 16, documento 82, D-N246). |
| **Codigo_Suspensao** | *código (14), opcional* | codSusp: número da decisão, do depósito ou do ato que suspende. |
| **Data_Decisao** | *data* | dtDecisao. |
| **Deposito_Integral** | *booleano* | indDeposito. |
| **ID_Deposito_Garantia** | *referência (Mov_Processo_Deposito_Garantia, opcional)* | O depósito que sustenta a suspensão. |
| **ID_Imposto** | *referência (Cad_Imposto, opcional)* | Tributo ou contribuição que a decisão alcança. |
| **Abrangencia** | *enumeração {contribuicao_previdenciaria, rat, fap, terceiros, irrf_retencao, pis_cofins, irpj_csll, acrescimo_lc_224, outra}* | Escopo da decisão dentro do tributo. |
| **Situacao_Eficacia** | *enumeração {vigente, cassada, revogada, transitada_em_julgado}* | --- |
| **Observacao** | *texto, opcional* | --- |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 16 --- campos alterados: ID_Indicativo_Suspensao.*

A decisão da empresa sobre recolher ou assumir o risco do acréscimo da
LC 224/2025, com a régua de aprovação, o depósito e a provisão, é
registrada em Mov_Apuracao_Decisao_Risco (Contabilidade & Fiscal,
revisão 17), que referencia esta suspensão, o prognóstico (seção 3) e o
depósito (seção 4).

6\. Perícia: Acompanhamento, Perito, Assistentes Técnicos e Fase

Requisito de Alberto: o processo pode passar por perícia, e o sistema
acompanha a perícia --- quem é o perito, quem são os assistentes
técnicos e em que momento ela está. O rito segue a prova pericial do
Código de Processo Civil (arts. 464 a 480): o juízo determina, nomeia o
perito, fixa honorários, as partes indicam assistentes técnicos e
apresentam quesitos, há a diligência, o laudo e a manifestação das
partes sobre ele. A fase atual é sempre a última do histórico de fases,
e a data do laudo aciona a reavaliação do prognóstico (seção 3).

Mov_Processo_Pericia

Uma perícia dentro de um processo. Um processo pode ter mais de uma
(contábil e médica, por exemplo).

*Vigência: não --- o andamento da perícia está em
Mov_Processo_Pericia_Fase.*

  -------------------------------------- ---------------------------------- ----------------------------------------
  **Campo**                              **Tipo lógico**                    **Descrição / regra**

  **ID_Pericia**                         *identificador*                    ---

  **ID_Processo**                        *referência (Cad_Processo)*        ---

  **ID_Juizo**                           *referência (Mov_Processo_Juizo,   O juízo que determinou a perícia.
                                         opcional)*                         

  **ID_Tipo_Pericia**                    *referência (Cad_Classe_Sistema,   contabil, medica, engenharia,
                                         domínio = tipo_pericia)*           insalubridade_periculosidade,
                                                                            grafotecnica, informatica_forense,
                                                                            avaliacao_de_bens, outra.

  **Objeto**                             *texto*                            O que o juízo mandou periciar.

  **Requerente**                         *enumeração {mlegate,              ---
                                         parte_contraria, juizo_de_oficio}* 

  **Data_Determinacao**                  *data*                             ---

  **Responsavel_Honorarios**             *enumeração {mlegate,              ---
                                         parte_contraria, dividido,         
                                         justica_gratuita}*                 

  **Valor_Honorarios_Proposto**          *número, opcional*                 Proposta do perito.

  **Valor_Honorarios_Fixado**            *número, opcional*                 Valor arbitrado pelo juízo.

  **ID_Deposito_Garantia**               *referência                        Depósito dos honorários, quando a
                                         (Mov_Processo_Deposito_Garantia,   Mlegate é a responsável.
                                         opcional)*                         

  **ID_Titulo_Honorarios**               *referência (Mov_Titulo,           Título a pagar dos honorários
                                         opcional)*                         (Origem_Tipo = processo_judicial).

  **ID_Fase_Atual**                      *referência (Cad_Classe_Sistema,   Calculada e armazenada: a última fase de
                                         domínio = fase_pericia)*           Mov_Processo_Pericia_Fase.

  **Data_Prazo_Proxima_Etapa**           *data, opcional*                   Calculada e armazenada a partir do prazo
                                                                            da última fase. Alimenta o aviso de
                                                                            prazo da Fase 0.

  **Data_Laudo**                         *data, opcional*                   ---

  **ID_Documento_Laudo**                 *referência (Cad_Documento,        Laudo no GED. Em perícia médica ou de
                                         opcional)*                         insalubridade, a classe do documento é
                                                                            sensível (Fase 0, seção 13).

  **Resultado_Laudo**                    *enumeração {pendente, favoravel,  Do ponto de vista da Mlegate.
                                         parcialmente_favoravel,            
                                         desfavoravel}*                     

  **Valor_Apurado_Laudo**                *número, opcional*                 Valor que o laudo apura. Serve de base
                                                                            ao prognóstico (Base_Estimativa =
                                                                            calculo_pericial).

  **Reavaliacao_Prognostico_Pendente**   *booleano*                         Calculado e armazenado: verdadeiro
                                                                            quando há laudo e nenhuma avaliação de
                                                                            Mov_Processo_Prognostico posterior à
                                                                            data do laudo.

  **ID_Ambiente_Trabalho**               *referência                        Na perícia de insalubridade ou
                                         (Cad_Rh_Ambiente_Trabalho,         periculosidade, o ambiente periciado.
                                         opcional)*                         
  -------------------------------------- ---------------------------------- ----------------------------------------

Mov_Processo_Pericia_Fase

O histórico das fases da perícia: em que momento ela se encontra e por
onde passou.

*Vigência: não --- registra um evento.*

  --------------------------------- -------------------------- ----------------------------------------
  **Campo**                         **Tipo lógico**            **Descrição / regra**

  **ID_Pericia_Fase**               *identificador*            ---

  **ID_Pericia**                    *referência                ---
                                    (Mov_Processo_Pericia)*    

  **ID_Fase_Pericia**               *referência                determinada, perito_nomeado,
                                    (Cad_Classe_Sistema,       proposta_de_honorarios,
                                    domínio = fase_pericia)*   honorarios_fixados,
                                                               honorarios_depositados,
                                                               assistentes_e_quesitos_indicados,
                                                               diligencia_agendada,
                                                               diligencia_realizada, laudo_entregue,
                                                               manifestacao_sobre_laudo,
                                                               esclarecimentos_solicitados,
                                                               laudo_complementar, encerrada,
                                                               cancelada. A lista é do sistema, e não
                                                               oficial, e acompanha o rito; os códigos
                                                               são numerados na ordem usual (10, 20,
                                                               30...), mas a perícia pode pular ou
                                                               repetir fases.

  **Data_Hora_Fase**                *data/hora*                ---

  **Data_Prazo**                    *data, opcional*           Prazo da etapa seguinte, quando a fase
                                                               abre um.

  **ID_Andamento_Origem**           *referência                O andamento do processo que registrou a
                                    (Mov_Processo_Andamento,   fase.
                                    opcional)*                 

  **ID_Participante_Responsavel**   *referência                Quem na Mlegate acompanha a etapa.
                                    (Cad_Participante,         
                                    opcional)*                 

  **Observacao**                    *texto, opcional*          ---
  --------------------------------- -------------------------- ----------------------------------------

Mov_Processo_Pericia_Profissional

O perito e os assistentes técnicos da perícia. Os dados de contato saem
de Cad_Participante; o registro no conselho profissional fica aqui.

*Vigência: sim --- a substituição do perito ou do assistente é uma nova
versão, com o motivo.*

  -------------------------------------- -------------------------------------- ----------------------------------------
  **Campo**                              **Tipo lógico**                        **Descrição / regra**

  **ID_Pericia_Profissional**            *identificador*                        ---

  **ID_Pericia**                         *referência (Mov_Processo_Pericia)*    ---

  **ID_Participante**                    *referência (Cad_Participante)*        Pessoa física ou empresa.

  **Papel**                              *enumeração {perito_judicial,          ---
                                         assistente_tecnico_mlegate,            
                                         assistente_tecnico_parte_contraria}*   

  **ID_Conselho_Profissional**           *referência (Cad_Classe_Sistema,       CRC, CREA, CRM, CORECON, CAU e outros.
                                         domínio = conselho_profissional,       
                                         opcional)*                             

  **Numero_Registro**                    *código (20), opcional*                ---

  **ID_Estado_Registro**                 *referência (Cad_Estado, opcional)*    ---

  **Especialidade**                      *texto, opcional*                      ---

  **Data_Indicacao**                     *data*                                 Nomeação do perito ou indicação do
                                                                                assistente.

  **Data_Fim**                           *data, opcional*                       Substituição ou dispensa.

  **Impedimento_Ou_Suspeicao_Arguida**   *booleano*                             ---

  **Data_Arguicao**                      *data, opcional*                       ---

  **Resultado_Arguicao**                 *enumeração {pendente, acolhida,       ---
                                         rejeitada}, opcional*                  

  **Valor_Honorarios_Acordado**          *número, opcional*                     Só do assistente técnico da Mlegate.

  **ID_Contrato_Honorarios**             *referência (Cad_Gestao_Contrato,      ---
                                         opcional)*                             

  **Data_Parecer**                       *data, opcional*                       Parecer do assistente técnico sobre o
                                                                                laudo.

  **ID_Documento_Parecer**               *referência (Cad_Documento, opcional)* ---

  **Vigencia_Inicio**                    *data*                                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                       *data*                                 Último dia em que esta versão vale
                                                                                (inclusive). Sempre preenchida:
                                                                                31/12/9999 quando o fim é indefinido
                                                                                (versão vigente) --- convenção da Fase
                                                                                0, seção 2.

  **Motivo_Vigencia**                    *texto, opcional*                      Por que esta versão foi criada.
  -------------------------------------- -------------------------------------- ----------------------------------------

Mov_Processo_Pericia_Quesito

Os quesitos da perícia e as respostas do perito.

*Vigência: não.*

  --------------------- ------------------------- ----------------------------------------
  **Campo**             **Tipo lógico**           **Descrição / regra**

  **ID_Quesito**        *identificador*           ---

  **ID_Pericia**        *referência               ---
                        (Mov_Processo_Pericia)*   

  **Autoria**           *enumeração {mlegate,     ---
                        parte_contraria, juizo}*  

  **Numero_Quesito**    *número*                  ---

  **Texto_Quesito**     *texto*                   ---

  **Resposta_Perito**   *texto, opcional*         ---

  **Data_Resposta**     *data, opcional*          ---
  --------------------- ------------------------- ----------------------------------------

Ligações: Mov_Processo_Andamento ganha ID_Pericia (opcional), para o
andamento que trata da perícia; o pagamento dos honorários usa Contas a
Pagar e o depósito da seção 4; a mudança de fase que passa por laudo
entregue gera o aviso de reavaliação do prognóstico. O laudo em perícia
médica ou de insalubridade é dado de saúde: a classe de documento
correspondente é sensível.

7\. Capital Social e Atos Societários

Cad_Empresa_Socio e Cad_Empresa_Responsavel ficam na Fase 0, como
decidido. O Jurídico acrescenta o que faltava em volta deles: o capital
social, os atos que criam e mudam a sociedade, e a distribuição de
lucros e de juros sobre o capital próprio. A distribuição é o que
alimenta os valores pagos por sócio do registro Y600 da ECF, que o Bloco
2 deixou esperando (V-28); o pró-labore vem da folha.

Mov_Ato_Societario

Contrato social, alteração, ata de assembleia ou de reunião, distrato e
demais atos que mudam a sociedade ou deliberam sobre ela, com o
arquivamento na Junta Comercial.

*Vigência: não --- registra o ato. Ato de retificação é outro registro.*

  ------------------------- ----------------------- ----------------------------------------
  **Campo**                 **Tipo lógico**         **Descrição / regra**

  **ID_Ato_Societario**     *identificador*         ---

  **ID_Empresa**            *referência             ---
                            (Cad_Empresa)*          

  **ID_Tipo_Ato**           *referência             contrato_social, alteracao_contratual,
                            (Cad_Classe_Sistema,    distrato, ata_assembleia,
                            domínio =               ata_reuniao_socios, ata_conselho,
                            tipo_ato_societario)*   ata_diretoria,
                                                    protocolo_incorporacao_cisao_fusao.

  **Data_Ato**              *data*                  ---

  **Descricao**             *texto*                 O que o ato decide.

  **ID_Junta_Comercial**    *referência             ---
                            (Cad_Junta_Comercial,   
                            opcional)*              

  **Numero_Arquivamento**   *código (até 20),       NIRE ou número do protocolo de
                            opcional*               arquivamento.

  **Data_Arquivamento**     *data, opcional*        ---

  **ID_Documento**          *referência             O ato assinado, no GED.
                            (Cad_Documento,         
                            opcional)*              

  **ID_Ato_Retificado**     *referência             ---
                            (Mov_Ato_Societario,    
                            autorreferência,        
                            opcional)*              

  **Situacao**              *enumeração {rascunho,  ---
                            assinado, arquivado,    
                            cancelado}*             
  ------------------------- ----------------------- ----------------------------------------

Cad_Empresa_Capital_Social

Capital social da empresa, com histórico.

*Vigência: sim --- cada aumento ou redução é uma nova versão, com o ato
que a motivou.*

  ----------------------------- ----------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**         **Descrição / regra**

  **ID_Capital_Social**         *identificador*         ---

  **ID_Empresa**                *referência             ---
                                (Cad_Empresa)*          

  **Valor_Subscrito**           *número*                ---

  **Valor_Integralizado**       *número*                ---

  **Quantidade_Quotas_Acoes**   *número, opcional*      ---

  **Valor_Nominal**             *número, opcional*      Valor de cada quota ou ação.

  **ID_Ato_Societario**         *referência             O ato que fixou esse capital.
                                (Mov_Ato_Societario)*   

  **Vigencia_Inicio**           *data*                  Primeiro dia em que esta versão vale.

  **Vigencia_Fim**              *data*                  Último dia em que esta versão vale
                                                        (inclusive). Sempre preenchida:
                                                        31/12/9999 quando o fim é indefinido
                                                        (versão vigente) --- convenção da Fase
                                                        0, seção 2.

  **Motivo_Vigencia**           *texto, opcional*       Por que esta versão foi criada.
  ----------------------------- ----------------------- ----------------------------------------

Nas entidades da Fase 0, ganham ID_Ato_Societario (opcional):
Cad_Empresa_Socio (o ato que admitiu ou alterou a participação) e
Cad_Empresa_Responsavel (o ato que nomeou o administrador ou o
procurador). Em Cad_Empresa_Responsavel, Tipo_Papel ganha
encarregado_dados (seção 10), e Registro_Crc, um texto que repete
Estado_Crc e Numero_Sequencial_Crc, é aposentado (Fase 0, seção 6).

8\. Distribuição de Lucros e JCP (Lei 15.270/2025)

A Lei 15.270/2025 passou a reter 10% de imposto de renda na fonte sobre
lucros e dividendos que uma mesma pessoa jurídica paga a uma mesma
pessoa física acima de R\$ 50 mil no mês (pelo que li, incidindo sobre o
total pago no mês, e não só sobre o excedente; o parâmetro abaixo aceita
as duas leituras), com transição para lucros apurados até 2025 e
deliberados até 31/12/2025, e 10% também para o beneficiário no
exterior. O JCP tem alíquota própria. Como a legislação mudou há pouco e
pode mudar de novo, todos os números vão para parâmetro com vigência, e
a carga inicial sai marcada como provisória.

Cad_Distribuicao_Lucro_Parametro

Parâmetros da retenção sobre distribuição de lucros e JCP. Uma linha por
vigência.

*Vigência: sim --- a legislação mudou em 2025 e pode mudar de novo; a
distribuição usa a versão vigente na data do pagamento.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Parametro_Distribuicao** | *identificador* | --- |
| **Limite_Mensal_Retencao** | *número* | Carga inicial: R\$ 50 mil por fonte pagadora e beneficiário pessoa física no mês de pagamento. Provisório. |
| **Base_Incidencia** | *enumeração {total_pago_no_mes, excedente_ao_limite}* | Como a retenção incide quando o limite é passado. Carga inicial: total_pago_no_mes. Provisório. |
| **Criterio_Acumulo_Fonte** | *enumeração {cnpj_raiz, cnpj_completo}* | O que conta como "mesma fonte pagadora" no acúmulo. Carga inicial: cnpj_raiz (mesma pessoa jurídica). Provisório. |
| **Aliquota_Irrf_Residente** | *número* | Carga inicial: 10%. |
| **Aliquota_Irrf_Nao_Residente** | *número* | Carga inicial: 10%. |
| **Aliquota_Irrf_Jcp** | *número* | Carga: 17,5% desde 01/01/2026 (LC 224/2025, art. 8º, que reescreve o art. 9º, § 2º, da Lei 9.249). A linha anterior, de 15%, vale até 31/12/2025. |
| **ID_Calendario_Corte_Lucro** | *referência (Cad_Calendario_Transicao)* | Revisão 11 (documento 72, D-N193): A linha do calendário com o parâmetro corte_lucro_transicao (carga inicial 31/12/2025, provisório). Lucro apurado até essa data e deliberado até a data limite fica fora da retenção. Antes Data_Corte_Lucro_Transicao, data. |
| **ID_Calendario_Limite_Deliberacao** | *referência (Cad_Calendario_Transicao)* | Revisão 11 (documento 72, D-N193): A linha do calendário com o parâmetro limite_deliberacao_lucro_transicao (carga inicial 31/12/2025, provisório). Antes Data_Limite_Deliberacao_Transicao, data. |
| **ID_Calendario_Limite_Pagamento** | *referência (Cad_Calendario_Transicao, opcional)* | Revisão 11 (documento 72, D-N193): A linha do calendário com o parâmetro limite_pagamento_lucro_transicao (carga inicial 31/12/2028, parâmetro sem valor fixo, ajustável por versão nova da linha; antes só o ano 2028; Q72-2 respondida em 19/10/2026). Antes Ano_Limite_Pagamento_Transicao, número. |
| **Codigo_Receita_Darf** | *código (4), opcional* | Carga inicial: 1841. Não confirmado. |
| **ID_Natureza_Rendimento** | *referência (Cad_Natureza_Rendimento, opcional)* | Natureza do rendimento na Reinf, em geral a de lucros e dividendos. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Fase 0, seção 9 (validação de dados legais provisórios). A carga inicial entra como provisória e só passa a validada com a aprovação de RH e contador. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia, opcional)* | Validação pela régua de aprovação (Fase 0, seção 9). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 4 --- campos alterados (documento 51): Aliquota_Irrf_Jcp.*

*Revisão 11 --- campos que mudam de nome e de tipo: Data_Corte_Lucro_Transicao → ID_Calendario_Corte_Lucro; Data_Limite_Deliberacao_Transicao → ID_Calendario_Limite_Deliberacao; Ano_Limite_Pagamento_Transicao → ID_Calendario_Limite_Pagamento.*

*Revisão 12 --- campos alterados: ID_Calendario_Limite_Pagamento.*

Mov_Distribuicao_Lucro

A deliberação de distribuir lucros ou pagar JCP, pelo ato societário que
a aprovou.

*Vigência: não --- registra a deliberação.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Distribuicao_Lucro** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | --- |
| **ID_Ato_Societario** | *referência (Mov_Ato_Societario)* | Ata ou alteração que deliberou. |
| **Tipo_Distribuicao** | *enumeração {dividendo, jcp, antecipacao_lucro}* | --- |
| **Data_Referencia_Lucro** | *data* | Data do balanço ou do período de que o lucro sai. |
| **Data_Deliberacao** | *data* | --- |
| **Data_Pagamento_Prevista** | *data, opcional* | --- |
| **Valor_Total_Deliberado** | *número* | --- |
| **Forma_Rateio** | *enumeração {proporcional_participacao, desproporcional_conforme_ato}* | A desproporcional exige que o ato societário a autorize. |
| **Lucro_Regime_Transicao** | *booleano* | Calculado e armazenado: verdadeiro quando Data_Referencia_Lucro e Data_Deliberacao cabem nas datas de corte do parâmetro vigente. |
| **ID_Lote** | *referência (Mov_Lote_Lancamento, opcional)* | Lançamento da deliberação (Origem_Tipo = distribuicao_lucro ou juros_capital_proprio). |
| **ID_Jcp_Calculo** | *referência (Mov_Jcp_Calculo, opcional)* | Novo na revisão 4 (documento 51). Cálculo do limite do JCP que sustenta a deliberação. Só no tipo jcp. Sem a condição do dobro atendida, a deliberação emite alerta com justificativa. |
| **Situacao** | *enumeração {deliberada, paga_parcialmente, paga, cancelada}* | --- |

*Revisão 4 --- campos novos (documento 51): ID_Jcp_Calculo.*

Mov_Distribuicao_Lucro_Socio

A parte de cada sócio na deliberação.

*Vigência: não.*

  --------------------------------- --------------------------- ----------------------------------------
  **Campo**                         **Tipo lógico**             **Descrição / regra**

  **ID_Distribuicao_Lucro_Socio**   *identificador*             ---

  **ID_Distribuicao_Lucro**         *referência                 ---
                                    (Mov_Distribuicao_Lucro)*   

  **ID_Socio**                      *referência                 Sócio na data da deliberação.
                                    (Cad_Empresa_Socio)*        

  **Percentual_Rateio**             *número*                    ---

  **Valor_Deliberado**              *número*                    ---

  **ID_Titulo**                     *referência (Mov_Titulo,    Obrigação a pagar ao sócio (Origem_Tipo
                                    opcional)*                  = distribuicao_lucro).
  --------------------------------- --------------------------- ----------------------------------------

Mov_Distribuicao_Lucro_Pagamento

Cada pagamento ao sócio, com o cálculo da retenção do mês. O acúmulo é
sempre do mês do pagamento.

*Vigência: não --- registra o pagamento.*

  --------------------------------- --------------------------------- ----------------------------------------
  **Campo**                         **Tipo lógico**                   **Descrição / regra**

  **ID_Pagamento_Lucro**            *identificador*                   ---

  **ID_Distribuicao_Lucro_Socio**   *referência                       ---
                                    (Mov_Distribuicao_Lucro_Socio)*   

  **ID_Baixa**                      *referência (Mov_Titulo_Baixa)*   O pagamento real.

  **Data_Pagamento**                *data*                            ---

  **Valor_Pago**                    *número*                          ---

  **Beneficiario_No_Exterior**      *booleano*                        Calculado do país do endereço vigente do
                                                                      sócio na data.

  **Valor_Acumulado_Antes**         *número*                          Total já pago no mês pela mesma fonte ao
                                                                      mesmo beneficiário.

  **Valor_Isento_Transicao**        *número*                          Parte que pertence ao lucro de
                                                                      transição.

  **Valor_Base_Irrf**               *número*                          Base da retenção, conforme
                                                                      Base_Incidencia do parâmetro.

  **Valor_Irrf**                    *número*                          ---

  **ID_Retencao**                   *referência (Mov_Titulo_Retencao, Retenção gerada, com natureza de
                                    opcional)*                        rendimento e código de receita para a
                                                                      Reinf e a DIRF substituta.
  --------------------------------- --------------------------------- ----------------------------------------

Como usa: o pagamento que faz o acumulado do mês passar do limite gera a
retenção do mês inteiro (ou do excedente, conforme o parâmetro) naquele
mesmo pagamento; a retenção é um Mov_Titulo_Retencao, com natureza do
rendimento (Bloco 2) e, quando a parte isenta é declarada, o tipo de
isenção da Reinf. O ECF Y600 soma por sócio e por ano os valores pagos
desta seção e o pró-labore da folha. Os títulos de pagamento passam pela
mesma régua de aprovação e pela mesma conciliação bancária dos demais.

9\. Beneficiário Final (e-BEF, IN RFB 2.290/2025)

A Instrução Normativa RFB 2.290/2025 (e-BEF) obriga a informar quem,
pessoa física, controla a empresa, ainda que por cadeia de outras
empresas. Não estava no relatório 15; Alberto decidiu que entra agora, e
a decisão foi aplicada nesta revisão. Como o quadro societário direto
(Cad_Empresa_Socio) já está na Fase 0, o custo é uma entidade só.

Cad_Empresa_Beneficiario_Final

Pessoa física que controla a empresa, direta ou indiretamente.

*Vigência: sim.*

  ---------------------------- ---------------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**              **Descrição / regra**

  **ID_Beneficiario_Final**    *identificador*              ---

  **ID_Empresa**               *referência (Cad_Empresa)*   ---

  **ID_Participante**          *referência                  ---
                               (Cad_Participante, classe    
                               pessoa física)*              

  **Tipo_Controle**            *enumeração                  ---
                               {participacao_capital,       
                               direitos_de_voto,            
                               controle_por_outros_meios,   
                               direcao}*                    

  **Percentual_Direto**        *número, opcional*           Vem de Cad_Empresa_Socio quando é sócio
                                                            direto.

  **Percentual_Indireto**      *número, opcional*           Soma dos percentuais na cadeia.

  **ID_Socio_Intermediario**   *referência                  Primeira empresa da cadeia, quando
                               (Cad_Empresa_Socio,          indireto.
                               opcional)*                   

  **Vigencia_Inicio**          *data*                       Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                       Último dia em que esta versão vale
                                                            (inclusive). Sempre preenchida:
                                                            31/12/9999 quando o fim é indefinido
                                                            (versão vigente) --- convenção da Fase
                                                            0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*            Por que esta versão foi criada.
  ---------------------------- ---------------------------- ----------------------------------------

10\. LGPD

Hoje a LGPD só aparece no recrutamento (Cad_Pre_Cadastro). Faltam o
registro do que se trata e por quê, o consentimento fora do
recrutamento, o atendimento ao titular, o registro de incidentes e o
encarregado. O desenho segue os artigos 7, 8, 11, 18, 19, 37, 38, 41 e
48 e as Resoluções CD/ANPD 2/2022, 15/2024, 18/2024 e 19/2024. Prazos e
condições vão para parâmetro. Alberto acrescentou as regras de uso dos
equipamentos da empresa (celulares, computadores e outros), que entram
na seção 11 e se ligam à LGPD.

Cad_Lgpd_Parametro

Prazos legais que o sistema controla. Uma linha por vigência.

*Vigência: sim.*

  -------------------------------------------- --------------------------- ----------------------------------------
  **Campo**                                    **Tipo lógico**             **Descrição / regra**

  **ID_Lgpd_Parametro**                        *identificador*             ---

  **Prazo_Resposta_Titular_Dias**              *número*                    Carga inicial: 15 dias para a declaração
                                                                           completa (art. 19, II). Provisório.

  **Prazo_Comunicacao_Incidente_Dias_Uteis**   *número*                    Carga inicial: 3 dias úteis a partir da
                                                                           ciência (Resolução CD/ANPD 15/2024).
                                                                           Provisório.

  **Situacao_Dado**                            *enumeração {provisorio,    Fase 0, seção 9 (validação de dados
                                               validado}*                  legais provisórios). A carga inicial
                                                                           entra como provisória e só passa a
                                                                           validada com a aprovação de RH e
                                                                           contador.

  **ID_Instancia_Aprovacao**                   *referência                 Validação pela régua de aprovação (Fase
                                               (Mov_Aprovacao_Instancia,   0, seção 9).
                                               opcional)*                  

  **Vigencia_Inicio**                          *data*                      Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                             *data*                      Último dia em que esta versão vale
                                                                           (inclusive). Sempre preenchida:
                                                                           31/12/9999 quando o fim é indefinido
                                                                           (versão vigente) --- convenção da Fase
                                                                           0, seção 2.

  **Motivo_Vigencia**                          *texto, opcional*           Por que esta versão foi criada.
  -------------------------------------------- --------------------------- ----------------------------------------

Cad_Lgpd_Tratamento

Registro das operações de tratamento (art. 37): o que se trata, para quê
e com qual base legal.

*Vigência: sim --- a finalidade e a base legal mudam por decisão.*

  ------------------------------------ -------------------------- ----------------------------------------
  **Campo**                            **Tipo lógico**            **Descrição / regra**

  **ID_Tratamento**                    *identificador*            ---

  **ID_Tratamento_Versao**             *identificador da versão*  Chave primária da versão (tabela física
                                                                  Cad_Lgpd_Tratamento_Versao).
                                                                  ID_Tratamento é a identidade, única e
                                                                  referenciada pelas outras tabelas; cada
                                                                  versão guarda a sua janela de vigência
                                                                  --- Fase 0, seção 2.

  **ID_Empresa**                       *referência (Cad_Empresa)  ---
                                       --- identidade*            

  **Nome**                             *texto --- identidade*     Ex.: "Folha de pagamento", "Banco de
                                                                  talentos".

  **Finalidade**                       *texto*                    ---

  **ID_Base_Legal**                    *referência                Arts. 7 e 11.
                                       (Cad_Classe_Sistema,       
                                       domínio =                  
                                       base_legal_lgpd)*          

  **ID_Categoria_Titular**             *referência                colaborador, candidato, cliente,
                                       (Cad_Classe_Sistema,       fornecedor, socio, visitante,
                                       domínio =                  dependente.
                                       categoria_titular_lgpd)*   

  **Trata_Dado_Sensivel**              *booleano*                 Verdadeiro liga o tratamento aos campos
                                                                  de Cad_Dado_Sensivel.

  **Compartilhado_Com**                *texto, opcional*          Órgãos e terceiros que recebem os dados.

  **Transferencia_Internacional**      *booleano*                 Art. 33.

  **ID_Documento_Classe**              *referência                A classe de documento cuja guarda
                                       (Cad_Documento_Classe,     sustenta o tratamento.
                                       opcional)*                 

  **Prazo_Retencao_Meses**             *número, opcional*         ---

  **Exige_Relatorio_Impacto**          *booleano*                 ---

  **ID_Documento_Relatorio_Impacto**   *referência                ---
                                       (Cad_Documento, opcional)* 

  **ID_Participante_Responsavel**      *referência                Área ou pessoa dona do tratamento.
                                       (Cad_Participante,         
                                       opcional)*                 

  **Vigencia_Inicio**                  *data*                     Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                     *data*                     Último dia em que esta versão vale
                                                                  (inclusive). Sempre preenchida:
                                                                  31/12/9999 quando o fim é indefinido
                                                                  (versão vigente) --- convenção da Fase
                                                                  0, seção 2.

  **Motivo_Vigencia**                  *texto, opcional*          Por que esta versão foi criada.
  ------------------------------------ -------------------------- ----------------------------------------

Mov_Lgpd_Consentimento

Consentimento dado por um titular, fora ou dentro do recrutamento.
Generaliza Consentimento_Banco_Talentos e Data_Consentimento de
Cad_Pre_Cadastro, que passam a ser calculados a partir daqui.

*Vigência: não --- a revogação é a data preenchida na mesma linha.*

  --------------------------- ------------------------ ----------------------------------------
  **Campo**                   **Tipo lógico**          **Descrição / regra**

  **ID_Consentimento**        *identificador*          ---

  **ID_Tratamento**           *referência              ---
                              (Cad_Lgpd_Tratamento)*   

  **ID_Participante**         *referência              Titular já cadastrado.
                              (Cad_Participante,       
                              opcional)*               

  **ID_Pre_Cadastro**         *referência              Titular ainda em pré-cadastro
                              (Cad_Pre_Cadastro,       (candidato, lead). Uma das duas
                              opcional)*               referências é obrigatória.

  **Finalidade_Especifica**   *texto*                  ---

  **Data_Consentimento**      *data/hora*              ---

  **Meio_Coleta**             *enumeração {portal,     ---
                              formulario_web,          
                              aplicativo, email,       
                              papel}*                  

  **Versao_Texto**            *código (20)*            Versão do texto de consentimento
                                                       apresentada.

  **ID_Documento_Prova**      *referência              ---
                              (Cad_Documento,          
                              opcional)*               

  **Data_Revogacao**          *data/hora, opcional*    Revogar não apaga: a linha fica e o
                                                       tratamento cessa.

  **Situacao**                *enumeração {vigente,    ---
                              revogado, expirado}*     
  --------------------------- ------------------------ ----------------------------------------

Mov_Lgpd_Solicitacao_Titular

Pedido de um titular (art. 18) e o atendimento.

*Vigência: não.*

  ------------------------------- ---------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**              **Descrição / regra**

  **ID_Solicitacao**              *identificador*              ---

  **ID_Participante**             *referência                  Titular.
                                  (Cad_Participante)*          

  **ID_Direito_Titular**          *referência                  confirmacao_tratamento, acesso,
                                  (Cad_Classe_Sistema, domínio correcao,
                                  = direito_titular_lgpd)*     anonimizacao_bloqueio_eliminacao,
                                                               portabilidade, eliminacao_consentimento,
                                                               informacao_compartilhamento,
                                                               informacao_consequencia_nao_consentir,
                                                               revogacao_consentimento,
                                                               revisao_decisao_automatizada.

  **Canal_Recebimento**           *enumeração {portal, email,  ---
                                  telefone, presencial,        
                                  encarregado}*                

  **Data_Recebimento**            *data/hora*                  ---

  **Data_Limite_Resposta**        *data*                       Calculada e armazenada: recebimento mais
                                                               o prazo do parâmetro.

  **ID_Participante_Atendente**   *referência                  ---
                                  (Cad_Participante,           
                                  opcional)*                   

  **Data_Resposta**               *data/hora, opcional*        ---

  **Resultado**                   *enumeração {pendente,       Negativa por guarda obrigatória cita a
                                  atendida,                    retenção de Cad_Documento_Retencao.
                                  atendida_parcialmente,       
                                  negada_com_justificativa}*   

  **Justificativa**               *texto, opcional*            ---

  **ID_Documento_Resposta**       *referência (Cad_Documento,  ---
                                  opcional)*                   
  ------------------------------- ---------------------------- ----------------------------------------

Mov_Lgpd_Incidente

Incidente de segurança com dado pessoal e a comunicação à ANPD e aos
titulares (art. 48).

*Vigência: não.*

  ----------------------------------- ---------------------- ----------------------------------------
  **Campo**                           **Tipo lógico**        **Descrição / regra**

  **ID_Incidente**                    *identificador*        ---

  **ID_Empresa**                      *referência            ---
                                      (Cad_Empresa)*         

  **Data_Ocorrencia**                 *data/hora, opcional*  ---

  **Data_Ciencia**                    *data/hora*            Contagem do prazo de comunicação.

  **Descricao**                       *texto*                ---

  **Afeta_Dado_Sensivel**             *booleano*             ---

  **Quantidade_Titulares_Afetados**   *número, opcional*     ---

  **Risco_Relevante**                 *booleano*             Risco ou dano relevante aos titulares:
                                                             exige comunicação.

  **Data_Limite_Comunicacao**         *data*                 Calculada e armazenada: ciência mais o
                                                             prazo, em dias úteis.

  **Data_Comunicacao_Anpd**           *data/hora, opcional*  ---

  **Numero_Protocolo_Anpd**           *código (30),          ---
                                      opcional*              

  **Data_Comunicacao_Titulares**      *data/hora, opcional*  ---

  **Medidas_Adotadas**                *texto, opcional*      ---

  **ID_Participante_Encarregado**     *referência            ---
                                      (Cad_Participante,     
                                      opcional)*             

  **Situacao**                        *enumeração            ---
                                      {em_analise,           
                                      comunicado,            
                                      sem_risco_relevante,   
                                      encerrado}*            
  ----------------------------------- ---------------------- ----------------------------------------

Encarregado (art. 41; Resolução CD/ANPD 18/2024):
Cad_Empresa_Responsavel.Tipo_Papel ganha encarregado_dados. A identidade
e o contato do encarregado saem do participante. A eliminação atendida
ao titular respeita a guarda obrigatória: Cad_Documento_Retencao impede
o descarte antes do vencimento, e a solicitação registra a negativa
justificada. Cad_Pre_Cadastro.Dados_Basicos (campo composto) é
desmembrado na Fase 0, seção 7.

11\. Regras de Uso de Equipamentos da Empresa

Requisito de Alberto: além da LGPD, o sistema guarda as regras de uso
dos equipamentos da empresa (celulares, computadores, tablets e
semelhantes). Quatro coisas: o cadastro do equipamento, a política de
uso com as suas regras, o aceite de quem recebe e a ocorrência (perda,
furto, dano, uso indevido). As regras são dado estruturado, e não só um
documento anexado, para que o sistema consiga listar quem aceitou qual
versão, quais equipamentos estão sob qual regra e o que fazer quando o
colaborador sai. Regra que envolve monitoramento aponta para o
tratamento LGPD correspondente, porque a transparência sobre o
monitoramento é dever da empresa (LGPD art. 6º, VI).

Cad_Equipamento_Corporativo

Equipamento que a empresa fornece, ou que o colaborador traz e a
política cobre (BYOD). Vale para o que é ativo imobilizado e para o que
é despesa (o celular de baixo valor, por exemplo).

*Vigência: não --- o uso está em Mov_Equipamento_Atribuicao.*

  -------------------------------- -------------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**                  **Descrição / regra**

  **ID_Equipamento_Corporativo**   *identificador*                  ---

  **ID_Empresa**                   *referência (Cad_Empresa)*       ---

  **ID_Filial**                    *referência (Cad_Filial,         ---
                                   opcional)*                       

  **ID_Tipo_Equipamento**          *referência (Cad_Classe_Sistema, celular, notebook, desktop, tablet,
                                   domínio =                        monitor, impressora, chip_linha,
                                   tipo_equipamento_corporativo)*   token_ou_cartao_de_acesso, outro.

  **Marca**                        *texto, opcional*                ---

  **Modelo**                       *texto, opcional*                ---

  **Numero_Serie**                 *código (50), opcional*          ---

  **Imei**                         *código (17), opcional*          Celular e tablet com chip.

  **Numero_Linha**                 *código (15), opcional*          Linha telefônica do chip.

  **ID_Participante_Operadora**    *referência (Cad_Participante,   Operadora da linha.
                                   opcional)*                       

  **Patrimonio**                   *código (30), opcional*          Etiqueta patrimonial.

  **ID_Ativo**                     *referência                      Quando o equipamento é imobilizado.
                                   (Cad_Ativo_Imobilizado,          
                                   opcional)*                       

  **Propriedade**                  *enumeração {da_empresa, locado, do_colaborador: BYOD, coberto pelas
                                   do_colaborador}*                 regras da política.

  **Data_Aquisicao**               *data, opcional*                 ---

  **Situacao**                     *enumeração {em_estoque, em_uso, ---
                                   em_manutencao, extraviado,       
                                   baixado}*                        

  **Data_Baixa**                   *data, opcional*                 ---
  -------------------------------- -------------------------------- ----------------------------------------

Cad_Politica_Uso_Equipamento

A política de uso de equipamentos da empresa, com o texto integral no
GED.

*Vigência: sim --- cada revisão da política é uma versão. Nova versão
que muda regra exige novo aceite de quem já usa equipamento, e o sistema
abre a pendência.*

  ---------------------------- ------------------ ----------------------------------------
  **Campo**                    **Tipo lógico**    **Descrição / regra**

  **ID_Politica_Uso**          *identificador*    ---

  **ID_Politica_Uso_Versao**   *identificador da  Chave primária da versão (tabela física
                               versão*            Cad_Politica_Uso_Equipamento_Versao).
                                                  ID_Politica_Uso é a identidade, única e
                                                  referenciada pelas outras tabelas; cada
                                                  versão guarda a sua janela de vigência
                                                  --- Fase 0, seção 2.

  **ID_Empresa**               *referência        ---
                               (Cad_Empresa) ---  
                               identidade*        

  **Nome**                     *texto ---         ---
                               identidade*        

  **Aplica_A**                 *enumeração        ---
                               {colaborador,      
                               terceiro, ambos}*  

  **Versao_Texto**             *código (20)*      Versão do texto da política.

  **ID_Documento**             *referência        Texto integral.
                               (Cad_Documento)*   

  **Exige_Aceite**             *booleano*         Verdadeiro: sem aceite não há entrega de
                                                  equipamento.

  **Vigencia_Inicio**          *data*             Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*             Último dia em que esta versão vale
                                                  (inclusive). Sempre preenchida:
                                                  31/12/9999 quando o fim é indefinido
                                                  (versão vigente) --- convenção da Fase
                                                  0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*  Por que esta versão foi criada.
  ---------------------------- ------------------ ----------------------------------------

Cad_Politica_Uso_Equipamento_Regra

Uma regra da política, estruturada.

*Vigência: sim --- a regra muda com a política.*

  ------------------------- --------------------------------- ----------------------------------------
  **Campo**                 **Tipo lógico**                   **Descrição / regra**

  **ID_Regra_Uso**          *identificador*                   ---

  **ID_Politica_Uso**       *referência                       ---
                            (Cad_Politica_Uso_Equipamento)*   

  **ID_Tipo_Equipamento**   *referência (Cad_Classe_Sistema,  Vazio: vale para todos os tipos.
                            domínio =                         
                            tipo_equipamento_corporativo,     
                            opcional)*                        

  **ID_Tipo_Regra**         *referência (Cad_Classe_Sistema,  uso_pessoal, instalacao_de_software,
                            domínio =                         email_pessoal, redes_sociais,
                            tipo_regra_uso_equipamento)*      nuvem_pessoal,
                                                              uso_de_equipamento_do_colaborador,
                                                              monitoramento_de_uso, geolocalizacao,
                                                              bloqueio_remoto,
                                                              criptografia_obrigatoria, senha_minima,
                                                              bloqueio_de_tela_minutos, backup,
                                                              uso_fora_do_expediente, uso_no_exterior,
                                                              devolucao_no_desligamento,
                                                              responsabilidade_por_dano_ou_perda.

  **Permitido**             *booleano*                        Verdadeiro: a conduta é permitida;
                                                              falso: proibida ou não exigida, conforme
                                                              o tipo.

  **Valor_Parametro**       *número, opcional*                Para as regras com número (tamanho
                                                              mínimo da senha, minutos do bloqueio,
                                                              dias de devolução).

  **Descricao**             *texto, opcional*                 Explicação da regra em linguagem
                                                              simples.

  **ID_Tratamento**         *referência (Cad_Lgpd_Tratamento, Obrigatório nas regras de
                            opcional)*                        monitoramento_de_uso e geolocalizacao: é
                                                              o tratamento de dados pessoais que o
                                                              monitoramento faz.

  **Vigencia_Inicio**       *data*                            Primeiro dia em que esta versão vale.

  **Vigencia_Fim**          *data*                            Último dia em que esta versão vale
                                                              (inclusive). Sempre preenchida:
                                                              31/12/9999 quando o fim é indefinido
                                                              (versão vigente) --- convenção da Fase
                                                              0, seção 2.

  **Motivo_Vigencia**       *texto, opcional*                 Por que esta versão foi criada.
  ------------------------- --------------------------------- ----------------------------------------

Mov_Politica_Uso_Aceite

O aceite da política por um colaborador ou terceiro.

*Vigência: não --- registra o aceite.*

  --------------------------- --------------------------------- ----------------------------------------
  **Campo**                   **Tipo lógico**                   **Descrição / regra**

  **ID_Aceite**               *identificador*                   ---

  **ID_Politica_Uso**         *referência                       A versão aceita é a vigente na data do
                              (Cad_Politica_Uso_Equipamento)*   aceite.

  **ID_Participante**         *referência (Cad_Participante)*   ---

  **ID_Vinculo**              *referência (Cad_Vinculo_Emprego, ---
                              opcional)*                        

  **Data_Hora_Aceite**        *data/hora*                       ---

  **Meio_Aceite**             *enumeração                       ---
                              {assinatura_eletronica, portal,   
                              papel}*                           

  **ID_Documento_Assinado**   *referência (Cad_Documento,       ---
                              opcional)*                        
  --------------------------- --------------------------------- ----------------------------------------

Mov_Equipamento_Atribuicao

A quem o equipamento foi entregue, e a devolução.

*Vigência: não.*

  -------------------------------- -------------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**                  **Descrição / regra**

  **ID_Atribuicao**                *identificador*                  ---

  **ID_Equipamento_Corporativo**   *referência                      ---
                                   (Cad_Equipamento_Corporativo)*   

  **ID_Participante**              *referência (Cad_Participante)*  Colaborador ou terceiro responsável.

  **ID_Vinculo**                   *referência                      ---
                                   (Cad_Vinculo_Emprego, opcional)* 

  **ID_Aceite**                    *referência                      Obrigatório quando a política vigente
                                   (Mov_Politica_Uso_Aceite,        Exige_Aceite.
                                   opcional)*                       

  **Data_Entrega**                 *data*                           ---

  **Estado_Na_Entrega**            *enumeração {novo, bom,          ---
                                   com_avarias}*                    

  **ID_Documento_Termo**           *referência (Cad_Documento,      Termo de responsabilidade assinado.
                                   opcional)*                       

  **Data_Devolucao**               *data, opcional*                 ---

  **Estado_Na_Devolucao**          *enumeração {bom, com_avarias,   ---
                                   nao_devolvido}, opcional*        
  -------------------------------- -------------------------------- ----------------------------------------

Mov_Equipamento_Ocorrencia

Perda, furto, roubo, dano, uso indevido ou acesso indevido com um
equipamento.

*Vigência: não.*

  -------------------------------- -------------------------------- ----------------------------------------
  **Campo**                        **Tipo lógico**                  **Descrição / regra**

  **ID_Ocorrencia**                *identificador*                  ---

  **ID_Equipamento_Corporativo**   *referência                      ---
                                   (Cad_Equipamento_Corporativo)*   

  **ID_Atribuicao**                *referência                      ---
                                   (Mov_Equipamento_Atribuicao,     
                                   opcional)*                       

  **Tipo_Ocorrencia**              *enumeração {perda, furto,       ---
                                   roubo, dano, uso_indevido,       
                                   acesso_indevido}*                

  **Data_Hora_Ocorrencia**         *data/hora*                      ---

  **Descricao**                    *texto*                          ---

  **Data_Hora_Bloqueio_Remoto**    *data/hora, opcional*            ---

  **ID_Documento_Boletim**         *referência (Cad_Documento,      Boletim de ocorrência.
                                   opcional)*                       

  **ID_Incidente**                 *referência (Mov_Lgpd_Incidente, Perda ou acesso indevido de aparelho com
                                   opcional)*                       dado pessoal abre incidente LGPD, com o
                                                                    prazo de comunicação da Fase 8 ---
                                                                    Jurídico, seção 10.

  **Responsabilidade_Apurada**     *enumeração {empresa,            ---
                                   colaborador, terceiro,           
                                   indeterminada}, opcional*        

  **Situacao**                     *enumeração {aberta, apurada,    ---
                                   encerrada}*                      
  -------------------------------- -------------------------------- ----------------------------------------

Regras de integração: o vínculo com desligamento e equipamento sem
devolução gera pendência no fechamento da rescisão (aviso, sem bloquear
o pagamento); a ocorrência com dano e responsabilidade do colaborador
não gera desconto em folha automático: o desconto exige previsão
acordada em contrato ou no termo, ou dolo (CLT, art. 462, §1º), e o
jurídico confirma o caso; nova versão da política que altera regra abre
pendência de novo aceite para cada atribuição em aberto.

12\. Certificados Digitais

Toda transmissão fiscal, trabalhista e bancária depende de certificado
ICP-Brasil (e-CNPJ ou e-CPF, tipo A1 ou A3, Resolução CG 211/2024)
dentro do prazo, e várias dependem de procuração (a eletrônica do e-CAC
segue a IN RFB 1.751/2017). O dicionário guarda quem tem qual
certificado, para quê, até quando, e quem tem poder de quê. A chave
privada e a senha nunca entram no banco do ERP: ficam num cofre externo,
e o cadastro guarda só a referência.

Cad_Certificado_Digital

Certificado digital de uma empresa ou de uma pessoa física que a
representa.

*Vigência: não --- a validade é do próprio certificado; renovação é
certificado novo apontado pelo substituto.*

  ---------------------------------------- --------------------------- ----------------------------------------
  **Campo**                                **Tipo lógico**             **Descrição / regra**

  **ID_Certificado**                       *identificador*             ---

  **ID_Empresa**                           *referência (Cad_Empresa)*  ---

  **ID_Participante_Titular**              *referência                 Empresa (e-CNPJ) ou responsável (e-CPF).
                                           (Cad_Participante)*         

  **Modelo**                               *enumeração {A1, A3}*       ---

  **Numero_Serie**                         *código (40)*               ---

  **Autoridade_Certificadora**             *texto*                     ---

  **Data_Emissao**                         *data*                      ---

  **Data_Validade**                        *data*                      ---

  **Local_Guarda**                         *enumeração                 ---
                                           {arquivo_em_cofre, token,   
                                           cartao, hsm, nuvem}*        

  **Referencia_Cofre**                     *texto, opcional*           Onde a chave está guardada, sem a chave
                                                                       nem a senha.

  **Dias_Aviso_Vencimento**                *número*                    Antecedência do aviso de vencimento.

  **ID_Certificado_Substituto**            *referência                 ---
                                           (Cad_Certificado_Digital,   
                                           autorreferência, opcional)* 

  **ID_Participante_Responsavel_Guarda**   *referência                 ---
                                           (Cad_Participante,          
                                           opcional)*                  

  **Situacao**                             *enumeração {ativo,         ---
                                           vencido, revogado,          
                                           substituido}*               
  ---------------------------------------- --------------------------- ----------------------------------------

Cad_Certificado_Digital_Uso

Para que o certificado serve; o sistema escolhe o certificado vigente
pelo uso e pela empresa.

*Vigência: sim.*

  ------------------------ ---------------------------- ----------------------------------------
  **Campo**                **Tipo lógico**              **Descrição / regra**

  **ID_Certificado_Uso**   *identificador*              ---

  **ID_Certificado**       *referência                  ---
                           (Cad_Certificado_Digital)*   

  **ID_Uso_Certificado**   *referência                  nfe, nfse, sped, esocial, reinf,
                           (Cad_Classe_Sistema, domínio dctfweb, ecac, integracao_bancaria,
                           = uso_certificado_digital)*  assinatura_contrato, outro.

  **Vigencia_Inicio**      *data*                       Primeiro dia em que esta versão vale.

  **Vigencia_Fim**         *data*                       Último dia em que esta versão vale
                                                        (inclusive). Sempre preenchida:
                                                        31/12/9999 quando o fim é indefinido
                                                        (versão vigente) --- convenção da Fase
                                                        0, seção 2.

  **Motivo_Vigencia**      *texto, opcional*            Por que esta versão foi criada.
  ------------------------ ---------------------------- ----------------------------------------

13\. Procurações

Cad_Procuracao

Procuração que a empresa outorga ou recebe.

*Vigência: sim --- a vigência é o prazo da procuração.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Procuracao** | *identificador* | --- |
| **ID_Procuracao_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Procuracao_Versao). ID_Procuracao é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Empresa** | *referência (Cad_Empresa) --- identidade* | --- |
| **ID_Participante_Outorgante** | *referência (Cad_Participante) --- identidade* | --- |
| **ID_Participante_Outorgado** | *referência (Cad_Participante) --- identidade* | --- |
| **Forma** | *enumeração {instrumento_particular, escritura_publica, eletronica_ecac}* | --- |
| **Pode_Substabelecer** | *booleano* | --- |
| **Numero_Registro** | *código (40), opcional* | Cartório ou protocolo do e-CAC. |
| **ID_Documento** | *referência (Cad_Documento, opcional)* | --- |
| **Data_Revogacao** | *data, opcional* | Revogação encerra a vigência. |
| **Restringe_Processos** | *booleano* | Novo na revisão 3 (documento 37). Verdadeiro quando o outorgante restringiu o acesso do outorgado a processos específicos, listados em Cad_Procuracao_Processo; falso dá acesso a todos. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

*Revisão 3 --- campos novos (documento 37): Restringe_Processos.*

Cad_Procuracao_Poder

O que a procuração autoriza.

*Vigência: não --- muda com a procuração.*

  ---------------------------- ---------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**        **Descrição / regra**

  **ID_Procuracao_Poder**      *identificador*        ---

  **ID_Procuracao**            *referência            ---
                               (Cad_Procuracao)*      

  **ID_Poder**                 *referência            representar_perante_receita,
                               (Cad_Classe_Sistema,   transmitir_obrigacoes,
                               domínio =              assinar_contratos, representar_em_juizo,
                               poder_procuracao)*     receber_citacao,
                                                      movimentar_conta_bancaria,
                                                      substabelecer, outro.

  **Limite_Valor**             *número, opcional*     Teto de valor para o poder, quando há.

  **Descricao_Complementar**   *texto, opcional*      ---
  ---------------------------- ---------------------- ----------------------------------------

Vínculos: Cad_Empresa_Responsavel (tipo procurador) ganha ID_Procuracao
(opcional); Cad_Processo_Advogado aponta para a procuração do processo;
Mov_Esocial_Evento ganha ID_Certificado (opcional) para registrar qual
certificado assinou cada envio; os demais módulos de transmissão passam
a fazer o mesmo quando forem implementados. Os avisos de vencimento de
certificado e de procuração e de prazo processual e de prazo LGPD usam o
mecanismo de notificação da Fase 0, que ganha quatro tipos novos.

14\. Como este módulo se conecta com a Fase 0 e outros módulos

  ------------------------------------------- --------------------------------------- ----------------
  **Entidade referenciada**                   **Como este módulo usa**                **Observação**

  **Cad_Participante /                        Partes, advogados, peritos, assistentes *Fase 0*
  Cad_Participante_Classe**                   técnicos, sócios, beneficiários finais, 
                                              titulares de dados, outorgantes e       
                                              outorgados são participantes do         
                                              cadastro único; nenhuma pessoa é        
                                              duplicada neste módulo.                 

  **Cad_Empresa / Cad_Empresa_Socio /         Os atos societários, o capital social e *Fase 0, revisão
  Cad_Empresa_Responsavel**                   a distribuição de lucros são da         45*
                                              empresa; Cad_Empresa_Socio e            
                                              Cad_Empresa_Responsavel continuam na    
                                              Fase 0 e ganharam ID_Ato_Societario (e  
                                              o responsável, ID_Procuracao e o papel  
                                              encarregado_dados).                     

  **Cad_Documento / Cad_Documento_Vinculo /   Peças, laudos, atas, procurações e      *Fase 0, revisão
  Cad_Documento_Classe /                      provas de consentimento são documentos  45*
  Cad_Documento_Retencao (GED)**              do GED. A guarda fica suspensa enquanto 
                                              o processo estiver em andamento         
                                              (Cad_Documento_Retencao.ID_Processo), e 
                                              o marco inicial do prazo vem de         
                                              Cad_Documento_Classe.                   

  **Cad_Classe_Sistema**                      Todas as listas de códigos deste módulo *Fase 0, revisão
                                              (área do processo, papel processual,    45*
                                              tipo de perícia, base legal, direito do 
                                              titular, tipo de equipamento, poder de  
                                              procuração e outras) são domínios.      

  **Mov_Aprovacao_Instancia /                 Validação dos parâmetros provisórios    *Fase 0, seção
  Cad_Regua_Aprovacao**                       (validacao_dado_legal), mudança de      9*
                                              prognóstico acima do limite             
                                              (prognostico_processo) e decisão de     
                                              risco fiscal (decisao_risco_fiscal)     
                                              passam pela mesma régua.                

  **Mov_Lote_Lancamento / Mov_Lancamento**    Provisão de contingência, depósito      *Fase 0, revisão
                                              judicial, distribuição de lucros e JCP  45 (novos
                                              geram lançamento contábil pelo Motor de Origem_Tipo)*
                                              Regras; o Jurídico não conhece plano de 
                                              contas.                                 

  **Cad_Periodo_Fechamento /                  Trava prognóstico, movimento de         *Fase 0, seção
  Cad_Bloco_Fechamento (bloco juridico)**     depósito e deliberação de distribuição  10*
                                              em competência fechada.                 

  **Cad_Dado_Sensivel /                       Laudos médicos, dados de deficiência e  *Fase 0, seção
  Mov_Acesso_Dado_Sensivel /                  dados pessoais do titular são tratados  13*
  Cad_Usuario_Escopo**                        como sensíveis; o escopo do usuário     
                                              restringe o acesso ao contencioso por   
                                              tipo de processo.                       

  **Mov_Titulo / Mov_Titulo_Baixa**           Condenação, acordo, custas, honorários, *Contas a
                                              depósitos, pagamento trabalhista e      Pagar/Receber,
                                              distribuição de lucros viram título a   revisão 12*
                                              pagar (Origem_Tipo processo_judicial,   
                                              processo_trabalhista e                  
                                              distribuicao_lucro).                    

  **Mov_Titulo_Retencao /                     A suspensão de exigibilidade (seção 5)  *Contabilidade &
  Mov_Apuracao_Irpj_Csll /                    alcança a retenção e a apuração de IRPJ Fiscal, revisão
  Mov_Apuracao_Decisao_Risco**                e CSLL; a retenção sobre lucros         17*
                                              distribuídos é uma Mov_Titulo_Retencao. 

  **Mov_Rh_Processo_Trabalhista /             O processo trabalhista (S-2500 e        *Folha & RH,
  Cad_Rh_Estabelecimento_Esocial /            S-2501) desdobra Cad_Processo por       revisão 16*
  Cad_Rh_Lotacao_Tributaria /                 trabalhador (um processo tem vários     
  Mov_Esocial_Evento**                        trabalhadores); a suspensão do RAT e da 
                                              lotação usa Mov_Processo_Suspensao; o   
                                              envio dos eventos registra o            
                                              certificado.                            

  **Cad_Gestao_Contrato**                     Garantias, penalidades, forma de        *Gestão de
                                              assinatura e foro do contrato ficam em  Contratos,
                                              Gestão de Contratos; o contrato pode    revisão 7*
                                              estar em litígio (Cad_Processo).        

  **Cad_Participante_Email_Tipo_Notificacao / Quatro tipos novos de aviso: vencimento *Fase 0, revisão
  tipo_notificacao_sistema**                  de certificado, vencimento de           45*
                                              procuração, prazo processual e prazo    
                                              LGPD.                                   
  ------------------------------------------- --------------------------------------- ----------------

15\. Notas para a sua revisão

-   Cad_Processo é um cadastro mestre com identidade e versão (D-1): a
    identidade é ID_Empresa, Formato_Numero e Numero_Processo (código de
    30 posições, para caber o padrão CNJ de 20 dígitos e os números
    administrativos). A movimentação do processo entre varas e
    instâncias não altera a identidade: fica em Mov_Processo_Juizo, e
    cada evento do eSocial aponta para o juízo em que a decisão foi
    proferida.

-   A provisão nasce da decisão da empresa (Tratamento_Contabil), e não
    do prognóstico isolado: o sistema sugere pelo CPC 25 (provável:
    provisão; possível: divulgação; remoto: nada) e registra o que a
    empresa decidiu, com justificativa quando diverge da sugestão.

-   A LC 224/2025 (acréscimo do IRPJ e da CSLL): o sistema sempre
    calcula com a majoração; a empresa decide, com aprovação, se recolhe
    ou assume o risco, se deposita em juízo e se lança provisão. O
    resultado das ADIs 7936 e 7982 e a divergência entre os tribunais
    regionais NÃO foram confirmados; a estrutura não depende do
    resultado.

-   Distribuição de lucros e JCP: a base da retenção (total pago no mês
    ou só o excedente), o critério de acúmulo por fonte pagadora, a
    alíquota do JCP, o código do DARF e o ano limite do pagamento da
    transição são parâmetros PROVISÓRIOS, sujeitos à validação de RH e
    contador; o texto da Lei 15.270/2025 foi lido por resumo, e a
    leitura de que a retenção incide sobre o total pago no mês precisa
    de confirmação.

-   Indicativos de suspensão: o desenho usa um só domínio
    (codigo_suspensao_esocial) para o eSocial e a Reinf. Não foi
    confirmado que as duas listas são idênticas; se divergirem, o
    domínio é separado.

-   Perícia: o rito segue os arts. 464 a 480 do CPC; a fase atual é
    sempre a última do histórico de fases; o laudo entregue gera o aviso
    de reavaliação do prognóstico. O laudo médico ou de insalubridade é
    dado sensível.

-   Equipamentos: dano com responsabilidade do colaborador não gera
    desconto automático em folha; o desconto exige previsão acordada ou
    dolo (CLT, art. 462, §1º) e confirmação do jurídico. Regra de
    monitoramento aponta para o tratamento LGPD correspondente.

-   Prazos de guarda sugeridos para carga inicial (documento fiscal e
    contábil, prontuário ocupacional, contrato, peças de processo) são
    propostas a confirmar pelo jurídico; só o prazo do CTN e o da NR-7
    vêm de norma citada.

-   Certificados e procurações: a chave privada e a senha nunca entram
    no banco do ERP; o cadastro guarda só a referência ao cofre.

-   Leiautes S-2500 e S-2501 (Folha & RH): conferidos na consolidação
    contra o XSD oficial do S-1.3.00, e o grupo foi refeito a partir
    deles (ver Folha & RH, seção 10). Continua por conferir a quantidade
    de códigos de cada tabela oficial do eSocial.

-   Revisão 1 (primeira entrega): 35 entidades neste documento. O Bloco
    3 completo acrescenta 58 entidades novas ao dicionário, distribuídas
    entre este documento e os demais módulos (ver o desenho e o
    histórico do bloco nos documentos 20 e 22 do Projeto).

16\. Próximo Passo

*Revisão 1 --- primeira entrega do módulo Jurídico, consolidada junto
com o Bloco 3 (Fase 0 revisão 45). Próximos passos combinados com
Alberto: conferir os pontos marcados como não confirmados nas Notas
(parâmetros de distribuição de lucros e de LGPD, prazos de guarda,
quantidade de códigos das tabelas do eSocial) e definir com o jurídico
da Mlegate a carga inicial das tabelas oficiais do CNJ. Depois deste
bloco, o dicionário passa para a fase de revisão de qualidade final
(auditoria de consistência entre os módulos).*

*Revisão 2 --- Bloco 4 consolidado junto com a Fase 0 (revisão 46),
Contabilidade & Fiscal (revisão 18) e Folha & RH (revisão 17).*



17\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este anexo reúne 2 entidades novas de Jurídico, vindas dos documentos de desenho 33 a 46, que Alberto aprovou e mandou consolidar em 12/10/2026. As alterações em entidades que já existiam aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3"). As regras legais citadas (alíquotas, prazos, versões de leiaute, códigos oficiais) são parâmetros com vigência, nunca valores fixos no código.

17.1. Manuais oficiais: EFD-ICMS/IPI, PGDAS-D, DOI, CNO, LCDPR, DEAP e Mafon (documento 37)

Mov_Processo_Juntada

Solicitação de juntada de documento a um processo digital do e-CAC (e-Processo): consulta, rascunho e conclusão, ligada à ciência respondida e ao documento no GED. Resposta a intimação por juntada.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Processo_Juntada** | *identificador* | --- |
| **ID_Processo** | *referência (Cad_Processo)* | Processo digital que recebe o documento. |
| **ID_Andamento_Ciencia** | *referência (Mov_Processo_Andamento, opcional)* | Ciência ou intimação respondida pela juntada. |
| **Numero_Solicitacao** | *código (até 20), opcional* | Número da solicitação de juntada, devolvido na conclusão. |
| **Descricao** | *texto* | Descrição do documento juntado. |
| **Situacao** | *enumeração {rascunho, concluida}* | Etapa da solicitação. |
| **Data_Hora_Solicitacao** | *data/hora* | Quando o rascunho foi aberto. |
| **Data_Hora_Conclusao** | *data/hora, opcional* | Quando a solicitação foi concluída. |
| **ID_Documento** | *referência (Cad_Documento, opcional)* | Documento juntado, guardado no GED. |

Cad_Procuracao_Processo

Restrição de procuração por processo: o outorgante limita o acesso do outorgado a processos digitais específicos; sem restrição o outorgado vê todos, e processo novo precisa ser incluído.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Procuracao_Processo** | *identificador* | --- |
| **ID_Procuracao** | *referência (Cad_Procuracao)* | Procuração restrita. |
| **ID_Processo** | *referência (Cad_Processo)* | Processo a que o outorgado tem acesso. |
| **Data_Inclusao** | *data* | Quando o processo entrou na restrição. |
| **Observacao** | *texto, opcional* | Observação. |



18\. Anexo --- Entidades e domínios da revisão 4 (documento 51)

Revisão 4 do dicionário: este anexo reúne 3 entidades novas, vindas das decisões D-N118 a D-N124 do documento 51 (LC 224/2025, Mafon 2024 e 2025), que Alberto aprovou e mandou consolidar em 12/10/2026. As alterações em entidades que já existiam aparecem nas próprias tabelas (campos marcados "Novo na revisão 4"). As regras legais citadas (alíquotas, limites, prazos, listas oficiais) são parâmetros com vigência, nunca valores fixos no código; a carga inicial é provisória até o texto oficial.

18.1. Cálculo do limite dos juros sobre capital próprio (documento 51, D-N123)

Cad_Conta_Contabil_Papel_Jcp

Diz que contas do patrimônio líquido compõem a base de cálculo do limite dos juros sobre capital próprio (documento 51, D-N123; Mafon 2025, código 5706, nota 4, p. 58): capital social integralizado, reservas de capital dos arts. 13, § 2º, e 14, parágrafo único, da Lei 6.404, reservas de lucros (exceto a de incentivo fiscal do art. 195-A), ações em tesouraria, e lucros ou prejuízos acumulados.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Conta_Papel_Jcp** | *identificador* | --- |
| **ID_Conta_Papel_Jcp_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Conta_Contabil_Papel_Jcp_Versao). ID_Conta_Papel_Jcp é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| **ID_Conta** | *referência (Cad_Conta_Contabil) --- identidade* | Conta analítica de natureza patrimônio líquido. |
| **Categoria_Base_Jcp** | *enumeração {capital_social_integralizado, reserva_capital_art_13_14, reserva_lucros, acoes_tesouraria, lucros_prejuizos_acumulados, fora_da_base}* | fora_da_base marca a reserva de incentivo fiscal e qualquer conta que a lei exclui. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) --- convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

Mov_Jcp_Calculo

Cálculo do limite dos juros sobre capital próprio de uma empresa em um período (documento 51, D-N123): base do patrimônio líquido, limite pela TJLP e a condição de lucros de duas vezes os juros (Mafon 2025, códigos 5706 e 9453). Os JCP deliberados do período (Mov_Distribuicao_Lucro do tipo jcp) apontam para este cálculo.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Jcp_Calculo** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | A pessoa jurídica. |
| **Data_Inicio_Periodo** | *data* | Início do período a que o limite se refere. |
| **Data_Fim_Periodo** | *data* | Fim do período a que o limite se refere. |
| **Data_Saldo_Base** | *data* | A data dos saldos das contas. O Mafon não diz se é o início ou o fim do período; confirmar na IN RFB 1.700, art. 75. |
| **Base_Patrimonio_Liquido** | *número* | Soma dos saldos das contas de Cad_Conta_Contabil_Papel_Jcp (credor positivo; ações em tesouraria e prejuízos reduzem). |
| **Limite_Pela_Tjlp** | *número* | Soma dos limites parciais de Mov_Jcp_Calculo_Tjlp. |
| **Lucro_Antes_Jcp** | *número* | Lucros do período antes da dedução dos juros. |
| **Lucros_Acumulados_E_Reservas** | *número* | Lucros acumulados e reservas de lucros. |
| **Valor_Deliberado_Periodo** | *número* | Soma dos JCP deliberados no período (Mov_Distribuicao_Lucro do tipo jcp). |
| **Condicao_Dobro_Atendida** | *booleano* | Verdadeiro quando Lucro_Antes_Jcp ou Lucros_Acumulados_E_Reservas é igual ou maior que duas vezes o valor deliberado. Quando falso, a deliberação do JCP emite alerta com justificativa, e não bloqueio. |
| **Excedente_Ao_Limite** | *número* | O que o valor deliberado passa de Limite_Pela_Tjlp. |
| **Situacao** | *enumeração {calculado, confirmado}* | Confirmado depois da revisão do contador. |

Mov_Jcp_Calculo_Tjlp

Faixas de TJLP dentro do período do cálculo, para o "pro rata dia" do limite dos juros sobre capital próprio (documento 51, D-N123). A série TJLP vive em Cad_Serie_Cotacao (tipo indice_financeiro, fonte banco_central) e os valores trimestrais em Mov_Serie_Cotacao_Valor; os valores não estão no Projeto.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Jcp_Calculo_Tjlp** | *identificador* | --- |
| **ID_Jcp_Calculo** | *referência (Mov_Jcp_Calculo)* | O cálculo. |
| **ID_Valor_Tjlp** | *referência (Mov_Serie_Cotacao_Valor)* | O valor da TJLP usado na faixa. |
| **Data_Inicio** | *data* | Início da faixa em que a taxa valeu. |
| **Data_Fim** | *data* | Fim da faixa em que a taxa valeu. |
| **Dias** | *número* | Dias da faixa. |
| **Dias_Base_Ano** | *número* | O divisor do ano. O Mafon não diz se é 360 ou 365; confirmar na IN RFB 1.700. |
| **Limite_Parcial** | *número* | Base vezes a taxa anual vezes Dias dividido por Dias_Base_Ano. |
