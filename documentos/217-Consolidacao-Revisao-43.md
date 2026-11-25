# Consolidação da Revisão 43 — Documento 217

*Relatório do que entrou no dicionário com o seu "consolidar" de 12/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava aplicado**: o documento 215 inteiro, na versão 2.1 (ST de autopeças e as variações por UF; Q215-1 a Q215-4, D-N571, e Q215-6, D-N573) e o documento 216 inteiro (Imposto Seletivo de bebidas, fumígenos, minerais e prognósticos; Q216-1 a Q216-6, D-N575, com a regra de que qualquer NCM pode ter IS, D-N574).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 42 | Revisão 43 | Diferença |
|---|---|---|---|
| Entidades | 1.206 | 1.220 | +14 |
| Campos | 13.895 | 14.154 | +259 |
| Campos de referência (FK) | 3.586 | 3.645 | +59 |
| Entidades mestres | 247 | 256 | +9 |
| Referências genéricas | 62 | 63 | +1 |
| Domínios de `Cad_Classe_Sistema` | 360 | 369 | +9 |
| Tabelas físicas (DDL) | 1.453 | 1.476 | +23 |
| Chaves estrangeiras (DDL) | 3.833 | 3.901 | +68 |
| Índices (DDL) | 3.924 | 3.992 | +68 |
| Comentários (DDL) | 11.668 | 11.913 | +245 |
| Comandos do T-SQL | 20.879 | 21.283 | +404 |
| Chaves opcionais que esperam a onda de destino | 84 | 84 | 0 |

**14 entidades novas** (246 campos; 7 do documento 215 e 7 do 216) e **3 existentes alteradas** (13 campos novos). Nove das novas têm vigência (as seis de cadastro da ST de autopeças e três do Imposto Seletivo) e viram duas tabelas cada no DDL; por isso as 14 entidades dão 23 tabelas. Treze entidades ficam na onda 3 (Contabilidade & Fiscal) e `Mov_Icms_St_Base_Calculo_Item`, na onda 4, porque depende do item da nota de saída.

# 2. O que entrou

**Do documento 215 (ST de autopeças por UF):**

- **`Cad_Icms_St_Acordo_Regra`** (21 campos, mestre): o acordo que a UF usa (Protocolo 41/08, 97/10 ou legislação própria), com a prioridade quando o item está em dois, o método de cálculo e a fonte.
- **`Cad_Icms_St_Uf_Mva`** (16 campos, mestre): a MVA por UF, por perfil do remetente, por CEST e por alíquota interestadual.
- **`Cad_Icms_St_Uf_Base_Criterio`** (14 campos, mestre): a ordem e a condição dos preços da base e a definição da alíquota interna.
- **`Cad_Icms_St_Uf_Recolhimento`** (16 campos, mestre): prazo, guia, parcelas e código de receita por tipo de operação.
- **`Cad_Icms_St_Uf_Nao_Aplicacao`** (14 campos, mestre): as hipóteses em que a ST não se aplica, com o efeito (afasta ou mantém).
- **`Cad_Icms_St_Lista_Item`** (16 campos, mestre): a lista de itens da UF e do acordo, por CEST ou NCM.
- **`Mov_Icms_St_Base_Calculo_Item`** (27 campos): a memória do cálculo por item de nota.
- **6 campos novos:** `Regime_Fidelidade_Distribuicao`, `Papel_Substituto_St` e `ID_Documento_Autorizacao_Fisco` em `Cad_Autopecas_Perfil`; `Natureza_Regime`, `Renovacao_Automatica` e `Prazo_Meses` em `Cad_Filial_Regime_Icms`.
- **4 domínios abertos** (`acordo_st_icms`, `metodo_calculo_st_uf`, `perfil_remetente_st` e `hipotese_nao_aplicacao_st`; 22 valores) e **6 valores novos** em `tipo_regime_icms` (o credenciamento de AL, a dispensa de MG e quatro obrigações acessórias do MS).
- **18 regras** e **18 avisos** do Motor, no anexo. **Sem carga de UF** (D-N569, Q215-3).

**Do documento 216 (Imposto Seletivo):**

