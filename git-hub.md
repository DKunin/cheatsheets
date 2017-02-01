# Github

## [Source](https://github.com/tiimgreen/github-cheat-sheet/)

### Ignore Whitespace
Adding `?w=1` to any diff URL will remove any changes only in whitespace, enabling you to see only that code that has changed.

![Diff without whitespace](https://camo.githubusercontent.com/797184940defadec00393e6559b835358a863eeb/68747470733a2f2f6769746875622d696d616765732e73332e616d617a6f6e6177732e636f6d2f626c6f672f323031312f736563726574732f776869746573706163652e706e67)


### Adjust Tab Space
Adding `?ts=4` to a diff or file URL will display tab characters as 4 spaces wide instead of the default 8. The number after `ts` can be adjusted to suit your preference. This does not work on Gists, or raw file views, but a [Chrome](https://chrome.google.com/webstore/detail/tab-size-on-github/ofjbgncegkdemndciafljngjbdpfmbkn) or [Opera extension](https://addons.opera.com/en/extensions/details/github-tab-size/) can automate this.

Here is a Go source file before adding `?ts=4`:

![Before, tab space example](http://i.imgur.com/GIT1Fr0.png)

...and this is after adding `?ts=4`:

![After, tab space example](http://i.imgur.com/70FL4H9.png)

### Gists
[Gists](https://gist.github.com/) are an easy way to work with small bits of code without creating a fully fledged repository.

![Gist](http://i.imgur.com/VkKI1LC.png?1)

Add `.pibb` to the end of any Gist URL ([like this](https://gist.github.com/tiimgreen/10545817.pibb)) in order to get the *HTML only* version suitable for embedding in any other site.

Gists can be treated as a repository so they can be cloned like any other:

```bash
$ git clone https://gist.github.com/tiimgreen/10545817
```

![Gists](http://i.imgur.com/BcFzabp.png)

This means you also can modify and push updates to Gists:

```bash
$ git commit
$ git push
Username for 'https://gist.github.com':
Password for 'https://tiimgreen@gist.github.com':
```

However, Gists do not support directories. All files need to be added to the repository root.
[*Read more about creating Gists.*](https://help.github.com/articles/creating-gists/)

### Keyboard Shortcuts
When on a repository page, keyboard shortcuts allow you to navigate easily.

 - Pressing `t` will bring up a file explorer.
 - Pressing `w` will bring up the branch selector.
 - Pressing `s` will focus the search field for the current repository. Pressing Backspace to delete the “This repository” pill changes the field to search all of GitHub.
 - Pressing `l` will edit labels on existing Issues.
 - Pressing `y` **when looking at a file** (e.g. `https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.md`) will change your URL to one which, in effect, freezes the page you are looking at. If this code changes, you will still be able to see what you saw at that current time.

To see all of the shortcuts for the current page press `?`:

![Keyboard shortcuts](http://i.imgur.com/y5ZfNEm.png)

### Closing Issues via Commit Messages
If a particular commit fixes an issue, any of the keywords `fix/fixes/fixed`, `close/closes/closed` or `resolve/resolves/resolved`, followed by the issue number, will close the issue once it is committed to the master branch.

```bash
$ git commit -m "Fix screwup, fixes #12"
```


### Syntax Highlighting in Markdown Files
For example, to syntax highlight Ruby code in your Markdown files write:

    ```ruby
    require 'tabbit'
    table = Tabbit.new('Name', 'Email')
    table.add_row('Tim Green', 'tiimgreen@gmail.com')
    puts table.to_s
    ```

This will produce:

```ruby
require 'tabbit'
table = Tabbit.new('Name', 'Email')
table.add_row('Tim Green', 'tiimgreen@gmail.com')
puts table.to_s
```

### Images/GIFs
Images and GIFs can be added to comments, READMEs etc.:

```
![Alt Text](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)
```

Raw images from the repo can be used by calling them directly.:

```
![Alt Text](https://github.com/{user}/{repo}/raw/master/path/to/image.gif)
```

![Peter don't care](http://www.sheawong.com/wp-content/uploads/2013/08/keephatin.gif)


### Task Lists
In Issues and Pull requests check boxes can be added with the following syntax (notice the space):

```
- [ ] Be awesome
- [ ] Prepare dinner
  - [ ] Research recipe
  - [ ] Buy ingredients
  - [ ] Cook recipe
- [ ] Sleep
```

![Task List](http://i.imgur.com/jJBXhsY.png)

When they are clicked, they will be updated in the pure Markdown:

```
- [x] Be awesome
- [ ] Prepare dinner
  - [x] Research recipe
  - [x] Buy ingredients
  - [ ] Cook recipe
- [ ] Sleep
```
#### Task Lists in Markdown Documents
In full Markdown documents **read-only** checklists can now be added using the following syntax:

```
- [ ] Mercury
- [x] Venus
- [x] Earth
  - [x] Moon
- [x] Mars
  - [ ] Deimos
  - [ ] Phobos
```

- [ ] Mercury
- [x] Venus
- [x] Earth
  - [x] Moon
- [x] Mars
  - [ ] Deimos
  - [ ] Phobos


### Previous Branch
To move to the previous branch in Git:

```bash
$ git checkout -
# Switched to branch 'master'

$ git checkout -
# Switched to branch 'next'

$ git checkout -
# Switched to branch 'master'
```


### Git Resources
| Title | Link |
| ----- | ---- |
| Official Git Site | http://git-scm.com/ |
| Official Git Video Tutorials | http://git-scm.com/videos |
| Code School Try Git | http://try.github.com/ |
| Introductory Reference & Tutorial for Git | http://gitref.org/ |
| Official Git Tutorial | http://git-scm.com/docs/gittutorial |
| Everyday Git | http://git-scm.com/docs/everyday |
| Git Immersion | http://gitimmersion.com/ |
| Ry's Git Tutorial | http://rypress.com/tutorials/git/index |
| Git for Computer Scientists | http://eagain.net/articles/git-for-computer-scientists/ |
| Git Magic | http://www-cs-students.stanford.edu/~blynn/gitmagic/ |
| GitHub Training Kit | https://training.github.com/kit/ |
| Git Visualization Playground | http://onlywei.github.io/explain-git-with-d3/#freeplay |
| Learn Git Branching | http://pcottle.github.io/learnGitBranching/ |
| A collection of useful .gitignore templates | https://github.com/github/gitignore |

#### Git Books
| Title | Link |
| ----- | ---- |
| Pragmatic Version Control Using Git | https://pragprog.com/titles/tsgit/pragmatic-version-control-using-git |
| Pro Git | http://git-scm.com/book |
| Git Internals PluralSight | https://github.com/pluralsight/git-internals-pdf |
| Git in the Trenches | http://cbx33.github.io/gitt/ |
| Version Control with Git | http://www.amazon.com/Version-Control-Git-collaborative-development/dp/1449316387 |
| Pragmatic Guide to Git | https://pragprog.com/titles/pg_git/pragmatic-guide-to-git |
| Git: Version Control for Everyone | https://www.packtpub.com/application-development/git-version-control-everyone |

#### Git Videos
| Title | Link |
| ----- | ---- |
| Linus Torvalds on Git | https://www.youtube.com/watch?v=4XpnKHJAok8 |
| Introduction to Git with Scott Chacon | https://www.youtube.com/watch?v=ZDR433b0HJY |
| Git From the Bits Up | https://www.youtube.com/watch?v=MYP56QJpDr4 |
| Graphs, Hashes, and Compression, Oh My! | https://www.youtube.com/watch?v=ig5E8CcdM9g |
| GitHub Training & Guides | https://www.youtube.com/watch?list=PLg7s6cbtAD15G8lNyoaYDuKZSKyJrgwB-&v=FyfwLX4HAxM |

#### Git Articles
| Title | Link |
| ----- | ---- |
| GitHub Flow  | http://scottchacon.com/2011/08/31/github-flow.html |
