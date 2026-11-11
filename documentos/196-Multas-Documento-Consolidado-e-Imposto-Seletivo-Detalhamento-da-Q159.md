# Detalhamento da Q159-4, Q159-10 e Q159-11: multas, documento fiscal consolidado e Imposto Seletivo — Documento 196

> **O que este documento faz.** Responde ao seu pedido de 10/11/2026: "Q159-4 — Detalhar" e "Q159-10 e Q159-11 detalhar o que precisa". Para cada uma ele lê o texto da lei de novo, confere o que o dicionário da revisão 35 já tem, mostra o que falta, com exemplos numéricos, e propõe o desenho mínimo. **Nada foi aplicado ao dicionário**; o que você aprovar entra no próximo "consolidar".

*Fontes: LC 214 consolidada (Planalto) e texto da LC 227, os dois já na sessão; dicionário da revisão 35 (1.138 entidades e 12.769 campos); documentos 10, 14, 34, 90, 157 e 159; três páginas de imprensa e consultoria sobre a MP 1.399/2026 (o texto oficial da MP não abriu, seção 5.3).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **Respostas registradas (D-N525).** Q159-1 a Q159-3 e Q159-5 a Q159-9 aprovadas ("Sim"), entram no próximo "consolidar". Ficam abertas só a Q159-4, a Q159-10 e a Q159-11, que este documento detalha, e a Q159-E1 (equipe).
- **Multas (Q159-4).** Recomendo a **opção A+**: manter a D-N284 (o ERP só registra a penalidade do auto) e registrar **nove avisos do Motor** nos momentos em que o usuário cria o risco de multa (por exemplo, cancelar um documento depois do fato gerador). Não custa entidade nova. A opção B (calcular a multa) fecha em **3 entidades e 51 campos**; os exemplos da seção 3.2 mostram onde ela depende de leitura que o contador ainda não deu (C230).
- **Duas correções ao documento 159.** (1) O art. 341-F, § 3º, traz um **quinto percentual (50%)** que o anexo A do 159 não listou: o domínio passa de 28 para **29 valores**. (2) O art. 330, § 1º, VII, exige no auto do IBS o **ente federativo responsável pelo lançamento**; `Mov_Auto_Infracao` não tem esse dado (+1 campo).
- **Documento fiscal consolidado (Q159-10).** A lei só diz que o ato conjunto **deve permitir** o documento consolidado (art. 60, § 7º) e que a plataforma substituta pode emiti-lo (art. 22, § 13, I). Não achei leiaute, nota técnica nem prazo. O dicionário liga **um documento a uma só origem**; o consolidado exigiria várias. Listo na seção 4.4 os **10 pontos que o ato precisa responder** e mostro um esboço (1 entidade, 12 campos), que **não recomendo aplicar** antes do leiaute.
- **Imposto Seletivo (Q159-11).** A conferência achou **cinco lacunas**: o dicionário não registra a hipótese do fato gerador nem a base do art. 414, nem quem é o contribuinte do art. 424, nem o valor de referência, e tem **dois caminhos para a alíquota do IS** (`Cad_NCM_Imposto_Seletivo` e a lista legal com `ID_Aliquota`). Proponho **1 entidade nova (`Cad_Is_Hipotese_Base`, 15 campos, 11 linhas de carga)**, 2 campos no item da apuração, 1 campo em `Cad_NCM_Imposto_Seletivo` (o grupo do art. 409, § 1º) e 4 domínios novos. **Tudo parte do NCM, como você lembrou (e como o art. 409, § 1º, diz):** o NCM do produto dá o grupo (fumígeno, bebida, veículo e os outros) e a alíquota, e o grupo escolhe a base; nada é digitado pelo usuário (seção 5.4).
- **Fato novo: MP 1.399/2026.** Três páginas de imprensa e consultoria dizem que a MP, publicada em 04/11/2026, fixa as alíquotas do IS a partir de 02/02/2027 (cigarros: 66,7% mais R$ 3,50 por vintena, sobre um valor de referência de 15% do preço de varejo). **Não consegui abrir o texto oficial.** Nada do desenho depende desses números, mas a seção 5.3 lista o que eles exigiriam. Peço o texto na Q196-10.
- **Perguntas.** Q196-1 a Q196-11 na seção 6, cada uma com recomendação. Do contador: C230 a C232, só no documento 188 (Parte 7). Total, se tudo for aprovado: +1 entidade e +19 campos sobre o documento 159 (**1.144 entidades e 12.860 campos** na revisão 36, soma minha).

# 2. As respostas de 10/11/2026 ao documento 159

| Pergunta | Resposta | O que acontece |
|---|---|---|
| Q159-1 a Q159-3 | Sim | Lista refeita dos 131 artigos, conciliação com o CSV e correção do "art. 95" para art. 22; ordem de aplicação (art. 7º-A); consulta e contencioso. Entram no próximo "consolidar". |
| Q159-4 | Detalhar | Seção 3 deste documento. |
| Q159-5 a Q159-9 | Sim | PNCT sem `Participa_Pnct`; penalidades do prestador de pagamento no B7; devolução ao turista só com cliente; destino dos artigos em bloco (inclusive os 19 do anexo B); energia elétrica como texto de regra. Entram no próximo "consolidar". |
| Q159-10 e Q159-11 | Detalhar o que precisa | Seções 4 e 5 deste documento. |

**Leitura minha a confirmar.** A Q159-1 foi lida como aprovando a lista e a conciliação do anexo B, inclusive a correção que faço agora ao próprio anexo (o art. 348 está desenhado no documento 157, seção 7.4, e não "parcial"; no anexo B, 19 artigos ALTO e MÉDIO têm desenho ou decisão, 1 é parcial e 19 só têm destino).

# 3. Q159-4: multas — registrar, avisar ou calcular

## 3.1 O que a lei fixa

A LC 227 criou o capítulo de infrações e penalidades do IBS e da CBS (arts. 341-A a 341-H). Em resumo:

