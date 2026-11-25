# Desenho do FGTS: provisão, retorno do eSocial, guia, histórico de remunerações e rescisão — Documento 252 (versão 9)

*Você aprovou a **Q250-46** («sim, concordo»): no FGTS cada etapa tem **um dono só** (a folha calcula e estima, a camada eSocial envia e recebe, o FGTS Digital emite a guia e calcula a multa, o motor bancário só paga o Pix da guia, a conciliação confere) e o **título do FGTS passa a nascer do valor oficial**, com a folha lançando só a provisão. Este documento é o **desenho** disso. **Nada foi aplicado ao dicionário** (continua a revisão 59: **1.270 entidades e 14.944 campos**); entra só se você aprovar as perguntas da seção 6 e escrever «consolidar».*

*Versão 9 (24/11/2026): você escreveu **«consolidar»**. Apliquei ao dicionário, na **revisão 60** (documento 258), **tudo o que você aprovou neste documento**: as **9 entidades novas e 111 campos** e o valor **`folha_externa`** em `Mov_Titulo.Origem_Tipo`. **Resultado:** **1.279 entidades e 15.055 campos** (eram 1.270 e 14.944), 3.809 campos de referência (eram 3.782), 1.556 tabelas físicas. **Nada ficou de fora.** **Onde ficou (leitura minha, porque o documento não dizia):** as **nove entidades no módulo Folha & RH** (a guia, os débitos e o lote ficam ao lado do retorno do eSocial, onde já mora o `Mov_Esocial_Retorno`; o Financeiro usa por perfil, R13) e o valor `folha_externa` em **Contas a Pagar/Receber**, onde mora o `Mov_Titulo`. **Sem Carga:** os dois valores do domínio `tipo_evento_esocial` (S-5003 e S-5013) são cadastro do usuário, como o domínio sempre foi. Decisão **D-N706**.*

*Versão 8 (24/11/2026): você respondeu duas perguntas. **Q252-10: «seguir recomendação»**: a **estrutura do lote importado da folha externa fica aprovada** (as duas entidades `Mov_Rh_Folha_Externa_Lote` e `Mov_Rh_Folha_Externa_Lote_Ocorrencia`, o campo `ID_Lote_Folha_Externa` no retorno e o valor `folha_externa` em `Mov_Titulo.Origem_Tipo`). **Q252-11: «OK. Mas o que o eSocial retorna, considerar a importação do XML do eSocial»**: as **outras naturezas** da folha externa (líquido, INSS e IRRF) **saem do documento 252** e serão desenhadas na integração da folha com o financeiro (recomendação (b)), **com a condição que você pôs**: onde o eSocial devolve o dado (S-5001 e S-5002 por trabalhador; S-5011 e S-5012 consolidados, que o ERP já importa), **o caminho é importar o XML**, e o CSV só entra onde o eSocial não devolve nada (o líquido). **Correção minha:** na Q252-10 eu escrevi «3 valores de enumeração» como custo da proposta; a conta certa é: **3 valores em entidades que já existem** no total (os 2 do domínio `tipo_evento_esocial` e o `folha_externa`), dos quais **só 1 é novo desta proposta**; o `importacao_csv` pertence à entidade nova do retorno e já está nos campos. **Efeito:** (a) **nove entidades novas e 111 campos aprovados** para o próximo «consolidar»: **1.279 entidades, 15.055 campos e 3.809 referências** se aplicado; (b) a seção 3.6 corrige o `Mov_Titulo.Origem_Tipo` (agora **um valor novo**, `folha_externa`); (c) **nenhuma pergunta aberta** neste documento; (d) o desenho das outras naturezas fica **pendente do meu lado** (seção 5). **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos).*

*Versão 7 (24/11/2026): você respondeu duas perguntas. **Q252-3: «seguir recomendação»** (leitura minha: a pergunta que sobrava era a **quantidade** de admitidos antes de 03/2024; a recomendação é que a **quantidade sai da própria migração**, e você não precisa informá-la). **Q252-8: «considerar importar o XML do S-5003 e usar este para gerar um layout do csv»** (leitura minha: na folha processada fora do ERP, o ERP **importa o XML do S-5003** que a folha externa recebeu do eSocial, e o **CSV tem o leiaute derivado do esquema do S-5003**, para quando o XML não estiver à mão). **Efeito:** (a) a regra **R15** é reescrita (o ERP **passa a receber o retorno** também nesse modo, por importação; a minha recomendação anterior dizia que não); (b) o leiaute do CSV, de 14 colunas tiradas do esquema, está na **nova seção 3.8**; (c) regra **R20** (conferência do lote antes de gerar o título); (d) **proposta de estrutura** (Q252-10): +2 entidades (`Mov_Rh_Folha_Externa_Lote` e `Mov_Rh_Folha_Externa_Lote_Ocorrencia`), +1 campo no retorno e +3 valores de enumeração; (e) **pergunta nova Q252-11** (e as outras naturezas: líquido, INSS e IRRF?). **O desenho aprovado continua 7 entidades e 88 campos**; a proposta, se aprovada, leva a **1.279 entidades e 15.055 campos** (3.809 referências). **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos).*

*Versão 6 (24/11/2026): você respondeu à **Q252-3**: **«sim tem admitidos antes desta data 03/2024, guardasse todo o histórico desde a contratação»**. **Leitura minha:** o sistema de folha atual **guarda todo o histórico de remunerações desde a contratação** (e o ERP deve **recebê-lo inteiro**: as duas leituras dão o mesmo efeito). **Efeito:** (a) a **migração do histórico é possível e é o caminho** (`Origem_Historico` = `migracao`); (b) o **Método 1** (todas as remunerações, Anexo I) passa a ser o **padrão** para os admitidos antes de 03/2024, e o **Método 2** (base pedida à Caixa) fica só como **exceção**; (c) regra **R19**. **Nenhuma entidade nem campo novo** (7 entidades e 88 campos como na versão 5). **Falta** só a **quantidade** desses admitidos, que ajuda a dimensionar a migração mas **não bloqueia** nada. **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos).*

*Versão 5 (24/11/2026): você respondeu **«Q252-9: Aprovo»** (decisão **D-N702**). **Efeito:** a **entidade nova `Mov_Esocial_Retorno_Fgts_Valor`** (12 campos) e os **dois campos novos** do cabeçalho do retorno (`Indicador_Apuracao` e `Existencia_Informacao`) **entram no desenho aprovado**, junto com a **regra R18** (conferência por tipo de valor). **Total aprovado para o próximo «consolidar»: 7 entidades e 88 campos** (1.277 entidades, 15.032 campos e 3.804 referências se aplicado). **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos). Faltam só **dois materiais seus** (o CSV de exemplo da folha externa e a quantidade de admitidos antes de 03/2024).*

*Versão 4 (24/11/2026): você enviou **três pacotes de esquemas XSD S-1.3** (de 01/12/2026, 14/12/2026 e 18/01/2027). Para o **S-5003 (`evtBasesFGTS`) e o S-5013 (`evtFGTS`) os três são idênticos** (os pacotes diferem em outros eventos: S-1000, S-1010, S-5001, S-5011, S-8200 e `evtContProc`). **Li os dois esquemas** e a estrutura está em 3.2 (tabelas «Leiaute conferido»). **Três achados:** (a) o **vencimento**: o S-5003 só informa `dtVenc` para períodos **anteriores ao FGTS Digital** (e no dia 7), e o S-5013 **não tem** vencimento; portanto o campo `Data_Vencimento_Fgts` fica vazio na prática e o vencimento vem do parâmetro (dia 20) e da guia, o que **confirma a Q252-7**; (b) o retorno traz o **depósito por tipo de valor** (mensal, 13º, rescisão, aviso prévio, período anterior, entre outros), que é o que casa com os débitos da guia, e o desenho da versão 1 só guardava o total; (c) o S-5003 e o S-5013 vêm **por estabelecimento e lotação**. **Proposta (Q252-9, não aprovada):** +2 campos no retorno e **uma entidade de detalhe por tipo de valor** (12 campos). **O que você aprovou na D-N697 (6 entidades e 74 campos) continua valendo.** **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos).*

*Versão 3 (24/11/2026): você respondeu **«Q252-1 a 8 Seguir recomendações»** (decisão **D-N697**). **Efeito:** (a) **Q252-7 (a):** o título do FGTS nasce da **integração da folha** quando o retorno volta, e a **guia do FGTS Digital se liga ao título** (traz o Pix e confere valor e vencimento); (b) **Q252-1:** a recomendação dela era a guia como gatilho e **conflita** com a da Q252-7; como a Q252-1 já tinha sido substituída pela Q252-7, **prevalece a Q252-7** (**confirmado por você em seguida, D-N698: «FGTS integração vem da folha»**); (c) **Q252-2, 3, 4, 5, 6 e 8:** seguem as recomendações (CSV da folha externa com **todas as naturezas** no mesmo leiaute; estimativa da multa rotulada; retorno por webservice com importação manual; perfis RH e Financeiro; migrar o histórico existente). **Muda uma contagem:** o valor `fgts_guia_debito` de `Mov_Titulo.Origem_Tipo` **deixa de ser necessário** (o título usa `folha_pagamento`, que já existe): são **2 valores de enumeração**, e não 3. Continuam **6 entidades e 74 campos**. **Falta material seu (seção 6):** o **arquivo do leiaute (XSD ou PDF)** do S-5003 e do S-5013 (**tentei buscar no portal do eSocial e não consegui a tabela de tags**), o **CSV de exemplo** da folha externa e a **quantidade de admitidos antes de 03/2024**. **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos); o desenho entra no próximo «consolidar».*

