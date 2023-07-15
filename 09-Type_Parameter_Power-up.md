# Type Parameter Power-up!

* Variance
  * in Scala 
      * all values have a type
      * types have supertype relation up to Any
      * types have a subtype relationshipt down to Nothing
      * references cand store subclass instances
      * functions can be passed subclass instances
      * functions can return subclass instances
  * liskov subsititution principle
  * Higer-Kinded Types
    * generic classes
    * types with parameters
  * two axis of subclassing
    * container super/subclass
    * contents super/subclass
  * varience defined - correlation of subtyping relationship of complex types ans subtyping relationship of thier component typs
    * In truth what you are interested in when you can substitute complex types and their component types

  * Invariance - the default case
    * no subclass relationship
    * cannot subsitute Container[T] for Container[U] unless T is U
    * subclasses SubContainer[T] can be subsituted for Container[U]
  * Covariance 
    * subclass relationship when contents have a subclass relationship
    * can subsituted Container[U] for Container[T] if U is a subclass of T
    * useful for extracting the contents of the container
    * problematic when adding or changing values
    * represented by [+T]
  * Contravariance
    * subclass relationship ehen contents have a superclass relationship
    * can subsitute Container[T] for Container[U] if T is a superclass of U
    * useful for processors or consumers of values
      * instances of U can be used when T instance are expected
      * types are sound
      * Consumer[U] can consume T instances
    * problematic when returning or producing values
    * represented by [-A]

  * Positions
    * covariant position - method returns
    * contravariant position - method arguments
    * invariant position - mutable vars

  * When to use
    * Covariance
      * containers
      * producers
      * representing inputs
    * contravariance
      * consumers
      * processors or vistitors
      * represnting outputs
    * invariance
      * distinct types
      * markers or labels
      * influence inference
  * Upper bound - parameter is same or subtype
  * Lower bound - paremert is same or supertype

  * Example case object Nil extends List[Nothing]
    abstract class List[+A]{
      def prepend[B <: A]
    }


  * view bounds - deprecated from 2.11 [A <% B]
  * context Bounds 
    * [A : Ctx]
    * Intidcates A has some context Ctx
      * there exists a Ctx[A] in implicit scope
    * introduces an evidence parameter
      * def ctxBound[X:M](x: X) = ???
      * def ctxBound[X](x: X) (implicyt)

* Typeclass Pattern
  * external implementation of an interface
    * no need to dextend directory
    * possible wihout access to class source
  * introduce via a context bound
  * implement in terms of other instances
    * add[Pair[Int]] defined in terms of Adder[Int]
  * how?[]
    * define an interface
    * implement for your class
    * introduce to implict scope
    * pass to function as implicit parameter
    * call method on interface

* Dotty/Scala 3 changes
  * fundementally the same language
  * variance and type bounds till exist - sessentially the same
  * No existential types
  * Structural types - different implementation

* Takeaways
  * Variance
    * subsitution
    * arises naturally as a consequence of Liskov subsitution
    * deply entwined with subclassing in higher-kinded types
  * Bounds
    * interact with variance -> widening
    * interact with implicits -> typeclasses

@CJPhelps
https://github.com/chrisphelps/type-parameter-power-up