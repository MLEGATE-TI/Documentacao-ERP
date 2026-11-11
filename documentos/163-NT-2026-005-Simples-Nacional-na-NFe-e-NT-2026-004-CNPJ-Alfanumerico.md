# NT 2026.005 (Simples Nacional na NF-e e NFC-e) e NT 2026.004 v1.00 (CNPJ alfanumérico) — Documento 163

> **Nada foi aplicado ao dicionário.** Ele continua na **revisão 28** (995 entidades, 10.844 campos). Este documento compara com o dicionário as duas notas técnicas que você enviou em 03/11/2026: a **NT 2026.005 v1.00** (outubro de 2026, "Reforma Tributária do Consumo – Simples Nacional", versão da NF-e e da NFC-e) e a **NT 2026.004 v1.00** (abril de 2026, "NFe/NFCE – CNPJ Alfanumérico"). Ele também **corrige o documento 161**, que só conhecia a NT 2026.005 por fonte secundária.

*Lidas por inteiro: NT 2026.005 v1.00 (12 páginas) e NT 2026.004 v1.00 da NF-e (14 páginas). Dicionário conferido pelo DDL e pelos comentários da revisão 28 e pelos documentos 34, 41, 42 e 50 do Projeto.*

Mlegate · Alberto Beyeler · 3 de novembro de 2026

# 1. Resumo

- **Há duas notas com o número 2026.004.** A que você enviou é a da **NF-e e da NFC-e** (CNPJ alfanumérico; a v1.00 é de abril de 2026 e, em 03/11/2026, você enviou também a **v1.01, de junho de 2026**: muda só a data de homologação e inclui o leiaute do serviço de inutilização, ver seção 4). A do Ato nº 10 é outra: a **NT 2026.004 v1.01 do RTC** (CT-e, CT-e OS, NFCom, BP-e, NF3e, NFAg e NFGas), que **continua sem chegar**.
- **NT 2026.004 v1.00 (CNPJ alfanumérico):** só muda o tipo dos campos de CNPJ e de chave de acesso nos schemas (de numérico para texto). **Nada muda no modelo de dados**, o que já constava no documento 34. Só confiro as datas (seção 6).
- **NT 2026.005 v1.00 (Simples Nacional):** cria dois campos novos (`tpRegimeIBSCBS` e `cAtivSN`), o grupo `gTribSN` no item e no total, quatro rejeições (1275, 1276, 1277 e 1284) e o **evento 412140** do fisco. **Produção em 16/11/2026** (testes até 26/10/2026); o evento fica para "implementação futura", sem data.
- **O dicionário cobre quase tudo.** O regime e a opção pendente do Simples já existem (`Cad_Simples_Opcao`, `Cad_Participante_Regime_Ibs_Cbs`, `excesso_sublimite` da filial); a atividade do Simples já está no produto e na NFS-e; o `gTribSN` do item cabe no complemento da apuração (`ibs_cbs_simples_nacional`, documento 41); `tpRBSN` já está no `Cad_Cclasstrib`.
- **Faltam duas coisas, as duas pequenas:** (1) o **item da NF-e de saída não guarda a atividade do Simples** (`cAtivSN`), **+1 campo**; (2) o **evento 412140**, que traz um detalhe por item, **+1 entidade de 11 campos**.
- **Contagem proposta: +1 entidade e +12 campos** (seção 7). A revisão 29 prevista passa a **1.005 entidades e 11.000 campos** (11.002 se você aprovar também as Q161-1 e Q161-2).

# 2. NT 2026.005 v1.00: o que ela traz

**Objetivo (seção 1).** Capturar, **por item** da nota, o que o Simples precisa para a receita bruta do Simples (RBSN), a receita acumulada de 12 meses (RBT12) e o IBS e a CBS do regime. Dos contribuintes ela exige informar: regime, atividade por item, classificação tributária e os valores de IBS e CBS do Simples.

