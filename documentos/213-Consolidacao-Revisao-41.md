# Consolidação da Revisão 41 — Documento 213

*Relatório do que entrou no dicionário com o seu "consolidar" de 11/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou na D-N553 e ainda não estava aplicado**: o documento 212 inteiro (B7, marketplace e plataformas digitais; Q212-1 a Q212-13).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 40 | Revisão 41 | Diferença |
|---|---|---|---|
| Entidades | 1.198 | 1.201 | +3 |
| Campos | 13.738 | 13.801 | +63 |
| Campos de referência (FK) | 3.554 | 3.568 | +14 |
| Entidades mestres | 244 | 245 | +1 |
| Referências genéricas | 62 | 62 | 0 |
| Domínios de `Cad_Classe_Sistema` | 360 | 360 | 0 |
| Tabelas físicas (DDL) | 1.442 | 1.446 | +4 |
| Chaves estrangeiras (DDL) | 3.798 | 3.813 | +15 |
| Índices (DDL) | 3.889 | 3.904 | +15 |
| Comentários (DDL) | 11.519 | 11.579 | +60 |
| Comandos do T-SQL | 20.649 | 20.743 | +94 |
| Chaves opcionais que esperam a onda de destino | 81 | 81 | 0 |

**3 entidades novas** (57 campos, todas em Contabilidade & Fiscal e na onda 3) e **3 existentes alteradas** (uma com 6 campos novos e duas só com valor de enumeração ou texto). Só `Cad_Participante_Plataforma_Fornecedor` tem vigência e vira duas tabelas no DDL; por isso as 3 entidades dão 4 tabelas.

# 2. O que entrou

