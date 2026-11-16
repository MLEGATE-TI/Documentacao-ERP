# Consolidação da Revisão 44 — Documento 219

*Relatório do que entrou no dicionário com o seu "consolidar" de 16/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava aplicado**, que é só o **documento 218 inteiro, na versão 2.2** (Bloco 1 de combustíveis e usina: o livro de movimentação do posto, o C171 por tanque e a produção da usina; Q218-1 a Q218-17, D-N581). As Q188-7 e Q188-8 (aprovadas em 16/11, D-N584) **não entraram**, porque ainda não têm desenho em campos.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 43 | Revisão 44 | Diferença |
|---|---|---|---|
| Entidades | 1.220 | 1.229 | +9 |
| Campos | 14.154 | 14.261 | +107 |
| Campos de referência (FK) | 3.645 | 3.663 | +18 |
| Entidades mestres | 256 | 259 | +3 |
| Referências genéricas | 63 | 63 | 0 |
| Domínios de `Cad_Classe_Sistema` | 369 | 369 | 0 (2 valores novos em `modulo_fiscal_opcional`) |
| Tabelas físicas (DDL) | 1.476 | 1.488 | +12 |
| Chaves estrangeiras (DDL) | 3.901 | 3.922 | +21 |
| Índices (DDL) | 3.992 | 4.013 | +21 |
| Comentários (DDL) | 11.913 | 12.011 | +98 |
| Comandos do T-SQL | 21.283 | 21.435 | +152 |
| Chaves opcionais que esperam a onda de destino | 84 | 85 | +1 |
| Alertas do gerador de DDL (texto sem tamanho em chave única) | 7 | 8 | +1 |

**9 entidades novas** (107 campos) e **nenhuma entidade existente alterada**. Três têm vigência (tanque, bomba e bico) e viram duas tabelas cada no DDL; por isso as 9 entidades dão 12 tabelas. Oito entidades ficam na onda 3 (Contabilidade & Fiscal) e `Mov_Nota_Fiscal_Entrada_Item_Tanque` (o C171), na onda 4, porque depende do item da nota de entrada.

# 2. O que entrou

**Cadastros do posto (seção 5 do documento 218):**

- **`Cad_Lmc_Tanque`** (14 campos, mestre): número do tanque (até 3 posições, único por filial), capacidade e o combustível que guarda. O produto está no tanque, e não no bico; trocar o produto gera uma versão nova, e as leituras antigas continuam apontando para o mesmo tanque.
- **`Cad_Lmc_Bomba`** (13 campos, mestre): a bomba medidora do 1350. Não usa `Cad_Equipamento_Fiscal`, que exige modelo de documento fiscal.
- **`Cad_Lmc_Bomba_Lacre`** (5 campos): um lacre por linha, com a data de aplicação e a de remoção (o 1360).
- **`Cad_Lmc_Bico`** (9 campos, mestre): liga a bomba ao tanque; guarda o valor máximo do contador, para dividir o 1320 quando o contador passa do máximo.

**Movimento do posto (seção 6):**

- **`Mov_Lmc_Tanque_Dia`** (17 campos): uma linha por tanque e por dia. A pessoa (ou a automação da pista) informa o estoque físico medido no fechamento; o resto o ERP calcula, e o fechamento do dia grava o resultado para o livro fechado não mudar sozinho.
- **`Mov_Lmc_Bomba_Intervencao`** (12 campos): a intervenção do técnico credenciado, que vale para todos os bicos da bomba.
- **`Mov_Lmc_Bico_Leitura`** (10 campos): um trecho de bico por dia; a cada intervenção nasce um trecho novo. O volume vendido não é gravado: é a leitura final menos a inicial e a aferição.
- **`Mov_Nota_Fiscal_Entrada_Item_Tanque`** (4 campos; C171): o combustível recebido pode ir a vários tanques. Substitui o desenho da seção 5.6 do documento 175, que nunca entrou: o tanque agora é referência, e não código.

**Usina (seção 8):**

