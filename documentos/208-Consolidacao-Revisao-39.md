# Consolidação da Revisão 39 — Documento 208

*Relatório do que entrou no dicionário com o seu "consolidar" de 10/11/2026 (depois do documento 206). Você não escolheu escopo; apliquei **só o que você aprovou e que fecha sozinho**: o documento 202 inteiro (B6, regime automotivo, crédito presumido da CBS dos projetos habilitados; Q202-1 a Q202-11, D-N541) e o ajuste A1 do documento 205 (Q205-3, D-N544). Ficaram de fora o B1 do documento 205 (a entidade dele é do documento 204, que não tem resposta) e o documento 206 (sem resposta).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 38 | Revisão 39 | Diferença |
|------------------------------------------------------|----------------|----------------|---------------|
| Entidades | 1.165 | 1.173 | +8 |
| Campos | 13.204 | 13.339 | +135 |
| Campos de referência (FK) | 3.445 | 3.463 | +18 |
| Entidades mestres | 235 | 237 | +2 |
| Referências genéricas | 62 | 62 | 0 |
| Domínios de `Cad_Classe_Sistema` | 355 | 355 | 0 |
| Tabelas físicas (DDL) | 1.400 | 1.410 | +10 |
| Chaves estrangeiras (DDL) | 3.680 | 3.700 | +20 |
| Índices (DDL) | 3.771 | 3.791 | +20 |
| Comentários (DDL) | 10.993 | 11.120 | +127 |
| Comandos do T-SQL | 19.845 | 20.022 | +177 |
| Chaves opcionais que esperam a onda de destino | 80 | 80 | 0 |

**8 entidades novas** (134 campos, todas em Contabilidade & Fiscal e na onda 3) e **3 existentes alteradas** (1 com campo novo, 2 só com valor de enumeração ou texto), distribuídas assim:

| Decisão | Entidades novas | Campos nelas | Campos novos em existentes |
|----------------------|-----------------------------------|--------|-----------------------------------|
| Q202-2 (habilitação automotiva) | 2 (`Cad_Habilitacao_Automotiva` 22, mestre, e `Cad_Habilitacao_Automotiva_Produto` 10) | 32 | 0 (texto em `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao`) |
| Q202-3 (parâmetros do crédito) | 1 (`Cad_Credito_Automotivo_Parametro` 16, mestre) | 16 | 0 |
| Q202-4 (apuração mensal) | 2 (`Mov_Credito_Automotivo_Apuracao` 20 e `Mov_Credito_Automotivo_Apuracao_Ncm` 9) | 29 | 0 (valor novo `presumido_automotivo` em `Mov_Credito_Fiscal.Origem`) |
| Q202-6 (limite mensal de uso) | 1 (`Mov_Credito_Automotivo_Debitos_Proprios` 14) | 14 | 1 (`ID_Credito_Automotivo_Debitos_Proprios` em `Mov_Credito_Fiscal_Aplicacao`) |
| Q202-7 e Q205-3 (compromissos, com o A1) | 1 (`Mov_Habilitacao_Automotiva_Compromisso` 17) | 17 | 0 |
| Q202-8 (devolução) | 1 (`Mov_Credito_Automotivo_Devolucao` 26) | 26 | 0 (valor novo `devolucao_credito_automotivo` em `Mov_Titulo.Origem_Tipo`) |
| Q202-1, Q202-5, Q202-9 a Q202-11 | 0 | 0 | 0 (escopo, leituras provisórias, documentação, período e partes e peças: carga e regras de texto) |
| **Total** | **8** | **134** | **1** |

Duas das oito entidades novas têm vigência e viram duas tabelas no DDL (mestres): `Cad_Habilitacao_Automotiva` e `Cad_Credito_Automotivo_Parametro`. Por isso as 8 entidades dão 10 tabelas.

# 2. O que entrou, por decisão

## 2.1 Habilitação e parâmetros (Q202-1 a Q202-3, Q202-9 a Q202-11)

