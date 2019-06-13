##### Scala notes continued from Structuring information : https://www.scala-exercises.org/scala_tutorial/structuring_information
* case class to group the related data
* seal trait to define set of values for variable, compiler warning in case of not handling all the cases.
* equal to operator can perform the comparison between objects.


##### https://www.scala-exercises.org/scala_tutorial/higher_order_functions
* anonymous function
  * why do we need to have x=>x ???
* Higher order function : function taking function as argument or returing function as value


##### https://www.scala-exercises.org/scala_tutorial/standard_library
* right association
```
println(1 :: (5 to 10) ::xs) ==> List(1, Range(5, 6, 7, 8, 9, 10), 2, 3, 4)

println(xs .:: (5 to 10) .:: (1)) ==> List(1, Range(5, 6, 7, 8, 9, 10), 2, 3, 4)

println(1 :: xs .:: (2)) ==> List(1, 2, 2, 3, 4)
```
* optional value : may have None or Some()
 
 ```
 def abc : Option[String] = if (true) None else Some("1")
abc
 ```
