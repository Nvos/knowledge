# Pick
Creates new type using only provided keys
```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}
 
type TodoPreview = Pick<Todo, "title" | "completed">;
```
`TodoPreview` wont have `description` field
**Opposite of `Pick` is`Omit`**
# Partial
Transforms type into new one where all properties are optional
```typescript
interface Todo {
  title: string;
  description: string;
  completed: boolean;
}

type TodoPreview = Partial<Todo>;
```
`TodoPreview` will have all properties as `value | undefined`