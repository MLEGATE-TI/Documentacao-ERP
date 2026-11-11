# Parâmetros das outras obrigações: as linhas do catálogo central — Documento 160

> **O que este documento faz.** É o último da fila que você escolheu (156, 157, 150, 158, 159 e **160**). O documento 155 criou o catálogo central de parâmetros por obrigação (`Cad_Obrigacao_Parametro_Definicao` e `Cad_Obrigacao_Parametro_Valor`) e a tela com uma aba por obrigação, mas só semeou duas linhas. Aqui eu **procuro, em todo o dicionário (revisão 36), onde moram os parâmetros das demais obrigações**, **classifico cada um** e **proponho as linhas do catálogo** (carga, sem entidade nova), incluindo a linha da Q93-6 (indicador de atividade rural), que você ainda não tinha visto.
>
> **Nada foi aplicado ao dicionário.** Ele continua na revisão 36 (1.144 entidades e 12.860 campos). Este documento só entra na revisão 37 depois das suas respostas às perguntas da seção 7 e de você mandar "consolidar".

*Fontes: a sua regra de 29/10/2026 (Q152-1, D-N440) e as respostas Q155-1 a Q155-5 (D-N441); o documento 155; o dicionário na revisão 36 (59 entidades escolhidas pelo nome, com o propósito lido de cada uma); os documentos 93, 118 e 188 (C99). Não consultei norma nova: o assunto é estrutura. As leituras de norma que aparecem vêm dos campos que já estão no dicionário.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que achei.** Os parâmetros de obrigação estão em **cinco lugares**, e não só nos três que o documento 155 contou: (1) o perfil fiscal da empresa (11 campos de obrigação, como o 155 disse); (2) o **perfil fiscal do estabelecimento**, que o 155 não contou: 5 campos da EFD ICMS/IPI; (3) a tabela de **módulos opcionais** `Cad_Empresa_Modulo_Opcional`, com **32 valores**, 29 deles ligados a uma obrigação; (4) **11 tabelas de parâmetro legal ou de cadastro próprio** de uma obrigação (limites da ECF, valores do Simples, DeSTDA, DES-IF, EFD-Reinf e outras); e (5) um campo solto em `Cad_Simples_Opcao` (o regime de apuração do PGDAS-D).
- **Proposta: 59 linhas novas no catálogo, nenhuma entidade nova, nenhum campo novo.** Elas se dividem em quatro classes (seção 3): **17** apontam para um campo que já existe (classe a, a opção B da Q155-2), **29** apontam para o módulo opcional (classe b), **11** mostram em leitura uma tabela própria (classe c) e **2** têm valor central (as duas que ainda não têm onde morar: `atividade_rural` e `obrigada_ecd`). Com as 2 linhas que já existem, o catálogo passa a **61 linhas** em 13 obrigações. A carga está no Anexo A (tabela) e no arquivo `Cad_Obrigacao_Parametro_Definicao_proposta.csv`.
- **Duas mudanças pequenas de texto, não de estrutura** (Q160-3 e Q160-6): o campo `Armazenamento` do catálogo ganha o **terceiro valor `tabela_propria`**, para as 11 tabelas em leitura que você aprovou na Q155-3; e o texto de `Cad_Contribuinte_Reinf.Obrigada_Ecd`, que hoje diz "vem do perfil fiscal da empresa", **passa a dizer de onde vem de verdade**, porque o perfil não tem esse campo.
- **A Q93-6 fica fechada no desenho** (seção 5): a linha `atividade_rural`, da ECF, booleana, de nível empresa, valor central, sem obrigatoriedade, e o campo no perfil **não é criado**.
- **Seis linhas novas em `Cad_Obrigacao_Acessoria`** (Anexo B): PGDAS_D, DAS_MEI, DESTDA, DESIF, DOI e LCDPR. Sem elas, 9 das 59 linhas não têm obrigação dona. As demais obrigações da lista do documento 155 (eSocial, DIRF e DIMOB) **só ganham linha quando tiverem parâmetro** (Q160-4).
- **Fica de fora da regra** (Anexo B): tudo o que decide o **cálculo do tributo** (por exemplo `Incidencia_Pis_Cofins`, `Forma_Apuracao_Irpj`, as tabelas de retenção, de compensação de prejuízo, do TEF e do bônus), a **integração e a emissão de documento**, a **folha** e os **fatos e movimentos**. É a mesma linha que o documento 155 já traçou; aqui ela ganha a lista completa.
- **Perguntas:** Q160-1 a Q160-9 na seção 7, cada uma com recomendação. **Para o contador não há pergunta nova:** a C99 (documento 188) já pede a lista de parâmetros de cada obrigação, e as 61 linhas passam a ser a lista que ele confere e completa.

# 2. O que o documento 155 pediu e o que eu fiz

O documento 155 fechou três coisas que valem aqui: a tela tem **uma aba para cada linha de `Cad_Obrigacao_Acessoria`**, inclusive as que não têm parâmetro (Q155-1); os 11 campos do perfil **ficam onde estão e aparecem na tela** (Q155-2, opção B na leitura que fiz, "migração obrigação por obrigação, depois"); e as **tabelas de parâmetro legal continuam como estão e aparecem em leitura** (Q155-3). A lista de partida do documento 155 (seção 5) era curta de propósito: "A mapear com o contador".

