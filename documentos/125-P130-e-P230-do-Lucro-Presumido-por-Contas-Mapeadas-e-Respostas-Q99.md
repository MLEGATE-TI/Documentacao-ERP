# P130 e P230 do lucro presumido por contas mapeadas, e as respostas às Q99-1 a Q99-6 — Documento 125

> **Nota de 27/10/2026 (documento 131):** a conferência com o manual **corrige** duas recomendações deste documento: o P130 e o P230 exigem também `OPT_REFIS` = S (Q125-5, e a seção 6 não vale quando diz que o desenho não exige o Refis) e o **X280 não pode ficar de fora** (Q125-7 foi substituída pela Q131-1).

> **Respostas de 27/10/2026 registradas (D-N372, documento 14); nada foi aplicado ao dicionário.** O dicionário continua na **revisão 24** (925 entidades e 10.033 campos); a revisão 25 (929 entidades e 10.096 campos com o que já espera) aguarda o seu "consolidar". Este documento tem duas partes: o que você respondeu e como li (seção 2), e o **desenho novo** que a sua resposta à Q99-1 pede (seções 3 a 8), com **sete perguntas** (Q125-1 a Q125-7) e a lista de campos que você precisa ver antes de eles entrarem.

*Documento pedido pela sua resposta à Q99-1 ("P130 e P230: estes dois itens podem ser incluídos agora, pois vão ser contas mapeadas para estes registros que vão compor os valores destes itens"). Estende o documento 99 (cadeia do lucro presumido). As leituras de norma e de prática contábil são minhas e **não foram conferidas** com o contador nem no texto oficial.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **O alcance muda:** o lucro presumido passa a ter **as seis abas do bloco P** (P130, P200, P230, P300, P400 e P500; 252 linhas), e não só o núcleo de quatro (132 linhas). Você respondeu **o contrário da minha recomendação** na Q99-1, e a sua resposta prevalece.
- **De onde vêm os valores do P130 e do P230:** de **contas contábeis mapeadas às linhas**, somadas por período, com ajuste do contador e motivo (a mesma ideia da Q99-2, que você aprovou para as "demais receitas e exclusões" do P200 e do P400).
- **O que falta no dicionário:** hoje uma conta só se liga a um **código do plano referencial** (`Cad_Conta_Contabil_Referencial`); **nada liga uma conta a uma linha de tabela dinâmica**. Proponho **1 entidade nova de mapeamento** (`Cad_Ecf_Linha_Mapeamento`, **10 campos**), que serve ao P130, ao P230, e também às linhas de "demais receitas e exclusões" do P200 e do P400 (a Q99-2).
- **O P230 quase não precisa de mapeamento:** das 38 linhas, **37 são cálculo** (lê o P130 e o P200) e **só a linha 38** (redução por reinvestimento) é editável. O peso do mapeamento está no **P130** (54 das 82 linhas são editáveis).
- **Campos aprovados que entram na revisão 25:** só o `Codigo_Referencia` (Q99-5, **1 campo**). Com a entidade de mapeamento, se você aprovar: **930 entidades e 10.107 campos** (seção 7).
- **Para o contador** (seção 6): o P130 e o P230 valem, pelo manual, para o presumido **optante pelo Refis** com isenção ou redução; o P130 **não tem os percentuais majorados** da LC 224/2025 nem o de 38,4%; e a redução por reinvestimento tem texto de orientação que fala só de períodos até 2013.

# 2. Suas respostas e como as li

