# Dedução de material e de gênero alimentício na base das retenções: INSS (IN RFB 2.110) e IR, CSLL, PIS e Cofins (IN RFB 1.234) — Documento 210

> **O que este documento faz.** Na pergunta Q210-1 (seção 1.35 do documento 38) você escolheu **desenhar** o que a Solução de Consulta Cosit 220/2026 mostrou que falta no dicionário: **onde o ERP guarda o material, o equipamento e o gênero alimentício que a contratada fornece junto com o serviço**, e como isso muda a retenção. Ao ler as normas, achei que **a seção 1.35 e a D-N549 juntaram dois mecanismos diferentes** e corrijo isso aqui: no **INSS** o material **sai da base** de cálculo; na **IN 1.234** o material **não deduz nada**, só decide **qual linha de percentual** (5,85% ou 9,45%) vale sobre o pagamento inteiro.
>
> **Resposta (11/11/2026, D-N561):** "Q210-2 a Q210-12 - Seguir as recomendações". O documento está **aprovado inteiro**; as recomendações "sim, provisório" das Q210-6 (10 linhas de piso) e Q210-12 (ordem do art. 120, C299) valem como provisórias. **Ainda não aplicado ao dicionário**: entra no próximo "consolidar".

> **Nada foi aplicado ao dicionário.** Ele está na revisão 41 (1.201 entidades e 13.801 campos). Este documento só vale com a sua resposta às Q210-2 a Q210-12. A Q210-13 foi respondida com o texto oficial da IN 2.110, que você enviou, e a Q210-14 com "sim, há clientes".

*Fontes: Solução de Consulta Cosit 220/2026 (DOU de 11/11/2026), que você enviou; IN RFB 2.110/2022, **texto do DOU de 19/10/2022 (190 páginas), que você enviou** (arts. 110, 114 a 125, 130, 276 e 277 lidos no texto oficial; **é o texto original, sem as alterações posteriores**); guia "Orientações IRRF – IN 1.234/12" da Prefeitura de São Paulo (versão de 29/06/2023, com o Anexo I adaptado, só do IR); Solução de Consulta Disit/SRRF04 4042/2026; IN RFB 1.234/2012 (**DOU de 12/01/2012, página 22, e a versão multivigente impressa em 18/03/2019, os dois PDFs que você enviou em 11/11/2026**; e o art. 2º no texto do site Normas Legais, última alteração listada: IN RFB 2.257/2025); páginas de comentário (Tributo Devido, Foco Tributário, Migalhas), usadas só para localizar os artigos; dicionário na revisão 41 e os documentos 14, 38, 51 e 188.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **São dois mecanismos, e o ERP precisa dos dois.** **(A) INSS** (retenção de 11%, ou 3,5% se o prestador é da CPRB; IN 2.110, arts. 116 a 119): o valor do material, do equipamento (que não seja manual) e, pela SC 220, do **gênero alimentício** fornecidos pela contratada **sai da base**, com prova e, em alguns casos, com **piso** (a base não pode ficar abaixo de um percentual do valor bruto da nota). **(B) IR, CSLL, PIS e Cofins retidos por órgão público federal** (IN 1.234, art. 2º, § 7º, I): o serviço "prestado com emprego de materiais" **não tem dedução**; ele **muda a linha de percentual**, de 9,45% (código 6190) para 5,85% (código 6147), **sobre o valor todo do pagamento**.
- **O dicionário não guarda nenhuma das duas informações.** Não há onde o contrato diga que a contratada fornece material (nem a planilha de materiais com valores), onde a nota discrimine o material, nem onde a base do INSS apareça com a conta feita: `Mov_Reinf_Servico_Previdenciario_Tipo.Valor_Base_Retencao` é só o `vlrBaseRet` do evento, sem a origem.
- **A prova decide tudo.** O material só sai da base se (i) o **contrato** prevê o fornecimento (com valores ou sem eles), (ii) a **nota** o discrimina e (iii) a contratada **comprova** o custo, e o valor excluído **não passa do custo de aquisição ou de locação**. Material que **não consta do contrato** entra na base **inteiro**, mesmo discriminado na nota (art. 119).
- **A SC 220 só trata do caso de copeiragem** (gênero alimentício) e manda observar o art. 116. Eu a li como **autorização para tratar o gênero alimentício como material** do art. 116; se o contrato não trouxer valores, o art. 117 e o piso de 50% (hipótese "demais casos") entram (leitura minha, C296).
- **Proposta:** **4 entidades novas** (70 campos, 11 deles de referência): `Cad_Gestao_Contrato_Material` (o que o contrato prevê, com vigência, no módulo de Gestão de Contratos), `Mov_Nota_Material_Discriminado` (o que a nota discrimina e o que foi excluído), `Mov_Retencao_Inss_Base_Apuracao` (a conta da base, com o piso) e `Cad_Inss_Base_Piso_Percentual` (os 10 pisos, parâmetro com vigência); **3 campos novos** em duas entidades existentes (2 em `Cad_Gestao_Contrato`, 1 em `Mov_Titulo_Retencao`); a descrição de `Valor_Base_Retencao` ganha a origem; 15 regras e 13 avisos do Motor. Nenhum domínio novo.
- **O texto oficial da IN 2.110 foi conferido (Q210-13) e mudou quatro coisas.** Os valores e os pisos dos arts. 116 a 118 **conferem** com o que eu tinha lido pela SC 170. As diferenças: **(i)** a IN **vigora desde 01/11/2022** (art. 277), e não desde 17/10; **(ii)** o art. 118, II vale **"independentemente da previsão contratual"** do equipamento inerente, então a linha de equipamento inerente sem linha no contrato **não** cai no art. 119; **(iii)** o art. 119 tem uma **exceção para o transporte de passageiros** (base mínima de 30%); **(iv)** o **art. 120** (dedução de alimentação e vale-transporte), que eu tinha deixado de fora, foi lido e entra na proposta (regra R13, 5 campos na apuração, Q210-12).
- **Os PDFs da IN 1.234 (DOU de 2012 e multivigente de 2019) foram lidos e confirmam o desenho (D-N560, item 12 da seção 4):** o § 7º, I não traz a palavra "essenciais" (a essencialidade é da SC Cosit 220); entraram as regras R14 e R15 (§§ 10 e 11); o Anexo I oficial confirma 5,85% e 9,45%. Totais: **4 entidades, 70 campos, 3 campos novos, 15 regras e 13 avisos**.
- **O ERP calcula o que a norma fecha, propõe e avisa; não bloqueia** (D-N284). O usuário confirma a classificação do material e o piso; tudo fica provisório até o contador (C296 a C302).
- **Contador:** 7 perguntas novas, C296 a C302 (documento 188, Parte 18).

# 2. O que li

