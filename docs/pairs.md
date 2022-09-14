<!--
 oldlspec (c) by Eray Erdin
 
 oldlspec is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Pairs

Pairs are a type of entry. In OLDL, you can spot them by the colon.

| Input | Output |
| ----- | ------ |
| `foo:bar` | `[P("foo", "bar")]` |

There might be any number of spaces around the colon. It will be a valid pair.

| Input      | Output |
| ---------- | ------ |
| `foo :bar` | `[P("foo", "bar")]` |
| `foo: bar` | `P("foo", "bar")]` |
| `foo : bar` | `P("foo", "bar")]` |

## Keys and Values with Multiple Words

The key and value in a pair might include a space, but then the key or value should be enclosed in single or double quotes.

| Input | Output |
| ----- | ------ |
| `foo:"bar baz"` | `[P("foo", "bar baz")]` |
| `foo:'bar baz'` | `[P("foo", "bar baz")]` |
| `"foo bar":baz` | `[P("foo bar", "baz")]` |
| `'foo bar':baz` | `[P("foo bar", "baz")]` |

!!! warning "Warning (For Developers)"
    While this is an option, this is usually not a good idea. It breaks the readability and makes it harder to comprehend. So, avoid it as much as possible.

## The Type of Key and Value

The type of key and (especially) value should always be string. That is because it is the developer's responsibility to handle the type.

There are many possible types out there. While the primitive ones are integers, floats, booleans or whatnot, the developer might want to have, for example, a valid datetime, or a range for prices. The possibilities are limitless. So, it's better to [KISS](https://en.wikipedia.org/wiki/KISS_principle).

While the implementors should always provide their implementations to always return a string for key and value in a pair, they might want to choose to expand it with extensions. The core, however, should obey this principle.

## Arrays (Especially for Developers)

As mentioned [The Type of Key and Value](pairs.md#the-type-of-key-and-value), there is no other type than string. However, the developer might want to have an array. For example, filtering the movies by multiple genres. Two possible approaches come to mind. Pick your poison.

### Approach 1: One key with comma-separated values

An example is this:

```plain
# input
genres:action,horror

# result
[P("genres", "action,horror")]
```

The developers can use a simple [split method like in Python](https://docs.python.org/3/library/stdtypes.html#str.split) to turn it into a list. It is easier to write.

However, the user might use a comma+space combination, which will break the parser.

### Approach 2: Multiple keys with different values

Below is an example:

```plain
# input
genres:action genres:horror
```

The developers can create a list and push into it each time the same key occurs. Despite its verbosity, it is easier to comprehend.

On the other hand, this requires too many keystores and takes longer to type.