# Respostas aos Documentos 189 e 190, o Liga e Desliga do IPI e a IN RFB 2.295 (Confia) — Documento 191

*Você respondeu em 09/11/2026 às perguntas dos documentos 189 e 190 e enviou três PDFs sem mensagem: a IN RFB 2.295/2025 (Confia), um ADE da DRF/SOR nº 658/2026 e uma portaria nº 658 de 2021. Este documento registra as respostas, desenha o que a Q189-3 mudou ("ligar e desligar o IPI a partir de um momento"), confere a IN 2.295 contra o dicionário e lê o ADE. É **proposta**: **nada foi alterado no dicionário** (revisão 34: 1.135 entidades e 12.739 campos).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **Respostas registradas (D-N513):** Q189-1, Q189-2, Q189-4 e Q190-1 a Q190-5 "Sim"; Q189-5 "Fechado"; **Q189-3 com ajuste**: o IPI pode ser prorrogado e precisa ter um **liga e desliga a partir de uma data**. Tudo entra no próximo "consolidar", com o ajuste da Q189-3 desenhado abaixo.
- **Liga e desliga do IPI (seção 3):** o dicionário já tem o mecanismo: `Cad_Empresa_Modulo_Opcional` guarda, por empresa ou filial, `Habilitado` verdadeiro ou falso **com vigência**. Proponho **2 valores novos** no domínio `modulo_fiscal_opcional`, sem campo nem entidade nova. Você precisa confirmar o alcance (Q191-1).
- **IN RFB 2.295/2025 (Confia):** a multivigente tem as alterações das INs 2.317 (vigência 09/04/2026, o bônus da CSLL) e 2.328 (18/06/2026, troca "certificação" por **admissão**). **Confere** com o desenho do bônus dos documentos 185 e 187 (percentuais, limites, 12 meses, +1 ponto até 3%, fora da estimativa mensal, ECF e DCTFWeb). **Corrige duas leituras minhas**: o bônus do Confia é revogado **a partir do período de apuração** em que sai o ADE de exclusão (e não "até o fim do mês", que é regra do Sintonia), e os 12 meses do primeiro bônus contam **da publicação do ADE de admissão**, não do selo.
- **Acrescenta:** 2 campos em `Cad_Empresa_Programa_Conformidade` (data do ADE de admissão e data do fato da exclusão), 4 motivos de exclusão novos, 1 valor de origem de parcelamento (o plano de regularização do art. 34) e 3 avisos (devedor contumaz, 12 meses e 60 dias).
- **ADE DRF/SOR 658/2026 (REIDI):** é uma habilitação real. Confere com `Cad_Habilitacao_Regime_Especial`, com **1 lacuna** (a data de conclusão do projeto, que dispara o pedido de cancelamento em 30 dias) e **1 dúvida para o contador** (o prazo de 5 anos conta da habilitação, não da aprovação do projeto).
- **Dois arquivos podem estar errados:** a "Portaria 658" que veio é a Portaria da **Casa Civil de 2021 sobre entrada no país na pandemia** (revogada); a Portaria que a 703/2026 cita é a **Portaria RFB 658/2026** (comitês do Confia). Proponho dispensar (Q191-8).
- **Contagem:** este documento propõe **0 entidades e 3 campos** (1 a mais que o documento 189 sozinho). Aprovados os documentos 189, 190 e 191: **1.136 entidades e 12.749 campos**.

# 2. O que você respondeu e como entra

| Pergunta | Sua resposta | Como registro |
|---|---|---|
| Q189-1 | Sim | Carga das 5 situações cadastrais do art. 9º da IN 2.119 em `situacao_cadastral_cnpj`, provisória |
| Q189-2 | Sim | 3 campos e aviso do Motor para a inidoneidade do art. 51 da IN 2.119 |
| Q189-3 | "Pode ser prorrogado o IPI, tenho que deixar ele como eu ligar e desligar ele a partir de um momento" | **Aprovada com ajuste:** os 6 valores de domínio, a descrição e os 4 avisos entram, e o IPI ganha o liga e desliga da seção 3. O valor `ipi_suspensao_lei_10485` virou `autopecas_lei_10485` (Q190-3) |
| Q189-4 | Sim | Repetro-Industrialização continua gancho |
| Q189-5 | Fechado | Fechada com o envio dos anexos (documento 190) |
| Q190-1 | Sim | 24 motivos de suspensão do CNPJ e a entidade filha `Cad_Participante_Situacao_Cnpj_Motivo` (4 campos) |
| Q190-2 | Sim | Anexo II da IN 2.333 fora do ERP |
| Q190-3 | Sim | 66 linhas da Lei 10.485 em `autopecas_lei_10485`, provisórias |
| Q190-4 | Sim | Anexo Único da IN 2.324 e carteira do Confia sem campo novo |
| Q190-5 | Sim | Retenção do art. 3º, § 3º, da Lei 10.485 fica para depois, com o contador |
| Q190-6 | Enviou a IN 2.295/2025 | Lida na seção 4; a Q187-3 fica **fechada**. A Portaria RFB 658/2026 não veio (seção 6) |

