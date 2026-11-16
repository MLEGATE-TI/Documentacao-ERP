# Consolidação da Revisão 45 — Documento 223

*Relatório do que entrou no dicionário com o seu segundo "consolidar" de 16/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava aplicado**: as **Q188-7 e Q188-8** (D-N584) e as **Q220-1, Q220-5 e Q221-1 a Q221-13** (D-N588). Como esse conjunto não tinha desenho em campos, **escrevi o desenho (documento 222) e o apliquei no mesmo passo**; se algo do desenho não for o que você queria, corrijo na revisão 46.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **** | **Revisão 44** | **Revisão 45** | **Diferença** |
|---|---|---|---|
| Entidades | 1.229 | 1.239 | +10 |
| Campos | 14.261 | 14.364 | +103 |
| Campos de referência (FK) | 3.663 | 3.682 | +19 |
| Entidades mestres | 259 | 266 | +7 |
| Referências genéricas | 63 | 63 | 0 |
| Domínios de `Cad_Classe_Sistema` | 369 | 370 | +1 (`bandeira_cartao_dfe`) |
| Tabelas físicas (DDL) | 1.488 | 1.505 | +17 |
| Chaves estrangeiras (DDL) | 3.922 | 3.948 | +26 |
| Índices (DDL) | 4.013 | 4.039 | +26 |
| Comentários (DDL) | 12.011 | 12.104 | +93 |
| Comandos do T-SQL | 21.435 | 21.597 | +162 |
| Chaves opcionais que esperam a onda de destino | 85 | 85 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |

**10 entidades novas** (103 campos) e **13 entidades existentes alteradas** (9 na estrutura de campos e 4 só em texto ou em domínio; os campos novos e os que saíram se compensam, e o saldo de campos das alteradas é zero). Sete das novas são mestres, com vigência, e viram duas tabelas cada no DDL; por isso as 10 entidades dão 17 tabelas. Oito ficam na onda 3 (Contabilidade & Fiscal) e as duas tabelas filhas do item da nota ficam na onda 4. As 81 entidades empurradas por módulo posterior não mudam.

# 2. O que entrou

**NBS com hierarquia (Q220-1 e Q220-5):** `Cad_NBS` passa a guardar capítulo, posição, subposições, item e subitem: `Codigo_NBS` de 3 a 9 posições, `ID_NBS_Pai`, `Nivel` e `Analitico` (só o subitem de 9 posições).

**cClassTrib, CST, modelos e CFOP (Q221-1 a Q221-7):** `Cad_Cclasstrib` ganha `Tipo_Aliquota` (5 valores) e `Numero_Anexo_Lc_214` e perde `Indicador_Duimp`; `Cad_CFOP.Indicador_Combustivel` vira `Tipo_Combustivel` (0, 1 e 2); o crédito presumido fica com dois valores (`nao_permite` e `exige`); o texto "19 códigos" do CST virou "18" em `Mov_Apuracao_Tributo_Item`.

**Unidades e uTrib (Q221-8 e Q221-9):** `Cad_Unidade_Medida.Origem_Tabela` (as duas tabelas, sem fundir); a sigla do litro nos exemplos de `Unidade_Estatistica` passa a `LT`.

**Tabelas do Portal que não tinham entidade (Q221-10 e Q221-11), 6 entidades novas:** `Cad_Icms_Monofasico_Aliquota`, `Cad_Combustivel_Mistura_Obrigatoria`, `Cad_Fcp_Aliquota_Uf`, `Cad_Gtin_Prefixo_Gs1`, `Cad_Veiculo_Tipo_Especie` e `Cad_Regime_Especial_Padrao_Numero_Processo`; e o domínio `bandeira_cartao_dfe` (28 bandeiras).

**Origem do combustível repetível (Q221-12):** duas tabelas filhas do item da nota (`Mov_Nota_Fiscal_Saida_Item_Origem_Combustivel` e `Mov_Nota_Fiscal_Entrada_Item_Origem_Combustivel`); os três campos do conjunto único saem dos dois itens.