| Item | Sua resposta | Como li |
|---|---|---|
| **Q99-1** | "P130 e P230: estes dois itens podem ser incluídos agora, pois vão ser contas mapeadas para estes registros que vão compor os valores destes itens" | **Não** à minha recomendação (deixar para a segunda etapa): os dois entram **agora**, junto com o núcleo. Li "contas mapeadas para estes registros" como **contas contábeis ligadas às linhas do P130 e do P230**, cujo saldo no período compõe o valor da linha. **Se você quis dizer contas do plano referencial P150, diga** (a Q125-1 pergunta isso) |
| **Q99-2** | "Sim" | As "demais receitas e exclusões" do P200 e do P400 (linhas 11 a 25.02 do P200 e 7 a 20 do P400) vêm da **soma das contas mapeadas ao plano referencial P150**, com **ajuste do contador e motivo**; o ERP não inventa valor onde não há mapeamento e **avisa** o contador |
| **Q99-3** | "Sim" | A conferência entre a apuração do ERP e a da ECF **só avisa**, sem bloquear a geração (diferença acima de R$ 0,01) |
| **Q99-4** | "Sim" | Vale para o presumido a **mesma decisão** que você der à Q93-7c e d (que **continuam sem resposta**): imposto a pagar = P300 15 e P500 13, com o adicional dentro do item do IRPJ e sem as linhas de RET e de imposto postergado. Se a Q93-7 mudar o desenho, o presumido muda junto |
| **Q99-5** | "Sim" | Entra o campo `Codigo_Referencia` (texto, opcional) em `Cad_Ecf_Tabela_Dinamica_Linha`: o código da linha sem pontos, único por aba e vigência; as 4 colisões da X480 ficam sem valor e vão para a lista de pendências da carga. **+1 campo** |
| **Q99-6** | "Sim" | As funções novas (`ARRED`, `CASO`, `PERIODO_PRIMEIRO`, `PERIODO_ULTIMO`, `CONTAR`, `ANO`, `COD_NAT` e a referência a outro período) valem como leitura **provisória** até a Receita responder (documento 98) |
| **Q99-7** | Enviou a ECF 2025 de uma empresa de presumido, com o texto "ECF lucro presumido" | Lido como a resposta. Teste no documento 126: **108 de 108** linhas calculadas do P200, P300, P400 e P500 batem (com arredondamento por linha). P130, P230 e LC 224 seguem sem prova: o arquivo é de 2025 e tem `IND_RED_ISEN` = N |

# 3. O que são o P130 e o P230 (lido da carga, leiaute 12)

**P130, "Demonstração das Receitas Incentivadas do Lucro Presumido"** (82 linhas; 54 editáveis, 9 de cálculo alterável, 10 de cálculo não alterável, 9 rótulos). São **nove blocos**, um por benefício, com a mesma forma:

| Linha do bloco | Tipo | O que é |
|---|---|---|
| 4 linhas de receita | editável | **Receita bruta sujeita ao percentual** de 1,6%, 8%, 16% e 32% |
| Lucro presumido da atividade | cálculo alterável | Soma de cada receita × o seu percentual |
| Ajustes decorrentes de métodos (preços de transferência) | editável | Valor do ajuste |
| Recuperação de custos e despesas | editável | Valor |
| Lucro presumido **ajustado** da atividade | cálculo não alterável | A soma das três linhas acima |

Os nove blocos são: **atividade isenta; redução de 75%, 70%, 50%, 33,33%, 25% e 12,5%; redução por reinvestimento; demais atividades**. A linha 82 soma os nove lucros ajustados. Essa lista **coincide com os benefícios do registro X280** do leiaute (isenção, reduções de 75%, 70%, 50%, 33,33%, 25% e 12,5%, reinvestimento), o que me faz ler cada bloco como "as receitas de um benefício reconhecido".

**P230, "Cálculo da Isenção e Redução do Lucro Presumido"** (38 linhas; 21 de cálculo alterável, 15 de cálculo não alterável, 1 rótulo, 1 editável). São **sete blocos** (isenção e as seis reduções), cada um com: o lucro ajustado da atividade (lido do P130), a parcela do lucro com o benefício (lucro × 1,00, 0,75, 0,70, 0,50, 0,3333, 0,25 ou 0,125), o **imposto** (15%) e o **adicional** (10% sobre o que passa de R$ 20.000 por mês do período) proporcionais à fatia incentivada, e o total do bloco. A linha 37 soma tudo. **A linha 38**, "redução por reinvestimento" (válida desde 2020), é **editável** e é lida pelo P300 linha 9.

