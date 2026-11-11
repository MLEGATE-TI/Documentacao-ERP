# Cálculo da Cadeia do Lucro Presumido da ECF (P200, P300, P400 e P500) — Documento 99

> **Respondido em 27/10/2026 (D-N372, documento 125): Q99-2 a Q99-6 sim; Q99-1 não: P130 e P230 entram agora, por contas mapeadas às linhas (desenho no documento 125, com as perguntas Q125-1 a Q125-7). Q99-7 respondida pelo envio de uma ECF real de presumido de 2025, provada no documento 126 (108 de 108 linhas calculadas; LC 224 sem prova). Nada foi aplicado ao dicionário;** o Q99-5 (`Codigo_Referencia`) entra na revisão 25. Onde o texto abaixo diz que P130 e P230 ficam para a segunda etapa, vale esta nota.

*Proposta de desenho, no mesmo molde do documento 93 (lucro real): o ERP calcula as abas do lucro presumido da ECF interpretando as fórmulas guardadas no cadastro. É um relatório e uma proposta: **nada foi alterado no dicionário**. Só entra depois das suas respostas e do seu "consolidar", com a lista de campos que você tiver visto.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Por que existe:** você pediu o desenho do lucro presumido depois de enviar os capítulos VI e XIII das Perguntas e Respostas da PJ. O documento 93 só cobre o **lucro real**. As abas do lucro presumido da ECF são as do **bloco P**: P130, P200, P230, P300, P400 e P500. (O bloco T é o lucro arbitrado e o U é imunes e isentas; em uma versão anterior do documento 98 eu os troquei, e já corrigi.)
- **Tamanho:** o núcleo (P200, P300, P400, P500) tem **132 linhas e 64 fórmulas**. P130 (receitas incentivadas, 82 linhas, 19 fórmulas) e P230 (isenção e redução, 38 linhas, 36 fórmulas) ficam para uma segunda etapa.
- **Proposta central: não criar entidade nova para o núcleo.** O motor do documento 93 (`Mov_Ecf_Apuracao_Linha_Valor`, que guarda um valor por linha e por apuração, e `Mov_Ecf_Escolha_Contador_Ano`) já serve ao presumido. O que muda é a **leitura**: mais funções na linguagem da fórmula (seção 4), a fonte dos valores das linhas editáveis (seção 5) e um aviso de conferência entre a apuração do ERP e a da ECF (seção 6).
- **O dicionário já calcula o presumido:** `Mov_Apuracao_Presuncao_Atividade`, `Mov_Apuracao_Presuncao_Limite` e `Mov_Apuracao_Presuncao_Ajuste_Anual` guardam o acréscimo da LC 224/2025 (limite de R$ 1.250.000 por trimestre, saldo entre trimestres, ajuste anual). As linhas 25100 a 25250 do P200 e 18100 a 18500 do P300 e do P500 refazem a mesma conta na ECF. Hoje são **dois cálculos do mesmo número**, e é isso que vale conferir.
- **A planilha da Receita tem erros nessas abas** (percentual `0,348`, parênteses que não fecham, indicadores 7 e 8 que a linha P500 2 ignora). Eles estão no documento 98, perguntas 2, 3 e 7. Até a resposta, o ERP avisa e não calcula a linha afetada.
- **Perguntas:** 7 (seção 8). Nenhuma delas altera o que já foi consolidado.

# 2. O que entra no cálculo

| Aba | Papel | Linhas | Fórmulas | Linhas que mudam em 2026 (LC 224/2025) |
|---------------|--------------------------------------------|------|--------|----------------|
| P200 | Base de cálculo do IRPJ: receita bruta por percentual (1,6%, 8%, 16%, 32%, 38,4%), mais as demais receitas e ganhos, menos as exclusões | 47 | 18 | 22 |
| P300 | IRPJ: 15%, adicional, deduções, imposto a pagar | 24 | 9 | 6 |
| P400 | Base de cálculo da CSLL: receita bruta por percentual (12%, 32%, 38,4%) e as mesmas somas | 39 | 28 | 17 |
| P500 | CSLL: alíquota, deduções, CSLL a pagar | 22 | 9 | 6 |
| P130 | Demonstrativo das receitas incentivadas | 82 | 19 | 0 |
| P230 | Isenção e redução do IRPJ (lucro da exploração) | 38 | 36 | 0 |

