---
layout: post
title: Build Your Website
parent: Resources
permalink: /resources/build-your-website
---

# Build Your Website

This is a note to self, mainly, on how I built my own personal website.

Before we get started, we should talk about how we can get a website.
There are two issues here: getting a **host** and getting a **domain**.
The host is the physical server where your website (the HTML pages) are stored.
The domain is the URL that directs visitors to the website.

### Hosting

There is a whole spectrum of hosting solutions to choose from.
Such spectrum is characterized by the technical difficulty in setting up and managing your website.
But it also ranges in terms of flexibility you get, such as getting the design you prefer.

On the easy (but not very flexible) side we have options such as Google Sites and Squarespace.
These are easy-to-set-up hosting solutions, meaning that those companies will provide the hardware where your website will be stored.
They will not expose the folder structure of the website to you, so you will not directly work on the files that constitute the website.
Rather, they will provide an easy interface to build your website, typically with a point-and-click interface.
These solutions are appealing because you can get a website with no coding experience.
The cost here is that you do not get enough flexibility, so your website will probably never look _exactly_ the way your would like.
This post does _not_ deal with this kind of hosting.

On the other hand, you may set up your own, physical server and manage it by yourself.
This requires much knowledge about how the Internet works, how to get a static IP address (in order to reach your server) and so on.
It is quite complicated to do that.
This post does _not_ deal with this kind of hosting either.

