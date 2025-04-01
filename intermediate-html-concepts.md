# Emmet
- a plugin to provide helpful shortcuts
- an example is the '!' to provide the html boilerplate
- 2 useful emmet abbreviations:
    1) wrap with abbreviation
        - can input an abbreviationa and it wraps itself into the element
        - shift command A
    2) remove tag:
        - removes a tag
        - command k
- Emmet can also create basic elements:
    - by typing in the actual element, e.g. 'div' or 'button' and pressing enter
    - can add attributes too with div.xyz (creates element with class xyz) or div#xyz (creates div with id xyz)
    - if you dont type an element, it assumes its a div
    - to add a child element: use a gradient >
        e.g. div.purple>span.cyan
    - to add sibling elements, use +
        e.g. header+main+span
    - if you want to climb out of a child space, use ^ or ()
        e.g. header>nav^main+footer or (header<nav)+footer+span (makes a header with child element nav, then mgoes back to header and makes siblings)
    - can create multiple elements of something by using *. and curly brackets for text
        e.g. header>nav>ul*3{badfhybdhyf}
        - if you want it to count up for different elements, use $
            e.g. header>nav>ul*3.class-${List Item $$}
    
# SVG
- common scalable image format on web
- defined using XML (Extensible markup language)
    - makes it human readable, unlike JPEG which would be binary
    - means you can put the code directly into html file and it should display an image. So you could target them with CSS and create the using element WebAPI youve been using already
- drawbacks:
    - inefficient at storing large detail complex images

## Anatomy of an SVG:
- xmlns
    - "XML Namespace". Specified what dialect of XML to use
- viewbox:
    - Defines bounds of SVG, also aspect ratio and origin
- class, id:
    - same as html attribute functions
- elements such as <circle>, <rect>, <path>, <text>
    - basic building blocks of SVG. Complete list online.
- many SVG attributes such as fill or stroke 
    - can be changed in CSS
## Embedding SVGs
- 2 approaches:
    1) linked
        - use html img tag, or link in CSS. Cant access the full detail of the SVG.
    2) inline
        - paste contents directly into code. Makes it harder to read. **Prefer to use this**


# Tables
- create using <table></table>
- smallest container in a table is <td>. "Table data"
- use <tr></tr> to make a row
- use <th></th> to make a bold header
- to make cells span across multiple rows or columns:
    - use "colspan" or "rowspan" attributes, e.g. <th colspan="2">Hippopotamus</th>
- use <caption></caption> within the table to make a caption for blind persons
- use <thead>, <tbody>, <tfoot> to mark up table with structure. They dont make anything visually different but they allow for CSS enhancements. 
    - thead is usually the first row containing the column headings.
    - tbody element wraps main part of table content that isnt header/footer
    - tfoot element wraps footer, usually the fnal row with items in previous rows summed.
- use "scope" arribute to tell screen readers what cells the header is a header for
    - e.g. <th scope="col">Purchase</th>
           <th scope="col">Location</th>
    - use scope="row" to identify a row
    - use scope="colgroup" or scope="rowgroup" for headings that sit over multiple columns or rows
- id and headers attributes:
    - alternative to using the scope attribute to create associations between headers and cells
    - headers takes a list of unordered, space-separated strings, each corresponding to unirque id of the <th> elements that provide elements for either a data cell or another header cell.
- to remove space between cells, style in css with border-collapse: collapse