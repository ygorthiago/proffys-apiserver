# 🚀 Proffys - API Server
API desenvolvida durante a NextLevelWeek#2 para funcionar como backend da aplicação Proffys na Web e Mobile. 
Para construção da API foram utilizados NodeJS com TypeScript, Express, CORS e SQLite com o auxílio do KnexJS.

## Endpoints

### Aulas
#### GET /classes
- Esse endpoint é responsável por retornar a listagem das aulas.

#### Parâmetros 
Query:
	week_day: Dia da semana (0 a 6) que o usuário seja ter aula,
	subject: Matéria que o usuário deseja ter aula,
	time: Horário em que o usuário deseja ter aula (HH:MM)

#### Respostas 
##### OK! 200
Caso essa resposta aconteça, você vai receber a listagem das aulas que pertencem ao parâmetro inserido.

Exemplo de resposta: 
```
[
  {
    "id": 2,
    "subject": "Artes",
    "cost": 130,
    "user_id": 2,
    "name": "Ygor Thiago",
    "avatar": "url-aqui",
    "whatsapp": "999999999",
    "bio": "Professor de artes."
  }
]
```
##### Bad request! 400
Caso essa resposta aconteça, isso significa que algum dos parâmetros não foi preenchido.
Exemplo de resposta: 
```
{
  "error": "Missing filters to search classes"
}
```

#### POST /classes
- Esse endpoint é responsável por criar uma nova aula.

#### Parâmetros 
name: Nome do professor,
avatar: URL do avatar do professor,
whatsapp: Número do whatsapp do professor,
bio: Biografia do professor,
subject: Matéria da aula,
cost: Preço da hora/aula,
schedule: 
	week_day: Dia da semana (0 a 6) da aula,
	from: Horário início em que o professor estará disponível para dar aula (HH:MM),
	to: Horário final em que o professor estará disponível para dar aula (HH:MM)

Exemplo: 
```
{
	"name": "Ygor Thiago",
	"avatar": "URL do avatar do professor,
	"whatsapp": "999999999",
	"bio": "Professor de física",
	"subject": "Física",
	"cost": 80,
	"schedule": [
		{
			"week_day": 1, 
			"from":"8:00",
			"to": "12:00"
		}
	]
}
```

#### Respostas 
##### Created! 201
Caso essa resposta aconteça, a aula foi criada com sucesso.

##### Bad request! 400
Caso essa resposta aconteça, isso significa que algum dos parâmetros não foi preenchido.
Exemplo de resposta: 
```
{
  "error": "Unexpected error while creating new class"
}
```


### Conexões
#### GET /connections
Esse endpoint é responsável por retornar o número total de conexões já realizadas entre alunos e professores.

#### Parâmetros 
Nenhum.

#### Respostas 
##### OK! 200
Caso essa resposta aconteça, você vai receber o número total de conexões já realizadas.

Exemplo de resposta: 
```
{
  "total": 266
}
```

#### POST /connections
- Esse endpoint é responsável por contabilizar uma nova conexão entre alunos e professores.

#### Parâmetros 
Nenhum.

#### Respostas 
##### Created! 201
Caso essa resposta aconteça, será contabilizada uma nova conexão entre alunos e professores.

Exemplo de resposta: 
```
"Uma nova conexão foi realizada!"
```

