### Datatypes 

#### Defining Datatypes

data Name = Constructor 1 <args> | Constructor <argv> | ...

So in Haskell we have the chance to create our own datatypes, which are similar to creating a struct in C. For get a better grasp of this idea, here are some examples...

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

#### Differences between data, type and newtype
Type is an allias for types. Let's look at this example 

```
data Color = RBG(Int, Int, Int)
type Palette = [Color]
```

Here the data is Color, and type is Palette-- so alias means that in type checking type and data are the same. 

We could even change the example above to this...

```
type Color = (Int, Int, Int)
type Palette = [Color]
```

So now what is a newtype?

It's like data with only one constructor and only one field!

Let's look at an example:
```
newtype Name = Name String
```
Why is this helpful? Why not using data?

Because its constructor clearly signifies a newtype! But, data can do the same? The newtype and the type of the field are in direct corrospondence (isomorphic). And, newtype is checked at compile time, yet ignored at runtime; thus, no work done when pattern matching)! 

### References and Recommendations for Future Reading:
- [Datatypes - Youtube](https://www.youtube.com/watch?v=7sbxVALuuxA&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=10)
- [data, newtype, type - Youtube](https://www.youtube.com/watch?v=oAiwUAgWKwk&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=21)
- [More on datatypes - Haskell Docs](https://en.wikibooks.org/wiki/Haskell/More_on_datatypes)