# Desenho dos combustíveis: catálogo, alíquota específica por unidade e regime monofásico da CBS — Documento 170

*Responde à Q140-7 (`Cad_Aliquota_Combustivel`: "Desenhar", 04/11/2026) e à Q150-11 (combustíveis é desenho próprio). Parte dos textos que você reenviou (LC 214 com a LC 227 e Decreto 12.955, Q161-4) e da pesquisa de hoje sobre a alíquota de 2027. **Nada entra no dicionário agora**: tudo entra no seu próximo "consolidar", junto com os documentos 157 e 150, que você aprovou com "Sim" em todas as perguntas.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

Os combustíveis têm regime próprio na LC 214 (arts. 172 a 180) e no Decreto 12.955 (arts. 259 a 268 e 471 a 478): a CBS incide **uma única vez**, sobre a **quantidade** (litro, quilograma ou metro cúbico), por **alíquota específica em reais por unidade**, e quem compra para revender não toma crédito. Antes de desenhar, conferi o que o dicionário já tem. **Tem mais do que parecia**: o item da apuração já guarda `Forma_Tributacao = especifica_por_unidade`, `Quantidade_Tributada` e `Valor_Especifico_Unidade`; a nota de saída já leva os campos de combustível do leiaute; o `Cad_Cclasstrib` já tem os indicadores dos grupos monofásicos; `Credito_Vedado_Adquirente` já existe. Falta o que a lei trata como parâmetro: **o catálogo dos combustíveis, a tabela de alíquotas por unidade, o vínculo com os códigos da ANP e da NCM, a autorização da ANP e o limite do crédito**.

O desenho acrescenta **4 entidades novas (60 campos)**, altera **2 existentes** (3 campos novos e 3 valores novos em uma enumeração) e cria 2 grupos de valores de domínio (seção 10). As três tabelas de parâmetro ficam nos Motores Transversais (ao lado de `Cad_Aliquota` e `Cad_Produto_Anp`) e a autorização do participante, na Contabilidade & Fiscal.

| Peça | O que a lei diz | O que o dicionário já tinha | O que este documento acrescenta |
|---|---|---|---|
| **Catálogo** (LC, art. 172; Decreto, art. 259) | 12 incisos; IX a XI adiados para 01/01/2033 | Só `Cad_Produto_Anp` (código da ANP) | `Cad_Combustivel_Regime` e o vínculo com ANP e NCM (`Cad_Combustivel_Produto_Vinculo`) |
| **Alíquota** (LC, arts. 174 e 175; Decreto, arts. 471 a 478) | Específica por unidade, uniforme, divulgada por ato, majoração só depois de 90 dias | `Cad_Aliquota` (só percentual) | `Cad_Aliquota_Combustivel` com a carga provisória da Portaria MF nº 3.074/2026 |
| **Apuração** (LC, art. 173; Decreto, art. 260) | Base = quantidade a 20 °C × alíquota | Item com forma de tributação específica, quantidade e valor por unidade | Três tipos de complemento para os grupos monofásicos do leiaute e o limite do crédito (art. 267, § 4º) |
| **Quem participa** (LC, arts. 176 e 180; Decreto, arts. 263 e 268) | Contribuintes por tipo de agente; inscrição exige autorização da ANP | `Cad_Participante_Qualificacao_Cbs` | `Cad_Participante_Autorizacao_Anp` e o domínio `agente_cadeia_combustiveis` |

**Seis achados que você precisa ler.**

1. **A alíquota de 2027 já saiu.** A Portaria MF nº 3.074, de 09/10/2026, fixou a CBS por unidade para oito combustíveis, com efeito a partir do 91º dia da publicação (**08/01/2027**), e o Decreto 13.133, da mesma data, mudou os arts. 471 e 476 e revogou o 477. **Só li notícias e quadros de sites; o texto da portaria eu não li.** A carga sai provisória e pergunto na Q170-9 se você manda o texto.
2. **Há uma janela sem alíquota: 01/01/2027 a 07/01/2027.** A LC exige 90 dias entre a publicação e a majoração (art. 174, II). O ERP não deixa valor escondido: nesses sete dias a consulta não acha linha e o ERP avisa. O que vale na janela é decisão do contador (Q170-C1).
3. **O gás natural processado, o biometano e o GNV só entram em 01/01/2033.** Quem adia é o Decreto (art. 259, § 4º); a LC (art. 172, § 3º) só autoriza adiar por ato conjunto do CGIBS e do Poder Executivo. Marquei `Origem_Regra = decreto` na carga e pergunto ao contador se o decreto basta (Q170-C2).
4. **O leiaute da nota já tem os grupos monofásicos** (gMonoPadrao, gMonoReten e gMonoRet no TMonofasia do XSD da NT 2026.004). Os valores são quantidade, alíquota por unidade e valor do tributo: cabem no complemento da apuração que já existe, com **três valores novos em `Tipo_Complemento` e dois campos**. Nenhuma tabela nova por grupo.
5. **Não dá para conferir a faixa de 40% a 90% dos biocombustíveis só com os números da portaria.** A razão bruta da CBS é 24,25% (EAC sobre gasolina) e 42,11% (B100 sobre diesel); a lei manda considerar a equivalência energética (art. 175, § 2º, I), cujo fator não li em lugar nenhum. Criei o campo do fator, vazio, e a conferência só roda quando ele existir.
6. **O texto de `Quantidade` e de `Valor_Especifico_Unidade` do complemento diz "diferido" (qBCMonoDif e adRemICMSDif).** Ao reaproveitar os campos para os grupos monofásicos, o texto precisa dizer isso; entra em "Textos que a consolidação corrige" (seção 11).

# 2. Regras que segui

Valem as dos documentos 156, 157 e 150 (parâmetro com vigência e fim em 31/12/9999; sem valor padrão escondido; carga provisória com `Situacao_Dado = provisorio` até o contador validar; o ERP avisa e nunca bloqueia; "O ERP só registra"; nomes em português com sublinhado). Mais estas:

