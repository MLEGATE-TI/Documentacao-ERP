# Detalhamento da Q100-6: Mapa de Sugestão de Natureza da Operação — Documento 102 (versão 6)

> **Q102-7 respondida em 27/10/2026 (D-N374, documento 127): não há tabela pronta de NBS para natureza, porque varia com o CNAE principal da empresa; o mapa segue sem carga.**
>
> **Consolidado na revisão 21 (23/10/2026, documento 108), sem as linhas de partida da seção 6 (Q102-5, sem resposta; a carga do mapa fica vazia).** As contagens abaixo são as de quando o documento foi escrito.

*Você pediu para detalhar a Q100-6 do documento 100. Este documento mostra o que a tabela de naturezas que você enviou permite sugerir automaticamente, o que não permite, três opções de desenho e o que eu recomendo. **Não altera o dicionário** (revisão 20: 915 entidades, 9.878 campos). A versão 2 (22/10/2026) incorpora as suas respostas **Q102-1 (opção C), Q102-2 (sim) e Q102-4 (sim)** e traz o parâmetro do limite de US\$ 50.000. A versão 3 registra que, pelo documento 103, a sugestão passa a aparecer **na entrada do título** (regra 4 com dois momentos). A versão 4 incorpora a sua observação na Q103-5: **a faixa não pode ficar presa ao dólar**; ela é comparada na **moeda do parâmetro**, e títulos em euro ou em outra moeda são convertidos (regra 4). **A versão 6 (22/10/2026) registra a sua decisão de tirar a faixa de US\$ 50.000** e o princípio de que **na baixa vale sempre o contrato de câmbio**, o valor efetivo que cai na conta: o ERP **não calcula faixa, não converte moeda nem escolhe compra ou venda** para sugerir a natureza. Saem o campo `Faixa_Valor`, o parâmetro do limite com `ID_Moeda` e a seção 5A. O que ainda não foi respondido segue como proposta.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Para que serve o mapa:** o financeiro faz a pré-classificação (Q100-7) escolhendo, para cada pagamento ou recebimento com não residente, uma das **139 naturezas vigentes**. O mapa só **sugere** a natureza, para ele confirmar com um clique. **Nunca grava sozinho** e nunca bloqueia (regra 10 do documento 100).
- **O achado principal:** a **origem do título** (`Mov_Titulo.Origem_Tipo`) sozinha **não basta**. Uma `nota_fiscal_entrada` pode ser importação de mercadoria (natureza 12xxx) ou serviço (46xxx ou 47xxx), e essas duas coisas têm códigos diferentes. É preciso olhar **o que foi comprado**: o CFOP da nota (mercadoria) ou o NBS do serviço.
- **Segundo achado (a faixa saiu, 22/10/2026):** a tabela tem **dois níveis por valor**: nos grupos "Até US\$50.000,00" os códigos são resumidos (por exemplo `12995`, `46978`, `46992`) e nos "Acima de US\$ 50.000,00" são detalhados (por exemplo `12438`, `12122`, `46002`). Você decidiu que **o ERP não calcula essa faixa**: o código, resumido ou detalhado, é o que o **contrato de câmbio** do banco mostra, e o financeiro o escolhe na lista. A norma do Banco Central permite o código detalhado também até US\$ 50.000 (a pedido do cliente), então **sugerir o detalhado nunca é erro**.
- **Terceiro achado:** a tabela **não tem coluna de direção** (pagar ou receber). O mesmo código serve aos dois sentidos, então o **tipo** (`recebido` ou `pago`) entra na chave.
- **O que eu não consegui montar:** a ligação entre o **NBS** do serviço e o **código de natureza**. Fiz uma busca rápida e **não encontrei tabela oficial** que ligue as duas coisas (o que existe é a correlação NBS com item de serviço e CBS, da Receita, que é outro assunto). Se existir, é o contador quem sabe. Por isso **não proponho nenhuma linha NBS para natureza**: elas seriam inventadas.
- **Decidido por você:** **opção C** (mapa por critérios, agora com **10 campos**, sem a faixa), com o histórico do participante **antes** do mapa. Começa com **3 linhas de partida** que seguem dos nomes da tabela (seção 6), e o contador completa o resto com o uso. Pode vir **depois da primeira geração** do Y520.
- **Sem parâmetro de limite (decisão de 22/10/2026):** a aprovação da Q102-4 ficou **sem efeito**: não há conversão de moeda no ERP, então o limite de US\$ 50.000 **não entra** em `Cad_Ecf_Parametro` (seção 5A) e `Cad_Ecf_Parametro` **não ganha** o campo `ID_Moeda`.

