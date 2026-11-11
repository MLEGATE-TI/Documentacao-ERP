**ERP — DESENHO CONCEITUAL**

**Documento Analítico e Ordem de Desenvolvimento**

*Consolidação módulo a módulo, quadro de dependências e roteiro lógico de construção*

Mlegate

Alberto Beyeler

Setembro de 2026

Sumário

*Se os números de página não aparecerem automaticamente, clique sobre o sumário e pressione F9 (ou clique com o botão direito e escolha "Atualizar campo").*

1\. Introdução

Este documento consolida, de forma analítica e estruturada, o desenho conceitual de um sistema ERP construído em torno de um pequeno número de motores reutilizáveis — não de dezoito módulos independentes. Ele é complementar à apresentação em PowerPoint que acompanha esta entrega: onde a apresentação simplifica para comunicar a ideia, este documento aprofunda cada módulo e, principalmente, propõe uma ordem lógica de desenvolvimento, com a justificativa de dependência por trás de cada fase.

O princípio central que atravessa todo o desenho é simples de enunciar e difícil de abandonar depois de adotado: o que se repete — classificação por prioridade, versionamento por vigência, aprovação em faixas de valor, cadastro único de participante — deve ser construído uma única vez, como serviço transversal, e reaproveitado por todos os módulos que precisam dele. Essa escolha é o que torna viável oferecer o sistema como produto multi-tenant, porque reduz drasticamente a necessidade de customização por cliente.

2\. Princípios arquiteturais transversais

Os nove princípios a seguir não pertencem a nenhum módulo específico — eles sustentam todos, do primeiro ao último, e qualquer decisão de especificação técnica que os contradiga deve ser tratada como uma exceção deliberada, nunca como um esquecimento.

Framework / plugin

Tudo que varia por cliente ou por integração externa — banco, autoridade fiscal, transportadora, país — é tratado como um módulo plugável dentro de um núcleo estável, nunca como um branch de código específico para aquele cliente. O mesmo padrão vale para bancos (CNAB/API), esquemas de nota fiscal, e a comunicação de Comércio Exterior com o Siscomex.

Vigência universal

Todo registro mestre — cadastro, regra, verba, depreciação, alocação de recurso a uma planta — carrega período de validade como parte da sua própria identidade. O histórico nunca é sobrescrito: uma mudança abre um novo período de vigência, e cada obrigação usa sempre o valor que estava vigente na data do fato gerador.

Cadastro único

Cliente, fornecedor e colaborador são o mesmo participante, distinguido por classes que podem coexistir na mesma pessoa ou empresa. Produto segue o mesmo princípio: matéria-prima, intermediário e produto acabado são o mesmo cadastro, todos potencialmente vendáveis.

Pré-cadastro

Relacionamentos ainda especulativos — um lead comercial, um candidato a emprego — ficam num cadastro separado e só são promovidos ao cadastro único quando o negócio fecha ou a contratação se efetiva. Isso evita contaminar a base definitiva com relações que nunca se concretizam.

Motor de regras com prioridade, sempre versionado

A mesma lógica de classificação — a regra mais específica vence a mais genérica, com o motivo da decisão sempre visível e um histórico de regra auditável — reaparece em esquema de nota fiscal, tabela de preço, tabela de comissão e comissão de royalty.

Régua de aprovação única

Uma única árvore de aprovação — faixas de valor, papéis de aprovador (obrigatório, principal, secundário) e suplentes — é reaproveitada por qualquer gatilho de desvio: orçamento, limite de crédito, ou uma camada extra de caixa acima do limite do gestor. Deliberadamente não existe uma régua por tipo de gatilho, para não multiplicar configuração.

Tudo é insumo de BI

O dado nasce estruturado no ponto de entrada, nunca como texto livre, para que possa ser cruzado e tabulado depois. Isso vale para toda a base — não é uma camada de relatório encaixada ao final, é uma restrição de desenho desde o primeiro cadastro.