| Bloco | O que diz | Onde está no texto |
|---|---|---|
| **Multa de ofício** | 75% do tributo não declarado ou declarado a menor e não pago, ou do crédito indevido; **50%** se a declaração descreve corretamente o bem ou serviço, as quantidades e o valor da operação; 100% na sonegação, fraude, simulação ou conluio; 150% na reincidência dessas condutas (3 anos). | Art. 341-F, caput, §§ 1º e 3º |
| **Obrigações acessórias** | 22 incisos: **24 penalidades** (os incisos IV e XVII têm duas alíneas). Parte em **UPF** (de 1 a 150 UPF, conforme o inciso, por período, equipamento, documento, número, evento, informação, dispositivo ou requisito); parte em **percentual** do "tributo de referência", do crédito ou da diferença. Majoração de 50% na reincidência específica (mesmo inciso, 3 anos). O inciso IV não se aplica a mera falha ou erro material. | Art. 341-G, caput, §§ 1º a 4º |
| **Tributo de referência** | Alíquota de referência vezes o valor da operação, ainda que imune, isenta, de alíquota zero, reduzida, diferida ou suspensa. CBS desde 2027; IBS de 2027 a 2032 pelo **dobro** da alíquota de referência da CBS; IBS desde 2033 pela própria alíquota de referência. Em 2026: **6%** (CBS) e **12%** (IBS) do valor da operação. | Art. 341-G, § 5º |
| **Piso e teto** | Informação de comércio exterior omitida (inciso XIX): 100 UPF por informação, no máximo 1% do valor da operação, no mínimo 50 UPF. | Art. 341-G, § 7º, III |
| **UPF** | R$ 200,00, atualizada por ano pelo IPCA (ou índice que o substitua); o valor atualizado sai em ato conjunto do CGIBS e da RFB. Não achei o ato com o valor de 2026. | Art. 341-C |
| **Cumulação e mora** | As penalidades se somam quando houver falta de obrigação acessória e principal. Se o tributo já serviu de base à multa punitiva, a multa de mora não se aplica **até a notificação** do lançamento. A multa punitiva se calcula depois dos juros do art. 29, § 2º, II. | Arts. 341-B e 341-D |
| **Redução** | Pagamento ou parcelamento: 50%, 40%, 30% ou 20% da penalidade, conforme a hipótese; 60%, 50%, 40% ou 30% para quem participa do PNCT ou tem "bons antecedentes" (que o regulamento ainda não define). | Art. 341-H |
| **2026** | Auto de infração por obrigação acessória do art. 341-G: intimação para suprir a omissão em 60 dias, e o atendimento extingue a penalidade. **Já desenhado** no documento 157, seção 7.4 (`Mov_Auto_Infracao`). | Art. 348, §§ 3º e 4º |

## 3.2 Quatro exemplos com números

As alíquotas de referência abaixo são **hipotéticas, só para o exemplo**; a da CBS de 2027 (9%) e a do IBS (o dobro, 18%) não são as oficiais. A UPF é a de R$ 200,00 da lei.

**Exemplo 1: a UPF.** Arquivo fiscal entregue em atraso (art. 341-G, IV). Sem intimação, a alínea "a" cobra 20 UPF por período: 20 × R$ 200,00 = **R$ 4.000,00**. Com intimação, a alínea "b" cobra 30 UPF por período e a cada intimação: 30 × R$ 200,00 = **R$ 6.000,00**. Se for o mesmo inciso, repetido em até 3 anos, a majoração de 50% leva a alínea "a" a **R$ 6.000,00**. O ERP só tem como conferir isso se souber o valor da UPF do ano, que muda por ato.

**Exemplo 2: o tributo de referência.** Bem fornecido sem documento fiscal (inciso XI): 100% do tributo de referência. Operação de R$ 100.000,00. Em **2026**: CBS 6% = R$ 6.000,00 e IBS 12% = R$ 12.000,00. Em **2027** (alíquotas hipotéticas): CBS R$ 9.000,00 e IBS R$ 18.000,00 (o dobro). **Dúvida:** o texto não diz se o percentual incide em separado sobre o IBS e sobre a CBS (duas multas, soma de R$ 27.000,00 em 2027) ou sobre a soma. Vai ao contador (C230).

**Exemplo 3: ofício e redução.** Tributo de R$ 10.000,00 declarado a menor e não pago. Multa de 75% = **R$ 7.500,00**; se a declaração descreve corretamente o bem, as quantidades e o valor (art. 341-F, § 3º), 50% = **R$ 5.000,00**; com sonegação, fraude ou conluio, 100% = **R$ 10.000,00**; reincidente, 150% = **R$ 15.000,00**. Sobre a multa de 75%, o art. 341-H dá:

| Hipótese | Redução | Multa a pagar | Com PNCT ou bons antecedentes |
|---|---|---|---|
| Pagamento até o fim do prazo da impugnação | 50% | R$ 3.750,00 | 60% → R$ 3.000,00 |
| Parcelamento até o fim do prazo da impugnação | 40% | R$ 4.500,00 | 50% → R$ 3.750,00 |
| Pagamento depois do prazo e antes da dívida ativa | 30% | R$ 5.250,00 | 40% → R$ 4.500,00 |
| Parcelamento depois do prazo e antes da dívida ativa | 20% | R$ 6.000,00 | 30% → R$ 5.250,00 |

**Exemplo 4: 2026.** Auto de infração lavrado em 2026 por falta de uma obrigação acessória do art. 341-G. O contribuinte é intimado e tem 60 dias para suprir a omissão; se atende, a penalidade se extingue (art. 348, § 4º). O ERP já guarda a data da intimação, a do atendimento e a marca de penalidade extinta (documento 157, seção 7.4).

## 3.3 O que já está desenhado e o que o documento 159 propôs (opção A)

Hoje o dicionário tem `Mov_Auto_Infracao` (a D-N284: só registra, sem calcular multa) com os quatro campos do suprimento de 2026 (documento 157). O documento 159, opção A, acrescentaria 8 campos (tipo da penalidade, percentual, valor, reincidência específica, regime especial de fiscalização, hipótese e percentual de redução, valor pago) e o domínio `tipo_penalidade_ibs_cbs`, com 28 valores. O catálogo de números da lei (UPF de R$ 200,00 e os 8 percentuais do art. 341-H) já entra em `Cad_Parametro_Legal_Ibs_Cbs` (Q159-3, aprovada), **de modo que a opção A já guarda os números da lei, sem calcular com eles**.

**Correção ao anexo A do documento 159.** O art. 341-F, § 3º, fixa **50%** no lançamento de ofício do inciso I quando a declaração descreve o bem, a quantidade e o valor. O anexo A tinha 28 penalidades (4 do art. 341-F e 24 do art. 341-G) e não listou esse caso. Proponho o valor `oficio_50_declaracao_correta` (29 valores) e `Percentual_Multa_Aplicado` com 50, 75, 100 ou 150 no art. 341-F. A frase "28 penalidades de obrigação acessória" da tabela de triagem do 159 também estava errada: são **24** de obrigação acessória e 4 (agora 5) de ofício.

## 3.4 Opção A+ (recomendada): registrar e avisar

