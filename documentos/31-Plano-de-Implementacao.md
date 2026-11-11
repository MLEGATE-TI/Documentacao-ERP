# Plano de Implementação por Ondas e DDL — Documento 31

*Ordem técnica de construção do banco a partir do dicionário (revisão 40 do dicionário, de 11/11/2026: Fase 0 revisão 87, Folha & RH 29, Contabilidade & Fiscal 58, CRM & Vendas 24, Compras 29, Estoque 18, Produção 16, Contas a Pagar/Receber 31, Tesouraria 12, Jurídico 8, Gestão de Contratos 8), com o DDL gerado e testado; os números abaixo foram refeitos depois da consolidação da revisão 40 (documento 211: os documentos 204, tributação do veículo por combustível, potência e art. 149, com o B1 do 205; 206, Programa Mover e Rota 2030; e 209, autopeças por destinação; 25 entidades novas, todas em Contabilidade & Fiscal e na onda 3 (as sete com vigência são mestres: Cad_Veiculo_Versao, Cad_Veiculo_Versao_Sustentavel, Cad_Is_Veiculo_Ajuste, Cad_Mover_Ato_Registro, Cad_Mover_Habilitacao, Cad_Mover_Parametro e Cad_Autopecas_Perfil; as dezoito sem vigência são movimentos); 15 campos novos em 5 entidades existentes (Cad_NCM_Imposto_Seletivo 6, Mov_Nota_Fiscal_Entrada_Item 1, Mov_Nota_Fiscal_Saida_Item 4, Mov_Pedido_Venda_Item 3 e Mov_Nota_Fiscal_Saida_Item_St_Informacao 1; os dois campos do B1 e o ID_Mover_Ato_Registro já nasceram dentro das entidades novas) e 91 referências novas; de 1410 para 1442 tabelas, de 3700 para 3798 chaves estrangeiras, de 3791 para 3889 índices e de 11120 para 11519 comentários; as chaves estrangeiras que esperam a onda de destino passam de 80 para 81: a nova é Mov_Beneficio_Veiculo_Utilizacao.ID_Nota_Fiscal_Saida_Item, da onda 3 para a 4) e, antes dela, depois da consolidação da revisão 39 (documento 208: o documento 202, o desenho do B6, regime automotivo, com o ajuste A1 do documento 205; 8 entidades novas, todas em Contabilidade & Fiscal e na onda 3 (as duas com vigência são mestres: Cad_Habilitacao_Automotiva e Cad_Credito_Automotivo_Parametro; as seis sem vigência são movimentos: Cad_Habilitacao_Automotiva_Produto, Mov_Credito_Automotivo_Apuracao, Mov_Credito_Automotivo_Apuracao_Ncm, Mov_Credito_Automotivo_Debitos_Proprios, Mov_Habilitacao_Automotiva_Compromisso e Mov_Credito_Automotivo_Devolucao); 1 campo novo em 1 entidade existente (Mov_Credito_Fiscal_Aplicacao) e 18 referências novas; de 1400 para 1410 tabelas, de 3680 para 3700 chaves estrangeiras, de 3771 para 3791 índices e de 10993 para 11120 comentários; as chaves estrangeiras que esperam a onda de destino seguem em 80, sem nenhuma nova) e, antes dela, depois da consolidação da revisão 38 (documento 203: os documentos 200, o desenho do B0b-2, e 201, a documentação dos parâmetros; 10 entidades novas: oito em Contabilidade & Fiscal e na onda 3 (as três com vigência são mestres: Cad_Regra_Credito_Tomador, Cad_Parametro_Documentacao e Cad_Parametro_Efeito_Obrigacao; as cinco sem vigência são movimentos: Cad_Arrendamento_Mercantil, Mov_Arrendamento_Parcela, Mov_Antecipacao_Recebivel, Mov_Antecipacao_Recebivel_Item e Mov_Credito_Servico_Regime_Especifico) e duas em Folha & RH e na onda 6 (Mov_Rh_Beneficio_Acordo_Coletivo e Mov_Rh_Beneficio_Credito_Cbs, sem vigência); 5 campos novos em 2 entidades existentes (Mov_Emprestimo e Cad_Serie_Cotacao) e 41 referências novas; de 1387 para 1400 tabelas, de 3636 para 3680 chaves estrangeiras, de 3727 para 3771 índices e de 10816 para 10993 comentários; as chaves estrangeiras que esperam a onda de destino passam de 79 para 80: a nova é Cad_Arrendamento_Mercantil.ID_Contrato, opcional, para Cad_Gestao_Contrato, da onda 5) e, antes dela, depois da consolidação da revisão 37 (documento 199: o documento 198, o desenho do B4, e o documento 160; 11 entidades novas, todas em Contabilidade & Fiscal e na onda 3 (as quatro com vigência são mestres: Cad_Participante_Regime_Base, Cad_Componente_Base_Regime, Cad_Regime_Aliquota_Soma e Cad_Coeficiente_Rateio_Plano_Saude; as sete sem vigência são movimentos: Mov_Regime_Especifico_Afericao, Mov_Regime_Especifico_Saldo_Dedutivel, Mov_Regime_Especifico_Saldo_Utilizacao, Mov_Dere_Individualizacao, Mov_Dere_Individualizacao_Dependente, Mov_Dere_Ativo_Garantidor_Mes e Mov_Dere_Deducao_Documento); 2 campos novos em 2 entidades existentes e 39 referências novas; de 1372 para 1387 tabelas, de 3593 para 3636 chaves estrangeiras, de 3684 para 3727 índices e de 10669 para 10816 comentários; as chaves estrangeiras que esperam a onda de destino seguem em 79) e, antes dela, depois da consolidação da revisão 36 (documento 197: o documento 159 aprovado, o documento 196 e a D-N523; 6 entidades novas, a primeira na Fase 0 e na onda 0 (Cad_Is_Hipotese_Base, as hipóteses do Imposto Seletivo por NCM), duas em Jurídico e na onda 2 (Mov_Processo_Consulta_Tributaria e Mov_Processo_Uniformizacao, sem vigência) e três em Contabilidade & Fiscal e na onda 3 (Cad_Instituto_Beneficio_Ordem, Cad_Parametro_Legal_Ibs_Cbs e Cad_Programa_Conformidade_Beneficio); as quatro com vigência são mestres; 14 campos novos em 4 entidades existentes e 20 referências novas; de 1362 para 1372 tabelas, de 3569 para 3593 chaves estrangeiras, de 3660 para 3684 índices e de 10587 para 10669 comentários; as chaves estrangeiras que esperam a onda de destino seguem em 79) e, antes dela, depois da consolidação da revisão 35 (documento 195: os documentos 185 e 187, 189 a 192, as respostas às Q188-3 a Q188-5 e as datas do Confia e do REIDI; 3 entidades novas, 1 na Fase 0 e na onda 0 (Cad_Participante_Situacao_Cnpj_Motivo, o motivo estruturado da suspensão do CNPJ, que não é mestre) e 2 em Contabilidade & Fiscal e na onda 3 (Mov_Ecf_Periodo, o registro 0000 da ECF, e Mov_Ciencia_Indicio_Infracao, a ciência do indício de infração), nenhuma mestre; 7 campos novos em 4 entidades existentes e 8 referências novas; de 1359 para 1362 tabelas, de 3561 para 3569 chaves estrangeiras, de 3652 para 3660 índices e de 10561 para 10587 comentários; as chaves estrangeiras que esperam a onda de destino seguem em 79) e, antes dela, depois da consolidação da revisão 34 (documento 186: o B3, compras governamentais e Zona Franca de Manaus e áreas de livre comércio, documento 158; a transação de cartão, documento 177; o núcleo da ECD, documento 183; a moeda funcional, as subcontas e o razão auxiliar, a mudança do plano, o histórico padrão, o relacionamento e o bloco K, documento 184; e a carga de cClass da NFGás; 28 entidades novas, todas em Contabilidade & Fiscal, 27 na onda 3 e **1 na onda 4** (Mov_Zfm_Alc_Internamento, que exige a nota de saída), 7 delas mestres na onda 3 (Cad_Regra_Compra_Governamental, Cad_Area_Incentivada, Cad_Zfm_Alc_Regra, Cad_Subconta_Contabil, Cad_Historico_Padrao, Cad_Participante_Relacionamento e Cad_Conta_Consolidada_Mapa) e 21 de movimento; 21 campos novos em 14 entidades existentes alteradas e 95 referências novas; de 1324 para 1359 tabelas, de 3459 para 3561 chaves estrangeiras, de 3547 para 3652 índices e de 10268 para 10561 comentários; as chaves estrangeiras que esperam a onda de destino passam de 75 para 79, com Mov_Lancamento.ID_Historico_Padrao e Mov_Titulo_Baixa.ID_Transacao_Cartao esperando a onda 3 e os dois campos de item de nota de entrada de Mov_Credito_Presumido_Zfm e Mov_Zfm_Alc_Importacao_Suspensao esperando a onda 4) e, antes dela, da revisão 33 e da revisão 32 (documento 178: as tabelas do validador da EFD-ICMS/IPI, documento 172; as lacunas G15 a G19 da EFD-ICMS/IPI, documento 175; e o confronto com o FAQ da Receita, documento 176; 32 entidades novas, todas em Contabilidade & Fiscal, 6 delas mestres na onda 3 (Cad_Icms_Beneficio_Ajuste_Codigo, Cad_Icms_Informacao_Adicional_Codigo, Cad_Efd_Codigo_Estadual, Cad_Iss_Df_Valor_Uniprofissional, Cad_Efd_Giaf_Campo e Cad_Efd_1601_Regra_Uf) e 26 de movimento; 43 campos novos em 22 entidades existentes alteradas e 99 referências novas; de 1286 para 1324 tabelas, de 3353 para 3458 chaves estrangeiras, de 3441 para 3546 índices e de 9965 para 10266 comentários; as chaves estrangeiras que esperam a onda de destino passam de 74 para 75). A revisão 33 (documento 182: o bônus de adimplência da CSLL ligado à baixa do título e ao desconto para a ECF, documentos 180 e 181; nenhuma entidade nova; 2 campos novos em `Mov_Bonus_Adimplencia_Csll`, que passam a 12.406 campos no total, e 1 chave estrangeira nova para `Mov_Titulo_Baixa`: de 3458 para 3459 chaves estrangeiras, de 3546 para 3547 índices e de 10266 para 10268 comentários; a mesma onda e a mesma contagem de entidades) mudou só os totais das tabelas abaixo. A revisão 31 (documento 174: o B0a, documento 157: fato gerador, ajuste da operação, acréscimos do art. 27, locação, transição de 2026, entrega do arquivo e cadastro da filial; o B5, documento 150: gorjeta, cooperativa, locação por temporada e agência de turismo; os combustíveis, documento 170, e os programas de apoio, documento 173; 27 entidades novas, 8 em Motores Transversais e na onda 0 (o catálogo e a alíquota dos combustíveis e os programas de apoio, todas mestres) e 19 na Contabilidade & Fiscal e na onda 3 (3 delas mestres: Cad_Locacao_Temporada_Regra, Cad_Participante_Modelo_Intermediacao e Cad_Participante_Autorizacao_Anp); 62 campos novos em 28 entidades existentes (33 alteradas em campo, valor ou texto de campo, mais 2 só em texto de descrição) e 110 referências novas; um campo removido (Mov_Estoque_Abertura_Cbs_Estorno.Valor_Acrescimos); de 1248 para 1286 tabelas, de 3232 para 3353 chaves estrangeiras, de 3313 para 3441 índices e de 9561 para 9965 comentários; as chaves estrangeiras que esperam a onda de destino passam de 70 para 74). A revisão 30 (documento 169: os arts. 5º, 57 e 12 da LC 214, documento 156; o BP-e modelo 63, documento 164; as lacunas G1 a G14 da EFD-ICMS/IPI, documento 168; e dois campos em Cad_Cclasstrib, documento 161; 28 entidades novas, todas em Contabilidade & Fiscal, 18 na onda 3 e **10 na onda 4** (BP-e, complementos de ST, CIAP por documento, item da operação equiparada e alienação do uso pessoal, que exigem a nota de saída ou de entrada), 2 delas mestres (Cad_Bloco_K_Exigencia_Registro e Cad_Utilidade_Classificacao_Efd); 102 campos novos em 30 entidades existentes (37 alteradas ao todo) e 106 referências novas; de 1218 para 1248 tabelas, de 3126 para 3232 chaves estrangeiras, de 3204 para 3313 índices e de 9162 para 9561 comentários; as chaves estrangeiras que esperam a onda de destino passam de 69 para 70). A revisão 29 (documento 166: o catálogo central de parâmetros por obrigação, documento 155; o selo de conformidade, os programas, o devedor contumaz e o bônus de adimplência da CSLL, documento 140; o ajuste de critério da ECF, o ajuste do IBS e da CBS na devolução do adiantamento e o evento do Simples na NF-e, documentos 152, 153 e 163; e a entrada de NFGas e NF3e, documento 165; 25 entidades novas, todas em Contabilidade & Fiscal, 10 na onda 3 e **15 na onda 4** (NFGas e NF3e, que exigem a nota de entrada), 2 delas mestres (Cad_Obrigacao_Parametro_Definicao e Cad_Obrigacao_Parametro_Valor); 23 campos novos em 9 entidades existentes e 67 referências novas; de 1191 para 1218 tabelas, de 3057 para 3126 chaves estrangeiras, de 3133 para 3204 índices e de 8883 para 9162 comentários; as chaves estrangeiras que esperam a onda de destino passam de 66 para 69). A revisão 28 (documento 154: o mapa da atividade de presunção, documentos 127 e 152, e o adiantamento de clientes, documento 153; 4 entidades novas, todas em Contabilidade & Fiscal e na onda 3, 1 delas mestre (Cad_Adiantamento_Regra_Tributacao); 4 campos novos em 4 entidades existentes e 12 referências novas; de 1186 para 1191 tabelas, de 3044 para 3057 chaves estrangeiras, de 3119 para 3133 índices e de 8838 para 8883 comentários; as chaves estrangeiras que esperam a onda de destino seguiam em 66). A revisão 27 (documento 151: o TEF da SAF, documentos 146, 147 e 149, e a hotelaria e o Motor de Regras, documento 148; 5 entidades novas, todas em Contabilidade & Fiscal e na onda 3, 3 delas mestres; 4 campos novos em 4 entidades existentes e 17 referências novas; de 1178 para 1186 tabelas, de 3024 para 3044 chaves estrangeiras, de 3099 para 3119 índices e de 8762 para 8838 comentários; as chaves estrangeiras que esperam a onda de destino seguem em 66). A revisão 26 (documento 145: B1 completo, documentos 142 a 144, e B2, documento 116; 54 entidades novas, todas em Contabilidade & Fiscal, 53 na onda 3 e **Mov_Locacao_Pagamento na onda 5**, porque exige Cad_Gestao_Contrato; 14 campos novos em 5 entidades existentes, 108 referências novas, 15 domínios novos e 6 entidades mestres novas; de 1118 para 1178 tabelas, de 2910 para 3024 chaves estrangeiras, de 2985 para 3099 índices e de 8179 para 8762 comentários; as chaves estrangeiras que esperam a onda de destino passam de 63 para 66). A revisão 25 (documento 133) tinha levado o dicionário de 925 para 932 entidades e de 1111 para 1118 tabelas, com Mov_Remessa_Bancaria_Item_Exterior na onda 3 e não na 1), antes dela a revisão 23 (documento 117), que **não mudou nenhum número** (2 valores de enumeração e textos de 6 campos, sem entidade, campo ou referência nova), antes dela a revisão 22 (documento 113: 2 entidades novas, as duas em Contas a Pagar/Receber (onda 1: Cad_Tipo_Baixa, mestre com vigência, e Cad_Tipo_Baixa_Bloco), 8 entidades existentes alteradas, 25 campos novos, 6 referências novas e 1 domínio novo; de 1105 para 1108 tabelas, de 2864 para 2871 chaves estrangeiras, de 2935 para 2943 índices e de 8029 para 8054 comentários; nenhuma entidade mudou de onda e as 63 chaves estrangeiras que esperam a onda de destino são as mesmas), antes dela da revisão 21 (documento 108: 5 entidades novas, 4 em Contabilidade & Fiscal (onda 3: naturezas da operação cambial, classificação do Y520 por pagamento, Y520 consolidado e mapa de sugestão da natureza) e 1 em Contas a Pagar/Receber (onda 1: reavaliação cambial do título), 8 entidades existentes alteradas, 95 campos novos; de 1099 para 1105 tabelas, de 2838 para 2864 chaves estrangeiras, de 2908 para 2935 índices e de 7936 para 8029 comentários), antes dela da revisão 20 (documento 97: nenhuma entidade nova nem campo novo; tipo do lançamento contábil em três valores e regra do lote em Mov_Lancamento e Mov_Lote_Lancamento, e o sufixo Com_Sinal em dois campos da ECF; só mudam 2 comentários de coluna, de 7934 para 7936), antes dela da revisão 19 (documentos 90 e 95: 8 entidades novas, 6 em Contabilidade & Fiscal (onda 3: lista legal por NCM e NBS, depreciação da CBS, crédito presumido por categoria, repasse da agência de turismo, auto de infração e regra de operação equiparada) e 2 em Folha & RH (onda 6: ocorrências do retorno do eSocial), 13 entidades existentes alteradas, 5 domínios novos e 1 que saiu, e 1 entidade mestre a mais: 184 agora; nenhuma entidade mudou de onda e as 62 chaves estrangeiras que esperam a onda de destino são as mesmas), antes dela da revisão 18 (documentos 91 e 92: plano referencial da ECF por segmento, forma de tributação e finalidade; nenhuma entidade nova, 3 campos novos em Cad_Ecf_Tabela_Dinamica, 1 que saiu de Cad_Plano_Referencial e 3 novos em Cad_Empresa_Perfil_Fiscal, todos na onda 3, mais 2 domínios novos; nenhuma entidade mudou de onda e as 62 chaves estrangeiras que esperam a onda de destino são as mesmas), antes dela da revisão 17 (documentos 84 a 88 e 89: 8 entidades novas, todas em Contabilidade & Fiscal e na onda 3 (DES-IF, leiaute e tabelas dinâmicas da ECF, importação da ECF por linha e por campo), 1 que saiu (Cad_Lalur_Tabela_Dinamica), 25 existentes alteradas, 6 domínios novos e 3 entidades mestres a mais: 183 agora; nenhuma entidade mudou de onda e as 62 chaves estrangeiras que esperam a onda de destino são as mesmas), antes dela da revisão 16 (documentos 80 e 82: 5 campos novos na DES-IF, em Cad_Desif_Instituicao e Mov_Desif_Declaracao, na onda 3, sem chave estrangeira, entidade nem domínio novos), antes dela da revisão 15 (documento 78: 1 campo e 1 chave estrangeira novos em Cad_Rh_Funcao, na onda 6, sem entidade nova nem mudança de onda) e, antes dela, das revisões 12, 13 e 14 (documentos 74, 75 e 76: 12 entidades novas, 9 na Folha & RH (onda 6: 2 da revisão 12 e 7 da 13) e 3 em Contabilidade & Fiscal (onda 3, revisão 14), 5 domínios novos e 2 entidades mestres novas, uma em cada uma dessas duas ondas: 180 mestres agora) e, antes delas, da revisão 11 (documento 72: calendário único da transição tributária, com 1 entidade nova no lugar de 3, 15 entidades existentes alteradas e 2 domínios novos; as seções 2.2 e 3 e a tabela 3.1 foram regeradas do modelo, porque estavam sem as entidades e chaves das revisões 9 e 10) e, antes dela, da revisão 10 (documento 69: respostas do pacote de importação de 14/10/2026, com 7 entidades novas, 6 campos novos em entidades existentes e 1 domínio novo) e antes dela depois da revisão 9 (documento 67: Regulamento da CBS e PUC, com 9 entidades novas, 15 campos novos em entidades existentes e 5 domínios novos) e da revisão 8 (documento 65: correção do controle de uso dos créditos de PIS/Cofins pelo texto oficial da LC 214, sem entidade nova, com 4 campos e 1 chave estrangeira novos); a revisão 7 levou o dicionário de 857 para 874 entidades (documentos 59, 60 e 61: dono único da escrituração, entrada de NFCom e NFAg e uso dos créditos de PIS/Cofins contra a CBS; a revisão 6, de 846 para 857, trouxe a NF-e ABI, documento 62; a revisão 5, de 837 para 846, tinha aplicado os documentos 48 a 50 e 53 a 57). Não altera o dicionário. Documento de controle da equipe.*

