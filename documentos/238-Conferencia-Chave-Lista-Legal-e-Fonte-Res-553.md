# Conferência das cargas das listas legais contra a chave nova e a fonte da Res. 553 — Documento 238

*Você respondeu "1 e 2" ao "próximo passo": (1) conferir as cargas das outras listas legais contra a chave nova de `Cad_Lista_Legal_Item` (D-N616) e (2) procurar na internet o Anexo Único atual da Res. Gecex 553/2024. **Nada foi aplicado ao dicionário** (você ainda não escreveu "consolidar"); a Carga238 é só proposta. Achei **um problema**: a Carga26 (listas da LC 214 e do IS) repete a chave em 49 casos, só no SQL Server.*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. Resumo

| **Lista (carga)** | **Linhas** | **Chaves repetidas** | **Situação** |
|---|---|---|---|
| LC 214 e Imposto Seletivo (Carga26, `03-lista-legal`) | 708 | **49 chaves, 151 linhas** | **Problema** (seção 2); proposta de correção na Carga238 (Q238-1) |
| Lista da Lei 10.485 (Carga35) | 66 | 0 | Limpa |
| Mover, anexo I (Carga40) | 80 | 0 depois dos 46 ajustes da Carga51 | Limpa (antes dos ajustes, o número do Ex ficava em `Restricao_Tecnica` e não na chave) |
| Pneus de autopeças (Carga40) | 2 | 0 | Limpa |
| Autopeças não produzidas e Res. 553 (Carga51) | 11.456 + 7.128 | 0 | Limpa (a de 553 é a lista original de 2024, provisória) |
| Decreto 12.955 (Repetro, GNL, Reporto, arts. 196 e 197), IPI, ZFM e medicamentos do art. 146 | — | — | **Não conferi:** não há carga dessas listas no meu ambiente (seção 4) |

A chave usada na conferência é a da revisão 51: (tipo da lista, anexo, NCM, NBS, registro na Anvisa, `Numero_Ex`), com o código sem pontos e o vazio valendo como valor igual (regra do SQL Server). No PostgreSQL o nulo vale como valor diferente e a chave única nunca recusa essas linhas; por isso o problema só aparece quando o banco inicial, o SQL Server, receber a Carga26.

# 2. O problema da Carga26 (LC 214 e Imposto Seletivo)

A Carga26 trouxe **uma linha por item do anexo**. Quando o mesmo NCM (ou NBS) aparece em **dois ou mais itens do mesmo anexo**, as linhas diferem só no texto de `Fundamento_Legal` ("LC 214, Anexo IV, item 2", "…item 29" e assim por diante). Como `Fundamento_Legal` não faz parte da chave, no SQL Server a segunda linha seria recusada. Conferi por programa que, dentro de cada grupo repetido, **todas as outras colunas são iguais** (vigência, restrição técnica, exceção, situação do dado e marca de revisão); só muda o item do anexo.

| **Anexo (tipo da lista)** | **Chaves repetidas** | **Linhas envolvidas** |
|---|---|---|
| Anexo I | 1 | 2 |
| Anexo II | 1 | 2 |
| Anexo III | 1 | 10 |
| Anexo IV | 16 | 52 |
| Anexo V | 2 | 11 |
| Anexo VI | 8 | 30 |
| Anexo IX | 15 | 31 |
| Anexo XI | 4 | 10 |
| Anexo XII | 1 | 3 |
| **Total** | **49** | **151** |

Das 49 chaves, 44 são de NCM e 5 de NBS. O caso mais extremo é uma chave do Anexo III que aparece em 10 itens (18 a 26 e 28). Os números decimais de item (por exemplo, 1.1 a 1.7 do Anexo V e 2.22, 2.23 e 2.26 do Anexo XI) foram tratados como itens distintos.

**Correção proposta (Q238-1):** reunir as linhas repetidas **numa só linha por chave**, escrevendo no `Fundamento_Legal` todos os itens ("LC 214, Anexo IV, itens 2, 29, 30, 31, 32, 68, 72, 92 e 105, versão LC 227/2026"). Isso leva a Carga26 de **708 para 606 linhas** (708 − 151 + 49) e não muda o dicionário, só a carga. A Carga238 traz os dois arquivos: as 151 linhas que repetem a chave (com o número da linha no arquivo original e o item) e a carga de 606 linhas pronta para substituir a do `03-lista-legal` da Carga26.

