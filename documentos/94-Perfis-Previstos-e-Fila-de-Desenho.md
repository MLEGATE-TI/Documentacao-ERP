# Perfis de Cliente Previstos e Fila de Desenho — Documento 94

> **Resposta (27/10/2026):** Q94-5, os oito perfis sem resposta (seção 2.3) **ficam como gancho, para desenhar no futuro** (suas palavras: "fica como gancho para futuramente desenhar"). Nenhum desenho agora; os 33 nomes de ganchos seguem como estão. **Q94-6: "sim"** (lido como a recomendação: o split payment **segue adiado para janeiro de 2028**, a D-N282 **não é reaberta** e só o marketplace avança; o PSP fica previsto, sem desenho). Q94-2 (Duimp: só registra) e Q94-4 (leitura: o campo entra no cadastro) estão no documento 115. Nada foi aplicado ao dicionário.

> **Correção (04/11/2026, revisão 31, documento 157):** o B0a, o B5 e os combustíveis foram desenhados nos documentos 157, 150, 170 e 173 e **entraram no dicionário na revisão 31** (documento 174). A redução de 0,1 ponto da CBS em 2027 e 2028 é do art. 347 da LC 214 (e do art. 585 do Decreto), e os acréscimos do art. 27 têm **22 artigos** do Decreto que remetem a ele, e não "mais de dez".

> **Correção (26/10/2026, documento 115):** o texto original dizia que 78 nomes caem nos oito blocos; o certo é **67** (19 + 16 + 4 + 10 + 8 + 5 + 4 + 1), porque 67 + 11 superados + 33 ganchos = 111. A ordem e as dependências não mudam. O detalhamento da Q94-1 está no documento 115.

> **Segunda correção (26/10/2026, documento 115 v3):** este documento dizia que faltavam o texto do art. 27 e o do art. 274. **Os dois já estavam no decreto que você colou em 13/10/2026** (documento 86, seção 14.1). Faltam só a LC 225/2026, o Decreto 13.133/2026, a confirmação da consolidação com o Decreto 13.075/2026 e os Anexos I a XV da LC 214. Você também respondeu a Q94-1: o B2 é desenhado primeiro, sozinho, e depois o B0a, com os acréscimos do art. 27 (que saem do B1 e vão para o B0a).

*Cruza os 14 perfis que você marcou como "previsto" na Q70-1 (21/10/2026) com as lacunas do Decreto 12.955/2026 que o documento 70 apontou, e propõe uma ordem de desenho. É um relatório e uma proposta: **nada foi alterado no dicionário** e nenhuma entidade nova nasce daqui. Cada bloco só vira desenho (documento próprio, com lista de campos) quando você escolher a ordem. Os nomes de entidade são os que as leituras do documento 70 propuseram; as duplicatas se unem no desenho.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- Você marcou **14 perfis como "previsto"** e **nenhum como "hoje"**: prestador de serviço de pagamento (PSP), marketplace, seguradora, plano de saúde, SAF ou clube, cooperativa, agência de turismo, bar/restaurante/hotel, venda a órgão público, Zona Franca de Manaus ou ALC, montadora, importador, exportador e comercial exportadora. **Oito perfis ficaram sem resposta** (seção 2.3).
- Como o princípio do projeto é não limitar o tipo de cliente, **tudo entra mais cedo ou mais tarde**. O que a resposta decide é a ordem. Como nenhum perfil é "hoje", não há cliente esperando; a ordem é sua.
- Dos nomes de entidade que o Anexo A do documento 70 propôs, **111 ainda não existem no modelo** (as revisões 17 a 19 já criaram 5 dos nomes: lista legal, depreciação, operação equiparada, agência de turismo e auto de infração). Dos 111, **67 caem nos oito blocos dos seus perfis**, **11 foram superados** por decisões que você tomou (por exemplo, a D-N284 decidiu que o ERP só registra o auto de infração, sem calcular multa) ou são nomes de entidade que já existe, e **33 não têm perfil marcado** (ganchos).
- Proponho oito blocos (B0 a B7) e a ordem **B2 e B0, B1, B5, B3, B4, B6, B7** (seção 4). Sete perguntas (seção 5).

# 2. Seus perfis contra as lacunas

## 2.1 Os 14 perfis marcados "previsto"

