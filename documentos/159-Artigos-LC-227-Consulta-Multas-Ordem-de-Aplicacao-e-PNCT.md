# Artigos da LC 227/2026 sem desenho, artigos mal extraídos, consulta, multas, ordem de aplicação e PNCT — Documento 159

> **O que este documento faz.** É o quinto da fila que você escolheu (156, 157, 150, 158, **159** e 160). Ele (1) **reextrai os nove artigos que o documento 138 não conseguiu ler** (14, 22, 28, 41, 59, 60, 195, 243 e 271); (2) **refaz a lista dos artigos "sem desenho"** com o texto da LC 227 e o texto consolidado do Planalto; (3) separa o que **entra em bloco já na fila**, o que já está coberto e o que não tem efeito; e (4) **propõe o desenho** do que é de fato novo: a ordem de aplicação dos institutos (art. 7º-A), a consulta e o contencioso (arts. 323-A a 323-M), as multas (arts. 341 a 341-H) e o PNCT (arts. 471-A a 471-C). **Nada foi aplicado ao dicionário**: continua na revisão 35 (1.138 entidades e 12.769 campos). O que você aprovar entra na revisão 36 no próximo "consolidar".

*Fontes: o texto da LC 227/2026 (Câmara dos Deputados), o texto consolidado da LC 214 do Planalto com as marcas da LC 227 (os dois textos legais que estão na sessão desde 03/11/2026), o dicionário na revisão 35 e os documentos 10, 14, 94, 115, 138, 155, 156, 157 e 158. Conferi cada artigo no texto da lei, e não no decreto.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **Os nove artigos mal extraídos, relidos:** **cinco não foram alterados pela LC 227** (14, 41, 195, 243 e 271 não têm marca da LC 227 nem no texto da lei nem no consolidado; o art. 14 do documento 138 era uma nota do CTN dentro do art. 6º, XII). **Quatro foram alterados e agora estão lidos:** o art. 22 (plataformas, §§ 13 a 15), o art. 28 (energia elétrica), o art. 59 (DTE unificado) e o art. 60 (documentos consolidados).
- **Correção ao documento 138.** A linha "art. 95 (plataformas)" da tabela de impacto ALTO descreve o texto do **art. 22, §§ 13 a 15**. O art. 95 da LC 214 (remessa internacional) **não tem marca da LC 227** em nenhuma das duas fontes. A Q138-6 já mandava o desenho das plataformas para o B7; só o número do artigo estava errado.
- **A lista dos 131 artigos.** O CSV do documento 138 (`conferencia_lc227_por_artigo.csv`, na pasta ERP-Revisao25) foi encontrado e comparado artigo por artigo (Anexo B, seção 9). Os dois têm 131 artigos e **124 coincidem**. O CSV traz sete que a minha lista não traz (7, 14, 41, 95, 195, 243 e 271), todos sem marca da LC 227 nas minhas fontes. A minha lista traz sete que o CSV não traz (3, 6, 7-A, 201, 341, 438 e 471); pesam o 7-A (ordem de aplicação) e o 341 (multa de ofício duplicada no regime especial). Os outros artigos que eu suspeitava ausentes (152, 217, 323-H a 323-M, 341-B, 350 e 493-A) estão no CSV.
- **Dos 131**, o documento 138 classificou 11 como ALTO e 30 como MÉDIO; três desses 41 (95, 195 e 243) não têm marca. **Dos outros 38, só 18 têm desenho ou decisão** (10 nos documentos 156, 157, 150 e 158, 7 na Q138 e o art. 471-C neste documento), 1 é parcial (64) e **19 só têm o destino apontado pelo documento 138, sem desenho** (Anexo B; a versão de 10/11/2026 dava os 38 como encaminhados, o que estava errado). Da minha lista, restam **93 artigos** (tabela da seção 3): **21 vão para desenho neste documento**, 14 entram em blocos já na fila, 13 já estão cobertos, 10 são texto de regra sem campo, 5 só entram com cliente, 23 não têm efeito no ERP e 7 viram pergunta.
- **Desenho proposto:** **5 entidades novas (62 campos)**, **10 campos novos em duas existentes** (`Cad_Cclasstrib` e `Mov_Auto_Infracao`), cinco domínios novos e um valor novo em `programa_conformidade` (`pnct`). Se tudo for aprovado: **1.143 entidades, 12.841 campos, 3.357 campos de referência (FK) e 349 domínios**.
- **A decisão que mais pesa é a das multas (Q159-4).** A D-N284 decidiu que o ERP só **registra** o auto de infração e não calcula multa. Respeitei isso (opção A: 8 campos em `Mov_Auto_Infracao`, sem tabela de multas). A opção B (catálogo das 28 penalidades, UPF e simulação) está descrita só na pergunta Q159-4 e só entra se você quiser rever a D-N284.
- **Perguntas:** Q159-1 a Q159-11 na seção 6, cada uma com recomendação. Dos contadores: Q159-C1 a Q159-C4. Da equipe: Q159-E1.

# 2. Os nove artigos mal extraídos, relidos

Li cada um no texto da LC 227 (parte que altera a LC 214, a partir do art. 174 da lei) e no consolidado do Planalto.

## 2.1 Resultado

| Art. | O que o documento 138 viu | O que o texto mostra | Destino |
|---|---|---|---|
| 14 | "Nota do CTN" | O art. 14 da LC 214 (alíquotas fixadas por lei de cada ente) **não tem marca**. O CTN, art. 14, é citado dentro do art. 6º, XII, alterado | Sem efeito |
| 22 | Alíneas faltando | **Alterado.** Inciso II (responsabilidade solidária da plataforma: não informa o § 5º, ou o fornecedor contribuinte não emite o documento), § 7º (a plataforma não responde pela diferença quando o split é possível e ela informa o que os §§ 5º e 6º pedem), §§ 8º e 9º revogados, § 13 (a plataforma pode optar, com anuência do fornecedor, por ser **substituta tributária**), § 14 (30 dias para emitir o documento; os acréscimos e a multa recaem só no fornecedor), § 15 (alíquota de referência na falta de informação, com acerto depois) | B7 |
| 28 | "Nota da Lei 5.764" | **Alterado.** Quem recolhe o IBS e a CBS da energia elétrica: a distribuidora (ambiente regulado e uso do sistema), o alienante (ambiente livre, ou adquirente fora do regime regular), o comercializador varejista ou o estabelecimento consumidor (compra multilateral) e a transmissora (transmissão e conexão); fornecimento da transmissão no momento do art. 10, § 3º | Pergunta Q159-9 |
| 41 | Conteúdo trocado | **Sem marca.** Define o regime regular | Sem efeito |
| 59 | Truncado | **Alterado:** § 5º, o Domicílio Tributário Eletrônico (art. 332) é **unificado no IBS e obrigatório** para todas as entidades e pessoas jurídicas sujeitas à inscrição no CNPJ | Texto de regra |
| 60 | Truncado | **Alterado:** § 7º, o ato conjunto do § 3º deve permitir **documentos fiscais consolidados** | Pergunta Q159-10 |
| 195 | Truncado | **Sem marca.** Títulos de dívida no regime de serviços financeiros | Sem efeito |
| 243 | Conteúdo era o art. 5º, §§ 9º e 10 | **Sem marca.** Plano de saúde de animais domésticos | Sem efeito |
| 271 | Conteúdo era o art. 7º-A | **Sem marca.** Cooperativas | Sem efeito |

## 2.2 O "art. 95" do documento 138

A tabela do documento 138 (seção 4) descreve o "art. 95" com o § 13 (a plataforma pode ser substituta tributária) e o § 14 (acréscimos só ao fornecedor). Esses parágrafos são do **art. 22**. O art. 95 da LC 214 trata da responsabilidade solidária do fornecedor na remessa internacional com tributação simplificada e **não foi alterado**. Corrijo no documento 14 e no 38: onde se lê art. 95 (plataformas), lê-se art. 22. A conclusão do documento 138 (os três valores de responsabilidade que o documento 70 propôs para `Cad_Participante_Plataforma_Fornecedor`, entidade que ainda não existe no dicionário, não cobrem a substituição tributária nem a alíquota provisória) **vale**, e o B7 a recebe.

# 3. Os artigos da LC 227 depois dos 41 do documento 138

