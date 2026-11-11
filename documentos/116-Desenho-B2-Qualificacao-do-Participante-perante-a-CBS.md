# Desenho do B2: Qualificação do Participante perante a CBS — Documento 116

*Primeiro desenho da fila da CBS, na ordem que você escolheu (Q115-1, opção B: o B2 sozinho, depois o B0a). Reli o Anexo A e o documento 70 (seção 3.2), o documento 86 (seção 4, Q70-3), o documento 94 (bloco B2) e conferi no dicionário da revisão 22 as oito entidades vizinhas, para não duplicar o que já existe. Proponho **uma entidade nova com 20 campos**, mais **2 campos novos em entidades existentes**, **1 valor novo em um domínio fechado** e a carga de **dois domínios abertos** (30 tipos de qualificação e 2 critérios do Motor de Regras). É proposta: **nada foi alterado no dicionário**, que segue na revisão 22 até você pedir "consolidar".*

Mlegate · Alberto Beyeler · Outubro de 2026 · Versão 1 (26/10/2026)

**Respostas de 27/10/2026:** **Q116-7 sim** (só o usuário com permissão específica, uma linha em `Cad_Permissao`, cria ou altera a qualificação; a mudança fecha a janela anterior sem apagá-la) e **Q116-8 sim** (qualificação sem comprovante ou vencida: o Motor sugere e o usuário confirma na linha, sem aplicar sozinho e sem bloquear; regra de texto, sem campo novo). **Q116-5 sim** (o valor `cnpj_pessoa_fisica` entra em `Tipo_Inscricao`, o ERP guarda CPF e CNPJ, e a data de início é parâmetro do B0a; +1 valor de enumeração, sem campo novo). **Q116-4 sim**: entra o campo `ID_Natureza_Juridica` (opcional, referência a `Cad_Natureza_Juridica`) em `Cad_Participante_Situacao_Cnpj` (+1 campo e +1 chave estrangeira), e o tipo do ente é lido de `ID_Ente_Federativo`, sem campo novo. As demais perguntas (Q116-1 a Q116-3 e Q116-6) seguem abertas, e a entidade nova do B2 ainda não está aprovada. Nada foi aplicado ao dicionário.

**Suas respostas que valem aqui.** D-N268: a qualificação **tem de ser guardada**. Q94-3: a estrutura é **uma entidade com vigência e tipo em domínio aberto** (o documento 38 registra que você confirmou a estrutura; faltava a lista de campos, que é este documento). Q115-1 = B e Q115-2 = sim: este desenho vem antes do B0a, e os acréscimos do art. 27 vão para o B0a.

# 1. Resumo

- A qualificação é **um fato cadastral do participante que muda no tempo** e decide o enquadramento na CBS: não contribuinte (condomínio, consórcio, SCP, nanoempreendedor, fundos), produtor rural, transportador autônomo, administração pública, entidade de saúde com certificação, ICT, coletor incentivado, profissão do art. 202 e outros. O dicionário hoje não tem onde guardá-la; guarda o regime (Simples, MEI), o porte e a classe comercial.
- Proponho a entidade **`Cad_Participante_Qualificacao_Cbs`** (seção 3), **na janela com vigência**, no mesmo padrão de `Cad_Participante_Porte` e `Cad_Participante_Situacao_Cnpj`: o tipo é um valor do domínio aberto `qualificacao_cbs` em `Cad_Classe_Sistema`, e o Motor de Regras lê a qualificação como critério. **Novo tipo é carga de domínio, não é campo novo.**
- Um participante pode ter **mais de uma qualificação ao mesmo tempo** (por exemplo, sociedade profissional do art. 202 e entidade que opta pelo regime regular); a identidade é participante mais tipo mais vigência.
- A **empresa própria também é participante** (`Cad_Filial.ID_Participante`), então a mesma entidade serve ao emitente e ao cliente ou fornecedor. O participante é único para todo o ERP (não tem `ID_Empresa`), então a qualificação vale para qualquer empresa do grupo que negocie com ele.
- **Quatro itens de lista (seção 5)** ficam fora da entidade: o CNPJ da pessoa física, a natureza jurídica, o `Participa_Pnct` (que **proponho adiar para o B0b**, por depender da LC 225) e os critérios do Motor.
- Nenhuma percentagem nem data da lei vai para código ou para o campo: o limite de 80% de uso residencial, o prazo de 12 meses da opção e a data de 1º/1/2027 do CNPJ da pessoa física são **parâmetros com vigência**, que o B0a desenha. Aqui só se guarda **o que foi medido ou informado para aquele participante**.

