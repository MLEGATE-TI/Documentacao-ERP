# Conferência das Fontes Oficiais Pendentes e a NT 13/2026 da EFD-Contribuições — Documento 226

*Você escolheu conferir nas fontes oficiais os três pontos que ficaram como leitura minha na revisão 46 (C21, C25 e C258). A conferência fechou os três e achou uma coisa que você não tinha pedido: a **Nota Técnica EFD-Contribuições nº 13/2026**, de novembro de 2026, que muda o leiaute da EFD-Contribuições para 2027 e contradiz em parte a resposta do contador à C25. **Nada foi aplicado ao dicionário, às cargas ou ao DDL**: as propostas esperam as suas respostas (seção 6) e o seu "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| Ponto | O que a fonte diz | Efeito no dicionário |
|---|---|---|
| **C21** (limite da CSLL no presumido; MP 1.303/2025) | A **MP 1.303/2025 perdeu a eficácia em 08/10/2025** (Ato Declaratório do Presidente da Mesa do Congresso nº 67, de 14/10/2025). O limite de R$ 5 milhões vem da **LC 224/2025, art. 4º, § 5º**; a Receita confirma R$ 1,25 milhão por trimestre e **R$ 3,75 milhões para a CSLL em 2026** (perguntas e respostas da Receita, itens 11 a 13) | Posso trocar a leitura minha por fonte oficial e validar as linhas da CSLL (Q226-5) |
| **C25** (fim da EFD-Contribuições) | O ato é a **Nota Técnica EFD-Contribuições 011/2026** (orientativa, da Receita) e, depois, a **NT 13/2026**. Nenhuma das duas fixa data de fim: a EFD **continua em 2027** para o regime de caixa, os saldos credores e os créditos presumidos da CBS. **Não é uma IN** | O contador disse "a princípio deixa de existir": a Receita diz que **não deixa**. Proposta de texto e de gatilhos (Q226-4) |
| **C258** (potência em kW na nota) | O grupo de veículo novo da NF-e (`veicProd`) tem **só a potência em CV** (`pot`); não achei campo em kW | O kW continua vindo da ficha (Inmetro); o cv da nota continua só como aviso. **Nenhuma mudança** |
| **NT 13/2026** (novo) | Registros novos 1950, 1959, F159 e 1980; F150 redefinido para o estoque de abertura da CBS; tabela nova de descrição do estoque | 4 mudanças em campos e 1 entidade nova propostas (seção 5) |

# 2. C21: o limite da CSLL e a MP 1.303/2025

**A MP caducou.** O Ato Declaratório do Presidente da Mesa do Congresso Nacional nº 67, de 14/10/2025 (DOU de 15/10/2025, seção 1, página 3), declara que a MP 1.303, de 11/06/2025 ("tributação de aplicações financeiras e ativos virtuais"), teve a vigência encerrada em 08/10/2025; a Câmara tinha retirado a MP de pauta por 251 votos a 193. As fontes que li não dizem que a MP tratasse do lucro presumido; **a regra do acréscimo de 10% e do limite está na LC 224/2025**, que o dicionário já cita (documento 51). A leitura minha de que "a MP não mexe no limite" fica então sem efeito: a MP não existe mais e o limite não vem dela.

**O que a Receita publicou** (perguntas e respostas "Redução dos Incentivos e Benefícios Tributários", versão 2, itens 11 a 14; li cerca de três quartos do texto):

| Dado | Valor | Item |
|---|---|---|
| Limite anual de receita bruta | R$ 5.000.000, com base no art. 4º, § 5º, da LC 224/2025 | 11 e 11.1 |
| Limite por trimestre | R$ 1.250.000 (para o IRPJ e para a CSLL) | 11 |
| IRPJ | acréscimo desde o 1º trimestre de 2026 | 12 |
| CSLL | acréscimo desde o 2º trimestre de 2026; **limite de 2026 de R$ 3.750.000** (três quartos do anual) | 12 e 13 |
| Receitas que contam | só as sujeitas ao percentual de presunção; receitas financeiras e ganhos de capital ficam de fora | 11.1 |

