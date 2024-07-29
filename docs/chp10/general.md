To authenticate a user, we need reproducibility: we must run the very same hashing routine every single time.
To keep authenticating old users we must store, next to each, the exact set of load parameters used to compute it.

Naive approach - add three columns + Algothim -> tedious

## PHC string

`${algorithm}${algorithm version}${$-separated algorithm parameters}${hash}${salt}`

Example
`$argon2id$v=19$m=65536,t=2,p=1$gZiV/M1gPc22ElAH/Jh1Hw$CWOrkoo7oJBQ/iyh7uJ0LO2aLEfrHwTWllSAxT0zRn`

## Async / Polling

Offload our CPU-intensive task to a separate threadpool using `tokio::task::spawn_blocking`.
Those threads are reserved for blocking operations and do not interfere with the scheduling of async tasks.

## Security

TSL -> HTTPS

Interaction Types

- Machine to Machine
- Person via browser

  'Basic' Authentication required the client to present their credentials on every single request.
  We need a way to remember that a user authenticated a few moments ago - i.e. to attach some kind of state
  to a sequence of requests coming from the same browser. This is accomplished using sessions.

  A user is asked to authenticate once, via a login form:
  if successful, the server generates a one-time secret - an authenticated session token. The token is stored in the browser as a secure cookie.
  Sessions, unlike passwords, are designed to expire. (session-based authentication)

  Federated Identity
  Social logins rely on identity federation - we delegate the authentication step to a third-party identity provider, which in turn shares with us the pieces
  of information we asked for.

- Another API, on behalf of a person
  In this case, the third-party service is not authorised, on its onw, to perform any action against our API.
  The third-party service can only perform actions against our API if a user grants them access, scoped to thier set of permissions

  'Basic' authentication would be a very poor fit here: we do not want to share our password with a third-party-app.
  This is a textbook scenario for OAuth2 - the third-party never gets to see our username and password.
  They receive an opaque access token from the authentication server which our API knows how to inspect to grant (or deny) access.