# 2. O que o dicionário já tem e não muda

| Entidade | O que guarda | Relação com a qualificação |
|---|---|---|
| `Cad_Participante_Classe` | Papel comercial (cliente, fornecedor, funcionário, transportadora, licenciante, representante, estabelecimento próprio, outro), com vigência | **Fica separada.** Papel comercial não é enquadramento tributário; misturar apaga o histórico (opção B da Q70-3, recusada) |
| `Cad_Participante_Porte` | MEI, ME, EPP ou demais, com vigência | Fica. O MEI é **porte**, não qualificação; o documento 70 já tirava o MEI do tipo de transportador |
| `Cad_Participante_Regime_Ibs_Cbs` | A opção do Simples por semestre (unificado, híbrido, híbrido só CBS) | Fica. **Não confundir** com a `Opcao_Regime_Regular` do art. 25 (consórcio e SCP): aquela é a opção **do não contribuinte** por ser contribuinte |
| `Cad_Participante_Regime_Especifico` | Regime específico de atividade (instituição financeira, plano de saúde, cooperativa e outros) | Fica. Descreve **a atividade**; a qualificação descreve **a condição do sujeito** (o plano de autogestão do art. 25 é qualificação; o plano de saúde que presta serviço é regime específico) |
| `Cad_Participante_Situacao_Cnpj` | Situação cadastral do CNPJ (ativa, suspensa, inapta, baixada, nula), com ajuste manual e vigência | Fica. Ganha 1 campo (seção 5) |
| `Cad_Participante_Inscricao` | Inscrições (estadual, municipal, Suframa, NIRE, CAEPF) | Fica. Ganha 1 valor (seção 5) |
| `Cad_Participante_Deficiencia` | Deficiência da pessoa física, com acesso restrito | Fica. É do benefício na compra de veículo (arts. 226 e 227), que é **fato da operação** e não qualificação |
| `Cad_Documento` | O comprovante em arquivo (GED) | A qualificação aponta para ele |

# 3. A entidade `Cad_Participante_Qualificacao_Cbs`

Módulo proposto: **Contabilidade & Fiscal**, o mesmo de `Cad_Participante_Porte`. Com vigência (`Vigencia_Inicio`, `Vigencia_Fim`, `Motivo_Vigencia`) e identificador de versão, como as outras janelas do participante.

| # | Campo | Tipo | Para quê |
|---:|---|---|---|
| 1 | `ID_Participante_Qualificacao_Cbs` | identificador | Chave |
| 2 | `ID_Participante_Qualificacao_Cbs_Versao` | identificador da versão | Histórico da janela |
| 3 | `ID_Participante` | referência (`Cad_Participante`), identidade | Quem é qualificado |
| 4 | `ID_Tipo_Qualificacao` | referência (`Cad_Classe_Sistema`, domínio `qualificacao_cbs`), identidade | O tipo (seção 4) |
| 5 | `Indicador_Contribuinte_Cbs` | enumeração {contribuinte_regime_regular, nao_contribuinte, optante_regime_regular}, opcional | A condição na CBS **naquela vigência**; é o que o Motor lê primeiro |
| 6 | `Motivo_Condicao` | enumeração {por_natureza, por_limite_de_receita, por_opcao, por_ato_da_administracao}, opcional | **Por que** está nessa condição (o produtor rural sai de não contribuinte por limite de receita; o consórcio entra por opção) |
| 7 | `Data_Opcao` | data, opcional | Início da opção pelo regime regular |
| 8 | `Data_Renuncia` | data, opcional | Fim da opção (a lei prevê prazo mínimo e renúncia; o prazo é parâmetro do B0a) |
| 9 | `Percentual_Residencial` | número, opcional | Condomínio: percentual de unidades residenciais **apurado** (o limite da lei é parâmetro) |
| 10 | `Teste_Fii_Atendido` | booleano, opcional | FII e Fiagro: resultado do teste da lei para ser não contribuinte |
| 11 | `Registro_Dispensado_Por_Ato` | booleano, opcional | Art. 105, § 8º: a inscrição no CNPJ dispensada por ato |
| 12 | `Numero_Comprovante` | texto, opcional | CEBAS, título habilitante, filiação, registro do ICT, outros números |
| 13 | `ID_Documento_Comprovante` | referência (`Cad_Documento`), opcional | O arquivo do comprovante |
| 14 | `Data_Validade` | data, opcional | Fim da validade do comprovante (o CEBAS vence) |
| 15 | `Fundamento_Legal` | texto, opcional | Artigo ou ato que dá a qualificação |
| 16 | `Origem` | enumeração {informado_pelo_usuario, calculado_pelo_sistema, carga_inicial} | Quem criou a linha: pessoa, o sistema (por exemplo, o limite do produtor rural) ou a carga |
| 17 | `ID_Usuario_Registro` | referência (`Cad_Usuario`), opcional | **Quem registrou**; vazio quando o sistema calculou |
| 18 | `Vigencia_Inicio` | data | Início da janela |
| 19 | `Vigencia_Fim` | data | Fim da janela |
| 20 | `Motivo_Vigencia` | texto, opcional | Por que a janela abriu ou fechou |

