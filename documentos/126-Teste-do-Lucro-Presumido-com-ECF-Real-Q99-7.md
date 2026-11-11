# Teste do lucro presumido com ECF real (Q99-7) — Documento 126

> **Respondidas em 27/10/2026 (D-N374, documento 127): Q126-1 sim; Q126-2 sim, com o Refis por período; Q126-3 sim, com o detalhamento do caixa no documento 127.**
>
> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 24** (925 entidades e 10.033 campos); a revisão 25 (929 entidades e 10.097 campos com o que já espera) aguarda o seu "consolidar". **Leitura que fiz:** o arquivo que você enviou, com o texto "ECF lucro presumido", é a **resposta à Q99-7** (pedi um arquivo real de presumido para provar as fórmulas). **Resultado:** as fórmulas da Receita reproduzem **108 de 108** linhas calculadas do arquivo, **desde que cada linha calculada seja arredondada a 2 casas antes de alimentar a seguinte**. Há **3 perguntas** (Q126-1 a Q126-3).

*Documento pedido pelo seu envio do arquivo `SpedEcf-43671544000198-Original-dez.2025.txt` (ECF do ano-calendário 2025, lucro presumido trimestral). Estende os documentos 99 e 125. As leituras de norma e de prática contábil são minhas e **não foram conferidas** com o contador.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

- **Prova do núcleo do presumido (P200, P300, P400 e P500): 108 de 108** linhas calculadas batem com o arquivo, nos quatro trimestres de 2025. Sem o arredondamento por linha, são 106 de 108 (dois desvios de R$ 0,01 na linha 15 do P300). O arredondamento por linha é o que a função `ARRED` que você aprovou na Q99-6 faz; o teste mostra **onde ela precisa ser aplicada**: em toda linha calculada.
- **A fonte das "demais receitas" que você aprovou na Q99-2 se confirma no arquivo:** a linha 11 do P200 (rendimentos de aplicação financeira) é igual, nos quatro trimestres, ao valor da conta referencial `3.01.01.05.01.05` do P150.
- **O percentual de presunção não sai do código do P150.** No 4º trimestre o arquivo tem R$ 350.000,00 na conta referencial de "prestação de serviços" e os mesmos R$ 350.000,00 na linha de **8%** do IRPJ (P200 4) e de **12%** da CSLL (P400 2). Isso confirma o desenho do documento 99 (o percentual vem da atividade, em `Mov_Apuracao_Presuncao_Atividade`) e mostra o caso em que o código sozinho não basta.
- **O arquivo traz dois fatos que o dicionário não guarda:** a empresa é **optante do Refis** (0010) e reconhece a receita por **regime de caixa** (0010). O perfil fiscal não tem campo para nenhum dos dois (Q126-2 e Q126-3).
- **P130 e P230 não foram provados:** o arquivo não tem esses registros (o indicador `IND_RED_ISEN` é não). Eles seguem desenhados no documento 125 e sem prova.
- **LC 224/2025 não foi provada:** o arquivo é de 2025, antes da lei. As fórmulas de 2026 seguem como leitura provisória (Q99-6).
- **Provisão contábil e ECF diferem em R$ 0,01** em três dos quatro trimestres (seção 6.1, Q126-1).

# 2. O arquivo

## 2.1 Registros 0010 e 0020 (o que decide o presumido)

| Campo | Valor no arquivo | O que significa |
|------------------------|--------|--------------------------------------------------|
| `0010.FORMA_TRIB` | 5 | Lucro presumido |
| `0010.FORMA_APUR` | T | Apuração trimestral |
| `0010.COD_QUALIF_PJ` | 01 | PJ em geral |
| `0010.FORMA_TRIB_PER` | PPPP | Presumido nos quatro trimestres |
| `0010.OPT_REFIS` | **S** | **Optante pelo Refis** |
| `0010.TIP_ESC_PRE` | C | Obrigada a entregar a ECD (ou entrega facultativa) |
| `0010.IND_REC_RECEITA` | **1** | **Regime de caixa** (2 seria competência) |
| `0020.IND_ALIQ_CSLL` | 1 | CSLL a 9% |
| `0020.IND_RED_ISEN` | **N** | **Sem isenção ou redução do imposto** |
| Os outros 27 indicadores do 0020 | N | Todos não |

## 2.2 Registros do bloco P

