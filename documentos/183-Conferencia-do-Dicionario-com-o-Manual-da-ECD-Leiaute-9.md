# Conferência do Dicionário com o Manual da ECD (Leiaute 9): Documento 183

*Cruza os 71 registros do Manual de Orientação do Leiaute 9 da ECD (Ato Declaratório Executivo Cofis nº 01/2026, atualização de janeiro de 2026) e as regras do capítulo 1 com o dicionário da revisão 33. Mostra o que está coberto, o que se deriva, o que está parcial e o que falta, e propõe o desenho das lacunas. **Nada foi aplicado ao dicionário**; entra na próxima consolidação, depois das suas respostas.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. O que fiz e o resultado

Li o seu envio, "Manual do ECD que faltava", como um **pedido de conferência** do dicionário contra o manual, no mesmo molde dos documentos 167 e 176 para a EFD. Se você queria outra coisa, me diga. Li o capítulo 1 (regras gerais), a tabela de registros e o leiaute campo a campo dos blocos 0, I, J, K e 9. As regras de validação por registro li por amostra (0000, I051, J005, J801 e as do capítulo 4 só pelo título).

**Resultado em uma frase.** O núcleo contábil da ECD já está no dicionário: plano de contas, lançamentos, saldos, plano referencial, estrutura das demonstrações, signatários, e o arquivo com recibo, hash e retificação (a lacuna G-11 do documento 32, fechada pelos documentos 33 e 46, D-N104). O que falta é a **identificação do livro** (termo de abertura, forma, situação do período, grande porte), o **termo de verificação e as outras informações do bloco J**, o **código CVM do auditor**, o **centro de custo no plano referencial** e, dependendo de respostas suas, **subcontas da Lei 12.973 (RAS)**, **moeda funcional**, **mudança de plano**, **relacionamento com participantes** e o **bloco K**.

| Situação | Registros | O que significa |
|---|---|---|
| Coberto | 12 | Já tem entidade e campo. |
| Derivado | 17 | Sai de dados que existem na hora de gerar o arquivo (aberturas, encerramentos, contagens, termos). |
| Parcial | 18 | Existe a maior parte; faltam campos ou valores de domínio. |
| Ausente | 13 | Não existe no dicionário. |
| Fora do escopo | 11 | Bloco C (o PGE da Receita preenche) e o livro de balancetes diários, só de instituição financeira. |
| **Total** | **71** | Os registros da tabela 3.2 do manual. |

**O que proponho aplicar sem depender de informação sua** (seção 4.1): 2 entidades novas, 3 campos novos e 5 valores novos no domínio de `Tipo_Inscricao`. O restante (seção 4.2) espera as suas respostas, porque depende de fatos do grupo que eu não tenho.

# 2. Conferência registro a registro

