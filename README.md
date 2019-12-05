This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

# API
### Tech stack:
  - Node JS
  - TypeScript
  - GraphQL
  - Postgres
### Installations
#### Code Setup
  - Pre-requisites
    - Install [node JS](https://nodejs.org/en/download/)
    - Install [Yarn](https://yarnpkg.com/lang/en/docs/install/#mac-stable) globally
  - Clone the repo
  - Run the following command to install the node modules
    - `yarn`
  - Run the following command to start the API server
    - `yarn start`
#
#### DB setup
##### Install postgres
  - Best and easier way is to install it through [PostgresApp](https://postgresapp.com/)
    - Download and install it and run the DB server
  - Install [Postico](https://eggerapps.at/postico/) to manage or interact with DB
    - Once installation is done, create a database with the name of `bullseye_development`
  - Download DB dump from heroku:
    - Install [heroku CLI tool](https://devcenter.heroku.com/articles/heroku-cli)
    - Once installation is done: run the following command
      - `Heroku login`
      - `git remote add staging https://git.heroku.com/be-api-staging.git`
      - `git remote add prod https://git.heroku.com/be-api-production.git`
      - `heroku pg:backups:capture  --remote staging`
      - `heroku pg:backups:download  --remote staging`
      - Once dump is downloaded, run the following command
        - `pg_restore --verbose --clean --no-acl --no-owner -h localhost -U postgres -d bullseye_development ./latest.dump`
#
#### Deployment
##### Staging
  - There is branch called demos. This branch is representing the staging server.
  - Once the code to be deployed is merged in demos branch, run the following commands.
    - `git push staging demos:master`
    - `heroku pg:backups:capture --remote staging`
    - `heroku run bash --remote staging`
    - `sequelize db:migrate`

##### Production
  - Master branding is representing production.
  - Once the code to be deployed is merged in master branch, run the following commands.
    - `git push prod master`
    - `heroku maintenance:on --remote prod`
    - `heroku pg:backups:capture --remote prod`
    - `heroku run bash --remote prod`
      - `sequelize db:migrate`
    - `heroku maintenance:off --remote prod`

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).
