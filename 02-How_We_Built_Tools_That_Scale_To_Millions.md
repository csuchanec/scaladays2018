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

Future sematic APIS (Dotty)
  * scala.reflect is based on scala compiler internals - so it was discarded
  * Tasty - serialization format for Dotty compiler internals
  * Used in Dotty IDE & the upcoming macro system


Tasty 
 * does still leak some internals
 * looks similar to scala.reflect but reimplemented for Dotty
   * still basd on the cpmiler
   * still undocumented
   * still requires a compiler instance

Scalameta
  * focused on tool writers

Semantic DB
  * data model for semantic information about programs
  * Focused on what tool writers need for the complier
  * uses protobuf specifications for the interchange format

  * compiler plugin or command line tool ot generate


* Metadoc - web based tool to navigate code based (cli generates the code)
  * generate Semantic DB files and then injest them
* metals - foundation for an IDE - https://geirsson.com/assets/metals
  * bring scalamet based tools ot the editor
  * integrated with scalafix & scalafmt

* Company-wide semantic index
  * doesn't require a compiler instance
  * can be fast even on huged codebases
  * can be put into a SQLite datbase and ~500Mb per 1 M LOC and queiry in 10 ms
* Company-wide language servcer
  * experimental LSP implementation backed by semantic index

* Code review - can support go to definition
eburmako@twitter.com 




