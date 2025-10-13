# Klima 2.0 White Paper

This repo is to house the canonical Klima 2.0 white paper text in `index.qmd`.
The goal is to derive sites, docs, PDFs from this canonical .qmd file, while
using `git` for document version control.

This package is powered by Quarto. Quarto makes it possible to derive and export
a variety of different documents (TeX, PDF, HTML, etc.) from the `index.qmd`
source file. It also provides tools for modularizing content, embedding
visualizations, and more.

## Getting Started

If you want to edit or export these docs, install VS Code, Quarto, and the VS
Code Quarto Extension.

https://quarto.org/docs/get-started/

## Prerequisites / Dependencies

Install `tinytex` by running `quarto install tinytex`, and install
`rsvg-convert` by running `sudo apt install -y librsvg2-bin`.

## Usage

All outputs can be found in the `./out` directory.

**Website Preview with Hot Reload**

```bash
# Start interactive editing in the browser
quarto preview
```

**Output All Documents**

```bash
# Outputs html, pdf, and .md to ./out
quarto render
```