Cada linha traz o assunto lido no texto e o destino. "Já coberto" significa que achei a entidade ou o documento que trata do assunto; **não conferi campo a campo** o texto novo contra a entidade, só o assunto e os números que a LC 227 trouxe (por exemplo, 3,65% do art. 487 e R$ 600 do art. 260).

| Art. | Assunto | Destino | Observação |
|---|---|---|---|
| 3 | § 3º: locação, arrendamento e cessão temporária são fornecimento | Já coberto | Locação já tratada (documentos 34 e 41; D-N33 e D-N60). |
| 4 | §§ 4º e 6º: ativo não circulante e atividade não habitual; pessoa física contribuinte fora da atividade | Texto de regra, sem campo | A qualificação por vigência já guarda a condição (`Cad_Participante_Qualificacao_Cbs`); regra do Motor. |
| 6 | XII: contribuições associativas estatutárias não são fornecimento | Texto de regra, sem campo | Entra como linha de classificação (carga) se o contador confirmar. |
| 7-A | Ordem de aplicação e cumulação dos institutos | Desenho neste documento | Seção 4.1. |
| 12 | § 9º: base da energia elétrica multilateral é a liquidação da CCEE | Já coberto | `Mov_Energia_Ccee_Liquidacao` (documento 156, Q156-9). |
| 22 | §§ 13 a 15: plataforma digital substituta tributária; alíquota de referência na falta de informação | B7 (marketplace e PSP) | É o texto que o documento 138 chamou de "art. 95" (seção 2.2). |
| 28 | Energia elétrica: quem recolhe (distribuidora, alienante, comercializador varejista, estabelecimento consumidor, transmissora) | Pergunta | Q159-9. |
| 34 | V, a: quem segrega e recolhe no split | Texto de regra, sem campo | Depende da volta do split (D-N282). |
| 58 | §§ 4º e 5º: gratuidade do acesso aos mecanismos de integração; custo das transações extras | Sem efeito no ERP | Direito do contribuinte; sem dado a guardar. |
| 59 | § 5º: Domicílio Tributário Eletrônico unificado e obrigatório para todo CNPJ | Texto de regra, sem campo | O ERP já recebe mensagens do DTE (`Mov_Caixa_Postal_Fiscal`); a regra é de aviso. |
| 60 | § 7º: o ato conjunto deve permitir documentos fiscais consolidados | Pergunta | Q159-10. |
| 71 | Alíquota da importação igual à da aquisição no País; ressalva do art. 126, § 6º (RTS) | B1 (comércio exterior) | — |
| 73 | Parágrafo único: responsabilidade excluída por caso fortuito ou força maior | Texto de regra, sem campo | Aviso do Motor; sem campo. |
| 76 | § 3º: pagamento posterior para OEA e para remessas no RTS | B1 (comércio exterior) | Prazo parametrizado no B1. |
| 98 | Abastecimento de aeronave em tráfego internacional é exportação | B1 (comércio exterior) | — |
| 98-A | Regimes aduaneiros especiais aplicados a bens com destino ao exterior | B1 (comércio exterior) | — |
| 98-B | Suspensão vira alíquota zero com a destruição do bem sob controle aduaneiro | B1 (comércio exterior) | — |
| 116 | § 5º vetado | Sem efeito no ERP | — |
| 117 | § 2º, I: o consumo do cashback exclui o que está sujeito ao Imposto Seletivo | Texto de regra, sem campo | Regra do cálculo do cashback; sem campo. |
| 149 | Automóvel para taxista e para pessoa com deficiência ou TEA: limite de R$ 200.000 e benefício até R$ 100.000 (inciso II) | Desenho neste documento | `Cad_Parametro_Legal_Ibs_Cbs` (seção 4.2); o dicionário não tinha esses números. |
| 152 | Intervalo mínimo de 3 anos para o inciso II (2 anos para o táxi) | Desenho neste documento | `Cad_Parametro_Legal_Ibs_Cbs`. |
| 156 | Alíquota zero na pesquisa e desenvolvimento por ICT sem fins lucrativos e fundação de apoio | Texto de regra, sem campo | Linha de classificação (carga); o registro do ICT já cabe em `Numero_Comprovante` da qualificação. |
| 201 | Arrendamento mercantil: base no regime de caixa, na medida do recebimento | B4 (serviços financeiros) | Liga ao arrendamento mercantil previsto no B0b-2 (`Cad_Arrendamento_Mercantil` ainda não existe). |
| 212 | FGTS: alíquotas nacionais uniformes por ano (1,0% em 2027 a 2028 até a regra de 2033) | B4 (serviços financeiros) | Parâmetro com vigência por ano. |
| 214 | §§ 3º e 6º: base do arranjo de pagamento é a remuneração recebida do credenciado, do instituidor ou de outros participantes | B4 (serviços financeiros) | — |
| 217 | Revogado | Sem efeito no ERP | — |
| 218-A | Regulamento: prazos e retenção do instituidor e dos participantes do arranjo | B4 (serviços financeiros) | — |
| 219-A | Programa de fidelização: base é o valor dos pontos emitidos menos o resgatado; sem crédito ao adquirente | B4 (serviços financeiros) | — |
| 231 | Importação de serviço financeiro com alíquota zero (§ 1º, IV; § 3º) | B4 (serviços financeiros) | — |
| 233 | Soma das alíquotas dos serviços financeiros: 10,85% em 2027 e 2028 a 12,50% em 2033 | B4 (serviços financeiros) | Parâmetro com vigência por ano. |
| 238 | Plano de saúde: parágrafo único sobre o crédito do contratante (art. 57, § 3º, IV, f) | B4 (serviços financeiros) | — |
| 252 | Permuta de imóveis: torna tributada; § 5º-A (contribuinte e não contribuinte) | Já coberto | `Mov_Permuta_Imovel` (Bloco 2, revisão 15) já traz `Contraparte_Regime_Regular` e as regras do redutor. |
| 258 | Redutor de ajuste: valor de aquisição; § 10 (manutenção na compra de contribuinte) | Já coberto | `Cad_Imovel_Redutor_Ajuste` (Bloco 2). |
| 260 | Redutor social da locação residencial de R$ 600 por mês | Já coberto | Já no documento 10, seção do Bloco 2. |
| 321 | §§ 2º a 4º: pedido de harmonização da interpretação | Sem efeito no ERP | Órgão público. |
| 322 | Fórum de Harmonização Jurídica das Procuradorias | Sem efeito no ERP | Órgão público. |
| 323-A a 323-F | Consulta tributária | Desenho neste documento | Seção 4.3. |
| 323-G a 323-M | Recurso especial e incidente de uniformização | Desenho neste documento | Seção 4.4. |
| 325 | § 4º: ambiente nacional guarda respostas e documentos entregues à fiscalização | Sem efeito no ERP | Direito do contribuinte; sem dado a guardar. |
| 327-A | Suframa fiscaliza o processo produtivo básico por servidores efetivos | Sem efeito no ERP | Órgão público. |
| 341 | Regime especial de fiscalização duplica a multa de ofício | Desenho neste documento | Campo em `Mov_Auto_Infracao` (seção 4.6). |
| 341-A | Conceito de infração | Texto de regra, sem campo | — |
| 341-B | A multa punitiva se calcula depois do acréscimo do art. 29, § 2º, II | Já coberto | `Cad_Acrescimo_Legal_Cbs.Multa_Punitiva_Apos_Juros` (documento 157). |
| 341-C | UPF de R$ 200,00, atualizada pelo IPCA | Pergunta | Q159-4 (só na opção B). |
| 341-D | Penalidades cumulativas; multa de mora afastada até a notificação | Já coberto | `Cad_Acrescimo_Legal_Cbs.Multa_Mora_Afastada_Com_Multa_Punitiva`. |
| 341-E | As penalidades não excluem cobrança do tributo nem outras medidas | Texto de regra, sem campo | — |
| 341-F | Multa de ofício de 75%, 100% e 150% | Desenho neste documento | Anexo A e seção 4.6. |
| 341-G | 24 penalidades de obrigação acessória (22 incisos; IV e XVII têm duas alíneas), mais 4 de ofício no art. 341-F | Desenho neste documento | Anexo A e seção 4.6. |
| 341-H | Redução da multa por pagamento ou parcelamento (20% a 60%) | Desenho neste documento | Seções 4.2 e 4.6. |
| 344 | Alíquota de referência do IBS para o art. 189, § 2º, e arts. 485 a 487 | Sem efeito no ERP | Cálculo do Senado; a alíquota de referência já é parâmetro. |
| 350 | Receita de referência da União | Sem efeito no ERP | Cálculo das alíquotas de referência. |
| 361 a 365 | Fixação das alíquotas de referência estadual e municipal de 2029 a 2033 | Sem efeito no ERP | Cálculo do Senado. |
| 384 | Compensação dos titulares de benefícios onerosos de ICMS (2029 a 2032) | Só com cliente (D-N68) | Entidade só se houver cliente com benefício oneroso. |
| 392 | A RFB reconhece e paga a compensação em até 60 dias | Só com cliente (D-N68) | Idem. |
| 414 | III, c; VI: Imposto Seletivo, base dos fumígenos e valor de mercado | Pergunta | Q159-11. |
| 424 | I: fabricante é o contribuinte do IS | Pergunta | Q159-11. |
| 434 | § 2º-A: importação de fumígenos, base é a maior entre duas | Pergunta | Q159-11. |
| 438 | Regulamento do IS editado pelo Executivo | Sem efeito no ERP | — |
| 440 | II: indústria incentivada na ZFM habilitada na Suframa | Já coberto | `Cad_Habilitacao_Suframa` (documento 158). |
| 442 | Inscrição e projeto técnico-econômico na Suframa | Já coberto | Idem. |
| 460 | Idem para as áreas de livre comércio | Já coberto | Idem. |
| 471 | Devolução do IBS e da CBS ao turista estrangeiro | Pergunta | Q159-7. |
| 471-A | PNCT instituído; adesão voluntária por critérios do regulamento | Desenho neste documento | Seções 4.5 e 4.7. |
| 471-B | Objetivos do PNCT | Texto de regra, sem campo | — |
| 471-D | Penalidades do prestador de pagamento no split | Só com cliente (D-N68) | Q159-6; B7 (PSP). |
| 471-E | Prática reiterada e penalidades do órgão regulador | Só com cliente (D-N68) | Q159-6. |
| 471-F | Impugnação (20 dias úteis) e recurso hierárquico (10) do prestador | Só com cliente (D-N68) | Q159-6. |
| 475 | §§ 7º e 10: subsídios à avaliação quinquenal | Sem efeito no ERP | — |
| 481 | § 2º: escolha dos representantes municipais no CGIBS provisório | Sem efeito no ERP | Órgão público. |
| 482 | CGIBS provisório | Sem efeito no ERP | Órgão público. |
| 482-A | Mandatos do CGIBS provisório até 31/03/2027 | Sem efeito no ERP | Órgão público. |
| 483 | Custeio do Conselho Superior | Sem efeito no ERP | Órgão público. |
| 484 | Aporte da União de até R$ 3,8 bilhões | Sem efeito no ERP | Órgão público. |
| 485 | Incorporação com patrimônio de afetação: opção pela receita recebida | Já coberto | Documento 10, Bloco 2 (arts. 485, 486 e 488). |
| 486 | Parcelamento do solo: opção pela receita recebida | Já coberto | Idem. |
| 487 | §§ 2º e 12: 3,65% da receita bruta recebida e repartição | Já coberto | Idem; o percentual de 3,65% confere com o texto do Bloco 2. |
| 493-A | Associação pública especial da RFB e do CGIBS | Sem efeito no ERP | Órgão público. |
| 542 | Revogações a partir de 01/01/2027 (LC 7, 17 e 70) | Sem efeito no ERP | A transição do PIS e da Cofins já está na D-N175. |

