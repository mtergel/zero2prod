# General

### Running, inner dev loop

```sh
cargo watch -x check -x test -x run
```

Tests

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

Make a habit of revisiting user stories throughout the lifecycle of a project.
When you spend time workign on a problem you end up deeping your understanding of its domain.
You often acquire a more precise language that can used to refine earlier attempts of describing the
the desired functionality.

Example

Old one

```
As the blog author,
I want to send an email to all my subscribers,
So that I can notify them when new content is published.
```

New one

```
As the blog author,
I want to send an email to all my confirmed subscribers, So that I can notify them when new content is published.
```
