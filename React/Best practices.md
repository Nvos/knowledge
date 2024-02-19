---
tags:
  - frontend
  - react
  - web
  - best-practices
---
# Reusability
Strictly enforcing reusability without deeper understanding most of time is bad idea, preferably wait for at least few cases where something can be re-used before extracting it as separate component/function. 

If we extract it before further consideration and know what it is supposed to do it will end up with a lot of flags and conditionals inside to handle all those cases which in time becomes nightmare to maintain. Thus most of times it is actually good idea to **copy** something instead of extracting it as reusable component

Good case for this which quite often happens are modals initially create and edit modal for some object will be nearly same so with only slight changes we can handle both of those in single component but in time as there are more and more requirements differences will grow making it reasonable to have 2 separate components instead of maintaining single one with multiple conditionals
# Derive
Quite often we need to combine multiple sources of data into single one or modify value, beginners most of time reach for state + effect which requires keeping state in sync. While it will work it is not ideal as it introduces quite a bit more complexity than necessary and triggers additional re-render

Best solution for such case is just pure function which takes multiple sources and combines them, depending on calculation complexity wrapping it in `useMemo` can be worth considering
# Props drilling
Quite often we need to pass data from parent to deeply nested child, drilling this prop through all children in subtree can be quite annoying. Thus quite often it is preferable to use one of following solutions:
* Component composition and children props is likely cleanest way to handle it, thought it is not always applicable
* Context allows whole sub tree to access data, it is preferable way for **dependency** injection or **rarely** changed values
* State management libraries are most convenient way to handle it but can be problematic due to it being global state, this means that it is not bound to some component which introduces some special cases such as needing to destroy/resetting it manually
# Early return
Always prefer to early return given some conditional instead of constructing complex conditionals, quite often this will result in additional components but will result in much easy to reason about code
# Avoid bool flags
Quite often components are configurable, most common way to implement such thing is simple bool flag which does not scale very well. It is nearly always better idea to instead to consolidate those flags into respective single state represented by enum or union of string constants. Good example of it would be type of button while w could provide it via multiple booleans e.g. `isPrimary` and `isSecondary` it would result in inconsistency as we can provide those 2 flags at same time. It would be preferable to instead pass them as `"primary" | "secondary"`  via single property

Boolean flags can still be used but it should be done with care, if we know that some state will only be enabled and wont have different states then it is reasonable for it to be bool but such thing is actually quite rare
# Immutability
React by default makes all comparisons via references thus data should always be copied which can be quite annoying for more complex cases with nested data, thankfully there are libraries such as [immer](https://github.com/immerjs/immer) which allows for creation of next immutable state via mutation.
# Project structure
* Keep it as flat as possible ideally, max 2 directories deep
* Collocate relevant code as close as possible to usage