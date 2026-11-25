# Consolidação da Revisão 47 — Documento 229

*Relatório do que entrou no dicionário com o seu "consolidar" de 16/11/2026, depois de aprovar as Q227-1 a Q227-5 ("sim para todas") e de pedir a leitura da NT 010. O escopo é o desenho do documento 227 como você o aprovou; as Q226-1 a Q226-5 (não aprovadas) e o que o documento 227 só sugeriu ficaram de fora.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 46** | **Revisão 47** | **Diferença** |
|---|---|---|---|
| Entidades | 1.239 | 1.240 | +1 (`Mov_Nfse_Via_Passagem`) |
| Campos | 14.365 | 14.398 | +33 (21 na entidade nova e 12 em 4 entidades existentes) |
| Campos de referência (FK) | 3.682 | 3.691 | +9 (7 na entidade nova, `ID_Procuracao` e `ID_Motivo_Desoneracao_St`) |
| Entidades mestres | 266 | 266 | 0 (a entidade nova é movimento) |
| Referências genéricas | 63 | 63 | 0 |
| Domínios de `Cad_Classe_Sistema` | 370 | 373 | +3 |
| Tabelas físicas (DDL) | 1.505 | 1.506 | +1 |
| Chaves estrangeiras (DDL) | 3.948 | 3.957 | +9 |
| Índices (DDL) | 4.039 | 4.048 | +9 |
| Comentários (DDL) | 12.105 | 12.137 | +32 |
| Comandos do T-SQL | 21.598 | 21.649 | +51 |
| Chaves opcionais que esperam a onda de destino | 85 | 86 | +1 (`Mov_Dfe_Distribuicao.ID_Procuracao`, que espera `Cad_Procuracao`) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos |  | Fase 0 93, Contabilidade & Fiscal 65, CRM & Vendas 27 (Compras segue em 31) |  |

Foram tocadas **7 entidades**: 1 nova e 6 existentes. Das existentes, 4 ganharam campos (`Mov_Dfe_Distribuicao` 3, `Mov_Dfe_Evento` 1, `Mov_Nota_Fiscal_Saida_Item` 2 e `Mov_Apuracao_Tributo_Item` 6), `Cad_Indicador_Operacao` só mudou o texto de `Aplica_Nfse_Via` e `Cad_Classe_Sistema` ganhou 3 domínios. Quatro campos existentes receberam texto novo (`Mov_Dfe_Evento.ID_Tipo_Evento`, `Mov_Dfe_Evento.Codigo_Motivo`, `Mov_Dfe_Distribuicao.Ultimo_Nsu` e `Cad_Indicador_Operacao.Aplica_Nfse_Via`). Nenhum campo perdeu texto.

# 2. O que entrou

**NFS-e Via, lado do adquirente (Q227-1).** A entidade nova `Mov_Nfse_Via_Passagem` (Contabilidade & Fiscal, sem vigência, 21 campos e 7 referências) é a extensão 1:1 de `Mov_Documento_Fiscal` com o que é próprio da passagem em praça de pedágio: placa, categoria do veículo, sentido em graus, código de acesso, modalidades de passagem e de pagamento, contrato, praça (código, nome, quilômetro e município), trecho, data e hora da passagem, situação (normal, substituição, decisão judicial) e o motivo da substituição. O veículo da empresa é achado pela placa (`ID_Veiculo_Transporte`, opcional), que permite apropriar o pedágio por veículo e por ativo. Os valores de ISSQN, PIS, COFINS, IBS e CBS entram pelo item e pela apuração do item, sem entidade nova. Entram 3 domínios abertos: `categoria_veiculo_via` (14 valores, 00 a 12 e 99), `modalidade_passagem_via` (5) e `modalidade_pagamento_via` (6, com o valor 6 "sem cobrança" da NT 010). O texto "fora do escopo" saiu de `Cad_Indicador_Operacao.Aplica_Nfse_Via`. **Emitir** NFS-e Via, o papel da concessionária, continua fora.

**Consulta do ADN por procuração (Q227-2).** `Mov_Dfe_Distribuicao` ganha `Documento_Consulta` (CNPJ ou CPF da inscrição consultada; vazio = o titular do certificado), `Tipo_Consulta` (inscricao_certificado, cnpj_base ou procuracao, como o ADN v1.1 devolve em `TipoConsulta`) e `ID_Procuracao` (o mesmo `Cad_Procuracao` do Integra Contador). Com isso o NSU de duas inscrições não se mistura: o texto de `Ultimo_Nsu` agora diz que o NSU vale por inscrição consultada.

