# Plano Referencial da ECF por Segmento da Empresa — Documento 91

*Desenho para aprovação, a partir das suas respostas de 20/10/2026 sobre o plano compartilhado por segmentos diferentes, sobre a vigência do leiaute e sobre as perguntas Q91-1 e Q91-2 (seção 9). Consolidado em 20/10/2026 na revisão 18 (documento 92): D-N327 a D-N331 entraram no dicionário e a carga foi regerada; ficaram de fora a Q91-10 e as Q91-3, Q91-4, Q91-5 e Q91-6, sem resposta. Depois de respondidas, entraram na revisão 19 (documento 95): Q91-10 (4 campos), Q91-4 (bloqueio), Q91-5 (vigência do plano e das contas), Q91-3 (segmento nas abas M300, M350 e N630 A, B e C, na carga) e Q91-6 (texto). O texto abaixo é o da proposta. Os nomes de campo abaixo são meus, não seus.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

Você decidiu três coisas: não deixar plano referencial duplicado; nos planos que se diferenciam, identificar qual segmento cada um atende, para facilitar o relacionamento entre o plano de contas da empresa e o de referência; e guardar o segmento no cadastro da empresa, para o ERP saber qual plano referencial usar. Sobre a vigência, você confirmou que, na troca de plano, a vigência do plano antigo termina um dia antes do início da nova e o novo entra com vigência aberta (31/12/9999).

Conferi o desenho com a planilha e achei um ponto que muda a proposta: **o segmento sozinho não escolhe o plano.** No segmento "PJ em geral" há planos diferentes para lucro real e para lucro presumido, e o plano patrimonial é diferente do plano de resultado. A escolha precisa de três dados da empresa e da tabela: o **segmento**, a **forma de tributação** e a **finalidade** (patrimonial ou de resultado). A seção 3 traz a matriz completa das 22 tabelas de plano e dos 18 planos.

A proposta não cria entidade nova. Ela acrescenta **3 campos** em `Cad_Ecf_Tabela_Dinamica`, tira **1 campo** de `Cad_Plano_Referencial` e acrescenta **2 campos** em `Cad_Empresa_Perfil_Fiscal` (o segmento e a forma de tributação, esta com a lista do manual: seção 9). O plano continua único e passa a servir a vários segmentos pelas tabelas que apontam para ele.

# 2. O que você decidiu

**D-N327 (plano e segmento).** Sem plano duplicado (já era a regra da D-N321: as abas idênticas apontam para o mesmo plano). Cada plano identifica os segmentos que atende. O cadastro da empresa guarda o segmento, e é por ele que o ERP escolhe o plano referencial.

**D-N328 (vigência).** Na troca, a vigência anterior termina um dia antes do início da nova, e a nova entra com fim 31/12/9999. É a convenção da Fase 0, e confirma a carga do leiaute 12 (início 01/01/2025, fim 31/12/9999).

# 3. Como o plano é escolhido hoje na planilha

A planilha traz 22 abas de plano referencial, e várias apontam para o mesmo plano. As abas de "linhas" que também variam por segmento estão na Q91-3. As colunas "Forma de tributação" e "Segmento" abaixo foram lidas por mim do título de cada aba; vale conferir.

