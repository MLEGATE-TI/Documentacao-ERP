# Consolidação da Revisão 17 do Dicionário — Documento 89

*Relatório da consolidação feita em 20/10/2026, depois do "Verificar inconsistencia e consolidar" de Alberto para os documentos 84 a 88 (decisões D-N259 em diante). Não altera decisões: registra o que mudou, o que ficou de fora e por quê, as inconsistências achadas, os números e os testes.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

O dicionário passou de **900 para 907 entidades**: 8 entidades novas e 1 que saiu (`Cad_Lalur_Tabela_Dinamica`, substituída pelas tabelas dinâmicas gerais da ECF). Os campos passaram de **9.672 para 9.760**, os campos de referência (FK) de **2.596 para 2.624**, os domínios de **260 para 266** e as entidades mestres de **180 para 183**. As referências genéricas seguem em **50**. Foram alteradas **25 entidades existentes**: 5 na Fase 0 (documento 01), 13 em Contabilidade & Fiscal (documento 10) e 7 em Folha & RH (documento 11). A auditoria acusou 6 achados na primeira passada (campos de referência novos sem o prefixo `ID_`, regra D2), corrigidos antes de fechar, e terminou com **0 achados**.

O DDL foi regerado: **1.090 tabelas físicas**, **2.807 chaves estrangeiras**, **2.872 índices** e **7.816 comentários**. O PostgreSQL 16 executou os oito arquivos de onda e o de comentários, em ordem, sem erro. O T-SQL (**14.586 comandos**) foi lido por um analisador sem erro; **não foi executado** num SQL Server, e a primeira execução continua para a equipe.

**Como entendi o pedido.** "Verificar inconsistência e consolidar" são duas tarefas em ordem. Primeiro conferi as decisões dos documentos 84 a 88 entre si e com o dicionário (seção 4). Depois consolidei **só o que tem resposta sua e desenho completo de campos**. Onde a decisão está tomada mas o documento só dá o nome da entidade e uma estimativa de campos (por exemplo, "cerca de 8 campos"), não inventei a lista: ela está no **documento 90, para a sua aprovação**, e entra numa revisão 18. Onde não houve resposta, nada entrou. Se a leitura estiver errada e você quiser que eu aplique o documento 90 já, basta dizer.

# 2. O que mudou no dicionário

## 2.1 Entidades novas (8, todas em Contabilidade & Fiscal, onda 3)

| Entidade | Campos | Decisão | O que guarda |
|-----------------------------|-------|---------------|--------------------------------------------------|
| `Cad_Desif_Instituicao_Enquadramento` | 10 | D-N259 a D-N262 | Histórico do tipo e do enquadramento da instituição na DES-IF, com vigência; confirmação do contador na própria linha; aviso e não bloqueio |
| `Cad_Obrigacao_Leiaute_Registro` | 14 | D-N318 | Registros de cada versão de leiaute de uma obrigação (a ECF entra como mais uma obrigação, leiaute 12) |
| `Cad_Obrigacao_Leiaute_Campo` | 14 | D-N318 e D-N319 | Campos de cada registro: tipo, tamanho, obrigatório, valores válidos |
| `Cad_Ecf_Tabela_Dinamica` | 6 | D-N321 | Uma linha por tabela dinâmica da ECF (uma aba da planilha) |
| `Cad_Ecf_Tabela_Dinamica_Linha` | 15 | D-N321 | Linhas das tabelas dinâmicas, com vigência; recebe as linhas do M300 e do M350 |
| `Cad_Ecf_Parte_B_Relacionamento` | 8 | D-N321 | Relacionamento da tabela padrão da Parte B |
| `Mov_Ecf_Importacao_Registro` | 6 | D-N317 e D-N319 | Cada linha de cada registro importado dos blocos X, Y e W, exatamente como veio |
| `Mov_Ecf_Importacao_Registro_Campo` | 6 | D-N319 | Um campo por linha importada (`Eh_Alterado` marca o que mudou numa importação derivada) |

**Saiu:** `Cad_Lalur_Tabela_Dinamica` (9 campos, revisão 15). `Mov_Lalur_Lancamento_Parte_A.ID_Lalur_Tabela` passa a apontar para `Cad_Ecf_Tabela_Dinamica_Linha`; o valor antigo `compensacao` virou `compensacao_prejuizo` e o tipo de lançamento ganhou `lucro`. Conta: 79 campos novos, 9 que saem e 18 de saldo nas entidades existentes dão os 88 a mais.