# 2. O que o ERP já sabe na hora do pagamento

| Dado | De onde vem | Serve para sugerir |
|----------------------|----------------------------------|------------------------------|
| Tipo (pagar ou receber) | `Mov_Titulo.Tipo` | Direção (`pago` ou `recebido`) |
| Origem do título | `Mov_Titulo.Origem_Tipo` (24 valores, como `nota_fiscal_entrada`, `nota_fiscal_saida`, `emprestimo`, `distribuicao_lucro`, `royalty_venda`, `avulso`, `outro`) | Só a **família** da operação; muito grossa para a natureza |
| Nota de origem | `ID_Origem` aponta a nota; a nota tem itens com CFOP | Mercadoria: **CFOP começando em 3** é importação, **em 7** é exportação |
| Serviço da nota | `Cad_Produto_Servico_Dados_Servico.ID_NBS` (já existe) | Qual serviço; o código de natureza depende do contador |
| Participante | `Cad_Participante` (país, não residente) | Histórico: a última natureza usada com ele |

# 3. Três opções de desenho

| Opção | O que é | Campos | Quando serve | Limite |
|-------|---------|--------|--------------|--------|
| **A. Sem mapa** | O ERP repete a **última natureza** classificada para o mesmo participante e tipo; se não houver, vazio | 0 | Poucos fornecedores do exterior, sempre os mesmos | A primeira operação de cada participante vem em branco |
| **B. Mapa simples** | Chave `Origem_Tipo` + tipo: "título de tal origem, de tal tipo, sugere tal natureza" (o que está na seção 6.6 do documento 100) | 7 | Quando a origem já define a natureza (`emprestimo`, `distribuicao_lucro`) | Para `nota_fiscal_entrada` e `nota_fiscal_saida` **não distingue** mercadoria de serviço |
| **C. Mapa por critérios** | Chave `Origem_Tipo` + tipo + prefixo do CFOP + prefixo do NBS, com prioridade e vigência (a faixa de valor saiu em 22/10/2026) | 10 | Empresas que compram mercadoria e serviços do exterior | Mais campos; precisa do contador para preencher |

**Você escolheu a C (Q102-1).** A B quase não ajudaria justamente nos dois casos mais comuns (importação de mercadoria e de serviço), e a diferença é de **4 campos** a mais. A A pode continuar valendo **junto** com a C, como segundo critério (regra da seção 5).

# 4. Campos da opção C (`Cad_Natureza_Operacao_Sugestao`, nova, com vigência)

| **Campo** | **Tipo lógico** | **Descrição / regra** |
|--------------------|--------------------------------|------------------------------------------|
| **ID_Natureza_Sugestao** | *identificador* | --- |
| **ID_Empresa** | *referência (Cad_Empresa, opcional)* | Vazio vale para todas as empresas. |
| **Origem_Tipo_Titulo** | *código (40), opcional* | A origem do título (`Mov_Titulo.Origem_Tipo`). Vazio vale para qualquer origem. |
| **Tipo_Exterior** | *enumeração {recebido, pago}* | Receber ou pagar. |
| **Prefixo_CFOP** | *código (4), opcional* | Começo do CFOP dos itens da nota, por exemplo `3` (importação) ou `7` (exportação). Vazio não olha o CFOP. |
| **Prefixo_NBS** | *código (9), opcional* | Começo do NBS do serviço. Vazio não olha o NBS. |
| **Prioridade** | *inteiro* | Menor número vence quando duas linhas servem (a mais específica deve ter número menor). |
| **ID_Natureza_Operacao_Cambial** | *referência (Cad_Natureza_Operacao_Cambial)* | A natureza sugerida. Tem de estar vigente na data final da ECF. |
| **Vigencia_Inicio** | *data* | Início. |
| **Vigencia_Fim** | *data, opcional* | Fim. |