| Registro | O que é | Situação | Onde está no dicionário e o que falta |
|---|---|---|---|
| **0000** | Abertura e identificação | Parcial | Cobertos: período, nome, CNPJ, UF, IE, município, IM (cadastro e `Mov_Escrituracao_Arquivo`), finalidade (`Finalidade`), hash da substituída (`Hash_Escrituracao_Anterior`), SCP (`ID_Entidade_Ligada`), versão (`Versao_Leiaute`). **Faltam:** situação no início do período, grande porte, tipo da ECD, moeda funcional, descentralizada, código do plano referencial (1 a 10). Entram em `Mov_Ecd_Periodo` (seção 4.1). |
| **0001** | Abertura do bloco 0 | Derivado | Indicador de movimento sai da existência de dados. |
| **0007** | Outras inscrições cadastrais | Parcial | `Cad_Participante_Inscricao` tem estadual, municipal, Suframa e NIRE; **faltam** as instituições da tabela do manual (Banco Central, Susep, CVM, ANTT e TSE). Cinco valores novos no domínio de `Tipo_Inscricao`, sem campo novo. |
| **0020** | Escrituração descentralizada | Ausente | Só vale se a sede e as filiais escrituram separado. Pergunta Q183-8. |
| **0035** | Identificação das SCP | Coberto | `Cad_Entidade_Ligada_Reinf` (a SCP) e `ID_Entidade_Ligada` no arquivo. |
| **0150** | Cadastro do participante | Coberto | `Cad_Participante` (país, CNPJ ou CPF, IE, município, Suframa). |
| **0180** | Relacionamento com o participante | Parcial | Coligada e controlada saem de `Cad_Participacao_Societaria`; **faltam** matriz e filial no exterior, controlada em conjunto, EPE, participante do conglomerado, vinculada (art. 23 da Lei 9.430) e país de tributação favorecida (art. 24). Pergunta Q183-7. |
| **0990** | Encerramento do bloco 0 | Derivado | Contagem de linhas na geração. |
| **C001 a C990** | Bloco C: ECD recuperada (9 registros) | Fora do escopo | O PGE da Receita preenche; o ERP gera o arquivo da própria contabilidade (seção 3, item 1.32). |
| **I001** | Abertura do bloco I | Derivado | Existência de dados. |
| **I010** | Identificação da escrituração | Parcial | Versão do leiaute coberta (`Versao_Leiaute`); **falta** a forma (G, R, A, B, Z): `Forma_Escrituracao`. |
| **I012** | Livros auxiliares e hash | Ausente | Só existe com diário resumido (R) e livros auxiliares. Pergunta Q183-2. |
| **I015** | Contas da escrituração resumida | Ausente | Idem. |
| **I020** | Campos adicionais | Ausente | Só serve à moeda funcional. Pergunta Q183-3. |
| **I030** | Termo de abertura | Parcial | NIRE coberto (`Cad_Participante_Inscricao`). **Faltam:** número de ordem, natureza do livro, data de arquivamento e de conversão dos atos, data de encerramento do exercício social. Entram em `Mov_Ecd_Periodo`. |
| **I050** | Plano de contas | Coberto | `Cad_Conta_Contabil` (código, natureza, sintética ou analítica, conta superior, descrição); a data da alteração é o início da vigência da versão; o nível sai da árvore; as naturezas receita, despesa e custo valem 04 (resultado). |
| **I051** | Plano referencial | Parcial | `Cad_Conta_Contabil_Referencial` liga a conta ao código por empresa e vigência. **Falta** o centro de custo, que desde o leiaute 9 é a chave do registro e é obrigatório na incorporação com RET e centro de custo por obra. `ID_Valor_Centro_Custo` opcional. |
| **I052** | Códigos de aglutinação | Coberto | `Cad_Estrutura_Demonstrativo_Linha_Conta` (a conta e a linha da demonstração). |
| **I053** | Subcontas correlatas | Ausente | Lei 12.973: AVJ, AVP, ágio desdobrado, adoção inicial e TBU. Pergunta Q183-4. |
| **I075** | Histórico padronizado | Ausente | Facultativo; hoje só o texto livre `Mov_Lancamento.Historico`. Pergunta Q183-6. |
| **I100** | Centro de custos | Coberto | `Cad_Dimensao_Contabil` com `Eh_Centro_Custo` e `Cad_Dimensao_Contabil_Valor`. |
| **I150 e I155** | Saldos periódicos | Coberto | `Mov_Saldo_Contabil` e `Mov_Saldo_Contabil_Dimensao` (inicial, débitos, créditos e final por conta e centro de custo); o indicador D ou C sai do sinal. |
| **I157** | Transferência de saldos do plano anterior | Ausente | Só quando o plano muda no meio do período. Pergunta Q183-5. |
| **I200** | Lançamento contábil | Coberto | O lote (`Mov_Lote_Lancamento`); o tipo N, E ou X é `ID_Tipo_Lancamento` (normal, encerramento, extemporâneo); a data do extemporâneo sai de `ID_Periodo_Referencia`. |
| **I250** | Partidas do lançamento | Parcial | Conta, centro de custo, valor, débito ou crédito, histórico e documento de origem (`Origem_Tipo` e `ID_Origem` do lote) cobertos. **Faltam** o código do histórico padronizado (Q183-6) e o participante da partida (Q183-7). |
| **I300 e I310** | Balancetes diários (livro B) | Fora do escopo | O livro B é só de instituições financeiras (manual, item 1.7). |
| **I350 e I355** | Contas de resultado antes do encerramento | Coberto | `Saldo_Final_Antes_Encerramento`. |
| **I500, I510, I550 e I555** | Razão auxiliar de leiaute parametrizável (RAS) | Ausente | Livro Z das subcontas. Pergunta Q183-4. |
| **I990** | Encerramento do bloco I | Derivado | Contagem de linhas. |
| **J001** | Abertura do bloco J | Derivado | Existência de dados. |
| **J005** | Demonstrações contábeis (período) | Coberto | Período e escopo: `Cad_Estrutura_Demonstrativo` (escopo empresa é ID_DEM 1; escopo grupo societário é ID_DEM 2, consolidadas). |
| **J100 e J150** | Balanço e DRE | Parcial | `Cad_Estrutura_Demonstrativo_Linha` (código de aglutinação, nível, superior, total ou detalhe, sinal). **Falta** a referência à nota explicativa (`NOTA_EXP_REF`): `Referencia_Nota_Explicativa`. |
| **J210 e J215** | DLPA e DMPL, fatos contábeis | Derivado | Estrutura pelo tipo `dmpl`; os fatos do J215 saem dos lançamentos nas contas ligadas à linha. |
| **J800** | Outras informações (RTF) | Ausente | Notas explicativas, relatório da administração, parecer, DFC, DVA, DRA. `Mov_Ecd_Documento_Complementar`. |
| **J801** | Termo de verificação para substituição | Ausente | Motivo e arquivo do termo, em `Mov_Ecd_Periodo`. |
| **J900** | Termo de encerramento | Derivado | Número de ordem, natureza, linhas e período saem de `Mov_Ecd_Periodo` e do arquivo. |
| **J930** | Signatários da escrituração | Coberto | `Cad_Empresa_Responsavel` (qualificação do assinante, CRC, indicador do responsável); e-mail e telefone vêm do cadastro do participante. |
| **J932** | Signatários do termo de verificação | Derivado | O contador do período e, se há auditoria, o auditor (`Cad_Empresa_Responsavel`). |
| **J935** | Auditores independentes | Parcial | `Tipo_Papel = auditor_independente` existe; **falta** o código CVM: `Codigo_Cvm_Auditor`. |
| **J990** | Encerramento do bloco J | Derivado | Contagem de linhas. |
| **K001 e K030** | Abertura e período do bloco K | Derivado | Só existe com escrituração consolidada. |
| **K100, K110 e K115** | Empresas e eventos societários da consolidação | Parcial | `Cad_Participacao_Societaria` (percentual, vigência) e `Mov_Ato_Societario`; faltam o percentual consolidado e a participação por evento. Pergunta Q183-8. |
| **K200 e K210** | Plano consolidado e mapeamento | Parcial | `Cad_Estrutura_Demonstrativo` com escopo grupo societário e `Cad_Estrutura_Demonstrativo_Linha`; falta o plano de contas consolidado por natureza e o mapeamento das contas das empresas. Pergunta Q183-8. |
| **K300, K310 e K315** | Saldos consolidados e eliminações | Parcial | `Mov_Lancamento_Consolidacao` (eliminações por tipo); falta o saldo agregado, eliminado e consolidado por conta, com a empresa detentora e a contraparte. Pergunta Q183-8. |
| **K990** | Encerramento do bloco K | Derivado | Contagem de linhas. |
| **9001 a 9999** | Bloco 9 (4 registros) | Derivado | Controle do arquivo: totais por registro e fim. |

