# How We Built Tools That Scale To Millions of Lines of Code

* Need semantic tools
  * not enought to treat programs like text

* Existing Semantic APIS (as of 2017)
  * compiler internals
  * scala.reflect (thin wrapper around compiler internals)
  * scalasignatures (serialization format for compiler internals)

  * Blcokers
    * Learning curve
      * complicated ata modle and arcae preconditions 
      * span dozens of modules and thousands of methods
    * Scarce documenation
      * Scala requires and extensive smantic API
      * There is a lot od documentation
      * the documentation significantly lagging behind
    * Compiler instance
      * requires a compiler instance
      * poor performance for simple operations like "go to definition" or "find all usages"
      * tools that use scala complier interals write their own indexer or accept the limitations
    

