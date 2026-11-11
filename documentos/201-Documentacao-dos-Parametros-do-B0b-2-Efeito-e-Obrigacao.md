# Documentação dos parâmetros do B0b-2: o efeito de cada um e a obrigação em que ele atua — Documento 201

> **O que este documento faz.** Ao aprovar o documento 200, você pediu que os parâmetros do B0b-2 tenham **documentação própria, dizendo qual é o efeito de cada um e em qual obrigação ele atua**. O B0b-2 tem muitos: as marcas das 28 regras de crédito, os campos de contrato que escolhem a regra, os parâmetros que ele lê de outros cadastros e cinco leituras minhas que eu tinha deixado escritas no texto do Motor. Inventariei **41**, escrevi a documentação de cada um (Anexo A), mapei os **58 efeitos** nas obrigações (Anexo B e C) e propus **duas entidades novas** para que a documentação more no dicionário e apareça na tela, e não só neste Word.
>
> **Nada foi aplicado ao dicionário.** Ele continua na revisão 37 (1.155 entidades e 13.017 campos); o documento 200 foi aprovado (D-N534) e entra no próximo "consolidar" com 1.163 entidades e 13.169 campos. Este documento soma a esse total e só entra depois das suas respostas à seção 7 e de você mandar "consolidar".

*Fontes: o catálogo central de parâmetros por obrigação (documentos 155 e 160; D-N440, D-N441, D-N528 e D-N531); os documentos 198 e 200 (D-N529 a D-N534); o inventário de parâmetros que o documento 160 fez; o documento 32 (a escrituração do IBS e da CBS ainda sem leiaute oficial) e o documento 36 (a Plataforma e a apuração assistida); a LC 214/2025 com a LC 227/2026 e o Decreto 12.955/2026, nos artigos que o documento 200 já citou. **Não li** o leiaute oficial da escrituração do IBS e da CBS (não foi fechado), o manual da DeRE (Q198-12, não chegou) nem o manual do eSocial.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

- **O que achei.** O dicionário já tem o lugar certo para parâmetros de obrigação (a regra D-N440: tela e catálogo central, uma linha por parâmetro). Cada linha do catálogo tem **uma obrigação dona**, um texto de `Ajuda` e o `Fundamento_Legal`. Falta o que você pediu: o **efeito** de cada valor e a lista de **todas as obrigações** em que o parâmetro atua. Hoje isso cabe, no máximo, numa frase da `Ajuda`, como "Campo FORMA_TRIB do registro 0010 da ECF".
- **Os 41 parâmetros do B0b-2 são de quatro tipos.** (A) **12** são as marcas das regras do catálogo `Cad_Regra_Credito_Tomador` (a forma de cálculo, o regime de caixa, a proporção do art. 291, as cinco vedações e condições, a vigência, a situação e a base do fornecedor, mais o próprio catálogo); (B) **20** são **chaves de decisão**, campos de contrato e de movimento que o Motor lê para escolher a regra (a forma de captação do empréstimo, o tipo do arrendamento, o fim do acordo coletivo e outros); (C) **4** são parâmetros que **já existem** e o B0b-2 passa a ler (os seis meses do acordo, a soma das alíquotas, as bases do participante e a qualificação de cooperativa); (D) **5** são as **leituras provisórias** que eu tinha escrito no texto do Motor e que o contador ainda vai confirmar.
- **Os efeitos estão em duas obrigações do catálogo e em uma proposta.** Dos 58 efeitos, **51 aparecem na escrituração do IBS e da CBS** (`ESCRITURACAO_IBS_CBS`: é onde o crédito do tomador é apurado e conferido com a Plataforma), **6 na DeRE** (como fonte do dado do fornecedor, e na dedução da despesa na base do próprio tomador) e **1 no eSocial** (a origem do desconto do plano de saúde). O eSocial ainda não é linha de `Cad_Obrigacao_Acessoria`; a Q201-6 pede a linha. **ECD e ECF ficam sem efeito documentado**: não consegui ancorar numa norma o que o crédito do tomador muda nelas, e a pergunta foi ao contador (C246).
- **Proposta: 2 entidades novas, nenhum campo novo em entidades existentes, nenhum domínio novo.** `Cad_Parametro_Documentacao` (21 campos, com vigência) guarda a documentação de cada parâmetro (o que é, os valores, o padrão, o que acontece sem valor, quem altera, o fundamento). `Cad_Parametro_Efeito_Obrigacao` (14 campos, com vigência) guarda, em uma linha por parâmetro, obrigação e valor, o **tipo do efeito**, o **local da obrigação** em que ele aparece e **o que muda**. Um parâmetro pode atuar em várias obrigações e uma obrigação recebe efeito de vários parâmetros; a tela mostra os dois sentidos.
- **Seis linhas no catálogo central** (`Cad_Obrigacao_Parametro_Definicao`): uma para o catálogo das 28 regras (em leitura, como o documento 160 fez com as 11 tabelas próprias) e **cinco para as leituras provisórias**, por empresa, com o padrão visível e um aviso quando o Motor usa o padrão. É uma exceção à regra "sem padrão escondido" da Q155, e vai à Q201-4.
- **Uma regra geral nova**, para valer daqui em diante: **nenhum parâmetro entra no dicionário sem a documentação do efeito e da obrigação**, e a auditoria da carga acusa o que não tem (Q201-3).
- **Perguntas:** Q201-1 a Q201-10 (seção 7), cada uma com recomendação. **Para o contador:** duas perguntas novas, **C246 e C247** (Anexo E), que entram no documento 188.
- **Se você aprovar:** 1.165 entidades (+2), 13.204 campos (+35), 3.445 chaves estrangeiras (+5), 41 linhas de documentação, 58 de efeito, 6 do catálogo e 1 de `Cad_Obrigacao_Acessoria`; os documentos 14 (D-N535) e 38 (seção 1.31) acompanham.

# 2. O que o dicionário já tem

| Entidade | O que guarda hoje | O que falta para a sua regra |
|---------------------------------|---------------------------------|---------------------------------|
| `Cad_Obrigacao_Parametro_Definicao` (documentos 155 e 160) | Uma linha por parâmetro de obrigação: `ID_Obrigacao` (a **dona**), `Codigo`, `Rotulo`, `Ajuda` ("o que o parâmetro faz, onde a lei ou o manual o cita"), tipo, nível, onde o valor mora (`central`, `campo_existente` ou `tabela_propria`) e `Fundamento_Legal`. 61 linhas, em 13 obrigações. | Só **uma** obrigação por parâmetro. A `Ajuda` é um texto livre: não separa o efeito por valor, nem o local no arquivo, nem as demais obrigações. |
| `Cad_Obrigacao_Parametro_Valor` | O valor por empresa e vigência, com `Situacao_Dado` provisório ou validado. | Nada: é onde o contador responde. |
| `Cad_Obrigacao_Acessoria` | As obrigações (SPED_FISCAL, SPED_CONTRIBUICOES, ECD, ECF, REINF, DCTFWEB, MIT, ESCRITURACAO_IBS_CBS, DERE e mais seis). | Sem linha para o eSocial. |
| `Cad_Parametro_Legal_Ibs_Cbs`, `Cad_Regime_Aliquota_Soma`, `Cad_Componente_Base_Regime` | Parâmetros legais por vigência, cada um com `Fundamento_Legal` e situação. | Cada linha cita a lei, mas **não diz o que o valor muda nem em que obrigação**. |
| Os campos de contrato e de movimento (por exemplo, `Mov_Emprestimo.Forma_Captacao`) | A coluna `Descricao` do dicionário, com o significado. | O que a escolha do valor **desencadeia** no Motor e na obrigação. |

**Regras que já valem e este documento respeita:** a D-N440 (toda obrigação tem tela de parâmetros e eles ficam centralizados), a Q155-3 (as tabelas legais continuam nas tabelas próprias e a tela as mostra em leitura), a Q155-4 (só o contador altera, com a permissão "Parametrizar obrigação"), a Q160-1 (as quatro classes de armazenamento) e o princípio "o ERP avisa e não bloqueia" (D-N284).

# 3. O que é um "parâmetro" aqui

Li "parâmetro" no sentido amplo, que cobre o que você chamou de "diversos parâmetros". Separei dois **papéis**, porque a documentação serve aos dois, mas quem mexe neles é diferente.

**Parâmetro** é o valor que o contador ou o gestor ajusta para mudar o comportamento do ERP: as marcas das regras de crédito, as janelas e as leituras provisórias. **Chave de decisão** é o campo de um contrato ou de um movimento que o Motor lê para escolher a regra: o tipo do arrendamento, a forma de captação do empréstimo, a marca de moeda estrangeira. Quem cadastra o contrato dá o valor; o efeito é o mesmo tipo de efeito, e o auditor pergunta pelos dois do mesmo jeito ("o que isso muda e onde aparece?").

Fora do conceito ficaram os **fatos** (o valor pago, a data, o saldo, a alíquota gravada) e os **textos** (descrição, condição, fundamento): eles não decidem nada.

O Anexo A traz a documentação dos 41, nos quatro grupos da seção 1, com os valores, o padrão, o que acontece sem valor e quem altera.

# 4. Achados

**4.1 A `Ajuda` do catálogo não comporta o que você pediu.** As 61 linhas do catálogo foram escritas com uma frase de ajuda e uma obrigação dona. O efeito depende do **valor** (por exemplo, a forma de cálculo tem seis valores com seis efeitos diferentes) e o parâmetro pode agir em **mais de uma obrigação** (o `Admite_Tomador_Regime_Especifico` age na escrituração e na DeRE do próprio tomador). Para guardar isso sem esticar a `Ajuda` e sem repetir linhas do catálogo, o desenho precisa de uma tabela de efeitos de muitos para muitos (seção 5.1).

**4.2 A maioria dos parâmetros do B0b-2 não pode entrar no catálogo.** Das 41, 35 são **colunas** de tabelas legais ou de contratos, e o catálogo central é por empresa. A Q155-3 já tinha resolvido o caso das tabelas legais: elas ficam nas tabelas próprias e a tela as mostra em leitura. Por isso o catálogo recebe **uma linha para o catálogo das regras** (`Armazenamento = tabela_propria`, como o documento 160 fez com as 11 tabelas) e a documentação de cada marca mora em `Cad_Parametro_Documentacao`, apontando para a entidade e a coluna. A D-N440 fica de pé: nenhum parâmetro de obrigação nasce como campo solto; ele nasce documentado.

**4.3 Cinco leituras minhas estavam escritas no texto do Motor.** No documento 200 eu li, de um jeito provisório: os juros de mora fora da base (C239), o arrendamento financeiro sobre a parcela inteira (C241), a menor taxa no empate de vencimentos do DI e os 252 dias úteis da curva (C242) e a oferta de esforços restritos como oferta pública (C240). Se o contador responder diferente, o texto do Motor teria que mudar. Viram **cinco parâmetros por empresa**, com o padrão provisório documentado: a resposta do contador troca o valor sem mudar o desenho (Anexo A, grupo D).

