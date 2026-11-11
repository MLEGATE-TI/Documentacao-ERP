# Consolidação da Revisão 26 — Documento 145

*Relatório do que entrou no dicionário com o seu "consolidar" de 28/10/2026, do que ficou de fora e de como conferi. A revisão 26 aplica o **B1 completo** que você escolheu: a Duimp no leiaute da Nota 77 (documento 142), a leitura pela API do Portal Único, o Pagamento Centralizado e o ICMS da importação, o catálogo de produtos e operadores (documento 143), as despesas da nota, o aluguel recebido e a locação de pessoa física (documento 144); mais o **B2** (documento 116, qualificação do participante perante a CBS), as regras de texto já respondidas (Q134 e Q135) e as cargas. Entram **54 entidades novas, 14 campos novos em 5 entidades existentes e o texto de 11 campos em 8 entidades**. O dicionário passa de 932 entidades e 10.130 campos para **986 entidades e 10.714 campos**.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

| | Revisão 25 | Revisão 26 | Diferença |
|---|---:|---:|---:|
| Entidades | 932 | 986 | **+54** |
| Campos | 10.130 | 10.714 | **+584** |
| Campos de referência (FK) | 2.724 | 2.832 | **+108** |
| Referências genéricas | 51 | 53 | **+2** (`Mov_Duimp_Despesa_Rateio.ID_Origem` e `Mov_Duimp_Importacao_Ocorrencia.ID_Registro_Destino`) |
| Valores de `Cad_Classe_Sistema.Dominio` | 276 | 291 | **+15** domínios novos, todos abertos |
| Entidades mestres (identidade e versão) | 186 | 192 | **+6** |
| Tabelas, chaves estrangeiras, índices e comentários no DDL | 1.118 / 2.910 / 2.985 / 8.179 | 1.178 / 3.024 / 3.099 / 8.762 | +60 / +114 / +114 / +583 |
| Comandos T-SQL lidos pelo analisador (sqlglot) | 15.193 | 16.064 | +871 |
| Linhas da carga das tabelas dinâmicas da ECF | 4.486 | 4.488 | +2 (P200 26 e P400 21 divididas, Q135-1) |
| Carga da lista legal (`Cad_Lista_Legal_Item`) | 0 | 708 | +708 (provisória) |

Dos 584 campos novos, 570 estão nas 54 entidades novas (550 no B1, 53 entidades, e 20 no B2) e 14 em cinco entidades que já existiam. Aritmética conferida: 932 + 54 = 986 entidades, 10.130 + 584 = 10.714 campos e 2.724 + 108 = 2.832 campos de referência (105 nas entidades novas e 3 nas existentes). As 192 entidades mestres são as 186 de antes mais seis novas: `Cad_Operador_Estrangeiro`, `Cad_Comex_Codigo`, `Cad_Duimp_Fundamento_Cclasstrib`, `Cad_Duimp_Tributo_Parametro`, `Cad_Pcce_Conta_Autorizada` e `Cad_Participante_Qualificacao_Cbs`.

Auditoria: **0 achados em aberto** (a primeira passada achou 52, explicados na seção 6). **PostgreSQL 16 sem erro** nos oito arquivos de onda e no de comentários, rodados numa instância nova: 1.178 tabelas, 3.024 chaves estrangeiras e 8.762 comentários conferidos no banco. O T-SQL foi lido pelo analisador (sqlglot), sem erro; **não foi executado num SQL Server**.

Módulos alterados: Fase 0 (revisão 74), Contas a Pagar/Receber (22) e Contabilidade & Fiscal (44). **As 54 entidades novas estão todas na Contabilidade & Fiscal** (seção 2).

# 2. Como li o "consolidar"

Você respondeu "B1 completo (Recomendado)": entram os documentos 142, 143 e 144 inteiros, a entidade do B2, as cargas e os textos de regra já respondidos. O B1 ainda tem perguntas sem resposta (Q144-1 a Q144-12), então **entra com as minhas leituras marcadas abaixo**; se alguma estiver errada, diga e eu corrijo na revisão 27.

