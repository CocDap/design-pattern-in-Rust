## What is the NewType 
New Type Pattern is designed for wrapping a existing type to new type 

## Why
The newtype pattern can help enforce type safety, encapsulate implementation details and increase the expressiveness of your code

## Example

```rust
    struct Email(String);
```
-> String represent email info  -> describe details information 

## How to use
1. **Prevent misuse**
+ Problem: we have multiple ids of Organization. it doesnt make sense to represent those below
```rust
    let org_1 = 1111;
    let org_2 = 2222;
```
+ Fix: Wrap new type 
```rust
    struct Identifier(u64);

    let org_1 = Identifier(1111);
    let org_2 = Identifier(2222);
```
-> Unable to add or substract id, `u64` is represented `Identifier` of object

2. **Extend Functionality**
+ Example : Suppose you want to display a credit card number to the user but wish to conceal certain digits.

```rust
use std::fmt;
struct CreditCardNumber(String);

impl fmt::Display for CreditCardNumber {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "({} **** **** {})", &self.0[0..4], &self.0[15..])
    }
}

fn main() {
    let credit = CreditCardNumber(String::from("1111 2222 3333 4444"));
    println!("Credit Card:{}", credit);
    //Credit Card:(1111 **** **** 4444)
}
```