# js-object-basics

## Exercise 01

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

```diff
function createHtmlElement(obj) {
  let tag = ''
}
```

#### 5. I need to know what HTML element I need to generate, that elementy type comes with the property name `element` from the object that user send us.

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

#### 9. That’s all. Our tests should be passing with no errors.

