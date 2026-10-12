# UI & UX

The screenshots show the original Korean service. Numbered explanations describe controls in each figure.

## Visitor home page

<img src="https://user-images.githubusercontent.com/80964004/217172918-93a32efd-a22d-4454-bb35-46cef0486d88.png" alt="...">

**Interface labels:** 'Login', 'Furniture', 'These are popular products today', and 'Get personalized recommendations.' The My Own Home logo links back to the main page; heart controls record product preferences after sign-in.

1. The service logo returns to the main page.
2. The sign-in button opens the login page.
3. Interior products are grouped by category.
4. Visitors cannot like products or request personalized recommendations; these actions show a login-required message.

<img src="https://user-images.githubusercontent.com/80964004/217171994-c236b175-093d-4844-9cd0-88ae2be47c45.png" alt="...">

**Dialog translation:** 'Login is required. Would you like to log in?' Buttons: 'OK' and 'Cancel'.

## Signup: profile information

<img src="https://user-images.githubusercontent.com/80964004/217175293-b38f157c-f4e0-4e65-8f3e-149200c07c87.png" alt="...">

**Form translation:** 'Enter the type of home where the recommended furniture will be placed.' Fields: space type, household type and floor area (in Korean pyeong). Then: 'Enter the email address you will use to log in', 'Check email', and 'Please check whether this email is already registered.'

1. Enter space type, household type and floor area; dropdowns restrict selected fields.
2. Enter an email address. Email checking verifies its format and whether it is already registered.
3. A valid, unused email enables `Next!`.

<img src="https://user-images.githubusercontent.com/80964004/217174299-5b58e6e4-1bbd-442c-b5d0-8fd79887240f.png" alt="...">

**Success-state labels:** 'Enter the email address you will use to log in', 'Change email', and 'Please press [Next!]'. The screen shows the state after an email passes the form checks.

4. Continue to photograph selection.

## Signup: interior photographs

<img src="https://user-images.githubusercontent.com/80964004/217180601-63ab5ad8-465b-42ea-8567-33dabdc26a77.png" alt="...">

**On-screen instructions:** 'Select images you like. The more you select, the more personalized the results will be.' Bottom controls: 'Please select at least five', 'View more products', and 'Complete signup (0/5)'. These show the selection requirement and its running count.

1. Instructions explain that at least five photographs must be selected.
2. Photograph choices appear with a running selection count.
3. A next-images control reveals more options; selected images guide subsequent options toward the user's taste. After five next-page clicks the button changes as shown.

<img src="https://user-images.githubusercontent.com/80964004/217179001-07036c04-46db-4515-95f3-db134ae37710.png" alt="...">

**Button text:** 'View the next products >'. Supporting text: 'If you have finished selecting products, click below to complete signup.' This is the later signup state, when the completion control becomes relevant.

4. After at least five choices, signup can be completed. A confirmation reminds the user that this selection step will end.

## Sign-in

<img src="https://user-images.githubusercontent.com/80964004/217181261-4c605ab6-4f4a-4842-a7db-c2abe4307cb8.png" alt="...">

**Login labels:** 'Enter the email address used at signup', 'Email', 'Login', and 'Sign up'.

Enter the signup email; its format is checked. New users can follow the signup button.

## Member home page

<img src="https://user-images.githubusercontent.com/80964004/217183185-39512754-5d37-45d6-8a8a-f4d95cf21c25.png" alt="...">

**Member-page labels:** 'My Page', 'Logout', 'Get new recommendations', and 'We selected products you may like.' The helper text asks users to like products, explains that more likes refine recommendations, and points to My Page for reviewing liked items.

1. A heart marks a liked product and changes state.

<img src="https://user-images.githubusercontent.com/80964004/217182022-73483666-1303-4eea-8148-e9094d98e716.png" alt="..." width="15%">

**Product-card example:** Seller A.neuk; a domestically made tempered-glass living-room/sofa table; price KRW 71,700. The filled heart indicates that the user has liked this product.

2. Liked products can be reviewed on My Page.
3. `Get new recommendations` requests a refreshed result. Likes help refine preferences; new results are placed at the top.

<img src="https://user-images.githubusercontent.com/80964004/217182732-15c2f721-5bc6-4295-b2e7-97188fc24099.png" alt="..." width="50%">

**Section heading:** 'These are newly recommended products.' This row is inserted above existing recommendations after a refresh; where no price is available, cards say 'No estimated price information'.

4. A control returns to the top of the page.
5. A logout button ends the session.

## Product details

<img src="https://user-images.githubusercontent.com/80964004/217184719-a7206828-ad67-414e-8ac1-8245b79c95d3.png" alt="...">

**Product-detail labels:** Category path 'Furniture → Shelves → Freestanding shelves'; a solid-wood shelf offered in three colors; discounted price KRW 10,994; rating 4.7. The heart control records a preference for the displayed product.

1. View product information.
2. Express a preference from the detail page.

<img src="https://user-images.githubusercontent.com/80964004/217185654-7871738f-7025-4580-ad0b-c12e56245948.png" alt="...">

**Related-product section titles, top to bottom:** 'How about these products?' (similarity cluster); 'Products from the same series' (same-category products from the seller); and 'Popular freestanding shelves' (popular products in the category).

3. Browse products in the same similarity cluster.
4. Browse same-category products from the same seller.
5. Browse popular products from that category.

## My Page

<img src="https://user-images.githubusercontent.com/80964004/217185777-e64c3c86-8002-4fd3-825b-3c97e80f2cb7.png" alt="...">

**Liked-product examples:** A.neuk tempered-glass sofa table (KRW 239,000); IKEA MULIG clothes rack (KRW 24,900); modular furniture unit (KRW 215,000). Filled hearts identify items saved to My Page; these are product examples, not a recommendation-quality score.

Review previously liked products together.

## Loading and persistent controls

<img src="https://user-images.githubusercontent.com/80964004/217183539-1848cec5-d333-48ab-af87-83dd387012fc.png" alt="...">

**Loading-state text:** The underlying page asks users to like products to refine future recommendations and review them on My Page. The central spinner indicates that a recommendation refresh is in progress.

A loading screen indicates work in progress during operations that take time.

<img src="https://user-images.githubusercontent.com/80964004/217184207-41c1cf03-98ee-45cb-9ee6-68cf1865641b.png" alt="...">

**Persistent controls:** 'My Page', 'Logout', and 'Get new recommendations'. These controls remain accessible while the user scrolls the product list.

The menu bar and recommendation-refresh button remain accessible while scrolling.


---

[Wiki home](Home.md) · [Original Korean source](https://github.com/boostcampaitech4lv23recsys2/final-project-level3-recsys-12/wiki/UI%26UX)