1. **Cito sempre "LC, art. X" e "Decreto, art. Y".** A numeração do Decreto não é a da LC: LC, arts. 172 a 180 = Decreto, arts. 259 a 268; LC, arts. 174 e 175 = Decreto, arts. 471 a 478.
2. **Só desenho o que o cliente usa ou o que a nota já exige** (D-N68). A ponta do produtor (retenção do EAC na gasolina A e mistura a mais ou a menos) fica em **esboço** na seção 9, sem entidade, até você dizer que há cliente (Q170-8).
3. **O que o leiaute já leva não vira campo novo.** Os grupos monofásicos reaproveitam o complemento (seção 7).
4. **Valor derivado não se guarda.** Os totais do item (vTotIBSMonoItem, vTotCBSMonoItem) são soma; o ERP não os guarda. Guardo só o limite do crédito (`Valor_Limite_Credito`), porque a tabela de alíquotas pode ser corrigida depois e a conta precisa dar o mesmo resultado.
5. **A alíquota percentual e a específica não se misturam.** `Cad_Aliquota` continua só com percentual; a específica por unidade vive em `Cad_Aliquota_Combustivel`.
6. **Uma leitura minha é sempre dita como minha** e vai ao contador.

# 3. O que os textos pedem

**Incidência.** A CBS incide uma única vez, qualquer que seja a finalidade, sobre 12 incisos (Decreto, art. 259): gasolina e correntes, EAC, óleo diesel e correntes, B100, GLP (inclusive GLGN), EHC, QAV, óleo combustível, gás natural processado, biometano, GNV e "outros combustíveis especificados e autorizados pela ANP", que o ato conjunto relacionar (inciso XII). A incidência é no fornecimento pelos contribuintes do art. 263 ou na importação (§ 1º). O § 4º posterga para 01/01/2033 os incisos IX, X e XI.

**Base.** A quantidade de combustível na unidade própria (Decreto, art. 260, §§ 1º e 3º): litro para gasolina, EAC, diesel, B100, EHC e QAV; quilograma para GLP e óleo combustível; metro cúbico para gás natural processado, biometano e GNV. O líquido por volume é convertido a **20 °C** (§ 2º). O ato do inciso XII especifica a unidade de cada combustível que relacionar (§ 4º). A nota sai com a unidade da seção (art. 261, § 2º) e o cálculo considera os códigos da **ANP e da NCM/SH** (art. 261, § 1º).

**Alíquota.** Uniforme no País, específica por unidade, diferenciada por produto (LC, art. 174, I); reajustada no ano anterior ao da vigência, com anterioridade nonagesimal para a majoração (II); divulgada pelo Ministro da Fazenda quanto à CBS (Decreto, art. 471, III, com a redação do Decreto 13.133) e pelo Comitê Gestor quanto ao IBS. A CBS de 2027 não pode passar da carga dos tributos federais extintos, calculada pelas regras do art. 474 do Decreto (LC, art. 174, §§ 1º e 2º); o IBS entra só em 2029, em degraus de 10%, 20%, 30%, 40% e 100% da carga (§ 4º). Os biocombustíveis têm alíquota **entre 40% e 90%** da do fóssil comparado (LC, art. 175, § 1º; Decreto, art. 476), os pares do art. 472, parágrafo único: gasolina com EAC, gasolina C com EHC e diesel com B100. O EHC tem ainda um diferencial mínimo (LC, art. 175, §§ 3º a 5º; Decreto, art. 478), e o Executivo pode reduzir a do B100 feito com matéria-prima da agricultura familiar (§ 6º).

**Sujeição passiva.** São contribuintes o produtor nacional de biocombustíveis, a refinaria e suas bases, a CPQ, a UPGN, o formulador, o importador (inclusive o distribuidor quando importa) e o agente produtor autorizado pela ANP e pelo CGIBS (Decreto, art. 263; LC, art. 176). O adquirente é solidariamente responsável, salvo se a liquidação tiver split payment (art. 264, § 1º, I).

**Crédito.** Fica vedado nas aquisições para distribuição, comercialização ou revenda (art. 267). O contribuinte do regime regular aproveita o crédito nos demais casos, e o exportador o mantém (§§ 1º e 2º). Os documentos fiscais da cadeia trazem a CBS recolhida antecipadamente, em reais por unidade (§ 3º), e o crédito fica **limitado à quantidade vezes a alíquota vigente na data da incidência monofásica** (§ 4º).

**Cadastro.** Todos os participantes da cadeia se inscrevem no cadastro único, e a inscrição exige **autorização da ANP** (art. 268, § 1º); a inscrição pode ser suspensa por ato conjunto da RFB e do CGIBS (§ 2º).

# 4. O que o dicionário já tem e o que falta

| Peça | O que faz | O que falta |
|---|---|---|
| `Cad_Produto_Anp` | O código COD_COMB da ANP, com vigência | Ligar o código ao combustível do regime |
| `Cad_Produto_Servico_Dados_Produto.ID_Produto_Anp` | O produto aponta para a ANP | Nada; o vínculo parte daqui |
| `Mov_Nota_Fiscal_Saida_Item` (`Combustivel_Codigo_Anp`, `Combustivel_Quantidade_Temperatura_Ambiente` e os demais campos `Combustivel_*`) | O que a nota exige do item de combustível | Nada |
| `Mov_Apuracao_Tributo_Item` | `Forma_Tributacao` com `especifica_por_unidade`, `Quantidade_Tributada`, `Valor_Especifico_Unidade`, `Credito_Vedado_Adquirente`, `Gera_Credito` | De onde veio a alíquota específica (auditoria) |
| `Mov_Apuracao_Tributo_Item_Complemento` | 16 tipos de complemento da nota (diferimento, transferência de crédito, ajustes e outros) | Os três grupos monofásicos; o limite do crédito |
| `Cad_Cst.Indicador_Tributacao_Monofasica` e `Cad_Cclasstrib.Indicador_Mono_Padrao`, `_Reten`, `_Ret` e `_Dif` | Quais grupos o código de tributação exige | Nada |
| `Cad_Participante_Qualificacao_Cbs` | A qualificação do participante perante a CBS (30 tipos, `Numero_Comprovante`, `Data_Validade`) | Número e situação da autorização da ANP e vários tipos de agente por participante |
| `Cad_Motor_Regra` e filhos | Escolhem o cClassTrib por critérios | Três critérios novos (seção 10) |
| `Cad_Aliquota` | Percentual com vigência por tributo e ente | Nada: a específica não cabe aqui |

