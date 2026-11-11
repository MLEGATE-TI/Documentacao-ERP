# Cobertura do dicionário contra o Guia Prático da EFD-ICMS/IPI v3.2.4 — Documento 167

*Resposta à sua pergunta de 03/11/2026: o desenho já cobre a entrega do Guia v3.2.4 (30/07/2026)? Conferi registro a registro. Nada deste documento entrou no dicionário; só entra com o seu "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resposta curta

**Cobre em parte.** O desenho cobre bem os blocos E (apurações), G (CIAP), H (inventário) e K (produção e estoque), o núcleo do C100 e o C500 com NF3e e NFGás de entrada. Mas **não cobre inteiro**: de 270 registros do guia, **151 estão cobertos ou saem por derivação (56%)**, **92 estão parciais** (faltam campos) e **28 não têm onde guardar o dado**.

Eu tinha registrado "nada a aplicar" porque li a sua frase como afirmação. Era pergunta, e a conferência de verdade mostra lacunas. Corrigi os documentos 14, 38 e 166 (seção 7).

Os pontos que mais pesam, em ordem:

1. **Campos novos do leiaute 2027** (o guia 3.2.3 já os traz, com vigência a partir do período de janeiro de 2027): `IND_BENEFICIO` em C197, C597, D197, D737, E111, E220 e 1921, e a nota de crédito por redução (`COD_SIT` 09 e 10, exceção 12 do C100). **Não existem no dicionário.** O ERP nasce em 2026, então eles têm de estar prontos.
2. **ICMS-ST, FCP e DIFAL por item e o núcleo de ressarcimento de ST** (C101, C170, C176, C180 a C186, C191, 1250 e 1255): faltam valores unitários, alíquota de ST, FCP por item e a partilha DIFAL por item.
3. **Processo e histórico nas obrigações a recolher** (E116, E250, E316 e 1926): faltam `IND_PROC`, `PROC` e `TXT_COMPL`.
4. **Documentos referenciados e ajustes de documento fora do ERP** (C113, C114, C116, E113, E240, E313, E531): só se guarda a chave, e o guia pede modelo, série, número, data e participante.
5. **Blocos setoriais** (combustíveis, usina, DCTA, GIAF, faixa de documentos, exportação detalhada, controle de créditos, ECF/cupom em termos de ICMS, bilhetes de passagem): 13 registros do Bloco 1 e 9 do Bloco D estão sem estrutura. Você aprovou em 05/10/2026 que "todas as lacunas da EFD entram agora", por parâmetro de habilitação por empresa. A conferência de 05/10 olhou as lacunas dos blocos B, D, E, G, H e K num nível mais geral; o Bloco 1 e boa parte do C e do D só agora foram conferidos campo a campo.

# 2. Como conferi

Li o guia inteiro (270 registros, 1.843 campos) e comparei, registro a registro, com o dicionário da revisão 29 (1.020 entidades). Seis conferências paralelas, uma por bloco, cada uma com a tabela por registro (anexos A a F). Julguei pelas **suas regras**: o ERP só registra, o arquivo é gerado dos dados (não exige tabela espelho por registro), registros de abertura, encerramento, totais e analíticos contam como **derivados** quando a origem existe, e parâmetro com vigência, sem valor escondido.

Vereditos: **coberto** (cada campo tem origem), **coberto por derivação**, **parcial** (faltam campos) e **ausente** (não há onde guardar).

Limites da conferência, para você pesar o resultado:

- A listagem do dicionário que usei **corta as listas de valores longas** (enumerações). Onde o veredito dependia de um valor cortado, o anexo diz.
- **Não conferi as cargas** das tabelas oficiais (4.1.2, 5.3, 5.5, 5.6, 5.7, 5.9.1, 4.4.6 e cClass da NF3e e da NFGás). O documento 43 já diz que várias não foram carregadas; isso é pendência de carga, não de desenho.
- A extração do guia em texto perdeu alguns campos; os agentes conferiram esses no guia completo.
- A contagem por registro é aproximada (alguns registros foram avaliados em grupo).

# 3. Resultado por bloco

| Bloco | Registros | Cobertos | Por derivação | Parciais | Ausentes |
|---|---|---|---|---|---|
| 0, B, 9, G e H | 53 | 26 | 20 | 7 | 0 |
| C, parte 1 (C001 a C197) | 36 | 7 | 3 | 22 | 4 |
| C, parte 2 (C300 a C897) | 47 | 9 | 18 | 18 | 2 |
| D | 49 | 4 | 15 | 20 | 9 (6 são modelos obsoletos desde 2019) |
| E e K | 49 | 26 | 10 | 13 | 0 |
| 1 | 38 | 5 | 8 | 12 | 13 |
| **Total** | **272** | **77** | **74** | **92** | **28** |

O total passa de 270 porque alguns registros aparecem em dois grupos. Leitura: **E, G, H e K estão sólidos** (os ajustes são localizados). O **Bloco C** tem a maior parte dos parciais, porque o C170, o C176 e o ressarcimento de ST cobrem o dado principal mas faltam campos do leiaute novo. O **Bloco 1** concentra os ausentes, todos setoriais.

# 4. O que mudou nas versões 3.2.3 e 3.2.4

| Mudança do guia | Situação no dicionário |
|---|---|
| **3.2.4**: Nota Orientativa 2026.001, escrituração da NFGás modelo 76 em C500, C510 e C590 | **Coberta no essencial**: `Mov_Nfgas_Entrada` e filhas (revisão 29), chave em texto, C590 derivável. **Faltam**: `ENER_INJET` e `OUTRAS_DED` (C500 campos 39 e 40), o mapa do cClass para o campo da EFD que ele alimenta (como já existe para a NFCom), a tabela cClass (Q165-12) e a regra "NFGás só finalidade 1 e 2", que o dicionário não mostra. |
| 3.2.3: CNPJ de N para C (0000, 0100, 0150, C115, C175, 1320) | **Atendida** onde há campo (`Documento_Principal` do participante). **Falta** o CNPJ da concessionária no C175 (não há campo). |
| 3.2.3: chave de documento eletrônico de N para C (B020, C100, C113, C116, C176, C181, C186, C465, C500, C800, D100, D700, E113, E240, E313, E531, G130, 1105, 1110, 1210, 1923) | **Atendida**: `Chave_Acesso` é texto de até 50 posições. Ressalva: onde o documento não está no ERP, só a chave não basta (item 4 da seção 1). |
| 3.2.3: `IND_BENEFICIO` (C197, C597, D197, D737 campo 09; E111, E220, 1921 campo 05) | **Ausente.** Vigência: leiaute 2027 (subseção 16 do guia), obrigatório a partir do período de janeiro de 2027. |
| 3.2.3: `COD_PROD` no C180 (campo 12) | **Ausente.** |
| 3.2.3: `COD_SIT` 09 e 10 (nota de crédito por redução) e exceção 12 do C100 | **Depende da carga e do desenho.** A situação do documento é a tabela 4.1.2 em `Cad_Classe_Sistema`; falta confirmar os valores 09 e 10 na carga, e a finalidade da nota de entrada não tem "crédito" nem "débito". A exceção 12 vale a partir de 01/01/2027. |
| 3.2.3: validações de C500 campo 38, D700 campo 30, D530 campo 05, D100 campo 25, totais de E110, E210, E310 e 1920 | **Totais cobertos.** D100 campo 25: faltam os municípios sentinela 9999999 e 9999998 e a regra com vigência (9999998 vedado de 2027 em diante). |
| 3.2.2: `VL_DOC` do C100 inclui IBS/CBS exceto em 2026; documento só com IBS/CBS não se escritura | **Coberta**: o valor total é "tal como emitido" e o item não soma IBS, CBS e IS. |
| 3.2.1: `SER` do D700 de N para C | **Atendida** (série em texto). |

# 5. As lacunas, agrupadas

As lacunas vêm dos seis anexos. Ordenei por quando passam a ser exigidas ou por quão comum é o caso. Cada proposta segue o padrão do projeto: parâmetro com vigência, sem valor escondido, aviso e não bloqueio.

## 5.1 Obrigatórias a partir de janeiro de 2027 (leiaute 2027)

**G1. Indicador de benefício (`IND_BENEFICIO`).** Valores 0, 1, 2, 3 e 9; obrigatório quando o terceiro dígito do código de ajuste não é 9. Proposta: campo `Indicador_Beneficio` em `Mov_Apuracao_Ajuste` (E111, E220, 1921) e em `Mov_Nota_Ajuste_Documento` (C197, C597, D197, D737), com **sugestão por código de ajuste** em `Cad_Icms_Codigo_Ajuste` (padrão por código e UF, com vigência a partir de 01/01/2027).

**G2. Nota de crédito por redução (`COD_SIT` 09 e 10, exceção 12 do C100).** Confirmar 09 e 10 na tabela 4.1.2 e acrescentar a finalidade "nota de crédito de redução" na nota de entrada, com a regra de que o documento de terceiros entra como saída (`IND_OPER` 1, `IND_EMIT` 1).

**G3. Município sentinela e regra do D100 campo 25.** Aceitar 9999999 (exterior) e 9999998 (origem do CT-e simplificado) em `Cad_Municipio` sem o prefixo de UF, e guardar a regra "9999998 vedado a partir de 2027" em `Cad_Obrigacao_Leiaute_Campo.Valores_Validos` com vigência.

**G4. Obrigatoriedade por entrada e por saída.** `Cad_Obrigacao_Leiaute_Campo.Eh_Obrigatorio` é um só booleano; o guia distingue entrada, saída e "opcional condicional". Proposta: duas colunas (entrada e saída) com vigência.

## 5.2 De uso comum (empresa industrial ou comercial)

**G5. ICMS-ST, FCP e DIFAL por item.** Faltam alíquota do ST (`pICMSST`), FCP próprio, FCP do ST e FCP retido por item, e a partilha DIFAL por item (destino, remetente, FCP de destino). Atinge C101, C170, C191, D101, D731 e D761. Proposta: declarar as parcelas em `Cad_Imposto` (ICMS destino, ICMS remetente, FCP) e dar a cada linha de `Mov_Apuracao_Tributo_Item` um **tipo de parcela**.

**G6. Núcleo de ressarcimento e complemento de ST (C176, C180, C181, C185, C186, C330, C380, C430, C480, C815, C880, 1250, 1255).** Os valores unitários por movimento e de estoque médio não têm entidade; `Mov_Icms_St_Ressarcimento` segue o leiaute antigo do C176. Faltam também `COD_RESP_RET`, `COD_DA` e `NUM_DA`, a NF-e da retenção, base e alíquota do ICMS próprio da última entrada, `COD_PROD` (cProd do fornecedor, campo novo do C180) e os cinco valores da consolidação do 1255 com a tabela 5.7 de motivos.

**G7. Processo e histórico nas obrigações a recolher (E116, E250, E316, 1926).** Faltam `IND_PROC`, `PROC` e `TXT_COMPL`; `Numero_Processo` tem 15 posições (o guia admite 60); `Mes_Referencia` deve ser obrigatório.

**G8. Documentos referenciados e ajustes de documento fora do ERP (C113, C114, C116, C115, E113, E240, E313, E531).** Falta guardar modelo, série, subsérie, número, data de emissão, participante, equipamento e COO. Proposta: campos opcionais nas entidades de referência e de ajuste de documento, obrigatórios quando não há documento no ERP.

**G9. CIAP (G130).** O documento de saída (alienação e transferência, `TIPO_MOV` AT e outros) não tem ligação, e `Mov_Ciap_Bem.ID_Item_Nota_Entrada` é obrigatório, o que impede bem que entrou antes do ERP.

**G10. Bloco K.** (a) **K200 com `IND_EST` 1 e 2**: nada alimenta o material de terceiros em poder da Mlegate nem o próprio em poder de terceiros, e os documentos 04 e 06 se contradizem sobre o assunto; (b) K235 e K255 sem origem para a data de consumo; (c) obrigatoriedade dos registros do K por tipo de leiaute (tabela do K010) está escondida no código, não em parâmetro; (d) IPI decendial: `Mov_Apuracao_Ipi` só tem a competência, faltam as datas do decêndio (E500, K100).

**G11. Rótulos trocados em `Mov_Apuracao_Ipi`.** `Ipi_Recolher` e `Saldo_Credor_Transportar` estão com `VL_SD_IPI` e `VL_SC_IPI` invertidos nas descrições, e `Estornos` mistura `VL_OD_IPI` e `VL_OC_IPI`. É correção de descrição e separação de coluna.

**G12. CT-e simplificado (D130, desde janeiro de 2025).** Falta o detalhe por entrega (município de origem e destino, valor, componentes, documentos), a classe do componente de valor, o redespachado e `IND_FRT_RED`.

**G13. ISS no DF (Bloco B).** B020 sem `VL_MAT_TER`, `VL_SUB` e `VL_DED_BC` por documento (hoje só como total em `Mov_Apuracao_Iss_Df`, o que contraria "o ERP só registra"); B510 sem cadastro do profissional não habilitado e sem a regra de `IND_ESC`; B350 (instituição financeira) sem `QTD_OCOR`, `COD_SERV` e o vínculo com o COSIF.

**G14. NF3e e NFGás (C500).** `ENER_INJET` e `OUTRAS_DED`, e o mapa do cClass para o campo da EFD que ele alimenta (como já existe para a NFCom em `Cad_Nfcom_Classificacao_Servico`).

## 5.3 Setoriais (entram por habilitação por empresa, como você aprovou em 05/10)

**G15. Bloco 1.** Combustíveis (1300 a 1370: tanque, bomba, lacre, bico, medição e aferição), usina (1390 e 1391), faixa de documentos utilizados e cancelados (1700 e 1710), DCTA (1800), GIAF (1960 a 1980), valores agregados (1400, com a tabela 5.9.1), exportação detalhada (1100 e 1110: `IND_DOC`, `DT_DE`, `DT_RE`, `CHC_EMB`, `DT_CHC`, `TP_CHC`, `NR_MEMO`), controle de créditos (1200 e 1210: vínculo com o código 5.1.1, `CRED_RECEB`, tabela 5.5, `NR_DOC`, `CHV_DOCe`) e energia (1510: `IND_REC` e participante).

**G16. Cupom e ECF em termos de ICMS.** C420 (totalizadores parciais, tabela 4.4.6), C460, C465 e C470 (cupom), ICMS por totalizador na Redução Z (`Mov_Ecf_Reducao_Z_Tributo` só traz PIS e Cofins), C300 a C395 (nota modelo 02), C591 (FCP por item), C700, C895 e C897.

**G17. Combustíveis na entrada (C165, C171) e outros do C.** C112 (documento de arrecadação), C165 (`NR_PASSE`, `TEMPER`, motorista), C171 (tanque de recebimento), C179 (repasse, dedução e complemento de ST), C173 (`IND_MED`, `TP_PROD`), C178 (`CL_ENQ`), C140 (`IND_TIT`, `NUM_TIT`), C130 (`VL_SERV_NT`, IRRF e previdência), C105 (`UFST`).

**G18. Transporte de passageiros, comunicação e BP-e.** BP-e modelo 63 (sem estrutura); D300 a D420 (bilhetes e resumo de movimento diário); D500, D510 e D530 na saída (modelos 21 e 22); D695 e D696 (Convênio ICMS 115/03); D160 a D162 para CTRC em papel.

**G19. Cadastros.** 0220 (`COD_BARRA` por unidade convertida), H010 (`TXT_COMPL` e `COD_CTA`), e a consolidação do H005 por filial.

## 5.4 O que não é lacuna

O guia proíbe os modelos 07, 09, 10, 11, 26 e 27 com data de 2019 em diante, e o ERP nasce em 2026; por isso D110, D120, D140, D150, D170, D180 e parte de D160 a D162 **não precisam ser desenhados**. Também não desenhar o 0210 (revogado em 2021) nem o C495 (obsoleto desde 2014). Registros de abertura, encerramento e totais (X001, X990, 9900, 9990, 9999, C190, E110, E210 e E310) saem por derivação.

# 6. Perguntas para você

**Q167-1.** As lacunas G1 a G14 são de uso comum ou obrigação de 2027: posso desenhar todas na próxima revisão? *(Minha recomendação: sim.)*

**Q167-2.** As lacunas setoriais (G15 a G19) entram **todas agora**, por habilitação, como você decidiu em 05/10, ou só as que a Mlegate usa de fato? Se souber quais negócios a Mlegate tem (venda a consumidor com nota 02, ECF ou SAT, combustível, usina, fornecimento de energia, gás ou água, transporte de passageiros, Convênio 115), digo o que cai fora.

**Q167-3.** K200 com `IND_EST` 1 e 2 (documentos 04 e 06 se contradizem): (a) tratar o material de terceiros como movimento de estoque de propriedade de terceiros, sem valor, com participante; ou (b) calcular o saldo por nota (remessa menos consumo menos retorno)? *(Recomendo (a), porque o inventário H010 também precisa do mesmo saldo.)*

**Q167-4.** Nota de crédito por redução (G2): acrescento uma finalidade própria na nota de entrada e uma regra de que o documento de terceiros entra como saída, ou prefere tratar o caso só como situação do documento (`COD_SIT` 09 e 10)?

**Q167-5.** Tabelas oficiais ainda não carregadas (4.4.6, 5.3, 5.5, 5.6, 5.7, 5.9.1 e o cClass da NF3e e da NFGás): você manda os arquivos ou eu monto a carga de partida pelo guia e marco como provisória?

**Q167-6.** O Bloco 1 de combustíveis e usina (1300 a 1391) é grande (cadastros de tanque, bomba, bico e lacre, mais leituras diárias). Desenho em uma revisão só, ou separo em uma revisão própria?

# 7. O que corrigi nos documentos anteriores

- **Documento 14, D-N457 (item 4)**: tinha "nada a aplicar" para o guia. Agora diz que a conferência mostrou lacunas e remete a este documento.
- **Documento 38**: o guia passa a constar como pendência (lacunas e perguntas Q167-1 a Q167-6).
- **Documento 166, seção 4**: a linha do guia da EFD-ICMS/IPI foi corrigida.

---

# Anexos: tabelas por registro

Os anexos abaixo são a conferência bruta de cada agente. As tabelas por registro dizem, para cada registro do guia, o veredito, onde está no dicionário e quais campos faltam. Mantive o texto como veio, sem reescrever, para você poder conferir.



# Anexo A — Blocos 0, B, 9, G e H


Escopo: 53 registros (bloco 0: 23; bloco B: 13; bloco 9: 4; bloco G: 7; bloco H: 6).
Fontes: `guide_A.txt` (completado com `/tmp/efd324.txt` onde a extração perdeu campos: 0000 campos 09 UF, 10 IE e 12 IM; 0150 campo 07 IE; 0500 campo 05 NIVEL) e `dict_dump.txt`.
Critérios: regras do projeto (o ERP só registra; derivados contam como COBERTO-DERIVADO se a origem existe; parâmetros por empresa/filial com vigência).

##### Resumo por veredito

| Veredito | Qtde | Registros |
|---|---|---|
| COBERTO | 26 | 0000, 0002, 0005, 0015, 0100, 0150, 0190, 0200, 0205, 0206, 0221, 0300, 0305, 0450, 0460, 0500, 0600, B460, B470, B500, G110, G125, G126, G140, H020, H030 |
| COBERTO-DERIVADO | 20 | 0001, 0175, 0400, 0990, B001, B025, B030, B035, B420, B440, B990, 9001, 9900, 9990, 9999, G001, G990, H001, H005, H990 |
| PARCIAL | 7 | 0210 (obsoleto), 0220, B020, B350, B510, G130, H010 |
| AUSENTE | 0 | nenhum |

##### Bloco 0

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| 0000 | Abertura do arquivo e identificação da entidade | COBERTO | `Mov_Escrituracao_Arquivo` (DT_INI/DT_FIN = Periodo_Inicio/Periodo_Fim; COD_FIN = Finalidade original/substituta; COD_VER = Versao_Leiaute, com a tabela `Cad_Obrigacao_Leiaute_Versao` e `Cad_Obrigacao_Acessoria` = SPED_FISCAL; ID_Filial). NOME, CNPJ/CPF, UF, COD_MUN, IE, IM, SUFRAMA vêm de `Cad_Filial.ID_Participante` → `Cad_Participante` (Nome_Razao_Social, Documento_Principal), `Cad_Participante_Endereco` (tipo fiscal, ID_Municipio → UF) e `Cad_Participante_Inscricao` (estadual, municipal, suframa). IND_PERFIL e IND_ATIV = `Cad_Filial_Perfil_Fiscal` (ID_Perfil_Efd, ID_Indicador_Atividade_Sped), com vigência. | nenhum (ver dúvida D1 sobre o Convênio 113/04) |
| 0001 | Abertura do bloco 0 | COBERTO-DERIVADO | IND_MOV deriva da existência de dados no bloco | nenhum |
| 0002 | Classificação do estabelecimento industrial | COBERTO | `Cad_Filial_Perfil_Fiscal.ID_Classe_Estabelecimento_Industrial` (CLAS_ESTAB_IND; só quando IND_ATIV = 0) | nenhum |
| 0005 | Dados complementares da entidade | COBERTO | `Cad_Participante.Nome_Fantasia` (FANTASIA), `Cad_Participante_Endereco` fiscal (CEP, Logradouro, Numero, Complemento, Bairro), `Cad_Participante_Telefone` (FONE e FAX por Tipo_Telefone), `Cad_Participante_Email` | nenhum (D2: FANTASIA é opcional no dicionário e obrigatória no guia) |
| 0015 | Contribuinte substituto ou responsável pelo ICMS destino | COBERTO | `Cad_Participante_Inscricao` com Tipo_Inscricao = estadual_substituto (ID_Estado = UF_ST, Numero_Inscricao = IE_ST), uma linha por UF | nenhum |
| 0100 | Dados do contabilista | COBERTO | `Cad_Empresa_Responsavel` (Tipo_Papel = contador, por empresa ou filial, com vigência) → ID_Participante (NOME, CPF, endereço, fone, e-mail) e ID_Participante_Escritorio (CNPJ do escritório, alfanumérico); CRC = ID_Estado_Crc + Numero_Sequencial_Crc | nenhum (D3: confirmar que Numero_Sequencial_Crc guarda o nº de inscrição no CRC e não só a certidão) |
| 0150 | Cadastro do participante | COBERTO | `Cad_Participante` (NOME; CNPJ ou CPF em Documento_Principal por Tipo_Pessoa), `Cad_Pais.Codigo_Bacen` (COD_PAIS, Brasil = 1058), `Cad_Participante_Inscricao` (IE, SUFRAMA), `Cad_Participante_Endereco` (COD_MUN via ID_Municipio, END, NUM, COMPL, BAIRRO). COD_PART é gerado a partir de ID_Participante. | nenhum |
| 0175 | Alteração do cadastro de participante | COBERTO-DERIVADO | Histórico de versões com vigência de `Cad_Participante`, `Cad_Participante_Endereco` e `Cad_Participante_Inscricao` (DT_ALT = Vigencia_Inicio; CONT_ANT = valor da versão anterior; NR_CAMPO = mapeamento do campo) | nenhum |
| 0190 | Unidades de medida | COBERTO | `Cad_Unidade_Medida` (UNID = Sigla; DESCR = Nome) | nenhum (D4: tamanho máximo de Sigla não declarado; guia: 6) |
| 0200 | Tabela de identificação do item | COBERTO | `Cad_Produto_Servico` (COD_ITEM = Codigo_Item, DESCR_ITEM = Descricao, TIPO_ITEM = ID_Tipo_Item_Sped), `Cad_Produto_Servico_Dados_Produto` (COD_BARRA = Gtin; UNID_INV = ID_Unidade_Medida; COD_NCM = ID_Classificacao_NCM; EX_IPI = ID_Ex_Tipi; CEST = ID_Cest), `Cad_Produto_Servico_Codigo_Anterior` (COD_ANT_ITEM), `Cad_Produto_Servico_Dados_Servico` + `Cad_Servico_Tributacao_Nacional` (COD_LST, item da LC 116). COD_GEN deriva dos 2 primeiros dígitos do NCM. ALIQ_ICMS deriva de `Cad_Aliquota` (ICMS interno por UF) pelo Motor de Regras. | nenhum (COD_GEN e ALIQ_ICMS são derivados, sem campo próprio) |
| 0205 | Alteração do item | COBERTO | `Cad_Produto_Servico_Codigo_Anterior` (DESCR_ANT_ITEM = Descricao_Anterior, COD_ANT_ITEM = Codigo_Item_Anterior, DT_INI = Data_Inicio_Uso, DT_FIM = Data_Fim_Uso) | nenhum (D5: Data_Inicio_Uso é opcional; DT_INI é O no guia) |
| 0206 | Código de produto ANP | COBERTO | `Cad_Produto_Anp` (Codigo = COD_COMB) via `Cad_Produto_Servico_Dados_Produto.ID_Produto_Anp` | nenhum |
| 0210 | Consumo específico padronizado (válido até 31/12/2021) | PARCIAL (obsoleto) | `Cad_Estrutura_Producao` e `Cad_Estrutura_Producao_Item` (COD_ITEM_COMP = ID_Produto_Servico_Componente; QTD_COMP = Quantidade_Padrao ÷ Quantidade_Base_Receita) | PERDA (perda/quebra normal percentual; só existe Percentual_Tolerancia_Ajuste, que é outro conceito). Registro revogado; não exigir. |
| 0220 | Fatores de conversão de unidades | PARCIAL | `Cad_Produto_Servico_Conversao_Unidade` (UNID_CONV = ID_Unidade_Origem; FAT_CONV = Fator, com vigência) | COD_BARRA da unidade convertida (OC). Só existe Gtin_Tributavel, que cobre uma única unidade; a conversão não tem GTIN próprio. |
| 0221 | Correlação entre códigos de itens comercializados | COBERTO | `Cad_Produto_Servico_Atomico` (COD_ITEM_ATOMICO = ID_Produto_Servico_Contido; QTD_CONTIDA = Quantidade_Contida) | nenhum |
| 0300 | Cadastro de bens ou componentes do ativo imobilizado | COBERTO | `Cad_Ativo_Imobilizado` (COD_IND_BEM = Codigo_Individual_Bem; IDENT_MERC = Identificacao_Bem; DESCR_ITEM = Descricao; COD_PRNC = ID_Ativo_Principal; COD_CTA = ID_Conta_Contabil), `Mov_Ciap_Bem.Numero_Parcelas` (NR_PARC) | nenhum |
| 0305 | Informação sobre a utilização do bem | COBERTO | `Cad_Ativo_Imobilizado` (COD_CCUS = ID_Dimensao_Contabil_Valor_Centro_Custo; FUNC = Funcao_Bem; VIDA_UTIL = Vida_Util_Meses, com padrão em `Cad_Ativo_Imobilizado_Classe.Vida_Util_Padrao_Meses`) | nenhum |
| 0400 | Natureza da operação/prestação | COBERTO-DERIVADO | `Natureza_Operacao` (texto) nos itens de `Mov_Nota_Fiscal_Entrada_Item` e `Mov_Nota_Fiscal_Saida_Item`; o dicionário diz que o 0400 sai dos textos distintos. COD_NAT é gerado. | nenhum |
| 0450 | Informação complementar do documento fiscal | COBERTO | `Cad_Informacao_Complementar_Fiscal` (COD_INF = Codigo, TXT = Texto) e `Mov_Nota_Fiscal_Informacao_Complementar` | nenhum |
| 0460 | Observações do lançamento fiscal | COBERTO | `Cad_Observacao_Lancamento_Fiscal` (COD_OBS = Codigo, TXT = Texto) e `Mov_Nota_Observacao_Lancamento` | nenhum |
| 0500 | Plano de contas contábeis | COBERTO | `Cad_Conta_Contabil` (DT_ALT = Vigencia_Inicio; COD_NAT_CC = Natureza, em que receita, despesa e custo mapeiam para 04; IND_CTA = Hierarquia; NIVEL deriva da árvore por ID_Conta_Pai; COD_CTA = Codigo; NOME_CTA = Descricao) | nenhum (NOME_CTA é C060; truncar na geração) |
| 0600 | Centro de custos | COBERTO | `Cad_Dimensao_Contabil` (Eh_Centro_Custo) e `Cad_Dimensao_Contabil_Valor` (COD_CCUS = Codigo; CCUS = Descricao; DT_ALT = Vigencia_Inicio) | nenhum (D6: regra dos códigos padrão 1 a 4 quando a empresa não adota centro de custos) |
| 0990 | Encerramento do bloco 0 | COBERTO-DERIVADO | contagem de linhas | nenhum |

