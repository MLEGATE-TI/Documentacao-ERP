# Manuais Oficiais da Receita Federal: EFD-ICMS/IPI, PGDAS-D, DOI, CNO, LCDPR, DEAP, e-Processo, NAF e Mafon — Documento 37

*Leitura dos 17 manuais que Alberto enviou em 05/10/2026 e o que eles pedem do dicionário. Relatório de achados e proposta: nada foi consolidado. O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 12/10/2026 (documento 51): chegou o texto da LC 224/2025, e o art. 8º confirma o imposto retido de 17,5% sobre o JCP desde 01/01/2026. Chegou também o Mafon 2024, que foi comparado com o 2025: a tabela de códigos e percentuais da retenção federal é idêntica nas duas, e a regra nova da dispensa de R$ 10 por pagamento está na decisão D-N121 do documento 51.*

# 1. Resumo

Os 19 arquivos recebidos traziam duas cópias de materiais que já estavam no Projeto (o manual do CNO e o da DCTFWeb); elas foram removidas. Restaram 17 manuais, de pesos muito diferentes para o ERP.

Três deles mudam o desenho de verdade: o **Guia Prático da EFD-ICMS/IPI** (principalmente o Bloco K, de produção e estoque), o **Manual do PGDAS-D** (apuração e DAS do Simples) e o **Manual do CNO** (cadastro de obras). Dois outros trazem lacunas menores, mas reais: o **Mafon** (retenções na fonte por código de receita) e o **e-Processo** (ciência de intimações e juntada de documentos). Os demais, **DOI, LCDPR, DEAP e NAF**, pouco ou nada pedem do dicionário, salvo se a Mlegate tiver clientes de um perfil específico.

Este documento também **corrige duas premissas já escritas**: o DAS avulso do Simples (D-N41, documento 36) e a descrição da retenção de IR em venda a órgão público (documento 10, seção 11).

A proposta soma **cerca de 27 entidades novas** (estimativa, a recontar na revisão 3, junto com as propostas dos documentos 33 a 36 que ainda não foram consolidadas) e **9 decisões** (D-N42 a D-N50), que estão na seção 9. Os módulos de Produção e Estoque são os mais afetados.

# 2. Fontes lidas e relevância

| Fonte | O que é | Impacto no dicionário |
|---|---|---|
| Guia Prático EFD-ICMS/IPI v3.2.2 (11/02/2026, 362 p.) | Leiaute e regras da escrituração fiscal de ICMS e IPI | **Alto** para Produção, Estoque e apuração estadual |
| Manual do PGDAS-D (versão de 17/06/2025, 139 p.) | Apuração mensal e DAS do Simples, mais a DEFIS | **Alto** para as entidades `Mov_Simples_*` |
| Manual do CNO v1.1 (2019, 49 p.) | Cadastro Nacional de Obras | **Médio**: há cliente de construção civil |
| Mafon 2025 (258 p.) | Manual do IRRF e retenções por código de receita | **Médio**: parâmetros de retenção |
| e-Processo no e-CAC (fev/2022, 73 p.) | Processos digitais, ciência e juntada | **Médio**: intimações e procuração |
| Manual da DEAP e 5 roteiros | Opção pelo Regime Especial de Atualização Patrimonial (Rearp, Lei 15.265/2025) | **Baixo**: Darf avulso e restituição fora do PER/DCOMP |
| DOI (3 manuais, abr/2025) | Declaração dos cartórios sobre operações imobiliárias | **Baixo**: só se houver cliente cartório |
| LCDPR v1.3 (31 p.) | Livro caixa do produtor rural pessoa física | **Baixo**: só se houver produtor rural PF |
| Manual NAF v2.0 (120 p.) | Atendimento de cidadãos e MEI pelos núcleos de apoio fiscal | **Quase nulo**: certidões fiscais e parcelamento |

**Limites da leitura.** O texto do manual de preenchimento da DOI veio com letras perdidas, e foi lido por OCR nas páginas principais. Das 258 páginas do Mafon foram lidos o sumário e as páginas de maior interesse (58, 192 a 196, 205, 206 e 218 a 245); o restante ficou como não verificado. Os Anexos I a V do PGDAS-D são imagens e não foram extraídos. O Guia da EFD **não reproduz** as tabelas externas (4.5.4, 5.1.1, 5.2, 5.3, 5.4, 5.6, 5.7, 5.8 e 5.9.1), que ficam no portal do SPED.

