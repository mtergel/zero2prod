### Using PgPool instead of PgConnection

Use PgPool to share a pointer to connection to database, sqlx query executor requires a &mut connection.
