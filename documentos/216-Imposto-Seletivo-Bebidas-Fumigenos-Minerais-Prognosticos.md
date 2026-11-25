# Imposto Seletivo de bebidas, fumígenos, minerais e prognósticos: o que a MP 1.399/2026 e a LC 214 pedem do modelo — Documento 216

> **O que este documento faz.** Você escolheu desenhar o **Imposto Seletivo (IS)** dos grupos que o dicionário ainda não calcula: **bebidas alcoólicas, bebidas açucaradas, fumígenos, bens minerais (com o gás natural) e concursos de prognósticos**. Os veículos, as aeronaves e as embarcações já estão no documento 204. Li o texto da **Medida Provisória 1.399/2026** (arts. 1º a 19 e Anexos IV a VI), os **arts. 409 a 438 e 244 a 250 da LC 214**, com a LC 227, e cruzei o Anexo IV com a **Tipi** que você enviou. Agora você acrescentou que **"qualquer NCM no futuro pode ter IS"**. Por isso o desenho **não trava o IS em grupos**: quem manda é a linha de `Cad_NCM_Imposto_Seletivo`, de qualquer NCM, e o Motor não tem lista fixa de grupos. Resultado: **7 entidades novas, 7 campos novos em `Cad_NCM_Imposto_Seletivo`, 5 domínios abertos novos, 17 regras e 18 avisos** do Motor, e **11 perguntas ao contador** (C324 a C334).
>
> **Nada foi aplicado ao dicionário.** Ele está na revisão 42 (1.206 entidades e 13.895 campos). O documento 215 também espera o "consolidar". A carga das alíquotas (Anexo B) é **provisória** e só entra quando você aprovar.

> **Atualização de 12/11/2026 (D-N575).** Você respondeu "Q216-1 a Q216-6 - Seguir com as recomendações": o documento está **aprovado inteiro** (7 entidades, 7 campos novos, 5 domínios abertos, carga provisória do Anexo B, 17 regras, 18 avisos, o texto literal da MP onde diverge da Tipi e o valor informado quando o valor de referência não sair da regra). **Nada foi aplicado ao dicionário:** entra no próximo "consolidar" (não pedido). Não há pergunta aberta com você neste documento; ficam as perguntas ao contador C324 a C334.

*Fontes: Medida Provisória 1.399, de 4 de novembro de 2026 (Planalto), arts. 1º a 19 e Anexos I a VI, com efeitos a partir de 2 de fevereiro de 2027; LC 214/2025 compilada com a LC 227/2026 (Planalto, texto de 10/11/2026), Livro II (arts. 409 a 438), arts. 244 a 250 e Anexo XVII; Tipi enviada por você (70 linhas de NCM e Ex nas posições envolvidas). Dicionário: revisão 42; documentos 196 e 204 (veículos); documento 215 aguardando consolidação.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que a lei fixa.** O IS é monofásico e sem crédito (art. 410). Os grupos do art. 409, § 1º, são sete: veículos, embarcações e aeronaves, fumígenos, bebidas alcoólicas, bebidas açucaradas, bens minerais e concursos de prognósticos e *fantasy sport*. A lista de NCM está no **Anexo XVII**. A MP 1.399 deu os **números provisórios** de 2027: o Anexo IV (alíquotas ad valorem e específicas de bebidas e fumígenos), o Anexo VI (redução do pequeno produtor de bebida alcoólica), 0,5% para os prognósticos (art. 7º) e as regras transitórias do art. 6º, **até 31/12/2027**. A lei ordinária das alíquotas de 2028 em diante ainda não existe (art. 15: projeto até 31/05/2027).
- **O dicionário já cobre a espinha.** `Cad_NCM_Imposto_Seletivo` (NCM, alíquota, grupo, fator), `Cad_Is_Hipotese_Base` (contribuinte e base por hipótese do art. 412) e `Mov_Apuracao_Tributo_Item` (quantidade, valor específico, valor de referência informado) já existem. Falta o que o texto pede para **bebida, fumígeno, mineral e prognóstico**: o teor alcoólico e a vintena do produto, a metodologia do valor de referência, a faixa de pequeno produtor e o volume do ano anterior, a memória do cálculo por item, a declaração do gás natural e a receita própria dos concursos.
- **A regra nova: qualquer NCM pode ter IS.** Nenhuma entidade nova fixa grupo ou NCM. A **linha da NCM** diz se há IS, qual é o grupo, o tipo (ad valorem, específica ou mista) e se exige ficha do produto (`Exige_Ficha_Produto`). A **ficha do produto** vale para qualquer NCM. O **cálculo por item** (`Mov_Is_Produto_Apuracao`) lê a linha e não conhece produto. Quando o legislador pôr IS em outra NCM, basta nova linha com vigência; o escalonamento de 2029 a 2033 do art. 422, § 5º, também entra só como novas versões da linha.
- **O que a MP tem de estranho em relação à Tipi** (seção 5): o Anexo IV "Inicial" é igual à Tipi em todas as linhas, mas põe **toda a 24.01 e toda a 24.04 a 30%**, enquanto a Tipi tem NT em parte; **não exclui o álcool etílico** (Tipi 5,2%) da linha de 24%; e trata o "pequeno produtor" por **produção** no Anexo VI e por **fornecimento** no art. 6º, IV.
- **Proposta:** 7 entidades novas (`Cad_Is_Produto_Ficha`, `Cad_Is_Valor_Referencia_Regra`, `Cad_Is_Pequeno_Produtor_Faixa`, `Mov_Is_Pequeno_Produtor_Volume`, `Mov_Is_Produto_Apuracao`, `Mov_Is_Gas_Natural_Declaracao` e `Mov_Prognostico_Receita_Periodo`), 7 campos em `Cad_NCM_Imposto_Seletivo`, 5 domínios abertos, 17 regras e 18 avisos. **Carga provisória** de 25 linhas de NCM, 3 faixas de pequeno produtor, 4 regras de valor de referência e a alíquota de prognósticos (Anexo B).
- **O que não li e pesa:** o **ato do chefe do Poder Executivo do art. 414, § 2º** (metodologia do valor de referência; ainda não publicado), o **Decreto 7.212** (arts. 212-B e 220-A, que a MP cita para o cigarro), a **lei ordinária de 2028**, o **regulamento** do art. 18 da MP e a **forma da declaração do gás natural**. Nada disso trava o desenho; trava a carga de 2028 em diante.

# 2. O que li

| Fonte | O que li | Observação |
|---|---|---|
| MP 1.399/2026 (Planalto) | Arts. 1º a 19 e Anexos IV, V e VI; os Anexos I a III já tinham sido lidos no documento 204 | Texto oficial. Efeitos a partir de 02/02/2027; vale até a lei do art. 15 produzir efeitos |
| LC 214/2025 compilada (com a LC 227/2026) | Arts. 409 a 438 (Livro II) e 244 a 250 (prognósticos); Anexo XVII | Texto compilado de 10/11/2026 |
| Tipi (planilha enviada por você) | As posições 2202.10, 2203, 2204, 2205, 2206, 2208, 2401 a 2404, 2601, 2709.00.10, 2711.11 e 2711.21: 70 linhas | Comparei cada linha com o Anexo IV |
| Dicionário, revisão 42 | `Cad_NCM_Imposto_Seletivo`, `Cad_Is_Hipotese_Base`, `Mov_Is_Veiculo_Apuracao`, `Mov_Apuracao_Tributo_Item`, documentos 196 e 204 | Para não duplicar o que já existe |

Não li: o Decreto 7.212 (arts. 212-B e 220-A), o ato do art. 414, § 2º, a lei ordinária de 2028 e o regulamento do art. 18 da MP, porque não existem ou não foram enviados.

# 3. O que o dicionário já tem

| Peça | O que faz | O que falta para este grupo |
|---|---|---|
| `Cad_NCM_Imposto_Seletivo` | Por NCM (qualquer nível) e Ex: tipo de alíquota, alíquota ad valorem, valor específico, unidade, grupo, modo (fixa ou composta), alíquota inicial, fatores, tabela de ajuste, piso; com vigência | Faixa de teor alcoólico, condição do produto, teto da alíquota (minerais), atualização pelo IPCA, e se exige ficha (7 campos novos) |
| `Cad_Is_Hipotese_Base` | Por hipótese do art. 412 e grupo: contribuinte e base (valor de venda, de referência, aduaneiro mais II, receita própria etc.) | Nada: já tem as 11 linhas de partida, inclusive a regra da maior base dos fumígenos importados |
| `Mov_Is_Veiculo_Apuracao` | Memória do cálculo do IS do veículo | Serve só ao veículo. Bebida, fumígeno e mineral precisam de memória própria (`Mov_Is_Produto_Apuracao`) |
| `Mov_Apuracao_Tributo_Item` | Linha de apuração do item, com quantidade tributada, valor específico por unidade, hipótese de base e valor de referência informado | Recebe o resultado do IS; já tem os campos, sem mudança |
| `Cad_Classe_Sistema` | Domínios abertos, entre eles `grupo_produto_is`, `hipotese_fato_gerador_is`, `tipo_base_calculo_is` | 5 domínios novos (6.3) |
| `Cad_Serie_Cotacao` | Séries de cotação e índices | Guarda o IPCA e as cotações de bolsa dos minerais |
| `Mov_Processo_Prognostico` | **Não tem relação:** é o prognóstico de risco do processo judicial (Fase 8) | O nome é parecido, o assunto é outro; a entidade nova usa `Mov_Prognostico_Receita_Periodo` |

