# Introduction

This article contains a general introduction to the popular markup language Markdown, as well as the formatting requirements of Open Journals and the Journal of Open Source Software (JOSS). 

## Markdown summary

Markdown is a lightweight markup language used frequently in software development and online environments. Based on email conventions, it was developed in 2004 by John Gruber and Aaron Swartz. 

# Markdown primer

This section explains basic Markdown syntax. If you are already familiar with Markdown, the JOSS formatting requirements can be found [here].

## Inline markup

The markup in Markdown should be semantic, not presentations. The table below has some basic examples.

+---------------------+-------------------------+-----------------------+
| Markup              | Markdown example        | Rendered output       |
+:====================+:=======================:+:=====================:+
| emphasis            | `*this*`                | *this*                |
+---------------------+-------------------------+-----------------------+
| strong emphasis     | `**that**`              | **that**              |
+---------------------+-------------------------+-----------------------+
| strikeout           | `~~not this~~`          | ~~not this~~          |
+---------------------+-------------------------+-----------------------+
| subscript           | `H~2~O`                 | H~2~O                 |
+---------------------+-------------------------+-----------------------+
| superscript         | `Ca^2+^`                | Ca^2+^                |
+---------------------+-------------------------+-----------------------+
| underline           | `[underline]{.ul}`      | [underline]{.ul}      |
+---------------------+-------------------------+-----------------------+
| small caps          | `[Small Caps]{.sc}`     | [Small Caps]{.sc}     |
+---------------------+-------------------------+-----------------------+
| inline code         | `` `return 23` ``       | `return 23`           |
+---------------------+-------------------------+-----------------------+

: Basic inline markup and examples.

### Links

Link syntax is `[link description](targetURL)`. E.g., this link to the
[Journal of Open Source Software](https://joss.theoj.org/) is written as \
`[Journal of Open Source Software](https://joss.theoj.org/)`.

Open Journal publications are not limited by the constraints of print
publications. We encourage authors to use hyperlinks for websites and
other external resources. However, the standard scientific practice of
citing the relevant publications should be followed regardless.

### Images

Markdown syntax for an image is that of a link, preceded by an
exclamation mark `!`.

The main use of images in papers is within figures. An image is treated
as a figure if

1. it has a non-empty description, which will be used as the figure
   label and
2. it is the only element in a paragraph, i.e., it must be surrounded by
   blank lines.
   
Example:

```markdown
![Figure caption](path/to/image.png)
```

Images that are larger than the text area are scaled to fit the page. It
can sometimes be useful to give images an explicit height and/or width,
e.g. when adding an image as part of a paragraph. The Markdown `![Nyan
cat](nyan-cat.png){height="9pt"}` includes the image "nyan-cat.png"
![Nyan cat](nyan-cat.png){height="9pt"} while scaling it to a height of
9 pt.


![The "Mandrill" standard test image, sometimes erroneously called
"Baboon", is a popular sample photo and used in image processing
research.](mandrill.jpg){#fig:mandrill}

### Citations

Bibliographic data should be collected in a file `paper.bib`; it
should be formatted in the BibLaTeX format, although plain BibTeX
is acceptable as well. All major citation managers offer to export
these formats.

Cite a bibliography entry by referencing its identifier:
`[@upper1974]` will create the reference "[@upper1974]". Omit the
brackets when referring to the author as part of a sentence: "For
a case study on writers block, see @upper1974." Please refer to
the [pandoc manual](https://pandoc.org/MANUAL#extension-citations)
for additional features, including page locators, prefixes,
suffixes, and suppression of author names in citations.

### Mathematical Formulæ

Mark equations and other math content with dollar signs (`$`). 
Use a single dollar sign (`$`) for math that will appear directly within the text. Use two dollar signs (`$$`) when the formula is to be presented centered and on a separate line, in "display" style. The formula itself must be given using TeX syntax.

To give some examples: When discussing a variable $x$ or a short formula
like $\sin \frac{\pi}{2}$, we would write `$x$` and `$\sin
\frac{\pi}{2}$`, respectively. However, for more complex formulæ,
display style is more appropriate. Writing `$$\int_{-\infty}^{+\infty}
e^{-x^2} \, dx = \sqrt{\pi}$$` will give us

$$\int_{-\infty}^{+\infty} e^{-x^2} \, dx = \sqrt{\pi}$$

Numbered equations and internal cross-references are discussed
[further below][Equations].

### Footnotes

Syntax for footnotes centers around the "caret" character `^`. The
symbol is also used as a delimiter for superscript text and thereby
mirrors the superscript numbers used to mark a footnote in the final
text.[^markers]

``` markdown
Articles are published under a Creative Commons license[^1].
Software should use an OSI-approved license.

[^1]: An open license that allows reuse.
```

The above example results in the following output:

> Articles are published under a Creative Commons license[^1].
> Software should use an OSI-approved license.
>
> [^1]: An open license that allows reuse.

Note: numbers do not have to be sequential, they will be reordered
automatically in the publishing step. In fact, the identifier of a note
can be any sequence of characters, like `[^marker]`, but may not contain
whitespace characters.

[^markers]: it should be noted that some publishers prefer
    symbols or letters as footnote markers.

## Blocks

The larger components of a document are called "blocks".

### Headings

Headings are added with `#` followed by a space, where each additional
`#` demotes the heading to a level lower in the hierarchy:

```markdown
# Section

## Subsection

### Subsubsection
```

Please start headings on the first level. The maximum supported level is
5, but paper authors are encouraged to limit themselves to headings
of the first two or three levels.

#### Deeper nesting

Fourth- and fifth-level subsections – like this one and the following
heading – are supported by the system; however, their use is
discouraged.

##### Avoiding excessive nesting

Usually [lists], as described in the next section, should be preferred
over forth- and fifth-level headings.


### Lists

Bullet lists and numbered lists, a.k.a. enumerations, offer an
additional method to present sequential and hierarchical information.

``` markdown
- apples
- citrus fruits
  - lemons
  - oranges
```

- apples
- citrus fruits
  - lemons
  - oranges

Enumerations start with the number of the first item. Using the the
first two [laws of
thermodynamics](https://en.wikipedia.org/wiki/Laws_of_thermodynamics) as
example.

``` markdown
0. If two systems are each in thermal equilibrium with a third, they are
   also in thermal equilibrium with each other.
1. In a process without transfer of matter, the change in internal
   energy, $\Delta U$, of a thermodynamic system is equal to the energy
   gained as heat, $Q$, less the thermodynamic work, $W$, done by the
   system on its surroundings. $$\Delta U = Q - W$$
```

Rendered:

0. If two systems are each in thermal equilibrium with a third, they are
   also in thermal equilibrium with each other.
1. In a process without transfer of matter, the change in internal
   energy, $\Delta U$, of a thermodynamic system is equal to the energy
   gained as heat, $Q$, less the thermodynamic work, $W$, done by the
   system on its surroundings. $$\Delta U = Q - W$$