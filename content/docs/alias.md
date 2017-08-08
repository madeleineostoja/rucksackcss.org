---
title: "Property Aliases"
anchor: "alias"
weight: 9
---
Rucksack allows you to set aliases for long property names and save some of those precious keystrokes. To set an alias simply add it to the `@alias` rule in the format of `[alias]: [property];`. Aliases are global in a stylesheet, so it's a good idea to have just a single `@alias` rule in your project and specify all aliases in one place.

## Input
```css
@alias {
  fs: font-size;
  fw: font-weight;
}

.foo {
  fs: 16px;
  fw: bold;
}
```

## Output
```css
.foo {
  font-size: 16px;
  font-weight: bold
}
```

**Note:** Using aliases inside propety values is not supported

```css
@alias {
  op: opacity;
}

.foo {
  /* Not supported! */
  transition: op 300ms ease;
}
```
