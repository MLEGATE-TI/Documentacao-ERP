# Lista de Autopeças Não Produzidas e Documentos do Setor Automotivo — Documento 235

*Em 18/11/2026 você avisou que ia anexar vários documentos do setor automotivo e depois escreveu "foram todos". Chegaram 70 arquivos: a lista oficial de autopeças não produzidas do MDIC (a de outubro de 2026 e o histórico desde 2020), os formulários dos pleitos, três portarias do Mover para veículos pesados, cinco avisos de consulta pública, um ofício, o plano dos semicondutores e o arquivo do ciclo de condução do VECTO. Este documento fecha a **Q206-10** (a lista que faltava), corrige o que escrevi sobre ela nas D-N549 e D-N550 e propõe o desenho em campos. **Nada foi aplicado ao dicionário**: espera as respostas e o "consolidar" (revisão 51).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Assunto** | **Resultado** |
|---|---|
| Lista de autopeças não produzidas (Q206-10) | **Chegou.** O arquivo de outubro de 2026 tem **10.717 ex-tarifários** (Anexo I 9.609; Anexo II 1.108) em **438 NCM**; todos os NCM existem na tabela vigente de 16/11/2026. A carga está pronta: **Carga235** (10.717 linhas de `Cad_Lista_Legal_Item`). |
| Correções ao que eu escrevi | Eram 9.658 ex em 422 NCM (fonte não oficial): o oficial tem 10.717 em 438. O Anexo II **não** é de bens de capital: os arquivos o chamam de "autopeças grafadas na Nomenclatura Comum do Mercosul". A lista oficial **não traz o regime** (isenção ou redução) de cada item. |
| Prazo | **3.713 ex-tarifários (35%) vencem em 31/12/2026**, daqui a 43 dias; 9.586 (89%) vencem até 30/09/2027, nos quatro lotes da Resolução 935/2026. |
| Mudança no desenho | Faltam dois campos em `Cad_Lista_Legal_Item`: o número do Ex e a descrição do item (Q235-2). Sem eles a chave de negócio colide (um NCM chega a ter 693 ex). Contagem prevista: 1.242 entidades e **14.436 campos** (+2). |
| Portarias e avisos do Mover (pesados) | **Nenhum campo novo.** O que existe (`Mov_Mover_Requisito_Ano`) já cobre eficiência de pesados, desempenho estrutural, rotulagem e pegada de carbono. As consultas públicas são minutas; esperam a portaria final (Q235-6). |
| Perguntas para você | **Q235-1 a Q235-6** (seção 1.49 do documento 38). Para o contador, a **C286** foi reescrita (não há pergunta nova). |

# 2. O que chegou

**Grupo A — lista de autopeças não produzidas (MDIC).** Três fotos atuais (julho, agosto e outubro de 2026, todas com NCM, Ex, descrição, resolução e fim da vigência, em dois anexos), uma versão "sem ex excluídos" (aparenta ser uma foto de meados de 2026: o fim de alguns itens é 30/09/2026), e o histórico: lista geral de maio de 2022 a fevereiro de 2024 (nove versões), listas das Resoluções 284 e 285 de maio a novembro de 2022 e as listas de 2020 e 2021 (arquivos chamados "redução, Resolução 23" e "isenção, Resolução 102"; não li essas resoluções). Os arquivos repetidos (versões "_1" e cópias) são idênticos aos originais.

**Grupo B — formulários do processo de pleito.** Ficha técnica dos Anexos I e II, comprovante de capacidade de produção nacional, manifestação de produção nacional equivalente, pleitos de alteração e de revogação, prorrogação de vigência e os dois catálogos em Word. São modelos para a empresa pedir inclusão, alteração, revogação ou prorrogação de um Ex. A planilha de pontuação da prorrogação tem 14 perguntas (eficiência energética, segurança, conectividade, novos materiais, inovação, escala, complexidade, patentes e outras) e parte dela com erro `#REF!`.