## 2.2 Campos novos, que saem e renomeados nas entidades existentes

| Entidade | Mudança | Decisão |
|----------------------------------------|----------------------------------------|---------------------|
| `Cad_Desif_Instituicao` | Saem `ID_Tipo_Instituicao`, `Enquadramento` e `Fundamento_Enquadramento` (vão para a entidade de histórico) | D-N259 |
| `Cad_Participante_Situacao_Cnpj` | Novos `Origem` {consulta_receita, ajuste_manual} e `ID_Usuario_Ajuste`; `ID_Consulta` fica vazio no ajuste manual | D-N272, D-N274 a D-N276 |
| `Mov_Documento_Fiscal` | Novos `Situacao_Idoneidade` {idoneo, nao_idoneo, a_reavaliar} e `Motivo_Situacao_Idoneidade` | D-N272, D-N274 a D-N276 |
| `Cad_Dfe_Parametro_Regra` | Novo `ID_Situacao_Cadastral_Impeditiva` (substitui a D-N132) | D-N272 |
| `Cad_Redutor_Base_Dere` | Novo `ID_Cod_Trib`: o redutor passa a variar por tipo de informação e por período | D-N273 |
| `Cad_Aliquota` | Novos `Eh_Suspensao` (exige percentual zero) e `ID_Natureza_Aliquota` {efetiva, teste} | D-N277, D-N279, D-N291, D-N292 |
| `Cad_Rh_Parametro_Jornada` | Novos `ID_Filial`, `ID_Modo_Composicao_Noturna`, `Duracao_Hora_Noturna_Minutos` e `Minutos_Hora_Aula`; ordem de busca: filial com categoria, categoria, filial, empresa | D-N293, D-N294, D-N297 a D-N299 |
| `Cad_Vinculo_Emprego` | Sai `Conta_Cota_Pcd`; `Regime_Previdenciario` vira `ID_Regime_Previdenciario` (domínio) | D-N300, D-N305 |
| `Cad_Vinculo_Temporario`, `Cad_Vinculo_Estatutario`, `Mov_Rh_Processo_Trabalhista_Contrato` | `Hipotese_Legal`, `Tipo_Plano_Rpps` e `Regime_Previdenciario` viram referências a domínios de `Cad_Classe_Sistema` (`ID_Hipotese_Legal`, `ID_Tipo_Plano_Rpps`, `ID_Regime_Previdenciario`) | D-N305 |
| `Cad_Participante_Vinculacao` | Novos `ID_Usuario_Confirmacao` e `Data_Hora_Confirmacao`: só o contador cria e altera | D-N312, D-N313, D-N325 |
| `Cad_Obrigacao_Leiaute_Versao` | `Codigo_Versao_Arquivo` passa de 3 para até 4 caracteres; novos `Data_Edicao_Manual`, `Situacao_Dado` e `ID_Instancia_Aprovacao`; a ECF entra como obrigação | D-N318 |
| `Mov_Ecf_Importacao_Bloco` | `Versao_Leiaute` vira `ID_Leiaute_Versao`; novos `ID_Importacao_Origem` e `Motivo_Alteracao` (importação derivada) | D-N318, D-N322 |
| `Cad_Plano_Referencial` | `Segmento` vira `ID_Segmento` (domínio de 9 segmentos) | D-N321 |
| `Cad_Plano_Referencial_Conta` | Novos `Tipo_Conta`, `Nivel` e `Orientacoes` | D-N321 |
| `Mov_Lalur_Lancamento_Parte_A` | `ID_Lalur_Tabela` aponta para a linha da tabela dinâmica geral | D-N321 |

## 2.3 Domínios (6 novos, 2 ampliados)

Novos em `Cad_Classe_Sistema.Dominio`: `natureza_aliquota` (efetiva, teste), `modo_composicao_noturna` (composto, soma), `hipotese_legal_temporario`, `plano_rpps`, `regime_previdenciario` (todos com o código do eSocial) e `segmento_plano_referencial` (nove segmentos). Ampliados: `indicador_perfil_ecf`, de 9 para 28 valores (um por indicador de sim ou não do registro 0020 do leiaute 12), e `parametro_ecf`, com `limite_cartao_exterior_anual`. Os nomes dos 20 valores novos do perfil foram escritos por mim a partir do nome do campo do manual (cada um traz o nome do campo entre parênteses no anexo do documento 01) e valem como rótulo: o contador pode ajustá-los sem mudar a estrutura.