##### Bloco B (ISS do Distrito Federal)

A habilitação do bloco por filial está em `Cad_Empresa_Modulo_Opcional` (filial, vigência, "Bloco B do DF").

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| B001 | Abertura do bloco B | COBERTO-DERIVADO | IND_DAD deriva da existência de dados; habilitação em `Cad_Empresa_Modulo_Opcional` | nenhum |
| B020 | Nota fiscal de serviço (entrada e saída) | PARCIAL | IND_OPER = origem em `Mov_Nota_Fiscal_Entrada` (aquisição) ou `Mov_Nota_Fiscal_Saida` (prestação). COD_PART, SER, NUM_DOC, DT_DOC, VL_CONT = Valor_Total, CHV_NFE = Chave_Acesso (texto, 50 posições). COD_MOD via `Cad_Modelo_Documento_Fiscal_Codigo`; COD_SIT via ID_Situacao_Documento. COD_MUN_SERV = ID_Municipio_Incidencia_Iss do item. VL_BC_ISS, VL_ISS e VL_ISNT_ISS (Valor_Desonerado) via `Mov_Apuracao_Tributo_Item` (Imposto = iss). VL_ISS_RT e VL_BC_ISS_RT via Responsabilidade_Tributaria e `Mov_Titulo_Retencao`. COD_INF_OBS via `Mov_Nota_Observacao_Lancamento`. | VL_MAT_TER (material de terceiros) e VL_SUB (subempreitada) por documento: só existem como totais em `Mov_Apuracao_Iss_Df`; nenhum campo na nota. VL_DED_BC: só há Valor_Ajuste_Bc_Issqn na DPS da NFS-e emitida (`Mov_Nfse_Dps`) e os documentos de ajuste em `Mov_Nfse_Ajuste_Bc_Documento`; nota recebida e modelos 01/03/3B/04/08 não têm campo de dedução da base. |
| B025 | Detalhamento por alíquota e item da lista (filho do B020) | COBERTO-DERIVADO | Itens com ID_Servico_Tributacao (COD_SERV = item da LC 116) e `Mov_Apuracao_Tributo_Item` (Base_Calculo_Efetiva, Aliquota_Efetiva, Valor_Tributo, Valor_Desonerado), agrupados por alíquota e item | nenhum (herda a lacuna do B020 para VL_CONT_P quando há dedução) |
| B030 | NF de serviços simplificada (3A), por faixa | COBERTO-DERIVADO | Cada nota 3A lançada em `Mov_Nota_Fiscal_Saida`/`Mov_Documento_Fiscal` com Cad_Serie_Documento_Fiscal; faixa NUM_DOC_INI/FIN e QTD_CANC derivadas por série e data; valores somados | nenhum (D7: depende de o modelo 3A estar na tabela 4.1.1 carregada e de cada nota ser lançada individualmente) |
| B035 | Detalhamento do B030 por alíquota e item | COBERTO-DERIVADO | idem B025, sobre as notas da faixa | nenhum |
| B350 | Serviços prestados por instituições financeiras (COSIF) | PARCIAL | `Cad_Conta_Contabil` (COD_CTD, CTA_ISS = Descricao); `Mov_Desif_Apuracao_Subtitulo` traz receita, base, alíquota e ISS por subtítulo e `Mov_Desif_Balancete.Codigo_Cosif` traz o COSIF (modelagem da DES-IF municipal, não do bloco B) | QTD_OCOR (quantidade de ocorrências na conta); COD_SERV (item da lista por conta); ligação direta conta contábil → CTA_COSIF no plano de contas da própria empresa; COD_INF_OBS. Só se aplica a instituição financeira com estabelecimento no DF. |
| B420 | Totalização dos serviços prestados por alíquota e item | COBERTO-DERIVADO | soma de B025 e B035 | nenhum |
| B440 | Totalização dos valores retidos | COBERTO-DERIVADO | soma do B020 por participante e IND_OPER (VL_CONT_RT, VL_BC_ISS_RT, VL_ISS_RT) | nenhum |
| B460 | Deduções do ISS | COBERTO | `Mov_Apuracao_Iss_Deducao_Df` (IND_DED = Tipo_Deducao; VL_DED = Valor_Deducao; NUM_PROC; IND_PROC = Origem_Processo; PROC = Descricao_Processo; COD_INF_OBS = ID_Observacao; IND_OBR = Obrigacao_Aplicacao) | nenhum |
| B470 | Apuração do ISS | COBERTO | `Mov_Apuracao_Iss_Df` com os 14 campos do guia (VL_CONT a VL_ISS_REC_UNI), um a um, citados pelo nome do guia | nenhum (gravado, não derivado; ver lacuna L2) |
| B500 | Apuração do ISS da sociedade uniprofissional | COBERTO | `Mov_Iss_Fixo_Apuracao` (QTD_PROF = Quantidade_Profissionais; VL_ISS = Valor_Devido); VL_REC = receita mensal somada das notas de saída | nenhum (D8: a entidade é descrita como trimestral e o B500 é mensal) |
| B510 | Uniprofissional, empregados e sócios | PARCIAL | `Cad_Empresa_Profissional_Habilitado` (profissionais habilitados, com CPF e nome pelo participante), `Cad_Empresa_Socio` (IND_SOC), `Cad_Participante_Dados_Pessoa_Fisica.ID_Grau_Instrucao` (IND_ESC por mapeamento do código eSocial) | Profissional NÃO habilitado (empregado sem habilitação, IND_PROF = 1): não há cadastro desse perfil, só dos habilitados. IND_ESC depende de uma regra de mapeamento (nível superior ou médio) que não está definida. |
| B990 | Encerramento do bloco B | COBERTO-DERIVADO | contagem de linhas | nenhum |

##### Bloco 9

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| 9001 | Abertura do bloco 9 | COBERTO-DERIVADO | sempre gerado | nenhum |
| 9900 | Registros do arquivo | COBERTO-DERIVADO | contagem por tipo de registro gerado; `Mov_Escrituracao_Arquivo` guarda o arquivo (ID_Documento_Arquivo, Hash) | nenhum |
| 9990 | Encerramento do bloco 9 | COBERTO-DERIVADO | contagem | nenhum |
| 9999 | Encerramento do arquivo digital | COBERTO-DERIVADO | contagem | nenhum |

##### Bloco G (CIAP)

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| G001 | Abertura do bloco G | COBERTO-DERIVADO | IND_MOV deriva da existência de dados | nenhum |
| G110 | ICMS, ativo permanente, CIAP | COBERTO | `Mov_Ciap_Apuracao_Periodo` (DT_INI/DT_FIN = Competencia; SALDO_IN_ICMS = Saldo_Inicial; SOM_PARC = Total_Parcelas_Apropriadas; VL_TRIB_EXP = Total_Saidas_Tributadas; VL_TOTAL = Total_Saidas; IND_PER_SAI = Indice_Participacao; ICMS_APROP = Icms_Apropriado; SOM_ICMS_OC = Total_Outros_Creditos) | nenhum |
| G125 | Movimentação de bem ou componente do ativo imobilizado | COBERTO | `Mov_Ciap_Movimentacao` (DT_MOV = Data_Movimentacao; TIPO_MOV = Tipo_Movimentacao; VL_IMOB_ICMS_OP/ST/FRT/DIF; NUM_PARC) e `Mov_Ciap_Apropriacao` (VL_PARC_PASS = Valor_Parcela); COD_IND_BEM via ID_Bem → `Mov_Ciap_Bem` → `Cad_Ativo_Imobilizado.Codigo_Individual_Bem` | nenhum (D9: conferir que a enumeração de Tipo_Movimentacao tem os 9 valores SI, IM, IA, CI, MC, BA, AT, PE, OT; o dump trunca a lista) |
| G126 | Outros créditos CIAP | COBERTO | `Mov_Ciap_Apropriacao_Outro_Periodo` (DT_INI, DT_FIM, NUM_PARC, VL_PARC_PASS, VL_TRIB_OC, VL_TOTAL, IND_PER_SAI, VL_PARC_APROP), todos com o nome do guia na descrição | nenhum |
| G130 | Identificação do documento fiscal | PARCIAL | `Mov_Ciap_Bem_Item` → `Mov_Nota_Fiscal_Entrada_Item` → `Mov_Nota_Fiscal_Entrada` (COD_PART, COD_MOD, SERIE, NUM_DOC, DT_DOC, CHV_NFE_CTE = Chave_Acesso em texto, IND_EMIT derivado) e NUM_DA = `Mov_Ciap_Bem_Item.Numero_Documento_Arrecadacao` | Documento fiscal de SAÍDA (alienação ou transferência, TIPO_MOV = AT, e outras saídas): o guia diz que o G130 identifica "entrada ou saída", com COD_PART do adquirente, mas `Mov_Ciap_Bem_Item` e `Mov_Ciap_Bem` só apontam para item de nota de entrada (e `ID_Item_Nota_Entrada` é obrigatório). Também não há onde registrar o documento de bem que entrou antes do ERP (saldo inicial SI originado de IM, IA ou MC). |
| G140 | Identificação do item do documento fiscal | COBERTO | `Mov_Ciap_Bem_Item` (QTDE = Quantidade_Aplicada; VL_ICMS_OP/ST/FRT/DIF_APLICADO) e `Mov_Nota_Fiscal_Entrada_Item` (NUM_ITEM = Numero_Item; COD_ITEM = ID_Produto_Servico; UNID = ID_Unidade_Medida) | nenhum (herda a lacuna do G130 para saídas) |
| G990 | Encerramento do bloco G | COBERTO-DERIVADO | contagem | nenhum |

##### Bloco H (inventário)

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| H001 | Abertura do bloco H | COBERTO-DERIVADO | IND_MOV deriva da existência de inventário no período (regra de fevereiro é de geração) | nenhum |
| H005 | Totais do inventário | COBERTO-DERIVADO | `Mov_Inventario` (DT_INV = Data_Hora_Inventario; MOT_INV = ID_Motivo_Inventario); VL_INV = soma de `Mov_Inventario_Item.Valor_Item` consolidada por filial, data e motivo (o inventário é por `Cad_Local_Estoque`) | nenhum |
| H010 | Inventário | PARCIAL | `Mov_Inventario_Item` (COD_ITEM = ID_Produto_Servico; QTD a partir de `Mov_Inventario_Contagem` e Quantidade_Sistema; VL_UNIT = Valor_Unitario; VL_ITEM = Valor_Item; IND_PROP = Propriedade; COD_PART = ID_Participante_Proprietario; VL_ITEM_IR = Valor_Item_Ir); UNID = unidade do produto | TXT_COMPL (OC, sem campo). COD_CTA (OC): não há conta contábil no item do inventário; só deriva do lançamento do fechamento de estoque (Motor de Regras), sem campo explícito. Ambos opcionais. |
| H020 | Informação complementar do inventário | COBERTO | `Mov_Inventario_Item_Tributacao` (CST_ICMS = ID_Cst; BC_ICMS = Base_Calculo_Icms; VL_ICMS = Valor_Icms) | nenhum |
| H030 | Informações complementares do inventário de ST | COBERTO | `Mov_Inventario_Item_Complemento_St` (VL_ICMS_OP, VL_BC_ICMS_ST, VL_ICMS_ST, VL_FCP, valores médios unitários) | nenhum |
| H990 | Encerramento do bloco H | COBERTO-DERIVADO | contagem | nenhum |

##### Mudanças do leiaute 2026 (guia 3.2.3 e 3.2.4) no escopo

1. CNPJ de N para C (0000, 0100, 0150; C115, C175 e 1320 ficam fora do escopo). Atendido: `Cad_Participante.Documento_Principal` é "código (14) --- CNPJ alfanumérico quando PJ" (revisão 41, tipo lógico CNPJ da seção 2.5), `CNPJ_Raiz` é código (8) com "caracteres", e a convenção do tipo "código" preserva zeros à esquerda e aceita letras (`Cad_Ente_Federativo_Responsavel.Cnpj_Ente`: "Texto com zeros à esquerda preservados e aceitando caracteres alfanuméricos"). O CNPJ do escritório do 0100 vem de ID_Participante_Escritorio (mesmo tipo). CPF continua numérico (N 011) e entra no mesmo campo por Tipo_Pessoa. Não verifiquei, por estar fora do escopo, a regra de dígito verificador alfanumérico.
2. Chave de documento eletrônico de N para C (B020 CHV_NFE, G130 CHV_NFE_CTE). Atendido: `Mov_Documento_Fiscal.Chave_Acesso`, `Mov_Nota_Fiscal_Entrada.Chave_Acesso` e `Mov_Nota_Fiscal_Saida.Chave_Acesso` são "código (até 50)", portanto texto; `Chave_Dfe` está explícito como "texto de 50 posições, porque a chave pode ter letras". Observação: `Mov_Inventario_Nota_Fiscal_Ajuste.Chave_Acesso` está como "código (44)" (de uso do bloco H por ajuste de inventário); 44 basta para a NF-e, mas difere dos 50 das demais.
3. IND_BENEFICIO (E111, E220, 1921, C197, C597, D197, D737) e COD_PROD do C180: fora do escopo A. Atenção: o guia (subseção 16, "Alterações no leiaute 2027") dá vigência a partir de janeiro de 2027, não 2026. Mesmo conferido por quem tiver o bloco E, a data de início é 2027.
4. Totais de E110, E210, E310, 1920: fora do escopo A; no guia 3.2.3 são só alterações de regra de validação.
5. Novos COD_SIT 09 e 10 (tabela 4.1.2): afetam C e D; o B020 aceita só [00, 02, 06, 08]. O dicionário descreve o domínio `situacao_documento_fiscal` como "regular, cancelado, denegado, inutilizado, complementar, extemporâneo e demais"; não dá para confirmar no dump que 09 e 10 estão na carga (ver D10).
6. Orientação do 0150 para DIFAL da EC 87/2015 (3.1.9 e 3.2.1): um 0150 específico com o município de entrada física. Origem existe: `Mov_Nota_Fiscal_Saida_Local` (Tipo_Local = entrega, ID_Endereco). Atende como derivado, se a geração criar o COD_PART distinto por documento.

##### Lacunas reais (o que precisaria ser desenhado)

L1. G130 de saída: ligar `Mov_Ciap_Movimentacao` (TIPO_MOV AT, BA, OT e demais com documento) a um documento fiscal de saída (`Mov_Nota_Fiscal_Saida` ou `Mov_Documento_Fiscal`), com COD_PART do adquirente; e tornar opcional `Mov_Ciap_Bem.ID_Item_Nota_Entrada` (ou prever documento legado) para bens que entraram antes do ERP (saldo inicial originado de IM, IA ou MC exige documento).
L2. B020: acrescentar, por documento de serviço, material fornecido por terceiros (VL_MAT_TER), subempreitada (VL_SUB) e dedução da base (VL_DED_BC) na nota recebida e nos modelos não NFS-e (hoje esses valores só existem como totais manuais em `Mov_Apuracao_Iss_Df`, o que contraria "o ERP só registra": o B470 não consegue ser derivado dos documentos).
L3. B510: cadastro ou marca de profissional não habilitado (empregado) da sociedade uniprofissional, e regra de mapeamento de grau de instrução para IND_ESC (superior ou médio). Hoje só há `Cad_Empresa_Profissional_Habilitado` (habilitados).
L4. B350 (só se algum estabelecimento no DF for instituição financeira): QTD_OCOR, COD_SERV por conta e vínculo conta contábil → COSIF no plano de contas da empresa.
L5. H010: TXT_COMPL (opcional) e COD_CTA (opcional; hoje só por lançamento do fechamento de estoque). Decidir se entram em `Mov_Inventario_Item` ou se COD_CTA é derivado pelo Motor de Regras.
L6. 0220: COD_BARRA por unidade convertida (opcional), hoje só `Gtin_Tributavel` do produto.
L7. 0210: obsoleto (válido até 2021); só PERDA falta. Recomendação: não desenhar.

##### Dúvidas

D1. 0000 em estabelecimento de outra UF com IE pelo Convênio 113/04 (comunicação ou energia): UF, IE e COD_MUN passam a ser os do tomador/consumidor, e COD_MUN deve ser a capital do estado. `Mov_Escrituracao_Arquivo` tem ID_Filial, mas não a UF da IE do arquivo, e `Cad_Estado` não tem o município da capital. Só importa se a Mlegate ou algum cliente cair no caso.
D2. 0005.FANTASIA é O no guia e `Nome_Fantasia` é opcional no dicionário; 0100.EMAIL e COD_MU são O e o e-mail do participante é opcional. Definir fallback (razão social) ou validação na geração.
D3. 0100.CRC (C015): `Numero_Sequencial_Crc` (até 12) é descrito como número sequencial da certidão de regularidade (ECD J930). Confirmar se é o mesmo dado que o número de inscrição no CRC do 0100, e como compor o formato com ID_Estado_Crc.
D4. `Cad_Unidade_Medida.Sigla` não declara tamanho; UNID do 0190 é C006 e deve bater com UNID do 0200, H010 e G140.
D5. 0205.DT_INI é O no guia; `Data_Inicio_Uso` é opcional. Pode derivar da vigência da versão anterior do item.
D6. 0600: quando a empresa não adota centro de custos, o guia manda informar códigos padrão (1 área operacional etc.); regra de geração, sem dado.
D7. B030/B035 (nota 3A): confirmar que o modelo 3A consta da carga de `Cad_Modelo_Documento_Fiscal` e `Cad_Modelo_Documento_Fiscal_Codigo` e que a emissão no DF seria registrada nota a nota.
D8. B500: `Mov_Iss_Fixo_Apuracao` descreve Periodo_Inicio/Fim como trimestre (regra de São Paulo); o B500 do DF é mensal. Confirmar que a entidade aceita período mensal (Periodicidade em `Cad_Empresa_Regime_Iss` já admite mensal).
D9. G125: o dump trunca a enumeração de `Mov_Ciap_Movimentacao.Tipo_Movimentacao`; conferir os 9 valores do guia. A descrição do dicionário chama MC de "mudança de classificação", e o guia define MC como "imobilização oriunda do ativo circulante" (só o rótulo difere).
D10. `situacao_documento_fiscal`: conferir se a carga tem os códigos 09 e 10 da tabela 4.1.2 (novos no guia 3.2.3) e o descontinuamento de 04 e 05 desde 2023.
D11. H005: o inventário é por `Cad_Local_Estoque`; confirmar a regra de consolidação por filial, data e motivo (um H005 por DT_INV e MOT_INV) e a origem do VL_INV (Valor_Item do inventário versus `Mov_Saldo_Estoque_Valor`).
D12. Nota sobre a extração: `guide_A.txt` perdeu campos de alguns registros (0000 campos 09, 10 e 12; 0150 campo 07; 0500 campo 05; nomes cortados em G125 e B470). Usei `/tmp/efd324.txt` para completar; os vereditos acima consideram os campos completos.


# Anexo B — Bloco C, parte 1 (C001 a C197)


Fontes: `guide_bloco_C1.txt` (extrato), `/tmp/efd324.txt` (guia completo, para os campos que o extrato perdeu) e `dict_dump.txt` (1.020 entidades). Em uma consulta ao Project "ERP" (doc 43, item P43-04) confirmei o estado de carga das tabelas 5.3, 5.6 e 5.7 do Guia.

Critérios do projeto: (1) o ERP só registra e o arquivo é gerado dos dados; (2) registros derivados (C190, C191, C001, C990) contam como COBERTO-DERIVADO quando a origem existe; (3) parâmetros com vigência, sem valor oculto.

##### 0. Contagem

| Veredito | Qtde | Registros |
|---|---|---|
| COBERTO | 7 | C100, C110, C141, C160, C172, C174, C195 |
| COBERTO-DERIVADO | 3 | C001, C190, C990 |
| PARCIAL | 22 | C101, C105, C111, C113, C114, C115, C116, C120, C130, C140, C165, C170, C173, C175, C176, C178, C180, C181, C185, C186, C191, C197 |
| AUSENTE | 4 | C112, C171, C177 (novo, a partir de 2019), C179 |
| Total | 36 | 35 registros do extrato + C990 (fora do extrato) |