A+ é a opção A mais **nove avisos do Motor**, registrados como texto (a regra da casa: o ERP avisa, não bloqueia, e os avisos do Motor ficam registrados sem programação). Cada um nasce do **momento em que o usuário faz algo que a lei pune**:

| Nº | Quando o ERP avisa | Penalidade possível | O aviso diz |
|---|---|---|---|
| 1 | Cancelar documento fiscal depois do fato gerador, ou depois do prazo de cancelamento | Art. 341-G, XVII, a e b: 66% ou 33% do tributo de referência | "Cancelar depois do fato gerador pode gerar multa de 66% do tributo de referência." |
| 2 | Documento recebido sem manifestação do adquirente (confirmação, desconhecimento, devolução) | Art. 341-G, IX: 1 UPF por documento | "Falta manifestar este documento; a omissão tem multa de 1 UPF por documento." |
| 3 | Inutilizar número de documento sem comunicar no prazo | Art. 341-G, VIII: 1 UPF por número | "A inutilização precisa ser comunicada no prazo." |
| 4 | Arquivo ou declaração fiscal em atraso, ou já intimada | Art. 341-G, IV, a e b: 20 UPF por período; 30 UPF por período e intimação | "Entrega em atraso: 20 UPF por período (30 UPF se houver intimação)." |
| 5 | Apropriar crédito de documento recebido marcado como não idôneo | Art. 341-G, XIII e XV: 66% do tributo de referência e 66% do crédito | "Este documento está como não idôneo; crédito indevido tem multa de 66%." |
| 6 | Deixar de estornar ou anular crédito quando a regra exige | Art. 341-G, XV: 66% do crédito | "A regra pede estorno; sem ele a multa é de 66% do crédito." |
| 7 | Aquisição que exige documento de entrada e ele não foi emitido | Art. 341-G, XVI: 100% do tributo de referência | "Falta o documento de entrada desta aquisição." |
| 8 | Contingência (DPEC) com valor diferente do documento definitivo | Art. 341-G, XVIII: 33% da diferença | "O valor da contingência diverge do documento; multa de 33% da diferença." |
| 9 | Operação de importação ou exportação sem as informações que o controle fiscal exige | Art. 341-G, XIX: 100 UPF por informação, de 50 UPF até 1% da operação | "Informação de comércio exterior incompleta." |

Cada aviso **cita** a multa e **não a calcula**: o texto vem do valor do domínio `tipo_penalidade_ibs_cbs` e do parâmetro de `Cad_Parametro_Legal_Ibs_Cbs`. Não há entidade nova. O aviso 4 já tem par no documento 157 para 2026 (prazo de 60 dias).

## 3.5 Opção B: calcular e simular

B acrescentaria **3 entidades e 51 campos** (a estimativa do documento 159, "cerca de 40", ficou curta): o catálogo das penalidades (`Cad_Infracao_Regra`, 20), os valores anuais da UPF (`Cad_Upf_Valor`, 11) e a simulação (`Mov_Multa_Simulacao`, 20). A simulação responderia a "quanto seria a multa se eu cancelar este documento agora" e "o auto veio com este valor, confere?".

**Cad_Infracao_Regra** — uma linha por penalidade (29 linhas de carga provisória). Mestre com identidade e versão.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Infracao_Regra** | *identificador* | Identidade. |
| **ID_Infracao_Regra_Versao** | *identificador da versão* | Chave da versão. |
| **ID_Tipo_Penalidade** | *referência (Cad_Classe_Sistema, domínio = tipo_penalidade_ibs_cbs) — identidade* | A penalidade do domínio do documento 159, anexo A. |
| **Artigo** | *código (até 10)* | 341-F ou 341-G. |
| **Inciso** | *código (até 10)* | Inciso ou parágrafo. |
| **Alinea** | *código (1), opcional* | a ou b (incisos IV e XVII). |
| **Descricao_Infracao** | *texto* | O texto da infração, resumido. |
| **Tipo_Medida** | *enumeração {upf, percentual_tributo_referencia, percentual_tributo_lancado, percentual_credito, percentual_diferenca}* | Como a penalidade se mede. |
| **Quantidade_Upf** | *número, opcional* | Quantas UPF, quando a medida é a UPF. |
| **Percentual** | *número, opcional* | O percentual, quando a medida é percentual. |
| **Unidade_Cobranca** | *enumeração {por_infracao, por_periodo_apuracao, por_periodo_e_intimacao, por_equipamento, por_numero, por_documento, por_evento, por_informacao, por_dispositivo, por_requisito, unica}* | Por que unidade a UPF se multiplica. |
| **Admite_Majoracao_Reincidencia** | *booleano* | Verdadeiro nos incisos do art. 341-G (50% na reincidência específica). |
| **Valor_Minimo_Upf** | *número, opcional* | Piso em UPF (inciso XIX: 50). |
| **Percentual_Teto_Valor_Operacao** | *número, opcional* | Teto sobre o valor da operação (inciso XIX: 1%). |
| **Fundamento_Legal** | *texto* | Dispositivo. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Provisório até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale; 31/12/9999 quando em aberto. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**Cad_Upf_Valor** — uma linha por ano. A carga inicial é só a UPF de R$ 200,00; os valores seguintes dependem do ato conjunto, que não achei.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Upf_Valor** | *identificador* | Identidade. |
| **Valor_Upf** | *número* | R$ 200,00 na criação; atualizado por ano. |
| **Ano_Referencia** | *número* | O ano a que o valor se aplica. |
| **Indice_Atualizacao** | *texto* | IPCA ou o índice que o substituir (art. 341-C). |
| **Percentual_Variacao_Indice** | *número, opcional* | A variação aplicada. |
| **Ato_Divulgacao** | *texto, opcional* | O ato conjunto do CGIBS e da RFB que divulgou o valor (art. 341-C, parágrafo único). |
| **Fundamento_Legal** | *texto* | Art. 341-C. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Provisório até o ato ser conferido. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale; 31/12/9999 quando em aberto. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**Mov_Multa_Simulacao** — cada simulação feita, para a auditoria. Não é lançamento.

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Multa_Simulacao** | *identificador* | Identidade. |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa. |
| **ID_Infracao_Regra** | *referência (Cad_Infracao_Regra)* | A penalidade simulada. |
| **ID_Auto_Infracao** | *referência (Mov_Auto_Infracao), opcional* | O auto, quando a simulação conferir um auto recebido. |
| **ID_Documento_Fiscal** | *referência (Mov_Documento_Fiscal), opcional* | O documento que motivou a simulação. |
| **Data_Referencia** | *data* | A data do fato; define UPF, alíquota de referência e ano. |
| **Tributo** | *enumeração {ibs, cbs, nao_se_aplica}* | O tributo da base. |
| **Valor_Base** | *número* | Valor da operação, do tributo, do crédito ou da diferença, conforme a medida. |
| **Valor_Tributo_Referencia** | *número, opcional* | Art. 341-G, § 5º: alíquota de referência vezes o valor da operação. |
| **Quantidade_Unidades** | *número, opcional* | Períodos, equipamentos, documentos, números ou eventos. |
| **ID_Upf_Valor** | *referência (Cad_Upf_Valor), opcional* | A UPF aplicada. |
| **Reincidencia_Especifica** | *booleano* | Aplica a majoração de 50% (art. 341-G, § 1º). |
| **Valor_Calculado** | *número* | A penalidade simulada, antes da redução. |
| **Valor_Minimo_Aplicado** | *número, opcional* | O piso, quando houver. |
| **Valor_Teto_Aplicado** | *número, opcional* | O teto, quando houver. |
| **ID_Hipotese_Reducao** | *referência (Cad_Classe_Sistema, domínio = hipotese_reducao_multa), opcional* | A hipótese do art. 341-H usada. |
| **Valor_Apos_Reducao** | *número, opcional* | A penalidade depois da redução. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | Provisório: simulação não é lançamento. |
| **Data_Inclusao** | *data/hora* | Preenchida pelo sistema. |
| **Observacao** | *texto, opcional* | Livre. |