## 2.4 Alterações só de texto

Regras da nota de aluguel (`Mov_Locacao_Faturamento`, `Mov_Nfse_Unidade_Imobiliaria`, `Mov_Nfse_Dps`, D-N270 e D-N271); texto de `Cad_Rh_Regra_Hora_Extra` (cálculo composto, D-N297); obrigatoriedade da cota de pessoa com deficiência derivada do cadastro (`Cad_Rh_Estabelecimento_Esocial`, D-N300); `Cad_Ecf_Parametro` (vigência desde 01/01/2026, fonte no manual, D-N310 e D-N323); `Mov_Ecf_Perfil_Indicador` e `Mov_Ecf_Importacao_Bloco` (conferência de 21 linhas, regra do Y520, D-N309, D-N311, D-N315, D-N324); lista de tipos de vinculação (D-N325); a tabela de conferência do documento 10, de 8 grupos para 21 linhas.

# 3. O que ficou de fora e por quê

## 3.1 Decidido por Alberto, mas sem lista de campos aprovada (documento 90)

| Decisão | O que falta |
|-----------------------|-----------------------------------------------------------------------------|
| D-N269 e D-N278 | `Cad_Lista_Legal_Item` (com `ID_Aliquota`) e `Cad_Taxa_Depreciacao_Cbs`: o documento 86 dá os nomes e as regras, não os campos |
| D-N280 e D-N281 | Coeficiente do crédito presumido por ano e categoria e `Permite_Ressarcimento`: falta dizer em que entidade moram |
| D-N283 | `Mov_Agencia_Turismo_Repasse` (cerca de 8 campos) |
| D-N284 | Auto de infração e procedimento fiscal (cerca de 8 a 10 campos) |
| D-N285 a D-N290 | `Cad_Regra_Operacao_Equiparada_Cbs`, `Tipo_Onerosidade`, opção da doação com origem e confirmação, e `Regra_Fornecimento_Gratuito_Cbs` no participante (6 campos em entidades existentes) |
| D-N295 e D-N296 | Alíquota do Imposto Seletivo e do IPI pelo item da lista legal, com NBS nos serviços; depende da D-N269 |
| D-N301 a D-N303 | `Cad_Esocial_Ocorrencia`, `Mov_Esocial_Evento_Ocorrencia` (cerca de 14 campos) e o texto de `Evento_Importado` |

## 3.2 Sem resposta de Alberto (nada entrou)

D-N249 a D-N253, D-N257, D-N258 e D-N263 (locação, DeSTDA, MEI, tabela oficial vencida e `Mov_Nfse_Dps.Versao_Leiaute`), D-N267 (desenho do módulo de Comércio Exterior, em documento próprio) e D-N268 (`Cad_Participante_Qualificacao_Cbs`, sem confirmação expressa).

## 3.3 Adiado por Alberto

D-N282, split payment (arts. 28 a 30 do Decreto 12.955/2026): reabrir com a regulamentação definitiva ou com cliente prestador de pagamento. A informação de que a entrada foi adiada para 2028 é dele, não conferida no texto legal.

# 4. Inconsistências achadas na verificação

| Nº | Achado | Tratamento |
|------|-----------------------------------------------|-----------------------------------------------|
| 1 | O documento 88 dá `Codigo_Tabela` como "até 10", mas a aba `ParteB_Padrao` tem 13 caracteres | Apliquei "até 20" |
| 2 | O documento 88 conta 27 campos para as duas entidades do leiaute; a lista tem 28 (14 em cada) | Vale a lista; a contagem do documento 88 era a errada |
| 3 | Os campos novos de referência da primeira versão não tinham o prefixo `ID_` (6 achados da regra D2 da auditoria) | Renomeados: `ID_Natureza_Aliquota`, `ID_Modo_Composicao_Noturna`, `ID_Regime_Previdenciario` (2 entidades), `ID_Tipo_Plano_Rpps` e `ID_Hipotese_Legal` |
| 4 | A D-N301 substitui a regra de 19/10/2026 (S-2200 do vínculo importado só depois da confirmação do lote pelo RH), mas a D-N301 ficou fora | **Divergência conhecida:** `Evento_Importado` (documento 11) segue com a regra antiga até a aprovação do documento 90 |
| 5 | O texto de apoio do manual da ECF cita um X291 que não existe no PDF nem no Word | Ignorado (D-N324); nenhuma entidade nem valor usa o X291 |
| 6 | O manual da ECF, lido ao pé da letra, não deixa informar as linhas R e P do Y520 ao mesmo tempo; a decisão de Alberto (convivem) vale | Conferência só em aviso (D-N315); teste no validador da Receita fica com o contador |
| 7 | `Enquadramento_Confirmado_Em` (D-N241) e o campo `Enquadramento` na instituição ficariam duplicados com a entidade nova | D-N259 substitui a D-N241; os três campos saíram da instituição |
| 8 | Menções restantes a `Cad_Lalur_Tabela_Dinamica`, `Conta_Cota_Pcd`, `Versao_Leiaute` (do bloco da ECF) e aos nomes renomeados | Conferi: só aparecem nas notas de revisão e na descrição histórica; nenhuma referência quebrada |
| 9 | Os valores de `natureza_aliquota` na carga (CBS 0,9% e IBS 0,1% em 2026) vêm de fonte secundária | Mantidos como teste, com a marca de a conferir na descrição de `ID_Natureza_Aliquota` |
| 10 | O valor 4 (spsmfa) de `regime_previdenciario` no S-2500 não foi conferido no leiaute | Registrado na descrição do campo; a validação do evento decide |

