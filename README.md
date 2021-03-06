# UkorBR Backend-Test API

API Node.js para aplicação UkorBR.

## Módulos

* [Express](http://expressjs.com/) - Web Framework
* [Sequelize](http://docs.sequelizejs.com/en/latest/) - ORM compatível com bancos de dados SQL
* [GraphQL](http://graphql.org) - GraphQL é uma linguagem de consulta de dados
* [Mocha](https://mochajs.org/) - Test Runner para Node.js
* [Chai](http://chaijs.com/) - Interface BDD e TDD para implementação de testes
* [Babel](https://babeljs.io/) - Transpiler EcmaScript 6

E tem mais no [package.json](https://github.com/lucassant0s/ukorbr-backend-teste/blob/master/package.json) do projeto.

Live Code -> https://backend-testt.herokuapp.com/graphiql

## Instalação

* Clone o repositório: `git clone git@github.com:lucassant0s/ukorbr-backend-teste.git`
* Acesse o diretório do projeto: `cd ukorbr-backend-teste`
* Inicie o servidor: `docker-composer up ou docker-composer up --build`

## Utilização das Funções GraphQL

Url -> http://0.0.0.0:3000/graphiql

#### Salvando 1º Pergunta:
```
mutation {
  saveName(name: "Laura")
}
```
```
{
  "data": {
    "saveName": 3
  }
}
```

#### Salvando 2º Pergunta utilizando a `id` returnado após salvar o nome do usuário:
```
mutation {
  saveBirthDay(id: 3, birthDay: "1992-09-20T00:00:00.000Z")
}
```
```
{
  "data": {
    "saveBirthDay": "Resposta salva."
  }
}
```

#### Salvando 3º Pergunta utilizando a `id` returnado após salvar o nome do usuário:
```
mutation {
  saveResponse(id: 3, response: "Ansioso")
}
```
```
{
  "data": {
    "saveResponse": "Resposta salva."
  }
}
```

#### Returnando o total de usuarios por categoria:
```
query {
  totalUsersCategory {
    Feliz
    Triste
    Ansioso
  }
}
```
```
{
  "data": {
    "totalUsersCategory": {
      "Feliz": 1,
      "Triste": 1,
      "Ansioso": null
    }
  }
}
```

#### Returnando total de usuarios com sentimento (feliz, triste, etc...):
```
query {
  totalUsersFeeling {
    Adolescentes {
      Feliz
      Triste
      Ansioso
      Estressado
      Desanimado
    }
    Adultos {
      Feliz
      Triste
      Ansioso
      Estressado
      Desanimado
    }
    Idosos {
      Feliz
      Triste
      Ansioso
      Estressado
      Desanimado
    }
  }
}
```
```
{
  "data": {
    "totalUsersFeeling": {
      "Adolescentes": {
        "Feliz": 1,
        "Triste": 1,
        "Ansioso": null,
        "Estressado": null,
        "Desanimado": null
      },
      "Adultos": {
        "Feliz": null,
        "Triste": null,
        "Ansioso": null,
        "Estressado": null,
        "Desanimado": null
      },
      "Idosos": {
        "Feliz": null,
        "Triste": null,
        "Ansioso": null,
        "Estressado": null,
        "Desanimado": null
      }
    }
  }
}
```

## Utilizando PgAdmin v4

Através do link `http://0.0.0.0:5000` utilizando usuário: `pgadmin4@pgadmin.org` e senha `admin` podemos ter total acesso ao banco de dados por uma UI.

## Execução dos testes

- Acessando `container` da aplicação utilizando `docker exec -it api_web_1 bash`
- Para executar todos os testes utilizar `yarn test`
- Para executar um teste separadamente, basta rodar `yarn test ${nome do arquivo sem 'test.js'}`

## About

Lucas N. Santos - http://twitter.com/lucasnst