| Fonte | O que li | O que tirei |
|---|---|---|
| SC Cosit 220/2026 (DOU de 11/11/2026) | O texto inteiro (3 páginas) | Quatro ementas: **INSS** (dedução dos gêneros alimentícios da copeiragem, "observado o art. 116 da IN 2.110"; dispositivos: Lei 8.212, art. 31; Decreto 3.048, art. 219, *caput* e § 7º; IN 2.110, arts. 116, 117 e 118) e **IRPJ, CSLL, PIS e Cofins** (a copeiragem com gêneros pode ser "serviço prestado com emprego de materiais" se os materiais, **essenciais** ao serviço, estão discriminados no contrato ou em planilhas anexas **e** na nota ou fatura; IN 1.234, art. 2º, § 7º, I). As quatro ementas de IRPJ, CSLL, PIS e Cofins tratam de pagamentos feitos por **órgãos públicos federais** |
| IN RFB 2.110/2022 (DOU de 19/10/2022, edição 199, p. 46; 190 páginas) | O texto oficial que você enviou: arts. 110, 114 a 125, 130, 276 e 277 (os demais artigos não li) | Art. 110: retenção de 11% do valor bruto. Art. 114 e 115: serviços sem retenção e dispensa da retenção. Art. 116: material ou equipamento (menos o manual) discriminado **no contrato e na nota**, comprovado, **sai da base**, sem passar do custo de aquisição ou locação; § 3º: a planilha só vale se **integra o contrato por cláusula expressa**. Art. 117: previsto no contrato **sem valor**, discriminado na nota: sai da base, mas a base **não pode ficar abaixo de** 30% (transporte de passageiros), 65% (limpeza hospitalar), 80% (outras limpezas) ou 50% (demais casos); o parágrafo único manda aplicar os §§ 1º e 2º do art. 116. Art. 118: equipamento **inerente** ao serviço, **com discriminação na nota**: com valores no contrato, art. 116; **sem valores no contrato, independentemente da previsão contratual**, pisos de 50% (serviços em geral) e de 10%, 15%, 45%, 50% e 35% (construção civil); § 1º: nota com mais de um serviço usa o percentual de cada um conforme o contrato, ou o maior se o contrato não permite identificar. Art. 119: **sem previsão no contrato** (e equipamento não inerente), base = valor bruto, **exceto transporte de passageiros** (mínimo de 30%); parágrafo único: sem discriminação na nota, base = valor bruto. **Art. 120**: deduzem-se da base, **se discriminados na nota**, o custo da alimentação *in natura* e do auxílio-alimentação (desde que não pago em dinheiro) e o vale-transporte (mesmo em dinheiro, limitado ao necessário ao transporte coletivo); a taxa de administração ou de agenciamento **não** se deduz (§ 1º). Art. 121: destaque "RETENÇÃO PARA A PREVIDÊNCIA SOCIAL" na nota. Art. 122: dedução da retenção feita sobre a subcontratada (mesma competência e mesmo serviço; o dicionário já tem `Valor_Retencao_Subcontratada` no evento do Reinf). Art. 123: recolhimento até o dia 20 do mês seguinte ao da emissão da nota. Art. 276, I: **revoga a IN 971/2009**. Art. 277: **vigora em 1º de novembro de 2022** |
| SC Cosit 170/2026, itens 12 a 19 | A aplicação dos pisos | O piso do art. 117, IV é **global do documento**, não por material (item 18.3); o 35% **não** autoriza presumir que os 65% restantes são material (itens 13 e 19.1); quando o art. 118 e o art. 117 incidem em parcelas diferentes da mesma nota, a base é o **maior** entre (i) o piso da parcela mais as parcelas que entram inteiras e (ii) 50% do bruto (itens 17.2 e 18.2) |
| IN RFB 1.234/2012, art. 2º | O artigo inteiro na versão do site (os incisos I a VI do *caput* foram revogados pela IN 2.145/2023) | § 7º, I: "serviços prestados com emprego de materiais" exige materiais **discriminados no contrato ou em planilhas integrantes** e **na nota ou fatura**; § 7º, II (empreitada de construção civil com materiais) e § 8º (exclui serviços hospitalares e médicos do inciso I); § 9º (instrumentos de trabalho e materiais consumidos na obra não são material incorporado); § 10 (glosa sem nova nota: a retenção incide sobre o valor original) e § 11 (juros e multa por atraso entram na base). **Conferido nos dois PDFs oficiais: o texto do § 7º, I é o mesmo nos dois e não traz a palavra "essenciais"** |
| IN 1.234, Anexo I e arts. 3º, 26 e 27 | **Li o Anexo I na versão oficial do DOU de 12/01/2012 (página 26) e, antes, na versão adaptada do guia da Prefeitura de São Paulo** (29/06/2023; mostra só o IR). Na linha **6147** (1,20% de IR) estão "Serviços prestados com emprego de materiais" e "Construção civil por empreitada com emprego de materiais"; na **6190** (4,80% de IR), "Demais serviços", limpeza, vigilância e locação de mão de obra. O guia repete o conceito do § 7º, I (materiais discriminados no contrato ou em planilha integrante **e** na nota; fora os serviços hospitalares e médicos) e diz que o fato gerador é o **pagamento** e que a retenção vale para pagamentos antecipados. O Anexo I oficial **confirma** as colunas: **6147** = IR 1,2 + CSLL 1,0 + Cofins 3,0 + PIS 0,65 = **5,85%**; **6190** = IR 4,8 + 1,0 + 3,0 + 0,65 = **9,45%**. A linha 6147 traz também "Alimentação" e "Energia elétrica"; a 6190 traz "Limpeza", "Vigilância", "Locação de mão de obra" e "Demais serviços". O art. 38, I diz que a IN alcança só a retenção do art. 64 da Lei 9.430 e do art. 34 da Lei 10.833 | O enquadramento escolhe a **linha** do Anexo I; o dicionário já guarda a linha em `Cad_Retencao_Federal_Parametro` e o vínculo em `Mov_Titulo_Retencao.ID_Retencao_Federal_Parametro` |
| SC Disit/SRRF04 4042/2026 e outros atos de 11/11/2026 | A 4042 (3 páginas) e a retificação da SC Cosit 174; os ADE ALF/MNS 66, DRF/CGE 2, ALF/BSB 52 e Cofis 18 só tive de olhar | A **4042** diz que serviços profissionais de medicina estão sujeitos à retenção de IRPJ, CSLL, PIS e Cofins entre pessoas jurídicas, e que **só** os prestados por ambulatório, banco de sangue, casa de saúde, casa de recuperação ou repouso, hospital e pronto-socorro ficam fora; **home care não está fora**. Trata da retenção entre empresas (Lei 10.833, art. 30), **não** do § 8º da IN 1.234; **não muda este desenho**, mas vale para a natureza dos serviços em `Cad_Retencao_Federal_Parametro`. Os demais atos (OEA, despachante, origem preferencial, selos de cigarro e a retificação de data da SC 174) **não têm relação** com este desenho |
| Páginas de comentário (5) | Tributo Devido (limpeza e copa; emprego de materiais), Foco Tributário (apuração e dedução; 5,85%) e Migalhas (SC 170 e 171/2026) | Os três requisitos do 5,85% são **cumulativos**; a prova vale **a cada pagamento**; os pisos antigos da IN 971, art. 122, são os mesmos de agora (30, 65, 80 e 50); a alimentação e o transporte tinham dedução à parte (IN 971, art. 124), que **continua na IN 2.110, art. 120** (conferido no texto oficial) |
| Dicionário, revisão 41 | `Cad_Retencao_Federal_Parametro`, `Mov_Titulo_Retencao`, `Mov_Reinf_Servico_Previdenciario` e `_Tipo`, `Cad_Gestao_Contrato` e `_Item`, `Mov_Nota_Fiscal_Entrada` e `_Saida`, `Mov_Apuracao_Iss_Df` | Ver a seção 3 |

# 3. O que o dicionário já tem

