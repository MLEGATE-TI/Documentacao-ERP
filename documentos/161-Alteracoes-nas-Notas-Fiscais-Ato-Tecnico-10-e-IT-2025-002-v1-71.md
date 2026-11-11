# Alterações nas notas fiscais: Ato Técnico Conjunto nº 10/2026 e IT 2025.002 v1.71 — Documento 161

> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 28** (995 entidades, 10.844 campos). Este documento compara o que o **Ato Técnico Conjunto RFB/SUFIS/CGIBS/Diretoria-Executiva nº 10, de 28/10/2026** (DOU de 29/10/2026) e o **Informe Técnico 2025.002 v1.71** (outubro de 2026) trazem com o que o dicionário já guarda. Só entra na revisão 29 depois das suas respostas e do "consolidar".

*Fontes lidas por inteiro: o Ato nº 10 (2 páginas) e o IT 2025.002 v1.71 (13 páginas), enviados por você. Fonte secundária, só para o resumo das notas técnicas (as notas em si **não foram enviadas**): o artigo do portal reformatributaria.com sobre as cinco notas técnicas e a publicação da Inventti sobre a NT 2025.002 v1.53. Dicionário conferido pelo DDL e pelos comentários da revisão 28 e pelo documento 34 (Project).*

Mlegate · Alberto Beyeler · 3 de novembro de 2026

# 1. Resumo

- **O Ato nº 10 aprova dez conjuntos de documentação (incisos I a X).** Entra em vigor e produz efeitos na publicação no DOU (29/10/2026, edição 205-C) e no sítio do CGIBS. Para a **NF-e e a NFC-e**: NT 2025.002 **v1.53** (a do documento 34 era a v1.52), NT 2026.005 **v1.00** (Simples Nacional, **nova** para o projeto), NT 2026.006 **v1.01** (vinculação ao pagamento), NT 2026.007 **v1.11** (contribuinte exclusivo do IBS/CBS) e NT 2026.008 **v1.01** (valor líquido). Para **CT-e, CT-e OS, NFCom, BP-e, NF3e, NFAg e NFGas**: NT 2026.004 **v1.01** e, para CT-e, CT-e OS, NFCom e BP-e, também a NT 2026.005 (Simples). Para a **NF-e ABI** (modelo 77): NT 2026.001 v1.00, IT 2026.003 v1.00 e Tabela de Códigos v1.01. E o **IT 2025.002 v1.71** com a tabela cClassTrib v1.71.
- **O IT 2025.002 v1.71 mexe pouco**: atualização de textos e **ativação do indicador de uso na DIR** (Declaração de Importação de Remessas) para os cClassTrib 410003 e 410999. A versão anterior (v1.70) trouxe os códigos novos 000006, 200055, 200056, 400003, 400004 e 550026 a 550029, mais as colunas novas da tabela de crédito presumido.
- **O dicionário já cobre a maior parte da estrutura**: as colunas da tabela de crédito presumido (`indDecPag`, `indNFe`, `indNFCe`, `indCTe`, `indNFSe`, `pRedTransicaoIBS`), os indicadores do cClassTrib, o vínculo com o pagamento (grupo `gPgtoVinc` e evento 110300), o valor líquido do item e a nota do contribuinte exclusivo do IBS/CBS. O que a NT 2025.002 v1.53 muda (referência de devolução no cabeçalho ou no item) **cabe nas duas entidades de referência que já existem**.
- **Achei 4 pontos de ajuste do dicionário** (seção 3) e **3 conjuntos de notas técnicas que eu preciso ler** para dizer se há campo novo (seção 4). **Contagem proposta: +2 campos (N2 e N4) e 2 correções de texto (N1 e N3); o resto é carga de tabela oficial e conferência.**

# 2. O que cada documento do Ato traz (e o que li)

