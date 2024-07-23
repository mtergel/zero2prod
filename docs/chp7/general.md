### Reqwest

Reqwest, every time a Client instance is created reqwest initialises a connection
pool under the hood.
To leverage this connection pool we need to reuse the same Client across multiple requests.
Client::clone does not create a new connection pool - we just clone a pointer to the
underlying pool.

Failures

- non-success status
- slow responses

As a rule of thumb: every time you are performing an IO operation, always set a timeout!

### Zero downtime Deployments

A user should be able to use the service before, during and after the rollout of a new version
of the application to production. This is very important if you are practising continuous deployment.

#### New Mandatory Column

- Add as Optional -> migrate local database -> migrate production database
- Start using the new column -> deploy the new version to prod
- Backfill and Mark as NOT NULL -> migrate local database -> migrate production database

#### New Table

- Create table -> migrate local database -> migrate production -> deploy