**Cadeia de dependência (lida das referências das fórmulas):** P200 → P300 (base do IRPJ e adicional), P400 → P500 (base da CSLL), P200 e P400 → blocos da LC 224/2025 (acréscimo), P230 → P300 (redução por reinvestimento, linha 9), P300 → P500 (receitas da atividade imobiliária pelo RET, linha 14).

**Duas versões de fórmula (a regra do Q93-1, dividir por vigência):** P200 26 e P400 21 têm texto "Até 31/12/2025" e "A partir de 01/01/2026" na mesma linha. Pela decisão do documento 93, cada uma vira duas linhas de vigência (2 linhas a mais). P200 24 (resultados não tributáveis de cooperativas) também tem duas versões, mas já vem separada na planilha (até 2025 e a partir de 2026).

**Tipos de linha:** o P200 tem 27 linhas editáveis, 18 de cálculo não alterável e 2 rótulos; o P300, 12 editáveis, 8 de cálculo não alterável, 1 de cálculo alterável e 3 rótulos; o P400, 12 editáveis, 15 de cálculo não alterável, 10 de cálculo alterável e 2 rótulos; o P500, 11 editáveis, 7 de cálculo não alterável, 2 de cálculo alterável e 2 rótulos.

# 3. O que o presumido herda do documento 93

| Tema | Como fica no presumido |
|-----------------------------|----------------------------------------------------------|
| Valor por linha e por apuração | `Mov_Ecf_Apuracao_Linha_Valor` como está (10 campos). A apuração é a de `Mov_Apuracao_Irpj_Csll` com `Regime_Aplicado` = lucro_presumido e `Tipo_Apuracao` = trimestral |
| Forma de tributação e segmento | Pelo perfil fiscal (revisão 18): `ID_Forma_Tributacao_Ecf` = lucro presumido escolhe o conjunto P130, P200, P230, P300, P400, P500; o segmento (PJ em geral ou financeiras) escolhe o plano referencial P100 e P150 |
| `0020.IND_ALIQ_CSLL` | Escolha do contador por ano (Q93-5), na entidade `Mov_Ecf_Escolha_Contador_Ano`. A fórmula do P500 2 lê o indicador de lá |
| Indicadores 7 e 8 | A fórmula da P500 2 não os trata (documento 98, pergunta 3). Vale a regra da Q93-5b: o ERP para a linha, avisa e espera o valor do usuário. Pista: a linha P500 18300 da própria planilha usa 9% (código 7) ou 15% (código 8) em T01 de 2026 e 12% ou 17,5% nos demais trimestres |
| Linha alterada pelo contador | `Eh_Alterado`, `Motivo_Alteracao` e `Valor_Calculado_Com_Sinal`, como no documento 93 |
| Majoração da LC 224/2025 | A ECF sempre calcula com a majoração (requisito já registrado em `Mov_Apuracao_Decisao_Risco`); o valor não recolhido aparece como tributo devido não pago |
| Imposto a pagar | **A resposta da Q93-7 vale por analogia**: P300 15 (IRPJ a pagar) e P500 13 (CSLL a pagar), com o adicional dentro do item do IRPJ e sem dedução do adicional (as Perguntas e Respostas XIII-025 e VI-030 confirmam). Linhas 16 e 17 (RET e imposto postergado) fora do "a pagar". Fica para a Q93-7c e d, se você concordar |

# 4. A linguagem das fórmulas: o que o presumido acrescenta

O documento 93 listou as funções das fórmulas do lucro real. As abas do presumido usam outras, que o ERP precisa entender:

| Função ou construção | Usos | Onde | Leitura |
|---------------------------|------|------------------------|--------------------------------------------------|
| `ARRED(x)` | 9 | P300 18300 e 18500, P500 18300 | Arredonda para duas casas |
| `CASO(x) IGUAL("T01") ... FIM_IGUAL ... CASO_CONTRARIO ... FIM_CASO` | 2 | P200 25120, P400 20120 | Seleção por valor: soma da receita dos trimestres anteriores do ano. A sintaxe vem grudada na planilha (`CASO(PERIODO_ATUAL())IGUAL("T01")0FIM_IGUAL`) |
| `PERIODO_PRIMEIRO()` e `PERIODO_ULTIMO()` | 38 | P200, P400, P300 e P500 (LC 224) | Primeiro e último trimestre em atividade no ano. O último é onde sai o ajuste anual |
| `CONTAR(P030(*))` | 2 | P200 25180, P400 20180 | Quantidade de períodos em atividade no ano (registro P030): limite anual = quantidade × R$ 1.250.000 |
| `ANO(0000.DT_INI())` | 2 | P500 18300 | O ano da escrituração |
| `0030.COD_NAT()` | 1 | P200 24 | Natureza jurídica do registro 0030 (código 2143, cooperativa) |
| Referência a outro período: `P200(2:9;"T01")` e `P200("25.130";PERIODO_ULTIMO())` | vários | P200, P400, P300, P500 | Valor da linha em outro trimestre do mesmo ano. O ERP lê o `Mov_Ecf_Apuracao_Linha_Valor` da apuração daquele trimestre |
| Intervalo com `SOMA(x(a:b))` e `SOMA(x(a:b;periodo1:periodo2))` | 47 | todas | Soma por intervalo de linhas e, na LC 224, também por intervalo de períodos |

**Ordem de cálculo entre trimestres:** a linha do último trimestre lê valores do primeiro ao penúltimo; o ERP precisa ter calculado e confirmado T01 a T03 antes de calcular T04. Se um trimestre anterior estiver pendente (`pendente_decisao`), o ERP avisa em vez de calcular o ajuste.

# 5. De onde vêm os valores das linhas editáveis

O documento 93 já previu que as linhas "editáveis" vêm da Parte A do e-Lalur. No presumido **não há Parte A**. Por isso a fonte é outra:

| Linhas | O que são | Fonte proposta |
|----------------------------|----------------------------------|----------------------------------------------------|
| P200 2, 4, 6, 8 e 9; P400 2, 4 e 5 | Receita bruta por percentual de presunção | `Mov_Apuracao_Presuncao_Atividade.Receita_Bruta_Atividade`, somada por percentual padrão da atividade (IRPJ: 1,6, 8, 16, 32 e 38,4; CSLL: 12, 32 e 38,4). Já existe |
| P200 11 a 20.01; P400 7 a 16.01 | Rendimentos de aplicação financeira, juros sobre o capital próprio, valores diferidos, recuperação de custos, preços de transferência, multas por rescisão, lucros e rendimentos do exterior, variações cambiais, demais receitas e ganhos de capital, contraprestação de arrendamento | **A decidir (Q99-2).** O dicionário tem as receitas por atividade, mas não vi hoje uma entidade que guarde essas outras receitas acrescidas ao lucro presumido, trimestre a trimestre. As Perguntas e Respostas XIII-014 listam as sete parcelas |
| P200 22 a 25.02; P400 18 a 20 | Exclusões (excedente de variação cambial, resultados de cooperativa, divulgação eleitoral) | A decidir (Q99-2), com a mesma resposta |
| P300 e P500, linhas de dedução (retenções, imposto pago no exterior, isenções) | Deduções do imposto e da CSLL | `Mov_Apuracao_Irpj_Csll_Item.Valor_Deducoes`, que já guarda "incentivos, retenções na fonte e estimativas já pagas" (o presumido não tem estimativa) |
| P300 5 | Diferença de imposto pela mudança de coeficiente | Digitada pelo contador, com motivo |
| P300 16 e 17; P500 14 e 15 | Receitas do RET e imposto ou CSLL postergado | Digitadas pelo contador (como no lucro real) |

