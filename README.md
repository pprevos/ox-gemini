# ox-gemini

This package supports exporting org files in [Gemtext format](https://gemini.circumlunar.space/) used in gemini capsules and gemlogs.

## Text
- Write paragraphs as single long lines
- Short lines don't join together
- Blank lines are rendered verbatim

## Links
Links are on a separate line (no inline links), A link line consists of `=>` and the URL, for example:

=> gemini://peterprevos.com/index.gmi

Labels are separated from the URL by one or more spaces or tabs:

=> https://peterprevos.com/ Peter Prevos' website

Gemtext does not have inline links. All inline links are marked with square brackets and `ox-gemini` places link lines at the end of the section. The `org-gemini-link-symbol` variable defines the marking symbols for inline links.

## Headings
Gemtext has a maximum of three levels starting with one or more octothorps:

```
# Heading
## Sub-heading
### Sub-subheading
```

The export engine translates the `#+title:` keyword in org mode as a level one heading.

Org headings start at level 2:
- `*` becomes `##`
- `**` becomes `###`
- All other levels `###`

## Lists
Gemtext only has one unnumbered list level, starting with an asterisk:

```
* Mercury
* Gemini
* Apollo
```

`ox-gemini` collapses all lists items to level 1 and converts it to an unnumbered list.

## Quotes
Here's a quote from Maciej Cegłowski:

> I contend that text-based websites should not exceed in size the major works of Russian literature.

## Pre-fromatted text
Lines which start with ``` cause clients to toggle in and out of ordinary rendering mode and preformatted mode. In preformatted mode, text appears in a monospace font.

