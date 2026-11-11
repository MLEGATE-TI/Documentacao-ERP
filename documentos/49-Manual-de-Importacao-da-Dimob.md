# Manual de Importação da Dimob — Documento 49

*Leitura do manual "Instruções gerais – Importação" da Dimob (47 páginas) que Alberto enviou em 12/10/2026, comparado ao desenho do documento 33 (seção 6.2) e às entidades da DIMOB no dicionário (829 entidades). Documento de proposta e controle: nada foi alterado no dicionário. O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N114 a D-N116 (Dimob), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

O manual traz o **leiaute do arquivo de importação da Dimob**, o item que o documento 33 listava como "falta o leiaute do arquivo da DIMOB". São cinco tipos de registro: o cabeçalho `DIMOB`, a ficha de dados iniciais `R01`, a locação `R02`, a construção e incorporação `R03`, a intermediação de venda `R04` e o fecho `T9`. Os campos do desenho do documento 33 cobrem quase tudo. A leitura achou **três decisões novas** (D-N114 a D-N116), uma dúvida sobre a data do manual e nove regras de geração que entram como validação, sem campo novo.

Dois pontos pedem atenção. O primeiro: o manual **não tem data nem versão**, e o campo de ano diz "válidos 2005 a 2010", sinal de texto antigo. O leiaute não traz sublocação, cessão de direitos, permuta, percentual de participação, base recebida ou auferida, nem valor restituído, que o desenho já guarda a partir das perguntas e respostas de 2026. Antes de gerar o arquivo é preciso confirmar com a versão atual (P-R5-01). O segundo: o arquivo é **de importação**, ou seja, alimenta o programa da Dimob; a transmissão à Receita não está neste manual.

# 2. O que chegou

| Material | O que é | Situação |
|---|---|---|
| `Dimob manual.pdf` (47 páginas, impresso em 12/10/2026 a partir da ajuda do programa) | 8 páginas de leiaute e instruções, mais a tabela de códigos de município (Anexo A) | Lido inteiro |
| Anexo A, tabelas de município | Só **São Paulo (645 municípios), Acre (22) e Alagoas (102)**; o índice lista as 27 UFs, mas as outras 24 não foram impressas | Contei as linhas: os três estados estão completos |

# 3. O leiaute em resumo

Arquivo sequencial ASCII de Hex 20 a Hex 7E (sem acentos), registro de tamanho fixo por tipo, fim de registro Hex 0D0A, nome com extensão TXT. Valores em reais, 14 posições (12 inteiras e 2 decimais, sem separador); datas DDMMAAAA; CNPJ e CPF só com dígitos.

| Registro | Conteúdo | Tamanho | Campos |
|---|---|---|---|
| `DIMOB` (cabeçalho) | Constante "DIMOB" | 376 | 3 |
| `R01` | Dados iniciais: CNPJ, ano-calendário, retificadora e recibo, situação especial (data e código), nome empresarial, CPF do responsável perante a RFB, endereço, UF e município do declarante | 272 | 16 |
| `R02` | Locação: sequencial, locador, locatário, contrato (número e data), **três valores por mês** (aluguel, comissão e imposto, janeiro a dezembro), tipo, endereço, CEP, município e UF do imóvel | 801 | 54 |
| `R03` | Construção e incorporação: sequencial, comprador, contrato, valor da operação, valor pago no ano, imóvel | 251 | 18 |
| `R04` | Intermediação de venda: sequencial, comprador, vendedor, contrato, valor da venda, **valor da comissão**, imóvel | 325 | 20 |
| `T9` (fecho) | Constante "T9" | 104 | 3 |

Ordem do arquivo: cabeçalho e `R01` (obrigatórios e únicos), depois um registro por imóvel em `R02`, `R03` e `R04` (pode faltar algum tipo) e o `T9`. A importação é integral e substitui a declaração existente com as mesmas características. Erro no cabeçalho ou no `R01` impede a importação inteira; nos demais, só o registro errado é recusado.

# 4. Cruzamento com o dicionário

