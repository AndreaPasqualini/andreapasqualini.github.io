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

    jekyll new <website-folder-name>

This creates a folder called `<website-folder-name>` in your current working directory.
The newly created folder is the root folder of the website.
It also delivers a minimal working Jekyll setup based off the [Minima Jekyll theme](https://github.com/jekyll/minima).

To preview the website locally, enter the newly created folder and run

    bundle exec jekyll serve


### Making sure GitHub Pages will work once the site goes live

The default Gemfile that was created with `jekyll new` contains the following comment:

    If you want to use GitHub Pages, remove the "gem "jekyll"" above and uncomment the line below. To upgrade, run `bundle update github-pages`.

Do as it says.


### Changing the theme

The default Jekyll theme, [Minima](https://github.com/jekyll/minima), is advertised as a _one size fits all_ theme, but it is mostly oriented towards blogs.
As my personal webpage is not intended to be a blog (at the moment), I changed the theme.

There are many Jekyll themes out there, see [Jekyll's page](https://jekyllrb.com/docs/themes/) on the matter.
The one I like the most is called [Just the Docs](https://pmarsceill.github.io/just-the-docs/).
On a computer screen, it has a sidebar for easy navigation and a main body part that is large enough for normal content.
Content does not span the whole horizontal space, so [text lines won't be too long](https://en.wikipedia.org/wiki/Line_length).
On a mobile device, the sidebar is hidden and can be accessed with a [Hamburger Button](https://en.wikipedia.org/wiki/Hamburger_button).
To learn how to use the Just the Docs theme, see the related [Getting Started section](https://pmarsceill.github.io/just-the-docs/#getting-started).

Given the output of the [First Setup](#first-setup) above, I did the following.
First, in the [Gemfile](./Gemfile), I replaced the line

    gem "minima", "~> 2.5"

to

    gem "just-the-docs"

which instructs Bundler to go fetch the gem called `just-the-docs`.
This gem contains all the files necessary to build and render the new theme.
Second, in the file [_config.yml](./_config.yml), I replaced the line

    theme: minima

to

    theme: "just-the-docs"

Once you rebuild the site with `bundle exec jekyll serve`, the website will adopt the new theme.

There is one thing left to do.
The Just the Docs theme has a search bar at the top of each page.
This won't work with the configuration so far.
We need to set it up.
The instructions are [here](https://pmarsceill.github.io/just-the-docs/docs/search/).

    bundle exec just-the-docs rake search:init

To further customize the theme, we need to get access to certain special folders.
Such folders carry the names `_includes`, `_layouts` and `_sass`.
Given the instructions in [First Setup](#first-setup), we do not have those folders in our root folder.
We need to find them and copy them over.
Once they're copied, we can modify the copies to override certain defaults (e.g., the color of the hyperlinks).
We can locate where these folders are by running

    bundle show just-the-docs

Call the result of such command `<that-folder>`.
Then, we can copy the folders over

    cp <that-folder>/_includes ./_includes -r
    cp <that-folder>/_layouts ./_layouts -r
    cp <that-folder>/_sass ./_sass -r

The command `cp` copies the files and is a Unix/Linux command (meaning you have it on macOS).
You can learn more about that command [here](http://man7.org/linux/man-pages/man1/cp.1.html).
Now we can modify the contents of these three folders (the ones in the root folder of your website, not the ones in `<that-folder>`!) to override default theme settings.
