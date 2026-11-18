# Desenho e Consolidação da Revisão 50 — Documento 234

*Você escreveu "Q231-2 - Consolidar este item". A Q231-2 pedia um desenho (documento) do que as notas técnicas novas exigem e o documento 230 não cobriu; como a recomendação era "Sim" e o desenho cabe em poucos campos, **escrevi o desenho e o apliquei na mesma etapa**, como na revisão 45. Entrou só a Q231-2, nas quatro partes: (a) emitente contribuinte exclusivo do IBS/CBS, sem IE; (b) NA01-20 e 3BA02; (c) DFeReferenciado na devolução; (d) fim da denegação por irregularidade do emitente. Nada além.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 49** | **Revisão 50** | **Diferença** |
|---|---|---|---|
| Entidades | 1.242 | **1.242** | 0 (nenhuma entidade nova) |
| Campos | 14.431 | **14.434** | +3 |
| Campos de referência (FK) | 3.701 | **3.701** | 0 |
| Entidades mestres | 266 | 266 | 0 |
| Domínios de `Cad_Classe_Sistema` | 374 | 374 | 0 |
| Tabelas físicas (DDL) | 1.508 | **1.508** | 0 |
| Chaves estrangeiras (DDL) | 3.967 | **3.967** | 0 |
| Índices (DDL) | 4.058 | **4.058** | 0 |
| Comentários (DDL) | 12.169 | **12.175** | +6 (3 campos novos e 3 campos que só tinham "---" e ganharam texto) |
| Comandos do T-SQL | 21.703 | **21.709** | +6 |
| Chaves opcionais que esperam a onda de destino | 86 | 86 | 0 |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Referências genéricas | 63 | 63 | 0 |
| Revisão dos módulos | Fase 0 95, Compras 32, CRM & Vendas 27, Contabilidade & Fiscal 67 | Fase 0 **96**, Compras **33**, CRM & Vendas **28**, Contabilidade & Fiscal **68** |  |

O desenho é pequeno de propósito: as quatro partes são, quase todas, **regras de validação da SEFAZ** (que vão para a `Cad_Dfe_Parametro_Regra` e para o `Cad_Dfe_Codigo_Retorno` pela carga) e **textos** dos campos que o Motor lê. A estrutura nova são **3 campos**.

# 2. O desenho

## 2.1. (a) Emitente contribuinte exclusivo do IBS/CBS, sem IE (NT 2026.007 v1.11, produção desde 16/11/2026)

**O que a NT pede.** Contribuinte exclusivo do IBS/CBS é o emitente que, ao mesmo tempo, não informa a `emit/IE`, tem CNPJ com situação cadastral Ativa na Receita e não tem inscrição estadual habilitada para o ICMS na UF (conferência no Cadastro Centralizado de Contribuintes, CCC). A NF-e dele é autorizada **só na SVRS**, os eventos de autoria dele vão à SVRS, não pode emitir NFC-e até 2032, o CNPJ é obrigatório (não vale CPF), a IEST é proibida, o grupo ICMS e o ICMSUFDest são proibidos, o grupo IBS/CBS é obrigatório em todo item e só valem os CFOP com a coluna `indExcIBSCBS`. Mais a validação dos CNPJ (emitente, destinatário, locais de retirada e de entrega e autor do evento) na Lista Centralizada de Contribuintes da Receita (LCC-RFB) e a conferência da IE dos locais de retirada e de entrega no CCC.

**O que o dicionário já tinha.** `Cad_CFOP.Indicador_Exclusivo_Ibs_Cbs` (revisão 40); `Cad_Participante_Situacao_Cnpj` (situação do CNPJ, revisão 17); `Cad_Participante_Inscricao` (a IE por UF); `Mov_Consulta_Cadastro_Externo` (fonte `contribuinte_icms`); `Mov_Nota_Fiscal_Saida_Local` (retirada e entrega); `Cad_Autoridade_Fiscal` com a SVRS.

**O que entrou.**

| **Entidade e campo** | **Tipo** | **O que guarda** |
|---|---|---|
| `Cad_Filial_Perfil_Fiscal.Contribuinte_Exclusivo_Ibs_Cbs` | booleano, opcional | O estabelecimento emite NF-e sem IE. Exige `Contribuinte_Icms` falso, CNPJ ativo e nenhuma IE habilitada. Com verdadeiro o Motor não preenche `emit/IE`, autoriza na SVRS, manda os eventos à SVRS, bloqueia NFC-e, exige CNPJ, proíbe IEST, proíbe ICMS e exige IBS/CBS no item e só usa CFOP com o indicador. Se uma consulta mostrar IE habilitada, o Motor impede a marcação e avisa o contador (rejeição 163). Tem vigência (a entidade é versionada) |
| `Cad_Participante_Inscricao.Situacao_Habilitacao_Icms` | enumeração {habilitado, nao_habilitado, desconhecido}, opcional | cSitIE do CCC, só na inscrição estadual. Alimenta a decisão acima e as conferências 5AF15-12 e 5BG15-12 (IE do local de retirada e de entrega não ativa) |
| `Mov_Nota_Fiscal_Saida.Indicador_Emitente_Exclusivo_Ibs_Cbs` | booleano, opcional | Cópia, na emissão, do campo do perfil: a nota guarda o que valeu (como `ID_Destinacao_Autopeca`). Decide rota, eventos e as regras N01-10, UB12-11 e I08-191 |