**Contra o dicionário** (`Cad_Presuncao_Acrescimo`): IRPJ R$ 5.000.000 desde 01/01/2026 (confere); CSLL R$ 3.750.000 de 01/04/2026 a 31/12/2026 (confere, e agora tem fonte oficial, além da resposta do contador); CSLL R$ 5.000.000 desde 01/01/2027 (é a regra permanente do art. 4º, § 5º; a Receita não fala de 2027 nos itens que li); limite trimestral de R$ 1.250.000 na CSLL (o item 11 vale para os dois impostos). **Proposta (Q226-5):** passar a `validado` a linha da CSLL de 2027 e o limite trimestral da CSLL, e preencher `Fundamento_Legal` das linhas com a LC 224/2025, art. 4º, § 5º, a IN RFB 2.305/2025, art. 15 (redação da IN 2.306/2026) e os itens 11 a 13 das perguntas e respostas. **Limite:** não li o texto da LC 224 nesta sessão (o documento 51 trouxe o art. 4º, § 5º) nem os itens 14 em diante do PDF da Receita.

# 3. C25: o fim da EFD-Contribuições

**O que a NT 011/2026 diz** (nota orientativa da Receita; o PDF que li não traz a data, e sites de notícias a dão como publicada em 04/02/2026): a EFD-Contribuições **não é descontinuada de imediato**; deixa de apurar novos fatos geradores de PIS e Cofins a partir de janeiro de 2027; a manutenção, a consulta e a retificação da escrituração persistem pelo **prazo mínimo de cinco anos** da legislação tributária (sem artigo citado); os saldos credores de 31/12/2026 devem estar corretos para compensar com a CBS (LC 214/2025); **o leiaute não muda** para escriturar CBS, IBS e IS nos documentos de 2026. A nota não cita nenhuma IN e não trata de regime de caixa.

**O que a NT 13/2026 diz** (li o PDF; o texto extraído não traz a data de publicação, e sites de notícias a dão como de 05/11/2026): a apuração regular de PIS e Cofins termina em 31/12/2026, e a EFD-Contribuições **continua existindo em 2027 para cinco finalidades**: (a) regime de caixa, "à medida do efetivo recebimento" (LC 214, art. 408, § 3º); (b) controle e uso dos saldos credores de 31/12/2026 (art. 378); (c) créditos presumidos da CBS do imobilizado, F120 e F130 (art. 380); (d) crédito presumido do **estoque de abertura de 01/01/2027**, F150 (art. 381); (e) a consolidação dos créditos de CBS no registro 1980. **Não informa data de fim nem prazo de guarda.**

**Contra a resposta do contador e o dicionário:**

| Ponto | Contador (16/11/2026) | Fonte oficial | Efeito |
|---|---|---|---|
| Existe depois de 2026? | "A princípio deixa de existir, podendo ser prorrogada" | **Continua** para as cinco finalidades acima; sem data de fim | O texto aplicado na revisão 46 em `Cad_Obrigacao_Acessoria.Vigencia_Fim` ("a princípio deixa de existir") precisa mudar (Q226-4) |
| Regime de caixa, competência de 2026 recebida em 2027 | "Até a última parcela recebida" | "À medida do efetivo recebimento" (NT 13/2026); a NT não diz "última parcela" | **Consistente**; a base legal passa a ser o art. 408, § 3º, da LC 214 |
| Ato oficial | Não citou | NT 011/2026 e NT 13/2026 (notas técnicas, não IN) | Fecha a pergunta "há ato oficial" da C25 |
| Guarda | — | Mínimo de cinco anos, sem artigo | Coincide com `Cad_Obrigacao_Guarda_Arquivo` (5 anos, sem fundamento legal, Q188-7) |

# 4. C258: a potência em kW na nota fiscal