# 5. Catálogo: `Cad_Combustivel_Regime`

O catálogo é a lista do art. 259, com a unidade da base, o início do regime e, nos biocombustíveis, o fóssil comparado e a faixa. Uma linha por combustível, com vigência: o ato do inciso XII entra por cadastro, sem mexer no código. A carga tem 11 linhas (incisos I a XI; Anexo A.1).

Por que o fóssil comparado é campo e não regra no código: o par vem do art. 472, parágrafo único, I, e muda se o ato mudar. A gasolina é uma linha só (inciso I, "gasolina e suas correntes"); o Decreto compara o EAC com a gasolina A e o EHC com a gasolina C, e essa distinção vive no produto e na nota, não no catálogo (Q170-C3).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Regime` | identificador | --- |
| `ID_Combustivel_Regime_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Regime_Versao). ID_Combustivel_Regime é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `Codigo` | código (até 30) --- identidade | Por exemplo `GASOLINA`, `OLEO_DIESEL`, `EAC`, `EHC`, `B100`, `GLP`, `QAV`, `OLEO_COMBUSTIVEL`, `GAS_NATURAL_PROCESSADO`, `BIOMETANO`, `GNV`. |
| `Descricao` | texto | O nome do combustível como o art. 259 o escreve. |
| `Inciso_Art_259` | código (até 4) | O inciso do art. 259 do Decreto (I a XII); o mesmo do art. 172 da LC. |
| `ID_Unidade_Medida` | referência (Cad_Unidade_Medida) | A unidade da base de cálculo: litro, quilograma ou metro cúbico (Decreto, art. 260, § 3º). O documento fiscal sai com ela (art. 261, § 2º). |
| `Origem_Combustivel` | enumeração {fossil, biocombustivel} | Decide se a faixa de 40% a 90% se aplica. |
| `ID_Combustivel_Fossil_Comparado` | referência (Cad_Combustivel_Regime), opcional | Só no biocombustível: o fóssil com que se compara (EAC com a gasolina, EHC com a gasolina e B100 com o diesel; Decreto, art. 472, parágrafo único, I). |
| `Percentual_Minimo_Sobre_Fossil` | número, opcional | 40 nos biocombustíveis (LC, art. 175, § 1º; Decreto, art. 476). |
| `Percentual_Maximo_Sobre_Fossil` | número, opcional | 90 nos biocombustíveis. |
| `Fator_Equivalencia_Energetica` | número, opcional | O fator de equivalência energética contra o fóssil comparado (LC, art. 175, § 2º, I). Vazio até o ato dizer qual; sem ele o ERP não confere a faixa (Q170-C2). |
| `Inicio_Regime` | data | Quando o regime específico passa a valer para o combustível: 01/01/2027 nos oito primeiros e 01/01/2033 no gás natural processado, no biometano e no GNV (Decreto, art. 259, § 4º). |
| `Origem_Regra` | enumeração {lei, decreto, ato_conjunto} | `decreto` no início de 2033 (a LC, art. 172, § 3º, só permite adiar por ato conjunto do CGIBS e do Poder Executivo). |
| `Fundamento_Legal` | texto | LC, art. 172 e Decreto, art. 259. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

# 6. Vínculo com a ANP e a NCM: `Cad_Combustivel_Produto_Vinculo`

O Decreto manda considerar "os códigos da ANP e da NCM/SH" no cálculo (art. 261, § 1º). O ERP descobre o combustível do item por esta ordem: (1) o `Combustivel_Codigo_Anp` da nota, que leva a `Cad_Produto_Anp`; (2) o `ID_Produto_Anp` do cadastro do produto; (3) a NCM do produto, de qualquer nível, valendo para os descendentes. O vínculo guarda **um dos dois** (ANP ou NCM) por linha, com vigência. A carga fica **vazia**: depende da tabela da ANP carregada e da conferência do contador (Q170-C4). Sem vínculo, o item de combustível cai no regime geral com aviso, como em D-N427.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Combustivel_Produto_Vinculo` | identificador | --- |
| `ID_Combustivel_Produto_Vinculo_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Combustivel_Produto_Vinculo_Versao). ID_Combustivel_Produto_Vinculo é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Combustivel_Regime` | referência (Cad_Combustivel_Regime) --- identidade | O combustível do regime. |
| `ID_Produto_Anp` | referência (Cad_Produto_Anp), opcional --- identidade | O produto da ANP (COD_COMB). Pelo menos um entre este e a NCM. |
| `ID_Classificacao_Mercadoria` | referência (Cad_Classificacao_Mercadoria), opcional --- identidade | A NCM, de qualquer nível (vale para os descendentes). |
| `Observacao` | texto, opcional | --- |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

# 7. Alíquota específica: `Cad_Aliquota_Combustivel`

A tabela guarda a alíquota **em reais por unidade**, por combustível, tributo e ente, com vigência. O que separa esta tabela de `Cad_Aliquota`: a unidade (a do combustível, não percentual), a divulgação por ato (`Ato_Divulgacao` e `Data_Publicacao`) e a ressalva do que a portaria deixa de fora (GLP de uso doméstico até 13 kg; B100 de agricultura familiar, LC, art. 175, § 6º). **O que fica de fora não tem alíquota aqui**: quem decide é o Motor pelo cClassTrib, e o ERP não inventa um valor (Q170-C5).

**Avisos, nunca bloqueios.** (1) Se `Vigencia_Inicio` fica antes do 91º dia da `Data_Publicacao`, o ERP avisa que a majoração não pode ter efeito ainda (LC, art. 174, II). (2) Se o item é de combustível e a consulta não acha linha vigente na data da operação, o ERP avisa e o item fica com `Status = pendente_decisao`. (3) Para o biocombustível, se houver `Fator_Equivalencia_Energetica`, o ERP compara a alíquota com a do fóssil comparado e avisa quando sai da faixa; sem o fator, não compara.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Aliquota_Combustivel` | identificador | --- |
| `ID_Aliquota_Combustivel_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Aliquota_Combustivel_Versao). ID_Aliquota_Combustivel é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Combustivel_Regime` | referência (Cad_Combustivel_Regime) --- identidade | O combustível. |
| `ID_Imposto` | referência (Cad_Imposto) --- identidade | CBS ou IBS. |
| `Ente_Competente` | enumeração {uniao, estado, municipio} --- identidade | `uniao` na CBS; no IBS, as partes estadual e municipal, distribuídas pelas alíquotas de referência (LC, art. 174, § 10). |
| `Valor_Aliquota_Por_Unidade` | número | Reais por unidade de medida do combustível, com quatro casas (a mesma precisão do `adRem` do leiaute). |
| `ID_Natureza_Aliquota` | referência (Cad_Classe_Sistema, domínio = natureza_aliquota) | Efetiva ou de teste, como em `Cad_Aliquota`. |
| `Ressalva_Aplicacao` | enumeração {nenhuma, exceto_glp_uso_domestico_ate_13kg, exceto_biodiesel_agricultura_familiar} | O que a portaria deixa de fora da alíquota da linha. O que fica de fora não tem alíquota aqui: o Motor decide pelo cClassTrib (Q170-C3). |
| `Ato_Divulgacao` | texto | O ato que divulga a alíquota, por exemplo "Portaria MF nº 3.074, de 09/10/2026". |
| `Data_Publicacao` | data | A publicação do ato. A majoração só vale depois da anterioridade nonagesimal (LC, art. 174, II): se `Vigencia_Inicio` fica antes do 91º dia da publicação, o ERP avisa; não bloqueia. |
| `Origem_Valor` | enumeração {ato_ministro, ato_cgibs, calculo_provisorio} | Quem fixou o valor. `calculo_provisorio` é para a linha que o usuário preenche antes do ato. |
| `Fundamento_Legal` | texto | LC, arts. 174 e 175; Decreto, arts. 471 a 478. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador (área validacao_dado_legal). |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

