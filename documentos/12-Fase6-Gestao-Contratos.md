**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 6 · MÓDULO 11**

**Gestão de Contratos**

*Contrato com cliente e com fornecedor no mesmo cadastro, reajuste por
índice, três modelos de valor (fixo, fixo mais variável por fórmula,
quantidade garantida apurada após o período), aditivos com dupla
aprovação e apuração periódica gerando título a pagar/receber*

*Revisão 8 --- consolidação da revisão 31 do dicionário (documentos 150, 157, 170 e 173, com as respostas de Alberto de 04/11/2026): 1 entidades existentes alteradas; Data_Exigibilidade em Mov_Gestao_Contrato_Apuracao, para o fato gerador da execução continuada (documento 157, Q157-1).*

*Revisão 7 --- Bloco 3 da validação geral do dicionário (folha e
eSocial, jurídico), construída junto com a revisão 45 da Fase 0 e com o
novo módulo Fase 8 --- Jurídico: Cad_Gestao_Contrato ganha forma e data
de assinatura, testemunhas, renovação automática, prazo de aviso de
denúncia, foro e cláusula arbitral; novas Cad_Gestao_Contrato_Garantia e
Cad_Gestao_Contrato_Penalidade.*

*Revisão 6 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; Cad_Gestao_Contrato_Item marcado com vigência (já
era versionado por nova linha) e datas padronizadas para
Vigencia_Inicio/Vigencia_Fim.*

