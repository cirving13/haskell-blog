#### IO 

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
        return ()
```