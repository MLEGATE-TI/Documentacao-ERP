# Consolidação da Revisão 49 — Documento 233

*Relatório do que entrou no dicionário com o seu "consolidar" de 17/11/2026. Perguntei o escopo e você escolheu: **a D-N600 (Q226-1 a Q226-5 do documento 226 e a Q229-1 do documento 229; a Q229-2 segue em espera) mais o documento 232 (revisão 2) com as recomendações lidas como "Sim"**. É só isso; nada além.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 48** | **Revisão 49** | **Diferença** |
|---|---|---|---|
| Entidades | 1.240 | **1.242** | +2 (`Mov_Escrituracao_Arquivo_Validacao` e `Mov_Dfe_Evento_Pagamento`) |
| Campos | 14.398 | **14.431** | +33 (20 nas entidades novas e 13 em 6 existentes) |
| Campos de referência (FK) | 3.691 | **3.701** | +10 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 373 | **374** | +1 (`descricao_estoque_abertura_cbs`) |
| Tabelas físicas (DDL) | 1.506 | **1.508** | +2 |
| Chaves estrangeiras (DDL) | 3.957 | **3.967** | +10 |
| Índices (DDL) | 4.048 | **4.058** | +10 |
| Comentários (DDL) | 12.137 | **12.169** | +32 |
| Comandos do T-SQL | 21.649 | **21.703** | +54 |
| Chaves opcionais que esperam a onda de destino | 86 | 86 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Revisão dos módulos | Fase 0 94, Compras 31, Contabilidade & Fiscal 66 | Fase 0 **95**, Compras **32**, Contabilidade & Fiscal **67** | CRM & Vendas segue em 27 |

Os números batem com os que o documento 232 previu (1.242, 14.431, 3.701, 374 e 1.508). **O que não bateu foram as contagens de carga do documento 232**, e a seção 4 as corrige: são **103** linhas novas de regra (não 107), **66** de cBenef (não 69), **37** códigos de retorno novos (não 31) e **48** linhas novas de tipo de evento (não 47).

# 2. O que mudou na estrutura

| **Origem** | **Entidade e campo** | **O que entrou** |
|---|---|---|
| Q226-1 (D-N600) | `Mov_Estoque_Abertura_Cbs_Item`: `ID_Descricao_Estoque`, `ID_Cst_Pis`, `ID_Cst_Cofins` | 3 campos de referência (opcionais, obrigatórios quando `Elegivel` é verdadeiro), para o F150 de 2027 da NT 13/2026; o texto da entidade diz que o F150 de 2027 sai deste estoque |
| Q226-1 (D-N600) | `Cad_Classe_Sistema.Dominio` e a lista de domínios da Fase 0 | domínio novo `descricao_estoque_abertura_cbs`, aberto, com 10 códigos provisórios (1, 2, 21, 3, 4, 41, 5, 6, 7, 8) |
| Q226-2 (D-N600) | `Mov_Apuracao_Processo_Referenciado.Origem_Tipo` | valor `estoque_abertura_cbs` (o F159, processo do F150 de 2027) |
| Q226-3 (D-N600) | **entidade nova** `Mov_Escrituracao_Arquivo_Validacao` (módulo 10, sem vigência, 6 campos) | registro 1950: hash e datas da EFD-Contribuições anterior; o ERP guarda e não bloqueia. O 1959 não é armazenado (sai de cálculo) |
| Q226-4 (D-N600) | `Cad_Obrigacao_Acessoria.Vigencia_Fim` | a EFD-Contribuições fica **sem data de fim (31/12/9999)** com quatro gatilhos de 2027 e a transmissão antecipada; troca a frase da revisão 46 ("deixa de existir") |
| Q226-5 (D-N600) | `Cad_Presuncao_Acrescimo` (`Situacao_Dado`, `Limite_Receita_Anual`, `Limite_Receita_Trimestral`, `Fundamento_Legal`) | CSLL de 2027 e limite trimestral passam a **validado**, com o fundamento legal e a ressalva de que o texto da LC 224 não foi lido |
| Q229-1 (D-N600) | `Mov_Nota_Fiscal_Entrada_Item` e `Cad_Produto_Servico_Dados_Produto`: `Codigo_Barras_Comercial`, `Codigo_Barras_Tributavel` | 4 campos (cBarra e cBarraTrib que não são GTIN), como na nota de saída (revisão 47) |
| Q232-4 | `Cad_Dfe_Evento_Tipo.Maximo_Ocorrencias` | 1 campo (vazio vale 1; 2 nos eventos conclusivos da manifestação) |
| Q232-5 | `Mov_Nota_Fiscal_Saida_Pagamento`: `Cnpj_Transacional`, `ID_Estado_Transacional`, `Cnpj_Recebedor`, `Identificador_Terminal_Pagamento` | 4 campos (YA03c, YA03d, YA07a e YA07b da NT 2023.004 v1.20) |
| Q232-6 | **entidade nova** `Mov_Dfe_Evento_Pagamento` (módulo 01, sem vigência, 14 campos) | o detalhe de pagamento (`detPag`) do evento ECONF (110750), de 1 a 100 por evento; o ERP só recebe |
| Q232-7 | `Mov_Apuracao_Tributo_Item.Indicador_Deduz_Desoneracao` | 1 campo (`indDeduzDeson`), booleano opcional |

