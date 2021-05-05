<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# General Structure

!!! tip
    The results are presented in a way that is similiar to Python for easier understanding. `""` is string, `{}` is dict and `[]` is array.

OLDL mainly consists of two main parts: (i) content and (ii) body.

```plain
cute category:cats
```

In this case, this expression results in:

```plain
content: "cute"
body: {"category": "cats"}
```

Both content and body are optional. So, empty input would result in:

```plain
content: ""
body: {}
```
