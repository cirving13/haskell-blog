# FUNCTIONS

### Higher Order Functions
Higher-order functions are functions that take other functions as arguments or returns a function as a result. 

An example of a higher order function is...

```
app:: (a->b) -> a -> b
app fx = fx

add1 :: Int ->  Int
add1 x = x + 1
app add1 1

=> 2
```

In fact, many functions in the haskell libraries are higher-order. Some of them include map and fold. 

Below is an example that shows the difference between higher-order functions and other types of functions are...

For instance, we could write..

```
doubleList [] = []
doubleList (x:xs) =  2*x : doubleList xs
```
and 

```
tripleList [] = []
tripleList (x:xs)  = 3*x : tripleList xs
```

we can write ....

```
multList n [] = []
multList n (x:xs) = n*x : multList n xs
```
and define them as...

```
tripleList = multList 3
doubleList = multList 2
```

So clearly the advantage of higher-order functions is concise code and less error prone defintions.

### Anonymous Functions

An anonymous function is function without a name, and a lambda abstraction. These functions essentially increment its parameters...for example in GHCI...

```
Prompt> (\x -> x + 1) 4
5 :: Integer
```

Another example is ...
```
Prompt> (\x y -> x + y) 3 5
8 :: Integer
```

Here is the syntax for anonymous functions
```
(\<args> -> <expr>)
```

Keep in mind that these type of functions are similar to lambda calculus, which we will talk about later

To get a clearer picture and a better understanding of anonymous functions, here are some more examples

```
(\x y z -> x+y+z) 1 2 3
=> 6
```

Let's look at a more advanced example.
```
map (\x -> x+1) [1,2,3,4,5]
=> [2,3,4,5,6]
```
In this implementation of a map function, for each element x in the list is added by 1. A similar idea is shown in the example below 

```
map (\(x,y) -> x+y) [(1,2),(2,3),(3,4)]
=> [3,5,7]
```

### Currying 

Currying is the process of transforming a function that takes multiple arguments in a tuple as its argument, into a function that takes just a single argument and returns another function which accepts further arguments, one by one, that the original function would receive in teh rest of that tuple.

For example...
```
f :: a-> (b-> c)  --which can also be written as f::a->b->c
```
is the curried form of
```
g::(a,b) -> c
```

### Function Composition
Function composition is the act of pipelining the result of one function, to the input of another, creating an entirely new function.

This is performed with any two functions, where the argument type of the first is the return type of the second. The newly created function takes what the second function would as a parameter and feeds it through the second funcction, then the result of the second function through the first function, and returns the result of the first function. In Haskell, the dot operator is used to compose function.

```
(.) :: (b->c) -> (a->b) -> a -> c
(f . g) equiv. to (\x -> f (g x))
```

Here's an example of function composition

```
-- result of sort is pipelilned to reverse 
desort = (reverse . sort)

-- the result is a descending sort 
countdown = desort [2,8,7,10,1,9]
```
The example just presented is the equivalent to...
```
\x -> reverse(sort x)
```