Auditabilidade universal

Quem fez, quando e por quê é registrado em todo módulo e em toda exceção ou override — não apenas nas mudanças cadastrais, mas em qualquer decisão que se desvie do padrão.

Isolamento multi-tenant

Dado de negócio nunca cruza tenants. Entre tenants (clientes) diferentes, a única coisa que pode ser exportada de uma empresa para outra é regra de configuração — nunca dado — e mesmo isso respeita a modalidade de fornecimento (on-premise versus SaaS). Dentro de um mesmo tenant, porém, empresas do mesmo Grupo Societário podem ir além da regra: podem compartilhar cadastro inteiro entre si, no todo ou em parte — por exemplo, um plano de contas único servindo todas as empresas do grupo, em vez de um por empresa.

3\. Arquitetura em camadas

O sistema se organiza em cinco camadas, cada uma dependendo da anterior já existir e funcionar corretamente. Da base para o topo: o Núcleo reúne os motores transversais (cadastro único, vigência, motor de regras, régua de aprovação) que nenhum módulo de negócio reimplementa. A camada de Operação cobre o ciclo transacional principal — Planejamento/Orçamento, Compras, Estoque e Produção. A camada Financeira fecha o ciclo em valor e obrigação fiscal — Contas a Pagar/Receber, Tesouraria, Contabilidade & Fiscal e Ativo Imobilizado. A camada de Interação é onde o cliente e o colaborador efetivamente encontram o sistema — CRM & Vendas, Expedição, Portal do Cliente, Gestão de Contratos e de Projetos. E a camada Transversal — BI/Analytics, GED, Folha & RH, isolamento multi-tenant — consome e alimenta todas as camadas abaixo dela, em vez de operar isolada.

Essa mesma lógica de camadas é o que orienta a ordem de desenvolvimento proposta na seção 6: não é uma opção estética, é a sequência que evita retrabalho.

4\. Módulos — descrição analítica

Cada subseção descreve a função do módulo, os mecanismos-chave decididos ao longo da contextualização, e suas dependências diretas dentro do quadro apresentado na seção 5.

Planejamento & Orçamento

*Cluster: Núcleo transacional*

O ponto de partida deliberado do sistema é a verba/orçamento empenhado por área — mas o orçamento funciona como referência, não como bloqueio. Qualquer fuga de valor, incluindo uma reposição automática disparada por estoque mínimo, escala para a régua de aprovação em vez de travar a operação. A contratação de pessoal também empenha verba, e a Folha compromete automaticamente os meses seguintes após a efetivação da contratação.

Confirmado como decisão de gestão, não arquitetural: uma empresa pode exigir uma camada extra de aprovação mesmo quando o orçamento pré-aprovado do gestor já cobriria o valor, porque a execução orçamentária é uma visão de caixa da empresa como um todo, não isolada por departamento. Essa camada extra não é um mecanismo à parte — é apenas mais um degrau na mesma régua de aprovação, e qualquer nível da régua pode ter um ou mais aprovadores.

**Depende de:** Contabilidade (saldo histórico), dimensões contábeis **\| Alimenta:** Compras, Folha (verba de contratação), régua de aprovação

Compras

*Cluster: Núcleo transacional*

Toda entrada é ancorada em XML padrão (NF-e/NFC-e/NFS-e/CT-e) — nunca digitação manual — e roteada por Destinação: Estoque, Ordem de Produção, Imobilizado ou Custo/Despesa de uma área específica, conforme a classificação da área (produtiva, vendas, administrativa, apoio à produção, apoio geral). O módulo suporta triangulação, com notas fiscais em depósito de terceiros ou industrialização em terceiros.

