# HTML

## Introduction

In this section we will be discussing HTML guidelines and rules to be used in all projects. Throughout this section, to avoid repeating the same code over and over (keep it DRY), we will be contrasting the don'ts with this example:

```HTML
<body>
    <header>
        <nav>
            <ul>
                <li>
                    <a href="#"></a>
                </li>
            </ul>
            <ul>
                <li>
                    <a href="#"></a>
                </li>
            </ul>
            <ul>
                <li>
                    <a href="#"></a>
                </li>
            </ul>
        </nav>
    </header>
    <main>
        <section>
            <article>
                <p></p>
            </article>
        </section>
        <aside>
            <div>
            </div>
        </aside>
    </main>
    <footer>
    </footer>
</body>
```

All examples that follow will be an example of what **NOT** to do in contrast to the block above. There are multiple lessons to take away from the block of markup above, which from a high level we will call **Cleanliness**, **Semantic Markup** and **Accessibility**, which we will address in order.

## Cleanliness

Maintainability is of primary concern here. If a developer looks at your markup and cannot easily glean the structure of your site, you're doing something wrong.

### Concise Markup

Blocks of markup **MUST** be reduced to the fewest number of elements. **NOT** this:

```HTML
<body>
    <header>
        <nav>
            <div>
                <ul>
                    <li>
                        <span>
                            <a href="#"><span></span></a>
                        </span>
                    </li>
                    <li>
                        <span>
                            <a href="#"><span></span></a>
                        </span>
                    </li>
                    <li>
                        <span>
                            <a href="#"><span></span></a>
                        </span>
                    </li>
                </ul>
            </div>
        </nav>
    </header>
    <main>
        <section>
            <article>
                <div>
                    <span></span>
                </div>
            </article>
        </section>
        <aside>
            <div>
                <div>
                    <p></p>
                </div>
            </div>
        </aside>
    </main>
    <footer>
    </footer>
</body>
```

The primary function of this rule is to encourage legibility of markup *without* having to look at the rendered site. Further, the additional elements and expanded blocks serve no semantic purpose and, provided concise and appropriate use of CSS, serve no styling purpose as well. This is an extreme example, intended only to illustrate the point.

### Identifiers

Tags that do not necessitate a Class or ID **MUST** not have them. **NOT** this:

```HTML
<body class="site-body">
    <header class="top-section">
        <nav id="nav">
            ...
        </nav>
    </header>
    <main class="body">
        <section>
            <article>
                ...
            </article>
        </section>
        <aside>
        </aside>
    </main>
    <footer>
    </footer>
</body>
```

These class names are not semantic, in a couple situations they are declaring what should already be inferred by the element name, and in the case of `<main class="body">...</main>`, it is contradicting the function of that element.

## Semantic Markup

The next thing to take away from the top example is the use of semantic HTML elements. This is the primary support for both *clean* and *accessible* markup, and works strongly in service to both of those goals. In terms of cleanliness, they reduce the call for Class and ID declarations, and in terms of accessibility, they clearly mark the function of each section of a site.

### Semantic Elements

There is not a semantic HTML element for every situation, but their primary function is to provide the basic layout of a site. To that end, we suggest referring to the [Mozilla Developer Network HTML Element Guide](https://developer.mozilla.org/en-US/docs/Web/HTML/Element) and gaining a knowledge of the available semantic HTML elements and an understanding of when to use them.

That said, there frequently *are* situations in which there is no semantic HTML element, and a `<div>...</div>` or `<span>...</span>` is the appropriate element to use. The main things to keep in mind here are the cleanliness we discussed above. Do not apply a Class or ID if it is not necessary, and ensure your markup as concise as possible, not adding elements if they are not necessary.

If a Class or ID is necessary, ensure that the identifier it is given is semantic, in that it details the function of that element.

#### Semantic Naming

We will discuss our naming convention in more detail in the CSS section, but as an outline, we use the Block-Element-Modifier (BEM) naming convention, primarily because it effectively ensures semantic markup and style identification. In this style, the top level of a block of markup is given a Class or ID, and children of that top level are given names relating to the block, separated by two underscores. Assume at the top level of a block you have a `<nav>...</nav>` element and an unordered list providing the navigation elements. An example of semantic BEM naming, in this case, would be thus:

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

In this instance, the Block part of BEM is the `<nav>...</nav>` element, and the Element parts of BEM are the `<li class="nav__link">...</li>` elements. Because the `<ul>...</ul>` functions essentially as just a container for the nav links, it does not *necessitate* a Class or ID on its own. The Modifier part of BEM will be discussed in more detail in the CSS section.

## Accessibility

If you follow the guides above, half of the work in terms of accessibility is done for you. Semantic HTML elements help screen readers discern the layout of your site and what is most important, and keeping your markup and code concise helps facilitate expeditious delivery of your site to people who may not have the most robust internet connection. Another to keep in mind are `alt` tags on images and videos. With regard to `alt` tags, there are really just two rules:

1. If an image or video is serving a purpose or contributing content to a page, it **MUST** have a completed, descriptive alt tag.

2. If an image or video is purely cosmetic, such as adding some texture to a site or a video background, you **MUST** omit an alt tag entirely, and in addition, you **MUST** include the `aria-hidden="true"` attribute.

Further, each element or section that is purely cosmetic or functional, providing no information, you **MUST** include the `aria-hidden="true"` attribute. In addition, for each element or section that *does* provide information or content, a `role` attribute **MUST** be supplied to assist in navigation and accessibility for screen readers. Consult [Mozilla Developer Network's 'Using Aria' Guide](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques) to reference the difference between aria landmarks, widgets, composite and document structure roles, all of which should be utilized where necessary and applicable.

### Buttons

Special attention must be given to the creation and styling of buttons. This section will be brief; the more intricate description of button styling will be relegated to the CSS section. Of primary concern, here, is the choice between a `<button>...</button>` element, or an `<a>...</a>` element. As many developers simply reach for these interchangeably, or neglect both in preference of using a `<div>...</div>` or `<span>...</span>`, this topic must at least be discussed. Any element designed as a button **MUST** be either a `<button>...</button>` element, or an `<a>...</a>` element, **NOT** any other element, regardless of their intended function.

When choosing between a `<button>...</button>` element, or an `<a>...</a>` element, one must consider the intended function. A button that transports the user to another page **MUST** be an `<a>` element. A button that is intended as a point of user interaction, such as changing content on a page or triggering a script or form submission **MUST** be a `<button>` element. This is entirely independent of styling; from a purely markup based perspective, this is the most accessible option as screen readers can easily differentiate between function for users.
