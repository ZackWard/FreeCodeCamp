---
id: 587d7db2367417b2b2512b8b
title: Understand the Immediately Invoked Function Expression (IIFE)
challengeType: 1
---

## Description
<section id='description'>
A common pattern in JavaScript is to execute a function as soon as it is declared:
<blockquote>(function () {<br>&nbsp;&nbsp;console.log("Chirp, chirp!");<br>})(); // this is an anonymous function expression that executes right away<br>// Outputs "Chirp, chirp!" immediately</blockquote>
Note that the function has no name and is not stored in a variable. The two parentheses () at the end of the function expression cause it to be immediately executed or invoked. This pattern is known as an <code>immediately invoked function expression</code> or <code>IIFE</code>.
</section>

## Instructions
<section id='instructions'>
Rewrite the function <code>makeNest</code> and remove its call so instead it's an anonymous <code>immediately invoked function expression</code> (<code>IIFE</code>).
</section>

## Tests
<section id='tests'>

```yml
- text: The function should be anonymous.
  testString: 'assert(/\(\s*?function\s*?\(\s*?\)\s*?{/.test(code), "The function should be anonymous.");'
- text: Your function should have parentheses at the end of the expression to call it immediately.
  testString: 'assert(/}\s*?\)\s*?\(\s*?\)/.test(code), "Your function should have parentheses at the end of the expression to call it immediately.");'

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function makeNest() {
  console.log("A cozy nest is ready");
}

makeNest();
```

</div>



</section>

## Solution
<section id='solution'>


```js
(function () {
  console.log("A cozy nest is ready");
})();
```

</section>
