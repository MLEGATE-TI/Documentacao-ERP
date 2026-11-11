# Consolidação da Revisão 37 — Documento 199

*Relatório do que entrou no dicionário com o seu "consolidar" de 10/11/2026. Você não escolheu escopo; apliquei **tudo o que você aprovou e ainda não estava no dicionário** depois da revisão 36: o documento 198 inteiro (B4, regimes específicos de serviços financeiros, seguro e plano de saúde; Q198-1 a Q198-12, D-N530) e as Q160-1 a Q160-7 do documento 160 (parâmetros das outras obrigações; D-N531).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| | Revisão 36 | Revisão 37 | Diferença |
|-----------------------------------------------------|----------------|----------------|---------------|
| Entidades | 1.144 | 1.155 | +11 |
| Campos | 12.860 | 13.017 | +157 |
| Campos de referência (FK) | 3.365 | 3.404 | +39 |
| Entidades mestres | 228 | 232 | +4 |
| Referências genéricas | 61 | 61 | 0 |
| Domínios de `Cad_Classe_Sistema` | 353 | 355 | +2 |
| Tabelas físicas (DDL) | 1.372 | 1.387 | +15 |
| Chaves estrangeiras (DDL) | 3.593 | 3.636 | +43 |
| Índices (DDL) | 3.684 | 3.727 | +43 |
| Comentários (DDL) | 10.669 | 10.816 | +147 |
| Comandos do T-SQL | 19.319 | 19.567 | +248 |
| Entidades com FK que espera a onda de destino | 79 | 79 | 0 |

**11 entidades novas** (155 campos) e **7 existentes alteradas** (2 com campo novo, 5 só com texto ou valor de enumeração), distribuídas assim:

| Decisão | Entidades novas | Campos nelas | Campos novos em existentes |
|----------------------------------|----------------------------------|--------|------------------------|
| Q198-1 a Q198-3 (escopo, aferição mensal; D-N273 mantida) | 1 (`Mov_Regime_Especifico_Afericao`) | 33 | 0 (texto em `Cad_Redutor_Base_Dere`) |
| Q198-4 (catálogo de componentes) | 1 (`Cad_Componente_Base_Regime`) | 23 | 1 (`Cad_Cod_Trib_Dere`) |
| Q198-5 (alíquota fixada em lei) | 1 (`Cad_Regime_Aliquota_Soma`) | 12 | 1 (`Cad_Aliquota`) |
| Q198-6 (base negativa e perda excedente) | 2 (`Mov_Regime_Especifico_Saldo_Dedutivel` 10 e `Mov_Regime_Especifico_Saldo_Utilizacao` 7) | 17 | 0 |
| Q198-7 (individualização e coeficientes) | 3 (`Mov_Dere_Individualizacao` 20, `Mov_Dere_Individualizacao_Dependente` 6 e `Cad_Coeficiente_Rateio_Plano_Saude` 10) | 36 | 0 |
| Q198-8 (ativo garantidor) | 1 (`Mov_Dere_Ativo_Garantidor_Mes`) | 14 | 0 |
| Q198-9 (dedução por documento) | 1 (`Mov_Dere_Deducao_Documento`) | 11 | 0 |
| Q198-10 e Q198-11 (débito sem guia própria; participante e dispensa de DeRE) | 1 (`Cad_Participante_Regime_Base`) | 9 | 0 (texto em `Cad_Participante_Regime_Especifico`) |
| Q198-12 (manual oficial da DeRE, com você) | 0 | 0 | 0 |
| Q160-1 a Q160-7 (documento 160) | 0 | 0 | 0 (só dois textos de campo) |
| **Total** | **11** | **155** | **2** |

Quatro das onze entidades novas têm vigência e viram duas tabelas no DDL (mestres): `Cad_Participante_Regime_Base`, `Cad_Componente_Base_Regime`, `Cad_Regime_Aliquota_Soma` e `Cad_Coeficiente_Rateio_Plano_Saude`. Por isso as 11 entidades dão 15 tabelas.

# 2. O que entrou, por decisão

## 2.1 Aferição mensal do regime específico (Q198-1 a Q198-3, Q198-10)