- **Módulo.** As 54 entidades novas ficam na **Contabilidade & Fiscal** (seção 40 do documento 10, anexo), onde já moram a nota de saída de importação e a locação. `Mov_Locacao_Pagamento` fica nesse módulo, mas **vai para a onda 5 do DDL**, porque exige `Cad_Gestao_Contrato`.
- **Tipos.** Os tipos que as especificações usavam e o dicionário não tem foram convertidos: "decimal (p,s)" virou `número (p,s)` (por exemplo, `número (16,7)` na Duimp, R1 do documento 142; o gerador do DDL passou a ler essa forma e gera `numeric(16,7)`); "inteiro" virou `número`; "enumeração (12 valores)" dos quatro campos `Tipo_Tributo` virou a lista dos 12 tipos do Portal; "código (N, domínio aberto)" virou `código (N)`.
- **Obrigatoriedade (leitura minha).** Na Duimp, **o que não é chave nem referência ao pai é opcional**, porque a importação grava o que conseguir e abre aviso para o resto (R9 do documento 143); ficaram obrigatórios só os identificadores (número da Duimp, versão, item, tipo de tributo e semelhantes) e as referências ao pai (versão, item, importação). Cada entidade tem a lista exata no documento 142.
- **Identidade.** Os campos das "chaves únicas" dos documentos 142 e 143 foram marcados como `--- identidade`: `Mov_Duimp` (número), `Mov_Duimp_Versao` (Duimp e versão), `Mov_Duimp_Item` (versão e número do item), `Mov_Duimp_Tributo_Total`, `Mov_Duimp_Item_Tributo`, `Cad_Operador_Estrangeiro` (código e versão), `Cad_Comex_Codigo` (tabela e código), `Cad_Duimp_Fundamento_Cclasstrib` e `Cad_Duimp_Tributo_Parametro` (tipo de tributo; a empresa não entrou na identidade porque pode ser vazia, e a unicidade por empresa fica para o motor).
- **Vigência.** Seis entidades mestres (com `_Versao` e o trio de vigência): as cinco cadastros do B1 acima e a qualificação do B2 ("janela com identificador de versão", como no documento 116).
- **Credencial do Portal.** `Cad_Autoridade_Fiscal_Credencial.Client_Id` passou a **opcional** e `Tipo_Autenticacao` {chave_acesso, certificado} também é opcional: a plataforma da CBS segue com Client Id e segredo (tipo vazio) e o Portal Único autentica por chave ou certificado. É leitura minha; o documento 144 listava só os campos novos.
- **Nomes.** Quatro acertos de nome ou de referência que o dicionário exige: `Cad_Produto` (que não existe) virou `Cad_Produto_Servico`; `Mov_Titulo_Baixa_Titulo` virou `Mov_Titulo_Baixa`; `Mov_Duimp_Versao.Frete_Consolidado_Moeda` virou `ID_Moeda_Frete_Consolidado` (referência sem o prefixo `ID_` é achado da auditoria); `Mov_Duimp_Importacao_Ocorrencia.ID_Registro_Destino` passou a referência genérica.
- **Tipo_Tributo em maiúsculas.** Os 12 códigos (II, IPI, PIS, COFINS, CBS, IBS_ESTADUAL e os demais) ficam como o Portal os envia, e a auditoria passou a aceitá-los como siglas. As duas tabelas de código do Portal (`Cad_Comex_Codigo` e `Cad_Duimp_Fundamento_Cclasstrib`) ficam sem chave estrangeira de propósito, ligadas por texto, como as demais tabelas de código; a auditoria as aceita.
- **B2.** A entidade `Cad_Participante_Qualificacao_Cbs` entra com os **20 campos do documento 116** (Q116-1, "sim"), e o domínio `qualificacao_cbs` entra como valor do domínio aberto. Os 30 tipos (Q116-2, "sim") **ainda não viram carga**: o próprio documento 116 (seção 4) condiciona a carga à conferência do contador com o artigo de cada tipo, e as descrições em português saem nessa conferência. `Participa_Pnct` não foi criado (Q116-6 e Q140-3). As Q116-7 e Q116-8 (sim) estão no texto da entidade; Q116-4 e Q116-5 já tinham entrado na revisão 25.
- **Q143-3 e o enum de `Ambiente`.** O ambiente `treinamento` entra em `Cad_Autoridade_Fiscal_Credencial.Ambiente`; o valor `portal_unico` de `uso_certificado_digital` e a linha "Portal Único Siscomex" de `Cad_Autoridade_Fiscal` são carga.
- **Lista legal.** Os 14 anexos da LC 214 (o XIV está revogado) viram os valores `lc214_anexo_i` a `lc214_anexo_xv` do domínio aberto `tipo_lista_legal` (**nomes meus**) e o Anexo XVII entra como `imposto_seletivo` (já existente). A vigência de partida é **01/01/2027 em todas as linhas, provisória** (o documento 137 não traz a data de cada anexo).