**Quem lê o quê:** o P230 lê o **P130** (lucros ajustados) e o **P200** (linhas 26, a base do IRPJ, e 22, o excedente de variação cambial) e usa `MESES_PERIODO()` (3 no trimestre). O resultado vai para o **P300**: a linha 8 ("isenção e redução do imposto") é **editável** na planilha, com o limite "não pode ser maior que a soma das linhas 3, 4 e 5", e a linha 9 (reinvestimento) é calculada a partir do P230 linha 38.

# 4. Como os valores nascem (proposta)

## 4.1 O mapeamento de contas às linhas

**O problema.** O P130 pede receita **por benefício e por percentual**. O dicionário já tem a receita por atividade e percentual (`Mov_Apuracao_Presuncao_Atividade`), mas **sem a dimensão do benefício**: uma conta de receita não diz se a receita é incentivada. A sua resposta resolve isso mapeando **a conta** à **linha**: a conta "receita de serviços do projeto na área da Sudene" é ligada à linha "redução de 75%, receita sujeita a 32%" do P130.

**A entidade nova (proposta; você ainda não a viu).**

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Linha_Mapeamento** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa para a qual o mapeamento vale |
| **ID_Tabela_Linha** | *referência (Cad_Ecf_Tabela_Dinamica_Linha)* | A linha **editável** que recebe a soma (do P130, e, pela Q99-2, do P200 e do P400). Linha de cálculo ou rótulo não aceita mapeamento |
| **Tipo_Origem** | *enumeração {conta_contabil, codigo_referencial}* | De onde sai o valor: de uma conta da empresa, ou do conjunto de contas ligadas a um código do plano referencial |
| **ID_Conta_Contabil** | *referência (Cad_Conta_Contabil), opcional* | Obrigatória quando a origem é `conta_contabil`. Conta **analítica** de resultado |
| **ID_Codigo_Referencial** | *referência (Cad_Plano_Referencial_Conta), opcional* | Obrigatório quando a origem é `codigo_referencial`: um código **vigente** do plano P150 da empresa (a regra de escolha do plano é a da revisão 18). As contas ligadas a ele por `Cad_Conta_Contabil_Referencial` entram na soma |
| **Operacao** | *enumeração {somar, subtrair}* | Como o saldo entra na linha |
| **Vigencia_Inicio**, **Vigencia_Fim**, **Motivo_Vigencia** | *data, data, texto opcional* | Vigência própria do mapeamento, no padrão de `Cad_Conta_Contabil_Referencial` |

**Regras propostas:**

- **Valor da linha** = soma, na `Operacao`, do **movimento líquido do período** (o trimestre da apuração) das contas mapeadas, na natureza da conta de resultado (receita: créditos menos débitos).
- Uma conta **não entra em duas linhas da mesma aba** na mesma vigência (evita contar duas vezes); o ERP bloqueia.
- **Sem mapeamento**, o ERP **não inventa valor** e avisa o contador (Q99-2). **Ajuste do contador** com motivo: o campo `Eh_Alterado` e o motivo de `Mov_Ecf_Apuracao_Linha_Valor` já existem.
- `Mov_Ecf_Apuracao_Linha_Valor.Origem` ganha o valor **`contas_mapeadas`** (hoje {calculo, lancamento, manual, importado_ecf}). **0 campos.**
- **Regime de caixa:** o movimento da conta segue a **contabilidade** (competência). A empresa que apura a receita do presumido por caixa precisa do **ajuste do contador** com motivo (o documento 99 já registrava o ponto; ver seção 6).

## 4.2 A fonte de cada grupo de linhas

