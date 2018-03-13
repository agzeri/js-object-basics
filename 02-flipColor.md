# js-object-basics

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