Mlegate · Alberto Beyeler · Outubro de 2026

# 1. Resumo

O dicionário vira 1442 tabelas físicas (1198 entidades; as 244 entidades mestres viram duas tabelas cada, identidade e versão), 3798 chaves estrangeiras, 3889 índices e 11519 comentários de coluna. O banco inicial é o **SQL Server** (decisão de Alberto, 04/10/2026), e o sistema terá uma camada de integração com o banco, para que uma troca de SGBD fique restrita a ela; por isso o DDL é gerado por **dialeto**: T-SQL para SQL Server (o primeiro, pasta sqlserver) e PostgreSQL 16 (pasta postgresql, que serve de prova de que a estrutura não depende de um único banco). O DDL foi dividido em oito ondas. A divisão obedece uma regra só: nenhuma chave estrangeira obrigatória aponta para uma onda posterior. A ordem é a **técnica** (o que pode existir antes do quê). A ordem de **negócio** (o que a Mlegate precisa primeiro) e os prazos legais são decisão sua; a seção 6 mostra os dois lado a lado. A seção 5 trata da camada de integração com o banco.

# 2. Ondas

| Onda | Conteúdo | Entidades | Mestres | Tabelas físicas | Campos | Chaves estrangeiras na onda |
|---|---|---|---|---|---|---|
| 0 | Fundação (Fase 0) | 179 | 63 | 242 | 1.846 | 410 |
| 1 | Financeiro base (Contas a Pagar/Receber e Tesouraria) | 28 | 4 | 32 | 332 | 95 |
| 2 | Jurídico | 42 | 5 | 47 | 492 | 150 |
| 3 | Contabilidade & Fiscal | 635 | 141 | 776 | 7.829 | 1883 |
| 4 | Suprimentos e Comercial (Planejamento, Compras, Estoque, CRM & Vendas) | 124 | 1 | 125 | 1.518 | 484 |
| 5 | Produção, Expedição e Gestão de Contratos | 58 | 6 | 64 | 525 | 202 |
| 6 | Folha & RH | 131 | 24 | 155 | 1.188 | 328 |
| 7 | Portal do Cliente | 1 | 0 | 1 | 8 | 2 |
| | **Total** | **1198** | **244** | **1442** | **13.738** | **3554** |

