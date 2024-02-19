---
tags:
  - frontend
  - react
  - web
  - optimization
---

# Re-render
Any of following actions will trigger re-render
1. Initial component render
2. Component state change
When trigger happens then while component sub-tree will render as well, which can result in poor performance for frequent changes, thus such components which frequently update might require special care
# Memoization
1. `useMemo` - allows to memoize value depending on specific dependencies, value will re-calculate only when dependencies change (by default verification happens using reference comparison). It is worth noting that value can be JSX thus making it possible to refresh part of component only when dependencies change, thought in the end it is preferable to use it mostly for values
2. `memo` - allows to memoize component, it is very useful for bailing out of renders when props didn't change. Good usage example would be some component containing large sub-tree which we do not want to re-render frequently as props rarely change but parent component changes frequently thus we can wrap this child component in memo in order to prevent frequent renders.
# Debounce / Throttle
Quite often we want to trigger some action when during user interactions such as scrolling/typing etc. but given that any state change triggers re-render it is somewhat problematic as it would result in triggering actions on each key-press such actions could for example be fetching data. In order to prevent it we can debounce or throttle depending on needs
- `debounce` - delays execution of function until user stops performing action for specific time - most common usage of it would be debouncing typed text, resulting in execution of action only after user stops typing for a while
- `throttle` - limits execution of function to once in interval - most common usage would be scroll or resize, preventing too frequent updates which could result in laggy UI during such operations
# Splitting components
Splitting larger component into smaller ones can improve performance, for example large component with a lot of state will re-render all children no matter what on any state change but if we split it into smaller components and nest related state inside of them then those changes wont affect other components due to state change resulting in re-render of component sub tree

Additional thing to note is that `children` property represents isolated VDOM which means that it cannot be re-rendered by parent which allows for quite a lot of optimization possibilities  
# Devtools
* Re-render visualization toggle allows for easy way to see at runtime when re-renders happen in app
* Profiling allows to create re-render flame chart  showing render times, components and reason why it happened (doesn't work well for hooks)
# Why did you render
[why-did-you-render](https://github.com/welldone-software/why-did-you-render) - very useful library which patches react in order to track reason for re-render, works very well even with hooks and provides very good description of re-render reason
# Code splitting
Initial download size and render time can degrade along with application size, this can be prevented/reduced via splitting application into smaller parts which can be loaded lazily. Most common part which is code split are views which we can lazy load when needed - e.g. when navigation to such view happens. Those views could have other lazy loaded dependencies.

It is worth noting that there are possible optimizations for applications which use code splitting, such as prefetching code before usage after application becomes interactive and is idle. Some frameworks even prefetch on link hover