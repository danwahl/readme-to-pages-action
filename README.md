# README to GitHub Pages Action

A simple GitHub Action that converts your README file to HTML and deploys it to GitHub Pages.

[![View on GitHub](https://img.shields.io/badge/View%20on-GitHub-blue)](https://github.com/danwahl/readme-to-pages-action)
[![Visit Website](https://img.shields.io/badge/Visit-Website-green)](https://danwahl.github.io/readme-to-pages-action/)

## Usage

```yaml
name: Deploy README to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  deploy-readme:
    runs-on: ubuntu-latest
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/checkout@v4
      - uses: danwahl/readme-to-pages@v1
        with:
          title: "My Awesome Project Documentation"
          readme: "docs/README.md"
          theme: "auto"
      - uses: actions/deploy-pages@v4
        id: deployment
```

## Inputs

| Input    | Description                                   | Required | Default                                                                 |
|----------|-----------------------------------------------|----------|-------------------------------------------------------------------------|
| `readme` | Path to the README file                       | No       | `README.md`                                                             |
| `style`  | CSS style for the body element                | No       | `min-width:200px;max-width:980px;margin:0 auto !important;padding:45px` |
| `theme`  | Theme for the page (`light`, `dark`, `auto`)  | No       | `auto`                                                                  |
| `title`  | Title for the HTML page                       | No       | Repository name                                                         |

## Setup

1. Enable GitHub Pages in your repository settings
2. Set the Pages source to "GitHub Actions"
3. Add the workflow file to `.github/workflows/`

## License

MIT