"Chaves estrangeiras na onda" conta as que ficam criadas quando a onda termina, incluindo as que apontam para ondas anteriores.

## 2.1. Dependências entre módulos

Além dos Motores Transversais (que todos usam), as dependências obrigatórias entre módulos, contadas pelas chaves estrangeiras obrigatórias, são: Tesouraria, de Contabilidade & Fiscal e Contas a Pagar/Receber; Contabilidade & Fiscal, de CRM & Vendas, Compras, Contas a Pagar/Receber, Estoque, Gestão de Contratos, Jurídico e Tesouraria; Folha & RH, de Jurídico; Jurídico, de Contabilidade & Fiscal e Contas a Pagar/Receber; Compras, de Contabilidade & Fiscal; CRM & Vendas, de Contabilidade & Fiscal e Estoque; Produção, de CRM & Vendas; Expedição, de CRM & Vendas e Compras; Gestão de Contratos, de Produção. Os Motores Transversais, por sua vez, têm campos obrigatórios que apontam para Folha & RH (5), Gestão de Contratos (1), Contabilidade & Fiscal (2) e outros módulos, e é isso que obriga a mover entidades da Fase 0 para onda posterior (seção 2.2).

## 2.2. Entidades que ficam em onda posterior à do seu módulo

79 entidades têm referência obrigatória a um módulo de onda posterior e por isso são criadas junto com ele: 8 da Fase 0 (Motores Transversais), 69 de Contabilidade & Fiscal (notas fiscais, CIAP, inventário, locação e, desde a revisão 29, a entrada de NFGas e NF3e, que dependem da nota de entrada, de Compras, Estoque, CRM & Vendas e Gestão de Contratos; desde a revisão 30, o BP-e, os complementos de ST e o CIAP por documento, que dependem da nota de saída ou de entrada; e, desde a revisão 34, o controle do internamento da Zona Franca de Manaus e das áreas de livre comércio, Mov_Zfm_Alc_Internamento, que depende da nota de saída) e 2 de outros módulos (Tesouraria e Jurídico). A revisão 26 corrigiu o quadro: Mov_Remessa_Bancaria_Item_Exterior, que a revisão 25 já tinha posto na onda 3, não constava dele. As 27 entidades da revisão 31 não entram neste quadro: as 8 de combustíveis ficam na onda 0 e as 19 da Contabilidade & Fiscal ficam na onda 3, junto com o seu módulo. As 25 da revisão 40 também não entram neste quadro: todas ficam na onda 3, em Contabilidade & Fiscal, e as chaves delas apontam para entidades de ondas anteriores ou da própria onda 3 (a exceção é a chave opcional Mov_Beneficio_Veiculo_Utilizacao.ID_Nota_Fiscal_Saida_Item, para a onda 4, que entra na tabela da seção 3.1). As 8 da revisão 39 também não entram neste quadro: todas ficam na onda 3, em Contabilidade & Fiscal, e as chaves delas apontam para entidades de ondas anteriores ou da própria onda 3. As 10 da revisão 38 também não entram neste quadro: oito ficam na onda 3, em Contabilidade & Fiscal, e duas na onda 6, em Folha & RH, cada uma com o seu módulo; as chaves delas apontam para entidades de ondas anteriores ou da própria onda (a exceção é a chave opcional Cad_Arrendamento_Mercantil.ID_Contrato, para Cad_Gestao_Contrato, da onda 5, criada com o ALTER TABLE da onda 5; ver a seção 3.1). As 11 da revisão 37 também não entram neste quadro: todas ficam na onda 3, em Contabilidade & Fiscal, e as chaves delas apontam para entidades de ondas anteriores ou da própria onda 3. As 6 da revisão 36 também não entram neste quadro: Cad_Is_Hipotese_Base fica na onda 0, Mov_Processo_Consulta_Tributaria e Mov_Processo_Uniformizacao, na onda 2, e Cad_Instituto_Beneficio_Ordem, Cad_Parametro_Legal_Ibs_Cbs e Cad_Programa_Conformidade_Beneficio, na onda 3, cada uma com o seu módulo. As 3 da revisão 35 também não entram neste quadro: Cad_Participante_Situacao_Cnpj_Motivo fica na onda 0, e Mov_Ecf_Periodo e Mov_Ciencia_Indicio_Infracao, na onda 3, junto com o seu módulo. Das 28 da revisão 34, 27 ficam na onda 3, junto com o seu módulo, e a que aparece abaixo vai para a onda 4:

| Entidade | Onda física | Motivo |
|---|---|---|
| Cad_Dfe_Emitente_Configuracao | 2 | obrigatória para Cad_Certificado_Digital |
| Cad_Distribuicao_Lucro_Parametro | 3 | obrigatória para Cad_Calendario_Transicao |
| Cad_Gestao_Contrato_Imovel | 5 | obrigatória para Cad_Gestao_Contrato |
| Cad_Modelo_Documento_Fiscal_Codigo | 3 | obrigatória para Cad_Obrigacao_Acessoria |
| Cad_Obra | 5 | obrigatória para Cad_Gestao_Contrato |
| Cad_Participante_Historico_Cargo | 6 | obrigatória para Cad_Rh_Cargo, Cad_Vinculo_Emprego |
| Cad_Participante_Historico_Departamento | 6 | obrigatória para Cad_Vinculo_Emprego |
| Cad_Participante_Historico_Filial | 6 | obrigatória para Cad_Vinculo_Emprego |
| Cad_Participante_Historico_Salario | 6 | obrigatória para Cad_Vinculo_Emprego |
| Mov_Bem_Usado_Aquisicao | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Bem_Usado_Venda | 4 | obrigatória para Mov_Bem_Usado_Aquisicao, Mov_Nota_Fiscal_Saida_Item |
| Mov_Bpe | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Bpe_Componente | 4 | obrigatória para Mov_Bpe |
| Mov_Bpe_Viagem | 4 | obrigatória para Mov_Bpe |
| Mov_Ciap_Apropriacao | 4 | obrigatória para Mov_Ciap_Bem |
| Mov_Ciap_Apropriacao_Outro_Periodo | 4 | obrigatória para Mov_Ciap_Apropriacao |
| Mov_Ciap_Bem | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Ciap_Bem_Item | 4 | obrigatória para Mov_Ciap_Bem |
| Mov_Ciap_Movimentacao | 4 | obrigatória para Mov_Ciap_Bem |
| Mov_Ciap_Movimentacao_Documento | 4 | obrigatória para Mov_Ciap_Movimentacao |
| Mov_Dfe_Produto_Perigoso | 3 | obrigatória para Mov_Mdfe_Documento |
| Mov_Estoque_Abertura_Cbs_Estorno | 4 | obrigatória para Mov_Devolucao_Compra_Item |
| Mov_Icms_St_Complemento_Devolucao_Saida | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Icms_St_Complemento_Entrada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Icms_St_Complemento_Saida | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Icms_St_Complemento_Saida_Entrada | 4 | obrigatória para Mov_Icms_St_Complemento_Saida |
| Mov_Icms_St_Ressarcimento | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item, Mov_Nota_Fiscal_Saida_Item |
| Mov_Inventario_Item_Complemento_St | 4 | obrigatória para Mov_Inventario_Item |
| Mov_Inventario_Item_Tributacao | 4 | obrigatória para Mov_Inventario_Item |
| Mov_Locacao_Faturamento | 5 | obrigatória para Cad_Gestao_Contrato |
| Mov_Locacao_Pagamento | 5 | obrigatória para Cad_Gestao_Contrato |
| Mov_Locacao_Repasse | 5 | obrigatória para Cad_Gestao_Contrato |
| Mov_Nf3e_Entrada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nf3e_Entrada_Grandeza_Contratada | 4 | obrigatória para Mov_Nf3e_Entrada |
| Mov_Nf3e_Entrada_Item | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Nf3e_Entrada_Item_Bandeira | 4 | obrigatória para Mov_Nf3e_Entrada_Item |
| Mov_Nf3e_Entrada_Item_Medicao | 4 | obrigatória para Mov_Nf3e_Entrada_Item, Mov_Nf3e_Entrada_Medidor |
| Mov_Nf3e_Entrada_Item_Tarifa | 4 | obrigatória para Mov_Nf3e_Entrada_Item |
| Mov_Nf3e_Entrada_Medidor | 4 | obrigatória para Mov_Nf3e_Entrada |
| Mov_Nf3e_Entrada_Scee_Geradora | 4 | obrigatória para Mov_Nf3e_Entrada |
| Mov_Nf3e_Entrada_Scee_Saldo | 4 | obrigatória para Mov_Nf3e_Entrada |
| Mov_Nfag_Entrada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nfag_Entrada_Item | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Nfag_Entrada_Item_Medicao | 4 | obrigatória para Mov_Nfag_Entrada_Item |
| Mov_Nfag_Entrada_Medidor | 4 | obrigatória para Mov_Nfag_Entrada |
| Mov_Nfcom | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nfcom_Entrada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nfcom_Entrada_Item | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Nfcom_Fatura | 4 | obrigatória para Mov_Nfcom |
| Mov_Nfcom_Item | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Nfcom_Item_Processo | 4 | obrigatória para Mov_Nfcom_Item |
| Mov_Nfcom_Item_Processo_Numero | 4 | obrigatória para Mov_Nfcom_Item_Processo |
| Mov_Nfgas_Entrada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nfgas_Entrada_Item | 4 | obrigatória para Mov_Nota_Fiscal_Entrada_Item |
| Mov_Nfgas_Entrada_Item_Medicao | 4 | obrigatória para Mov_Nfgas_Entrada_Item, Mov_Nfgas_Entrada_Medidor |
| Mov_Nfgas_Entrada_Item_Tarifa | 4 | obrigatória para Mov_Nfgas_Entrada_Item |
| Mov_Nfgas_Entrada_Medidor | 4 | obrigatória para Mov_Nfgas_Entrada |
| Mov_Nfgas_Entrada_Volume_Contratado | 4 | obrigatória para Mov_Nfgas_Entrada |
| Mov_Nota_Fiscal_Entrada_Fatura | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nota_Fiscal_Entrada_Item_Lote | 4 | obrigatória para Cad_Lote_Produto, Mov_Nota_Fiscal_Entrada_Item |
| Mov_Nota_Fiscal_Entrada_Referenciada | 4 | obrigatória para Mov_Nota_Fiscal_Entrada |
| Mov_Nota_Fiscal_Saida_Autorizado_Xml | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Combustivel_Transporte | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Item_Equiparada | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Nota_Fiscal_Saida_Item_Exportacao | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Nota_Fiscal_Saida_Item_Importacao | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Nota_Fiscal_Saida_Item_Importacao_Adicao | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item_Importacao |
| Mov_Nota_Fiscal_Saida_Item_Lote | 4 | obrigatória para Cad_Lote_Produto, Mov_Nota_Fiscal_Saida_Item |
| Mov_Nota_Fiscal_Saida_Item_St_Informacao | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Nota_Fiscal_Saida_Local | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Pagamento | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Referenciada | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Servico_Nao_Icms | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Terminal_Faturado | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Volume | 4 | obrigatória para Mov_Nota_Fiscal_Saida |
| Mov_Nota_Fiscal_Saida_Volume_Lacre | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Volume |
| Mov_Remessa_Bancaria_Item_Exterior | 3 | obrigatória para Cad_Natureza_Operacao_Cambial |
| Mov_Uso_Consumo_Pessoal_Alienacao | 4 | obrigatória para Mov_Nota_Fiscal_Saida_Item |
| Mov_Zfm_Alc_Internamento | 4 | obrigatória para Mov_Nota_Fiscal_Saida |

