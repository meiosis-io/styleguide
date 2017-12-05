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

## Class and ID Declaration

Class and ID are not to be used interchangeably. Class declarations are to be used to declare a style that will be reused on multiple elements. ID declarations are to be used on distinct, single use elements. Do *NOT* use a class on a single use element. And let's face it, there's probably not a lot of single use elements on whatever site we're working on.