**Manifestação do adquirente (Q227-3).** `Mov_Dfe_Evento` ganha `Nome_Autor_Informado` (o `xRazaoSocial` da manifestação, de 2 a 60 caracteres); o tipo de identificação se deduz do tamanho de `Documento_Autor`. Os textos de `ID_Tipo_Evento` e `Codigo_Motivo` registram os códigos 203202 e 203204 e os motivos da NFS-e Via.

**NT 2020.005 (Q227-4).** Oito campos novos, todos opcionais e com descrição completa: `Codigo_Barras_Comercial` e `Codigo_Barras_Tributavel` (código de 3 a 30 caracteres que não é GTIN) em `Mov_Nota_Fiscal_Saida_Item`; e, em `Mov_Apuracao_Tributo_Item`, `Valor_Desonerado_St` e `ID_Motivo_Desoneracao_St` (ICMS-ST desonerado, que reaproveita o domínio `motivo_desoneracao_icms`), `Percentual_Fcp_Diferido`, `Valor_Fcp_Diferido`, `Valor_Fcp_Efetivo` (grupo 51) e `Compoe_Total_Documento` (se o PIS-ST ou a COFINS-ST compõe o total da nota).

**Q227-5** não muda o dicionário: a consulta ao Comitê Gestor é o documento 228 (Q228-1).

**Módulos tocados:** 01 (Fase 0, revisão 93), 05 (CRM & Vendas, revisão 27) e 10 (Contabilidade & Fiscal, revisão 65, com o anexo 59 da entidade nova).

# 3. Cargas de partida (`Carga47-20261116`)

A pasta (e o zip de mesmo nome, com LEIA-ME e ordem de carga) traz **só as linhas a incluir**, com a chave de negócio, CSV com BOM e separador ";". Tudo provisório.

| **Arquivo** | **Linhas** | **Observação** |
|---|---|---|
| `Cad_Classe_Sistema_NFSe_Via_27_valores` | 27 | 14 + 5 + 6 valores dos três domínios novos e os 2 valores novos de `tipo_evento_dfe` (203202 e 203204); textos do schema v1.01, com "(ou Pix, texto da NT 010)" no valor 1 do pagamento |
| `Cad_Dfe_Evento_Tipo_NFSE_VIA` | 4 | 101101, 105102, 203202 e 203204 no modelo `NFSE_VIA` (que já entrou na `Carga45`); eventos assinados, como o schema |
| `Cad_Dfe_Evento_Motivo_NFSE_VIA` | 11 | cancelamento 2 (serviço não prestado), substituição 1 (erro na emissão), rejeição 1 a 8 e 99 |
| `Cad_Dfe_Codigo_Retorno_ADN` | 15 | os 15 códigos da seção 1.1.2 do Manual do ADN v1.1, com o texto oficial; conferir quais já existem |

Total: **57 linhas de dados** em 4 arquivos (com LEIA-ME).

# 4. Leituras minhas que aguardam a sua confirmação

1. **Eventos da NFS-e Via:** `Autor_Permitido` (emitente nos cancelamentos, tomador na manifestação), `Ambiente_Receptor` (adn), `Evento_Unico` e `Aplica_Prazo_Municipal` não vêm do schema nem da NT 010; são leitura minha. `Somente_Recepcao` (sim nos cancelamentos, que o adquirente só recebe) e `Efeito` seguem o texto do schema.
2. **Códigos do ADN:** a `Natureza` e a `Acao_Padrao` de cada um dos 15 códigos e o código de negócio da autoridade ("ADN") são leitura minha; o texto é o oficial.
3. **Vigência:** 01/01/2026 nos valores e eventos (não li a data de produção do leiaute 1.01) e 03/11/2026 nos códigos do ADN (data do manual).
4. **`Compoe_Total_Documento`:** a marca vale na linha de PIS ou de COFINS com ST (o campo único substitui `indSomaPISST` e `indSomaCOFINSST`, que o leiaute separa por tributo); a leitura é minha.
5. **`ID_Motivo_Desoneracao_St`:** reaproveita o domínio do ICMS próprio; os valores que a NT aceita para o ST não foram conferidos um a um.
6. **1:1 da passagem:** `Mov_Nfse_Via_Passagem.ID_Documento_Fiscal` leva a marca "1:1" no texto, como as demais extensões; o dicionário não gera constraint de unicidade além das marcadas "identidade".

