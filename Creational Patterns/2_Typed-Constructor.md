## What is the Typed Constructor

Rust doesnt have constructors -> new methods with arguments that are strongly typed, properly initialized values 

## Why use them
+ Leveraging of type system to prevent data corruption and logic errors appearing at runtime

## Where it appears

1. Fake number: the problem of overloading data type. ex: row ID, phone number, credit card, ... should not support addition or substraction 
+ Example: `id` is numerical data, it can add or substract. But in this case, we have course_id that represent identifer of the course

```rust
struct Course {
    id: u32
}

impl Course {
    fn new(id: u32) -> Self {
        ...
    }
}
```

+ Solution : Wrap new type -> Wrap `u32` 
```rust
struct Id(u32);

struct Course {
    id: Id
}

impl Course {
    fn new(id: Id) -> Self {
        ...
    }
}
```

2. Stringly typed data: validate and compare string repeatly
+ Example : the remaning matching string is invalid -> panic 
```rust
match size {
    "s" => ...,
    "l" => ...,
    "m" => ...,
    _ => panic!()
}
```

+ Solution: Define enum -> parse string to enum

```rust
enum Size {S , M, L}

impl std::str::FromStr for Size {
    ...
}
let parsed ="s".parse::<Size>();
```
