---
title: "Java: Algorithms"
last_modified_at: 2020-10-14
categories:
  - Java
tags:
  - Programming
  - Backend
classes: narrow
toc: true
---

An algorithm is a set of instructions for solving a class of problems by
a mechanical process.

Greatest Common Divisor
-----------------------

### Euclid's Algorithm

If r is the remainder when a is divided by b, then the common divisors
of a and b are the same as the common divisors of b and r. Thus to find
the Greatest Common Divisor we have this equation : gcd(a, b) = gcd(b,
r).

``` java
/**
 * Returns the greatest common divisor of two integers
 *
 * @see org.apache.commons.math3.util.ArithmeticUtils#gcd(int, int)
 * @see java.math.BigInteger#gcd(BigInteger)
 */
public static int gcd(int a, int b) {
    if (b == 0)
        return Math.abs(a);
    return gcd(b, a % b);
}
```

### Binary GCD algorithm

See [Wikipedia: Binary GCD
Algorithm](https://en.wikipedia.org/wiki/Binary_GCD_algorithm).

Counting
--------

The process of counting follows a traverse-and-count pattern. There are
3 things needed in a counting process:

1.  A set or container that can be traversed, like a string or an array
2.  A test to be applied to each element in the set
3.  A counter that keeps track of how many elements pass the test

To count the times a single element repeats in an array:

``` java
public static int count(int[] array, int a) {
    int count = 0;
    for (int i = 0; i < array.length; i++) {
        if (array[i] == a)
            count++;
    }
    return count;
}
```

To count the number of elements in an array that fall in a given range:

``` java
public static int count(int[] array, int low, int high) {
    int count = 0;
    for (int i = 0; i < array.length; i++) {
        if (array[i] >= low && array[i] <= high)
            count++;
    }
    return count;
}
```

To make a histogram: A histogram is an array of integers where each
integer counts the number of values that fall into a certain range:

``` java
public static int[] histogram(int[] array) {
    int[] count = new int[10];
    for (int i = 0; i < array.length; i++) {
        int index = array[i];
        count[index]++;
    }
    return count;
}
```

Sorting
-------

Sorting visualization:

-   <https://visualgo.net/bn/sorting>
-   <https://airtucha.github.io/SortVis/>

### Bubble sort

With bubble sort, starting from the first element, you compare each pair
of adjacent elements in the list. Once a pair of elements are out of
order, swap them. Repeat the number of times that is equal to the length
of the list. [image](http://codepumpkin.com/bubble-sort/)

For example, sorting an array of integers into increasing order:

``` java
public static void bubbleSort(int[] list) {
    for (int i = 0; i < list.length; i++) {
        for (int j = 0; j < list.length - 1; j++) {
            if (list[j] > list[j + 1]) {
                int temp = list[j + 1];
                list[j + 1] = list[j];
                list[j] = temp;
            }
        }
    }
}
```

You can optimize this algorithm by counting the times of swapping during
each iteration. If no swap occurs during an iteration, the sorting is
done. For example, to sort an array of integers into decreasing order:

``` java
public static void bubbleSort2(int[] list) {
    int swaps = 1;
    while (swaps > 0) {
        swaps = 0;
        for (int i = 0; i < list.length - 1; i++) {
            if (list[i] < list[i + 1]) {
                int temp = list[i];
                list[i] = list[i + 1];
                list[i + 1] = temp;
                swaps++;
            }
        }
    }
}
```

### Insertion sort

The idea of insertion sort is to assume a list is partially sorted in
ascending or descending order starting from the first item, and insert
those out-of-order items into their corresponding position in the sorted
part. For example, to sort an array of integers into ascending order the
mind process would be like this:

1.  Starting from the second integer traverse from left to right. Once
    an integer is less than its previous integer store it in a `temp`
    variable and mark its position as P1. Pause the traverse and go to
    step 2;
2.  Starting from P1 traverse from right to left. Move each integer to
    the right by 1 position until an integer is less than temp. Mark
    this integer's next position as P2. Now put the value of temp to P2
    and stop this traverse;
3.  Now continue the traverse in step 1 from position (P1+1) and repeat
    above steps.

[image](https://commons.wikimedia.org/wiki/File:Insertion-sort-example.gif)

``` java
public static void insertionSort(int[] list) {
    for (int i = 1; i < list.length; i++) {
        if (list[i] < list[i - 1]) {
            int temp = list[i];
            for (int j = i - 1; j >= 0; j--) {
                list[j + 1] = list[j];
                if (j == 0 || list[j - 1] < temp) {
                    list[j] = temp;
                    break;
                }
            }
        }
    }
}
```

### Selection sort

The idea of selection sort is to find the smallest (for ascending order)
or greatest (for descending order) item from the unsorted part of an
array and put it in the first position of the unsorted part, repeat this
for remaining unsorted items until all are sorted.

[image](http://codepumpkin.com/selection-sort-algorithms/)

For example, to sort an array of integer into ascending order you could:

1.  Starting from the first integer traverse from left to right. If an
    integer is less than the first, swap them, and continue traversing
    till the end. Now the smallest integer is in the beginning of the
    array;
2.  Repeat the above process from the second integer.

``` java
public static void selectionSort(int[] list) {
    for (int i = 0; i < list.length; i++) {
        for (int j = i + 1; j < list.length; j++) {
            if (list[i] > list[j]) {
                int temp = list[j];
                list[j] = list[i];
                list[i] = temp;
            }
        }
    }
}
```

or

1.  Starting from the first integer traverse from left to right. Find
    the smallest integer in the array and then swap it with the first
    integer;
2.  Repeat the above process from the second integer.

``` java
public static void selectionSort2(int[] list) {
    for (int i = 0; i < list.length; i++) {
        int idx = i;
        for (int j = i + 1; j < list.length; j++) {
            if (list[idx] > list[j])
                idx = j;
        }
        if (idx != i) {
            int temp = list[i];
            list[i] = list[idx];
            list[idx] = temp;
        }
    }
}
```

Efficiency: The total time of sorting n items in an array is
proportional to n<sup>2</sup>.

### Merge sort

To understand merge sort, you need to know the merging process first.
Suppose you have two arrays of integers sorted in ascending order, the
easiest way to put the two sorted arrays into one sorted array would be
combining them by comparing the first item of one array to the first
item of the other. Pick out the smaller item and put it in the first
position of the combined array. Then again, compare the first items of
each array and always pick out the smaller one until all integers are
put in one array, which would be sorted in ascending order when it's
finished. This is the process of merging. You should note that the two
arrays are sorted before merging, and how they are sorted is not told.
You can use selection sort or other methods to sort them, and then merge
them. This whole process is called merge sort.

``` java
public static int[] mergeSort(int[] arr) {
    int[] arr1 = new int[arr.length / 2];
    int[] arr2 = new int[arr.length - arr1.length];
    System.arraycopy(arr, 0, arr1, 0, arr1.length);
    System.arraycopy(arr, arr1.length, arr2, 0, arr2.length);
    selectionSort(arr1);
    selectionSort(arr2);
    return merge(arr1, arr2);
}


public static int[] merge(int[] arr1, int[] arr2) {
    int[] arr = new int[arr1.length + arr2.length];
    int i = 0, j = 0, k = 0;
    while (true) {
        if (i == arr1.length) {
            if (j == arr2.length)
                break;
            arr[k++] = arr2[j++];
            continue;
        }
        if (j == arr2.length) {
            arr[k++] = arr1[i++];
            continue;
        }
        if (arr1[i] < arr2[j]) {
            arr[k] = arr1[i++];
        } else {
            arr[k] = arr2[j++];
        }
        k++;
    }
    return arr;
}
```

Of course, there's a better way to achieve merge sort - do it
recursively! A recursive merge sort breaks an array into 2 halves, and
then breaks them into smaller halves, until both halves have only one
item. An array with only one item is already sorted, so you can merge
them and return the sorted two-item array to the upper calling stack,
and merge it with the other sorted half, and so on and so forth.

``` java
public static void mergeSort(int[] arr, int left, int right) {
    if (left >= right)
        return;

    int mid = (left + right) / 2;
    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);

    int[] arr1 = new int[mid - left + 1];
    int[] arr2 = new int[right - mid];
    for (int i = 0; i < arr1.length; i++) {
        arr1[i] = arr[left + i];
    }
    for (int i = 0; i < arr2.length; i++) {
        arr2[i] = arr[mid + 1 + i];
    }
    int i = 0, j = 0, k = left;
    while (true) {
        if (i == arr1.length) {
            if (j == arr2.length)
                break;
            arr[k++] = arr2[j++];
            continue;
        }
        if (j == arr2.length) {
            arr[k++] = arr1[i++];
            continue;
        }

        if (arr1[i] < arr2[j]) {
            arr[k] = arr1[i++];
        } else {
            arr[k] = arr2[j++];
        }
        k++;
    }
}
```

[image](http://codepumpkin.com/merge-sort-sorting-algorithm/)

Efficiency: To sort n item, it takes time proportional to n\*logn.

### Quick sort

The idea of quick sort is to place an item (usually the first one) of
the list to be sorted to its pivot position, which is the final position
of the item in the sorted list, in just one traverse. To achieve this
you need to place all items less than the pivot to its left and all
items greater than the pivot to its right. You can start from the last
item and traverse backwards. Once an item is less than the pivot move it
to the beginning of the list. Then start from the second item of the
list and traverse forwards until an item is greater than the pivot. Move
the item to where the last moved item was before moving and then again
traverse backwards. Repeat these back-and-forth traverses and there will
be a point where all items greater than the pivot are placed to its
right and smaller items to its left, i.e., the pivot position. Finally
you place the item selected as the pivot to this position, and the first
traverse to the whole list is completed. Then you do the above process
recursively to the sub-lists before and after the pivot.

``` java
public static void quickSort(int[] list, int left, int right) {
    if (left >= right)
        return;
    int pivot = list[left];
    int i = left;
    int j = right;
    while (i < j) {
        while (list[j] > pivot && i < j) {
            j--;
        }
        if (i == j)
            break;
        list[i++] = list[j];
        while (list[i] < pivot && i < j) {
            i++;
        }
        if (i == j)
            break;
        list[j--] = list[i];
    }
    list[i] = pivot;
    quickSort(list, left, i - 1);
    quickSort(list, i + 1, right);
}
```

### Java sorting methods

``` example
Arrays.sort()
```

### Unsorting

To unsort an array is to make the order of the items as random as
possible. To do this you can firstly select an item at a random position
in the array and swap it with the last item of the array, and then
repeat this process for remaining items.

``` java
public static void unsort(int[] arr) {
    for (int i = arr.length - 1; i > 0; i--) {
        int rdmIdx = (int) (Math.random() * (i + 1));
        int temp = arr[rdmIdx];
        arr[rdmIdx] = arr[i];
        arr[i] = temp;
    }
}
```

Searching
---------

### Linear search

-   Linear search is suitable for ordered and unordered arrays, and it's
    the only method for unordered arrays;
-   The process is simply "traverse and compare".

### Bisection/Binary search

Bisection search only works for ordered arrays (ascending order for
example). First you set the range of the list in which the target item
is searched for. If the target is smaller than the first item of the
range or greater than the last item of the range then it's not in the
range and the search is finished. If it's in the range then you can
compare it with the item in the middle of the range. If the middle item
happens to equal the target then the search is finished, or else you
continue searching in the sub-range before or after the middle item
depending on whether the target is smaller or greater than the middle
item. In this way you're narrowing down the range for searching and
eventually find the target faster than traversing through the list and
comparing each item with the target.

The recursive approach:

``` java
/**
 * @param arr    the array to be searched
 * @param i      the index of the first item of the range to be searched
 * @param j      the index of the last item of the range to be searched
 * @param target the target item to be searched for
 * @return the index of the target item, or -1 if the target isn't found in the array
 */
public static int binarySearch(int[] arr, int i, int j, int target) {
    if (target < arr[i] || target > arr[j])
        return -1;

    int mid = (i + j) / 2;
    if (target == arr[mid])
        return mid;
    else if (target > arr[mid])
        i = mid + 1;
    else
        j = mid - 1;

    return binarySearch(arr, i, j, target);
}
```

The iterative approach:

``` java
/**
 * Binary search with an iterative approach
 *
 * @param arr    the array to be searched
 * @param i      the index of the first item of the range to be searched
 * @param j      the index of the last item of the range to be searched
 * @param target the target item to be searched for
 * @return the index of the target item, or -1 if the target isn't found in the array
 */
public static int binarySearch(int[] arr, int i, int j, int target) {
    while (i <= j) {
        int mid = (i + j) / 2;
        if (target == arr[mid])
            return mid;
        else if (target > arr[mid])
            i = mid + 1;
        else
            j = mid - 1;
    }
    return -1;
}
```

Analysis of algorithms
----------------------

### Asymptotic analysis

How the run time of the program is related to the size of the problem.

1.  Big-Oh notation

    These notations do not tell you the actual value of the running time
    of an algorithm, but instead, they tell you the rate of growth of
    the running time as the size of the problem increases.

    1.  O(f(n))

        -   It reads "big o of f of n".
        -   f(n) is a function that assigns a positive real number to
            every positive integer n.
        -   n is the size of the problem. How to decide the size of a
            problem:
            -   If the problem is to sort a list of items, the size of
                the problem is the number of items;
            -   If the input to an algorithm is an integer, the size of
                the problem is the number of bits in the integer instead
                of the integer itself.
        -   To say the running time of an algorithm is O(f(n)) means for
            large values of the problem size n, the running time of the
            algorithm is less than or equal to some constants times
            f(n). O(f(n)) sets an upper limit on the run time, or in
            other words, it tells you the maximum amount of time it
            takes for the algorithm to finish.

    2.  Ω(f(n))

        -   It reads "Omega of f of n".
        -   It sets an lower limit on the run time, that is, the run
            time of the algorithm is greater than or equal to some
            constant times f(n) (for large values of n). It tells you
            the minimum run time.

    3.  Θ(f(n))

        -   It reads "Theta of f of n";
        -   If an algorithm has run time that is both O(f(n)) and
            Ω(f(n)), then it is said to have run time Θ(f(n)).
        -   To say that the run time of an algorithm is Θ(f(n)) means
            for large values of n, the run time is between af(n) and
            bf(n), where a and b are constants, with b greater than a,
            and both greater than zero.

2.  Run time efficiency of some common algorithms

    1.  Adding up the integers in a list with a for loop

        ``` java
        int total = 0;
        int n = list.length;
        for (int i = 0; i < n; i++) {
            total += list[i];
        }
        ```

        If each iteration takes time a, then it takes a\*n for the whole
        loop to finish. The initialization of the variables could take
        time b. Thus the total run time is a\*n + b. Since b &lt;= b\*n,
        a\*n + b &lt;= (a+b)\*n. So the run time of this program is
        O(n), which means the run time of the algorithm is no bigger
        than some constant times n. If the run time of an algorithm is
        O(n), then it is also legit to say its run time is
        O(n<sup>2</sup>) or even O(n<sup>10</sup>) for the run time is
        certainly less than the same constant times n<sup>2</sup> or
        n<sup>10</sup>.

    2.  List of algorithm run times:

        | Algorithm       | Run time         |
        |-----------------|------------------|
        | Linear search   | O(n)             |
        | Binary search   | Θ(log(n))        |
        | Bubble sort     | O(n<sup>2</sup>) |
        | Merge sort      | Θ(n\*log(n))     |
        | Quick sort      | Θ(n\*log(n))     |
        | Towers of Hanoi | O(2n)            |

3.  Worst case run time & Average case run time

    Since run time depends not just on the size of the problem, but on
    the specific data that has to be processed, we need to look at all
    possible problems of size n and their run times. Worst case run time
    is the longest run time for all such problems, while average case
    run time is the average run time for all such problems.

Encryption & Decryption
-----------------------

<https://commons.apache.org/proper/commons-crypto/userguide.html>
<https://docs.oracle.com/javase/8/docs/technotes/guides/security/crypto/CryptoSpec.html#KPGEx>

规则引擎
--------

Search engines
--------------

-   MapReduce
