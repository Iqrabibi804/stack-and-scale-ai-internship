EDUPREDICT - DAY 1 (MONDAY, 2 NOVEMBER 2026)
Understanding the dataset and the prediction question

==============================================================
1. PROJECT
==============================================================

EduPredict is a small classification prototype that explores whether a
student will pass their final math grade. It is for learning and
demonstration only. It is not an admissions or grading tool.

Intended user: a learner exploring educational data and model behaviour.


==============================================================
2. DATASET
==============================================================

Name:    UCI Student Performance dataset, math file (student-mat.csv)
Rows:    395 students
Columns: 33
Source:  https://archive.ics.uci.edu/dataset/320/student+performance

The file uses semicolons as separators, so it is loaded with sep=';'.


==============================================================
3. TARGET DEFINITION
==============================================================

Target column: performance

    pass  if G3 >= 10
    fail  otherwise

G3 is the final grade on a 0-20 scale. I used two classes instead of
three because 395 rows are too few for three well-balanced groups.

Note: G3 = 0 may mean the student did not complete the final assessment.
It does not always mean they failed.


==============================================================
4. INPUT FEATURES (WHY THEY ARE AVAILABLE BEFORE THE OUTCOME)
==============================================================

The rule: a feature can be used only if it is known before the final
grade is decided.

Excluded:
  - G3            : the final grade. It is the outcome, so using it would
                    leak the answer.
  - performance   : the target column itself.

Candidate inputs:
  - studytime     : weekly study time (1 to 4). Recorded during the year.
  - failures      : number of past class failures.
  - absences      : school absences. Recorded over the year, so the full
                    total is only known late in the year.
  - higher        : whether the student wants higher education (survey).
  - schoolsup     : extra educational support from school.
  - famsup        : family educational support.
  - Medu, Fedu    : mother's and father's education level.
  - goout         : how often the student goes out with friends.

G1 and G2 (first and second period grades) are also in the data. They are
known before G3, but they are strongly related to it. I have noted them
for a later decision and have not used them in Day 1.


==============================================================
5. WHAT I DID TODAY
==============================================================

- Loaded the dataset with pandas (the code downloads the UCI zip and
  extracts the CSV automatically).
- Checked the shape: 395 rows, 33 columns.
- Checked data types, missing values (0) and duplicate rows (0).
- Defined the target (performance) and checked the class balance.
- Plotted the class balance and the G3 distribution, with the pass
  threshold marked.
- Wrote down the leakage rule and the candidate input features.


==============================================================
6. OBSERVATIONS
==============================================================

Pass and fail counts and shares: [fill in from your output]
Number of students with G3 = 0: [fill in from your output]
Anything unusual in the G3 distribution: [fill in from your plot]


==============================================================
7. LIMITATIONS
==============================================================

- Small sample from two Portuguese schools. Results may not generalise.
- G3 = 0 may mean the final assessment was missed, not failure.
- Results show association, not causation.
- absences is only fully known late in the year.
- This is an educational prototype, not a decision system.


==============================================================
8. HOW TO RUN
==============================================================

Platform: Google Colab (or Jupyter).
Runtime > Run all (Ctrl + F9). Every cell should run without errors.
The output "File Founded: student-mat.csv" and shape (395, 33) confirms
that the data has loaded.


==============================================================
9. SOURCES AND AI ASSISTANCE
==============================================================

- UCI Machine Learning Repository: dataset.
- AI tools were used for explanations and debugging. I have read and can
  explain the code I submitted.
