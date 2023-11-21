## What is Clone

In Rust, `Clone` is a trait that defines a method called `clone()`. Types that implement the `Clone` trait can create a duplicate, or clone, of an instance. The `clone()` method is used to produce a new instance with the same data as the original.

## Advantages
+ Easily to use 
+ Solve ownership problem 
## Disadvantages
+ Duplicate 
+ Extra memory use 

## Example
-> If we remove `.clone()`, compiler fail
-> `value borrowed here after move`
```rust
fn main() {
    let a = String::from("Hello");
    let b = a.clone();
    println!("{a}") 
    //Hello
}
```

## Avoid using Clone too much
Using Arc( https://doc.rust-lang.org/std/sync/struct.Arc.html) or RC( https://doc.rust-lang.org/std/rc/struct.Rc.html)


```rust
use std::sync::Arc;

fn main() {
    let a = Arc::new(String::from("Hello"));
    let b = Arc::clone(&a);

    println!("a: {}", a);
    println!("b: {}", b);
}
```