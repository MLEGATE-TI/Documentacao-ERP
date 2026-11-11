# IN RFB nº 2.316/2026 (Sintonia) e o Bônus de Adimplência da CSLL: Documento 185

*Confere a Instrução Normativa RFB nº 2.316, de 25/03/2026 (visão multivigente, com as alterações da IN RFB nº 2.339, de 21/08/2026), contra o desenho do selo e do bônus de adimplência da CSLL (documentos 140, 180 e 181). Nada foi aplicado ao dicionário (revisão 33).*

Mlegate · Alberto Beyeler · Novembro de 2026

# 1. O que recebi e como li

Você enviou o PDF da IN RFB 2.316/2026 sem mensagem. Li como a resposta à **Q180-3** ("o ato da Receita que regulamenta o bônus ou o texto do art. 41 da LC 225"). Se era outra coisa, me diga. A norma regulamenta o **Sintonia** (arts. 30 a 32, 40 a 47 e 58 da LC 225) e traz, nos arts. 12 e 13, o bônus de adimplência fiscal do **detentor do Selo Sintonia**. Ela **não** regulamenta o Confia nem o OEA, que também dão o selo e o bônus pelo art. 41 da lei. Na sequência você colou uma **tabela-resumo do art. 41 da LC 225** (desconto inicial de 1% no pagamento à vista da CSLL até o vencimento; carência de 12 meses de detenção do selo; mais 1 ponto a cada 12 meses, até 3%; limite anual de R$ 250 mil, R$ 500 mil e R$ 1 milhão; parcela não aproveitada não passa ao período seguinte), com links para o Planalto. As cinco regras **conferem** com a IN e com o dicionário. **É um resumo, e não o texto da lei**: não consegui abrir a página do Planalto daqui, e o resumo não traz os parágrafos sobre estimativa, Simples Nacional e base de cálculo. O texto do art. 41 continua fora do Project; a IN o repete nos pontos abaixo.

# 2. O que a IN confirma no desenho

| Regra da IN | Onde está no dicionário | Situação |
|---|---|---|
| Art. 12, I: desconto de 1% no pagamento à vista da CSLL devida, até o vencimento | `Cad_Parametro_Bonus_Adimplencia.Percentual_Inicial`; `Mov_Bonus_Adimplencia_Csll.Pago_A_Vista_Ate_Vencimento` | Confere |
| Art. 12, § 1º, IV: só depois de 12 meses de detenção do selo | `Meses_Minimos_Selo` (12); `Meses_Selo_Mantido` | Confere |
| Art. 12, § 1º, III: não vale para o Simples Nacional | `Aplica_Simples_Nacional` (falso) | Confere |
| Art. 13: +1 ponto a cada 12 meses, até 3% | `Incremento_Percentual`, `Meses_Por_Periodo`, `Percentual_Maximo` | Confere |
| Art. 13, § 1º: limites anuais de R$ 250 mil, R$ 500 mil e R$ 1 milhão | `Limite_Anual_Ano_1`, `_Ano_2`, `_Ano_3_Em_Diante` | Confere |
| Art. 13, § 2º: a parcela não aproveitada não passa ao período seguinte | `Valor_Bonus_Nao_Aproveitado` | Confere |
| Art. 10, § 2º e § 3º: selo de 1 ano a partir do mês seguinte ao da divulgação, renovado sem pedido se o contribuinte for "A+" no mês seguinte ao da expiração | `Mov_Selo_Conformidade.Data_Validade` e nova linha por renovação | Confere |
| Art. 15: cancelamento de ofício em 5 hipóteses (medida cautelar fiscal; inadimplência após intimação; falência ou extinção; cadastro irregular não regularizado em 30 dias; devedor contumaz) | Domínio `motivo_cancelamento_selo`, com os mesmos cinco valores | Confere |
| Art. 4º, parágrafo único, II: MEI e Simei fora; art. 4º, III: Simples Nacional dentro do programa | Habilitação do programa por empresa | Confere |

Com isso, os valores da lei do `Cad_Parametro_Bonus_Adimplencia` têm agora **uma segunda fonte** (a IN, arts. 12 e 13), além do art. 41 da LC 225. Continuam provisórios até o contador validar.

# 3. O que a IN muda ou acrescenta

