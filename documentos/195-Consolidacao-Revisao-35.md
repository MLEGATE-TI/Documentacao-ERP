# Consolidação da Revisão 35 — Documento 195

*Relatório do que entrou no dicionário com o seu "consolidar" de 09/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava no dicionário** depois da revisão 34: os documentos 185 e 187 (D-N500 e D-N516), os limites da ECF (D-N504 e D-N507), a origem XML da entrada (D-N506 e D-N510), os documentos 189 e 190 (D-N513), o documento 191 (D-N515) e o documento 192 (D-N519).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 34 | Revisão 35 | Diferença |
|---|---|---|---|
| Entidades | 1.135 | 1.138 | +3 |
| Campos | 12.739 | 12.769 | +30 |
| Campos de referência (FK) | 3.337 | 3.345 | +8 |
| Entidades mestres | 224 | 224 | 0 |
| Referências genéricas | 61 | 61 | 0 |
| Domínios de `Cad_Classe_Sistema` | 340 | 344 | +4 |
| Tabelas físicas (DDL) | 1.359 | 1.362 | +3 |
| Chaves estrangeiras (DDL) | 3.561 | 3.569 | +8 |
| Índices (DDL) | 3.652 | 3.660 | +8 |
| Comentários (DDL) | 10.561 | 10.587 | +26 |
| Comandos do T-SQL | 19.134 | 19.179 | +45 |
| Entidades com FK que espera a onda de destino | 79 | 79 | 0 |

**3 entidades novas** (23 campos) e **8 existentes alteradas** (7 campos novos em 4 delas; as outras 4 só mudam em valor de domínio ou em texto de descrição), distribuídas assim:

| Documento | Entidades novas | Campos nelas | Campos novos em existentes |
|---|---|---|---|
| 185 e 187 (ciência do indício de infração) | 1 (`Mov_Ciencia_Indicio_Infracao`) | 9 | 0 |
| 189 (situação cadastral e art. 51 da IN 2.119; suspensão do IPI) | 0 | 0 | 3 |
| 190 (motivos da suspensão do CNPJ) | 1 (`Cad_Participante_Situacao_Cnpj_Motivo`) | 4 | 0 |
| 191 (Confia, REIDI e liga e desliga do IPI) | 0 | 0 | 3 |
| 192 (registro 0000 da ECF) | 1 (`Mov_Ecf_Periodo`) | 10 | 0 |
| Q188-5 (origem XML da entrada) | 0 | 0 | 1 |
| Q188-3 e Q188-4 (Y520 e `IND_ATIV_EXT`) | 0 | 0 | 0 |
| **Total** | **3** | **23** | **7** |

As oito existentes alteradas são `Cad_Classe_Sistema` (4 domínios novos), `Cad_Participante_Situacao_Cnpj` (+2), `Mov_Documento_Fiscal` (+2), `Cad_Habilitacao_Regime_Especial` (+1), `Cad_Empresa_Programa_Conformidade` (+2), `Mov_Ecf_Y520_Linha` (valor `abaixo_do_limite`), `Cad_Ecf_Parametro` (texto) e `Mov_Escrituracao_Arquivo` (texto). O DDL não tem tabela a mais por mestre: nenhuma das três entidades novas tem vigência.

# 2. O que entrou, por documento

## 2.1 Documentos 185 e 187: ciência do indício e avisos do Confia e do Sintonia

- **`Mov_Ciencia_Indicio_Infracao`** (9 campos): o selo (`ID_Empresa_Programa`, Confia ou Sintonia), `Data_Ciencia`, `Data_Limite_Regularizacao` (digitada, o ERP não conta os 60 dias), `Situacao`, `Numero_Processo`, os dois campos padrão de dado provisório e `Observacao`. Padrão de `Mov_Condicao_Devedor_Contumaz`; o ERP só registra.
- **Cinco classificações do Sintonia** (A+, A, B, C e D, com a faixa da nota no texto) na carga de `classificacao_programa_conformidade`, provisórias.
- **Avisos do Motor, sem programar** (Q185-1, Q185-3, Q187-1 e Q187-2): sem bônus em estimativa mensal, para o Confia e o Sintonia; o selo do Sintonia vale até o fim do mês do cancelamento ou da expiração; readmissão no Confia antes de 2 anos da exclusão; indicadores do Sintonia como nota estimada por mês. A regra do bônus do Confia segue a **correção da Q191-3** (acaba no período de apuração do ADE de exclusão).
- A vigência dos selos em 09/04/2026 (art. 58, I) confirma a data da carga de `Cad_Parametro_Bonus_Adimplencia`, que era "pela minha conta" (registrado em regra de texto da carga).

## 2.2 Documentos 189, 190 e 191: CNPJ, IPI, Confia e REIDI