O C177 antigo (selo de controle do IPI) valia só até 31/12/2018 e não entra na conta.

##### 1. Tabela por registro

Nomes de entidade abreviados: `Ent` = Mov_Nota_Fiscal_Entrada; `Ent_Item` = Mov_Nota_Fiscal_Entrada_Item; `Sai` = Mov_Nota_Fiscal_Saida; `Sai_Item` = Mov_Nota_Fiscal_Saida_Item; `Apur` = Mov_Apuracao_Tributo_Item.

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam (nomes do guia) |
|---|---|---|---|---|
| C001 | Abertura do bloco C | COBERTO-DERIVADO | IND_MOV sai da existência de notas no período (Ent, Sai). | — |
| C100 | NF 01/1B/04/55/65 | COBERTO | IND_OPER e IND_EMIT: Sai.Tipo_Operacao e a entidade de origem. COD_PART: ID_Participante_Fornecedor (Ent) e ID_Participante_Cliente (Sai). COD_MOD: ID_Modelo_Documento e Cad_Modelo_Documento_Fiscal_Codigo (Campo_Destino = COD_MOD). COD_SIT: ID_Situacao_Documento (tabela 4.1.2). SER, NUM_DOC, CHV_NFE: Serie, Numero, Chave_Acesso (texto de até 50). DT_DOC e DT_E_S: Data_Emissao e Data_Entrada (Ent), Data_Hora_Saida_Entrada (Sai). VL_DOC: Valor_Total "tal como emitido". IND_PGTO: Ent.Indicador_Pagamento e Sai_Pagamento.Indicador_Prazo. VL_ABAT_NT: Valor_Abatimento_Nao_Tributado. IND_FRT: ID_Modalidade_Frete. VL_FRT: Sai.Valor_Frete e soma de Valor_Frete_Item. VL_DESC, VL_SEG, VL_OUT_DA, VL_MERC: soma dos campos _Item. Totais de ICMS, ST, IPI, PIS, COFINS, PIS_ST, COFINS_ST: soma de Apur por item. | Nada falta como campo. Ressalvas na seção 3 (carga de COD_SIT 09 e 10, Finalidade da entrada sem "credito", domínio de modalidade_frete). |
| C101 | Inf. complementar EC 87/15 (DIFAL/FCP) | PARCIAL | Apur.ID_Estado_Destino ("UF de destino do DIFAL e do FCP de destino"); apuração periódica em Mov_Apuracao_Icms_Difal (E300/E310). | VL_FCP_UF_DEST, VL_ICMS_UF_DEST, VL_ICMS_UF_REM: não há campo por item para a partilha (vICMSUFDest, vICMSUFRemet, vFCPUFDest) nem um discriminador de "linha DIFAL" ou "linha FCP" em Apur. Cad_Imposto não lista FCP. |
| C105 | ICMS ST recolhido para UF diversa | PARCIAL | OPER=0 e UF: Ent_Item e Sai_Item.ID_Estado_Consumo_Combustivel (comb/UFCons, exceção 8 do guia). OPER=2: UF do local de retirada (Sai_Local, Tipo_Local = retirada, via ID_Endereco). | UF no caso OPER=1 (leasing ou faturamento direto): falta UFST. Só existe Apur.Percentual_Base_Operacao_Propria (pBCOp) e ID_Estado_Devedor (descrito só para CT-e). |
| C110 | Informação complementar | COBERTO | Mov_Nota_Fiscal_Informacao_Complementar (COD_INF via Cad_Informacao_Complementar_Fiscal, Texto_Complementar = TXT_COMPL). Texto livre em Informacoes_Complementares e Informacoes_Fisco. | — |
| C111 | Processo referenciado | PARCIAL | Mov_Apuracao_Processo_Referenciado liga Cad_Processo ao item de apuração (Origem_Tipo = apuracao_tributo_item) e traz o NUM_PROC. Cad_Processo.ID_Origem_Processo_Efd traz o IND_PROC. | Vínculo nota (C110) com processo ou ato concessório citado na infCpl. Cad_Processo é cadastro jurídico e não comporta "ato concessório" nem processo SEFAZ. IND_PROC 0, 2 e 3 (SEFAZ, Justiça Estadual, SECEX/SRF): o domínio origem_processo_efd foi desenhado para a EFD-Contribuições. |
| C112 | Documento de arrecadação referenciado | AUSENTE | Nada ligado à nota. Existem só NUM_DA em ajustes de apuração (E111/G130) e guias GARE/GNRE no módulo de obrigações. | COD_DA, UF, NUM_DA, COD_AUT, VL_DA, DT_VCTO, DT_PGTO. |
| C113 | Documento fiscal referenciado | PARCIAL | Mov_Nota_Fiscal_Saida_Referenciada e Mov_Nota_Fiscal_Entrada_Referenciada: Tipo_Referencia, Chave_Referenciada (texto), ID_Documento_Fiscal_Referenciado. Com a chave, derivam-se CNPJ do emitente, modelo, série e número. | SER, SUB e NUM_DOC nos modelos 01/1B/04 (a descrição diz "se identificam por outros campos", mas a entidade não os tem). DT_DOC (a chave só traz AAMM) quando o documento não está no ERP. COD_PART quando o emitente não é participante cadastrado. IND_EMIT e IND_OPER do referenciado. |
| C114 | Cupom fiscal referenciado | PARCIAL | Tipo_Referencia "cupom_fiscal" na Referenciada; Cad_Equipamento_Fiscal (Numero_Serie_Fabricacao = ECF_FAB, Numero_Caixa = ECF_CX). | Vínculo da nota com o equipamento (ID_Equipamento_Fiscal), NUM_DOC (COO) e DT_DOC na entidade Referenciada. |
| C115 | Local de coleta e/ou entrega | PARCIAL | Mov_Nota_Fiscal_Saida_Local (Tipo_Local retirada ou entrega; ID_Participante dá CNPJ ou CPF, texto de 14; ID_Endereco dá o município IBGE; IE em Cad_Participante_Inscricao). Só saída, como o guia pede. | IND_CARGA (0 rodoviário, 1 ferroviário, 2 rodo-ferroviário, 3 aquaviário, 4 dutoviário, 5 aéreo, 9 outros). "Modal" existe só em CT-e e MDF-e. ID_Modalidade_Frete é responsabilidade do frete, não modal. |
| C116 | CF-e referenciado | PARCIAL | Chave_Referenciada (texto). NR_SAT e NUM_CFE derivam da chave. Cad_Equipamento_Fiscal (SAT: Numero_Serie_Fabricacao de 9 dígitos). | DT_DOC (a chave não traz o dia). Não se vê, no dump, valor de Tipo_Referencia para CF-e (o enumerado está truncado no dump). |
| C120 | Complemento — importação | PARCIAL | Sai_Item_Importacao (Tipo_Declaracao di, dsi ou duimp = COD_DOC_IMP; Numero_Declaracao de até 15 = NUM_DOC_IMP) e Sai_Item_Importacao_Adicao.Numero_Drawback (NUM_ACDRAW). PIS_IMP e COFINS_IMP: Apur (pis e cofins) e Mov_Duimp_Item_Tributo. Cobre a nota de entrada própria (IND_EMIT = 0). | Nota de entrada de terceiro com DI na nota (importação por conta e ordem ou por encomenda, recebida): as FK de Sai_Item_Importacao apontam só para Sai_Item, e Ent_Item não tem grupo DI. |
| C130 | ISSQN, IRRF e previdência | PARCIAL | VL_BC_ISSQN e VL_ISSQN: Apur com ID_Imposto = iss. IRRF e INSS: Mov_Titulo_Retencao (Base_Calculo, Valor_Retido, ID_Tipo_Retencao irrf ou inss). | VL_SERV_NT (só existe em Mov_Nota_Fiscal_Utilidade, que é de energia, água, gás e comunicação). VL_BC_IRRF, VL_IRRF, VL_BC_PREV, VL_PREV como dado destacado na nota: o ERP guarda a retenção na baixa do título, não o destaque do documento. |
| C140 | Fatura | PARCIAL | QTD_PARC e VL_TIT: Mov_Titulo (Origem_Tipo = nota; Numero_Parcela, Valor_Titulo). IND_EMIT: derivado da nota. Mov_Nota_Fiscal_Entrada_Fatura é da NFCom/NFAg e não substitui. | IND_TIT (00 duplicata, 01 cheque, 02 promissória, 03 recibo, 99 outros), NUM_TIT, DESC_TIT. O único tipo de título é ID_Tipo_Documento_Cobranca (CNAB, só em cobrança). |
| C141 | Vencimento da fatura | COBERTO | Mov_Titulo (Numero_Parcela, Data_Vencimento, Valor_Titulo). | — (ver dúvida sobre nota à vista sem título) |
| C160 | Volumes transportados | COBERTO | COD_PART: ID_Participante_Transportadora. VEIC_ID e UF_ID: Mov_Nota_Fiscal_Saida_Transporte_Veiculo (Placa, ID_Estado_Placa) e Cad_Veiculo_Transporte. QTD_VOL, PESO_BRT, PESO_LIQ: Mov_Nota_Fiscal_Saida_Volume. | — |
| C165 | Operações com combustíveis | PARCIAL | COD_PART, VEIC_ID e UF_ID: como no C160. COD_AUT: Combustivel_Codigo_Codif (CODIF). HORA: Data_Hora_Saida_Entrada. QTD_VOL, PESO_BRT, PESO_LIQ: Sai_Volume. | NR_PASSE, TEMPER (só existe qTemp, a quantidade à temperatura ambiente), NOM_MOT, CPF do motorista. |
| C170 | Itens do documento | PARCIAL | NUM_ITEM, COD_ITEM, DESCR_COMPL, QTD, UNID, VL_ITEM, VL_DESC: Numero_Item, ID_Produto_Servico, Descricao_Produto_Servico, Quantidade, ID_Unidade_Medida, Valor_Total, Valor_Desconto_Item. IND_MOV: Cad_CFOP.Indicador_Sem_Movimentacao_Fisica. CST_ICMS: ID_Origem_Mercadoria mais Apur.ID_Cst. CFOP: ID_CFOP_Entrada e ID_CFOP_Saida. COD_NAT: Natureza_Operacao. Bases, alíquotas e valores de ICMS, ST, IPI, PIS e COFINS: Apur (Base_Calculo_Efetiva, Aliquota_Efetiva, Valor_Tributo, Base_Calculo_St, Valor_St_Retido; quantidade e valor por unidade em Quantidade_Tributada e Valor_Especifico_Unidade). COD_ENQ: ID_Enquadramento_Ipi. IND_APUR: Mov_Apuracao_Ipi.Tipo_Periodo. COD_CTA: ID_Conta_Contabil. | VL_ABAT_NT por item (campo 38): o dicionário só tem o total no cabeçalho, e o guia exige que C100 = soma dos C170. ALIQ_ST (campo 17): sem campo (nenhuma "Aliquota_St"). |
| C171 | Armazenamento de combustíveis | AUSENTE | Só Combustivel_Numero_Tanque nos itens, que é o tanque do bico no grupo encerrante (comb/encerrante/nTanque) da NF-e de venda. Não há entidade de tanque nem de recebimento por tanque; "LMC" não aparece no dicionário. | NUM_TANQUE (tanque onde foi armazenado) e QTDE por tanque (relação 1:N). |
| C172 | Operações com ISSQN | COBERTO | Apur com ID_Imposto = iss (base, Aliquota_Efetiva, Valor_Tributo) e ID_Servico_Tributacao ou Codigo_Servico_Municipal no item. | — |
| C173 | Operações com medicamentos | PARCIAL | LOTE_MED, QTD_ITEM, DT_FAB, DT_VAL: Sai_Item_Lote e Cad_Lote_Produto (Numero_Lote, Data_Fabricacao, Data_Validade). VL_TAB_MAX: Medicamento_Preco_Maximo_Consumidor (vPMC). | IND_MED (tipo de referência da base do ICMS ST) e TP_PROD (similar, genérico, ético). Lote por item na entrada: Ent_Item não tem lote (só Mov_Estoque_Movimento_Item.ID_Lote). |
| C174 | Operações com armas de fogo | COBERTO | Arma_Tipo = IND_ARM, Arma_Numero_Serie = NUM_ARM, Arma_Descricao = DESCR_COMPL (Ent_Item e Sai_Item). | — |
| C175 | Operações com veículos novos | PARCIAL | IND_VEIC_OPER: Veiculo_Tipo_Operacao. CHASSI_VEIC: Veiculo_Chassi (texto de 17). | CNPJ e UF da concessionária. O CNPJ é obrigatório com IND_VEIC_OPER = 1, e não há campo. O domínio é o da NF-e (tpOp), sem a distinção de "venda para a concessionária" (0) e "venda da concessionária" (3). |
| C176 | Ressarcimento de ICMS e FCP em ST | PARCIAL | Mov_Icms_St_Ressarcimento. COD_MOD_ULT_E, NUM_DOC_ULT_E, SER_ULT_E, DT_ULT_E, COD_PART_ULT_E, CHAVE_NFE_ULT_E, NUM_ITEM_ULT_E: via ID_Item_Entrada_Origem. QUANT_ULT_E: Quantidade_Ressarcida. VL_UNIT_BC_ST: Base_St_Unitaria. VL_UNIT_ICMS_ULT_E: Icms_St_Unitario ou Icms_Proprio_Unitario. VL_UNIT_RES: Valor_Ressarcimento dividido pela quantidade. COD_MOT_RES: ID_Motivo_Ressarcimento. VL_UNIT_RES_FCP_ST: Fcp_St_Unitario (é o FCP retido, não o ressarcimento; nome divergente). VL_UNIT_ULT_E: derivável de Ent_Item. | VL_UNIT_BC_ICMS_ULT_E (12). ALIQ_ICMS_ULT_E (13). VL_UNIT_LIMITE_BC_ICMS_ULT_E (14, derivado: o menor entre o 09 e o 12). ALIQ_ST_ULT_E (16). COD_RESP_RET (18). CHAVE_NFE_RET, COD_PART_NFE_RET, SER_NFE_RET, NUM_NFE_RET, ITEM_NFE_RET (20 a 24). COD_DA e NUM_DA (25 e 26). A entidade usa "VL_UNIT_ICMS_NF_ULT_E", do leiaute anterior. |
| C177 | Complemento do item (novo, desde 01/01/2019) | AUSENTE | Só Item_Observacao (obsCont e obsFisco, xCampo e xTexto da NF-e), que não é a tabela 5.6. | COD_INF_ITEM (código da tabela 5.6 publicada pela UF). O C177 antigo (selo IPI) está encerrado. |
| C178 | IPI por unidade ou quantidade | PARCIAL | VL_UNID: Apur.Valor_Especifico_Unidade. QUANT_PAD: Apur.Quantidade_Tributada (Forma_Tributacao = especifica_por_unidade). | CL_ENQ (classe de enquadramento, tabela 4.5.1, 5 posições). ID_Enquadramento_Ipi é o cEnq de 3 dígitos, que é outra coisa. |
| C179 | Informações complementares ST | AUSENTE | Só Base_Calculo_St e Valor_St_Retido, da operação própria. | BC_ST_ORIG_DEST, ICMS_ST_REP, ICMS_ST_COMPL, BC_RET, ICMS_RET (repasse, dedução, complemento e substituído intermediário). |
| C180 | Complemento — entrada de mercadoria sujeita à ST | PARCIAL | QUANT_CONV e UNID: Quantidade com Cad_Produto_Servico_Conversao_Unidade. VL_UNIT_CONV: derivado de Ent_Item. VL_UNIT_BC_ICMS_ST_CONV e VL_UNIT_ICMS_ST_CONV: derivados de Apur.Base_Calculo_St e Valor_St_Retido (retidos anteriormente) por unidade. | COD_RESP_RET. VL_UNIT_ICMS_OP_CONV (ICMS que teria no regime comum: só existe em Mov_Icms_St_Ressarcimento, e só após uma saída). VL_UNIT_FCP_ST_CONV (sem FCP por item). COD_DA e NUM_DA. COD_PROD (novo, cProd do fornecedor): Ent_Item não tem o código do produto do fornecedor. |
| C181 | Complemento — devolução de saída sujeita à ST | PARCIAL | Identificação da saída: Mov_Devolucao_Venda_Item.ID_Nota_Item para Sai_Item e nota (COD_MOD_SAIDA, SERIE_SAIDA, NUM_DOC_SAIDA, CHV_DFE_SAIDA, DT_DOC_SAIDA, NUM_ITEM_SAIDA); ECF_FAB_SAIDA via Cad_Equipamento_Fiscal. QUANT_CONV e UNID. VL_UNIT_CONV_SAIDA: derivável. Chaves em texto (até 50). | COD_MOT_REST_COMPL (tabela 5.7; ver seção 3). Núcleo calculado sem entidade: VL_UNIT_ICMS_OP_ESTOQUE_CONV_SAIDA, VL_UNIT_ICMS_ST_ESTOQUE_CONV_SAIDA, VL_UNIT_FCP_ICMS_ST_ESTOQUE_CONV_SAIDA, VL_UNIT_ICMS_NA_OPERACAO_CONV_SAIDA, VL_UNIT_ICMS_OP_CONV_SAIDA, valores de restituição e de complemento. |
| C185 | Complemento — saída de mercadoria sujeita à ST | PARCIAL | NUM_ITEM, COD_ITEM, CST_ICMS, CFOP, QUANT_CONV, UNID, VL_UNIT_CONV: Sai_Item e Apur. | COD_MOT_REST_COMPL (tabela 5.7). Todo o bloco calculado dos campos 10 a 18: VL_UNIT_ICMS_NA_OPERACAO_CONV, VL_UNIT_ICMS_OP_CONV, VL_UNIT_ICMS_OP_ESTOQUE_CONV, VL_UNIT_ICMS_ST_ESTOQUE_CONV, VL_UNIT_FCP_ICMS_ST_ESTOQUE_CONV, VL_UNIT_ICMS_ST_CONV_REST, VL_UNIT_FCP_ST_CONV_REST, VL_UNIT_ICMS_ST_CONV_COMPL, VL_UNIT_FCP_ST_CONV_COMPL. Os valores médios de estoque só existem em Mov_Inventario_Item_Complemento_St (H020, inventário com motivo 06). |
| C186 | Complemento — devolução de entrada sujeita à ST | PARCIAL | Identificação da entrada: Mov_Devolucao_Compra_Item.ID_Nota_Item para Ent_Item e nota (COD_MOD_ENTRADA, SERIE_ENTRADA, NUM_DOC_ENTRADA, CHV_DFE_ENTRADA, DT_DOC_ENTRADA, NUM_ITEM_ENTRADA). NUM_ITEM, COD_ITEM, CST_ICMS, CFOP, QUANT_CONV, UNID. | COD_MOT_REST_COMPL (tabela 5.7). VL_UNIT_CONV_ENTRADA, VL_UNIT_ICMS_OP_CONV_ENTRADA, VL_UNIT_BC_ICMS_ST_CONV_ENTRADA, VL_UNIT_ICMS_ST_CONV_ENTRADA, VL_UNIT_FCP_ST_CONV_ENTRADA (os valores que o C180 teria na entrada; não estão guardados). |
| C190 | Analítico do documento | COBERTO-DERIVADO | Agrupamento de Apur por CST, CFOP e Aliquota_Efetiva. VL_OPR: Valor_Total, ou Valor_Total_Liquido a partir de 2027 (sem IBS, CBS e IS), mais rateios e menos desconto. VL_BC_ICMS, VL_ICMS, VL_BC_ICMS_ST, VL_ICMS_ST, VL_IPI: Apur. VL_RED_BC: Base_Calculo_Bruta menos Base_Calculo_Efetiva (Mecanismo_Reducao = reducao_base_calculo). COD_OBS: Mov_Nota_Observacao_Lancamento. | — (ver dúvidas sobre VL_OPR e COD_OBS por combinação) |
| C191 | FCP na NF-e e NFC-e | PARCIAL | Existe só o fechamento periódico em Mov_Apuracao_Icms_Difal (Fcp_*, E310) e Fcp_St_Unitario no ressarcimento. Apur tem a estrutura (base, alíquota, valor, Responsabilidade_Tributaria), mas não declara FCP. | VL_FCP_OP, VL_FCP_ST, VL_FCP_RET por item (vBCFCP, pFCP, vFCP, vFCPST, vFCPSTRet). Cad_Imposto não traz FCP. |
| C195 | Observações do lançamento | COBERTO | Mov_Nota_Observacao_Lancamento (COD_OBS via Cad_Observacao_Lancamento_Fiscal, Texto_Complementar = TXT_COMPL). | — |
| C197 | Outras obrigações e ajustes do documento | PARCIAL | Mov_Nota_Ajuste_Documento: COD_AJ (Cad_Icms_Codigo_Ajuste, Tabela_Origem = documento_5_3), DESCR_COMPL_AJ, COD_ITEM, VL_BC_ICMS, ALIQ_ICMS, VL_ICMS, VL_OUTROS, ID_Subapuracao. | IND_BENEFICIO (campo 09, novo; 0, 1, 2, 3 ou 9; obrigatório quando o 3º dígito do COD_AJ for diferente de 9). Não aparece em Mov_Nota_Ajuste_Documento nem em Cad_Icms_Codigo_Ajuste. |
| C990 | Encerramento do bloco C | COBERTO-DERIVADO | Contagem de linhas do arquivo gerado (não está em `guide_bloco_C1.txt`). | — |

##### 2. Verificações pedidas

- **C100, COD_SIT 09 e 10 e exceção 12.** Ent.ID_Situacao_Documento e Sai.ID_Situacao_Documento apontam para a tabela 4.1.2 em Cad_Classe_Sistema. A descrição lista "regular, cancelado, denegado, inutilizado, complementar, extemporâneo e demais". Os valores 09 (emitido com redução de valores ou quantidades) e 10 (a extemporânea dele) dependem da carga do domínio, que o dump não mostra. Ent e Sai têm ID_Tipo_Nota_Credito (tpNFCredito). Mas Ent.Finalidade é {normal, complementar, ajuste, devolucao, substituicao}, sem crédito ou débito, enquanto Sai.Finalidade tem. A exceção 12 inverte o IND_OPER (nota de crédito de terceiro vai como saída; a própria, como entrada), o que é regra do gerador, não campo.
- **VL_DOC com IBS/CBS.** Cobre: Valor_Total é "tal como emitido". Para VL_OPR do C190, Sai_Item e Ent_Item têm Valor_Total_Liquido (vProdLiq, sem IBS, CBS e IS). Em 2026 o guia manda não somar IBS, CBS e IS no VL_DOC.
- **C197.IND_BENEFICIO.** AUSENTE no dicionário.
- **C180.COD_PROD.** AUSENTE: Ent_Item não guarda o cProd do fornecedor.
- **CNPJ e chave como texto.** OK onde há campo. Chave_Acesso (50), Chave_Referenciada (50), Chave_Acesso_Referenciada (44), Chave_Acesso_Devolucao (44) e Mov_Documento_Fiscal.Chave_Acesso (50) são código/texto. Documento_Principal (14) é "CNPJ alfanumérico". Numero_Declaracao (15) e Veiculo_Chassi (17) são texto. Não há campo para o CNPJ do C175, e os campos de CHV_DFE de C181 e C186 dependem de entidades que não existem para os valores.
- **C176, C180 a C186.** Ver a tabela. O dicionário modela o ressarcimento no leiaute antigo do C176 (por par saída e última entrada) mais o consolidado do 1255. O modelo "valor unitário médio de estoque" dos C180 a C186 só aparece no H020.
- **C101, C105, C111 a C114.** Ver a tabela.
- **C120, C130, C140, C141, C160, C165, C171 a C179.** Ver a tabela.

##### 3. Lacunas reais (ordem de gravidade)