- **`Mov_Usina_Producao_Dia`** (23 campos): o 1391, por dia, produto e insumo (esmagamento, mel residual, anidro e hidratado, resíduos). O código do produto vem da tabela oficial `cod_prod_usinas`, que já está em `Cad_Efd_Codigo_Estadual`.

**Habilitação (seção 9):** 2 valores novos no domínio aberto `modulo_fiscal_opcional`: `efd_combustivel_lmc_1300` (posto revendedor: 1300, 1310, 1320, 1350, 1360, 1370 e C171) e `efd_usina_1390` (usina: 1390 e 1391). **Nenhum vem ligado**: a empresa liga por filial, com vigência (D-N68).

**Anexo 57 do documento 10:** as 9 entidades, a tabela de como o ERP gera cada registro (seção 7 do documento 218) e os 27 avisos do Motor (A1 a A27; nenhum bloqueia). **Documento 01:** a linha ampliada de `modulo_fiscal_opcional`. **Documento 10, tabela de decisões da EFD:** a linha do C171 e do Bloco 1, que dizia "ficam para um bloco próprio", agora aponta para o documento 218.

**Textos corrigidos ao passar:** o documento 175 (seção 5.6 e Q175-E4) e o Anexo F do documento 167 ganharam uma nota de atualização; o texto original fica como histórico. O documento 218 ganhou uma linha de situação no alto.

# 3. Cargas de partida (provisórias)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Classe_Sistema`: `modulo_fiscal_opcional` | 2 | `efd_combustivel_lmc_1300` e `efd_usina_1390`; nenhum ligado por padrão |
| Avisos do Motor (texto) | 27 | A1 a A27 do documento 218, em CSV de leitura; a gravação em `Cad_Motor_Regra` é do carregador do Motor |

Total: **2 linhas de tabela e 27 de texto**, em 2 arquivos de dados (pasta `Carga44`, com LEIA-ME), depois da Carga43. **Fora da carga, de propósito:** as nove entidades são cadastros e movimentos do cliente, e o limite de variação do estoque (`Limite_Variacao_Percentual`) não tem valor padrão: o posto preenche.

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como o documento 218 (v2.2) inteiro e nada mais**, porque é o único aprovado ainda não aplicado.
2. **As Q188-7 e Q188-8 ficaram fora.** Você aprovou o prazo de guarda do arquivo transmitido (Q188-7) e o parâmetro consolidada ou individualizada por empresa (Q188-8), mas falta o meu desenho em campos; entram no próximo documento de desenho e só depois no "consolidar". A Q188-9 não muda campo, e a Q188-6 continua com você.
3. **O aviso A22 entrou sem a Solução de Consulta Cosit 223/2023**, até você responder a Q218-18 (a perda de até 0,6% da gasolina como custo no lucro real, sem campo novo e sem adição automática ao e-Lalur).
4. **`Mov_Nota_Fiscal_Entrada_Item_Tanque` fica na onda 4**, junto com o item da nota de entrada; as outras 8 ficam na onda 3. A chave opcional `Cad_Lmc_Tanque.ID_Local_Estoque` (o tanque ligado a um local de estoque, só para o aviso A10) espera `Cad_Local_Estoque`, da onda 4; as chaves que esperam a onda de destino passam de 84 para 85.
5. **`Cad_Lmc_Bomba.Numero_Serie` é texto sem tamanho em chave única**, porque o Guia da EFD não fixa o tamanho do número de série. O gerador limita a 200 (D-9) e acusa o oitavo alerta, junto com os sete anteriores; declarar `texto (n)` nos oito é decisão sua.
6. **A descrição dos valores de domínio** da carga é o próprio código com espaços; você ou o contador ajustam o rótulo.
7. **As somas previstas bateram** (1.229 entidades e 14.261 campos, como o ensaio do documento 218; 3.663 referências, 259 mestres, 63 referências genéricas e 369 domínios).
8. **Uma correção minha:** a abertura da seção 3.1 do documento 31 dizia 81 chaves que esperam a onda de destino, mas a tabela já tinha 84 desde a revisão 42; agora diz 85 e confere com a tabela.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto | 1.220 + 9 entidades e 14.154 + 107 campos: **1.229 entidades e 14.261 campos**, como o modelo regerado; 369 domínios |
| Referências | 3.663 (+18, todas nas entidades novas: tanque 4, bomba 1, lacre 1, bico 2, tanque no dia 2, intervenção 1, leitura 2, item por tanque 2 e usina 3) |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 63 referências genéricas (sem mudança); refeita depois do ajuste de texto da tabela de decisões do documento 10 |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.488 tabelas, 3.922 chaves estrangeiras e 12.011 comentários conferidos no banco; as 12 tabelas novas foram criadas. O DDL regerado depois do ajuste de texto é idêntico ao executado (mesma soma de verificação dos arquivos) |
| T-SQL (contagem dos comandos nos oito arquivos de onda e no de comentários) | 21.435 comandos (152 a mais: 12 tabelas, 21 chaves, 21 índices e 98 comentários), lidos por um analisador de T-SQL sem erro. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | 8 entidades na onda 3 e 1 na onda 4; 81 entidades empurradas por módulo posterior (80 + `Mov_Nota_Fiscal_Entrada_Item_Tanque`); 85 chaves opcionais esperam a onda de destino; nenhuma dependência obrigatória nova entre módulos |
| Carga | 2 linhas de tabela e 27 de texto, em 2 arquivos; os 27 avisos lidos do próprio documento 218, na versão aprovada |
| Documentos 31, 29, 14 e 38 | Os quadros do documento 31 (ondas, entidades empurradas e chaves que esperam) foram regerados do modelo, e cada quadro só ganhou a linha nova esperada; os totais foram conferidos por programa contra o modelo |
| Modelo entidade-relacional | Regerado, com 109 diagramas |