**Textos alterados:** `Cad_CFOP.Indicador_Exclusivo_Ibs_Cbs` (as duas exceções da I08-191: devolução e nota de crédito tipo 03); `Cad_Dfe_Evento_Tipo.Ambiente_Receptor` (o evento do emitente sem IE vai à SVRS, 1P10-40); `Mov_Consulta_Cadastro_Externo.Fonte` (o CCC e a LCC-RFB são bases das SEFAZ, sem serviço para o emitente: o ERP as **antecipa** pela consulta de contribuinte e pela situação do CNPJ e **não as copia**; a rejeição final é da SEFAZ).

**Decisões de desenho.** (1) **Sem campo para a rota:** o Motor deriva a SVRS do perfil e `Mov_Dfe_Transmissao.ID_Autoridade` já registra a autoridade que recebeu. (2) **Sem tabela de CCC ou de LCC:** são cadastros das SEFAZ; copiar seria guardar um dado que muda e que o emitente não consegue ler. (3) **`Indicador_Emitente_Exclusivo_Ibs_Cbs` na nota** em vez de derivar do perfil na data da emissão: o perfil tem vigência e aceita ajuste retroativo, e a nota precisa ficar fixa. (4) **Regras na carga, não em colunas:** a `Cad_Dfe_Parametro_Regra` recebe 43 linhas (seção 3).

## 2.2. (b) NA01-20 e as cinco regras 3BA02 (NT 2022.005 v1.11, produção em 03/04/2023)

**NA01-20 (rejeição 694).** O grupo ICMSUFDest é obrigatório quando a operação é interestadual (idDest = 2), com consumidor final (indFinal = 1), não contribuinte (indIEDest = 9) e sem ISSQN. Exceções: grupo de partilha informado; emissão anterior a 01/07/2016; devolução de nota com chave anterior a 2016; CFOP de retorno; nota de entrada. A UF de destino é a da **entrada física** (Ajuste SINIEF 18/2022, § 30). **No dicionário:** o ICMSUFDest já é a parcela `difal_destino` de `Mov_Apuracao_Tributo_Item_Parcela_Icms`; entrou o texto da regra nesse campo e uma linha na carga (`NFE-ICMS-UF-DESTINO-OBRIGATORIO`, rejeição 694). `Cad_CFOP.Indicador_Retorno` já cobre a exceção 4.

**3BA02-50, 54, 58, 64 e 68 (rejeições 545, 546, 566, 567 e 581).** O total da devolução (vNF, vICMS, vFCP, vICMSUFDest, vFCPUFDest) não pode superar o das NF-e referenciadas, com tolerância de R$ 1,00; só vale se todas as referenciadas estão na base da SEFAZ; a SEFAZ pode limitar a 5 notas e a 3 meses; no vNF não vale no comércio exterior. Desde a v1.53 (produção em 16/11/2026) só vale com a chave **no cabeçalho**. **No dicionário:** cinco linhas na carga (`NFE-DEVOLUCAO-VALOR-MAXIMO-*`, tolerância de R$ 1,00, `facultativa_por_uf`) e o texto de `Mov_Devolucao_Venda_Item.ID_Nota_Item`: o Motor compara a devolução com a nota original **antes** de transmitir, por item (`Mov_Devolucao_Venda_Item` já guarda quantidade e valor devolvidos).

## 2.3. (c) DFeReferenciado na devolução (NT 2025.002 v1.53)

**O que a NT diz.** Em 03/11/2026 (v1.52) a devolução passou a referenciar a nota **só** no item (`DFeReferenciado`, rejeição 321). Em 16/11/2026 a v1.53 voltou a **permitir o cabeçalho**, mas com **uma só ocorrência** (B25-40, rejeição 255), e "nunca os dois". O `nItem` é opcional. O emitente (CNPJ base ou CPF) é o mesmo em todos os itens (VC02-40, rejeição 1193) e, na devolução de saída, é o destinatário da nota (VC02-50, rejeição 1194). Exceção da VC02-14: CFOP 5.921 e 6.921.

