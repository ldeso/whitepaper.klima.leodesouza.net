This is a Quarto project for the Klima 2.0 white paper. `index.qmd` is our
source of truth. From it, we will generate many documents of varying complexity.

Be careful not to disturb any math equations unless explicitly asked. Notify the
user if your changes would alter the result of a math calculation.

## Project Structure

- `.quarto/` - Quarto build cache and session files
- `out/` - Generated output files (configured in `_quarto.yml`)

Be sure to read `README.md` for project setup details.

## Key Files

- `index.qmd` - Primary white paper document (source of truth)
- `_quarto.yml` - Quarto project configuration
- `README.md` - Project setup and usage instructions
- `AGENTS.md` - Special instructions for AI agents working on this project

# Markdown Formatting

Use `$` delimiters for inline math and `$$` delimiters for display math.

## .content-visible

To make content visible only for a given format, you can create a div (`:::`)
with the `.content-visible` class. For example, here we mark content as only
visible in HTML:

``` markdown
::: {.content-visible when-format="html"}

Will only appear in HTML.

:::
```

You can also mark content as visible for all formats *except* a specified
format. For example:

```markdown
::: {.content-visible unless-format="pdf"}

Will not appear in PDF.

:::
```

## .content-hidden

To prevent content from being displayed when rendering to a given format, use
the `.content-hidden` class. For example, here we mark content as hidden in
HTML:

```markdown
::: {.content-hidden when-format="html"}

Will not appear in HTML.

:::
```
