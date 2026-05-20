# 🛍️ Product Catalog

**Feature:** Search, Filters & Product Detail  
**Environment:** Staging | Chrome 124  
**Tested by:** Paola Fermin

---

## 1. Search

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PROD-01 | Search for an existing product | 1. Go to the home page <br> 2. Type "wireless headphones" in the search bar <br> 3. Press Enter | Results page shows matching products with name, price, and image | ✅ Pass |
| PROD-02 | Search with no matching results | 1. Go to the home page <br> 2. Type "xyznotaproduct123" in the search bar <br> 3. Press Enter | Message displayed: "No results found for your search" | ✅ Pass |
| PROD-03 | Search with empty input | 1. Go to the home page <br> 2. Click the search bar without typing <br> 3. Press Enter | No navigation occurs; search bar shows placeholder or validation hint | ❌ Fail — page reloads with all products listed |

---

## 2. Filters

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PROD-04 | Filter by category | 1. Go to product listing page <br> 2. Select "Electronics" from category filter <br> 3. Observe results | Only electronics products are displayed | ✅ Pass |
| PROD-05 | Filter by price range | 1. Go to product listing page <br> 2. Set price range: $20 – $60 <br> 3. Apply filter | Only products within that price range are shown | ✅ Pass |
| PROD-06 | Apply multiple filters simultaneously | 1. Go to product listing page <br> 2. Select category "Electronics" <br> 3. Set price range $20 – $60 <br> 4. Apply both filters | Results show only electronics within the price range | ❌ Fail — price filter not applied when category is already active |

---

## 3. Product Detail

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PROD-07 | View product detail page | 1. Search for a product <br> 2. Click on a result | Detail page shows: name, price, description, images, stock status, and "Add to cart" button | ✅ Pass |
