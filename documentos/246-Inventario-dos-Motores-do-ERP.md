# Inventário dos Motores do ERP: Estado e Percentual de Desenho — Documento 246

*Você pediu um documento com todos os motores, com o estado (completo, parcial ou não iniciado) e o percentual estimado de finalização. **É um levantamento: nada foi aplicado ao dicionário** (revisão 54, 1.243 entidades e 14.460 campos). Os percentuais são **estimativa minha**, com margem de cerca de 10 pontos, e medem o **desenho** nos documentos, não código.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **61 motores levantados em 5 grupos.** Estado: **30 completos, 30 parciais e 1 não iniciado**. A média simples dos percentuais é **76%**.
2. **O que "motor" quer dizer aqui.** Seguindo a sua arquitetura (documento 00b), motor é cada peça reutilizável do sistema: os serviços transversais da Fase 0 e também cada cálculo ou processo que os módulos repetem (apurar um tributo, emitir um documento, calcular a folha). Cada módulo de negócio entra pela parte que calcula ou processa, não como cadastro.
3. **Código: nenhum registrado.** Nos documentos que li não há código escrito; o projeto está na fase de dicionário e desenho. "Completo" quer dizer **desenho fechado**, e não motor pronto para uso.
4. **Os maiores buracos de desenho (50% ou menos):** auditoria universal (nº 12, 35%), isolamento multi-tenant (nº 14, 20%), BI e Analytics (nº 15, 10%), gestão de caixa (nº 37, 35%), depreciação (nº 39, 45%), TEF e SAF (nº 40, 45%), estoque proativo (empenho) (nº 44, 50%), gestão de projetos (PERT) (nº 47, 20%). A seção 5 pede a sua prioridade sobre eles.
5. **O que não trava o resto.** Os motores fiscais ficam entre 70% e 80% e nenhum está completo, mas não por falta de estrutura: o que pesa são as **cargas provisórias**, as perguntas ao contador e os materiais oficiais que ainda não chegaram.

# 2. Como li cada coluna

| Coluna | Significado |
|---|---|
| **Estado** | **Completo**: 85% ou mais (o desenho está fechado; pode restar uma pergunta curta que não muda a estrutura). **Parcial**: de 20% a 80%. **Não iniciado**: menos de 20%. |
| **%** | Estimativa do desenho: 40% pela estrutura de dados, 40% pelas regras e pelo comportamento descrito e 20% pelas cargas e pela validação (contador ou fonte oficial). Quando o motor não tem carga, a conta é 50% e 50%. Arredondado a 5 pontos (meio ponto sobe) |
| **D / R / C** | As três notas (de 0 a 100): **D** estrutura de dados no dicionário; **R** regras, fórmulas e comportamento descritos; **C** cargas e validação (traço quando não se aplica) |
| **Onde está** | O documento ou as entidades onde o desenho vive |
| **O que falta** | O que impede os 100%, com a pergunta ou o código de pendência quando existe |

**Base da estimativa.** Contei entidades e campos no modelo da revisão 54, li as seções de cada módulo, o documento 38 (perguntas em aberto) e o plano de implementação (documento 31). Para os módulos de operação e pessoas, "nada de desenho em aberto" significa que **não achei** pendência no documento 38 nem nota de escopo pendente; não reli cada módulo inteiro para este levantamento.

# 3. Visão por grupo

| Grupo | Motores | Média | Completos | Parciais | Não iniciados |
|---|---|---|---|---|---|
| A. Motores transversais (Fase 0 e arquitetura) | 15 | 74% | 10 | 4 | 1 |
| B. Motores fiscais e de documentos eletrônicos | 17 | 75% | 0 | 17 | 0 |
| C. Financeiro, tesouraria e valor | 8 | 68% | 4 | 4 | 0 |
| D. Operação e relacionamento | 14 | 81% | 12 | 2 | 0 |
| E. Pessoas | 7 | 79% | 4 | 3 | 0 |
| **Total** | **61** | **76%** | **30** | **30** | **1** |

# 4. Os motores, um a um

## A. Motores transversais (Fase 0 e arquitetura)

