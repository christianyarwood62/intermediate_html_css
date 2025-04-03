# Default styles
- each browser has its own set of default styles
- can override defaults in CSS as they take precedence
    - can use CSS resets. They provide a clean slate for developers, but not mandatory to use
- top fix consistency problems, use:
    1) normalise - apply a ***normalise*** stylesheet to fix inconsistencies but broadly retain default set of styles
    2) reset - removes marins, paddings, text styles across the board
    3) hybrid - many frameworks take hybrid approach. 

# CSS Units
## Absolute units
- px are absolute units

## Relative units
- em and rem refer to font size **note - prefer rem**
- 1em is the font-size of an element. For example, if element font-size is 16px, then setting its width to 4em would make its width 64px
- 1 rem is the font-size of the root element (either :root or html)
**- use rem for font sze, px for everything else**

## Viewport units
- vh and vw relate to size of the viewport, e.g. 1vh is equal to 1% of the viewport height and 1 vw is equal to 1% of the viewport width. Useful for full-screen app-like interfaces
**- difference between vh and %, is %is relative to local contect, vh is relative to full width of browser window**
- vmin and vmax - percentages of viewport width or height (whichevere is smaller). 

## Responsive typography
- use a calc()
    - e.g. calc(16px + 0.5vw) - this combines a base size with a viewport relative adjustment



# More Text Styles
## System Font Stacks
- tries to use the default font of system, going through list until it finds one thats installed
```
body {
  font-family: system-ui, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
```

## Web fonts
- if you want to use a font that isnt installed on users device. need to import it. Remember to add a fallback still!
- use font-family: system-ui to default system font

## Online font libraries
- To use a font from one of these libraries, go to the website, select a font and then copy a snippet from the website to import that font from their server into your website. Usually given a <link> tag to put in the html or an @import tag to be dropped at top of CSS file.

## Self hosted fonts
- it is possible to use a font downloaded from web, by importing and defining a custom font using the @font-face rule. have to use @font-face in css to specify which font file to download, then an html element to use that specified font
```
@font-face {
  font-family: my-cool-font;
  src: url(../fonts/the-font-file.woff);
}

h1 {
  font-family: my-cool-font, sans-serif;
}
```
- when downloading fonts, it will get a zip with multiple files, use https://www.fontsquirrel.com/tools/webfont-generator to download another zip file of the css. This will have WOFF2 file - use this! its newer but not supported everywhere.

## Text Styles
- Font-style:
    - use <em> tag to make text in the ***middle of the text*** italic (for emphasis), otherwise use font-style 
- letter-spacing:
    - letter-spacing adjusts space in a word, uses px/em
- line-height:
    - increases readibility, no units
- text-transform:
    - changes case of given text
- text-shadow:
    - good for presentations
- ellipsis:
    - not a single property
    - set text-overflow: ellipsis; to truncate overflowing text with an ellipsis, but have to also use a few other properties to make it work, use this full snippet:
    ```
        .overflowing {
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    }
    ```
- use clamp(minimum value, calc function, max value) function to scale font size to a specific range,

# More CSS properties
## Background property
- shorthand for 8 different background related properties
- look online for syntax

## Borders
- another shorthand.
- border-radius creates rounded corners on things

## box-shadow
- creates depth to element

## Overflow
- defines what happens to an element when its content is too big to fit
- most common usage is to add scrollbars to an element inside a webpage

# Advanced Selectors
> - the child combinator
    - use > to select only the child div in a parent element. Can be used multiple times to select a grand-child
+ - the adjacant combinator
    - using this will only select the adjacant selector to the first selection, e.g. .group1 + div (selects the div adjacant to .group1)
~ - the general combinator
    - selects all the siblings following an element, not just the first one

## Pseudo-selectors
### a pseudo class
 is a selector that selects elements that are in a specific state, e.g. being hovered or are the first element of their type. They start with a colon, e.g. :hover.. Or e.g:
    div p:first-child {
        font-size: 120%;
    }
    - also :last-child, :only-child, :invalid are pseudo classes.
#### Dynamic and user action pseudo-classes
- :focus
    - applies to an element when selecting it with their cursor or keyboard
- :hover
    - under mouse pointer
- :active
    - applies to elements being clicked to give feedback
- :visited
    - applies to all URL links that user has visited 
- :link
    - will apply to all unvisited url links

#### structural pseudo classes
- :root
    - represents top level of your document, one with no parents, equivalent to the html 
- :first-child and :last-child match elements that are first or last sibling
- :empty
    - matches elements with no children
- :only-child 
    - matches elements that dont have siblings
- :nth-child
    - e.g. .myList:nth-child(5) selects 5th element with class myList. .myList:nth-child(even) is possible to select every even element.

### Pseudo-element
- behave similar to pseudo classes but act as if you added a new html element into the markup, rather than applying a class
- start with a double colon, e.g. ::before, or ::first-line (this essentially creates a span around the first line so you can apply CSS)
- ::before and ::after would do something like add text after an element. More typical to insert icons, rather than text through CSS.

### Attribute Selectors
- attributes are anything in the opening tag of html element, like src or href
- basic usage:
    1) [attribute] {}. e.g. [src]
    2) img[src] {}. Targests img elements that have an src attribute
    3) img[src=""] {}. Targets img elements with an src attribute of puppy.jpg
- sometime you want to be more general accessing attributes, e.g. interested in img elements where src attribute ends in .jpg:
    - [attribute^="value"] - ^= Will match strings from the start. e.g.:
        [class^='aus'] {
            /* Classes are attributes too!
                This will target any class that begins with 'aus':
                class='austria'
                class='australia'
            */
        }
    - [attribute$="value"] - $= Will match strings from the end.
    - [attribute*="value"] - *= The wildcard selector will match anywhere inside the string.

# Positioning
## Static and relative Positioning
- static is the default positioning mode 
- relative is almost same as static, but allows you change top, left, right, and bottom of this element relative to the static position
    - relative takes it out of the normal flow so things may overflow

## Absolute positioning
- allows you to position something at an exact point on a screen without disturbing elements around it
- useful for: modals, images with caption, icons on top of elements

## Fixed positioning
- fixed elements are removed from normal flow of document and are positioned relative to the viewport

## Sticky positioning
- act like normal elements until you scroll past them, then they behave like fixed elements. 
- not taken out of normal flow of document
- useful for sticky headers when you scroll down to see what category youre in

# CSS functions
## calc()
- useful for :
    - mixing units, e.g. calc(11vh - 30px + 3rem)
    - ability to nest calc( calc() - calc() )

## min() and max()
- e.g. width = min(3px, 100%). This make a div 3 px if its available, if theres less, it goes to 100% of its parent width
- e.g. width = max(100px, 4em, 50%). This will select the largest. 

## clamp()
- makes elements fluid and responsive. Takes 3 values
    1) smallest value
    2) ideal value
    3) largest value

# Custom properties
- AKA CSS variables
- scope of these are in the div its declared in and all child elements 
    - can declare variable in :root on all selectors
- @property can let you define if child elements inherit the custom variable from its parent
    ```
    @property --box-color {
        syntax: "<color>";
        initial-value: cornflowerblue;
        inherits: false;
    }
    ```
- double hypden following by name with hyphens. Declare this variable with var(--variable-name)
```
.error-modal {
  --color-error-text: red;
  --modal-border: 1px solid black;
  --modal-font-size: calc(2rem + 5vw);

  color: var(--color-error-text);
  border: var(--modal-border);
  font-size: var(--modal-font-size);
}
```

## Fallback values
- var() takes 2 arguments. 
    1) the custom property we want to assign, see above.
    2) the optional fallback value
    