| Peça | Entidade | Uso neste desenho |
|---|---|---|
| Linha de percentual da retenção federal | `Cad_Retencao_Federal_Parametro` (com vigência; `Percentual_Ir`, `_Csll`, `_Cofins`, `_Pis`, `Percentual_Total`, `Natureza_Bem_Servico`) | O mecanismo B **só escolhe a linha** (6147 ou 6190); **nenhum campo novo**. Não achei carga dessa tabela nos pacotes das revisões; as linhas vêm da tabela do Mafon (p. 241 a 243) |
| Retenção por baixa | `Mov_Titulo_Retencao` (`Tipo`, `ID_Retencao_Federal_Parametro`, `Base_Calculo`, `Aliquota_Aplicada`, `Considerada_Antecipacao`) | Guarda a linha escolhida; **ganha 1 campo** com o resultado da verificação dos requisitos do § 7º, I |
| Serviço com retenção de INSS | `Mov_Reinf_Servico_Previdenciario` (por nota, sentidos tomado e prestado) e `Mov_Reinf_Servico_Previdenciario_Tipo` (`Valor_Base_Retencao` = `vlrBaseRet`, `Valor_Retencao`) | A base já existe como **resultado**; falta a **conta**. O R-2010 e o R-2020 só pedem a base, não o material |
| Contrato | `Cad_Gestao_Contrato` (módulo 12, sem vigência) e `Cad_Gestao_Contrato_Item` (com vigência; produto ou serviço com valor) | O item é o **serviço**; **não há** onde dizer que a contratada fornece material, nem a planilha de materiais |
| Nota | `Mov_Nota_Fiscal_Entrada` e `Mov_Nota_Fiscal_Saida` (`ID_Contrato`, `Valor_Total`; itens com 118 e 133 campos) | O item da nota é produto ou serviço fiscal; **não diz** que uma linha é material discriminado para fins de retenção. O `Mov_Reinf_Servico_Previdenciario` já aponta para a nota (entrada no sentido tomado, saída no prestado) |
| Material do ISS | `Mov_Apuracao_Iss_Df` e `Mov_Nota_Iss_Df_Complemento` (`Valor_Material_Terceiros`, `Valor_Material_Proprio`) | **É outra coisa**: é a dedução da base do **ISS** na DF. Não muda e não serve ao INSS |
| Prova e aprovação | `Cad_Usuario`, `Mov_Aprovacao_Instancia`, `Mov_Documento_Fiscal` | O usuário que confirma, a validação do contador e a nota de compra do material |
| Documentação de parâmetros | `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao` (documento 201) | Cada parâmetro nasce documentado: a tabela dos pisos entra com a sua linha (seção 5.6) |

# 4. Achados e leituras minhas

- **(1)** **A seção 1.35 e a D-N549 estavam imprecisas.** Elas diziam "dedução de material na base das retenções (INSS e IN 1.234)". Na **IN 1.234 não há dedução**: o texto do § 7º, I **qualifica o serviço** e a qualificação **troca a linha** do Anexo I; o percentual (5,85%) incide sobre o **pagamento inteiro**. Só o **INSS** tem base reduzida. Por isso o desenho tem **uma tabela de apuração da base** (INSS) e **um campo de enquadramento** (IN 1.234), e não uma coluna "material dedutível" comum às duas.
- **(2)** **O gênero alimentício é material.** A SC 220 manda deduzir da base do INSS os gêneros fornecidos "observado o art. 116", e nas outras quatro ementas os trata como "materiais" do § 7º, I. O dicionário ganha o valor `genero_alimenticio` em `Tipo_Material` **só para rastrear e relatar**; o tratamento é o do material (Q210-8).
- **(3)** **O contrato é o ponto de partida.** Os arts. 116 a 119 e o § 7º, I perguntam primeiro **o que o contrato prevê**. Sem contrato, o material não sai da base (art. 119). Por isso o contrato recebe a **lista** do que a contratada fornece (`Cad_Gestao_Contrato_Material`, com vigência, porque o aditivo muda a lista) e dois marcadores no cabeçalho.
- **(4)** **"Planilha anexa" só vale se integra o contrato.** O art. 116, § 3º, considera discriminado no contrato o valor que está em planilha à parte **se o contrato diz, em cláusula expressa, que ela o integra**. A SC 220 diz "planilhas anexas" e a IN 1.234 diz "planilhas integrantes". O campo `Planilha_Material_Integra_Contrato` guarda a cláusula e o aviso 6 acusa a linha de planilha sem ela.
- **(5)** **Equipamento manual não entra** nos arts. 116 e 117 ("exceto equipamentos manuais"). Equipamento **inerente** ao serviço tem o art. 118, com piso. Por isso as linhas têm `Eh_Equipamento_Manual` e `Eh_Inerente_Ao_Servico`.
- **(6)** **O piso é do documento, não do material.** A SC 170 diz que o piso de 50% do art. 117, IV é global da nota (item 18.3). A tabela de apuração por nota tem um piso e uma base final, e não um piso por linha de material.
- **(7)** **A combinação do art. 118 com o art. 117 na mesma nota** (itens 17.2 e 18.2 da SC 170) pede "o maior entre dois valores". Implementei a regra R7, mas **li esses itens pelo resumo do site de terceiros**, e a fórmula vai ao contador (C297).
- **(8)** **Nota com mais de um serviço** (art. 118, § 1º): usa o percentual de cada serviço pelo contrato, ou o **maior** se o contrato não identifica o valor de cada um. A apuração guarda o piso aplicado e o aviso 8 diz quando foi o maior.
- **(9)** **O lado prestado é só conferência.** No R-2020 (a empresa **presta** o serviço), quem calcula a base é o **tomador**. O ERP calcula a base esperada com a nota emitida e **guarda a base que o tomador informou** (`Base_Informada_Pelo_Tomador`); o aviso 9 mostra a divergência. Não recalcula a retenção do tomador.
- **(10)** **O que a contratada discrimina na nota decide o benefício.** Sem a discriminação, a base é o valor bruto (art. 119, parágrafo único) e o serviço não é "com emprego de materiais" (a linha 6190 vale). O aviso 11 diz isso antes da emissão, quando a empresa é a prestadora.
- **(11)** **A dedução de alimentação e de transporte está no art. 120 da IN 2.110** (a IN 971, art. 124, foi revogada). Ela vale **se a nota discrimina** a parcela; a alimentação não pode ser paga em dinheiro; o vale-transporte pode, mas até o necessário ao transporte coletivo; a taxa de administração não deduz. O texto **não diz** em que ordem ela se combina com o piso dos arts. 117 e 118. Entra na proposta como a regra R13, **provisória** (a dedução incide sobre a base final dos arts. 116 a 119, leitura minha, C299), com 5 campos na apuração (Q210-12).
- **(12)** **Os dois PDFs da IN 1.234 foram lidos (D-N560)** e confirmam o desenho, com três mudanças. **(i)** O § 7º, I **não usa a palavra "essenciais"**: exige o fornecimento de materiais pelo contratado, discriminados no contrato ou em planilha integrante **e** na nota ou fatura. A essencialidade vem da **SC Cosit 220/2026**; mantive o campo `Eh_Essencial_Ao_Servico` e o valor `nao_atende_essencialidade`, agora com a fonte certa, e a C300 pergunta se vale além da copeiragem. **(ii)** Os **§§ 10 e 11** (glosa e juros/multa) entraram como regras R14 e R15, sem campo novo. **(iii)** O **Anexo I oficial** confirma 5,85% (6147) e 9,45% (6190) com as quatro colunas; a linha 6147 traz "Alimentação" como natureza própria (o fornecimento de refeição), diferente da copeiragem com material dentro de um serviço de limpeza ou apoio. O art. 38 confirma que a IN só trata da retenção dos órgãos públicos federais (Lei 9.430, art. 64, e Lei 10.833, art. 34).
- **(12)** **O texto da IN 2.110 agora é o oficial** (DOU de 19/10/2022), mas é o **texto original**: alterações posteriores não estão nele (a IN 2.185/2024 não altera os arts. 112 a 125, pelo que li num site de terceiros; as demais não verifiquei, C302). A IN 1.234 continua lida pelo site Normas Legais e pelo guia da Prefeitura de São Paulo, não pelo texto da Receita.
- **(13)** **A IN 2.110 vigora desde 01/11/2022** (art. 277) e revogou a IN 971/2009 (art. 276, I). Contratos e notas anteriores a essa data seguem a IN 971 (C302).

# 5. Proposta