# 3. Liga e desliga do IPI

## 3.1 Como leio a sua resposta

"Pode ser prorrogado o IPI" tem duas leituras, e o desenho cobre as duas com o mesmo mecanismo:

1. **A suspensão do IPI da IN 2.324** (e a lista da Lei 10.485) pode ter o prazo prorrogado: não posso gravar uma data final fixa no sistema.
2. **O IPI como tributo** pode continuar sendo cobrado depois do momento em que a reforma o reduz: o usuário precisa poder ligar ou desligar a apuração do IPI a partir de uma data.

**Dicionário hoje.** `Cad_Empresa_Modulo_Opcional` já é exatamente isso: empresa (e filial, se for o caso), módulo, `Habilitado` (verdadeiro liga, falso desliga sem apagar o histórico), `Ato_Habilitacao` e vigência. Cada mudança abre uma versão nova. O domínio `modulo_fiscal_opcional` é aberto (já tem os módulos do Bloco K, do DF, da sub-apuração, da EFD e da ECD).

## 3.2 Proposta (Q191-1): 0 entidades, 0 campos, 2 valores de domínio

| Valor novo em `modulo_fiscal_opcional` | O que liga e desliga |
|---|---|
| `ipi_suspensao` | As hipóteses de suspensão da IN 2.324 (arts. 2º a 19): o Motor só oferece a suspensão, a lista `autopecas_lei_10485` e os textos da nota quando o módulo está ligado na data do fato. Desligado, a saída segue com o IPI normal |
| `ipi_apuracao` | A apuração e o destaque do IPI da empresa ou da filial: o Motor só calcula o IPI quando ligado. Desligado a partir de uma data, as notas dessa data em diante saem sem IPI e o EFD-ICMS/IPI não gera os blocos do IPI para o período |

**Regras (todas avisos, sem bloqueio, como o resto do ERP):**

- A data de corte é a do **fato** (emissão, entrada ou saída), nunca a data em que o usuário mexeu no cadastro: ligar ou desligar com data retroativa **avisa** que há notas já emitidas no período.
- A **prorrogação legal** não pede código: o dado legal (lista, alíquota e regime) tem `Vigencia_Fim`, e prorrogar é abrir uma versão nova com o fim novo. O ERP **avisa** quando o fim legal que ele tem já passou e o módulo continua ligado, para o contador conferir se houve prorrogação.
- O que o módulo desligado **não apaga**: as notas e os créditos já registrados continuam como estão.

**O que o módulo `ipi_apuracao` não decide:** a alíquota do IPI em 2027 em diante (a redução da reforma e a exceção dos produtos que concorrem com os da Zona Franca) continua dado com vigência em `Cad_Aliquota` e na lista do IS e do IPI (D-N295). O liga e desliga é a **chave da empresa**; a alíquota continua sendo o **dado**. Se você só queria o liga e desliga da suspensão, o valor `ipi_apuracao` sai e nada mais muda.

# 4. IN RFB 2.295/2025: o Confia

Publicada no DOU de 08/12/2025 (p. 89), visão multivigente com a **IN 2.317** (25/03/2026, vigência **09/04/2026**) e a **IN 2.328** (17/06/2026, vigência **18/06/2026**). Os Anexos I (autoavaliação), II (Termo de Compromisso) e III (Plano de Trabalho) são PDFs que **não vieram**; o Anexo IV lista 20 ADEs do piloto de 2024.

## 4.1 O que confere com o dicionário

