# Data Analysis

## Jupyter Lab:
[Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/getting_started/overview.html)

Text editor in Jupyter contains syntax highlighting and configurable indentation. Terminals in Jupyter provide full support for system shells for Mac, Linux, and Powershell. 

When a notebook opens you are in command mode. This mode is used to easily navigate and change the framework of your notebook. The framework is made up of cells.

a - add a cell above
b - add a cell below
c - copy
v - paste
x - cut
dd - delete
z - undo
shift z - redo
y - cell format: code
m - cell format: markdown

Edit mode:
Press enter to edit the currently active cell. Shift Enter will let you see how the cell looks.

If you are inputing code, shift enter will run the code depending on your kernel.


## Numpy Tutorial:
[Numpy Tutorial](https://www.dataquest.io/blog/numpy-tutorial-python/)

Numpy is a commonly used Python data analysis package.
In the reading they import the csv file as such.
```
import csv
with open('winequality-red.csv', 'r') as f:
    wines = list(csv.reader(f, delimiter=';'))
```

NumPy is used to work with multidimensional arrays. 2 dimensional array is called a matrix.
You can create a NumPy array using the numpy.array function. If you pass in a list of lists it will automatically create a NumPy array with the same number of rows and columns. You however want all the elements to be `float` elements for easy computation so you have to leave off the header row, which contains strings. A limitation of NumPy is that all elements in an array have to be of the same type, so if the header is included it will read everything as strings.

In the reading they:
Import the numpy package.
Pass the list of lists wines into the array function, which converts it into a NumPy array.
Exclude the header row with list slicing.
Specify the keyword argument dtype to make sure each element is converted to a float. We’ll dive more into what the dtype is later on.
```
import csv
with open("winequality-red.csv", 'r') as f:
    wines = list(csv.reader(f, delimiter=";"))
import numpy as np
wines = np.array(wines[1:], dtype=np.float)
```

`wines.shape` - will give you the number of rows and columns for this wines data set.

You can also create empty arrays.
```
empty_array = np.zeros((3,4))

empty_array
```
The above will create an array with 3 rows and 4 columns all filled with 0s.
Can also create an array of random numbers using
`np.random.rand(3,4)` - 3 being rows and 4 being columns again.

Note: NumPy arrays are also 0 indexed like normal Python lists.

`wines[0:3,3]` - this will give the first three items in column 4. The colon indicates we want everything from the first given index, up to but not including the 2nd listed index. The 0 can be omited if you just want everything from the start. `wines[:3,3]`

`wines[:,3]` - Use an empty colon if you want everything in that entire column.

`wines[3,:]` - Same as above but for selecting an entire row.

`wines[:,:]` - This being the entire array.

The above notation we have been using can also be used for assigning value to a certain index:
`wines[1,5] = 10` to assign a specific cell, or `wines[:,10] = 50` to assign an entire column.

You can set a single column to a variable `third_wine = wines[3,:]`, grabbing only that 1 dimensional list (vector). You can then grab indexs like you would normall with a list `third_wine[1]`.

Important NumPy data types:
float — numeric floating point data.
int — integer data.
string — character data.
object — Python objects.

[Full list here](https://numpy.org/doc/stable/reference/arrays.dtypes.html)

`numpy.ndarray.astype` is a method to convert an array into a different type. It will actually copy the array and then return a new array with the specified data type. `wines.astype(int)` will turn all of the float values we have been using to integers.

`wines.astype(np.int32)` - If you want more control you can specify which type of that data type you want.

### NumPy Array Operations

Taken directly from reading:
If you do any of the basic mathematical operations (/, *, -, +, ^) with an array and a value, it will apply the operation to each of the elements in the array.

Let’s say we want to add 10 points to each quality score because we’re drunk and feeling generous. Here’s how we’d do that:

`wines[:,11] + 10`
`array([ 15., 15., 15., ..., 16., 15., 16.])`
Note that the above operation won’t change the wines array — it will return a new 1-dimensional array where 10 has been added to each element in the quality column of wines.

If we instead did +=, we’d modify the array in place. `wines[:,11] += 10`

### Broadcasting

Taken directly from reading:
Unless the arrays that you’re operating on are the exact same size, it’s not possible to do elementwise operations. In cases like this, NumPy performs broadcasting to try to match up elements. Essentially, broadcasting involves a few steps:

The last dimension of each array is compared.
If the dimension lengths are equal, or one of the dimensions is of length 1, then we keep going.
If the dimension lengths aren’t equal, and none of the dimensions have length 1, then there’s an error.
Continue checking dimensions until the shortest array is out of dimensions.
For example, the following two shapes are compatible:
```
A: (50,3)
B (3,)
```
This is because the length of the trailing dimension of array A is 3, and the length of the trailing dimension of array B is 3. They’re equal, so that dimension is okay. Array B is then out of elements, so we’re okay, and the arrays are compatible for mathematical operations.

The following two shapes are also compatible:
```
A: (1,2)
B (50,2)
```
The last dimension matches, and A is of length 1 in the first dimension.

These two arrays don’t match:
```
A: (50,50)
B: (49,49)
```
The lengths of the dimensions aren’t equal, and neither array has either dimension length equal to 1.

### NumPy Array Methods

`numpy.ndarray.sum` is used to fina the sum of all elements in an array by default. `wines[:,11].sum()`

Taken directly from reading:
The total of all of our quality ratings is 154.1788. We can pass the axis keyword argument into the sum method to find sums over an axis. If we call sum across the wines matrix, and pass in axis=0, we’ll find the sums over the first axis of the array. This will give us the sum of all the values in every column. This may seem backwards that the sums over the first axis would give us the sum of each column, but one way to think about this is that the specified axis is the one “going away”. So if we specify axis=0, we want the rows to go away, and we want to find the sums for each of the remaining axes across each row:

`wines.sum(axis=0)`

We can verify that we did the sum correctly by checking the shape. The shape should be 12, corresponding to the number of columns:

`wines.sum(axis=0).shape`
`(12,)`

If we pass in axis=1, we’ll find the sums over the second axis of the array. This will give us the sum of each row:

`wines.sum(axis=1)`

There are several other methods that behave like the sum method, including:

numpy.ndarray.mean — finds the mean of an array.
numpy.ndarray.std — finds the standard deviation of an array.
numpy.ndarray.min — finds the minimum value in an array.
numpy.ndarray.max — finds the maximum value in an array.

[Full List of methods](https://numpy.org/doc/stable/reference/arrays.ndarray.html)

### NumPy Array Comparisons:

Taken directly from the reading:

NumPy makes it possible to test to see if rows match certain values using mathematical comparison operations like <, >, >=, <=, and ==. For example, if we want to see which wines have a quality rating higher than 5, we can do this:

`wines[:,11] > 5`
`array([False, False, False, ..., True, False, True], dtype=bool)`

We get a Boolean array that tells us which of the wines have a quality rating greater than 5. We can do something similar with the other operators. For instance, we can see if any wines have a quality rating equal to 10:

`wines[:,11] == 10`
`array([False, False, False, ..., False, False, False], dtype=bool)`

### Subsetting

One of the powerful things we can do with a Boolean array and a NumPy array is select only certain rows or columns in the NumPy array. For example, the below code will only select rows in wines where the quality is over 7:
```
high_quality = wines[:,11] > 7
wines[high_quality,:][:3,:]
```

We select only the rows where high_quality contains a True value, and all of the columns. This subsetting makes it simple to filter arrays for certain criteria. For example, we can look for wines with a lot of alcohol and high quality. In order to specify multiple conditions, we have to place each condition in parentheses, and separate conditions with an ampersand (&):
```
high_quality_and_alcohol = (wines[:,10] > 10) & (wines[:,11] > 7)
wines[high_quality_and_alcohol,10:]
```

We can combine subsetting and assignment to overwrite certain values in an array:
```
high_quality_and_alcohol = (wines[:,10] > 10) & (wines[:,11] > 7)
wines[high_quality_and_alcohol,10:] = 20
```

### Reshaping NumPy Arrays

`np.transpose(wines).shape` - This will flip the axes. Row becomes columns, columns becomes rows.

`wines.ravel()` - numpy.ravel will turn an array into a 1D representation.

`numpy.reshape` - This function will reshape an array to a certain shape we specify. `wines[1,:].reshape((2,6))` this code will turn the second row of wines into a 2D array with 2 rows and 6 columns.

### Combining NumPy Arrays

`numpy.vstack` - Can use this to vertically stack multiple arrays. Think of it like the second arrays’s items being added as new rows to the first array.

`numpy.hstack` - This will horizontally stack arrays. The arrays need to have the same number of rows for this to work.

`numpy.concatenate` - general purpose version of hstack and vstack. If we want to concatenate two arrays, we pass them into concatenate, then specify the axis keyword argument that we want to concatenate along. Concatenating along the first axis is similar to vstack, and concatenating along the second axis is similar to hstack

Example from reading:

In the below code, we:

Read in winequality-white.csv.
Display the shape of white_wines.
```
white_wines = np.genfromtxt("winequality-white.csv", delimiter=";", skip_header=1)
white_wines.shape
(4898, 12)
```
As you can see, we have attributes for 4898 wines. Now that we have the white wines data, we can combine all the wine data.

In the below code, we:

Use the vstack function to combine wines and white_wines.
Display the shape of the result.
```
all_wines = np.vstack((wines, white_wines))
all_wines.shape
(6497, 12)
```
As you can see, the result has 6497 rows, which is the sum of the number of rows in wines and the number of rows in red_wines.



[Back](README.md)