| Campo do leiaute | Onde está no dicionário | Resultado |
|---|---|---|
| `R01`: CNPJ, nome empresarial, endereço, UF e município do declarante | `Cad_Empresa`, `Cad_Participante_Inscricao`, `Cad_Municipio` | Coberto |
| `R01`: município com código de **4 dígitos** (o código TOM/SIAFI, não o IBGE) | `Cad_Municipio.Codigo_Siafi` (opcional) | Coberto; vira obrigatório na geração (regra 4). Tabela só de SP, AC e AL |
| `R01`: retificadora (0/1) e número do recibo (10 dígitos) | `Mov_Escrituracao_Arquivo.Finalidade` e `Numero_Recibo_Anterior` | Coberto |
| `R01`: situação especial (0/1), data do evento e código: 00 normal, 02 fusão, 03 incorporação (incorporada), 04 cisão total | `Mov_Escrituracao_Arquivo.ID_Tipo_Evento_Especial` e `Data_Evento_Especial` | Coberto; os códigos entram na tabela de conversão do tipo de evento. **O código 01 não aparece no texto**, embora o documento 33 cite a extinção: conferir (P-R5-01) |
| `R01`: CPF do responsável pela pessoa jurídica perante a RFB | `Cad_Empresa_Responsavel` (`Tipo_Papel` = `responsavel_legal`, `Indicador_Responsavel_Legal`) | Coberto, com a ressalva de que o responsável do ERP deve ser o cadastrado no CNPJ |
| `R02`: aluguel, comissão e imposto de cada mês | `Mov_Dimob_Operacao_Mensal` (`Valor_Recebido`, `Valor_Comissao`, `Valor_Imposto_Retido`) | Coberto. O acréscimo moratório e o mês da antecipação não têm campo no leiaute: o valor entra no aluguel ou na comissão, conforme `Destino_Acrescimo` |
| `R02`/`R03`/`R04`: sequencial de 7 dígitos | Sem campo | Gerado na geração do arquivo, por tipo de registro, de 0000001 em diante (regra 1) |
| `R02`: locador, locatário, comprador e vendedor (CPF ou CNPJ e nome de 60 posições) | `Mov_Dimob_Operacao` e `Mov_Dimob_Operacao_Parte` | Coberto; nome acima de 60 posições é cortado (regra 2) |
| `R02`: locatário aceita **NDP** (não domiciliado no País) | `Mov_Dimob_Operacao_Parte.Indicador_Ndp` | Coberto, mas o leiaute só aceita NDP no locatário da locação (regra 5) |
| Número do contrato com **6 posições** | `Numero_Contrato` (até 30) | **Lacuna: D-N115** |
| Data do contrato | `Data_Contrato` | Coberto; regra de período (regra 6) |
| `R03`: valor da operação e valor pago no ano | `Valor_Operacao` e `Valor_Pago_Ano` | Coberto; um dos dois precisa ser maior que zero (regra 7) |
| `R04`: valor da venda e **valor da comissão** | `Valor_Operacao`; comissão sem campo (o `Valor_Comissao` do dicionário é só mensal, da locação) | **Lacuna: D-N114** |
| Tipo do imóvel: U (urbano) ou R (rural) | `Cad_Imovel.Destinacao` (opcional) | Coberto; obrigatório quando há operação na Dimob (regra 3) |
| Endereço do imóvel em um campo de 60 posições, CEP, município (código de 4 dígitos) e UF | `Cad_Imovel` (`Logradouro`, `Numero`, `Complemento`, `Bairro`, `Cep`, `ID_Municipio`) | Coberto; o endereço é montado juntando os campos e cortado em 60 posições |
| Ficha ligada ao tipo de operação | `Mov_Dimob_Operacao.Tipo_Operacao` | Coberto, com o mapa da seção 5 |

# 5. Que operação vai em qual registro

| `Tipo_Operacao` do dicionário | Registro |
|---|---|
| locação, sublocação, intermediação de locação | `R02` |
| venda de imóvel próprio, incorporação, construção, loteamento | `R03` |
| intermediação de venda | `R04` |
| cessão onerosa de direitos, permuta | Sem registro próprio no leiaute lido: conferir (P-R5-01) |

A sublocação, a cessão de direitos, a permuta, o contrato sub judice, a rescisão e o valor restituído não aparecem em nenhum campo. O desenho continua guardando esses dados, que servem para calcular o que vai nos campos, mas **não saem como campo próprio** até a versão atual do leiaute dizer outra coisa.

# 6. Decisões propostas

