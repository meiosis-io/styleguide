# CSS and SASS

Below is a collection of rules and preferred methods of writing CSS and SASS. This will be expanded upon as time goes on and use cases pop up.

## Naming

Semantic naming is the goal here. If there is not a semantic HTML element to use, make sure your naming of an element with a Class or ID relays information about what that element does in the site. Example, this:

HTML
```HTML
<form class="contact">
  <input class="contact__first">
</form>
```

Not this:

HTML
```HTML
<form class="form">
  <input class="input">
</form>
```

The Block-Element-Modifier (BEM) naming standard is to be used. Double underscores indicate child elements of a block. Example:

HTML
```HTML
<section>
  <form class="contact">
    <input class="contact__first">
  </form>
</section>
```

CSS
```CSS
.contact {
  //styles applied to the contact block
}

.contact__first {
  //styles applied to the first input
}
```

Double hyphens indicate element modifiers, I.E. an incomplete input. As above, keep it semantic:

CSS
```CSS
.contact__first--incomplete {
  border: 2px solid red;
}
```

The end result being semantic CSS that makes it easy to skim and discern what is being styled and why.

## Rule Declaration

When applying styles to multiple elements, each declared element is separated by a comma and placed on a new line. Example:

```CSS
.element,
.element-2,
.element-3 {
  //styles
}
```

## Media Queries

When doing media queries, from top to bottom, start with core styles, then work your way down in size from there. Example:

```CSS
.element {
  //core styles
}

@media (min-width: 1280px) {
  .element {
    //big styles
  }
}

@media (max-width: 1279px) {
  .element {
    //small styles
  }
}

@media (max-width: 770px) {
  .element {
    //even smaller styles
  }
}

@media (max-width: 480px) {
  .element {
    //smallest styles
  }
}
```

## Class and ID Declaration

Class and ID are not to be used interchangeably. Class declarations are to be used to declare a style that will be reused on multiple elements. ID declarations are to be used on distinct, single use elements. Do *NOT* use a class on a single use element. And let's face it, there's probably not a lot of single use elements on whatever site we're working on.

## SASS/SCSS

We use SASS/SCSS because we are civilized. More specifically, we use SCSS for reasons.

My preferred method of writing SCSS, and this is directed at you Zach, so you can correct me if you feel differently, is to write out SCSS in the same structure it is declared in HTML. This allows the DOM structure to be gleaned by looking at the SCSS so a basic understanding of layout can come together. There are limits to this, and ultimately it does not result in terribly beautiful compiled CSS, but I am also of the opinion that if you're writing SCSS to compile into minified CSS, maintainability of the SCSS is more important than readability of the resulting CSS.

### Media Queries

Media queries are to be declared on an element to element basis, within the CSS declaration of that element. Example, this:

```CSS
.element {
  //styles

  @media (min-width: 480px) {
    //smaller styles
  }
}
```

Not this:

```CSS
.element {
  //styles
}

@media (min-width: 480px) {
  .element {
    //smaller styles
  }
}
```

Note that it would be preferred to make media queries the same among various elements, so as not to add unnecessary bulk to the compiled CSS. Example, this:

```CSS
.element {
  //styles

  @media (min-width: 480px) {
    //smaller styles
  }
}

.element-2 {
  //styles

  @media (min-width: 480px) {
    //smaller styles
  }
}
```

Not this:

```CSS
.element {
  //styles

  @media (min-width: 480px) {
    //smaller styles
  }
}

.element-2 {
  //styles

  @media (min-width: 460px) {
    //smaller styles
  }
}
```

### Rule Declaration Order

To keep it semantic, legible and, most importantly, consistent, rule declarations are to be done in the order of Core, Altered State and Media Query. Example:

```CSS
.element {
  color: green;
  border: 1px solid black;

  &:hover,
  &:focus {
    color: purple;
    border: 1px dotted red;
  }

  @media (min-width: 480px) {
    font-size: 16px;
  }

  @media (max-width: 479px) {
    //even smaller styles
  }
}

```
