# Consolidação da Revisão 42 — Documento 214

*Relatório do que entrou no dicionário com o seu "consolidar" de 11/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava aplicado**: o documento 210 inteiro (material, equipamento e gênero alimentício na base das retenções do INSS e da IN RFB 1.234; Q210-2 a Q210-12, D-N561) e o documento 207 inteiro (alíquota de IPI de 31/12/2025 das posições 8702 a 8704, por ficha de veículo; Q207-1 a Q207-6, D-N566, com a Q207-7 respondida na D-N565).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 41 | Revisão 42 | Diferença |
|---|---|---|---|
| Entidades | 1.201 | 1.206 | +5 |
| Campos | 13.801 | 13.895 | +94 |
| Campos de referência (FK) | 3.568 | 3.586 | +18 |
| Entidades mestres | 245 | 247 | +2 |
| Referências genéricas | 62 | 62 | 0 |
| Domínios de `Cad_Classe_Sistema` | 360 | 360 | 0 |
| Tabelas físicas (DDL) | 1.446 | 1.453 | +7 |
| Chaves estrangeiras (DDL) | 3.813 | 3.833 | +20 |
| Índices (DDL) | 3.904 | 3.924 | +20 |
| Comentários (DDL) | 11.579 | 11.668 | +89 |
| Comandos do T-SQL | 20.743 | 20.879 | +136 |
| Chaves opcionais que esperam a onda de destino | 81 | 84 | +3 |

**5 entidades novas** (91 campos; 4 do documento 210 e 1 do 207) e **4 existentes alteradas** (3 campos novos, 1 valor de enumeração e 2 descrições). Duas das novas têm vigência (`Cad_Gestao_Contrato_Material` e `Cad_Inss_Base_Piso_Percentual`) e viram duas tabelas cada no DDL; por isso as 5 entidades dão 7 tabelas. Quatro entidades ficam na onda 3 (Contabilidade & Fiscal) e `Cad_Gestao_Contrato_Material`, na onda 5 (Gestão de Contratos).

# 2. O que entrou

**Do documento 210 (base das retenções):**

- **`Cad_Gestao_Contrato_Material`** (19 campos, mestre, em Gestão de Contratos): o que o contrato diz que a contratada fornece junto com o serviço (material, equipamento ou gênero alimentício), com ou sem valor, na cláusula ou na planilha. O aditivo muda a lista pela vigência.
- **`Mov_Nota_Material_Discriminado`** (18 campos): o material, o equipamento e o gênero alimentício que a nota discrimina e o que foi comprovado.
- **`Mov_Retencao_Inss_Base_Apuracao`** (19 campos): a base do INSS por nota, com o regime (arts. 116 a 119 da IN 2.110), o piso aplicado, a dedução do art. 120 e a base final que o Motor reparte entre os tipos de serviço.
- **`Cad_Inss_Base_Piso_Percentual`** (14 campos, mestre): os pisos dos arts. 117 e 118 da IN 2.110; 10 linhas provisórias.
- **3 campos novos:** `Preve_Fornecimento_Material` e `Planilha_Material_Integra_Contrato` em `Cad_Gestao_Contrato`, e `Enquadramento_Emprego_Materiais` em `Mov_Titulo_Retencao` (o enquadramento da IN 1.234, art. 2º, § 7º, I; a essencialidade é da SC Cosit 220/2026, e não do texto da IN).
- **Sem campo novo:** a descrição de `Mov_Reinf_Servico_Previdenciario_Tipo.Valor_Base_Retencao` passa a dizer que o valor é o rateio da base final.
- **15 regras** (as R14 e R15 são os §§ 10 e 11 da IN 1.234) e **13 avisos** do Motor, no anexo.

**Do documento 207 (alíquota de IPI):**

