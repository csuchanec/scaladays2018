# Keeping the fun in functional

* Spark
  * Built on top of two abstractions RDDs & Datasets
  * What is the magic of Spark?
    * automatically distributed functional programming
    * DAG/ "query plan"
    * Optimizer to cobine steps
    * resiliency
    * in memory + spill-to-disk
    * select operations without desrialization
* what are the problems
  * serialization complications - makes people think closures are more limited than they can be
  * lots of Map[String, String] settings
  * hard to debug
  * New ML & SQL APis without "any" types
* DataFrames/Datasets
  * DataFrames - everything is a Row
  * Datasets - types are useful
  * More SQL inspired than functional inspired
  * stared with no fn ops or types
  * schema inference
  * Datasets 
    * mix functional & relational style
    * Strongly typed
    * Tungsten - better serialization
    * potential better language interop
* Spark API seems to have a lot of missing types needed
* Spark ML Pipelines
  * scikit inspired
  * no types
* Apache Arrow
  * integrated in Spark 2.3
  * Doesn't deal with datetimes well or something like that?