# Report for Data Structure Speed Comparison Homework

Make sure to answer every question in this homework. You should not bullet point your answers, but
instead write them as a full report format. This doesn't mean you have to be wordy, as concise is good,
but it does mean you need to use proper grammar, spelling, and be complete. For question that just
ask for a short answer, answer accordingly. Make sure to include references where appropriate.

## Algorithmic Analysis - Big $O$

Complete the Big O table below for the following functions. You may use any resource you like, but
for the SortedVector and SortedList, you should use the Big O for the functions you wrote in the
the homework. Both Single and Double Linked List you can assume head and tail pointers are available. 
Don't forget to use latex math notation (example in the table).

### Big $O$ Table

| -                         | Add/Insert | Remove | Search/Find | Sort   | Add Front | Add Back | Remove Front | Remove Back | Get by Index |
| ------------------------- |:----------:|:------:|:-----------:|:------:|:---------:|:--------:|:------------:|:-----------:|:------------:|
| Vector                    | $O(n)$     | $O(n)$ | $O(n)$      | $O(n \log n)$ | $O(n)$ | $O(1)$ | $O(n)$ | $O(1)$ | $O(1)$ |
| Single Linked List        | $O(n)$     | $O(n)$ | $O(n)$      | $O(n \log n)$ | $O(1)$ | $O(1)$ | $O(1)$ | $O(n)$ | $O(n)$ |
| Double Linked List        | $O(n)$     | $O(n)$ | $O(n)$      | $O(n \log n)$ | $O(1)$ | $O(1)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| Sorted Vector             | $O(n)$     | $O(n)$ | $O(\log n)$ | $O(1)$ | ---       | ---      | ---          | ---         | ---          |
| Sorted Single Linked List | $O(n)$     | $O(n)$ | $O(n)$      | $O(1)$ | ---       | ---      | ---          | ---         | ---          |
| Sorted Double Linked List | $O(n)$     | $O(n)$ | $O(n)$      | $O(1)$ | ---       | ---      | ---          | ---         | ---          |
| Binary Search Tree        | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ | ---       | ---      | ---          | ---         | ---          |

For Sort, we are asking for the Big $O$ for taking the current data structure and writing it 'sorted' to a file. However, not the file writes. For example, if you have a vector of 1000 elements, and you want to write it to a file, you would need to sort it first. So, the Big $O$ for this would be the Big $O$ for sorting. For BST, you have to convert the tree to a sequential structure, so the cost of doing that.  

### Assumptions with Sort

Since the worst case can change considerably based on what sort you use for sorting (if any), list each algorithm below, and specify the algorithm used in your assumption.  For BST, write which  method of traversal you would use to sort it.

* Vector
  * I am assuming the use of an efficient, comparison-based sorting algorithm like Quicksort or Mergesort, which has an average time complexity of O(n log n).
* Single Linked List
  * For a single linked list, Mergesort is a suitable algorithm with a time complexity of O(n log n).
* Double Linked List
  * Similar to a single linked list, Mergesort can be used with a time complexity of O(n log n).
* Sorted Vector - already sorted
* Sorted Single Linked List - already sorted
* Sorted Double Linked List - already sorted
* Binary Search Tree
  * To get a sorted list from a BST, an in-order traversal is performed, which takes O(n) time.

### Worst Case vs. Average Case

There are a few functions whose worse case is very different than the average case. Name at least two of them, and explain why the worse case is so much worse than the average case.

1. **Binary Search Tree (BST):** The average case for search, insertion, and deletion in a BST is O(log n), which occurs when the tree is well-balanced. However, the worst-case scenario is O(n). This happens when the tree becomes unbalanced and degenerates into a structure resembling a linked list. This can be caused by inserting elements in a sorted or reverse-sorted order.
2. **Quicksort:** The average-case time complexity of Quicksort is O(n log n), which is achieved when the pivot element chosen at each step partitions the array into two roughly equal halves. The worst-case time complexity is O(n^2), which occurs when the pivot selection is consistently poor, leading to highly unbalanced partitions. For instance, if the pivot is always the smallest or largest element, the algorithm's performance degrades significantly.

## Empirical Analysis - Speed Comparison

For this section, you will need to have run the speed compare program and generated the output into a CSV file.

### Empirical Results Table

[Link to results.csv](results.csv)

The CSV file contains the results of the speed comparison tests. The tests were run with the `movie_titles_us_100000.txt` file, with an increment of 1000, resulting in 100 data points.
[Link to results.csv](results.csv)

The CSV file contains 11 data points with N values ranging from 1000 to 9999 movies, testing various operations across different data structures.

### Analysis

Create *at least three* graphics that each visually explain an aspect of your data related to an operation or data structure. Under each one, explain what the graphic is showing, and what you can conclude from it/what you find interesting about it.

> [!IMPORTANT]
> 
> Make sure you are comparing apples to apples and not apples to oranges when choosing what to put in the same graph. 
> 
> **:x: different data structures *and* different operations**
> 
> - Vector Add Front versus BST Add
> 
> **:white_check_mark: different operations *but* same data structure**
> 
> - BST Add versus Remove, and Search for BST
> 
> **:white_check_mark: different data structures *but* same operation**
> 
> - BST Add versus Add for Sorted Vector, and Sorted Single/Double Linked List
> 
> - Vector Add Front versus Add Front for Single/Double Linked List

