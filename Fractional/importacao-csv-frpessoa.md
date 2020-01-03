# Configuração de tarefa de importação de FrPessoa a partir de arquivo csv

* Configurar a seguinte tarefa, lembrando de marcar na aba `Filial` as filiais onde a tarefa deverá rodar.
![](https://i.imgur.com/ARwLNSu.png)

* Efetuar as configurações no módulo `Diretório para importação de dados cadastrais` acessível em `Multipropriedade->Cadastros`
* Neste módulo, informar o caminho dos diretórios a serem percorridos pela tarefa
![](https://i.imgur.com/UJ4Aztr.png)
* O caminho do diretório deverá ser absoluto e acessível para leitura e escrita partindo do servidor onde o serviço do Access Center é executado
* É possível testar as configurações nesse módulo efetuando uma varredura manual, pelo comando `Efetuar nova varredura`
![](https://i.imgur.com/9VyRLeC.png)
* Arquivos importados com sucesso serão movidos para a pasta `Importados`, criada dentro do diretório configurado anteriormente.
* Os arquivos deverão obrigatoriamente conter a extensão `.csv`
* O formato do arquivo esperado é:

```
Nome,Tipo,Cpf,Cnpj,Passaporte,RG,OrgaoExpedidor,DataEmissao,Sexo,Nacionalidade,DataNascimento,EstadoCivil,NomePai,NomeMae,Apelido,Naturalidade,Escolaridade,Email,Profissao,Renda,PossuiCartaoCredito,QtdDependentes,IdadeFilhos,TempoCasamento,ResidenciaPropria,ModeloVeiculo,AnoVeiculo,Logradouro,Cidade,Numero,Bairro,Complemento,TelefoneFixo,TelefoneMovel,Cep
JOSE ALVES DA SILVA,F,278.552.286-91,,,,,,M,,,SOLTEIRO,,,,,,,Metalurgico,"R$ 8.000,00",True,,,2,True,HYUNDAI HB20 5 ANOS 1.6 FLEX 16V AUT.,2017,Avenida B,Caldas Novas-GO,0,Centro,0,0000000000,6499599999,1234567

```
* Os campos de data devem estar no formado `dd/mm/aaaa`, ou seja: `31/12/2019`
* O campo de renda deve estar formatado com duas casas decimais, do tipo `1.000,00` ou `100000` ou `R$ 1000,00`, todos considerados como representando mil reais.