Destinação é hoje um cadastro pré-registrado e parametrizável — nunca algo dinâmico que aparece e some — porque outras regras do sistema (fiscal, contábil) ficam amarradas à identidade estável de cada Destinação. Um produto carrega uma Destinação padrão como sugestão, mas quem decide de fato é o item do pedido de compra ou importação, por linha: o mesmo produto pode aparecer em duas linhas do mesmo pedido com quantidades e Destinações diferentes (por exemplo, parte para Estoque e parte para Imobilizado). Frete é tratado como uma compra normal, podendo virar contrato por km ou por entrega. Uma mudança de Destinação depois que o item já está na empresa — por exemplo, mudança de finalidade de uma importação — é tratada como um novo período de vigência daquela Destinação, e pode exigir ajustes lançados simultaneamente em Fiscal, Estoque e Imobilizado, cobrindo tanto correção de erro quanto mudança legítima de finalidade, sempre reaproveitando os mecanismos de ajuste já previstos na legislação.

**Depende de:** Cadastro único, motor de regras (esquema de nota), régua de aprovação **\| Alimenta:** Estoque, Imobilizado, Fiscal (blocos do SPED), nota de entrada

Estoque

*Cluster: Núcleo transacional*

O Estoque é proativo, não passivo: alimenta a Produção e a área comercial em vez de apenas responder a retiradas. Uma vez que um produto entra na sequência de produção, o material correspondente é empenhado; uma cotação convertida em pedido de venda reserva o produto imediatamente, para nunca dar a falsa impressão de disponibilidade e depois falhar com o cliente.

Foi formalizada a distinção canônica entre Estoque Físico (o que fisicamente existe) e Estoque Disponível (o físico menos o que está empenhado ou reservado). Todo gatilho de negócio — mínimo e segurança, reposição automática, o que o vendedor vê como vendável — opera sempre sobre o Disponível, nunca sobre o Físico bruto. Se um pedido de venda é cancelado antes da saída física, o produto volta ao Disponível.

**Depende de:** Compras, Produção (empenho) **\| Alimenta:** Produção, Vendas (reserva), Expedição

Produção

*Cluster: Núcleo transacional*

Suporta três modos — estrutura padrão (BOM), produção sob medida com estrutura própria, e produção por receita com ajuste final (indústria química). A estrutura de produto é versionada com vigência, mas é uma referência: a execução de uma ordem específica pode se desviar dela (substituição de insumo por falta, por exemplo) sem alterar a estrutura mestre, desde que o desvio seja destacado, nunca absorvido silenciosamente. O roteiro de produção é um grafo, não uma cadeia linear — etapas podem rodar em paralelo e convergir depois.

O apontamento de horas (timesheet) é uma única entidade de dado, não três estruturas paralelas: a mesma peça alimenta Produção (cronômetro por operador/máquina), Gestão de Contratos (hora corrida por colaborador/projeto) e Gestão de Projetos (hora por atividade/recurso). O custeio segmentado por tipo (matéria-prima direta/indireta, mão de obra direta/indireta, terceiros, industrialização) é sempre calculado na moeda funcional da empresa — nunca em paralelo em múltiplas moedas — e o tratamento multi-moeda fica restrito à camada de CTA na Contabilidade.

**Depende de:** Estoque (empenho), Folha/RH (MOD/MOI), Engenharia (BOM), recursos de produção **\| Alimenta:** Estoque (produto acabado, subproduto/coproduto), Vendas (prazo), Contabilidade (custeio)

CRM & Vendas

*Cluster: Núcleo transacional*

CRM e Pedido de Venda são intertrincados, não separados. Um prospect fica em pré-cadastro, separado do cadastro único, até que uma cotação seja aceita — só então o pedido de venda nasce, sempre já confirmado (a aprovação aconteceu no momento da aceitação da cotação). O status é tracked como histórico completo, por item de pedido, não um único status agregado, e o pedido pode ser entregue e faturado em múltiplas notas fiscais ao longo do tempo.