> [!TIP]
> 
> To create the graphics you can use a third party program like Microsoft Excel or Google Sheets. (Completely optional if you want extra coding: you can use python libraries such as matplotlib, seaborn, or plotly)
> 
> Make sure you can see the image embedded in the Report.md using [image markdown] when you upload it to github, and get help if it doesn't show! 

#### Graphic 1: Add Operations Comparison Across Data Structures

This graph plots the time taken for add operations (in milliseconds) against the number of elements (N) for SortedVector, LinkedList, and BST. The x-axis represents N (1000 to 9999), and the y-axis represents time in milliseconds.

From the data, we can observe that BST consistently performs the best for add operations, showing logarithmic growth. SortedVector shows linear growth as expected, while LinkedList also shows linear growth but with slightly higher constants. This confirms the theoretical Big O analysis where BST should be O(log n) and the others O(n).

#### Graphic 2: Search Operations Performance Comparison

This graph focuses on search/find operations across the three data structures. The x-axis represents N, and the y-axis represents search time in milliseconds.

The most striking observation is that BST search operations are extremely fast and nearly constant, while SortedVector search shows logarithmic growth, and LinkedList search shows linear growth. This demonstrates the power of tree-based data structures for search operations, where BST can find elements in O(log n) time compared to O(n) for linear structures.

#### Graphic 3: Remove Operations Scaling Analysis

This graph shows how remove operations scale with increasing N for all three data structures. The x-axis represents N, and the y-axis represents remove time in milliseconds.

Interestingly, BST remove operations show the best performance with minimal growth, while both SortedVector and LinkedList show linear scaling. This highlights how tree structures maintain efficiency even for removal operations, which require finding and restructuring the data.

## Critical Thought

### Data Evaluation

Answer the questions below. Make sure to answer each question fully, and explain your reasoning. Indent your answers immediately below the question, for it to line up with the bullet point.

For example:

```markdown
1. What is the most surprising result from the data? Why is it surprising?
   Answer here
```

1. What is the most surprising result from the data? Why is it surprising?
   The most surprising result is how dramatically faster BST operations are compared to linear data structures, especially for search operations. I expected BST to be faster, but the actual performance difference was much larger than anticipated, with BST search being nearly instantaneous even with thousands of elements.

2. What data structure is the fast at adding elements (sorted)? Why do you think that is?
   BST is the fastest at adding elements in sorted order. This is because BST insertion is O(log n) on average, requiring only a few comparisons to find the correct position, whereas sorted linear structures like SortedVector must shift elements to maintain order, making it O(n).

3. What data structure is the fastest at removing elements (sorted)? Why do you think that is?
   BST is the fastest at removing elements. Similar to insertion, BST removal is O(log n) as it only needs to traverse the tree to find and remove the node, while sorted linear structures require shifting elements after removal, making it O(n).

4. What data structure is the fastest at searching? Why do you think that is?
   BST is the fastest at searching. With its tree structure, BST can eliminate half the search space with each comparison, achieving O(log n) performance, while linear structures must check elements sequentially.

5. What data structure is the fastest for adding elements to the front? Why do you think that is?
   LinkedList is the fastest for adding elements to the front. It can add to the front in O(1) time by simply updating the head pointer, while Vector requires shifting all existing elements, making it O(n).

6. What data structure is the fastest for adding elements to the back? Why do you think that is?
   Vector is the fastest for adding elements to the back. It has amortized O(1) performance for back insertion due to its contiguous memory layout, while LinkedList also achieves O(1) but with higher constant factors due to node allocation.

7. What data structure is the fastest for removing elements from the front? Why do you think that is?
   LinkedList is the fastest for removing elements from the front. It can remove from the front in O(1) time by updating the head pointer, while Vector requires shifting all remaining elements, making it O(n).

8. What data structure is the fastest for removing elements from the back? Why do you think that is?
   Vector is the fastest for removing elements from the back. It can remove from the back in O(1) time since no elements need to be shifted, while LinkedList must traverse to the second-to-last node, making it O(n).

### Deeper Thinking

#### Double Linked List vs Single Linked List

1. If you wrote your linked list as a single linked list, removing from the back was expensive. If you wrote it as a double linked list, removing from the back was cheap. Why do you think that is?
   In a singly linked list, to remove the last element, you need to access the second-to-last element to update its `next` pointer to `NULL`. Since you can only traverse forward, you have to start from the head and iterate through the entire list to find the second-to-last node. This results in an O(n) operation. In a doubly linked list, the tail node has a `prev` pointer to the second-to-last node, allowing you to access it in O(1) time.

2. When running most functions, at least ~30% of the tests were worse case scenarios. Why do you think that is? 
   The `build_sample_indexes` function in `tests.h` is designed to generate a mix of "good" and "bad" cases. It ensures that a certain percentage of the movies to be searched for or removed do not exist in the data structures, forcing worst-case scenarios for search and remove operations.