# 3. Regras do capítulo 1 e onde cada uma vive

| Item do manual | Regra | Como o dicionário trata |
|---|---|---|
| 1.3 | Quem entrega: exclui Simples Nacional, inativas, órgãos públicos, imunes e isentas com receita abaixo de R$ 4,8 milhões e lucro presumido que adote livro caixa (com exceções, como distribuição acima da base). | Obrigação por empresa e regime já existe (`Cad_Obrigacao_Acessoria`, prazo por empresa); a decisão de entregar é do contador. Sem campo novo. |
| 1.5 | Prazo: último dia útil de junho do ano seguinte; extinção, cisão, fusão e incorporação até junho (evento de janeiro a maio) ou o último dia útil do mês seguinte ao evento (junho a dezembro). | `Cad_Obrigacao_Prazo_Entrega` e `Finalidade = evento_especial` com `Data_Evento_Especial` (documento 33, seção 6.2). Coberto. |
| 1.6 e 1.7 | Formas G, R, A, Z e B; só G sem auxiliares; R convive com A e Z; auxiliares vão antes e o hash entra no I012. | Falta a forma e o hash dos auxiliares: `Forma_Escrituracao` em `Mov_Ecd_Periodo`; I012 só se a Q183-2 pedir. |
| 1.8 | Hash do livro calculado pelo PGE (40 posições hexadecimais). | `Hash` e `Hash_Escrituracao` (D-N104). Coberto. |
| 1.10 e 1.11 | Um livro por arquivo; mais de um só com auxiliares; acima de 5 GB, só mensal; meses completos, mesmo ano, sem buracos; cisão parcial e incorporadora geram duas escriturações. | `Numero_Versao`, `Periodo_Inicio` e `Periodo_Fim` por arquivo; as regras viram avisos do Motor (seção 5). |
| 1.12 | Substituição: só com erro que lançamento extemporâneo não corrige; termo de verificação (J801) assinado pelo contador e, se auditada, pelo auditor; só até o fim do prazo da ECD do ano seguinte; mesmo CNPJ; hash do substituído. | `ID_Arquivo_Substituido`, `Hash_Escrituracao_Anterior`, `Numero_Recibo_Anterior` existem. Faltam o motivo e o arquivo do termo (`Mov_Ecd_Periodo`); o prazo e o CNPJ viram aviso. |
| 1.13 | Assinatura: no mínimo duas (contador, código 900, e um responsável pela assinatura, só um, que não seja o contador); e-CNPJ do declarante é o recomendado. | `Cad_Empresa_Responsavel` com qualificação e `Indicador_Responsavel_Legal`; as contagens viram aviso. |
| 1.16 | Plano com no mínimo 4 níveis; quarta fórmula só para um fato contábil. | Aviso do Motor. |
| 1.17 e 1.34 | Plano referencial facultativo; é o mesmo da ECF; desde o leiaute 9 a chave do I051 é o centro de custo e conta de natureza diferente é erro. | `Cad_Plano_Referencial*` já é o da ECF (documento 91). Falta o centro de custo (`ID_Valor_Centro_Custo`); a natureza vira aviso. |
| 1.18 | Multa por atraso: Lei 8.218, art. 12 (0,02% ao dia sobre a receita bruta, limite 1%, com redução); DARF código 1438, calculado no Sicalcweb. | O ERP não calcula multa (o PGE também não). Fica como informação; sem campo. |
| 1.21 | Período societário diferente do fiscal: ECD pelo societário, ajuste na ECF. | `Data_Encerramento_Exercicio_Social` em `Mov_Ecd_Periodo`; o bloco J só é obrigatório se o encerramento cai no período (aviso). |
| 1.22 | RAS: livro Z das subcontas (27 colunas por item), a manter e apresentar se intimada. | Ausente. Q183-4. |
| 1.23 | Moeda funcional: valores em reais nos campos normais e em moeda funcional (convertida) nos campos adicionais do I020. | Parcial: `Valor_Moeda_Funcional` existe no lançamento; falta o par reais e moeda funcional nos saldos e partidas. Q183-3. |
| 1.24 | SCP entrega ECD própria, com o CNPJ do sócio ostensivo e o da SCP no `COD_SCP`. | `ID_Entidade_Ligada`; falta `Tipo_Ecd`. |
| 1.25 | Livro auxiliar da investida no exterior, em arquivo digital padrão. | Não conferi o restante do item (seção 8). Sem desenho. |
| 1.26 e 1.28 | Autenticação é o próprio recibo; recuperar o recibo perdido. | `Numero_Recibo`, `ID_Documento_Recibo`, `Data_Hora_Recibo`. Coberto. |
| 1.30 | RET: escrituração segregada por incorporação, em livros próprios ou nos da incorporadora, por centro de custo. | O módulo imobiliário já trata o RET; o centro de custo no I051 é o campo que falta (Q183-C1). |
| 1.32, 1.39 e 1.40 | Recuperar a ECD anterior; saldo final anterior igual ao saldo inicial; correção por lançamento extemporâneo tipo X. | O ERP é a fonte dos próprios saldos (`Saldo_Inicial` = `Saldo_Final` anterior) e tem o tipo extemporâneo. Aviso quando o saldo inicial difere da ECD aceita. |
| 1.36, 1.43 e 1.44 | Mesmo código mantém a natureza; só entram no plano as contas com saldo ou movimento; plano único no ano. | Avisos do Motor. |
| 1.38 | Número do livro: a base não aceita repetido; não precisa ser sequencial. | `Numero_Ordem_Livro`; aviso se repetir no ERP. |