*Versão 2 (24/11/2026): você respondeu a **Q252-2** descrevendo o circuito: o FGTS **nasce na folha**, a folha o **envia ao eSocial**, o **retorno volta para a folha** (fecha o circuito) e **da folha segue ao financeiro e à tesouraria** para pagamento, **por integração entre os módulos**; se a folha for **processada externamente**, o financeiro **importa um CSV**. Registrei em 3.1 e nas regras R14 e R15 (decisão **D-N696**). **O que mudou:** (a) **nenhuma entidade nem campo novo** (o retorno já se liga à apuração da folha pelo evento de origem); (b) **conflito com a minha recomendação da Q252-1** (título nascer da guia importada): o seu circuito faz o título nascer da **integração da folha**; por isso a Q252-1 fica **substituída pela Q252-7**; (c) **duas perguntas novas:** Q252-7 (como a guia se encaixa) e Q252-8 (o CSV da folha externa). **Nada aplicado ao dicionário** (continua 1.270 entidades e 14.944 campos).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **O que muda no fluxo:** hoje a liquidação da folha gera o título do FGTS. No desenho novo, a folha lança só a **provisão contábil** do FGTS (como já faz com INSS e IRRF retido desde 01/10/2026, P-15) e o **título nasce com o valor oficial**: quando o retorno do eSocial **volta para a folha**, a folha **entrega o FGTS ao contas a pagar** (Q252-7, aprovada, D-N697). A **guia do FGTS Digital** se liga ao título e traz o Pix (seção 3.1).
2. **O que o ERP passa a guardar:** (a) o **retorno do eSocial** do FGTS, S-5003 (por trabalhador) e S-5013 (consolidado), para conferir a folha (seção 3.2); (b) a **guia** do FGTS Digital e os **débitos** que ela agrupa (seção 3.3); (c) o **histórico de remunerações** e o **arquivo do Anexo I** (seção 3.4); (d) a **rescisão**: o método da multa, a base pedida à Caixa e a multa estimada contra a oficial (seção 3.5). Na **folha externa**, o ERP importa o **XML do S-5003** ou um **CSV derivado dele** (seção 3.8).
3. **Nove entidades novas, 111 campos (aprovadas na D-N697, na D-N702 e na D-N705, e **aplicadas na revisão 60**, D-N706):** `Mov_Esocial_Retorno_Fgts` (23, com o campo do lote), `Mov_Esocial_Retorno_Fgts_Valor` (12), `Mov_Fgts_Guia` (16), `Mov_Fgts_Guia_Debito` (9), `Mov_Rh_Fgts_Arquivo_Historico` (9), `Mov_Rh_Fgts_Historico_Remuneracao` (7), `Mov_Rh_Fgts_Rescisao` (13) e, da folha externa, `Mov_Rh_Folha_Externa_Lote` (14) e `Mov_Rh_Folha_Externa_Lote_Ocorrencia` (8). Nenhuma tem vigência. Mais **três valores de enumeração** em entidades que já existem (seção 3.6). **Aplicado na revisão 60: 1.279 entidades e 15.055 campos** (27 campos de referência a mais).
4. **O que não existe e eu não inventei:** o manual do FGTS Digital (versão 1.70) **não traz API** para emitir guia, consultar débito ou obter saldo. A guia, portanto, **entra no ERP por importação do relatório (CSV) ou por digitação conferida**, e o **valor da base rescisória** (Método 2) é **pedido à Caixa** e digitado. O leiaute de tags dos eventos S-5003 e S-5013 **não foi conferido** nesta versão (as páginas que li não trazem as tabelas de tags): os campos do retorno são os de **negócio** (base, depósito, vencimento, recibo) e o XML fica guardado inteiro (**Q252-5**).
5. **Para você:** as **onze perguntas foram respondidas** (D-N697, D-N702, D-N704 e D-N705); **não falta mais material seu** (a Q252-3 e a Q252-8 foram respondidas, D-N704), e **nenhuma pergunta ficou aberta**; o que resta é **meu** (desenhar as outras naturezas da folha externa, seção 5). **Para o contador:** a C374 continua aberta (vencimento no dia 20 e multa de 40%); proponho **uma pergunta nova** sobre a contabilização (seção 7).
6. **O que a versão 2 trouxe (D-N696):** o **circuito do FGTS que você descreveu** (folha calcula e envia, retorno volta para a folha, folha entrega ao financeiro por integração; **folha externa = CSV importado**), com regras R14 e R15 e as perguntas Q252-7 e Q252-8. **Sem mudança de entidades ou campos.**
7. **O que a versão 3 trouxe (D-N697):** todas as perguntas respondidas pelas recomendações; **o título nasce da integração da folha e a guia se liga a ele** (R16); o valor `fgts_guia_debito` sai (**2 valores de enumeração**); **sem mudança em entidades e campos** (6 e 74); tentei obter as tags do S-5003 e do S-5013 e **não consegui** (seção 10).
8. **O que a versão 4 trouxe (D-N701):** o **leiaute do S-5003 e do S-5013 lido nos esquemas XSD S-1.3** (seção 3.2), a **correção do vencimento** (o eSocial não o informa no FGTS Digital) e a **proposta Q252-9** (retorno por tipo de valor: +1 entidade e +14 campos). A Q252-5 está **cumprida**; faltam dois materiais (o CSV da folha externa e a quantidade de admitidos antes de 03/2024).
9. **O que a versão 5 trouxe (D-N702):** a **Q252-9 aprovada**: entra a entidade `Mov_Esocial_Retorno_Fgts_Valor` (12 campos) e mais 2 campos no retorno; **7 entidades e 88 campos** aprovados para o próximo «consolidar»; regra R18 em vigor.
10. **O que a versão 6 trouxe (D-N703):** a **Q252-3 respondida**: há admitidos antes de 03/2024 e o sistema atual guarda o histórico desde a contratação; **migração do histórico completo** e **Método 1 como padrão** (R19). Sem mudança de entidades e campos.
11. **O que a versão 7 trouxe (D-N704):** a **Q252-3 fechada** (a quantidade sai da migração) e a **Q252-8 respondida**: na folha externa o ERP **importa o XML do S-5003** e o **CSV tem o leiaute derivado do esquema** (seção 3.8, R15 e R20). **Proposta** (Q252-10): +2 entidades e +23 campos para o lote importado; **pergunta nova** Q252-11 (outras naturezas).
12. **O que a versão 8 trouxe (D-N705):** a **Q252-10 aprovada** (lote importado da folha externa: **9 entidades e 111 campos** aprovados; 1.279 / 15.055 / 3.809) e a **Q252-11 respondida** (as outras naturezas saem deste documento, e onde o eSocial devolve o dado o caminho é **importar o XML**); correção da conta de valores de enumeração.
13. **O que a versão 9 trouxe (D-N706):** o **«consolidar»**: a **revisão 60** aplicou as **9 entidades e 111 campos** e o valor `folha_externa` (1.279 entidades e 15.055 campos); sem Carga; nada ficou de fora.

# 2. O que o dicionário já tem

| Peça | O que existe | Limite |
|---|---|---|
| Cálculo do FGTS | Verbas com `Incide_Fgts` e `ID_Incidencia_Fgts` (`Cad_Rh_Verba`); `Mov_Rh_Folha_Item` (verba por colaborador); `Cad_Rh_Motivo_Desligamento` com `Percentual_Multa_Fgts` e `Percentual_Saque_Fgts`; `Cad_Vinculo_Emprego.Data_Opcao_Fgts` | É a **estimativa**; não há retorno oficial para conferir |
| Título do FGTS | A liquidação de `Mov_Rh_Folha_Apuracao` gera um título por natureza, **inclusive `fgts`** (`Natureza_Titulo_Folha`); o vencimento vem de `Cad_Regra_Vencimento` e do parâmetro `Cad_Rh_Parametro_Vencimento_Encargo` (revisão 56) | O título nasce **da folha**, não do valor oficial |
| Retorno do eSocial | `Mov_Esocial_Retorno` (S-5011, S-5012 e S-5501), com conciliação e diferença de provisão para INSS e IRRF | **Não há** S-5003 nem S-5013 |
| Envio ao eSocial | `Mov_Esocial_Evento` (status, recibo, retificação) | O S-5003 e o S-5013 são **retorno**, não evento enviado |
| Pagamento | `Mov_Remessa_Bancaria_Item` e o motor bancário (documento 250): Pix por QR Code ou copia e cola (R89, R100); `E2eid` (R16) | Não conhece a guia do FGTS Digital |
| Processo trabalhista | `Mov_Rh_Processo_Trabalhista_Apuracao_Base` (`Base_Fgts`, `Valor_Fgts_Devido`) e o S-5503 | É outro caminho (reclamatória), fora deste documento |
| Histórico de remunerações, base rescisória, guia, multa oficial | **Nada** (conferi o modelo: nenhuma entidade nem campo com esses nomes) | É o que este documento desenha |

# 3. Desenho

## 3.1 Quem faz o quê, e quando o título nasce

| Etapa | Dono | O que faz |
|---|---|---|
| 1. Cálculo | **Folha** | Base e valor do FGTS por colaborador e competência; lança a **provisão contábil** (conta de provisão de encargos, critério `natureza_titulo_folha`); **estima** a multa na rescisão |
| 2. Envio e retorno | **Camada eSocial** | Envia remuneração (S-1200), desligamento (S-2299 e S-2399) e fechamento (S-1299); recebe o **S-5003** (retorno de cada evento de remuneração ou desligamento, por contrato) e o **S-5013** (retorno do fechamento, total do período) |
| 3. Guia e multa | **FGTS Digital** (portal) | Emite a guia a partir do que o eSocial entregou e **calcula a multa** (indenização compensatória); o ERP **importa** a guia |
| 4. Título | **Contas a pagar** | O título do FGTS **nasce da integração da folha** quando o retorno volta (Q252-7, D-N697), com o **vencimento previsto** do parâmetro (dia 20, C374), e a provisão é revertida contra o contas a pagar, como no INSS (Contabilidade & Fiscal, seção 22.4.2). A **guia** do FGTS Digital, quando chega, **liga-se a esse título** (R16). A diferença entre o título (ou a guia) e a provisão vira **pendência para o contador** e fica numa conta de diferença; nunca é absorvida em silêncio |
| 5. Pagamento | **Tesouraria e motor bancário** | Paga **só o Pix da guia**, até as **21h59min59s do vencimento** (R100), e guarda o `E2eid` (R16). Não calcula nem monta guia |
| 6. Conferência | **Conciliação** | Compara a **provisão da folha**, o **retorno do eSocial**, a **guia** e o **valor pago**; diferença vai para tratamento (R11) |

**O circuito que você descreveu (Q252-2, D-N696).** O FGTS **nasce na folha**, é **enviado ao eSocial pela folha**, o **retorno do FGTS volta para a folha** (fecha o circuito) e **da folha segue ao financeiro e à tesouraria** para pagamento, **por integração entre os módulos**. Quando a folha é **processada externamente**, o financeiro **importa um CSV**.

| Modo | Como o FGTS chega ao financeiro |
|---|---|
| **Folha feita no ERP** | (1) a folha calcula e lança a provisão; (2) a camada eSocial envia o evento (S-1200, S-2299, S-1299) com origem na **apuração da folha** (`Mov_Esocial_Evento`, `Origem_Tipo` = `mov_rh_folha_apuracao`); (3) o retorno (S-5003 e S-5013) **volta e fica ligado à apuração** pelo evento de origem (`ID_Evento_Esocial`), **sem campo novo**, e a folha o confere contra a provisão; (4) com o circuito fechado, a folha **entrega o FGTS ao contas a pagar** por integração, como já acontece com o INSS (gatilho S-5011); (5) a tesouraria e o motor bancário pagam o Pix |
| **Folha processada fora do ERP** | O ERP **não envia** o eSocial dessa folha (quem faz é a folha externa), mas **recebe o retorno por importação** (versão 7). O financeiro **importa o XML do S-5003** que a folha externa recebeu do eSocial (ou, sem o XML, um **CSV derivado do S-5003**, seção 3.8) e o título nasce do **lote importado** (R15, R20 e Q252-8, versão 7) |

**Leituras minhas:** (a) «o retorno volta para a folha» = o S-5003 e o S-5013 ficam visíveis e conferidos **na apuração da folha**, e a folha só entrega ao financeiro com o circuito fechado (retorno recebido e conferido, ou a divergência tratada); (b) o CSV é o da **folha externa**, e **não** o relatório da guia do FGTS Digital; (c) «financeiro» = contas a pagar (o título) e «tesouraria» = tesouraria e motor bancário (o pagamento). **Conflito com a minha recomendação anterior:** na Q252-1 eu recomendava que o título nascesse da **guia importada**; o seu circuito faz o título nascer da **integração da folha com o retorno**. Como o FGTS Digital **não tem API** e é a guia que traz o **Pix**, a **Q252-7** pergunta como a guia se encaixa.

