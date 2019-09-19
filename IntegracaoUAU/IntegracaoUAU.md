# Configuração de integração UAU

## Configurações de cadastros 
Configurar no Access Center os códigos dos blocos `(Empreendimento -> Cadastros -> Bloco)` de acordo com os códigos equivalentes das Obras no UAU.

  ![][blocos]

Cadastrar também um cliente com o CNPJ igual ao CNPJ cadastrado na empresa da venda no UAU. Esse cadastro será usado para definir o proprietário de uma cota que teve sua venda cancelada (ou seja, uma cota disponível) como a empresa.

## Configurações no módulo de integração
Acessar o módulo de Integração UAU `(eSolution -> Integrações -> Integração UAU)` e clicar na opção `Configurar integração` para abrir a tela a seguir:

  ![][configuracoes]

1. **API**: Configurar de acordo com a versão da API do UAU instalada. Para versões superiores à `10.5`, usar a opção `REST`, para versões anteriores, usar `SOAP`

2. **Usuário UAU**: O login (nome de usuário) fornecido para uso na integração. Esse login é configurado no UAU

3. **Senha**: A senha do Usuário UAU

4. **Endereço do serviço**: O endereço da API UAU, provavelmente terá o formato `http://127.1.1.1:8080/uauAPI/`

5. **Obras a integrar**: O código das Obras do UAU que deverão ser integradas. Obras que não estiverem nessa lista serão ignoradas. Deve conter o código da obra, sem espaços e separado por vírgulas (se houver mais de uma). Exemplo `OBRAB,OBRAC`

6. **Iniciar a partir de**: A data inicial, usada como base para buscar as vendas no UAU. A integração irá buscar apenas vendas feitas ou alteradas no UAU a partir dessa data.

7. **Data de int. pessoa**: Usado na integração de dados cadastrais de clientes. Não é necessário para a integração das vendas, pois a mesma já atualiza os dados cadastrais de proprietários no momento que a venda é integrada.

8. **Última integração**: Não é necessário configurar, o processo de integração usa essa data como base para buscar novas vendas. Esse campo será incrementado a medida que a integração roda, até ficar com o valor igual a data atual.

9. **Qtd. max. tentativas**: A quantidade máxima de tentativas da integração para uma determinada venda. Vendas que não conseguirem ser integradas após essa quantidade ficarão salvas na fila de integração com uma mensagem informativa de quaisquer problemas que a impediram de ser integradas.

10. **Categoria de cota -> Proprietário**: A categoria de cota que será gravada na cota no momento que uma venda for identificada pela integração.

11. **Categoria de cota -> Administrativa**: A categoria de cota que será gravada na cota no momento que um cancelamento de venda for identificado pela integração.

12. **X-Integration Token**: Token necessário para uso com a API REST. Será fornecido pela UAU.

### Configuração de regex 

O formato de chave usado pelo UAU é variável de acordo com o cliente e de complexa extração dos dados relevantes. Para isso, é necessário configurar uma expressão regular (*Regex*) que definirá como extrair os dados.
Adicionar um *Regex* para cada entrada na tela.
As expressões regulares podem ser testadas e validadas no site <http://regexstorm.net/tester>

![][regex]


### Configurar o agendamento de tarefa

Configurar um agendamento para a tarefa `1001 - Integração UAU`. Definir o **Escopo** como **Empresa** e, na Aba **Empresa**, definir em quais empresas a integração irá rodar. O usuário definido em **Usuário execução** deve ter permissão no módulo de **Cotas** para adicionar e alterar uma cota, bem como permissões para adicionar e alterar um **Cliente**

![][agendamento]

Os demais campos devem ser configurados de acordo com a necessidade de cada cliente.

# Identificando erros na integração

  Ao identificar uma divergência entre as vendas do UAU e o que foi integrado, verificar se não há nenhuma venda na fila de integração. Vendas na fila de integração que não estouraram o total de tentativas terão uma nova tentativa de integração no próximo momento que a tarefa de integração rodar (esse tempo é variável de acordo com o que foi cofigurado no agendmaneto de tarefa, quando foi a última vez que a tarefa rodou, etc). É possível forçar a tentativa de uma venda na fila de integração selecionando a venda e clicando em `Integrar selecionado`

![][fila]

  Caso a venda divergente não esteja na fila de integração, é possível integrá-la manualmente no módulo de integração, através da opção `Integrar venda específica`, bastando informar os dados da venda para tentar integrá-la imediatamente. Para conseguir identificar qual venda está divergente, será necessário analisar o Access Center pelo módulo `Empreendimento -> Cadastro -> Cota` e confrontar com as vendas no UAU. Esse procedimento se faz necessário pois o recurso de integração com vendas excluídas no UAU só foi recentemente disponibilizado pela GlobalTech e ainda não foi desenvolvido no Access Center.
  
  Identificado a mensagem de erro na fila de integração (coluna Observação) ou na própria tela de integração (coluna Observações), caso não seja possível resolver com correção de cadastro, acionar o suporte da eSolution com as informações identificadas (venda, mensagem de erro, etc).
  
  

[blocos]:http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-19-09_53_48-Window.png
[configuracoes]:http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-19-10_16_33-Window.png
[regex]:http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/regex.png
[agendamento]:http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-19-11_07_24-Agendador-de-tarefa.png
[fila]:http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/filadeintegracao.png
