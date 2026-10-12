# Project conventions

The team standardized labels, milestones, issues and pull requests to make collaboration systematic.

## Labels

Labels identify the domain and nature of requested work.

<img src="https://user-images.githubusercontent.com/67851701/217255139-01b50583-cf66-436a-a8d9-6493921c8675.png" width="600">

## Milestones

The project grouped work into five broad areas and used milestones to track progress.

<img src="https://user-images.githubusercontent.com/67851701/217255952-f8f44e75-a353-4c91-856b-663d2e99b983.png" width="1000">

**Milestone descriptions:** Serving = deployment with GCP/Docker; Front-end = Svelte interface; Data = crawling, EDA and database work; Back-end = FastAPI implementation; Model = models used by the project. The progress bars and closed/open counts are the status at the time of the screenshot.

## Issues

Issues track ideas, feedback, tasks and bugs, and provide a place to discuss problems together.

### How the team filed an issue

<img src="https://user-images.githubusercontent.com/67851701/217257456-a82dad59-5974-49ad-85ef-3ba58d37108a.png" width="1000">

**Highlighted instructions:** Fill in the issue template; assign yourself; select appropriate labels, project board and milestone. These fields connect a task to its owner and project area.

1. Create an issue when a problem appears.
2. Follow the issue template.
3. Assign yourself.
4. Select relevant labels.
5. Link the project board.
6. Set the appropriate milestone.
7. Share the issue through Slack or KakaoTalk.

### Example

<img src="https://user-images.githubusercontent.com/67851701/217258082-588de431-9cd7-4338-9021-f2255787ecc8.png" width="1000">

**Example issue translation:** After liking an item and requesting new recommendations, unrelated new products incorrectly appear liked. Reproduction: refresh recommendations → like a recommended item → refresh again. The note diagnoses a component initialized only on the first page load and proposes re-rendering it when data changes, using a keyed block.

## Pull requests

The template makes proposed changes consistent and readable. PRs let teammates review/discuss changes and add follow-up commits before integration.

### Team procedure

<img src="https://user-images.githubusercontent.com/67851701/217260192-7b69f347-958d-46d9-a247-52181eb8c2a8.JPG" width="1000">

**Highlighted instructions:** Fill in the PR title, date, change description and cautions; request review from a same-domain teammate and the PM; assign yourself; select relevant labels, project board and milestone.

1. Open a PR when work is ready for integration.
2. Follow the template.
3. Include one same-domain teammate and the PM as assignees/reviewers.
4. Select labels, project board and milestone.
5. Share the PR through Slack or KakaoTalk.

The original note says to open a PR for changes to `main`; see [Git Flow](Git-Flow.md) for the development/release branch strategy introduced during the project.

### Example

<img src="https://user-images.githubusercontent.com/67851701/217260740-7cf68b06-b4ae-48d0-988f-87050fbe54de.png" width="1000">

References: [GitHub Issues](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues), [Pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Project-Convention)
