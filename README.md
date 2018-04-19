# Key takeaways

## CSS Priority Rules

| Order | Priorities | Example |
| :-------------: | :-------------: | ----- |
| 1 | Importance |  Adding `!important` (e.g., `width: 100% !important`) to a value overrides all other similar styles (but never use `!important`) |
| 2 |	Inline |	A declaration that is put on an element using `style=` |
| 3 |	Media Type |	When a style is applied through a media query |
| 4 |	User defined |	Most browsers have the accessibility feature: a user defined CSS |
| 5 |	Selector specificity |	Styling applied via a class or id overwrites generic styling |
| 6 |	Rule order |	The last style written has priority |
| 7 |	Parent inheritance |	If there is no style specified, then children inherit styles from their parent |
| 8 |	CSS |	CSS rules from a stylesheet or `style` block that are applied to generic elements |
| 9 |	Browser defaults |	Lowest priority, these are the default styles that browsers ship with |

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
- They are cumulative, i.e., if an element with font size *0.5em* appears inside an element whose font size is also *0.5em*, then the resulting font size for that bottom child element is *0.25em*
#### Use for
- Fonts

### `rem` (root em)
#### Salient points:
- Percentage of absolute font size of the html tag
- Best practice is to set a font size for the module’s wrapper using a *rem* unit, and then style the fonts inside using *em* units
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

### Margins, Padding and Borders
- If you specify the width of a block element and apply a border or padding to it, the additional border or padding will go outside of the content. You end up with an element that is bigger than the dimensions you specified
- To fix the total width of the content box, and force the *border* and *padding* to fit inside we can use the `box-sizing: border-box` declaration

#### Margin
- For block elements, the browser allows for only one of the vertical margins to apply (the larger one)
- If you have a block element, like a *div*, *p*, or a *ul*, that has a width set by a style, you can make the browser center that element horizontally within its parent container by setting the left and right *margin* to *auto*
- *Negative margins* draws the element up and out of the normal place it occupies on the page and overlays it on content that normally it wouldn’t be able to affect

#### Padding
- *Padding* pushes content inside an element away from the edges of the element

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
- CSS *clear* rule is used to let the browser know to end floats

### Overflow
Overflow property controls what happens to content that breaks outside of its bounds for a  wrapper that has a set height or width
- *visible*: content is not clipped when it proceeds outside its box. This is the *default* value of the property
- *hidden*: overflowing content will be hidden
- *scroll*: similar to hidden except users will be able to scroll through the hidden content
- *auto*: if the content proceeds outside its box then that content will be hidden whilst a scroll bar should be visible for users to read the rest of the content.
- *initial*: uses the default value which is visible
- *inherit*: sets the overflow to the value of its parent element

> *overflow: hidden* works for clearing floats because it makes the browser want to keep content contained entirely within the wrapper. If there is no set dimension on the wrapper, the browser just expands the boundaries of the wrapper to reach the end of the floated elements, and then lets the elements that follow display on the page normally


## Jekyll Basics

### Jekyll Object Types
- layouts/layout templates
- includes
- pages/page templates
- posts

#### Layouts/layout templates
- Anything in the `_layouts` directory get read by the engine looking for *Liquid* tags and other Jekyll formatting
- One of the key parts of many Jekyll pages is *frontmatter*, which is metadata at the top of an HTML file (in YAML format) that identifies the kind of layout to be used, a page-specific title, etc.
- If there is no frontmatter in a layout file, then it is a true layout, and it needs to have a full HTML page structure. If there is frontmatter, then the file is a layout template that can be built into other layouts, and it doesn’t need to have a full HTML page structure
- Layouts are often the most base-level objects, defining a standard page with a `DOCTYPE, html/head/body` tags, `meta` tags, stylesheet links, JavaScript, etc., and they usually pull in includes like a site header or site footer
- Layouts have the special ability to load content, like posts, using a generic Liquid tag that looks like this: `{{ content }}`

#### Includes
- Files in the `_includes` folder can have Jekyll magic even though they don’t need frontmatter, and these files are always intended to be built into something else
- Includes tend to be little snippets of a site that get repeated on many pages, such as the *header* and *footer* or a standard set of social-media *links*

#### Pages
- Any other HTML file in the project directory is a page
- If there is no frontmatter in the file it is a static page, and Jekyll magic will not work (Liquid tags go unprocessed)
- If a page has frontmatter, though, it will need to specify a layout, and then all the Jekyll magic will be available

#### Posts
- Posts are self-contained pieces of content, such as blog posts or product details, that are saved as files in the `_posts` directory
- Content like *blog posts* are typically organized by date, while other post content (like product descriptions) are organized based on other attributes into *collections*

### Style Note: Style HTML5 elements with classes
- To ensure maximum backwards compatibility, it’s not a good idea to target the newer HTML5 semantic elements like `header` and `nav` directly
- When an old browser encounters new HTML tags, it sees them as regular `divs`, and any styles are ignored
- To avoid this situation, it’s better to give such elements classes, and then target your styles at the classes

### Positioning