**Regime de caixa:** as Perguntas e Respostas XIII-038 tratam do regime de reconhecimento de receitas no presumido (caixa ou competência). A escolha muda o momento em que a receita entra na linha; a ECF só lê o resultado da apuração. A conferir: se a apuração do presumido do dicionário já distingue caixa e competência.

# 6. Conferência entre a apuração do ERP e a da ECF

O ERP calcula o presumido em `Mov_Apuracao_Presuncao_*` (revisões 4 e 5) e a ECF recalcula o mesmo valor pelas fórmulas da Receita. Proposta: **o cálculo da ECF não substitui o da apuração; o ERP compara e avisa**, como já faz na DeRE (Q96-1: avisa se der diferente, não bloqueia).

| Comparação | Valor no ERP | Valor na ECF |
|------------------------|-------------------------------------|------------------------------------------|
| Base do IRPJ do trimestre | `Mov_Apuracao_Irpj_Csll_Item.Base_Calculo_Com_Sinal` (IRPJ) | P300 1 (igual a P200 26) |
| Base da CSLL do trimestre | idem (CSLL) | P500 1 (igual a P400 21) |
| Adicional da LC 224 | `Mov_Apuracao_Presuncao_Atividade` (faixa majorada) | P200 25200 a 25250 |
| Limite ajustado e excedente | `Mov_Apuracao_Presuncao_Limite` | P200 25140 a 25190 |
| IRPJ, adicional e CSLL a pagar | `Valor_A_Pagar` do item | P300 15 e P500 13 |
| Ajuste anual (tributo a maior) | `Mov_Apuracao_Presuncao_Ajuste_Anual` | P300 18300 e 18500; P500 18300 e 18500 |

Diferença acima de R$ 0,01 gera aviso para o contador, que decide qual valor vale (aprovando a linha com `Eh_Alterado` e motivo). **Pode ser que a diferença seja erro da planilha** (documento 98): o aviso mostra a linha e a fórmula, para o contador comparar com o PVA da Receita.

# 7. Achados que afetam o cálculo

- **Percentual `0,348`** na linha P500 18200 (deveria ser `0,384`): documento 98, pergunta 7.
- **Parênteses que não fecham** nas linhas P200 25210 a 25250 e P300 9: documento 98, pergunta 2.
- **P500 2 sem os indicadores 7 e 8**, enquanto a P500 18300 os trata: documento 98, pergunta 3.
- **Códigos de linha escritos de dois jeitos.** A planilha publica alguns códigos como número (por exemplo `25110`, `51100`, mostrados como "25.110" com separador de milhar) e as fórmulas os citam com ponto (`P200("25.110")`). Na carga, **165 referências** de fórmula citam o código com ponto e a linha foi gravada sem ponto (por exemplo `N600("3.100")` aponta a linha `3100`). Outros códigos foram gravados com ponto como texto (80 linhas, como `17.951`). O motor precisa comparar **sem os pontos**. Há **4 colisões** na aba X480 (`1.1` e `11`, `18.1` e `181`, `19.1` e `191`, `21.1` e `211`), fora do escopo desta proposta. Isso vale também para o documento 93 (lucro real), cujas fórmulas também citam códigos com ponto (por exemplo no N600).
- **Funções sem definição** (documento 98, pergunta 5): `ARRED`, `CASO` e `CONTAR` também não estão no manual. A leitura das seções 4 é a mais provável, mas não confirmada.

# 8. Perguntas para você

