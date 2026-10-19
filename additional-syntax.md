# Additional syntax for Module 9

These short examples support the audit practice. Read them before using the worked notebook. A method can be valid Python and still implement the wrong business rule.

```python
import pandas as pd
amount = pd.Series([20, -5, 15])
print(amount.clip(lower=0).tolist())  # [20, 0, 15]
print(amount.abs().tolist())          # [20, 5, 15]
```

`clip(lower=...)` replaces smaller values with the lower bound; `upper=...` caps larger values. `abs()` removes the sign. Neither is appropriate for refunds if you need net revenue. Preserve original values if later calculations need them.

```python
status = pd.Series(["paid", None, "open"], dtype=object)
print(status.fillna("paid").eq("paid").tolist())  # [True, True, False]
```

`.eq(v)` means `== v`; `.ne(v)` means `!= v`. `.gt(v)` and `.ge(v)` mean `>` and `>=`. If a blank means paid, fill it before the comparison. With object data, comparing first produces False for the blank; filling afterward does not repair that choice. Missing-value comparison behavior can also depend on dtype, so inspect it rather than relying on a blanket rule.

```python
visits = pd.DataFrame({"tip": [10, None]})
print(visits.dropna(subset=["tip"]))  # keeps only the recorded tip
print(visits["tip"].fillna(0).mean()) # 5.0, only justified if blank means zero
```

`dropna(subset=[...])` removes rows missing a value in the named columns. It changes the population; it does not establish that unknown values are zero.

```python
rate = pd.Series(["9%", "20%"])
print(rate.str.replace("%", "").astype(float).tolist())  # [9.0, 20.0]
print(pd.to_numeric(rate.str.replace("%", "")).tolist()) # [9, 20]
```

`astype(float)` converts to decimal numbers; `astype(int)` converts to integers when valid. `pd.to_numeric` is another way to parse numeric text. Remove the percent sign first. These values are percentage points, not proportions: divide by 100 if a later calculation requires 0.09 and 0.20.

The lottery notebook also uses standard Python `random.Random(seed)` and `shuffle` to permute entries reproducibly. The longer input-validation code and optional `itertools.permutations` exact check are supplied reference code, not new syntax students must memorize for this exercise.
