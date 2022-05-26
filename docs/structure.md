<!--
 oldlspec (c) by Eray Erdin
 
 oldlspec is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# General Structure

A deserialized OLDL data should return an array of entries. There are two kinds of entries:

 - **Pair** entries, which we will refer to as `P`s while giving some examples.
 - **Text** entries, which we will refer to as `T`s while giving some examples.

Check out the example below:

| Input | Output |
| ----- | ------ |
| `foo bar:baz` | `[T("foo"), P("bar", "baz")]` |

In this example, the user provides `foo bar:baz` as input, which should result as one `T` with `foo` and one `P` with `bar` and `baz` as its values.

## Frequently Asked Questions

### As an implementor, how do I define an array with two types?

In highly object-oriented languages, you can create a base abstract class or interface named `Entry` and extend or implement it with two concrete classes: `Pair` and `Text`. Check out a Dart example below:

```dart
abstract class Entry {
  String get value;
}

class Pair extends Entry {
  final String key;
  final String value;

  Pair(this.key, this.value);
}

class Text extends Entry {
  final String value;

  Text(this.value);
}

// somewhere in code

// the result of: `foo bar:baz`
final List<Entry> entries = [
    Text('foo'),
    Pair('bar', 'baz'),
];
```

If the language you are implementing OLDL has enums with values, you can check out this example in Rust:

```rust
enum Entry {
    Text(String),
    Pair(String, String),
}

// somewhere in code

// the result of: `foo bar:baz`
let entries = vec![
    Entry::Text("foo".to_string()),
    Entry::Pair("bar".to_string(), "baz".to_string()),
];
```