A reasonable (in my opinion) middle-ground solution is given by [GitHub Pages](https://pages.github.com/) or [GitLab Pages](https://about.gitlab.com/product/pages/).
These are hosting solutions that can serve [static websites](https://en.wikipedia.org/wiki/Static_web_page).
You get to manage the individual files, so you can get the website to look exactly like you want it, provided you know how to do it.
You can also get predefined templates (think themes).
You also do not get into the intricacies of setting up a physical server and you do not have to worry about how the Internet works.
These solutions are also free of charge.
This post deals with this sort of hosting solution.


### Domain

A domain is a name that you type in the URL bar of your web browser.
More technically, it is a human readable form of an IP address.
It is the destination that you type into a web browser in order to visit a website.
Getting a custom domain is costly.
There are many vendors that sell domains, among which we have [Google](https://domains.google/), [Domain.com](https://www.domain.com/domains/), [namecheap](https://www.namecheap.com/) and [GoDaddy](https://www.godaddy.com/).
Prices vary, but it is common to see them ranging from 8 to 20 EUR yearly.


## The gist of it

To create a new website from scratch, execute the following from a terminal:

```bash
$ jekyll new new_website    # creates folder "new_website"
$ cd new_website            # moves into new folder
$ bundle exec jekyll serve  # generates a local preview of website
```

Open up a tab on your browser, navigate to [`http://localhost:4000/`](http://localhost:4000/).
Here you will see the newly created website.


## Setup

From here on we get into the details.
First I describe the sort of environment I am working in.
Then I present a small tutorial on how to get a website similar to mine.


### Preliminary information

In the following there are some code blocks.
A line in code block starting with the dollar symbol (`$`) denotes a Shell prompt.
Linux and macOS both come with a shell (either [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) or [Zsh](https://en.wikipedia.org/wiki/Z_shell)).
This may appear in your system as an application called Terminal.
I won't write here why using a terminal might be better than using a point-and-click interface.
It should suffice to say: giving instructions through a terminal is much easier (and unambiguous) relative to a point-and-click interface.

If you are on Windows 10, you do not have an adequate shell out of the box (yes, you have PowerShell, but it sucks).
In this case, install the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) (WSL) and you will obtain a full-fledged Linux environment to work with.


### Operating environment

The following requires [Ruby](https://www.ruby-lang.org/en/), [Bundler](https://bundler.io/) and [Jekyll](https://jekyllrb.com/).
Both Bundler and Jekyll are libraries written in the Ruby programming language.
Ruby libraries are called Gems.
We first need to install Ruby.
Once we have Ruby, we can install Gems.

To install Ruby on an APT-based Linux distribution (e.g., Debian, Ubuntu), execute

```bash
$ sudo apt install ruby
```

If you are on a non-Linux environment, such as macOS or bare Windows, or on a non APT-based Linux distribution (e.g., Fedora), then your installation instruction for Ruby will differ.

Once Ruby is installed, we need to install Bundler and Jekyll.

```bash
$ gem install bundler jekyll
```


### First setup

Create a new website from scratch, based on a default Jekyll template.

```bash
$ jekyll new <website-folder-name>
```

This creates a folder called `<website-folder-name>` in your current working directory.
Inside this folder, we will already find some files.
The newly created folder is the root folder of the website.
It also delivers a minimal working Jekyll setup based off the [Minima Jekyll theme](https://github.com/jekyll/minima).

To preview the website locally, enter the newly created folder and run

```bash
$ bundle exec jekyll serve
```

The terminal will print some lines, one of which will be like the following:

```bash
Server address: http://127.0.0.1:4000
```

This _local_ address can now be reached through your web browser to preview the website.
The website is not yet public though.
As soon as you change a file in the website folder, the Jekyll instance will instantly update your website.
You can terminate the Jekyll instance by pressing <kbd>Ctrl</kbd> + <kbd>C</kbd> at any time.

In this setup, we have two crucial files: `Gemfile` and `_config.yml`.
The first relates to Bundler and keeps track of all Ruby requirements needed to build the website.
The second relates to Jekyll and contains some settings about the website.


### Making sure GitHub Pages will work once the site goes live

The default Gemfile that was created with `jekyll new` contains the following comment:

```bash
# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
```

Do as it says.


### Uploading the website to GitHub, for publication

To publish the website using GitHub Pages, you need to create a repository at [github.com](https://github.com).
If you do not have a custom domain yet, and want your website to appear automatically, then the repository you create must have the name `[username].github.io`, which will also be the URL at which your website will be found.
Once you have the repository, move all files created by Jekyll above into the git repository.
As soon as you push the new files to GitHub, GitHub will start building your website.
It will be publicly available at `[username].github.io` after few minutes.
GitHub will only build using the files in the `master` branch.
If you push updates to your code in another branch, then GitHub will ignore them until you merge into `master`.

(If you are using GitHub, the last two sentences must make sense to you)
{: .fs-2 }


### Changing the theme

The default Jekyll theme, [Minima](https://github.com/jekyll/minima), is advertised as a _one size fits all_ theme, but it is mostly oriented towards blogs.
As my personal webpage is not intended to be a blog (at the moment), I changed the theme.
In particular, I wanted a sidebar with links to the main sections of my website.

There are many Jekyll themes out there, see [Jekyll's page](https://jekyllrb.com/docs/themes/) on the matter.
The one I use is called [Just the Docs](https://pmarsceill.github.io/just-the-docs/).
On a computer screen, it has a sidebar for easy navigation and a main body part that is large enough for normal content.
Content does not necessarily span the whole horizontal space, so [text lines won't be too long](https://en.wikipedia.org/wiki/Line_length).
On a mobile device, the sidebar is hidden and can be accessed with a [Hamburger Button](https://en.wikipedia.org/wiki/Hamburger_button).
To learn how to use the Just the Docs theme, see the author's [Getting Started section](https://pmarsceill.github.io/just-the-docs/#getting-started).

Given the output of the [First Setup](#first-setup) above, we can do the following.
First, in the `Gemfile`, we replace the line

```
gem "minima", "~> 2.5"
```

with

```
gem "just-the-docs"
```

which instructs Bundler to go fetch the gem called `just-the-docs`.
This gem contains all the files necessary to build and render the website using the new theme.
Second, in the file `_config.yml`, we replace the line

```
theme: minima
```

with

```
theme: "just-the-docs"
```

Once you rebuild the site with `bundle exec jekyll serve`, the website will adopt the new theme.

> **Note:** every time you change a file in the website folder, Bundler will automatically rebuild the website locally (you will see this happening in your terminal) for you to verify your changes if you refresh the browser window. However, this cannot happen when you change the `_config.yml` file for technical reasons. To see the changes to `_config.yml`, you need to terminate Jekyll in the terminal and relaunch it.

At this stage, there is one thing not working.
The Just the Docs theme has a search bar at the top of each page.
This won't work with the configuration so far.
We need to set it up.
The instructions are [here](https://pmarsceill.github.io/just-the-docs/docs/search/).

```bash
$ bundle exec just-the-docs rake search:init
```

With this, the search bar will start working.
You may want to exclude certain pages (and their contents) from appearing in the search box.
This may be the case for the `404.html` page you have in the root folder of the website.
All you need to do is to open such page and, in the preamble (delimited with `---`), add the following line

```
search_exclude: true
```

To further customize the theme, we need to get access to certain special folders.
Notable such folders carry the names `_includes`, `_layouts` and `_sass`.
Given the instructions in [First Setup](#first-setup), we do not have those folders in our root folder.
We need to find them and copy them over.
Once they're copied, we can modify the copies to override certain defaults (e.g., the color of the hyperlinks).
We can locate where these folders are by running

```bash
$ bundle show just-the-docs
```

Call the result of such command `<that-folder>`.
Then, we can copy the folders over

```bash
$ cp <that-folder>/_includes ./_includes -r
$ cp <that-folder>/_layouts ./_layouts -r
$ cp <that-folder>/_sass ./_sass -r
```

The command `cp` copies the files and is a Unix/Linux command (meaning you have it on macOS).
You can learn more about that command [here](http://man7.org/linux/man-pages/man1/cp.1.html).
Now we can modify the contents of these three folders (the ones in the root folder of your website, not the ones in `<that-folder>`!) to override default theme settings.
