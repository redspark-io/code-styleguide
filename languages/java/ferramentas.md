# Ferramentas

## Checkstyle

Nós usamos a ferramenta checkstyle para reforçar, automaticamente, o padrão de estilo de escrita de código. 
É uma ferramenta bem configurável e atualmente suportada por várias outras ferramentas e serviços, 
como Intellij IDEA, Sonar, entre outros. 

Atualmente temos um arquivo XML [__redspark_checks.xml__](languages/java/checkstyle/redspark_checks.xml ':ignore') com as regras adotadas na Redspark que está em constante evolução. Este arquivo foi baseado no code style da Google.
Repositório oficial: https://github.com/checkstyle/checkstyle

### Configurações - Pre-commit
Antes de cada commit, podem ser realizadas diversas verificações a fim de assegurar a qualidade e caso não esteja de acordo com o desejado, o commit não será efetuado.
Para usar o hook de pre-commit, siga os seguintes passos:

1. Faça o download dos seguintes arquivos:
    - [__redspark_checks.xml__](languages/java/checkstyle/redspark_checks.xml ':ignore')
    - [__checkstyle-8.20-all.jar__](https://github.com/checkstyle/checkstyle/releases/download/checkstyle-8.20/checkstyle-8.20-all.jar ':ignore')
    - [__pre-commit__](languages/java/checkstyle/pre-commit ':ignore')
2. Coloque os arquivos baixados no seguinte diretório do seu projeto. Atenção: o diretório deve ser um diretório git.
    - {PROJECT_DIR}/.git/hooks

Após esses passos, você já conseguirá usar a verificação. Para isso, basta tentar commitar algo, que a verificação do checkstyle irá rodar. Atenção: é necessário ter o executável do java no PATH.

Vale ressaltar que, caso o projeto na máquina do desenvolvedor não esteja nos conformes para rodar a verificação pre-commit, esta ação será postergada para a verificação no CI. Entretanto, é recomendado que em todo projeto que tiver o pre-commit, o desenvolvedor realize estas ações acima. Servirá como lembrete para se acostumar a entregar o código já verificado, evitando voltas durante o Pull Request.


### Configurações - Intellij IDEA
Para evitar que o programador só encontre erros no momento que for realizar o commit, é ideal que as regras definidas pela Redspark estejam configuradas de uma maneira fácil na IDE. Dessa maneira, é possível já saber em qual linha se encontra o problema, para corrigir e verificar previamente se acontecerão erros nas validações.

#### Plugin Checkstyle-IDEA
Este plugin auxilia a visualizar em quais linhas as verificações encontraram falhas de estilo.
Para instalar e configurar:
1. File > Settings > Plugins > Marketplace > Buscar por Checkstyle-IDEA > Instalar > Reiniciar a IDE
2. File > Settings > Other Settings > Checkstyle
    - Escolher a versão do checkstyle como 8.20
    - Deixar habilitada a opção "Treat Checkstyle errors as warnings"
    - Em configuration File, adicione um novo.
        - Description: Redspark Checks
        - Local file: escolha o mesmo arquivo utilizado nas configurações de "pre-commit". Ele se encontra em {PROJECT_DIR}/.git/hooks/redspark_checks.xml
        - Finalize a configuração e deixe a configuração criada Redspark Checks como habilitada
    - Em Third-Party Checks, adicione o seguinte arquivo: [__checkstyle-addons-5.2.2-all.jar__] (https://github.com/checkstyle-addons/checkstyle-addons/releases/download/v5.2.2/checkstyle-addons-5.2.2-all.jar)

#### Correção automática
É possível corrigir automaticamente pelo Intellij alguns erros de estilo de código. Para isso, pode ser usado o mesmo arquivo de configurações como base.
1. File > Settings > Editor > Code Style > Java
    - Em Scheme, clique na engrenagem e escolha a opção Import Scheme > CheckStyle Configuration
    - Escolha o arquivo utilizado no pre-commit. Ele se encontra em {PROJECT_DIR}/.git/hooks/redspark_checks.xml

Após configurado, seu Intellij já estará pronto para utilizar as verificações do Checkstyle.
Aparecerá uma nova aba CheckStyle na barra acima da barra de status. Nesta aba, será possível verificar por erros nos arquivos modificados, no módulo atual ou no projeto inteiro.
Para corrigir diversos erros de estilo automaticamente, basta digitar Ctrl+Alt+L para o arquivo atual ou clicar com o botão direito do mouse no nome do package raiz e escolher "Reformat Code". Na nova janela que aparecer, é possível selecionar somente os arquivos modificados, marcando a opção "Only VCS changed text"