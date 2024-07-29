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