- **`Mov_Regime_Especifico_Afericao`** (33 campos): uma linha por empresa, mês e base de cálculo, com receitas, deduções, reversão na exportação, ISS, PIS e COFINS de 2026, base, base negativa, alíquotas e o débito de CBS e IBS. O que é calculado fica gravado na própria linha (Q96-17). A fórmula é a do decreto (art. 274, § 2º, "por dentro"), com o art. 584 só em 2026.
- **D-N273 mantida:** `Cad_Redutor_Base_Dere`, `Papel_Estimativa` e a Estimativa da revisão 8 ficam como estão. O decreto só conhece "fator de redução" na importação (art. 328, § 5º); o texto de `Percentual_Redutor` diz isso, e o redutor **só entra na aferição se o contador responder à C233 que ele tem base em lei**.
- **Débito sem guia própria (Q198-10):** a aferição entrega o débito por base e mês; compensação, pagamento e split ficam no espelho e na Plataforma, e o ERP não gera guia até um ato mandar.
- **Escopo (Q198-1):** 23 bases no domínio `base_regime_especifico` (o arrendamento operacional e o financeiro têm duas bases cada), com catálogo nas 19 que a lei lista; resseguro, intermediação, FGTS e proteção mutualista ficam sem componente; prognósticos e os demais regimes do documento 94 ficam de fora.

## 2.2 Catálogo, alíquota e coeficientes (Q198-4, Q198-5, Q198-7)

- **`Cad_Componente_Base_Regime`** (23 campos, mestre): o catálogo legal do que entra na base (receita), do que se deduz e do que não integra a base, com as marcas de cada item (caixa, documento fiscal idôneo, individualização, rateio, saldo, base agregada, adquirente fora do regime regular e fator da importação). Carga de 92 linhas, provisórias. Substitui o nome `Cad_Deducao_Regime_Especifico` do documento 70.
- **`Cad_Cod_Trib_Dere.ID_Componente_Base_Regime`** (opcional): a que componente o `codTrib` da Tabela 11 pertence; fica vazio até a carga da Tabela 11 completa.
- **`Cad_Regime_Aliquota_Soma`** (12 campos, mestre) e **`Cad_Aliquota.ID_Base_Regime`**: a soma de IBS e CBS do art. 233 (10,85% em 2027 e 2028, até 12,50% em 2033 e depois), as reduções com ISS, resseguro zero, saúde e funerário com redução de 60%, pet com 30% e as três bases de alíquota do bem. 14 linhas, vigência desde 01/01/2027.
- **`Cad_Coeficiente_Rateio_Plano_Saude`** (10 campos, mestre): os dez coeficientes por faixa etária do art. 339, § 2º, II (de 0,17 a 1,00), com vigência.

## 2.3 Saldos, individualização, ativo garantidor e dedução por documento (Q198-6 a Q198-9)

- **Saldo (Q198-6):** `Mov_Regime_Especifico_Saldo_Dedutivel` (10) guarda a base negativa (cinco anos do último dia útil, sem atualização) e a perda excedente (sem prazo) por empresa e base, e `Mov_Regime_Especifico_Saldo_Utilizacao` (7) guarda o uso. A sugestão é do mais antigo para o mais novo, com troca manual; o prazo de cinco anos é parâmetro com vigência.
- **Individualização (Q198-7):** `Mov_Dere_Individualizacao` (20) e `Mov_Dere_Individualizacao_Dependente` (6), com o domínio `tipo_relacao_dere` (11 papéis) e o reaproveitamento de `Cad_Participante_Dependente`.
- **Ativo garantidor (Q198-8):** `Mov_Dere_Ativo_Garantidor_Mes` (14), do evento D-1106, que só conheço por fonte secundária; a conferência com o manual oficial fica para a Q198-12.
- **Dedução por documento (Q198-9):** `Mov_Dere_Deducao_Documento` (11); quando o documento não está no ERP (reembolso de plano de saúde), o usuário descreve o comprovante e o ERP só avisa.

## 2.4 Participante, DeRE e domínios (Q198-11)

