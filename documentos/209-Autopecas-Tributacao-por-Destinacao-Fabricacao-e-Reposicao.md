# Autopeças: tributação por destinação, fabricação de veículos × reposição (PIS/Cofins, IPI, ICMS ST, CBS e IBS) — Documento 209

> **O que este documento faz.** Você disse que, nas autopeças, a tributação muda conforme a peça vá para a **fabricação de veículos** ou para a **reposição no mercado**, e escolheu os quatro tributos: PIS e Cofins de 2026 (Lei 10.485), IPI (suspensão da Lei 9.826, art. 5º), ICMS com substituição tributária e CBS e IBS de 2027 em diante. Li a Lei 10.485/2002 compilada (o PDF que você enviou), o Convênio ICMS 142/18 (também enviado, com o Anexo II de autopeças e o Anexo XVI de pneus) e, na LC 214 e no Decreto 12.955, os artigos que tratam do fim da Lei 10.485 e do estoque. Desenhei **uma entidade nova, sete campos novos em três entidades existentes, dois domínios novos e uma carga provisória de regras**.
>
> **Nada foi aplicado ao dicionário.** Ele está na revisão 39 (1.173 entidades e 13.339 campos). Este documento só vale com a sua resposta às Q209-1 a Q209-11.

*Fontes: Lei 10.485/2002 (texto compilado, arts. 1º a 7º; arts. 1º e 2º só para o contexto), Lei 9.826/1999, art. 5º (na redação do art. 4º da Lei 10.485), Convênio ICMS 142/18 (cláusulas 1ª a 21ª, Anexo II e Anexo XVI; texto impresso em 11/11/2026, com alterações até o Convênio ICMS 107/26), LC 214/2025 (arts. 316, 381 e 542) e Decreto 12.955 (art. 605). Dicionário: revisão 39. **Não li** o Protocolo ICMS 41/2008 nem a legislação de ST de nenhuma UF.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **A diferença está no comprador, não na peça.** A mesma peça dos Anexos I e II da Lei 10.485 paga PIS e Cofins de **1,65% e 7,6%** quando a venda é para fabricante de veículos e máquinas (ou para fabricante de autopeças, se a peça vai para a fabricação deles) e de **2,3% e 10,8%** quando a venda é para atacadista, varejista ou consumidor (art. 3º, I e II). O atacadista e o varejista, quando vendem, pagam **0%** (art. 3º, § 2º). Por isso o desenho guarda a **destinação por item de pedido e de nota**, e não por produto.
- **Quem fabrica veículos e revende peça cai na alíquota da reposição** (art. 3º, § 6º) e, no ICMS, perde a inaplicabilidade da ST quando comercializa o mesmo bem (Convênio 142, cláusula nona, III). Um só marcador, `Comercializa_Mesmo_Item`, serve aos dois.
- **A retenção de 0,1% de PIS e 0,5% de Cofins é de quem compra**, quando o comprador é fabricante de veículos e máquinas do art. 1º e a peça é dos Anexos I e II, exceto pneumáticos; não vale para fornecedor do Simples nem para atacadista e varejista (art. 3º, §§ 3º a 7º). O dicionário já tem onde guardar (`Cad_Retencao_Federal_Parametro` e `Mov_Titulo_Retencao`); falta o **código de receita**, que vai ao contador (C278).
- **IPI:** as peças dos autopropulsados saem com **suspensão do IPI** do estabelecimento industrial para o estabelecimento industrial que as emprega na produção ou na montagem; a destinação diferente obriga a sair com imposto (Lei 9.826, art. 5º, §§ 2º e 5º). A filial ou controlada de fabricante que vende reposição também recebe com suspensão (§ 6º).
- **ICMS:** o Convênio 142 **não cria** a ST de autopeças (ela depende de acordo entre as UFs: cláusula segunda); ele só diz quando a ST **não se aplica**. Na operação interestadual para estabelecimento industrial que emprega a peça como matéria-prima, produto intermediário ou embalagem, e que não comercializa o mesmo bem, a ST não vale (cláusula nona, I e III). O texto do Protocolo ICMS 41/2008, que fixa a regra de autopeças, **ainda não foi lido**.
- **CBS e IBS de 2027:** a LC 214 **revoga os arts. 1º a 3º, 5º e 6º da Lei 10.485 em 01/01/2027** (art. 542, XVI) e não traz regra por destinação (busca "autope" nos dois textos: vazia). A destinação deixa de mudar o imposto da venda e passa a importar só para o **crédito presumido do estoque de 01/01/2027** (art. 381, II, "b": bens do art. 3º, II, e do art. 5º) e para o histórico.
- **Proposta:** 1 entidade nova (`Cad_Autopecas_Perfil`, 16 campos), 7 campos novos (3 em `Mov_Pedido_Venda_Item`, 3 em `Mov_Nota_Fiscal_Saida_Item` e 1 em `Mov_Nota_Fiscal_Saida_Item_St_Informacao`), 2 domínios novos (15 valores), 1 valor novo em `tipo_lista_legal`, 2 linhas de NCM de pneus, 1 linha de retenção que espera o código de receita e **18 regras provisórias** no Motor (Anexo A): as de PIS, Cofins e IPI terminam em 31/12/2026, as de ICMS não têm fim fixado e as de CBS e IBS começam em 01/01/2027.
- **Contador:** 8 perguntas novas, C278 a C285 (documento 188, Parte 15).

