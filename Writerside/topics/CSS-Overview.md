# CSS (Cascading Style Sheets) Overview

CSS, short for Cascading Style Sheets, is a stylesheet language used to describe the presentation of a document written
in HTML or XML. CSS describes how elements should be rendered on screen, on paper, in speech, or on other media.

## What is CSS? {collapsible="true" default-state="expanded"}

- **Style Control**: CSS is used to define styles for your web pages, including the design, layout, and variations in
  display for different devices and screen sizes.
- **Separation of Concerns**: CSS helps in keeping the content separate from the design, which makes site maintenance
  easier.

## Basic Syntax {collapsible="true" default-state="expanded"}

CSS is made up of selectors and declarations:

```css
selector {
  property: value;
}
```

- **Selectors**: Specify the HTML element to be styled.
- **Declarations**: Consist of a property and a value separated by a colon.

## Types of CSS {collapsible="true" default-state="expanded"}

- **Inline CSS**: Style is applied directly on an HTML element.
- **Internal CSS**: Style is defined within the `<style>` element in the head section of an HTML page.
- **External CSS**: Style is defined in a separate `.css` file.

## Common Properties {collapsible="true" default-state="expanded"}

- **Text Styles**: `font-family`, `font-size`, `color`, `text-align`.
- **Layouts**: `margin`, `padding`, `border`, `width`, `height`.
- **Positioning**: `position`, `top`, `bottom`, `left`, `right`.

## Box Model {collapsible="true" default-state="expanded"}

- Every element in a web page is a box. The CSS box model describes this principle with the following properties:
    - **Content**: The actual content of the box, where text and images appear.
    - **Padding**: Clears an area around the content.
    - **Border**: A border that goes around the padding and content.
    - **Margin**: Clears an area outside the border.

## Responsive Design {collapsible="true" default-state="expanded"}

- **Media Queries**: Allow the application of CSS styles depending on media type, screen resolution, and other factors.
- **Flexbox**: A layout model that allows responsive elements within a container to be automatically arranged depending
  upon screen size.
- **Grid**: CSS Grid Layout is a two-dimensional grid-based layout system that offers a new way of thinking about layout
  in CSS.

## Preprocessors {collapsible="true" default-state="expanded"}

- **Sass**, **LESS**, and **Stylus** are popular CSS preprocessors that allow you to use variables, nested rules,
  mixins, functions, and more in CSS.

## Conclusion {collapsible="true" default-state="expanded"}

CSS is essential for web design. It allows for much greater control over the appearance of a website, letting web
designers create attractive, consistently styled web pages.

This overview covers the basics of CSS, including its purpose, syntax, common properties, the box model, responsive
design, and preprocessors. This format is useful for understanding the key concepts and applications of CSS in web
development.

## Glossary {collapsible="true"}

A definition list or a glossary:

First Term
: This is the definition of the first term.

Second Term
: This is the definition of the second term.
