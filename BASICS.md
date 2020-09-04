# The Basics

### Data Types

- Int: Intergers that are bounded 
- Integer: Intergers that are not bounded
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

#### .. Built-In Math Functions...for fun?
Just for future reference, I wrote down some built-in math functions below. You can skip this tbh.

`piVal = pi`