| Item da NT | Tag | O que é |
|---|---|---|
| Regime de apuração do IBS/CBS do emitente | `tpRegimeIBSCBS` (C21a, grupo do emitente) | Valores 1 a 4. **Só** para o optante do Simples que escolheu o regime regular (1) e para o contribuinte do Regime Normal (CRT 3) com **opção pelo Simples indeferida e em discussão** (2, 3 e 4). Não se informa nos demais casos |
| Atividade do Simples por item | `cAtivSN` (I17d, 2 posições, item) | 01 e 02 (Anexo I), 03 e 04 (Anexo II, ZFM) e 90 (operação não tributável). Só para optante ou com opção pendente |
| Composição do IBS e da CBS do Simples, por item | `gTribSN` (UB115a): `gIBSSN` (`pIBSSN`, `vIBSSN`) e `gCBSSN` (`pCBSSN`, `vCBSSN`) | Alíquota efetiva e valor |
| Totais | `gTribSN` (W59h): `vIBSSN` e `vCBSSN` | Soma dos itens |
| Rejeições | 1275 e 1276 (grupo de totais ausente ou indevido), 1277 (total do IBS difere da soma), 1284 (total da CBS difere da soma) | |
| **Evento 412140** "Tributação do Simples Nacional" | `e412140_v1.00.xsd` | **Gerado pelo fisco** (autor 5 = Fisco), com a receita bruta, o tipo de receita, as alíquotas, os valores e os valores pendentes ou suspensos de **cada item** (até 990) e os totais. Cancela-se pelo evento genérico **110001** |
| Preenchimento por regime (seção 2.3) | tabela | Qual grupo informar (`gIBSCBS`, `gTribSN`) conforme o CRT e o regime regular |
| Devolução e retorno por recusa (seção 2.4) | regra | O grupo IBS/CBS do item é **espelho** do item da nota de fornecimento referenciada |

**Cronograma:** campos, **teste até 26/10/2026 e produção em 16/11/2026**; evento, "implementação futura" nos dois ambientes.

**Correção do documento 161.** Lá eu escrevi que a NT 2026.005 criava o "evento automático de conformidade (número não informado)" e que o Simples da NF-e entrava com o cronograma de 01/01/2027. Agora li a nota: o evento é o **412140**, e os campos entram em produção em **16/11/2026**. A frase "possível evento novo em `Mov_Dfe_Evento`" da seção 4 do documento 161 vira a Q163-3 abaixo.

# 3. O que o dicionário já cobre

| Pedido da NT | No dicionário | Situação |
|---|---|---|
| `tpRegimeIBSCBS` | **Derivável.** Situação do Simples e opção pendente em `Cad_Simples_Opcao_Versao.Situacao` (o valor `pendente` já atende `opSimpNac` = 4 da NFS-e); sublimite em `Cad_Filial_Perfil_Fiscal.Excesso_Sublimite` (define o CRT, junto com o regime do participante); regime regular em `Cad_Participante_Regime_Ibs_Cbs.Regime` (`hibrido`, `hibrido_somente_cbs`), com vigência | **Sem campo** (derivar, não guardar). Q163-1 |
| `cAtivSN` | A atividade do Simples está no produto (`Cad_Produto_Servico_Simples_Versao.ID_Atividade_Simples`) e na NFS-e (`Mov_Nfse_Dps.ID_Atividade_Simples`, códigos 07 a 14 e 90). **O item da NF-e de saída não tem o campo.** Os códigos **01 a 04** da NF-e não aparecem nos comentários | **Lacuna: +1 campo** (Q163-2) |
| `gTribSN` do item (`pIBSSN`, `vIBSSN`, `pCBSSN`, `vCBSSN`) | `Mov_Apuracao_Tributo_Item_Complemento`, tipo `ibs_cbs_simples_nacional` (`Percentual` e `Valor`, uma linha por tributo), do documento 41 | **Coberto** |
| `gTribSN` do total (`vIBSSN`, `vCBSSN`) | É a **soma dos itens** (rejeições 1277 e 1284) | **Derivado**, sem campo; as quatro rejeições entram como regra de validação do ERP (aviso antes da transmissão) |
| `tpRBSN` | `Cad_Cclasstrib_Versao.Tipo_Receita_Bruta_Sn`, que decide a receita bruta e o `gTribSN` | **Coberto.** Conferir os valores (o evento usa 0 a 5 e 9) |
| Evento 412140 | `Mov_Dfe_Evento` é genérica e aceita evento do fisco (`Papel_Autor` = `fisco`), mas **não há valor 412140 nem estrutura para o detalhe por item** | **Lacuna: +1 entidade** (Q163-3) |
| Cancelamento do evento pelo 110001 | `Mov_Dfe_Evento.ID_Dfe_Evento_Cancelado` já é a autorreferência dos cancelamentos de evento (110181, 110191, 110301 e 610111); o 110001 **não está na lista** | Acrescentar o 110001 ao texto e ao tipo de evento |
| Preenchimento por regime e espelho na devolução (seções 2.3 e 2.4) | O Motor decide o CST e o cClassTrib do item; **não há regra de espelho** na devolução | **Regra do Motor**, só texto (Q163-4) |

