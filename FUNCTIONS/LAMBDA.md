# Lambdas

Lambdas are basically anonymous functions that are used because we need some functions only once. 

The symbol for lambda is \ and then the parameters are separated by spaces. After that we used the -> symbol and then the function body. 

Here's an example of the application of lammbda in ghci..
```
zipWith (\a b -> (a*30+3)/b) [5,4,3,2,1] [1,2,3,4,5]

=> [153.0,61.5,31.0,15.75,6.6]
```

So like normal functions, we can pattern match in lambdas. The only difference between the two is that you can't define several patterns for one parameter, like making a [] and an (x:xs) pattern for the same parameter and then having values fall through. If a pattern matching fails in a lambda, a runtime error occurs, so be careful when pattern matching in lambdas! 