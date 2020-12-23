#### Folding Exercises 

##### Exercise # 1: Create a function 'rev' that reverses a list. 

```
rev :: [a] -> [a]
```

Solution
```
rev :: [a] -> [a]
rev = foldl (\acc x -> x : acc) []
```
We go through the list, and the order is important so we want to start from the left. the first element starting from the left is prepended. 

We could also use the flip function, with partial function application
```
rev :: [a] -> [a]
rev = foldl (flip (:)) []
```

However, I would prefer the first version because it is more readable and provides a clearer picture on the process. 

##### Exercise 2
Create a function prefixes that return all the prefixes of a given list.

```
prefixes :: [a] -> [[a]]
prefixes [1,2,3] => [[1],[1,2],[1,2,3]]
```

Solution
```
prefixes ::[a] -> [[a]]
prefixes = foldr (\x acc -> [x] : (map ((:) x) acc)) []
```
We can use a fold right. We can to go through the list in reverse. The map takes the element and prepended the prefixes we have to the accumulator. 

##### Exercise 3
Create a function foldrie that folds the elements of a trie in a preorder traversal. So, given a prefix tree, we want to perform a pre-order traversal of the tree.

```
data Trie a = Leaf a | Node a [Trie a]
foldtrie :: (b->a->b) -> b -> Trie a -> b
```

Solution..
```
foldtrie :: (b->a->b) -> b -> Trie a -> b
foldtrie f acc (Lead x) = f acc x
foldtrie f acc (Node x xs) = foldl f' (f acc x) xs
    where
    f' acc t = foldtrie f acc t
```
The case where we have a leaf, we apply the value x to accumulator. Then we look the element within the node which is done with `foldl f' (f acc x) xs` the f prime function is a foldtrie of f. 
