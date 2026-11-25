# Consolidação da Revisão 56 — Documento 253

*Você escreveu **«consolidar o que temos até aqui»** e, perguntado, escolheu **«Doc 250 completo, pelas recomendações»**: apliquei o **desenho do motor de envio bancário** (documento 250, D-N639 a D-N658) como está, **sem o estoque proativo** (documento 251), e o que o documento marca como «fora» continua fora. Depois você respondeu mais perguntas (Q250-39, 42 e 48 a 53), pediu que o **vencimento do FGTS seja parâmetro** e disse que a **folha pode sair de qualquer conta**: tudo isso **entrou na mesma revisão**. **Se não era isso, me diga que eu desfaço** (a revisão 55 está guardada). Em seguida, como você pediu, as dúvidas ainda abertas foram **agrupadas por banco** no documento 254.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 55** | **Revisão 56** | **Diferença** |
|---|---|---|---|
| Entidades | 1.249 | **1.265** | +16 (15 em Tesouraria e 1 em Folha & RH) |
| Campos | 14.529 | **14.871** | +342 (289 nas 16 entidades novas e 53 em 5 entidades existentes) |
| Campos de referência (FK) | 3.721 | **3.764** | +43 |
| Entidades mestres | 269 | **274** | +5 (driver, canal da conta, carteiras, mapa de ocorrências e parâmetro do vencimento do FGTS) |
| Domínios de `Cad_Classe_Sistema` | 374 | **376** | +2 (`tipo_movimento_remessa_bancaria` e `motivo_baixa_titulo_bancario`, abertos; as cargas vão na Carga56) |
| Tabelas físicas (DDL) | 1.518 | **1.539** | +21 (16 entidades e 5 tabelas de versão) |
| Chaves estrangeiras (DDL) | 3.990 | **4.038** | +48 |
| Índices (DDL) | 4.082 | **4.130** | +48 |
| Comentários (DDL) | 12.263 | **12.589** | +326 |
| Comandos do T-SQL | 21.854 | **22.297** | +443 |
| Chaves opcionais que esperam a onda de destino | 90 | **92** | +2 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Fase 0 100, Tesouraria 12, Folha & RH 29 | Fase 0 **101**, Tesouraria **13**, Folha & RH **30** |  |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.539 tabelas, 4.038 chaves estrangeiras, 12.589 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria rodou de novo sobre os Markdown regerados e fechou com **0 achados em aberto**. Junto com o estoque proativo (que **não** entrou), seriam 1.267 entidades e 14.918 campos.

# 2. O que entrou

| **Decisão** | **Onde ficou no dicionário** |
|---|---|
| Motor de envio bancário para qualquer banco, por driver (D-N639 a D-N650) | **`Cad_Banco_Driver`** (11 campos, vigência), **`Cad_Banco_Driver_Capacidade`** (26 campos: a matriz que mostra ou esconde cada operação), **`Cad_Conta_Bancaria_Canal`** (26 campos, vigência: ambiente, endereço e referência ao cofre, nunca o segredo), **`Cad_Conta_Bancaria_Canal_Webhook`** (14), **`Mov_Banco_Mensagem`** (17) e **`Mov_Remessa_Bancaria_Evento`** (7): a trilha de cada envio. |
| Mapa de ocorrências e baixa do boleto (D-N651, Q250-49 a Q250-53) | **`Cad_Banco_Ocorrencia_Mapa`** (13 campos, vigência): o código do banco vira a ação do ERP e o **motivo da baixa**; **só o pagamento baixa o título** (R107). Domínios novos `tipo_movimento_remessa_bancaria` (13 comandos) e `motivo_baixa_titulo_bancario` (9 motivos). |
| Carteiras e convênios cadastrados por banco (D-N655; sua resposta à Q250-25) | **`Cad_Conta_Bancaria_Carteira`** (14 campos, vigência): o usuário cria o número da carteira e deixa cadastradas as carteiras registradas em cada banco; convênio e variação moram na carteira (leitura minha; R119); `ID_Carteira_Cobranca` no item de cobrança. |
| Boleto sempre em PDF A4, no padrão do banco, por e-mail ou WhatsApp (D-N655) | `ID_Documento_Boleto_Pdf` no item de cobrança (R123). O dicionário **não tem canal de WhatsApp** (Q250-57). |
| Dados do item que só alguns produtos usam (Q250-14, Q250-21 e Q250-48) | **`Mov_Remessa_Bancaria_Item_Cobranca`** (43 campos) e **`Mov_Remessa_Bancaria_Item_Tributo`** (23 campos); +53 campos em 5 entidades existentes (remessa, item de remessa, retorno, item de retorno e extrato). |
| DDA e Pix Automático (D-N652; Q250-17) | **`Mov_Dda_Titulo`** (20), **`Mov_Pix_Recorrencia`** (28), **`Mov_Pix_Recorrencia_Agendamento`** (11) e **`Mov_Pix_Recorrencia_Tentativa`** (9): **desenhados e desligados na matriz até a fase 2** (R115). |
| Certificados de confiança dos bancos | **`Cad_Banco_Certificado_Confianca`** (14 campos). |
| FGTS: pagar e consultar o saldo para a rescisão (D-N655, Q250-35) | O produto `fgts_saldo_rescisorio` na matriz de capacidades (R122); o pagamento do FGTS é só por Pix (R100). O desenho do saldo, do retorno S-5003 e S-5013 e da guia importada é do **documento 252** (ainda reservado). |
| **Vencimento do FGTS em parâmetro** (D-N658; pedido de hoje) | **`Cad_Rh_Parametro_Vencimento_Encargo`** (13 campos, vigência, Folha & RH): empresa (ou todas), tipo de encargo, regra (dia fixo do mês seguinte ou enésimo dia útil), dia, ajuste em dia sem expediente, ato legal, situação do dado e vigência. A tabela de prazos da Fase 0 passou a dizer «dia 20 do mês seguinte (parâmetro; C374)». |
| **Folha paga de qualquer conta, dividida se quiser** (D-N658; pedido de hoje) | **Nenhuma entidade nova**: a conta de débito fica na remessa e uma folha com duas contas vira **duas remessas** (R124). Duas regras minhas na Q250-58: a soma dos itens bate com o líquido da folha, e o mesmo colaborador não aparece em duas remessas da competência sem confirmação. |

