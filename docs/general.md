# General

### Running, inner dev loop

```sh
cargo watch -x check -x test -x run
```

### Tests

A good test suite is, first and foremost, a risk-mitigation measure.
Automated tests reduce the risk associated with changes to an existing codebase -
most regressions and bugs are caught in the CI pipeline and never reach users.
The team is therefore empowered to iterate faster and release more often.

- Embedded
  This module has privileged access to the code living next to it, structs,
  methods, fields, functions that have not been marked as public. Use these to
  test them.
- External tests folder and doc tests.
  Mostly for integration testing, exactly the same way a user would.

We converted the binary into a library to share the code for testing.

Inner Development Loop

- Make a change;
- Compile the application;
- Run tests;
- Run the application;