- **Situação cadastral (Q189-1):** as cinco do art. 9º da IN 2.119 (ativa, suspensa, inapta, baixada, nula) carregadas, e a descrição de `ID_Situacao_Cadastral` deixa de dizer "a conferir".
- **Art. 51 da IN 2.119 (Q189-2):** `Numero_Ato_Declaratorio` e `Data_Inicio_Efeito_Inidoneidade` em `Cad_Participante_Situacao_Cnpj`; `Situacao_Idoneidade_Federal` em `Mov_Documento_Fiscal` (idôneo, inidôneo pelo art. 51 e comprovado pagamento e recebimento). A regra da CBS e do IBS (`Situacao_Idoneidade`) não muda. O IRRF do § 6º fica só como aviso (C216).
- **Suspensão do IPI (Q189-3, com o ajuste da Q191-1):** 2 valores em `tipo_regime_especial_federal`, 3 em `situacao_suspensao_regime_especial`, o valor `autopecas_lei_10485` em `tipo_lista_legal` (no lugar de `ipi_suspensao_lei_10485`), duas descrições e os 4 avisos; e o **liga e desliga do IPI** pelos valores `ipi_suspensao` e `ipi_apuracao` de `modulo_fiscal_opcional`, por empresa e filial, a partir de uma data (nenhum ligado por padrão).
- **Repetro-Industrialização (Q189-4):** continua gancho; o desenho futuro está no texto do documento 01.
- **Motivos da suspensão do CNPJ (Q190-1):** `Cad_Participante_Situacao_Cnpj_Motivo` (4 campos) e os 24 motivos do Anexo I da IN 2.333 em `motivo_suspensao_cnpj`, provisórios, com vigência a partir de 10/07/2026.
- **Lista da Lei 10.485 (Q190-3):** 66 linhas (51 do Anexo I e 15 do Anexo II), vigência inicial 01/11/2002, provisórias, sem alíquota.
- **Fora do ERP (Q190-2, Q190-4 e Q190-5):** Anexo II da IN 2.333, Anexo Único da IN 2.324, carteira do Confia e retenção do art. 3º, § 3º, da Lei 10.485 (esta, com o contador, C219).
- **Confia e REIDI (documento 191):** `Data_Ato_Admissao` e `Data_Fato_Exclusao` em `Cad_Empresa_Programa_Conformidade`; `Data_Ato_Exclusao` passa a ser a publicação do ADE; 4 motivos de exclusão novos; o valor `plano_regularizacao_confia`; `Data_Conclusao_Projeto` na habilitação do REIDI; a descrição de `ID_Empresa` passa a "admitida"; avisos de 12 meses, 60 dias, devedor contumaz com Confia admitido e 30 dias do REIDI.

## 2.3 Documento 192: registro 0000 da ECF

- **`Mov_Ecf_Periodo`** (10 campos, uma linha por arquivo, sem vigência): situação de início, situação especial e data, percentual do patrimônio remanescente na cisão, `Tipo_Ecf`, evento da SCP, mudança de forma de tributação e `Hash_Ecf_Anterior`.
- **Três domínios** (`ecf_situacao_inicio_periodo`, `ecf_situacao_especial` e `ecf_evento_scp`) com 21 valores provisórios, o número do manual como código.
- Os campos genéricos de situação especial de `Mov_Escrituracao_Arquivo` ficam **vazios na ECF** (descrição), e o prazo lê `Data_Situacao_Especial`; os 11 avisos do Motor e as regras de prazo estão no anexo do documento 10. Onde a tabela e a lista do manual divergem, o ERP segue a lista do campo 6 e avisa o contador, até a resposta da Receita (pergunta 27).

## 2.4 Limites da ECF (D-N504 e D-N507)

- **Y520:** volta o valor `abaixo_do_limite` em `Mov_Ecf_Y520_Linha.Situacao` e o corte de R$ 120.000 do manual para cartão e moeda; **substitui a D-N356**. Câmbio, transferência internacional em reais e depósito ou recursos no exterior saem sempre. O indicador do 0020 conta só as linhas que vão ao arquivo.
- **Moeda:** `limite_moeda_exterior_anual` em `parametro_ecf`, com a mesma carga do cartão (R$ 120.000, vigência 01/01/2026, provisório).
- **`IND_ATIV_EXT`:** sim quando recebíveis de não residentes em aberto mais o saldo das contas bancárias no exterior somam R$ 100.000 ou mais, na data de encerramento, pela taxa de fechamento; o ERP calcula e o contador revisa. Só texto da descrição de `Cad_Ecf_Parametro.ID_Parametro`.

## 2.5 Origem XML da entrada (D-N510)

