## Motivation

It was once common for statistical instructors to use the following statistical notation:

- **matrices**: squiggly underline
- **vectors**: underline

This notation has, sadly, fallen out of favor: 

I find the traditional notation to be much easier to read than modern choices (such as bold face).

## The code

This LaTeX code will work in Quarto:

```
\renewcommand{\vector}[1]{\underline{#1}}
\renewcommand{\matrix}[1]{\underset{\sim}{#1}}
```

## Implementation for rendering Quarto to HTML

To implement this in Quarto when rendering to HTML, place the above within `$$` near the top of your Quarto document, like this:

```
$$
\renewcommand{\vector}[1]{\underline{#1}}
\renewcommand{\matrix}[1]{\underset{\sim}{#1}}
$$
```

## Implementation for rendering Quarto to PDF

To implement this in Quarto when rendering to PDF, place the above within `include-in-header` in the YAML, like this:

```
format:
  pdf:
    include-in-header:
      text: |
        \let\matrix\relax
        \renewcommand{\vector}[1]{\underline{#1}}
        \newcommand{\matrix}[1]{\underset{\sim}{#1}}
```

