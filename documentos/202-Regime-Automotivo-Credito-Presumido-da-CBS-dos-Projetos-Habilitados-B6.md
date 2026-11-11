# Regime automotivo: crédito presumido da CBS dos projetos habilitados (B6) — Documento 202

> **O que este documento faz.** Você escolheu o B6 como o próximo desenho. É o regime automotivo da montadora: o **crédito presumido da CBS** dos projetos habilitados nos termos do art. 11-C da Lei 9.440/1997 e dos arts. 1º a 4º da Lei 9.826/1999, de 2027 a 2032 (LC 214, arts. 309 a 315; Decreto 12.955, arts. 518 a 527). Li os dois textos, conferi o que o dicionário já tem e propus **oito entidades e um campo novo**, com as duas fórmulas, o limite de uso, os compromissos e a devolução. Pela regra do documento 201 (Q201-3), os **25 parâmetros** do B6 entram **com a documentação do efeito e da obrigação**. Onde a lei não fecha a conta, deixei uma leitura minha, marcada como provisória, e perguntei ao contador (C248 a C255).
>
> **Nada foi aplicado ao dicionário.** Ele continua na revisão 37 (1.155 entidades e 13.017 campos). Os documentos 200 e 201 foram aprovados (D-N534 e D-N536) e entram no próximo "consolidar" com 1.165 entidades e 13.204 campos; este documento soma a esse total e só entra depois das suas respostas à seção 7.

*Fontes: o texto da LC 214/2025 consolidado com a LC 227/2026 (arts. 309 a 316; o texto que li não traz marca de alteração da LC 227 nesses artigos) e o Decreto 12.955/2026 (arts. 518 a 527), os dois lidos na íntegra nos artigos citados; os documentos do Projeto 94 e 115 (a fila de desenho), 158 (a habilitação da Suframa e o crédito presumido da ZFM), 155 e 160 (o catálogo central de parâmetros por obrigação), 198 e 200 (D-N529 a D-N534) e 201 (a documentação dos parâmetros, D-N535 e D-N536). **Não li** a Lei 9.440, a Lei 9.826, os Decretos 10.457/2020 e 7.422/2010 (que o decreto manda continuar valendo), o ato concessório de nenhum projeto, a Tipi, nem o leiaute da escrituração do IBS e da CBS (não fechado, documento 32).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que a lei dá.** Um **crédito presumido de CBS**, de 01/01/2027 a 31/12/2032, para projetos habilitados que **produzem veículos** (elétricos, com ou sem motor a combustão a biocombustível; a combustão a biocombustível, só para projeto antigo; e, pelo Decreto, partes, peças e pneumáticos). Há **duas fórmulas**, conforme a lei do projeto: na Lei 9.440, um **percentual** das vendas no mercado interno que cai por faixa do **mês de fruição** (11,60%, 10% e 8,70%, reduzidos em 20% do inicial por ano de 2029 a 2032); na Lei 9.826, **`V × Al × (1 − Al) × F`**, com **Al** a alíquota de IPI de 31/12/2025 por posição da Tipi e **F** o fator do ano (32% em 2027 e 2028, caindo até 6,40% em 2032). Em 2033 o crédito acaba.
- **O que a lei limita.** O crédito **não se transfere**, **não se ressarce**, só se usa **a partir do mês seguinte** e só abate **a CBS** e os **débitos federais próprios** do estabelecimento habilitado, na **fração** entre as vendas de veículos dele e as de todos os estabelecimentos da pessoa jurídica nos três meses anteriores. Não se soma a outro benefício federal de CBS. A habilitação pode ser **suspensa** (irregularidade fiscal: o uso para) ou **cancelada** (o crédito apurado volta, vezes 100% menos F1 × F2 × F3).
- **O que o dicionário já tem.** A habilitação genérica (`Cad_Habilitacao_Regime_Especial`, com situação ativa, suspensa e cancelada, e versões com vigência), o **marcador da habilitação no item de venda** (`Mov_Nota_Fiscal_Saida_Item.ID_Habilitacao`, que já tem também os campos de veículo), a **alíquota de IPI da Tipi com vigência** (`Cad_Classificacao_Mercadoria.Aliquota_Ipi`), o crédito fiscal e o seu uso (`Mov_Credito_Fiscal`, `Mov_Credito_Fiscal_Aplicacao`, `Mov_Perdcomp`) e o molde da Suframa (`Cad_Habilitacao_Suframa`) para uma habilitação com extensão própria. **Faltam** a parte automotiva da habilitação, a lista de produtos do projeto, os percentuais, a apuração mensal, o limite de uso, os compromissos e a devolução.
- **Proposta: 8 entidades novas e 1 campo novo em entidade existente, nenhum domínio novo** (um valor novo em `tipo_regime_especial_federal`). `Cad_Habilitacao_Automotiva` (22 campos) e `Cad_Habilitacao_Automotiva_Produto` (10); `Cad_Credito_Automotivo_Parametro` (16, com vigência; 22 linhas de carga); `Mov_Credito_Automotivo_Apuracao` (20) e `Mov_Credito_Automotivo_Apuracao_Ncm` (9); `Mov_Credito_Automotivo_Debitos_Proprios` (14); `Mov_Habilitacao_Automotiva_Compromisso` (14); `Mov_Credito_Automotivo_Devolucao` (26). O crédito nasce em `Mov_Credito_Fiscal` com origem nova `presumido_automotivo`. O ERP **calcula, grava e avisa; não bloqueia** (D-N284).
- **Oito pontos em que a lei não fecha a conta** foram lidos de um jeito meu e vão ao contador: de quando se conta o **mês de fruição** (C248), o **IPI na base** (C249), os **débitos próprios** e o limite mensal (C250), o **tratamento contábil** (C251), a **alíquota de IPI com as Notas Complementares** (C252), as **partes, peças e pneumáticos**, que o Decreto traz e a LC 214 que li não (C253), o que é **veículo** na fração (C254) e a **devolução** (C255). Quatro viram **parâmetros por empresa com padrão visível e aviso**, como na Q201-4.
- **Documentação dos parâmetros** (regra do documento 201): **25 parâmetros** (7 legais, 14 chaves de decisão e 4 leituras provisórias), **34 efeitos**, **todos na escrituração do IBS e da CBS**, e 5 linhas novas no catálogo central. ECD, ECF e as obrigações de compensação ficam **sem efeito documentado** por falta de norma (C251).
- **Perguntas:** Q202-1 a Q202-11 (seção 7), cada uma com recomendação. **Para o contador:** C248 a C255 (Anexo E), que entram no documento 188.
- **Se você aprovar:** 1.173 entidades (+8), 13.336 campos (+132), 3.463 chaves estrangeiras (+18), 22 linhas de parâmetros legais, 25 de documentação, 34 de efeito, 5 do catálogo e 1 valor de domínio; os documentos 14 (D-N537) e 38 (seção 1.31) acompanham.

# 2. O que a lei e o decreto dizem

Li os arts. 309 a 316 da LC 214 e os arts. 518 a 527 do Decreto 12.955. O decreto repete a lei e acrescenta o que a lei deixou para ato do Poder Executivo; as diferenças estão na coluna da direita.

| Tema | Onde | O que diz | Diferença entre a LC e o Decreto |
|-------------|------------------------|--------------------------------|--------------------------------|
| Quem tem o crédito | LC 309, caput e § 1º; Decreto 518 | Projetos habilitados ao art. 11-C da Lei 9.440 e aos arts. 1º a 4º da Lei 9.826, de 2027 a 2032: projetos aprovados até 31/12/2024 de pessoas jurídicas habilitadas em 20/12/2023, e novos projetos aprovados até 31/12/2025 que ampliam ou reiniciam produção em planta já habilitada | Iguais |
| O que o projeto produz | LC 309, § 1º, I e § 2º; Decreto 518, §§ 1º e 2º | Veículos com motor elétrico capaz de tracionar sozinho (com ou sem motor a combustão a biocombustível); os projetos antigos também de veículos a combustão a biocombustível | **O Decreto soma partes, peças, componentes, conjuntos, subconjuntos e pneumáticos** (518, § 2º, III), que não achei no art. 309 (C253) |
| Requisitos | LC 309, §§ 2º a 6º; Decreto 518, §§ 3º a 6º, e 519 | Iniciar a produção de veículos até 01/01/2028; compromissos de investimento mínimo, produção mínima, processo produtivo básico, manutenção da produção e pesquisa, desenvolvimento e inovação de 10% do crédito; regularidade fiscal; comprovação no MDIC, que manda as auditorias à RFB todo ano; os Decretos 10.457 e 7.422 seguem valendo até o ato | O Decreto traz o inciso II do § 3º com os cinco compromissos; a LC põe a pesquisa e desenvolvimento no § 3º, I |
| Sem cumulação | LC 310; Decreto 520 | Não se soma a outro benefício fiscal federal da CBS do mesmo beneficiário | Iguais |
| Lei 9.440: percentual | LC 311; Decreto 521 | Percentual sobre as vendas no mercado interno do mês dos produtos do projeto: 11,60% até o 12º mês de fruição, 10% do 13º ao 48º e 8,70% do 49º ao 60º; reduzidos em 20% do inicial por ano, de 2029 a 2032; extinto em 2033 | **O Decreto escreve a matriz ano × faixa**; conferi que ela bate com a conta do § 3º da LC (Anexo C) |
| Base de cálculo | LC 311, §§ 1º e 2º; Decreto 521, §§ 1º e 2º | Não entram os tributos da venda e saem os descontos incondicionais; só vendas com CBS integral; ficam fora isentas, imunes, alíquota zero, reduzidas, suspensas, canceladas e devolvidas | **A LC fala em "impostos e contribuições incidentes"; o Decreto lista seis (ICMS, ICMS substituição, ISS, CBS, IBS e Imposto Seletivo) e não cita o IPI** (C249) |
| Lei 9.826: fórmula | LC 312; Decreto 522 | `CP = V × Al × (1 − Al) × F`; Al é a alíquota de IPI de 31/12/2025 da Tipi, com as Notas Complementares, nas posições 8702 a 8704; F é 32% (2027 e 2028), 25,60%, 19,20%, 12,80% e 6,40% (2032) | A LC chama (1 − Al) de "fator de eficiência", para cada posição da Tipi; mesma conta |
| Uso do crédito | LC 313; Decreto 523 | Só para compensar com débitos de CBS (art. 26, I) e com débitos próprios de tributos da RFB; não se transfere a outro estabelecimento; só a partir do mês seguinte; não se ressarce | **A LC deixa o rateio dos débitos próprios para ato do Poder Executivo; o Decreto o escreve** (§§ 2º e 3º): fração entre vendas de veículos do habilitado e de todos os estabelecimentos, nos três meses anteriores ao fato gerador (C250 e C254) |
| Descumprimento | LC 314; Decreto 524 e 525 | Cancelamento da habilitação com efeitos retroativos ou suspensão; a suspensão é por irregularidade fiscal e suspende o uso do crédito; sanada, o crédito pretérito pode ser usado | O parágrafo único é da LC; o Decreto o repete no art. 525 |
| Devolução | LC 315; Decreto 526 e 527 | Crédito apurado no período do ato × (100% − F1 × F2 × F3); cada F é a razão entre o realizado e o mínimo do ato, até 100%; o MDIC apura; juros de mora como os tributos federais; recolher até o último dia útil do mês seguinte ao cancelamento; cinco anos para iniciar o processo e para cobrar | Iguais |
| IPI de 2026 | LC 316 | Prorroga até 31/12/2026 os benefícios de **IPI** dos mesmos projetos; o crédito presumido do art. 11-C é a alíquota da Lei 10.485 vezes o valor das vendas vezes 0,75 | **Fora deste documento**: é IPI, e de 2026 |

# 3. O que o dicionário já tem

