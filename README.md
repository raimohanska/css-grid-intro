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

## Tables

I'd very much like to style my `<table>`s with Grid as well. 

To start with, [here](https://codepen.io/raimohanska/pen/xxPwrEg) is an example of a table, with some column width tuning- the center column is to take up all the remaining space. This can be implemented with `width: 100%`, which feels a bit wrong. Certainly there's no 100% to be given to the column when the other columns need some with as well.

I can style a table with CSS Grid like [this](https://codepen.io/raimohanska/pen/zYPvzdo). Now, because a semantically correct `<table>` is not a flat collection of cells (they are nested within `<tbody>` and `<tr>`), the Grid doesn't apply well by default. However, this can be fixed by applying the `display: contents` style on the intermediary elements, so that the `<td>`s and `<th>`s will be laid out on the grid. Nice! And with grid, I get far superior control over column widths, as I can use the `fr` unit among other units here.

Alas, there's a drawback I don't know how to fix yet: the nice _row hover_ feature in the first example gets broken, as it doesn't seem to play ball with `display: contents`. Therefore, at least for now, I'm back with normal table layout in cases where there is anything I want to do on the row level.
