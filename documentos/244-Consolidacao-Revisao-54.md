# Consolidação da Revisão 54 — Documento 244

*Você escreveu "consolidar". Li como no D-N603 e na D-N622: **o único item sem aplicar era o desenho do documento 243** (valor aproximado dos tributos, Lei 12.741), com as suas respostas D-N624, D-N625 e D-N626. Entrou só ele. **Se não era isso que você queria aprovar, me diga que eu desfaço** (a revisão 53 está guardada).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 53** | **Revisão 54** | **Diferença** |
|---|---|---|---|
| Entidades | 1.242 | **1.243** | +1 (`Cad_Percentual_Tributos_Aproximados`) |
| Campos | 14.448 | **14.460** | +12 (10 da entidade nova e 2 no item da nota de saída) |
| Campos de referência (FK) | 3.703 | **3.706** | +3 (NCM, NBS e filial) |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 |
| Tabelas físicas (DDL) | 1.508 | **1.509** | +1 |
| Chaves estrangeiras (DDL) | 3.969 | **3.972** | +3 |
| Índices (DDL) | 4.060 | **4.064** | +4 |
| Comentários (DDL) | 12.189 | **12.200** | +11 (a chave primária não leva comentário) |
| Comandos do T-SQL | 21.727 | **21.746** | +19 |
| Chaves opcionais que esperam a onda de destino | 87 | 87 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Contabilidade & Fiscal 71, CRM & Vendas 28 | Contabilidade & Fiscal **72**, CRM & Vendas **29** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.509 tabelas, 3.972 chaves estrangeiras, 12.200 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**.

# 2. O que entrou

| **Id** | **Decisão** | **Onde ficou no dicionário** |
|---|---|---|
| Q243-1 (D-N624) | Guardar o valor aproximado dos tributos do item (`vTotTrib`, Lei 12.741); o percentual é estimado todo mês | `Mov_Nota_Fiscal_Saida_Item.Valor_Tributos_Aproximados` e `Percentual_Tributos_Aproximados` (**+2 campos**, opcionais); o total da nota segue derivado; a fonte vai em `Informacoes_Complementares` |
| Q243-2 (D-N625) | O percentual varia por NCM, por NBS e por filial ("pode ter variação por estado") | **Entidade nova** `Cad_Percentual_Tributos_Aproximados` (Contabilidade & Fiscal, parâmetro com vigência): `ID_Classificacao_Mercadoria` (NCM) ou `ID_NBS`, exatamente um dos dois, mais `ID_Filial` (opcional; vazio vale para todas) |
| Q243-3 (D-N626) | O contador mantém o percentual: valida a tabela e só altera as linhas que mudam; não há recarga mensal | Cada linha tem a sua vigência; só a que muda ganha linha nova. `Percentual_Total` (um só percentual), `Fonte` e `Competencia_Ultima_Validacao` (competência em que o contador conferiu a linha) |
| NFS-e | O valor da carga tributária já era guardado na NFS-e | `Mov_Nfse_Rps.Percentual_Carga_Tributaria` e `Fonte_Carga_Tributaria` ganham texto: o percentual vem da mesma tabela, pela NBS; **0 campos** |

# 3. A entidade nova, campo a campo

| **Campo** | **Tipo** | **Para que serve** |
|---|---|---|
| `ID_Percentual_Tributos_Aproximados` | identificador | Identidade da linha |
| `ID_Classificacao_Mercadoria` | referência (`Cad_Classificacao_Mercadoria`), opcional | NCM do produto |
| `ID_NBS` | referência (`Cad_NBS`), opcional | NBS do serviço; exatamente um dos dois, por regra do Motor |
| `ID_Filial` | referência (`Cad_Filial`), opcional | Filial emissora; vazio vale para todas; a linha da filial prevalece sobre a geral (leitura minha) |
| `Percentual_Total` | número | O percentual aproximado da carga tributária total |
| `Fonte` | texto (até 100) | Nome da tabela de origem (por exemplo, IBPT), que a lei manda informar na nota |
| `Competencia_Ultima_Validacao` | data, opcional | Competência em que o contador conferiu a linha (sugestão minha, para avisar quando a tabela do mês não foi validada) |
| `Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia` | data, data, texto | Janela de vigência da linha, como em `Cad_Percentual_Presuncao` |

# 4. Leituras minhas e limites do que apliquei

- **Carga vazia.** A fonte da tabela não foi dita; a D-N626 diz só que o contador define o percentual. Sem linha para o NCM ou a NBS e a filial, o `vTotTrib` fica em branco, o que o esquema permite (campo opcional). Quando o contador entregar a tabela (planilha ou IBPT), a carga entra como o documento 14 manda para parâmetros com vigência.
- **Um só percentual.** Você não disse se a fonte separa federal, estadual e municipal; guardei o total, que é o que o XML leva. Se a fonte separar, o contador informa a soma.
- **Exatamente um de NCM ou NBS** e a **unicidade** (NCM ou NBS, filial e `Vigencia_Inicio`) são regra do Motor e da carga; o gerador de DDL não cria restrição, como em `Cad_Taxa_Depreciacao_Cbs` (Q239-4).
- **Prevalência da filial** sobre a linha geral na mesma data e o aviso de tabela não validada no mês são leituras minhas; se preferir outra regra, é troca de texto.
- **Documento 243:** o texto da Q243-1 nele (1 campo, 0 entidades) ficou como histórico; vale o documento 14, D-N624 a D-N627.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 5. O que fica aberto

- **Você:** Q239-4, Q234-3, Q228-1 e Q228-2, a "Lista Vigente" da Res. 553 (art. 2º) e os demais itens do documento 38. **A fonte do percentual** (de onde o contador tira a tabela) não é pergunta nova: entra na carga quando ele a entregar.
- **Contador:** nada novo (C1 a C364).

Próximos números: D-N628, contador C365, documento 245, Q243-4, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.52.
