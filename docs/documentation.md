# Theme Documentation 
## Blockquotes

> Morbi eget dapibus felis. Vivamus venenatis porttitor tortor sit amet rutrum.
  Pellentesque aliquet quam enim, eu volutpat urna rutrum a.

## Lists

### Unordered lists

* Sed sagittis eleifend rutrum.
    * Duis mollis est eget nibh volutpat, fermentum aliquet dui mollis.
* Aliquam metus eros, pretium sed nulla venenatis, faucibus auctor ex.
* Nulla et rhoncus turpis. 

### Ordered lists

1. Integer vehicula feugiat magna, a mollis tellus. 

2. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur
  ridiculus mus.

    1. Vivamus venenatis porttitor tortor sit amet rutrum. 

    2. Morbi eget dapibus felis. 

    3. Pellentesque eget `:::js var _extends` ornare tellus, ut gravida mi.

3. Vivamus id mi enim. Integer id turpis sapien. Ut condimentum lobortis sagittis.

### Definition lists

Lorem ipsum dolor sit amet

:   Sed sagittis eleifend rutrum. Donec vitae suscipit est.

Cras arcu libero

:   Aliquam metus eros, pretium sed nulla venenatis, faucibus auctor ex. Proin
    ut eros sed sapien ullamcorper consequat. 

## Code blocks

    #!js hl_lines="8"
    var _extends = function(target) {
      for (var i = 1; i < arguments.length; i++) {
        var source = arguments[i];
        for (var key in source) {
          target[key] = source[key];
        }
      }
      return target;
    };

## Horizontal line

***

## Data tables

| Sollicitudo / Pellentesi | consectetur | adipiscing |
| ------------------------ | ----------- | ---------- |
| Vivamus a pharetra       | yes         | yes        |
| Ornare viverra ex        | yes         | yes        |
| Mauris a ullamcorper     | yes         | yes        |
| Nullam urna elit         | yes         | yes        |
| Malesuada eget finibus   | yes         | yes        |

## Notes

!!! note

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

  [2]: #types

!!! note "Phasellus posuere in sem ut cursus"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! note

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

    ``` mysql
    SELECT
      Employees.EmployeeID,
      Employees.Name,
      Employees.Salary,
      Manager.Name AS Manager
    FROM
      Employees
    ```

    Nunc eu odio eleifend, blandit leo a, volutpat sapien. Phasellus posuere in
    sem ut cursus. Nullam sit amet tincidunt ipsum, sit amet elementum turpis.
    Etiam ipsum quam, mattis in purus vitae, lacinia fermentum enim.

!!! summary

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! tip

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! success

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! warning

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! failure

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! danger

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! bug

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

!!! quote

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.

## Code Block

``` python
import tensorflow as tf
```

``` python
#!/usr/bin/python
import tensorflow as tf
```

    #!python
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]

    #!python hl_lines="3 4"
    """ Bubble sort """
    def bubble_sort(items):
        for i in range(len(items)):
            for j in range(len(items) - 1 - i):
                if items[j] > items[j + 1]:
                    items[j], items[j + 1] = items[j + 1], items[j]

## Footnotes

Lorem ipsum[^1] dolor sit amet, consectetur adipiscing elit.[^2]

<a href="#fn:1">Jump to footnote at the bottom of the page</a>

## Metadata

The [Metadata][1] extension makes it possible to add metadata to a document
which gives more control over the theme in a page-specific context.

  [1]: https://pythonhosted.org/Markdown/extensions/meta_data.html

Example:

``` markdown
title: Lorem ipsum dolor sit amet
description: Nullam urna elit, malesuada eget finibus ut, ac tortor.
path: path/to/file
source: file.js

## Permalinks

Permalinks are a feature of the [Table of Contents][1] extension, which is part
of the standard Markdown library. The extension inserts an anchor at the end of
each headline, which makes it possible to directly link to a subpart of the
document.

  [1]: https://pythonhosted.org/Markdown/extensions/toc.html

## Installation

To enable permalinks, add the following to your `mkdocs.yml`:

``` yaml
markdown_extensions:
  - toc(permalink=true)
```

This will add a link containing the paragraph symbol `¶` at the end of each
headline (exactly like on the page you're currently viewing), which the
Material theme will make appear on hover. In order to change the text of the
permalink, a string can be passed, e.g.:

``` markdown
markdown_extensions:
  - toc(permalink=Link)
```

## PyMdown Extensions

[PyMdown Extensions][1] is a collection of Markdown extensions that add some
great features to the standard Markdown library. For this reason, the
**installation of this package is highly recommended** as it's well-integrated
with the Material theme.

  [1]: http://facelessuser.github.io/pymdown-extensions/

## Installation

The PyMdown Extensions package can be installed with the following command:

``` sh
pip install pymdown-extensions
```

The following list of extensions that are part of the PyMdown Extensions
package are recommended to be used together with the Material theme:

``` yaml
markdown_extensions:
  - pymdownx.arithmatex
  - pymdownx.betterem(smart_enable=all)
  - pymdownx.caret
  - pymdownx.critic
  - pymdownx.emoji:
      emoji_generator: !!python/name:pymdownx.emoji.to_svg
  - pymdownx.inlinehilite
  - pymdownx.magiclink
  - pymdownx.mark
  - pymdownx.smartsymbols
  - pymdownx.superfences
  - pymdownx.tasklist(custom_checkbox=true)
  - pymdownx.tilde
