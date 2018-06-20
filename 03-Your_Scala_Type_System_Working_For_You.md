# Your Scala Type System Working For You

* Web Mercator model used by Bing, Google, etc is wrong (Finland ~35 miles from where it should be)
* Raster data assumes equal area pixels but this doesn't work in large scale with a sphere
* Raster images assume constant images
* Coordinate reference systems (CRS) - # -> location
  * projections CRS -> CRS
  * projection + datum defines how CRS relate
  * can convert from one CRS to another with varying amounts of error
  * 
* There are many CRS and they can overlap and its critical not to get them mixed up or you will get the wrong data in an undetectable way

* Most systems do runtime CRS checks

* By making a implicit refrence to itself in the companion object it will always be abvailable in the case class
