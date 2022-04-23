                                                        Bem-vindx a api Hamburkenzie!

                                            O url base da API é https://hamburkenzie.herokuapp.com/

                                                                ENDPOINTS:
                                                                /login/
                                                                /register/
                                                                /cart/
                                                                /products/


____________________________________________________________________________________________________________________________________________________________

### Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login.

Cadastro
POST /register
POST /signup
POST /users

CORPO DA REQUISIÇÃO:

```json 
{
  "email": "johndoe@email.com",
  "password": "123456",
  "name": "John Doe"
}
```

RESULTADO ESPERADO:
```json 
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlQG9paS5jb20iLCJpYXQiOjE2MzYzMTgzNTgsImV4cCI6MTYzNjMyMTk1OCwic3ViIjoiNSJ9.lfhWHqUMz7T2R2i-IATV6YEyKA6-dITIBUEEwACFByY",
  "user": {
    "email": "johndoe@email.com",
    "name": "John Doe"
    "id": 1
  }
}
```

#### Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password. Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

_____________________________________________________________________________________________________________________________________________________________

Login
POST /login
POST /signin

CORPO DA REQUISIÇÃO
```json 
{
"email": "johndoe@email.com",
"password": "123456",
}
```
#### RESULTADO ESPERADO
```json 
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Imtra0Bra2suY29tIiwiaWF0IjoxNjM2MzE4OTI2LCJleHAiOjE2MzYzMjI1MjYsInN1YiI6IjYifQ.5ig3xQkws3FW83F4pOPM-vo_Ptw2WxjynhbT9gp9j8E",
  "user": {
    "email": "johndoe@email.com",
    "name": "John",
    "id": 1
  }
}
```
#### Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"


____________________________________________________________________________________________________________________________________________________________

Obter a lista de todos os produtos disponíveis na loja mesmo sem estar logado

SEM CORPO E SEM AUTORIZAÇÃO,
RESPOSTA ESPERADA
```json 
[
  {
    "image": "https://i.ibb.co/FHh5Cc8/hamburguer.png",
    "title": "Hamburguer",
    "category": "Sanduíches",
    "price": 14,
    "id": 1
  },
  {
    "image": "https://i.ibb.co/wy0BjYh/xburguer.png",
    "title": "X-Burguer",
    "category": "Sanduíches",
    "price": 16,
    "id": 2
  },
  {
    "image": "https://i.ibb.co/dQCBhxS/bigkenzie.png",
    "title": "Big Kenzie",
    "category": "Sanduíches",
    "price": 18,
    "id": 3
  },
  {
    "image": "https://i.ibb.co/ZYr9G8h/combokenzie.png",
    "title": "Combo Kenzie",
    "category": "Combos",
    "price": 26,
    "id": 4
  },
  {
    "image": "https://i.ibb.co/MMddrWd/fantaguarana.png",
    "title": "Fanta Guaraná",
    "category": "Bebidas",
    "price": 5,
    "id": 5
  },
  {
    "image": "https://i.ibb.co/tHVczNt/cocacola.png",
    "title": "Coca-Cola",
    "category": "Bebidas",
    "price": 7,
    "id": 6
  },
  {
    "image": "https://i.ibb.co/PChgTpp/ovomaltine.png",
    "title": "McShake Ovomaltine",
    "category": "Sobremesas",
    "price": 10,
    "id": 7
  },
  {
    "image": "https://i.ibb.co/mq8gMpH/shakeovomaltine.png",
    "title": "McShake Nutella",
    "category": "Sobremesas",
    "price": 10,
    "id": 8
  }
]
```
GET /products - FORMATO DE RESPOSTA - STATUS 200

____________________________________________________________________________________________________________________________________________________________

        Rotas que necessitam de autorização!

ADICIONAR produto ao carrinho           POST     /cart/
LISTAR produtos no carrinho             GET      /cart/?userId=id
RETIRAR produto do carrinho             DELETE   /cart/id
ATUALIZAR quantidade do produto         PATCH    /cart/id     


Necessitam de autorização e devem ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:
Authorization: Bearer {token}
Após o usuário estar logado, ele deve conseguir ver o que tem em seu carrinho de compras e adicionar mais produtos à ele.


Para ADICIONAR produto ao carrinho, informe no corpo da requisição o id de usuário (userId)

POST /cart/   FORMATO DA REQUISIÇÃO

{
     "product": "McShake Nutella",
      "image": "https://i.ibb.co/mq8gMpH/shakeovomaltine.png",
      "category": "Sobremesas",
      "price": 10,
      "userId": 8,
      "quantity": 1,
    }

Para VISUALIZAR seu carrinho, informe no corpo da requisição o id de usuário (userId)

GET /cart/?userId=id

Para ATUALIZAR quantidade de algum produto no teu carrinho, informe no corpo da requisição a quantidade

PATCH /cart/:id

    {
      "quantity": 2,
    }


Para REMOVER algum item do teu carrinho, informe no corpo da requisição o id de usuário (userId)

DELETE /cart/:id  
