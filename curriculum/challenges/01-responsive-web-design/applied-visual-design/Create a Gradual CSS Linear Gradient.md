---
id: 587d78a5367417b2b2512ad6
title: Create a Gradual CSS Linear Gradient
challengeType: 0
videoUrl: 'https://scrimba.com/c/cg4dpt9'
---

## Description
<section id='description'>
Applying a color on HTML elements is not limited to one flat hue. CSS provides the ability to use color transitions, otherwise known as gradients, on elements. This is accessed through the <code>background</code> property's <code>linear-gradient()</code> function. Here is the general syntax:
<code>background: linear-gradient(gradient_direction, color 1, color 2, color 3, ...);</code>
The first argument specifies the direction from which color transition starts - it can be stated as a degree, where 90deg makes a vertical gradient and 45deg is angled like a backslash. The following arguments specify the order of colors used in the gradient.
Example:
<code>background: linear-gradient(90deg, red, yellow, rgb(204, 204, 255));</code>
</section>

## Instructions
<section id='instructions'>
Use a <code>linear-gradient()</code> for the <code>div</code> element's <code>background</code>, and set it from a direction of 35 degrees to change the color from <code>#CCFFFF</code> to <code>#FFCCCC</code>.
<strong>Note</strong><br>While there are other ways to specify a color value, like <code>rgb()</code> or <code>hsl()</code>, use hex values for this challenge.
</section>

## Tests
<section id='tests'>

```yml
- text: The <code>div</code> element should have a <code>linear-gradient</code> <code>background</code> with the specified direction and colors.
  testString: 'assert(code.match(/background:\s*?linear-gradient\(35deg,\s*?(#CCFFFF|#CFF),\s*?(#FFCCCC|#FCC)\);/gi), "The <code>div</code> element should have a <code>linear-gradient</code> <code>background</code> with the specified direction and colors.");'

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='html-seed'>

```html
<style>

  div{
    border-radius: 20px;
    width: 70%;
    height: 400px;
    margin: 50px auto;

  }

</style>

<div></div>
```

</div>



</section>

## Solution
<section id='solution'>


```js
var code = "<style> div{border-radius: 20px; width: 70%; height: 400px; margin: 50px auto; background: linear-gradient(35deg, #cff, #fcc);}</style><div></div>"
```

</section>
