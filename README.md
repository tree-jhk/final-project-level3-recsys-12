# My Own Home — Personalized Furniture Recommendation Service

[한국어 원문](README.ko.md) · [English project wiki](docs/wiki/Home.md) · [Demo](https://youtu.be/JuKz3PUd5xo) · [Presentation](https://www.youtube.com/watch?v=rJuBYWqGv-g)

<p align="center"><img src="https://user-images.githubusercontent.com/67851701/216806796-d05452c4-bdf4-4f8d-a126-ef3dad2cedcb.png" width="600"></p>

A five-person **NAVER Boostcamp AI Tech** project built in early 2023. My Own Home helps users discover furniture that matches their preferences instead of repeatedly exposing them to the most popular products.

**Status:** The beta service has ended. This fork provides English documentation for the original team project, not a newly deployed service. The Korean interface and original figures are intentionally retained.

**Attribution:** Developed by **Team RAYN — Recommendation is All You Need**. [Original repository](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12). English documentation is maintained in Junhyuk Kwon's fork; the original repository is unchanged.

## How it works

1. A new user selects interior photographs they like. Associated products provide an initial preference signal.
2. **Multi-DAE**, a denoising autoencoder, takes a preferred-item vector and scores products without requiring a previously trained user ID.
3. Users like products and request refreshed recommendations as their preferences become clearer.
4. Product pages expose related products through product-name clustering.

<img src="https://user-images.githubusercontent.com/67851701/216807924-682433cb-2bd5-42de-9236-76639df1e729.png" width="900">

## Engineering decisions and findings

| Challenge | Approach | Result / finding |
| --- | --- | --- |
| Sparse, popularity-skewed interactions | Select Multi-DAE against personalization, new-user support, sparse-data learning and inference-speed requirements | Accepts a preference vector for newly onboarded users |
| Offline accuracy plateau hid repetitive recommendations | Inspect service recommendations; add catalog-coverage monitoring and extend training | Diversity and accuracy improved; a web A/B test compared diversity satisfaction against a popularity baseline |
| Expensive product-name comparisons | Sort names and compare within a sliding window instead of every pair | Similarity-calculation time: **15 hours → 10 minutes** |
| Similar names could merge unrelated products | Depth-limited BFS; autoencoder-compressed category/seller features and a Random Forest quality check | **81 / 2,630 clusters** flagged for inspection: **3.1%**, not a measured misclassification rate |

See [Data](docs/wiki/Data.md), [Model](docs/wiki/Model.md) and [Image-based cold start](docs/wiki/Cold-Start.md) for original figures and design details. The training matrix was approximately **99.96% sparse**. Products in interior posts were treated as implicit preferences, not independently verified purchases or explicit ratings.

## Junhyuk Kwon's contributions

This was a team project, not a solo application. Junhyuk's work included:

- Data analysis and preprocessing; product-name similarity, depth-limited BFS clustering and cluster-quality checks.
- Recommendation-model selection, training and evaluation, including repetition missed by accuracy metrics.
- Cloud model-artifact transfer and inference/A/B-test API integration with the web service.

Frontend, backend and database development were collaborative. Image-based cold-start work is described as **team work**, not Junhyuk's sole implementation.

## System architecture

<img src="https://user-images.githubusercontent.com/67851701/216807835-225f09bf-69f6-46e5-b53f-1c3150b0beb9.png" width="900">

**Svelte / Vite** frontend · **FastAPI / Poetry** backend · **MySQL** database · **PyTorch** recommender · **Google Cloud Storage** model artifacts.

Docker deployment redesign, Jenkins security checks and parts of the automation pipeline were **future work**, not completed production infrastructure.

## Repository guide

| Folder | Contents |
| --- | --- |
| [EDA](EDA/README.md) | Exploration, product-name similarity and clustering |
| [crawling](crawling/README.md) | Collection and preprocessing |
| [model](model/README.md) | Autoencoder training and inference |
| [backend](backend/README.md) | API, services, database integration and inference |
| [frontend](frontend/README.md) | Svelte interface |
| [database](database/README.md) | Schema and management scripts |
| [gcp](gcp/README.md) | Model-artifact transfer |
| [English wiki](docs/wiki/Home.md) | Project decisions, troubleshooting and collaboration; figures unchanged |

Commands reflect the **2023 environment**. Private datasets, checkpoints and cloud/database credentials are not included; the retired service cannot be recreated with a single command.

## Team

| Member | GitHub |
| --- | --- |
| Taehun Kang | [thkyang324](https://github.com/thkyang324) |
| Junhyuk Kwon | [tree-jhk](https://github.com/tree-jhk) |
| Daeun Kim | [daeni-dang](https://github.com/daeni-dang) |
| Jisoo Ryu | [JisooRyu99](https://github.com/JisooRyu99) |
| Youngseo Yoo | [7dudtj](https://github.com/7dudtj) |

## Further reading

- [Presentation slides (Korean)](나만의집%20발표%20자료.pdf)
- [Original wrap-up report](https://dear-queen-578.notion.site/Final-Project-Wrap-Up-Report-99d475442c304775804d41523113e385)
- [English wiki](docs/wiki/Home.md)
- [Original Korean wiki](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki)
