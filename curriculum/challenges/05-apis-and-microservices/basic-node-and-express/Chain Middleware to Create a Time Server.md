---
id: 587d7fb1367417b2b2512bf4
title: Chain Middleware to Create a Time Server
challengeType: 2
---

## Description
<section id='description'>
Middleware can be mounted at a specific route using <code>app.METHOD(path, middlewareFunction)</code>. Middleware can also be chained inside route definition.
Look at the following example:
<blockquote>app.get('/user', function(req, res, next) {<br>  req.user = getTheUserSync();  // Hypothetical synchronous operation<br>  next();<br>}, function(req, res) {<br>  res.send(req.user);<br>})</blockquote>
This approach is useful to split the server operations into smaller units. That leads to a better app structure, and the possibility to reuse code in different places. This approach can also be used to perform some validation on the data. At each point of the middleware stack you can block the execution of the current chain and pass control to functions specifically designed to handle errors. Or you can pass control to the next matching route, to handle special cases. We will see how in the advanced Express section.
In the route <code>app.get('/now', ...)</code> chain a middleware function and the final handler. In the middleware function you should add the current time to the request object in the <code>req.time</code> key. You can use <code>new Date().toString()</code>. In the handler, respond with a JSON object, taking the structure <code>{time: req.time}</code>.
Hint: The test will not pass if you don’t chain the middleware. If you mount the function somewhere else, the test will fail, even if the output result is correct.
</section>

## Instructions
<section id='instructions'>

</section>

## Tests
<section id='tests'>

```yml
- text: The /now endpoint should have mounted middleware
  testString: 'getUserInput => $.get(getUserInput("url") + "/_api/chain-middleware-time").then(data => { assert.equal(data.stackLength, 2, ""/now" route has no mounted middleware"); }, xhr => { throw new Error(xhr.responseText); })'
- text: The /now endpoint should return a time that is +/- 20 secs from now
  testString: 'getUserInput => $.get(getUserInput("url") + "/_api/chain-middleware-time").then(data => { var now = new Date(); assert.isAtMost(Math.abs(new Date(data.time) - now), 20000, "the returned time is not between +- 20 secs from now"); }, xhr => { throw new Error(xhr.responseText); })'

```

</section>

## Challenge Seed
<section id='challengeSeed'>

</section>

## Solution
<section id='solution'>

```js
// solution required
```
</section>