**Grupo C — Mover e veículos pesados.** Portaria GM/MDIC 176/2025 (cronograma do programa de eficiência energética de pesados), 167/2026 (implementos do Grupo 01 e procedimentos de ensaio), 294/2026 (ciclo de condução do Grupo 01, DOU de 09/10/2026, com o arquivo `.vdri` de velocidade e gradiente e os hashes SHA-256 e SHA-512), avisos de consulta pública 3, 5, 6, 7 e 8/2026, o Ofício SEI 3219/2024 do MDIC à AEA e o plano de ação dos semicondutores (dezembro de 2021, só contexto).

# 3. A lista de outubro de 2026

| **Medida** | **Anexo I** | **Anexo II** | **Total** |
|---|---|---|---|
| Linhas (ex-tarifários) | 9.609 | 1.108 | **10.717** |
| NCM distintos | 401 | 112 | **438** (75 estão nos dois anexos) |
| NCM fora da tabela vigente de 16/11/2026 | 0 | 0 | **0** |
| Chave (NCM + Ex) repetida dentro do anexo | 0 | 0 | 0 (1 par aparece nos dois anexos) |
| Resoluções distintas | 36 | 27 | **37 atos** (resolução e data do DOU) |
| Sem fim de vigência | 6 | 0 | 6 |

**Datas de fim.** 31/12/2026: 3.713 (Anexo I 3.353; II 360). 31/03/2027: 1.338. 30/06/2027: 1.580. 30/09/2027: 2.955 (esses quatro são os lotes que as fontes secundárias atribuíam à Resolução 935/2026: 9.586 linhas). Depois: 30/11/2027 a 30/09/2028, 1.125 linhas (resoluções mais novas, entre elas a 974, DOU de 07/10/2026). Dos 3.713 que vencem em 31/12/2026, 2.702 vêm da Resolução 284/2021 e 817 da 545 (republicada em 18/12/2023).

**Os seis sem fim:** `3917.22.90 ex 1` (Res. 898/2026), `8511.40.00 ex 7 e 8`, `8536.50.90 ex 71 e 98` e `8536.90.40 ex 40`. A carga os leva com 31/12/9999 e um aviso (Q235-3).

**Como a lista muda.** De julho para agosto entraram 11 (Res. 946) e saíram 78; de agosto para outubro entraram 190 (Res. 974, DOU de 07/10/2026) e saíram 29; nenhum item mudou de resolução ou de data. Ou seja, o MDIC publica a lista nova por foto e o ERP precisa comparar a foto nova com a vigente (chave: anexo, NCM e Ex).

**O texto.** Descrições de até 1.706 caracteres; 4.175 têm ponto e vírgula, aspas ou quebra de linha (a carga troca a quebra por espaço e usa aspas, como as outras).

**Datas do DOU.** 10.706 linhas trazem "DOU dd/mm/aaaa" na resolução; as 11 da Res. 946 estão sem espaço ("DOU06/08/2026") e a carga corrige. As 1.201 republicações (545: 839; 665: 253; 589: 109) trazem a primeira data.

# 4. Correções ao que escrevi (D-N549, D-N550 e C286)

1. **Quantidade.** 10.717 ex-tarifários em 438 NCM (eu tinha 9.658 em 422, de um buscador não oficial).
2. **Anexo II.** Os títulos dos arquivos são "Anexo I: lista de autopeças destinadas à produção" e "Anexo II: lista de autopeças grafadas na Nomenclatura Comum do Mercosul". Eu tinha escrito "bens de capital, informática e telecomunicações" (era o outro regime, o de BIT e BK). Corrijo na carga e no doc 188.
3. **284 e 285.** Em novembro de 2022 a lista geral era a soma das duas listas (6.514 = 5.291 da 284 + 1.226 da 285 − 3 em comum). Na lista de 2026 **a 285 não aparece mais pelo nome**: 824 dos seus ex estão lá, 820 deles sob a Resolução 545 (republicada em 18/12/2023). Não li a 545; **o arquivo não diz se o item é de isenção ou de redução**.
4. **Vencimento.** A lista confirma os quatro lotes de 31/12/2026, 31/03/2027, 30/06/2027 e 30/09/2027 (89% dos itens). Os demais têm resoluções novas e datas de 2027 e 2028.
5. **Fonte.** A lista oficial e atual existe (planilha do MDIC por foto, com data), o que responde a letra (d) da C286.

