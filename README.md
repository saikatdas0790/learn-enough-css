# Key takeaways:


## Sizing Units Usage Guidelines

### px
Use for:
- Margins
- Padding
- Borders
- Banner ads
- Images

### %
#### Salient points
- Percentage sizing is based on the parent container that an element is wrapped by
- Percentage heights are a little weird because they require a set height on the parent element
- If you use a percentage for a text size, the resulting size of the font is based not on the pixel dimensions of the container but rather on whatever font-size style that container has inherited
#### Use for:
- Text Size

### em
#### Salient points:
- Represents number of pixels equal to the current font size of any given element’s parent container
- If there is no font size that is inherited, then the default page font size is used
- Automatically change value based on the font size that is inherited by the parent object that they are contained in
- They are cumulative, i.e., if an element with font size *0.5em* appears inside an element whose font size is also *0.5em*, then the resulting font size for that bottom child element is *0.25em*
#### Use for:
- Fonts

### rem