1. **ICMS ST e FCP por item (alimenta C101, C170, C176, C180 a C186, C191).** Faltam ALIQ_ST (pICMSST), FCP próprio, FCP ST e FCP retido por item, e a partilha DIFAL por item (vICMSUFDest, vICMSUFRemet, vFCPUFDest). Sugestão: declarar FCP em Cad_Imposto e separar a linha DIFAL em Apur.
2. **Núcleo de ressarcimento e complemento de ST (C180, C181, C185, C186).** Os valores unitários por movimento e de estoque médio não têm entidade. COD_RESP_RET, COD_DA e NUM_DA faltam também no C176. O C176 não guarda a NF-e da retenção (CHAVE_NFE_RET e correlatos) e a base e alíquota do ICMS próprio da última entrada (campos 12, 13, 14, 16).
3. **C197.IND_BENEFICIO** (campo 09 novo), a ser guardado no ajuste do documento ou em Cad_Icms_Codigo_Ajuste.
4. **C180.COD_PROD** (campo 12 novo): código do produto no fornecedor (cProd) no item da entrada.
5. **C112** (documento de arrecadação referenciado): sem entidade.
6. **C171** (tanque de recebimento de combustível) e **C165** (NR_PASSE, TEMPER, NOM_MOT, CPF do motorista).
7. **C179** (repasse, dedução e complemento de ST): sem campos.
8. **Referências de documento (C113, C114, C116):** a entidade Referenciada só tem a chave. Faltam SER, SUB, NUM_DOC, DT_DOC, COD_PART, equipamento e COO para as referências a documentos fora do ERP.
9. **C115.IND_CARGA** (modal de transporte da nota).
10. **C140.IND_TIT e NUM_TIT.**
11. **C130:** VL_SERV_NT e os destaques de IRRF e previdência na nota.
12. **C173:** IND_MED e TP_PROD. **C175:** CNPJ e UF da concessionária. **C178:** CL_ENQ. **C105:** UFST do leasing. **C170:** VL_ABAT_NT por item. **C111:** vínculo nota com processo e ato concessório. **C120:** DI na nota de entrada de terceiro.
13. **C177 novo** (COD_INF_ITEM, tabela 5.6).

##### 4. Dúvidas

- **Cargas pendentes.** O doc 43 do Project (P43-04) registra que as tabelas 5.2, 5.3, 4.5.4, 5.6, 5.7, 5.8 e 5.9.1 ainda não foram carregadas. Isso atinge COD_AJ do C197 (5.3), COD_INF_ITEM do C177 (5.6) e COD_MOT_REST_COMPL dos C181, C185 e C186 (5.7). As tabelas 4.5.1 e 4.5.2 (CL_ENQ do C178 e selo) também não aparecem na carga citada.
- **Tabela 5.7 e o motivo de ressarcimento.** O domínio motivo_ressarcimento_icms_st é descrito com os motivos do C176 (saída para outra UF, isenção, perda, furto, exportação, Simples e outros) e usado também como COD_MOT_REST_COMPET do 1255. Esse campo segue a tabela 5.7 (5 posições, publicada pela UF). Os dois domínios são o mesmo? Se não, falta um domínio para a 5.7.
- **Modalidade de frete.** A descrição de modalidade_frete lista emitente, destinatário, terceiros e sem frete. O guia (a partir de 2018) aceita também 3 e 4 (transporte próprio do remetente e do destinatário).
- **Finalidade da entrada.** Ent.Finalidade tem ID_Tipo_Nota_Credito mas o enumerado não tem "credito" nem "debito". Falta registrar a finalidade 5 e 6 no recebimento, e a regra do IND_OPER da exceção 12 não está escrita.
- **Notas só com IBS, CBS e IS.** O guia manda não escriturar documentos que tragam só os novos tributos. A regra do gerador (ICMS ou IPI no item) deriva de Apur, mas não vi decisão registrada.
- **COD_SIT 08 em 2026** para documentos emitidos com redução (Ajuste SINIEF 49/2025): regra do gerador a confirmar.
- **C190.COD_OBS e C195.** Mov_Nota_Observacao_Lancamento liga a observação à nota, não a uma combinação CST, CFOP e alíquota. Como o COD_OBS do C190 é escolhido quando há mais de uma observação?
- **C141 em nota à vista.** O guia diz que o C140 deve refletir a parcela paga no ato. Mov_Titulo nasce em nota à vista?
- **C170.IND_APUR.** Hoje o período do IPI (mensal ou decendial) só aparece em Mov_Apuracao_Ipi.Tipo_Periodo, que é a apuração, não um parâmetro do estabelecimento (Cad_Filial_Perfil_Fiscal só tem Contribuinte_Ipi).
- **C175.IND_VEIC_OPER.** O domínio do dicionário (tpOp da NF-e) não separa 0 (venda para concessionária) e 3 (venda da concessionária). Mapeamento por papel do emitente?
- **C111.** IND_PROC no C111 tem 0 a 3 e 9, e origem_processo_efd foi desenhado para a EFD-Contribuições.
- **Guia, inconsistência interna.** No C176, o COD_RESP_RET lista 4 valores na tabela do campo, mas a validação diz [1, 2, 3].
- **VL_OPR.** Confirmar se o gerador usa Valor_Total_Liquido (opcional na nota) em 2027 em diante.
- **Divergência com o Project.** O doc 32 do Project classifica "EFD ICMS/IPI, Bloco C" como "Coberto". Este levantamento, campo a campo, aponta lacunas.

##### 5. Observações sobre as fontes

- O extrato `guide_bloco_C1.txt` perdeu campos: C112 (UF), C115 (CPF_COL), C165 (COD_PART, PESO_BRT, PESO_LIQ), C175 (UF), C180 (VL_UNIT_BC_ICMS_ST_CONV), toda a lista do C191 (VL_FCP_OP, VL_FCP_ST, VL_FCP_RET) e as descrições completas de C180 a C186 (nomes de campo cortados). Usei `/tmp/efd324.txt` para completar. O extrato traz só o C177 antigo (selo IPI, até 2018). O C177 vigente (COD_INF_ITEM) está só em `/tmp/efd324.txt`.
- `dict_dump.txt` corta a coluna de tipo em cerca de 80 caracteres e a de descrição em cerca de 200. Os enumerados longos aparecem truncados (por exemplo Tipo_Referencia, Tipo_Complemento, Responsabilidade_Tributaria e Origem_Tipo). Onde o veredito dependia do enumerado inteiro, marquei como dúvida.


# Anexo C — Bloco C, parte 2 (C300 a C897)


Fontes lidas: `guide_bloco_C2.txt`, trechos de `/tmp/efd324.txt` (C500 a C597 completos, C600, C800 a C897, Tabela 4.1.1, Tabela 4.4.6, lista de mudanças da v3.2.4), `dict_dump.txt` (entidades citadas abaixo) e, como contexto, os documentos 37, 43 e 10 do Project ERP (via busca).

Observações de método:
- O `guide_bloco_C2.txt` perdeu alguns campos na extração (C500 campos 26, 28 a 33; C591 campo 01 etc.). Usei o texto completo de `/tmp/efd324.txt` para esses.
- O dump do dicionário corta a coluna de tipo/enumeração em ~80 caracteres e as descrições em ~300. Onde isso impede ver uma lista de valores, está dito em "Dúvidas".
- As citações "C481/C485/C490/C491/C495" em `Mov_Ecf_Reducao_Z_Tributo` são da EFD-Contribuições (PIS/Cofins por item e CST). Não cobrem o C490/C495 da EFD-ICMS/IPI (CST/CFOP/alíquota de ICMS).
- Contexto do Project (doc 43, tabela tb131): a tabela de totalizadores parciais da Redução Z (Tabela 4.4.6) NÃO foi carregada, por decisão registrada ("legado, reavaliar se o desenho passar a gerar C300 a C495"). O doc 37 (sobre o Guia 3.2.2) lista C300–C495, C500/C510/C590 e C800–C890 como lacunas. Depois vieram o D-N93 (equipamento fiscal e Redução Z) e a revisão 29 (doc 165: entrada de NFGás e NF3e). Esta conferência mede o estado atual do dicionário.
- Perfil do emitente: `Cad_Modelo_Documento_Fiscal.Possui_Motor_Emissao` cita só 55, 65, 57, 58, 62 e NFS-e. Logo, "saída" de modelos 06/28/29/66/76 e a consolidação C600–C791 (feita por concessionária) só fazem sentido se a Mlegate tiver esse perfil. Marquei esses itens como "condicional".

##### 1. Mapa de origem (entidades do dicionário que sustentam o bloco)

| Assunto | Entidade / campo |
|---|---|
| Documento (entrada) | `Mov_Nota_Fiscal_Entrada` (Numero, Serie, Subserie, Chave_Acesso 50, Data_Emissao, Data_Entrada, Valor_Total, ID_Modelo_Documento, ID_Situacao_Documento, Finalidade, Status); itens em `Mov_Nota_Fiscal_Entrada_Item` |
| Documento (saída) | `Mov_Nota_Fiscal_Saida` (idem + Documento_Consumidor, Nome_Consumidor, Subserie, `ID_Equipamento_Fiscal`); itens em `Mov_Nota_Fiscal_Saida_Item` (Numero_Item, Valor_Desconto_Item, Valor_Outras_Despesas_Item, ID_Classificacao_Item_Utilidade, ID_Conta_Contabil) |
| ICMS por item (CST, base, alíquota, valor, ST, redução) | `Mov_Apuracao_Tributo_Item` (ID_Imposto=ICMS; Base_Calculo_Bruta/Efetiva, Aliquota_Efetiva, Valor_Tributo, Base_Calculo_St, Valor_St_Retido, Valor_Desonerado, Gera_Credito); CST sem origem + `ID_Origem_Mercadoria` do item = CST de 3 dígitos |
| Energia/água/gás (cabeçalho EFD) | `Mov_Nota_Fiscal_Utilidade` (faixa/classe de consumo, município, consumo, Valor_Fornecimento, Valor_Servico_Nao_Tributado_Icms, Valor_Cobrado_Terceiros, Valor_Despesas_Acessorias, Tipo_Ligacao, Grupo_Tensao) |
| Extensão NF3e / NFGás | `Mov_Nf3e_Entrada*` e `Mov_Nfgas_Entrada*` (só entrada), `Cad_Ponto_Servico_Utilidade`, `Mov_Nota_Fiscal_Entrada_Referenciada` |
| Observação / ajuste por documento | `Cad_Observacao_Lancamento_Fiscal` (0460), `Mov_Nota_Observacao_Lancamento` (C195/C595/C855/C895), `Mov_Nota_Ajuste_Documento` (C197/C597/C857/C897), `Cad_Icms_Codigo_Ajuste` (tabela 5.3) |
| Informação complementar | `Mov_Nota_Fiscal_Informacao_Complementar` (COD_INF) |
| ECF e SAT | `Cad_Equipamento_Fiscal` (C400, C860), `Mov_Ecf_Reducao_Z` (C405), `Mov_Ecf_Reducao_Z_Tributo` (só PIS/Cofins) |
| Ressarcimento de ST (parcial) | `Mov_Icms_St_Ressarcimento` (campos de C176) |

##### 2. Cobertura registro a registro

Legenda: COBERTO / COBERTO-DERIVADO / PARCIAL / AUSENTE. "(cond.)" = vale se a Mlegate lançar documentos desse tipo.

###### 2.1 NF venda a consumidor, modelo 02 (C300–C390)

| Registro | Nome | Veredito | Onde está no dicionário | Campos que faltam |
|---|---|---|---|---|
| C300 | Resumo diário NF venda a consumidor | COBERTO-DERIVADO (cond.) | `Mov_Nota_Fiscal_Saida` modelo 02: Serie, Subserie, Numero (INI/FIN), Data_Emissao, Valor_Total; PIS/Cofins em `Mov_Apuracao_Tributo_Item`; COD_CTA no item | Nenhum de dado. Não está dito que o modelo 02 entra como nota de saída (o doc 43 chama de "legado") |
| C310 | Documentos cancelados | COBERTO-DERIVADO (cond.) | Notas com Status=cancelada / ID_Situacao_Documento | — |
| C320 | Analítico do resumo diário | COBERTO-DERIVADO (cond.) | Agrupa `Mov_Apuracao_Tributo_Item` (ICMS) por CST, CFOP (ID_CFOP_Saida) e Aliquota_Efetiva; VL_RED_BC = Base_Calculo_Bruta − Base_Calculo_Efetiva | COD_OBS por combinação (ver Dúvidas) |
| C321 | Itens do resumo diário | COBERTO-DERIVADO (cond.) | Itens de saída: Codigo_Item do produto, Quantidade, unidade, Valor_Total, Valor_Desconto_Item, base/ICMS/PIS/Cofins | — |
| C330 | ST (restituição/complemento), mod. 02 | PARCIAL | `Mov_Icms_St_Ressarcimento` (só campos do C176) | QUANT_CONV, VL_UNIT_CONV, VL_UNIT_ICMS_NA_OPER, VL_UNIT_ICMS_OP_CON, VL_UNIT_ICMS_OP_ESTO, VL_UNIT_ICMS_ST_ESTO, FCP ST (estoque, restituição e complemento), ICMS ST complemento. Domínio COD_MOT_REST_COMPL (tabela 5.7) não identificado |
| C350 | NF venda a consumidor | COBERTO (cond.) | Cabeçalho de saída: SER, SUB_SER (Subserie), NUM_DOC, DT_DOC, CNPJ_CPF (Documento_Consumidor), VL_DOC; VL_DESC = soma de Valor_Desconto_Item; VL_PIS/VL_COFINS por item | — |
| C370 | Itens | COBERTO (cond.) | `Mov_Nota_Fiscal_Saida_Item`: Numero_Item, produto, Quantidade, unidade, Valor_Total, Valor_Desconto_Item | — |
| C380 | ST complementar | PARCIAL | Igual ao C330 | Igual ao C330, mais CST_ICMS e CFOP do item (estes existem) |
| C390 | Analítico NF venda a consumidor | COBERTO-DERIVADO (cond.) | Igual ao C320 | COD_OBS por combinação |

###### 2.2 ECF (C400–C495)

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| C400 | Equipamento ECF | COBERTO | `Cad_Equipamento_Fiscal` (Tipo=ecf): COD_MOD via ID_Modelo_Documento, ECF_MOD = Modelo_Equipamento (20), ECF_FAB = Numero_Serie_Fabricacao (21), ECF_CX = Numero_Caixa | A descrição do campo cita modelos "02, 2D, 59 ou 65"; o 60 (CF-e-ECF), válido no C400, não é citado (basta existir na tabela de modelos) |
| C405 | Redução Z | COBERTO | `Mov_Ecf_Reducao_Z`: Data_Movimento, CRO, CRZ, Numero_Coo_Final, Grande_Total_Final, Valor_Venda_Bruta | Só o nome: o dicionário cita "GT_FINAL"; o campo do Guia é GT_FIN |
| C410 | PIS/Cofins totalizados no dia | COBERTO-DERIVADO | Soma de `Mov_Ecf_Reducao_Z_Tributo.Valor_Tributo` por imposto. Dispensado se houver EFD-Contribuições do mesmo período | — |
| C420 | Totalizadores parciais da Redução Z | **AUSENTE** | Nenhuma entidade. Tabela 4.4.6 (tb131) não carregada (doc 43). `Mov_Ecf_Reducao_Z_Tributo` é só PIS/Cofins | COD_TOT_PAR (Tnnnn, 01Tnnnn, Fn, In, Nn, Snnnn, DT, AT, Can-T, OPNF…), VLR_ACUM_TOT, NR_TOT, DESCR_NR_TOT; a tabela 4.4.6 |
| C425 | Resumo de itens do movimento diário | PARCIAL | `Mov_Ecf_Reducao_Z_Tributo`: produto (COD_ITEM), Valor_Item (VL_ITEM), Valor_Tributo (VL_PIS, VL_COFINS) | QTD e UNID do item vendido (só existe Quantidade_Base_Calculo, que é base por unidade, e opcional); vínculo ao totalizador do C420; linha única por item em vez de uma por imposto/CST |
| C430 | ST complementar (ECF) | PARCIAL | Igual ao C330 | Igual ao C330 |
| C460 | Documento fiscal emitido por ECF (cupom) | PARCIAL | Não há entidade de cupom ECF. Caberia em `Mov_Nota_Fiscal_Saida` (Numero=COO, Status/ID_Situacao_Documento=COD_SIT, Data_Emissao, Valor_Total, Documento_Consumidor/Nome_Consumidor, ID_Equipamento_Fiscal), mas o dicionário só cita essa ligação para C800/C860 | Decisão de que o cupom é nota de saída; vínculo cupom → Redução Z (C405) ou → equipamento+data; regra de cupom cancelado só com COD_MOD/COD_SIT/NUM_DOC |
| C465 | Complemento do CF-e-ECF (modelo 60) | PARCIAL | CHV_CFE = Chave_Acesso (texto até 50; 44 no arquivo) | NUM_CCF (contador de cupom fiscal) |
| C470 | Itens do cupom ECF | PARCIAL | Itens de saída: produto, Quantidade, unidade, Valor_Total, CFOP, CST e Aliquota_Efetiva do ICMS, PIS/Cofins (se o cupom for nota) | QTD_CANC (quantidade cancelada); a própria existência do cupom (C460) |
| C480 | ST complementar (ECF) | PARCIAL | Igual ao C330 | Igual ao C380 |
| C490 | Analítico do movimento diário (CST/CFOP/alíquota) | PARCIAL | Derivável do ICMS por item dos cupons, se existirem. Da Redução Z não: ela não guarda ICMS | Totais de ICMS por CST/CFOP/alíquota na Redução Z (conferência com o C420); COD_OBS |
| C495 | Resumo mensal de itens ECF | AUSENTE (sem relevância) | — | Só BA até 31/12/2013; a partir de 2014 usa-se o C425. Não é o C495 da EFD-Contribuições citado no dicionário |

###### 2.3 Energia / água / gás — documentos (C500–C597)

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| C500 | NF/Conta energia (06), NF3e (66), água (29), gás (28), NFGás (76) | **PARCIAL** | Ver tabela 3 (campo a campo) | Campo 39 ENER_INJET e campo 40 OUTRAS_DED sem campo; mapa cClass → campo EFD ausente (ver Lacunas) |
| C510 | Itens (06, 28, 29; só saída, papel) | PARCIAL (cond.) | `Mov_Nota_Fiscal_Saida_Item`: COD_CLASS = ID_Classificacao_Item_Utilidade; QTD, UNID, VL_ITEM, VL_DESC, CST, CFOP, base, alíquota, ICMS, ST, PIS, Cofins, COD_CTA. Não vale para NF3e/NFGás (eletrônicas) nem para entrada | IND_REC (0 própria / 1 terceiros) e COD_PART do receptor da receita por item. `ID_Tipo_Receita_Comunicacao` é o D600.IND_REC, outro domínio |
| C590 | Analítico do documento | COBERTO-DERIVADO | Agrupa `Mov_Apuracao_Tributo_Item` (ICMS) por CST+CFOP+alíquota. VL_OPR = valor fornecido + outras despesas − desconto incondicional, a partir dos itens. VL_RED_BC derivado. Entrada: valores só se `Gera_Credito` (enfoque do declarante) | Regras de derivação a registrar: item sem CST de ICMS fora do C590; energia injetada fora (CST 40 com zero quando a injeção gera isenção); só funcionam por grupo de cClass, cuja tabela não veio |
| C591 | FCP na NF3e e na NFGás | PARCIAL | Informativo, sem efeito no bloco E | FCP da operação própria e FCP ST por item: `Mov_Apuracao_Tributo_Item` não tem campo de FCP; só existem FCP de apuração (E310) e `Fcp_St_Unitario` (ressarcimento) |
| C595 | Observações do lançamento (06, 28, 29, 66, 76) | COBERTO | `Mov_Nota_Observacao_Lancamento` (Origem_Tipo entrada/saída; COD_OBS + Texto_Complementar) e `Cad_Observacao_Lancamento_Fiscal` | — |
| C597 | Ajustes e outras obrigações do documento | **PARCIAL** | `Mov_Nota_Ajuste_Documento` (COD_AJ, descrição, item, base, alíquota, valor, outros) | **IND_BENEFICIO** (campo 09, valores 0, 1, 2, 3, 9; obrigatório se o 3º dígito do COD_AJ for ≠ 9) |

###### 2.4 Energia / água / gás — consolidação (C600–C791), cond. a perfil de concessionária

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| C600 | Consolidação diária (06, 28, 29) | COBERTO-DERIVADO (cond.) | Notas de saída + `Mov_Nota_Fiscal_Utilidade`: COD_MUN = ID_Municipio_Consumo, COD_CONS = ID_Faixa_Consumo, CONS = Consumo_Total, VL_FORN, VL_SERV_NT, VL_TERC, VL_DA; contagens e somas | Confirmar que o domínio COD_CONS (01 a 08) está em `Cad_Faixa_Consumo_Sped` (ver Dúvidas) |
| C601 | Documentos cancelados da consolidação | COBERTO-DERIVADO (cond.) | Notas com Status=cancelada | — |
| C610 | Itens do documento consolidado | COBERTO-DERIVADO (cond.) | Itens de saída (ver C510); COD_CLASS só para modelo 06 | — |
| C690 | Analítico (06, 28, 29) | COBERTO-DERIVADO (cond.) | Como C590 | — |
| C700 | Consolidação Convênio 115 (06, 28, 66) | PARCIAL (cond.) | COD_MOD, SER, NRO_ORD_INI/FIN, DT_DOC_INI/FIN derivam das notas | NOM_MEST (nome do arquivo mestre) e CHV_COD_DIG (autenticação digital do mestre): não existem. `Hash_Convenio_115` é só da nota referenciada |
| C790 | Analítico (06, 28, 66) | COBERTO-DERIVADO (cond.) | Como C590 | — |
| C791 | ST por UF (06, 66) | COBERTO-DERIVADO (cond.) | Base_Calculo_St e Valor_St_Retido; UF possivelmente em ID_Estado_Devedor | Confirmar qual UF do item alimenta o campo UF (ver Dúvidas) |

###### 2.5 SAT CF-e (C800–C897)

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| C800 | CF-e-SAT (59) | COBERTO | `Mov_Nota_Fiscal_Saida` (modelo 59): COD_SIT, NUM_CFE = Numero, DT_DOC, VL_CFE = Valor_Total, CNPJ_CPF = Documento_Consumidor, NR_SAT = Numero_Serie_Fabricacao do equipamento, CHV_CFE = Chave_Acesso (texto), VL_DESC, VL_MERC, VL_OUT_DA, VL_ICMS, VL_PIS/COFINS e ST somados dos itens | — |
| C810 | Itens do CF-e-SAT | COBERTO | `Mov_Nota_Fiscal_Saida_Item`: Numero_Item, produto, Quantidade, unidade, Valor_Total, CST, CFOP | — |
| C815 | ST complementar (SAT) | PARCIAL | Igual ao C330 | Igual ao C330 |
| C850 | Analítico do CF-e-SAT | COBERTO-DERIVADO | Agrupa ICMS por item (CST, CFOP, alíquota efetiva); VL_BC = VL_OPR quando maior que zero (alíquota efetiva) | COD_OBS por combinação (ver Dúvidas) |
| C855 | Observações do CF-e-SAT | COBERTO | `Mov_Nota_Observacao_Lancamento` | — |
| C857 | Ajustes do CF-e-SAT | COBERTO | `Mov_Nota_Ajuste_Documento`. O Guia 3.2.4 não tem IND_BENEFICIO no C857 (nem no C897). O campo existe só em C197, C597, D197, D737, E111, E220 e 1921 (guia, linhas 1076–1082) | — |
| C860 | Identificação do equipamento SAT | COBERTO-DERIVADO | `Cad_Equipamento_Fiscal` (Tipo=sat_cfe: COD_MOD, NR_SAT); DT_DOC, DOC_INI, DOC_FIM do menor e maior Numero por dia | — |
| C870 | Itens do resumo diário SAT | COBERTO-DERIVADO | Itens dos CF-e por dia e equipamento: COD_ITEM, QTD (5 casas), UNID, CST, CFOP | — |
| C880 | ST complementar (SAT) | PARCIAL | Igual ao C330 | Igual ao C330 |
| C890 | Resumo diário do CF-e-SAT por equipamento | COBERTO-DERIVADO | Soma por dia, equipamento, CST, CFOP e alíquota | COD_OBS por combinação |
| C895 | Observações do resumo diário SAT | PARCIAL | `Mov_Nota_Observacao_Lancamento` prende a observação à nota, não ao resumo diário/equipamento | Onde guardar a observação do C890 (nível equipamento/dia), quando a UF a exigir |
| C897 | Ajustes do resumo diário SAT | PARCIAL | `Mov_Nota_Ajuste_Documento` prende o ajuste à observação da nota | Idem C895 |
| C990 | Encerramento do bloco C | COBERTO-DERIVADO | Contagem de linhas do arquivo gerado | — |

