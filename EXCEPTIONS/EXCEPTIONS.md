# Exceptions in Haskell

An exception, in general, is an event that occurs during the execution of a program that disrupts the normal flow of instructions. If you want to use Exceptions in Haskell you can use `import Control.Exception`. It's important to note that in Haskell, an exception is a typeclass that contains three functions: toException, fromException, displayException.


To define your own exception you should follow this format:
```
data MyError = ErrorA | Error B deriving Show
```

So how do we throw an exception? It means that exceptions may be thrown from purely functional ccode, but may only be caught within the IO monad. The phrase "may only be caught within the IO monad" is important because purely functional code does not know how to deal with exceptions. This is why,for a long time, Haskell didn't have any IO. 

In order to "catch" something, we have the catch function:
```
catch :: Excecption e => IO a -> (e-> IO a) -> IO a
```
It gets an IO action, some handler function, and produces the new IO monad. Catch is called like this...

```
catch ioAction execeptionHander
```

Here's a full example of catching...

```
import Control.Exception 

data MyError = Error deriving Show 
instance Exception MyError
failing :: IO ()
failing = do
    throw Error 

main :: IO()
main = do
    catch failing (\e :: MyError) -> do
    putStrLn "Something went wrong!"
    )
```
### Exercise: Try compiling the above code using XScopedTypeVariables

### Are exceptions a good idea in Haskell?

In Haskell, it would be better to have purely functional code. Meaning purely functional code shouldn't touch exceptions (since exceptions are not part of what it means to be pure functional code). Instead, I would recommend using Maybe and Either, since those aree are purely functional.



### References and Recommendations for Future Reading:
- [Exception - Haskell Docs](https://hackage.haskell.org/package/base-4.12.0.0/docs/Control-Exception.html)
- [Handling Errors in Haskell](https://wiki.haskell.org/Handling_errors_in_Haskell)
- [Haskell Compiler User's Guide](https://downloads.haskell.org/~ghc/latest/docs/html/users_guide/glasgow_exts.html)
- [What's an Exception and Why Do I Care?](http://www.upv.es/~jgonsol/tutorial/java/exceptions/definition.html#:~:text=Definition%3A%20An%20exception%20is%20an,the%20normal%20flow%20of%20instructions.&text=The%20exception%20object%20contains%20information,program%20when%20the%20error%20occurred.)