## 5.1 Como as peças se encaixam

O ERP **só registra, calcula o que a norma fecha e avisa; não bloqueia** (D-N284). A ordem é:

- **(1)** **O contrato prevê material?** O contrato tem `Preve_Fornecimento_Material` e, se tiver a lista, as linhas de `Cad_Gestao_Contrato_Material` (com valor ou sem valor, na cláusula ou na planilha).
- **(2)** **A nota discrimina?** O usuário (ou o Motor, por proposta) marca as linhas da nota que são material, equipamento ou gênero alimentício e registra `Mov_Nota_Material_Discriminado`: valor discriminado, valor comprovado, nota de compra e a linha do contrato.
- **(3)** **O Motor decide o valor excluído de cada linha** (regras R1 a R6) e o **regime** (art. 116, 117, 118 ou 119).
- **(4)** **O Motor monta a base do INSS** em `Mov_Retencao_Inss_Base_Apuracao` (R7 a R9 e R13): base pelos valores, piso (se houver), dedução do art. 120 e base final; o `Mov_Reinf_Servico_Previdenciario_Tipo.Valor_Base_Retencao` é o rateio da base final entre os tipos de serviço.
- **(5)** **Na retenção federal do órgão público** (IN 1.234), o Motor verifica os três requisitos do § 7º, I e grava o resultado em `Mov_Titulo_Retencao.Enquadramento_Emprego_Materiais`; a **linha** escolhida (6147 ou 6190) fica em `ID_Retencao_Federal_Parametro` (R10 a R12).
- **(6)** **Avisos** (seção 6) dizem o que falta ou diverge.

## 5.2 As entidades novas

### `Cad_Gestao_Contrato_Material` (Gestão de Contratos, com vigência, 19 campos)

O que o contrato diz que a contratada fornece junto com o serviço: material, equipamento ou gênero alimentício, com ou sem valor, na cláusula ou na planilha. Serve às duas pontas: a empresa que **presta** o serviço (e precisa discriminar na nota para reduzir a base) e a que **toma** (e retém). Tem vigência porque o aditivo muda a lista.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Contrato_Material` | identificador | Chave. |
| `ID_Contrato_Material_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Gestao_Contrato_Material_Versao). Fase 0, seção 2. |
| `ID_Contrato` | referência (Cad_Gestao_Contrato) --- identidade | O contrato que prevê o fornecimento. |
| `Numero_Linha` | número --- identidade | A linha na cláusula ou na planilha do contrato. |
| `Tipo_Material` | enumeração {material, equipamento, genero_alimenticio} | O que a contratada fornece. O gênero alimentício tem o tratamento do material (SC Cosit 220/2026); o valor separado serve para rastrear e relatar. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico), opcional | O cadastro do bem fornecido, quando houver. |
| `Descricao` | texto | O que o contrato diz que é fornecido. |
| `Forma_Previsao` | enumeração {com_valor, sem_valor} | `com_valor`: o contrato ou a planilha traz o valor (art. 116). `sem_valor`: o contrato só prevê o fornecimento (art. 117). |
| `Origem_Previsao` | enumeração {clausula, planilha} | Onde a previsão está. A planilha só vale se `Cad_Gestao_Contrato.Planilha_Material_Integra_Contrato` for verdadeiro (art. 116, § 3º). |
| `Valor_Previsto` | número, opcional | O valor do contrato ou da planilha. Obrigatório quando `Forma_Previsao` é `com_valor`. |
| `Base_Valor_Previsto` | enumeração {por_mes, por_unidade, total_do_contrato}, opcional | A que o valor se refere. Preenchido junto com `Valor_Previsto`. |
| `Eh_Essencial_Ao_Servico` | booleano | O material é essencial à prestação do serviço (SC Cosit 220/2026; **a palavra "essenciais" não está no texto do § 7º, I da IN 1.234**). O usuário marca; o ERP não decide. Padrão falso. |
| `Eh_Equipamento_Manual` | booleano | Equipamento manual não sai da base nos arts. 116 e 117. Só se aplica a `Tipo_Material` = `equipamento`. Padrão falso. |
| `Eh_Inerente_Ao_Servico` | booleano | O uso do equipamento é inerente à execução do serviço (art. 118). Padrão falso. |
| `ID_Aditivo_Origem` | referência (Cad_Gestao_Contrato_Aditivo), opcional | O aditivo que criou ou mudou a linha. |
| `Observacao` | texto, opcional | A cláusula, a página da planilha ou o que for útil. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

Regras de conferência: a unicidade é por `ID_Contrato` e `Numero_Linha` na vigência; `Valor_Previsto` é obrigatório quando `Forma_Previsao` é `com_valor`; `Eh_Equipamento_Manual` e `Eh_Inerente_Ao_Servico` só valem para `Tipo_Material` = `equipamento`.

### `Mov_Nota_Material_Discriminado` (Contabilidade & Fiscal, movimento, 18 campos)

