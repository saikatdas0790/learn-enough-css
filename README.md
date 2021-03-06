# Key takeaways

## CSS Priority Rules

| Order |      Priorities      | Example                                                                                                                         |
| :---: | :------------------: | ------------------------------------------------------------------------------------------------------------------------------- |
|   1   |      Importance      | Adding `!important` (e.g., `width: 100% !important`) to a value overrides all other similar styles (but never use `!important`) |
|   2   |        Inline        | A declaration that is put on an element using `style=`                                                                          |
|   3   |      Media Type      | When a style is applied through a media query                                                                                   |
|   4   |     User defined     | Most browsers have the accessibility feature: a user defined CSS                                                                |
|   5   | Selector specificity | Styling applied via a class or id overwrites generic styling                                                                    |
|   6   |      Rule order      | The last style written has priority                                                                                             |
|   7   |  Parent inheritance  | If there is no style specified, then children inherit styles from their parent                                                  |
|   8   |         CSS          | CSS rules from a stylesheet or `style` block that are applied to generic elements                                               |
|   9   |   Browser defaults   | Lowest priority, these are the default styles that browsers ship with                                                           |

## CSS Combinators

### Child Selector

`div > .class`

- Will select all elements that are direct children of a `div` and have the class `.class`

### Descendant Selectors

`div .class`

- Will select all elements inside a div and having the class `.class`

### Adjacent Sibling Selector

`div + .class`

- Will match any element that immediately follows a `div` and have the class `.class`

### General Sibling Selector

`div ~ .class`

- Will match all elements of the type in the declaration if they follow the primary element
- The sibling selectors don’t pass styles to elements that are wrapped inside any other elements. They only work on elements inside the same parent

### `:` (Pseudo Classes)

- Pseudo-classes select regular elements but under certain conditions, like when their position relative to siblings or when they’re under a particular state
- When you are using the child pseudo-classes you need the elements to be inside of some other HTML element
- If there is anything like text, or an HTML element of a different type, between the top of the parent and the element you are trying to target, the first and last child pseudo-classes won’t work

#### Dynamic pseudo-classes

- `:link`
- `:visited`
- `:hover`
- `:active`
- `:focus`

#### UI element states pseudo-classes

- `:enabled`
- `:disabled`
- `:checked`

### `::` (Pseudo Elements)

Pseudo-elements effectively create new elements that are not specified in the markup of the document and can be manipulated much like a regular element. This introduces huge benefits for creating cool effects with minimal markup, also aiding significantly in keeping the presentation of the document out of the HTML and in CSS where it belongs.

- `::before`
- `::after`
- `::first-letter`
- `::first-line`

## Sizing Units Usage Guidelines

### `px` (pixel)

#### Use for

- Margins
- Padding
- Borders
- Banner ads
- Images

### `%` (percentage)

#### Salient points

- Percentage sizing is based on the parent container that an element is wrapped by
- Percentage heights are a little weird because they require a set height on the parent element
- If you use a percentage for a text size, the resulting size of the font is based not on the pixel dimensions of the container but rather on whatever font-size style that container has inherited

#### Use for

- Text Size

### `em`

#### Salient points

- Represents number of pixels equal to the current font size of any given element’s parent container
- If there is no font size that is inherited, then the default page font size is used
- Automatically change value based on the font size that is inherited by the parent object that they are contained in
- They are cumulative, i.e., if an element with font size _0.5em_ appears inside an element whose font size is also _0.5em_, then the resulting font size for that bottom child element is _0.25em_

#### Use for

- Fonts

### `rem` (root em)

#### Salient points:

- Percentage of absolute font size of the html tag
- Best practice is to set a font size for the module’s wrapper using a _rem_ unit, and then style the fonts inside using _em_ units

#### Use for

- Boxes
- Font sizes

### `vh` & `vw` (viewport-height and viewport-width)

#### Salient points

- Size elements on the page based on the actual size of the browser window or mobile device screen

### `vmin` & `vmax`

#### Salient points:

- `vmin` represents 1% of the smaller viewport dimension (either vh or vw, whichever is smaller)
- `vmax` represents 1% of the larger viewport dimension (either vh or vw, whichever is larger)