- **`Cad_Habilitacao_Automotiva`** (22 campos, mestre) e **`Cad_Habilitacao_Automotiva_Produto`** (10): a parte automotiva da habilitação, no molde da Suframa. O projeto aprovado nos termos do art. 11-C da Lei 9.440/1997 ou dos arts. 1º a 4º da Lei 9.826/1999, o estabelecimento incentivado, o ato concessório, o início da fruição e o período do crédito; os produtos por NCM, com a alíquota de IPI de referência. `Cad_Habilitacao_Regime_Especial` ganha o tipo `regime_automotivo` (carga) e o texto de `Numero_Habilitacao` passa a dizer que, nesse regime, o número é o do ato concessório do MDIC.
- **`Cad_Credito_Automotivo_Parametro`** (16, mestre): os percentuais por faixa do mês de fruição (art. 521), os fatores do IPI (art. 522), a data de referência da alíquota (31/12/2025) e o mínimo de 10% de pesquisa e desenvolvimento. Carga de 22 linhas, todas provisórias. O crédito vale de 01/01/2027 a 31/12/2032 (Q202-10); não há parâmetro de 2033 em diante.
- **Partes, peças e pneumáticos** (Q202-11): marca `Abrange_Partes_Pecas_Pneumaticos` e aviso permanente até o contador responder (C253).
- **Documentação** (Q202-9): 25 parâmetros e 34 efeitos pela regra da Q201-3, todos na escrituração do IBS e da CBS, mais cinco linhas do catálogo central; ECD, ECF e as demais obrigações ficam sem efeito documentado até a C251.

## 2.2 Apuração, uso e leituras provisórias (Q202-4 a Q202-6)

- **`Mov_Credito_Automotivo_Apuracao`** (20) e **`Mov_Credito_Automotivo_Apuracao_Ncm`** (9): a apuração mensal com a memória de cálculo. Lei 9.440: base × percentual da faixa do mês de fruição; Lei 9.826: soma por NCM de V × Al × (1 − Al) × F, com Al a alíquota de IPI de 31/12/2025 ou a informada no produto. O crédito nasce em `Mov_Credito_Fiscal` (CBS) com a origem nova `presumido_automotivo`, a partir do primeiro dia do mês seguinte; não é ressarcível nem transferível.
- **`Mov_Credito_Automotivo_Debitos_Proprios`** (14) e o campo novo em `Mov_Credito_Fiscal_Aplicacao`: o limite mensal de uso (débitos federais do mês vezes a fração das vendas de veículos do estabelecimento habilitado nos três meses anteriores). O ERP avisa, nunca bloqueia (D-N284).
- **As quatro leituras provisórias** (Q202-5) viram parâmetros por empresa, com padrão visível e aviso a cada uso: o mês de fruição contado do início da fruição (C248), o IPI na base (C249) e os débitos próprios com os tributos federais que o ERP apura e o limite que não acumula (C250).

## 2.3 Compromissos e devolução (Q202-7, Q202-8, Q205-3)

- **`Mov_Habilitacao_Automotiva_Compromisso`** (17): o ERP só registra os compromissos do ato concessório e o que a auditoria do MDIC disse. **Com o ajuste A1 do documento 205** (Q205-3), a entidade já nasce com o valor `informacao_anual_pdi` em `Tipo_Compromisso` e os campos `Data_Limite_Cumprimento` (31/07 do ano seguinte, sugerido), `Data_Intimacao` e `Data_Limite_Regularizacao` (intimação mais 30 dias). Os avisos 21 e 22 são regra de texto do Motor, sem campo; o saldo de pesquisa, a perda do direito e o máximo de fruição seguem sem campo até a C267.
- **`Mov_Credito_Automotivo_Devolucao`** (26): a devolução quando a habilitação é cancelada (art. 526), com F1, F2 e F3 como conferência do valor que o MDIC apurar, o título a pagar (valor novo `devolucao_credito_automotivo` em `Mov_Titulo.Origem_Tipo`) e o prazo de cinco anos, sem cálculo de juros de mora (C255).

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|--------------------------------|--------|-----------------------------------------------------------|
| `Cad_Classe_Sistema` (valor novo) | 1 | `regime_automotivo` em `tipo_regime_especial_federal` |
| `Cad_Credito_Automotivo_Parametro` | 22 | 15 percentuais, 5 fatores, a data de referência e o mínimo de pesquisa |
| `Cad_Obrigacao_Parametro_Definicao` | 5 | uma do catálogo legal e quatro das leituras provisórias |
| `Cad_Parametro_Documentacao` | 25 | 7 parâmetros legais, 14 chaves de decisão e 4 leituras provisórias |
| `Cad_Parametro_Efeito_Obrigacao` | 34 | todos na `ESCRITURACAO_IBS_CBS` |

Total: **87 linhas em 5 arquivos de dados** (pasta `Carga39`, com LEIA-ME). Ordem de carga: `Cad_Parametro_Documentacao` antes de `Cad_Parametro_Efeito_Obrigacao`, ambas depois da Carga38.

# 4. Leituras minhas que aguardam a sua confirmação

