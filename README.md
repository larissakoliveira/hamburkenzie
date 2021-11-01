                                                        Bem-vindx a api Hamburkenzie!

                                            O url base da API é https://hamburkenzie.herokuapp.com/

                                                                ENDPOINTS:
                                                                /users/login/
                                                                /users/register/
                                                                /cart/
                                                                /products/


____________________________________________________________________________________________________________________________________________________________
Para fazer a criação de um novo usuário: 

POST /users/register/ - FORMATO DA REQUISIÇÃO
{
"email": "johndoe@email.com",
"password": "123456",
"name": "John Doe"
}

____________________________________________________________________________________________________________________________________________________________
Login do usuário: 

POST /users/login/ - FORMATO DA REQUISIÇÃO
{
"email": "johndoe@email.com",
"password": "123456",
}
____________________________________________________________________________________________________________________________________________________________
Obter a lista de todos os produtos disponíveis na loja mesmo sem estar logado

GET /products/ 

____________________________________________________________________________________________________________________________________________________________

        Rotas que necessitam de autorização!
ADICIONAR produto ao carrinho           POST     /cart/
LISTAR produtos no carrinho             GET      /cart/?userId=id
RETIRAR produto do carrinho             DELETE   /cart/:id
ATUALIZAR quantidade do produto         PATCH    /cart/id     


Necessitam de autorização e devem ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:
Authorization: Bearer {token}

Após o usuário estar logado, ele deve conseguir ver o que tem em seu carrinho de compras e adicionar mais produtos à ele.


Para ADICIONAR produto ao carrinho, informe no corpo da requisição o id de usuário (userId)

POST /cart/   FORMATO DA REQUISIÇÃO

{
     "product": "McShake Nutella",
      "image": "https://s3-alpha-sig.figma.com/img/1418/8d02/bff95df5c4ffe3b30eb1fc1d20d11c67?Expires=1636934400&Signature=V~Gg~czQ8Ite9oRrZb9KATPcDSYuylX9pydWe3QLrCqL~ji6nY-i7yh1g-Y8ZymVDujBIL8U4kMrKLbkX~5iKsKPmYeGTLabX9IGay2dOnuCCsI~BCHmmkZmSNL7uL0kzwCenc1lE4JKfoukbfsVQ2X4z5YimJq5NzU~xSrDLVt7Rs0-8wdH-jT3q8OxmTdo7~zbmShUqcK3aryBsxk-FKgTwklzJ~XYmnBsQotrOD8QeLuxSG4Yv3eDelzKPOxkB5O6D38yxrleLXqF~vbo4EtWUC-8gcYSyfJsWcO-tSRhbWyZeUOu~hGA-tvfBe2HLah3G6rvE57cQfJejq7C4Q__&Key-Pair-Id=APKAINTVSUGEWH5XD5UA",
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