O dicionário continua como está (essas entidades pertencem à Fase 0 pelo desenho). A mudança é só de calendário de construção.

# 3. O que cada onda entrega

## Onda 0 — Fundação (Fase 0)

Cadastros, tabelas oficiais, motores de regra, participantes, empresas, filiais, aprovação, auditoria, plano de contas e períodos. Base de tudo. As 30 tabelas com código oficial (CFOP, NCM, municípios e outras) precisam de carga inicial antes de qualquer outra onda usá-las (seção 7).

Entidades por módulo: Motores Transversais (179).

Arquivos: `sqlserver/onda_0_Fundacao.sql` e `postgresql/onda_0_Fundacao.sql`.

## Onda 1 — Financeiro base (Contas a Pagar/Receber e Tesouraria)

Contas a pagar e a receber, títulos, baixas, remessas e retornos bancários, caixa e conciliação. Primeira onda com movimento financeiro.

Entidades por módulo: Contas a Pagar/Receber (16); Tesouraria (12).

Arquivos: `sqlserver/onda_1_Financeiro.sql` e `postgresql/onda_1_Financeiro.sql`.

## Onda 2 — Jurídico

Processos, partes, andamentos, perícias, advogados, prognósticos e suspensões. Folha & RH e Contabilidade dependem dele.

Entidades por módulo: Motores Transversais (1); Jurídico (41).

Arquivos: `sqlserver/onda_2_Juridico.sql` e `postgresql/onda_2_Juridico.sql`.

## Onda 3 — Contabilidade & Fiscal

Apuração de tributos, SPED, Reinf, DCTFWeb, MIT, LALUR e imobiliário. A maior onda em campos e a que concentra as tabelas de classificação fiscal.

Entidades por módulo: Motores Transversais (2); Tesouraria (1); Contabilidade & Fiscal (631); Jurídico (1).

Arquivos: `sqlserver/onda_3_Contabil_Fiscal.sql` e `postgresql/onda_3_Contabil_Fiscal.sql`.

## Onda 4 — Suprimentos e Comercial (Planejamento, Compras, Estoque, CRM & Vendas)

Orçamento, cotação e compras, estoque, pedidos, notas fiscais de entrada e saída, CRM e ordens de serviço.

Entidades por módulo: Planejamento & Orçamento (8); Compras (15); Estoque (20); CRM & Vendas (16); Contabilidade & Fiscal (65).

Arquivos: `sqlserver/onda_4_Suprimentos_Comercial.sql` e `postgresql/onda_4_Suprimentos_Comercial.sql`.

## Onda 5 — Produção, Expedição e Gestão de Contratos

Ordens de produção, expedição, contratos e obras, entregáveis e medições. O contrato de Gestão referencia Produção.

Entidades por módulo: Motores Transversais (1); Produção (35); Expedição (7); Contabilidade & Fiscal (4); Gestão de Contratos (11).

Arquivos: `sqlserver/onda_5_Producao_Expedicao_Contratos.sql` e `postgresql/onda_5_Producao_Expedicao_Contratos.sql`.

## Onda 6 — Folha & RH

Vínculos de emprego, cargos, folha, eventos do eSocial, benefícios, processo trabalhista e igualdade salarial. Inclui as quatro entidades de histórico de participante que a Fase 0 aponta para o vínculo.

Entidades por módulo: Motores Transversais (4); Folha & RH (127).

Arquivos: `sqlserver/onda_6_Folha_RH.sql` e `postgresql/onda_6_Folha_RH.sql`.

## Onda 7 — Portal do Cliente

Chamados do portal do cliente. Depende de Motores Transversais e entra por último.

Entidades por módulo: Portal do Cliente (1).

Arquivos: `sqlserver/onda_7_Portal_Cliente.sql` e `postgresql/onda_7_Portal_Cliente.sql`.

## 3.1. Chaves estrangeiras que esperam a onda de destino

81 chaves estrangeiras são opcionais e apontam para uma onda posterior. O DDL de cada onda não as cria; elas entram no arquivo da onda de destino, no final (comando ALTER TABLE). Até lá, a coluna existe e fica vazia.

