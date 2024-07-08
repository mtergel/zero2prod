## Serialisation in Rust: Serde

Serde is a framework for serializing and deserializing Rust data structures
eﬀiciently and generically. Serde defines interfaces.

#[derive(Serialize)] #[derive(Deserialize)]
These macros will parse the definition of your type and automatically generate for you the right implementation.
