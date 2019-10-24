# Documentação Módulo Programa de Férias (Férias Fácil)


___


## Cenário


O módulo de Programa de Férias foi desenvolvido para a atender ao seguinte caso de uso:

1. O cliente adquire um carnê com um cartão de consumo;
2. O carnê possui um ou mais números gerados aleatoriamente, utilizados para sorteio;
3. Os carnês que o cliente paga são revertidos em crédito em conta que podem ser utilizados para consumo no parque;
4. O valor revertido em crédito em conta pode ser configurável como apenas um percentual do valor total pago pelo cliente, até que todas as parcelas do carnê tenham sido pagas

---

## Configuração e uso

### Módulo 598 - Série de programa de férias
#### Programa de férias -> Cadastros -> Série de programa de férias
* Permissões para editar, excluir, imprimir e inserir

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/serie-programa-ferias.png)

1. Identificador da série (preenchido automaticamente)
2. Código da série (preenchido automaticamente ou manualmente, dependendo de configuração prévia de código. Códigos numéricos de até dois dígitos serão usados para a geração do número do cartão de consumo)
3. Nome da série (preenchido manualmente)
4. Filial (por padrão, recomendada a filial logada. A série só será utilizável na filial informada neste campo)
5. Status (preenchido automaticamente de acordo com a situação da série). Pode assumir os seguintes valores:
    - **Cancelado**: A série está cancelada e não será mais possível utilizá-la
    - **Pendente**: A série está pendente de conclusão e não pode ser utilizada pelos outros módulos, útil quando a série não está totalmente cadastrada
    - **Concluída**: A série está pronta para ser usada no restante do programa de férias e, por isso, não pode mais ter seus cadastro alterado
6. Campo para impressão do carnê
7. Campo para impressão do carnê
8. Campo para impressão do carnê

Os campos 6, 7 e 8 são exibidos na impressão do carnê conforme a seguinte imagem:

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-16-11_21_05-Window.png)

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/serie-programa-ferias-financeiro.png)

1. Cliente que será informado nos recebimentos e boletos gerados que ainda não foram vendidos ao cliente final.
2. A operação financeira que será usada para gerar os recebimentos dos carnês. É limitado apenas à operações que não contabilizem no lançamento, pois é desejável gerar contabilização apenas de carnês vendidos.
3. O tipo de recebimento que será usado para gerar os recebimentos dos carnês. Informar um tipo pré-configurado como `Boleto` para a geração dos carnês a serem impressos ser feita corretamente.
4. O PDV que será usado para gerar os recebimentos dos carnês
5. A quantidade de parcelas que serão geradas no carnê. Serão gerados esse número de recebimentos e de boletos vinculados ao carnê gerado
6. O valor de cada parcela gerada. Calculado automaticamente com base nos valores informados nos campos _6_ e _7_
7. O valor total do carnê. Calculado automaticamente com base nos valores informados nos campos _5_ e _6_

Ao alterar a quantidade de parcelas (campo _5_). Toda a cadeia de progressão de crédito será atualizada de acordo com a quantidade de parcelas informada. Uma notificação será exibida comunicando o usuário da alteração.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/serie-programa-ferias-sorteio.png)

1. Os números para sorteio serão gerados a partir do valor informado neste campo
2. A quantidade de números para sorteio gerados para cada carnê. Esses números são pré-gerados no momento da conclusão da série e, por isso, quanto maior o valor informado nesse campo, mais tempo levará a conclusão da série.
3. A quantidade de números que será gerada para cada carnê
4. A quantidade de dígito em cada número gerado. Tem como finalidade a formatação desses números na impressão dos carnês

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/serie-programa-ferias-progressao.png)

As parcelas desta aba são preenchidas de acordo com a quantidade de parcelas informada na aba `Financeiro`. O campo `Percentual liberado` é editável e já começa com valores percentuais lineares preenchidos.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/serie-programa-ferias-liberacao.png)

Configurar a quantidade de dias para liberação de crédito de acordo com a `Finalizadora` do Tipo de contas a receber de cada parcela do carnê, conforme desejado. Uma quantidade de dias igual a 180, significa que após 180 dias do pagamento de uma parcela com a finalizadora informada a conta de consumo será aberta e os valores serão lançados.

### Módulo 612 - Campanha de programa de férias
#### Programa de férias -> Cadastros -> Campanha de programa de férias
* Permissões para editar, excluir, imprimir e inserir

![Tela de cadastro de Campanha de programa de férias - aba Geral][cpfgeral]

1. Descritivo ou nome da campanha
2. Filial onde a campanha é aplicada
3. A série da campanha, dados para a geração de carnês dependem dessa série
4. O status da campanha, pode assumir os seguintes valores:
    - **Pendente**: A campanha ainda não está válida, útil em caso de cadastros parciais
    - **Cancelada**: A campanha está cancelada e não pode mais ser usada para gerar carnês
    - **EmProcessoVenda**: A campanha teve seus carnês gerados e já estão prontos para serem vendidos. Quando apenas alguns carnês da campanha estiverem vendidos, a campanha também assume esse status
    - **Finalizado**: A campanha já teve todos os seus carnês vendidos e não pode mais ser utilizada para geração de novos carnês ou vendas.
5. A data de vencimento da primeira parcela gerada nos carnês. As parcelas subsequentes têm seu vencimento acrescido de 1 mês para cada parcela
6. A quantidade de carnês no total que será gerada nessa campanha ao concluí-la
7. O número do primeiro cartão de consumo dos carnês. Cada carnê gerado incrementará em 1 esse número

![Tela de cadastro de Campanha de programa de férias - aba Carnês][cpfcarnes]