**Regras que já valem (suas decisões):** a NCM dá o grupo e a alíquota; o valor de referência é informado por item até o ato do art. 414, § 2º (Q196-9); embalagem primária é aviso, sem campo próprio (Q196-11); o Motor nunca bloqueia (D-N284).

# 4. O que o texto diz

## 4.1 Grupos, incidência e não incidência

- **Grupos do art. 409, § 1º:** I veículos; II embarcações e aeronaves; III fumígenos; IV bebidas alcoólicas; V bebidas açucaradas; VI bens minerais; VII concursos de prognósticos e *fantasy sport*. O § 2º limita **fumígenos e bebidas alcoólicas à embalagem primária**.
- **Incidência única, sem crédito** (art. 410). **Fatos geradores** (art. 412, I a VIII): primeiro fornecimento, arrematação, transferência não onerosa, incorporação ao ativo, extração, consumo pelo fabricante, fornecimento ou pagamento do serviço, importação.
- **Não incide** (art. 413): energia elétrica e telecomunicações, e bens e serviços com alíquota reduzida pelo art. 9º, § 1º, da EC 132. A MP, art. 5º, acrescenta caminhões e o uso operacional das Forças Armadas e da segurança pública (já no documento 204). Exportação: arts. 426 e 427 (empresa comercial exportadora).
- **Contribuinte e responsável** (arts. 424 e 425): fabricante, importador, arrematante, extrator, fornecedor do serviço; o adquirente do gás natural responde se o destino é diverso.

## 4.2 Base de cálculo

- **Art. 414:** valor de venda; valor de arremate; **valor de referência** na transação não onerosa, no consumo, na extração de mineral e na **comercialização e importação de fumígenos** (LC 227); valor contábil na incorporação ao ativo; **receita própria** dos prognósticos; valor de mercado nas demais hipóteses. O § 2º remete a **metodologia do valor de referência a ato do chefe do Poder Executivo** (não publicado). O § 3º usa o preço de varejo dos fumígenos.
- **Art. 417:** não integram a base a CBS, o IBS e o próprio IS, e os descontos incondicionais e a bonificação nas mesmas condições; **na alíquota específica a bonificação conta na quantidade** (§ 3º); **até 31/12/2032 o ICMS e o ISS também ficam de fora** (§ 4º). **Art. 418:** devolução gera abatimento.
- **Importação (art. 434):** base ad valorem = valor aduaneiro mais o Imposto de Importação; nos **fumígenos, a maior** entre o valor de referência e essa soma; pagamento no registro da declaração; suspensão em regime aduaneiro; loja franca.

## 4.3 Alíquotas: Anexo IV da MP 1.399

A alíquota ad valorem é **Inicial × Fator de conversão = Final**. A Inicial é a da Tipi (art. 3º, § 1º, III); o fator compensa a exclusão dos tributos da base (art. 3º, § 3º). Na importação entra ainda o **fator de ajuste do art. 8º** (1,45 nas bebidas; 1,17 em veículos, aeronaves e embarcações; 1,00 nos demais, e 1,00 nos fumígenos de base "a maior"), cumulativo com o de conversão.

| Produto | Inicial | Fator | Final | Específica |
|---|---|---|---|---|
| Bebidas açucaradas, 2202.10.00 | 2,6 | 1,00 | 2,6 | - |
| Cervejas de malte, 22.03 | 3,9 | 1,07 | 4,2 | - |
| 22.04 (exceto vinhos da madeira, do porto e de xerez) e 22.06 (exceto mais de 14%) | 6,5 | 1,23 | 8,0 | - |
| 22.05 | 9,75 | 1,23 | 12,0 | - |
| Vinhos da madeira, do porto e de xerez (4 códigos), 2206.00.90 com mais de 14%, 2208.90.00 refrescante com menos de 8% | 13 | 1,23 | 16,0 | - |
| 2208.40.00 exceto melaço | 16,25 | 1,23 | 20,0 | - |
| Demais da 22.08 (inclui melaço) | 19,5 | 1,23 | 24,0 | - |
| Cigarros (2402.20.00 exceto Ex 01) e cigarrilhas (2402.10.00 Ex 01) | 66,7 | 1,00 | 66,7 | R$ 3,50 por vintena |
| Demais fumígenos, 24.01 a 24.04 | 30,0 | 1,25 | 37,5 | - |

**Transição de 2027 (MP, art. 6º, até 31/12/2027):** o valor de referência dos fumígenos é **15% do preço de venda a varejo tabelado**, ou o **valor líquido da primeira operação entre partes não relacionadas** quando não há preço tabelado; as **alíquotas específicas de bebidas e fumígenos ficam em zero, salvo cigarros e cigarrilhas**; os **bens minerais extraídos têm alíquota zero**; as notas complementares da Tipi dos veículos (documento 204) seguem. **Art. 7º:** prognósticos a **0,5%**.

## 4.4 Pequeno produtor de bebida alcoólica

O art. 6º, IV, reduz a alíquota **ad valorem** das bebidas alcoólicas quando o volume de fornecimento de álcool não passa de **250.000 litros**: volume = soma, em litros de álcool, do **teor alcoólico × volume de cada bebida**. O § 1º define o pequeno produtor (cervejaria, vinícola, produtor de licores, destilaria, associação ou cooperativa integrada só por pequenos produtores) e soma todos os estabelecimentos e as partes relacionadas. **Anexo VI:** até 50.000 litros, 40%; acima de 50.000 até 125.000, 20%; acima de 125.000 até 250.000, 10%. O volume é o do **ano-calendário anterior**.

## 4.5 Fumígenos

O art. 422, § 1º, I, exige **ad valorem cumulada com específica** para **todo o código 24.02**. A MP só traz a específica (R$ 3,50 por vintena) dos cigarros e das cigarrilhas do art. 3º, § 1º, II (valores do art. 212-B do Decreto 7.212 vigentes na publicação). O art. 436 manda **atualizar as alíquotas específicas pelo IPCA uma vez por ano**. A MP, art. 17, mantém o **preço mínimo de venda a varejo de cigarros** do art. 220-A do Decreto 7.212.

## 4.6 Bens minerais e gás natural

Alíquota **máxima de 0,25%** sobre bens minerais extraídos (art. 422, § 2º, LC 227); a MP põe **zero em 2027**. Anexo XVII: 2601 (minérios de ferro), 2709.00.10 (petróleo), 2711.11.00 e 2711.21.00 (gás natural). **Art. 423:** o gás natural destinado a insumo industrial e a combustível para transporte tem alíquota **zero**, mediante **declaração do adquirente ou do importador**; destino diverso obriga a recolher pela alíquota do art. 422, § 2º, com multa e juros do art. 29, § 2º (adquirente como responsável, importador como contribuinte).

## 4.7 Concursos de prognósticos e *fantasy sport*

O regime dos arts. 244 a 250 trata a **receita própria** como base: arrecadação menos as **premiações** e as **destinações obrigatórias por lei** (art. 245). O art. 414, V, usa a mesma base para o IS, com alíquota de **0,5%** (MP, art. 7º). No meio virtual o apostador é identificado na obrigação acessória (art. 248); o serviço virtual prestado a residente no exterior é exportação e fica imune ao IBS e à CBS (art. 250); quanto ao IS, é a C328.

## 4.8 Apuração, pagamento e vigência

- **Apuração mensal** que consolida os estabelecimentos, com pagamento centralizado e *split payment* (arts. 430 a 433). **Extinção do débito** (MP, art. 14): pagamento, *split payment*, pagamento pelo responsável, abatimento da devolução e compensação (Lei 9.430, arts. 73 e 74). **Apuração assistida** (MP, art. 12) e cancelamento de documento (art. 11).
- **Vigência da MP:** efeitos de 02/02/2027 até a lei de 2028 (arts. 15 e 19). O projeto da lei é para 31/05/2027. **Escalonamento do art. 422, § 5º:** de 2029 a 2033 as alíquotas de fumígenos, bebidas alcoólicas e bebidas açucaradas incorporam, aos poucos, o diferencial do ICMS.

# 5. Achados e leituras minhas

