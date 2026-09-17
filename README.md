# ECE2112 - Experiment 3

This repository contains my solutions for **Experiment 3** in ECE2112 - Advanced Computer Programming and Algorithms.

The activity focuses on using **Pandas** to read a dataset, inspect its contents, select specific rows and columns, and filter data based on different conditions.

## Files

* `SAMOY_PA3.ipynb` - Jupyter Notebook containing the Python codes
* `cars.csv` - Dataset used in the activity
* `README.md` - Documentation of the program

---

## Importing Pandas and Loading the Dataset

```python
import pandas as pd
cars = pd.read_csv("cars.csv")
cars
```

`pandas` is imported as `pd` to make its functions easier to use.

`pd.read_csv("cars.csv")` reads the CSV file and stores it inside the DataFrame called `cars`.

Writing `cars` displays the complete dataset.

---

## Checking the Dataset

```python
print("Shape: ", cars.shape)
print("Column names: ", cars.columns.tolist())
```

`cars.shape` shows the number of **rows and columns** in the dataset.

`cars.columns.tolist()` gets all the column names and converts them into a list for easier viewing.

---

## Selecting Rows 6 to 10

```python
cars_6_to_10 = cars.iloc[5:10]
cars_6_to_10
```

`.iloc[]` is used to select rows based on their numerical position.

Python starts counting from index `0`, so:

```python
cars.iloc[5:10]
```

selects the **6th up to the 10th row** of the dataset.

The selected rows are stored in `cars_6_to_10`.

---

## Selecting Specific Columns

```python
cars_6_to_10[["Model", "mpg", "cyl", "hp", "gear"]]
```

This selects only the following columns from rows 6 to 10:

* `Model` - car model
* `mpg` - miles per gallon
* `cyl` - number of cylinders
* `hp` - horsepower
* `gear` - number of forward gears

Using double brackets allows multiple columns to be selected from the DataFrame.

---

## Finding the Toyota Corolla

```python
toyota = cars[cars["Model"] == "Toyota Corolla"]
toyota
```

This filters the dataset and selects only the row where the `Model` is equal to `"Toyota Corolla"`.

The result is stored in the variable `toyota`.

---

## Finding the Pontiac Firebird

```python
pontiac = cars[cars["Model"] == "Pontiac Firebird"][["Model", "mpg", "hp", "wt"]]
pontiac
```

This first searches for the row containing the `"Pontiac Firebird"`.

After filtering the row, only the following columns are displayed:

* `Model`
* `mpg`
* `hp`
* `wt`

This shows how row filtering and column selection can be combined in one statement.

---

## Selecting Multiple Car Models

```python
models = ["Datsun 710", "Lotus Europa", "Ferrari Dino"]
```

A list named `models` is created containing the three car models that will be searched in the dataset.

```python
selected_cars = cars[
    cars["Model"].isin(models)
][["Model", "mpg", "cyl", "hp", "gear"]]

selected_cars
```

`.isin(models)` checks whether each value in the `Model` column is included in the `models` list.

Only the matching cars are selected.

The code then displays only the following columns:

* `Model`
* `mpg`
* `cyl`
* `hp`
* `gear`

The final result is stored in `selected_cars`.

---

## Checking the Shape of the Selected Data

```python
print("Shape of selected_cars:", selected_cars.shape)
```

`.shape` is used again to determine how many rows and columns are present in the filtered `selected_cars` DataFrame.

---

## Pandas Concepts Used

The activity applies the following Pandas concepts:

* `pd.read_csv()`
* DataFrames
* `.shape`
* `.columns`
* `.tolist()`
* `.iloc[]`
* Column selection
* Conditional filtering
* `.isin()`

---

## Requirements

The program requires:

```text
Python
Pandas
Jupyter Notebook
```

Pandas can be installed using:

```bash
pip install pandas
```

The `cars.csv` file should also be located in the same directory as the Jupyter Notebook.

---

## Summary

The activity demonstrates basic data manipulation using Pandas. It includes loading a CSV dataset, checking its dimensions and columns, selecting specific rows and columns, and filtering data based on single or multiple car models.
