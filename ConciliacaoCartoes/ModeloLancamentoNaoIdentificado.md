# Documentação do módulo Modelo para lançamento de movimentações não identificadas (usado na conciliação de cartões)

---

## Cenário

Este módulo foi desenvolvido com o objetivo de agilizar o lançamento de movimentações financeiras não identificadas durante a operação de conciliação de cartões de crédito/débito. É possível definir como cada movimentação é lançada, configurando operação financeira, destinação contábil (para contabilização) e aplicação de caixa (para fluxo de caixa), bem como o desmembramento entre as taxas de admnistração e antecipação em movimentações financeiras diferentes.

---

## Configuração e uso

### Módulo 621 - Modelo para lançamento de movimentações não identificadas
#### Financeiro -> Cadastros -> Modelo para lançamento de movimentações não identificadas
* Permissões para editar, excluir, imprimir e inserir

![Figura 1. Tela de cadastro de modelo, aba lançamento][modelo_lancamento]

A tela de cadastro de modelo define um padrão para lançamento automático das movimentações não identificadas oriundas do módulo de conciliação de cartões.
Os campos **Código** e **Nome** são necessários apenas para facilitar a localização do modelo desejado posteriormente. O campo **Conta financeira** define em que conta financeira é lançada a movimentação.
Com o cadastro de um modelo, é possível configurar que o crédito em conta (o valor creditado pela operadora de cartões) seja efetuado seguindo determinados critérios de aplicação caixa/operação financeira/destinação contábil. 
Na aba **Lançamento em conta** é definido como a movimentação financeira do valor creditado será lançada. Os campos com um * indicam campos obrigatórios com base nas regras definidas nos campos **Op. mov. financeira** e **Destino contábil**

![Figura 2. Aba taxa de administração][modelo_taxa_adm]

A aba **Taxa de administração** define como será feito o lançamento de uma movimentação financeira avulsa para taxa de admnistração (caso o campo **Lançar movimentação avulsa para taxa de administração** esteja marcado e o campo **Op. mov. financeira** esteja preenchido). Caso o campo **Op. mov. financeira** não seja informada, o sistema não gerará uma movimentação separada para a taxa e ela fará parte apenas do fluxo de caixa, através do campo **Aplicação caixa** e do processamento contábil através do campo **Destino contábil**. Os dados informados na aba **Lançamento em conta** definem o critério para informar ou não esses campos.


![Figura 3. Aba taxa de antecipação][modelo_taxa_antecipacao]

Através da aba **Taxa de antecipação**, de configuração similar à aba **Taxa de administração** é possível definir uma regra para a geração avulsa das taxas de antecipação (se houver).


No exemplo das imagens neste documento, uma movimentação seguindo as regras preenchidas ficaria da seguinte maneira:

![Figura 4. Conciciliação de cartões, movimentações não identificadas][mov_nao_identificada]

Após enviar a movimentação para **Movimentações não identificadas** durante uma conciliação de cartões, ao clicar na opção **Gerar movimentações**, as seguintes movimentações financeiras serão geradas:

![Figura 5. Movimentações financeira geradas][movimentacoes]


Ou seja, a taxa de antecipação foi desmembrada em sua própria movimentação financeira que segue a configuração informada no modelo.


![Figura 6. Destinação contábil da taxa de antecipação][destinacao]


![Figura 7. Aplicação caixa na movimentação financeira][aplicacao]


Com isso, a tarefa de baixas automáticas pode efetuar a baixa vinculando o valor à movimentação financeira principal, com a baixa tomando a seguinte forma:

![Figura 8. Baixa][baixa]

[modelo_lancamento]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/modelo_lancamento.png
[modelo_taxa_adm]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/modelo_taxa_adm.png
[modelo_taxa_antecipacao]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/modelo_taxa_antecipacao.png
[mov_nao_identificada]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/mov_nao_identificada.png
[movimentacoes]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/movimentacoes-1.png
[destinacao]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/taxa_antecipacao.png
[aplicacao]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/aplicacoes.png
[baixa]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/baixa-1.png
