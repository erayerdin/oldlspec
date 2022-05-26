<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Data Types

As already defined in [General Structure](structure.md), OLDL data should be deserialized into an array of two types. Those are:

 - *Regular (R)*: This is just a string that a user has provided.
 - *Pair (P)*: This is the key value pairs.

| # | Input | Output |
|---|---|---|
| 1.1 | foo bar:baz | `[R("foo"), P("bar", "baz")]` |

The terminal attrubutes of these data types are always string. There's no other type than string in OLDL. This is because it is the developer's job to handle the expected data type to cover the cases.

## Frequently Asked Questions

### As a developer, how do we define an array?

Since there's only string type in OLDL, one might need this requirement to have a sort of array and wonder why it does not exist.

That's because it requires a lot of keypresses and that defies the [objective][objective] "The data should be human-writable.".

If you need an array so bad, two approaches below are convenient to achieve that:

| | Example Input | Advantages | Disadvantages | Approach |
|---|---|---|---|---|
| Comma-separated values | `foo:bar,baz,qux` | Easier to write for users | Users might provide comma+space, which would cause headaches. | Simply split the value by comma.
| Multiple keys | `foo:bar foo:baz foo:qux` | Clear. | Harder to write for users | Put the each value of `foo` key into an array. |

### As an implementor, do I need to implement array to make it convenient for developers to handle multiple values?

The common approaches along with their pros and cons are discussed in [this question](datatypes.md#how-do-we-define-an-array). Since there are multiple possible approaches, it is the best bet to not implement it in your library.

### As an implementor, in the target language, how do I define an array with two different types R and P?

In highly object oriented languages, you can create an interface or abstract class named `Type` and implement it with two concrete classes named `Regular` and `Pair`. With this method, you can define an array with two types, using the parent interface. An example using Dart is:

```dart
// A super-class.
abstract class Type {
    // ...
}

// A concrete class that extends `Type`.
class RegularType extends Type {
    // ...
}

// A concrete class that extends `Type`.
class PairType extends Type {
    // ...
}

// ... later in code ...

final List<Type> output  [Regular(), Pair()];
```

If the target language has value-based enums as in Rust, you can simply use them. A Rust example would be:

```rust
enum Type {
    Regular(String),
    Pair(String, String),
}
```

[faq]: datatypes.md#frequently-asked-questions
[objectives]: index.md#objectives
