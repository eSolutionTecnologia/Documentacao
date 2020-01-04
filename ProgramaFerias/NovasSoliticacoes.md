# Alterações requisitadas em 17/09/2019

## 1. Exportar os numeros dos carnês (número do cartão)

Necessidade de enviar uma planilha do Excel para a empresa que confeccionará os cartões de consumo, contendo uma coluna de número de sequência e o número do cartão desejado.

Exemplo:


| Sequência | Número do cartão |
| :-------: | :--------------: |
|         1 |              101 |
|         2 |              102 |
|         3 |              103 |


Exibir o número do cartão e o número sequencial na tela de Lançamento de Programa de Férias pode atender essa requisição.

## 2. Alterar a geração do número do cartão

Hoje o número do cartão é apenas um número sequêncial, alterar para o formato XXYYYYYYZ onde XX é o código da série, YYYYYY é o número sequêncial e Z é um dígito verificador.

## 3. Alterar a opção de liberar após X dias
  
  Necessário ter essa opção configurada de acordo com o tipo de contas a receber (ou a finalizadora do tipo de contas a receber), pois pagamentos em boleto são liberados após 1 ano, enquanto pagamentos em cartão/cheque são liberados após 6 mêses apenas.
  O tipo de contas a receber, portanto, deverá ser informado ao lançar a venda, porém os carnês devem ser gerados previamente.
  
## 4. Remessa apenas dos carnês vendidos

Criação de recurso para filtrar apenas boletos vendidos quando enviar a remessa para o banco. Atualmente enviaria todos os boletos (inclusive os ainda não vendidos que estariam no nome da empresa).

## 5. Montar a progressão de uso de acordo com o total de parcelas informado

  Desta maneira não é necessário adicionar um registro na progressão de uso, apenas editar os valores percentuais de todas as parcelas.
  
## 6. Consultar o estado financeiro do carnê na recepção

  Atualmente só é possível consultar pelo Access Center, a recepção teria que usar os dois sistemas ou desenvolver um recurso no Portal.
  
   Pesquisar carnê por nome, número do cartão, série, campanha...
   Exibir dados das parcelas. Número da parcela, número do carnê, vencimento, valor, valor pendente, valor pago, status, data de pagamento.


## 7. Clientes que pagam boleto após o vencimento

  Liberar o crédito para consumo retroativo.


## 8. Cadastro de vendedor 
  
  Hoje é um usuário do sistema, mas é um cadastro bem mais simples no portal. Importar esse vendedor ou cadastrar novamente (cadastrar novamente impedirá a criação de dados obsoletos que estão cadastrados no portal). Alterar no sistema para usar o usuário do sistema de comissionamento (CargoPedidoPessoa), pode usar um simples cadastro de pessoa. No portal o vendedor é cadastrado em `Sócio -> Vendedor`

## 9. Possibilidade de controlar o vendedor que está com carnês para vender

  Os carnês são enviados para o vendedor, deve ser possível controlar qual vendedor está com qual carnê. Possibilidade de requisitar de volta carnês não vendidos que estão de posse de um vendedor. Com isso é possível controlar a venda e o estoque de carnês.

## 10. Possibilidade de pagar o carnê na recepção

  Mesmo caso do item 6. Não seria possível realizar o pagamento do carnê no Portal. Usando o Access Center para realizar essa venda acabaria gerando dois controles de caixa (lançamentos da recepção no caixa do Portal, lançamentos de Férias Fácil no caixa do Access Center)

## 11. Pagamento de carnê em conjunto às parcelas

  É possível que um cliente compre o carnê e já quite as parcelas no ato da venda, num cartão de crédito, por exemplo. O valor da venda do carnê (atualmente R$ 40,00) deve ser transferido para o vendedor nesses casos, pois o lançamento no cartão será único (o valor da venda + o valor das parcelas)
