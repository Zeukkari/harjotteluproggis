# Harjotteliproggis: Todo-appseja

## Kerrattavia juttuja

- Backend-devaus
- Tietokantahommat
  - Relaatiotietokannat
  - NoSQL-tietokannat
- API:n suunnittelu
  - RESTinä
- Microservice-arkkitehtuurit
- JWT-tokenit ja autentikaatiohommat
- Konttien käyttö ja DevOps-hommat

## Testirepoja

- https://github.com/Zeukkari/postgres-express-node-tutorial
- https://github.com/Zeukkari/user-authentication-nodejs

## Devausserveri

- https://sample-frontend-zeukkari.herokuapp.com


## Resursseja

PlantUML:

- https://stackoverflow.com/questions/32203610/how-to-integrate-uml-diagrams-into-gitlab-or-github
- https://real-world-plantuml.com
- https://plantuml.com/

~~yUML~~

~~LucidChart~~

Tietokantamalleja:

- http://www.databaseanswers.org/data_models/

Pilvihommia:

- https://docs.microsoft.com/en-gb/learn/paths/azure-fundamentals/
- https://github.com/haraldfianbakken/MCW-Modern-cloud-apps/

Backend-devausta:

Node.js + Express + SQL:
- https://scotch.io/tutorials/getting-started-with-node-express-and-postgres-using-sequelize

Node.js + Express + NoSQL:
- https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/mongoose

## Arkkitehtuuri

![](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/Zeukkari/harjotteluproggis/master/arkkitehtuuri.puml)

## ER-malli

![](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/Zeukkari/harjotteluproggis/master/tietokanta.puml)

## API

### initial users and rols step

> 1.  post `/api/initialize` to create roles and super admin account
> 2.  post `api/users` - create new account
> 3.  post `api/users/login` - login and get jwt token then frontend can store this token to use other api
> 4.  use request header: `{Authorization: (jwt token)}` when use other api

### Authentication

Check token valid

- `/api/users/logout`

Check token valid and expired

- `/api/users/:id`
- `/api/users/me`

### Permissions(roles)

- admin
  _ `delete` - other users and roles
  _ `get` - all users and roles
  _ `post` - user and role
  _ `put` - all users and other user's role

- user
  _ `delete` - self
  _ `get` - self
  _ `post` - signup
  _ `put` - self but cannot update role

### Documentation

- request header - Authorization (json web token)

- **api** - api root

- **api/initialize**

  `post - create roles and admin user`

- **api/users**

  `post - create new user`

* **api/users/login**

  `post - login and get jwt token`

* **api/users/me**

  `get - get current user info`

* **api/users/:id**

  `delete - delete user`

  `get - get user info`

  `put - update username、displayName only superadmin can update other user's role`

* **api/todo**

  `get - list todos`

  `delete - delete all todos`

  `post - create new todo`

* **api/todo/:id**

  `get - get todo item`

  `delete - delete todo item`
