+++
title = "Experiments 2"
lastmod = "2017-08-26"
date = "2017-08-26"
[elements]
  footer = true
  contact = true
[style]
  center = false
+++

``` r
library(collapsibleTree)
`Locke Data`<-readr::read_csv("SiteDecisionTree.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   L1 = col_character(),
    ##   L2 = col_character(),
    ##   L3 = col_character(),
    ##   URL = col_character()
    ## )

``` r
`Locke Data`$end<-glue::glue('<a href="{url}">{text}</a>',url=`Locke Data`$URL,text=`Locke Data`$L3)

collapsibleTree(
  `Locke Data`,
  c("L1","L2","L3"),
  collapsed = FALSE,
  nodeSize = "leafCount",
  tooltip = TRUE,
  tooltipHtml = "end"
)
```

<!--html_preserve-->

<script type="application/json" data-for="htmlwidget-ca12581a66c86668baef">{"x":{"data":{"name":"Locke Data","SizeOfNode":14.05,"WeightOfNode":"17","children":[{"name":"Company","SizeOfNode":9.64,"WeightOfNode":"8","children":[{"name":"Training","SizeOfNode":5.9,"WeightOfNode":"3","children":[{"name":"On-site training","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Public training","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Onlien training","SizeOfNode":3.41,"WeightOfNode":"1"}]},{"name":"Support","SizeOfNode":3.41,"WeightOfNode":"1","children":[{"name":"Remote Guru","SizeOfNode":3.41,"WeightOfNode":"1"}]},{"name":"Consultancy","SizeOfNode":6.82,"WeightOfNode":"4","children":[{"name":"Getting started with data science","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Help on projects","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Need a review","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Other services","SizeOfNode":3.41,"WeightOfNode":"1"}]}]},{"name":"Person","SizeOfNode":10.22,"WeightOfNode":"9","children":[{"name":"Read","SizeOfNode":4.82,"WeightOfNode":"2","children":[{"name":"Books","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Blog","SizeOfNode":3.41,"WeightOfNode":"1"}]},{"name":"Events","SizeOfNode":4.82,"WeightOfNode":"2","children":[{"name":"Upcoming events","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Past talks and slides","SizeOfNode":3.41,"WeightOfNode":"1"}]},{"name":"Online","SizeOfNode":7.62,"WeightOfNode":"5","children":[{"name":"Learn R by email","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Newsletter","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"GitHub","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Packages","SizeOfNode":3.41,"WeightOfNode":"1"},{"name":"Videos","SizeOfNode":3.41,"WeightOfNode":"1"}]}]}]},"options":{"hierarchy":["L1","L2","L3"],"input":null,"attribute":"leafCount","linkLength":null,"fontSize":10,"tooltip":true,"collapsed":false,"zoomable":true,"margin":{"top":20,"bottom":20,"left":79.05,"right":190},"fill":"lightsteelblue"}},"evals":[],"jsHooks":[]}</script>
<!--/html_preserve-->