**Regras de preenchimento (do desenho, não do dicionário).** Os campos 7 a 11 só se preenchem para os tipos a que se aplicam (seção 4): a opção vale para os tipos que a lei deixa optar, o percentual residencial só para condomínio, o teste só para fundo de investimento. Não é uma restrição de banco: é validação do cadastro, para que um tipo novo possa entrar sem alterar a estrutura.

**Quem altera.** Só o usuário com permissão específica: uma linha em `Cad_Permissao` (módulo "Qualificação do participante", ações visualizar, criar e editar), na carga de perfis, como você decidiu para os tipos de baixa (Q113-10). A mudança de qualificação **nunca apaga** a anterior: fecha a janela e abre outra.

**Qualificação vigente na data do fato.** O Motor lê a qualificação **vigente na data do fato gerador** do documento, e não a de hoje; assim um período fechado reprocessa com a qualificação que valia.

# 4. O domínio aberto `qualificacao_cbs`: 30 tipos iniciais

Juntei as duas listas que as leituras do documento 70 propuseram (a do art. 105 e a da faixa de 200 a 258). **Decisões minhas de unificação**, marcadas porque você ainda não as viu: (a) `produtor_rural` é **um** valor, porque pessoa física ou jurídica já está em `Cad_Participante.Tipo_Pessoa`; (b) `tac` e `transportador_autonomo_pf` são o **mesmo** tipo, chamado `transportador_autonomo_carga`; (c) `plataforma_digital` **sai** da lista (seção 6); (d) `condominio_civil` entra por constar da síntese do art. 25 que fiz no Anexo A, e a leitura do artigo precisa confirmá-lo.

| Grupo | Tipos | Campos que se aplicam além do tipo |
|---|---|---|
| **A. Não contribuinte do art. 25 e sujeitos do art. 105** (12) | entidade_imune_isenta, plano_autogestao, previdencia_complementar_fechada, fundo_investimento, fundo_patrimonial, condominio_edilicio, condominio_civil, nanoempreendedor, consorcio, scp, socio_ostensivo_scp, outro_nao_contribuinte_art25 | Opção e renúncia: consórcio, SCP e os que a lei permitir. Percentual residencial: condomínios. Teste: fundo_investimento. Dispensa de registro: os que o ato listar |
| **B. Produção rural, transporte de carga e coleta** (8) | produtor_rural, produtor_rural_integrado, associacao_cooperativa_produtores_rurais, transportador_autonomo_carga, coletor_incentivado_pf, coletor_incentivado_associacao_cooperativa, entidade_congregadora, rerrefinador_coletor_anp | Motivo da condição (limite de receita no produtor rural); comprovante nos coletores e no rerrefinador |
| **C. Profissão, saúde, ciência, transporte coletivo e outros** (9) | profissional_autonomo_art_202, sociedade_profissional_art_202, entidade_saude_imune_cebas, fabricante_medicamento_tac_cmed, ict_sem_fins_lucrativos, fundacao_apoio_ict, prestador_transporte_coletivo_titulo_habilitante, associacao_clube_desportivo_filiado, sociedade_seguranca_cibernetica_socio_brasileiro | Comprovante e validade (CEBAS, título habilitante, filiação, registro) |
| **D. Administração pública** (1) | administracao_publica_direta_autarquia_fundacao | Nenhum além do tipo; o **tipo do ente** (União, estado, DF, município) vem de outro lugar (seção 5, item 2) |