| Documento | Versão | O que sei | Fonte |
|---|---|---|---|
| NT 2025.002 (NF-e e NFC-e, RTC) | **1.53** | A finalidade de **devolução** volta a aceitar a referência à nota original **no cabeçalho ou no item**; o cabeçalho fica limitado a **uma** ocorrência (regra de validação **B25-40**) | Artigo secundário; a NT **não foi lida** |
| NT 2026.005 (Simples Nacional) | 1.00 (**nova**) | Viabiliza a apuração assistida do Simples na reforma: campos de **regime**, **atividade por item** e **valores de IBS e CBS**; cria um **evento fiscal automático de conformidade** (número não informado no artigo) | Artigo secundário; a NT **não foi lida** |
| NT 2026.006 (vinculação à transação de pagamento) | 1.01 | Grupo `gPgtoVinc` para pagamentos gerados antes da nota; **evento 110300** para vínculo depois da autorização | Artigo secundário; o dicionário usou a v1.00 |
| NT 2026.007 (contribuinte exclusivo do IBS/CBS) | 1.11 | NF-e 55 sem inscrição estadual, autorizada na SVRS; **validação cadastral na LCC-RFB** (lista centralizada de contribuintes) passa a ser obrigatória | Artigo secundário; o dicionário usou a v1.10 |
| NT 2026.008 (valor líquido) | 1.01 | Valor líquido unitário e total do item; grupo do **ICMS previsto em pagamento antecipado** | Artigo secundário; o dicionário usou a v1.00 |
| NT 2026.004 (RTC) | 1.01 | CT-e, CT-e OS, NFCom, **BP-e, NF3e, NFAg e NFGas** | Só o Ato (título e versão); o dicionário usou a v1.00 para CT-e e NFCom |
| NF-e ABI | NT 2026.001 v1.00; IT 2026.003 v1.00; Tabela de Códigos v1.01 | Documento 62 partiu da visão geral (MOC v1.00a) | Só o Ato |
| IT 2025.002 | **1.71** | Seção 7.10 e as seções 2 a 5 (lidas) | Lido por inteiro |

# 3. Pontos de ajuste do dicionário (do que li por inteiro)

| Nº | O que o IT diz | O que o dicionário tem | Proposta |
|---|---|---|---|
| **N1** | **v1.60:** o indicador `ind_gMonoDif` foi **excluído** da tabela cClassTrib | `Cad_Cclasstrib.Indicador_Mono_Dif` (revisão 7, D-N146 e D-N147) | **Não apagar** (histórico). Marcar a descrição "excluído na IT v1.60; sem uso a partir da carga v1.60" e a carga não preenche. **Sem campo novo**, só texto |
| **N2** | **v1.60:** criado o indicador **`ind_gpBioDiferenca`** (grupo da diferença do biocombustível) | Procurei no DDL e nos comentários da revisão 28: **não há campo** | **+1 campo** em `Cad_Cclasstrib`: `Indicador_Grupo_Biocombustivel_Diferenca` (booleano). A regra de preenchimento do grupo na NF-e depende da NT 2025.002 (que não li); fica como marca da classificação, como as demais |
| **N3** | **v1.60 e v1.70:** criados os indicadores de **modelo** `indDIR` e `indDERE` (e `indDUIMP`, já existente), com ativações e desativações por código (v1.70: ativa DIR em 410037; v1.71: ativa DIR em 410003 e 410999; desativa DIR em 200012 e 200033; desativa DERE em 410034; desativa DUIMP em 550021) | `Cad_Cclasstrib_Modelo` guarda **um par (cClassTrib, modelo de documento) com `Permitido`**, o que comporta os três indicadores **se** os modelos `dir`, `dere` e `duimp` existirem no domínio de modelos. O DDL não mostra os valores do domínio | **Conferir** na carga se o domínio de modelo tem `dir` e `dere`; se não tem, **só valor de carga novo** (sem campo). As ativações da v1.71 entram na carga da tabela, com vigência |
| **N4** | A coluna **ANEXO** da tabela cClassTrib passou a usar o **"anexo técnico"** `ZXXXY`: `XXX` é o número do artigo, `Y` o sequencial; **Z = 9** é artigo da LC 214 e **Z = 8** é artigo do regulamento do IBS ou da CBS; a v1.70 incluiu anexo para 200002, 550008 a 550013, 550015 e 550018 | `Cad_Cclasstrib` não tem o campo; `Cad_Lista_Legal_Item` (listas por NCM e NBS) guarda `Fundamento_Legal` em texto, sem o código | **+1 campo** em `Cad_Cclasstrib` (versão): `Codigo_Anexo_Tecnico` (texto de 5 posições, opcional), ; a lista legal correspondente (`Cad_Lista_Legal_Item`) seria achada por esse código na **carga**, sem chave nova. **Recomendação: sim**, porque é o elo oficial entre a classificação e a lista de NCM/NBS que o Motor de Regras usa |

