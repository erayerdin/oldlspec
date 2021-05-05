<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Content

Content is the part of OLDL data where a user can provide some keywords or a whole sentence for developers to filter some content. An example is:

```plain
two guys fight each other type:action type:movie
```

In this case, the content is "two guys fight each other".

## The Format of Content

The content can be presented without any string delimiters.

```plain
wireless adapter type:"used"
```

Any characters can be used in content except, as you might have probably guessed, [the definer](keyvalue.md#definer-specification) in key-value pairs. In that case, string delimiters should be used for content.

```plain
"higurashi no naku koro ni: onikakushi" type:visual-novel
```

## The Order of Content

The content can precede or succeed the body. The examples below have the same effect.

```plain
higurashi no naku koro ni type:visual-novel
type:visual-novel higurashi no naku koro ni
```