| Destino | Artigos |
|---|---|
| Desenho neste documento | 21 |
| B1 (comércio exterior) | 5 |
| B4 (serviços financeiros) | 8 |
| B7 (marketplace e PSP) | 1 |
| Já coberto | 13 |
| Texto de regra, sem campo | 10 |
| Só com cliente (D-N68) | 5 |
| Sem efeito no ERP | 23 |
| Pergunta | 7 |
| **Total** | **93** |

**Blocos que recebem artigos.** O B1 recebe 71, 76, 98, 98-A e 98-B; o B4, 201, 212, 214, 218-A, 219-A, 231, 233 e 238; o B7, o 22 (§§ 13 a 15) e, quando vier, o 471-D a 471-F. Isso é leitura minha de **onde cada assunto mora na LC 214** (os arts. 182 a 238 são o título dos serviços financeiros e dos regimes ligados a ele, que o documento 94 pôs no B4); a Q159-8 pede a sua confirmação.

# 4. O desenho proposto

Regras que valem para as cinco entidades e as duas alterações: o ERP **avisa e não bloqueia**; carga provisória até o contador validar (`Situacao_Dado`); domínios abertos em `Cad_Classe_Sistema` (valor novo = linha nova, só carga); parâmetros com vigência; o lado dos órgãos públicos (CGIBS, RFB, Carf, Câmara Nacional) **fica fora** (D-N68).

## 4.1. Cad_Instituto_Beneficio_Ordem

A ordem em que os cinco institutos que mudam a tributação de uma operação se aplicam quando mais de um cabe (LC 214, art. 7º-A, incluído pela LC 227): redução a zero, suspensão com conversão em alíquota zero, isenção, diferimento e redução de alíquota distinta. Cinco linhas de carga. O Motor lê a ordem desta tabela para desempatar regras que se sobrepõem; a `Prioridade` do `Cad_Motor_Regra` continua sendo o desempate dentro do mesmo instituto.

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Instituto_Beneficio_Ordem** | *identificador* | — |
| **ID_Instituto_Beneficio_Ordem_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Instituto_Beneficio_Ordem_Versao). ID_Instituto_Beneficio_Ordem é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Instituto** | *referência (Cad_Classe_Sistema, domínio = instituto_beneficio_ibs_cbs) — identidade* | reducao_a_zero, suspensao_com_conversao, isencao, diferimento, reducao_de_aliquota_distinta. Domínio novo, cinco valores. |
| **Ordem** | *número* | 1 a 5, na ordem do art. 7º-A (incisos I a V). Menor número prevalece. |
| **Fundamento_Legal** | *texto* | LC 214, art. 7º-A, incisos I a V. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**10 campos.**

## 4.2. Cad_Parametro_Legal_Ibs_Cbs

Um catálogo único dos números de lei do IBS e da CBS que não pertencem a nenhuma obrigação acessória (os que pertencem ficam em `Cad_Obrigacao_Parametro_Definicao`, documento 155): prazos do processo (consulta, recurso especial, harmonização), limites do automóvel de pessoa com deficiência e do táxi, e os percentuais de redução da multa. Uma linha por número, com vigência; quem precisar de um número novo cria uma linha, e não uma tabela. Carga provisória de 16 linhas (seção 4.2).

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Parametro_Legal_Ibs_Cbs** | *identificador* | — |
| **ID_Parametro_Legal_Ibs_Cbs_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Parametro_Legal_Ibs_Cbs_Versao). ID_Parametro_Legal_Ibs_Cbs é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **Codigo** | *código (60) — identidade* | Estável, em minúsculas, por exemplo prazo_consulta_pagamento_sem_penalidade. É o que o Motor e as telas leem. |
| **Rotulo** | *texto* | O nome na tela. |
| **Valor_Numerico** | *número* | O valor, na unidade abaixo. |
| **Unidade** | *enumeração {dias_corridos, dias_uteis, anos, reais, percentual}* | Decide como a tela mostra o valor e como o Motor o lê. |
| **Fundamento_Legal** | *texto* | Artigo, parágrafo e inciso de onde vem o número. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**12 campos.**

**Carga proposta (16 linhas, todas provisórias, vigência inicial na da lei):**