**4.4 O padrão visível é uma exceção à Q155.** A Q155 estabeleceu "sem padrão escondido: parâmetro sem linha significa que ninguém respondeu, e não 'não'". Para as cinco leituras, o Motor precisa de um comportamento mesmo sem resposta, e o dicionário já tem o hábito de gravar `Regra_Provisoria` e avisar. A proposta mantém o espírito da Q155: o padrão é **escrito na documentação** (`Valor_Padrao`), é **visível** na tela, e o ERP **avisa** cada vez que o usa. Se você preferir seguir a Q155 ao pé da letra, a alternativa é o Motor **não calcular** os créditos afetados enquanto o contador não responder; a diferença está na Q201-4.

**4.5 Os efeitos estão quase todos na escrituração do IBS e da CBS, e esse leiaute não existe.** O crédito do tomador é apurado e conferido com a aba de créditos da Plataforma (documento 36). A obrigação `ESCRITURACAO_IBS_CBS` está no catálogo como a escrituração digital do IBS e da CBS (vigência desde 2026), mas o **leiaute oficial ainda não foi fechado** (documento 32). Por isso a coluna `Local_Do_Efeito` descreve **o ponto da apuração** (a conta de créditos apropriados, a conferência com o espelho) e a coluna `Leiaute_Referencia` diz "a conferir". Quando o leiaute sair, o efeito ganha o registro e o campo, numa versão nova (por isso as duas tabelas têm vigência).

**4.6 A DeRE aparece de duas formas.** Na primeira, a DeRE é a **fonte do dado**: o fornecedor informa, na DeRE dele, o adquirente e o tributo que pagou, e o crédito do tomador só existe com essa informação (formas `valor_pago_pelo_fornecedor` e o plano de saúde da operadora). Na segunda, é um efeito **na DeRE do próprio tomador**, quando ele está em regime específico: o crédito das tarifas só vale se a despesa não foi deduzida da base dele (LC 214, art. 198, parágrafo único). O manual da DeRE não foi lido (Q198-12); o efeito descreve a regra e a conferência fica marcada. A segunda forma foi ao contador (C247): como o tomador mostra, na DeRE, que não deduziu a despesa.

**4.7 A declaração do art. 337, § 2º, não tem obrigação para morar.** O decreto manda a empresa declarar à RFB a condição e o prazo do acordo coletivo, mas o ato conjunto não foi publicado e não há nome para a obrigação. O efeito ficou em `ESCRITURACAO_IBS_CBS`, com a anotação "ato conjunto não publicado" (Q201-7). Quando o ato sair, a obrigação ganha linha e os efeitos passam para ela por versão nova.

**4.8 ECD e ECF.** O crédito do tomador pode mudar o lançamento contábil (a despesa financeira líquida do tributo recuperável) e, por consequência, a base do IRPJ e da CSLL. Não encontrei nos documentos do projeto nem nas normas que li uma regra que diga isso, e **não documentei efeito algum** nessas duas obrigações; a C246 pergunta ao contador. É melhor uma lacuna escrita que um efeito inventado.

**4.9 Os parâmetros que já existem não têm essa documentação.** Os 61 parâmetros do catálogo, os quatro cadastros do B4 e as demais tabelas legais seguem com a `Ajuda` e o fundamento. A estrutura proposta serve a todos (nada nela é do B0b-2), mas documentar tudo é outro volume de trabalho; a Q201-9 pergunta a ordem.

# 5. Proposta

## 5.1 Duas entidades novas

| Entidade | Para quê | Vigência | Campos |
|----------------------------|-------------------------------------------------------|----------|--------|
| `Cad_Parametro_Documentacao` | A documentação de cada parâmetro ou chave de decisão: o que é, os valores possíveis, o padrão, o que acontece sem valor, quem altera e o fundamento legal. Uma linha por parâmetro, esteja ele no catálogo central de parâmetros por obrigação ou numa coluna de uma tabela legal ou de um contrato. O efeito em cada obrigação está em `Cad_Parametro_Efeito_Obrigacao`. | sim | 21 |
| `Cad_Parametro_Efeito_Obrigacao` | O efeito de um parâmetro em uma obrigação: uma linha por parâmetro, obrigação e, quando o efeito depende do valor, por valor. Diz o tipo do efeito, o local da obrigação em que ele aparece e o que muda. Um parâmetro pode atuar em mais de uma obrigação, e uma obrigação recebe efeito de muitos parâmetros; a tela mostra os dois sentidos. | sim | 14 |

Nas duas valem as convenções da Fase 0: `ID_X` é a identidade, `ID_X_Versao` a chave da versão, e `Vigencia_Inicio`, `Vigencia_Fim` (31/12/9999 quando em aberto) e `Motivo_Vigencia` fecham cada linha. Um efeito muda de versão quando a obrigação muda o leiaute ou o ato conjunto sai; a versão antiga fica guardada.

### `Cad_Parametro_Documentacao` (Contabilidade & Fiscal, com vigência, 21 campos)

A documentação de cada parâmetro ou chave de decisão: o que é, os valores possíveis, o padrão, o que acontece sem valor, quem altera e o fundamento legal. Uma linha por parâmetro, esteja ele no catálogo central de parâmetros por obrigação ou numa coluna de uma tabela legal ou de um contrato. O efeito em cada obrigação está em `Cad_Parametro_Efeito_Obrigacao`.