# 3. Correções a premissas já escritas

| Onde | O que estava escrito | O que a fonte diz | Proposta |
|---|---|---|---|
| Documento 36, seção 9 (D-N41) | O DAS avulso não tem apuração do PGDAS-D | O manual do PGDAS-D (seção 6.8.4, p. 40) diz que "deverá existir uma apuração transmitida" para o período do DAS avulso | `ID_Apuracao_Simples` fica **obrigatório** no avulso e opcional só no DAS de auto de infração, que o manual não trata |
| Documento 36, seção 9 | Origem do DAS: pgdas_d, avulso, auto_infracao | O manual (p. 50) lista também DAS de cobrança, medida judicial e processo | Domínio de `Origem` ganha cobrança, medida_judicial e processo |
| Documento 10, seção 11 | Retenção em venda a órgão público: "IR 15% sobre a base", total "em torno de 9,45%" | O Mafon (p. 241 a 243) mostra IR de 0,24% a 4,8% conforme o código de receita; o total de 9,45% do código 6190 é 4,8 (IR) + 1,0 (CSLL) + 3,0 (Cofins) + 0,65 (PIS) | Corrigir só o texto; a estrutura de `Mov_Titulo_Retencao` não muda |
| Documento 33 | A DEFIS acaba em 2027 | O manual do PGDAS-D ainda fixa o prazo de 31/03 (p. 82) e bloqueia o PGDAS-D de março em diante sem a DEFIS do ano anterior | Confirmar com a norma de 2026; enquanto isso, o ERP precisa da regra de bloqueio |
| Documento 32 | Cita o "Guia 3.2.3" como fonte secundária | O guia em mãos é a versão 3.2.2 (11/02/2026); a 3.2.3 não consta | Conferir a versão vigente no portal do SPED |

**JCP (Aliquota_Irrf_Jcp, documento 20).** O Mafon 2025 traz 15% de IRRF sobre juros sobre capital próprio (p. 58) e o dicionário carrega 17,5% como "não confirmado". O Mafon é anterior a 2026. Várias fontes secundárias indicam que a Lei Complementar 224/2025 elevou a alíquota para 17,5% a partir de 2026, o que condiz com o dicionário. **Atualização de 12/10/2026:** o texto da lei chegou e confirma. O art. 8º da LC 224 dá ao § 2º do art. 9º da Lei 9.249 a alíquota de 17,5% "na data do pagamento ou do crédito", com efeitos desde 01/01/2026 (art. 14, III); o rótulo "não confirmado" sai na consolidação, e os 15% do Mafon 2025 ficam como a versão anterior, até 31/12/2025. A estrutura, que tem vigência, já comportava a mudança.

**Chave de 50 posições contra 44 da EFD.** O dicionário guarda a chave com 50 posições (decisão D-N1, que também comporta a chave da NFS-e nacional); a EFD usa 44 para NF-e e CT-e (campo `CHV_NFE`, N44). Não é erro: é regra de exportação, que o desenho deve registrar.

# 4. EFD-ICMS/IPI (Guia 3.2.2)

## 4.1 Regras gerais

O perfil A, B ou C é definido pelo fisco estadual, e o prazo de entrega vem da legislação de cada UF (Guia p. 3, 5 e 18). Assinatura com certificado A1 ou A3 e validação no PVA antes do envio (p. 3 e 4). Retificação sem autorização até o último dia do 3º mês seguinte ao período; depois, só com autorização ou dispensa da SEFAZ (p. 5). Guarda do TXT transmitido e do recibo pelo prazo dos documentos fiscais (p. 4 a 6). O Bloco B (ISS) é exclusivo do Distrito Federal.

## 4.2 Reforma tributária na EFD (Seção 10, p. 7, e C100/C190)

A EFD ICMS/IPI **não serve à apuração de IBS, CBS e IS**. Esses tributos entram no valor total do documento (`C100.VL_DOC`), **exceto no exercício de 2026**, e não entram no valor da operação dos registros analíticos (`C190.VL_OPR`). Documento que traga **somente** os novos tributos não é escriturado (p. 62 e 63). O Guia **não traz nenhum registro ou campo novo** para IBS, CBS ou IS. O dicionário já guarda os tributos novos por item (`Mov_Apuracao_Tributo_Item`); falta registrar a regra de exportação (D-N44).

