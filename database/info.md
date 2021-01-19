# Databases


## Postgres

run postgres in a docker container 
[article](https://medium.com/better-programming/connect-from-local-machine-to-postgresql-docker-container-f785f00461a7)

after installing the postgres image of choice 

```
docker run -d --name dev-postgres -e POSTGRES_PASSWORD=password -v ${HOME}/postgres-data/:/var/lib/postgresql/data -p 5432:5432 postgres

# after container starts you may want to check that psql and everything is running in the container properly
docker exec -it dev-postgres bash
psql 

```

### USERS
Here is an article i used for learning about the interactive user in postgresql
[article](https://ubiq.co/database-blog/create-user-postgresql/)

create a user for remote login


```
docker exec -it dev-postgres bash

su - postgres
createuser --interactive --pwprompt
```