| Criada na onda | Entidade | Campo | Aponta para | Onda da origem |
|---|---|---|---|---|
| 2 | Cad_Autoridade_Fiscal_Credencial | ID_Certificado | Cad_Certificado_Digital | 0 |
| 2 | Cad_Autoridade_Fiscal_Credencial | ID_Procuracao | Cad_Procuracao | 0 |
| 2 | Cad_Documento_Retencao | ID_Processo | Cad_Processo | 0 |
| 2 | Cad_Empresa_Responsavel | ID_Ato_Societario | Mov_Ato_Societario | 0 |
| 2 | Cad_Empresa_Responsavel | ID_Procuracao | Cad_Procuracao | 0 |
| 2 | Cad_Empresa_Socio | ID_Ato_Societario | Mov_Ato_Societario | 0 |
| 2 | Mov_Dfe_Transmissao | ID_Certificado | Cad_Certificado_Digital | 0 |
| 3 | Cad_Dfe_Parametro_Regra | ID_Calendario | Cad_Calendario_Transicao | 0 |
| 3 | Cad_Local_Operacao | ID_Cno_Obra | Cad_Cno_Obra | 0 |
| 3 | Cad_Produto_Servico | ID_Cprb_Atividade | Cad_Cprb_Atividade | 0 |
| 3 | Cad_Regra_Vencimento | ID_Obrigacao | Cad_Obrigacao_Acessoria | 0 |
| 3 | Mov_Decisao_Motor | ID_Reducao_Beneficio | Cad_Reducao_Beneficio_Federal | 0 |
| 3 | Mov_Dfe_Evento_Item | ID_Credito_Presumido_Ibs_Cbs | Cad_Credito_Presumido_Ibs_Cbs | 0 |
| 3 | Mov_Dfe_Lacre | ID_Mdfe | Mov_Mdfe | 0 |
| 3 | Mov_Lancamento | ID_Historico_Padrao | Cad_Historico_Padrao | 0 |
| 3 | Mov_Titulo | ID_Natureza_Operacao_Cambial | Cad_Natureza_Operacao_Cambial | 1 |
| 3 | Mov_Titulo_Baixa | ID_Transacao_Cartao | Mov_Transacao_Cartao | 1 |
| 3 | Mov_Distribuicao_Lucro_Pagamento | ID_Retencao | Mov_Titulo_Retencao | 2 |
| 4 | Cad_Ativo_Imobilizado | ID_Item_Nota_Entrada_Origem | Mov_Nota_Fiscal_Entrada_Item | 0 |
| 4 | Mov_Apuracao_Ajuste_Criterio | ID_Nota_Fiscal_Saida | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Beneficio_Veiculo_Utilizacao | ID_Nota_Fiscal_Saida_Item | Mov_Nota_Fiscal_Saida_Item | 3 |
| 4 | Mov_Bilhete_Passagem_Consolidado | ID_Nota_Rmd | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Cooperativa_Transferencia_Credito | ID_Nota_Fiscal_Saida | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Credito_Ajuste_Documento | ID_Nota_Ajuste | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Credito_Destino_Item | ID_Nota_Debito_Antecipacao | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Credito_Estoque_Abertura | ID_Fechamento_Estoque | Mov_Estoque_Fechamento_Custo_Medio | 3 |
| 4 | Mov_Credito_Presumido_Zfm | ID_Nota_Fiscal_Entrada_Item | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Duimp_Despesa_Rateio | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Duimp_Despesa_Rateio_Item | ID_Nota_Fiscal_Entrada_Item | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Empreendimento_Deducao | ID_Nota_Fiscal_Entrada_Item | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Estoque_Abertura_Cbs | ID_Fechamento | Mov_Estoque_Fechamento_Custo_Medio | 3 |
| 4 | Mov_Estoque_Abertura_Cbs_Item | ID_Saldo_Estoque_Valor | Mov_Saldo_Estoque_Valor | 3 |
| 4 | Mov_Estoque_Abertura_Cbs_Item | ID_Item_Inventario | Mov_Inventario_Item | 3 |
| 4 | Mov_Locacao_Temporada | ID_Nota_Fiscal_Saida | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Nfse_Aceite | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Agropecuario | ID_Nota | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Agropecuario | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Compra_Governamental | ID_Nota | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Compra_Governamental | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Item_Observacao | ID_Item | Mov_Nota_Fiscal_Saida_Item | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Item_Observacao | ID_Item_Entrada | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Item_Referencia | ID_Item | Mov_Nota_Fiscal_Saida_Item | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Item_Referencia | ID_Item_Entrada | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Retencao_Transporte | ID_Nota | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Retencao_Transporte | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Transporte_Veiculo | ID_Nota | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Nota_Fiscal_Saida_Transporte_Veiculo | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Operacao_Imobiliaria | ID_Pedido_Venda | Mov_Pedido_Venda | 3 |
| 4 | Mov_Operacao_Imobiliaria | ID_Nota_Fiscal_Saida | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Reinf_Aquisicao_Producao | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Reinf_Servico_Previdenciario | ID_Nota_Fiscal_Entrada | Mov_Nota_Fiscal_Entrada | 3 |
| 4 | Mov_Reinf_Servico_Previdenciario | ID_Nota_Fiscal_Saida | Mov_Nota_Fiscal_Saida | 3 |
| 4 | Mov_Uso_Consumo_Pessoal_Item | ID_Item_Nota_Entrada | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 4 | Mov_Zfm_Alc_Importacao_Suspensao | ID_Nota_Fiscal_Entrada_Item | Mov_Nota_Fiscal_Entrada_Item | 3 |
| 5 | Cad_Habilitacao_Regime_Especial | ID_Contrato | Cad_Gestao_Contrato | 0 |
| 5 | Cad_Local_Operacao | ID_Obra | Cad_Obra | 0 |
| 5 | Cad_Processo_Advogado | ID_Contrato_Honorarios | Cad_Gestao_Contrato | 2 |
| 5 | Mov_Processo_Pericia_Profissional | ID_Contrato_Honorarios | Cad_Gestao_Contrato | 2 |
| 5 | Cad_Arrendamento_Mercantil | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Cno_Contratante | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Cno_Obra | ID_Obra | Cad_Obra | 3 |
| 5 | Cad_Cno_Obra | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Empreendimento_Imobiliario | ID_Obra | Cad_Obra | 3 |
| 5 | Cad_Empreendimento_Imobiliario | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Locacao_Opcao | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Nfcom_Assinante | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Participante_Modelo_Intermediacao | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Cad_Ponto_Servico_Utilidade | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Mov_Locacao_Temporada | ID_Contrato | Cad_Gestao_Contrato | 3 |
| 5 | Mov_Mdfe | ID_Expedicao | Mov_Expedicao_Saida | 3 |
| 5 | Mov_Mdfe | ID_Trecho | Mov_Expedicao_Trecho | 3 |
| 5 | Mov_Nota_Fiscal_Entrada | ID_Contrato | Cad_Gestao_Contrato | 4 |
| 5 | Mov_Nota_Fiscal_Saida | ID_Expedicao | Mov_Expedicao_Saida | 4 |
| 5 | Mov_Nota_Fiscal_Saida_Item | ID_Ordem_Servico_Item | Mov_Ordem_Servico_Item | 4 |
| 6 | Cad_Filial | ID_Categoria_Sindical_Padrao | Cad_Rh_Categoria_Sindical | 0 |
| 6 | Mov_Pre_Cadastro_Conversao | ID_Vaga_Candidato | Mov_Rh_Vaga_Candidato | 0 |
| 6 | Mov_Equipamento_Atribuicao | ID_Vinculo | Cad_Vinculo_Emprego | 2 |
| 6 | Mov_Politica_Uso_Aceite | ID_Vinculo | Cad_Vinculo_Emprego | 2 |
| 6 | Mov_Processo_Pericia | ID_Ambiente_Trabalho | Cad_Rh_Ambiente_Trabalho | 2 |
| 6 | Mov_Dctfweb_Declaracao | ID_Processo_Trabalhista | Mov_Rh_Processo_Trabalhista | 3 |
| 6 | Mov_Simples_Folha_Mensal | ID_Folha_Apuracao | Mov_Rh_Folha_Apuracao | 3 |

# 4. Convenções do DDL

Os dois dialetos saem do mesmo modelo, com as mesmas tabelas, colunas, chaves e índices; muda só o mapa de tipos e a sintaxe. As regras abaixo valem para as oito ondas.

| Item | SQL Server (T-SQL) | PostgreSQL 16 |
|---|---|---|
| Nomes | minúsculas com sublinhado, entre colchetes, no esquema erp; limite de 128 caracteres | minúsculas com sublinhado, no esquema padrão; limite de 63 (nome longo é encurtado com sufixo de hash) |
| identificador | bigint IDENTITY(1,1) NOT NULL PRIMARY KEY | bigint GENERATED ALWAYS AS IDENTITY PRIMARY KEY |
| referência | bigint; chave estrangeira no fim do arquivo da onda (ALTER TABLE ... ADD CONSTRAINT) | igual |
| código (n) | varchar(n) | varchar(n) |
| texto (n) | nvarchar(n) até 4.000; acima disso nvarchar(max) | varchar(n) |
| texto sem tamanho | nvarchar(max); em chave única, nvarchar(200) (D-9) | text; em chave única, varchar(200) |
| número | numeric pelo nome do campo: percentual, alíquota e fator numeric(15,8); quantidade e peso numeric(19,6); valor, total, saldo e custo numeric(19,4); número, dias e meses int; demais numeric(19,6) | igual, com integer no lugar de int |
| data, data/hora, hora | date, datetimeoffset(3), time(0) | date, timestamptz, time |
| competência | date com CHECK (DAY(coluna) = 1) | date com CHECK de primeiro dia do mês |
| enumeração | varchar(80) com CHECK (coluna IN (...)) quando os valores são bem formados | igual |
| booleano | bit; default 1 ou 0 | boolean |
| Mestre (identidade e versão) | duas tabelas; identidade com UNIQUE sobre os campos marcados "— identidade"; versão com UNIQUE (id, Vigencia_Inicio), CHECK Vigencia_Fim >= Vigencia_Inicio e índice (id, início, fim) | igual |
| Vigência sem versão | CHECK de fim >= início e índice na primeira chave estrangeira mais a vigência | igual |
| Índices | um índice em toda coluna de chave estrangeira | igual |
| Comentários | sp_addextendedproperty (MS_Description) por coluna, em comentarios.sql, depois da onda 7 | COMMENT ON COLUMN, em comentarios.sql |
| Separador de lote | GO entre blocos (SSMS e sqlcmd) | não se aplica |
| Sem chave estrangeira | as referências genéricas (par tipo + identificador: 61 campos) | igual |

As restrições de unicidade que não estão marcadas "— identidade" no dicionário não foram inventadas. O DDL não cria gatilhos, visões, partições nem permissões; isso é projeto de banco, não de dicionário. Descrições de comentário são truncadas em 250 caracteres.

**Limites do SQL Server verificados no DDL.** Chave única ou índice não aceita nvarchar(max) e tem limite de 1.700 bytes (900 na chave primária agrupada). Quatro chaves únicas do dicionário eram sobre texto sem tamanho (Cad_Imposto.Sigla, Cad_Dado_Sensivel.Entidade e Campo, Cad_Lgpd_Tratamento.Nome e Cad_Politica_Uso_Equipamento.Nome) e foram limitadas a 200 caracteres, nos dois dialetos (decisão D-9). Depois do ajuste, nenhuma chave ou índice passa do limite de bytes, e a maior tabela tem 50 colunas.

# 5. Camada de integração com o banco

Alberto definiu (04/10/2026) que o banco inicial é o SQL Server e que o projeto terá um framework de integração com o banco, de modo que, numa troca de SGBD, a mudança fique restrita ao framework e o restante funcione sem alteração. Abaixo, o que o dicionário já garante e o que a camada precisa assumir.

**O que o dicionário já garante.** Ele é neutro: usa tipos lógicos (identificador, referência, código, texto, número, data, competência, booleano, enumeração) e não cita nenhum SGBD. O DDL é derivado dele por um gerador com um adaptador por dialeto, de modo que um banco novo é um adaptador novo (mapa de tipos, sintaxe de identidade, de comentário e de separador), não uma revisão do dicionário.

**Regras que o dicionário exige e que os bancos não garantem igual.** Ficam na camada de integração, e não no código dos módulos:

