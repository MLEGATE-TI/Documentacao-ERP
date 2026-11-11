# Consolidação da Revisão 38 — Documento 203

*Relatório do que entrou no dicionário com o seu "consolidar" de 10/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava no dicionário** depois da revisão 37: o documento 200 inteiro (B0b-2, crédito de quem compra o serviço financeiro, o arrendamento, a antecipação de recebíveis e o plano de saúde dos empregados; Q200-1 a Q200-11, D-N534) e o documento 201 inteiro (documentação dos parâmetros do B0b-2; Q201-1 a Q201-10, D-N536). O documento 202 (B6, regime automotivo) ficou de fora: as Q202-1 a Q202-11 não têm resposta.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 37 | Revisão 38 | Diferença |
|------------------------------------------------------|----------------|----------------|---------------|
| Entidades | 1.155 | 1.165 | +10 |
| Campos | 13.017 | 13.204 | +187 |
| Campos de referência (FK) | 3.404 | 3.445 | +41 |
| Entidades mestres | 232 | 235 | +3 |
| Referências genéricas | 61 | 62 | +1 |
| Domínios de `Cad_Classe_Sistema` | 355 | 355 | 0 |
| Tabelas físicas (DDL) | 1.387 | 1.400 | +13 |
| Chaves estrangeiras (DDL) | 3.636 | 3.680 | +44 |
| Índices (DDL) | 3.727 | 3.771 | +44 |
| Comentários (DDL) | 10.816 | 10.993 | +177 |
| Comandos do T-SQL | 19.567 | 19.845 | +278 |
| Chaves opcionais que esperam a onda de destino | 79 | 80 | +1 |

**10 entidades novas** (182 campos) e **6 existentes alteradas** (2 com campo novo, 4 só com texto ou valor de enumeração), distribuídas assim:

| Decisão | Entidades novas | Campos nelas | Campos novos em existentes |
|------------------------|--------------------------------------|---------|------------------------------|
| Q200-2 (catálogo do crédito do tomador) | 1 (`Cad_Regra_Credito_Tomador`, mestre) | 21 | 0 |
| Q200-3 (empréstimo e Selic) | 0 | 0 | 5 (`Mov_Emprestimo` 3 e `Cad_Serie_Cotacao` 2) |
| Q200-5 (arrendamento) | 2 (`Cad_Arrendamento_Mercantil` 19 e `Mov_Arrendamento_Parcela` 8) | 27 | 0 (valor novo em `Mov_Titulo.Origem_Tipo`) |
| Q200-6 (antecipação de recebíveis) | 2 (`Mov_Antecipacao_Recebivel` 14 e `Mov_Antecipacao_Recebivel_Item` 15) | 29 | 0 |
| Q200-7 (registro do crédito) | 1 (`Mov_Credito_Servico_Regime_Especifico`) | 38 | 0 (dois valores novos em `Mov_Credito_Fiscal.Origem`) |
| Q200-8 (plano de saúde dos empregados) | 2 (`Mov_Rh_Beneficio_Acordo_Coletivo` 11 e `Mov_Rh_Beneficio_Credito_Cbs` 21) | 32 | 0 (texto em `Cad_Criterio_Uso_Preponderante`) |
| Q200-1, Q200-4, Q200-9 a Q200-11 | 0 | 0 | 0 (carga e regras de texto) |
| Q201-2 (documentação e efeito) | 2 (`Cad_Parametro_Documentacao` 21 e `Cad_Parametro_Efeito_Obrigacao` 14, mestres) | 35 | 0 (texto em `Cad_Obrigacao_Parametro_Definicao.Ajuda`) |
| Q201-1, Q201-3 a Q201-10 | 0 | 0 | 0 (regra geral e carga) |
| **Total** | **10** | **182** | **5** |

Três das dez entidades novas têm vigência e viram duas tabelas no DDL (mestres): `Cad_Regra_Credito_Tomador`, `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao`. Por isso as 10 entidades dão 13 tabelas.

# 2. O que entrou, por decisão

## 2.1 Crédito do tomador do serviço financeiro (Q200-1 a Q200-4, Q200-10)

