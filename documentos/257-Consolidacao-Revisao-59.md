# Consolidação da Revisão 59 — Documento 257

*Você escreveu **«consolidar»**. Apliquei ao dicionário **tudo o que você já tinha aprovado** e esperava a aplicação: o **parâmetro do convênio de folha** (`Cad_Rh_Parametro_Pagamento_Folha`, Q250-73), o campo **`Meio_Transmissao`** no canal da conta (Q250-67) e o campo **`Layout_Cnab`** na carteira (Q250-63). Resultado: **1.270 entidades e 14.944 campos**. Não ficou nenhum item aprovado de fora.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 58** | **Revisão 59** | **Diferença** |
|---|---|---|---|
| Entidades | 1.269 | **1.270** | +1 (Folha & RH) |
| Campos | 14.934 | **14.944** | +10 (8 do parâmetro de folha, 1 em `Cad_Conta_Bancaria_Canal` e 1 em `Cad_Conta_Bancaria_Carteira`) |
| Campos de referência (FK) | 3.780 | **3.782** | +2 (o parâmetro aponta para `Cad_Empresa` e para `Cad_Conta_Bancaria_Canal`) |
| Entidades mestres | 276 | **277** | +1 (`Cad_Rh_Parametro_Pagamento_Folha`, com vigência) |
| Domínios de `Cad_Classe_Sistema` | 376 | 376 | 0 |
| Tabelas físicas (DDL) | 1.545 | **1.547** | +2 (a entidade e a tabela de versão) |
| Chaves estrangeiras (DDL) | 4.056 | **4.059** | +3 (as duas do parâmetro e a da tabela de versão) |
| Índices (DDL) | 4.148 | **4.151** | +3 |
| Comentários (DDL) | 12.648 | **12.657** | +9 |
| Comandos do T-SQL | 22.398 | **22.415** | +17 |
| Chaves opcionais que esperam a onda de destino | 93 | 93 | 0 (o parâmetro está na onda 6 e aponta para as ondas 0 e 1) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Tesouraria 14, Folha & RH 30 | Tesouraria **15**, Folha & RH **31** (a Fase 0 continua na 102) | |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.547 tabelas, 4.059 chaves estrangeiras, 12.657 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria fechou com **0 achados em aberto**, sem acrescentar nenhuma entidade à lista de aceitos de propósito (o parâmetro de folha tem chaves estrangeiras de saída).

# 2. O que entrou

| **Decisão** | **Onde ficou no dicionário** |
|---|---|
| **Convênio de folha em parâmetro**, com troca de banco a qualquer momento, o usuário escolhe o canal a cada folha (Multipag ou Folha no Bradesco) e qualquer banco paga (Q250-71, Q250-72 e Q250-73; D-N686 e D-N689; R148 e R151) | **`Cad_Rh_Parametro_Pagamento_Folha`** (módulo 11, anexo, seção 31), com vigência: `ID_Parametro_Pagamento_Folha`, `ID_Parametro_Pagamento_Folha_Versao`, `ID_Empresa` (opcional; vazio vale para todas), **`ID_Conta_Bancaria_Canal`** (o canal que a folha pode usar), **`Padrao`** (o canal que o ERP sugere; os outros ficam para o usuário escolher) e a vigência padrão. A troca de banco é uma versão nova com data de início; as remessas já enviadas não mudam. |
| **Meio de transmissão** do arquivo (Q250-67; D-N680) | **`Meio_Transmissao`** (opcional) em **`Cad_Conta_Bancaria_Canal`**: {portal_manual, host_a_host, api, van}. No `portal_manual` o ERP gera o arquivo e o usuário o sobe no portal; no `host_a_host` o ERP envia e busca sozinho. |
| **Layout do CNAB por carteira**, com o padrão na conta (Q250-63; D-N688; R150) | **`Layout_Cnab`** (opcional, {240, 400}) em **`Cad_Conta_Bancaria_Carteira`**. Vazio = usa o `Layout_Cnab` da conta; vale só para registros novos. |

# 3. O que não entrou

- **7º campo de dias do Pix do boleto em atraso:** não entrou porque você escolheu o **mesmo prazo do boleto** (Q250-62, R141).
- **Valores do SISDEB e do débito automático** (`debito_automatico` e `retorno_debito_automatico`): só com contrato, na fase 2 (R144).
- **Todo o resto do documento 254:** são 34 perguntas abertas, por banco; o que depende da sua resposta ou do gerente do banco continua fora do dicionário.

# 4. A Carga

**Não há Carga59.** O parâmetro de folha não tem linha inicial: depende de os canais de folha de cada banco estarem cadastrados e ativos, o que só acontece com o contrato (Q250-72). Sem linha, o motor usa o **canal que o usuário escolher** ao processar a folha (R124) ou Pix e TED comuns (R146). Os campos `Meio_Transmissao` e `Layout_Cnab` entram vazios; o vazio significa «não informado» e «usa o da conta», respectivamente.

# 5. Leituras minhas e limites do que apliquei

- **Tudo o que estava aprovado entrou**, e só isso. As perguntas abertas por banco (documento 254) não foram tratadas como aprovadas.
- **`Padrao` não é único por regra do banco de dados.** O dicionário diz que só um canal vigente é o padrão, mas a garantia é regra de validação do ERP, não restrição de tabela (como nos demais parâmetros com vigência).
- **`ID_Empresa` vazio vale para todas as empresas**, como em `Cad_Rh_Parametro_Vencimento_Encargo`.
- **Percentuais do inventário (documento 246):** não foram revistos com esta aplicação.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** as 34 perguntas do envio bancário, por banco, no documento 254, os **três PDFs da Caixa** bloqueados (Q250-56) e os demais itens do documento 38.
- **Contador:** a **C374** (FGTS Digital: vencimento do dia 20 e multa de 40% da rescisão), no documento 188.

Próximos números: D-N691, contador C375, documento 252 (FGTS, reservado), documento 258, R152, Q250-74, Q251-9, Q246-9, Q248-7, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.56.
