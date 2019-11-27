# Personal Website

This repository hosts my personal website.
GitHub serves [apsql.github.io](https://apsql.github.io) using the files in this repo.
If you are interested in learning more about me, then this repo is useless to you.
If, instead, you want to learn how I did this website, then read on.


## Build Instructions

This website is built using [Jekyll](https://jekyllrb.com/), hosted on [GitHub](https://github.com/) and served by [GitHub Pages](https://pages.github.com/).
To have an overview of the steps to build, see the [Help page on GitHub](https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).

To start a local build of the website, open a Terminal into the repository and run

```bash
$ bundle exec jekyll serve
```

then navigate to http://127.0.0.1:4000/ to preview the website locally.
The previous command assumes that Ruby is installed, together with the gems Bundler and Jekyll.
