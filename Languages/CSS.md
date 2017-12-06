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

Declaring `.body {...}` is not entirely necessary but, depending on the structure of your site, it might help to apply a class on `<body>...</body>` to indicate, for instance, which page or section of the site to which the `.body {...}` is referring. This helps ensure specificity when declaring styles and helps keep your code organized.

### Partials

Use as many partials as desired, as long as they are all appropriate in terms of organization and they are all imported into the master SCSS file.

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
