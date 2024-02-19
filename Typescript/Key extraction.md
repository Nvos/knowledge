---
tags:
  - typescript
---

Extracting all keys recursively from provided type
```typescript
type RecursiveKeyOf<T> = T extends object ? (
	T extends readonly any[] ? RecursiveKeyOf<T[number]>: (
		keyof T | RecursiveKeyOf<T[keyof T]>
	)
) : never
```
- Array in typescript typing's is considered `object` as well but with index being `number` type
- When `T` is array we can use number to index it like so `T[number]`
- `T[keyof T]` returns type representing union of objects, more details at https://www.typescriptlang.org/docs/handbook/2/indexed-access-types.html