## 4.3 Cobertura dos blocos 0, B e C

Cobertos: 0000, 0015, 0150, 0175, 0190, 0206, 0500, 0600, C101, C190 e C191. Parciais: 0005, 0100, 0200, 0205, 0220, 0300/0305, 0400, 0450, C100, C110 a C116, C120, C140/C141, C170, C176 e C197. Lacunas: 0002, 0210, 0221, 0460, C105, C175, C177, C195, C300 a C495, C500/C510/C590, C800 a C890 e o Bloco B no DF.

As lacunas que mais pesam, em ordem:

1. **Código de negócio do item.** O registro 0200 exige `COD_ITEM` (até 60 caracteres, único, não reutilizável) e o 0205 o código anterior. O dicionário só tem `ID_Produto_Servico`.
2. **Campos do C100/C170 sem lugar no dicionário:** `IND_MOV`, `VL_ABAT_NT`, `COD_NAT` e `COD_CTA` por item, e `IND_PGTO` na entrada.
3. **Ajuste por documento (C197) e tabela 5.3.** O documento 33 cita as tabelas 5.1.1 e 5.4, mas o C197 usa a **5.3**. Faltam também C195, 0460 e a sub-apuração.
4. **Fator de conversão (0220).** O dicionário deixa o fator variar por vigência; o Guia (p. 41 e 42) exige novo código de unidade quando o fator muda.
5. **Aquisição de energia, água e gás (C500/C590).** Só é lacuna relevante se a empresa tomar crédito de ICMS nessas compras (o documento 32 trata a NF3e como fora do núcleo).

## 4.4 Bloco K (produção e estoque)

O Bloco K controla mensalmente produção, consumo de insumos e estoque. É obrigatório para industriais, equiparados e atacadistas; o Simples Nacional é dispensado (p. 265). O perfil A, B ou C **não** o diferencia; o que muda é o leiaute do `K010`: 0 simplificado, 1 completo e 2 restrito aos saldos de estoque (p. 266). Registros como K210/K215, K235, K255, K260/K265, K275, K292 e K302 só são exigidos no leiaute completo. **Não existe registro de perda** no Bloco K: a perda normal ficava no registro 0210, descontinuado.

| Registro | Exige | Situação no dicionário |
|---|---|---|
| K100 | Período do bloco (prevalece o mais curto no IPI decendial) | Parcial: `Cad_Periodo_Fechamento_Filial` |
| K200 | Saldo por item com propriedade (0 próprio em poder, 1 próprio em terceiros, 2 de terceiros em poder) e participante | Parcial: o saldo é por local e lote, **sem propriedade nem participante**; material do encomendante fica fora do saldo (documento 06, §8.2) |
| K230/K235 | Produção e consumo por ordem, com código de OP de 30 posições; OP aberta repete todo mês | Parcial: `Mov_Ordem_Producao` e `_Item`; falta apontamento por período e código de OP de 30 posições |
| K250/K255, K300 a K302 | Industrialização por terceiros | Parcial: remessa e retorno existem; falta data de produção e variação do estoque em terceiro |
| K290 a K292 | Produção conjunta, só coprodutos | Parcial: subprodutos têm rateio; falta marcar coproduto contra subproduto |
| K210/K215 | Desmontagem | **Lacuna** |
| K220 | Reclassificação de item (troca de código) | **Lacuna**: só há transferência |
| K260/K265 | Reprocesso ou reparo no próprio estabelecimento | **Lacuna**: o documento 06 trata reprocesso como nova ordem |
| K270/K275/K280 | Correção de apontamento de período anterior, só entre dois inventários | **Lacuna**: o documento 06 diz que vira nova ordem |
| K010 | Tipo de leiaute (0, 1 ou 2) | **Lacuna**: sem parâmetro |

O Guia também registra uma inconsistência: o início do Bloco K aparece como 2016 (p. 265) e como janeiro de 2017 (p. 7).

## 4.5 Blocos D, E, G, H, 1 e 9