# 5. Auditoria

Primeira passada: 6 achados (item 3 da seção 4). Depois da correção: **0 achados em aberto**. As regras de nome e de domínio seguem o padrão (os domínios novos são valores de `Cad_Classe_Sistema.Dominio`; os booleanos `Eh_Suspensao` e `Eh_Alterado` usam o prefixo permitido).

# 6. Efeito no plano de implementação

Nenhuma entidade mudou de onda e as 62 chaves estrangeiras que esperam a onda de destino são as mesmas. Onda 0: de 1.619 para 1.626 campos e de 362 para 365 chaves estrangeiras. Onda 3 (Contabilidade & Fiscal): de 391 para 398 entidades, de 87 para 90 mestres, de 4.635 para 4.713 campos e de 1.161 para 1.180 chaves estrangeiras. Onda 6 (Folha & RH): de 1.130 para 1.133 campos e de 311 para 317 chaves estrangeiras.

# 7. Números

| | Revisão 16 | Revisão 17 |
|----------------------------------------------------------|---------------------|---------------------|
| Entidades | 900 | 907 |
| Campos | 9.672 | 9.760 |
| Campos de referência (FK) | 2.596 | 2.624 |
| Referências genéricas | 50 | 50 |
| Domínios em `Cad_Classe_Sistema` | 260 | 266 |
| Entidades mestres | 180 | 183 |
| Tabelas físicas | 1.080 | 1.090 |
| Chaves estrangeiras no DDL | 2.776 | 2.807 |
| Índices no DDL | 2.840 | 2.872 |
| Comentários de coluna no DDL | 7.731 | 7.816 |
| Comandos T-SQL lidos pelo analisador | 14.428 | 14.586 |
| Achados da auditoria (final) | 0 | 0 |

Revisões dos documentos: Fase 0 de 64 para 65, Contabilidade & Fiscal de 34 para 35 e Folha & RH de 26 para 27; Compras (23), Jurídico (7) e os demais seguem como estavam.

# 8. Perguntas depois da consolidação

| Nº | Situação |
|---------------------------------------|-------------------------------------------------------------|
| Q84-5 | **Aberta**, do contador: quando o enquadramento muda dentro do semestre do Módulo 1, o arquivo usa a linha da última competência (provisório) |
| Q80-1 | **Aberta**, do contador: regra da NFTS no R-2010 (D-N242); vale o tratamento provisório da D-N240 |
| Q80-5 | **Aberta**, de Alberto e do contador: quais clientes equiparados existem e o que já foi entregue |
| Q86-6 | **Aberta**: "tipo de informação" do redutor da DeRE é o `codTrib`? (o campo `ID_Cod_Trib` muda de referência se for outra classificação) |
| Q87-13, Q87-18, Q87-21 a Q87-23, Q87-27 | **Abertas** (RH, contador e fontes externas, documento 87) |
| Q70-1, Q70-13 e Q85-1 a Q85-9 e Q85-13 | **Abertas** (perfis de cliente, textos que faltam, locação e MEI) |
| Aprovações do contador | Limites da ECF (provisório), incisos do art. 4º da Lei 14.596, teste do Y520 no validador, conferência da carga do leiaute e das tabelas dinâmicas |
| Manual do eSocial | Código de "registro já existe", serviço de consulta por trabalhador e caminho de correção da matrícula (D-N301 a D-N303) |
| Documento 90 | **Para a sua aprovação**: campos das entidades da seção 3.1 |

