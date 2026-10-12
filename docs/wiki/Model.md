# Recommendation model

## Training data

### Interior-tour posts

Ohouse users publish posts introducing their homes.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217498091-97174c96-3d29-43a6-b86a-8f4d8bd21d9a.png">

Each post collects the products used in that interior.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217499421-860b32b9-f7b3-417a-bd04-b56757ad3676.png">

The team formed author–product interactions from these associations, assuming the products reflect the author's preferences. They are implicit signals rather than independently verified purchases.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217506734-6d0bcb4b-1fee-4797-8e51-534b1acd78d9.png">

## Inference data

### Image-based onboarding

New users choose interior photographs during signup.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217509127-d08442aa-aa51-4e07-8b35-765820a828b6.png">

Products associated with their selected interiors form an initial preference vector, which produces the first recommendations.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217509763-f65489d5-6762-41ab-a543-b7c67f530d4e.png">

### Refinement through likes

Liking a product adds it to the preference vector, allowing refreshed recommendations to incorporate further preference signals.

<img width="400" src="https://user-images.githubusercontent.com/97151660/217511710-440c04d7-5997-4519-b322-dfb98f5507e7.png">

## Initial approach: LightGCN

[LightGCN](https://arxiv.org/abs/2002.02126) simplifies [NGCF](https://arxiv.org/abs/1905.08108), retaining graph-based collaborative filtering through user–item connections.

<img width="300" src="https://user-images.githubusercontent.com/97151660/217512766-91732407-1011-4c91-8b27-2119034b0566.png">

The team considered its small parameter count attractive for efficient learning/serving. Because the original formulation depends on trained users, synthetic users were created by combining preferences to mimic selecting five interiors at signup.

### Why the approach was rejected

The data had **99.9599% sparsity** and a severe long tail. The team found that linking users through unpopular items would require deeper message passing, while deeper propagation risked oversmoothing. Changing graph depth did not solve the training issue in this setting. This is the team's empirical diagnosis, not a claim that LightGCN always fails on sparse data.

## Model-selection criteria

<img width="400" src="https://user-images.githubusercontent.com/80964004/217541410-a062f4e3-1e76-4aeb-a5f6-0a3ad629c7b8.png">

1. **Personalization:** reflect the user's preferences.
2. **New-user support:** accept preferred items without requiring a pre-trained user ID, termed “user-free” in the original notes.
3. **Sparse-data learning:** handle highly sparse interactions.
4. **Fast inference:** suitable response time for the service.

## Multi-DAE

<img width="400" src="https://user-images.githubusercontent.com/80964004/217542207-a4e721b9-0ade-4a9e-be30-5327bef556e3.png">

**Multi-Denoising Autoencoder** maps an item-preference vector through a dense latent representation to item scores. This lets the service score products for a new user from onboarding preferences. The team selected it against the four criteria above.

## Model performance and evaluation

NDCG@10 and Recall@10 changed little by approximately **200 epochs**, initially suggesting sufficient training.

<img width="500" src="https://user-images.githubusercontent.com/80964004/217543318-5702fab1-c50f-4ce0-9d0a-553f539f6441.png">

Service recommendations told a different story: similar items appeared regardless of the user's input preferences. Accuracy metrics alone had missed a personalization failure.

<img width="400" src="https://user-images.githubusercontent.com/80964004/217544033-248f89c6-96e2-408b-9bd1-2d36c342709e.png">

The team added **Diversity@10**, a catalog-coverage measure based on distinct items appearing among top-10 recommendations. It is not pairwise semantic diversity and was not a new training loss.

<img width="500" src="https://user-images.githubusercontent.com/80964004/217543757-4a51cf45-953b-4a0e-b489-7a4db5aae133.png">

Coverage continued increasing with training, motivating additional epochs. Eventually accuracy improved alongside coverage.

<img width="500" src="https://user-images.githubusercontent.com/67851701/229434322-e3b77c66-52fa-49aa-921e-477177d51162.JPG">

The updated model produced visibly more diverse recommendations in the service.

<img width="400" src="https://user-images.githubusercontent.com/80964004/217544635-83a6b462-beaf-4970-857b-738fe80c1a54.png">

The lesson: validate whether recommendations actually reflect different preferences instead of accepting an offline metric plateau as proof of successful personalization. The separate web A/B test compared satisfaction with recommendation diversity against a popularity-based recommender; ambiguous survey denominators are not reinterpreted here as a validated accuracy or business-impact statistic.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/%EB%AA%A8%EB%8D%B8)
