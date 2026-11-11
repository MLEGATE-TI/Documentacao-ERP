# Registro 0000 da ECF: Situação de Início de Período, Situação Especial e Eventos da SCP — Documento 192

*Você enviou em 09/11/2026 o Manual de Orientação do Leiaute 12 da ECF (atualização de 23/07/2026, 622 páginas) sem mensagem e escolheu **"Desenhar o registro 0000"**. O manual é a mesma edição que o projeto já usa (documentos 98, 136 e 179). Ao conferir o registro 0000 contra o modelo, achei que o dicionário **não tem** os campos da ECF para a situação de início do período, a situação especial, a data do evento, o patrimônio remanescente de cisão, o tipo da ECF e o evento da SCP. Este documento é **proposta**: **nada foi alterado no dicionário** (revisão 34: 1.135 entidades e 12.739 campos; com os documentos 189 a 191 aprovados: 1.136 entidades e 12.749 campos).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O manual não traz o texto das fórmulas** das tabelas dinâmicas, então **não fecha a Q179-3**. Ele diz **onde está a planilha**: o arquivo "Tabelas_Dinamicas_ECF_Leiaute_12_AC2025_SIT_ESP_2026.xlsx", no endereço http://sped.rfb.gov.br/pasta/show/1644 (Anexo I, página 620). As regras de validação ficam na pasta do programa da ECF (`C:\Arquivos de Programas RFB\Programas SPED\ECF\recursos\tabelas`, capítulo 3, seção 3.2). A Q179-3 segue **aberta** (seção 2).
- **Lacuna encontrada:** o registro 0000 da ECF tem 16 campos. O dicionário cobre 9 deles pelos campos genéricos de `Mov_Escrituracao_Arquivo` e de `Cad_Empresa`. **Faltam 7**: `IND_SIT_INI_PER` (9 valores, de 0 a 8), `SIT_ESPECIAL` (10 valores, de 0 a 9), `PAT_REMAN_CIS`, `DT_SIT_ESP`, `TIP_ECF`, `EVENTO_SCP` (**novo em 23/07/2026**) e a marca "F" do campo `RETIFICADORA` (original com mudança de forma de tributação). Mais um campo do 0010, o `HASH_ECF_ANTERIOR`, que o manual liga à situação de início do período.
- **Proposta (Q192-1 a Q192-6):** **1 entidade nova**, `Mov_Ecf_Periodo` (**10 campos**), no mesmo padrão de `Mov_Ecd_Periodo`; **3 domínios novos** com 21 valores em `Cad_Classe_Sistema`; **11 avisos do Motor**; nenhuma regra bloqueia.
- **O manual tem inconsistências** que o ERP não pode resolver sozinho (seção 6): a tabela das situações especiais manda usar o indicador 2 e o 4 para a segunda ECF da incorporadora e do desenquadramento, mas a lista do campo 6 e o texto da seção 1.31 trazem o 6 e o 5; e a regra do `DT_FIN` chama o valor 7 de "Transformação", enquanto a tabela chama de "Mudança de Qualificação". Proponho levar à Receita (Q192-7) e ao contador (C223).
- **Contagem:** este documento propõe **+1 entidade e +10 campos**. Aprovados os documentos 189 a 192: **1.137 entidades e 12.759 campos**.

# 2. O que o manual trouxe e o que ele não resolve

| Ponto | O que o manual diz | Efeito no projeto |
|---|---|---|
| Planilha das tabelas dinâmicas | Arquivo único para todos os anos-calendário de 2021 em diante: "Tabelas_Dinamicas_ECF_Leiaute_12_AC2025_SIT_ESP_2026.xlsx", em sped.rfb.gov.br/pasta/show/1644 | **É a planilha da Q179-3 (1).** Ainda preciso do arquivo; o manual só dá o nome e o endereço |
| Regras de validação das tabelas | Arquivos "SPEDECF_DINAMICO_AAAA$SPEDECF_DINAMICA_..._REGRAS" na pasta do programa da ECF | Não estão no manual; saem da instalação do programa da ECF |
| Texto das fórmulas | O manual do leiaute 12 não traz | A pergunta 10 do documento 179 continua rascunho |
| Alterações de 23/07/2026 (Anexo II, item II.4) | Campo `EVENTOS_SCP` no 0000; opção 8 no `IND_SIT_INI_PER`; regras novas; ajuste na regra do `DT_FIN`; texto novo na seção 1.31 | **É a lacuna deste documento** |

