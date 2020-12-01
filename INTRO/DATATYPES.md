### Datatypes 

#### Defining Datatypes

data Name = Constructor 1 <args> | Constructor <argv> | ...

So in Haskell we have the chance to create our own datatypes, which are similar to creating a struct in C. For get a better grasp of this idea, here are some examples....

```
data Color = Red | Orange | Yellow | Green | Blue | Magenta

data PeaNum = Succ PeaNum | Zero
--Succ = successor number
add :: PeaNum -> PeaNum -> PeaNum
add Zero n = n
add (Succ m) n = Succ $ add m n

sum :: [PeaNum] -> PeaNum
sum [] = Zero
sum (x:xs) = add x $ sum xs

data Calculation = Add Int Int | Sub Int Int | Mul Int Int | Div Int Int

calc :: Calculation -> Int
calc (Add x y) = x + y
calc (Sub x y) = x - y
calc (Mul x y) = x*y
calc (Div x y) = div x y


data Tree a = Leaf | Node (Tree a) a (Tree a)
tree :: Tree Int
tree = Node (Node Leaf 1 Leaf) 2 (Node (Node Leaf 3 Leaf) 4 Leaf)
```