| Perfil | O que o decreto exige e o dicionário não tem | O que o dicionário já tem | Bloco |
|---|---|---|---|
| Importador | Processo da importação: valor aduaneiro, componentes da base, câmbio, fato gerador, pagamento, crédito só da CBS paga, responsável (transportadora, armazém geral, courier) | Dados da DI e da Duimp por item da nota (`Mov_Nota_Fiscal_Saida_Item_Importacao` e a adição) | B1 |
| Exportador | Comprovação em 180 dias (averbação da DU-E, prorrogação, devolução simbólica, conversão em operação onerosa), suspensão com prazo | Dados de exportação por item da nota (`Mov_Nota_Fiscal_Saida_Item_Exportacao`) | B1 |
| Comercial exportadora | Suspensão e alíquota zero com prazo, vínculo com o fornecedor, acréscimos do art. 27 se a exportação não ocorrer | `Cad_Aliquota.Eh_Suspensao` (D-N277) | B1 |
| Venda a órgão público | Redutor por ano (art. 601) e regra por tipo de ente (arts. 439 a 443); estatal fica fora | `Mov_Nota_Fiscal_Saida_Compra_Governamental` (tipo do ente e redutor por nota) | B3 e B2 |
| Zona Franca de Manaus ou ALC | Importação com suspensão de 48 meses e conversão em isenção, internamento, produtos por regra, transição própria, habilitação Suframa | `Mov_Credito_Presumido_Zfm` (sem saldo nem expiração de cinco anos), tipo de crédito presumido no item | B3 |
| Seguradora | Regime específico de serviços financeiros (arts. 269 a 329): aferição mensal, base negativa compensável, deduções por regime, DeRE por segurado | `Cad_Participante_Regime_Especifico`, `Cad_Cod_Trib_Dere`, `Cad_Redutor_Base_Dere`, mapeamento de contas | B4 |
| Plano de saúde | Arts. 330 a 346: coeficiente de rateio, DeRE com titulares e dependentes, glosa | Os mesmos de B4 e o lado REINF (`Mov_Reinf_Rendimento_Plano_Saude`) | B4 |
| Cooperativa | Transferência de crédito do cooperado e cálculo do limite (arts. 394 e 395) | `Cad_Cooperativa_Associado`, `Mov_Cooperativa_Listagem_Envio` | B5 e B2 |
| SAF ou clube | Apuração mensal por caixa (arts. 421 a 429) | Nada | B5 |
| Agência de turismo | Falta o tipo do serviço da agência (intermediação ou fornecimento direto) | `Mov_Agencia_Turismo_Repasse` (revisão 19, D-N283) | B5 |
| Bar, restaurante e hotel | Exclusão da gorjeta da base, limite de 15% (art. 399, ambíguo); locação por temporada até 90 dias (art. 410) | Nada específico (a locação imobiliária de longo prazo existe) | B5 |
| Montadora | Regime automotivo (arts. 518 a 527): percentual por ano e mês, apuração, uso do crédito pela fração dos débitos próprios, devolução | Nada | B6 |
| Marketplace | Responsabilidade da plataforma e vínculo plataforma-fornecedor (`Cad_Participante_Plataforma_Fornecedor`) | Nada | B7 |
| PSP | Arts. 579 a 581: transações, segregação, recolhimento, tolerância mensal; é um módulo inteiro | Só `Mov_Titulo_Baixa.Canal_Split` | B7 |

## 2.2 O que já foi feito desde o documento 70

Entraram até a revisão 19: a lista legal por NCM e NBS (`Cad_Lista_Legal_Item`, `Cad_Taxa_Depreciacao_Cbs`, D-N269), a idoneidade do documento fiscal (D-N272), o redutor da DeRE por `codTrib` (D-N273, ainda sujeito ao documento 96), a suspensão como marcador na alíquota (D-N277), a nota de entrada com crédito presumido e a categoria (D-N280, D-N281, D-N334), a agência de turismo (D-N283), o auto de infração (D-N284), brindes, doações e retiradas (D-N285 a D-N290) e a parte relacionada pela vinculação existente (D-N288).

**Ainda sem entidade e sem decisão de campos:** qualificação do participante (a D-N268 diz que tem de ser guardada, mas a estrutura não foi confirmada), Comércio Exterior (D-N267 decidiu o módulo completo; o desenho está pendente, com a pergunta da Duimp aberta), e todo o resto dos blocos abaixo.

## 2.3 Os oito perfis sem resposta