# 3. O que entrou

## 3.1 Entidades novas (54)

| Grupo (anexo da seção 40 do documento 10) | Entidades | Campos | Decisão |
|---|---:|---:|---|
| Duimp: cabeçalho, versões e situação | 15 | 127 | Documentos 142 e 143 (Q141, Q142-1 a Q142-12, Q143) |
| Duimp: itens, tributos, rateio e catálogo | 16 | 176 | Documentos 142 a 144 |
| Duimp: cadastros e parâmetros | 9 | 84 | Documentos 142 e 143 |
| Duimp: importação do JSON e reimportação | 3 | 35 | Documentos 143 e 144 (Q143-1 a Q143-3) |
| Pagamento Centralizado (PCCE) e ICMS da importação | 6 | 81 | Documentos 142 e 143 (Q142-6 a Q142-9) |
| Leitura pela API do Portal Único | 3 | 32 | Documento 144 (Q143-3) |
| Aluguel recebido (a empresa como locatária) | 1 | 15 | Documento 144 |
| Qualificação do participante perante a CBS | 1 | 20 | Documento 116 (D-N268, Q94-3, Q116-1 a Q116-3, Q116-6 a Q116-8) |

A lista completa, com os campos, está na seção 40 do documento 10 e nos documentos 142, 143 e 144; as contagens por grupo acima somam os campos já com o trio de vigência e a chave da versão.

## 3.2 Campos novos em entidades existentes (14)

| Entidade | Campos novos | Decisão |
|---|---|---|
| `Mov_Nota_Fiscal_Saida_Item_Importacao` | `ID_Duimp_Item` | Documento 142, seção 9 |
| `Cad_Autoridade_Fiscal_Credencial` | `Tipo_Autenticacao`, `Perfil_Portal`, `ID_Certificado`, `Data_Expiracao_Chave` | Q143-3 |
| `Cad_Locacao_Obrigacao_Emissao` | `Percentual_Antecipacao`, `ID_Serie_Cotacao_Atualizacao` | Q143-11 |
| `Mov_Locacao_Limite_Pf` | `Receita_Locacao_Fora_Erp`, `Quantidade_Imoveis_Fora_Erp`, `Limite_Receita_Aplicado`, `Percentual_Do_Limite`, `Obrigado_Emitir_Ano_Corrente`, `Data_Ultrapassou_Limite_Antecipado`, `Origem_Calculo` | Q143-11 |

## 3.3 Domínios e valores de enumeração

- `Cad_Classe_Sistema.Dominio`: **15 domínios abertos** novos, 14 do comércio exterior (`situacao_duimp`, `situacao_analise_retificacao`, `situacao_licenciamento`, `controle_carga`, `canal_analise_risco`, `resultado_tratamento_administrativo`, `situacao_conferencia_aduaneira`, `situacao_conferencia_anuente`, `resultado_analise_risco_rfb`, `resultado_analise_risco_anuente`, `situacao_pcce_icms`, `tipo_evento_pcce_icms`, `tipo_tratamento_icms` e `tipo_despesa_importacao`) e `qualificacao_cbs`. Os valores de partida, lidos nas especificações públicas do Portal em 28/10/2026, estão no anexo do documento 10.
- `Mov_Titulo.Origem_Tipo`: **`duimp_tributo`**, **`duimp_icms`** e **`locacao_pagamento`**.
- `Cad_Autoridade_Fiscal_Credencial.Ambiente`: **`treinamento`**.
- `Cad_Gestao_Contrato_Imovel.Papel_Empresa`: **`locataria`** (aluguel recebido: "o ERP tem que permitir receber e emitir notas de aluguel").
- Em `Mov_Duimp_Importacao`, `Situacao` passa a {importado, importado_com_avisos, rejeitado}; em `Mov_Pcce_Icms_Solicitacao`, `Tipo_Tratamento` substitui `Tratamento_Duimp` e `Situacao` usa os 15 códigos da API; em `Cad_Duimp_Tributo_Parametro`, `Debito_Automatico` e `Forma_Recolhimento_Sem_Debito` substituem `Forma_Recolhimento`. São mudanças do desenho (documentos 143 e 144), feitas dentro das entidades novas.