1. **O Anexo IV "Inicial" é igual à Tipi em todas as linhas que conferi.** A MP copiou a Tipi (art. 3º, § 1º, III) e multiplicou pelo fator.
2. **Álcool etílico (2208.90.00 Ex 01):** a Tipi tem 5,2%, mas a MP **não o exclui** da linha "demais da 22.08" (24%). Lido ao pé da letra, o álcool etílico pagaria 24%. É a **C324**.
3. **Fumo (24.01) e desperdícios:** a Tipi tem **NT** em 2401.10.xx e 2401.30.00 (fumo não manufaturado e desperdícios), mas o Anexo IV põe **30 × 1,25 = 37,5% em toda a 24.01**. É a **C325**.
4. **24.04:** a Tipi tem 0%, 10% e 30%, e o Anexo IV põe 37,5% em todos. Também **C325**.
5. **Cigarro sem tabaco (2402.90.00 Ex 01):** a Tipi tem 300%, a MP o põe na linha dos "demais fumígenos" (37,5%), mas o art. 422, § 1º, I, da LC 214 exige ad valorem **e** específica para toda a 24.02. Também **C325**.
6. **Cigarros feitos à mão (2402.20.00 Ex 01):** a MP os tira da linha mista; caem nos 37,5%.
7. **Mostos de uva** (2204.22.20, 2204.29.20, 2204.30.00) ficam na linha da 22.04 (8,0%), embora não sejam bebida pronta. Sem exceção no texto; **C324**.
8. **Pequeno produtor:** o art. 6º, IV, fala em volume de **fornecimento**; o cabeçalho do Anexo VI, em volume de **produção acumulada**. O art. 422, § 8º, I, da LC 214 fala em "volume de produção". O modelo guarda o critério usado (`Criterio_Volume`). **C329.**
9. **A coluna "Final" é arredondada** (3,9 × 1,07 = 4,173, e a tabela diz 4,2). Nas linhas fixas o Motor usa a Final da tabela; na importação multiplica os três fatores, com o arredondamento do parâmetro da empresa (C256).
10. **A específica das bebidas é zero na MP.** O art. 422, § 1º, II, manda considerar teor × volume, mas a tabela traz "-" e o art. 6º, II, zera. O modelo calcula em litros de álcool puro, para quando a lei der o valor.
11. **O valor de referência dos fumígenos é regra transitória** (até 31/12/2027); a regra definitiva depende do ato do art. 414, § 2º. Por isso `Cad_Is_Valor_Referencia_Regra` tem vigência e o campo `Ato_Metodologia_Publicado`.
12. **A alíquota dos minerais em 2028** depende da lei ordinária; o teto é 0,25%. A MP põe zero até 31/12/2027. **C331.**
13. **Gás natural:** o art. 423 faz a alíquota zero depender de **declaração**; a forma é do regulamento. O modelo guarda a declaração, a destinação efetiva e o recolhimento no destino diverso. **C330.**
14. **Bebidas açucaradas:** só o código 2202.10.00 (Anexo XVII), fator 1,00. A **Nota Complementar 22-1 da Tipi** entra no cálculo das **estimativas** dos fatores (art. 3º, § 4º, V, b), e não na alíquota. **C333.**
15. **Não incide:** energia, telecomunicações e bens com alíquota reduzida pela EC 132 (art. 413). O item grava o motivo em `Hipotese_Excecao`.
16. **Qualquer NCM pode ter IS:** o desenho já aceita. A linha de `Cad_NCM_Imposto_Seletivo` aceita qualquer NCM, em qualquer nível, o grupo vem do domínio aberto e o campo novo `Exige_Ficha_Produto` diz se há dado extra. `Mov_Is_Produto_Apuracao` e `Cad_Is_Valor_Referencia_Regra` não citam produto.

# 6. Proposta

## 6.1 Como as peças se encaixam

1. O item da nota (ou da Duimp) traz a **NCM e o Ex da Tipi** (`ID_Ex_Tipi`).
2. O Motor procura a linha vigente de `Cad_NCM_Imposto_Seletivo` na data do fato gerador: o **Ex vence o código** e o **código mais longo vence o mais curto**. Sem linha, não há IS e o Motor não avisa. A linha dá o grupo, o tipo, a alíquota inicial, o fator, a unidade da específica, o teto e se exige ficha.
3. Se `Exige_Ficha_Produto`, o Motor lê a ficha vigente (`Cad_Is_Produto_Ficha`): teor, volume, vintena, condição, preço tabelado.
4. O grupo e a operação escolhem a linha de `Cad_Is_Hipotese_Base` (contribuinte e base).
5. Se a base é o valor de referência, `Cad_Is_Valor_Referencia_Regra` diz como calcular; sem regra, vale o `Valor_Referencia_Informado` do item (Q196-9).
6. Nas bebidas alcoólicas, o Motor confere o volume do ano anterior em `Mov_Is_Pequeno_Produtor_Volume` e aplica a redução da faixa.
7. O resultado vai para `Mov_Is_Produto_Apuracao` (a memória) e para `Mov_Apuracao_Tributo_Item` (o valor). Gás natural com alíquota zero guarda a declaração; prognósticos usam `Mov_Prognostico_Receita_Periodo`, sem item de nota.

## 6.2 As entidades novas

### `Cad_Is_Produto_Ficha` (Contabilidade & Fiscal, com vigência, 18 campos)

A ficha do produto sujeito ao Imposto Seletivo quando a linha da NCM pede dados que a NCM sozinha não traz (`Exige_Ficha_Produto`). Hoje serve às bebidas e aos fumígenos: o teor alcoólico, o volume da embalagem, as unidades por embalagem (a vintena do cigarro), a condição que escolhe a linha de alíquota, o preço de venda a varejo tabelado e a marca da embalagem primária. É o dado do produto que a NCM sozinha não traz.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Produto_Ficha` | identificador | Chave. |
| `ID_Is_Produto_Ficha_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Is_Produto_Ficha_Versao). ID_Is_Produto_Ficha é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Produto_Servico` | referência (Cad_Produto_Servico) --- identidade | O produto da ficha. Vale para qualquer produto cuja NCM tenha linha vigente em `Cad_NCM_Imposto_Seletivo`, de qualquer grupo: a ficha não é exclusiva de bebida e fumígeno. |
| `Teor_Alcoolico_Percentual` | número, opcional | Teor alcoólico em % v/v a 20 °C (MP 1.399, art. 6º, § 1º, IV). Obrigatório nas bebidas alcoólicas: escolhe a linha (acima de 14%, abaixo de 8%) e calcula o litro de álcool. |
| `Volume_Liquido_Litros` | número, opcional | Volume líquido da embalagem primária, em litros. |
| `Litros_Alcool_Puro_Por_Embalagem` | número, opcional | Teor × volume ÷ 100. A LC 214, art. 422, § 1º, II, manda a alíquota específica considerar o produto do teor alcoólico pelo volume. Calculado e gravado. |
| `Unidades_Por_Embalagem` | número, opcional | Unidades da embalagem primária. No cigarro, 20 é a vintena (o maço); a alíquota específica é por vintena. |
| `ID_Condicao_Produto_Is` | referência (Cad_Classe_Sistema, domínio = condicao_produto_is), opcional | A condição do produto: vinho da madeira, do porto ou de xerez; aguardente de cana de melaço ou não; bebida refrescante; cigarro feito à mão. O Ex da Tipi do item (`ID_Ex_Tipi`) é que escolhe a linha da NCM; a condição serve de conferência (aviso 4). Domínio aberto. |
| `Embalagem_Primaria` | booleano | Verdadeiro se a unidade vendida é a embalagem em contato direto com o produto e destinada ao consumidor final (LC 214, art. 409, § 2º). Falso gera o aviso 5. |
| `Preco_Venda_Varejo_Tabelado` | número, opcional | Preço de venda a varejo tabelado do fumígeno, base do valor de referência de 15% (MP 1.399, art. 6º, I, a). Vazio quando não há preço tabelado. |
| `Data_Preco_Varejo` | data, opcional | A data do preço tabelado. |
| `Fonte_Preco_Varejo` | texto, opcional | O ato ou a lista que tabela o preço (por exemplo, o preço mínimo de venda de cigarros do art. 220-A do Decreto 7.212, que o art. 17 da MP mantém). |
| `Atributos_Complementares` | texto, opcional | Atributos que uma lei futura venha a exigir de qualquer NCM (por exemplo, teor de açúcar de bebida), em pares nome=valor, até que viram campo próprio. O Motor ignora; o aviso 17 lembra de propor o campo. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A ficha nasce provisória até o responsável fiscal validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Is_Valor_Referencia_Regra` (Contabilidade & Fiscal, com vigência, 18 campos)