O que fiz foi o mapeamento que dava para fazer **sem o contador**: ler o propósito das 59 entidades de parâmetro, configuração e perfil do dicionário (e os campos das que guardam escolha da empresa), e dizer, para cada parâmetro, em qual das quatro classes ele cai e a qual obrigação pertence. O que **só o contador sabe** (se uma empresa entrega ou não uma obrigação, e quais outras escolhas por empresa existem) continua na C99.

# 3. A regra de classificação

Cada parâmetro cai em **uma** classe. A pergunta que decide é: "isto é uma escolha da empresa, ou um dado da lei, e onde o valor mora hoje?".

| Classe | O que é | Linha do catálogo | Armazenamento |
|---|---|---|---|
| **a** | Escolha da empresa ou do estabelecimento que **já tem campo** (perfil fiscal da empresa, perfil fiscal do estabelecimento, `Cad_Simples_Opcao`) | Uma linha por campo, nível empresa ou filial | `campo_existente`, com `Entidade_Alvo` e `Campo_Alvo` |
| **b** | Módulo ou bloco que a empresa liga e desliga (`Cad_Empresa_Modulo_Opcional`) e que pertence a uma obrigação | Uma linha por módulo, com o `Codigo` igual ao código do módulo | `campo_existente`, apontando para `Habilitado` |
| **c** | Tabela própria da obrigação, com colunas tipadas, vigência e validação (limites, valores, regras por UF ou município, cadastro do contribuinte) | Uma linha por tabela, **em leitura**, com o atalho para a tela da tabela (Q155-3) | `tabela_propria` (valor novo, Q160-3) |
| **central** | Escolha que **não tem campo** em lugar nenhum | Uma linha, com o valor em `Cad_Obrigacao_Parametro_Valor` | `central` |
| **d** | Não é parâmetro de obrigação: decide o cálculo do tributo, a integração, a emissão do documento, a folha, ou é um fato ou movimento | **Sem linha** | Fica onde está (Anexo B) |

**Um caso à parte, sem linha:** as tabelas que **já têm `ID_Obrigacao`** (`Cad_Regra_Vencimento`, `Cad_Obrigacao_Prazo_Entrega`, `Cad_Obrigacao_Leiaute_Versao` e `Cad_Obrigacao_Decadencia`, mais `Mov_Obrigacao_Prazo_Empresa` e `Mov_Escrituracao_Arquivo`, que são movimento, e, pela versão de leiaute, os registros e campos do leiaute em `Cad_Obrigacao_Leiaute_Registro` e `Cad_Obrigacao_Leiaute_Campo`) aparecem na aba da obrigação **pela própria chave estrangeira**, em leitura, num bloco "Prazos, leiaute e decadência". Uma linha de catálogo para elas só repetiria o que a chave já diz.

# 4. O inventário

## 4.1 Por obrigação (as 59 linhas)

| Obrigação | Classe a | Classe b | Classe c | Central | Linhas novas |
|---|---|---|---|---|---|
| ECF | 5 | 0 | 1 | 1 (`atividade_rural`) | 7 (mais a `presumido_somente_por_refis`, que já existe) |
| EFD-Contribuições (SPED_CONTRIBUICOES) | 4 | 0 | 1 | 0 | 5 |
| MIT | 2 | 0 | 0 | 0 | 2 |
| EFD ICMS/IPI (SPED_FISCAL) | 5 | 24 | 1 | 0 | 30 |
| ECD | 0 | 3 | 0 | 1 (`obrigada_ecd`) | 4 |
| PGDAS-D | 1 | 0 | 2 | 0 | 3 |
| DAS-MEI | 0 | 0 | 2 | 0 | 2 |
| DeSTDA | 0 | 0 | 1 | 0 | 1 |
| DES-IF | 0 | 0 | 1 | 0 | 1 |
| EFD-Reinf | 0 | 0 | 2 | 0 | 2 |
| DOI | 0 | 1 | 0 | 0 | 1 |
| LCDPR | 0 | 1 | 0 | 0 | 1 |
| **Total** | **17** | **29** | **11** | **2** | **59** |

Fora desta tabela: **ESCRITURACAO_IBS_CBS** (a linha `gera_rascunho_nota_debito_antecipacao`, que já existe), **DCTFWEB** (a aba fica vazia: não achei parâmetro de DCTFWeb no dicionário) e as demais linhas de `Cad_Obrigacao_Acessoria` que você pedir (Q160-4).

## 4.2 Classe a: os 17 campos que já existem

**Perfil fiscal da empresa (`Cad_Empresa_Perfil_Fiscal`, 11 campos, os mesmos do documento 155):** ECF, 5 (`ID_Forma_Tributacao_Ecf`, `ID_Tipo_Entidade_Imune_Ecf`, `Criterio_Reconhecimento_Receita`, `Optante_Refis` e `ID_Segmento_Plano_Referencial`); EFD-Contribuições, 4 (`ID_Natureza_Pj_Efd`, `ID_Atividade_Preponderante_Efd`, `Metodo_Apropriacao_Credito_Comum` e `Criterio_Escrituracao_Cumulativo`); MIT, 2 (`ID_Qualificacao_Pj_Mit` e `Criterio_Variacao_Monetaria`).

