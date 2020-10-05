# FUNCTIONS

### Higher Order Functions

An example of a higher order function is...

```
app:: (a->b) -> a -> b
app fx = fx

add1 :: Int ->  Int
add1 x = x + 1
app add1 1

=> 2
```