A planilha do **leiaute 11** (2025), que traz o texto de 2024 das fórmulas N620 18, N620 19 e N630A 18 (Q152-4), **não aparece** no manual. A Q179-3 fica assim: faltam as **duas planilhas**, como registrei na D-N516.

# 3. O registro 0000 contra o dicionário

O 0000 identifica a escrituração por CNPJ básico, `COD_SCP` e `DT_FIN`, e tem ocorrência 1 para 1 (manual, páginas 61 a 67). Conferi os 16 campos.

| Nº | Campo do manual | O que é | Hoje no dicionário |
|---|---|---|---|
| 3 | `COD_VER` | Versão do leiaute (0012 para o AC 2025 e as situações especiais de 2026) | **Coberto:** `Mov_Escrituracao_Arquivo.Versao_Leiaute` |
| 4 e 5 | `CNPJ`, `NOME` | Declarante (na SCP, o CNPJ do sócio ostensivo) | **Coberto:** `Cad_Empresa` |
| 6 | `IND_SIT_INI_PER` | Situação no início do período: **9 valores (0 a 8)** | **Falta na ECF.** Existem `Mov_Ecd_Periodo.Situacao_Inicio_Periodo` (4 valores, da ECD) e `Mov_Lcdpr_Periodo.Situacao_Inicial` (3 valores, do LCDPR) |
| 7 | `SIT_ESPECIAL` | Situação especial e outros eventos: **10 valores (0 a 9)** | **Parcial:** `Mov_Escrituracao_Arquivo.Situacao_Especial` (5 valores, com o nome de campo da EFD) e `ID_Tipo_Evento_Especial` não distinguem incorporada e incorporadora, cisão parcial, mudança de qualificação, desenquadramento de imune ou isenta e inclusão no Simples |
| 8 | `PAT_REMAN_CIS` | Percentual do patrimônio remanescente na cisão parcial (0 a 100); "necessário para o controle de saldos na conta da parte B do Lalur" | **Falta** |
| 9 | `DT_SIT_ESP` | Data do evento (deliberação) ou, na extinção, a da conclusão da liquidação | **Parcial:** `Data_Evento_Especial` é genérico e hoje serve ao cálculo do prazo |
| 10 e 11 | `DT_INI`, `DT_FIN` | Período da escrituração | **Coberto:** `Periodo_Inicio` e `Periodo_Fim` |
| 12 | `RETIFICADORA` | S retificadora, N original, **F original com mudança de forma de tributação** (IN RFB 2.004/2021, art. 7º, § 2º) | **Parcial:** `Finalidade` cobre S e N; **falta o F** |
| 13 | `NUM_REC` | Recibo da ECF anterior (obrigatório com S ou F) | **Coberto:** `Numero_Recibo_Anterior` |
| 14 | `TIP_ECF` | 0 empresa sem SCP, 1 sócio ostensivo de SCP, 2 ECF da SCP | **Falta na ECF** (a ECD tem `Tipo_Ecd`) |
| 15 | `COD_SCP` | CNPJ da SCP, só na ECF da própria SCP | **Coberto:** `ID_Entidade_Ligada`, que leva ao CNPJ da SCP |
| 16 | `EVENTO_SCP` | 0 normal, 1 alteração do sócio ostensivo (**novo em 23/07/2026**) | **Falta** |
| 0010, campo 2 | `HASH_ECF_ANTERIOR` | Hashcode da ECF do período anterior, que o programa **recupera** para os saldos iniciais da parte B (lucro real) | **Não achei campo com esse nome** (seção 8) |