Contagem: **1 entidade, 10 campos** (no documento 100 estava prevista com 7; a faixa de valor saiu em 22/10/2026).

# 5. Regras propostas

- **Regra 1. Só sugere.** O campo `ID_Natureza_Operacao_Cambial` da classificação nasce **preenchido com a sugestão** e `Situacao = sugerida`; só vira `classificada` quando o financeiro confirma ou troca (documento 100, regras 4 e 10). **Na entrada do título** (documento 103) a natureza sugerida também é só uma proposta: a pessoa a confirma ou troca, e ela é **obrigatória** para salvar o título de não residente.
- **Regra 2. Ordem das fontes.** (a) a **última classificada** para o mesmo participante, tipo e mesma "classe do item" (mercadoria ou serviço); (b) a **linha do mapa** mais específica; (c) vazio. Assim o que o financeiro já escolheu uma vez com aquele fornecedor vale mais que o mapa geral.
- **Regra 3. Escolha da linha do mapa.** Entre as linhas vigentes na data da baixa, vale a que atende a **todos** os critérios preenchidos; havendo várias, a de **menor Prioridade**. Critério vazio atende a tudo.
- **Regra 4. Sem faixa de valor (decisão de 22/10/2026).** O ERP **não** compara o valor com US\$ 50.000, **não** converte moeda e **não** escolhe cotação, paridade, compra ou venda para sugerir. **Na baixa vale sempre o contrato de câmbio**, o valor efetivo que cai na conta (documento 101: `Taxa_Cambio` e `Valor_Pago_Reais` digitados do contrato). A sugestão traz o código **detalhado** (válido em qualquer valor) e o financeiro troca pelo **resumido** quando o contrato do banco assim o classifica. **Qualquer natureza da lista é aceita** na baixa; a norma só orienta, o ERP não trava por valor.
- **Regra 5. Nota com itens de naturezas diferentes.** Se os itens da nota levam a sugestões diferentes, **não sugere** e o financeiro escolhe. Não somo nem escolho "o item de maior valor".
- **Regra 6. Alternativas.** Quando a sugestão é uma das naturezas "irmãs" (por exemplo os seis códigos de prazo da importação de mercadoria), a tela mostra a sugerida e as **irmãs do mesmo grupo** para trocar com um clique. O prazo (antecipado, até 180 dias, de 181 a 360, mais de 360) **o ERP não sabe**: depende da data do embarque, que não tem campo no contas a pagar; quem classifica escolhe.
- **Regra 7. Código vencido.** Sugestão com natureza **não vigente** na data final da ECF não é oferecida (a lista já filtra, documento 100, regra 4).
- **Regra 8. Quem mantém.** Só o contador e o gestor mantêm o mapa. O financeiro **vê** a sugestão, mas não edita as linhas.
- **Regra 9. Sem efeito retroativo.** Mudar o mapa **não** muda classificações já confirmadas; só as que ainda estão `sugerida` podem ser refeitas, e só por um botão "refazer sugestões" (o usuário aciona).

# 5A. Sem parâmetro do limite de US\$ 50.000

Em 22/10/2026 você tirou a faixa. Por isso **não há** o parâmetro `limite_natureza_detalhada`, **nem** o campo `ID_Moeda` em `Cad_Ecf_Parametro`, **nem** os campos `Paridade_Contrato` do documento 104. `Cad_Ecf_Parametro` **fica como está** (limites de ativos no exterior, país a país e cartão, em reais). As perguntas Q102-3, Q102-4 e Q102-8 ficam **sem efeito**.

# 6. Linhas de partida (proposta, a validar com o contador)

Só coloquei o que **segue direto dos nomes da tabela**. O contador completa e corrige.