# 2. O que li

| Fonte | O que li | O que tirei |
|-------------------|----------------------------------------|----------------------------------------|
| Lei 10.485/2002 (compilada) | Arts. 3º (todos os parágrafos), 4º, 5º, 6º e 7º | As alíquotas por comprador, a retenção, a regra do fabricante que revende, os pneus e a exclusão de produtos usados |
| Lei 9.826/1999, art. 5º | O artigo inteiro, na redação do art. 4º da Lei 10.485 | As condições da suspensão do IPI, a obrigação de sair com imposto se a destinação mudar e a filial de reposição |
| Convênio ICMS 142/18 | Cláusulas 1ª a 21ª, a lista dos anexos, o Anexo II (autopeças) e o Anexo XVI (pneus) | Quando a ST não se aplica, o texto obrigatório na nota, a lista de CEST e a regra de que o convênio só vale com acordo entre as UFs |
| LC 214/2025 e Decreto 12.955 | Arts. 316, 381, 542 (XVI) e 605 | O fim da Lei 10.485 em 01/01/2027 e o crédito presumido do estoque |

**O que o Convênio 142 diz sobre autopeças.** O Anexo II traz **130 CESTs** do segmento 01 (identificados por varredura automática do texto, a conferir item a item na carga) e o Anexo XVI traz **10 CESTs** de pneus, câmaras de ar e protetores (segmento 16). O convênio é **geral**: a cláusula segunda condiciona a ST a acordo específico entre as UFs, e a cláusula quarta manda seguir a legislação da UF de destino. Por isso a regra de autopeças em si (quem retém, qual MVA) está no protocolo, que não li.

# 3. O que o dicionário já tem

| Peça | Entidade | Uso no 209 |
|-------------------|----------------------------------------|----------------------------------------|
| Lista legal | `Cad_Lista_Legal_Item` (20 campos; tipo `autopecas_lei_10485` com 66 linhas: 51 do Anexo I e 15 do Anexo II) | Diz se a NCM da peça é do regime; já tem `Condicao_Comprador` (`qualquer` ou `orgao_publico_ou_entidade_saude_imune`), que **não serve** para este caso e não muda |
| Destinação da compra | `Cad_Destinacao` e `Mov_Nota_Fiscal_Entrada_Item_Destinacao` | É a destinação do **comprador** (estoque, produção, imobilizado, despesa); fica para o crédito e para o estoque de abertura |
| Retenção federal | `Cad_Retencao_Federal_Parametro` (24 campos) e `Mov_Titulo_Retencao` (com `Valor_Retido_Pis_Pasep` e `Valor_Retido_Cofins`) | A retenção de 0,1% e 0,5%; o domínio `natureza_retencao_pis_cofins` já tem o valor "05: retenção por fabricante de máquinas e veículos" |
| Qualificação do participante | `Cad_Participante_Qualificacao_Cbs` (20 campos) | **Não reaproveito:** exige `Indicador_Contribuinte_Cbs` e é da CBS; o perfil de autopeças acaba em 2026 |
| Estoque de abertura | `Mov_Estoque_Abertura_Cbs_Item` (`ID_Motivo_Sem_Credito_Anterior` e `Fundamento_Hipotese`) | Já cobre a monofasia do art. 381, II, "b", e cita a Lei 10.485 |
| ICMS ST | `Cad_Cest`, `Cad_Cest_Classificacao`, `Mov_Nota_Fiscal_Saida_Item_St_Informacao` (7 campos), `Mov_Icms_St_Complemento_*` | A lista de CEST e o cálculo da ST; faltam só o texto e o dispositivo da inaplicabilidade |
| Motor de regras | `Cad_Motor_Regra`, `Cad_Motor_Regra_Criterio` (domínio aberto `campo_criterio_regra`), `Cad_Motor_Regra_Resultado` | Recebe os critérios e os resultados do Anexo A |
| Itens de venda | `Mov_Pedido_Venda_Item` (13 campos) e `Mov_Nota_Fiscal_Saida_Item` (129 campos) | **Nenhum dos dois tem campo para o uso da peça pelo comprador**; é a lacuna que o documento fecha |

# 4. Achados e leituras minhas