A metodologia do valor de referência do Imposto Seletivo por grupo de produto e por hipótese: o percentual de 15% sobre o preço de varejo dos fumígenos, o valor líquido da primeira operação entre partes não relacionadas, a cotação de bolsa ou de agência dos minerais. Guarda se o ato do art. 414, § 2º, já foi publicado.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Valor_Referencia_Regra` | identificador | Chave. |
| `ID_Is_Valor_Referencia_Regra_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Is_Valor_Referencia_Regra_Versao). ID_Is_Valor_Referencia_Regra é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `ID_Grupo_Produto_Is` | referência (Cad_Classe_Sistema, domínio = grupo_produto_is) --- identidade | O grupo do art. 409, § 1º, ou o grupo que lei futura acrescentar ao domínio aberto (fumígenos, bens minerais, e qualquer outro quando o ato do art. 414, § 2º, os alcançar). |
| `ID_Hipotese_Fato_Gerador_Is` | referência (Cad_Classe_Sistema, domínio = hipotese_fato_gerador_is) --- identidade | A hipótese do art. 412 a que a regra vale: comercialização, importação, extração, transferência não onerosa, consumo pelo fabricante. |
| `ID_Metodologia_Valor_Referencia` | referência (Cad_Classe_Sistema, domínio = metodologia_valor_referencia_is) --- identidade | A metodologia: percentual do preço de varejo, valor líquido da primeira operação, cotação ou índice de bolsa ou agência, valor de mercado, valor informado. Domínio aberto. |
| `Condicao_Preco_Tabelado` | enumeração {com_preco_tabelado, sem_preco_tabelado, indiferente} --- identidade | Se o produto tem preço de venda tabelado no varejo (MP 1.399, art. 6º, I, a) ou não (alínea b). |
| `Percentual_Sobre_Base` | número, opcional | O percentual aplicado à base da metodologia: 15 sobre o preço de varejo (MP, art. 6º, I, a). |
| `ID_Serie_Cotacao` | referência (Cad_Serie_Cotacao), opcional | A série de cotação, índice ou preço quando a metodologia é de bolsa ou de agência (LC 214, art. 414, § 2º). |
| `Exclui_Tributos_Do_Valor` | booleano | Verdadeiro quando o valor líquido exclui o ICMS, a CBS e o IBS (MP, art. 6º, I, b). |
| `Exige_Parte_Nao_Relacionada` | booleano | Verdadeiro quando só vale a primeira operação entre partes não relacionadas (LC 214, art. 5º, §§ 2º a 5º, por remissão da MP). |
| `Base_Importacao_Maior_Valor` | booleano | Verdadeiro nos fumígenos importados com alíquota ad valorem: a base é a maior entre o valor de referência e o valor aduaneiro mais o Imposto de Importação (LC 214, art. 434, § 2º-A). |
| `Ato_Metodologia_Publicado` | booleano | Falso enquanto o ato do chefe do Poder Executivo do art. 414, § 2º, não foi publicado: a linha é a regra transitória da MP e vale até 31/12/2027 (art. 6º). |
| `Fundamento_Legal` | texto | MP 1.399/2026, art. 6º, I; LC 214, arts. 414 e 434. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Is_Pequeno_Produtor_Faixa` (Contabilidade & Fiscal, com vigência, 12 campos)

A tabela do Anexo VI da MP 1.399: a redução da alíquota ad valorem das bebidas alcoólicas por faixa de volume de álcool do pequeno produtor, e o limite de 250 mil litros.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Pequeno_Produtor_Faixa` | identificador | Chave. |
| `ID_Is_Pequeno_Produtor_Faixa_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Is_Pequeno_Produtor_Faixa_Versao). ID_Is_Pequeno_Produtor_Faixa é a identidade, única e referenciada pelas outras tabelas; cada versão guarda a sua janela de vigência --- Fase 0, seção 2. |
| `Volume_Alcool_Litros_Minimo` | número --- identidade | Início da faixa, em litros de álcool, exclusivo (0 na primeira faixa). |
| `Volume_Alcool_Litros_Maximo` | número --- identidade | Fim da faixa, em litros de álcool, inclusive (50.000, 125.000 e 250.000). |
| `Percentual_Reducao` | número | A redução da alíquota ad valorem: 40, 20 ou 10 (MP, Anexo VI). |
| `Volume_Limite_Pequeno_Produtor` | número | O teto do conceito de pequeno produtor: 250.000 litros de álcool (MP, art. 6º, IV). |
| `Fundamento_Legal` | texto | MP 1.399/2026, art. 6º, IV e § 1º, e Anexo VI. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido (versão vigente). |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Is_Pequeno_Produtor_Volume` (Contabilidade & Fiscal, sem vigência, 16 campos)

O volume do ano-calendário anterior que enquadra a empresa como pequeno produtor de bebida alcoólica, somando todos os estabelecimentos e as partes relacionadas, e a faixa de redução que daí resulta.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Pequeno_Produtor_Volume` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | O contribuinte. O volume soma todos os seus estabelecimentos (MP, art. 6º, § 1º, II, a). |
| `Ano_Calendario_Base` | número | O ano-calendário anterior ao da apuração, que é o que a MP manda considerar. |
| `ID_Tipo_Pequeno_Produtor` | referência (Cad_Classe_Sistema, domínio = tipo_pequeno_produtor_is) | Cervejaria, vinícola, produtor de licores, destilaria, ou associação ou cooperativa (MP, art. 6º, § 1º, III). |
| `Associacao_Integrada_So_Por_Pequenos` | booleano | Verdadeiro na associação ou cooperativa integrada exclusivamente por pequenos produtores (alínea b do inciso III). |
| `Criterio_Volume` | enumeração {fornecimento_art_6_iv, producao_anexo_vi} | O texto da MP fala em volume de **fornecimento** no art. 6º, IV, e em volume de **produção acumulada** no cabeçalho do Anexo VI. Enquanto a Receita não esclarece (C329), o ERP guarda qual critério foi usado. |
| `Volume_Proprio_Litros` | número | Litros de bebida fornecidos (ou produzidos, conforme o critério) pelos estabelecimentos do contribuinte no ano-calendário anterior. |
| `Volume_Partes_Relacionadas_Litros` | número | Litros fornecidos pelas partes relacionadas (LC 214, art. 5º, §§ 2º a 5º). |
| `Volume_Total_Litros_Alcool` | número | Soma, em litros de álcool, do produto do teor alcoólico pelo volume de cada bebida (MP, art. 6º, § 1º, I). Calculado pelas fichas. |
| `Enquadra_Pequeno_Produtor` | booleano | Verdadeiro quando o volume total de álcool é inferior a 250.000 litros (alínea a do inciso III). |
| `ID_Is_Pequeno_Produtor_Faixa` | referência (Cad_Is_Pequeno_Produtor_Faixa), opcional | A faixa do Anexo VI que vale para o volume. Vazio quando não enquadra. |
| `Percentual_Reducao_Aplicado` | número | A redução da faixa, copiada para o cálculo. Zero quando não enquadra. |
| `Origem_Volume` | enumeração {calculado_pelo_erp, informado_pelo_contador} | Se o volume saiu das notas e das fichas ou foi digitado. |
| `Data_Calculo` | data | Quando o volume foi calculado. |
| `Memoria_Calculo` | texto | A conta, para auditoria. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do enquadramento. |

### `Mov_Is_Produto_Apuracao` (Contabilidade & Fiscal, sem vigência, 27 campos)

A memória do cálculo do Imposto Seletivo de um item de **qualquer NCM** que tenha linha em `Cad_NCM_Imposto_Seletivo` (hoje bebidas, fumígenos e minerais): a quantidade da alíquota específica, o valor de referência, as alíquotas inicial e final, os fatores, a redução do pequeno produtor, a parte ad valorem e a parte específica. Faz para esses bens o que `Mov_Is_Veiculo_Apuracao` faz para os veículos.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Produto_Apuracao` | identificador | Chave. |
| `ID_Apuracao` | referência (Mov_Apuracao_Tributo_Item) | A linha de apuração do item que recebeu o resultado. |
| `ID_NCM_Imposto_Seletivo` | referência (Cad_NCM_Imposto_Seletivo) | A linha da NCM que deu a alíquota inicial, o fator e a condição. |
| `ID_Is_Produto_Ficha` | referência (Cad_Is_Produto_Ficha), opcional | A ficha usada (bebidas e fumígenos). |
| `ID_Is_Valor_Referencia_Regra` | referência (Cad_Is_Valor_Referencia_Regra), opcional | A metodologia do valor de referência usada, quando a base é esse valor. |
| `ID_Is_Pequeno_Produtor_Volume` | referência (Mov_Is_Pequeno_Produtor_Volume), opcional | O enquadramento de pequeno produtor usado. |
| `ID_Is_Gas_Natural_Declaracao` | referência (Mov_Is_Gas_Natural_Declaracao), opcional | A declaração de destinação do gás natural, quando a alíquota é zero por ela. |
| `Data_Fato_Gerador` | data | A data que escolhe as linhas vigentes. |
| `Operacao` | enumeração {saida_fabricante, importacao, extracao, transferencia_nao_onerosa, consumo_pelo_fabricante, incorporacao_ativo, arrematacao} | A hipótese do art. 412. Na importação entra o fator de ajuste. |
| `Quantidade_Base_Especifica` | número, opcional | A quantidade da alíquota específica: litros de álcool puro nas bebidas, vintenas nos cigarros. Inclui os bens dados em bonificação (LC 214, art. 417, § 3º). |
| `ID_Unidade_Medida_Base` | referência (Cad_Unidade_Medida), opcional | A unidade da quantidade acima. |
| `Valor_Base_Ad_Valorem` | número, opcional | A base da parte ad valorem: valor de venda, valor de referência, valor aduaneiro mais o Imposto de Importação, ou a maior entre as duas nos fumígenos importados. |
| `Valor_Referencia_Calculado` | número, opcional | O valor de referência calculado pela regra, quando a base é esse valor. |
| `Exclusao_Icms_Iss_Ate_2032` | número, opcional | O ICMS e o ISS que não integram a base até 31/12/2032 (LC 214, art. 417, § 4º). |
| `Aliquota_Inicial_Ad_Valorem` | número, opcional | A alíquota inicial do Anexo IV, vinda da linha da NCM. |
| `Fator_Conversao` | número, opcional | O fator de conversão do Anexo IV (1,00 a 1,25), vindo da linha da NCM. |
| `Fator_Ajuste_Importacao` | número, opcional | O fator do art. 8º da MP (1,45 nas bebidas, 1,00 nos fumígenos e nos demais), cumulativo com o de conversão. Vazio fora da importação. |
| `Aliquota_Final_Ad_Valorem` | número, opcional | Inicial × conversão × ajuste, com o arredondamento do parâmetro da empresa. |
| `Reducao_Pequeno_Produtor_Percentual` | número, opcional | A redução do Anexo VI aplicada à alíquota ad valorem da bebida alcoólica. |
| `Valor_Especifico_Unitario` | número, opcional | O valor específico por unidade, já atualizado pelo IPCA (R$ 3,50 por vintena; zero nas bebidas até 31/12/2027). |
| `Valor_Ad_Valorem` | número | Base × alíquota final, depois da redução. |
| `Valor_Especifico` | número | Quantidade × valor específico unitário. |
| `Valor_Is_Apurado` | número | Soma das duas partes. É o valor gravado em `Mov_Apuracao_Tributo_Item`. |
| `Hipotese_Excecao` | enumeração {nenhuma, aliquota_zero_especifica_transitoria, aliquota_zero_mineral_transitoria, aliquota_zero_gas_natural, suspensao_regime_aduaneiro, suspensao_loja_franca, aliquota_zero_ou_reducao_por_lei_futura, nao_incide_exportacao, nao_incide_energia_telecom, nao_incide_aliquota_reduzida_ec_132} | Quando diferente de `nenhuma`, o valor ou parte dele é zero, ou o imposto não incide, e o item guarda o motivo. |
| `Fator_Reduzido_Por_Decreto` | booleano | Verdadeiro se o fator usado é o reduzido por decreto (MP, art. 3º, § 3º, e art. 8º, § 3º). O aviso 12 lembra que a redução só vale depois do art. 156-A, § 9º, da Constituição. |
| `Dados_Provisorios` | booleano | Verdadeiro se alguma linha usada está `provisorio`: o relatório avisa. |
| `Memoria_Calculo` | texto | O texto da conta, para auditoria. |