| Código | Valor | Unidade | Fundamento |
|---|---|---|---|
| prazo_consulta_pagamento_sem_penalidade | 15 | dias corridos | Art. 323-C, parágrafo único, I |
| prazo_recurso_especial | 10 | dias úteis | Art. 323-G |
| prazo_harmonizacao_decisao | 90 | dias úteis | Art. 321, § 3º |
| prazo_minuta_consulta_outro_orgao | 30 | dias corridos | Art. 323-B, § 1º (prorrogável uma vez por igual período) |
| automovel_pcd_preco_maximo | 200.000 | reais | Art. 149, § 2º, II |
| automovel_pcd_beneficio_maximo | 100.000 | reais | Art. 149, § 2º, II |
| automovel_pcd_intervalo_minimo | 3 | anos | Art. 152, II (redação da LC 227) |
| automovel_taxi_intervalo_minimo | 2 | anos | Art. 152, I (sem mudança; entra por coerência) |
| reducao_multa_pagamento_ate_impugnacao_padrao | 50 | percentual | Art. 341-H, I |
| reducao_multa_parcelamento_ate_impugnacao_padrao | 40 | percentual | Art. 341-H, II |
| reducao_multa_pagamento_apos_impugnacao_padrao | 30 | percentual | Art. 341-H, III |
| reducao_multa_parcelamento_apos_impugnacao_padrao | 20 | percentual | Art. 341-H, IV |
| reducao_multa_pagamento_ate_impugnacao_conformidade | 60 | percentual | Art. 341-H, § 1º (PNCT ou bons antecedentes) |
| reducao_multa_parcelamento_ate_impugnacao_conformidade | 50 | percentual | Art. 341-H, § 1º |
| reducao_multa_pagamento_apos_impugnacao_conformidade | 40 | percentual | Art. 341-H, § 1º |
| reducao_multa_parcelamento_apos_impugnacao_conformidade | 30 | percentual | Art. 341-H, § 1º |

O inciso II do § 1º do art. 341-H manda aplicar o percentual maior a quem tem "bons antecedentes fiscais, **nos termos do regulamento**", e o regulamento não existe. Por isso a tela só **avisa** que a hipótese pode valer; quem decide é o contador.

## 4.3. Mov_Processo_Consulta_Tributaria

A consulta sobre a legislação do IBS e da CBS que a empresa formula (LC 214, arts. 323-A a 323-F, incluídos pela LC 227), 1:1 com o `Cad_Processo` (Tipo_Processo = administrativo, área tributária). O processo guarda número, partes, andamento e prazos; esta extensão guarda o que é próprio da consulta e que decide os efeitos do art. 323-C (nenhum procedimento fiscal sobre a espécie consultada e pagamento sem penalidade em 15 dias) e do art. 323-D (consulta que não produz efeito). A consulta não suspende o prazo de recolhimento (art. 323-D); por isso a estrutura não tem campo de suspensão.

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Consulta** | *identificador* | — |
| **ID_Processo** | *referência (Cad_Processo)* | 1:1. O processo administrativo a que a consulta pertence (relação 1:1). |
| **Tributos_Consultados** | *enumeração {cbs, ibs, ibs_e_cbs}* | O art. 323-B prevê a resposta conjunta da RFB e do CGIBS quando há matéria comum. |
| **Orgao_Competente** | *enumeração {rfb, cgibs, conjunto}* | Quem emite a solução (art. 323-B). |
| **Materia_De_Direito** | *texto* | A matéria de direito objeto da dúvida (art. 323-A, § 1º, II). Cada consulta trata de uma só matéria, salvo questões conexas (§ 2º). |
| **Descricao_Do_Fato** | *texto* | O fato determinado, completa e exatamente descrito (art. 323-A, caput). A descrição incompleta tira o efeito da consulta (art. 323-D, II). |
| **Data_Fato_Gerador** | *data, opcional* | Se o fato gerador já ocorreu (art. 323-A, § 1º, III). |
| **Declarou_Procedimento_Fiscal** | *booleano* | A declaração de existência ou não de procedimento fiscal contra o consulente (art. 323-A, § 1º, IV). Consulta feita depois de iniciado o procedimento não produz efeito (art. 323-D, VI). |
| **Data_Protocolo** | *data* | A data do protocolo. Os efeitos do art. 323-C exigem protocolo até o vencimento da obrigação a que a consulta se refere. |
| **Data_Vencimento_Obrigacao** | *data, opcional* | O vencimento da obrigação a que a consulta se refere; com a data do protocolo, o ERP avisa se os efeitos do art. 323-C estão em risco. Aviso, não bloqueio. |
| **Situacao** | *enumeração {protocolada, em_harmonizacao, respondida, ineficaz, revogada}* | em_harmonizacao: a minuta foi ao Comitê de Harmonização e a consulta fica suspensa até a resolução (art. 323-B, § 2º). ineficaz: o motivo vai no campo abaixo. A solução é definitiva e não admite recurso (art. 323-F). |
| **Data_Ciencia_Resposta** | *data, opcional* | A ciência da solução. Dela contam os 15 dias de pagamento sem penalidade (art. 323-C, parágrafo único, I; prazo em Cad_Parametro_Legal_Ibs_Cbs). |
| **Aceitacao_Tacita** | *booleano, opcional* | Verdadeiro quando a solução saiu em conjunto por aceitação tácita de um dos órgãos, passados 30 dias sem manifestação (art. 323-B, § 3º). |
| **ID_Motivo_Ineficacia** | *referência (Cad_Classe_Sistema, domínio = motivo_ineficacia_consulta), opcional* | Só quando Situacao = ineficaz: dados inexatos, fato não descrito exata e completamente, protelatória, exigência formal não suprida, inconstitucionalidade ou negativa de aplicação, formulada após o início de procedimento fiscal (art. 323-D, parágrafo único, I a VI). Domínio novo, seis valores. |
| **Data_Pagamento_Conforme_Resposta** | *data, opcional* | Quando o tributo devido segundo a resposta foi pago. O ERP compara com o prazo de 15 dias e avisa; a perda da isenção de penalidade é conclusão do contador. |
| **Observacao** | *texto, opcional* | — |

**16 campos.**

## 4.4. Mov_Processo_Uniformizacao

O recurso especial e os incidentes de uniformização da jurisprudência administrativa comum ao IBS e à CBS (LC 214, arts. 323-G a 323-M, incluídos pela LC 227), ligados ao `Cad_Processo` em que a decisão foi proferida. A Câmara Nacional de Integração do Contencioso, o CGIBS e o Carf são órgãos públicos e ficam fora (D-N68); a empresa registra só o que ela, ou a Fazenda contra ela, propõe. O efeito sobre a exigibilidade é regra de Tipo, e não campo: o recurso especial suspende a exigibilidade (art. 323-G, § 4º); o incidente de matéria repetitiva não suspende (art. 323-J, parágrafo único); o incidente contra a decisão que deixou de aplicar provimento vinculante suspende (art. 323-L, parágrafo único).

*Vigência: não.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Uniformizacao** | *identificador* | — |
| **ID_Processo** | *referência (Cad_Processo)* | O processo cuja decisão se ataca ou cujo julgamento gera o incidente. |
| **Tipo** | *enumeração {recurso_especial, incidente_materia_repetitiva, incidente_provimento_vinculante}* | Decide o efeito sobre a exigibilidade do crédito (descrição da entidade). O ERP avisa que a exigibilidade está suspensa; a suspensão é regra do Tipo e não se grava em Mov_Processo_Suspensao (Q159-E1). |
| **Quem_Propos** | *enumeração {fazenda_publica, sujeito_passivo, presidente_de_orgao}* | Arts. 323-G, § 3º, 323-J e 323-L. O sujeito passivo só propõe o recurso especial e o incidente contra a decisão que deixou de aplicar provimento vinculante. |
| **Data_Interposicao** | *data* | — |
| **Data_Ciencia_Decisao_Recorrida** | *data, opcional* | Do recurso especial: o prazo é de 10 dias úteis (art. 323-G; Cad_Parametro_Legal_Ibs_Cbs). O ERP avisa o prazo; não bloqueia. |
| **Numero_Decisao_Paradigma** | *texto, opcional* | A decisão paradigma, cuja ementa a petição deve transcrever (art. 323-G, § 2º). |
| **Situacao** | *enumeração {interposto, admitido, julgado, nao_conhecido}* | — |
| **Data_Julgamento** | *data, opcional* | — |
| **Numero_Sumula** | *texto, opcional* | A súmula de caráter vinculante publicada no DOU, quando o incidente de matéria repetitiva fixa tese (art. 323-H, § 1º). |
| **Observacao** | *texto, opcional* | — |

**11 campos.**

## 4.5. Cad_Programa_Conformidade_Beneficio