# 4. Lacunas e propostas

## 4.1 `cAtivSN` no item da NF-e de saída (Q163-2)

`Mov_Nota_Fiscal_Saida_Item` ganha **`ID_Atividade_Simples`** (referência ao domínio da atividade do Simples, **opcional**): sugerido pelo `Cad_Produto_Servico_Simples_Versao` do produto, confirmável pelo usuário, preenchido **só quando o emitente é optante do Simples ou tem a opção pendente** e vazio nos demais. Segue o padrão do `ID_Atividade_Presuncao` do item da nota (revisão 28). Os códigos **01 a 04 e 90** da NF-e entram como valores do domínio (carga); conferir se o domínio atual os tem.

## 4.2 Evento 412140 do fisco (Q163-3)

O evento chega pela distribuição de DF-e (o ERP **só registra**). O detalhe por item não cabe em `Mov_Dfe_Evento`; entra uma entidade filha, **`Mov_Dfe_Evento_Simples_Item`**, como `Mov_Dfe_Evento_Adquirente` já faz na NF-e ABI:

| Campo | Tipo lógico | Descrição / regra |
|---|---|---|
| **ID_Dfe_Evento_Simples_Item** | identificador | --- |
| **ID_Dfe_Evento** | referência (`Mov_Dfe_Evento`) | O evento 412140 a que a linha pertence |
| **Numero_Item** | número | `nItem`, 1 a 990 |
| **Valor_Receita_Bruta_Sn** | número | `vRBSNitem`: receita bruta do Simples atribuída ao item |
| **Tipo_Receita_Bruta_Sn** | código (1) | `tpRBSN`: 0 não é receita bruta; 1 interna; 2 interna sem cálculo de IBS e CBS; 3 exportação direta; 4 exportação indireta; 5 mercado interno e exportação; 9 fornecimento incompatível com o Simples. Mesmo domínio do `Cad_Cclasstrib_Versao` |
| **Percentual_Ibs_Sn** | número, opcional | `pIBSSN` |
| **Valor_Ibs_Sn** | número, opcional | `vIBSSN`: IBS devido pelo Simples |
| **Percentual_Cbs_Sn** | número, opcional | `pCBSSN` |
| **Valor_Cbs_Sn** | número, opcional | `vCBSSN`: CBS devida pelo Simples |
| **Valor_Ibs_Pendente_Suspenso** | número, opcional | `vIBSPendSusp` |
| **Valor_Cbs_Pendente_Suspenso** | número, opcional | `vCBSPendSusp` |

