# IO 

So in this blog we're finally going to write Hello World! And you can do this with the following line of code...

```
putStrLn "Hello World"
```

We can save this into a variable
```
hw = putStrLn "Hello World"
hw :: IO()
```
So when we run our program in ghci it should give us "Hello World"

```
ghci > hw
Hello World
```

Now let's look at another IO action
```
getLine :: IO String
```
It reads one line from standard input. Let's look at an example

```
greet :: IO ()   --- not a function application, it an IO ACTION
greet = do 
    putStrLn "What is your name?"
    name <- getLine   --this is where can can work with the result of getLine
    putStrLn ("Hello" ++ name ++ ".")
```

This is how it would like in the terminal 
```
ghci>  greet 
What is your name?
Hagi
Hello Hagi
```


Let's do another example

```
main :: IO()
main = do 
    i <- getLine
    if i /= "quit" then do 
        putStrLn ("Input: "++i)
        main
    else
        return ()  --when the user enter quit, exits the program.
```

Here we can recursively do the IO function and gives us the option to quit. 


It is also possible to have arguments as you can see the example below

```
count :: Int -> Int -> IO ()
count n m = do 
    putStrLn (show n)
    if n < m then 
        count (n+1) m
    else
        return ()
```


### References and Recommendations for Future Reading:
- [IO- Youtube](https://www.youtube.com/watch?v=fP0srOQVGB8&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=15)
- [Intro to IO](https://wiki.haskell.org/Introduction_to_IO)
- [Intro to Haskell IO](https://wiki.haskell.org/Introduction_to_Haskell_IO)
- [Intro to Haskell IO/Actions](https://wiki.haskell.org/Introduction_to_Haskell_IO/Actions)