# 4. Lacunas e desenho proposto

## 4.1 O que proponho aplicar já

**Mov_Ecd_Periodo** (nova): identificação da ECD de um arquivo. É para a ECD o que `Mov_Efd_Contribuicoes_Periodo` é para a EFD-Contribuições: guarda os dados de abertura que o arquivo precisa e não pertencem ao cadastro. Uma linha por linha de `Mov_Escrituracao_Arquivo` com `ID_Obrigacao = ECD`. *Vigência: não.*

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Ecd_Periodo` | identificador | — |
| `ID_Escrituracao_Arquivo` | referência (`Mov_Escrituracao_Arquivo`) | Um por arquivo; só arquivo da ECD. |
| `Forma_Escrituracao` | enumeração {diario_geral, diario_resumido, diario_auxiliar, balancetes_balancos, razao_auxiliar} | I010 (G, R, A, B, Z). Sem valor oculto: o usuário escolhe. |
| `Numero_Ordem_Livro` | número | I030 e J900. Aviso se já existe outro arquivo da empresa com o mesmo número. |
| `Natureza_Livro` | texto (até 80) | I030 e J900 (por exemplo, "Livro Diário"). |
| `Situacao_Inicio_Periodo` | enumeração {normal, abertura, resultante_cisao_fusao_ou_incorporadora, inicio_obrigatoriedade} | 0000, campo 12. A situação especial (cisão, fusão, incorporação e extinção) fica em `Mov_Escrituracao_Arquivo.Situacao_Especial`; "abertura" ali é da EFD e na ECD vale aqui. |
| `Data_Encerramento_Exercicio_Social` | data | I030. Decide se o bloco J é obrigatório (aviso). Informada na ECD, sem valor sugerido escondido (Q183-9). |
| `Data_Arquivamento_Atos_Constitutivos` | data, opcional | I030, `DT_ARQ`. |
| `Data_Arquivamento_Conversao` | data, opcional | I030, `DT_ARQ_CONV`: conversão de sociedade simples em empresária. |
| `Indicador_Grande_Porte` | booleano | 0000: ativo total acima de R$ 240 milhões ou receita bruta anual acima de R$ 300 milhões. Informado; aviso quando difere do que os saldos mostram (Q183-9). |
| `Tipo_Ecd` | enumeração {empresa_sem_scp, socio_ostensivo_de_scp, scp} | 0000, `TIP_ECD`. |
| `Indicador_Moeda_Funcional` | booleano | 0000, `IDENT_MF`. Falso até a Q183-3. |
| `Indicador_Escrituracao_Descentralizada` | booleano | 0000, `IND_CENTRALIZADA`. Falso até a Q183-8. |
| `ID_Tipo_Plano_Referencial` | referência (`Cad_Classe_Sistema`, domínio = plano_referencial_ecd, opcional) | 0000, `COD_PLAN_REF` (1 a 10: PJ em geral lucro real e presumido, financeiras, seguradoras, imunes e isentas, previdência, partidos). Não é `Cad_Plano_Referencial` (essa é a edição publicada por leiaute). |
| `ID_Motivo_Substituicao` | referência (`Cad_Classe_Sistema`, domínio = motivo_substituicao_ecd, opcional) | J801, `COD_MOT_SUBS` (001, 002, 003, 004, 005 e 099). Obrigatório quando `Finalidade` é substituta. |
| `ID_Documento_Termo_Verificacao` | referência (`Cad_Documento`, opcional) | J801: o termo em RTF, no GED. Obrigatório com o motivo. |

Os campos "mudança de plano" (`IND_MUDANC_PC`) e "escrituração consolidada" (`IND_ESC_CONS`) **não** viram campo: saem da vigência de `Cad_Plano_de_Contas_Empresa` dentro do período e da existência do bloco K.

**Mov_Ecd_Documento_Complementar** (nova): os arquivos do J800, um por documento. *Vigência: não.*

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Documento_Complementar` | identificador | — |
| `ID_Escrituracao_Arquivo` | referência (`Mov_Escrituracao_Arquivo`) | O arquivo da ECD. |
| `ID_Tipo_Documento` | referência (`Cad_Classe_Sistema`, domínio = tipo_documento_ecd) | 001 resultado abrangente, 002 fluxos de caixa, 003 valor adicionado, 010 notas explicativas, 011 relatório da administração, 012 parecer dos auditores, 099 outros. |
| `Descricao` | texto, opcional | `DESC_RTF`. |
| `ID_Documento` | referência (`Cad_Documento`) | O RTF no GED (até 30 MB). O hash do RTF é calculado na geração, não é digitado. |