### `Mov_Is_Gas_Natural_Declaracao` (Contabilidade & Fiscal, sem vigência, 15 campos)

A declaração do adquirente ou do importador de que o gás natural será usado como insumo em processo industrial ou como combustível para transporte (LC 214, art. 423), que leva a alíquota a zero, e o recolhimento quando o destino efetivo é outro.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Is_Gas_Natural_Declaracao` | identificador | Chave. |
| `Origem_Tipo` | enumeração {nota_fiscal_entrada, nota_fiscal_saida, duimp} | O documento a que a declaração se refere. |
| `ID_Item_Origem` | referência genérica | O item do documento (`Mov_Nota_Fiscal_Entrada_Item`, `Mov_Nota_Fiscal_Saida_Item` ou item da Duimp). |
| `ID_Participante_Declarante` | referência (Cad_Participante) | O adquirente ou o importador que declara. |
| `Papel_Declarante` | enumeração {adquirente_responsavel, importador_contribuinte} | O art. 423, § 2º: o adquirente responde como responsável e o importador como contribuinte. |
| `ID_Destinacao_Gas_Natural` | referência (Cad_Classe_Sistema, domínio = destinacao_gas_natural_is) | Insumo em processo industrial, combustível para transporte ou outra destinação. |
| `Data_Declaracao` | data | Quando a declaração foi feita (forma do regulamento, ainda não publicada). |
| `Quantidade_Declarada` | número | A quantidade de gás natural declarada. |
| `ID_Unidade_Medida` | referência (Cad_Unidade_Medida) | A unidade da quantidade. |
| `Destinacao_Efetiva_Confirmada` | booleano | Verdadeiro quando o uso real confere com a declaração. |
| `Data_Constatacao_Destino_Diverso` | data, opcional | Quando se constatou destino diferente do declarado. |
| `Valor_Is_A_Recolher` | número, opcional | O imposto da alíquota do art. 422, § 2º, que passa a ser devido no destino diverso. |
| `Valor_Multa_Juros` | número, opcional | Multa e juros de mora do art. 29, § 2º, da LC 214. |
| `ID_Documento_Declaracao` | referência (Cad_Documento), opcional | O documento da declaração no GED. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A aprovação do tratamento do destino diverso. |

### `Mov_Prognostico_Receita_Periodo` (Contabilidade & Fiscal, sem vigência, 16 campos)

A receita própria da entidade que opera concursos de prognósticos e fantasy sport em um período: arrecadação, premiações pagas e destinações obrigatórias. É a base do Imposto Seletivo (LC 214, art. 414, V) e também a do IBS e da CBS (art. 245). Fica previsto; nenhum cliente opera hoje.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Prognostico_Receita_Periodo` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A entidade que promove a atividade e é a contribuinte (art. 424, V). |
| `Competencia` | data | O mês de apuração (LC 214, art. 430). |
| `ID_Modalidade_Prognostico` | referência (Cad_Classe_Sistema, domínio = modalidade_prognostico_is) | Modalidade lotérica, aposta de quota fixa, sweepstake, aposta de turfe, demais apostas ou fantasy sport (art. 244). |
| `Meio_Aposta` | enumeração {fisico, virtual} | Em meio físico ou virtual. No virtual o apostador é identificado na obrigação acessória (art. 248, parágrafo único). |
| `Valor_Arrecadacao` | número | O produto da arrecadação do período. |
| `Valor_Premiacoes_Pagas` | número | As premiações pagas, que saem da base e não sofrem incidência (art. 245, I e parágrafo único). |
| `Valor_Destinacoes_Obrigatorias` | número | As destinações obrigatórias por lei a órgão ou fundo público e a outros beneficiários (art. 245, II). |
| `Valor_Receita_Propria` | número | Arrecadação menos premiações e destinações. Calculado e gravado. |
| `Aliquota_Is_Percentual` | número | A alíquota do Imposto Seletivo: 0,5% (MP, art. 7º). |
| `Valor_Is_Apurado` | número | Receita própria × alíquota. |
| `Local_Aposta_Informado` | booleano | Verdadeiro quando o local da aposta consta da obrigação acessória (art. 248). |
| `Prestado_A_Residente_Exterior` | booleano | Verdadeiro quando o serviço virtual foi prestado a residente no exterior: exportado e imune ao IBS e à CBS (art. 250), a conferir quanto ao IS (C328). |
| `Dados_Provisorios` | booleano | Verdadeiro se a alíquota usada está `provisorio`. |
| `ID_Apuracao` | referência (Mov_Apuracao_Tributo_Item), opcional | A linha de apuração que recebeu o Imposto Seletivo. |
| `Memoria_Calculo` | texto | A conta, para auditoria. |

## 6.3 Campos novos em entidades existentes

