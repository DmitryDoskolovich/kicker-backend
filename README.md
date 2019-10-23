# Kicker

## Prerequisites

* Install [Docker Engine](https://hub.docker.com/search?q=&type=edition&offering=community)
* Install [Yarn](https://yarnpkg.com/en/docs/install) package manager

## Run services

```bash
# Install project's dependencies
yarn install

# Start project's services
# - api (nodejs app)
# - mysql (database server)
# - adminer (3rd party database management app)
docker-compose up --detach
```

## Prepare database

```bash
# Login to api service container
docker-compose exec api bash

# Apply database migrations
yarn sequelize db:migrate

# Populate database with default data
yarn sequelize db:seed:all
```

If everything goes fine you will be able to get users list by calling http://localhost:3000/api/users

## Debug

```bash
# Display logs from api service
docker-compose logs --follow --tail=100 api

# Restart api service
docker-compose restart api
```

## Database management

It's possible to explore database state by Adminer on http://localhost:8080. Use credentials configured for mysql service.
