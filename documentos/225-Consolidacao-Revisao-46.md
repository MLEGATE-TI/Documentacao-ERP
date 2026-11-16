# Consolidação da Revisão 46 — Documento 225

*Relatório do que entrou no dicionário com o seu "consolidar" de 16/11/2026, depois de aprovar a Q188-6 (aplicar as 21 respostas do contador) e as Q224-1 a Q224-3 (seguir com as recomendações). O escopo é o desenho do documento 224 como você o aprovou; não entrou nada além dele.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 45** | **Revisão 46** | **Diferença** |
|---|---|---|---|
| Entidades | 1.239 | 1.239 | 0 |
| Campos | 14.364 | 14.365 | +1 (`Eh_Imposto_Devido`) |
| Campos de referência (FK) | 3.682 | 3.682 | 0 |
| Entidades mestres | 266 | 266 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Domínios de `Cad_Classe_Sistema` | 370 | 370 | 0 |
| Tabelas físicas (DDL) | 1.505 | 1.505 | 0 |
| Chaves estrangeiras (DDL) | 3.948 | 3.948 | 0 |
| Índices (DDL) | 4.039 | 4.039 | 0 |
| Comentários (DDL) | 12.104 | 12.105 | +1 |
| Comandos do T-SQL | 21.597 | 21.598 | +1 |
| Chaves opcionais que esperam a onda de destino | 85 | 85 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos |  | Fase 0 92, Contabilidade & Fiscal 64, CRM & Vendas 26, Compras 31 |  |

Foram tocados **25 campos em 19 entidades** (mais a tabela de valores iniciais de `Cad_Regra_Vencimento`, que mora no texto da Fase 0): **1 campo novo**, **2 campos que passam de obrigatório a opcional** (com texto novo) e **22 campos só com texto novo**. Nenhum campo perdeu texto. O documento 224 falava em "23 campos" de texto; a contagem feita sobre o modelo é 22 de texto mais os 2 de obrigatoriedade e o campo novo.

# 2. O que entrou

**Campo novo (C8 e Q224-2):** `Cad_Ecf_Tabela_Dinamica_Linha.Eh_Imposto_Devido` (booleano) marca a linha que traz o imposto devido da aba: **N630A linha 26** (IRPJ) e **N670 linha 21** (CSLL). N620 26, N660 18, N630B 23 e N630C 23 ficam sem marca e o Motor avisa. O campo é obrigatório no DDL (booleano sem padrão, como os demais): a carga leva a coluna para todas as linhas.

**Obrigatório a opcional (C32 e Q224-1):** `Chave_Acesso` em `Mov_Nota_Fiscal_Entrada` e em `Mov_Nota_Fiscal_Saida`. O Motor exige a chave quando `Cad_Modelo_Documento_Fiscal.Eletronico` é verdadeiro e aceita a nota sem chave nos modelos 01, 1B, 04, 02, 2D, 2E, 06, 28 e 29; os casos por modelo seguem abertos.

**Texto novo em 22 campos** ("Revisão 46 (documento 224; D-N590: Cn): ..."): ECF (C6 no indicador de pagamento ao exterior; C7, C10 e C11 na fórmula; C8), classificação 85 do declarante (C14 e), competência do crédito de PIS e Cofins (C20), presunção da CSLL (C21), ISS fixo por profissional (C22 a), fim da EFD-Contribuições (C25), feriado nacional (C28), centro de custo no I051 (C207), bons antecedentes (C226), multa de mora e juros sobre a multa punitiva (C227), contribuinte na industrialização por encomenda (C232), arredondamento do IS de veículos (C256), potência em kW (C258 e C262), motorização do táxi (C261) e declaração do comprador de autopeças (C279).

**Tabela de valores iniciais de `Cad_Regra_Vencimento` na Fase 0 (C14 a, b e c):** seis famílias validadas (contribuição previdenciária no dia 20, PIS e Cofins no dia 25, IPI no dia 25, IRPJ e CSLL no último dia útil, FGTS Digital no dia 7 e DAS no dia 20), PIS e Cofins de financeiras no dia 20, IRRF no dia 20 do mês seguinte ao pagamento e o texto de que IOF e CIDE no resgate são descontados na conta, sem guia própria. Seguem a definir o IRRF por período e o IOF por operação.

**Módulos tocados:** 01 (Fase 0, revisão 92), 10 (Contabilidade & Fiscal, revisão 64), 05 (CRM & Vendas, revisão 26) e 03 (Compras, revisão 31).

# 3. Cargas de partida (`Carga46-20261116`)

