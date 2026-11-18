# Consulta ao Comitê Gestor da NFS-e Nacional: texto final com quatro dúvidas — Documento 245

*Você escreveu "seguir com as recomendações" (D-N628): a Q228-2 entra e a Q228-1 é sim. Este documento traz o **texto final para enviar**, com as três dúvidas do documento 228 e a quarta, do erro E2243 do ADN v1.1. **O envio é seu.** Nada foi aplicado ao dicionário (continua a revisão 54).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| Dúvida | Onde aparece | O que o ERP faz sem resposta |
|---|---|---|
| **Q-3** Sinal e alcance de `vAjusteBCIBSCBSComExt` na base do IBS e da CBS | NT SE/CGNFS-e 009, seção 2.3, e aba LEIAUTE do Anexo VI v1.04.01 | Segue o Anexo: soma o campo à `vBC`, com o sinal positivo |
| **Q-5** Caminho do grupo `gIBSCBSAjuste`: `IBSCBS/valores/trib/` (NT e matriz) ou `IBSCBS/valores/trib/gIBSCBS/` (aba LEIAUTE) | NT 009, seção 2.2, matriz de ajuste e aba LEIAUTE | Segue a aba LEIAUTE (com `gIBSCBS`) |
| **Q-12** Quando vale `regApIBSCBSSN` = 2 (CBS pelo Simples Nacional e IBS pelo regime regular) | NT 009, seção 2.4 | Guarda o que o contribuinte declarou; a hipótese do excesso do sublimite estadual fica registrada como leitura minha |
| **Q228-2** Erro **E2243** do ADN v1.1: "mesmo CNPJ base" contra a consulta por procuração de outra raiz (E2245) | Manual do ADN v1.1 (03/11/2026), consulta por procuração | Segue o texto da consulta por procuração e guarda o código de erro como o manual o publica |

As três primeiras só se resolvem por quem publica o leiaute: nenhum dos XSD enviados traz os grupos da NT 009 (os pacotes de 09/02/2026 e de 27/07/2026 são do leiaute 1.01). A quarta só se resolve por quem mantém o ADN.

# 2. Texto para enviar

**Assunto:** Dúvidas sobre o leiaute da DPS e da NFS-e com os grupos do IBS e da CBS (NT SE/CGNFS-e nº 009 e Anexo VI v1.04.01) e sobre a consulta do ADN (versão 1.1)

Prezados,

Somos a Mlegate, desenvolvedora de sistema de gestão que emitirá e receberá NFS-e pelo padrão nacional. Ao confrontar a Nota Técnica SE/CGNFS-e nº 009 (versão 1.0, de 04/06/2026) com o Anexo VI do leiaute (versão 1.04.01), e o Manual do ADN (versão 1.1) com ele mesmo, encontramos quatro pontos em que os textos divergem ou não dizem o suficiente. Pedimos a gentileza de esclarecê-los, indicando, se possível, a versão em que a resposta vale.

1. **Sinal e alcance do campo `vAjusteBCIBSCBSComExt`.** No Anexo VI, a base de cálculo do IBS e da CBS (`vBC`) soma esse campo, que no nome sugere uma redução e que tem valor positivo. A seção 2.3 da NT 009 apresenta a fórmula da `vBC` terminando em `vISSQN`, sem citar o campo. A fórmula do Anexo é a vigente? O campo reduz ou aumenta a base, em que sinal deve ser informado e para quais operações (comércio exterior) ele se aplica?

2. **Caminho do grupo `gIBSCBSAjuste`.** A seção 2.2 da NT 009 e a matriz de ajuste do Anexo VI situam o grupo em `IBSCBS/valores/trib/`. A aba LEIAUTE do mesmo Anexo o situa em `IBSCBS/valores/trib/gIBSCBS/`. Qual é o caminho correto no XML?

3. **Valor 2 do campo `regApIBSCBSSN`.** A seção 2.4 da NT 009 confirma os três valores e seus textos, mas não diz em que situação se informa o valor 2 (CBS apurada pelo Simples Nacional e IBS pelo regime regular). Trata-se do contribuinte que ultrapassou o sublimite estadual, ou de outra hipótese? Existe regra de validação que condicione o valor 2 a algum evento ou data?

4. **Erro E2243 na consulta do ADN (versão 1.1).** O Manual do ADN v1.1 diz, no erro E2243, que o CNPJ informado na consulta "deve ter o mesmo CNPJ base" do solicitante. O mesmo manual, porém, autoriza a consulta de outra raiz de CNPJ mediante procuração (erro E2245 para a procuração inválida). Para a consulta por procuração, vale a exigência de mesmo CNPJ base do E2243 ou a regra da procuração? Se o E2243 se aplica só à consulta sem procuração, o texto do erro deve ser entendido assim?

Aguardamos o retorno e agradecemos a atenção.

Atenciosamente,
Alberto Beyeler
Mlegate · [CNPJ] · [telefone e e-mail de contato]

# 3. Antes de enviar

- **O canal é seu:** não confirmei o canal de atendimento do Comitê Gestor da NFS-e nem o prazo de resposta. O texto serve para e-mail, formulário ou chamado.
- **Preencha** CNPJ e contato; deixei entre colchetes porque não os tenho.
- **Se quiser, acrescente** a Q-13 (cronograma de produção do leiaute 1.04): a NT diz que o cronograma sai "nas próximas semanas" e a regra E0855 fala em 01/10/2026. Não incluí, porque você aprovou só os pontos acima.
- Traga a resposta ou o número do protocolo e atualizo os documentos 41, 227 e 229.

# 4. Limites

- O texto reproduz a minha leitura da NT 009, do Anexo VI v1.04.01 e do Manual do ADN v1.1 feita nos documentos 41, 227 e 229; **não reli esses arquivos nesta sessão** (não estão neste ambiente). A redação do item 4 segue a descrição do achado no documento 229; confira o texto exato do E2243 e do E2245 no manual antes de enviar.
- A hipótese do excesso do sublimite estadual para o valor 2 é minha e **não** foi colocada na pergunta como fato.
