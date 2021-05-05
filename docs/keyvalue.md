<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Key-Value Pairs

The body contains key-value pairs seen as below:

```plain
key1:value1 key2:value2
```

```plain
content: ""
body: {
    "key1": "value1",
    "key2": "value2",
}
```

A pair contains three parts: (i) key, (ii) definer, which is colon character, and (iii) value. The key and definer are required while the value is optional.

```plain
/* valid examples */
key:value
key:

/* invalid examples */
key
:value
```

Each pair should be separated with more than one whitespace characters except, of course, the newline character.

!!! warning
    The examples below will be written in multiple lines for easier understanding. OLDL, hence the name, does not contain more than one line.

```plain
/* valid examples */
key1:value1 key2:value2
key1:value1    key2:value2 /* four space */
key1:value1    key2:value2 /* consider this as a tab */

/* invalid examples */
key1:value1key2:value2
```

## Key Specification

Keys can contain more than one numeric, alphanumeric, dash (`-`) and underscore (`_`) characters. It cannot contain other than these, like whitespaces or string delimiters.

```plain
/* valid examples */
key:value
key1:value
1key:value
1st-key:value
1st_key:value
_key:value
-key:value
key_:value
key-:value

/* invalid examples */
my key: value
"my key":value
```
## Definer Specification

Definer is a single colon (`:`) character. It cannot contain any whitespace around it.

```plain
/* valid example */
key:value

/* invalid examples */
key: value
key :value
key : value
```

## Value Specification

The format of value is defined by its type. See [data types](datatypes.md) section.