- **`Cad_Is_Produto_Ficha`** (18 campos, mestre): a ficha do produto de qualquer NCM (teor alcoólico, volume, vintena, condição, preço tabelado).
- **`Cad_Is_Valor_Referencia_Regra`** (18 campos, mestre): a metodologia do valor de referência por grupo e hipótese.
- **`Cad_Is_Pequeno_Produtor_Faixa`** (12 campos, mestre): as faixas de redução do pequeno produtor de bebida alcoólica (Anexo VI da MP).
- **`Mov_Is_Pequeno_Produtor_Volume`** (16 campos): o volume do ano anterior por produtor.
- **`Mov_Is_Produto_Apuracao`** (27 campos): a memória do cálculo do IS por item.
- **`Mov_Is_Gas_Natural_Declaracao`** (15 campos): a declaração do gás natural (art. 423 da LC 214).
- **`Mov_Prognostico_Receita_Periodo`** (16 campos): a receita própria dos concursos de prognósticos e do *fantasy sport*.
- **7 campos novos em `Cad_NCM_Imposto_Seletivo`:** `Exige_Ficha_Produto`, `Teor_Alcoolico_Minimo_Percentual`, `Teor_Alcoolico_Maximo_Percentual`, `ID_Condicao_Produto_Is`, `Aliquota_Maxima_Percentual`, `Atualiza_Pelo_Ipca` e `ID_Serie_Cotacao_Atualizacao`. Nenhuma entidade nova fixa grupo ou NCM: a linha da NCM governa e qualquer NCM pode ganhar IS no futuro (D-N574).
- **5 domínios abertos** (`condicao_produto_is`, `metodologia_valor_referencia_is`, `tipo_pequeno_produtor_is`, `destinacao_gas_natural_is` e `modalidade_prognostico_is`; 24 valores).
- **17 regras** e **18 avisos** do Motor, no anexo.

