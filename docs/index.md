# Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

## 中文搜索测试段落

> [官方中文搜索支持配置](https://squidfunk.github.io/mkdocs-material/blog/2022/05/05/chinese-search-support/?h=search)

这是一个测试段落。

## 安装依赖

```bash
pip install mkdocs-git-revision-date-localized-plugin

pip install mkdocs-git-committers-plugin-2
pip install mkdocs-git-authors-plugin

pip install "mkdocs-material[imaging]"

```

## 自动化部署文档

```yml
# .github/workflows/ci.yml
name: ci 
on:
  push:
    branches:
      - master
      - main
      - doc
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ["3.10"]
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-python@v4
        with:
          python-version: 3.x
      - run: pip install mkdocs-material
      - run: pip install mkdocs-minify-plugin
      - run: pip install mkdocs-git-revision-date-localized-plugin
      - run: pip install pip install mkdocs-git-committers-plugin-2
      - run: pip install mkdocs-git-authors-plugin
      - run: mkdocs gh-deploy --force
```
