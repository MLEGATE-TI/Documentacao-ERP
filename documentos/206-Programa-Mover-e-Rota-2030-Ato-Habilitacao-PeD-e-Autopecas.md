# Programa Mover e Rota 2030: ato de registro, habilitação, pesquisa e desenvolvimento e autopeças não produzidas (bloco B8) — Documento 206

> **O que este documento faz.** Você enviou a página e a legislação do Rota 2030 do MDIC e o modelo de pedido de ato de registro, e escolheu o escopo "programa inteiro: ato, habilitação, P&D e autopeças". Li a Lei 14.902/2024 (Mover), o Decreto 12.435/2025, o Decreto 9.557/2018 (Rota 2030) e o modelo, e desenhei o bloco **B8**: 18 entidades novas que registram o ato de registro de compromissos, a habilitação, o projeto, os dispêndios, o crédito financeiro, os aportes ao FNDIT, o regime de autopeças e as obrigações com o MDIC. Entra também o legado do Rota 2030 (a dedução do IRPJ e da CSLL), que a lei nova não revogou por inteiro.
>
> **Nada foi aplicado ao dicionário.** Ele está na revisão 38 (1.165 entidades e 13.204 campos). Este documento só vale com a sua resposta às Q206-1 a Q206-12.

*Fontes: Lei 14.902/2024 (texto de 02/07/2025, arts. 2º a 8º e 12 a 32), Decreto 12.435/2025 (arts. 1º a 15 e Anexo I; os Anexos II a IV só varridos), Decreto 9.557/2018 (arts. 13 a 38, Anexos VI, X e XI só varridos), páginas "Rota 2030 - Mobilidade e Logística" e "Legislação Rota 2030" do MDIC e a planilha "Solicitação de Ato de Registro de Compromissos – Pessoa Jurídica". Dicionário: revisão 38, mais os documentos 202, 204 e 205.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que o MDIC pede de quem vende veículo no País.** Desde 01/06/2025, o fabricante ou o importador de veículo novo dos códigos do Anexo I do Decreto 12.435 precisa ter **ato de registro de compromissos** (eficiência energética, reciclabilidade, rotulagem e desempenho estrutural). Quem importa sem o ato paga multa de 20% e só nacionaliza com o comprovante (art. 7º). O ato antigo do Rota 2030 foi revogado na mesma data (art. 14).
- **O que o Mover dá a quem faz pesquisa e desenvolvimento.** A empresa **habilitada** forma **crédito financeiro de CSLL**: 50% dos dispêndios, limitado a 5% da receita bruta do segundo mês anterior, com acréscimos por indicadores (até 7%, 13% ou 16% da receita) e crédito sobre o investimento em ativo fixo (12,5% ou 25%). O crédito é compensado ou ressarcido em dinheiro no 48º mês; os tetos globais vão de R$ 3,5 bilhões (2024) a R$ 4,1 bilhões (2028).
- **O que o regime de autopeças pede.** A importação sem produção nacional equivalente é **isenta do Imposto de Importação**, com contrapartida de **2% do valor aduaneiro** em P&D, até o último dia útil do segundo mês depois do desembaraço, e aplicação do bem na industrialização em três anos.
- **Proposta:** **18 entidades novas** (247 campos, contando 1 campo novo em entidade do 204), **1 domínio novo** (`tipo_atividade_pd_mover`, 6 valores), 4 valores novos em domínios existentes, 3 valores novos em enumerações (`Mov_Credito_Fiscal.Origem` e `Mov_Titulo.Origem_Tipo`), **34 linhas de parâmetros legais** (28 códigos, todos documentados pela regra da Q201-3), **80 linhas** do Anexo I do Decreto 12.435 na lista legal e **4 obrigações novas** no catálogo. O ERP **registra, calcula o que a lei fecha e avisa; não bloqueia** (D-N284).
- **Três achados.** (1) O **Rota 2030 acabou**: a habilitação cessou em 30/11/2023 e o ato de registro foi revogado em 01/06/2025; só ficam os direitos adquiridos. O modelo de pedido que você enviou é de 2018 e pede os documentos do art. 2º do Decreto 9.557. (2) A **multa das autopeças** é de 30% sobre a diferença na lei (art. 28, § 1º) e de 100% no Decreto 9.557 (art. 38, § 3º); a lei é posterior, e o desenho usa 30% (C275). (3) A aba **Pontuação** do modelo tem 14 perguntas que somam 25 pontos, com fórmulas quebradas, e não diz a que processo serve; **não modelei** (Q206-11).
- **Contador:** 9 perguntas novas, C269 a C277 (documento 188, Parte 14).

# 2. O que li

| Fonte | O que li | O que tirei |
|-------------------|-----------------------------------------|-----------------------------------------|
| Lei 14.902/2024 | Arts. 2º a 8º (requisitos, ato, multas), 12 a 25 (habilitação, créditos, penalidades), 26 a 28 (autopeças), 29 (FNDIT) e 31 | Os percentuais, limites, prazos e penalidades do Anexo A |
| Decreto 12.435/2025 | Arts. 1º a 15 e Anexo I | O ato de registro, as multas por requisito, a importação sem ato e os 80 códigos da Tipi |
| Decreto 9.557/2018 | Arts. 13 a 38 | A habilitação e a dedução do Rota 2030; o regime de autopeças (arts. 34 a 38), ainda a única regra detalhada |
| Páginas do MDIC | Duas | A lista de 17 portarias do Rota 2030 e a estrutura do programa; nenhuma portaria do Mover |
| Modelo de pedido (planilha) | Três abas | Os campos do requerimento e a declaração; a aba Pontuação |

O modelo é um exemplo preenchido de 2018 (assinado em novembro de 2018, de uma montadora); **não copiei nenhum dado dele**, só os campos: razão social, CNPJ da matriz, contato, endereço, anexos (contrato social, procuração, identidade do solicitante) e a declaração de compromisso.

# 3. O que o dicionário já tem

| Peça | Entidade | Uso no B8 |
|----------------------|----------------------------------|--------------------------------------------|
| Habilitação de regime especial | `Cad_Habilitacao_Regime_Especial` (21 campos) | O Mover e as autopeças entram como dois tipos novos; o ato e a situação ficam aqui |
| Regime automotivo (B6) | `Cad_Habilitacao_Automotiva` e as outras sete do 202 | Outro regime, da LC 214; não se mistura com o Mover |
| Lista legal | `Cad_Lista_Legal_Item` | O Anexo I do Decreto 12.435 e a lista de autopeças entram como dois tipos de lista |
| Importação | `Mov_Duimp`, `Mov_Duimp_Item`, `Mov_Duimp_Item_Tributo` | A multa sem ato e a isenção do II ligam-se ao item |
| Crédito e compensação | `Mov_Credito_Fiscal`, `Mov_Perdcomp` | O crédito financeiro do Mover nasce e é compensado aqui |
| Título | `Mov_Titulo` | Aportes e recolhimentos viram título a pagar |
| Apuração do IRPJ e da CSLL | `Mov_Apuracao_Irpj_Csll_Item` (`Valor_Deducoes`) | Recebe a dedução do Rota 2030 |
| Contabilidade | `Mov_Lancamento`, `Cad_Dimensao_Contabil_Valor` | O dispêndio liga-se ao lançamento e ao centro de custo de P&D |
| Versão sustentável (204) | `Cad_Veiculo_Versao_Sustentavel` | Recebe a referência ao ato de registro |

Não há hoje nenhuma entidade de Mover, de Rota 2030, de FNDIT nem de dispêndio de P&D (procurei por nome e por texto nos campos).

# 4. Achados e leituras minhas

# 1. **O Rota 2030 acabou.** O Decreto 9.557 fixa a habilitação até 30/11/2023 e manda cancelar todas nessa data, "exceto quanto ao cumprimento dos compromissos assumidos e ao usufruto dos direitos adquiridos" (art. 14, II e § 4º). O Decreto 12.435 revoga os atos de registro do art. 2º do Decreto 9.557 a partir de 01/06/2025 (art. 14). A página do MDIC, atualizada em 06/07/2026, ainda descreve o programa antigo. O desenho trata o Rota 2030 como **legado**: um valor de `Programa` na habilitação e uma entidade de dedução. 2. **O Mover não substitui tudo por inteiro.** O art. 21, I, da Lei 14.902 diz que os benefícios do Mover **não se acumulam** com os arts. 1º a 26 da Lei 13.755 (a lei do Rota 2030). O regime de autopeças, porém, está na Lei 14.902 (arts. 26 a 28) com o Decreto 9.557 como único detalhe; **não achei decreto novo** do regime. Uso o Decreto 9.557, arts. 34 a 38, como regra e marco a divergência da multa (C275). 3. **Multa das autopeças: 30% ou 100%.** Lei 14.902, art. 28, § 1º: 30% sobre a diferença entre o aporte devido e o realizado. Decreto 9.557, art. 38, § 3º: 100%. A lei é de 2024 e o decreto de 2018; uso 30% (Q206-7). 4. **A multa de importação sem ato tem base composta.** Decreto 12.435, art. 7º, I: 20% "sobre o valor aduaneiro, acrescido dos tributos da nacionalização e de margem de comercialização de 20%". Leio como 20% × (valor aduaneiro + tributos) × 1,20 (C271). A Lei (art. 5º) fala em 20% da receita da venda; para o importado, o art. 5º, parágrafo único, manda cobrar na nacionalização. 5. **Os tetos de multa dos requisitos.** As multas de eficiência energética (arts. 6º e 7º da Lei: R$ 50 a R$ 500 por faixa) e de desempenho estrutural multiplicam por veículo licenciado, somam no máximo 20% da receita dos veículos que não cumpriram (art. 8º, § 1º) e, nos importados, 20% do valor aduaneiro mais tributos (§ 2º). Só a multa maior vale quando falham os dois ciclos de eficiência (art. 6º, parágrafo único). **O ERP não recalcula**: registra o valor que o MDIC apurou (Q206-6, C270). 6. **O dispêndio mínimo e o crédito.** O benefício "não incidirá" sobre 0,6%, 0,3% e 0,3% da receita bruta (art. 16, § 4º): é o dispêndio mínimo, que não gera crédito. A lei é anual; o crédito é mensal. **Leio** que os primeiros dispêndios aprovados do ano cobrem o mínimo e só o excedente forma crédito (C274). 7. **Os indicadores do art. 18.** O crédito de 50% "poderá ser acrescido" em até 20 pontos (fabril e mercado, limite 7% da receita) e em até 250 pontos (tecnologia avançada, limite 13% ou 16% da receita dos produtos). Leio que os pontos **somam ao 50%** e que o limite de receita **substitui** o de 5% (C274). Os pesos e a escala MRL estão em ato do MDIC que **não li**. 8. **A aba Pontuação.** Quatorze perguntas (eficiência, segurança, conectividade, novos materiais, inovação, reciclabilidade, novo modelo, início da produção local, componentes nacionais, baixa escala, complexidade, patentes, inexistência de tecnologia, política industrial) valem 1 ou 2 pontos, até 25. As fórmulas apontam para células removidas (`#REF!`) e as perguntas falam de "autopeça importada": parece pontuação de pleito de autopeça não produzida. Não achei essa pontuação na lei nem nos decretos (Q206-11). 9. **Os anexos de 2018.** O Anexo X (lista de autopeças não produzidas, cerca de mil linhas) e o Anexo XI (percentuais mínimos do Rota 2030, 2018 a 2023) são de 2018; a Camex altera a lista (Decreto 9.557, art. 34, § 3º). Não carreguei nenhum (Q206-10).

# 5. Proposta

## 5.1 Como as peças se encaixam