- **`Cad_Participante_Regime_Base`** (9 campos, mestre): em quais bases o participante atua, com a dispensa de DeRE (nenhuma, parcial ou total) e o fundamento.
- **Seguradora, previdência e capitalização** entram como `instituicao_financeira`, sem valor novo em `Tipo_Regime_Especifico`; quem distingue as bases é `Cad_Participante_Regime_Base` (texto do campo).
- **Domínios:** `base_regime_especifico` (23 valores) e `tipo_relacao_dere` (11) em `Cad_Classe_Sistema`, abertos: valor novo é carga.
- **Obrigação `DERE`:** uma linha nova de `Cad_Obrigacao_Acessoria`, na carga.

## 2.5 Parâmetros das outras obrigações (documento 160, Q160-1 a Q160-7)

- **Só dois textos de campo, nenhuma entidade e nenhum campo novo:** `Cad_Obrigacao_Parametro_Definicao.Armazenamento` ganha o terceiro valor `tabela_propria` (para as 11 tabelas em leitura; as convenções da Q160-2 vão no texto do campo), e `Cad_Contribuinte_Reinf.Obrigada_Ecd` passa a dizer que o valor é copiado da linha `obrigada_ecd` do catálogo da ECD (o texto anterior dizia "vem do perfil fiscal da empresa", que não tem o campo).
- **Carga:** 59 linhas de definição do catálogo central (17 campo existente, 29 módulo, 11 tabela própria e 2 de valor central, `atividade_rural` e `obrigada_ecd`), 6 linhas novas de `Cad_Obrigacao_Acessoria` (PGDAS_D, DAS_MEI, DESTDA, DESIF, DOI e LCDPR) e a correção da obrigação da linha `gera_rascunho_nota_debito_antecipacao` para `ESCRITURACAO_IBS_CBS`.
- **Q93-6 fechada:** o indicador de atividade rural vira a linha `atividade_rural` do catálogo (ECF, booleana, empresa, valor central), e não campo do perfil.
- **Q160-8 e Q160-9** seguem sem resposta; as duas recomendações são "não" e não mudam o dicionário.

# 3. Cargas de partida (todas provisórias até o contador validar)

| Carga | Linhas | Observação |
|------------------------------------------|-------|---------------------------------------------------|
| `Cad_Classe_Sistema` (valores novos) | 34 | 23 de `base_regime_especifico` e 11 de `tipo_relacao_dere` |
| `Cad_Componente_Base_Regime` | 92 | 34 receitas, 50 deduções e 8 itens fora da base; 88 de lei e 4 só do decreto |
| `Cad_Regime_Aliquota_Soma` | 14 | vigência desde 01/01/2027 (a data da lei) |
| `Cad_Coeficiente_Rateio_Plano_Saude` | 10 | art. 339, § 2º, II |
| `Cad_Parametro_Legal_Ibs_Cbs` | 1 | `prazo_base_negativa_regime_anos` = 5 anos |
| `Cad_Obrigacao_Acessoria` | 7 | `DERE` e as 6 do documento 160; início em 01/01/2026 (uso no ERP, não a data legal) |
| `Cad_Obrigacao_Parametro_Definicao` | 59 | definições sem valor: o valor só nasce quando o contador responder na aba |
| Correção da linha `gera_rascunho_nota_debito_antecipacao` | 1 | substitui a linha de mesma chave da Carga29 |

Total: **218 linhas em 8 arquivos de dados** (pasta `Carga37`, com LEIA-ME). Ficam sem carga: o leiaute oficial da DeRE (Tabelas 11 e 12 e o evento D-1106), até você enviar o manual (Q198-12), e `Cad_Cod_Trib_Dere.ID_Componente_Base_Regime`, até a carga da Tabela 11 completa.

# 4. Leituras minhas que aguardam a sua confirmação

