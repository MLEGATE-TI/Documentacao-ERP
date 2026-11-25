# Consolidação da Revisão 60 — Documento 258

*Você escreveu **«consolidar»**. Apliquei ao dicionário **tudo o que você já tinha aprovado** e esperava a aplicação: o **desenho do FGTS do documento 252** (retorno do eSocial, guia, histórico de remunerações, rescisão e o lote da folha processada fora do ERP), em **9 entidades novas e 111 campos**, e o valor **`folha_externa`** em `Mov_Titulo.Origem_Tipo`. Resultado: **1.279 entidades e 15.055 campos**. Não ficou nenhum item aprovado de fora.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Medida** | **Revisão 59** | **Revisão 60** | **Diferença** |
|---|---|---|---|
| Entidades | 1.270 | **1.279** | +9 (todas em Folha & RH) |
| Campos | 14.944 | **15.055** | +111 (os campos das nove entidades; o valor novo de enumeração não conta como campo) |
| Campos de referência (FK) | 3.782 | **3.809** | +27 |
| Entidades mestres (com vigência) | 277 | 277 | 0 (nenhuma das nove tem vigência) |
| Domínios de `Cad_Classe_Sistema` | 376 | 376 | 0 |
| Tabelas físicas (DDL) | 1.547 | **1.556** | +9 (sem tabela de versão, porque nenhuma tem vigência) |
| Chaves estrangeiras (DDL) | 4.059 | **4.086** | +27 |
| Índices (DDL) | 4.151 | **4.178** | +27 |
| Comentários (DDL) | 12.657 | **12.750** | +93 |
| Comandos do T-SQL | 22.415 | **22.571** | +156 |
| Chaves opcionais que esperam a onda de destino | sem mudança | sem mudança | 0 (as 27 novas apontam para a mesma onda ou para ondas anteriores) |
| Alertas do gerador de DDL | 8 | 8 | 0 |
| Revisão dos módulos | Contas a Pagar/Receber 31, Folha & RH 31 | Contas a Pagar/Receber **32**, Folha & RH **32** (Tesouraria continua na 15 e a Fase 0 na 102) | |

O DDL foi executado em ordem, em PostgreSQL 16, sem erro (1.556 tabelas, 4.086 chaves estrangeiras, 12.750 comentários). O T-SQL foi só lido (contagem de comandos), não executado num SQL Server. A auditoria fechou com **0 achados em aberto**, sem acrescentar nenhuma entidade à lista de aceitos de propósito.

# 2. O que entrou

Todas as nove entidades ficaram no módulo **Folha & RH** (anexo, seção 32), na onda 6 do DDL, e **nenhuma tem vigência**.

| **Entidade** | **Campos** | **O que é** | **Decisões** |
|---|---|---|---|
| **`Mov_Esocial_Retorno_Fgts`** | 23 | O retorno do eSocial do FGTS: **S-5003** (por trabalhador) e **S-5013** (consolidado). Guarda o XML inteiro, a comparação com a provisão da folha, `Indicador_Apuracao`, `Existencia_Informacao` e `ID_Lote_Folha_Externa`; o recibo pode ficar vazio (CSV sem recibo). O retorno novo da mesma chave substitui o anterior sem apagá-lo | D-N697, D-N702, D-N705; R14, R15, R17 |
| **`Mov_Esocial_Retorno_Fgts_Valor`** | 12 | O retorno **por tipo de valor** (mensal, 13º, rescisão, aviso prévio, período anterior e outros), por estabelecimento e lotação: a base da conferência contra cada débito da guia | D-N702; R18 |
| **`Mov_Fgts_Guia`** | 16 | A **guia do FGTS Digital**, importada em CSV ou digitada (não há API), com vencimento oficial, valor, Pix copia e cola e situação | D-N692, D-N696, D-N697; R2, R3, R5, R16 |
| **`Mov_Fgts_Guia_Debito`** | 9 | Os **débitos que a guia agrupa** (mensal, 13º, rescisório, multa de 40%, consignado), ligados ao título e ao retorno | D-N697; R16, R18 |
| **`Mov_Rh_Fgts_Historico_Remuneracao`** | 7 | O **histórico de remunerações** por vínculo e competência (folha do ERP, migração desde a contratação ou digitação) | D-N697, D-N703; R9, R19 |
| **`Mov_Rh_Fgts_Arquivo_Historico`** | 9 | O **arquivo do Anexo I** gerado para o FGTS Digital (até 5.000 linhas ou 130 KB), com a situação do envio ao portal | D-N697; R9, R13 |
| **`Mov_Rh_Fgts_Rescisao`** | 13 | A **rescisão**: método da multa, base pedida à Caixa, **multa estimada** (sempre rotulada) contra a **oficial** | D-N697, D-N703; R9, R10, R11, R19 |
| **`Mov_Rh_Folha_Externa_Lote`** | 14 | O **lote importado** da folha processada fora do ERP (XML do S-5003 ou CSV derivado), com hash, totais, usuário e situação | D-N704, D-N705; R15, R20 |
| **`Mov_Rh_Folha_Externa_Lote_Ocorrencia`** | 8 | As **ocorrências da conferência** do lote (tudo ou nada), com linha, campo e situação do tratamento | D-N705; R20 |
| **Total** | **111** | | |