**Exemplo calculado** (alíquotas provisórias da Portaria MF nº 3.074/2026; as quantidades são minhas):

| Operação | Quantidade | Alíquota por unidade | CBS |
|---|---|---|---|
| Gasolina | 10.000 l | 0,7925 | 7.925,00 |
| Óleo diesel | 20.000 l | 0,3515 | 7.030,00 |
| GLP | 5.000 kg | 0,1677 | 838,50 |
| Óleo combustível | 3.000 kg | 0,3403 | 1.020,90 |
| **Total** | | | **16.814,40** |

**A janela de 01/01 a 07/01/2027.** Publicação em 09/10/2026 mais 90 dias é 07/01/2027, e o efeito começa no 91º dia, 08/01/2027. Uma linha com `Vigencia_Inicio` em 01/01/2027 dispara o aviso do item (1); com 08/01/2027, não. Nos sete dias de 01/01 a 07/01 a consulta não acha linha e o item fica pendente (Q170-C1).

**Faixa dos biocombustíveis.** Com os valores da portaria, EAC sobre gasolina dá 0,1922 ÷ 0,7925 = 24,25% e B100 sobre diesel dá 0,1480 ÷ 0,3515 = 42,11%. A razão bruta do EAC fica abaixo de 40%, mas a lei manda comparar com a equivalência energética (LC, art. 175, § 2º, I): **a razão bruta não prova que a alíquota está fora da faixa**, e o ERP não conclui nada sem o fator (Q170-C6).

# 8. Apuração monofásica no complemento

O leiaute da nota tem três grupos que importam ao ERP: **gMonoPadrao** (a tributação monofásica própria do emitente), **gMonoReten** (a retenção do tributo de um terceiro, como o EAC misturado na gasolina A) e **gMonoRet** (o tributo recolhido anteriormente, que o adquirente lê na nota de entrada). Cada um traz quantidade, alíquota por unidade e valor do IBS ou da CBS. O dicionário já tem o complemento com o mesmo desenho (`Quantidade`, `Valor_Especifico_Unidade`, `Valor`), usado pelo diferimento. **O desenho reaproveita:** uma linha de complemento por item e tributo, com o tipo dizendo o grupo.

**`Mov_Apuracao_Tributo_Item_Complemento`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| Valor novo em `Tipo_Complemento` | `monofasia_padrao`, `monofasia_retencao` e `monofasia_retida_anteriormente` | Os grupos gMonoPadrao, gMonoReten e gMonoRet do leiaute. Cada linha de apuração (item e tributo) tem o seu: `Quantidade` guarda o qBCMono, `Valor_Especifico_Unidade` guarda o adRem e `Valor` guarda o valor do IBS ou da CBS monofásica. Nenhum campo novo para isso. O diferimento (gMonoDif) já tem o tipo `diferimento`. |
| `Data_Incidencia_Monofasica` | data, opcional | Só em `monofasia_retida_anteriormente`: o dia em que o fornecedor da cadeia recolheu a CBS. É com a alíquota desta data que se mede o limite do crédito (Decreto, art. 267, § 4º). Provisório (Q170-C4). |
| `Valor_Limite_Credito` | número, opcional | Só em `monofasia_retida_anteriormente`: a quantidade vezes a alíquota específica vigente em `Data_Incidencia_Monofasica`. Guardado porque a tabela de alíquotas pode ser corrigida depois. O crédito não passa dele; passando, o ERP avisa. |

**`Mov_Apuracao_Tributo_Item`**

| Campo ou valor | Tipo | Descrição |
|---|---|---|
| `ID_Aliquota_Combustivel` | referência (Cad_Aliquota_Combustivel), opcional | Só na tributação monofásica: a linha e a versão da alíquota específica aplicada, para a auditoria. A `Aliquota_Nominal` do item continua sendo a percentual; no regime monofásico vale `Valor_Especifico_Unidade`. |

| Grupo do leiaute | `Tipo_Complemento` | `Quantidade` | `Valor_Especifico_Unidade` | `Valor` |
|---|---|---|---|---|
| gMonoPadrao | `monofasia_padrao` | qBCMono | adRemIBS ou adRemCBS | vIBSMono ou vCBSMono |
| gMonoReten | `monofasia_retencao` | qBCMonoReten | adRemIBSReten ou adRemCBSReten | vIBSMonoReten ou vCBSMonoReten |
| gMonoRet | `monofasia_retida_anteriormente` | qBCMonoRet | adRemIBSRet ou adRemCBSRet | vIBSMonoRet ou vCBSMonoRet |

