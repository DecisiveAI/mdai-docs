<img src="src/media/logo.png" alt="MyDecisive logo">

## ⚠️ **Pre-Alpha Disclaimer**
This open-source project is currently under construction and is subject to frequent changes and updates. For more information about our pre-alpha release, see our [Pre-Alpha Disclaimer](./DISCLAIMER.md)

----

# MyDecisive Engine Documentation

Welcome to the docs! This repo is used to build [the decisive engine docs site](https://decisiveai.github.io/mdai-docs/). More to come in our first beta release!

## Editing/Development

### Prerequisites

- This site is built using [mdBook](https://github.com/rust-lang/mdBook). You can install the `mdbook` utility by following [these instructions](https://rust-lang.github.io/mdBook/guide/installation.html).

```sh
cargo install mdbook mdbook-toc
```

### Local development

Use `mdbook serve` to spin up a local development server, at [http://localhost:3000](http://localhost:3000) by default. Make edits and reload the page to see updated content.

### Deployment

Use `mdbook build` to build the static documentation site at `./book`, which can be deployed to a static site host.