A quantidade de SCP do sócio ostensivo (`IND_QTE_SCP`) **já está** em `Mov_Ecf_Escolha_Contador_Ano.Quantidade_Scp` (D-N365).

# 4. Proposta (Q192-1 a Q192-6): `Mov_Ecf_Periodo` e três domínios

## 4.1 A entidade

`Mov_Ecf_Periodo`, módulo Contabilidade & Fiscal, **sem vigência** (é movimento), **uma linha por arquivo da ECF**, no padrão de `Mov_Ecd_Periodo`. Como o arquivo fechado é um retrato congelado, os campos do 0000 ficam gravados aqui e o arquivo sai sempre igual ao que foi fechado.

| Campo | Tipo | Descrição |
|---|---|---|
| `ID_Ecf_Periodo` | identificador | Chave da linha |
| `ID_Escrituracao_Arquivo` | referência (`Mov_Escrituracao_Arquivo`), única | O arquivo da ECF a que o período pertence |
| `ID_Situacao_Inicio_Periodo` | referência (`Cad_Classe_Sistema`, domínio `ecf_situacao_inicio_periodo`) | 0000, campo 6 |
| `ID_Situacao_Especial` | referência (`Cad_Classe_Sistema`, domínio `ecf_situacao_especial`) | 0000, campo 7 |
| `Data_Situacao_Especial` | data, opcional | 0000, campo 9 (`DT_SIT_ESP`); vazia quando a situação é normal |
| `Percentual_Patrimonio_Remanescente_Cisao` | número com 4 casas decimais, opcional | 0000, campo 8 (`PAT_REMAN_CIS`), de 0 a 100; só na cisão parcial; alimenta o controle de saldos da parte B |
| `Tipo_Ecf` | enumeração {empresa_sem_scp, socio_ostensivo_de_scp, scp} | 0000, campo 14; o ERP sugere a partir das entidades ligadas e o contador confirma |
| `ID_Evento_Scp` | referência (`Cad_Classe_Sistema`, domínio `ecf_evento_scp`), opcional | 0000, campo 16 (`EVENTO_SCP`); só na ECF da SCP |
| `Mudanca_Forma_Tributacao` | booleano | `RETIFICADORA` = "F": ECF original com mudança de forma de tributação; exige o recibo anterior |
| `Hash_Ecf_Anterior` | código (até 40), opcional | 0010, campo 2 (`HASH_ECF_ANTERIOR`) |

## 4.2 Os três domínios (21 valores, carga provisória)

Os valores ficam em `Cad_Classe_Sistema`, como os outros domínios abertos: a Receita já acrescentou valores a estas listas em 2026, e valor novo é linha nova, sem mudar o dicionário. Todos entram como **provisório** até o contador validar (Q192-2).

- **`ecf_situacao_inicio_periodo` (9):** 0 Regular (início no primeiro dia do ano); 1 Abertura (início de atividades no ano-calendário); 2 Resultante de fusão ou cisão total; 3 Resultante de mudança de qualificação da pessoa jurídica; 4 Início de obrigatoriedade no curso do ano-calendário (exclusão do Simples); 5 Resultante de desenquadramento como imune ou isenta do IRPJ; 6 Realizou incorporação ou remanescente de cisão parcial; 7 Retorno às atividades de empresas inativas; 8 Alteração do sócio ostensivo.
- **`ecf_situacao_especial` (10):** 0 Normal; 1 Extinção; 2 Fusão; 3 Incorporação (incorporada); 4 Incorporação (incorporadora); 5 Cisão total; 6 Cisão parcial; 7 Mudança de qualificação da pessoa jurídica; 8 Desenquadramento de imune ou isenta; 9 Inclusão no Simples Nacional.
- **`ecf_evento_scp` (2):** 0 Normal; 1 Alteração do sócio ostensivo.

O código de cada valor é o número do manual.

## 4.3 A relação com os campos genéricos (Q192-4)

