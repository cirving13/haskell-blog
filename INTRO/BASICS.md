# The Basics

### Functional vs Imperative Programming

- Functional Programming  
    - We are interested in pure (mathematical) functions
    - Immutable data, cannot be changed in place 
    - no/less side-effects
    - Declarative
    - Easier to verify, because we can mathematically prove the correctness of our algorithms

#### Declarative (aka Functional) vs. Imperative  -- shown in code

    *Imperative*
    ``` 
    int sum (int *arr, int length) {
        int i, sum = 0;
        for(i=0;i<length;i++){
            sum+=arr[i]
        }
    }  
    ```  
    In the imperative approach, we explicitly tell the program what to do at each step.  

    *Declarative*  

    ```
    sum [] = 0
    sum (x:xs) = x + sum xs
    
            OR

    sum = foldr (+) 0
    ```  
    In the declarative approach, we define what it means to have a sum (sum [] = 0, where the sum of an empty list is 0). Then, in the second line, we say a list with at least one element (x) is plus whatever the rest of the sum is. 

### Lazy vs. Strict  

Lazy  

```
func arg = 
    let x = func1 arg
        y = func2 arg
        z = func3 arg
    in 
    if z then x else y

```  

Strict  
```
int func(int arg){
    int x = func1(arg);
    int y = func2(arg);
    int z = func3(arg);

    if(z){
        return x;
    } else {
        return y;
    }
}
```

When a compiler encounters an expression, usually it tries to evaluate it. The style of only evaluating what's needed is called lazy evaluation , while the opposite (evaluating immediately) is called strict evaluation. If you wanna see what that looks like in code, look at the examples above. 

### Types  
Every value in Haskell has a type, and that type is strict.  
`name :: <type>`  

Here are some examples...

```  
x::Integer  
x = 1  
```

```
y::Bool
y = True
```

```
z::Float
z = 3.1415
```

I've provided some more data types below...  

- Int: Integers that are bounded 
- Integer: Integers that are not bounded
- Float: A decimal that is only up to the tenths place (i.e. 0.1)
- Double: A decimal that goes up the 14 places after the decimal point.
- Bool: A boolean that results in True or False
    - Must be exactly ... *True* or *False*
- Char: an enumeration whose values represent Unicode code points
- String: a list of characters

Now that we understand the data types, let's try to incorporate functional programming concepts while running some basic math functions. To prevent any confusion, I'll use a common math function- sqrt. 

Let's type `:t sqrt` in the terminal. The below should appear on the terminal.

`sqrt :: Floating a => a -> a`

So if you're use to programming in Java or Python, you're probably completely lost. Don't worry, I was too. 

The first part `Floating a` refers to the programming 'thinking' it's going to receive floating point number `a` (i.e. 3.2).  The remaining portion of the code `a -> a` refers to the function receive a value `a` and outputing a value `a`. So you're probably thinking, what if we just want an Int?  

`num9 = 9 :: Int`  

`sqrtOf9 = sqrt(fromIntegral num9)` 

In the first line we are declaring a variable `num9` as an Int with the value of 9 (*not an Integer*). The second is calculating the square root of 9 using the `fromIntegral` built function which converts an Int to a Float. As we saw before, the `sqrt` function usually return a Float and now we're returning an Int. Using this keyword, we get 3 instead of 3.0, if we didn't include `fromIntegral` 

### Functions
- Defintion  
`name arg1 arg2 .. argn = <expr>  `
- Application
`name arg1 arg2 .. argn`  

Note: there are no parentheses  
- Examples
```
in_range min max x = 
    x >= min && x <= max
```
checks if x is between min and max. The second line is written as a function call. Realize that a return statement is not include. 

```
in_range 0 5 3
    => True
```

```
in_range 4 5 3
    => False
```

Now here are some more "complicated" functions.   
```
1. in_range :: Integer -> Integer -> Integer -> Bool
2. in_range min max x = x >= min && x <= max

3. in_range 0.5  1.5  1       TYPE ERROR
4. in_range 0    5    3       CORRECT :)
```
At line 1 in the example above, we're stating that we want three Integer inputs and and output that is of type Bool.  

```
in_range min max x = 
    in_lower_bound = min <= x;
    in_upper_bound = max >= x;
    return (in_lower_bound && in_upper_bound);
```
Now in this example, we can see that this is imperative, not declarative! So let's convert this to Haskell using let bindings which allows us to evaluate them when we need them.   
```
in_range min max x = 
    let in_lower_bound = min <= x
        in_upper_bound = max >= x
    in 
    in_lower_bound && in_uppper_bound
```

Or we can use where bindings...where you have the final result of your function. 
```
in_range min max x = ilb & iub
 where
  ilb = min <= x
  iub = max >= x
```

To allow some program flow in your program, you can use if statements.
```
in_range min max x = 
 if ilb then iub else False
 where 
  ilb = min <= x
  iub = max >= x
```

- Infix Functions  
These type of functions allow us to write the function in between the arguments. 

```
ghci> :t (+)
(+) :: Num a => a -> a-> a 
```  
The above us to see the data type used in a function. We'll go more into depth later, but just know that there are different ways to write functions.  
```
add a b = a+b
add 10 20     

-- the above and below statements are the same

10 `add` 20
```
### Basic Operations

#### 1. Module  

`modEx = mod 5 4`  
prints  

`modEx2 = 5 'mod' 4`  
prints 1, using quotes prints the exact result


#### 2. Arithmetic 

Operations: +, -, *, /, ^ (or **)

Note: if you want to add negative numbers you need to surround a negative number with parentheses. See the example below

`negNumEx = 5 + (-4)`

#### 3. Boolean
`trueAndFalse = True && False`  
`trueOrFalse = True || False`  

&& = and  
|| = or  

`notTrue = not(True)`  
  
The output would be False.  


### References:
- [Quick Intro to Haskell](https://wiki.haskell.org/Learn_Haskell_in_10_minutes)
- [Youtube - Imperative v. Declarative](https://www.youtube.com/watch?v=Vgu82wiiZ90&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=1)