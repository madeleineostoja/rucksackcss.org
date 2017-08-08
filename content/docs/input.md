---
title: "Input Pseudo-Elements"
anchor: "input"
weight: 5
---
Rucksack adds new pseudo-elements that allow you to easily style the inner elements of HTML5 inputs across browsers. Currently the only element supported is the range input (and `::placeholder` if you enable automatic vendor prefixing), more will be added as browser vendors open up their APIs.

Note that the rules in the output generated (see below) are duplicated, since if a browser finds a single selector it doesn't understand in a group the whole group is ignored (see [Selectors Level 3](http://www.w3.org/TR/selectors/#Conformance)).

## Range Elements
Style the notoriously tricky range input with `::track` and `::thumb`. Track targets the 'line', while thumb targets the 'button'. They can be applied to any range element, or at the root of your stylesheet for global styling.

Input
```css
input[type="range"]::track {
  background: #9d9d9d;
  height: 3px;
}

input[type="range"]::thumb {
  background: #4286be;
  width: 16px;
  height: 8px;
}
```
Output
```css
input[type="range"]::-webkit-slider-runnable-track {
  -webkit-appearance: none;
  background: #9d9d9d;
  height: 3px;
}

input[type="range"]::-moz-range-track  {
  -moz-appearance: none;
  background: #9d9d9d;
  height: 3px;
}

input[type="range"]::-ms-track  {
  background: #9d9d9d;
  height: 3px;
}

input[type="range"]::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: #4286be;
  width: 16px;
  height: 8px;
}

input[type="range"]::-moz-range-thumb {
  -moz-appearance: none;
  background: #4286be;
  width: 16px;
  height: 8px;
}

input[type="range"]::-ms-thumb {
  background: #4286be;
  width: 16px;
  height: 8px;
}
input[type="range"] {
  -webkit-appearance: none;
}
input[type=range]::-moz-focus-outer {
  border: 0;
}
```

The `-webkit-appearance: none;` and `-moz-appearance: none;` declarations are added to relevant elements so that your custom styles are properly applied. Note that this means that for webkit (Chrome, etc) you must style _both_ `::track` and `::thumb`, since the appearance must be set on the root element.

The additional `::-moz-focus-outer` rule simply removes the dotted outline around the element on some versions of firefox.