- **(1)** **A lei fala em "venda para fabricante", não em "peça de fabricação".** O art. 3º, I, "a", é a venda a fabricante de veículos e máquinas do art. 1º; o "b" é a venda a fabricante de autopeças **quando a peça é destinada à fabricação** dos produtos dos Anexos. A destinação então depende de quem compra **e** do que ele faz com a peça. O ERP não consegue provar isso: ele registra a declaração do comprador e avisa (D-N284).
- **(2)** **O mesmo teste do "fabricante que revende" aparece três vezes.** No PIS e na Cofins, o fabricante de veículos que revende peça paga a alíquota do inciso II (art. 3º, § 6º). No ICMS, a ST só deixa de valer para o industrial que **não comercializa o mesmo bem** (cláusula nona, III). No IPI, a suspensão exige emprego na produção ou na montagem (art. 5º, § 2º, da Lei 9.826) e a destinação diversa obriga a sair com imposto (§ 5º). Um marcador no perfil do comprador, `Comercializa_Mesmo_Item`, e a destinação por item cobrem os três.
- **(3)** **O IPI tem uma terceira via que o PIS e a Cofins não têm.** A filial ou controlada de fabricante que opera na **reposição** compra com suspensão do IPI (art. 5º, § 6º), mas, no PIS e na Cofins, é comerciante e entra na alíquota de 2,3% e 10,8%. Por isso a destinação tem o valor próprio `reposicao_filial_controlada`.
- **(4)** **A retenção é do comprador e já está meio desenhada.** O § 3º do art. 3º manda o **fabricante pagador** reter. Como o dicionário já tem a retenção federal com PIS e Cofins separados, a linha nova de `Cad_Retencao_Federal_Parametro` basta. O que falta é o código de receita da guia (entidade obriga o campo `ID_Codigo_Receita`), e eu **não** inventei um: a linha só entra depois da C278.
- **(5)** **Pneus são outro caso.** O art. 5º da Lei 10.485 cobra 2% e 9,5% de fabricante e importador de pneus (4011) e câmaras de ar (4013), com 0% para atacadista e varejista, **sem distinção por destinação**, e a retenção do § 3º não vale para pneus. Os pneus não estão nos Anexos I e II; precisam de uma lista própria.
- **(6)** **O Convênio 142 só trata da ST que não se aplica.** A inaplicabilidade vem de duas hipóteses: I (destinatário é industrial fabricante do **mesmo** bem) e III (destinatário é industrial que emprega a peça como matéria-prima, produto intermediário ou embalagem e não comercializa o mesmo bem), ambas só em **operação interestadual**. Quando a ST não se aplica, a cláusula vigésima, § 2º, manda indicar o dispositivo em "Informações Complementares", e a cláusula nona, § 3º, passa a sujeição passiva por substituição ao **destinatário**, salvo disposição da UF.
- **(7)** **Em 2027 a destinação some do imposto da venda.** A LC 214, art. 542, XVI, revoga os arts. 1º a 3º, 5º e 6º da Lei 10.485 a partir de 01/01/2027. O art. 4º, que traz a suspensão do IPI, **não** está na lista, mas o IPI vira zero em 2027, salvo a Zona Franca de Manaus (art. 454). O que sobrevive é o crédito presumido do estoque: o art. 381, II, "b", e o art. 605, II, "b", do Decreto 12.955, listam os bens do **art. 3º, II** (reposição) e do **art. 5º** (pneus); o **inciso I** (fabricação) **não** entra. (Leitura minha: quem comprou para fabricar usou a peça no processo e não tem estoque a creditar.)
- **(8)** **Leitura minha, a confirmar (C285):** o estoque de peças de reposição que o comprador adquiriu de fabricante na condição do inciso I não dá direito ao crédito presumido, mesmo que depois seja revendido.
- **(9)** **O que não resolvi:** a regra de ST na reposição. Sem o Protocolo ICMS 41/2008, o desenho só cobre a inaplicabilidade; a ST na reposição segue os mecanismos que o dicionário já tem (CEST, MVA e complemento por UF).

# 5. Proposta

## 5.1 Como as peças se encaixam

A decisão do Motor segue uma ordem fixa, e o ERP **só registra, calcula o que a lei fecha e avisa; não bloqueia** (D-N284):

- **(1)** **A peça é do regime?** A NCM do item está na lista `autopecas_lei_10485` (Anexos I e II) ou na lista nova `pneus_lei_10485` (4011 e 4013), e o item não é usado (art. 6º).
- **(2)** **Em que data?** As regras da Lei 10.485 e da suspensão do IPI valem até 31/12/2026.
- **(3)** **Quem vende?** O perfil da empresa vendedora (`Cad_Autopecas_Perfil` com `ID_Empresa`): fabricante, importador, atacadista, varejista ou fabricante de veículos que revende.
- **(4)** **Para que o comprador usa a peça?** A destinação do item (`ID_Destinacao_Autopeca`). Se estiver vazia, o Motor sugere pelo perfil do comprador (5.4) e o usuário confirma ou muda.
- **(5)** **Resultado:** alíquotas de PIS e Cofins, CST, IPI com suspensão ou com imposto, texto obrigatório na nota, ST aplicável ou não, e avisos.