Os nomes são **códigos** de `Cad_Classe_Sistema` e ganham descrição em português na carga. O nome `fabricante_medicamento_tac_cmed` e os demais da faixa 200 a 258 vêm da leitura do documento 70, e **não reli artigo por artigo** para esta versão; a carga só sai depois de o contador conferir cada tipo com o artigo que o sustenta (seção 8).

# 5. O que fica fora da entidade (e o que entra nas outras)

| # | Onde | O que | Por quê |
|---:|---|---|---|
| 1 | `Cad_Participante_Inscricao.Tipo_Inscricao` | Ganha o valor **`cnpj_pessoa_fisica`** (o número cabe em `Numero_Inscricao`, com vigência) | Art. 105, § 4º-A: a pessoa física contribuinte terá CNPJ próprio, além do CPF, a partir de 1º/1/2027. **A data é parâmetro (B0a)**; o formato do número ainda não saiu, então o ERP guarda os dois |
| 2 | `Cad_Participante_Situacao_Cnpj` | **+1 campo** `ID_Natureza_Juridica` (referência a `Cad_Natureza_Juridica`, opcional) | A compra governamental depende da natureza jurídica do comprador; hoje só a empresa própria (`Cad_Empresa`) a tem. O **tipo do ente** já está em `ID_Ente_Federativo` (`Cad_Ente_Federativo_Responsavel`, com `Tipo_Ente`). O B3 lê os dois |
| 3 | `Cad_Empresa_Perfil_Fiscal` | `Participa_Pnct` (booleano) **adiado para o B0b** | O programa e os selos dependem da LC 225/2026, que ainda não está no Project. Um booleano sem o texto seria chute |
| 4 | `Cad_Classe_Sistema` | Dois valores novos no domínio `campo_criterio_regra`: **`qualificacao_cbs_do_adquirente`** e **`qualificacao_cbs_do_fornecedor`** | É por onde o Motor de Regras lê a qualificação nos dois lados da operação. Carga de domínio, sem campo novo |
| 5 | `Cad_Classe_Sistema.Dominio` | Dois valores novos na lista fechada de domínios: `qualificacao_cbs` (e o de critério é o item 4) | A lista de domínios é uma enumeração; cada domínio novo é um valor |

# 6. O que **não** entra na qualificação

- **`plataforma_digital` e `importador`:** são **papéis comerciais**, e o documento 70 já os propunha como valores de `Cad_Participante_Classe.Classe`. O importador é do B1; a plataforma é do B7. Ficam lá.
- **MEI:** é porte (`Cad_Participante_Porte`).
- **O benefício do veículo (táxi, pessoa com deficiência, TEA):** é um **fato da compra**, com laudo e uso único, proposto pelo documento 70 como entidade da operação. É do B3, não do cadastro do participante.
- **A apuração do limite do produtor rural (R$ 3,6 milhões):** é movimento mensal, entidade do B5 (rural). **Escreve** nesta qualificação (`Origem` = `calculado_pelo_sistema`, `Motivo_Condicao` = `por_limite_de_receita`), mas não mora aqui.
- **O associado da cooperativa:** o `Indicador_Contribuinte_Cbs` do associado **é lido desta qualificação** quando o associado é um participante cadastrado; o B5 decide o que fazer com o associado que só tem documento (`Cad_Cooperativa_Associado.Documento_Associado`).

# 7. Quem lê, e o que isso desbloqueia

| Bloco | O que lê |
|---|---|
| **B0a** | Parâmetros da lei (limite residencial, prazo da opção, data do CNPJ da pessoa física) que esta entidade cita; **esta entidade não os guarda** |
| **B1** (comércio exterior) | Responsável na importação; classe importador |
| **B3** (governo e Zona Franca) | Tipo de ente e natureza jurídica para o redutor da compra governamental e a regra por tipo de ente |
| **B5** (setoriais) | Cooperado e produtor rural; clube desportivo filiado |
| **B4** (financeiro e saúde) | Plano de autogestão, previdência complementar fechada e fundos |
| **Motor de Regras** | Os dois critérios novos, em qualquer regra de CST, cClassTrib ou crédito presumido |