# 6. O que continua aberto

- **Você:** a **Q188-6** (aplicar as 21 respostas do contador, seção 1.42 do documento 38); a **Q218-18** (a Solução de Consulta Cosit 223/2023 no aviso A22, seção 1.41); a **Q218-8** (só o Ajuste SINIEF 14/2025 e o 01/92, em fonte oficial); a Q215-5 (os textos oficiais para a carga por UF da ST de autopeças); a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9.
- **Contador:** C1 a C357 do documento 188, com os esclarecimentos que voltaram a ele (C6, C8, C9, C13, C14(f), C22(b), C25, C27 em seu fundamento legal, C28, C29, C208, C209, C227, C232, C249, C261, C262(a), C281, C324 e C325).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.
- **Fila de desenho (minha):** o desenho em campos das **Q188-7** (prazo de guarda do arquivo transmitido) e **Q188-8** (escrituração consolidada ou individualizada por empresa), na seção 1.13 do documento 38; o split payment (adiado por você) e a carga da lista de autopeças não produzidas.

# 7. Limites

- **Nenhum cliente opera posto ou usina hoje** (Q218-E1): o desenho está pronto e **desligado** (D-N68); sem tela nem rotina até haver cliente.
- O Guia Prático da EFD-ICMS/IPI 3.2.4 foi lido inteiro; a Resolução ANP 884/2022 foi conferida no Diário Oficial. O **Ajuste SINIEF 14/2025** segue lido só em fonte não oficial (Q218-8).
- Os **termos de abertura e de fechamento** do livro (Q218-12, C356) e o **vínculo posto-distribuidor** (Q218-14, D-N68) ficaram fora; a folha do LMC é relatório, e não entidade.
- O ERP **registra, calcula o que a norma fecha e avisa; não bloqueia** (D-N284). O aviso A22 entrou sem citar a Solução de Consulta Cosit 223/2023 (Q218-18), e o ERP não faz adição automática da perda ao e-Lalur.
- O Project continua acima do limite de tamanho, e a documentação é mantida no repositório GitHub (a gravação nele é manual nesta sessão): os .md desta entrega estão na pasta `Documentacao-ERP-completa`.
