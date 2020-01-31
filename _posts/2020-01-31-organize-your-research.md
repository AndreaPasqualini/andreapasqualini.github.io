---
layout: post
title: How I Organize My Research
parent: Resources
permalink: /resources/how-you-can-organize-your-research
---

# How I Organize My Research

When I started working on research projects, I had no idea of how I could organize my files.
I knew I needed a folder for each project, but I did not know how to organize files inside it.
It took me roughly two years to understand the workflow, and one more year to optimize my organization around it.
This is the reason that motivates this post.
I will describe what I found works best (for me), so that others may draw inspiration from it.


## The problem

Consider the following folder structure.

```
research_project
├── code
├── data
├── drafts
├── figures
└── journal
```

Every folder has a name describing its contents.
This is trivial to understand and conceive.

However, research is a lot about trying things.
We change parameters to our models, we simulate them, we run different regressions simply swapping variables over and over again.
When we run complex calculations, we save the results to a dataset so that we can quickly pick those up later.
This produces a lot of code, intermediate datasets and figures.
Also, we might want to store personal notes (that is why I have the folder `journal`) so that we do not lose anything.
When it comes to drafts of the paper, we often make edits and submit write-ups to multiple places, so we may want to keep multiple versions of the paper, just for reference.

When I started working on a research project, its folder quickly became a mess.

```
.
├── bureaucracy
├── code
│   ├── 1000periodi_sbagliati
│   ├── 300periodi_sbagliati
│   ├── 500periodi_giusti_forse
│   ├── dev
│   ├── lib
│   ├── old
│   │   ├── v1
│   │   ├── v2
│   │   ├── v3
│   │   └── v4
│   │       ├── dev
│   │       └── lib
│   ├── prof
│   ├── r_out
│   └── scratches
├── data
│   ├── calibration
│   ├── Data Stock Market and CPI
│   ├── old
│   ├── productivity
│   │   ├── Estimation
│   │   └── Graphs
│   ├── sdf
│   │   └── old
│   │       └── Stock markets
│   └── US
├── draft
├── figures
│   ├── comparison_returns
│   │   ├── backward
│   │   │   ├── r1
│   │   │   ├── r2
│   │   │   └── r4
│   │   └── forward
│   │       ├── r1
│   │       ├── r2
│   │       └── r4
│   ├── descriptives_stock_mkt
│   ├── hall2017_replication
│   ├── irfs
│   │   └── all
│   ├── old_descriptives
│   ├── old_simulations
│   ├── productivity
│   ├── simulations_govt_yields
│   ├── simulations_joint
│   ├── simulations_stock_mkt
│   ├── simulations_stock_mkt_lei
│   ├── simulations_wrds_stock_mkt
│   ├── studying_ar
│   └── US_simulations
├── misc
│   ├── send_to_diego
│   │   ├── data
│   │   └── lib
│   │       └── SIMON
│   ├── send_to_diego_2
│   │   └── lib
│   ├── send_to_diego_3
│   │   ├── figures
│   │   └── refs
│   └── slides34 - Cambridge
│       └── ORIGINAL_MATERIAL
├── notes
│   └── old
├── old_code
│   ├── dev
│   ├── exercises
│   │   ├── aggregation_returns
│   │   ├── cqst_productivity_data
│   │   └── insta_hiring
│   ├── lib
│   │   └── SIMON
│   ├── old
│   │   ├── andrea
│   │   │   ├── dynare_alternative
│   │   │   │   └── model_FRAME_dynare
│   │   │   │       └── Output
│   │   │   ├── hall2017_replication
│   │   │   └── lib
│   │   ├── Original codes alexey
│   │   └── SIMON
│   └── scratches
├── old_draft
│   ├── latest
│   │   └── figures
│   ├── old
│   │   ├── 2018-03-march
│   │   │   └── figures
│   │   ├── 2018-04-april
│   │   ├── 2018-07-july
│   │   │   ├── figures
│   │   │   └── old_revisions
│   │   ├── 2018-10-october
│   │   │   └── figures
│   │   └── 2019-02-february
│   │       └── figures
│   └── old_alexey
├── old_notes
│   └── figures_lmi
├── old_slides
│   ├── 2017_11_10-London
│   │   └── graphs
│   ├── 2018_06_08-Brussels
│   │   ├── 20180608-graphs
│   │   └── lyx
│   └── 2019_03_14-Brussels
│       └── figures
└── related_literature
    ├── calibration
    │   └── ElsbyEtAl2012
    ├── Discount_factors
    ├── dual_labor_markets
    ├── Hall2017
    │   └── Matlab
    ├── interpolation
    ├── petroskynadeau_zhang_2017_qe
    │   └── Sec2 programs
    │       ├── Figures
    │       ├── Output
    │       ├── Programs
    │       └── support_funcs
    │           └── CompEcon2012
    └── productivity
```