A apuração (E), o CIAP (G) e o inventário (H) existem só como proposta do documento 33 (seção 6.1), ainda não consolidada. Dela faltam: separação entre ajuste de documento e ajuste de apuração e o débito especial (`DEB_ESP`) no E110/E210; DIFAL e FCP em contas separadas no E310; detalhe de documento de arrecadação e processo (E112, E115, E230, E312); os quatro componentes de crédito do CIAP (operação, ST, frete e diferencial) e os registros G126 e G140; e o H030, obrigatório quando o motivo do inventário é 06 (controle de ST). Os registros do Bloco D de transporte (D100/D190) estão parciais; D500 e a NFCom adquirida ficam como lacuna de baixa prioridade. A sub-apuração (1900 a 1926) só é necessária se a UF exigir. O Bloco 9 só traz contagens de geração.

# 5. PGDAS-D (Simples Nacional)

O manual traz o fluxo completo: opção pelo regime de caixa ou competência (anual e irretratável), receita do período em mercado interno e externo, segregação por estabelecimento e atividade (14 grupos), qualificações (ST, monofásico, exigibilidade suspensa, isenção, redução, valor fixo e outras), folha para o Fator r, geração do DAS, DAS avulso e de cobrança, retificação, malha fiscal, a multa por atraso na entrega (MAED) e a DEFIS. Importante: apesar do nome do arquivo, a capa é de **17/06/2025**, e o manual **não menciona** IBS, CBS, regime híbrido, NFS-e nacional nem o Integra Contador (a via de API de D-N3 não se valida por esta fonte).

## 5.1 Lacunas em `Mov_Simples_*`

| Tema | Lacuna | Fonte |
|---|---|---|
| Estabelecimento | `Mov_Simples_Apuracao_Atividade` não tem filial | p. 23 e 52 |
| Parcelas por tributo | Só existe um `Tipo_Segregacao` por linha; o manual pede várias parcelas (ST, monofásico, isenção e redução com valor e percentual, exigibilidade suspensa com processo e vara, valor fixo) | p. 26 a 34 |
| Município e UF | Falta o ente de ISS e ICMS por tributo e por linha de DAS | p. 26, 27 e 40 |
| Receita | Faltam receita recebida (caixa) e RBA, RBAA e RBT12 proporcional separados em mercado interno e externo | p. 8, 16, 51 e 79 |
| DAS | Só guarda totais; o DAS de cobrança agrupa **vários períodos** e `ID_Apuracao_Simples` é único; faltam data limite, DAS complementar e o diferido abaixo de R$ 10 | p. 36 a 43 e 63 |
| Malha | Não há situação retida, intimada, liberada, rejeitada, nem as comunicações do DTE-SN | p. 56 a 62 |
| MAED | Multa de 2% ao mês, teto de 20% e mínimo de R$ 50, sem entidade | p. 18 e 19 |
| Impedimento | Falta UF e data de início do efeito do excesso de sublimite | p. 79 e 80 |
| Não optante com processo | A opção não guarda número do processo nem o ente | p. 13 |
| DEFIS | Há recibo e sócios; faltam quase todos os campos | p. 82 a 103 |

## 5.2 Regras que o cálculo do ERP precisa documentar

Fator r: FS12 dividido por RBT12, com resultado 0,01 quando FS12 é zero e 0,28 quando FS12 é positivo e RBT12 é zero, em duas casas sem arredondar (p. 76 e 77). ISS efetivo limitado a 5%, com redistribuição aos tributos federais (p. 74). Início de atividade: RBT12 proporcional ao mês, depois à média (p. 78). DAS abaixo de R$ 10 não é gerado e o valor é diferido (p. 38). Retificar receita obriga retificar os períodos seguintes até dezembro do ano seguinte (p. 54). PGDAS-D de março em diante é bloqueado sem a DEFIS do ano anterior (p. 82).

**Defasagens possíveis do manual:** limites de R$ 360 mil, R$ 3,6 milhões e R$ 4,8 milhões; sublimites por UF; "Pagar Online" só no Banco do Brasil (sem Pix); alíquotas e partilha (Anexos em imagem); referências a artigos da Resolução CGSN 140. As Resoluções CGSN 190 e 191 não foram lidas (só aparecem no documento 33).

# 6. CNO, DOI e LCDPR

## 6.1 CNO (Cadastro Nacional de Obras)

O CNO substitui o CEI e vale para todos os atos da obra. É obrigatório para o dono da obra, o incorporador, a construtora em empreitada total e o líder de consórcio; na empreitada parcial, inscreve-se o contratante (p. 5 e 6). Prazo de 30 dias do início das atividades (p. 6). O manual não traz penalidade, nem tipo e tamanho dos campos, nem o formato do número do CNO, e é de 2019: as normas citadas (IN RFB 971/2009 e 1.845/2018) podem ter mudado.

