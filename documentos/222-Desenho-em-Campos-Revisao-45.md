# Desenho em Campos da Revisão 45 — Documento 222

*Desenho em campos de tudo o que você aprovou em 16/11/2026 e ainda não tinha campos: as **Q188-7 e Q188-8** (D-N584) e as **Q220-1, Q220-5 e Q221-1 a Q221-13** (D-N588). Você escreveu "consolidar" logo depois, então escrevi o desenho e **apliquei no mesmo passo** (revisão 45, documento 223). O que é leitura minha de uma resposta sua está marcado assim.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. O que cada pergunta muda no dicionário

| **Pergunta** | **Você aprovou** | **No dicionário** |
|---|---|---|
| Q188-7 (C27) | Guardar os dois prazos: a decadência do tributo e o prazo de guarda do arquivo transmitido (5 anos da última transmissão, reiniciado a cada retificação, suspenso por fiscalização) | Entidades novas `Cad_Obrigacao_Guarda_Arquivo` e `Mov_Escrituracao_Retencao_Fiscalizacao`; 2 campos novos em `Mov_Escrituracao_Arquivo`; nota em `Cad_Obrigacao_Decadencia` |
| Q188-8 (C33) | Escrituração consolidada ou individualizada por empresa, com aviso de filial sem movimento | `Cad_Efd_Contribuicoes_Opcao_Escrituracao`: `ID_Filial` vira `ID_Empresa` e `Grupo_Documento` sai; aviso A222-3 |
| Q220-1 | `Cad_NBS` guarda a hierarquia, como a NCM | `Codigo_NBS` passa de 9 posições fixas a "até 9"; entram `ID_NBS_Pai`, `Nivel` e `Analitico` (este, leitura minha) |
| Q220-5 | Aceitar as posições derivadas (271 na NCM e 45 na NBS) | Sem campo: a carga as cria e marca no `Motivo_Vigencia` |
| Q221-1 | CST de IBS/CBS com duas linhas por código (CBS e IBS) | Sem campo novo (já era uma linha por tributo); o texto "19 códigos" de `Mov_Apuracao_Tributo_Item` passa a "18" |
| Q221-2 | `Tipo_Aliquota` do cClassTrib | `Cad_Cclasstrib.Tipo_Aliquota`, com 5 valores |
| Q221-3 | Número do anexo da LC 214 (1 a 15) | `Cad_Cclasstrib.Numero_Anexo_Lc_214` |
| Q221-4 | 17 indicadores de modelo viram 17 linhas de modelo; as 2.941 marcas entram depois | Sem campo: só carga (`Cad_Modelo_Documento_Fiscal` e `Cad_Cclasstrib_Modelo`) |
| Q221-5 | `Indicador_Duimp` sai; DIR a definir | `Cad_Cclasstrib.Indicador_Duimp` removido; o DIR entra com descrição provisória |
| Q221-6 | `Indicador_Combustivel` do CFOP vira `Tipo_Combustivel` (0, 1 e 2) | `Cad_CFOP.Tipo_Combustivel`, código de 1 posição, guardado como publicado |
| Q221-7 | Crédito presumido com dois valores | `Indicador_Credito_Ibs` e `Indicador_Credito_Cbs` passam a {`nao_permite`, `exige`} |
| Q221-8 | uTrib da NCM em `Unidade_Estatistica` | Sem campo novo; o exemplo de sigla do litro passa de `L` a `LT` |
| Q221-9 | As duas tabelas de unidade, sem fundir | `Cad_Unidade_Medida.Origem_Tabela`, com 4 valores (`ambas` e `propria` são leitura minha) |
| Q221-10 | ICMS monofásico ad rem e mistura obrigatória | Entidades novas `Cad_Icms_Monofasico_Aliquota` e `Cad_Combustivel_Mistura_Obrigatoria` |
| Q221-11 | FCP por UF, prefixo GS1, tipo e espécie de veículo, regime especial e bandeiras | Entidades novas `Cad_Fcp_Aliquota_Uf`, `Cad_Gtin_Prefixo_Gs1`, `Cad_Veiculo_Tipo_Especie` e `Cad_Regime_Especial_Padrao_Numero_Processo`; domínio novo `bandeira_cartao_dfe` |
| Q221-12 | `origComb` repetível no item da nota | Entidades novas `Mov_Nota_Fiscal_Saida_Item_Origem_Combustivel` e `Mov_Nota_Fiscal_Entrada_Item_Origem_Combustivel`; 3 campos saem de cada item |
| Q221-13 | O PDF é o Anexo I da Portaria 2.000/2018 e a NBS 2.0 segue vigente (leitura minha) | Sem campo: o registro da carga da NBS sai de `com_pendencia` para `processada` |