**Três campos em entidades que existem:**

| Entidade | Campo novo | Tipo | Regra |
|---|---|---|---|
| `Cad_Empresa_Responsavel` | `Codigo_Cvm_Auditor` | código (até 20), opcional | J935. Só com `Tipo_Papel = auditor_independente`. |
| `Cad_Conta_Contabil_Referencial` | `ID_Valor_Centro_Custo` | referência (`Cad_Dimensao_Contabil_Valor`, opcional) | I051: a chave desde o leiaute 9. Conta e centro de custo mapeiam para um só código referencial. Vazio: o código vale para a conta em qualquer centro de custo. |
| `Cad_Estrutura_Demonstrativo_Linha` | `Referencia_Nota_Explicativa` | código (até 12), opcional | `NOTA_EXP_REF` do J100, J150 e J210. |

Mais **cinco valores** no domínio de `Cad_Participante_Inscricao.Tipo_Inscricao` (`bacen`, `susep`, `cvm`, `antt`, `tse`), para o registro 0007, sem campo novo.

**Contas previstas se aprovado:** 1.109 entidades (+2), 12.430 campos (+24: 16 e 5 nas entidades novas e 3 nas existentes) e 3.250 campos de referência (+8).

## 4.2 O que depende da sua resposta

Cada item abaixo precisa de um fato do grupo, que o manual não responde. Só desenho depois do seu "sim".