| Registro | Linhas no arquivo | Observação |
|------|-----|----------------------------------------------|
| P030 | 4 | T01 a T04 de 2025 |
| P100 e P150 | 2.928 e 844 | Plano referencial de balanço e de resultado, por trimestre |
| P200 | 100 | 25 linhas por trimestre; 2 com fórmula (10 e 26) |
| P300 | 69 | Linhas 1, 3, 4, 10 e 15 com valor |
| P400 | 88 | 22 linhas por trimestre; 15 com fórmula |
| P500 | 61 | Linhas 1, 2, 4 e 13 com valor |
| **P130 e P230** | **0** | Não existem no arquivo (coerente com `IND_RED_ISEN` = N) |
| **X280** | **0** | Idem |

# 3. Como testei

1. Usei **as fórmulas da carga de tabelas dinâmicas** do dicionário (Cad_Ecf_Tabela_Dinamica_Linha, a planilha da Receita), só as **versões vigentes em 2025** (as da LC 224 não valem em 2025).
2. As linhas **editáveis** (receita por percentual, rendimentos, retenções) foram **lidas do arquivo**; as **calculadas** foram **refeitas** pelo motor de fórmulas e **comparadas** com o valor gravado. Linha ausente no arquivo vale zero.
3. Parâmetros lidos do arquivo: qualificação 01 (PJ em geral), alíquota da CSLL 1 (9%), apuração trimestral.
4. O teste roda **na memória**: nada foi gravado no dicionário e a planilha da Receita não foi alterada.

# 4. Resultado

| Aba | Linhas calculadas comparadas | Batem | Observação |
|-----|-----|-----|------------------------------------------|
| P200 | 8 | 8 | Linhas 10 e 26 nos quatro trimestres |
| P300 | 20 | 20 | Linhas 1, 3, 4, 9 (zero) e 15 |
| P400 | 60 | 60 | 15 linhas por trimestre |
| P500 | 20 | 20 | Linhas 1, 2, 4, 13 e 14 |
| **Total** | **108** | **108** | Com arredondamento por linha |

**Sem o arredondamento por linha: 106 de 108.** Os dois desvios são da linha 15 do P300 (imposto a pagar), de R$ 0,01 no T01 e no T03. A razão: o arquivo grava a linha 3 (15%) e a linha 4 (adicional) **já arredondadas** e a linha 15 é a soma delas menos a retenção; o motor, sem arredondar, somava os valores com mais casas. Arredondando cada linha calculada (meio para cima ou meio para o par dão o mesmo resultado neste arquivo), os 108 batem.

**A cadeia do 4º trimestre, linha a linha (todos os valores batem com o arquivo):**

| Passo | Conta | Valor (R$) |
|------------------------------|------------------------------------|------------|
| Receita a 32% (P200 8) | lida do arquivo | 441.504,72 |
| Receita a 8% (P200 4) | lida do arquivo | 350.000,00 |
| Resultado dos percentuais (P200 10) | 441.504,72 × 32% + 350.000,00 × 8% | 169.281,51 |
| Rendimentos de aplicação (P200 11) | lida do arquivo | 52.629,73 |
| **Base do IRPJ (P200 26 = P300 1)** | 169.281,51 + 52.629,73 | **221.911,24** |
| IRPJ a 15% (P300 3) | 221.911,24 × 15% | 33.286,69 |
| Adicional (P300 4) | (221.911,24 − 60.000,00) × 10% | 16.191,12 |
| Retenção na fonte (P300 10) | lida do arquivo | 9.368,84 |
| **IRPJ a pagar (P300 15)** | 33.286,69 + 16.191,12 − 9.368,84 | **40.108,97** |
| Resultado dos percentuais (P400 6) | 441.504,72 × 32% + 350.000,00 × 12% | 183.281,51 |
| **Base da CSLL (P400 21 = P500 1)** | 183.281,51 + 52.629,73 | **235.911,24** |
| **CSLL a pagar (P500 13)** | 235.911,24 × 9% | **21.232,01** |

A base da CSLL (235.911,24) é **maior** que a do IRPJ (221.911,24) só no 4º trimestre, porque os R$ 350.000,00 entram a 8% no IRPJ e a 12% na CSLL. É o comportamento esperado do presumido.

# 5. O que o arquivo confirma do desenho

