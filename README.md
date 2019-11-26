# Personal Website

This repository hosts my personal website.
GitHub serves apsql.github.io using the files in this repo.
If you are interested in learning more about me, then this repo is useless to you.
If, instead, you want to learn how I did this website, then read on.


## Build Instructions

This website is built using [Jekyll](https://jekyllrb.com/), hosted on [GitHub](https://github.com/) and served by [GitHub Pages](https://pages.github.com/).
To have an overview of the steps to build, see the [Help page on GitHub](https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).


### Environment

The following requires [Ruby](https://www.ruby-lang.org/en/), [Bundler](https://bundler.io/) and [Jekyll](https://jekyllrb.com/).
I am using [Debian](https://www.debian.org/) in the [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
This means that what I write in this section works on Windows (provided WSL is installed) and on any APT-based distribution (e.g., [Ubuntu](https://ubuntu.com/desktop)).
Ruby is the programming language at the basis of Jekyll.

    sudo apt install ruby

Once Ruby is installed, we need to install Bundler and Jekyll.

    gem install bundler jekyll


### First setup

The initial setup of this folder has been carried out by executing

    gem install bundler jekyll
    jekyll new apsql.github.io

This delivers a minimal working Jekyll setup based off the [Minima Jekyll theme](https://github.com/jekyll/minima).
