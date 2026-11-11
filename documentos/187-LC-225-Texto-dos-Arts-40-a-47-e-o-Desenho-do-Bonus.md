# LC 225/2026, arts. 40 a 47 (texto oficial), e o que ele muda no desenho do bônus e dos selos: Documento 187

*Confere o texto da Lei Complementar nº 225, de 8 de janeiro de 2026 (PDF do Planalto, 23 páginas, impresso em 09/11/2026) contra o desenho dos selos e do bônus de adimplência da CSLL (documentos 140, 180, 181 e 185). Registra a aprovação das Q185-1 a Q185-3. Nada foi aplicado ao dicionário (revisão 34).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. O que recebi e como li

Você enviou o PDF da LC 225 sem mensagem e, em seguida, respondeu **"Q185-1 a Q185-3 Sim para todas"**. Li o PDF como resposta à **Q185-4** (o texto do art. 41) e à parte do texto da lei da **Q180-3**. O texto que recebi é o do Planalto, com a ressalva de que não substitui o publicado no DOU de 09/01/2026. Li inteiros os arts. 27 a 29 (adesão e exclusão do Confia), 40 a 47 (selos) e 58 (vigência), e passei os olhos nos arts. 30 a 32 (Sintonia). **O ato da Receita que regulamenta o Confia continua sem ser enviado**: o art. 29 manda a RFB disciplinar a adesão e a exclusão, e não encontrei esse ato no que você enviou.

# 2. O texto do art. 41 confere com o dicionário

Com o texto da lei na mão, as regras do bônus que antes só tinham a IN e o resumo que você colou têm agora a fonte primária. **Todas conferem**:

| Regra do art. 41 | Onde está no dicionário | Situação |
|---|---|---|
| Caput e inciso I: selos Confia e Sintonia dão o bônus de 1% no pagamento à vista da CSLL até o vencimento (o OEA não dá) | `Mov_Bonus_Adimplencia_Csll.ID_Selo` (o selo OEA não dá o bônus); `Pago_A_Vista_Ate_Vencimento` | Confere |
| § 1º: só depois de 12 meses de detenção do selo | `Meses_Minimos_Selo`; `Meses_Selo_Mantido` | Confere |
| § 2º: +1 ponto por período adicional de 12 meses, até 3% | `Incremento_Percentual`, `Meses_Por_Periodo`, `Percentual_Maximo` | Confere |
| § 3º: R$ 250 mil, R$ 500 mil e R$ 1 milhão por ano | `Limite_Anual_Ano_1`, `_Ano_2`, `_Ano_3_Em_Diante` | Confere |
| § 4º: a parcela não aproveitada não passa ao período seguinte | `Valor_Bonus_Nao_Aproveitado` | Confere |
| **§ 5º: o bônus não entra na base de cálculo de nenhum tributo** | Sem campo; vale para a ECF (`Valor_Desconto_Na_Baixa`, Q185-C1) | Confere com o documento 185, item 3.2; agora é **a lei**, e não só a IN |
| § 6º: não vale para o Simples Nacional | `Aplica_Simples_Nacional` (falso) | Confere |
| Art. 40, § 1º: selos Confia e Sintonia valem 1 ano e são renovados sem pedido enquanto as condições durarem | `Mov_Selo_Conformidade.Data_Validade` e nova linha por renovação | Confere |
| Art. 44: cinco hipóteses de cancelamento do Selo Sintonia; art. 43: Confia cancelado pela exclusão (art. 28) | Domínio `motivo_cancelamento_selo` | Confere |
| Art. 28, I a III: três motivos de exclusão do Confia | Domínio `motivo_exclusao_programa` | Confere |

**Vigência (art. 58, I).** Os programas Confia e Sintonia e os selos (arts. 19 a 32 e 40 a 47) entram em vigor **90 dias depois da publicação** (DOU de 09/01/2026), ou seja, em **09/04/2026**. A carga do `Cad_Parametro_Bonus_Adimplencia` tem vigência desde 09/04/2026, que na revisão 29 foi "conta minha". **Agora é a data da lei**: ao consolidar, tiro a ressalva.

# 3. O que o texto da lei acrescenta ou ajusta

