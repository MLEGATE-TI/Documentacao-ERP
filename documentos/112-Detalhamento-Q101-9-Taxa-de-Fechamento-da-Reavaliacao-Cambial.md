# Detalhamento da Q101-9: Taxa de Fechamento do Mês na Reavaliação Cambial — Documento 112

> **Consolidado na revisão 22 (26/10/2026, documento 113).** Entraram os **4 campos** aprovados (`Cad_Serie_Cotacao.Uso_Fechamento` e `Referencia_Fonte`; `Mov_Titulo_Reavaliacao.ID_Serie` e `Data_Referencia_Taxa`), a descrição de `Taxa_Fechamento` e a regra de que o **fechamento espera** a cotação (sem campo novo). O dicionário passou a ter 922 entidades e 9.998 campos. A frase "nada foi alterado no dicionário" abaixo é a de quando o documento foi escrito. Segue com o contador: PTAX de venda única, PTAX como "taxa à vista" do CPC 02 e taxa da variação tributada.

*Você pediu para detalhar a Q101-9 do documento 101: "qual taxa de fechamento do mês a reavaliação usa e de qual série?". Reli o que o dicionário já guarda de séries de cotação e da reavaliação, e li o que o CPC 02 (R2), a IN RFB 1.079/2010 e o Banco Central dizem sobre a taxa. **O CPC 02 não escolhe entre compra e venda**, e a IN 1.079 não traz regra de taxa para converter saldo; por isso a escolha é de critério, e há proposta e pontos para o contador. É proposta de desenho: **nada foi alterado no dicionário** (revisão 21: 920 entidades, 9.973 campos). As perguntas abertas ficam no documento 38.*

Mlegate · Alberto Beyeler · Outubro de 2026 · Versão 5 (26/10/2026)

**Sua resposta (26/10/2026):** "para variação cambial antes do pagamento está correto, taxa única e última do mês; no caso de ser não dia útil, pegar a taxa do último dia do mês". Registrei: **Q112-1 respondida (sim, taxa única, a PTAX de venda da opção A)** e **Q112-2 respondida (sim)**. Li "o último dia do mês" como o **último dia do mês que tem cotação**, isto é, o **último dia útil**: com 31/10/2026 em sábado, vale a PTAX de sexta, 30/10, que é o mesmo que "a última cotação até a data". **Se você quis outra coisa, me diga.** Li "taxa única" como a PTAX de **venda** da proposta; se queria a de compra, me diga. Faltam as Q112-3, Q112-4 e Q112-5.

**Suas respostas seguintes (26/10/2026):** **Q112-3: sim** (os 3 campos). **Q112-4:** "se não tiver câmbio cadastrado, avisar da pendência; porém o sistema pode carregar automaticamente a cotação do dólar no Banco Central". **Q112-5:** "moeda não divulgada pelo Banco Central, o usuário tem que informar a cotação, ou apontar onde é possível pegar a cotação". Registrei: aviso da pendência quando falta a cotação, **carga automática da PTAX no Banco Central** para as moedas que ele divulga, e, nas demais, **cotação digitada ou fonte indicada** (seção 4.4). Isso abriu a **Q112-6** (o fechamento espera ou conclui?) e a **Q112-7** (um campo para "onde pegar a cotação"). Nada foi alterado no dicionário.

**Suas respostas finais (26/10/2026):** **Q112-6:** "tem que esperar até alimentar a cotação". **Q112-7: sim.** Registrei: **o fechamento espera** enquanto faltar a cotação (não conclui sem reavaliar a moeda) e **entra o campo `Cad_Serie_Cotacao.Referencia_Fonte`**. **Todas as perguntas do desenho (Q112-1 a Q112-7) estão respondidas**; restam só os pontos para o contador (seção 7). Nada foi alterado no dicionário.

# 1. Resumo

