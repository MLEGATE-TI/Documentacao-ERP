# Consolidação da Revisão 48 — Documento 231

*Relatório do que entrou no dicionário com o seu "consolidar" de 16/11/2026, depois do documento 230 (comparação das regras de validação da NT 2020.005). Você não tinha respondido as Q230-1 a Q230-5, e eu tinha achado, nas normas mais novas, três linhas do documento 230 que mudaram. Perguntei o escopo e você escolheu: **o documento 230 com as recomendações lidas como "Sim" e com os ajustes das normas novas**. É só isso; nada além.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 47** | **Revisão 48** | **Diferença** |
|---|---|---|---|
| Entidades | 1.240 | 1.240 | 0 |
| Campos | 14.398 | 14.398 | 0 (6 campos mudaram de tipo ou de texto) |
| Campos de referência (FK) | 3.691 | 3.691 | 0 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 373 | 373 | 0 |
| Tabelas físicas (DDL) | 1.506 | 1.506 | 0 |
| Chaves estrangeiras (DDL) | 3.957 | 3.957 | 0 |
| Índices (DDL) | 4.048 | 4.048 | 0 |
| Comentários (DDL) | 12.137 | 12.137 | 0 |
| Comandos do T-SQL | 21.649 | 21.649 | 0 |
| Chaves opcionais que esperam a onda de destino | 86 | 86 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Fase 0 93, Contabilidade & Fiscal 65 | Fase 0 **94**, Contabilidade & Fiscal **66** | CRM & Vendas segue em 27 e Compras em 31 |

O número de entidades e de campos **não muda**, como o documento 230 previa. Mudam **6 campos em 4 entidades** e entram **76 linhas de carga** (seção 3).

# 2. O que mudou na estrutura (Q230-2, Q230-3 e Q230-5)

| **Entidade e campo** | **Antes** | **Depois** | **Efeito** |
|---|---|---|---|
| `Cad_Dfe_Parametro_Regra.ID_Modelo_Documento` | referência, na versão | referência **--- identidade** (sobe para o mestre) | a mesma regra vale para o modelo 55 e para o 65 em linhas próprias |
| `Cad_Dfe_Parametro_Regra.ID_Estado` | referência opcional, na versão | referência opcional **--- identidade** (sobe para o mestre) | linha nacional (vazio) e linha da UF (AC, BA e SP na inutilização; G56, G110 e G138 da NFCom), sem um código por UF |
| `Cad_Dfe_Parametro_Regra.Codigo_Regra` (texto) | identidade (`Codigo_Regra`, `Ambiente`) | identidade (`ID_Modelo_Documento`, `Codigo_Regra`, `Ambiente`, `ID_Estado`) | a chave única do mestre passa de 2 para 4 colunas |
| `Cad_Dfe_Evento_Combinacao.Resultado` | {permitido, rejeitado, rejeitado_se_mesmo_autor} | + `rejeitado_se_nao_cancelado` | exceção da regra 4P15-34: cancelar a nota com eventos financeiros se cada um tiver o seu cancelamento |
| `Mov_Nota_Fiscal_Saida_Item_Importacao.Tipo_Declaracao` | {di, duimp, dsi} | + `dire` | a DIRE que o campo nDI lista; sigla lida como declaração de importação de remessa expressa |
| `Mov_Nota_Fiscal_Saida_Item_Importacao_Adicao.Numero_Adicao` | código (até 3) | código (até 3), **opcional** | vazio na DUImp, como a NT 2020.005 manda (nAdicao, ocorrência 0-1) |

No DDL do PostgreSQL a chave única do mestre fica `UNIQUE (id_modelo_documento, codigo_regra, ambiente, id_estado)`, as colunas `id_modelo_documento` e `id_estado` passam para a tabela do mestre e o `CHECK` de `resultado` ganha o valor novo. **Limite:** como `id_estado` pode ser vazio, o PostgreSQL não considera duas linhas nacionais iguais como duplicadas (NULL é distinto de NULL na chave única); o SQL Server considera. É o mesmo comportamento de `Cad_Dfe_Leiaute` com `ID_Autoridade` opcional, e a unicidade da linha nacional precisa de uma conferência na aplicação até o desenho do índice.