##### 3. C500 campo a campo (inclui as regras da Nota Orientativa 2026.001 / NFGás modelo 76)

| Campo | Origem no dicionário | Situação |
|---|---|---|
| 02 IND_OPER, 03 IND_EMIT | Entrada (0) ou saída (1); emissão própria (0) ou terceiros (1). Saída de terceiros usa COD_SIT 08 (exceção 5) | OK |
| 04 COD_PART | `ID_Participante_Fornecedor` (entrada). 66/76 em saída só se IND_DEST=1 | OK |
| 05 COD_MOD | `Cad_Modelo_Documento_Fiscal_Codigo` (Campo_Destino=COD_MOD). Precisa de linha para 76; a Tabela 4.1.1 do Guia 3.2.4 não lista o 76 (só o campo C500 o cita) | OK, ver Dúvidas |
| 06 COD_SIT | `ID_Situacao_Documento` (Tabela 4.1.2) | OK |
| 07 SER, 08 SUB | Serie; Subserie (não preencher em 66/76) | OK |
| 09 COD_CONS | `Mov_Nota_Fiscal_Utilidade.ID_Faixa_Consumo` (não preencher em 66/76) | OK com ressalva |
| 10 a 12 NUM_DOC, DT_DOC, DT_E_S | Numero, Data_Emissao, Data_Entrada | OK |
| 13 VL_DOC | Valor_Total, que deve fechar com VL_FORN + VL_DA + VL_SERV_NT + VL_TERC − (VL_DESC + ENER_INJET + OUTRAS_DED) | OK, mas o fechamento depende dos campos 39 e 40 |
| 14 VL_DESC | Soma de Valor_Desconto_Item | Derivado |
| 15 VL_FORN, 16 VL_SERV_NT, 17 VL_TERC, 18 VL_DA | `Mov_Nota_Fiscal_Utilidade` (Valor_Fornecimento, Valor_Servico_Nao_Tributado_Icms, Valor_Cobrado_Terceiros, Valor_Despesas_Acessorias) | OK. Na NF3e a regra é por grupo de cClass (060–065, 085, 087 etc.); na NFGás, por natureza do item (dentro ou fora do campo de incidência do ICMS) |
| 19 a 22 | Soma de ICMS por item (base, valor, Base_Calculo_St, Valor_St_Retido) | Derivado; entrada só com `Gera_Credito` |
| 23 COD_INF | `Mov_Nota_Fiscal_Informacao_Complementar` | OK |
| 24, 25 PIS, Cofins | Por item. Dispensado se houver EFD-Contribuições | Derivado |
| 26 TP_LIGACAO | `Mov_Nota_Fiscal_Utilidade.Tipo_Ligacao` (mono/bi/trifásica = 1/2/3). Só saída modelo 06 | OK (a descrição diz "a conferir") |
| 27 COD_GRUPO_TENSAO | `Grupo_Tensao` (código 2). Só saída modelo 06 | OK (idem) |
| 28 CHV_DOCe | `Chave_Acesso` (texto até 50; 44 no arquivo; regra de exportação a registrar). Obrigatório em 66 e, desde 2026, em 76 | OK |
| 29 FIN_DOCe | `Mov_Nota_Fiscal_Entrada.Finalidade` {normal, complementar, ajuste, devolucao, substituicao}. Mapa: 1 normal, 2 substituicao, 3 normal com ajuste = `ajuste`. NFGás só 1 e 2 | OK para 1 e 2. A restrição "76 só 1 e 2" é regra de validação que o dicionário não mostra |
| 30 CHV_DOCe_REF | `Mov_Nota_Fiscal_Entrada_Referenciada.Chave_Referenciada` (Tipo=substituicao) | OK |
| 31 IND_DEST, 32 COD_MUN_DEST | Só saída: indicador de IE e município do participante | Derivado |
| 33 COD_CTA | `ID_Conta_Contabil` do item; no cabeçalho só se única | OK com ressalva |
| 34 COD_MOD_DOC_REF | Modelo do documento referenciado, ou `Modelo_Papel` (paper). 76 exige 28 ou 76; 66 exige 06 ou 66 | OK |
| 35 HASH_DOC_REF | `Hash_Convenio_115` (agora também para o 28) | OK |
| 36 SER_DOC_REF, 37 NUM_DOC_REF | `Serie_Papel` (3 posições; o campo do Guia tem 4), `Numero_Papel` | OK, ver Dúvidas |
| 38 MES_DOC_REF | `Competencia_Emissao` (mês da emissão do substituído) | OK, ver Dúvidas |
| **39 ENER_INJET** | Sem campo. Só derivável dos itens cClass grupos 560/085/087 da NF3e, e a tabela cClass não veio | **FALTA** |
| **40 OUTRAS_DED** | Sem campo. Só derivável dos itens cClass grupos 590/085/087 (NF3e) e dos grupos "deduções" da NFGás, e a tabela cClass não veio | **FALTA** |

Pontos específicos da NFGás (modelo 76) pedidos:
- Finalidades só 1 e 2: o dicionário aceita 5 finalidades na nota de entrada e nenhuma regra visível limita o 76. Ver Dúvidas.
- Grupos cClass: `Mov_Nfgas_Entrada_Item.ID_Classificacao_Item` guarda o cClass de 7 dígitos, mas a tabela não veio (Q165-12). Não há atributo que diga a que campo da EFD (VL_FORN, VL_SERV_NT, VL_TERC, OUTRAS_DED) cada grupo alimenta, como existe para a NFCom (`Cad_Nfcom_Classificacao_Servico` com indicadores).
- Itens sem CST não escriturados: o dicionário só registra o caso "sem CST" para a NFCom saída (`ID_CFOP_Saida` opcional). Para NF3e/NFGás de entrada a regra seria "item sem linha de ICMS em `Mov_Apuracao_Tributo_Item`", mas não está dita.
- C510/C590: documentos eletrônicos de emissão própria não têm C510; entrada de NF3e/NFGás tem C500 + C590 (+ C591, C595, C597). O dicionário cobre esse formato.

##### 4. Lacunas reais (por ordem de peso)

1. **IND_BENEFICIO (C597 campo 09)**: não existe em `Mov_Nota_Ajuste_Documento` nem em `Cad_Icms_Codigo_Ajuste`. O mesmo campo é exigido em C197, D197, D737, E111, E220 e 1921 (fora deste escopo); vale checar os mesmos pontos no resto do dicionário. No C857/C897 o Guia não tem o campo, então não há lacuna ali.
2. **C500 campos 39 e 40 (ENER_INJET, OUTRAS_DED)** sem campo, e sem mapa cClass → campo EFD (grupos da NF3e; grupos de deduções da NFGás). Sem os dois, o VL_DOC do C500 não fecha pela regra do Guia, para notas com energia injetada ou deduções. Falta também a carga da tabela cClass da NF3e e da NFGás.
3. **C420 (totalizadores parciais da Redução Z) e Tabela 4.4.6**: ausentes. Sem eles não saem C420, C425 (itens do dia) e a conferência do C490.
4. **Cupom ECF** (C460, C465, C470, C490): sem entidade nem decisão. Faltam NUM_CCF e QTD_CANC; `Mov_Ecf_Reducao_Z_Tributo` é só PIS/Cofins e não tem QTD/UNID do item.
5. **Família ST restituição/complemento** (C330, C380, C430, C480, C815, C880; e, em outro arquivo, C180/C181/C185/C186): sem entidade para QUANT_CONV, VL_UNIT_CONV, VL_UNIT_ICMS_NA_OPER, VL_UNIT_ICMS_OP_CON/ESTO, VL_UNIT_ICMS_ST_ESTO, FCP ST e ICMS ST de restituição/complemento. `Mov_Icms_St_Ressarcimento` só traz o equivalente ao C176. A obrigatoriedade é definida por UF.
6. **C591**: sem origem de FCP próprio e FCP ST por item (informativo, UF-dependente).
7. **C700**: NOM_MEST e CHV_COD_DIG (Convênio 115) sem campo (só concessionária).
8. **C510**: IND_REC e COD_PART do receptor da receita por item (só saída papel).
9. **C895/C897**: observação e ajuste no nível do resumo diário do equipamento SAT não têm onde ficar.

##### 5. Dúvidas (para Alberto ou para confirmar na carga)

1. **Perfil**: a Mlegate emite NF mod. 02, usa ECF/SAT ou fornece energia/gás/água? Se não, C300–C495, C510–C791 e parte do C8xx ficam como "legado, não gerar", como o doc 43 já tratou a tb131.
2. **COD_CONS (C500/C600, modelos 06 e 28)**: o Guia fixa 8 classes (01 Comercial a 08 Serviço público). `Cad_Faixa_Consumo_Sped` é descrito com limites de consumo (kWh/reais) e "4.4.5 energia, 4.4.3 gás". Confirmar que as linhas carregadas de energia e gás são as 8 classes e não uma tabela de faixas. Para água vale a Tabela 4.4.2.
3. **Grupo de tensão (01 a 14) e Tipo de ligação**: `Grupo_Tensao` é código de 2 posições sem domínio nomeado; `Tipo_Ligacao` e `Grupo_Tensao` trazem "a conferir".
4. **Finalidade do modelo 76**: confirmar a regra que barra finalidades diferentes de normal e substituição, e que `ajuste` (FIN_DOCe 3) é só NF3e. O próprio dicionário diz que o tpAjuste da NF3e foi descontinuado com a finalidade 3.
5. **Tabela de modelos**: o Guia 3.2.4 (subseção 1.4) não lista o 76, mas o C500 o aceita. Garantir a linha COD_MOD=76 em `Cad_Modelo_Documento_Fiscal_Codigo`. Verificar também 2D, 60, 59 e 28.
6. **MES_DOC_REF**: usar `Competencia_Emissao`. `Competencia_Apuracao_Papel` (doc 165) é competência de apuração, não mês de emissão. `Serie_Papel` tem 3 posições; SER_DOC_REF tem 4.
7. **COD_OBS no nível analítico** (C320, C390, C490, C590, C690, C790, C850, C890): o dicionário liga a observação à nota, não à combinação CST/CFOP/alíquota. Definir qual observação vai em qual combinação quando a nota tem várias.
8. **CST sob o enfoque do declarante (C590, entrada)**: o `ID_Cst` do item é "decidido pelo Motor de Regras". Confirmar que o CST do fornecedor, como veio na nota, também fica guardado.
9. **C791**: confirmar qual UF alimenta o campo UF (`ID_Estado_Devedor` ou `ID_Estado_Destino`).
10. **Truncamento do dump**: a enumeração de `Mov_Apuracao_Tributo_Item.Origem_Tipo` aparece cortada ("nota_fiscal_entrada, nota_fiscal_saida, evento_conta_financeira, pag…"). Não deu para confirmar se há origem para cupom ECF ou resumo diário, o que afeta C460 a C490 e C895/C897.
11. **C181/C186** (citados na tarefa): ficam no arquivo C1 e não aparecem pelo nome no dicionário. A chave do documento de entrada seria derivada da nota (`Chave_Acesso`), por `Mov_Icms_St_Ressarcimento.ID_Item_Entrada_Origem`; confirmar no escopo do outro arquivo.

##### 6. Resumo numérico

47 registros analisados: COBERTO 9, COBERTO-DERIVADO 18, PARCIAL 18, AUSENTE 2 (C420 e C495; este último sem relevância, obsoleto desde 2014). Os vereditos marcados "(cond.)" valem se a Mlegate lançar esses documentos no dicionário.


# Anexo D — Bloco D


Método: li o guide_bloco_D.txt inteiro, confrontei com o guia completo (/tmp/efd324.txt) e procurei no dict_dump.txt por entidade e por termo (CT-e, NFCom, Utilidade, Equipamento_Fiscal, Redução Z, Referenciada, Apuracao_Tributo_Item, Cad_Obrigacao_*).

Aviso sobre o guide_bloco_D.txt: a extração perdeu campos que existem no guia completo. Conferi no guia completo e já usei nos vereditos: D100.13 TP_CT-e, D190.05 VL_OPR, D530 (campo 05 está certo), D690.08 e .09 (VL_BC_ICMS_UF e VL_ICMS_UF), D696.02 e .05, D697.02 UF, D700.01 a 09, 22 CHV_DOCe, 23 FIN_DOCe, 26 CHV_DOCe_REF.
Aviso sobre o dict_dump.txt: as enumerações vêm cortadas em cerca de 80 caracteres (Tipo_Cte, Tipo_Referencia etc.). Onde o veredito depende de um valor de enumeração cortado, está dito.

Legenda: COBERTO / COBERTO-DERIVADO (origem existe, o registro é montado na geração) / PARCIAL (faltam campos) / AUSENTE (não há onde guardar).
Regras aplicadas: (1) "O ERP só registra", sem tabela espelho por registro; (2) analíticos e consolidações contam COBERTO-DERIVADO quando CST, CFOP, alíquota, base e ICMS por documento existem; (3) parâmetro com vigência, sem valor oculto. Como no res_1.md, registro setorial AUSENTE entra como lacuna a registrar, atrás do parâmetro de habilitação por empresa (Cad_Empresa_Modulo_Opcional), com uma exceção: os registros dos modelos 07, 09, 10, 11, 26 e 27 não podem mais ser apresentados (ver "Fato que muda a leitura").

##### Fato que muda a leitura

O guia, no D100 campo 11, diz: "Se COD_MOD for 07, 09, 10, 11, 26 ou 27, a data informada deverá ser menor que 01/01/2019". Logo, para qualquer arquivo de 2019 em diante (o ERP nasce em 2026) esses modelos não existem. Isso torna sem efeito prático D110, D120, D140, D150, D170 e D180 (e D160 a D162 para 09, 10, 11, 26, 27). Marquei esses registros AUSENTE (porque o dicionário não os tem) mas com a nota "N/A 2019+", e não os contei como lacuna a registrar. Continuam válidos em período corrente: modelo 08 (CTRC) e 8B (avulso), 57 (CT-e, inclusive simplificado), 63 (BP-e) e 67 (CT-e OS).

##### Caminho dos dados no dicionário (para ler a tabela)

- CT-e entra e sai como nota: Mov_Nota_Fiscal_Entrada (recebido) ou Mov_Nota_Fiscal_Saida (emitido), ligada a Mov_Documento_Fiscal (chave, protocolo) e a Mov_Cte (dados do transporte, 1 por documento fiscal). A descrição de Mov_Nota_Observacao_Lancamento diz isso: "inclui o CT-e, que entra como nota". O item da nota carrega CFOP, CST (ID_Cst), conta (COD_CTA), desconto e número do item. Os impostos do item ficam em Mov_Apuracao_Tributo_Item (Origem_Tipo nota_fiscal_entrada ou nota_fiscal_saida; base bruta e efetiva, alíquota, valor, valor desonerado, Gera_Credito, ID_Estado_Devedor para ICMS de outra UF, ID_Estado_Destino para DIFAL e FCP).
- Modelo (COD_MOD) vem de Cad_Modelo_Documento_Fiscal_Codigo (Campo_Destino, Registros_Aplicaveis, vigência). Situação (COD_SIT) vem de ID_Situacao_Documento (tabela 4.1.2).
- NFCom: saída em Mov_Nfcom (+ Cad_Nfcom_Assinante, _Terminal, Mov_Nfcom_Fatura, Mov_Nfcom_Item, Cad_Nfcom_Classificacao_Servico); entrada em Mov_Nfcom_Entrada (+ _Item) e Mov_Nota_Fiscal_Entrada_Fatura.
- Notas 21 e 22 (comunicação) usam a nota de entrada ou de saída mais Mov_Nota_Fiscal_Utilidade (valor não tributado, valor de terceiros, despesas acessórias, município de consumo, classe de consumo) e, no item de saída, ID_Tipo_Receita_Comunicacao e ID_Classificacao_Item_Utilidade.
- Observação (D195 e D735) em Mov_Nota_Observacao_Lancamento, ajuste (D197 e D737) em Mov_Nota_Ajuste_Documento, informação complementar (COD_INF) em Mov_Nota_Fiscal_Informacao_Complementar.
- Layout e regras por campo: Cad_Obrigacao_Leiaute_Registro e _Campo (com vigência), parâmetros em Cad_Obrigacao_Parametro_Definicao e _Valor.

##### Tabela por registro