| Tema | O que o manual exige | O que eu proponho se a resposta for "sim" |
|---|---|---|
| **Subcontas e RAS** (Q183-4) | I053 liga a subconta à conta principal, com a natureza da tabela (TBU, ágio em goodwill, mais valia e menos valia, AVJ, AVP, adoção inicial: 25 naturezas). O RAS (livro Z) guarda, por item, saldo inicial e final do bem e da subconta, realização, lançamento e adoção inicial (27 colunas). | 3 campos em `Cad_Conta_Contabil` (natureza da subconta, conta principal, código do grupo) e uma entidade de item do RAS. O `Mov_Agio` de hoje só tem o valor do ágio; o desdobramento em mais valia e goodwill precisaria entrar. |
| **Moeda funcional** (Q183-3) | Campos normais em reais; campos adicionais (I020) com a moeda funcional convertida em reais, em I155, I157, I200, I250, I310 e I355. | Um segundo conjunto de valores em `Mov_Lancamento` e `Mov_Saldo_Contabil`, ligado ao `Indicador_Moeda_Funcional`. |
| **Mudança de plano** (Q183-5) | I157 lista, para cada conta nova, as contas do plano antigo e o saldo transferido. | Uma entidade de sucessão (conta anterior, conta nova, vigência); os saldos saem de `Mov_Saldo_Contabil`. |
| **Histórico padronizado** (Q183-6) | I075 e `COD_HIST_PAD` do I250 (facultativos). | `Cad_Historico_Padrao` e `ID_Historico_Padrao` opcional em `Mov_Lancamento`. |
| **Participante e relacionamento** (Q183-7) | `COD_PART` na partida (facultativo) e 0180 com 11 tipos de relacionamento. | `ID_Participante` opcional em `Mov_Lancamento`; entidade `Cad_Participante_Relacionamento` (participante, empresa, tipo, vigência). |
| **Bloco K e escrituração descentralizada** (Q183-8) | K: empresas consolidadas, eventos, plano e saldos consolidados, eliminações; 0020: sede e filiais com livros separados. | Entidades do K (plano consolidado, mapeamento, saldo por conta com agregado, eliminado e consolidado, detentora e contraparte). |

