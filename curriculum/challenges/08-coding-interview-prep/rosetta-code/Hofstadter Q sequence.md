---
title: Hofstadter Q sequence
id: 59637c4d89f6786115efd814
challengeType: 5
---

## Description
<section id='description'>
<p>The <a href="https://en.wikipedia.org/wiki/Hofstadter_sequence#Hofstadter_Q_sequence" title="wp: Hofstadter_sequence#Hofstadter_Q_sequence">Hofstadter Q sequence</a> is defined as:</p>
<p>$Q(1)=Q(2)=1, \\ Q(n)=Q\big(n-Q(n-1)\big)+Q\big(n-Q(n-2)), \quad n>2.$</p>
<p>It is defined like the <a href="http://rosettacode.org/wiki/Fibonacci sequence" title="Fibonacci sequence">Fibonacci sequence</a>, but whereas the next term in the Fibonacci sequence is the sum of the previous two terms, in the Q sequence the previous two terms tell you how far to go back in the Q sequence to find the two numbers to sum to make the next term of the sequence.</p>
Task:
Implement the Hofstadter Q Sequence equation into JavaScript
</section>

## Instructions
<section id='instructions'>

</section>

## Tests
<section id='tests'>

```yml
- text: <code>hofstadterQ</code> is a function.
  testString: 'assert(typeof hofstadterQ === "function", "<code>hofstadterQ</code> is a function.");'
- text: <code>hofstadterQ()</code> should return <code>integer</code>
  testString: 'assert(Number.isInteger(hofstadterQ(1000)), "<code>hofstadterQ()</code> should return <code>integer</code>");'
- text: <code>hofstadterQ(1000)</code> should return <code>502</code>
  testString: 'assert.equal(hofstadterQ(testCase[0]), res[0], "<code>hofstadterQ(1000)</code> should return <code>502</code>");'
- text: <code>hofstadterQ(1500)</code> should return <code>755</code>
  testString: 'assert.equal(hofstadterQ(testCase[1]), res[1], "<code>hofstadterQ(1500)</code> should return <code>755</code>");'
- text: <code>hofstadterQ(2000)</code> should return <code>1005</code>
  testString: 'assert.equal(hofstadterQ(testCase[2]), res[2], "<code>hofstadterQ(2000)</code> should return <code>1005</code>");'
- text: <code>hofstadterQ(2500)</code> should return <code>1261</code>
  testString: 'assert.equal(hofstadterQ(testCase[3]), res[3], "<code>hofstadterQ(2500)</code> should return <code>1261</code>");'

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='js-seed'>

```js
function hofstadterQ (n) {
  // Good luck!
  return n;
}
```

</div>


### After Test
<div id='js-teardown'>

```js
console.info('after the test');
```

</div>

</section>

## Solution
<section id='solution'>


```js
function hofstadterQ (n) {
  const memo = [1, 1, 1];
  const Q = function (i) {
    let result = memo[i];
    if (typeof result !== 'number') {
      result = Q(i - Q(i - 1)) + Q(i - Q(i - 2));
      memo[i] = result;
    }
    return result;
  };
  return Q(n);
}

```

</section>
