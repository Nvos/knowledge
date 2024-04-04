---
tags:
  - css
  - frontend
  - flexbox
---

# Fill height overflow child container

Min width and height have default of `0` but in flex context it is `auto`, which can result in those elements taking more space than desired resulting in overflow. Thus in order for child to fill height of parent and overflow it is necessary to set min height or width (depending on direction) to `0`

**Thus required for overflowing child is following css:**

```css
flex: 1;
min-width: 0;
```