*Contagem desta seção: **+2 campos** (N2 e N4), 2 correções de texto (N1 e N3) e a carga. Se você preferir deixar o anexo técnico só na carga, sem campo, o total cai para +1 (Q161-2).*

**Já cobertos (conferido no DDL e nos comentários da revisão 28; nenhuma mudança):**

- `Cad_Credito_Presumido_Ibs_Cbs`: `Indicador_Declaracao_Pagamento` (`indDecPag`), `Indicador_Uso_Nfe`, `_Nfce`, `_Cte` e `_Nfse`, `Percentual_Reducao_Transicao_Ibs`, `ID_Cclasstrib_Nota_Referenciada` e as datas de vigência da CBS e do IBS. A desativação de "Apropria via NF?" para os códigos 01 e 03 (v1.70) é **carga**.
- `Cad_Cclasstrib`: `Tipo_Receita_Bruta_Sn` (`tpRBSN`), `Tipo_Doacao` (`tpDoacao`, destacado na v1.70), `Indicador_Duimp` e `Indicador_Estorno_Credito`.
- Vínculo com o pagamento: `Mov_Dfe_Vinculo_Pagamento` (`gPgtoVinc`, evento 110300).
- Valor líquido do item: P-14 do documento 34. Contribuinte exclusivo do IBS/CBS: P-17 do documento 34.
- **Alíquotas padrão** (IT, seção 5): **2026** IBS-UF 0,1%, IBS-município 0% e CBS 0,9%; **2027 e 2028** IBS-UF 0,05% e IBS-município 0,05%, **CBS "aguardar legislação"**; **2029 em diante** tudo "aguardar legislação". É a carga de `Cad_Aliquota` com vigência. **Não conferi** a carga atual contra essa tabela.

# 4. O que eu preciso ler para fechar (não foi enviado)

| Item | Por que importa | O que muda se houver campo novo |
|---|---|---|
| **NT 2026.005 v1.00 (Simples Nacional)** | É a única **nova**. O dicionário tem o regime híbrido/unificado do Simples (documentos 33, 36 e 41), os campos `tpRBSN`/`gTribSN` e `ibs_cbs_simples_nacional` (`Mov_Apuracao_Tributo_Item_Complemento`), mas isso veio da NFS-e Nacional. Os campos de **regime**, **atividade por item** e **valores de IBS/CBS** na **NF-e**, e o **evento automático de conformidade**, não aparecem no dicionário | Possível evento novo em `Mov_Dfe_Evento` e campos no item da nota. O Simples entra a partir de **01/01/2027** (cronograma, documento 14) |
| **NT 2026.004 v1.01 (CT-e, NFCom, BP-e, NF3e, NFAg, NFGas)** | O documento 60 deixou **BP-e, NF3e e NFGas** para quando essa NT chegasse; a NFAg e a NFCom ficaram só na **entrada** (D-N141); o BP-e aéreo tem marco em 01/12/2026 | Desenho de entrada do BP-e e da NF3e (que você ainda não pediu) |
| **NT 2025.002 v1.53 (NF-e)** | Só sei o que o artigo resume. A **estrutura de referência cabe** em `Mov_Nota_Fiscal_Saida_Referenciada` (cabeçalho) e `Mov_Nota_Fiscal_Saida_Item_Referencia` (item), então a mudança é **regra de validação** (no máximo uma referência no cabeçalho, B25-40) | Texto de regra; sem campo |
| **NT 2026.006 v1.01, 2026.007 v1.11 e 2026.008 v1.01** | Versões novas das três que o documento 34 já usa (v1.00, v1.10 e v1.00). Pode haver regra ou campo | Conferência contra o P-13, P-14 e P-17 |
| **NF-e ABI: NT 2026.001 v1.00, IT 2026.003 e Tabela de Códigos v1.01** | O documento 62 partiu da visão geral (MOC v1.00a) e a decisão D-N51 foi "só o framework" | Conteúdo da nota fica para depois, como você já decidiu |