Distribuidora de energia, água, gás ou telecomunicações (cashback, arts. 492 a 514); câmbio (regime financeiro); combustíveis (arts. 259 a 268); loteria ou aposta (prognósticos, arts. 347 a 358); ensino superior (ProUni, arts. 516 e 517); Repetro; Reporto (Anexos II e III do decreto, regimes aduaneiros); e PNCT (arts. 551 e 578). **Não decidi nada por eles.** Pelo princípio de não limitar o cliente, eles continuam como ganchos sem desenho; as 33 entidades sem perfil (seção "Ganchos") são deles.

# 3. Os blocos

A contagem de nomes é a do Anexo A do documento 70, **antes** de unir as duplicatas.

## B0. O que vale para qualquer cliente (19 nomes)

Restante da base de cálculo e do fato gerador (**arts. 11, 13 e 57 a 64 do Decreto 12.955**; correção de 04/11/2026, revisão 30: essa é a numeração do **Decreto**, não da LC 214, em que a base de cálculo é o art. 12 e o uso e consumo pessoal é o art. 57; no Decreto, a base está nos arts. 13 e 14 e o uso pessoal nos arts. 62 a 64): `Cad_Regra_Base_Calculo_Cbs`, `Cad_Regra_Fato_Gerador_Cbs`, `Mov_Fornecimento_Antecipacao`; valor de mercado (`Cad_Regra_Valor_Mercado`, `Mov_Valor_Mercado_Apuracao`, `Cad_Valor_Mercado_Locacao_Parametro`); ajuste genérico de operação (`Mov_Cbs_Ajuste_Operacao` e efeito); uso e consumo pessoal; devolução de venda; transição de 2026 (`Mov_Cbs_Transicao_2026_Periodo`) e o campo da redução de 0,1 ponto da alíquota de 2027 e 2028 (**art. 347 da LC 214 e art. 585 do Decreto 12.955**; correção de 04/11/2026, revisão 31: o documento 157 mostrou que a LC não tem art. 585); entrega do XML ao adquirente e evento cadastral da filial; selo de conformidade (LC 225). Mais o **lado de quem toma o serviço financeiro**, que atinge qualquer cliente com empréstimo, leasing de frota ou antecipação de cartão: `Mov_Credito_Servico_Regime_Especifico`, `Cad_Arrendamento_Mercantil`, `Mov_Arrendamento_Parcela`, `Mov_Antecipacao_Recebivel`; e o plano de saúde dos empregados (`Mov_Rh_Beneficio_Credito_Cbs`).

*Depende de:* da LC 225 (selos). O art. 27 (acréscimos) já está no decreto colado e, pela Q115-2, o parâmetro passa a ficar no B0a. *Observação:* é o bloco que o documento 70 recomendou desenhar primeiro.

## B1. Comércio exterior completo (16 nomes)

Importação (`Mov_Importacao`, itens e componentes da base), regras (`Cad_Regra_Comex_Cbs`, `Cad_Regime_Suspensao_Parametro`), suspensão com eventos (`Mov_Suspensao_Cbs` e evento), exportação (`Mov_Declaracao_Exportacao`, `Mov_Exportacao_Comprovacao`, suspensão da exportação), drawback (`Cad_Ato_Concessorio`, itens, vínculo), acréscimos legais (`Cad_Acrescimo_Legal_Cbs`) e remessa internacional. Decidido: **módulo completo** (D-N267) e suspensão **sem habilitação** quando for o caso do art. 196 (D-N277).

*Depende de:* a pergunta da **Duimp** (o ERP gera e transmite ou só registra o que o despachante devolve?) (o art. 27 já está no decreto colado). A qualificação do participante (B2) entra para o responsável na importação.

## B2. Qualificação do participante perante a CBS (4 nomes, que viram uma entidade)

`Cad_Participante_Qualificacao_Cbs`, `Cad_Participante_Enquadramento_Cbs`, `Cad_Participante_Imunidade`, `Cad_Participante_Fundo` são a mesma ideia com nomes diferentes. Proposta já dada no documento 86: **uma entidade com vigência e tipo em domínio aberto**, lida pelo Motor (condomínio, consórcio, SCP, nanoempreendedor, fundo, produtor rural, transportador autônomo, administração pública, entidade de saúde, ICT e outros), mais `Participa_Pnct` no perfil fiscal. Você decidiu que a qualificação **tem de ser guardada** (D-N268), mas não confirmou a estrutura.

*É pré-requisito de* B3 (tipo do ente), B5 (cooperado) e B1 (responsável na importação).