| **Mudança em entidade que já existia** | **O que entrou** |
|---|---|
| **`Mov_Titulo.Origem_Tipo`** (Contas a Pagar/Receber, módulo 08) | O valor **`folha_externa`**: o título do FGTS da folha processada fora do ERP nasce do lote importado, e o `ID_Origem` aponta `Mov_Rh_Folha_Externa_Lote`. O `folha_pagamento` continua para a folha feita no ERP. A descrição do `ID_Origem` também foi atualizada |

# 3. O que não entrou

- **O desenho das outras naturezas da folha externa** (líquido, INSS e IRRF): você decidiu (Q252-11, D-N705) que saem do documento 252 e serão desenhadas na integração da folha com o financeiro, **importando o XML do eSocial onde ele devolve o dado** (S-5001, S-5002, S-5011 e S-5012). É **pendência minha**, e não há entidade nova para isso.
- **A contabilização do FGTS** (reversão da provisão, mora e multa de 40%): depende do contador. A **C375** continua só **proposta** no documento 252 e **não** foi escrita no documento 188.
- **Todo o resto do documento 254:** as 34 perguntas abertas por banco continuam fora do dicionário.

# 4. A Carga

**Não há Carga60.** Os dois valores do domínio `tipo_evento_esocial` (**S-5003** e **S-5013**) são **cadastro do usuário** (o domínio é aberto: a Receita publica o evento e a Mlegate só cadastra o valor, nunca uma tabela nova), como o domínio sempre foi. As nove tabelas entram vazias.

# 5. Leituras minhas e limites do que apliquei

- **Módulo das entidades:** o documento 252 não dizia em qual módulo cada entidade ficava. Pus as **nove em Folha & RH**, ao lado do `Mov_Esocial_Retorno` (o retorno do eSocial já mora lá). A guia, os débitos e o lote são usados pelo Financeiro **por perfil** (R13), não por módulo. Se você preferir a guia e o débito em Contas a Pagar/Receber, é só mover.
- **Chaves de negócio não são restrição de tabela.** `ID_Empresa` + `Numero_Guia` único (R2), o hash do lote que barra o mesmo arquivo duas vezes (R20 a) e a chave do retorno (um vigente por chave) são **regras de validação do ERP**, como nos demais cadastros; o banco de dados não as impõe.
- **`Valor_Deposito` vale zero** quando o XML não traz o `dpsFGTS`; no CSV ele é obrigatório (R20).
- **O CSV leva só as colunas que o ERP guarda** (14, derivadas do esquema do S-5003). As outras tags (desligamento, `dtVenc`, `notAFT`, `detRubrSusp` e demais) só ficam no XML.
- **T-SQL:** só lido, não executado; a primeira execução num SQL Server é da equipe (documento 31, seção 4).

# 6. O que fica aberto

- **Você:** as 34 perguntas do envio bancário, por banco, no documento 254, os **três PDFs da Caixa** (Q250-56) e os demais itens do documento 38. **Nenhuma pergunta aberta no documento 252.**
- **Meu lado:** o desenho das outras naturezas da folha externa (Q252-11), quando você disser.
- **Contador:** a **C374** (FGTS Digital: vencimento do dia 20 e multa de 40% da rescisão), no documento 188, e a **C375** (contabilização), que ainda é proposta.

Próximos números: D-N707, contador C375 (proposta no documento 252), documento 259, R154 (do documento 250), Q250-76, Q251-9, Q246-9, Q248-7, Q232-12, Q234-4, Q228-3, Q229-3, Q235-8, Q236-5, Q237-2, Q239-5; seções do doc 38 a partir de 1.56.
