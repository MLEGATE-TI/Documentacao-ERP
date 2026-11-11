# Consolidação da Revisão 40 — Documento 211

*Relatório do que entrou no dicionário com o seu "consolidar" de 11/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou na D-N548 e ainda não estava aplicado**: o documento 204 (tributação do veículo por combustível, potência e art. 149; Q204-1 a Q204-10), o B1 do documento 205 (Q205-2), o documento 206 (Programa Mover e Rota 2030; Q206-1 a Q206-12) e o documento 209 (autopeças por destinação; Q209-1 a Q209-11).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 39 | Revisão 40 | Diferença |
|------------------------------------------------------|----------------|----------------|---------------|
| Entidades | 1.173 | 1.198 | +25 |
| Campos | 13.339 | 13.738 | +399 |
| Campos de referência (FK) | 3.463 | 3.554 | +91 |
| Entidades mestres | 237 | 244 | +7 |
| Referências genéricas | 62 | 62 | 0 |
| Domínios de `Cad_Classe_Sistema` | 355 | 360 | +5 |
| Tabelas físicas (DDL) | 1.410 | 1.442 | +32 |
| Chaves estrangeiras (DDL) | 3.700 | 3.798 | +98 |
| Índices (DDL) | 3.791 | 3.889 | +98 |
| Comentários (DDL) | 11.120 | 11.519 | +399 |
| Comandos do T-SQL | 20.022 | 20.649 | +627 |
| Chaves opcionais que esperam a onda de destino | 80 | 81 | +1 |

**25 entidades novas** (384 campos, todas em Contabilidade & Fiscal e na onda 3) e **9 existentes alteradas** (5 com campos novos, 4 só com valor de enumeração ou texto), distribuídas assim:

| Decisão | Entidades novas | Campos nelas | Campos novos em existentes |
|-------------------------|---------------------------|------------|------------------------------------|
| Documento 204 (veículo: IS, IPI e art. 149) | 6 (122 campos) | 122 | 8 (6 em `Cad_NCM_Imposto_Seletivo`, 1 em cada nota de entrada e de saída) |
| B1 do documento 205 (Q205-2) | 0 (2 campos já dentro de `Mov_Is_Veiculo_Apuracao`) | incluídos nos 122 | 0 |
| Documento 206 (Mover e Rota 2030) | 18 (246 campos) | 246 | 0 (o campo `ID_Mover_Ato_Registro` já nasceu dentro de `Cad_Veiculo_Versao_Sustentavel`) |
| Documento 209 (autopeças por destinação) | 1 (`Cad_Autopecas_Perfil`, 16 campos) | 16 | 7 (3 no pedido de venda, 3 na nota de saída e 1 na informação de ST) |
| **Total** | **25** | **384** | **15** |

Sete das 25 entidades têm vigência e viram duas tabelas no DDL (mestres): `Cad_Veiculo_Versao`, `Cad_Veiculo_Versao_Sustentavel`, `Cad_Is_Veiculo_Ajuste`, `Cad_Mover_Ato_Registro`, `Cad_Mover_Habilitacao`, `Cad_Mover_Parametro` e `Cad_Autopecas_Perfil`. Por isso as 25 entidades dão 32 tabelas.

# 2. O que entrou, por decisão

## 2.1 Documento 204 e B1 do 205: veículo por combustível e potência

- **`Cad_Veiculo_Versao`** (27, mestre): a ficha técnica da versão do veículo (propulsão, potência em kW, eficiência energética, desempenho estrutural, reciclabilidade, picape e uso operacional), que a lei usa para graduar o Imposto Seletivo, o IPI até 2026 e as condições do art. 149. **`Cad_Veiculo_Versao_Sustentavel`** (18, mestre): o registro de versão sustentável do MDIC, agora ligado ao ato de registro do Mover.
- **`Cad_Is_Veiculo_Ajuste`** (16, mestre): as tabelas de ajuste por critério (cinco da MP 1.399, Anexos II e III, e as do IPI, NC 87-13 e 87-14). **`Mov_Is_Veiculo_Apuracao`** (24): a memória do cálculo do item, **com o B1**: `Condicao_Nota_Complementar` (6 notas da Tipi) e `ID_Documento_Condicao`. A NC 88-3 não tem valor, até o complemento da C263.
- **Art. 149 da LC 214** (táxi, PcD e TEA): `Cad_Beneficio_Veiculo_Reconhecimento` (16) e `Mov_Beneficio_Veiculo_Utilizacao` (21).
- **Em existentes:** 6 campos em `Cad_NCM_Imposto_Seletivo` (modo, alíquota inicial, fatores de conversão e de importação, tabela de ajuste e piso) e `ID_Veiculo_Versao` nas notas de entrada e de saída. Domínios novos: `tecnologia_propulsao_veiculo` (14 valores) e `categoria_veiculo_eficiencia` (8).

## 2.2 Documento 206: Programa Mover e Rota 2030