| Origem | Tipo | CFOP | NBS | Natureza sugerida | De onde tirei |
|------|------|------|-----|----------------------|----------------------------|
| `nota_fiscal_entrada` | pago | 3 | vazio | `12438` Importação, pagamento posterior, até 180 dias | Grupo "Comércio de bens"; **o mais comum**, mas o prazo muda o código (regra 6) |
| `nota_fiscal_saida` | recebido | 7 | vazio | `12122` Exportação, recebimento posterior, até 360 dias | Grupo "Comércio de bens"; o prazo muda o código (regra 6) |
| `distribuicao_lucro` | pago | vazio | vazio | `52443` Investimento direto, dividendos e juros sobre capital próprio | Grupo "Rendas de capitais" |

O código resumido (`12995`, compra ou venda de mercadoria) **não vai** para as linhas de partida: quem decide por ele é o contrato de câmbio, na escolha do financeiro.

**O que ficou de fora de propósito:** serviços (as famílias `46xxx` e `47xxx`), empréstimo (as famílias `72xxx` e `67xxx`, que se diferenciam por prazo e por tipo de credor), royalties e direitos autorais (`46112`, `46129`, `46136`, `47551` a `47582`). Para esses eu **preciso do contador**: a escolha depende de detalhes que não estão no cadastro (tipo do contrato, prazo, quem é o credor).

# 7. Decisões afetadas

- **Documento 100 (versão 11):** a seção 6.6 passa para a opção C **sem faixa** (10 campos) e a regra 4 ganha a ordem de fontes. Já ajustado.
- **`Cad_Ecf_Parametro` (Fase 2, Contabilidade e Fiscal):** **nada muda** (a proposta do `ID_Moeda` foi retirada).
- **Q100-7 (financeiro pré-classifica, contador corrige):** não muda; o mapa só preenche o ponto de partida.
- **Nada na revisão 20.** Só entra no dicionário quando você mandar "consolidar".

# 8. Não proponho

- Ligar o NBS direto ao código de natureza sem validação do contador.
- Gravar a natureza sem confirmação de uma pessoa.
- Deduzir o prazo (antecipado ou posterior) da data do pagamento: falta a data do embarque.
- Carregar o mapa completo agora: começa com as 5 linhas e cresce com o uso.
- Usar a "descrição" da tabela por texto (busca por palavra) para adivinhar o código.

# 9. Perguntas

**Respondidas por você (22/10/2026):** Q102-1 (opção C), Q102-2 (histórico do participante antes do mapa) e a **decisão de tirar a faixa de US\$ 50.000** (que torna sem efeito a Q102-4, o parâmetro do limite, a Q102-3, sobre os dois níveis por valor, e a Q102-8, o `ID_Moeda`).

**Ainda abertas (3)**

| Nº | Pergunta | Minha recomendação |
|-----|----------------------------------------------------|----------------------------------|
| **Q102-5** | As **3 linhas de partida** (seção 6) podem seguir como proposta para o contador validar? | Sim |
| **Q102-6** | Nota com itens de naturezas diferentes **não sugere nada** (regra 5)? | Sim |
| **Q102-7** | Seu contador conhece uma tabela que ligue **NBS** ao código de natureza? Se conhecer, ela vira a carga inicial do mapa de serviços | Perguntar ao contador |

# 10. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| `Cad_Natureza_Operacao_Sugestao` (opção C sem faixa, Q102-1) | 1 | 10 |
| **Total do documento 102** | **1** | **10** |

Sobre a revisão 20 (915 entidades e 9.878 campos): os documentos 100 e 101 com o mapa de 10 campos e o indicador de conta no exterior (Q100-9, ainda aberta) somam **920 entidades e 9.962 campos**. Sem o indicador de conta no exterior, tire 1 campo. Se o `Codigo_Referencia` do documento 99 também for aprovado, some 1 campo. Nada disso altera a revisão 20 até a consolidação.

# 11. Limites do que eu li

- Os **grupos** e os **códigos** vêm do arquivo do programa da ECF que você enviou (versão 9). A leitura dos dois níveis por valor é minha, e a Resolução BCB 277 (lida em resumo, no documento 104) a confirma; **não** usei mais essa leitura no desenho.
- As descrições de alguns códigos de empréstimo e de capitais estão **cortadas** no arquivo; por isso não os uso nas linhas de partida.
- Nenhuma linha aqui foi validada pelo contador.
