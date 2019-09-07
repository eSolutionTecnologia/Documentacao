# Instalação do OracleDataAccess.dll no cache do Visual Studio e Debug 64bits

----

## Introdução

Para evitar conflitos de versões de client do oracle instalados nas diversas máquinas dos desenvolvedores, é possível configurar o Visual Studio para usar o client instalado na máquina em vez de uma dll fixa no projeto. Uma das vantagens desse recurso é a possibilidade de debugar o sistema em 64bits.

--- 

## Passo 1: Instalação do oracle client
Instalar o oracle client desejado. Instalar um oracle client 64bits caso o objetivo seja debugar 64bits.

## Passo 2: Consultar o cache do Visual Studio
Idealmente, a instalação do Oracle Client já deveria adicionar os arquivos necessários ao cache do Visual Studio instalado na máquina. Porém várias vezes isso não acontece. Para certificar, é possível consultar o cache.

1. Localize e execute como *administrador* o prompt de desenvolvimento do visual studio. A maneira mais fácil é pesquisando no próprio menu iniciar do Windows.

![Developer Command Prompt][prompt]

2. Execute o seguinte comando no prompt de desenvolvimento

```
gacutil -l | findstr Oracle.DataAccess
```

Caso o assembly do oracle esteja no cache, ele aparecerá nessa tela.

![Assembly do Oracle][assembly]

Caso o nome do arquivo esteja presente, copie o nome completo e pule para o **Passo 4**


## Passo 3: Adicionar a OracleDataAccess.dll ao cache
Localize a pasta `ODP.NET\bin` do oracle client instalado, normalmente é uma pasta similar a:

```
C:\app\client\<usuario>\product\<versao>\client_1\ODP.NET\bin
```

Localize a subpasta da versão do `.NETFramework` dentro desta pasta. Normalmente apenas uma pasta chamada `4`, caso não houver, use a pasta `2.x`. Dentro desta pasta está a dll `Oracle.DataAccess.dll`. Copie o caminho completo para esta dll, ou seja:

```
C:\app\client\<user>\product\<versao>\client_1\ODP.NET\bin\4\Oracle.DataAccess.dll
```

Feito isso, adicione o assembly através do comando

```
gacutil -i <path completo para o arquivo Oracle.DataAccess.dll>
```


3. Execute novamente o comando

```
gacutil -l | findstr Oracle.DataAccess
```

Para obter o nome completo do Assembly no cache.

## Passo 4: Editar o web.config

Atualize o arquivo Web.config de desenvolvimento com a seguinte informação, dentro do nó `<configuration>`, no final dele:

```xml
<configuration>
...
...
...
  <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <qualifyAssembly partialName="Oracle.DataAccess"
                             fullName="Nome do assembly obtido pelo comando gacutil -l"
            />
        </assemblyBinding>
    </runtime>
</configuration>
```

O nome do assembly deve ser parecido com:

```
Oracle.DataAccess, Version=4.122.18.3, Culture=neutral, PublicKeyToken=89b483f429c47342, processorArchitecture=AMD64
```

Dependendo da versão do Oracle instalada. Certifique-se de usar o nome que termine com `AMD64` pois eles são os assemblies 64bits


## Passo 5: Removendo referências anteriores

Remova todas as referências à dll `Oracle.DataAccess.dll` existentes nos projetos. Remova também todo arquivo de mesmo nome na pasta bin da aplicação (`esAccessCenterService\bin`).
Por fim, marque nas propriedades do projeto `esAccessCenterService` para usar o IIS de 64 bits, conforme imagem:

![ISS Express][bitness]

## Verificando o funcionamento

Para verificar se tudo deu certo para debug 64bits, debugar o serviço pelo visual studio normalmente, conectar nele e acessar o módulo `Monitoramento de serviço`, onde o campo `Plataforma` deve apresentar como `64 bits` conforme a imagem a seguir:

![64 bits][verificacao]



[prompt]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/Developer_command_prompt.png
[assembly]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/oracle_data_access.png
[bitness]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/bitness.png
[verificacao]: http://conhecimento.esolution.com.br/wp-content/uploads/2019/08/verificacao.png