| Entidade | Campo | Tipo | Para quê |
|---|---|---|---|
| `Cad_NCM_Imposto_Seletivo` | `Exige_Ficha_Produto` | booleano | Verdadeiro quando a linha só calcula com os dados de `Cad_Is_Produto_Ficha` (teor alcoólico, vintena, preço tabelado). Qualquer NCM que ganhe linha no futuro diz aqui se precisa de ficha; falso = a NCM e o valor da operação bastam. |
| `Cad_NCM_Imposto_Seletivo` | `Teor_Alcoolico_Minimo_Percentual` | número, opcional | Teor alcoólico mínimo (exclusivo) da linha: 14 na bebida do código 2206.00.90 com teor acima de 14% (MP 1.399, Anexo IV). |
| `Cad_NCM_Imposto_Seletivo` | `Teor_Alcoolico_Maximo_Percentual` | número, opcional | Teor alcoólico máximo (exclusivo) da linha: 8 na bebida refrescante do código 2208.90.00 (Anexo IV). |
| `Cad_NCM_Imposto_Seletivo` | `ID_Condicao_Produto_Is` | referência (Cad_Classe_Sistema, domínio = condicao_produto_is), opcional | A condição do produto que esta linha trata (vinho da madeira, aguardente de melaço, cigarro feito à mão). O Ex da Tipi escolhe a linha; a condição e o teor da ficha são conferência. |
| `Cad_NCM_Imposto_Seletivo` | `Aliquota_Maxima_Percentual` | número, opcional | O teto que a lei impõe à linha: 0,25% nos bens minerais extraídos (LC 214, art. 422, § 2º). |
| `Cad_NCM_Imposto_Seletivo` | `Atualiza_Pelo_Ipca` | booleano | Verdadeiro nas linhas com valor específico, que a lei manda atualizar pelo IPCA uma vez por ano (LC 214, art. 436). |
| `Cad_NCM_Imposto_Seletivo` | `ID_Serie_Cotacao_Atualizacao` | referência (Cad_Serie_Cotacao), opcional | A série do IPCA usada na atualização do valor específico. A data-base vem da lei ordinária (C327). |

**Domínios e valores** (sem campo novo):

| Entidade | Mudança |
|---|---|
| `Cad_Classe_Sistema` | **5 domínios abertos novos:** `condicao_produto_is` (vinho_madeira_porto_xerez, aguardente_cana_nao_melaco, aguardente_melaco, bebida_refrescante_menos_8, cigarro_feito_a_mao), `metodologia_valor_referencia_is` (percentual_preco_varejo, valor_liquido_primeira_operacao, cotacao_bolsa_ou_agencia, valor_mercado, valor_informado), `tipo_pequeno_produtor_is` (cervejaria, vinicola, produtor_licores, destilaria, associacao_ou_cooperativa), `destinacao_gas_natural_is` (insumo_processo_industrial, combustivel_transporte, outra) e `modalidade_prognostico_is` (modalidade_loterica, aposta_quota_fixa, sweepstake, aposta_turfe, demais_apostas, fantasy_sport). Valores provisórios; **domínios abertos** |
| `Cad_Classe_Sistema` (domínio `grupo_produto_is`) | **Sem valor novo:** os sete valores cobrem o art. 409. Grupo novo de lei futura entra por carga |
| `Cad_Motor_Regra` e filhas | **Carga:** 17 regras (Anexo A), provisórias |
| `Cad_Is_Hipotese_Base` | **Sem mudança:** a linha padrão vale para qualquer grupo; a linha com grupo vale sobre ela |
| `Mov_Apuracao_Tributo_Item` | **Nenhum campo novo:** `Quantidade_Tributada`, `Valor_Especifico_Unidade`, `ID_Is_Hipotese_Base` e `Valor_Referencia_Informado` já recebem o resultado |

## 6.4 Exemplos numéricos

| N | Caso | Conta | Resultado |
|---|---|---|---|
| 1 | Cerveja de malte (2203), saída do fabricante, base já líquida das exclusões do art. 417 de R$ 80.000,00 | Alíquota final da tabela, 4,2%; específica zero (MP, art. 6º, II) | **R$ 3.360,00** |
| 2 | Aguardente de cana que não é de melaço (2208.40.00), pequeno produtor com 100.000 litros de álcool no ano anterior (faixa de 20%), base de R$ 50.000,00 | 20,0% × (1 − 20%) = 16,0%; específica zero | **R$ 8.000,00** |
| 3 | Cigarro (2402.20.00, sem o Ex 01), 10,000 maços de vintena com preço de venda a varejo tabelado de R$ 8,00 | Valor de referência = 15% × R$ 8,00 = R$ 1,20 por maço, base R$ 12.000,00; ad valorem 66,7% = R$ 8.004,00; específica 10,000 × R$ 3,50 = R$ 35.000,00 | **R$ 43.004,00** |
| 4 | Importação de aguardente de vinho (2208.20.00): valor aduaneiro R$ 50.000,00 e Imposto de Importação R$ 10.000,00 | Base R$ 60.000,00; alíquota = 19,5 × 1,23 × 1,45 = 34,778% (sem arredondar; o arredondamento é a C256) | **R$ 20.866,95** |
| 5 | Concurso de prognósticos: arrecadação R$ 1.000.000,00, premiações R$ 600.000,00 e destinações obrigatórias R$ 100.000,00 | Receita própria R$ 300.000,00 × 0,5% | **R$ 1.500,00** |
| 6 | Minério de ferro (2601) extraído: valor de referência R$ 1.000.000,00 | Em 2027 a alíquota é zero (MP, art. 6º, III, a, 3); a partir de 2028 o teto é 0,25% (LC 214, art. 422, § 2º) | **R$ 0,00** em 2027; no máximo **R$ 2.500,00** em 2028 |

Os valores são hipotéticos, só para conferir a conta do Motor. O exemplo 3 usa um preço de varejo inventado.

# 7. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|---|---|---|
| 1 | Produto sem ficha | A linha da NCM tem `Exige_Ficha_Produto` e o produto não tem linha vigente em `Cad_Is_Produto_Ficha` |
| 2 | NCM do IS sem alíquota carregada | A NCM tem linha de IS, mas a alíquota inicial, o valor específico ou o fator está vazio na data do fato gerador (por exemplo, 2028 em diante, até a lei) |
| 3 | Teor alcoólico ou volume ausente | Bebida alcoólica sem teor ou sem volume na ficha: a específica e o enquadramento do pequeno produtor não calculam |
| 4 | Ficha contradiz o Ex da Tipi | O teor ou a condição da ficha está fora da faixa da linha que o Ex escolheu (por exemplo, Ex "mais de 14%" com 12%) |
| 5 | Fora da embalagem primária | `Embalagem_Primaria` falso em bebida alcoólica ou fumígeno: o IS só incide na embalagem primária (art. 409, § 2º) |
| 6 | Valor de referência não informado | A base é o valor de referência, não há regra aplicável (sem preço tabelado ou primeira operação) e `Valor_Referencia_Informado` está vazio |
| 7 | Regra transitória do valor de referência | `Ato_Metodologia_Publicado` falso: vale a regra do art. 6º da MP até 31/12/2027 |
| 8 | Específica zerada pela MP | Bebida ou fumígeno (exceto cigarro e cigarrilha) com específica em zero por força do art. 6º, II |
| 9 | Mineral com alíquota zero transitória | Bem mineral em 2027: alíquota zero; a partir de 2028 depende da lei ordinária e o teto é 0,25% |
| 10 | Pequeno produtor sem volume do ano anterior | Bebida alcoólica sem `Mov_Is_Pequeno_Produtor_Volume`: o Motor não aplicou a redução |
| 11 | Critério do volume | O volume foi calculado por `fornecimento_art_6_iv` e o Anexo VI fala em produção (C329) |
| 12 | Fator reduzido por decreto | `Fator_Reduzido_Por_Decreto` verdadeiro: a redução só vale depois do art. 156-A, § 9º, da Constituição (MP, art. 3º, § 6º) |
| 13 | Importação com fator de ajuste | O Motor multiplicou conversão e ajuste (1,45 nas bebidas) ou usou 1,00 por ser fumígeno de base "a maior" |
| 14 | Gás natural sem declaração | NCM 2711.11.00 ou 2711.21.00 com alíquota zero e sem `Mov_Is_Gas_Natural_Declaracao` |
| 15 | Destino diverso do gás natural | A declaração tem `Data_Constatacao_Destino_Diverso`: recolher com a alíquota do art. 422, § 2º, multa e juros |
| 16 | Dado provisório | A linha, a faixa, a regra ou a ficha usada está `provisorio` |
| 17 | Variação fora de campo | `Atributos_Complementares` preenchido: a lei futura pediu um atributo que ainda não tem campo; propor o campo |
| 18 | Bonificação na específica | Há bens dados em bonificação em item com alíquota específica: entram na quantidade (art. 417, § 3º) |

# 8. Perguntas

Todas aprovadas em 12/11/2026 ("seguir com as recomendações", D-N575).