| Assunto | Diferença entre bancos | O que a camada assume |
|---|---|---|
| Vigência (294 entidades) | Nenhum dos dois bancos impede, de forma portável, janelas que se sobrepõem para a mesma chave de negócio; só o CHECK de fim >= início e a unicidade de (chave, início) entram no DDL | A camada oferece a operação "vigente na data D" e a de gravar um período novo (encerrar o anterior, validar sobreposição); nenhum módulo escreve essa consulta à mão |
| Referência genérica (61 campos) | Sem chave estrangeira em nenhum banco; o par tipo + identificador não tem integridade declarativa | A camada valida o tipo e a existência do registro de destino na gravação |
| Chave gerada | SQL Server devolve a chave por OUTPUT INSERTED ou SCOPE_IDENTITY; PostgreSQL, por RETURNING | Uma única operação "inserir e devolver o identificador" |
| Unicidade com valores vazios | Em UNIQUE, o SQL Server trata dois vazios como iguais; o PostgreSQL aceita vários | Os campos "— identidade" são obrigatórios no dicionário; qualquer outra unicidade opcional é regra da camada |
| Texto: maiúsculas, acentos e ordenação | A ordenação do SQL Server depende da collation do banco (em geral ignora maiúsculas e acentos); a do PostgreSQL diferencia por padrão | Definir e testar a ordenação por tipo de campo (código x nome); a camada normaliza a comparação |
| Data e hora, fuso | datetimeoffset no SQL Server; timestamptz no PostgreSQL | Gravar sempre em UTC e converter na borda; competência é sempre o primeiro dia do mês |
| Concorrência otimista | rowversion no SQL Server; sem equivalente direto no PostgreSQL | Coluna de controle de versão tratada pela camada |
| Inserir ou atualizar, paginação, funções de data | MERGE e OFFSET/FETCH no SQL Server; ON CONFLICT e LIMIT no PostgreSQL | Operações da camada, sem SQL nativo nos módulos |
| Tamanho de nomes | 128 contra 63 caracteres | O gerador usa o menor limite como alerta; hoje nenhum nome passa de 63 |
| Comentários de coluna | Propriedade estendida contra COMMENT ON | Gerados pelo adaptador a partir da descrição do dicionário |

**Regras de uso para os módulos** (proposta, para decisão em D-12): nenhum SQL fora da camada; nenhuma função nativa de um banco; os módulos enxergam só os tipos lógicos do dicionário; migrações são geradas por dialeto a partir do dicionário e versionadas; e a camada tem uma bateria de testes de contrato que roda contra cada banco suportado, porque é isso que prova a independência prometida. O PostgreSQL já faz esse papel de segundo banco: a mesma estrutura foi executada nele.

**Pilha definida (04/10/2026): back-end em C# e front-end em React.** O React fala só com a API do back-end e nunca com o banco, então não entra na camada de integração; a camada é uma biblioteca C# (.NET) usada pelos módulos do back-end. Tipos lógicos do dicionário e o tipo C# correspondente (proposta):

| Tipo lógico | Tipo em C# |
|---|---|
| identificador, referência | long (chave de referência opcional: long?) |
| código (n), texto, texto (n) | string |
| número (valor, quantidade, percentual) | decimal; inteiro como int |
| data, hora, data/hora | DateOnly, TimeOnly, DateTimeOffset (UTC) |
| competência | tipo próprio Competencia (envolve DateOnly sempre no dia 1) |
| booleano | bool |
| enumeração | enum de C# (valores do dicionário em snake_case, convertidos na camada) ou string validada |
| referência genérica | par (tipo, identificador) validado pela camada |

**Proposta de framework (para decisão em D-12).** (a) Uma biblioteca própria de acesso a dados, fina, com interfaces de repositório e de consulta (incluindo "vigente na data D" e "gravar novo período"), que é a única que os módulos enxergam. (b) Por baixo, o Entity Framework Core com o provedor de cada banco (SQL Server primeiro; Npgsql para PostgreSQL), mais SQL escrito à mão só dentro de adaptadores por dialeto, nos casos de desempenho (por exemplo, fechamento de folha e apuração fiscal). (c) As classes de entidade e o mapeamento são gerados do dicionário, da mesma fonte do DDL, para os dois não divergirem. (d) O DDL gerado do dicionário é a fonte do esquema; as migrações do Entity Framework não são usadas para criar tabelas. Alternativas: Dapper com adaptadores por dialeto (mais controle de SQL, mais código para escrever) ou camada inteiramente própria sobre ADO.NET (máxima independência, maior custo). A recomendação é (a) a (d) porque a independência de banco fica na biblioteca própria, e o Entity Framework Core cuida do que é comum entre os bancos.

# 6. Ordem técnica e ordem de negócio

A ordem das ondas é a mais antiga possível, e não a mais urgente. Os prazos legais já registrados nas pendências são:

| Data | O que é | Onde mexe |
|---|---|---|
| 26/10/2026 | Pacote XSD do eSocial; ajustes de outubro da NT 07/2026 (infoMesmoMtv e outros) | Folha & RH (onda 6) |
| 23/11/2026 | Horas do tempo parcial e jornada 12x36 (NT 07/2026) | Folha & RH (onda 6) |
| 01/12/2026 | Códigos de incidência do Anexo I da NT 07/2026 | Folha & RH (onda 6), Cad_Rh_Codigo_Incidencia |
| 14/12/2026 | Início dos códigos de incidência 23 e seguintes (P-39, a data mais conservadora) | Folha & RH (onda 6) |
| 2027-01 | Campos do eSocial com vigência a partir de 2027-01 (P-28), e a transição tributária IBS/CBS no cadastro de classificação (Cad_Cclasstrib) | Folha & RH (onda 6); Contabilidade & Fiscal (onda 3) |

Na ordem técnica, a Folha & RH, que concentra as datas mais próximas, é a penúltima onda. Isso vem da regra de agrupar por módulo, não de uma dependência real: calculando o fecho das chaves estrangeiras **obrigatórias**, Folha & RH precisa, além da Fase 0, de apenas duas entidades de fora dela, ambas de Jurídico. Contabilidade & Fiscal, depois da revisão 3, precisa de muito mais: as notas fiscais, o título e a baixa, o estoque e o lote, o contrato de gestão, o certificado digital e o processo, porque as entidades fiscais novas apontam para elas (lista abaixo); a revisão 5 tirou a procuração (Jurídico), que deixou de ser obrigatória na configuração do Integra Contador (D-N135), e acrescentou à parte da Fase 0 a autoridade fiscal, as suas credenciais e o driver de DF-e (Mov_Cbs_Solicitacao os exige), que já estão na onda 0; o corte mínimo da Contabilidade & Fiscal deixou de ser pequeno. Por isso existe a alternativa de **corte mínimo**, útil se a prioridade for cumprir os prazos de dezembro:

- Folha & RH: Fase 0 (onda 0) mais Cad_Processo, Mov_Processo_Suspensao, depois a onda 6. As chaves opcionais para os demais módulos esperam (seção 3.1).
- Contabilidade & Fiscal: Fase 0 mais Cad_Certificado_Digital, Cad_Gestao_Contrato, Cad_Local_Estoque, Cad_Lote_Produto, Cad_Processo, Mov_Inventario, Mov_Inventario_Item, Mov_Nota_Fiscal_Entrada, Mov_Nota_Fiscal_Entrada_Item, Mov_Nota_Fiscal_Saida, Mov_Nota_Fiscal_Saida_Item, Mov_Processo_Suspensao, Mov_Titulo, Mov_Titulo_Baixa, depois a onda 3.

Cad_Processo e Mov_Processo_Suspensao fazem parte da onda 2 (Jurídico). O corte mínimo cria só o necessário dessas tabelas e deixa o restante do módulo para depois, o que obriga a separar o arquivo da onda 2 por entidade e a manter duas rotas de implantação. Não está feito; é trabalho a acrescentar se você escolher essa rota.

A escolha entre ordem técnica completa e corte mínimo é a decisão D-2.

# 7. Tabelas oficiais a carregar

