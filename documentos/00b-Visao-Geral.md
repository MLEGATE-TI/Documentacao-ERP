# ERP Mlegate — Visão Geral (conteúdo extraído da apresentação)


## Slide 1

- ERP
- Arquitetura Conceitual do Sistema
- Visão geral para apresentação da ideia — módulos, motores reutilizáveis e como se interligam
- Mlegate  ·  Alberto Beyeler  ·  Setembro de 2026

## Slide 2

- A ideia em uma frase
- O sistema não é um conjunto de módulos independentes — é um pequeno número de motores reutilizáveis, aplicados repetidamente sob nomes diferentes.
- 1
- Cadastro único
- Um participante, um produto — múltiplos papéis por contexto, nunca cadastros duplicados.
- 2
- Vigência
- Toda decisão tem período de validade — o histórico nunca é sobrescrito, só substituído a partir de uma data.
- 3
- Motor de regras com prioridade
- A mesma lógica de classificação (mais específico vence o mais genérico) reaparece em nota fiscal, preço, comissão e mais.
- 4
- Régua de aprovação única
- Uma só árvore de aprovação, por faixa de valor, serve qualquer tipo de desvio — orçamento, crédito, operação.
- ERP Mlegate — Arquitetura Conceitual
- 2

## Slide 3

- Princípios arquiteturais transversais
- O que sustenta todos os módulos, do primeiro ao último
- Framework / plugin
- O que varia por cliente (banco, autoridade fiscal, transportadora) é plugável, não codificado.
- Vigência universal
- PK com histórico completo; obrigação sempre usa o valor válido na data do fato.
- Cadastro único
- Cliente/fornecedor/colaborador são o mesmo participante com classes diferentes.
- Pré-cadastro
- Lead e candidato ficam separados até virarem negócio fechado ou contratação.
- Motor de regras versionado
- Classificação sempre mostra o motivo, com histórico de regra.
- Régua de aprovação única
- Uma árvore, reaproveitada por qualquer gatilho de desvio.
- Tudo é insumo de BI
- Dado nasce estruturado, não texto livre — para poder ser cruzado depois.
- Auditabilidade universal
- Quem fez, quando e por quê — em todo módulo, toda exceção.
- Isolamento multi-tenant
- Dado de negócio nunca cruza tenants; só regra de configuração pode ser exportada.
- ERP Mlegate — Arquitetura Conceitual
- 3

## Slide 4

- Como as camadas se sustentam
- De baixo para cima: cada camada depende da anterior já existir
- TRANSVERSAL — BI/Analytics · GED · Folha & RH · Multi-tenant
- consome e alimenta todas as camadas abaixo
- INTERAÇÃO — CRM & Vendas · Expedição · Portal do Cliente · Gestão de Contratos/Projetos
- onde o cliente e o colaborador encontram o sistema
- FINANCEIRA — Contas a Pagar/Receber · Tesouraria · Contabilidade & Fiscal · Imobilizado
- fecha o ciclo em valor e obrigação fiscal
- OPERAÇÃO — Planejamento/Orçamento · Compras · Estoque · Produção
- o ciclo transacional principal
- NÚCLEO — cadastro único · vigência · motor de regras · régua de aprovação
- a base que todo o resto reaproveita
- ERP Mlegate — Arquitetura Conceitual
- 4

## Slide 5

- Fluxo operacional principal
- Da prospecção ao fechamento financeiro — um só caminho, sem retrabalho de dado
- Pré-cadastro / CRM
- Cotação
- Pedido de Venda
- Produção / Estoque
- Expedição
- Faturamento
- Financeiro / Contabilidade
- Compras → Estoque
- reposição / empenho
- BI / Analytics — coleta dado estruturado de cada uma dessas etapas, em tempo real
- ERP Mlegate — Arquitetura Conceitual
- 5

## Slide 6

- Núcleo transacional
- O ciclo operacional do dia a dia
- Planejamento & Orçamento
- Verba por área como referência, não bloqueio — desvio escala para a régua de aprovação.
- Compras
- Toda entrada via XML, roteada por Destinação (estoque, produção, imobilizado, despesa) por linha de pedido.
- Estoque
- Proativo: empenha para produção, reserva para venda; disponível = físico menos empenhado/reservado.
- Produção
- BOM versionado por vigência, roteiro em grafo, timesheet e cronômetro alimentando o custeio direto.
- CRM & Vendas
- Pré-cadastro → cotação → pedido; tabela de preço e comissão pelas mesmas 6 dimensões de produto.
- Expedição
- Reserva confirma a saída; frete é uma compra normal; rastreio delegado ao link da transportadora.
- ERP Mlegate — Arquitetura Conceitual
- 6

