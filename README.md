# README to GitHub Pages Action

A simple GitHub Action that converts your README file to HTML and deploys it to GitHub Pages.

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
```

## Inputs

| Input         | Description                                  | Required | Default         |
| ------------- | -------------------------------------------- | -------- | --------------- |
| `readme`      | Path to the README file                      | No       | `README.md`     |
| `theme`       | Theme for the page (`light`, `dark`, `auto`) | No       | `light`         |
| `title`       | Title for the HTML page                      | No       | Repository name |

## Setup

1. Enable GitHub Pages in your repository settings
2. Set the Pages source to "GitHub Actions"
3. Add the workflow file to `.github/workflows/`

## License

MIT