## 3.4 Texto de regra alterado (11 campos, 8 entidades)

| Entidade | Campos | Decisão |
|---|---|---|
| `Cad_Classe_Sistema` | `Dominio` (os 15 domínios, e as linhas de carga `portal_unico` e `qualificacao_cbs_do_adquirente` e `_do_fornecedor`) | Documentos 142 a 144 e 116 |
| `Mov_Titulo` | `Origem_Tipo` | Documentos 142 e 144 |
| `Cad_Autoridade_Fiscal_Credencial` | `Ambiente`, `Client_Id` | Q143-3 |
| `Cad_Gestao_Contrato_Imovel` | `Papel_Empresa` | Aluguel recebido |
| `Cad_Locacao_Obrigacao_Emissao` | `Receita_Anual_Minima`, `Quantidade_Imoveis_Minima` (estritamente maior) | Q143-11 |
| `Mov_Locacao_Limite_Pf` | `Receita_Locacao`, `Quantidade_Imoveis_Locados` (total: ERP mais fora do ERP) | Q143-11 |
| `Mov_Ecf_Apuracao_Linha_Valor` | `Origem` (demais atividades do P130, versão da linha, base negativa da CSLL de 2025, aspas tipográficas) | Q134-1 a Q134-6 e Q135-1 a Q135-4 |
| `Cad_Ecf_Linha_Mapeamento` | `ID_Tabela_Linha` (só a receita incentivada é mapeada; as demais atividades sobram sozinhas) | Q134-1 e Q134-2 |

# 4. O que ficou de fora

| Item | Por que ficou | Onde está |
|---|---|---|
| **Q144-1 a Q144-12** | Sem resposta (despesas da nota por valor, locação de pessoa física, aluguel recebido; quatro vão ao contador) | Documento 38, seções 1.5c e 2.3 |
| **Q93-6, Q94-4 (confirmação), Q93-3b, Q93-7, Q93-8, Q118-x, Q122-1** | Sem resposta ou sem campos vistos | Documento 38 |
| **Q127-2 a Q127-5, Q128-3 a Q128-7, Q130-x, Q132-5** | Sem resposta | Documento 38 |
| **Q138, Q139, Q140-1 a Q140-7** | Sem resposta (conferência da LC 227 e medicamentos do art. 146, documentos 138 a 140) | Documento 38 |
| **Ajustes do art. 26 no B2** (Q138-5) | Pergunta aberta (condições do FII/Fiagro e do FIDC, opção irretratável, tipo de fundo contribuinte); a entidade entrou como o documento 116 a desenhou | Documento 38, seção 1.4c |
| **Anexo XVI da LC 214** (limite inferior da alíquota própria, 49 anos) | Não há entidade no dicionário; entra com o B0a (D-N295). O CSV acompanha a carga só para conferência | `Pendencias_Carga.csv` |
| **Carga dos 30 tipos de `qualificacao_cbs`** (aprovados na Q116-2) | O documento 116 a condiciona à conferência do contador com o artigo de cada tipo; as descrições em português saem nessa conferência | Documento 116, seção 4 |

# 5. Pontos de atenção

