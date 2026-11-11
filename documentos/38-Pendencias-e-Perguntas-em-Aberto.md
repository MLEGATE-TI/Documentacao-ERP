# Pendências e Perguntas em Aberto — Documento 38 (arquivo único)

**Este é o único arquivo de pendências do projeto** (regra de Alberto, 23/10/2026) e **guarda só o que está pendente** (pedido dele de 26/10/2026): o que já foi respondido e aplicado saiu daqui e está no documento 14 (histórico de decisões) e nos relatórios de consolidação. A cada resposta ou item novo atualizo só este documento. **Estado em 10/11/2026:** o dicionário está na **revisão 39** (documento 208, D-N546: o B6, regime automotivo, crédito presumido da CBS dos projetos habilitados, documento 202, com o ajuste A1 do documento 205; **1.173 entidades e 13.339 campos**), sobre a revisão 38 (documento 203, D-N538: o B0b-2 e a documentação dos parâmetros; 1.165 e 13.204) e a revisão 37 (documento 199, D-N532; 1.155 e 13.017). Entraram todas as respostas aprovadas até 10/11/2026 que fecham sozinhas (D-N440 a D-N447, D-N453, D-N457, D-N460 a D-N487, D-N491, D-N492, D-N495, D-N496, D-N498, D-N500, D-N504, D-N507, D-N510, D-N513, D-N515, D-N516, D-N519, D-N523, D-N525, D-N526, D-N530, D-N531, D-N534, D-N536, D-N541 e, do D-N544, o A1), **menos** o que depende do leiaute oficial da DeRE (Q198-12); o texto oficial da MP 1.399/2026 chegou em 10/11/2026 (Q196-10 cumprida quanto ao texto). **Ficou fora da revisão 39:** o B1 do documento 205 (Q205-2, aprovada), porque a entidade dele é do documento 204; **documento 204 (tributação do veículo por combustível e potência, IS, IPI e art. 149):** proposta sem resposta (seção 1.32, D-N540), e o B1 e a correção da Q205-1 entram junto com ele; **documento 206 (B8, Mover e Rota 2030):** proposta sem resposta (seção 1.34, D-N545).   Das perguntas dos documentos 175 e 176, "Também 175 e 176 completos" foi lido como "Sim" (seção 0.1); ficam ao contador a Q176-C8 (documento 188) e à equipe a seção 3.14. **Documento 183 (06/11/2026, D-N494):** a conferência com o Manual da ECD entrou na revisão 34 (seção 1.25; a Q183-C1 segue no documento 188). **Documento 184 (D-N496 e D-N498):** entrou na revisão 34; seguem abertas ao contador as Q184-C1 a C3 (documento 188). **Documentos 185 e 187 (D-N497 e D-N500):** a IN do Sintonia e o texto da LC 225 (arts. 40 a 47) foram conferidos contra o bônus da CSLL (seções 1.27 e 1.28) e as Q185-1 a Q185-3, aprovadas, **entraram na revisão 35**. O histórico das revisões e documentos anteriores está no documento 14. Este arquivo foi revisto por inteiro em 29/10/2026 e atualizado nas consolidações de 03/11/2026, de 04/11/2026 e de 05/11/2026 (seção 5). A conferência do Guia Prático da EFD-ICMS/IPI v3.2.4 (documento 167, D-N459) mostrou que o desenho cobria em parte; as lacunas de uso comum e de 2027 (G1 a G14) entraram na revisão 30, as G15 a G19, na revisão 32, e o Bloco 1 de combustíveis está na seção 1.13. **Desde 09/11/2026 as perguntas e pendências do contador ficam somente no documento 188** (regra de Alberto, D-N501); esta lista não as repete.

Mlegate · Alberto Beyeler · Outubro de 2026

# 0. Respondido por você e ainda não aplicado ao dicionário (entra no desenho indicado)

Estes itens **não são perguntas**: você já respondeu. O que entrou nas revisões 25 a 39 (documentos 133, 145, 151, 154, 166, 169, 174, 178, 182, 186, 195, 197, 199, 203 e 208) saiu daqui, e as leituras minhas que foram aplicadas estão na seção 0.1. O que fica abaixo espera um desenho ou uma resposta sua antes de entrar no dicionário.

| Itens | Sua resposta | O que falta para entrar |
|---|---|---|
| Q205-1 e Q205-2 (10/11/2026) | "Seguir as recomendações" | **Q205-1** (correção do documento 204: a NC 87-2 é a das ambulâncias, carros celulares e carros funerários; a NC 89-1 é a das empresas de turismo) e **Q205-2** (B1: `Condicao_Nota_Complementar` e `ID_Documento_Condicao` em `Mov_Is_Veiculo_Apuracao`, 22 para 24 campos). **Entram quando o documento 204 for aprovado** (Q204-1 a Q204-10, seção 1.32), porque a entidade é dele. Sobre a revisão 39: 1.179 entidades e 13.468 campos com o 204 |
| Q193-1 a Q193-3 (09/11/2026) | "Sim" | O conjunto para a Receita passa a ter **28 perguntas**: a **pergunta 10 fechada** com sete pontos (substitui o rascunho), as **quatro funções** a mais na pergunta 5 (`PERIODO_PRIMEIRO`, `PERIODO_ULTIMO`, `ARRED` e `ANO`) e a **pergunta 28** (P400 linha 20 duplicada e sem fórmula). Textos prontos no zip `Textos-Perguntas-Receita-Doc193.zip` (perguntas 5, 10, 27 e 28). Sem campo novo; nada a aplicar ao dicionário. O envio à Receita é seu |
| Q152-4 (29/10/2026; carga) | "sim": carga provisória das três fórmulas de 2024 (N620 18, N620 19 e N630A 18) | A versão "até 31/12/2025" já passou a valer só em 2025 (`Carga29`). **Faltam as três fórmulas de 2024**: o texto delas está na planilha do leiaute 11 que você enviou antes, e ela não está mais no meu ambiente. **Reenvie a planilha do leiaute 11** (é a parte que resta da Q179-3, seção 1.24) e eu preencho as 3 linhas (`PENDENTE_Formulas_2024.csv`) |
| Locação e NT 007 (28/10/2026; mensagem com o PDF) | "A nota é a NFS-e, mas as definições de código estão na NT 007" | Confirma o que o dicionário já tem (documentos 34 e 41, D-N33, D-N60; D-N412). Nada a aplicar; faltam os Anexos VI v1.03.00 e VII v1.01.00 (seção 3) |
| Q137-4 (documento 137) | "Sim": conferência da LC 227/2026 contra as decisões D-N | **Feita em parte.** A primeira passada completa cobriu 131 artigos e está no documento 138 (11 de impacto ALTO, 30 MÉDIO, 43 sem desenho, 47 BAIXO; as perguntas estão na seção 1.4c). Os documentos 61 e 65 e o texto de 18/10 já tinham usado trechos da LC 227, então ela **não era a primeira**. Nada foi aplicado |
| Q99-4 (27/10/2026) | "Sim": o imposto a pagar do presumido segue o desenho do documento 99 (P300 15 e P500 13, adicional dentro do IRPJ, RET e postergado fora) | Atado à Q93-7 (seção 1.4), que não foi respondida; só texto de regra, sem campo |
| Q102-5 | Sim: 3 linhas de partida do mapa para o contador validar | É carga, não dicionário: a carga do mapa fica vazia até o contador validar as linhas |
| Q135-6 (29/10/2026) | "Sim" | Arquivo 09 gerado e pergunta 9 no documento 98, seção 3.9. Nada no dicionário; o envio é seu |
| Q138-3 a Q138-7 (04/11/2026) | "Sim para todos": **Q138-3** corrige só o texto do documento 10, seção 10 (split simplificado não dá crédito ao adquirente), sem campo; **Q138-4** desenho único dos arts. 5º, 57 e 12 (documento 156); **Q138-5** ajustes do art. 26 no B2, em documento próprio; **Q138-6** arts. 81-A, 95, 168 e 450 junto dos blocos B1, B7, B3 e do crédito presumido; **Q138-7** reextrair os artigos mal extraídos | Q138-3 **entrou na revisão 30** (correção de texto no documento 10, seção 10; D-N467); Q138-4 é o documento 156, **aplicado na revisão 30**; Q138-5 vira documento próprio; Q138-6 entra com os blocos; Q138-7: 5º, 6º, 12 e 57 feitos, o resto no documento 159 |

## 0.1 Leituras minhas aplicadas nas revisões 24 a 39, para você confirmar

