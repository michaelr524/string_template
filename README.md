# string_template
Very simple string template for Rust

### Usage

Add this to your `Cargo.toml`:

```toml
[dependencies]
string_template = "0.1.0"
```

and this to your crate root:

```rust
extern crate string_template;
```

Here's a simple example:

```rust
extern crate string_template;

use string_template::Template;

fn main() {
        let template = Template::new("Hi, my name is {{name}} and I'm a {{lang}} developer.");
            
        let mut args = HashMap::new();
        args.insert("name", "Michael");
        args.insert("lang", "Rust");
        let s = template.render(&args);

        assert_eq!(s, "Hi, my name is Michael and I'm a Rust developer.");

        let mut args1 = HashMap::new();
        args1.insert("name", "Vader");
        args1.insert("lang", "Dart");
        let s2 = template.render(&args1);

        assert_eq!(s2, "Hi, my name is Vader and I'm a Dart developer.");
}
```
