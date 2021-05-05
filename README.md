<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# OLDL (One Line Data Language)

![Documentation Status](https://img.shields.io/readthedocs/oldl?style=flat-square)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/erayerdin/oldl?style=flat-square)

OLDL is a data language just like JSON, YAML or TOML but the data is represented on one line.

It tries to solve the problem where user can provide the data only on one line such as input field on web browsers.

## Examples

```plain
/* provide keys and values */
topic:linguistics author:"noam chomsky"

/* provide a content for full-text search, before or after */
higurashi type:anime
type:anime higurashi

/* has types */
name:Eray age:27 points:3.7

/* has array */
type:bug type:need-help

/* has null values */
is-created: is-updated:
```

## Specification and Implementations

You can read the specification [here](https://oldl.readthedocs.io). You can view implementations on [Implementations](https://oldl.readthedocs.io/implementations) section.

## License

This specification is licensed under [CC BY-SA 4.0](LICENSE).
