# Coding and comment conventions

## Code

- Python functions/variables use [snake_case](https://en.wikipedia.org/wiki/Snake_case).
- Classes use capitalized camel case (PascalCase).
- Use one statement per line.
- Add whitespace around operators and after commas.
- Use **black** for formatting and **isort** for import ordering.

```python
    pip install black
    pip install isort
```

## Docstrings

The team used the **autoDocstring** VS Code extension for consistent comments/docstrings.

<img src="https://user-images.githubusercontent.com/67851701/217250429-f6a75c6e-8ed2-4f1b-b8bc-8035912c3141.png" width="600">

Type three double quotes and press Enter to generate a template.

<img src="https://user-images.githubusercontent.com/67851701/217250730-a1d6e490-6554-4bfd-ba85-1bd4e7437470.png" width="300">

Describe the function in `Summary`, input types/purposes in `Args`, and outputs in `Returns`. Write for teammates who have not implemented that function.

## In practice

<img src="https://user-images.githubusercontent.com/67851701/217251191-6ec9e5e7-bfe5-43e2-b44b-4b5547776aeb.png" width="400">

**Screenshot translation:** The function checks whether a user has liked an item. `member_email` is the user's email address and `item_id` is the item identifier; it returns `False` when no matching preference record exists and `True` otherwise.

[Original reference](https://ui.toast.com/fe-guide/ko_CODING-CONVENTION)


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Coding-Convention)