Tabela de preço e tabela de comissão compartilham as mesmas seis dimensões configuráveis de produto (classe, família, licenciamento, marca), com prioridade de regra definida pelo gestor. Desconto reduz comissão de forma proporcional ou por fator tabelado, e o mesmo motor calcula royalty de licenciamento. Crédito do cliente é consolidado no Grupo Econômico (conjunto de participantes) quando existir, distinto do Grupo Societário (conjunto de empresas do próprio tenant) — dois cadastros, dois nomes, nunca confundidos.

**Depende de:** Estoque (disponível), Produção (prazo), tabela de preço/comissão **\| Alimenta:** Expedição, Contas a Receber, BI

Expedição

*Cluster: Núcleo transacional*

Trabalha lado a lado com o Estoque — o mapeamento de posição reduz o tempo de separação — e é responsável por localizar material e obter o aval da Qualidade antes do embarque. O pedido de venda especifica a responsabilidade de cada trecho de transporte, num espectro de tipo Incoterm.

Frete é tratado como uma compra normal — nunca um módulo à parte — podendo virar contrato por km ou por entrega, reaproveitando a Gestão de Contratos. O CT-e entra como despesa de vendas, marcado pelo cliente atendido, para que o BI calcule resultado por cliente incluindo o custo de frete. O rastreio é resolvido por redirecionamento ao link da própria transportadora, sem exigir integração estruturada — o que também sinaliza ao cliente que a responsabilidade daquele trecho passou a ser de terceiro. Um envio multimodal é tratado como um projeto simples, com etapas predefinidas, reaproveitando a Gestão de Projetos.

**Depende de:** Estoque, Vendas (reserva) **\| Alimenta:** Contas a Pagar/Receber (frete), Gestão de Contratos

Contas a Pagar & Receber

*Cluster: Camada financeira*

É um único módulo, não dois — o mesmo motor, com direção diferente conforme o fluxo seja de pagamento ou recebimento. Controla adiantamentos de clientes e fornecedores, permite encontro de contas quando um fornecedor também é cliente, e verifica saldo em bancos, caixa e aplicações no momento da baixa.

O limite de crédito de um cliente é medido pela exposição total — saldo a receber em aberto mais o novo pedido — e só se recompõe com o recebimento efetivo, nunca com o simples faturamento. Quando o cliente pertence a um Grupo Econômico, o bloqueio por inadimplência aplica-se ao grupo inteiro, não apenas ao CNPJ em atraso, sem exigir consentimento prévio do cliente — é uma decisão interna de gestão de risco.

**Depende de:** Cadastro único, Fiscal (XML de entrada e saída) **\| Alimenta:** Tesouraria, BI

Tesouraria

*Cluster: Camada financeira*

Funciona como painel de gestão, não como tela puramente operacional: tem visão prospectiva (o que vence nos próximos dias) e retrospectiva (o que ficou pendente de dias anteriores) — nunca apenas o dia corrente. Sugere aplicação financeira para sobra de caixa, sem impor, e não há parâmetro fixo de caixa mínimo — fica a critério do gestor com base na informação em tela.

A régua de cobrança escala deliberadamente do gentil ao definitivo: um aviso discreto próximo do vencimento, uma notificação de pendência pouco depois do atraso, e só além de um número configurável de dias o bloqueio de novas vendas e a zeragem do limite de crédito — sempre com alerta cruzado para Vendas, Gestor de Vendas e Financeiro, porque cobrança nunca é assunto isolado da Tesouraria.

**Depende de:** Contas a Pagar/Receber, bancos (API/CNAB) **\| Alimenta:** Contabilidade, painel de gestão executivo

Contabilidade & Fiscal

*Cluster: Camada financeira*

As dimensões contábeis são configuráveis por empresa — Empresa, Filial, Grupo Societário, Centro de Custo, Gerência, Unidade de Negócio, e quantas mais forem necessárias — e uma vez registradas, são honradas em todo o sistema. O motor de esquemas de nota aprende regra de classificação fiscal (fornecedor, produto, CFOP, NCM, camada tributária) com histórico versionado e motivo sempre exibido, e o controle de período é por período aberto — o que não está aberto está implicitamente fechado — granular por módulo.