As duas entidades novas ficam nas ondas 3 (`Mov_Escrituracao_Arquivo_Validacao`, junto com a escrituração) e 0 (`Mov_Dfe_Evento_Pagamento`, junto com `Mov_Dfe_Evento`); nenhuma nova chave estrangeira espera onda posterior (continuam 86).

# 3. A carga (`Carga49-20261117`)

A Carga49 é **completa**: junta as linhas da Carga48 com as novas e **substitui** os três arquivos da Carga48 (a pasta e o zip de mesmo nome trazem LEIA-ME e a ordem de carga). CSV com BOM, separador ";", chaves de negócio. Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_Dfe_Parametro_Regra_NFe` | 137 | 36 da Carga48 − 2 que saem (`NFE-VNF-FORMULA-IBSCBS`, 55 e 65) + **103 novas**. Das 34 que ficam, 5 foram encerradas por data (3 fórmulas da W16-10 em 29/03/2023 e 2 da exceção 3 em 30/06/2024) e 1 teve a descrição ajustada (exceção 7) |
| `Cad_Dfe_Codigo_Retorno_NFe` | 65 | 28 da Carga48 + **37 novas**, contadas por modelo e código |
| `Cad_Dfe_Evento_Tipo_NFe` | 54 | 6 da Carga48 + **48 novas** (43 códigos); coluna nova `Maximo_Ocorrencias` |
| `Cad_Dfe_Evento_Combinacao_NFe` | 11 | 6 da Carga48 + 5 da manifestação (655 ×3, 650, 651) |
| `Cad_Classe_Sistema` (domínio `descricao_estoque_abertura_cbs`) | 10 | 10 códigos provisórios; só o código 7 tem texto, e os outros dizem "texto a conferir" |
| `Cad_Classe_Sistema` (domínio `tipo_evento_dfe`) | 43 | os 43 códigos do catálogo; incluir só os que faltarem |
| Ajustes em linhas já carregadas | 4 | fim da EFD-Contribuições (Q226-4) e CSLL de 2027 validada (Q226-5) |

Total: **324 linhas de dados** em 8 arquivos (com LEIA-ME).

## 3.1. As 103 linhas novas de regra

| **Grupo** | **Linhas** | **Rejeição** | **Início** |
|---|---|---|---|
| W16-10 com o `vICMSMonoReten` (3 fórmulas novas) | 3 | 610 | 30/03/2023 |
| W16-10, exceção 4 (`NFE-VNF-EXC-DESONERACAO-NAO-DEDUZIDA`, 55 e 65) | 2 | 610 | 01/07/2024 |
| `vItem` e `vNFTot` (obrigatoriedade e fórmula; VB01 e W60) | 9 | 1137, 1105, 1004 e 1094 | 01/01/2027 |
| GAP03a-3 do modelo 55 (`NFE-LOTE-ASSINCRONO-MINIMO-NOTAS`) | 1 | 452 | 13/10/2025 |
| I08-90 (regra e exceção da UFCons) | 2 | 523 | 01/11/2020 |
| CFOP: NFC-e (3), exceções por UF (10), CE na NF-e (1), devolução (2) e CST 51 interna (1) | 17 | 725, 382, 386, 508 e 327 | de 01/11/2020 a 05/10/2026 |
| cBenef por UF (DF, GO, PR, RJ, RS, SC e SP) | 66 | 928 a 931, 934, 946, 664 a 666 | de 02/09/2019 a 06/04/2026 |
| Prazo da manifestação (90 dias; 180 dias até 31/05/2026; ciência em 10 dias) | 3 | 596 | de 02/05/2022 a 01/06/2026 |

Soma: 3 + 2 + 9 + 1 + 2 + 17 + 66 + 3 = **103**. O documento 232 dizia 107 porque contava a linha da exceção 7 (CST 51 interna) duas vezes (uma na Q232-1 e outra nas 17 de CFOP) e contava 69 de cBenef.

# 4. Correções em relação ao documento 232

| **Ponto** | **Documento 232** | **Aplicado** | **Por quê** |
|---|---|---|---|
| Linhas de cBenef por UF | 69 | **66** | A regra N12-97 é do modelo 55 só (NT 2019.001, grupo N); a matriz de UF diz "55/65" para GO, PR e RJ, e uma linha de NFC-e rejeitaria algo que a SEFAZ não rejeita. Entrou uma linha só (modelo 55) nessas três UF |
| Linhas novas de regra | 107 | **103** | −3 do cBenef e −1 da dupla contagem da exceção 7 |
| `Cad_Dfe_Parametro_Regra` | 141 | **137** | 36 + 103 − 2 |
| Linhas novas de código de retorno | 31 | **37** | O documento 232 contou por código, e a identidade do código inclui o modelo: cBenef 15 (e não 9), CFOP 4, manifestação 8, vItem e vNFTot 8, e 2 de I08-90 e GAP03a-3. A Carga48 tinha 28 linhas, e a Carga49 tem **65** |
| Linhas novas de tipo de evento | 47 | **48** | O evento 110300 (vinculação do pagamento) vale para o modelo 55 **e** para o 65, segundo a NT 2026.006 v1.01 ("modelo 55/65"); o documento 232 só listava o 55. São 43 códigos e 54 linhas na carga (6 + 48) |
| Evento 112110 | "não aparece em nenhum documento" | definido | A NT 2025.002 v1.53 define o 112110 (informação de efetivo pagamento integral para liberar crédito presumido do adquirente, autor emitente, modelo 55). Só os eventos 420110 a 420170 seguem sem definição (Q232-9) |
| Q231-1 (estender `Compoe_Total_Documento`) | recomendação "Não" | **encerrada** | A Q232-10 (d), lida como Sim, decide por não estender; a Q231-1 sai do documento 38 |

# 5. Leituras minhas que aguardam a sua confirmação

1. **Datas de início:** as da matriz de cBenef (última data de cada célula do PDF), as do RS e do CE na NFC-e (03/07/2023), a de SP (21/10/2024), o prazo de 180 dias da manifestação desde 02/05/2022, o `vItem` e `vNFTot` desde 01/01/2027 e os eventos da NT 2025.002 desde 06/10/2026 são leituras minhas; cada linha diz isso em `Motivo_Vigencia`.
2. **Exceções E2, E3 e E4 da matriz de cBenef:** o texto da tabela quebra de linha e o alinhamento às colunas é leitura minha. Em SC, as seis colunas de exceção foram atribuídas às regras N12-85, 86, 94, 98, N14a-10 e N14a-20 (a I05h-10 ficou sem exceção).
3. **Eventos:** `Categoria`, `Autor_Permitido`, `Ambiente_Receptor` (SVRS para o ECONF e para a RTC; ambiente nacional para a manifestação; o resto em `sefaz_uf`), `Evento_Unico` e `Somente_Recepcao` são leitura minha, exceto onde a NT diz o autor (RTC, ECONF, 110300).
4. **Os 10 códigos do estoque de abertura** (`descricao_estoque_abertura_cbs`): só o código 7 tem texto (motocicletas, art. 43 da MP 2.158-35), e o F150 diz "máquinas e implementos agrícolas" (C361 ao contador). As demais descrições são "texto a conferir" até você enviar o anexo da NT 13/2026.
5. **Descrição de código de retorno com dois textos:** o 931 vale para as regras N12-88 e N12-94 com mensagens diferentes; usei a da N12-94.
6. **Natureza e ação padrão** dos 37 códigos e **autoridade `AN_NFE`**: leitura minha, como na Carga48.
7. **A exceção 3 da W16-10** li como substituída pela exceção 4 (a NT 2023.004 v1.20 imprime as duas, e a própria NT diz "substituir a Exceção 3 pela Exceção 4"; o PDF só traz texto).

# 6. O que ficou de fora

- **Eventos 420110 a 420170** (Q232-9): sem definição em nenhuma NT recebida; ficaram fora da carga.
- **A pergunta à Receita sobre o 1950 e o 1959** (Q226-3): é você quem a envia; até a resposta o ERP guarda e não bloqueia.
- **Q229-2** (valor "recibo de passagem veicular" em `Origem_Dados_Entrada`): em espera, à espera do Manual v1.02 e do Anexo IV da NFS-e Via.
- **Q231-2** (emitente sem IE, devolução 3BA02 e NA01-20, DFeReferenciado, rejeição 301): só desenho, não aplicado.
- **Literal "SEM CBENEF"** de algumas UF e as tabelas cBenef × CST de cada UF: dependem dos portais das Fazendas e não entram.

# 7. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagens contra o previsto no documento 232 | 1.242 entidades, 14.431 campos, 3.701 referências, 374 domínios, 266 mestres, 1.508 tabelas: batem |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.508 tabelas, 3.967 chaves estrangeiras, 4.058 índices e 12.169 comentários |
| T-SQL (analisador sqlglot) | 21.703 comandos, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Carga49 | 137 + 65 + 54 + 11 linhas de regra, código e evento, mais 53 de domínio e 4 ajustes; nenhuma sobreposição de vigência na mesma chave de negócio; 65 pares (modelo, código) distintos; mensagens dos códigos copiadas das NT e do MOC 7.0; nada carregado em banco |
| Fontes lidas de novo | NT 2019.001 v1.70 (matriz e mensagens), NT 2020.001 v1.60 (H01 a H08), NT 2025.002 v1.53 (VB01, W60, eventos RTC), NT 2026.006 (110300) e MOC 7.0 (523) |
| Modelo entidade-relacional e diagramas | Regerados (110 diagramas) |

# 8. O que continua aberto

- **Você:** Q232-9 (a NT dos eventos 420110 a 420170); Q231-2; Q229-2 (espera); Q228-1 e Q228-2; a definição de **DIR** (Q221-5); a Q218-8; a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9; as Q132-5, Q130-1 a Q130-3, Q130-5, Q93-3b, Q93-8, Q118-1, Q139-1 e Q139-2, Q140-5b, 5d e 5e e Q180-3; **enviar a pergunta da Q226-3 à Receita**; o anexo da NT 13/2026 (tabela de descrição do estoque) e o texto da LC 224; o Manual v1.02 e o Anexo IV da NFS-e Via.
- **Contador:** C1 a C363 do documento 188 (a C361 inclui o código 7 da tabela do estoque).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.

# 9. Limites

- **As 137 linhas de regra, os 65 códigos e os 54 tipos de evento são provisórios.** O texto das regras vem do MOC 7.0 e das NT recebidas; a leitura por amostragem de parte das NT (seção 11 do documento 232) continua valendo.
- **O domínio `tipo_evento_dfe` tem 81 códigos fora da lista visível** e não consegui conferir se os 43 já estão lá; a carga os traz para incluir só os que faltarem.
- **A NT 13/2026 não está comigo:** as descrições dos 9 dos 10 códigos do estoque, e o campo 13 do F150, vêm do que o documento 226 registrou.
- **Nada foi validado num SQL Server nem carregado em banco;** o T-SQL foi só lido por um analisador.
- O Project continua acima do limite de tamanho (a gravação dos documentos maiores pode ser recusada), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
