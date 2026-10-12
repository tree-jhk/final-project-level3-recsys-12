# fetchall() index error

The backend intermittently raised `IndexError: list index out of range` on its first execution, even though the author believed the index was valid.

The original author attributed this to garbage collection during `fetchall()` and recorded a `print(list)` workaround.

**Qualification:** This was an unverified diagnosis in the original development note. Printing a list is not established garbage-collection management or a general SQLAlchemy fix. The translation preserves what was reported without presenting it as a confirmed mechanism.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/SQLAlchemy-fetchall-%EC%98%A4%EB%A5%98)