# 2. Entidades alteradas

| **Entidade** | **O que muda** |
|---|---|
| `Cad_NBS` | `Codigo_NBS` passa a código (até 9) — identidade |
| `Cad_NBS` | campo novo `ID_NBS_Pai` (referência (Cad_NBS), opcional) |
| `Cad_NBS` | campo novo `Nivel` (enumeração {capitulo, posicao, subposicao_1, subposicao_2, item, subitem}) |
| `Cad_NBS` | campo novo `Analitico` (booleano) |
| `Cad_Cclasstrib` | campo novo `Tipo_Aliquota` (enumeração {sem_aliquota, padrao, uniforme_setorial, fixa, uniforme_nacional_referencia}, opcional) |
| `Cad_Cclasstrib` | campo novo `Numero_Anexo_Lc_214` (código (até 2), opcional) |
| `Cad_Cclasstrib` | campo `Indicador_Duimp` sai |
| `Cad_CFOP` | `Indicador_Combustivel` vira `Tipo_Combustivel` (código (1)) |
| `Cad_Credito_Presumido_Ibs_Cbs` | `Indicador_Credito_Ibs` passa a enumeração {nao_permite, exige} |
| `Cad_Credito_Presumido_Ibs_Cbs` | `Indicador_Credito_Cbs` passa a enumeração {nao_permite, exige} |
| `Cad_Classificacao_Mercadoria` | texto de `Unidade_Estatistica` corrigido: "(ex.: UN, KG, L)" passa a "(ex.: UN, KG, LT)" |
| `Cad_Unidade_Medida` | campo novo `Origem_Tabela` (enumeração {comercial, utrib_comercio_exterior, ambas, propria}) |
| `Mov_Apuracao_Tributo_Item` | texto de `ID_Cst` corrigido: "um CST próprio de 19 códigos" passa a "18 códigos" |
| `Cad_Efd_Contribuicoes_Opcao_Escrituracao` | `ID_Filial` vira `ID_Empresa` (referência (Cad_Empresa) — identidade) |
| `Cad_Efd_Contribuicoes_Opcao_Escrituracao` | campo `Grupo_Documento` sai |
| `Mov_Escrituracao_Arquivo` | campo novo `Data_Descarte_Prevista` (data, opcional) |
| `Mov_Escrituracao_Arquivo` | campo novo `Retido_Por_Fiscalizacao` (booleano) |
| `Cad_Obrigacao_Decadencia` | nota em `Base_Contagem` |
| `Mov_Nota_Fiscal_Saida_Item` | campo `Combustivel_Indicador_Importado` sai |
| `Mov_Nota_Fiscal_Saida_Item` | campo `ID_Estado_Origem_Combustivel` sai |
| `Mov_Nota_Fiscal_Saida_Item` | campo `Combustivel_Percentual_Origem` sai |
| `Mov_Nota_Fiscal_Entrada_Item` | campo `Combustivel_Indicador_Importado` sai |
| `Mov_Nota_Fiscal_Entrada_Item` | campo `ID_Estado_Origem_Combustivel` sai |
| `Mov_Nota_Fiscal_Entrada_Item` | campo `Combustivel_Percentual_Origem` sai |

# 3. Entidades novas

São **10 entidades novas e 103 campos** (já contando os campos de vigência das 7 que são mestres). As 8 de Contabilidade & Fiscal ficam na onda 3; as duas tabelas filhas do item da nota ficam na onda 4, junto com o item.

## 3.1 `Cad_Icms_Monofasico_Aliquota`