| Nº | Motor | Estado | % | D / R / C | Onde está | O que falta |
|---|---|---|---|---|---|---|
| 1 | Cadastro único (participante, produto/serviço, destinação, empresa, filial, grupos) | **Completo** | 85% | 90 / 85 / 70 | Fase 0, seções 4 a 6 (cerca de 75 entidades) | Q179-1 e Q179-3 (consulta à Receita, reescrita) e Q234-3 (estabelecimento sem IE) |
| 2 | Vigência (histórico por janela de datas) | **Completo** | 90% | 100 / 80 / — | Fase 0, seção 2; 294 entidades com vigência | A consulta "vigente na data D" e a gravação de período novo ficam na camada de integração (documento 31, seção 5), cuja escolha (D-12) espera você; o banco não impede janelas sobrepostas |
| 3 | Cadastro de sistema (domínios e códigos oficiais) | **Completo** | 90% | 100 / 90 / 80 | Fase 0, seção 3; 374 domínios | Alguns domínios com valores provisórios (por exemplo, `descricao_estoque_abertura_cbs`, 10 códigos) |
| 4 | Pré-cadastro (lead e candidato) | **Completo** | 95% | 95 / 90 / — | Fase 0, seção 7 | Nada de desenho em aberto |
| 5 | Motor de Regras (prioridade, motivo, aprendizado) | **Completo** | 90% | 95 / 90 / 85 | Fase 0, seção 8; 12 entidades | As regras de cada empresa são carga de configuração, que só nasce com o uso |
| 6 | Régua de aprovação | **Completo** | 95% | 95 / 90 / — | Fase 0, seção 9 | Nada de desenho em aberto |
| 7 | Dimensões contábeis, plano de contas, lançamento e saldos | **Completo** | 90% | 95 / 90 / 85 | Fase 0, seção 10 | Nada de desenho em aberto |
| 8 | Fechamento de período por bloco | **Completo** | 95% | 95 / 90 / — | Fase 0, seção 10; `Cad_Bloco_Fechamento` | Nada de desenho em aberto |
| 9 | GED (retenção, vínculo, versão) | **Completo** | 90% | 90 / 85 / — | Fase 0, seção 11 | A guarda física e a execução do descarte são de implementação, não de dicionário |
| 10 | Usuários, perfis, permissões e dado sensível | **Parcial** | 80% | 80 / 75 / — | Fase 0, seção 13 | `Cad_Usuario` guarda só login e situação; autenticação (senha, segundo fator, login único) não está no dicionário |
| 11 | Índices e taxas de câmbio | **Completo** | 85% | 95 / 85 / 75 | Fase 0, seção 15 | Fonte automática da cotação (plugin) por confirmar |
| 12 | Auditoria universal (quem, quando e por quê, em toda exceção) | **Parcial** | 35% | 35 / 35 / — | Só logs específicos: aplicação de regra, acesso a dado sensível, fechamento | Falta a trilha geral de alteração; hoje cada módulo guarda o seu |
| 13 | Plug-ins e camada de integração com o banco | **Parcial** | 65% | 80 / 50 / — | Fase 0, seção 19 (`Cad_Dfe_Driver`, `Cad_Autoridade_Fiscal`); documento 31, seção 5 | D-12: escolha do framework de banco (C#, EF Core) aguarda você |
| 14 | Isolamento multi-tenant e template entre empresas | **Parcial** | 20% | 25 / 10 / — | Só o compartilhamento dentro do grupo societário (Fase 0, seção 6) | Isolamento entre tenants, exportação só de regra e template de configuração não têm desenho |
| 15 | BI / Analytics e painéis de gestão | **Não iniciado** | 10% | 10 / 10 / — | Só o princípio (dado estruturado na origem) | Visões de ganho e perda, painéis por papel: sem entidade; fecha o roteiro por natureza (Fase 7) |

## B. Motores fiscais e de documentos eletrônicos

| Nº | Motor | Estado | % | D / R / C | Onde está | O que falta |
|---|---|---|---|---|---|---|
| 16 | Classificação fiscal e esquemas de nota (CST, cClassTrib, listas legais, regimes) | **Parcial** | 80% | 90 / 80 / 65 | Fase 0 e documentos 86, 90, 239 e 240 | Cargas provisórias (Carga52); validação pela equipe das listas do IPI, ZFM e medicamentos |
| 17 | Emissão e transmissão de DF-e (NF-e, NFC-e, NFS-e, CT-e, MDF-e, NFCom, BP-e) | **Parcial** | 80% | 90 / 80 / 60 | Documentos 34, 35, 40 a 42 e 232; `Mov_Dfe_*` | Manual da NFS-e Via v1.02 e Anexo IV (não chegaram), Q228-1 (consulta), Q234-3, teste com XML real; o DANFE é de implementação |
| 18 | Recebimento de DF-e (distribuição por NSU, manifestação, NF3e, NFGás, NFAg) | **Parcial** | 80% | 90 / 80 / 70 | `Mov_Dfe_Distribuicao`, documentos 164 e 165 | Tabela de cClass da NFGás (Q175-9) |
| 19 | Apuração de ICMS, ICMS-ST, IPI, DIFAL e CIAP | **Parcial** | 75% | 85 / 75 / 60 | Fase 2, Contabilidade & Fiscal; documentos 209 e 215 | ST de autopeças por UF (Q215-5) e textos oficiais de MT e BA para a carga |
| 20 | Apuração de PIS e Cofins | **Parcial** | 80% | 90 / 80 / 70 | Documentos 44 e 46; `Mov_Apuracao_Pis` | Linha de retenção do documento 209 espera o código de receita (C278) |
| 21 | Apuração de ISS e NFS-e | **Parcial** | 80% | 85 / 80 / 70 | Documentos 35, 41 e 46; `Mov_Apuracao_Iss`, `Mov_Iss_Guia` | Q228-1 e Q228-2 (consulta ao Comitê Gestor) |
| 22 | Apuração de CBS e IBS e Imposto Seletivo | **Parcial** | 70% | 80 / 65 / 50 | Documento 36; `Mov_Cbs_*`, `Mov_Is_*`, `Cad_Parametro_Legal_Ibs_Cbs` | Regulamentação em curso; split payment adiado para 2028 (D-N282); cargas provisórias |
| 23 | Apuração de IRPJ, CSLL, LALUR e presunção | **Parcial** | 75% | 85 / 70 / 55 | `Mov_Apuracao_Irpj`, `Mov_Lalur_*`, `Mov_Apuracao_Presuncao` | Q130-1 a Q130-5, Q132-5, Q139-1 e Q139-2, Q140-5b a 5e |
| 24 | Simples Nacional (PGDAS-D, DEFIS, DAS, apuração estadual) | **Parcial** | 75% | 85 / 75 / 65 | Documentos 33 e 37; `Mov_Simples_*` | Dúvidas de leitura dos manuais, sem pergunta formal em aberto |
| 25 | Retenções, EFD-Reinf, DCTFWeb e MIT | **Parcial** | 75% | 85 / 75 / 60 | `Mov_Reinf_*`, `Mov_Dctfweb_*`, `Mov_Mit_*` | P-08: primeiro XML real da DCTFWeb |
| 26 | EFD-ICMS/IPI | **Parcial** | 75% | 85 / 70 / 55 | Documentos 172, 175 e 176 | Q176-E4 e Q176-E5 (a verificar); tabelas do validador |
| 27 | EFD-Contribuições | **Parcial** | 75% | 85 / 75 / 60 | Documento 44 (Guia v1.35); `Mov_Efd_Contribuicoes_*` | Q226-3 (pergunta à Receita, envio seu); anexo da NT 13/2026 |
| 28 | ECD e ECF | **Parcial** | 70% | 85 / 70 / 45 | `Mov_Ecd_*`, `Mov_Ecf_*`; documentos 93, 99 e 118 | 78 tabelas dinâmicas e leiaute da ECF são carga provisória até o contador validar (D-N320 e D-N321) |
| 29 | Outras declarações (DIMOB, DOI, DES-IF, DeSTDA, CNO, LCDPR, DEAP, NAF) | **Parcial** | 70% | 80 / 65 / 50 | Documentos 33, 37 e 39 | Manuais oficiais que ainda não chegaram (seção 3.2 do documento 38) |
| 30 | Comércio exterior (DUIMP, importação e exportação) | **Parcial** | 75% | 85 / 70 / 60 | `Mov_Duimp_*` (cerca de 20 entidades), `Cad_Imposto_Exportacao_Aliquota` | Resoluções Gecex em atualização (documento 236) |
| 31 | Regimes setoriais (combustíveis e usina, ZFM e ALC, autopeças, imobiliário, rural, turismo, Mover) | **Parcial** | 75% | 85 / 70 / 55 | Documentos 170, 173, 215, 216 e 218 | Ajuste SINIEF 14/2025 lido só em fonte não oficial; Q218-8 |
| 32 | Carga e atualização das tabelas oficiais; consulta cadastral externa | **Parcial** | 70% | 85 / 65 / 60 | `Cad_Tabela_Oficial`, `Mov_Carga_Tabela_Oficial`, `Mov_Consulta_Cadastro_Externo` | P-18 (Integra Contador); 68 entidades ainda sem a carga inicial completa |

## C. Financeiro, tesouraria e valor

| Nº | Motor | Estado | % | D / R / C | Onde está | O que falta |
|---|---|---|---|---|---|---|
| 33 | Títulos a pagar e a receber (baixa, encontro de contas, crédito, reprogramação, empréstimo, limite de crédito) | **Completo** | 90% | 90 / 85 / — | Documento 08; 16 entidades | Nada de desenho em aberto |
| 34 | Conciliação bancária e extrato | **Completo** | 85% | 90 / 80 / — | Documento 09 | Nada de desenho em aberto |
| 35 | Envio e retorno bancário (CNAB, Pix API, Open Finance, exterior) | **Parcial** | 65% | 85 / 40 / — | `Mov_Remessa_Bancaria*`, `Mov_Retorno_Bancario*` | O "motor de envio" (transmissão) não foi desenhado; os dados estão prontos |
| 36 | Cobrança, aging e provisão para duvidosos | **Completo** | 90% | 90 / 85 / — | `Cad_Regua_Cobranca*`, `Cad_Banda_Aging` | Nada de desenho em aberto |
| 37 | Gestão de caixa (painel, previsão e sugestão de aplicação) | **Parcial** | 35% | 40 / 30 / — | Só o painel, como consulta sobre os dados (documento 09) | Aplicação financeira e sugestão de sobra de caixa não têm entidade |
| 38 | Multimoeda (conversão, variação cambial, CTA, reavaliação) | **Completo** | 90% | 90 / 90 / 80 | Fase 0, seção 10; `Mov_Lancamento_CTA`, `Mov_Titulo_Reavaliacao` | Nada de desenho em aberto |
| 39 | Depreciação e vida útil (inclui a tabela do Anexo I da CBS) | **Parcial** | 45% | 70 / 25 / 40 | `Mov_Ativo_Depreciacao`, `Cad_Taxa_Depreciacao_Cbs` | Desenho **todo aprovado** em 18/11/2026 (Q247-1 a Q247-14, D-N634 e D-N635) no documento 247, versão 5: n tipos de depreciação por grupo de bem, contabilização por tipo, acelerada incentivada rural e química, pausas, ajuste de valor (impairment e reavaliação) e ligação ao Anexo I. Falta aplicar (5 entidades e 51 campos, no "consolidar"), aplicar a tabela de vidas úteis do documento 248, aprovada (Anexo III da IN 1.700 em 222 linhas, +1 entidade e +18 campos, Q248-1 a Q248-6), e validar com o contador (C365 a C373). O percentual sobe quando a entidade for aplicada (o "consolidar") |
| 40 | TEF e SAF (regime da sociedade anônima do futebol) | **Parcial** | 45% | 60 / 30 / — | `Mov_Apuracao_Tef*`, `Cad_Regime_Tef_*` | O motor "quando entrar" (Q118-1) não foi desenhado |

## D. Operação e relacionamento

| Nº | Motor | Estado | % | D / R / C | Onde está | O que falta |
|---|---|---|---|---|---|---|
| 41 | Orçamento e compromisso orçamentário | **Completo** | 90% | 90 / 85 / — | Documento 02 | Nada de desenho em aberto |
| 42 | Compras (cotação, pedido, recebimento, devolução, rateio por destinação) | **Completo** | 90% | 90 / 85 / — | Documento 03; 16 entidades | Nada de desenho em aberto |
| 43 | Estoque (movimento, saldo, custo médio, lote, inventário, condição, bloqueio) | **Completo** | 90% | 90 / 85 / — | Documento 04; 20 entidades | Nada de desenho em aberto |
| 44 | Reserva, empenho e saldo disponível (estoque proativo) | **Parcial** | 50% | 55 / 40 / — | `Mov_Estoque_Reserva` (só para venda) | Não achei entidade de empenho de material para produção; o disponível é consulta derivada |
| 45 | Produção (estrutura, roteiro em grafo, ordens, apontamento) | **Completo** | 85% | 90 / 80 / — | Documento 06; 35 entidades | Capacidade e prazo sugerido ao CRM ficaram fora, por decisão |
| 46 | Custeio, rateio e custo apurado da produção | **Completo** | 90% | 90 / 85 / — | Documento 06, `Mov_Ordem_Producao_Custo_*` | Nada de desenho em aberto |
| 47 | Gestão de projetos (PERT, caminho crítico), fundida em Produção | **Parcial** | 20% | 25 / 10 / — | Só as precedências entre fases (`Mov_Ordem_Producao_Fase_Precedencia`) | Não achei as três estimativas de prazo nem o cálculo do caminho crítico |
| 48 | Preço, comissão e royalty (pelo Motor de Regras) | **Completo** | 85% | 85 / 85 / — | Documento 05, seção 3 | Nenhuma tabela própria, por decisão |
| 49 | CRM e vendas (cotação, pedido, devolução) | **Completo** | 90% | 90 / 85 / — | Documento 05; 17 entidades | Nada de desenho em aberto |
| 50 | Expedição e frete | **Completo** | 90% | 90 / 85 / — | Documento 07 | Nada de desenho em aberto |
| 51 | Manutenção de ativos (ciclo preventivo, capitalização) | **Completo** | 90% | 90 / 85 / — | Fase 0, seção 12 | Ativo concedido ficou fora, por decisão |
| 52 | Gestão de contratos (reajuste por índice, aditivo, medição, apuração) | **Completo** | 90% | 90 / 85 / — | Documento 12; 12 entidades | Nada de desenho em aberto |
| 53 | Portal do cliente | **Completo** | 85% | 85 / 80 / — | Documento 13; 1 entidade (chamado) | Lê os outros módulos por API; sem pendência de desenho |
| 54 | Jurídico, LGPD, procurações e certificados | **Completo** | 85% | 90 / 80 / — | Documento 21; 42 entidades | Nada de desenho em aberto |

## E. Pessoas

| Nº | Motor | Estado | % | D / R / C | Onde está | O que falta |
|---|---|---|---|---|---|---|
| 55 | Folha de pagamento (verbas, fórmulas, ordem de cálculo, férias, 13º, rescisão, provisões) | **Parcial** | 80% | 90 / 75 / 60 | Documento 11; `Cad_Rh_Verba`, `Mov_Rh_Folha_*` | P-38 a P-42 (NT 07/2026; regra do horista, P-42, aberta) |
| 56 | eSocial (eventos, retornos, mensagens) | **Parcial** | 75% | 85 / 75 / 60 | Documento 11; 10 entidades `Mov_Esocial_*` | NT 07/2026; primeiro retorno real |
| 57 | Ponto, jornada, banco de horas e DSR | **Completo** | 85% | 90 / 85 / 85 | Documento 11; 7 entidades | Nada de desenho em aberto |
| 58 | Recrutamento, avaliação de desempenho e estágio probatório | **Completo** | 90% | 90 / 85 / — | Documento 11 | Nada de desenho em aberto |
| 59 | Benefícios, pensão, tabela salarial e reajuste coletivo | **Completo** | 85% | 90 / 80 / — | Documento 11 | Nada de desenho em aberto |
| 60 | Ficha do colaborador, SST e ambiente de trabalho | **Completo** | 85% | 85 / 80 / — | Documento 11, seção 12 | Nada de desenho em aberto |
| 61 | Migração do sistema anterior (bases acumuladas) | **Parcial** | 55% | 70 / 40 / — | `Mov_Rh_Base_Acumulada_Migrada` | P-41 (unidade de pagamento do salário) |

# 5. O que eu levaria para decisão sua

São os assuntos sem desenho ou com desenho a menos de 50%. Não recomendo desenhar todos agora; a ordem abaixo é só uma sugestão.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q246-2 | **Envio bancário (nº 35).** Desenhar o motor de envio (CNAB, Pix API, Open Finance) junto com a escolha do framework (D-12)? | Sim, junto: os dois dependem do canal que o banco oferece |
| Q246-3 | **Auditoria universal (nº 12).** Criar uma trilha geral de alteração, ou manter só os logs específicos de cada módulo? | Trilha geral, por entidade e campo sensível; é requisito da sua arquitetura ("quem, quando e por quê") |
| Q246-4 | **Estoque proativo (nº 44).** Criar a reserva de material para produção (empenho)? | Sim, mesma estrutura da reserva da venda, para o disponível ser físico menos reservado |
| Q246-5 | **Gestão de projetos (nº 47).** Fechar o PERT e o caminho crítico dentro da Produção, como você decidiu, ou deixar fora do escopo atual? | Deixar para a fase de iniciativas de ciclo longo; hoje nenhum fluxo depende disso |
| Q246-6 | **BI e multi-tenant (nº 14 e 15).** Mantê-los para o fim do roteiro, como o documento 00 prevê? | Sim; só registrar agora o requisito de isolamento, para a camada de integração não ignorá-lo |
| Q246-7 | **Gestão de caixa (nº 37) e TEF e SAF (nº 40).** Desenhar agora? | Não: o painel de caixa já funciona como consulta e o regime da SAF só importa se a Mlegate tiver cliente nesse regime. Registrar como "adiado" no documento 38 |
| Q246-8 | **D-12 (nº 13).** Quando decidir o framework de integração com o banco (proposta do documento 31, seção 5)? | Antes do primeiro código: tudo o mais assume essa camada |

# 6. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N629 | Criar o **inventário dos motores** (documento 246), com estado e percentual estimado do desenho; levantamento apenas, sem efeito no dicionário. | Pedido de Alberto de 18/11/2026: "vamos criar um documento com todos os motores, com colunas dizendo se estão completos, parciais, ou não iniciados, com o % estimado de finalização" |

# 7. Limites

Os percentuais são julgamento meu, não medição; uma nota de 85 e uma de 90 não se distinguem com segurança. Não reli todos os módulos para este documento, e uma pendência que esteja só dentro de um módulo (e não no documento 38) pode ter escapado. Se você discordar de uma nota, diga o número do motor e eu releio o módulo correspondente. O documento deve ser reemitido quando houver nova consolidação do dicionário.

# 8. Como manter este documento

Este é o **documento de controle dos motores** (decisão de Alberto de 18/11/2026, D-N630). Ele não é substituído: continua com o número 246 e o mesmo nome de arquivo, e cada atualização sobe a versão e ganha uma linha no quadro abaixo.

| Regra | O que vale |
|---|---|
| **Quando atualizar** | A cada consolidação que mude um motor (entidades, regras ou cargas); a cada resposta que abra ou feche uma pergunta Q246; e quando chegar material oficial ou validação do contador que mude uma carga |
| **O que muda** | Só as linhas afetadas: estado, percentual, D / R / C e "o que falta". O resumo e a visão por grupo são recalculados |
| **Numeração** | Os números dos motores não são reaproveitados. Motor novo entra no fim do grupo com número novo; motor que sai fica na tabela marcado como aposentado |
| **Percentual** | Só sobe com fato: entidade aplicada, pergunta respondida, carga validada. Nada sobe por impressão |
| **Perguntas** | As Q246 abertas ficam na seção 5 e no documento 38 (seção 1.52); as respondidas saem do 38 e ficam no documento 14 |

| Versão | Data | Revisão do dicionário | O que mudou |
|---|---|---|---|
| 1 | 18/11/2026 | 54 | Primeira emissão: 61 motores, 30 completos, 30 parciais e 1 não iniciado, média de 76% |
| 2 | 18/11/2026 | 54 | Q246-1 respondida (desenhar a depreciação agora, D-N631 a D-N633); motor nº 39 aponta para o documento 247, versão 3 (n tipos de depreciação, acelerada incentivada rural; proposta, sem efeito no percentual). Demais motores sem mudança |
| 3 | 18/11/2026 | 54 | Q247-1 a Q247-10 aprovadas e C365 a C368 respondidas (D-N634); o motor nº 39 aponta para a versão 4 do documento 247 (impairment, reavaliação, pausas, outras acelerações). Percentuais sem mudança até o "consolidar" |
| 4 | 18/11/2026 | 54 | Q247-11 a Q247-14 aprovadas e C369 a C371 respondidas (D-N635): o motor nº 39 passa a ter o desenho todo aprovado (documento 247, versão 5), pendente só de aplicação. Percentuais sem mudança até o "consolidar" |
| 5 | 18/11/2026 | 54 | Recebido o Anexo III da IN 1.700; documento 248 (D-N636): tabela de vidas úteis fiscais ligada ao grupo de bem, e correção de 2 linhas da carga do Anexo I do decreto. Aplicado na revisão 55 (documento 249); percentuais sem mudança |
| 6 | 18/11/2026 | 54 | Q248-1 a Q248-6 aprovadas e C372 e C373 respondidas (D-N637): o motor nº 39 tem os documentos 247 e 248 aprovados, pendentes só de aplicação. Percentuais sem mudança até o "consolidar" |
