![Zul Digital](https://s3-us-west-2.amazonaws.com/blu-static/logo/small_logo_zul-1024.jpg)

## Challenge

The goal is to create an application that makes a request to our mock API with tweets and print the output of one of the tweets respecting the business rules.

You can use the technology that you have better domain. The most important thing to try to develop the complete solution to run the application.

### Business rules
**R1.** Randomly get the attribute text from one of the tweets at our mock API.	  
**R2.** Respect the limit of 45 characters to make the tweet output.  
**R2.a.** If the text has more than 45 characters, the tweet needs to be sliced in N parts until the whole text have been presented.

### API Mock

The API has two methods. One to make the authentication and get the JWT token with 60 seconds of duration, that needs to be used to make the request to the timeline endpoint. And the second one that returns the timeline of the tweets.


|Base URL  | https://n8e480hh63o547stou3ycz5lwz0958.herokuapp.com/ |
| ----------- | ------------------------------------------------------------------------------------ |
|**Version**  | **1.1** |
| | [![Run in Postman](https://run.pstmn.io/button.svg)](https://www.getpostman.com/collections/47875da49b734fddadcd)|

#### Auth POST /{version}/auth

| Status Code | Description | Response |
| ----------- | --------- | ---------|
| 200 | Success authentication. | ```{ "token": "..." }``` |
| 500 | Unexpected error. |  |

#### Timeline GET /{version}/statuses/home_timeline.json

| Status Code | Description | Response |
| ----------- | --------- | ---------|
| 200 | Get tweets list. | ```[{"created_at": "Wed Apr 11 22:15:17 +0000 2018" ... }]``` |
| 403 | Occur an error at the token validation. | ```{"message": "Invalid JWT token." }``` |
| 500 | Unexpected error. |  |

### Example

Above there's an example with the output that was expected to be answered after executing the application.

| Text | Output |
| ---- | ------ |
| Interferência na Av. Washington Luis sentido Bairro, próximo Praça. Comte. Linneu Gomes. Ocupa uma faixa. #ZS. | Tweet #1: Interferência na Av. Washington Luis sentido | 
|  | Tweet #2: Bairro, próximo Praça. Comte. Linneu Gomes. |
|  | Tweet #3: Ocupa uma faixa. #ZS.

### How can I delivery the code?

The delivery of your code must be in ***ZIP*** format, with your whole source code. At the root path of your project you need to add a Dockerfile that will be responsible for building and executing your code.

The Dockerfile needs to be executed with the following commands and, at the end of the execution, it needs to print the formated output.

* docker build -t zuldigital/engineer-exam .
* docker run --rm zuldigital/engineer-exam

The ZIP file must be named as follow: ***yourname-YYYYMMDD.zip*** and it needs to be attached at your selective process after you finish it.

### Tips

* Use all the things that you considers best coding practices.
* Add all the documentation that you understand that will be necessary.
* Unit testing is always important!