O B8 tem quatro grupos. O **grupo 1** responde "a empresa pode vender ou importar veículo?" (ato de registro, requisitos por ano, multa na importação sem ato). O **grupo 2** responde "a empresa pode formar crédito de P&D?" (habilitação, projeto, dispêndios, mínimo, crédito, indicadores, aportes, ocorrências). O **grupo 3** responde "a importação de autopeça com isenção está em dia?" (item importado e contrapartida de 2%). O **grupo 4** cobre as obrigações com o MDIC e o legado do Rota 2030. O Mover e as autopeças são dois tipos novos de `Cad_Habilitacao_Regime_Especial`, como o B6 fez com o regime automotivo e a Suframa com a ZFM.

| Entidade | Para quê | Vigência | Campos |
|-----------------------------|------------------------------------------------------|---------|--------|
| `Cad_Mover_Ato_Registro` | O ato de registro de compromissos que o MDIC emite ao fabricante ou ao importador de veículos novos (Decreto 12.435, art. | sim | 23 |
| `Mov_Mover_Requisito_Ano` | Cada requisito do art. | não | 14 |
| `Mov_Mover_Importacao_Sem_Ato` | A importação de veículo por quem não tem ato de registro de compromissos: a multa compensatória de 20% sobre o valor aduaneiro mais os tributos da nacionalização mais a margem de 20%, recolhida como aporte ao FNDIT, e a informação ao importador autorizado da marca (Decreto 12.435, art. | não | 14 |
| `Cad_Mover_Habilitacao` | A habilitação da empresa ao regime de incentivos à pesquisa, ao desenvolvimento e à produção tecnológica do Programa Mover (Lei 14.902, arts. | sim | 19 |
| `Cad_Mover_Projeto` | O projeto com autorização prévia do MDIC que sustenta os créditos financeiros: de pesquisa e desenvolvimento (art. | não | 14 |
| `Mov_Mover_Projeto_Cronograma` | O cronograma físico-financeiro e de produção do projeto (art. | não | 9 |
| `Mov_Mover_Credito_Autorizacao_Ano` | O valor de crédito financeiro que o MDIC autoriza ao projeto em cada ano-calendário, dentro do teto global da lei (R$ 3,5 bilhões em 2024 a R$ 4,1 bilhões em 2028, art. | não | 9 |
| `Mov_Mover_Dispendio` | Cada dispêndio de pesquisa e desenvolvimento, de engenharia ou de investimento em ativo fixo que a empresa lança no Mover: o valor, a atividade, a forma de execução, a prova e a elegibilidade. | não | 16 |
| `Mov_Mover_Dispendio_Minimo_Ano` | O dispêndio mínimo do ano: o percentual da receita bruta, o realizado, o resíduo que passa ao ano seguinte, o excesso dos dois anos anteriores e o complemento por aporte (Lei 14.902, art. | não | 11 |
| `Mov_Mover_Credito_Apuracao` | A apuração mensal do crédito financeiro do Mover, por habilitação e por tipo de crédito: a base de dispêndios, o saldo não utilizado, o limite sobre a receita bruta do segundo mês anterior, o percentual e o crédito calculado. | não | 17 |
| `Mov_Mover_Credito_Indicador` | Os pontos percentuais que cada indicador do art. | não | 7 |
| `Mov_Mover_Aporte` | Todo aporte ao FNDIT ou a conta de programa prioritário: o dispêndio feito sob a forma de aporte, o complemento de glosa, a contrapartida de 2% das autopeças e as multas pagas por aporte. | não | 13 |
| `Mov_Mover_Habilitacao_Ocorrencia` | A prorrogação, a suspensão, o cancelamento e o restabelecimento da habilitação, com a consequência de cada um: o cancelamento retroage ao início do ano-calendário do fato e obriga a recolher os créditos ressarcidos ou compensados, ou a estorná-los, até o último dia útil do mês seguinte (Lei 14.902, arts. | não | 12 |
| `Mov_Mover_Obrigacao_Acessoria` | As obrigações de prestar informação ao MDIC que a lei e o decreto criam: relatório de acompanhamento do ato, comprovação anual da habilitação e dos dispêndios, inventário e pegada de carbono, comprovação do aporte das autopeças. | não | 13 |
| `Cad_Mover_Parametro` | Os parâmetros legais do Programa Mover e do regime de autopeças: percentuais, limites, prazos e tetos. | sim | 14 |
| `Mov_Autopecas_Importacao_Item` | O item importado no regime de autopeças não produzidas (isenção do Imposto de Importação das partes, peças, componentes, conjuntos, subconjuntos e pneumáticos sem produção nacional equivalente: Lei 14.902, art. | não | 14 |
| `Mov_Autopecas_Contrapartida` | A contrapartida de 2% do valor aduaneiro em pesquisa, desenvolvimento e inovação e programas prioritários, por habilitação e mês de desembaraço, com o prazo (último dia útil do segundo mês seguinte), a multa sancionatória e a multa de mora (Lei 14.902, arts. | não | 14 |
| `Mov_Rota_2030_Deducao` | A dedução do IRPJ e da CSLL devidos da empresa habilitada ao Rota 2030: 30% dos dispêndios de pesquisa e desenvolvimento, mais até 15% sobre os estratégicos (limite de 45%), com o excedente levado aos períodos seguintes (Decreto 9.557, art. | não | 13 |


## 5.2 Grupo 1: Ato de registro de compromissos (Decreto 12.435)

### `Cad_Mover_Ato_Registro` (Contabilidade & Fiscal, com vigência, 23 campos)

O ato de registro de compromissos que o MDIC emite ao fabricante ou ao importador de veículos novos (Decreto 12.435, art. 2º). Sem ele, a empresa não cumpre a condição do art. 1º para comercializar veículo produzido no País nem para importar veículo dos códigos do Anexo I; a importação sem o ato paga a multa de 20% do art. 7º. Substitui, desde 01/06/2025, os atos do art. 2º do Decreto 9.557 (Decreto 12.435, art. 14).

| Campo | Tipo | Descrição |
|------------------------|--------------------------------------|--------------------------------------|
| `ID_Mover_Ato_Registro` | identificador | Chave. |
| `ID_Mover_Ato_Registro_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Mover_Ato_Registro_Versao). Fase 0, seção 2. |
| `ID_Empresa` | referência (Cad_Empresa) --- identidade | A empresa titular do ato (CNPJ da matriz, como no requerimento). |
| `Numero_Ato` | código (até 40) | O número do ato publicado pelo MDIC. A nota e o Duimp do veículo podem citá-lo. |
| `Data_Ato` | data | A data de emissão do ato, assinado pelo Secretário de Desenvolvimento Industrial, Inovação, Comércio e Serviços (art. 2º, § 1º, II). |
| `Tipo_Requerente` | enumeração {fabricante, importador, fabricante_e_importador} | Quem o ato alcança. O importador sem vínculo direto com o fabricante fica dispensado do ato (Lei 14.902, art. 4º) e paga a multa do art. 7º do Decreto na importação (C269). |
| `Abrange_Veiculos_Leves` | booleano | O ato cobre os códigos da seção A do Anexo I (veículos leves): metas de eficiência, reciclabilidade, rotulagem e desempenho estrutural (art. 1º, I). |
| `Abrange_Veiculos_Pesados` | booleano | O ato cobre os códigos da seção B (veículos pesados): relatório de eficiência, reciclabilidade, rotulagem e desempenho estrutural (art. 1º, II). |
| `Producao_Sob_Licenca_Encomenda` | booleano | Verdadeiro quando a empresa produz sob licença ou encomenda. Se ela não tem ato, os requisitos recaem sobre o licenciante ou o encomendante (art. 1º, §§ 4º e 5º). |
| `ID_Participante_Licenciante_Encomendante` | referência (Cad_Participante), opcional | O licenciante ou encomendante a quem os requisitos recaem. Obrigatório quando `Producao_Sob_Licenca_Encomenda` é verdadeiro e a empresa não tem ato. |
| `Tem_Autorizacao_Assistencia_Rede` | booleano | A empresa está formalmente autorizada a prestar assistência técnica e a organizar rede de distribuição no País (art. 2º, § 2º, III, a). |
| `Tem_Autorizacao_Marca` | booleano | A empresa está autorizada a usar as marcas do fabricante nos veículos comercializados no País, por documento válido no Brasil (art. 2º, § 2º, III, b). |
| `Situacao_Ato` | enumeração {solicitado, vigente, cancelado, revogado} | Só `vigente` cumpre a condição do art. 1º. `revogado` é o ato do Decreto 9.557 extinto em 01/06/2025. |
| `Motivo_Cancelamento` | enumeração {a_pedido, descumprimento_reciclabilidade, descumprimento_rotulagem, outro}, opcional | O cancelamento é consequência do não cumprimento das metas de reciclabilidade ou de rotulagem (art. 4º) ou é pedido a qualquer tempo pelo titular (art. 2º, § 5º). |
| `Data_Solicitacao_Cancelamento` | data, opcional | A data em que a empresa pediu o cancelamento. |
| `Janela_Residual_Inicio` | data, opcional | Calculada: 12 meses antes de `Data_Solicitacao_Cancelamento`. O cancelamento não dispensa os requisitos, calculados nos 12 meses anteriores ao pedido ou nos últimos 12 meses de atividade (art. 2º, § 6º). |
| `Janela_Residual_Fim` | data, opcional | Calculada: a data do pedido de cancelamento (ou o último dia de atividade). |
| `ID_Documento_Solicitacao` | referência (Cad_Documento), opcional | O requerimento e os anexos: contrato social, procuração, autorizações e declaração de compromisso (art. 2º, § 2º). |
| `Numero_Ato_Rota_2030_Revogado` | código (até 40), opcional | O número do ato emitido pelo art. 2º do Decreto 9.557, quando a empresa tinha um; fica só como histórico. |
| `Fundamento_Legal` | texto, opcional | Lei 14.902, art. 2º; Decreto 12.435, arts. 1º a 7º. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Mov_Mover_Requisito_Ano` (Contabilidade & Fiscal, sem vigência, 14 campos)

Cada requisito do art. 1º do Decreto 12.435 em cada ano-calendário: a meta, o resultado informado, a situação e a sanção prevista. O ERP registra o que o MDIC e a auditoria credenciada apuram e avisa; não calcula a média ponderada da frota (D-N284).

| Campo | Tipo | Descrição |
|------------------|-----------------------------------------|-----------------------------------------|
| `ID_Mover_Requisito_Ano` | identificador | Chave. |
| `ID_Mover_Ato_Registro` | referência (Cad_Mover_Ato_Registro) | O ato a que o requisito pertence. |
| `Ano_Calendario` | número | O ano da meta. |
| `Tipo_Requisito` | enumeração {eficiencia_energetica_leves, relatorio_eficiencia_pesados, reciclabilidade, rotulagem, desempenho_estrutural, pegada_carbono, inventario_carbono} | Os requisitos do art. 1º, I e II; a pegada de carbono vale a partir de 01/01/2027 (art. 1º, § 1º); o inventário, a apresentar até 31/12/2026 (art. 2º, § 2º, V). |
| `Meta_Valor` | número, opcional | A meta numérica do ano, quando existe (por exemplo, o consumo energético máximo em MJ/km). A meta vem dos Anexos II a IV; o ERP guarda o número informado. |
| `Unidade_Meta` | texto (30), opcional | A unidade da meta: MJ/km, gCO₂e/km, razão de reciclabilidade, percentual de modelos etiquetados. |
| `Resultado_Valor` | número, opcional | O resultado atingido, informado a partir do relatório ao MDIC ou do relatório da auditoria. |
| `Situacao_Requisito` | enumeração {a_apurar, em_acompanhamento, cumprido, nao_cumprido, dispensado} | `dispensado` para os produtos do art. 3º (aplicação especial, uso bélico, pequena série, quadriciclos e triciclos). |
| `Sancao_Prevista` | enumeração {nenhuma, multa_compensatoria, cancelamento_do_ato} | Preenchida pelo Motor pela tabela do tipo: eficiência energética e desempenho estrutural geram multa compensatória (arts. 5º e 6º do Decreto; arts. 6º e 7º da Lei); reciclabilidade e rotulagem geram o cancelamento (art. 4º). |
| `Valor_Multa_Compensatoria` | número, opcional | O valor que o MDIC apurou. O ERP não recalcula as faixas por centésimo e por grama (C270); só registra e confere o aporte. |
| `ID_Mover_Aporte` | referência (Mov_Mover_Aporte), opcional | O aporte ao FNDIT que pagou a multa. |
| `Verificado_Por` | enumeração {mdic, auditoria_credenciada}, opcional | Quem verificou o atendimento: o MDIC diretamente ou entidade credenciada contratada pela empresa (art. 2º, § 4º; art. 11). |
| `ID_Documento_Verificacao` | referência (Cad_Documento), opcional | O relatório do MDIC ou da auditoria. |
| `Observacao` | texto, opcional | Anotação livre. |

### `Mov_Mover_Importacao_Sem_Ato` (Contabilidade & Fiscal, sem vigência, 14 campos)

A importação de veículo por quem não tem ato de registro de compromissos: a multa compensatória de 20% sobre o valor aduaneiro mais os tributos da nacionalização mais a margem de 20%, recolhida como aporte ao FNDIT, e a informação ao importador autorizado da marca (Decreto 12.435, art. 7º). O comprovante é condição para nacionalizar o veículo.

| Campo | Tipo | Descrição |
|--------------------------|-------------------------------|-------------------------------------------|
| `ID_Mover_Importacao_Sem_Ato` | identificador | Chave. |
| `ID_Duimp` | referência (Mov_Duimp) | A declaração de importação do veículo. |
| `ID_Duimp_Item` | referência (Mov_Duimp_Item), opcional | O item (veículo) da declaração, quando a declaração tem mais de um. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa importadora. |
| `Valor_Aduaneiro` | número | O valor aduaneiro do veículo, em reais. |
| `Valor_Tributos_Nacionalizacao` | número | Os tributos incidentes na nacionalização (II, IPI, PIS, Cofins, IS e demais). A leitura de quais entram é minha (C271). |
| `Percentual_Margem_Comercializacao` | número | 20, do parâmetro `importacao_sem_ato_margem` (art. 7º, I e § 3º). |
| `Base_Multa` | número | Calculada: (`Valor_Aduaneiro` + `Valor_Tributos_Nacionalizacao`) × (1 + margem). Leitura minha do § 3º (C271). |
| `Percentual_Multa` | número | 20, do parâmetro `importacao_sem_ato_multa`. |
| `Valor_Multa` | número | Calculada: `Base_Multa` × `Percentual_Multa`. |
| `ID_Mover_Aporte` | referência (Mov_Mover_Aporte), opcional | O aporte ao FNDIT que pagou a multa (art. 7º, § 1º). |
| `Data_Informacao_Importador_Autorizado` | data, opcional | A data em que a empresa informou a entrada do veículo ao importador autorizado da marca. Deve ser anterior à homologação do veículo (art. 7º, II e § 4º). |
| `ID_Participante_Importador_Autorizado` | referência (Cad_Participante), opcional | O importador autorizado da marca, quando há. |
| `Situacao` | enumeração {a_pagar, paga, ato_vigente_na_data} | `ato_vigente_na_data`: havia ato vigente e a multa não se aplica. |

## 5.3 Grupo 2: Habilitação, projeto, dispêndio e crédito financeiro (Lei 14.902)

### `Cad_Mover_Habilitacao` (Contabilidade & Fiscal, com vigência, 19 campos)

A habilitação da empresa ao regime de incentivos à pesquisa, ao desenvolvimento e à produção tecnológica do Programa Mover (Lei 14.902, arts. 12 a 14), concedida por ato do Secretário do MDIC, com comprovação anual. Especializa `Cad_Habilitacao_Regime_Especial` (tipo `mover`), como `Cad_Habilitacao_Automotiva` o faz para o regime automotivo. Com `Programa` = `rota_2030`, guarda a habilitação antiga (Decreto 9.557, art. 13), que cessou em 30/11/2023 e só mantém os direitos adquiridos.

| Campo | Tipo | Descrição |
|----------------------|---------------------------------------|---------------------------------------|
| `ID_Mover_Habilitacao` | identificador | Chave. |
| `ID_Mover_Habilitacao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Mover_Habilitacao_Versao). Fase 0, seção 2. |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) --- identidade | A habilitação de tipo `mover` (valor novo em `tipo_regime_especial_federal`). O titular é a pessoa jurídica habilitada; o número do ato e a situação ficam lá. |
| `Programa` | enumeração {mover, rota_2030} | `rota_2030` só para a habilitação antiga, que mantém os direitos adquiridos (Decreto 9.557, art. 14, § 4º). |
| `Modalidade_Habilitacao` | enumeração {producao_automotiva, projeto_desenvolvimento_producao, servicos_pd_engenharia} | As três do art. 13: (I) produção de produtos automotivos, sistemas e soluções estratégicas; (II) projeto de desenvolvimento e produção tecnológica aprovado; (III) serviços de pesquisa, desenvolvimento, inovação ou engenharia. No Rota 2030 as modalidades eram outras (Decreto 9.557, art. 13). |
| `Segmento_Empresa` | enumeração {automoveis_comerciais_leves, caminhoes_onibus, autopecas_sistemas} | Decide o dispêndio mínimo: 0,6%, 0,3% ou 0,3% da receita bruta (art. 16, § 4º). Uma empresa com mais de um segmento tem uma habilitação por segmento (C272). |
| `ID_Filial` | referência (Cad_Filial), opcional | O estabelecimento da fábrica, planta ou linha: a habilitação do projeto é específica para cada uma (art. 13, § 4º, III). |
| `Descricao_Planta_Linha` | texto, opcional | A fábrica, a planta industrial ou a linha de produção que o projeto instala. |
| `Tipo_Projeto_Especial` | enumeração {nova_producao, relocalizacao_unidade, reciclagem_economia_circular, infraestrutura_gnl_baixo_carbono}, opcional | Os projetos do art. 13, § 4º, I: relocalização de unidade, linha ou célula; unidade de reciclagem ou economia circular; infraestrutura de postos de GNL e fontes de baixa emissão. |
| `Data_Ato_Habilitacao` | data | A data do ato do Secretário. |
| `Prorrogada` | booleano | A habilitação do projeto só pode ser prorrogada uma vez, se o cronograma foi cumprido (art. 13, § 4º, III). |
| `Data_Fim_Prorrogacao` | data, opcional | O novo fim da habilitação, quando prorrogada. |
| `ID_Dimensao_Valor_Centro_Custo_Pd` | referência (Cad_Dimensao_Contabil_Valor), opcional | O centro de custo de pesquisa e desenvolvimento que a lei exige (art. 13, § 1º, II). |
| `Marca_Propria_Tecnologia_Global` | booleano | A empresa faz no País o desenvolvimento e a gestão global de tecnologia e de marca própria de veículo ou autopeça: o limite do art. 18, § 4º sobe de 13% para 16% (art. 18, § 5º). |
| `Data_Ultima_Comprovacao_Anual` | data, opcional | A última comprovação anual do atendimento aos compromissos (art. 13, § 2º, I). |
| `Fundamento_Legal` | texto, opcional | Lei 14.902, arts. 12 a 14 e 18; Decreto 9.557, arts. 13 a 18, no Rota 2030. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Mover_Projeto` (Contabilidade & Fiscal, sem vigência, 14 campos)

O projeto com autorização prévia do MDIC que sustenta os créditos financeiros: de pesquisa e desenvolvimento (art. 16), de investimento em ativos fixos e P&D (art. 19) e de importação de equipamento ou de exportação (art. 20). Sem a autorização prévia e o cronograma, o crédito não se forma (art. 15, § 1º).

| Campo | Tipo | Descrição |
|-----------------------|--------------------------------------|--------------------------------------|
| `ID_Mover_Projeto` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação do projeto. |
| `Codigo_Projeto_Mdic` | código (até 40) | O código ou número do projeto no MDIC. |
| `Nome_Projeto` | texto | O nome do projeto. |
| `Tipo_Beneficio` | enumeração {pesquisa_desenvolvimento_art16, investimento_producao_art19, importacao_equipamento_art20, exportacao_art20} | Qual crédito o projeto sustenta. |
| `Categoria_Investimento` | enumeração {veiculos_automotores, autopecas_sistemas_estrategicos}, opcional | Decide o percentual do art. 19: 12,5% dos investimentos em veículos; 25% em autopeças ou sistemas e soluções estratégicas. |
| `Numero_Autorizacao_Previa` | código (até 40) | O número da autorização prévia do projeto (art. 15, § 1º, II; art. 19, § 1º, II, a). |
| `Data_Autorizacao_Previa` | data | A data da autorização. |
| `Data_Inicio_Execucao` | data, opcional | O início da execução. |
| `Data_Fim_Prevista` | data, opcional | O fim previsto no cronograma. |
| `Valor_Investimento_Ativo_Fixo_Previsto` | número, opcional | O investimento em ativos fixos previsto no projeto. |
| `Valor_Dispendio_Pd_Previsto` | número, opcional | O dispêndio em pesquisa e desenvolvimento previsto, inclusive engenharia automotiva. |
| `Situacao_Projeto` | enumeração {proposto, autorizado, em_execucao, concluido, cancelado} | Só `autorizado` e `em_execucao` formam crédito. |
| `ID_Documento_Projeto` | referência (Cad_Documento), opcional | O projeto e a autorização. |

### `Mov_Mover_Projeto_Cronograma` (Contabilidade & Fiscal, sem vigência, 9 campos)

O cronograma físico-financeiro e de produção do projeto (art. 15, § 1º, III; art. 19, § 1º, II, b): o previsto e o realizado por competência. O descumprimento do cronograma é motivo de aviso e de possível suspensão ou cancelamento.

| Campo | Tipo | Descrição |
|---------------------------|---------------------------------------|----------------------------------|
| `ID_Mover_Projeto_Cronograma` | identificador | Chave. |
| `ID_Mover_Projeto` | referência (Cad_Mover_Projeto) | O projeto. |
| `Competencia` | competência | O mês da etapa. |
| `Etapa` | texto, opcional | A etapa física do cronograma. |
| `Valor_Previsto` | número | O valor físico-financeiro previsto. |
| `Valor_Realizado` | número, opcional | O valor realizado. |
| `Producao_Prevista_Unidades` | número, opcional | A produção prevista, em unidades. |
| `Producao_Realizada_Unidades` | número, opcional | A produção realizada. |
| `Situacao_Etapa` | enumeração {no_prazo, atrasada, concluida} | O Motor avisa a etapa atrasada. |

### `Mov_Mover_Credito_Autorizacao_Ano` (Contabilidade & Fiscal, sem vigência, 9 campos)

O valor de crédito financeiro que o MDIC autoriza ao projeto em cada ano-calendário, dentro do teto global da lei (R$ 3,5 bilhões em 2024 a R$ 4,1 bilhões em 2028, art. 15, § 2º); a autorização pode alcançar anos seguintes, nos projetos plurianuais (§ 3º).

| Campo | Tipo | Descrição |
|-------------------------|----------------------------|-----------------------------------------------|
| `ID_Mover_Credito_Autorizacao_Ano` | identificador | Chave. |
| `ID_Mover_Projeto` | referência (Cad_Mover_Projeto) | O projeto. |
| `Ano_Calendario` | número | O ano da autorização. Único por projeto. |
| `Valor_Autorizado` | número | O crédito autorizado no ano. |
| `Valor_Utilizado` | número, calculado | Soma de `Mov_Mover_Credito_Apuracao.Credito_Calculado` do projeto no ano. |
| `Saldo_Autorizado` | número, calculado | `Valor_Autorizado` menos `Valor_Utilizado`. O Motor avisa quando o crédito apurado passa do saldo. |
| `Data_Autorizacao` | data, opcional | A data do ato de autorização. |
| `Numero_Ato_Autorizacao` | código (até 40), opcional | O número do ato. |
| `ID_Documento` | referência (Cad_Documento), opcional | O ato de autorização. |

### `Mov_Mover_Dispendio` (Contabilidade & Fiscal, sem vigência, 16 campos)

Cada dispêndio de pesquisa e desenvolvimento, de engenharia ou de investimento em ativo fixo que a empresa lança no Mover: o valor, a atividade, a forma de execução, a prova e a elegibilidade. É a base do dispêndio mínimo e do crédito financeiro.

| Campo | Tipo | Descrição |
|--------------------|----------------------------------------|----------------------------------------|
| `ID_Mover_Dispendio` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação. |
| `ID_Mover_Projeto` | referência (Cad_Mover_Projeto), opcional | O projeto, quando o dispêndio é de projeto autorizado. |
| `Data_Dispendio` | data | A data do dispêndio. |
| `Competencia` | competência | O mês em que o dispêndio entra na apuração. |
| `Valor_Dispendio` | número | O valor do dispêndio, em reais. |
| `ID_Filial` | referência (Cad_Filial) | O estabelecimento que realizou o dispêndio. A lei exige que seja realizado no País. |
| `ID_Dimensao_Valor_Centro_Custo` | referência (Cad_Dimensao_Contabil_Valor), opcional | O centro de custo de pesquisa e desenvolvimento. |
| `ID_Lancamento` | referência (Mov_Lancamento), opcional | O lançamento contábil do dispêndio. |
| `ID_Tipo_Atividade` | referência (Cad_Classe_Sistema, domínio = tipo_atividade_pd_mover) | Pesquisa básica dirigida, pesquisa aplicada, desenvolvimento experimental, projeto estruturante, engenharia automotiva e ativo fixo de produção. Domínio aberto; a carga de partida usa as definições do Decreto 9.557, arts. 22 e 23 (C273). |
| `Forma_Execucao` | enumeração {direta, fornecedor_contratado, universidade_ict_empresa_especializada, aporte_programa_prioritario, aporte_fndit} | Como o dispêndio foi feito (Decreto 9.557, art. 15, § 1º, II; Lei 14.902, art. 14, § 1º). |
| `ID_Participante_Executor` | referência (Cad_Participante), opcional | O fornecedor, a universidade, a ICT ou a instituição do programa prioritário. |
| `ID_Documento_Comprovacao` | referência (Cad_Documento), opcional | Nota, contrato ou comprovante. |
| `Situacao_Elegibilidade` | enumeração {informado, submetido, aprovado, glosado} | O MDIC ou a auditoria aprova ou glosa. A glosa pode ser complementada por aporte ao FNDIT (art. 14, § 3º). |
| `Valor_Glosado` | número, opcional | A parte glosada. |
| `Motivo_Glosa` | texto, opcional | O motivo da glosa. |

### `Mov_Mover_Dispendio_Minimo_Ano` (Contabilidade & Fiscal, sem vigência, 11 campos)

O dispêndio mínimo do ano: o percentual da receita bruta, o realizado, o resíduo que passa ao ano seguinte, o excesso dos dois anos anteriores e o complemento por aporte (Lei 14.902, art. 16, § 3º; art. 14, § 3º). Só o que passa do mínimo gera crédito financeiro (art. 16, § 4º).

| Campo | Tipo | Descrição |
|--------------------|---------------------------------------|-----------------------------------------|
| `ID_Mover_Dispendio_Minimo_Ano` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação. |
| `Ano_Calendario` | número | O ano. Único por habilitação. |
| `Receita_Bruta_Base` | número | A receita bruta total de venda de bens e serviços do ano, sem os impostos e contribuições sobre a venda. Vem de `Mov_Apuracao_Tributo_Item`. |
| `Percentual_Minimo` | número | 0,6, 0,3 ou 0,3, do parâmetro do `Segmento_Empresa`. |
| `Dispendio_Minimo_Exigido` | número, calculado | `Receita_Bruta_Base` × `Percentual_Minimo` mais o resíduo do ano anterior. |
| `Dispendio_Realizado` | número, calculado | Soma dos dispêndios aprovados do ano (`Mov_Mover_Dispendio`). |
| `Residuo_Ano_Anterior` | número, opcional | O que faltou no ano anterior e se soma ao mínimo deste (art. 16, § 3º, I). |
| `Excesso_Anos_Anteriores_Usado` | número, opcional | O excesso dos dois anos anteriores usado para cumprir o mínimo (art. 16, § 3º, II). |
| `Complemento_Aporte_Fndit` | número, opcional | O complemento do mínimo por aporte ao FNDIT (art. 14, § 3º). |
| `Situacao` | enumeração {a_apurar, cumprido, residual_transferido, descumprido} | O Motor avisa o `descumprido` e o `residual_transferido`. |

### `Mov_Mover_Credito_Apuracao` (Contabilidade & Fiscal, sem vigência, 17 campos)

A apuração mensal do crédito financeiro do Mover, por habilitação e por tipo de crédito: a base de dispêndios, o saldo não utilizado, o limite sobre a receita bruta do segundo mês anterior, o percentual e o crédito calculado. O crédito é crédito de CSLL (art. 17) e nasce em `Mov_Credito_Fiscal` com origem `credito_financeiro_mover`.

| Campo | Tipo | Descrição |
|-----------------------|--------------------------------------|--------------------------------------|
| `ID_Mover_Credito_Apuracao` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação. |
| `ID_Mover_Projeto` | referência (Cad_Mover_Projeto), opcional | O projeto autorizado, quando o crédito é de projeto. |
| `Competencia` | competência | O mês de apuração. |
| `Tipo_Credito` | enumeração {pd_art16, investimento_art19, importacao_equipamento_art20_i, exportacao_art20_ii} | O crédito apurado. Os indicadores do art. 18 acrescem o `pd_art16` e ficam em `Mov_Mover_Credito_Indicador`. |
| `Base_Dispendios_Elegiveis` | número | Os dispêndios aprovados do mês acima do mínimo (art. 16, § 4º) ou o investimento do art. 19. |
| `Saldo_Dispendio_Nao_Utilizado_Anterior` | número | O dispêndio que ficou sem uso por causa do limite e pode ser usado nos meses seguintes (art. 16, § 1º). |
| `Receita_Bruta_Segundo_Mes_Anterior` | número | A receita bruta total de venda de bens e serviços do segundo mês-calendário anterior, sem impostos (art. 16, II). No limite do art. 18, § 4º, é só a receita dos produtos do inciso III. |
| `Percentual_Credito` | número | 50% sobre o dispêndio (art. 16, I) mais os pontos dos indicadores; 12,5% ou 25% no art. 19. |
| `Limite_Percentual_Receita` | número | 5%, ou 7%, 13% ou 16% com os indicadores (arts. 16, II, e 18, §§ 2º, 4º e 5º). |
| `Limite_Valor` | número, calculado | `Receita_Bruta_Segundo_Mes_Anterior` × `Limite_Percentual_Receita`. |
| `Credito_Calculado` | número, calculado | O menor entre `Percentual_Credito` × (`Base_Dispendios_Elegiveis` + `Saldo_Dispendio_Nao_Utilizado_Anterior`) e `Limite_Valor`. A leitura da soma de indicadores é minha (C274). |
| `Limitado_Por` | enumeração {dispendio, limite_receita, autorizacao_anual, nenhum} | O que travou o crédito do mês. O `autorizacao_anual` vem do saldo de `Mov_Mover_Credito_Autorizacao_Ano`. |
| `Saldo_Dispendio_Nao_Utilizado_Final` | número, calculado | O dispêndio que sobra por causa do limite e passa ao mês seguinte. |
| `Ajuste_Periodo_Cumulativo` | número, opcional | O ajuste do cálculo em períodos cumulativos, abatidos os créditos já pedidos para ressarcimento ou compensação (art. 16, § 2º). |
| `ID_Credito_Fiscal` | referência (Mov_Credito_Fiscal), opcional | O crédito financeiro gerado. Origem `credito_financeiro_mover`. |
| `Situacao_Apuracao` | enumeração {calculada, conferida, autorizada_mdic, cancelada} | `autorizada_mdic` quando o MDIC reconheceu o valor. |

### `Mov_Mover_Credito_Indicador` (Contabilidade & Fiscal, sem vigência, 7 campos)

Os pontos percentuais que cada indicador do art. 18 acrescenta ao crédito de pesquisa e desenvolvimento: atividade fabril e de engenharia no País, diversificação de mercados, produção de tecnologias de propulsão avançada, veículos e sistemas eletrônicos embarcados, volume de investimentos. O ERP guarda os pontos que o ato do MDIC fixa e confere os tetos da lei.

| Campo | Tipo | Descrição |
|------------------|-----------------------------------------|-----------------------------------------|
| `ID_Mover_Credito_Indicador` | identificador | Chave. |
| `ID_Mover_Credito_Apuracao` | referência (Mov_Mover_Credito_Apuracao) | A apuração acrescida. |
| `Indicador` | enumeração {atividade_fabril_engenharia, diversificacao_mercados, propulsao_avancada, veiculo_propulsao_avancada_ou_recarga, sistemas_eletronicos_autonomos, volume_investimento} | Os indicadores do art. 18, I, II, III (a, b, c) e § 8º. |
| `Pontos_Percentuais` | número | Os pontos que o indicador soma. Tetos: 20 pontos para os dois primeiros somados (§ 1º); 250 para o inciso III (§ 3º); 20 para o volume de investimento (§ 8º). |
| `Peso_Metodologia` | número, opcional | O peso da metodologia do MDIC que pondera os pontos (§ 1º). |
| `Nivel_Mrl` | número, opcional | O nível de maturidade da manufatura (escala MRL) que pondera o inciso III (§§ 3º e 7º). |
| `ID_Documento_Metodologia` | referência (Cad_Documento), opcional | O ato ou a planilha de metodologia do MDIC. |

### `Mov_Mover_Aporte` (Contabilidade & Fiscal, sem vigência, 13 campos)

Todo aporte ao FNDIT ou a conta de programa prioritário: o dispêndio feito sob a forma de aporte, o complemento de glosa, a contrapartida de 2% das autopeças e as multas pagas por aporte. Gera título a pagar em `Mov_Titulo`.

| Campo | Tipo | Descrição |
|------------------|-----------------------------------------|-----------------------------------------|
| `ID_Mover_Aporte` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa que paga. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao), opcional | A habilitação do Mover, quando o aporte é dela. |
| `ID_Habilitacao_Autopecas` | referência (Cad_Habilitacao_Regime_Especial), opcional | A habilitação do regime de autopeças, quando é o caso. |
| `ID_Autopecas_Contrapartida` | referência (Mov_Autopecas_Contrapartida), opcional | A contrapartida de 2% que o aporte paga. |
| `Origem_Aporte` | enumeração {dispendio_pd_fndit, complemento_glosa, autopecas_contrapartida, multa_importacao_sem_ato, multa_eficiencia_energetica, multa_desempenho_estrutural, multa_autopecas} | Lei 14.902, arts. 14, §§ 1º e 3º, 27 e 28; Decreto 12.435, arts. 5º a 7º. |
| `Destino` | enumeração {fndit, conta_programa_prioritario} | Se o FNDIT não funciona, o aporte vai a conta específica da instituição coordenadora (Lei 14.902, art. 29, § 6º). |
| `Competencia_Referencia` | competência, opcional | O mês a que o aporte se refere (por exemplo, o do desembaraço, nas autopeças). |
| `Data_Aporte` | data, opcional | A data do pagamento. |
| `Valor_Aporte` | número | O valor aportado. |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título a pagar do aporte (valor novo `aporte_mover` em `Origem_Tipo`). |
| `ID_Documento_Comprovante` | referência (Cad_Documento), opcional | O comprovante do aporte. |
| `Situacao_Aporte` | enumeração {previsto, realizado, comprovado, glosado} | `comprovado` quando o MDIC ou a auditoria aceitou. |

### `Mov_Mover_Habilitacao_Ocorrencia` (Contabilidade & Fiscal, sem vigência, 12 campos)

A prorrogação, a suspensão, o cancelamento e o restabelecimento da habilitação, com a consequência de cada um: o cancelamento retroage ao início do ano-calendário do fato e obriga a recolher os créditos ressarcidos ou compensados, ou a estorná-los, até o último dia útil do mês seguinte (Lei 14.902, arts. 23 a 25).

| Campo | Tipo | Descrição |
|---------------------|----------------------------------------|----------------------------------------|
| `ID_Mover_Habilitacao_Ocorrencia` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação. O cancelamento de uma não afeta as outras da mesma empresa (art. 24, § 1º). |
| `Tipo_Ocorrencia` | enumeração {prorrogacao, suspensao, cancelamento, restabelecimento} | O que aconteceu. |
| `Motivo_Legal` | enumeração {descumprimento_requisitos_art14, nao_realizacao_projeto, condicao_art13_1_iii, obrigacao_acessoria_3_meses, outro}, opcional | Os motivos dos arts. 24 e 25. |
| `Data_Ocorrencia` | data | A data do ato. |
| `Retroage_Desde` | data, opcional | O início do ano-calendário em que ocorreu o fato que causou o cancelamento (art. 24, § 2º). |
| `Valor_A_Recolher` | número, opcional | O valor dos créditos ressarcidos ou compensados que se recolhe, ou dos créditos formados que se estornam (art. 24, II). Cálculo do ERP: soma de `Mov_Mover_Credito_Apuracao.Credito_Calculado` desde `Retroage_Desde`. |
| `Prazo_Recolhimento` | data, opcional | O último dia útil do mês seguinte ao cancelamento. |
| `Tratamento_Credito` | enumeração {nao_se_aplica, recolher, estornar} | Recolher o que já foi ressarcido ou compensado; estornar o que ainda é saldo. |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título do recolhimento (valor novo `recolhimento_mover` em `Origem_Tipo`). |
| `ID_Documento_Ato` | referência (Cad_Documento), opcional | O ato do MDIC. |
| `Situacao_Recolhimento` | enumeração {nao_se_aplica, a_recolher, recolhido, estornado} | O Motor avisa o prazo. |

## 5.4 Grupo 3: Regime de autopeças não produzidas

### `Mov_Autopecas_Importacao_Item` (Contabilidade & Fiscal, sem vigência, 14 campos)

O item importado no regime de autopeças não produzidas (isenção do Imposto de Importação das partes, peças, componentes, conjuntos, subconjuntos e pneumáticos sem produção nacional equivalente: Lei 14.902, art. 26; Decreto 9.557, art. 34). Liga o item do Duimp à habilitação, à contrapartida de 2% e ao prazo de três anos para aplicar o bem na industrialização.

| Campo | Tipo | Descrição |
|--------------------------|----------------------------------|-----------------------------------------|
| `ID_Autopecas_Importacao_Item` | identificador | Chave. |
| `ID_Duimp_Item` | referência (Mov_Duimp_Item) | O item da declaração de importação. |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) | A habilitação de tipo `autopecas_nao_produzidas` (valor novo em `tipo_regime_especial_federal`). |
| `Modalidade_Importacao` | enumeração {direta, por_encomenda, por_conta_e_ordem} | A importação pode ser direta, por encomenda ou por conta e ordem, com o mesmo tratamento tributário (Lei 14.902, art. 26, § 6º). |
| `ID_Participante_Encomendante_Adquirente` | referência (Cad_Participante), opcional | Na encomenda e na conta e ordem, a empresa habilitada que encomenda ou adquire, sobre quem recai a contrapartida (art. 26, § 7º). |
| `Valor_Aduaneiro` | número | O valor aduaneiro do item, base da contrapartida de 2%. |
| `Valor_Ii_Isentado` | número | O Imposto de Importação que seria devido sem a isenção (`Mov_Duimp_Item_Tributo`). |
| `Data_Fato_Gerador_Ii` | data | A data de desembaraço (fato gerador do II). |
| `Data_Limite_Industrializacao` | data, calculada | `Data_Fato_Gerador_Ii` mais 3 anos (Decreto 9.557, art. 37). |
| `Quantidade_Importada` | número | A quantidade do item. |
| `Quantidade_Aplicada` | número, opcional | A quantidade já aplicada na industrialização de produtos automotivos. |
| `Percentual_Perda_Inevitavel` | número, opcional | A perda inevitável do processo, declarada na EFD e tolerada (Decreto 9.557, art. 37, § 2º). |
| `ID_Autopecas_Contrapartida` | referência (Mov_Autopecas_Contrapartida), opcional | A contrapartida do mês do desembaraço. |
| `Situacao_Aplicacao` | enumeração {a_aplicar, aplicada, vencida_sem_aplicacao} | `vencida_sem_aplicacao`: o II isentado passa a ser devido com juros e multa de mora desde o fato gerador (Decreto 9.557, art. 37, § 1º). |

### `Mov_Autopecas_Contrapartida` (Contabilidade & Fiscal, sem vigência, 14 campos)

A contrapartida de 2% do valor aduaneiro em pesquisa, desenvolvimento e inovação e programas prioritários, por habilitação e mês de desembaraço, com o prazo (último dia útil do segundo mês seguinte), a multa sancionatória e a multa de mora (Lei 14.902, arts. 27 e 28; Decreto 9.557, art. 36, § 3º).

| Campo | Tipo | Descrição |
|--------------------|----------------------------------------|----------------------------------------|
| `ID_Autopecas_Contrapartida` | identificador | Chave. |
| `ID_Habilitacao` | referência (Cad_Habilitacao_Regime_Especial) | A habilitação. |
| `Competencia_Desembaraco` | competência | O mês dos desembaraços cobertos. Único por habilitação. |
| `Valor_Aduaneiro_Total` | número, calculado | Soma de `Mov_Autopecas_Importacao_Item.Valor_Aduaneiro` do mês. |
| `Percentual_Contrapartida` | número | 2, do parâmetro `autopecas_contrapartida`. |
| `Valor_Obrigacao` | número, calculado | `Valor_Aduaneiro_Total` × `Percentual_Contrapartida`. |
| `Data_Limite_Aporte` | data, calculada | O último dia útil do segundo mês-calendário posterior ao mês do desembaraço (Decreto 9.557, art. 36, § 3º). |
| `Valor_Aportado` | número, calculado | Soma dos `Mov_Mover_Aporte` ligados à contrapartida. |
| `Diferenca_A_Menor` | número, calculado | `Valor_Obrigacao` menos `Valor_Aportado`, quando positivo. |
| `Percentual_Multa_Sancionatoria` | número | 30, do parâmetro `autopecas_multa_sancionatoria`. O Decreto 9.557, art. 38, § 3º, diz 100%; a lei posterior fixou 30% (C275). |
| `Valor_Multa_Sancionatoria` | número, calculado | `Diferenca_A_Menor` × `Percentual_Multa_Sancionatoria`. |
| `Data_Termo_Inicio_Fiscalizacao` | data, opcional | O recebimento do termo de início de fiscalização: nos 20 dias seguintes a multa cai pela metade se o devido é pago (art. 28, § 3º). |
| `Multa_Mora_Calculada` | número, opcional | 0,33% por dia de atraso, limitada a 20%, desde o primeiro dia útil depois do prazo (art. 28, §§ 5º e 6º). |
| `Situacao` | enumeração {a_aportar, cumprida, aporte_a_menor, pago_espontaneamente, em_fiscalizacao} | O Motor avisa o prazo e o aporte a menor. |

## 5.5 Grupo 4: Obrigações acessórias e legado do Rota 2030

### `Mov_Mover_Obrigacao_Acessoria` (Contabilidade & Fiscal, sem vigência, 13 campos)

As obrigações de prestar informação ao MDIC que a lei e o decreto criam: relatório de acompanhamento do ato, comprovação anual da habilitação e dos dispêndios, inventário e pegada de carbono, comprovação do aporte das autopeças. A obrigação descumprida por mais de três meses seguidos pode suspender a habilitação (Lei 14.902, art. 25, II; Decreto 9.557, art. 27, II).

| Campo | Tipo | Descrição |
|-------------------|----------------------------------------|----------------------------------------|
| `ID_Mover_Obrigacao_Acessoria` | identificador | Chave. |
| `ID_Empresa` | referência (Cad_Empresa) | A empresa obrigada. |
| `ID_Mover_Ato_Registro` | referência (Cad_Mover_Ato_Registro), opcional | O ato de registro, nas obrigações dele. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao), opcional | A habilitação do Mover. |
| `ID_Habilitacao_Autopecas` | referência (Cad_Habilitacao_Regime_Especial), opcional | A habilitação das autopeças. |
| `Tipo_Obrigacao` | enumeração {relatorio_acompanhamento_requisitos, comprovacao_anual_habilitacao, comprovacao_dispendios_pd, comprovacao_aporte_autopecas, inventario_carbono, pegada_carbono, informacao_importador_autorizado, registro_mensal_beneficio_rota_2030} | Decreto 12.435, arts. 2º, §§ 2º, V, e 3º, e 7º, II; Lei 14.902, arts. 13, § 2º, 14, § 4º, e 28; Decreto 9.557, art. 30, § 1º. |
| `Competencia_Referencia` | competência, opcional | O mês ou o ano a que a obrigação se refere. |
| `Data_Limite` | data, opcional | O prazo. O ato do MDIC fixa os prazos e modelos; sem o ato, o campo fica vazio e o Motor não avisa vencimento. |
| `Data_Entrega` | data, opcional | Quando foi entregue. |
| `Numero_Protocolo` | código (até 40), opcional | O protocolo do MDIC ou do Siscomex. |
| `ID_Documento` | referência (Cad_Documento), opcional | O relatório entregue. |
| `Situacao` | enumeração {a_entregar, entregue, em_atraso} | `em_atraso` quando passou a `Data_Limite` sem entrega. |
| `Meses_Consecutivos_Atraso` | número, calculado | Contagem para o aviso de suspensão: mais de três meses seguidos (Lei 14.902, art. 25, II). |

### `Mov_Rota_2030_Deducao` (Contabilidade & Fiscal, sem vigência, 13 campos)

A dedução do IRPJ e da CSLL devidos da empresa habilitada ao Rota 2030: 30% dos dispêndios de pesquisa e desenvolvimento, mais até 15% sobre os estratégicos (limite de 45%), com o excedente levado aos períodos seguintes (Decreto 9.557, art. 19). A habilitação cessou em 30/11/2023; o legado fica para o excedente e os direitos adquiridos (C276).

| Campo | Tipo | Descrição |
|---------------------|----------------------------------|---------------------------------------------|
| `ID_Rota_2030_Deducao` | identificador | Chave. |
| `ID_Mover_Habilitacao` | referência (Cad_Mover_Habilitacao) | A habilitação com `Programa` = `rota_2030`. |
| `ID_Apuracao_Irpj` | referência (Mov_Apuracao_Irpj_Csll) | A apuração do IRPJ e da CSLL em que a dedução entra. |
| `ID_Imposto` | referência (Cad_Imposto, Fase 0) | IRPJ ou CSLL. |
| `Dispendio_Base_Deducao` | número | Os dispêndios do período, no País, classificáveis como despesa operacional, até o limite da base. |
| `Dispendio_Estrategico` | número, opcional | Os dispêndios estratégicos do art. 24. |
| `Deducao_Basica_Calculada` | número, calculado | Alíquota e adicional do IRPJ (ou alíquota da CSLL) × 30% × `Dispendio_Base_Deducao`. |
| `Deducao_Adicional_Calculada` | número, calculado | Alíquota × até 15% × `Dispendio_Estrategico`, limitada a 45% da base do caput. |
| `Limite_Imposto_Devido` | número, calculado | O imposto devido do período: a dedução não passa dele (art. 19, § 1º). |
| `Deducao_Utilizada` | número, calculado | O menor entre a dedução calculada mais o excedente anterior usado e o limite. |
| `Excedente_Anterior_Utilizado` | número, opcional | O excedente de períodos anteriores, usado até 30% do tributo (art. 19, § 3º). |
| `Excedente_A_Carregar` | número, calculado | O que passou do limite e segue para os períodos seguintes. |
| `ID_Apuracao_Item` | referência (Mov_Apuracao_Irpj_Csll_Item), opcional | A linha da apuração cujo `Valor_Deducoes` recebe a dedução. |



## 5.6 O que muda em entidades que já existem

**Um campo novo:**

| Entidade | Campo | Tipo | Para quê |
|--------------------------|--------------|-------------------------|------------------------------------|
| `Cad_Veiculo_Versao_Sustentavel` (documento 204) | `ID_Mover_Ato_Registro` | referência (Cad_Mover_Ato_Registro), opcional | O registro de versão sustentável exige o ato de compromissos (Decreto 12.549, art. 4º, II). O número que o 204 já guarda continua. |

**Valores, textos e carga** (sem campo novo):

| Entidade | Mudança |
|--------------------------------------------------|--------------------------------------------------|
| `Mov_Credito_Fiscal.Origem` | Um valor novo, **`credito_financeiro_mover`**: crédito de CSLL (Lei 14.902, art. 17), no mesmo ciclo de estados dos demais; compensação ou ressarcimento pelo `Mov_Perdcomp`. Sem prazo de utilização na lei. |
| `Mov_Titulo.Origem_Tipo` | Dois valores novos: **`aporte_mover`** (aportes ao FNDIT) e **`recolhimento_mover`** (recolhimento do cancelamento da habilitação). |
| `Cad_Habilitacao_Regime_Especial.Numero_Habilitacao` | **Só texto:** nos tipos `mover` e `autopecas_nao_produzidas`, o número é o do ato do MDIC (ato do Secretário; habilitação no Siscomex). |
| `Cad_Classe_Sistema` | **Só carga:** 2 valores em `tipo_regime_especial_federal`, 2 em `tipo_lista_legal` e o domínio novo `tipo_atividade_pd_mover` (6 valores). |
| `Cad_Lista_Legal_Item` | **Só carga:** 80 linhas do Anexo I do Decreto 12.435 (tipo `mover_requisitos_anexo_i`). |
| `Cad_Obrigacao_Acessoria` | **Só carga:** 4 linhas (`MDIC_MOVER`, `MDIC_AUTOPECAS`, `PERDCOMP`, `DUIMP`). |
| `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao` (documento 201) | **Só carga:** 28 e 28 linhas do B8 (Anexos A e B), pela regra da Q201-3. |
| `Mov_Duimp`, `Mov_Duimp_Item_Tributo`, `Mov_Perdcomp`, `Mov_Apuracao_Irpj_Csll_Item`, `Mov_Nota_Fiscal_Saida_Item` | **Nenhum campo novo:** o B8 só lê e liga. |

## 5.7 Como o ERP calcula

**Crédito de pesquisa e desenvolvimento (art. 16).** Para cada mês, por habilitação: `Crédito = menor de [ percentual × (dispêndios elegíveis do mês + saldo não utilizado) ] e [ limite % × receita bruta do segundo mês anterior ]`. O percentual é 50%, mais os pontos dos indicadores. O limite é 5%, ou 7%, 13% ou 16% com os indicadores. O dispêndio que sobra por causa do limite passa ao mês seguinte (art. 16, § 1º). Os dispêndios elegíveis são os aprovados do ano **acima do mínimo** (0,6%, 0,3% ou 0,3% da receita bruta do ano). Depois do cálculo, o Motor confere o saldo autorizado do ano ao projeto; se o crédito passa dele, avisa e marca `Limitado_Por` = `autorizacao_anual`.

**Crédito de investimento (art. 19).** Base de investimento do projeto × 12,5% (veículos) ou 25% (autopeças e sistemas estratégicos), sujeito à autorização prévia, ao cronograma e aos indicadores fabril e de mercado; os limites do art. 15 valem. O crédito do art. 20 (II de equipamento importado; IRPJ e CSLL sobre o lucro da exportação) entra como valor informado, porque a lei não traz a fórmula.

**Uso do crédito (art. 17).** O crédito nasce em `Mov_Credito_Fiscal` com origem `credito_financeiro_mover`; a empresa compensa por `Mov_Perdcomp` ou pede ressarcimento em dinheiro; se não compensou, a Receita ressarce no 48º mês a contar do pedido. O valor entra no resultado operacional (art. 17, § 1º); o tratamento na ECF é a C277.

**Cancelamento da habilitação (art. 24).** O valor a recolher é a soma dos créditos já ressarcidos ou compensados desde o início do ano-calendário do fato; o prazo é o último dia útil do mês seguinte; o que ainda é saldo é estornado. O cancelamento de uma habilitação não afeta as outras da empresa.

**Importação sem ato (Decreto 12.435, art. 7º).** `Base = (valor aduaneiro + tributos da nacionalização) × 1,20`; `Multa = Base × 20%`. O comprovante do aporte ao FNDIT é condição para a nacionalização; a informação ao importador autorizado vem antes da homologação do veículo.

**Autopeças (Lei 14.902, arts. 27 e 28; Decreto 9.557, arts. 36 e 37).** Contrapartida do mês = soma do valor aduaneiro dos desembaraços × 2%, até o último dia útil do segundo mês seguinte. Aporte a menor: multa de 30% sobre a diferença; pagamento espontâneo até o segundo mês seguinte ao aporte a menor dispensa a multa (art. 28, § 2º); depois do termo de fiscalização, 20 dias para pagar com a multa pela metade (§ 3º). Multa de mora de 0,33% por dia, até 20%, e juros pela Selic. O bem importado deve ser aplicado em três anos do fato gerador; a perda inevitável declarada na EFD é tolerada.

## 5.8 Ligações com os outros blocos

- **B6 (documento 202).** O regime automotivo da LC 214 (crédito presumido da CBS) e o Mover são regimes diferentes, com habilitações diferentes; a mesma empresa pode ter os dois. O art. 21 da Lei 14.902 diz quais benefícios não se acumulam (os da Lei 13.755 e do Decreto-Lei 288); o ERP só avisa quando a empresa tem os dois cadastrados.
- **Documento 204.** A versão sustentável exige o ato de registro; o campo novo do 5.6 faz a ligação. Os requisitos de reciclabilidade e desempenho estrutural do 204 (`Nivel_Reciclabilidade`, `Atende_Desempenho_Estrutural`) são o cumprimento por veículo do que o ato exige da empresa.
- **Duimp.** A multa sem ato e a isenção do II ligam-se a `Mov_Duimp` e `Mov_Duimp_Item`; o II isentado vem de `Mov_Duimp_Item_Tributo`.
- **IPI (documento 207, a preparar).** As Notas Complementares 87-7 a 87-12 (reduções do Rota 2030 até 31/12/2026) entram na tabela de IPI da Q205-4, não aqui.

## 5.9 Documentação dos parâmetros (regra do documento 201)

As 34 linhas de `Cad_Mover_Parametro` têm 28 códigos; cada código tem documentação (Anexo A) e efeito por obrigação (Anexo B), como a Q201-3 manda. As obrigações são cinco: `MDIC_MOVER`, `MDIC_AUTOPECAS`, `PERDCOMP` e `DUIMP` (novas no catálogo) e `ECF` (existente). O MDIC não tem leiaute oficial nem arquivo de entrega que o ERP gere; o "local do efeito" é a entidade do ERP que calcula e a comprovação que a empresa faz ao MDIC. **Nenhum parâmetro por empresa** é novo: não há escolha da empresa que a lei deixe em aberto (as leituras minhas estão nas C269 a C277).

# 6. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|------|----------------------------------------------|------------------------------------------------|
| 1 | Veículo do Anexo I vendido ou importado sem ato de registro vigente | A nota de saída ou o Duimp tem NCM da lista e o ato não está `vigente` na data |
| 2 | Importação sem ato sem comprovante da multa | O Duimp aproxima-se da nacionalização e `Mov_Mover_Importacao_Sem_Ato.Situacao` é `a_pagar` |
| 3 | Importador autorizado sem informação | Falta `Data_Informacao_Importador_Autorizado` antes da homologação |
| 4 | Requisito de reciclabilidade ou rotulagem não cumprido | O ato fica sujeito a cancelamento (art. 4º) |
| 5 | Meta de eficiência ou de desempenho não cumprida, multa sem aporte | `Sancao_Prevista` é `multa_compensatoria` e não há `ID_Mover_Aporte` |
| 6 | Inventário e pegada de carbono | Inventário vence em 31/12/2026; a pegada vale desde 01/01/2027 |
| 7 | Habilitação sem pré-requisito | Falta centro de custo de P&D, lucro real ou regularidade federal |
| 8 | Dispêndio sem prova ou glosado | `Situacao_Elegibilidade` em `informado` sem documento ou `glosado`; o complemento por aporte é possível |
| 9 | Dispêndio mínimo do ano | `Situacao` do mínimo em `descumprido` ou `residual_transferido` |
| 10 | Crédito do mês limitado | `Limitado_Por` é `limite_receita` ou `autorizacao_anual` |
| 11 | Pontos de indicador acima do teto | 20, 250 ou 20 pontos |
| 12 | Etapa do projeto atrasada | `Situacao_Etapa` = `atrasada` |
| 13 | Obrigação acessória atrasada | Atraso por mais de três meses seguidos: risco de suspensão |
| 14 | Habilitação suspensa ou cancelada | Suspensa: uso do crédito pede confirmação; cancelada: recolher ou estornar até o último dia útil do mês seguinte |
| 15 | Fim da vigência dos incentivos | Cinco anos (art. 31); a habilitação cessa (art. 13, § 6º) |
| 16 | Ressarcimento do 48º mês | Aviso da data do ressarcimento no pedido |
| 17 | Autopeça: contrapartida a vencer, vencida ou a menor | Pelo prazo e pela diferença |
| 18 | Autopeça: três anos sem aplicação | Aviso 90 dias antes e no vencimento |
| 19 | Autopeça fora da lista | O NCM do item não está em `autopecas_nao_produzidas` |
| 20 | Rota 2030: excedente de dedução a carregar | `Excedente_A_Carregar` maior que zero |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|--------|-----------------------------------------------------|---------------------------------------|
| Q206-1 | Aprova o **grupo 1** (ato de registro, requisitos por ano e importação sem ato: 3 entidades) como no 5.2? | Sim |
| Q206-2 | Aprova o **grupo 2** (habilitação, projeto, cronograma, autorização anual, dispêndio, mínimo, crédito, indicador, aporte e ocorrência: 10 entidades) e as regras do 5.7? | Sim |
| Q206-3 | Aprova o **grupo 3** (item importado e contrapartida das autopeças: 2 entidades; a lista de autopeças entra na lista legal)? | Sim |
| Q206-4 | Aprova o **grupo 4** (`Mov_Mover_Obrigacao_Acessoria` e o legado `Mov_Rota_2030_Deducao`) e as 4 obrigações novas no catálogo (`MDIC_MOVER`, `MDIC_AUTOPECAS`, `PERDCOMP`, `DUIMP`)? | Sim |
| Q206-5 | Mantém o legado do **Rota 2030** (habilitação `rota_2030` e dedução do IRPJ e da CSLL com excedente), mesmo com a habilitação extinta em 2023? | Sim: o excedente pode ainda estar em uso (C276) |
| Q206-6 | O ERP só **registra** a multa compensatória de eficiência energética e de desempenho estrutural (valor do MDIC), sem recalcular as faixas por centésimo e por grama? | Sim: D-N284 e C270 |
| Q206-7 | Usa **30%** na multa das autopeças (lei) e não 100% (Decreto 9.557)? | Sim: a lei é posterior (C275) |
| Q206-8 | Aceita a **leitura provisória** do crédito: o 50% soma os pontos dos indicadores, o limite de receita substitui o de 5% e o dispêndio mínimo sai dos primeiros dispêndios do ano? | Sim, provisória até a C274 |
| Q206-9 | Aceita a **base da multa de importação sem ato**: (valor aduaneiro + tributos) × 1,20 × 20%? | Sim, provisória até a C271 |
| Q206-10 | Envia a **lista vigente de autopeças não produzidas** (ato da Camex, por NCM)? Sem ela, o tipo de lista fica criado e sem carga. | Enviar |
| Q206-11 | **Não modela** a aba Pontuação do modelo (14 perguntas, 25 pontos, fórmulas quebradas) até saber a que processo serve? Se você souber, diga. | Sim: não modelar |
| Q206-12 | Aprova o campo novo `ID_Mover_Ato_Registro` em `Cad_Veiculo_Versao_Sustentavel` (documento 204) e os 3 valores novos de enumeração do 5.6? | Sim |

# 8. O que acontece se você aprovar

- **Tudo (Q206-1 a Q206-12):** 18 entidades novas, 247 campos (246 nas entidades novas e 1 no 204), 58 campos de referência, 1 domínio novo. Sobre a revisão 38, só o 206: 1.183 entidades e 13.451 campos. **Com 202, 204, 205 e 206:** 1.197 entidades, **13.715 campos**, 3.544 campos de referência e 358 domínios. São somas minhas, a conferir no "consolidar". Nada é aplicado antes.
- **Carga:** 34 linhas de parâmetros, 80 do Anexo I, 10 valores de domínio, 4 obrigações, 28 documentações e 28 efeitos (pasta `Carga206`).
- **Ao contador:** nove perguntas novas, C269 a C277 (documento 188, Parte 14).
- **Se a Q206-4 vier "não" para o legado:** saem `Mov_Rota_2030_Deducao` (13 campos) e o valor `rota_2030` de `Programa`; o resto não muda.

# 9. Limites

- **Não li:** as portarias do Mover (o ato do MDIC do art. 14 sobre dispêndios mínimos e comprovação, o ato dos indicadores e da metodologia do art. 18, o ato do art. 13, § 7º), as 17 portarias do Rota 2030 listadas na página do MDIC, os Anexos II a IV do Decreto 12.435 (metas) e os Anexos VI, IX, X e XI do Decreto 9.557 por inteiro, a Lei 13.755/2018 e o art. 35 da Lei 14.902 (que trata do fim das habilitações).
- **Os valores das metas** (consumo, CO₂, reciclabilidade, desempenho estrutural) não entram no desenho: o campo `Meta_Valor` guarda o número que o MDIC informar.
- **As leituras minhas** estão nas C269 a C277: a base da multa de importação, o acúmulo dos indicadores, o desconto do mínimo, a compensação dos tributos e o tratamento contábil do crédito.
- **O formulário** que você enviou é de 2018 e não vale para o ato atual (art. 2º do Decreto 12.435 pede outros documentos); o ERP guarda o pacote de documentos, não o formulário.
- **O dicionário** não tem entidade de **FNDIT** nem de programa prioritário: o aporte é registrado, mas a conta do fundo está fora do ERP.

# Anexo A. Documentação dos parâmetros do B8 (34 linhas, 28 códigos)

| Parâmetro | Segmento ou ano | Valor | O que é | Fundamento |
|--------------------|--------------|-----------|------------------------------|-------------------------|
| `credito_pd_percentual` | --- | 50 % | Crédito financeiro sobre os dispêndios de pesquisa e desenvolvimento. | Lei 14.902, art. 16, I |
| `credito_pd_limite_receita` | --- | 5 % | Limite do crédito sobre a receita bruta do segundo mês anterior. | Lei 14.902, art. 16, II |
| `credito_ind_pontos_max_fabril_mercado` | --- | 20 pontos | Teto da soma dos indicadores de atividade fabril e de diversificação de mercados. | Lei 14.902, art. 18, § 1º |
| `credito_ind_limite_receita_fabril_mercado` | --- | 7 % | Limite do crédito com os indicadores fabril e de mercado. | Lei 14.902, art. 18, § 2º |
| `credito_ind_pontos_max_tecnologia` | --- | 250 pontos | Teto dos pontos do indicador de produção de tecnologia avançada. | Lei 14.902, art. 18, § 3º |
| `credito_ind_limite_receita_tecnologia` | --- | 13 % | Limite do crédito com o indicador de tecnologia, sobre a receita dos produtos do inciso III. | Lei 14.902, art. 18, § 4º |
| `credito_ind_limite_receita_marca_propria` | --- | 16 % | Limite quando a empresa desenvolve e gere no País tecnologia e marca própria. | Lei 14.902, art. 18, § 5º |
| `credito_ind_pontos_max_investimento` | --- | 20 pontos | Teto do acréscimo pelo volume de investimentos no País. | Lei 14.902, art. 18, § 8º |
| `credito_art19_veiculos` | --- | 12,5 % | Crédito sobre os investimentos em ativos fixos e P&D para produzir veículos. | Lei 14.902, art. 19, § 1º, I, a |
| `credito_art19_autopecas` | --- | 25 % | Crédito sobre os investimentos para autopeças ou sistemas e soluções estratégicas. | Lei 14.902, art. 19, § 1º, I, b |
| `dispendio_minimo_percentual` | automoveis comerciais leves | 0,6 % | Dispêndio que não gera crédito: automóveis e comerciais leves, sobre a receita bruta. | Lei 14.902, art. 16, § 4º, I |
| `dispendio_minimo_percentual` | caminhoes onibus | 0,3 % | Dispêndio que não gera crédito: caminhões e ônibus. | Lei 14.902, art. 16, § 4º, II |
| `dispendio_minimo_percentual` | autopecas sistemas | 0,3 % | Dispêndio que não gera crédito: autopeças e sistemas automotivos. | Lei 14.902, art. 16, § 4º, III |
| `credito_teto_global_ano` | 2024 | 3.500.000.000 reais | Teto global de crédito financeiro do ano, para todo o País. | Lei 14.902, art. 15, § 2º, I |
| `credito_teto_global_ano` | 2025 | 3.800.000.000 reais | Teto global de 2025. | Lei 14.902, art. 15, § 2º, II |
| `credito_teto_global_ano` | 2026 | 3.900.000.000 reais | Teto global de 2026. | Lei 14.902, art. 15, § 2º, III |
| `credito_teto_global_ano` | 2027 | 4.000.000.000 reais | Teto global de 2027. | Lei 14.902, art. 15, § 2º, IV |
| `credito_teto_global_ano` | 2028 | 4.100.000.000 reais | Teto global de 2028. | Lei 14.902, art. 15, § 2º, V |
| `credito_ressarcimento_meses` | --- | 48 meses | Prazo para a Receita ressarcir em dinheiro o crédito não compensado, a contar do pedido. | Lei 14.902, art. 17, § 3º |
| `incentivo_vigencia_anos` | --- | 5 anos | Vigência dos incentivos dos arts. 15 a 20 da lei. | Lei 14.902, art. 31 |
| `suspensao_meses_obrigacao_acessoria` | --- | 3 meses | Meses seguidos de obrigação acessória em atraso que permitem suspender a habilitação. | Lei 14.902, art. 25, II |
| `importacao_sem_ato_multa` | --- | 20 % | Multa compensatória da importação de veículo sem ato de registro. | Decreto 12.435, art. 7º, I |
| `importacao_sem_ato_margem` | --- | 20 % | Margem de comercialização somada à base da multa. | Decreto 12.435, art. 7º, I e § 3º |
| `autopecas_contrapartida` | --- | 2 % | Contrapartida sobre o valor aduaneiro em pesquisa, desenvolvimento e inovação. | Lei 14.902, art. 27 |
| `autopecas_prazo_aporte_meses` | --- | 2 meses | Prazo do aporte: último dia útil do segundo mês depois do desembaraço. | Decreto 9.557, art. 36, § 3º; Lei 14.902, art. 28, § 2º |
| `autopecas_multa_sancionatoria` | --- | 30 % | Multa sobre a diferença entre o aporte devido e o realizado. | Lei 14.902, art. 28, § 1º |
| `autopecas_multa_reducao_fiscalizacao` | --- | 50 % | Redução da multa se o devido é pago em 20 dias do termo de fiscalização. | Lei 14.902, art. 28, § 3º |
| `autopecas_multa_mora_dia` | --- | 0,33 % | Multa de mora por dia de atraso do aporte. | Lei 14.902, art. 28, § 5º |
| `autopecas_multa_mora_limite` | --- | 20 % | Limite da multa de mora. | Lei 14.902, art. 28, § 5º |
| `autopecas_prazo_industrializacao_anos` | --- | 3 anos | Prazo para aplicar o bem importado com isenção na industrialização. | Decreto 9.557, art. 37 |
| `rota_deducao_percentual_dispendio` | --- | 30 % | Parte dos dispêndios de P&D sobre a qual se aplicam alíquota e adicional do IRPJ e alíquota da CSLL. | Decreto 9.557, art. 19 |
| `rota_deducao_adicional_estrategico` | --- | 15 % | Dedução adicional sobre os dispêndios estratégicos. | Decreto 9.557, art. 19, § 4º |
| `rota_deducao_limite_estrategico` | --- | 45 % | Limite da dedução adicional sobre os dispêndios do caput. | Decreto 9.557, art. 19, § 4º |
| `rota_deducao_limite_excedente` | --- | 30 % | Limite de uso do excedente nos períodos seguintes, sobre o valor do tributo. | Decreto 9.557, art. 19, § 3º |


# Anexo B. Os 28 efeitos por obrigação

| Parâmetro | Obrigação | Tipo | Local | O que muda |
|--------------------|--------|----------|-------------------------------|-------------------------------|
| `credito_pd_percentual` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Multiplica a base de dispêndios elegíveis do mês; é a conta do crédito `pd_art16`. |
| `credito_pd_limite_receita` | `MDIC_MOVER` | condiciona_credito | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Trava o crédito do mês; o que passa do limite fica como saldo de dispêndio. |
| `credito_ind_pontos_max_fabril_mercado` | `MDIC_MOVER` | gera_aviso | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Confere os pontos em `Mov_Mover_Credito_Indicador`; aviso se passam. |
| `credito_ind_limite_receita_fabril_mercado` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Troca o limite de 5% pelo de 7% na apuração. |
| `credito_ind_pontos_max_tecnologia` | `MDIC_MOVER` | gera_aviso | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Confere os pontos do inciso III; aviso se passam. |
| `credito_ind_limite_receita_tecnologia` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Troca o limite na apuração do inciso III. |
| `credito_ind_limite_receita_marca_propria` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Vale no lugar de 13% se `Marca_Propria_Tecnologia_Global` é verdadeiro. |
| `credito_ind_pontos_max_investimento` | `MDIC_MOVER` | gera_aviso | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Confere os pontos do indicador de volume de investimento. |
| `credito_art19_veiculos` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Multiplica o investimento do projeto com `Categoria_Investimento` = `veiculos_automotores`. |
| `credito_art19_autopecas` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Multiplica o investimento do projeto com `Categoria_Investimento` = `autopecas_sistemas_estrategicos`. |
| `dispendio_minimo_percentual` | `MDIC_MOVER` | calcula_valor | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Calcula o mínimo do ano e tira a parcela do mínimo da base do crédito. |
| `credito_teto_global_ano` | `MDIC_MOVER` | gera_aviso | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Só informativo: o ERP não controla o teto global; o saldo que vale é o da autorização do projeto. |
| `credito_ressarcimento_meses` | `PERDCOMP` | gera_aviso | pedido de utilização do crédito (`Mov_Perdcomp`) | Gera o aviso da data do ressarcimento no pedido de utilização do crédito. |
| `incentivo_vigencia_anos` | `MDIC_MOVER` | define_vigencia | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Limita a data final de apuração do crédito; depois dela a habilitação cessa (art. 13, § 6º). |
| `suspensao_meses_obrigacao_acessoria` | `MDIC_MOVER` | gera_aviso | apuração do crédito (`Mov_Mover_Credito_Apuracao`) e comprovação ao MDIC (a obrigação não tem leiaute oficial no catálogo) | Dispara o aviso de risco de suspensão em `Mov_Mover_Obrigacao_Acessoria`. |
| `importacao_sem_ato_multa` | `DUIMP` | calcula_valor | item do Duimp (`Mov_Duimp_Item`) | Multiplica a base da multa em `Mov_Mover_Importacao_Sem_Ato`. |
| `importacao_sem_ato_margem` | `DUIMP` | calcula_valor | item do Duimp (`Mov_Duimp_Item`) | Compõe a base da multa. |
| `autopecas_contrapartida` | `MDIC_AUTOPECAS` | calcula_valor | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Multiplica o valor aduaneiro do mês em `Mov_Autopecas_Contrapartida`. |
| `autopecas_prazo_aporte_meses` | `MDIC_AUTOPECAS` | define_vigencia | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Calcula `Data_Limite_Aporte`. |
| `autopecas_multa_sancionatoria` | `MDIC_AUTOPECAS` | calcula_valor | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Multiplica a diferença a menor (C275: o Decreto 9.557 dizia 100%). |
| `autopecas_multa_reducao_fiscalizacao` | `MDIC_AUTOPECAS` | calcula_valor | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Calcula a multa reduzida na janela de 20 dias. |
| `autopecas_multa_mora_dia` | `MDIC_AUTOPECAS` | calcula_valor | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Multiplica os dias de atraso, até o limite. |
| `autopecas_multa_mora_limite` | `MDIC_AUTOPECAS` | condiciona_credito | contrapartida do mês (`Mov_Autopecas_Contrapartida`) e comprovação ao MDIC | Trava a multa de mora. |
| `autopecas_prazo_industrializacao_anos` | `DUIMP` | define_vigencia | item do Duimp (`Mov_Duimp_Item`) | Calcula `Data_Limite_Industrializacao`. |
| `rota_deducao_percentual_dispendio` | `ECF` | calcula_valor | dedução do IRPJ e da CSLL devidos (`Mov_Apuracao_Irpj_Csll_Item.Valor_Deducoes`) | Calcula a dedução básica do legado Rota 2030. |
| `rota_deducao_adicional_estrategico` | `ECF` | calcula_valor | dedução do IRPJ e da CSLL devidos (`Mov_Apuracao_Irpj_Csll_Item.Valor_Deducoes`) | Calcula a dedução adicional. |
| `rota_deducao_limite_estrategico` | `ECF` | condiciona_credito | dedução do IRPJ e da CSLL devidos (`Mov_Apuracao_Irpj_Csll_Item.Valor_Deducoes`) | Trava a dedução adicional. |
| `rota_deducao_limite_excedente` | `ECF` | condiciona_credito | dedução do IRPJ e da CSLL devidos (`Mov_Apuracao_Irpj_Csll_Item.Valor_Deducoes`) | Limita `Excedente_Anterior_Utilizado`. |


# Anexo C. Anexo I do Decreto 12.435 na lista legal (80 linhas)

Tipo de lista `mover_requisitos_anexo_i`, vigência desde 01/06/2025 (art. 1º), provisório. A observação é o texto do decreto ("Ex" é o ex-tarifário da Tipi).

| Seção | Código da Tipi | Observação |
|---------|--------------------|------------------------------------------------------------------------|
| A | 8702.10.00 | exceto Ex 02 |
| A | 8702.20.00 | exceto Ex 02 |
| A | 8702.30.00 | exceto Ex 02 |
| A | 8702.40.90 | exceto Ex 02 |
| A | 8702.90.00 | exceto Ex 02 |
| A | 8703.21.00 | --- |
| A | 8703.22.10 | --- |
| A | 8703.22.90 | --- |
| A | 8703.23.10 | --- |
| A | 8703.23.10 | Ex 01 |
| A | 8703.23.90 | --- |
| A | 8703.23.90 | Ex 01 |
| A | 8703.24.10 | --- |
| A | 8703.24.90 | --- |
| A | 8703.31.10 | --- |
| A | 8703.31.90 | --- |
| A | 8703.32.10 | --- |
| A | 8703.32.90 | --- |
| A | 8703.33.10 | --- |
| A | 8703.33.90 | --- |
| A | 8703.40.00 | --- |
| A | 8703.50.00 | --- |
| A | 8703.60.00 | --- |
| A | 8703.70.00 | --- |
| A | 8703.80.00 | --- |
| A | 8703.90.00 | --- |
| A | 8704.21.10 | Ex 01 |
| A | 8704.21.20 | Ex 01 |
| A | 8704.21.30 | Ex 01 |
| A | 8704.21.90 | Ex 01 |
| A | 8704.31.10 | exceto Ex 01 |
| A | 8704.31.20 | exceto Ex 01 |
| A | 8704.31.30 | exceto Ex 01 |
| A | 8704.31.90 | exceto Ex 01 |
| A | 8704.41.00 | Ex 01 |
| A | 8704.41.00 | Ex 02 |
| A | 8704.41.00 | Ex 03 |
| A | 8704.51.00 | exceto Ex 01, 02 e 03 |
| A | 8704.60.00 | Ex 01 |
| B | 8701.21.00 | --- |
| B | 8701.22.00 | --- |
| B | 8701.23.00 | --- |
| B | 8701.24.00 | --- |
| B | 8701.29.00 | --- |
| B | 8702.10.00 | Ex 02 |
| B | 8702.20.00 | Ex 02 |
| B | 8702.30.00 | Ex 02 |
| B | 8702.40.90 | Ex 02 |
| B | 8702.90.00 | Ex 02 |
| B | 8704.21.10 | exceto Ex 01 |
| B | 8704.21.20 | exceto Ex 01 |
| B | 8704.21.30 | exceto Ex 01 |
| B | 8704.21.90 | exceto Ex 01 |
| B | 8704.22.10 | --- |
| B | 8704.22.20 | --- |
| B | 8704.22.30 | --- |
| B | 8704.22.90 | --- |
| B | 8704.23.10 | --- |
| B | 8704.23.20 | --- |
| B | 8704.23.30 | --- |
| B | 8704.23.90 | exceto Ex 01 |
| B | 8704.31.10 | Ex 01 |
| B | 8704.31.20 | Ex 01 |
| B | 8704.31.30 | Ex 01 |
| B | 8704.31.90 | Ex 01 |
| B | 8704.32.10 | --- |
| B | 8704.32.20 | --- |
| B | 8704.32.30 | --- |
| B | 8704.32.90 | --- |
| B | 8704.41.00 | exceto Ex 01, 02 e 03 |
| B | 8704.42.00 | --- |
| B | 8704.43.00 | exceto Ex 01 |
| B | 8704.51.00 | Ex 01 |
| B | 8704.51.00 | Ex 02 |
| B | 8704.51.00 | Ex 03 |
| B | 8704.52.00 | --- |
| B | 8704.60.00 | exceto Ex 01 |
| B | 8704.90.00 | --- |
| B | 8706.00.10 | exceto chassis com motor dos veículos do Ex 01 de 8702.10.00, 8702.20.00, 8702.30.00, 8702.40.90 e 8702.90.00 |
| B | 8706.00.90 | Ex 01 |


# Anexo D. Arquivos de carga (pasta `Carga206`)

| Arquivo | Linhas |
|-----------------------------------------------------------------------------------|-----------------|
| `Cad_Mover_Parametro.csv` | 34 |
| `Cad_Lista_Legal_Item_mover_anexo_i.csv` | 80 |
| `Cad_Classe_Sistema_valores_novos.csv` | 10 |
| `Cad_Obrigacao_Acessoria_linhas_novas.csv` | 4 |
| `Cad_Parametro_Documentacao_linhas_B8.csv` | 28 |
| `Cad_Parametro_Efeito_Obrigacao_linhas_B8.csv` | 28 |

# Anexo E. Perguntas ao contador (C269 a C277, documento 188, Parte 14)

- **C269** · Lei 14.902/2024, arts. 4º e 5º, e Decreto 12.435/2025, art. 7º · Importação de veículo sem ato de registro: dispensa, multa e tratamento da multa.
- **C270** · Lei 14.902/2024, arts. 6º, 7º e 8º, e Decreto 12.435/2025, arts. 5º e 6º · Multa compensatória de eficiência energética e de desempenho estrutural.
- **C271** · Decreto 12.435/2025, art. 7º, I e § 3º · Base da multa de importação sem ato.
- **C272** · Lei 14.902/2024, art. 16, § 4º · Dispêndio mínimo da empresa com mais de um segmento.
- **C273** · Lei 14.902/2024, art. 14 e Decreto 9.557/2018, arts. 22 e 23 · O que conta como dispêndio de P&D no Mover.
- **C274** · Lei 14.902/2024, arts. 16 e 18 · Como o crédito financeiro soma os indicadores e desconta o mínimo.
- **C275** · Lei 14.902/2024, arts. 26 a 28, e Decreto 9.557/2018, arts. 34 a 38 · Regime de autopeças não produzidas: multa de 30% ou 100%, e o decreto que vale.
- **C276** · Decreto 9.557/2018, arts. 14 e 19 · Rota 2030: excedente da dedução e direitos adquiridos depois de 30/11/2023.
- **C277** · Lei 14.902/2024, arts. 15 a 17 · Crédito financeiro do Mover: tratamento contábil, tributário e de compensação.

O texto completo de cada pergunta está no documento 188, Parte 14.