**O que B exige que hoje não existe.** (1) Manter a UPF de cada ano. (2) Ler o "tributo de referência" de cada ano e tributo (hoje há linhas de alíquota de referência em `Cad_Aliquota`, mas o ERP teria de decidir se a multa de 100% incide sobre cada tributo ou sobre a soma, C230). (3) Decidir o que é "período de apuração" e "intimação" para multiplicar a UPF. (4) Acompanhar o regulamento dos "bons antecedentes". Cada leitura errada vira número errado numa tela.

## 3.6 Comparação e recomendação

| | **A** | **A+** | **B** |
|---|---|---|---|
| Registra a penalidade do auto | Sim | Sim | Sim |
| Guarda os números da lei (UPF, reduções) | Sim, como parâmetro | Sim, como parâmetro | Sim, e usa para calcular |
| Avisa antes da multa | Não | Sim, 9 avisos | Sim, com valor |
| Calcula a multa | Não | Não | Sim |
| Entidades e campos novos | 0 e 1 (ente do lançamento) | 0 e 1 | 3 e 51, mais o 1 |
| Risco de número errado na tela | Nenhum | Nenhum (o aviso cita, não calcula) | Alto até o contador responder C230 e o ato da UPF existir |
| Relação com a D-N284 | Mantém | Mantém | Reverte em parte |

**Recomendo A+.** Dá ao usuário o que a multa tem de útil (saber **antes** que o ato é punível) sem o ERP assumir uma conta que depende de uma UPF que ainda não achei e de leituras do contador. B só se justifica se um cliente quiser provisionar multa ou simular autuação; nesse caso entra com o texto da C230 respondido. Os avisos custam texto, e esse texto serve a B se um dia ela vier.

# 4. Q159-10: documento fiscal consolidado

## 4.1 O que a lei diz

- **Art. 60, § 7º (LC 227).** "Para fins de simplificação", o ato conjunto do CGIBS e da RFB (que fixa forma, conteúdo e prazos dos documentos fiscais, § 3º) **deverá permitir** a emissão de documentos fiscais consolidados. A lei não define "consolidado".
- **Art. 22, § 13, I (LC 227).** A plataforma digital que optar por ser **substituta tributária** do fornecedor residente no País deve emitir os documentos fiscais eletrônicos das operações dele, "inclusive de forma consolidada".
- **Art. 22, § 14.** Se a plataforma emitir o documento em até 30 dias depois do prazo do fornecedor e pagar o tributo, os acréscimos do art. 29, § 2º, e a multa pela falta de documento só se exigem do fornecedor.
- **Art. 60, § 1º.** As informações do documento têm caráter declaratório e constituem confissão do valor devido: o consolidado carregaria essa confissão por muitas operações.

## 4.2 O que se sabe fora da lei

Só fontes secundárias e nada oficial: uma matéria do Portal da Reforma Tributária (17/09/2025) conta que a emenda do PLP 108 nasceu para atender plataformas e empresas de tecnologia com regimes especiais de ISS, que emitem uma nota consolidada com relatório de milhares de transações; cita o risco de o número de documentos passar de cerca de 300 mil para 100 milhões em alguns setores. O **Ato Conjunto RFB/CGIBS nº 1/2025** (republicação lida) não trata de documento consolidado, e **não achei leiaute, nota técnica nem prazo**. Em suma: a lei autoriza, e quem define é o ato que ainda não existe.

## 4.3 O que o dicionário tem

| O que existe | O que faz | Serve ao consolidado? |
|---|---|---|
| `Mov_Documento_Fiscal` (40 campos) | Um documento, **uma origem** (`Origem_Tipo` e `ID_Origem`: nota de saída, nota de entrada, expedição ou outro). | Não: o consolidado reúne várias origens num documento. |
| `Mov_Bilhete_Passagem_Consolidado` (23 campos) | Linhas do bilhete de passagem consolidado (D300 e D410), com número inicial e final e valores por CST e CFOP. | Só como analogia: é **escrituração** consolidada de documentos já emitidos. |
| EFD-Contribuições consolidada (`Forma_Escrituracao`) | Escolhe registros consolidados (C180, C190, C490) em vez de um por documento. | Idem: escrituração, não emissão. |
| `Mov_Dfe_Vinculo_Pagamento` (documento 34) | Liga o documento fiscal à transação de pagamento (split). | Parcial: a ligação documento–pagamento existe; a ligação documento–várias operações não. |
| Plataforma substituta (art. 22) | Não existe entidade; o B7 (marketplace e PSP) ainda não foi desenhado (Q159-8, aprovada). | Não. |

## 4.4 O que o ato conjunto precisa responder (dez pontos)

O que o ERP **precisa** para suportar o consolidado, com onde cada ponto cairia no dicionário. Sem a resposta do ato, qualquer campo seria palpite.