| Dispositivo | O que diz | Dicionário | Resultado |
|---|---|---|---|
| Art. 5º, XIII e § 4º | Bônus de 1% da CSLL à vista até o vencimento; +1 ponto a cada 12 meses de selo, até 3%; limites de R$ 250 mil, R$ 500 mil e R$ 1 milhão por ano; não vale para estimativa mensal; informado na ECF e confessado na DCTFWeb; fora da base de qualquer tributo | `Cad_Parametro_Bonus_Adimplencia` e `Mov_Bonus_Adimplencia_Csll` | **Confere** |
| Art. 5º, § 5º | A parcela não aproveitada não passa para o período seguinte | `Valor_Bonus_Nao_Aproveitado` | **Confere** |
| Art. 5º, § 3º | Valor devido da CSLL é o apurado no lucro real, presumido ou arbitrado | `Valor_Csll_Devida` | **Confere** |
| Art. 47, § 3º | Readmissão só depois de **2 anos** do ADE de exclusão | Aviso da Q187-2 | **Confere** (agora com o texto do próprio Confia) |
| Art. 45, I e II, a, b, f | Exclusão a pedido, por princípios, por critérios, por simulação | `motivo_exclusao_programa`: `a_pedido`, `descumpriu_principios`, `deixou_criterios_de_adesao`, `ma_fe_fraude_ou_simulacao` | **Confere** |
| Art. 21 | A admissão é por ADE da Comac, publicado no DOU; não homologa as informações | `Numero_Ato_Admissao` | Confere, mas falta a **data** (4.2) |
| Art. 2º e 20 a 21 (IN 2.328) | O termo passa de "certificação" para **admissão** | `Numero_Ato_Admissao`, `admitida` | Confere; só a **descrição** de `ID_Empresa` ainda diz "admitida ou certificada" |

## 4.2 O que corrige ou acrescenta

**1. Quando começa a contar o bônus do Confia (art. 5º, § 4º, III).** O primeiro bônus só vem **depois de 12 meses da publicação do ADE de admissão**; os pontos adicionais (IV) contam por período de 12 meses de selo. O dicionário conta tudo de `Data_Concessao_Original`, a data do selo, e **não guarda a data do ADE**. Proposta: **+1 campo** `Data_Ato_Admissao` (data da publicação do ADE no DOU) em `Cad_Empresa_Programa_Conformidade`; o Motor **avisa** se há bônus antes de 12 meses dela. Os 12 meses do primeiro bônus passam a ser o maior entre a data do ADE e a do selo, para o contador decidir (C221).

**2. Quando o bônus acaba (art. 5º, § 4º, V).** O bônus é revogado **a partir do período de apuração** em que o ADE de exclusão é publicado. Isso **corrige a Q187-1**, em que eu estendi ao Confia a regra do Sintonia ("o selo vale até o fim do mês do cancelamento"). Para o Confia: a apuração (trimestre ou ano) que contém a data de publicação do ADE de exclusão **já não tem bônus**. O Sintonia continua com a regra dele. Proposta: a regra do Motor passa a ser **por programa** (aviso, como já aprovado).

**3. Efeitos da exclusão (art. 47, caput e § 1º).** Pela redação da IN 2.317, a exclusão produz efeitos **desde a data do fato** que a motivou, formalizada por ADE; **depois** da publicação do ADE a fruição dos benefícios é interrompida e voltam as **majorações de multa** (art. 44, §§ 1º e 2º, da Lei 9.430). O campo `Data_Ato_Exclusao` do dicionário mistura as duas datas na descrição ("data do ato; termo inicial na data do fato"). Proposta: `Data_Ato_Exclusao` fica como **a publicação do ADE** e entra **+1 campo**, `Data_Fato_Exclusao` (a data do fato que motivou). Com isso, o total do item é **2 campos** (este e o do item 1) em `Cad_Empresa_Programa_Conformidade`.

**4. Motivos de exclusão (art. 45, II).** Três motivos da lista do art. 45, II, **não existem** no domínio `motivo_exclusao_programa`, mais um sobre o selo. Proposta: **+4 valores** de domínio, sem campo:

| Valor novo | Dispositivo |
|---|---|
| `plano_trabalho_nao_cumprido` | Art. 45, II, c: não pactuar, não renovar periodicamente ou não cumprir o Plano de Trabalho |
| `inconformidade_tributaria_nao_corrigida` | Art. 45, II, d: não corrigir inconformidades tributárias identificadas |
| `falha_governanca_nao_corrigida` | Art. 45, II, e: não corrigir falhas de gestão e de governança tributária |
| `uso_indevido_selo` | Art. 45, II, g (IN 2.317): uso indevido do selo, nos termos do manual da marca |

**5. Devedor contumaz (art. 5º-A, IN 2.317).** Enquanto admitido no Confia, o contribuinte **não está sujeito à qualificação de devedor contumaz**, nos termos da legislação específica. O dicionário tem `Mov_Condicao_Devedor_Contumaz` e `Cad_Empresa_Programa_Conformidade` sem ligação entre eles. Proposta: **aviso** do Motor quando houver condição de contumácia aberta para empresa com Confia **admitida** na data (sem bloqueio, sem campo): quem decide o efeito é a Receita.

