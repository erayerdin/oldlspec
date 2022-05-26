<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Regular Type

Anything that's not a pair is a regular type. Regular type instances can be at the start, end or in the middle of OLDL data.

| Input | Output |
| ----- | ------ |
| lorem ipsum:dolor sit amet:consectetur adipiscing | `[R("lorem"), P("ipsum", "dolor"), R("sit"), P("amet", "consectetur"), R("adipiscing")]` |

Regulars should not be splitted by spaces. They should be grouped. In the example below, "dolor sit" part should not be considered two different regular instances, it should be parsed as one regular instance.

| Input | Output |
| ----- | ------ |
| lorem:ipsum dolor sit amet:consectetur | `[P("lorem", "ipsum"), R("dolor sit"), P("amet", "consectetur")]` |