### Records

We have seen datatype definitions such as this one..
```
data Person = Person String Int
```
where we define a datatype that include datatype constructors. However, we don't know what "String" or "Int" represent. So as the prgrammer, we would say that the string represent the name, and the int represent the age. But with records, we could do this.

```
data Person = Person {name :: String, age :: Int}
```
Which automatically generates `name::Person -> String` and `age::Person->Int`


However, there are two different sets of issues:
- the narrow issue: namespacing for record field names. Currently in Haskell two records in the same module can't share a field name. 
- the broad issue: first class record types. In Haskell there is no "record type" per se. Rather, you can simply give names to the fields of a constructor. Records are not extensible andd there is no polymorphism on records