**Perfil fiscal do estabelecimento (`Cad_Filial_Perfil_Fiscal`, 5 campos, o que o documento 155 não contou):** `ID_Indicador_Atividade_Sped` (registro 0000), `ID_Perfil_Efd` (perfil A, B ou C), `ID_Classe_Estabelecimento_Industrial` (registro 0002), `Tipo_Leiaute_Bloco_K` e `Informa_Ordem_Producao_Bloco_K`. Nível filial, porque a EFD ICMS/IPI é por estabelecimento.

**`Cad_Simples_Opcao.Regime_Apuracao` (1 campo):** caixa ou competência, para o PGDAS-D. É o único campo de `Cad_Simples_Opcao` que é parâmetro de obrigação; o resto da tabela (situação, data da opção, forma de ingresso, processo de inclusão) é o **fato** da opção e fica fora.

**Quando o valor muda.** Gravar pela tela um campo de classe a cria **a versão nova do registro dono do campo** (o perfil, ou a opção do Simples), com a data de vigência e o motivo, exatamente como hoje. A tela só mostra o histórico que o registro já guarda; não nasce tabela de histórico.

## 4.3 Classe b: os 32 módulos, 29 em obrigação e 3 fora

`Cad_Empresa_Modulo_Opcional` tem **32 valores** no domínio aberto `modulo_fiscal_opcional`. Distribuição:

| Obrigação | Módulos | Quantos |
|---|---|---|
| EFD ICMS/IPI | `bloco_k_efd`, `subapuracao_icms_efd`, `bloco_b_df_efd`, `aquisicao_utilidades_efd`, `equipamento_fiscal_efd`; as seis de ST (`efd_c176`, `efd_c180`, `efd_c181`, `efd_c185`, `efd_c186`, `efd_1250_1255`); as treze do documento 175 (Bloco 1, varejo, combustível, bilhete e comunicação) | 24 |
| ECD | `ecd_moeda_funcional`, `ecd_subcontas_ras`, `ecd_consolidada` | 3 |
| DOI | `doi` | 1 |
| LCDPR | `lcdpr` | 1 |
| **Fora (classe d)** | `darf_avulso` (uso da tabela de Darf avulso, que não é uma obrigação), `ipi_suspensao` e `ipi_apuracao` (decidem o cálculo e o destaque do IPI, como `Incidencia_Pis_Cofins` decide o do PIS e da Cofins) | 3 |

**O módulo é a única classe em que a linha precisa de uma regra de leitura**, porque a tabela de módulos tem **uma linha por módulo** e o catálogo aponta para **um campo**. A regra (Q160-2, item 1): `Entidade_Alvo = Cad_Empresa_Modulo_Opcional`, `Campo_Alvo = Habilitado`, e a linha da tabela que a tela lê ou grava é a cujo `ID_Modulo_Opcional` tem o código igual ao `Codigo` da definição. Como o código do módulo já é único e estável, **não preciso de campo novo**. A alternativa seria um campo de filtro na definição (+1 campo), e eu não a recomendo.

**Sem linha em `Cad_Empresa_Modulo_Opcional`, o módulo está desligado.** Isso vale para os 13 do documento 175 pela Q175-6 ("nenhum ligado por padrão", lida como "Sim") e é a leitura natural dos demais (o campo se chama "opcional"). Por isso as 29 linhas de módulo têm `Obrigatorio = falso`: a ausência é uma resposta, não uma lacuna.

## 4.4 Classe c: as 11 tabelas próprias

| Obrigação | Tabela | Nível | O que traz |
|---|---|---|---|
| ECF | `Cad_Ecf_Parametro` | global | Limites do Y520, dos ativos no exterior e do país a país |
| EFD ICMS/IPI | `Cad_Icms_Obrigacao_Recolher` | global | Códigos de obrigação de ICMS a recolher e código de receita por UF (tabela 5.4) |
| EFD-Contribuições | `Cad_Efd_Contribuicoes_Opcao_Escrituracao` | filial | Forma de escrituração do Bloco C por filial e grupo de documento |
| PGDAS-D | `Cad_Simples_Parametro` | global | Valor mínimo do DAS, teto e piso do ISS efetivo, Fator r, MAED |
| PGDAS-D | `Cad_Simples_Limite` | global | Limite anual, sublimite, limite de exportação e tolerância |
| DAS-MEI | `Cad_Mei_Parametro` | global | Percentual do INSS e valores fixos por tipo de atividade |
| DAS-MEI | `Cad_Simples_Limite` | global | A mesma tabela do Simples, que traz o limite do MEI |
| DeSTDA | `Cad_Destda_Parametro_Uf` | global | Se a UF exige, dia de entrega, canal e base legal |
| DES-IF | `Cad_Desif_Parametro_Municipio` | global | Regras que cada município define |
| EFD-Reinf | `Cad_Contribuinte_Reinf` | empresa | O cadastro do contribuinte no evento de cadastro (classificação tributária, desoneração, situação da PJ e outros) |
| EFD-Reinf | `Cad_Contribuinte_Reinf_Software_House` | empresa | As software houses da Reinf |

