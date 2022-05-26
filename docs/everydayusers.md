<!--
 oldlspec (c) by Eray Erdin
 
 oldlspec is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# An Introduction for Everyday Users

A plain text is a valid text in OLDL. So:

```plain
this is valid
```

This example is a valid OLDL.

You use OLDL when you want to send some extra data to an app, like filtering or sorting the results.

Imagine you are doing online shopping. You look for a phone to buy. So, naturally, you type this to the search bar:

```plain
phone
```

However, you see some iPhones on the list and there's too many of them. You think "I want to see only Android phones.". Then, you can do something like:

```plain
phone os:android
```

This time, you see some expensive ones among the cheap ones. You want to see the lowest price first. So, you can do this:

```plain
phone os:android sort:+price
```

However, you also want to have a phone with either 4-core or 6-core CPU. Then, you can do this:

```plain
phone os:android sort:+price cores:4 cores:6
```

Congratulations, this is all you need to know about OLDL, it is simple as that.

!!! warning
    The examples here are arbitrary. An online shopping app might use different names for parameters, for example, `core-count:4` instead of `cores:4`. These should be evident to the user (you) by the developer.