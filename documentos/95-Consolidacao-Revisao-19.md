# Consolidação da Revisão 19 — Documento 95

*Relatório do que entrou no dicionário com o seu "consolidar" de 21/10/2026, do que ficou de fora e de como conferi. A revisão 19 aplica o documento 90 (que você aprovou nas Q90-1 a Q90-6) e as decisões do documento 91 e do documento 87 que já tinham lista de campos vista por você. Tudo o que não tinha vai para o documento 96, como proposta, e **não altera o dicionário**.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

| | Revisão 18 | Revisão 19 | Diferença |
|---|---:|---:|---:|
| Entidades | 907 | 915 | +8 |
| Campos | 9.765 | 9.878 | +113 |
| Campos de referência (FK) | 2.627 | 2.654 | +27 |
| Domínios | 268 | 272 | +4 (5 novos, 1 saiu) |
| Entidades mestres (com tabela de versão) | 183 | 184 | +1 |
| Tabelas no DDL | 1.090 | 1.099 | +9 |

Auditoria: **0 achados**. DDL: 1.099 tabelas, 2.838 chaves estrangeiras, 2.908 índices e 7.934 comentários; **PostgreSQL 16 sem erro**; T-SQL só lido pelo analisador (14.780 comandos, nenhum erro de leitura). Módulos alterados: Fase 0 (revisão 67), Contabilidade & Fiscal (37), Folha & RH (28), CRM & Vendas (18) e Compras (24).

Os 113 campos novos são 99 nas oito entidades novas e 14 em entidades que já existiam (um campo saiu e outro entrou em `Cad_Rh_Parametro_Jornada`, saldo zero).

# 2. Como li o "consolidar"

Você escreveu só "consolidar", depois de responder às perguntas abertas. Entendi: aplicar tudo o que você aprovou **e que eu já tinha desenhado em campos que você viu**. Quando a decisão não tinha lista de campos vista (porque você a tomou depois do desenho, ou porque pediu um documento à parte), não escrevi campos por conta própria: está no documento 96. Se você queria que eu entrasse com esses itens também, diga, e eu aplico na revisão 20 com a aprovação do documento 96.

# 3. O que entrou

## 3.1 Entidades novas (8, 99 campos)

| Entidade | Módulo | Campos | Decisão |
|---|---|---:|---|
| `Cad_Credito_Presumido_Categoria` | Contabilidade & Fiscal | 10 | D-N334 (Q90-1): categoria, coeficiente por ano, ressarcimento, fundamento legal, situação do dado, instância de aprovação e vigência |
| `Cad_Lista_Legal_Item` | Contabilidade & Fiscal | 17 | D-N269 e Q90-2 (mestre): itens das listas legais por NCM e NBS |
| `Cad_Taxa_Depreciacao_Cbs` | Contabilidade & Fiscal | 11 | D-N269: Anexo I do decreto |
| `Cad_Regra_Operacao_Equiparada_Cbs` | Contabilidade & Fiscal | 13 | D-N285 e Q90-5 (condições como colunas) |
| `Mov_Agencia_Turismo_Repasse` | Contabilidade & Fiscal | 13 | D-N283 e Q90-3 (13 campos) |
| `Mov_Auto_Infracao` | Contabilidade & Fiscal | 12 | D-N284 e Q90-4 (`Tipo_Registro` e `Orgao_Autuante` mantidos) |
| `Cad_Esocial_Ocorrencia` | Folha & RH | 11 | D-N301 e D-N302: catálogo das ocorrências do retorno do eSocial, com vigência |
| `Mov_Esocial_Evento_Ocorrencia` | Folha & RH | 12 | D-N302: ocorrências recebidas por evento |

## 3.2 Entidades que já existiam e mudaram (6 com campo, 4 só com texto)

| Entidade | Mudança | Decisão |
|---|---|---|
| `Cad_Credito_Presumido_Ibs_Cbs` | +`ID_Categoria_Credito_Presumido` (obrigatório; ver seção 5) | D-N334 |
| `Mov_Nota_Fiscal_Saida_Item` | +5 campos: `Tipo_Onerosidade`, `Opcao_Doacao_Cbs`, `Origem_Opcao_Doacao`, `ID_Usuario_Confirmacao`, `Data_Hora_Confirmacao` | D-N285 e D-N286 |
| `Cad_Participante` | +`Regra_Fornecimento_Gratuito_Cbs` | D-N290 |
| `Cad_Rh_Parametro_Jornada` | −`ID_Modo_Composicao_Noturna`; +`Aplica_Hora_Noturna_Na_Prorrogacao` (booleano) | D-N335 (Q87-27) e D-N339 (Q87-13) |
| `Mov_Apuracao_Irpj_Csll` | +4 campos: plano patrimonial, plano de resultado, usuário e data e hora da confirmação do contador | D-N336 (Q91-10) |
| `Cad_Plano_Referencial` | +`Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia`; virou tabela de janela (sem versão própria), com vigência para o plano inteiro e outra nas contas | D-N338 (Q91-5) |
| `Mov_Nota_Fiscal_Entrada`, `Mov_Esocial_Evento`, `Cad_Rh_Regra_Hora_Extra`, `Cad_Conta_Contabil_Referencial` (e o texto de `Cad_Ecf_Tabela_Dinamica` e de `Cad_Obrigacao_Leiaute_Versao`) | Só descrição: nota de entrada vale para qualquer nota de entrada (D-N280); vínculo importado (D-N301, D-N303); hora extra só composta (D-N335); código fora do plano referencial **bloqueia** (D-N337, Q91-4); segmento e versão do leiaute escolhida pelo operador (D-N333 e D-N340, Q91-6) | — |

