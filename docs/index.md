<!--
 oldl (c) by Eray Erdin
 
 oldl is licensed under a
 Creative Commons Attribution-ShareAlike 4.0 International License.
 
 You should have received a copy of the license along with this
 work. If not, see <http://creativecommons.org/licenses/by-sa/4.0/>.
-->

# OLDL

OLDL (One-Line Data Language) is a data language just like JSON, YAML and TOML. However, hence the name, the data is represented on only one line.

## Why?

Github's issues section has issue filtering field, which defaults to `is:issue is:open`. This filters only the issues and only open ones at that.

Google also uses some filters on its search engine. You can use `site:foo.com` on your search to filter only pages from `foo.com`.

In both examples, some keywords are accompanied by these filters as well.

To solve the same problem, some websites rely on "detailed search" section with multiple form fields. Some other websites rely on Javascript-based solution, providing *pill-like* components in an input field. While this presents (maybe) a good UI/UX solution, it is simply too much work to implement and is prone to bugs at times.

OLDL tries to solve this problem by providing a standard.

## Objectives

 - **The data should be human-readable**. A person should recognize and congnitively-parse what the data represents easily.
 - **The data should be *human-writable***. As well as human-readability, the standard should be set in a way that a user can provide this data. In desktop, (i) it should require as less key combinations[^1] as possible and (ii) these key combinations should be physically close[^2] to each other. In mobile, it should have (i) as less long-press[^3] as possible and (ii) page-switch[^4] should be avoided.
 - **Users should be able to provide content along with data**. In some cases, key-value pairs do not make sense by themselves or they are simply not enough. So, users should be able to provide a content containing keywords to narrow the results down further.
 - **The data should be friendly for any user**. OLDL does not only target developers as users, but everyday users as well. The data should be presented in a way that any user make sense out of it or write it.
 - **The data should be flat as much as possible**. Since the data should be *human-writable* and *human-readable*, a second dimension in data would require complex representations, which is very hard to read and write. That's why it's better to keep it in one dimension as much as possible. We say "as much as possible" because users also should be able to present some kind of array to, for instance, filter different targets in the same domain. See [Array](datatypes.md#array) for details.

## Documentation License

[![CC BY-SA 4.0](https://mirrors.creativecommons.org/presskit/buttons/88x31/svg/by-sa.svg)](https://creativecommons.org/licenses/by-sa/4.0/)

This document is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

[^1]: It is meant that the case where user needs to press multiple keys at once to provide a character, usually these combinations start with `SHIFT`, `CTRL`, `ALT` etc.

[^2]: In order to provide colon sign (`:`), user should press `SHIFT+.`, which is physically very close to each other.

[^3]: It is meant that user needs to press and hold a key in mobile virtual keyboards. It slows down data providing process and might get user annoyed.

[^4]: It is meant that user needs to switch the page on the mobile keyboard to find a specific character. It is annoying to switch the page and try to find a character, so it should be avoided if possible.