| Ponto do desenho | O que se viu no arquivo |
|------------------------------------|------------------------------------------------------|
| P200 11 por **soma das contas mapeadas ao P150** (Q99-2, aprovada) | Igual à conta referencial `3.01.01.05.01.05` ("Outras Receitas Financeiras") nos 4 trimestres: 100.497,50, 122.867,27, 95.603,23 e 52.629,73. Prova com **um** código; os outros códigos do P200 vieram zerados |
| Receita por percentual vem da **atividade** (documento 99) | P200 8 (32%) é a conta de locação em todos os trimestres; P200 4 (8%) no T04 é a mesma conta de "prestação de serviços" que o arquivo marca a 8%. O código sozinho não diz o percentual |
| Soma dos percentuais = receita bruta do P150 | Nos 4 trimestres, a soma das linhas de receita por percentual (P200 e P400) é igual à receita bruta do P150 (`3.01.01.01.01`): 437.033,98, 441.504,72, 441.504,72 e 791.504,72 |
| `ARRED` como função provisória (Q99-6, aprovada) | Necessária em toda linha calculada; sem ela, R$ 0,01 de desvio |
| CSLL a pagar sem retenção (Q99-4, atada à Q93-7) | P500 13 = P500 4 = P500 2 nos 4 trimestres (o arquivo não tem retenção de CSLL) |
| P130 e P230 só com `IND_RED_ISEN` = sim (Q125-5, sem resposta) | Compatível: o arquivo é **Refis = S** e **IND_RED_ISEN = N**, e **não traz** P130 nem P230. Mostra que o Refis, sozinho, não gera os dois registros. É **um** arquivo, não regra |

# 6. O que o arquivo mostra que o desenho ainda não cobre

## 6.1 Provisão contábil diferente da ECF em R$ 0,01

O P150 traz a **provisão para o IRPJ** e a **provisão para a CSLL** do trimestre. A da CSLL é **igual** ao P500 nos 4 trimestres. A do IRPJ **não** é igual à soma das linhas 3 e 4 do P300 em três trimestres:

| Trimestre | Provisão no P150 (R$) | P300 3 + 4 (R$) | Diferença |
|-----|-----------|-----------|-----------|
| T01 | 54.087,09 | 54.087,10 | −0,01 |
| T02 | 60.037,21 | 60.037,20 | +0,01 |
| T03 | 53.221,19 | 53.221,18 | +0,01 |
| T04 | 49.477,81 | 49.477,81 | 0,00 |

Os sinais mudam, então não é um método único de arredondamento: a contabilidade da empresa calculou o IRPJ por outro caminho. **Consequência para o ERP:** se o lançamento da provisão sair de um cálculo e a ECF sair de outro, a conferência que você aprovou como **só aviso** (Q99-3) avisaria por R$ 0,01. **Q126-1.**

## 6.2 Optante do Refis sem os campos do 0010

`OPT_REFIS` = S muda o que a ECF aceita (por exemplo, o texto de `FORMA_TRIB_PER` e os registros Y680 e Y681, que o arquivo traz). Pelo documento 91, o perfil fiscal (`Cad_Empresa_Perfil_Fiscal`) tem hoje **a forma de tributação** (`FORMA_TRIB`) e **o tipo de entidade imune ou isenta** (`TIP_ENT`) do 0010. **Não tem** `OPT_REFIS`. Dos outros campos do 0010 não conferi aqui se o dicionário já os obtém de dados existentes. **Q126-2.**

## 6.3 Receita por regime de caixa

`IND_REC_RECEITA` = 1: a empresa reconhece a receita do presumido **no recebimento**, não na emissão. No documento 99 (seção 5) eu tinha deixado como "a conferir" se a apuração do presumido do dicionário distingue caixa e competência. **Conferi: não distingue.** O único campo parecido do dicionário (`Situacao_Transicao`, valor `receita_regime_caixa`) é da transição da reforma tributária, não do presumido. No arquivo, a receita do 4º trimestre (R$ 350.000,00 + R$ 441.504,72) bate com a **receita bruta do resultado contábil** (P150), e não tenho como saber, só pelo arquivo, se o contador a ajustou por caixa antes. **Q126-3.**

## 6.4 Para o contador (não decidi nada)

- **Classificação do R$ 350.000,00 do 4º trimestre:** a conta referencial é de "prestação de serviços" e o percentual usado é o de 8% (IRPJ) e 12% (CSLL), e há "custo dos produtos de fabricação própria vendidos" de R$ 110.250,00 no mesmo trimestre. Não afirmo erro; o ponto é que o percentual vem da atividade que o contador classifica, e o ERP precisa guardar essa classificação com motivo (já é o desenho do documento 99).
- **Optante do Refis sem benefício** (`IND_RED_ISEN` = N): confirmar com o contador se isso é o caso comum, porque o desenho do documento 125 depende disso (item do documento 38, seção 2.2).
- **Regime de caixa com `TIP_ESC_PRE` = C:** o manual diz que o presumido por competência é obrigado a entregar a ECD; o arquivo é por caixa e mesmo assim marca "C" (o manual aceita a entrega facultativa). Sem consequência para o dicionário.

# 7. Defeitos da planilha da Receita encontrados no teste