Uma linha por material, equipamento ou gênero alimentício que a **nota** discrimina, com a prova e o valor que o Motor excluiu da base. O que a nota não discrimina não tem linha (e entra na base, art. 119, parágrafo único).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Nota_Material` | identificador | Chave. |
| `ID_Nota_Fiscal_Entrada` | referência (Mov_Nota_Fiscal_Entrada), opcional | Obrigatório e exclusivo no sentido tomado (a mesma regra de `Mov_Reinf_Servico_Previdenciario`). |
| `ID_Nota_Fiscal_Saida` | referência (Mov_Nota_Fiscal_Saida), opcional | Obrigatório e exclusivo no sentido prestado. |
| `Numero_Linha` | número | A ordem da discriminação na nota. |
| `Tipo_Material` | enumeração {material, equipamento, genero_alimenticio} | O mesmo domínio do contrato. |
| `Descricao` | texto | Como a nota descreve o material. |
| `ID_Contrato_Material` | referência (Cad_Gestao_Contrato_Material), opcional | A linha do contrato que prevê o material. **Vazio quando o contrato não o prevê**: o valor entra na base (art. 119). |
| `Eh_Equipamento_Manual` | booleano | Cópia da linha do contrato, ou marcação do usuário quando não há linha. Padrão falso. |
| `Eh_Inerente_Ao_Servico` | booleano | Idem, para o art. 118. Padrão falso. |
| `Valor_Discriminado` | número | O valor que a nota traz para o material. |
| `Valor_Comprovado` | número, opcional | O custo de aquisição ou de locação comprovado. O valor excluído nunca passa dele (art. 116, § 1º). |
| `ID_Documento_Comprobatorio` | referência (Mov_Documento_Fiscal), opcional | A nota de compra do material, quando houver. |
| `Referencia_Comprovante` | texto, opcional | O contrato de locação, o recibo ou outra prova que não é documento fiscal. |
| `Regime_Aplicado` | enumeração {art_116, art_117, art_118_i, art_118_ii, art_119}, opcional | O dispositivo que o Motor aplicou à linha. Vazio enquanto não calculado. |
| `Valor_Excluido_Da_Base` | número | O valor que sai da base: o menor entre `Valor_Discriminado` e `Valor_Comprovado`, quando a linha pode sair; zero nos demais casos. Calculado e armazenado. |
| `Situacao_Exclusao` | enumeração {excluido, limitado_ao_comprovado, sem_previsao_no_contrato, sem_comprovacao, equipamento_manual} | Por que o valor saiu, saiu em parte ou não saiu. |
| `Origem_Decisao` | enumeração {calculado_pelo_sistema, informado_pelo_usuario} | Quem decidiu o valor excluído. |
| `Observacao` | texto, opcional | Qualquer nota do usuário. |

Regra de conferência: exatamente um entre `ID_Nota_Fiscal_Entrada` e `ID_Nota_Fiscal_Saida` é preenchido.

### `Mov_Retencao_Inss_Base_Apuracao` (Contabilidade & Fiscal, movimento, 19 campos)

A conta da base do INSS de uma nota: o valor bruto, o que saiu pelos valores, o piso, a dedução do art. 120 (alimentação e vale-transporte) e a base final. Uma linha por serviço com retenção (`Mov_Reinf_Servico_Previdenciario`), 1:1. Deixa de existir a base "sem origem".

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Base_Apuracao` | identificador | Chave. |
| `ID_Servico_Previdenciario` | referência (Mov_Reinf_Servico_Previdenciario) | O serviço com retenção (R-2010 ou R-2020). 1:1. |
| `Valor_Bruto_Documento` | número | O valor bruto da nota na data do cálculo (cópia, para a conta ficar reproduzível). |
| `Valor_Excluido_Total` | número | A soma de `Valor_Excluido_Da_Base` das linhas da nota. |
| `Valor_Base_Pelos_Valores` | número | `Valor_Bruto_Documento` menos `Valor_Excluido_Total`. |
| `ID_Piso_Aplicado` | referência (Cad_Inss_Base_Piso_Percentual), opcional | O piso que vale para a nota (o maior, quando a nota tem mais de um serviço sem valores individualizados, art. 118, § 1º). Vazio quando só o art. 116 se aplica. |
| `Percentual_Piso` | número, opcional | Cópia do percentual do piso na data do cálculo. |
| `Valor_Base_Pelo_Piso` | número, opcional | Pelo piso, conforme a regra R7. |
| `Piso_Prevaleceu` | booleano | Verdadeiro quando a base pelo piso é maior que a base pelos valores. |
| `Alimentacao_Paga_Em_Dinheiro` | booleano | Verdadeiro quando a alimentação ou o auxílio-alimentação foi pago em dinheiro: **não deduz** (art. 120, I). Padrão falso. |
| `Valor_Alimentacao_Discriminada` | número, opcional | O custo da alimentação *in natura* ou do auxílio-alimentação que a nota discrimina (art. 120, I). |
| `Valor_Vale_Transporte_Discriminado` | número, opcional | O vale-transporte que a nota discrimina, mesmo pago em dinheiro (art. 120, II). |
| `Valor_Vale_Transporte_Limite` | número, opcional | O valor necessário ao custeio do deslocamento em transporte coletivo; o vale-transporte deduzido não passa dele (art. 120, II). |
| `Valor_Deducao_Art120` | número | A dedução que o Motor aplicou (regra R13): a alimentação (se não paga em dinheiro) mais o menor entre o vale-transporte discriminado e o limite. Zero sem discriminação na nota. Calculado e armazenado. |
| `Valor_Base_Final` | número | O maior entre os dois quando há piso, senão a base pelos valores; **menos** `Valor_Deducao_Art120`, com mínimo zero. A soma de `Valor_Base_Retencao` dos tipos de serviço da nota é igual a este valor. |
| `Base_Informada_Pelo_Tomador` | número, opcional | **Só no sentido prestado**: a base com que o tomador reteve. Serve à conferência (aviso 9). |
| `Origem_Decisao` | enumeração {calculado_pelo_sistema, informado_pelo_usuario} | Quem decidiu a base final. |
| `ID_Usuario_Confirmacao` | referência (Cad_Usuario), opcional | Quem confirmou a apuração. |
| `Observacao` | texto, opcional | Qualquer nota do usuário. |

### `Cad_Inss_Base_Piso_Percentual` (Contabilidade & Fiscal, com vigência, 14 campos)