**No dicionário.** As duas formas já existem: `Mov_Nota_Fiscal_Saida_Referenciada` (cabeçalho) e `Mov_Nota_Fiscal_Saida_Item_Referencia` (item, com chave e `nItem` opcional). **Nenhum campo novo:** o modo não é gravado, porque se lê dos filhos (uma linha de cabeçalho ou linhas de item) e a regra "nunca os dois" é conferência. Entraram textos nos três campos de referência e em `Mov_Devolucao_Compra_Item` e `Mov_Devolucao_Venda_Item`, e cinco linhas de carga (VC02-14 em duas versões, VC02-40, VC02-50 e B25-40). **Regra do Motor:** devolução de **uma** nota original pode ir pelo cabeçalho ou pelo item; de **mais de uma**, só por item (o cabeçalho aceita uma ocorrência).

## 2.4. (d) Fim da denegação por irregularidade do emitente (NT 2023.002 v1.02, seção 7)

A regra 1C17-40 (Uso Denegado 301) deixa de existir em 04/09/2023 (produção da NT 2023.002 v1.00; Ajuste SINIEF 10/2023): o emitente em situação irregular recebe a **rejeição 781** (1C17-38, "Emissor não habilitado para emissão da NF-e/NFC-e") e a nota não fica denegada. **No dicionário:** nenhum campo; `Cad_Dfe_Codigo_Retorno.Natureza` ganhou o texto, a carga traz o 781 (modelos 55 e 65) e o ajuste que encerra o 301 em 03/09/2023. A denegação por irregularidade do **destinatário** não muda, e `denegado` continua em `situacao_documento_fiscal`.

# 3. A carga (`Carga50-20261117`)