| Aba | Forma de tributação | Segmento | Finalidade | Plano |
|--------|------------------------|-----------------------------------------|---------------|------------|
| L100A | lucro real | PJ em geral | patrimonial | Plano 01 |
| L100B | lucro real | financeiras | patrimonial | Plano 02 |
| L100C | lucro real | seguradoras e previdência aberta | patrimonial | Plano 03 |
| L300A | lucro real | PJ em geral | resultado | Plano 04 |
| L300B | lucro real | financeiras | resultado | Plano 05 |
| L300C | lucro real | seguradoras e previdência aberta | resultado | Plano 06 |
| P100A | lucro presumido | PJ em geral | patrimonial | Plano 07 |
| P100B | lucro presumido | financeiras | patrimonial | Plano 02 |
| P150A | lucro presumido | PJ em geral | resultado | Plano 08 |
| P150B | lucro presumido | financeiras | resultado | Plano 05 |
| S100 | TEF/SAF | TEF e SAF | patrimonial | Plano 09 |
| S150 | TEF/SAF | TEF e SAF | resultado | Plano 10 |
| U100A | imune ou isenta | imunes e isentas em geral | patrimonial | Plano 11 |
| U100B | imune ou isenta | associação de poupança e empréstimo | patrimonial | Plano 02 |
| U100C | imune ou isenta | previdência aberta sem fins lucrativos | patrimonial | Plano 03 |
| U100D | imune ou isenta | previdência fechada | patrimonial | Plano 12 |
| U100E | imune ou isenta | partidos políticos | patrimonial | Plano 13 |
| U150A | imune ou isenta | imunes e isentas em geral | resultado | Plano 14 |
| U150B | imune ou isenta | associação de poupança e empréstimo | resultado | Plano 15 |
| U150C | imune ou isenta | previdência aberta sem fins lucrativos | resultado | Plano 16 |
| U150D | imune ou isenta | previdência fechada | resultado | Plano 17 |
| U150E | imune ou isenta | partidos políticos | resultado | Plano 18 |

Três leituras desta tabela:

- **O Plano 02** serve a três abas de formas de tributação diferentes (lucro real e presumido das financeiras, e imune ou isenta da associação de poupança e empréstimo). O **Plano 03** serve a seguradoras (lucro real) e a previdência aberta sem fins lucrativos (imune ou isenta). O **Plano 05** serve às financeiras no lucro real e no presumido. Por isso o segmento não pode ficar no plano como um valor só.
- **A forma de tributação só desempata** no segmento "PJ em geral" (Plano 01 e 04 para lucro real, 07 e 08 para presumido). Nos outros segmentos o plano não muda com ela, mas a aba muda, e é a aba que a ECF usa.
- **Cada combinação de forma de tributação, segmento e finalidade aparece uma só vez** nas 22 abas. Então a aba é a unidade certa para guardar essas três informações: nenhuma combinação aponta para dois planos.

# 4. Proposta de campos

## 4.1 `Cad_Ecf_Tabela_Dinamica` (3 campos novos, os três opcionais)

Preenchidos nas abas de plano referencial (Tipo_Tabela = plano_referencial); vazios nas demais, até a Q91-3.

| Campo | Tipo | Regra |
|-------------|-------------------------------------------|-------------------------------------------|
| `ID_Segmento` | referência (`Cad_Classe_Sistema`, domínio = `segmento_plano_referencial`), opcional | O segmento que a aba atende, lido do título (os nove segmentos da D-N321). |
| `Forma_Tributacao` | enumeração {lucro_real, lucro_presumido, tef_saf, imune_isenta}, opcional | A forma de tributação a que a aba se aplica. Enumeração fechada pelas quatro famílias de aba da planilha (L, P, S e U); se a Receita criar uma quinta, vira domínio, pela regra da D-N305. |
| `Finalidade_Plano` | enumeração {patrimonial, resultado}, opcional | Contas patrimoniais (série 100) ou contas de resultado (série 150 ou 300). |

## 4.2 `Cad_Plano_Referencial` (1 campo sai)

`ID_Segmento` sai. Um plano passa a servir a vários segmentos, e o segmento de cada um está nas abas que apontam para ele. Continua valendo que o plano é uma edição da tabela por leiaute (`Leiaute_Sped`), sem duplicar linha.

## 4.3 `Cad_Empresa_Perfil_Fiscal` (2 campos novos, depois da Q91-1 e da Q91-2)

