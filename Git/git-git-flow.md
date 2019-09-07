# Instalação
## Git-Fork
Baixar e instalar o Fork do site <https://git-fork.com/>

## Git bash
Caso o Fork não instale o git bash, instalar de <https://git-scm.com/downloads>

Certifique-se de marcar, durante a instalação, a instalação do Git Bash

![Git Bash][gitbash]

# Configurações

## SSH
Configurar acesso SSH para comunicação mais cômoda e rápida com o repositório remoto.

1- Abra o Git Bash e digite o seguinte comando
```bash
ssh-keygen -t rsa -b 4096 -C "<seu_email_do_github@email.com>"
```
Isso vai gerar as chaves pública/privada para identificar a máquina. A seguinte mensagem vai aparecer perguntando pelo caminho para salvar essas chaves. 
```bash
Enter a file in which to save the key (/c/Users/Usuario/.ssh/id_rsa):[Press enter]
```
Apenas tecle `Enter` para usar o local padrão.

Em sequência, será pedido uma senha para o arquivo. Recomendo deixar em branco ou escolher uma fácil de lembrar (deverá repetir a senha logo em seguida para confirmar)
```bash
Enter passphrase (empty for no passphrase): [Type a passphrase]
```

2- Ainda no Git Bash, rode o seguinte comando
```bash
eval $(ssh-agent -s)
```
para certificar-se que o ssh-agent está rodando, a mensagem com o id do processo deverá aparecer na tela

```bash
Agent pid 59566
```

3- Adicione a chave gerada no passo 1 ao agente com o seguinte comando
```bash
ssh-add ~/.ssh/id_rsa
```
Aqui o caminho `~/.ssh/id_rsa` só funcionará se, no passo 1, o caminho padrão para geração das chaves foi definido. Caso tenha escolhido um caminho diferente, informe-o aqui.

4- Faça login no Github e localize as seguintes opções:

![Settings][github1]

![SSH and GPG keys][ssh]

![New SSH key][newssh]


Volte ao Git Bash e execute o seguinte comando
```bash
clip < ~/.ssh/id_rsa.pub
```
Para copiar a chave gerada para a área de transferência

Cole o conteúdo da área de transferência com `Ctrl-V` no github, no campo a seguir

![Colar a chave SSH][pastessh]

No campo título, coloque um nome para identificar a origem da chave, exemplo `Notebook-eSolution`

Por fim, adicione a chave

![Add SSH key][add]

O Github pode pedir a senha da conta nesse processo, basta digitar e autorizar a adição da chave.

# Clonar o repositório
Com a chave na máquina e adicionada ao Github, é possível realizar o clone do repositório.

1- Vá até a página do repositório no Github, e clique em `Clone or download`

![Clone or Download][new_repository]

2- Selecione o link SSH

![SSH][clone-ssh]

E copie a url da caixa de texto, o formato deverá ser parecido com `git@github.com:eSolutionTecnologia/Portal.git`

3- No Fork, selecione `File->Clone` ou tecle `Ctrl-N`. Na caixa de diálogo que irá aparecer, informe a Url obtida no passo 1, o caminho desejado para salvar o projeto na máquina local e o nome da pasta do projeto (será criada essa pasta dentro do caminho informado.)

![Clone][clone-fork]

4- Feito isso um clone será gerado da branch `master`. Ainda no Fork, clique em `Repository->Git Flow->Initialize Git Flow...` e na caixa de diálogo, informe os seguintes campos:

![Initialize Git Flow][initflow]

Esses campos foram padronizados para desenvolvimento dos sistemas na eSolution.

```
Produciton Branch: master
Development Branch: develop
Feature Prefix: OS/
Release Prefix: hotfix/
Version Tag Prefix: version/
```

# Git-flow

O Git-flow é uma metodologia de trabalho com o git e uma extensão que facilita o trabalho com essa metodologia. O git-flow já está habilitado no Fork.

## Desenvolvimento
Artigo em desenvolvimento...

## Homologação
Artigo em desenvolvimento...


[clone-fork]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-04-16_50_45-Clone.png
[gitbash]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-04-12_55_52-.png
[github1]: https://help.github.com/assets/images/help/settings/userbar-account-settings.png
[ssh]: https://help.github.com/assets/images/help/settings/settings-sidebar-ssh-keys.png
[newssh]: https://help.github.com/assets/images/help/settings/ssh-add-ssh-key.png
[pastessh]: https://help.github.com/assets/images/help/settings/ssh-key-paste.png
[add]: https://help.github.com/assets/images/help/settings/ssh-add-key.png
[initflow]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/initialize-git-flow-4.jpg
[new_repository]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-04-16_44_08-eSolutionTecnologia_Portal.png
[clone-ssh]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/09/2019-09-04-16_46_35-eSolutionTecnologia_Portal.png
