### Maybe 
The Maybe type is defined as follows:
```
data Maybe a = Nothing | Just a
    deriving (Eq,Ord)
```
The Maybe satisfies the type Equation FX = 1+X, where the functor F takes a set to a point plus that set. In comparison to imperative languages, they support this by rewriting as a union or allow one to use/return NULL (define in some manner) to specify a value might not be there. 

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
this is important if you want to do filtering or mapping, for example, on a list of maybes

So how would be return a maybe to its polymorphic type
