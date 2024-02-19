---
tags:
  - typescript
---
# Type narrowing
- Simplest way to narrow type is wrapping it in conditional or returning early from conditional (preferred). Narrowing can happen via multiple different operators such as simple reference comparison check for type via `typeof` guard, checking for property existence via `in`
```typescript
const len = (value: string | undefined) => {
  if (value === undefined) {
    return 0;
  }

  // Value there is narrowed to string
  return value.length;
}
```
- Custom user-defined type guard
```typescript
type Cat = { isCat: boolean };
type Car = { isCar: boolean };
function isCar = (value: Cat | Car): value is Car {
  if ('isCar' in value) {
    return true;
  }

  return false
}
```

Type narrowing is especially useful when working with unions, as it allows us to narrow to specific union which can have additional data
```typescript
type FieldType = {type: 'numeric', value: number} | {type: 'string', value: string};
```
When we narrow to specific type we can have different value or event additional fields