*Revisão 5 --- corrigido o desenho do período de fechamento deste
módulo, que foi na verdade o próprio gatilho de todo o novo mecanismo
transversal da Fase 0 (seção 10, revisão 37): ID_Periodo_Referencia
(Mov_Gestao_Contrato_Apuracao, seção 4.1) deixa de referenciar
Cad_Periodo_Contabil --- extensão registrada como não confirmada na
revisão anterior (seção 7), e que se mostrou equivocada --- e passa a
referenciar Cad_Periodo_Fechamento com ID_Bloco=\"gestao_contratos\",
período próprio e independente do contábil, pedido explicitamente por
Alberto (\"o período de fechamento dos contratos tem que ser
independente do contábil, pois precisa ser fechados todos os contratos
para a contabilização sem interferência de eventual alteração no
contrato\"); o mesmo gate é estendido a Mov_Gestao_Contrato_Consumo
(seção 4.2, Data_Consumo) e a Mov_Gestao_Contrato_Medicao (seção 4.3,
Data_Medicao) --- nenhum consumo ou medição aceito com data dentro de
uma competência fechada do bloco gestao_contratos, para a filial do
contrato; sem validação de pendência associada a este fechamento,
confirmado por Alberto --- contrato vigente atravessa meses, mesma
lógica já usada em Produção*

*Revisão 4 --- três pontos fechados com Alberto: unificação da medição
de obra/construção civil (antes duplicada em Cad_Obra/Mov_Obra_Medicao,
Fase 0) numa medição só, transversal às duas posições --- nova seção
4.3, Mov_Gestao_Contrato_Medicao/\_Item, com vínculo opcional a
entregável (parcela mensal liberada só após aceite); novo mecanismo de
consumo por evento (seção 4.2, Mov_Gestao_Contrato_Consumo) para
contratos calculados na hora de cada uso --- ex. frete por km/entrega,
construído junto com o patch em Expedição (revisão 5) --- acumulando até
fechar contra a nota fiscal do fornecedor, quantidade e valor sempre em
campos separados; ID_Filial deixa de ser exclusivo da posição
Contratante*

*Revisão 3 --- módulo original cobria bem só a posição Contratado
(Mlegate prestando serviço); esta revisão fecha a posição Contratante
(Mlegate contratando/adquirindo), levantada por Alberto: papel derivado
da classe do participante (nunca campo próprio); régua de aprovação
própria do contrato --- não só do aditivo ---, com
Origem_Tipo=contrato_aquisicao ou contrato_venda conforme a posição,
reaproveitado também pelo aditivo; ID_Filial e Forma_Compromisso
migrados de Compras (Cad_Contrato_Fornecimento, agora aposentado naquele
documento); pagamento na posição Contratante sempre amarrado a medição
(Percentual_Avanco_Fisico) e/ou nota fiscal de entrada
(ID_Nota_Fiscal_Entrada), tanto na apuração periódica quanto no novo
Mov_Gestao_Contrato_Entregavel --- entregável por etapa de um fornecedor
(ex.: construção de um galpão: terraplenagem, fundação, estrutura,
instalações), espelhado mas distinto de Mov_Ordem_Producao_Entregavel
(Produção, exclusivo da posição Contratado); Status do contrato
harmonizado com o enum que existia em Compras*

*Revisão 2 --- três pontos pedidos por Alberto: preço por item do
contrato (novo Cad_Gestao_Contrato_Item, opcional --- cada item com seu
próprio modelo de valor, podendo divergir entre itens do mesmo contrato;
cabeçalho do contrato continua servindo para o caso de valor global, sem
item nenhum); apuração periódica passa a poder ocorrer por item; e
faturamento por entregável (Modelo_Faturamento, nova seção Faturamento
por Entregável com Mov_Gestao_Contrato_Faturamento_Entregavel, disparado
quando um entregável de projeto --- Mov_Ordem_Producao_Entregavel,
Produção --- é concluído), construído junto com o patch em Produção
(revisão 9) que introduz o próprio conceito de entregável, adiado desde
a fusão de Gestão de Projetos*

*Revisão 1 --- primeira entrega do módulo Fase 6 Gestão de Contratos:
cadastro único de contrato (cliente ou fornecedor) com três modelos de
valor (fixo, fixo mais variável por fórmula livre, quantidade garantida
apurada após o período com cobrança da diferença ou do mínimo), reajuste
por índice (Cad_Serie_Cotacao, Fase 0), aditivos com dupla aprovação
(régua interna + aceite da contraparte) e apuração periódica gerando
título a pagar/receber; Gestão de Projetos (PPM) permanece fundida em
Produção, fora deste documento*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o módulo de Gestão de Contratos, no mesmo
formato usado nos módulos já entregues: função e dados juntos, entidade
por entidade, sempre referenciando os motores transversais da Fase 0
(Cad_Participante, Cad_Empresa, Cad_Serie_Cotacao,
Cad_Regua_Aprovacao/Mov_Aprovacao_Instancia, Cad_Documento_Vinculo/GED)
em vez de redefini-los. Cobre contrato com cliente E com fornecedor no
MESMO cadastro --- mesmo princípio de cadastro único já usado para
Cad_Participante em todo o dicionário (Fase 0): não há uma tabela de
\"contrato de cliente\" e outra de \"contrato de fornecedor\", o papel
vem da classe já existente do participante envolvido, nunca de um campo
próprio de papel nesta entidade.

Escopo desta revisão: cadastro de contrato com três modelos de valor
(fixo; fixo mais variável apurado por fórmula livre; quantidade
garantida apurada após o período, com cobrança da diferença quando o uso
real ultrapassa o mínimo ou do próprio mínimo quando fica abaixo),
reajuste por índice cadastrável, aditivos contratuais com dupla
aprovação (régua interna da Mlegate e aceite da contraparte, tratados
como dois mecanismos distintos) e apuração periódica gerando o título a
pagar ou a receber correspondente.

*Nota explícita de escopo, decisão definitiva já tomada por Alberto e
não uma pendência deste documento: \"Gestão de Projetos\" (PPM), que
originalmente seria a segunda metade deste módulo no Documento
Analítico, foi FUNDIDA por Alberto dentro do módulo de Produção (Fase 1)
numa revisão anterior daquele documento --- não faz parte deste
documento, e não é referenciada aqui como gancho de extensão futura.*

Contrato por hora corrida (ex.: serviço prestado por hora trabalhada)
reaproveita o mesmo apontamento de horas já usado por Produção ---
Mov_Apontamento_Tempo (Fase 1, seção 4) --- em vez de um apontamento
próprio deste módulo: honra o princípio \"uma única entidade de dado,
nunca estruturas paralelas\" já documentado no Documento Analítico deste
projeto. Um apontamento de horas passa a poder apontar diretamente para
um contrato (Mov_Apontamento_Tempo.ID_Contrato, construído em paralelo
com este documento), e este documento consome esse vínculo tanto na
fórmula de cálculo do contrato (seção 2) quanto na apuração periódica
(seção 4), sem duplicar o registro do tempo trabalhado.

2\. Cadastro de Contrato

O cadastro único de contrato --- de cliente ou de fornecedor,
indistintamente, o mesmo princípio de \"uma classe não exige uma tabela
separada\" já usado em Cad_Participante_Classe (Fase 0) aplicado aqui a
um cadastro que o consome, não que o redefine.

Cad_Gestao_Contrato

O contrato em si --- com cliente ou com fornecedor, no mesmo cadastro.
Mudanças ao longo da vida do contrato (prazo, valor, fórmula) nunca
sobrescrevem estes campos diretamente: são registradas como um
Cad_Gestao_Contrato_Aditivo (seção 3), histórico append-only; o valor
vigente em cada momento é sempre a combinação deste cadastro com o
aditivo mais recente aplicável até a data de referência.

*Vigência: não --- mudanças no contrato ao longo do tempo são
registradas por Cad_Gestao_Contrato_Aditivo (seção 3), nunca editando
estes campos diretamente.*

  ------------------------------- ------------------------------------ -----------------------------------------------------
  **Campo**                       **Tipo lógico**                      **Descrição / regra**

  **ID_Contrato**                 *identificador*                      ---

  **ID_Empresa**                  *referência (Cad_Empresa, Fase 0)*   A empresa do grupo Mlegate parte do contrato.

  **ID_Participante**             *referência (Cad_Participante, Fase  O cliente OU o fornecedor do contrato --- mesmo
                                  0)*                                  cadastro único de participante usado em todo o
                                                                       dicionário. O papel (cliente ou fornecedor) é dado
                                                                       pela classe já existente do participante
                                                                       (Cad_Participante_Classe.Classe=cliente/fornecedor,
                                                                       Fase 0), nunca por um campo de papel próprio nesta
                                                                       entidade.

  **Objeto**                      *texto*                              Descrição do objeto contratual --- texto livre.

  **Data_Inicio**                 *data*                               ---

  **Data_Fim**                    *data*                               A vigência original contratada --- pode ser estendida
                                                                       por aditivo (Novo_Data_Fim, seção 3), sem editar este
                                                                       campo.

  **Modelo_Valor**                *enumeração {fixo,                   Estrutural: decide quais dos campos de valor abaixo
                                  fixo_mais_variavel,                  se aplicam. fixo: valor fechado por período.
                                  quantidade_garantida}*               fixo_mais_variavel: uma parte fixa mais uma parte
                                                                       calculada por fórmula livre. quantidade_garantida:
                                                                       cobrança apurada depois do período, sobre o maior
                                                                       valor entre o uso real e um mínimo garantido.

  **Valor_Fixo**                  *número, opcional*                   Preenchido quando Modelo_Valor=fixo ou
                                                                       fixo_mais_variavel --- o valor fixo cobrado a cada
                                                                       período.

  **Formula_Variavel**            *texto livre, opcional*              Preenchido quando Modelo_Valor=fixo_mais_variavel ---
                                                                       reaproveita o MESMO motor de fórmula livre já usado
                                                                       em Cad_Rh_Verba.Formula (Fase 5 --- Folha & RH, seção
                                                                       5), em vez de um motor de cálculo próprio deste
                                                                       módulo. Para contrato por hora corrida, a fórmula
                                                                       referencia Mov_Apontamento_Tempo.Horas_Efetivas
                                                                       (Produção, Fase 1, seção 4), somando os apontamentos
                                                                       cujo ID_Contrato aponta para este contrato no período
                                                                       apurado.

  **Quantidade_Garantida**        *número, opcional*                   Preenchida junto com Valor_Unitario quando
                                                                       Modelo_Valor=quantidade_garantida --- o mínimo de
                                                                       quantidade garantido por período, cobrado mesmo que o
                                                                       uso real fique abaixo dele.

  **Valor_Unitario**              *número, opcional*                   Preenchido junto com Quantidade_Garantida quando
                                                                       Modelo_Valor=quantidade_garantida --- o valor
                                                                       unitário aplicado tanto ao mínimo garantido quanto à
                                                                       diferença apurada acima dele.

  **ID_Serie_Cotacao_Reajuste**   *referência (Cad_Serie_Cotacao, Fase O índice financeiro de reajuste do contrato, sempre
                                  0 seção 15, opcional)*               com Cad_Serie_Cotacao.Tipo=indice_financeiro ---
                                                                       reaproveita a série de índices/cotações da Fase 0 em
                                                                       vez de um cadastro de índice próprio deste módulo.
                                                                       Vazio para contrato sem cláusula de reajuste.

  **Periodicidade_Reajuste**      *enumeração {mensal, anual},         Preenchida junto com ID_Serie_Cotacao_Reajuste --- a
                                  opcional*                            periodicidade em que o reajuste pelo índice é
                                                                       aplicado. Enumeração fechada dentro da própria
                                                                       entidade, não domínio aberto: conjunto pequeno e
                                                                       estável, mesmo critério já usado para outras
                                                                       enumerações estruturais deste dicionário (ex.:
                                                                       Periodicidade_Taxa, Contas a Pagar/Receber).

  **Status**                      *enumeração {rascunho, em_aprovacao, Estrutural --- armazenado, e não puramente derivado
                                  vigente, suspenso, encerrado,        de Data_Fim, porque um contrato pode ser encerrado ou
                                  cancelado}*                          cancelado antes do prazo (rescisão, distrato), o que
                                                                       Data_Fim sozinha não capturaria. Harmonizado nesta
                                                                       Revisão 3 com o enum que existia em Compras
                                                                       (Cad_Contrato_Fornecimento, agora aposentado):
                                                                       \"em_aprovacao\" enquanto a instância de
                                                                       ID_Instancia_Aprovacao (abaixo) está pendente;
                                                                       \"suspenso\" cobre paralisação temporária do contrato
                                                                       sem encerrá-lo.

  **Modelo_Faturamento**          *enumeração {periodico,              NOVO na Revisão 2 --- periodico (padrão) usa a
                                  por_entregavel}*                     apuração periódica já existente
                                                                       (Mov_Gestao_Contrato_Apuracao, seção 4.1);
                                                                       por_entregavel usa a nova entidade
                                                                       Mov_Gestao_Contrato_Faturamento_Entregavel (seção
                                                                       5.1), disparada quando um entregável do projeto
                                                                       (Mov_Ordem_Producao_Entregavel, Produção, Fase 1) é
                                                                       concluído --- confirmado por Alberto: \"sim tem
                                                                       contratos que são faturamento periódico e outros por
                                                                       entregáveis\".

  **ID_Filial**                   *referência (Cad_Filial, Fase 0),    NOVO na Revisão 3 --- migrado do módulo Compras
                                  opcional*                            (Cad_Contrato_Fornecimento, agora aposentado, revisão
                                                                       12 daquele documento). Generalizado na Revisão 4: a
                                                                       filial responsável/executora do contrato --- vale nas
                                                                       duas posições (Contratante: filial que faz a
                                                                       aquisição; Contratado: filial que executa o serviço
                                                                       prestado, ex. uma obra de construção civil, ver
                                                                       Cad_Obra, Fase 0).

  **Forma_Compromisso**           *enumeração {integral, mensal},      NOVO na Revisão 3 --- idem, migrado de Compras --- só
                                  opcional*                            relevante na posição Contratante. \"integral\" gera
                                                                       um único compromisso orçamentário
                                                                       (Mov_Compromisso_Orcamentario, Planejamento &
                                                                       Orçamento) pelo valor total do período vigente do
                                                                       contrato; \"mensal\" gera um compromisso por mês,
                                                                       conforme ele ocorre. Confirmado por Alberto: \"no
                                                                       caso de venda não tem compromisso orçamentario só na
                                                                       aquisição\" --- na posição Contratado este campo fica
                                                                       vazio e nenhum compromisso é gerado.

  **ID_Instancia_Aprovacao**      *referência                          NOVO na Revisão 3 --- a aprovação do CONTRATO EM SI
                                  (Mov_Aprovacao_Instancia, Fase 0     (não só do aditivo, que já tinha a sua própria desde
                                  seção 9), opcional*                  a Revisão 1, seção 3): Origem_Tipo=contrato_aquisicao
                                                                       quando o contrato está na posição Contratante (alçada
                                                                       por valor comprometido/orçamento, herdando o espírito
                                                                       da régua que já aprova pedido de compra em Compras)
                                                                       ou Origem_Tipo=contrato_venda quando Contratado
                                                                       (alçada por desconto/condição comercial em relação à
                                                                       tabela, herdando o espírito da régua que já aprova
                                                                       cotação de venda em CRM & Vendas,
                                                                       Origem_Tipo=cotacao_venda). O papel
                                                                       (Contratante/Contratado) é sempre derivado da classe
                                                                       do participante (acima), nunca um campo de papel
                                                                       próprio nesta entidade.

  **Forma_Assinatura**            *enumeração {manuscrita,             Lei 14.063/2020. Decide se o contrato é título
                                  eletronica_simples,                  executivo sem testemunhas (Código de Processo Civil,
                                  eletronica_avancada,                 art. 784, III e §4º).
                                  eletronica_qualificada_icp_brasil,   
                                  nao_assinado}*                       

  **Data_Assinatura**             *data, opcional*                     Adicionado na revisão 7 (Bloco 3).

  **Quantidade_Testemunhas**      *número, opcional*                   Dispensadas quando a assinatura é eletrônica
                                                                       verificada.

  **Renovacao_Automatica**        *booleano*                           Adicionado na revisão 7 (Bloco 3).

  **Prazo_Aviso_Denuncia_Dias**   *número, opcional*                   Antecedência com que uma das partes avisa que não
                                                                       renova ou denuncia o contrato.

  **ID_Municipio_Foro**           *referência (Cad_Municipio,          Foro eleito.
                                  opcional)*                           

  **Clausula_Arbitral**           *booleano*                           Adicionado na revisão 7 (Bloco 3).
  ------------------------------- ------------------------------------ -----------------------------------------------------

Garantias e penalidades do contrato (revisão 7)

A forma de assinatura decide se o contrato é título executivo sem
testemunhas (Lei 14.063/2020 e Código de Processo Civil, art. 784, III e
§4º). Caução, fiança, seguro-garantia e demais garantias, e as multas e
penalidades previstas, deixam de ficar em texto livre e viram entidades
próprias. A aplicação da penalidade (cálculo e título a pagar ou a
receber) continua como gancho, como estava: o cadastro só guarda a
regra.

Cad_Gestao_Contrato_Garantia

Nova na revisão 7 (Bloco 3 da validação geral). Caução, fiança,
seguro-garantia e demais garantias do contrato, a favor da Mlegate ou da
contraparte.

*Vigência: não.*

  ----------------------------- -------------------------- ----------------------------------------
  **Campo**                     **Tipo lógico**            **Descrição / regra**

  **ID_Garantia**               *identificador*            ---

  **ID_Contrato**               *referência                ---
                                (Cad_Gestao_Contrato)*     

  **Lado**                      *enumeração                ---
                                {a_favor_da_mlegate,       
                                a_favor_da_contraparte}*   

  **Tipo_Garantia**             *enumeração                ---
                                {caucao_dinheiro,          
                                titulos_divida_publica,    
                                seguro_garantia,           
                                fianca_bancaria,           
                                fianca_pessoal, outra}*    

  **Valor_Garantia**            *número*                   ---

  **Percentual_Contrato**       *número, opcional*         ---

  **ID_Participante_Emissor**   *referência                Seguradora ou banco.
                                (Cad_Participante,         
                                opcional)*                 

  **Numero_Documento**          *código (40), opcional*    ---

  **Data_Emissao**              *data*                     ---

  **Data_Vencimento**           *data, opcional*           Alimenta o aviso de vencimento da Fase
                                                           0.

  **Situacao**                  *enumeração {vigente,      ---
                                liberada, executada,       
                                vencida}*                  

  **ID_Documento**              *referência                ---
                                (Cad_Documento, opcional)* 
  ----------------------------- -------------------------- ----------------------------------------

Cad_Gestao_Contrato_Penalidade

Nova na revisão 7 (Bloco 3 da validação geral). Multas e penalidades
previstas no contrato.

*Vigência: não --- muda por aditivo, já registrado em
Cad_Gestao_Contrato_Aditivo.*

  ------------------------- ------------------------------- ----------------------------------------
  **Campo**                 **Tipo lógico**                 **Descrição / regra**

  **ID_Penalidade**         *identificador*                 ---

  **ID_Contrato**           *referência                     ---
                            (Cad_Gestao_Contrato)*          

  **Lado**                  *enumeração                     ---
                            {aplicavel_a_mlegate,           
                            aplicavel_a_contraparte}*       

  **ID_Gatilho**            *referência                     atraso_entrega, atraso_pagamento,
                            (Cad_Classe_Sistema, domínio =  rescisao_antecipada,
                            gatilho_penalidade_contrato)*   descumprimento_nivel_servico,
                                                            quebra_confidencialidade, outro.

  **Tipo_Calculo**          *enumeração                     ---
                            {percentual_sobre_valor,        
                            valor_fixo,                     
                            percentual_por_dia}*            

  **Percentual**            *número, opcional*              ---

  **Valor**                 *número, opcional*              ---

  **Teto_Percentual**       *número, opcional*              ---

  **Prazo_Carencia_Dias**   *número, opcional*              ---

  **Clausula**              *texto, opcional*               Referência da cláusula no contrato.
  ------------------------- ------------------------------- ----------------------------------------

*Conceito de \"posição\" do contrato, novo nesta Revisão 3: não é um
campo próprio da entidade --- é sempre DERIVADO da classe já existente
do participante (Cad_Participante_Classe.Classe, Fase 0), mesmo
princípio já usado em Cad_Gestao_Contrato.ID_Participante desde a
Revisão 1. Quando ID_Participante é classe FORNECEDOR, a Mlegate está na
posição \"Contratante\" (ela está adquirindo/contratando um serviço ou
produto). Quando ID_Participante é classe CLIENTE, a Mlegate está na
posição \"Contratado\" (ela está prestando o serviço, sendo contratada).
Essa distinção de posição passa a determinar quais campos e
comportamentos do contrato se aplicam --- ID_Filial, Forma_Compromisso e
ID_Instancia_Aprovacao acima, a apuração periódica, o consumo por evento
e a medição formal (seção 4) e o entregável por etapa de fornecedor
(seção 5.2).*

