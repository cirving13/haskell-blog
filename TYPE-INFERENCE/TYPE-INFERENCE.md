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
===============
### References 
- https://www.cs.cornell.edu/courses/cs3110/2016fa/l/17-inference/lec.pdf
- https://wiki.haskell.org/Type_inference
- https://youtu.be/bv7aenMgSkg
