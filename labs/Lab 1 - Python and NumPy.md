---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Julian Davis


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
```

```python

a = np.ones((6, 4))
a = a + 1
print(a)

```

## Exercise 2

```python
b = np.ones((6, 4))

x = np.eye(4) * 2

newrow = [0, 0, 0, 0]
x = np.vstack([x, newrow])
x = np.vstack([x, newrow])

b = b + x
print(b)
```

## Exercise 3


- a * b works because all this does is multiply each cell in one matrix by it's corresponding cell in the other
- dot(a, b), which is true matrix multiplication, doesn't work unless the proper dimensions are in place ((n * m) * (m * n))

```python

c = a * b
# c = np.dot(a, b)
print(c)
```

## Exercise 4

```python
The results are in different shapes order matters in matrix multiplication.
```

```python
x = np.dot(a.transpose(),b)
y = np.dot(a,b.transpose())

print(x)
print()
print(y)
```

## Exercise 5

```python
def hello():
    print("Hello")
    
hello()
```

## Exercise 6

```python
def arrCalcs():
    a = [[1, 2, 3, 4], [-10, 8, 7, 32]]
    sum_a = np.sum(a); mean_a = np.mean(a); med_a = np.median(a)
    print("A: Sum", sum_a, "Mean", mean_a, "Median", med_a)
    
arrCalcs()
```

## Exercise 7

```python
def countOnes(arr):
    dims = np.shape(arr)
    num_ones = 0
    for i in range(dims[0]):
        for j in range(dims[1]):
            if b[i][j] == 1:
                num_ones += 1
            
    return num_ones

print("First count:", countOnes(b))

indices = np.where(b == 1)

print(b[indices])
sum2 = np.sum(b[indices])
print("Second count:", sum2)




```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd
```

```python
lst = [2, 2, 2, 2]
a = pd.DataFrame([lst, lst, lst, lst, lst, lst])

print(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
lst1 = [3, 1, 1, 1]
lst2 = [1, 3, 1, 1]
lst3 = [1, 1, 3, 1]
lst4 = [1, 1, 1, 3]
lst5 = [1, 1, 1, 1]

b = pd.DataFrame([lst1, lst2, lst3, lst4, lst5, lst5])

print(b)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.


same answer as exercise 3

```python
c = a * b
# c = a.dot(b)
print(c)

```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
def countOnes(arr):
    dims = arr.shape
    numOnes = 0
    for i in range(dims[1]):
        for j in range(dims[0]):
            if arr[i][j] == 1:
                numOnes += 1
    return numOnes
            
print("First count:", countOnes(b))

indices = b[b == 1]
sum2 = sum(indices.sum(axis = 1, skipna = True)) 
print("Second count:", sum2)



```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df["name"]
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
```

```python
titanic_df.loc["female"]
# there are 466 female passengers
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index(inplace = True)
titanic_df
```