- **`Cad_Regra_Credito_Tomador`** (21 campos, mestre): o catálogo legal do crédito de quem compra o serviço de fornecedor em regime específico, com a forma de cálculo, o regime de caixa, a proporção do art. 291 e as vedações (cooperativa, moeda estrangeira). Carga de 28 regras (26 de lei e 2 de decreto, nove vedações), com vigência desde 01/01/2027 e **aviso** para pagamento anterior (o ERP avisa, não bloqueia).
- **`Mov_Emprestimo`**: três campos novos (credor, forma de captação e marca de moeda estrangeira). **`Cad_Serie_Cotacao`**: dois campos (`Uso_Legal_Cbs` e `Data_Vencimento_Contrato`), com uma série Selic diária na carga e as séries de DI futuro cadastradas pelo usuário.
- **Domínio:** `tipo_emprestimo` ganha `debenture` e `nota_comercial` (carga; nenhum domínio novo).

## 2.2 Arrendamento e antecipação de recebíveis (Q200-5, Q200-6)

- **`Cad_Arrendamento_Mercantil`** (19) e **`Mov_Arrendamento_Parcela`** (8): o contrato em que a empresa é arrendatária e cada parcela, com o crédito pela parcela inteira (leitura literal do art. 203 da LC 214), os encargos gravados e o aviso de excesso. `Mov_Titulo.Origem_Tipo` ganha `arrendamento_parcela`.
- **`Mov_Antecipacao_Recebivel`** (14) e **`Mov_Antecipacao_Recebivel_Item`** (15): a antecipação, o deságio e os recebíveis cedidos; a baixa usa o `ID_Tipo_Baixa` que o usuário escolhe.

## 2.3 Registro do crédito e plano de saúde dos empregados (Q200-7 a Q200-9, Q200-11)

- **`Mov_Credito_Servico_Regime_Especifico`** (38): a memória de cálculo (o que foi pago, deduções, base, alíquotas gravadas, proporção e vedações), com `ID_Origem` genérico (a referência genérica nova). O crédito nasce em `Mov_Credito_Fiscal` com duas origens novas: `servico_financeiro_tomador` e `beneficio_empregado`.
- **`Mov_Rh_Beneficio_Acordo_Coletivo`** (11) e **`Mov_Rh_Beneficio_Credito_Cbs`** (21), em Folha & RH: o acordo com cláusula compulsória e o crédito do benefício pelo art. 337 do Decreto, com o desconto da folha do ERP como fonte. Os vales só registram o que o fornecedor informar; a declaração à RFB só registra situação, data e protocolo, até o ato conjunto.

## 2.4 Documentação dos parâmetros (Q201-1 a Q201-10)

- **`Cad_Parametro_Documentacao`** (21, mestre) e **`Cad_Parametro_Efeito_Obrigacao`** (14, mestre): o efeito de cada valor do parâmetro em cada obrigação. Carga: 41 parâmetros (12 da regra, 20 chaves de decisão, 4 existentes que o B0b-2 lê e 5 leituras provisórias) e 58 efeitos (51 na escrituração do IBS e da CBS, 6 na DeRE e 1 no eSocial).
- **Regra geral (Q201-3):** nenhum parâmetro entra sem documentação do efeito e da obrigação. As cinco leituras provisórias viram parâmetros por empresa, com padrão visível e aviso a cada uso (Q201-4).
- **`Cad_Obrigacao_Parametro_Definicao`**: seis linhas novas no catálogo central e o texto de `Ajuda`, que passa a ser o resumo. **`Cad_Obrigacao_Acessoria`**: a linha `ESOCIAL`.
- **Depois (Q201-9):** os quatro cadastros e as regras do B4, e as 61 linhas do catálogo, em documentos seguintes.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|----------------------------------|---------|---------------------------------------------------------|
| `Cad_Classe_Sistema` (valores novos) | 2 | `debenture` e `nota_comercial` em `tipo_emprestimo` |
| `Cad_Regra_Credito_Tomador` | 28 | 26 de lei, 2 de decreto, nove vedações; vigência desde 01/01/2027 |
| `Cad_Serie_Cotacao` | 1 | Selic diária; criar só se a série ainda não existir |
| `Cad_Obrigacao_Acessoria` | 1 | `ESOCIAL`; início em 01/01/2026 (uso no ERP, não a data legal) |
| `Cad_Obrigacao_Parametro_Definicao` | 6 | uma do catálogo das 28 regras e cinco das leituras provisórias |
| `Cad_Parametro_Documentacao` | 41 | |
| `Cad_Parametro_Efeito_Obrigacao` | 58 | ECD e ECF sem efeito documentado até a C246 |

