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
  
* val type does not allow re assignment but allows appending
 ``` val builder1 = new StringBuilder; builder1 += 'A';builder1 += 'C'; println(builder1)```: ```AC```
 
* lazy evaluation:
  * it is pretty intuitive but the coding can go tricky
  ```
  val builder = new StringBuilder

  val x = { builder += 'x'; 1 }
  lazy val y = { builder += 'y'; 2 }
  def z = { builder += 'z'; 3 }

  z + y + x + z + y + x

  builder.result() shouldBe 
  "xzyz"

  ```
  * Let us see in details how it works and results in "xzyz":
    * Note that x and y are val; though y is lazy it is a val. Therefore, both will have the value only once.
    * z is definition/function without parameter and hence will execute the fixed operation each time called.
    * Now, since x is defined first, value 'x' goes into to builder for the first and last time and also x gets a value 1
    * size y is defined lazy 'y' does not goes into builder at the time of definition and also would not get value 2
    * z is not lazy but it is a function and hence it would not put value 'z' into builder until called.
    
    * Now let us look at the execution order:
      * 'z' value is appended to builder and 3 is in memory ==> Output: xz and sum = 3
      * 'y' value si appended to builder and 2 gets added to 3 ==> Output: xzy and sum = 5
      * 1 gets added to 5 ==> Output: xzy and sum = 6
      * 'z' value is appended to builder and 3 gets added to 6 ==> output xzyz and sum = 9
      * 2 gets added to 9 ==> Output: xzyz and sum = 12
      * 1 gets added to 12 ==> Output: builder = xzyz and sum = 13
      
      
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

* difference between foreach and map : https://stackoverflow.com/questions/17080186/difference-between-map-and-foreach-method-in-scala
 * foreach does not have any return of values and works on the same principle as that of map
 * map works on each of the items on which it is applied (usually list) and return the set of transformed items.

* Imperative programming : https://www.scala-exercises.org/scala_tutorial/imperative_programming
 * to see the python like value assignment we need to have the variable declared as var x : Any. This would allow x to have value of an integer or a string too or for that matter "Any"thing.
 
* ```(1 until 3).foreach(i=> "abcd".foreach(j => println(s"$i $j")))```
  * for each of 1,2 values associate each of "abcd". How? println inthis just a simple association. It could be anything. Note that foreach takes a function that operates on one instance of the var to which it is associated. This function can be anonymous. Anymous function do not have name but like other function operates on variable and hence starts witha variable and right hand side of "=>" this determines the body of it.

 * ```(1 until 3).foreach(x => println(x)) : Note that ``` : Note that here we did not mention the data type of x. Even if you mentioned data type it would fail with syntax error. The reason being the foreach function takes the array or object on which it is being used as reference and provide the same to println. Therefore no data type is required.
 
 * ```val aa = {i:Any => println(i)} ; aa("abcd","abcd")```: ```(abcd,abcd)``` = Here we need to define the type of the variable i because it is being passed to it and hence it has to be explicit about what is being passed and nothing to infer about the data type. Note that here it can take any number of argumets :)
 
 * ```val states = Map("AL" -> List(1,2,3,4), "AK" -> "Alaska"); states("AL")``` : equivalent to python dictionary
    * states += ("KA"-> "Karnataka") would fail here because states is "val" but works fine if it was "var"
    
* Type Classes:
  * to define a generic class which can cater to different class type.

* partial function vs curried function:
```
def isInRange(left: Int, right: Int, n: Int): Boolean = {
    if (left < n && n < right) true else false
}


val a = (isInRange _).curried

val b = a(10)

val c=  b(30)



val abc = isInRange(20, 30,_ :Int)

println(abc(0))

println(c(0))
```
* Let us read the above code:
 * isInRange will take 3 parameter; 3rd parameter is check for existing between first 2 parameters.
 * now curried function let us create a function with respect each of those parameters in isInRange function.
   * note that here it lets you create a function with respect one parameter only
 * however, partial functions lets u change multiple parameter at a go.
 * That does not say partial is better over curried.
   * curried not only simplifies the code 
   * and also confirms that we have addressed all the parameters