# 5. Avisos do Motor que o manual traz

Registrados como **aviso**, nunca bloqueio, e **não programados** (regra D-N284: o ERP só registra; quem barra é o validador da Receita):

1. Período: meses completos, no mesmo ano e sem buracos, salvo situação especial ou início de atividade (0000 e item 1.11).
2. Arquivo acima de 5 GB só pode ser mensal (item 1.10; o texto da regra do registro 0000 fala em "um gigabyte (5 GB)", e o manual se contradiz).
3. Plano de contas com no mínimo 4 níveis, só contas com saldo ou movimento no período e um plano único para todos os arquivos do ano (itens 1.16 e 1.43).
4. Plano referencial: só conta analítica, mesma natureza da conta contábil, código vigente no período e uma referência por conta e centro de custo (item 1.34).
5. Saldo inicial igual ao saldo final do período anterior; total devedor igual ao credor; mesmo código mantém a natureza (item 1.36).
6. Número do livro repetido para a mesma empresa (item 1.38).
7. Substituição: só até o fim do prazo da ECD do ano-calendário seguinte, mesmo CNPJ, hash do substituído e termo de verificação presentes (item 1.12).
8. Assinaturas: no mínimo duas, um contador (900), um só responsável pela assinatura e esse responsável não é o contador (item 1.13).
9. Bloco J obrigatório quando o encerramento do exercício cai no período; em substituição, o termo e os signatários dele (itens 1.21 e 1.35).
10. Cisão parcial ou incorporadora: duas escriturações; situação especial em 31 de dezembro: uma só (item 1.11).
11. Grande porte: ativo total acima de R$ 240 milhões ou receita bruta acima de R$ 300 milhões pede auditor independente (J935); aviso quando o indicador difere (registro 0000).
12. Lançamento extemporâneo só em período fechado ou já entregue, e quarta fórmula só para um fato contábil (itens 1.16 e 1.32).

# 6. Quadro de decisões

| Item | Decisão |
|---|---|
| ECD no dicionário: núcleo coberto, G-11 fechada | **Registrado** nesta conferência. |
| `Mov_Ecd_Periodo`, `Mov_Ecd_Documento_Complementar`, 3 campos e 5 valores de domínio | **Proposta**; entra na consolidação depois do seu "sim" (Q183-1). |
| Subcontas e RAS, moeda funcional, mudança de plano, histórico padronizado, participante, bloco K e 0020 | **Pendentes** das suas respostas (Q183-3 a Q183-8). |
| 12 avisos do Motor | **Proposta** (Q183-10). |

