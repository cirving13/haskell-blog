# Folding Exercises 

### Exercise # 1: Create a function 'rev' that reverses a list. 

```
rev :: [a] -> [a]
```

### Exercise 2
Create a function prefixes that return all the prefixes of a given list.

```
prefixes :: [a] -> [[a]]
prefixes [1,2,3] => [[1],[1,2],[1,2,3]]
```

### Exercise 3
Create a function foldrie that folds the elements of a trie in a preorder traversal. So, given a prefix tree, we want to perform a pre-order traversal of the tree.

```
data Trie a = Leaf a | Node a [Trie a]
foldtrie :: (b->a->b) -> b -> Trie a -> b
```


#### To check your work look at FOLDING-EXERCISES-KEY