Cad_Gestao_Contrato_Item

NOVO na Revisão 2 --- o detalhamento do preço do contrato por item
(produto/serviço), OPCIONAL: um contrato pode usar só os campos de valor
do cabeçalho de Cad_Gestao_Contrato acima (contrato de valor global, sem
item nenhum --- confirmado por Alberto: \"posso ter contrato por valores
globais\... para produtos/serviços recorrentes\", ex. serviço recorrente
mensal) ou detalhar por item quando o preço precisa ser quebrado por
produto/serviço, cada item com seu próprio modelo de valor, podendo
divergir dos demais itens do mesmo contrato --- confirmado por Alberto:
\"sim pode ter itens que são unitários e outros fechados\".

*Vigência: sim (marcação corrigida na revisão 6) --- um reajuste do item
gera uma nova versão, com nova janela de vigência, sem apagar a
anterior; o item já era versionado por nova linha, só a marcação estava
como \"não\".*

  -------------------------- ------------------------ ----------------------------------------
  **Campo**                  **Tipo lógico**          **Descrição / regra**

  **ID_Item**                *identificador*          ---

  **ID_Item_Versao**         *identificador da        Chave primária da versão (tabela física
                             versão*                  Cad_Gestao_Contrato_Item_Versao).
                                                      ID_Item é a identidade, única e
                                                      referenciada pelas outras tabelas; cada
                                                      versão guarda a sua janela de vigência
                                                      --- Fase 0, seção 2.

  **ID_Contrato**            *referência              ---
                             (Cad_Gestao_Contrato)*   

  **ID_Produto_Servico**     *referência              O produto ou serviço deste item ---
                             (Cad_Produto_Servico,    reaproveita o cadastro único de
                             Fase 0)*                 produto/serviço já existente na Fase 0,
                                                      sem um cadastro de item próprio deste
                                                      módulo.

  **Modelo_Valor**           *enumeração {fixo,       Mesmos três valores de
                             fixo_mais_variavel,      Cad_Gestao_Contrato.Modelo_Valor (seção
                             quantidade_garantida}*   2), mas aplicado por item: cada item
                                                      pode ter um modelo DIFERENTE dos demais
                                                      itens do mesmo contrato, confirmado
                                                      explicitamente por Alberto (\"pode ter
                                                      itens que são unitários e outros
                                                      fechados\").

  **Valor_Fixo**             *número, opcional*       Preenchido quando Modelo_Valor=fixo ou
                                                      fixo_mais_variavel --- mesmo papel do
                                                      campo equivalente do cabeçalho (seção
                                                      2), aplicado a este item.

  **Formula_Variavel**       *texto livre, opcional*  Preenchido quando
                                                      Modelo_Valor=fixo_mais_variavel ---
                                                      mesmo motor de fórmula livre já
                                                      referenciado em
                                                      Cad_Gestao_Contrato.Formula_Variavel
                                                      (seção 2), aplicado a este item.

  **Quantidade_Garantida**   *número, opcional*       Preenchida junto com Valor_Unitario
                                                      quando Modelo_Valor=quantidade_garantida
                                                      --- mesmo papel do campo equivalente do
                                                      cabeçalho, aplicado a este item.

  **Valor_Unitario**         *número, opcional*       Preenchido junto com
                                                      Quantidade_Garantida quando
                                                      Modelo_Valor=quantidade_garantida.

  **Vigencia_Inicio**        *data*                   Início da vigência desta linha de valor
                                                      do item. Renomeado na revisão 6 (antes
                                                      Data_Vigencia_Inicio).

  **Vigencia_Fim**           *data*                   Preenchida quando esta linha de vigência
                                                      do item é encerrada por uma nova ---
                                                      vazio enquanto a linha é a vigente.
                                                      Renomeado na revisão 6 (antes
                                                      Data_Vigencia_Fim). Sempre preenchida:
                                                      31/12/9999 quando o fim é indefinido
                                                      (versão vigente) --- convenção da Fase
                                                      0, seção 2.

  **Motivo_Vigencia**        *texto, opcional*        Por que esta versão foi criada.
  -------------------------- ------------------------ ----------------------------------------

*Nota explícita, para não haver ambiguidade: quando existem linhas de
Cad_Gestao_Contrato_Item para um contrato, os campos de valor do
CABEÇALHO
(Cad_Gestao_Contrato.Modelo_Valor/Valor_Fixo/Formula_Variavel/Quantidade_Garantida/Valor_Unitario,
seção 2) ficam em desuso para aquele contrato --- servem só para o caso
de contrato de valor global, sem item nenhum (ex. serviço recorrente
mensal, confirmado por Alberto: \"posso ter contrato por valores
globais\... para produtos/serviços recorrentes\"). Um contrato usa OU o
cabeçalho OU os itens, nunca os dois ao mesmo tempo.*

*Contrato de frete, usado pela Expedição: é só mais um
Cad_Gestao_Contrato comum, com ID_Participante apontando para a
transportadora (classe fornecedor) --- nenhuma estrutura paralela por
módulo consumidor. O MESMO contrato é referenciável tanto pela Expedição
(o frete de uma carga específica) quanto por uma ordem de
produção/projeto (Produção, Fase 1, quando a ordem é marcada como
projeto), sem duplicação de cadastro entre os dois consumidores. NOVO na
Revisão 4: construído junto com o patch em Expedição (Fase 1, revisão
5), Mov_Expedicao_Saida/Mov_Expedicao_Trecho ganham ID_Contrato opcional
referenciando este contrato, e cada embarque/trecho coberto gera um
Mov_Gestao_Contrato_Consumo (seção 4.2) --- o gancho de extensão futura
registrado desde a Revisão 1 está, portanto, fechado.*

3\. Aditivos e Aprovação

O registro de cada mudança contratual ao longo da vida do contrato ---
prazo, valor, fórmula, quantidade garantida --- sempre como um novo
registro append-only, nunca sobrescrevendo Cad_Gestao_Contrato original,
mesmo princípio de vigência/histórico já usado em todo o dicionário
(ex.: Cad_Participante_Historico_Cargo, Fase 5).

Cad_Gestao_Contrato_Aditivo

Um aditivo contratual --- o que mudou, e os novos valores dos campos
afetados, sempre opcionais conforme o que aquele aditivo especificamente
altera.

*Vigência: não --- cada aditivo é um evento imutável; o histórico
completo é a sequência de aditivos de um contrato ordenada por
Data_Aditivo, nunca sobrescrita.*

  ------------------------------- --------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**             **Descrição / regra**

  **ID_Aditivo**                  *identificador*             ---

  **ID_Contrato**                 *referência                 ---
                                  (Cad_Gestao_Contrato)*      

  **Data_Aditivo**                *data*                      ---

  **Descricao**                   *texto*                     O que mudou, em texto livre --- a
                                                              motivação e o resumo do aditivo.

  **Novo_Data_Fim**               *data, opcional*            Preenchido quando o aditivo estende (ou
                                                              reduz) a vigência do contrato.

  **Novo_Valor_Fixo**             *número, opcional*          Preenchido quando o aditivo altera o
                                                              valor fixo (Modelo_Valor=fixo ou
                                                              fixo_mais_variavel).

  **Nova_Formula_Variavel**       *texto livre, opcional*     Preenchido quando o aditivo altera a
                                                              fórmula variável
                                                              (Modelo_Valor=fixo_mais_variavel) ---
                                                              mesmo motor de fórmula livre de
                                                              Cad_Gestao_Contrato.Formula_Variavel.

  **Nova_Quantidade_Garantida**   *número, opcional*          Preenchido quando o aditivo altera o
                                                              mínimo garantido
                                                              (Modelo_Valor=quantidade_garantida).

  **Novo_Valor_Unitario**         *número, opcional*          Preenchido quando o aditivo altera o
                                                              valor unitário
                                                              (Modelo_Valor=quantidade_garantida).

  **ID_Instancia_Aprovacao**      *referência                 A régua de aprovação INTERNA (alçada da
                                  (Mov_Aprovacao_Instancia,   Mlegate) do aditivo --- reaproveita o
                                  Fase 0 seção 9)*            mesmo Origem_Tipo já usado na aprovação
                                                              do próprio contrato (contrato_aquisicao
                                                              ou contrato_venda, conforme a posição do
                                                              contrato sendo alterado, seção 2), com
                                                              ID_Origem=ID_Aditivo em vez de
                                                              ID_Contrato --- não precisa de um
                                                              terceiro Origem_Tipo próprio de aditivo,
                                                              confirmado por Alberto.

  **Data_Aceite_Contraparte**     *data, opcional*            O aceite/assinatura da CONTRAPARTE
                                                              (cliente ou fornecedor) --- campo
                                                              separado da régua de aprovação interna,
                                                              nunca misturado com ela: aditivo
                                                              contratual passa por DUPLA aprovação, e
                                                              este segundo lado não é uma aprovação
                                                              interna, é o aceite externo da outra
                                                              parte do contrato. Vazio enquanto a
                                                              contraparte não tiver aceitado
                                                              formalmente.
  ------------------------------- --------------------------- ----------------------------------------

*Dupla aprovação, precisada explicitamente por Alberto: um aditivo
contratual precisa tanto da régua de aprovação INTERNA (a alçada da
Mlegate, reaproveitando o motor
Cad_Regua_Aprovacao/Mov_Aprovacao_Instancia já existente desde a Fase 0
--- e, desde a Revisão 3, o mesmo Origem_Tipo já usado na aprovação do
contrato sendo alterado, contrato_aquisicao ou contrato_venda conforme a
posição, seção 2, com ID_Origem=ID_Aditivo, em vez de um terceiro
Origem_Tipo próprio de aditivo) quanto do aceite da CONTRAPARTE (cliente
ou fornecedor) --- os dois mecanismos são estruturalmente distintos e
não se substituem: a régua interna decide se a Mlegate aprova a mudança;
Data_Aceite_Contraparte registra se a outra parte também aceitou. Um
aditivo pode estar aprovado internamente e ainda pendente de aceite da
contraparte, ou vice-versa --- os dois campos evoluem de forma
independente.*

*O documento assinado do aditivo (o instrumento contratual em si) é
anexado via GED --- Cad_Documento_Vinculo (Fase 0, seção 11) ---, mesmo
mecanismo genérico já usado em todo o dicionário para vincular um
documento a qualquer entidade, sem um campo de anexo dedicado nesta
tabela.*

4\. Apuração, Consumo e Medição

Três mecanismos de cálculo do valor devido pelo contrato, cada um
cobrindo um padrão de contrato diferente: apuração periódica no
fechamento do período (4.1); consumo por evento, calculado na hora de
cada uso (4.2); e medição formal, camada opcional de validação de avanço
físico/financeiro antes de cobrar (4.3). Um mesmo contrato usa o
mecanismo que se aplica ao seu modelo --- os três convergem no mesmo
título a pagar/receber (Contas a Pagar/Receber, Fase 2).

4.1 Apuração Periódica

O cálculo periódico do valor efetivamente devido pelo contrato --- o
único ponto do módulo onde o valor a cobrar é de fato apurado e gera o
título financeiro correspondente.

Mov_Gestao_Contrato_Apuracao

Uma apuração de um contrato para um período de referência --- quantidade
real (quando aplicável), valor variável apurado (quando aplicável) e o
valor total cobrado, sempre derivado, nunca digitado solto.

*Vigência: não --- é o registro de um evento (a apuração de um período);
uma correção gera uma nova linha, nunca uma edição da apuração original,
mesma filosofia de fidelidade ao valor real do restante do dicionário.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Apuracao** | *identificador* | --- |
| **ID_Contrato** | *referência (Cad_Gestao_Contrato)* | --- |
| **ID_Item** | *referência (Cad_Gestao_Contrato_Item, opcional)* | NOVO na Revisão 2 --- preenchido quando o contrato tem itens (seção 2): a apuração passa a poder ocorrer por item, uma linha de apuração por item, cada uma com sua própria Quantidade_Real/Valor_Variavel_Apurado/Valor_Total_Cobrado calculada conforme o Modelo_Valor daquele item específico, não mais o do cabeçalho. Vazio quando o contrato não tem itens --- a apuração continua no nível do contrato inteiro, como já documentado. |
| **ID_Periodo_Referencia** | *referência (Cad_Periodo_Fechamento, Fase 0 seção 10, ID_Bloco=\"gestao_contratos\")* | NOVO nesta Revisão 5 --- o período apurado, agora um período de fechamento PRÓPRIO deste bloco (Cad_Bloco_Fechamento.Codigo=\"gestao_contratos\"), independente do período contábil: pedido explícito de Alberto, generalizado por ele para todos os módulos do dicionário --- mesmo mecanismo transversal (Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial, Fase 0 seção 10) hoje usado por Compras, Expedição e demais blocos. Substitui a referência a Cad_Periodo_Contabil da revisão anterior (ver nota corrigida, seção 7). |
| **Quantidade_Real** | *número, opcional* | Para Modelo_Valor=quantidade_garantida: a quantidade de fato utilizada no período. Para contrato por hora corrida, é a soma de Mov_Apontamento_Tempo.Horas_Efetivas (Produção, Fase 1, seção 4) do período, entre os apontamentos cujo ID_Contrato aponta para este contrato --- sem duplicar o registro do apontamento em si. |
| **Valor_Variavel_Apurado** | *número, opcional* | Calculado pela Formula_Variavel de Cad_Gestao_Contrato (ou pela mais recente Nova_Formula_Variavel de aditivo aplicável) quando Modelo_Valor=fixo_mais_variavel --- o resultado da fórmula para este período específico, armazenado após o cálculo, não recalculado a cada consulta. |
| **Valor_Total_Cobrado** | *número* | Sempre derivado, nunca digitado solto --- a fórmula depende de Modelo_Valor: para quantidade_garantida = MAIOR(Quantidade_Real, Quantidade_Garantida) × Valor_Unitario, cobrando a diferença quando o uso real ultrapassa o mínimo garantido e cobrando o próprio mínimo quando o uso real fica abaixo dele, confirmado explicitamente por Alberto; para fixo_mais_variavel = Valor_Fixo + Valor_Variavel_Apurado; para fixo = sempre Valor_Fixo, gerado automaticamente todo período, sem nenhuma apuração variável real por trás. Quando ID_Item está preenchido, Modelo_Valor consultado é o do item (Cad_Gestao_Contrato_Item, seção 2), não o do cabeçalho do contrato. |
| **ID_Medicao** | *referência (Mov_Gestao_Contrato_Medicao, seção 4.3), opcional* | NOVO na Revisão 4 --- preenchido quando este período de apuração está amarrado a uma medição formal (ver seção 4.3) --- vazio para contrato sem medição. |
| **ID_Nota_Fiscal_Entrada** | *referência (Mov_Nota_Fiscal_Entrada, Compras --- Fase 1), opcional* | NOVO na Revisão 3 --- o documento fiscal do fornecedor referente a este período --- usado tanto para conferir uma medição formal (seção 4.3, quando ID_Medicao está preenchido) quanto para conciliar consumo por evento acumulado no período (seção 4.2, quando o contrato usa Mov_Gestao_Contrato_Consumo) --- só relevante na posição Contratante. |
| **ID_Titulo** | *referência (Mov_Titulo, Contas a Pagar/Receber --- Fase 2, opcional)* | O título gerado a partir desta apuração --- a pagar, quando o participante do contrato é fornecedor, ou a receber, quando é cliente. Vazio até o título ser de fato gerado a partir da apuração. |
| **Data_Exigibilidade** | *data, opcional* | Revisão 31 (documento 157, seção 3.5, Q157-1; D-N466 e D-N469): A data que o critério da regra (Criterio_Exigibilidade: fatura, medição aceita, vencimento contratual) indica; o contrato periódico sem título (ID_Titulo vazio) não tinha a data em que o direito de receber se constitui. O fato gerador (a menor entre esta data e a primeira baixa) se deriva (LC 214, art. 10, § 3º). |

*Revisão 31 --- campos novos: Data_Exigibilidade.*

*Comportamento de aplicação, confirmado por Alberto: \"Quando eu for
contratante, o pagamento tem que estar amarrado a uma medição e/ou nota
fiscal\" --- na posição Contratante (seção 2), o título a pagar gerado a
partir desta apuração NUNCA nasce solto: precisa ter pelo menos um dos
dois preenchidos, ID_Medicao OU ID_Nota_Fiscal_Entrada (podem ser os
dois juntos). Na posição Contratado, essa exigência não se aplica --- o
título a receber nasce normalmente do valor apurado, como já
documentado.*

*Comportamento de aplicação, NOVO na Revisão 4: quando o contrato usa
consumo por evento (seção 4.2), Valor_Total_Cobrado deste período é a
soma de Mov_Gestao_Contrato_Consumo.Valor_Calculado de todos os consumos
daquele contrato/item ainda em aberto (ID_Apuracao vazio, seção 4.2) até
a data de fechamento --- nunca um valor solto. Ao fechar, cada consumo
incluído recebe este ID_Apuracao. A nota fiscal vinculada
(ID_Nota_Fiscal_Entrada, acima) é conferida contra esse total --- alerta
de divergência, nunca recálculo, mesmo princípio já usado em Compras
para conferir nota contra pedido.*

4.2 Consumo por Evento

NOVO na Revisão 4. Alguns contratos na posição Contratante têm o valor
calculado no momento de cada uso, não só apurado no fechamento do
período --- o exemplo trazido por Alberto é frete contratado por km ou
por entrega (ver Expedição, Fase 1): cada embarque gera seu próprio
custo calculado na hora, pela tarifa já negociada no contrato, e esses
valores se acumulam até fechar contra a nota fiscal de cobrança que a
transportadora enviar --- o mesmo vale para qualquer outro serviço
contratado com esse padrão de uso recorrente e tarifado, não só frete.

Mov_Gestao_Contrato_Consumo

Uma linha por evento de uso/consumo de um contrato --- quantidade e
valor SEMPRE em campos separados, nunca misturados, confirmado por
Alberto.

*Vigência: sim, parcialmente --- Quantidade e Valor_Calculado são
imutáveis desde o registro do evento; ID_Apuracao é o único campo
preenchido depois, no fechamento do período (seção 4.1).*

  --------------------- -------------------------------- ----------------------------------------
  **Campo**             **Tipo lógico**                  **Descrição / regra**

  **ID_Consumo**        *identificador*                  ---

  **ID_Contrato**       *referência                      ---
                        (Cad_Gestao_Contrato)*           

  **ID_Item**           *referência                      Preenchido quando o contrato tem preço
                        (Cad_Gestao_Contrato_Item, seção por item (seção 2) --- vazio para
                        2), opcional*                    contrato de valor global.

  **Data_Consumo**      *data*                           ---

  **Origem_Tipo**       *texto (nome da entidade de      O tipo/entidade de origem do evento que
                        origem)*                         gerou este consumo, mesmo padrão de
                                                         referência genérica
                                                         (Origem_Tipo/ID_Origem) já usado em todo
                                                         o dicionário --- no caso do frete,
                                                         \"Mov_Expedicao_Saida\" ou
                                                         \"Mov_Expedicao_Trecho\" (Expedição,
                                                         Fase 1); outro serviço contratado com
                                                         esse padrão de uso recorrente usaria seu
                                                         próprio valor aqui.

  **ID_Origem**         *referência genérica*            O identificador do registro de origem,
                                                         dentro da entidade indicada por
                                                         Origem_Tipo --- no caso do frete, aponta
                                                         para um Mov_Expedicao_Saida ou
                                                         Mov_Expedicao_Trecho específico
                                                         (Expedição, Fase 1).

  **Quantidade**        *número*                         Km, entregas, ou qualquer unidade física
                                                         do evento --- sempre em campo separado
                                                         do valor calculado (Valor_Calculado,
                                                         abaixo), nunca misturados, confirmado
                                                         por Alberto.

  **Valor_Calculado**   *número*                         O valor já calculado na hora do evento,
                                                         pela tarifa negociada no contrato (ou no
                                                         item do contrato, quando ID_Item está
                                                         preenchido) --- fidelidade ao valor
                                                         calculado no momento, nunca recalculado
                                                         depois.

  **ID_Apuracao**       *referência                      Vazio significa que este consumo ainda
                        (Mov_Gestao_Contrato_Apuracao,   está EM ABERTO, não incluído em nenhum
                        seção 4.1), opcional*            fechamento de período; \"em aberto a ser
                                                         cobrado\" nunca é um campo armazenado, é
                                                         sempre a consulta dos consumos com este
                                                         campo vazio, mesmo princípio de nunca
                                                         guardar o que pode ser derivado.

  **Vigencia_Inicio**   *data*                           Primeiro dia em que esta versão vale.

  **Vigencia_Fim**      *data*                           Último dia em que esta versão vale
                                                         (inclusive). Sempre preenchida:
                                                         31/12/9999 quando o fim é indefinido
                                                         (versão vigente) --- convenção da Fase
                                                         0, seção 2.

  **Motivo_Vigencia**   *texto, opcional*                Por que esta versão foi criada.
  --------------------- -------------------------------- ----------------------------------------

*Comportamento de aplicação --- fechamento de período
(bloco=gestao_contratos), NOVO na Revisão 5: antes de aceitar o registro
de um Mov_Gestao_Contrato_Consumo, o sistema consulta
Cad_Periodo_Fechamento_Filial (mecanismo transversal da Fase 0, seção
10) pela combinação Bloco=\"gestao_contratos\" + Filial do contrato
(Cad_Gestao_Contrato.ID_Filial) + competência derivada de Data_Consumo
--- na ausência de uma linha com Status=aberto para essa combinação
(regime fail-closed, mesmo princípio já usado em toda a Fase 0), o
registro é bloqueado. Mesmo gate agora aplicado a ID_Periodo_Referencia
(seção 4.1) e a Mov_Gestao_Contrato_Medicao (seção 4.3) --- um consumo
não pode ser incluído (ID_Apuracao, acima) numa apuração cujo período já
esteja fechado para aquela filial.*

4.3 Medição Formal

Camada OPCIONAL, só para contrato que exige validação formal antes de
cobrar --- ex. obra de construção civil (ver Cad_Obra, Fase 0), ou um
projeto cuja parcela mensal só é liberada depois que um entregável
específico é aceito. Contratos mais simples (recorrência direta, ou
consumo por evento como frete, seção 4.2) não precisam de nenhuma
Mov_Gestao_Contrato_Medicao.

Mov_Gestao_Contrato_Medicao

O cabeçalho de uma medição formal de avanço físico/financeiro de um
contrato --- substitui Mov_Obra_Medicao, que existia em Cad_Obra (Fase
0) só para construção civil e só para a posição Contratado; esta versão
é única e serve as duas posições.

*Vigência: sim --- Status, Data_Validacao, ID_Nota_Fiscal_Saida/Entrada
e ID_Titulo são preenchidos e atualizados ao longo do fluxo de validação
e faturamento da medição.*

  ------------------------------ ---------------------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**                    **Descrição / regra**

  **ID_Medicao**                 *identificador*                    ---

  **ID_Medicao_Versao**          *identificador da versão*          Chave primária da versão (tabela física
                                                                    Mov_Gestao_Contrato_Medicao_Versao).
                                                                    ID_Medicao é a identidade, única e
                                                                    referenciada pelas outras tabelas; cada
                                                                    versão guarda a sua janela de vigência
                                                                    --- Fase 0, seção 2.

  **ID_Contrato**                *referência (Cad_Gestao_Contrato)* ---

  **ID_Entregavel**              *referência                        O vínculo que faz uma parcela mensal só
                                 (Mov_Gestao_Contrato_Entregavel,   ser liberada depois que o entregável
                                 seção 5.2), opcional*              referenciado está com Status=aceito ---
                                                                    confirmado por Alberto: \"pode ter
                                                                    contratos que pago mensalmente só um
                                                                    grupo de parcelas que seriam pagas
                                                                    depois de um entregável\". Vazio para
                                                                    medição puramente periódica, sem
                                                                    entregável associado.

  **Numero_Medicao**             *número*                           Sequencial por contrato.

  **Data_Medicao**               *data*                             ---

  **Periodo_Inicio**             *data*                             ---

  **Periodo_Fim**                *data*                             ---

  **Percentual_Avanco_Fisico**   *número, opcional*                 ---

  **Valor_Medido**               *número*                           ---

  **Status**                     *enumeração {em_elaboracao,        em_validacao cobre tanto o envio ao
                                 em_validacao, aprovada, rejeitada, cliente para validação, quando
                                 faturada}*                         Contratado, quanto a conferência interna
                                                                    da Mlegate, quando Contratante --- sem
                                                                    duas palavras diferentes para a mesma
                                                                    etapa do fluxo.

  **Data_Validacao**             *data, opcional*                   ---

  **ID_Nota_Fiscal_Saida**       *referência                        Quando Contratado, a nota emitida pela
                                 (Mov_Nota_Fiscal_Saida, CRM &      Mlegate a partir desta medição.
                                 Vendas --- Fase 1), opcional*      

  **ID_Nota_Fiscal_Entrada**     *referência                        Quando Contratante, a nota do fornecedor
                                 (Mov_Nota_Fiscal_Entrada, Compras  referente a esta medição.
                                 --- Fase 1), opcional*             

  **ID_Titulo**                  *referência (Mov_Titulo, Contas a  ---
                                 Pagar/Receber --- Fase 2),         
                                 opcional*                          

  **Vigencia_Inicio**            *data*                             Primeiro dia em que esta versão vale.

  **Vigencia_Fim**               *data*                             Último dia em que esta versão vale
                                                                    (inclusive). Sempre preenchida:
                                                                    31/12/9999 quando o fim é indefinido
                                                                    (versão vigente) --- convenção da Fase
                                                                    0, seção 2.

  **Motivo_Vigencia**            *texto, opcional*                  Por que esta versão foi criada.
  ------------------------------ ---------------------------------- ----------------------------------------

Mov_Gestao_Contrato_Medicao_Item

O detalhamento por item/quantidade medida dentro de uma medição ---
mesmo padrão que existia em Mov_Obra_Medicao_Item (Fase 0, agora
aposentada).

*Vigência: não --- é o detalhamento imutável de uma medição fechada; uma
correção gera uma nova medição (e novos itens), nunca uma edição direta
dos itens já registrados.*

  ----------------------- -------------------------------- ----------------------------------------
  **Campo**               **Tipo lógico**                  **Descrição / regra**

  **ID_Item_Medicao**     *identificador*                  ---

  **ID_Medicao**          *referência                      ---
                          (Mov_Gestao_Contrato_Medicao)*   

  **ID_Item**             *referência                      Preenchido quando o item medido
                          (Cad_Gestao_Contrato_Item, seção corresponde a um item já cadastrado do
                          2), opcional*                    contrato.

  **Descricao_Item**      *texto, opcional*                Descrição livre, quando não há
                                                           Cad_Gestao_Contrato_Item correspondente.

  **Quantidade_Medida**   *número*                         ---
  ----------------------- -------------------------------- ----------------------------------------

*Comportamento de aplicação --- fechamento de período
(bloco=gestao_contratos), NOVO na Revisão 5: pelo mesmo motor
transversal da Fase 0 (seção 10), nenhuma Mov_Gestao_Contrato_Medicao
pode ser registrada ou alterada com Data_Medicao dentro de uma
competência já fechada para a Filial do contrato
(Cad_Gestao_Contrato.ID_Filial) no bloco \"gestao_contratos\" --- mesma
consulta a Cad_Periodo_Fechamento_Filial e o mesmo regime fail-closed
descritos em 4.2, acima. Sem validação de pendência associada a este
fechamento --- mesma decisão já registrada para o módulo inteiro (seção
7): contrato vigente atravessa meses, mesma lógica de Produção.*

5\. Entregável e Cobrança por Etapa

5.1 Posição Contratado --- entregável de projeto próprio (Produção)

Esta subseção é exclusiva da posição Contratado (seção 2) --- a Mlegate
entregando via sua própria Produção. NOVO na Revisão 2. Contratos com
Modelo_Faturamento=periodico (seção 2) continuam usando a apuração da
seção 4.1, calculada por período de referência, independente de qualquer
entrega física do projeto. Contratos com
Modelo_Faturamento=por_entregavel faturam, em vez disso, no ritmo do
projeto: cada entregável concluído --- Mov_Ordem_Producao_Entregavel
(Produção, Fase 1), o mesmo entregável que agrupa uma ou N fases da
ordem de produção/projeto, confirmado por Alberto: \"sim um entregável é
composto pode 1 ou n fases do projeto\" --- gera uma linha de
faturamento própria, sem esperar o fechamento de um período contábil.
Confirmado por Alberto: \"sim tem contratos que são faturamento
periódico e outros por entregáveis\".

Mov_Gestao_Contrato_Faturamento_Entregavel

O faturamento de um contrato disparado pela conclusão de um entregável
do projeto, um registro por entregável concluído.

*Vigência: não --- é o registro de um evento (o faturamento de um
entregável concluído); uma correção gera uma nova linha, nunca uma
edição da original, mesma filosofia de fidelidade ao valor real do
restante do dicionário.*

  ---------------------- --------------------------------- ----------------------------------------
  **Campo**              **Tipo lógico**                   **Descrição / regra**

  **ID_Faturamento**     *identificador*                   ---

  **ID_Contrato**        *referência                       Sempre um contrato com
                         (Cad_Gestao_Contrato)*            Modelo_Faturamento=por_entregavel (seção
                                                           2).

  **ID_Entregavel**      *referência                       O entregável do projeto que disparou
                         (Mov_Ordem_Producao_Entregavel,   este faturamento --- entidade do módulo
                         Produção, Fase 1)*                Produção, construída em paralelo com
                                                           este documento (Produção, revisão 9): um
                                                           entregável agrupa uma ou N fases da
                                                           ordem de produção/projeto.

  **Data_Faturamento**   *data*                            ---

  **Valor_Faturado**     *número*                          O valor faturado para este entregável
                                                           específico.

  **ID_Titulo**          *referência (Mov_Titulo, Contas a O título gerado a partir deste
                         Pagar/Receber, Fase 2, opcional)* faturamento --- mesmo padrão já usado em
                                                           Mov_Gestao_Contrato_Apuracao.ID_Titulo
                                                           (seção 4.1). Vazio até o título ser de
                                                           fato gerado.
  ---------------------- --------------------------------- ----------------------------------------

*Comportamento de aplicação: este registro é gerado automaticamente
quando Mov_Ordem_Producao_Entregavel.Status (Produção, Fase 1) muda para
concluido, para contratos com Modelo_Faturamento=por_entregavel (seção
2) --- nenhuma ação manual do usuário dispara o faturamento, é reativo
ao evento de conclusão do entregável.*

5.2 Posição Contratante --- entregável de fornecedor por etapa

NOVO na Revisão 3. Um contrato na posição Contratante também pode ser
por projeto com entregáveis --- exemplo dado por Alberto: contratação da
construção de um galpão, com etapas como terraplenagem, fundação,
estrutura, instalações, entre outras. Aqui quem entrega cada etapa é o
FORNECEDOR, não a Produção da própria Mlegate --- por isso este caso usa
uma entidade própria deste módulo, em vez de
Mov_Ordem_Producao_Entregavel (Produção, que serve só a posição
Contratado, quando é a Mlegate quem produz/entrega).

Mov_Gestao_Contrato_Entregavel

Uma etapa de entrega dentro de um contrato na posição Contratante ---
cada contrato define suas próprias etapas, sem uma lista fixa (ex.:
terraplenagem, fundação, estrutura, instalações, no exemplo de uma
obra).

*Vigência: sim --- Status, Data_Entrega_Real, Data_Aceite,
ID_Nota_Fiscal_Entrada e ID_Titulo são preenchidos e atualizados ao
longo da vida da própria etapa, à medida que ela avança; diferente da
apuração periódica (seção 4.1), que fecha um evento por período, aqui é
o estado atual de uma etapa em progresso.*

  ---------------------------- ------------------------------- -----------------------------------------
  **Campo**                    **Tipo lógico**                 **Descrição / regra**

  **ID_Entregavel**            *identificador*                 ---

  **ID_Entregavel_Versao**     *identificador da versão*       Chave primária da versão (tabela física
                                                               Mov_Gestao_Contrato_Entregavel_Versao).
                                                               ID_Entregavel é a identidade, única e
                                                               referenciada pelas outras tabelas; cada
                                                               versão guarda a sua janela de vigência
                                                               --- Fase 0, seção 2.

  **ID_Contrato**              *referência                     Sempre um contrato na posição Contratante
                               (Cad_Gestao_Contrato)*          (seção 2).

  **Nome**                     *texto*                         Ex.: \"Terraplenagem\", \"Fundação\",
                                                               \"Estrutura\", \"Instalações\" --- texto
                                                               livre, cada contrato define as suas.

  **Descricao**                *texto, opcional*               ---

  **Data_Entrega_Estimada**    *data*                          ---

  **Data_Entrega_Real**        *data, opcional*                ---

  **Status**                   *enumeração {em_andamento,      \"entregue\" é o fornecedor avisando que
                               entregue, aceito, rejeitado,    concluiu a etapa; \"aceito\" é a Mlegate
                               cancelado}*                     validando --- só a partir do aceite a
                                                               etapa pode ser cobrada, mesmo espírito da
                                                               inspeção de qualidade que já condiciona o
                                                               fechamento do pedido em Compras (seção 7
                                                               daquele documento).

  **Data_Aceite**              *data, opcional*                Preenchida quando Status muda para
                                                               aceito.

  **Valor_Etapa**              *número*                        O valor contratado para esta etapa
                                                               específica, informado diretamente ---
                                                               fidelidade ao que foi negociado, nunca
                                                               recalculado.

  **ID_Medicao**               *referência                     NOVO na Revisão 4 --- preenchido quando
                               (Mov_Gestao_Contrato_Medicao,   esta etapa específica precisa de medição
                               seção 4.3), opcional*           formal itemizada (ex. uma etapa grande de
                                                               obra que precisa detalhar quantidades
                                                               medidas item a item) --- o fluxo simples
                                                               (Status entregue→aceito, acima) continua
                                                               funcionando sozinho, sem medição, para
                                                               etapas que não precisam desse
                                                               detalhamento.

  **ID_Nota_Fiscal_Entrada**   *referência                     O documento fiscal do fornecedor
                               (Mov_Nota_Fiscal_Entrada,       referente a esta etapa, quando já
                               Compras --- Fase 1), opcional*  recebido.

  **ID_Titulo**                *referência (Mov_Titulo, Contas O título a pagar gerado a partir desta
                               a Pagar/Receber --- Fase 2),    etapa aceita. Vazio até o título ser de
                               opcional*                       fato gerado.

  **Vigencia_Inicio**          *data*                          Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                          Último dia em que esta versão vale
                                                               (inclusive). Sempre preenchida:
                                                               31/12/9999 quando o fim é indefinido
                                                               (versão vigente) --- convenção da Fase 0,
                                                               seção 2.

  **Motivo_Vigencia**          *texto, opcional*               Por que esta versão foi criada.
  ---------------------------- ------------------------------- -----------------------------------------

*Regra análoga à apuração periódica (seção 4.1), confirmada por Alberto:
o título a pagar só nasce quando Status=aceito E pelo menos um dos dois,
ID_Medicao (quando a etapa exige medição formal, seção 4.3) OU
ID_Nota_Fiscal_Entrada, estiver preenchido --- nunca os dois vazios ao
mesmo tempo.*

6\. Como Este Módulo se Conecta com a Fase 0 e Outros Módulos

  --------------------------------- ----------------------------------------------- ----------------
  **Entidade referenciada**         **Como este módulo usa**                        **Observação**

  **Cad_Participante / Cad_Empresa  O cliente ou fornecedor do contrato             *Fase 0, sem
  (Fase 0)**                        (Cad_Gestao_Contrato.ID_Participante) e a       mudança
                                    empresa do grupo Mlegate parte dele --- mesmo   estrutural*
                                    cadastro único de participante, papel dado pela 
                                    classe existente.                               

  **Cad_Serie_Cotacao (Fase 0,      O índice financeiro de reajuste do contrato     *Fase 0, seção
  seção 15)**                       (ID_Serie_Cotacao_Reajuste, seção 2), sempre    15 ---
                                    Tipo=indice_financeiro.                         construída em
                                                                                    paralelo*

  **Cad_Produto_Servico (Fase 0)**  O produto ou serviço de cada item de contrato,  *Fase 0 --- sem
                                    quando o contrato é detalhado por item          mudança
                                    (Cad_Gestao_Contrato_Item.ID_Produto_Servico,   estrutural*
                                    seção 2).                                       

  **Cad_Regua_Aprovacao /           A aprovação do contrato em si, com              *Fase 0, seção 9
  Mov_Aprovacao_Instancia (Fase 0,  Origem_Tipo=contrato_aquisicao (posição         --- dois novos
  seção 9)**                        Contratante) ou contrato_venda (posição         valores de
                                    Contratado) --- seção 2 ---, e a aprovação      domínio,
                                    interna de cada aditivo contratual, que         compartilhados
                                    reaproveita o mesmo Origem_Tipo do contrato     entre contrato e
                                    sendo alterado, com ID_Origem=ID_Aditivo (seção aditivo*
                                    3).                                             

  **Cad_Documento_Vinculo / GED     O documento assinado do aditivo é anexado por   *Fase 0, seção
  (Fase 0, seção 11)**              este mecanismo genérico (seção 3), sem campo de 11, sem mudança
                                    anexo próprio.                                  estrutural*

  **Mov_Apontamento_Tempo           O apontamento de horas de contrato por hora     *Produção, Fase
  (Produção, Fase 1, seção 4)**     corrida --- referenciado tanto pela             1, seção 4 ---
                                    Formula_Variavel do contrato (seção 2) quanto   ganha
                                    pela Quantidade_Real da apuração periódica      ID_Contrato em
                                    (seção 4.1), somando os apontamentos cujo       paralelo*
                                    ID_Contrato aponta para este contrato.          

  **Mov_Ordem_Producao_Entregavel   O entregável do projeto cuja conclusão dispara  *Produção, Fase
  (Produção, Fase 1)**              o faturamento por entregável                    1 --- construída
                                    (Mov_Gestao_Contrato_Faturamento_Entregavel,    em paralelo,
                                    seção 5.1), para contratos na posição           revisão 9*
                                    Contratado com                                  
                                    Modelo_Faturamento=por_entregavel (seção 2).    

  **Mov_Nota_Fiscal_Entrada         O documento fiscal do fornecedor amarrado à     *Compras, Fase 1
  (Compras, Fase 1)**               apuração (seção 4.1), ao consumo por evento     --- sem mudança
                                    (seção 4.2), à medição (seção 4.3) ou ao        estrutural*
                                    entregável (seção 5.2) de um contrato na        
                                    posição Contratante.                            

  **Mov_Titulo (Contas a            O título a pagar (fornecedor) ou a receber      *Contas a
  Pagar/Receber, Fase 2)**          (cliente) gerado por cada apuração periódica    Pagar/Receber,
                                    (seção 4.1), por cada faturamento por           Fase 2, seção 2*
                                    entregável na posição Contratado (seção 5.1) ou 
                                    por cada entregável aceito na posição           
                                    Contratante                                     
                                    (Mov_Gestao_Contrato_Entregavel.ID_Titulo,      
                                    seção 5.2).                                     

  **Mov_Expedicao_Saida /           O contrato de frete com a transportadora é um   *Expedição, Fase
  Mov_Expedicao_Trecho (Expedição,  Cad_Gestao_Contrato comum (seção 2);            1 --- patch
  Fase 1)**                         Mov_Expedicao_Saida/Mov_Expedicao_Trecho ganham construído em
                                    ID_Contrato opcional e geram                    paralelo,
                                    Mov_Gestao_Contrato_Consumo (seção 4.2) a cada  revisão 5*
                                    embarque/trecho coberto por um contrato de      
                                    frete pré-estabelecido.                         

  **Cad_Obra (Fase 0)**             Classificação PAIC de um contrato de construção *Fase 0 ---
                                    civil, quando aplicável --- a medição em si     Cad_Obra
                                    (seção 4.3) vive aqui, não mais em Cad_Obra.    reduzido nesta
                                                                                    rodada, patch
                                                                                    construído em
                                                                                    paralelo*

  **Cad_Bloco_Fechamento /          NOVO na Revisão 5 --- o período de fechamento   *Fase 0, seção
  Cad_Periodo_Fechamento /          PRÓPRIO deste módulo                            10 --- revisão
  Cad_Periodo_Fechamento_Filial     (Bloco=\"gestao_contratos\"), referenciado por  37, mecanismo
  (Fase 0, seção 10)**              ID_Periodo_Referencia (seção 4.1) e consultado  generalizado a
                                    por Filial+competência antes de aceitar         partir deste
                                    apuração, consumo por evento (seção 4.2) ou     módulo*
                                    medição (seção 4.3) --- gatilho original deste  
                                    mecanismo transversal, hoje reaproveitado por   
                                    todos os módulos.                               
  --------------------------------- ----------------------------------------------- ----------------

7\. Notas para a Sua Revisão

-   Gestão de Projetos (PPM), que originalmente seria a segunda metade
    deste módulo no Documento Analítico, não está neste documento ---
    foi fundida em Produção (Fase 1) por decisão explícita e definitiva
    de Alberto, numa revisão anterior daquele documento; este documento
    não a trata como pendência.

-   Fechado nesta Revisão 4 o gancho registrado desde a Revisão 1:
    Expedição (Fase 1) foi patcheada, em paralelo (revisão 5 daquele
    documento), para Mov_Expedicao_Saida/Mov_Expedicao_Trecho ganharem
    ID_Contrato opcional referenciando Cad_Gestao_Contrato --- cada
    embarque/trecho coberto por contrato de frete gera um
    Mov_Gestao_Contrato_Consumo (seção 4.2, ver seção 2 e seção 6).

-   A integração técnica de busca automática do valor do índice de
    reajuste (ex.: consumir a fonte oficial e alimentar
    Mov_Serie_Cotacao_Valor periodicamente) fica inteiramente em Fase 0
    (Cad_Serie_Cotacao/Mov_Serie_Cotacao_Valor, seção 15) --- este
    documento só consome a série já resolvida, sem duplicar essa
    responsabilidade.

-   Corrigido na Revisão 5: ID_Periodo_Referencia
    (Mov_Gestao_Contrato_Apuracao, seção 4.1) tinha sido modelado, na
    revisão anterior, como referência a Cad_Periodo_Contabil (Fase 0)
    --- extensão registrada ali como não confirmada por Alberto, por
    analogia ao mesmo padrão já usado em outras entidades de apuração
    periódica deste dicionário (Planejamento & Orçamento, Folha & RH).
    Essa analogia estava equivocada: Folha & RH nunca usou o período
    contábil --- sempre teve período PRÓPRIO, independente, desde a
    primeira entrega daquele documento. Foi exatamente Alberto quem
    apontou o problema de fundo, generalizando-o a partir deste módulo:
    \"O período de fechamento dos contratos tem que ser independente do
    contábil, pois precisa ser fechados todos os contratos para a
    contabilização sem interferência de eventual alteração no contrato\"
    --- e, na sequência, estendeu a mesma exigência a todos os módulos
    do dicionário. Resultado: a Fase 0 generalizou seu antigo período
    contábil exclusivo da Contabilidade
    (Cad_Periodo_Contabil/Cad_Periodo_Contabil_Filial) num mecanismo
    transversal por bloco
    (Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial,
    Fase 0 seção 10, revisão 37), e este módulo passou a consumi-lo com
    Bloco=\"gestao_contratos\" --- ID_Periodo_Referencia (seção 4.1),
    Mov_Gestao_Contrato_Consumo (seção 4.2) e
    Mov_Gestao_Contrato_Medicao (seção 4.3) travados por
    Filial+competência, fail-closed, sem validação de pendência no
    fechamento (contrato vigente atravessa meses, mesma lógica de
    Produção). Gestão de Contratos foi, portanto, o gatilho original de
    todo este mecanismo --- não mais uma suposição em aberto.

-   Fechado nesta Revisão 2: o modelo de preço por item do contrato
    (Cad_Gestao_Contrato_Item, opcional, cada item com seu próprio
    Modelo_Valor), a apuração periódica por item, e o faturamento por
    entregável (Modelo_Faturamento, seção 5.1), construído junto com o
    patch em Produção (revisão 9) que introduz o conceito de entregável
    --- os três pontos pedidos por Alberto nesta rodada.

-   Nesta Revisão 3, o módulo de Compras (Fase 1) aposentou
    Cad_Contrato_Fornecimento/Cad_Contrato_Fornecimento_Valor (revisão
    12 daquele documento) --- duas entidades que duplicavam o contrato
    de fornecimento contínuo já coberto por este módulo; os campos
    ID_Filial e Forma_Compromisso foram migrados de lá para
    Cad_Gestao_Contrato (seção 2), aplicáveis só na posição Contratante.

-   Fechado nesta Revisão 3: toda a posição Contratante do contrato
    (Mlegate adquirindo/contratando), levantada por Alberto --- régua de
    aprovação própria do contrato (Origem_Tipo=contrato_aquisicao ou
    contrato_venda, também reaproveitada pelo aditivo, seção 3),
    pagamento amarrado a medição e/ou nota fiscal de entrada
    (ID_Nota_Fiscal_Entrada) tanto na apuração periódica (seção 4.1)
    quanto no entregável por etapa de fornecedor
    (Mov_Gestao_Contrato_Entregavel, seção 5.2), e o Status do contrato
    harmonizado com o enum que existia em Compras.

-   Fechado nesta Revisão 4, unificação da medição: Cad_Obra e
    Mov_Obra_Medicao/Mov_Obra_Medicao_Item (Fase 0), que cobriam só
    construção civil e só a posição Contratado, foram aposentados
    naquele documento --- a medição agora vive aqui, em
    Mov_Gestao_Contrato_Medicao/\_Item (seção 4.3), servindo as duas
    posições e qualquer contrato que exija validação formal, não só
    obra.

-   Fechado nesta Revisão 4, novo mecanismo de consumo por evento
    (Mov_Gestao_Contrato_Consumo, seção 4.2), para contratos cujo valor
    é calculado no momento de cada uso --- o exemplo trazido por Alberto
    é frete contratado por km ou por entrega (construído junto com o
    patch em Expedição, Fase 1, revisão 5), mas o mecanismo é genérico e
    serve qualquer outro serviço contratado com o mesmo padrão de uso
    recorrente e tarifado, não só frete.

-   Fechado nesta Revisão 4: ID_Filial (Cad_Gestao_Contrato, seção 2)
    deixa de ser exclusivo da posição Contratante --- passa a valer
    também na posição Contratado, identificando a filial que executa o
    serviço prestado (ex. uma obra de construção civil, ver Cad_Obra,
    Fase 0).

-   Revisão 6 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): Cad_Gestao_Contrato_Item marcado com
    vigência (já era versionado por nova linha) e datas padronizadas
    para Vigencia_Inicio/Vigencia_Fim. A convenção completa (vigência,
    identidade + versão, sucessão de códigos oficiais, competência, CNPJ
    alfanumérico, um campo por informação, saldos guardados de período
    fechado, sequência de fechamento) vive na Fase 0, seções 2 e 10
    (revisão 41).

-   Revisão 7 --- Cad_Gestao_Contrato ganha forma e data de assinatura,
    testemunhas, renovação automática, prazo de aviso de denúncia, foro
    e cláusula arbitral; novas Cad_Gestao_Contrato_Garantia e
    Cad_Gestao_Contrato_Penalidade. Desenho aprovado e histórico do
    bloco nos documentos 20 e 22 do Projeto.

8\. Próximo Passo

*Esta Revisão 4 fecha três pontos levantados por Alberto após a Revisão
3: unificação da medição de obra/construção civil (antes duplicada em
Cad_Obra/Mov_Obra_Medicao, Fase 0, agora aposentados naquele documento)
numa medição só, transversal às duas posições --- nova seção 4.3,
Mov_Gestao_Contrato_Medicao/\_Item, com vínculo opcional a entregável
(seção 5.2); novo mecanismo de consumo por evento (seção 4.2,
Mov_Gestao_Contrato_Consumo) para contratos calculados na hora de cada
uso --- ex. frete por km/entrega, construído junto com o patch em
Expedição (Fase 1, revisão 5) --- acumulando até fechar contra a nota
fiscal do fornecedor; e ID_Filial generalizado para as duas posições
(seção 2). A Revisão 3 permanece válida e não foi alterada nesta rodada,
exceto pelos ajustes pontuais listados nas Notas (seção 7): posição
Contratante do contrato, régua de aprovação própria, e Status
harmonizado com o enum de Compras. A Revisão 2 também permanece válida:
preço por item do contrato (Cad_Gestao_Contrato_Item, seção 2), apuração
periódica por item (seção 4.1) e faturamento por entregável de projeto
próprio (Modelo_Faturamento, seção 5.1). Gestão de Projetos (PPM)
permanece, deliberadamente, fora deste documento, fundida em Produção.
Como sempre neste projeto, a decisão de por onde continuar --- seja um
novo ciclo de comentários sobre esta entrega, seja o próximo módulo da
Fase 6, seja o patch em Expedição (revisão 5) que consome
Mov_Gestao_Contrato_Consumo --- fica a critério de Alberto.*

*Revisão 5, registrada aqui por ser a origem de todo o redesenho: o
período de fechamento deste módulo (ID_Periodo_Referencia, seção 4.1)
deixa de referenciar o período contábil e passa a ser um período PRÓPRIO
do bloco \"gestao_contratos\", consumindo o novo mecanismo transversal
da Fase 0
(Cad_Bloco_Fechamento/Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial,
seção 10, revisão 37) --- o mesmo gate estendido a consumo por evento
(seção 4.2) e medição formal (seção 4.3). A nota da revisão anterior
sobre este ponto (seção 7) foi corrigida: a suposição original, por
analogia a Folha & RH, estava equivocada, e foi exatamente esse ponto
que Alberto corrigiu ao pedir período independente para Contratos ---
pedido que ele próprio generalizou, na sequência, para todos os módulos
do dicionário. Como sempre, o próximo passo --- novo ciclo de
comentários sobre esta entrega, ou o próximo módulo da Fase 6 --- fica a
critério de Alberto.*

*Revisão 6 --- Bloco 1 da validação geral consolidado junto com a Fase 0
(revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 7 --- Bloco 3 consolidado junto com a Fase 0 (revisão 45). O
prazo de guarda dos contratos (10 anos a partir do encerramento, a
confirmar pelo jurídico) está em Cad_Documento_Classe na Fase 0.*
