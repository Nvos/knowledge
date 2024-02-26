---
tags:
  - go
  - backend
---
Ensure type satisfies interface via compile time check
```go
type Todo struct {}
type TodoInterface interface {
  SomeFunction()
}
var _ TodoInterface = (*Todo)(nil)
```
By creating `_` variable of interface type, nil pointer to struct which is supposed to implement interface passed. In case when it is not passed there will be compile time error. Additionally most tools will allow easy code generation for interface implementation