- **O que a Q101-9 pergunta.** No fim de cada mês, o ERP reavalia o saldo em aberto de cada título em moeda estrangeira (`Mov_Titulo_Reavaliacao`, documento 101). A pergunta é qual **taxa** converte esse saldo e de **qual série** ela vem. Na **baixa** não há dúvida: vale o contrato de câmbio (sua decisão de 22/10/2026). A reavaliação **não tem contrato**, por isso precisa de uma regra.
- **O que as fontes dizem.** O CPC 02 (R2) manda converter os itens monetários em moeda estrangeira pela **taxa de câmbio de fechamento**, que é a taxa à vista vigente no fim do período, e reconhecer a variação no resultado do período. **Não diz** se é a taxa de compra ou a de venda e **não cita a PTAX**. A IN RFB 1.079/2010 trata de **quando** a variação é tributada (caixa ou competência); só usa o dólar de **venda** do Banco Central para medir a "elevada oscilação" (10% no mês), e não traz regra de taxa para converter saldos.
- **Proposta (A, recomendada).** Uma **única taxa**: a **PTAX de venda do Banco Central** da **data do fechamento**; se a data não tem cotação (sábado, domingo, feriado), vale a **última cotação até a data**. Combina com o seu princípio de não complicar com compra e venda. O contador confirma.
- **Para guardar isso**, sem entidade nova: **1 campo** em `Cad_Serie_Cotacao` (marca a série usada no fechamento) e **2 campos** em `Mov_Titulo_Reavaliacao` (qual série e qual data de cotação foram usadas, para auditoria): **0 entidades e 3 campos** (aprovados, Q112-3), mais **1 campo** em `Cad_Serie_Cotacao` para "onde pegar a cotação" nas moedas sem PTAX (Q112-7, aprovado): **0 entidades e 4 campos**. O fechamento **espera** a cotação (Q112-6): é regra de validação, sem campo novo.
- **Perguntas:** Q112-1 a Q112-7 **todas respondidas**; restam 3 pontos para o contador (seção 7).

# 2. O que o dicionário já tem

| Peça | O que existe | O que falta |
|---|---|---|
| Série de câmbio | `Cad_Serie_Cotacao`: `Nome`, `Tipo` (`taxa_cambio`), `ID_Moeda_Origem`, `ID_Moeda_Destino`, `Fonte` (inclui `banco_central`), `Ativo`. **Sem campo de lado** (compra ou venda) | Dizer qual série é a do fechamento |
| Valor por data | `Mov_Serie_Cotacao_Valor`: `Data_Referencia`, `Valor`, `Origem` {`manual`, `automatico`}. Uma linha por dia, nunca sobrescrita | Nada |
| Busca automática | Camada de aplicação futura: Banco Central para PTAX (já escrito no dicionário) | Nada agora |
| Reavaliação | `Mov_Titulo_Reavaliacao`: `Data_Reavaliacao` (último dia do período), `Taxa_Fechamento` "lida da série na data" | Não diz **qual série** nem **de qual dia** veio a taxa |

Como a série não tem campo de lado, **compra e venda são séries diferentes** ("Dólar PTAX venda" e "Dólar PTAX compra"), sem mudar o dicionário.

# 3. O que li

| Fonte | O que diz | Para esta pergunta |
|---|---|---|
| CPC 02 (R2), item 23 | "Itens monetários em moeda estrangeira devem ser convertidos, usando-se a taxa de câmbio de fechamento" no fim de cada período | Confirma a **reavaliação ao fim do mês** (o seu desenho do documento 101) |
| CPC 02 (R2), item 8 | Taxa de fechamento é a **taxa à vista vigente ao término do período**; taxa à vista é a normalmente usada para liquidação imediata | A norma define o **conceito**, não a **fonte** |
| CPC 02 (R2), itens 28 e 29 | A variação cambial do item monetário vai ao **resultado do período**; se a liquidação é em período posterior, a variação de cada período é a mudança de taxa dele | Confirma o desenho em duas etapas: variação **não realizada** no mês e **realizada** na quitação |
| CPC 02 (R2), compra ou venda | **Não há menção** a taxa de compra, de venda ou à PTAX no texto atual. Uma versão antiga da definição dizia que, no Brasil, a taxa é a divulgada pelo Banco Central; essa frase **não consta** do texto revisado | A escolha entre compra e venda **não vem da norma** |
| IN RFB 1.079/2010, arts. 2º a 8º | Caixa (tributa na liquidação) ou competência (tributa no período); a opção vale o ano todo | É sobre **quando tributa**. **Sem regra de taxa** para converter saldo |
| IN RFB 1.079/2010, art. 5º-A | A "elevada oscilação" é o dólar de **venda** do Banco Central variando mais de 10% no mês (primeiro contra último dia) | Só mede oscilação para trocar de regime; **não é a taxa do fechamento** |
| Banco Central, PTAX | Média de quatro consultas a dealers (10h, 11h, 12h e 13h), com **cotação de compra e de venda**; publicada **depois das 13h**. Em dia sem câmbio (fim de semana, feriado), a referência é a do **último dia útil anterior** | Existem **duas PTAX** (compra e venda); a do fim do mês cai, às vezes, em dia sem cotação |

# 4. Pontos e proposta

## 4.1 Qual taxa

| Opção | Como fica | Observação |
|---|---|---|
| **A. PTAX de venda, única (recomendada)** | Todo título em moeda, a pagar ou a receber, é reavaliado pela PTAX de venda | Simples; uma série por moeda; combina com o seu princípio de não distinguir compra e venda. A prática comum de mercado, que **não verifiquei em norma** |
| **B. Venda no a pagar e compra no a receber** | A pagar (a empresa compra a moeda para pagar): venda. A receber (a empresa vende a moeda recebida): compra | Reflete o lado da liquidação, mas são **duas séries por moeda** e uma regra por tipo de título; contraria a simplicidade que você pediu |
| **C. Taxa própria** | A empresa define o critério (por exemplo, a taxa do banco com quem opera) | Foge da fonte oficial; dificulta auditoria |