## Slide 7

- Camada financeira
- Fecha o ciclo em valor, caixa e obrigação fiscal
- Contas a Pagar & Receber
- Módulo único (não dois): mesmo motor, direção diferente. Controla adiantamento, encontro de contas e limite de crédito por grupo econômico.
- Tesouraria
- Painel de gestão prospectivo e retrospectivo — nunca só o dia corrente; sugere aplicação de sobra de caixa.
- Contabilidade & Fiscal
- Dimensões configuráveis por empresa; motor de esquemas de nota aprende classificação com motivo sempre exibido.
- Ativo Imobilizado
- Depreciações simultâneas (fiscal/acelerada/gerencial), cada uma em todas as moedas de CTA, sempre à taxa histórica.
- ERP Mlegate — Arquitetura Conceitual
- 7

## Slide 8

- Pessoas e iniciativas de ciclo longo
- Quem executa, e o que é organizado como um pacote com prazo
- Folha & RH
- Ficha única do colaborador (exames, vacinas, acidentes); ponto eletrônico calibra lacunas como sugestão, nunca automaticamente; verba tem origem legal ou interna, com nível de acesso próprio.
- Gestão de Contratos
- Um só módulo para cliente e fornecedor; reajuste por índice cadastrável; timesheet único alimenta apuração de resultado por contrato/projeto.
- Gestão de Projetos (PPM)
- Três estimativas de prazo (PERT), rede de antecessoras/sucessoras, caminho crítico; Destinação decidida por entregável, não pelo projeto todo.
- ERP Mlegate — Arquitetura Conceitual
- 8

## Slide 9

- Serviços transversais
- Os motores que todo módulo acima reaproveita, em vez de reimplementar
- Cadastro Único & Vigência
- Participante e produto com histórico versionado no PK.
- Motor de Regras
- Classificação por prioridade, com motivo sempre exibido.
- Régua de Aprovação
- Faixa de valor + papéis + suplente, para qualquer desvio.
- GED
- Retenção por classe de documento, com bloqueio judicial quando aplicável.
- BI / Analytics
- Ganho/perda por visão independente — produto, cliente, grupo econômico, mix.
- Isolamento Multi-tenant
- Dado de negócio nunca cruza tenant; só regra pode ser exportada entre empresas.
- ERP Mlegate — Arquitetura Conceitual
- 9

## Slide 10

- Quadro de dependências (simplificado)
- Quadro completo, com os 13 módulos, no documento Word em anexo
| Módulo | Consome de | Alimenta |
| Planejamento/Orçamento | Contabilidade (histórico) | Compras, Folha, régua de aprovação |
| Compras | Cadastro único, motor de regras | Estoque, Imobilizado, Fiscal |
| Estoque | Compras, Produção (empenho) | Produção, Vendas, Expedição |
| Produção | Estoque, Engenharia, Folha/RH | Estoque, Vendas, Contabilidade |
| CRM & Vendas | Estoque, Produção, tabela de preço | Expedição, Contas a Receber, BI |
| Contas a Pagar/Receber | Cadastro único, Fiscal | Tesouraria, BI |
| Contabilidade & Fiscal | Todos os módulos operacionais | Imobilizado, BI, obrigações |
- ERP Mlegate — Arquitetura Conceitual
- 10

## Slide 11

- Ordem lógica de desenvolvimento
- De baixo para cima na arquitetura em camadas — detalhamento completo no documento Word
- 0
- Fundações
- Cadastro único, vigência, motor de regras, régua de aprovação
- 1
- Núcleo operacional
- Orçamento, Compras, Estoque
- 2
- Financeira
- Contas a Pagar/Receber, Tesouraria, Contabilidade & Fiscal
- 3
- Produção & Ativos
- Produção, Engenharia/BOM, Imobilizado
- 4
- Comercial
- CRM & Vendas, Expedição, Portal do Cliente
- Pessoas (Folha & RH) e Iniciativas de ciclo longo (Contratos, Projetos) podem correr em paralelo a partir da Fase 1; BI/Analytics e Comércio Exterior fecham o roadmap por serem, por natureza, consolidadores.
- ERP Mlegate — Arquitetura Conceitual
- 11

## Slide 12

- Próximos passos
- 1
- Especificação técnica
- Modelagem de dados módulo a módulo, a partir do quadro de dependências.
- 2
- Prototipagem dos motores
- Cadastro único, vigência, motor de regras e régua de aprovação primeiro — tudo o resto reaproveita.
- 3
- Validação com o time de desenvolvimento
- Confrontar este desenho com restrições reais de implementação antes da primeira tela.
- Documento Word em anexo com o detalhamento analítico completo, módulo a módulo.