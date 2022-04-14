# Desafio Técnico - Pessoa desenvolvedora Back-end Junior
Na DIWE, atualmente trabalhamos preferencialmente com JavaScript, TypeScript, GoLang e PHP, mas fique à vontade para escolher a tecnologia que mais se adeque ao seu projeto. Já no banco de dados costumamos utilizar MariaDB e MongoDB para dados não estruturados.

# Objetivo do teste
O desafio consiste na criação de uma api que servirá dados a um sistema de controle financeiro e deverá contar com as caracteristicas citadas abaixo.


# Estrutura de dados
Abaixo listarei as tabelas que o banco de dados deve constar, lembrando que você está livre para reformular esta estrutura (relacional ou não), porém lembre-se de documentar sua nova estrutura sinalizando as alterações e os seus motivos.

As tabelas são :
## Usuários (users)
| id | full_name | email | password | created_at | updated_at | 
| --- | --- | --- | --- | --- | --- | 
|  auto increment integer | required string (120) | required string (200) | require string (200) | required timestamp | required timestamp |


## Status (statuses)
| id | name | 
| --- | --- |
|  auto increment integer | required string (100) |

## Tipo de lançamentos (types)
| id | name | 
| --- | --- |
|  auto increment integer | required string (100) |

## Lançamentos (financial_entries)
| id | status_id | user_id | type_id | amount | description | created_at | updated_at | 
| --- | --- | --- | --- | --- | --- | --- | --- | 
|  auto increment integer | foreign key de statuses | integer foreign key de users | foreign key de types | required integer, valor convertido (exemplo, no caso de R$ 10,59 deve ser gravado 1059) | required string (255) | required timestamp | required timestamp |

# Regras de negócio
#### Rotas abertas
A api deve conta com apenas uma rota aberta do tipo POST que será responsável pelo login, que ao se receber credenciais válidas (email e password) retornará um token jwt ( boas práticas de tempo de expiração, renovação de token serão considerados diferenciais ), que poderá ser utilizado para autenticar as demais rotas.

#### Rotas fechadas
A api também deve conter as seguintes rotas fechadas :
- [GET] - '/types', por está rota o usuário autenticado deverá receber uma lista de todos os tipos de lançamentos.
- [GET] - '/statuses', por está rota o usuário autenticado deverá receber uma lista de todos os status.
- [POST] - '/financial-entries', por está rota o usuário autenticado deverá enviar um JSON contendo amount, description e status_id e type_id e o backend deverá validar os dados e gravar o lançamento em questão setando o user_id automáticamente.
- [GET] - '/financial-entries', por está rota o usuário autenticado deverá conseguir consultar todos seus lançamentos ( implementação de filtros será considerada diferencial )
- [PUT] - '/financial-entries/{id}', por está rota o usuário autenticado deverá conseguir receber e alterar apenas os campos amount e status_id

# Oque esperamos de você
- Documentação, crie um arquivo readme e documente oque achar necessário.
- Boas práticas, padrãonização e organização é essencial para conseguirmos avaliar bem seu desempenho.
- Testes, teste bem sua aplicação antes de entrega-la, implementação de testes unitários será considerada diferencial.
- Atente-se para segurança das rotas, valide bem os parametros recebidos em cada rota.
- Criar collection postman de cada rota que sua api contém para facilitar a avaliação.

# Oque não avaliaremos
- Aplicação frontend, testaremos tudo via postman.

# Oque não avaliaremos
Ao fim do teste, criar um repositório aberto no github e nos enviar.

Boa sorte e obrigado por participar do nosso processo!