A norma contábil não obriga A nem B. **A escolha do critério é do contador**; recomendo A para começar e deixar **B como evolução**, que só pede a segunda série e uma regra, sem mudar estrutura.

## 4.2 Qual dia

A taxa é a da **`Data_Reavaliacao`**, que é o **último dia do período de fechamento**. Se esse dia **não tem cotação**, vale a **última cotação com data até ele**. Exemplo real: **31/10/2026 é sábado**; a reavaliação de outubro usa a PTAX de **sexta, 30/10/2026**. A regra vale também para 31/12. **Sem campo novo**: é uma regra de leitura da série (a maior `Data_Referencia` menor ou igual à data).

## 4.3 De qual série

A série do fechamento é uma por par de moedas (por exemplo, dólar para real). Proposta, **sem entidade nova**:

| Onde | Campo | Descrição proposta |
|---|---|---|
| `Cad_Serie_Cotacao` | `Uso_Fechamento` (**novo**, booleano) | Marca a série usada na reavaliação mensal. **No máximo uma série ativa marcada por par de moedas.** Só vale para `Tipo` = `taxa_cambio` |
| `Mov_Titulo_Reavaliacao` | `ID_Serie` (**novo**, referência a `Cad_Serie_Cotacao`) | A série da qual a taxa foi lida. Guarda o critério **daquele mês**, mesmo que o critério mude depois |
| `Mov_Titulo_Reavaliacao` | `Data_Referencia_Taxa` (**novo**, data) | O dia da cotação lida (pode ser anterior à `Data_Reavaliacao`, como na sexta de 30/10). Para auditoria |
| `Cad_Serie_Cotacao` | `Referencia_Fonte` (**novo, Q112-5 e Q112-7, aprovado**, texto) | **Onde se pega a cotação** quando a moeda não é divulgada pelo Banco Central (nome do órgão ou endereço da página). Obrigatório quando `Fonte` = `outro`. Serve de guia a quem digita a cotação e, no futuro, de base para outra busca automática |

**Por que não uma entidade de parâmetro:** o dicionário tem parâmetros por vigência para obrigações específicas, mas a série **não precisa de vigência**: quando o critério mudar, as reavaliações antigas continuam guardando a série que usaram (`ID_Serie`). Mudar de A para B é marcar outra série e, se for o caso, acrescentar a regra por lado.

## 4.4 Cotação que falta e moeda sem PTAX (Q112-4 e Q112-5, respondidas)

- **Carga automática (sua resposta à Q112-4).** O sistema **carrega sozinho** a cotação do Banco Central (PTAX) para as moedas que ele divulga, gravando uma linha por dia em `Mov_Serie_Cotacao_Valor` com `Origem` = `automatico` e a série com `Fonte` = `banco_central`. O dicionário **já tem** esses campos e já descreve a busca como camada de aplicação; **não precisa campo novo**. Eu **não testei** a integração: o Banco Central publica os boletins de câmbio como dado aberto (apareceu na pesquisa), mas não verifiquei o formato nem a disponibilidade.
- **Cotação que falta (sua resposta à Q112-4).** Se, no fechamento, **não há cotação cadastrada** para a moeda, o ERP **avisa a pendência** (qual moeda e qual data). Não usa uma taxa antiga em silêncio. **O que o fechamento faz com a pendência (sua resposta à Q112-6):** **espera**. O fechamento do período **não conclui** enquanto faltar a cotação de alguma moeda com título em aberto; só conclui depois que a cotação for **alimentada** (carga automática ou digitada). É uma **regra de validação do fechamento**, sem campo novo. Na consolidação, confiro onde o dicionário já guarda a lista de pendências do fechamento para a pendência de cotação entrar nela; se não houver lugar, volto a você antes de propor campo.
- **Moeda que o Banco Central não divulga (sua resposta à Q112-5).** O usuário **informa a cotação**, **ou aponta onde é possível pegá-la**. A cotação digitada fica com `Origem` = `manual` e a série com `Fonte` = `outro`. O "onde pegar" fica guardado no campo `Referencia_Fonte` (seção 4.3, aprovado na Q112-7).

# 5. Exemplo

Título a pagar de **US$ 10.000**, contabilizado a **5,20** (R$ 52.000). Fim de outubro de 2026: a `Data_Reavaliacao` é **sábado, 31/10/2026**, e a última cotação até lá é a de **sexta, 30/10/2026**. Suponha, como **valor ilustrativo**, PTAX de venda de **5,30** nessa sexta.

