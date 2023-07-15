# Unshaped Protos: Beyond Code Generation for Protocol Buffers

* Protoless Protos
  * Why? 
    * No code generation
    * interoperability not a conern
    * your case classes
  * Let user create their own case class
    * then use the TypeClass pattern
  * How to do implement toByte Array
    * find size of message
    * writeTo bytes method
      * Option 1 - manual definition
        * cons: boring, tedious, error prone
      * Option 2 - runtime reflection
        * pros: not manual and small code, compiles fast
        * cons: however errors discovered at runtime, slow
      * Option 3 - Generic derivations
        * relies on hlists, shapeless Generic, inductive implicit search
        * shapeless Generic goes from case class -> HList or HList -> case class
        * pros: errors at compile time, relatively fast, custom serialisers
        * cons: unhelpful compiler errors, slower than generated code, decoding: unclear
      * Option 4 - Implicit Macros - compile-time code generation
        * implicit function of the type you want to get
        * define method implementation
        * Type parameter T : WeakTypeTag -> Tree (which is the abstract syntax tree)
        * use quasi-quotes to write scala code
        * Pros: fast, custom serializers, better compiler errors
        * Cons: limited debugging tools





