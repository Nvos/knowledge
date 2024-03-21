# Stack
- Everything for which go can determine lifetime during compile time will be allocated on stack, examples of those are local non pointer variables and global constants. This memory will not be managed by garbage collector and instead be tied to lexical scope.
- Everything for which compiler cannot determine lifetime **escapes to the heap**
- [Eliminating heap allocations](https://tip.golang.org/doc/gc-guide#Eliminating_heap_allocations)
# Optimizing allocations
- Always when slice length is know or can be calculated prefer to create it via built in function `make`  and pass known size as third parameter `capacity`, this will reduce number of allocations thus improving performance. When slice is created without providing initial capacity it will grow automatically when needed
- Avoiding allocations via mutating in-place instead of creating new one, e.g. sorting or filtering slices
- When it is necessary to create array of pointers with known size it might be worthwhile to allocate non pointer array of specific type instead of allocating for each one in loop
# Map
- Maintains a backing array to store map entries, this means that along with entries put into map, this backing array might be too small thus will need to grow
- Backing array will never shrink which means that even if all values are cleared it will still use more memory
	- In order to release map it is necessary to set it to nil,  create new one or use built-in function `clear`
- If number of elements in map is known or upper bound could be predicted it is preferable use `make` and pass size argument in order to avoid growing map