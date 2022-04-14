# Desafio Técnico - Pessoa desenvolvedora Back-end Junior
Na DIWE, atualmente trabalhamos preferencialmente com JavaScript, TypeScript, GoLang e PHP, mas fique à vontade para escolher a tecnologia que mais se adeque ao seu projeto. Já no banco de dados costumamos utilizar Mysql, MariaDB e MongoDB para dados não relacionais.

# Objetivo do teste
O desafio consiste na criação de uma API  que servirá dados a um sistema de controle financeiro e deverá contar com as caracteristicas citadas abaixo.


# Estrutura de dados
Abaixo listarei as tabelas que o banco de dados deve conter. Lembrando que você está livre para reformular esta estrutura (relacional ou não), porém lembre-se de documentar a nova estrutura sinalizando as alterações e sua motivação.

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
A API deve contar com apenas uma rota aberta do tipo POST que será responsável pelo login do usuário. 
Ao receber credenciais válidas (email e password) retornará um token JWT (boas práticas de tempo de expiração e renovação de token serão considerados diferenciais).

#### Rotas fechadas
A API também deve conter as seguintes rotas fechadas :
- [GET] - '/types', por está rota o usuário autenticado deverá receber uma lista de todos os tipos de lançamentos.
- [GET] - '/statuses', por está rota o usuário autenticado deverá receber uma lista de todos os status.
- [POST] - '/financial-entries', por está rota o usuário autenticado deverá enviar um JSON contendo: amount, description, status_id, type_id. O backend deverá validar os dados e gravar o lançamento, setando o user_id automáticamente.
- [GET] - '/financial-entries', por está rota o usuário autenticado deverá conseguir consultar todos seus lançamentos (implementação de filtros será considerada diferencial).
- [PUT] - '/financial-entries/{id}', por está rota o usuário autenticado deverá conseguir receber e alterar apenas os campos amount e status_id.
- [DELETE] - '/financial-entries/{id}', por está rota o usuário autenticado deverá conseguir remover o lançamento.

# Oque esperamos de você
- Documentação. Crie um arquivo "readme" e documente oque achar necessário.
- Boas práticas. Padronização e organização é essencial para conseguirmos avaliar bem seu desempenho.
- Testes. Teste bem sua aplicação antes de entregá-la, a implementação de testes unitários será considerada diferencial.
- Atente-se para segurança das rotas, valide bem os parâmetros recebidos em cada rota.
- Criar collection dos endpoints para facilitar a avaliação.

# Oque não avaliaremos
- Aplicação frontend, testaremos tudo via postman/insomnia.

# Entrega do Teste
Ao fim do teste, crie um repositório aberto no github e o compartilhe com os seguintes emails:
-   vinicius.silva@diwe.com.br
-   maicon.passos@diwe.com.br
-   vinicius.bassalobre@diwe.com.br.

Boa sorte e obrigado por participar do nosso processo seletivo!
