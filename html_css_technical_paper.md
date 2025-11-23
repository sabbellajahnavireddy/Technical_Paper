# HTML and CSS Technical Paper

## Table of contents
1. Box Model
2. Inline versus Block Elements. Examples.
3. Positioning: Relative/Absolute
4. Common CSS structural classes
5. Common CSS syling classes
6. CSS Specificity
7. CSS Responsive Queries
8. Flexbox/Grid
9. Common header meta tags
10. CSS Units
11. Pseudo-classes and Pseudo-Elements
## 1. Box Model
- The CSS Box Model describes how every HTML element is structured and spaced on a webpage. Each element is treated as a box made up of content, padding, border, and margin. Padding adds space inside the box, the border surrounds it, and the margin creates space outside the element. Understanding the box model helps in controlling layout and design effectively.

```
+--------------------------------------------------+
|                     MARGIN                       |
|  +--------------------------------------------+  |
|  |                   BORDER                   |  |
|  |   +------------------------------------+   |  |
|  |   |               PADDING              |   |  |
|  |   |   +----------------------------+   |   |  |
|  |   |   |          CONTENT           |   |   |  |
|  |   |   +----------------------------+   |   |  |
|  |   +------------------------------------+   |  |
|  +--------------------------------------------+  |
+--------------------------------------------------+
```

- CSS has four main types of box models:

**1. Content-Box (Default Box Model):**
- In this model, the width and height apply only to the content. Padding, border, and margin are added outside the content, which increases the total size of the element.

```html
<div class="content-box">Content-Box Model</div>
```

```css
.content-box {
  width: 200px;
  padding: 20px;
  border: 3px solid black;
  box-sizing: content-box;
  background-color: lightblue;
}
```

**2. Border-Box**
- In this model, the width and height include the content, padding, and border. This means the total size remains fixed, making layout and spacing easier to control.

```html
<div class="border-box">Border-Box Model</div>
```
```css
.border-box {
  width: 200px;
  padding: 20px;
  border: 3px solid black;
  box-sizing: border-box;
  background-color: lightgreen;
}
```

**3. Padding**
- Padding is the space inside an element, between the content and the border. It is used to give breathing room to text or images inside a box. Increasing padding makes the element look more spacious without affecting the space outside the element.

```css
.box-padding {
  padding: 20px;
  background-color: lightgreen;
}
```

**4. Margin**
- Margin is the space outside an element’s border. It controls the distance between one element and another on the webpage. Margins help in layout alignment and separation of components.

```css
.box-margin {
  margin: 25px;
  background-color: lightcoral;
}
```
## 2. Inline versus Block Elements. Examples.

- HTML elements are generally categorized as inline or block based on how they appear and behave on a webpage.

**Block Elements**
- Block elements always start on a new line and span the full width available. They take up the entire row, even if the content is small. These elements are used for structural layout.
- Examples of block elements: <div>, <p>, <h1> to <h6>, <section>, <ul>, <li>
- Example code:
```html
<p>This is a block element. It takes up the full width.</p>
<div>This is another block element.</div>
```
**Inline Elements**
- Inline Elements
- Inline elements do not start on a new line. They only take up as much width as the content requires and are mainly used inside text for formatting or linking.
- Examples of inline elements: <span>, <a>, <strong>, <em>, <img>
- Example code:
```html
<p>This is <span>inline text</span> inside a paragraph.</p>
<a href="#">This is an inline link.</a>
```
## 3. Positioning: Relative/Absolute
- CSS positioning helps control where elements appear on a webpage. Two commonly used positioning types are relative and absolute.
**Relative Position**
- position: relative; keeps the element in its normal place in the document, but allows it to be moved slightly using properties like top, left, right, or bottom. The space originally reserved for the element remains unchanged.
- Example:
```css
.relative-box {
  position: relative;
  top: 10px;
  left: 20px;
  background-color: lightblue;
  width: 150px;
  padding: 10px;
}
```
```html
<div class="relative-box">This box is relatively positioned.</div>
```

**Absolute Position**
- position: absolute; removes the element from the normal document flow and positions it relative to the nearest positioned parent (not static). It does not take up space in the layout.
- Example:
```css
.container {
  position: relative;
  width: 200px;
  height: 200px;
  background-color: lightgray;
}

.absolute-box {
  position: absolute;
  top: 20px;
  left: 30px;
  background-color: lightgreen;
  padding: 10px;
}
```
```html
<div class="container">
  <div class="absolute-box">Absolutely positioned element</div>
</div>
```
## 4. Common CSS structural classes
- CSS structural classes are reusable class names commonly applied to organize layout, spacing, and formatting across a webpage. They help maintain consistency and make CSS easier to manage. Some frequently used structural classes include containers, rows, and columns, which help in arranging content in clean sections.

