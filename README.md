tag-graph-map-of-stackexchange
==============================

Generates map in form of a graph from tags
on [StackExchange sites](http://stackexchange.com/sites),
e.g. [StackOverflow](http://stackoverflow.com).

Started as [an entry for StackExchange visualization competition at Kaggle](https://www.kaggle.com/c/predict-closed-questions-on-stack-overflow/prospector#211).

Current state:

* with queries from [SE Data Explorer](http://data.stackexchange.com) (but it works for any other csv tables for any other tags, as long as it is in the same form)
* some other stuff

To do:

* interactive d3js graphs
* plots for beta sites and for Area51 

==============================

And example use:

data.stackexchange.com -> csv -> oetable2graphml.py -> graphml -> gephi -> pdf


- To get data, use [a data.SE query](http://data.stackexchange.com/stackoverflow/query/83415/)
to obtain table of tag [co-occurrences](http://stats.stackexchange.com/questions/40977/is-there-a-term-for-pa-cap-b-papb);
[my other queries](http://data.stackexchange.com/users/8877/piotr-migdal)

- Run oetable2graphml.py to convert it to graphml file (requires [NetworkX](http://networkx.lanl.gov/)), e.g.

<code>python oetable2graphml.py input.csv output.graphml</code>

- Use [Gephi](http://gephi.org) to import graphml file and process it to your taste.<br>
E.g. (on Gephi 0.8.1 beta): 

* Overview tab:
 * Ranking -> Nodes -> Size -> weight -> Min:15, Max:30, Spline:3 -> Run <br>
  (optimal options may vary)
 * Layout -> ARF -> Run <br>
  OR: Layout -> Force Atlas -> Run; Layout -> Fruchterman Reingold -> Run <br>
  (and you may like to experiment with parameters or other methods)
 * Layout -> Noverlap -> Run
 * Statistics -> Modularity -> Run
 * Partition -> Nodes -> Refresh -> Modularity Class -> Apply <br>
  (and optionally choosing colors to your taste)
 * Font size: 26pt, Node size, Show node labels
 * Layout -> Label Adjust -> Run
* Preview tab: 
 * Nodes -> Border Color: #A0A0A0
 * Node Labels -> Show Labels: True, Font: 4pt  
 * Edges -> Opacity: 40.0
 * Refresh; Export

