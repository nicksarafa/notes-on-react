## JSX
#### Single line variables
`var primaryHeader = <h1></h1>;`
* JSX tags are not required to be self-closing tags (<MyComponentClass />) but may also be open (<MyComponentClass></MyComponentClass>)
***
#### Multi line variables
* If a JSX line takes up more than 1 line you should wrap it in parenthesis
* Nested variables can be saved as expressions and/or passed to functions
```
render (
  <div class="title">
    <h1>
      Hello world
    </h1>
  </div>
);
```
#### JSX outermost wrapper weirdness
* JSX render function(s) may only have __precisely one (1)__ outermost element
##### Works
```
var example = (
	<div>
		<h1>Yo</h1>
		<h1>Lo</h1>
	</div>
);
```
##### Breaks
```
var example = (
	<h1>Yo</h1>
	<h1>Lo</h1>
);
```
***
#### HTML versus JSX naming diff
```
HTML => class
JSX  => className
```
* Difference in naming convention between HTML and JSX is due to the manner in which JSX is translated into JavaScript
* Also, `class` is a reserved word in JavaScript
* When JSX is rendered, JSX className attributes automatically become class attributes
#### JSX closing tag gotcha
* Unlike HTML self-closing tags (`<img/>`, `<input/>`, etc.), JSX self-closing tags are __required to have a space before the /> at the end of the self closing tag__
##### Works
`<img src="myImage.jpeg />`
##### Breaks
`<img src="myImage.jpeg/>`
***
## JSX Curly Braces {}
* JSX curly braces themselves __are not treated as JSX nor as JavaScript__
* JSX curly braces are __markers that signal__ the beginning and end of a JavaScript injection into JSX, similar to the quotation marks that signal the boundaries of a string
* Any code in between the tags of a JSX element will be read as JSX
 `<h1>2+3</h1>   => 2 + 3`
* Any code wrapped in Curly Braces {} renders as JavaScript
`<h1>{2+3}</h1> => 5`
***
## JSX Event Listeners
JSX elements can have event listeners, just like HTML elements can
`HTML => <img onclick="functionName"/>`
`JSX  => <img onClick={functionName} />`
* Note the letter 'c' inside of the JSX event listener is capitalized
* Note space between " and />
***
## JSX lack of if/else statement(s) workarounds
* __Cannot__ inject JavaScript `if` and/or `else` statements into a JSX expression
Workarounds to JSX if/then exclusion include..
1. Execute if/else statement OUTSIDE of JSX
2. Execute if/else via a Ternary Operator
* JSX accepts Ternary operator, and behaves the same way as JS
Take this if/then statement..
```
if (userAgeIsAtLeast21) {
  serveBeer();
} else {
  serveSoda();
}
```
Is the same as..
```
userAgeIsAtLeast21 ? serveBeer() : serveSoda(); 
```
Or..
```
if (userAge >= 21) {
  serveBeer();
} else {
  serveSoda();
}
```
Or..
```
userAge >= 21 ? serveBeer() : serveSoda();
```
3. Use an executable `!condition && statement`
`{ !condition && <h1>Condition was met and this is rendered</h1> }`
***
## .map in JSX
.map generates elements using iteration
```
var fruits = [
  'apple',
  'bananna',
  'orange'
];
```
```
var listFruits = fruits.map(
  function(fruit) {
    return <li>{fruit}</li>
  }
);
```
```
ReactDOM.render(
  <ul>{listFruits}</ul>,
  document.getElementById('app')
);
```
***
## Keys in JSX
- A key is a JSX attribute
- The attribute's name is key.
- The attribute's value should be something unique.
- Similar to an id attribute.
- Keys don't do anything that you can see. React uses them internally to keep track of lists
- Note ~ If you don't use keys when you're supposed to, React might accidentally scramble your list-items into the wrong order!
* Not all lists need keys.. 
- List needs keys only if..
  1. The list-items need to have memory from one render to the next. For instance, when a to-do list renders, each item must "remember" whether it is supposed to be checked off. The items should not get amnesia when they render.
	2. A list's order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.
```
var people = [
  'appleMan',
  'banannaMan',
  'orangeMan'
];
var listPeople = people.map(
  function(person, i) {
    return <li key={"person_" + i}></li>;
  }
);
ReactDOM.render(
  <ul>{listPeople}</ul>,
  document.getElementById('app')
);
```
***
#### JSX is secretly the __same thing__ as React.createElement
When a JSX element is compiled, the compiler actually converts it into the method that you see above: React.createElement()
* JSX
`var header = <h1>Hello, world</h1>;`
* React 
```
var header = React.createElement(
  "h1",           // <= string/ReactClass type
  null,           // <= [object props]	
  "Hello, world"  // <= [children ...]
);
```
