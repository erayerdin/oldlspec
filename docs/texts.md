<!--
 oldlspec (c) by Eray Erdin
 
 oldlspec is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Texts

Texts are a type of entry that is not a valid pair. The main goal is for user to provide some keywords. Examples below contain texts:

| Input | Output | Description |
| ----- | ------ | ----------- |
| `foo` | `[T("foo")]` | Simple text |
| `foo bar` | `[T("foo bar")]` | Text with space |
| `foo bar:baz` | `[T("foo"), P("bar", "baz")]` | Text and pair |
| `foo:bar baz` | `[P("foo", "bar"), T("baz")]` | Pair and text |
| `foo bar:baz qux` | `[T("foo"), P("bar", "baz"), T("qux")]` | Surrounding text |
| `foo:bar baz qux:quux` | `[P("foo", "bar"), T("baz"), P("qux", "quux")]` | Text in the middle |
| `foo:bar baz qux quux:corge` | `[P("foo", "bar"), T("baz qux"), P("quux", "corge")]` | Text in the middle with space |

As you can see, text can be located anywhere, whether it is the start, the end, or in the middle or many of them at the same time.