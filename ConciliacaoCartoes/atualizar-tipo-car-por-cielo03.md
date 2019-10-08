# Introdução 

Com este recurso, o sistema automaticamente corrige tipo de contas a receber e valor de parcelas que estejam divergentes ao informado no arquivo de vendas de plano parcelado.

# Configuração

## Atualização de tipo de conta a receber

Para habilitar o recurso de alteração de tipo, é necessário marcar o campo correspondente no cadastro da financeira.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/2019-10-08-10_36_08-eSolution-Access-Center.png)

  Após isso, é necessário a criação e correta configuração dos tipos de conta a receber em `Finacneiro -> Cadastros -> Tipo de contas a receber` de acordo com as bandeiras dos cartões.


  Por exemplo, caso uma parcela conste no arquivo de conciliação da Cielo como `Visa Crédito`, deverá existir um tipo de contas a receber com a seguinte configuração:

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/2019-10-08-09_32_26-.png)

Sendo:

1. **Finalizadora**: Deverá obrigatoriamente constar o valor `Financeira`.
2. **Modalidade**: `Crédito` ou `Débito`, dependendo do caso. No exemplo deste artigo, deverá ser informado `Crédito`.
3. **Financeira**: Deverá constar a mesma `Financeira` usada na importação de arquivos no módulo de conciliação de cartões.
4. **Bandeira**: Esse campo já possui um pré-cadastro de diversas bandeiras, feito pelo sistema. Deverá ser informada a mesma bandeira do registro no arquivo de conciliação. No exemplo deste artigo, deverá ser informado `Visa`.

  Toda combinação de bandeira e modalidade deve ser cadastrada como um tipo de contas a receber para cada finalizadora utilizada. Caso o sistema não encontre um tipo de contas a receber que atenda o informado no registro do arquivo de conciliação, ele não alterará o tipo de conta a receber na parcela. Caso o sistema encontre mais de um tipo de conta a receber para a mesma configuração, o primeiro encontrado será utilizado.


## Atualização de valor

Necessário configurar os seguintes campos no cadastro de `Financeira` em `Financeiro -> Cadastros -> Financeira`:

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/10/2019-10-08-09_25_35-.png)

1. **Alterador de valor**: Uma alteração de valor feita através deste recurso gera um novo alterador de valor na parcela vinculada. Informe neste campo o alterador de valor que deve ser aplicado nestes casos.
2. **Filial**: Caso o alterador de valor informado em 1 exija filial, informe neste campo.
3. **Centro de custo**: Caso o alterador de valor informado em 1 exija centro de custo, informe neste campo.

Caso o alterador de valor (campo 1) não seja informado na financeira, o recurso de alteração de valor será considerado desativado (as parcelas manterão o valor salvo no sistema)


# Observações

Os recursos demonstrados neste artigo não têm efeito retroativo. A alteração de tipo e de valor é aplicada apenas no momento da importação do arquivo, da vinculação manual ou da sincronização de um arquivo previamente importado e apenas se todas as configurações estiverem corretas.
