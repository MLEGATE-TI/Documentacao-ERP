# Anexo Único da IN RFB 2.345/2026 e Decreto 12.808/2025: Leitura e Cruzamento — Documento 56

*Os materiais que Alberto autorizou baixar ou enviou em 12/10/2026 (o terceiro, a Portaria MF 3.278/2025, está na seção 8): o "Anexo Único.pdf" da IN RFB nº 2.345/2026 (modelos do Comprovante de Inscrição e de Situação Cadastral do CNPJ) e o Decreto nº 12.808/2025 (redução dos incentivos e benefícios federais, regulamenta a LC 224/2025). Traz também uma correção da contagem da revisão 5 (seção 2). Documento de proposta e controle: nada foi alterado no dicionário. O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N132 e D-N133 (situação cadastral do CNPJ e carga do Decreto 12.808/2025), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

**Decreto 12.808/2025.** Li o texto inteiro no Planalto. Ele **confere com o dicionário** (D-N120 e D-N127): os 7 tipos de benefício dos arts. 5º a 12 são as 7 formas de `Cad_Reducao_Beneficio_Federal.Forma_Beneficio`, com os mesmos percentuais (10%, 90%, acréscimo de 10%); as 13 exceções do art. 14 são os 13 valores de `excecao_reducao_lc224`, na mesma ordem; o corte de 31/12/2025 (art. 8º, parágrafo único) e a regra de que suspensão só de diferimento fica fora (art. 13) são os dois pontos que a D-N127 já propõe. O Decreto **libera a carga genérica** (por tributo, regime e forma) que a revisão 4 deixou esperando por ele (D-N133). O que continua faltando é a regra por produto: a Portaria MF 3.278/2025 que o art. 15 manda editar chegou depois (seção 8) e **não traz lista de produtos**; resta o demonstrativo de gastos tributários da LOA 2026, que o art. 2º, § 2º, I, usa para dizer quais benefícios entram, e a orientação da Receita sobre cada benefício.

**Anexo Único da IN 2.345.** O PDF tem 2 páginas, só com as imagens dos dois modelos do Comprovante do CNPJ (Modelo I e Modelo II). O dicionário cobre quase todos os campos, mas **não guarda a situação cadastral do CNPJ** (situação, motivo, situação especial e as respectivas datas), a data de inscrição e a de constituição de quem não é a própria empresa. Proposta **D-N132** (seção 3).

**Correção.** As decisões **D-N106 a D-N117** (documentos 48, 49 e 50), que você respondeu, **ainda não estão no dicionário**: a revisão 4 aplicou só D-N118 a D-N124. Meus documentos 53, 54 e 55 contavam a revisão 5 sem elas (seção 2).

# 2. Correção da contagem da revisão 5

**O que verifiquei.** Procurei no `model.json` da revisão 4 (837 entidades) os campos das decisões D-N106 a D-N117. Não estão lá: `Valor_Cbs` em `Cad_Mei_Parametro`, `Valor_Ibs` em `Mov_Mei_Das`, `Origem_Declaracao` e `Diferenca_Conferencia` em `Mov_Simples_Apuracao`, `Valor_Deduzido_Regime_Regular` em `Mov_Simples_Apuracao_Tributo`, `Valor_Comissao` e `Numero_Contrato_Declarado` em `Mov_Dimob_Operacao`, `Indicador_Matriz` em `Cad_Participante`, `Data_Inicio_Atividade` em `Cad_Empresa`. Os valores de domínio novos (`sublimite_inicio_atividade_mensal`, `informada_receita_anterior_opcao`, `difal_consumidor_final`, `webservice_uf`) também não. O relatório da revisão 4 (documento 52) diz que aplicou "D-N118 a D-N124", o que confere; o erro é meu, nos documentos seguintes.

**O que isso muda.** São só campos e valores, sem entidade nova (pela tabela do documento 45). Então o total de entidades da revisão 5 não muda; o de **entidades alteradas sobe**:

| Parte da revisão 5 | Entidades novas | Entidades alteradas |
|---|---|---|
| Documento 53 (D-N125 a D-N128) | 3 | 6 |
| Documento 54 (D-N129) | 1 | 3 (a `Cad_Classe_Sistema` já está acima) |
| Documento 55 (D-N130 e D-N131) | 1 | 2 |
| Documento 56 (D-N132 e D-N133) | 1 | 0 (a `Cad_Reducao_Beneficio_Federal` já está acima) |
| Decisões D-N106 a D-N117 (documentos 48 a 50) | 0 | no mínimo 9: `Cad_Mei_Parametro`, `Mov_Mei_Das`, `Mov_Simples_Apuracao_Atividade`, `Cad_Simples_Limite`, `Mov_Simples_Apuracao`, `Mov_Simples_Apuracao_Tributo`, `Cad_Empresa`, `Mov_Dimob_Operacao` e `Cad_Participante`; mais as entidades da DeSTDA (D-N113), do regime de caixa (D-N106) e da origem da receita anterior à opção (D-N110), que a tabela não nomeia |
| **Total** | **837 mais 6 = 843** | **no mínimo 20**, a recontar na consolidação |

Corrijo o documento 55 (que dizia "842 e 11 alteradas") e os documentos 45 e 14. O documento 53 e o 54 falam só do que cada um propõe e continuam certos.

# 3. Anexo Único da IN 2.345: o Comprovante do CNPJ

**O que a IN faz.** O art. 1º troca o Anexo III da IN RFB 2.119/2022 pelo Anexo Único, "para adequar o Comprovante de Inscrição e de Situação Cadastral às alterações promovidas no CNPJ" (publicada no DOU de 23/09/2026, em vigor na publicação; base: Portaria MF 220/2026, art. 59 da LC 214/2025 e arts. 104 e 105 do Decreto 12.955/2026). O anexo não traz o texto do Anexo III antigo, então **não consegui dizer o que mudou** em cada campo.

**Como li o arquivo.** O PDF (556 KB, 2 páginas) só tem imagem dos formulários; li pelo navegador do aplicativo, e o arquivo não foi guardado em lugar nenhum (o servidor onde trabalho está bloqueado para o portal da Receita por política da rede).

**Campos dos dois modelos.** Os dois modelos têm os mesmos campos básicos; o Modelo II acrescenta o representante legal e o quadro de sócios e administradores.

| Campo do comprovante | Onde está no dicionário |
|---|---|
| Número de inscrição | `Cad_Participante.Documento_Principal` (CNPJ alfanumérico) |
| Data de inscrição no CNPJ | **Falta** |
| Nome empresarial | `Cad_Participante.Nome_Razao_Social` |
| Data de constituição | **Falta** (só a empresa própria tem `Data_Obito`; nenhuma data de constituição) |
| Título do estabelecimento (nome de fantasia) | `Cad_Participante.Nome_Fantasia` |
| Porte | `Cad_Participante_Porte` (mei, me, epp, demais) |
| Atividade econômica principal e secundárias | `Cad_Filial_Atividade`, só da empresa própria e das filiais; participante de terceiros não tem CNAE |
| Natureza jurídica | `Cad_Empresa.ID_Natureza_Juridica`, só da empresa própria |
| Endereço, CEP, bairro, município, UF | `Cad_Participante_Endereco` |
| Endereço eletrônico e telefone | `Cad_Participante_Email` e `Cad_Participante_Telefone` |
| Ente federativo responsável (EFR) | `Cad_Ente_Federativo_Responsavel` existe, mas só o Reinf e o eSocial o usam; o participante em geral não aponta para ele |
| Situação cadastral, data e motivo | **Falta** |
| Situação especial e data | **Falta** (`Situacao_Especial` existe só em Simples, LCDPR e arquivo de escrituração, com outro sentido) |
| Código QR e código de barras | Não precisa de campo: o retorno completo fica no GED (`Mov_Consulta_Cadastro_Externo.ID_Documento`) |
| Modelo II: representante legal e quadro de sócios | `Cad_Empresa_Socio` cobre só a empresa própria; não proponho nada para terceiros |

