# LISTS, RECURSION, and FUNCTIONS

#### 1. Calculate the length of a list
`len [] = 0`  
`len(x:xs) = 1 + len xs`  
`main = print(len[1,2,3])`  

#### 2. Implement the`even` function 
`even 4`  
The even function determines if a value is even, returns True or False

#### 3. Implement the `odd` function
`odd 3`  
The odd function determines if a value is odd, returns True or False  

#### 4. Implement the append function  
`'C' : ['H','e','l','l','o']`  
returns `"CHello"`  

#### 5. Implement the `reverse` function  
`reverse[1..5]`  
returns `5,4,3,2,1`  

#### 6. Implement the `zip` function
`zip[1..5]['a'..'e']`  
returns `[(1,'a'),(2,'b'),(3,'c'),(4,'d'),(5,'e')]`


--------------------------------------------

#### 7. Implement a function that calculate the factorial
`fac 0 = 1`  
`fac n = n * fac(n-1)`  
`main = print(fac 42)`  

---------------------------------------------
#### 8. Select_Evens function

```
select_odds :: [Int] -> [Int]
select_odds [] =  []
select_odds (x:xs) = if x `mod` 2 == 0
                        then x : select_odds xs 
                        else select_odds xs

main = print(select_odds [1,2,3]) 
```

#### 9. Select_odds function
```
select_odds :: [Int] -> [Int]
select_odds [] =  []
select_odds (x:xs) = if x `mod` 2 == 1 
                        then x : select_odds xs 
                        else select_odds xs

main = print(select_odds [1,2,3])
```

#### 10. Member function

we could use...
```
4 `elem` [3,4,5,6]  
```
in Prelude, but in order to understand functions and functional programming 
we are gonna do it from  scratch  :(


```
member :: Eq a => a -> [a] -> Bool
member a [] = False
member a (x:xs)
  | a == x = True
  | otherwise = member a xs

main= print(member 3 [1,2,3])
```

#### 11. Append function
```
appendNum :: a -> [a] -> [a]
appendNum n [] = [n]
appendNum n (x:xs) = x : appendNum n xs

main =  print(appendNum 8 [1,2,3,4,5])
```

#### 12. Revert function
```
main = do 
   let x = [1..10]  
   putStrLn "Original list is:" 
   print (x) 
   putStrLn "The list in Reverse Order is:" 
   print (reverse x)
```

#### 13. Less_equal function
```
lessEqual :: [Int] -> [Int] -> Bool
lessEqual [] [] = True
lessEqual (x:xs) (y:ys) 
    | x > y = False
    | otherwise = lessEqual xs ys
main = print(lessEqual [1,2,3] [2,3,2])
```

#### 14. Zipp function
```
zipp :: [a] -> [a] -> [a]
zipp xs     []     = xs
zipp []     ys     = ys
zipp (x:xs) (y:ys) = x : y : zipp xs ys

main = print(zipp [1,2,3] [4,5,6,7,8])
```

#### 15. Merge functoini
```
mergeLists :: [Int] -> [Int] -> [Int]
mergeLists xs ys = foldr (:) ys xs
main = print(mergeLists [1,2,3] [4,5,6])
```
#### 16. Implement merge-sort
```
mergeSort :: (Ord a) => [a] -> [a]
mergeSort [] = []
mergeSort [a] = [a]
mergeSort a =
  merge (mergeSort firstFew) (mergeSort lastFew)
    where firstFew = take ((length a) `div` 2) a
          lastFew = drop ((length a) `div` 2) a
-- Expects a and b to already be sorted
merge :: (Ord a) => [a] -> [a] -> [a]
merge a [] = a
merge [] b = b
merge (a:as) (b:bs)
  | a < b     = a:(merge as (b:bs))
  | otherwise = b:(merge (a:as) bs)

main = print(mergeSort [3,1,4,5,2])