**Por que importa:** Alberto confirmou ter cliente de construção civil (documento 01, seção 14), e o CNO já aparece na Reinf R-2010, na NFS-e de obra e na folha. Hoje o número é um código solto de 30 posições em quatro entidades (`Cad_Local_Operacao`, `Mov_Reinf_Servico_Previdenciario` e as da folha). `Cad_Obra` guarda só a classificação do PAIC, que **não equivale** à categoria, destinação e tipo do CNO. Além disso, `Cad_Participante_Inscricao.Tipo_Inscricao` não tem cno, caepf nem cei, embora o documento 11 diga que o número sai dessa entidade: é uma inconsistência a esclarecer.

**Proposta (D-N45):** quatro entidades. `Cad_Cno_Obra` (número como identidade, situação ativa/paralisada/suspensa/encerrada/nula, datas, CNAEs, endereço com código de localização, categoria, destinação, tipo e metragens, ligação opcional a `Cad_Obra` e ao contrato), `Cad_Cno_Responsavel` (vínculo: construtora, consórcio, líder, proprietário, dono da obra, incorporador; datas; confirmação), `Cad_Cno_Contratante` e `Mov_Cno_Situacao` (paralisação e reativação). Os códigos soltos passariam a apontar para `Cad_Cno_Obra`. A lista de categorias, que no manual de 2019 está só em imagem, veio da página oficial da Receita (publicada e atualizada em 09/05/2021): **obra nova**, **acréscimo** (aumento das medidas sobre construção existente), **reforma** (sem alterar medidas) e **demolição**; a página também lista "existente" (construção existente sobre a qual se faz acréscimo, reforma ou demolição), que precisa de conferência. Para cada categoria informam-se as **áreas complementares**: quadras esportivas, estacionamento térreo, piscina e área complementar de posto de gasolina. Isso vira o domínio de categoria e quatro indicadores (ou uma tabela filha de áreas) em `Cad_Cno_Obra`. A página não traz tabela ligando categoria a destinação nem base legal.

## 6.2 DOI (Declaração sobre Operações Imobiliárias)

A DOI é obrigação **do cartório** (notas, registro de imóveis e títulos e documentos), não da empresa que é parte do negócio. Prazo: último dia útil do mês seguinte ao ato; multa de 0,1% ao mês sobre o valor da operação (teto de 1% e mínimo de R$ 20) e R$ 50 por informação inexata (Perguntas e Respostas, Q108). Os manuais trazem o leiaute de importação em JSON (ficha por ficha). A Mlegate só seria afetada se tivesse cliente cartório, e nada no dicionário indica isso. Mesmo sem cartório, os manuais servem de lista de dados do imóvel; faltam em `Cad_Imovel` o código nacional de matrícula (CNM), o código INCRA, a denominação rural, a área construída, a destinação e o RIP/CAT de imóvel da União, e em `Mov_Operacao_Imobiliaria` a data do negócio, o tipo de operação, a forma de pagamento e a base do ITBI. O dígito verificador do CIB tem regra publicada (p. 35 e 36) e pode virar validação.

**Pendência nas fontes:** o manual de preenchimento (p. 45) admite CPF do cônjuge ou dos pais para quem não tem CPF, e as Perguntas e Respostas (Q37) dizem que isso foi revogado.

## 6.3 LCDPR (Livro Caixa Digital do Produtor Rural)

O LCDPR é do **produtor rural pessoa física** cuja receita da atividade rural supera o limite (o valor não consta no texto); entrega até o fim do prazo da DIRPF, com certificado ICP-Brasil. O declarante pessoa física está fora do dicionário (documento 15, P-25), e não há cliente produtor rural PF nos documentos. Só se justifica se a Mlegate passar a atender pessoa física. O leiaute (registros 0000, 0010, 0030, 0040, 0045, 0050, Q100, Q200 e 9999) está resumido para uso futuro; o manual tem duas inconsistências próprias (ocorrência do Q100 e um exemplo do Q200 com dois conjuntos de valores).

# 7. Relacionamento com o fisco: DEAP, e-Processo, NAF e Mafon

## 7.1 DEAP (Rearp Atualização, Lei 15.265/2025)