```

## Usage

### GitHub Flavored Markdown

Most of the extensions included in the PyMdown Extensions package try to bring
the Markdown experience closer to GitHub Flavored Markdown (GFM).

The PyMdown Extensions package adds a shorthand to enable all of the included
extensions that provide the GFM experience. However, usage of the shorthand is
discouraged, because some extensions are not supported, as the Material theme
uses some incompatible extensions included in the standard Markdown library.

#### BetterEm

[BetterEm][2] improves the handling of emphasis markup (**bold** and *italic*)
within Markdown by providing a more sophisticated parser for better detecting
start and end tokens. Read the documentation for [usage notes][3].

  [2]: https://facelessuser.github.io/pymdown-extensions/extensions/betterem/
  [3]: https://facelessuser.github.io/pymdown-extensions/usage_notes/

#### Emoji

[Emoji][4] adds the ability to insert a :shit:-load of emojis that we use in
our daily lives. See the [EmojiOne demo][5] for a list of all available
emojis. Happy scrolling :tada:

!!! warning "Legal disclaimer"

    Material has no affiliation with [EmojiOne][6] which is released under
    [CC BY 4.0][7]. When including EmojiOne images or CSS, please read the
    [EmojiOne license][8] to ensure proper usage and attribution.

  [4]: https://facelessuser.github.io/pymdown-extensions/extensions/emoji/
  [5]: https://emoji.codes/
  [6]: http://emojione.com
  [7]: https://creativecommons.org/licenses/by/4.0/legalcode
  [8]: http://emojione.com/licensing/

#### MagicLink

[MagicLink][9] detects links in Markdown and auto-generates the necessary
markup, so no special syntax is required. It auto-links `http[s]://` and
`ftp://` links, as well as references to email addresses:

  [9]: https://facelessuser.github.io/pymdown-extensions/extensions/magiclink/

#### SuperFences

[SuperFences][10] provides the ability to nest code blocks under blockquotes,
lists and other block elements, which the [Fenced Code Blocks][11] extension
from the standard Markdown library doesn't parse correctly.

  [10]: https://facelessuser.github.io/pymdown-extensions/extensions/superfences/
  [11]: https://pythonhosted.org/Markdown/extensions/fenced_code_blocks.html

#### Tasklist

[Tasklist][12] adds support for styled checkbox lists. This is useful for
keeping track of tasks and showing what has been done and has yet to be done.
Checkbox lists are like regular lists, but prefixed with `[ ]` for empty or
`[x]` for filled checkboxes.

Example:

``` markdown
* [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
* [x] Nulla lobortis egestas semper
* [x] Curabitur elit nibh, euismod et ullamcorper at, iaculis feugiat est
* [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [x] Sed egestas felis quis elit dapibus, ac aliquet turpis mattis
    * [ ] Praesent sed risus massa
* [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
* [ ] Nulla vel eros venenatis, imperdiet enim id, faucibus nisi
```

Result:

* [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
* [x] Nulla lobortis egestas semper
* [x] Curabitur elit nibh, euismod et ullamcorper at, iaculis feugiat est
* [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [x] Sed egestas felis quis elit dapibus, ac aliquet turpis mattis
    * [ ] Praesent sed risus massa
* [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
* [ ] Nulla vel eros venenatis, imperdiet enim id, faucibus nisi

[12]: https://facelessuser.github.io/pymdown-extensions/extensions/tasklist/

#### Tilde

[Tilde][13] provides an easy way to ~~strike through~~ cross out text.
The portion of text that should be erased must be enclosed in two tildes
`~~...~~` and the extension will take care of the rest.

  [13]: https://facelessuser.github.io/pymdown-extensions/extensions/tilde/

### More syntactic sugar

#### Caret

[Caret][14] is the sister extension of [Tilde][15] and makes it possible to
highlight ^^inserted text^^. The portion of text that should be marked as added
must be enclosed in two carets `^^...^^`.

  [14]: https://facelessuser.github.io/pymdown-extensions/extensions/caret/
  [15]: #tilde

#### Mark

[Mark][16] adds the ability to ==highlight text== like it was marked with a
==yellow text marker==. The portion of text that should be highlighted must be
enclosed in two equal signs `==...==`.

  [16]: https://facelessuser.github.io/pymdown-extensions/extensions/mark/

#### SmartSymbols

[SmartSymbols][17] converts markup for special characters into their
corresponding symbols, e.g. arrows (<--, -->, <-->), trademark and copyright
symbols ((c), (tm), (r)) and fractions (1/2, 1/4, ...).

  [17]: https://facelessuser.github.io/pymdown-extensions/extensions/smartsymbols/

#### Critic

[Critic][18] implements [Critic Markup][19], a Markdown extension that enables
the tracking of changes (additions, deletions and comments) on documents.
During compilation of the Markdown document, changes can be rendered (default),
accepted or rejected.

Text can be {--deleted--} and replacement text {++added++}. This can also be
combined into {~~one~>a single~~} operation. {==Highlighting==} is also
possible {>>and comments can be added inline<<}.

{==

Formatting can also be applied to blocks, by putting the opening and closing
tags on separate lines and adding new lines between the tags and the content.

==}

  [18]: https://facelessuser.github.io/pymdown-extensions/extensions/critic/
  [19]: http://criticmarkup.com/