O PDF oficial da NT 04/2026 não foi aberto (só a notícia); nada do dicionário depende dele hoje. A primeira execução do DDL num SQL Server continua para a equipe.

# 9. O que ficou para depois e a carga da ECF

- **Carga do leiaute 12 da ECF** (D-N320) e **carga das 78 tabelas dinâmicas** (D-N321): não foram geradas na consolidação em si, mas foram geradas em seguida, no mesmo dia, como arquivos CSV provisórios (seção 9.1).
- **Modelo ER do módulo Contabilidade & Fiscal no Project:** regerado localmente, mas não regravado no Project (o Project está acima do limite).


## 9.1 Carga provisória da ECF (gerada depois da consolidação)

Os arquivos de carga das duas decisões saíram em pacote próprio (`Revisao17-Carga-ECF.zip`, com LEIAME). **Nada entrou no dicionário nem no banco**: são CSV com chaves naturais, para a importação trocar pelos identificadores. Tudo sai `provisorio` até o contador validar.

| Carga | Arquivos | Linhas |
|------------------------------------|------------------------------------------|----------------------|
| Leiaute 12 (manual de 622 páginas) | versão, registros, campos | 1 · 188 · 1.122 |
| Tabelas dinâmicas (planilha de 24/09/2026, 27.842 linhas) | planos, contas dos planos, tabelas, linhas, relacionamento da Parte B | 18 · 12.744 · 78 · 4.475 · 904 |

O leiaute foi conferido por três testes: os 188 registros do manual foram lidos, a numeração dos campos é sequencial em todos e o campo REG confere com o código do registro (a exceção é o Y681, cujo REG diz X681 no manual). A carga não corrige o que a Receita publicou: o que é estranho vai para os arquivos de pendências (205 linhas no leiaute e 31 nas tabelas dinâmicas).

**Três pontos para Alberto:**

# 1. **Tipo NS.** O manual distingue `N` (sem sinal) de `NS` (numérico com sinal), em 34 campos; o dicionário só tem `caractere` e `numerico`. A carga grava `numerico`. Proposta (não feita): acrescentar `numerico_com_sinal` ao domínio, numa revisão 18. 2. **Plano compartilhado por segmentos diferentes.** As abas L100B, P100B e U100B são idênticas e de segmentos diferentes, e o mesmo vale para L100C e U100C. O plano compartilhado não pode ter um segmento só, e ficou sem segmento; o título da aba fica em `Cad_Ecf_Tabela_Dinamica`. Se o segmento precisar valer por aba, o desenho muda. 3. **Vigência do leiaute.** O manual fixa a validade por período da escrituração (ano-calendário 2025 e situações especiais de 2026), não por data. A carga grava início em 01/01/2025 e fim em 31/12/9999 (convenção da Fase 0); o contador confirma.

Entre as pendências do leiaute, as que mais pedem o contador: a obrigatoriedade condicional do CEBAS (0020) e do V100 (gravada como falso), os 45 registros em que a ocorrência do bloco difere da tabela de hierarquia (a carga usa o bloco) e os níveis de X451 e Y650 (bloco 3, tabela 2; a carga usa o bloco).

# 10. Documentos atualizados

- **Dicionário:** documento 01 (Fase 0, revisão 65), documento 10 (Contabilidade & Fiscal, revisão 35) e documento 11 (Folha & RH, revisão 27). Os documentos 03, 08 e 21 não mudaram.
- **Desenho:** documentos 84 a 88 (nota de consolidação no cabeçalho).
- **Relatórios:** documento 14 (seção da revisão 17), documento 29 (parágrafo), documento 31 (números das ondas e do DDL) e documento 45 (nota e perguntas).
- **Novo:** documento 89 (este) e documento 90 (campos propostos, para aprovação).
- **Modelo ER e diagramas:** regerados; o texto da revisão muda em todos os módulos, e mudam o conteúdo da Fase 0, de Contabilidade & Fiscal e de Folha & RH.

# 11. Espaço no Project

O Project continua acima do limite de 2.000.000 de unidades; nada foi apagado. Os documentos 59 a 90 (novos) **não estão no Project**. Os documentos 01, 10, 11, 14, 29, 31 e 45, que já existiam, são regravados no lugar.