# 3. O que não entrou

- **Carga de drivers, matrizes e mapas de ocorrência:** só quando houver o manual de cada banco; a Carga56 leva só os **22 valores dos dois domínios** e **uma linha** do vencimento do FGTS.
- **DDA e Pix Automático ligados:** estão desenhados, mas desligados na matriz até a fase 2 (R115).
- **Estoque proativo** (documento 251, +2 entidades e +47 campos): ficou de fora, como você escolheu.
- **O que o documento marca como «fora»** (Q250-50, aprovada): SISDEB, débito automático da cobrança e do pagamento, Vendor, mensagem de cobrança do Itaú e FGTS pelo SISPAG; débito veicular só para **pagamento**, e driver à parte quando se souber o estado (R52).
- **Documento 252 (FGTS: retorno S-5003 e S-5013, guia importada, histórico de remunerações com o arquivo do Anexo I, saldo rescisório):** reservado, não aberto.

# 4. A Carga56

| **Pasta** | **Conteúdo** | **Linhas** |
|---|---|---|
| 01-dominios-banco | `Cad_Classe_Sistema`: 13 comandos de `tipo_movimento_remessa_bancaria` e 9 motivos de `motivo_baixa_titulo_bancario` | 22 |
| 02-parametro-vencimento-fgts | `Cad_Rh_Parametro_Vencimento_Encargo`: FGTS, dia 20 do mês seguinte, antecipa, **provisório** (manual do FGTS Digital 1.70, de 12/06/2026) | 1 |

# 5. Leituras minhas e limites do que apliquei

- **Dia 20 no vencimento do FGTS:** o manual do FGTS Digital (versão 1.70) diz dia 20 do mês seguinte, antecipando; o documento 01 dizia dia 7. Como é parâmetro, **carreguei o dia 20 como provisório** até o contador confirmar (C374); `Vigencia_Inicio` é a data do manual (12/06/2026), leitura minha: se houver competência anterior para recalcular, a data muda.
- **Convênio na carteira** (e não na conta): leitura minha da sua instrução de cadastrar as carteiras por banco; o convênio da Caixa tem 12 posições no CNAB 240 de pagamentos e 7 no de cobrança (documento 250, seção 3.19).
- **Folha em várias contas:** a regra de soma e a de um colaborador por remessa são minhas (Q250-58).
- **Q250-49 aprovada em parte:** valem os itens a, b, c e f; ficam abertas, como pergunta aos bancos, o código 10 e a agência 7777 do Itaú e o código 99 do Pix Automático da Caixa.
- **Manuais da Caixa:** li o CNAB 240 de cobrança, o extrato CNAB 240 v005 e o manual IBC; o site **bloqueou** o CNAB 400, o Tradutor CNAB do Pix Automático e a GRCSU v1.8, e não contornei o bloqueio. **Sem esses três, a carga do mapa da Caixa não é feita** (Q250-56).
- **Nubank e XP:** sem canal técnico confirmado; o extrato continua manual (R20).
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** as **perguntas** do documento 250 que continuam abertas (34 na consolidação e, depois, a Q250-59, do teste em produção, e a Q250-60, das regras da carteira), **agrupadas por banco** no documento 254 (Itaú, Bradesco, Banco do Brasil, Caixa, Santander, Nubank, XP e as gerais); os **três PDFs da Caixa** bloqueados (Q250-56); a Q250-58 (folha em várias contas); e os demais itens do documento 38.
- **Contador:** a **C374** (reservada): confirmar o dia 20 do FGTS e a multa de 40 por cento da rescisão (Q250-47).
- **Bancos:** contrato, produto e canal de cada um (Q250-51), na ordem da Q250-1.

Próximos números: D-N659, contador C374, documento 252 (FGTS), documento 255, R125, Q250-59, Q251-8, Q246-9, Q248-7, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.56.
