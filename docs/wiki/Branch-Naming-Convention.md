# Branch naming

Team RAYN adopted naming conventions alongside Git Flow to make collaboration and branch purpose clearer.

## Default branch

Use `main` rather than `master`. Historical rename example:

```bash
# master branch의 이름을 main으로 바꾸는 명령어
git branch -m master main
```

## Feature branches

Use `feat/<task>` for individual development branches:

```bash
feat/db
feat/front
feat/back
```

## Experiment branches

Use `test/<experiment>`:

```bash
test/inference
test/login
```

## In practice

<img src="https://user-images.githubusercontent.com/67851701/217251960-838b83cf-15ea-44a7-8fcc-b0ba9d3a8968.png" width="300">


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Branch-Naming-Convention)