# 5. Desenho proposto (nada aplicado)

**5.1 Onde entra.** Em `Cad_Lista_Legal_Item`, sem entidade nova. Cada ex-tarifário é uma linha com vigência própria, `ID_Tipo_Lista` = `autopecas_nao_produzidas` (Q235-1), `Codigo_Anexo` = "Anexo I" ou "Anexo II", `ID_Classificacao_Mercadoria` = NCM, `Fundamento_Legal` = resolução e data do DOU, `Situacao_Dado` = provisório até o contador validar, `Eh_Excecao` falso, `Condicao_Comprador` qualquer.

**5.2 Dois campos novos (Q235-2).** `Numero_Ex` (código até 10, opcional, entra na chave de negócio) e `Descricao_Item` (texto, opcional). Hoje a chave é tipo da lista, anexo, NCM (ou NBS ou registro da Anvisa) e restrição; sem o número do Ex, as 693 linhas do NCM 8708.29.99 se chocam. Alternativa sem campo novo: pôr o número em `Grupo_Item` e a descrição em `Restricao_Tecnica`, com o inconveniente de misturar o sentido desses campos (o `Restricao_Tecnica` é potência, capacidade e "exceto"; a chave já o usa).

**5.3 Vigência (Q235-3).** `Vigencia_Inicio` = data do DOU da resolução (leitura minha: a resolução pode fixar outra data de início); `Vigencia_Fim` = "Fim da Vigência" da lista; os seis sem fim ficam com 31/12/9999 e aviso. Sem prorrogação automática: a prorrogação vem por resolução e vira versão nova da linha. O Motor avisa 90 dias antes do fim (proposta do doc 206) e, **no dia 01/01/2027, trata como sem benefício** a linha que não foi prorrogada.

**5.4 Atualização por foto.** A foto nova é comparada com a vigente pela chave (anexo, NCM, Ex): o que entrou vira linha; o que mudou de fim ou de resolução vira versão nova; o que saiu fecha na véspera da data do arquivo, ou na data da resolução quando ela vier (Q235-3). A carga é manual, por usuário com permissão, como as outras listas.

**5.5 Habilitação e regime.** Como o arquivo não traz o regime, **a habilitação decide** (tipo `autopecas_nao_produzidas` em `Cad_Habilitacao_Regime_Especial`, como no doc 206), e não cada linha da lista. Isso substitui os dois instrumentos `autopecas_isencao` e `autopecas_reducao` da D-N550, que eu só poderia carregar se soubesse a origem de cada item (a C286 continua com o contador).

**5.6 Histórico.** A carga leva só a lista vigente (foto de outubro de 2026). Os arquivos de 2020 a 2024 ficam guardados para consulta; se a Mlegate precisar das datas antigas (importação passada), peço depois (Q235-4).

**5.7 Contagem se tudo for aprovado.** 1.242 entidades, 14.436 campos (+2), 3.701 referências, 374 domínios; DDL com 1.508 tabelas e 12.177 comentários (a conferir na consolidação).

# 6. Formulários, portarias e avisos do Mover

**6.1 Formulários dos pleitos.** São o roteiro do processo (identificação da empresa, ficha técnica de uma autopeça, comprovação da capacidade nacional, pontuação). O ERP não precisa dos campos para emitir nota ou apurar tributo. **Proposta (Q235-5): não guardar os pleitos no ERP**; se a Mlegate for pedir inclusão ou prorrogação de Ex, o controle fica fora do sistema.