| Nº | O que precisa ser definido | Onde cairia |
|---|---|---|
| 1 | Quem pode emitir: o próprio fornecedor (art. 60, § 7º) e a plataforma substituta (art. 22, § 13, I). Em quais setores ou situações. | `Mov_Documento_Fiscal.Papel`; a substituta, no B7. |
| 2 | O critério de agrupamento: período, adquirente, estabelecimento, classificação tributária ou alíquota. | Parâmetro com vigência (entidade nova se o critério variar por setor). |
| 3 | Se o documento leva o **relatório das operações** (e em que formato) ou se o relatório fica com o emitente. | Guarda de arquivo (GED) e, se exigido, uma linha por operação. |
| 4 | Como o documento aponta **várias origens**. Hoje: uma. | Entidade de ligação documento–origem. |
| 5 | Se o documento mistura classificações tributárias (`cClassTrib`) e como os totais se abrem por classificação. | Itens do documento consolidado com `ID_Cclasstrib`. |
| 6 | Quem pode receber consolidado: só adquirente não contribuinte (varejo) ou também contribuinte, e como o adquirente contribuinte apropria o crédito (art. 47). | Regra do Motor e do crédito (`Mov_Credito_Fiscal`). |
| 7 | Como se cancela, devolve ou ajusta **uma** operação dentro de um documento consolidado (art. 47, §§ 8º e 12; ajuste da operação do documento 157). | Situação por operação na entidade de ligação e referência ao documento de ajuste. |
| 8 | Prazo para emitir o consolidado depois do fato gerador (a lei só fixa os 30 dias da plataforma, art. 22, § 14). | Parâmetro em `Cad_Parametro_Legal_Ibs_Cbs`. |
| 9 | Se o consolidado é um **novo modelo de documento** ou um tipo de emissão dos modelos atuais (NF-e, NFS-e). | `Cad_Modelo_Documento_Fiscal` e `Cad_Dfe_Leiaute` (carga, sem estrutura). |
| 10 | Leiaute, nota técnica, autorizador e data de uso. | `Cad_Dfe_Leiaute` e `Cad_Autoridade_Fiscal_Servico` (carga). |

## 4.5 Esboço, para o dia em que o leiaute chegar

Se o ato seguir o que a lei sugere, bastariam **uma entidade de ligação e três campos**. Está aqui para você ver o tamanho, **não para aplicar**:

**Mov_Documento_Fiscal_Operacao** (esboço, 12 campos).

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Documento_Fiscal_Operacao** | *identificador* | Identidade. |
| **ID_Documento_Fiscal** | *referência (Mov_Documento_Fiscal)* | O documento consolidado. |
| **Origem_Tipo** | *enumeração (os valores de Mov_Documento_Fiscal.Origem_Tipo)* | O tipo da origem desta operação. |
| **ID_Origem** | *referência genérica* | A operação incluída. |
| **Data_Operacao** | *data* | Data do fato gerador da operação. |
| **ID_Participante_Adquirente** | *referência (Cad_Participante), opcional* | O adquirente, quando o ato exigir. |
| **ID_Cclasstrib** | *referência (Cad_Cclasstrib)* | A classificação desta operação. |
| **Valor_Operacao** | *número* | Valor da operação. |
| **Valor_Ibs** | *número, opcional* | IBS da operação. |
| **Valor_Cbs** | *número, opcional* | CBS da operação. |
| **Situacao** | *enumeração {incluida, cancelada, devolvida, ajustada}* | O que aconteceu com a operação depois. |
| **ID_Documento_Fiscal_Ajuste** | *referência (Mov_Documento_Fiscal), opcional* | O documento que cancelou, devolveu ou ajustou. |

Em `Mov_Documento_Fiscal`, mais três campos: `Indicador_Consolidado` (booleano), `Periodo_Inicio` e `Periodo_Fim` (datas, opcionais). Total do esboço: **1 entidade e 15 campos**.

## 4.6 Recomendação

**Não aplicar o esboço agora.** O documento fiscal é o centro do ERP e o consolidado mexe na regra "um documento, uma origem". Mudar isso sem leiaute arrisca refazer. Peço duas coisas: (a) aprovar os **dez pontos** da seção 4.4 como a lista que eu uso para ler o ato conjunto quando ele sair; (b) aprovar o **gatilho** para desenhar: a publicação do ato ou da nota técnica, **ou** um cliente que emita consolidado (plataforma ou empresa com regime especial de ISS). Se você preferir preparar já, o esboço da seção 4.5 é o ponto de partida.

# 5. Q159-11: Imposto Seletivo

## 5.1 O que a LC 227 mudou

| Artigo | Redação da LC 227 | Efeito |
|---|---|---|
| 414, III, c | O valor de referência é a base na **comercialização e na importação de produtos fumígenos**. | Os fumígenos passam a ter base própria, não a de venda. |
| 414, VI | Nas demais hipóteses, a base é o **valor de mercado do bem**. | Inciso novo: fecha o artigo com uma base de reserva. |
| 424, I | O contribuinte é o **fabricante**, no primeiro fornecimento, na incorporação do bem ao ativo imobilizado, na tradição em transação não onerosa ou no consumo do bem. | O contribuinte passa a ser identificado por quatro momentos, não só pelo primeiro fornecimento. |
| 434, § 2º-A | Na importação de fumígenos com alíquota ad valorem, a base é a **maior** entre a do art. 414, III, c, e a do § 2º (valor aduaneiro mais Imposto de Importação). | Duas bases calculadas e a maior vale. |

O texto anterior desses dispositivos não está no ambiente (só o consolidado, que já traz a nova redação).

Outros artigos do IS que a LC 227 alterou e já têm destino: art. 422, §§ 2º e 5º (teto de 0,25% para minerais e escalonamento 2029 a 2033), tratados como linhas com vigência (anexo B do documento 159).

## 5.2 O que o dicionário tem e o que falta

