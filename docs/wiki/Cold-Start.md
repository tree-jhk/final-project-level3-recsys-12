# Image-based cold start

The recommender takes an item-preference vector. How can it recommend furniture before a new user has any interaction history?

## Original onboarding

1. Collect interior photographs and their style labels from Ohouse posts.

<img width="700" alt="스크린샷 2023-02-07 오후 4 04 38" src="https://user-images.githubusercontent.com/111856748/217171937-e0f681e4-670d-4d9c-8452-11f9c7d47a23.png">

2. Sample five photographs from each of 11 styles: **55 photographs**.
3. Ask the user to choose at least five photographs they like.

<img width="700" alt="회원가입-기존" src="https://user-images.githubusercontent.com/111856748/217170404-5d5e067e-527c-42bc-8903-4206e563bf00.png">

4. Use associated products from preference-relevant categories, such as sofas and shelves, as initial liked items.

<img width="700" alt="스크린샷 2023-02-07 오후 4 09 03" src="https://user-images.githubusercontent.com/111856748/217172761-0c947e14-1dc0-4653-bbd7-95d437c82fec.png">

If none of the sampled images matches the user's taste, selection can become frustrating and users may leave.

## Problems with style-based sampling

Style labels were imbalanced.

<img width="600" alt="스타일별개수" src="https://user-images.githubusercontent.com/111856748/217194439-c2ec0f80-d784-410f-8830-8e7ead9a0642.png">

They were also subjective: an interior labeled “natural” might look “modern” to another person. Some photographs drew attention to people rather than the interior.

<img height="250" alt="내추럴이미지" src="https://user-images.githubusercontent.com/111856748/217195763-138bf3f5-0219-477d-916e-fb93159ea4e5.jpg">

<img height="250" alt="image" src="https://user-images.githubusercontent.com/111856748/217494239-e488040e-92db-45d3-beb9-d464df9d454e.png">

The team reframed the task: filter distracting images and organize remaining images by their visual content instead of relying only on style labels.

<img width="1000" alt="image" src="https://user-images.githubusercontent.com/111856748/217493363-128ebc70-647f-411f-876f-6e7f1be3f477.png">

## Method

### 1. Filter distracting images

Pretrained YOLO object detection provided a way to identify people and other objects. Not every detected object is noise: cats, pet furniture or other features can still be relevant. The initial version filtered **people**, leaving other categories for later investigation.

<img width="804" alt="image" src="https://user-images.githubusercontent.com/111856748/217535467-0d1e8b1e-dfda-4189-aacd-b467b1db2d97.png">

### 2. Learn image representations

Without reliable style targets, the team used a **convolutional autoencoder** to reconstruct the input image. An encoder produces a latent representation; a decoder reconstructs the image. Flattening and linear layers convert encoder outputs into a compact vector.

<img width="400" alt="CAE" src="https://user-images.githubusercontent.com/111856748/217256368-25ea93f1-f34d-4ffb-8642-0d3fed7af7d7.png">

t-SNE visualizations suggested that images with similar visual moods sometimes grouped together; this is qualitative evidence, not a validated measure of representation quality.

<img width="400" alt="스크린샷 2023-02-05 오후 5 30 07" src="https://user-images.githubusercontent.com/111856748/217487507-f44e7112-d9a9-4c58-ab03-05089e2c0d28.png">

### 3. Adapt the selection range

Initially show images from a broad range. After selections, compute their center in representation space and narrow the next sampling range as the number of selections grows. The original algorithm describes a selection-dependent parameter `n` and samples images within that distance of the center.

<img width="400" alt="스크린샷 2023-02-05 오후 5 30 07" src="https://user-images.githubusercontent.com/111856748/217488679-f907c891-5243-4a6a-8833-df9c0764529a.gif">

## Result

Early choices remained varied; subsequent choices increasingly reflected a similar interior mood.

<img width="900" alt="모델적용결과" src="https://user-images.githubusercontent.com/111856748/217203386-793e4613-5eb3-47a3-afa3-801a369b835b.png">

## Discussion

Products such as beds and sofas associated with selected interiors were treated as a new user's preferences. The original pool contained **over 80,000 images**. Showing 55 randomly sampled images at once was slow, imposed a fixed selection burden and risked lower attention to later images. Filtering and compact representations allowed more adaptive selection.

## Open questions

- Which distracting objects besides people should be filtered?
- Does the latent representation capture preference-relevant information?
- How should the service distinguish aesthetic preference from practical constraints, such as a studio resident selecting a photograph with a large sofa?


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/Cold-start-%EB%AC%B8%EC%A0%9C-%EA%B0%9C%EC%84%A0)
