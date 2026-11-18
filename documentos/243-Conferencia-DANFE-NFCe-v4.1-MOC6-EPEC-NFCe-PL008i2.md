# Conferência do DANFE NFC-e v4.1, do MOC 6.0, do EPEC da NFC-e e do PL_008i2 — Documento 243

*Você escreveu "Q232-9 sim correto" e enviou quatro arquivos; depois lembrou que **os esquemas da NFC-e já estavam nos pacotes que você mandou**. Você tem razão, e eu errei no documento 241 (seção 2). Propostas de ajuste, **nada foi aplicado ao dicionário** (revisão 53); ele só muda depois do seu "consolidar".*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

1. **Q232-9: registrada como "sim"** (D-N623). Vale o esquema, não a planilha de 50 códigos: o catálogo continua com os 44 tipos de evento dos esquemas, e os códigos 420110 a 420170 ficam fora da lista de emissão até existir uma Nota Técnica para eles. A pergunta sai do documento 38.
2. **A Q241-1 caiu.** Pedi o "pacote da NFC-e" por engano: a NFC-e usa o mesmo esquema da NF-e (`leiauteNFe_v4.00.xsd`), e ele estava nos cinco pacotes que você enviou (PL_010d a PL_010h). A Q241-1 sai do documento 38.
3. **Dos quatro arquivos novos, três não mudam nada** e um traz **uma pergunta nova** (Q243-1, valor aproximado dos tributos, Lei 12.741). O DANFE NFC-e v4.1 (dez/2016), o MOC 6.0 (set/2015) e o PL_008i2 (NF-e 3.10, 2015) são versões históricas, superadas pelo que o dicionário já usa; o pacote EPEC da NFC-e é **byte a byte igual** ao que você já tinha enviado (conferi o hash).
4. **Estrutura proposta: 1 campo** (se você disser "sim" à Q243-1). Nenhuma entidade nova.

# 2. Correção do documento 241: a NFC-e estava nos pacotes

No documento 241 escrevi que "a PL_010g e a PL_010h só aceitam `mod` = 55" e concluí que o pacote da NFC-e não tinha vindo. Reli os esquemas:

| Onde | `TMod` (modelo do documento) |
|---|---|
| `NFe/tiposBasico_v4.00.xsd`, nas cinco versões (PL_010d v1.03, 010e v1.02, 010f v1.04, 010g v1.03 e 010h v1.03) | **55 e 65** |
| `Evento/tiposBasico_v1.03.xsd` (010d, 010g e 010h) | só 55 |

O arquivo de 1.03 é o dos **eventos** (cancelamento 110001, 110300 etc., que na PL_010g e na PL_010h importam esse tipo), e foi ele que li. A documentação do `ide/mod` no `leiauteNFe_v4.00.xsd` diz "55 = NF-e; 65 = NFC-e" nas cinco versões. Portanto:

- o leiaute da NFC-e (QR Code, `gPgtoVinc`, IBS e CBS) **foi conferido no documento 34** (923 campos de NF-e **e NFC-e**, pacote PL_010f) e a decisão D-N23 já o trata como a mesma estrutura de nota, com a diferença no motor de emissão;
- a Q241-1 estava errada e **não vale mais**; o texto do documento 241 que a cita fica como histórico, e o documento 38 deixa de mostrá-la.

O pacote do seu link (PL_010e v1.02, com as NT 2025.002, 2026.002 e 2026.003) é um dos cinco que li.

# 3. O que chegou

| Arquivo | O que é | Resultado |
|---|---|---|
| Manual de Especificações Técnicas do DANFE NFC-e e QR Code, **versão 4.1 (dez/2016)** | Divisões I a IX do DANFE NFC-e, QR Code de **versão 1 (`nVersao` = 100)**, consulta pública e códigos de retorno | Histórico. O dicionário já parte do QR Code 2.00 e 3 (documento 34, P-16) e do DANFE Tipo 2 (NT 2026.003). Seção 4 |
| Manual de Orientação do Contribuinte (MOC) **v6.0, set/2015** (299 páginas) | MOC da NF-e 3.10 | Superado pelo MOC 7.0 (nov/2020), que é a base das regras (documento 232). Sem efeito |
| `Evento_EPEC_NFCe_PL1.00` | Esquema do EPEC da NFC-e (110140) | **Idêntico** ao já recebido (mesmo hash). Seção 5 |
| `PL_008i2_CFOP_EXTERNO` | Pacote da NF-e **3.10** (NT 2015.002 e 2015.003) em que a lista de CFOP deixa de ser enumeração no esquema | Histórico. Seção 6 |