A alíquota ad rem do ICMS monofásico dos combustíveis por produto da ANP e por vigência (tabela de combustíveis monofásicos do Portal da NF-e; Convênios ICMS 199/22, 15/23 e 19/23, NT 2023.01): reais por unidade de medida do produto. O item da nota guarda o valor aplicado no complemento; esta tabela é o que o ERP usa para propor e conferir o valor, e só avisa quando diverge. A tabela de CBS e IBS é outra (`Cad_Aliquota_Combustivel`).

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 13 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Icms_Monofasico_Aliquota** | *identificador* |  |
| **ID_Icms_Monofasico_Aliquota_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Icms_Monofasico_Aliquota_Versao). ID_Icms_Monofasico_Aliquota é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Produto_Anp** | *referência (Cad_Produto_Anp) — identidade* | O produto da ANP (cProdANP) a que a alíquota se aplica. |
| **ID_Unidade_Medida** | *referência (Cad_Unidade_Medida)* | A unidade do valor ad rem: litro ou quilograma (coluna uTrib da tabela). |
| **Valor_Ad_Rem_Icms** | *número* | adRemICMS: reais por unidade, com quatro casas (arredondamento pela ABNT NBR 5891, NT 2023.01, pergunta 20). |
| **Exige_Percentual_Mistura** | *booleano* | Marca pBio da tabela: o item informa o percentual de mistura obrigatória (`Combustivel_Percentual_Biodiesel`). |
| **Exige_Origem_Combustivel** | *booleano* | Marca origComb da tabela: o item informa a origem em registros que somam 100% (tabela filha do item); no GLP e no GLGN o 100% vale em separado para o nacional e para o importado. |
| **Fundamento_Legal** | *texto, opcional* | O convênio e a cláusula da janela de vigência. A tabela do Portal não traz o ato de cada janela; o contador informa. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.2 `Cad_Combustivel_Mistura_Obrigatoria`

O percentual de mistura obrigatória do biocombustível por produto da ANP e por vigência (hoje o anidro na gasolina C: 32% desde 01/08/2026, 30% de 01/08/2025 a 31/07/2026 e 27% antes; tabela de índice da IT 2025.004 v1.20). O ERP confere o pBio do item e só avisa.

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 10 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Combustivel_Mistura_Obrigatoria** | *identificador* |  |
| **ID_Combustivel_Mistura_Obrigatoria_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Combustivel_Mistura_Obrigatoria_Versao). ID_Combustivel_Mistura_Obrigatoria é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Produto_Anp** | *referência (Cad_Produto_Anp) — identidade* | O produto da ANP a que a mistura se aplica (por exemplo, gasolina C comum ou aditivada). |
| **Percentual_Mistura** | *número* | Percentual obrigatório do biocombustível no produto (32 significa 32%). A tabela publica a fração (0,32); a carga converte. |
| **Fundamento_Legal** | *texto, opcional* | O ato que fixa o percentual; o contador informa. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.3 `Cad_Fcp_Aliquota_Uf`

A alíquota do Fundo de Combate à Pobreza por UF (tabela do Portal da NF-e): até três alíquotas possíveis por UF, e UF com teto em vez de alíquota fixa. Serve ao DIFAL e à ST; os valores calculados continuam nos movimentos.

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 13 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Fcp_Aliquota_Uf** | *identificador* |  |
| **ID_Fcp_Aliquota_Uf_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Fcp_Aliquota_Uf_Versao). ID_Fcp_Aliquota_Uf é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Estado** | *referência (Cad_Estado) — identidade* | A UF. |
| **Ordem_Aliquota** | *número — identidade* | 1 a 3: a ordem em que a tabela lista as alíquotas possíveis da UF. |
| **Tipo_Aliquota** | *enumeração {fixa, maxima}* | fixa = a alíquota; maxima = teto (RJ até 4%; GO, MT e RR trazem "máxima 2%, padrão"). UF sem FCP (AC, AP, PA e SC) tem uma linha fixa de 0%. |
| **Percentual** | *número* | Percentual do FCP (2 significa 2%). |
| **Observacao_Tabela** | *texto, opcional* | A observação da tabela do Portal (por exemplo, "UF com até 3 Alíquotas possíveis"). |
| **Fundamento_Legal** | *texto, opcional* | A lei estadual; a tabela do Portal não a traz e o contador informa. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.4 `Cad_Gtin_Prefixo_Gs1`