O teste precisou de **três reparos em memória** (a planilha não foi alterada). Os dois primeiros são da planilha; o terceiro é convenção de data:

| Aba e linha | Defeito | Efeito |
|-----------|--------------------------------------------|-------------------------------------|
| P300 9 | Parênteses que não fecham (já está no documento 98, pergunta 2) | O motor não lê a fórmula; a linha 9 só deu zero porque o P230 38 não existe no arquivo |
| P500 2 | Barra vertical `\|` sobrando no fim da fórmula | O motor para; reparo: retirar o caractere |
| P500 2, M300B, M350B, T181 e U182 | Compara a data de início com texto no formato `"2022-01-01"` (ou `"2024-12-31"`), enquanto a ECF grava a data como `ddmmaaaa` (`01012025`) | Sem converter, a comparação de texto dá resultado errado. **O ERP compara datas como datas**, o que resolve; não é pendência do dicionário |

Se você decidir enviar a consulta à Receita (documento 98), os dois primeiros podem entrar na lista. **Não envio nada por você.**

# 8. Limites do teste

- **Um arquivo, um ano, uma empresa** (locação de imóveis, com um trimestre misto de 8%, 12% e 32%). O teste prova que as fórmulas e o motor reproduzem esse arquivo; **não prova** os caminhos que ele não usa (percentuais de 1,6%, 16% e 38,4%, rendimento do exterior, ganhos de capital, JCP, retenção de CSLL, RET).
- **Só 2025.** As linhas da LC 224/2025 (P200 25100 a 25250, P300 e P500 18100 a 18500) não existem no arquivo, e a ECF de 2026 só existirá em 2027. **Elas seguem sem prova** e como leitura provisória (Q99-6).
- **P130, P230 e X280 sem prova.** O arquivo não os traz.
- **As linhas editáveis foram lidas do arquivo**, não calculadas pelo ERP. O teste **não** prova que o ERP chegará aos mesmos R$ 441.504,72 ou R$ 100.497,50; isso depende do mapeamento (Q99-2 e documento 125) e da apuração por atividade do dicionário. O que ele prova é a **cadeia de cálculo da ECF a partir** dessas linhas.
- **Não conferi** o P100, a conferência do plano referencial contra o balanço, nem os blocos C, E, J e K do arquivo.

# 9. Perguntas

| # | Pergunta | Recomendação |
|-----|--------------------------------------------------|---------------------------|
| **Q126-1** | O lançamento contábil da provisão do IRPJ (e da CSLL) usa o **valor da apuração** (soma das linhas já arredondadas, igual ao P300 e ao P500), para a contabilidade e a ECF não divergirem em R$ 0,01? A conferência da Q99-3 continua só aviso. | **Sim.** Um só valor de imposto, o da apuração; a diferença de R$ 0,01 some e a conferência só avisa o que for real |
| **Q126-2** | O perfil fiscal (`Cad_Empresa_Perfil_Fiscal`, com vigência) ganha **`Optante_Refis`** (sim ou não) para guardar o `0010.OPT_REFIS`? Hoje ele não tem campo. Custo: **1 campo**. | **Sim.** É dado do contribuinte que o ERP não deduz, e o P130/P230 e o Y680 dependem dele |
| **Q126-3** | O perfil fiscal ganha **`Criterio_Reconhecimento_Receita`** (`caixa` ou `competencia`, obrigatório quando a forma de tributação é lucro presumido) para o `0010.IND_REC_RECEITA`, e eu **detalho no próximo documento** como a receita por percentual é apurada quando o critério é caixa (hoje a apuração do presumido não distingue)? Custo do campo: **1 campo**. | **Sim ao campo e ao detalhamento.** Sem ele, uma empresa por caixa, como a do arquivo, teria a receita da apuração diferente da da ECF |

**Não decidi nada** nas três. Se você aprovar as três como recomendo, a revisão 25 passa de 929 entidades e 10.097 campos para **929 entidades e 10.099 campos** (930 e 10.109 com a entidade de mapeamento da Q125-1).

# 10. O que este documento fecha e o que deixa aberto

- **Fecha:** a **Q99-7** (arquivo enviado). O teste do núcleo do presumido em 2025 está feito.
- **Deixa aberto:** a prova da LC 224/2025 (depende de ECF de 2026), a prova do P130 e do P230 (depende de um arquivo com `IND_RED_ISEN` = sim), as perguntas Q125-1 a Q125-7 e as três novas deste documento.
- **Custo no dicionário (se tudo aprovado como recomendo):** 0 entidades e 2 campos novos, **todos** dependentes de você ver e aprovar. Nada entra antes do "consolidar".