# 4. DANFE NFC-e v4.1 contra o dicionário

O manual descreve o que se imprime. Quase tudo sai de campos que o dicionário já guarda, ou é regra de impressão (do emissor de DANFE, não do cadastro):

| Item do manual | Onde está no dicionário | Situação |
|---|---|---|
| Chave, número, série, data de emissão, protocolo e data de autorização | `Mov_Documento_Fiscal` e `Mov_Nota_Fiscal_Saida` | Coberto |
| Itens, quantidade, valor unitário e valor total | `Mov_Nota_Fiscal_Saida_Item` | Coberto |
| Valor total, desconto e acréscimos, valor a pagar | Derivados dos itens | Derivado |
| Forma de pagamento, valor pago e **troco** | `Mov_Nota_Fiscal_Saida_Pagamento` (`Valor_Troco` já existe) | Coberto |
| Identificação do consumidor (CPF, CNPJ, estrangeiro, nome, endereço de entrega) | `Mov_Nota_Fiscal_Saida.Documento_Consumidor` e `Nome_Consumidor`; endereço de entrega em `Mov_Nota_Fiscal_Saida_Local` | Coberto |
| "CONSUMIDOR NÃO IDENTIFICADO", limite de R$ 10.000 sem identificação (hoje por UF) | Texto fixo do DANFE; limite como parâmetro com vigência (documento 34, P-16) | Coberto |
| "EMITIDA EM CONTINGÊNCIA — Pendente de autorização", "EMITIDA EM AMBIENTE DE HOMOLOGAÇÃO — SEM VALOR FISCAL", "Via do Estabelecimento" | Regra de impressão por `Tipo_Emissao` e `Ambiente` | Derivado |
| Segunda via do DANFE em contingência ou guarda eletrônica do XML por termo no livro de ocorrências | A guarda do XML está em `Mov_Documento_Fiscal`; a opção é regra de UF | Sem campo novo |
| Consulta pela chave e QR Code | `Cad_Autoridade_Fiscal_Servico` (endereços) e `Mov_Documento_Fiscal.Url_Qrcode` (calculada) | Coberto |
| QR Code **versão 1** (`nVersao` 100; CSC de 16 a 36 posições, `cIdToken` de 6, hash SHA-1) | `Cad_Dfe_Leiaute.Versao_Qrcode` (texto cita 2.00 e 3), `Identificador_Csc` e `Referencia_Cofre_Csc` | Histórico; ver abaixo |
| Códigos de retorno da consulta pública e do QR Code (100 a 104, 220 a 232, 247…) | `Cad_Dfe_Codigo_Retorno`; **são os da consulta do consumidor, que a SEFAZ responde** | Sem efeito (o ERP não presta esse serviço) |
| **Valor aproximado dos tributos (Lei 12.741)**, por item e no total | O documento 34 e o 42 (Q-16) o trataram como **derivado**; a NFS-e guarda (`Mov_Nfse_Rps.Valor_Carga_Tributaria`) | **Pergunta Q243-1** |

**QR Code versão 1.** O dicionário não precisa dela: o ERP só emite NFC-e com a versão vigente (3). Se algum dia importarmos histórico, o texto de `Versao_Qrcode` ganharia a menção "100 (versão 1, até 2018)". **Recomendo não mexer agora.**

## Q243-1: guardar o valor aproximado dos tributos (Lei 12.741)?

