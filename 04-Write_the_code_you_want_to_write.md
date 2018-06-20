# Write the code you want to write

* Procedural/non-FP/OO paradigm code with threading - hard to figure out how did you get into the state you got into
    * Syntax is easy to understand at point of change
* FP Change management Problems
  * Code is hard to read, write, and rason about? - really? Don't think I agree with this point.
    * Illustrate with deep copy to make this argument
  * Copying things is not free

* Referential Transperancy
  * Given the same input, guaranteed to get the call with its result and have no impact on the result of the program
  * Gives us
    * order independence
    * parallism
    * Asynchronousity
    * caching/memoization

* Solution space
  *  Node construct
    * annotation to guarantee that the function is referentially transparent
    * Don't compile with normal compiler instead use scala async compiler that builds a state machine
  * Scheduler - nodes create work queue and then scheduler can make an execution plan 
    * This is cache aware
  * Caching - 
    * use function as a cache key with parameters, then add instance identity, and scenario
      * entity annotation to give identity to 
  * scenario a collection of tweaks
    * a tweak is an intention to change the code
    * use @node annotation to be able to change the value
    * Basically this is create a base then a delta to change states before getting to the result