Para a ECF, `Mov_Escrituracao_Arquivo.Situacao_Especial`, `ID_Tipo_Evento_Especial` e `Data_Evento_Especial` **ficam vazios** e a `Finalidade` é `original` ou `substituta`; a situação especial da ECF mora só em `Mov_Ecf_Periodo`, para não haver duas verdades. O **prazo de entrega** da situação especial passa a ler `Data_Situacao_Especial`, pela regra de vencimento com vigência (`Cad_Regra_Vencimento`, que já existe), sem campo novo. As regras do manual são:

- **Situações 1 a 6 (extinção, fusão, incorporada, incorporadora, cisão total e cisão parcial):** a ECF vai até o **último dia útil do 3º mês** depois do evento; se o evento foi de janeiro a abril, até o **último dia útil de julho**.
- **Incorporadora e cisão parcial:** são **duas ECFs**; a segunda, do dia seguinte ao evento até 31/12, vai no **prazo normal**.
- **Situações 7 e 8 (duas ECFs) e 9 (uma ECF):** todas no **prazo normal**.

# 5. Como cada situação preenche o 0000

O quadro junta a tabela do manual (página 61 e seguintes) com a regra de validação do `DT_FIN`.

| Situação (`SIT_ESPECIAL`) | ECFs | `DT_FIN` da 1ª ECF | `IND_SIT_INI_PER` da 2ª ECF, pela tabela | Pela lista do campo 6 |
|---|---|---|---|---|
| 1 Extinção | 1 | `DT_SIT_ESP` | não há | não se aplica |
| 2 Fusão | 1 | `DT_SIT_ESP` | não há | a empresa nova usa 2 |
| 3 Incorporada | 1 | `DT_SIT_ESP` | não há | não se aplica |
| 4 Incorporadora | 2 | `DT_SIT_ESP` | **2** | **6** (realizou incorporação) |
| 5 Cisão total | 1 | `DT_SIT_ESP` | não há | as empresas novas usam 2 |
| 6 Cisão parcial | 2 | `DT_SIT_ESP` | 6 | 6 |
| 7 Mudança de qualificação | 2 | `DT_SIT_ESP` menos 1 dia | 3 | 3 |
| 8 Desenquadramento de imune ou isenta | 2 | `DT_SIT_ESP` menos 1 dia | **4** | **5** |
| 9 Inclusão no Simples | 1 | `DT_SIT_ESP` menos 1 dia | não há | não se aplica |

Em todas, a segunda ECF leva `SIT_ESPECIAL` = 0. Nas duas linhas em negrito a tabela e a lista **divergem** (seção 6).

**Alteração do sócio ostensivo (novo em 23/07/2026, seção 1.31).** Quando o sócio ostensivo muda sem ser situação especial da SCP (por exemplo, o sócio é incorporado por outra empresa), a SCP entrega **duas ECFs e pelo menos duas ECDs**. A primeira, de janeiro até a data da troca, leva `IND_SIT_INI_PER` = 0, `SIT_ESPECIAL` = 0, `TIP_ECF` = 2, o CNPJ da SCP e `EVENTO_SCP` = 1 (o `DT_FIN` fica editável para a data da troca). A segunda, da troca até 31/12, leva `IND_SIT_INI_PER` = 8 e `EVENTO_SCP` = 0. O exemplo do manual usa as empresas Alfa (até 30/06) e Beta (de 01/07 a 31/12).

# 6. Inconsistências do manual

1. **Segunda ECF da incorporadora:** a tabela da página 61 manda usar o indicador **2** ("resultante de cisão/fusão ou remanescente de cisão, ou realizou incorporação"); a lista do campo 6 e a seção 1.3 (recuperação da ECF anterior, a partir do leiaute 11) usam o **6** ("realizou incorporação ou remanescente de cisão parcial"). Leitura minha: a tabela ficou com o texto do leiaute 10.
2. **Segunda ECF do desenquadramento de imune ou isenta:** a tabela manda o **4** (exclusão do Simples); a lista traz o **5**, específico para o desenquadramento, e a seção 1.31 também. Leitura minha: vale o 5.
3. **Valor 7 do `SIT_ESPECIAL`:** a regra do `DT_FIN` o chama de "Transformação"; a tabela e a lista, de "Mudança de Qualificação da Pessoa Jurídica". Leitura minha: é o mesmo evento.