| Registro | Nome | Veredito | Onde está | Campos que faltam |
| ---|---|---|---|--- |
| D001 | Abertura do Bloco D | COBERTO-DERIVADO | IND_MOV calculado pela existência de documentos nos registros do bloco; layout em Cad_Obrigacao_Leiaute_Registro e _Campo | nenhum |
| D100 | Notas de transporte (07, 08, 8B, 09, 10, 11, 26, 27), CT-e 57, CT-e OS 67, BP-e 63 | PARCIAL | IND_OPER e IND_EMIT: Papel e Mov_Nota_Fiscal_Entrada/Saida. COD_PART: ID_Participante_Fornecedor (entrada) ou tomador (Mov_Cte.ID_Participante_Tomador, saída). COD_MOD: Cad_Modelo_Documento_Fiscal_Codigo. COD_SIT: ID_Situacao_Documento. SER: Serie (código até 5, texto, serve ao "000" do CT-e). SUB: Subserie. NUM_DOC: Numero (até 15). CHV_CTE: Chave_Acesso (código até 50, texto, nunca número). DT_DOC: Data_Emissao. DT_A_P: Data_Entrada (entrada) ou Data_Hora_Saida_Entrada (saída). TP_CT-e: Mov_Cte.Tipo_Cte (0, 1, 3, 4, 5, 6 do schema 4.00). CHV_CTE_REF: Mov_Nota_Fiscal_Saida_Referenciada (Tipo_Referencia cte_substituido) e Mov_Nota_Fiscal_Entrada_Referenciada (substituicao). VL_DOC: Valor_Total. VL_DESC: soma de Valor_Desconto_Item. IND_FRT: ID_Modalidade_Frete. VL_SERV: Mov_Cte.Valor_Prestacao. VL_BC_ICMS, VL_ICMS: Mov_Apuracao_Tributo_Item (na entrada só com Gera_Credito). VL_NT: derivável do CST e do valor desonerado. COD_INF: Mov_Nota_Fiscal_Informacao_Complementar. COD_CTA: item.ID_Conta_Contabil. COD_MUN_ORIG e COD_MUN_DEST: Mov_Cte.ID_Municipio_Origem e _Destino | (a) BP-e 63: nenhuma estrutura (Mov_Cte só cobre CT-e e CT-e OS; sem tipo de BP-e, sem município de origem e destino do bilhete). (b) 9999999 (exterior) e 9999998 (origem do CT-e simplificado, campo 24): não há onde guardar o código; Cad_Municipio.Codigo_IBGE exige 2 primeiros dígitos iguais à UF. O campo 25 (destino) não aceita mais 9999998 e, a partir de 2027, o guia veda o 9999998: a regra precisa viver em Cad_Obrigacao_Leiaute_Campo.Valores_Validos com vigência, não em código. (c) Modelos 08 e 8B de saída: município de origem e destino (obrigatório em toda saída desde 2022) só existe em Mov_Cte, que é eletrônico. (d) Sub-quadro por modelo abaixo |
| D100 por modelo | (sub-quadro) | | 57 CT-e: COBERTO, salvo (b). 67 CT-e OS: COBERTO (a descrição de Tipo_Cte cita "CT-e e CT-e OS"), salvo (b). 63 BP-e: AUSENTE (a). 08 e 8B: entrada COBERTO via nota de entrada com o modelo; saída PARCIAL por (c); o ERP não tem motor de emissão desses modelos. 07, 09, 10, 11, 26, 27: N/A em 2019+ | ver (a), (b), (c) |
| D101 | Informação complementar, EC 87/15 (57, 63, 67) | PARCIAL | Mov_Apuracao_Tributo_Item tem ID_Estado_Destino ("UF de destino do DIFAL e do FCP de destino"). A regra de não apresentar (UFs iguais ou 9999999) deriva de Mov_Cte | VL_FCP_UF_DEST, VL_ICMS_UF_DEST e VL_ICMS_UF_REM: não há como separar as três parcelas por documento. Cad_Imposto (Sigla aberta, sem FCP nem DIFAL nominal) e a linha de tributo não dizem qual linha é qual. VL_ICMS_UF_REM é zero desde 2019, mas o zero precisa de parâmetro com vigência |
| D110 | Itens da NF de transporte 07 | COBERTO-DERIVADO (N/A 2019+) | NUM_ITEM: Numero_Item; COD_ITEM: ID_Produto_Servico; VL_SERV: Valor_Total do item; VL_OUT: Valor_Outras_Despesas_Item | nenhum |
| D120 | Complemento da NF de transporte 07 | AUSENTE (N/A 2019+) | nada no dicionário para município de origem e destino em nota que não seja CT-e | COD_MUN_ORIG, COD_MUN_DEST, VEIC_ID, UF_ID. Sem efeito prático |
| D130 | Complemento do CTRC 08, 8B e CT-e simplificado 57 (TP_CT-e 5 e 6, desde 01/2025) | PARCIAL | COD_PART_CONSG no CT-e simplificado: o tomador (Mov_Cte.ID_Participante_Tomador). VEIC_ID e UF_ID (OC): Cad_Veiculo_Transporte (Placa, ID_Estado_Licenciamento) via Mov_Mdfe_Documento pela chave. VL_FRT, VL_LIQ_FRT: só o total do CT-e (Mov_Cte.Valor_Prestacao, Mov_Cte_Componente_Valor) | (a) CT-e simplificado exige 1 registro por entrega ("identificar individualmente cada entrega/prestação"), com município de origem e destino e VL_FRT próprios, e o D100.VL_SERV deve ser igual à soma dos VL_FRT. Mov_Cte tem um só origem, um só destino e um só valor; não há entidade de detalhe por entrega. (b) VL_SEC_CAT, VL_DESP, VL_PEDG, VL_OUT: Mov_Cte_Componente_Valor guarda só Nome_Componente em texto livre; falta a classe do componente (frete peso, Sec/Cat, despacho, pedágio, outros) para somar por campo. (c) COD_PART_RED e IND_FRT_RED (0, 1, 2, 9): Mov_Cte tem Tipo_Servico (redespacho) mas não o participante redespachado nem quem paga o frete do redespacho. (d) COD_PART_CONSG do CTRC 08 de saída: sem campo, sem efeito prático |
| D140 | Complemento do conhecimento aquaviário 09 | AUSENTE (N/A 2019+) | Mov_Cte.Modal aceita aquaviario mas não há grupo do modal | IND_VEIC, VEIC_ID (IRIM), IND_NAV, VIAGEM, VL_DESP_PORT, VL_DESP_CAR_DESC, VL_FRT_MM e demais. Sem efeito prático |
| D150 | Complemento do conhecimento aéreo 10 | AUSENTE (N/A 2019+) | idem (Modal aereo sem grupo) | VEIC_ID (aeronave), VIAGEM, IND_TFA, VL_PESO_TX, taxas. Sem efeito prático |
| D160 | Carga transportada (08, 8B, 09, 10, 11, 26, 27) | PARCIAL (só 08 e 8B contam) | CNPJ_CPF_REM, IE_REM, CNPJ_CPF_DEST, IE_DEST: participantes remetente e destinatário de Mov_Cte; COD_MUN_ORI e COD_MUN_DEST: Mov_Cte | DESPACHO (número do despacho, OC). O CT-e 57 não usa D160 (exceção 4 do D100) |
| D161 | Local da coleta e entrega (08, 8B, 09, 10, 11, 26) | PARCIAL (só 08 e 8B contam) | Mov_Cte tem expedidor e recebedor (participantes) e o modal | IND_CARGA (tipo de transporte da carga coletada: 0 rodoviário a 5 aéreo, 9 outros) sem campo próprio (parece derivar de Mov_Cte.Modal, mas a lista difere: falta "rodo-ferroviário"); município do local de coleta e de entrega: só se for o do participante expedidor ou recebedor; confirmar a regra |
| D162 | Documentos fiscais da carga (08, 8B, 09, 10, 11, 26, 27) | PARCIAL (só 08 e 8B contam) | Mov_Cte_Documento_Transportado: Serie, Numero_Documento, Data_Emissao, Valor_Documento (VL_DOC), Valor_Produtos (VL_MERC), Peso_Kg (PESO_BRT, só nota em papel), Modelo_Nf_Papel (COD_MOD); para NF-e, chave e ID_Documento_Fiscal | QTD_VOL (obrigatório) e PESO_LIQ: sem campo por documento transportado; PESO_BRT só existe para NF em papel |
| D170 | Complemento do conhecimento multimodal 26 | AUSENTE (N/A 2019+) | nada | COD_PART_CONSG, COD_PART_RED, OTM, IND_NAT_FRT, VL_GRIS, VL_PDG e demais. Sem efeito prático |
| D180 | Modais (26) | AUSENTE (N/A 2019+) | nada | todos. Sem efeito prático |
| D190 | Analítico dos documentos de transporte | COBERTO-DERIVADO | Agrupa os itens por CST (ID_Cst), CFOP (ID_CFOP_Entrada ou _Saida) e alíquota (Aliquota_Efetiva). VL_OPR: itens mais frete, seguro e outras despesas; VL_BC_ICMS e VL_ICMS: Base_Calculo_Efetiva e Valor_Tributo; VL_RED_BC: Base_Calculo_Bruta menos Base_Calculo_Efetiva (Mecanismo_Reducao); COD_OBS: Mov_Nota_Observacao_Lancamento | nenhum campo. Ver dúvida 9 (COD_OBS por combinação) |
| D195 | Observações do lançamento fiscal | COBERTO | Mov_Nota_Observacao_Lancamento: ID_Observacao (COD_OBS, Cad_Observacao_Lancamento_Fiscal), Texto_Complementar (TXT_COMPL) | nenhum |
| D197 | Outras obrigações e ajustes do documento | PARCIAL | Mov_Nota_Ajuste_Documento: COD_AJ (ID_Codigo_Ajuste, tabela 5.3), DESCR_COMPL_AJ, COD_ITEM (Tipo_Item_Origem e ID_Item_Origem), VL_BC_ICMS, ALIQ_ICMS, VL_ICMS, VL_OUTROS, sub-apuração | IND_BENEFICIO (campo 09, novo em 01/2027; 0, 1, 2, 3 ou 9; obrigatório quando o 3º dígito do COD_AJ não é 9). Não existe em nenhuma entidade do dicionário |
| D300 | Analítico dos bilhetes consolidados (13, 14, 15, 16) | COBERTO-DERIVADO (condicional) | Só se cada bilhete for lançado como Mov_Nota_Fiscal_Saida de modelo do tipo "passagem" (domínio aberto de Cad_Modelo_Documento_Fiscal): faixa por série e subsérie, datas, CST, CFOP, alíquota, base e ICMS vêm dos itens | nada no nível de campo. O dicionário não diz que o bilhete individual é lançado; ver dúvida 1 |
| D301 | Bilhetes cancelados | COBERTO-DERIVADO (condicional) | Notas da faixa com ID_Situacao_Documento = cancelado (mesma condição do D300) | nenhum |
| D310 | Complemento dos bilhetes, por município de origem | PARCIAL | Valores por município: derivados do bilhete | COD_MUN_ORIG do bilhete: Mov_Nota_Fiscal_Saida não tem município de origem do serviço (Mov_Cte tem, mas é CT-e) |
| D350 | Equipamento ECF (2E, 13, 14, 15, 16) | COBERTO | Cad_Equipamento_Fiscal (Tipo_Equipamento = ecf): Modelo_Equipamento (ECF_MOD), Numero_Serie_Fabricacao (ECF_FAB), Numero_Caixa (ECF_CX), ID_Modelo_Documento (COD_MOD) | nenhum campo. Dúvida 6: a descrição do campo lista só os modelos 02, 2D, 59 e 65 |
| D355 | Redução Z | COBERTO | Mov_Ecf_Reducao_Z: Data_Movimento (DT_DOC), Contador_Reinicio_Operacao (CRO), Contador_Reducao_Z (CRZ), Numero_Coo_Final, Grande_Total_Final (GT_FIN), Valor_Venda_Bruta (VL_BRT). As descrições citam C405, os dados são os mesmos | nenhum |
| D360 | PIS e COFINS totalizados no dia | COBERTO-DERIVADO | Soma de Mov_Ecf_Reducao_Z_Tributo.Valor_Tributo por ID_Imposto (PIS, Cofins) e Redução Z. Dispensado quando há EFD-Contribuições do mesmo período | nenhum |
| D365 | Totalizadores parciais da Redução Z | AUSENTE | Mov_Ecf_Reducao_Z_Tributo só tem PIS e Cofins; nada para ICMS por totalizador | COD_TOT_PAR, VLR_ACUM_TOT, NR_TOT, DESCR_NR_TOT. É a mesma lacuna do C420 (ECF de mercadoria); confirmar se há tratamento no Bloco C |
| D370 | Complemento dos documentos informados (13 a 16 e 2E) | AUSENTE | nada | COD_MUN_ORIG, QTD_BILH, VL_SERV, VL_BC_ICMS, VL_ICMS por município de origem |
| D390 | Analítico do movimento diário (ECF) | AUSENTE | Mov_Ecf_Reducao_Z_Tributo não tem ICMS, CST, CFOP, alíquota nem ISSQN. Não é derivável de documentos porque a fonte é a Redução Z | todos os valores (VL_OPR, VL_BC_ISSQN, ALIQ_ISSQN, VL_ISSQN, VL_BC_ICMS, VL_ICMS, COD_OBS) |
| D400 | Resumo de movimento diário, RMD (18) | PARCIAL | Pode ser nota de saída de modelo 18 (Numero, Serie, Subserie, Data_Emissao, ID_Situacao_Documento, Valor_Total, itens, impostos, COD_CTA) | COD_PART é a agência, filial ou posto: Mov_Nota_Fiscal_Saida só tem cliente e filial emitente. Depende do modelo 18 estar na carga de Cad_Modelo_Documento_Fiscal_Codigo |
| D410 | Documentos informados no RMD (13 a 16) | PARCIAL | Faixas e totais derivam dos bilhetes (mesma condição do D300) | vínculo entre bilhete e RMD (o bilhete do D400 não pode repetir no D300); não há campo |
| D411 | Bilhetes cancelados do RMD | PARCIAL | ID_Situacao_Documento do bilhete | mesmo vínculo com o RMD |
| D420 | Complemento do RMD, por município de origem | PARCIAL | Valores derivados | COD_MUN_ORIG do bilhete (como D310) |
| D500 | NF de comunicação 21 e telecomunicação 22 | PARCIAL | Mov_Nota_Fiscal_Entrada/Saida com modelo 21 ou 22, mais Mov_Nota_Fiscal_Utilidade: VL_SERV_NT (Valor_Servico_Nao_Tributado_Icms), VL_TERC (Valor_Cobrado_Terceiros), VL_DA (Valor_Despesas_Acessorias). Demais campos como no D100 (Subserie, DT_A_P, COD_INF, VL_PIS e VL_COFINS em Mov_Apuracao_Tributo_Item, COD_CTA). Entrada fica COBERTO | TP_ASSINANTE (campo 24, obrigatório na saída): domínio próprio do D500 (1 comercial/industrial, 2 poder público, 3 residencial/PF, 4 público, 5 semi-público, 6 outros). O dicionário só tem tipo_assinante_nfcom (Cad_Nfcom_Assinante e Cad_Ponto_Servico_Utilidade), com outros códigos, e só para NFCom. Sem efeito prático se o Mlegate não escritura saída de 21 e 22 |
| D510 | Itens da NF 21 e 22 (só saída) | PARCIAL | Numero_Item; ID_Produto_Servico (COD_ITEM); ID_Classificacao_Item_Utilidade (COD_CLASS, tabela 4.4.1); Quantidade; ID_Unidade_Medida; Valor_Total; Valor_Desconto_Item; CST, CFOP, base, alíquota e ICMS em Mov_Apuracao_Tributo_Item; base e ICMS de outras UFs por ID_Estado_Devedor; ID_Tipo_Receita_Comunicacao (IND_REC); VL_PIS e VL_COFINS; ID_Conta_Contabil | COD_PART (campo 17, participante da receita de terceiros): o item de saída não tem participante. A regra "IND_REC 1, 5 ou 9 obriga base, alíquota e ICMS zero" é validação, não campo |
| D530 | Terminal faturado (21 e 22, só saída) | PARCIAL | Para NFCom: Cad_Nfcom_Assinante (ID_Tipo_Servico_Utilizado dá IND_SERV, Numero_Terminal_Principal dá COD_AREA e TERMINAL) e Mov_Nfcom_Fatura (Data_Uso_Inicio, Data_Uso_Fim, Competencia dá PER_FISCAL). Os dados de uso existem, mas só no pacote NFCom | Para nota 21 e 22 de saída: nenhuma entidade de terminal (Cad_Nfcom_Assinante é 1:1 com Mov_Nfcom). Campo 05 PER_FISCAL agora é N com 6 posições (MMAAAA): Competencia serve se a geração formatar assim. Os 7 tipos de tpServUtil (inclui "vários") não casam um a um com IND_SERV (0, 1, 2, 3, 4, 9) |
| D590 | Analítico da NF 21 e 22 | COBERTO-DERIVADO | Mesmo mecanismo do D190, mais VL_BC_ICMS_UF e VL_ICMS_UF (linhas com ID_Estado_Devedor diferente da UF do informante) | nenhum |
| D600 | Consolidação 21 e 22 (não obrigadas ao Convênio 115) | COBERTO-DERIVADO (condicional) | Soma das notas de saída 21 e 22 por município (Mov_Nota_Fiscal_Utilidade.ID_Municipio_Consumo), classe de consumo (ID_Faixa_Consumo, Servico = comunicacao, Modelos_Aplicaveis 21 e 22, Consolida_Documentos), série, subsérie e data; QTD_CONS é contagem; VL_SERV_NT, VL_TERC, VL_DA da Utilidade | nenhum campo. Condição: nota individual lançada; escolha entre D500 e D600 é parâmetro (dúvida 8) |
| D610 | Itens do consolidado | COBERTO-DERIVADO | Itens agrupados: COD_CLASS (ID_Classificacao_Item_Utilidade), COD_ITEM, QTD, UNID, VL_ITEM, VL_DESC, CST, CFOP, alíquota, base, ICMS, base e ICMS de outras UFs, redução, PIS, COFINS, COD_CTA | nenhum |
| D690 | Analítico do consolidado | COBERTO-DERIVADO | Como D590 | nenhum |
| D695 | Consolidação 21 e 22 (Convênio ICMS 115/03) | AUSENTE | nada. O único traço do Convênio 115 é Hash_Convenio_115 nas notas referenciadas | NRO_ORD_INI, NRO_ORD_FIN, DT_DOC_INI, DT_DOC_FIN, NOM_MEST (nome do arquivo mestre), CHV_COD_DIG (hash de 32). Só vale se o Mlegate for prestador sujeito ao convênio |
| D696 | Analítico do D695 | PARCIAL | Os valores por CST, CFOP e alíquota derivam das notas, como no D590 | vínculo da nota com o intervalo do D695 (série e faixa de ordem do arquivo mestre) |
| D697 | Outras UFs, TV por assinatura via satélite | COBERTO-DERIVADO (condicional) | Base e ICMS por UF do tomador: UF do participante (endereço) ou ID_Estado_Devedor | nenhum campo; só tem sentido com D695 |
| D700 | NFCom (62), entrada e saída | PARCIAL | IND_OPER, IND_EMIT, COD_PART (só entrada), COD_MOD, COD_SIT (00 e 08), SER (Serie, texto), NUM_DOC, DT_DOC, DT_E_S, VL_DOC, VL_DESC, COD_INF, VL_PIS, VL_COFINS, CHV_DOCe (Chave_Acesso). FIN_DOCe: Finalidade (normal, ajuste, substituicao, nos dois sentidos). TIP_FAT: ID_Tipo_Faturamento (Mov_Nfcom e Mov_Nfcom_Entrada). VL_SERV, VL_SERV_NT (itens sem destaque), VL_TERC (item com Cnpj_Cobranca_Terceiro), VL_DA (Valor_Outras_Despesas_Item), DED (itens com Natureza_Valor = deducao, o "grupo 590"), VL_BC_ICMS e VL_ICMS: itens. COD_MUN_DEST (saída): município do assinante (Cad_Nfcom_Assinante.ID_Municipio_Terminal ou endereço). Referências: Competencia_Emissao (MES_DOC_REF, campo 30), Hash_Convenio_115 (HASH_DOC_REF), Chave_Referenciada (CHV_DOCe_REF); na entrada também Modelo_Papel, Serie_Papel, Numero_Papel | (a) Saída: Mov_Nota_Fiscal_Saida_Referenciada não tem modelo, série nem número do documento 21 ou 22 substituído (COD_MOD_DOC_REF, SER_DOC_REF, NUM_DOC_REF); isso trava também a emissão do gSub/gNF. (b) Entrada: Serie_Papel tem 3 posições e SER_DOC_REF tem 4; as descrições dessas colunas falam só de NFGas e NF3e. (c) Nas entradas, VL_DOC, VL_DESC, VL_SERV, VL_SERV_NT, VL_TERC e VL_DA ignoram os cClass 110, 120 e 130: o dicionário não diz que flag de Cad_Nfcom_Classificacao_Servico marca esses grupos (dúvida 7). (d) NFCom de ajuste de entrada exige COD_PART igual ao próprio informante (dúvida 10) |
| D730 | Analítico da NFCom | COBERTO-DERIVADO | Itens por CST, CFOP e alíquota; VL_OPR só dos serviços próprios (exclui o que não é próprio, pela classificação do cClass) | nenhum campo |
| D731 | FCP da NFCom | PARCIAL | Mov_Nfcom_Item_Processo.Valor_Fcp existe, mas só no grupo de processo (gProcRef) | VL_FCP_OP do item comum: sem campo nem imposto nominal (mesma lacuna do D101) |
| D735 | Observações do lançamento (62) | COBERTO | Mov_Nota_Observacao_Lancamento | nenhum |
| D737 | Outras obrigações e ajustes (62) | PARCIAL | Mov_Nota_Ajuste_Documento, como D197 | IND_BENEFICIO (campo 09, 01/2027) |
| D750 | Escrituração consolidada da NFCom | COBERTO-DERIVADO | Soma das NFCom de saída normais (Finalidade normal, COD_SIT 00) por SER, DT_DOC e IND_PREPAGO (Mov_Nfcom.Indicador_Pre_Pago: 0 pré, 1 pós); DED pela classificação | nenhum campo. Falta definir o parâmetro "a UF manda consolidar a NFCom de saída" (dúvida 8) |
| D760 | Analítico do D750 | COBERTO-DERIVADO | Como D730 | nenhum |
| D761 | FCP do D760 | PARCIAL | Como D731 | VL_FCP_OP |
| D990 | Encerramento do Bloco D | COBERTO-DERIVADO | QTD_LIN_D é contagem na geração | nenhum |

##### Lacunas reais (para registrar)

1. IND_BENEFICIO em D197 e D737 (período 01/2027 em diante). Não existe em lugar nenhum do dicionário. É o mesmo buraco de C197, C597, E111, E220 e 1921 (ver res_1.md, lacuna 1). Mov_Nota_Ajuste_Documento precisa do campo Indicador_Beneficio (0, 1, 2, 3, 9), obrigatório quando o terceiro dígito do código de ajuste não é 9, com sugestão por código de ajuste em Cad_Icms_Codigo_Ajuste (parâmetro com vigência).
2. FCP e DIFAL por documento (D101, D731, D761). Mov_Apuracao_Tributo_Item tem ID_Estado_Destino, mas nada diz qual linha é o ICMS de destino, o ICMS do remetente e o FCP. Faltam linhas nominais em Cad_Imposto (ou um tipo de parcela na linha de tributo) e o item de NFCom/CT-e passa a guardá-las. D101.VL_ICMS_UF_REM (zero após 2019) precisa de parâmetro com vigência.
3. CT-e simplificado, D130 (desde 01/2025): falta uma entidade de detalhe por entrega (município de origem e destino, valor líquido, valor do frete, componentes, documentos transportados), a classe do componente de valor (frete peso, Sec/Cat, despacho, pedágio, outros) em Mov_Cte_Componente_Valor, o participante redespachado e o tipo do frete do redespacho (IND_FRT_RED).
4. Municípios sentinela. 9999999 (exterior) e 9999998 (origem do CT-e simplificado, D100.24) não têm lugar. Cad_Municipio.Codigo_IBGE exige UF pelos 2 primeiros dígitos. O campo 25 do D100 não aceita 9999998 e, de 2027 em diante, o guia veda o 9999998; isso deve estar em Cad_Obrigacao_Leiaute_Campo.Valores_Validos com vigência e não em código.
5. BP-e (63): sem estrutura para tipo de BP-e (TP_CT-e do D100), origem e destino, e para a regra do D101 (obrigatório no BP-e interestadual). Só importa se o Mlegate emitir passagem.
6. Cad_Obrigacao_Leiaute_Campo.Eh_Obrigatorio é um único booleano. O guia tem obrigatoriedade separada para Entradas e Saídas e a condicional "OC" (por exemplo D100.24 e .25, D700.31 N na entrada e O na saída, D500.24 OC e O, todo o D130 a D420 "Não" na entrada). Falta onde guardar a coluna de entrada e a de saída.
7. D700 saída: modelo, série e número do documento 21 ou 22 substituído em Mov_Nota_Fiscal_Saida_Referenciada. Efeito colateral na emissão da NFCom de substituição.
8. D500, D510 e D530 de saída (modelos 21 e 22): TP_ASSINANTE (domínio 1 a 6 próprio), COD_PART do D510 e o terminal faturado do D530 só existem para NFCom. Só entra se o Mlegate escriturar saída 21 e 22.
9. D695 (Convênio ICMS 115/03): nenhuma entidade do arquivo mestre. D696 sem vínculo com o intervalo. Só se o Mlegate for sujeito ao convênio.
10. ECF no Bloco D e bilhetes (D365, D370, D390, D400 a D420, D310): sem totalizador parcial nem ICMS na Redução Z, sem município de origem do bilhete, sem vínculo bilhete e RMD. Só se o Mlegate presta transporte de passageiros; entram pelo parâmetro de habilitação por empresa.
11. D160 a D162 (só CTRC 08 e 8B): faltam DESPACHO, QTD_VOL e PESO_LIQ por documento transportado. Sem efeito prático se o Mlegate não escritura CTRC em papel.
12. Fora do Bloco D, mas visto no caminho: nenhum registro de totalizador parcial de ICMS da Redução Z (C420, C490), pois Mov_Ecf_Reducao_Z_Tributo só tem PIS e Cofins.

Registros sem efeito prático por serem de 2018 para trás (não contam como lacuna): D110, D120, D140, D150, D170, D180 e D160 a D162 para os modelos 09, 10, 11, 26 e 27.

##### Dúvidas

1. O Mlegate presta ou lança transporte de passageiros (13 a 16, 18, 2E, BP-e), serviço 21 e 22 de saída ou arquivos do Convênio 115? Se não, vale declarar esses registros fora de escopo, sem lançar como lacuna. D300 e D301 só ficam COBERTO-DERIVADO se o bilhete individual for lançado como nota de saída; o dicionário não afirma isso.
2. Enumerações cortadas no dict_dump.txt: Mov_Cte.Tipo_Cte (a lista parece ter "anulacao", "substituto" e "substituicao", e a descrição diz que o schema 4.00 só tem 0, 1, 3, 4, 5, 6) e Tipo_Referencia das duas Referenciada. Confirmar o mapa para TP_CT-e e que a entrada também aceita CT-e substituído (hoje só a saída lista cte_substituido; a entrada tem "substituicao" genérico).
3. ID_Modalidade_Frete (domínio modalidade_frete) é o modFrete da NF-e (emitente, destinatário, terceiros, sem frete). O D100.IND_FRT tem 0, 1, 2, 9 com outro significado (0 emitente, 1 destinatário/remetente, 2 terceiros, 9 sem frete). Confirmar se o mesmo domínio serve ou se precisa de mapa por modelo (Mov_Cte.Papel_Tomador ajuda).
4. 9999999 e 9999998 em Cad_Municipio: a descrição de Mov_Cte.ID_Municipio_Envio diz "9999999 nas operações com o exterior", mas Cad_Municipio.Codigo_IBGE exige 2 dígitos de UF. Como o código entra? (lacuna 4)
5. Carga de Cad_Modelo_Documento_Fiscal_Codigo para o COD_MOD do Bloco D: 08, 8B, 13 a 16, 18, 21, 22, 2E, 57, 62, 63, 67 (e 07, 09, 10, 11, 26, 27 apenas com vigência até 2018). A estrutura permite; não vi a carga. Subserie é descrita para C395, C500 e C600 e precisa valer também para D100, D400 e D500.
6. Cad_Equipamento_Fiscal.ID_Modelo_Documento descreve "02, 2D, 59 ou 65"; o D350 usa 2E, 13, 14, 15 e 16. Um ECF que emite mais de um modelo precisa de mais de uma linha D350.
7. Cad_Nfcom_Classificacao_Servico: os cClass 110, 120 e 130 (excluídos dos totais de entrada do D700) correspondem aos flags Indicador_Faturamento_Centralizado, Indicador_Cofaturamento e Indicador_Ressarcimento? Se não, falta um atributo de grupo do cClass. O mesmo vale para DED, que o guia amarra ao "grupo 590" enquanto a tabela usa Natureza_Valor (código iniciado por 5 deduz).
8. Parâmetros por UF com vigência (em Cad_Obrigacao_Parametro_Definicao): "a UF manda escriturar a NFCom de saída de forma consolidada (D750) ou individual (D700)"; "empresa não obrigada ao Convênio 115 escritura 21 e 22 por D500 ou por D600"; "o Mlegate está sujeito ao Convênio 115". Não vi a definição desses parâmetros; a estrutura comporta.
9. D190.COD_OBS: a observação está por nota (Mov_Nota_Observacao_Lancamento), e o D190 pede o COD_OBS por combinação de CST, CFOP e alíquota. Com várias observações na mesma nota, qual vai para qual linha analítica? Falta uma regra ou um vínculo com o item.
10. D700 NFCom de ajuste de entrada: COD_PART deve apontar o próprio informante. Mov_Nota_Fiscal_Entrada.ID_Participante_Fornecedor é obrigatório; confirmar que a própria filial existe como participante (0150).
11. As descrições de ID_Tipo_Receita_Comunicacao, ID_Classificacao_Item_Utilidade (D600, D601, D605), Mov_Ecf_Reducao_Z (C405) e Mov_Ecf_Reducao_Z_Tributo (C481 e C485) citam só registros da EFD-Contribuições ou do Bloco C. Confirmar que os mesmos campos alimentam D510, D610, D355 e D360 da EFD-ICMS/IPI e acrescentar os registros às descrições.
12. D100.SER: "se não existir série para CT-e, informar 000". Esse valor padrão precisa ser parâmetro com vigência (regra 3) ou vir sempre da chave de acesso. No CT-e recebido a série vem na chave; no emitido vem de Cad_Serie_Documento_Fiscal.
13. MDF-e não tem registro no Bloco D. Entrou na conferência só como origem opcional de VEIC_ID e UF_ID (Mov_Mdfe_Documento liga a chave do CT-e ao veículo de tração).


# Anexo E — Blocos E e K


Fontes: /tmp/efd324.txt (leiaute campo a campo, linhas 13895-15760 para o E e 16542-17780 para o K), guide_EK.txt, dict_dump.txt.
Regras aplicadas: (1) o ERP só registra, o arquivo é gerado; (2) totais, abertura e encerramento são COBERTO-DERIVADO se a origem existe; (3) parâmetros com vigência e sem valor oculto.

