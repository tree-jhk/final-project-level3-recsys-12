# Data

- [Overview](#overview)
- [Collection and updates](#collection-and-updates)
- [Characteristics](#characteristics)
- [Product-name clustering](#product-name-clustering)
- [Cluster-quality checks](#cluster-quality-checks)
- [ERD](#erd)

## Overview

<img width="400" src="https://user-images.githubusercontent.com/97151660/217165143-ce00a149-7e5e-4998-a764-3c9e42e1a30b.png">

**Figure translation:** 'Items used by the user in their interior.' Products attached to an author's home-tour post are linked to that author to form implicit user–item interactions.

Ohouse users publish interior-tour posts. Products associated with each post were treated as items the author preferred, providing **implicit user–item interactions**. This is a modeling assumption, not independent verification that every product was purchased or explicitly liked.

## Collection and updates

### Access checks

The team checked `robots.txt` before collection. This historical check is not blanket authorization for current scraping; terms and policies must be checked separately.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217172148-3a8968fd-9b5e-4a13-a6c1-73ce38301233.png">

### Pipeline

The collection pipeline reduced collection time by organizing dependencies between identifiers and detailed records.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217169432-2fc9fc2c-1bf7-4516-9bfb-4748837dcc03.png">

**Flowchart translation:** Interior posts → Selenium → post IDs. From each post ID, Beautiful Soup (`Bs4`) retrieves post details and image IDs, while Selenium retrieves furniture IDs. Beautiful Soup then retrieves image details and furniture details from their respective IDs.

### Collection procedure

1. Collect interior-post IDs from the listing page.
2. Collect related photograph and product IDs for each post.
3. Retrieve detailed records using those identifiers.

<img width="600" src="https://user-images.githubusercontent.com/97151660/217196394-58052b72-75f7-49d8-8524-67274dfa0b7c.png">

**Screenshot translation:** 'View products' opens 'Products used in this home.' The arrows show two detail lookups: interior photographs from a home-tour post, and product records from its associated product list. The example lamp's name and price are incidental to the collection procedure.

### Incremental updates

New posts appeared at the top with a `New` label. The updater first checked the top three posts, then collected newly discovered products and photographs rather than recrawling all data.

<img width="600" src="https://user-images.githubusercontent.com/97151660/217198324-08ba2c44-5ae5-476b-9c70-af07bae21f58.png">

## Characteristics

### Extremely high sparsity

The user–item matrix was **99.96% sparse**: almost all possible pairs were unobserved. The figure visualizes a subset covering 10% of items.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217179649-e07d8276-41fb-4eaa-84ae-268eda027b1a.png">

### Long-tail popularity

A small fraction of items—reported as 0.41%—received disproportionately many interactions. Training on this imbalance could favor popular products over personalization.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217182310-24717c4a-56cc-4509-b2f8-813c1f9a7bb8.png">

**Chart annotation:** 'A small fraction of items (0.41%) has disproportionately many interactions = an imbalance problem.' Item popularity is concentrated in a small part of the catalog.

## Preprocessing

String cleaning, KoNLPy and Keras `text_to_word_sequence` converted text into a form suitable for processing.

## Product-name clustering

### Overview

<img width="600" src="https://user-images.githubusercontent.com/97151660/217184203-1e5a718e-1a71-4e57-910c-d196bf287a22.png">

**Pipeline translation:** Product names → sorting → vectorization → similarity calculation for the nearest `k` names in a sliding window → distance-aware clustering with BFS → similar-product suggestions. The bottom-right interface asks, 'How about these products?'

### Similar names, different variants

Some products have similar names but differ in color, size or shape. Grouping related variants supports similar-product browsing, but does not establish exact product identity.

<img width="600" src="https://user-images.githubusercontent.com/97151660/217184600-6681af53-3a9d-4c54-a867-a3ba169af367.png">

**Example names:** The left pair is 'INDIRA bedspread' and 'INDIRA bedspread, white, 230 × 250 cm.' The right group contains 'ezbo hero shelf/bookcase' variants with different model identifiers. Similar wording can describe different colors, sizes or configurations, so name similarity alone does not prove exact identity.

### Name similarity

Names averaged approximately 19 characters. Short strings did not work well with the team's TF-IDF, bag-of-words and word2vec approaches. The team used character-level Gestalt pattern matching through Python's [difflib](https://docs.python.org/3/library/difflib.html) to obtain numerical similarity scores.

### Reducing similarity-calculation cost

<img width="400" src="https://user-images.githubusercontent.com/97151660/217188936-c5663e15-d777-40b1-a769-b0db043e00f2.png">

**Figure explanation:** Sorting brings related product names closer together. The highlighted names include blankets and slippers sharing words such as 'warm' and 'fiber'; only nearby names are compared afterward. The colored boxes illustrate candidate comparisons, not verified matches.

Comparing every pair required quadratic pair comparisons and took **15 hours**. Sorting names and comparing only nearby names within a sliding window reduced the pair-comparison count to approximately `O(n × k)` and runtime to **10 minutes**. Sorting and the string-comparison cost remain separate components; this is not an exact-duplicate guarantee.

### Similarity graph and BFS

<img width="400" src="https://user-images.githubusercontent.com/97151660/217189668-6ad1dea9-89ba-49f6-8de0-e738df74daf2.png">

**Figure labels:** The table maps 'product name' to 'similar product names' and similarity scores. The diagrams show 'cluster group 0' and 'cluster group 1'; red crosses mark traversal paths that are cut off to prevent indirect similarity chains from merging too many products.

Build an undirected similarity graph and group related products with BFS. Limit traversal depth to avoid including distant neighbors through overly long chains; cover all nodes.

### Service example

<img width="400" src="https://user-images.githubusercontent.com/97151660/217194991-9986f9ac-75e0-49d8-bfd7-e0757c4c62b4.png">

**On-screen label:** 'How about these products?' Beneath a glass-vase detail view, the service displays related vase products from the similarity group.

## Cluster-quality checks

### Cluster summary

- Products in groups of at least two: **6,008**.
- Multi-product clusters: **2,630**.
- Mean products per cluster: **2.284**.

Example five-product group and its photographs:

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289223-0b8b88b1-ea5d-49ad-9f42-b3033f043a81.png">

**Table explanation:** The product names describe Persian-style rug variants from one seller, with different patterns, sizes, ratings and review counts. This is a coherent-looking group used to illustrate cluster inspection, not a labeled matching benchmark.

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289414-124d643b-436a-4309-8707-45127cbcb018.png">

### Features

Category hierarchy supplied **1,003 category features**, represented as multi-hot vectors. Similar names can nevertheless belong to different categories.

<img width="100" src="https://user-images.githubusercontent.com/97151660/218289252-e898ab3c-1379-452d-9c34-e49cfad188c2.png">

**Category translation:** Furniture → drawers/storage cabinets → kitchen storage → upper/lower cabinets. These hierarchical category labels become features for checking whether similarly named products belong together.

Seller IDs supplied approximately **12,000 seller features**, represented as one-hot vectors. Products in a group often share a seller, though not always.

### Compression and consistency model

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289255-836cd43b-9b2d-4cc1-bce9-6256adcd1d2e.png">

**Illustrative checklist:** 'Is your name RX9?', 'Are you a robot?', 'Do you cost over KRW 300,000?', 'Are you white?', 'Are you from this brand?', and a humorous final question. The first two examples have one 'No'; the third has three and is rejected. This cartoon explains checking consistency across multiple attributes; it is not the actual Random Forest decision rule.

An autoencoder compressed the sparse feature representation to **100 dimensions**, with reported reconstruction MSE **0.000100418**. A **Random Forest regressor** then checked cluster membership using labels 0/1 for the target and comparison groups.

### Procedure

1. Choose a comparison cluster with the same item count.
2. Train the Random Forest using products from the target and comparison clusters.
3. Check predictions for the target cluster; flag a cluster if any relevant prediction is below 0.5.

This is a heuristic consistency check, not an independently labeled test of matching accuracy.

### Results and review candidates

- Flagged clusters: **81 of 2,630**, or **3.080%**.
- Products inside flagged clusters: **425**.
- The flags focus manual inspection on approximately **3.1%** of clusters; they do **not** establish a 3.1% true error rate or validated precision/recall.

Two flagged examples, each followed by the corresponding photographs:

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289269-89e852b5-750f-4420-8595-fedf7e48ccf5.png">

**Flagged category labels, top to bottom:** Standard dressing table; storage cabinet; bookcase; bedside table; bookcase. Their names share the same product-line prefix, but the category differences reveal a potentially over-merged cluster.

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289474-43c78f90-cecc-4693-80f5-52f927df2b37.png">

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289290-0b54205a-1b19-4751-a6b2-2e1350692385.png">

**Flagged category labels, top to bottom:** Stool/bench; chair; display cabinet; storage dressing table; standard dressing table. The shared product-line name has grouped functionally different furniture, making this cluster a candidate for manual review.

<img width="400" src="https://user-images.githubusercontent.com/97151660/218289485-8c1785ec-16d1-475d-9ce4-15f053c6c8b8.png">

The original note proposed removing the flagged clusters. Human review is needed before treating all flags as definite errors.

## ERD

<img width="800" src="https://user-images.githubusercontent.com/97151660/217198844-86918cef-c646-4577-8597-f299fc5bc4dc.png">

**Diagram translation:** `item` = products; `cluster_item` = product-cluster membership; `card` = interior photographs; `house` = home-tour posts; `house_item` = products associated with a post; `house_color` = interior color features; `member` = service users; `member_prefer` = liked products; `inference_result` = recommendation results. Post IDs connect photographs and products, while member emails connect preferences and recommendations. See the [ERD page](https://github.com/tree-jhk/final-project-level3-recsys-12/wiki/ERD) for the field glossary.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EB%8D%B0%EC%9D%B4%ED%84%B0)