## Box Model

### Inline Elements

- Only allowed to have margins and padding applied to the left and right (not top or bottom)
- Won’t accept a width or height set by CSS
- Floated inline elements become block elements

### Display Properties

> Affect the way elements are drawn

#### display: none

- Prevents the element from displaying on the page

#### display: block

- Forces an element to be a block element
- If dimensions not set, it will take up the entire width of its parent element

#### display: inline

- Turns a block element into an inline element
- Width, height, top margins or padding will no longer be applied
- Element will no longer be on its own line, but rather will flow with text like any other inline element

#### display: inline block

- Width, height, top margins and padding will be applied to a particular element
- Text will still flow around it and it will only take up as much horizontal space as it needs to contain the content

#### display: flex

- Forces all child elements to fill the entire parent element

### Positioning

#### `static`

> every element has a static position by default, so the element will stick to the normal page flow. So if there is a `left/right/top/bottom/z-index` set then there will be no effect on that element

#### `relative`

> an element’s original position remains in the flow of the document, just like the static value. But now `left/right/top/bottom/z-index` will work. The positional properties “nudge” the element from the original position in that direction

#### `absolute`

> the element is removed from the flow of the document and other elements will behave as if it’s not even there whilst all the other positional properties will work on it

##### Note

> An element with relative positioning gives you the control to absolutely position children elements inside of it

#### `fixed`

> the element is removed from the flow of the document like absolutely positioned elements. In fact they behave almost the same, only fixed positioned elements are always relative to the document, not any particular parent, and are unaffected by scrolling

#### `sticky`

> the element is treated like a relative value until the scroll location of the viewport reaches a specified threshold, at which point the element takes a fixed position where it is told to stick

#### `inherit`

> the position value doesn’t cascade, so this can be used to specifically force it to, and inherit the positioning value from its parent

### Margins, Padding and Borders

- If you specify the width of a block element and apply a border or padding to it, the additional border or padding will go outside of the content. You end up with an element that is bigger than the dimensions you specified
- To fix the total width of the content box, and force the _border_ and _padding_ to fit inside we can use the `box-sizing: border-box` declaration

#### Margin

- For block elements, the browser allows for only one of the vertical margins to apply (the larger one)
- If you have a block element, like a _div_, _p_, or a _ul_, that has a width set by a style, you can make the browser center that element horizontally within its parent container by setting the left and right _margin_ to _auto_
- _Negative margins_ draws the element up and out of the normal place it occupies on the page and overlays it on content that normally it wouldn’t be able to affect

#### Padding

- _Padding_ pushes content inside an element away from the edges of the element

#### Border

##### border-style

- none
- hidden
- dotted
- dashed
- solid
- double
- groove
- ridge
- inset
- outset

##### border-radius

- creates a box with rounded corners
- To make circles, give the elements a set width and height, and then make the border-radius bigger than the width of the element, while also making sure the height and width of the element are equal

### Floats

- CSS _clear_ rule is used to let the browser know to end floats

### Overflow

Overflow property controls what happens to content that breaks outside of its bounds for a wrapper that has a set height or width

- _visible_: content is not clipped when it proceeds outside its box. This is the _default_ value of the property
- _hidden_: overflowing content will be hidden
- _scroll_: similar to hidden except users will be able to scroll through the hidden content
- _auto_: if the content proceeds outside its box then that content will be hidden whilst a scroll bar should be visible for users to read the rest of the content.
- _initial_: uses the default value which is visible
- _inherit_: sets the overflow to the value of its parent element

> _overflow: hidden_ works for clearing floats because it makes the browser want to keep content contained entirely within the wrapper. If there is no set dimension on the wrapper, the browser just expands the boundaries of the wrapper to reach the end of the floated elements, and then lets the elements that follow display on the page normally

## Other CSS Gotchas

- `vertical-align` only works in `tables`
- `width: 100%` only works on `display: block` & `display: inline-block` elements. Also the `width` on its _parent_ has to be explicitly **set**
- `margin` is applied on top of the _calculated_ width