**A conta do crédito (Decreto, art. 267, § 4º).** O adquirente do regime regular que usa o combustível (por exemplo, uma transportadora com diesel para a frota) lê na nota o gMonoRet. O crédito é o valor da nota, **limitado à quantidade vezes a alíquota vigente na data da incidência**. O ERP calcula o limite com a linha de `Cad_Aliquota_Combustivel` vigente em `Data_Incidencia_Monofasica`, guarda o resultado em `Valor_Limite_Credito` e avisa se o valor da nota o excede.

*Exemplo calculado:* 5.000 l de diesel; a nota traz CBS recolhida de 1.800,00; a alíquota vigente na incidência era 0,3515. Limite = 5.000 × 0,3515 = **1.757,50**; o crédito é 1.757,50 e o ERP avisa que a nota excede o limite em 42,50. Se a tabela for corrigida depois (por exemplo, para 0,3600 hipotético), o limite guardado continua 1.757,50, porque a data da incidência não mudou; a nova alíquota entra por versão e vale só para as operações seguintes.

**Quem não toma crédito.** O distribuidor, o posto e o revendedor (art. 267, *caput*) ficam com `Credito_Vedado_Adquirente` e `Gera_Credito = falso`. O Motor decide pelo cClassTrib e pelo agente do destinatário (critério `agente_cadeia_do_destinatario`, seção 10); não há campo novo. O exportador mantém o crédito (§ 2º); não verifiquei se o dicionário já o cobre (Q170-E4).

# 9. Autorização da ANP: `Cad_Participante_Autorizacao_Anp`

A inscrição no cadastro único da cadeia exige autorização da ANP (Decreto, art. 268, § 1º), e o tipo de agente decide se o participante é contribuinte do regime (art. 263) ou comprador que não toma crédito (art. 267). O dicionário já tem `Cad_Participante_Qualificacao_Cbs`, mas ele guarda **uma qualificação** com comprovante e validade, e o agente da cadeia de combustíveis tem mais de um tipo por participante (o importador que também distribui), número da autorização, validade e **situação** (suspensa por ato conjunto, art. 268, § 2º). Por isso a entidade é própria; o domínio é `agente_cadeia_combustiveis` (11 valores, Anexo A.3).

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Participante_Autorizacao_Anp` | identificador | --- |
| `ID_Participante_Autorizacao_Anp_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Participante_Autorizacao_Anp_Versao). ID_Participante_Autorizacao_Anp é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Participante` | referência (Cad_Participante) --- identidade | Quem tem a autorização. |
| `ID_Tipo_Agente` | referência (Cad_Classe_Sistema, domínio = agente_cadeia_combustiveis) --- identidade | O tipo de agente (domínio aberto, seção 7.2). |
| `Numero_Autorizacao` | código (até 30) | O número da autorização na ANP. |
| `Data_Autorizacao` | data, opcional | Quando a ANP autorizou. |
| `Data_Validade` | data, opcional | O fim da validade, quando a autorização vence. |
| `Situacao` | enumeração {ativa, suspensa, cancelada} | `suspensa` quando o ato conjunto da RFB e do CGIBS suspende a inscrição (art. 268, § 2º, que depende de ato ainda sem texto). |
| `Motivo_Situacao` | texto, opcional | Por que está suspensa ou cancelada. |
| `ID_Documento_Comprovante` | referência (Cad_Documento), opcional | O arquivo da autorização. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (convenção da Fase 0, seção 2). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

**O tipo de agente não decide o regime sozinho.** O Motor lê o tipo (critérios `agente_cadeia_do_emitente` e `agente_cadeia_do_destinatario`) junto com o combustível do item (`combustivel_do_item`). O ERP só registra a autorização; a decisão de quem é contribuinte continua do Motor, com regras de cadastro do contador.

**Esboço da ponta do produtor (não entra no consolidar).** A LC e o Decreto têm duas obrigações que só existem para quem produz ou mistura: (1) a refinaria, a CPQ, o formulador e o importador retêm a CBS do EAC na saída da gasolina A pela fórmula VRBM = [QTDA ÷ (1 − IM)] × IM × ALIQ (Decreto, art. 265, § 1º); (2) a distribuidora que mistura EAC a mais recolhe sobre o excesso e a que mistura a menos tem direito a ressarcimento (art. 266). Com o índice de mistura hipotético de 30% (o índice real é do órgão regulamentador), 10.000 l de gasolina A dão uma gasolina C de 14.285,71 l, um EAC de 4.285,71 l e um VRBM de 823,71 (= 4.285,71 × 0,1922). O que um desenho precisaria guardar: a nota da gasolina A, QTDA, IM, ALIQ do EAC, VRBM e o excesso ou a falta de mistura. **Não desenhei**: D-N68 manda entidade só quando há cliente (Q170-8).

# 10. Motor de Regras e domínios

O Motor decide o cClassTrib dos combustíveis; este documento pede **três critérios novos** e um domínio novo, e nenhum código de classificação tributária.

| Valor novo em `campo_criterio_regra` | O que lê |
|---|---|
| `combustivel_do_item` | O combustível do regime a que o item pertence, pelo vínculo da seção 6 (ou nenhum). |
| `agente_cadeia_do_emitente` | O tipo de agente em `Cad_Participante_Autorizacao_Anp` vigente do emitente na data da operação. |
| `agente_cadeia_do_destinatario` | O mesmo, do destinatário (para a revenda sem crédito, art. 267). |

**Domínio novo em `Cad_Classe_Sistema`:** `agente_cadeia_combustiveis` (11 valores: `produtor_biocombustiveis`, `refinaria`, `cpq`, `upgn`, `formulador`, `importador`, `distribuidor`, `transportador_revendedor_retalhista`, `posto_revendedor`, `comercializador_etanol` e `outro_produtor_autorizado`). De `produtor_biocombustiveis` a `importador` vêm do art. 263, I a VI; `distribuidor`, do § 1º do mesmo artigo; `outro_produtor_autorizado`, do inciso VII; e `transportador_revendedor_retalhista`, `posto_revendedor` e `comercializador_etanol`, do art. 268, § 2º, II.

# 11. O que entra no próximo "consolidar"

**4 entidades novas (60 campos).**

| Entidade | Tipo | Campos | Vigência | Módulo | Capítulo |
|---|---|---|---|---|---|
| `Cad_Combustivel_Regime` | catálogo (11 linhas) | 19 | sim | Motores Transversais | 5 |
| `Cad_Combustivel_Produto_Vinculo` | vínculo (carga vazia) | 11 | sim | Motores Transversais | 6 |
| `Cad_Aliquota_Combustivel` | parâmetro (8 linhas provisórias) | 17 | sim | Motores Transversais | 7 |
| `Cad_Participante_Autorizacao_Anp` | cadastro do participante (carga vazia) | 13 | sim | Contabilidade & Fiscal | 9 |

**2 entidades alteradas** (3 campos novos e 3 valores novos em uma enumeração).

| Entidade | O que muda |
|---|---|
| `Mov_Apuracao_Tributo_Item_Complemento` | `Tipo_Complemento` + `monofasia_padrao`, `monofasia_retencao`, `monofasia_retida_anteriormente`; `Data_Incidencia_Monofasica`; `Valor_Limite_Credito` |
| `Mov_Apuracao_Tributo_Item` | `ID_Aliquota_Combustivel` |

**Domínios e valores novos.**

| Onde | O que entra |
|---|---|
| `Cad_Classe_Sistema.Dominio` | `agente_cadeia_combustiveis` (11 valores) |
| `campo_criterio_regra` | 3 valores: `combustivel_do_item`, `agente_cadeia_do_emitente`, `agente_cadeia_do_destinatario` |

**Cargas provisórias** (todas com `Situacao_Dado = provisorio` até o contador validar; Anexo A):

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Combustivel_Regime` | 11 | Incisos I a XI; IX a XI com início em 01/01/2033 e `Origem_Regra = decreto` |
| `Cad_Aliquota_Combustivel` | 8 | CBS da Portaria MF nº 3.074/2026, vigência 08/01/2027, **fonte secundária** (texto não lido); nenhuma linha de IBS |
| `Cad_Combustivel_Produto_Vinculo` | 0 | Depende da tabela da ANP e do contador |
| `Cad_Participante_Autorizacao_Anp` | 0 | Cadastro do usuário, por participante |
| `Cad_Classe_Sistema` | 14 | 11 agentes e 3 critérios do Motor |