**11 campos.** Os totais do evento (`vRBSNtot`, `vIBSSNtot`, `vCBSSNtot` e os pendentes ou suspensos) **são somas dos itens** e não se guardam. O evento é **registrado e comparado**: o ERP compara os valores do fisco com os do item da nota (complemento `ibs_cbs_simples_nacional`) e **avisa** a diferença, sem recalcular e sem bloquear. Em `tipo_evento_dfe` entram os valores `412140` (Tributação do Simples Nacional) e `110001` (Cancelamento de Evento), se ainda não existirem. **Desenho provisório:** a nota diz "implementação futura", e o schema `e412140_v1.00.xsd` **não foi enviado**; confiro os nomes e tamanhos dos campos quando ele chegar.

## 4.3 Regras que ficam como texto (Q163-1 e Q163-4)

- **`tpRegimeIBSCBS` derivado** (Q163-1): 1 quando o emitente é optante (CRT 1 ou 2) **com** regime regular; 2, 3 e 4 só no contribuinte do Regime Normal (CRT 3) com opção pendente, pela combinação do CRT pendente (1 ou 2) com ter ou não o regime regular. **Leitura minha:** o CRT pendente (1 ou 2) sai do `Excesso_Sublimite` da filial.
- **Quais grupos informar** (seção 2.3 da NT, tabela por regime): o Motor passa a seguir a tabela. Optante **sem** regime regular informa `gIBSSN` e `gCBSSN` e **não** informa `gIBSCBS`; com regime regular informa `gIBSUF`, `gIBSMun` e `gCBS` e **não** informa `gTribSN`; o optante com excesso de sublimite sem regime regular informa os dois (com a CBS regular de alíquota zerada) e o `gCBSSN`. **CST 620** (monofásica de combustíveis): preenche `gIBSCBSMono` e **não** informa `gTribSN`. **MEI (CRT 4) não informa o grupo IBSCBS.** Compra governamental em 2027 e 2028: com ente "1 = União", `pIBSSN` é zero e `pCBSSN` é a soma das alíquotas efetivas; com os demais entes, cada um a sua.
- **Espelho** (seção 2.4): a nota de devolução (`finNFe` 4), a de crédito de retorno por recusa total ou parcial (`finNFe` 5, `tpNFCredito` 03 ou 06) e a de débito de retorno por recusa parcial (`finNFe` 6, `tpNFDebito` 09) levam, em cada item, o grupo IBS/CBS **igual ao do item referenciado**. O Motor **copia** (não decide) a partir de `Mov_Nota_Fiscal_Saida_Item_Referencia`, e o ERP **avisa** se o usuário alterar.
- **Nota recebida:** o `tpRegimeIBSCBS` e o `cAtivSN` do fornecedor, quando vierem no XML, são comparados com `Cad_Participante_Regime_Ibs_Cbs`; diferença gera **aviso**, nunca bloqueio.

# 5. NT 2026.004 v1.00 (NF-e e NFC-e, CNPJ alfanumérico)

**O que traz.** Complementa a NT conjunta DFe 2025.001. Só muda o schema: os campos do tipo CNPJ e as chaves de acesso passam de numéricos para texto (alfanuméricos). Lista: CNPJ do emitente de NF referenciada e de NF de produtor (`BA06`, `BA13`), do emitente (`C02`), do destinatário (`E02`), de retirada e entrega (`F02`, `G02`), do autorizado a obter o XML (`GA02`), do fabricante (`I05e`), do adquirente da importação (`I23d`), do produtor (`O03`), do transportador (`X04`), do pagamento (`YA03c`), do intermediador (`YB02`) e do responsável técnico (`ZD02`); chaves `refNFe`, `refNFeSig`, `refCTe`, `chNFe` da exportação indireta e `chaveAcesso` do DF-e referenciado; e os serviços de retorno de autorização, evento, consulta de protocolo, de cadastro, distribuição e resumo.