| Item | Valor |
|---|---|
| Taxa lida | 5,30 (série "Dólar PTAX venda", `Data_Referencia_Taxa` = 30/10/2026) |
| Valor em reais antes | R$ 52.000 |
| Valor em reais depois | US$ 10.000 × 5,30 = R$ 53.000 |
| Variação (a pagar, positivo é perda) | **perda de R$ 1.000**, não realizada |
| O que a linha guarda | `Taxa_Fechamento` = 5,30; `ID_Serie`; `Data_Referencia_Taxa` = 30/10/2026; `Data_Reavaliacao` = 31/10/2026 |

*O número é ilustrativo; não é a cotação do dia.*

# 6. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q112-1** | A taxa da reavaliação é **uma só**: a **PTAX de venda** do Banco Central, para título a pagar e a receber (opção A)? O contador confirma | **Respondida em 26/10/2026: sim, taxa única.** |
| **Q112-2** | Em data sem cotação (sábado, domingo, feriado), vale a **última cotação até a data**? | **Respondida em 26/10/2026: sim** (a taxa do último dia útil do mês). |
| **Q112-3** | Entram os 3 campos: `Cad_Serie_Cotacao.Uso_Fechamento`, `Mov_Titulo_Reavaliacao.ID_Serie` e `Mov_Titulo_Reavaliacao.Data_Referencia_Taxa`? | **Respondida em 26/10/2026: sim.** |
| **Q112-4** | Sem cotação no fechamento: o que o ERP faz? | **Respondida em 26/10/2026:** avisar a pendência; o sistema pode carregar automaticamente a cotação do dólar do Banco Central. |
| **Q112-5** | Moeda que o Banco Central não publica? | **Respondida em 26/10/2026:** o usuário informa a cotação ou aponta onde é possível pegá-la. |
| **Q112-6** | Com a pendência avisada (falta a cotação da moeda no fechamento), o **fechamento da contabilidade espera** até a cotação existir, ou conclui sem reavaliar aquela moeda? | **Respondida em 26/10/2026: espera** até alimentar a cotação. |
| **Q112-7** | Entra o campo `Cad_Serie_Cotacao.Referencia_Fonte` (texto, obrigatório quando `Fonte` = `outro`) para guardar **onde pegar a cotação**? | **Respondida em 26/10/2026: sim.** |

# 7. Para o contador

- Qual critério adotar: **PTAX de venda única** (A) ou **venda no a pagar e compra no a receber** (B)? O CPC 02 (R2) não escolhe, e a taxa de **fechamento** é a **à vista no fim do período**.
- A **PTAX do Banco Central** serve como a "taxa à vista" do CPC 02? (O texto atual da norma não a cita; uma versão antiga citava o Banco Central.)
- Para a empresa no regime de **competência** (IRPJ, CSLL, PIS e Cofins), qual taxa vale para a **variação mensal tributada**? A IN RFB 1.079/2010 **não traz regra de taxa** para converter saldo; **não encontrei** outra norma tributária sobre isso, e **não pesquisei** além dela.

# 8. Contagem e limites

**0 entidades e 4 campos aprovados**: 2 em `Cad_Serie_Cotacao` (`Uso_Fechamento`, `Referencia_Fonte`) e 2 em `Mov_Titulo_Reavaliacao` (`ID_Serie`, `Data_Referencia_Taxa`), a entrar na próxima consolidação (revisão 22). Mudam também, só no texto, a descrição de `Taxa_Fechamento` (a taxa da série marcada, na última cotação até a data) e a regra do fechamento (espera a cotação e lista a pendência de moeda e data).

**Limites.** Li o CPC 02 (R2) pela cópia publicada pela CVM, por extração do texto; **não li a norma inteira com os apêndices**. Li a IN RFB 1.079/2010 em página de legislação, não no Diário Oficial. O funcionamento da **PTAX** (quatro consultas, compra e venda, dia útil anterior) está em artigo de blog e deve ser **conferido no site do Banco Central**. **Não verifiquei** se a PTAX de **venda** é a prática dominante do mercado: está como recomendação minha, não como norma. Não testei nada com dados.

**Fontes consultadas.**

- CPC 02 (R2), cópia da CVM: https://conteudo.cvm.gov.br/cvm_institucional/export/sites/cvm/menu/regulados/normascontabeis/cpc/CPC_02_R2_rev_13.pdf
- IN RFB 1.079/2010: https://www.normaslegais.com.br/legislacao/in_rfb_1079_2010.htm
- Como o Banco Central calcula a PTAX (artigo): https://numerando.com.br/blog/taxa-ptax-banco-central-como-calculada