**6.2 Portaria 176/2025 (pesados).** Define o Grupo 01 (caminhão-trator 6x2 e 6x4 acima de 12 t) e o cronograma: primeiro ciclo 2025-2026 (normativos de ensaio e implementos até 31/03/2026; rotas até 30/06/2026; adaptação do VECTO até 31/12/2026); segundo ciclo 2027-2028 (validação da ferramenta até 01/06/2027; resultados de 01/10/2027 a 30/09/2028, relatório de 01/10 a 01/11/2028; linha de base até 31/12/2028); terceiro ciclo 2029-2030 (metas até 30/04/2029; relatório anual até 01/11; etiquetagem pública a partir de 01/01/2030; verificação das metas a partir de 01/10/2033). O prazo corre mais devagar se o VECTO atrasar (art. 3º, § 3º). Cada grupo seguinte tem dois anos de diferença.

**6.3 Portarias 167/2026 e 294/2026.** A 167 (DOU de 19/06/2026) fixa os implementos "Furgão" e "RB" e remete os ensaios ao Regulamento (UE) 2017/2400 e ao 2025/258; a 294 (DOU de 09/10/2026) fixa o ciclo de condução do Grupo 01 pelo arquivo `Ciclo_Conducao_VECTO_BR_Grupo01.vdri` (valendo só o arquivo com os hashes do § 2º) e muda o art. 3º da 167 (a remissão aos apêndices 8, 9 e 10 passa do Anexo IX para o Anexo VI do regulamento europeu). São normas técnicas de ensaio do **fabricante**; o ERP guarda só o resultado em `Mov_Mover_Requisito_Ano` (tipo `relatorio_eficiencia_pesados`).

**6.4 Avisos de consulta pública (minutas, sem força de norma).** Aviso 3/2026 (DOU de 25/09/2026): rotulagem veicular de conteúdo e origem de componentes e a **Etiqueta Nacional de Origem de Componentes (ENOC)**; aviso 5: metas de desempenho estrutural e de tecnologias assistivas à direção (Índice de Tecnologias Embarcadas, **InTec**) para M2, M3, N2 e N3, com **créditos e débitos** compensáveis; aviso 6: inventário de carbono, pegada de carbono e informações de desmontagem; avisos 7 e 8: pegada de carbono parcial de veículos leves e pesados. Todos pedem manifestação em 15 dias por e-mail ao MDIC. **Proposta (Q235-6): esperar a publicação das portarias** antes de qualquer campo; os conceitos de crédito e débito do InTec e a ENOC só entram quando o texto final disser o que o importador ou o fabricante deve registrar.

**6.5 Ofício 3219/2024 e plano dos semicondutores.** O ofício (14/05/2024) pede apoio da AEA para a metodologia de pegada de carbono e o manual de auditoria do Mover; o plano (dezembro de 2021) é de contexto (Programa Padis e demanda automotiva). Nenhum dos dois muda o dicionário.

# 7. Perguntas para você (documento 38, seção 1.49)

| **Id** | **Pergunta** | **Recomendação** |
|---|---|---|
| Q235-1 | Um só tipo de lista, `autopecas_nao_produzidas`, e o regime (isenção ou redução) vem da habilitação, já que a lista oficial não diz o regime de cada item? | **Sim** |
| Q235-2 | Acrescentar `Numero_Ex` e `Descricao_Item` a `Cad_Lista_Legal_Item` (14.436 campos)? | **Sim** |
| Q235-3 | Início = data do DOU da resolução; fim = "Fim da Vigência"; os 6 sem fim com 31/12/9999 e aviso; sem prorrogação automática; sem benefício a partir de 01/01/2027 para o Ex que não foi prorrogado? | **Sim** |
| Q235-4 | Carregar só a lista vigente de outubro de 2026 (o histórico de 2020 a 2024 fica de consulta)? | **Sim** |
| Q235-5 | Não guardar no ERP os formulários e os pleitos de Ex-tarifário? | **Sim** |
| Q235-6 | Esperar a portaria final antes de desenhar ENOC, InTec, pegada de carbono e desmontagem (consultas 3, 5, 6, 7 e 8/2026)? | **Sim** |