**1. .container**
- Used to wrap content and center layout elements.
- Example:

```css
.container {
  width: 80%;
  margin: auto;
  padding: 20px;
}
```
```html
<div class="container">
  <p>Content inside a container.</p>
</div>
```
**2. .row**
- Used to group elements horizontally.
- Example:

```css
.row {
  display: flex;
  gap: 10px;
}
```
```html
<div class="row">
  <div>Item 1</div>
  <div>Item 2</div>
</div>
```
**3. .column**
- Used to create vertical sections, especially inside rows.
- Example:

```css
.column {
  flex: 1;
  padding: 10px;
  background-color: lightgray;
}
```
```html
<div class="row">
  <div class="column">Column 1</div>
  <div class="column">Column 2</div>
</div>
```
## 5. Common CSS Styling Classes
- CSS styling classes are reusable class names used to apply consistent visual formatting such as colors, text alignment, spacing, and buttons throughout a webpage. These classes help avoid repeating styles and make the design easier to maintain.

**1. .text-center**
- Used to align text to the center.
- Example:

```css
.text-center {
  text-align: center;
}
```
```html
<p class="text-center">This text is centered.</p>
```
**2. .btn**
- Used for buttons to apply consistent styling.
- Example:

```css
.btn {
  padding: 10px 15px;
  background-color: #4CAF50;
  color: white;
  border-radius: 5px;
  text-decoration: none;
}
```
```html
<a href="#" class="btn">Click Me</a>
```
**3. .highlight**
- Used to highlight important text.
- Example:

```css
.highlight {
  background-color: yellow;
  font-weight: bold;
}
```
```html
<p>This is a <span class="highlight">highlighted</span> word.</p>
```

**4. .shadow**
- Adds a shadow effect to elements.
- Example:
```css
.shadow {
  box-shadow: 0 4px 6px rgba(0,0,0,0.3);
}
```
```html
<div class="shadow">This box has a shadow effect.</div>
```
## 6. CSS Specificity
- CSS specificity determines which style rule is applied when multiple rules target the same element. The browser assigns weight to different selectors, and the rule with the highest specificity gets applied. Specificity follows a hierarchy: **Inline styles > IDs > Classes/Attributes/Pseudo-classes > Elements/Pseudo-elements.**

