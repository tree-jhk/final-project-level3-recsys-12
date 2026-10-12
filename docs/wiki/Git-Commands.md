# Common Git commands

Historical command reference. Examples are documentation only; destructive commands must not be executed casually.

## Stage a file

```PowerShell
$ git add "file name"
```

Ask Git to track/stage the selected file.

## Commit

```
$ git commit -m "Fix: I fix error"
```

Create a commit from staged changes. The original note describes entering a multiline message before the closing quotation mark.

## Push

```
$ git push
```

Push the working branch. A first push may require `git push --set-upstream origin BRANCH_NAME`.

## Initialize a repository

```
$ git init
```

Create the `.git` directory and repository metadata.

## Switch branches

```
$ git checkout main
```

Switch to `main`.

```
$ git checkout -b "new branch name"
```

Create and switch to a branch.

```
$ git branch "new branch name"
```

Create a branch without switching.

## Inspect a commit

```
$ git checkout COMMIT_ID
```

Check out a selected commit; this can leave the repository in detached-HEAD state.

## Status and merge

```
$ git status
```

Inspect working-tree status.

```
$ git merge "branch name"
```

Merge the named branch into the current branch.

## Reset — destructive

```
$ git reset --hard COMMIT_ID
```

Moves the branch to a selected commit and discards tracked working-tree changes. Do not use without confirming scope and preserving needed work.

## Remove files from the index

```
$ git rm -r --cache .
```

The original snippet has a typo: the intended flag is `--cached`, not `--cache`. Recursive index removal is broad; prefer targeted `git rm --cached PATH` when updating ignore rules. Removing from the index does not remove a secret from prior commits.

## History

```
$ git log
```

Show commit history.

```
$ git log --oneline
```

Compact one-line history.

```
$ git log --oneline --graph
```

Graph view.

```
$ git reflog
```

Inspect local reference movements.

## Stash

```
$ git stash
```

Temporarily store eligible working changes.

```
$ git stash list
```

List saved entries.

```
// 가장 최근의 stash를 가져와 적용한다.
$ git stash apply

// stash 이름(ex. stash@{2})에 해당하는 stash를 적용한다.
$ git stash apply [stash 이름]
```

Apply a saved entry; the original comments describe the latest or a named entry.

```
// 가장 최근의 stash를 제거한다.
$ git stash drop

// stash 이름(ex. stash@{2})에 해당하는 stash를 제거한다.
$ git stash drop [stash 이름]

// apply + drop의 형태
$ git stash pop
```

`drop` removes a saved entry; `pop` applies it and removes it after successful application. Confirm which entry you are acting on.

## Amend

```
$ git commit --amend
```

Modify the latest commit, rewriting its identity. Coordinate before changing shared history.

[Original reference](https://gmlwjd9405.github.io/2018/05/18/git-stash.html)


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EC%9E%90%EC%A3%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-git-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%AA%A8%EC%9D%8C)
