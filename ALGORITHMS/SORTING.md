# Sorting

### Quicksort

So before we implement the Quicksort algorithm in Haskell, let's review on what the algorithm itself is. Quicksort is essentially a divide-and-conquer algorithm, which selects a pivot element from the array and partitions the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.  

For a clearer undestanding click here: [Quicksort](https://www.geeksforgeeks.org/quick-sort/)


```
quicksort1 :: (Ord a) => [a] -> [a]
quicksort1 [] = []
quicksort1 (x:xs) =
  let smallerSorted = quicksort1 [a | a <- xs, a <= x]
      biggerSorted = quicksort1 [a | a <- xs, a > x]
  in  smallerSorted ++ [x] ++ biggerSorted

```

then in ghci you run the function like this: `quicksort1 [1,5,2]`

So the code above we are taking the first element as our pivot, divide the remaining list into the elements greater than the pivot and less than the pivot. Then we recursively sort each of these sub-list, and combine them with the pivot in the middle. The pitfall with this version of quicksort is in each new list we make takes extra memory. Meaning that we copy part of the list at each recursive step, or in other words, we will use at least O(n) memory. By the way, it's important to know that this version uses the first elementas the pivot. 


### Mergesort 

The mergesort algorithm, similar quicksort, is a divide and conquer algorithm.  The algorithm is as follows....

1. List is split into two parts
2. Two parts are sorted by the algorithm
3. The sorted parts are merged by a special merging procedure for sorted lists.

```
mergesort'merge :: (Ord a) => [a] -> [a] -> [a]
mergesort'merge [] xs = xs
mergesort'merge xs [] = xs
mergesort'merge (x:xs) (y:ys)
    | (x < y) = x:mergesort'merge xs (y:ys)
    | otherwise = y:mergesort'merge (x:xs) ys
 

mergesort'splitinhalf :: [a] -> ([a], [a])
mergesort'splitinhalf xs = (take n xs, drop n xs)
    where n = (length xs) `div` 2 
 

mergesort :: (Ord a) => [a] -> [a]
mergesort xs 
    | (length xs) > 1 = mergesort'merge (mergesort ls) (mergesort rs)
    | otherwise = xs
    where (ls, rs) = mergesort'splitinhalf xs

```

In the mergesort'splitinhalf function we split a list into two parts, thus returning a pair of array into which the original array was split. `n` is equal to the half of the length of the array, and then we use the standard functions `take` and `drop` to get the first `n` elements of the list  `take n xs` and the rest of the list after those first elements `drop n xs`.


So the mergesort'merge function receives two arrays and produces one array of the same type. The algorithm for merge the two subarrays is as follows:

- if the first list is empty [] then the result of the merge is the second list xs
- if the second list is empty [] then the result of the merge is the first list xs
- otherwise we compare the first elements of the lists and append with the colon (:) function the least of them to the new list which is the result of merge the remaining two lists


Now let's go over to our mergesort function. If the length of the list is greater than 1 then we do the standard step of the algorithm. Otherwise the list with the length of 1 is already  sorted (the condition for ending the recursion). 


### Bubble Sort

So before we dive into the Haskell implementation of Bubble Sort, let's define the algorithm itself. Bubble sort is one of the simplest sorting algorithms that works by repeatedly swapping the adjacent elements if they are in the wrong order. 


```
bubblesort'iter :: (Ord a) => [a] -> [a]
bubblesort'iter (x:y:xs)
    | x > y = y : bubblesort'iter (x:xs)
    | otherwise = x : bubblesort'iter (y:xs)
bubblesort'iter (x) = (x)

bubblesort' :: (Ord a) => [a] -> Int -> [a]
bubblesort' xs i 
    | i == (length xs) = xs
    | otherwise = bubblesort' (bubblesort'iter xs) (i + 1) 
 
bubblesort :: (Ord a) => [a] -> [a]
bubblesort xs = bubblesort' xs 0
```

In the implementation above, bubblesort'iter will go through all the elements in a list and exchange pairs of elements. Then in the bubblesort function it will apply the bubblesort'iter n time -- where n is the length of the list that should be sorted. So in the bubblesort function we take into two arguments: the current list and the number of the current iteration i. 


### Selection Sort

The implementation of selection sort below selects the minimum element repeatedly until the list is empty. 

```
import Data.List (minimum, delete)

ssort :: Ord t => [t] -> [t]
ssort [] = []
ssort xs = let { x = minimum xs } 
           in  x : ssort (delete x xs)
```

### References and Recommendations for Future Reading:
- [Bubble sort, Mergesort, and other sorting algorithms](https://smthngsmwhr.wordpress.com/2012/11/09/sorting-algorithms-in-haskell/#quicksort)