O cálculo do CTA (Ajuste Acumulado de Conversão) separa dois eixos: Movimento (Diário ou Médio) e Saldo (Final ou Histórico) por conta contábil. Contas de Imobilizado, sendo do tipo Histórico, capitalizam o ativo na moeda funcional e em cada moeda de CTA, sempre pela taxa histórica de aquisição — o que também vale, sem exceção, para cada tipo de depreciação simultânea (fiscal, acelerada, gerencial): todas são calculadas em todas as moedas de CTA. O plano de contas em si pode ser único e compartilhado entre todas as empresas do mesmo Grupo Societário, em vez de um por empresa — o mesmo mecanismo de compartilhamento de cadastro do Grupo Societário, aplicado à dimensão contábil mais central.

**Depende de:** Todos os módulos operacionais, dimensões contábeis **\| Alimenta:** Imobilizado, BI, obrigações acessórias (SPED, Reinf, DCTFWeb)

Ativo Imobilizado

*Cluster: Camada financeira*

É alimentado por notas de compra ou por imobilizado em andamento (obras, galpões), classificado por tipo/classe com uma regra de depreciação padrão que pode ser sobreposta por ativo individual. Ativos concedidos (uma rodovia com concessão até uma data fixa) têm sua taxa de depreciação calculada de trás para frente, a partir dessa data — não uma duração padrão fixa.

Um mesmo ativo pode ter múltiplas depreciações simultâneas — fiscal, acelerada, gerencial — cada uma com lançamento próprio, e cada uma delas replicada em todas as moedas de CTA, sempre à taxa histórica de aquisição, nunca à taxa do mês corrente. O mesmo vale para uma eventual baixa do ativo.

**Depende de:** Compras, Contabilidade (CTA, multi-moeda) **\| Alimenta:** Contabilidade, BI

Folha & RH

*Cluster: Pessoas*

O colaborador é um participante com classe própria dentro do cadastro único, com matrícula por vínculo — permitindo desligar e recontratar sem perder o histórico da pessoa. A ficha do colaborador concentra tudo — exames, vacinas, afastamentos, viagens, e agora também acidentes de trabalho — com cada tipo de evento mapeado ao código correspondente do eSocial, e um atributo próprio indicando se o envio deve ser imediato ou pode esperar o fechamento da folha.

Verbas são tipificadas e configuráveis por fórmula por empresa, com detecção de dependência circular na ordem de cálculo, e agora carregam também um atributo de origem — legal (base fixada por lei, como o FGTS sobre remuneração bruta) ou interna (regra livre da empresa, como previdência complementar sobre salário líquido). Esse atributo governa também o nível de acesso: um usuário pode ter permissão para alterar só verbas legais, só internas, ou ambas — e mesmo uma verba legal muda quando a legislação muda, sempre por vigência, nunca por sobrescrita direta. O ponto eletrônico cruza marcações com o horário contratual para identificar falta/atraso/hora extra, sempre sugerindo — nunca aplicando automaticamente — o preenchimento de lacunas de marcação.

**Depende de:** Cadastro único, ponto eletrônico, Orçamento (verba de contratação) **\| Alimenta:** Produção (MOD/MOI), Contabilidade, comissão de vendas

Gestão de Contratos

*Cluster: Iniciativas de ciclo longo*

Segue o mesmo princípio de cadastro único das demais áreas: um só módulo de contrato, não um para cliente e outro para fornecedor. Suporta reajuste por índice cadastrável com período configurável, e três modelos de valor — fixo, fixo mais variável por parâmetro, ou quantidade garantida apurada após o período.

Contratos por hora corrida usam o timesheet único já definido para Produção, permitindo apuração de resultado por contrato e por projeto — e, quando aplicável, alimentando diretamente o custeio de produção com o mesmo apontamento.

