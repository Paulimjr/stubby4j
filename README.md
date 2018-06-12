# Docker - docker-compose.yml

version: '2'
services:
 stubby4j:
   image: sandokandias/stubby4j-docker
   ports:
     - "8883:8883"
   environment:
     STUBBY_PORT: 8883
   volumes:
     - /api.yml:/usr/local/stubby.yml

# Stubby4j - api.yml

- request:
    method: GET
    url: ^/buscatoken$

  response:
    status: 201
    headers:
      content-type: application/json
    body: >
     {
       "dsDadosResposta": {
         "dadosAutenticacao": {
           "token": "779DA4E1-A66D-4755-BCB5-A8AD47696774",
           "validade": "2018-06-12 12:49:27"
         }
       }
     }

- request:
    method: GET
    url: ^/buscaperfil$

  response:
    status: 201
    headers:
      content-type: application/json
    body: >
     {
       "dsBuscaPerfil": {
         "perfil": {
           "nome": "Marcelo Cheruti Caetano",
           "email": "marcel@zup.com.br",
           "telefone": "0112121212",
           "registroID": "323232",
           "ipphone": "#00527323"
         }
       }
     }
     