Três observações. **(1)** `Cad_Simples_Limite` aparece duas vezes (PGDAS-D e DAS-MEI), porque o limite do MEI mora na mesma tabela; a linha é uma para cada obrigação, e a tabela é uma só. **(2)** As duas tabelas da Reinf têm **colunas próprias, vigência e dono (a empresa)** e já são a "tela de parâmetros" da obrigação; não faz sentido espalhar os campos delas em linhas de catálogo, e por isso entram em leitura, como as demais. **(3)** `Cad_Efd_Contribuicoes_Opcao_Escrituracao` é de nível **filial**, e o 155 já dizia que ela "não se funde com os parâmetros do 0110, que são por empresa e anuais"; continua separada.

## 4.5 O que `tabela_propria` exige

O catálogo tem hoje, em `Armazenamento`, dois valores: `central` e `campo_existente`. Uma tabela inteira não é nenhum dos dois. A proposta é **acrescentar um terceiro valor, `tabela_propria`**, e, nas linhas desse valor, usar `Tipo_Valor = cadastro` e `Entidade_Referencia` com o nome da tabela (os dois campos já existem e já têm essa leitura: "a entidade referenciada"); `Entidade_Alvo` e `Campo_Alvo` ficam vazios. O custo é **um valor a mais no texto de um campo**, nenhum campo novo (Q160-3). A alternativa é **não ter linha para as tabelas**; aí a aba da obrigação não teria como saber quais tabelas mostrar, e o que você aprovou na Q155-3 ficaria sem mecanismo.

# 5. A Q93-6: a linha `atividade_rural`

**Sua resposta de 22/10/2026:** "sim, indicador de atividade rural no perfil (campo próprio)". Depois, a sua regra de 29/10/2026 (D-N440) e a aprovação da Q155-1 mudaram o destino: parâmetro de obrigação **não nasce como campo solto**. O documento 38 já dizia que a linha ia substituir o campo e que o desenho dela ainda não estava escrito. Está aqui:

| Item | Proposta |
|---|---|
| Obrigação | ECF |
| `Codigo` | `atividade_rural` |
| `Rotulo` | Exerce atividade rural |
| `Tipo_Valor` | booleano |
| `Nivel` | empresa |
| `Obrigatorio` | falso |
| `Armazenamento` | central |
| `Grupo_Tela` e `Ordem_Tela` | Regime de tributação, 60 |
| Efeito | Quando verdadeiro, a ECF do lucro real usa as abas de linhas **M300R e M350R** (atividade rural) da tabela dinâmica da ECF; o documento 93 e a D-N333 já mandavam a atividade rural para pergunta própria, que é esta |
| Valor vazio | Ninguém respondeu: o aviso não dispara (regra do documento 155, "sem padrão escondido") |
| Quem responde | O contador, na aba da ECF; entra provisório e só passa a validado com ele |

**O que isto não faz:** não decide como a atividade rural entra no cálculo do lucro real (o desenho das linhas M300R e M350R vem do documento 93 e das fórmulas); só diz **se a empresa a exerce**. **Leitura minha:** `Obrigatorio = falso`, porque a pergunta só faz sentido para quem tributa pelo lucro real, e a obrigatoriedade condicional ("obrigatória se a forma de tributação é real") não cabe no catálogo (ver Q160-8).

# 6. Duas coisas que achei no caminho

## 6.1 `Cad_Contribuinte_Reinf.Obrigada_Ecd` aponta para um campo que não existe

O texto do campo diz: "indEscrituracao: a empresa é obrigada à Escrituração Contábil Digital. **Vem do perfil fiscal da empresa**." O perfil fiscal da empresa **não tem** esse campo (conferi os 21 campos). Hoje, então, o dado não tem origem.

**Proposta (Q160-6):** a linha `obrigada_ecd` do catálogo, na obrigação ECD, booleana, nível empresa, valor central, `Obrigatorio = falso`. O campo `Obrigada_Ecd` da Reinf **continua** (é o dado do evento, e o evento guarda a cópia de quando foi gerado), e o texto passa a dizer: "copiado, na geração do evento de cadastro, da linha `obrigada_ecd` do catálogo da ECD". Isso corrige o texto de **um campo** e **não muda a estrutura**. Sem a linha, o campo da Reinf não tem de onde ser preenchido.

## 6.2 O texto da linha `gera_rascunho_nota_debito_antecipacao`