As faixas de prefixo da GS1 (tabela do Portal da NF-e), para o ERP validar o GTIN informado no produto (a faixa do Brasil é 789 a 790).

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 11 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Gtin_Prefixo_Gs1** | *identificador* |  |
| **ID_Gtin_Prefixo_Gs1_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Gtin_Prefixo_Gs1_Versao). ID_Gtin_Prefixo_Gs1 é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **Prefixo_Inicial** | *código (até 3) — identidade* | Primeiro prefixo da faixa, como publicado. |
| **Prefixo_Final** | *código (até 3)* | Último prefixo da faixa; igual ao inicial quando a faixa tem um só prefixo. |
| **Prefixo_Especial_Sem_Pais** | *booleano* | Verdadeiro nas faixas de uso restrito, cupom, publicação e outras que não identificam país. |
| **Entidade_Uso** | *texto* | A organização GS1 do país ou o uso da faixa, como na tabela. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.5 `Cad_Veiculo_Tipo_Especie`

Os pares de tipo e espécie de veículo do grupo veicProd da NF-e (tabela do Portal desde 12/03/2020), para validar `tpVeic` e `espVeic`.

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 11 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Veiculo_Tipo_Especie** | *identificador* |  |
| **ID_Veiculo_Tipo_Especie_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Veiculo_Tipo_Especie_Versao). ID_Veiculo_Tipo_Especie é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **Codigo_Tipo_Veiculo** | *código (até 2) — identidade* | tpVeic. |
| **Codigo_Especie_Veiculo** | *código (até 2) — identidade* | espVeic. |
| **Descricao_Tipo** | *texto* | Nome do tipo (por exemplo, Ciclomotor). |
| **Descricao_Especie** | *texto* | Nome da espécie (por exemplo, Passageiro). |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.6 `Cad_Regime_Especial_Padrao_Numero_Processo`

O padrão do número do processo de regime especial por UF (tabela do Portal da NF-e; hoje só o Paraná, `NNNNN/AAAA`), com a expressão regular da validação.

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 11 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Regime_Especial_Padrao** | *identificador* |  |
| **ID_Regime_Especial_Padrao_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Regime_Especial_Padrao_Numero_Processo_Versao). ID_Regime_Especial_Padrao é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Estado** | *referência (Cad_Estado) — identidade* | A UF que publica o padrão. |
| **Padrao** | *texto* | O padrão em letras, como publicado (por exemplo, NNNNN/AAAA). |
| **Expressao_Regular** | *texto* | A expressão regular da validação, como publicada. |
| **Exemplos** | *texto, opcional* | Os exemplos válidos da tabela. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.7 `Mov_Nota_Fiscal_Saida_Item_Origem_Combustivel`

A origem do combustível do item da nota de saída, em quantos registros forem necessários (origComb). Substitui o conjunto único de três campos do item (`Combustivel_Indicador_Importado`, `ID_Estado_Origem_Combustivel` e `Combustivel_Percentual_Origem`), que não comportava a origem repetida da NT 2023.01.

*Módulo: CRM & Vendas · sem vigência · 5 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Item_Origem_Combustivel** | *identificador* |  |
| **ID_Item** | *referência (Mov_Nota_Fiscal_Saida_Item) — identidade* | O item da nota com combustível. |
| **Indicador_Importado** | *booleano — identidade* | indImport: falso = nacional, verdadeiro = importado. |
| **ID_Estado_Origem** | *referência (Cad_Estado) — identidade* | cUFOrig: a UF de origem do produtor ou do importador. |
| **Percentual_Origem** | *número* | pOrig: o percentual originário da UF. A soma dos registros do item é 100% (no GLP e no GLGN, 100% para o nacional e 100% para o importado, em separado; NT 2023.01, perguntas 6 e 16); o ERP avisa quando não fecha. |