| Entidade ou campo | Para quê | Vigência | Campos |
|-----------------------------------|----------------------------------------------|--------|-----------|
| `Cad_Autopecas_Perfil` (nova) | O perfil do comprador ou do vendedor para a Lei 10.485, a Lei 9.826 e o Convênio 142 | sim | 16 |
| `Mov_Pedido_Venda_Item`: 3 campos | A destinação da peça, a origem da informação e a declaração do comprador | não | 13 para 16 |
| `Mov_Nota_Fiscal_Saida_Item`: 3 campos | Os mesmos três, copiados do pedido e congelados na nota | não | 129 para 132 |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao`: 1 campo | O dispositivo do convênio que afasta a ST | não | 7 para 8 |

## 5.2 A entidade nova

### `Cad_Autopecas_Perfil` (Contabilidade & Fiscal, com vigência, 16 campos)

O perfil de uma pessoa (participante ou a própria empresa) perante a Lei 10.485, a Lei 9.826 e o Convênio ICMS 142: tipo de pessoa, se o estabelecimento é industrial, se comercializa o mesmo bem e a declaração que prova isso. Existe porque o dicionário não tem o campo que diz "este comprador é fabricante de veículos" nem "este industrial também revende a peça", e porque a mesma pessoa pode mudar de perfil no tempo. Não substitui nenhuma entidade; é lida pelo Motor.

| Campo | Tipo | Descrição |
|------------------|-----------------------------------------|-----------------------------------------|
| `ID_Autopecas_Perfil` | identificador | Chave. |
| `ID_Autopecas_Perfil_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Autopecas_Perfil_Versao). Fase 0, seção 2. |
| `ID_Participante` | referência (Cad_Participante), opcional | O comprador ou fornecedor. Exatamente um entre este campo e `ID_Empresa` é preenchido. |
| `ID_Empresa` | referência (Cad_Empresa), opcional | A própria empresa do ERP, quando ela é a vendedora ou a pagadora da retenção. |
| `ID_Tipo_Perfil` | referência (Cad_Classe_Sistema, domínio = tipo_perfil_autopecas) | O tipo da pessoa (Anexo B): fabricante de veículo ou máquina do art. 1º, fabricante de autopeças, importador, atacadista, varejista, consumidor final, filial ou controlada de reposição, fabricante de pneus e câmaras. |
| `Estabelecimento_Industrial` | booleano | O estabelecimento é industrial ou equiparado (condição da suspensão do IPI e da inaplicabilidade da ST). |
| `Comercializa_Mesmo_Item` | booleano | O estabelecimento também vende, sem industrializar, o mesmo bem (Lei 10.485, art. 3º, § 6º; Convênio 142, cláusula nona, III). O padrão é falso e o aviso 8 lembra de conferir. |
| `Origem_Declaracao` | enumeração {declaracao_do_comprador, consulta_cadastral, informado_pelo_usuario} | De onde veio a informação. |
| `ID_Documento_Declaracao` | referência (Cad_Documento), opcional | A declaração do comprador sobre o uso das peças. O ERP guarda e não valida. |
| `Data_Validade` | data, opcional | Até quando a declaração vale; depois disso, o Motor avisa. |
| `Fundamento_Legal` | texto, opcional | A norma ou o documento que sustenta o perfil. |
| `ID_Usuario_Registro` | referência (Cad_Usuario), opcional | Quem registrou. |
| `Situacao_Dado` | enumeração {provisorio, validado} | Provisório até o contador ou o usuário validar. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale; 31/12/9999 se indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

Regra de conferência: `ID_Participante` ou `ID_Empresa`, nunca os dois e nunca nenhum.

## 5.3 Campos novos nas entidades que já existem

