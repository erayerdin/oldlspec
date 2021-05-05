<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# Data Types

The body has pairs and pairs are formed of key, definer and value. The format of key and definer is already defined in [Key-Value Pairs](keyvalue.md) section. The format of value is dependent on the type it has.

## String

A string can be defined with or without any string delimiter if it has no whitespace characters, the valid string delimiters are single (`'`) and double quotation marks (`"`). These quotation marks should surround the value if present.

```plain
key1=value1 key2='value2' key3="value3"
```

If the string contains any whitespace, string delimiters are required.

```plain
/* invalid */
name:Ruslan Hasanov

/* valid */
name:"Ruslan Hasanov"
name:'Ruslan Hasanov'
```

## Number

The integers are floats can be defined as follows:

```plain
age:27
points:3.25
points:3,25

/* these will resolve as string, be careful */
age:"27"
points:'3.25'
points:'3,25'
```

If you are curious as to why there is only *number* type instead of separate integer and float type and why we can define float with comma, see [Frequently Asked Questions][faq] section.

## Array

In OLDL, the keys are not bound to be unique. You can define them multiple times and that's exactly how we can define arrays.

```plain
is:open is:bug
```

The result is:

```plain
content: ""
body: {
    "is": ["open", "bug"]
}
```

If you think defining the same key multiple times to form an array is counterintuitive, think that some other way (like separating with comma) should be the method or this requires a lot of keypresses, which is a no-go for mobile, see [Frequently Asked Questions][faq].

## Null

In [Key-Value Pairs](keyvalue.md) section, we have said *values are optional*. So user can provide only key and definer to provide a null value.

```plain
is-open: is-issue:
```

The result is:

```
content: ""
body: {
    "is-open": null,
    "is-issue": null,
}
```

If you think why we should need a null type in the first place, you can refer to related [Frequently Asked Questions][faq] section.

## Frequently Asked Questions

### Why does the specification not define separate integer and float type?

As we discussed in [Objectives][objectives], *the data should be friendly for any user*. A developer can make sense of integer and float distinction but everyday user might not be aware of that.

This distinction can be made in implementation in a language anyway so it is left to implementation developers to deserialize the number type into float or integer in their programming languages.

### Why can we define float with comma?

As we discussed in [Objectives][objectives], *the data should be friendly for any user*. In some locales, the default for decimal separator is comma or an everyday user got accustomed to using comma instead of dot.

### Why do we provide multiple keys to define an array?

At first, it might be counterintuitive to define arrays with defining keys multiple times because it requires a lot of keypresses and that defies the [objective][objective] "The data should be human-writable.".

A better approach you might come up with is to separate the values with commas or something similiar like `key:value1,value2` which would result in `{"key":["value1", "value2"]}`.

In current version of OLDL, the data above will result in `{"key": "value1,value2"}`, which is actually a string. The proposed approach would conflict with String type, which is not desired in this case.

An implementation user can come up with a parsing solution anyway. They can parse `value1,value2` with [a simple split method like in Python](https://docs.python.org/3/library/stdtypes.html#str.split) to turn it into an array if this is the behavior they'd like.

### Why is there no boolean type?

A boolean type would, again, conflict with a string type without delimiters. Also, four or five keypresses would be too much if the data contained more than one boolean type. The thing is, the same behavior can be achieved by not checking the values, but validating the existence of a key in the body.

For example, instead of defining `bug=true`, an implementation user might check `is-bug` key in body. In case of presence, the developer would implement the `true` behavior.

### Why is there a null type?

As discussed in [Why is there no boolean type?](datatypes.md#why-is-there-no-boolean-type), in some cases, what's important for a developer could be to check whether a specific key exists, like `is-bug`. In that case, user would only provide `is-bug:` as an input, which is `null`, but what's important is not the value of `is-bug`, it is whether it exists or not.

### Why is there no X-type?

This question can mean anything. However, as mentioned in the [objectives][objectives], "the data should be friendly for any user".

For example, you might think some kind of datetime data type should exist in OLDL [just like TOML](https://toml.io/en/v1.0.0#offset-date-time). However, datetime itself has its formats like [RFC 3339](https://tools.ietf.org/html/rfc3339), which is cumbersome to write for user.

Or you might think some human-readable names could be present such as "now", "yesterday" or "5 days ago" or "tomorrow" even, but that only complicates things for implementation developers. On the other hand, this can be, again, post-processed implementation user.

We think the types we have at hand now are just enough for implementation developers, implementation users and end users.

[faq]: datatypes.md#frequently-asked-questions
[objectives]: index.md#objectives
