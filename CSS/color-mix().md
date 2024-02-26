---
tags:
  - css
  - frontend
---
New function responsible for color modifications, main benefit is possibility of adding alpha to any color via just CSS without need for creating/modifying variables thought color mixing is possible as well

```css
div {
  background-color: color-mix(in srgb, #34c9eb 25%, white)
}
```

Breakdown:
- First parameter `in srgb` is resulting colour space
- Second parameter `#34c9eb 25%` is base colour and mix percentage of it
- Finally `white` is colour to which it will blend
# Links
- https://developer.chrome.com/docs/css-ui/css-color-mix?hl=pl