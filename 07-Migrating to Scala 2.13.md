Migrating to Scala 2.13

* Features
    * simplfying collections
    * compiler performance
    * modularizing the standard library
    * User friendliness

* M4 merged, M5 August 10

* Prepare for migration
  * remove deprecated calls that are deprecated in 2.13
* Compiler flags removed
* Cleanup on 2.12 - argument adaptation /auto tupling
  * 2.14 will adhere to dotty rules
* parallell collections have been moved to a separate module
  * won't be available until for m5 (not available yet with new collection library)
* scala-xml is no longer a transitive dependency of scala-compiler


* scala-collection-compat - used if you need to deal with cross compile and old collections

* Goals of colelction redesign
  * Simpler user-facing API
  * Correct operation implementations for non-strict collections
  * simpler internal heerarchy ( no Gen... types)

Major incompatabilities
  * scala.Seq is now scala.collection.immutable.Seq
    * same for IndexedSeq
    * consistent with Set and Map
    * why was this not the case before - varargs uses scala.Seq
    * Wrapped Java varargs pretend the array is immutable
    * using the new s.c.i.ArraySeq
    * A deprecated impicit converstion makes a copy of the array
  * CanBuildFrom replaced by BuildFrom
    * flatMap no longer need it
    * used in methods like Future.sequence
    * Factory allows target type-driven building (like CanBuild in 2.12) 
    * General rule: UseBuildFrom to rebuild with the best matching type of an existing source collection, otherwise use Factory
 


