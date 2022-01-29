# css-grid-intro

Materials for a little CSS Grid Training at Reaktor. Not a comprehensive tutorial, but more like a motivation piece.

## My first CSS Grid

The first time I decided to try a CSS Grid was when I was about to implement a layout roughly like this:

```
-------------------------
|    ORDER SUBMITTED    |
|                       |
|-----------------------|
|          |            |
|  SVG     |   Details  |
|          |   More     |
|          |   Details  |
|          |   Stuff    |
|          |   ...      |
|          |            |
-------------------------

```

Goes without saying that one doesn't want to specify the exact pixel widths for all the areas but instead say
something like "Put the header on top, centered and then divide the rest of the area half-by-half for the 
illustration and a section containing order details".

It's not like it's hard to implement a layout like this using, for instance, Flexbox, but, I had just read a 
nice tutorial (not sure which one it was but [here's](https://www.codeinwp.com/blog/css-grid-tutorial-layout/) one) and
I wanted to try it out.

It's not like it's hard to implement a layout like this using, Flexbox, which is a one-dimensional layout, 
meaning that you cannot organize your stuff on a grid directly. You can of course implement the given layout by 
introducing a `<div>` for the content part and divide it equally between the `<svg>` and the details part, as in this [pen](https://codepen.io/raimohanska/pen/VwrvPoE).

With Grid, you don't need any intermediate divs, but can layout the elements directly on a grid, like [here](https://codepen.io/raimohanska/pen/PoOPpzY).

One cool thing about grid is that you can define you grid laoyut using sort of "ascii graphics", as in the example:

```css
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-template-areas:
    "header header"
    "image content";
  column-gap: 64px;
  row-gap: 32px;
```

Then in the components you're placing on the grid, you define which areas of the grid they will be laid out:

```css
header {
  grid-area: header;
}
```

## My second CSS Grid

Admittedly, the first example is equally easy to implement with Flexbox. In a secong example, the grid turns out to be a
really useful tool though. Here's a formish thing to lay out.

```
--------------------------------
| PATIENT INFORMATION          |
|------------------------------|
| FIRST_NAME    | LAST_NAME    |
| DATE_OF_BIRTH | SEX          |
--------------------------------
```

The form components are laid out in two rows and we want to align them in a neat grid. Once again, we don't want to specify exact pixel widths for each component, but instead have a responsive UI.

This is a perfect case for CSS Grid. [Here](https://codepen.io/raimohanska/pen/dyZYvzr)'s how.
```