# 7. Perguntas para você

**Q183-1.** Aprova o **núcleo da seção 4.1**: `Mov_Ecd_Periodo` (16 campos), `Mov_Ecd_Documento_Complementar` (5 campos), os 3 campos novos e os 5 valores de `Tipo_Inscricao`? Recomendo **sim**.

**Q183-2.** A Mlegate entrega a ECD como **diário geral (G)**, sem livros auxiliares? Se sim, o I012 e o I015 não entram e o hash dos auxiliares fica de fora. Recomendo **sim**; `Forma_Escrituracao` guarda os cinco valores do manual.

**Q183-3.** Alguma empresa do grupo escritura em **moeda funcional diferente do real** e precisa informar `IDENT_MF = S`? Recomendo **responder**: sem empresa nesse caso, o `Indicador_Moeda_Funcional` fica falso e o segundo conjunto de valores não é desenhado.

**Q183-4.** Alguma empresa do grupo tem **subconta da Lei 12.973**: ágio desdobrado em mais valia e goodwill, ajuste a valor justo (AVJ) ou a valor presente (AVP), adoção inicial ou controlada no exterior (TBU)? Se sim, desenho o I053 e o RAS (livro Z, que o manual manda manter e apresentar se houver intimação). Se não, deixo só a natureza da subconta na conta (3 campos), sem o RAS.

**Q183-5.** O plano de contas pode **mudar no meio do ano** (I157)? Recomendo **só na virada do período da ECD**: assim o I157 não é necessário. Se mudar no meio, desenho a sucessão de contas.

**Q183-6.** Quer o **histórico padronizado** (I075)? Recomendo **não agora**: o registro é facultativo e o texto livre do lançamento basta.

**Q183-7.** Quer (a) o **participante em cada partida** (`COD_PART`, facultativo) e (b) a tabela de **relacionamento com o participante** (0180: coligada, controlada, vinculada, país de tributação favorecida e outros)? Recomendo **(a) não** e **(b) sim**: o relacionamento tende a servir também às partes vinculadas da ECF (a conferir no leiaute 12).

**Q183-8.** O grupo faz **escrituração consolidada** na ECD (bloco K, só de conglomerado econômico) ou **escritura sede e filiais em separado** (registro 0020)? Recomendo **não** nos dois, que valem para casos regulados; `Indicador_Escrituracao_Descentralizada` fica falso.

**Q183-9.** A **data de encerramento do exercício social** e o **grande porte** entram **informados na ECD** (recomendo), sem parâmetro na empresa, com aviso quando o grande porte diverge dos saldos?

**Q183-10.** Aprova registrar os **12 avisos** da seção 5 sem programá-los? Recomendo **sim**.

**Q183-C1 (contador).** Na incorporação com RET e centro de custo por obra, o plano referencial é mapeado **por centro de custo** no I051? Isso decide se o `ID_Valor_Centro_Custo` fica em uso ou só previsto.

# 8. Limites

- O manual é o de **janeiro de 2026** (leiaute 9). Não conferi se há edição posterior nem as tabelas externas que ele cita (naturezas das contas, qualificação do assinante e plano referencial por segmento).
- As regras de validação por registro li **por amostra**; o capítulo 4 (níveis 1 e 2) não li. Os itens 1.25 (restante), 1.31 e 1.32 (detalhe) também não.
- A conferência olha o **dicionário** (revisão 33), não o que o programa ainda vai gerar. A geração do arquivo, em leiaute `Cad_Obrigacao_Leiaute_Registro` e `Cad_Obrigacao_Leiaute_Campo`, carrega os registros do leiaute 9 como dado; essa carga não está feita.
- Nada foi aplicado: continua a revisão 33 (1.107 entidades e 12.406 campos).
