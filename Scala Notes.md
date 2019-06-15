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

* Either, Left, Right
  * in "Some" case we have either type of the variable or None case
  * In Either case we can have type of the variable or any specified type.
  * Right keyword explicitly mentions it is 2nd type in Either case
  * Similarly, Left indicates the first type mentioned in the Either declaration.
  * fetching left or right value
  ```
  val aa = Left(2)
  println( aa.left.get == 2) ==> true
  println(aa.right.get == 2) ==> 
  java.util.NoSuchElementException: Either.right.value on Left
  ```
* tuples:

```
val a  = (1,2)
val (b,c) = a
println(b,c)

Here b = 1 and c is 2
```

* OOPs
  * default variables inside class is public, need to specify private to make it private
  ```
  class abc(x:Int){
  val xx = x
  }

  println(new abc(10).xx)
  ```
  * Not only defines a class but also constructor
  * auxillary constructor - this constructor
  * abstract class = cannot have object instantiation, may or may not define function, class extending can override the method and parameter
  * def + (x : class_name) = operator overriding