O que o PVA aceita de fato não está no manual; é pergunta à Receita (Q192-7) e confirmação do contador (C223). **Até a resposta, o ERP segue a lista do campo 6** (6, 5 e 7 acima) **e avisa o contador**.

# 7. Avisos do Motor (Q192-5)

O ERP só registra e avisa; o PVA é que rejeita. Cada aviso vem das regras de validação do manual (páginas 66 e 67):

1. `DT_INI` anterior a 01/01/2014.
2. Situação de início 0 com `DT_INI` diferente de 01/01 do ano.
3. Situação especial 0 e `EVENTO_SCP` 0 (ou vazio) com `DT_FIN` diferente de 31/12.
4. Situações 1 a 6 com `DT_FIN` diferente de `DT_SIT_ESP`; situações 7 a 9 com `DT_FIN` diferente de `DT_SIT_ESP` menos 1 dia.
5. `DT_INI` e `DT_FIN` de anos diferentes.
6. `DT_SIT_ESP` vazia com situação especial diferente de 0, ou preenchida com situação 0.
7. `PAT_REMAN_CIS` vazio na cisão parcial (situação 6) ou preenchido nas outras situações.
8. `EVENTO_SCP` vazio na ECF da SCP com situação especial 0, ou preenchido fora da ECF da SCP ou com situação especial diferente de 0.
9. Retificadora (S) ou "F" sem o recibo anterior; original (N) com recibo anterior.
10. Abertura (situação de início 1) com `DT_INI` diferente da data de abertura do CNPJ (`Cad_Empresa.Data_Inicio_Atividade`); retorno às atividades (situação de início 7) sem lembrar que a inatividade precisa estar informada à Receita (DCTF Inativa ou equivalente, seção 1.31).
11. Lucro real com situação de início 0, 3 ou 6 e `DT_INI` diferente de 01/01/2014, **sem o hash da ECF anterior**: o programa exige recuperar a ECF do período anterior (seção 1.3, a partir do leiaute 11).

# 8. O `HASH_ECF_ANTERIOR` (Q192-6)

O manual diz que, no lucro real, o programa da ECF **exige recuperar a ECF do período imediatamente anterior** quando a situação de início é 0, 3 ou 6, e que a falta é verificada na **transmissão**. O hash dessa ECF vai no 0010 (campo 2), e os saldos iniciais da parte B e das contas referenciais dependem dele (por exemplo, `L100.VAL_CTA_REF_INI`). Procurei campo com esse nome ou com essa descrição em todas as entidades do modelo e **não achei**. `Mov_Ecf_Importacao_Bloco` guarda a importação de um arquivo de fora, e a ligação entre uma ECF e a anterior não está registrada. Proponho o campo `Hash_Ecf_Anterior` em `Mov_Ecf_Periodo`, preenchido com o `Hash_Escrituracao` da ECF aceita do período anterior, por ele já existir em `Mov_Escrituracao_Arquivo`. Se você preferir tratar a recuperação em documento próprio (ela mexe nos saldos da parte B), diga na Q192-6.

# 9. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Revisão 34 (documento 186) | 1.135 | 12.739 |
| Documentos 189 a 191, aprovados (D-N513 e D-N515) | +1 | +10 |
| **Subtotal aprovado** | **1.136** | **12.749** |
| Este documento: `Mov_Ecf_Periodo` | +1 | +10 |
| **Total se você aprovar este documento** | **1.137** | **12.759** |

Sem a Q192-6, o total de campos é 12.758. Domínios: 3 novos, com 21 linhas de carga provisória.

# 10. Perguntas para você