**Versão 1, para registro: por que eu recomendava a guia, e não o S-5013, como gatilho do título** (diferente do INSS, em que o gatilho é o S-5011): (1) o manual diz que a guia **não depende do fechamento da folha**, e o S-5013 só vem com o fechamento (S-1299); (2) a guia **agrupa débitos** (mensal, rescisório, multa, consignado) e **não admite pagamento parcial** do que agrupa; (3) é a guia que traz **vencimento, valor com atualização e o Pix**; (4) o S-5003 e o S-5013 informam **base e depósito**, mas não o valor final a pagar. O retorno do eSocial serve para **conferir cedo**: quando chega, o ERP compara com a provisão e avisa a diferença **antes** de a guia existir.

**Mudança no texto existente (se aprovada):** o parágrafo 22.4.1 do documento 10 e a nota «FGTS Digital... não mudam» do documento 11 passam a dizer que a liquidação da folha **não gera mais título de FGTS**, só provisão. O título nasce quando o retorno volta e a folha o entrega ao contas a pagar (Q252-7, D-N697); o vencimento do título é o **previsto** pelo parâmetro `Cad_Rh_Parametro_Vencimento_Encargo` (dia 20), e o **vencimento da guia** que se liga a ele **confere** o previsto (diferença vira alerta, R3).

## 3.2 O retorno do eSocial: `Mov_Esocial_Retorno_Fgts` (20 campos na versão 1; **22** com a Q252-9) e `Mov_Esocial_Retorno_Fgts_Valor` (12 campos)

Um registro por retorno recebido: o **S-5003** (por trabalhador, estabelecimento e lotação, depois de cada evento de remuneração ou desligamento) ou o **S-5013** (consolidado do período, depois do fechamento). Segue o padrão do `Mov_Esocial_Retorno`: o retorno novo da mesma chave **substitui** o anterior, sem apagá-lo.

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Retorno_Fgts` | identificador | |
| `ID_Empresa` | referência (Cad_Empresa) | O empregador (matriz) |
| `ID_Tipo_Evento` | referência (Cad_Classe_Sistema, domínio `tipo_evento_esocial`) | **S-5003** ou **S-5013** (dois valores novos do domínio, que é aberto) |
| `Periodo_Apuracao` | competência | `perApur` |
| `ID_Vinculo` | referência (Cad_Vinculo_Emprego), opcional | Só no S-5003 (um por contrato); vazio no S-5013 |
| `ID_Estabelecimento_Esocial` | referência (Cad_Rh_Estabelecimento_Esocial), opcional | O estabelecimento do S-5003; vazio no S-5013 consolidado |
| `Numero_Recibo_Base` | texto (60) | O recibo do evento de origem, como veio |
| `ID_Evento_Esocial` | referência (Mov_Esocial_Evento), opcional | O evento enviado que originou o retorno, achado pelo recibo |
| `Situacao_Vigencia` | enumeração {vigente, substituido} | `substituido` quando chega retorno posterior da mesma chave |
| `ID_Retorno_Anterior` | referência (Mov_Esocial_Retorno_Fgts, autorreferência), opcional | O retorno que este substitui |
| `Valor_Base_Fgts` | número | Base de cálculo do FGTS informada pelo eSocial |
| `Valor_Deposito_Fgts` | número | O depósito (FGTS devido) informado pelo eSocial |
| `Data_Vencimento_Fgts` | data, opcional | O `dtVenc` do S-5003, que o eSocial **só informa para períodos anteriores ao FGTS Digital** (dia 7); **vazio** nos demais e no S-5013 (versão 4; o vencimento vem do parâmetro e da guia) |
| `Valor_Provisao_Folha` | número, opcional | A provisão de FGTS que a folha lançou para a mesma chave. **Calculada** na conciliação, não digitada |
| `Valor_Diferenca_Provisao` | número, opcional | O valor oficial menos a provisão; acima da tolerância marca o retorno como divergente |
| `Origem_Recebimento` | enumeração {consulta_webservice, importacao_manual} | Como o retorno chegou (igual ao `Mov_Esocial_Retorno`) |
| `Data_Hora_Recebimento` | data/hora | |
| `Xml_Retorno` | texto | O retorno **inteiro, como recebido** (as bases por categoria e por lotação ficam aqui, e não em colunas) |
| `Situacao_Conciliacao` | enumeração {nao_conferido, conferido, divergente} | Resultado da comparação com a folha |
| `Data_Hora_Conciliacao` | data/hora, opcional | |

**Leiaute conferido nos esquemas XSD S-1.3 (versão 4).** Li `evtBasesFGTS.xsd` (S-5003) e `evtFGTS.xsd` (S-5013), idênticos nos três pacotes que você enviou. Estrutura (grupos entre colchetes: ocorrência):

**S-5003, informações do FGTS por trabalhador (`evtBasesFGTS`)**

| Grupo e tags | O que é |
|---|---|
| `ideEvento`: `nrRecArqBase`, `indApuracao` {1 mensal, 2 anual}, `perApur` | `nrRecArqBase` é o **recibo do evento de origem** (S-1200, S-2299, S-2399 ou S-3000), 23 caracteres |
| `ideEmpregador`, `ideTrabalhador`: `cpfTrab` | O empregador e o **CPF** do trabalhador |
| `infoFGTS`: `dtVenc` [0..1], `classTrib` [0..1] | `dtVenc` **só para período anterior ao FGTS Digital** (dia 7); `classTrib` só 04 (MEI) e 22 (segurado especial) |
| `ideEstab` [1..n] e `ideLotacao` [1..n] | Estabelecimento (`tpInsc`, `nrInsc`) e lotação (`codLotacao`, `tpLotacao`, `tpInsc`, `nrInsc`): **um retorno pode ter vários** |
| `infoTrabFGTS` [1..99] | `matricula`, `codCateg`, `categOrig`, `tpRegTrab`, `remunSuc`, `dtDeslig`, `mtvDeslig`, `dtTerm`, `mtvDesligTSV` e `sucessaoVinc` (a sucessão de vínculo) |
| `infoBaseFGTS` > `basePerApur` [0..99] | **`tpValor`** (30 códigos da Tabela 23), `indIncid` {1 normal, 9 suspensa por decisão judicial}, **`remFGTS`** (base), **`dpsFGTS`** (**depósito histórico**), `notAFT`, `natRubr`, `detRubrSusp` |
| `infoBaseFGTS` > `infoBasePerAntE` [0..180] > `basePerAntE` [1..99] | Período anterior: `perRef`, `tpAcConv` {E conversão de licença saúde em acidente, H base anterior ao FGTS Digital, I sentença judicial}, `tpValorE`, `indIncidE`, `remFGTSE`, `dpsFGTSE`, `detRubrSusp` |
| `procCS` [0..1], `eConsignado` [0..n] | `procCS`: processo judicial que suspende a contribuição social rescisória (`nrProcJud`). `eConsignado`: `instFinanc`, `nrContrato`, **`vreConsignado`** (desconto do eConsignado) |

**S-5013, informações do FGTS consolidadas por contribuinte (`evtFGTS`)**

| Grupo e tags | O que é |
|---|---|
| `ideEvento`: `indApuracao`, `perApur`; `ideEmpregador` | Como no S-5003 (**sem** `dtVenc`) |
| `infoFGTS`: `nrRecArqBase`, `indExistInfo` {1 há informações, 2 há movimento sem FGTS, 3 sem movimento} | `nrRecArqBase` é o **recibo do S-1299** (o fechamento) |
| `ideEstab` [0..n] > `ideLotacao` [1..n] > `infoBaseFGTS` | **Por estabelecimento e lotação**, não um total único da empresa |
| `basePerApur` [0..99] | `tpValor` (inclui o **19**, avulso não portuário), `indIncid`, **`baseFGTS`**, **`vrFGTS`** (depósito), `notAFT`, `natRubr`. Pelo esquema, `vrFGTS` e `baseFGTS` são a **soma dos `dpsFGTS` e `remFGTS` do S-5003**, por `tpValor` (no 19, 8% sobre a base do S-1270) |
| `infoBasePerAntE` [0..180] | Igual ao do S-5003 (E, H, I), sem o detalhe de rubrica suspensa |

**O que o `tpValor` diz (Tabela 23, no esquema):** 11 e 15, FGTS mensal (e aprendiz); 12 e 16, 13º salário; 21 e 27, mês da rescisão; 22 e 28, 13º rescisório; 23 e 29, aviso prévio indenizado; 13, 14, 17, 18, 24, 25, 26, 30, 31 e 32, os mesmos para **períodos anteriores**; 41 a 50, indenização compensatória do empregado doméstico; 19, avulso não portuário (só no S-5013). É esse código que **separa** o que a guia agrupa (mensal, rescisório) e o que a multa de 40% não alcança.

**O que isso muda no desenho:** (a) o **vencimento** não vem do eSocial (primeiro achado da versão 4); (b) o **depósito vem por tipo de valor**, mas o retorno da versão 1 guarda só o total (`Valor_Base_Fgts` e `Valor_Deposito_Fgts`): **sem o detalhe não dá para conferir o retorno contra cada débito da guia**; (c) o retorno é **por estabelecimento e lotação**, e o cabeçalho tem só um `ID_Estabelecimento_Esocial` opcional; (d) faltam no cabeçalho dois campos que o `Mov_Esocial_Retorno` já tem: o **indicador de apuração** (mensal ou anual) e a **existência de informação** (`indExistInfo`); (e) `eConsignado` e `procCS` ficam no XML guardado (o consignado entra na guia consignado, que o desenho já prevê).

**Aprovado na versão 5 (Q252-9, D-N702; aplicado na revisão 60, D-N706):**

| Onde | O que entra |
|---|---|
| `Mov_Esocial_Retorno_Fgts` (20 para 22 campos) | `Indicador_Apuracao` (enumeração {mensal, anual}, o `indApuracao`) e `Existencia_Informacao` (enumeração {com_informacao, movimento_sem_fgts, sem_movimento}, o `indExistInfo`, só no S-5013) |
| **Entidade nova** `Mov_Esocial_Retorno_Fgts_Valor` (12 campos, sem vigência) | Uma linha por **estabelecimento, lotação, tipo de valor, incidência e período anterior** do retorno: `ID_Retorno_Fgts_Valor`; `ID_Retorno_Fgts` (referência); `ID_Estabelecimento_Esocial` (referência, opcional); `Codigo_Lotacao` (texto 30, opcional); `Codigo_Tipo_Valor` (número, o `tpValor` ou `tpValorE`); `Categoria_Valor` (enumeração {mensal, decimo_terceiro, rescisao, decimo_terceiro_rescisorio, aviso_previo_indenizado, indenizacao_domestico, avulso_nao_portuario}, calculada do código); `Periodo_Anterior` (verdadeiro ou falso); `Periodo_Referencia` (competência, opcional, o `perRef`); `Tipo_Instrumento_Periodo_Anterior` (enumeração {conversao_licenca_acidente, base_anterior_fgts_digital, sentenca_judicial}, opcional, o `tpAcConv`); `Indicativo_Incidencia` (enumeração {normal, suspensa_decisao_judicial}); `Valor_Base`; `Valor_Deposito` |
| Totais do cabeçalho | `Valor_Base_Fgts` e `Valor_Deposito_Fgts` passam a ser a **soma das linhas** (conferência de consistência) |
| Com isto | **1.277 entidades (+7) e 15.032 campos (+88)**, **22 campos de referência a mais** (3.804); nenhuma entidade com vigência; **2 valores de enumeração** no domínio como antes |

**O vínculo com a folha (D-N696).** O retorno volta à folha pelo evento enviado: `Mov_Esocial_Evento.Origem_Tipo` aceita `mov_rh_folha_apuracao` e `ID_Origem` guarda o `ID_Apuracao` (conferi no modelo); o `ID_Evento_Esocial` do retorno aponta para esse evento. Por isso **não preciso de campo novo** para «voltar para a folha»: a folha mostra os retornos da sua apuração por essa cadeia.

**Como o retorno chega (Manual de Orientação do Desenvolvedor 1.15, abril de 2025; R17).** (1) O **identificador** do S-5003 e do S-5013 é gerado pelo eSocial: `ID` + código do evento (**`003`** e **`013`**) + **31 posições formadas a partir do número do recibo do evento que o gerou** (o seu CSV confirma `003 gov` para o S-5003); pelo XSD, o recibo de origem é o do S-1200, S-2299, S-2399 ou S-3000 (S-5003) e o do **S-1299** (S-5013). **O manual não diz como as 31 posições são preenchidas a partir do recibo de 21 dígitos**; por isso **montar o ID** a partir de `Mov_Esocial_Evento.Numero_Recibo` é uma **otimização a validar na produção restrita**, e o caminho seguro é a **consulta de identificadores** (tipo do evento e período de apuração). (2) O **download** (`SolicitarDownloadEventosPorId`, até **50 identificadores por chamada**) e a **consulta de identificadores** (por tipo de evento e período de apuração) exigem **certificado**, mas **não exigem procuração**. (3) **Limites do webservice:** **10 acessos por dia** somando consulta e download, **nenhuma solicitação entre os dias 1 e 7 de cada mês**, **uma por vez** (sem paralelismo) e só eventos recebidos **há mais de uma hora**. (4) O manual descreve o retorno de totalizadores **dentro do resultado do lote** só para S-5001, S-5002, S-5011 e S-5012; **não diz** o mesmo do S-5003 e do S-5013 (leitura minha: no FGTS, o caminho é o download). **Efeito:** a importação manual do XML (`importacao_manual`) deixa de ser só alternativa e vira **contingência prevista** para os dias 1 a 7 e para o fim da cota. Nenhum campo novo.

## 3.3 A guia: `Mov_Fgts_Guia` (16 campos) e `Mov_Fgts_Guia_Debito` (9 campos)

A **Guia Rápida** (mensal, rescisória, consignado e mista) e a **Guia Parametrizada** (o usuário escolhe os débitos) saem do FGTS Digital. Uma guia **agrupa** vários débitos e **não admite pagamento parcial** do que agrupa; por isso a guia é uma tabela e os débitos são a outra, como o DARF e os seus itens (`Mov_Dctfweb_Darf_Item`).

**`Mov_Fgts_Guia`**

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Fgts_Guia` | identificador | |
| `ID_Empresa` | referência (Cad_Empresa) | |
| `Tipo_Guia` | enumeração {rapida_mensal, rapida_rescisoria, rapida_consignado, rapida_mista, parametrizada} | O tipo que o FGTS Digital emitiu |
| `Numero_Guia` | texto (40) | O número da guia, como veio; **único por empresa** (R2) |
| `Data_Hora_Emissao` | data/hora | |
| `Data_Vencimento` | data | O vencimento **da guia** (manda sobre o parâmetro, R3) |
| `Valor_Total` | número | O valor integral a pagar |
| `Valor_Atualizacao_Mora` | número, opcional | A parte de atualização, multa e juros de mora, quando a guia é paga em atraso (a **contabilização** depende do contador, seção 7) |
| `Pix_Copia_E_Cola` | texto | O Pix copia e cola da guia (ou o texto do QR Code); é o que o motor bancário paga (R89 e R100) |
| `Url_Payload_Pix` | texto, opcional | O endereço do payload, quando a guia traz |
| `Situacao_Guia` | enumeração {emitida, paga, vencida, substituida, cancelada} | `substituida` quando a guia foi **refeita** (por exemplo, desligamento com saque entre os dias 1 e 9): o ERP **não paga** a guia substituída (R5) |
| `ID_Fgts_Guia_Substituida` | referência (Mov_Fgts_Guia, autorreferência), opcional | A guia que esta refez |
| `Origem_Importacao` | enumeração {relatorio_csv, digitacao} | Como a guia entrou no ERP (não há API, seção 1) |
| `ID_Remessa_Bancaria_Item` | referência (Mov_Remessa_Bancaria_Item), opcional | O item de Pix que pagou a guia |
| `Situacao_Conciliacao` | enumeração {nao_conferido, conferido, divergente} | Guia contra retorno do eSocial, provisão e pago |
| `Data_Hora_Importacao` | data/hora | Quando a guia entrou no ERP |