## 3.3 Domínios

Cinco novos: `tipo_lista_legal`, `tipo_operacao_equiparada`, `efeito_credito_operacao`, `criterio_base_operacao` e `categoria_credito_presumido` (produtor_rural, residuos, bens_usados, transportador_autonomo). Um saiu: `modo_composicao_noturna` (D-N335).

## 3.4 Carga da ECF

Regerada e comparada com a da revisão 18: mudaram **só** a vigência do plano referencial e **9 células de segmento** (as abas M300, M350 e N630, A, B e C, da D-N333). O resto bateu linha a linha. Pacote `Revisao19-Carga-ECF`.

## 3.5 Documentos atualizados

Dicionário: documentos 01, 03, 05, 10 e 11. Contagens e quadro de ondas: documento 31. Histórico: documento 14, com a seção "Consolidação da revisão 19" (D-N334 a D-N341). Auditoria: documento 29. Pendências: documento 45. Os documentos 90 e 91 receberam o aviso de que foram aplicados.

# 4. O que ficou de fora, e por quê

| Item | Por que não entrou | Onde está |
|---|---|---|
| Redutor da DeRE por contas (Q86-6, D-N341) | Decisão tomada depois do desenho, sem lista de campos vista; e a minha leitura inicial estava errada (um parâmetro da lei não aponta para conta da empresa) | Documento 96, seção 2 |
| Sufixo `Com_Sinal` (D-N326) | Falta decidir em quais campos entra, porque o nome do campo no leiaute não muda; minha lista de candidatos tinha erro | Documento 96, seção 3 |
| Cadeia do lucro real da ECF (documento 93, D-N332) | As Q93-1 a Q93-8 não foram respondidas | Documento 93 |
| D-N249 a D-N253, D-N257, D-N258, D-N263, D-N267, D-N268 e Duimp | Você pediu detalhar em documento específico | A escrever depois; o cruzamento com os seus perfis está no documento 94 |
| D-N282 (split payment) | Adiado por você para janeiro de 2028 | Sem mudança |
| Respostas da Q85 e da Q87 (21/10/2026) | Registradas no documento 14; não pediram campo novo | Documento 14 |

# 5. Pontos que decidi sem você, e que você pode reverter

- **Campos de `Cad_Credito_Presumido_Categoria`.** Você viu quatro itens (categoria, coeficiente, ressarcimento, vigência); os demais (a chave, o fundamento legal, a situação do dado e a instância de aprovação) são meus, pelo padrão das outras entidades de parâmetro.
- **`ID_Categoria_Credito_Presumido` ficou obrigatório** no código cCredPres. A tabela tem 13 códigos e o domínio tem quatro categorias; se algum código não couber, o campo obrigatório força uma classificação errada. Proponho torná-lo opcional (documento 96, Q96-9).
- **`Aplica_Hora_Noturna_Na_Prorrogacao`** é nome meu.
- **`Cad_Plano_Referencial` como tabela de janela, sem versão própria** (as contas dentro dele já tinham vigência). Se você preferia o padrão de mestre com versão, é troca pequena.
- **Numeração das decisões.** Usei D-N334 a D-N341 no documento 14. A D-N340 (Q91-6) estava sem número no primeiro texto e corrigi.
- **Documento 31.** A frase "69 entidades com campo de código identidade" já estava velha (o modelo dá 74 na revisão 19) e eu **não mudei**: só acrescentei a frase das cargas novas. Corrijo se você aprovar.

# 6. Como conferi

- **Auditoria** do dicionário: regras de vigência (B1, B4), nomes de referência (D2) e tipo numérico para valores (H2). 0 achados.
- **PostgreSQL 16:** o DDL completo roda sem erro. **SQL Server:** o T-SQL foi lido pelo analisador (14.780 comandos, nenhum erro), mas **ninguém executou** ainda num SQL Server: é a primeira execução que a equipe tem de fazer.
- **Contagens** conferidas contra o quadro de ondas do documento 31 (915 entidades, 184 mestres, 1.099 tabelas, 9.878 campos, 2.654 chaves). As contagens do relatório batem com a diferença que o modelo calcula entre as revisões 18 e 19.
- **Carga:** diferença com a revisão 18 só nos pontos da seção 3.4.

# 7. Perguntas abertas depois desta revisão

- Documento 96: Q96-1 a Q96-9.
- Documento 93: Q93-1 a Q93-8 (cadeia do lucro real).
- Documento 94: a fila de desenho dos seus perfis (Q94-1 a Q94-7).
- Documento específico de Comércio Exterior, qualificação do participante e demais itens que você mandou detalhar (cobertos pelo documento 94, blocos B1 e B2).
- Os oito perfis que você não marcou (documento 94, seção 2.3) e a Q70-13 (textos da LC 225, do Decreto 13.133, consolidação com o 13.075 e Anexos I a XV da LC 214).
- Do contador: limites da ECF, incisos do art. 4º, teste do Y520, Q80-1 e as funções da cadeia do documento 93.
- Da equipe: primeira execução do DDL em SQL Server.

# 8. Limites

O Project está acima do limite de espaço: os documentos 90 a 96 ficam só locais e em Word. Os documentos do dicionário e o histórico foram reescritos no Project. Nenhum dado de cliente foi usado. As contagens são do modelo gerado, e o modelo é gerado a partir dos documentos: se um campo estiver errado no documento, estará errado em tudo.