| Id | Pergunta | Recomendação |
|---|---|---|
| Q216-1 | Aprova as **7 entidades novas** como no 6.2: `Cad_Is_Produto_Ficha` (18 campos), `Cad_Is_Valor_Referencia_Regra` (18), `Cad_Is_Pequeno_Produtor_Faixa` (12), `Mov_Is_Pequeno_Produtor_Volume` (16), `Mov_Is_Produto_Apuracao` (27), `Mov_Is_Gas_Natural_Declaracao` (15) e `Mov_Prognostico_Receita_Periodo` (16)? | Sim |
| Q216-2 | Aprova os **7 campos novos** em `Cad_NCM_Imposto_Seletivo` e os **5 domínios abertos** (6.3), com a regra de que **qualquer NCM pode ter IS** (linha com vigência, grupo do domínio aberto, `Exige_Ficha_Produto`)? | Sim |
| Q216-3 | Aprova a **carga provisória** do Anexo B: 25 linhas de NCM e Ex (Anexo IV e minerais), com vigência de **02/02/2027 a 31/12/2027**, 3 faixas do Anexo VI, 4 regras de valor de referência e 0,5% para prognósticos, **sem linha para 2028** até a lei do art. 15? | Sim, tudo provisório |
| Q216-4 | Aprova as **17 regras** (Anexo A) e os **18 avisos** (seção 7) como texto do Motor, sempre sem bloquear (D-N284)? | Sim |
| Q216-5 | Onde o Anexo IV diverge da Tipi (24.01 e 24.04 inteiros a 37,5%, álcool etílico a 24%, cigarro sem tabaco a 37,5%), o ERP segue o **texto literal da MP** e avisa, até a Receita esclarecer (C324 e C325)? | Sim, literal com aviso |
| Q216-6 | Quando o valor de referência não puder sair da regra (sem preço tabelado ou primeira operação), o ERP usa o **valor informado no item** e avisa (como na Q196-9), em vez de bloquear? | Sim |

# 9. O que acontece se você aprovar

- **Tudo (Q216-1 a Q216-6):** 7 entidades novas e **129 campos** (122 nas entidades novas e 7 em `Cad_NCM_Imposto_Seletivo`), **30 campos de referência novos** (28 nas entidades novas e 2 na NCM) e **5 domínios abertos novos**. No ensaio sobre a revisão 42 (1.206 entidades, 13.895 campos, 3.586 campos de referência, 360 domínios e 247 mestres): **1.213 entidades, 14.024 campos, 3.616 campos de referência, 365 domínios e 250 mestres** (as três entidades com vigência viram mestres). No ensaio com o gerador de DDL: **1.463 tabelas físicas** (+10, com as três tabelas de versão), 3.866 chaves estrangeiras (+33), 3.957 índices (+33) e 11.790 comentários (+122); a auditoria fecha com **0 achados em aberto**. Se o documento 215 for consolidado junto, os totais somam: **1.220 entidades, 14.154 campos, 3.645 campos de referência, 369 domínios e 256 mestres**. São somas do ensaio, a conferir no "consolidar".
- **Carga:** 5 domínios abertos com 24 valores, 17 regras e 18 avisos do Motor, **25 linhas de NCM** (Anexo B), 3 faixas, 4 regras de valor de referência e 1 alíquota de prognóstico, tudo provisório.
- **Ao contador:** onze perguntas novas, C324 a C334 (documento 188, Parte 21).
- **Se a Q216-1 vier "não":** o IS de bebida e fumígeno fica sem memória do cálculo, e o usuário digita a base e o valor em `Mov_Apuracao_Tributo_Item`, sem teor, vintena, pequeno produtor nem declaração do gás natural.

# 10. Limites

- **Li o texto oficial da MP e da LC 214, mas a MP é provisória.** Ela vale até a lei de 2028 (art. 19); o Congresso pode mudá-la e o ERP guarda tudo com vigência.
- **O ato do art. 414, § 2º** (valor de referência) **não existe**; a regra do art. 6º vale até 31/12/2027.
- **Decreto 7.212, arts. 212-B e 220-A:** a MP remete a eles os valores do cigarro (R$ 3,50 por vintena) e o preço mínimo; **não li o Decreto**. O R$ 3,50 vem da tabela da MP.
- **Tipi:** conferi as 70 linhas das posições envolvidas; posições de **qualquer outro NCM** só entram com carga futura.
- **Prognósticos:** o ERP **prevê** a receita própria e a alíquota, mas **nenhum cliente opera** hoje; sem tela nem rotina até haver cliente.
- **Escalonamento de 2029 a 2033** (art. 422, § 5º) e a **atualização pelo IPCA** (art. 436) dependem de lei ordinária: entram como novas versões da linha (C327).
- **Importação de fumígenos:** o fator de ajuste 1,00 vale quando a base é a maior entre o valor de referência e o valor aduaneiro mais o II (MP, art. 3º, § 4º, IV); o modelo segue o texto e não projeta o que acontece se essa regra de base mudar (aviso 13).

# Anexo A. As 17 regras provisórias do Motor

| Regra | Se | Resultado | Fundamento | Vigência |
|---|---|---|---|---|
| R1 | O item tem NCM com linha vigente em `Cad_NCM_Imposto_Seletivo` na data do fato gerador, **de qualquer grupo** | O IS incide. O Ex vence o código, e o código mais longo vence o mais curto. Sem linha, o IS não incide. O Motor não tem lista fixa de grupos nem de NCM | LC 214, art. 409; Anexo XVII; regra de Alberto, 12/11/2026 | sem fim fixado |
| R2 | O item tem grupo e operação | A linha de `Cad_Is_Hipotese_Base` com grupo vale sobre a linha padrão e dá contribuinte e base | LC 214, arts. 412, 414 e 424 | sem fim fixado |
| R3 | A base é o valor de venda | Valor da operação menos descontos incondicionais, CBS, IBS e o próprio IS; até 31/12/2032, menos também o ICMS e o ISS | LC 214, art. 417 | ICMS e ISS até 31/12/2032 |
| R4 | A base é o valor de referência e a regra exige | Aplica `Percentual_Sobre_Base` ao preço de varejo tabelado (15%), ou usa o valor líquido da primeira operação entre partes não relacionadas | MP 1.399, art. 6º, I | até 31/12/2027 |
| R5 | A linha é de modo fixo | Alíquota ad valorem = `Aliquota_Ad_Valorem` (a coluna Final). Na importação: inicial × conversão × ajuste, com o arredondamento do parâmetro (C256) | MP, arts. 3º e 8º; Anexo IV | conforme a linha |
| R6 | Bebida alcoólica de pequeno produtor | Redução da faixa do Anexo VI sobre a alíquota ad valorem, só com volume do ano anterior abaixo de 250.000 litros de álcool | MP, art. 6º, IV, e Anexo VI | até 31/12/2027 |
| R7 | A linha tem valor específico | IS específico = quantidade (litros de álcool puro ou vintenas, com a bonificação) × valor unitário atualizado pelo IPCA; zero nas bebidas e nos fumígenos (exceto cigarro e cigarrilha) até 31/12/2027 | LC 214, arts. 417, § 3º, 422 e 436; MP, art. 6º, II | até 31/12/2027 (zero) |
| R8 | A linha é mista (cigarro) | IS = parte ad valorem + parte específica | LC 214, art. 422, § 1º; MP, Anexo IV | conforme a linha |
| R9 | Bem mineral extraído | Alíquota zero em 2027; depois, o teto de 0,25% da linha; base = valor de referência | MP, art. 6º, III, a, 3; LC 214, arts. 414 e 422, § 2º | zero até 31/12/2027 |
| R10 | Gás natural com declaração | Alíquota zero; se o destino efetivo for outro, recolhe pela alíquota do art. 422, § 2º, com multa e juros | LC 214, art. 423 | sem fim fixado |
| R11 | Concurso de prognóstico | Base = arrecadação menos premiações e destinações obrigatórias; alíquota 0,5% | LC 214, arts. 245 e 414, V; MP, art. 7º | conforme a MP |
| R12 | Operação com energia, telecomunicações ou bem com alíquota reduzida pela EC 132, ou exportação | O IS não incide; o item grava o motivo | LC 214, arts. 413, 426 e 427 | sem fim fixado |
| R13 | Importação | Base = valor aduaneiro + II (fumígeno: a maior com o valor de referência); fator de ajuste cumulativo; pago no registro da declaração; suspensão em regime aduaneiro e loja franca | LC 214, art. 434; MP, art. 8º | conforme a MP |
| R14 | Fator reduzido por decreto | Mínimo 1,00 e só depois do art. 156-A, § 9º, da Constituição | MP, art. 3º, §§ 3º, 6º e 7º; art. 8º, § 3º | sem fim fixado |
| R15 | Há IS apurado no mês | Apuração mensal consolidando os estabelecimentos; pagamento, *split payment*, abatimento de devolução e compensação | LC 214, arts. 418 e 430 a 433; MP, art. 14 | sem fim fixado |
| R16 | O valor específico venceu um ano | Atualiza pelo IPCA, em nova versão da linha | LC 214, art. 436 | anual |
| R17 | A linha tem `Exige_Ficha_Produto` | O Motor lê a ficha vigente; sem ficha, calcula com o que tem e avisa | Regra de Alberto, 12/11/2026 | sem fim fixado |