A carga de partida do documento 155 (arquivo `Cad_Obrigacao_Parametro_Definicao.csv`, revisão 29) escreveu a obrigação dessa linha como "Apuração do IBS e da CBS (criar em `Cad_Obrigacao_Acessoria` se não existir)". O código que `Cad_Obrigacao_Acessoria` já cita é **`ESCRITURACAO_IBS_CBS`**. Proponho corrigir o texto da carga para esse código (Q160-4), para não nascer uma obrigação duplicada com nome diferente.

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| Q160-1 | Aprova a **regra de classificação em quatro classes** (a campo existente, b módulo, c tabela própria em leitura, d fora) e o **inventário** das seções 3 e 4, com as 59 linhas novas do Anexo A (17 + 29 + 11 + 2) e o bloco "Prazos, leiaute e decadência" pela chave estrangeira? | Sim |
| Q160-2 | Aprova as **quatro convenções sem estrutura nova**: (1) a linha de módulo tem o `Codigo` igual ao código do módulo, e a tela lê `Habilitado` da linha de `Cad_Empresa_Modulo_Opcional` com esse código; (2) campo de enumeração do perfil entra como `Tipo_Valor = lista` com `Dominio_Lista` vazio (a lista é a do próprio campo); (3) `Obrigatorio = verdadeiro` só onde o campo do perfil **não é opcional** (6 linhas), e falso nas demais; (4) gravar um campo de classe a cria a versão nova do registro dono do campo? | Sim |
| Q160-3 | Acrescenta o valor **`tabela_propria`** ao campo `Armazenamento` do catálogo (nenhum campo novo), para as 11 tabelas em leitura da classe c? | Sim |
| Q160-4 | Cria as **6 linhas novas** em `Cad_Obrigacao_Acessoria` (PGDAS_D, DAS_MEI, DESTDA, DESIF, DOI e LCDPR; Anexo B), com início em 01/01/2026 como nos parâmetros da ECF (D-N323), **corrige** o texto da linha `gera_rascunho_nota_debito_antecipacao` para `ESCRITURACAO_IBS_CBS` e **deixa para depois** a linha de eSocial, DIRF, DIMOB e DEFIS, que só entram quando tiverem parâmetro? | Sim |
| Q160-5 | Aprova a **linha `atividade_rural`** da seção 5 (ECF, booleana, empresa, valor central, sem obrigatoriedade) no lugar do campo no perfil? | Sim |
| Q160-6 | Aprova a linha **`obrigada_ecd`** (ECD, booleana, empresa, valor central) e a **correção do texto** de `Cad_Contribuinte_Reinf.Obrigada_Ecd` (seção 6.1)? | Sim |
| Q160-7 | Concorda com a **lista da classe d** do Anexo B, em particular: as tabelas `Cad_Qualificacao_Cbs_Inicio_Obrigacao` e `Cad_Locacao_Obrigacao_Emissao` (quando começa a obrigação de **emitir o documento**, e não de escriturar), `Atividade_Principal_Family_Office` (decide uma regra de tributo) e os módulos `darf_avulso`, `ipi_suspensao` e `ipi_apuracao`? | Sim, ficam fora |
| Q160-8 | Quer um parâmetro padrão em cada obrigação, **"a empresa entrega esta obrigação"** (booleano, empresa ou filial), para que a obrigatoriedade condicional ("obrigatório se a empresa entrega a ECF") e o aviso do Motor tenham de onde ler? Hoje vários campos dizem "vazio quando não entrega" e **nada no dicionário diz quem entrega o quê** | **Não agora.** Depende da resposta do contador à C99 e mexe na geração dos prazos (`Mov_Obrigacao_Prazo_Empresa`); volta num documento próprio |
| Q160-9 | Quer migrar algum campo de classe a **para o valor central** (opção A da Q155-2) já nesta rodada? | Não: a opção B vale; cada obrigação migra quando for revista |

# 8. O que acontece se você aprovar

| Item | Efeito |
|---|---|
| Entidades e campos | **Nenhuma entidade e nenhum campo novo**: continuam 1.144 entidades e 12.860 campos |
| `Cad_Obrigacao_Parametro_Definicao.Armazenamento` | +1 valor de enumeração (`tabela_propria`), só no texto do campo |
| `Cad_Contribuinte_Reinf.Obrigada_Ecd` | Texto corrigido (seção 6.1) |
| Carga | **59 linhas** de definição (todas sem valor; os valores só nascem quando o contador responder) e **6 linhas** de `Cad_Obrigacao_Acessoria` |
| Tela | 13 abas com linha, mais a DCTFWeb e as demais vazias |
| Ondas, DDL e ER | Sem mudança |
| Documentos | 14 (D-N528) e 38 (seção 1.28 e a linha da Q93-6 da seção 0) |

# 9. Limites

- **Escolhi as 59 entidades pelo nome** ("Parametro", "Configuracao", "Opcao", "Limite", "Opcional", "Habilita", "Perfil", "Obrigacao" ou "Contribuinte_Reinf") **e li o propósito de cada uma; os campos eu li nas de perfil, de módulo, da Reinf e das opções do Simples, do MEI e da EFD-Contribuições. Não li as outras 1.085 entidades.** Se houver um parâmetro de obrigação escondido numa entidade que não leva esses nomes, ele não está aqui. A busca nos campos de `Cad_Empresa`, `Cad_Filial` e `Cad_Participante` por nome de obrigação achou só o `Caepf` (para o LCDPR e a DCTFWeb de pessoa física), que é cadastro e fica fora.
- **Não achei no dicionário nem nas cargas uma lista de carga das linhas de `Cad_Obrigacao_Acessoria`.** Tratei como existentes os 8 códigos que o campo `Codigo` cita (SPED_FISCAL, SPED_CONTRIBUICOES, ECD, ECF, REINF, DCTFWEB, MIT e ESCRITURACAO_IBS_CBS) e os 4 módulos DESIF_M1 a M4 que `Mov_Desif_Declaracao` cita. **Confira antes de carregar**; se faltar algum, ele entra na carga do Anexo B.
- **A classificação de cada tabela como "da obrigação" ou "do cálculo do tributo" é leitura minha**, feita pelo propósito da entidade. As mais discutíveis estão na Q160-7.
- **As 59 linhas nascem sem valor.** O catálogo só diz **onde** cada parâmetro mora; **o que a empresa escolheu** continua nos campos de hoje (classe a e b) ou espera o contador (central).
- **Nenhuma linha passa por validação do contador.** As definições não têm `Situacao_Dado`; a validação é do **valor**, e o contador a faz na aba, como o documento 155 desenhou.
- **O prazo, o leiaute e a decadência por obrigação** aparecem na aba pela chave estrangeira; não conferi se os dados dessas tabelas estão completos para as 6 obrigações novas (as linhas novas nascem sem prazo, leiaute e decadência).

