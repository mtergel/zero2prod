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
