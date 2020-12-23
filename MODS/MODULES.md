# Modules 

#### What is a module? Why us them?

A Haskell module is a collection of related functions, types and typeclasses. A Haskell program is essentially a collection of modules where the main module loads up the other modules and then uses the functions defined in them to do something. So having code split up into several modules has some advantages when you come across more complex problems. If a module is generic, the functions it exports can be used in a multitude of different programs. If your code is separated into self-contained modules which don't rely on ecah other too much, you can reuse them later. 

#### Importing modules

The syntax for importing modules is `import <module name>`, which has to be done before defining functions (at the top of the file).

We can also using the hiding keyword--the hiding keyword basically says that they want to import everything besides certain functionalities. Take a look at the example below.

```
import Module hiding (name1,name2)
```

Then there is the qualified keyword, which forces the user to put the name of the module, in front of the name imported from that module. This is helpful when you're importing several modules that have the same function names.

```
import qualified Module
Module.name
```

The "as" keyword renames modules. 
```
import Module as NewName
```

Now what if you want to import a specific constructor? Look at the example below...
```
data DataType = A | B | C

import Module (DataType(..))
import Module (DataType(A))
import Module (DataType(A,B))
```

The first import statement imports all the constructors (because it uses '..'), and the second one only imports A. The third, imports A and B, but not C.

#### Defining Modules 

Now what if we want to make and organize our own modules?

Well first, we can only have one module per file, and when we call it we want it in this format...

```
Module name = File name (without ,,.hs")
```

Let's look at an example where the root contains Main.hs and Foo.hs. Below are the defintions, or the way we would call these modules.

```
(Foo.hs)
module Foo where

(Main.hs)
import Foo
```

Now let's say that Foo.hs is in a directory called Bar. So in the files we can have to change this and add the directory name, Bar, as the prefix. 

```
(Foo.hs)
module Bar.Foo where

(Main.hs)
import Bar.Foo
```


#### Example

In this example we will use the Data.List module, which has a bunch of useful functions for working with lists, to tell us how mnay unqiue elements a list has. 

```
import Data.List

numUniques :: (Eq a) => [a] -> Int
numUniques = length . nub
```

When you import a module, its exports become available in the global namespace, meaning that you can call them from wherever. The word "nub", in the example above, is a function defined in Data.List that takes a list and weeds out duplicate elements. 


### References and Recommendations for Future Reading:
- [Learn you Haskell](http://learnyouahaskell.com/modules#loading-modules)
- [Youtube](https://www.youtube.com/watch?v=SGSrjUoi29U&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV&index=23)
- [Haskell Documentation](https://www.haskell.org/onlinereport/modules.html)