| Entidade | O que guarda hoje | O que falta para o B6 |
|---------------------------------|----------------------------------|----------------------------------|
| `Cad_Habilitacao_Regime_Especial` (versionada) | O titular, o tipo (domínio `tipo_regime_especial_federal`), o número do ato, a situação (ativa, suspensa, cancelada) e a vigência. Serve ao REIDI, ao REPES, ao IPI e à Suframa. | Um valor para o tipo (`regime_automotivo`) e os dados do projeto automotivo (lei, estabelecimento, início da fruição, período do crédito). |
| `Cad_Habilitacao_Suframa` | O molde: uma extensão 1:1 da habilitação geral, com os dados próprios do regime. | Nada: é o modelo que o B6 copia. |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Habilitacao`, `ID_Classificacao_NCM`, os campos `Veiculo_*` e os descontos do item. | Nada: o `ID_Habilitacao` já é a marca de que o item é do projeto. |
| `Mov_Apuracao_Tributo_Item` | Por item: forma de tributação, mecanismo de redução, valor desonerado e os tributos. | Nada: o B6 lê dele o que é "CBS integral" e os tributos que saem da base. |
| `Cad_Classificacao_Mercadoria` | A alíquota de IPI da Tipi, com vigência (`Aliquota_Ipi`). | Nada: a versão vigente em 31/12/2025 dá o Al. |
| `Mov_Credito_Fiscal`, `Mov_Credito_Fiscal_Aplicacao`, `Mov_Perdcomp` | O crédito, os usos (compensação com a CBS, declaração de compensação, ressarcimento) e o PER/DCOMP. | Uma origem nova (`presumido_automotivo`) e a ligação do uso ao limite mensal. |
| `Mov_Credito_Presumido_Zfm` e `Cad_Zfm_Alc_Regra` | O crédito presumido da ZFM e o catálogo de regras com vigência (documento 158). | Nada: o B6 segue o desenho, com outra entidade porque a fórmula e o uso são outros. |
| `Cad_Obrigacao_Parametro_Definicao` e a documentação do documento 201 | O catálogo central e a regra de que todo parâmetro tem efeito e obrigação. | Cinco linhas novas e as 25 documentações do B6. |
| `Mov_Titulo` | Os títulos a pagar, com `Origem_Tipo`. | Um valor novo para o título da devolução. |

# 4. Achados e leituras minhas

**4.1 A habilitação já existe e o B6 só a estende.** O titular, a situação e a vigência estão na habilitação geral. A suspensão por irregularidade fiscal (art. 525) é uma **versão nova** da habilitação com `Situacao_Habilitacao = suspensa`, e o parágrafo único (o crédito pretérito volta a poder ser usado quando sanada) é a versão seguinte com `ativa`. Por isso não criei entidade de ocorrência, como a Suframa precisou.

**4.2 O item de venda já tem a marca.** O `ID_Habilitacao` do item de venda e os campos `Veiculo_*` já existem. A base do crédito é o conjunto de itens de saída do estabelecimento, no mês, com a habilitação marcada. O Motor **sugere a marca** quando o estabelecimento e a NCM batem com a lista de produtos do projeto; sem a marca o item não entra e há aviso.

**4.3 Duas fórmulas, uma só apuração.** O projeto é de uma lei ou de outra, e a fórmula segue a lei. A apuração mensal tem um cabeçalho (a base, o mês de fruição e o crédito) e, para a Lei 9.826, uma linha por NCM, porque o Al é de cada posição e a conta não é linear no total.

**4.4 Leitura minha: o mês de fruição conta do início da fruição do benefício.** A lei diz "mês de fruição do benefício" e dá três faixas de 12, 36 e 12 meses. Não diz se o mês é contado desde o início da fruição do benefício original (que pode ter começado antes de 2027) ou se recomeça com a CBS. Li a primeira: a habilitação guarda a **data de início da fruição** e o Motor conta os meses dela. Depois do 60º mês não há percentual, e o crédito do mês é zero. O usuário pode **informar o mês** na apuração. Vira o parâmetro `credito_auto_contagem_mes_fruicao` (padrão provisório `desde_inicio_fruicao`) e a C248.

**4.5 Leitura minha: o IPI fica na base.** A LC 214 diz que não entram "os impostos e as contribuições incidentes sobre a operação"; o Decreto lista seis tributos e não cita o IPI. Segui o Decreto: o IPI **fica na base**, e o Motor avisa quando o item tem IPI destacado. Vira o parâmetro `credito_auto_ipi_fora_da_base` (padrão provisório falso) e a C249.

**4.6 Leitura minha: o limite é mensal e não acumula.** O art. 523, § 2º, diz que os débitos próprios são os débitos federais do mês multiplicados pela fração. Não diz se o limite que sobrou num mês soma ao seguinte. Li que **não acumula**, e que os tributos que entram nos débitos são os tributos federais que o ERP apura no mês, com os acréscimos legais. Viram dois parâmetros (`credito_auto_limite_acumula` e `credito_auto_tributos_debito_proprio`, com padrões provisórios) e a C250.

**4.7 A alíquota Al tem duas fontes.** A lei manda a alíquota de IPI de 31/12/2025, com as Notas Complementares. O Motor lê `Cad_Classificacao_Mercadoria.Aliquota_Ipi` da versão dessa data. Como a Tipi muda e as Notas Complementares podem mudar a alíquota por produto, o produto do projeto pode **trazer a alíquota informada**, que vale no lugar da lida e fica gravada na apuração com a origem. A C252 pergunta qual é a fonte certa.

**4.8 O ERP não conversa com o MDIC.** Os compromissos, a auditoria e o cancelamento são do MDIC. O ERP **registra** o que o ato e a auditoria dizem (o mínimo, o realizado, a situação) e usa o registro para os avisos e para a conferência da devolução, como o documento 150 fez com o auto de infração (D-N284). O valor da devolução é o que o MDIC apurou; o que o ERP calcula é só **conferência**.

**4.9 As partes, peças e pneumáticos estão só no Decreto.** O art. 518, § 2º, III, do Decreto inclui esses produtos no projeto; o art. 309 da LC 214 que li não tem a alínea. Pus a marca `Abrange_Partes_Pecas_Pneumaticos` e um **aviso permanente** enquanto a C253 não for respondida. Não inventei fórmula própria para elas: seguem a lei do projeto.

**4.10 O IPI de 2026 fica fora.** O art. 316 da LC 214 prorroga os benefícios de **IPI** dos mesmos projetos até 31/12/2026. É outro tributo e é do ano que está acabando; não desenhei. Se algum cliente precisar do crédito presumido de IPI de 2026, é outro documento.

**4.11 Efeito nas obrigações.** O crédito aparece na apuração da escrituração do IBS e da CBS (que não tem leiaute fechado) e é usado em compensações com débitos federais por declaração de compensação. **Não encontrei norma** sobre o efeito nas demais obrigações (ECD, ECF, DCTFWeb): não documentei efeito algum nelas, e a C251 pergunta.

# 5. Proposta

## 5.1 Nenhum domínio novo

O B6 **não cria domínio**. Entra **um valor novo** em `tipo_regime_especial_federal`, domínio aberto de `Cad_Classe_Sistema`: **`regime_automotivo`** (Anexo D). As enumerações das entidades novas ficam nas próprias entidades.

## 5.2 As oito entidades

| Entidade | Para quê | Vigência | Campos |
|--------------------------------|---------------------------------------------------|---------|-------|
| `Cad_Habilitacao_Automotiva` | A parte automotiva da habilitação: o projeto aprovado nos termos do art. | sim | 22 |
| `Cad_Habilitacao_Automotiva_Produto` | Os produtos do projeto: o que a habilitação alcança, por NCM. | não | 10 |
| `Cad_Credito_Automotivo_Parametro` | Os parâmetros legais do crédito presumido automotivo: os percentuais por faixa do mês de fruição (art. | sim | 16 |
| `Mov_Credito_Automotivo_Apuracao` | A apuração mensal do crédito presumido de um estabelecimento habilitado: a base (vendas no mercado interno com CBS integral, menos as exclusões), o mês de fruição, o percentual ou o fator, o crédito calculado e a data a partir da qual ele pode ser usado. | não | 20 |
| `Mov_Credito_Automotivo_Apuracao_Ncm` | A base por NCM do mês, para a fórmula do IPI da Lei 9.826 (`CP = V × Al × (1 − Al) × F`): a alíquota de IPI é a de cada posição, por isso a conta é por NCM. | não | 9 |
| `Mov_Credito_Automotivo_Debitos_Proprios` | O limite mensal de uso do crédito: os débitos federais do mês multiplicados pela fração entre as vendas de veículos do estabelecimento habilitado e as de todos os estabelecimentos da pessoa jurídica nos três meses anteriores (art. | não | 14 |
| `Mov_Habilitacao_Automotiva_Compromisso` | Os compromissos do ato concessório e o que se cumpriu: investimento mínimo, produção mínima, processo produtivo básico, manutenção da produção e pesquisa, desenvolvimento e inovação de 10% do crédito. | não | 14 |
| `Mov_Credito_Automotivo_Devolucao` | A devolução do crédito quando a habilitação é cancelada (art. | não | 26 |

Em `Cad_Habilitacao_Automotiva` e em `Cad_Credito_Automotivo_Parametro` valem as convenções da Fase 0: `ID_X` é a identidade, `ID_X_Versao` a chave da versão, e `Vigencia_Inicio`, `Vigencia_Fim` (31/12/9999 quando em aberto) e `Motivo_Vigencia` fecham cada linha. Nas outras seis, que não têm vigência, o que muda de valor entra como linha nova do mês (apuração, limite) ou como atualização do registro (compromisso, devolução).

### `Cad_Habilitacao_Automotiva` (Contabilidade & Fiscal, com vigência, 22 campos)

A parte automotiva da habilitação: o projeto aprovado nos termos do art. 11-C da Lei 9.440/1997 ou dos arts. 1º a 4º da Lei 9.826/1999, o estabelecimento incentivado, o ato concessório, o início da fruição e o período do crédito. Especializa `Cad_Habilitacao_Regime_Especial` (tipo `regime_automotivo`) do mesmo jeito que `Cad_Habilitacao_Suframa` o faz para a Suframa. O titular, a situação (ativa, suspensa, cancelada) e o número do ato ficam na habilitação geral.

| Campo | Tipo | Descrição |
|------------------------|--------------------------------------|--------------------------------------|
| `ID_Habilitacao_Automotiva` | identificador | Chave. |
| `ID_Habilitacao_Automotiva_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Habilitacao_Automotiva_Versao). Fase 0, seção 2. |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) --- identidade | A habilitação de tipo `regime_automotivo` (valor novo em `tipo_regime_especial_federal`). O titular é a pessoa jurídica habilitada. |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento incentivado, na região incentivada. O crédito só se usa para os débitos próprios dele (Decreto 12.955, art. 523, § 1º, II). |
| `Lei_Origem` | enumeração {lei_9440_art_11c, lei_9826_arts_1_a_4} | De qual lei vem o projeto. Decide a fórmula: percentual sobre as vendas (Lei 9.440, art. 11-C; Decreto, art. 521) ou a fórmula do IPI (Lei 9.826; Decreto, art. 522). |
| `Condicao_Projeto` | enumeração {projeto_aprovado_ate_2024, novo_projeto_aprovado_ate_2025} | Projeto aprovado até 31/12/2024 de pessoa jurídica habilitada em 20/12/2023, ou novo projeto aprovado até 31/12/2025 que amplia ou reinicia produção em planta já habilitada (art. 518, § 1º, II). |
| `Abrange_Veiculo_Eletrico` | booleano | O projeto produz veículos com motor elétrico capaz de tracionar sozinho, com ou sem motor a combustão a biocombustível (art. 518, § 2º, I). |
| `Abrange_Veiculo_Combustao_Biocombustivel` | booleano | O projeto produz veículos de motor a combustão com biocombustível (art. 518, § 2º, II). |
| `Abrange_Partes_Pecas_Pneumaticos` | booleano | O projeto produz partes, peças, conjuntos, subconjuntos e pneumáticos para veículos elétricos (art. 518, § 2º, III). Não achei esta alínea no texto do art. 309 da LC 214 que li (C253). |
| `Numero_Ato_Concessorio` | código (até 40) | O número do ato concessório do benefício, que fixa os compromissos e o período do crédito. |
| `Data_Ato_Concessorio` | data | A data do ato concessório. |
| `Data_Aprovacao_Projeto` | data | A data da aprovação do projeto, que decide a condição do projeto. |
| `Data_Inicio_Fruicao` | data | O primeiro mês de fruição do benefício. O Motor conta daqui o mês de fruição das faixas do art. 521 (leitura minha, C248). |
| `Periodo_Credito_Inicio` | competência | Primeiro mês do período do crédito fixado no ato concessório; é a base da devolução do art. 526. |
| `Periodo_Credito_Fim` | competência | Último mês do período do crédito. |
| `Data_Limite_Inicio_Producao` | data | O prazo para iniciar a produção de veículos no estabelecimento incentivado: 01/01/2028 (art. 518, § 3º, I). |
| `Data_Inicio_Producao_Veiculos` | data, opcional | Quando a produção de veículos de fato começou. Vazia depois do prazo gera aviso. |
| `Normas_Anteriores_Vigentes` | booleano | Verdadeiro enquanto o ato do Poder Executivo do § 4º não sair e o ato concessório segue o Decreto 10.457/2020 ou o Decreto 7.422/2010 (art. 518, § 5º). |
| `Fundamento_Legal` | texto, opcional | Os artigos da LC 214 e do Decreto. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Habilitacao_Automotiva_Produto` (Contabilidade & Fiscal, sem vigência, 10 campos)

Os produtos do projeto: o que a habilitação alcança, por NCM. É a lista que o Motor usa para marcar os itens de venda (`Mov_Nota_Fiscal_Saida_Item.ID_Habilitacao`) e, no projeto da Lei 9.826, a alíquota de IPI de cada posição.

| Campo | Tipo | Descrição |
|-----------------------|-----------------------------------|------------------------------------------|
| `ID_Habilitacao_Automotiva_Produto` | identificador | Chave. |
| `ID_Habilitacao_Automotiva` | referência (Cad_Habilitacao_Automotiva) | A habilitação automotiva a que o produto pertence. |
| `ID_Classificacao` | referência (Cad_Classificacao_Mercadoria) | A NCM do produto. Na Lei 9.826 vale a posição 8702, 8703 ou 8704 (Decreto, art. 522). |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico), opcional | O produto do cadastro, quando o projeto aponta um item específico. |
| `Descricao_No_Projeto` | texto, opcional | Como o produto aparece no ato concessório. |
| `Aliquota_Ipi_Referencia` | número, opcional | A alíquota de IPI vigente em 31/12/2025 conforme a Tipi, com as Notas Complementares. Vazia: o Motor lê `Cad_Classificacao_Mercadoria.Aliquota_Ipi` da versão da data de referência. Informar aqui congela o valor do ato (C252). |
| `Origem_Aliquota_Ipi` | enumeração {tipi_na_data_referencia, informada}, opcional | De onde vem a alíquota usada: da Tipi na data de referência ou informada por quem cadastra. |
| `Data_Inclusao` | data | Desde quando o produto está no projeto. |
| `Data_Exclusao` | data, opcional | Até quando; vazia enquanto o produto estiver no projeto. |
| `Observacao` | texto, opcional | Anotação livre. |

### `Cad_Credito_Automotivo_Parametro` (Contabilidade & Fiscal, com vigência, 16 campos)

Os parâmetros legais do crédito presumido automotivo: os percentuais por faixa do mês de fruição (art. 521), os fatores multiplicadores da fórmula do IPI (art. 522), a data de referência da alíquota de IPI e o percentual mínimo de pesquisa e desenvolvimento (art. 518, § 3º, II, e). Uma linha por valor, com vigência, como `Cad_Zfm_Alc_Regra`.

| Campo | Tipo | Descrição |
|-----------------------|--------------------------------------|--------------------------------------|
| `ID_Credito_Automotivo_Parametro` | identificador | Chave. |
| `ID_Credito_Automotivo_Parametro_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Credito_Automotivo_Parametro_Versao). Fase 0, seção 2. |
| `Codigo` | código (até 60) --- identidade | Estável, em minúsculas (por exemplo, `auto_pct_faixa_1_2027`). |
| `Tipo_Parametro` | enumeração {percentual_faixa_fruicao, fator_multiplicador_ipi, data_referencia_aliquota_ipi, pdi_minimo_sobre_credito} | `percentual_faixa_fruicao`: percentual do art. 521. `fator_multiplicador_ipi`: fator F do art. 522. `data_referencia_aliquota_ipi`: a data da alíquota de IPI (31/12/2025). `pdi_minimo_sobre_credito`: o mínimo de pesquisa e desenvolvimento, 10% do crédito apurado. |
| `Lei_Origem` | enumeração {lei_9440_art_11c, lei_9826_arts_1_a_4, ambas} | A lei do projeto a que o parâmetro se aplica. |
| `Mes_Fruicao_Inicial` | número inteiro, opcional | Primeiro mês de fruição da faixa (1, 13 ou 49). Só no percentual por faixa. |
| `Mes_Fruicao_Final` | número inteiro, opcional | Último mês de fruição da faixa (12, 48 ou 60). Só no percentual por faixa. |
| `Valor_Percentual` | número, opcional | O percentual ou o fator, em pontos percentuais (11,60 é onze inteiros e sessenta centésimos). Vazio na data de referência. |
| `Data_Referencia` | data, opcional | Só no tipo `data_referencia_aliquota_ipi`. |
| `Origem_Regra` | enumeração {lei, decreto} | `lei` quando a LC 214 e o Decreto dizem o mesmo; `decreto` quando só o Decreto traz o número. Os percentuais de 2029 a 2032 são `lei` pela conta do art. 311, § 3º, da LC 214, que bate com as tabelas do art. 521. |
| `Fundamento_Legal` | texto | Os artigos da LC 214 e do Decreto. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Credito_Automotivo_Apuracao` (Contabilidade & Fiscal, sem vigência, 20 campos)

A apuração mensal do crédito presumido de um estabelecimento habilitado: a base (vendas no mercado interno com CBS integral, menos as exclusões), o mês de fruição, o percentual ou o fator, o crédito calculado e a data a partir da qual ele pode ser usado. Guarda a memória de cálculo que o auditor pede. O crédito nasce em `Mov_Credito_Fiscal` com origem `presumido_automotivo`.

| Campo | Tipo | Descrição |
|------------------------|-----------------------------------|------------------------------------------|
| `ID_Credito_Automotivo_Apuracao` | identificador | Chave. |
| `ID_Habilitacao_Automotiva` | referência (Cad_Habilitacao_Automotiva) | A habilitação apurada. |
| `Competencia` | competência | O mês das vendas. |
| `Lei_Origem` | enumeração {lei_9440_art_11c, lei_9826_arts_1_a_4} | Copiada da habilitação na data da apuração, para a memória de cálculo. |
| `Mes_Fruicao_Calculado` | número inteiro, opcional | O mês de fruição da competência, contado de `Cad_Habilitacao_Automotiva.Data_Inicio_Fruicao` (ou de 01/2027, conforme o parâmetro de contagem). Só na Lei 9.440. |
| `Mes_Fruicao_Informado` | número inteiro, opcional | O mês de fruição que o usuário informa quando discorda do calculado (por exemplo, pelo ato concessório). Quando preenchido, vale no lugar do calculado, e o Motor avisa. |
| `ID_Credito_Automotivo_Parametro` | referência (Cad_Credito_Automotivo_Parametro), opcional | A linha do percentual por faixa usada. Só na Lei 9.440; na Lei 9.826 a linha é a do fator, na linha de cada NCM. |
| `Valor_Vendas_Projeto` | número | As vendas dos produtos do projeto no mercado interno no mês (itens com `Mov_Nota_Fiscal_Saida_Item.ID_Habilitacao` da habilitação). |
| `Valor_Vendas_Sem_Cbs_Integral` | número | As vendas isentas, imunes, fora da incidência, com alíquota zero, com redução de alíquota ou de base, ou com suspensão: saem da base (art. 521, § 2º, I). |
| `Valor_Vendas_Canceladas_Devolvidas` | número | As vendas canceladas e as devolvidas: saem da base (art. 521, § 2º, II). |
| `Valor_Tributos_Excluidos` | número | ICMS, ICMS substituição, ISS, CBS, IBS e Imposto Seletivo da operação: saem da base (art. 521, § 1º, I). O IPI só sai se o parâmetro mandar (C249). |
| `Valor_Descontos_Incondicionais` | número | Os descontos incondicionais: saem da base (art. 521, § 1º, II). Desconto condicional não sai. |
| `Valor_Base_Calculo` | número | Calculado: as vendas menos as quatro exclusões acima. Na Lei 9.826 é a soma das bases por NCM. |
| `Percentual_Aplicado` | número, opcional | Na Lei 9.440: o percentual da faixa do mês de fruição. Vazio na Lei 9.826. |
| `Valor_Credito_Calculado` | número | Calculado. Lei 9.440: base × percentual. Lei 9.826: soma dos créditos por NCM (`Mov_Credito_Automotivo_Apuracao_Ncm`). Zero depois de 2032 e quando a habilitação está cancelada. |
| `Data_Disponivel_Uso` | data | O primeiro dia do mês seguinte à competência: o crédito só se usa a partir daí (art. 523, § 1º, II). |
| `ID_Credito` | referência (Mov_Credito_Fiscal), opcional | O crédito gerado (`Origem` = `presumido_automotivo`, CBS). |
| `Regra_Provisoria` | booleano | Verdadeiro quando o cálculo usou parâmetro provisório ou padrão visível (todas as linhas de `Cad_Credito_Automotivo_Parametro` nascem provisórias). |
| `Memoria_Calculo` | texto | O cálculo escrito: vendas, exclusões, base, mês de fruição, percentual ou fator, crédito. |
| `Aviso` | texto, opcional | Os avisos da seção 6 que valeram para esta apuração. |

### `Mov_Credito_Automotivo_Apuracao_Ncm` (Contabilidade & Fiscal, sem vigência, 9 campos)

A base por NCM do mês, para a fórmula do IPI da Lei 9.826 (`CP = V × Al × (1 − Al) × F`): a alíquota de IPI é a de cada posição, por isso a conta é por NCM. Na Lei 9.440 a linha não é usada.

| Campo | Tipo | Descrição |
|-----------------------|------------------------------------|-----------------------------------------|
| `ID_Credito_Automotivo_Apuracao_Ncm` | identificador | Chave. |
| `ID_Credito_Automotivo_Apuracao` | referência (Mov_Credito_Automotivo_Apuracao) | A apuração do mês. |
| `ID_Classificacao` | referência (Cad_Classificacao_Mercadoria) | A NCM (posição 8702 a 8704). |
| `Valor_Base_Ncm` | número | A base da NCM no mês, depois das mesmas exclusões da apuração. |
| `Aliquota_Ipi_Referencia` | número | Al: a alíquota de IPI vigente em 31/12/2025 da NCM, gravada na apuração. |
| `Origem_Aliquota_Ipi` | enumeração {tipi_na_data_referencia, informada_no_projeto} | De onde veio Al: da Tipi na data de referência ou do produto do projeto. |
| `Fator_Multiplicador` | número | F do ano (32%, 25,60%, 19,20%, 12,80% ou 6,40%), lido de `Cad_Credito_Automotivo_Parametro`. |
| `ID_Credito_Automotivo_Parametro` | referência (Cad_Credito_Automotivo_Parametro) | A linha do fator usada. |
| `Valor_Credito_Ncm` | número | Calculado: `Valor_Base_Ncm × Al × (1 − Al) × F`, com Al e F em fração. |

### `Mov_Credito_Automotivo_Debitos_Proprios` (Contabilidade & Fiscal, sem vigência, 14 campos)

O limite mensal de uso do crédito: os débitos federais do mês multiplicados pela fração entre as vendas de veículos do estabelecimento habilitado e as de todos os estabelecimentos da pessoa jurídica nos três meses anteriores (art. 523, §§ 2º e 3º). Cada uso do crédito consome este limite.

| Campo | Tipo | Descrição |
|---------------------------|----------------------------|---------------------------------------------|
| `ID_Credito_Automotivo_Debitos_Proprios` | identificador | Chave. |
| `ID_Habilitacao_Automotiva` | referência (Cad_Habilitacao_Automotiva) | A habilitação. |
| `Competencia` | competência | O mês do fato gerador dos tributos que se quer compensar. |
| `Competencia_Base_Inicio` | competência | Primeiro dos três meses anteriores. |
| `Competencia_Base_Fim` | competência | Último dos três meses anteriores (o mês imediatamente anterior ao fato gerador). |
| `Valor_Vendas_Veiculos_Habilitado` | número | As vendas de veículos produzidos no estabelecimento habilitado nos três meses, pelas notas fiscais eletrônicas, sem canceladas, devolvidas, tributos e descontos incondicionais (art. 523, § 3º). |
| `Valor_Vendas_Veiculos_Total` | número | As vendas de veículos de todos os estabelecimentos da pessoa jurídica nos mesmos três meses, com as mesmas exclusões. |
| `Fracao_Debitos_Proprios` | número, opcional | Calculado: habilitado ÷ total. Vazio quando o total é zero; aí o limite é zero e o ERP avisa. |
| `Valor_Debitos_Federais_Mes` | número | Os débitos da pessoa jurídica nos impostos e contribuições federais do mês, com os acréscimos legais, dos tributos que o parâmetro de composição manda somar (C250). |
| `Valor_Limite_Uso` | número | Calculado: débitos federais do mês × fração. O máximo que o crédito pode abater no mês. |
| `Valor_Utilizado_Mes` | número | Calculado: a soma dos usos do mês (`Mov_Credito_Fiscal_Aplicacao` ligados a esta linha), na compensação com a CBS e na declaração de compensação. |
| `Saldo_Limite_Mes` | número | Calculado: limite menos utilizado. Negativo gera aviso. |
| `Regra_Provisoria` | booleano | Verdadeiro quando a composição dos débitos usou o padrão visível. |
| `Memoria_Calculo` | texto | O cálculo escrito. |

### `Mov_Habilitacao_Automotiva_Compromisso` (Contabilidade & Fiscal, sem vigência, 14 campos)

Os compromissos do ato concessório e o que se cumpriu: investimento mínimo, produção mínima, processo produtivo básico, manutenção da produção e pesquisa, desenvolvimento e inovação de 10% do crédito. Alimenta os fatores F1, F2 e F3 da devolução e os avisos. O ERP só registra o que o ato e a auditoria do MDIC dizem (D-N284).

| Campo | Tipo | Descrição |
|-----------------------|--------------------------------------|--------------------------------------|
| `ID_Habilitacao_Automotiva_Compromisso` | identificador | Chave. |
| `ID_Habilitacao_Automotiva` | referência (Cad_Habilitacao_Automotiva) | A habilitação. |
| `Tipo_Compromisso` | enumeração {investimento_minimo, producao_minima, processo_produtivo_basico, manutencao_producao, pdi_sobre_credito} | Os cinco compromissos do art. 518, § 3º, II. |
| `Periodo_Inicio` | data | Início do período a que o mínimo e o realizado se referem. |
| `Periodo_Fim` | data | Fim do período. |
| `Unidade_Medida` | texto, opcional | Reais, unidades, meses ou "cumprido" (processo produtivo básico). |
| `Valor_Minimo_Ato` | número, opcional | O mínimo fixado no ato concessório. No `pdi_sobre_credito`, o Motor calcula 10% do crédito apurado e grava aqui. |
| `Valor_Realizado` | número, opcional | O que se realizou no período. |
| `Percentual_Cumprimento` | número, opcional | Calculado: realizado ÷ mínimo, limitado a 100% (art. 526, § 1º, II). |
| `Fonte` | enumeração {ato_concessorio, auditoria_mdic, informado_usuario} | De onde vem o dado. |
| `Data_Auditoria` | data, opcional | Quando o MDIC auditou e mandou o resultado à RFB (art. 519, parágrafo único). |
| `Situacao` | enumeração {em_andamento, cumprido, descumprido} | O estado do compromisso, informado ou conferido. |
| `ID_Documento` | referência (Cad_Documento), opcional | O ato, o laudo ou a auditoria. |
| `Observacao` | texto, opcional | Anotação livre. |

### `Mov_Credito_Automotivo_Devolucao` (Contabilidade & Fiscal, sem vigência, 26 campos)

A devolução do crédito quando a habilitação é cancelada (art. 526): o crédito apurado no período vezes 100% menos o produto de F1, F2 e F3. O MDIC apura o valor; o ERP guarda o que o MDIC apurou, calcula a conta como conferência, avisa da divergência, gera o título a pagar e conta o prazo de cinco anos.

| Campo | Tipo | Descrição |
|---------------------|---------------------------------------|---------------------------------------|
| `ID_Credito_Automotivo_Devolucao` | identificador | Chave. |
| `ID_Habilitacao_Automotiva` | referência (Cad_Habilitacao_Automotiva) | A habilitação cancelada. |
| `Data_Ciencia_Descumprimento` | data | A ciência do descumprimento; o processo de cancelamento começa em até cinco anos dela (art. 527, I). |
| `Data_Cancelamento` | data | O cancelamento da habilitação; o recolhimento vence no último dia útil do mês seguinte (art. 527, III). |
| `Periodo_Credito_Inicio` | competência | Início do período do crédito fixado no ato concessório. |
| `Periodo_Credito_Fim` | competência | Fim do período. |
| `Valor_Credito_Apurado_Periodo` | número | Calculado: a soma de `Valor_Credito_Calculado` das apurações do período. |
| `Valor_Investimentos_Realizados` | número | Somatório dos investimentos realizados no período do crédito (de `Mov_Habilitacao_Automotiva_Compromisso`). |
| `Valor_Investimentos_Minimo` | número | O volume mínimo de investimentos do ato. |
| `Fator_F1` | número | Calculado: investimentos realizados ÷ mínimo, no máximo 100%. |
| `Valor_Producao_Realizada` | número | Somatório dos volumes de produção realizados no período do crédito. |
| `Valor_Producao_Minima` | número | O volume mínimo de produção do ato. |
| `Fator_F2` | número | Calculado: produção realizada ÷ mínima, no máximo 100%. |
| `Prazo_Manutencao_Realizado_Meses` | número inteiro | O prazo em que a produção se manteve no estabelecimento, inclusive depois do fim do benefício. |
| `Prazo_Manutencao_Minimo_Meses` | número inteiro | O prazo mínimo do ato, inclusive o período depois do fim do benefício. |
| `Fator_F3` | número | Calculado: prazo realizado ÷ mínimo, no máximo 100%. |
| `Percentual_Devolucao` | número | Calculado: 100% menos F1 × F2 × F3. |
| `Valor_Devolucao_Calculado` | número | Calculado: crédito apurado no período × percentual de devolução. |
| `Valor_Devolucao_Apurado_Mdic` | número, opcional | O valor que o MDIC apurou no encerramento do processo (art. 527, I). É o que vale; o calculado confere. |
| `Valor_Juros_Mora` | número, opcional | Os juros de mora informados, na forma dos tributos federais, contados do período em que ocorreu o fato do cancelamento (art. 527, II). O ERP não os calcula. |
| `Divergencia_Mdic` | booleano | Calculado: o apurado pelo MDIC difere do calculado. |
| `Data_Vencimento_Recolhimento` | data | O último dia útil do mês seguinte ao cancelamento (art. 527, III). |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título a pagar da devolução (`Origem_Tipo` = `devolucao_credito_automotivo`). |
| `Data_Limite_Cobranca` | data | Cinco anos a partir do primeiro dia do mês seguinte àquele em que o recolhimento deveria ter sido feito (art. 527, parágrafo único). |
| `Situacao` | enumeração {em_apuracao, apurada, titulo_gerado, recolhida, prescrita} | O estado da devolução. |
| `Memoria_Calculo` | texto | A conta escrita. |

## 5.3 O que muda em entidades que já existem

**Um campo novo:**

| Entidade | Campo | Tipo | Para quê |
|----------------|--------------------|------------------------------|---------------------------------|
| `Mov_Credito_Fiscal_Aplicacao` | `ID_Credito_Automotivo_Debitos_Proprios` | referência (Mov_Credito_Automotivo_Debitos_Proprios), opcional | O limite mensal que o uso do crédito presumido automotivo consumiu. Só quando o crédito tem `Origem` = `presumido_automotivo`. Aviso quando o uso passa do limite. |

**Textos, enumerações e carga** (sem campo novo):

| Entidade | Mudança |
|--------------------------------------------------|--------------------------------------------------|
| `Mov_Credito_Fiscal.Origem` | Um valor novo, **`presumido_automotivo`**. O crédito é de CBS e usa o mesmo ciclo de estados dos demais; não tem prazo de utilização na lei, então `Data_Limite_Utilizacao` fica vazia. |
| `Mov_Titulo.Origem_Tipo` | Um valor novo, **`devolucao_credito_automotivo`**: a devolução do art. 526 gera título a pagar, como o `arrendamento_parcela` do documento 200. |
| `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao` | **Só texto:** a descrição passa a dizer que, no regime automotivo, o número é o do **ato concessório**, que vem do MDIC e não da Receita. |
| `Cad_Classe_Sistema` | **Só carga:** `tipo_regime_especial_federal` ganha `regime_automotivo`. |
| `Cad_Obrigacao_Parametro_Definicao` | **Só carga:** cinco linhas novas, em `ESCRITURACAO_IBS_CBS` (Anexo D). |
| `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao` (documento 201) | **Só carga:** 25 e 34 linhas do B6 (Anexos A e B), pela regra da Q201-3. |
| `Mov_Nota_Fiscal_Saida_Item`, `Mov_Apuracao_Tributo_Item`, `Cad_Classificacao_Mercadoria`, `Mov_Perdcomp` | **Nenhum campo novo:** o B6 só lê. |

## 5.4 Como o crédito é calculado

O Motor calcula **por mês**, no fechamento da competência. O ERP **calcula, grava e avisa; não bloqueia**. Os números dos exemplos são **inventados**, só para mostrar a conta.

- **Passo 1. Acha a habilitação.** Lê `Cad_Habilitacao_Regime_Especial` do tipo `regime_automotivo` e a extensão `Cad_Habilitacao_Automotiva` do estabelecimento, com vigência na competência. Sem habilitação ativa, o crédito do mês é zero (cancelada) ou o uso fica suspenso (suspensa, seção 5.5). A lei do projeto (`Lei_Origem`) escolhe a fórmula.
- **Passo 2. Junta os itens.** Os itens de saída do estabelecimento, no mês, com `Mov_Nota_Fiscal_Saida_Item.ID_Habilitacao` igual à habilitação. O Motor sugere a marca quando a NCM bate com `Cad_Habilitacao_Automotiva_Produto`; item da NCM do projeto sem a marca gera aviso.
- **Passo 3. Tira o que a lei manda tirar.** Do total das vendas dos itens saem: as vendas **sem CBS integral** (isentas, imunes, fora da incidência, com alíquota zero, com redução de alíquota ou de base, ou com suspensão, lidas de `Mov_Apuracao_Tributo_Item`: forma de tributação, mecanismo de redução e valor desonerado); as **canceladas e devolvidas**; os **tributos da operação** (ICMS, ICMS substituição, ISS, CBS, IBS e Imposto Seletivo; o IPI só se o parâmetro mandar); e os **descontos incondicionais** (`Valor_Desconto_Item`). O desconto condicional não sai. O resultado é `Valor_Base_Calculo`.
- **Passo 4. Aplica a fórmula da lei do projeto.**
  - **Lei 9.440 (`lei_9440_art_11c`).** Calcula o **mês de fruição** (`Mes_Fruicao_Calculado` = meses entre `Data_Inicio_Fruicao` e a competência, mais um, ou o `Mes_Fruicao_Informado`), escolhe em `Cad_Credito_Automotivo_Parametro` a linha do ano e da faixa e calcula **crédito = base × percentual**. Exemplo: em 2027, mês 5, base de R$ 80.000.000 e percentual de 11,60%: crédito de R$ 9.280.000. Depois do 60º mês não há linha, e o crédito do mês é zero, com aviso.
  - **Lei 9.826 (`lei_9826_arts_1_a_4`).** Para cada NCM (posição 8702 a 8704), lê a alíquota **Al** (do produto do projeto, se informada, ou de `Cad_Classificacao_Mercadoria.Aliquota_Ipi` na versão de 31/12/2025) e o fator **F** do ano, e calcula **crédito da NCM = base da NCM × Al × (1 − Al) × F**. Exemplo: base de R$ 50.000.000, Al de 10% e F de 32% (2027): 50.000.000 × 0,10 × 0,90 × 0,32 = R$ 1.440.000. O crédito do mês é a soma dos créditos das NCMs, gravados em `Mov_Credito_Automotivo_Apuracao_Ncm`.
- **Passo 5. Aplica o fim do benefício.** Competência de 2033 em diante: não há linha de parâmetro (o crédito está extinto) e o crédito é zero, com aviso.
- **Passo 6. Grava.** Cria `Mov_Credito_Automotivo_Apuracao` com a memória de cálculo e cria o crédito em `Mov_Credito_Fiscal` (CBS, `Origem` = `presumido_automotivo`), com `Data_Apropriacao` e `Data_Disponivel_Uso` no primeiro dia do mês seguinte. Marca `Regra_Provisoria` quando usou algum padrão provisório.

## 5.5 Uso do crédito e limite mensal

O crédito é usado nas **duas formas** do art. 523: **compensação com débitos de CBS** (art. 26, I; `Forma_Utilizacao` = `compensacao_cbs`) e **compensação com débitos próprios de tributos federais** por declaração de compensação (`declaracao_compensacao`, com `Mov_Perdcomp`). Cada uso é uma linha de `Mov_Credito_Fiscal_Aplicacao`, ligada à linha do limite do mês pelo campo novo.

- **Limite do mês.** `Mov_Credito_Automotivo_Debitos_Proprios`, uma linha por habilitação e mês do fato gerador: `Valor_Limite_Uso` = `Valor_Debitos_Federais_Mes` × `Fracao_Debitos_Proprios`, com a fração = vendas de veículos do estabelecimento habilitado ÷ vendas de veículos de todos os estabelecimentos, **nos três meses anteriores** ao fato gerador (art. 523, §§ 2º e 3º). Exemplo: débitos federais de R$ 40.000.000, vendas do habilitado de R$ 300.000.000 e totais de R$ 900.000.000 nos três meses: fração de 1/3 e limite de R$ 13.333.333,33. O uso do mês não passa do limite do mês (padrão provisório, C250); passou, o ERP avisa.
- **Só a partir do mês seguinte.** Uso com data anterior a `Data_Disponivel_Uso` gera aviso (art. 523, § 1º, II).
- **O que é vedado.** O crédito **não pode ser ressarcido** nem **transferido** a outro estabelecimento (art. 523, § 1º, I e III): ressarcimento (`pedido_ressarcimento`), transferência por sucessão e transferência de cooperativa em crédito com origem `presumido_automotivo` geram aviso. Compensação com débitos de **outro** estabelecimento da pessoa jurídica gera aviso.
- **Sem cumulação.** Se o beneficiário tem, na mesma competência, outro benefício federal de CBS (por exemplo, um crédito presumido de outra habilitação), o ERP avisa (art. 520).

## 5.6 Suspensão, cancelamento e devolução

- **Suspensão (art. 525).** A irregularidade fiscal suspende o **uso** do crédito, e o crédito do mês continua nascendo. No ERP é uma **versão nova** de `Cad_Habilitacao_Regime_Especial` com `Situacao_Habilitacao = suspensa`: o uso na data da suspensão gera aviso. Sanada, vem outra versão `ativa` e o crédito pretérito volta a poder ser usado, sem prazo. O ERP **não suspende sozinho**: a suspensão é ato, e quem a registra é o usuário.
- **Cancelamento (art. 526).** A habilitação passa a `cancelada` com efeito retroativo. O MDIC apura a devolução; o processo começa em até cinco anos da ciência do descumprimento.
- **Devolução.** `Mov_Credito_Automotivo_Devolucao`: `Valor_Credito_Apurado_Periodo` (soma das apurações do período do ato) × **(100% − F1 × F2 × F3)**, com F1 = investimentos realizados ÷ mínimo, F2 = produção realizada ÷ mínima e F3 = prazo de manutenção realizado ÷ mínimo, cada um **limitado a 100%**. Exemplo: crédito apurado de R$ 120.000.000, F1 de 80%, F2 de 100% e F3 de 50%: devolve R$ 120.000.000 × (1 − 0,40) = R$ 72.000.000. **O valor que vale é o do MDIC** (`Valor_Devolucao_Apurado_Mdic`); o calculado é conferência, e a diferença gera aviso. Os **juros de mora** o ERP não calcula: guarda o informado. O **título a pagar** vence no último dia útil do mês seguinte ao cancelamento (art. 527, III), e o prazo de cobrança é de cinco anos (`Data_Limite_Cobranca`).
- **Compromissos.** `Mov_Habilitacao_Automotiva_Compromisso` guarda, por tipo e período, o mínimo do ato e o realizado (`Valor_Minimo_Ato`, `Valor_Realizado`). A pesquisa e desenvolvimento tem mínimo calculado: 10% do crédito apurado (`Cad_Credito_Automotivo_Parametro`, tipo `pdi_minimo_sobre_credito`). Descumprimento gera aviso na apuração.

## 5.7 Documentação dos parâmetros (regra do documento 201)

Pela Q201-3, **nenhum parâmetro entra sem documentação do efeito e da obrigação**. O B6 tem **25 parâmetros e chaves de decisão** em três grupos: **7 parâmetros legais** (as colunas de `Cad_Credito_Automotivo_Parametro` e o catálogo que as mostra), **14 chaves de decisão** (campos da habilitação, do produto, da apuração e do compromisso que o Motor lê, mais três que já existem e o B6 passa a ler) e **4 leituras provisórias** (os parâmetros por empresa da seção 5.8). A documentação de cada um está no **Anexo A** e os **34 efeitos** no **Anexo B**: 9 de cálculo do valor, 10 de seleção de regra, 6 que condicionam o crédito, 3 que o vedam, 2 de vigência e 4 avisos. **Todos os efeitos estão na escrituração do IBS e da CBS**; ECD, ECF, DCTFWeb e as demais não têm efeito documentado por falta de norma (C251). A auditoria da carga confere que cada parâmetro tem documentação e ao menos um efeito (Q201-3).

## 5.8 Padrão provisório das quatro leituras

Quatro leituras minhas viram **parâmetros por empresa com padrão visível e aviso a cada uso**, como as cinco do documento 201 (Q201-4): a contagem do mês de fruição (`credito_auto_contagem_mes_fruicao`, padrão `desde_inicio_fruicao`, C248), o IPI fora da base (`credito_auto_ipi_fora_da_base`, padrão falso, C249), os tributos que compõem os débitos próprios (`credito_auto_tributos_debito_proprio`, padrão "todos os tributos federais que o ERP apura", C250) e o limite que acumula (`credito_auto_limite_acumula`, padrão falso, C250). O padrão está em `Valor_Padrao` da documentação e na tela; a resposta do contador cria o valor em `Cad_Obrigacao_Parametro_Valor` (por empresa, com vigência e situação "validado") e o aviso some. É a mesma exceção à regra "sem padrão" da Q155 que você aprovou na Q201-4.

# 6. Regras de texto: o que o Motor avisa

Nenhuma regra bloqueia; todas gravam o aviso na linha e mostram a mensagem ao usuário (D-N284: "o ERP avisa, não bloqueia").

| # | Regra | Onde avisa |
|------|-----------------------------------------------|-----------------------------------------------|
| 1 | Habilitação da Lei 9.440 **sem data de início da fruição**: o mês de fruição não é calculável | `Mov_Credito_Automotivo_Apuracao` |
| 2 | **Mês de fruição informado** no lugar do calculado | `Mov_Credito_Automotivo_Apuracao` |
| 3 | Mês de fruição **acima de 60**: sem percentual, crédito do mês zero | `Mov_Credito_Automotivo_Apuracao` |
| 4 | **Padrão provisório** de parâmetro usado (a mensagem traz o parâmetro, o padrão e a documentação) | `Mov_Credito_Automotivo_Apuracao` e `Mov_Credito_Automotivo_Debitos_Proprios` |
| 5 | Item com a **NCM do projeto vendido sem a marca** da habilitação | `Mov_Nota_Fiscal_Saida_Item` |
| 6 | Item com **IPI destacado** com o IPI na base (padrão) | `Mov_Credito_Automotivo_Apuracao` |
| 7 | Produto da Lei 9.826 **sem alíquota Al** (nem na Tipi da data nem informada): crédito da NCM zero | `Mov_Credito_Automotivo_Apuracao_Ncm` |
| 8 | **Alíquota informada** no produto diferente da Tipi da data de referência | `Mov_Credito_Automotivo_Apuracao_Ncm` |
| 9 | Uso do crédito com a habilitação **suspensa** na data | `Mov_Credito_Fiscal_Aplicacao` |
| 10 | Uso **antes do mês seguinte** à competência | `Mov_Credito_Fiscal_Aplicacao` |
| 11 | Uso **acima do limite mensal** | `Mov_Credito_Automotivo_Debitos_Proprios` |
| 12 | **Ressarcimento**, transferência a outro estabelecimento ou compensação de débito de outro estabelecimento com crédito automotivo (art. 523, § 1º) | `Mov_Credito_Fiscal_Aplicacao` |
| 13 | **Fração sem denominador** (vendas totais de veículos zero): limite zero | `Mov_Credito_Automotivo_Debitos_Proprios` |
| 14 | Outro **benefício federal de CBS** do mesmo beneficiário na competência (art. 520) | `Mov_Credito_Automotivo_Apuracao` |
| 15 | Passou de **01/01/2028** sem data de início da produção de veículos | `Cad_Habilitacao_Automotiva` |
| 16 | **Compromisso** descumprido ou abaixo do mínimo; pesquisa e desenvolvimento **abaixo de 10%** do crédito apurado | `Mov_Habilitacao_Automotiva_Compromisso` |
| 17 | **Condição do projeto** incompatível (projeto de combustão com condição de projeto novo) ou aprovação depois do limite | `Cad_Habilitacao_Automotiva` |
| 18 | **Partes, peças e pneumáticos** no projeto: aviso permanente até a C253 | `Cad_Habilitacao_Automotiva` |
| 19 | Venda **antes de 01/01/2027** ou **depois de 31/12/2032**: sem linha de parâmetro | `Mov_Credito_Automotivo_Apuracao` |
| 20 | **Divergência** entre a devolução calculada e a apurada pelo MDIC | `Mov_Credito_Automotivo_Devolucao` |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---------|------------------------------------------------------------|-------------------------------|
| Q202-1 | Aprova o **escopo** do B6: o crédito presumido da CBS dos projetos habilitados (Lei 9.440, art. 11-C, e Lei 9.826, arts. 1º a 4º), de 2027 a 2032, as **oito entidades** e o campo novo em entidade existente, para **qualquer cliente**, deixando de fora o crédito de IPI de 2026 (LC 214, art. 316)? | Sim |
| Q202-2 | Aprova a **habilitação automotiva** como extensão de `Cad_Habilitacao_Regime_Especial` (valor novo `regime_automotivo`), com `Cad_Habilitacao_Automotiva` (22 campos) e `Cad_Habilitacao_Automotiva_Produto` (10), no molde da Suframa, com a suspensão como versão nova da habilitação geral? | Sim |
| Q202-3 | Aprova `Cad_Credito_Automotivo_Parametro` (16 campos, com vigência) e as **22 linhas provisórias** do Anexo C (15 percentuais, 5 fatores, a data de referência do IPI e o mínimo de 10% de pesquisa e desenvolvimento), que nascem com `Situacao_Dado = provisorio`? | Sim |
| Q202-4 | Aprova a **apuração mensal** (`Mov_Credito_Automotivo_Apuracao`, 20 campos, e a base por NCM, 9 campos) com as duas fórmulas da seção 5.4, a alíquota Al lida da Tipi de 31/12/2025 ou informada no produto (C252), o crédito em `Mov_Credito_Fiscal` com a origem `presumido_automotivo` e o uso a partir do mês seguinte? | Sim |
| Q202-5 | Aprova as **quatro leituras provisórias** como parâmetros por empresa, com **padrão visível e aviso a cada uso** (como na Q201-4): mês de fruição contado do início da fruição (C248), IPI na base (C249), débitos próprios com todos os tributos federais que o ERP apura e limite que não acumula (C250)? A alternativa é o Motor não calcular até o contador responder. | Sim, com padrão visível e aviso |
| Q202-6 | Aprova o **limite mensal de uso** (`Mov_Credito_Automotivo_Debitos_Proprios`, 14 campos), o campo novo `ID_Credito_Automotivo_Debitos_Proprios` em `Mov_Credito_Fiscal_Aplicacao` e os avisos de uso da seção 6 (limite, mês seguinte, ressarcimento e transferência, habilitação suspensa, sem cumulação), com "veículo" como as posições 8702 a 8704 (C254)? | Sim |
| Q202-7 | Aprova `Mov_Habilitacao_Automotiva_Compromisso` (14 campos): o ERP **só registra** o que o ato e a auditoria do MDIC dizem, avisa sem bloquear e usa o registro nos fatores da devolução? | Sim |
| Q202-8 | Aprova `Mov_Credito_Automotivo_Devolucao` (26 campos): **F1, F2 e F3 como conferência** do valor que o MDIC apurar, o **título a pagar** (valor novo `devolucao_credito_automotivo` em `Mov_Titulo.Origem_Tipo`) e o prazo de cinco anos, **sem calcular os juros de mora** (C255)? | Sim |
| Q202-9 | Aprova a **documentação dos 25 parâmetros** do B6 (34 efeitos, todos na escrituração do IBS e da CBS), as **cinco linhas** novas no catálogo central e o texto novo de `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao`, deixando ECD, ECF, DCTFWeb e demais **sem efeito documentado** até a C251? | Sim |
| Q202-10 | O crédito vale de **01/01/2027** a **31/12/2032**, com aviso para venda fora do período, e o parâmetro de 2033 em diante **não existe** (crédito extinto)? | Sim |
| Q202-11 | As **partes, peças e pneumáticos** do art. 518, § 2º, III, do Decreto entram com a marca `Abrange_Partes_Pecas_Pneumaticos` e **aviso permanente** até o contador responder se a LC 214 os alcança (C253)? | Sim |

# 8. O que acontece se você aprovar

| Item | Efeito |
|---------------------------|-------------------------------------------------------------------------|
| Entidades | **1.165 → 1.173** (+8, todas em Contabilidade & Fiscal; 1.155 na revisão 37 mais 8 do documento 200, 2 do 201 e 8 deste) |
| Campos | **13.204 → 13.336** (+132: 131 nas oito entidades novas e 1 em `Mov_Credito_Fiscal_Aplicacao`) |
| Chaves estrangeiras | **3.445 → 3.463** (+18: 17 nas entidades novas e 1 em `Mov_Credito_Fiscal_Aplicacao`) |
| Domínios | **355 → 355** (nenhum novo) |
| Valores de domínio | **+1** em `tipo_regime_especial_federal` (`regime_automotivo`) |
| Carga | **22** linhas de `Cad_Credito_Automotivo_Parametro`, **25** de documentação, **34** de efeito, **5** do catálogo central e **1** valor de domínio (Anexo D) |
| Textos e enumerações | `Mov_Credito_Fiscal.Origem` (+1), `Mov_Titulo.Origem_Tipo` (+1) e `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao` (texto) |
| Ondas, DDL e ER | As oito entidades entram na onda de Contabilidade & Fiscal; `Cad_Habilitacao_Automotiva` e `Cad_Credito_Automotivo_Parametro` geram também a tabela `_Versao`; regerados na consolidação |
| Documentos | 14 (D-N537), 38 (seção 1.31) e 188 (C248 a C255, total 255) |

# 9. Limites

- **Li a LC 214, arts. 309 a 316, e o Decreto 12.955, arts. 518 a 527, na íntegra.** O texto da LC que li não traz marca de alteração da LC 227 nesses artigos; **não conferi** com o texto oficial do Planalto neste documento.
- **Não li** a Lei 9.440 e a Lei 9.826 (a lei do projeto e o que "mês de fruição" quer dizer vêm delas), os Decretos 10.457/2020 e 7.422/2010 (que o Decreto manda continuar valendo até o ato), **nenhum ato concessório**, a Tipi e o ato do Poder Executivo do art. 518, § 4º (não publicado, pelo que sei). As entidades guardam o que a lei manda saber, e não o que os atos concessórios trazem.
- **Quatro leituras são minhas e provisórias**: o mês de fruição contado do início da fruição, o IPI na base, os débitos próprios com todos os tributos federais e o limite que não acumula. Mais três **leituras de desenho** sem parâmetro: "veículo" como as posições 8702 a 8704 na fração, a alíquota Al por NCM de oito dígitos, e o crédito do mês de uma habilitação suspensa continuando a nascer (só o uso para). **Todas as 22 linhas de parâmetro nascem provisórias**; o contador valida linha a linha.
- **Os percentuais e fatores** foram conferidos contra o texto do art. 521 (15 percentuais) e do art. 522 (5 fatores) por um programa, e a matriz de 2029 a 2032 bate com a conta do art. 311, § 3º, da LC.
- **O ERP não conversa com o MDIC** nem transmite nada: registra o ato, os compromissos, a auditoria e o cancelamento, e avisa. A suspensão e o cancelamento são registrados pelo usuário.
- **A fórmula da Lei 9.826 depende da Tipi de 31/12/2025**, que o ERP só tem se o cadastro de NCM carregou a versão dessa data; sem ela, vale a alíquota informada no produto.
- **O leiaute da escrituração do IBS e da CBS não existe**: a coluna `Local_Do_Efeito` descreve o ponto da apuração, e `Leiaute_Referencia` fica "leiaute ainda não fechado".
- **Fora deste desenho:** o crédito presumido de **IPI de 2026** (LC 214, art. 316), a **venda a ZFM ou ALC** pelo beneficiário e o efeito contábil do crédito (C251).
- **As contagens** vêm de um programa sobre o modelo da revisão 37 (1.155 entidades, 13.017 campos, 3.404 chaves, 355 domínios) somado aos documentos 200 e 201, conferido contra os nomes e os destinos de cada chave; o texto dos artigos eu conferi à mão nos trechos citados.
- **Nada passou por validação do contador.** As oito perguntas C248 a C255 estão no documento 188.

# Anexo A. Documentação dos 25 parâmetros do B6

Pela regra da Q201-3. Cada linha é uma linha de `Cad_Parametro_Documentacao`; o **efeito** de cada uma está no Anexo B. **Quem altera:** `contador` (parâmetro, com a permissão "Parametrizar obrigação", Q155-4), `usuario_do_contrato` (quem cadastra a habilitação ou o movimento) ou `carga_do_sistema`.

## A. Parâmetros legais do crédito

| Parâmetro | O que é | Valores, padrão e sem valor | Quem altera e fundamento |
|---------------|----------------------------|----------------------------|----------------------------|
| `credito_auto_parametros_legais` | **Parâmetros legais do crédito presumido automotivo** (catálogo central). O catálogo legal dos percentuais por faixa de fruição, dos fatores do IPI, da data de referência da alíquota de IPI e do mínimo de pesquisa e desenvolvimento. Aparece na tela de parâmetros da escrituração em leitura; o contador valida as linhas. | Valores: Uma linha por valor e por vigência (22 linhas na carga). Padrão: Sem padrão: sem linha para o ano e a faixa, o Motor não calcula e avisa. Sem valor: Sem linha para a competência o crédito não nasce; o ERP avisa. Em 2033 em diante não há linha porque o crédito está extinto. | contador. LC 214, arts. 309 a 315; Decreto 12.955, arts. 518 a 527 |
| `credito_auto_tipo_parametro` | **Tipo do parâmetro legal** (`Cad_Credito_Automotivo_Parametro.Tipo_Parametro`). Diz o que a linha do catálogo é: percentual por faixa (Lei 9.440), fator multiplicador do IPI (Lei 9.826), data de referência da alíquota de IPI ou mínimo de pesquisa e desenvolvimento. | Valores: percentual_faixa_fruicao, fator_multiplicador_ipi, data_referencia_aliquota_ipi, pdi_minimo_sobre_credito. Padrão: Sem padrão: campo obrigatório. Sem valor: A carga recusa a linha. | contador. LC 214, arts. 309 a 315; Decreto 12.955, arts. 518 a 527 |
| `credito_auto_percentual_faixa` | **Percentual por faixa de fruição (Lei 9.440)** (`Cad_Credito_Automotivo_Parametro.Valor_Percentual`). O percentual aplicado sobre as vendas no mercado interno, por ano e por faixa do mês de fruição: 11,60%, 10% e 8,70% em 2027 e 2028, reduzidos em 20% do inicial por ano de 2029 a 2032. | Valores: 2027-2028: 11,60 / 10 / 8,70; 2029: 9,28 / 8 / 6,96; 2030: 6,96 / 6 / 5,22; 2031: 4,64 / 4 / 3,48; 2032: 2,32 / 2 / 1,74. Padrão: Sem padrão: valor legal. Sem valor: Sem linha, não calcula. | contador. LC 214, art. 311 e § 3º; Decreto 12.955, art. 521 |
| `credito_auto_faixa_mes_fruicao` | **Faixa do mês de fruição** (`Cad_Credito_Automotivo_Parametro.Mes_Fruicao_Inicial`). O intervalo de meses de fruição de cada percentual: do 1º ao 12º, do 13º ao 48º e do 49º ao 60º. | Valores: 1 a 12, 13 a 48, 49 a 60. Padrão: Sem padrão: valor legal. Sem valor: Mês de fruição fora das três faixas (acima de 60): o Motor não acha linha, o crédito é zero e há aviso. | contador. LC 214, art. 311, I a III; Decreto 12.955, art. 521, I a V |
| `credito_auto_fator_multiplicador` | **Fator multiplicador da fórmula do IPI (Lei 9.826)** (`Cad_Credito_Automotivo_Parametro.Valor_Percentual`). O fator F que multiplica `V × Al × (1 − Al)`: 32% em 2027 e 2028, 25,60% em 2029, 19,20% em 2030, 12,80% em 2031 e 6,40% em 2032. | Valores: 32 (2027-2028), 25,60, 19,20, 12,80, 6,40. Padrão: Sem padrão: valor legal. Sem valor: Sem linha para o ano, o crédito é zero e há aviso. De 2033 em diante o benefício está extinto (F = 0). | contador. LC 214, art. 312, IV; Decreto 12.955, art. 522 |
| `credito_auto_data_referencia_ipi` | **Data de referência da alíquota de IPI** (`Cad_Credito_Automotivo_Parametro.Data_Referencia`). A data em que vale a alíquota de IPI da Tipi usada em Al: 31/12/2025. | Valores: 2025-12-31. Padrão: Sem padrão: valor legal. Sem valor: Sem linha, o Motor usa a alíquota informada no produto do projeto; sem as duas, avisa e não calcula. | contador. LC 214, art. 312, II; Decreto 12.955, art. 522 |
| `credito_auto_pdi_minimo` | **Mínimo de pesquisa e desenvolvimento sobre o crédito** (`Cad_Credito_Automotivo_Parametro.Valor_Percentual`). O percentual mínimo do crédito apurado que o projeto deve investir em pesquisa, desenvolvimento e inovação na região: 10%. | Valores: 10. Padrão: Sem padrão: valor legal. Sem valor: Sem linha, o ERP não calcula o mínimo e não avisa. | contador. LC 214, art. 309, § 3º, I; Decreto 12.955, art. 518, § 3º, II, e |

## B. Chaves de decisão

| Parâmetro | O que é | Valores, padrão e sem valor | Quem altera e fundamento |
|-----------------|----------------------------|----------------------------|----------------------------|
| `credito_auto_lei_origem` | **Lei do projeto habilitado** (`Cad_Habilitacao_Automotiva.Lei_Origem`). A lei de origem do projeto decide qual das duas fórmulas vale: percentual sobre as vendas ou fórmula do IPI. | Valores: lei_9440_art_11c, lei_9826_arts_1_a_4. Padrão: Sem padrão: campo obrigatório. Sem valor: A habilitação não é gravada sem a lei. | usuario_do_contrato. LC 214, arts. 309 a 315; Decreto 12.955, arts. 518 a 527 |
| `credito_auto_condicao_projeto` | **Condição do projeto** (`Cad_Habilitacao_Automotiva.Condicao_Projeto`). Projeto aprovado até 31/12/2024 de pessoa jurídica habilitada em 20/12/2023, ou novo projeto aprovado até 31/12/2025 em planta já habilitada. Só quem está numa das duas condições tem o crédito. | Valores: projeto_aprovado_ate_2024, novo_projeto_aprovado_ate_2025. Padrão: Sem padrão: campo obrigatório. Sem valor: A habilitação não é gravada sem a condição. | usuario_do_contrato. LC 214, art. 309, § 1º, II; Decreto 12.955, art. 518, § 1º, II |
| `credito_auto_abrange_veiculo_eletrico` | **Projeto de veículo elétrico** (`Cad_Habilitacao_Automotiva.Abrange_Veiculo_Eletrico`). O projeto produz veículos com motor elétrico capaz de tracionar o veículo só com energia elétrica, com ou sem motor a combustão a biocombustível. | Valores: verdadeiro, falso. Padrão: falso. Sem valor: Sem nenhuma das três marcas o ERP avisa que a habilitação não diz o que o projeto produz. | usuario_do_contrato. LC 214, art. 309, § 1º, I; Decreto 12.955, art. 518, §§ 1º, I, e 2º, I |
| `credito_auto_abrange_combustao` | **Projeto de veículo a combustão com biocombustível** (`Cad_Habilitacao_Automotiva.Abrange_Veiculo_Combustao_Biocombustivel`). O projeto produz veículos tracionados por motor a combustão que usa biocombustíveis, isolados ou com derivados de petróleo. Só vale para projeto aprovado até 31/12/2024 de pessoa jurídica habilitada em 20/12/2023. | Valores: verdadeiro, falso. Padrão: falso. Sem valor: Sem a marca, os produtos desse tipo não entram na base. | usuario_do_contrato. LC 214, art. 309, § 2º; Decreto 12.955, art. 518, § 2º, II |
| `credito_auto_abrange_partes_pecas` | **Projeto de partes, peças e pneumáticos** (`Cad_Habilitacao_Automotiva.Abrange_Partes_Pecas_Pneumaticos`). O projeto produz partes, peças, componentes, conjuntos e subconjuntos, acabados e semiacabados, e pneumáticos usados nos veículos elétricos. Está no Decreto e não achei no texto do art. 309 da LC 214 (C253). | Valores: verdadeiro, falso. Padrão: falso. Sem valor: Sem a marca, esses produtos não entram na base. | usuario_do_contrato. Decreto 12.955, art. 518, § 2º, III |
| `credito_auto_data_inicio_fruicao` | **Início da fruição do benefício** (`Cad_Habilitacao_Automotiva.Data_Inicio_Fruicao`). O primeiro mês de fruição do benefício, de onde o Motor conta o mês de fruição para escolher a faixa do percentual. | Valores: Uma data. Padrão: Sem padrão: campo obrigatório na Lei 9.440. Sem valor: Sem a data o Motor não calcula o mês de fruição e avisa; o usuário pode informar o mês na apuração. | usuario_do_contrato. LC 214, art. 311, I a III; Decreto 12.955, art. 521 |
| `credito_auto_periodo_credito` | **Período do crédito fixado no ato concessório** (`Cad_Habilitacao_Automotiva.Periodo_Credito_Inicio`). O período do crédito que o ato concessório fixa. É o período sobre o qual a devolução do art. 526 é calculada. | Valores: Duas competências. Padrão: Sem padrão: campo obrigatório. Sem valor: Sem o período o ERP não monta a devolução e avisa. | usuario_do_contrato. LC 214, art. 315, § 1º, I; Decreto 12.955, art. 526, § 1º, I |
| `credito_auto_limite_inicio_producao` | **Prazo para iniciar a produção** (`Cad_Habilitacao_Automotiva.Data_Limite_Inicio_Producao`). O prazo para iniciar a produção de veículos no estabelecimento incentivado: 01/01/2028. | Valores: Uma data (01/01/2028 pelo Decreto). Padrão: 2028-01-01. Sem valor: Sem a data efetiva de início depois do prazo, o ERP avisa. | usuario_do_contrato. LC 214, art. 309, § 2º, I; Decreto 12.955, art. 518, § 3º, I |
| `credito_auto_aliquota_ipi_produto` | **Alíquota de IPI de referência do produto** (`Cad_Habilitacao_Automotiva_Produto.Aliquota_Ipi_Referencia`). A alíquota de IPI de 31/12/2025 do produto do projeto, informada para congelar o valor do ato, inclusive com as Notas Complementares da Tipi. | Valores: Um número, ou vazio. Padrão: Vazio: o Motor lê a Tipi na data de referência. Sem valor: Sem valor informado e sem Tipi na data, o crédito da NCM é zero e há aviso. | usuario_do_contrato. LC 214, art. 312, II e III; Decreto 12.955, art. 522 |
| `credito_auto_mes_fruicao_informado` | **Mês de fruição informado** (`Mov_Credito_Automotivo_Apuracao.Mes_Fruicao_Informado`). O mês de fruição que o usuário informa na apuração quando discorda do calculado, por exemplo, quando o ato concessório conta de outra forma. | Valores: Número inteiro, ou vazio. Padrão: Vazio: vale o calculado. Sem valor: Vazio, vale o calculado a partir da data de início da fruição. | usuario_do_contrato. Decreto 12.955, art. 521 |
| `credito_auto_tipo_compromisso` | **Tipo de compromisso do ato concessório** (`Mov_Habilitacao_Automotiva_Compromisso.Tipo_Compromisso`). Qual dos cinco compromissos do ato a linha registra: investimento mínimo, produção mínima, processo produtivo básico, manutenção da produção ou pesquisa, desenvolvimento e inovação. | Valores: investimento_minimo, producao_minima, processo_produtivo_basico, manutencao_producao, pdi_sobre_credito. Padrão: Sem padrão: campo obrigatório. Sem valor: A linha não é gravada sem o tipo. | usuario_do_contrato. LC 214, art. 309, §§ 2º e 3º; Decreto 12.955, art. 518, § 3º, II |
| `credito_auto_situacao_habilitacao` | **Situação da habilitação** (`Cad_Habilitacao_Regime_Especial.Situacao_Habilitacao`). Ativa, suspensa ou cancelada. Já existe no dicionário; o B6 passa a lê-la no uso do crédito. A suspensão por irregularidade fiscal suspende o uso do crédito; sanada a irregularidade, o crédito pretérito volta a poder ser usado. | Valores: ativa, suspensa, cancelada. Padrão: ativa (na habilitação nova). Sem valor: Sem versão na data do uso, o ERP avisa. | usuario_do_contrato. LC 214, art. 314, parágrafo único; Decreto 12.955, arts. 524 e 525 |
| `credito_auto_item_habilitacao` | **Habilitação marcada no item de venda** (`Mov_Nota_Fiscal_Saida_Item.ID_Habilitacao`). Já existe no dicionário. O B6 passa a usá-la como a marca de que o item de venda é produto do projeto: sem a marca, o item não entra na base do crédito. | Valores: Uma habilitação, ou vazio. Padrão: Vazio: o item não entra. Sem valor: Item vendido sem a habilitação e com a NCM do projeto gera aviso. | usuario_do_contrato. Decreto 12.955, art. 521 |
| `credito_auto_aliquota_ipi_tipi` | **Alíquota de IPI da Tipi por NCM** (`Cad_Classificacao_Mercadoria.Aliquota_Ipi`). Já existe no dicionário, com vigência. O B6 lê a versão vigente em 31/12/2025 para a alíquota Al da Lei 9.826. | Valores: Um número por NCM e vigência. Padrão: Sem padrão. Sem valor: Sem versão na data de referência e sem alíquota no produto do projeto, o crédito da NCM é zero e há aviso. | carga_do_sistema. LC 214, art. 312, II; Decreto 12.955, art. 522 |

## C. Leituras provisórias

| Parâmetro | O que é | Valores, padrão e sem valor | Quem altera e fundamento |
|-----------------|----------------------------|----------------------------|---------------------------|
| `credito_auto_contagem_mes_fruicao` | **Contagem do mês de fruição** (catálogo central). Escolhe de onde se conta o mês de fruição: do início da fruição do benefício, que vem do ato (padrão provisório), ou de janeiro de 2027, quando o crédito da CBS começa. Muda o percentual aplicado; aguarda a C248. | Valores: desde_inicio_fruicao (padrão provisório), desde_2027. Padrão: desde_inicio_fruicao. Sem valor: Sem valor, vale o padrão provisório e o ERP avisa a cada apuração. | contador. LC 214, art. 311, I a III; Decreto 12.955, art. 521 |
| `credito_auto_ipi_fora_da_base` | **IPI fora da base do crédito** (catálogo central). Verdadeiro: o IPI da operação sai da base, como os demais tributos. Falso (padrão provisório): só saem os seis tributos que o Decreto lista, e o IPI fica na base. A LC 214 diz "impostos e contribuições incidentes", o Decreto lista seis sem o IPI; aguarda a C249. | Valores: verdadeiro, falso. Padrão: falso. Sem valor: Sem valor, vale o padrão provisório (IPI na base) e o ERP avisa quando o item tem IPI destacado. | contador. LC 214, art. 311, § 1º; Decreto 12.955, art. 521, § 1º, I |
| `credito_auto_tributos_debito_proprio` | **Tributos que compõem os débitos próprios** (catálogo central). A lista de tributos federais que somam os débitos do mês sobre os quais a fração do art. 523, § 2º, é aplicada (padrão provisório: os tributos federais que o ERP apura no mês, com os acréscimos legais). Muda o limite mensal de uso; aguarda a C250. | Valores: Uma lista de `Cad_Imposto`. Padrão: Todos os tributos federais apurados no mês. Sem valor: Sem valor, vale o padrão provisório e o ERP avisa. | contador. LC 214, art. 313, § 2º; Decreto 12.955, art. 523, § 2º |
| `credito_auto_limite_acumula` | **Limite mensal acumula sobre meses sem uso** (catálogo central). Verdadeiro: o limite não usado de um mês soma ao do mês seguinte. Falso (padrão provisório): cada mês tem o seu limite, e o que não foi usado não acumula. O texto não diz; aguarda a C250. | Valores: verdadeiro, falso. Padrão: falso. Sem valor: Sem valor, vale o padrão provisório e o ERP avisa quando o uso passa do limite do mês. | contador. Decreto 12.955, art. 523, § 2º |


# Anexo B. Os 34 efeitos por obrigação

Todos na obrigação **`ESCRITURACAO_IBS_CBS`**. O **local** é de dois tipos, porque o leiaute oficial não existe: (a) **apuração do crédito presumido** da escrituração, com conferência na aba de créditos do espelho da Plataforma (`Mov_Cbs_Apuracao_Espelho_Conta`); (b) **uso do crédito**, na compensação com débitos de CBS (`Mov_Credito_Fiscal_Aplicacao`, forma `compensacao_cbs`) e na declaração de compensação com débitos federais. Tipos de efeito: `calcula_valor`, `seleciona_regra`, `condiciona_credito`, `veda_credito`, `define_fonte_do_dado`, `define_vigencia` e `gera_aviso`.

| Parâmetro | Quando o valor é | Tipo | Local | O que muda |
|--------------------|----------------------------|-----------|--------|---------------------------------|
| `credito_auto_parametros_legais` | qualquer valor | calcula_valor | (a) apuração | Fornece o percentual ou o fator usado na conta do crédito do mês; sem a linha, o crédito do mês é zero e há aviso. |
| `credito_auto_tipo_parametro` | percentual_faixa_fruicao | seleciona_regra | (a) apuração | O Motor busca a linha do tipo certo para a fórmula da habilitação: percentual por faixa na Lei 9.440, fator na Lei 9.826. |
| `credito_auto_tipo_parametro` | fator_multiplicador_ipi | seleciona_regra | (a) apuração | Fator F do ano da competência, na fórmula `V × Al × (1 − Al) × F`. |
| `credito_auto_tipo_parametro` | data_referencia_aliquota_ipi | define_vigencia | (a) apuração | Data em que a alíquota de IPI de cada posição da Tipi é lida (31/12/2025). |
| `credito_auto_tipo_parametro` | pdi_minimo_sobre_credito | gera_aviso | (a) apuração | Base do aviso de pesquisa e desenvolvimento abaixo de 10% do crédito apurado. |
| `credito_auto_percentual_faixa` | qualquer valor | calcula_valor | (a) apuração | Crédito = base de vendas × percentual da faixa do mês de fruição, no ano da competência. |
| `credito_auto_faixa_mes_fruicao` | qualquer valor | seleciona_regra | (a) apuração | Escolhe a linha do percentual pelo mês de fruição calculado ou informado. |
| `credito_auto_faixa_mes_fruicao` | mes_fruicao > 60 | veda_credito | (a) apuração | Depois do 60º mês de fruição não há percentual e o crédito do mês é zero (leitura minha, C248). |
| `credito_auto_fator_multiplicador` | qualquer valor | calcula_valor | (a) apuração | Crédito da NCM = base × Al × (1 − Al) × F do ano. |
| `credito_auto_data_referencia_ipi` | qualquer valor | define_vigencia | (a) apuração | Escolhe a versão de `Cad_Classificacao_Mercadoria.Aliquota_Ipi` vigente na data, para a alíquota Al de cada NCM. |
| `credito_auto_pdi_minimo` | qualquer valor | gera_aviso | (a) apuração | Quando o realizado do compromisso `pdi_sobre_credito` é menor que 10% do crédito apurado, avisa; o benefício fica condicionado ao investimento. |
| `credito_auto_lei_origem` | lei_9440_art_11c | seleciona_regra | (a) apuração | Aplica o percentual por faixa sobre a base de vendas (Lei 9.440, art. 11-C). |
| `credito_auto_lei_origem` | lei_9826_arts_1_a_4 | seleciona_regra | (a) apuração | Aplica `V × Al × (1 − Al) × F` por NCM (Lei 9.826). |
| `credito_auto_condicao_projeto` | qualquer valor | condiciona_credito | (a) apuração | O crédito só nasce para projeto numa das duas condições; data de aprovação fora do limite (2024 ou 2025) gera aviso. |
| `credito_auto_abrange_veiculo_eletrico` | qualquer valor | condiciona_credito | (a) apuração | Marca o escopo do projeto; os produtos fora do escopo não entram na base (aviso). |
| `credito_auto_abrange_combustao` | qualquer valor | condiciona_credito | (a) apuração | Inclui os veículos a combustão a biocombustível no escopo; exige que a condição do projeto seja `projeto_aprovado_ate_2024` (aviso se não for). |
| `credito_auto_abrange_partes_pecas` | qualquer valor | condiciona_credito | (a) apuração | Inclui as partes, peças e pneumáticos no escopo e na base; aviso permanente enquanto a C253 não for respondida. |
| `credito_auto_data_inicio_fruicao` | qualquer valor | seleciona_regra | (a) apuração | Mês de fruição = meses entre esta data e a competência, mais um; escolhe a faixa de 1 a 12, 13 a 48 ou 49 a 60. |
| `credito_auto_periodo_credito` | qualquer valor | calcula_valor | (a) apuração | Define a soma dos créditos apurados que entra na base da devolução em caso de cancelamento da habilitação. |
| `credito_auto_limite_inicio_producao` | qualquer valor | gera_aviso | (a) apuração | Aviso quando passa de 01/01/2028 sem `Data_Inicio_Producao_Veiculos`; o ERP não suspende o crédito sozinho (a suspensão e o cancelamento são do ato). |
| `credito_auto_aliquota_ipi_produto` | qualquer valor | calcula_valor | (a) apuração | Al da fórmula `V × Al × (1 − Al) × F`; se informada, vale no lugar da lida na Tipi (aviso de origem). |
| `credito_auto_mes_fruicao_informado` | qualquer valor | seleciona_regra | (a) apuração | Quando preenchido, escolhe a faixa por este número e o Motor avisa que usou o informado. |
| `credito_auto_tipo_compromisso` | qualquer valor | gera_aviso | (a) apuração | Compromisso descumprido ou abaixo do mínimo gera aviso na apuração do crédito e alimenta F1, F2 e F3 da devolução. |
| `credito_auto_tipo_compromisso` | investimento_minimo, producao_minima, manutencao_producao | calcula_valor | (a) apuração | Os tipos `investimento_minimo`, `producao_minima` e `manutencao_producao` alimentam F1, F2 e F3 da devolução. |
| `credito_auto_situacao_habilitacao` | suspensa | veda_credito | (b) uso | Habilitação suspensa na data do uso: o ERP avisa que o uso está suspenso e não deixa apropriar a compensação sem confirmação. |
| `credito_auto_situacao_habilitacao` | ativa | condiciona_credito | (b) uso | Sanada a suspensão, o crédito pretérito pode ser usado, e o aviso some. |
| `credito_auto_situacao_habilitacao` | cancelada | veda_credito | (a) apuração | Habilitação cancelada: o crédito do mês não nasce (a devolução do art. 526 é registrada). |
| `credito_auto_item_habilitacao` | qualquer valor | seleciona_regra | (a) apuração | Junta o item à base de vendas do projeto na competência. |
| `credito_auto_aliquota_ipi_tipi` | qualquer valor | calcula_valor | (a) apuração | Fornece Al quando o produto do projeto não traz a alíquota informada. |
| `credito_auto_contagem_mes_fruicao` | desde_inicio_fruicao | seleciona_regra | (a) apuração | Conta o mês de fruição desde a data de início da fruição da habilitação. |
| `credito_auto_contagem_mes_fruicao` | desde_2027 | seleciona_regra | (a) apuração | Conta o mês de fruição desde janeiro de 2027: a faixa de 11,60% (ou 10%, ou 8,70%) recomeça no primeiro mês da CBS. |
| `credito_auto_ipi_fora_da_base` | verdadeiro | calcula_valor | (a) apuração | Verdadeiro: o IPI destacado sai da base; falso: fica na base e a base é maior. |
| `credito_auto_tributos_debito_proprio` | qualquer valor | calcula_valor | (b) uso | Soma dos débitos do mês que entra no limite (débitos × fração). |
| `credito_auto_limite_acumula` | falso | condiciona_credito | (b) uso | Falso: o uso do mês não passa do limite do mês. Verdadeiro: o limite não usado acumula. |

# Anexo C. Carga de `Cad_Credito_Automotivo_Parametro` (22 linhas)

Todas com `Situacao_Dado = provisorio`, vigência do ano de cada valor e `Origem_Regra = lei`. **Conferência:** os 15 percentuais foram comparados por programa com o texto do art. 521 do Decreto, e os cinco fatores com o do art. 522; a matriz de 2029 a 2032 é igual a "percentual inicial × (1 − 20% × anos depois de 2028)", como manda o art. 311, § 3º, da LC 214.

| Código | Tipo | Lei do projeto | Mês de fruição | Valor (%) ou data | Vigência |
|--------------------|---------------------|---------------|------------|--------------|------------------|
| `auto_pct_faixa_1_2027_2028` | percentual_faixa_fruicao | lei_9440_art_11c | 1 a 12 | 11,60 | 01/01/2027 a 31/12/2028 |
| `auto_pct_faixa_2_2027_2028` | percentual_faixa_fruicao | lei_9440_art_11c | 13 a 48 | 10,00 | 01/01/2027 a 31/12/2028 |
| `auto_pct_faixa_3_2027_2028` | percentual_faixa_fruicao | lei_9440_art_11c | 49 a 60 | 8,70 | 01/01/2027 a 31/12/2028 |
| `auto_pct_faixa_1_2029` | percentual_faixa_fruicao | lei_9440_art_11c | 1 a 12 | 9,28 | 01/01/2029 a 31/12/2029 |
| `auto_pct_faixa_2_2029` | percentual_faixa_fruicao | lei_9440_art_11c | 13 a 48 | 8,00 | 01/01/2029 a 31/12/2029 |
| `auto_pct_faixa_3_2029` | percentual_faixa_fruicao | lei_9440_art_11c | 49 a 60 | 6,96 | 01/01/2029 a 31/12/2029 |
| `auto_pct_faixa_1_2030` | percentual_faixa_fruicao | lei_9440_art_11c | 1 a 12 | 6,96 | 01/01/2030 a 31/12/2030 |
| `auto_pct_faixa_2_2030` | percentual_faixa_fruicao | lei_9440_art_11c | 13 a 48 | 6,00 | 01/01/2030 a 31/12/2030 |
| `auto_pct_faixa_3_2030` | percentual_faixa_fruicao | lei_9440_art_11c | 49 a 60 | 5,22 | 01/01/2030 a 31/12/2030 |
| `auto_pct_faixa_1_2031` | percentual_faixa_fruicao | lei_9440_art_11c | 1 a 12 | 4,64 | 01/01/2031 a 31/12/2031 |
| `auto_pct_faixa_2_2031` | percentual_faixa_fruicao | lei_9440_art_11c | 13 a 48 | 4,00 | 01/01/2031 a 31/12/2031 |
| `auto_pct_faixa_3_2031` | percentual_faixa_fruicao | lei_9440_art_11c | 49 a 60 | 3,48 | 01/01/2031 a 31/12/2031 |
| `auto_pct_faixa_1_2032` | percentual_faixa_fruicao | lei_9440_art_11c | 1 a 12 | 2,32 | 01/01/2032 a 31/12/2032 |
| `auto_pct_faixa_2_2032` | percentual_faixa_fruicao | lei_9440_art_11c | 13 a 48 | 2,00 | 01/01/2032 a 31/12/2032 |
| `auto_pct_faixa_3_2032` | percentual_faixa_fruicao | lei_9440_art_11c | 49 a 60 | 1,74 | 01/01/2032 a 31/12/2032 |
| `auto_fator_ipi_2027_2028` | fator_multiplicador_ipi | lei_9826_arts_1_a_4 |  | 32,00 | 01/01/2027 a 31/12/2028 |
| `auto_fator_ipi_2029` | fator_multiplicador_ipi | lei_9826_arts_1_a_4 |  | 25,60 | 01/01/2029 a 31/12/2029 |
| `auto_fator_ipi_2030` | fator_multiplicador_ipi | lei_9826_arts_1_a_4 |  | 19,20 | 01/01/2030 a 31/12/2030 |
| `auto_fator_ipi_2031` | fator_multiplicador_ipi | lei_9826_arts_1_a_4 |  | 12,80 | 01/01/2031 a 31/12/2031 |
| `auto_fator_ipi_2032` | fator_multiplicador_ipi | lei_9826_arts_1_a_4 |  | 6,40 | 01/01/2032 a 31/12/2032 |
| `auto_data_referencia_ipi` | data_referencia_aliquota_ipi | lei_9826_arts_1_a_4 |  | 2025-12-31 | 01/01/2027 a 31/12/2032 |
| `auto_pdi_minimo` | pdi_minimo_sobre_credito | ambas |  | 10,00 | 01/01/2027 a 31/12/2032 |

# Anexo D. Arquivos de carga (pasta `Carga202`)

| Arquivo | Linhas | Conteúdo |
|----------------------------------------|-------|-----------------------------------------------------|
| `Cad_Credito_Automotivo_Parametro.csv` | 22 | Os percentuais por faixa, os fatores do IPI, a data de referência e o mínimo de pesquisa e desenvolvimento (Anexo C) |
| `Cad_Parametro_Documentacao_linhas_B6.csv` | 25 | A documentação dos 25 parâmetros (Anexo A), para `Cad_Parametro_Documentacao` do documento 201 |
| `Cad_Parametro_Efeito_Obrigacao_linhas_B6.csv` | 34 | Os 34 efeitos (Anexo B), para `Cad_Parametro_Efeito_Obrigacao` do documento 201 |
| `Cad_Obrigacao_Parametro_Definicao_linhas_novas.csv` | 5 | Uma linha para o catálogo legal (em leitura) e quatro para as leituras provisórias, em `ESCRITURACAO_IBS_CBS` |
| `Cad_Classe_Sistema_valores_novos.csv` | 1 | O valor `regime_automotivo` em `tipo_regime_especial_federal` |

As duas cargas de documentação dependem da estrutura do documento 201 (aprovada na D-N536) e só podem ser carregadas depois dela.

# Anexo E. Perguntas ao contador (C248 a C255, documento 188, Parte 11)

Oito perguntas novas; o documento 188 passa a ter **255**. Cada uma traz o fundamento, o que o ERP faz hoje e o que muda com a resposta.

**C248 · LC 214, art. 311, I a III, e Decreto 12.955, art. 521 · Crédito presumido automotivo: de quando se conta o mês de fruição**

*Documento 202, seção 4.4 (Q202-5)*

O percentual do crédito da Lei 9.440, art. 11-C, cai por faixa do "mês de fruição do benefício": 11,60% até o 12º mês, 10% do 13º ao 48º e 8,70% do 49º ao 60º em 2027 e 2028 (e, reduzidos em 20% do inicial por ano, de 2029 a 2032). O texto não diz se o mês é contado desde o início da fruição do benefício original, que pode ter começado antes de 2027, ou se recomeça em janeiro de 2027, com a CBS.

Pergunta: (a) o mês de fruição conta do início da fruição do benefício (data do ato concessório ou do primeiro mês de uso), ou de 01/2027? (b) depois do 60º mês de fruição não há crédito, ou vale a última faixa? (c) quem fixa o mês de fruição: o ato concessório, o MDIC ou a RFB? (d) para o projeto novo (aprovado até 31/12/2025), o mês 1 é o primeiro mês em que o crédito foi apurado?

**O que o ERP faz:** Proposta do documento 202 (Q202-5): parâmetro por empresa `credito_auto_contagem_mes_fruicao`, padrão provisório "desde o início da fruição"; o usuário pode informar o mês na apuração; depois do 60º mês o crédito do mês é zero, com aviso. Nada aplicado ao dicionário.

**C249 · LC 214, art. 311, § 1º, e Decreto 12.955, art. 521, § 1º, I · Crédito presumido automotivo: o IPI fica na base ou sai?**

*Documento 202, seção 4.5 (Q202-5)*

A LC 214 manda não incluir na base do crédito "os impostos e as contribuições incidentes sobre a operação de venda". O Decreto lista seis tributos (ICMS, ICMS substituição, ISS, CBS, IBS e Imposto Seletivo) e não cita o IPI.

Pergunta: (a) o IPI destacado na venda sai da base do crédito, como "imposto incidente", ou fica, como o Decreto sugere? (b) para o projeto da Lei 9.826 a resposta é a mesma? (c) outras parcelas da nota (frete, seguro, outras despesas acessórias) entram na base?

**O que o ERP faz:** Proposta do documento 202 (Q202-5): parâmetro por empresa `credito_auto_ipi_fora_da_base`, padrão provisório falso (o IPI fica na base, como o Decreto), com aviso quando o item tem IPI destacado; nada aplicado ao dicionário.

**C250 · LC 214, art. 313, § 2º, e Decreto 12.955, art. 523, §§ 2º e 3º · Crédito presumido automotivo: débitos próprios, fração e limite mensal**

*Documento 202, seção 4.6 (Q202-5 e Q202-6)*

O crédito só abate os "débitos próprios" do estabelecimento habilitado: os débitos da pessoa jurídica em impostos e contribuições federais e acréscimos legais do mês, multiplicados pela razão entre as vendas de veículos do habilitado e as de todos os estabelecimentos nos três meses anteriores ao fato gerador.

Pergunta: (a) quais tributos entram nos débitos do mês: CBS, IRPJ, CSLL, IPI, contribuições previdenciárias, retenções? (b) os três meses são os três imediatamente anteriores ao mês do fato gerador? (c) o limite não usado num mês acumula para o seguinte? (d) a fração se aplica ao uso na compensação com a própria CBS, ou só à compensação com os demais tributos? (e) o limite vale por estabelecimento habilitado ou por pessoa jurídica?

**O que o ERP faz:** Proposta do documento 202 (Q202-5 e Q202-6): parâmetros por empresa `credito_auto_tributos_debito_proprio` (padrão provisório: todos os tributos federais que o ERP apura) e `credito_auto_limite_acumula` (padrão provisório falso), limite por habilitação; aviso quando o uso passa do limite; nada aplicado ao dicionário.

**C251 · LC 214, arts. 309 a 315 · Crédito presumido automotivo: tratamento contábil e efeito na ECD, na ECF e nas obrigações de compensação**

*Documento 202, seção 4.11 (Q202-9)*

O documento 202 documenta o efeito de cada parâmetro do crédito na escrituração do IBS e da CBS, onde o crédito é apurado. Para a ECD, a ECF e as obrigações que informam as compensações com débitos federais não encontrei norma.

Pergunta: (a) o crédito presumido da CBS é registrado como redução de tributo, receita ou subvenção, e entra na base do IRPJ e da CSLL? (b) há conta do plano referencial da ECD ou código da ECF para ele? (c) a compensação com débitos federais aparece na DCTFWeb ou só no PER/DCOMP? (d) o crédito presumido compõe o mesmo registro da escrituração que os créditos comuns ou tem registro próprio?

**O que o ERP faz:** Proposta do documento 202 (Q202-9): nenhum efeito é documentado na ECD, na ECF, na DCTFWeb e nas demais obrigações até a sua resposta; o crédito segue como Mov_Credito_Fiscal, sem lançamento contábil novo; nada aplicado ao dicionário.

**C252 · LC 214, art. 312, II e III, e Decreto 12.955, art. 522 · Crédito presumido automotivo (Lei 9.826): a alíquota de IPI de 31/12/2025 e as Notas Complementares**

*Documento 202, seção 4.7 (Q202-4)*

A fórmula da Lei 9.826 usa a alíquota de IPI de 31/12/2025, "conforme a Tipi, inclusive Notas Complementares", nas posições 8702 a 8704, "para cada posição na Tipi". O ERP lê a alíquota de `Cad_Classificacao_Mercadoria` na versão dessa data e deixa o produto do projeto trazer a alíquota informada.

Pergunta: (a) a alíquota é por NCM de oito dígitos ou por posição de quatro, quando os itens da posição têm alíquotas diferentes? (b) a Nota Complementar que reduz ou zera a alíquota de certo produto vale para o Al, e como identificar o produto (ex-tarifário)? (c) a alíquota congela em 31/12/2025 mesmo que a Tipi mude depois? (d) a lista de produtos de cada projeto vem do ato concessório?

**O que o ERP faz:** Proposta do documento 202 (Q202-4): o Motor lê a Tipi na data de referência; o produto do projeto pode trazer a alíquota informada, que vale no lugar e fica gravada com a origem; sem nenhuma das duas, o crédito da NCM é zero e há aviso; nada aplicado ao dicionário.

**C253 · Decreto 12.955, art. 518, § 2º, III · Crédito presumido automotivo: partes, peças, componentes e pneumáticos**

*Documento 202, seção 4.9 (Q202-11)*

O Decreto inclui no projeto "partes, peças, componentes, conjuntos e subconjuntos, acabados e semiacabados, e pneumáticos" usados nos veículos elétricos. Esta alínea não está no texto do art. 309, § 2º, da LC 214 que li.

Pergunta: (a) o crédito alcança esses produtos? (b) como se calcula: pelo percentual da Lei 9.440 ou pela fórmula da Lei 9.826, conforme a lei do projeto? (c) as vendas desses produtos entram na fração do art. 523 (vendas de veículos)? (d) a base inclui as vendas a outros fabricantes de veículos?

**O que o ERP faz:** Proposta do documento 202 (Q202-11): a marca `Abrange_Partes_Pecas_Pneumaticos` na habilitação; os produtos entram na base pela lei do projeto, com aviso permanente até a sua resposta; nada aplicado ao dicionário.

**C254 · Decreto 12.955, art. 523, §§ 2º e 3º · Crédito presumido automotivo: o que é "venda de veículos" na fração dos débitos próprios**

*Documento 202, seção 4.6 (Q202-6)*

A fração do limite de uso é a razão entre "o valor total da venda dos veículos produzidos no estabelecimento habilitado" e "o valor total da venda de veículos de todos os estabelecimentos da pessoa jurídica", pelas notas fiscais eletrônicas, sem canceladas, devolvidas, tributos e descontos incondicionais.

Pergunta: (a) "veículos" são só as posições 8702 a 8704, ou todo o capítulo 87 (motocicletas, reboques, chassis, partes)? (b) vendas de veículos usados e revendidos entram no denominador? (c) vendas para a Zona Franca e para exportação entram? (d) a nota de venda sem a marca da habilitação, mas de veículo produzido no estabelecimento, entra no numerador?

**O que o ERP faz:** Proposta do documento 202 (Q202-6): numerador e denominador pelos itens de saída com a NCM das posições 8702 a 8704 (leitura minha), guardados como valores na linha do limite; nada aplicado ao dicionário.

**C255 · LC 214, art. 315, e Decreto 12.955, arts. 526 e 527 · Crédito presumido automotivo: devolução na hipótese de cancelamento**

*Documento 202, seção 5.6 (Q202-8)*

No cancelamento da habilitação, o crédito apurado no período do ato volta, multiplicado por 100% menos F1 × F2 × F3. O MDIC apura o valor; há juros de mora e recolhimento até o último dia útil do mês seguinte ao cancelamento.

Pergunta: (a) o crédito já compensado e o ainda não usado têm o mesmo tratamento (o que não foi usado é baixado, o usado é recolhido)? (b) os juros de mora seguem a Selic acumulada desde o mês do fato do cancelamento, e o ERP deve calcular ou só registrar o informado? (c) F3, quando o benefício ainda não acabou, usa o prazo já realizado até a data do cancelamento? (d) qual a contabilização do título da devolução: despesa, redução do crédito ou outra?

**O que o ERP faz:** Proposta do documento 202 (Q202-8): o ERP guarda o valor apurado pelo MDIC, calcula F1, F2 e F3 só como conferência, não calcula os juros de mora e gera o título a pagar pelo valor informado; nada aplicado ao dicionário.

