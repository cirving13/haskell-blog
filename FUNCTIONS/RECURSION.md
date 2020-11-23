# RECUSION

### Recusion
So...there are no loops, but we can 'loop' through recursion. 

*you need a refresher on recusion check out the link below*
https://www.geeksforgeeks.org/recursion/

Here's an example of recursion in Haskell...
``` 
fac n = 
    if n <= 1 then 
        1
    else 
        n * fac(n-1)
```

In this (^) example the recusion happens in our else statement, more specifically in face(n-1). In this instance, we decrement our n argument by 1 and multplify by n. 

### Guards 

Guards are essentially a way of testing whether some property of a value (or several of them) are true or false. I know that it sounds very similar to an if statement and it's very similar. So why use them? The advantage is that guards are a lot more readable when you have several conditions. Here's an example below. 

```
fac n 
    | n <= 1 = 1
    | otherwise = n * fac(n-1)
```

Looks familiar right? Well this is essentially the same as our fac function from earlier--instead of if statement we're using guards. The first if statement (n <=1) is the same as if n<=1 then return 1. And our else statement is using the keyword 'otherwise'. Otherwise is defined simply as otherwise = True and catches everything. 


### Accumulators

Accumulators are functions take a number n, and returns a function that takes another number i and returns a functions that takes another number i and return n incremented by i. This is basically another way of implementing a recursive functioin. 

```
fac n = aux n 1 
    where 
      aux n acc 
        | n <= 1 = acc  --returns a constant value
        | otherwise = acc (n-1) (n*acc)  --direct recursive call, this is a tail recursive function; which won't call a stack overflow

```

The same thing in Java...

```
fac n;
acc = 1;
while(True){
    if(n<=1){
        return acc;
    }
    else{
        n=n-1;
        acc=n*acc;
    }
}
```