Caso algum carnê tenha sido gerado nessa campanha, suas informações básicas serão exibidas nessa tela. É possível acompanhar a situação das vendas de cada carnê gerado na campanha

---

### Módulo 599 - Lançamento de programa de férias
#### Programa de férias -> Movimentação -> Lançamento de programa de férias
* Permissões para imprimir, concluir venda e  visualizar histórico financeiro (permite ver e baixar/renegociar as parcelas do carnê)

![][lpfmodulo]

Através do módulo de lançamento de programa de férias é possível consultar os carnês gerados. Carnês que se encontram no status "DisponivelVenda" podem ser vendidos neste módulo.

Para lançar uma nova venda, selecionar o carnê e escolher a opção _Lançar venda_

Clicar duas vezes num carnê abre uma tela com mais informações de um carnê específico

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/carne.png)

1. Identificador único do carnê
2. Status do carnê, pode apresentar os seguintes valores:
    - **DisponivelVenda**: O carnê pode ser vendido ao usário final, estando apenas salvo no banco de dados
    - **Vendido**: O carnê já se encontra vendido ao usuário final e não pode mais ser alterado, apenas consultado
    - **Cancelado**: O carnê foi cancelado/inutilizado
3. A filial do carnê
4. A campanha de programa de férias que gerou este carnê
5. O cliente que adquiriu o carnê. Caso o carnê esteja _DisponivelVenda_ o cliente será o mesmo informado na série de programa de férias como cliente padrão dos carnês
6. A data da venda, caso houver
7. O usuário vendedor, informado no momento de lançar a venda. Será exibido apenas se o carnê foi vendido. O vendedor deverá ser cadastrado através do módulo `Cargo pedido pessoa`. Seu funcionamento está fora do escopo desta documentação.
8. O número do cartão de consumo deste carnê, gerado conforme configurado na campanha de programa de férias que gerou este carnê. Seguirá o formato SS00000D, sendo `SS` o código da série (caso seja numérico e entre 00 e 99, caso contrário será preenchido com zeros), `00000` o número sequêncial (incrementado a cada carnê) e `D` o dígito verificador, calculado por módulo 10.
9. Comando para efetuar o lançamento de uma nova venda, caso o carnê esteja disponível

![Tela de lançamento de programa de férias - aba Números para sorteio][lpfnum]

Nesta tela é possível consultar os números para sorteio gerados para o carnê em específico.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/carne-financeiro.png)

Nesta tela é possível visualizar e efetuar baixas/renegociações do financeiro do carnê. Está disponível apenas para usuários que possuem a permissão de visualizar financeiro. A opção de baixar é habilitada apenas em carnês vendidos. Ao clicar em `Baixar` a tela de baixa padrão de contas a receber é carregada com todas as parcelas pendentes do carnê. Seu funcionamento está além do escopo desta documentação, visto que é uma tela pertencente ao módulo financeiro.

![Tela para lançamento de nova venda de carnê][lpfvenda]

1. A campanha do carnê a ser vendido
2. O número do cartão de consumo do carnê a ser vendido
3. A data da venda a ser lançada
4. O cliente que está adquirindo o carnê através dessa venda. Ao lançar a venda, o cliente informado neste campo será propagado para os recebimentos gerados para o carnê bem como a qualquer boleto derivado. Gerando uma remessa de alteração de dados caso a remessa do boleto já tenha sido transmitida para o banco
5. O vendedor que efetuou a venda, cadastrado pelo módulo `Cargo pedido pessoa`


---

## Tarefas e integração com Portal

Para o lançamento de valores em conta do cliente, duas tarefas precisam ser configuradas:
No momento, apenas a tarefa de integração com o portal está implementada.

Para que a abertura e lançamento de conta funcionem com integração com o Portal, deve ser feita a configuração da ApiWebrest conforme a [configuração para alteração de proprietário de cota](http://conhecimento.esolution.com.br/2018/10/06/alteracao-de-proprietario-accesscenter-para-o-portal-2/).

* O tipo de recebimento informado no cadastro de Série de programa de férias deve possuir a tag **PORTAL** informada com o valor igual ao Id do recebimento do portal que será usada para efetuar o lançamento em conta.
* O pdv informado no cadastro de Série de programa de férias deve possuir a tag **PORTAL** informada com o valor igual ao Id do Pdv equivalente do Portal.

### Tarefa para abertura de contas

![Tarefa para abertura de conta][tarefa_abertura]

Informar na aba _Filiais_ as filiais que lançam programa de férias

### Tarefa para lançamento em conta

![Tarefa para lançamento em conta][tarefa_lancamento]

Informar na aba _Filiais_ as filiais que lançam programa de férias

Como resultado, o lançamento em conta aparece no controle de caixa no Portal, conforme imagem:

![Controle de caixa Portal][portal]


[portal]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/lancamentoportal.jpg
[cadastro_serie_programa_ferias]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/serie_programa_ferias.png
[spf_financeiro]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/spf_financeiro.png
[spf_sorteios]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/spf_sorteios.png
[spf_progress]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/spf_progress.png
[cpfgeral]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/cpf_geral.png
[cpfcarnes]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/cpf_carnes.png
[lpfmodulo]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/lpfmodulo.png
[lpfgeral]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/lpf1.png
[lpfnum]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/lpf2.png
[lpfvenda]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/lpfnovavenda.png
[tarefa_abertura]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/tarefa_abrir_conta.png
[tarefa_lancamento]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/tarefa_lancar_conta.png
[spf2]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-16-11_26_21-Window.png
[carne]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-16-11_21_05-Window.png