| ID | Proposta | Motivo |
|---|---|---|
| D-N114 | `Valor_Comissao` (número, opcional) em `Mov_Dimob_Operacao`, para a comissão da intermediação de venda | O `R04` tem o campo e exige que valor da venda ou comissão seja maior que zero; o dicionário só guarda comissão por mês, na locação |
| D-N115 | `Numero_Contrato_Declarado` (código de 6, opcional) em `Mov_Dimob_Operacao` | O leiaute aceita 6 posições; o `Numero_Contrato` vai até 30. O campo guarda o que foi declarado, para o número não mudar de um ano para o outro nem colidir quando o original for cortado |
| D-N116 | A Dimob segue o modelo da DES-IF (documento 39): o ERP gera o arquivo TXT de importação e registra o recibo; **a importação e a transmissão ficam no programa da Receita**. Sem entidade nova | O manual descreve só o arquivo de importação. `Mov_Escrituracao_Arquivo` já guarda o arquivo gerado (`ID_Documento_Arquivo`), o recibo (`ID_Documento_Recibo`) e o certificado |

# 7. Regras de geração (validação, sem campo novo)

1. **Sequencial** por tipo de registro, de 0000001 a 9999999, gerado na hora de montar o arquivo (o leiaute ainda aceita 5 dígitos).
2. **Texto em ASCII sem acentos** (Hex 20 a 7E): nomes e endereços são normalizados e cortados nas posições do leiaute (nome 60, endereço 60).
3. **Tipo do imóvel** U ou R obrigatório: a geração barra a operação com `Cad_Imovel.Destinacao` vazia.
4. **Código de município** de 4 dígitos obrigatório (`Codigo_Siafi`): a geração barra município sem ele.
5. **NDP** só no locatário do `R02`. Nos campos de comprador e vendedor, o leiaute lido pede CPF ou CNPJ válido; parte sem CPF nesses registros precisa de confirmação (P-R5-01).
6. **Datas**: na locação, entre 1950 e o ano-calendário; na incorporação e na intermediação, só dentro do ano-calendário declarado.
7. **Valores**: no `R03`, valor da operação e valor pago no ano não podem ser os dois zero; no `R04`, valor da venda e comissão idem. Valor vazio é preenchido com zeros.
8. **Vários proprietários ou compradores**: um registro por pessoa, como diz a resposta oficial (documento 33). O leiaute não tem campo de percentual, então o valor de cada registro deve ser a parte da pessoa. Essa conta é inferência minha e entra em P-R5-01.
9. **Críticas do programa**: erro no cabeçalho ou no `R01` impede tudo; nos outros registros só recusa o registro. O validador do ERP repete essas críticas e grava cada uma em `Mov_Escrituracao_Arquivo_Ocorrencia` (campos `Registro` e `Campo`).

# 8. O que ainda falta

1. **Manual atual da Dimob** (ou a confirmação de que este é o atual): o texto não tem data e fala em anos 2005 a 2010.
2. **Tabelas de município das outras 24 UFs** (Anexo A). Também serve a tabela TOM/SIAFI pública da Receita.
3. **Código 01 da situação especial** (extinção) e o tratamento de cessão de direitos, permuta e sublocação no arquivo.
4. **Passo de transmissão** (programa da Dimob e Receitanet): este manual só cobre o arquivo de importação.

# 9. Perguntas para Alberto

| ID | Pergunta | Se não responder |
|---|---|---|
| P-R5-01 (respondida em 12/10/2026: **sim, é o atual**) | Este manual é da versão atual da Dimob? Se há um mais novo, mande-o; ele dirá se sublocação, permuta, percentual de participação e NDP em comprador existem no arquivo | Respondida: o arquivo sai só com o que este leiaute traz (seções 3 e 7); sublocação, permuta, percentual e demais dados ficam como dado interno de cálculo. D-N114 a D-N116: Alberto respondeu "como recomendado" em 12/10/2026. A dúvida sobre o código 01 e sobre NDP em comprador e vendedor segue com o contador |

# 10. Fontes e verificação

**Oficial.** Manual "Instruções gerais – Importação" da Dimob, impresso da ajuda do programa (PDF de 47 páginas), lido inteiro.

**Verificação feita.** Conferi cada entidade e campo citado contra o dicionário de 829 entidades (`Mov_Dimob_Operacao`, `Mov_Dimob_Operacao_Mensal`, `Mov_Dimob_Operacao_Parte`, `Cad_Imovel`, `Cad_Municipio`, `Cad_Empresa_Responsavel` e `Mov_Escrituracao_Arquivo`). Contei as linhas das tabelas de município: SP 645, AC 22, AL 102.

**Não verificado.** Se o leiaute é o vigente; o código 01 da situação especial; a transmissão à Receita; o tratamento de NDP em comprador e vendedor.