É a declaração de opção para atualizar o valor de bens móveis e imóveis; para pessoa jurídica, IRPJ a 4,8% e CSLL a 3,2%, em quota única ou até 36 quotas de no mínimo R$ 1.000. Os prazos (19/02 e 27/02/2026) já passaram. O que sobra para o ERP:

- **Darf avulso** (sem declaração): códigos 1835 (IRPJ) e 1836 (CSLL) com extensão igual ao número da quota, "Número de Referência" igual ao número do processo gerado na transmissão e cálculo pelo Sicalc. Não existe no dicionário (o Darf nasce da DCTFWeb).
- **Restituição fora do PER/DCOMP:** para esses códigos, o pedido é um processo digital com formulário (Anexo I da IN RFB 2.055/2021). O dicionário assume o PER/DCOMP como única via.
- **Regra de juros:** a Selic conta só até o mês de emissão do Darf; emitido antes do vencimento, deve ser pago até o último dia útil do mês de emissão.

**Pergunta em aberto:** as fontes não dizem se a Mlegate optou pela DEAP. Se não optou, as propostas valem pelo uso geral (parcelamento, auto de infração) e têm prioridade baixa. O lado IRPF e a migração de bens da Dabim ficam **sem impacto**. O manual tem erros de redação (p. 5 com "2027", p. 9 com "R$ 2.0000,00").

## 7.2 e-Processo (manual de 08/02/2022)

O processo administrativo, o andamento e o prazo fatal já estão no dicionário (`Cad_Processo`, `Mov_Processo_Andamento`). Faltam: **tipo da ciência** (intimação ou comunicado) e **natureza** (eletrônica, postal, pessoal, edital), data da ciência e prazo para manifestação contado dela; **solicitação de juntada de documento**; **caixa postal fiscal** do e-CAC e do DTE (só existe a mensagem do eSocial); e a **restrição de procuração por processo**, que `Cad_Procuracao` não tem. O manual é de 2022 e pode estar defasado.

## 7.3 NAF

O manual é de atendimento a cidadãos e MEI e **não pede entidade nova** na maior parte. Exceções: **certidões fiscais** (esfera, resultado negativa/positiva com efeitos de negativa/positiva, validade; a federal vale 6 meses, p. 23) e **parcelamento** (só existe `Numero_Parcelamento` como texto em `Mov_Dctfweb_Vinculacao`). O DAS e a declaração anual do MEI já estão propostos no documento 33.

## 7.4 Mafon 2025

Reúne as regras de retenção por código de receita. A estrutura do dicionário (`Mov_Titulo_Retencao` nos dois sentidos, antecipação compensável, natureza do rendimento ligada ao código, Reinf) **cobre o essencial**. Lacunas:

- **Tabela de percentuais por código** na venda a órgão público federal (p. 241 a 243), por exemplo 6147 (IR 1,2, total 5,85), 9060 (IR 0,24, total 4,89) e 6190 (IR 4,8, total 9,45). Hoje `Valor_Retido` é explícito, sem validação contra a tabela.
- **Ente do órgão pagador:** estados e municípios retêm só IR, recolhem em guia própria e informam o código 6256 na Reinf (p. 244 e 245); o dicionário não distingue.
- **Dispensas e prazos por código:** valor de retenção até R$ 10 (p. 219), Simples e cooperativas em ato cooperado (p. 221), prazo por decêndio ou quinzena (p. 222 a 226).

O manual traz "Versão 1.0 – XX/XX/2025" na p. 2, ou seja, versão sem data final.

# 8. Proposta consolidada de entidades (estimativa)

| Grupo | Entidades propostas | Qtde |
|---|---|---|
| Produção e Estoque (Bloco K) | `Mov_Ordem_Producao_Apontamento`, `Mov_Producao_Correcao`, `Mov_Producao_Desmontagem` e `_Destino`, `Mov_Estoque_Reclassificacao`, `Mov_Producao_Reprocesso` e seus itens; campos: propriedade e participante no saldo, `Codigo_OP_Sped`, `Eh_Coproduto`, `Tipo_Leiaute_Bloco_K` | ≈ 7 |
| Apuração estadual (E, G, H) | `Mov_Apuracao_Ajuste_Detalhe` (documento de arrecadação e processo), H030; campos de DEB_ESP, DIFAL e FCP separados e CIAP em quatro componentes | ≈ 2 |
| Simples | `Mov_Simples_Apuracao_Parcela`, `Mov_Simples_Das_Item`, `Mov_Simples_Das_Periodo`, `Mov_Simples_Apuracao_Malha`, `Mov_Simples_Comunicacao`, `Mov_Simples_Impedimento`, `Mov_Simples_Maed`; campos de filial, ente, receita recebida e RBT12 | 7 |
| CNO | `Cad_Cno_Obra`, `Cad_Cno_Responsavel`, `Cad_Cno_Contratante`, `Mov_Cno_Situacao` | 4 |
| Relacionamento com o fisco | `Mov_Darf_Avulso`, `Mov_Processo_Juntada`, caixa postal fiscal, `Mov_Certidao_Fiscal`, `Mov_Parcelamento_Tributario` e parcela, `Cad_Retencao_Federal_Parametro` | ≈ 7 |
| **Total** | | **≈ 27** |
| Só sob condição | DOI para cartório (≈ 5 entidades) e LCDPR para produtor rural PF (≈ 3) | fora |

