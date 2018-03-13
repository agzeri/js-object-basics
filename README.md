# js-object-basics

## Exercise 01 – `createHtmlElement`

### Steps

#### 1. Create a function called `createHtmlElement`
```js
function createHtmlElement() {}
```

#### 2. Tell to the function that will accept one parameter.
```diff
+ function createHtmlElement(obj) {}
```

###### I called `obj`, because we are accepting JS objects as parameters, with the next structure:

```js
const paragraph = {
  element: 'p',
  textContent: 'This is so freaking cool!',
  classNames: 'featured-section'
}

const heading2 = {
  element: 'h2',
  textContent: 'Bill Brasky',
  classNames: 'ui-card-title bg--inverse'
}
```

#### 3. From that structure, I need to generate (taking the first example) the next structure:

```html
<p class='featured-section'>This is so freaking cool!</p>
```

###### If we put attention, we have the type of element that we need to create (`p`), the corresponding classes (`featured-section`) and the text content (`This is fo freaking cool!`).

#### 4. Inside `createHtmlElement` function, we’ll need to code our answer. But first, I’m going to create a variable to save my generated content.

```js
function createHtmlElement(obj) {
  let tag = ''
}
```

#### 5. I need to know what HTML element I need to generate, that element type comes with the property name `element` from the object that user sent us.

```js
const paragraph = {
  element: 'p',
  textContent: 'This is so freaking cool!',
  classNames: 'featured-section'
}
```

###### Considering the previous example, I know that I need to generate a `p` element, I’ll write the correct structure for HTML validation.

```diff
function createHtmlElement(obj) {
+ let tag = '<p></p>'
}
```

#### 7. That way is not dynamic, because our function will generate a `p` element ALWAYS. And I want to generate the element that is sent in the parameter. So, I’ll change that code for this:

```diff
function createHtmlElement(obj) {
+ let tag = `<${obj.element}></${obj.element}>`
}
```

###### I’m accessing to `obj.element` which is the property that is sent in the object and has our `tag`.

#### 8. Now, we have to add the classes and the text content.

###### 8.1 Inspecting the object properties I realize that `obj` parameter contains `textContent` and `classNames`.
+ `textContent` contains the text content
+ `classNames` contains the css class names for my HTML tag

###### 8.2 To add classes to one HTML tag I’ll do it using the `class` attribute, like this:
```html
<p class='featured-section'></p>
```

###### 8.3 So, I’ll change the code to render the class names.
```diff
function createHtmlElement(obj) {
+ let tag = `<${obj.element} class='${obj.classNames}'></${obj.element}>`
}
```

###### 8.4 Now, render the text content from the `obj` received.
```diff
function createHtmlElement(obj) {
+ let tag = `<${obj.element} class='${obj.classNames}'>${obj.textContent}</${obj.element}>`
}
```

#### 9. That’s all. Don’t forget to return our variable created (`tag`).
```diff
function createHtmlElement(obj) {
  let tag = `<${obj.element} class='${obj.classNames}'>${obj.textContent}</${obj.element}>`
  
+ return tag
}
```
**Our tests should be passing with no errors.**

## Exercise 02 – `flipColor`

### Steps

#### 1. Create a function called `flipColor`.

```js
function flipColor() {}
```

#### 2. `flipColor` should take an argument, which is an object. How do I know that? Because on the tests I have this declared:

```js
const tileObj = {
  width: "200px",
  height: "200px",
  color: "blue"
}
```

###### Change the function to accept a parameter. I’m using `tile` as parameter name, you can use whatever you want. But, as in the indications says, _maybe we are changing the tile color in a game_
```diff
+ function flipColor(tile) {}
```

#### 3. According to tests, if I sent an object with a `color` property in blue, the function should return it with a `color` property in red.

###### Basically we are just changing the color, from red to blue, and from blue to red.

```js
// [1]
// Sending this object to the function
const tileObj = {
  width: "200px",
  height: "200px",
  color: "blue"
}

// I should receive this:
const tileObj = {
  width: "200px",
  height: "200px",
  color: "red"
}

// [2]

// If I sent this object to the function:
const tileObj = {
  width: "200px",
  height: "200px",
  color: "red"
}

// I should receive this:
const tileObj = {
  width: "200px",
  height: "200px",
  color: "blue"
}
```

#### 4. Now, it’s time to write the code. I need to know what is the value of `color` property. If it is blue, I should change it to red, and viceversa.


###### 4.1 To access to the value of the `color` property that comes with the object (we chose `tile` as a parameter name), you need to do it like this:

```diff
function flipColor(tile) {
+ console.log(tile.color)
}
```

#### 4.2 In the browser console, I should see:
```js
blue // or red
```

#### 4.3 We know how to access to the color value, it’s time to ask (using a `if`) what is the value so we know how to change it.
```diff
function flipColor(tile) {
+ if (tile.color === 'blue') {
+   // change the color to red
+ }
}
```

#### 4.4 Using another `if` we can validate for the other color (`red`).
```diff
function flipColor(tile) {
  if (tile.color === 'blue') {
    // change the color to red
  }
+ if (tile.color === 'red') {
+   // change the color to blue
+ }
}
```

#### 5. Now, we have our conditions, we need to write our code that will help us to change (_flip_) the color.

###### To change the color, we are going to use the same object received (`tile`) and just modify the `color` property using `dot` notation.

```diff
function flipColor(tile) {
  if (tile.color === 'blue') {
+   tile.color = 'red'
  }
  if (tile.color === 'red') {
+   tile.color = 'blue'
  }
}
```

#### 6. We need to return our object, and because we didn’t create a new one we are just return the object received (`tile`).
```diff
function flipColor(tile) {
  if (tile.color === 'blue') {
    tile.color = 'red'
  }
  if (tile.color === 'red') {
    tile.color = 'blue'
  }
+  
+  return tile
}
```

#### 7. This way we are validating the color, but we have a problem. We are returning at the end, that means if we have an object with a `blue` color will enter the first time in the first `if`, change the color to `red` and then, will enter into the second `if` and change the color to `blue`. (Exactly like we received the object).

###### Solution

**We need to return our object immediately, not at the end because we risk to enter two times in `if`.**
```diff
function flipColor(tile) {
  if (tile.color === 'blue') {
    tile.color = 'red'
    
+   return tile
  }
  if (tile.color === 'red') {
    tile.color = 'blue'
    
+   return tile
  }
  
- return tile
}
```

#### 8. With that fix, our tests should be passing with zero errors.