And these are just the directories.
You do not want to see the folder tree including the files!

Housekeeping this mess quickly became a burden and was slowing down my productivity.
When I had to edit some code, it was not clear where exactly it was:
Which folder?
Which file?
Should I overwrite existing files?
Should I copy the file, calling the new one `code_new`?
Should I rename the old file `code_old`?

All of this becomes worse when you work on a project with somebody else.
You need to coordinate if you want the project folder to stay organized.
Unspoken conventions and verbal agreements have never been enough in my experience.
Somebody was messing up something, and that was grinding my gears even more.
It could not go on like this.

So I began lurking the web, googling for advice on how to keep things organized.
It had to be simple and concise, but it also had to keep track of old work in case I needed to go back to it.

No matter what or how I searched, I always ended up observing two facts.

1. There are little resources from academics about this issue, and
1. Non-academic people with relevant/valuable advice were software developers with one and only one suggestion: a _version control system_ and written guidelines/documentation about the contents of the project.


## A solution: Git

What is `git`?
It is a program created by Linus Torvalds that implements a _version control system_ (VCS).
A VCS does exactly what it says: it tracks files and manages their versions.

I will not write in depth what git is, or how to use it.
There are countless manuals, blog posts and other resources on the Internet about it.
Trivially, you should check the [Wikipedia page on git](https://en.wikipedia.org/wiki/Git).
However, the gist of it is the following.

Git tracks files inside a root folder.
This post is about managing files for a research project, so the root folder is the folder of the research project.
Once we set up git (`git init` for a new folder/project, `git clone` for existing remote resources), it starts checking our actions.
Any file inside the root folder is either tracked or untracked.
Untracked files are just ignored by git, unless we manually track them (using `git add filename`).
Tracked files instead can be in four states: unmodified, modified, new, deleted (A file that is renamed counts as deleted and re-created ex-novo with the new name; a file that is moved counts as a renamed file.).
For every action we take, we can _commit_ the change with a (mandatory) message.
For example, suppose we have a tracked file and we change it by adding some code to it.
Git will notice the change.
Once we are done with the changes, we can `git commit` them, appending a message.
The message [should provide context](https://chris.beams.io/posts/git-commit/) for the change.

This process defines a commit history, which is an overview of all changes that occurred throughout the life of the project.

Another useful feature of git is _branches_.
The default branch name is `master`.
Say that everything is clean on the master branch, and now it is time for us to try something with our code.
We can create a new branch (say, `development`), and try everything we want in that branch.
The commit history of the master branch will be unaffected by the commits to the development branch.
This way, we are sure that the master branch will have clean, usable code, while the develpoment branch might have some problems (e.g., code not working, messy filenames).
Once we are done with the development branch and we are ready to include all the changes in the master branch, all we do it `merge` the two branches.
Finally, if you want to save a snapshot of your code (that would otherwise end up in a folder called `old`), all you have to do is to branch out the snapshot, give it a sensible name (e.g., `snapshot-yyyy-mm-dd`) and never touch it again.

At the end of the day, after committing, branching out and merging, we end up with something like this.

<img src="http://gitready.com/images/pick.png" alt="Commit history" style="margin:auto;border-style:inset;border-width:1px;border-color:#ededed;border-radius:8px">

<sup>This is a random example I found on the internet, it has nothing to do with my work, but I believe it gets the message through.</sup>

To make all of this even more attractive, we can use hosting services like [GitHub](https://github.com/) or [GitLab](https://gitlab.com/) as _remotes_ for our folders.
This effectively amounts to backing up our work, so that if something happens to our computer, we are safe.
Having remotes also allows for easy collaboration across co-workers, where everybody contributes to what is in the remote at the end of the day.
In this instance, local copies are only useful to the individual working on their own machine.
We can `git pull` to download from the remote and `git push` to upload.

I found this workflow to be neat.
So I use it everyday in my research.
My master branches are always working, but may be outdated.
My development branches instead might have code that does not work or results that make no sense.
If I am working on two independent things (e.g., a new regression and a draft of the paper with the old regression), then I create two branches, one for each task.

<sup>
For the git masters out there: yes, you can do soooo much more with git. This is not the right place for listing everything git can do.
</sup>

A note for users of cloud sync services (e.g., Dropbox):
you should not keep your git folders synced up on these cloud services, because (hidden) git folders change all the time and syncing them leads to all sorts of errors.
As I mentioned, you can use cloud hosting at GitHub/GitLab to sync git repositories and to share your work with coworkers.


## The need for guidelines/documentation

There is one last issue I would like to discuss.
The need for documentation.

Here, I call documentation _anything_ that helps yourself and others understand what they are looking at.
It can be instructions on how to use some code, but it can also be a `ReadMe.txt` file that describes the structure of the folder.

Placing documentation in your research project is invaluable.
It provides a guide to your future self.
It did happen to me that I had to leave my project for sometime to work on something else, and then I would go back to it.
It did happen that, coming back to it, I had no idea where I was left.
I had no track of what I was doing last time.
I could not remember what was the issue with a particular line of code, or a particular result.
It did also happen that I simply could not remember what file I had to pick up.
This meant that I spent way too much time getting up to speed, trying to remember what I was doing, before actually getting work done.

A similar argument applies when you share a project with a co-worker.
Documentation helps co-workers understand what you do and why you organized your folder in that way.
It also helps peers replicate your work, should they ever want to do that.

A simple way of documenting your project folder is by adding a `ReadMe` file.
I use Markdown files (with extension `.md` or `.markdown`), so I can use basic editing markup like bold and italics.
I can also include hyperlinks.
These files are then translated into HTML by GitHub (or GitLab), so it is easy to consult them.


## Conclusion

Using a version control system and a set of ReadMe files works very well for me.
To be clear, learning and using git (or any other VCS) takes its overhead in terms of time.
But in the long run it pays off, because the time used in overhead tasks (using git) will be much less than the time used in manual housekeeping only using filenames.

This is how the development branch of my main research project looks like at the time of writing.

```
.
├── bibliography.bib
├── code
│   ├── compare_markups.do
│   ├── compute_markups_basile.do
│   ├── data_prep.do
│   ├── download_sdi_data.py
│   ├── fred_prep.do
│   ├── gmm.log
│   ├── markups.do
│   ├── markups_markdowns.do
│   ├── pull_variables.json
│   ├── sdi_dataset_assembler.py
│   └── summary_stats.do
├── data
│   ├── cpi.dta
│   ├── fred
│   │   ├── CPILFESL.csv
│   │   └── README.md
│   ├── markups.dta
│   ├── master_allbanks.dta
│   ├── master.dta
│   ├── README.md
│   ├── sdi
│   │   ├── README.md
│   │   └── sdi_income_and_expenses.pdf
│   └── sdi.csv
├── dload_n_build_master.sh
├── drafts
│   ├── 20200105-warwick_phd_conference.pdf
│   ├── 20200105-warwick_phd_conference.tex
│   └── README.md
├── figures
│   ├── both_markups.pdf
│   ├── breakdown_cobb_douglas_edepdom.pdf
│   ├── breakdown_cobb_douglas_eintexp.pdf
│   ├── breakdown_cobb_douglas_epremagg.pdf
│   ├── breakdown_cobb_douglas_eqcdiv.pdf
│   ├── breakdown_cobb_douglas_esal.pdf
│   ├── breakdown_cobb_douglas_ideoth.pdf
│   ├── breakdown_translog_edepdom.pdf
│   ├── breakdown_translog_eintexp.pdf
│   ├── breakdown_translog_epremagg.pdf
│   ├── breakdown_translog_eqcdiv.pdf
│   ├── breakdown_translog_esal.pdf
│   ├── breakdown_translog_ideoth.pdf
│   ├── decomposition_cd.pdf
│   ├── decomposition_tl.pdf
│   ├── markups_cobb_douglas_by_varcost.pdf
│   └── markups_translog_by_varcost.pdf
├── journal
│   ├── 20190912-meeting_serranovelarde.md
│   ├── 20191004-note.md
│   ├── 20191008-note.md
│   ├── 20191212-meeting_basile.md
│   ├── 20200128-note.md
│   ├── 20200129-note.md
│   └── 20200130-meeting_basile.md
├── LICENSE
├── notebooks
│   └── deposit_competition.ipynb
└── README.md
```

And these are _all_ the files I have (as of yet), not only the directories.
It ended up being very clean and functional.
Things will change as I progress, and using git allows me to easily switch between versions of my work.
I got rid of all those files with weird names, like `*_old`, `*_old_old` and `*_wrong`.
Keeping up with progress has never been more faster for me.

I hope that you, my reader, can find this note useful for your own work.


---

To generate the text representation of my folder structure, I used the following Unix commands.

```bash
$ tree     # for listing all directories and files
$ tree -d  # for listing only the directories
```
