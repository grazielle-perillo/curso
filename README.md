# Getting Started

### Documentação de referência
Como guia de referênia, favor considerar as seguintes seções:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.2.1.RELEASE/maven-plugin/)
* [Spring Batch](https://docs.spring.io/spring-boot/docs/2.2.1.RELEASE/reference/htmlsingle/#howto-batch-applications)

### Guias
Os guias abaixo ilustram como utilizar corretamente algumas features do spring batch:

* [Creating a Batch Service](https://spring.io/guides/gs/batch-processing/)

### Pré-requisitos do projeto
* Java 11
* Maven 3.5.* ou superior
* Arquivo settings.xml configurado para o Nexus da RD
* Configurar o workspace para utilizar os fontes no encode UTF-8
* A biblioteca Lombok está sendo utilizada como recurso para auxiliar a criação de classes, verifique se a sua IDE possui suporte/plugin para usuar o Lombok. Mais informações em https://projectlombok.org.

### Variáveis de ambiente
O arquivo `application.properties` da pasta `src/main/resources` contém as variáveis de ambiente que serão utilizadas pela aplicação.
Caso nenhuma variável de ambiente seja informada os valores deafult serão utilizados.
Descrição das variáveis:
* `ACTIVE_PROFILE`   : (spring.profiles.active) Ambiente no qual a aplicação está rodando, os valores podem ser: `dev`, `qa` e `prd`. O valor padrão é: `dev`.
* `REPOSITORY_DRIVER`: (spring.datasource.driverClassName) Driver utilizado para conexão com o banco de dados de repositório do Spring Batch. O valor padrão é: `org.h2.Driver`, referente ao banco h2 em memória.
* `REPOSITORY_URL`   : (spring.datasource.url) Sring de conexão para o banco de dados de repositório do Spring Batch. O valor padrão é: jdbc:h2:mem:testdb.
* `REPOSITORY_USER`  : (spring.datasource.username) Usuário de conexão com o banco de dados de repositório do Spring Batch. O valor padrão é: sa.
* `REPOSITORY_PASS`  : (spring.datasource.password) Senha de conexão com o banco de dados de repositório do Spring Batch. O valor padrão é: <vazio>.

### Executando o projeto com docker
O plugin maven Jib constrói uma imagem Docker. Para criar uma imagem execute o comando abaixo substituindo a variável {nomeDaImagem} pelo nome da imagem a ser gerada. O Jib utilizará o Docker daemon local:

```
mvn clean package jib:dockerBuild -Dimage={nomeDaImagem}
```

Já para rodar o job utilizando docker execute o comando abaixo:

```
docker run -it -e {variável de ambiente}={valor da variável de ambiente} {nomeDaImagem} {parâmetro do job}={valor do parâmetro do job}
```