**Depende de:** Cadastro único, timesheet, régua de aprovação **\| Alimenta:** Contas a Pagar/Receber, Expedição (contrato de frete)

Gestão de Projetos (PPM)

*Cluster: Iniciativas de ciclo longo*

Cada atividade do projeto é estimada por três prazos (realista, pessimista, otimista), ponderados ao estilo PERT, e conectada a antecessoras e sucessoras — permitindo ao sistema identificar caminho crítico e caminhos com folga, inclusive para realocar recursos entre projetos diferentes. O timesheet, já definido para Produção e Contratos, ganha aqui uma dimensão de atividade/projeto.

O projeto é um pacote: a Destinação contábil e fiscal (Imobilizado, Custo de Produção diferido, ou Serviço/Produto em elaboração) é decidida por entregável, não pelo projeto como um todo — um mesmo projeto de implantação de planta pode ter uma edificação indo para uma conta de Imobilizado, máquinas para outra, e deslocamentos para despesa.

**Depende de:** Timesheet, Cadastro único (stakeholders), régua de aprovação **\| Alimenta:** Imobilizado, Custo de Produção, Contas a Receber

Serviços transversais

Não são módulos de negócio — são os motores que todo módulo acima reaproveita em vez de reimplementar. Tratá-los como serviços de primeira classe, com contrato próprio, é o que sustenta a viabilidade de todo o resto do desenho.

Cadastro Único & Vigência

Participante e produto com histórico versionado no PK — a base sobre a qual todo o resto é construído.

Motor de Regras

Classificação por prioridade — mais específico vence o mais genérico — com motivo sempre exibido e histórico de regra auditável.

Régua de Aprovação

Faixa de valor, papéis de aprovador e suplente, reaproveitada por qualquer gatilho de desvio.

GED

Retenção por classe de documento, com extensão automática sob processo judicial e descarte sempre sujeito a aprovação prévia.

BI / Analytics

Ganho ou perda por visões independentes e trocáveis — produto, cliente, Grupo Econômico, mix — nunca dado recalculado, sempre dado já estruturado na origem.

Isolamento multi-tenant

Dado de negócio nunca cruza tenant; entre tenants, só regra de configuração pode ser exportada. Dentro do mesmo tenant, empresas do mesmo Grupo Societário podem compartilhar cadastro inteiro entre si (ex.: plano de contas único).

5\. Quadro de dependências

Quadro completo dos treze módulos de negócio, com o que cada um consome e o que alimenta a jusante. Comércio Exterior não aparece como linha própria porque, por decisão de desenho, permanece embutido em Compras e Vendas — sua contribuição específica (DI, Siscomex, drawback) é tratada como uma extensão fiscal desses dois módulos, não como um módulo isolado.

|                              |                                                         |                                                           |
|------------------------------|---------------------------------------------------------|-----------------------------------------------------------|
| **Módulo**                   | **Consome de**                                          | **Alimenta**                                              |
| **Planejamento & Orçamento** | Contabilidade (histórico), dimensões contábeis          | Compras, Folha (verba de contratação), régua de aprovação |
| **Compras**                  | Cadastro único, motor de regras (esquema de nota)       | Estoque, Imobilizado, Fiscal (SPED), Destinação           |
| **Estoque**                  | Compras, Produção (empenho)                             | Produção (acabado/subproduto), Vendas, Expedição          |
| **Produção**                 | Estoque (empenho), Folha/RH (MOD/MOI), Engenharia (BOM) | Estoque, Vendas (prazo), Contabilidade (custeio)          |
| **CRM & Vendas**             | Estoque (disponível), Produção (prazo), tabela de preço | Expedição, Contas a Receber, BI                           |
| **Expedição**                | Estoque, Vendas (reserva)                               | Contas a Pagar/Receber (frete), Contratos                 |
| **Contas a Pagar & Receber** | Cadastro único, Fiscal (XML)                            | Tesouraria, BI                                            |
| **Tesouraria**               | Contas a Pagar/Receber, bancos                          | Contabilidade, painel de gestão                           |
| **Contabilidade & Fiscal**   | Todos os módulos operacionais, dimensões                | Imobilizado (CTA), BI, obrigações acessórias              |
| **Ativo Imobilizado**        | Compras, Contabilidade (multi-moeda/CTA)                | Contabilidade, BI                                         |
| **Folha & RH**               | Cadastro único, ponto eletrônico, Orçamento (verba)     | Produção (MOD/MOI), Contabilidade, comissão               |
| **Gestão de Contratos**      | Cadastro único, timesheet                               | Contas a Pagar/Receber, Expedição (frete)                 |
| **Gestão de Projetos (PPM)** | Timesheet, Cadastro único (stakeholders)                | Imobilizado, Custo de Produção, Contas a Receber          |