## 3.8 `Mov_Nota_Fiscal_Entrada_Item_Origem_Combustivel`

A origem do combustível do item da nota de entrada, em quantos registros forem necessários (origComb), como na saída. Substitui o conjunto único de três campos do item.

*Módulo: Compras · sem vigência · 5 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Item_Origem_Combustivel** | *identificador* |  |
| **ID_Item** | *referência (Mov_Nota_Fiscal_Entrada_Item) — identidade* | O item da nota com combustível. |
| **Indicador_Importado** | *booleano — identidade* | indImport: falso = nacional, verdadeiro = importado. |
| **ID_Estado_Origem** | *referência (Cad_Estado) — identidade* | cUFOrig: a UF de origem do produtor ou do importador. |
| **Percentual_Origem** | *número* | pOrig: o percentual originário da UF. A soma dos registros do item é 100% (no GLP e no GLGN, 100% para o nacional e 100% para o importado, em separado; NT 2023.01, perguntas 6 e 16); o ERP avisa quando não fecha. |

## 3.9 `Cad_Obrigacao_Guarda_Arquivo`

O prazo de guarda do arquivo transmitido de cada obrigação (resposta do contador à C27, aprovada na Q188-7): 5 anos contados da última transmissão, reiniciados a cada retificação, e retenção por tempo indeterminado enquanto o arquivo estiver em fiscalização. É outro prazo que o da decadência do tributo (`Cad_Obrigacao_Decadencia`), que fica como está. O fundamento legal segue aberto com o contador.

*Módulo: Contabilidade & Fiscal · mestre, com vigência · 13 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Guarda_Arquivo** | *identificador* |  |
| **ID_Guarda_Arquivo_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Obrigacao_Guarda_Arquivo_Versao). ID_Guarda_Arquivo é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Obrigacao** | *referência (Cad_Obrigacao_Acessoria), opcional — identidade* | A obrigação a que o prazo se aplica; vazio vale para todas as obrigações sem linha própria. |
| **Anos_Guarda** | *número* | 5 na resposta do contador. |
| **Base_Contagem** | *enumeração {ultima_transmissao}* | A data a partir da qual o prazo corre: a transmissão aceita mais recente da escrituração do período. |
| **Reinicia_Na_Retificacao** | *booleano* | Verdadeiro: a retificadora reinicia a contagem para o período inteiro, inclusive para as versões anteriores. |
| **Suspende_Em_Fiscalizacao** | *booleano* | Verdadeiro: o arquivo fica retido, sem prazo, até o fim da fiscalização (`Mov_Escrituracao_Retencao_Fiscalizacao`). |
| **Fundamento_Legal** | *texto, opcional* | O contador informa; a resposta à C27 não cita norma. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

## 3.10 `Mov_Escrituracao_Retencao_Fiscalizacao`

A retenção dos arquivos transmitidos por fiscalização: enquanto uma linha está em curso, os arquivos da empresa, da obrigação e dos períodos que ela cobre não podem ser descartados, e o ERP marca `Mov_Escrituracao_Arquivo.Retido_Por_Fiscalizacao`.

*Módulo: Contabilidade & Fiscal · sem vigência · 11 campos.*

| **Campo** | **Tipo** | **Descrição** |
|---|---|---|
| **ID_Retencao_Fiscalizacao** | *identificador* |  |
| **ID_Empresa** | *referência (Cad_Empresa)* | A empresa sob fiscalização. |
| **ID_Obrigacao** | *referência (Cad_Obrigacao_Acessoria), opcional* | A obrigação coberta; vazio cobre todas. |
| **Periodo_Inicio** | *data, opcional* | Primeiro dia dos períodos cobertos; vazio cobre desde o primeiro. |
| **Periodo_Fim** | *data, opcional* | Último dia dos períodos cobertos; vazio cobre até o último. |
| **Data_Inicio_Retencao** | *data* | Quando a empresa foi notificada da fiscalização. |
| **Data_Fim_Retencao** | *data, opcional* | Quando a fiscalização terminou; vazio = em curso, e a retenção vale. |
| **Numero_Procedimento** | *código (até 40), opcional* | O número do procedimento fiscal, quando houver. |
| **Orgao_Fiscalizador** | *texto, opcional* | Quem fiscaliza. |
| **ID_Usuario** | *referência (Cad_Usuario)* | Quem registrou a retenção. |
| **Observacao** | *texto, opcional* |  |

