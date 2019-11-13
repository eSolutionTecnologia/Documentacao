# Configuração financeira para conciliação de cartões

A fim de proporcionar um melhor funcionamento com conciliação de cartão com outros tipos de arquivo (em primeiro momento, arquivos da NEXXERA), os recursos de configuração de conciliação de cartões foram migrados para um módulo separado, a partir da versão 00307.01.

Esses tipos de arquivos podem conter registros de mais de uma adquirente e, por isso, foi feito esse desmembramento. As configurações estão acessíveis agora através do módulo `Financeiro -> Configuração de conciliação de cartão`, identificado como o módulo de código `624`.

Com isso, a aba de detalhes do cadastro da financeira possui apenas o campo do tipo de arredondamento e o identificador de adquirente, conforme imagem a seguir.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/11/financeira-detalhes-30701.png)

Os campos de configuração estão disponíveis no novo módulo, conforme imagem a seguir.

![](http://conhecimento.esolution.com.br/wp-content/uploads/2019/11/configuracao.png)

O processo de atualização para a versão 307.01 faz automaticamente a migração das configurações do cadastro da financeira para o novo cadastro, sendo necessário apenas inativar configurações que não deverão ser usadas e atualizar o nome, informando algum nome mais intuitivo.

# Observações
Este artigo apresenta uma versão atualizada para complementação dos artigos [Conciliação de cartões de crédito/debito – Baixa](http://conhecimento.esolution.com.br/2019/01/15/conciliacao-de-cartoes-de-credito-debito-baixa/) e [Alteração de tipo de conta a receber e valor a partir de arquivo de plano de venda parcelada (CIELO 03)](http://conhecimento.esolution.com.br/2019/10/08/alteracao-de-tipo-de-conta-a-receber-e-valor-a-partir-de-arquivo-de-plano-de-venda-parcelada-cielo-03/)
