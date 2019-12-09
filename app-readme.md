This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

# Frontend - Student Portal
### Tech stack:
  - React
  - TypeScript
  - GraphQL
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
#### Deployment
##### Staging
  - There is branch called demos. This branch is representing the staging server.
  - Once the code to be deployed is merged in demos branch, run the following commands.
    - `git push prod master`
    - `heroku maintenance:on --remote prod`
    - `heroku pg:backups:capture --remote prod`
    - `heroku run bash --remote prod`
      - `sequelize db:migrate`
    - `heroku maintenance:off --remote prod`

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).