O contador disse que "a nota fiscal deverá trazer kW". O grupo `veicProd` da NF-e (24 campos, em fonte de terceiro, o Buscador NCM, e **não** no manual da Receita) tem `pot`, "potência máxima do motor em CV", de 1 a 4 posições, obrigatório quando o grupo existe, e `cilin` (cilindradas); **não há campo em kW**. Dois resumos da NT 2025.002 v1.40 (Systax e Makrosystem) não falam de potência; as duas páginas da CNT não abriram. **Conclusão:** a expectativa do contador não está confirmada, e o dicionário **não muda**: `Cad_Veiculo_Versao.Potencia_Kw` vem da ficha técnica (Inmetro), a nota traz o cv, e a comparação continua só como aviso. **Limite:** não li o manual de orientação nem o XSD oficial da NF-e, nem uma nota técnica específica de veículos do Imposto Seletivo; se ela existir, o campo pode estar lá.

# 5. NT 13/2026: o que muda no dicionário

O dicionário já tem a base do estoque de abertura (`Mov_Estoque_Abertura_Cbs` e seus itens, com os três motivos do art. 381, 9,25%, importação, prazo de 30/06/2027 e 12 parcelas), os saldos credores (`Mov_Credito_Fiscal`, registros 1100 e 1500), o processo referenciado (`Mov_Apuracao_Processo_Referenciado`) e o hash da escrituração (`Mov_Escrituracao_Arquivo`). Faltam as peças abaixo. Li o texto da nota extraído por programa, com colunas de tamanho truncadas: **conferir tamanho e decimais no PDF antes de gerar o leiaute**.

| N | Registro da NT | O que a NT pede | Dicionário hoje | Proposta |
|---|---|---|---|---|
| 1 | **F150** (estoque de abertura da CBS) | NAT_BC_CRED = 18; CST do PIS e da Cofins de 50 a 56; descrição do estoque pela **tabela nova** (campo 13); alíquota de 1,65% e 7,6% no nacional e a da importação; vale também para o regime cumulativo, o misto e a ST ou monofasia | `Mov_Estoque_Abertura_Cbs_Item` guarda motivo, origem e valor; **não guarda o CST nem a descrição da tabela**. `Mov_Estoque_Abertura_Cbs` diz que é "distinta do F150" (`Mov_Credito_Estoque_Abertura`), o que a NT desmente: o F150 de 2027 é este estoque | **Q226-1:** domínio novo `descricao_estoque_abertura_cbs` (10 códigos: 1, 2, 21, 3, 4, 41, 5, 6, 7 e 8; provisório, porque a nota diz "inicialmente prevista"); 3 campos novos no item: `ID_Descricao_Estoque`, `ID_Cst_Pis` e `ID_Cst_Cofins` (50 a 56), obrigatórios quando `Elegivel` é verdadeiro; o F150 sai do agrupamento dos itens (nada armazenado); o texto da entidade passa a dizer que alimenta o F150 de 2027 |
| 2 | **F159** (processo do F150) | Número do processo e origem (1 Justiça Federal, 3 SRFB, 9 outros); só decisão transitada em julgado; desliga a validação padrão de alíquota; exige o 1010 ou 1020 | `Mov_Apuracao_Processo_Referenciado.Origem_Tipo` tem 3 valores, nenhum para o estoque | **Q226-2:** valor novo `estoque_abertura_cbs` em `Origem_Tipo`, apontando para o item do estoque |
| 3 | **1950 e 1959** (créditos de 2026, validação cruzada com EFD anteriores) | 1950: hash e datas da EFD anterior usada; 1959: por período, origem, tipo de crédito e contribuição, o apurado e o usado por desconto, ressarcimento, DCOMP e outras formas. "Preenchidos pelo PGE" | O hash do arquivo existe (`Hash_Escrituracao`); **não há ligação entre um arquivo e os anteriores que o validam**. O 1959 é cálculo sobre `Mov_Credito_Fiscal` | **Q226-3:** 1 entidade nova, `Mov_Escrituracao_Arquivo_Validacao` (arquivo, arquivo anterior opcional, hash de 40 posições, datas inicial e final: o 1950); o 1959 sai do cálculo sobre `Mov_Credito_Fiscal`, sem armazenar |
| 4 | **1980** e o quadro do recibo | Consolidação do crédito de CBS do período; no estoque, o total é a parcela vezes 12 | Parcelas em `Mov_Credito_Fiscal_Parcela` | Sem campo: **geração** a partir das linhas com CST de 50 a 56 |
| 5 | **F120 e F130** em 2027 | Estrutura mantida; a EFD de um mês com F120 ou F130 pode ser transmitida **a partir do último dia do período**, sem esperar o mês seguinte; o F150 vale de janeiro a junho de 2027, em qualquer dia | Prazo de transmissão por obrigação | **Q226-4:** regra de prazo em texto na obrigação; a entidade que guarda o prazo se localiza na aplicação |
| 6 | Obrigação em 2027 | Só existe para as cinco finalidades | `Cad_Obrigacao_Acessoria.Vigencia_Fim` com "por volta de 2033" e a nota da revisão 46 | **Q226-4:** sem data de fim (31/12/9999) e **gatilhos** para o Motor gerar a obrigação a partir de 2027: parcela de caixa de 2026 a receber, saldo credor de 31/12/2026, F120 ou F130 de crédito presumido, F150 |