- **Grupo 1, ato de registro de compromissos (Decreto 12.435):** `Cad_Mover_Ato_Registro` (23, mestre), `Mov_Mover_Requisito_Ano` (14) e `Mov_Mover_Importacao_Sem_Ato` (14).
- **Grupo 2, habilitação, projeto, dispêndio e crédito financeiro (Lei 14.902):** `Cad_Mover_Habilitacao` (19, mestre), `Cad_Mover_Projeto` (14), `Mov_Mover_Projeto_Cronograma` (9), `Mov_Mover_Credito_Autorizacao_Ano` (9), `Mov_Mover_Dispendio` (16), `Mov_Mover_Dispendio_Minimo_Ano` (11), `Mov_Mover_Credito_Apuracao` (17), `Mov_Mover_Credito_Indicador` (7), `Mov_Mover_Aporte` (13) e `Mov_Mover_Habilitacao_Ocorrencia` (12).
- **Grupo 3, autopeças não produzidas:** `Mov_Autopecas_Importacao_Item` (14) e `Mov_Autopecas_Contrapartida` (14).
- **Grupo 4, obrigações e legado do Rota 2030:** `Mov_Mover_Obrigacao_Acessoria` (13) e `Mov_Rota_2030_Deducao` (13). **Parâmetros:** `Cad_Mover_Parametro` (14, mestre).
- **Em existentes (valores e texto):** `Mov_Credito_Fiscal.Origem` ganha `credito_financeiro_mover` (crédito de CSLL, art. 17 da Lei 14.902); `Mov_Titulo.Origem_Tipo` ganha `aporte_mover` e `recolhimento_mover`; `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao` passa a dizer que, no Mover e nas autopeças não produzidas, o número é o do ato do MDIC. Domínio novo: `tipo_atividade_pd_mover` (6 valores).

## 2.3 Documento 209: autopeças por destinação

- **`Cad_Autopecas_Perfil`** (16, mestre): o perfil do comprador ou da própria empresa perante a Lei 10.485, a Lei 9.826 e o Convênio ICMS 142 (tipo de pessoa, estabelecimento industrial, comercializa o mesmo bem, declaração e validade).
- **Destinação por item:** `ID_Destinacao_Autopeca`, `Origem_Destinacao_Autopeca` e `ID_Documento_Declaracao` em `Mov_Pedido_Venda_Item` e em `Mov_Nota_Fiscal_Saida_Item`; `Dispositivo_Inaplicabilidade_St` em `Mov_Nota_Fiscal_Saida_Item_St_Informacao`. Domínios novos: `destinacao_autopeca_venda` (7 valores) e `tipo_perfil_autopecas` (8).
- **Regras:** as 18 do Anexo A do documento 209 (PIS e Cofins até 31/12/2026, retenção, IPI, ICMS ST e CBS e IBS) vão como carga de texto; a destinação não muda o cálculo de CBS e IBS a partir de 2027.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|-------------------------------------------|--------|-------------------------------------------------|
| `Cad_Is_Veiculo_Ajuste` | 124 | 62 de IS (MP 1.399) e 62 de IPI (até 31/12/2026) |
| `Cad_NCM_Imposto_Seletivo` | 10 | Anexos I e V da MP 1.399 |
| `Cad_Classe_Sistema` (valores) | 52 | 43 valores dos 5 domínios novos (os 14, 8, 6, 7 e 8), 4 valores em domínios existentes do 206, `pneus_lei_10485` e 4 critérios do Motor |
| `Cad_Mover_Parametro` | 34 | 28 códigos |
| `Cad_Lista_Legal_Item` | 82 | 80 do Anexo I do Decreto 12.435 e 2 de pneus (NCM 4011 e 4013) |
| `Cad_Obrigacao_Acessoria` | 4 | `MDIC_MOVER`, `MDIC_AUTOPECAS`, `PERDCOMP` e `DUIMP` |
| `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao` | 28 + 28 | Parâmetros do Mover, pela regra da Q201-3 |
| Regras R1 a R18 do 209 (texto) | 18 | CSV de leitura; a gravação em `Cad_Motor_Regra` é do carregador do Motor |

Total: **380 linhas em 12 arquivos de dados** (pasta `Carga40`, com LEIA-ME). Ordem: `Cad_Parametro_Documentacao` antes de `Cad_Parametro_Efeito_Obrigacao`, ambas depois da Carga38 e da Carga39.

**Fora da carga, de propósito:** a lista de autopeças não produzidas (Q206-10; sem arquivo consolidado, e não li o texto oficial das Resoluções Gecex 284, 285, 935 e 951; D-N549 e D-N550); a linha de retenção de PIS e Cofins da regra R9 (espera o código de receita, C278); e as 4 linhas do catálogo central dos parâmetros por empresa do IS (documento 204, seção 5.8), porque a linha exige a obrigação em que o IS é declarado, que não existe no Projeto (C262).

# 4. Leituras minhas que aguardam a sua confirmação

