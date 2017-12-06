# HTML

## General

The most important thing to keep in mind here is semantic markup, and clean organization of your code.

### Semantic Markup

Semantic markup is the use of specific HTML elements that are named for their intended function to separate content and functionality on your site. This is in contrast to what we call 'Div Soup,' where your layout is made up of divs, some with Classes, some with IDs, some not given any semantic info at all, which is not necessary and something we'll come to later.

A basic example of semantic markup:

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
            <ul class="nav__container">
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
