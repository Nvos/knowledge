---
tags:
  - frontend
  - react
  - library
  - web
---

# Forms 
1. [react-hook-form](https://react-hook-form.com) - flexible hook based form library
2. [zod](https://github.com/colinhacks/zod) - type-safe schema validation library
3. [valibot](https://github.com/fabian-hiller/valibot) - modular type-safe schema validation library, looks very promising quite likely can prove to be good zod replacement
# Styling
1. [vanilla-extract](https://vanilla-extract.style/)- type-safe zero runtime (styles generated at build time) framework agnostic css-in-js library
2. [panda-css](https://panda-css.com/)- type-safe (styles generated at build time) framework agnostic css-in-js library. In comparison to vanilla-extract it provides more standardization, additionally it uses code generation for baseline code. Token and theme type safety feels bit worse than vanilla-extract
3. [radix-ui](https://github.com/radix-ui/primitives) - accessible, high quality primitive components (as of 02-09-2024 20:35 it is not actively maintained prefer to use [ark-ui](https://ark-ui.com/) instead)
4. [ark-ui](https://ark-ui.com/)- can be considered successor of radix, benefit is that it supports multiple frameworks and is more feature complete than radix
# Local state
1. [jotai](https://github.com/pmndrs/jotai)- atom based library (focuses on combining and composing multiple atoms), successor to [recoil](https://github.com/facebookexperimental/Recoil) with simplified API
2. [redux-toolkit](https://redux-toolkit.js.org/)- official, opinionated kit for redux
3. [zustand](https://github.com/pmndrs/zustand) - can be thought as successor of redux, simplifies whole ceremony required by redux, seem to be most preferred solution for local state management in community
# Remote state
1. [tanstack-query](https://tanstack.com/query)- framework agnostic library for asynchronous remote state, most convenient usage is with REST or GRPC, it is possible to use with GraphQL but it is less convenient than specific solutions
2. [urql](https://github.com/urql-graphql/urql)- framework agnostic GraphQL client, after using Apollo for quite a while and encountering quite a lot cache bugs urql seem a lot more stable and focuses on library not some SASS offering
3. [relay](https://relay.dev/)- GraphQL client offering a lot of standardization, most convenient to use when backend is build according to its specific requirements such as strictly conforming to connection format and using globally unique ids
4. [trpc](https://trpc.io/)- most convenient way for API when backend is built in node which allows writing server side code and easily extracting types from it to be used on client side
5. [connect-es](https://github.com/connectrpc/connect-es) - convenient client for for gRPC supporting gRPC, gRPC-web and their own [connect](https://connectrpc.com/docs/protocol) protocol
# Routing
1. [react-router](https://reactrouter.com)- default routing library for most projects, API is focused for their framework ([remix](https://remix.run)) needs which might be problematic for future of project
2. [tanstack-router](https://tanstack.com/router/latest)- new modern routing library which might be good and possibly better alternative to react-router, main benefit is full type-safety for whole routing which includes links, route/query parameters and much more
# SSR
- [Nextjs](https://nextjs.org/)- full framework, currently needs for this project drive React features. Pretty much default solution for projects requiring SSR
- [Astro](https://astro.build/) - framework agnostic solution offering SSR and other output types