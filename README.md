Five-Q-CSS-Guidelines
=====================

Guidelines containing best practices and how we build and lay out our CSS at Five Q.


## Syntax & Formatting

At a very high-level, we want:
* four (4) space indents, no tabs
* 80 character wide columns
* multi-line CSS
* meaningful use of whitespace
* contextual comments

## Table of Contents

A table of contents is a fairly substantial maintenance overhead, but the benefits it brings far outweigh any costs. It takes a diligent developer to keep a table of contents up to date, but it is well worth sticking with. An up-to-date table of contents provides a team with a single, canonical catalogue of what is in a CSS project, what it does, and in what order.

A simple table of contents will—in order, naturally—simply provide the name of the section and a brief summary of what it is and does, for example:

```css
/**
 * CONTENTS
 *
 * SETTINGS
 * Global...............Globally-available variables and config.
 *
 * TOOLS
 * Mixins...............Useful mixins.
 *
 * GENERIC
 * Normalize.css........A level playing field.
 * Box-sizing...........Better default `box-sizing`.
 *
 * BASE
 * Headings.............H1–H6 styles.
 *
 * OBJECTS
 * Wrappers.............Wrapping and constraining elements.
 *
 * COMPONENTS
 * Page-head............The main page header.
 * Page-foot............The main page footer.
 * Buttons..............Button elements.
 *
 * TRUMPS
 * Text.................Text helpers.
 */
```

Each item maps to a section and/or include.

Naturally, this section would be substantially larger on the majority of projects, but hopefully we can see how this section—in the master stylesheet—provides developers with a project-wide view of what is being used where, and why.


## 80 Characters Wide

Where possible, limit CSS files' width to 80 characters. Reasons for this include:
* the ability to have multiple files open side by side
* viewing CSS on sites like GitHub, or in terminal windows
* providing a comfortable line length for comments

```css
/**
 * I am a long-form comment. I describe, in detail, the CSS that follows. I am
 * such a long comment that I easily break the 80 character limit, so I am
 * broken across several lines.
 */
```
There will be unavoidable exceptions to this rule—such as URLs, or gradient syntax—which shouldn't be worried about.


## Titling

Begin every new major section of a CSS project with a title:
```css
/*------------------------------------*\
    #SECTION-TITLE
\*------------------------------------*/

.selector {}
```

The title of the section is prefixed with a hash (#) symbol to allow us to perform more targeted searches (e.g. grep, etc.): instead of searching for just SECTION-TITLE—which may yield many results—a more scoped search of #SECTION-TITLE should return only the section in question.

Leave a carriage return between this title and the next line of code (be that a comment, some Sass, or some CSS).

If you are working on a project where each section is its own file, this title should appear at the top of each one. If you are working on a project with multiple sections per file, each title should be preceded by five (5) carriage returns. This extra whitespace coupled with a title makes new sections much easier to spot when scrolling through large files:
```css
/*------------------------------------*\
    #A-SECTION
\*------------------------------------*/

.selector {}





/*------------------------------------*\
    #ANOTHER-SECTION
\*------------------------------------*/

/**
 * Comment
 */

.another-selector {}
```


## Anatomy of a Ruleset

Before we discuss how we write out our rulesets, let’s first familiarise ourselves with the relevant terminology:
```css
[selector] {
    [property]: [value];
    [<--declaration--->]
}
```

For example:
```css
.foo, .foo--bar,
.baz {
    display: block;
    background-color: green;
    color: red;
}
```

Here you can see we have

* related selectors on the same line; unrelated selectors on new lines
* a space before our opening brace ({)
* properties and values on the same line
* a space after our property–value delimiting colon (:)
* each declaration on its own new line
* the opening brace ({) on the same line as our last selector
* our first declaration on a new line after our opening brace ({)
* our closing brace (}) on its own new line
* each declaration indented by four (4) spaces
* a trailing semi-colon (;) on our last declaration
* This format seems to be the largely universal standard (except for variations in number of spaces, with a lot of developers preferring two (2))

As such, the following would be incorrect:
```css
foo, .foo--bar, .baz
{
	display:block;
	background-color:green;
	color:red }
```

Problems here include

* tabs instead of spaces
* unrelated selectors on the same line
* the opening brace ({) on its own line
* the closing brace (}) does not sit on its own line
* the trailing (and, admittedly, optional) semi-colon (;) is missing
* no spaces after colons (:)
