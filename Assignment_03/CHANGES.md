# Assignment 03 — CHANGES

**Name:** Paing Thu Kha Kyaw  **Student ID:** 6705140018

This is the written part of your submission. Explain **what you changed and why**, then record your **prompt log**. Keep before/after snippets to a line or two.

---

## 1 · What I changed
    
One row per change. Name the OOP concept and say how you checked the behaviour was unchanged.

| # | Code smell in the original | What I changed it to | OOP concept applied | How I verified behaviour was unchanged |
|---|---|---|---|---|
| 1 | Products were stored as tuples, so code accessed fields by position, such as `PRODUCTS[pi][1]`. | I created `Product` with `name`, `price`, `category`, and `tax_rate()`. | Class and encapsulation | The self-test compared the complete printed output and returned PASS. |
| 2 | Orders used nested tuples and item indexes instead of objects. | `Order` has a `Customer` and a list of `OrderItem` objects; each item has a `Product`. Constructors check names, prices, categories, quantities, and object types. | Composition and encapsulation | Ran `python Assignment_03.py`; it returned PASS. |
| 3 | The old `calc()` checked the tier with `if/elif` for both discounts and points. | `Customer`, `SilverCustomer`, `GoldCustomer`, and `PlatinumCustomer` hold their own rates and points multipliers. `Order` calls the customer methods. | Inheritance and polymorphism | PASS confirms the tier calculations still produce the same receipts. |
| 4 | `calc()` mixed calculations with receipt printing. | `Order.subtotal()`, `discount()`, `tax()`, `total()`, and `points()` return values; `receipt()` builds the text, and `refactored_main()` prints it. | Separation of responsibilities | The output comparison returned PASS, including receipt formatting and grand total. |
| 5 | The old calculation used numbers such as `10`, `0.03`, and `0.07` directly and declared `global TAXRATE`. | I used named constants in the new solution, such as `BULK_QTY_THRESHOLD`, `BULK_DISCOUNT_RATE`, and `TAX_RATE`. `Product.tax_rate()` handles food separately. | Encapsulation and clean code | PASS confirms the same tax and bulk discount results. The protected legacy code still contains its original `global`. |

## 2 · Short reflection (4–6 sentences)

The biggest improvement was giving `Order` separate methods for the subtotal, discount, tax, total, and points. In the old `calc()` function, those calculations were mixed with printing, which made it harder to follow. The new customer classes also make the different membership rules easier to find. I had to be careful with the `subtotal > 100` rule, the bulk discount at 10 items, and the order of the tax and discount calculation. I also kept the receipt text and blank lines the same, because the self-test compares the entire output.

---

## 3 · Prompt log (Level 2 — required)

Record **every** prompt where AI helped. If you wrote a part yourself, say so in one row. AI-shaped code with an empty log does **not** meet the Level-2 policy.

| # | My prompt to the AI | What it suggested (summary) | Accept / reject / edited | How I checked it |
|---|---|---|---|---|
| 1 | “Help me turn the product tuples into Product and OrderItem classes.” | Suggested objects for product details and item quantities. | Accepted and reviewed | Checked the class definitions and ran the self-test. |
| 2 | “How can the customer classes handle discounts and points without a tier if/elif?” | Suggested customer subclasses with their own rates and points multipliers. | Accepted and reviewed | Checked the customer classes; the self-test printed PASS. |
| 3 | “Help me separate the Order calculations from the receipt printing.” | Suggested methods that return numbers and a separate receipt method. | Accepted and reviewed | Checked that calculation methods do not print and ran the self-test. |
| 4 | “Tell me how to refactor the messy store code into a cleaner OOP program and keep the output exactly the same?” | Helped put the separate classes together into the finished program. | Accepted and reviewed | Ran `python Assignment_03.py`; the self-test printed PASS. |

**Ownership statement.** *By submitting, I confirm I understand and can explain every line of code I submitted, and that this prompt log reflects my actual AI use.*

---

## 4 · Before-you-submit checklist

- [x] `python Assignment_03.py` prints **PASS**.
- [x] No tuples / parallel lists left — products, orders, and items are objects.
- [x] No `if tier == ...` chains — tiers are a class family.
- [x] Calculation methods **return** values and do not `print`; printing is separate.
- [x] Constructors validate state; no leftover `global`; magic numbers are named.
- [x] The change table and reflection above are filled in.
- [x] The prompt log is complete and the ownership statement is signed.
