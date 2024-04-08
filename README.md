# Source text

Library for storing efficient line offset and column from `std::string::String`. It processes lines only once at the first invokation of any of the retrieval methods.

## Bugs

It looks to be failling when retrieving the end column of the second line of:

```

default xml namespace =

```

It reports 3:28, but should report 2:24.

## Example

Here is a basic example:

```rust
// offset 5 = "bar"
let text = SourceText::new("foo\r\nbar\r\nqux".into());
assert_eq!(0, text.get_column(5));
assert_eq!(2, text.get_line_number(5));
assert_eq!(5, text.get_line_offset(2).unwrap());
assert_eq!(5, text.get_line_offset_from_offset(7));
```