Limitação da fonte: o dict_dump.txt corta o tipo em cerca de 80 caracteres e a descrição em cerca de 200. As listas de enumeração longas ficaram truncadas (Cad_Icms_Codigo_Ajuste.Natureza, Mov_Producao_Correcao.Origem_Correcao, Mov_Ordem_Producao_Apontamento.Tipo_Registro_Bloco_K, Mov_Apuracao_Ajuste_Detalhe.Tipo_Documento_Vinculado). Admiti que cobrem os valores citados na descrição ("1 a 9", "0 a 3 e 9"), mas não consegui conferir um a um. Para K200/Propriedade e para a industrialização por encomenda li também os documentos 04 e 06 do Project (busca).

Correções de premissa sobre o Guia 3.2.4:
- IND_BENEFICIO só existe em E111 (campo 05), E220 (campo 05), 1921 (campo 05), C197, C597, D197 e D737 (campo 09), e vale a partir do período de janeiro de 2027. O E311 não tem esse campo.
- MES_REF é o campo 10 de E116, E250 e E316 (obrigatório desde 2011). Não é novidade do E116 apenas.
- CHV_DOCe é o campo 10 do E113 e do E240, e o campo 07 do E313. O E531 usa CHV_NFE (campo 10, só modelo 55).

##### 1. Bloco E

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| E001 | Abertura do bloco E | COBERTO-DERIVADO | IND_MOV sai da existência de apuração de ICMS/IPI (Mov_Apuracao_Icms_Proprio, _St, _Difal, Mov_Apuracao_Ipi) | nenhum |
| E100 | Período da apuração do ICMS | COBERTO-DERIVADO | Mov_Apuracao_Icms_Proprio.Competencia (DT_INI e DT_FIN = mês) | só existe período mensal; sem lacuna para apuração mensal (ver dúvida D3) |
| E110 | Apuração do ICMS - operações próprias (15 campos) | COBERTO | Mov_Apuracao_Icms_Proprio: Total_Debitos, Ajustes_Debito_Documento, Ajustes_Debito, Estornos_Credito, Total_Creditos, Ajustes_Credito_Documento, Ajustes_Credito, Estornos_Debito, Saldo_Credor_Anterior, Saldo_Apurado, Deducoes, Icms_Recolher, Saldo_Credor_Transportar, Debitos_Especiais. As validações da 3.2.3 têm origem: documentos em Mov_Apuracao_Tributo_Item (com ID_Situacao_Documento para COD_SIT 01, 07 e 10), C197/D197 em Mov_Nota_Ajuste_Documento (3º e 4º caracteres do código em Cad_Icms_Codigo_Ajuste.Natureza e Indicador_Subapuracao) e E111 em Mov_Apuracao_Ajuste | nenhum campo. Regras de cálculo sem parâmetro explícito: ver D1 |
| E111 | Ajuste/benefício/incentivo da apuração | PARCIAL | Mov_Apuracao_Ajuste (Tipo_Apuracao = icms_proprio) + Cad_Icms_Codigo_Ajuste: COD_AJ_APUR (Codigo), DESCR_COMPL_AJ, VL_AJ_APUR | IND_BENEFICIO (campo 05, obrigatório, valores 0/1/2/3/9, LC 214/2025 art. 385 V a/b/c, a partir de 01/2027). Não existe em Mov_Apuracao_Ajuste, Cad_Icms_Codigo_Ajuste nem Cad_Beneficio_Fiscal_Icms |
| E112 | Informações adicionais dos ajustes | COBERTO | Mov_Apuracao_Ajuste_Detalhe: Numero_Documento_Arrecadacao (NUM_DA), Numero_Processo (até 60), Origem_Processo (0/1/2/9), Descricao_Processo (PROC), Texto_Complementar | nenhum |
| E113 | Identificação dos documentos fiscais do ajuste | PARCIAL (só no caso de documento fora do ERP) | Mov_Apuracao_Ajuste_Documento: ID_Documento_Fiscal ou Item de origem (dá COD_PART, COD_MOD, SER, SUB, NUM_DOC, DT_DOC e COD_ITEM), Valor (VL_AJ_ITEM), Chave_Documento (código até 50, texto; CHV_DOCe tem 44 posições, o gerador precisa validar o tamanho e o DV) | Quando só há Chave_Documento (documento de terceiro ou fora do ERP): COD_PART, COD_MOD, SER, SUB, NUM_DOC e DT_DOC. A chave só dá modelo, série, número e AAMM, não o dia de emissão |
| E115 | Valores declaratórios | COBERTO | Mov_Apuracao_Informacao_Adicional: COD_INF_ADIC (Cad_Classe_Sistema, tabela 5.2), Valor_Informacao, Descricao_Complementar | nenhum (ver D6 sobre UF da tabela 5.2) |
| E116 | Obrigações do ICMS recolhido ou a recolher | PARCIAL | Mov_Apuracao_Obrigacao_Recolher + Cad_Icms_Obrigacao_Recolher: COD_OR, COD_REC (Codigo_Receita), VL_OR (Valor), DT_VCTO (Data_Vencimento), MES_REF (Mes_Referencia), NUM_PROC | IND_PROC, PROC e TXT_COMPL. NUM_PROC está com até 15 posições (o Guia admite 60). MES_REF está como opcional "quando a UF exige", mas o Guia o exige sempre desde 2011 |
| E200 | Período da apuração do ICMS-ST | COBERTO-DERIVADO | Mov_Apuracao_Icms_St.ID_Estado + Competencia | nenhum |
| E210 | Apuração do ICMS-ST (15 campos) | COBERTO | Mov_Apuracao_Icms_St: Saldo_Credor_Anterior, Devolucoes, Ressarcimentos (de Mov_Icms_St_Ressarcimento), Outros_Creditos, Ajustes_Credito_Documento, Icms_Retido, Outros_Debitos, Ajustes_Debito_Documento, Saldo_Devedor, Deducoes, Icms_Recolher, Saldo_Credor_Transportar, Debitos_Especiais | IND_MOV_ST não é campo, mas é derivável (existência de operação com ST na UF e no período) |
| E220 | Ajuste/benefício/incentivo ICMS-ST | PARCIAL | Mov_Apuracao_Ajuste (Tipo_Apuracao = icms_st) | IND_BENEFICIO (igual ao E111) |
| E230 | Informações adicionais dos ajustes ST | COBERTO | Mov_Apuracao_Ajuste_Detalhe | nenhum |
| E240 | Documentos fiscais dos ajustes ST | PARCIAL (só no caso de documento fora do ERP) | Mov_Apuracao_Ajuste_Documento | Mesmos campos do E113. Aqui COD_PART é obrigatório no Guia |
| E250 | Obrigações do ICMS-ST a recolher | PARCIAL | Mov_Apuracao_Obrigacao_Recolher (Tipo_Apuracao = icms_st) + Cad_Icms_Obrigacao_Recolher (COD_REC da UF do substituído) | IND_PROC, PROC, TXT_COMPL; NUM_PROC com tamanho 15 em vez de 60; MES_REF opcional em vez de obrigatório |
| E300 | Período do DIFAL/FCP por UF | COBERTO-DERIVADO | Mov_Apuracao_Icms_Difal.ID_Estado_Destino + Competencia | nenhum (o nome do campo diz "destino" e o E300 também aceita UF de origem, ver D5) |
| E310 | Apuração do FCP e DIFAL (21 campos, leiaute desde 2017) | COBERTO | Mov_Apuracao_Icms_Difal: Indicador_Movimento (IND_MOV_FCP_DIFAL) e as colunas Difal_* e Fcp_* (saldo anterior, débitos, outros débitos, créditos, outros créditos, saldo devedor antes das deduções, deduções, a recolher, saldo a transportar, débitos especiais). Totais de C101/D101 vêm de Mov_Apuracao_Tributo_Item.ID_Estado_Destino | nenhum |
| E311 | Ajuste da apuração FCP/DIFAL | COBERTO | Mov_Apuracao_Ajuste (Tipo_Apuracao = icms_difal; 3º caractere do código 2 = DIFAL, 3 = FCP, em Cad_Icms_Codigo_Ajuste.Tipo_Apuracao difal/fcp) | nenhum. O E311 não tem IND_BENEFICIO no Guia 3.2.4 |
| E312 | Informações adicionais dos ajustes DIFAL/FCP | COBERTO | Mov_Apuracao_Ajuste_Detalhe | nenhum |
| E313 | Documentos fiscais dos ajustes DIFAL/FCP | PARCIAL (só no caso de documento fora do ERP) | Mov_Apuracao_Ajuste_Documento (CHV_DOCe no campo 07) | Mesmos campos do E113 |
| E316 | Obrigações DIFAL/FCP a recolher | PARCIAL | Mov_Apuracao_Obrigacao_Recolher (Tipo_Apuracao = icms_difal) | IND_PROC, PROC, TXT_COMPL; NUM_PROC 15 em vez de 60; MES_REF opcional em vez de obrigatório |
| E500 | Período da apuração do IPI | PARCIAL | Mov_Apuracao_Ipi.Tipo_Periodo (IND_APUR) e Competencia | DT_INI e DT_FIN do decêndio. Só há Competencia (mês); não dá para guardar os até três decêndios do mês |
| E510 | Consolidação dos valores do IPI | COBERTO-DERIVADO | Itens de nota (CFOP em ID_CFOP_Saida e ID_CFOP_Entrada; Valor_Total do item) + Mov_Apuracao_Tributo_Item com ID_Imposto = IPI (ID_Cst = CST_IPI, Base_Calculo_Efetiva, Valor_Tributo), somados por CFOP + CST | nenhum |
| E520 | Apuração do IPI (7 campos) | COBERTO-DERIVADO, com defeitos de rótulo | Mov_Apuracao_Ipi: Saldo_Credor_Anterior, Debitos, Creditos, Estornos, Ipi_Recolher, Saldo_Credor_Transportar. VL_OD_IPI e VL_OC_IPI vêm da soma de Mov_Apuracao_Ajuste (Tipo_Apuracao = ipi) por natureza (IND_AJ 0 e 1) | Não falta dado, mas: (a) a coluna Estornos diz guardar VL_OD_IPI e VL_OC_IPI juntos, e são dois valores distintos que incluem créditos presumidos e outros ajustes; (b) as descrições trocaram os campos: Ipi_Recolher aparece como VL_SC_IPI (saldo credor a transportar) e Saldo_Credor_Transportar como VL_SD_IPI (saldo devedor a recolher). Os nomes estão certos e os códigos do Guia estão invertidos |
| E530 | Ajustes da apuração do IPI | COBERTO | Mov_Apuracao_Ajuste (Tipo_Apuracao = ipi; IND_AJ pela Natureza débito/crédito do código; VL_AJ) + Cad_Icms_Codigo_Ajuste (COD_AJ de 3 posições, tabela 4.5.4) + Mov_Apuracao_Ajuste_Detalhe (IND_DOC em Tipo_Documento_Vinculado, NUM_DOC em Numero_Documento_Vinculado) | Nenhum campo. Ressalvas de obrigatoriedade em D7 (IND_DOC e DESCR_AJ são obrigatórios no Guia e aqui são opcionais; Tabela_Origem não tem a tabela 4.5.4) |
| E531 | Documentos fiscais dos ajustes do IPI (modelos 01 e 55) | PARCIAL (só no caso de documento fora do ERP) | Mov_Apuracao_Ajuste_Documento (CHV_NFE em Chave_Documento) | Mesmos campos do E113. No modelo 01 não há chave, então COD_PART, SER, SUB, NUM_DOC e DT_DOC dependem de haver nota no ERP |
| E990 | Encerramento do bloco E | COBERTO-DERIVADO | contagem de linhas do arquivo gerado (Mov_Escrituracao_Arquivo) | nenhum |

##### 2. Bloco K

| Registro | Nome | Veredito | Onde está | Campos que faltam |
|---|---|---|---|---|
| K001 | Abertura do bloco K | COBERTO-DERIVADO | IND_MOV = existe K100 com filho; habilitação em Cad_Filial_Perfil_Fiscal.Tipo_Leiaute_Bloco_K (vazio = não entrega) e Cad_Empresa_Modulo_Opcional | nenhum |
| K010 | Tipo de leiaute | COBERTO | Cad_Filial_Perfil_Fiscal.Tipo_Leiaute_Bloco_K {simplificado, completo, restrito_saldos}, com vigência | nenhum. A tabela de obrigatoriedade dos registros por leiaute não está em nenhuma entidade (ver L5) |
| K100 | Período de apuração ICMS/IPI | COBERTO-DERIVADO no caso mensal; PARCIAL se o IPI for decendial | Competencia do ICMS (mês). O período mais curto só aparece em Mov_Ordem_Producao_Apontamento.Data_Inicio_Periodo e Data_Fim_Periodo | Entidade de período decendial (mesma lacuna do E500). Sem apontamento no período, o K100 do decêndio não tem de onde sair, e o K200 por decêndio depende do saldo calculado até a data |
| K200 | Estoque escriturado | PARCIAL | Mov_Saldo_Estoque (Quantidade_Final por local, posição, produto, lote, competência; Propriedade = IND_EST; ID_Participante_Proprietario = COD_PART). O tipo de item vem de Cad_Produto_Servico (TIPO_ITEM) | IND_EST = 0 está coberto. IND_EST = 1 e 2 não têm origem: (a) o material do encomendante (documento 06, seção 8.2) nunca entra em Mov_Estoque_Movimento ("a Mlegate nunca é dona desse material"; "saldo de material de terceiro fica deliberadamente fora"), contradizendo o documento 04, que diz "entra no saldo sem valorização"; (b) o material próprio remetido ao industrializador sai por nota de remessa e não entra em local do tipo "terceiros". Mov_Estoque_Movimento_Item não tem Propriedade nem participante. Ver L2 |
| K210 | Desmontagem - item de origem | COBERTO | Mov_Producao_Desmontagem: Data_Inicio_Os, Data_Fim_Os, Codigo_Documento_Os, ID_Produto_Servico_Origem, Quantidade_Origem (6 casas) | nenhum. No Guia DT_INI_OS e COD_DOC_OS são condicionais e aqui são obrigatórios (ver D8) |
| K215 | Desmontagem - itens de destino | COBERTO | Mov_Producao_Desmontagem_Destino: ID_Produto_Servico_Destino, Quantidade_Destino | nenhum |
| K220 | Outras movimentações internas | COBERTO | Mov_Estoque_Reclassificacao: Data_Movimento, Produto_Origem, Produto_Destino, Quantidade_Origem, Quantidade_Destino | nenhum |
| K230 | Itens produzidos | COBERTO | Mov_Ordem_Producao (Data_Abertura = DT_INI_OP, Data_Conclusao = DT_FIN_OP, Codigo_Op_Sped = COD_DOC_OP até 30, ID_Produto_Servico) + Mov_Ordem_Producao_Apontamento (Tipo_Registro_Bloco_K = producao_k230, Quantidade_Produzida_Periodo = QTD_ENC, Encerrada) | nenhum. O parâmetro "informar por OP ou por período" não existe (ver D9) |
| K235 | Insumos consumidos | PARCIAL | Mov_Ordem_Producao_Item (COD_ITEM = ID_Produto_Servico_Componente, QTD = Quantidade_Consumida); DT_SAÍDA vem da data do movimento de estoque ligado (ID_Movimento_Estoque_Item_Saida) | DT_SAÍDA no caso da OP com Tipo_Ordem = industrializacao_terceiro: o material do encomendante não tem movimento de estoque, só a nota de remessa recebida, e o consumo não tem data. COD_INS_SUBST é descontinuado desde 2022 e não é necessário |
| K250 | Industrialização por terceiros - itens produzidos | COBERTO | Mov_Ordem_Producao_Apontamento (Tipo = terceiros_k250, Data_Producao_Terceiro = DT_PROD, Quantidade_Produzida_Periodo, Variacao_Estoque_Terceiro) | nenhum |
| K255 | Industrialização em terceiros - insumos consumidos | PARCIAL | Mov_Ordem_Producao_Item com Terceirizado = verdadeiro (COD_ITEM, QTD, nota de remessa e de retorno) | DT_CONS (data do reconhecimento do consumo). A saída por remessa dá a data da nota, não a do reconhecimento do consumo. Pode ser a Data_Producao_Terceiro, mas o dicionário não diz |
| K260 | Reprocessamento/reparo | COBERTO | Mov_Producao_Reprocesso: Codigo_Documento_Op_Os, ID_Produto_Servico, Data_Saida, Quantidade_Saida, Data_Retorno, Quantidade_Retorno | nenhum |
| K265 | Reprocessamento - mercadorias consumidas e/ou retornadas | COBERTO | Mov_Producao_Reprocesso_Item: ID_Produto_Servico_Insumo, Quantidade_Consumida, Quantidade_Retornada | nenhum |
| K270 | Correção de apontamento (K210, K220, K230, K250, K260, K291, K292, K301, K302) | COBERTO | Mov_Producao_Correcao (Tipo_Registro_Correcao = apontamento_producao; Origem_Correcao = ORIGEM 1 a 9; Data_Inicio_Apontamento, Data_Fim_Apontamento; ID_OP ou Codigo_Documento_Os; ID_Produto_Servico; Quantidade_Corrigida_Positiva e Negativa; vínculo com os dois inventários) | nenhum |
| K275 | Correção de apontamento e retorno de insumos | COBERTO | Mov_Producao_Correcao com Tipo_Registro_Correcao = insumo_ou_retorno e ID_Correcao_Principal apontando o K270 | COD_INS_SUBST sem campo, mas o registro 0210 foi descontinuado em 2023 (ver D10) |
| K280 | Correção de apontamento - estoque escriturado | COBERTO | Mov_Producao_Correcao com Tipo_Registro_Correcao = estoque: Data_Estoque_Corrigido, ID_Produto_Servico, Quantidades, Propriedade (IND_EST), ID_Participante_Proprietario | nenhum |
| K290 | Produção conjunta - ordem de produção | COBERTO | Mov_Ordem_Producao (mesmos campos do K230) + Mov_Ordem_Producao_Subproduto.Eh_Coproduto + Apontamento com Tipo = producao_conjunta_k290 | nenhum |
| K291 | Produção conjunta - itens produzidos | COBERTO | Mov_Ordem_Producao_Apontamento.ID_Produto_Servico (coproduto) + Quantidade_Produzida_Periodo | nenhum |
| K292 | Produção conjunta - insumos consumidos | COBERTO | Mov_Ordem_Producao_Item (COD_ITEM, QTD) | nenhum |
| K300 | Produção conjunta - industrialização por terceiros | COBERTO | Apontamento com Data_Producao_Terceiro (DT_PROD) | nenhum |
| K301 | Produção conjunta por terceiros - itens produzidos | COBERTO | Apontamento (terceiros em produção conjunta): ID_Produto_Servico, Quantidade_Produzida_Periodo, Variacao_Estoque_Terceiro | nenhum |
| K302 | Produção conjunta por terceiros - insumos consumidos | COBERTO | Mov_Ordem_Producao_Item (Terceirizado = verdadeiro) | nenhum (K302 não tem campo de data) |
| K990 | Encerramento do bloco K | COBERTO-DERIVADO | contagem de linhas do arquivo gerado | nenhum |

##### 3. Lacunas reais

L1. IND_BENEFICIO (E111 e E220, obrigatório, valores 0/1/2/3/9, vigente a partir de 01/2027). Não há campo no ajuste, no código de ajuste nem no cadastro de benefício. Proposta: Cad_Icms_Codigo_Ajuste.Indicador_Beneficio (padrão por código e UF, com vigência a partir de 01/01/2027) e Mov_Apuracao_Ajuste.Indicador_Beneficio (obrigatório, padrão 0, sobrescreve o do código). O mesmo campo falta em Mov_Nota_Ajuste_Documento (C197, C597, D197, D737, fora do escopo deste exame) e no ajuste da sub-apuração (1921, que usa Mov_Apuracao_Ajuste com icms_subapuracao).

L2. K200 com IND_EST = 1 e 2. O saldo tem as colunas Propriedade e participante, mas nada as alimenta nos dois casos de industrialização por encomenda: material do encomendante em poder da Mlegate (documento 06, seção 8.2, deixa o saldo fora do Estoque) e material próprio remetido para industrializar (a remessa baixa o saldo próprio e não entra em local "terceiros"). Também há contradição entre os documentos 04 ("entra no saldo sem valorização") e 06 ("deliberadamente fora"). É preciso decidir entre (a) movimento de estoque de propriedade de terceiros, sem valor, com participante, ou (b) saldo calculado por nota (remessa menos consumo menos retorno). Em qualquer das duas, Mov_Estoque_Movimento_Item precisa carregar Propriedade e participante.

L3. K235 (DT_SAÍDA) e K255 (DT_CONS) sem origem de data no consumo de material de terceiros e no consumo em terceiros. Proposta: campo Data_Consumo em Mov_Ordem_Producao_Item, obrigatório quando o item não tem ID_Movimento_Estoque_Item_Saida.

L4. Período decendial do IPI (E500, K100, K200). Mov_Apuracao_Ipi só tem Competencia. Proposta: Data_Inicio_Periodo e Data_Fim_Periodo em Mov_Apuracao_Ipi (ou entidade de período de apuração da filial) e usar a mesma fonte no K100.

L5. Parâmetro da obrigatoriedade dos registros do Bloco K por tipo de leiaute (tabela do K010: K210, K215, K235, K255, K260, K265, K275, K292, K302 não exigidos no simplificado; K230 com quantidade zero também dispensado; leiaute 2 só saldos). Cad_Obrigacao_Leiaute_Registro tem só Ocorrencia. A regra ficaria escondida no código; deveria ser parâmetro com vigência (registro x tipo de leiaute x obrigatório).

L6. E116, E250 e E316: faltam IND_PROC, PROC e TXT_COMPL em Mov_Apuracao_Obrigacao_Recolher; Numero_Processo está com 15 posições (Guia: 60); Mes_Referencia deve ser obrigatório. Sem IND_PROC e PROC não é possível cumprir a validação "NUM_PROC preenchido exige IND_PROC e PROC".

L7. E113, E240, E313 e E531 com documento que não está no ERP. Faltam em Mov_Apuracao_Ajuste_Documento: modelo, série, subsérie, número, data de emissão e participante (obrigatórios quando não há ID_Documento_Fiscal nem item de origem). A chave não supre a data de emissão. Também não há vínculo com o cabeçalho de nota de entrada ou saída (só item ou Mov_Documento_Fiscal); ajuste sem COD_ITEM em nota não eletrônica não tem como apontar a nota (ver D4).

L8. Rótulos trocados e coluna ambígua em Mov_Apuracao_Ipi (ver E520): Ipi_Recolher = VL_SD_IPI; Saldo_Credor_Transportar = VL_SC_IPI; separar Estornos em Outros_Debitos (VL_OD_IPI) e Outros_Creditos (VL_OC_IPI), ou declarar que são derivados de Mov_Apuracao_Ajuste.

##### 4. Dúvidas

D1. Regras de cálculo do E110 que dependem de parâmetro e não aparecem no dicionário: CFOP 5605 e 1605 (transferência de saldo devedor, excluído ou incluído em débitos e créditos); o envio de COD_SIT 01, 07 e 10 ao DEB_ESP e ao primeiro período; para o DIFAL, o envio ao primeiro período de apuração. Cad_CFOP não tem indicador para 5605/1605. É regra de geração ou deve ser parâmetro com vigência?

D2. IND_MOV_ST (E210) fica derivado e não gravado, enquanto o DIFAL grava Indicador_Movimento. Confirmar que o critério de derivação fica documentado (qualquer valor de ST diferente de zero, ou qualquer documento com ST na UF?). O mesmo vale para IND_MOV do E001 e do K001.

D3. E100 e E200/E300 aceitam mais de um período por mês quando a UF assim determina. O dicionário só tem competência mensal. Há UF de interesse com período menor?

D4. Mov_Apuracao_Ajuste_Documento aponta o documento só por Mov_Documento_Fiscal (opcional) ou item. Toda nota (inclusive modelo 01) tem Mov_Documento_Fiscal? Se não, o ajuste de documento inteiro (sem COD_ITEM) de nota não eletrônica fica sem vínculo.

