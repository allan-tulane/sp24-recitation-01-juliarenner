# CMPS 2200  Recitation 01

**Name (Team Member 1):** Julia Renner

In this recitation, we will investigate asymptotic complexity. Additionally, we will get familiar with the various technologies we'll use for collaborative coding.

To complete this recitation, follow the instructions in this document. Some of your answers will go in this file, and others will require you to edit `main.py`. All tests are in `test_main.py`.

## Install Python Dependency

We need Python library of "tabulate" to visualize the results in a good shape. Please install it by running 'pip install tabulate' or 'pip install -r requirements.txt' in Shell Tab of Repl.  

## Running and testing your code

- To run tests, from the command-line shell, you can run
  + `pytest test_main.py` will run all tests
  + `pytest test_main.py::test_one` will just run `test_one`
  + We recommend running one test at a time as you are debugging.

## Turning in your work

- Once complete, click on the "Git" icon in the left pane on repl.it.
- Enter a commit message in the "what did you change?" text box
- Click "commit and push." This will push your code to your github repository.
- Although you are working as a team, please have each team member submit the same code to their repository. One person can copy the code to their repl.it and submit it from there.

## Comparing search algorithms

We'll compare the running times of `linear_search` and `binary_search` empirically.

`Binary Search`: Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise, narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.

- [+] 1. In `main.py`, the implementation of `linear_search` is already complete. Your task is to implement `binary_search`. Implement a recursive solution using the helper function `_binary_search`. 

- [+] 2. Test that your function is correct by calling from the command-line `pytest test_main.py::test_binary_search`

- [+] 3. Write at least two additional test cases in `test_binary_search` and confirm they pass.

- [+] 4. Describe the worst case input value of `key` for `linear_search`? for `binary_search`?

**The worst case input value of 'key' for 'linear_search' would be a value that is not present in the array. This is because for 'linear_search', the enumerate function compares each item in the array to the key starting at index 0. Thereby, even if the key is not in the list, the function will still check each index creating the longest possible runtime. The worst case input value of 'key' for 'binary_search' would also be a value that is not present in the sorted array. This is because the function will continue dividing the search interval in half until the left value is greater than right. This also results in the longest possible runtime compared to when the key value exists somewhere in the list.**

- [+] 5. Describe the best case input value of `key` for `linear_search`? for `binary_search`? 

**The best case input value of 'key' for 'linear_search' would be the value that exists at index 0 of the array. This is because the function will begin by checking that index and will immediately find the key. The best case input value of 'key' for 'binary_search' would be the value that exists in the middle of the sorted array. This is because, similarly, the function will begin by comparing that index and will immediately find the key.**

- [+] 6. Complete the `time_search` function to compute the running time of a search function. Note that this is an example of a "higher order" function, since one of its parameters is another function.

- [+] 7. Complete the `compare_search` function to compare the running times of linear search and binary search. Confirm the implementation by running `pytest test_main.py::test_compare_search`, which contains some simple checks.

- [+] 8. Call `print_results(compare_search())` and paste the results here:

**|            n |   linear |   binary |
  |--------------|----------|----------|
  |       10.000 |    0.002 |    0.002 |
  |      100.000 |    0.005 |    0.002 |
  |     1000.000 |    0.065 |    0.005 |
  |    10000.000 |    0.737 |    0.011 |
  |   100000.000 |    6.744 |    0.070 |
  |  1000000.000 |   75.856 |    0.033 |
  | 10000000.000 | 1195.368 |    0.056 |**

- [+] 9. The theoretical worst-case running time of linear search is $O(n)$ and binary search is $O(log_2(n))$. Do these theoretical running times match your empirical results? Why or why not?

**The theoretical running times do match my empirical results. This can be seen through the chart since linear search's time increases linearly as the size of the list increases ($O(n)$). Binary search's time increases, but at a much slower rate due to the logarithmic time complexity ($O(log2(n))$).**

- [+] 10. Binary search assumes the input list is already sorted. Assume it takes $\Theta(n^2)$ time to sort a list of length $n$. Suppose you know ahead of time that you will search the same list $k$ times. 
  + What is worst-case complexity of searching a list of $n$ elements $k$ times using linear search? **$O(kn)$**
  + For binary search? **$O(n^2 + k * log_2(n))$**
  + For what values of $k$ is it more efficient to first sort and then use binary search versus just using linear search without sorting? **It is more efficient to first sort then use binary search when both $n$ and $k$ are large values.**
