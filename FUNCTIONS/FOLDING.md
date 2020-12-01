### Folding (foldr,foldl)

In functional programming, fold (aka reduce) is a family of higher order funcctions that process a data structure in some order and build a return value. So when you 'unfold' functions they take a starting value and apply it to a function to generate a data structure. 

Typicaly, a fold deals with two things: a combining function, and a data structure, typically a list of elements. The fold function would then proceed to combine elements of the data structure using the function in some systematic way. Consider the example below....

```
fold (+) [1,2,3,4,5]
->1+2+3+4+5 -> 15
```

In the example, we can see that for each element in the list a '+' is added after each element. 

#### Folding Direction - foldl, foldr
foldr = fold right...start from right to left
foldr (\elem acc -> <term>) <start_acc> <list>

foldl = fold left...start from left to right
foldl (\acc elem -> <term>) <start_acc> <list>


#### Folding Exercises 


