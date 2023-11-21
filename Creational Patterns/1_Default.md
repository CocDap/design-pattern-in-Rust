## What is the Default Pattern 
Default pattern is used to create an instance of object with no argument. In other words, this is inialization step of object

## Where it appears

+ `new` static method 
```rust
    Vec::new(), String::new()
```
+ `Default` trait 

## Default trait vs new method

We should use both 

## How it works

```rust
// Define struct 
struct Example(i32);

impl Example {
    // Define new static method 
    fn new() -> Self {
        Example::default()
    }
}

// Implement trait Default to get initial value
impl Default for Example {
    fn default() -> Self {
        Example(0)
    }
}
```

## Some cases to be cautious when using Default or new.

1. **Example 1**: 

+ Object Id will be the same for all instances 

```rust
struct Project {
    id: u64,
    name: String,
    description: String 
}
```
+ How to fix: Generate random id 

```rust
use rand::Rng;

fn generate_id_random() -> u64 {
    let mut rng = rand::thread_rng();
    rng.gen::<u64>()
}

impl Default for Project {
    fn default() -> Self {
        let id = generate_id_random();
        Self {
            id,
            name: String::new(),
            description: String::new()  
        }
    }
}
```

2. **Example 2**:
+ Coordinate with `Default` value 

```rust
struct Coordinate(f32, f32);

impl Default for Coordinate {
    fn default() -> Coordinate {
        Coordinate(0.0, 0.0)
    }
}

```

-> Unreasonable when initializing latitude and longitude with a value of 0.0 or fixed value

+ The first solution : use `new` method with 2 dynamic args: lat and long

```rust
impl Coordinate {
    fn new(lat: f32, long: f32) -> Self {
        Self(lat, long)
    }
}
```

+ The second solution: use `Option`

## Derive Default Trait 
Rather than manually implementing the `Default` trait for types, we can leverage the `derive` Default feature provided by the Rust Standard Library

```rust
#[derive(Default)]
enum Size {
    Small,
    #[default]
    Medium,
    Large
}
```
-> Default value should be `Size::Medium`