- **`Mov_Locacao_Pagamento` fica na onda 5 do DDL**, e não na 3 (a do módulo), porque exige `Cad_Gestao_Contrato`, da onda 5. É a única entidade nova que mudou de onda. As chaves estrangeiras opcionais que esperam a onda de destino passam de 63 para 66.
- **Onda 3 pesa agora 468 entidades** (era 415) e 1.343 chaves estrangeiras; o arquivo `onda_3_Contabil_Fiscal.sql` cresce em proporção.
- **Valores da Duimp com 7 casas.** O gerador passou a ler `número (p,s)` e grava `numeric(16,7)` nos valores em reais e `numeric(13,7)` no valor unitário na moeda negociada; os percentuais saem como `numeric(15,8)` pela regra geral das taxas e percentuais.
- **Débito automático.** Partida: ligado nos 9 tipos que o Portal aceita no registro e desligado em CBS e IBS (o Portal não debita esses dois na versão 75.2.0). Com o débito desligado, quem paga é o despachante (título a pagar ao despachante, um por tributo) ou a empresa (guia).
- **Chamadas ao Portal.** O registro de cada chamada (`Mov_Portal_Chamada`) e o limite por hora (`Cad_Portal_Sincronizacao.Maximo_Chamadas_Por_Hora`) existem para o ERP respeitar o bloqueio da API (PUCX-ER1001: a 1ª ocorrência bloqueia até o fim da hora; a 2ª, mais 6 horas; da 3ª em diante, 24 horas). A regra em si é do motor, não do dicionário.
- **Segredos.** Nenhuma credencial, chave de acesso ou certificado é gravado no dicionário ou nas cargas; o segredo continua só no cofre (`Referencia_Cofre_Segredo`).
- **Domínios do Portal são de partida.** Os valores foram lidos das especificações públicas; as tabelas Comex só trazem valores pela API autenticada, então `Cad_Comex_Codigo` só tem como carga de partida o Incoterm (13 códigos) e os códigos de tributo (11), provisórios; as demais esperam a Q143-10.
- **Documento 31, seção 2.2.** O quadro das entidades criadas em onda posterior à do módulo não trazia `Mov_Remessa_Bancaria_Item_Exterior` (que a revisão 25 já tinha posto na onda 3); incluí a linha dela e a de `Mov_Locacao_Pagamento`, e o texto passou de 46 para 48 entidades.
- **A carga da ECF** passa de 4.486 para 4.488 linhas (P200 26 e P400 21 em duas versões cada; só essas duas linhas mudaram em relação à carga 25). As 4 colisões da X480 continuam sem `Codigo_Referencia` (8 linhas) e vão para `Pendencias_Carga.csv`.
- **A carga da lista legal** (708 linhas) é **provisória**: 29 linhas "conferir exceto", 11 NBS em nível curto e 9 capítulos têm marca para o contador; a vigência de partida é 01/01/2027; os nomes dos tipos de lista são meus.

# 6. Como conferi

- **Dicionário:** comparei o modelo antes e depois. Entraram exatamente 54 entidades (570 campos), 14 campos novos em 5 entidades existentes e o texto de 11 campos em 8 entidades; nenhum campo foi removido e nenhuma entidade mudou de módulo. Conferi que **todos os 540 campos** das especificações dos documentos 142, 143 e 144 (e das mudanças da seção 6 deles) estão no modelo, salvo o trio de vigência, que o motor acrescenta, e a renomeação de `Frete_Consolidado_Moeda`.
- **Auditoria:** a primeira passada achou 52 pontos: 48 valores de enumeração fora de `snake_case` (os 12 códigos de tributo em 4 campos), 1 campo `ID_` que não era referência (`ID_Registro_Destino`), 1 referência sem o prefixo `ID_` (`Frete_Consolidado_Moeda`) e 2 entidades isoladas (as duas tabelas de código do Portal). Corrigi os dois campos e aceitei de propósito os códigos em maiúsculas e as duas tabelas de código, como as demais exceções de 04/10/2026. Fechou com 0 achados.
- **DDL:** gerado nos dois dialetos (1.178 tabelas, 3.024 chaves estrangeiras, 3.099 índices e 8.762 comentários). No PostgreSQL 16 tudo rodou numa instância nova, sem erro; conferi no banco que `mov_duimp_item_valor.valor_frete_reais` é `numeric(16,7)` e `mov_duimp_tributo_total.valor_a_recolher` é `numeric(16,7)`, e que as contagens de tabelas, chaves e comentários batem com o gerador.
- **T-SQL:** 16.064 comandos lidos por analisador de sintaxe (sqlglot), sem erro de leitura; o aumento de 871 comandos é exatamente 60 tabelas, 114 chaves estrangeiras, 114 índices e 583 comentários. **Não equivale a executar num SQL Server.**
- **Modelo ER em Word:** regerado para os 14 módulos, com 89 diagramas (eram 85) e 1.549 chaves entre módulos.
- **Limites:** nada foi validado pelo contador; o que depende dele está nos documentos 142 a 144 e 116 (tributação da importação e do aluguel recebido, a locação de pessoa física, os 30 tipos de qualificação) e na seção 4 acima.
