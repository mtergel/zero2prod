# General

### Running, inner dev loop

```sh
cargo watch -x check -x test -x run
```

### Tests

- Embedded
  This module has privileged access to the code living next to it, structs,
  methods, fields, functions that have not been marked as public. Use these to
  test them.
- External tests folder and doc tests.
  Mostly for integration testing, exactly the same way a user would.

We converted the binary into a library to share the code for testing.
