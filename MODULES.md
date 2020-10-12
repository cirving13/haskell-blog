# Modules 

#### What is a module? Why us them?

A Haskell module is a collection of related functions, types and typeclasses. A Haskell program is essentially a collecction of modules where the main module loads up the other modulesand then uses the functions defined in them to do something. So having code split up into several modules has some advantages when you come across more complex problems. If a module is generic, the functions it exports can be used in a multitude of different programs. If your code is separated into self-contained modules which don't rely on ecah other too much, you can reuse them later. 

#### Importing modules

The syntax for importing modules is `import <module name>`, which has to be done before defining functions (at the top of the file).

#### Example

In this example we will use the Data.List module, which has a bunch of useful functions for working with lists, to tell us how mnay unqiue elements a list has. 

```
import Data.List

numUniques :: (Eq a) => [a] -> Int
numUniques = length . nub
```

When you import a module, its exports become available in the global namespace, meaning that you can call them from wherever. `nub`, in the example below, is a function defined in Data.List that takes a list and weeds out duplicate elements. 