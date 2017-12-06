# HTML

## General

Clean, organized, semantic and accessible markup. This is the goal.

### Cleanliness

Tags that do not *need* Class or ID identifiers do not get them. This:

```HTML
<body>
    <header>
        <nav>
        </nav>
    </header>
    <main>
        <section>
            <article>
            </article>
        </section>
        <section>
        </section>
    </main>
    <footer>
    </footer>
</body>
```

Not this:

```HTML
<body class="site-body">
    <header class="top-section">
        <nav id="nav">
        </nav>
    </header>
    <main class="body">
        <section>
            <article>
            </article>
        </section>
        <section>
        </section>
    </main>
    <footer>
    </footer>
</body>
```

for so many reasons. These class names are not semantic, in a couple situations they are declaring what should already be inferred by the element name, and in the case of `<main class="body">...</main>`, it is contradicting the function of that element.

Blocks should be reduced to the fewest necessary containing elements. Example, this:

```HTML
<nav>
    <ul>
        <li>
            <a href="#"></a>
        </li>
        <li>
            <a href="#"></a>
        </li>
        <li>
            <a href="#"></a>
        </li>
    </ul>
</nav>

Not this:

```HTML
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
```

### Organzation

We'll discuss semantic markup below, which will help with organization of your markup, but we have a few guidelines here.

#### Indentation
1. Spaces, not tabs, for indentation. If you are comfortable with tabs, configure your editor to convert tabs to spaces.
2. Double indentation. Not entirely necessary, but encouraged for the sake of clarity.

#### Markup layout
Markup should be written such that it would make sense if viewed without any styling applied. Example, which will return later:

```HTML
<body>
    <header>
        <nav>
        </nav>
    </header>
    <main>
        <section>
            <article>
            </article>
        </section>
        <section>
        </section>
    </main>
    <footer>
    </footer>
</body>
```

### Semantic Markup

Semantic markup is the use of specific HTML elements that are named for their intended function to separate content and functionality on your site. This is in contrast to what we call 'Div Soup,' where your layout is made up of divs, some with Classes, some with IDs, some not given any semantic info at all, which is not necessary and something we'll come to later.

A basic example of semantic markup, using the block from above:

```HTML
<body>
    <header>
        <nav>
        </nav>
    </header>
    <main>
        <section>
            <article>
            </article>
        </section>
        <section>
        </section>
    </main>
    <footer>
    </footer>
</body>
```

This does not include everything that could or would be on a site, and we will discuss the use of semantic elements later, but this is a general layout to give an example of semantic markup. Note that you can infer what will be in each tag based on the tag itself; the header tag indicates the site header, and (not exclusively) contained within is the navigation, the main section contains two sections, one of which contains an article, the footer tag is at the bottom. These are not the only semantic elements, and to that end we suggest referring to the [Mozilla Developer Network HTML Element Guide](https://developer.mozilla.org/en-US/docs/Web/HTML/Element), but as stated above, this is simply an example layout.

Note that semantic elements do not ALWAYS have to be used; sometimes it's not appropriate to wrap something in a `<section></section>` or `<article></article>`, and sometimes it's necessary or encouraged to place content inside of a `<div></div>` instead, which is perfectly fine. Semantic elements are primarily intended to layout the blocking of a site. Example:

```HTML
<body>
    <header>
        <div id="header__logo">
            <img src="#" alt="A giant beaver eating a maple and mayonnaise sandwich">
        </div>
        <nav>
            <ul>
                <li class="nav__link">
                    <a href="#"></a>
                </li>
                <li class="nav__link">
                    <a href="#"></a>
                </li>
                <li class="nav__link">
                    <a href="#"></a>
                </li>
            </ul>
        </nav>
    </header>
    <main>
        <section class="main-content">
            <article>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
            </article>
        </section>
        <section class="sidebar">
            <div class="sidebar__child">

            </div>
        </section>
    </main>
    <footer>
        <div id="footer__logo">
            <img src="#" alt="A smaller version of a giant beaver eating a maple and mayonnaise sandwich">
        </div>
    </footer>
</body>
```

You'll note that in certain places, a div was the appropriate tag to use provided that, if it is serving a functional or semantic purpose, it is given a semantic Class or ID. We will discuss the semantic naming system in the CSS section.

### Accessibility

It's really easy not to care about this, but I encourage you to put the effort forth. The primary things to keep in mind with accessibility are, as stated above, semantic markup, and additionally the use of alt text and other related tags to be used with screen readers. I don't think an example is necessary, but there are two main rules to keep in mind.

1. If an image or video is serving a purpose or contributing content to a page, it MUST have a completed, descriptive alt tag.

2. If an image or video is purely cosmetic, such as adding some texture to a site or a video background, an alt tag is unnecessary.
