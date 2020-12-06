### Datatypes 

#### Defining Datatypes

data Name = Constructor 1 <args> | Constructor <argv> | ...

So in Haskell we have the chance to create our own datatypes, which are similar to creating a struct in C. For get a better grasp of this idea, here are some examples....

#### Example 1
```
data Color = Red | Orange | Yellow | Green | Blue | Magenta
```
In this example, we're creating a datatype called Color where it has types red,orange,yellow and so on.


#### Example 2
```
data PeaNum = Succ PeaNum | Zero
--Succ = successor number
add :: PeaNum -> PeaNum -> PeaNum
add Zero n = n
add (Succ m) n = Succ $ add m n

sum :: [PeaNum] -> PeaNum
sum [] = Zero
sum (x:xs) = add x $ sum xs
```
In the add function, a datatype Peanum could be a Zero or a Successor function. So the function itseld deals with the case where PeaNum could be Zero or a Successor number.

#### Example 3

```
data Calculation = Add Int Int | Sub Int Int | Mul Int Int | Div Int Int

calc :: Calculation -> Int
calc (Add x y) = x + y
calc (Sub x y) = x - y
calc (Mul x y) = x*y
calc (Div x y) = div x y
```
In the datatype Calculator, it include the type of functions that we can perform: add, subtract, multiple and divide. Also of which, by the way, take intergers. 