A Carga50 é **completa para regras e códigos de retorno**: junta as linhas da Carga49 com as novas e **substitui** os dois arquivos da Carga49 (eventos, domínios e os ajustes da Carga49 continuam valendo). CSV com BOM, separador ";", chaves de negócio. Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_Dfe_Parametro_Regra_NFe` | 193 | 137 da Carga49 + **56 novas** |
| `Cad_Dfe_Codigo_Retorno_NFe` | 122 | 65 da Carga49 + **57 novas**, contadas por modelo e código (46 códigos distintos) |
| Ajustes em linhas já carregadas | 2 | encerra a rejeição 301 (denegado) em 03/09/2023, nos modelos 55 e 65, se a linha existir |

## 3.1. As 56 linhas novas de regra

| **Parte** | **Linhas** | **Rejeições** | **Início** |
|---|---|---|---|
| (a) emitente sem IE: definição, autorização e eventos na SVRS, NFC-e proibida, CNPJ, IEST, CFOP, ICMS, grupo IBS/CBS | 9 | 156 a 159, 161, 162, 166 e 188 | 16/11/2026 (NFC-e: fim em 31/12/2032) |
| (a) exceções da SVRS (B02-10, C12-10, P12-40, B25-90) | 4 | 226, 247, 249 e 1002 | 16/11/2026 |
| (a) conferência da IE no CCC: emitente (1C17-02 e 1C17-04) | 2 | 163 e 164 | 16/11/2026 |
| (a) IE e CNPJ dos locais de retirada e de entrega no CCC (5AF e 5BG) | 10 | 165, 167 a 169, 171, 173, 175 a 177 e 942 | 16/11/2026 |
| (a) CNPJ na LCC-RFB: emitente (3 regras), destinatário (2), retirada (2), entrega (2) e autor do evento (2), por modelo | 18 | 170 e 178 a 187 | 16/11/2026 |
| (b) NA01-20 e as cinco 3BA02 | 6 | 694, 545, 546, 566, 567 e 581 | 03/04/2023 |
| (c) VC02-14 (duas versões), VC02-40, VC02-50 e B25-40 | 5 | 321, 1193, 1194 e 255 | 03/11/2026 e 16/11/2026 |
| (d) 1C17-38 (modelos 55 e 65) | 2 | 781 | 04/09/2023 |

Soma: 9 + 4 + 2 + 10 + 18 + 6 + 5 + 2 = **56**. As 57 linhas novas de código de retorno cobrem 46 códigos: os 31 do emitente sem IE (156 a 188, menos 160, 172 e 174, mais 942), as quatro rejeições antigas citadas pelas exceções (226, 247, 249 e 1002), o 694, as cinco da 3BA02, o 321, o 1193, o 1194, o 255 e o 781. A mensagem de cada código é a da NT.

**Não entraram na carga:** a VC02-20 (1072) e a VC03-20 (1048), que a NT chama de "implementação futura" e não dá data; a VC02-05 (1010) e a VC02-30 (1130), cuja data eu não li; e a C17-10 (229) e a 5E17-70 (246), que a NT 2026.007 **exclui**.

# 4. Leituras minhas e o que perguntei

1. **Devolução, cabeçalho e item (Q234-1).** O histórico da v1.53 diz "é permitido referenciar a Chave de Acesso no cabeçalho ou no item" e a nota da UB12-10 repete; a **observação 1 da VC02-14 ainda diz "fica proibido"** o refNFe. Li a observação como resto de texto antigo. A linha de 03/11 a 15/11 (cabeçalho proibido) existe para as notas desse intervalo.
2. **Denegação (Q234-2).** A tabela da NT traz as regras 1C17-40 e 1C17-38 para os modelos 55 e 65, e o texto da seção fala só da NFC-e. Apliquei aos dois modelos, pela tabela.
3. **Estabelecimento sem IE na Mlegate (Q234-3).** Não sei se algum estabelecimento da Mlegate emite NF-e sem IE. Se nenhum, o campo fica falso e a revisão não muda nada na emissão.
4. **Datas:** início em 16/11/2026 para a NT 2026.007 (produção da v1.11; a homologação foi até 26/10/2026), 03/04/2023 para a NT 2022.005 (produção da v1.10), 04/09/2023 para o fim da denegação (a NT diz "até 04/09/2023"), 03/11/2026 para a primeira versão da VC02-14 e 16/11/2026 para a v1.53; VC02-40 e VC02-50 entraram na v1.40, e a carga traz o texto da v1.53 desde 16/11/2026. O fim da regra da NFC-e em 31/12/2032 (a NT diz "a partir de 2033") e o início de 01/11/2020 dos quatro códigos antigos (a data do MOC 7.0) também são leituras minhas; cada linha diz isso em `Motivo_Vigencia`.
5. **Acesso ao CCC e à LCC-RFB:** a NT não diz que o emitente pode consultá-los. Li que são bases das SEFAZ e que o ERP só antecipa pela consulta pública de contribuinte e pela situação do CNPJ.
6. **Natureza e ação padrão** dos 57 códigos: leitura minha (o 166 e o 188 são "reenviar", porque o documento vai à SVRS; os outros, "corrigir").

# 5. O que ficou de fora

- **Eventos 420110 a 420170** (Q232-9) e **Q229-2** (em espera): sem mudança.
- **A conferência da NA01-20 na DIFAL do ERP** (cálculo, não rejeição): já está no documento 230.
- **VC02-20 e VC03-20**, quando a NT der data: viram linhas da carga sem mudar a estrutura.

# 6. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagens | 1.242 entidades, 14.434 campos (+3: um em cada uma das três entidades), 3.701 referências, 374 domínios, 266 mestres, 1.508 tabelas |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.508 tabelas, 3.967 chaves estrangeiras, 4.058 índices e 12.175 comentários; os três campos novos existem (boolean, character varying e boolean) |
| T-SQL (analisador sqlglot) | 21.709 comandos, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Carga50 | 193 linhas de regra, 122 códigos de retorno e 2 ajustes; toda regra com rejeição aponta para um código do mesmo modelo; nenhuma sobreposição de vigência na mesma chave; mensagens copiadas das NT; nada carregado em banco |
| Fontes lidas de novo | NT 2026.007 v1.11 (inteira), NT 2022.005 v1.11, NT 2025.002 v1.53 (VC02, VC03, B25-40, 3BA02, UB12-10 e o histórico) e NT 2023.002 v1.02 (seção 7) |
| Modelo entidade-relacional e diagramas | Regerados (110 diagramas) |

# 7. O que continua aberto

- **Você:** **Q234-1 a Q234-3** (documento 38, seção 1.48); Q232-9; Q229-2 (espera); Q228-1 e Q228-2; a definição de **DIR** (Q221-5); a Q218-8; a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9; as Q132-5, Q130-1 a Q130-3, Q130-5, Q93-3b, Q93-8, Q118-1, Q139-1 e Q139-2, Q140-5b, 5d e 5e e Q180-3; enviar a pergunta da Q226-3 à Receita; o anexo da NT 13/2026 e o texto da LC 224; o Manual v1.02 e o Anexo IV da NFS-e Via.
- **Contador:** C1 a C363 do documento 188 (nenhuma pergunta nova nesta revisão).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.

# 8. Limites

- **As 193 linhas de regra e os 122 códigos são provisórios.** O texto vem das NT recebidas; a NT 2026.007 foi lida inteira, mas as demais foram lidas nos trechos das regras citadas.
- **Nada foi validado num SQL Server nem carregado em banco;** o T-SQL foi só lido por um analisador.
- **O Motor não consulta o CCC nem a LCC-RFB** (leitura minha, item 5 da seção 4): a rejeição final é sempre da SEFAZ.
- O Project continua acima do limite de tamanho (a gravação dos documentos maiores pode ser recusada), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