# 1. **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: o documento 198 inteiro e as Q160-1 a Q160-7. O leiaute oficial da DeRE (Q198-12) e o texto da MP 1.399/2026 (Q196-10) seguem com você. 2. **As Q160-8 e Q160-9, sem resposta, foram lidas como a recomendação ("não")**, o que não muda o dicionário. 3. **Módulo:** as 11 entidades ficam em Contabilidade & Fiscal (onda 3), como o documento 198 desenhou. Se você preferir outro módulo, mudo sem alterar campo. 4. **O texto novo do redutor** ficou em `Cad_Redutor_Base_Dere.Percentual_Redutor`, porque a entidade não tem campo de descrição; a D-N273 está mantida. 5. **Vigência de partida das cargas:** 01/01/2026 (uso no ERP, como a D-N323) e 01/01/2027 para as alíquotas (data da lei), todas provisórias; o contador valida (C233 a C238, documento 188). 6. **O leiaute da DeRE continua fonte secundária** até você enviar o manual oficial (1.3.0, Anexo I e Tabelas 11 e 12) e o ato conjunto do fator de redução da importação. 7. **As 6 obrigações novas** começam em 01/01/2026, a data de uso no ERP; tratei como existentes os 8 códigos que `Cad_Obrigacao_Acessoria.Codigo` cita (entre eles `ESCRITURACAO_IBS_CBS`) e os módulos DESIF_M1 a M4, sem lista de carga para conferir: confira antes de carregar. 8. **Os avisos do Motor** do B4 (documento 198, seção 6) ficam registrados em texto e não programados.

# 5. Como conferi

| Conferência | Resultado |
|--------------------------------------------------|--------------------------------------------------|
| Contagem de entidades e campos contra o previsto no documento 198 | 1.144 + 11 entidades e 12.860 + 155 + 2 campos: **1.155 entidades e 13.017 campos**, como o modelo regerado; 3.404 referências (+39) e 355 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto; 61 referências genéricas, como antes |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.387 tabelas e 3.636 chaves estrangeiras; as 11 tabelas novas e as 4 de versão foram criadas; 10.816 comentários no arquivo |
| T-SQL (analisador sqlglot, oito arquivos de onda e os comentários) | Lido sem erro; 19.567 comandos (248 a mais). **Não equivale a executar num SQL Server.** |
| Ondas | As 11 entidades na onda 3; nenhuma chave nova espera onda de destino (79, como antes) |
| Carga | 218 linhas; os 23 códigos de base e os 11 de relação têm até 30 caracteres; as 92 linhas de componente apontam para uma das 23 bases; todas provisórias |
| Modelo entidade-relacional | Regerado (15 arquivos) |

# 6. O que continua aberto

- **Você:** o manual oficial da DeRE (pacote 1.3.0, Anexo I e Tabelas 11 e 12) e o ato conjunto do fator de redução da importação (Q198-12); o texto oficial da MP 1.399/2026 (Q196-10); a Q159-E1 (equipe); as Q179-1 e Q179-3 (parte 2: planilha do leiaute 11, também Q152-4); as Q160-8 e Q160-9 (sem efeito no dicionário).
- **Contador:** C1 a C238 do documento 188 (entre elas C233 a C238, do B4).
- **Equipe e fontes oficiais:** seção 3 do documento 38; Portaria MF 2.813.
- **Fila de desenho:** a fila 156 a 160 está completa; o B0b-2 (serviço financeiro do tomador), o B6 e o B7 seguem sem desenho.

# 7. Limites

- O desenho do B4 vem da LC 214 (arts. 181 a 246, com a LC 227) e do Decreto 12.955 (arts. 13, 269 a 346, 480 e 584) que você enviou; li o FGTS só em parte e não li a proteção mutualista nem os prognósticos. **Não conferi no DOU.**
- O leiaute da DeRE (registros, Tabelas 11 e 12 e o evento D-1106) vem só de fonte secundária, não oficial.
- As marcas dos 92 componentes, a fórmula da exportação, a vigência das alíquotas desde 01/01/2027 e a sugestão do saldo mais antigo primeiro são leituras minhas (seção 4), a validar com o contador.
- Os códigos e as linhas de carga marcados como leitura minha não vêm de norma.
- O Project continua acima do limite de tamanho: nele só os documentos 14, 29, 31 e 38 são substituídos; os documentos 1 e 10 do dicionário, o 198 e o 199 seguem só nos Word desta entrega.