# Anexo A. As 59 linhas propostas

O arquivo `Cad_Obrigacao_Parametro_Definicao_proposta.csv` traz as 18 colunas do formato da carga 29 (rótulo, ajuda, grupo e ordem da tela, fundamento, vigência de 01/01/2026 a 31/12/9999 e motivo). A tabela abaixo traz o essencial, na ordem da tela (por grupo e por ordem). Nível: **E** empresa, **F** filial, **G** global.

| Obrigação | Código | Rótulo | Tipo | Nível | Onde mora o valor |
|---|---|---|---|---|---|
| ECF | `segmento_plano_referencial` | Segmento para o plano referencial | lista (segmento_plano_referencial) | E | Perfil da empresa: `ID_Segmento_Plano_Referencial` |
| ECF | `forma_tributacao_ecf` | Forma de tributação na ECF | lista (forma_tributacao_ecf) | E | Perfil da empresa: `ID_Forma_Tributacao_Ecf` |
| ECF | `tipo_entidade_imune_ecf` | Tipo de entidade imune ou isenta na ECF | lista (tipo_entidade_imune_ecf) | E | Perfil da empresa: `ID_Tipo_Entidade_Imune_Ecf` |
| ECF | `criterio_reconhecimento_receita` | Critério de reconhecimento da receita (lucro presumido) | lista | E | Perfil da empresa: `Criterio_Reconhecimento_Receita` |
| ECF | `optante_refis` | Optante do Refis | booleano | E | Perfil da empresa: `Optante_Refis` |
| ECF | `atividade_rural` | Exerce atividade rural | booleano | E | Valor central |
| ECF | `tabela_ecf_parametro` | Limites da ECF (ativos no exterior, cartão e país a país) | cadastro | G | Tabela `Cad_Ecf_Parametro`, em leitura |
| SPED_CONTRIBUICOES | `natureza_pj_efd` | Natureza da pessoa jurídica | lista (natureza_pj_efd_contribuicoes) | E | Perfil da empresa: `ID_Natureza_Pj_Efd` |
| SPED_CONTRIBUICOES | `atividade_preponderante_efd` | Atividade preponderante | lista (indicador_atividade_efd_contribuicoes) | E | Perfil da empresa: `ID_Atividade_Preponderante_Efd` |
| SPED_CONTRIBUICOES | `metodo_apropriacao_credito_comum` | Método de apropriação do crédito comum | lista | E | Perfil da empresa: `Metodo_Apropriacao_Credito_Comum` |
| SPED_CONTRIBUICOES | `criterio_escrituracao_cumulativo` | Critério de escrituração do regime cumulativo | lista | E | Perfil da empresa: `Criterio_Escrituracao_Cumulativo` |
| SPED_CONTRIBUICOES | `tabela_efd_contribuicoes_opcao_escrituracao` | Forma de escrituração do Bloco C por filial e grupo de documento | cadastro | F | Tabela `Cad_Efd_Contribuicoes_Opcao_Escrituracao`, em leitura |
| MIT | `qualificacao_pj_mit` | Qualificação da pessoa jurídica no MIT | lista (qualificacao_pj_mit) | E | Perfil da empresa: `ID_Qualificacao_Pj_Mit` |
| MIT | `criterio_variacao_monetaria` | Critério das variações monetárias no MIT | lista | E | Perfil da empresa: `Criterio_Variacao_Monetaria` |
| SPED_FISCAL | `subapuracao_icms_efd` | Sub-apuração do ICMS (1900 a 1926) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `bloco_b_df_efd` | Bloco B (ISS), só no Distrito Federal | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_exportacao_1100` | Exportação (1100, 1105 e 1110) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_credito_icms_1200` | Controle de créditos de ICMS (1200 e 1210) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_valor_agregado_1400` | Valores agregados, IPM (1400) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_energia_1500` | Energia, saída interestadual (1500 e 1510) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_documento_utilizado_1700` | Documentos em papel (1700 e 1710) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_dcta_1800` | DCTA, transporte aéreo (1800) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_giaf_pe` | GIAF de Pernambuco (1960, 1970, 1975 e 1980) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `tipo_leiaute_bloco_k` | Tipo de leiaute do Bloco K | lista | F | Perfil do estabelecimento: `Tipo_Leiaute_Bloco_K` |
| SPED_FISCAL | `informa_ordem_producao_bloco_k` | Informa ordem de produção no Bloco K | booleano | F | Perfil do estabelecimento: `Informa_Ordem_Producao_Bloco_K` |
| SPED_FISCAL | `bloco_k_efd` | Bloco K (produção e estoque) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_combustivel_c165` | Combustível na nota de saída (C165) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `aquisicao_utilidades_efd` | Aquisição de energia, água e gás com crédito de ICMS | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_convenio_115` | Convênio 115 (C700, C790, C791 e D695 a D697) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `equipamento_fiscal_efd` | ECF, SAT-CF-e e MFE (C400, C800 e correlatos) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_cupom_ecf` | Cupom fiscal de ECF (C400 a C490 e D350 a D390) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_sat_resumo_obs` | Observação do resumo do SAT (C895 e C897) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `indicador_atividade_sped` | Indicador de atividade | lista (indicador_atividade_sped) | F | Perfil do estabelecimento: `ID_Indicador_Atividade_Sped` |
| SPED_FISCAL | `perfil_efd` | Perfil de apresentação (A, B ou C) | lista (perfil_efd) | F | Perfil do estabelecimento: `ID_Perfil_Efd` |
| SPED_FISCAL | `classe_estabelecimento_industrial` | Classe do estabelecimento industrial | lista (classe_estabelecimento_industrial_efd) | F | Perfil do estabelecimento: `ID_Classe_Estabelecimento_Industrial` |
| SPED_FISCAL | `efd_c176` | Ressarcimento de ST (C176) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_c180` | Complemento da entrada de ST (C180) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_c181` | Devolução de saída com ST (C181) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_c185` | Complemento da saída de ST (C185) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_c186` | Entradas ligadas à saída de ST (C186) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_1250_1255` | Ressarcimento consolidado de ST (1250 e 1255) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `tabela_icms_obrigacao_recolher` | Códigos de obrigação de ICMS a recolher por UF (tabela 5.4) | cadastro | G | Tabela `Cad_Icms_Obrigacao_Recolher`, em leitura |
| SPED_FISCAL | `efd_bilhete_passagem` | Bilhetes de passagem e RMD (D300 a D420) | booleano | F | Módulo opcional (`Habilitado`) |
| SPED_FISCAL | `efd_comunicacao_saida` | Comunicação, saída (D500, D510 e D530) | booleano | F | Módulo opcional (`Habilitado`) |
| ECD | `ecd_moeda_funcional` | Moeda funcional na ECD | booleano | E | Módulo opcional (`Habilitado`) |
| ECD | `ecd_subcontas_ras` | Subcontas da Lei 12.973 e razão auxiliar | booleano | E | Módulo opcional (`Habilitado`) |
| ECD | `ecd_consolidada` | Escrituração consolidada (bloco K da ECD) | booleano | E | Módulo opcional (`Habilitado`) |
| ECD | `obrigada_ecd` | Obrigada à Escrituração Contábil Digital | booleano | E | Valor central |
| PGDAS_D | `regime_apuracao_simples` | Regime de apuração da receita no PGDAS-D | lista | E | `Cad_Simples_Opcao.Regime_Apuracao` |
| PGDAS_D | `tabela_simples_parametro` | Valores legais do Simples Nacional | cadastro | G | Tabela `Cad_Simples_Parametro`, em leitura |
| PGDAS_D | `tabela_simples_limite` | Limites e sublimites do Simples Nacional e do MEI | cadastro | G | Tabela `Cad_Simples_Limite`, em leitura |
| DAS_MEI | `tabela_mei_parametro` | Valores do DAS-MEI por tipo de atividade | cadastro | G | Tabela `Cad_Mei_Parametro`, em leitura |
| DAS_MEI | `tabela_simples_limite` | Limites do MEI (mesma tabela do Simples) | cadastro | G | Tabela `Cad_Simples_Limite`, em leitura |
| DESTDA | `tabela_destda_parametro_uf` | Regras da DeSTDA por UF | cadastro | G | Tabela `Cad_Destda_Parametro_Uf`, em leitura |
| DESIF | `tabela_desif_parametro_municipio` | Regras da DES-IF por município | cadastro | G | Tabela `Cad_Desif_Parametro_Municipio`, em leitura |
| REINF | `tabela_contribuinte_reinf` | Cadastro do contribuinte no EFD-Reinf | cadastro | E | Tabela `Cad_Contribuinte_Reinf`, em leitura |
| REINF | `tabela_contribuinte_reinf_software_house` | Software house do EFD-Reinf | cadastro | E | Tabela `Cad_Contribuinte_Reinf_Software_House`, em leitura |
| DOI | `doi` | Entrega a DOI (cartório) | booleano | E | Módulo opcional (`Habilitado`) |
| LCDPR | `lcdpr` | Entrega o LCDPR (produtor rural pessoa física) | booleano | E | Módulo opcional (`Habilitado`) |

