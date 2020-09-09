# Dialog FullStack (react/pwa/node) Test

## Objetivo

Desenvolver uma API GraphQL node e um front-end React/PWA:

## Descrição da API

Deve conter uma query `list()`.

A chamada query `list` sem parâmetro (o termo da busca por nome) deverá retornar todos os itens.

Se fornecido o argumento da busca `name`, deverá retornar os dados que contém parte da string, usar RegEx no filtro.

Download: [Data JSON](db.json)

Modelo:
```javascript
[
    {
        "_id": "5f1b3f4b7917ef26107bd58c",
        "index": 0,
        "picture": "https://i.pravatar.cc/200?u=5f1b3f4b7917ef26107bd58c",
        "age": 37,
        "eyeColor": "brown",
        "name": "Weber Stein",
        "company": "VIAGRAND",
        "email": "weber.stein@viagrand.ca",
        "phone": "+1 (866) 533-3564",
        "friends": [
          {
            "_id": "5f1d7f3e8882c9c811b111ce",
            "index": 0,
            "picture": "https://i.pravatar.cc/200?u=5f1d7f3e8882c9c811b111ce",
            "age": 23,
            "eyeColor": "green",
            "name": "Patti Mckenzie",
            "company": "DAISU",
            "email": "pattimckenzie@daisu.com",
            "phone": "+1 (960) 566-3327"
          },
        ],
        "greeting": "Hello, Weber! You have 9 unread messages."
    }
]
```

### Stack:
- GraphQL (apollo ou relay)
- Express

### Requisitos:
- colocar um middleware no Express para log dos requests
- no final desse `README.md` colocar uma chamada funcional para a API em `curl`.

### Diferencial

- Usar TypeScript

### Executar o projeto

Deverá executar com `yarn start` na porta 4000


## Descrição do React/PWA

### Tela Inicial
![tela_incial](./docs/browser02.png)

### Tela detalhe de amigos
![tela_detalhe_amigos](./docs/browser03.png)


### Stack:
- React
- React Hooks
- React Router
- Apollo client (opcional)
- styled-components
- CSS Grid
  - deve ser responsivo, no celular exibir apenas um card na horizontal.
- Service Worker
  - app deve funcionar off-line (páginas que foram visitadas)

### Diferencial

- Usar TypeScript

### Executar o projeto

Deverá executar com `yarn start` na porta 3000


### Anotações que valem menção colocar aqui:
#### Sobre clonagem do repositório: 

Para clonar o repositório é necessario usar a tag --recursive para carregar os submodules que dependem de outros repositórios.
#### git clone https://github.com/guidovin/dialogSocialDemo.git --recursive

#### Instruções para rodar o projeto:

cd dialogSocialDemo && cd challenge_backend && yarn install && yarn start; 
cd dialogSocialDemo && cd challenge_frontend && yarn install && yarn start;

Npm can be used instead of yarn.
Built with Node v12.18.2.

#### curl para chamada da api
curl 'http://localhost:4000/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: http://localhost:4000' --data-binary '{"query":"# Write your query or mutation here\n{\n  list {\n\t\tid\n\t\tindex\n\t\tpicture\n\t\tage\n    eyeColor\n\t\tname\n\t\tcompany\n\t\temail\n\t\tphone\n\t\tgreeting\n      \n  }\n}"}' --compressed

#### curl para chamada da api com parametro "Cecilia"
'http://localhost:4000/graphql' -H 'Accept-Encoding: gzip, deflate, br' -H 'Content-Type: application/json' -H 'Accept: application/json' -H 'Connection: keep-alive' -H 'DNT: 1' -H 'Origin: http://localhost:4000' --data-binary '{"query":"# Write your query or mutation here\n{\n  list(name:\"Cecilia\"){\n\t\tid\n\t\tindex\n\t\tpicture\n\t\tage\n    eyeColor\n\t\tname\n\t\tcompany\n\t\temail\n\t\tphone\n\t\tgreeting\n      \n  }\n}"}' --compressed

O tempo de loading dos links de imagem no mock db.json são bem grandes, então adicionei um spinner de loading enquanto ainda não estão prontas (instantaneo se já na cache)