**Anexo 56 do documento 10 e anexo 10 do documento 01:** as 14 entidades, as cargas, as regras e os avisos dos dois documentos.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Classe_Sistema`: 4 domínios do 215 | 22 | `acordo_st_icms` 4, `metodo_calculo_st_uf` 5, `perfil_remetente_st` 4, `hipotese_nao_aplicacao_st` 9 |
| `Cad_Classe_Sistema`: `tipo_regime_icms` | 6 | Valores novos do domínio existente |
| `Cad_Classe_Sistema`: 5 domínios do 216 | 24 | `condicao_produto_is` 5, `metodologia_valor_referencia_is` 5, `tipo_pequeno_produtor_is` 5, `destinacao_gas_natural_is` 3, `modalidade_prognostico_is` 6 |
| `Cad_NCM_Imposto_Seletivo` | 25 | 21 linhas do Anexo IV da MP 1.399 (bebidas e fumígenos, com os Ex da Tipi) e 4 de bens minerais; vigência de 02/02/2027 a 31/12/2027 |
| `Cad_Is_Pequeno_Produtor_Faixa` | 3 | 0 a 50.000 L (40%), 50.000 a 125.000 L (20%) e 125.000 a 250.000 L (10%) |
| `Cad_Is_Valor_Referencia_Regra` | 4 | 3 do fumígeno (art. 6º, I) e 1 do mineral (art. 414, § 2º, ato ainda não publicado) |
| Regras do Motor (texto) | 18 + 17 | CSV de leitura; a gravação em `Cad_Motor_Regra` é do carregador do Motor |
| Avisos do Motor (texto) | 18 + 18 | CSV de leitura |

Total: **84 linhas de carga em tabelas e 71 de texto (regras e avisos)**, em 10 arquivos de dados (pasta `Carga43`, com LEIA-ME). Ordem: `01-dominios` primeiro (as linhas do IS apontam para os domínios), depois `02-imposto-seletivo`; ambas depois da Carga42.

**Fora da carga, de propósito:** qualquer linha de UF da ST de autopeças (Q215-5); a alíquota de 0,5% dos prognósticos (fica em `Mov_Prognostico_Receita_Periodo.Aliquota_Is_Percentual`); as linhas de ficha, de volume, de declaração e de apuração (são dados do cliente); o IS de 2028 em diante e o escalonamento de 2029 a 2033 (dependem da lei do art. 15).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como os documentos 215 (v2.1) e 216 inteiros** (D-N571, D-N573 e D-N575).
2. **A vigência das linhas do IS** vai de 02/02/2027 (efeitos da MP 1.399) a 31/12/2027; não há linha para 2028 até a lei do art. 15.
3. **O fator de ajuste de importação das bebidas** (1,45, art. 8º da MP) vale também para a bebida açucarada, porque o texto diz "bebidas" (C332); nos fumígenos é 1,00 e nos minerais fica vazio.
4. **A descrição dos valores de domínio** da carga é o próprio código com espaços; é provisória e você ou o contador ajustam o rótulo.
5. **A unidade "vintena"** do valor específico do cigarro (R$ 3,50, atualizado pelo IPCA) tem de existir em `Cad_Unidade_Medida`; o carregador a cria se faltar.
6. **`Mov_Icms_St_Base_Calculo_Item` fica na onda 4**, junto com o item da nota de saída; as outras 13 ficam na onda 3.
7. **As regras e os avisos vão como CSV de texto**, como nas cargas anteriores.
8. **As linhas do Anexo IV seguem o texto da MP**, inclusive onde ele diverge da Tipi (C324 e C325: o álcool etílico, a 24.01 e a 24.04 inteiras a 37,5% e o cigarro sem tabaco, que cai em "demais"); a divergência é do contador, e o ERP calcula pelo texto e avisa.
9. **As somas previstas bateram** (1.220 entidades, 14.154 campos, 3.645 referências, 369 domínios e 256 mestres). **Alertas do gerador de DDL:** os mesmos sete campos de texto sem tamanho em chave única; nenhum novo.
10. **Nenhuma chave opcional nova espera a onda de destino:** continuam 84 na seção 3.1 do documento 31.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto | 1.206 + 14 entidades e 13.895 + 246 + 13 campos: **1.220 entidades e 14.154 campos**, como o modelo regerado; 369 domínios |
| Referências | 3.645 (+59: 29 do documento 215 e 30 do 216, 28 nas entidades novas e 2 em `Cad_NCM_Imposto_Seletivo`), como previsto |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 63 referências genéricas (+1: `Mov_Is_Gas_Natural_Declaracao.ID_Item_Origem`). Dois achados do rascunho foram corrigidos antes: o nome da chave de versão das mestres do 216 (tem de ser a chave primária mais `_Versao`) e esse campo de referência genérica, que estava como identificador |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.476 tabelas, 3.901 chaves estrangeiras e 11.913 comentários conferidos no banco; as 14 tabelas novas foram criadas |
| T-SQL (contagem dos comandos nos oito arquivos de onda e no de comentários) | 21.283 comandos (404 a mais: 23 tabelas, 68 chaves, 68 índices e 245 comentários), lidos por um analisador de T-SQL sem erro. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | 13 entidades na onda 3 e 1 na onda 4; 80 entidades empurradas por módulo posterior (79 + `Mov_Icms_St_Base_Calculo_Item`); 84 chaves opcionais esperam a onda de destino |
| Carga | 84 linhas de carga em 7 arquivos e 71 de texto em 4 (10 arquivos de dados; os de domínio têm 52 valores); colunas conferidas em todas as linhas; as linhas do Anexo B do documento 216 e as regras e avisos lidos dos próprios documentos 215 e 216, nas versões aprovadas |
| Modelo entidade-relacional | Regerado, com 109 diagramas |

# 6. O que continua aberto

- **Você:** a Q215-5 (os textos oficiais para a carga por UF: o Anexo X do RICMS-MT e a Portaria 195/2019, o Anexo 1 do RICMS-BA, o regulamento atual de ST do RICMS-PR, o Decreto 90.309/2023 de AL e os Protocolos 97/10, 93/26, 94/26 e 96/26); a lista de autopeças não produzidas (Q206-10); o Protocolo 41/2008 e o regulamento de ST de uma UF (Q209-9, em parte cumprida); o manual oficial da DeRE e o ato do fator de redução (Q198-12); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9.
- **Contador:** C1 a C334 do documento 188 (entre elas C308 a C323, do 215: a denúncia e a adesão do DF, a MVA original de AL, BA, MT, PR e PI, a alíquota da ST e a ALQ intra, a autorização do fisco de destino, o segundo acordo de autopeças, SP depois de 01/10/2026 e as tabelas de BA, AL, PA, MG e AC; e C324 a C334, do 216: o álcool etílico e os mostos, os fumígenos 24.01 e 24.04, o valor de referência dos fumígenos, a atualização pelo IPCA, os prognósticos, o pequeno produtor, o gás natural, os bens minerais, a importação, a bebida açucarada e a embalagem primária).
- **Equipe e fontes oficiais:** seção 3 do documento 38.
- **Fila de desenho:** o que segue sem desenho está na seção 1.13 do documento 38 (o Bloco 1 de combustíveis e usina, o split payment e a carga da lista de autopeças não produzidas).

# 7. Limites

- A carga do **IS** vem do **texto da MP 1.399/2026 (Anexos IV e VI)**, que é provisória: vale até a lei do art. 15 (projeto até 31/05/2027), e o Congresso pode mudá-la. O ERP guarda tudo com vigência.
- **O ato do art. 414, § 2º** (metodologia do valor de referência) **não existe**; vale a regra do art. 6º até 31/12/2027. O **Decreto 7.212** (arts. 212-B e 220-A) não foi lido; o R$ 3,50 por vintena vem da tabela da MP.
- Na **ST de autopeças** o modelo aceita as variações por UF, mas **nenhum percentual, lista ou prazo de UF está carregado**: o ERP não grava "36,56 e 71,78" como regra do protocolo (Q215-3). Os valores dependem da leitura dos textos oficiais de cada UF e da vigência dos Protocolos 93/26, 94/26 e 96/26, com efeitos de 01/10/2026.
- **Prognósticos:** o ERP prevê a receita própria e a alíquota, mas nenhum cliente opera hoje; sem tela nem rotina até haver cliente.
- O ERP registra, calcula o que a norma fecha e avisa; não bloqueia (D-N284).
- O Project continua acima do limite de tamanho, e a documentação passou a ser mantida no repositório GitHub (a gravação nele é manual nesta sessão): os .md desta entrega estão na pasta `Documentacao-ERP-completa`.
