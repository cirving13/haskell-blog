### Typeclasses 

```
(+) :: Num a => a->a->a
```
a has to have an instance of the Num type. So a typeclass defines some functions that need to be defined in a class and for a type to be in that type class is has to have an instance of such a class. 

```
sum :: Num p => [p] -> p
sum [] = 0
sum (x:xs) = x + sum xs
```

Another example of a typeclass is when we open ghci and type ':info Num'

```
ghci> :info Num 
class Num a where 
(+) :: a->a->a
(-) :: a->a->a
(*) :: a->a->a
negate :: a->a
abs ::a->a
signum :: a->a
fromInteger :: Integer -> a
```
it gives us the information on the types that are defined in the Num typeclass. 

```
ghci> :info Show 
class Show a where 
    showsPrec :: Int -> a -> ShowS
    show :: a-> String 
    showList :: [a] -> ShowS
    {-3 MINIMAL showsPrec |show #-}
```
the last line tells us that we don't need to create all the three functions. We need to create showsPrec or show. We also see this in the Eq class.

```
ghci> :info Eq 
class Eq a where 
    (==) :: a->a->Bool
    (/= :: a->a->Bool)
    {-# MINIMAL (==) | (/=) #-}
```
Here we only need to make == or /=.


```
ghci > :info Ord 
class Eq a => Ord a where 
    compare :: a->a->Ordering 
    (<) :: a ->a->Bool
    (<=) :: a->a->Bool
    (>) :: a->a->Bool
    max :: a->a->a
    min :: a->a->a
    {-# MINIMAL compare | (<=) #-}
```
what `class Eq a=> Ord a` means is that numbers can be ordered can also be checked for equivalence. 


##### Deriving Typeclasses
Deriving typeclasses can be benficial if you want your data types to be printable, and if you don't want to write new instances of the show typeclasses. 

```
data Temperature = C Float | F Float 
    deriving (Show,Eq)
```
In this case the dervied equivalence is the following:

```
Dervied equivalence:
    (==) (C n) (C m) = n == m
    (==) (F n) (F m) = n ==m 
    (==) _ _ = False
```


### References and Recommendations for Future Reading:
- [Typeclasses - Youtube](https://www.youtube.com/watch?v=1txgSlcpQmo&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=13)

- [Typeclasses](http://learnyouahaskell.com/types-and-typeclasses)

- [Typeclassse - Real World Haskell](http://book.realworldhaskell.org/read/using-typeclasses.html)