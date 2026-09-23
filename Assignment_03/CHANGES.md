# Assignment 03 — CHANGES

**Name:** Paing Thu Kha Kyaw **Student ID:** 6705140018
This is the written part of your submission. Explain **what you changed and why**, then record your **prompt log**. Keep before/after snippets to a line or two.

---

## 1 · What I changed

| # | Code smell in the original | What I changed it to | OOP concept applied | How I verified behaviour was unchanged |
|---|---|---|---|---|
| 1 | Products were stored as bare tuples such as `("Laptop", 1200.0, "electronics")`. | Created a `Product` class with `name`, `price`, `category`, validation, and product tax behaviour. | Classes / encapsulation | Ran `python Assignment_03_completed.py` → PASS |
| 2 | Orders and items used nested tuples and numeric product indexes throughout the calculations. | Created `OrderItem` and `Order` classes. An `Order` has a `Customer` and many `OrderItem` objects; each item has a `Product`. | Composition / domain modelling | Self-test PASS and compared receipt output with the legacy behaviour. |
| 3 | Discount and points logic repeated `if/elif` checks for membership tiers. | Created a `Customer` base class plus `SilverCustomer`, `GoldCustomer`, and `PlatinumCustomer` subclasses with tier-specific rates and point multipliers. | Inheritance / polymorphism | Self-test PASS; there is no `if tier == ...` chain in the calculations. |
| 4 | Calculation and receipt printing were mixed together inside `calc()`. | Added pure methods such as `subtotal()`, `discount()`, `tax()`, `total()`, and `points()`. `receipt()` only builds the receipt text. | Pure functions vs modifiers / separation of concerns | Self-test PASS and checked that calculation methods do not print. |
| 5 | The legacy code contained magic numbers and a leftover `global TAXRATE`. | Added named constants such as `TAX_RATE`, `DISCOUNT_THRESHOLD`, `BULK_QTY_THRESHOLD`, `BULK_DISCOUNT_RATE`, and `POINTS_DIVISOR`; the refactored code uses no global statement. | Clean code / constants | Self-test PASS and reviewed the refactored section for magic business-rule values and `global`. |

## 2 · Short reflection (4–6 sentences)

The change that improved the code the most was replacing the membership `if/elif` chains with a family of customer classes. Each membership type now keeps its own discount rates and points multiplier, so the `Order` class does not need to know the details of every tier. Composition also makes the model easier to understand because an order contains a customer and order items, and each order item contains a product. Keeping the behaviour identical required me to be careful with the exact receipt text, rounding, tax rules, discount threshold, and blank lines. I used the provided self-test after the refactor and confirmed that it prints PASS, showing that the observable output is unchanged.

---

## 3 · Prompt log (Level 2 — required)

| # | My prompt to the AI | What it suggested (summary) | Accept / reject / edited | How I checked it |
|---|---|---|---|---|
| 1 | “pls answer all” (with `Assignment_03.py` and `CHANGES.md` uploaded) | Complete the required OOP refactor using domain classes, composition, constructor validation, polymorphic customer tiers, pure calculation methods, named constants, and complete the written change log. | Accepted and reviewed | Ran the supplied self-test and got `PASS - behaviour is unchanged. Your refactor is safe.` |
| 2 | I did not provide a separate prompt for individual methods; the complete solution was generated from the uploaded assignment requirements. | Preserve the legacy business rules and exact output while separating calculations from receipt formatting. | Accepted and verified against the assignment | Read the refactored code and ran `python Assignment_03_completed.py`; PASS. |
| 3 | I reviewed the generated answer rather than requesting another AI change. | No additional AI suggestion. | Reviewed | Checked the rubric requirements and self-test result before submission. |

**Ownership statement.** *By submitting, I confirm I understand and can explain every line of code I submitted, and that this prompt log reflects my actual AI use.*

---

## 4 · Before-you-submit checklist

- [x] `python Assignment_03_completed.py` prints **PASS**.
- [x] No tuples / parallel lists are used as the domain model in the refactored solution — products, orders, and items are objects.
- [x] No `if tier == ...` chains — tiers are a class family.
- [x] Calculation methods **return** values and do not `print`; printing is separate.
- [x] Constructors validate state; no leftover `global` in the refactored solution; magic business-rule numbers are named.
- [x] The change table and reflection above are filled in.
- [x] The prompt log is complete.
- [ ] Add your name and student ID, and make sure you personally understand every submitted line before signing/submitting.