| Linhas | Fonte proposta |
|---|---|
| **P130, 4 linhas de receita dos oito blocos incentivados** (isenta, 75%, 70%, 50%, 33,33%, 25%, 12,5% e reinvestimento) | **Contas mapeadas** à linha (o benefício e o percentual estão na linha) |
| **P130, 4 linhas de receita da "demais atividades"** (74 a 77) | **O total da receita por percentual** (o que a apuração já guarda e alimenta o P200 2, 4, 6 e 8) **menos** a soma dos oito blocos incentivados, no mesmo percentual (**Q125-2**) |
| **P130, ajustes de preços de transferência e recuperação de custos** (2 por bloco) | **Contas mapeadas**, com ajuste do contador (as mesmas linhas existem no P200 e entram na Q99-2) |
| **P130, linhas de cálculo** (lucro da atividade, lucro ajustado, total) | **Fórmula** da planilha |
| **P230, linhas 2 a 37** | **Fórmula** da planilha (lê P130 e P200). Não há valor a mapear |
| **P230, linha 38** (redução por reinvestimento) | **Digitada pelo contador, com motivo** (**Q125-3**) |
| **P300, linha 8** (isenção e redução do imposto) | O ERP **preenche com o P230 linha 37** e o contador pode alterar com motivo (**Q125-4**) |

## 4.3 Quando o P130 e o P230 existem

O perfil fiscal já guarda os indicadores do registro 0020 (revisão 17), entre eles o **`IND_RED_ISEN`** (isenção e redução do imposto para o lucro presumido). **Proponho:** o P130 e o P230 são gerados **só quando** a forma de tributação é lucro presumido **e** o indicador é **sim**; fora disso as duas abas não existem para a empresa (**Q125-5**). Se uma conta mapeada ao P130 tiver movimento com o indicador em **não**, o ERP **avisa**.

## 4.4 Exemplo (valores ilustrativos)

Trimestre com receita de serviços de **R$ 600.000**, tudo no percentual de 32%. **R$ 200.000** estão numa conta mapeada à linha P130 **14** (bloco de redução de 75%, receita sujeita a 32%). Sem outras receitas nem exclusões.

| Passo | Conta | Resultado |
|---|---|---|
| P130 14 (conta mapeada) | Saldo do período da conta | **R$ 200.000** |
| P130 77 (demais atividades, 32%) | 600.000 − 200.000 | **R$ 400.000** |
| P130 15 e P130 18 (bloco de 75%) | 200.000 × 0,32 | **R$ 64.000** |
| P130 78 e P130 81 (demais) | 400.000 × 0,32 | **R$ 128.000** |
| P130 82 | 64.000 + 128.000 | **R$ 192.000** |
| P200 26 (base do IRPJ) | 600.000 × 0,32 | **R$ 192.000** |
| P300 3 e 4 (imposto e adicional integrais) | 192.000 × 15% = 28.800; (192.000 − 60.000) × 10% = 13.200 | **R$ 28.800 e R$ 13.200** |
| P230 9 (imposto do bloco de 75%) | 192.000 × 0,15 × 0,75 × (64.000 / 192.000) | **R$ 7.200** |
| P230 10 (adicional do bloco) | 132.000 × 0,10 × 0,75 × (64.000 / 192.000) | **R$ 3.300** |
| P230 11 e P230 37 | 7.200 + 3.300 | **R$ 10.500** |
| P300 8 (isenção e redução) | Preenchida com P230 37; limite: 42.000 | **R$ 10.500** |
| P300 15 (IRPJ a pagar) | 28.800 + 13.200 − 10.500 | **R$ 31.500** |

*Conferência por fora:* a fatia incentivada é um terço do lucro; o imposto integral dela é R$ 14.000 e o benefício de 75% tira R$ 10.500, que é 75% de R$ 14.000. O limite de 20.000 por mês é de 60.000 no trimestre.

# 5. Conferências (só avisos, como na Q99-3)