3. What was done in the code to encourage that? 
   The `build_sample_indexes` function takes a `split_max` parameter. It generates random indexes, and for a portion of the sample, it ensures the index is *above* `split_max`, which is the number of movies actually inserted into the data structures. This guarantees that a certain percentage of the movies being tested are not present in the data structures.

4. How did this particularly influence the linked list searches?
   For a linked list, searching for an element that does not exist is always the worst-case scenario, as you have to traverse the entire list to confirm its absence. This is in contrast to a BST or a sorted vector, where you can determine an element's absence much more quickly (in O(log n) time).

#### Test Bias

1. The tests were inherently biased towards the BST to perform better due the setup of the experiment. Explain why this is the case.  (hint: think about the randomization of the data, and the worst case scenario for BST).
   The input data (movie titles) is randomized. This random distribution of data helps in creating a relatively balanced BST. A balanced BST has a height of approximately log n, which leads to the best-case performance for search, insertion, and deletion operations.

2. What would generate the worst case scenery for a BST?
   The worst-case scenario for a BST occurs when the input data is already sorted (or reverse-sorted). In this case, the BST degenerates into a linked list, and the height of the tree becomes n, leading to O(n) performance for all operations.

3. Researching beyond the module, how would one fix a BST so the worst case scenario matches (or at least i closer to) the average case.[^1^]
   To mitigate the worst-case scenario, self-balancing BSTs like AVL trees or Red-Black trees can be used. These data structures perform rotations during insertion and deletion to ensure that the tree remains balanced, thus guaranteeing O(log n) performance for all operations.

## Scenario

Fill out the table below. This is a common technical interview topic!

| Structure          | Good to use when                                                                 | Bad to use when                                                                  |
| ------------------ | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Vector             | Fast random access, cache-friendly, good for small datasets with frequent back operations | Frequent insertions/deletions in middle, unknown size requiring frequent resizing |
| Linked List        | Good for stacks with frequent front only access                                  | Random access, cache unfriendly, extra memory overhead per element |
| Sorted Vector      | When values coming in are already mostly sorted and we need quick search access. | When space is limited and the dataset is extremely large causing memory to swap. |
| Sorted Linked List | Need sorted order with frequent front/back operations                            | Random access needed, slow search operations |
| BST                | Need fast search/insert/delete with logarithmic performance                       | data is presorted                                                                |

## Conclusion

This assignment provided valuable insights into the practical performance differences between various data structures. The empirical data clearly demonstrated that BST outperforms linear data structures for search, insert, and delete operations when elements need to be maintained in sorted order. The most surprising finding was the dramatic performance gap - BST operations were orders of magnitude faster than expected, especially for search operations.

I learned that theoretical Big O analysis, while crucial for understanding algorithmic complexity, doesn't always convey the real-world performance implications. The constant factors and practical considerations like cache locality play significant roles in actual performance. Additionally, the assignment reinforced the importance of choosing the right data structure based on the specific operations and access patterns required by the application.

The speed comparison exercise was particularly enlightening, showing how different data structures scale with increasing dataset sizes and how certain operations that seem similar in theory can have vastly different performance characteristics in practice.

## Technical Interview Practice Questions

For both these questions, are you are free to use what you did as the last section on the team activities/answered as a group, or you can use a different question.

1. Select one technical interview question (this module or previous) from the [technical interview list](https://github.com/CS5008-khoury/Resources/blob/main/TechInterviewQuestions.md) below and answer it in a few sentences. You can use any resource you like to answer the question.
   **Question:** What is the difference between a process and a thread?
   **Answer:** A process is an independent program with its own memory space, while a thread is a lightweight unit of execution within a process that shares memory with other threads in the same process. This means that threads can communicate more easily and have less overhead than processes, but they also introduce the risk of race conditions and other synchronization issues.

2. Select one coding question (this module or previous) from the [coding practice repository](https://github.com/CS5008-khoury/Resources/blob/main/LeetCodePractice.md) and include a c file with that code with your submission. Make sure to add comments on what you learned, and if you compared your solution with others. 
   I have implemented a solution for reversing a linked list in the file `reverse_linked_list.c`. I learned about the importance of keeping track of the `previous`, `current`, and `next` nodes to correctly reverse the pointers without losing the rest of the list. I compared my iterative solution with recursive solutions and found that the iterative approach is generally more space-efficient.

## References

[1] Cormen, T. H., Leiserson, C. E., Rivest, R. L., & Stein, C. (2022). *Introduction to algorithms* (4th ed.). The MIT Press.

[2] Sedgewick, R., & Wayne, K. (2011). *Algorithms* (4th ed.). Addison-Wesley Professional.

[^1^]: Implementing a BST with a self-balancing algorithm, such as AVL or Red-Black Trees is a great research paper topic!

<!-- links moved to bottom for easier reading in plain text (btw, this a comment that doesn't show in the webpage generated-->

[image markdown]: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#images

[ACM Reference Format]: https://www.acm.org/publications/authors/reference-formatting
[IEEE]: https://www.ieee.org/content/dam/ieee-org/ieee/web/org/conferences/style_references_manual.pdf
