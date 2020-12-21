### Type inferencec 

- a type inference is a feature of the type system which means that concrete tytpes are deduced by the type system wherever it is obvious. If you add an integere variable x to a numeric literal 2, then the type system concludes that 2, which in principle can represent 2 for every number type, musta also be an integer, since + support only addition of numbers of the same type. (This restriction is a good thing, as we explain for the idea of a Generic number type)

- Here an example:
```
map :: (a-> b) -> [a] -> [b]
Char.ord :: (Char -> Int)
```
For the expression `map ord` the type cchecker finds out that the type variable `a` must be bound to the type Char and `b` must be buond to Int and thus it concludes

```
map ord :: [Char] -> [Int]
```

- The goal of type inferences is too reconstruct types of expression based on known types of some symbols that occur in expressions. These are especially useful in managing the types of higher-order functions. In functional languages (for example, C++) is the following

```
auto x = e; //declarese variable x, initialized with expression e, and type of x is automatically inferred
decltype(e)   //is a type that means "whatever type e has"
```

#### Type checking vs type inferences

standard type checking:
```
int f(int x) {return x+1;};
int g(int y) {return f(y+1)*2;};
```
- uses declared types to ccheck agreement 

type inference:
```
f(x) {return x+1;};
g(y) {return f(y+1)*2};
```
- infer the most general types that could have been declared

#### Why study type inference?
- reduces syntactic overhead of expressive types 
- guaranteed to produce most general type 
- widely regarded as important languagee innovation
- illustrative example of a flow-insensitive static analysis algorithm

#### step by step on how to implement typeinference 

1) assign every variable a unique typevariable
2) assign every function its type with next unique type variables
3) for each subexpression of the expression generate equations of types
4) resolve the equations until no further simplifications can be done. Cconflicting types iimply a type error otherwiise the type has been inferred! 

Here's a full example of implementing typeinference in Haskell
```
add x y z = (x+y) : z
x :: a
y :: b
z :: c
```
Here we have a function add, that contaiins three arguments: x,y,z. Where the sum of x and y are prepended to z. 
But can we not infer that z has to be list? Yes, but if we do we can get type define errors.


```
add x y z = (x+y) : z
x :: a
y :: b          (+) :: (Num d) => d -> d -> d
z :: c          (:) :: e-> [e] -> [e]

from (x+y) derive a = d and b = d
from (x+y) : z derive [e] = c and d = e
```

For the functions `(+)` and `(-)`, those are defined above as type signatures. We have a unique type variables d and e. 

Let's look at the first x+y, the plus operator's first argument is d and d. Here we specify that a is d and b is d. 
In the second one, it specifies that d must be an element within the list (e) and c must be a list that must contains elements of e. 


```
add x y z = (x+y) : z
x :: a
y :: b          (+) :: (Num d) => d -> d -> d
z :: c          (:) :: e-> [e] -> [e]

from (x+y) derive a = d and b = d
from (x+y) : z derive [e] = c and d = e

x::d y::d z::[e] z::[d]
```
Now that there are not other subexpressions to look at. The question is how do we get at the result. The last line is the last piece of the puzzle--establishing the rules. Here's the full and complete example...


```
add :: (Num d) => d -> d -> [d] -> [d]
add x y z = (x+y) : z

(+) :: (Num d) => d -> d -> d
(:) :: e-> [e] -> [e]

x::d y::d z::[e] z::[d]
```

Now let's try to use typeinference in partial function application!

```
f = reverse. sort

reverse :: [a] -> [a]
(.) :: (c->d) -> (b->c) -> b -> d
sort :: Ord e => [e] -> [e]
```
Since we don't have any variables, we don't hav eany variables that we can assign a type to, we can skip the first stage ( assign every variable a unique typevariable). So now we cacn derive rules for the last three lines (referring to the example above) .

```
f = reverse. sort

reverse :: [a] -> [a]
(.) :: (c->d) -> (b->c) -> b -> d
sort :: Ord e => [e] -> [e]


-- rules...
from reverse . sort derive 
b = [e], c = [e], c = [a], d = [a], a = e
```
We can imply that a must equal to e, so we know that Ord a =. [a] -> [a]. So with the rule a = e, we can rewrite a so that it's equal to a list of e's.

===============
### References 
- https://www.cs.cornell.edu/courses/cs3110/2016fa/l/17-inference/lec.pdf
- https://wiki.haskell.org/Type_inference
- https://youtu.be/bv7aenMgSkg
