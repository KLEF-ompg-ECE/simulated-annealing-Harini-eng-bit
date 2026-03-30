# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** Sama Harini 
**Student ID    :** 2310040116
**Date Submitted:** 30 March 2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
The count_clashes() function calculates how many exam conflicts exist in the timetable. 
A clash occurs when exams that share students are scheduled in the same time slot. 
A perfect timetable has 0 clashes.
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
The generate_neighbor() function creates a new timetable by slightly modifying the current one. 
It usually moves one exam from its current time slot to another slot randomly. 
This produces a nearby solution that the algorithm can evaluate.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
This line decides whether the new timetable should be accepted or rejected. 
If the new timetable has fewer clashes it is always accepted. 
Sometimes a worse solution is accepted to help the algorithm escape local minima and explore better solutions.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric               | Your Result |
| -------------------- | ----------- |
| Number of iterations | 1379        |
| Start clashes        | 12          |
| Final clashes        | 3           |
| Is timetable valid   | Yes         |


**Copy the printed timetable output here:**
```
Slot 1: Geography
Slot 2: Chemistry, English
Slot 3: History, Computer Science, Economics
Slot 4: Biology, Statistics
Slot 5: Mathematics, Physics
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
The number of clashes drops quickly during the early iterations of the algorithm. 
After the initial drop, the curve becomes flatter as the algorithm gradually improves the timetable. 
This shows that simulated annealing explores widely at first and then stabilizes near a good solution.
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**
| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
| ------------ | ------------- | -------------------- | ------------------ |
| 0.80         | 4             | 205                  | No                 |
| 0.95         | 1             | 899                  | No                 |
| 0.995        | 0             | 1379                 | Yes                |



**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
When the cooling rate is 0.80, the temperature decreases very quickly, so the algorithm stops exploring early and produces more clashes.
With cooling rate 0.95, the algorithm explores more solutions and the result improves.
With cooling rate 0.995, the temperature decreases slowly, allowing the algorithm to explore many possibilities and eventually reach zero clashes.
```

**Which cooling_rate gave the best result? Why do you think that is?**
```
The best cooling rate is 0.995.
This value cools the temperature slowly, which allows the algorithm to explore more solutions and find a better timetable with zero clashes.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment       | Key setting          | Final clashes | Main finding                             |
| ---------------- | -------------------- | ------------- | ---------------------------------------- |
| 1 — Baseline     | cooling_rate = 0.995 | 0             | SA successfully reduced clashes to zero. |
| 2 — Cooling rate | cooling_rate = 0.995 | 0             | Slow cooling gives better solutions.     |


**In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)**
```
| Experiment       | Key setting          | Final clashes | Main finding                             |
| ---------------- | -------------------- | ------------- | ---------------------------------------- |
| 1 — Baseline     | cooling_rate = 0.995 | 0             | SA successfully reduced clashes to zero. |
| 2 — Cooling rate | cooling_rate = 0.995 | 0             | Slow cooling gives better solutions.     |

```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, timetable pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