**6. Confissão sem multa nos 60 dias (art. 21, § 3º).** Em até **60 dias da publicação do ADE de admissão**, o contribuinte pode confessar crédito não constituído e pagar tributo e juros, **sem multa de mora nem de ofício** (medida do art. 7º, § 1º, II, da Lei 14.689). Com a `Data_Ato_Admissao`, o ERP **avisa** o prazo de 60 dias. Sem campo novo.

**7. Plano de regularização (art. 34).** Se há concordância sobre a questão tributária, o contribuinte pode pagar **30% de entrada** e o saldo em até **60 parcelas** mensais, com Selic acumulada desde o mês seguinte ao da consolidação e **1%** no mês do pagamento; sem multa de mora se paga nos prazos; **confissão irrevogável e irretratável** (§ 4º). O prazo de reconhecimento do débito pode ser de até 120 dias (art. 33, § 5º). O dicionário tem `Mov_Parcelamento_Tributario` com o domínio `origem_parcelamento_tributario`. Proposta: **+1 valor** `plano_regularizacao_confia`, sem campo; o ERP só registra as parcelas, e as regras (30%, 60, Selic) ficam como texto do fundamento (C221).

**8. Coisas da norma que o ERP não precisa guardar.** Etapas da admissão, vagas, autoavaliação, Plano de Trabalho anual (de 1º de janeiro a 31 de dezembro), pontos focais, reuniões, Fórum de Diálogo, renovação cooperativa de CND, sigilo e recursos são **processo da Receita e do contribuinte**; o ERP **só registra** a admissão, o selo, a exclusão e o bônus. O ponto focal do contribuinte e o substituto (art. 14, II) são pessoas que o cadastro de contatos já comporta.

**9. Fechamento da Q187-3.** O ato do Confia que a LC 225 (art. 29) pedia é a **IN 2.295/2025**, com as INs 2.317 e 2.328. A Q187-1 fica corrigida pelo item 2.

# 5. ADE DRF/SOR nº 658/2026: um REIDI real

**O que é.** Ato Declaratório Executivo da DRF/SOR, de 14/04/2026 (DOU de 15/04/2026, p. 55), que concede a habilitação ao REIDI a uma pessoa jurídica para um projeto aprovado por portaria do Ministério de Minas e Energia (Portaria nº 3.033/SNTP/MME, de 15/12/2025), com previsão de conclusão em 30/01/2026. Cita os arts. 646 a 663 da **IN RFB 2.121/2025** (que **não li**) e o Decreto 6.144/2007.

| O que o ato diz | Dicionário (`Cad_Habilitacao_Regime_Especial`) | Resultado |
|---|---|---|
| Habilitação ao REIDI do titular do projeto (CNPJ) | `ID_Participante_Titular`, `Tipo_Habilitacao` = habilitação | Confere |
| Número e data do ADE | `Numero_Habilitacao`; a data é o início da vigência | Confere |
| Projeto aprovado por portaria do ministério (número e data) | `Numero_Ato_Aprovacao` e `Data_Aprovacao_Projeto` | Confere |
| **Previsão de conclusão** do projeto (30/01/2026) | **Sem campo** | **Lacuna** |
| Art. 2º: benefício nas aquisições, locações e importações **no período de 5 anos contados da data da habilitação** | `Data_Aprovacao_Projeto`: "o período entre a aprovação do projeto e a habilitação é acrescido aos 5 anos" | **Dúvida:** o ADE não fala em acréscimo (C222) |
| Art. 3º: concluída a participação, **cancelar a habilitação em 30 dias** do adimplemento, sob pena de sanção | `Situacao_Habilitacao` (cancelada) | Falta a **data** que dispara o prazo |
| Art. 4º: cancelamento de ofício se faltar requisito | `Situacao_Habilitacao` | Confere |

**Proposta (Q191-7): +1 campo** `Data_Conclusao_Projeto` (data, opcional) em `Cad_Habilitacao_Regime_Especial`: a prevista no ADE, atualizada pela real; o Motor **avisa** o prazo de 30 dias para pedir o cancelamento. O ERP não pede o cancelamento.

**Observação.** O ato traz o nome e o CNPJ de uma empresa real, mas é publicação oficial; não uso nenhum dado dele na carga nem em exemplo do dicionário.

# 6. Os dois outros arquivos

