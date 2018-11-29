# string_template
Very simple string template for Rust.
Can render named parameters from a HashMap or positional parameters from a slice.

### Usage

Add this to your `Cargo.toml`:

```toml
[dependencies]
string_template = "0.2.1"
```

If you're on Rust 2015, and this to your crate root:

```rust
extern crate string_template;
```

Here's a simple example:

```rust
extern crate string_template;                                                             
                                                                                          
use string_template::Template;                                                            
use std::collections::HashMap;                                                            
                                                                                          
fn main() {                                                                               
    let template = Template::new("Hi, my name is {{name}} and I'm a {{lang}} developer.");
    let mut args = HashMap::new();                                                        
    args.insert("name", "Vader");                                                         
    args.insert("lang", "Dart");                                                          
    let s = template.render(&args);                                                       
                                                                                          
    assert_eq!(s, "Hi, my name is Vader and I'm a Dart developer.");                      
                                                                                          
    let template2 = Template::new("Hi, my name is {{}} and I'm a {{}} developer.");       
    let args2 = vec!["Vader", "Dart"];                                                    
    let s2 = template2.render_positional(&args2);                                         
                                                                                          
    assert_eq!(s2, "Hi, my name is Vader and I'm a Dart developer.");                     
}                                                                                         
```