# 3. A carga (`Carga48-20261116`)

A pasta (e o zip de mesmo nome, com LEIA-ME e ordem de carga) traz **só as linhas a incluir**, com a chave de negócio, CSV com BOM e separador ";". Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_Dfe_Parametro_Regra_NFe` | 36 | 25 do documento 230 (27 menos as 2 de São Paulo da 3B08-100) + 11 de ajuste das normas novas (seção 4) |
| `Cad_Dfe_Codigo_Retorno_NFe` | 28 | 19 códigos, autoridade `AN_NFE`: os 23 do documento 230 e 5 novos (126 na NFC-e; 129 e 998 nos modelos 55 e 65) |
| `Cad_Dfe_Evento_Tipo_NFe` | 6 | 790700, 990100, 900120, 900140, 900138 e 900110 no modelo 55; se o tipo já existir, ignorar a linha |
| `Cad_Dfe_Evento_Combinacao_NFe` | 6 | 790700 → 110111 rejeitado (939); os cinco eventos financeiros → 110111 `rejeitado_se_nao_cancelado` (940) |

Total: **76 linhas de dados** em 4 arquivos (com LEIA-ME).

# 4. Os ajustes das normas novas

Li os PDFs que você enviou (NT 2023.002 v1.02, NT 2022.005 v1.11 e NT 2026.007 v1.11, do Portal da NF-e, e dois resumos de terceiros da NT 2025.002). O que mudou em relação ao documento 230:

| **Linha ou regra do documento 230** | **O que mudou** | **Fonte** | **Como ficou na carga** |
|---|---|---|---|
| `NFE-INUTILIZACAO-TIPOS-EMISSAO-SP` (2 linhas, regra 3B08-100, observação de São Paulo) | **Saiu.** A observação de São Paulo está **riscada** na NT 2023.002 v1.02 (página 9) e a regra ganhou a exceção "não se aplica para as UF: AC, BA e SP". Meu primeiro resumo dizia que São Paulo passava a validar os tipos 2, 4 e 5: estava errado, o agente leu o texto riscado como vigente. | NT 2023.002 v1.02, seções 2.5 e 3, páginas 6 e 9 | As 2 linhas não entram. As linhas `NFE-INUTILIZACAO-TIPOS-EMISSAO` ficam com a nota de que não valem em AC, BA e SP |
| (nova) `NFE-INUTILIZACAO-SERVICO-ATIVO` | O serviço de inutilização deixa de existir em AC, BA e SP (Ajustes SINIEF 38 e 40/2026): a SEFAZ responde HTTP 404 ou a rejeição **998** (regra I01a). Teste até 11/11/2026 e produção em 11/11/2026, a mesma data. | NT 2023.002 v1.02, cronograma e seção 5.1 | 6 linhas (AC, BA e SP × modelos 55 e 65), valor 0 desde 11/11/2026; linha ausente = serviço ativo. O código 998 entra na carga |
| `NFCE-LOTE-ASSINCRONO-MINIMO-NOTAS` (GAP03a-3, rejeição 452) | A NT 2023.002 v1.02 **não cita** a regra nem a rejeição 452; a autorização assíncrona acaba em 05/04/2027 (testes até 01/02/2027) e o lote de NFC-e já é de 1 nota desde 04/09/2023 | NT 2023.002 v1.00 e v1.02, cronograma e seção 3.1 | A linha **vale até 04/04/2027**; o 452 também. Pode ter caído antes: a conferir no Anexo I do MOC atual |
| (nova) `NFE-AUTORIZACAO-ASSINCRONA-PERMITIDA` e `NFCE-LOTE-MAXIMO-NOTAS` | Regra GAP03a-6: a SEFAZ rejeita indSinc=0 com a **129**, nos modelos 55 e 65. Regra GAP03a-4: o lote da NFC-e só aceita 1 nota (rejeição **126**; o código 961 traz a mesma mensagem e não aparece em nenhuma regra do texto) | NT 2023.002 v1.02, seção 3.1 | 2 linhas (valor 0 desde 05/04/2027) e 1 linha (1 nota por lote, desde 04/09/2023); códigos 126 e 129 na carga |
| `NFE-VNF-FORMULA` (W16-10, rejeição 610) | O total da NF-e passa a **incluir IBS e CBS**; em 2026 eles não entram no total, mesmo informados (período de testes). A rejeição 610 e a fórmula da NT 2020.005 não foram revistas por mim | Resumo da NT 2025.002 v1.00 (Inventti, 14/04/2025) e da v1.40 (Systax, 20/05/2026): fontes de terceiros | As 6 linhas do documento 230 ficam. Entram 2 linhas `NFE-VNF-FORMULA-IBSCBS` (55 e 65), **início em 01/01/2027, leitura minha**, composição exata não conferida (Q231-1 e Q231-3) |
| `NFE-VICMSUFDEST-FORMULA` e `NFE-VICMSUFREMET-FORMULA` (NA15-10 e NA17-10) | **Sem mudança.** A NT 2022.005 v1.11 só reativa a NA01-20 (rejeição 694) e acrescenta as regras 3BA02 de devolução; diz que não alterou as outras regras do DIFAL | NT 2022.005 v1.11, páginas 3 a 7 | As 2 linhas ficam como estavam. A NA01-20 e as 5 regras 3BA02 **não** entram (Q231-2) |
| `1C17-50`, `5E17-10`, `N12-70` e `N12-80` (documento 230) | **Sem mudança.** A NT 2026.007 v1.11 não os cita; só exclui a 5E17-70 e a C17-10 e cria o tratamento do contribuinte exclusivo do IBS/CBS, sem IE (produção em 16/11/2026, a v1.00 previa 03/11/2026) | NT 2026.007 v1.11, páginas 3 a 11 | Nada muda nas linhas. O desenho do emitente sem IE fica para a Q231-2 |
| Rejeição 301 (denegação por irregularidade fiscal do emitente) | A regra 1C17-40 está **riscada** nos modelos 55 e 65 e passa a valer a 1C17-38, com a rejeição **781**; o texto da NT fala só em NFC-e (Ajuste SINIEF 10/2023) | NT 2023.002, seção 7, página 11 | **Fora da carga**: o 301 não estava no documento 230; fica como ponto a conferir (Q231-2) |

# 5. Leituras minhas que aguardam a sua confirmação

1. **Início de `NFE-VNF-FORMULA-IBSCBS`:** 01/01/2027 é leitura minha do texto "em 2026 os valores de IBS e CBS não serão computados"; não li a regra W16-10 atual.
2. **Modelo 65 da inutilização:** a NT 2023.002 lista a 3B08-100 só para o modelo 55; mantive o 65 (que o documento 230 trazia da NT 2020.005) e a Seção 2.5 da NT trata o serviço como "da NF-e e da NFC-e".
3. **Indicadores em `Valor_Numerico`** (0 ou 1 nas linhas de serviço ativo, assíncrono permitido, CEST ativo e tolerância da desoneração): o campo não proíbe, mas não é o uso de limite ou prazo que os documentos 40 e 42 descrevem.
4. **Natureza e ação padrão** dos 28 códigos, e **autor e ambiente receptor** dos 6 eventos: leitura minha. O 998 tem ação "nenhuma" porque o ERP já sabe, pela linha de serviço ativo, que não deve pedir a inutilização.
5. **Autoridade `AN_NFE`:** leitura minha, porque os códigos são comuns às SEFAZ e a identidade do código inclui a autoridade.
6. **DIRE** = declaração de importação de remessa expressa: leitura minha; pode ser o mesmo que o DIR da Q221-5, que segue em aberto.

# 6. O que ficou de fora

- **`Compoe_Total_Documento` não foi estendido a IBS e CBS** (Q231-1). A marca entrou na revisão 47 só para PIS-ST e COFINS-ST; a linha `NFE-VNF-FORMULA-IBSCBS` já fala em IBS e CBS no total, mas o campo que diria, por linha de tributo, se compõe o total não foi mudado.
- **NA01-20, as 5 regras 3BA02, o DFeReferenciado na devolução e o emitente sem IE** não foram desenhados (Q231-2): a NT 2022.005 v1.11 e a NT 2026.007 v1.11 trazem regras novas, e a NT 2025.002 v1.40 passa a proibir `refNFe` na devolução e a exigir o grupo DFeReferenciado (regra VC02-14, produção em 01/09/2026, segundo a Systax; **não li a regra**).
- **Rejeição 301 e regra 1C17-38** (Q231-2).
- **ZD01-10, ZD02-10, ZD07-10, 1C17-50, 5E17-10 e B00** continuam sem linha, como no documento 230.
- **A exceção 7 da N12-70** continua com o texto quebrado pelo PDF da NT 2020.005 (só os quatro CFOP que a frase cita antes).

# 7. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagens contra o previsto no documento 230 | 1.240 entidades, 14.398 campos, 3.691 referências, 373 domínios, 266 mestres, 1.506 tabelas, sem mudança |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem, duas vezes: antes e depois de corrigir o cabeçalho dos arquivos) | Sem erro: 1.506 tabelas, 3.957 chaves estrangeiras e 12.137 comentários; chave única de `cad_dfe_parametro_regra` com 4 colunas; as colunas do modelo e da UF estão na tabela do mestre |
| T-SQL (analisador sqlglot) | 21.649 comandos, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Fontes lidas de novo no PDF original | NT 2023.002 v1.02 (12 páginas), NT 2022.005 v1.11 (8), NT 2026.007 v1.11 (11), Systax sobre a NT 2025.002 v1.40 (12) e Inventti sobre a v1.00 (4): as correções do resumo dos agentes saíram desta leitura |
| Carga | 76 linhas geradas em 4 CSV; chaves de negócio (UF, modelo, autoridade, código) conferidas contra o documento 230; nada carregado em banco |
| Modelo entidade-relacional e diagramas | Regerados |

# 8. O que continua aberto

- **Você:** Q231-1 a Q231-3 (seção 1.46 do documento 38); Q226-1 a Q226-5; Q228-1 e Q228-2; Q229-1 e Q229-2; a definição de **DIR** (Q221-5); a Q218-8; a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9; o envio do Manual v1.02 e do Anexo IV da NFS-e Via e do **Anexo I do MOC atual** e da **NT 2020.006**.
- **Contador:** C1 a C363 do documento 188 (a C362 e a C363 seguem abertas).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.
- **Fila de desenho (minha):** o split payment (adiado por você), a carga da lista de autopeças não produzidas (espera a Q206-10) e, se você disser sim na Q231-2, o desenho da NT 2026.007, do DFeReferenciado e das regras de devolução.

# 9. Limites

- **As 36 linhas e os 28 códigos são provisórios:** não li o Anexo I do MOC atual nem a NT 2025.002 em vigor; o Portal da NF-e bloqueia a consulta automática e não contornei.
- **Duas das cinco fontes novas são resumos de terceiros** (Inventti e Systax) e a regra W16-10 atual não foi lida; o início de 01/01/2027 do IBS/CBS no total é leitura minha.
- **As datas da NT 2023.002** têm a inutilização em teste e em produção no mesmo dia (11/11/2026), já passado; o texto não diz se já está em vigor em cada UF. Vale confirmar com a SEFAZ.
- **Correção de forma nos arquivos de DDL das revisões 44 a 47:** o comentário da primeira linha de cada onda dizia "revisão 43"; o conteúdo estava certo. A revisão 48 corrige o cabeçalho para "revisão 48".
- **Nada foi validado num SQL Server;** o T-SQL foi só lido por um analisador.
- O Project continua acima do limite de tamanho (a gravação dos documentos 188, 224, 226, 227, 229 e 231 pode ser recusada), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