**Textos que a consolidação corrige.** Em `Mov_Apuracao_Tributo_Item_Complemento`: `Quantidade` passa a dizer "quantidade tributada diferida (qBCMonoDif) **ou** a base monofásica (qBCMono, qBCMonoReten, qBCMonoRet)"; `Valor_Especifico_Unidade` passa a dizer "alíquota ad rem do imposto diferido (adRemICMSDif) **ou** a alíquota específica da CBS ou do IBS monofásico (adRemCBS, adRemIBS e variantes)"; `Valor` passa a incluir "vIBSMono e vCBSMono". **Nada deste documento mexe** nos regimes de B5 (documento 150), no TEF nem na apuração do Simples.


# 12. Perguntas

## 12.1 Para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q170-1** | Catálogo `Cad_Combustivel_Regime` com 11 linhas de carga (incisos I a XI), o XII por cadastro, e o início de 01/01/2033 nos incisos IX a XI com `Origem_Regra = decreto`? | Sim |
| **Q170-2** | `Cad_Combustivel_Produto_Vinculo` (combustível ligado à ANP ou à NCM, com vigência), com a carga **vazia** até a tabela da ANP e o contador? | Sim |
| **Q170-3** | `Cad_Aliquota_Combustivel` com a alíquota específica por unidade, por combustível, tributo e ente, e os avisos da seção 7 (noventena, janela sem linha, faixa dos biocombustíveis)? | Sim |
| **Q170-4** | Carga provisória de 8 linhas de CBS da Portaria MF nº 3.074/2026 (vigência 08/01/2027, fonte secundária) e nenhuma linha de IBS? | Sim |
| **Q170-5** | Monofasia no complemento da apuração: três tipos novos de `Tipo_Complemento`, `Data_Incidencia_Monofasica`, `Valor_Limite_Credito` e `ID_Aliquota_Combustivel` no item, sem tabela por grupo? | Sim |
| **Q170-6** | `Cad_Participante_Autorizacao_Anp` com o domínio `agente_cadeia_combustiveis` (11 valores), carga vazia? | Sim |
| **Q170-7** | Motor: os três critérios novos (`combustivel_do_item`, `agente_cadeia_do_emitente`, `agente_cadeia_do_destinatario`) e nenhum código de classificação tributária criado neste documento? | Sim |
| **Q170-8** | A ponta do produtor (retenção do EAC na gasolina A e mistura a mais ou a menos, Decreto, arts. 265 e 266) fica só em esboço, **sem entidade**, até haver cliente refinaria, formulador, importador ou distribuidora? Existe esse cliente hoje? | Sim, só esboço |
| **Q170-9** | Você me envia o texto da Portaria MF nº 3.074/2026 e o da Portaria conjunta MF/CGIBS nº 14/2026 (metodologia), para eu conferir a carga e a faixa dos biocombustíveis? | Sim |
| **Q170-10** | Aplico tudo no próximo "consolidar", junto com os documentos 157 e 150? | Sim |