`Origem_Dados_Entrada` em `Mov_Documento_Fiscal` (importado de XML ou digitado). Importado: número, série e data vêm do arquivo e não se alteram; se o XML veio errado, importa-se o arquivo certo ou descarta-se o documento. A conferência final do desenho da NFTS segue com o contador (C4 do documento 188).

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Classe_Sistema` (valores novos) | 69 | 24 motivos de suspensão do CNPJ, 5 situações cadastrais, 21 da ECF (9 + 10 + 2), 2 + 3 do regime especial, 1 da lista legal, 2 do módulo opcional, 4 motivos de exclusão, 1 de parcelamento, 1 de parâmetro da ECF e 5 classificações do Sintonia |
| `Cad_Lista_Legal_Item` (`autopecas_lei_10485`) | 66 | 51 do Anexo I (5 com Ex da Tipi) e 15 do Anexo II (com o texto de "próprio para"); vigência inicial 01/11/2002 |
| `Cad_Ecf_Parametro` | 1 | `limite_moeda_exterior_anual` = R$ 120.000, vigência 01/01/2026 |

Total: **136 linhas em 3 arquivos de dados e 3 de regra de texto** (pasta `Carga35`). Ficam sem carga: as habilitações `ipi_suspensao` e `ipi_apuracao` (ligadas pela empresa), as classificações do Confia e do OEA, o Anexo II da IN 2.333 e os cadastros de habilitação do REIDI e do IPI (do usuário).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: ficaram de fora o documento 194 (Q194-1, Q194-3, Q194-4 e Q194-5 sem resposta) e o documento 193 (sem campo).
2. **`Origem_Dados_Entrada` ficou em `Mov_Documento_Fiscal`**, só no documento recebido; a regra vale também para `Mov_Nota_Fiscal_Entrada` e `Mov_Nfts` por texto, sem campo nelas. A D-N510 pedia "campo e entidades a conferir".
3. **A situação da ciência do indício** tem quatro valores meus (`aberta`, `regularizada_no_prazo`, `vencida_sem_regularizacao` e `sem_direito_ao_prazo`), porque o documento 185 listava os campos sem os valores; os 9 campos incluem `Situacao_Dado`, `ID_Instancia_Aprovacao` e `Observacao`, como em `Mov_Condicao_Devedor_Contumaz`.
4. **`ID_Participante_Situacao_Cnpj_Versao`**, em `Cad_Participante_Situacao_Cnpj_Motivo`, aponta para a versão da situação (a tabela física `_Versao`).
5. **Os códigos das cinco classificações do Sintonia** (`sintonia_a_mais`, `sintonia_a`, `sintonia_b`, `sintonia_c`, `sintonia_d`) são meus; a IN dá as letras e as faixas.
6. **Vigência dos 24 motivos** (10/07/2026) fica no texto do fundamento, porque `Cad_Classe_Sistema` não tem vigência; o inciso é o código (`XVI_a` a `XVI_d` nas alíneas).
7. **`Tipo_Ecf`** é o campo do 0000 gravado; o ERP sugere e o contador confirma.
8. **Os avisos do Motor continuam registrados e não programados**: art. 51, suspensão do IPI, liga e desliga, Confia, Sintonia, REIDI e os 11 do registro 0000.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto nos documentos | Documentos 189 a 192 (1.137 e 12.759) mais a ciência do indício (1 entidade e 9 campos) e a origem XML (1 campo): **1.138 entidades e 12.769 campos**, como o modelo regerado; 3.345 referências (+8) |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.362 tabelas, 3.569 chaves estrangeiras e 10.587 comentários; as colunas novas existem em `mov_documento_fiscal`, e as três tabelas novas foram criadas |
| T-SQL (analisador sqlglot, oito arquivos) | Lido sem erro; 19.179 comandos (45 a mais). **Não equivale a executar num SQL Server.** |
| Ondas | `Cad_Participante_Situacao_Cnpj_Motivo` na onda 0; `Mov_Ecf_Periodo` e `Mov_Ciencia_Indicio_Infracao` na onda 3; nenhuma chave nova espera onda de destino (79, como antes) |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** Q179-1 e a parte 2 da Q179-3 (planilha do leiaute 11, também Q152-4), Q194-1 e Q194-3 a Q194-5 (documento 194), Q93-6 (indicador de atividade rural) e o envio das perguntas 27 a 29 à Receita (os textos estão nos zips dos documentos 193 e 194).
- **Contador:** C1 a C225 do documento 188 (entre elas C216 a C225 dos documentos 189 a 194).
- **Equipe e fontes oficiais:** seção 3 do documento 38; Portaria MF 2.813.
- **Fila de desenho:** documentos 159 (43 artigos da LC 227 e os mal extraídos) e 160 (parâmetros das outras obrigações).

# 7. Limites

- Os dados das cargas (24 motivos, 66 linhas da Lei 10.485 e 21 valores da ECF) vêm dos meus documentos 190 e 192, que li dos PDFs e do manual; **não conferi no DOU** nem no Planalto de novo.
- Os códigos e os valores de enumeração marcados como leitura minha na seção 4 não vêm de norma.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1 e 10 do dicionário e o 195 seguem só nos Word desta entrega.
