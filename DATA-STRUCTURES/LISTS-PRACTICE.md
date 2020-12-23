# LIST EXERCISES

- Exercise #1: Create a fxn elem that returns True if an element is in a given list and returns False otherwise

```
elem:: (Eq a) => a -> [a] -> Bool
elem _ [] = False
elem e (x:xs) = (e == x) || (elem e xs)

```

- Exercise #2: Create a removeDups that removes all dups from a given list

```
removeDup :: (Eq a) => a -> [a]
removeDup [] = []
removeDup (x:xs)
    | x `elem` xs = removeDup xs
    | otherwise = x:removeDup xs
```

- Exercise #3: Create a function isAsc that returns True if the list given to it is a list of ascending order 

```
isAsc::[Int] -> Bool
isAsc [] = True
isAsc[x] = True
isAsc (x:y:xs) =
    (x<=y) && isAsc (y:xs)
```



WILL ADD MORE ......

- Exercise #4: 