| Campo | Tipo | Regra |
|--------------------|----------------------------------------|----------------------------------------|
| `ID_Segmento_Plano_Referencial` | referência (`Cad_Classe_Sistema`, domínio = `segmento_plano_referencial`) | O segmento da empresa para escolher o plano referencial. Obrigatório (Q91-2, resposta sim). Como o perfil tem vigência, o segmento pode mudar no tempo (por exemplo, uma empresa que passa a ser financeira), e a ECF usa o do período da escrituração. Não confundir com `ID_Segmento_Csll`: são domínios diferentes (a CSLL usa a divisão da LC 224 e da LC 105; o plano usa a divisão da planilha da RFB). |
| `ID_Forma_Tributacao_Ecf` | referência (`Cad_Classe_Sistema`, domínio = `forma_tributacao_ecf`), opcional | A forma de tributação da empresa na ECF (campo FORMA_TRIB do registro 0010), com os dez valores do manual (seção 9). Como o perfil tem vigência, a forma pode mudar no tempo (Q91-1, resposta sim). Vazio para a empresa que não entrega a ECF. |

## 4.4 Regra de escolha do plano

Para o período da escrituração, o ERP procura em `Cad_Ecf_Tabela_Dinamica` as abas de plano referencial da versão do leiaute vigente com `ID_Segmento` igual ao da empresa, `Forma_Tributacao` igual à dela e as duas finalidades. O resultado são duas abas (patrimonial e de resultado) e os dois planos para onde elas apontam. O mapeamento `Cad_Conta_Contabil_Referencial` só aceita código de um desses planos (Q91-4: aviso ou bloqueio). Quando dois segmentos usam o mesmo plano, o ERP não carrega nada duas vezes. Refinamento depois da conferência com o manual: seção 9.

## 4.5 Vigência (D-N328)

O plano é uma edição por leiaute e **não ganha vigência própria**: a validade dele é a da versão do leiaute a que a aba pertence (`Cad_Obrigacao_Leiaute_Versao`, com início e fim). Na carga de um novo leiaute, o ERP encerra a versão anterior com fim igual ao início da nova menos um dia e grava a nova com 31/12/9999. A vigência de cada código, dentro do plano, continua como está (DT_INI e DT_FIM da planilha). Se você preferir que o plano tenha janela própria, ele viraria entidade mestre, com tabela de versão, e o desenho cresce: Q91-5.

# 5. Efeito na carga

Se você aprovar, a carga muda assim: `Cad_Ecf_Tabela_Dinamica.csv` ganha as três colunas nas 22 abas de plano (a matriz da seção 3); `Cad_Plano_Referencial.csv` perde a coluna de segmento; e as duas pendências de "plano compartilhado por segmentos diferentes" fecham. O número de planos (18) e de contas (12.744) não muda.

# 6. Contagem

| | Hoje (revisão 17) | Com este documento |
|---|---:|---:|
| Entidades | 907 | 907 |
| Campos em `Cad_Ecf_Tabela_Dinamica` | 6 | 9 |
| Campos em `Cad_Plano_Referencial` | 6 | 5 |
| Campos em `Cad_Empresa_Perfil_Fiscal` | 14 | 16 |
| Saldo de campos | | +4 |
| Domínios em `Cad_Classe_Sistema` | 266 | 267 (novo: `forma_tributacao_ecf`) |

Somado ao documento 90, se os dois forem aprovados: 914 entidades, 9.861 campos e 271 domínios (os 4 do documento 90 mais este).

# 7. Perguntas para você

| Nº | Pergunta | Recomendação |
|------|-----------------------------------------------|-----------------------------------------------|
| Q91-1 | **Respondida (sim, e pode mudar no tempo).** Campo da forma de tributação da empresa na ECF no perfil fiscal. | Feito na seção 4.3, com a lista do manual. |
| Q91-2 | **Respondida (sim, obrigatório).** | Feito na seção 4.3; a Q91-7 trata da empresa que não entrega a ECF. |
| Q91-3 | As abas de "linhas" que também mudam por segmento (M300A, B e C; M350A, B e C; N630A, B e C) recebem os mesmos três campos preenchidos, para o ERP escolher a aba certa do e-Lalur e da apuração? A atividade rural (M300R, M350R) é outra divisão. | Sim para o segmento; a atividade rural fica para uma pergunta própria. |
| Q91-4 | O código referencial fora do plano da empresa dá aviso ou bloqueia o mapeamento? | Aviso, até o contador validar a carga (mesmo critério da D-N311). |
| Q91-5 | O plano fica sem vigência própria (a da versão do leiaute vale), ou vira mestre com janela própria? | Sem vigência própria: o plano é uma edição por leiaute. |
| Q91-6 | O contador confirma como o leiaute 12 convive com o 13: o leiaute 12 também vale para as situações especiais de 2026, enquanto o 13 deve valer para o ano-calendário 2026, e as datas de início podem coincidir (01/01/2026). | Escolher a versão pelo período e pelo tipo da escrituração (normal ou situação especial), não só pela data. Ponto do contador. |