1. **O bônus não vale para estimativa mensal (art. 12, § 1º, I).** Responde, em parte, ao que a Q140-5d perguntava. `Mov_Apuracao_Irpj_Csll.Tipo_Apuracao` já distingue `estimativa_mensal`. **Regra nova do Motor** (aviso, não bloqueio): não calcular o bônus quando o `Tipo_Apuracao` da apuração é `estimativa_mensal`. Sem campo novo.
2. **O bônus não entra na base de cálculo de nenhum tributo (art. 12, § 1º, II).** Responde, em parte, à Q140-6b (exclusão na Parte A, presumido e PIS/Cofins). Para a **ECF**, isso reforça o seu pedido de registrar o desconto na baixa: o valor de `Valor_Desconto_Na_Baixa` é o que o contador precisa para **excluir** da base. A conta contábil, o momento e a linha da ECF continuam com o contador (Q140-6a, 6c, 6d e 6e). **Minha leitura anterior** ("redução da despesa de CSLL") fica **mantida, mas sujeita à exclusão**: o lucro contábil sobe pelo bônus e a base fiscal não.
3. **A perda do selo corta o bônus a partir do mês seguinte (art. 12, § 2º).** O cancelamento ou a expiração tem efeito a partir do **mês seguinte**, salvo renovação. **Regra nova do Motor:** o selo conta para o bônus até o fim do mês do cancelamento ou da expiração. Sem campo novo (`Data_Cancelamento` e `Data_Validade` bastam).
4. **A escala do Sintonia (art. 8º):** "A+" nota final de 0,995 (99,5%) ou mais; "A" de 0,970 a 0,994; "B" de 0,900 a 0,969; "C" de 0,700 a 0,899; "D" abaixo de 0,700. Só o "A+" dá o selo (art. 10). **Proposta de carga:** cinco valores do domínio `classificacao_programa_conformidade` (hoje "sem carga") para o Sintonia, com a faixa da nota no texto, provisórios. As faixas do Confia e do OEA continuam sem fonte.
5. **Aviso prévio de inconformidade (art. 14).** O detentor do selo recebe antes informação sobre indício de infração e pode **regularizar em 60 dias, contados da ciência**, sem a multa de mora do art. 61 da Lei 9.430; vencido o prazo, a multa corre desde o vencimento original (§ 2º). Não vale nos indícios de sonegação, fraude ou conluio nem nos pedidos de restituição ou compensação com indício de falsidade (§ 3º). **O dicionário não tem lugar para registrar essa ciência e o prazo** (pergunta Q185-2).
6. **Os indicadores do Sintonia (Anexo Único)** são todos calculáveis com dados que o ERP já tem: entrega de DCTF, PGDAS-D, ECF, EFD-Contribuições e DCTFWeb (assiduidade e pontualidade); divergência entre DCTF e ECF, e entre DCTF e EFD-Contribuições; receita declarada contra documentos fiscais (a receita declarada vezes 1,05 dividida pela dos documentos, limitada a 1); estabilidade das retificadoras (5% no PGDAS-D e 20% nas demais, 180 dias); pagamento com juros e multa até 20% da arrecadação; adimplência de IRPJ, CSLL, PIS e Cofins. **Proposta:** registrar como **avisos do Motor, sem programar** (nota estimada por mês e domínio, nunca bloqueio), pelo padrão da Q183-10 (pergunta Q185-3). Os redutores da nota de consistência (0,05 por procedimento fiscal encerrado com crédito ou com multa isolada, e 0,2 por representação penal) vêm de dados que o ERP não tem; ficam fora.
7. **Prioridades do selo (art. 11) e benefícios não tributários (art. 12, II a IV)**, como a vedação ao arrolamento de bens e a preferência de contratação em licitação: ficam fora do dicionário (benefícios administrativos, não calculados).

# 4. O que continua aberto

| Pergunta | Situação |
|---|---|
| **Q180-3** (o texto do ato) | Respondida pela IN para o **Sintonia**, e o resumo do art. 41 que você colou confere; falta o ato do **Confia** e o texto da lei, se você tiver |
| **Q140-5b** ("à vista" é só a cota única?) | Não respondida: a IN diz só "pagamento à vista... até a data de vencimento". Segue para a Receita (pergunta 26 do documento 179) |
| **Q140-5d** (estimativas abatem o valor total da guia ou o pago?) | A IN resolve que o bônus **não incide nas estimativas**, mas não diz se o ajuste anual abate o valor da guia ou o pago. Segue para a Receita |
| **Q140-5e** (meses de selo até o vencimento ou o pagamento; ordem do limite) | Não respondida pela IN (o art. 12 usa "o pagamento à vista até a data de vencimento"). Segue para a Receita |
| **Q140-6a a 6e** | Fica com o contador, com o dado novo do item 3.2 |

# 5. Perguntas

| Nº | Pergunta | Recomendação |
|---|---|---|
| **Q185-1** | Aprova as regras novas do Motor (sem estimativa mensal; selo vale até o fim do mês do cancelamento) e a carga das cinco classificações do Sintonia, provisória? | **Sim** |
| **Q185-2** | Quer registrar a **ciência do indício de infração** e o prazo de 60 dias do art. 14 (entidade nova de poucos campos: empresa, programa, data da ciência, data limite digitada, situação, número do processo)? O ERP só registra, sem contar o prazo | **Sim**, pelo padrão da contumácia (`Mov_Condicao_Devedor_Contumaz`) |
| **Q185-3** | Registra os avisos do Sintonia (item 3.6), sem programar? | **Sim** |
| **Q185-4** | Você tem o ato do **Confia** e o **texto** do art. 41 da LC 225 (a tabela que você colou é resumo)? | Enviar o ato do Confia e o PDF ou texto da LC 225, se tiver |
| **Q185-C1** | (contador) Com o bônus fora da base de qualquer tributo (art. 12, § 1º, II), qual é a conta do bônus, o momento do reconhecimento e a linha da ECF da exclusão? | Reduzir a despesa de CSLL e excluir na Parte A; o contador confirma |

# 6. Limites

O PDF é a visão multivigente de 09/11/2026 e traz o aviso de que não substitui o texto publicado. Não li a IN RFB 2.339/2026 em separado: usei as alterações marcadas nesta visão (arts. 6º, § 5º, 9º, 10, 14 e itens 4.1.6 e 4.1.7). Não tenho o texto da LC 225 (arts. 30 a 47); a conferência é entre a IN e o desenho que já existe. As faixas do domínio de classificação do Confia e do OEA seguem sem fonte.
