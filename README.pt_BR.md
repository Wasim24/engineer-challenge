![Zul Digital](https://s3-us-west-2.amazonaws.com/blu-static/logo/small_logo_zul-1024.jpg)

## Desafio

O objetivo é criar uma aplicação que faça uma requisição para o nosso mock da API com tweets e apresente o output de um dos tweets seguindo as regras de negócio que foram definidas.

Você pode utilizar a tecnologia que tem maior domínio. O importante é tentar desenvolver a solução completa para rodar a aplicação.

### Regras de negócio
**R1.** Recuperar o atributo text de um dos tweets da nossa API mock de forma randômica.   
**R2.** Respeitar o limite de 45 caracteres para fazer o output do tweet.  
**R2.a.** Caso o texto tenha mais do que 45 caracteres, o tweet deve ser quebrado em N partes até que o texto de toda a descrição seja apresentada.

### API Mock

A API tem dois métodos. Um para fazer a autenticação e recuperar um JWT token com duração de 60 segundos, que deve ser utilizado na chamada do endpoint da timeline. E o segundo método responsável por trazer a timeline com os tweets.

|Base URL  | https://n8e480hh63o547stou3ycz5lwz0958.herokuapp.com/ |
| ----------- | ------------------------------------------------------------------------------------ |
|**Version**  | **1.1** |
| | [![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/47875da49b734fddadcd)|

#### Auth POST /{version}/auth

| Status Code | Descrição | Response |
| ----------- | --------- | ---------|
| 200 | Autenticação feita com sucesso. | ```{ "token": "..." }``` |
| 500 |Erro inesperado. |  |

#### Timeline GET /{version}/statuses/home_timeline.json

| Status Code | Descrição | Response |
| ----------- | --------- | ---------|
| 200 | Retorna uma lista com os tweets. | ```[{"created_at": "Wed Apr 11 22:15:17 +0000 2018" ... }]``` |
| 403 | Ocorreu um erro na validação do token. | ```{"message": "Invalid JWT token." }``` |
| 500 |Erro inesperado. |  |

### Exemplo

Segue abaixo um exemplo com o output que é esperado como resposta ao executar a aplicação.

| Text | Output |
| ---- | ------ |
| Interferência na Av. Washington Luis sentido Bairro, próximo Praça. Comte. Linneu Gomes. Ocupa uma faixa. #ZS. | Tweet #1: Interferência na Av. Washington Luis sentido | 
|  | Tweet #2: Bairro, próximo Praça. Comte. Linneu Gomes. |
|  | Tweet #3: Ocupa uma faixa. #ZS.

### Como deve ser feita a entrega do código?

A entrega do seu código deve ser em formato ***ZIP***, contendo todo o source que você desenvolveu. Na raiz do seu projeto você precisa colocar um Dockerfile que será responsável pelo processo de build e execução do seu código. 

O Dockerfile deve estar pronto para ser executado com os comandos abaixo e ao final da execução deve apresentar o output esperado.

* docker build -t zuldigital/engineer-exam .
* docker run --rm zuldigital/engineer-exam

O arquivo ZIP deve seguir a nomenclatura: ***seunome-YYYYMMDD.zip*** e deve ser enviado em anexo a mensagem do processo seletivo assim que estiver pronto.

### Dicas

* Utilize tudo o que você considera boas práticas.
* Adicione toda a documentação que você entende ser necessária.
* Testes unitários são sempre importantes!