## B3. Compras governamentais e Zona Franca (10 nomes)

`Cad_Redutor_Compra_Governamental`, `Cad_Regra_Compra_Governamental`; ZFM e ALC: `Cad_Regra_Zfm_Alc_Cbs`, `Cad_Zfm_Alc_Produto_Regra`, `Cad_Cronograma_Transicao_Zfm`, `Cad_Area_Incentivada` (e municípios), `Mov_Zfm_Alc_Internamento`, `Mov_Importacao_Suspensao_Zfm_Alc`, `Mov_Habilitacao_Suframa_Ocorrencia`; e o saldo e a expiração de cinco anos do crédito presumido ZFM (hoje `Mov_Credito_Presumido_Zfm` não tem).

*Depende de:* B2 (tipo do ente) e B1 (a importação com suspensão da ZFM usa o processo de importação).

## B4. Regimes específicos financeiro, seguro e saúde (8 nomes)

`Cad_Deducao_Regime_Especifico`, `Cad_Regime_Especifico_Parametro`, `Cad_Regime_Aliquota_Soma`, `Mov_Regime_Especifico_Afericao`, `Mov_Regime_Especifico_Saldo_Dedutivel`, `Mov_Dere_Individualizacao` (e dependente), `Cad_Coeficiente_Rateio_Plano_Saude`. É o lugar onde nasce a **apuração completa da DeRE**, hoje inexistente no dicionário, e onde a proposta do documento 96 (redutor por contas) encaixa.

*Depende de:* aprovação do documento 96, e da definição de segurado, titular e dependente na DeRE. Seguradora e plano de saúde entram juntas.

## B5. Regimes setoriais (5 nomes, mais um campo pendente)

Cooperativa (`Mov_Cooperativa_Transferencia_Credito`, `Mov_Operacao_Cooperativa`), SAF e TEF (`Cad_Regime_Tef_Parametro`, `Mov_Apuracao_Tef` e itens). Sem nome no documento 70: a gorjeta de bar, restaurante e hotel (art. 399, ambíguo entre os §§ 1º e 3º), a locação por temporada de até 90 dias (art. 410) e o **tipo de serviço da agência de turismo** (`Tipo_Servico_Agencia`: intermediação ou fornecimento direto), que faltou na revisão 19. A CBS de 2029 a 2032 foi omitida no art. 425 (SAF): não deve ser inventada.

*Depende de:* B2 (cooperado, tipo de ente do clube).

## B6. Regime automotivo (4 nomes)

`Cad_Credito_Automotivo_Percentual`, `Mov_Credito_Automotivo_Apuracao`, `Mov_Credito_Automotivo_Debitos_Proprios`, `Mov_Credito_Automotivo_Devolucao`. Percentuais por ano e mês de fruição, uso do crédito pela fração dos débitos próprios e devolução com F1, F2 e F3 (arts. 518 a 527).

*Depende de:* B1 (importação) e de habilitação (a habilitação genérica já existe).

## B7. Marketplace e PSP (1 nome, mais o módulo do PSP)

`Cad_Participante_Plataforma_Fornecedor` para o marketplace. O lado do **prestador de pagamento** (arts. 579 a 581) é um módulo inteiro e depende do split payment, que você **adiou para janeiro de 2028** (D-N282). O "previsto" do PSP é justamente o gatilho que a D-N282 pedia ("reabrir com cliente prestador de pagamento"), por isso pergunto na Q94-6, sem reabrir sozinho.

## Superados ou nomes que já existem (11 nomes)

`Cad_Anexo_Beneficio_Ncm` e `Cad_Classificacao_NCM` (existem como `Cad_Lista_Legal_Item` e `Cad_Classificacao_Mercadoria`); `Cad_Cronograma_Transicao_Tributaria` (o nome real é `Cad_Calendario_Transicao`, e o campo da redução de 0,1 ponto está em B0); `Cad_Participante_Relacao` (a D-N288 usa `Cad_Participante_Vinculacao`); e sete nomes de penalidade e procedimento fiscal (`Mov_Auto_Infracao_Exigencia`, `Cad_Penalidade_Cbs`, `Cad_Cbs_Penalidade_Parametro`, `Cad_Regra_Reducao_Multa_Pagamento`, `Mov_Procedimento_Fiscal`, `Mov_Regime_Especial_Fiscalizacao` e a medida), que a D-N284 deixou de fora ao decidir que o ERP só registra.

## Ganchos: 33 nomes sem perfil marcado