Os pisos dos arts. 117 e 118 da IN 2.110. Parâmetro legal com vigência; cada linha é uma hipótese. A carga (10 linhas, provisórias) está no Anexo B.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Inss_Base_Piso_Percentual` | identificador | Chave. |
| `ID_Inss_Base_Piso_Percentual_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Inss_Base_Piso_Percentual_Versao). Fase 0, seção 2. |
| `Codigo_Hipotese` | código (até 30) --- identidade | A hipótese, por exemplo ART117_III. |
| `Dispositivo` | texto | O artigo, inciso e alínea da IN 2.110. |
| `Descricao_Hipotese` | texto | A hipótese em palavras, por exemplo "outros serviços de limpeza". |
| `Artigo_Origem` | enumeração {art_117, art_118} | Decide em que regime a linha entra. |
| `Percentual_Minimo` | número | O percentual do valor bruto da nota abaixo do qual a base não pode ficar. |
| `Exige_Equipamento_Inerente` | booleano | Verdadeiro nas linhas do art. 118. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até a conferência com o texto da Receita e a validação do contador. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Fundamento_Legal` | texto | A norma e a linha de onde veio. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

Regra de conferência: a unicidade é por `Codigo_Hipotese` na vigência.

## 5.3 Campos novos nas entidades que já existem

| Entidade | Campo | Tipo | Para quê |
|---|---|---|---|
| `Cad_Gestao_Contrato` | `Preve_Fornecimento_Material` | booleano | O contrato prevê que a contratada fornece material, equipamento ou gênero alimentício (IN 2.110, arts. 116 a 119; IN 1.234, art. 2º, § 7º, I). Vale mesmo sem a lista de `Cad_Gestao_Contrato_Material` (art. 117: previsão sem valor). Padrão falso |
| `Cad_Gestao_Contrato` | `Planilha_Material_Integra_Contrato` | booleano | O contrato diz, em cláusula expressa, que a planilha de materiais o integra (IN 2.110, art. 116, § 3º). Padrão falso |
| `Mov_Titulo_Retencao` | `Enquadramento_Emprego_Materiais` | enumeração {atende, nao_atende_contrato, nao_atende_nota, nao_atende_essencialidade, servico_de_saude_excluido}, opcional | O resultado da verificação dos requisitos da IN 1.234, art. 2º, § 7º, I: (1) o contrato prevê o fornecimento, (2) os materiais estão no contrato ou na planilha integrante e são essenciais ao serviço (esse requisito é da SC Cosit 220/2026, não do texto da IN), (3) estão na nota ou fatura. `servico_de_saude_excluido` é o § 8º. Preenchido na retenção `retido_pelo_cliente` de órgão público federal |

Descrição de `Mov_Reinf_Servico_Previdenciario_Tipo.Valor_Base_Retencao` (sem campo novo): passa a dizer que o valor é o rateio, entre os tipos de serviço, de `Mov_Retencao_Inss_Base_Apuracao.Valor_Base_Final`, e que a soma dos tipos é a base final.

## 5.4 Como o Motor decide a base do INSS

1. **Sem linha de material na nota:** `Valor_Base_Final` = `Valor_Bruto_Documento` (art. 119, parágrafo único), mesmo que o contrato preveja material.
2. **Com linha de material:** cada linha recebe o regime e o valor excluído, na ordem abaixo; a **primeira** condição que vale define o regime.

| Ordem | Condição da linha | Regime | Valor excluído |
|---|---|---|---|
| 1 | `ID_Contrato_Material` vazio (o contrato não prevê o material) | `art_119` — **salvo** (a) equipamento inerente ao serviço, discriminado na nota (`Eh_Inerente_Ao_Servico` verdadeiro): `art_118_ii`, que vale **independentemente da previsão contratual** (art. 118, II), calculado como na linha 4; (b) transporte de passageiros: `art_119` com **base mínima de 30%** (`ART117_I`, art. 119, parte final) | Zero no `art_119`; `sem_previsao_no_contrato` |
| 2 | `Eh_Equipamento_Manual` verdadeiro | `art_119` | Zero; `equipamento_manual` |
| 3 | Linha do contrato `com_valor`, vinda de cláusula, ou de planilha com `Planilha_Material_Integra_Contrato` verdadeiro | `art_116` (ou `art_118_i` se for equipamento inerente) | O menor entre `Valor_Discriminado` e `Valor_Comprovado`; zero e `sem_comprovacao` se não houver prova; `limitado_ao_comprovado` se o comprovado for menor |
| 4 | Linha do contrato `sem_valor`, ou `com_valor` vinda de planilha sem a cláusula | `art_117` (ou `art_118_ii` se for equipamento inerente) | Igual ao da linha 3, **e a base final tem piso** |

3. **Piso:** o Motor propõe a linha de `Cad_Inss_Base_Piso_Percentual` pela natureza do serviço (limpeza, transporte de passageiros, construção civil ou demais) e o usuário confirma; sem natureza identificada, entra a hipótese `ART117_IV` (50%) nas linhas `art_117` e `ART118_II_A` (50%) nas linhas `art_118_ii`. Nota com mais de um serviço usa o piso de **cada serviço conforme o contrato**; se o contrato não permite identificar o valor de cada um, usa o **maior** (art. 118, § 1º).
4. **Base final:** só `art_116`: base pelos valores. Com `art_117` ou `art_118_ii`: o **maior** entre a base pelos valores e o piso sobre o valor bruto (R7 trata a nota que mistura os dois, itens 17.2 e 18.2 da SC 170). **Dedução do art. 120:** da base assim obtida o Motor subtrai `Valor_Deducao_Art120` (R13), com mínimo zero.
5. **Rateio:** o Motor reparte `Valor_Base_Final` entre os tipos de serviço da nota (`Valor_Base_Retencao`), de modo que a soma bata; a retenção é 11% (ou 3,5%, `Prestador_Contribuinte_Cprb`) da base, como hoje.

## 5.5 Como o Motor decide a linha da IN 1.234

O enquadramento vale **a cada pagamento** e só para o órgão público federal que retém IR, CSLL, PIS e Cofins (`Tipo` = `retido_pelo_cliente`). O Motor verifica os requisitos do § 7º, I (o contrato prevê e discrimina o material; a nota ou fatura o discrimina) e, pela SC Cosit 220/2026, a essencialidade do material, e grava o resultado:

| Se | Resultado | Linha escolhida |
|---|---|---|
| O serviço é hospitalar ou médico (§ 8º) | `servico_de_saude_excluido` | A do serviço, fora deste desenho |
| `Preve_Fornecimento_Material` é falso, ou não há linha de `Cad_Gestao_Contrato_Material` | `nao_atende_contrato` | 6190 (9,45%) |
| Nenhuma linha essencial (`Eh_Essencial_Ao_Servico`) está no contrato ou na planilha integrante | `nao_atende_essencialidade` | 6190 |
| A nota ou a fatura do pagamento não tem linha de `Mov_Nota_Material_Discriminado` para o material | `nao_atende_nota` | 6190 |
| Os três requisitos valem | `atende` | 6147 (5,85%) |

O percentual incide sobre o **valor todo** do pagamento. O ERP **não deduz** material do valor retido por esta via. Com **glosa** de valores da nota sem nova nota, a retenção incide sobre o valor **original** da nota (§ 10; R14); com **juros e multa** por atraso, sobre o valor da nota **incluídos os acréscimos** (§ 11; R15). O Motor **sugere** a linha; o valor retido continua explícito (`Mov_Titulo_Retencao.Valor_Retido`).

## 5.6 Parâmetro documentado e ligações com os outros blocos

- **Parâmetro documentado (documento 201).** A tabela `Cad_Inss_Base_Piso_Percentual` entra em `Cad_Parametro_Documentacao` com **uma linha** (o que é, os 10 valores, o padrão, o que acontece sem valor: a base é o valor bruto, quem altera, o fundamento) e em `Cad_Parametro_Efeito_Obrigacao` com o efeito na **EFD-Reinf, eventos R-2010 e R-2020** (`vlrBaseRet`). O mecanismo B não tem parâmetro novo: ele só escolhe uma linha de `Cad_Retencao_Federal_Parametro`, cujo efeito é o do código de receita no DARF e no R-4020.
- **Gestão de Contratos.** O aditivo muda `Cad_Gestao_Contrato_Material` pela vigência; o cálculo usa a versão vigente **na data da nota**.
- **Retenção por baixa.** `Mov_Titulo_Retencao.Base_Calculo` e `Aliquota_Aplicada` não mudam; para o INSS, `Base_Calculo` pode apontar para `Valor_Base_Final` (leitura minha).
- **Reinf.** O R-2010 e o R-2020 só pedem o valor da base; o material não vai no arquivo. A apuração fica para a conferência e a defesa (a prova do art. 116, § 2º, fica com a contratada).

# 6. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|---|---|---|
| 1 | Contrato prevê material sem lista | `Preve_Fornecimento_Material` verdadeiro e nenhuma linha vigente em `Cad_Gestao_Contrato_Material`: só vale o art. 117, com piso |
| 2 | Material na nota que o contrato não prevê | `Mov_Nota_Material_Discriminado` sem `ID_Contrato_Material`: o valor entra na base (art. 119) |
| 3 | Valor discriminado maior que o comprovado | `Valor_Discriminado` maior que `Valor_Comprovado`: o excluído fica no comprovado |
| 4 | Material sem comprovação | `Valor_Comprovado` vazio: nada sai da base (`sem_comprovacao`) |
| 5 | Equipamento manual discriminado | `Eh_Equipamento_Manual` verdadeiro: não sai da base nos arts. 116 e 117 |
| 6 | Planilha sem cláusula de integração | Linha com `Origem_Previsao` = `planilha` e `Planilha_Material_Integra_Contrato` falso: tratada como `sem_valor` (art. 117) |
| 7 | Piso maior que a base pelos valores | `Piso_Prevaleceu` verdadeiro: o material discriminado não reduz a base ao que o contrato permitiria |
| 8 | Nota com mais de um serviço sem valores individualizados | Foi usado o maior piso (art. 118, § 1º); sugere separar os serviços na nota |
| 9 | Base do tomador diferente da calculada | Sentido prestado, `Base_Informada_Pelo_Tomador` diferente de `Valor_Base_Final` |
| 10 | Enquadramento da IN 1.234 não atendido | `Enquadramento_Emprego_Materiais` diferente de `atende` e o contrato prevê material: diz qual requisito falhou |
| 11 | Prestação sem discriminar o material | A empresa presta serviço a órgão público federal, o contrato prevê material e a nota emitida não tem linha de material: perde a base reduzida do INSS e a linha 6147 |
| 12 | Gênero alimentício sem essencialidade marcada | `Tipo_Material` = `genero_alimenticio` com `Eh_Essencial_Ao_Servico` falso na linha do contrato: a SC Cosit 220/2026 pede material essencial (o texto da IN 1.234 não usa a palavra) |
| 13 | Dedução do art. 120 sem efeito | Alimentação paga em dinheiro (não deduz), vale-transporte acima do limite (o excedente não sai) ou parcela que a nota não discrimina (não existe dedução sem discriminação na nota)|

# 7. Perguntas

A Q210-1 está **respondida** ("desenhar", ao escolher o documento 210 como próximo passo, D-N555). A **Q210-14** está **respondida** ("sim, tem clientes", D-N556) e a **Q210-13**, **respondida** com o texto oficial da IN 2.110 que você enviou (D-N558). As demais seguem abertas.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q210-2 | Aceita que o desenho **separe os dois mecanismos** (INSS: material **sai da base**; IN 1.234: material **troca a linha** de percentual e não deduz), corrigindo a leitura da seção 1.35 e da D-N549? | Sim |
| Q210-3 | Aprova **`Cad_Gestao_Contrato_Material`** (19 campos, com vigência, no módulo de Gestão de Contratos) e os **2 campos novos** em `Cad_Gestao_Contrato` (5.3)? | Sim |
| Q210-4 | Aprova **`Mov_Nota_Material_Discriminado`** (18 campos)? | Sim |
| Q210-5 | Aprova **`Mov_Retencao_Inss_Base_Apuracao`** (19 campos, já com a dedução do art. 120) e a nova descrição de `Valor_Base_Retencao`? | Sim |
| Q210-6 | Aprova **`Cad_Inss_Base_Piso_Percentual`** (14 campos, com vigência) e a **carga provisória de 10 linhas** do Anexo B? | Sim, provisório |
| Q210-7 | Aprova o campo **`Enquadramento_Emprego_Materiais`** em `Mov_Titulo_Retencao` (5.3) e a regra de escolha da linha 6147 ou 6190 (5.5)? | Sim |
| Q210-8 | O **gênero alimentício** fica com valor próprio em `Tipo_Material` e **tratamento de material** (SC 220)? | Sim |
| Q210-9 | O Motor **propõe** a classificação do que é material na nota e o **piso**, e o usuário **confirma** (nada bloqueia)? | Sim |
| Q210-10 | No **sentido prestado**, o ERP calcula a base esperada e **guarda a base do tomador** só para conferência, sem recalcular a retenção dele? | Sim |
| Q210-11 | Aprova os **13 avisos** (seção 6) e as **15 regras** de texto do Anexo A? | Sim |
| Q210-12 | Entra no desenho a **dedução de alimentação e vale-transporte do art. 120** da IN 2.110 (agora lido): **5 campos** na apuração, a regra **R13** e o aviso 13, com a ordem "depois do piso" provisória até o contador (C299)? | Sim, provisório |
| Q210-13 | **Respondida.** Você enviou o texto oficial da IN 2.110/2022 e o guia com o Anexo I adaptado da IN 1.234; a conferência está nas seções 2 e 4 | Respondida |
| Q210-14 | **Respondida:** há cliente com contrato de serviço com fornecimento de material, de copeiragem ou de limpeza (D-N556). A implantação **não** espera cliente | Respondida |

# 8. O que acontece se você aprovar

- **Tudo (Q210-2 a Q210-12):** **4 entidades novas**, **70 campos nelas** e **3 campos** em entidades existentes (**73 campos** ao todo), **11 campos de referência** nas novas, nenhum domínio novo e nenhuma enumeração alterada. Sobre a revisão 41: **1.205 entidades, 13.874 campos, 3.579 campos de referência e 360 domínios**. **Ensaio feito** (sem entregar nada): a auditoria fechou com **0 achados** e o gerador de DDL deu **1.452 tabelas** (as 4 novas e as versões de `Cad_Gestao_Contrato_Material` e de `Cad_Inss_Base_Piso_Percentual`), **3.826 chaves estrangeiras, 3.917 índices e 11.648 comentários**. As **entidades mestres** passam de 245 para 247. **Três chaves opcionais novas esperam a onda de destino** (de 81 para 84): `Mov_Nota_Material_Discriminado` (onda 3) aponta para as notas de entrada e de saída (onda 4) e para `Cad_Gestao_Contrato_Material` (onda 5).
- **Carga:** 10 linhas de `Cad_Inss_Base_Piso_Percentual` (provisórias), 1 linha de documentação do parâmetro e as 15 regras e 13 avisos em texto. Não há carga de linha de material nem de apuração: são dados do contrato e da nota.
- **Ao contador:** sete perguntas novas, C296 a C302 (documento 188, Parte 18).
- **Se a Q210-2 vier "não":** o desenho volta a ter uma só coluna "material dedutível", que **não reproduz a IN 1.234**.
- **Q210-14 respondida ("sim, há clientes"):** a implantação não espera cliente.
- **Se a Q210-12 vier "não":** a dedução do art. 120 fica fora; os 5 campos e a regra R13 saem, e a apuração volta a 14 campos.
- **Nada é aplicado antes de "consolidar".**

# 9. Limites

- **Não li:** os arts. 111 a 113 e 126 a 129, 131 em diante da IN 2.110 (quem está sujeito, atividades, construção civil, obrigações acessórias), só os que o desenho usa; as alterações da IN 1.234 **depois de 18/03/2019** (a versão multivigente que li é dessa data; a IN 2.145/2023 e a IN 2.257/2025 só li pelo site); o **art. 31 da Lei 8.212** e o **art. 219 do Decreto 3.048** por inteiro; as SC Cosit 170 e 171/2026 por inteiro (li o que o PDF trouxe).
- **A IN RFB 2.185/2024** (de 05/04/2024, DOU de 09/04/2024), que você indicou pelo link da Receita, atualiza a IN 2.110 mas, pelo texto que li num site de terceiros, **não altera os arts. 112 a 125** (retenção, base, materiais, pisos); a notícia também não os menciona. Outras alterações posteriores a abril de 2024 **não verifiquei**. A página da Receita pedia autenticação e não abriu; li a notícia pela Agência Gov.
- **A tabela dos pisos** (Anexo B) **confere** com o texto oficial (arts. 117 e 118), que é o **original de 19/10/2022**. Se a IN 2.110 teve alteração depois, o dado muda; por isso a carga sai `provisorio` até o contador responder a C302. A vigência inicial (01/11/2022) vem do art. 277.
- **Os itens 17.2 e 18.2 da SC 170** (maior entre dois valores) **não estão no texto da IN**; estão na regra R7 como li na solução de consulta, e o contador confirma (C297).
- **A ordem entre o piso e a dedução do art. 120** não está na IN 2.110; a regra R13 é leitura minha (C299).
- **A SC 220 só trata de copeiragem.** A extensão do gênero alimentício a outras atividades, e do tratamento de material a outras mercadorias, é leitura minha.
- **A essencialidade** (SC Cosit 220/2026; não consta do texto da IN 1.234) é marcação do usuário; o ERP não a avalia.
- **A prova** (nota de compra, locação) é guardada, não avaliada. O limite de "custo de aquisição" é conta simples.
- **O ISS** (dedução de material na base da DF) e o **PIS e a Cofins** do próprio contrato (crédito, regime) **não mudam** neste desenho.
- **Nada foi conferido com a Receita**; as leituras são dos textos das normas e das soluções de consulta.

# Anexo A. As 15 regras provisórias do Motor

| Regra | Se | Resultado | Fundamento |
|---|---|---|---|
| R1 | Linha da nota sem `ID_Contrato_Material` | Regime `art_119`; excluído zero; `sem_previsao_no_contrato`. **Exceções:** equipamento inerente ao serviço, discriminado na nota: regime `art_118_ii` (vale sem previsão contratual); transporte de passageiros: base mínima de 30% | IN 2.110, art. 119 e art. 118, II |
| R2 | `Eh_Equipamento_Manual` verdadeiro | Excluído zero; `equipamento_manual` | IN 2.110, arts. 116 e 117 (exceto equipamentos manuais) |
| R3 | Linha do contrato `com_valor` (cláusula ou planilha integrante) | Regime `art_116` (ou `art_118_i`); excluído = menor entre discriminado e comprovado | IN 2.110, art. 116, §§ 1º a 3º; art. 118, I |
| R4 | Linha do contrato `sem_valor` (ou planilha sem a cláusula) | Regime `art_117` (ou `art_118_ii`); excluído = menor entre discriminado e comprovado; a base final tem piso | IN 2.110, art. 117; art. 118, II |
| R5 | Sem comprovação (`Valor_Comprovado` vazio) | Excluído zero; `sem_comprovacao` | IN 2.110, art. 116, § 2º |
| R6 | Gênero alimentício da copeiragem | Tratado como material do art. 116 (ou do art. 117, sem valor) | SC Cosit 220/2026 |
| R7 | Linhas `art_117` ou `art_118_ii`; base final | Base final = maior entre a base pelos valores e o piso sobre o bruto; nota com parcelas dos dois artigos: maior entre (piso da parcela mais as parcelas inteiras) e 50% do bruto | IN 2.110, arts. 117 e 118; SC Cosit 170/2026, itens 17.2 e 18.2 (leitura minha) |
| R8 | Nota sem linha de material | Base final = valor bruto | IN 2.110, art. 119, parágrafo único |
| R9 | Nota com mais de um serviço sem valores individualizados | Piso = o maior percentual dos serviços | IN 2.110, art. 118, § 1º |
| R10 | `Tipo` = `retido_pelo_cliente`, órgão público federal; os três requisitos do § 7º, I valem | `atende`; linha 6147 | IN 1.234, art. 2º, § 7º, I |
| R11 | Falta um dos três requisitos | `nao_atende_contrato`, `nao_atende_essencialidade` ou `nao_atende_nota`; linha 6190 | IN 1.234, art. 2º, § 7º, I (contrato e nota); essencialidade: SC Cosit 220/2026 |
| R12 | Serviço hospitalar ou médico | `servico_de_saude_excluido`; fora deste desenho | IN 1.234, art. 2º, § 8º |
| R13 | Nota com parcela de alimentação ou de vale-transporte **discriminada** | `Valor_Deducao_Art120` = alimentação (zero se `Alimentacao_Paga_Em_Dinheiro`) mais o menor entre o vale-transporte e o limite; `Valor_Base_Final` = base de R7 ou R8 menos a dedução, mínimo zero; taxa de administração nunca deduz | IN 2.110, art. 120 e § 1º; a ordem depois do piso é leitura minha (C299) |
| R14 | Retenção federal de órgão público (`retido_pelo_cliente`) com glosa de valores da nota, sem nova nota | Base da retenção = valor **original** da nota; a glosa não reduz a retenção | IN 1.234, art. 2º, § 10 (regra do Motor, sem campo novo) |
| R15 | Retenção federal de órgão público com juros e multa por atraso | Base da retenção = valor da nota **incluídos** os acréscimos | IN 1.234, art. 2º, § 11 (regra do Motor, sem campo novo) |

# Anexo B. Carga provisória de `Cad_Inss_Base_Piso_Percentual` (10 linhas)

| Código | Dispositivo (IN 2.110) | Hipótese | Percentual mínimo | Equipamento inerente |
|---|---|---|---|---|
| ART117_I | art. 117, I (e art. 119, na exceção do transporte de passageiros) | Transporte de passageiros, com combustível e manutenção por conta da contratada | 30 | não |
| ART117_II | art. 117, II | Limpeza hospitalar | 65 | não |
| ART117_III | art. 117, III | Outros serviços de limpeza | 80 | não |
| ART117_IV | art. 117, IV | Demais casos (inclui a copeiragem, leitura minha, C296) | 50 | não |
| ART118_II_A | art. 118, II, "a" | Serviços em geral, com equipamento inerente e sem valores no contrato | 50 | sim |
| ART118_II_B_1 | art. 118, II, "b", 1 | Pavimentação asfáltica | 10 | sim |
| ART118_II_B_2 | art. 118, II, "b", 2 | Terraplenagem, aterro sanitário e dragagem | 15 | sim |
| ART118_II_B_3 | art. 118, II, "b", 3 | Obras de arte (pontes ou viadutos) | 45 | sim |
| ART118_II_B_4 | art. 118, II, "b", 4 | Drenagem | 50 | sim |
| ART118_II_B_5 | art. 118, II, "b", 5 | Demais serviços de construção civil com equipamentos não manuais | 35 | sim |

Todas as linhas saem `provisorio`, com vigência inicial **01/11/2022** (art. 277 da IN 2.110, texto oficial) e fim em 31/12/9999; o texto é o original, e as alterações posteriores seguem em verificação (C302).

# Anexo C. Correspondência dos dispositivos

| Tema | Dispositivo | Onde está neste desenho |
|---|---|---|
| Exclusão com valores no contrato e na nota | IN RFB 2.110, art. 116 e §§ 1º a 3º | R3, `Forma_Previsao` = `com_valor`, aviso 6 |
| Exclusão com previsão sem valor, com piso | Art. 117 | R4, `Cad_Inss_Base_Piso_Percentual` |
| Equipamento inerente ao serviço | Art. 118, I e II, e § 1º | `Eh_Inerente_Ao_Servico`, R4, R9 |
| Sem previsão contratual ou sem discriminação | Art. 119 e parágrafo único | R1, R8 |
| Dedução de alimentação e vale-transporte | Art. 120 e § 1º | R13, aviso 13, campos da apuração |
| Vigência e revogação da IN 971 | Arts. 276, I, e 277 | Anexo B, C302 |
| Pisos globais e combinação dos artigos | SC Cosit 170/2026, itens 12 a 19 | R7 |
| Gênero alimentício da copeiragem (INSS) | SC Cosit 220/2026, ementa 1 | R6, `Tipo_Material` = `genero_alimenticio` |
| Emprego de materiais (IR, CSLL, PIS, Cofins) | IN RFB 1.234/2012, art. 2º, § 7º, I | 5.5, R10 e R11 |
| Serviços hospitalares e médicos fora | Art. 2º, § 8º | R12 |
| Base da retenção federal com glosa, juros e multa | IN 1.234, art. 2º, §§ 10 e 11 | R14 e R15 |
| Linhas 6147 e 6190 | Anexo I da IN 1.234 (lido no DOU de 12/01/2012, página 26, e conferido com o guia da Prefeitura de São Paulo) | `Cad_Retencao_Federal_Parametro` |

# Anexo D. Perguntas ao contador (C296 a C302, documento 188, Parte 18)

| Id | Assunto |
|---|---|
| C296 | Copeiragem com gêneros alimentícios: o tratamento é o do art. 116 mesmo sem valor no contrato? Sem valor, vale o art. 117 e o piso de 50% ("demais casos") ou a copeiragem tem outro percentual? |
| C297 | Piso global e combinação dos arts. 117 e 118 na mesma nota (itens 17.2 e 18.2 da SC Cosit 170/2026): confirmar a fórmula "maior entre dois valores" e como tratar o rateio entre tipos de serviço |
| C298 | Prova do material: que documentos valem (nota de compra, locação, rateio de estoque comum a vários contratos, material produzido pela contratada) e como se calcula o "custo de aquisição" quando o material sai do estoque da própria empresa |
| C299 | Alimentação e transporte (art. 120 da IN 2.110): a dedução incide **depois** do piso dos arts. 117 e 118, ou o piso é calculado sobre o valor bruto já sem a dedução; a nota precisa discriminar uma a uma; como se prova o limite do vale-transporte |
| C300 | SC Cosit 220/2026 e IN 1.234, § 7º, I (o texto da IN **não exige** material "essencial"; a essencialidade vem da SC 220): o que torna o material "essencial ao serviço" e se vale além da copeiragem; "planilhas anexas" (SC 220) e "planilhas integrantes" (IN 1.234) são a mesma coisa; e a verificação vale a cada pagamento |
| C301 | Quando o órgão público retém o INSS pela base reduzida e o IR pela linha 6147, o que o prestador deve informar na nota para o tomador (art. 2º, § 6º da IN 1.234) e qual a responsabilidade dele se a nota não discrimina |
| C302 | Alterações da IN 2.110 depois de 19/10/2022 nos arts. 116 a 120 (a IN RFB 2.185/2024 não os altera, pelo que li; as posteriores não verifiquei) e como tratar notas de contratos anteriores a 01/11/2022 (regidos pela IN 971, revogada) |