O que cada programa de conformidade pode dar a quem participa dele, uma linha por programa e tipo de benefício. Serve ao PNCT (LC 214, arts. 471-A a 471-C, incluídos pela LC 227), cujo art. 471-C diz que o programa "poderá prever" sete tipos de benefício e deixa o resto para ato conjunto do CGIBS e da RFB que ainda não existe; serve também ao Confia, ao Sintonia e ao OEA quando o contador mapear os benefícios deles. A carga fica vazia até o ato sair; as linhas nascem provisórias e o contador valida. A participação da empresa é de `Cad_Empresa_Programa_Conformidade` (programa = pnct).

*Vigência: sim.*

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Programa_Conformidade_Beneficio** | *identificador* | — |
| **ID_Programa_Conformidade_Beneficio_Versao** | *identificador da versão* | Chave primária da versão (tabela física Cad_Programa_Conformidade_Beneficio_Versao). ID_Programa_Conformidade_Beneficio é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência — Fase 0, seção 2. |
| **ID_Programa** | *referência (Cad_Classe_Sistema, domínio = programa_conformidade) — identidade* | confia, sintonia, oea e, com este documento, pnct. |
| **ID_Tipo_Beneficio** | *referência (Cad_Classe_Sistema, domínio = tipo_beneficio_programa_conformidade) — identidade* | Domínio novo, sete valores do art. 471-C: prazo ampliado de obrigação acessória; prioridade em pedido de ressarcimento; redução de penalidade; análise prioritária de consulta; menos exigência documental; flexibilização da verificação do valor de mercado entre partes relacionadas (art. 5º, § 7º); outro, por regulamento. |
| **Descricao** | *texto* | O benefício como o ato o descreve. |
| **Percentual_Beneficio** | *número, opcional* | Quando o benefício é um percentual (por exemplo, as reduções maiores da multa do art. 341-H, § 1º, que ficam em Cad_Parametro_Legal_Ibs_Cbs). |
| **Ato_Regulamentador** | *texto, opcional* | O ato conjunto que regulamentou o benefício. Vazio enquanto o ato não existe. |
| **Fundamento_Legal** | *texto* | LC 214, art. 471-C, inciso e parágrafo. |
| **Situacao_Dado** | *enumeração {provisorio, validado}* | A carga sai provisória até o contador validar. |
| **ID_Instancia_Aprovacao** | *referência (Mov_Aprovacao_Instancia), opcional* | A validação do contador (área validacao_dado_legal). |
| **Vigencia_Inicio** | *data* | Primeiro dia em que esta versão vale. |
| **Vigencia_Fim** | *data* | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente) — convenção da Fase 0, seção 2. |
| **Motivo_Vigencia** | *texto, opcional* | Por que esta versão foi criada. |

**13 campos.**

## 4.6 Alterações em existentes

### Cad_Cclasstrib (+2 campos)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Instituto_Beneficio** | *referência (Cad_Classe_Sistema, domínio = instituto_beneficio_ibs_cbs), opcional* | O instituto que a classificação aplica (redução a zero, suspensão com conversão, isenção, diferimento ou redução distinta). Vazio na classificação de tributação regular. Dá ao Motor a ordem do art. 7º-A por Cad_Instituto_Beneficio_Ordem. |
| **Admite_Cumulacao_Reducao** | *booleano, opcional* | Verdadeiro só quando a lei prevê expressamente a cumulação desta redução com outra (art. 7º-A, parágrafo único, I). Sem previsão, prevalece a maior redução (II). Vazio no que não é redução. |

### Mov_Auto_Infracao (+8 campos)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|---|---|---|
| **ID_Tipo_Penalidade** | *referência (Cad_Classe_Sistema, domínio = tipo_penalidade_ibs_cbs), opcional* | A penalidade aplicada, entre as 28 dos arts. 341-F e 341-G (anexo A). Registro do que o auto diz; o ERP não calcula a multa (D-N284). |
| **Percentual_Multa_Aplicado** | *número, opcional* | Quando o auto aplica percentual (75, 100 ou 150 no art. 341-F; 33, 66 ou 100 no art. 341-G). |
| **Valor_Penalidade** | *número, opcional* | O valor da penalidade como consta do auto, em reais. |
| **Reincidencia_Especifica** | *booleano, opcional* | O auto aplicou a majoração de 50% do art. 341-G, § 1º. |
| **Em_Regime_Especial_Fiscalizacao** | *booleano, opcional* | A infração foi cometida durante o regime especial de fiscalização; a multa de ofício do IBS e da CBS fica duplicada (art. 341, § 1º). |
| **ID_Hipotese_Reducao** | *referência (Cad_Classe_Sistema, domínio = hipotese_reducao_multa), opcional* | A hipótese do art. 341-H em que a multa foi paga com redução: pagamento ou parcelamento, antes ou depois do prazo de impugnação. Domínio novo, quatro valores. |
| **Percentual_Reducao_Aplicado** | *número, opcional* | O percentual da redução, como o pagamento a aplicou. O ERP compara com o valor de Cad_Parametro_Legal_Ibs_Cbs (50, 40, 30 e 20; ou 60, 50, 40 e 30 com PNCT ou bons antecedentes) e avisa se diferir. |
| **Valor_Penalidade_Paga** | *número, opcional* | O valor efetivamente pago da penalidade, depois da redução. |

**Domínios novos em `Cad_Classe_Sistema`:** `instituto_beneficio_ibs_cbs` (5 valores), `motivo_ineficacia_consulta` (6), `tipo_beneficio_programa_conformidade` (7), `tipo_penalidade_ibs_cbs` (28, anexo A) e `hipotese_reducao_multa` (4). **Valor novo** em `programa_conformidade`: `pnct`, "Programa Nacional de Conformidade Tributária" (LC 214, art. 471-A). Em `Mov_Auto_Infracao`, o campo `Tipo_Registro` continua com os dois valores.

**Regra do Motor (aviso, não programado):** ao pagar uma penalidade com redução, o ERP compara `Percentual_Reducao_Aplicado` com o parâmetro da hipótese e, se a empresa tem participação ativa em `Cad_Empresa_Programa_Conformidade` com programa `pnct` na data, mostra também o percentual de conformidade. O aviso entra no anexo dos avisos do documento 10, como os 18 dos documentos 175 e 176.

## 4.7 O PNCT e a Q116-6

A Q116-6 deixou `Participa_Pnct` esperando o B0b (LC 225). O PNCT, porém, é da **LC 214** (art. 471-A, incluído pela LC 227), e não da LC 225. Proponho que **não exista** o campo `Participa_Pnct`: a participação é uma linha de `Cad_Empresa_Programa_Conformidade` com programa `pnct`, que já tem situação (admitida, em processo de exclusão, excluída), ato de admissão, ato de exclusão, vigência e validação, e dá a mesma resposta pela data. Conferi que **nenhum campo `Participa_Pnct` existe** na revisão 35, então a Q116-6 não deixou nada a desfazer. O art. 471-C, parágrafo único, diz que os benefícios dos incisos II, III e V valem, para o IBS e a CBS, **exclusivamente no âmbito do PNCT**; por isso a tabela de benefícios guarda o programa de cada um.

# 5. Anexo A: as 28 penalidades dos arts. 341-F e 341-G (carga do domínio `tipo_penalidade_ibs_cbs`)

Todas provisórias. "Tributo de referência" é o valor do art. 341-G, § 5º: a alíquota de referência vezes o valor da operação, ainda que imune, isenta, de alíquota zero, reduzida, diferida ou suspensa; em 2026, 6% da operação para a CBS e 12% para o IBS; de 2027 a 2032, para o IBS, o dobro da alíquota de referência da CBS.