O esquema da NF-e e da NFC-e tem `vTotTrib` **no item** (`det/imposto/vTotTrib`) e **nos totais** (`ICMSTot/vTotTrib`), opcionais. O manual diz que esses campos têm "natureza declaratória pela empresa" e que **a SEFAZ não valida** a soma contra os tributos destacados: a lei pede a carga tributária total da cadeia (tabela tipo IBPT), não só os tributos da última etapa. Isso contraria a premissa de "derivado" dos documentos 34 e 42: **o valor não sai das linhas de tributo que o ERP já guarda**, vem de uma tabela externa que muda com o tempo. Para a NFS-e o dicionário já guarda o valor (`Valor_Carga_Tributaria`, `Percentual_Carga_Tributaria` e `Fonte_Carga_Tributaria`).

| Proposta | Detalhe |
|---|---|
| **+1 campo** em `Mov_Nota_Fiscal_Saida_Item` | `Valor_Tributos_Aproximados` (número, opcional): o `vTotTrib` do item, como foi declarado na emissão |
| Total | **Derivado** (soma dos itens), como já está |
| Fonte | O nome da fonte (por exemplo, IBPT) vai no texto de `Informacoes_Complementares`, que já existe; é onde a lei manda dizer |
| Tabela de alíquotas aproximadas por NCM e NBS | **Não criar agora.** Entra quando você disser de onde a Mlegate tira o número (tabela própria, contratada ou nenhuma) |

Efeito: **1 campo, 0 entidades**. Sem isso, a Mlegate imprime o valor (se quiser) mas o ERP não guarda o que declarou, e a reconstituição do XML autorizado (que já fica guardado) seria a única prova.

| Id | Pergunta | Recomendação |
|---|---|---|
| Q243-1 | Guardar o valor aproximado dos tributos do item (`vTotTrib`) em `Mov_Nota_Fiscal_Saida_Item` (1 campo), com o total derivado, e deixar a tabela de alíquotas aproximadas para quando você escolher a fonte? | **Sim.** É o único valor da NF-e/NFC-e que o ERP declara sem ter como recalcular |

# 5. EPEC da NFC-e

O esquema (`eventoEPEC_v0.01`, `tiposBasico_v3.10`) traz `cOrgaoAutor`, `tpAutor`, `verAplic`, `dhEmi`, `tpNF`, `IE` e o grupo `dest` com **UF, CNPJ ou CPF ou `idEstrangeiro`, `vNF` e `vICMS`** (sem `vST` e com o destinatário opcional, porque a NFC-e pode não identificar o consumidor). O evento **110140 já está em `tipo_evento_dfe`**, o `tpEmis` 4 já está em `Tipo_Emissao` e todos os campos do grupo saem da própria nota (destinatário, valor, ICMS) ou da filial (`cOrgaoAutor`). **Nada a mudar.**

# 6. MOC 6.0 e PL_008i2

O **MOC 6.0** (2015) descreve a NF-e 3.10 e as regras daquela época. As regras de validação que o dicionário usa vêm do MOC 7.0 e das NT posteriores (documentos 230 a 232). **Sem efeito.**

O **PL_008i2 "CFOP externo"** é o pacote em que o CFOP passa de enumeração a **padrão** (`[1,2,3,5,6,7]{1}[0-9]{3}`) e a lista de CFOP válidos fica numa tabela externa. É o mesmo desenho que o dicionário já adotou: a lista é carga com vigência (`Cad_CFOP`, com `Indicador_NFe` e `Indicador_Cte`), e a validade de cada CFOP por modelo vem da tabela oficial, não do esquema. **Sem efeito.**

# 7. Decisões para registrar

| Nº | Decisão | Origem |
|---|---|---|
| D-N623 | (a) **Q232-9: sim.** O esquema prevalece sobre a planilha de 50 códigos; o catálogo fica com os 44 tipos de evento; 420110 a 420170 fora da lista de emissão até existir NT. (b) **Q241-1 retirada**: a NFC-e já estava nos pacotes da NF-e (PL_010d a PL_010h). | "Q232-9 sim correto" e "nos esquemas que mandei tinha o da NFC-e", 18/11/2026 |

# 8. O que muda se você disser "sim" à Q243-1

| Medida | Revisão 53 | Depois |
|---|---|---|
| Entidades | 1.242 | 1.242 |
| Campos | 14.448 | **14.449** |
| Comentários do DDL | 12.189 | 12.190 |

Nada disso entra antes do seu "consolidar".
