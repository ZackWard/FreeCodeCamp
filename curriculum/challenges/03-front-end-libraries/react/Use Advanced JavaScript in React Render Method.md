---
id: 5a24c314108439a4d4036183
title: Use Advanced JavaScript in React Render Method
challengeType: 6
isRequired: false
---

## Description
<section id='description'>
In previous challenges, you learned how to inject JavaScript code into JSX code using curly braces, <code>{ }</code>, for tasks like accessing props, passing props, accessing state, inserting comments into your code, and most recently, styling your components. These are all common use cases to put JavaScript in JSX, but they aren't the only way that you can utilize JavaScript code in your React components.
You can also write JavaScript directly in your <code>render</code> methods, before the <code>return</code> statement, <strong><em>without</em></strong> inserting it inside of curly braces. This is because it is not yet within the JSX code. When you want to use a variable later in the JSX code <em>inside</em> the <code>return</code> statement, you place the variable name inside curly braces.
</section>

## Instructions
<section id='instructions'>
In the code provided, the <code>render</code> method has an array that contains 20 phrases to represent the answers found in the classic 1980's Magic Eight Ball toy. The button click event is bound to the <code>ask</code> method, so each time the button is clicked a random number will be generated and stored as the <code>randomIndex</code> in state. On line 52, delete the string <code>"change me!"</code> and reassign the <code>answer</code> const so your code randomly accesses a different index of the <code>possibleAnswers</code> array each time the component updates. Finally, insert the <code>answer</code> const inside the <code>p</code> tags.
</section>

## Tests
<section id='tests'>

```yml
- text: The <code>MagicEightBall</code> component should exist and should render to the page.
  testString: 'assert.strictEqual(Enzyme.mount(React.createElement(MagicEightBall)).find("MagicEightBall").length, 1, "The <code>MagicEightBall</code> component should exist and should render to the page.");'
- text: <code>MagicEightBall</code>&apos;s first child should be an <code>input</code> element.
  testString: 'assert.strictEqual(Enzyme.mount(React.createElement(MagicEightBall)).children().childAt(0).name(), "input", "<code>MagicEightBall</code>&apos;s first child should be an <code>input</code> element.");'
- text: <code>MagicEightBall</code>&apos;s third child should be a <code>button</code> element.
  testString: 'assert.strictEqual(Enzyme.mount(React.createElement(MagicEightBall)).children().childAt(2).name(), "button", "<code>MagicEightBall</code>&apos;s third child should be a <code>button</code> element.");'
- text: <code>MagicEightBall</code>&apos;s state should be initialized with a property of <code>userInput</code> and a property of <code>randomIndex</code> both set to a value of an empty string.
  testString: 'assert(Enzyme.mount(React.createElement(MagicEightBall)).state("randomIndex") === "" && Enzyme.mount(React.createElement(MagicEightBall)).state("userInput") === "", "<code>MagicEightBall</code>&apos;s state should be initialized with a property of <code>userInput</code> and a property of <code>randomIndex</code> both set to a value of an empty string.");'
- text: 'When <code>MagicEightBall</code> is first mounted to the DOM, it should return an empty <code>p</code> element.'
  testString: 'assert(Enzyme.mount(React.createElement(MagicEightBall)).find("p").length === 1 && Enzyme.mount(React.createElement(MagicEightBall)).find("p").text() === "", "When <code>MagicEightBall</code> is first mounted to the DOM, it should return an empty <code>p</code> element.");'
- text: 'When text is entered into the <code>input</code> element and the button is clicked, the <code>MagicEightBall</code> component should return a <code>p</code> element that contains a random element from the <code>possibleAnswers</code> array.'
  testString: 'async () => { const waitForIt = (fn) => new Promise((resolve, reject) => setTimeout(() => resolve(fn()), 250)); const comp = Enzyme.mount(React.createElement(MagicEightBall)); const simulate = () => { comp.find("input").simulate("change", { target: { value: "test?" }}); comp.find("button").simulate("click"); }; const result = () => comp.find("p").text(); const _1 = () => { simulate(); return waitForIt(() => result()) }; const _2 = () => { simulate(); return waitForIt(() => result()) }; const _3 = () => { simulate(); return waitForIt(() => result()) }; const _4 = () => { simulate(); return waitForIt(() => result()) }; const _5 = () => { simulate(); return waitForIt(() => result()) }; const _6 = () => { simulate(); return waitForIt(() => result()) }; const _7 = () => { simulate(); return waitForIt(() => result()) }; const _8 = () => { simulate(); return waitForIt(() => result()) }; const _9 = () => { simulate(); return waitForIt(() => result()) }; const _10 = () => { simulate(); return waitForIt(() => result()) }; const _1_val = await _1(); const _2_val = await _2(); const _3_val = await _3(); const _4_val = await _4(); const _5_val = await _5(); const _6_val = await _6(); const _7_val = await _7(); const _8_val = await _8(); const _9_val = await _9(); const _10_val = await _10(); const actualAnswers = [_1_val, _2_val, _3_val, _4_val, _5_val, _6_val, _7_val, _8_val, _9_val, _10_val]; const hasIndex = actualAnswers.filter((answer, i) => possibleAnswers.indexOf(answer) !== -1); const notAllEqual = new Set(actualAnswers); assert(notAllEqual.size > 1 && hasIndex.length === 10, "When text is entered into the <code>input</code> element and the button is clicked, the <code>MagicEightBall</code> component should return a <code>p</code> element that contains a random element from the <code>possibleAnswers</code> array.");}'

```

