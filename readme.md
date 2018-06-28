### Linked Lists vs Arrays Brief Overview ###

Both are used to store a collection of data

Arrays:
1. Have a *fixed size* (we need to express upper limit of # of items inserted into the array in e.g C, however Javascript does       not have array bounds checking.

2. for Arrays if we want to insert an item into it we *need to allocate space* for the items and if we want to allocate space      for it the current elements need to shift over -> **costly**

   Example Array:    [1,5,10,20,30]
   if you wanted to insert the number 7 into this array and maintain it in sorted order we need to shift every number after 5 over.
   if you wanted to delete the number 10 from this array and maintain it in sorted order we need to shift ever number after 10 


LinkedLists: 
1. Like an array but instead of items being placed at indices they are *connected through a chain of references*, with each        item containing a reference to the next item -> results in extra memory for reference pointer for every element in the list
   In javascript it looks like objects nested inside more objects  e.g 
 const list = {
    head: {
        value: 5
        next: {
            value: 10
            next: {
                value: 20
                next: null
            }
        }
    }
};
so *instead of indices* access like arrays we would use 
**list.head.next.next.value;** -> 20 
2. Dynamic size 
3. Have to **access elements sequentially** starting from the first node -> cannot do e.g Binary Search 
   ** Searching for element inside a sorted array and continually compare element value with value of element in middle of         array (start is lowest val end is highest val) if value less than searching for value only look to the right of that         array else look left continue process until found. 
   If searching **take advantage that your array is already sorted**, allowing you to find this element in O(log(N)) time instead of searching the entire array which would be O(N) runtime complexity.
4. Since all the nodes in a linked list are distributed through the computer's memory, you don't have to shift anything, no        matter where you insert/delete an element. All you have to do is find the nodes on the left and right of where you want to      insert the new node. *O(1) time complexity* vs *Arrays (require a traversal) O(N) time complexity* 


# Sorting #
- QuickSort has a worst case Runtime of 0(N^2) compared with MergeSort having a worst case running time of O(Nlog(N))
- Quicksort uses worst-case O(log n) memory, while mergesort requires O(n) memory since you have to store the elements  
  For lists it's O(log n) additional memory.
  Lists only need some pointers changed during the merge process. That requires constant additional memory.
  -> **MergeSort better for LinkedLists and QuickSort better for Arrays**

### QuickSort ###
- Better for arrays
- can be up to 3x as fast than MergeSort
- Quick Sort is an in-place sort (doesn’t require any extra storage) whereas merge sort requires O(N) extra storage, N denoting   the array size which may be quite expensive.
- Quick Sort is also tail recursive -> tail call optimizations is done. 
  A recursive function is tail recursive when recursive call is the last thing executed by the function. 


### MergeSort ###
 - Better for linked lists 
 - we can insert items in the middle in O(1) extra space and O(1) time. Therefore merge operation of merge sort can be            implemented without extra space for linked lists.
 **Scenerios to use over Quicksort**
1. Array is already sorted. 
2. All elements in the array are the same.
3. Array is sorted in reverse order.
If no information is given about the data use MergeSort


# How do they Work #
- Quicksort is a divide and conquer algorithm.
  Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.

1. Randomly Pick an element(pivot) from the array. 
   OR Always pick first element as pivot.
   OR Always pick last element as pivot 
   OR Pick median as pivot.
2. Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). 
3. Repeat steps 1 and 2 to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.

- MergeSort is a divide and conquer algorithm as well
1. It divides input array in two halves 
2. calls itself for the two halves 
3. merges the two sorted halves.

 # Apriori Algorithm # 
 - (There's an NPM package for this) npm install apriori
 - Apriori is an algorithm for calculating if an item is set is frequent of a specified size over transactional databases. It     proceeds by identifying the frequent individual items in the database and extending them to larger and larger item sets as     long as those item sets appear sufficiently often in the database. 
 - useful for datamining  
 - support threshold is given, where a support is the number of occurences of a item
 - It is very important for effective Market Basket Analysis and it helps the customers in purchasing their items with more       ease which increases the sales of the markets. It has also been used in the field of healthcare for the detection of adverse   drug reactions. Businesses also may use it to put certain items in bundles for customers to buy
 - You can create association rules on the likelyhood of items appearing together  
   - confidence signifies the likelihood of item Y being purchased when item X is purchased, association rule given support and   confidence what is the likelyhood they'll appear together with a certain support.


