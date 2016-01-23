---
layout: post
section-type: post
title:  "Matrix product"
category: Interview Algorithms
comments: true
tags: [ 'interviewAlgorithms', 'tdd' ]

description: I had this problem to solve in an interview, and several external factors forced me to have not the wanted outcome. If only I had used a Test driven development... Anyway, here an example of using TDD to write a function to multiply two matrices.
---

I had this problem to solve in an interview, and several external factors forced me to have not the wanted outcome. 
If only I had used a Test driven development... Anyway, here an example of using TDD to write a function to multiply two matrices.

The language used is *python*.

##Problem

> Get the product of two matrices. The first matrix should have the same number of columns as the second matrix.


##Analysis

As there is a restriction with the number of rows and columns, this should be my first test. I will assume that these matrices are not
empty nor null. Furthermore, the matrices are regular two-dimensional array structures. Regular means that all rows have the same number
of columns.

I started implementing the validation of the number of rows and columns. This was my first test. Once the test was passed, I moved forward 
to design the next test.

1. Validate that the first matrix has the same number of columns as the second.
2. Multiply a 1x1 matrix with a second 1x1 matrix.
3. Multiply a 1x2 matrix with a second 2x1 matrix.
4. Multiply a 2x2 matrix with a second 2x1 matrix.
5. Multiply a 2x2 matrix with a second 2x2 matrix.
6. Multiply a bigger one, 3x2 with a 2x3.

##Implementation

#### Test 1. Validate that the first matrix has the same number of columns as the second

I thougth that a good idea would be to rise an exception. Therefore the test should receive an exception:

{% highlight python %}

def testDifferentNumberofColumnsAndRows(self):
	m1 = [[1, 2, 3, 4]]  # 4 columns
	m2 = [[1, 2], [3, 4]]  # 2 rows
	with self.assertRaises(Exception) as context:
		matrix.product(m1, m2)

	self.assertTrue('M1 has different number of columns than M2 rows' in context.exception)	
{% endhighlight %}

The following was coded to pass the test.

{% highlight python %}
def product(m1, m2):
    if len(m1[0]) != len(m2):
        raise Exception('M1 has different number of columns than M2 rows')

{% endhighlight %}

#### Test 2. Multiply a 1x1 matrix with a second 1x1 matrix.

The easiest matrix multiplication would be with two 1x1 matrices. So the test would be like:

{% highlight python %}
def testOneCol_X_OneRow(self):
	m1 = [[1]]
	m2 = [[2]]
	res = matrix.product(m1, m2)
	exp = [[2]]
	self.assertEqual(exp, res)		
{% endhighlight %}

As we can see in the test, the result is the product of 1*2. So, lets return a 1x1 matrix with the product of the matrix coordinates of these numbers.
These coordinates are [0,0].

{% highlight python %}
def product(m1, m2):
    if len(m1[0]) != len(m2):
        raise Exception('M1 has different number of columns than M2 rows')

    res = [[0]]
    res[0][0] = m1[0][0] * m2[0][0]
    return res
{% endhighlight %}

#### Test 3. Multiply a 1x2 matrix with a second 2x1 matrix.

Then the next test was added. I only incremented one column to matrix one and therefore one row to matrix two. The result is still a matrix 1x1.

{% highlight python %}
def testTwoCol_X_TwoRow(self):
	m1 = [[1, 2]]
	m2 = [[3], [4]]
	res = matrix.product(m1, m2)
	exp = [[11]]
	self.assertEqual(exp, res)	
{% endhighlight %}

To get the result, the formula is ``(1*3)+(2*4)=11`` . These in coordinates is ``(m1[0,0]* m2[0,0]) + (m1[0,1] * m2[1,0]) = 11``
As we can see, the row of matrix 1 and the column of matrix 2 are incremented by one in the second multiplication. So I refactored and
used a loop as below:

{% highlight python %}
def product(m1, m2):
    numberColsM1 = len(m1[0])
    numberRowsM2 = len(m2)

    if len(m1[0]) != numberRowsM2:
        raise Exception('M1 has different number of columns than M2 rows')

    res = [[0]]

    for i in range(numberColsM1):
        res[0][0] = res[0][0] + (m1[0][i] * m2[i][0])

    return res
{% endhighlight %}

#### Test 4. Multiply a 2x2 matrix with a second 2x1 matrix.

Now, lets increment a row in matrix 1:

{% highlight python %}
def testTwoColTwoRow_X_OneRow(self):
	m1 = [[1, 2], [2, 1]]
	m2 = [[3], [4]]
	res = matrix.product(m1, m2)
	exp = [[11], [10]]
	self.assertEqual(exp, res)
{% endhighlight %}

Now the result has another row. So the number of rows of the result depends on the number of rows of matrix one. I will need another loop to iterate
through these rows as well:

{% highlight python %}
def product(m1, m2):
    numberColsM1 = len(m1[0])
    numberRowsM2 = len(m2)

    if numberColsM1 != numberRowsM2:
        raise Exception('M1 has different number of columns than M2 rows')

    # initialize matrix
    numberRowsM1 = len(m1)
    res = [[0] for rows in range(numberRowsM1)]

    for rows in range(numberRowsM1):
        for i in range(numberColsM1):
            res[rows][0] = res[rows][0] + (m1[rows][i] * m2[i][0])

    return res
{% endhighlight %}

#### Test 5. Multiply a 2x2 matrix with a second 2x2 matrix.

And now, lets increment a column in matrix 2:

{% highlight python %}
def testTwoColTwoRow_X_TwoColTwoRow(self):
	m1 = [[1, 2],
		  [2, 1]]
	m2 = [[3, 1],
		  [4, 1]]
	res = matrix.product(m1, m2)
	exp = [[11, 3],
		   [10, 3]]
	self.assertEqual(exp, res)
{% endhighlight %}

And the result has another column. Similar to the previous test, the number of columns of the result depends on the number of columns of matrix two. 
And a third loop is necessary to iterate through these columns:

{% highlight python %}
def product(m1, m2):
    numberColsM1 = len(m1[0])
    numberRowsM2 = len(m2)

    if numberColsM1 != numberRowsM2:
        raise Exception('M1 has different number of columns than M2 rows')

    # initialize matrix
    numberRowsM1 = len(m1)
    numberColsM2 = len(m2[0])
    res = [[0 for cols in range(numberColsM2)] for rows in range(numberRowsM1)]

    for cols in range(numberColsM2):
        for rows in range(numberRowsM1):
            for i in range(numberColsM1):
                res[rows][cols] = res[rows][cols] + (m1[rows][i] * m2[i][cols])

    return res
{% endhighlight %}

#### Test 6. Multiply a bigger one, 3x2 with a 2x3.

It seems that the code is complete. This last test is just to be more sure (and I think more testing are needed).

{% highlight python %}
def testBigger(self):
	m1 = [[1, 4],
	      [2, 5],
	      [3, 6]]
	m2 = [[7, 8, 9],
              [10, 11, 12]]
	res = matrix.product(m1, m2)
	exp = [[47, 52, 57],
               [64, 71, 78],
               [81, 90, 99]]
	self.assertEqual(exp, res)
{% endhighlight %}

Run all tests, and all tests passed. Hurray!!! Any question? Feel free to ask below;