| Ponto | O que o dicionário tem hoje | Falta |
|---|---|---|
| Quais bens e serviços | `Cad_NCM_Imposto_Seletivo` (11 campos; NCM em qualquer nível, `Ex_Descricao`, tipo de alíquota ad valorem, específica ou **mista**, valor específico com unidade) e a lista legal `imposto_seletivo` em `Cad_Lista_Legal_Item` (pertinência e exceção da ZFM); `Sujeito_Imposto_Seletivo` no produto. | **Dois caminhos para a alíquota**: `Cad_NCM_Imposto_Seletivo` (suporta mista e específica) e a lista legal com `ID_Aliquota` (D-N295), cuja entidade `Cad_Aliquota` só tem percentual e não carrega valor por unidade. Precisa de uma regra única. |
| Fato gerador e contribuinte | Nada específico. O IS usa `Mov_Apuracao_Tributo_Item` com `ID_Imposto` = imposto seletivo. | Nenhum campo diz **qual** dos oito momentos do art. 412 ocorreu nem **quem** é o contribuinte (art. 424: fabricante, importador, arrematante, produtor-extrativista, fornecedor do serviço). |
| Base de cálculo | `Base_Calculo_Bruta`, `Base_Calculo_Efetiva`, `Forma_Tributacao` (ad valorem, específica, pauta), `Quantidade_Tributada`, `Valor_Especifico_Unidade`. | Nenhum campo diz **qual das seis bases do art. 414** foi usada (venda, arremate, valor de referência, valor contábil, receita própria, valor de mercado), e a importação tem outra (valor aduaneiro mais II). |
| Valor de referência | Não existe. Há valor de mercado (`Mov_Valor_Mercado_Apuracao`, `Cad_Regra_Valor_Mercado`) para o art. 5º e para locação. | O valor de referência (art. 414, § 2º: metodologia por ato do chefe do Executivo; § 3º: nos fumígenos, o preço de venda no varejo) não tem campo. |
| Valor de mercado (art. 414, VI) | `hipotese_valor_mercado` tem os casos do art. 5º, brinde e permuta. | Valor novo no domínio: IS, demais hipóteses (sem campo novo). |
| Importação | A Duimp e o Imposto de Importação existem (documentos 141 a 144). | Falta a regra de duas bases e o ponto de comparação (art. 434, § 2º-A); cabe em `Cad_Is_Hipotese_Base` e no aviso do Motor. |
| Cálculo misto | `Forma_Tributacao` tem um valor por linha de apuração; o documento 10 lê o IS misto como duas linhas (ad valorem e específica). | Confirmar que as duas linhas somam no documento e aparecem juntas (Q196-7). |

## 5.3 A MP 1.399/2026 (fonte secundária)

**Atenção.** Li três páginas (Fiscoplan, TaxUp e DGABC). O texto oficial da MP no Planalto não abriu (a permissão não foi respondida), e uma quarta página (Canal Rural) falhou. **Tudo abaixo é leitura de terceiros e pode mudar** (a MP precisa ser votada em até 120 dias). O que as páginas dizem, e o que cada ponto exigiria do dicionário:

| O que as fontes dizem | O dicionário comporta? |
|---|---|
| MP 1.399/2026, publicada em 04/11/2026; efeitos desde **02/02/2027**; regime transitório até 31/12/2027. | Sim: alíquota com vigência. |
| **Cigarros: alíquota mista**, 66,7% ad valorem mais R$ 3,50 por vintena (as fontes divergem: maço ou vintena). | Em parte: `Cad_NCM_Imposto_Seletivo` tem tipo mista, valor específico e unidade; confirmar a unidade "vintena" em `Cad_Unidade_Medida`. |
| **Base dos cigarros:** valor de referência = 15% do preço de venda a varejo, quando o preço é tabelado; sem preço tabelado, o valor líquido da primeira operação entre partes não relacionadas, sem ICMS, CBS e IBS. | **Não.** Não há preço de varejo tabelado nem metodologia (seção 5.4, Q196-9). |
| **Importação:** base = valor aduaneiro mais II, com **fatores de ajuste** (1,17 para veículos, embarcações e aeronaves; 1,45 para bebidas). | **Não.** Os fatores não têm campo. |
| **Veículos:** alíquota-base de 6,3% (passeio) ou 3,9% (comerciais), com **ajustes em pontos percentuais por cinco critérios** e fator de conversão 1,21. | **Não.** Uma alíquota por NCM não comporta ajustes por critério do veículo. |
| Bebidas: cerveja 4,2%; alcoólicas em geral 8%; vermutes 12%; destilados 24%; açucaradas 2,6%. Minerais: 0% até 31/12/2027. | Sim: alíquota por NCM com vigência. |

Por isso **nenhum número da MP entra em carga**, e o desenho abaixo não depende deles. Se o texto oficial confirmar os fatores de importação e os ajustes dos veículos, abre-se um documento próprio (Q196-10).

## 5.4 O desenho proposto

**Regra de partida (sua, 10/11/2026): o NCM é a base da segregação dos tributos.** O art. 409, § 1º, diz o mesmo: o IS incide sobre os bens "classificados nos códigos da NCM/SH" (e o carvão mineral) e sobre os serviços listados no Anexo XVII, em sete grupos. O desenho segue esse caminho, sem escolha digitada pelo usuário:

1. o produto tem NCM (`Cad_Produto_Servico` e `Cad_Classificacao_Mercadoria`);
2. o NCM, em qualquer nível (vale para os descendentes), acha a linha de `Cad_NCM_Imposto_Seletivo`, que dá a alíquota, o tipo e o **grupo**;
3. o grupo e o momento do fato gerador (art. 412) acham a linha de `Cad_Is_Hipotese_Base`, que dá o contribuinte e a base; a linha com grupo vale sobre a linha sem grupo.

**Três consequências.** (a) O fumígeno deixa de ser um escopo digitado: a primeira versão deste documento tinha um campo `Escopo_Produto` com três valores, que **substituí** pelo grupo que vem do NCM (`ID_Grupo_Produto_Is`). (b) O `Sujeito_Imposto_Seletivo` do produto passa a ser **derivado** do NCM, e não digitado (Q196-11). (c) Os **serviços** do Anexo XVII (concursos de prognósticos e fantasy sport) não têm NCM: ficam pela NBS (`Cad_NBS`) na lista legal do tipo `imposto_seletivo`, com a alíquota em `Cad_Aliquota` (só percentual; confirmar na Q196-8). **Embalagem:** o art. 409, § 2º, só alcança fumígenos e bebidas alcoólicas "em embalagem primária"; o grupo vindo do NCM diz quando o aviso vale, e o Motor pede para conferir a embalagem (Q196-11).