**Da NT 011/2026, sem proposta:** os novos documentos (BP-e modelo 63, NFAg 75, NFGas 76, NF-e ABI 77, NFS-e Via e DeRE) devem ser escriturados nos registros atuais com `COD_MOD` = 55 enquanto a EFD não é adaptada (D100/D200 para o 63; C500/C600 para o 75 e o 76; F200 para o 77; A100 ou F100 para a NFS-e Via; Bloco I para a DeRE). **Não conferi se os documentos 164 e 165 já trazem essa regra de mapeamento**; se não trazem, é texto de regra, sem campo.

**Contagem se tudo for aprovado:** **1.240 entidades** (+1), **14.374 campos** (+3 no item do estoque e +6 na entidade nova do 1950: o identificador, `ID_Escrituracao_Arquivo`, `ID_Escrituracao_Arquivo_Anterior`, `Hash_Efdc_Anterior`, `Data_Inicial_Efdc_Anterior` e `Data_Final_Efdc_Anterior`), **3.687 referências** (+5: 3 no item e 2 na entidade nova), 1 valor novo de enumeração, 1 domínio novo em `Cad_Classe_Sistema` (371) e 1 tabela de DDL a mais (1.506); as entidades mestres e as referências genéricas não mudam.

# 6. Perguntas para você

| Id | Pergunta | Recomendação |
|---|---|---|
| Q226-1 | Criar o domínio `descricao_estoque_abertura_cbs` (10 códigos da tabela da NT 13/2026) e os campos `ID_Descricao_Estoque`, `ID_Cst_Pis` e `ID_Cst_Cofins` em `Mov_Estoque_Abertura_Cbs_Item`, e dizer que o F150 de 2027 sai deste estoque? | **Sim.** Sem eles o ERP não preenche os campos 7, 10 e 13 do F150. Os códigos entram provisórios |
| Q226-2 | Acrescentar `estoque_abertura_cbs` aos valores de `Origem_Tipo` em `Mov_Apuracao_Processo_Referenciado` (o F159)? | **Sim.** Reaproveita a estrutura única de processo (D-N85) |
| Q226-3 | Criar `Mov_Escrituracao_Arquivo_Validacao` para o registro 1950 e gerar o 1959 por cálculo? A NT diz que o PGE preenche os dois; não sei se um arquivo gerado pelo ERP deve gravá-los ou se o PGE os insere na importação | **Sim**, e **mandar a pergunta à Receita** (Fale Conosco, como no documento 98) antes de gerar. Enquanto isso o ERP guarda o dado e **não bloqueia** |
| Q226-4 | Tirar a "data de fim" da EFD-Contribuições (31/12/9999), registrar os gatilhos de 2027 (caixa de 2026, saldo credor, F120 e F130, F150) e as regras de transmissão antecipada, citando a NT 011/2026, a NT 13/2026 e os arts. 378, 380, 381 e 408, § 3º, da LC 214? | **Sim.** A resposta do contador à C25 fica registrada, mas a Receita diz que a EFD continua |
| Q226-5 | Passar a **validado** a linha da CSLL de 2027 e o limite trimestral da CSLL de `Cad_Presuncao_Acrescimo`, e preencher o fundamento legal das três linhas (LC 224, art. 4º, § 5º; IN RFB 2.305, art. 15; itens 11 a 13 das perguntas e respostas)? | **Sim**, com a ressalva de que não li o texto da LC 224 nesta sessão nem o PDF da Receita inteiro |