# 5. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Revisão 28 (real) | 995 | 10.844 |
| N2 (`Indicador_Grupo_Biocombustivel_Diferenca`) | 0 | +1 |
| N4 (`Codigo_Anexo_Tecnico`), se aprovado | 0 | +1 |
| N1 e N3 | 0 | 0 (texto e carga) |
| **Total deste documento** | **0** | **+2** |

*A revisão 29 prevista no documento 38 (1.004 entidades e 10.988 campos) **não inclui** estes 2 campos; some na consolidação.*

# 6. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| **Q161-1** | Cria o campo `Indicador_Grupo_Biocombustivel_Diferenca` em `Cad_Cclasstrib` (N2) e marca o `Indicador_Mono_Dif` como excluído pela IT v1.60, sem apagar (N1)? | **Sim** |
| **Q161-2** | Cria `Codigo_Anexo_Tecnico` em `Cad_Cclasstrib` (N4), para ligar a classificação à lista de NCM/NBS do anexo? | **Sim** |
| **Q161-3** | Você envia a **NT 2026.005 v1.00** (Simples Nacional) e a **NT 2026.004 v1.01** (CT-e, NFCom, BP-e, NF3e, NFAg e NFGas) para eu desenhar o que faltar? As demais notas (2025.002 v1.53, 2026.006 v1.01, 2026.007 v1.11, 2026.008 v1.01) eu só conferiria contra o que já está desenhado | **Sim**, começando pela 2026.005 |
| **Q161-4** | Você reenvia as fontes que perdi quando o ambiente de trabalho foi reiniciado (a LC 214 sumarizada, o texto do Decreto 12.955 e o PDF da LC 227/2026), para eu refazer os desenhos dos documentos 150 (B5) e 156 (arts. 5º, 57 e 12) e fazer os 157 (B0a), 158 (B3), 159 (43 artigos da LC 227 sem desenho) e 160 (parâmetros das outras obrigações)? | **Sim**; sem as fontes eu não refaço de memória |

# 7. Para o contador

| Id | Pergunta | Tratamento provisório |
|---|---|---|
| **Q161-C1** | Validar a carga de `Cad_Aliquota` contra a tabela de alíquotas padrão da IT v1.71 (2026: 0,1% e 0,9%; 2027 e 2028: IBS 0,05% mais 0,05%, CBS a definir) | Carga provisória; a CBS de 2027 e 2028 entra **vazia** até a legislação |

# 8. Limites

- **Não li nenhuma das notas técnicas**, só o Ato e o IT v1.71. O que escrevi sobre elas vem de dois textos de terceiros (artigo do portal reformatributaria.com e publicação da Inventti), que **não trazem** números de campo, de regra (salvo B25-40) nem de evento (salvo 110300), e nem as datas de vigência.
- A comparação com o dicionário usa o DDL e os comentários da **revisão 28**; não reabri o modelo completo (o ambiente de trabalho foi reiniciado e perdi o arquivo do modelo; recuperei o DDL da sua pasta).
- Os **valores de domínio** (por exemplo, se `dir` e `dere` existem entre os modelos de documento) não aparecem no DDL: ficam como conferência (N3).
- O prazo de homologação e produção da v1.71 (até 30/10/2026) é o da tabela de controle de versões do IT. O **03/11/2026** (schema PL_010f obrigatório em produção) vem do documento 34 e é só lembrete.
- Nada disto foi validado pelo contador.