69 entidades têm um campo de código marcado como identidade: 30 nos Motores Transversais (entre elas Cad_Classe_Sistema, Cad_Pais, Cad_Estado, Cad_Municipio, Cad_CFOP, Cad_Moeda, Cad_NBS, Cad_CNAE, Cad_Cst, Cad_Cclasstrib, Cad_Cest e Cad_Tabela_Oficial), 36 em Contabilidade & Fiscal (a maioria vinda das tabelas externas do SPED, documento 43), 2 em Folha & RH (Cad_Rh_Verba, Cad_Rh_Codigo_Incidencia e Cad_Rh_Lotacao_Tributaria) e 1 em Jurídico (Cad_Processo, que é o número do processo e não uma tabela oficial). As outras 68 precisam de carga inicial. Revisão 17: a ECF entra em Cad_Obrigacao_Leiaute_Versao (leiaute 12, COD_VER 0012) e traz duas cargas novas, provisórias até o contador validar (D-N320 e D-N321): o leiaute (registros e campos, extraído do manual) e as 78 tabelas dinâmicas (27.842 linhas da planilha de 24/09/2026); as duas entram na onda 3 e foram geradas em 20/10/2026 como arquivos CSV, ainda fora do banco (leiaute: 1 versão, 188 registros e 1.122 campos; tabelas dinâmicas: 18 planos, 12.744 contas de plano, 78 tabelas, 4.475 linhas e 904 relacionamentos da Parte B), com as pendências em arquivos próprios. A carga usa o mecanismo de Cad_Tabela_Oficial e Mov_Carga_Tabela_Oficial (Bloco 2). Revisão 21: a tabela de naturezas da operação cambial da ECF (arquivo da versão 9, 599 códigos e 675 versões, 139 vigentes em 31/12/2026) entra na onda 3, em Cad_Natureza_Operacao_Cambial, e foi inserida no PostgreSQL de teste sem erro; a conferência é do contador. Sem ela, nenhuma tabela que referencia esses códigos recebe dados, mesmo com o DDL no lugar; por isso a carga faz parte da onda de cada módulo e não é um item à parte. Revisão 18 (D-N327): na carga das tabelas dinâmicas, cada aba de plano referencial traz o segmento, a forma de tributação e a finalidade (22 abas, conferidas contra a matriz do documento 91) e o plano sai sem segmento; as duas pendências de plano compartilhado por segmentos diferentes foram resolvidas (Pendencias_Carga passou de 31 para 29 linhas); o pacote foi regerado. Revisão 19 (D-N338 e D-N333): a carga ganhou a vigência própria do plano (Cad_Plano_Referencial, início 2025-01-01 e fim 9999-12-31) e o segmento nas nove abas de linhas M300, M350 e N630 nas variantes A, B e C; o resto é idêntico. Duas cargas novas, provisórias, saem da revisão 19, ambas na onda 3 e na onda 6: a lista legal por NCM e NBS e a depreciação do decreto (cerca de mil e 258 linhas, do texto que Alberto colou; os Anexos I a XV da LC 214 não vieram) e o catálogo de ocorrências do eSocial (só o "já existe" que o manual confirmar).

# 8. Bloqueios externos por módulo

Nenhuma pendência do documento 26 impede criar as tabelas; todas têm tratamento provisório. Elas condicionam a **carga** e a **lógica**:

| Onda | Pendências | Quem resolve |
|---|---|---|
| 3 (Contabilidade & Fiscal) | P-01 a P-06, P-08, P-09 (primeiro XML real da DCTFWeb); P-10 a P-14, P-31, P-32 (contador); P-20 a P-24 (material externo) | Primeiro XML real; contador |
| 6 (Folha & RH) | P-38 a P-42 (NT 07/2026; P-42, regra do horista, aberta); P-41 (migração da unidade de pagamento do salário); P-24 | RH e contador |
| 0 / transversal | P-18 (Integra Contador), P-19 (formato dos diagramas), P-15 a P-17 e P-33 a P-37 (decididas em 01/10/2026, aguardam sua confirmação) | Alberto |
| Equipe | P-29 e P-30 (limpeza e envio dos arquivos ao Projeto) | Equipe |

P-25 a P-27 são limites de escopo assumidos e não bloqueiam nada.

# 9. Decisões para o Alberto

Uma decisão já está tomada (D-1). As demais não alteram o dicionário; D-9 pede só que o dicionário passe a declarar tamanho de texto em quatro campos-chave.

| Código | Decisão | Situação ou recomendação |
|---|---|---|
| D-1 | Banco de dados | **Decidido (04/10/2026): SQL Server**, com uma camada de integração que isole o banco. O DDL é gerado em T-SQL e em PostgreSQL 16 (seção 4) |
| D-2 | Ordem de implementação: técnica completa (ondas 0 a 7) ou corte mínimo para os prazos de dezembro (Fase 0, Folha & RH, mais as duas entidades de Jurídico de que ela depende; Contabilidade & Fiscal e comerciais depois) | Corte mínimo se os prazos da NT 07/2026 valem para a Mlegate; ordem técnica completa caso contrário |
| D-3 | Identificador: bigint sequencial (como no DDL) ou uuid | bigint, por tamanho de índice e legibilidade; uuid só se houver integração com sistemas externos que gerem a chave |
| D-4 | Competência como date com CHECK de primeiro dia do mês, ou como inteiro AAAAMM | date com CHECK |
| D-5 | Precisão numérica: o mapa por nome de campo (seção 4) é heurístico | Aprovar o mapa ou listar as exceções; a lista de campos por tipo sai do gerador |
| D-6 | Alvo alternativo (R-7 do documento 30) | **Resolvido (04/10/2026)**: nenhum campo aponta mais para duas entidades; os onze foram tratados no dicionário (documento 30) |
| D-7 | Partição das grandes tabelas de movimento (notas fiscais, itens de folha, remessa bancária) | Decidir com volume real; não afeta o dicionário |
| D-8 | Ferramenta de migração (versionamento dos arquivos de DDL) | Cada onda é uma migração, e os arquivos já têm a ordem; com C#, DbUp ou Flyway rodam os scripts por dialeto; as migrações do Entity Framework não seriam a fonte do esquema (seção 5) |
| D-9 | Texto sem tamanho em chave única: Cad_Imposto.Sigla, Cad_Dado_Sensivel.Entidade e Campo, Cad_Lgpd_Tratamento.Nome, Cad_Politica_Uso_Equipamento.Nome. O SQL Server não indexa nvarchar(max) | Declarar "texto (n)" nesses cinco campos no dicionário; o DDL já usa 200 caracteres. Mais geral: definir um tamanho padrão para "texto" de nomes e siglas (hoje é nvarchar(max), que não pode ser indexado nem pesquisado com eficiência) |
| D-10 | Linguagem e pilha do sistema | **Decidido (04/10/2026): C# no back-end e React no front-end** |
| D-12 | Framework de integração com o banco em C#, e as regras de uso da seção 5 (nenhum SQL fora da camada, nenhuma função nativa, testes de contrato contra cada banco) | Biblioteca própria sobre o Entity Framework Core com provedores por banco, entidades e mapeamento gerados do dicionário (seção 5, a a d); alternativas: Dapper ou ADO.NET puro |
| D-11 | Nvarchar ou varchar para texto no SQL Server: usei nvarchar para "texto" (aceita qualquer alfabeto, inclusive nomes de participantes estrangeiros) e varchar para "código" | Manter; custa o dobro de espaço em texto longo |

# 10. Como foi verificado

O gerador lê o modelo extraído do dicionário e escreve, por dialeto, os oito arquivos de onda e o de comentários. **PostgreSQL 16:** os arquivos foram executados em ordem numa instância nova, sem erro: 1442 tabelas, 3798 chaves estrangeiras, 3889 índices (explícitos) e 11519 comentários. **SQL Server:** o ambiente desta sessão não tem uma instância do SQL Server; os 20.649 comandos do T-SQL (18.595 na revisão 32, 18.599 na 33, mais 535 na revisão 34, mais 45 na revisão 35, mais 140 na revisão 36 mais 248 na revisão 37, mais 278 na revisão 38, mais 177 na revisão 39 e mais 627 na revisão 40: 32 tabelas, 98 chaves estrangeiras, 98 índices e 399 comentários) foram lidos por um analisador de sintaxe T-SQL (sqlglot) sem erro, e o limite de largura de chaves e de índices foi verificado por programa (seção 4). Isso **não** equivale a executar. A primeira execução do DDL num SQL Server deve ser feita pela equipe, onda por onda, antes de qualquer outro trabalho sobre ele; como a estrutura é a mesma que já rodou no PostgreSQL, o risco está em sintaxe e em limites do T-SQL, não na ordem das ondas. O teste cobre sintaxe, ordem e consistência das referências, não volume nem desempenho; o dicionário não define unicidades além das marcadas "— identidade", então o banco ainda aceita duplicidades que a camada de integração deverá impedir.

Alertas do gerador: 7 (campos de texto sem tamanho em chave única, limitados a 200 pelo gerador, decisão D-9; o texto anterior deste documento dizia cinco e o gerador acusa sete, um deles novo na revisão 38: Cad_Parametro_Efeito_Obrigacao.Quando_Valor; declarar texto (n) nos sete é decisão sua). Nenhum nome passa de 63 caracteres, e nenhum campo aponta para duas entidades.

