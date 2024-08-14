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

#### Preimage Attack

Finding a input string hash matches the one in database.
If n > 128 considered unfeasible SHA3-256 is ok

#### Dictionary Attack

Cryptographic algorithms are designed to be fast, so we could be hit with a dictionary attack.
We need something much slower

### Argon2

OWASP recommends - Argon2, bcrypt, scrypt, PBKDF2

- Use Argon2id with a minimum configuration of 15 MiB of memory, an iteration count of 2, and 1 degree of parallelism.
- If Argon2id is not available, use bcrypt with a work factor of 10 or more and with a password limit of 72 bytes.
- For legacy systems using scrypt, use a minimum CPU/memory cost parameter of (2^16), a minimum block size of 8 (1024 bytes), and a parallelization parameter of 1.
- If FIPS-140 compliance is required, use PBKDF2 with a work factor of 310,000 or more and set with an internal hash function of HMAC-SHA-256.
- Consider using a pepper to provide additional defense in depth (though alone, it provides no additional secure characteristics)

To authenticate a user, we need reproducibility: we must run the very same hashing routine every single time.
The PHC string format provides a standard representation for a password hash: it includes the hash itself, the salt, the algorithm and all its associated parameters.

Example:

```
# ${algorithm}${algorithm version}${$-separated algorithm parameters}${hash}${salt}
$argon2id$v=19$m=65536,t=2,p=1$gZiV/M1gPc22ElAH/Jh1Hw$CWOrkoo7oJBQ/iyh7uJ0LO2aLEfrHwTWllSAxT0zRno
```

If an attacker knows at least one valid username, they can inspect the server response times81 to confirm if another username exists or not
we are looking at a potential user enumeration vulnerability. Is this an issue?

To prevent

1. Remove the timing difference
2. Limit the number of failed auth attempts