**Cad_Is_Hipotese_Base** (entidade nova, mestre com identidade e versão). Uma linha por hipótese do art. 412, aberta quando a base muda por fumígeno. Ela responde, para cada fato gerador do IS, **quem é o contribuinte** e **qual é a base**, e fica fora do cálculo da alíquota.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Is_Hipotese_Base** | *identificador* | Identidade da linha. |
| **ID_Is_Hipotese_Base_Versao** | *identificador da versão* | Chave da versão, padrão da Fase 0. |
| **ID_Hipotese_Fato_Gerador_Is** | *referência (Cad_Classe_Sistema, domínio = hipotese_fato_gerador_is) — identidade* | Qual momento do art. 412: primeiro fornecimento, arrematação, transferência não onerosa, incorporação ao ativo imobilizado, extração de bem mineral, consumo pelo fabricante, fornecimento ou pagamento do serviço, importação. Domínio novo, 8 valores. |
| **ID_Grupo_Produto_Is** | *referência (Cad_Classe_Sistema, domínio = grupo_produto_is), opcional — identidade* | O grupo do art. 409, § 1º, que vem do **NCM** do produto (`Cad_NCM_Imposto_Seletivo.ID_Grupo_Produto_Is`). Vazio = linha padrão, que vale para todos os grupos; a linha com grupo vale sobre a linha sem grupo (por exemplo, fumígenos: art. 414, III, c, e art. 434, § 2º-A). |
| **ID_Contribuinte_Tipo** | *referência (Cad_Classe_Sistema, domínio = tipo_contribuinte_is)* | Quem é o contribuinte nesta hipótese (art. 424): fabricante, importador, arrematante, produtor-extrativista, fornecedor do serviço. Domínio novo, 5 valores. |
| **ID_Base_Calculo_Tipo** | *referência (Cad_Classe_Sistema, domínio = tipo_base_calculo_is)* | A base do art. 414: valor de venda, valor de arremate, valor de referência, valor contábil de incorporação ao ativo, receita própria da entidade, valor de mercado; e, na importação, valor aduaneiro mais o Imposto de Importação (art. 434, § 2º). Domínio novo, 7 valores. |
| **ID_Base_Calculo_Tipo_Alternativa** | *referência (Cad_Classe_Sistema, domínio = tipo_base_calculo_is), opcional* | Só na importação de fumígenos com alíquota ad valorem: a base é a **maior** entre esta e a principal (art. 434, § 2º-A). |
| **Base_Minima_Valor_Mercado_Parte_Relacionada** | *booleano* | Verdadeiro quando a comercialização entre partes relacionadas, com alíquota ad valorem e sem valor de referência, não pode ter base inferior ao valor de mercado (art. 416). O valor de mercado usa `Mov_Valor_Mercado_Apuracao`. |
| **Descricao_Momento** | *texto* | O texto do art. 412 para a tela (por exemplo, "o que ocorrer primeiro: fornecimento ou pagamento do serviço"). |
| **Fundamento_Legal** | *texto* | Arts. 412, 414, 416, 424 e 434 da LC 214, com a LC 227. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação. |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale; 31/12/9999 quando em aberto. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**Carga proposta (11 linhas, todas provisórias):**

| Hipótese (art. 412) | Grupo (do NCM) | Contribuinte (art. 424) | Base (art. 414 e 434) |
|---|---|---|---|
| Primeiro fornecimento (I) | vazio (padrão) | Fabricante | Valor de venda (414, I); partes relacionadas: não inferior ao valor de mercado (416) |
| Primeiro fornecimento (I) | fumígenos | Fabricante | Valor de referência (414, III, c) |
| Arrematação em leilão (II) | vazio (padrão) | Arrematante | Valor de arremate (414, II) |
| Transferência não onerosa (III) | vazio (padrão) | Fabricante | Valor de referência (414, III, a) |
| Incorporação ao ativo imobilizado (IV) | vazio (padrão) | Fabricante | Valor contábil de incorporação (414, IV) |
| Extração de bem mineral (V) | vazio (padrão) | Produtor-extrativista | Valor de referência (414, III, b) |
| Consumo pelo fabricante (VI) | vazio (padrão) | Fabricante | Valor de referência (414, III, a) |
| Fornecimento ou pagamento do serviço (VII) | vazio (padrão) | Fornecedor do serviço | Receita própria da entidade (414, V) |
| Importação (VIII) | vazio (padrão) | Importador | Valor aduaneiro mais II (434, § 2º) |
| Importação (VIII) | fumígenos | Importador | A maior entre o valor de referência (414, III, c) e o valor aduaneiro mais II (434, § 2º-A) |
| Demais hipóteses | vazio (padrão) | conforme o caso | Valor de mercado (414, VI) |

**Domínios novos (4, 27 valores):** `hipotese_fato_gerador_is` (8), `tipo_contribuinte_is` (5), `tipo_base_calculo_is` (7) e `grupo_produto_is` (7, os incisos do art. 409, § 1º: veículos; embarcações e aeronaves; produtos fumígenos; bebidas alcoólicas; bebidas açucaradas; bens minerais; concursos de prognósticos e fantasy sport). Mais um valor em `hipotese_valor_mercado` (IS, demais hipóteses), sem campo.

**Campos novos nas existentes (4):**

**Mov_Apuracao_Tributo_Item** (+2)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Is_Hipotese_Base** | *referência (Cad_Is_Hipotese_Base), opcional* | Só quando ID_Imposto = imposto_seletivo: a linha da hipótese e da base aplicada, para a auditoria. |
| **Valor_Referencia_Informado** | *número, opcional* | Só quando a base é o valor de referência (art. 414, III): o valor informado pelo usuário ou sugerido pelo Motor. O ERP avisa se estiver vazio; enquanto não houver ato do Poder Executivo com a metodologia (art. 414, § 2º), o valor é digitado. |

**Mov_Auto_Infracao** (+1)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **Ente_Federativo_Lancamento** | *enumeração {uniao, estado, distrito_federal, municipio}, opcional* | Art. 330, § 1º, VII: o auto de infração do IBS traz o ente federativo responsável pelo lançamento. Quem autuou (nome do órgão) continua em Orgao_Autuante. |

**Cad_NCM_Imposto_Seletivo** (+1)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Grupo_Produto_Is** | *referência (Cad_Classe_Sistema, domínio = grupo_produto_is)* | Qual dos sete grupos do art. 409, § 1º, este NCM (e o `Ex_Descricao`) alcança. É o que liga o NCM à hipótese e à base de `Cad_Is_Hipotese_Base`. Carga provisória: o grupo de cada linha existente. |

**O que não faz.** Não calcula a alíquota (continua em `Cad_NCM_Imposto_Seletivo`), não calcula o valor de referência e não decide quem é "fabricante" numa industrialização por encomenda (C232). O ERP avisa quando falta a hipótese ou o valor de referência.

**Regra única para a alíquota do IS (Q196-8).** Para os **bens (NCM)**, recomendo que **`Cad_NCM_Imposto_Seletivo` seja a única fonte da alíquota e do grupo** (ela já suporta a alíquota mista, a específica e a unidade); a lista legal do tipo `imposto_seletivo` guarda só a **exceção da ZFM**, sem `ID_Aliquota` para bens (o `ID_Aliquota` continua para o IPI e os demais). Para os **serviços (NBS, Anexo XVII)**, a lista legal com `ID_Aliquota` e `Cad_Aliquota`, que só carrega percentual e basta para o serviço. Isso corrige a D-N295 só para os bens.