1. **A ciência prévia de indício de infração (art. 42) vale para os dois selos, Confia e Sintonia.** O documento 185 tratou só do Sintonia (art. 14 da IN). O art. 42, I, dá o direito a **todo detentor de selo Confia ou Sintonia**; o § 1º dá 60 dias da ciência para regularizar sem a multa de mora do art. 61 da Lei 9.430; o § 2º diz que, vencido o prazo, as multas correm desde o vencimento original, **"ressalvadas as disposições específicas do Confia"**. A entidade da Q185-2, que você aprovou, deve ligar-se a `Cad_Empresa_Programa_Conformidade` (que já diz se é Confia ou Sintonia), e não só ao Sintonia. **Sem campo novo além dos já propostos.**
2. **O art. 42, II, dá "informação para fins de renovação das certidões de regularidade fiscal"** ao detentor do selo. É informação que a Receita presta; o ERP **não registra** (fica fora, como as prioridades do art. 41, II a IV, e do art. 31).
3. **O Confia dá os benefícios do maior grau do Sintonia e tem preferência (art. 46).** Não precisa de classificação do Sintonia: o `Cad_Empresa_Programa_Conformidade` do Confia dá o selo por si. A preferência nas prioridades do art. 31 e do art. 41, III e IV, é benefício administrativo, **fora do dicionário**.
4. **A estimativa mensal não aparece no texto da lei.** A exclusão do bônus nas estimativas vem **só da IN 2.316 (art. 12, § 1º, I), que regulamenta o Sintonia**. Para o detentor do **Confia** não há ato. A regra do Motor aprovada na Q185-1 vale como **aviso** para os dois selos até o ato do Confia chegar (leitura minha, Q187-1).
5. **Readmissão no Confia (art. 28, § 7º).** O excluído pode ser readmitido **após 2 anos da publicação do ato declaratório de exclusão**, cumpridos os requisitos de adesão. O dicionário já tem `Data_Ato_Exclusao` e `Cad_Empresa_Programa_Conformidade` com vigência: a readmissão é uma **nova versão do programa da empresa**. Proposta: aviso do Motor (sem bloqueio) quando a data da nova admissão for menor que 2 anos depois da `Data_Ato_Exclusao` (Q187-2).
6. **A exclusão do Confia tem termo inicial na data do fato (art. 28, § 3º)** e volta a majoração da multa do art. 44 da Lei 9.430 (§ 5º). O `Data_Ato_Exclusao` e a `Vigencia_Fim` já distinguem as duas datas; a multa é do lado do contador, e o ERP não calcula.

# 4. Aprovação das Q185-1 a Q185-3

Você aprovou as três (D-N500). O que entra no **próximo "consolidar"**, com os ajustes dos itens 3.1, 3.4 e 3.5:

| Nº | O que entra |
|---|---|
| **Q185-1** | Duas regras novas do Motor, como **aviso** (sem estimativa mensal; o selo conta até o fim do mês do cancelamento ou da expiração) e a carga provisória dos cinco valores do Sintonia (A+ a D, art. 8º da IN) em `classificacao_programa_conformidade`, com a faixa da nota no texto |
| **Q185-2** | Entidade nova para a **ciência do indício de infração**: empresa, programa (Confia ou Sintonia, por `ID_Empresa_Programa`), data da ciência, data limite digitada, situação, número do processo. O ERP só registra, sem contar o prazo (padrão `Mov_Condicao_Devedor_Contumaz`) |
| **Q185-3** | Avisos do Motor com os indicadores do Sintonia (Anexo da IN), por nota estimada e por domínio, sem programar e sem bloquear |

# 5. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q187-1** | As duas regras da Q185-1 (sem bônus em estimativa mensal; selo vale até o fim do mês do cancelamento) valem como aviso também para o selo **Confia**, até haver ato próprio? | **Sim**, só aviso |
| **Q187-2** | Aviso do Motor quando a readmissão no Confia for anterior a 2 anos da exclusão (art. 28, § 7º)? | **Sim**, só aviso, sem campo novo |
| **Q187-3** | Você tem o **ato da Receita que regulamenta o Confia** (art. 29)? Sem ele o Confia fica com a lei e o que a IN do Sintonia permite aproveitar | Enviar, se existir |

# 6. Limites

O PDF é o texto do Planalto e traz a ressalva de que não substitui o DOU. Li com atenção só os arts. 27 a 29, 40 a 47 e 58 (adesão e exclusão do Confia, selos e vigência); os arts. 30 a 32 (Sintonia) só de relance, porque a IN 2.316 já os regulamenta; os demais (devedor contumaz, OEA e a parte do código de defesa) já estavam desenhados e não foram relidos. O Confia segue sem ato da Receita; o Sintonia tem a IN 2.316/2026.