# Anexo B. Carga provisória proposta (não aplicada)

| NCM / Ex | Descrição | Tipo | Inicial (%) | Fator | Final (%) | Específica (R$) | Condições |
|---|---|---|---|---|---|---|---|
| 2202.10.00 | Bebidas açucaradas | ad_valorem | 2,6 | 1,00 | 2,6 | - | Só o código 2202.10.00 (Anexo XVII da LC 214) |
| 2203 | Cervejas de malte (posição) | ad_valorem | 3,9 | 1,07 | 4,2 | - |  |
| 2204 | Vinhos e mostos (posição), regra geral | ad_valorem | 6,5 | 1,23 | 8,0 | - | Exceto os quatro códigos de vinho da madeira, do porto e de xerez, abaixo |
| 2204.21.00 Ex 01 | Vinhos da madeira, do porto e de xerez | ad_valorem | 13 | 1,23 | 16,0 | - | Condição `vinho_madeira_porto_xerez` |
| 2204.22.11 Ex 01 | Idem | ad_valorem | 13 | 1,23 | 16,0 | - | Idem |
| 2204.22.19 Ex 01 | Idem | ad_valorem | 13 | 1,23 | 16,0 | - | Idem |
| 2204.29.10 Ex 01 | Idem | ad_valorem | 13 | 1,23 | 16,0 | - | Idem |
| 2205 | Vermutes e demais da posição 22.05 | ad_valorem | 9,75 | 1,23 | 12,0 | - |  |
| 2206 | Sidra e demais da posição 22.06, regra geral | ad_valorem | 6,5 | 1,23 | 8,0 | - | Exceto o 2206.00.90 com mais de 14% |
| 2206.00.90 Ex 01 | Bebida com teor alcoólico superior a 14% | ad_valorem | 13 | 1,23 | 16,0 | - | `Teor_Alcoolico_Minimo_Percentual` = 14 |
| 2208 | Demais bebidas da posição 22.08 | ad_valorem | 19,5 | 1,23 | 24,0 | - | Inclui rum e aguardente de melaço |
| 2208.40.00 | Rum e aguardente de cana, exceto melaço | ad_valorem | 16,25 | 1,23 | 20,0 | - | Condição `aguardente_cana_nao_melaco` |
| 2208.40.00 Ex 01 | Rum e aguardente obtidos do melaço da cana | ad_valorem | 19,5 | 1,23 | 24,0 | - | Condição `aguardente_melaco` |
| 2208.90.00 Ex 02 | Bebida refrescante com menos de 8% de álcool | ad_valorem | 13 | 1,23 | 16,0 | - | `Teor_Alcoolico_Maximo_Percentual` = 8 |
| 2402.20.00 | Cigarros que contêm tabaco | mista | 66,7 | 1,00 | 66,7 | 3,50 por vintena | Exceto o Ex 01 (feitos à mão); `Atualiza_Pelo_Ipca` |
| 2402.10.00 Ex 01 | Cigarrilhas | mista | 66,7 | 1,00 | 66,7 | 3,50 por vintena | Idem |
| 2402.20.00 Ex 01 | Cigarros feitos à mão | ad_valorem | 30,0 | 1,25 | 37,5 | - | Cai na linha dos demais fumígenos (MP, Anexo IV, última linha) |
| 2401 | Fumo e desperdícios (posição) | ad_valorem | 30,0 | 1,25 | 37,5 | - | Literal do Anexo IV; a Tipi tem NT em parte (C325) |
| 2402 | Charutos e demais da posição 24.02 | ad_valorem | 30,0 | 1,25 | 37,5 | - | O Ex 01 do 2402.90.00 (cigarro sem tabaco) cai aqui por ora (C325) |
| 2403 | Fumo para narguilé, homogeneizado e outros | ad_valorem | 30,0 | 1,25 | 37,5 | - |  |
| 2404 | Nicotina e produtos sem tabaco | ad_valorem | 30,0 | 1,25 | 37,5 | - | A Tipi tem 0, 10 e 30 (C325) |
| 2601 | Minérios de ferro e concentrados | ad_valorem | 0 | - | 0 | - | Alíquota zero em 2027; `Aliquota_Maxima_Percentual` = 0,25 |
| 2709.00.10 | Petróleo | ad_valorem | 0 | - | 0 | - | Idem |
| 2711.11.00 | Gás natural liquefeito | ad_valorem | 0 | - | 0 | - | Idem; declaração do art. 423 |
| 2711.21.00 | Gás natural no estado gasoso | ad_valorem | 0 | - | 0 | - | Idem; declaração do art. 423 |

**Vigência de todas as linhas acima:** de **02/02/2027** (art. 19 da MP) a **31/12/2027**; **sem linha para 2028** até a lei do art. 15. Os fatores e alíquotas dos Anexos IV e V seguem a MP; `Situacao_Dado` = `provisorio`.

**Anexo VI (`Cad_Is_Pequeno_Produtor_Faixa`):**

| De (litros de álcool, exclusivo) | Até (inclusive) | Redução | Limite |
|---|---|---|---|
| 0 | 50.000 | 40% | 250.000 |
| 50.000 | 125.000 | 20% | 250.000 |
| 125.000 | 250.000 | 10% | 250.000 |

**Valor de referência (`Cad_Is_Valor_Referencia_Regra`):**

| Grupo | Hipótese | Metodologia | Condição | Percentual | Observação |
|---|---|---|---|---|---|
| fumigeno | primeiro_fornecimento | percentual_preco_varejo | com_preco_tabelado | 15 | MP, art. 6º, I, a |
| fumigeno | primeiro_fornecimento | valor_liquido_primeira_operacao | sem_preco_tabelado | - | Exclui ICMS, CBS e IBS; parte não relacionada |
| fumigeno | importacao | percentual_preco_varejo | com_preco_tabelado | 15 | Base é a maior com o valor aduaneiro mais II (`Base_Importacao_Maior_Valor`) |
| bem_mineral | extracao_bem_mineral | valor_informado | indiferente | - | Até o ato do art. 414, § 2º |

**Prognósticos:** alíquota de 0,5% do IS sobre a receita própria (MP, art. 7º), em `Mov_Prognostico_Receita_Periodo.Aliquota_Is_Percentual`.

# Anexo C. Perguntas ao contador (C324 a C334, documento 188, Parte 21)

| Id | Assunto |
|---|---|
| C324 | Álcool etílico (2208.90.00 Ex 01, Tipi 5,2%) e mostos de uva (2204.22.20, 2204.29.20 e 2204.30.00): o Anexo IV os alcança nas linhas de 24% e de 8%? |
| C325 | Fumígenos: o Anexo IV põe 37,5% em toda a 24.01, em toda a 24.04 e no cigarro sem tabaco (2402.90.00 Ex 01, Tipi 300%), onde a Tipi tem NT, 0%, 10% e 300%, e o art. 422, § 1º, I, exige específica em toda a 24.02. Vale o texto literal? |
| C326 | Valor de referência dos fumígenos: qual é o preço de venda a varejo tabelado (o preço mínimo do art. 220-A do Decreto 7.212?) e como achar a primeira operação entre partes não relacionadas quando não há preço tabelado? |
| C327 | Atualização pelo IPCA (art. 436): índice, data-base, data de vigência e se o R$ 3,50 por vintena é valor de 2026 |
| C328 | Prognósticos e *fantasy sport*: o serviço virtual prestado a residente no exterior (art. 250) também está fora do IS? Como se aplica o IS ao *fantasy sport* e ao apostador não identificado? |
| C329 | Pequeno produtor: volume de **fornecimento** (art. 6º, IV) ou de **produção** (cabeçalho do Anexo VI e art. 422, § 8º)? Como somar partes relacionadas, associações e cooperativas? |
| C330 | Gás natural (art. 423): forma, prazo e quem faz a declaração; como o ERP prova a destinação efetiva; multa e juros do destino diverso |
| C331 | Bens minerais: alíquota de 2028 em diante (teto de 0,25%), valor de referência por mineral (cotação de bolsa ou agência) e o IS na extração exportada |
| C332 | Importação: IS pago no registro da declaração, suspensão em regime aduaneiro, loja franca e a combinação dos fatores 1,23 e 1,45; e a base "a maior" dos fumígenos com fator 1,00 |
| C333 | Bebidas açucaradas: o conceito legal além do código 2202.10.00, e o papel da Nota Complementar 22-1 da Tipi (só nas estimativas ou também na alíquota?) |
| C334 | Embalagem primária (art. 409, § 2º): como tratar bebida a granel, cigarro avulso e fornecimento fora da embalagem primária |