**Valor de referência (Q196-9).** `Cad_Is_Valor_Referencia` (um esboço de cerca de 12 campos: grupo ou NCM, método, percentual do preço de varejo, fundamento, situação do dado e vigência) **só depois** do texto oficial da MP e do ato do Executivo do art. 414, § 2º. Até lá, `Valor_Referencia_Informado` no item, com aviso.

# 6. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q196-1** | **Multas:** (A+) manter a D-N284 e registrar os nove avisos do Motor da seção 3.4; (A) só registrar, sem avisos; ou (B) catálogo, UPF e simulação (3 entidades, 51 campos)? | **A+.** Não custa entidade, e B espera a C230 e o ato da UPF. |
| **Q196-2** | Corrigir o domínio `tipo_penalidade_ibs_cbs` para **29 valores** (acrescentar `oficio_50_declaracao_correta`, art. 341-F, § 3º) e `Percentual_Multa_Aplicado` para 50, 75, 100 ou 150 no art. 341-F? | Sim. É correção do anexo A do 159. |
| **Q196-3** | Acrescentar `Ente_Federativo_Lancamento` (+1 campo) em `Mov_Auto_Infracao` (art. 330, § 1º, VII)? | Sim. |
| **Q196-4** | Registrar os **nove avisos** da seção 3.4 como texto do Motor (sem programar)? | Sim. É a regra da casa. |
| **Q196-5** | **Documento consolidado:** aprovar os **dez pontos** da seção 4.4 como a lista de leitura do ato conjunto e o **gatilho** (ato ou nota técnica publicado, ou cliente que emita consolidado), sem campo agora? | Sim. |
| **Q196-6** | Preferir preparar já o esboço da seção 4.5 (1 entidade, 12 campos e 3 campos no documento)? | Não agora. Mexe na regra "um documento, uma origem" sem leiaute. |
| **Q196-7** | **Imposto Seletivo:** aprovar `Cad_Is_Hipotese_Base` (15 campos, 11 linhas de carga provisória), os 4 domínios novos (inclusive `grupo_produto_is`), o campo `ID_Grupo_Produto_Is` em `Cad_NCM_Imposto_Seletivo` e os 2 campos de `Mov_Apuracao_Tributo_Item`? E confirmar que o IS misto do cigarro é gravado em duas linhas de apuração (ad valorem e específica) que somam no documento? | Sim. |
| **Q196-8** | Para **bens**, `Cad_NCM_Imposto_Seletivo` passa a ser a **única fonte da alíquota e do grupo do IS**, e a lista legal `imposto_seletivo` guarda só a exceção da ZFM (sem `ID_Aliquota` para bens); para **serviços** (NBS, Anexo XVII), a lista legal com `ID_Aliquota`? Corrige a D-N295 só para bens. | Sim. `Cad_Aliquota` não carrega valor por unidade, e o serviço só tem percentual. |
| **Q196-9** | **Valor de referência:** até haver o ato do art. 414, § 2º, ele é informado no item (`Valor_Referencia_Informado`), com aviso; `Cad_Is_Valor_Referencia` só com o texto oficial? | Sim. |
| **Q196-10** | Você envia o **texto oficial da MP 1.399/2026** (e, quando sair, o ato do Executivo do art. 414, § 2º)? Com ele, confiro os ajustes dos veículos, os fatores de importação, a unidade da vintena e a base dos fumígenos. | Sim. Sem ele, nada da seção 5.3 entra em carga. |
| **Q196-11** | **O NCM manda:** o `Sujeito_Imposto_Seletivo` de `Cad_Produto_Servico` passa a ser **derivado** do NCM (ou da NBS) e não digitado, com aviso quando o NCM do produto não achar linha? E, para fumígenos e bebidas alcoólicas (só tributados em embalagem primária, art. 409, § 2º), o Motor avisa para conferir a embalagem, sem campo? | Sim aos dois. É a sua regra: o NCM é a base da segregação dos tributos. |

**Perguntas ao contador.** Ficam só no documento 188 (D-N501), na Parte 7, com campo de resposta.

| Nº | Pergunta | No documento 188 |
|---|---|---|
| **Q196-C1** | A multa de 100% ou 66% do "tributo de referência" (art. 341-G, § 5º) incide **em separado** sobre o IBS e sobre a CBS, ou sobre a soma? E o IBS de 2027 a 2032 é mesmo o dobro da alíquota de referência da CBS? | C230 |
| **Q196-C2** | O adquirente contribuinte do regime regular pode apropriar crédito com base em **documento fiscal consolidado**, e como a operação é identificada para o crédito (art. 47)? | C231 |
| **Q196-C3** | No IS, quem é o **fabricante** (art. 424, I) quando a industrialização é por encomenda, e o valor de referência dos fumígenos vem do preço de varejo tabelado? | C232 |

# 7. Como conferi e limites

- **Texto da lei.** Li os arts. 341-A a 341-H, 330, 348, 22, 60, 414, 424 e 434 no texto da LC 227 e no consolidado do Planalto. O texto anterior dos arts. 414, 424 e 434 não está no ambiente.
- **Dicionário.** Procurei pelo nome de entidade e de campo, e pela descrição, no modelo da revisão 35 (1.138 entidades). "O dicionário tem" é por busca, não por conferência campo a campo.
- **Fontes secundárias.** A MP 1.399/2026 e a história do documento consolidado vêm de páginas de terceiros. O texto oficial da MP não abriu e não tentei outro caminho. Nada do que é número da MP entra em carga.
- **Exemplos.** As alíquotas de referência dos exemplos são hipotéticas. Os resultados são aritmética sobre o texto, e não parecer.
- **Contagens.** São a revisão 35, mais o documento 159 e mais este, somadas por mim; a conferência pelo gerador só acontece no "consolidar".
- **Nada foi validado pelo contador.** As cargas são provisórias.

# 8. Resultado

Nada aplicado (1.138 entidades e 12.769 campos). Se você aprovar o recomendado (A+ nas multas, sem campo no consolidado, `Cad_Is_Hipotese_Base` no IS), este documento acrescenta **+1 entidade e +19 campos** ao que o 159 propôs: **1.144 entidades, 12.860 campos, 3.365 campos de referência e 353 domínios** na revisão 36 (soma minha, a conferir no "consolidar"). A opção B das multas acrescentaria 3 entidades e 51 campos, e o esboço do consolidado, 1 entidade e 15 campos.