- **`Cad_Participante_Plataforma_Fornecedor`** (17 campos, mestre): o vínculo entre a plataforma e o fornecedor, visto da empresa do ERP. Guarda a opção da plataforma (`nenhuma`, `emite_e_paga` ou `substituta_tributaria`), a anuência do fornecedor, a condição de contribuinte informada pela administração e se a plataforma calcula pela alíquota de referência. Serve às duas pontas pelo `Papel_Empresa` (a empresa é a plataforma ou vende por ela). **Não guarda a responsabilidade**, que é da operação.
- **`Mov_Plataforma_Operacao`** (27 campos): uma linha por operação intermediada, com quem é quem, o documento fiscal, o fundamento da responsabilidade da plataforma em **um só valor de 8** (`Responsabilidade_Plataforma`), quem decidiu o valor, a regra de apuração do débito, a informação do art. 22, § 5º, os dois marcadores de split (sem cálculo) e quem responde pelos acréscimos.
- **`Mov_Plataforma_Operacao_Tributo`** (13 campos): uma linha por imposto (CBS ou IBS), com o devido, o pago pela plataforma, a alíquota aplicada, a diferença e seu sentido, a parte que paga ou recebe, o título e o espelho da CBS.
- **`Cad_Empresa_Perfil_Fiscal`** (6 campos novos, de 21 para 27): `Eh_Plataforma_Digital`, os quatro `Controla_*` (cobrança, pagamento, termos e condições, entrega) e `Atividade_Unica_Excluida`.
- **Sem campo novo:** `Cad_Participante_Classe.Classe` ganha `plataforma_digital` e `importador` (Q116-3, que ficara de fora); a descrição de `Mov_Documento_Fiscal.ID_Participante_Emitente` passa a dizer que, no documento emitido pela plataforma, ele aponta o fornecedor em cujo nome o documento sai.
- **Anexo 54 do documento 10:** as 3 entidades, as 12 regras do Motor, os 13 avisos e as cargas de partida.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Parametro_Legal_Ibs_Cbs` | 2 | `prazo_emissao_plataforma_dias` = 30 e `percentual_receita_nanoempreendedor_plataforma` = 25 |
| `Cad_Parametro_Documentacao` | 2 | Documentação dos dois parâmetros, pela regra da Q201-3 |
| Regras R1 a R12 do Motor (texto) | 12 | CSV de leitura; a gravação em `Cad_Motor_Regra` é do carregador do Motor |
| Avisos 1 a 13 do Motor (texto) | 13 | CSV de leitura |

Total: **29 linhas em 4 arquivos de dados** (pasta `Carga41`, com LEIA-ME). Ordem: `Cad_Parametro_Legal_Ibs_Cbs` antes de `Cad_Parametro_Documentacao`, ambas depois da Carga38, da Carga39 e da Carga40.

**Fora da carga, de propósito:** `Cad_Parametro_Efeito_Obrigacao` dos dois parâmetros, porque a informação das operações da plataforma (art. 22, § 5º) ainda não tem obrigação nem leiaute no Projeto; o split e o PSP (D-N282 e D-N391).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como a D-N553 inteira:** o documento 212, sem corte.
2. **A vigência de partida é 01/01/2027** nas duas linhas de parâmetro e nas regras, como o documento 212 propôs.
3. **O efeito por obrigação dos dois parâmetros ficou sem linha** (ver a seção 3); a documentação entrou.
4. **Regras e avisos vão como CSV de texto**, como as 18 regras do documento 209.
5. **"Hoje não tem, mas temos que prever" (Q212-13)** foi lido como: o B7 entra inteiro no dicionário e a implantação não tem urgência, como o PSP e o split.
6. **A responsabilidade em um só valor e os dois parâmetros seguem provisórios** até o contador responder (C290 e C287 a C295, documento 188, Parte 17).
7. **As somas previstas bateram** (1.201 entidades, 13.801 campos, 3.568 referências e 360 domínios; entidades mestres de 244 para 245). **Alertas do gerador de DDL:** os mesmos sete campos de texto sem tamanho em chave única; nenhum novo. **Nenhuma chave opcional nova** espera a onda de destino (continuam 81).

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto no documento 212 | 1.198 + 3 entidades e 13.738 + 57 + 6 campos: **1.201 entidades e 13.801 campos**, como o modelo regerado; 360 domínios |
| Referências | 3.568 (+14), pela regeneração, como previsto |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 62 referências genéricas (sem mudança) |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.446 tabelas, 3.813 chaves estrangeiras e 11.579 comentários conferidos no banco; as quatro tabelas novas (a das três entidades e a versão da mestre) foram criadas |
| T-SQL (analisador sqlglot, oito arquivos de onda, lotes separados por GO) | Lido sem erro; 20.743 comandos (94 a mais: 4 tabelas, 15 chaves, 15 índices e 60 comentários). **Não equivale a executar num SQL Server.** |
| Ondas | As 3 entidades na onda 3; nenhuma chave opcional nova espera outra onda (81, como antes; continuam as 79 entidades empurradas por módulo posterior) |
| Carga | 29 linhas em 4 arquivos; regras e avisos lidos do próprio documento 212 |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** a lista de autopeças não produzidas (os Anexos I e II das Resoluções Gecex 284 e 285 ou os links do Diário Oficial; Q206-10); o Protocolo ICMS 41/2008 e o regulamento de ST de uma UF (Q209-9); a Q210-1 (dedução de material na base da retenção); a tabela de IPI de 31/12/2025 (documento 207) e a Tipi consolidada (Q205-4); o manual oficial da DeRE e o ato do fator de redução (Q198-12); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9; o ato do art. 414, § 2º, da LC 214 e a portaria MF 2.813.
- **Contador:** C1 a C295 do documento 188 (entre elas C287 a C295, do B7: partes do § 12, prova do controle de elemento essencial, diferença devolvida, precedência dos fundamentos, regime favorecido na substituição, documento em nome do fornecedor, informações do § 5º, split e § 7º, dispensa de inscrição do fornecedor no exterior).
- **Equipe e fontes oficiais:** seção 3 do documento 38 (a Q176-E2, sobre a baixa por cartão ou marketplace, segue com a equipe); o ato conjunto da opção das plataformas (§§ 12 a 14), o leiaute do documento emitido em nome do fornecedor e o regulamento do IBS ainda não foram lidos.
- **Fila de desenho:** o Imposto Seletivo de bebidas, fumígenos e minerais segue sem desenho.

# 7. Limites

- O desenho vem da LC 214 (arts. 22, 23, 26, 64, 95 a 97, com a LC 227) e do Decreto 12.955 (só CBS), no texto que você enviou; **não conferi no DOU**. O regulamento do IBS está ausente, então IBS e CBS na mesma estrutura é leitura minha (Q212-10).
- O ERP não conversa com a Receita nem com o Comitê Gestor: registra o vínculo, a operação e a responsabilidade, calcula o que a lei fecha e avisa; não bloqueia (D-N284). Não calcula split nem trata o PSP (D-N282 e D-N391).
- A ordem de precedência entre os fundamentos de responsabilidade (itens 3 a 7 do 5.4 do documento 212) é leitura minha e vai ao contador (C290).
- O Project continua acima do limite de tamanho, e a documentação passou a ser mantida no repositório GitHub (a gravação nele é manual nesta sessão): os .md desta entrega estão na pasta `Documentacao-ERP-completa`.
