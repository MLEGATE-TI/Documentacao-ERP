# CNPJ Alfanumérico: Perguntas e Respostas da Receita — Documento 50

*Leitura do PDF "CNPJ alfanumérico" da Receita Federal (14 páginas, 52 perguntas e respostas) que Alberto enviou em 12/10/2026, comparado ao tipo lógico CNPJ da Fase 0 (seção 2.5) e aos campos de CNPJ do dicionário (829 entidades). Documento de proposta e controle: nada foi alterado no dicionário. O dicionário só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026

*Nota de 13/10/2026: as decisões D-N117 (matriz pelo indicador, não pelo sufixo 0001), respondidas por Alberto, foram aplicadas no dicionário na revisão 5 (documento 58; 846 entidades). Os totais e as contagens deste documento valem para a data em que foi escrito; o que continua provisório está na seção 8 do documento 58.*

# 1. Resumo

O PDF **fecha a pendência das letras** que estava na lista de materiais do documento 45. A Receita diz que o CNPJ alfanumérico usa os números de 0 a 9 e **quaisquer das 26 letras de A a Z** (maiúsculas), e que as adaptações dos sistemas devem considerar todas as letras do alfabeto: as combinações proibidas são controladas pela própria Receita na geração. A lista de letras vedadas (I, O, U, Q e F) que o documento 45 guardava como parâmetro **não tem fonte e sai da pendência**.

O tipo lógico CNPJ do dicionário (Fase 0, seção 2.5) já está de acordo: 14 posições, sem máscara, letras de A a Z e números nas 12 primeiras posições, dois dígitos verificadores numéricos e o valor de cada caractere igual ao código ASCII menos 48. A leitura achou **uma decisão nova** (D-N117) e **um conflito com uma confirmação anterior de Alberto**: o sufixo "0001" deixa de ser identificador definitivo de matriz, e o dicionário usa o "0001" para achar a matriz de um participante.

# 2. O que o PDF diz

| Ponto | Regra | Pergunta |
|---|---|---|
| Formato | 14 posições, máscara igual à do CNPJ numérico (AA.AAA.AAA/AAAA-DV); as 12 primeiras posições (raiz e ordem) podem ter letras; o DV é numérico, por módulo 11 | 2 e 21 |
| Caracteres | 0 a 9 e A a Z maiúsculas; os sistemas devem aceitar todas as letras; a Receita controla internamente as combinações proibidas | 1, 38 e 45 |
| Dígito verificador | Módulo 11 com o valor de cada caractere igual ao código ASCII menos 48; pesos 2 a 9 da direita para a esquerda, repetindo; o segundo DV repete o cálculo com o primeiro incluído | 14 |
| Início | A partir de julho de 2026, só em **novas inscrições**, inclusive filiais de empresas que já existem; os CNPJs atuais não mudam e os dois formatos convivem | 4, 5, 6, 15 e 20 |
| Atribuição | Aleatória: uma inscrição nova pode vir só com números mesmo depois de julho de 2026; as letras não carregam UF, natureza jurídica nem outro atributo | 18, 27 e 28 |
| Raiz e filial | A raiz (8 primeiras posições) pode ser alfanumérica e a ordem da filial (9ª a 12ª) numérica, ou o contrário; a raiz é a mesma da matriz e das filiais | 17 e 23 |
| **Sufixo 0001** | Continua indicando a matriz **na geração**, mas deixa de ser definitivo: com o tempo uma filial pode virar a matriz, com ordem diferente de 0001 | 25 |
| MEI | O MEI atual não muda; MEI novo pode ter CNPJ alfanumérico | 30 e 31 |
| PIX e DARF | A chave PIX com CNPJ continua; o DARF não numerado aceita CNPJ alfanumérico | 46 e 52 |
| Teste | **Simulador Nacional de CNPJ**: gera até 1.000 CNPJs fictícios (matriz e filial) por usuário, valida a formação e os dígitos verificadores, e funciona no navegador, mesmo sem internet depois de carregado | 47 a 51 |

# 3. Cruzamento com o dicionário

| Ponto do PDF | No dicionário | Resultado |
|---|---|---|
| Tipo CNPJ de 14 caracteres, letras de A a Z, DV numérico por ASCII menos 48 | Fase 0, seção 2.5: tipo lógico "CNPJ" (revisão 41) | Coberto, com o mesmo texto |
| Todos os campos de CNPJ como código, nunca número | Regra da seção 2.6; campos como `Cad_Participante.Documento_Principal`, `Cnpj_Ente`, `Cnpj_Recebedor`, `Cnpj_Centralizador`, `Sindicato_Cnpj` | Coberto |
| Raiz = 8 primeiros caracteres | `Cad_Participante.CNPJ_Raiz` (calculado) | Coberto |
| Chave de acesso de 44 caracteres | Seção 2.5 | Coberto |
| MEI, filial e PIX com CNPJ alfanumérico | Sem regra específica | Cabe no tipo; nada a mudar |
| **Matriz pelo sufixo 0001** | `Cad_Participante.Propagar_Limite_Credito` ("preenchido só na matriz, o participante cuja `Documento_Principal` é a raiz, '0001'") e o texto do módulo de Contas a Pagar/Receber | **Conflito: D-N117** |
| Matriz de uma empresa do próprio grupo | `Cad_Filial.Indicador_Matriz` | Coberto: já é um indicador, não o sufixo |
| Letras vedadas (I, O, U, Q e F) | Nenhum campo; só a nota do documento 45 | Sai da pendência: valem as 26 letras |

