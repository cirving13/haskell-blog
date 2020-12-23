# Recursion

### Recusion
So...there are no loops, but we can 'loop' through recursion. 

you need a refresher on recusion check out this [link](https://www.geeksforgeeks.org/recursion/)


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

Another way of implementing recursive functions is with accumulators. In an acccumulator, you can accumulate some result, which is done in the example below. 
```
fac n = aux n 1 
    where 
      aux n acc 
        | n <= 1 = acc  --if n<=1 then we return our acc
        | otherwise = acc (n-1) (n*acc)  --we update n (we decrement n by one) and multiply the acc by n.

```

The same thing in Java (using imperative programming)...

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
In this case, the "recursion" is done with a while loop, and if n<= 1 we can return the accumulator. If n is not <= 1, we update our n value and our acc value. 

### Try out some exercises in RECURSIONS-EXERCISES

### References and Recommendations for Future Readings:
- [Functions, Accumulators, Guards - Youtube](https://www.youtube.com/watch?v=y6xiaSkVlvs&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=3)
- [Accumulators - Haskell Docs](https://wiki.haskell.org/Performance/Accumulating_parameter)