## 12.2 Para o contador

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q170-C1** | De 01/01/2027 a 07/01/2027, a LC já vale (art. 174, II exige 90 dias só para a **majoração**), mas a portaria só tem efeito no 91º dia. Qual alíquota específica vale nos sete dias? Há norma de transição? | Nenhuma linha; o ERP avisa e o item fica pendente |
| **Q170-C2** | O Decreto, art. 259, § 4º, posterga os incisos IX a XI para 01/01/2033, e a LC, art. 172, § 3º, só autoriza adiar por **ato conjunto do CGIBS e do Poder Executivo**. O decreto basta? | O decreto basta; `Origem_Regra = decreto` |
| **Q170-C3** | O Decreto compara o EAC com a gasolina A e o EHC com a gasolina C (art. 472, parágrafo único, I). Basta uma linha de catálogo para a gasolina, com a distinção na nota e no produto? Qual é o par do biometano? | Uma linha; biometano sem par |
| **Q170-C4** | Os códigos da ANP e da NCM de cada combustível (Decreto, art. 261, § 1º): há tabela de correspondência oficial ou o vínculo é do contador? E o "gasolina e suas correntes" (art. 259, § 2º) inclui quais códigos? | Vínculo vazio |
| **Q170-C5** | Ressalvas da portaria: como se identifica na nota o GLP de uso doméstico até 13 kg e o B100 com matéria-prima da agricultura familiar (LC, art. 175, § 6º)? Pelo cClassTrib ou por outro dado do documento? | Pelo cClassTrib, escolhido pelo Motor |
| **Q170-C6** | Faixa de 40% a 90%: qual é o **fator de equivalência energética** de cada par e quem o publica? O diferencial mínimo do EHC (LC, art. 175, §§ 3º a 5º) é conferido pelo ERP ou só pelo ato? | `Fator_Equivalencia_Energetica` vazio; o ERP não confere |
| **Q170-C7** | Limite do crédito (Decreto, art. 267, § 4º): a **data da incidência monofásica** é a da saída do contribuinte do art. 263 ou a do fato gerador? Como o adquirente a conhece (campo do documento fiscal)? | A data do documento do contribuinte do regime, informada |
| **Q170-C8** | IBS dos combustíveis em 2027 e 2028: o art. 174, § 4º, fixa o IBS só a partir de 2029. Nos dois anos anteriores não há IBS específico? Qual alíquota vale? | Nenhuma linha de IBS |
| **Q170-C9** | Autorização da ANP (Decreto, art. 268, § 1º): basta o número e a validade, ou o ERP precisa conferir a situação na ANP? O que acontece com a nota do participante com autorização suspensa? | Só registro; a suspensão é informada, e o ERP avisa |
| **Q170-C10** | Responsabilidade solidária do adquirente (Decreto, art. 264): o ERP precisa de campo para o caso sem split payment? Quando se aplica o § 1º, III (participante que "concorreu para o não pagamento")? | Fora deste desenho |

## 12.3 Para a equipe

| Nº | Pergunta |
|---|---|
| **Q170-E1** | A conversão do volume a 20 °C (Decreto, art. 260, § 2º) já vem feita do PDV ou do sistema do posto? O item tem `Combustivel_Quantidade_Temperatura_Ambiente`; confirmar que `Quantidade_Tributada` recebe a quantidade já convertida. |
| **Q170-E2** | O cadastro de unidades de medida (`Cad_Unidade_Medida`) tem litro, quilograma e metro cúbico com os símbolos do leiaute? A nota de combustível sai com a unidade da seção (art. 261, § 2º). |
| **Q170-E3** | A tabela da ANP (`Cad_Produto_Anp`) já está carregada com vigência? O vínculo da seção 6 depende dela. |
| **Q170-E4** | O exportador de combustíveis mantém o crédito (Decreto, art. 267, § 2º). Não verifiquei se o dicionário já cobre isso nos documentos de exportação: confirmar. |
| **Q170-E5** | A nota de entrada com gMonoRet chega pelo XML? Confirmar que o ERP lê o grupo e grava uma linha de complemento por item e tributo. |
| **Q170-E6** | Há cliente ou fornecedor que seja refinaria, formulador, importador ou distribuidora com mistura de EAC? Isso responde à Q170-8. |

# 13. Limites

1. **Nada deste documento entra no dicionário agora.** Tudo vai no próximo "consolidar".
2. **A alíquota de 2027 é de fonte secundária.** Li notícias e quadros de sites; o texto da Portaria MF nº 3.074/2026 não foi lido. Os oito valores carregam `Situacao_Dado = provisorio` até o contador validar com o texto.
3. **Não crio código de classificação tributária.** Os cClassTrib da monofasia são cadastro do Motor, validado pelo contador.
4. **A ponta do produtor está em esboço** (retenção do EAC e mistura): sem entidade até haver cliente (Q170-8).
5. **Não desenhei a responsabilidade solidária** (Decreto, art. 264) **nem a suspensão da inscrição por ato conjunto** (art. 268, § 2º): dependem de texto que ainda não existe (Q170-C9 e Q170-C10).
6. **Não conferi a faixa dos biocombustíveis**: o fator de equivalência energética não foi encontrado (Q170-C6). O campo existe, vazio.
7. **As leituras minhas** (a data da incidência, a janela de 01/01 a 07/01/2027, o vínculo por ANP ou NCM) estão marcadas e vão ao contador; nenhuma vira regra no código.

# Anexo A. Carga provisória (todas com `Situacao_Dado = provisorio`)

## A.1 `Cad_Combustivel_Regime`: 11 linhas

| `Codigo` | Inciso | Descrição | Unidade | `Origem_Combustivel` | Fóssil comparado | Faixa (%) | `Inicio_Regime` | `Origem_Regra` |
|---|---|---|---|---|---|---|---|---|
| `GASOLINA` | I | Gasolina e suas correntes | litro | `fossil` | vazio | vazio | 01/01/2027 | `lei` |
| `EAC` | II | Etanol anidro combustível | litro | `biocombustivel` | `GASOLINA` | 40 a 90 | 01/01/2027 | `lei` |
| `OLEO_DIESEL` | III | Óleo diesel e suas correntes | litro | `fossil` | vazio | vazio | 01/01/2027 | `lei` |
| `B100` | IV | Biodiesel | litro | `biocombustivel` | `OLEO_DIESEL` | 40 a 90 | 01/01/2027 | `lei` |
| `GLP` | V | GLP, inclusive o derivado de gás natural (GLGN) | quilograma | `fossil` | vazio | vazio | 01/01/2027 | `lei` |
| `EHC` | VI | Etanol hidratado combustível | litro | `biocombustivel` | `GASOLINA` | 40 a 90 | 01/01/2027 | `lei` |
| `QAV` | VII | Querosene de aviação | litro | `fossil` | vazio | vazio | 01/01/2027 | `lei` |
| `OLEO_COMBUSTIVEL` | VIII | Óleo combustível | quilograma | `fossil` | vazio | vazio | 01/01/2027 | `lei` |
| `GAS_NATURAL_PROCESSADO` | IX | Gás natural processado | metro cúbico | `fossil` | vazio | vazio | 01/01/2033 | `decreto` |
| `BIOMETANO` | X | Biometano | metro cúbico | `biocombustivel` | vazio | vazio | 01/01/2033 | `decreto` |
| `GNV` | XI | Gás natural veicular | metro cúbico | `fossil` | vazio | vazio | 01/01/2033 | `decreto` |