# 4. Decisão proposta

| ID | Proposta | Motivo |
|---|---|---|
| D-N117 | `Indicador_Matriz` (booleano, opcional, só para pessoa jurídica) em `Cad_Participante`: indica o estabelecimento principal da raiz. `Propagar_Limite_Credito` e qualquer regra de "matriz" passam a usar esse indicador, e não o sufixo "0001". No cadastro novo, o campo nasce marcado quando a ordem é 0001, e o usuário (ou a consulta cadastral, quando houver) corrige se a matriz mudou | A Receita diz que o 0001 só indica a matriz na geração e que uma filial pode virar matriz (pergunta 25). Na revisão 7, Alberto confirmou o 0001 como convenção padrão para a propagação do limite de crédito; o PDF muda esse pressuposto |

Se D-N117 for aceita, a descrição de `Propagar_Limite_Credito` muda e o texto do módulo de Contas a Pagar/Receber (seção do limite de crédito) acompanha. Nenhuma outra entidade precisa mudar.

# 5. Regras de validação (sem campo novo)

1. **Aceitar** só 0 a 9 e A a Z maiúsculas nas 12 primeiras posições; letra minúscula digitada é convertida para maiúscula antes de validar. Nenhuma letra é recusada por ser "vedada".
2. **Dígitos verificadores** calculados como no PDF: valor do caractere = código ASCII menos 48, pesos de 2 a 9 da direita para a esquerda, repetindo; resto menor que 2 dá DV zero, e o segundo DV inclui o primeiro. Casos de teste conferidos por mim com o algoritmo: `12ABC34501DE` dá DV 35 (o exemplo do manual); `123456780001` dá 95; `12345678000A` dá 08; `AA345678000A` dá 29. O exemplo 1 da pergunta 23 (`AA3456780003`, mostrado com DV 29) **não fecha**: o algoritmo dá 86. Os outros quatro fecham, então é provável erro de digitação do PDF; vale conferir no Simulador.
3. **Raiz e ordem** são independentes: raiz numérica com ordem alfanumérica é válida, e o contrário também.
4. **Não inferir** UF, natureza jurídica nem matriz a partir das letras ou do sufixo (D-N117).
5. **Convivência**: CNPJ numérico e alfanumérico valem em todos os processos; a máscara é só de tela e a gravação é sem máscara, com 14 caracteres e zeros à esquerda preservados.
6. **Teste de homologação**: usar o Simulador Nacional de CNPJ para gerar e validar casos (matriz e filial) antes de ligar a emissão e as obrigações com CNPJ novo. Os arquivos oficiais (EFD, DIMOB, DeSTDA e outros) já estão nos documentos de desenho com o campo como código.

# 6. O que ainda falta

1. **Confirmar o exemplo 1 da pergunta 23** (`AA345678/0003-29`) no Simulador, ou o rotina oficial de cálculo da Receita "em linguagens mais usuais", que o PDF diz que será disponibilizada.
2. **Calendário** de quais tipos de empresa ou atividade recebem primeiro o CNPJ alfanumérico (pergunta 5: ainda a ser elaborado).

# 7. Perguntas para Alberto

| ID | Pergunta | Se não responder |
|---|---|---|
| D-N117 (respondida em 12/10/2026: **sim, como recomendado**) | Troca do critério "sufixo 0001" pelo indicador de matriz no participante (seção 4) | Respondida: entra na próxima rodada de consolidação |

# 8. Fontes e verificação

**Oficial.** PDF "CNPJ alfanumérico" da Receita Federal, 14 páginas, perguntas 1 a 52, lido inteiro. Não tem data nem versão no texto; ele cita a IN RFB nº 2.119/2022, alterada pela IN RFB nº 2.229/2024, e o início em julho de 2026. A Fase 0 cita também a IN RFB nº 2.333/2026 (início em 31/07/2026), que não consta neste PDF.

**Verificação feita.** Implementei o algoritmo do dígito verificador e conferi os exemplos do PDF (seção 5, regra 2). Conferi cada campo citado contra o dicionário de 829 entidades e contra o texto da Fase 0.

**Não verificado.** A data de 31/07/2026 da IN 2.333/2026 contra o texto da instrução; o exemplo 1 da pergunta 23; o calendário de adoção por tipo de empresa.