Combustíveis (4: `Cad_Combustivel_Cbs`, `Cad_Combustivel_Mistura`, `Mov_Combustivel_Mistura_Apuracao`, `Cad_Participante_Agente_Combustivel`); cashback (4); habilitações detalhadas, que servem a Repetro, Reporto, REIDI e semelhantes (10: `Cad_Habilitacao_Atividade`, `Cad_Habilitacao_Bem_Classificacao`, `Cad_Habilitacao_Bem_Incentivado`, `Cad_Habilitacao_Compromisso`, `Cad_Habilitacao_Imovel`, `Cad_Habilitacao_Produto`, `Mov_Habilitacao_Apuracao_Anual`, `Mov_Habilitacao_Compromisso`, `Mov_Habilitacao_Compromisso_Realizado`, `Mov_Habilitacao_Requisito`); imobiliário e bens usados de pessoa física (5); ProUni, turista estrangeiro, fidelidade, rota aérea regional, consulta tributária, beneficiário de tratado, viajante e lista legal por atividade (10). Ficam como gancho até alguém marcar o perfil.

# 4. Ordem sugerida

| Ordem | Bloco | Por quê |
|---:|---|---|
| 1 | **B2** (qualificação) e **B0** (qualquer cliente) | B2 é pré-requisito de B1, B3 e B5; B0 vale para todos e foi a recomendação do documento 70 |
| 2 | **B1** (comércio exterior) | Três dos seus 14 perfis (importador, exportador, comercial exportadora) e o maior bloco; a D-N267 já decidiu o escopo |
| 3 | **B5** (setoriais) | Quatro perfis (cooperativa, SAF, agência, bar/restaurante/hotel), sem dependência pesada além de B2 |
| 4 | **B3** (governo e ZFM) | Dois perfis; depende de B2 e B1 |
| 5 | **B4** (financeiro, seguro e saúde) | Dois perfis; depende do documento 96 (o art. 274 já está no decreto colado) |
| 6 | **B6** (automotivo) | Um perfil; depende de B1 |
| 7 | **B7** (marketplace e PSP) | O PSP depende do split (adiado para 2028); o marketplace pode vir antes se você quiser |

A ordem é uma sugestão; se você preferir outra, os documentos seguem a sua.

# 5. Perguntas para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q94-1 | Aprova os oito blocos e a ordem da seção 4? Qual desenho eu escrevo primeiro? | B2 e B0 juntos, depois B1 |
| Q94-2 | **Duimp:** o ERP gera e transmite, ou só registra o que o despachante devolve? (aberta desde a D-N267; muda o tamanho de B1) | Só registrar |
| Q94-3 | Confirma a estrutura única `Cad_Participante_Qualificacao_Cbs`, com vigência e tipo em domínio aberto (D-N268 só confirmou a necessidade)? | Sim |
| Q94-4 | Agência de turismo: acrescentar `Tipo_Servico_Agencia` {intermediação, fornecimento direto}, que o decreto exige e a revisão 19 não tem? | Sim, em B5 |
| Q94-5 | ~~Os oito perfis sem resposta (seção 2.3): ficam como gancho sem desenho até você marcá-los, ou quer marcar algum agora?~~ **Respondida em 27/10/2026: gancho, para desenhar no futuro** | Gancho |
| Q94-6 (**respondida em 27/10/2026: sim, split adiado**) | PSP e split: o "previsto" do PSP reabre a D-N282, ou o split segue adiado para 2028 e só o marketplace avança? | Split adiado; marketplace pode avançar |
| Q94-7 | Quais textos da Q70-13 você consegue mandar primeiro? LC 225 e Decreto 13.133 (B0b e ganchos), a confirmação da consolidação com o Decreto 13.075 e os **Anexos I a XV da LC 214** (a carga da lista legal nasce vazia sem eles). O art. 27 e o art. 274 **já estavam no decreto colado e saíram da pergunta** | Anexos da LC 214 |

# 6. Limites

A classificação artigo a artigo é a do documento 70, feita por leituras independentes e **só reconferida em seis achados**. A associação dos nomes de entidade aos blocos é minha (por assunto, não por decisão sua). A contagem de nomes **não** é a de entidades finais: várias descrevem a mesma coisa. O texto do decreto usado é o que você colou, sem as consolidações posteriores (Decreto 13.075/2026) nem o Decreto 13.133/2026. Nada foi conferido nas fontes oficiais.