# Anexo B. As linhas novas de `Cad_Obrigacao_Acessoria` e o que fica fora

## B.1 Seis linhas novas

| Código | Descrição | Início | Fim |
|---|---|---|---|
| PGDAS_D | PGDAS-D: declaração de apuração mensal do Simples Nacional | 01/01/2026 | 31/12/9999 |
| DAS_MEI | DAS-MEI: guia mensal do microempreendedor individual | 01/01/2026 | 31/12/9999 |
| DESTDA | DeSTDA: declaração de substituição tributária, diferencial de alíquota e antecipação | 01/01/2026 | 31/12/9999 |
| DESIF | DES-IF: declaração eletrônica de serviços das instituições financeiras (módulos M1 a M4) | 01/01/2026 | 31/12/9999 |
| DOI | DOI: declaração sobre operações imobiliárias (cartório) | 01/01/2026 | 31/12/9999 |
| LCDPR | LCDPR: livro caixa digital do produtor rural (pessoa física) | 01/01/2026 | 31/12/9999 |

A data de início é a do **uso no ERP**, como nos parâmetros da ECF (D-N323: valem para 2026, sem histórico anterior), e **não a data legal** da obrigação. Se um cliente precisar de competência anterior a 2026, entra uma versão com início antes.

**DES-IF:** os quatro módulos (DESIF_M1 a M4) já existem como obrigação. A linha nova **DESIF** é a obrigação "guarda-chuva" que recebe a tabela de regras por município, que vale para os quatro módulos. Os módulos continuam sem parâmetro próprio.