Para o contador entra uma pergunta nova no documento 188, a **C361**: o código 7 da tabela de descrição do estoque (`Motocicletas`, art. 43 da MP 2.158-35, no anexo da NT) aparece como "máquinas e implementos agrícolas" no texto do F150 da mesma nota; qual é o certo, e qual alínea do art. 381, II, da LC 214 ele cobre?

# 7. Pontos da NT 13/2026 que parecem erro da própria nota

1. No campo 12 do F150 a instrução manda somar o valor devolvido ao "campo 08", mas o campo 09 diz que a soma é com o 12; pelo contexto parece ser o campo 04.
2. O campo 05 do registro 1980 diz "soma dos campos 04 e 05", que se refere a ele mesmo; pelo contexto seria 03 e 04.
3. O código 7 do anexo (item 6 acima, C361).
4. A obrigatoriedade do F159 aparece ambígua ("OC N S") no texto extraído.

A aplicação, se você aprovar, usa o PDF e o Guia atualizado, e não esta leitura.

# 8. Como será aplicado e conferido

Quando você escrever "consolidar" (revisão 47): aplico o que você aprovar pelo mesmo mecanismo das revisões anteriores, regero a extração, a normalização, a auditoria, o DDL (PostgreSQL 16 e T-SQL) e os diagramas, gero a `Carga47` (códigos do domínio novo, ajuste das linhas da CSLL e as linhas de prazo e gatilho) e **confiro** (1) que as contagens são as da seção 5, (2) que o DDL roda sem erro, (3) que nenhum campo perdeu texto. Se você disser não a uma pergunta, o item sai e o resto segue. As Q226-1 a Q226-3 mudam a estrutura; as Q226-4 e Q226-5 só mudam texto e situação do dado.

# 9. Limites

- **As fontes oficiais que li são resumos por programa:** a NT 13/2026 (PDF, com colunas truncadas), a NT 011/2026 (PDF sem data), as perguntas e respostas da Receita (cerca de três quartos do texto) e o Ato Declaratório 67/2025. As datas de publicação das duas notas técnicas vêm de sites de notícias, não do PDF.
- **Não li** o texto da LC 224/2025 nem da LC 214/2025 nesta sessão, nem o manual de orientação ou o XSD da NF-e; o campo `pot` e a lista do `veicProd` vêm de um site de terceiros.
- **Sem validação do contador:** as cinco propostas são leituras minhas das fontes.
- Esta conferência **não substitui** a leitura do Guia Prático da EFD-Contribuições atualizado para 2027, que não encontrei.

Fontes: [Ato Declaratório do Presidente da Mesa do Congresso nº 67/2025](https://legis.senado.leg.br/norma/41564758); [Agência Senado, 08/10/2025](https://www12.senado.leg.br/noticias/materias/2025/10/08/camara-retira-mp-do-iof-de-pauta-e-texto-perdera-validade); [Receita Federal, perguntas e respostas sobre a redução de benefícios, v2](https://www.gov.br/receitafederal/pt-br/centrais-de-conteudo/publicacoes/perguntas-e-respostas/beneficios-fiscais/perguntas-e-respostas-reducao-de-beneficios-v2.pdf); [NT EFD-Contribuições 011/2026](https://www.reformatributaria.com/wp-content/uploads/2026/02/Descontinuidade_da_EFD_Contribui_es_1770165768.pdf); [NT EFD-Contribuições 13/2026](https://www.reformatributaria.com/wp-content/uploads/2026/11/Nota-Tecnica-013_2026-Alteracoes-EFD-Contribuicoes-para-RTC-2027.pdf); [Buscador NCM, campo pot](https://buscadorncm.com.br/nfe/tags-xml/pot); [Buscador NCM, grupo veicProd](https://buscadorncm.com.br/nfe/tags-xml/veicprod); [Systax, NT 2025.002 v1.40](https://www.systax.com.br/?p=42952).
