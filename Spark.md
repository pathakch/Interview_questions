24. WHAT IS A PARQUET FILE?
Parquet is a columnar format file supported by many other data processing systems. 
Spark SQL performs both read and write operations with Parquet file and consider it 
be one of the best big data analytics formats so far. 

Parquet is a columnar format, supported by many data processing systems. The advantages of having a columnar storage are as follows:

Columnar storage limits IO operations.
It can fetch specific columns that you need to access.
Columnar storage consumes less space.
It gives better-summarized data and follows type-specific encoding.

21. What is PageRank in GraphX?
PageRank measures the importance of each vertex in a graph, assuming an edge from u to v represents an endorsement of v’s importance by u. 
For example, if a Twitter 

user is followed by many others, the user will be ranked highly.

GraphX comes with static and dynamic implementations of PageRank as methods on the PageRank Object. Static PageRank runs for a fixed number of iterations, while 

dynamic PageRank runs until the ranks converge (i.e., stop changing by more than a specified tolerance). GraphOps allows calling these algorithms directly as methods 

on Graph.


20. IS THERE AN API FOR IMPLEMENTING GRAPHS IN SPARK?
GraphX is the Spark API for graphs and graph-parallel computation. Thus, it extends the Spark RDD with a Resilient Distributed Property Graph.

The property graph is a directed multi-graph which can have multiple edges in parallel. Every edge and vertex have user defined properties associated with it. Here, 

the parallel edges allow multiple relationships between the same vertices. At a high-level, GraphX extends the Spark RDD abstraction by introducing the Resilient 

Distributed Property Graph: a directed multigraph with properties attached to each vertex and edge.

To support graph computation, GraphX exposes a set of fundamental operators (e.g., subgraph, joinVertices, and mapReduceTriplets) as well as an optimized variant of 

the Pregel API. In addition, GraphX includes a growing collection of graph algorithms and builders to simplify graph analytics tasks.
-----------------------
BIG DATA SPARK

Big data(2015 starts):-->>structured,semi structured,unstructured data
structure/traditional data -any data which is in row column ex-csv,rdbms table,excel data 
analysing structured data-We can analyse structured data in excel or in oracle table format easily
semi structured :ex xml file,json file 
some sort of structured but not fully structured like row column format ex-json has key value format 
unstructured data : do not have any kind of structure example: audio file,video file 

Big data -size of the data is really huge in order of terabyte,petabyte 
not only big it's also complex 
real life example -black box data in flight ,everydata store 10 k our 15k data 
social media data is also big data :like facebook/twitter
Size is not only the factor 

5 PROPERTIES OF BIG DATA 
1.volume : size of dsata 
2.variety: different types of data 
3.velocity: deals the speed o data from which data is coming 
4.Value:
5.veracity:talks about quality of data -->>

What is Hadoop: created in 2006
is a platform storing big data across a spectrun of devices 
helps to store and analyse the big data 
open source 
uses parallel processing to analyse huge amount of data 
it's computational layer-mapreduce
storage : hdfs

hadoop gets installed on group of machines
lets say three machine 
each one has 5 terabyte hard disk
all machine 2 cpu 16gb ram 

when install hadoop in all these three machine 

now hadoop will use total 15 TB storage it's called hadoop cluster 

there is 1000 machine in one cluster in real time 

Hadoop can leverage all the three machine cpu and RAM and process the data 

APache Spark :Distributed processing engine for big data 
spark can be installed on top of hadoop 

hadooop will store all the data and spark will process the data 

Runs 100 times faster than hadoop map reduce 
Map reduce is very old big data processing engine 
if we install hadoop by default we will get map reduce engine 

Ease of use 
language 
java scala R python sql 
Java is prefered when 
Spark is written in scala 
so source code is written in scala 
What about python :
Using spark u can do ML on big data 
R is for those people who are coming from data science 
Spark sql is most used in industries

Generality 
Combine sql analytics and streaming 
lets take example of e commerce company 
want to use ml to recommend new products to users 
2nd think 
if they want to analyse the test is called NLP 
thwy would like to analyse chat windows means want to analyse the mood of customers 

ALso they want to 
they like to real time analysis of user data 
by looking at what users are searching on website,they can offer real time deal 

Now s[park can do all above mentioned analyti=cs 

RUns everywhere 
Spark is platform independent 
u can install anywhere 


RDBMS very costly 
u can process 100 terabyte data on oracle but cost of license is very high 

Used cases o Apache Spark AMazon ALibaba,baidue,databricks,ebay,hexabnib,IBM,hitachi,NASA,yahoo,TripAdviser

Spark created in 2009 
university in barkleys 
these people ctreated databricks 
Databricks provides community addition to create our own cluster of 15 GB here 15 GB will work as RAM and 
also this cluster provides some 10 GB of ROM
Databricks has its own notebook where we can not only analyse the data but visualize the data also
 
 
val df=Spark.read.json to read any json file then create a dataframe from this json file 
no need to define any schema and all 
