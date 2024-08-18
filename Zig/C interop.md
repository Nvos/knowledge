---
tags:
  - zig
---

# Single file
Just import it via `@cImport` and `@cInclude` then it just works, types and everything via ZLS
```c
const c = @cImport({
  @cInclude("unistd.h");
});
```
## Raylib
1. Add `raylib` to dependencies in `build.zig.zon` easiest way to handle this is to just use `zig fetch --save {url to archive}` . Calling fetch will add it to `build.zig.zon` dependencies section.
	1. Example URL from commit - https://github.com/raysan5/raylib/archive/b432aa2b9cd5eb35391636b6e147db8d9a9cf1cc.zip
2. Add `dependency` in `build.zig`
```c
const raylib_dep = b.dependency("raylib", .{
	.target = target,
	.optimize = optimize,
});
```
3. Link library in `build.zig`
```c
exe.linkLibrary(raylib_dep.artifact("raylib"));
```
4. Add `raylib` import
```c
const r = @cImport(@cInclude("raylib.h"));
```
5. It just works, types and everything via ZLS