# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Projetos Front-end.

## Endpoints

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.


### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"


####################################################################################################################
<------------------------------------------DOCUMENTAÇÃO IMPROVISADA------------------------------------------------>

### CADASTRO POST http://locahost:3001/signup

*** CORPO:

{
	"mail": "teste@teste.com",
	"password": 1234,
	"user_description": "Adoro pets",
	"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Frevistapegn.globo.com%2FNoticias%2Fnoticia%2F2014%2F06%2F11-maneiras-simples-de-ser-mais-feliz-todos-os-dias.html&psig=AOvVaw39XJwheaRXsIyegpini4vz&ust=1682472057053000&source=images&cd=vfe&ved=2ahUKEwi6_dr77sP-AhUJkZUCHTg1C3wQjRx6BAgAEAw"
}


*** RESPOPSTA: satus 200

{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQE1tYWlsLmNvbSIsImlhdCI6MTY4MjM4NTk2MiwiZXhwIjoxNjgyMzg5NTYyLCJzdWIiOiIyIn0.odXe-T1wih-Py961gn36qeKSJNA8o3IU8Coq_zsgmA0",
	"user": {
		"email": "teste@Mmail.com",
		"user_description": "Adoro pets",
		"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Frevistapegn.globo.com%2FNoticias%2Fnoticia%2F2014%2F06%2F11-maneiras-simples-de-ser-mais-feliz-todos-os-dias.html&psig=AOvVaw39XJwheaRXsIyegpini4vz&ust=1682472057053000&source=images&cd=vfe&ved=2ahUKEwi6_dr77sP-AhUJkZUCHTg1C3wQjRx6BAgAEAw",
		"id": 2
	}
}

### LOGIN: POST http://locahost:3001/signin

*** CORPO:

{
	"email": "kenzinho@mail.com",
	"password": "123456"
}


*** RESPOSTA: status 200

{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImtlbnppbmhvQG1haWwuY29tIiwiaWF0IjoxNjgyMzg0NzkwLCJleHAiOjE2ODIzODgzOTAsInN1YiI6IjEifQ.T0PXEEifueKjAPdQmU8YNqJbpspysP6djry_Lkuih_8",
	"user": {
		"email": "kenzinho@mail.com",
		"name": "Kenzinho",
		"age": 38,
		"id": 1
	}
}

### LISTAR TODOS OS PETS (USURARIO DEVERÁ ESTAR LOGADO PARA LISTAR PETS)

*** CORPO: não possui corpo, mas exige autenticação 

Authorization: Bearer token


*** RESPOSTA : status 200 

[
	{
		"id": 1,
		"type": "cat",
		"race": "persa",
		"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.patasdacasa.com.br%2Fnoticia%2Fgato-persa-tudo-que-voce-precisa-saber-sobre-a-personalidade-da-raca_a4829%2F1&psig=AOvVaw1gmJV0d8a7IuW8Eg6v01nc&ust=1682468892565000&source=images&cd=vfe&ved=2ahUKEwiI_OGW48P-AhUPR7gEHYB8AYcQjRx6BAgAEAw"
	},
	{
		"id": 2,
		"type": "dog",
		"race": "huscky",
		"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.patasdacasa.com.br%2Fnoticia%2Fhusky-siberiano-filhotes-origem-alimentacao-cuidados-saude-e-comportamento-desse-cao-de-raca-grande_a579%2F1&psig=AOvVaw3cuj25nZRxfXx7hntUmeau&ust=1682469088755000&source=images&cd=vfe&ved=2ahUKEwjruqj048P-AhWiuZUCHRrGC7YQjRx6BAgAEAw"
	},
	{
		"id": 3,
		"type": "dog",
		"race": "srd",
		"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.dogchoni.com.br%2Fblog%2Fpost%2Fdesvende-qual-o-porte-do-seu-cao-srd&psig=AOvVaw2Bp-Zab9sMuwEysBLD2-Dc&ust=1682468969958000&source=images&cd=vfe&ved=2ahUKEwjB1dW748P-AhV9rZUCHTHKAAAQjRx6BAgAEAw"
	},
	{
		"id": 4,
		"type": "cat",
		"race": "norueguês",
		"img": "https://www.google.com/url?sa=i&url=https%3A%2F%2Fmeupet.elanco.com%2Fbr%2Fnovos-tutores%2Fperfil-da-ra-gato-noruegues-da-floresta&psig=AOvVaw2s2hKlogGkyXvXYEn-JLu1&ust=1682468790547000&source=images&cd=vfe&ved=2ahUKEwjcpo_m4sP-AhVSlJUCHSIvDWgQjRx6BAgAEAw"
	},
	{
		"id": 5,
		"type": "cat",
		"rece": "minecoon",
		"img": "https://br.pinterest.com/joaninaaraujo/gato-maine-coon/"
	}
]