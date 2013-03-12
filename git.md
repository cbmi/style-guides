# Git

### Branching

Follow the [git branching model](http://nvie.com/posts/a-successful-git-branching-model/)

- `master` is for releases
- `develop` should generally not be worked on directly unless they are non-functional or trivial changes and apply project-wide
    - `develop` acts as the _staging_ branch for CI and should be as stable as master
- Create separate branches for each feature and isolate set of fixes
- Each feature should branch off `develop` unless the branch depends on an existing _unmerged_ feature/bug-fix branch

### Merging

- To prevent noise in the `develop` and `master` branches, feature/bug-fix merges will be squashed unless there is a good reason to keep the history, in which case the branch owner must rebase against `develop`
    - Read about the difference [here](http://stackoverflow.com/a/2427520/407954).
- The maintainer/release manager of the project is responsible for reviewing the feature/bug-fix branch and merging it into `develop`, then ultimately `master` when a release occurs

### Commit Messages

- Commit messages should be _present tense_ since the commit message is a description of what _has_ happened (in that commit), not what _had_ happened
    - e.g. "Fix missing local reference to `foo`", not "Fixed" or "Fixing"
- If a commit is intended to be visible in the history, it must have a meaningful commit message
    - This _should not_ require others to look at the code to generally understand what changed
- For bad commits that require a subsequent "fixed", "fixing", "whoops" commit message use `git commit --amend` to ammend the previous commit
    - On a side note, if you already pushed the commit you need to ammend, you can do `git push --force` for _your_ branch to force overwriting thte commit on the server. Be aware of the impact of this if other developers are working on the same branch.
