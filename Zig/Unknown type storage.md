---
tags:
  - zig
---
Zig doesn't have `any` type, making generic storage problematic. Though there are few ways this can be handled:

## Storing pointer as raw bytes or integer

```c
const Position = struct {
    x: i32,
};
...
var pos = Position{ .x = 1 };
// Using @intFromPtr and @ptrFromInt to cast it back to pointer
const value_ptr = @intFromPtr(&pos);
const value_reverse = @as(*Position, @ptrFromInt(value_ptr));

// Using asBytes and casting it back to pointer via @ptrCast
const mem_value_ptr = std.mem.asBytes(&pos);
const mem_value_reverse: *Position = @alignCast(@ptrCast(mem_value_ptr.ptr));
```
It is worth noting that  `pos` variable cannot be `const` in this case and reference to it should be taken when passing it

## Using `*anyopaque`
`*anyopaque` can be used for type erasure, allowing for creation of type erased struct, which later on can be cast back.
```c
pub const Erased = struct {
    ptr: *anyopaque,

    pub fn cast(ptr: *anyopaque) *Impl {
        return @ptrCast(@alignCast(ptr));
    }
};

pub fn new(allocator: std.mem.Allocator) !ErasedComponentStorage {
    const new_ptr = try allocator.create(Impl);
    new_ptr.* = Impl{};

    return Erased{
        .ptr = new_ptr,
    };
}
```
## Union
If all types are known beforehand and it is not library, storing multiple structures as union can be considered. Though it wont be memory efficient as it will use memory from largest type inside of union for all other types (there's additional memory usage for tag).
```c
const Result = union {
    int: i64,
    float: f64,
    bool: bool,
};
```
In case of this example, even if `Result` stores `bool` memory used will be according to largest type, so in this case `f64`