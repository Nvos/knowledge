# Slice
- Pointer by default
- Nil slice doesn't require allocation but is still zero length and zero capability
- It is good idea when using stored slice to pass copy instead in order to avoid potential mutations to main one
- Appending to array slice can have unexpected consequences when slice grows due to lack of space
- Arrays with non pointer values are comparable
# Struct
- Non pointer structs are comparable
# Map
- Can easily leak memory, as deleting elements doesn't shrink backing array
- Pointer by default
- It is good idea when using stored map to pass copy instead in order to avoid potential mutations to main one