| Entidade | Campo | Tipo | Para quê |
|--------------------|----------------|--------------------------------|--------------------------------|
| `Mov_Pedido_Venda_Item` | `ID_Destinacao_Autopeca` | referência (Cad_Classe_Sistema, domínio = destinacao_autopeca_venda), opcional | Para que o comprador vai usar a peça (7 valores, Anexo B) |
| `Mov_Pedido_Venda_Item` | `Origem_Destinacao_Autopeca` | enumeração {perfil_do_comprador, declaracao_do_item, informado_pelo_usuario}, opcional | De onde veio o valor; só a declaração do item prova a destinação |
| `Mov_Pedido_Venda_Item` | `ID_Documento_Declaracao` | referência (Cad_Documento), opcional | A declaração do comprador para aquele item ou pedido |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Destinacao_Autopeca` | referência (Cad_Classe_Sistema, domínio = destinacao_autopeca_venda), opcional | Copiado do pedido; a nota guarda o que valeu na emissão |
| `Mov_Nota_Fiscal_Saida_Item` | `Origem_Destinacao_Autopeca` | enumeração (os mesmos 3 valores), opcional | Idem |
| `Mov_Nota_Fiscal_Saida_Item` | `ID_Documento_Declaracao` | referência (Cad_Documento), opcional | Idem |
| `Mov_Nota_Fiscal_Saida_Item_St_Informacao` | `Dispositivo_Inaplicabilidade_St` | texto, opcional | O dispositivo do Convênio 142 que afasta a ST (cláusula nona, I ou III), que a cláusula vigésima, § 2º, manda pôr em "Informações Complementares" |

**Valores, textos e carga** (sem campo novo):

| Entidade | Mudança |
|---------------------------------------|-------------------------------------------------------------|
| `Cad_Classe_Sistema` | **Carga:** os domínios novos `destinacao_autopeca_venda` (7 valores) e `tipo_perfil_autopecas` (8 valores), ambos abertos, e 1 valor em `tipo_lista_legal` (`pneus_lei_10485`) |
| `Cad_Classe_Sistema` (`campo_criterio_regra`) | **Carga:** 4 critérios novos para o Motor: `perfil_vendedor_autopecas`, `perfil_comprador_autopecas`, `destinacao_autopeca_venda` e `lista_autopecas` |
| `Cad_Lista_Legal_Item` | **Carga:** 2 linhas (NCM 4011 e 4013) do tipo `pneus_lei_10485`, provisórias, vigência inicial 01/11/2002 |
| `Cad_Retencao_Federal_Parametro` | **Carga:** 1 linha (PIS 0,1%, Cofins 0,5%, IR e CSLL zero, `Dispensa_Optante_Simples` verdadeiro, natureza "05"), que **espera o código de receita** (C278) |
| `Cad_Motor_Regra` e filhas | **Carga:** 18 regras do Anexo A, provisórias |
| `Mov_Estoque_Abertura_Cbs_Item` | **Nenhum campo novo:** o motivo "monofasia" e o `Fundamento_Hipotese` já cobrem o art. 381, II, "b" |
| `Mov_Titulo_Retencao` | **Nenhum campo novo:** já guarda PIS e Cofins retidos |

## 5.4 Como o Motor sugere a destinação

Quando o item não tem destinação, o Motor sugere pelo perfil do comprador e deixa o usuário mudar. **O ERP nunca bloqueia** (D-N284); só avisa.

| Perfil do comprador | Destinação sugerida | Observação |
|--------------------------------|----------------------|-----------------------------------------------|
| Fabricante de veículo ou máquina do art. 1º | `fabricacao_veiculo_maquina` | Se `Comercializa_Mesmo_Item` for verdadeiro, o aviso 8 pergunta se a peça é para revenda |
| Fabricante de autopeças | `fabricacao_autopecas` | A lei exige que a peça vá para a fabricação dos produtos dos Anexos; o aviso 3 pede a declaração |
| Atacadista ou varejista | `reposicao_atacado_varejo` | |
| Filial ou controlada de reposição | `reposicao_filial_controlada` | Alíquota de PIS e Cofins de reposição, IPI com suspensão |
| Consumidor final | `consumidor_final` | |
| Comprador no exterior | `exportacao` | A exportação tem as regras gerais; o desenho só marca |

## 5.5 Como o ERP calcula

**PIS e Cofins até 31/12/2026 (Anexo A, R1 a R9).** Vendedor fabricante ou importador de peça dos Anexos I e II: destinação `fabricacao_veiculo_maquina` ou `fabricacao_autopecas`, **1,65% e 7,6%**; destinações de reposição ou consumidor, **2,3% e 10,8%**. Vendedor atacadista ou varejista, **0% e 0%**. Vendedor fabricante de veículo que revende, **2,3% e 10,8%** quaisquer que sejam a destinação e o perfil do comprador. Pneus e câmaras: **2% e 9,5%** do fabricante e do importador, **0%** do atacadista e do varejista. Item usado fica de fora. O CST e a natureza da receita de cada caso são a C280.

**Retenção na fonte (R9).** O comprador fabricante de veículo ou máquina do art. 1º que paga peça dos Anexos I e II (exceto pneus) retém **0,1% de PIS e 0,5% de Cofins** sobre o valor a pagar, a título de antecipação do fornecedor, **salvo** fornecedor do Simples, atacadista ou varejista; alcança também a industrialização por encomenda. O valor retido na quinzena é recolhido até o último dia útil da quinzena seguinte à do pagamento. O ERP calcula, grava em `Mov_Titulo_Retencao` com a natureza "05" e avisa; o código de receita espera a C278.

**IPI até 31/12/2026 (R10 a R13).** A saída de peça, componente, acessório ou carroçaria dos autopropulsados das posições 84.29, 84.32, 84.33, 87.01 a 87.06 e 87.11 vai com **suspensão** para o estabelecimento industrial que a emprega na produção de peças ou na montagem; na nota entra a expressão "Saída com suspensão do IPI" com o dispositivo legal e **sem destaque do imposto** (art. 5º, § 4º); o crédito de IPI do adquirente se mantém (§ 3º). Para peça destinada a **produzir peça**, a suspensão vale só se a peça final é dos Anexos I e II da Lei 10.485 (art. 4º, parágrafo único). O comprador que recebe com suspensão e dá **destinação diversa** emite a saída com imposto (§ 5º): o aviso 4 cobre. Reposição e consumidor saem com IPI.

**ICMS ST (R14 a R16).** Operação **interestadual** para estabelecimento industrial que é fabricante do **mesmo** bem (cláusula nona, I) ou que emprega a peça como matéria-prima, produto intermediário ou embalagem **e não comercializa o mesmo bem** (III): ST não se aplica, o Motor grava o dispositivo em `Dispositivo_Inaplicabilidade_St` e monta o texto de "Informações Complementares" (cláusula vigésima, § 2º). Nos demais casos, e em toda operação interna, vale a regra da UF de destino (cláusulas segunda, § 3º, e quarta); o desenho não cria nada novo. O CEST vai em todo item, mesmo sem ST (cláusula vigésima, I).

**CBS e IBS (R17 e R18).** A partir de 01/01/2027 a destinação **não muda** a alíquota da venda. No estoque de 01/01/2027, as peças compradas **para estoque** (destinação do comprador com rota `estoque`) cuja NCM está na lista `autopecas_lei_10485` ou `pneus_lei_10485` entram no `Mov_Estoque_Abertura_Cbs_Item` com motivo de monofasia e `Fundamento_Hipotese` "LC 214, art. 381, II, 'b'; Lei 10.485, art. 3º, II, ou art. 5º". As peças compradas para produção (rota `producao`) ficam fora. O ERP **sugere**; a elegibilidade é do usuário e do contador (C285).

## 5.6 Ligações com os outros blocos

- **B6 (documento 202).** O regime automotivo da LC 214 (crédito presumido de CBS) é de quem **fabrica** veículos; o 209 é de quem **vende peça**. Não se misturam.
- **IPI (documento 207, a preparar).** A tabela de IPI de 31/12/2025 trata das posições 8702 a 8704; as peças e o IPI das autopeças ficam neste documento.
- **Documento 206 (Mover).** O regime de autopeças **não produzidas** (isenção do II) é outro assunto e não depende deste.
- **Estoque de abertura (documento 65).** O 209 só liga o perfil e a destinação à elegibilidade do art. 381, II, "b".

# 6. Regras de texto: o que o Motor avisa

| N | Aviso | Quando |
|------|-----------------------------------------|-----------------------------------------------------|
| 1 | Venda de peça do regime sem destinação | O item tem NCM da lista e `ID_Destinacao_Autopeca` vazia, a data é até 31/12/2026 |
| 2 | Destinação sugerida pelo perfil, não declarada | `Origem_Destinacao_Autopeca` é `perfil_do_comprador` e a alíquota é a de fabricação (1,65% e 7,6%) |
| 3 | Fabricante de autopeças sem declaração | Destinação `fabricacao_autopecas` e `ID_Documento_Declaracao` vazio |
| 4 | Entrada com suspensão do IPI e destinação diversa | O item entrou com IPI suspenso e a saída ou o consumo não é produção ou montagem |
| 5 | Retenção de PIS e Cofins não calculada | O pagador é fabricante do art. 1º, a peça é dos Anexos e o fornecedor não é do Simples, atacadista ou varejista, e não há retenção no título |
| 6 | Perfil do comprador vencido | `Data_Validade` passou |
| 7 | Peça usada | O item é marcado como usado e a NCM é do regime (art. 6º: fora da lei) |
| 8 | Fabricante que também revende | `Comercializa_Mesmo_Item` verdadeiro: PIS e Cofins pela alíquota II e ST pode se aplicar |
| 9 | ST afastada sem dispositivo | Operação interestadual sem ST e `Dispositivo_Inaplicabilidade_St` vazio |
| 10 | ST afastada para comprador sem perfil industrial | `Estabelecimento_Industrial` falso ou sem perfil |
| 11 | Venda interestadual com CEST, sem regra de ST na UF | A UF de destino não tem regra carregada para o CEST |
| 12 | Regra de 2026 em nota de 2027 | A nota é de 01/01/2027 em diante e a regra da Lei 10.485 foi aplicada |
| 13 | Estoque de 31/12/2026 sem classificação | Peça do regime em estoque sem motivo no estoque de abertura |
| 14 | Destinação do pedido diferente da nota | Os dois itens têm valores diferentes |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---------|----------------------------------------------------------|---------------------------------|
| Q209-1 | Aprova **a destinação por item** (7 valores) e o **perfil** (8 valores), com a entidade nova `Cad_Autopecas_Perfil` (16 campos) como no 5.2? | Sim |
| Q209-2 | Aprova os **7 campos novos** do 5.3 (3 no pedido, 3 na nota e 1 na informação de ST)? | Sim |
| Q209-3 | Aceita que o **perfil da própria empresa** (vendedor e pagador da retenção) fique na mesma entidade, com `ID_Empresa`? | Sim |
| Q209-4 | Aprova as **regras de PIS e Cofins** R1 a R9 do Anexo A como carga provisória, com vigência até 31/12/2026? | Sim |
| Q209-5 | Aceita que a **linha de retenção** (0,1% e 0,5%) só entre quando o contador responder o código de receita (C278)? | Sim: não invento código |
| Q209-6 | Aprova as regras de **IPI** R10 a R13 com fim em 31/12/2026, deixando a Zona Franca de Manaus de 2027 em diante **fora**? | Sim |
| Q209-7 | Aprova, no ICMS, **só a inaplicabilidade** da cláusula nona (R14), o dispositivo na nota e o CEST em todo item? A ST na reposição segue os mecanismos que já existem. | Sim, até o Protocolo 41/2008 chegar |
| Q209-8 | Aceita que, em 2027, a **destinação não mude o cálculo** de CBS e IBS e só sirva ao estoque de abertura e ao histórico? | Sim |
| Q209-9 | Envia o **Protocolo ICMS 41/2008** (com as alterações de dezembro de 2025) e o regulamento de ST de uma UF de partida? Sem eles, a regra de ST na reposição fica sem desenho. | Enviar |
| Q209-10 | Aprova a **lista própria de pneus e câmaras** (`pneus_lei_10485`, 2 linhas)? | Sim |
| Q209-11 | Aceita que a **declaração do comprador** seja só guardada, sem validação automática (D-N284)? | Sim |

# 8. O que acontece se você aprovar

- **Tudo (Q209-1 a Q209-11):** 1 entidade nova, 23 campos (16 na entidade e 7 nas existentes), 9 campos de referência (5 na entidade e 4 nos itens) e 2 domínios novos. Sobre a revisão 39, só o 209: 1.174 entidades, 13.362 campos, 3.472 campos de referência e 357 domínios. **Com o 204, o B1 e o 206** (somas do documento 208): 1.198 entidades, 13.738 campos, 3.553 referências e 360 domínios. São somas minhas, a conferir no "consolidar". Nada é aplicado antes.
- **Carga:** 15 valores de domínio, 1 valor em `tipo_lista_legal`, 4 critérios do Motor, 2 linhas de pneus, 1 linha de retenção (espera a C278) e 18 regras (Anexo A).
- **Ao contador:** oito perguntas novas, C278 a C285 (documento 188, Parte 15).
- **Se a Q209-1 vier "não":** a destinação por item cai e o ERP só calcula pela lista legal, sem distinguir a fabricação da reposição; o PIS e a Cofins das autopeças ficam com a alíquota de reposição e o usuário corrige à mão.

# 9. Limites

- **Não li:** o **Protocolo ICMS 41/2008** e as suas alterações, a **legislação de ST de qualquer UF**, a Lei 10.485 arts. 1º e 2º (veículos e máquinas: 2% e 9,6%; fora deste desenho), o art. 17, § 5º, da MP 2.189-49 (exceção do art. 3º, § 2º, II), e o Decreto 12.955 além do art. 605.
- **O texto da lei vale até 31/12/2026.** As regras de PIS e Cofins e a suspensão do IPI **terminam** nessa data; o desenho não projeta 2027, salvo o estoque de abertura.
- **A ST na reposição não foi desenhada.** O Convênio 142 só dá o quadro geral; a regra de autopeças está no protocolo.
- **A declaração do comprador** é só guardada. O ERP não prova que a peça foi mesmo para a fabricação.
- **O Anexo II do Convênio 142** (130 CESTs) e o **Anexo XVI** (10 CESTs) foram contados por varredura automática; a carga confere item a item.
- **Art. 1º da Lei 10.485** (venda de veículos e máquinas) não está desenhado aqui. Se você quiser, é outro documento.

# Anexo A. As 18 regras provisórias do Motor

| Regra | Imposto | Se (vendedor; comprador ou destinação; peça) | Resultado | Fundamento | Vigência |
|---|----------|-------------------------|-------------------------|-------------------------|-------------|
| R1 | PIS e Cofins | Vendedor fabricante ou importador; `fabricacao_veiculo_maquina`; NCM nos Anexos I e II | 1,65% e 7,6% | Lei 10.485, art. 3º, I, "a" | até 31/12/2026 |
| R2 | PIS e Cofins | Vendedor fabricante ou importador; `fabricacao_autopecas`; NCM nos Anexos | 1,65% e 7,6% | Art. 3º, I, "b" | até 31/12/2026 |
| R3 | PIS e Cofins | Vendedor fabricante ou importador; `reposicao_atacado_varejo`, `reposicao_filial_controlada` ou `consumidor_final`; NCM nos Anexos | 2,3% e 10,8% | Art. 3º, II | até 31/12/2026 |
| R4 | PIS e Cofins | Vendedor atacadista ou varejista; NCM nos Anexos | 0% e 0% | Art. 3º, § 2º, I | até 31/12/2026 |
| R5 | PIS e Cofins | Vendedor fabricante de veículo ou máquina do art. 1º que revende; NCM nos Anexos | 2,3% e 10,8%, qualquer destinação | Art. 3º, § 6º | até 31/12/2026 |
| R6 | PIS e Cofins | Vendedor fabricante ou importador; NCM 4011 ou 4013 | 2% e 9,5% | Art. 5º | até 31/12/2026 |
| R7 | PIS e Cofins | Vendedor atacadista ou varejista; NCM 4011 ou 4013 | 0% e 0% | Art. 5º, parágrafo único | até 31/12/2026 |
| R8 | PIS e Cofins | Item usado | Fora da lei | Art. 6º | até 31/12/2026 |
| R9 | Retenção PIS e Cofins | Pagador fabricante do art. 1º; fornecedor que não é do Simples, atacadista ou varejista; NCM nos Anexos, exceto pneus | 0,1% e 0,5% do valor a pagar | Art. 3º, §§ 3º a 7º | até 31/12/2026 (espera a C278) |
| R10 | IPI | Destinação `fabricacao_veiculo_maquina`; peça dos autopropulsados (84.29, 84.32, 84.33, 87.01 a 87.06, 87.11) | Suspensão; texto "Saída com suspensão do IPI" e dispositivo; sem destaque | Lei 9.826, art. 5º, caput, §§ 2º, II, e 4º | até 31/12/2026 |
| R11 | IPI | Destinação `fabricacao_autopecas`; peça final dos Anexos I e II | Suspensão (idem) | Art. 5º, § 2º, I, e art. 4º, parágrafo único, da Lei 10.485 | até 31/12/2026 |
| R12 | IPI | Destinação `reposicao_filial_controlada` | Suspensão (idem) | Lei 9.826, art. 5º, § 6º | até 31/12/2026 |
| R13 | IPI | Destinação de reposição ou consumidor; entrada com suspensão sem destinação válida | Saída com imposto; aviso 4 | Art. 5º, § 5º | até 31/12/2026 |
| R14 | ICMS ST | Operação interestadual; CEST do segmento 01 ou 16; comprador `Estabelecimento_Industrial` e fabricante do mesmo bem, ou industrial que emprega a peça e `Comercializa_Mesmo_Item` falso | ST não se aplica; grava dispositivo; sujeição passiva ao destinatário | Convênio 142, cláusula nona, I e III, e § 3º; cláusula vigésima, § 2º | sem fim fixado (ICMS) |
| R15 | ICMS ST | Demais casos interestaduais | Regra da UF de destino, com o CEST no item | Convênio 142, cláusulas segunda, quarta e vigésima, I | sem fim fixado |
| R16 | ICMS ST | Operação interna | Regra da UF | Convênio 142, cláusula segunda, § 3º | sem fim fixado |
| R17 | CBS e IBS | Venda a partir de 01/01/2027 | Destinação sem efeito no cálculo | LC 214, art. 542, XVI | a partir de 01/01/2027 |
| R18 | CBS e IBS (estoque) | Estoque em 01/01/2027; compra com rota `estoque`; NCM nas listas | Sugere crédito presumido de monofasia no estoque de abertura | LC 214, art. 381, II, "b"; Decreto 12.955, art. 605, II, "b" | 01/01/2027 |

# Anexo B. Valores dos dois domínios novos

**`destinacao_autopeca_venda` (7 valores, domínio aberto):**

| Código | Rótulo | Quando |
|----------------------|--------------------------------|----------------------------------------------|
| `fabricacao_veiculo_maquina` | Fabricação de veículos e máquinas | Venda a fabricante de veículo ou máquina do art. 1º (Lei 10.485, art. 3º, I, "a") |
| `fabricacao_autopecas` | Fabricação de autopeças | Venda a fabricante de autopeças, peça destinada à fabricação (art. 3º, I, "b") |
| `reposicao_atacado_varejo` | Reposição, atacado e varejo | Venda a atacadista ou varejista (art. 3º, II) |
| `reposicao_filial_controlada` | Reposição, filial ou controlada de fabricante | Venda a filial ou controlada de fabricante que opera reposição (Lei 9.826, art. 5º, § 6º) |
| `consumidor_final` | Consumidor final | Venda ao consumidor (art. 3º, II) |
| `exportacao` | Exportação | Comprador no exterior |
| `outra` | Outra | Qualquer outra destinação; exige o aviso 1 |

**`tipo_perfil_autopecas` (8 valores, domínio aberto):**

| Código | Rótulo | Observação |
|---------------------|----------------------------------|---------------------------------------------|
| `fabricante_veiculo_maquina` | Fabricante de veículo ou máquina do art. 1º | Retém PIS e Cofins na compra de peça (art. 3º, § 3º) |
| `fabricante_autopecas` | Fabricante de autopeças | Vende com alíquota de fabricação se a peça vai para a fabricação dos Anexos |
| `importador` | Importador | Mesmas alíquotas do fabricante nas vendas |
| `atacadista` | Atacadista | 0% na venda (art. 3º, § 2º) |
| `varejista` | Varejista | 0% na venda |
| `consumidor_final` | Consumidor final | Alíquota de reposição do vendedor |
| `filial_controlada_reposicao` | Filial ou controlada de fabricante, na reposição | Recebe com suspensão do IPI (Lei 9.826, art. 5º, § 6º) |
| `fabricante_pneus_camaras` | Fabricante de pneus e câmaras de ar | Art. 5º da Lei 10.485 |

# Anexo C. Convênio ICMS 142/18: o que o texto diz para autopeças

| Dispositivo | O que diz | Uso no desenho |
|------------------|-----------------------------------------|-----------------------------------------|
| Cláusula 2ª, caput e § 3º | A ST nas operações interestaduais depende de acordo específico entre as UFs; a UF que a institui deve instituí-la também nas operações internas | O convênio sozinho não cria a ST de autopeças; o protocolo (não lido) cria |
| Cláusula 4ª | O substituto observa a legislação da UF de destino | R15 e R16 |
| Cláusula 7ª | Os bens são os dos Anexos II a XXVI, com descrição, NCM e CEST; só vale se a descrição bate | A lista de CEST do segmento 01 |
| Cláusula 9ª, I | A ST não se aplica à operação interestadual para estabelecimento industrial fabricante do mesmo bem | R14 |
| Cláusula 9ª, III | Idem, para industrial que emprega o bem como matéria-prima, produto intermediário ou embalagem e **não comercializa o mesmo bem** | R14 e `Comercializa_Mesmo_Item` |
| Cláusula 9ª, § 3º | Nas hipóteses da cláusula (exceto a do inciso V), a sujeição passiva por substituição cabe ao estabelecimento destinatário | R14 |
| Cláusula 20, I e § 2º | O CEST vai em todo item, mesmo sem ST; nas hipóteses da cláusula nona, a nota traz o dispositivo em "Informações Complementares" | R14, R15 e `Dispositivo_Inaplicabilidade_St` |
| Anexo II | Autopeças (segmento 01): 130 CESTs identificados | Lista de CEST |
| Anexo XVI | Pneumáticos, câmaras de ar e protetores de borracha (segmento 16): 10 CESTs | Lista de CEST |

# Anexo D. Perguntas ao contador (C278 a C285, documento 188, Parte 15)

| Id | Assunto |
|-----------|-----------------------------------------------------------------------------------------|
| C278 | Código de receita, base, prazo e cumulação da retenção de PIS e Cofins do art. 3º, §§ 3º a 7º, da Lei 10.485 |
| C279 | O que prova que a peça foi "destinada à fabricação" (art. 3º, I, "b") e quem responde quando a destinação muda |
| C280 | CST e natureza da receita (EFD-Contribuições) de cada caso R1 a R8 |
| C281 | A exceção do art. 3º, § 2º, II (art. 17, § 5º, da MP 2.189-49) para o atacadista e o varejista |
| C282 | O teste "não comercializa o mesmo bem" da cláusula nona, III: pelo estabelecimento comprador ou pela operação |
| C283 | A regra de ST de autopeças no Protocolo ICMS 41/2008 e nas UFs: destinação, MVA e inaplicabilidade |
| C284 | IPI: a base e o responsável na saída com imposto do § 5º, a prova do vínculo da filial ou controlada do § 6º e a Zona Franca em 2027 |
| C285 | CBS e IBS: o crédito presumido do estoque de 01/01/2027 para peças compradas na condição do inciso I e revendidas |