D5. Mov_Apuracao_Icms_Difal.ID_Estado_Destino: o E300 aceita a UF de origem (entradas e devoluções, até 2018 obrigatória). O nome do campo restringe o conceito.

D6. E115: o COD_INF_ADIC é da tabela 5.2 de cada SEFAZ, modelada como domínio de Cad_Classe_Sistema, que não tem coluna de UF. Funciona se o código já carrega a UF no prefixo; confirmar.

D7. E530: IND_DOC e DESCR_AJ são obrigatórios; Mov_Apuracao_Ajuste_Detalhe e Descricao_Complementar são opcionais. Exigir quando Tipo_Apuracao = ipi. Cad_Icms_Codigo_Ajuste.Tabela_Origem só tem apuracao_5_1_1 e documento_5_3; falta a tabela 4.5.4 do IPI (códigos de 3 posições).

D8. K210/K215: no Guia a ordem de serviço é opcional (e o K215 é obrigatório no controle sem OS, com saída e entrada no mesmo período). No dicionário Codigo_Documento_Os e Data_Inicio_Os são obrigatórios. Se o ERP sempre gera um código interno de OS, o arquivo sempre informa OS e o K215 pode vir em período posterior; confirmar que é a intenção. O Guia também não diz se o K210 de OS aberta se repete nos meses seguintes (como o K230), e não há apontamento por período para a desmontagem.

D9. K230/K290: o Guia permite informar a produção por período, sem OP (DT_INI_OP, DT_FIN_OP e COD_DOC_OP em branco). O dicionário exige ID_OP no apontamento. A escolha "por OP ou por período" é do contribuinte; não há parâmetro dela.

D10. K275.COD_INS_SUBST não tem campo. O Guia 3.2.4 só manda não preencher o campo nos K235 e K255 (a partir de 2022), mas o 0210 foi descontinuado em 2023. Confirmar que o campo pode ser considerado obsoleto.

D11. Cad_Icms_Obrigacao_Recolher tem identidade (UF, obrigação) e um só Codigo_Receita por vigência. Há UF com mais de um COD_REC para o mesmo COD_OR (por atividade ou por tipo de débito)? Se houver, a identidade precisa incluir o código de receita.

D12. Mov_Saldo_Estoque é único por (local, posição, produto, lote, competência); Propriedade e participante não entram na chave. Dois proprietários no mesmo local para o mesmo item, ou estoque próprio e de terceiro no mesmo local, colidem. Também o K200 usa 3 casas decimais e os demais registros do K usam 6; conferir a precisão das colunas de quantidade.


# Anexo F — Bloco 1


Método: li as descrições do guia_bloco_1.txt e comparei com o guia completo (/tmp/efd324.txt) e com dict_dump.txt.
Aviso sobre o guia_bloco_1.txt: a extração compacta perdeu campos que existem no guia completo. Conferi contra o guia completo: 1200.07 SLD_CRED_FIM, 1210.05 CHV_DOCe, 1391.11 SAÍDAS, 1923.10 CHV_DOCe e 1926.10 MES_REF. Os campos deste aviso já entram nos vereditos abaixo.

Legenda: COBERTO / COBERTO-DERIVADO (origem existe, o registro é montado na geração) / PARCIAL (faltam campos) / AUSENTE (não há onde guardar).
Regra aplicada: "O ERP só registra", sem tabela espelho por registro. Registro setorial AUSENTE conta como lacuna a registrar, por causa da aprovação de 05/10/2026 (parâmetro de habilitação por empresa).

##### Tabela por registro

| Registro | Nome | Veredito | Onde está | Campos que faltam |
| ---|---|---|---|--- |
| 1001 | Abertura do Bloco 1 | COBERTO-DERIVADO | IND_MOV é calculado: há dados em algum registro do bloco | nenhum |
| 1010 | Obrigatoriedade de registros | COBERTO-DERIVADO | Cad_Empresa_Modulo_Opcional (empresa e filial, com vigência, ID_Modulo_Opcional do domínio aberto modulo_fiscal_opcional, Habilitado, Ato_Habilitacao). Cada IND_* sai da habilitação mais a existência de dados no período. IND_EXP vem de haver averbação no mês | nenhum campo. Ver Dúvida 1: o domínio precisa de um valor por indicador (CCRF, COMB, USINA, VA, EE, CART, FORM, AER, GIAF1/3/4, REST_RESSARC) |
| 1100 | Informações sobre exportação | PARCIAL | Mov_Nota_Fiscal_Saida_Item_Exportacao.Numero_Registro_Exportacao (NRO_RE; também Numero_Drawback e Chave_Nota_Exportacao). Mov_Dfe_Evento_Item: Numero_Due (NRO_DE, 14 posições), Data_Hora_Averbacao (DT_AVB) e Data_Hora_Embarque, mas só quando o evento de averbação 790700 foi recebido. PAIS sai de Cad_Participante_Endereco.ID_Pais do destinatário. NAT_EXP sai de haver ou não Chave_Nota_Exportacao (indireta) | IND_DOC (DE/DSE/DU-E); DT_DE; DT_RE; CHC_EMB (nº do conhecimento de embarque); DT_CHC; TP_CHC (tipo do conhecimento, tabela de 20 códigos). NRO_DE e DT_AVB dependem do evento 790700; sem ele não há onde guardar (a coluna "Onde está" mostra só o que existe) |
| 1105 | Documentos fiscais de exportação | COBERTO-DERIVADO | Mov_Nota_Fiscal_Saida e Mov_Nota_Fiscal_Saida_Item, ligados pelo Item_Exportacao.ID_Item. COD_MOD, SERIE, NUM_DOC, CHV_NFE (Chave_Acesso), DT_DOC e COD_ITEM vêm da nota; o vínculo com o 1100 é o Numero_Registro_Exportacao | nenhum |
| 1110 | Exportação indireta, mercadorias de terceiros | PARCIAL | Item_Exportacao.Chave_Nota_Exportacao (CHV_NFE, texto de 44 posições) e Quantidade_Exportada (QTD, opcional). COD_PART, COD_MOD, SER, NUM_DOC e DT_DOC derivam da Mov_Nota_Fiscal_Entrada achada pela chave. UNID vem do item | NR_MEMO (memorando de exportação). Não há referência ao item da entrada para COD_MOD 01, 1B e 04 (sem chave): só existe o campo de chave de 44 posições, então SER/NUM_DOC/DT_DOC/COD_PART dessas notas não têm origem |
| 1200 | Controle de créditos fiscais ICMS | PARCIAL | Mov_Credito_Fiscal (ID_Imposto = ICMS, Valor_Credito, Competencia_Apuracao, Status) e Mov_Credito_Fiscal_Aplicacao (Competencia, Valor_Aplicado). Dão CRED_APR, CRED_UTIL, SLD_CRED e SLD_CRED_FIM por soma | COD_AJ_APUR: nenhum campo liga o crédito a Cad_Icms_Codigo_Ajuste (tabela 5.1.1, código com 4º caractere 9; a Natureza controle_extra_apuracao existe só no cadastro). CRED_RECEB para ICMS: só existe transferência por sucessão (Participante_Cedente/Ato_Societario), não transferência entre estabelecimentos ou de terceiros |
| 1210 | Utilização de créditos fiscais ICMS | PARCIAL | Mov_Credito_Fiscal_Aplicacao (Valor_Aplicado = VL_CRED_UTIL, Competencia) | TIPO_UTIL (tabela 5.5 ou da UF; Forma_Utilizacao é uma lista de PIS/Cofins/CBS, sem os códigos 5.5); NR_DOC; CHV_DOCe (chave NF-e/CT-e/CT-e OS usada na baixa) |
| 1250 | Saldos consolidados restituição, ressarcimento e complementação do ICMS | PARCIAL | Mov_Icms_St_Ressarcimento_Consolidado (Valor_Credito, Valor_Debito, Valor_Total por motivo e mês). O 1250 é a soma dos 1255 | VL_CREDITO_ICMS_OP, VL_ICMS_ST_REST, VL_FCP_ST_REST, VL_ICMS_ST_COMPL e VL_FCP_ST_COMPL não estão abertos: a consolidação só tem Crédito, Débito e Total |
| 1255 | Idem, por motivo | PARCIAL | Mesma entidade, chave por filial, competência e ID_Motivo_Ressarcimento | O guia manda somar os campos VL_UNIT_*_CONV_REST/COMPL × QUANT_CONV dos C181, C185, C330, C380, C430, C480, C815 e C880. No dicionário só há Mov_Icms_St_Ressarcimento (base do C176): faltam QUANT_CONV, unitários de complemento (ICMS-ST e FCP-ST), e o motivo da tabela 5.7 (o domínio motivo_ressarcimento_icms_st é o COD_MOT_RES do C176). Ver Dúvida 3 |
| 1300 | Movimentação diária de combustíveis | PARCIAL | Mov_Estoque_Movimento e Movimento_Item (data/hora, produto, local) dão ESTQ_ABERT, VOL_ENTR e VOL_SAIDAS por dia e produto. Cad_Produto_Anp. Mov_Saldo_Estoque é só mensal | FECH_FISICO (medição física diária), VAL_AJ_PERDA e VAL_AJ_GANHO em litros por dia; saldo diário (o dicionário só guarda saldo mensal) |
| 1310 | Movimentação diária por tanque | AUSENTE | Só existe o texto Combustivel_Numero_Tanque no item da nota (NF-e/NFC-e) | Cadastro de tanque (NUM_TANQUE, CAP_TANQUE, novo em 2026), produto do tanque, medição diária por tanque (ESTQ_ABERT, VOL_ENTR, VOL_DISP, VOL_SAIDAS, ESTQ_ESCR, perda, ganho, FECH_FISICO). Um Cad_Local_Estoque poderia servir de tanque, mas sem capacidade nem aferição |
| 1320 | Volume de vendas por bico | AUSENTE | Só os campos de encerrante inicial e final no item da nota (Combustivel_Encerrante_Inicial/Final, Numero_Bico) | Leitura diária do contador por bico (VAL_ABERT, VAL_FECHA), VOL_AFERI, intervenção (NR_INTERV, MOT_INTERV, NOM_INTERV, CNPJ_INTERV, CPF_INTERV) |
| 1350 | Bombas | AUSENTE | só Combustivel_Numero_Bomba (texto) no item da nota | Cadastro de bomba: SERIE, FABRICANTE, MODELO, TIPO_MEDICAO |
| 1360 | Lacres da bomba | AUSENTE | (Mov_Nota_Fiscal_Saida_Volume_Lacre é lacre de volume de transporte, outra coisa) | NUM_LACRE, DT_APLICACAO, ligados à bomba |
| 1370 | Bicos da bomba | AUSENTE | só Numero_Bico, Numero_Tanque e produto no item da nota | Cadastro bico (NUM_BICO, produto, tanque) ligado à bomba |
| 1390 | Controle de produção de usina | AUSENTE | nada | Cadastro dos produtos da usina por COD_PROD (tabela 5.8, 2 dígitos) |
| 1391 | Produção diária da usina | AUSENTE | nada (Mov_Ordem_Producao não tem estes campos: esmagamento, mel residual, anidro/hidratado, resíduos DDG/WDG/bagaço) | QTD_MOID, ESTQ_INI, QTD_PRODUZ, ENT_ANID_HID, OUTR_ENTR, PERDA, CONS, SAI_ANI_HID, SAÍDAS, ESTQ_FIN, ESTQ_INI_MEL, PROD_DIA_MEL, UTIL_MEL, PROD_ALC_MEL, OBS, COD_ITEM (insumo), TP_RESIDUO, QTD_RESIDUO, QTD_RESIDUO_DDG, QTD_RESIDUO_WDG, QTD_RESIDUO_CANA |
| 1400 | Valores agregados | PARCIAL | Município do participante (Cad_Participante_Endereco, Cad_Municipio) e valores das notas permitem somar por município | Tabela 5.9.1 (itens por UF, COD_ITEM_IPM) e o mapa de CFOP/produto para o item IPM; regra de origem/destino do município (MUN) |
| 1500 | Nota/conta de energia elétrica, saída interestadual | COBERTO-DERIVADO | Mov_Nota_Fiscal_Saida (modelo 06/66; participante, série, número, datas, valores, situação, ID_Observacao para COD_INF) e Mov_Nota_Fiscal_Utilidade com Origem_Tipo = nota_fiscal_saida (COD_CONS via Cad_Faixa_Consumo_Sped, VL_FORN, VL_SERV_NT, VL_TERC, VL_DA, Tipo_Ligacao, Grupo_Tensao) | nenhum campo. Ver Dúvidas 2 e 5 (as marcas "a conferir" em Tipo_Ligacao e Grupo_Tensao; o ERP não emite NF3e de saída, só escritura) |
| 1510 | Itens da nota/conta de energia | PARCIAL | Mov_Nota_Fiscal_Saida_Item: COD_ITEM, QTD, UNID, VL_ITEM, VL_DESC, CST, CFOP, base/alíquota/valor de ICMS e ST, ID_Classificacao_Item_Utilidade (COD_CLASS, tabela 4.4.1), ID_Conta_Contabil (COD_CTA) | IND_REC (0 receita própria, 1 de terceiros; o ID_Tipo_Receita_Comunicacao é do D600 e tem outro domínio); COD_PART do terceiro receptor da receita |
| 1600 | Operações com cartão (válido até 31/12/2021) | COBERTO-DERIVADO | Mov_Nota_Fiscal_Saida_Pagamento (ID_Forma_Pagamento tPag crédito/débito, Valor_Pagamento, ID_Participante_Credenciadora) | nenhum; só histórico anterior a 2022 |
| 1601 | Instrumentos de pagamento eletrônico (desde 2022) | COBERTO-DERIVADO | COD_PART_IP = ID_Participante_Credenciadora; COD_PART_IT = Mov_Nota_Fiscal_Saida.ID_Participante_Intermediador; TOT_VS e TOT_ISS = Valor_Pagamento agrupado por tipo de nota (ICMS x ISS) | nenhum campo. Ver Dúvida 4 sobre TOT_OUTROS e pagamento sem nota |
| 1700 | Documentos fiscais utilizados | AUSENTE | só Cad_Serie_Documento_Fiscal (série, numeração) e Mov_Serie_Documento_Controle (último número) | COD_DISP (00 a 05), NUM_AUT (autorização de impressão, 60 posições), faixa utilizada NUM_DOC_INI e NUM_DOC_FIN, SUB do dispositivo; COD_MOD e SER saem da série |
| 1710 | Documentos cancelados/inutilizados | PARCIAL | Mov_Dfe_Inutilizacao (série, Numero_Inicial/Final) para eletrônicos; Mov_Nota_Fiscal_Saida.Status = cancelada | Para papel: vínculo com a autorização do 1700 e faixa cancelada/inutilizada dentro dela (só depende do 1700) |
| 1800 | DCTA, crédito do ICMS sobre transporte aéreo | AUSENTE | nada | VL_CARGA, VL_PASS, VL_FAT, IND_RAT (8 posições, 6 decimais), VL_ICMS_ANT, VL_BC_ICMS, VL_ICMS_APUR, VL_BC_ICMS_APUR. VL_FAT, IND_RAT e os apurados são cálculo; as bases (créditos e BC) não têm onde ficar |
| 1900 | Indicador de sub-apuração | COBERTO | Mov_Apuracao_Icms_Subapuracao.Indicador_Apuracao_Separada (3 a 8) e Descricao_Apuracao | nenhum |
| 1910 | Período da sub-apuração | COBERTO | Mov_Apuracao_Icms_Subapuracao.Data_Inicio_Periodo/Data_Fim_Periodo | nenhum. Ver Dúvida 6 (cobertura contínua dos períodos) |
| 1920 | Sub-apuração do ICMS | COBERTO | Mov_Apuracao_Icms_Subapuracao: Transferencia_Debitos, Ajustes_Debito, Estornos_Credito, Transferencia_Creditos, Ajustes_Credito, Estornos_Debito, Saldo_Credor_Anterior, Saldo_Devedor_Apurado, Deducoes, Icms_Recolher, Saldo_Credor_Transportar, Debitos_Especiais (os 12 campos) | nenhum |
| 1921 | Ajuste/benefício/incentivo da sub-apuração | PARCIAL | Mov_Apuracao_Ajuste (Tipo_Apuracao = icms_subapuracao): ID_Codigo_Ajuste (COD_AJ_APUR), Descricao_Complementar, Valor_Ajuste | IND_BENEFICIO (0, 1, 2, 3 ou 9; obrigatório O desde 01/2027, repercussão econômica dos benefícios onerosos, arts. 384 a 405 da LC 214/2025). Não existe em nenhum lugar do dicionário (busca por IND_BENEFICIO e repercussão: nenhum resultado) |
| 1922 | Informações adicionais dos ajustes | COBERTO | Mov_Apuracao_Ajuste_Detalhe (NUM_DA, NUM_PROC, IND_PROC, PROC, TXT_COMPL) | nenhum |
| 1923 | Identificação dos documentos fiscais do ajuste | COBERTO-DERIVADO | Mov_Apuracao_Ajuste_Documento (ID_Documento_Fiscal, Chave_Documento, ID_Item_Origem, Valor = VL_AJ_ITEM). COD_PART, COD_MOD, SER, SUB, NUM_DOC, DT_DOC, COD_ITEM e CHV_DOCe saem do documento/item | nenhum campo. Ver Dúvida 7 (documento fora do ERP sem chave) |
| 1925 | Valores declaratórios da sub-apuração | COBERTO | Mov_Apuracao_Informacao_Adicional (Tipo_Apuracao = icms_subapuracao): COD_INF_ADIC, VL_INF_ADIC, DESCR_COMPL_AJ | nenhum |
| 1926 | Obrigações a recolher da sub-apuração | PARCIAL | Mov_Apuracao_Obrigacao_Recolher (Tipo_Apuracao = icms_subapuracao): COD_OR, VL_OR, DT_VCTO, MES_REF (Mes_Referencia), NUM_PROC; COD_REC sai de Cad_Icms_Obrigacao_Recolher.Codigo_Receita | IND_PROC, PROC, TXT_COMPL (só existem no Mov_Apuracao_Ajuste_Detalhe, que é do ajuste). NUM_PROC: o dicionário tem até 15 posições, o guia pede 60 |
| 1960 | GIAF 1 (indústria, crédito presumido, PE) | AUSENTE | nada | IND_AP (tabela de sub-apuração por benefício) e G1_01 a G1_11 |
| 1970 | GIAF 3 (importação) | AUSENTE | nada | IND_AP, G3_01 a G3_08, G3_09 e G3_T (dedução de incentivo) |
| 1975 | GIAF 3, saídas internas por faixa de alíquota | AUSENTE | nada | ALIQ_IMP_BASE, G3_10, G3_11, G3_12 (um registro por alíquota) |
| 1980 | GIAF 4 (central de distribuição) | AUSENTE | nada | IND_AP, G4_01 a G4_12 |
| 1990 | Encerramento do Bloco 1 | COBERTO-DERIVADO | QTD_LIN_1 é contagem na geração | nenhum |

##### Lacunas reais (para registrar)

1. 1921.IND_BENEFICIO (obrigatório O a partir do período 01/2027): não existe em lugar nenhum. O mesmo campo é obrigatório em E111, E220, C197, C597, D197 e D737 no guia (subseção 16), então o buraco está também em Mov_Apuracao_Ajuste (E111, E220, 1921) e em Mov_Nota_Ajuste_Documento (C197, C597, D197, D737). Proposta: campo Indicador_Beneficio (0, 1, 2, 3, 9) nas duas entidades, com sugestão por código de ajuste (parâmetro com vigência em Cad_Icms_Codigo_Ajuste).
2. Exportação (1100): faltam IND_DOC, DT_DE, DT_RE, CHC_EMB, DT_CHC e TP_CHC. NRO_DE e DT_AVB só vêm se o evento 790700 for recebido. 1110: falta NR_MEMO e o vínculo com a entrada para notas sem chave (modelos 01, 1B e 04).
3. Controle de créditos de ICMS (1200/1210): falta o vínculo do crédito com o código de ajuste 5.1.1 (COD_AJ_APUR), CRED_RECEB para transferência entre estabelecimentos ou de terceiros, o tipo de utilização da tabela 5.5 (TIPO_UTIL), NR_DOC e CHV_DOCe.
4. Restituição/ressarcimento/complemento de ST (1250/1255): a consolidação não abre os cinco valores (ICMS próprio, ST e FCP-ST de restituição; ST e FCP-ST de complemento) e não existe a origem C181/C185/C330/C380/C430/C480/C815/C880 (QUANT_CONV e unitários de restituição e complemento) nem a tabela 5.7 de motivos.
5. Combustíveis (1310, 1320, 1350, 1360, 1370, e a parte de medição física e perdas do 1300): sem cadastro de tanque, bomba, lacre, bico, medição diária por tanque, leitura diária por bico, aferição e intervenção. Usina (1390 e 1391): sem nada. Faixa 1700/1710 (papel): sem autorização (COD_DISP, NUM_AUT, faixa). DCTA (1800): sem nada. GIAF 1960, 1970, 1975 e 1980: sem nada. Todos entram pelo parâmetro de habilitação por empresa.
6. Valores agregados (1400): falta a tabela 5.9.1 da UF e o mapa de item IPM.
7. Energia (1510): faltam IND_REC (receita própria ou de terceiro) e COD_PART do terceiro receptor.
8. 1926: faltam IND_PROC, PROC e TXT_COMPL, e NUM_PROC com 60 posições. A mesma entidade serve o E116, que também exige IND_PROC, PROC e TXT_COMPL (fora do Bloco 1, mas a lacuna é a mesma).

##### Dúvidas

1. Domínio modulo_fiscal_opcional: não vi a lista de valores. A cobertura do 1010 supõe um valor para cada IND_* (CCRF, COMB, USINA, VA, EE, CART, FORM, AER, GIAF1, GIAF3, GIAF4, REST_RESSARC). Confirmar a lista.
2. Tipo_Ligacao (monofásica, bifásica, trifásica) e Grupo_Tensao estão marcados "EFD ICMS/IPI (a conferir)" em Mov_Nota_Fiscal_Utilidade. Confirmar os códigos do guia (TP_LIGACAO 1 a 3; COD_GRUPO_TENSAO de 2 posições).
3. A origem dos registros C181 e C185 (e C330, C380, C430, C480, C815, C880), que o guia exige para validar o 1255, não apareceu na minha busca pelo dicionário. Mov_Icms_St_Ressarcimento parece ser o C176. Confirmar se C181/C185 estão cobertos em outro bloco da conferência.
4. 1601: TOT_OUTROS (compras de cartão presente, saques, fatura de telefone) não tem origem identificada, e o pagamento só existe em Mov_Nota_Fiscal_Saida_Pagamento (grupo de pagamento da NF-e). Recebimentos de PIX, cartão ou boleto sem nota (baixa de título) não indicam a instituição pagadora. Confirmar se Mov_Titulo_Baixa serve de origem.
5. 1500: Possui_Motor_Emissao não inclui o modelo 06 nem a NF3e de saída. O ERP só escritura a nota de energia emitida pela distribuidora; a cobertura vale se Mov_Nota_Fiscal_Saida aceitar o modelo 06 sem motor de emissão. Confirmar.
6. 1910: o guia exige períodos sem lacuna nem sobreposição cobrindo toda a escrituração, e um 1900 por IND_APUR_ICMS por arquivo. Mov_Apuracao_Icms_Subapuracao tem uma linha por filial, competência e indicador, com um par de datas. Não vi chave única nem regra de cobertura contínua; ela é validação, não campo.
7. 1923: se o documento do ajuste não está no ERP e não tem chave (nota em papel de terceiro), só existe Chave_Documento (até 50) e nenhum campo de série, número, data, participante ou modelo. Provavelmente todo documento entra como Mov_Nota_Fiscal_Entrada, mas confirmar.
8. 1900 também serve para a diferença entre preço ao consumidor e base de cálculo da ST (ressarcimento, restituição ou complemento), por critério da UF. Confirmar se o Indicador_Apuracao_Separada atende esse uso.