# 8. Limites

As colunas de segmento e de forma de tributação da seção 3 foram lidas por mim do título das abas, e não de um campo da planilha. Não conferi se a Receita publica o plano de resultado de "imunes e isentas em geral" separado do de "PJ em geral" por regra própria ou só por título. A matriz é a carga atual (leiaute 12); um leiaute novo pode desfazer o que aqui parece regra. Nada disto foi aplicado ao dicionário, ao banco ou à carga.

# 9. Respostas de 20/10/2026 e o que a conferência com o manual mudou

Você respondeu **sim** à Q91-1 (criar o campo da forma de tributação da empresa na ECF, que pode mudar com o tempo) e **sim** à Q91-2 (segmento obrigatório). Registrei como **D-N329** no documento 14. O perfil fiscal da empresa já tem vigência, então os dois campos mudam no tempo sem nada a mais.

Ao ajustar o desenho, li no manual (registro 0010, páginas 70 e seguintes) a **regra oficial de escolha do plano referencial**, que confirma a matriz da seção 3 e acrescenta dois pontos:

- **O plano segue a qualificação da pessoa jurídica (0010.COD_QUALIF_PJ):** 01 PJ em geral, 02 componente do sistema financeiro, 03 seguradoras, de capitalização ou entidade aberta de previdência complementar, 04 SAF. Para imunes e isentas, o campo fica vazio e vale o tipo da entidade (0010.TIP_ENT): 11 associação de poupança e empréstimo; 12 previdência aberta sem fins lucrativos; 06 previdência fechada; 15 partidos políticos; e os demais tipos (01 a 05, 07 a 10, 13, 14 e 99) usam o plano de imunes e isentas em geral. É exatamente a lista de nove segmentos da D-N321, o que dá segurança ao domínio.
- **A forma de tributação do manual (0010.FORMA_TRIB) tem dez valores, e não quatro:** 1 lucro real; 2 lucro real/arbitrado; 3 lucro presumido/real; 4 lucro presumido/real/arbitrado; 5 lucro presumido; 6 lucro arbitrado; 7 lucro presumido/arbitrado; 8 imune do IRPJ; 9 isenta do IRPJ; 10 TEF. Por isso o campo da empresa (`ID_Forma_Tributacao_Ecf`) guarda os dez valores, como um domínio de `Cad_Classe_Sistema` (a lista já cresceu com o TEF, e a regra das listas que podem crescer é a D-N305). Os quatro valores que propus para a aba (lucro real, lucro presumido, TEF/SAF e imune ou isenta) continuam servindo para agrupar as abas.

**Ligação entre a forma da empresa e a aba:** valores 1 e 2 levam à aba de lucro real; 5 e 7, à de lucro presumido; 8 e 9, à de imune ou isenta; 10, à de TEF/SAF. Nos valores 3, 4 e 6 (mistos e arbitrado) a forma muda por trimestre; nesse caso a escolha segue a forma de cada período (`Regime_Aplicado` da apuração, e o campo FORMA_TRIB_PER do manual), e não só a forma anual da empresa.

Perguntas novas:

| Nº | Pergunta | Recomendação |
|------|-----------------------------------------------|-----------------------------------------------|
| Q91-7 | **Respondida (sim, obrigatório).** O segmento é obrigatório também para a empresa que não entrega a ECF. | Padrão "PJ em geral" na criação da empresa; a forma de tributação segue opcional (seção 10). |
| Q91-8 | **Respondida por Alberto (o contador ainda confirma):** no período arbitrado o ERP avisa e o contador seleciona o plano, normalmente o de "PJ em geral". | Campos na seção 10 (Q91-10). |
| Q91-9 | O segmento escolhe o plano, mas não preenche o 0010.TIP_ENT (16 valores de tipo de imune ou isenta, 01 a 15 e 99, e vários caem no mesmo segmento). O tipo da entidade imune ou isenta vira campo do perfil fiscal, ou fica para o desenho da geração do 0010? | **Respondida (criar o campo agora, leitura B da seção 10.2)**, depois de eu pedir a confirmação do "sim" ambíguo. |

# 10. Respostas de 20/10/2026 às Q91-7 a Q91-9

**D-N330.** Você respondeu: (Q91-7) **sim, segmento obrigatório** para toda empresa, inclusive a que não entrega a ECF (com o padrão "PJ em geral" na criação, como recomendei, para o cadastro não travar). (Q91-8) No período arbitrado **o ERP avisa e o contador seleciona o plano**, normalmente o de "PJ em geral". (Q91-9) Respondeu "sim", que não consegui separar da recomendação; pedi a confirmação e você escolheu criar o campo agora (D-N331).

## 10.1 Plano escolhido pelo contador no período arbitrado (Q91-8)

Hoje o dicionário não tem onde guardar a escolha do contador. Proponho 4 campos opcionais em `Mov_Apuracao_Irpj_Csll` (a apuração já traz o `Regime_Aplicado` do período):

| Campo | Tipo | Regra |
|------------------------|-------------------------------|---------------------------------------------|
| `ID_Plano_Referencial_Patrimonial` | referência (`Cad_Plano_Referencial`), opcional | O plano das contas patrimoniais escolhido pelo contador. Obrigatório quando `Regime_Aplicado` = arbitrado e a escrituração for gerada; nos outros regimes o ERP escolhe pela seção 4.4 e o campo fica vazio. |
| `ID_Plano_Referencial_Resultado` | referência (`Cad_Plano_Referencial`), opcional | Idem, para as contas de resultado. |
| `ID_Usuario_Confirmacao_Plano` | referência (`Cad_Usuario`), opcional | Quem escolheu (padrão de confirmação da Fase 0). |
| `Data_Hora_Confirmacao_Plano` | data e hora, opcional | Quando escolheu. |

Regra: na geração da ECF de um período arbitrado sem escolha, o ERP **avisa** e não escolhe sozinho. Como você disse que normalmente será o plano de "PJ em geral", a tela pode sugerir esse plano, mas só vale depois da confirmação do contador. Fica por decidir se a sugestão é a das abas de lucro real ou a das de lucro presumido (as duas têm plano de "PJ em geral"): é ponto do contador. **Q91-10:** aprova os 4 campos?

## 10.2 Tipo de imune ou isenta (Q91-9)

- **Leitura A (a recomendação):** nada muda agora; o tipo da entidade (0010.TIP_ENT, 16 valores) entra no desenho da geração do registro 0010.
- **Leitura B (a pergunta):** o tipo vira campo do perfil fiscal agora: `ID_Tipo_Entidade_Imune_Ecf` (referência a `Cad_Classe_Sistema`, domínio `tipo_entidade_imune_ecf`, com os 16 valores do manual (01 a 15 e 99), opcional, obrigatório quando a forma de tributação for 8 ou 9). Mais 1 campo e 1 domínio.

**Q91-11: respondida.** Você confirmou a **leitura B**: o campo `ID_Tipo_Entidade_Imune_Ecf` entra no perfil fiscal (D-N331).

## 10.3 Contagem

| | Com as seções 1 a 9 | Com a seção 10 |
|-----------------------------|-------------------|-----------------------------------------------------|
| Campos (junto com o documento 90) | 9.861 | 9.866 (os 4 campos do 10.1, se aprovados na Q91-10, e o campo da leitura B, já decidido) |
| Domínios | 271 | 272 (novo: `tipo_entidade_imune_ecf`) |
