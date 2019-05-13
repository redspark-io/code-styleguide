# Ferramentas

## Checkstyle

Nós usamos a ferramenta checkstyle para reforçar, automaticamente, o padrão de estilo de escrita de código. 
É bem configurável e atualmente suportada por várias outras ferramentas e serviços, 
como Intellij IDEA, Sonar, entre outros. 

Atualmente temos um arquivo XML [__redspark_checks.xml__](languages/java/checkstyle/redspark_checks.xml ':ignore') com as regras adotadas na Redspark que está em constante evolução. Este arquivo foi baseado no code style da Google.
Repositório oficial: https://github.com/checkstyle/checkstyle

### Configurações - Pre-commit

Antes de cada commit, podem ser realizadas diversas verificações a fim de assegurar a qualidade e caso não esteja de acordo com o desejado, o commit não será efetuado.
Para usar o hook de pre-commit, siga os seguintes passos:

1. Faça o download dos seguintes arquivos:
    - [__redspark_checks.xml__](languages/java/checkstyle/redspark_checks.xml ':ignore')
    - [__checkstyle-8.20-all.jar__](languages/java/checkstyle/checkstyle-8.20-all.jar ':ignore')
    - [__pre-commit__](languages/java/checkstyle/pre-commit ':ignore')
2. Coloque os arquivos baixados no seguinte diretório do seu projeto. Atenção: o diretório deve ser um diretório git.
    - {PROJECT_DIR}/.git/hooks

Após esses passos, você já conseguirá usar a verificação. Para isso, basta tentar commitar algo, que a verificação do checkstyle irá rodar. Atenção: é necessário ter o executável do java no PATH.

Vale ressaltar que, caso o projeto na máquina do desenvolvedor não esteja nos conformes para rodar a verificação pre-commit, esta ação será postergada para a verificação no CI. Entretanto, é recomendado que em todo projeto que tiver o pre-commit, o desenvolvedor realize estas ações acima caso necessário. Servirá como lembrete para se acostumar a entregar o código já verificado, evitando voltas durante o Pull Request.








