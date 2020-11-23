# LISTS 

So in Python you can have a list with a string, integer, or whatever you want in it. But, in Haskell, that's not the case. Lists in Haskell can only have 1 enternal type. For example, this is our Haskell interprets a list....

```
[1,2,3,4,5] :: [Integer]

-- ONLY ONE ENTERNAL TYPE!!!

```

How are lists constructed? 

```
[]
x:xs
```
Every element (x) is prepend  to the list (xs). For example....

```
1: 2: 3: 4: 5 : []
^start           ^end
```

# TUPLES

Tuples, unlike lists, don't have to be homogenuous. 
They're usually in this form..

```
(1,2):: (Int,Int)  --remember that they don't have to be homogenuous
```


# LIST COMPREHENSION

Why is this legal in Haskell?

```
[(x,y) | x<- [1,2,3],  y<-['a','b']]

=> [(1,'a'), (1,'b'), (2,'a'), (2,'b'), (3,'a'), (3,'b')]
```

Remember that tuples are not restricted to one data type. So we can create a list of tuples to have a collection of different data types. 

