# Maybe 

The Maybe type is defined as follows:
```
data Maybe a = Nothing | Just a
    deriving (Eq,Ord)
```
The Maybe satisfies the type Equation FX = 1+X, where the functor F takes a set to a point plus that set. In comparison to imperative languages, they support this by rewriting as a union or allow one to use/return NULL (define in some manner) to specify a value might not be there. 

So why are Maybe's helpful? there are cases where we want to create functions that don't throw exceptions when there's an error. 

Here's an example of Maybe 
```
safediv :: Integral a => a -> a -> Maybe a
safediv a b =
    if b == 0 then Nothing else Just $ div a b
```

So if we call safediv like this..
```
safediv 10 2
=> Just 5
```
It will return Just 5 according to the condition we included. 


If we call it like this..
```
safediv 10 0
=> Nothing  
```
We get nothing since b == 0. 



#### Importing Data.Maybe

we can import the Data.Maybe module which gives us these functions...

```
isJust :: Maybe a -> Bool
isNothing :: Maybe a -> Bool 
fromJust :: Maybe a -> a
```

IsJust and IsNothing checks if the value is a Just or Nothing constructor,this is important if you want to do filtering or mapping, for example, on a list of maybes. FromJust extracts the element out of a Just and throws an error if its argument is Nothing.

So how would be able to return a maybe to its polymorphic type?
```
fromMaybe :: a-> Maybe a -> a

fromMaybe 3.1415 (Nothing)
=> 3.1415

fromMaybe 3.1415 (Just 2.7183)
=> 2.7183
```
We could write our own conversion function, but we could use fromMaybe to perform the conversion. The example above performs that conversion, where if we get a Nothing, we get the default value back. And, if we use Just then we get the Just value back (2.7183).

### References and Recommendations Future Reading:
- [Haskell Documentation](https://wiki.haskell.org/Maybe)
- [Youtube](https://www.youtube.com/watch?v=O0iohEXMCsU&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=14)