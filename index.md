---
title: Git++
theme: blood
css: index.css
template: index.html
---

# Git++

----

De la gestion de versions à CI/CD : des pratiques peu répendues, parfois inconnues

Notes:
* Inneficient collaborative development.
* No traceability of sources and their history.
* No unit tests and automated integration tests.
* No CI/CD.
* First steps towards DevOps culture.

----

Je ne suis pas développeur !

Notes:
* The scripts, configuration and documentation are also source code.
* The Civil Code under Github.

---

## `git`

----

Gestion de versions décentralisé

----

```bash
git help
git help help
```

----

```bash
mkdir my-project/ && cd my-project/

git init .
```

----

```bash
git add .
git add <filename>
git add -p
```
```bash
git status
```
```bash
git commit -m "commit message"
```

![](images/git-trees.png)

Notes:
* You can propose changes (add it to the Index) using `git add <filename>` and `git add *`.
* This is the first step in the basic git workflow.
* To actually commit these changes use `git commit -m "commit message"`.
* Now the file is committed to the *HEAD*, but not in your remote repository yet.
* Your local repository consists of three "trees" maintained by git.
* The first one is your Working Directory which holds the actual files.
* The second one is the Index which acts as a staging area and finally the *HEAD* which points to the last commit you've made.

----

```bash
git push origin master
```
```bash
git remote add origin <server>
```

Notes:
* Your changes are now in the *HEAD* of your local working copy.
* To send those changes to your remote repository, execute `git push origin master`. Change *master* to whatever branch you want to push your changes to. 
* If you have not cloned an existing repository and want to connect your repository to a remote server, you need to add it with `git remote add origin <server>`.
* Now you are able to push your changes to the selected remote server.

----

```bash
git checkout -b <branch>
git checkout master
git branch -d <branch>
```
```bash
git push origin <branch>
```

Notes:
* Branches are used to develop features isolated from each other.
* The *master* branch is the "default" branch when you create a repository.
* Use other branches for development and merge them back to the *master* branch upon completion.
* A branch is not available to others unless you push the branch to your remote repository.

----

```bash
git pull
```
```bash
git merge <branch>
```
```bash
git rebase -i 1b2e1d63ff
git rebase <branch>
```

![](/images/git-branches.png)

Notes:
* To update your local repository to the newest commit, execute `git pull` in your working directory to fetch and merge remote changes.
* To merge another branch into your active branch (e.g. *master*), use `git merge <branch>`.
* In both cases git tries to auto-merge changes.
* Unfortunately, this is not always possible and results in conflicts.
* You are responsible to merge those conflicts manually by editing the files shown by git.
* After changing, you need to mark them as merged with `git add <filename>`.
* Before merging changes, you can also preview them by using `git diff <source_branch> <target_branch>`.

----

```bash
git tag 1.0.0
git tag 0.9.0 1b2e1d63ff
```

Notes:
* It's recommended to create tags for software releases.
* This is a known concept, which also exists in SVN.
* You can create a new tag named 1.0.0 by executing `git tag 1.0.0 1b2e1d63ff` the *1b2e1d63ff* stands for the first 10 characters of the commit id you want to reference with your tag.
* You can get the commit id by looking at the log...

----

```bash
git log
git log --author=le-garff-yoann
```

Notes:
* In its simplest form, you can study repository history using `git log`.
* You can add a lot of parameters to make the log look like what you want.
* To see only the commits of a certain author: `git log --author=bob`.
* To see a very compressed log where each commit is one line: `git log --pretty=oneline`.
* Or maybe you want to see an ASCII art tree of all the branches, decorated with the names of tags and branches: `git log --graph --oneline --decorate --all`.
* See only which files have changed: `git log --name-status`.
* These are just a few of the possible parameters you can use.
* For more, see git `log --help`.

----

```bash
git checkout -- <filename>
```
```bash
git fetch origin
git reset --hard origin/master
```

Notes:
* In case you did something wrong, which for sure never happens, you can replace local changes using the command `git checkout -- <filename>`.
* This replaces the changes in your working tree with the last content in *HEAD*.
* Changes already added to the index, as well as new files, will be kept.

* If you instead want to drop all your local changes and commits, fetch the latest history from the server and point your local *master* branch at it like this:
```bash
git fetch origin
git reset --hard origin/master
```

----

```bash
git config user.name le-garff-yoann
git config user.email pe.weeble@yahoo.fr
```

----

```bash
git clone https://github.com/torvalds/linux.git
```

---

### Un remote. C'est quoi ?

----

Versions d'un repository qui est hébergée sur Internet ou le réseau

Notes:
* 
It is possible to have several remote configured for the same repository.

----

Ces repository sont souvent hébergés sur des plateformes collaboratives voir des usines logicielles (GitLab, suite Atlassian, ...)

![](/images/remote-logos.png)

---

### Pull request et workflows Git

----

Les pull requests permettent de proposer des modifications sur un remote

Ces dernières sont généralement discutées, corrigées et testées avant d'être mergées

----

Des plateformes, comme [GitHub](https://github.com/OpenNebula/one/pull/2167), proposent ce mécanisme</h2></a>

----

Certains workflows Git, comme [GitHub Flow](https://guides.github.com/introduction/flow/), s'appuient sur cette fonctionnalité

Notes:
* Do not forget to mention gitflow.

---

### CI/CD

----

* **Continuous Integration/CI**
  * Code
  * Build
* **Continuous Delivery/CD**
  * Integrate
  * Release

----

* **Continuous Deployment**
  * Deploy

----

Un exemple vaut mieux qu'un long discours

Notes:
* Use the "Fork me" ribbons.

---

### Ressources

----

* [Git community book](https://book.git-scm.com/)
* [Git - petit guide](http://rogerdudler.github.io/git-guide/index.fr.html)
* [GitHub Flow](https://guides.github.com/introduction/flow/)
* [AngularJS git commit message conventions](https://gist.github.com/stephenparish/9941e89d80e2bc58a153)
* [Semantic versionning](https://semver.org/)
* [Git for Windows](https://gitforwindows.org/)
* [Documentation GitLab](https://docs.gitlab.com/)
* [CI/CD](https://en.wikipedia.org/wiki/CI/CD)
* [DevOps](https://en.wikipedia.org/wiki/DevOps)

Notes:
* Pull request in the pipe : Add `* [Le Code Civil sous GitHub](https://www.numerama.com/magazine/32646-le-code-civil-sous-github-pour-mieux-lire-ses-evolutions.html)` to this presentation.