| Nº | Pergunta | Minha recomendação |
|---|---|---|
| **Q192-1** | Criar `Mov_Ecf_Periodo` (10 campos), uma linha por arquivo da ECF, no padrão de `Mov_Ecd_Periodo`? | **Sim** |
| **Q192-2** | Os 3 domínios (`ecf_situacao_inicio_periodo`, `ecf_situacao_especial` e `ecf_evento_scp`, 21 valores) entram em `Cad_Classe_Sistema`, com carga provisória até o contador validar? | **Sim** |
| **Q192-3** | `Tipo_Ecf` fica gravado (como `Tipo_Ecd` na ECD), sugerido pelo ERP a partir das entidades ligadas e confirmado pelo contador? | **Sim** |
| **Q192-4** | Na ECF, os campos genéricos de situação especial de `Mov_Escrituracao_Arquivo` ficam vazios, a `Finalidade` é original ou substituta e o prazo da situação especial lê `Data_Situacao_Especial` pela regra de vencimento? | **Sim** |
| **Q192-5** | Os 11 avisos do Motor da seção 7, só como aviso? | **Sim** |
| **Q192-6** | O campo `Hash_Ecf_Anterior` entra agora, junto do 0000? Ou a recuperação da ECF anterior fica em documento próprio? | **Entrar agora**, e o documento próprio só se houver mais campos |
| **Q192-7** | Levar as três inconsistências da seção 6 à Receita, como **pergunta 27 do documento 179** (você envia pelo Fale Conosco)? | **Sim** |

**Texto para a pergunta 27 (se aprovada):** *Prezados, no Manual de Orientação do Leiaute 12 da ECF (atualização de 23/07/2026), registro 0000, a tabela das situações especiais (p. 61 e 62) manda preencher o `IND_SIT_INI_PER` da segunda ECF com 2 na incorporadora e com 4 no desenquadramento de imune ou isenta, mas a lista do campo 6 (p. 63) e a seção 1.31 trazem o 6 (realizou incorporação) e o 5 (desenquadramento de imune ou isenta). Além disso, a regra do `DT_FIN` (p. 67) chama o valor 7 do `SIT_ESPECIAL` de "Transformação", e a tabela e a lista o chamam de "Mudança de Qualificação da Pessoa Jurídica". Pergunto: (1) quais indicadores o PVA aceita na segunda ECF da incorporadora e do desenquadramento; (2) se o valor 7 é o mesmo evento da mudança de qualificação; (3) se o manual será corrigido e em que versão.* Pedido: o fundamento e a data da correção do manual.

# 11. Perguntas para o contador

Entram no **documento 188**, na Parte 6, e não aqui (D-N501): **C223**, sobre as inconsistências do manual e o que o PVA aceita; **C224**, sobre a alteração do sócio ostensivo de uma SCP (o ERP só gera as duas ECFs se o sócio incorporado e o sucessor existirem como empresas no cadastro).

# 12. Limites do que eu li

- Conferi o registro **0000** (páginas 61 a 67), a seção 1.31 (páginas 28 e 29), a seção 1.3 (recuperação da ECF anterior), o Anexo I (página 620) e a lista de alterações (página 622). O campo `HASH_ECF_ANTERIOR` é do 0010; **não conferi o 0010 inteiro**.
- **Não li** o manual inteiro e **não conferi** as demais alterações do Anexo II: o TEF e a SAF de 20/05/2026, a obrigatoriedade do Y600 de 09/07/2026 e as linhas novas das tabelas dinâmicas.
- Os prazos da seção 4.3 são os da tabela do manual; **não conferi** com a IN RFB 2.004/2021.
- As leituras das inconsistências (seção 6) são minhas, e o PVA pode aceitar o que o manual não explica.
- O `Tipo_Ecf` sugerido pelas entidades ligadas e o `Hash_Ecf_Anterior` preenchido pela ECF aceita anterior são **desenho meu**; nenhuma recomendação foi confirmada pelo contador.
