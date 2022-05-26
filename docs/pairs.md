<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Pairs

Pairs are the definitions of a key and a value separated by a colon (:) sign.

```plain
foo:bar
```

In this example, the key of this pair is `foo` and the value of this pair is `bar`.

**Pairs should not have whitespaces ever.** Below explains it:

| # | Input | Output |
|---|---|---|
| 1.1 | foo bar:baz | `[R("foo"), P("bar", "baz")]` |
| 1.2 | foo:bar baz | `[P("foo", "bar"), R("baz")]` |

This also covers the colon, it should never have whitespace around it:

| # | Input | Output |
|---|---|---|
| 1.3 | foo: bar baz:qux | `[R("foo: bar"), P("baz", "qux")]` |

The pairs also should fill both key and value. If only key or only value is provided, these should be deserialized as regular.

| # | Input | Output |
|---|---|---|
| 2.1 | foo: bar:baz | `[R("foo:"), P("bar", "baz")]` |
| 2.2 | foo:bar :baz | `[P("foo", "bar"), R(":baz")]` |