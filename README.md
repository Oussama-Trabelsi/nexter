# Nexter: A CSS Grid layout Project

This project was built following the [Jonas Schmedtmann's Advanced CSS and Sass course.](https://www.udemy.com/advanced-css-and-sass/ 'Udemy | Advanced CSS and Sass: Flexbox, Grid, Animations and More!') The main goal of this project was to create a responsive landing page using **CSS Grid layout**, following the BEM methodology for organizing and naming CSS classes.

View project live at [oussama-tr.github.io/nexter](https://oussama-tr.github.io/nexter/).

## Instructions

Clone or download project and then run:

```
npm install
npm start
```

_Notice: The project is set to open on `localhost:8080` in your default browser. You can change any of these settings in `package.json` under `devserver` property. If you wish to change the browser on which to run the project by default you can add the --browser flag. [See more live-server config options here.](https://github.com/tapio/live-server#usage-from-command-line)_

## Table of Contents

- [Grid Layout](#grid-layout)
- [Responsive Design](#responsive-design)
- [NPM Scripts](#npm-scripts)

## Grid Layout

CSS Grid Layout is the a powerful layout system available with CSS. It is two dimensional, allowing to handle both rows and columns simultaneously - which is not possible with Flexbox. In this manner, CSS Grid is similar to a table, but offers many more layout possibilities and even supports nesting grids.

```scss
.gallery {
  display: grid;
  grid-template-columns: repeat(8, 1fr);
  grid-template-rows: repeat(7, 5vw);

  &__item {
    &--1 {
      grid-row: 1 / span 2;
      grid-column: 1 / span 2;
    }

    &--2 {
      grid-row: 1 / span 3;
      grid-column: 3 / span 3;
    }
  }
}
```

We can see how powerful the CSS Grid is in the Gallery section example. It would be very hard to achieve this exact layout without the use of some JavaScript or libraries like [Masonry](https://masonry.desandro.com/). We can also see the `grid-gap` property in action, which makes the use of margin on child elements obsolete. However powerful the CSS Grid might be, there is always room for improvement. It would be nice if more browsers besides Firefox would adopt [`subgrid`](https://caniuse.com/?search=subgrid 'Can I use subgrid?') value, as well as if we could set different row and column gaps, or have `nth` selector for rows and columns. One more thing would be enabling transitions when `grid-column` or `grid-row` values change. I hope that we will see these enhancements in the near future.

![Grid: Gallery section](img/readme/gallery.png 'Grid: Gallery section')

If you want to learn more about CSS Grid and how to incorporate these techniques in your own projects check out this awesome article on [CSS Tricks website](https://css-tricks.com/snippets/css/complete-guide-grid/ 'A Complete Guide to Grid') and visit official documentation on [MND web docs](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout 'CSS Grid Layout').

CSS Grid is supported in all major browsers except IE 9 and lower. _[See browser support for grid.](https://caniuse.com/?search=grid 'Can I use grid?')_

_PS: It's a good practice to name columns and keep in mind that you cannot use -1 on implicit grids :wink:_

## Responsive Design

This project uses **Desktop First** strategy. This means that we first write CSS for desktop screens and then use media queries (`@media`) to adapt CSS for smaller tablet and mobile screens. Also, we are not using some specific breakpoints, e.g. like Bootstrap does (`576px, 768px, 992px, 1200px`), but instead we add media queries when design starts to break. _This approach is not recommended for bigger projects._

CSS Grid, like Flexbox, allows us to very easily make changes in a website layout. Even more so because we do not need to have additional container elements - we just have to add a new row or column and specify the area an element should occupy, _e.g._ sidebar navigation section. Besides this, CSS Grid has some lovely features which enable us to have responsive card layout without the use of media queries, _e.g._ features, real estates or footer section.

```scss
.features {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(25rem, 1fr));
}
```



|           Desktop Screens           | 
| :---------------------------------: | 
| ![](img/readme/desktop-screens.png) | 

<div align="center">

|           Tablet Screens            |          Mobile Screens                   |
| :---------------------------------: | :---------------------------------------: |
| [img/readme/tablet-screens.png](https://github.com/oussama-tr/nexter/blob/master/img/readme/tablet-screens.png)  | [img/readme/mobile-screens.png](https://github.com/oussama-tr/nexter/blob/master/img/readme/mobile-screens.png)  |

</div>


## NPM Scripts

Besides aforementioned `start` script - which runs live-server and watches for .scss file changes to recompile in parallel, we also have a `build:css` script which performs the following actions:

1. Compiles SASS (SCSS)
2. Uses PostCSS Autoprefixer feature to apply prefixes for better browser support
3. Compresses (minifies) CSS