# 4. Domínio novo: `bandeira_cartao_dfe`

Domínio aberto de `Cad_Classe_Sistema`, com as **28 bandeiras** da tabela do Portal da NF-e. O `tPag` da nota guarda só o código de 2 posições; este domínio valida o campo. A carga sai provisória.

| **Código** | **Bandeira** |
|---|---|
| 01 | Visa |
| 02 | Mastercard |
| 03 | American Express |
| 04 | Sorocred |
| 05 | Diners Club |
| 06 | Elo |
| 07 | Hipercard |
| 08 | Aura |
| 09 | Cabal |
| 10 | Alelo |
| 11 | Banes Card |
| 12 | CalCard |
| 13 | Credz |
| 14 | Discover |
| 15 | GoodCard |
| 16 | GreenCard |
| 17 | Hiper |
| 18 | JcB |
| 19 | Mais |
| 20 | MaxVan |
| 21 | Policard |
| 22 | RedeCompras |
| 23 | Sodexo |
| 24 | ValeCard |
| 25 | Verocheque |
| 26 | VR |
| 27 | Ticket |
| 99 | Outros |

# 5. Avisos do Motor (A222-1 a A222-13)

Nenhum bloqueia: o ERP registra, calcula o que a norma fecha e avisa (D-N284).

| **N** | **Aviso** | **Quando** |
|---|---|---|
| A222-1 | Arquivo com descarte previsto em até 90 dias | `Data_Descarte_Prevista` a menos de 90 dias, sem retenção por fiscalização. Só avisa; descartar é decisão do usuário (Q188-7). |
| A222-2 | Retificadora reinicia a contagem | Ao criar a retificadora, o ERP recalcula `Data_Descarte_Prevista` de todas as versões do período (Q188-7). |
| A222-3 | Filial sem movimento na escrituração individualizada | EFD-Contribuições com `Forma_Escrituracao` = individualizada e filial sem documento no período: a filial entra no arquivo com a marca de sem movimento e o ERP avisa (Q188-8, C33). |
| A222-4 | NFC-e consolidada sem limite de tamanho | Escrituração consolidada da empresa e `Limite_Tamanho_Arquivo_Mb` vazio: a regra do Guia só permite consolidar a NFC-e se o arquivo individualizado passasse de 1 GB. |
| A222-5 | Origem do combustível não fecha 100% | A soma de `Percentual_Origem` do item é diferente de 100 (no GLP e no GLGN, a soma é conferida em separado para o nacional e para o importado; Q221-12). |
| A222-6 | Alíquota ad rem diverge da tabela | O adRem do item é diferente do valor vigente em `Cad_Icms_Monofasico_Aliquota` na data do documento (Q221-10). Só avisa. |
| A222-7 | Mistura diverge da obrigatória | O `Combustivel_Percentual_Biodiesel` do item é diferente do percentual vigente em `Cad_Combustivel_Mistura_Obrigatoria` (Q221-10). Só avisa. |
| A222-8 | cClassTrib 620003 sem grupo monofásico | A tabela traz as três marcas do grupo monofásico zeradas para o 620003, embora o CST 620 exija o grupo; o ERP usa a tabela como veio e avisa (C358). |
| A222-9 | CFOP de combustível sem produto ANP | `Cad_CFOP.Tipo_Combustivel` 1 ou 2 e item sem `Combustivel_Codigo_Anp` (Q221-6). |
| A222-10 | GTIN fora das faixas da GS1 | O prefixo do GTIN do produto não está em `Cad_Gtin_Prefixo_Gs1` (Q221-11). Só avisa. |
| A222-11 | Tipo e espécie de veículo inexistentes | O par `tpVeic` e `espVeic` não está em `Cad_Veiculo_Tipo_Especie` (Q221-11). |
| A222-12 | Número do processo de regime especial fora do padrão | O número não casa com a expressão regular da UF em `Cad_Regime_Especial_Padrao_Numero_Processo` (Q221-11). |
| A222-13 | FCP fora das alíquotas da UF | O percentual do FCP do documento não está entre as alíquotas de `Cad_Fcp_Aliquota_Uf` da UF (Q221-11). |