| Conferência | Regra proposta |
|---|---|
| **Receita do P130 contra a do P200** | A soma, por percentual, dos nove blocos do P130 = a receita do P200 no mesmo percentual (2, 4, 6 e 8). Pela Q125-2 ela fecha por construção; o aviso vale quando o contador alterar uma linha |
| **P300 8 contra P230 37** | Se o contador alterou a linha 8, mostra a diferença e o motivo |
| **P300 8 acima de P300 3 + 4 + 5** | Excede o limite da orientação da linha: aviso (o PVA da Receita pode recusar) |
| **P230 6 contra o X280** | Uma página de ajuda de software que li diz que o PVA exige que a soma do valor de incentivo do X280 com benefício "01 isenção" seja igual à soma do P230 linha 6 nos quatro trimestres ([Alterdata](https://ajuda.alterdata.com.br/prosoftcontabil/c1490-sped-ecf-registro-p230-x280-148076623.html)). **O dicionário não tem o X280** (ver Q125-7), então esta conferência **não existe** hoje |
| **Mapeamento sem saldo** ou conta de resultado com movimento e sem mapeamento | Aviso ao contador, linha a linha |

# 6. Para o contador (fora do desenho)

- **Quem usa o P130 e o P230.** O texto do campo `IND_RED_ISEN` do 0020 diz que é a PJ do lucro presumido **optante pelo Refis** que usufrui isenção ou redução do imposto, e a descrição do P130 que li num leiaute publicado por um software diz o mesmo ([Senior](https://documentacao.senior.com.br/goup/5.10.3/Menu_Controladoria/sped/contabil-fiscal-ecf/bloco-p.htm)). O desenho **não exige o Refis**: só o indicador. O contador diz se a condição existe. Uma página de consultoria que li diz que o lucro presumido está **excluído** do benefício de 75% da Sudam e da Sudene (seção 9), o que não casa com o P230.
- **Percentuais majorados da LC 224/2025 e 38,4%.** O P130 só tem 1,6%, 8%, 16% e 32%; o P200 tem 38,4% e, a partir de 2026, o acréscimo de 10% sobre a faixa que passa do limite. O P130 **não tem onde informar** isso. O desenho segue o P130 como publicado, e o contador diz como a Receita espera o dado.
- **Redução por reinvestimento.** A orientação da linha P300 9 fala em depósito nos bancos regionais e em **períodos até 31/12/2013**, e a linha do P230 vale desde **2020**. O contador diz se a redução ainda se aplica e como se informa (por isso a Q125-3 recomenda digitar).
- **Regime de caixa.** Receita do presumido por caixa não coincide com o movimento contábil por competência (documento 99, seção 5).
- **O documento 99 (seção 10) diz** que os capítulos das Perguntas e Respostas que li confirmam "a ausência de incentivo no presumido". Isso **não casa** com a existência do P130 e do P230. Leio a frase como "sem incentivos de dedução do imposto" (por exemplo, programas que deduzem imposto do lucro real); **não reli o capítulo**. O contador confirma, e eu corrijo o documento 99.

# 7. O que muda no dicionário

| Item | Efeito | Campos |
|---|---|---|
| **Q99-5 (aprovada)** | `Codigo_Referencia` em `Cad_Ecf_Tabela_Dinamica_Linha` | **+1** |
| Q99-6 (aprovada) | Texto da seção de funções: leitura provisória; sem campo | 0 |
| Q99-2, Q99-3, Q99-4 (aprovadas) | Regras da apuração do presumido (fonte por contas mapeadas, conferência só aviso, imposto a pagar); sem campo, e dependem da entidade da Q125-1 para a Q99-2 | 0 |
| **Q125-1, se aprovada** | Entidade `Cad_Ecf_Linha_Mapeamento` (seção 4.1) | **+1 entidade, +10** |
| Q125-1 | Valor `contas_mapeadas` em `Mov_Ecf_Apuracao_Linha_Valor.Origem` | 0 |
| Q125-6, se aprovada | P200 26 e P400 21 em duas linhas de vigência cada (como a Q93-1; doc 99 seção 2): **+2 linhas de carga**, 0 campos | 0 |
| Carga do P130 e do P230 | Já está na carga (82 e 38 linhas); nada muda | 0 |

**Contagem:**

| Cenário | Entidades | Campos |
|---|---|---|
| Revisão 25 prevista antes desta rodada (documentos 123 e 124) | 929 | 10.096 |
| Com a Q99-5 (aprovada) | 929 | **10.097** |
| Com a entidade de mapeamento (Q125-1) | **930** | **10.107** |

# 8. Perguntas

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q125-1** | O mapeamento é **uma entidade só** (`Cad_Ecf_Linha_Mapeamento`, 10 campos), que liga **conta contábil** (P130) ou **código do plano P150** (P200 e P400, Q99-2) a uma linha editável? Ou você queria só **código do plano referencial** também para o P130? | Entidade única. O P130 precisa de **conta** porque o código do P150 não diz se a receita é incentivada |
| **Q125-2** | As quatro linhas de "**demais atividades**" do P130 (74 a 77) saem do **total da receita por percentual menos os oito blocos incentivados**, e só as contas incentivadas são mapeadas? | Sim: mapear toda a receita da empresa seria trabalho sem ganho |
| **Q125-3** | A linha 38 do P230 (**redução por reinvestimento**) é **digitada pelo contador, com motivo**, e não por contas mapeadas? | Sim: é um valor de imposto com condições, e não saldo de conta |
| **Q125-4** | O ERP **preenche o P300 linha 8** com o P230 linha 37, e o contador pode alterar com motivo? | Sim |
| **Q125-5** | O P130 e o P230 só são gerados com **lucro presumido e o indicador `IND_RED_ISEN` = sim** no perfil? | Sim |
| **Q125-6** | **P200 26 e P400 21** (duas versões de fórmula no mesmo texto, até 2025 e a partir de 2026) são divididas em **duas linhas de vigência**, como as 11 da Q93-1? | Sim (sem isso o motor lê o texto inteiro) |
| **Q125-7** | O **X280** (atividades incentivadas) **fica de fora agora**? Ele guarda ato concessório, órgão, projeto, vigência e receita líquida por benefício, e a Receita confere o P230 linha 6 contra ele | Sim, fica de fora; o contador diz se o ERP deve gerá-lo, e então o desenho entra junto da lista do bloco X |

**Também confirme** as duas leituras da seção 2: a da **Q99-1** (contas contábeis ligadas às linhas, e não só códigos do P150) e a da **Q99-4** ("sim" como adoção do desenho do documento 99, atado à Q93-7).

# 9. Limites do que li

- Li a **carga** das abas P130, P230, P200 (linhas 20.01 a 26) e P300 (linhas 1 a 17), com fórmulas e orientações; as **descrições do 0020 e do X280** do leiaute 12; os documentos 88, 93, 99 e 118; e o dicionário na revisão 24.
- Das páginas externas, a [Alterdata (P230 e X280)](https://ajuda.alterdata.com.br/prosoftcontabil/c1490-sped-ecf-registro-p230-x280-148076623.html) trata só da validação P230 6 contra o X280 e não menciona o P130; a [Senior](https://documentacao.senior.com.br/goup/5.10.3/Menu_Controladoria/sped/contabil-fiscal-ecf/bloco-p.htm) lista os campos do P130 e do P230 (iguais), com a observação sobre o Refis. A [Planning (Sudam e Sudene)](https://planning.com.br/incentivos-sudam-sudene-irpj/) diz que o lucro presumido está **excluído** do benefício de 75%, o que **contraria** o P230 da planilha; **não resolvi isso** e o deixo para o contador, junto do ponto do Refis.
- **Não provei** o desenho contra arquivo real de ECF: o arquivo de presumido que você enviou (documento 126) prova o núcleo (P200, P300, P400 e P500) em 2025, mas **não tem P130 nem P230** (`IND_RED_ISEN` = N), então estes dois seguem sem prova.
- Nada foi validado pelo contador.