- **`Mov_Aliquota_Ipi_Veiculo`** (21 campos): a `Al` da Lei 9.826 por ficha de veículo, com a Nota Complementar que decidiu (a ordem NC (87-15), (87-2), (87-3), (87-13) ou (87-14) e a alíquota-base).
- **`Mov_Credito_Automotivo_Apuracao_Ncm`:** o valor novo `calculada_pelo_motor` em `Origem_Aliquota_Ipi` e a descrição de `Aliquota_Ipi_Referencia` (a linha é por NCM e por `Al`).
- **6 condições** de cálculo da `Al` e **6 avisos** do Motor, no anexo.

**Anexo 55 do documento 10 e anexo 9 do documento 12:** as 5 entidades, os pisos, as regras, os avisos e as cargas de partida.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|---|---|---|
| `Cad_Inss_Base_Piso_Percentual` | 10 | Pisos dos arts. 117 e 118; vigência de 01/11/2022 (art. 277 da IN 2.110) |
| `Cad_Parametro_Documentacao` | 1 nova, 1 atualizada | Nova: o piso do INSS. Atualizada: o texto de `credito_auto_aliquota_ipi_tipi` (85 linhas, 2 fontes), trocado na versão atual |
| `Cad_Parametro_Efeito_Obrigacao` | 1 | O piso na EFD-Reinf, R-2010 e R-2020 (`vlrBaseRet`) |
| `Cad_Classificacao_Mercadoria.Aliquota_Ipi` | 56 | Versões novas de 01/11/2025 a 31/12/9999 (Decreto 12.549 e Tipi enviada) |
| `Cad_NCM_Ex_Tipi` | 29 | Idem, para os destaques "Ex" |
| Regras do Motor (texto) | 15 + 6 | CSV de leitura; a gravação em `Cad_Motor_Regra` é do carregador do Motor |
| Avisos do Motor (texto) | 13 + 6 | CSV de leitura |

Total: **98 linhas de carga em tabelas, 40 de texto (regras e avisos) e 85 de conferência da carga de IPI** (as duas fontes lado a lado), em 11 arquivos de dados (pasta `Carga42`, com LEIA-ME). Ordem: `01-pisos-inss` antes de `02-documentacao-parametros`; ambas depois da Carga39.

**Fora da carga, de propósito:** as linhas de material do contrato, de material discriminado e de apuração (são dados do contrato e da nota); os Ex 01 de 8703.23.10 e 8703.23.90 (C304).

# 4. Leituras minhas que aguardam a sua confirmação

1. **"Consolidar" foi lido como os documentos 210 e 207 inteiros** (D-N561, D-N565 e D-N566).
2. **A vigência de partida é a do documento:** 01/11/2022 nos pisos e nas regras do 210 (IN 2.110, art. 277) e 01/11/2025 na carga de IPI e nas regras do 207 (Decreto 12.549).
3. **O texto de `credito_auto_aliquota_ipi_tipi`** em `Cad_Parametro_Documentacao` é trocado na versão atual, sem versão nova.
4. **A marca de provisório da carga de IPI** fica em `Motivo_Vigencia`, porque `Cad_Classificacao_Mercadoria` e `Cad_NCM_Ex_Tipi` não têm situação do dado.
5. **O efeito do piso na EFD-Reinf** entra como `calcula_valor` (o piso define o valor de `vlrBaseRet`); o material não vai no arquivo.
6. **As regras e os avisos vão como CSV de texto**, como nas cargas anteriores.
7. **A ordem "depois do piso" do art. 120** (C299) **e a `Al` zero da versão sustentável** (C306) **seguem provisórias** até o contador responder.
8. **As somas previstas bateram** (1.206 entidades, 13.895 campos, 3.586 referências e 360 domínios; entidades mestres de 245 para 247). **Alertas do gerador de DDL:** os mesmos sete campos de texto sem tamanho em chave única; nenhum novo.
9. **Três chaves opcionais novas esperam a onda de destino** (81 passam a 84): `ID_Nota_Fiscal_Entrada` e `ID_Nota_Fiscal_Saida` de `Mov_Nota_Material_Discriminado` (as notas são da onda 4) e `ID_Contrato_Material` (a lista do contrato é da onda 5). São opcionais e entram na seção 3.1 do documento 31.
10. **Correção de rotina:** o cabeçalho dos arquivos de DDL (que dizia "revisão 31") e o texto de regeração dos arquivos do modelo entidade-relacional (que dizia "revisão 30") estavam parados desde aquelas revisões; passaram a dizer a revisão 42. Os arquivos de DDL e do modelo entidade-relacional das revisões anteriores já entregues ficam como estão.

