# LIST EXERCISES KEY

#### Exercise #1: Create a fxn elem that returns True if an element is in a given list and returns False otherwise

ANSWER
```
elem:: (Eq a) => a -> [a] -> Bool
elem _ [] = False
elem e (x:xs) = (e == x) || (elem e xs)

```
First, we define our function that receives a list and returns a bool. The second line in the answer above basically says that if there is an empty list, it's automatically false. And in the third line, we search through the whole list--where x is an element in the list, and the list is called xs. Along with searching through the list, we check if an element in the list is equal to the element we're searching for (e), else we keep going through the list. 

#### Exercise #2: Create a removeDups that removes all dups from a given list

ANSWER
```
removeDup :: (Eq a) => [a] -> [a]
removeDup [] = []
removeDup (x:xs)
    | x `elem` xs = removeDup xs
    | otherwise = x:removeDup xs
```
When declaring the function, we do some pattern matching, and then if the list is empty, we automatically return an empty list. And if we have some element x in the list, we check if the element is in xs. Otherwise, if the element x is not a duplicate, we build a new list prepended the element x to it. 

#### Exercise #3: Create a function isAsc that returns True if the list given to it is a list of ascending order 

ANSWER
```
isAsc::[Int] -> Bool
isAsc [] = True
isAsc[x] = True
isAsc (x:y:xs) =
    (x<=y) && isAsc (y:xs)
```

Given a list of integers, we can assume that if the list is empty, the function will return True; and if there is only one element in the list it will return True as well. Otherwise, we look at the first two elements of the list and see if the first is less than the second element. If that is true, we look at the recursive result of isAsc(y:xs).

