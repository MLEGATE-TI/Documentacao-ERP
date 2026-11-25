# Consolidação da Revisão 58 — Documento 256

*Você escreveu **«consolidar»**. Apliquei ao dicionário **só o que já estava aprovado** e esperava a aplicação: o **parâmetro global do boleto com ou sem Pix** (`Cad_Cobranca_Parametro`, D-N666) e o valor **`debito_veicular`** em `Produto` (D-N675), do documento 250, versão 34. **Uma entidade nova e 6 campos.** Decisão registrada como D-N679.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 57** | **Revisão 58** | **Diferença** |
|---|---|---|---|
| Entidades | 1.268 | **1.269** | +1 (Tesouraria) |
| Campos | 14.928 | **14.934** | +6 (os 6 campos de `Cad_Cobranca_Parametro`; o valor novo de `Produto` é valor de enumeração, não campo) |
| Campos de referência (FK) | 3.780 | 3.780 | 0 (o parâmetro é global e não aponta para outra entidade) |
| Entidades mestres | 275 | **276** | +1 (`Cad_Cobranca_Parametro`, com vigência) |
| Domínios de `Cad_Classe_Sistema` | 376 | 376 | 0 |
| Tabelas físicas (DDL) | 1.543 | **1.545** | +2 (a entidade e a tabela de versão) |
| Chaves estrangeiras (DDL) | 4.055 | **4.056** | +1 (a tabela de versão aponta para a entidade) |
| Índices (DDL) | 4.147 | **4.148** | +1 |
| Comentários (DDL) | 12.643 | **12.648** | +5 |
| Comandos do T-SQL | 22.389 | **22.398** | +9 |
| Chaves opcionais que esperam a onda de destino | 93 | 93 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Tesouraria 13 | Tesouraria **14** (a Fase 0 continua na 102) | |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.545 tabelas, 4.056 chaves estrangeiras, 12.648 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**, depois de uma decisão minha explicada na seção 5.

# 2. O que entrou

| **Decisão** | **Onde ficou no dicionário** |
|---|---|
| Boleto com ou sem Pix é **opção do usuário e vale para todos os boletos** (Q250-16 a, D-N666, R129) | **`Cad_Cobranca_Parametro`** (módulo 09, anexo, seção 16): `ID_Cobranca_Parametro`, `ID_Cobranca_Parametro_Versao`, **`Boleto_Com_Pix`** (booleano: verdadeiro = todo boleto **novo** sai com Pix; falso = sai sem Pix) e a vigência padrão (`Vigencia_Inicio`, `Vigencia_Fim` e `Motivo_Vigencia`). A mudança fica registrada e vale só para os boletos novos. |
| **Débito veicular** do Bradesco, para pagamento (Q250-23, Q250-66, D-N674 e D-N675, R137) | Valor **`debito_veicular`** no campo `Produto` de **`Cad_Banco_Driver_Capacidade`** (a matriz) e de **`Cad_Conta_Bancaria_Canal`** (o canal da conta). Sem canal, o produto fica desligado, como os demais. |

# 3. O que não entrou

- **`Meio_Transmissao` no canal da conta (Q250-67):** a pergunta **continua aberta**, então o campo não foi aplicado. Se você aprovar, entra 1 campo opcional no canal (14.935 campos).
- **7º campo de dias do Pix do boleto em atraso (Q250-62):** continua aberta. Se você escolher um número fixo de dias (opção b), entra um campo em `Cad_Cobranca_Parametro`; pela opção que recomendei (o mesmo prazo do boleto) não muda nada.
- **Valores do SISDEB** (`debito_automatico` e `retorno_debito_automatico`): só com contrato, na fase 2 (D-N675).
- **Todo o resto do documento 254:** são 35 perguntas abertas, por banco; o que depende da sua resposta ou do gerente do banco continua fora do dicionário.

# 4. A Carga

**Não há Carga58.** O parâmetro do boleto não tem linha inicial: é uma escolha sua. Até existir uma linha, o motor trata o boleto como **sem Pix** (leitura minha, a opção mais segura, porque o boleto nunca deixa de ser emitido). O valor `debito_veicular` é estrutura da enumeração, não dado de carga.

# 5. Leituras minhas e limites do que apliquei

- **Só o aprovado entrou.** Li «consolidar» como «aplique o que já está decidido». As perguntas abertas (Q250-62 e Q250-67) não foram tratadas como aprovadas pela recomendação, ao contrário do que foi feito na revisão 56, quando você pediu o documento completo pelas recomendações.
- **Entidade isolada aceita de propósito.** A auditoria apontou `Cad_Cobranca_Parametro` como entidade sem chave estrangeira de entrada nem de saída. Acrescentei-a à lista de aceitos de propósito, no mesmo critério de outras tabelas de parâmetro (`Cad_Obrigacao_Acessoria`, `Cad_Comex_Codigo`): é um parâmetro global, lido pelo motor, sem empresa nem conta. Se um dia a Mlegate quiser o parâmetro por empresa ou por conta, entra um campo opcional de referência e a entidade deixa de ser isolada.
- **Sem linha, sem Pix.** Ver a seção 4.
- **Percentuais do inventário (documento 246):** não foram revistos com esta aplicação.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** as 35 perguntas do envio bancário, por banco, no documento 254 (em especial a **Q250-62**, a **Q250-67** e a **Q250-64**, que mexem na estrutura), os **três PDFs da Caixa** bloqueados (Q250-56) e os demais itens do documento 38.
- **Contador:** a **C374** (FGTS Digital: vencimento do dia 20 e multa de 40% da rescisão), no documento 188.

Próximos números: D-N680, contador C375, documento 252 (FGTS, reservado), documento 257, R141, Q250-68, Q251-9, Q246-9, Q248-7, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.56.
