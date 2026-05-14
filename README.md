## Motivation

It was once common for statistical instructors to use the following notation:

- **vectors**: underline
- **matrices**: squiggly underline

This notation has, sadly, fallen out of favor: most modern textbooks and online resources use bold face. 

I find the traditional notation to be much easier to read than bold face.

## The code

```
\renewcommand{\vector}[1]{\underline{#1}}
\renewcommand{\matrix}[1]{\underset{\sim}{#1}}
\newcommand{\ev}{\mathrm{E}}
\newcommand{\var}{\mathrm{Var}}
```

This will define the following commands:

- `\vector`: for vectors
- `\matrix`: for matrices
- `\ev`: for expected value
- `\var`: for variance

## Implementation 

### Rendering Quarto to HTML

To implement this in Quarto when rendering to HTML, place the code within `$$` near the top of your Quarto document, like this:

```
$$
\renewcommand{\vector}[1]{\underline{#1}}
\renewcommand{\matrix}[1]{\underset{\sim}{#1}}
\newcommand{\ev}{\mathrm{E}}
\newcommand{\var}{\mathrm{Var}}
$$
```

### Rendering Quarto to PDF

To implement this in Quarto when rendering to PDF, place the code after `include-in-header` in the YAML, like this:

```
format:
  pdf:
    include-in-header:
      text: |
        \let\matrix\relax
        \renewcommand{\vector}[1]{\underline{#1}}
        \newcommand{\matrix}[1]{\underset{\sim}{#1}}
        \newcommand{\ev}{\mathrm{E}}
        \newcommand{\var}{\mathrm{Var}}
```

Note that you must include `\let\matrix\relax` here.

### Rendering LaTeX

Place the code in the premable:

```
\let\matrix\relax
\renewcommand{\vector}[1]{\underline{#1}}
\newcommand{\matrix}[1]{\underset{\sim}{#1}}
\newcommand{\ev}{\mathrm{E}}
\newcommand{\var}{\mathrm{Var}}
```

Note that you must include `\let\matrix\relax` here.
