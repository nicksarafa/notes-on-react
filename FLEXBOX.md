# FlexBox
### align-content (alignContent)
#### Sets the spacing between lines, determining how multiple lines are spaced apart from each other
##### If there is only one (1) line, align-content does __nothing__
* center: Lines are packed at the vertical center of the container.
* flex-end: Lines are packed at the bottom of the container.
* flex-start: Lines are packed at the top of the container.
* space-around: Lines display with equal spacing around them.
* space-between: Lines display with equal spacing between them.
* stretch: Lines are stretched to fit the container.
***
### align-items (alignItems)
#### Declares how the items as a whole are aligned within the container
#### Vertical Alignment __unless flex-direction: column;__
* baseline: Items display at the baseline of the container
* center: Items align at the vertical center of the container
* flex-end: Items align to the bottom of the container
* flex-start: Items align to the top of the container
* stretch: Items are stretched to fit the container
***
### align-self (alignSelf)
#### __Overrides__ the align-items attribute
#### Accepts same parameters as align-items
* baseline: Items display at the baseline of the container
* center: Items align at the vertical center of the container
* flex-end: Items align to the bottom of the container
* flex-start: Items align to the top of the container
* stretch: Items are stretched to fit the container
***
### flex-direction (flexDirection)
#### **Direction** of items inside of the container
* column-reverse: Items are placed bottom to top
* column: Items are placed top to bottom
* row-reverse: Items are placed opposite to the text direction
* row: Items are placed the same as the text direction
***
### flex-wrap (flexWrap)
#### Specifies whether flex items are forced onto a single line or can be 'wrapped' onto multiple lines
* nowrap: Every item is fit to a single line.
* wrap: Items wrap around to additional lines.
* wrap-reverse: Items wrap around to additional lines in reverse.
***
### flex-flow __no react-native prop__
#### Shorthand for flex-direction and flex-wrap
* Accepts parameters of one, or both <flex-direction> and <flex-wrap> separated by a space
***
### justify-content (justifyContent)
#### Horizontal Alignment __unless flex-direction: column;__
* center: Items align at the center of the container
* flex-end: Items align to the right side of the container
* flex-start: Items align to the left side of the container
* space-around: Items display with equal spacing around them
* space-between: Items display with equal spacing between them
***
### order __no react-native prop__
#### Takes integer which specifies the order of the flex item
* 0 by default
* Can be positive (+), or negative (-)
* Can be set to a group of flex items, as well as individually
* Always relative to the flex item's starting position after the view is rendered
***
#### Gotchas
##### *-reversed
* When you set the direction to a reversed row or column, start and end are also reversed
  * Applies to both **column-reversed** and **row-reversed**
***
##### align-items ♻ justify-content
* When the flex direction is a column, justify-content changes to the vertical and align-items to the horizontal