6\. Ordem lógica de precedência para desenvolvimento

A lógica geral é a mesma da arquitetura em camadas: primeiro os motores transversais, depois o menor ciclo operacional que os exercita de ponta a ponta, depois o fechamento financeiro desse ciclo, e só então as camadas que dependem de custo e crédito já calculados corretamente — produção avançada e ativos, comercial e logística. Pessoas pode correr em paralelo desde cedo, por depender pouco do restante. Iniciativas de ciclo longo e inteligência de negócio fecham o roteiro, porque ambas são, por natureza, consolidadoras: reaproveitam o que já existe em vez de o antecederem.

|          |                                                                                             |                                                                                                                                                                                                                                                       |                          |
|----------|---------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| **Fase** | **Módulos / componentes**                                                                   | **Por que nesta ordem**                                                                                                                                                                                                                               | **Pré-requisito direto** |
| **0**    | **Cadastro único, vigência, motor de regras, régua de aprovação, dimensões contábeis, GED** | São os motores que todo módulo posterior reaproveita. Construir qualquer módulo de negócio antes deles significa reconstruí-lo depois.                                                                                                                | Nenhum — é a base        |
| **1**    | **Planejamento/Orçamento, Compras, Estoque**                                                | Formam o menor ciclo operacional fechado (verba → compra → estoque) e validam os motores da Fase 0 sob transação real.                                                                                                                                | Fase 0                   |
| **2**    | **Contas a Pagar/Receber, Tesouraria, Contabilidade & Fiscal**                              | Precisam que Compras/Estoque já emitam os documentos fiscais que alimentam esta camada; Produção só posta custo corretamente depois que a Contabilidade existe.                                                                                       | Fase 1                   |
| **3**    | **Produção (Engenharia/BOM, recursos, timesheet), Ativo Imobilizado**                       | Dependem de Estoque (empenho) e de Contabilidade (custeio, depreciação, CTA) já operando.                                                                                                                                                             | Fase 1 e 2               |
| **4**    | **CRM & Vendas, Expedição, Portal do Cliente**                                              | Um fluxo comercial confiável exige Estoque (disponível), Produção (prazo de entrega) e Financeiro (crédito e cobrança) já maduros.                                                                                                                    | Fase 1, 2 e 3            |
| **5**    | **Folha & RH (ponto eletrônico, SST/eSocial)**                                              | Pode correr em paralelo às Fases 2–4, pois depende principalmente da Fase 0 (cadastro único, vigência, orçamento). Só a integração completa com MOD/MOI de Produção exige a Fase 3 já ativa.                                                          | Fase 0 (paralelo)        |
| **6**    | **Gestão de Contratos, Gestão de Projetos (PPM)**                                           | Reaproveitam o timesheet e a régua de aprovação já maduros, e precisam de Contas a Pagar/Receber e Imobilizado como destino de faturamento/capitalização.                                                                                             | Fase 2 e 3               |
| **7**    | **BI/Analytics, Comércio Exterior, Template de configuração entre empresas**                | São camadas de consolidação e expansão por natureza — BI precisa de dado estruturado vindo de todos os módulos; Comércio Exterior é aditivo dentro de Compras/Vendas; o template de configuração só faz sentido com uma base de clientes já operando. | Todas as anteriores      |

