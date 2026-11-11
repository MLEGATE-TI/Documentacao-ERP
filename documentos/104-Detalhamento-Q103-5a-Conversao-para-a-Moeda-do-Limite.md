# Registro da Q103-5a: Conversão para a Moeda do Limite (Retirada) — Documento 104 (versão 3)

> **Registro, sem campo (documento 108, revisão 21).** As contagens abaixo são as de quando o documento foi escrito.

*Este documento nasceu para detalhar a Q103-5a (como converter um título em euro para a moeda do limite de US\$ 50.000: série direta ou por reais, compra ou venda, dia da operação ou dia anterior). **Em 22/10/2026 você tirou a faixa de US\$ 50.000** e fixou o princípio de que **na baixa vale sempre o contrato de câmbio**. A versão 3 fica só como **registro** do que foi pesquisado e do motivo da retirada. **Não altera o dicionário** (revisão 20: 915 entidades, 9.878 campos) e **não cria campo.***

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Princípio decidido por você:** na baixa vale **sempre o contrato de câmbio**, o **valor efetivo que cai na conta**, o que o banco cobra ou paga. As regras de cotação, paridade e de lado compra ou venda servem para **calcular o contrato de câmbio**, que é feito fora do ERP, e **não importam** no ERP.
- **Decisão:** **tirar a faixa de US\$ 50.000** da sugestão da natureza. Saem `Faixa_Valor` do mapa (documentos 100 e 102), o parâmetro do limite e o campo `ID_Moeda` em `Cad_Ecf_Parametro` (documento 102, seção 5A), os 2 campos `Paridade_Contrato` que este documento propunha na versão 2 e a regra 3 do documento 103.
- **Como fica a sugestão:** o ERP sugere pelo **histórico do participante** e pelo **mapa** (origem, tipo, CFOP, NBS), trazendo o código **detalhado**, que a norma aceita em qualquer valor. **O financeiro troca** pelo código **resumido** quando o contrato do banco assim classifica. **Qualquer natureza da lista é aceita** na baixa.
- **O que continua valendo, e já está no desenho:** `Taxa_Cambio` e `Valor_Pago_Reais` digitados **do contrato** (documento 101) e o Y520 com o **valor líquido que entrou na conta** (documento 100). Nada disso depende de série de cotação.
- **Custo no dicionário:** **0 campos** neste documento. A retirada **reduz** o total (seção 4).

# 2. O que foi pesquisado (registro)

- **Resolução BCB 277** (lida em resumo, na página do Legisweb): até US\$ 50.000 "ou equivalente" os códigos de finalidade são os do Anexo III; acima, os do Anexo IV. A **pedido do cliente**, e com a concordância da instituição, pode-se usar o Anexo IV mesmo **até** US\$ 50.000. Os artigos citados são os que a página trouxe e **podem ter mudado** com alterações posteriores (a busca trouxe também a Resolução BCB 337/2023, que **não li**).
- **Equivalente em dólares:** a norma pede "a informação sobre taxas de câmbio mais recentemente disponível para a data do evento". Isso é regra de **quem fecha o câmbio**, não do ERP.
- **Banco Central, dados abertos:** para o **euro**, o Banco Central publica a **paridade em dólares por unidade** e **deriva** a cotação em reais multiplicando pela cotação do dólar. Por isso a conversão por "série direta" e a "por reais" dão o mesmo número quando usam o mesmo boletim e o mesmo lado.
- **Fracionamento:** a norma proíbe fracionar operação de câmbio para usar a faixa menor. É controle do **banco** no fechamento; o ERP **não** o replica (a Q104-6, aviso de fracionamento, fica **sem efeito**).

# 3. Um ponto de linguagem

Na versão 1 eu usei compra e venda **do ponto de vista do banco** (o banco **vende** a moeda a quem paga no exterior, o banco **compra** de quem recebe). Na sua mensagem a mesma ideia aparece com os nomes **trocados**, provavelmente do ponto de vista da empresa. É um exemplo do que você apontou: **o rótulo confunde**, e por isso o ERP **não** guarda nem escolhe lado. Vale o **valor efetivo** do contrato.

# 4. Contagem

| Item | Entidades | Campos |
|------------------------------|-----------|--------|
| Campos propostos na versão 2 (`Paridade_Contrato` em `Mov_Titulo_Baixa` e em `Mov_Credito`) | 0 | **retirados** |
| **Total do documento 104** | **0** | **0** |

**Efeito da retirada sobre os totais:** o mapa do documento 102 passa de 11 para **10 campos** (sai `Faixa_Valor`) e `Cad_Ecf_Parametro` **não ganha** o `ID_Moeda`. Os documentos 100 a 103, com os opcionais, somam **920 entidades e 9.965 campos** (eram 9.967). Se o `Codigo_Referencia` do documento 99 também for aprovado, some 1 campo. A revisão 20 segue intacta até a consolidação.

# 5. Perguntas

**Sem efeito (22/10/2026):** Q104-1 a Q104-8, porque a faixa saiu. Nenhuma pergunta aberta neste documento.

**Para o contador (opcional, fora do desenho):** a versão em vigor da Resolução BCB 277, caso você queira registrar a norma no dicionário como fundamento da natureza.

# 6. Limites do que eu li

- A **Resolução BCB 277** foi lida num resumo da página do Legisweb; os artigos podem ter mudado com alterações posteriores, e parte do texto não foi lida.
- A descrição dos dados abertos do Banco Central estava **cortada** em partes; usei só o que veio inteiro.
- Nenhuma conclusão foi validada pelo contador.

**Fontes:** [Resolução BCB 277 (Legisweb)](https://www.legisweb.com.br/legislacao/?id=440931) · [Taxas de câmbio, boletins diários (dados abertos do Banco Central)](https://dadosabertos.bcb.gov.br/dataset/taxas-de-cambio-todos-os-boletins-diarios)