**No dicionário.** O tipo lógico CNPJ já tem 14 posições com letras (documento 50) e vários campos já dizem "aceita CNPJ alfanumérico" (por exemplo `cnpj_recebedor` do vínculo de pagamento e `cnpj_empresa_imobiliaria` da ABI). A chave de acesso é texto de 44 posições (50 na NFS-e Nacional). O documento 34 já registrava: **"nada muda no modelo de dados"**; a regra do dígito verificador (módulo 11, ASCII menos 48) e a lista de letras aceitas ficam como parâmetro. **Esta NT não muda isso.** Quem implementa a emissão precisa dos schemas; o dicionário já comporta.

**Datas.** A v1.00 desta NT dava **testes em 01/06/2026**; a **v1.01 (junho/2026) troca para "até 15/06/2026"**, e a **produção segue em 01/07/2026**. O documento 34 registra homologação em 06/04/2026 e produção em 06/07/2026 para o conjunto da NT 2026.004 e da NT conjunta; **os dois pares de datas diferem**. Podem vir de documentos distintos (a NT conjunta e esta NT), mas **não conferi**: Q163-E1.

# 6. O que ainda falta chegar

Das notas do Ato nº 10, **a NT 2026.005 desta versão (NF-e e NFC-e) chegou**; o Ato aprova a mesma NT 2026.005 **também para CT-e, CT-e OS, NFCom e BP-e**, e essas versões **não vieram**. Também faltam: **NT 2026.004 v1.01 do RTC** (CT-e, NFCom, BP-e, NF3e, NFAg e NFGas), **NT 2025.002 v1.53**, **NT 2026.006 v1.01**, **NT 2026.007 v1.11**, **NT 2026.008 v1.01**, **NT 2026.001 da NF-e ABI**, a Tabela de Códigos da ABI v1.01, a planilha de CFOP v2.10 e a tabela de NCM (documentos 161 e 162). Resumo na Q163-5.

# 7. Contagem

| Item | Entidades | Campos |
|---|---|---|
| Revisão 28 (real) | 995 | 10.844 |
| Q163-2: `Mov_Nota_Fiscal_Saida_Item.ID_Atividade_Simples` | 0 | +1 |
| Q163-3: `Mov_Dfe_Evento_Simples_Item` | +1 | +11 |
| Q163-1 e Q163-4: regras de texto; Q163-3: 2 valores de `tipo_evento_dfe` | 0 | 0 |
| **Total deste documento** | **+1** | **+12** |

**Revisão 29 prevista:** 1.005 entidades e 11.000 campos (os 10.988 do documento 38 mais 12). Com as Q161-1 e Q161-2 aprovadas, 11.002 campos.

# 8. Perguntas

| Id | Pergunta | Recomendação |
|---|---|---|
| **Q163-1** | O `tpRegimeIBSCBS` do emitente **não vira campo**: é derivado da opção do Simples (`Cad_Simples_Opcao`), do sublimite da filial e do regime regular (`Cad_Participante_Regime_Ibs_Cbs`), pela tabela da NT (seção 4.3)? | **Sim** |
| **Q163-2** | Cria `ID_Atividade_Simples` (opcional) no item da NF-e de saída, para o `cAtivSN` (códigos 01 a 04 e 90), sugerido pelo produto e preenchido só para optante ou opção pendente? | **Sim** |
| **Q163-3** | Aprova o registro do evento 412140 do fisco com a entidade `Mov_Dfe_Evento_Simples_Item` (11 campos), desenho provisório até o schema chegar, com comparação por aviso e sem recalcular? | **Sim** |
| **Q163-4** | O Motor passa a seguir as regras da NT (grupos por regime, CST 620, MEI sem grupo IBSCBS, compra governamental) e a **copiar** o grupo IBS/CBS do item referenciado nas devoluções e retornos por recusa, com aviso se o usuário mudar? | **Sim** |
| **Q163-5** | Você envia as notas que faltam (seção 6), começando pela **NT 2026.004 v1.01 do RTC** e pela **NT 2026.001 da NF-e ABI**? (Substitui a Q161-3 no que a NT 2026.005 da NF-e já resolveu.) | **Sim** |