# 5. Como conferi

| Conferência | Resultado |
|---|---|
| Contagem de entidades e campos contra o previsto | 1.201 + 5 entidades e 13.801 + 91 + 3 campos: **1.206 entidades e 13.895 campos**, como o modelo regerado; 360 domínios |
| Referências | 3.586 (+18: 4 de `Mov_Nota_Material_Discriminado`, 3 de `Mov_Retencao_Inss_Base_Apuracao`, 1 de `Cad_Inss_Base_Piso_Percentual`, 3 de `Cad_Gestao_Contrato_Material` e 7 de `Mov_Aliquota_Ipi_Veiculo`), como previsto |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 62 referências genéricas (sem mudança) |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.453 tabelas, 3.833 chaves estrangeiras e 11.668 comentários conferidos no banco; as sete tabelas novas foram criadas |
| T-SQL (contagem dos comandos nos oito arquivos de onda e no de comentários) | 20.879 comandos (136 a mais: 7 tabelas, 20 chaves, 20 índices e 89 comentários). **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | 4 entidades na onda 3 e 1 na onda 5; as 79 entidades empurradas por módulo posterior não mudaram; 84 chaves opcionais esperam a onda de destino |
| Carga | 98 linhas de carga em 11 arquivos de dados; colunas conferidas em todas as linhas de todos os arquivos; pisos, regras, avisos e tabela de IPI lidos dos próprios documentos 210 e 207 (nas versões aprovadas) |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** a lista de autopeças não produzidas (os Anexos I e II das Resoluções Gecex 284 e 285 ou os links do Diário Oficial; Q206-10); o Protocolo ICMS 41/2008 e o regulamento de ST de uma UF (Q209-9); o manual oficial da DeRE e o ato do fator de redução (Q198-12); a Q159-E1; as Q179-1 e Q179-3 (parte 2, também Q152-4); as Q160-8 e Q160-9.
- **Contador:** C1 a C307 do documento 188 (entre elas C296 a C302, do 210: copeiragem e piso, piso global e combinação dos arts. 117 e 118, prova do material, alimentação e transporte do art. 120, essencialidade, informação na nota ao tomador, alterações da IN 2.110 depois de 2022; e C303 a C307, do 207: Rota 2030 em 31/12/2025, os Ex 01 de 8703.23, convivência das NC (87-2) e (87-3) com a (87-13), a `Al` por ficha e outros atos de 2025).
- **Equipe e fontes oficiais:** seção 3 do documento 38 (a Q176-E2, sobre a baixa por cartão ou marketplace, segue com a equipe).
- **Fila de desenho:** o Imposto Seletivo de bebidas, fumígenos e minerais segue sem desenho.

# 7. Limites

- Os pisos do INSS vêm do **texto original da IN RFB 2.110, de 19/10/2022**; as alterações posteriores seguem em verificação (C302). A IN 1.234 foi lida no DOU de 12/01/2012 e na versão multivigente de 2019.
- A alíquota de IPI vem do **Anexo I do Decreto 12.549 (conferido no DOU)** para as 47 linhas que ele cita e da **Tipi enviada (ADE RFB 1/2026)** para as outras 38; não existe Tipi consolidada com o decreto (Q207-7). A carga é provisória.
- O ERP registra, calcula o que a norma fecha e avisa; não bloqueia (D-N284). A prova do material (art. 116, § 2º) fica com a contratada.
- O Project continua acima do limite de tamanho, e a documentação passou a ser mantida no repositório GitHub (a gravação nele é manual nesta sessão): os .md desta entrega estão na pasta `Documentacao-ERP-completa`.
