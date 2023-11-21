## What is the Guard

The guard pattern ensures that resources are required and released in a safe. In Rust, this concept is often implemented through its ownership system


## Why
Guard usually use in concurrency programming
+ Thread safety
+ Prevention of Data Races
+ Synchronization
+ ...



## Example
```rust
use std::sync::Mutex;

fn main() {
    // Create a Mutex-protected counter
    let counter = Mutex::new(0);

    // Lock the mutex to get exclusive access
    let mut guard = counter.lock().unwrap();

    // Increment the counter
    *guard += 1;

    // MutexGuard is automatically released when it goes out of scope
    println!("Counter value: {}", *guard);
    // Counter value: 1
}
```