**Revisão 39 (documento 208, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "o que você aprovou e fecha sozinho"**: o documento 202 inteiro e o A1 do 205. Ficaram de fora o B1 do 205 (a entidade é do documento 204, sem resposta) e o documento 206 (Q206-1 a Q206-12 sem resposta). Se você queria o 204 e o 206 dentro, responda as Q204-1 a Q204-10 e as Q206-1 a Q206-12 e eu faço a revisão 40. (2) **O A1 entrou direto na entidade nova** (`Mov_Habilitacao_Automotiva_Compromisso` já com 17 campos e o valor `informacao_anual_pdi`). (3) **Cargas de partida provisórias:** 22 parâmetros do crédito (15 percentuais por faixa, 5 fatores do IPI, a data de referência de 31/12/2025 e o mínimo de 10% de pesquisa), 25 de documentação, 34 de efeito e 5 do catálogo central; o contador valida (C248 a C255). (4) **Os avisos 21 e 22** (informação anual de pesquisa e intimação de 30 dias) são regra de texto do Motor, sem campo. (5) **Alertas do gerador de DDL:** os mesmos sete da revisão 38; nenhum novo.

**Revisão 38 (documento 203, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: os documentos 200 e 201 inteiros; o documento 202 ficou de fora porque as Q202-1 a Q202-11 não têm resposta. (2) **A chave opcional `Cad_Arrendamento_Mercantil.ID_Contrato`** (para `Cad_Gestao_Contrato`, da onda 5) **está no modelo e conta nas 3.445 referências**; o documento 200 dizia que ela ficava fora da contagem, o que não confere com o total que você aprovou. Como é opcional e aponta para onda posterior, ela entra no ALTER TABLE da onda 5 e a lista do documento 31 passa de 79 para 80 chaves. (3) **Módulos:** seis entidades do B0b-2 e as duas da documentação ficam em Contabilidade & Fiscal (onda 3) e as duas do plano de saúde em Folha & RH (onda 6). (4) **Cargas de partida provisórias:** vigência de 01/01/2027 para as 28 regras e 01/01/2026 para `ESOCIAL` (uso no ERP, como a D-N323); o contador valida (C239 a C247). (5) **A série Selic** de `Cad_Serie_Cotacao` deve ser criada só se ainda não existir. (6) **Alertas do gerador de DDL:** são sete campos de texto sem tamanho em chave única (o documento 31 dizia cinco); o novo é `Cad_Parametro_Efeito_Obrigacao.Quando_Valor`; mantive o desenho aprovado e a escolha do tamanho (texto (n)) fica com você.

**Revisão 37 (documento 199, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: o documento 198 inteiro (Q198-1 a Q198-12) e as Q160-1 a Q160-7 do documento 160; o leiaute oficial da DeRE (Q198-12) e o texto da MP 1.399/2026 (Q196-10) seguem com você. (2) **As Q160-8 e Q160-9, sem resposta, foram lidas como a recomendação ("não")**, o que não muda o dicionário. (3) **Módulo:** as 11 entidades do B4 ficam em Contabilidade & Fiscal (onda 3), como o documento 198 desenhou; se você preferir outro módulo, mudo sem alterar campo. (4) **O texto novo do redutor** (o decreto só tem fator de redução na importação) ficou em `Cad_Redutor_Base_Dere.Percentual_Redutor`, porque a entidade não tem campo de descrição; a D-N273 está mantida. (5) **Vigência de partida das cargas:** 01/01/2026 (uso no ERP, como a D-N323) e 01/01/2027 para as alíquotas (data da lei), todas provisórias; o contador valida (C233 a C238). (6) **O leiaute da DeRE continua fonte secundária** até você enviar o manual oficial. (7) **As 6 obrigações novas** de `Cad_Obrigacao_Acessoria` (PGDAS_D, DAS_MEI, DESTDA, DESIF, DOI e LCDPR) começam em 01/01/2026, a data de uso no ERP, e não a legal; tratei como existentes os 8 códigos que o campo cita e os módulos DESIF_M1 a M4, sem lista de carga para conferir.

**Revisão 36 (documento 197, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: o documento 159 (Q159-1 a Q159-3 e Q159-5 a Q159-9), o documento 196 (Q196-1 a Q196-11) e a D-N523; ficaram de fora o documento 160 (não desenhado) e o que depende da MP 1.399/2026. (2) **14 códigos de domínio foram abreviados** para caber nos 30 caracteres de `Cad_Classe_Sistema.Codigo` (por exemplo, `is_demais_hipoteses` no lugar de `imposto_seletivo_demais_hipoteses`); os documentos 159 e 196 citam os nomes longos, e a lista de correspondência está no documento 197. (3) **Módulos:** `Cad_Instituto_Beneficio_Ordem`, `Cad_Parametro_Legal_Ibs_Cbs` e `Cad_Programa_Conformidade_Beneficio` ficam em Contabilidade & Fiscal (onda 3), `Mov_Processo_Consulta_Tributaria` e `Mov_Processo_Uniformizacao` em Jurídico (onda 2) e `Cad_Is_Hipotese_Base` na Fase 0 (onda 0), ao lado de `Cad_NCM_Imposto_Seletivo`; se você preferir outro módulo, mudo sem alterar campo. (4) **Q196-6** foi lida como "não preparar o esboço da entidade do documento consolidado": só os dez pontos e o gatilho. (5) **A vigência de partida das cargas novas é 13/01/2026** (publicação da LC 227), todas provisórias; o contador confirma. (6) **Os nove avisos do Motor das multas, o aviso da embalagem primária (art. 409, § 2º) e o do valor de referência ficam registrados em texto e não programados.** (7) **As 8 linhas de CBS dos combustíveis** mantêm os valores da carga 31 (iguais aos da Portaria MF 3.074 lida) e o início em 08/01/2027 até a C161.

**Revisão 35 (documento 195, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: documentos 185 e 187, 189 a 192 e as respostas às Q188-3 a Q188-5; ficaram de fora o documento 194 (sem respostas) e o documento 193 (sem campo). (2) **`Origem_Dados_Entrada`** (importado de XML ou digitado) ficou em `Mov_Documento_Fiscal`, só no documento recebido, e a regra vale também para `Mov_Nota_Fiscal_Entrada` e `Mov_Nfts`; a D-N510 pedia "campo e entidades a conferir". (3) **A ciência do indício** ganhou 9 campos e a situação em quatro valores (`aberta`, `regularizada_no_prazo`, `vencida_sem_regularizacao` e `sem_direito_ao_prazo`), porque o documento 185 listava os campos sem os valores. (4) **`ID_Participante_Situacao_Cnpj_Versao`** em `Cad_Participante_Situacao_Cnpj_Motivo` aponta para a versão da situação (a tabela física `_Versao`), pelo desenho do documento 190. (5) **Os códigos das cinco classificações do Sintonia** (`sintonia_a_mais`, `sintonia_a`, `sintonia_b`, `sintonia_c`, `sintonia_d`) são minhas; a IN dá só as letras e as faixas da nota. (6) **`limite_moeda_exterior_anual`** entrou com a mesma carga do cartão (R$ 120.000, vigência 01/01/2026, provisório), como a D-N507 mandou. (7) **A vigência dos 24 motivos de suspensão** começa em 10/07/2026 (art. 3º da IN 2.333), registrada no texto do fundamento, porque `Cad_Classe_Sistema` não tem vigência. (8) **Os avisos do Motor** dos documentos 185 a 192 estão registrados e **ainda não programados**.

**Revisão 34 (documento 186, seção 4): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "tudo o que você aprovou e não estava no dicionário"**: documentos 158, 177, 183 (núcleo) e 184 e a carga de cClass; o documento 185 não entrou (na consolidação, as Q185-1 a Q185-4 estavam sem resposta; as Q185-1 a Q185-3 foram aprovadas depois, D-N500). (2) **`IND_MUDANC_PC` e `IND_ESC_CONS` viraram campo** em `Mov_Ecd_Periodo`: o documento 183 dizia que não, e valeu o 184, que você aprovou. (3) **`Indicador_Escrituracao_Descentralizada`** ficou "informado pelo usuário, sem valor oculto" (a Q183-8 trata do bloco K, e não da descentralizada). (4) **cClass da NFGás:** a continuidade e as marcas do grupo vão no **texto da descrição** dos 46 códigos; os grupos 030, 060 e 073 ficam **sem linha** em `Cad_Utilidade_Classificacao_Efd`, e `Fatura_Agregadora` é falso nas 8 linhas carregadas. (5) **`Permite_Ressarcimento` falso nas 23 linhas** de `Cad_Zfm_Alc_Regra`, porque o campo é obrigatório e só o crédito presumido o tem em questão. (6) **Início de vigência da carga da ZFM e ALC vazio** ("o contador define"); só a compra governamental leva as datas do art. 372. (7) **`ID_Plano_Empresa` é obrigatório** em `Mov_Ecd_Periodo`. (8) Os avisos do Motor dos documentos 158, 177, 183 e 184 estão registrados e **ainda não programados**.

**Revisão 33 (documento 182, seção 2): leituras que aguardam a sua confirmação.** (1) **"Consolidar" foi lido como "só o que você aprovou"**: o bônus da CSLL na baixa (D-N491 e D-N492); os documentos 158 e 177 ficam de fora. (2) **"Baixar pelo valor pago"** foi lido como `Valor_Baixado` igual ao valor total do título, com o desconto e o dinheiro separados (Q181-1, que você aprovou ao seguir a recomendação). (3) Os 3 avisos do Motor do bônus estão registrados no documento 10 e **ainda não programados**. (4) A conta contábil do desconto e o uso na ECF seguem com o contador (Q140-6).

**Revisão 32 (documento 178, seção 2): leituras que aguardam a sua confirmação.** (1) **"Também 175 e 176 completos" foi lido como "Sim" em todas as perguntas abertas desses dois documentos** (Q175-1 a Q175-9, Q176-11 e Q176-12), com a recomendação de cada uma; a parte da Q175-9 que pede a tabela de cClass da NFGás segue aberta (seção 1.21). (2) **A natureza do código de receita não bate com a medição do documento 172**: o documento dizia 703 de 1.935 códigos com um único termo; não reproduzi a lista de palavras e usei uma reconstruída, que dá 730 das 2.162 linhas (654 dos 1.935 códigos distintos; 1.132 sem termo e 149 com mais de um). A sugestão é provisória e visível. (3) **Q176-11:** AL, CE, RN e MG ficam com `quem_vendeu`, a PB sem valor em `Estabelecimento_Informante` (o FAQ não diz) e o PR sem critério nem estabelecimento; por isso esses dois campos de `Cad_Efd_1601_Regra_Uf` ficaram opcionais. (4) `tipo_documento_iss_df` (8 valores) entrou como domínio; o `tipo_conhecimento_embarque` já existia desde o documento 43 e foi reaproveitado; dois domínios saem (trocados por entidades com UF e vigência). (5) A ligação de cada arquivo do validador a uma tabela do Guia é leitura minha (contador, C1 a C3). (6) Os 18 avisos do Motor estão **registrados no anexo do documento 10 e ainda não programados**. (7) **A descrição do K275 nos documentos 167 e 168 ("decidido: não preencher") e a correção do C130 no documento 176 ficam só nos documentos 14 e 38; os documentos de desenho não foram reescritos.** (8) A carga sai no pacote `Carga32`, toda provisória; a vigência das cargas dos documentos 175 e 176 sai vazia (o Guia e o FAQ não a fixam) e o contador define.

**Revisão 31 (documento 174, seção 2): leituras que aguardam a sua confirmação.** (1) **O lado de quem recebe o apoio fica fora** (as cinco entidades de 66 campos e o critério do Motor `adesao_programa_do_emitente`), porque você aprovou "só com cliente" (Q173-8, D-N68); **confirme se leio certo** e diga se já existe um cliente (Q173-E2). (2) **`Valor_E_Maximo` virou `Eh_Valor_Maximo`**: a regra H2 do dicionário não aceita booleano com o prefixo `Valor_`. (3) **Módulo:** as 8 entidades de combustíveis ficam em Motores Transversais (onda 0) e a autorização da ANP na Contabilidade & Fiscal; se você preferir tudo na Contabilidade & Fiscal, mudo de módulo sem alterar campo. (4) **Um campo saiu:** `Mov_Estoque_Abertura_Cbs_Estorno.Valor_Acrescimos`, substituído pela multa e pelos juros do art. 27 (D-N466). (5) A carga de `Cad_Acrescimo_Legal_Cbs` tem vigência inicial provisória de 01/01/2027 (Q157-C7) e a do valor de mercado da locação sai vazia. (6) A exceção dos combustíveis do regime específico à redução de 0,1 ponto fica em `Cad_Cclasstrib.Aplica_Reducao_Transicao_Cbs` até haver catálogo (Q157-C11). (7) As quatro leituras da carga do documento 173 (fim do etanol em 15/10/2026; MP 1.391, etanol e MP 1.358 sem fim no cabeçalho; imposto de exportação de 50% até 31/12/2026; média simples do desconto do distribuidor). (8) As cargas saem no pacote `Carga31`, todas provisórias.

**Revisão 30 (documento 169, seção 2): leituras que aguardam a sua confirmação.** (1) **Q164-1:** li "seguir com todas as recomendações" como rodoviário, aquaviário e ferroviário **mais o aéreo** agora (obrigatório em 01/12/2026) e o **metropolitano só com cliente**; **confirme se leio certo**. (2) Os motivos de substituição do BP-e entram como valores novos, pelo nome, no mesmo domínio do `ID_Motivo_Substituicao`; se os códigos colidirem com os da NFCom, divido o domínio por modelo (como no documento 165). (3) `Mov_Valor_Mercado_Apuracao.ID_Item_Origem` e `Mov_Apuracao_Tributo_Item_Base_Especial.ID_Origem` são referências genéricas **sem campo de tipo**, como o documento 156 desenhou. (4) Em `Mov_Apuracao_Tributo_Item`, `Origem_Tipo = bpe_evento` aponta `Mov_Bpe_Evento`. (5) `Cad_Utilidade_Classificacao_Efd` entrou como entidade e **sem carga**, e a tabela 5.7 (`motivo_restituicao_complemento_icms_st`) também fica sem carga, até a Q167-5. (6) `Valor_Acrescimos` do estorno do uso pessoal fica como estava (nota: "a calcular pelo parâmetro do B0a, documento 157, ainda não consolidado"). (7) Três entidades novas aparecem como isoladas na auditoria (F1) de propósito (`Cad_Bloco_K_Exigencia_Registro` e `Cad_Utilidade_Classificacao_Efd`, catálogos lidos por código, e `Mov_Nota_Iss_Df_Complemento`, ligada à nota por referência genérica). (8) As cargas do documento 156 (21 critérios, 8 linhas de operação equiparada, 12 hipóteses com prefixos de NCM, 19 componentes de base, 8 métodos e 2 regras de câmbio) saem no pacote `Carga30`, todas provisórias, com `Vigencia_Inicio` de partida em 01/01/2026 nas regras da base (a confirmar pelo contador).

**Revisão 29 (documento 166, seção 2): leituras que aguardam a sua confirmação.** (1) Na Q155-2, "Sim" foi lido como a recomendação: **opção B** (os 11 campos de obrigação do perfil ficam onde estão e aparecem na tela do catálogo; a migração é obrigação por obrigação) e `Incidencia_Pis_Cofins`, `Forma_Apuracao_Irpj`, `ID_Segmento_Csll` e `Sujeita_Tef_Saf` ficam no perfil; se você quis a opção A (migrar tudo agora), diga; (2) as **25 entidades novas** ficam na Contabilidade & Fiscal (anexo da seção 43 do documento 10); 10 na onda 3 e as 15 de NFGas e NF3e na **onda 4** (exigem a nota de entrada); só `Cad_Obrigacao_Parametro_Definicao` e `Cad_Obrigacao_Parametro_Valor` são mestres; (3) o campo de data de `Cad_Obrigacao_Parametro_Valor` se chama **`Data_Valor`**, e não `Valor_Data` como no documento 155 (regra H2 da auditoria); (4) a **classificação do item** de NFGas e NF3e é referência a `Cad_Classe_Sistema` (domínios `classificacao_item_nfgas` e `classificacao_item_nf3e`), porque o documento 165 citava uma entidade que não existe; os domínios ficam sem valores até as tabelas de classificação chegarem; (5) o catálogo recebeu 2 linhas na carga (`presumido_somente_por_refis`, vigência desde 01/01/2026, e `gera_rascunho_nota_debito_antecipacao`, desde 01/01/2027) e **nenhuma resposta** de empresa, exceto o rascunho da nota de débito, ligado conforme a Q153-14; (6) a nova versão da regra do adiantamento (CBS e IBS, base `valor_recebido_sem_tributo`) começa em 01/01/2027, como a versão anterior; (7) o bônus da CSLL (art. 41 da LC 225) entra com vigência desde **09/04/2026** (início dos arts. 40 a 47, pela minha conta); (8) `Mov_Credito_Ajuste_Documento` tem **13 campos** (os 12 do documento 153 mais `ID_Dfe_Evento`, da Q153-11); (9) o valor `devolucao_adiantamento` em `Mov_Titulo.Origem_Tipo` entra junto com `devolucao_nota_cancelada`, porque você confirmou os dois casos (Q153-7 e Q153-8); (10) os motivos de substituição da NFGas e da NF3e entram como domínios por modelo, com os textos como placeholder até o MOC ou o schema chegar; (11) as 3 linhas da ECF (N620 18, N620 19 e N630A 18) passam a começar em 01/01/2025, e as fórmulas de 2024 esperam a planilha.

**Revisão 28 (documento 154, seção 2): leituras aplicadas.** (1) Na Q128-6, "tarifa do destino do serviço" é o **local da operação** (onde o serviço é executado), e vale para IBS e CBS; e "a tributação é na emissão da nota fiscal" (PIS e Cofins) é lida como a **data de emissão da nota** contra a qual o adiantamento é aplicado, sobre o valor da nota, sem tributar o recebimento; (2) na Q128-5, "o contador parametriza" é um **indicador no perfil fiscal**; (3) na Q127-4, o ERP **nunca altera sozinho** a receita por caixa e guarda só a **confirmação** do usuário; (4) na Q128-4, o Y681 zerado é aceito e o ERP não avisa quando ele sai zerado das contas mapeadas; (5) na Q139-3, a carga **não muda** (o texto `"20:99"` fica como publicado) e só o motor lê `"20.99"`; (6) `Cad_Atividade_Presuncao_Mapa` tem **13 campos**, e não 12 como diziam os documentos 127 e 152: a tabela do documento 127 sempre teve 13 linhas (identificador, empresa, três prefixos, prioridade, atividade, segregação, observação, situação e os três de vigência); (7) as **quatro entidades novas** ficam na Contabilidade & Fiscal (anexo da seção 42 do documento 10), na onda 3, e só `Cad_Adiantamento_Regra_Tributacao` é mestre; (8) a carga de partida de `Cad_Adiantamento_Regra_Tributacao` (6 linhas) vale de 01/01/2027 em CBS e IBS e de 01/01/2026 em PIS, Cofins, IRPJ e CSLL, com `Origem_Valor` = `resposta_do_gestor`; (9) `Mes_Competencia` entra na identidade da linha e fica vazio nas linhas que não são do Y681; (10) até a Q152-2, a confirmação da mudança de critério fica no histórico geral de auditoria; (11) a permissão "Decidir conflito de reimportação" é só linha de carga em `Cad_Permissao`, por perfil que você indicar; (12) `Mov_Credito_Aplicacao.Data_Aplicacao` ganhou o texto sobre qual nota conta (Q128-7).

**Revisão 27 (documento 151, seção 2): leituras que aguardam a sua confirmação.** (1) As cinco entidades do TEF ficam na **Contabilidade & Fiscal** (anexo da seção 41 do documento 10), na onda 3 do DDL; (2) três delas são **mestres** com vigência (parâmetro, repartição e mapa de categoria por conta); (3) os **códigos das 17 categorias** são curtos, por causa do limite de 30 caracteres de `Cad_Classe_Sistema.Codigo`, e a numeração dos incisos do art. 423 é a da minha leitura; (4) a carga de alíquotas e da repartição vale a partir de **01/01/2027** e é toda provisória; (5) o campo `Opcao_Tef_Saf` dos documentos 70 e 94 nunca entrou; vale `Sujeita_Tef_Saf`, e os dois documentos mantêm o nome antigo; (6) a descrição de `Credito_Vedado_Adquirente` inclui a regra da SAF como fornecedor; (7) o valor `direito_desportivo` na importação de intangível **não foi aplicado**; a Q151-1 foi respondida em 29/10/2026 (seguir a recomendação: não criar, reconhecer pelo NBS e pelo Motor).

**Revisão 26 (documento 145, seção 2): leituras que aguardam a sua confirmação.** (1) Na Duimp, o que não é chave nem referência ao pai é **opcional**, porque a importação grava o que consegue e abre aviso; (2) os campos das "chaves únicas" dos documentos 142 e 143 são identidade; (3) seis entidades mestres (as cinco de cadastro do B1 e a qualificação do B2); (4) `Client_Id` e `Tipo_Autenticacao` **opcionais** na credencial (a CBS segue com Client Id; o Portal Único, com chave ou certificado); (5) os tipos de lista legal se chamam `lc214_anexo_i` a `lc214_anexo_xv` e a vigência de partida é 01/01/2027 na carga da lista legal; (6) os 12 códigos de tributo ficam em maiúsculas, como o Portal os envia; (7) `Mov_Locacao_Pagamento` vai para a onda 5 do DDL; (8) os 30 tipos de qualificação ainda não viram carga (esperam o contador). Das revisões anteriores: nenhuma leitura aguarda confirmação. Em 28/10/2026 você confirmou os demais itens desta seção (as leituras das Q101, Q102, Q103, Q113, Q99, Q125, Q126, Q128 e Q132, o "Sim aprovo" do documento 124, o nome `ID_Classificacao_NCM`, os domínios novos, `Origem_Tipo` e a onda 3 do DDL) e esclareceu a Q129-2 ("sim tem o Código do banco, mas deixar sempre o país nas regras"): vale a leitura 2, país e indicador juntos na regra. As leituras ficam registradas nos documentos 14 (D-N397) e 133. Duas ressalvas de conteúdo, não de leitura, continuam no documento 188: o tratamento contábil do adiantamento em moeda (Q101-10b) e a regra do trimestre de Refis (Q128-1), que são do contador.

# 1. Para você responder

**Em aberto para você:** seção 1.3 (Q132-5), 1.4 (Q130-1 a Q130-3, Q130-5, Q93-3b, Q93-8 e Q118-1), 1.4a (Q139-1 e Q139-2), 1.5b (Q140-5b, 5d e 5e para a Receita; a Q140-6 é do contador, documento 188), 1.13 (Q167-6, adiada por você), 1.24 (Q179-1 e Q179-3), **1.28 (Q160-8 e Q160-9, sem efeito no dicionário)**, **1.32 (Q204-1 a Q204-10, tributação do veículo)**, **1.34 (Q206-1 a Q206-12, Programa Mover e Rota 2030)** e os itens avulsos das seções 1.6 e 1.7. As demais seções 1.x não têm pergunta aberta.

## 1.1 Y520, moeda estrangeira, tipo da baixa e exterior (documentos 100 a 103, 107, 108, 110, 111, 113 e 114)

Nenhuma pergunta aberta: todas as perguntas desta seção foram respondidas e aplicadas (revisão 25, documento 133). Os pontos que dependem do contador estão no documento 188.

## 1.2 (sem perguntas abertas)

O número foi mantido para não mudar as referências dos outros documentos.

## 1.3 Documentos 99, 125, 126, 127, 128, 131, 132 e 135: lucro presumido da ECF, caixa, atividade de presunção e Refis (Q132-5)

| Nº | Pergunta | Recomendação |
|---|---|---|
| Q132-5 | Os **pontos 1 e 2** da pergunta 8 da consulta à Receita (documento 98, seção 3.8; arquivo 08 gerado): a regra do X280 trata as linhas 74 a 77 do P130 como redução, mas a fórmula as chama de demais atividades; e o P130 não tem linha de 38,4%, que o P200 10 inclui. O ponto 3 (orientação da linha 6 citando P130/68) você já aprovou na Q134-6 | Sim (o texto está pronto; o envio é seu) |

## 1.4 Documentos 93, 118 e 130: cadeia do lucro real da ECF e alíquotas 7 e 8 da CSLL (Q130-1 a Q130-5)

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q130-1** | Documento 130: de onde vem o texto que você colou sobre as alíquotas 7 e 8 da CSLL (resposta da Receita com protocolo e data, contador, ferramenta de pesquisa ou outra fonte)? A pergunta 3 do documento 98 foi **enviada**? | Informar a origem; se não for da Receita, manter a pergunta 3 na lista de envio |
| **Q130-2** | Mapeamento código × alíquota a partir de 2028: vale o do manual (3 = 20%, 4 = 15%) ou o do texto (3 = 15%, 5 = 20%)? O texto também usa 15% para o código 3 e para o 4 | Aguardar a Receita (perguntas 3 e 4 do documento 98); de 2028 em diante "a confirmar" |
| **Q130-3** | Usar a tabela de 2026 e 2027 (7: 9% até março e 12% depois; 8: 15% e 17,5%) como parâmetro provisório "a confirmar", calculando em vez de parar e avisar (Q93-5b)? As datas por segmento batem com a IN RFB 2.315/2026 (conferida só por um artigo) | Não ainda; só depois da Q130-1 e se a origem for oficial |
| **Q130-5** | T181 6 e U182 2, código 4 de 2022 em diante: o ERP usa 15% em todos os trimestres, com aviso, enquanto a planilha não for corrigida? | Sim, 15% com aviso, e manter a pergunta 3 (3) na consulta |
| Q93-3b | Você pediu "guardar a composição das linhas". É o **rastro do cálculo** (quais linhas e valores formaram cada linha calculada) ou a **composição pelos lançamentos e contas da Parte A**, como nos registros M310 e M312? | Perguntei antes de desenhar |
| Q93-8 | Escopo das linhas editáveis: o ERP só soma os lançamentos da Parte A feitos pelo contador, ou também **sugere** adições e exclusões? | Só soma agora; sugestão vira documento próprio |
| Q118-1 | A S200 linha 90 (TEF e SAF) também é dividida em duas linhas na carga, pela mesma regra da Q93-1, quando o motor do TEF e SAF entrar? (documento 118, seção 5) | Sim, mesma regra, sem campo novo |

**Do contador, no documento 188:** Q93-7 (C8), Q118-2 (C9), Q122-1 (C11) e Q130-4 (C12).

As leituras das funções do manual são minhas; o teste cobriu só as versões de 2025. O leiaute 13 deve mudar fórmulas (por isso ficam no cadastro).

## 1.4a Documento 139: comparação das fórmulas com a planilha do leiaute 11 (Q139-1 e Q139-2; Q139-3 a Q139-5 respondidas em 29/10/2026)

A planilha que você enviou (Q136-1) traz 372 fórmulas: 364 são iguais às da carga, 8 diferem e nenhuma falta. As 84 que o manual de 2025 não permitia validar são **idênticas às de 2025**. Cinco das sete divergências do documento 136 já estavam na planilha de 2025. **Substituem as Q136-2, Q136-3 e Q136-4** (documento 136, que continua válido como análise).

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q139-1** | Reescrevo a **pergunta 10** da consulta à Receita (documento 98, seção 3.10) com as divergências na forma do documento 139, seção 4 (cinco herdadas de 2025, uma mudada em 2026, uma linha nova) e gero o arquivo 10? O envio é seu | Sim; a Q136-3 fica substituída por esta |
| **Q139-2** | Das divergências herdadas (N660 5 a 9, N610 3, N660 12.01, N670 12 e M350R 267), o motor segue a **fórmula como publicada** e avisa o contador? | Sim, como publicada, com aviso |

## 1.4b Documento 137: Anexos I a XV da LC 214 e Decreto 13.075/2026

Nenhuma pergunta aberta: as Q137-1 a Q137-6 foram respondidas "sim" e estão na seção 0.

## 1.4c Documento 138: conferência da LC 227/2026 (Q138-3 a Q138-10 respondidas)

Nenhuma pergunta aberta. A Q138-3 a Q138-7 foram respondidas "Sim para todos" em 04/11/2026 (D-N464; seção 0). Ficam como trabalho já decidido: os arts. 5º, 6º, 12 e 57 estão no documento 156; os demais artigos mal extraídos (14, 22, 28, 41, 59, 60, 195, 243 e 271) **foram relidos no documento 159** (D-N524: 14, 41, 195, 243 e 271 não têm marca da LC 227; 22, 28, 59 e 60 foram lidos, e a linha "art. 95 (plataformas)" do documento 138 é do art. 22, §§ 13 a 15); o art. 26 (B2) em documento próprio; os arts. 81-A, 95, 168 e 450 junto dos blocos B1, B7, B3 e do crédito presumido.

## 1.4d Documento 151: consolidação da revisão 27 (Q151-1 respondida em 29/10/2026)

Nenhuma pergunta aberta para você. O TEF da SAF (documentos 146, 147 e 149), a hotelaria e o Motor (documento 148) entraram no dicionário na revisão 27 (documento 151; D-N431). A Q151-1 foi respondida em 29/10/2026 ("seguir recomendação"): **não se cria o valor `direito_desportivo`**; a importação de direitos desportivos é reconhecida pelo NBS do serviço no item da nota de entrada e pelo enquadramento do Motor (D-N434). O que depende do contador está nas documento 188 a 2.7.

## 1.5 Documentos 94 e 115: perfis previstos e fila de desenho

Ordem do desenho já decidida por você: B2 (documento 116) e B0a em seguida; depois, por prontidão, B1 (a Duimp: só registra; leitura no documento 141 e desenho de campos no documento 142), B5, B3, B4, B6, B7. O **B0b-1** (selo de conformidade, programas, devedor contumaz e bônus da CSLL) foi aprovado na Q140-1 (documento 140, seção 5) e **entrou na revisão 29** (documento 166); o **B4** foi desenhado no **documento 198** (D-N529; Q198-1 a Q198-12 aprovadas em 10/11/2026, D-N530; **entrou na revisão 37**, documento 199) e o **B0b-2** (serviço financeiro do tomador) foi desenhado no **documento 200** (D-N533; Q200-1 a Q200-11 aprovadas em 10/11/2026, D-N534; **entrou na revisão 38**, documento 203). A documentação dos parâmetros do B0b-2 que você pediu é o **documento 201** (D-N535; Q201-1 a Q201-10 aprovadas em 10/11/2026, D-N536; **entrou na revisão 38**, documento 203). O **B6** (regime automotivo, crédito presumido da CBS dos projetos habilitados) foi desenhado no **documento 202** (D-N537; Q202-1 a Q202-11 aprovadas em 10/11/2026, D-N541; **entrou na revisão 39**, documento 208). Segue sem desenho o B7. A tributação do veículo por combustível e potência (observação D-N539) foi desenhada no **documento 204** (D-N540; Q204-1 a Q204-11 na seção 1.32; nada aplicado).

**B5 (bares e restaurantes e hotelaria):** você respondeu "sim" à Q148-5 (29/10/2026): o regime de bares e restaurantes é desenhado no **documento 150** (aprovado em 04/11/2026, com a gorjeta de 15%, os valores de plataforma, os §§ 3º e 4º do art. 399, a refeição por contrato, a cooperativa, a locação por temporada e a agência de turismo); **entrou na revisão 31** (D-N477).

**B3 (compras governamentais e Zona Franca de Manaus e áreas de livre comércio):** desenhado no **documento 158** (04/11/2026): 10 entidades novas (155 campos), 5 existentes alteradas (9 campos novos) e 20 valores de domínio. As perguntas Q158-1 a Q158-13 estão na seção 1.20; **entrou na revisão 34** depois da sua resposta. Ficam para os documentos 159 e 160 a LC 227 (43 artigos e os mal extraídos) e os parâmetros das outras obrigações.

Nenhuma pergunta aberta: a **Q94-7** foi respondida ("já foram enviados"; D-N408). A LC 225, o Decreto 13.133 (colado de novo em 28/10/2026 e conferido: documento 140, seção 7) e o Decreto 12.955 consolidado chegaram.

## 1.5a Documento 116: qualificação do participante perante a CBS (B2)

Nenhuma pergunta aberta: Q116-1 a Q116-8 respondidas "sim" (seção 0). A entidade `Cad_Participante_Qualificacao_Cbs` entrou na revisão 26 (documento 145); a carga dos 30 tipos espera o contador, e os ajustes do art. 26 estão na Q138-5 (seção 1.4c).

## 1.5b Documento 140: LC 225/2026, Decreto 13.133/2026 e o B0b-1 (Q140-5 e Q140-6; Q140-7 respondida "Desenhar" em 04/11/2026, documento 170; Q140-1 a Q140-4 respondidas em 29/10/2026)

A seção 5 do documento 140 (5 entidades e 80 campos, Q140-1) **entrou na revisão 29** (D-N447 e D-N458). **Estado em 06/11/2026** (documentos 180 e 181, D-N490 e D-N491): a Q140-5a e a Q140-5c foram **respondidas** (cada apuração calcula o seu bônus; a guia entra pelo valor total e o desconto aparece na baixa, registrado para a ECF). Ficam abertas as Q140-5b, Q140-5d e Q140-5e (para a Receita, pergunta 26 do documento 179), as Q140-6a a Q140-6e (contador) e a Q180-3. As Q181-1 a Q181-4 e a Q180-2 foram **respondidas** ("seguir com as recomendações"; seção 0). A Q140-6 fica com o contador; o ERP não lança o bônus até ele responder.

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q140-5b, 5d e 5e** | "À vista" é só a cota única? As estimativas abatem no ajuste anual o valor total da guia ou o pago? Os meses de selo contam até o vencimento ou o pagamento, e em que ordem o limite anual é consumido? (documento 180, seção 3) | Cota única até o vencimento; valor total da guia; vencimento para os meses e pagamento para a ordem. Vão à Receita pela pergunta 26 do documento 179 |
| **Q180-3** | **Respondida em parte em 09/11/2026:** a IN RFB 2.316/2026 regulamenta o bônus do Selo Sintonia (arts. 12 e 13) e o PDF da **LC 225** (documento 187) traz o texto do art. 41. **Falta só o ato do Confia** (Q187-3) | Enviar, se existir |

**Do contador, no documento 188:** Q140-6a a 6e, com a Q185-C1 (C212).

## 1.5c Documento 144: leitura pela API do Portal, despesas da nota, locação por pessoa física e aluguel recebido e emitido (Q144-1 a Q144-12, respondidas em 29/10/2026)

Nenhuma pergunta aberta: você respondeu "seguir com as recomendações" às Q144-1 a Q144-12 em 29/10/2026 (seção 0). O documento 144 aplicou as respostas Q143 e acrescentou cinco entidades e 56 campos, que entraram no dicionário na revisão 26 (documento 145). As Q144-8, Q144-10, Q144-11 e Q144-12 continuam também no documento 188, para o contador confirmar.

## 1.6 Itens avulsos

| Item | Situação |
|---|---|
| D-N250 (DeSTDA: Paraíba com `Exigida` falso desde 01/01/2026 pela EFD-OIE; texto do aplicativo nacional) e D-N251 (MEI: efeito do desenquadramento, data-limite de comunicação, percentual do primeiro alerta; o limite do transportador ficou fora pela Q85-4) | Propostas do documento 85 que nunca tiveram decisão nem aplicação e não constam do documento 14. Esperam a sua resposta; **a parte do contador** (qual das duas leituras vale para a Paraíba; critério de contagem do MEI, por caixa ou por emissão) **está no documento 188** (C213 e C214). O texto completo está na cópia do documento 85 na pasta ERP-Revisao26 |
| Q80-5 (quais clientes equiparados existem, desde quando são obrigados e o que já foi entregue) | Sem resposta registrada; o Módulo 2 de outubro da DES-IF vence em 10/11/2026 e a resposta dá as primeiras linhas de enquadramento |

## 1.7 Das listas antigas (documentos 38 e 45), sem resposta registrada

| Item | Pergunta | Se não responder |
|---|---|---|
| Q-E | Quais clientes são cooperativas e quantos associados cada uma tem? Já optaram pelo regime específico (prazo 31/10/2026)? A listagem de associados sai do ERP? (D-N39 respondida: há cliente cooperativa; faltam quais e quantos) | Entidades sem carga; sem apoio à listagem de 2026 |
| Q-2 | De onde vem a lista de códigos municipais com alíquotas (Lei 13.701/03)? | Sem carga até haver fonte |
| P46-12 | A Mlegate tem subvenção para investimento concedida hoje? Qual ente, ato e empreendimento? | Sem cadastro inicial |
| D-2, D-3, D-4, D-5, D-7, D-8, D-9, D-11 e D-12 (documento 31) | Decisões técnicas: ordem de implementação (corte mínimo ou completa), identificador bigint ou uuid, competência como `date` com CHECK, mapa de precisão numérica, partição das tabelas, ferramenta de migração, tamanho do texto em chave única, nvarchar e framework de acesso a dados em C#. O DDL já segue a recomendação em D-3, D-4, D-9 e D-11, mas **não há resposta sua registrada** | Segue a recomendação |
| P-19 | Diagramas do modelo ER: Mermaid ou imagem PNG? | Sem resposta registrada |
| P-15 a P-17 e P-33 a P-37 | Confirmar as decisões de 01/10/2026 (provisão da folha, cadastros de vencimento, perfil fiscal, retificação do S-5011 e S-5012, retenções e títulos, pagamento a maior) | Valem como decididas |
| G-10 | Escrituração periódica do IBS/CBS: aguardar o leiaute oficial | Reservar `Cad_Obrigacao_Acessoria` |
| D-N8 | NFS-e do aluguel: a Q85-13 deu as datas (pessoa jurídica locadora em 01/12/2026; pessoa física que abrir CNPJ, em 01/01/2027). Falta o conectivo dos limites da pessoa física ("e" ou "ou") | Premissa do documento 33 |


## 1.8 Documento 161: Ato Técnico Conjunto nº 10/2026 e IT 2025.002 v1.71 (respondidas em 03/11/2026 e 04/11/2026)

O Ato nº 10 (DOU de 29/10/2026) aprova dez conjuntos de documentação das notas (NT 2025.002 v1.53, NT 2026.005 v1.00 do Simples, NT 2026.006 v1.01, NT 2026.007 v1.11, NT 2026.008 v1.01, NT 2026.004 v1.01, NF-e ABI e o IT 2025.002 v1.71). **Li só o Ato e o IT**; as notas técnicas não foram enviadas. A **Q161-1** (`Indicador_Grupo_Biocombustivel_Diferenca`, com `Indicador_Mono_Dif` marcado como excluído pela IT v1.60, sem apagar) e a **Q161-2** (`Codigo_Anexo_Tecnico`, 5 posições, opcional) foram respondidas "Sim" em 04/11/2026 e **entraram na revisão 30** (D-N465 e D-N467): +2 campos em `Cad_Cclasstrib`. Ficam sem aplicar só as notas técnicas, que não foram enviadas.

A **Q161-4** foi atendida por ação em 03/11/2026: você enviou a LC 214 (PDF do DOU e a republicação do Anexo XXIII, que traz 2032 e 2033 do MEI e o DOU cortou), a LC 227 e o Decreto 12.955 consolidado, e escolheu a ordem 156, 157, 150, 158, 159 e 160, em sequência. O documento 156 **entrou na revisão 30**; os demais seguem.

## 1.9 Documento 162: ITs de meios de pagamento, CFOP, NCM e NF-e ABI (respondidas em 03/11/2026)

Nenhuma pergunta aberta: as Q162-1 a Q162-4 foram respondidas "sim" em 03/11/2026 e **entraram na revisão 29** (D-N453 e D-N458). Ficam o Q162-C1 (documento 188), o Q162-E1 e o Q162-E2 (seção 3.1) e os materiais da Q162-4 (seção 3.2).

## 1.10 Documento 163: NT 2026.005 (Simples Nacional na NF-e e NFC-e) e NT 2026.004 v1.00 (respondidas em 03/11/2026)

Nenhuma pergunta aberta: as Q163-1 a Q163-5 foram respondidas "sim" em 03/11/2026 e **entraram na revisão 29** (D-N453 e D-N458). Ficam o Q163-C1 a Q163-C3 (documento 188), o Q163-E1 e o Q163-E2 (seção 3.1) e os materiais da Q163-5 (seção 3.2).

## 1.11 Documento 164: BP-e, modelo 63 (Q164-1 a Q164-12 respondidas em 03/11/2026)

Nenhuma pergunta aberta: você respondeu "Seguir com todas as recomendações" às Q164-1 a Q164-12 e o documento 164 **entrou na revisão 30** (D-N462 e D-N467: 4 entidades, 55 campos e 7 campos no pagamento da nota de saída, mais `Numero_Tar`, os valores de referência e os 8 domínios novos). Confirme a leitura da Q164-1 (seção 0.1). Fica a **Q164-12 como entrega sua**: o MOC do BP-e, o DABPE, o texto da NT 2026.004 v1.01 e das NT 2026.005 (BP-e) e a tabela de cClassTrib do BP-e (seção 3.2). Ficam também as perguntas ao contador Q164-C1 a Q164-C6 (documento 188) e as da equipe Q164-E1 a Q164-E3 (seção 3.4).

## 1.12 Documento 165: entrada de NFGas e NF3e, conferência de NFAg e NFCom e NT 2026.005 SN do CT-e (respondidas em 03/11/2026)

Nenhuma pergunta aberta: você respondeu "Sim para todas" às Q165-1 a Q165-12 em 03/11/2026 e o documento 165 **entrou na revisão 29** (D-N457 e D-N458: 15 entidades e 142 campos novos, mais 23 campos nas entidades existentes junto com os outros itens da revisão). Ficam as perguntas ao contador Q165-C1 a Q165-C5 (documento 188), as da equipe Q165-E1 a Q165-E5 (seção 3.5) e os materiais da Q165-12 (seção 3.2).

## 1.13 Documentos 167 e 168: cobertura do Guia EFD-ICMS/IPI v3.2.4 e desenho das lacunas G1 a G14

O documento 167 (cobertura) e o 168 (desenho de G1 a G14) estão entregues, e o desenho **entrou na revisão 30** (D-N460, D-N461 e D-N467: 11 entidades novas e 26 alteradas), com as respostas Q168-1 a Q168-5 e Q167-1 e Q167-3. A Q167-2 e a Q167-5 foram respondidas em 05/11/2026 e entraram pelo documento 175 (revisão 32; seção 1.21). Adiada:

| Pergunta | Tratamento provisório |
|---|---|
| **Q167-6:** o Bloco 1 de combustíveis e usina (1300 a 1391), em uma revisão própria? | **Você respondeu em 05/11/2026: "Fica para depois, em bloco próprio".** Fora do documento 175; o C171 (tanque) vai junto, no Bloco 1 |

## 1.14 Documento 156: arts. 5º, 57 e 12 da LC 214 (Q156-1 a Q156-15 respondidas em 04/11/2026)

O documento 156 desenha os três artigos juntos (13 entidades novas, 9 alteradas). Você respondeu "Sim" às Q156-1 a Q156-15 em 04/11/2026 (seção 0), com uma regra sua na Q156-8 sobre a variação cambial. O documento **entrou na revisão 30** (D-N463, D-N465 e D-N467: 13 entidades novas e 9 alteradas, mais as cargas provisórias do anexo). Seguem abertas só as perguntas ao contador (documento 188) e à equipe (seção 3.6).

A Q138-4 e a Q138-7, que eu tinha lido por ação, foram confirmadas por você em 04/11/2026 (seção 0).

## 1.15 Documento 157: B0a (Q157-1 a Q157-14 respondidas em 04/11/2026)

Nenhuma pergunta aberta: você respondeu "Sim para todas" em 04/11/2026 (seção 0). O documento 157 **entrou na revisão 31** (D-N477). As perguntas ao contador estão no documento 188 e as da equipe, na seção 3.7.

## 1.16 Documento 150: B5 (Q150-1 a Q150-12 respondidas em 04/11/2026)

Nenhuma pergunta aberta: você respondeu "Sim para todas" em 04/11/2026 (seção 0). O documento 150 **entrou na revisão 31** (D-N477). As perguntas ao contador estão no documento 188 e as da equipe, na seção 3.8.

## 1.17 Documento 170: combustíveis (Q170-1 a Q170-10 respondidas em 04/11/2026)

Nenhuma pergunta aberta: você respondeu "Sim para Todos" em 04/11/2026 (seção 0). O documento 170 **entrou na revisão 31** (D-N477). As perguntas ao contador estão no documento 188 e as da equipe, na seção 3.9. Os textos da Portaria MF 3.074 e da conjunta 14 foram conferidos no documento 194 (seção 0). Seu alerta sobre subsídios por período virou o documento 171 e, depois dos textos oficiais, o **documento 173** (seção 1.18).

## 1.18 Documento 173: programas de apoio aos combustíveis, revisão do 171 com os textos oficiais (Q173-1 a Q173-11 respondidas em 04/11/2026)

O documento 173 **substitui as listas de campos do 171** a partir dos textos que você enviou. Resumo: 5 entidades novas (59 campos), 5 do 171 alteradas (de 75 para 95 campos; 154 no total), 2 valores novos no domínio de agentes, 2 linhas em `Cad_Imposto` (CIDE-COMBUSTIVEIS e IE) e carga provisória de 70 linhas, só de texto oficial. As leituras minhas estão marcadas no documento (fim do etanol em 15/10/2026, programas da MP 1.391, do etanol e da MP 1.358 sem fim no cabeçalho, imposto de exportação de 50% até 31/12/2026 e média simples do desconto do distribuidor). Perguntas ao contador no documento 188 e à equipe na seção 3.10.

Nenhuma pergunta aberta: você respondeu "Sim para todos" às Q173-5 a Q173-11 em 04/11/2026 (seção 0). O documento 173 **entrou na revisão 31** no lugar do 171 (que não entrou). O lado de quem recebe (adesão, item, requerimento, entrada e repasse do distribuidor) **não entrou**: só quando houver cliente (D-N68); a Q173-E2 (seção 3.10) pergunta se já existe.

## 1.19 Documento 172: tabelas do validador da EFD-ICMS/IPI (Q172-1 a Q172-10 respondidas; entrou na revisão 32; sem pergunta aberta)

O documento 172 desenha as 197 tabelas distintas que você enviou (26 UFs, mais 37 nacionais; **RR não tem tabela**): 4 entidades novas (46 campos), 6 alteradas, 4 domínios novos em `Cad_Classe_Sistema`. Você aprovou o desenho em 05/11/2026 (Q172-5 a Q172-10) e ele **entrou na revisão 32** (D-N488). O documento 175 acrescentou a ele a tabela 4.4.6 (21 linhas, de 1.226 para 1.247) e corrigiu o rótulo "5.1.2" do catálogo de ajustes de benefício (documento 175, seção 9). Perguntas ao contador no documento 188 e à equipe na seção 3.11.

## 1.20 Documento 158: B3, compras governamentais e Zona Franca de Manaus e áreas de livre comércio (Q158-1 a Q158-13 respondidas "Sim" em 09/11/2026; entrou na revisão 34; sem pergunta aberta)

Você aprovou as 13 perguntas, e a **Q158-13** mandou aplicar tudo: **entrou na revisão 34** (documento 186, D-N499). As perguntas ao contador estão no documento 188 e as da equipe na seção 3.12.

## 1.21 Documento 175: lacunas setoriais G15 a G19 da EFD-ICMS/IPI, sem o Bloco 1 de combustíveis (entrou na revisão 32; a tabela de cClass da NFGás chegou em 09/11/2026)

O documento 175 **entrou na revisão 32** (D-N488): 27 entidades novas (o C171 saiu para o Bloco 1 de combustíveis) e 22 existentes alteradas junto com os documentos 172 e 176, 13 valores de habilitação por empresa e 4 domínios novos; as Q175-1 a Q175-9 foram lidas como "Sim" (seção 0.1). Perguntas ao contador no documento 188 e à equipe na seção 3.13.

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q175-9 (parte aberta)** | **Respondida em 09/11/2026:** você enviou a tabela de cClass da NFGás, e a Q184-14 aprovou a carga | **Entrou na revisão 34** (46 códigos, 2 campos e o mapa provisório dos grupos; o contador valida o mapa na Q184-C3) |

## 1.22 Documento 176: o FAQ da Receita (EFD-ICMS/IPI v7.8) contra o dicionário (entrou na revisão 32; sem pergunta aberta)

O documento 176 **entrou na revisão 32** (D-N488), com as Q176-1 a Q176-10 ("Seguir com as recomendações"), a Q176-11 e a Q176-12 (lidas como "Sim", seção 0.1) e as respostas C176-1 a C176-3, C176-6 e a do C130: o 1601 derivado das baixas de título (`efd_1601` em `bloco_destino_baixa`, três campos na baixa, `ID_Participante` na instituição financeira, `Cad_Efd_1601_Regra_Uf` com carga provisória de AL, CE, MG, PB, PR, RN e SC); C130 só na saída; C171 no Bloco 1 de combustíveis; `ID_Classe_Enquadramento_Ipi` opcional e `COD_ENQ` vazio; `Informa_Ordem_Producao_Bloco_K` no perfil da filial; quatro motivos novos de reclassificação. Ficam abertas a Q176-C8 (documento 188) e as perguntas à equipe (seção 3.14). O **documento 177** (transação de cartão) altera a leitura do 1601 de cartão e segue na seção 1.23.

## 1.23 Documento 177: transação de cartão e as sete datas (Q177-1 a Q177-5 respondidas "Sim" em 09/11/2026; entrou na revisão 34; sem pergunta aberta)

Você aprovou as cinco perguntas, e o documento **entrou na revisão 34** (documento 186, D-N499). Perguntas ao contador no documento 188 e à equipe na seção 3.15.

## 1.24 Documento 179: a consulta à Receita, reescrita (Q179-1 e Q179-3 abertas)

O documento 179 (D-N489, 05/11/2026) reúne **26 perguntas** prontas para colar no Fale Conosco da Receita (blocos A a D) e, no anexo, o que não é da Receita. Nada foi enviado; o envio é seu.

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q179-1** | Aprova o conjunto das 28 perguntas para envio, na ordem da seção 2 do documento? (Com as Q192-7 e Q193-1 a Q193-3 aprovadas, o conjunto tem **28 perguntas**: a 10 está fechada, a 5 ganhou quatro funções e entraram a 27 e a 28; os textos novos estão no zip do documento 193.) | **Sim**; as que preferir levar ao contador, apague antes de enviar |
| **Q179-3** | **Recebida a planilha do leiaute 12 (24/09/2026), parte (1).** Conferida no documento 193: a carga confere, as perguntas 1 a 9 do documento 179 estão certas e a **pergunta 10 ficou fechada** (sete pontos). **Falta só a (2): a planilha do leiaute 11 (de 2025)**, que traz o texto de 2024 das N620 18, N620 19 e N630A 18 (Q152-4; seguem provisórias em `PENDENTE_Formulas_2024.csv`). Nenhuma outra tabela está pendente para estas perguntas | Reenviar a planilha do leiaute 11 (ou dizer onde está) |

**Do contador, no documento 188:** Q179-2, o canal das perguntas de interpretação (C215). Alberto aprova só o conjunto da Q179-1.

## 1.25 Documento 183: conferência com o Manual da ECD, leiaute 9 (Q183-1 a Q183-10 respondidas em 09/11/2026; entrou na revisão 34; sem pergunta aberta)

Você respondeu as dez perguntas; o núcleo do documento e o que as respostas pedem (documento 184, seção 1.26) **entraram na revisão 34** (documento 186, D-N499). Segue aberta a Q183-C1 (contador, documento 188).

## 1.26 Documento 184: respostas da Q183 e o desenho que elas pedem (Q184-1 a Q184-14 respondidas "Sim" em 09/11/2026; entrou na revisão 34; sem pergunta aberta)

Você aprovou as quatorze perguntas, e o documento **entrou na revisão 34** (documento 186, D-N499). As Q184-3, Q184-5 e Q184-11 pediam listas (empresas com moeda funcional, subcontas de cada empresa, empresa declarante do bloco K); você disse que **não tem a relação agora** e que basta **deixar a opção para quando for necessário**. Pergunta ao contador no documento 188.

## 1.27 Documento 185: IN RFB 2.316/2026 (Sintonia) e o bônus da CSLL (Q185-1 a Q185-3 aprovadas em 09/11/2026; entraram na revisão 35)

O documento 185 (D-N497, 09/11/2026) confere a IN contra os documentos 140, 180 e 181: os percentuais, os limites anuais, os 12 meses de selo, a exclusão do Simples e os motivos de cancelamento **conferem**. A IN **acrescenta**: bônus fora da estimativa mensal (art. 12, § 1º, I), bônus fora da base de qualquer tributo (II), perda do selo com efeito no mês seguinte (§ 2º), a escala A+ a D do Sintonia (art. 8º) e a ciência prévia de indício de infração com 60 dias (art. 14). **Entrou na revisão 35** (documento 195, D-N522).

Você aprovou as Q185-1 a Q185-3 ("Sim para todas", D-N500); o desenho vale como está, com os ajustes do documento 187 (a ciência do indício vale para Confia e Sintonia; as regras do Motor valem como aviso também para o Confia). A **Q185-4** foi atendida em parte: o PDF da LC 225 chegou (texto do art. 41 **confere**); falta o ato do Confia (Q187-3).

## 1.28 Documento 160: parâmetros das outras obrigações (Q160-8 e Q160-9, abertas; sem efeito no dicionário)

As Q160-1 a Q160-7 foram aprovadas em 10/11/2026 (D-N531) e **entraram na revisão 37**: os dois textos de campo no dicionário e as 59 linhas do catálogo, as 6 linhas de obrigação e a correção da linha do rascunho da nota de débito na carga (`Carga37`). Ficam duas perguntas, **ambas com recomendação "não"**, que não mudam o dicionário em nenhum dos dois sentidos; se você pedir "consolidar" sem respondê-las, leio como a recomendação.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q160-8 | Quer um parâmetro "a empresa entrega esta obrigação" em cada obrigação? | Não agora: depende da C99 e mexe na geração dos prazos |
| Q160-9 | Quer migrar algum campo de classe a para o valor central (opção A da Q155-2) já nesta rodada? | Não: a opção B vale |

Do contador não há pergunta nova: a C99 (documento 188) já pede a lista de parâmetros por obrigação, e as 61 linhas passam a ser a lista que ele confere e completa.

## 1.32 Documento 204: tributação do veículo por combustível, potência e demais critérios (Q204-1 a Q204-10, abertas; Q204-11 respondida pelo documento 205)

O documento 204 responde à sua observação sobre o documento 202 (D-N539): o IS dos veículos (MP 1.399/2026, desde 02/02/2027), o IPI até 31/12/2026 e as condições de combustível e cilindrada do art. 149 da LC 214 variam com os mesmos dados do veículo. Propõe 6 entidades novas (119 campos), 8 campos em 3 entidades existentes, 2 domínios, 124 linhas de ajuste, 10 de NCM e 4 parâmetros por empresa. O documento 202 não muda (aprovado em 10/11/2026, D-N541, e já na revisão 39). Nada do 204 foi aplicado; entra no próximo "consolidar" se você aprovar, junto com o B1 do documento 205 (1.179 entidades e 13.468 campos sobre a revisão 39). Ao contador, C256 a C265 (documento 188, Parte 12).

| Id | Pergunta | Recomendação |
|---|---|---|
| Q204-1 | Aprova o **escopo** do documento 204: a tributação do veículo por propulsão, potência e demais critérios no **Imposto Seletivo** (veículos, aeronaves e embarcações dos Anexos I, II, III e V da MP 1.399), no **IPI até 31/12/2026** e nas condições do **art. 149 da LC 214** (táxi, PcD e TEA), com **seis entidades novas**, 8 campos em entidades existentes e 2 domínios? Bebidas, fumígenos e minerais (Anexos IV e VI) ficam para outro documento. | Sim |
| Q204-2 | Aprova a **ficha da versão do veículo** (`Cad_Veiculo_Versao`, 27 campos, com vigência) e o **registro de versão sustentável** (`Cad_Veiculo_Versao_Sustentavel`, 17 campos), com a ficha ligada ao produto e a nota continuando a levar os campos do XML? | Sim |
| Q204-3 | Aprova a **tabela de ajustes** (`Cad_Is_Veiculo_Ajuste`, 16 campos, com vigência) e a **carga provisória de 124 linhas**: 62 do Imposto Seletivo (desde 02/02/2027) e 62 do IPI (de 01/11/2025 a 31/12/2026)? | Sim |
| Q204-4 | Aprova os **6 campos novos** de `Cad_NCM_Imposto_Seletivo` (modo da alíquota, inicial, fator de conversão, fator de importação, tabela e piso) e as **10 linhas provisórias** de NCM (veículos 87.03 e 8704, aeronaves e embarcações), mantendo o NCM como base, como você decidiu na Q196-8? | Sim |
| Q204-5 | Aprova a **apuração do item de veículo** (`Mov_Is_Veiculo_Apuracao`, 22 campos) e a **regra de cálculo** da seção 5.4: base + cinco ajustes, piso de zero, fator 1,21, fator 1,17 na importação, as oito hipóteses de alíquota zero e de não incidência e a memória da conta? | Sim |
| Q204-6 | Aprova o **reconhecimento e a utilização do benefício do art. 149** (`Cad_Beneficio_Veiculo_Reconhecimento`, 16 campos, e `Mov_Beneficio_Veiculo_Utilizacao`, 21), com o intervalo mínimo, o preço máximo, as quatro portas, a motorização do táxi e a alienação antecipada? A alternativa é deixar o art. 149 só nos parâmetros que já existem. | Sim |
| Q204-7 | Aprova `ID_Veiculo_Versao` nos itens da nota de saída e de entrada (2 campos) e o aviso do Motor quando os cavalos da nota (`Veiculo_Potencia_Cv`) não batem com os quilowatts da ficha (1 cv = 0,7355 kW)? | Sim |
| Q204-8 | Aceita a **carga provisória e visível**: toda linha de MP nasce `provisorio`, com o fundamento "MP 1.399/2026", sem fim de vigência, e o relatório do Motor avisa quando um cálculo usa linha provisória, até a MP ser convertida (C265)? | Sim |
| Q204-9 | Aprova os **4 parâmetros por empresa** da seção 5.8 (arredondamento da alíquota, item sem CAT, kW derivado do cv e tabela para posições fora da lista), com padrão provisório, aviso a cada uso e a documentação de efeito da regra do documento 201? | Sim |
| Q204-10 | Mantém o documento 202 **como está** (nada muda nas oito entidades) e trata a alíquota `Al` do crédito presumido (C252, C264) depois que o contador responder? A alternativa é rever o documento 202 antes das suas respostas. | Manter |
| Q204-11 | **Respondida pelo documento 205**: você enviou a Tipi, o Decreto 9.557, a LC 214 compilada e as leis; li os textos atuais das Notas Complementares 87-2, 88-1, 88-2, 88-3 e 89-1 (seção 4.1 do documento 205). Li também o Anexo XVII da LC 214 (seção 4.4 do documento 205). Fica sem leitura o ato do MDIC sobre a versão sustentável. | Só se quiser enviar o ato do MDIC |

## 1.33 Documento 205: conferência das oito normas do automotivo (Q205-1 a Q205-4, respondidas em 10/11/2026)

O documento 205 conferiu as normas que você enviou sem mensagem com os documentos 202 e 204. O **202 e o 204 se mantêm**; há uma correção minha no 204 (a NC 87-2 é a das ambulâncias, carros celulares e carros funerários; a NC 89-1 é a das empresas de turismo), dois campos novos no 204 (qual nota complementar vale na venda) e três campos, um valor e dois avisos novos no 202 (a informação anual de 31/07 e a intimação de 30 dias dos Decretos 10.457 e 7.422, que valem pelo art. 518, § 5º, do Decreto 12.955). A Tipi que você enviou **não traz o Decreto 12.549** no capítulo 87, e isso muda a fonte da alíquota `Al` da Lei 9.826. O documento 205 só vale junto com o 202 e o 204.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q205-1 | Aceita a **correção** do documento 204: a NC 87-2 é a das ambulâncias, carros celulares e carros funerários; a NC 89-1 é a das empresas de turismo; a Q204-11 fica respondida e os textos atuais das notas passam a ser os da seção 4.1 do documento 205? | **Respondida: sim.** Aprovada, ainda não aplicada (D-N544). |
| Q205-2 | Aprova o ajuste **B1**: `Condicao_Nota_Complementar` e `ID_Documento_Condicao` em `Mov_Is_Veiculo_Apuracao` (24 campos) e as regras do Motor da seção 5.1, com a NC 88-3 fora até o complemento da C263? | **Respondida: sim.** Aprovada, ainda não aplicada (D-N544). |
| Q205-3 | Aprova o ajuste **A1** no documento 202: três campos novos e um valor novo em `Mov_Habilitacao_Automotiva_Compromisso` (17 campos), dois avisos (22 no total) e nenhum parâmetro novo, com o saldo de pesquisa, a perda do direito e a declaração do máximo de fruição **fora** até a C267? | **Respondida: sim.** Aprovada (D-N544) e **aplicada na revisão 39** (documento 208). |
| Q205-4 | Pede que eu prepare, num próximo documento, a **tabela da alíquota de IPI de 31/12/2025** das posições 8702 a 8704 (Decreto 12.549, Anexo I, com as Notas Complementares e as reduções da Rota 2030 que valiam em 31/12/2025), como carga provisória da `Al` da Lei 9.826, e envia, quando puder, a **Tipi consolidada da Receita** com o Decreto 12.549 incorporado? | **Respondida: preparar.** O documento da tabela de IPI será o próximo; falta a Tipi consolidada, que você enviará (D-N544). |

## 1.34 Documento 206: Programa Mover e Rota 2030, bloco B8 (Q206-1 a Q206-12, abertas)

O documento 206 desenha o programa inteiro que você escolheu: **ato de registro de compromissos** (Decreto 12.435), **habilitação e crédito financeiro de P&D** (Lei 14.902, crédito de CSLL) e **regime de autopeças não produzidas**, mais o **legado do Rota 2030**, que acabou em 30/11/2023 e só mantém direitos adquiridos. São 18 entidades novas, 34 linhas de parâmetros, 80 linhas do Anexo I do Decreto 12.435 e 4 obrigações novas. O modelo de pedido que você enviou é de 2018 e a aba Pontuação não foi modelada.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q206-1 | Aprova o **grupo 1** (ato de registro, requisitos por ano e importação sem ato: 3 entidades)? | Sim |
| Q206-2 | Aprova o **grupo 2** (habilitação, projeto, cronograma, autorização anual, dispêndio, mínimo, crédito, indicador, aporte e ocorrência: 10 entidades) e as regras do 5.7? | Sim |
| Q206-3 | Aprova o **grupo 3** (item importado e contrapartida das autopeças: 2 entidades; a lista entra na lista legal)? | Sim |
| Q206-4 | Aprova o **grupo 4** (`Mov_Mover_Obrigacao_Acessoria` e o legado `Mov_Rota_2030_Deducao`) e as 4 obrigações novas no catálogo? | Sim |
| Q206-5 | Mantém o legado do **Rota 2030** (habilitação `rota_2030` e dedução com excedente), mesmo com a habilitação extinta em 2023? | Sim: o excedente pode estar em uso (C276) |
| Q206-6 | O ERP só **registra** a multa compensatória de eficiência energética e de desempenho estrutural, sem recalcular as faixas? | Sim |
| Q206-7 | Usa **30%** na multa das autopeças (lei) e não 100% (Decreto 9.557)? | Sim (C275) |
| Q206-8 | Aceita a **leitura provisória** do crédito: 50% soma os pontos dos indicadores, o limite de receita substitui o de 5% e o mínimo sai dos primeiros dispêndios do ano? | Sim, provisória (C274) |
| Q206-9 | Aceita a **base da multa de importação sem ato**: (valor aduaneiro + tributos) × 1,20 × 20%? | Sim, provisória (C271) |
| Q206-10 | Envia a **lista vigente de autopeças não produzidas** (ato da Camex, por NCM)? | Enviar |
| Q206-11 | **Não modela** a aba Pontuação do modelo (14 perguntas, 25 pontos, fórmulas quebradas) até saber a que processo serve? Se você souber, diga. | Sim: não modelar |
| Q206-12 | Aprova o campo novo `ID_Mover_Ato_Registro` em `Cad_Veiculo_Versao_Sustentavel` (documento 204) e os 3 valores novos de enumeração? | Sim |

# 2. Para o contador

**Esta seção não guarda mais perguntas.** Por regra de Alberto (09/11/2026, D-N501), **todas as perguntas e pendências do contador ficam somente no documento 188**, com cada pergunta detalhada (de onde vem, texto completo, o que o ERP faz enquanto isso e campos para resposta, data e situação). São **277 perguntas** (C1 a C277). Quando o contador responder, atualizo o 188 e, para o que é de Alberto, esta lista.

| Parte do documento 188 | Assunto | Perguntas |
|---|---|---|
| Parte 1 | ECF, Y520 e cadeia do lucro real | 13 (C1 a C13) |
| Parte 2 | Listas antigas: tributos federais, vencimentos, EFD-Contribuições, DES-IF, DeSTDA e SUP | 29 (C14 a C42) |
| Parte 3 | ECF, presumido, caixa, encontro de contas, moeda estrangeira e adiantamento (documentos 100 a 155) | 57 (C43 a C99) |
| Parte 4 | IBS e CBS, documentos fiscais, EFD-ICMS/IPI, combustíveis e ECD (documentos 144 a 185) | 112 (C100 a C211) |
| Parte 5 | Itens que estavam na seção 1 e são do contador | 4 (C212 a C215) |
| Parte 6 | Documentos 189 a 194: CNPJ, suspensão do IPI, Lei 10.485, Confia (IN RFB 2.295), REIDI, registro 0000 da ECF e IBS do EAC e do B100 | 10 (C216 a C225) |
| Parte 7 | Documentos 159 e 196: consulta, multas, ordem de aplicação, PNCT, documento consolidado e Imposto Seletivo (LC 227) | 7 (C226 a C232) |
| Parte 8 | Documento 198: regimes específicos de serviços financeiros, seguro e plano de saúde (B4) | 6 (C233 a C238) |
| Parte 9 | Documento 200: crédito do tomador do serviço financeiro, arrendamento, antecipação e plano de saúde (B0b-2) | 7 (C239 a C245) |
| Parte 10 | Documento 201: efeito do crédito do tomador na ECD e na ECF, e a dedução da despesa na DeRE do tomador | 2 (C246 e C247) |
| Parte 11 | Documento 202: regime automotivo (mês de fruição, IPI na base, débitos próprios, tratamento contábil, alíquota de IPI, partes e peças, "veículo" na fração e devolução) | 8 (C248 a C255) |
| Parte 12 | Documento 204: tributação do veículo (arredondamento do IS, desempenho estrutural, kW, posições fora das listas, versão sem CAT, táxi, obrigação do IS, notas da Tipi, IPI da Lei 9.826, conversão da MP) | 10 (C256 a C265) |
| Parte 13 | Documento 205: conferência das normas do automotivo (alíquota `Al` de 31/12/2025, condições dos Decretos 10.457 e 7.422 e conflito com o art. 315, numeração das notas da Rota 2030); a C263 ganhou complemento | 3 (C266 a C268) |
| Parte 14 | Documento 206: Programa Mover e Rota 2030 (importação sem ato, multa por requisito, dispêndio mínimo e indicadores, autopeças com multa de 30% ou 100%, excedente do Rota 2030, tratamento do crédito financeiro) | 9 (C269 a C277) |

**Passaram da seção 1 para o documento 188:** Q93-7 (C8), Q118-2 (C9), Q122-1 (C11), Q130-4 (C12), Q140-6a a 6e com a Q185-C1 (C212), a parte do contador das D-N250 e D-N251 (C213 e C214), a Q179-2 (C215) e os prazos que só o contador cumpre (apêndice A).

# 3. Para a equipe e fontes oficiais

| Pendência | Tratamento provisório |
|---|---|
| **Primeira execução do DDL num SQL Server**: o T-SQL foi lido pelo analisador (18.595 comandos na revisão 32, nenhum erro de leitura) e nunca executado | PostgreSQL 16 sem erro |
| **Q163-E1 e Q163-E2** (documento 163): datas da NT 2026.004 da NF-e (teste até 15/06/2026 na v1.01, que era 01/06/2026 na v1.00, e produção 01/07/2026, contra 06/04 e 06/07/2026 do documento 34) e valores dos domínios `tipo_receita_bruta_sn` (0 a 5 e 9) e atividade do Simples (se tem 01 a 04) | Vale a data da v1.01, com vigência; carga como publicada |
| **Q162-E1 e Q162-E2** (documento 162): conferir a carga de NCM contra o histórico do IT 2024.001 v2.40 (NCM 85181020 desde 01/10/2026 e sucessões 1 para vários da v2.30) e se o domínio `tPag` já tem os códigos 23 (Pix automático) e 24 (TEF / booktransfer) | Carga como publicada na tabela do portal; 23 e 24 provisórios no domínio do vínculo |
| Manual do eSocial: código de retorno de "registro já existe" (D-N301 a D-N303) e o `dtBase` no MOS (D-N304) | Classificação do retorno em catálogo com vigência |
| Carga do leiaute 12 da ECF, extraída do manual por mim: provisória até o contador validar (D-N320); a versão do leiaute (12 ou 13) é decisão do operador do sistema (D-N340) | Carga provisória |
| Ato da RFB que regulamenta Confia, Sintonia, OEA e selos (LC 225, arts. 29 e 47); seções do CCT e do Siscomex Importação, valores das tabelas do Portal que só saem autenticadas (métodos de valoração, acréscimos e deduções, motivos sem cobertura, regimes, fundamentos, recintos; carga pela API na Q144-7; a consulta pública do TTCE pediu CAPTCHA e não foi contornada), PDF de Perguntas e Respostas da NFS-e v1.00 de 08/09/2026 (regra da locação por pessoa física; Q144-8) e Anexos VI v1.03.00 e VII v1.01.00 da NT 007 da NFS-e (documentos 34, 143 e 144) | `ID_Classificacao` do programa fica sem carga; B1 segue o Anexo I da Nota 77, os manuais de 2018 a 2020 (os mais recentes, Q141-8) e as especificações da API lidas nos documentos 143 e 144; os campos de tabelas autenticadas ficam livres até a carga |

## 3.1 Das listas antigas, sem registro de resposta

| Item | Pendência |
|---|---|
| P40-04, P40-05 e Q-5 e Q-6 do documento 42 | Conflito das datas e do total do documento na NT 2026.004 (perguntar à Receita ou ao ENCAT) |
| Q-3, Q-7, Q-12, Q-13 e Q-15 do documento 41 e N-1 a N-11 | NFS-e Nacional: sinal de `vAjusteBCIBSCBSComExt`, `regApIBSCBSSN` = 2, cronograma do leiaute 1.04.01 e o XSD 1.04 |
| Q-N1 a Q-N11 do documento 40 | MOC da NFCom: versão nova, `cClass`, URLs por UF e divergências internas |
| Q-4, Q-8, Q-9, Q-10 e Q-15 do documento 42 | Alíquotas da CBS de 2027 e do IBS de 2029 em diante; inconsistências do MOC e das NTs do CT-e |
| P43-03, P43-06, P43-07 e P43-08 (revista) | Fontes: Convênio ICMS 142/18, tabela de países do Bacen, IBGE; óleo diesel por unidade sem linha depois de 31/05/2026 |
| P-22 | Qual das duas versões da Tabela 01 da Reinf é a mais nova |
| P-01 a P-09, P-24 e P-40 | Primeiro XML real da DCTFWeb (nenhum bloqueia; valor bruto guardado) |
| P-25 a P-27 | Limitações assumidas (declarante pessoa física no eSocial, categoria Aferição/Sero, PER/DCOMP sem transmissão) |
| Q61-x, Q62-x e Q67-x (documentos 61, 62 e 67) | Se algum ficou sem resposta, não consta nos registros que consultei |

## 3.2 Materiais oficiais que ainda não chegaram

Ato COTEPE 47/15 e manual do SEDIF-SN (DeSTDA); Manual do PGDAS-D e do DAS-MEI de 2027 e art. 30 da Resolução CGSN 140; demonstrativo de gastos tributários da LOA 2026; Anexo III antigo da IN RFB 2.119/2022 e lista de valores da situação cadastral do CNPJ; valores trimestrais da TJLP, IN RFB 1.700 (art. 75) e IN RFB 1.037 atual; texto da LC 235/2026; Catálogo de Serviços e Swagger do Integra Contador e páginas de pagamentos e situação da API de Débitos da CBS; Anexo I do MOC da NF-e ABI e NT do DANFE-ABI; NFCom (tabela `cClass`, URLs e WSDL por UF); XSD do leiaute 1.04 da NFS-e; Anexo I do MOC do CT-e; PL_010g, schema do evento 110300 final e IT 2026.001 (meios de pagamento); NT 2026.004 v1.01 do RTC (a v1.01 da NF-e e NFC-e chegou em 03/11/2026, é outra nota), NT 2026.005 das versões CT-e, CT-e OS, NFCom e BP-e, NT 2025.002 v1.53, NT 2026.006 v1.01, NT 2026.007 v1.11 e NT 2026.008 v1.01, e NT 2026.001 da NF-e ABI (a NT 2026.005 da NF-e e a NT 2026.004 v1.00 da NF-e já chegaram, e em 03/11/2026 também os pacotes de schemas do BP-e, sem os textos das NT; nas Q162-4 e Q163-5 você respondeu "sim" e ainda não chegaram), Tabela de Códigos v1.01 da NF-e ABI, planilha de CFOP v2.10 e tabela de NCM em uso, MOC, DABPE e tabela de cClassTrib do BP-e (Q164-12) (Ato nº 10/2026 e ITs de 03/11/2026, documentos 161 e 162; o IT 2026.003 v1.00 já chegou); Guia atual da EFD-Contribuições; **planilha do leiaute 11 da ECF** (as fórmulas de 2024 da N620 18, N620 19 e N630A 18, Q152-4; reenviar);  tabela 4.5.4 da EFD ICMS/IPI (as demais tabelas externas chegaram no documento 172); manual atual do CNO; tabela de códigos de receita do MIT; pacote XSD do eSocial posterior a 26/10/2026 e primeiro XML real da DCTFWeb; série da tabela do ISS fixo desde 2004. Do documento 165: texto das NT 2026.001, .002, .004 e .005 de NFAg, NFGas, NF3e e NFCom e das NT de CT-e (schemas e MOCs vieram, textos não); MOC da NF3e e da NFCom; tabelas de classificação de item (`cClass`) do gás e da energia.

**Dos documentos 170 e 173 (Q170-9 e Q173-E3).** **Já chegaram** (04/11/2026): as MPs 1.340, 1.349, 1.358, 1.363 e 1.391; os Decretos 12.878, 12.930 e 12.995; a Portaria MF 2.946 e o Alerta Legislação nº 38; o Decreto 13.119 (etanol) li pela página do Senado. **Chegaram em 09/11/2026** o texto da Portaria MF nº 3.074/2026 e o da Portaria conjunta MF/CGIBS nº 14/2026 (Q170-9 atendida; documento 194). **Faltam:** a Portaria MF 2.813 e a prorrogação de 26/10/2026; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha da MP 1.391 e do etanol); a LC 235; o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio (hoje só pelas redações do texto consolidado dos outros decretos); e, quando saírem, o ato do QAV e o que valer para 2027.

**Do documento 172:** as tabelas do validador da EFD-ICMS/IPI chegaram (197 tabelas, 04/11/2026), então saem desta lista as tabelas 5.1.1, 5.2, 5.3 e 5.6 a 5.9.1 por UF. Faltam a versão para comparação do cBenef (Q172-E1) e a forma de chegada do validador novo (Q172-E5).

**Do documento 196 (Q196-10, você respondeu "Seguir com as recomendações", que inclui enviar):** o texto oficial da MP 1.399/2026 **chegou em 10/11/2026** (você o enviou; os Anexos I a III e V dos veículos, aeronaves e embarcações foram conferidos e estão no documento 204; os Anexos IV e VI, de bebidas e fumígenos, e a unidade da vintena seguem sem desenho). Falta o ato do chefe do Poder Executivo com a metodologia do valor de referência (art. 414, § 2º).

**Do documento 198 (Q198-12, você respondeu "seguir", que inclui enviar):** o manual oficial da DeRE (pacote 1.3.0, Anexo I e Tabelas 11 e 12) e o ato conjunto do fator de redução da importação (art. 328, § 5º). Com eles confiro o leiaute dos registros, os `codTrib` da Tabela 11, a Tabela 12 e o evento D-1106 do ativo garantidor.

**Do documento 164 (Q164-12, você respondeu que envia):** o MOC do BP-e, o DABPE, o texto da NT 2026.004 v1.01 e das NT 2026.005 (BP-e) e a tabela de cClassTrib do BP-e.

## 3.3 Novos, dos documentos 100 a 116

| Pendência | Tratamento provisório |
|---|---|
| **Carga das instituições financeiras atuais** com `ID_Pais` = Brasil (o campo agora é obrigatório) | Carga provisória gerada em 28/10/2026 (1.061 instituições ativas, `Cad_Instituicao_Financeira_carga_provisoria.csv`): lista do Banco Central (ativas), STR e Pix, com ISPB e código de compensação. Você disse "só subir as ativas". Faltam três pontos seus: `Vigencia_Inicio` (usei 2000-01-01, as fontes não informam), a chave de `Cad_Pais` no lugar do texto `BRA` e se as cooperativas entram (ISPB pela raiz do CNPJ, só nas que o Pix ou o STR confirmam) |
| **Banco de dados e gerador do DDL** (documento 129): se aceitam índice único que ignora valores vazios (dois índices simples em `Codigo_Ispb` e `Codigo_Swift` dariam a unicidade da instituição no banco) | A camada de integração impede a duplicidade até a TI responder |
| Canal da ordem de pagamento ao exterior de cada banco do cliente (documentos 107 e 124) | Desenho aprovado; o plugin de cada banco trata o canal |
| **Unicidade das janelas e do código do tipo de baixa** (documento 113): o banco aceita duas linhas de `Cad_Tipo_Baixa_Bloco` com o mesmo tipo, bloco e `Vigencia_Inicio` (como nas outras janelas) e o código de `Cad_Tipo_Baixa` | A camada de integração impede |
| **Área de inconsistências** (Q113-11): cada processo automático (retorno bancário, baixa automática, carga da cotação do Banco Central, geração do Y520, importações) precisa gravar nela quando falhar ou depender do usuário, e reprocessar o registro depois do tratamento | A fazer na implementação (`Mov_Processo_Inconsistencia` entrou na revisão 25, documento 133) |
| **Retorno bancário, telas e relatórios de saldo** (fora do dicionário): a baixa automática precisa preencher `ID_Tipo_Baixa` pelo de-para entre a forma e o tipo (Q113-5; sem tipo mapeado, a operação para e pede ao usuário que relacione; no retorno, o item vai para a área de inconsistências, Q113-11; só o perfil de cadastro relaciona); o saldo do título não soma mais `Valor_Encontro`; a conciliação lê `Valor_Financeiro` (documento 113, seção 5) | A fazer na implementação |
| Formato e dígito de controle do IBAN, do SWIFT e do código de roteamento por país: o dicionário só guarda o valor | Sem validação de formato |
| **Código do CNAB e do PIX** (fora do dicionário): tratar `Codigo_Ispb`, `Agencia` e `Numero_Conta` como opcionais, obrigatórios só para instituição brasileira (documento 108, seção 5) | A fazer na implementação |

## 3.4 Novos, do documento 164 (BP-e)

| Pendência | Tratamento provisório |
|---|---|
| **Q164-E1** (equipe): datas das NT do BP-e (homologação e produção) e a marca de 01/12/2026 do BP-e aéreo (documentos 14 e 161); os schemas não trazem data e os textos das NT não vieram | `BPE-NT-DATAS` sem valor; a marca de 01/12/2026 fica como leitura anterior, não confirmada |
| **Q164-E2** (equipe): conferir no DDL se `xPag` e `xBand` já existem em `Mov_Nota_Fiscal_Saida_Pagamento` (os comentários mostram 10 colunas, sem eles) | Contados como novos até a conferência |
| **Q164-E3** (equipe): o `indFornecimento` do BP-e metropolitano diz que dispensa o "evento de confirmação de embarque", que não está nos schemas; ele existe? | Sem desenho |

## 3.5 Novos, do documento 165 (entrada de NFGas e NF3e)

| Pendência | Tratamento provisório |
|---|---|
| **Q165-E1** (equipe): conferir no DDL se já existem os campos de nota antecipada em `Mov_Nota_Fiscal_Entrada_Item` e de nota em papel em `Mov_Nota_Fiscal_Entrada_Referenciada` | Contados como novos até a conferência |
| **Q165-E2** (equipe): eventos dos MOCs da NFGas e da NFAg além de cancelamento, vínculo e Simples: ler e desenhar | Sem desenho |
| **Q165-E3** (equipe): o MOC da NFAg 1.00l não cita `tpFat` 4 e 5 e o MOC da NFGas tem inconsistência sobre o `tpFat` (G47 e G60, obrigatoriedade da `gFat`); confirmar com o autorizador | Vale o schema |
| **Q165-E4** (equipe): mapear classe, fase e tensão às tabelas SPED 4.4.5, 4.4.2 e 4.4.3 usadas em `Mov_Nota_Fiscal_Utilidade` | Domínios por modelo até o mapa |
| **Q165-E5** (equipe): datas das NT de NFAg, NFGas, NF3e, NFCom e CT-e (2026.001, .002, .004 e .005); os schemas não trazem data e os textos não vieram | Sem valor em `Cad_Dfe_Leiaute` e nos parâmetros |

## 3.6 Novos, do documento 156 (arts. 5º, 57 e 12)

**Q156-E1:** o leiaute da NF-e (NT 2025.002 e as seguintes) separa o desconto condicional do incondicional no item? Provisório: se não separar, `Valor_Desconto_Condicional_Item` é controle do ERP e não vai no XML.

## 3.7 Novos, do documento 157 (B0a)

| Nº | Pergunta | Provisório |
|---|---|---|
| **Q157-E1** | Na NFS-e nacional, o campo de competência da DPS basta como data do fato gerador, ou a DPS precisa dos três campos do item da nota? | Só nas notas de produto |
| **Q157-E2** | O leiaute da nota de saída (NF-e e NFS-e) tem o grupo do pagamento antecipado (NT 2025.002; documento 34)? | Sem campo até a conferência |
| **Q157-E3** | Existe ligação entre `Mov_Credito` (tipo pagar) e `Mov_Credito_Fiscal` para o crédito do adquirente na extinção do débito da antecipação (LC, art. 10, § 6º)? Se não, propor `ID_Credito_Origem` em `Mov_Credito_Fiscal`. | Sem campo até a conferência |
| **Q157-E4** | Qual é a fonte da série da Selic (acumulada no mês) para `Cad_Serie_Cotacao`? | Série vazia |

## 3.8 Novos, do documento 150 (B5)

| Nº | Pergunta |
|---|---|
| **Q150-E1** | A Folha terá rubrica de gorjeta repassada ao empregado, para a origem `folha` da conferência (`Mov_Gorjeta_Repasse_Periodo`)? Até lá o repasse é informado. |
| **Q150-E2** | O PDV de bares e restaurantes consegue lançar gorjeta e valor de plataforma como itens próprios da nota (a segregação do art. 399, § 2º)? |
| **Q150-E3** | Há sistema de reservas ou de hospedagem que entregue início e fim da ocupação à locação por temporada, ou o cadastro será feito no ERP? |
| **Q150-E4** | O total de fornecimentos do associado à cooperativa sai da apuração por cClassTrib da nota; confirmar que as notas à cooperativa carregam o cClassTrib da redução do art. 391, I. |
| **Q150-E5** | A conferência da transferência de crédito lê o saldo credor da conta `saldo_credor_periodo_seguinte` do espelho da apuração (`Mov_Cbs_Apuracao_Espelho_Conta`) e a situação `concluida` do período: confirmar que essa conta é o saldo credor do art. 44 e que ela fica disponível quando o período conclui. |
| **Q150-E6** | Agência de turismo (Decreto, art. 420): o cálculo do crédito da agência já deixa de fora o valor que ela deduziu da base (`Valor_Deduzido` em `Mov_Agencia_Turismo_Repasse`), ou precisa de regra? |

## 3.9 Novos, do documento 170 (combustíveis)

| Nº | Pergunta |
|---|---|
| **Q170-E1** | A conversão do volume a 20 °C (Decreto, art. 260, § 2º) já vem feita do PDV ou do sistema do posto? O item tem `Combustivel_Quantidade_Temperatura_Ambiente`; confirmar que `Quantidade_Tributada` recebe a quantidade já convertida. |
| **Q170-E2** | O cadastro de unidades de medida (`Cad_Unidade_Medida`) tem litro, quilograma e metro cúbico com os símbolos do leiaute? A nota de combustível sai com a unidade da seção (art. 261, § 2º). |
| **Q170-E3** | A tabela da ANP (`Cad_Produto_Anp`) já está carregada com vigência? O vínculo da seção 6 depende dela. |
| **Q170-E4** | O exportador de combustíveis mantém o crédito (Decreto, art. 267, § 2º). Não verifiquei se o dicionário já cobre isso nos documentos de exportação: confirmar. |
| **Q170-E5** | A nota de entrada com gMonoRet chega pelo XML? Confirmar que o ERP lê o grupo e grava uma linha de complemento por item e tributo. |
| **Q170-E6** | Há cliente ou fornecedor que seja refinaria, formulador, importador ou distribuidora com mistura de EAC? Isso responde à Q170-8. |

## 3.10 Novos, do documento 173 (programas de apoio aos combustíveis; substituem a seção do 171)

| Nº | Pergunta |
|---|---|
| **Q173-E1** | O destaque do desconto na NF-e fora da MP 1.363: qual campo e qual frase na MP 1.391, no etanol e nos programas anteriores? Só **Informações complementares** com texto livre, ou há campo estruturado em nota técnica? Preciso do leiaute ou da NT. |
| **Q173-E2** | Algum cliente ou fornecedor da Mlegate é produtor, refinaria, importador, **distribuidor** de diesel, GLP ou etanol que adere aos programas? Isso responde à Q173-8 (e à Q171-E2). |
| **Q173-E3** | Mandar os textos que faltam: Portaria MF 2.813 e a prorrogação de 26/10; o ato do Ministro da MP 1.358; os atos da ANP (adesão, períodos e planilha da MP 1.391 e do etanol); a LC 235; o Decreto 13.116; os Decretos 12.883, 12.942, 12.974 e 12.992 em arquivo próprio; e, quando saírem, o QAV e o que valer para 2027. |
| **Q173-E4** | Método do desconto médio do distribuidor (Decreto 12.930, art. 11, § 1º, IV, redação do 12.974): média do lote, do mês ou do saldo corrente? A ANP tem modelo de planilha (Decreto 12.995, art. 6º)? |
| **Q173-E5** | O distribuidor envia à ANP, a cada 14 dias, volumes e valores médios de compra e de venda (Decreto 12.930, art. 20). O ERP precisa gerar esse relatório? |
| **Q173-E6** | O contas a receber tem tipo de título para a subvenção, com a ANP como órgão pagador? O ERP emitiu notas de diesel, GLP ou etanol em 2026 com desconto de subvenção, e precisamos do histórico? (juntam Q171-E4 e Q171-E6) |

## 3.11 Novos, do documento 172 (tabelas do validador da EFD-ICMS/IPI)

| Nº | Pergunta | Por que importa |
|---|---|---|
| **Q172-E1** | Há um arquivo de cBenef (por exemplo o da NF-e) para comparar com os códigos de ES e DF da informação adicional? | Confirma a ligação opcional da Q172-1 e dá a conferência. |
| **Q172-E2** | Há interesse em relacionar o valor por profissional do DF ao ISS fixo do DF? | Sem interesse, o valor só é guardado. |
| **Q172-E3** | Conferir os códigos de energia, água e gás (CLASCONS) com a fonte do documento 43: quem confere a diferença? | A carga só lista. |
| **Q172-E4** | Em que UFs a Mlegate tem clientes? (repete a Q173-E2) | Pela D-N68, o que é só de um regime entra quando há cliente; aqui a lista decide quais tabelas de UF o contador valida primeiro. |
| **Q172-E5** | Como o validador novo chega à equipe (download manual do PVA, pacote do portal)? | Define a rotina de recarga e o aviso de "tabela mais nova disponível". |

## 3.12 Novos, do documento 158 (B3)

| Nº | Pergunta |
|---|---|
| **Q158-E1** | Os códigos dos eventos fiscais de **internamento**, de **conclusão do desembaraço** e de **não internamento** não estão nos documentos que tenho (vêm de nota técnica). Quando a NT chegar, entram em `Cad_Dfe_Evento_Tipo` com autor `suframa` ou destinatário. Há uma NT em mãos? |
| **Q158-E2** | Manaus, Rio Preto da Eva e Itacoatiara entram só em parte na ZFM (Decreto, art. 433, I). O ERP guarda o município, e não o endereço dentro da parte demarcada. Aceito que o usuário informe a marca `Eh_Parcial` e confirme no cadastro do destinatário? |
| **Q158-E3** | O cadastro de clientes já traz a inscrição Suframa em `Cad_Participante_Inscricao` (`Tipo_Inscricao` = suframa) e a nota já leva o número em campo próprio (Decreto, art. 529, § 2º)? Se não, o cadastro de inscrições é o ponto de entrada. |
| **Q158-E4** | Há hoje cliente na ZFM ou nas ALC? A resposta define a prioridade do internamento e da importação com suspensão na implantação. |

## 3.13 Novos, do documento 175 (lacunas setoriais da EFD-ICMS/IPI)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q175-E1** | A Mlegate (ou algum cliente) recebe nota modelo 02 **só consolidada**, sem as notas individuais? Se sim, criamos uma consolidação como a do Convênio 115. | Não há caso conhecido; fica sem estrutura. |
| **Q175-E2** | `Mov_Cte` aceita o BP-e (modelo 63), sem `COD_PART`, `SUB` e `IND_FRT`? | A verificar. |
| **Q175-E3** | Consequência de Q172-C1 ("só o Guia"): as linhas dos catálogos do validador que o Guia não traz ficam com `Tabela_Origem` do validador. Está correto manter assim? | Sim. |

## 3.14 Novos, do documento 176 (FAQ da Receita sobre a EFD-ICMS/IPI)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q176-E1** | A baixa de título por retorno bancário já traz a instituição do repasse? (para propor `ID_Participante_Instituicao_Pagamento` a partir de `Cad_Conta_Bancaria`) | A verificar. |
| **Q176-E2** | A baixa por cartão ou por marketplace chega com a credenciadora? Hoje ela só está na nota (`Mov_Nota_Fiscal_Saida_Pagamento`). | A verificar. |
| **Q176-E3** | A entrada em estoque por transferência acontece na entrada física da nota (C170 da filial de destino) ou na saída da origem? | Na entrada física (FAQ 16.3.1.19). |
| **Q176-E4** | O Motor distingue produção sem ordem de ordem sem apontamento? (viabilidade da Q176-8) | A verificar. |
| **Q176-E5** | O Motor acha a filial que informa o 1601 pela conta bancária onde o dinheiro caiu: `Mov_Titulo_Baixa.ID_Conta_Contabil` leva à `Cad_Conta_Bancaria` e dela vem `ID_Filial`. Cada conta contábil de banco corresponde a **uma só** conta bancária (corrente, poupança ou aplicação)? | Sim; se não, a baixa precisa apontar a conta bancária. |

## 3.15 Novos, do documento 177 (transação de cartão)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q177-E1** | O arquivo da credenciadora (EDI) e o TEF trazem as sete datas, ou só algumas? | A verificar; as que faltarem ficam vazias (opcionais). |
| **Q177-E2** | Uma autorização que paga mais de uma nota é frequente? | Se não for, o pagamento da nota vira 1:1 e a transação ganha o `ID_Nota`. |

## 3.16 Novos, do documento 159 (consulta, multas, ordem de aplicação e PNCT)

| Nº | Pergunta | Minha leitura |
|---|---|---|
| **Q159-E1** | O `Mov_Processo_Suspensao` usa o indicativo de suspensão do eSocial (`codigo_suspensao_esocial`) e por isso não serve ao IBS e à CBS. Amplia essa entidade com um segundo indicativo ou a suspensão do IBS e da CBS fica dentro das duas entidades novas? | Fica dentro das duas entidades novas, como o documento 159 propõe; muda só se a equipe preferir uma entidade única de suspensão. |

# 4. Prazos de calendário

Estas datas vêm do texto de 11/10/2026 do antigo documento 38 e **não foram reconferidas nas fontes oficiais**. As que já passaram (01/10, 13/10 e 16/10/2026) foram retiradas. Os que dependem de resposta sua ou do contador estão em negrito. Os prazos que só o contador cumpre estão no apêndice A do documento 188.

| Data | O que vence | Quem decide ou age |
|-----------------|------------------------------------------|-----------------------------------------|
| **31/10/2026** | Opção das cooperativas pelo regime específico de IBS/CBS (vale a partir de 01/01/2027), com listagem de associados assinada com certificado | Alberto (há cliente cooperativa; faltam quais e quantos associados; Q-E) |
| 01/11/2026 | Fim do compartilhamento de ME/EPP na regra E0163 da NFS-e Nacional (NT 009); o ERP aceita os dois canais por parâmetro | Alberto |
| **10/11/2026** | DES-IF, Módulo 2 de outubro (se houver cliente instituição financeira equiparada em São Paulo; Q80-5) | Alberto e contador |
| 16/11/2026 | NT 2026.004: produção das regras de IBS/CBS no CT-e, MDF-e e NFCom (conflito de datas registrado: P40-04); **NT 2026.005 v1.00 da NF-e e NFC-e (campos do Simples; documento 163)**, com o evento 412140 sem data | Equipe |
| 23/11/2026 | Limite de horas do tempo parcial (S-2200 e S-2206) | Equipe e RH |
| **até 30/11/2026** | Cancelamento da opção pelo regime regular de IBS/CBS no Simples (a CGSN pode adiar) | Alberto, se houver cliente |
| 01/12/2026 | NFAg, NFGás, NFS-e de plataformas e NF-e ABI; obrigação de NFS-e na locação (Q85-13, MEI locador: pessoa jurídica obrigada em 01/12/2026; pessoa física que abrir CNPJ para emitir, em 01/01/2027) | Alberto |
| 14/12/2026 | CT-e Simplificado reestruturado (só se houver cliente nesse modelo); códigos de incidência do salário-paternidade | Alberto e RH |
| 20/12/2026 | Receita e folha de 12/2025 a 11/2026 de quem ingressa no Simples em 01/01/2027 ou vem do MEI: conferir, alterar ou completar no módulo "Receitas Anteriores à Opção" (Resolução CGSN 190, art. 144-E; condicional a haver cliente nessa situação, P-R4-01) | Alberto e contador |
| 01/01/2027 | Simples e NF-e Importação e Combustíveis no cronograma da Receita; efeitos das Resoluções CGSN 190 e 191 | Alberto |
| 20/01/2027 | Receita e folha de 12/2026 das mesmas empresas do prazo de 20/12/2026 (Resolução CGSN 190, art. 144-E, II) | Alberto e contador |
| 01/02/2027 e 01/03/2027 | NT 2026.004: ICMS previsto no pagamento antecipado, em homologação e em produção (P40-04) | Equipe |
| Janeiro de 2028 | Início previsto do split payment (D-N282, adiado por você) | Alberto |

# 5. Limites desta lista

**Atualização de 06/11/2026 (documento 183).** Entraram a seção 1.25 (Q183-1 a Q183-10) e a seção 2.20 (Q183-C1). Nada saiu: o documento 183 não aplica nada ao dicionário. O manual chegou com a sua frase "Manual do ECD que faltava" e foi conferido (o que não li está na seção 8 do documento 183).

**Consolidação de 05/11/2026 (revisão 32, documento 178).** Saíram da seção 0 as linhas aplicadas (Q172-1 a Q172-10, Q172-C1, C4 e C6, Q167-2, Q167-5, Q176-1 a Q176-10, `COD_INS_SUBST`, Q176-C1 a C3, Q176-C6 e o C130); a linha da Q176-C4 passa a dizer só do documento 177. Saíram das seções 1.21 e 1.22 as Q175-1 a Q175-8, a Q176-11 e a Q176-12 (lidas como "Sim"); da Q175-9 fica só a tabela de cClass da NFGás. Entrou a leitura da Revisão 32 (seção 0.1) e a contagem de comandos do T-SQL passa a 18.595. As perguntas ao contador e à equipe dos documentos 172, 175 e 176 (seções 2.15, 2.17, 2.18, 3.11, 3.13 e 3.14) seguem abertas, e as dos documentos 158 e 177 também.

**Atualização de 05/11/2026 (C130).** Saiu a Q176-C7 (o Guia responde: o C130 não é apresentado na entrada). Entrou a Q176-12, uma correção minha ao documento 176 (C130 só na saída). A resposta entrou na seção 0.

**Atualização de 05/11/2026 (C176-6).** Saiu a Q176-C6: as duas formas de correção da ordem aberta são aceitas. A resposta entrou na seção 0.

**Atualização de 05/11/2026 (documento 177).** Entraram as seções 1.23 (Q177-1 a Q177-5), 2.19 (Q177-C1) e 3.15 (Q177-E1 e E2). Saiu a Q176-C4 (seção 2.18). A resposta entrou na seção 0.

**Atualização de 05/11/2026 (respostas C176-1 a C176-3).** Saíram a Q176-C1, C2 e C3 (seção 2.18). Entraram a Q176-11 (seção 1.22), a Q176-C8 (seção 2.18) e a Q176-E5 (seção 3.14). A resposta entrou na seção 0.

**Atualização de 05/11/2026 (D10).** Saiu a Q176-C5: você decidiu que o `COD_INS_SUBST` do K235, do K255 e do K275 não se preenche. A resposta entrou na seção 0.

**Atualização de 05/11/2026 (respostas ao documento 176).** Saíram a Q176-1 a Q176-10 (seção 1.22, aprovadas) e a Q175-E4 (perdeu o objeto: o C171 vai ao Bloco 1); a Q175-3 ganhou a nota da Q176-6. A resposta entrou na seção 0.

**Atualização de 05/11/2026 (documento 176).** Entraram as seções 1.22 (Q176-1 a Q176-10), 2.18 (Q176-C1 a C7) e 3.14 (Q176-E1 a E4). A Q175-3 e a Q175-E4 ganharam nota remetendo à Q176-6. A Dúvida 4 do documento 167 (origem do 1601) foi fechada pelo FAQ; a D10 (`COD_INS_SUBST` do K275) continua aberta (Q176-C5).

**Atualização de 05/11/2026 (documento 175).** Entraram as seções 1.21 (Q175-1 a Q175-9), 2.17 (Q175-C1 a C8) e 3.13 (Q175-E1 a E4). Saíram a Q172-5 a Q172-10 (seção 1.19), a Q172-C1, a C4 e a C6 (seção 2.15), a Q167-2 e a Q167-5 (seção 1.13); a Q167-6 ficou como adiada. A Q172-C3 foi reescrita com o rótulo correto. A resposta de 05/11/2026 entrou na seção 0.

**Atualização de 04/11/2026 (documento 158).** Entraram as seções 1.20 (Q158-1 a Q158-13), 2.16 (Q158-C1 a C11) e 3.12 (Q158-E1 a E4) e a nota do B3 na seção 1.5. O B5 passou a constar como incorporado à revisão 31.

**Atualização de 04/11/2026 (documentos 172 e 173, antes do "consolidar" da revisão 31).** Entraram a Q171-1 a Q171-8 (respondidas "Todas sim" e **substituídas pelo documento 173**), a Q172-1 a Q172-4 e a Q173-1 a Q173-4 na seção 0; as seções 1.18 (Q173-5 a Q173-11) e 1.19 (Q172-5 a Q172-10); as perguntas ao contador das seções 2.14 (Q173-C1 a C8) e 2.15 (Q172-C1 a C9); e as da equipe das seções 3.10 (Q173-E1 a E6) e 3.11 (Q172-E1 a E5). Saíram as perguntas Q171-1 a Q171-8, Q171-C1 a C9 (exceto a C5, que segue aberta) e Q171-E1 a E6, todas absorvidas pelo 173. Os documentos 157, 150, 170 e 173 entraram na revisão 31; o 172 aguarda a sua aprovação das Q172-5 a Q172-10. Atualização: a seção 1.18 deixou de ter pergunta aberta.

**Consolidação de 04/11/2026 (revisão 31, documento 174).** Saíram da seção 0 as linhas aplicadas (Q157-1 a Q157-14, Q150-1 a Q150-12, Q140-7, Q170-1 a Q170-10, Q171-1 a Q171-8, Q173-1 a Q173-11, Q137-6 e Q94-4); a Q161-4 passa a dizer que os documentos 156, 157 e 150 entraram; as seções 1.15 a 1.18 passam a dizer que os documentos 157, 150, 170 e 173 entraram; entrou a leitura da Revisão 31 (seção 0.1, com a confirmação do lado de quem recebe o apoio). A contagem de comandos do T-SQL passa a 18.046. As perguntas ao contador e à equipe dos documentos 157, 150, 170 e 173 (seções 2.11 a 2.14 e 3.7 a 3.10) seguem abertas.

**Consolidação de 04/11/2026 (revisão 30, documento 169).** Saíram da seção 0 as linhas aplicadas (Q164-1 a Q164-12, Q167-1 e Q167-3, Q161-1, Q161-2 e Q156-1 a Q156-15); a Q138-3, a Q138-4 e a Q161-4 ficam com a marca de aplicadas; as seções 1.8, 1.11, 1.13, 1.14 e 1.15 passam a dizer que os documentos 156, 161, 164 e 168 entraram; entrou a leitura da Revisão 30 (seção 0.1, com a confirmação da Q164-1). A contagem de comandos do T-SQL passa a 17.355.

**Consolidação de 03/11/2026 (revisão 29, documento 166).** Saíram da seção 0 as linhas aplicadas (Q137-3, Q128-5 e Q152-1, Q152-2, Q153-6 a Q153-15, Q155-1 a Q155-5, Q140-1 a Q140-4, Q138-8 a Q138-10, Q161-3, Q162-1 a Q162-4 e Q163-1 a Q163-5), a seção 1.12 virou "sem pergunta aberta" e entraram a linha da Q152-4 (carga, seção 0), a leitura da Revisão 29 (seção 0.1), a linha da carga (seção 2.2) e a planilha do leiaute 11 (seção 3.2). A contagem de comandos do T-SQL passa a 16.711.

**Consolidação de 29/10/2026 (revisão 28, documento 154).** Saíram da seção 0 as linhas aplicadas (Q103-6, Q127-2 a Q127-5, Q128-3, Q128-4, Q128-6, Q128-7, Q139-3 a Q139-5, Q144-1 a Q144-12 e Q153-1 a Q153-5); ficam as que esperam desenho ou resposta. A contagem de comandos do T-SQL passa a 16.265.

**Revisão de 29/10/2026.** Conferi item por item contra o histórico de decisões (documento 14): saíram a Q80-4 (respondida e aplicada como `Cad_Desif_Instituicao_Enquadramento`, D-N259 de 20/10/2026), a Q136-1 (resposta com resultado no documento 139), as Q138-1 e Q138-2 (substituídas e aplicadas na revisão 27) e as P-R3-01 a P-R3-03 e a Q151-1 (respondidas hoje). Corrigi o cabeçalho, o título da seção 0.1, a referência dos Anexos VI e VII da NT 007 (é a seção 3, e não a 3.2), a contagem de comandos do T-SQL (16.188) e acrescentei a lista de perguntas abertas no início da seção 1. Os itens das seções 1.6, 1.7, 2.1, 3.1 e 4 **não** foram reconferidos nas fontes: só vale o que está registrado nos documentos do Projeto.

A conferência das listas antigas foi feita **por busca de texto** nos relatórios e documentos e só vale para o que está registrado neles. Os prazos da seção 4 não foram reconferidos nas fontes oficiais.

**Consolidação de 06/11/2026 (revisão 33, documento 182).** Saiu da seção 0 a linha das Q181-1 a Q181-4 e Q180-2 (aplicadas). Entrou a leitura da Revisão 33 (seção 0.1). A contagem de comandos do T-SQL passa a 18.599 (18.595 mais 1 chave estrangeira, 1 índice e 2 comentários). Seguem abertas as Q140-5b, 5d e 5e (Receita), a Q140-6 (contador) e a Q180-3, além das dos documentos 158, 177 e 179.

**Atualização de 09/11/2026 (documento 184).** Entraram a seção 1.26 (Q184-1 a Q184-14) e a seção 2.21 (Q184-C1 a C3). Saíram as seções 1.20, 1.23 e 1.25 (respondidas "Sim" e movidas para a seção 0) e a parte aberta da Q175-9. As respostas Q183-1 a Q183-10, Q177-1 a Q177-5 e Q158-1 a Q158-13 e a tabela cClass entraram na seção 0.

**Atualização de 09/11/2026 (documento 185).** Entraram a seção 1.27 (Q185-1 a Q185-4), a seção 2.22 (Q185-C1) e a linha da IN RFB 2.316/2026 na seção 0. A Q180-3 passa a "respondida em parte" (falta o Confia).

**Atualização de 09/11/2026 (respostas da Q184).** Saiu a lista de perguntas da seção 1.26 (respondidas "Sim", movidas para a seção 0). Seguem abertas a Q184-C1 a C3 (contador, seção 2.21).

**Consolidação de 09/11/2026 (revisão 34, documento 186).** Saíram da seção 0 as linhas aplicadas (Q183-1 a Q183-10, Q177-1 a Q177-5, Q158-1 a Q158-13, a tabela de cClass da NFGás, Q184-1 a Q184-14 e a Q176-C4 e C130). As seções 1.20, 1.23, 1.25 e 1.26 passam a dizer que os documentos 158, 177, 183 e 184 entraram. Entrou a leitura da Revisão 34 (seção 0.1). A contagem de comandos do T-SQL passa a 19.134. Seguem abertas as Q185-1 a Q185-4 (seção 1.27), a Q184-C1 a C3, a Q183-C1, a Q185-C1 e as perguntas ao contador do documento 158 (seção 2.16), a Q140-5b, 5d e 5e (Receita), a Q140-6 (contador), a Q180-3 e as Q179-1 a Q179-3.

**Atualização de 09/11/2026 (documento 187).** Entrou a seção 1.28 (Q187-1 a Q187-3). As Q185-1 a Q185-3 foram aprovadas e saíram das perguntas abertas (seção 1.27); a Q185-4 foi atendida em parte (texto da LC 225 recebido, falta o ato do Confia). A Q180-3 segue com o ato do Confia. Seguem abertas a Q185-C1 (contador), a Q140-5b, 5d e 5e (Receita), a Q140-6, as Q179-1 a Q179-3 e a Q93-6.

**Atualização de 09/11/2026 (documento 188).** A seção 2 (para o contador) saiu daqui e virou o **documento 188**, com 215 perguntas detalhadas e campos de resposta; por regra de Alberto (D-N501) as perguntas e pendências do contador ficam **somente** lá. Saíram da seção 1 as linhas Q93-7, Q118-2, Q122-1, Q130-4, Q140-6a a 6e e Q179-2, e da seção 4 os prazos que só o contador cumpre. As referências às antigas seções 2.1 a 2.22 apontam agora para o documento 188. As notas de atualização anteriores a esta citam as seções 2.x como eram na data.

**Atualização de 09/11/2026 (resposta ao C1 do documento 188).** Entrou a linha dos limites da ECF na seção 0 e a seção . O C1 fica respondido por você, com a parte (3) (início da nova vigência) em aberto, e o contador confirma os valores; nada foi aplicado ao dicionário (revisão 34 mantida).

**Atualização de 09/11/2026 (Q188-1 e Q188-2 respondidas; D-N504).** Você respondeu que o limite de R$ 120.000 segue o manual (abaixo não detalhar, a partir dele detalhar) e que os "ativos" dos R$ 100.000 são os direitos de recebíveis do ativo do balanço e os bens no exterior que são contas bancárias. A seção 1.29 passa a trazer a Q188-3 e a Q188-4 (como aplico cada resposta); no documento 188 o C1 ganhou as duas respostas e o C65 (Q110-11) ficou decidido por você, com o contador só confirmando. Nada foi aplicado ao dicionário (revisão 34 mantida); a D-N504 substitui a D-N356 só quando você aprovar a Q188-3 e pedir o "consolidar".

**Atualização de 09/11/2026 (C2 do documento 188).** A lista de tipos de vinculação do art. 4º da Lei 14.596 foi para o documento 188 (C2) com o texto da lei e os achados da conferência (D-N503). Nada muda para você aqui; a validação é do contador e nada foi aplicado ao dicionário.

**Atualização de 09/11/2026 (C3 do documento 188; D-N505).** Você confirmou que o contador cadastra o participante e relaciona a vinculação (D-N312 e D-N313 seguem como estão). Nada muda para você aqui; a segunda parte do C3 (vinculação que a Receita exige informar sem operação no ano) segue com o contador, no documento 188.

**Atualização de 09/11/2026 (C4 do documento 188; D-N506).** Você respondeu que número, série e data da NFTS vindos de XML importado não podem ser alterados. Entrou a Q188-5 na seção 1.29 (vale para toda nota importada de XML, e como corrigir). A conferência final do desenho da NFTS segue com o contador, no documento 188. Nada foi aplicado ao dicionário.

**Atualização de 09/11/2026 (Q188-3 e Q188-4 respondidas; D-N507).** Você aprovou ("Sim") a aplicação do corte de R$ 120.000 do manual (substitui a D-N356) e o cálculo do `IND_ATIV_EXT` por recebíveis e contas bancárias no exterior. Saíram da seção 1.29; a linha da seção 0 segue com o texto do que entra no próximo "consolidar". Segue aberta a Q188-5 (NFTS). Nada foi aplicado ao dicionário.

**Atualização de 09/11/2026 (ECF de 2025 com Y520; D-N508).** Você enviou uma ECF de 2025 com o Y520 preenchido (9 linhas R e 5 P no mesmo arquivo, sem mensagem do validador sobre o Y520). Entrou como evidência no C5 e no C6 do documento 188; as respostas seguem com o contador. Nada muda para você aqui e nada foi aplicado ao dicionário.

**Atualização de 09/11/2026 (D-N509).** Você confirmou que a ECF de 2025 com Y520 foi validada e transmitida. No C5 do documento 188 a parte (1) fica respondida na prática; a parte (2) e a conferência de pendência da Receita seguem com o contador. Nada muda para você aqui.

**Atualização de 09/11/2026 (Q188-5 respondida; D-N510).** Você aprovou a regra para toda nota importada de XML. Saiu a seção 1.29 (sem pergunta aberta); a linha da NFTS entrou na seção 0.

**Atualização de 09/11/2026 (documento 189).** Entrou a seção 1.29 (Q189-1 a Q189-5) com a conferência das cinco normas; o documento 188 passou a ter **218 perguntas** (Parte 6, C216 a C218). Foi aprovada a Q188-5 (D-N510, trava de número, série e data de nota que entra por XML), que entra no próximo "consolidar" com a D-N504 e a D-N507.

**Atualização de 09/11/2026 (documento 190).** Entrou a seção 1.30 (Q190-1 a Q190-6); a Q189-5 foi respondida com o envio dos anexos. O documento 188 passou a ter **220 perguntas** (Parte 6, C216 a C220). A Q187-3 (ato do Confia) ganhou uma pista: a Portaria RFB 703/2026 cita a IN RFB 2.295/2025 (Q190-6).

**Atualização de 09/11/2026 (documento 191).** Suas respostas aos documentos 189 e 190 saíram das seções 1.29 e 1.30 e estão na seção 0; entrou a seção 1.29 com a Q191-1 a Q191-8. O documento 188 passou a ter **222 perguntas** (Parte 6, C216 a C222). A Q187-3 está fechada (a IN RFB 2.295/2025 é o ato do Confia) e a Q187-1 foi corrigida.

**Atualização de 09/11/2026 (respostas ao documento 191, D-N515).** As Q191-1 a Q191-8 foram respondidas e saíram da seção 1 (estão na seção 0). Não há pergunta nova sua em aberto por causa dos documentos 189 a 191; seguem abertas as do contador no documento 188 (222 perguntas).

**Atualização de 09/11/2026 (respostas às Q187-1 e Q187-2 e pergunta sobre a Q179-3, D-N516).** As Q187-1 e Q187-2 foram aprovadas ("sim para as duas") e saíram da seção 1 (a seção 1.28 foi removida; estão na seção 0). Você perguntou quais tabelas faltam na Q179-3: a linha da seção 1.24 passa a listar as **duas planilhas** (leiautes 12 e 11) e o que cada uma completa; a Q152-4 aponta para ela. Seguem abertas as Q179-1 e Q179-3, a Q93-6 e os itens avulsos; as do contador estão no documento 188 (222 perguntas).

**Atualização de 09/11/2026 (documento 192, D-N517).** Entrou a seção 1.28 (Q192-1 a Q192-7) com o desenho do registro 0000 da ECF a partir do Manual da ECF leiaute 12, que você enviou sem mensagem. O manual **não fecha a Q179-3** (não traz o texto das fórmulas), mas a linha da seção 1.24 passa a trazer o endereço da planilha do leiaute 12. O documento 188 passou a ter **224 perguntas** (Parte 6, C216 a C224).

**Atualização de 09/11/2026 (documento 193, D-N518).** Entrou a seção 1.29 (Q193-1 a Q193-3). A planilha do leiaute 12 que você enviou sem mensagem **fechou a parte (1) da Q179-3**: a pergunta 10 do documento 179 deixa de ser rascunho; falta só a planilha do leiaute 11 (parte 2). As perguntas do contador seguem no documento 188 (224 perguntas; nenhuma nova).

**Atualização de 09/11/2026 (respostas aos documentos 192 e 193, D-N519).** As Q192-1 a Q192-7 ("seguir com as recomendações") e as Q193-1 a Q193-3 ("sim") foram aprovadas e saíram da seção 1 (as seções 1.28 e 1.29 foram removidas; estão na seção 0). O documento 192 entra no próximo "consolidar" (1.137 entidades e 12.759 campos com os documentos 189 a 192). O conjunto da Q179-1 passa a ter 28 perguntas. Segue aberta só a parte (2) da Q179-3 (planilha do leiaute 11), além da Q179-1, da Q93-6 e dos itens avulsos; as do contador estão no documento 188 (224 perguntas).

**Atualização de 09/11/2026 (documento 194, D-N520).** Entrou a seção 1.28 (Q194-1 a Q194-4) com a conferência da Portaria MF 3.074 e da Portaria Conjunta MF/CGIBS 14, que você enviou sem mensagem junto com as Portarias CGIBS nº 1 a 12. A Q170-9 está atendida. O documento 188 passou a ter **225 perguntas** (C225 nova; C161, C165, C166 e C168 com o texto novo).

**Atualização de 09/11/2026 (resposta da Receita à pergunta 29, D-N521).** Você enviou a pergunta 29 e colou a resposta (seção 0). A Q194-2 está cumprida e saiu da seção 1.28; entrou a Q194-5 (leitura minha da resposta, sem campo novo). Seguem abertas as Q194-1, Q194-3, Q194-4 e Q194-5. O documento 188 continua com 225 perguntas; a C163 e a C166 receberam a resposta como evidência.

**Consolidação de 09/11/2026 (revisão 35, documento 195).** Saíram da seção 0 as linhas aplicadas (Q185-1 a Q185-3 e a LC 225, os limites da ECF, a NFTS e as notas por XML, Q187-1 e Q187-2, Q189-1 a Q190-5, Q191-1 a Q191-8 e Q192-1 a Q192-7). Ficam na seção 0 a pergunta 29 à Receita, as Q193-1 a Q193-3 (sem campo), o Q93-6 e as linhas antigas. Nada de novo para você responder por causa da consolidação; seguem abertas as Q179-1, Q179-3, Q194-1, Q194-3 a Q194-5 e Q93-6, e as do contador no documento 188.

**Atualização de 09/11/2026 (respostas ao documento 194, D-N523).** As Q194-1, Q194-3, Q194-4 e Q194-5 foram aprovadas ("Sim") e saíram da seção 1 (a seção 1.28 foi removida; estão na seção 0). Não há pergunta aberta sua por causa dos documentos 189 a 194. Seguem abertas as Q179-1, Q179-3 e Q93-6, e as do contador no documento 188 (225 perguntas).

**Atualização de 10/11/2026 (respostas aos documentos 159 e 196, D-N525 e D-N526).** As Q159-1 a Q159-3 e Q159-5 a Q159-9 ("Sim") e as Q196-1 a Q196-11 ("Seguir com as recomendações") foram aprovadas e saíram da seção 1 (as seções 1.28 e 1.29 foram removidas; estão na seção 0). Q159-4, Q159-10 e Q159-11 fecharam pelas Q196-1 a Q196-11. Não há pergunta aberta sua por causa dos documentos 159 e 196. Seguem abertas: o texto oficial da MP 1.399/2026 (seção 3.2), a Q159-E1 (seção 3.16), as Q179-1 e Q179-3 (parte 2), a Q93-6 e as perguntas do contador C226 a C232 (documento 188, Parte 7).

**Consolidação de 10/11/2026 (revisão 36, documento 197).** Saíram da seção 0 as linhas aplicadas (a pergunta 29 à Receita, as Q194-1, Q194-3, Q194-4 e Q194-5, as Q159-1 a Q159-3 e Q159-5 a Q159-9 e as Q196-1 a Q196-11). Ficam na seção 0 as Q193-1 a Q193-3 (sem campo), o Q93-6 e as linhas antigas. Nada de novo para você responder por causa da consolidação; seguem abertas: o texto oficial da MP 1.399/2026 (seção 3.2, Q196-10), a Q159-E1 (seção 3.16), as Q179-1 e Q179-3 (parte 2), a Q93-6 e as perguntas do contador C226 a C232 (documento 188, Parte 7).

**Atualização de 10/11/2026 (documento 160, D-N528).** O documento 160, o último da fila 156, 157, 150, 158, 159 e 160, foi entregue: o inventário dos parâmetros das outras obrigações, 59 linhas novas do catálogo central (nenhuma entidade e nenhum campo novo), 6 linhas novas de `Cad_Obrigacao_Acessoria` e o desenho da linha `atividade_rural` (Q93-6). Entrou a seção 1.28 (Q160-1 a Q160-9, com recomendação); a linha da Q93-6 da seção 0 aponta para a Q160-5. Nada foi aplicado; entra na revisão 37 com as suas respostas e o "consolidar". Para o contador, nada novo (C99). Seguem abertas: o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2), as Q160-1 a Q160-9 e as perguntas do contador C226 a C232 (documento 188, Parte 7).

**Atualização de 10/11/2026 (documento 198, D-N529).** O B4 foi desenhado: regimes específicos de serviços financeiros, seguro e plano de saúde, com 11 entidades novas (157 campos contando os 2 de entidades existentes), 2 domínios, 92 componentes legais da base e as regras de aferição, saldo, individualização e alíquota. Entrou a seção 1.29 (Q198-1 a Q198-12, com recomendação) e a nota do B4 na seção 1.5. Ao contador, seis perguntas novas (C233 a C238, documento 188, Parte 8, que passa a ter 238 perguntas; a contagem da seção 2 estava em 229 e foi corrigida). Nada foi aplicado; entra na revisão 37 ou na seguinte com as suas respostas e o "consolidar". Seguem abertas: o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2), as Q160-1 a Q160-9, as Q198-1 a Q198-12 (a Q198-12 pede o manual oficial da DeRE) e as perguntas do contador C226 a C238 (documento 188, Partes 7 e 8).

**Atualização de 10/11/2026 (respostas ao documento 198, D-N530).** "Seguir recomendacoes das Q198-1 a Q198-12": o B4 foi aprovado inteiro e a seção 1.29 saiu (as respostas estão na seção 0). Mantida a D-N273: o redutor e a Estimativa não mudam, e o redutor só entra na aferição depois da C233. Entra no próximo "consolidar" (1.155 entidades e 13.017 campos). Seguem abertas para você: o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2), as Q160-1 a Q160-9 e o Q93-6; ao contador, C226 a C238 (documento 188, Partes 7 e 8).

**Atualização de 10/11/2026 (respostas ao documento 160, D-N531).** "Q160-1 a Q160-7 - sim": o documento 160 foi aprovado nessas sete perguntas e elas saíram da seção 1.28 (estão na seção 0); a Q93-6 ficou fechada pela Q160-5. Entra no próximo "consolidar" junto do documento 198 (1.155 entidades e 13.017 campos, mais 59 linhas de catálogo, 6 de obrigação, 1 valor de enumeração e 1 texto de campo). Seguem abertas para você: a Q160-8 e a Q160-9 (recomendação "não", sem efeito no dicionário), o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1 e as Q179-1 e Q179-3 (parte 2); ao contador, C226 a C238 (documento 188, Partes 7 e 8).

**Consolidação de 10/11/2026 (revisão 37, documento 199).** Saíram da seção 0 as linhas aplicadas (as Q198-1 a Q198-12, as Q160-1 a Q160-7, a Q93-6 e a ordem de desenho 156 a 160, que ficou completa). Ficam na seção 0 as Q193-1 a Q193-3 (sem campo) e as linhas antigas. Nada de novo para você responder por causa da consolidação; seguem abertas: o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1 (seção 3.16), as Q179-1 e Q179-3 (parte 2), as Q160-8 e Q160-9 (sem efeito no dicionário) e, ao contador, C226 a C238 (documento 188, Partes 7 e 8).

**Atualização de 10/11/2026 (documento 200, D-N533).** O B0b-2 foi desenhado: o crédito de IBS e de CBS de quem compra o serviço financeiro, o arrendamento, a antecipação de recebíveis e o plano de saúde dos empregados, com 8 entidades novas (152 campos contando os 5 de entidades existentes), nenhum domínio novo, 28 regras provisórias e os avisos do Motor. Entrou a seção 1.30 (Q200-1 a Q200-11, com recomendação) e a nota do B0b-2 na seção 1.5. Ao contador, sete perguntas novas (C239 a C245, documento 188, Parte 9, que passa a ter 245). Nada foi aplicado; entra no próximo "consolidar" (1.163 entidades e 13.169 campos, se aprovado). Seguem abertas para você: as Q200-1 a Q200-11, o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C245 (documento 188, Partes 7 a 9).

**Atualização de 10/11/2026 (respostas ao documento 200, D-N534).** "Seguir com as recomendações Q200-1 a Q200-11": o B0b-2 foi aprovado inteiro e a seção 1.30 do documento 200 saiu (as respostas estão na seção 0). Você também pediu que os parâmetros tenham documentação do efeito e da obrigação em que atuam; vira o documento 201. Entra no próximo "consolidar" (1.163 entidades e 13.169 campos). Seguem abertas para você: o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C245 (documento 188, Partes 7 a 9).

**Atualização de 10/11/2026 (documento 201, D-N535).** Você pediu a documentação dos parâmetros do B0b-2 (efeito e obrigação). Entrou a seção 1.31 (Q201-1 a Q201-10, com recomendação) e a nota do B0b-2 na seção 1.5. Ao contador, duas perguntas novas (C246 e C247, documento 188, Parte 10, que passa a ter 247). Nada foi aplicado; entra no próximo "consolidar" junto do documento 200 (1.165 entidades e 13.204 campos, se aprovado). Seguem abertas para você: as Q201-1 a Q201-10, o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C247 (documento 188, Partes 7 a 10).

**Atualização de 10/11/2026 (respostas ao documento 201, D-N536).** "Q201-1 a Q201-10, sim para todos": o documento 201 foi aprovado inteiro e a seção 1.31 saiu (as respostas estão na seção 0). Entra no próximo "consolidar" junto do documento 200 (1.165 entidades e 13.204 campos). Seguem abertas para você: o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C247 (documento 188, Partes 7 a 10).

**Atualização de 10/11/2026 (documento 202, D-N537).** Você pediu o próximo passo e escolheu o B6 (regime automotivo). Entrou a seção 1.31 (Q202-1 a Q202-11, com recomendação) e a nota do B6 na seção 1.5. Ao contador, oito perguntas novas (C248 a C255, documento 188, Parte 11, que passa a ter 255). Nada foi aplicado; entra no próximo "consolidar" junto dos documentos 200 e 201 (1.173 entidades e 13.336 campos, se aprovado). Seguem abertas para você: as Q202-1 a Q202-11, o envio do manual oficial da DeRE e do ato do fator de redução (seção 3.2, Q198-12), o texto oficial da MP 1.399/2026 (Q196-10), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C255 (documento 188, Partes 7 a 11).

**Consolidação de 10/11/2026 (revisão 38, documento 203).** Saíram da seção 0 as linhas aplicadas (as Q200-1 a Q200-11 e as Q201-1 a Q201-10). O documento 202 segue na seção 1.31, com a observação de Alberto (D-N539). O documento 188 não mudou (C1 a C255).

**Atualização de 10/11/2026 (documento 204, D-N540).** Você enviou, sem mensagem, a MP 1.399/2026 e os Decretos 12.435 e 12.549 com a Lei 14.902; conferi os textos e desenhei a tributação do veículo por combustível, potência e demais critérios. Entrou a seção 1.32 (Q204-1 a Q204-11, com recomendação) e a Parte 12 do documento 188 (C256 a C265, que passa a ter 265 perguntas). A Q196-10 está cumprida quanto ao texto da MP (o ato do art. 414, § 2º, segue pendente). Nada foi aplicado; entra no próximo "consolidar" se você aprovar. Seguem abertas para você: as Q202-1 a Q202-11 e as Q204-1 a Q204-11, o manual oficial da DeRE e o ato do fator de redução (seção 3.2, Q198-12), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C265 (documento 188, Partes 7 a 12).

**Atualização de 10/11/2026 (respostas ao documento 202, D-N541).** "Q202-1 a Q202-11 - Seguir com as Recomendações": o documento 202 (B6) foi aprovado inteiro e a seção 1.31 saiu (as respostas estão na seção 0). Entra no próximo "consolidar" (1.173 entidades e 13.336 campos sobre a revisão 38; 1.179 e 13.463 com o documento 204 aprovado). Você enviou também o Decreto 4.186/2002 e o Decreto 8.168/2013: **os dois estão revogados** e trazem textos antigos das Notas Complementares da Tipi (88-1, 88-2, 88-3, 87-2, 87-4, 87-5 e 87-7); entraram como evidência na C263 e a Q204-11 pede o texto atual e a NC 89-1. Seguem abertas para você: as Q204-1 a Q204-11, o manual oficial da DeRE e o ato do fator de redução (seção 3.2, Q198-12), a Q159-E1, as Q179-1 e Q179-3 (parte 2) e as Q160-8 e Q160-9; ao contador, C226 a C265 (documento 188, Partes 7 a 12).

**Atualização de 10/11/2026 (documento 205, D-N542).** Você enviou, sem mensagem, oito normas (Leis 9.440 e 9.826, Decretos 10.457, 7.422 e 9.557, Tipi, LC 214 compilada e o quadro dos decretos de 2010). Li o que interessa ao automotivo e conferi o 202 e o 204: **ambos se mantêm**; o 205 traz uma correção (NC 87-2 e NC 89-1), dois campos para o 204 e três campos, um valor e dois avisos para o 202. **A Tipi enviada não incorpora o Decreto 12.549** no capítulo 87; a `Al` da Lei 9.826 deve vir da tabela do Decreto 12.549 com as notas (C266). O Decreto 12.955, art. 518, § 5º, mantém válidos os Decretos 10.457 e 7.422. A Q204-11 está respondida; ficam abertas para você as Q204-1 a Q204-10, a Q198-12, a Q159-E1, as Q179-1 e Q179-3 (parte 2), as Q160-8 e Q160-9; ao contador, C226 a C268 (documento 188, Partes 7 a 13).

**Atualização de 10/11/2026 (leitura do Anexo XVII, D-N543).** Você pediu a leitura do Anexo XVII da LC 214. As posições dos veículos, aeronaves e embarcações **conferem** com o documento 204, e as 25 linhas do Anexo XVII da carga da revisão 26 (`Cad_Lista_Legal_Item`, tipo `imposto_seletivo`) **batem sem diferença** com o texto. Respondidas em parte: a C259 (a lista legal alcança a posição 87.03 inteira e, em 8704, só seis códigos, exceto caminhões) e a C263 ganhou uma pergunta (a ressalva do uso operacional é por característica técnica, e a NC 88-3 não está na lei nem no art. 6º da MP). O documento 205 foi reemitido com a seção 4.4. Nenhum campo novo.

**Atualização de 10/11/2026 (respostas às Q205-1 a Q205-4, D-N544).** Você aprovou as quatro recomendações: a correção do 204 (NC 87-2 e NC 89-1), o ajuste B1 (24 campos em `Mov_Is_Veiculo_Apuracao`), o ajuste A1 (17 campos em `Mov_Habilitacao_Automotiva_Compromisso` e 22 avisos) e a preparação da tabela da alíquota de IPI de 31/12/2025 (8702 a 8704). Nada foi aplicado ao dicionário. Fica com você o envio da Tipi consolidada com o Decreto 12.549. Abertas para você: Q204-1 a Q204-10, Q198-12, Q159-E1, Q179-1, Q179-3 (parte 2), Q160-8 e Q160-9; ao contador, C226 a C268.

**Atualização de 10/11/2026 (documento 206, D-N545).** Você escolheu o programa inteiro do Rota 2030 e do Mover. O documento 206 propõe 18 entidades novas em quatro grupos e 4 obrigações novas; o **Rota 2030 acabou** (habilitação até 30/11/2023, atos de registro revogados em 01/06/2025), e a multa das autopeças é 30% na lei e 100% no Decreto 9.557 (o desenho usa 30%). Ficam abertas para você: Q206-1 a Q206-12 (seção 1.34), Q204-1 a Q204-10, Q198-12, Q159-E1, Q179-1, Q179-3 (parte 2), Q160-8 e Q160-9; ao contador, C226 a C277 (documento 188, Partes 7 a 14). Nada foi aplicado.

**Consolidação de 10/11/2026 (revisão 39, documento 208).** Saiu da seção 0 a linha do documento 202 (Q202-1 a Q202-11) e a Q205-3 passou a aplicada; entrou na seção 0 a linha das Q205-1 e Q205-2, que esperam o documento 204. O documento 188 não mudou (C1 a C277). O documento 207 está reservado para a tabela de IPI de 31/12/2025 (Q205-4), que depende da Tipi consolidada que você enviará.