# 5. O que ficou de fora

- **Q229-1 (nova):** o código de barras só entrou no item da nota de **saída**, como o documento 227 propôs; `Mov_Nota_Fiscal_Entrada_Item` e `Cad_Produto_Servico_Dados_Produto` também têm `Gtin` e `Gtin_Tributavel` e não receberam os 2 campos.
- **Q229-2 (nova):** o valor "recibo de passagem veicular" em `Origem_Dados_Entrada` era leitura minha e não foi aprovado.
- **Regras de validação da NT 2020.005** (rejeições novas): vão para `Cad_Dfe_Parametro_Regra` quando a emissão da NF-e for desenhada; não foram comparadas uma a uma.
- **NFS-e Via:** prazo da manifestação, efeito da falta de manifestação, regra da chave, erros e cronograma dependem do Manual v1.02 e do Anexo IV, que não li; a C362 (crédito do pedágio) segue com o contador.
- **Q226-1 a Q226-5:** não aprovadas; ficam como estavam.

# 6. Como conferi

| **Conferência** | **Resultado** |
|---|---|
| Contagem contra o previsto no documento 227 | 1.240 entidades; 14.365 + 33 = **14.398** campos; 3.691 referências; 266 mestres; 373 domínios; 1.506 tabelas no DDL |
| Auditoria sobre os Markdown regerados | 0 achados em aberto |
| DDL no PostgreSQL 16 (instância nova, oito ondas e comentários, em ordem) | Sem erro: 1.506 tabelas, 3.957 chaves estrangeiras e 12.137 comentários |
| T-SQL (contagem e leitura) | 21.649 comandos lidos por um analisador de T-SQL, 0 erros. **Não foi executado num SQL Server** (o ambiente não tem uma instância) |
| Ondas | `Mov_Nfse_Via_Passagem` fica na onda 3; as 81 entidades empurradas não mudam; entre as chaves opcionais que esperam a onda de destino entra uma linha (`Mov_Dfe_Distribuicao.ID_Procuracao`, onda 0 para a 2), e nenhuma linha anterior mudou (quadros 2.2 e 3.1 do documento 31 comparados) |
| Fontes lidas de novo na consolidação | Schemas da NFS-e Via v1.01 (domínios, motivos de evento, assinatura) e Manual do ADN v1.1, seção 1.1.2 (textos dos erros) |
| Documentos 29, 31, 14, 38, 188 e 227 | Totais e quadros do documento 31 regerados do modelo; 227 ganhou a revisão 3 com as correções; 38 ganhou as Q228-2, Q229-1 e Q229-2 |
| Modelo entidade-relacional e diagramas | Regerados |

# 7. O que continua aberto

- **Você:** Q226-1 a Q226-5; Q228-1 e Q228-2 (consulta ao Comitê Gestor); Q229-1 e Q229-2; a definição de **DIR** (Q221-5); a Q218-8 (só o Ajuste SINIEF 14/2025 e o 01/92); a Q215-5; a Q206-10; a Q209-9 (parte 2); a Q198-12; a Q159-E1; as Q179-1 e Q179-3; as Q160-8 e Q160-9; e o envio do Manual v1.02 e do Anexo IV da NFS-e Via.
- **Contador:** C1 a C362 do documento 188 (a C362, crédito do pedágio, segue aberta).
- **Equipe e fontes oficiais:** Q218-E1 a Q218-E9 e a seção 3 do documento 38.
- **Fila de desenho (minha):** o split payment (adiado por você) e a carga da lista de autopeças não produzidas (espera a Q206-10).

# 8. Limites

- **A NFS-e Via vem dos schemas, da NT 010 e do Manual v1.0 do portal**; sem o Manual v1.02 e o Anexo IV o desenho é provisório.
- **O erro E2243 do ADN v1.1** tem texto que não combina com a consulta por procuração de outra raiz descrita no mesmo manual; a carga leva o texto oficial (Q228-2).
- **Nada foi validado num SQL Server;** o T-SQL foi só lido por um analisador.
- **A NT 2020.005 não foi comparada com a planilha do documento 34** (que não está neste ambiente); a conferência foi por nome de campo no modelo.
- O Project continua acima do limite de tamanho (a gravação dos documentos 224, 226, 227, 188 e 229 pode ser recusada), e a documentação completa é mantida na pasta `Documentacao-ERP-completa`.