- Specificity Order (Highest to Lowest):
1. Inline Styles (style attribute inside HTML)
2. ID Selectors (#id)
3. Class, Attribute, and Pseudo-class Selectors (.class, :hover)
4. Element and Pseudo-element Selectors (p, h1, ::before)

- Example:

```html
<p id="main" class="text highlight" style="color: red;">CSS Specificity Example</p>
```
```css
p {
  color: blue;   /* Lowest specificity */
}

.text {
  color: green;  /* Class selector */
}

#main {
  color: purple; /* ID selector */
}
```
## 7. CSS Responsive Queries
- CSS responsive queries, also known as media queries, allow a webpage to adjust its layout and styling based on the device screen size. They help create designs that work well on desktops, tablets, and mobile devices. Media queries detect the screen width and apply specific styles when conditions are met, making the webpage responsive and user-friendly.
- Example:
```css
/* Default style (for large screens) */
.box {
  width: 400px;
  background-color: lightblue;
}

/* Tablet size */
@media (max-width: 768px) {
  .box {
    width: 300px;
    background-color: lightgreen;
  }
}

/* Mobile size */
@media (max-width: 480px) {
  .box {
    width: 200px;
    background-color: lightcoral;
  }
}
```
```html
<div class="box">Responsive Box</div>
```
## 8. Flexbox/Grid
- Flexbox and Grid are modern CSS layout systems used to arrange elements on a webpage in an efficient and responsive way.

- **Flexbox:**
- Flexbox (Flexible Box Layout) is used for one-dimensional layouts — either in a row (horizontal) or a column (vertical). It adjusts space automatically between items, making alignment and responsiveness easier.

- Example:
```css
.flex-container {
  display: flex;
  gap: 10px;
}

.flex-item {
  background-color: lightblue;
  padding: 15px;
}
```
```html
<div class="flex-container">
  <div class="flex-item">Item 1</div>
  <div class="flex-item">Item 2</div>
  <div class="flex-item">Item 3</div>
</div>
```
- **CSS Grid**
- CSS Grid is a two-dimensional layout system that allows control over rows and columns. It is ideal for more complex page structures like galleries or full page layouts.

```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}

.grid-item {
  background-color: lightgreen;
  padding: 15px;
}
```
```html
<div class="grid-container">
  <div class="grid-item">Box 1</div>
  <div class="grid-item">Box 2</div>
  <div class="grid-item">Box 3</div>
</div>
```
## 9. Common header meta tags
- Meta tags are used inside the <head> section of an HTML document to provide information about the webpage. They do not appear on the website visually but help browsers, search engines, and responsive design understand how the page should behave. Some commonly used meta tags include viewport settings, character encoding, and SEO-related information.

- Example:
```html
<head>
  <!-- Sets character encoding -->
  <meta charset="UTF-8">

  <!-- Controls responsive layout on mobile devices -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Description shown by search engines -->
  <meta name="description" content="This is a sample webpage demonstrating meta tags.">

  <!-- Keywords for search engine optimization -->
  <meta name="keywords" content="HTML, CSS, Web Development">

  <!-- Author of the document -->
  <meta name="author" content="Jahnavi">
  
  <title>Meta Tag Example</title>
</head>
```

## 10. CSS Units:
- CSS units define measurement values such as size, spacing, and layout. They are classified into absolute and relative units.

- **1. Absolute Units**
- These units do not change based on screen size or settings.

| Unit | Meaning                          | Example            |
| ---- | -------------------------------- | ------------------ |
| `px` | Pixels (fixed size, most common) | `font-size: 16px;` |
| `cm` | Centimeters                      | `width: 5cm;`      |
| `mm` | Millimeters                      | `height: 50mm;`    |
| `in` | Inches (1in = 96px)              | `width: 2in;`      |
| `pt` | Points (1pt = 1/72 inch)         | `font-size: 12pt;` |
| `pc` | Picas (1pc = 12pt)               | `width: 2pc;`      |

- **2. Relative Units**
- These units scale based on font size, viewport, or parent element.

| Unit   | Meaning                             | Example              |
| ------ | ----------------------------------- | -------------------- |
| `%`    | Relative to parent size             | `width: 50%;`        |
| `em`   | Relative to the element’s font size | `margin: 2em;`       |
| `rem`  | Relative to root font size          | `font-size: 1.5rem;` |
| `vh`   | 1% of viewport height               | `height: 50vh;`      |
| `vw`   | 1% of viewport width                | `width: 80vw;`       |
| `vmin` | Smaller value of `vh` or `vw`       | `font-size: 4vmin;`  |
| `vmax` | Larger value of `vh` or `vw`        | `font-size: 4vmax;`  |
| `ch`   | Width of the character "0"          | `width: 40ch;`       |
| `ex`   | Height of lowercase letter "x"      | `line-height: 2ex;`  |

- Example code:
```css
.container {
  width: 70%;
  height: 50vh;
  font-size: 1.2rem;
  padding: 2em;
  margin: 20px;
}
```
```html
<div class="container">
  CSS Units Example
</div>
```
## 11. Pseudo-Classes and Pseudo-Elements
- CSS pseudo-classes and pseudo-elements allow developers to style elements based on states or specific parts of an element that cannot be targeted using normal selectors.

**Pseudo-Classes**
- A pseudo-class is used to apply styles to an element when it is in a specific state (such as hover, focus, or visited).
- Common Pseudo Classes:
Pseudo-Classes
| Pseudo-Class   | Meaning                                          | Example                                 |
| -------------- | ------------------------------------------------ | --------------------------------------- |
| `:hover`       | Applies style when the mouse is over the element | `a:hover {color: red;}`                 |
| `:active`      | When an element is being clicked                 | `button:active {background: gray;}`     |
| `:focus`       | When an element like input is focused            | `input:focus {border: 2px solid blue;}` |
| `:visited`     | For visited links                                | `a:visited {color: purple;}`            |
| `:first-child` | Targets first child of parent                    | `p:first-child {font-weight: bold;}`    |

- Example code:
```css
button:hover {
  background-color: lightblue;
}

input:focus {
  border: 2px solid green;
}
```
```html
<button>Hover Me</button>
<br><br>
<input type="text" placeholder="Click to focus">
```

**Pseudo-Elements**
- Pseudo-elements are used to style specific parts of an element such as the first line, first letter, or to insert content.
- Common Pseudo-Elements:

| Pseudo-Element   | Meaning                        | Example                              |
| ---------------- | ------------------------------ | ------------------------------------ |
| `::before`       | Inserts content before element | `h1::before {content: "* ";}`        |
| `::after`        | Inserts content after element  | `h1::after {content: " ✔";}`         |
| `::first-letter` | Styles the first letter        | `p::first-letter {font-size: 2rem;}` |
| `::first-line`   | Styles the first line of text  | `p::first-line {font-weight: bold;}` |
| `::selection`    | Styles text when selected      | `::selection {background: yellow;}`  |

- Example code:
```css
p::first-letter {
  font-size: 30px;
  color: red;
}

h2::after {
  content: " — End";
  color: gray;
}
```
```html
<h2>Title</h2>
<p>This is an example paragraph demonstrating pseudo-elements.</p>
```





