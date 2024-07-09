## Beware of unknown unknowns

### Observability

Being able to ask arbitrary questions about your environment without having
to know ahead of time what you wanted to ask.

arbitrary is a strong word, so in practice we will settle for sufficiently observable
to enable use to deliver the level of service we promised to our users.
Our application is suﬀiciently observable if we can triage the issue from the
breadcrumbs of information he has provided us.

To build an observable system we need:

- instrument our application to collect high-quality telemetry data;
- access to tools and systems to efficiently slice, dice and manipulate the data
  to find answers.

### Logging

Common type of telemetry data.

Loglevels:

- trace: lowest level -> extremely verbose and have a low signal-to-noise ratio, etc TCP packet
- debug
- info
- warn
- error: report serious failures that might have user impact

`log::error!("Failed to execute query: {:?}", e)` notice the `{:?}` <- displays more raw view

When dealing with multiple request we need a way to correlate all logs related to the same request.
This is usually achieved using a request id aka correlation id

### Structured Logging

Ensure that request_id is included in all log records. Logs are the wrong abstraction for these
tree like processing pipleline.

## Tracing

tracing expands upon logging-style diagnostics

`subscriber_email = %form.email,` -> % means to use display implementation