</section>

## Challenge Seed
<section id='challengeSeed'>

<div id='jsx-seed'>

```jsx
const inputStyle = {
  width: 235,
  margin: 5
}

class MagicEightBall extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: ",
      randomIndex: "
    }
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: "
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const possibleAnswers = [
      'It is certain',
      'It is decidedly so',
      'Without a doubt',
      'Yes, definitely',
      'You may rely on it',
      'As I see it, yes',
      'Outlook good',
      'Yes',
      'Signs point to yes',
      'Reply hazy try again',
      'Ask again later',
      'Better not tell you now',
      'Cannot predict now',
      'Concentrate and ask again',
      'Don\'t count on it',
      'My reply is no',
      'My sources say no',
      'Most likely',
      'Outlook not so good',
      'Very doubtful'
    ];
    const answer = 'change me!' // << change code here
    return (
      <div>
        <input
          type="text"
          value={this.state.userInput}
          onChange={this.handleChange}
          style={inputStyle} /><br />
        <button onClick={this.ask}>
          Ask the Magic Eight Ball!
        </button><br />
        <h3>Answer:</h3>
        <p>
          { /* change code below this line */ }

          { /* change code above this line */ }
        </p>
      </div>
    );
  }
};
```

</div>


### After Test
<div id='jsx-teardown'>

```js
console.info('after the test');
```

</div>

</section>

## Solution
<section id='solution'>


```js
const inputStyle = {
  width: 235,
  margin: 5
}

class MagicEightBall extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: ",
      randomIndex: "
    }
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: "
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const possibleAnswers = [
      "It is certain", "It is decidedly so", "Without a doubt",
      "Yes, definitely", "You may rely on it", "As I see it, yes",
      "Outlook good", "Yes", "Signs point to yes", "Reply hazy try again",
      "Ask again later", "Better not tell you now", "Cannot predict now",
      "Concentrate and ask again", "Don't count on it", "My reply is no",
      "My sources say no", "Outlook not so good","Very doubtful", "Most likely"
    ];
    const answer = possibleAnswers[this.state.randomIndex];
    return (
      <div>
        <input
          type="text"
          value={this.state.userInput}
          onChange={this.handleChange}
          style={inputStyle} /><br />
        <button onClick={this.ask}>Ask the Magic Eight Ball!</button><br />
        <h3>Answer:</h3>
        <p>
          {answer}
        </p>
      </div>
    );
  }
};
```

</section>