**Guarda do arquivo e opção de escrituração (Q188-7 e Q188-8):** `Cad_Obrigacao_Guarda_Arquivo` (prazo de 5 anos da última transmissão, reiniciado na retificação), `Mov_Escrituracao_Retencao_Fiscalizacao` (suspende o descarte) e os campos `Data_Descarte_Prevista` e `Retido_Por_Fiscalizacao` em `Mov_Escrituracao_Arquivo`; `Cad_Efd_Contribuicoes_Opcao_Escrituracao` passa a ser por empresa.

**Avisos do Motor:** 13 novos (A222-1 a A222-13); nenhum bloqueia. **Anexo 58 do documento 10, anexo 13 do documento 03 e anexo 15 do documento 05:** as 10 entidades, a tabela das cargas e os avisos. **Documento 01:** a linha do domínio novo.

# 3. Cargas de partida (provisórias)

A pasta **`Carga45-20261116`** (zip de mesmo nome, com LEIA-ME e ordem de carga) reúne as cargas na estrutura nova e **substitui** os arquivos de NBS, cClassTrib, CFOP e unidades das cargas 220 e 221.

| **Carga** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_NBS` | 1.282 | 26 capítulos, 146 posições (45 derivadas), 130 + 50 subposições, 10 itens e 920 subitens; os 920 subitens são idênticos aos da carga anterior (conferido) |
| `Cad_Cst`, `Cad_Cclasstrib`, `Cad_Credito_Presumido_Ibs_Cbs` | 36 + 173 + 13 | `Tipo_Aliquota`: 89 sem alíquota, 64 padrão, 8 uniforme setorial, 7 fixa e 5 uniforme nacional de referência; 19 números de anexo |
| `Cad_Modelo_Documento_Fiscal` e `Cad_Cclasstrib_Modelo` | 17 + 2.941 | Um modelo por indicador da IT; as quatro marcas `Exige_*` ficam vazias; o DIR com descrição provisória |
| `Cad_CFOP` | 619 | `Tipo_Combustivel`: 556 com 0, 16 com 1 e 47 com 2 |
| `Cad_Unidade_Medida` | 68 | 55 comerciais, 7 só uTrib e 6 nas duas |
| `Cad_Icms_Monofasico_Aliquota` | 151 | 111 janelas encerradas e 40 vigentes (a tabela traz 191 linhas, mas 40 repetem a janela vigente) |
| `Cad_Combustivel_Mistura_Obrigatoria` | 23 | 9 vigentes e 14 encerradas; fração da tabela convertida em percentual |
| `Cad_Fcp_Aliquota_Uf`, `Cad_Gtin_Prefixo_Gs1`, `Cad_Veiculo_Tipo_Especie`, `Cad_Regime_Especial_Padrao_Numero_Processo` | 30 + 127 + 39 + 1 | Sem data na tabela do FCP, do GS1 e do regime especial: início 01/01/1900 (marcador de "desde sempre") |
| `Cad_Classe_Sistema` | 28 + 23 + 6 | bandeiras (novo), formas de pagamento e meios de pagamento (atualiza 6) |
| `Cad_Obrigacao_Guarda_Arquivo` | 1 | 5 anos; retificadora reinicia; fiscalização suspende; sem fundamento (C27) |
| Registro das cargas | 19 | as 10 do Portal, a NCM, a NBS (agora `processada`) e as 7 tabelas novas |
| Avisos do Motor (texto) | 13 | em CSV de leitura |

Total: **22.976 linhas de dados** em 25 arquivos (com LEIA-ME).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como tudo o que você aprovou e ainda não estava aplicado**, e escrevi o desenho em campos (documento 222) no mesmo passo, sem você revê-lo antes. Se algum campo não for o que você queria, mudo na revisão 46.
2. **Q221-13:** "prosseguir com as recomendações" valeu como a confirmação pedida (o PDF é o Anexo I da Portaria Conjunta 2.000/2018 e a NBS 2.0 segue vigente). O registro da NBS saiu de `com_pendencia` para `processada`, com vigência de 01/01/2019. Se o PDF não for o Anexo I, volto o registro.
3. **Ficaram de fora:** a **Q188-6** (aplicar as 21 respostas do contador; continua com você) e a **Q188-9** (o Imposto Seletivo literal da MP 1.399, que não muda campo: é o aviso 16 e a resposta do contador anexada como evidência).
4. **`Cad_NBS.Analitico`** e os valores **`ambas` e `propria`** de `Origem_Tabela` são extensões minhas.
5. **O ICMS monofásico tem 151 linhas, não 191.** Eu propus 40 + 151, mas as 40 "atuais" repetem a janela aberta de 2026 do histórico; carreguei o histórico e descartei as 40 repetidas. As marcas `pBio` e `origComb` só existem na tabela atual: ficam nas 40 janelas vigentes e valem `nao` nas 111 encerradas, o que está escrito no `Motivo_Vigencia`.
6. **O tamanho do código da NBS** por nível é 3, 5, 6, 7, 8 e 9 posições (não 2, 4, 6, 7, 8 e 9, como num rascunho meu); corrigido antes de aplicar.
7. **Modelos de documento:** o tipo do modelo e `Possui_Motor_Emissao` dos 17 modelos são leitura minha; as quatro marcas `Exige_*` ficam vazias até a lista por modelo (sua e do contador). O **DIR** continua sem definição (seção 0 do documento 38): entra com descrição provisória.
8. **`Cad_Efd_Contribuicoes_Opcao_Escrituracao`:** a chave passou de filial para empresa e o grupo de documento saiu. Se você queria manter a NFC-e separada no parâmetro, desfaço.
9. **Guarda do arquivo:** `Vigencia_Inicio` de 16/11/2026 (data da carga) é leitura minha; o fundamento legal fica vazio, porque a resposta do contador à C27 não cita norma.
10. **Fundamento legal vazio** nas tabelas de ICMS monofásico, mistura e FCP, e **"desde sempre" (1900-01-01)** onde a tabela não traz data.
11. **As somas previstas bateram** (1.239 entidades, 14.364 campos, 3.682 referências, 266 mestres, 63 referências genéricas e 370 domínios).

# 5. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagem contra o previsto | 1.229 + 10 entidades e 14.261 + 103 campos: **1.239 e 14.364**; referências 3.663 + 19 (20 nas entidades novas, 1 em `ID_NBS_Pai`, menos 2 nos itens); 370 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 63 referências genéricas |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.505 tabelas, 3.948 chaves estrangeiras e 12.104 comentários conferidos no banco; as 17 tabelas novas foram criadas |
| T-SQL (contagem e leitura) | 21.597 comandos lidos por um analisador de T-SQL, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | 8 entidades novas na onda 3 e 2 na onda 4; 81 entidades empurradas (sem mudança); 85 chaves opcionais esperam a onda de destino (sem mudança) |
| Cargas | Todas as conferências do LEIA-ME passaram: hierarquia da NBS (pai é prefixo do filho, tamanho do código por nível, 920 subitens iguais), 173 cClassTrib e as 19 marcas de anexo, 17 modelos e 2.941 marcas com cClassTrib existente, CFOP 556/16/47, siglas de unidade, produtos ANP, veículo e expressão regular |
| Documentos 31, 29, 14, 38 e 188 | Quadros do documento 31 regerados do modelo e comparados com os anteriores (só as linhas esperadas mudaram); totais conferidos por programa |
| Modelo entidade-relacional | Regerado |

# 6. O que continua aberto

- **Você:** a definição de **DIR** (Q221-5); a **Q188-6**; a **Q218-8** (só o Ajuste SINIEF 14/2025 e o 01/92); a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9.
- **Contador:** C1 a C359 do documento 188 (a C27 e a C33 ganharam a nota "aplicado na revisão 45"; o fundamento legal da C27 segue com ele; C358 e C359 são do documento 221).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.
- **Fila de desenho (minha):** o split payment (adiado por você) e a carga da lista de autopeças não produzidas. A fila das Q188-7 e Q188-8 e a do documento 221 **zeraram**.

# 7. Limites

- **A NBS não foi conferida no Diário Oficial:** a vigência vem dos atos que você enviou, e eu não consultei o DOU de 2019 a 2026.
- A **NT 2023.01** é a versão de 22/05/2023; não conferi se a NF-e atual mudou as regras. **120 códigos ANP** seguem sem descrição.
- **Nada foi validado com o contador;** o ERP registra, calcula o que a norma fecha e avisa, e não bloqueia (D-N284).
- O Project continua acima do limite de tamanho (a gravação dos documentos 221 e 188 foi recusada antes), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
