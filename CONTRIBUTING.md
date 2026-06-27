# Contributing

Thanks for helping keep this cheatsheet accurate. Corrections and additions are welcome.

## The bar: accuracy, with a source

This is a reference, so every factual change must be verifiable:

- **Cite a source** for any correction or addition, ideally a link to the official Neovim documentation or the relevant `:help` page (for example `:help ctrl-w`).
- Prefer the official docs over blog posts or AI output.
- If something is version-dependent, say so (which Neovim version).

## How it works

- The whole cheatsheet is one static page: **`public/index.html`**. To add or fix a binding, edit the relevant table row (`<tr>`) or card there.
- The search text and tooltip live in each row's `data-tip` and `data-example` attributes; keep them accurate too.
- **Do not edit anything between the `<!-- cs-footer:start -->` / `<!-- cs-footer:end -->` or `<!-- cs-meganav:start -->` / `<!-- cs-meganav:end -->` markers.** Those blocks are generated automatically and any edits inside them will be overwritten.
- Match the style of the surrounding rows. Please do not use em-dashes (project style); a colon, comma, or parentheses reads better.

## Submitting a change

1. Fork the repo and create a branch.
2. Make your edit in `public/index.html`.
3. Open a pull request describing what changed and linking your source.

All pull requests are reviewed before they are merged. Thank you for contributing.
