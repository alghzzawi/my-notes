
# Data Analysis


## Overview: What is Jupyter Lab

### You'll be able orchestrate multiple documents and activities side by side within the work region utilizing tabs and splitters. Documents and activities coordinated with each other, empowering unused workflows for intuitively computing, for example: 

* #### Code Comforts give transitory scratchpads for running code intuitiveness, with full back for wealthy yield. A code support can be connected to a note pad part as a computation log from the scratch pad, for example.

* #### Kernel-backed reports empower code in any content record (Markdown, Python, R, LaTeX, etc.) to be run intelligence in any Jupyter kernel. 

* #### Notebook cell yields can be reflected into their possess tab, side by side with the scratch pad, empowering basic dashboards with intelligently controls supported by a kernel. 

* #### Multiple sees of archives with diverse editors or watchers empower live altering of records reflected in other watchers. For case, it is simple to have live see of Markdown, Delimiter-separated Values, or Vega/Vega-Lite records.

> #### JupyterLab: empowers you to work with documents and activities such as Jupyter notebooks, content editors, terminals, and custom components in a adaptable, coordinates, and extensible way. For a demonstration of JupyterLab and its features,

---

<br>
<br>

# NumPy

### NumPy may be a commonly utilized Python data analysis package. By utilizing NumPy, you'll be able speed up your workflow, and interface with other packages within the Python environment, like scikit-learn, that utilize NumPy beneath the hood. NumPy was initially created within the mid 2000s, and emerged from an indeed more seasoned package called Numeric. This life span implies that nearly each data analysis or machine learning package for Python leverages NumPy in a few way.
 
 <br>
 <br>

## Using NumPy To Read In Files

### It’s possible to use NumPy to directly read csv or other files into arrays. We can do this using the numpy.genfromtxt function. We can use it to read in our initial data on red wines.

## In the below code, we:

* #### Use the __genfromtxt__ function to read in the __winequality-red.csv__ file.

* #### Specify the keyword argument __delimiter=";"__ so that the fields are parsed properly.

* #### Specify the keyword argument __skip_header=1__ so that the header row is skipped.

        wines = np.genfromtxt("winequality-red.csv", delimiter=";", skip_header=1)

#### __wines__ will end up looking the same as if we read it into a list then converted it to an array of floats. NumPy will automatically pick a data type for the elements in an array based on their format.

## Indexing NumPy Arrays

#### We now know how to create arrays, but unless we can retrieve results from them, there isn’t a lot we can do with NumPy. We can use array indexing to select individual elements, groups of elements, or entire rows and columns. One important thing to keep in mind is that just like Python lists, NumPy is zero-indexed, meaning that the index of the first row is 0, and the index of the first column is 0. If we want to work with the fourth row, we’d use index 3, if we want to work with the second row, we’d use index 1, and so on. We’ll again work with the wines array:

<br>

|||||||||||||
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 7.4 | 0.70 | 0.00 | 1.9 | 0.076 | 11 | 34 | 0.9978 | 3.51 | 0.56 | 9.4 | 5 |
|7.8|0.88|0.00|2.6|0.098|25|67|0.9968|3.20|0.68|9.8|5|
7.8|0.76|0.04|2.3|0.092|15|54|0.9970|3.26|0.65|9.8|5|
|11.2|0.28|0.56|1.9|0.075|17|60|0.9980|3.16|0.58|9.8|6|
|7.4|0.70|0.00|1.9|0.076|11|34|0.9978|3.51|0.56|9.4|5|

#### Let’s select the element at row 3 and column 4. In the below code, we pass in the index 2 as the row index, and the index 3 as the column index. This retrieves the value from the fourth column of the third row:

     __wines[2,3]__

     2.2999999999999998

#### Since we’re working with a 2-dimensional array in NumPy, we specify 2 indexes to retrieve an element. The first index is the row, or axis 1, index, and the second index is the column, or axis 2, index. Any element in wines can be retrieved using 2 indexes.