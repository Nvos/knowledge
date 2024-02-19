---
tags:
  - frontend
  - web
  - solidjs
  - best-practices
---
# Do not destructure
While syntax is very similar to `React` common practice of destructuring properties is actually quite problematic. Solid achieves reactivity via proxies and destructuring proxy, results in losing reactivity for destructured prop
# Treat component return as template
Solid doesn't re-render whole component on change instead changes are quite granular where state is used, JSX/TSX is actually used as template not function thus early returns which are quite common in `React` should not be used.

Component not re-rendering as a whole (only once) is actually large benefit - it makes easy to integrate with JavaScript/TypeScript libraries as those can be simply assigned to variable.
# Effect clean-up
Reactivity primitives such as effects can be nested, quite often it is necessary to create something in `createEffect` we can clean up effect on next run via nesting inside of it `onCleanup` 