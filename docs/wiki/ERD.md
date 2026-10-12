# Entity–relationship diagram

Original database diagram; labels and image remain unchanged.

<img src = "https://user-images.githubusercontent.com/90206705/217548562-b4307377-438e-4b1c-9c25-5425eaf33a7a.png">

**Table glossary:** `item` = products; `cluster_item` = product-cluster membership; `card` = interior photographs; `house` = home-tour posts; `house_item` = post–product associations; `house_color` = interior color features; `member` = users; `member_prefer` = liked products; `inference_result` = recommendation results.

**Korean field labels:** Product metadata includes category, rating, reviews, price, title, seller, discount rate, image, availability, estimated price, cleaned title, similar-product list and cluster ID. Home-tour metadata includes space type, floor area, occupation, home category, household type, region, style, project duration, budget, renovation details, likes, bookmarks, comments and views. `card` stores image ID, associated post ID, image space/type, URL and whether a person is present. `house_color` stores color indicators for the overall interior (`main_*`), walls (`wall_*`) and floor (`floor_*`).

**Relationships:** A home-tour post connects to its photographs and products through IDs. Service members connect to their associated home profile through `house_id`, and to liked products and recommendation results through `member_email`. Product IDs join the preference/result records to product metadata and cluster membership.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/ERD)
