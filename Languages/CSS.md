# CSS and SCSS

## Introduction

This section deals with our guidelines and rules for writing CSS and SCSS. This section will be broken into two parts, the first being general CSS rules, the second being focused on SCSS best practices. To keep things DRY in this section, we will primarily be referring back to this example, which is related to the example provided in the HTML section:

```CSS
nav {
    ...
}

nav ul {
    ...
}

.nav__link {
    ...
}
```

**Semantics** are of less concern in CSS because styles do not directly affect the structure of the site or its functionality, but they are still of concern, as are **cleanliness** and **brevity**, all of which will be addressed in order below, after some general rules.

# CSS

## General

### Indentation

As with HTML, double indentation here. 4 spaces, 2 tabs, whatever.

### Media Queries

When styling anything based on viewport width, start with core styles and then work your way down in size from the core styles.

```CSS
nav {
    //core styles
    ...
}

@media (min-width: 1280px) {
    nav {
        //full size styles
    }
}

@media (max-width: 1279px) {
    nav {
        //slightly smaller styles
    }
}

@media (max-width: 960px) {
    nav {
        //small styles
    }
}

@media (max-width: 720px) {
    nav {
        //smaller styles
    }
}

@media (max-width: 480px) {
    nav {
        //smallest styles
    }
}
```

When working in pure CSS, media queries are done in groups at the bottom of your CSS file, above which all core declarations go.

## Semantics

Semantics with regard to CSS refer primarily to the system used to name elements that are not semantic on their own. As stated in the HTML section, we use the Block-Element-Modifier (BEM) naming convention. Briefly, a group of code dealing with one function or section is grouped into a Block, children of which are Elements, which **MAY** have modifier classes available to them. Consider the given example from the HTML section:

```HTML
<nav>
    <ul>
        <li class="nav__link">...</li>
        <li class="nav__link">...</li>
        <li class="nav__link">...</li>
        ...
    </ul>
</nav>
```

In this instance, the `<nav>...</nav>` element is the Block, the `<li class="nav__link">...</li>` are the Elements, because the `<ul>...</ul>` is serving primarily as a container for the `<li class="nav__link">...</li>` elements and does not *necessitate* its own specific identifier in the BEM convention. Note that elements are indicated as part of a block by a double underscore.

Modifiers indicate styles that are applied to an element as a result of user interaction, usually by way of JavaScript, indicated by double hyphens.

```CSS
.nav__link--current {
    ...
}
```

The intended result of this naming system is that all Class and ID declarations are *necessary* and *semantic*. It encourages the developer to ensure their Class and IDs serve a purpose that is related to their function, and to think about their elements less as individual elements and more as pieces contributing to the function of a whole.

### Buttons

Touching on, briefly, the button discussion from the HTML section. In short, follow the design guidelines. You are more than welcome to style both `<button>` and `<a>` elements exactly the same, as long as their presence on any given page is based on intended functionality, as discussed in the HTML section. When styling buttons (in the broad sense of buttons), you must include focus and active styles to aid in accessibility.

To be clear, one need not style *all* `<a>` elements to behave as buttons. The recommendation here is to indicate all `<a>` elements that are intended to function as buttons with a class, e.g. `<a href="..." class="button">...</a>` or `<a href="..." class="btn">...</a>`, optionally with additional classes indicating the *type* of button the link will be. Either `.button` or `.btn` or whatever other indicator class you want is fine as long as there is adequate documentation.

## Organization

Lay your CSS out in an arrangement that follows your HTML markup. This ensures ease of jumping between HTML and CSS, and even further allows a dev to glean from your CSS the basic layout and look of your site without looking at the HTML or even the rendered site itself.

```CSS
body {
    ...
}

header {
    ...
}

main {
    ...
}

footer {
    ...
}
```

## Brevity

Basically, do not write any code that does not need to be written. As much as possible, limit your declarations to the shorthand versions:

```CSS
.nav__link {
    margin: 15px 20px 25px 30px; //top, right, bottom, left OR
    margin: 15px 20px; //top and bottom, left and right OR
    margin: 15px; //all sides together
}
```

The first time you declare a rule, comment it to indicate *what* is being styled and why.

# SCSS

## Introduction

Below is a collection of SCSS specific rules and guidelines.

## General

### Nesting

In keeping with the goal of organizing your CSS in a similar format to your markup, nest your SCSS declarations in a similar way.

```SCSS
body {
    ...

    header {
        ...

        nav {
            ...
        }
    }

    main {
        ...

        section {
            ...
        }

        aside {
            ...
        }
    }

    footer {
        ...
    }
}
```

Declaring `body {...}` is not entirely necessary but, depending on the structure of your site, it might help to have a container on a per-page basis that wraps everything on the page; in this instance, body is what we're using.

### Partials

Given the practicality of partials, you are encouraged to use as many as you see fit, provided they are organized in a tidy and semantic way. An example would be having a separate partial for each individual page of a site, a separate partial for each static element (e.g. navigation, header, footer), a separate partial containing variables (e.g. brand style guides, etc), a separate partial containing a group of related styles (e.g. button styles)

Variables, separate pages and reusable styles are encouraged to be in their own partials.

### Media Queries

Media queries are to be done on a per-element basis, for simplicity of editing.

```SCSS
nav {
    ...

    @media (min-width: 1280px) {
        ...
    }

    @media (max-width: 1279px) {
        ...
    }

    @media (max-width: 960px) {
        ...
    }

    ...
}
```