- **"Portaria-658-21-ccvimpressao.pdf"** é a **Portaria nº 658, de 5 de outubro de 2021, da Casa Civil**, que fixava medidas excepcionais de entrada no país por causa da covid-19, **revogada** pela Portaria 660/2021. **Não tem relação com o ERP**; deve ter vindo da busca pelo número 658. Não usei.
- A que a Portaria RFB 703/2026 cita (art. 4º) é a **Portaria RFB nº 658, de 9 de março de 2026**, dos Comitês Permanentes do Confia, que conduzem os Planos de Trabalho. É processo interno da Receita e **não muda o ERP**. Proponho dispensá-la (Q191-8).

# 7. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Q191-2: `Data_Ato_Admissao` e `Data_Fato_Exclusao` em `Cad_Empresa_Programa_Conformidade` | 0 | 2 |
| Q191-7: `Data_Conclusao_Projeto` em `Cad_Habilitacao_Regime_Especial` | 0 | 1 |
| Q191-1: 2 valores em `modulo_fiscal_opcional` | 0 | 0 |
| Q191-5: 4 valores em `motivo_exclusao_programa` | 0 | 0 |
| Q191-6: 1 valor em `origem_parcelamento_tributario` | 0 | 0 |
| Avisos do Motor (devedor contumaz, 12 meses, 60 dias, REIDI 30 dias) | 0 | 0 |
| **Total do documento 191** | **0** | **3** |

Sobre a revisão 34 (1.135 entidades e 12.739 campos): os documentos 189 e 190, que você aprovou, somam **1 entidade e 7 campos** (1.136 e 12.746); com o 191, **1.136 entidades e 12.749 campos**. Nada entra antes do "consolidar".

# 8. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q191-1** | O liga e desliga do IPI é o módulo opcional por empresa e filial, com data de início e fim, com **2 valores novos** (`ipi_suspensao` e `ipi_apuracao`)? Ou você só queria o da suspensão da IN 2.324? | **Os dois valores** |
| **Q191-2** | Criar `Data_Ato_Admissao` e `Data_Fato_Exclusao` em `Cad_Empresa_Programa_Conformidade` (2 campos), com os avisos de 12 meses e de 60 dias? | **Sim** |
| **Q191-3** | A regra do bônus do Confia passa a ser **por programa**: o Confia perde o bônus a partir do período de apuração do ADE de exclusão (corrige a Q187-1) e o Sintonia segue com o fim do mês? | **Sim** |
| **Q191-4** | Aviso do Motor quando há condição de devedor contumaz para empresa com o Confia admitido (art. 5º-A)? | **Sim**, só aviso |
| **Q191-5** | Acrescentar os 4 motivos de exclusão do art. 45, II, c, d, e e g? | **Sim** |
| **Q191-6** | O plano de regularização do Confia (art. 34) entra como valor `plano_regularizacao_confia` do parcelamento tributário, sem campo? | **Sim** |
| **Q191-7** | Criar `Data_Conclusao_Projeto` na habilitação do REIDI, com aviso de 30 dias para pedir o cancelamento? | **Sim** |
| **Q191-8** | Dispensar a Portaria RFB 658/2026 (comitês do Confia) e descartar a Portaria da Casa Civil de 2021 que veio no lugar? | **Dispensar** |

# 9. Perguntas para o contador

Entram no **documento 188**, na Parte 6, e não aqui (D-N501): **C221**, sobre o Confia (de quando contam os 12 meses do primeiro bônus, o prazo de confissão de 60 dias e o plano de regularização do art. 34); **C222**, sobre o prazo de 5 anos do REIDI (da habilitação, como diz o ADE, ou com o acréscimo desde a aprovação do projeto, como o dicionário descreve).

# 10. Limites do que eu li

- A IN 2.295 é a visão multivigente do portal Normas da Receita ("este texto não substitui o publicado oficialmente"); **não conferi no DOU**. Li o texto inteiro, mas o PDF traz a redação antiga e a nova lado a lado; usei a **vigente** (INs 2.317 e 2.328). Os Anexos I a III são PDFs que não vieram; o Anexo IV é só uma lista de 20 ADEs de 2024.
- **Não li** a IN RFB 2.121/2025 (que o ADE cita), o Decreto 6.144/2007, a Lei 14.689/2023 nem a Portaria RFB 658/2026.
- O ADE do REIDI é de **uma** habilitação; não tiro dele regra geral, só confiro os campos.
- O desenho do liga e desliga é proposta minha, e a leitura da sua resposta (seção 3.1) precisa da sua confirmação na Q191-1.
- Nenhuma recomendação foi confirmada pelo contador.