**Efeito hoje.** O cadastro automático já grava o retorno completo da Receita (`Mov_Consulta_Cadastro_Externo` e `_Campo`), então nenhum dado se perde. O que falta é guardar a situação como **dado consultável com vigência**, para o ERP avisar quando um fornecedor ou cliente fica suspenso, inapto ou baixado, e saber desde quando.

## D-N132: situação cadastral do CNPJ

Entidade nova **`Cad_Participante_Situacao_Cnpj`**, com vigência:

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Participante_Situacao_Cnpj` e `_Versao` | identificadores | Padrão de vigência da Fase 0, seção 2 |
| `ID_Participante` | referência (Cad_Participante), identidade | Só participante PJ |
| `ID_Situacao_Cadastral` | referência (Cad_Classe_Sistema, domínio = situacao_cadastral_cnpj) | Domínio aberto. O anexo não lista os valores; os iniciais seriam ativa, suspensa, inapta, baixada e nula, **a conferir na página da Receita** |
| `Data_Situacao_Cadastral` | data, opcional | |
| `Motivo_Situacao_Cadastral` | texto, opcional | Como veio da Receita |
| `Situacao_Especial` e `Data_Situacao_Especial` | texto e data, opcionais | |
| `Data_Inscricao_Cnpj` | data, opcional | |
| `Data_Constituicao` | data, opcional | |
| `ID_Ente_Federativo` | referência (Cad_Ente_Federativo_Responsavel), opcional | O EFR |
| `ID_Consulta` | referência (Mov_Consulta_Cadastro_Externo), opcional | A consulta que originou a versão |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | | |

Nenhuma regra de negócio (bloquear compra de fornecedor inapto, por exemplo) entra agora: o dado fica guardado e disponível, e a regra se desenha quando você quiser.

# 4. Decreto 12.808/2025: artigo por artigo

Decreto de 29/12/2025, DOU de 30/12/2025 (edição extra, retificado no mesmo dia). O Planalto avisa que o texto "não substitui o publicado no DOU".

| Artigo | O que diz | Dicionário |
|---|---|---|
| 2º | Redução vale para PIS/Pasep e Cofins (inclusive importação), IRPJ, CSLL, II, IPI e contribuição previdenciária patronal; abrange os benefícios do demonstrativo de gastos tributários da LOA 2026 e os regimes: lucro presumido, REIQ, crédito presumido de IPI (3 leis), crédito presumido de PIS e Cofins (8 leis) e as reduções a zero e de alíquota da Lei 10.925 | Os 7 tributos estão em `ID_Imposto`. **Falta a carga dos regimes e o demonstrativo da LOA 2026 (seção 5)** |
| 3º | Sistema padrão: IRPJ e CSLL pelo lucro real sem benefício; IPI pela Tipi sem as reduções das notas complementares; PIS e Cofins a 0,65% e 3% (cumulativo) ou 1,65% e 7,6% (não cumulativo); importação a 1,65% e 7,6% (serviços) ou 2,1% e 9,65% (bens); II pela TEC; patronal sobre a remuneração total | `Regime_Apuracao` e `Aliquota_Sistema_Padrao` |
| 5º | Isenção e alíquota zero: 10% da alíquota padrão; essas alíquotas não podem ser alteradas pelo Executivo (art. 153, § 1º); o adquirente não ganha crédito vedado | `Percentual_Aliquota_Padrao_Devido` = 10; `Credito_Adquirente` |
| 6º | Alíquota reduzida: 90% da reduzida mais 10% da padrão | `Percentual_Beneficio_Mantido` = 90 e `Percentual_Aliquota_Padrao_Devido` = 10 |
| 7º | Redução de base: 90% da redução | `Percentual_Beneficio_Mantido` = 90 |
| 8º | Crédito (inclusive presumido): aproveitamento limitado a 90%, cancelando o que não foi aproveitado; **não vale para crédito escriturado ou com direito adquirido até 31/12/2025** | D-N127: `Data_Corte_Credito_Escriturado` e `Valor_Cancelado_Reducao` |
| 9º | Redução de tributo devido: 90% da redução | `Percentual_Beneficio_Mantido` = 90 |
| 10 | Regimes de percentual da receita bruta: elevação de 10% na porcentagem | `Percentual_Acrescimo` = 10 |
| 11 e 12 | Base presumida: acréscimo de 10% nos percentuais de presunção (8% passa a 8,8%, como o documento 10 já descreve); no lucro presumido, só sobre a receita acima de R$ 5 milhões no ano, com limite proporcional a cada período e ajuste nos seguintes, e acréscimo proporcional às receitas de cada atividade | `Cad_Presuncao_Acrescimo`, `Mov_Apuracao_Presuncao_Atividade` e `_Limite` (D-N118, D-N119, D-N125 e D-N126) |
| 13 | Suspensão só com diferimento temporal fica fora da redução | D-N127: valor `suspensao_apenas_diferimento` |
| 14, I a XIII | As 13 exceções | `excecao_reducao_lc224`: **os 13 valores batem, na mesma ordem** |
| 15 | O Ministro da Fazenda regulamenta; a Receita orienta cada benefício reduzido | Portaria MF 3.278/2025 (lida: seção 8) |
| 16 e 17 (Cap. III) | Responsabilidade solidária por apostas de quota fixa não autorizadas (instituições financeiras e de pagamento; quem divulga publicidade) | Sem campo, como o documento 51 já registrou |

Duas conferências sem diferença: o limite de R$ 5 milhões no ano (art. 12, parágrafo único) é o que o dicionário tem para o IRPJ; para a CSLL continua valendo a observação do documento 53 (o texto dos atos não traz o limite anual de 2026, e o R$ 3,75 milhões segue como hipótese para o contador).

# 5. D-N133: carga genérica a partir do Decreto

A `Cad_Reducao_Beneficio_Federal` guarda uma linha por tributo, regime e forma de benefício, e a carga estava presa ao Decreto e à Portaria. O Decreto dá **todos os percentuais e as alíquotas padrão** (arts. 3º a 12), então a carga genérica pode ser montada agora: as combinações de tributo, regime e forma que o Decreto prevê, com `Fundamento_Legal` no artigo, `Situacao_Dado` provisório e vigência de 01/01/2026 (IRPJ e II) ou 01/04/2026 (demais). O número exato de linhas sai na consolidação.

**O que fica de fora da carga:** qual benefício específico cai em cada forma (a regra por produto), que depende do demonstrativo de gastos tributários da LOA 2026 e da orientação da Receita (a Portaria MF 3.278/2025 não traz lista, seção 8). A tabela de benefícios por produto (`Cad_Beneficio_Fiscal_Pis_Cofins` e o catálogo da D-N128) continua sem carga.

# 6. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| D-N132 | Criar `Cad_Participante_Situacao_Cnpj` (situação, motivo, situação especial, datas de inscrição e de constituição e EFR, com vigência) sem regra de bloqueio? | Sim: o anexo da IN 2.345 é a fonte e o dado não existe no dicionário |
| D-N133 | Carregar na revisão 5 as linhas genéricas de `Cad_Reducao_Beneficio_Federal` dos arts. 3º a 12 do Decreto, como provisórias, e deixar a regra por produto para depois (a Portaria não a traz)? | Sim: o Decreto é a fonte oficial dos percentuais |

**Respostas de Alberto (12/10/2026):** D-N132 sim, sem bloqueio; D-N133 sim, provisórias. Nada foi consolidado: o dicionário segue com 837 entidades e a revisão 5 (843 entidades, no mínimo 20 alteradas, D-N106 a D-N117 e D-N125 a D-N133) espera o "consolidar" de Alberto.

**Pendências que continuam:** demonstrativo de gastos tributários da LOA 2026 (art. 2º, § 2º, I, do Decreto; o catálogo de 34 itens da IN 2.305 é outra lista); texto do Anexo III antigo da IN 2.119/2022 (para saber o que a IN 2.345 mudou); lista de valores de situação cadastral do CNPJ; limite anual da CSLL em 2026 (contador).

# 7. Fontes e verificação

Fontes: "Anexo Único.pdf" da IN RFB 2.345/2026 (portal Normas da Receita, ato 153688, anexo 86624, 556 KB, lido em 12/10/2026 no navegador do aplicativo, com autorização de Alberto); texto do Decreto nº 12.808/2025 no Planalto, lido em 12/10/2026; `model.json` da revisão 4 (837 entidades).

**Conferido por mim.** Li o Decreto inteiro e comparei cada artigo com `Cad_Reducao_Beneficio_Federal`, `excecao_reducao_lc224`, o documento 10 e o documento 53; vi as duas páginas do anexo; procurei por script, em todas as entidades da revisão 4, os campos das decisões D-N106 a D-N117 e os campos do comprovante.

**Não verificado.** O que a IN 2.345 mudou em relação ao Anexo III antigo; os valores possíveis de situação cadastral; o demonstrativo da LOA 2026; a DOU (o Planalto não substitui a publicação oficial). O arquivo do anexo não foi guardado.

# 8. Portaria MF nº 3.278, de 31/12/2025 (chegou depois)

Alberto enviou o link do portal Normas da Receita (ato 148711). A Portaria (DOU de 31/12/2025, seção 1-B, página 1; assinada pelo Ministro substituto) é curta, com 6 artigos, e **não regulamenta por produto**. O que ela traz:

| Artigo | O que diz | Dicionário |
|---|---|---|
| 2º | Os 9 tributos reduzidos (PIS/Pasep, PIS/Pasep-Importação, Cofins, Cofins-Importação, IRPJ, CSLL, II, IPI e contribuição previdenciária patronal); o § 1º repete o art. 2º, § 2º, do Decreto: benefícios do demonstrativo de gastos tributários da LOA 2026 e os regimes (lucro presumido, REIQ, créditos presumidos de IPI e de PIS/Cofins, reduções da Lei 10.925); o § 2º manda a Receita orientar os contribuintes sobre cada benefício | `ID_Imposto` e `Regime_Apuracao` (a importação é regime de PIS e Cofins, não imposto separado) |
| 3º | **Datas:** a redução vale a partir de 01/01/2026 para IRPJ e II, e de 01/04/2026 para os demais tributos | Bate com a vigência de `Cad_Reducao_Beneficio_Federal` (documento 10) |
| 4º | Sistema padrão: as mesmas regras do art. 3º do Decreto | `Aliquota_Sistema_Padrao` |
| 5º | As mesmas 13 exceções do Decreto (art. 14), na mesma ordem | `excecao_reducao_lc224`: bate |
| 6º | Vigência na publicação | |

**O que ela não traz:** lista de produtos, NCM, benefício por benefício ou o demonstrativo da LOA 2026; também não repete os arts. 5º a 12 do Decreto (as formas e os percentuais). Então a carga por produto **não depende mais da Portaria**: depende do demonstrativo da LOA 2026 (a lista dos benefícios abrangidos) e da orientação da Receita (art. 2º, § 2º). A carga genérica da D-N133 não muda. Na consolidação, a descrição de `Cad_Reducao_Beneficio_Federal` (documento 10), que diz que a carga "depende do Decreto 12.808/2025 e da Portaria 3.278/2025", passa a citar as duas fontes como lidas e a pendência do demonstrativo da LOA.

**Fonte e verificação.** Texto do portal Normas da Receita, lido em 12/10/2026 no navegador do aplicativo ("este texto não substitui o publicado oficialmente"). Comparei com o Decreto e com `excecao_reducao_lc224`; não conferi no DOU.