# 9. Para o contador e para a equipe

| Id | Pendência | Tratamento provisório |
|---|---|---|
| **Q163-C1** | Contribuinte do Regime Normal com opção pelo Simples **indeferida e em discussão**: a NT diz que ele é "regime regular para todos os fins (transferência de crédito, devolução e apuração)", mas emite com o `gTribSN`. Qual é a apuração própria dele e o que acontece se a opção for deferida depois? | O ERP apura como regime regular (como diz a NT), emite como a tabela manda e avisa; sem retificação automática |
| **Q163-C2** | O regime `hibrido_somente_cbs` (CBS regular, IBS pelo Simples; `regApIBSCBSSN` = 2 na NFS-e) **não tem linha na tabela da seção 2.3 da NT**. Como preencher `tpRegimeIBSCBS` e os grupos nesse caso? | O ERP não escolhe: avisa e pede o preenchimento ao usuário |
| **Q163-C3** | Compra governamental em 2027 e 2028 (`pIBSSN` zero para a União e `pCBSSN` somada): confirmar a leitura e o `tpEnteGov` | Regra do Motor como a NT diz, provisória |
| **Q163-E1** (equipe) | Datas da NT 2026.004 da NF-e: até 15/06/2026 (teste, v1.01; era 01/06/2026 na v1.00) e 01/07/2026 (produção), contra 06/04 e 06/07/2026 do documento 34 | Vale a data desta NT; o parâmetro tem vigência |
| **Q163-E2** (equipe) | Conferir os valores do domínio de `tipo_receita_bruta_sn` (0 a 5 e 9, como no evento 412140) e do domínio de atividade do Simples (se tem 01 a 04) | Carga como publicada |

# 10. Limites

- Li as duas NTs por inteiro; **não tenho os schemas** (`e412140_v1.00.xsd` e os XSD da NF-e). Os nomes e tamanhos do evento seguem a tabela da NT.
- A **NT 2026.005 das demais modelos** (CT-e, CT-e OS, NFCom e BP-e) pode trazer campos próprios; esta análise vale só para a NF-e e a NFC-e.
- A leitura do CRT pendente pelo `Excesso_Sublimite` da filial é minha.
- Nada foi validado pelo contador.

## Acréscimo de 03/11/2026: NT 2026.004 v1.01 da NF-e e da NFC-e (junho/2026)

Você reenviou a NT 2026.005 v1.00 (arquivo idêntico ao anterior; nada muda neste documento) e enviou a **NT 2026.004 v1.01 da NF-e e da NFC-e**. Comparei com a v1.00 que eu já tinha. **O que mudou:** (1) a data de homologação passou de 01/06/2026 para **até 15/06/2026**; a produção segue em **01/07/2026**; (2) entrou o **leiaute do serviço de inutilização** (`inutNFe` e `retInutNFe`, campo CNPJ do emitente com 14 posições, tipo alfanumérico). O resto é igual: campos de CNPJ e chaves de acesso de numérico para alfanumérico nos grupos BA, C, E, F, G, GA, I, I01, I03, O, X, YA, YB, VC e ZD, e nos serviços de autorização, evento, consulta, cadastro, distribuição, resumos, cancelamento, EPEC e ator interessado.

**Efeito no dicionário: nenhum campo novo.** O CNPJ já é alfanumérico em todo o dicionário e `Mov_Dfe_Inutilizacao` (série, faixa, justificativa, protocolo) não guarda o CNPJ, que vem da filial. Fica só a data de vigência no parâmetro da NT.

**Esta não é a NT 2026.004 do RTC** (CT-e, CT-e OS, NFCom, BP-e, NF3e, NFAg e NFGas): aquela é outra nota com o mesmo número e **continua sem o texto**. Para o BP-e há só o pacote de schemas (documento 164).