| Código | Dispositivo | Penalidade |
|---|---|---|
| oficio_75_tributo_nao_pago | 341-F, I | 75% do tributo não declarado ou declarado a menor e não pago |
| oficio_75_credito_indevido | 341-F, II | 75% do crédito indevido |
| oficio_100_sonegacao_fraude | 341-F, § 1º, I | 100% (sonegação, fraude, simulação ou conluio) |
| oficio_150_reincidente | 341-F, § 1º, II | 150% (reincidência) |
| inscricao_cadastro_nao_feita | 341-G, I | 10 UPF |
| domicilio_principal_nao_atualizado | 341-G, II | 10 UPF por infração |
| estabelecimento_nao_comunicado | 341-G, III | 10 UPF por infração |
| arquivo_atraso_sem_intimacao | 341-G, IV, a | 20 UPF por período de apuração |
| arquivo_atraso_com_intimacao | 341-G, IV, b | 30 UPF por período e por intimação |
| software_fiscal_irregular_uso | 341-G, V | 100 UPF por equipamento |
| software_fiscal_irregular_fornecimento | 341-G, VI | 150 UPF por equipamento |
| medicao_volume_irregular | 341-G, VII | 100 UPF por equipamento |
| inutilizacao_nao_comunicada | 341-G, VIII | 1 UPF por número |
| confirmacao_operacao_omitida | 341-G, IX | 1 UPF por documento |
| embaraco_fiscalizacao | 341-G, X | 50 UPF por evento |
| bem_sem_documento_fiscal | 341-G, XI | 100% do tributo de referência |
| documento_usado_mais_de_uma_vez | 341-G, XII | 100% do tributo de referência |
| documento_nao_idoneo | 341-G, XIII | 66% do tributo de referência |
| documento_falsificado_ou_extraviado | 341-G, XIV | 100% do tributo de referência |
| credito_indevido_nao_estornado | 341-G, XV | 66% do crédito |
| documento_entrada_nao_emitido | 341-G, XVI | 100% do tributo de referência |
| cancelamento_apos_fato_gerador | 341-G, XVII, a | 66% do tributo de referência |
| cancelamento_apos_prazo | 341-G, XVII, b | 33% do tributo de referência |
| dpec_valor_divergente | 341-G, XVIII | 33% do valor da diferença |
| informacao_comercio_exterior_omitida | 341-G, XIX | 100 UPF por informação; teto de 1% do valor da operação, piso de 50 UPF (§ 7º, III) |
| dispositivo_seguranca_violado | 341-G, XX | 10 UPF por dispositivo |
| controle_zfm_alc_descumprido | 341-G, XXI | 66% do tributo de referência |
| instalacao_credenciada_zfm_sem_requisito | 341-G, XXII | 20 UPF por requisito exigido |

Majoração de 50% na **reincidência específica** em qualquer inciso do art. 341-G (mesmo inciso, dentro de 3 anos do lançamento anterior; § 1º e § 2º). Não se aplica o inciso IV a mera falha ou erro material (§ 4º).

# 6. Perguntas para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q159-1** | Aceita a **lista refeita** dos 131 artigos (seção 3) e a conciliação com o CSV do documento 138 (Anexo B), com os cinco artigos sem marca (14, 41, 195, 243 e 271) e a **correção do "art. 95" para art. 22** (seção 2.2)? | Sim. O CSV do documento 138 foi comparado (Anexo B). |
| **Q159-2** | **Ordem de aplicação (art. 7º-A):** criar `Cad_Instituto_Beneficio_Ordem` (5 linhas, 10 campos) e os dois campos em `Cad_Cclasstrib`, e aplicar a ordem pelo Motor? | Sim. A ordem e a cumulação são regra de lei com vigência; sem a tabela, ficariam escondidas no código. |
| **Q159-3** | **Consulta e contencioso:** criar `Mov_Processo_Consulta_Tributaria` (16 campos), `Mov_Processo_Uniformizacao` (11) e o catálogo único `Cad_Parametro_Legal_Ibs_Cbs` (12 campos, 16 linhas de carga), ligados ao `Cad_Processo` do Jurídico? | Sim. A empresa precisa acompanhar os 15 dias sem penalidade e a suspensão da exigibilidade; o `Cad_Processo` já aceita processo administrativo. |
| **Q159-4** | **Multas:** (A) manter a D-N284 e só **registrar** a penalidade em `Mov_Auto_Infracao` (+8 campos, 28 penalidades como domínio), ou (B) criar o catálogo de penalidades com UPF (`Cad_Infracao_Regra` com 28 linhas e `Cad_Upf_Valor` com vigência) e a **simulação** da multa? | **A.** B reverte parte da D-N284 e só se justifica se um cliente quiser provisionar multa. A opção B custa +3 entidades (cerca de 40 campos) e não muda o que já está desenhado. |
| **Q159-5** | **PNCT:** criar o valor `pnct` em `programa_conformidade` e a tabela `Cad_Programa_Conformidade_Beneficio` (13 campos, carga vazia até o ato conjunto), e **não** criar `Participa_Pnct` (Q116-6)? | Sim. |
| **Q159-6** | **Penalidades do prestador de pagamento (arts. 471-D, 471-E e 471-F):** ficam para o B7 (PSP), junto com a volta do split (D-N282)? | Sim. Só valem para cliente que seja prestador de pagamento (D-N68). |
| **Q159-7** | **Devolução ao turista estrangeiro (art. 471):** registrar como "só com cliente" (varejo com venda a turista), sem entidade agora? O texto depende de ato conjunto do Ministério da Fazenda e do CGIBS que não existe. | Sim. |
| **Q159-8** | Confirma o **destino dos artigos** que entram em bloco (seção 3): 71, 76, 98, 98-A e 98-B no B1; 201, 212, 214, 218-A, 219-A, 231, 233 e 238 no B4; o art. 22 e o 471-D a 471-F no B7? E confirma também que os **19 artigos do Anexo B sem desenho** (11, 16, 31, 32, 80, 89, 106, 126, 142, 172, 182, 183, 192, 197, 330, 408, 422, 517 e 544) seguem cada um para o destino da última coluna do anexo? | Sim. É a ordem do documento 115 (B1, B5, B3, B4, B6, B7). |
| **Q159-9** | **Energia elétrica (art. 28):** entra como texto de regra do Motor (quem recolhe em cada hipótese), sem campo, até haver cliente do setor elétrico? A liquidação da CCEE e o tipo `agente_ccee` já estão desenhados (documento 156). | Sim. As cinco hipóteses são escolha de quem recolhe, e o ERP do contribuinte só precisa saber de que lado está. |
| **Q159-10** | **Documento fiscal consolidado (art. 22, § 13, I; art. 60, § 7º):** esperar o ato conjunto e a nota técnica do leiaute, sem campo agora? | Sim. Sem leiaute, qualquer campo seria palpite. |
| **Q159-11** | **Imposto Seletivo (arts. 414, 424 e 434):** as três mudanças (base dos fumígenos, fabricante como contribuinte no primeiro fornecimento, importação de fumígenos com a maior entre duas bases) entram como texto de regra no desenho do Imposto Seletivo, e eu confiro o dicionário dele no próximo documento? Hoje não há "fumígeno" no dicionário. | Sim. Só confiro; se faltar campo, entra no documento 160 com pergunta própria. |

**Perguntas ao contador.** Ficam só no documento 188 (D-N501), na Parte 7, com campo de resposta.

| Nº | Pergunta | No documento 188 |
|---|---|---|
| **Q159-C1** | Os 16 números da carga de `Cad_Parametro_Legal_Ibs_Cbs` conferem com a LC 214 consolidada? | C229 |
| **Q159-C2** | O que são "bons antecedentes fiscais" (art. 341-H, § 1º, II) enquanto o regulamento não existe? A tela deve avisar a hipótese ou só o PNCT? | C226 |
| **Q159-C3** | A multa de mora do art. 29 e a punitiva do art. 341-F incidem juntas depois da notificação do lançamento de ofício? (O art. 341-D, parágrafo único, só afasta a de mora **até** a notificação.) | C227 |
| **Q159-C4** | Consulta protocolada depois do vencimento da obrigação perde os efeitos do art. 323-C por inteiro, ou só o do inciso I? | C228 |

**Pergunta à equipe.**

| Nº | Pergunta |
|---|---|
| **Q159-E1** | O `Mov_Processo_Suspensao` usa o indicativo de suspensão do **eSocial** (`codigo_suspensao_esocial`) e por isso não serve ao IBS e à CBS. Prefere ampliar essa entidade com um segundo indicativo ou manter a suspensão do IBS e da CBS dentro das duas entidades novas, como proponho? |

# 7. Como conferi e limites

