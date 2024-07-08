### Structure of Actix

- **HttpServer**, in other words, handles all transport level concerns.
- **App** is where all your application logic lives, routing, middleware etc...

### Endpoint - Route

Simplest way is to use `route` method.

```rust
.route("/", web::get().to(greet))
```

#### Request handler

```rust
async fn greet(req: HttpRequest) -> impl Responder {
    [...]
}
```

Responder trait -> can be converted into HttpResponse.

### Main

`#[actix_web::main]` -> Marks async main function as the Actix Web system entry-point.

### Extractors

Extract certain pieces of information from an incoming request. Path, Query, Json etc...