| Nº | Pergunta | Recomendação |
|------|------------------------------------------------------------|------------------------------------------------------|
| Q99-1 | **Alcance.** Começar pelo núcleo (P200, P300, P400, P500; 132 linhas e 64 fórmulas) e deixar P130 e P230 para a segunda etapa, junto com o N610 do lucro real (mesma lógica de isenção e redução)? | Sim. P230 e P130 dependem de lucro da exploração e de incentivos, que o lucro real já precisa desenhar |
| Q99-2 | **Fonte das "demais receitas e exclusões"** (P200 11 a 25.02 e P400 7 a 20: rendimentos de aplicação, JCP, recuperação de custos, preços de transferência, multas, ganhos de capital, exterior, cooperativa). Preencher por **soma das contas mapeadas** ao plano referencial P150 (como o L300 faz no lucro real), com ajuste do contador e motivo? Ou o contador digita cada linha por trimestre? | Por contas mapeadas, com ajuste e motivo; o ERP não inventa valor onde não houver mapeamento e avisa o contador |
| Q99-3 | **Conferência** entre a apuração do ERP e a da ECF (seção 6): só aviso, sem bloquear a geração? | Sim, só aviso |
| Q99-4 | **Imposto a pagar do presumido** (P300 15 e P500 13; adicional dentro do item do IRPJ; RET e postergado fora): vale a mesma resposta que você der à Q93-7c e d? | Sim, uma decisão só para os dois regimes |
| Q99-5 | **Campo `Codigo_Referencia`** (texto, opcional) em `Cad_Ecf_Tabela_Dinamica_Linha`: o código da linha sem pontos, para resolver as referências das fórmulas (seção 7). Único por aba e vigência; as 4 colisões da X480 ficam sem valor e vão para a lista de pendências da carga. Aprova? | Sim, 1 campo; evita adivinhar o código a cada leitura |
| Q99-6 | **Funções novas** (seção 4: `ARRED`, `CASO`, `PERIODO_PRIMEIRO`, `PERIODO_ULTIMO`, `CONTAR`, `ANO`, `COD_NAT` e referência a outro período). Aprova a leitura como provisória até a Receita responder (documento 98, pergunta 5)? | Sim, provisória, com teste em ECF real de presumido (você tem alguma para enviar?) |
| Q99-7 | **Teste.** Para provar o desenho como fez com o lucro real, envio de **um ou dois arquivos reais de ECF de lucro presumido** (de preferência 2025, trimestral, sem LC 224, e um de 2026 se houver) para eu rodar as fórmulas contra os valores gravados. Pode enviar? | Sim, sem isso as fórmulas da LC 224 ficam sem prova |

# 9. Se tudo for aprovado

| | Revisão 20 | Com este documento |
|----------------------------|--------------|------------------------------------------------|
| Entidades | 915 | 915 (nenhuma nova) |
| Campos | 9.878 | 9.879 (só `Codigo_Referencia`, se a Q99-5 for aprovada) |
| Linhas de carga das tabelas dinâmicas | 4.475 | 4.477 (P200 26 e P400 21 passam a duas linhas de vigência cada) |

*A contagem soma só a Q99-5 e a divisão das duas fórmulas. As contagens do documento 93 (revisão 21: `Mov_Ecf_Apuracao_Linha_Valor`, `Mov_Ecf_Escolha_Contador_Ano`, `Base_Estimativa`, 22 linhas de vigência) continuam à parte e só entram quando você mandar "consolidar".*

# 10. Limites

- O desenho cobre o **lucro presumido anual por trimestre**. O presumido de SCP e o de entidade de futebol (bloco S) ficam fora.
- **Não é parecer tributário.** As regras vêm da planilha da Receita (leiaute 12, 24/09/2026), das Perguntas e Respostas da PJ (capítulos VI e XIII, edições de 2020 e 2021, anteriores à LC 224/2025) e dos documentos 51, 53 e 54 do projeto. Os capítulos de 2020 e 2021 confirmam o adicional integral sem deduções, a ausência de incentivo no presumido e a compensação do imposto pago a maior; não tratam da LC 224/2025.
- As fórmulas da LC 224/2025 não foram provadas contra arquivo real: o arquivo enviado na Q99-7 é de 2025 (documento 126). A conferência de caixa e competência da seção 5 está respondida no documento 126, seção 6.3: a apuração do presumido do dicionário **não** distingue os dois critérios.