- **Texto da lei.** Separei o trecho da LC 227 que altera a LC 214 (arts. 3º a 544, a partir do art. 174 da lei) e o comparei com o consolidado do Planalto, que marca cada dispositivo alterado. Os 131 artigos vêm da **união** das duas fontes.
- **Dicionário.** Procurei cada assunto no dicionário da revisão 35 e nos documentos do Projeto (palavras-chave e nomes de entidade). "Já coberto" é por assunto; **não conferi campo a campo**.
- **O que não li.** O texto anterior da LC 214 (só existe o novo); regulamentos do PNCT e dos "bons antecedentes" (não existem); o art. 29, § 2º, na versão consolidada completa (usei a descrição do documento 157).
- **O CSV do documento 138.** Usei as colunas Artigo, Impacto, Onde o projeto trata e Observação. A coluna "Onde" é a leitura do documento 138; o que cada documento 156, 157, 150 e 158 desenha conferi pelo número do artigo da LC.
- **Contagens.** Entidades, campos, FK e domínios da seção 1 são a revisão 35 mais os acréscimos deste documento, somados por mim; a conferência pelo gerador do dicionário (auditoria, DDL) só acontece no "consolidar".
- **Nada foi validado pelo contador.** Todas as cargas são provisórias.

# 8. Resultado

Nada aplicado (1.138 entidades e 12.769 campos). Se você aprovar tudo: +5 entidades, +72 campos, 1.143 entidades e 12.841 campos na revisão 36, mais o texto novo dos documentos 14 e 38.
# 9. Anexo B: conciliação dos 131 artigos do CSV do documento 138

O arquivo `conferencia_lc227_por_artigo.csv` (pasta ERP-Revisao25) tem 131 artigos. Comparei cada um com a triagem da seção 3. **124 artigos coincidem** com a minha lista. O CSV tem sete que a minha lista não tem (7, 14, 41, 95, 195, 243 e 271), todos sem marca da LC 227 nas minhas fontes, e a minha lista tem sete que o CSV não tem (3, 6, 7-A, 201, 341, 438 e 471). Desses sete, pesam o 7-A (ordem de aplicação, seção 4.1) e o 341 (multa de ofício duplicada no regime especial, seção 4.6).

Dos 41 que o documento 138 deu como ALTO ou MÉDIO, três não têm marca (95, 195 e 243). Dos outros 38, **18 têm desenho ou decisão** (10 desenhados nos documentos 156, 157, 150 e 158; 7 com decisão da Q138; o art. 471-C, tratado neste documento), **1 é parcial** (64) e **19 só têm o destino apontado pelo documento 138, sem desenho** (11, 16, 31, 32, 80, 89, 106, 126, 142, 172, 182, 183, 192, 197, 330, 408, 422, 517 e 544). A versão deste documento de 10/11/2026 dava os 38 como encaminhados; isso estava errado. A busca foi pelo número do artigo da LC (não do Decreto) nos documentos 156, 157, 150 e 158 e nas respostas da Q138; não conferi campo a campo nem se as decisões da Q138 já foram aplicadas.