**`Mov_Fgts_Guia_Debito`**

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Fgts_Guia_Debito` | identificador | |
| `ID_Fgts_Guia` | referência (Mov_Fgts_Guia) | |
| `Tipo_Debito` | enumeração {mensal, decimo_terceiro, rescisorio, indenizacao_compensatoria, consignado, outro} | A natureza do débito agrupado |
| `Competencia` | competência, opcional | Vazio na multa rescisória sem competência |
| `ID_Vinculo` | referência (Cad_Vinculo_Emprego), opcional | O colaborador, nos débitos rescisórios e na multa; vazio no mensal consolidado |
| `Valor_Debito` | número | O valor do débito dentro da guia |
| `Situacao_Multa` | enumeração {completo, incompleto, saldo_rescisorio}, opcional | Só em `indenizacao_compensatoria`: como o FGTS Digital marca a multa (completa, incompleta ou saldo rescisório, conforme o método) |
| `ID_Titulo` | referência (Mov_Titulo), opcional | O título do FGTS ao qual este débito se liga (seção 3.1 e R16) |
| `ID_Retorno_Fgts` | referência (Mov_Esocial_Retorno_Fgts), opcional | O retorno do eSocial que sustenta o débito, quando houver |

## 3.4 O histórico de remunerações e o arquivo do Anexo I

Para **admitidos antes de 01/03/2024** com desligamento, o FGTS Digital só calcula a multa se o empregador informar **todas as remunerações** (Método 1, recomendável) ou a **base rescisória** (Método 2, seção 3.5). A importação em lote usa o **Anexo I (versão 1.2, de 03/10/2025)**: arquivo TXT ou CSV com ponto e vírgula, **até 5.000 linhas ou 130 KB**, linha tipo 1 (trabalhador) e tipo 2 (remuneração por competência); só competências **anteriores a 03/2024**; o trabalhador precisa ter o **desligamento já no eSocial**; **um erro em qualquer trabalhador rejeita o arquivo inteiro**; a competência que já existe é substituída.

**`Mov_Rh_Fgts_Historico_Remuneracao` (7 campos):** uma linha por contrato e competência.

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Historico_Remuneracao` | identificador | |
| `ID_Vinculo` | referência (Cad_Vinculo_Emprego) | |
| `Competencia` | competência | Só anteriores a 03/2024 vão ao Anexo I |
| `Valor_Remuneracao_Fgts` | número | A remuneração da competência, na moeda vigente nela (URV de março a junho de 1994) |
| `Origem_Historico` | enumeração {folha_erp, migracao, digitacao} | `folha_erp`: tirada da folha do ERP; `migracao`: do sistema anterior; `digitacao`: lançada à mão |
| `ID_Apuracao` | referência (Mov_Rh_Folha_Apuracao), opcional | A apuração de origem, quando `folha_erp` |
| `ID_Arquivo_Historico` | referência (Mov_Rh_Fgts_Arquivo_Historico), opcional | O arquivo do Anexo I em que a linha foi enviada |

