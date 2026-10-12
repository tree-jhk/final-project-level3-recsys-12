# Node.js and Ubuntu compatibility

## Problem

The development server used **Ubuntu 18**. Downloading the then-latest Node.js **v18** through `wget` produced a compatibility problem in that environment.

## Recorded workaround

```bash
conda install nodejs
```

Conda supplied a compatible **Node.js v16** build.

<img src = "https://user-images.githubusercontent.com/90206705/217526050-de1a9585-bf54-40fc-803a-f869679b619e.png" width="40%" height="20%">

This is a historical environment note, not a recommendation to use end-of-life versions today.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Node%EC%99%80-Ubuntu%EC%9D%98-%EB%B2%84%EC%A0%84-%EC%9D%B4%EC%8A%88)
