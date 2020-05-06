# Introduction

### New to [Git](https://git-scm.com/), [GitHub](https://github.com/), [GHE](https://enterprise.github.com/faq)?

- [How'd this page get here?](01_first_repo_101.md) ( 01_first_repo_101.md )

Git Handbook: [https://guides.github.com/introduction/git-handbook/](https://guides.github.com/introduction/git-handbook/)

- What's a version control system?
- What's a distributed version control system?
- Basic Git [commands](https://git-scm.com/docs)
  - [git init](https://git-scm.com/docs/git-init)
  - [git clone](https://git-scm.com/docs/git-clone)
  - [git add](https://git-scm.com/docs/git-add)
  - [git commit](https://git-scm.com/docs/git-commit)
  - [git status](https://git-scm.com/docs/git-status)
  - [git branch](https://git-scm.com/docs/git-branch)
  - [git merge](https://git-scm.com/docs/git-merge)
  - [git pull](https://git-scm.com/docs/git-pull)
  - [git push](https://git-scm.com/docs/git-push)

### New to Markdown?

_Markdown is a lightweight and easy-to-use syntax for styling all forms of writing on the GitHub platform._

- [Mastering Markdown](https://guides.github.com/features/mastering-markdown/)
  - [Basic writing and formatting syntax](https://help.github.com/en/github/writing-on-github/basic-writing-and-formatting-syntax)

### Expections

```diff
+ You understand the basic git commands: 
+   init, clone, add, commit, status, branch, merge, pull, push, log, diff
! You understand why this text is orange
- You understand why this text is red
# You understand why this text is gray
```

> :warning: **Please understand the GIT basics before continuing**: This is not a beginners guide!

**When in doubt** :book: https://git-scm.com/docs :book:


:white_check_mark: documented standard  
:warning: warning   
:heavy_exclamation_mark: danger  
:x: explicitly probihited 

# Starting out

  [GitHub 101](03_github_101.md) ( 03_github_101.md )
  
- One repository per application (unless otherwise stated by architecture) :white_check_mark:
- Repository naming (biz vertical / dept + app name) :white_check_mark:
- All common branches should be [protected](https://help.github.com/en/github/administering-a-repository/about-protected-branches): develop, master, release, etc :white_check_mark:
  - [Example](02_protected_branches_101.md) ( 02_protected_branches_101.md )
  
#### 1.6 Getting Started - [First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

```
$  git config --list --show-origin
file:/Users/p50736/.gitconfig   user.name=Ben Tomblin
file:/Users/p50736/.gitconfig   user.email=butomblin@acg.aaa.com
```

Your gitconfig email should always match  what's setup in:

https://paentgit01.aaa-acg.net/settings/emails

![Image](/images/01_starting_out.png)

> :warning: **When your email doesn't match**

![Image](/images/02_starting_out.png)

# Branching strategies

### Git Workflows

Git workflows are nothing special. They are just a documented branching and integration strategy teams can adhere to in order to allow lots of people to work on a project together seamlessly. 

- No Flow / Centralized Workflow (using GIT like SVN)
  - https://www.atlassian.com/git/tutorials/comparing-workflows#centralized-workflow
- **Github Flow**
  - https://guides.github.com/introduction/flow/
- **GitFlow**
  - https://nvie.com/posts/a-successful-git-branching-model/
  - https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
- **GitLab Flow**
  - https://docs.gitlab.com/ee/topics/gitlab_flow.html
  
 Overview: https://blog.programster.org/git-workflows

 ### Guidance

 Vincent Driessen (original author of Gitflow)

 >**Note of reflection** _(March 5, 2020)_
 >
> This model [GitFlow] was conceived in 2010, now more than 10 years ago, and not very long after Git itself came into being. In those 10 years, git-flow ([the branching model laid out in this article](https://nvie.com/posts/a-successful-git-branching-model/)) has become hugely popular in many a software team to the point where people have started treating it like a standard of sorts — but unfortunately also as a dogma or panacea.
>
> During those 10 years, Git itself has taken the world by a storm, and the most popular type of software that is being developed with Git is shifting more towards web apps — at least in my filter bubble. Web apps are typically continuously delivered, not rolled back, and you don't have to support multiple versions of the software running in the wild.
>
> This is not the class of software that I had in mind when I wrote the blog post 10 years ago. If your team is doing continuous delivery of software, I would suggest to adopt a much simpler workflow (like [GitHub flow](https://guides.github.com/introduction/flow/)) instead of trying to shoehorn git-flow into your team.
>
> If, however, you are building software that is explicitly versioned, or if you need to support multiple versions of your software in the wild, then git-flow may still be as good of a fit to your team as it has been to people in the last 10 years. In that case, please read on.
>
> To conclude, always remember that panaceas don't exist. Consider your own context. [Don't be hating](https://www.youtube.com/watch?v=oHg5SJYRHA0). Decide for yourself.

### Standards :white_check_mark: 

- Any publicly well documented git workflow is acceptable
  - The workflow being used must be declared in the projects README.md
- All commits should be made to [feature branches](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)
- Delete the feature branch during merge
- Branches should use the following prefixes/tags (as appropriate)
  - `feature/`
  - `hotfix/`
  - `release/`

#### If using GitFlow

> Each repository should have two historical branches, `master` and `develop`.
>
>`origin/master` is the "production-ready" state of the application. `origin/develop` is stable code ready for a release that runs in parallel with `master`.
>
>When working off of the `develop` branch use `feature` branches descriptively named and prefixed by "feature". For example, `feature/new-oauth2-scopes`. When your feature is complete and ready for review you need to make a pull request to merge your code into `develop`. Your code should be passing all tests if applicable. Your code must be reviewed and approved by another member of the team.
>
>When ready to make a release to production you should use a `release` branch off of `develop`, prefixed by "release". For example, `release/1.0.0`. Your release branch should be named using [semantic versioning](http://semver.org/) and this version should be the same as your version number in `package.json`. A pull request should be made to merge your release into `master`.
>
>If you need to make a bug fix to a production application make a `hotfix` branch off of `master`. A pull request should be made directly into `master` and `master` should then me merged back into `develop` to stay up to date. The developer should follow this branching model when the project is in "post-launch support". If a significant feature is being addressed use `feature` branches off of develop; if bug fixes are being addressed use `hotfix` branches and merge directly into `master`.

https://github.com/punkave/best-practices/blob/master/version-control.md

### Recommendations

- Try to maintain a [linear history](https://www.bitsnbites.eu/a-tidy-linear-git-history/)
  - Github: [Requiring a linear commit history](https://help.github.com/en/github/administering-a-repository/requiring-a-linear-commit-history)
  - [Advantages](https://stackoverflow.com/questions/20348629/what-are-advantages-of-keeping-linear-history-in-git)
- Feature branches should be short lived

### Prohibited :x:

- Using branching as versioning / environment strategy, the only branches below that follow any set branching strategy are `develop` and `master` the rest should be deleted
  
```
digital-api-auto-policy-detail p50736$ git branch -a
* master
remotes/origin/HEAD -> origin/master
remotes/origin/apply-authorizer
remotes/origin/develop
remotes/origin/master
remotes/origin/r1
remotes/origin/r1-dev
remotes/origin/r1-master
remotes/origin/r1-qa
remotes/origin/r2-dev
remotes/origin/r2-master
remotes/origin/r2-qa
remotes/origin/s-21611
remotes/origin/uat_tcs
remotes/origin/uprod-configuration
```

# Rebase vs Merge

[git-rebase](https://git-scm.com/docs/git-rebase) - Reapply commits on top of another base tip

[git-merge](https://git-scm.com/docs/git-rebase) - Join two or more development histories together

3.6 [Git Branching](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) - [Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)

GitHub- [Using Git rebase on the command line](https://help.github.com/en/github/using-git/using-git-rebase-on-the-command-line)  

[Don’t Fear The Rebase](https://hackernoon.com/dont-fear-the-rebase-bca683888dae)  
[A Beginner’s Guide to Squashing Commits with Git Rebase](https://medium.com/@slamflipstrom/a-beginners-guide-to-squashing-commits-with-git-rebase-8185cf6e62ec)

### Git team workflows: merge or rebase? 

Article: https://www.atlassian.com/git/articles/git-team-workflows-merge-or-rebase  
Tutorial: https://www.atlassian.com/git/tutorials/merging-vs-rebasing

>If you and your team are not familiar with, or don't understand the intricacies of `rebase`, then you probably shouldn't use it. In this context, **always merge** is the safest option.
>
>If you and your team are familiar with both options, then the main decision revolves around this: **Do you value more a clean, linear history? Or the traceability of your branches?** In the first case go for a `rebase` policy, in the later go for a `merge` one. 

:warning: **Warnings**: 

- The [golden rule](https://www.atlassian.com/git/tutorials/merging-vs-rebasing#the-golden-rule-of-rebasing) of git rebase is to never use it on public branches
- The [rebase and merge behavior on GitHub](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-request-merges) deviates *slightly* from `git rebase`

# Merge Conflicts

You can resolve simple merge conflicts that involve competing line changes on GitHub, using the [conflict editor](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-on-github).

For all other types of merge conflicts, you must [resolve the conflict locally on the command line](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-using-the-command-line). 

# Git Commit Messages

### The seven rules of a great Git commit message

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

https://chris.beams.io/posts/git-commit/

### My Favorite Git Commit

https://dhwthompson.com/2019/my-favourite-git-commit

### Telling Stories Through Your Commits

https://blog.mocoso.co.uk/talks/2015/01/12/telling-stories-through-your-commits/

# Versioning / Tagging :construction:

Your release branch should be named/tagged using [semantic versioning](http://semver.org/) and this version should be the same as your version number in `package.json` (if using node).

# References

- Git Pro Book: [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)
- Atlassian Tutorials: [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)

### Quick Reference Guides

- escape a git mess, step-by-step » http://justinhileman.info/article/git-pretty/git-pretty.png :laughing:
- GitHub- Git Cheat Sheet » https://github.github.com/training-kit/downloads/github-git-cheat-sheet/ (as [PDF](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf))
- Tower- Git Cheat Sheet » https://www.git-tower.com/learn/cheat-sheets/git  

### Git GUI Clients

- Atlassian Sourcetree: [https://www.sourcetreeapp.com/](https://www.sourcetreeapp.com/)
- Github Desktop: [https://desktop.github.com/](https://desktop.github.com/)

### General GIT Commands

- How to **reset**, **revert**, and return to previous states in Git
   - [https://opensource.com/article/18/6/git-reset-revert-rebase-commands](https://opensource.com/article/18/6/git-reset-revert-rebase-commands)
 - How to **delete** remote branches in Git
   - https://www.educative.io/edpresso/how-to-delete-remote-branches-in-git

### Misc / Fun

- Complete list of github markdown emoji markup: https://gist.github.com/rxaviers/7360908
- gitm:laughing:ji- An emoji guide for your commit messages: https://gitmoji.carloscuesta.me/