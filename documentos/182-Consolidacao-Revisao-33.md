# Consolidação da Revisão 33 — Documento 182

*Relatório do que entrou no dicionário com o seu "consolidar" de 06/11/2026. Você não escolheu escopo; apliquei **só o que você aprovou e ainda não estava no dicionário**: o bônus de adimplência da CSLL na baixa do título (documentos 180 e 181; D-N491 e D-N492).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 32 | Revisão 33 | Diferença |
|---|---|---|---|
| Entidades | 1.107 | 1.107 | 0 |
| Campos | 12.404 | 12.406 | +2 |
| Campos de referência (FK) | 3.241 | 3.242 | +1 |
| Entidades mestres | 217 | 217 | 0 |
| Referências genéricas | 61 | 61 | 0 |
| Tabelas físicas (DDL) | 1.324 | 1.324 | 0 |
| Chaves estrangeiras (DDL) | 3.458 | 3.459 | +1 |
| Índices (DDL) | 3.546 | 3.547 | +1 |
| Comentários (DDL) | 10.266 | 10.268 | +2 |
| Entidades com FK que espera a onda de destino | 75 | 75 | 0 |

Sem entidade nova e sem carga nova.

# 2. O que entrou

| Onde | Mudança |
|---|---|
| `Mov_Bonus_Adimplencia_Csll` (documento 10) | **+2 campos**, ambos opcionais: `ID_Baixa` (referência a `Mov_Titulo_Baixa`: a baixa em que o desconto da CSLL foi dado) e `Valor_Desconto_Na_Baixa` (cópia do `Valor_Desconto` da baixa; é o valor que a ECF usa). A descrição de `Situacao` diz agora o que são calculado, confirmado e perdido, e a de `Pago_A_Vista_Ate_Vencimento` diz que vem da baixa ligada. |
| `Mov_Titulo_Baixa.Valor_Desconto` (documento 8) | Só texto: na baixa de título de guia de CSLL com bônus, a guia entra pelo valor total, `Valor_Baixado` é o valor total do título, este campo guarda o desconto e o dinheiro que saiu é `Valor_Financeiro`. |
| Texto da entidade no documento 10 | A Q140-5 passa a "respondida para o ERP" (cada apuração calcula o seu bônus; guia pelo valor total; desconto na baixa; estimativas abatem o valor total da guia no ajuste anual; `Vale_Estimativa_Mensal` não é criado). |

**Exemplo (documento 181):** guia de R$ 500.000,00, bônus de R$ 10.000,00. Na baixa: `Valor_Baixado` de R$ 500.000,00, `Valor_Desconto` de R$ 10.000,00 e dinheiro de R$ 490.000,00. O bônus liga à baixa, copia o desconto e fica à disposição da ECF.

**Três avisos do Motor** (sem bloqueio) ficam **registrados e ainda não programados**: baixa de título de CSLL com desconto e sem bônus previsto; bônus calculado e baixa sem desconto até o vencimento (situação `perdido`); desconto da baixa diferente do calculado.

# 3. O que ficou de fora

- **Documento 158** (B3: compras governamentais e Zona Franca de Manaus e áreas de livre comércio): Q158-1 a Q158-13 sem resposta.
- **Documento 177** (transação de cartão e as sete datas): Q177-1 a Q177-5 sem resposta.
- **Documentos 179 e 180**: não são desenho do dicionário (a consulta à Receita e o detalhe das perguntas).
- **Indicador de atividade rural** (Q93-6): o desenho da linha do catálogo de parâmetros ainda não foi feito.

# 4. Como conferi

| Conferência | Resultado |
|---|---|
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.324 tabelas e 3.459 chaves estrangeiras; as colunas `id_baixa` e `valor_desconto_na_baixa` existem em `mov_bonus_adimplencia_csll` |
| T-SQL (analisador sqlglot, oito arquivos) | Lido sem erro; o aumento é de 4 comandos (1 chave estrangeira, 1 índice e 2 comentários). **Não equivale a executar num SQL Server.** |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 5. O que continua aberto

- **Q140-6 (contador):** conta do bônus, exclusão na Parte A do e-LALUR, presumido e PIS/Cofins, momento do reconhecimento e linha da ECF. O ERP não lança o bônus até ele responder (Q180-2).
- **Receita:** Q140-5b, 5d e 5e, na pergunta 26 do documento 179 (que também precisa da sua decisão: Q179-1 a Q179-3).
- **Você:** Q180-3 (o texto do art. 41 da LC 225 ou o ato da Receita), Q158-1 a Q158-13, Q177-1 a Q177-5, a tabela de cClass da NFGás, a planilha do leiaute 11 (Q152-4) e os textos da Portaria MF 3.074/2026 e da conjunta MF/CGIBS 14/2026.
- **Fila de desenho:** documento 159 (43 artigos da LC 227 e os mal extraídos) e documento 160 (parâmetros das outras obrigações).

# 6. Limites

- O texto da LC 225 e a planilha da ECF não estão no meu ambiente; o uso do desconto na ECF depende da Q140-6 e da resposta da Receita.
- A leitura "baixar pelo valor pago = `Valor_Baixado` é o valor total do título" é a da Q181-1, que você aprovou ao seguir a recomendação.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 8 e 10 do dicionário seguem na versão da revisão 32 no Project e estão atualizados nos Word desta entrega.
