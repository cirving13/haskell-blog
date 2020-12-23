### Either

Before I provide the defintion of the Either keyword or give you specific examples with the Either keyword...let's assume this:

Let's assume that we have some data that can be either an Int or a String. How would we construct a data for that datatype? 

```
data SomeData = Left Int | Right String
```

The above example that shows a data called 'SomeData', with a left constrtuctor that has SomeData as an Int and the right constructor as a String. This way is valid, but what if we want to do it in a polymorphoic way?

```
data Either a b = Left a | Right b

type SomeData = Either Int String 
```

The data "Either"  has two type variables -- a and b. The "Left" is a and the "Right is b. So when we construct a type called "SomeData", for example, can defined as a type alias. 

It's worth to note that Haskell has a module called Data.Either. Let's go over some of the functions that the module provides. 

```
lefts :: [Either a b] -> a
rights :: [Either a b] -> b
isLeft :: Either a b -> Bool
isRight:: Either a b -> Bool 
fromLeft :: a -> Either a b -> a
fromRight :: b -> Either a b -> b
```
The lefts and rights, take a list of either and filter the left and right. The functions isLeft and isRight tell you if the constructor used is left or right, this can be used for filtering for example. And, fromLeft and fromRight as their first arguments take a default value, and try to take a value from left or right. Let's discuss some more functions from the Data.Either module...

```
either :: (a->c) -> (b->c) -> Either a b -> c
```
The either function takes two functions and returns some c. The way to interpret this is that if the input is a Left then the first function (a->c) is applied, and if the input is Right then the second function (b->c) is applied. Now let's look an example, on how to build a function with "either".

```
f = either (\l -> "Number") (\r -> r)

f (Left 1)
=> "Number"

f (Right "Hello")
=> "Hello"
```
In this case, we have an either with Int and String, and takes its arguments (ignores it) and returns a String that's called Number--otherwise we return a value in that constructor. If we apply it to Left 1 we get "Number", and if we apply it to Right "Hello", we get "Hello". Next, let's look at partitionEithers.

```
partitionEither :: [Either a b] -> ([a],[b])

[Left 1, Right "Hello", Left 4, Left 5, Right "World"]
=> ([1,4,5], ["Hello","World"])
```
PartitionEithers takes care of the case when you have a list of Either, you might want to separate the lefts from the rights. Look at the list I provided below the partitionEithers function, the example returns a list of the Left values and another list that contains the Right Values. So why even do this? 

We can do error handinling with Either. Either works like Maybe but Nothiing holds it's own value! Let's look at the two definitions again...

```
data Either a b = Left a | Right b
data Maybe a = Nothing | Just a 
```
At first glance they look that same, the main difference between the two is the Left holds it's own value. And the Nothing in the case of Maybe holds nothing. Nothing represents some error state, and Just represents some correct value. With Either, the same principle applies, where the Left value can represent the incorrect value, and the Right value can represent the correct value. With Either defined this way, you can keep the incorrect value which is something that you might want; whereas with the Maybe keyword you are not able to keep the wrong value. 

## References
- [Haskell Documentation](http://hackage.haskell.org/package/base-4.12.0.0/docs/Data-Either.html)
- [Youtube](https://www.youtube.com/watch?v=IgdZX5wav1Q&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=22)