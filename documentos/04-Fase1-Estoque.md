**ERP --- ESPECIFICAÇÃO TÉCNICA · FASE 1 · MÓDULO 3**

**Estoque**

*Locais de estoque, tipos de movimento parametrizáveis, movimentação,
posição física, custo médio (diário/mensal) e inventário*

*Revisão 18 --- consolidação da revisão 32 do dicionário (documentos 172, 175 e 176, com as respostas de Alberto de 05/11/2026): 2 entidades existentes alteradas; texto e conta contábil do item do inventário (H010) e os quatro motivos novos da reclassificação do K220 (documentos 175 e 176).*

*Revisão 17 --- consolidação da revisão 30 do dicionário (documentos 156, 161, 164 e 168 e a Q138-3, com as respostas de Alberto de 03/11/2026): 3 entidades existentes alteradas; material de terceiros sem valor: Propriedade_Movimento no tipo de movimento, Propriedade e participante proprietário no movimento e no saldo (documento 168, G10; Q168-2).*

*Revisão 16 --- consolidação da revisão 27 do dicionário (documentos 146, 147, 148 e 149, com as respostas de Alberto de 29/10/2026): 1 entidades existentes alteradas; valor consumo_servico na origem do movimento de estoque (documento 148, Q148-12).*

*Revisão 15 --- consolidação da revisão 3 do dicionário (documentos 33 a 46, aprovada por Alberto em 12/10/2026): 1 entidades novas (anexo, seção 17); 3 entidades existentes alteradas. O dicionário passa de 543 para 829 entidades, construída junto com a Fase 0 e os demais módulos alterados.*

*Revisão 14 --- Bloco 3 da validação geral do dicionário (folha e
eSocial, jurídico), construída junto com a revisão 45 da Fase 0 e com o
novo módulo Fase 8 --- Jurídico: Cad_Estoque_Escopo_Usuario aposentada
(seção 13): o recorte de dado por local, produto e classificação passa
para Cad_Usuario_Escopo da Fase 0, com Modulo = estoque, sem mudança da
regra de aplicação.*

*Revisão 13 --- construída junto com a revisão 42 da Fase 0: tipo lógico
\"código (n)\" definido por Alberto --- todo campo que identifica algo
(inscrição, documento, agência, conta, número e série de nota,
matrícula, código oficial) é caractere, nunca numérico: os zeros à
esquerda fazem parte do código, e o padrão pode passar a aceitar letras
ou mudar de tamanho, como aconteceu com o CNPJ alfanumérico. Campos
revistos: Cep, Chave_Acesso, Codigo_Postal_Exterior, Numero_Nota_Fiscal,
Serie_Nota_Fiscal.*

*Revisão 12 --- Bloco 1 (fundação) da validação geral do dicionário
pedida por Alberto, construído junto com a revisão 41 da Fase 0 ---
vigência explícita em todas as tabelas com o trio
Vigencia_Inicio/Vigencia_Fim/Motivo_Vigencia (fim inclusivo e sempre
preenchido, 31/12/9999 quando indefinido) e ID da versão nos cadastros
mestres referenciados; Cad_Local_Estoque_Endereco padronizado (CEP,
campos próprios, sem ID_Estado); Cad_Estoque_Periodo_Custo_Medio
rebaixada a registro histórico; novas Mov_Saldo_Estoque e
Mov_Saldo_Estoque_Valor (saldos guardados por período fechado, definidos
por Alberto); chave primária de Cad_Tipo_Movimento_Estoque_Empresa;
número e série da nota de ajuste desmembrados; competência e chave de
acesso de 44 caracteres (CNPJ alfanumérico).*