# 8. Efeito, se tudo for aceito

| Item | Efeito |
|---|---|
| Entidades | 922 para **923** (`Cad_Participante_Qualificacao_Cbs`) |
| Campos | 9.998 para **10.019** (20 da entidade + 1 em `Cad_Participante_Situacao_Cnpj`) |
| Chaves estrangeiras | 2.685 para **2.690**: 4 na entidade nova (`ID_Participante`, `ID_Tipo_Qualificacao`, `ID_Documento_Comprovante`, `ID_Usuario_Registro`) e 1 em `Cad_Participante_Situacao_Cnpj` (`ID_Natureza_Juridica`) |
| Domínios | +2 valores em `Cad_Classe_Sistema.Dominio`; carga de **30** tipos e de **2** critérios |
| Valores de enumeração | +1 em `Cad_Participante_Inscricao.Tipo_Inscricao` |
| Decisões | A numerar na consolidação (revisão 23, junto das respostas pendentes) |

# 9. Perguntas para você

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q116-1** | Aprova os **20 campos** da seção 3? Em especial os valores de `Motivo_Condicao` {por_natureza, por_limite_de_receita, por_opcao, por_ato_da_administracao}, que são **proposta minha** | Sim |
| **Q116-2** | Aprova os **30 tipos iniciais** da seção 4, com as quatro unificações (produtor rural único, `tac` igual a transportador autônomo, `plataforma_digital` fora, `condominio_civil` dentro)? | Sim |
| **Q116-3** | `plataforma_digital` e `importador` ficam em `Cad_Participante_Classe` (B7 e B1), e **não** na qualificação? | Sim |
| **Q116-4** (**respondida em 27/10/2026: sim**) | Acrescentar `ID_Natureza_Juridica` em `Cad_Participante_Situacao_Cnpj` (1 campo) e ler o tipo do ente de `ID_Ente_Federativo`, sem campo novo? | Sim |
| **Q116-5** (**respondida em 27/10/2026: sim**) | O CNPJ da pessoa física entra como valor `cnpj_pessoa_fisica` de `Tipo_Inscricao` (o ERP guarda CPF e CNPJ), com a data de início como **parâmetro do B0a**? | Sim |
| **Q116-6** | `Participa_Pnct` espera o B0b (LC 225)? | Sim |
| **Q116-7** (**respondida em 27/10/2026: sim**) | Só o usuário com permissão específica cria ou altera a qualificação (linha em `Cad_Permissao`), e a mudança fecha a janela anterior, sem apagar? | Sim |
| **Q116-8** (**respondida em 27/10/2026: sim**) | Se o tipo exige comprovante (CEBAS, título habilitante, filiação) e a linha está **sem comprovante ou vencida**, o Motor **sugere e o usuário confirma na linha** (como na lista legal, Q70-4), em vez de aplicar sozinho ou de bloquear? | Sugerir e confirmar |

**Para o contador (não bloqueia a aprovação dos campos):** conferir cada um dos 30 tipos com o artigo que o sustenta; confirmar se `condominio_civil` é qualificação do art. 25; e dizer se a condição `optante_regime_regular` vale para algum tipo além de consórcio e SCP.

# 10. Limites

- Os **30 tipos** e os **campos 5 a 11** vêm das leituras do documento 70 (Anexo A, linhas 45 e 118, entidade E1) e do documento 86 (seção 4); **não reli os artigos** do decreto para esta versão, e a associação de campo a tipo na seção 4 é minha.
- Os valores de `Motivo_Condicao` e a regra "o campo só se preenche para tal tipo" são **proposta nova**, não estão nos documentos anteriores.
- Não desenhei a **tela** nem a integração com a consulta à Receita (que traz natureza jurídica e situação do CNPJ); a qualificação **não vem** da consulta, é cadastro do ERP.
- A LC 225/2026, o Decreto 13.133/2026 e os Anexos I a XV da LC 214 **não estão** no Project; o B2 não depende deles, mas a carga de tipos pode ganhar valores quando chegarem.
- Contagens de campos e de chaves são do **cálculo sobre a revisão 22** e só valem depois da consolidação.