# 8. O que fica aberto

- **Você:** Q235-1 a Q235-6; **depois da aprovação, "consolidar"** (revisão 51: os 2 campos e a Carga235); enviar uma lista nova quando o MDIC publicar a próxima resolução (a 951/2026 permite prorrogar até dois anos, e 3.713 Ex vencem em 31/12/2026). A Q206-10 está **atendida** (a lista chegou).
- **Contador:** C286 reescrita (regime de cada item depois da Resolução 545/2023; alíquota de 0% e contrapartida; fonte já resolvida). Nenhuma pergunta nova.
- **Eu:** conferir o texto da Resolução 545/2023 e da 974/2026 se você enviar; recalcular a carga se a lista mudar.

# 9. Respostas de 18/11/2026 e ajuste (revisão 2 do documento)

**Respostas.** "Q235-1 a Q235-6 - Sim para todos". Ficam aprovados o tipo único, os campos `Numero_Ex` e `Descricao_Item`, a vigência pela data do DOU, só a lista vigente, os pleitos fora do ERP e a espera das portarias finais. Nada aplicado: falta o "consolidar".

**Princípio que você pediu para lembrar (D-N608).** As peças **produzidas ou compradas** ficam todas agrupadas no **cadastro de produtos** (`Cad_Produto_Servico`); só entram **atributos** para os casos específicos, como as autopeças. Conferi o desenho com esse princípio:

1. **A carga não cria produto.** Cada linha da Carga235 é uma linha da **lista legal** (a descrição do Ex, como o MDIC publica), não um produto da Mlegate. O produto continua um só, no `Cad_Produto_Servico`, produzido ou comprado.
2. **Falta o elo.** Hoje o produto se liga ao Ex da Tipi por `Cad_Produto_Servico_Dados_Produto.ID_Ex_Tipi`, mas não há campo que diga em qual Ex-tarifário de autopeças ele se enquadra, e o item da importação (`Mov_Autopecas_Importacao_Item`) guarda a habilitação, mas não o Ex usado. Um NCM chega a ter 693 ex; sem o elo o Motor só poderia sugerir e o usuário escolheria de novo a cada importação.
3. **Estruturas que já seguem o princípio** (atributo ligado ao produto, sem lista paralela): `Cad_Is_Produto_Ficha` (ficha do Imposto Seletivo por produto) e `Cad_Habilitacao_Automotiva_Produto` (aponta para o produto do cadastro). `Cad_Produto_Catalogo` é o catálogo do Portal Único (externo, com a versão do governo) e se liga ao produto do ERP por `Mov_Duimp_Item.ID_Produto`; não é uma segunda lista de produtos.

**Proposta nova (Q235-7).** Dois campos, os dois opcionais e referências a `Cad_Lista_Legal_Item` (do tipo `autopecas_nao_produzidas`):

| **Entidade** | **Campo** | **Regra** |
|---|---|---|
| `Cad_Produto_Servico_Dados_Produto` | `ID_Lista_Legal_Item_Ex` | O Ex-tarifário de autopeça não produzida em que o produto se enquadra, como o `ID_Ex_Tipi` faz com a Tipi. Preenchido só nos produtos de que isso interessa. O NCM do produto tem que ser o do item da lista; senão o Motor avisa. Vazio: o Motor lista os Ex vigentes do NCM e o usuário escolhe na importação. |
| `Mov_Autopecas_Importacao_Item` | `ID_Lista_Legal_Item` | O Ex usado na importação (vem do produto, quando preenchido). Exigido na importação com benefício. O Motor confere a vigência na data do desembaraço e avisa se o Ex venceu (31/12/2026 para 3.713 deles). |

Contagem se tudo for aprovado (Q235-2 e Q235-7): 1.242 entidades e **14.438 campos** (+4).