**`Mov_Rh_Fgts_Arquivo_Historico` (9 campos):** um registro por arquivo gerado. Como **um erro rejeita o arquivo todo**, o ERP **divide** em arquivos de até 5.000 linhas e 130 KB e **valida antes** de gerar.

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Arquivo_Historico` | identificador | |
| `ID_Empresa` | referência (Cad_Empresa) | |
| `Data_Hora_Geracao` | data/hora | |
| `Quantidade_Trabalhadores` | número | Linhas tipo 1 |
| `Quantidade_Linhas` | número | Todas as linhas (limite de 5.000) |
| `Tamanho_Bytes` | número | Limite de 130 KB |
| `Conteudo_Arquivo` | texto | O arquivo gerado, para reenviar |
| `Situacao_Arquivo` | enumeração {gerado, enviado_ao_portal, aceito, rejeitado} | O usuário marca o envio ao portal (não há API) |
| `Mensagem_Rejeicao` | texto, opcional | O motivo que o portal devolveu |

## 3.5 A rescisão: `Mov_Rh_Fgts_Rescisao` (13 campos)

Um registro por **desligamento**, que junta o método da multa, o que foi pedido à Caixa, a **multa estimada pelo ERP** e a **multa oficial** do FGTS Digital. As quatro situações do documento 250 (seção 3.17.4) ficam assim:

| Situação | Método | O que o ERP faz |
|---|---|---|
| Admitido a partir de 03/2024 | `automatico` | O FGTS Digital calcula sozinho; o ERP só **estima e confere** |
| Admitido antes, com histórico completo na folha | `metodo_1_historico` | O ERP **gera o arquivo do Anexo I** (seção 3.4); o FGTS Digital calcula |
| Admitido antes, sem histórico completo | `metodo_2_base_caixa` | O RH **pede à Caixa** a base para fins rescisórios (integral, nunca só a diferença) e o ERP guarda valor, data e referência |
| Estimativa do ERP | (em todas) | Soma depósitos apurados mais atualização, **marcada como estimativa**, para a provisão e a pré-visualização da rescisão |

| Campo | Tipo | Regra |
|---|---|---|
| `ID_Fgts_Rescisao` | identificador | |
| `ID_Vinculo` | referência (Cad_Vinculo_Emprego) | O contrato desligado; **um registro por desligamento** |
| `Metodo_Multa` | enumeração {automatico, metodo_1_historico, metodo_2_base_caixa} | Pela data de admissão e pelo histórico (tabela acima) |
| `Valor_Base_Rescisoria_Caixa` | número, opcional | Método 2: a base **integral** pedida à Caixa; **não pode ser menor** que o FGTS devido atualizado desde 03/2024 (validação) |
| `Data_Base_Rescisoria` | data, opcional | A data a que a base se refere |
| `Data_Pedido_Caixa` | data, opcional | Quando o RH pediu |
| `Referencia_Pedido_Caixa` | texto (200), opcional | Protocolo, e-mail ou nome do arquivo recebido |
| `ID_Arquivo_Historico` | referência (Mov_Rh_Fgts_Arquivo_Historico), opcional | Método 1: o arquivo em que o histórico do contrato foi enviado |
| `Valor_Multa_Estimada` | número, opcional | A estimativa do ERP (`Percentual_Multa_Fgts` do motivo do desligamento); **sempre rotulada estimativa** |
| `Valor_Multa_Fgts_Digital` | número, opcional | A multa oficial, quando a guia traz |
| `ID_Fgts_Guia_Debito` | referência (Mov_Fgts_Guia_Debito), opcional | O débito de indenização compensatória que a guia trouxe |
| `Situacao_Conferencia` | enumeração {nao_conferido, conferido, divergente} | Estimativa contra multa oficial |
| `Data_Hora_Conferencia` | data/hora, opcional | |

## 3.6 Mudanças em entidades que já existem (só valores, nenhum campo)

| Onde | O que entra |
|---|---|
| `Mov_Titulo.Origem_Tipo` | **um valor novo, `folha_externa`** (Q252-10, D-N705): o título do FGTS da **folha processada fora do ERP** nasce do lote importado e o `ID_Origem` aponta `Mov_Rh_Folha_Externa_Lote`. O `folha_pagamento` **continua** para a folha feita no ERP (`ID_Origem` = apuração) e para o FGTS dela (Q252-7, D-N697); a guia se liga ao título pelo `ID_Titulo` do débito (o valor `fgts_guia_debito` da versão 1 **saiu**) |
| `Mov_Lote_Lancamento.Origem_Tipo` | **nenhum valor novo**: a reversão da provisão do FGTS usa `reversao_provisao_encargos_folha`, o mesmo do INSS e do IRRF |
| Domínio `tipo_evento_esocial` (`Cad_Classe_Sistema`) | valores **`S-5003` e `S-5013`** (domínio aberto, é dado de carga, não mudança de estrutura) |
| `Mov_Esocial_Evento.Origem_Tipo` | **nada**: o S-5003 e o S-5013 são retorno, não evento enviado |

## 3.7 Leituras e alertas (sem tabela)

- **Painel do FGTS do mês:** provisão da folha, retorno do eSocial, guia e pago, lado a lado, com a diferença de cada par.
- **Guia a vencer** e **guia vencida sem pagamento** (alerta), usando o vencimento da guia.
- **Guia refeita:** quando chega guia nova para a mesma competência e a anterior está `emitida`, o ERP a marca `substituida` e **bloqueia** o pagamento da antiga (R5).
- **Multa na pré-visualização da rescisão**, sempre com o rótulo «estimativa» e, depois da guia, a diferença para a multa oficial.
- **Admitidos antes de 03/2024 sem histórico completo:** lista para o RH pedir a base à Caixa.

## 3.8 Folha processada fora do ERP: importar o XML do S-5003 e o CSV derivado dele (versão 7, Q252-8)

**O que você pediu (Q252-8):** «considerar importar o XML do S-5003 e usar este para gerar um layout do csv». **Leitura minha:** (a) o caminho principal é **importar o XML do S-5003** (e, se houver, do S-5013) que a folha externa recebeu do eSocial; (b) o **CSV** tem o leiaute **derivado do esquema do S-5003** (`evtBasesFGTS.xsd`, seção 3.2), com as mesmas colunas de negócio, e serve quando o XML não está à mão; (c) os dois caminhos **caem nas mesmas tabelas do retorno** (3.2), então a conferência por tipo de valor (R18) e a ligação da guia ao título (R16) **não mudam**. **Mudança em relação à minha recomendação anterior:** eu tinha dito que, nesse modo, o ERP **não receberia** o S-5003 e o S-5013; **agora recebe**, por importação (a importação manual do XML já existia como contingência, R17).

| | **XML do S-5003** (principal) | **CSV derivado** (alternativa) |
|---|---|---|
| Quem entrega | O responsável pela folha externa (arquivo ou pasta compactada com um XML por trabalhador) | O mesmo responsável, em planilha exportada com o leiaute abaixo |
| O que o ERP faz | Valida a estrutura contra o esquema S-1.3 e grava o **XML inteiro** em `Xml_Retorno`, mais as linhas por tipo de valor (`Mov_Esocial_Retorno_Fgts_Valor`) | Lê as linhas, confere (R20) e grava as **mesmas linhas por tipo de valor**; **sem XML** (o campo fica vazio) |
| `Origem_Recebimento` | `importacao_manual` (já existe) | `importacao_csv` (**valor novo**, Q252-10) |
| O que se perde | Nada | As tags que o CSV não leva: `classTrib`, `dtVenc`, `sucessaoVinc`, `notAFT`, `natRubr`, `detRubrSusp`, `procCS`, `eConsignado` e os dados do desligamento. **Não mudam o valor do título**; só o XML as guarda |
| Duplicidade | Pelo **recibo** (`nrRecArqBase`) e pela chave do retorno | Pelo **hash do arquivo** e pela chave da linha (R20) |

**Leiaute do CSV (14 colunas, tiradas do esquema).** Arquivo **UTF-8**, separador **ponto e vírgula**, **primeira linha com os nomes das colunas** exatamente como abaixo (os nomes são os das tags do esquema), **uma linha por valor** (cada `basePerApur` ou `basePerAntE`/`basePerAntE` do XML vira uma linha, repetindo as colunas de identificação), **decimal com ponto** e sem separador de milhar, datas e competências como no XML (`AAAA-MM`), CPF e CNPJ **sem máscara**.

| Nº | Coluna | Tag de origem no S-5003 | Obrigatória | Formato | O que o ERP faz |
|---|---|---|---|---|---|
| 1 | `perApur` | `ideEvento/perApur` | Sim | `AAAA-MM` (`AAAA` se anual) | `Periodo_Apuracao` do retorno; tem de ser a competência escolhida na importação |
| 2 | `indApuracao` | `ideEvento/indApuracao` | Não (padrão 1) | 1 mensal, 2 anual | `Indicador_Apuracao` |
| 3 | `nrInsc_empregador` | `ideEmpregador/nrInsc` | Sim | 8 caracteres (raiz do CNPJ, como no XML) | Acha a empresa (`Cad_Empresa`) |
| 4 | `cpfTrab` | `ideTrabalhador/cpfTrab` | Sim | 11 dígitos | Acha o vínculo do trabalhador na competência |
| 5 | `matricula` | `infoTrabFGTS/matricula` | Só se o CPF tiver mais de um vínculo na competência | Texto, até 30 | Desempata o vínculo |
| 6 | `nrInsc_estab` | `ideEstab/nrInsc` | Sim, quando a empresa tem mais de um estabelecimento | 11 a 14 caracteres | Acha o `Cad_Rh_Estabelecimento_Esocial` |
| 7 | `codLotacao` | `ideLotacao/codLotacao` | Não | Texto, até 30 | `Codigo_Lotacao` |
| 8 | `tpValor` | `basePerApur/tpValor` ou `basePerAntE/basePerAntE/tpValorE` | Sim | Número, da lista da seção 3.2 | `Codigo_Tipo_Valor` e `Categoria_Valor` |
| 9 | `indIncid` | `indIncid` ou `indIncidE` | Sim | 1 normal, 9 suspensa por decisão judicial | `Indicativo_Incidencia` |
| 10 | `remFGTS` | `remFGTS` ou `remFGTSE` | Sim | Decimal, 2 casas | `Valor_Base` |
| 11 | `dpsFGTS` | `dpsFGTS` ou `dpsFGTSE` | **Sim no CSV** (no XML é opcional) | Decimal, 2 casas | `Valor_Deposito`; **é o que forma o título** |
| 12 | `perRef` | `infoBasePerAntE/perRef` | Só em período anterior | `AAAA-MM` | `Periodo_Referencia` |
| 13 | `tpAcConv` | `infoBasePerAntE/tpAcConv` | Só em período anterior | E, H ou I | `Tipo_Instrumento_Periodo_Anterior` (3.2) |
| 14 | `nrRecArqBase` | `ideEvento/nrRecArqBase` | Não | 23 caracteres | `Numero_Recibo_Base`; vazio fica vazio |

**Exemplo (dados fictícios, só para mostrar a forma):**

```
perApur;indApuracao;nrInsc_empregador;cpfTrab;matricula;nrInsc_estab;codLotacao;tpValor;indIncid;remFGTS;dpsFGTS;perRef;tpAcConv;nrRecArqBase
2026-10;1;12345678;11122233396;1001;12345678000195;ADM;11;1;3500.00;280.00;;;
2026-10;1;12345678;11122233396;1001;12345678000195;ADM;12;1;1750.00;140.00;;;
2026-10;1;12345678;44455566677;1002;12345678000195;OBRA1;11;1;2800.00;224.00;;;
2026-10;1;12345678;44455566677;1002;12345678000195;OBRA1;13;1;900.00;72.00;2026-04;H;
```

(As linhas 1 e 2 são o mensal e o 13º do mesmo trabalhador; a linha 4 é um período anterior, `tpValor` 13 com `perRef` e `tpAcConv`.)

**O lote importado (aprovado na versão 8, Q252-10, D-N705; aplicado na revisão 60, D-N706).** Para guardar **o que foi importado, por quem, e as ocorrências da conferência**, e para o título ter de onde nascer, proponho (no padrão de `Mov_Escrituracao_Arquivo` e sua ocorrência):

| Onde | O que entra |
|---|---|
| **Entidade nova** `Mov_Rh_Folha_Externa_Lote` (14 campos, sem vigência) | `ID_Lote_Folha_Externa`; `ID_Empresa` (referência, `Cad_Empresa`); `Competencia` (competência); `Formato_Arquivo` (enumeração {xml_s5003, csv_leiaute_s5003}); `Nome_Arquivo` (texto 200; nome do arquivo ou da pasta compactada); `Hash_Arquivo` (texto 64, SHA-256, para barrar o mesmo arquivo duas vezes); `Quantidade_Registros` (número); `Valor_Total_Base`; `Valor_Total_Deposito`; `Situacao` (enumeração {importado, com_ocorrencia, conferido, titulo_gerado, cancelado}); `ID_Titulo` (referência, `Mov_Titulo`, opcional); `ID_Usuario_Importacao` (referência, `Cad_Usuario`); `Data_Hora_Importacao`; `Data_Hora_Conferencia` (opcional) |
| **Entidade nova** `Mov_Rh_Folha_Externa_Lote_Ocorrencia` (8 campos, sem vigência) | Uma linha por problema achado na conferência: `ID_Lote_Ocorrencia`; `ID_Lote_Folha_Externa` (referência); `Numero_Linha` (número, opcional; no XML, a ordem do arquivo); `Codigo_Ocorrencia` (enumeração {arquivo_duplicado, empresa_divergente, competencia_divergente, cpf_nao_encontrado, vinculo_ambiguo, tipo_valor_invalido, valor_invalido, chave_repetida, estabelecimento_nao_encontrado, xml_fora_do_esquema}); `Nome_Campo` (texto 60, opcional); `Valor_Informado` (texto 100, opcional); `Mensagem` (texto 255); `Situacao_Tratamento` (enumeração {aberta, tratada}; o tratamento segue a R7) |
| `Mov_Esocial_Retorno_Fgts` (22 para **23** campos) | `ID_Lote_Folha_Externa` (referência, opcional): de qual lote o retorno veio; vazio quando o retorno veio da folha do ERP. E `Numero_Recibo_Base` passa a poder ficar **vazio** (CSV sem recibo) |
| Valores de enumeração (**1 novo** em entidade que já existe) | **`folha_externa`** em `Mov_Titulo.Origem_Tipo` (o `ID_Origem` aponta o lote; o valor `folha_pagamento` aponta a apuração da folha do ERP e não serve aqui). O `importacao_csv` em `Origem_Recebimento` **não conta aqui**: o retorno é entidade nova e o valor já está nos campos dela. Com este, o documento tem **3 valores em entidades que já existem** (os 2 do domínio `tipo_evento_esocial` e este) |
| Com isto | **1.279 entidades (+2) e 15.055 campos (+23)**, **5 campos de referência a mais** (3.809); nenhuma entidade com vigência |

# 4. Regras

- **R1.** **O título do FGTS nasce do valor oficial** (Q250-46, D-N692): a liquidação da folha lança **só a provisão**; o título nasce do valor oficial e a provisão é revertida contra o contas a pagar. **Quando** ele nasce: da **integração da folha** quando o retorno volta (Q252-7, aprovada, D-N697), e **não** da guia.
- **R2.** **Guia única por empresa e número.** Importar a mesma guia duas vezes devolve a que já existe (idempotência, R3 do documento 250).
- **R3.** **O vencimento da guia manda.** O parâmetro `Cad_Rh_Parametro_Vencimento_Encargo` serve à **previsão** e à **conferência**: vencimento diferente na guia vira alerta, nunca ajuste silencioso.
- **R4.** **Sem pagamento parcial.** A guia é paga **pelo valor integral**; o ERP bloqueia pagamento de valor diferente e o **segundo pagamento** do mesmo agrupamento (R3 do documento 250).
- **R5.** **Guia refeita substitui a anterior.** A guia substituída não é paga; o motor bancário **não paga guia com vencimento antigo** depois do desligamento (R14 do documento 250).
- **R6.** **Só o Pix da guia.** O pagamento é o Pix copia e cola ou QR Code da guia, até as **21h59min59s** do vencimento, **agendado** de preferência (R100).
- **R7.** **Quatro conferências, uma diferença por vez:** provisão contra retorno do eSocial, retorno contra guia, guia contra pago, multa estimada contra multa oficial. A diferença acima da tolerância abre tratamento (R11) e **nunca** é absorvida em silêncio.
- **R8.** **Retorno substitui retorno** da mesma chave, sem apagar o anterior (`Situacao_Vigencia`).
- **R9.** **Anexo I validado antes de gerado:** o ERP confere competências (todas anteriores a 03/2024), desligamento já enviado ao eSocial, 5.000 linhas e 130 KB, e **divide** o arquivo; erro em um trabalhador **não** é enviado ao portal junto com os demais.
- **R10.** **A base da Caixa é integral.** No Método 2, o valor guardado é a base **inteira**, e a validação recusa valor menor que o FGTS devido atualizado desde 03/2024.
- **R11.** **Estimativa sempre rotulada.** A multa do ERP é estimativa para provisão e pré-visualização; o valor que vale é o do FGTS Digital.
- **R12.** **Não há API do FGTS Digital** nos manuais lidos: guia, saldo e base rescisória entram por importação, digitação ou pedido à Caixa. Se a Caixa publicar API, entra como canal novo, sem mudar estas tabelas.
- **R13.** **Perfis (leitura minha, Q252-6):** o RH processa a folha, gera o Anexo I, pede a base à Caixa e acompanha o estado; o **Financeiro importa a guia e paga**; o RH vê o estado da guia, sem ver o contas a pagar.
- **R14.** **O circuito fecha na folha** (Q252-2, D-N696): com a folha feita no ERP, o retorno do eSocial (S-5003 e S-5013) volta e se liga à **apuração da folha** pelo evento de origem; a folha o confere contra a provisão e **entrega o FGTS ao contas a pagar por integração entre módulos**; a tesouraria paga. Retorno divergente ou ausente **bloqueia a entrega automática** e abre tratamento, nunca é ignorado (leitura minha).
- **R15.** **Folha processada fora do ERP** (Q252-2, D-N696; reescrita na versão 7, Q252-8, D-N704): o ERP **não envia** o eSocial dessa folha, mas **recebe o retorno por importação**: o financeiro **importa o XML do S-5003** (e do S-5013, se houver) que a folha externa recebeu, ou, sem o XML, um **CSV com o leiaute derivado do esquema do S-5003** (seção 3.8). Os dois caminhos gravam nas **mesmas tabelas do retorno** (3.2) e o **título nasce do lote importado** (R20). Nesse modo **não há provisão da folha do ERP** (`Valor_Provisao_Folha` fica vazio); a conferência é **retorno contra guia** (R18 e R16) e **S-5013 contra a soma dos S-5003** do período. A estrutura do lote está **aprovada** (Q252-10, D-N705).
- **R16.** **A guia se liga ao título** (Q252-7, D-N697): a guia do FGTS Digital (importada em CSV ou digitada) liga-se ao título já criado pela folha (mesma empresa, competência e natureza `fgts`; no rescisório, o mesmo vínculo), **confere valor e vencimento** e traz o **Pix**. Guia sem título correspondente, ou valor ou vencimento diferentes, abre **alerta e tratamento** (R7), nunca ajuste silencioso; o acesso ao portal é do **Financeiro**.
- **R17.** **Retorno do FGTS pelo download do eSocial** (D-N700, leitura minha a partir do manual do desenvolvedor 1.15): o ERP **consulta os identificadores** do S-5003 e do S-5013 (tipo do evento e período de apuração; **montar o ID** a partir do recibo só depois de validado na produção restrita), pede o download em **lotes de até 50 IDs**, respeita **10 acessos por dia** (consulta e download somados), **não pede nos dias 1 a 7** e faz **uma solicitação por vez**, e só pede eventos recebidos **há mais de uma hora**. Fora da janela ou sem cota, o usuário **importa o XML** (`importacao_manual`). A cota é **controlada pelo ERP** (contador do dia) e o esgotamento vira alerta, nunca erro.
- **R18.** **Conferência por tipo de valor** (Q252-9, aprovada em D-N702): o ERP compara o retorno (`Mov_Esocial_Retorno_Fgts_Valor`) com a provisão e com os débitos da guia **por `Categoria_Valor`** (mensal, 13º, rescisão e demais), e o S-5013 com a soma dos S-5003 do mesmo período e `Tipo_Valor` (diferença vira tratamento, R7).
- **R19.** **Migração do histórico de remunerações** (Q252-3, D-N703): o ERP **recebe do sistema de folha atual todo o histórico desde a contratação** dos contratos **admitidos antes de 03/2024** (e ainda ativos; leitura minha) em `Mov_Rh_Fgts_Historico_Remuneracao` com `Origem_Historico` = `migracao`; a **competência a partir de 03/2024** vem da folha do ERP (`folha_erp`). Para esses contratos o **Método 1** (Anexo I, R9) é o **padrão** e o Método 2 (base pedida à Caixa) só entra se faltar competência (a lista de «sem histórico completo», seção 3.7, passa a ser exceção). A **conferência da migração** (competências sem buraco desde a admissão, valores por competência) acontece **antes** do primeiro Anexo I.
- **R20.** **Conferência do lote importado antes de gerar o título** (Q252-8, D-N704; leitura minha): (a) o **hash** do arquivo já importado e não cancelado **barra** a importação; (b) confere **empresa** (raiz do CNPJ), **competência** (a escolhida na importação), **CPF com vínculo** na competência (matrícula se houver mais de um), **estabelecimento**, **`tpValor` da lista** da seção 3.2, **valores** (base e depósito não negativos; `dpsFGTS` presente no CSV) e **chave repetida** no arquivo; (c) **qualquer ocorrência deixa o lote em `com_ocorrencia` e nada vira retorno nem título** (tudo ou nada: o usuário corrige o arquivo e importa de novo, ou trata a ocorrência pela R7); (d) sem ocorrência, o ERP **mostra o total por categoria** (`Categoria_Valor`) e, **confirmado**, grava os retornos (um por vínculo e estabelecimento, `Origem_Recebimento` conforme o caminho) e gera **um título `fgts` por empresa e competência** com a soma de `dpsFGTS` (`Origem_Tipo` = `folha_externa`, vencimento previsto do parâmetro, C374); (e) retorno novo da mesma chave de outro lote **substitui** o anterior sem apagá-lo (3.2); (f) a **guia** do FGTS Digital liga-se a esse título como na R16.

# 5. O que fica fora

- **FGTS do processo trabalhista** (S-5503, reclamatória): continua no desenho da reclamatória (`Mov_Rh_Processo_Trabalhista_*`).
- **Saldo da conta vinculada** de cada trabalhador: **não é consulta do empregador** no FGTS Digital; só a base rescisória pedida à Caixa (Método 2).
- **Conectividade Social e GRF/GRRF antigas:** substituídas pelo FGTS Digital; o campo `Identificador_Fgts` do item de tributo (documento 250) fica como está, para guias antigas.
- **Contabilização da multa e da mora:** depende do contador (seção 7); este documento só guarda os valores.
- **Estrutura de tags dos eventos S-5003 e S-5013:** o retorno guarda o XML inteiro; as colunas são as de negócio (Q252-5).
- **Outras naturezas da folha externa (líquido, INSS e IRRF)** (Q252-11, D-N705): **fora deste documento**; serão desenhadas na **integração da folha com o financeiro** (documento 259, número reservado), pelo mesmo método do 3.8, **com a sua condição**: importar o XML do que o eSocial devolve. **Já existe no modelo** a importação de XML dos totalizadores **S-5011 e S-5012** (`Mov_Esocial_Retorno`, `Origem_Recebimento` = `importacao_manual`, com o XML guardado); **não existe** a do **S-5001** (INSS) e do **S-5002** (IRRF) **por trabalhador**, que está nos mesmos pacotes de esquemas que você mandou e ainda **não li**; o **líquido não existe no eSocial** e só pode vir em CSV. Esse desenho é **pendência minha**, não pergunta sua; você me diz quando abrir.

# 6. Perguntas para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q252-1 | **(Substituída pela Q252-7 em 24/11/2026, D-N696: o seu circuito põe a folha como origem do título.)** **Quando o título do FGTS nasce:** (a) na **guia importada** do FGTS Digital, ou (b) na chegada do **S-5013** (como o INSS, no S-5011)? | **(a)**: a guia não depende do fechamento, traz o vencimento, o valor com atualização e o Pix, e agrupa débitos. O S-5003 e o S-5013 ficam para conferir cedo, antes da guia **Em D-N697 você seguiu as recomendações, e a desta pergunta conflita com a da Q252-7: prevalece a Q252-7 (confirmado em D-N698: «FGTS integração vem da folha»).** |
| Q252-2 | **Como a guia entra no ERP:** o relatório da guia sai do FGTS Digital em **PDF e CSV**; o ERP importa o **CSV** e o usuário confere pelo **Pix copia e cola**, ou a equipe **digita** a guia? Quem acessa o portal (certificado e perfil)? | Importar o CSV (digitação só como alternativa) e conferir o valor com o Pix copia e cola; o acesso ao portal é do **Financeiro**. **Respondida em 24/11/2026 (D-N696):** o FGTS nasce na folha, é enviado ao eSocial pela folha, o retorno volta para a folha e segue ao financeiro por integração; folha externa = CSV importado. A parte da **guia do portal** passa para a Q252-7 **Confirmada em D-N697.** |
| Q252-3 | **Histórico de remunerações anteriores a 03/2024:** o sistema de folha atual **tem** o histórico dos contratos ainda ativos e será **migrado** para `Mov_Rh_Fgts_Historico_Remuneracao`? Quantos admitidos antes de 03/2024 a Mlegate tem hoje? | Migrar o que existir (`Origem_Historico` = `migracao`); sem histórico completo, usar o Método 2 só para esses contratos **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** **Falta saber quantos admitidos antes de 03/2024 a Mlegate tem.** **Respondida em 24/11/2026 (D-N703): há admitidos antes de 03/2024 e o sistema atual guarda todo o histórico desde a contratação; migrar (R19). Falta só a quantidade (não bloqueia).** **Respondida em 24/11/2026 (D-N704): «seguir recomendação»** (leitura minha: a **quantidade** sai da própria migração, pela conferência da R19, que lista os contratos admitidos antes de 03/2024; você não precisa informá-la). **Q252-3 encerrada.** |
| Q252-4 | **Multa estimada na pré-visualização da rescisão:** mostrar sempre, **rotulada estimativa**, com a diferença para a multa oficial depois da guia? | Sim **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** |
| Q252-5 | **Retorno do eSocial:** o ERP **consulta o S-5003 e o S-5013 pelo webservice** (como o S-5011) ou o usuário **importa** o XML? Você consegue me mandar o **leiaute (XSD) S-1.3** desses dois eventos, ou posso buscar no portal do eSocial? As páginas que li não trazem as tags | Consulta pelo webservice, com importação manual como alternativa (já existe no S-5011); eu busco o XSD no portal gov.br/esocial e confiro as colunas (a base e o depósito podem virar mais de um campo) **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** **Falta o arquivo do leiaute (seção 10): tentei o portal e não obtive as tags.** **Leiaute recebido em 24/11/2026 (D-N701): os três pacotes XSD S-1.3; ver a seção 3.2.** |
| Q252-6 | **Quem faz o quê** (leitura minha, R13): RH processa, gera o Anexo I e pede a base à Caixa; **Financeiro importa a guia e paga**; o RH acompanha o estado. Confere? | Sim, igual à folha (R149 do documento 250) **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** |
| Q252-7 | **Como o título e a guia se encaixam no seu circuito (D-N696):** a folha entrega o FGTS ao contas a pagar quando o retorno volta; a guia do FGTS Digital (sem API) continua necessária para **pagar**, porque traz o **Pix**, o vencimento oficial e o valor atualizado. (a) O título nasce da **integração da folha com o valor do retorno**, com vencimento **previsto** pelo parâmetro (dia 20, C374), e a guia, importada em CSV ou digitada, **liga-se ao título**, confere valor e vencimento e traz o Pix; ou (b) o título nasce da **guia importada** (minha recomendação da versão 1) e o retorno só confere? E quem acessa o portal para a guia (certificado e perfil)? | **(a)**: é o seu circuito (a folha fecha com o retorno e entrega ao financeiro). A guia liga-se ao título pelo `ID_Titulo` do débito (já previsto) e a diferença entre título e guia vira alerta (R7), nunca ajuste silencioso. Acesso ao portal do **Financeiro**. Se for (a), o valor `fgts_guia_debito` de `Mov_Titulo.Origem_Tipo` deixa de ser necessário (de três valores de enumeração passam a dois) e eu acerto as contagens na versão 3 **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** |
| Q252-8 | **Folha processada fora do ERP (R15):** (a) o CSV traz **só o FGTS** ou **todas as naturezas** (líquido, INSS, IRRF, FGTS e demais)? (b) Você pode me mandar **um CSV de exemplo** (sem dados pessoais) e dizer **quando** isso acontece (uma filial, 13º, rescisões, tudo)? (c) Neste modo o eSocial é enviado pela folha externa, e o ERP **não** recebe o S-5003 e o S-5013: confere? | (a) **todas as naturezas**, no mesmo leiaute, para o financeiro não ter dois caminhos; (b) com o exemplo eu desenho o leiaute e a estrutura do lote importado na versão 3; (c) sim, e a conferência com o retorno não existe nesse modo, só a conferência do CSV **Respondida em 24/11/2026 (D-N697): seguir a recomendação.** (Faltava o CSV de exemplo; ver a resposta da versão 7, a seguir.) **Respondida em 24/11/2026 (D-N704): «considerar importar o XML do S-5003 e usar este para gerar um layout do csv».** O leiaute do CSV (14 colunas derivadas do esquema) está na **seção 3.8**; R15 reescrita e R20 nova. **O CSV de exemplo deixa de ser necessário.** O que o S-5003 não cobre (líquido, INSS e IRRF) virou a **Q252-11**. |
| Q252-9 | **Retorno por tipo de valor (D-N701; leitura dos XSD):** o retorno do FGTS traz o depósito **por tipo de valor** (mensal, 13º, rescisão, aviso prévio, período anterior e outros), por estabelecimento e lotação, e a guia agrupa por tipo de débito. Aprova (a) **+2 campos** no cabeçalho do retorno (`Indicador_Apuracao` e `Existencia_Informacao`) e (b) a **entidade nova `Mov_Esocial_Retorno_Fgts_Valor`** (12 campos) com as linhas por tipo de valor, para conferir o retorno contra cada débito da guia (R18)? Ou prefere manter só o total e o XML guardado? | **Sim aos dois**: sem o detalhe por tipo de valor o ERP só confere o **total** e não sabe dizer **qual débito** da guia diverge (mensal, 13º ou rescisório). Custo: +1 entidade e +14 campos (1.277 e 15.032 se tudo entrar) **Respondida em 24/11/2026 (D-N702): «Aprovo» (os dois itens).** |
| Q252-10 | **Estrutura do lote importado (seção 3.8; D-N704):** aprova (a) a **entidade nova `Mov_Rh_Folha_Externa_Lote`** (14 campos), (b) a **entidade nova `Mov_Rh_Folha_Externa_Lote_Ocorrencia`** (8 campos), (c) **+1 campo** no retorno (`ID_Lote_Folha_Externa`) com o recibo podendo ficar vazio, e (d) os **valores de enumeração** `importacao_csv` (origem do retorno) e `folha_externa` (`Mov_Titulo.Origem_Tipo`)? Ou prefere um desenho mais leve (por exemplo, sem a entidade de ocorrência)? | **Sim aos quatro**: sem o lote não há como barrar o mesmo arquivo duas vezes, mostrar onde está o erro nem dizer de qual importação nasceu cada título. Custo: +2 entidades, +23 campos e 3 valores de enumeração (1.279 / 15.055 / 3.809 se tudo entrar). Só a entidade de ocorrência é dispensável (os erros ficariam só na tela e se perderiam ao fechar) **Respondida em 24/11/2026 (D-N705): «seguir recomendação».** Aprovados os quatro itens. **Correção da conta:** o custo é +2 entidades e +23 campos e **1 valor novo** de enumeração em entidade que já existe (`folha_externa`); o `importacao_csv` está nos campos da entidade nova. Totais: 1.279 / 15.055 / 3.809. |
| Q252-11 | **Outras naturezas da folha externa (D-N696 e Q252-8a):** o S-5003 traz **só o FGTS**. Para **líquido, INSS e IRRF** da folha externa: (a) o mesmo padrão (XML do eSocial quando existir, que é o **S-5001** para o INSS e o **S-5002** para o IRRF, e um CSV derivado do esquema; o **líquido não existe no eSocial** e só vem em CSV), ou (b) **tratar fora do documento 252**, na integração da folha com o financeiro, e aqui ficar só o FGTS? | **(b)**: este documento é do FGTS. As outras naturezas pedem o mesmo método (ler o esquema do S-5001 e do S-5002, já nos pacotes que você mandou) e uma decisão sobre o líquido, que não tem XML; faço quando você disser «seguir» **Respondida em 24/11/2026 (D-N705): «OK. Mas o que o eSocial retorna, considerar a importação do XML do eSocial».** Vale a recomendação (b) (tratar fora do documento 252), **com a sua condição:** onde o eSocial devolve o dado, **importar o XML** (S-5001, S-5002, S-5011, S-5012); CSV só para o que o eSocial não devolve (o líquido). |

**Material que falta:** **nenhum**. **Perguntas abertas neste documento:** **nenhuma** (as onze estão respondidas). **Pendência minha:** o desenho das outras naturezas da folha externa (seção 5, Q252-11), a abrir quando você disser.

# 7. Para o contador (documento 188)

- **C374 (aberta):** vencimento do FGTS Digital no **dia 20** (e não o dia 7 do documento 01) e se a multa de 40% inclui os **depósitos devidos da própria rescisão**.
- **Pergunta nova proposta (C375, a escrever no documento 188 se você aprovar):** **como contabilizar** (a) a **reversão da provisão do FGTS** quando a guia chega com valor diferente (conta de diferença, P-31), (b) a **atualização, multa e juros de mora** da guia paga em atraso e (c) a **multa de 40%** (indenização compensatória) paga pela guia: contas e momento.

# 8. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N692 | Resposta de Alberto (24/11/2026) à **Q250-46**: **«sim, concordo»**: um dono por etapa no FGTS e o título nasce do valor oficial, com a folha lançando só a provisão. **Efeito:** abre o documento 252 | Q250-46 |
| D-N693 (proposta) | Desenhar o FGTS com seis entidades novas (retorno do eSocial, guia e débito da guia, histórico de remunerações, arquivo do Anexo I e rescisão), 74 campos; nada aplicado até «consolidar» | Documento 252, versão 1 |
| D-N696 | Resposta de Alberto (24/11/2026) à **Q252-2**: o FGTS **nasce na folha**, a folha o **envia ao eSocial** e **recebe o retorno** (fecha o circuito), e **da folha segue ao financeiro e à tesouraria** por **integração entre os módulos**; se a folha é **processada externamente**, o financeiro **importa um CSV**. **Efeito:** regras R14 e R15; Q252-1 substituída pela Q252-7; perguntas novas Q252-7 e Q252-8; **nenhuma entidade nem campo novo** | Q252-2 |
| D-N697 | Resposta de Alberto (24/11/2026): **«Q252-1 a 8 Seguir recomendações»**. **Efeito:** (Q252-7) o título do FGTS nasce da **integração da folha** quando o retorno volta e a **guia se liga ao título** (R16); a recomendação da Q252-1 (guia como gatilho) conflita e **prevalece a Q252-7**; Q252-2, 3, 4, 5, 6 e 8 seguem as recomendações; o valor `fgts_guia_debito` sai (**2 valores de enumeração**); mesmas 6 entidades e 74 campos; faltam três materiais seus. **Nada aplicado** | Q252-1 a Q252-8 |
| D-N698 | Resposta de Alberto (24/11/2026): **«FGTS integração vem da folha»**. **Efeito:** **confirma** que o título do FGTS vem da **integração da folha** (e não da guia do FGTS Digital como gatilho), o que resolve o conflito entre as recomendações da Q252-1 e da Q252-7 apontado na D-N697. **Nenhuma mudança** de entidades, campos ou regras (R1, R14 e R16 já dizem isso). **Nada aplicado** | Q252-1 e Q252-7 |
| D-N699 | Entrada de Alberto (24/11/2026), sem mensagem: o link da **NT S-1.3 nº 07/2026 (rev. 20/10/2026)** do eSocial. **Resultado:** a nota é de ajustes e **não traz as tags** do S-5003 e do S-5013; confirma o grupo `infoBaseFGTS` do S-5003 e traz a mudança do `infoFGTS` do S-2500 em 14/12/2026 (reclamatória, fora deste documento). **Efeito:** nenhum na estrutura; a Q252-5 continua pedindo o anexo do leiaute ou o pacote XSD. **Nada aplicado** | Entrada |
| D-N700 | Entrada de Alberto (24/11/2026): o **Manual de Orientação do Desenvolvedor do eSocial** (versões 1.15 e 1.9), o CSV «Evento, Assunto, Código no ID» (S-5003 = `003 gov`, S-5011 = `011 gov`) e o link do **MOS S-1.3 consolidado até a NT 07/2026**. **Resultado:** os manuais do desenvolvedor trazem a regra do **ID** do retorno (`ID` + `003` ou `013` + recibo do evento gerador), o **download por ID** e os **limites** (10 acessos por dia, nenhum pedido nos dias 1 a 7, 50 IDs por chamada, certificado sem procuração), mas **não as tags**; o MOS tem as tags (páginas 376 e 400), mas o link só abriu até a página 40. **Efeito:** regra **R17** e parágrafo na seção 3.2; **nenhuma entidade nem campo novo**; a Q252-5 pede o PDF do MOS. **Nada aplicado** | Entrada |
| D-N701 | Entrada de Alberto (24/11/2026), sem mensagem: **três pacotes de esquemas XSD S-1.3** (01/12/2026, 14/12/2026 e 18/01/2027). **Resultado:** os três são **idênticos** para o S-5003 e o S-5013; li os dois esquemas; o `dtVenc` do S-5003 é só para período anterior ao FGTS Digital e o S-5013 não tem vencimento; o retorno traz o depósito **por tipo de valor**, por estabelecimento e lotação. **Efeito:** leiaute em 3.2; Q252-5 cumprida; **proposta Q252-9** (+1 entidade e +14 campos; 1.277 e 15.032); a D-N697 (6 entidades e 74 campos) **continua valendo**. **Nada aplicado** | Entrada |
| D-N702 | Resposta de Alberto (24/11/2026): **«Q252-9: Aprovo»**. **Efeito:** entram no desenho aprovado (a) os **dois campos novos** do cabeçalho do retorno (`Indicador_Apuracao` e `Existencia_Informacao`) e (b) a **entidade nova `Mov_Esocial_Retorno_Fgts_Valor`** (12 campos); regra **R18** em vigor. Total aprovado para o próximo «consolidar»: **7 entidades e 88 campos** (1.277 / 15.032 / 3.804). **Nada aplicado** | Q252-9 |
| D-N703 | Resposta de Alberto (24/11/2026) à **Q252-3**: **«sim tem admitidos antes desta data 03/2024, guardasse todo o histórico desde a contratação»**. **Efeito (leitura minha):** o sistema atual guarda todo o histórico e o ERP o **recebe inteiro**; **R19** (migração, `Origem_Historico` = `migracao`); **Método 1 padrão** e Método 2 só por exceção; **nenhuma entidade nem campo novo**; falta só a quantidade (não bloqueia). **Nada aplicado** | Q252-3 |
| D-N704 | Resposta de Alberto (24/11/2026): **«Q252-3 - Seguir recomendação»** e **«Q252-8 - Considerar importar o XML do S-5003 e usar este para gerar um layout do csv»**. **Efeito (leitura minha):** (Q252-3) a **quantidade** de admitidos antes de 03/2024 sai da própria migração (R19), sem pedir a você; (Q252-8) na folha externa o ERP **importa o XML do S-5003** e o **CSV tem o leiaute derivado do esquema** (14 colunas, seção 3.8); **R15 reescrita** (o ERP recebe o retorno por importação), **R20 nova** (conferência do lote); **proposta Q252-10** (+2 entidades, +23 campos, 3 valores de enumeração; 1.279 / 15.055 / 3.809) e **pergunta nova Q252-11** (outras naturezas). O desenho aprovado segue 7 entidades e 88 campos. **Nada aplicado** | Q252-3 e Q252-8 |
| D-N705 | Resposta de Alberto (24/11/2026): **«Q252-10 Seguir recomendação»** e **«Q252-11 - OK. Mas o que o eSocial retorna, considerar a importação do XML do eSocial»**. **Efeito:** (Q252-10) a **estrutura do lote importado fica aprovada**: `Mov_Rh_Folha_Externa_Lote` (14 campos), `Mov_Rh_Folha_Externa_Lote_Ocorrencia` (8), o campo `ID_Lote_Folha_Externa` no retorno (23 campos) e o valor `folha_externa` em `Mov_Titulo.Origem_Tipo`; **9 entidades e 111 campos aprovados** (1.279 / 15.055 / 3.809); **correção minha da conta:** 1 valor novo de enumeração em entidade existente (3 no total no documento), e não 3 novos; (Q252-11) as **outras naturezas saem do documento 252** (recomendação (b)), **com a condição** de importar o XML do eSocial onde ele devolve o dado (S-5001, S-5002, S-5011 e S-5012); desenho pendente do meu lado. **Nada aplicado** | Q252-10 e Q252-11 |
| D-N706 | Pedido de Alberto (24/11/2026): **«consolidar»**. **Decidido (leitura minha):** aplicar ao dicionário **tudo o que estava aprovado**: as **9 entidades e 111 campos** do documento 252 (D-N697, D-N702 e D-N705) e o valor **`folha_externa`** em `Mov_Titulo.Origem_Tipo` (Q252-10). **Efeito:** revisão 60, **1.279 entidades e 15.055 campos** (+9 e +111), 3.809 referências, 1.556 tabelas físicas; nove entidades no módulo Folha & RH e o valor novo em Contas a Pagar/Receber; sem Carga. **Nada aprovado ficou de fora.** |

# 9. O que foi aplicado (revisão 60, D-N706)

**Aplicado: 1.279 entidades (+9) e 15.055 campos (+111)**, com 27 campos de referência a mais (3.809); 1.556 tabelas físicas (+9; nenhuma entidade com vigência, então nenhuma tabela de versão); 277 entidades mestres (sem mudança). **Um valor novo de enumeração** em entidade que já existia (`folha_externa` em `Mov_Titulo.Origem_Tipo`); o `importacao_csv` está nos campos da entidade nova do retorno. **Sem Carga**: os dois valores do domínio `tipo_evento_esocial` (S-5003 e S-5013) são cadastro do usuário (domínio aberto). A auditoria fechou com **0 achados**; o DDL rodou em PostgreSQL 16 sem erro. **Fica de fora** o desenho das outras naturezas da folha externa (Q252-11), que é pendência minha.

# 10. Fontes e limites

- **Manual de Orientação do FGTS Digital, versão 1.70 (12/06/2026)** e **Cartilha do Empregador (V9)**, enviados por você em 23/11/2026; a leitura do manual está no documento 250, seção 3.17.4. A cartilha só foi extraída.
- **S-5003 e S-5013:** páginas de documentação de terceiros (Senior) confirmam o **leiaute S-1.3**, que o S-5003 é o retorno de cada evento de remuneração (S-1200) ou de desligamento (S-2299 e S-2399), por contrato, estabelecimento e lotação, **sem depender de fechamento**, e que o S-5013 é o retorno do fechamento (S-1299); **não trazem a tabela de tags**. Por isso não nomeei tags nem tipos de valor (`tpValor`): a Q252-5.
- **Tentativa de obter as tags (24/11/2026, D-N697):** li o índice do leiaute S-1.3 (gov.br, NT 06/2026 rev. 09/04/2026) e as páginas do S-5003 e do S-5013 da Senior; **nenhuma traz a tabela de tags** nem link de XSD. O leiaute oficial (PDF de estrutura ou XSD) precisa vir de você (Q252-5).
- **NT S-1.3 nº 07/2026, rev. 20/10/2026 (você enviou o link em 24/11/2026, D-N699):** li as 7 páginas (texto extraído; confira os nomes no PDF oficial). É nota de **ajustes**, **não traz a tabela de tags** do S-5003 nem do S-5013; os leiautes e as regras completos estão nos anexos e nos XSD publicados com ela, que **não li**. Do que interessa ao FGTS: (a) o S-5003 tem um grupo **`infoBaseFGTS`** (o nome confere com o que o retorno guarda como base); (b) no **S-2500** (reclamatória), o grupo `infoFGTS` muda em **14/12/2026** (restrição por categoria e regime, e novo valor 3 em `tpRegTrab`), assunto do desenho da reclamatória, **fora** deste documento; (c) **nada** sobre S-5013, S-1299 ou guia. **Não altera** nenhuma entidade nem campo do documento 252.
- **Manual de Orientação do Desenvolvedor do eSocial, versões 1.15 (abril de 2025) e 1.9 (agosto de 2020), e o CSV «Evento, Assunto, Código no ID» (você enviou em 24/11/2026, D-N700):** li o texto dos dois PDFs (125 e 120 páginas). **Não trazem as tags** do S-5003 e do S-5013 (é manual de webservice), mas trazem **a regra do ID** dos eventos gerados pelo eSocial, o **download por ID** e os **limites do webservice** (seção 3.2, R17). As versões **coincidem** nos limites; vale a **1.15**. O CSV (S-5003 = `003 gov`, S-5011 = `011 gov`) **confere** com o manual.
- **Esquemas XSD S-1.3 (três pacotes; você enviou em 24/11/2026, D-N701):** `evtBasesFGTS.xsd` (S-5003) e `evtFGTS.xsd` (S-5013) lidos por inteiro; as tags e as regras de validação que o esquema documenta estão em 3.2. **Não li** as regras do anexo II (REGRA_*) nem a Tabela 23 completa do anexo I; o `tpValor` vem das enumerações do próprio esquema. O MOS (abaixo) **deixa de ser necessário** para as tags.
- **Manual de Orientação do eSocial (MOS) S-1.3, consolidado até a NT 07/2026 (você enviou o link em 24/11/2026, D-N700):** a leitura pelo navegador **só chegou à página 40 de cerca de 410**. O sumário mostra o **leiaute do S-5003 na página 376 e o do S-5013 na página 400** (Capítulo III), que são exatamente as tags que faltam. O que li (itens 8.5, 10.3 e 14) confirma que a guia do FGTS Digital sai das informações do eSocial a partir de **03/2024** e que o FGTS **não depende do S-1299**; nada de tags do retorno.
- **Os campos de negócio do retorno** (base, depósito, vencimento, recibo) são **leitura minha** a partir do que o retorno informa; a conferência com o XSD pode acrescentar campos.
- **Não há API** do FGTS Digital nos manuais lidos (R12). **Não consultei** o portal do FGTS Digital (exige certificado).
- **Percentuais do inventário (documento 246):** não foram revistos.

Próximos números: D-N707, contador C375 (proposta), documento 259, R154 (do documento 250), Q252-12, Q250-76, Q251-9.