Total: **137 linhas em 7 arquivos de dados** (pasta `Carga38`, com LEIA-ME). Ordem de carga: `Cad_Obrigacao_Acessoria` (ESOCIAL) e `Cad_Parametro_Documentacao` antes de `Cad_Parametro_Efeito_Obrigacao`.

# 4. Leituras minhas que aguardam a sua confirmação

# 1. **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: os documentos 200 e 201 inteiros. O documento 202 ficou de fora porque as Q202-1 a Q202-11 não têm resposta. 2. **A chave opcional `Cad_Arrendamento_Mercantil.ID_Contrato`** (para `Cad_Gestao_Contrato`, da onda 5) **está no modelo e conta nas 3.445 referências.** O documento 200 dizia que ela ficava fora da contagem, o que não confere com o total aprovado. Como é opcional e aponta para onda posterior, o DDL a cria no ALTER TABLE da onda 5, e a lista do documento 31 passou de 79 para 80 chaves. 3. **Módulos:** as seis entidades do B0b-2 que não são de pessoal e as duas da documentação ficam em Contabilidade & Fiscal (onda 3); as duas do plano de saúde, em Folha & RH (onda 6). 4. **Vigência de partida das cargas:** 01/01/2027 para as 28 regras (como as alíquotas do B4) e 01/01/2026 para `ESOCIAL`, todas provisórias; o contador valida (C239 a C247, documento 188). 5. **Alertas do gerador de DDL:** o gerador acusa sete campos de texto sem tamanho em chave única (o documento 31 dizia cinco). Um é novo: `Cad_Parametro_Efeito_Obrigacao.Quando_Valor` (texto opcional na identidade). Mantive o desenho aprovado; declarar `texto (n)` é decisão sua. 6. **O documento 202 continua só proposta** e, depois da sua observação de hoje (diferença de tributação por combustível e potência do motor; D-N539), pode mudar antes da aprovação.

# 5. Como conferi

| Conferência | Resultado |
|--------------------------------------------------|--------------------------------------------------|
| Contagem de entidades e campos contra o previsto nos documentos 200 e 201 | 1.155 + 10 entidades e 13.017 + 182 + 5 campos: **1.165 entidades e 13.204 campos**, como o modelo regerado; 3.445 referências (+41) e 355 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 62 referências genéricas (+1) |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.400 tabelas, 3.680 chaves estrangeiras e 10.993 comentários conferidos no banco; as 10 tabelas novas e as 3 de versão foram criadas |
| T-SQL (analisador sqlglot, oito arquivos de onda e os comentários) | Lido sem erro; 19.845 comandos (278 a mais: 13 tabelas, 44 chaves, 44 índices e 177 comentários). **Não equivale a executar num SQL Server.** |
| Ondas | Oito entidades na onda 3 e duas na onda 6; uma chave opcional nova espera a onda de destino (80) |
| Carga | 137 linhas; as 28 regras e os 41 parâmetros foram conferidos contra os CSV dos documentos 200 e 201; todas provisórias |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** as Q202-1 a Q202-11 (e a observação sobre combustível e potência, D-N539); o manual oficial da DeRE e o ato do fator de redução (Q198-12); o texto oficial da MP 1.399/2026 (Q196-10); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9 (sem efeito no dicionário).
- **Contador:** C1 a C255 do documento 188 (entre elas C239 a C247 do B0b-2 e da documentação, e C248 a C255 do B6).
- **Equipe e fontes oficiais:** seção 3 do documento 38; Portaria MF 2.813.
- **Fila de desenho:** o B7 (marketplace) segue sem desenho; a documentação dos parâmetros do B4 e das 61 linhas do catálogo está para depois (Q201-9).

# 7. Limites

- O desenho do B0b-2 vem da LC 214 (artigos de crédito do tomador, nos trechos citados no documento 200) e do Decreto 12.955; **não conferi no DOU**, e o ato conjunto da RFB e do CGIBS ainda não foi publicado.
- Cinco leituras do documento 200 são minhas (Selic sobre o saldo do principal, detentor do título, base do arrendamento financeiro, curva DI e crédito em 2026); as 28 regras nascem provisórias.
- A documentação dos parâmetros (documento 201) cobre só os 41 do B0b-2; ECD e ECF ficam sem efeito até a resposta do contador.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1, 8, 10 e 11 do dicionário, o 200, o 201 e o 203 seguem só nos Word desta entrega.
