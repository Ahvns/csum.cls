
# csum

This is a LaTeX document class for writing course summaries.
I've written it to ease writing summaries in the future,
and as an exercise in writing LaTeX code and working with GitHub.

## Table of contents

- [`csum.cls`](https://github.com/Ahvns/csum#csumcls)
  - [Features](https://github.com/Ahvns/csum#features)
  - [Implementation](https://github.com/Ahvns/csum#implementation)
  - [Dependencies](https://github.com/Ahvns/csum#dependencies)
- [Custom Packages](https://github.com/Ahvns/csum#custom-packages)
  - [`csumhdr.sty`](https://github.com/Ahvns/csum#csumhdrsty)
  - [`csuminf.sty`](https://github.com/Ahvns/csum#csuminfsty)
  - [`csumsec.sty`](https://github.com/Ahvns/csum#csumsecsty)
  - [`csumtoc.sty`](https://github.com/Ahvns/csum#csumtocsty)
  - [`csumttl.sty`](https://github.com/Ahvns/csum#csumttlsty)
- [Planned Features](https://github.com/Ahvns/csum#planned-features)
- [License](https://github.com/Ahvns/csum#license)

---

## `csum.cls`

`csum.cls` is the main file of the document class.
It's based on the basic article class, with some visual changes and a couple of
new user commands to ease the making of a nice looking course summary.

### Features

Currently, the class adds the following:
- A custom titlepage, including user-input summary information
- A custom table of contents, styled to look similar to the one generated by the
`minitoc` package
- Custom section headers
- Custom header and footer
- A general typesetting preset
- A command to select the type of summary, `\summarytype{}`

Summary type options available:
- course
- article

The file `example.pdf` shows off these features, with `example.tex` containing
the source code and custom syntax used.

### Implementation

The class works by calling several custom packages, one for each feature.
All packages are written in such a manner that they can also be used on their
own, in case only a single feature of the class is desired.
At the moment, the class itself mostly only loads the packages and passes
options on to the article class.
It does provide some preset options for some of the external packages loaded.

### Dependencies

The class uses the following (custom) packages:

- external
  - `etoolbox`
  - `geometry`
  - `charter`
  - `microtype`
  - `hyperref`
- custom
  - `csuminf.sty`
  - `csumttl.sty`
  - `csumsec.sty`
  - `csumtoc.sty`
  - `csumhdr.sty`

---

## Custom Packages

The custom packages used by the class are documented below.
For each package, its features, added commands, dependencies and changed
commands are listed.

### `csumhdr.sty`

#### Features

This package provides a custom header and footer.
The header displays the current section on the left and the current subsection
on the right.
When a new part is started,
the name of the part replaces the section name in the header for that page.
The footer displays the name of the course the summary was written for on the
left and the page number on the right.
The package provides the user command `\headertype{}` to select the style of headers and footers.
Currently, the options `course`(default) and `article` are allowed.

#### Implementation

This package uses the following packages:

- `fancyhdr`
- `xcolor`
- `xstring`
- `csuminf`

It changes the following commands:

- `\partmark{}`
- `\sectionmark{}`
- `\subsectionmark{}`

### `csuminf.sty`

#### Features

This package provides several user commands to store document information.
This stored information is used by the other packages in their functions.
This package provides the following user commands:

- `\email{<mail@website.url>}` for storing author's e-mail
- `\course[<code>]{<name>}` for storing course name and code
- `\yeartaught{<year>}` for storing year the course was taught
- `\lecturer{<name>}` for storing the course lecturer's name
- `\faculty{<name>}` for storing the name of the faculty where the course was
taught
- `\titlequote{<text>}{<name>}` for storing a quote and the quote's author

#### Implementation

This package uses no other packages.
It changes the `\author{}` user command.

### `csumsec.sty`

#### Features

This package provides custom section headers.
Every part, section and subsection now starts on a new page.
Sections are now printed as `Lecture <x>   <name>`.
Subsubsections are now printed without numbering.
Sections, subsections and subsubsections are printed with a horizontal rule
below their name.
At the end of each part, section and subsection, a horizontal rule is printed
indicating the level of section that just ended.
The package provides the `\sectionype{}` user command to select the style of
section headers.
Currently, the options `course`(default) and `article` are allowed.

#### Implementation

This package uses the following packages:
- `titlesec`
- `xstring`
- `setspace`
- `calc`

It changes the following commands:

- `\thepart`
- `\partname`
- `\thesection`
- `\thesubsection`
- `\thesubsubsection`

### `csumtoc.sty`

#### Features

This package provides a custom table of contents, with a look similar to that of
the `minitoc` package table of contents.

#### Implementation

This package uses the following packages:

- `tocloft`
- `calc`

It changes the following commands:

- `\contentsname`
- `\tableofcontents`

### `csumttl.sty`

#### Features

This package provides a custom titlepage.
The titlepage contains the following:

- Author's name
- Author's email address (Optional)
- Course name
- Course code (Optional)
- Year the course was taught (Optional)
- Course lecturer's name (Optional)
- Faculty course was taught at (Optional)
- A quote (Optional)

The titlepage is printed on a separate page.
The package provides the `\titletype{}` user command to select the type of contents in the titlepage.
Currently, the options `course`(default) and `article` are allowed.

#### Implementation

This package uses the following packages:

- `calc`
- `setspace`
- `xstring`
- `ragged2e`
- `csuminf`

It changes the `\maketitle` command.

---

## Planned Features

- improve documentation for user commands
- add license
- provide comments in code
- clean up titlepage generation
- add options for titlepage (e.g. colour or different style)
- add options for section headers (e.g. different section names)
- add class-wide options (e.g. formatting for reading or taking notes)
- add GitHub issue templates
- whatever I think up

---

## License

This package is licensed under the LaTeX Project Public License.
The full license is enclosed in the `LICENSE` file.
