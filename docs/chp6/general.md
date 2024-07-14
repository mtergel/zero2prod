# General

## Functions
- validation function: it tells us that, at a certian point in the executaion
flow of our program, a set of conditions is verified.
- parsing function: a routine that accepts unstructed input and, if a set of conditions holds,
returns us a more structed output!, an output that structurally guarantees that the
invariants we care about hold from that point onwards.

## Type-Driven Development
Above parsing function it implemented using types!
Using this approach from a function we can make a ***local*** judgement, no need to go and
check all calling sites.


## Validation
- Unit tests, validator crate for hard cases