| Artigo | Impacto no documento 138 | Situação | Onde está agora |
|---|---|---|---|
| 4º | Sem desenho | Triagem (seção 3) | Texto de regra, sem campo. A qualificação por vigência já guarda a condição (`Cad_Participante_Qualificacao_Cbs`); regra do Motor. |
| 5º | Alto | Desenhado | Documento 156 (arts. 5º, 57 e 12; Q138-4). |
| 7º | Sem desenho | Sem marca | O CSV do documento 138 diz que o texto lido não mostra mudança. A mudança do art. 7º-A está na triagem (seção 4.1). |
| 10 | Médio | Desenhado | Documento 157 (B0a-1, fato gerador e antecipação). |
| 11 | Médio | Sem desenho | Faltam nos critérios do local da operação o adquirente não residente, a compra centralizada (matriz) e a energia. |
| 12 | Sem desenho | Triagem (seção 3) | Já coberto. `Mov_Energia_Ccee_Liquidacao` (documento 156, Q156-9). |
| 14 | Baixo | Sem marca | Relido: sem marca da LC 227 (seção 2). |
| 16 | Médio | Sem desenho | Sem campo novo: confirma a redução por ente (D-N199). A ressalva da alíquota uniforme vai ao contador. |
| 22 | Sem desenho | Triagem (seção 3) | B7 (marketplace e PSP). É o texto que o documento 138 chamou de "art. 95" (seção 2.2). |
| 26 | Alto | Decisão registrada | Q138-5: ajuste no B2 (documento 116). Não conferi se já foi aplicado. |
| 28 | Baixo | Triagem (seção 3) | Pergunta. Q159-9. |
| 29 | Médio | Desenhado | Documento 157 (`Cad_Acrescimo_Legal_Cbs`). |
| 31 | Médio | Sem desenho | Adiado com o split (D-N282); ao reabrir, partir do texto da LC 227. |
| 32 | Médio | Sem desenho | Adiado com o split (D-N282); ao reabrir, partir do texto da LC 227. |
| 33 | Alto | Decisão registrada | Q138-3: corrigir só o texto do documento 10, seção 10, sem campo. |
| 34 | Baixo | Triagem (seção 3) | Texto de regra, sem campo. Depende da volta do split (D-N282). |
| 41 | Baixo | Sem marca | Relido: sem marca da LC 227 (seção 2). |
| 47 | Médio | Desenhado | Documento 157 (ajuste da operação). |
| 57 | Alto | Desenhado | Documento 156 (arts. 5º, 57 e 12; Q138-4). |
| 58 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Direito do contribuinte; sem dado a guardar. |
| 59 | Baixo | Triagem (seção 3) | Texto de regra, sem campo. O ERP já recebe mensagens do DTE (`Mov_Caixa_Postal_Fiscal`); a regra é de aviso. |
| 60 | Baixo | Triagem (seção 3) | Pergunta. Q159-10. |
| 64 | Médio | Parcial | O documento 157 trata só a importação de serviço (art. 64, § 5º, I, a); o resto fica para o B1. |
| 71 | Sem desenho | Triagem (seção 3) | B1 (comércio exterior). |
| 73 | Sem desenho | Triagem (seção 3) | Texto de regra, sem campo. Aviso do Motor; sem campo. |
| 76 | Sem desenho | Triagem (seção 3) | B1 (comércio exterior). Prazo parametrizado no B1. |
| 80 | Médio | Sem desenho | Entra no B1: consumo no exterior definido pelo local da operação. |
| 81-A | Alto | Decisão registrada | Q138-6: desenhar junto do B1. |
| 89 | Médio | Sem desenho | Entra no B1: § 4º, dispensa do pagamento na importação temporária de aeronave. |
| 95 | Alto | Sem marca | O texto que o documento 138 atribuiu ao art. 95 é do art. 22 (seção 2.2). |
| 98 | Baixo | Triagem (seção 3) | B1 (comércio exterior). |
| 98-A | Baixo | Triagem (seção 3) | B1 (comércio exterior). |
| 98-B | Baixo | Triagem (seção 3) | B1 (comércio exterior). |
| 106 | Médio | Sem desenho | Rehidro no REIDI da CBS; a Lei 14.948 não foi lida no projeto (conferir o documento 191, que trata do REIDI). |
| 116 | Baixo | Triagem (seção 3) | Sem efeito no ERP. |
| 117 | Baixo | Triagem (seção 3) | Texto de regra, sem campo. Regra do cálculo do cashback; sem campo. |
| 126 | Médio | Sem desenho | Entra no B1: o regime diferenciado não vale na remessa internacional no RTS (critério do Motor). |
| 142 | Médio | Sem desenho | O tipo de participante e os 20% já estão no B2; resta a carga do Anexo XI (Q137-1 e Q137-2). |
| 146 | Alto | Decisão registrada | Q138-8 a Q138-10: desenho mínimo dos medicamentos. |
| 149 | Sem desenho | Triagem (seção 3) | Desenho neste documento. `Cad_Parametro_Legal_Ibs_Cbs` (seção 4.2); o dicionário não tinha esses números. |
| 152 | Sem desenho | Triagem (seção 3) | Desenho neste documento. `Cad_Parametro_Legal_Ibs_Cbs`. |
| 156 | Baixo | Triagem (seção 3) | Texto de regra, sem campo. Linha de classificação (carga); o registro do ICT já cabe em `Numero_Comprovante` da qualificação. |
| 168 | Alto | Decisão registrada | Q138-6: o crédito presumido vem antes, porque a entidade já está aplicada. |
| 172 | Médio | Sem desenho | A data de início dos incisos IX a XI deve ser parâmetro com vigência; a carga dos combustíveis foi conferida no documento 194. |
| 182 | Médio | Sem desenho | Entra no B4: domínio de espécie de serviço financeiro (liquidação antecipada e proteção patrimonial mutualista). |
| 183 | Médio | Sem desenho | Entra no B4: categorias do prestador (administradora de fidelização não supervisionada). |
| 192 | Médio | Sem desenho | Entra no B4: a perda dedutível na CBS segue a regra do IR; ligar a conta de perda a essa regra. |
| 195 (aviso) | Médio | Sem marca | Relido: sem marca da LC 227 (seção 2). |
| 197 | Médio | Sem desenho | Liga-se ao título em moeda estrangeira (documentos 101, 119 e 121) e ao B4: sem crédito em empréstimo e de associado de cooperativa. |
| 212 | Baixo | Triagem (seção 3) | B4 (serviços financeiros). Parâmetro com vigência por ano. |
| 214 | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). |
| 217 | Sem desenho | Triagem (seção 3) | Sem efeito no ERP. |
| 218-A | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). |
| 219-A | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). |
| 231 (importação de serviços financeiros) | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). |
| 233 (alíquotas dos serviços financeiros, 2027 a 2033) | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). Parâmetro com vigência por ano. |
| 238 (planos de saúde, crédito do contratante) | Sem desenho | Triagem (seção 3) | B4 (serviços financeiros). |
| 243 (arquivo; conteúdo é o art. 5º, §§ 9º e 10) | Médio | Sem marca | Relido: sem marca; o conteúdo é o do art. 5º, §§ 9º e 10 (seção 2). |
| 252 (imóveis, incidência e permuta) | Baixo | Triagem (seção 3) | Já coberto. `Mov_Permuta_Imovel` (Bloco 2, revisão 15) já traz `Contraparte_Regime_Regular` e as regras do redutor. |
| 253 (locação até 90 dias, como hotelaria) | Médio | Desenhado | Documento 150 (locação por temporada). |
| 258 (valor inicial do redutor de ajuste) | Baixo | Triagem (seção 3) | Já coberto. `Cad_Imovel_Redutor_Ajuste` (Bloco 2). |
| 260 (redutor social na locação residencial) | Baixo | Triagem (seção 3) | Já coberto. Já no documento 10, seção do Bloco 2. |
| 271 (arquivo; conteúdo é o art. 7º-A, incisos II a V e parágrafo único) | Sem desenho | Sem marca | Relido: sem marca; o conteúdo é o do art. 7º-A, incisos II a V (seção 2). |
| 280 (hotelaria, parques de diversão e temáticos) | Alto | Decisão registrada | Q138-2: corrigir o texto do documento 10, seção 7; o café da manhã e o frigobar ficam para o contador. |
| 293 (SAF, TEF) | Alto | Decisão registrada | Q138-1: o parâmetro parte da LC 227 (CBS 1% e IBS 1%). |
| 321 (Comitê de Harmonização) | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 322 (Fórum de Harmonização Jurídica) | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 323-A (consulta: direito e conteúdo) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-B (rito da solução de consulta RFB e CGIBS) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-C (efeitos da consulta) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-D (consulta não suspende prazos; casos sem efeito) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-E (lançamento e revogação) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-F (sem recurso; solução definitiva) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.3. |
| 323-G (recurso especial; Câmara Nacional) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-H (incidente de uniformização) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-I (requisitos do incidente repetitivo) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-J (quem suscita o incidente repetitivo) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-K (incidente por provimento vinculante não aplicado) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-L (quem suscita o incidente do inciso II) | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 323-M (ato conjunto) | Baixo | Triagem (seção 3) | Desenho neste documento. Seção 4.4. |
| 325 (compartilhamento de fiscalização) | Baixo | Triagem (seção 3) | Sem efeito no ERP. Direito do contribuinte; sem dado a guardar. |
| 327-A | Sem desenho | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 330 | Médio | Sem desenho | Liga-se a `Mov_Auto_Infracao` (seção 4.6): o ente autuante no IBS não tem campo. |
| 341-A | Baixo | Triagem (seção 3) | Texto de regra, sem campo. |
| 341-B | Sem desenho | Triagem (seção 3) | Já coberto. `Cad_Acrescimo_Legal_Cbs.Multa_Punitiva_Apos_Juros` (documento 157). |
| 341-C | Sem desenho | Triagem (seção 3) | Pergunta. Q159-4 (só na opção B). |
| 341-D | Sem desenho | Triagem (seção 3) | Já coberto. `Cad_Acrescimo_Legal_Cbs.Multa_Mora_Afastada_Com_Multa_Punitiva`. |
| 341-E | Baixo | Triagem (seção 3) | Texto de regra, sem campo. |
| 341-F | Sem desenho | Triagem (seção 3) | Desenho neste documento. Anexo A e seção 4.6. |
| 341-G | Sem desenho | Triagem (seção 3) | Desenho neste documento. Anexo A e seção 4.6. |
| 341-H | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seções 4.2 e 4.6. |
| 344 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado; a alíquota de referência já é parâmetro. |
| 348 | Médio | Desenhado | Documento 157 (§ 7.4, aplicação em 2026 e suprimento da omissão em 60 dias no auto). |
| 350 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo das alíquotas de referência. |
| 361 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado. |
| 362 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado. |
| 363 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado. |
| 364 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado. |
| 365 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Cálculo do Senado. |
| 384 | Sem desenho | Triagem (seção 3) | Só com cliente (D-N68). Entidade só se houver cliente com benefício oneroso. |
| 392 | Sem desenho | Triagem (seção 3) | Só com cliente (D-N68). Idem. |
| 408 | Médio | Sem desenho | A D-N175 já bate com o texto; conferir a citação do § 1º. |
| 414 | Sem desenho | Triagem (seção 3) | Pergunta. Q159-11. |
| 422 | Médio | Sem desenho | Escalonamento de 2029 a 2033 como linhas com vigência; teto de 0,25% como validação, sem campo hoje. |
| 424 | Sem desenho | Triagem (seção 3) | Pergunta. Q159-11. |
| 434 | Sem desenho | Triagem (seção 3) | Pergunta. Q159-11. |
| 440 | Sem desenho | Triagem (seção 3) | Já coberto. `Cad_Habilitacao_Suframa` (documento 158). |
| 442 | Sem desenho | Triagem (seção 3) | Já coberto. Idem. |
| 450 | Alto | Desenhado | Documento 158 (B3, crédito presumido da ZFM; Q138-6). |
| 460 | Sem desenho | Triagem (seção 3) | Já coberto. Idem. |
| 471-A | Sem desenho | Triagem (seção 3) | Desenho neste documento. Seções 4.5 e 4.7. |
| 471-B | Sem desenho | Triagem (seção 3) | Texto de regra, sem campo. |
| 471-C | Médio | Neste documento | Seção 4.5 (`Cad_Programa_Conformidade_Beneficio`). |
| 471-D | Sem desenho | Triagem (seção 3) | Só com cliente (D-N68). Q159-6; B7 (PSP). |
| 471-E | Sem desenho | Triagem (seção 3) | Só com cliente (D-N68). Q159-6. |
| 471-F | Sem desenho | Triagem (seção 3) | Só com cliente (D-N68). Q159-6. |
| 472 | Médio | Desenhado | Documento 158 (B3, compras governamentais). |
| 473 | Médio | Desenhado | Documento 158 (B3, compras governamentais). |
| 475 | Baixo | Triagem (seção 3) | Sem efeito no ERP. |
| 481 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 482 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 482-A | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 483 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 484 | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 485 | Baixo | Triagem (seção 3) | Já coberto. Documento 10, Bloco 2 (arts. 485, 486 e 488). |
| 486 | Baixo | Triagem (seção 3) | Já coberto. Idem. |
| 487 | Baixo | Triagem (seção 3) | Já coberto. Idem; o percentual de 3,65% confere com o texto do Bloco 2. |
| 493-A | Baixo | Triagem (seção 3) | Sem efeito no ERP. Órgão público. |
| 517 | Médio | Sem desenho | Simples: alíquota do crédito informada pelo optante e IBS e CBS na importação (LC 123). |
| 542 | Baixo | Triagem (seção 3) | Sem efeito no ERP. A transição do PIS e da Cofins já está na D-N175. |
| 544 | Médio | Sem desenho | Calendário: o crédito presumido de IBS da ZFM só vale desde 01/01/2029 (art. 450, § 1º). |

