<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# General Structure

A deserialized OLDL data should be an array. There are two types of elements that this array should contain: regular (R) and pair (P).

Below are some examples about the input and output.

| # | Input | Output |
|---|---|---|
| 1.1 | phone | `[R("phone")]` |
| 1.2 | phone os:android | `[R("phone"), P("os", "android")]` |
| 1.3 | phone os:android headphones sort:+price | `[R("phone"), P("os", "android"), R("headphones"), P("sort", "+price")]` |
| 1.4 | phone os:android cores:4 cores:6 | `[R("phone") P("os", "android"), P("cores", "4"), P("cores", "6")]` |

From these examples, you may have noticed a couple of things:

 - **As you can see in the sample 1.3**, a content in the middle (headphones) is considered to be a regular type. Thus, a key and a value must not have whitespaces.
 - **As you can see in the sample 1.4**, and the others as well, there's only string type even if the content provided is a valid integer.