## B.2 O que fica fora da regra (classe d), e por quê

| Grupo | Itens | Por que fica fora |
|---|---|---|
| **Decide o cálculo do tributo** | Perfil da empresa: `Incidencia_Pis_Cofins` (e a versão por UF em `Cad_Empresa_Perfil_Fiscal_Uf`), `Forma_Apuracao_Irpj`, `ID_Segmento_Csll`, `Sujeita_Tef_Saf`, `Atividade_Principal_Family_Office`. Perfil do estabelecimento: `Excesso_Sublimite`, `Contribuinte_Icms`, `Contribuinte_Ipi`, `ID_Regime_Apuracao_Icms`. Módulos `ipi_suspensao` e `ipi_apuracao` | Mudam o imposto, não o arquivo da obrigação (a mesma linha que o documento 155 traçou para os quatro primeiros) |
| **Tabelas de regra de tributo** | `Cad_Retencao_Federal_Parametro`, `Cad_Compensacao_Prejuizo_Parametro`, `Cad_Regime_Tef_Parametro`, `Cad_Parametro_Bonus_Adimplencia`, `Cad_Produtor_Rural_Parametro_Cbs`, `Cad_Valor_Mercado_Locacao_Parametro`, `Cad_Distribuicao_Lucro_Parametro`, `Cad_Duimp_Tributo_Parametro`, `Cad_Parametro_Legal_Ibs_Cbs` (o documento 159 já a definiu como "números de lei que não pertencem a nenhuma obrigação") | Parâmetro do cálculo, do título a pagar ou do benefício |
| **Início ou obrigatoriedade de emitir documento** | `Cad_Qualificacao_Cbs_Inicio_Obrigacao`, `Cad_Locacao_Obrigacao_Emissao` | É a obrigação principal de emitir a nota, e não uma obrigação acessória de `Cad_Obrigacao_Acessoria` (Q160-7) |
| **Integração e emissão de documento** | `Cad_Integra_Contador_Configuracao`, `Cad_Dfe_Emitente_Configuracao`, `Cad_Dfe_Parametro_Regra`, `Cad_Nfse_Parametro_Alvo`, `Cad_Filial_Perfil_Fiscal.Numero_Tar` | Credencial, ambiente, certificado e regra do DF-e; o documento 155 já tratava a integração à parte |
| **Folha e jurídico** | `Cad_Rh_Parametro_Irrf`, `Cad_Rh_Parametro_Dsr`, `Cad_Rh_Parametro_Jornada`, `Cad_Rh_Limite_Renda_Dependente_Irrf`, `Cad_Lgpd_Parametro` | Calculam a folha ou o prazo legal; não são escolha de obrigação (a folha não tem obrigação própria no catálogo hoje) |
| **Fatos e movimentos** | `Cad_Simples_Opcao` (menos `Regime_Apuracao`), `Cad_Locacao_Opcao` e `Cad_Locacao_Opcao_Imovel`, `Mov_Ecf_Perfil_Indicador`, `Mov_Obrigacao_Prazo_Empresa`, `Mov_Apuracao_Presuncao_Limite`, `Mov_Mei_Monitoramento_Limite`, `Mov_Locacao_Limite_Pf`, `Mov_Apuracao_Obrigacao_Recolher`, `Cad_Habilitacao_Regime_Especial`, `Cad_Habilitacao_Suframa`, `Cad_Habilitacao_Suframa_Produto`, `Mov_Habilitacao_Suframa_Ocorrencia`, `Cad_Empresa_Profissional_Habilitado` | Registram um ato ou um resultado, e não uma escolha de parâmetro |
| **Módulos fora de obrigação** | `darf_avulso` | Uso de uma tabela de guia, e não uma obrigação |
| **Acesso e motor** | `Cad_Perfil` e `Cad_Usuario_Perfil` (perfil de acesso, que o nome confunde com o perfil fiscal), `Cad_Motor_Aprendizado_Parametro` | Nada a ver com obrigação |