A pasta (e o zip de mesmo nome, com LEIA-ME e ordem de carga) traz **só as linhas a alterar ou a incluir**, com a chave de negócio, CSV com BOM e separador ";".

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_Ecf_Tabela_Dinamica_Linha_ALTERAR` | 23 | chave (tabela, código, início da vigência): 22 linhas de nota (as 11 fórmulas de 2026 e as 11 de até 2025: só `Motivo_Vigencia`) e a M350R 345 com `M350(343) - M350(344) + M350(170)` (C7, C10 e C11) |
| `Cad_Ecf_Tabela_Dinamica_Linha_Eh_Imposto_Devido` | 4.491 | "nao" em todas as chaves, "sim" em três (N630A 26 nas duas vigências e N670 21); as chaves vêm da Carga26 mais 3 linhas da Carga29 |
| `Cad_Presuncao_Acrescimo_ALTERAR` | 1 | CSLL de 01/04/2026: `Situacao_Dado` = validado (R$ 3.750.000 em 2026); 2027 e o limite trimestral seguem provisórios |
| `Cad_Regra_Vencimento` | 10 | 9 validadas e 1 provisória (ajuste anual de março); seletor de origem e raiz de código de receita a conferir |
| `Cad_Obrigacao_Parametro_Definicao`, `Cad_Parametro_Documentacao`, `Cad_Parametro_Efeito_Obrigacao` | 4 + 4 + 5 | os quatro parâmetros `is_veiculo_*`: `arredondamento_casas` (padrão 4) e `kw_derivado_do_cv` (padrão falso) validados; `item_sem_cat` e `tabela_fora_da_lista` provisórios; vigência de 02/02/2027 |

Total: **4.538 linhas de dados** em 7 arquivos (com LEIA-ME).

# 4. Leituras minhas que aguardam a sua confirmação

1. **Obrigação dos parâmetros `is_veiculo_*`:** o documento 204 não diz a obrigação; usei **`ESCRITURACAO_IBS_CBS`**, porque a apuração do IS do item mora na mesma apuração. Se for outra, troco a linha de efeito (`Cad_Parametro_Efeito_Obrigacao`).
2. **Vigência de 02/02/2027** para os quatro parâmetros, como `Cad_Is_Veiculo_Ajuste`.
3. **`Cad_Regra_Vencimento`:** o seletor de origem e a raiz de código de receita das 10 linhas ficam a conferir contra `Cad_Codigo_Receita_Raiz`; PIS e Cofins, IPI e IRPJ/CSLL não têm seletor estruturado nesta carga; o dia não útil de cada linha é leitura do dicionário (a C14(f) voltou ao contador).
4. **Cargas originais não vistas:** não encontrei nesta sessão as cargas originais de `Cad_Presuncao_Acrescimo` e de `Cad_Regra_Vencimento`. A `Carga46` traz a alteração por chave e as 10 linhas como valores iniciais; se elas já existirem no seu banco, trate como alteração de linha e confira.
5. **Leituras dentro das respostas:** unidade da alíquota do IS de veículos (percentual, C256), contribuinte da industrialização por encomenda (o encomendante, C232), aviso em vez de bloqueio nos bons antecedentes (C226), alcance da C14(d) (não vale para a tabela do Mafon; C360 ao contador) e a data de entrada da nota como competência (C20, a conferir).
6. **Texto do Limite_Receita_Anual:** a resposta da C21 não cita a MP 1.303/2025; a leitura de que ela não mexe no limite é minha e não foi conferida na fonte.

# 5. O que ficou de fora

- **C14(f), C22(b) e C249** voltam ao contador (documento 224, seção 4); a C360 é nova.
- Partes abertas das respostas aplicadas (obrigatoriedade do Y520, IRRF por período, IOF por operação, exceções do IPI, prazos da Reinf, ato oficial do fim da EFD-Contribuições, Carnaval e Corpus Christi, casos por modelo de nota, data inicial dos juros, fumígenos e IS misto, base legal do adendo do táxi, obrigação acessória do IS) seguem no documento 188, em "Ainda aberto".

# 6. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagem contra o previsto | 1.239 entidades; 14.364 + 1 = **14.365** campos; 3.682 referências; 266 mestres; 63 referências genéricas; 370 domínios |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.505 tabelas, 3.948 chaves estrangeiras e 12.105 comentários |
| T-SQL (contagem e leitura) | 21.598 comandos lidos por um analisador de T-SQL, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | `Eh_Imposto_Devido` fica na onda 3 com a entidade; as 81 entidades empurradas e as 85 chaves opcionais que esperam a onda de destino não mudam (quadros 2.2 e 3.1 do documento 31 comparados com os anteriores: nenhuma linha mudou) |
| Documentos 29, 31, 14, 38, 188 e 224 | Totais e quadros do documento 31 regerados do modelo; as 21 respostas do 188 marcadas "aplicada na revisão 46"; o documento 38 não guarda mais o estado "espera o consolidar" |
| Modelo entidade-relacional e diagramas | Regerados |

# 7. O que continua aberto

- **Você:** a definição de **DIR** (Q221-5); a **Q218-8** (só o Ajuste SINIEF 14/2025 e o 01/92); a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9.
- **Contador:** C1 a C360 do documento 188 (as 21 respostas aplicadas ganharam a nota; C14(f), C22(b) e C249 voltaram a ele; C360 é nova).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.
- **Fila de desenho (minha):** o split payment (adiado por você) e a carga da lista de autopeças não produzidas (espera a Q206-10).

# 8. Limites

- **Nenhuma das 21 respostas do contador cita norma;** C21, C258(d) e C25 pedem fonte oficial que ainda não li.
- **Nada foi validado num SQL Server;** o T-SQL foi só lido por um analisador.
- O Project continua acima do limite de tamanho (a gravação dos documentos 224 e 188 foi recusada), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
