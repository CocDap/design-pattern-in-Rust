## What is the Builder Pattern 
Using an intermediate type to build the instance of object

## When is it useful
+ Lots of optional value
+ Lots of business logic at creation time 
+ Lots of parameters


```rust
// Create builder
pub struct Builder {
    name: Option<String>,
    stack_size: Option<usize>
}

impl Builder {
    // Create initialized value
    fn new() -> Self {
        Self {
            name: None,
            stack_size: None
        }
        
    }
    // Create name 
    fn name(mut self, name: String) -> Self {
        self.name = Some(name);
        self
    }
    // Create stack size
    fn stack_size(mut self, stack_size: usize) -> Self {
        self.stack_size = Some(stack_size);
        self
    } 
}

```