**Alternativa (não recomendada):** acrescentar à chave um campo `Numero_Item_Anexo` (campo novo, mudança no dicionário e no T-SQL). Mantém uma linha por item, mas aumenta a chave de seis para sete colunas e não traz informação que o motor use: a alíquota e o tratamento dependem do NCM e do anexo, não do número do item. Só valeria a pena se o Motor precisasse citar o item exato na tela (hoje o `Fundamento_Legal` já cita todos).

# 3. O que não muda

- A identidade de `Cad_Lista_Legal_Item` continua a da D-N614 e D-N616 (seis colunas, as quatro últimas opcionais).
- As Cargas 35, 40 e 51 ficam como estão.
- Nenhuma tabela, campo, chave estrangeira ou índice do dicionário muda: a revisão 51 segue com 1.242 entidades, 14.438 campos e 1.508 tabelas.

# 4. O que não consegui conferir

Não há, no meu ambiente, carga das listas do **Decreto 12.955** (Repetro, GNL, Reporto, arts. 196 e 197), do **IPI**, da **Zona Franca de Manaus** e dos **medicamentos do art. 146**; por isso essas cinco listas **continuam com a equipe**: ao carregar, aplicar a mesma chave (tipo, anexo, NCM, NBS, Anvisa, Ex) e, se houver repetição, usar a regra da Q238-1 (uma linha por chave, itens no `Fundamento_Legal`). A conferência da chave também não substitui a execução do T-SQL num SQL Server, que continua pendente.

# 5. Res. Gecex 553/2024: o Anexo Único atual

Procurei a lista vigente (item 2 do seu pedido). Resultado:

- **Fonte oficial:** a página do MDIC sobre o regime de ex-tarifários e a lista "sem similar nacional" (Lessin), atualizada em **16/10/2026**, oferece o arquivo **"Lista Vigente"** em Excel (`lessin_16_10_2026.xlsx`). O endereço do arquivo veio de um resumo de modelo que **não consegui confirmar**; peço que você o confirme na página.
- **Por que não carreguei:** minhas ferramentas de leitura da internet devolveram o xlsx como binário ilegível, e a regra do projeto é não tentar outro caminho depois de uma falha. Também falharam, por erro do servidor, as páginas que reproduziam a Res. 813 (Okai) e um blog (Econet).
- **Cadeia de alterações da Res. 553 que encontrei:** a **575/2024** (revogada pela **645/2024**), a **645/2024**, a **708/2025**, a **785/2025** (revogada pela **822/2025**), a **813/2025** (altera condições) e a **822/2025** (vigência 01/12/2025). O Anexo pode ter mudado em 645, 708, 822 e, talvez, 813.
- **Consequência:** a Carga51/02 (7.128 linhas) continua sendo a **lista original de 2024**, provisória, como já estava.

**O que peço:** baixar o "Lista Vigente" na página do MDIC e me enviar o arquivo (ou, se preferir, os textos das Res. 645, 708, 822 e 813). Com o arquivo, comparo com a Carga51/02 e entrego a diferença (linhas novas, retiradas e com condição nova) para a sua aprovação.

# 6. Pergunta para você

| Id | Pergunta | Recomendação |
|---|---|---|
| Q238-1 | Reunir as **151 linhas** da Carga26 que repetem a chave (LC 214 e IS) em **49 linhas**, escrevendo todos os itens no `Fundamento_Legal`, e trocar a carga de 708 por 606 linhas? (sem mudança no dicionário; a alternativa é um campo novo `Numero_Item_Anexo`) | **Sim** |

# 7. Arquivos

A **Carga238-20261118** (zip) traz, em CSV UTF-8 com BOM, vírgula e CRLF (mesmo formato da Carga26):

| **Arquivo** | **Conteúdo** |
|---|---|
| `01-colisoes/Carga26_LC214_chaves_repetidas_49.csv` | 151 linhas: linha no arquivo original, tipo, anexo, NCM, NBS, item do anexo, `Fundamento_Legal` e tamanho do grupo |
| `02-proposta/Cad_Lista_Legal_Item_lc214_e_is_sem_repeticao_606.csv` | A carga da LC 214 e do IS com uma linha por chave (606 linhas) |
| `LEIA-ME.txt` | Descrição dos arquivos |

**Nada disso foi carregado nem aplicado.** Quando você escrever "consolidar", a Q238-1 entra com a sua resposta.
