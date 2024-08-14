## Auth

Few types

- Something they know: Password etc
- Something they have: Smartphone, u2f key etc
- Something they are: Biometrics

Each have their own flaws so its best to combine them. Multi-Factor Authentication

## Basic Authentication - RFC 2617

Header must have
`Authorization: Basic <encoded credential>` -> cred is base64 of `{username}:{password}`

According to spec, we need to partition our API into realms

If no header respond with 401 + `WWW-Authenticate` header.

### Password storage

Storing raw user passwords is not a good idea.
Check using hash or something security depends of `f` fn.

SHA3-256.

### Preimage Attack

Finding a input string hash matches the one in database.
If n > 128 considered unfeasible SHA3-256 is ok

### Dictionary Attack

Cryptographic algorithms are designed to be fast, so we could be hit with a dictionary attack.
We need something much slower