# 9. Decisões para você

Para cada decisão, a recomendação é a opção que vale pelo que as fontes mostram. Nenhuma foi aplicada.

| Nº | Decisão | Recomendação |
|---|---|---|
| D-N42 | A Mlegate, ou algum cliente, é industrial ou atacadista sujeito ao Bloco K da EFD? Se sim, modelar K210 a K280 (≈ 7 entidades) e o leiaute do K010 | Decidir pelo perfil dos clientes; se houver industrial, incluir tudo |
| D-N43 | Completar a apuração estadual do documento 33 (E112/E115, DEB_ESP, DIFAL e FCP separados, CIAP em 4 componentes, H030) | Incluir, junto da revisão 3 |
| D-N44 | Registrar a regra de exportação de IBS, CBS e IS na EFD (`VL_DOC` por exercício, `VL_OPR` sem os novos tributos, filtro de documento só da reforma) e o código de negócio do item (`COD_ITEM`) | Incluir: é só especificação |
| D-N45 | Cadastro do CNO em 4 entidades, substituindo os códigos soltos | Incluir: há cliente de construção civil |
| D-N46 | Simples: parcelas por tributo, filial, ente, DAS por item e por período, malha, comunicação, impedimento e MAED | Incluir as lacunas altas; adiar DEFIS campo a campo |
| D-N47 | Corrigir D-N41: DAS avulso exige apuração transmitida; ampliar `Origem` (cobrança, medida judicial, processo) | Sim, é correção |
| D-N48 | Relacionamento com o fisco: Darf avulso, caixa postal fiscal, ciência e juntada, certidões, parcelamento | Incluir ciência, caixa postal, certidão e parcelamento; Darf avulso só se a Mlegate optou pela DEAP ou tiver auto de infração |
| D-N49 | DOI e LCDPR: criar módulos próprios? | Não agora: só os campos de imóvel (CNM, INCRA, destinação) e o validador do CIB |
| D-N50 | `Cad_Retencao_Federal_Parametro` (percentuais por código, ente pagador, dispensas e prazos) e correção do texto do documento 10 | Incluir |

**Perguntas que dependem de fatos que só você sabe:** a Mlegate optou pela DEAP? Há cliente industrial ou atacadista? Há cliente cartório ou produtor rural pessoa física? A tabela de categorias do CNO e as tabelas externas da EFD precisam vir de você.

# 10. O que ainda falta

Além dos itens já pendentes dos documentos 33 a 36 (NFCom, Anexos VI e VII da NT 007, Resolução CGSN 191, leiaute da DIMOB, Swagger das APIs, entre outros), os manuais novos deixam estes pedidos:

- Tabelas externas da EFD (4.5.4, 5.1.1, 5.2, 5.3, 5.4, 5.6, 5.7, 5.8 e 5.9.1) do portal do SPED, para carregar os códigos de ajuste e afins.
- Manual vigente do CNO (o de 2019 pode estar defasado); a lista de categorias já veio da página da Receita (2021).
- Versão atual do Mafon (a de 2025 não tem data final) e do e-Processo (o de 2022).
- Texto da Lei Complementar 224/2025: chegou em 12/10/2026 e confirma o 17,5% do JCP (documento 51). Faltam as instruções normativas que a regulamentam (IN RFB 2.305/2025 e 2.306/2026), o Decreto 12.808/2025 e a Portaria 3.278/2025.
- Resoluções CGSN 190 e 191 e a regra atual da DEFIS.
