# Terminal customization

The team developed remotely on Linux through SSH in VS Code. A readable prompt can show time, path and branch, helping prevent work on the wrong branch.

## Display the date and time

Add the original prompt example to `.bashrc` and open a new terminal:

```bash
export PS1="\e[1;37m[\e[36m\D{%Y/%m/%d %H:%M:%S}\e[37m][\e[32m\u\e[31m\e[33m\e[37m]\e[34m\w\e[m\n\$"
```

<img src="https://user-images.githubusercontent.com/67851701/217790842-57df2aa4-410a-44bb-ad5a-846126241a2d.png" width="400">

## Timezone

The server initially displayed UTC; Korea uses UTC+9. The historical note suggested the following line:

```bash
export env TZ=KST-09:00:00
```

<img src="https://user-images.githubusercontent.com/67851701/217791459-b0ef844a-2964-4b93-8c52-5cefc8978f9c.png" width="400">

**Correction:** That historical `export env TZ=...` syntax should not be copied as shell guidance. For the intended timezone use `export TZ='Asia/Seoul'`; see the [Airflow timezone issue](Airflow-Troubleshooting.md#timezone-error).

## Show the Git branch

Add a branch-parsing function as illustrated:

<img src="https://user-images.githubusercontent.com/67851701/217792056-3a5c7183-8379-4c39-ba62-ed9a1c9fe265.png" width="800">

Then update the prompt to display its output:

```bash
export PS1="\$(parse_git_branch)\[\033[00m\] \e[1;37m[\e[36m\D{%Y/%m/%d %H:%M:%S}\e[37m][\e[32m\u\e[31m\e[33m\e[37m]\e[34m\w\e[m\n\$"
```

<img src="https://user-images.githubusercontent.com/67851701/217792408-28f7d6d3-850f-48e4-bc43-810b417bbfc5.png" width="600">

The team used branch visibility to reduce accidental work on the wrong branch. Displaying the active Conda environment can also help, although it was not adopted as part of this project.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EB%82%98%EB%A7%8C%EC%9D%98-%ED%84%B0%EB%AF%B8%EB%84%90-%EA%BE%B8%EB%AF%B8%EA%B8%B0)
