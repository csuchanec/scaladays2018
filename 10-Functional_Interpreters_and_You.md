# Functional Inteerpreters and You

@mmynstead - Mark Mynstead
@davegurnell - Dave Furnell

* Program == block of code that computes a result
* General programming languages have a lot of clutter, so a way to deal with this is to create a DSL to hide away these details
  * the drawback is that the DSL has no complier or runtime component
* split this into two parts
  * program - structure
  * interpreter - implementation
* You can write an interpreter and run a lot of different programs
* From a programs view you can have 1 program with different interpreters
  * you could abstract over effects

* Interpreter pattern 
  * re-use interpreters
  * multiple interpreters
  * abstract over effects
  * inspect and rewrite components

* DSL approaches
  * Reification - model programs as data -> Free (Monad)
  * chruch encoding - program as a sets of method calls - Tagless final

* Another axis of considration for DSL - standalone <-> embedded
  * standalone - complety custom and independent of host lnaguage
  * embedded - align with host language - resuse host language features

* Refied encodings
  * A calcualted example
    * val program = () => (1 + 2) * (3 + 4)  <- simplest 
    * you can create an intepreter to run it  - def eval(prog: () => Int) : Int = prog()
      * but there is not much to reason about here so its utility is low, you can only execute

  * simplify the language -> empower the interpreter 
    * the original example is not constrained by changing to a more constrained DSL we can do other things
    * contraints liberate and liberty constrains - 

  * What about types
    * without types you can represent invalid expressions/ones that don't make sense
    * Language mismatch -> complex interpreter 

  * Simplify this by using a typed DSL
    * you can simplify the interpreter as you can lean on the Scala type system to do the interpretation

  * deeper embedding -> simpler interpreter
    * the further you move from the host language them more you will have to write in your interpreter

  * ordering
    * Can we have explicit ordering?
      * Yes we can with monads

  * Monadic DSL
    * FlatMap! 
    * In this case Lit -> Pure[A](value: A) extends Expression[A]
    * FlatMap allows us to the use for comprehension for writing the expression

  * Adding Modadic step makes it more general but has restricted the ability to do inspectability
    * for example you have trouble doing pretty printing or a compiler

  * Do we have to write FlatMap ourselves?
    * Free monadic DSLs
      * Abstract Pure/FlatMap
  *

  * Free provides sequencing
  * Algebra provides steps


  * Lots of boilerplate
    * see Freestyle http://frees.io


* Church Encodings
  * encode programs as scala expressions
  * Simple church encoding
    * each case class becomes a method and each parmeter becomes an argument
  * can't abstract over effects
      * In comes Tagless final encoding (finaly tagless encoding?)
        * church encoding with an additional parameter that allows us to abstract over effects
  * combining DSL's is trivial in the tagless final
  * difficult to inspect
  * less boilerplate than free




