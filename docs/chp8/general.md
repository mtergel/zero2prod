## Errors

Errors serve two main purposes.

- Control flow (determine what do next); -> for machines -> Scripted -> Enums
- Reporting (investigate, after the fact, what went wrong); -> for humans -> provide context

We also distinguish errors based on their location:

- Internal (function calling another function within our application)
- At the edge (an API request that we failed to fulfill)

### Running single test with logs

```sh
export RUST_LOG="sqlx=error,info"
export TEST_LOG=enabled
cargo t subscribe_fails_if_there_is_a_fatal_database_error | bunyan
```

### Traits, impl

- Debug -> for programmers -> return as much information
- Display -> brief description with the essential amount of context

## Errors for Control Flow

Choosing the appropriate HTTP status code when an error occurs is a concern of the
request handler, it should not leak elsewhere.


|              | Internal               | At the edge   |
|--------------|------------------------|---------------|
| Control Flow | Types, methods, fields | Status codes  |
| Reporting    | Logs/traces            | Response body |