# 1. **"Consolidar" foi lido como a D-N548 inteira:** os documentos 204, 206 e 209 e o B1 do 205. A correção da Q205-1 só altera o texto do documento 204, sem campo; o Word do 204 não foi reemitido. 2. **O B1 e o campo do 206 entraram direto nas entidades novas:** `Mov_Is_Veiculo_Apuracao` nasce com 24 campos e `Cad_Veiculo_Versao_Sustentavel` com 18, sem passar por ALTER. 3. **Rótulos meus na carga:** os quatro critérios do Motor do 209 (`perfil_vendedor_autopecas`, `perfil_comprador_autopecas`, `destinacao_autopeca_venda` e `lista_autopecas`) e o nível de código `posicao` das duas linhas de pneus. O rótulo do valor `autopecas_nao_produzidas` diz **Gecex, e não Camex** (correção da D-N549 e D-N550); o Word do documento 206 e a `Carga206` ainda dizem "Camex" e serão corrigidos na próxima revisão deles. 4. **A soma das referências é 3.554**, e não 3.553 como eu tinha previsto: faltou contar a do B1 (`ID_Documento_Condicao`). As demais somas (1.198, 13.738 e 360) bateram. 5. **Uma chave opcional nova espera a onda de destino** (81, e não 80): `Mov_Beneficio_Veiculo_Utilizacao.ID_Nota_Fiscal_Saida_Item`, da onda 3 para a 4. 6. **Alertas do gerador de DDL:** os mesmos sete campos de texto sem tamanho em chave única; nenhum novo. Declarar `texto (n)` continua decisão sua. 7. **Números reservados:** o documento 207 (tabela de IPI de 31/12/2025, Q205-4) e o 210 (Q210-1). O relatório é o 211 por isso.

# 5. Como conferi

| Conferência | Resultado |
|--------------------------------------------------|--------------------------------------------------|
| Contagem de entidades e campos contra o previsto nos documentos 204, 206 e 209 | 1.173 + 25 entidades e 13.339 + 384 + 15 campos: **1.198 entidades e 13.738 campos**, como o modelo regerado; 360 domínios |
| Referências | 3.554 (+91), pela regeneração; a previsão de 3.553 não contava o B1 |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 62 referências genéricas (sem mudança) |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.442 tabelas, 3.798 chaves estrangeiras e 11.519 comentários conferidos no banco; as 25 tabelas novas e as 7 de versão foram criadas |
| T-SQL (analisador sqlglot, oito arquivos de onda e os comentários) | Lido sem erro; 20.649 comandos (627 a mais: 32 tabelas, 98 chaves, 98 índices e 399 comentários). **Não equivale a executar num SQL Server.** |
| Ondas | As 25 entidades na onda 3; uma chave opcional nova espera a onda 4 (continuam as 79 entidades empurradas por módulo posterior) |
| Carga | 380 linhas em 12 arquivos; os CSV dos documentos 204 e 206 são os já entregues, só com o rótulo da lista de autopeças corrigido para Gecex; a carga do 209 saiu do próprio documento (domínios, pneus e texto das regras) |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** a lista de autopeças não produzidas (os Anexos I e II das Resoluções Gecex 284 e 285 ou os links do Diário Oficial; Q206-10); o Protocolo ICMS 41/2008 e o regulamento de ST de uma UF (Q209-9); a Q210-1 (dedução de material na base da retenção); a tabela de IPI de 31/12/2025 (documento 207) e a Tipi consolidada (Q205-4); o manual oficial da DeRE e o ato do fator de redução (Q198-12); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9; o ato do art. 414, § 2º, da LC 214 e a portaria MF 2.813.
- **Contador:** C1 a C286 do documento 188 (entre elas C256 a C265 do documento 204, C266 a C268 do 205, C269 a C277 do 206, C278 a C285 do 209 e C286 da lista de autopeças).
- **Equipe e fontes oficiais:** seção 3 do documento 38; as portarias do Mover, as 17 portarias do Rota 2030 e o ato do MDIC sobre a versão sustentável, ainda sem leitura.
- **Fila de desenho:** o B7 (marketplace) e o Imposto Seletivo de bebidas, fumígenos e minerais seguem sem desenho.

# 7. Limites

- O desenho do veículo vem da MP 1.399/2026, dos Decretos 12.549 e 12.955 e da LC 214 (art. 149), no texto que você enviou; **não conferi no DOU**, e a MP precisa ser convertida em lei (C265). O desenho do Mover vem da Lei 14.902 e dos Decretos 12.435 e 9.557, e o das autopeças, da Lei 10.485, da Lei 9.826 e do Convênio ICMS 142.
- O ICMS ST das autopeças cobre só a inaplicabilidade da cláusula nona do Convênio 142, porque o Protocolo ICMS 41/2008 não foi lido; o IPI das autopeças vale só até 31/12/2026.
- A lista de autopeças não produzidas não entrou: pelas fontes secundárias, o primeiro lote de ex-tarifários vence em 31/12/2026, e o texto oficial das resoluções não foi lido.
- O ERP não conversa com o MDIC, a Receita nem a Suframa: registra o ato, os compromissos e as ocorrências, calcula o que a lei fecha e avisa; não bloqueia (D-N284).
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1, 3, 5, 8 e 10 do dicionário, o 204, o 206, o 209, o 211 e os demais relatórios seguem só nos Word desta entrega.