# 6. Cargas de partida

A pasta `Carga45-20261116` (e o zip de mesmo nome) traz todas as cargas na estrutura nova, com LEIA-ME e a ordem de carga. Ela **substitui** os arquivos de NBS, cClassTrib, CFOP e unidades das cargas anteriores.

| **Arquivo** | **Linhas** |
|---|---|
| Cad_NBS_1282_nos.csv | 1.282 |
| Cad_Cst_IBS_CBS_36_linhas.csv | 36 |
| Cad_Cclasstrib_173.csv | 173 |
| Cad_Modelo_Documento_Fiscal_17.csv | 17 |
| Cad_Cclasstrib_Modelo_2941.csv | 2.941 |
| Cad_Credito_Presumido_Ibs_Cbs_13.csv | 13 |
| Cad_CFOP_619.csv | 619 |
| Cad_Pais_NFe_261.csv | 261 |
| Cad_Municipio_5571.csv | 5.571 |
| Cad_Unidade_Medida_68.csv | 68 |
| Cad_Produto_Anp_1031.csv | 1.031 |
| Cad_Classificacao_Mercadoria_NCM_Unidade_Estatistica_10516.csv | 10.516 |
| Cad_Icms_Monofasico_Aliquota_151.csv | 151 |
| Cad_Combustivel_Mistura_Obrigatoria_23.csv | 23 |
| Cad_Fcp_Aliquota_Uf_30.csv | 30 |
| Cad_Gtin_Prefixo_Gs1_127.csv | 127 |
| Cad_Veiculo_Tipo_Especie_39.csv | 39 |
| Cad_Regime_Especial_Padrao_Numero_Processo_1.csv | 1 |
| Cad_Classe_Sistema_bandeira_cartao_dfe_28_valores.csv | 28 |
| Cad_Classe_Sistema_forma_pagamento_dfe_23_valores.csv | 23 |
| Cad_Classe_Sistema_meio_pagamento_vinculo_dfe_atualiza_6_valores.csv | 6 |
| Cad_Obrigacao_Guarda_Arquivo_1.csv | 1 |
| Avisos_do_Motor_A222_13.csv | 13 |
| Mov_Carga_Tabela_Oficial_carga45.csv | 19 |

# 7. Leituras minhas e limites

1. **`Cad_NBS.Analitico`** é extensão minha: só o subitem de 9 posições é analítico, "como na NCM". Você pediu a hierarquia; o campo que diz quem pode ser vinculado a produto e a item é consequência.
2. **`Cad_Unidade_Medida.Origem_Tabela`** tem dois valores meus além das duas tabelas: `ambas` (as 6 siglas que estão nas duas) e `propria` (unidade que o usuário cadastra).
3. **O tamanho do código da NBS por nível** é 3, 5, 6, 7, 8 e 9 posições sem pontos (capítulo 1.01 vira 101). Num primeiro rascunho eu tinha escrito 2, 4, 6, 7, 8 e 9; corrigi antes de aplicar.
4. **O ICMS monofásico tem 151 linhas**, não 191 como eu propus: as 40 linhas "atuais" repetem a janela aberta de 01/01/2026 do histórico (conferido nas 40: mesmo produto, mesma data e mesmo valor).
5. **`Cad_Efd_Contribuicoes_Opcao_Escrituracao`:** li "por empresa" como a chave passar de filial para empresa, com o grupo de documento saindo; a regra do Guia para a NFC-e (só consolidada se o arquivo individualizado passasse de 1 GB) continua em `Limite_Tamanho_Arquivo_Mb`.
6. **Fundamento legal** da guarda do arquivo, do ICMS monofásico, da mistura e do FCP fica vazio: as fontes não o trazem e o contador informa (C27 e a C358 e a C359 seguem no documento 188).
7. **Nada foi validado com o contador:** todas as cargas saem `provisorio`.
