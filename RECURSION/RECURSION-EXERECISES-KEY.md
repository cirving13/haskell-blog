# LISTS, RECURSION, and FUNCTIONS   KEY

### 1. Implement the select_evens function

```
select_evens :: [Int] -> [Int]
select_evens [] =  []
select_evens (x:xs) = if x `mod` 2 == 0
                        then x : select_evens xs 
                        else select_evens xs

main = print(select_evens [1,2,3]) 
```

#### 2. Implement the select_odds function
```
select_odds :: [Int] -> [Int]
select_odds [] =  []
select_odds (x:xs) = if x `mod` 2 == 1 
                        then x : select_odds xs 
                        else select_odds xs

main = print(select_odds [1,2,3])
```
### 3. Implement the member function

```
member :: Eq a => a -> [a] -> Bool
member a [] = False
member a (x:xs)
  | a == x = True
  | otherwise = member a xs

main= print(member 3 [1,2,3])
```

### 4. Implement the append function
```
appendNum :: a -> [a] -> [a]
appendNum n [] = [n]
appendNum n (x:xs) = x : appendNum n xs

main =  print(appendNum 8 [1,2,3,4,5])
```

### 5. Implement the less_equal function
```
lessEqual :: [Int] -> [Int] -> Bool
lessEqual [] [] = True
lessEqual (x:xs) (y:ys) 
    | x > y = False
    | otherwise = lessEqual xs ys
main = print(lessEqual [1,2,3] [2,3,2])
```

### 6. Implement the zipp function
```
zipp :: [a] -> [a] -> [a]
zipp xs     []     = xs
zipp []     ys     = ys
zipp (x:xs) (y:ys) = x : y : zipp xs ys

main = print(zipp [1,2,3] [4,5,6,7,8])
```