*Revisão 11 --- fechamento de estoque por categoria, decorrente da
revisão geral de módulos pedida por Alberto (\"o fechamento_estoque de
estoque tem que fazer os lançamentos por categoria, não da para ser um
pacotão so\"): o lançamento agregado mensal (seção 7) deixa de ser um
valor único e passa a gerar um Mov_Lancamento por Classe/Família de
produto (Cad_Produto_Servico_Dimensao_Valor, Fase 0), resolvido pelo
Motor de Regras; a categoria de produção sai deste agregado (seção 8),
porque passou a se contabilizar sozinha, em tempo real, pelo módulo de
Produção (Fase 1, revisão 11)*

*Revisão 10 --- migração do status de fechamento do Estoque para o motor
genérico da Fase 0 (Cad_Periodo_Fechamento_Filial, bloco \"estoque\"):
Cad_Estoque_Periodo_Custo_Medio aposentado como mecanismo de status;
travamento por competência fechada passa a cobrir TODA movimentação de
estoque, nos dois modos de custo médio*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o
sumário e pressione F9 (ou clique com o botão direito e escolha
\"Atualizar campo\").*

1\. Introdução

Este documento especifica o terceiro módulo da Fase 1 --- Estoque --- no
mesmo formato usado nos módulos anteriores: função e dados juntos,
entidade por entidade, sempre referenciando os motores transversais da
Fase 0 (Cad_Participante, Cad_Filial, Cad_Empresa, Cad_Produto_Servico,
Cad_Motor_Regra) e o módulo de Compras (Mov_Pedido_Item,
Mov_Nota_Fiscal_Entrada_Item, Mov_Pedido_Item_Inspecao) em vez de
redefini-los. A movimentação física de estoque ficou deliberadamente
fora do Fase 0 --- combinado com você desde a revisão original do
dicionário --- para ser tratada aqui.

A Revisão 3 incorporou identificação do participante terceiro,
recebimento sem pedido amarrado direto na nota, e inventário com
múltiplas contagens e nota fiscal de ajuste. A Revisão 4, resultado de
uma autorrevisão que fiz a pedido seu sobre a própria Revisão 3, trouxe:
tipo de movimento por empresa/grupo societário; ajuste de inventário
desmembrado em positivo/negativo; devolução amarrada na saída original;
data/hora em toda movimentação; nota fiscal de ajuste do inventário como
entidade própria; bloqueio de estoque; e controle de acesso por
local/produto/classificação de produto. A Revisão 5 modelou
Cad_Lote_Produto, e o custo médio de produtos controlados passou a poder
ser apurado por lote. As Revisões 6 a 8 fecharam fronteiras com CRM &
Vendas e Produção. A Revisão 9 acrescentou a seção 11, Condição do
Estoque e Resolução de Rejeição (Mov_Estoque_Condicao), pedida por
Alberto a partir de um comentário sobre a inspeção de saída da
Expedição. Continua no mesmo ritmo: comente o que ainda estiver errado
ou faltando, e no final me avise para consolidar.

Esta é a Revisão 10, pedida por Alberto ao confirmar que o bloco de
fechamento genérico da Fase 0 (Cad_Bloco_Fechamento /
Cad_Periodo_Fechamento / Cad_Periodo_Fechamento_Filial, Fase 0 seção 10)
se aplica também ao Estoque --- \"estoque, correto\" --- travando TUDO,
não só o custeio: Cad_Estoque_Periodo_Custo_Medio é aposentado como
mecanismo de status de período (o ponteiro único por filial, usado só no
modo mensal), substituído pelo controle por Filial+competência de
Cad_Periodo_Fechamento_Filial, bloco=\"estoque\";
Mov_Estoque_Fechamento_Custo_Medio continua existindo, agora
referenciando o período genérico em vez do antigo ponteiro; e o
travamento por competência fechada passa a cobrir TODA movimentação de
estoque (entrada, saída, transferência, ajuste), não só a apuração de
custo médio, e nos dois modos (diário e mensal) --- ver seção 5
(Movimentação), seção 7 (Custo Médio) e Notas para o registro explícito
desta extensão de escopo.

Fica FORA desta revisão, por decisão de escopo (não por esquecimento):
controle de número de série individual (equipamentos, ativos); reserva
de estoque para pedido de venda (depende do módulo de CRM & Vendas,
ainda não especificado); requisição interna de consumo como um processo
formal (fica só o gancho de origem do movimento, ver seção 5); e o
controle do que está \"em elaboração\" dentro de uma ordem de produção
--- o material sai do Estoque por um movimento normal e só volta por
outro movimento normal quando o produto fica pronto; o que acontece
entre esses dois pontos é assunto de um futuro Módulo de Produção (ver
seção 8).

2\. Locais de Estoque

Uma filial (Cad_Filial, Fase 0) pode ter mais de um local físico de
estoque --- um depósito e uma loja, por exemplo --- e é o local, não a
filial, que carrega saldo.

Cad_Local_Estoque

Um local físico onde produtos ficam guardados ou em trânsito.

*Vigência: não --- é um cadastro simples de local; o que varia no tempo
é o saldo nele, nunca armazenado (ver seção 5).*

  ------------------------------ -------------------- ----------------------------------------
  **Campo**                      **Tipo lógico**      **Descrição / regra**

  **ID_Local**                   *identificador*      ---

  **ID_Filial**                  *referência          ---
                                 (Cad_Filial)*        

  **Nome_Local**                 *texto*              ---

  **Descricao**                  *texto, opcional*    Adicionado nesta revisão: o Nome_Local
                                                      sozinho pode não ser suficiente para
                                                      identificar o local, ex.: um depósito
                                                      terceirizado (\"Openbox --- Galpão 3\").
                                                      O endereço estruturado, quando existir,
                                                      fica em Cad_Local_Estoque_Endereco
                                                      (abaixo) --- este campo é só um
                                                      complemento textual livre.

  **Tipo**                       *enumeração          \"transito\" cobre mercadoria em
                                 {deposito, loja,     deslocamento entre locais/filiais.
                                 producao, transito,  \"terceiros\" adicionado na revisão
                                 terceiros}*          anterior, para armazenagem em local de
                                                      um operador logístico (ex.: Openbox) ---
                                                      nesse caso o endereço em
                                                      Cad_Local_Estoque_Endereco normalmente é
                                                      obrigatório. \"producao\" é mantido como
                                                      redundância útil para consulta --- um
                                                      local físico dentro da área fabril que
                                                      ainda guarda material disponível, não
                                                      confundir com o material já consumido
                                                      dentro de uma ordem de produção, que
                                                      fica fora do escopo deste módulo (ver
                                                      seção 8).

  **ID_Participante_Terceiro**   *referência          Adicionado nesta revisão: obrigatório na
                                 (Cad_Participante,   prática quando Tipo=terceiros ---
                                 opcional)*           identifica QUEM (o operador logístico)
                                                      está de posse do bem, informação exigida
                                                      no SPED para mercadoria em poder de
                                                      terceiros. Reaproveita o cadastro único
                                                      de participante do Fase 0, sem duplicar
                                                      dado do terceiro aqui.

  **Status**                     *enumeração {ativo,  ---
                                 inativo}*            
  ------------------------------ -------------------- ----------------------------------------

Cad_Local_Estoque_Endereco

Endereço estruturado de um local de estoque --- mesmo conjunto de campos
de Cad_Participante_Endereco (Fase 0, revisão 41), aplicado por local.
Padronizado na revisão 12: CEP, número, complemento e bairro em campos
próprios, estado derivado do município e campos de texto para endereço
no exterior.

*Vigência: sim --- o endereço pode mudar (o operador logístico troca de
galpão, por exemplo) independente do resto do cadastro do local.*

  ---------------------------- ---------------------- ----------------------------------------
  **Campo**                    **Tipo lógico**        **Descrição / regra**

  **ID_Endereco**              *identificador*        ---

  **ID_Local**                 *referência            ---
                               (Cad_Local_Estoque)    
                               --- identidade*        

  **Cep**                      *código (8)*           Adicionado na revisão 12: obrigatório
                                                      para endereço no Brasil. Só dígitos, sem
                                                      máscara.

  **ID_Tipo_Logradouro**       *referência            Tabela 20 do eSocial.
                               (Cad_Classe_Sistema,   
                               Fase 0, domínio =      
                               tipo_logradouro,       
                               opcional)*             

  **Logradouro**               *texto*                Só o nome do logradouro --- número,
                                                      complemento e bairro têm campo próprio.

  **Numero**                   *texto*                Aceita \"S/N\".

  **Complemento**              *texto, opcional*      ---

  **Bairro**                   *texto, opcional*      ---

  **ID_Municipio**             *referência            Obrigatório no Brasil; o estado sai do
                               (Cad_Municipio, Fase   município (ID_Estado removido na revisão
                               0, opcional)*          12).

  **ID_Pais**                  *referência (Cad_Pais, ---
                               Fase 0)*               

  **Cidade_Exterior**          *texto, opcional*      Só fora do Brasil.

  **Regiao_Exterior**          *texto, opcional*      Estado, província ou região no exterior.

  **Codigo_Postal_Exterior**   *código (até 12),      ---
                               opcional*              

  **Vigencia_Inicio**          *data*                 Primeiro dia em que esta versão vale.

  **Vigencia_Fim**             *data*                 Último dia em que esta versão vale
                                                      (inclusive). Sempre preenchida:
                                                      31/12/9999 quando o fim é indefinido
                                                      (versão vigente) --- convenção da Fase
                                                      0, seção 2.

  **Motivo_Vigencia**          *texto, opcional*      Por que esta versão foi criada.
  ---------------------------- ---------------------- ----------------------------------------

3\. Recebimento Físico e Conferência

O módulo de Compras já trata a fidelidade fiscal/financeira da nota
(nunca recalcular valores), a divergência acumulada entre nota e pedido,
e a inspeção de QUALIDADE quando exigida. O que falta, e é função deste
módulo, é a contagem física em si --- quanto de fato chegou e foi
guardado, e em qual local.

Mov_Recebimento_Fisico

O registro da contagem física de uma mercadoria recebida --- pode haver
mais de um recebimento por item, no caso de entrega parcelada em
diversas notas.

*Vigência: não.*

  ------------------------------- -------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                  **Descrição / regra**

  **ID_Recebimento**              *identificador*                  ---

  **ID_Pedido_Item**              *referência (Mov_Pedido_Item,    A linha do pedido sendo recebida
                                  Fase 1 --- Compras, opcional)*   fisicamente, quando existir. Passou a
                                                                   ser opcional nesta revisão.

  **ID_Nota_Item**                *referência                      Adicionado nesta revisão: amarração
                                  (Mov_Nota_Fiscal_Entrada_Item,   direta com a nota fiscal, para o caso de
                                  Fase 1 --- Compras, opcional)*   nota SEM pedido (já suportado em Compras
                                                                   --- pequenas despesas, cartão
                                                                   corporativo) cujo item ainda assim
                                                                   precisa entrar fisicamente no estoque.
                                                                   Pelo menos um entre ID_Pedido_Item e
                                                                   ID_Nota_Item precisa estar preenchido
                                                                   --- todo recebimento fica sempre
                                                                   rastreável até o documento de origem.

  **Data_Hora_Recebimento**       *data/hora*                      Passou de \"data\" para \"data/hora\" na
                                                                   Revisão 4 --- necessário para sequenciar
                                                                   o movimento de entrada automático gerado
                                                                   por este recebimento (seção 5).

  **Quantidade_Recebida**         *número*                         A contagem física real --- pode divergir
                                                                   da nota fiscal (essa divergência
                                                                   fiscal/financeira já é tratada em
                                                                   Compras; aqui é especificamente a
                                                                   contagem física que confirma ou não o
                                                                   que a nota diz).

  **ID_Local_Estoque**            *referência (Cad_Local_Estoque)* Onde a mercadoria foi de fato guardada.

  **ID_Participante_Recebedor**   *referência (Cad_Participante)*  Quem contou/recebeu --- mesmo cadastro
                                                                   único do Fase 0.
  ------------------------------- -------------------------------- ----------------------------------------

*Comportamento de aplicação: a confirmação de um Mov_Recebimento_Fisico
dispara automaticamente um Mov_Estoque_Movimento de entrada (seção 5) no
Local de Estoque informado --- é assim que a mercadoria de fato entra no
saldo. Quando há pedido, combinado com a inspeção de qualidade
(Mov_Pedido_Item_Inspecao, Fase 1 --- Compras), fecha a condição
completa de encerramento de uma linha de pedido: Mov_Pedido_Item só
conta como efetivamente recebida quando (a) existe
Mov_Recebimento_Fisico com Quantidade_Recebida compatível, e (b) o item
não requer inspeção, ou requer e tem Resultado=aprovado. Quando não há
pedido (ID_Nota_Item preenchido, ID_Pedido_Item vazio), não existe linha
de pedido para encerrar --- o recebimento só serve para dar entrada
física no estoque, rastreada até a nota.*

4\. Tipos de Movimento

Adicionado na Revisão 3: cada empresa define seus próprios tipos de
movimento de estoque, e cada tipo pode afetar o saldo e ser valorizado
de uma forma diferente. Os exemplos abaixo --- envio para produção,
entrada por compras, as três devoluções, entrada por bonificação --- são
ilustrativos, não uma lista fechada do sistema. O que é fixo é a
estrutura: todo tipo tem uma Direção (o efeito estrutural sobre o saldo)
e um Método de Valorização (de onde vem o valor do movimento). Nesta
revisão, o tipo de movimento também passou a valer por empresa --- a
empresa onde é criado, por padrão, podendo ser estendido a outras do
mesmo grupo societário (ver Cad_Tipo_Movimento_Estoque_Empresa, abaixo).

Cad_Tipo_Movimento_Estoque

Cadastro parametrizável --- cada empresa cria os tipos de movimento que
fizer sentido para sua operação.

*Vigência: não --- parametrização de configuração, não histórico de
valor.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Tipo_Movimento** | *identificador* | --- |
| **ID_Empresa_Criadora** | *referência (Cad_Empresa, Fase 0)* | Adicionado nesta revisão: a empresa onde este tipo foi criado --- dona por padrão. Um tipo pode valer só para ela ou ser estendido a outras empresas do mesmo grupo societário, via Cad_Tipo_Movimento_Estoque_Empresa, abaixo. |
| **Nome** | *texto* | Ex.: \"Envio para Produção\", \"Entrada por Compras\", \"Devolução de Produção\", \"Devolução de Compra\", \"Devolução de Cliente\", \"Entrada por Bonificação\" --- nomes livres, definidos pela empresa. |
| **Direcao** | *enumeração {entrada, saida, transferencia, ajuste_positivo, ajuste_negativo}* | O efeito estrutural sobre o saldo --- mesmo enum que era fixo em Mov_Estoque_Movimento na Revisão 1, agora parametrizado por tipo em vez de fixo no cabeçalho do movimento: entrada soma; saída subtrai; transferência subtrai de um local/posição e soma em outro. Alterado nesta revisão: o valor único \"ajuste\" foi desmembrado em ajuste_positivo (sobra apurada em inventário, seção 10) e ajuste_negativo (falta apurada) --- cada um pode ter Método de Valorização próprio, já que a natureza econômica de um ganho e de uma perda/quebra costuma ser diferente. |
| **Metodo_Valoracao** | *enumeração {custo_medio, valor_documento_origem, valor_movimento_origem, informado_manualmente, sem_valor}* | Define de onde vem o valor do movimento. \"custo_medio\": a saída é valorizada pelo custo médio vigente da filial (ex.: Envio para Produção). \"valor_documento_origem\": o valor vem de um documento externo, via ID_Valor_Referencia (ex.: Entrada por Compras → Mov_Nota_Fiscal_Entrada_Item.Valor_Total; Entrada por Bonificação → Mov_Nota_Fiscal_Entrada_Item.Valor_Credito_Tributario, não o Valor_Total do item). \"valor_movimento_origem\": o valor é o mesmo pelo qual o material tinha saído/entrado antes, via ID_Valor_Referencia apontando para o movimento original --- cobre as três devoluções (Produção, Compra, Cliente) com a MESMA regra, não três regras distintas: nenhuma delas recalcula, todas reusam o valor do movimento de origem. \"informado_manualmente\": o usuário digita o valor no lançamento --- cobre casos residuais de ajuste avulso. Revisão 30 (documento 168, seção 3.10, G10; Q167-3, opção a): "sem_valor": o movimento não tem valor (Valor_Total é zero) e não entra no custo médio, no saldo de valor nem na contabilidade; só para os tipos de material de terceiros. |
| **Propriedade_Movimento** | *enumeração {proprio, de_terceiros_em_poder_da_empresa}* | Revisão 30 (documento 168, seção 3.10, G10; D-N460 e D-N461): De quem é o material que o tipo movimenta. A carga dos tipos existentes é proprio. A remessa da Mlegate para terceiros continua sendo transferência para um local Tipo = terceiros (que já tem o participante do operador), e o saldo dela é derivado do local, sem tipo próprio. Tipos novos de carga (nomes livres): "Entrada de material de terceiros (remessa para industrialização)", "Consumo de material de terceiros" e "Retorno de material de terceiros". |

*Revisão 30 --- campos novos: Propriedade_Movimento; valores de enumeração novos: Metodo_Valoracao (+sem_valor).*

Cad_Tipo_Movimento_Estoque_Empresa

Adicionado nesta revisão: lista as empresas autorizadas a usar um tipo
de movimento, além da criadora --- relação N:N. Ao criar um tipo, o
sistema insere automaticamente a linha da empresa criadora
(Cad_Tipo_Movimento_Estoque.ID_Empresa_Criadora); estender a outras
empresas do mesmo grupo societário (Cad_Grupo_Societario, Fase 0) é
adicionar novas linhas aqui.

*Vigência: sim --- uma empresa pode ganhar ou perder acesso a um tipo de
movimento ao longo do tempo, sem apagar o histórico de movimentos já
lançados com ele.*

  ------------------------------- ------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                 **Descrição / regra**

  **ID_Tipo_Movimento_Empresa**   *identificador*                 Adicionado na revisão 12 (chave primária
                                                                  declarada). Único por
                                                                  (ID_Tipo_Movimento, ID_Empresa,
                                                                  Vigencia_Inicio).

  **ID_Tipo_Movimento**           *referência                     ---
                                  (Cad_Tipo_Movimento_Estoque)*   

  **ID_Empresa**                  *referência (Cad_Empresa, Fase  ---
                                  0)*                             

  **Vigencia_Inicio**             *data*                          Primeiro dia em que esta versão vale.

  **Vigencia_Fim**                *data*                          Último dia em que esta versão vale
                                                                  (inclusive). Sempre preenchida:
                                                                  31/12/9999 quando o fim é indefinido
                                                                  (versão vigente) --- convenção da Fase
                                                                  0, seção 2.

  **Motivo_Vigencia**             *texto, opcional*               Por que esta versão foi criada.
  ------------------------------- ------------------------------- ----------------------------------------

*Comportamento de aplicação (não é um campo novo de dados): o sistema
aprende a sugerir o ID_Tipo_Movimento a partir da chave de entrada da
nota fiscal --- mesmo mecanismo já usado para sugerir o CFOP de entrada
em Compras: critério = ID_CFOP_Entrada + ID_CST_IBS_CBS de
Mov_Nota_Fiscal_Entrada_Item (podendo considerar também
fornecedor/produto/destinação), resultado = ID_Tipo_Movimento sugerido,
via Cad_Motor_Regra (Fase 0). Como o tipo já traz consigo Direcao e
Metodo_Valoracao, essa única sugestão resolve ao mesmo tempo \"qual
movimento gerar\" e \"como valorizá-lo\". Toda confirmação ou correção
do usuário realimenta a regra, mesmo comportamento de aprendizado já
usado no CFOP.*

5\. Movimentação de Estoque

Mesma filosofia já usada na Contabilidade (Fase 0): não existe uma
tabela de saldo de estoque. O saldo de um produto, num local (e, quando
aplicável, numa posição dentro do local --- ver seção 6, e num lote ---
ver Cad_Lote_Produto, abaixo), num momento, é sempre a soma das
quantidades de Mov_Estoque_Movimento_Item até aquele momento,
considerando a Direção do Tipo de Movimento de cada um. Adicionado nesta
revisão: quando o produto tem controle por lote, esse mesmo saldo é
sempre apurável também por produto+local(+posição)+lote --- a mesma
soma, só filtrada também por ID_Lote. Uma tabela de saldo materializada,
se for necessária por performance, é decisão de implementação --- não
deste dicionário --- mas precisa carregar lote como dimensão quando
aplicável.

Mov_Estoque_Movimento

O cabeçalho de um evento de movimentação --- o que aconteceu, de que
tipo e de onde veio.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Movimento** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | --- |
| **Data_Hora_Movimento** | *data/hora* | Passou de \"data\" para \"data/hora\" nesta revisão --- necessário para sequenciar corretamente múltiplos movimentos no mesmo dia, crítico no modo de custo médio diário (ver seção 7). |
| **ID_Tipo_Movimento** | *referência (Cad_Tipo_Movimento_Estoque)* | Substituiu o enum fixo \"Tipo_Movimento\" da Revisão 1 --- Direção e Método de Valorização agora vêm do cadastro do tipo (seção 4), não são mais definidos aqui. |
| **Origem_Tipo** | *enumeração {recebimento_fisico, requisicao_interna, transferencia, inventario, movimento_estoque, pedido_venda, venda_avulsa, ordem_producao, outro, consumo_servico}* | Referência genérica --- mesmo padrão já usado em Mov_Aprovacao_Instancia.Origem_Tipo/ID_Origem (Fase 0). \"requisicao_interna\" é só o gancho de origem --- o processo formal de requisição (quem pediu, aprovação) ainda não foi modelado (ver Notas). \"movimento_estoque\" foi adicionado na Revisão 4: usado nas devoluções (Produção, Compra, Cliente), que precisam estar amarradas na saída original sendo revertida, não só num documento externo --- o próprio Mov_Estoque_Movimento vira sua própria origem (self-reference). \"pedido_venda\" foi adicionado na revisão anterior, pedido pela especificação do módulo Fase 1 CRM & Vendas: a baixa física gerada pela nota fiscal de saída referencia o item do pedido de venda sendo atendido, não a nota em si --- a nota pode agrupar itens de mais de um pedido. \"venda_avulsa\" foi adicionado na revisão 7, pedido pela mesma especificação: cobre a venda balcão/avulsa, emitida sem pedido prévio --- não existe item de pedido para referenciar, então a baixa aponta direto para o item da nota fiscal de saída. \"ordem_producao\" foi adicionado nesta revisão (8), pedido pela especificação do módulo Fase 1 Produção: cobre tanto o ENVIO de matéria-prima/componente para uma ordem de produção (saída, Tipo_Movimento \"Envio para Produção\") quanto o RETORNO do produto acabado (entrada, Tipo_Movimento \"Entrada de Produção\") --- os dois pontos de fronteira que a seção 8 deste documento já reservava para um futuro módulo de Produção, agora especificado. Revisão 27 (documento 148, Q148-12): consumo_servico é o consumo de estoque incluso no preço de um serviço (por exemplo, a refeição incluída na diária do hotel); ID_Origem aponta o item da nota que cobra o serviço, e o consumo vira custo daquele item. A nota traz só o valor do serviço, sem rateio. |
| **ID_Origem** | *identificador do registro de origem* | Conforme Origem_Tipo --- ex.: o ID_Recebimento quando Origem_Tipo=recebimento_fisico, o ID_Movimento da saída original sendo devolvida quando Origem_Tipo=movimento_estoque, o ID_Item do pedido de venda (Mov_Pedido_Venda_Item, Fase 1 --- CRM & Vendas) quando Origem_Tipo=pedido_venda, o ID_Item da nota fiscal de saída (Mov_Nota_Fiscal_Saida_Item, Fase 1 --- CRM & Vendas) quando Origem_Tipo=venda_avulsa, ou o ID_Item de Mov_Ordem_Producao_Item (Fase 1 --- Produção) quando Origem_Tipo=ordem_producao. |

*Revisão 27 --- valores de enumeração novos: Origem_Tipo (+consumo_servico).*

Mov_Estoque_Movimento_Item

Uma linha do movimento --- o produto, a quantidade, o valor, os locais e
as posições envolvidas.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Movimento** | *referência (Mov_Estoque_Movimento)* | --- |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico)* | --- |
| **ID_Local_Estoque_Origem** | *referência (Cad_Local_Estoque, opcional)* | Vazio para entrada pura (nada saiu de um local --- veio de fora). |
| **ID_Local_Estoque_Destino** | *referência (Cad_Local_Estoque, opcional)* | Vazio para saída pura (nada foi guardado --- saiu de vez). Numa transferência, origem e destino são preenchidos juntos (ver seção 9). |
| **ID_Posicao_Estoque_Origem** | *referência (Cad_Posicao_Estoque, opcional)* | Adicionado nesta revisão: posição física dentro do local de origem, mais granular que o local sozinho (ver seção 6). |
| **ID_Posicao_Estoque_Destino** | *referência (Cad_Posicao_Estoque, opcional)* | Idem, para o local de destino. |
| **Quantidade** | *número, opcional* | Passou a ser opcional nesta revisão: um movimento pode ser só de valor, sem quantidade --- ex.: entrada de custo de importação que chegou depois da nota fiscal de entrada já lançada. Quando preenchida, é sempre positiva --- o efeito sobre o saldo vem da Direção do Tipo de Movimento, nunca do sinal aqui, exceto o caso de bonificação abaixo, em que a quantidade é positiva mas o Valor_Total é negativo. |
| **Valor_Total** | *número* | Substituiu Custo_Unitario (Revisão 1). Campo principal, sempre presente e não recalculado a partir de Quantidade × custo unitário --- mesmo princípio de fidelidade ao valor real já usado em Compras --- EXCETO na saída valorizada por Metodo_Valoracao=custo_medio, em que não existe documento externo e o valor É genuinamente calculado: Quantidade × custo médio vigente (seção 7). Pode ser negativo mesmo numa entrada --- caso de bonificação, ver exemplo abaixo. |
| **ID_Valor_Referencia_Tipo** | *enumeração {nota_fiscal_entrada_item, movimento_estoque_item, ordem_producao_custo_apurado, nenhum}* | Adicionado nesta revisão: de onde vem o Valor_Total, quando Metodo_Valoracao=valor_documento_origem ou valor_movimento_origem --- mesmo padrão de referência genérica já usado em Mov_Aprovacao_Instancia (Fase 0). \"ordem_producao_custo_apurado\" foi adicionado na revisão 8, pedido pela especificação do módulo Fase 1 Produção: a entrada de produto acabado (Tipo_Movimento \"Entrada de Produção\", Metodo_Valoracao=valor_documento_origem) não tem nota fiscal de origem nem reusa um movimento anterior --- o valor vem do custo total apurado daquela ordem (materiais diretos/indiretos, mão de obra direta/indireta, serviços de terceiros, industrialização em terceiros), calculado pelo próprio módulo de Produção. |
| **ID_Valor_Referencia** | *identificador do registro de referência, opcional* | Ex.: o ID_Item de Mov_Nota_Fiscal_Entrada_Item (compra: Valor_Total; bonificação: Valor_Credito_Tributario --- Fase 1, Compras), o ID_Item de um Mov_Estoque_Movimento_Item anterior (as três devoluções, que reusam o valor do movimento de origem), ou o ID_Custo_Apurado de Mov_Ordem_Producao_Custo_Apurado (Fase 1 --- Produção) quando ID_Valor_Referencia_Tipo=ordem_producao_custo_apurado. |
| **ID_Lote** | *referência (Cad_Lote_Produto, opcional)* | Controle de lote --- Cad_Lote_Produto modelado nesta revisão (abaixo). Vazio para produtos sem controle de lote; preenchido quando o produto exige rastreabilidade por lote, tipicamente um Produto_Controlado (Fase 0). Participa do saldo derivado (ver acima) e do custo médio por lote (seção 7). |
| **Propriedade** | *enumeração {proprio, de_terceiros_em_poder_da_empresa}* | Revisão 30 (documento 168, seção 3.10, G10; D-N460 e D-N461): Copiado do tipo de movimento no lançamento, e guardado para que a mudança futura do tipo não reescreva o passado. |
| **ID_Participante_Proprietario** | *referência (Cad_Participante), opcional* | Revisão 30 (documento 168, seção 3.10, G10; D-N460 e D-N461): O dono do material. Obrigatório (aviso) quando Propriedade não é proprio. |

*Revisão 30 --- campos novos: Propriedade, ID_Participante_Proprietario.*

*Comportamento de aplicação --- travamento por competência fechada
(adicionado na Revisão 10): a confirmação de qualquer
Mov_Estoque_Movimento --- entrada, saída, transferência ou ajuste
(positivo ou negativo), qualquer que seja o Metodo_Valoracao do Tipo de
Movimento envolvido, e independente de Cad_Empresa.Modo_Custo_Medio ser
diário ou mensal --- é bloqueada quando a competência de
Data_Hora_Movimento, para a Filial do movimento, estiver fechada em
Cad_Periodo_Fechamento_Filial (Fase 0, seção 10), bloco=\"estoque\".
Este é o mecanismo genérico de fechamento da Fase 0 substituindo e
ampliando o antigo controle de Cad_Estoque_Periodo_Custo_Medio
(aposentado --- ver seção 7): antes, só a apuração de custo médio no
modo mensal ficava protegida por um período fechado; agora, qualquer
movimentação física de estoque, nos dois modos, é travada por
competência fechada. Diferente de Compras, este bloco não valida
pendência alguma no fechamento --- ver Notas para o registro explícito
desta extensão de escopo.*

*Exemplo --- bonificação/amostra grátis: a empresa recebe um produto sem
cobrança, mas o emitente da nota pagou imposto sobre a saída da
mercadoria; quem recebe pode se creditar (beneficiar) desse imposto.
Nesse caso, Quantidade é positiva (o produto entrou fisicamente) e
Valor_Total é negativo --- só o crédito de imposto entra em valor, não o
valor de face do produto --- com
ID_Valor_Referencia_Tipo=nota_fiscal_entrada_item e ID_Valor_Referencia
apontando para o Valor_Credito_Tributario da linha da nota (Fase 1 ---
Compras), não para o Valor_Total do item.*

Cad_Lote_Produto

Adicionado nesta revisão: um lote específico de um produto ---
necessário para rastreabilidade e, quando o produto é controlado, para
custo médio apurado por lote (seção 7), não só por produto+filial.

*Vigência: não --- assumido estável; um lote não muda de identidade ao
longo do tempo.*

  ------------------------ ------------------------ ----------------------------------------
  **Campo**                **Tipo lógico**          **Descrição / regra**

  **ID_Lote**              *identificador*          ---

  **ID_Produto_Servico**   *referência              ---
                           (Cad_Produto_Servico)*   

  **Numero_Lote**          *texto*                  Identificação do lote, normalmente a
                                                    mesma que consta na nota
                                                    fiscal/documento de origem.

  **Data_Fabricacao**      *data, opcional*         ---

  **Data_Validade**        *data, opcional*         ---
  ------------------------ ------------------------ ----------------------------------------

*Nem todo produto usa controle por lote --- fica a critério de cada
empresa/produto, tipicamente produtos perecíveis, farmacêuticos, ou os
Produto_Controlado do Fase 0, que costumam ter exigência regulatória de
rastreabilidade. Quando um produto usa lote, todo
Mov_Estoque_Movimento_Item que o movimenta preenche ID_Lote (acima) ---
inclusive o Mov_Estoque_Custo_Medio correspondente (seção 7).*

6\. Posição Física dentro do Local

Adicionado nesta revisão: além do local (seção 2), muitas operações
precisam saber ONDE dentro do local o item está --- útil para localizar
fisicamente o item, ex.: filial X, estante Z, prateleira W.

Cad_Posicao_Estoque

Uma posição física específica dentro de um local de estoque.

*Vigência: não --- assumido estável; ver Notas se for necessário
histórico de mudança de identificação.*

  ---------------------- ---------------------- ----------------------------------------
  **Campo**              **Tipo lógico**        **Descrição / regra**

  **ID_Posicao**         *identificador*        ---

  **ID_Local_Estoque**   *referência            ---
                         (Cad_Local_Estoque)*   

  **Identificacao**      *texto*                Ex.: \"Estante Z / Prateleira W\".
  ---------------------- ---------------------- ----------------------------------------

*Livre/ocupada nunca é um campo armazenado --- é sempre derivado do
saldo (soma de Mov_Estoque_Movimento_Item apontando para aquela
posição): saldo zero é posição livre, saldo diferente de zero é posição
ocupada, mesma filosofia de saldo nunca armazenado já usada na seção 5.
Uma posição NÃO é fixa para um produto específico --- pode ser ocupada
por produtos diferentes ao longo do tempo (ex.: um produto personalizado
para um cliente ocupa uma posição enquanto durar aquele saldo; quando
esvazia, a posição fica livre para qualquer outro produto). Um mesmo
produto também pode estar em mais de uma posição simultaneamente --- um
saldo por posição, não um saldo único por local.*

*Transferência entre posições do mesmo local usa o mesmo
Mov_Estoque_Movimento (Tipo com Direcao=transferencia), com o MESMO
ID_Local_Estoque nos dois lados do item e
ID_Posicao_Estoque_Origem/Destino diferentes. Não há recálculo de custo
médio nesse caso --- nem o produto nem a quantidade total no local
mudam, só a posição física dentro dele.*

7\. Custo Médio

Assumi o método de custo médio ponderado móvel (o mais comum na prática
brasileira) --- se a Mlegate ou seus clientes usam outro método
(PEPS/FIFO, custo padrão), a estrutura muda bastante: FIFO, por exemplo,
exigiria rastrear camadas de custo por entrada, não uma média única (ver
Notas). Nesta revisão, além do método de cálculo, a CADÊNCIA da apuração
(diário ou mensal) também passou a ser parametrizável, por empresa.

Mov_Estoque_Custo_Medio

O custo médio vigente de um produto numa filial, recalculado a cada
movimento que afeta o valor do estoque.

*Vigência: sim --- histórico de custo ao longo do tempo, necessário para
apurar custo de mercadoria vendida (CMV) por período (ver Notas).*

  -------------------------- ------------------------ --------------------------------------------------
  **Campo**                  **Tipo lógico**          **Descrição / regra**

  **ID_Custo**               *identificador*          ---

  **ID_Produto_Servico**     *referência              ---
                             (Cad_Produto_Servico)*   

  **ID_Filial**              *referência              O custo médio é apurado por filial, não por local
                             (Cad_Filial)*            de estoque individual --- todos os locais de uma
                                                      mesma filial compartilham o mesmo custo médio.

  **ID_Lote**                *referência              Vazio para produtos sem controle de lote --- custo
                             (Cad_Lote_Produto,       médio único por produto+filial, como antes.
                             opcional)*               Preenchido quando o produto é controlado
                                                      (Cad_Produto_Servico.Produto_Controlado=true, Fase
                                                      0) E a empresa optou por descer a apuração até o
                                                      lote
                                                      (Cad_Empresa.Controla_Custo_Medio_Por_Lote=true,
                                                      adicionado na Fase 0 revisão 13): a apuração passa
                                                      a ser por produto+filial+lote, cada lote com seu
                                                      próprio custo médio. Quando a empresa mantém essa
                                                      flag falsa, este campo fica sempre vazio, mesmo
                                                      para produto com controle de lote --- a apuração
                                                      permanece por produto+filial.

  **Data_Hora_Referencia**   *data/hora*              Passou de \"data\" para \"data/hora\" nesta
                                                      revisão --- necessário para saber a sequência
                                                      exata de recálculo, sobretudo no modo diário.

  **Custo_Medio**            *número*                 Fórmula generalizada nesta revisão para cobrir
                                                      movimento só de valor e movimento de bonificação:
                                                      novo Custo_Medio = (saldo de quantidade anterior ×
                                                      custo médio anterior + Valor_Total do movimento) ÷
                                                      (saldo de quantidade anterior + Quantidade do
                                                      movimento, ou 0 quando Quantidade vier vazia).

  **Vigencia_Inicio**        *data*                   Primeiro dia em que esta versão vale.

  **Vigencia_Fim**           *data*                   Último dia em que esta versão vale (inclusive).
                                                      Sempre preenchida: 31/12/9999 quando o fim é
                                                      indefinido (versão vigente) --- convenção da Fase
                                                      0, seção 2.

  **Motivo_Vigencia**        *texto, opcional*        Por que esta versão foi criada.
  -------------------------- ------------------------ --------------------------------------------------

*Modo_Custo_Medio (Cad_Empresa, Fase 0) decide a cadência, por empresa:
no modo \"diario\", cada movimento recalcula o médio no momento, na
sequência de Data_Hora_Movimento --- e isso já é imutável por
construção: um movimento passado nunca é reaberto por um movimento
futuro, porque o cálculo incremental só olha para trás, nunca para
frente. No modo \"mensal\", o custo do período fica provisório até o
fechamento (abaixo); no fechamento, o médio final do período é apurado e
os Valor_Total das saídas por custo_medio ocorridas dentro daquele mesmo
período --- inclusive envio para produção --- são ajustados
retroativamente, uma única vez. Depois de fechado, o período é imutável:
um fechamento posterior nunca reabre nem ajusta um período anterior já
fechado, e o que já foi requisitado num período fechado não muda por
causa de um fechamento de período seguinte.*

*Custo médio por lote: quando ID_Lote está preenchido (produto
controlado E Cad_Empresa.Controla_Custo_Medio_Por_Lote=true), a fórmula
de Custo_Medio é a mesma, mas aplicada dentro do lote --- o saldo de
quantidade anterior e o custo médio anterior usados na fórmula são os do
próprio lote (produto+filial+lote), não do produto como um todo. Uma
saída daquele lote específico (Mov_Estoque_Movimento_Item.ID_Lote
preenchido) busca o custo médio vigente do lote, não a média geral do
produto na filial. Para produtos sem controle de lote, ou quando a
empresa mantém a flag falsa mesmo para produto controlado, nada muda: o
cálculo continua por produto+filial, como antes.*

*Cad_Estoque_Periodo_Custo_Medio --- APOSENTADO na Revisão 10 como
mecanismo de status (substituído por
Cad_Periodo_Fechamento/Cad_Periodo_Fechamento_Filial, Fase 0, bloco
\"estoque\") e retirado da lista de entidades na Revisão 12, para não
aparecer no modelo entidade-relacional como entidade viva: era um
ponteiro único do período mensal aberto por filial (ID_Filial,
Periodo_Aberto), atualizado no lugar a cada fechamento. Mantido aqui só
como registro histórico.*

*Cad_Estoque_Periodo_Custo_Medio, acima, foi APOSENTADO como mecanismo
de status nesta revisão (10) --- Alberto confirmou (\"estoque,
correto\") que o bloco de fechamento genérico da Fase 0
(Cad_Bloco_Fechamento / Cad_Periodo_Fechamento /
Cad_Periodo_Fechamento_Filial, Fase 0 seção 10) se aplica também ao
Estoque, travando TUDO, não só o custeio. O status de aberto/fechado por
Filial+competência passa a viver em Cad_Periodo_Fechamento_Filial (Fase
0), bloco=\"estoque\" --- fail-closed, mesma regra da Fase 0: nenhuma
linha para uma combinação Filial+competência é tratada como aberta por
omissão. Diferente do antigo ponteiro único, que só existia (e só
protegia, na prática, a apuração de custo médio) no modo mensal, o novo
mecanismo vale nos dois modos de custo médio --- ver seção 5
(Movimentação) para o comportamento de travamento, agora aplicado a toda
movimentação de estoque, e Notas para o registro explícito desta
extensão de escopo. Mov_Estoque_Fechamento_Custo_Medio (abaixo) continua
existindo --- é só o evento/detalhe do fechamento do custo médio em si
(o cálculo do médio final, o ajuste retroativo das saídas do período),
não mais a fonte do status de aberto/fechado.*

Mov_Estoque_Fechamento_Custo_Medio

O evento de fechamento do período mensal de custo médio, numa filial ---
continua existindo sem mudança de papel nesta revisão (10): é só o
detalhe do cálculo do fechamento, nunca foi a fonte do status de
aberto/fechado.

*Vigência: não --- é um evento histórico, não um cadastro; cada
fechamento é um novo registro.*

  -------------------------- --------------------------------- ----------------------------------------
  **Campo**                  **Tipo lógico**                   **Descrição / regra**

  **ID_Fechamento**          *identificador*                   ---

  **ID_Filial**              *referência (Cad_Filial)*         Mantido por conveniência de consulta
                                                               direta --- deve sempre coincidir com o
                                                               ID_Filial de ID_Periodo_Filial (abaixo).

  **ID_Periodo_Filial**      *referência                       Adicionado nesta revisão (10),
                             (Cad_Periodo_Fechamento_Filial,   substituindo a referência implícita ao
                             Fase 0)*                          antigo Cad_Estoque_Periodo_Custo_Medio
                                                               (aposentado --- ver acima): aponta para
                                                               a linha Filial+competência,
                                                               bloco=\"estoque\", que este evento
                                                               fechou. É isto, e não mais o ponteiro
                                                               único, que determina a que
                                                               período/filial o fechamento se refere.

  **Periodo_Fechado**        *competência*                     Ano/Mês da competência fechada. Até a
                                                               Revisão 9, era o período que estava
                                                               aberto em
                                                               Cad_Estoque_Periodo_Custo_Medio; a
                                                               partir desta revisão (10), é um espelho
                                                               de leitura direta do período genérico
                                                               (alcançável via ID_Periodo_Filial →
                                                               Cad_Periodo_Fechamento, Fase 0), mantido
                                                               aqui para evitar um JOIN a mais em telas
                                                               e relatórios. Tipo lógico competência
                                                               desde a revisão 12.

  **Data_Hora_Fechamento**   *data/hora*                       ---
  -------------------------- --------------------------------- ----------------------------------------

Saldos guardados de período fechado --- revisão 12, definição de Alberto
(Fase 0, seção 2.4): no fechamento do bloco estoque de cada filial e
competência, o saldo passa a ser gravado, porque o período fechado não
muda e, com anos de uso, recalcular a partir de todo o histórico de
movimentos pesa diretamente na performance. O saldo do período aberto
continua calculado: último saldo fechado + movimentos do período até a
data. Se o período for reaberto (em cascata para frente, Fase 0 seção
10), os saldos daquela competência e das seguintes são refeitos nos
novos fechamentos, em ordem cronológica.

Mov_Saldo_Estoque

Nova na revisão 12. A quantidade ao fim da competência, no menor nível
físico usado nas consultas --- local, posição e lote ---, gravada no
fechamento. Nunca digitada nem editada.

*Vigência: não --- retrato de um período fechado.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Saldo_Estoque** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial, Fase 0)* | --- |
| **ID_Local_Estoque** | *referência (Cad_Local_Estoque)* | --- |
| **ID_Posicao_Estoque** | *referência (Cad_Posicao_Estoque, opcional)* | Vazio quando o local não usa posição. |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico, Fase 0)* | --- |
| **ID_Lote** | *referência (Cad_Lote_Produto, opcional)* | Vazio para produto sem controle de lote. |
| **Competencia** | *competência* | Único por (ID_Local_Estoque, ID_Posicao_Estoque, ID_Produto_Servico, ID_Lote, Competencia) --- índice principal. |
| **ID_Fechamento** | *referência (Mov_Estoque_Fechamento_Custo_Medio)* | O fechamento que gerou este saldo. |
| **Quantidade_Inicial** | *número* | --- |
| **Quantidade_Entradas** | *número* | --- |
| **Quantidade_Saidas** | *número* | --- |
| **Quantidade_Final** | *número* | --- |
| **Data_Hora_Geracao** | *data/hora* | Quando foi gravado, ou regravado depois de uma reabertura. |
| **Propriedade** | *enumeração {proprio, de_terceiros_em_poder_da_empresa, da_empresa_em_poder_de_terceiros}* | Novo na revisão 3 (documento 37). IND_EST do K200 e IND_PROP do H010; mesma lista de Mov_Inventario_Item.Propriedade (documento 33). O material do encomendante (de terceiros em poder) entra no saldo sem valorização. Revisão 30 (documento 168, seção 3.10, G10; Q168-2): o saldo passa a ser único por local, posição, produto, lote, competência, propriedade e participante; o K200 e o H010 saem do saldo por propriedade, e o custo médio (Mov_Estoque_Custo_Medio) ignora tudo o que não é proprio. O material do encomendante em poder da Mlegate é controlado no estoque de terceiros, sem valor, como movimento de propriedade de terceiros (corrige o documento 06, seção 8.2). |
| **ID_Participante_Proprietario** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 37). COD_PART do K200: dono ou possuidor do item; obrigatório quando a propriedade não é própria em poder da empresa. Revisão 30 (documento 168, Q168-2): faz parte da unicidade do saldo, junto com Propriedade. |

*Revisão 3 --- campos novos (documento 37): Propriedade, ID_Participante_Proprietario.*

*Revisão 30 --- campos alterados: Propriedade, ID_Participante_Proprietario.*

Mov_Saldo_Estoque_Valor

Nova na revisão 12. O valor do estoque ao fim da competência, no nível
em que o custo médio é apurado --- filial, produto e lote. Separado da
quantidade por local porque o custo médio é da filial, e é este valor
que tem de bater com a conta de estoque na contabilidade. Alimenta os
Blocos H (inventário) e K do SPED.

*Vigência: não --- retrato de um período fechado.*

  ---------------------------- --------------------------------------- --------------------------------------------
  **Campo**                    **Tipo lógico**                         **Descrição / regra**

  **ID_Saldo_Estoque_Valor**   *identificador*                         ---

  **ID_Filial**                *referência (Cad_Filial, Fase 0)*       ---

  **ID_Produto_Servico**       *referência (Cad_Produto_Servico, Fase  ---
                               0)*                                     

  **ID_Lote**                  *referência (Cad_Lote_Produto,          Preenchido só quando
                               opcional)*                              Cad_Empresa.Controla_Custo_Medio_Por_Lote.

  **Competencia**              *competência*                           Único por (ID_Filial, ID_Produto_Servico,
                                                                       ID_Lote, Competencia).

  **ID_Fechamento**            *referência                             ---
                               (Mov_Estoque_Fechamento_Custo_Medio)*   

  **Quantidade_Final**         *número*                                Soma das quantidades finais dos locais da
                                                                       filial.

  **Valor_Inicial**            *número*                                ---

  **Valor_Entradas**           *número*                                ---

  **Valor_Saidas**             *número*                                ---

  **Valor_Final**              *número*                                Guardado como está no fechamento, sem
                                                                       recalcular Quantidade × Custo.

  **Custo_Medio_Final**        *número*                                O custo médio vigente no fechamento
                                                                       (Mov_Estoque_Custo_Medio).

  **Data_Hora_Geracao**        *data/hora*                             ---
  ---------------------------- --------------------------------------- --------------------------------------------

*Comportamento de aplicação (não são campos novos, exceto onde
indicado): ao fechar, o sistema (a) apura o médio final do período
recém-fechado; (b) ajusta o Valor_Total das saídas por custo_medio
ocorridas dentro daquele período (ver seção 8, com a exceção da revisão
11 abaixo); (c) marca Cad_Periodo_Fechamento_Filial.Status=fechado (Fase
0) para a Filial+competência, bloco=\"estoque\" --- substituindo, nesta
revisão (10), o antigo avanço de
Cad_Estoque_Periodo_Custo_Medio.Periodo_Aberto; e (d) gera um
Mov_Lote_Lancamento (Fase 0, Origem_Tipo=fechamento_estoque,
ID_Origem=ID_Fechamento) com os lançamentos contábeis decorrentes --- é
assim, e só assim, que o fechamento do estoque alimenta a Contabilidade.
Este período de custo médio é um controle próprio do Estoque
(bloco=\"estoque\"), independente do período contábil
(bloco=\"contabilidade\" --- ambos hoje instâncias do mesmo mecanismo
genérico, Cad_Periodo_Fechamento, Fase 0) --- os dois nunca se misturam,
mesmo quando ambos forem mensais na prática.*

*Revisão 11 --- fechamento por categoria, decorrente da revisão geral de
módulos pedida por Alberto (\"o fechamento_estoque de estoque tem que
fazer os lançamentos por categoria, não da para ser um pacotão so\"): o
item (d) acima deixa de gerar um único Mov_Lancamento pelo valor total
da filial --- passa a gerar um Mov_Lancamento por Classe/Família de
produto (Cad_Produto_Servico_Dimensao_Valor, Fase 0, nível de
classificação já usado para tabela de preço/comissão), cada um na sua
própria conta contábil, resolvida pelo mesmo Motor de Regras (Fase 0) já
usado no resto do dicionário --- matéria-prima numa conta, produto
acabado noutra, mercadoria para revenda noutra, e assim por diante,
nunca somadas num lançamento único. Quando um produto não tem nenhum
valor classificado no nível de Classe/Família configurado pela empresa,
cai numa categoria \"outro\", resolvida pela mesma regra, para nenhum
saldo ficar sem conta. Revisão 11, segundo tema: a categoria de produção
(Origem_Tipo=ordem_producao, movimentos \"Envio para Produção\" e
\"Entrada de Produção\", seção 8) é EXCLUÍDA deste agregado mensal ---
desde a revisão correspondente do módulo de Produção (Fase 1, seção 7),
esses dois movimentos passaram a gerar seu próprio lançamento em tempo
real, evento a evento (Origem_Tipo=producao_consumo_material e
producao_entrada_produto_acabado, Fase 0); mantê-los também no
fechamento agregado duplicaria o lançamento. Todas as demais categorias
(matéria-prima ainda não requisitada, produto acabado, mercadoria de
revenda, entre outras) continuam pelo fechamento mensal, só que agora
quebradas por Classe/Família em vez de um valor único.*

8\. Escopo: Produção e Produto em Elaboração

O envio de matéria-prima para uma ordem de produção é, do ponto de vista
deste módulo, uma saída normal (ex.: Tipo_Movimento \"Envio para
Produção\", Metodo_Valoracao=custo_medio, Origem_Tipo=ordem_producao ---
seção 5) --- a partir do momento em que sai, o material deixa de ser
saldo disponível no Estoque. O que acontece com ele dentro da ordem de
produção (estágios de elaboração, consumo, sobra, rateio de custo
indireto) fica INTEIRAMENTE fora do escopo deste módulo --- é assunto do
módulo de Produção, especificado nesta revisão (8) como Fase 1, Módulo
8. O Estoque não tenta modelar um saldo de \"produto em elaboração\"
como se fosse mais uma posição ou local: seria um saldo que este módulo
não tem como enxergar nem controlar corretamente.

Quando o produto acabado sai da produção, ele volta ao Estoque por uma
entrada normal (ex.: Tipo_Movimento \"Entrada de Produção\",
Metodo_Valoracao=valor_documento_origem,
ID_Valor_Referencia_Tipo=ordem_producao_custo_apurado --- seção 5) e
passa a ser saldo disponível como qualquer outro Cad_Produto_Servico ---
podendo, inclusive, ser consumido de novo como matéria-prima de um
terceiro produto, sem nenhuma distinção estrutural entre
\"matéria-prima\" e \"produto acabado\" no cadastro. Isso reforça, não
muda, o desenho unificado de Cad_Produto_Servico já usado desde o Fase
0.

*Confirmado nesta revisão (8): o valor que entra no Estoque por este
caminho é o custo TOTAL apurado da ordem (soma de todos os componentes
--- materiais, mão de obra, serviços de terceiros, industrialização em
terceiros), calculado pelo módulo de Produção. A quebra desse valor POR
TIPO fica preservada na origem, em Mov_Ordem_Producao_Custo_Apurado
(Fase 1 --- Produção, por ordem/lote) --- este módulo, por construção
(custo médio ponderado móvel, seção 7), não preserva prospectivamente
uma quebra por tipo dentro do próprio saldo médio: a partir do momento
em que o valor entra aqui, ele se mistura ao custo médio do
produto+filial(+lote) como um número único, junto com entradas de outras
origens. Fica como ponto de atenção explícito (ver Notas) se a Mlegate
precisar consultar a quebra por tipo de um saldo em estoque já
misturado, e não só da produção de origem.*

Cad_Local_Estoque.Tipo=producao (seção 2) é mantido como redundância
útil para consulta --- um local físico dentro da área fabril que ainda
guarda material disponível, não o material já consumido dentro de uma
ordem de produção.

*Revisão 11 --- os dois movimentos deste fluxo (\"Envio para Produção\"
e \"Entrada de Produção\") passaram a gerar lançamento contábil em TEMPO
REAL, evento a evento, por decisão de Alberto (\"sim dispara lançamentos
contábeis\"): a saída, no momento em que acontece; a entrada, no momento
da conclusão da ordem, já pela quebra por tipo de
Mov_Ordem_Producao_Custo_Apurado, não mais só pelo valor total
misturado. O desenho completo (contas de Estoque em Elaboração por
categoria,
Origem_Tipo=producao_consumo_material/producao_entrada_produto_acabado)
vive no módulo de Produção (Fase 1, seção 7); a única mudança PARA ESTE
módulo é que os dois movimentos passam a ficar de fora do fechamento
mensal agregado (seção 7) --- já contabilizados sozinhos, não precisam
(e não podem, sob risco de duplicar) entrar de novo no agregado por
Classe/Família.*

*Estabilidade de custo do que já saiu para produção: a regra de
fechamento de período (seção 7) garante que, no modo diário, o valor de
saída já registrado nunca é tocado por movimentos futuros; no modo
mensal, o valor só pode ser ajustado uma vez, no fechamento do próprio
período em que a saída ocorreu --- nunca depois de fechado, nem por um
fechamento de um período posterior.*

9\. Transferência entre Locais e Filiais

Transferência entre POSIÇÕES do mesmo local está na seção 6. Esta seção
trata de transferência entre LOCAIS (mesma filial) e entre FILIAIS
diferentes.

Transferência entre locais da MESMA filial usa só Mov_Estoque_Movimento
(Tipo com Direcao=transferencia, com ID_Local_Estoque_Origem e
ID_Local_Estoque_Destino preenchidos na mesma linha) --- sem nenhuma
estrutura adicional.

*Transferência entre FILIAIS diferentes provavelmente exige nota fiscal
de transferência --- uma operação fiscal própria, sem venda envolvida
--- fora do escopo desta revisão, mesma decisão já tomada para a nota
fiscal de saída (módulo de CRM & Vendas, ainda não especificado). Fica
como ponto de atenção para quando esse módulo for tratado; a estrutura
de Mov_Estoque_Movimento já comporta ID_Filial no cabeçalho e locais de
filiais diferentes nos dois lados do item, então a extensão futura deve
ser pequena.*

10\. Inventário e Ajuste

A contagem física periódica (inventário) compara o saldo apurado pelos
movimentos com a contagem real, e qualquer diferença vira um ajuste ---
que, por sua vez, tem implicação fiscal e precisa de nota fiscal
própria.

Mov_Inventario

O cabeçalho de um processo de contagem física.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Inventario** | *identificador* | --- |
| **ID_Local_Estoque** | *referência (Cad_Local_Estoque)* | --- |
| **Data_Hora_Inventario** | *data/hora* | Passou de \"data\" para \"data/hora\" na Revisão 4, mesmo motivo das demais datas do módulo. |
| **Status** | *enumeração {aberto, encerrado}* | \"encerrado\" dispara os ajustes (ver abaixo). Enquanto Status=aberto, um Mov_Estoque_Bloqueio (seção 12) normalmente cobre o local, impedindo movimentação concorrente durante a contagem. |
| **Numero_Contagens_Planejadas** | *número* | Quantas contagens o gestor do inventário decidiu fazer (ex.: até 3, sendo a 3ª um desempate). |
| **Numero_Contagens_Necessarias_Bater** | *número* | Quantas contagens, entre as feitas, precisam coincidir entre si para o resultado ser aceito (ex.: 2 contagens que precisam bater) --- pode ser igual ou menor que Numero_Contagens_Planejadas. |
| **ID_Motivo_Inventario** | *referência (Cad_Classe_Sistema, domínio = motivo_inventario)* | Novo na revisão 3 (documento 33). Motivo do inventário (MOT_INV do registro H005 da EFD ICMS/IPI): final do período, mudança de tributação, baixa cadastral, mudança de regime de pagamento, determinação do fisco ou controle de mercadoria sujeita à ST. |

*Revisão 3 --- campos novos (documento 33): ID_Motivo_Inventario.*

Mov_Inventario_Nota_Fiscal_Ajuste

O(s) documento(s) fiscal(is) que sustentam o ajuste de estoque apurado
neste inventário --- passou a ser entidade própria na Revisão 4: um
mesmo inventário pode ter sobra (entrada) e falta (saída) ao mesmo
tempo, e cada uma costuma exigir documento fiscal separado na prática
brasileira.

*Vigência: não.*

  ------------------------ ------------------- ----------------------------------------
  **Campo**                **Tipo lógico**     **Descrição / regra**

  **ID_Nota_Ajuste**       *identificador*     ---

  **ID_Inventario**        *referência         ---
                           (Mov_Inventario)*   

  **Numero_Nota_Fiscal**   *código (até 15)*   Desmembrado na revisão 12.

  **Serie_Nota_Fiscal**    *código (até 3)*    ---

  **Data_Nota_Fiscal**     *data*              ---

  **Chave_Acesso**         *código (44),       Adicionado nesta revisão (7), princípio
                           opcional*           geral pedido por Alberto: toda
                                               referência a nota fiscal no dicionário
                                               precisa carregar a chave de acesso da
                                               NFe.

  **Tipo**                 *enumeração         Sobra apurada vira entrada; falta
                           {entrada, saida}*   apurada vira saída. Não modelei uma
                                               entidade cheia de nota fiscal de
                                               ajuste/saída aqui --- o módulo Fase 1
                                               CRM & Vendas já modelou
                                               Mov_Nota_Fiscal_Saida separadamente;
                                               fica só o dado básico do documento por
                                               ora (ver Notas).
  ------------------------ ------------------- ----------------------------------------

Mov_Inventario_Item

Uma linha contada --- o produto e a quantidade que os movimentos
indicavam no momento da contagem.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Item** | *identificador* | --- |
| **ID_Inventario** | *referência (Mov_Inventario)* | --- |
| **ID_Produto_Servico** | *referência (Cad_Produto_Servico)* | --- |
| **Quantidade_Sistema** | *número* | O saldo derivado dos movimentos (seção 5) no momento da contagem --- guardado aqui como registro histórico da divergência, já que o saldo em si nunca é armazenado. |
| **Propriedade** | *enumeração {proprio, de_terceiros_em_poder_da_empresa, da_empresa_em_poder_de_terceiros}* | Novo na revisão 3 (documento 33). Indicador de propriedade e de posse do item (IND_PROP do H010). |
| **ID_Participante_Proprietario** | *referência (Cad_Participante, opcional)* | Novo na revisão 3 (documento 33). O proprietário ou possuidor do item quando não é próprio em poder da empresa (COD_PART). |
| **Valor_Unitario** | *número* | Novo na revisão 3 (documento 33). Valor unitário do item no inventário (VL_UNIT). |
| **Valor_Item** | *número* | Novo na revisão 3 (documento 33). Valor do item (VL_ITEM = quantidade x valor unitário). |
| **Valor_Item_Ir** | *número, opcional* | Novo na revisão 3 (documento 33). Valor do item para efeito do Imposto de Renda (VL_ITEM_IR). |
| **Texto_Complementar** | *texto, opcional* | Revisão 32 (documento 175, seção 8.2; D-N480; Q175-1 a Q175-9 pela recomendação): TXT_COMPL do H010. |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil), opcional* | Revisão 32 (documento 175, seção 8.2; D-N480; Q175-1 a Q175-9 pela recomendação): COD_CTA do H010: a conta contábil do item. Sem o campo o dado só se deduzia do lançamento do fechamento de estoque. |

*Revisão 3 --- campos novos (documento 33): Propriedade, ID_Participante_Proprietario, Valor_Unitario, Valor_Item, Valor_Item_Ir.*

*Revisão 32 --- campos novos: Texto_Complementar, ID_Conta_Contabil.*

Mov_Inventario_Contagem

Uma contagem física individual de um item --- substituiu
Quantidade_Contada (Revisão 2, um valor único por item) para suportar
múltiplas contagens.

*Vigência: não.*

  ------------------------------ ------------------------ ---------------------------------------------
  **Campo**                      **Tipo lógico**          **Descrição / regra**

  **ID_Contagem**                *identificador*          ---

  **ID_Item**                    *referência              ---
                                 (Mov_Inventario_Item)*   

  **Numero_Contagem**            *número*                 1ª, 2ª, 3ª contagem, etc. --- até o limite de
                                                          Mov_Inventario.Numero_Contagens_Planejadas.

  **Quantidade_Contada**         *número*                 A contagem física real, nesta rodada
                                                          específica.

  **ID_Participante_Contador**   *referência              Quem contou nesta rodada --- mesmo cadastro
                                 (Cad_Participante)*      único do Fase 0.

  **Data_Hora_Contagem**         *data/hora*              Passou de \"data\" para \"data/hora\" na
                                                          Revisão 4, mesmo motivo das demais datas do
                                                          módulo.
  ------------------------------ ------------------------ ---------------------------------------------

*Comportamento de aplicação (não são campos novos): a quantidade final
de um item só é aceita para o ajuste quando o número de contagens
exigido em Mov_Inventario.Numero_Contagens_Necessarias_Bater coincidir
entre si (ex.: 1ª e 2ª contagem batem); se divergirem, uma nova contagem
é necessária, até o limite de Numero_Contagens_Planejadas. Ao encerrar o
inventário (Status=encerrado), cada item cuja quantidade aceita for
diferente de Quantidade_Sistema gera um Mov_Estoque_Movimento ---
Direcao=ajuste_positivo quando a contagem for maior que o sistema
(sobra), ajuste_negativo quando for menor (falta),
Origem_Tipo=inventario --- que reconcilia o saldo derivado dos
movimentos com a contagem física real, respaldado pela nota fiscal de
ajuste correspondente em Mov_Inventario_Nota_Fiscal_Ajuste (Tipo=entrada
para sobra, Tipo=saida para falta). O encerramento também encerra o
Mov_Estoque_Bloqueio associado (seção 12), liberando o local para
movimentação normal.*

11\. Condição do Estoque e Resolução de Rejeição

Novo nesta revisão (9), pedido por Alberto a partir de um comentário
sobre a inspeção de saída da Expedição: quando um produto é rejeitado
numa inspeção de qualidade, ele precisa de uma CLASSIFICAÇÃO formal ---
condição --- e de um caminho de resolução: reparar (volta a disponível)
ou descartar (fica num saldo separado, para destruição ou venda como
defeituoso). Alberto confirmou que isso não é específico da Expedição
--- um item PRODUZIDO também pode ser avaliado pela própria Produção ---
por isso este motor mora aqui, no Estoque, transversal a qualquer módulo
que precise classificar uma quantidade de saldo, no mesmo espírito dos
demais motores transversais deste dicionário.

Mov_Estoque_Condicao

A classificação de condição de uma quantidade de saldo de um produto ---
disponível, rejeitada, em reparo, ou descartada.

*Vigência: não --- evento; a condição vigente de um
produto+lote(+posição) é sempre a Condicao do registro mais recente para
aquela combinação, nunca reescrita.*

  ------------------------------- ------------------------------- ----------------------------------------
  **Campo**                       **Tipo lógico**                 **Descrição / regra**

  **ID_Condicao**                 *identificador*                 ---

  **ID_Produto_Servico**          *referência                     ---
                                  (Cad_Produto_Servico)*          

  **ID_Lote**                     *referência (Cad_Lote_Produto,  Preenchido quando o produto usa controle
                                  opcional)*                      de lote (seção 5); quando não usa, a
                                                                  classificação vale por produto+posição
                                                                  (abaixo), sem nível de lote.

  **ID_Posicao_Estoque**          *referência                     Refinamento físico --- em qual posição a
                                  (Cad_Posicao_Estoque,           quantidade classificada está (ou para
                                  opcional)*                      onde vai, no caso de descarte; ver
                                                                  comportamento de aplicação, abaixo).

  **Quantidade**                  *número*                        A fração do saldo sendo classificada ---
                                                                  pode ser menor que o saldo total do
                                                                  lote/posição (ex.: só 2 das 10 unidades
                                                                  recebidas foram reprovadas na inspeção).

  **Condicao**                    *enumeração {rejeitado,         O novo estado. Um produto sem nenhum
                                  em_reparo, disponivel,          registro aqui é, por definição,
                                  descarte}*                      disponível --- mesmo princípio de nunca
                                                                  guardar o padrão já usado em todo o
                                                                  dicionário.

  **Origem_Tipo**                 *enumeração                     Referência genérica de quem disparou
                                  {mov_expedicao_item_inspecao,   esta classificação --- mesmo padrão já
                                  mov_pedido_item_inspecao,       usado em
                                  outro}*                         Mov_Estoque_Bloqueio.Origem_Tipo (seção
                                                                  12) e Mov_Aprovacao_Instancia (Fase 0).
                                                                  \"outro\" cobre qualquer avaliação
                                                                  manual, inclusive a Produção reavaliando
                                                                  um item fabricado (Alberto: \"se for um
                                                                  produto produzido a produção pode
                                                                  avaliar\") --- sem inspeção dedicada
                                                                  modelada ainda naquele módulo (Fase 1
                                                                  --- Produção).

  **ID_Origem**                   *identificador do registro de   O ID_Inspecao de
                                  origem, opcional*               Mov_Expedicao_Item_Inspecao (Fase 1 ---
                                                                  Expedição) ou de
                                                                  Mov_Pedido_Item_Inspecao (Fase 1 ---
                                                                  Compras), conforme Origem_Tipo; vazio
                                                                  quando Origem_Tipo=outro e não há
                                                                  registro estruturado de origem.

  **Data_Hora**                   *data/hora*                     ---

  **ID_Participante_Avaliador**   *referência (Cad_Participante)* Quem avaliou/decidiu --- mesmo cadastro
                                                                  único do Fase 0.

  **Observacao**                  *texto, opcional*               ---
  ------------------------------- ------------------------------- ----------------------------------------

*Comportamento de aplicação --- classificação: uma reprovação em
Mov_Expedicao_Item_Inspecao (Resultado=reprovado, Fase 1 --- Expedição,
seção 3) ou em Mov_Pedido_Item_Inspecao (Resultado=reprovado, Fase 1 ---
Compras, seção 7) dispara automaticamente um Mov_Estoque_Condicao com
Condicao=rejeitado, Origem_Tipo apontando para a inspeção de origem.*

*Comportamento de aplicação --- resolução: a partir de
Condicao=rejeitado, um novo Mov_Estoque_Condicao decide o caminho.
Reparar: Condicao=em_reparo (o item some do saldo disponível enquanto
aguarda) e, concluído o reparo, mais um novo registro com
Condicao=disponivel devolve o item ao saldo normal --- sem exigir
necessariamente um Mov_Estoque_Movimento físico, já que o reparo pode
acontecer na própria posição. Descartar: Condicao=descarte, sempre
acompanhado de um Mov_Estoque_Movimento (Direcao=transferencia, seção 5)
para uma Cad_Posicao_Estoque/Cad_Local_Estoque dedicado a descarte,
segregando fisicamente o saldo descartado do saldo disponível normal ---
mesmo padrão já usado para a posição de separação da Expedição: nenhum
tipo estrutural novo em Cad_Posicao_Estoque, só uma posição como outra
qualquer, dedicada por convenção de uso.*

*Comportamento de aplicação --- saldo disponível e venda de descarte: o
saldo \"disponível\" de um produto (usado, por exemplo, pela tela de
disponibilidade da Expedição, Fase 1 --- Expedição seção 2) passa a
excluir a quantidade cuja Condicao vigente não seja disponivel. Alberto
confirmou que um item em Condicao=descarte ainda pode ser vendido --- é
uma venda normal, sem tratamento fiscal específico --- mas, como a
quantidade não está classificada como disponível, a tela de separação da
Expedição precisa CONSULTAR explicitamente a Condicao vigente do
lote/posição ao processar essa saída, para o operador saber que está
lidando com um item fora da condição normal, em vez de uma venda cega.
Quando o item vendido é uma máquina produzida (Cad_Equipamento, Fase 1
--- Produção, seção 9) originada de uma venda a partir de
Condicao=descarte, a máquina nasce sem garantia --- ver aquele
documento.*

12\. Bloqueio de Estoque

Adicionado nesta revisão: durante um inventário, uma inspeção, ou outra
obrigação que exija que o saldo fique estável por um período, o local
(ou um produto específico dentro dele) pode ser bloqueado para outras
movimentações --- evitando que um movimento concorrente desalinhe a
contagem ou verificação em andamento.

Mov_Estoque_Bloqueio

Um período em que um local (ou um produto específico dentro de um local)
fica impedido de receber novas movimentações.

*Vigência: não --- é um evento de bloqueio, não um cadastro; cada
bloqueio é um novo registro.*

  ------------------------ ----------------------- --------------------------------------------------
  **Campo**                **Tipo lógico**         **Descrição / regra**

  **ID_Bloqueio**          *identificador*         ---

  **ID_Local_Estoque**     *referência             Preenchido para bloquear o local inteiro.
                           (Cad_Local_Estoque,     
                           opcional)*              

  **ID_Produto_Servico**   *referência             Preenchido para bloquear só este produto dentro do
                           (Cad_Produto_Servico,   local --- os dois campos podem ser combinados
                           opcional)*              (local + produto) ou usados isoladamente.

  **Origem_Tipo**          *enumeração             O motivo do bloqueio --- referência genérica,
                           {inventario, inspecao,  mesmo padrão já usado neste módulo (seção 5) e no
                           outro}*                 Fase 0
                                                   (Mov_Aprovacao_Instancia.Origem_Tipo/ID_Origem).

  **ID_Origem**            *identificador do       Ex.: o ID_Inventario, quando
                           registro de origem*     Origem_Tipo=inventario.

  **Data_Hora_Inicio**     *data/hora*             ---

  **Data_Hora_Fim**        *data/hora, opcional*   Vazio enquanto o bloqueio está ativo; preenchido
                                                   ao encerrar.

  **Status**               *enumeração {ativo,     ---
                           encerrado}*             
  ------------------------ ----------------------- --------------------------------------------------

*Comportamento de aplicação: enquanto existir um Mov_Estoque_Bloqueio
com Status=ativo cobrindo um local (ou um produto dentro dele), o
sistema impede a confirmação de novos Mov_Estoque_Movimento que afetem
aquele saldo. O encerramento do inventário (seção 10) ou da inspeção
correspondente encerra automaticamente o bloqueio associado --- a
estrutura não impede, por si só, dois bloqueios simultâneos sobre o
mesmo local/produto por motivos diferentes (ver Notas).*

13\. Acesso e Restrição por Usuário

Adicionado nesta revisão: usuários do Estoque precisam de acesso
limitado ao(s) local(is) sob sua responsabilidade, e por vezes também
por tipo/classificação de produto --- ex.: um usuário do estoque geral
não deveria enxergar o estoque de produtos químicos; um produto de uso
restrito (ex.: nitrocelulose) só deveria ser acessível a quem tem
permissão explícita. Este controle é um filtro ADICIONAL sobre
Cad_Permissao (Fase 0), que já cobre módulo + ação --- aqui é o RECORTE
de dado dentro do módulo Estoque que aquele usuário pode ver/operar.

*Cad_Estoque_Escopo_Usuario --- APOSENTADA na revisão 14 (Bloco 3).
Restringia o recorte de dado do Estoque por local, produto ou
classificação de produto. Foi substituída por Cad_Usuario_Escopo (Fase
0, seção 13), com Modulo = estoque: Tipo_Escopo vira ID_Tipo_Restricao
(local_estoque, produto, classificacao_produto) e ID_Escopo vira
ID_Valor_Restricao. A regra de combinação é a mesma que este módulo já
aplicava, agora generalizada: a AUSÊNCIA de linha de um tipo significa
acesso pleno naquele tipo, e a PRESENÇA restringe aos valores listados.*

*Comportamento de aplicação: a AUSÊNCIA de qualquer registro para um
usuário, num Tipo_Escopo, significa acesso pleno (sem restrição) naquele
tipo --- ex.: um usuário sem nenhuma linha Tipo_Escopo=local_estoque
enxerga todos os locais. A PRESENÇA de ao menos um registro restringe o
usuário aos valores explicitamente listados naquele tipo.
Cad_Produto_Servico.Produto_Controlado (Fase 0, ver Notas) inverte esse
padrão para um produto específico: fechado por padrão --- só quem tem
uma linha explícita cobrindo aquele produto (Tipo_Escopo=produto ou
classificacao_produto) o enxerga, mesmo que o usuário não tenha nenhuma
outra restrição de produto.*

14\. Como este módulo se conecta com a Fase 0, Compras, Expedição e
Produção

Referência rápida do que este módulo consome --- nunca redescrito aqui,
só referenciado por chave estrangeira.

  ---------------------------------------- --------------------------------------------------------- ------------------------------------------------------------------------
  **Entidade referenciada**                **Como este módulo usa**                                  **Observação**

  **Cad_Produto_Servico**                  O item movimentado, recebido, custeado, inventariado e    *Mesmo cadastro único do Fase 0*
                                           (adicionado nesta revisão) eventualmente marcado como     
                                           Produto_Controlado para restrição de acesso.              

  **Cad_Filial**                           Cada Local de Estoque pertence a uma filial; o custo      *---*
                                           médio e o fechamento de período são apurados por filial.  

  **Cad_Empresa**                          Modo_Custo_Medio decide a cadência (diário/mensal) da     *---*
                                           apuração do custo médio; e, adicionado nesta revisão,     
                                           Cad_Tipo_Movimento_Estoque.ID_Empresa_Criadora e          
                                           Cad_Tipo_Movimento_Estoque_Empresa referenciam quais      
                                           empresas do grupo societário podem usar cada tipo de      
                                           movimento.                                                

  **Cad_Participante**                     Quem recebe/conta fisicamente a mercadoria, e quem é o    *Mesmo cadastro único do Fase 0*
                                           terceiro depositário em                                   
                                           Cad_Local_Estoque.ID_Participante_Terceiro.               

  **Cad_Usuario**                          Adicionado nesta revisão: Cad_Usuario_Escopo referencia o *Fase 0*
                                           usuário cujo acesso está sendo restrito por               
                                           local/produto/classificação.                              

  **Cad_Produto_Servico_Dimensao_Valor**   Adicionado nesta revisão: alvo de                         *Fase 0*
                                           Cad_Usuario_Escopo.ID_Valor_Restricao quando              
                                           ID_Tipo_Restricao=classificacao_produto.                  

  **Cad_Motor_Regra**                      Sugere o Tipo de Movimento a partir do CFOP/CST da nota,  *Mesmo mecanismo já usado para o CFOP de entrada em Compras*
                                           aprendendo com a confirmação do usuário.                  

  **Cad_Bloco_Fechamento /                 Adicionado nesta revisão (10): trava a confirmação de     *Fase 0, seção 10, mecanismo transversal (revisão 37)*
  Cad_Periodo_Fechamento /                 qualquer Mov_Estoque_Movimento datado numa competência    
  Cad_Periodo_Fechamento_Filial**          fechada da Filial, bloco=\"estoque\" --- substitui        
                                           Cad_Estoque_Periodo_Custo_Medio (aposentado) como fonte   
                                           do status de aberto/fechado.                              

  **Mov_Lote_Lancamento / Mov_Lancamento** O fechamento do período de custo médio mensal gera        *Origem_Tipo=fechamento_estoque, ID_Origem=ID_Fechamento; produção ---
                                           lançamento contábil --- revisão 11: um Mov_Lancamento por Origem_Tipo=producao_consumo_material/producao_entrada_produto_acabado
                                           Classe/Família (Cad_Produto_Servico_Dimensao_Valor, Fase  (Fase 1 --- Produção)*
                                           0), não mais um valor único; a categoria de produção sai  
                                           deste agregado, contabilizada à parte em tempo real pelo  
                                           módulo de Produção.                                       

  **Mov_Pedido_Item (Compras)**            A linha do pedido sendo recebida fisicamente, quando      *Opcional*
                                           existir.                                                  

  **Mov_Nota_Fiscal_Entrada_Item           Fonte do Valor_Total (entrada por compra) ou do           *Fidelidade ao valor real --- mesmo princípio de Compras*
  (Compras)**                              Valor_Credito_Tributario (entrada por bonificação), via   
                                           ID_Valor_Referencia; e referenciada diretamente por       
                                           Mov_Recebimento_Fisico.ID_Nota_Item quando não há pedido. 

  **Mov_Pedido_Item_Inspecao (Compras)**   Combinado com Mov_Recebimento_Fisico, fecha o             *Nenhuma estrutura nova --- só a combinação das duas condições*
                                           encerramento da linha do pedido --- só se aplica quando   
                                           há pedido. Adicionado nesta revisão (9):                  
                                           Resultado=reprovado dispara Mov_Estoque_Condicao (seção   
                                           11), Origem_Tipo=mov_pedido_item_inspecao.                

  **Mov_Expedicao_Item_Inspecao            Adicionado nesta revisão (9): Resultado=reprovado dispara *Fase 1 --- Expedição, revisão 4, novo*
  (Expedição)**                            Mov_Estoque_Condicao (seção 11),                          
                                           Origem_Tipo=mov_expedicao_item_inspecao.                  

  **Mov_Pedido_Venda_Item (CRM & Vendas)** A linha do pedido de venda sendo baixada fisicamente pela *Origem_Tipo=pedido_venda, ID_Origem=ID_Item*
                                           nota fiscal de saída.                                     

  **Mov_Nota_Fiscal_Saida_Item (CRM &      Adicionado nesta revisão (7): a baixa física de uma venda *Origem_Tipo=venda_avulsa, ID_Origem=ID_Item*
  Vendas)**                                avulsa/balcão, sem pedido --- aponta direto para o item   
                                           da nota.                                                  

  **Cad_Empresa                            Adicionado na Fase 0 revisão 13: decide se o custo médio  *Fase 0*
  (Controla_Custo_Medio_Por_Lote)**        por lote (seção 7) desce até o lote ou fica só por        
                                           produto+filial.                                           

  **Mov_Ordem_Producao_Item /              Adicionado nesta revisão (8): origem do envio de material *Fase 1, construído em revisão anterior*
  Mov_Ordem_Producao_Custo_Apurado         para produção (Origem_Tipo=ordem_producao, saída) e da    
  (Produção)**                             entrada de produto acabado, valorizada pelo custo apurado 
                                           da ordem                                                  
                                           (ID_Valor_Referencia_Tipo=ordem_producao_custo_apurado,   
                                           entrada) --- seções 5 e 8. Uma avaliação de condição      
                                           feita pela própria Produção sobre um item fabricado       
                                           (seção 11) usa Mov_Estoque_Condicao.Origem_Tipo=outro,    
                                           apontando ID_Origem para o item da ordem --- sem inspeção 
                                           dedicada modelada ainda naquele módulo.                   
  ---------------------------------------- --------------------------------------------------------- ------------------------------------------------------------------------

15\. Notas para a sua revisão

Mesma lógica dos documentos anteriores: estas são decisões técnicas que
assumi por conta própria para fechar uma estrutura concreta --- nenhuma
está travada.

-   Cad_Lote_Produto foi modelado nesta revisão (Numero_Lote,
    Data_Fabricacao/Validade) --- assumi que o controle por lote é
    opcional por produto (nem todo produto precisa), tipicamente
    perecíveis, farmacêuticos ou controlados; não modelei uma regra de
    sistema que OBRIGUE lote quando Produto_Controlado=true, fica como
    convenção de uso, não uma restrição estrutural. O nome evita colisão
    com Mov_Lote_Lancamento (Fase 0, contábil) --- são conceitos
    diferentes.

-   Requisição interna de consumo (material saindo do estoque sem venda,
    ex.: uso interno) só o gancho de origem
    (Origem_Tipo=requisicao_interna) foi reservado --- o processo formal
    (quem pediu, aprovação) não foi modelado.

-   Custo médio ponderado móvel foi a premissa assumida para o MÉTODO de
    cálculo --- se a Mlegate ou seus clientes precisam de FIFO/PEPS ou
    custo padrão, a estrutura de Mov_Estoque_Custo_Medio muda
    significativamente (FIFO exige rastrear camadas de custo por
    entrada, não uma média única). A CADÊNCIA (diário/mensal), por outro
    lado, já é parametrizável nesta revisão via
    Cad_Empresa.Modo_Custo_Medio.

-   Assumi que o fechamento do período de custo médio mensal acontece
    por FILIAL (mesma granularidade de Mov_Estoque_Custo_Medio), mesmo o
    Modo_Custo_Medio sendo decidido a nível de empresa --- ou seja,
    todas as filiais de uma empresa usam o mesmo modo, mas cada filial
    fecha seu próprio período independentemente. Se as filiais precisam
    fechar sempre juntas, isso é regra de aplicação, não mudança na
    estrutura de dados.

-   Classificação explícita de matéria-prima / em-elaboração /
    produto-acabado em Cad_Produto_Servico não foi modelada nesta
    revisão --- ficou definido que não é necessária para o controle de
    saldo (produto acabado pode virar matéria-prima sem mudança de
    cadastro), mas pode fazer sentido para relatórios gerenciais; fica
    em aberto para quando o futuro Módulo de Produção for especificado.

-   Ordem de Produção --- o controle do que está \"em elaboração\" entre
    a saída do Estoque e o retorno do produto acabado --- é
    deliberadamente fora do escopo deste módulo (ver seção 8); o Estoque
    participa só das bordas (saída para produção, entrada de produto
    acabado).

-   Reserva de estoque para pedido de venda (evitar vender o que já está
    comprometido por outro pedido) continua fora deste módulo --- o
    módulo de CRM & Vendas, agora especificado, modela a reserva como um
    controle PRÓPRIO (Mov_Estoque_Reserva), separado dos movimentos
    reais: o saldo derivado deste módulo (seção 5) continua estritamente
    a soma de Mov_Estoque_Movimento_Item, sem reserva nenhuma entrando
    nessa conta --- \"disponível\" (saldo menos reservado) é uma leitura
    combinada das duas tabelas, calculada no módulo de CRM & Vendas, não
    uma mudança na fórmula de saldo aqui.

-   Mov_Estoque_Movimento.Origem_Tipo ganhou pedido_venda nesta revisão
    --- pedido pela especificação do módulo Fase 1 CRM & Vendas, para a
    baixa física gerada pela nota fiscal de saída referenciar o item do
    pedido de venda sendo atendido.

-   Controle de número de série individual (equipamentos, ativos
    rastreados um a um, não por lote) não foi modelado --- se for
    necessário, é uma extensão parecida com lote, mas por unidade.

-   Transferência entre filiais diferentes provavelmente exige nota
    fiscal de transferência --- ver seção 9; fica como ponto de atenção
    para quando a nota fiscal de saída for modelada.

-   Cad_Posicao_Estoque não tem vigência --- assumi que a identificação
    de uma posição (estante/prateleira) é estável; se precisar de
    histórico de mudança de identificação física, o mesmo padrão de
    vigência das demais entidades pode ser reaplicado aqui.

-   Cad_Estoque_Periodo_Custo_Medio guardava só o período aberto (um
    ponteiro por filial), não uma tabela de status por período ---
    decisão explícita, à época, para evitar abrir ou lançar num mês
    futuro antes da hora; APOSENTADO como mecanismo de status na Revisão
    10 (ver seção 7) --- o histórico de fechamentos continua em
    Mov_Estoque_Fechamento_Custo_Medio.

-   Mov_Inventario_Nota_Fiscal_Ajuste guarda só o dado básico do
    documento (número/série/data/chave de acesso) --- não modela uma
    entidade cheia de nota fiscal, porque o módulo Fase 1 CRM & Vendas
    já modelou Mov_Nota_Fiscal_Saida separadamente para a venda
    propriamente dita.

-   Revisão 7 --- pedida pela consolidação do módulo Fase 1 CRM &
    Vendas: Mov_Estoque_Movimento.Origem_Tipo ganhou venda_avulsa, para
    a baixa física da venda balcão/avulsa (sem pedido, sem reserva, sem
    histórico de status, sem comissão) apontar direto para o item da
    nota fiscal de saída; Chave_Acesso adicionada em
    Mov_Inventario_Nota_Fiscal_Ajuste (princípio geral de chave de
    acesso em toda referência a nota fiscal); e a descrição de
    Mov_Estoque_Custo_Medio.ID_Lote atualizada para refletir a nova flag
    Cad_Empresa.Controla_Custo_Medio_Por_Lote (Fase 0, revisão 13) ---
    produto controlado só desce ao lote quando a empresa também optar
    por isso.

-   Assumi que Mov_Inventario.Numero_Contagens_Planejadas e
    Numero_Contagens_Necessarias_Bater são definidos no cabeçalho do
    inventário (valem para todos os itens dele) --- se a Mlegate ou seus
    clientes precisam variar o número de contagens por produto dentro do
    mesmo inventário (ex.: itens de alto valor exigem mais contagens que
    os demais), a granularidade precisa descer para Mov_Inventario_Item.

-   Cad_Tipo_Movimento_Estoque_Empresa assume uma lista aberta, gerida
    manualmente empresa a empresa --- se a intenção for \"todas as
    empresas do grupo societário automaticamente\", a estrutura pode ser
    simplificada para referenciar Cad_Grupo_Societario direto em vez de
    listar empresa por empresa.

-   Metodo_Valoracao de ajuste_positivo e ajuste_negativo é
    parametrizado por tipo, igual às demais direções --- não assumi um
    valor padrão fixo (ex.: custo médio) para nenhum dos dois; cada
    empresa decide isso ao cadastrar o tipo.

-   Mov_Estoque_Bloqueio não impede, pela própria estrutura, dois
    bloqueios simultâneos sobre o mesmo local/produto por motivos
    diferentes (ex.: inventário e inspeção ao mesmo tempo) --- a
    validação desse tipo de conflito fica para a camada de aplicação,
    mesmo padrão já usado em Cad_Regua_Aprovador_Escopo (Fase 0).

-   Cad_Usuario_Escopo cobre o RECORTE de dado (quais locais/produtos),
    não a AÇÃO (visualizar/movimentar) --- essa distinção continua sendo
    papel de Cad_Permissao (Fase 0); o escopo se aplica igualmente a
    qualquer ação que o perfil do usuário já tiver naquele módulo.

-   Revisão 8 --- pedida pela especificação do módulo Fase 1 Produção:
    Mov_Estoque_Movimento.Origem_Tipo e
    Mov_Estoque_Movimento_Item.ID_Valor_Referencia_Tipo ganharam,
    respectivamente, ordem_producao e ordem_producao_custo_apurado
    (seção 5), fechando os dois pontos de fronteira que a seção 8 já
    reservava. Classificação explícita de
    matéria-prima/intermediário/acabado (apontada como gancho na
    revisão 5) permanece não modelada AQUI --- o módulo de Produção
    decidiu resolvê-la no próprio cadastro de extensão do produto
    (Cad_Produto_Servico_Dados_Producao), não neste módulo, já que é uma
    classificação de uso da produção, não do estoque em si. Fica como
    ponto de atenção explícito, também nesta revisão: a quebra de custo
    por tipo (materiais/mão de obra/terceiros) apurada pela Produção não
    é preservada prospectivamente dentro do custo médio deste módulo,
    que continua sendo um número único por produto+filial(+lote) --- ver
    seção 8.

-   Revisão 9 (Mov_Estoque_Condicao, seção 11): a posição de descarte
    não ganhou um Tipo estrutural novo em Cad_Posicao_Estoque --- é uma
    posição comum, dedicada por convenção de uso, mesmo padrão já usado
    para a posição de separação da Expedição (Fase 1, Expedição revisão
    2). O caminho de reparo (Condicao=em_reparo → disponivel) não exige,
    por estrutura, nenhum Mov_Estoque_Movimento físico associado --- se
    a Mlegate sempre move fisicamente o item para uma área de reparo,
    isso é convenção de uso, cabendo à camada de aplicação disparar o
    movimento quando fizer sentido.

-   Revisão 9: Mov_Estoque_Condicao.Origem_Tipo tem hoje dois valores
    estruturados (mov_expedicao_item_inspecao, mov_pedido_item_inspecao)
    e um catch-all (outro). Quando a Produção ganhar uma inspeção de
    qualidade própria e dedicada (hoje ela só tem, seção 5 daquele
    documento, a menção a \"inspeção de qualidade\" como exemplo de
    recurso de uma fase, sem entidade), Origem_Tipo pode ganhar um
    terceiro valor estruturado --- não modelado agora porque essa
    inspeção em si ainda não existe.

-   Revisão 9: não modelei uma trava que impeça
    Mov_Estoque_Condicao.Quantidade de exceder o saldo disponível do
    produto+lote(+posição) no momento do registro --- mesma filosofia de
    nunca travar estruturalmente o que é regra de processo, fica como
    validação de camada de aplicação.

-   Revisão 9: a venda de um item em Condicao=descarte não ganhou nenhum
    campo novo em CRM & Vendas nem em Expedição --- Alberto confirmou
    que é uma venda normal; o único requisito é que a Expedição CONSULTE
    a Condicao vigente ao separar (seção 11 acima, e Fase 1 ---
    Expedição seção 2), não que o pedido/nota carreguem uma marcação
    estrutural própria de \"venda de defeituoso\".

-   Revisão 10 (migração do status de fechamento para o motor genérico
    da Fase 0): Cad_Estoque_Periodo_Custo_Medio foi aposentado como
    mecanismo de status --- Alberto confirmou (\"estoque, correto\") que
    o bloco de fechamento genérico (Cad_Bloco_Fechamento /
    Cad_Periodo_Fechamento / Cad_Periodo_Fechamento_Filial, Fase 0
    seção 10) se aplica ao Estoque. O status de aberto/fechado por
    Filial+competência passa a viver em Cad_Periodo_Fechamento_Filial,
    bloco=\"estoque\" (fail-closed, seção 7).
    Mov_Estoque_Fechamento_Custo_Medio continua existindo como o
    evento/detalhe do cálculo de custo médio do fechamento, agora
    referenciando o período genérico via ID_Periodo_Filial em vez do
    antigo ponteiro único.

-   Revisão 10 --- EXTENSÃO DE ESCOPO registrada aqui como suposição
    minha, repassada para confirmação, NÃO como confirmação literal de
    Alberto sobre este ponto específico: o travamento por competência
    fechada (seção 5) passa a cobrir TODA movimentação de estoque
    (entrada, saída, transferência, ajuste positivo/negativo),
    independente de Cad_Empresa.Modo_Custo_Medio ser diário ou mensal.
    Isso é mais amplo que o antigo Cad_Estoque_Periodo_Custo_Medio, que
    só existia --- e, na prática, só protegia a apuração de custo médio
    --- no modo mensal; no modo diário nunca houve conceito de período
    fechado bloqueando lançamento. A extensão decorre do princípio geral
    que Alberto confirmou para todos os blocos de fechamento (fechar
    trava tudo, sem exceção específica de tipo de movimento), mas a
    aplicação literal desse princípio ao modo diário do Estoque
    especificamente é a parte que extrapolei ao escrever esta revisão
    --- se a intenção for manter o modo diário sempre livre para
    lançamento (já que ali não existe período provisório de custo médio
    a proteger), a seção 5 precisa ser revista para restringir o
    travamento só ao modo mensal.

-   Revisão 10: sem validação de pendência no fechamento deste bloco
    (\"estoque\") --- diferente de Compras, que valida pendência antes
    de aceitar o fechamento do próprio bloco. Se a Mlegate quiser o
    mesmo tipo de validação para o Estoque (ex.: impedir fechar um
    período com inventário em aberto, Mov_Inventario.Status=aberto,
    seção 10), isso precisa ser pedido e modelado explicitamente, não
    foi assumido por mim.

-   Revisão 12 --- Bloco 1 da validação geral (Relatório de Validação
    Geral e Desenho do Bloco 1): Cad_Local_Estoque_Endereco padronizado
    (CEP, campos próprios, sem ID_Estado);
    Cad_Estoque_Periodo_Custo_Medio rebaixada a registro histórico;
    novas Mov_Saldo_Estoque e Mov_Saldo_Estoque_Valor (saldos guardados
    por período fechado, definidos por Alberto); chave primária de
    Cad_Tipo_Movimento_Estoque_Empresa; número e série da nota de ajuste
    desmembrados; competência e chave de acesso de 44 caracteres (CNPJ
    alfanumérico). A convenção completa (vigência, identidade + versão,
    sucessão de códigos oficiais, competência, CNPJ alfanumérico, um
    campo por informação, saldos guardados de período fechado, sequência
    de fechamento) vive na Fase 0, seções 2 e 10 (revisão 41).

-   Revisão 13 --- tipo lógico \"código (n)\" definido por Alberto ---
    todo campo que identifica algo (inscrição, documento, agência,
    conta, número e série de nota, matrícula, código oficial) é
    caractere, nunca numérico: os zeros à esquerda fazem parte do
    código, e o padrão pode passar a aceitar letras ou mudar de tamanho,
    como aconteceu com o CNPJ alfanumérico. Campos revistos: Cep,
    Chave_Acesso, Codigo_Postal_Exterior, Numero_Nota_Fiscal,
    Serie_Nota_Fiscal. Convenção completa na Fase 0, seção 2.6 (revisão
    42).

-   Revisão 14 --- Cad_Estoque_Escopo_Usuario aposentada (seção 13): o
    recorte de dado por local, produto e classificação passa para
    Cad_Usuario_Escopo da Fase 0, com Modulo = estoque, sem mudança da
    regra de aplicação. Desenho aprovado e histórico do bloco nos
    documentos 20 e 22 do Projeto.

16\. Próximo passo

*O módulo de CRM & Vendas foi especificado numa rodada anterior, por
decisão de Alberto --- fora da ordem original do Documento Analítico,
que colocava Contas a Pagar/Receber (Fase 2) antes dele. Contas a
Pagar/Receber, Tesouraria e Contabilidade & Fiscal (Fase 2) foram
especificados nas rodadas seguintes, e a Revisão 8 fechou a fronteira
com o módulo de Produção. A Revisão 9 fechou um comentário pós-entrega
da Expedição --- condição de estoque e resolução de rejeição (seção 11)
--- transversal a Expedição, Compras e Produção, todos patcheados
naquela mesma rodada. Esta Revisão 10 migra o status de
abertura/fechamento do Estoque para o motor genérico de fechamento da
Fase 0 (Cad_Periodo_Fechamento_Filial, bloco=\"estoque\"), a pedido de
Alberto (\"estoque, correto\") --- aposentando
Cad_Estoque_Periodo_Custo_Medio como mecanismo de status e estendendo o
travamento por competência fechada a toda movimentação física de
estoque, nos dois modos de custo médio (ver seção 7 e Notas, inclusive o
registro explícito da extensão de escopo ao modo diário). Esta Revisão
11, decorrente da revisão geral de módulos pedida por Alberto, corrige o
fechamento agregado (seção 7) para lançar por Classe/Família em vez de
um valor único, e exclui a categoria de produção desse agregado, já que
ela passou a se contabilizar sozinha em tempo real (seção 8, ver módulo
de Produção). Nenhum outro ponto pendente de construção neste momento.*

*Revisão 12 --- Bloco 1 da validação geral consolidado junto com a Fase
0 (revisão 41). Próximos passos combinados com Alberto: Bloco 2 (fiscal)
e Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 13 --- tipo lógico \"código\" aplicado junto com a revisão 42
da Fase 0. Próximos passos combinados com Alberto: Bloco 2 (fiscal) e
Bloco 3 (folha e jurídico), cada um com desenho próprio para aprovação
antes de consolidar.*

*Revisão 14 --- Bloco 3 consolidado junto com a Fase 0 (revisão 45). Sem
pendência própria deste módulo.*



17\. Anexo --- Entidades e domínios da revisão 3 (documentos 33 a 46)

Revisão 3 do dicionário: este anexo reúne 1 entidades novas de Estoque, vindas dos documentos de desenho 33 a 46, que Alberto aprovou e mandou consolidar em 12/10/2026. As alterações em entidades que já existiam aparecem nas próprias tabelas (campos marcados "Novo na revisão 3" ou "Alterado na revisão 3"). As regras legais citadas (alíquotas, prazos, versões de leiaute, códigos oficiais) são parâmetros com vigência, nunca valores fixos no código.

17.1. Manuais oficiais: EFD-ICMS/IPI, PGDAS-D, DOI, CNO, LCDPR, DEAP e Mafon (documento 37)

Mov_Estoque_Reclassificacao

Reclassificação de item em estoque, quando o código muda por pedido do cliente ou por controle de qualidade (K220). Hoje só existe transferência entre locais, que não troca o item.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|----------------------------|----------------------------------------|
| **ID_Estoque_Reclassificacao** | *identificador* | --- |
| **ID_Filial** | *referência (Cad_Filial)* | Estabelecimento do estoque reclassificado. |
| **Data_Movimento** | *data* | DT_MOV: data da reclassificação. |
| **ID_Produto_Servico_Origem** | *referência (Cad_Produto_Servico)* | COD_ITEM_ORI: item que sai do estoque. |
| **ID_Produto_Servico_Destino** | *referência (Cad_Produto_Servico)* | COD_ITEM_DEST: item que entra no estoque, diferente do de origem. |
| **Quantidade_Origem** | *número* | QTD_ORI: quantidade do item de origem, maior que zero. |
| **Quantidade_Destino** | *número* | QTD_DEST: quantidade do item de destino, maior que zero. |
| **Motivo_Reclassificacao** | *enumeração {solicitacao_cliente, controle_qualidade, outro, deterioracao, obsolescencia_reaproveitamento, estoque_por_cliente, aglutinacao_insumo}* | Por que o código mudou, conforme o Guia. Revisão 32 (documento 176, seção 7.2, Q176-9; D-N482): deterioracao (item deteriorado que passa a subproduto vendável, FAQ 16.4.1.21), obsolescencia_reaproveitamento (16.4.1.15), estoque_por_cliente (estoque segregado por cliente com código próprio, 16.4.1.20) e aglutinacao_insumo (insumos de cores diferentes num código único, 16.4.1.18). O campo é interno (não vai ao arquivo); outro continua para o que não couber. |
| **ID_Movimento_Estoque_Item_Saida** | *referência (Mov_Estoque_Movimento_Item, opcional)* | Saída do item de origem. |
| **ID_Movimento_Estoque_Item_Entrada** | *referência (Mov_Estoque_Movimento_Item, opcional)* | Entrada do item de destino. |

*Revisão 32 --- valores de enumeração novos: Motivo_Reclassificacao (+deterioracao, obsolescencia_reaproveitamento, estoque_por_cliente, aglutinacao_insumo).*