`Fator_Equivalencia_Energetica` vazio nas três linhas de biocombustível (Q170-C6); biometano sem fóssil comparado (Q170-C3); `Situacao_Dado = provisorio`; vigência até 31/12/9999; `Fundamento_Legal` "LC, art. 172; Decreto, art. 259" (e "art. 259, § 4º" nos incisos IX a XI).

## A.2 `Cad_Aliquota_Combustivel`: 8 linhas de CBS

Todas com `ID_Imposto` = CBS, `Ente_Competente` = `uniao`, `ID_Natureza_Aliquota` = efetiva, `Ato_Divulgacao` = "Portaria MF nº 3.074, de 09/10/2026", `Data_Publicacao` = 09/10/2026, `Origem_Valor` = `ato_ministro`, `Vigencia_Inicio` = 08/01/2027, `Vigencia_Fim` = 31/12/9999 e `Fundamento_Legal` = "LC, art. 174; Decreto, art. 471". **Fonte secundária**: o texto da portaria não foi lido.

| Combustível | Unidade | `Valor_Aliquota_Por_Unidade` (R$) | `Ressalva_Aplicacao` |
|---|---|---|---|
| `GASOLINA` | litro | 0,7925 | nenhuma |
| `EAC` | litro | 0,1922 | nenhuma |
| `EHC` | litro | 0,1922 | nenhuma |
| `OLEO_DIESEL` | litro | 0,3515 | nenhuma |
| `B100` | litro | 0,1480 | `exceto_biodiesel_agricultura_familiar` |
| `GLP` | quilograma | 0,1677 | `exceto_glp_uso_domestico_ate_13kg` |
| `QAV` | litro | 0,0712 | nenhuma |
| `OLEO_COMBUSTIVEL` | quilograma | 0,3403 | nenhuma |

Nenhuma linha de gás natural processado, biometano ou GNV (adiados para 2033) nem de IBS (a alíquota é de 2029).

## A.3 `Cad_Classe_Sistema`

`agente_cadeia_combustiveis`: `produtor_biocombustiveis` (Produtor nacional de biocombustíveis), `refinaria` (Refinaria de petróleo ou suas bases), `cpq` (Central de matéria-prima petroquímica), `upgn` (Unidade de processamento de gás natural), `formulador` (Formulador de combustíveis), `importador` (Importador), `distribuidor` (Distribuidor de combustíveis), `transportador_revendedor_retalhista` (Transportador revendedor retalhista), `posto_revendedor` (Posto revendedor varejista), `comercializador_etanol` (Empresa comercializadora de etanol), `outro_produtor_autorizado` (Outro agente produtor autorizado pela ANP e pelo CGIBS). `campo_criterio_regra`: os três da seção 10.

# Anexo B. Cobertura dispositivo por dispositivo

| Dispositivo | Assunto | Onde está |
|---|---|---|
| LC, art. 172 e Decreto, art. 259 | Combustíveis do regime; adiamento de IX a XI | `Cad_Combustivel_Regime` (`Inicio_Regime`, `Origem_Regra`) |
| LC, art. 172, § 3º | Ato conjunto pode adiar | Pergunta ao contador (Q170-C2) |
| Decreto, art. 259, § 2º | Correntes | Vínculo com ANP e NCM; o contador define os códigos (Q170-C4) |
| Decreto, art. 259, § 3º | Suspensão para nafta e petroquímica | Sem campo novo: suspensão via Motor e cClassTrib; ato conjunto sem texto |
| LC, art. 173 e Decreto, art. 260 | Base: quantidade na unidade própria, a 20 °C | `ID_Unidade_Medida` do catálogo; `Quantidade_Tributada` (item); Q170-E1 |
| Decreto, art. 261 | Valor = base × alíquota; códigos ANP e NCM | `Cad_Aliquota_Combustivel`; `Cad_Combustivel_Produto_Vinculo` |
| LC, art. 174 e Decreto, arts. 471, 473 a 475 | Alíquota uniforme, específica, noventena, divulgação | `Cad_Aliquota_Combustivel` (`Ato_Divulgacao`, `Data_Publicacao`, aviso de noventena) |
| LC, art. 175 e Decreto, arts. 472, 476 e 478 | Biocombustíveis: faixa de 40% a 90%; EHC | `Cad_Combustivel_Regime` (par, faixa e fator); conferência só com o fator (Q170-C6) |
| LC, art. 175, § 6º | B100 da agricultura familiar | `Ressalva_Aplicacao`; Q170-C5 |
| LC, art. 176 e Decreto, art. 263 | Contribuintes do regime | `Cad_Participante_Autorizacao_Anp` (tipo de agente) e Motor |
| LC, art. 177 e Decreto, art. 264 | Responsabilidade solidária do adquirente | **Fora** deste desenho (Q170-C10) |
| LC, art. 178 e Decreto, art. 265 | Retenção do EAC na gasolina A | **Esboço** (seção 9), grupo gMonoReten já tem lugar no complemento |
| LC, art. 179 e Decreto, art. 266 | Mistura a mais ou a menos | **Esboço** (seção 9) |
| LC, art. 180 e Decreto, art. 267 | Crédito vedado na revenda; limite do crédito | `Credito_Vedado_Adquirente` (já existe); `Valor_Limite_Credito` e `Data_Incidencia_Monofasica` |
| Decreto, art. 267, § 3º | Documento da cadeia traz a CBS por unidade | `monofasia_retida_anteriormente` no complemento |
| Decreto, art. 268 | Inscrição e autorização da ANP | `Cad_Participante_Autorizacao_Anp` |
| Decreto, art. 268, § 2º | Suspensão da inscrição | `Situacao = suspensa`; ato conjunto sem texto (Q170-C9) |