# 1. **"Consolidar" foi lido como "o que você aprovou e fecha sozinho"**: o documento 202 inteiro e o A1 do 205. O **B1** do 205 (Q205-2, aprovada) acrescenta dois campos a `Mov_Is_Veiculo_Apuracao`, que é entidade do **documento 204**; como o 204 não tem resposta (Q204-1 a Q204-10), não há onde aplicar o B1. A Q205-1 (a correção do texto do 204) também espera. A D-N544 dizia que 202, 204 e 205 entrariam juntos; **se você queria o 204 e o 206 dentro, responda as perguntas deles e eu faço a revisão 40**, que já sai com as somas abaixo. 2. **O A1 entrou direto na entidade nova**: `Mov_Habilitacao_Automotiva_Compromisso` nasce com 17 campos e o valor `informacao_anual_pdi`, sem passar por ALTER. 3. **Vigência de partida das cargas:** as 22 linhas de parâmetros trazem a vigência do documento 202 (de 01/01/2027, com as faixas até 2032), todas provisórias; o contador valida (C248 a C255, documento 188). 4. **A alíquota `Al` da Lei 9.826** depende da Tipi de 31/12/2025 com o Decreto 12.549, que a Tipi enviada não traz (C266); a tabela virá no **documento 207** (Q205-4), que continua reservado. O relatório tem o número 208 por isso. 5. **Alertas do gerador de DDL:** os mesmos sete campos de texto sem tamanho em chave única da revisão 38; nenhum novo. Declarar `texto (n)` continua decisão sua.

**Somas para a revisão 40 (minhas, a conferir quando ela for feita):** com o documento 204 e o B1, 1.179 entidades, 13.468 campos, 3.486 referências e 357 domínios; com o documento 206 também, 1.197 entidades, 13.715 campos, 3.544 referências e 358 domínios.

# 5. Como conferi

| Conferência | Resultado |
|--------------------------------------------------|--------------------------------------------------|
| Contagem de entidades e campos contra o previsto no documento 202 e no A1 do 205 | 1.165 + 8 entidades e 13.204 + 134 + 1 campos: **1.173 entidades e 13.339 campos**, como o modelo regerado; 3.463 referências (+18) e 355 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 62 referências genéricas (sem mudança) |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.410 tabelas, 3.700 chaves estrangeiras e 11.120 comentários conferidos no banco; as 8 tabelas novas e as 2 de versão foram criadas |
| T-SQL (analisador sqlglot, oito arquivos de onda e os comentários) | Lido sem erro; 20.022 comandos (177 a mais: 10 tabelas, 20 chaves, 20 índices e 127 comentários). **Não equivale a executar num SQL Server.** |
| Ondas | As oito entidades na onda 3; nenhuma chave opcional nova espera a onda de destino (continuam 80) |
| Carga | 87 linhas; os CSV são os do documento 202, com o texto de origem trocado de "proposta" para "carga de partida da revisão 39"; todas provisórias |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** as Q204-1 a Q204-10 (e com elas o B1 e a Q205-1); as Q206-1 a Q206-12; a tabela de IPI de 31/12/2025 (documento 207) e a Tipi consolidada que você vai enviar (Q205-4); o manual oficial da DeRE e o ato do fator de redução (Q198-12); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9 (sem efeito no dicionário); o ato do art. 414, § 2º, da LC 214 (valor de referência do IS); a portaria MF 2.813; a lista vigente de autopeças da Camex (Q206-10).
- **Contador:** C1 a C277 do documento 188 (entre elas C248 a C255 do B6, C256 a C265 do documento 204, C266 a C268 do 205 e C269 a C277 do 206).
- **Equipe e fontes oficiais:** seção 3 do documento 38; as portarias do Mover, as 17 portarias do Rota 2030 e o ato do MDIC sobre a versão sustentável, ainda sem leitura.
- **Fila de desenho:** o B7 (marketplace) e o Imposto Seletivo de bebidas, fumígenos e minerais seguem sem desenho.

# 7. Limites

- O desenho do B6 vem da LC 214 (arts. 309 a 316), do Decreto 12.955 (arts. 518 a 527) e das Leis 9.440 e 9.826 e dos Decretos 10.457 e 7.422, nos trechos citados nos documentos 202 e 205; **não conferi no DOU**, e o ato do Poder Executivo do art. 518, § 4º, não foi publicado, pelo que sei.
- Quatro leituras do documento 202 são minhas (mês de fruição, IPI na base, débitos próprios e limite que não acumula); as 22 linhas de parâmetros nascem provisórias.
- A documentação dos parâmetros cobre só os 25 do B6; ECD, ECF e as demais obrigações ficam sem efeito até a resposta do contador (C251).
- O ERP não conversa com o MDIC: registra o ato, os compromissos, a auditoria e o cancelamento, e avisa.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1, 8 e 10 do dicionário, o 202, o 208 e os demais relatórios seguem só nos Word desta entrega.
