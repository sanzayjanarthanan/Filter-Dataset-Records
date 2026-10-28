# Task 19: Filter Dataset Records with Pandas

**Veda Technology Internship | AI & ML Track | Level 1, Day 19**
**Intern:** J Sanjay

## Overview

This project demonstrates how to filter records from a dataset using one or more conditions with Pandas. It uses the Titanic dataset and covers single conditions, combined conditions (AND, OR, NOT), `isin()` and `query()`.

## Objective

Learn how to retrieve relevant records from a dataset using Boolean conditions, and verify each result by checking the number of records returned.

## Tools Used

- Python
- Pandas
- Jupyter Notebook

## Dataset

Titanic dataset, loaded directly from a public CSV:

```
https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv
```

Columns used: `Survived`, `Pclass`, `Sex`, `Age`, `Fare`.

## Approach

1. Loaded the dataset into a DataFrame with `pd.read_csv()` and inspected it using `len(df)`, `df.columns` and `df.head()`.
2. Created Boolean masks from conditions and used them to select rows with `df[mask]`.
3. Combined conditions using `&` (AND), `|` (OR) and `~` (NOT), wrapping each condition in its own parentheses.
4. Checked the number of records after every filter using `len()`.

## Filtering Examples

| # | Filter | Code | Explanation |
|---|--------|------|-------------|
| 1 | Female passengers | `df[df['Sex'] == 'female']` | Single condition; Boolean mask keeps only True rows |
| 2 | 1st class and survived | `df[(df['Pclass'] == 1) & (df['Survived'] == 1)]` | AND: both conditions must be True |
| 3 | Age > 60 or Fare > 200 | `df[(df['Age'] > 60) \| (df['Fare'] > 200)]` | OR: at least one condition must be True |
| 4 | Not male | `df[~(df['Sex'] == 'male')]` | NOT: reverses the mask |
| 5 | Class 1 or 2 | `df[df['Pclass'].isin([1, 2])]` | `isin()` matches against a list of values |
| 6 | Children who survived | `df.query("Age < 18 and Survived == 1")` | `query()` takes the condition as a string |
| 7 | Female, 1st class, survived | `df[(df['Sex'] == 'female') & (df['Pclass'] == 1) & (df['Survived'] == 1)]` | Three conditions chained with `&` |

## Results

| Filter | Records |
|--------|---------|
| Total records | (your output) |
| Female passengers | (your output) |
| 1st class survivors | (your output) |
| Age > 60 or Fare > 200 | (your output) |
| Not male | (your output) |
| Class 1 or 2 | (your output) |
| Children who survived | (your output) |
| Female + 1st class + survived | (your output) |

## Key Learnings

- Boolean indexing is the main way to filter rows in Pandas.
- Use `&`, `|` and `~` for combining conditions, not `and`, `or`, `not`.
- Parentheses are required around each condition because `&` and `|` have higher precedence than comparison operators such as `>` and `==`. Without them, Pandas raises a `ValueError` (ambiguous truth value of a Series).
- Checking the record count after each filter confirms the result is correct.

## Outcome

Successfully filtered the Titanic dataset using multiple techniques and verified each result by record count. This forms the base for later steps such as data cleaning, analysis and model building.

## How to Run

1. Clone this repository.
2. Install dependencies: `pip install pandas jupyter`
3. Open `Task19_Filter_Dataset_Records.ipynb` in Jupyter Notebook and run all cells.

## Repository Contents

- `Task19_Filter_Dataset_Records.ipynb`: notebook with all examples and outputs
- `README.md`: project description, approach and outcome
