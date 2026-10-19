# Module 9
## Audit metrics, code, and claims

### The repo

Open `09-audit` in VS Code. In its terminal, run:

```text
uv sync --frozen
```

Select the repository's `.venv` Python kernel. Open `module09_in_class.ipynb`. The datasets are included in the notebook; there is nothing to download. Use `additional-syntax.md` when you need a short syntax example.

For each example, predict the result, run the code, and explain any difference. Review answers in `module09_in_class_worked_examples.ipynb` afterward.

### 9.1 What are we checking?

| Check | Ask |
| --- | --- |
| Purpose | Who uses this result? What decision will it support? |
| Definition | What is one observation? Who qualifies? Over what period? |
| Calculation | Does the code compute that definition? |
| Evidence | Can I reproduce a small case independently? |
| Claim | What does this evidence establish, and what remains uncertain? |

Choose one number from your team app. What does it claim to measure?

<!-- writing-lines: 2 -->

What would you need to know before deciding whether it is correct?

<!-- writing-lines: 2 -->

<!-- pagebreak -->
## 9.2 Customer loyalty

A manager wants to compare customer loyalty across stores. The notebook contains six completed orders in January 2026.

| Store | Customer | Completed orders |
| --- | --- | --- |
| A | Ana | 3 |
| A | Ben | 1 |
| B | Cai | 2 |

### Predict two different answers

Compute both summaries. For the second, call a customer a repeat customer if they placed at least two completed orders in the month. Include only customers with at least one completed order at that store in that month.

| Store | Orders per customer | Repeat customers / customers | Repeat-customer share |
| --- | --- | --- | --- |
| A |  |  |  |
| B |  |  |  |

Which summary better fits the manager's decision? What might either miss?

<!-- writing-lines: 2 -->

### Inspect the denominator

The notebook divides the number of repeat customers by the number of orders. Identify the unit of each count. Explain whether this computes the agreed share, then correct it.

<!-- writing-lines: 2 -->

### Try a boundary case

Add store C with two customers who each placed one order. What share should C have? What if a store has no qualifying customers?

<!-- writing-lines: 2 -->

A customer first buying on January 31 has less opportunity to return than one buying on January 1. Explain how this limits a claim about loyalty. Consider the small customer counts, too.

<!-- writing-lines: 2 -->

<!-- pagebreak -->
## 9.3 Average tip per visit

The visits table has one row per visit. For this first case, the data documentation says a blank tip means no tip, so it is treated as zero.

| Visit | Tip | Number of service rows |
| --- | --- | --- |
| A | $10 | 2 |
| B | blank (zero) | 1 |

### Predict before merging

What is the average tip per visit? Write the numerator and denominator.

<!-- writing-lines: 2 -->

After merging with the services table, visit A appears twice. List the three tip values that the merged table contains. What mean will the code produce?

<!-- writing-lines: 2 -->

### Test the unit of analysis

Add a third service to visit A without changing either tip. Predict both results.

| Calculation | Before the extra service | After the extra service |
| --- | --- | --- |
| Mean over merged rows |  |  |
| Mean per visit |  |  |

Where should the mean be calculated? Explain why your correction works.

<!-- writing-lines: 2 -->

### Change the meaning of missing

Now suppose the blank means the tip is unknown. Which number can you report, and what coverage should accompany it? Can you determine the mean for all visits?

<!-- writing-lines: 3 -->

<!-- pagebreak -->
## 9.4 Delivery performance

The business question is: what proportion of all eligible deliveries arrived on time?

| Store | On-time deliveries | Eligible deliveries |
| --- | --- | --- |
| A | 9 | 10 |
| B | 1 | 2 |

### Predict the summaries

| Summary | Your calculation | Expected result |
| --- | --- | --- |
| Store A rate |  |  |
| Store B rate |  |  |
| Mean of the two store rates |  |  |
| Overall delivery rate |  |  |

Which summary answers the question? What question does the other summary answer?

<!-- writing-lines: 2 -->

### Check independently

Represent the twelve deliveries as on-time or late values, without using the store-rate calculation. Compute the rate. Explain why this is a useful second check.

<!-- writing-lines: 2 -->

### Change the grouping

Split A into A1 with 5 on-time out of 5 and A2 with 4 on-time out of 5. No delivery changed. Which summary should stay the same? Predict the new unweighted average of store rates.

<!-- writing-lines: 2 -->

Before comparing real stores, define eligible deliveries, the on-time rule, the cutoff, and the treatment of missing outcomes. What could make a comparison misleading even when the arithmetic is correct?

<!-- writing-lines: 2 -->

<!-- pagebreak -->
## 9.5 A weighted lottery

This is a hypothetical mechanism, not a description of current immigration policy. Person A has one ticket and B has four. Shuffle all five tickets uniformly. Select distinct people in order of first appearance until all available slots are filled. A person can win at most once.

### Predict the probabilities

| Available slots | P(A selected) | P(B selected) | Sum of probabilities |
| --- | --- | --- | --- |
| 0 |  |  |  |
| 1 |  |  |  |
| 2 |  |  |  |

A proposed formula is `slots * weight / total_weight`. Apply it with two slots. What does the result tell you? Would clipping each probability to one repair the mechanism?

<!-- writing-lines: 3 -->

### Use a simulation as evidence

Read the provided simulation, then run it with its fixed seed. Identify where it shuffles tickets and where it prevents a person winning twice. Compare the estimated chances with your predictions.

<!-- writing-lines: 2 -->

With equal weights, how should the selection probabilities compare? What should their sum equal when slots do not exceed the number of people?

<!-- writing-lines: 2 -->

Simulation estimates vary with the number of runs and seed. The worked notebook includes an optional exact check of all 120 permutations of five labeled tickets.

<!-- pagebreak -->
## 9.6 Audit your team app

### What to hand in

Submit `my-audit.md` on Brightspace by the deadline on the course app's HW page. See `homework.md` for the audit requirements and team workflow.

Complete ten Practice Quiz 9 samples as specified in the assignment. The paper quiz is closed book: identify exactly two incorrect numbered lines, explain each mistake, and give corrected lines. Syntax from Modules 1 through 9 may appear.

### Vocabulary

| Term | Meaning |
| --- | --- |
| Unit of analysis | What one observation represents: customer, visit, delivery, or person. |
| Population | The people or records included in the calculation. |
| Denominator | The count or quantity against which the numerator is compared. |
| Proxy | A measurable substitute for a concept that is harder to observe. |
| Weighted average | An average in which observations or groups contribute different amounts. |
| Data cutoff | The latest time through which observations are included. |
| Boundary case | An extreme or special input that tests the definition or code. |
| Invariant | A property that should remain true when an irrelevant detail changes. |
| Independent check | A second way to obtain the expected result, avoiding the same logic. |

