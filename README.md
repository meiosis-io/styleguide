# Mitosis Coding Styleguide

Contained within is a collection of style rules and suggestions for markup and code used on Mitosis and Meiosis projects, including HTML, CSS/SASS, JavaScript and its frameworks, PHP, et al, with the end goal being maintainability, readability and consistency of code between all Mitosis and Meiosis projects and among all developers working on various projects.

## Outline, Goals

At time of writing, little conceptualization has been done on this, so this section will serve as an outline of what we would like to include. This section and this paragraph will be revised as more is added. The first iterations of this project will outline general goals for each subsection, and as sections are added or removed, this README will be updated.

### General

TBD

### HTML

My primary interests in HTML, including HTML that shows up in Vue and PHP, are accessibility and cleanliness of layout. To that end, I'd like to place *some* emphasis on semantic, accessible markup as opposed to div soup. -K

### CSS/SASS

Don't have a hell of a lot in mind for this, but while I wouldn't mind throwing together a light framework for us to use and tweak over time, I *really* don't want to fall into that modern framework trap of having so many utility classes that one may as well be using inline style, i.e.

```HTML

<div class="col-sm-12 bg-red text-green tacos-delicious"></div>

```
so if we were to work on a framework, I think it would fall more into the realm of styleguide anyway. What I generally have in mind are, potentially project-to-project, a subset of utility classes and style that we lean on on a particular project. For example:

```CSS

//primary button used throughout site
.button-primary {
  //styles for one button to be used throughout the site, including hover and focus states, inside of this because we use scss because we're not savages, etc
}

```

Because I've never used a set styleguide or framework for any project, this may be common practice, and if so ignore all of this.


### JavaScript

TBD

### PHP

TBD