| Campo | Tipo | Descrição |
|---------------------|---------------------------------------|---------------------------------------|
| `ID_Parametro_Documentacao` | identificador | Chave. |
| `ID_Parametro_Documentacao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Parametro_Documentacao_Versao). Fase 0, seção 2. |
| `Codigo_Parametro` | código (60) --- identidade | Estável, em minúsculas. Igual ao `Codigo` do catálogo central quando a origem é `catalogo_central`; nas demais, um código curto que o dicionário escolhe (por exemplo, `credito_forma_calculo`). |
| `Rotulo` | texto | O nome do parâmetro na tela. |
| `Origem_Parametro` | enumeração {catalogo_central, campo_de_tabela} | Onde o valor mora: no catálogo central de parâmetros por obrigação (D-N440), ou numa coluna de tabela legal, de cadastro ou de movimento, que a tela mostra com a documentação. |
| `Papel` | enumeração {parametro, chave_de_decisao} | `parametro`: valor que o contador ou o gestor ajusta para mudar o comportamento. `chave_de_decisao`: campo de contrato ou de movimento que o Motor lê para escolher a regra (por exemplo, o tipo de arrendamento). |
| `ID_Obrigacao_Parametro_Definicao` | referência (Cad_Obrigacao_Parametro_Definicao), opcional | A linha do catálogo central, quando a origem é `catalogo_central`. |
| `Entidade_Alvo` | código (80), opcional | Quando a origem é `campo_de_tabela`: a entidade da coluna. |
| `Campo_Alvo` | código (80), opcional | Quando a origem é `campo_de_tabela`: a coluna. |
| `Grupo` | texto, opcional | Agrupamento na tela de documentação (por exemplo, "Parâmetros da regra", "Chaves de decisão"). |
| `Descricao` | texto | O que o parâmetro é e o que ele decide, em palavras do dicionário. |
| `Valores_Possiveis` | texto | Os valores que o parâmetro aceita, com o que cada um significa quando o efeito difere (o efeito por valor está em `Cad_Parametro_Efeito_Obrigacao.Quando_Valor`). |
| `Valor_Padrao` | texto, opcional | O valor que o Motor usa enquanto ninguém respondeu, quando existe. Sempre marcado como provisório e sempre acompanhado de aviso. |
| `Efeito_Sem_Valor` | texto | O que o ERP faz quando o parâmetro está vazio: avisa, usa o padrão provisório ou deixa de calcular. |
| `Quem_Altera` | enumeração {contador, usuario_do_contrato, plataforma, carga_do_sistema} | Quem dá o valor. `contador`: parâmetro com a permissão "Parametrizar obrigação" (Q155-4). `usuario_do_contrato`: quem cadastra o contrato ou o movimento. `plataforma`: informado pela Plataforma da Receita. `carga_do_sistema`: lido ou gravado pelo Motor. |
| `Fundamento_Legal` | texto | Os artigos da LC, do decreto ou do ato de onde vem o parâmetro. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

### `Cad_Parametro_Efeito_Obrigacao` (Contabilidade & Fiscal, com vigência, 14 campos)

O efeito de um parâmetro em uma obrigação: uma linha por parâmetro, obrigação e, quando o efeito depende do valor, por valor. Diz o tipo do efeito, o local da obrigação em que ele aparece e o que muda. Um parâmetro pode atuar em mais de uma obrigação, e uma obrigação recebe efeito de muitos parâmetros; a tela mostra os dois sentidos.

| Campo | Tipo | Descrição |
|-----------------------|---------------------------------------|---------------------------------------|
| `ID_Parametro_Efeito_Obrigacao` | identificador | Chave. |
| `ID_Parametro_Efeito_Obrigacao_Versao` | identificador da versão | Chave primária da versão (tabela física Cad_Parametro_Efeito_Obrigacao_Versao). Fase 0, seção 2. |
| `ID_Parametro_Documentacao` | referência (Cad_Parametro_Documentacao) --- identidade | O parâmetro documentado. |
| `ID_Obrigacao` | referência (Cad_Obrigacao_Acessoria) --- identidade | A obrigação em que o efeito aparece. |
| `Quando_Valor` | texto, opcional --- identidade | O valor do parâmetro a que o efeito se refere; vazio quando o efeito vale para qualquer valor. |
| `Tipo_Efeito` | enumeração {calcula_valor, seleciona_regra, condiciona_credito, veda_credito, define_fonte_do_dado, define_vigencia, gera_aviso} | `calcula_valor`: entra na conta do valor. `seleciona_regra`: escolhe a regra ou a linha de parâmetro. `condiciona_credito`: o crédito só existe ou só vale quando a condição é atendida. `veda_credito`: o crédito sai zero. `define_fonte_do_dado`: diz de onde vem o dado. `define_vigencia`: fixa a data em que passa a valer. `gera_aviso`: só avisa, sem mudar o valor. |
| `Local_Do_Efeito` | texto | Onde o efeito aparece na obrigação: a apuração, a conta, o registro ou o campo do arquivo, ou a tela. Onde o leiaute oficial ainda não existe, descreve o ponto da obrigação. |
| `Efeito` | texto | O que muda quando o parâmetro tem este valor. |
| `Leiaute_Referencia` | texto, opcional | O registro ou o campo oficial da obrigação, quando o leiaute existe; "a conferir" quando não foi lido ou não foi publicado. |
| `Situacao_Dado` | enumeração {provisorio, validado} | A carga sai provisória até o contador validar. |
| `ID_Instancia_Aprovacao` | referência (Mov_Aprovacao_Instancia), opcional | A validação do contador. |
| `Vigencia_Inicio` | data | Primeiro dia em que esta versão vale. |
| `Vigencia_Fim` | data | Último dia em que esta versão vale (inclusive). Sempre preenchida: 31/12/9999 quando o fim é indefinido. |
| `Motivo_Vigencia` | texto, opcional | Por que esta versão foi criada. |

## 5.2 O que muda em entidades que já existem

| Entidade | Mudança |
|------------------------------------------------|----------------------------------------------------|
| `Cad_Obrigacao_Parametro_Definicao` | **Só carga, mais um texto:** seis linhas novas (Anexo D.1) e o texto de `Ajuda`, que passa a dizer que é o **resumo** e que o efeito completo está em `Cad_Parametro_Documentacao` e `Cad_Parametro_Efeito_Obrigacao`. Nenhum campo novo. |
| `Cad_Obrigacao_Acessoria` | **Só carga:** a linha `ESOCIAL` (Anexo D.2), início em 01/01/2026 como na D-N323. Depende da Q201-6. |
| `Cad_Regra_Credito_Tomador` e as demais entidades do documento 200 | Nenhum campo novo. A documentação aponta para as colunas que já existem. |

## 5.3 Como a documentação aparece

- **Na tela de parâmetros da obrigação** (D-N440), cada parâmetro ganha um painel **"Documentação"** com o que é, os valores, o padrão, o que acontece sem valor, quem altera e, em seguida, **uma linha por obrigação e por valor** com o tipo do efeito, o local e o que muda.
- **Na aba de cada obrigação**, uma lista **"Parâmetros que afetam esta obrigação"**, que é a mesma tabela lida ao contrário: para `ESCRITURACAO_IBS_CBS`, os 51 efeitos do Anexo C; para a DeRE, os 6; para o eSocial, 1.
- **Nos campos de contrato e de movimento** (as chaves de decisão), o dicionário e o formulário mostram um ícone de ajuda que abre a mesma documentação. O texto da ajuda sai da documentação, e não de uma coluna copiada, para não haver duas versões.
- **No aviso do Motor**, quando o ERP usa o padrão provisório de um parâmetro, a mensagem diz o parâmetro, o padrão usado e o link da documentação.

## 5.4 Regra de completude

Todos os parâmetros e chaves de decisão do B0b-2 (Anexo A) entram **com** documentação e com pelo menos um efeito. Daqui em diante vale a regra geral: **nenhum parâmetro entra no dicionário, em nenhum documento de desenho, sem a documentação do efeito e da obrigação.** A auditoria da carga confere três coisas e acusa o que falta: (a) toda linha do catálogo central tem linha em `Cad_Parametro_Documentacao`; (b) toda documentação tem ao menos um efeito em `Cad_Parametro_Efeito_Obrigacao`; (c) toda coluna que o desenho declara como parâmetro ou chave de decisão tem documentação. A conferência fica na carga e na auditoria; o banco não tem como garantir sozinho, porque a coluna é citada pelo nome e não por chave estrangeira.

## 5.5 Padrão provisório das cinco leituras

As cinco leituras do grupo D têm **padrão visível**: o valor aparece em `Valor_Padrao` da documentação e na tela, e o Motor o usa até o contador responder, **com aviso a cada uso**. A resposta do contador cria o valor em `Cad_Obrigacao_Parametro_Valor` (por empresa, com vigência e a situação "validado") e o aviso some. Fica como exceção declarada à regra "sem padrão" da Q155, e só para esses cinco.

## 5.6 O que a documentação não faz

Ela **não altera o cálculo** nem cria regra: só diz, por parâmetro, o que o Motor já faz. Onde o efeito depende de um leiaute que não existe (escrituração do IBS e da CBS), a documentação descreve o ponto da apuração e marca `Leiaute_Referencia` como "a conferir". Onde não encontrei norma (ECD e ECF), **não há efeito escrito**.

# 6. Regras de texto: o que o Motor avisa

Nenhuma regra bloqueia; todas gravam o aviso na linha e mostram a mensagem ao usuário (D-N284).

| # | Regra | Onde avisa |
|-------|----------------------------------------------------------|-----------------------------------|
| 1 | O Motor usou o **padrão provisório** de um parâmetro do grupo D (a mensagem traz o parâmetro, o padrão e a documentação) | `Mov_Credito_Servico_Regime_Especifico` |
| 2 | Parâmetro ou chave de decisão **sem documentação** na carga (auditoria) | auditoria da carga |
| 3 | Documentação **sem nenhum efeito** (auditoria) | auditoria da carga |
| 4 | Efeito com `Situacao_Dado = provisorio` mostrado ao usuário (o contador ainda não validou a leitura da obrigação) | painel "Documentação" |
| 5 | Efeito com `Leiaute_Referencia` "a conferir" | painel "Documentação" |
| 6 | Obrigação do efeito **sem linha** em `Cad_Obrigacao_Acessoria` (auditoria da carga) | auditoria da carga |

# 7. Perguntas

| Id | Pergunta | Recomendação |
|---------|------------------------------------------------------------|-------------------------------|
| Q201-1 | Aprova o **escopo**: documentar agora os **41 parâmetros e chaves de decisão do B0b-2** (12 marcas da regra e do catálogo, 20 chaves de decisão, 4 parâmetros existentes lidos pelo B0b-2 e 5 leituras provisórias), com o conceito de "parâmetro" da seção 3 (parâmetro e chave de decisão, sem fatos e textos)? | Sim |
| Q201-2 | Aprova as **duas entidades novas**, `Cad_Parametro_Documentacao` (21 campos) e `Cad_Parametro_Efeito_Obrigacao` (14 campos), as duas com vigência, com o efeito em muitos para muitos entre parâmetro e obrigação e por valor? | Sim |
| Q201-3 | Aprova a **regra geral** da seção 5.4: nenhum parâmetro entra no dicionário sem documentação do efeito e da obrigação, e a auditoria da carga acusa o que não tem? | Sim |
| Q201-4 | Aprova as **cinco leituras provisórias como parâmetros por empresa** (juros de mora, base do arrendamento financeiro, empate do DI, dias úteis da curva e oferta restrita), com o **padrão visível e aviso a cada uso**, como exceção à regra "sem padrão" da Q155? A alternativa é o Motor não calcular os créditos afetados até o contador responder. | Sim, com padrão visível e aviso |
| Q201-5 | Aprova as **seis linhas** no catálogo central (uma para o catálogo das 28 regras, em leitura, e cinco para as leituras) e o texto novo de `Ajuda` como resumo, com o detalhe na documentação? | Sim |
| Q201-6 | Aprova a linha **`ESOCIAL`** em `Cad_Obrigacao_Acessoria` (início 01/01/2026, como na D-N323), para registrar a origem do desconto do plano de saúde? A Q160-4 tinha deixado o eSocial esperando ter parâmetro. | Sim |
| Q201-7 | A **declaração do art. 337, § 2º**, fica documentada em `ESCRITURACAO_IBS_CBS` com a anotação "ato conjunto não publicado", e passa para a obrigação própria quando o ato sair (versão nova do efeito)? | Sim |
| Q201-8 | **ECD e ECF** ficam **sem efeito documentado** até a resposta do contador (C246), e o efeito na **DeRE do próprio tomador** fica como está no Anexo B, com a conferência marcada até a C247? | Sim |
| Q201-9 | Documentar depois os **parâmetros que já existem**, na ordem: primeiro os quatro cadastros e as regras do B4, depois as 61 linhas do catálogo e as demais tabelas legais, em documentos seguintes? | Sim, nessa ordem |
| Q201-10 | Aprova o **painel "Documentação" por parâmetro**, a **lista "Parâmetros que afetam esta obrigação"** em cada obrigação e a ajuda nos campos de contrato (seção 5.3)? | Sim |

# 8. O que acontece se você aprovar

| Item | Efeito |
|--------------------------|--------------------------------------------------------------------------|
| Entidades | **1.163 → 1.165** (+2, as duas em Contabilidade & Fiscal), já contando o documento 200 |
| Campos | **13.169 → 13.204** (+35: 21 + 14; nenhum campo novo em entidade existente) |
| Chaves estrangeiras | **3.440 → 3.445** (+5: o catálogo, o aprovador e a obrigação) |
| Domínios | **355** (sem mudança) |
| Carga | **41** linhas de documentação, **58** de efeito, **6** linhas de `Cad_Obrigacao_Parametro_Definicao` e **1** de `Cad_Obrigacao_Acessoria` (`ESOCIAL`) (Anexo D) |
| Textos de campo | `Cad_Obrigacao_Parametro_Definicao.Ajuda` (passa a ser o resumo) |
| Ondas, DDL e ER | As duas entidades entram na onda 3 (Contabilidade & Fiscal); ambas geram a tabela `_Versao`; regerados na consolidação |
| Documentos | 14 (D-N535), 38 (seção 1.31) e 188 (C246 e C247, total 247) |

Se o documento 200 e o 201 forem consolidados juntos (o 200 já está aprovado), o resultado é **1.165 entidades, 13.204 campos e 3.445 chaves estrangeiras**.

# 9. Limites

- **Os efeitos são os que consegui ancorar.** Todos os 58 vêm do texto da lei, do decreto ou do desenho do documento 200. **Nenhum foi conferido contra um leiaute oficial**: o da escrituração do IBS e da CBS não foi fechado, o manual da DeRE não chegou (Q198-12) e não li o do eSocial.
- **ECD e ECF estão sem efeito**, por falta de norma na minha leitura (C246). Pode haver efeito; só não o escrevi.
- **O efeito na DeRE do tomador** (a dedução da despesa na base) é minha leitura da LC 214, art. 198, parágrafo único, e vai ao contador (C247).
- **Os padrões das cinco leituras são provisórios** e vêm das minhas leituras do documento 200; cada um tem pergunta ao contador (C239, C240, C241 e C242).
- **A coluna `Local_Do_Efeito` descreve o ponto da obrigação**, e não o registro ou o campo do arquivo, onde o leiaute não existe.
- **A divisão em "parâmetro" e "chave de decisão"** é minha; a tela e a carga a usam para agrupar, e não muda o comportamento.
- **O B4 e os 61 parâmetros do catálogo ainda não têm essa documentação** (Q201-9).
- **As contagens** vêm de um programa sobre o modelo da revisão 37 mais as entidades do documento 200, conferido contra os nomes e os destinos de cada chave; o texto dos artigos eu conferi à mão nos trechos citados no documento 200.
- **Nada passou por validação do contador.** As duas perguntas C246 e C247 estão no documento 188.

# Anexo A. Manual dos 41 parâmetros do B0b-2

Uma tabela por grupo. A coluna "Sem valor" diz o que o ERP faz quando o parâmetro está vazio; o efeito de cada valor, em cada obrigação, está no Anexo B.

## A. Parâmetros da regra (12)

| Parâmetro | Onde mora | O que é | Valores | Padrão | Sem valor | Quem altera | Fundamento |
|--------------|-------------|--------------|--------------|-----------|--------------|---|--------------|
| Forma de cálculo do crédito do tomador (`credito_forma_calculo`) | `Cad_Regra_Credito_Tomador.Forma_Calculo` | Diz como o Motor produz o crédito do tomador na regra: calcula por conta própria, registra o que o fornecedor informou, aplica uma proporção do débito ou não dá crédito. | excedente_principal_selic, excedente_curva_di, parcela_pela_aliquota, valor_pago_pelo_fornecedor, proporcao_debito_fornecedor, sem_credito | Sem padrão: toda regra tem valor | Regra sem forma de cálculo não existe (campo obrigatório); a carga recusa a linha. | contador | LC 214, arts. 190, 194 a 198, 203, 219, § 5º, e 238, parágrafo único; Decreto 12.955, arts. 288 a 292, 296 a 298 e 337 |
| Crédito nasce no pagamento (regime de caixa) (`credito_regime_caixa`) | `Cad_Regra_Credito_Tomador.Regime_Caixa` | O crédito é reconhecido na data do pagamento efetivo, não na competência da despesa. | verdadeiro ou falso | Sem padrão: toda regra tem valor | Obrigatório; a carga recusa a linha. | contador | LC 214, arts. 194, 196 e 203 ("efetivamente pagas" e "efetivo pagamento"); Decreto 12.955, arts. 288 a 290, 296 e 298 |
| Crédito acompanha o débito extinto do fornecedor (`credito_proporcao_extincao`) | `Cad_Regra_Credito_Tomador.Aplica_Proporcao_Extincao` | O crédito apropriável é o calculado vezes a parte da CBS que o fornecedor extinguiu: integral se a base dele foi zero ou negativa, proporcional se parcial, nenhum se não pagou. | verdadeiro (empréstimo, título e desconto) ou falso | Falso | Sem valor a regra é recusada na carga. | contador | Decreto 12.955, art. 291 (vale para os arts. 288 a 290) |
| Veda o crédito ao associado de cooperativa de crédito (`credito_veda_cooperativa`) | `Cad_Regra_Credito_Tomador.Veda_Associado_Cooperativa` | Não dá crédito ao associado de cooperativa de crédito que exerceu a opção do art. 271. | verdadeiro ou falso | Falso | Obrigatório; a carga recusa a linha. | contador | LC 214, art. 197, I; Decreto 12.955, art. 284, I |
| Veda o crédito de operação referenciada em moeda estrangeira (`credito_veda_moeda_estrangeira`) | `Cad_Regra_Credito_Tomador.Veda_Referenciado_Moeda_Estrangeira` | Não dá crédito de juros a operação de crédito ou título de dívida referenciados em moeda estrangeira; as tarifas e comissões continuam com crédito. | verdadeiro ou falso | Falso | Obrigatório; a carga recusa a linha. | contador | LC 214, art. 197, II, observado o art. 198; Decreto 12.955, art. 284, II |
| Admite o tomador que também está em regime específico (`credito_admite_regime_especifico`) | `Cad_Regra_Credito_Tomador.Admite_Tomador_Regime_Especifico` | O tomador que está em regime específico da mesma seção pode tomar o crédito (tarifas e comissões, desde que a despesa não seja deduzida da base dele). | verdadeiro ou falso | Falso | Obrigatório; a carga recusa a linha. | contador | LC 214, arts. 194 e 198, parágrafo único; Decreto 12.955, art. 292 |
| Exige acordo ou convenção coletiva com cláusula compulsória (`credito_exige_acordo_coletivo`) | `Cad_Regra_Credito_Tomador.Exige_Acordo_Coletivo` | O crédito depende de instrumento coletivo com cláusula compulsória para o benefício (plano de saúde dos empregados). | verdadeiro (só a regra do plano de saúde) ou falso | Falso | Obrigatório; a carga recusa a linha. | contador | Decreto 12.955, arts. 63, § 1º, VI, e 337, § 1º |
| Exige declaração à RFB do acordo coletivo (`credito_exige_declaracao_rfb`) | `Cad_Regra_Credito_Tomador.Exige_Declaracao_Rfb` | O tomador deve declarar à RFB a condição e o prazo do acordo ou da convenção; o ERP só registra, porque o ato conjunto não foi publicado. | verdadeiro ou falso | Falso | Obrigatório; a carga recusa a linha. | contador | Decreto 12.955, art. 337, § 2º |
| Início de vigência da regra (`credito_inicio_vigencia`) | `Cad_Regra_Credito_Tomador.Vigencia_Inicio` | Primeiro dia em que a regra vale; as 28 regras de partida começam em 01/01/2027, como as alíquotas do B4. | data | 01/01/2027 na carga de partida | Obrigatório. | contador | Decreto 12.955, art. 480, I (CBS de 0,9% em 2026 sem regra de crédito do tomador); LC 214, art. 233 |
| Situação da regra (provisória ou validada) (`credito_situacao_regra`) | `Cad_Regra_Credito_Tomador.Situacao_Dado` | Indica se o contador já validou a regra; toda regra nasce provisória. | provisorio ou validado | provisorio | Obrigatório. | contador | Fase 0, seção 9 (dados legais provisórios) |
| Base de cálculo do fornecedor a que a regra se liga (`credito_base_regime_da_regra`) | `Cad_Regra_Credito_Tomador.ID_Base_Regime` | Liga a regra à base do B4 (por exemplo, `credito_cambio_tvm` ou `arrend_fin_parcelas`), de onde o Motor lê a alíquota do crédito. | um dos 23 valores de `base_regime_especifico` | Sem padrão | Obrigatório. | contador | LC 214, art. 233; Decreto 12.955, arts. 269 a 346 |
| Regras do crédito do tomador de serviço financeiro (catálogo) (`credito_tomador_regras`) | catálogo central (linha da tabela, em leitura) | O catálogo legal das 28 regras de crédito do tomador, mostrado em leitura na tela da obrigação; cada marca da regra tem documentação própria (grupo A). | as 28 linhas de `Cad_Regra_Credito_Tomador` | As linhas de partida (provisórias, desde 01/01/2027) | Sem linha de regra para o serviço: o ERP avisa e não calcula o crédito. | contador | LC 214, arts. 190 a 243; Decreto 12.955, arts. 284 a 346 |

## B. Chaves de decisão (20)

| Parâmetro | Onde mora | O que é | Valores | Padrão | Sem valor | Quem altera | Fundamento |
|--------------|-------------|--------------|--------------|----------|--------------|------|--------------|
| Forma de captação do empréstimo (`chave_forma_captacao`) | `Mov_Emprestimo.Forma_Captacao` | Diz se o contrato é operação de crédito, título de dívida ou título de dívida de oferta pública. | operacao_credito, titulo_divida, titulo_divida_oferta_publica | operacao_credito | Sem valor vale operação de crédito, com aviso. | quem cadastra o contrato | LC 214, arts. 194 e 195; Decreto 12.955, arts. 288 e 289 |
| Empréstimo referenciado em moeda estrangeira (`chave_emprestimo_moeda_estrangeira`) | `Mov_Emprestimo.Referenciado_Moeda_Estrangeira` | Marca o empréstimo ou título referenciado em moeda estrangeira (em moeda estrangeira ou indexado ao câmbio, a confirmar na C245). | verdadeiro ou falso | Falso | Sem valor vale falso. | quem cadastra o contrato | LC 214, art. 197, II; Decreto 12.955, art. 284, II |
| Credor do empréstimo (`chave_emprestimo_credor`) | `Mov_Emprestimo.ID_Participante_Credor` | Quem emprestou: banco, fundo ou investidor. É por ele que o Motor sabe se o fornecedor está em regime específico. | um participante cadastrado | Sem padrão | Vazio: o ERP avisa na baixa da parcela e não calcula o crédito. | quem cadastra o contrato | LC 214, arts. 190 e 194; Decreto 12.955, arts. 285 e 288 |
| Uso legal da série de cotação (`chave_serie_uso_legal`) | `Cad_Serie_Cotacao.Uso_Legal_Cbs` | Marca a série que a lei manda usar: a Selic diária ou um contrato de DI futuro. | selic_diaria, di_futuro (vazio nas demais séries) | Vazio | Sem série marcada o cálculo da dedução não roda e o ERP avisa. | contador | LC 214, arts. 194, II, 196 e 219, § 5º; Decreto 12.955, arts. 288, II, e 290 |
| Vencimento do contrato de DI futuro (`chave_serie_vencimento_di`) | `Cad_Serie_Cotacao.Data_Vencimento_Contrato` | O vencimento do contrato de DI futuro; só vale quando a série é `di_futuro`. | data | Vazio | Série `di_futuro` sem vencimento é ignorada na escolha, com aviso. | contador | Decreto 12.955, art. 290, parágrafo único |
| Tipo do arrendamento mercantil (`chave_tipo_arrendamento`) | `Cad_Arrendamento_Mercantil.Tipo_Arrendamento` | Operacional ou financeiro; define as bases do fornecedor e a regra de crédito do arrendatário. | operacional, financeiro | Sem padrão | Obrigatório no contrato. | quem cadastra o contrato | LC 214, art. 203; Decreto 12.955, arts. 296 a 298 |
| Classificação e natureza do bem arrendado (`chave_bem_arrendado`) | `Cad_Arrendamento_Mercantil.ID_Cclasstrib_Bem` | Classificação tributária do bem; define a alíquota de locação ou de venda usada no crédito (o imóvel segue o regime imobiliário, `Natureza_Bem`). | uma classificação tributária; `Natureza_Bem` = movel ou imovel | Sem padrão | Bem sem classificação: o ERP avisa e não calcula o crédito da parcela. | quem cadastra o contrato | LC 214, arts. 201, I, e 203; Decreto 12.955, arts. 296 a 298 |
| Tipo do pagamento do arrendamento (`chave_tipo_pagamento_arrendamento`) | `Mov_Arrendamento_Parcela.Tipo_Pagamento` | Diz se o pagamento é contraprestação, valor residual ou alienação do bem. | contraprestacao, valor_residual, alienacao_bem | contraprestacao | Sem valor vale contraprestação. | quem cadastra o contrato | LC 214, art. 203; Decreto 12.955, arts. 296 e 298 |
| Encargos financeiros da parcela do arrendamento (`chave_encargos_arrendamento`) | `Mov_Arrendamento_Parcela.Valor_Encargos_Financeiros` | A parte da parcela que é encargo financeiro, quando o arrendador informa. | número em reais | Vazio | Vazio: o ERP não consegue avisar do excesso e a base é a parcela inteira. | quem cadastra o contrato | Decreto 12.955, art. 297, § 1º |
| Base da antecipação de recebíveis (`chave_modalidade_antecipacao`) | `Mov_Antecipacao_Recebivel.ID_Base_Regime` | A base do fornecedor da operação: desconto, cessão e antecipação de crédito; securitização e faturização; ou antecipação de arranjo. | `credito_cambio_tvm`, `securitizacao_faturizacao`, `antecipacao_recebivel_arranjo` | Sem padrão | Obrigatório na operação. | quem cadastra o contrato | LC 214, arts. 196 e 219, § 5º; Decreto 12.955, arts. 290 e 314, § 6º |
| Detentor do título é do regime específico (`chave_detentor_titulo`) | `Mov_Credito_Servico_Regime_Especifico.Detentor_Regime_Especifico` | No título de dívida, diz se o detentor, no período, é contribuinte do regime específico. | verdadeiro, falso ou vazio | Vazio | Vazio: o crédito fica "a apropriar" e o ERP avisa. | Plataforma da Receita | LC 214, art. 195; Decreto 12.955, art. 289 |
| Associado de cooperativa que fez a opção do art. 271 (`chave_associado_cooperativa`) | `Mov_Credito_Servico_Regime_Especifico.Associado_Cooperativa_Opcao` | Gravado no pagamento: o tomador é associado de cooperativa de crédito que fez a opção. | verdadeiro ou falso | Falso (lido da qualificação) | Lido de `Cad_Participante_Qualificacao_Cbs`; sem qualificação vale falso. | Motor (lê e grava) | LC 214, art. 197, I |
| Tomador em regime específico (`chave_tomador_regime_especifico`) | `Mov_Credito_Servico_Regime_Especifico.Tomador_Regime_Especifico` | Gravado no pagamento: a empresa está em regime específico da seção. | verdadeiro ou falso | Falso (lido de `Cad_Participante_Regime_Base`) | Sem linha em `Cad_Participante_Regime_Base` vale falso. | Motor (lê e grava) | LC 214, arts. 194 e 198, parágrafo único |
| Quem fixou o valor do crédito (`chave_origem_valor_credito`) | `Mov_Credito_Servico_Regime_Especifico.Origem_Valor` | Diz se o valor foi calculado pelo ERP, informado pelo fornecedor ou ajustado pelo usuário. | calculado_pelo_erp, informado_pelo_fornecedor, ajustado_pelo_usuario | calculado_pelo_erp | Sem padrão. | Motor (lê e grava) | LC 214, art. 190; Decreto 12.955, art. 285 |
| Proporção da CBS extinta pelo fornecedor (`chave_proporcao_extincao`) | `Mov_Credito_Servico_Regime_Especifico.Proporcao_Extincao_Debito` | Parte do débito de CBS do fornecedor que foi extinta, em percentual, informada pela Plataforma. | número de 0 a 100 | Vazio | Vazio com a regra que aplica a proporção: crédito a apropriar, valor apropriável zero. | Plataforma da Receita | Decreto 12.955, art. 291 |
| Cláusula compulsória do acordo coletivo (`chave_clausula_compulsoria`) | `Mov_Rh_Beneficio_Acordo_Coletivo.Clausula_Compulsoria` | O instrumento coletivo traz cláusula compulsória para o plano de saúde. | verdadeiro ou falso | Falso | Sem acordo registrado: sem crédito. | quem cadastra o contrato | Decreto 12.955, art. 63, § 1º, VI |
| Fim da vigência do acordo coletivo (`chave_fim_vigencia_acordo`) | `Mov_Rh_Beneficio_Acordo_Coletivo.Data_Fim_Vigencia` | Último dia do instrumento; vazio enquanto vigente. O crédito vale até seis meses depois. | data | Vazio | Vazio: o instrumento é tido como vigente. | quem cadastra o contrato | Decreto 12.955, art. 63, § 5º |
| Situação da declaração à RFB do acordo (`chave_situacao_declaracao`) | `Mov_Rh_Beneficio_Acordo_Coletivo.Situacao_Declaracao` | Registra se a empresa declarou à RFB a condição e o prazo do instrumento. | nao_declarado, declarado, rejeitado | nao_declarado | Sem valor vale não declarado. | quem cadastra o contrato | Decreto 12.955, art. 337, § 2º |
| Origem do desconto do plano de saúde (`chave_origem_desconto_plano`) | `Mov_Rh_Beneficio_Credito_Cbs.Origem_Desconto` | De onde vem o valor descontado dos empregados: folha do ERP, eSocial ou documento fiscal da empresa. | folha_erp, esocial, documento_fiscal | folha_erp | Sem valor vale a folha do ERP, com aviso. | quem cadastra o contrato | Decreto 12.955, art. 337, §§ 3º a 5º |
| Fonte do dado da operadora (`chave_fonte_operadora`) | `Mov_Rh_Beneficio_Credito_Cbs.Fonte_Informacao_Operadora` | Se o débito e a proporção da operadora vieram da RFB ou foram digitados. | dere_rfb, informado_usuario | informado_usuario | Sem valor vale informado pelo usuário, com aviso. | quem cadastra o contrato | Decreto 12.955, art. 337, § 4º |

## C. Parâmetros que já existem e o B0b-2 lê (4)

| Parâmetro | Onde mora | O que é | Valores | Padrão | Sem valor | Quem altera | Fundamento |
|-----------------|-------------|-----------------|-------------|---------|-----------------|----|-----------|
| Meses de crédito depois do fim do acordo (`existente_meses_apos_fim_acordo`) | `Cad_Criterio_Uso_Preponderante.Meses_Apos_Fim_Acordo` | Janela depois do fim do acordo coletivo em que o crédito do plano de saúde ainda vale (seis meses). | número de meses | 6 | Vazio: o crédito acaba no último dia do acordo. | contador | Decreto 12.955, art. 63, § 5º |
| Soma legal das alíquotas do regime específico (`existente_soma_aliquotas`) | `Cad_Regime_Aliquota_Soma.Soma_Aliquotas` | Soma de CBS e IBS do regime específico (art. 233), de onde saem as alíquotas gravadas no crédito do tomador. | número em pontos percentuais, por base e vigência | Linhas do B4 (desde 01/01/2027) | Sem linha para a base e o mês: o ERP avisa e não calcula o crédito. | contador | LC 214, art. 233; Decreto 12.955, art. 480 |
| Bases em que o participante atua (`existente_base_do_participante`) | `Cad_Participante_Regime_Base.ID_Base_Regime` | Em quais bases de cálculo o participante é fornecedor de regime específico; é o que diz se credor, emissor ou operadora está no regime. | bases do domínio `base_regime_especifico`, por vigência | Sem padrão | Sem linha o participante é tratado como fora do regime específico, com motivo `fornecedor_fora_regime`. | contador | LC 214, arts. 181 a 246 |
| Qualificação do participante na CBS (cooperativa) (`existente_qualificacao_cooperativa`) | `Cad_Participante_Qualificacao_Cbs.ID_Tipo_Qualificacao` | Diz se o participante é associado de cooperativa e se exerceu a opção do art. 271. | tipos de qualificação por vigência | Sem padrão | Sem linha o tomador não é associado de cooperativa. | contador | LC 214, arts. 197, I, e 271 |

## D. Leituras provisórias (5)

| Parâmetro | Onde mora | O que é | Valores | Padrão | Sem valor | Quem altera | Fundamento |
|---------------|---------------|---------------|-----------|---------|---------------|----|---------------|
| Juros de mora entram na despesa financeira do crédito (`credito_tomador_juros_mora_na_base`) | catálogo central (`credito_tomador_juros_mora_na_base`, por empresa) | Define se os juros de mora de parcela paga com atraso entram na despesa financeira que dá crédito (leitura provisória aguardando a C239). | verdadeiro ou falso | Falso (juros de mora fora) | Sem valor vale o padrão, e o ERP avisa que usou a leitura provisória. | contador | LC 214, art. 194; Decreto 12.955, art. 288 (o texto não cita a mora) |
| Crédito do arrendamento financeiro só sobre os encargos (`credito_arrend_financeiro_so_encargos`) | catálogo central (`credito_arrend_financeiro_so_encargos`, por empresa) | Define se o crédito do arrendatário financeiro incide só sobre os encargos financeiros da parcela, e não sobre a parcela inteira (leitura provisória aguardando a C241). | verdadeiro ou falso | Falso (parcela inteira) | Sem valor vale o padrão, e o ERP avisa que usou a leitura provisória. | contador | LC 214, art. 203; Decreto 12.955, arts. 297, § 1º, e 298 |
| Empate de vencimentos do DI: usar a maior taxa (`credito_empate_di_maior_taxa`) | catálogo central (`credito_empate_di_maior_taxa`, por empresa) | Quando dois contratos de DI futuro estão à mesma distância do vencimento do recebível, define qual taxa vale (leitura provisória aguardando a C242). | verdadeiro (maior taxa) ou falso (menor taxa) | Falso (menor taxa, como o art. 290) | Sem valor vale o padrão, e o ERP avisa que usou a leitura provisória. | contador | Decreto 12.955, art. 290, parágrafo único (menor taxa) e art. 314, § 2º (maior taxa) |
| Dias úteis por ano na curva DI (`credito_dias_uteis_ano_curva_di`) | catálogo central (`credito_dias_uteis_ano_curva_di`, por empresa) | Divisor dos dias úteis do prazo na fórmula da curva DI (leitura provisória aguardando a C242). | número de dias | 252 | Sem valor vale 252, e o ERP avisa que usou a leitura provisória. | contador | LC 214, arts. 196 e 219, § 5º (a lei não escreve a fórmula) |
| Oferta de esforços restritos conta como oferta pública (`credito_oferta_restrita_como_publica`) | catálogo central (`credito_oferta_restrita_como_publica`, por empresa) | Define se o título de oferta pública com esforços restritos é tratado como oferta pública regulada pela CVM e, portanto, sem crédito ao emissor (leitura provisória aguardando a C240). | verdadeiro ou falso | Verdadeiro | Sem valor vale o padrão, e o ERP avisa que usou a leitura provisória. | contador | LC 214, art. 195, § 1º, II; Decreto 12.955, art. 289, § 1º, II |

# Anexo B. Os 58 efeitos, por parâmetro

Um efeito por linha: o parâmetro, o valor a que o efeito se refere, a obrigação, o tipo, o local, o que muda e a referência do leiaute. Tipos: `calcula_valor`, `seleciona_regra`, `condiciona_credito`, `veda_credito`, `define_fonte_do_dado`, `define_vigencia` e `gera_aviso` (seção 5.1).

| Parâmetro | Quando o valor é | Obrigação | Tipo | Local do efeito | O que muda | Leiaute |
|-------------|----------|--------|--------|---------------------|---------------------|------------------|
| `credito_forma_calculo` | excedente_principal_selic | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Base = máximo(0, (valor pago − principal) − Selic sobre o principal); crédito = base × alíquota. Vale para empréstimo e título de dívida. | Leiaute oficial da escrituração ainda não fechado |
| `credito_forma_calculo` | excedente_curva_di | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Base = soma, por recebível, do deságio que passa da curva DI; crédito = base × alíquota. Vale para desconto, cessão, factoring, securitização e antecipação de cartão. | Leiaute oficial da escrituração ainda não fechado |
| `credito_forma_calculo` | parcela_pela_aliquota | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Base = parcela paga (contraprestação, valor residual ou alienação); crédito = base × alíquota da receita do arrendador. | Leiaute oficial da escrituração ainda não fechado |
| `credito_forma_calculo` | valor_pago_pelo_fornecedor | `ESCRITURACAO_IBS_CBS` | define_fonte_do_dado | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | O ERP não calcula: grava o valor que o fornecedor informou (Plataforma, DeRE do fornecedor ou documento fiscal) como crédito. | Leiaute oficial da escrituração ainda não fechado |
| `credito_forma_calculo` | valor_pago_pelo_fornecedor | `DERE` | define_fonte_do_dado | identificação do adquirente na DeRE do fornecedor | O crédito só nasce se o fornecedor, na DeRE dele, identificar o tomador e o tributo que pagou; sem isso o ERP do tomador avisa e não cria crédito. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `credito_forma_calculo` | proporcao_debito_fornecedor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Crédito = débito do fornecedor × proporção dos empregados × parte que a empresa custeia (plano de saúde); capitalização: débitos extintos × proporção do prêmio. | Leiaute oficial da escrituração ainda não fechado |
| `credito_forma_calculo` | sem_credito | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Nenhum crédito; o registro sai com base zero e o motivo `regra_veda`. | Leiaute oficial da escrituração ainda não fechado |
| `credito_regime_caixa` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: o gatilho é a baixa em `Mov_Titulo_Baixa` e a competência do crédito é a do pagamento. Falso: o crédito acompanha o fato registrado pelo fornecedor. | Leiaute oficial da escrituração ainda não fechado |
| `credito_proporcao_extincao` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: o crédito nasce "a apropriar" e só passa a "apropriado" quando a Plataforma informa a proporção (`Proporcao_Extincao_Debito`); o valor apropriável é o calculado × proporção. Falso: o crédito é integral. | Leiaute oficial da escrituração ainda não fechado |
| `credito_veda_cooperativa` | qualquer valor | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro e tomador qualificado como associado que fez a opção (`Cad_Participante_Qualificacao_Cbs`): base zero e motivo `cooperativa`. | Leiaute oficial da escrituração ainda não fechado |
| `credito_veda_moeda_estrangeira` | qualquer valor | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro e `Mov_Emprestimo.Referenciado_Moeda_Estrangeira` ligado: base zero e motivo `moeda_estrangeira`. A regra de tarifas e comissões fica com falso. | Leiaute oficial da escrituração ainda não fechado |
| `credito_admite_regime_especifico` | falso | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Falso e tomador em `Cad_Participante_Regime_Base`: base zero e motivo `tomador_regime_especifico`. | Leiaute oficial da escrituração ainda não fechado |
| `credito_admite_regime_especifico` | verdadeiro | `DERE` | condiciona_credito | componente de dedução da base do tomador na DeRE (`Cad_Componente_Base_Regime`) | Verdadeiro: o crédito só vale se a despesa não foi deduzida da base da DeRE do próprio tomador; se foi deduzida, o ERP avisa e o crédito sai zero. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `credito_exige_acordo_coletivo` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: sem `Mov_Rh_Beneficio_Acordo_Coletivo` com cláusula compulsória e mês dentro da janela, o crédito do mês sai zero (`Mov_Rh_Beneficio_Credito_Cbs.Situacao = sem_credito`). | Leiaute oficial da escrituração ainda não fechado |
| `credito_exige_declaracao_rfb` | qualquer valor | `ESCRITURACAO_IBS_CBS` | gera_aviso | declaração do art. 337, § 2º (sem obrigação no catálogo; o leiaute depende do ato conjunto) | Verdadeiro: se `Situacao_Declaracao` não é `declarado`, o ERP avisa; o cálculo do crédito não muda. Quando o ato for publicado, a obrigação ganha linha própria. | Ato conjunto da RFB e do CGIBS não publicado |
| `credito_inicio_vigencia` | qualquer valor | `ESCRITURACAO_IBS_CBS` | define_vigencia | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Pagamento anterior ao início de vigência: o ERP não calcula e grava o motivo `fora_vigencia` com aviso. Mudar a data (por exemplo, se o contador disser que há crédito em 2026) cria versão nova da regra. | Leiaute oficial da escrituração ainda não fechado |
| `credito_situacao_regra` | qualquer valor | `ESCRITURACAO_IBS_CBS` | gera_aviso | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Provisória: o registro de crédito grava `Regra_Provisoria` e o ERP mostra o aviso; o valor é calculado do mesmo jeito. Validada: o aviso some. | Leiaute oficial da escrituração ainda não fechado |
| `credito_base_regime_da_regra` | qualquer valor | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Define a linha de `Cad_Regime_Aliquota_Soma` de onde vêm as alíquotas gravadas no crédito (de 01/01/2027 em diante). | Leiaute oficial da escrituração ainda não fechado |
| `credito_base_regime_da_regra` | qualquer valor | `DERE` | define_fonte_do_dado | base de cálculo do fornecedor na DeRE | Identifica a base em que o fornecedor informa o tributo pago; é a base que o ERP do tomador usa para casar o crédito com a informação do fornecedor. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `credito_tomador_regras` | qualquer valor | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Para cada pagamento, o Motor escolhe a regra deste catálogo pela forma de captação, pelo tipo de arrendamento, pela base da antecipação ou pela informação do fornecedor, e aplica as marcas dela. | Leiaute oficial da escrituração ainda não fechado |
| `chave_forma_captacao` | operacao_credito | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Escolhe a regra `cred_operacao_credito`. | Leiaute oficial da escrituração ainda não fechado |
| `chave_forma_captacao` | titulo_divida | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Escolhe a regra `cred_titulo_divida`; o crédito depende do detentor. | Leiaute oficial da escrituração ainda não fechado |
| `chave_forma_captacao` | titulo_divida_oferta_publica | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Escolhe a regra `cred_titulo_oferta_publica`: o emissor não toma crédito (motivo `oferta_publica`). | Leiaute oficial da escrituração ainda não fechado |
| `chave_emprestimo_moeda_estrangeira` | verdadeiro | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro, com a marca `credito_veda_moeda_estrangeira` na regra: o crédito de juros sai zero (motivo `moeda_estrangeira`). | Leiaute oficial da escrituração ainda não fechado |
| `chave_emprestimo_credor` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | O credor precisa estar em `Cad_Participante_Regime_Base` na data do pagamento; fora dele o motivo é `fornecedor_fora_regime`. | Leiaute oficial da escrituração ainda não fechado |
| `chave_serie_uso_legal` | selic_diaria | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | `selic_diaria`: série acumulada no período do empréstimo. | Leiaute oficial da escrituração ainda não fechado |
| `chave_serie_uso_legal` | di_futuro | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | `di_futuro`: série entre as quais o Motor escolhe o vencimento mais próximo do recebível. | Leiaute oficial da escrituração ainda não fechado |
| `chave_serie_vencimento_di` | qualquer valor | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | O Motor escolhe a série de vencimento mais próximo do vencimento do recebível; no empate usa a regra do parâmetro `credito_empate_di_maior_taxa`. | Leiaute oficial da escrituração ainda não fechado |
| `chave_tipo_arrendamento` | operacional | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Operacional: regras `cred_arrend_oper_parcela` e `cred_arrend_oper_alienacao`. | Leiaute oficial da escrituração ainda não fechado |
| `chave_tipo_arrendamento` | financeiro | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Financeiro: regras `cred_arrend_fin_parcela` e `cred_arrend_fin_residual`. | Leiaute oficial da escrituração ainda não fechado |
| `chave_bem_arrendado` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | A classificação do bem dá a alíquota aplicada à base da parcela ou do valor residual. | Leiaute oficial da escrituração ainda não fechado |
| `chave_tipo_pagamento_arrendamento` | qualquer valor | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Escolhe a regra do tipo e o tipo de arrendamento; `alienacao_bem` só existe no operacional e só no decreto. | Leiaute oficial da escrituração ainda não fechado |
| `chave_encargos_arrendamento` | qualquer valor | `ESCRITURACAO_IBS_CBS` | gera_aviso | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Preenchido: o ERP avisa quando o crédito calculado passa da proporção de encargos. | Leiaute oficial da escrituração ainda não fechado |
| `chave_encargos_arrendamento` | verdadeiro | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Preenchido e `credito_arrend_financeiro_so_encargos` verdadeiro: a base do arrendamento financeiro é só o encargo. | Leiaute oficial da escrituração ainda não fechado |
| `chave_modalidade_antecipacao` | qualquer valor | `ESCRITURACAO_IBS_CBS` | seleciona_regra | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Escolhe `cred_desconto_cessao`, `cred_securitizacao_faturiz` ou `cred_antecipacao_arranjo`; a modalidade (`Modalidade`) só rotula a tela. | Leiaute oficial da escrituração ainda não fechado |
| `chave_detentor_titulo` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: o crédito é calculado. Falso: motivo `fornecedor_fora_regime`. Vazio: crédito a apropriar até a Plataforma ou o usuário confirmar. | Leiaute oficial da escrituração ainda não fechado |
| `chave_associado_cooperativa` | qualquer valor | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Com `credito_veda_cooperativa` verdadeiro na regra, o crédito sai zero. | Leiaute oficial da escrituração ainda não fechado |
| `chave_tomador_regime_especifico` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Com `credito_admite_regime_especifico` falso na regra, o crédito sai zero. | Leiaute oficial da escrituração ainda não fechado |
| `chave_origem_valor_credito` | qualquer valor | `ESCRITURACAO_IBS_CBS` | define_fonte_do_dado | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | `ajustado_pelo_usuario` exige motivo e aparece na conferência com o espelho como divergência de origem. | Leiaute oficial da escrituração ainda não fechado |
| `chave_proporcao_extincao` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Define o valor apropriável e o estado do crédito (a apropriar ou apropriado). | Leiaute oficial da escrituração ainda não fechado |
| `chave_clausula_compulsoria` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Falso: o benefício não dá crédito (`Motivo_Sem_Credito` registrado no mês). | Leiaute oficial da escrituração ainda não fechado |
| `chave_fim_vigencia_acordo` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Define a janela (`Dentro_Janela_Acordo`) com `Meses_Apos_Fim_Acordo`; fora da janela o crédito do mês é zero. | Leiaute oficial da escrituração ainda não fechado |
| `chave_situacao_declaracao` | qualquer valor | `ESCRITURACAO_IBS_CBS` | gera_aviso | declaração do art. 337, § 2º (sem obrigação no catálogo) | Com `credito_exige_declaracao_rfb` verdadeiro, avisa quando não está `declarado`; não muda o cálculo. | Ato conjunto da RFB e do CGIBS não publicado |
| `chave_origem_desconto_plano` | folha_erp | `ESCRITURACAO_IBS_CBS` | define_fonte_do_dado | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | `folha_erp`: desconto lido da folha do ERP; `documento_fiscal`: do documento fiscal da empresa (§ 5º, só registrado). | Leiaute oficial da escrituração ainda não fechado |
| `chave_origem_desconto_plano` | esocial | `ESOCIAL` | define_fonte_do_dado | informação de desconto de plano de saúde do eSocial | `esocial`: o desconto vem do eSocial por convênio (art. 337, § 3º); o ERP lê, não grava no eSocial. | A conferir no manual do eSocial |
| `chave_fonte_operadora` | dere_rfb | `DERE` | define_fonte_do_dado | DeRE da operadora de plano de saúde | `dere_rfb`: o débito de CBS e a proporção vêm da informação que a RFB disponibiliza a partir da DeRE da operadora. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `chave_fonte_operadora` | informado_usuario | `ESCRITURACAO_IBS_CBS` | define_fonte_do_dado | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | `informado_usuario`: o crédito é calculado com o valor digitado e o ERP avisa que não há confirmação da RFB. | Leiaute oficial da escrituração ainda não fechado |
| `existente_meses_apos_fim_acordo` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Calcula `Dentro_Janela_Acordo` do crédito do plano de saúde: o mês até 6 meses depois do fim do acordo ainda tem crédito. | Leiaute oficial da escrituração ainda não fechado |
| `existente_soma_aliquotas` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Define `Aliquota_Cbs_Aplicada` e `Aliquota_Ibs_Aplicada` do crédito; o crédito é a base vezes essa alíquota. | Leiaute oficial da escrituração ainda não fechado |
| `existente_soma_aliquotas` | qualquer valor | `DERE` | calcula_valor | alíquota da base na aferição do fornecedor | É a mesma soma que o fornecedor usa para calcular o débito dele; o crédito do tomador não pode passar do tributo que o fornecedor pagou. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `existente_base_do_participante` | qualquer valor | `ESCRITURACAO_IBS_CBS` | condiciona_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Credor, emissor ou operadora fora do regime específico: não há débito do qual nasça crédito. | Leiaute oficial da escrituração ainda não fechado |
| `existente_base_do_participante` | qualquer valor | `DERE` | define_fonte_do_dado | lista de bases do participante na DeRE | Define em quais bases o fornecedor entrega DeRE; sem a base, o ERP não espera a informação dele. | A conferir no manual da DeRE (fonte secundária, Q198-12) |
| `existente_qualificacao_cooperativa` | qualquer valor | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Alimenta `Associado_Cooperativa_Opcao`; com a regra que veda, o crédito do associado sai zero. | Leiaute oficial da escrituração ainda não fechado |
| `credito_tomador_juros_mora_na_base` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: a base do empréstimo e do título soma os juros de mora pagos. Falso: só o juro contratado entra. | Leiaute oficial da escrituração ainda não fechado |
| `credito_arrend_financeiro_so_encargos` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: base = `Valor_Encargos_Financeiros` da parcela. Falso: base = parcela inteira, com aviso quando passa da proporção de encargos. | Leiaute oficial da escrituração ainda não fechado |
| `credito_empate_di_maior_taxa` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Muda a taxa usada na curva DI do crédito do tomador e, portanto, o valor do excedente. | Leiaute oficial da escrituração ainda não fechado |
| `credito_dias_uteis_ano_curva_di` | qualquer valor | `ESCRITURACAO_IBS_CBS` | calcula_valor | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Entra no expoente da curva: (1 + taxa DI) ^ (dias úteis ÷ este número) − 1. | Leiaute oficial da escrituração ainda não fechado |
| `credito_oferta_restrita_como_publica` | qualquer valor | `ESCRITURACAO_IBS_CBS` | veda_credito | apuração dos créditos da escrituração (conta de créditos apropriados) e conferência com a aba de créditos do espelho (`Mov_Cbs_Apuracao_Espelho_Conta`) | Verdadeiro: o título de oferta restrita segue a regra `cred_titulo_oferta_publica` (sem crédito). Falso: segue `cred_titulo_divida`. | Leiaute oficial da escrituração ainda não fechado |

# Anexo C. Os mesmos efeitos, por obrigação

A mesma tabela do Anexo B lida ao contrário: para cada obrigação, os parâmetros que atuam nela. É a lista "Parâmetros que afetam esta obrigação" da seção 5.3.


## `ESCRITURACAO_IBS_CBS`: Escrituração digital do IBS e da CBS (apuração de débitos, créditos, ajustes e saldo; leiaute oficial ainda não fechado, documento 32) (51 efeitos)

Por tipo de efeito: calcula_valor (11), condiciona_credito (11), define_fonte_do_dado (4), define_vigencia (1), gera_aviso (4), seleciona_regra (11), veda_credito (9).

| Parâmetro | Quando o valor é | Tipo | O que muda |
|-------------------------|--------------------|---------------|-----------------------------------------|
| `credito_forma_calculo` | excedente_principal_selic | calcula_valor | Base = máximo(0, (valor pago − principal) − Selic sobre o principal); crédito = base × alíquota. Vale para empréstimo e título de dívida. |
| `credito_forma_calculo` | excedente_curva_di | calcula_valor | Base = soma, por recebível, do deságio que passa da curva DI; crédito = base × alíquota. Vale para desconto, cessão, factoring, securitização e antecipação de cartão. |
| `credito_forma_calculo` | parcela_pela_aliquota | calcula_valor | Base = parcela paga (contraprestação, valor residual ou alienação); crédito = base × alíquota da receita do arrendador. |
| `credito_forma_calculo` | valor_pago_pelo_fornecedor | define_fonte_do_dado | O ERP não calcula: grava o valor que o fornecedor informou (Plataforma, DeRE do fornecedor ou documento fiscal) como crédito. |
| `credito_forma_calculo` | proporcao_debito_fornecedor | calcula_valor | Crédito = débito do fornecedor × proporção dos empregados × parte que a empresa custeia (plano de saúde); capitalização: débitos extintos × proporção do prêmio. |
| `credito_forma_calculo` | sem_credito | veda_credito | Nenhum crédito; o registro sai com base zero e o motivo `regra_veda`. |
| `credito_regime_caixa` | qualquer valor | condiciona_credito | Verdadeiro: o gatilho é a baixa em `Mov_Titulo_Baixa` e a competência do crédito é a do pagamento. Falso: o crédito acompanha o fato registrado pelo fornecedor. |
| `credito_proporcao_extincao` | qualquer valor | condiciona_credito | Verdadeiro: o crédito nasce "a apropriar" e só passa a "apropriado" quando a Plataforma informa a proporção (`Proporcao_Extincao_Debito`); o valor apropriável é o calculado × proporção. Falso: o crédito é integral. |
| `credito_veda_cooperativa` | qualquer valor | veda_credito | Verdadeiro e tomador qualificado como associado que fez a opção (`Cad_Participante_Qualificacao_Cbs`): base zero e motivo `cooperativa`. |
| `credito_veda_moeda_estrangeira` | qualquer valor | veda_credito | Verdadeiro e `Mov_Emprestimo.Referenciado_Moeda_Estrangeira` ligado: base zero e motivo `moeda_estrangeira`. A regra de tarifas e comissões fica com falso. |
| `credito_admite_regime_especifico` | falso | veda_credito | Falso e tomador em `Cad_Participante_Regime_Base`: base zero e motivo `tomador_regime_especifico`. |
| `credito_exige_acordo_coletivo` | qualquer valor | condiciona_credito | Verdadeiro: sem `Mov_Rh_Beneficio_Acordo_Coletivo` com cláusula compulsória e mês dentro da janela, o crédito do mês sai zero (`Mov_Rh_Beneficio_Credito_Cbs.Situacao = sem_credito`). |
| `credito_exige_declaracao_rfb` | qualquer valor | gera_aviso | Verdadeiro: se `Situacao_Declaracao` não é `declarado`, o ERP avisa; o cálculo do crédito não muda. Quando o ato for publicado, a obrigação ganha linha própria. |
| `credito_inicio_vigencia` | qualquer valor | define_vigencia | Pagamento anterior ao início de vigência: o ERP não calcula e grava o motivo `fora_vigencia` com aviso. Mudar a data (por exemplo, se o contador disser que há crédito em 2026) cria versão nova da regra. |
| `credito_situacao_regra` | qualquer valor | gera_aviso | Provisória: o registro de crédito grava `Regra_Provisoria` e o ERP mostra o aviso; o valor é calculado do mesmo jeito. Validada: o aviso some. |
| `credito_base_regime_da_regra` | qualquer valor | seleciona_regra | Define a linha de `Cad_Regime_Aliquota_Soma` de onde vêm as alíquotas gravadas no crédito (de 01/01/2027 em diante). |
| `credito_tomador_regras` | qualquer valor | seleciona_regra | Para cada pagamento, o Motor escolhe a regra deste catálogo pela forma de captação, pelo tipo de arrendamento, pela base da antecipação ou pela informação do fornecedor, e aplica as marcas dela. |
| `chave_forma_captacao` | operacao_credito | seleciona_regra | Escolhe a regra `cred_operacao_credito`. |
| `chave_forma_captacao` | titulo_divida | seleciona_regra | Escolhe a regra `cred_titulo_divida`; o crédito depende do detentor. |
| `chave_forma_captacao` | titulo_divida_oferta_publica | veda_credito | Escolhe a regra `cred_titulo_oferta_publica`: o emissor não toma crédito (motivo `oferta_publica`). |
| `chave_emprestimo_moeda_estrangeira` | verdadeiro | veda_credito | Verdadeiro, com a marca `credito_veda_moeda_estrangeira` na regra: o crédito de juros sai zero (motivo `moeda_estrangeira`). |
| `chave_emprestimo_credor` | qualquer valor | condiciona_credito | O credor precisa estar em `Cad_Participante_Regime_Base` na data do pagamento; fora dele o motivo é `fornecedor_fora_regime`. |
| `chave_serie_uso_legal` | selic_diaria | seleciona_regra | `selic_diaria`: série acumulada no período do empréstimo. |
| `chave_serie_uso_legal` | di_futuro | seleciona_regra | `di_futuro`: série entre as quais o Motor escolhe o vencimento mais próximo do recebível. |
| `chave_serie_vencimento_di` | qualquer valor | seleciona_regra | O Motor escolhe a série de vencimento mais próximo do vencimento do recebível; no empate usa a regra do parâmetro `credito_empate_di_maior_taxa`. |
| `chave_tipo_arrendamento` | operacional | seleciona_regra | Operacional: regras `cred_arrend_oper_parcela` e `cred_arrend_oper_alienacao`. |
| `chave_tipo_arrendamento` | financeiro | seleciona_regra | Financeiro: regras `cred_arrend_fin_parcela` e `cred_arrend_fin_residual`. |
| `chave_bem_arrendado` | qualquer valor | calcula_valor | A classificação do bem dá a alíquota aplicada à base da parcela ou do valor residual. |
| `chave_tipo_pagamento_arrendamento` | qualquer valor | seleciona_regra | Escolhe a regra do tipo e o tipo de arrendamento; `alienacao_bem` só existe no operacional e só no decreto. |
| `chave_encargos_arrendamento` | qualquer valor | gera_aviso | Preenchido: o ERP avisa quando o crédito calculado passa da proporção de encargos. |
| `chave_encargos_arrendamento` | verdadeiro | calcula_valor | Preenchido e `credito_arrend_financeiro_so_encargos` verdadeiro: a base do arrendamento financeiro é só o encargo. |
| `chave_modalidade_antecipacao` | qualquer valor | seleciona_regra | Escolhe `cred_desconto_cessao`, `cred_securitizacao_faturiz` ou `cred_antecipacao_arranjo`; a modalidade (`Modalidade`) só rotula a tela. |
| `chave_detentor_titulo` | qualquer valor | condiciona_credito | Verdadeiro: o crédito é calculado. Falso: motivo `fornecedor_fora_regime`. Vazio: crédito a apropriar até a Plataforma ou o usuário confirmar. |
| `chave_associado_cooperativa` | qualquer valor | veda_credito | Com `credito_veda_cooperativa` verdadeiro na regra, o crédito sai zero. |
| `chave_tomador_regime_especifico` | qualquer valor | condiciona_credito | Com `credito_admite_regime_especifico` falso na regra, o crédito sai zero. |
| `chave_origem_valor_credito` | qualquer valor | define_fonte_do_dado | `ajustado_pelo_usuario` exige motivo e aparece na conferência com o espelho como divergência de origem. |
| `chave_proporcao_extincao` | qualquer valor | condiciona_credito | Define o valor apropriável e o estado do crédito (a apropriar ou apropriado). |
| `chave_clausula_compulsoria` | qualquer valor | condiciona_credito | Falso: o benefício não dá crédito (`Motivo_Sem_Credito` registrado no mês). |
| `chave_fim_vigencia_acordo` | qualquer valor | condiciona_credito | Define a janela (`Dentro_Janela_Acordo`) com `Meses_Apos_Fim_Acordo`; fora da janela o crédito do mês é zero. |
| `chave_situacao_declaracao` | qualquer valor | gera_aviso | Com `credito_exige_declaracao_rfb` verdadeiro, avisa quando não está `declarado`; não muda o cálculo. |
| `chave_origem_desconto_plano` | folha_erp | define_fonte_do_dado | `folha_erp`: desconto lido da folha do ERP; `documento_fiscal`: do documento fiscal da empresa (§ 5º, só registrado). |
| `chave_fonte_operadora` | informado_usuario | define_fonte_do_dado | `informado_usuario`: o crédito é calculado com o valor digitado e o ERP avisa que não há confirmação da RFB. |
| `existente_meses_apos_fim_acordo` | qualquer valor | condiciona_credito | Calcula `Dentro_Janela_Acordo` do crédito do plano de saúde: o mês até 6 meses depois do fim do acordo ainda tem crédito. |
| `existente_soma_aliquotas` | qualquer valor | calcula_valor | Define `Aliquota_Cbs_Aplicada` e `Aliquota_Ibs_Aplicada` do crédito; o crédito é a base vezes essa alíquota. |
| `existente_base_do_participante` | qualquer valor | condiciona_credito | Credor, emissor ou operadora fora do regime específico: não há débito do qual nasça crédito. |
| `existente_qualificacao_cooperativa` | qualquer valor | veda_credito | Alimenta `Associado_Cooperativa_Opcao`; com a regra que veda, o crédito do associado sai zero. |
| `credito_tomador_juros_mora_na_base` | qualquer valor | calcula_valor | Verdadeiro: a base do empréstimo e do título soma os juros de mora pagos. Falso: só o juro contratado entra. |
| `credito_arrend_financeiro_so_encargos` | qualquer valor | calcula_valor | Verdadeiro: base = `Valor_Encargos_Financeiros` da parcela. Falso: base = parcela inteira, com aviso quando passa da proporção de encargos. |
| `credito_empate_di_maior_taxa` | qualquer valor | calcula_valor | Muda a taxa usada na curva DI do crédito do tomador e, portanto, o valor do excedente. |
| `credito_dias_uteis_ano_curva_di` | qualquer valor | calcula_valor | Entra no expoente da curva: (1 + taxa DI) ^ (dias úteis ÷ este número) − 1. |
| `credito_oferta_restrita_como_publica` | qualquer valor | veda_credito | Verdadeiro: o título de oferta restrita segue a regra `cred_titulo_oferta_publica` (sem crédito). Falso: segue `cred_titulo_divida`. |

## `DERE`: DeRE: declaração de regimes específicos de IBS e CBS (leiaute oficial não lido, Q198-12) (6 efeitos)

Por tipo de efeito: calcula_valor (1), condiciona_credito (1), define_fonte_do_dado (4).

| Parâmetro | Quando o valor é | Tipo | O que muda |
|-----------------------|-------------------|----------------|------------------------------------------|
| `credito_forma_calculo` | valor_pago_pelo_fornecedor | define_fonte_do_dado | O crédito só nasce se o fornecedor, na DeRE dele, identificar o tomador e o tributo que pagou; sem isso o ERP do tomador avisa e não cria crédito. |
| `credito_admite_regime_especifico` | verdadeiro | condiciona_credito | Verdadeiro: o crédito só vale se a despesa não foi deduzida da base da DeRE do próprio tomador; se foi deduzida, o ERP avisa e o crédito sai zero. |
| `credito_base_regime_da_regra` | qualquer valor | define_fonte_do_dado | Identifica a base em que o fornecedor informa o tributo pago; é a base que o ERP do tomador usa para casar o crédito com a informação do fornecedor. |
| `chave_fonte_operadora` | dere_rfb | define_fonte_do_dado | `dere_rfb`: o débito de CBS e a proporção vêm da informação que a RFB disponibiliza a partir da DeRE da operadora. |
| `existente_soma_aliquotas` | qualquer valor | calcula_valor | É a mesma soma que o fornecedor usa para calcular o débito dele; o crédito do tomador não pode passar do tributo que o fornecedor pagou. |
| `existente_base_do_participante` | qualquer valor | define_fonte_do_dado | Define em quais bases o fornecedor entrega DeRE; sem a base, o ERP não espera a informação dele. |

## `ESOCIAL`: eSocial (obrigação nova no catálogo, a aprovar na Q201-6) (1 efeitos)

Por tipo de efeito: define_fonte_do_dado (1).

| Parâmetro | Quando o valor é | Tipo | O que muda |
|----------------------|--------------|-----------------|-----------------------------------------------|
| `chave_origem_desconto_plano` | esocial | define_fonte_do_dado | `esocial`: o desconto vem do eSocial por convênio (art. 337, § 3º); o ERP lê, não grava no eSocial. |

## `ECD` e `ECF`: sem efeito documentado

- **ECD:** Lançamento contábil do crédito a recuperar e da despesa financeira líquida. Sem efeito documentado; ver a C246.
- **ECF:** Efeito do crédito na base do IRPJ e da CSLL (despesa financeira líquida do tributo recuperável). Sem efeito documentado; ver a C246.

# Anexo D. As cargas

## D.1 Linhas novas em `Cad_Obrigacao_Parametro_Definicao` (6)

Todas na obrigação `ESCRITURACAO_IBS_CBS`, com vigência desde 01/01/2027. A primeira é a tabela das regras (em leitura); as cinco seguintes são as leituras provisórias, por empresa, sem obrigatoriedade.

| Código | Rótulo | Tipo | Nível | Armazenamento | Ajuda |
|--------------------|---------------------------|------|-----|---------|---------------------------------|
| `credito_tomador_regras` | Regras do crédito do tomador de serviço financeiro | cadastro | global | tabela_propria | Catálogo legal das 28 regras de crédito de quem compra o serviço financeiro, o arrendamento, a antecipação e o plano de saúde dos empregados; cada marca da regra tem documentação de efeito (documento 201). Em leitura; o contador valida as linhas. |
| `credito_tomador_juros_mora_na_base` | Juros de mora entram na despesa financeira do crédito | booleano | empresa | central | Verdadeiro: a base do empréstimo e do título soma os juros de mora. Falso (padrão provisório): só o juro contratado. Muda o valor do crédito calculado na escrituração do IBS e da CBS; aguarda a C239. |
| `credito_arrend_financeiro_so_encargos` | Crédito do arrendamento financeiro só sobre os encargos | booleano | empresa | central | Verdadeiro: base = encargos financeiros da parcela. Falso (padrão provisório): parcela inteira, com aviso de excesso. Muda o valor do crédito na escrituração do IBS e da CBS; aguarda a C241. |
| `credito_empate_di_maior_taxa` | Empate de vencimentos do DI: usar a maior taxa | booleano | empresa | central | Verdadeiro: maior taxa. Falso (padrão provisório): menor taxa, como o art. 290 do decreto. Muda o excedente da curva DI na escrituração do IBS e da CBS; aguarda a C242. |
| `credito_dias_uteis_ano_curva_di` | Dias úteis por ano na curva DI | numero | empresa | central | Divisor dos dias úteis na fórmula da curva DI (padrão provisório 252). Muda o excedente da curva DI na escrituração do IBS e da CBS; aguarda a C242. |
| `credito_oferta_restrita_como_publica` | Oferta de esforços restritos conta como oferta pública | booleano | empresa | central | Verdadeiro (padrão provisório): o título de oferta restrita não dá crédito ao emissor. Falso: dá, como o título sem oferta pública. Muda a regra escolhida na escrituração do IBS e da CBS; aguarda a C240. |

## D.2 Linha nova em `Cad_Obrigacao_Acessoria` (1)

| Código | Descrição | Início |
|--------|----------------------------------------------------|----------------------------------------|
| `ESOCIAL` | eSocial: escrituração digital das obrigações fiscais, previdenciárias e trabalhistas | 01/01/2026 (uso no ERP, D-N323; não é a data legal) |

## D.3 `Cad_Parametro_Documentacao` (41 linhas) e `Cad_Parametro_Efeito_Obrigacao` (58 linhas)

São as tabelas dos Anexos A e B, nos arquivos `Cad_Parametro_Documentacao.csv` e `Cad_Parametro_Efeito_Obrigacao.csv`. Todas as linhas nascem `provisorio` e com vigência de 01/01/2027 a 31/12/9999.

# Anexo E. Perguntas ao contador (C246 e C247)

Estão também no documento 188, que passa a ter 247 perguntas.

**C246 · LC 214, arts. 194 a 203, e Decreto 12.955, arts. 284 a 298 · Crédito do tomador de serviço financeiro: efeito na ECD e na ECF**

*Documento 201, seção 4.8 (Q201-8)*

O documento 201 documenta o efeito de cada parâmetro do crédito do tomador nas obrigações. Para a escrituração do IBS e da CBS e para a DeRE há norma que ancora o efeito. Para a ECD e a ECF não encontrei norma: o crédito de CBS e de IBS do tomador reduz o custo da despesa financeira, do arrendamento e da antecipação, mas o dicionário não diz como a contabilidade e o IRPJ e a CSLL tratam isso.

Pergunta: (a) o crédito de CBS e de IBS do tomador é registrado como tributo a recuperar e a despesa financeira (ou de arrendamento, ou o deságio) é registrada pelo valor líquido do crédito? (b) na ECF, a despesa dedutível é a líquida do crédito, e o crédito não entra na receita? (c) no arrendamento financeiro e na antecipação, o tratamento muda por tipo de pagamento (parcela, valor residual, alienação)? (d) há conta do plano referencial da ECD ou código da ECF específico para o crédito do tomador?

Proposta do documento 201 (Q201-8): nenhum efeito é documentado na ECD e na ECF até a sua resposta; o crédito segue como Mov_Credito_Fiscal, sem lançamento automático novo; nada aplicado ao dicionário.

**C247 · LC 214, art. 198, parágrafo único, e Decreto 12.955, art. 292 · Tomador em regime específico: como mostrar na DeRE que a despesa não foi deduzida da base**

*Documento 201, seção 4.6 (Q201-8)*

O crédito de tarifas e comissões do tomador que também está em regime específico só vale se a despesa não foi deduzida da base de cálculo dele. O documento 198 criou o catálogo de componentes da base, mas nenhum item diz se a tarifa paga a outro fornecedor de serviço financeiro é ou não dedução na DeRE do tomador.

Pergunta: (a) tarifas, comissões e outras despesas pagas a fornecedor do regime específico entram em algum componente de dedução da DeRE do tomador, ou são sempre despesa fora da base? (b) se a empresa deduz parte da despesa, o crédito é proporcional à parte não deduzida? (c) o tomador precisa informar na DeRE a despesa de que tomou crédito, ou a conferência é só da Plataforma? (d) o tomador em regime específico que toma crédito na tarifa precisa individualizar o fornecedor?

Proposta do documento 201 (Q201-8): o ERP verifica se o componente de dedução da despesa está ligado na DeRE do tomador e avisa, sem bloquear; o crédito sai zero quando a despesa foi deduzida; nada aplicado ao dicionário.