Duas advertências práticas sobre esta ordem. Primeiro, ela é lógica, não necessariamente cronológica rígida — nada impede que uma equipe maior trabalhe em paralelo em fases adjacentes, desde que a Fase 0 esteja de fato estável antes de qualquer outra começar; é o único ponto em que paralelismo é arriscado. Segundo, o quadro de dependências da seção 5 é a fonte de verdade caso surja dúvida sobre se um módulo específico pode adiantar-se à sua fase — a resposta está em quais dependências diretas ele lista.

7\. Decisões de desenho já fechadas

Ao longo da contextualização e de duas rodadas de revisão crítica, doze pontos de inconsistência ou lacuna foram identificados e, em seguida, resolvidos com Alberto. Eles estão detalhados, com a justificativa completa de cada resolução, no artefato "Anatomia do ERP" publicado à parte; aqui ficam apenas registrados, para que este documento sirva de referência autônoma.

> **1.** Estoque Físico (o que existe fisicamente) e Estoque Disponível (físico menos empenhado/reservado) — todo gatilho de negócio usa sempre o Disponível.
>
> **2.** Limite de aprovação do gestor: parametrizável por empresa se o orçamento pré-aprovado basta, ou se exige uma camada extra — decisão de gestão, não do sistema.
>
> **3.** Custeio segmentado por tipo é sempre calculado na moeda funcional; multi-moeda fica restrito à camada de CTA na Contabilidade.
>
> **4.** Timesheet é uma única entidade de apontamento, reaproveitada por Produção, Contratos e Projetos — nunca três estruturas paralelas.
>
> **5.** Grupo Econômico (participantes) e Grupo Societário (empresas do tenant) são dois cadastros distintos, com nomes definitivos; empresas do mesmo Grupo Societário podem compartilhar cadastro entre si, no todo ou em parte (ex.: plano de contas único para o grupo).
>
> **6.** "Destinação" é o termo correto (não "destino") e é um único conceito reaproveitado em Compras, Importação e entregáveis de Projeto.
>
> **7.** Verba tem origem legal (base fixada por lei) ou interna (regra livre da empresa) — o exemplo de FGTS foi corrigido para incidir sobre remuneração bruta.
>
> **8.** Estimativa de adoção da NFS-e nacional foi atualizada com pesquisa datada: adesão quase universal, mas operacional ainda em torno de um terço dos municípios.
>
> **9.** Rastreio de expedição resolvido por redirecionamento ao link da própria transportadora, sem exigir integração estruturada.
>
> **10.** Todas as depreciações simultâneas de um ativo (fiscal, acelerada, gerencial) são calculadas em todas as moedas de CTA, sempre à taxa histórica.
>
> **11.** A camada extra de aprovação do achado 2 não é um mecanismo à parte — é apenas mais um degrau da mesma régua de aprovação já existente.
>
> **12.** Destinação é um cadastro pré-registrado e parametrizável; sua Destinação padrão por produto é só sugestão, sobrescrita pelo item do pedido, por linha. Mudança de Destinação pós-fato é tratada por vigência, podendo exigir ajustes em Fiscal, Estoque e Imobilizado.

8\. Próximos passos

Com o desenho conceitual fechado e sem lacunas conhecidas, o passo seguinte é a especificação técnica propriamente dita: modelagem de dados módulo a módulo, a partir do quadro de dependências da seção 5, começando pelos motores da Fase 0 — eles são o contrato que toda tela e toda API subsequente vai assumir como dado. Só depois disso faz sentido prototipar telas ou discutir stack de implementação com um time de desenvolvimento.
