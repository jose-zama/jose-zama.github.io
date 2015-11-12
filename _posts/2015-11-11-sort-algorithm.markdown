---
layout: post
section-type: post
title:  "Sort algorithm"
category: Interview Algorithms
comments: true
---

This post is one of a series showing my solutions and implementations to the interview questions that Smerity 
gathered in his [post](http://smerity.com/articles/2009/interviews.html).

In this post I show how I dealt with the **sort Algorithm**. First I show what is the problem, and then how 
I attempted to code a solution without looking somewhere else following a TDD (Test Driven Development) practices
. The language I used through TDD is python, though JavaScript and Java implementations are also given.

{::comment}
Finally I show my implementation to a interesting algorithm called **merge sort**.
{:/comment}

##Problem

The problem is simple:

> Implement a sort of your choice in your preferred language.


##Analysis

As the problem does not specify what to sort, I have chosen to sort an array of numbers. 
As I like to work following a TDD, I numbered
a list of simple test cases:

1. Sort an empty or a one size array. The result should be the same array.
2. Sort two different numbers. 
3. Sort three sorted and unsorted numbers.
4. Finally sort several numbers.

##Implementation

In TDD, one starts writing tests. The following are my unit tests. I used *unittest* as testing framework and the *sort* module has my implementation.

{% highlight python %}

import unittest
import sort

class MyTest(unittest.TestCase):

    def test_empty(self):
        numbers = []
        result = sort.sort(numbers)
        self.assertEqual(numbers, result)
        self.assertEqual(len(result), 0)

    def testSort1(self):
        input = [6]
        expected = [6]
        result = sort.sort(input)
        self.assertEqual(expected, result)

    def testSort2Unsorted(self):
        input = [6,2]
        expected = [2,6]
        result = sort.sort(input)
        self.assertEqual(expected, result)

    def testSort2Sorted(self):
        input = [2,6]
        expected = [2,6]
        result = sort.sort(input)
        self.assertEqual(expected, result)

    def testSort3Unsorted(self):
        input = [5,2,1]
        expected = [1,2,5]
        result = sort.sort(input)
        self.assertEqual(expected, result)

    def testSort3Sorted(self):
        input = [2,4,7]
        expected = [2,4,7]
        result = sort.sort(input)
        self.assertEqual(expected, result)

    def testSort10(self):
        input = [3,7,23,67,3,12,4,998,4,-5]
        expected = [-5,3,3,4,4,7,12,23,67,998]
        result = sort.sort(input)
        self.assertEqual(expected, result)

{% endhighlight %}

So my idea was to go through each number of the array starting from the second, and move it towards the start of the array as long as
it is less than the other numbers. If it reaches a smaller or equal number, then stop and do the same with the next number in the array.

The following snippet shows my implementation in python. It, obviously, pass my tests:

{% highlight python %}

def sort(numbers):

    if len(numbers) < 2:#Return the same array if it has less than two numbers
        return numbers

    i = 1
    while i < len(numbers):#Outer loop, select each number in the array
        j = i
        while j > 0:#Inner loop, compares and move a number towards the beginning of the array
            if numbers[j] < numbers[j-1]:
                temp = numbers[j-1]
                numbers[j-1] = numbers[j]
                numbers[j] = temp
                j -= 1
            else:
                break
        i += 1

    return numbers

{% endhighlight %}

Next is the implementation in Java:

{% highlight java %}

public class Sort {

    public void sort(int[] numbers) {

        if (numbers.length < 2) {
            return;
        }

        int i = 1, j;
        int temp;
        while (i < numbers.length) {
            j = i;
            while (j > 0) {
                if (numbers[j] < numbers[j - 1]) {
                    temp = numbers[j - 1];
                    numbers[j - 1] = numbers[j];
                    numbers[j] = temp;
                    j -= 1;
                } else {
                    break;
                }
            }
            i += 1;
        }
    }
{% endhighlight %}

And here is the implementation in javascript:

{% highlight javascript %}

function sort(numbers) {

	if (numbers.length < 2) {
		return numbers;
	}

	var i=1, j;
	var temp;

	while (i < numbers.length) {
		j = i;
		while (j > 0) {
		    if (numbers[j] < numbers[j - 1]) {
		        temp = numbers[j - 1];
		        numbers[j - 1] = numbers[j];
		        numbers[j] = temp;
		        j -= 1;
		    } else {
		        break;
		    }
		}
		i += 1;
	}	
	return numbers;
}

{% endhighlight %}

After finished coding my solution, I searched for sort algorithms and I noticed that my implementation is very similar to the
[Insertion sort algorithm](https://en.wikipedia.org/wiki/Insertion_sort). There are a lot of more efficient algorithms, so I 
recommend you to check them if you want to go deeper.

Please share any comment or question you have. See you and take care!