***QUESTION 1.-->> DIFFERENCE B/W BUCKETING AND PARTITIONING***

    ANSWER :
    Similarity:
        both works on the concept of dividing a dataset into parts and scan only required dataset and leave other 
        part of dataset
    FIRST  DIFFERENCES:-->> 
        Each partition is a folder and each bucket is a file
        suppose we have a order table where one column is state and there are values like US,UK,US,Australia,US,UK,INDIA etc
        so in this case if we have to select from this table where state ='' then we will go for partitioning on state column bcz 
        there are less distinct value for state column then folder will bw created for each state like one folder will be created 

    for US and one folder wil be created for UK like this for other state also thus 
    number of partition is eqaul to distinct value in column
    and 
    if we have to select * from table where id=''
    in this case we will go for bucketing with a fixed number of bucket like we can give bucket=4 or bucket=8 etc
    bcz if we go with partitioning in this case then we will end up eith millions of partiton which will reduce the perfomance 

    of processing since there are millions of distinct values in id column.
    thus whenever cardinality of column is high then go with bucket 
    cardinality means number of distinct values

    SECOND DIFERENCE -->>> 
    ----------------------
        partition is logic based means we divide our data on the basis of different state  UK data will go 
        in one folder,US data will go second folder 
        But bucket is not logic based its based on some hash function 

    Thus bucket is good sample of data means bucket has mixed data but partition has only one type of data not from various part


***QUESTION 2.-->> DIFFERENCE BETWEEN ORC AND PARQUET FILE FORMAT***

    ANSWER:
    Similarity : 
        Both of them are column based file format 

    Difference:
        1.ORC is best suited with HIVE and Parquert best suited with spark
        2.Compactness of data-->> ORC is good takes less storage than parquet 
        like if 1 GB data is stored in ORC in 200 MB ,Parquet May take 250 MB to store same data
        3.Parquest is best suited for nested data 
        4.Searches will be faster in case of ORC bcz it uses inbuilt indexes.
        5.Parquet is more generic in nature but ORC specifically design for HIVE thus for other platform Parquet is more compatible than ORC


***QUESTION 3.-->> Difference between Avro and Parquet***

    ANSWER:
    1.Avro is row based file format and Pearquet is column based file format 
    2.Avro provides faster write but slower read while Parquet offers faster read and slowe write 
    3.Avro is quite mature at schema evoluation but parquet just support on end means very limited support in schema evolution
    4.Parquet provides very good support for deeply nested data while avro is used where we have to select all the data not only subset of data 
    means only some columns 
	

***QUESTION 4.-->> Avro VS Parquet Vs ORC***

   ANSWER:
   1.Schema Evolution :Avro-Best then ORC Good then Parquet Ok
   2.Compression :    :ORC-Best then Parquet Good then Avro-Ok
   3.Splitability:    :ORC-Best,Parquet-Good,Avro-Good4
   4.Most Compatible Platform :Avro-Kafka,Druid 
                              :Parquet-Impala,Arrow drill,Spark 
							  :ORC-HIVE,Presto
   5.Read OR Write:
                   Avro-Write
				   Parquet-Read
				   ORC-Read
   6.Row OR Column
                1.Avro-Row
                2.Parquet-Column
                3.ORC-Column

***QUESTION 5.-->> Serde means SER+DE***

ANSWER: 
- SERIALIZATION AND DESERIALIZATION

1. Serialization -->>means converting data in form which can be transfered over the network and stored in files
like in case of java data is converted in bites and transfered over the network and stored in files 
converting from object to bytes which can be shared over the network 

2. Deserialization-->>Reverse of serialization converting the data from a form that can be stored or 
that can be transfered 
over the network into a form which can be read
like in java in deserialzation converting from bytes to object 
    
    -- THUS IN CASE OF HIVE :
              
        -->>When sending over network and storing the data in files hive converts it to a form which is feasible for this and 
        that form is ROW based 
            that is serialization
        -->>When reading it from file ,it tries tto convert it in column which it can understand 
        bcz Hive undertands only columnar data that is deserialization 	
   
	
    Since there is no support for Json in HIVE by default, so we need to add a jar and add it in Hive then hive will understand SERDE.

    SO Basically 
-   1. We get csv file from third party in our hdfs location 
    2. will create a normal hive table on top of this csv file -table1 which is not optimized
    3. will create an optimized table with good file format like ORC/Parquet or Avro-table2
    4. will copy the data from table1 to table2
    5. drop the table table1 nd use table2.

***QUESTION 6. What are Row based and Column Based file formats ?***

1. Row based File format
2. Column based file format

Let's say there is emplloyee table 
employee_id,employee_name,employee_salary,employee_department

1,sumit,1000,sales
2,shilpi,2000,HR
3,shushant,3000,Finance

Row based file ormat look like :
     1,sumit,1000,sales 2,shilpi,2000,HR 3,shushant,3000,Finance
    SO if ANY new record comes then it will be appended in last very simply 
	like below: 
	    1,sumit,1000,sales 2,shilpi,2000,HR 3,shushant,3000,Finance 4,kapil,4000,HR
		
    Now suppose if we want to select employee_id,employee_salary from employee table then 
    it will go and scan all the rows unnecessarily then it will select only employee_id and employee_salary it will degrade the performance 
	Thus writing is easy but reading is not easy if we select subset of column
    Compression is not good bcz we have different datatypes like id is int then name is string again salary is long 

Column based file format look like:
    1,2,3 sumit,shilpi,shushant 1000,2000,3000 Sales,HR,Finance
	in this format if we want to insert any new record suppose 4,kapil,4000,HR then 
	we have to insert id at id place then name at name place and same for salary and department which is mess up 
	thus writing here is not easy 
	But if we want to select employee_id,employee_salary from employee table then 
	it will be easuy and fast  bcz we dont have to read entire rows bcz it knows that where is grouping or id and where is group of salary
	thus reading will be easy here.
    Compression is good 
	bcz in one group let's say id only one type of datatype int is there so it will compress for int what is good then name 
	
que.what is hive 
ans:Hive is a data warehouse software which i used to facilitates querying and managing large dataset rsiding in distributred storage.
Hiive also allows traditional map reduce programm to customize mappers and reducers when it is convenient and inefficient to 
execute the logicin hiveql
Hive is an open source apached project it is a data warehouse software ecosystem under hadoop

que2.where is the hive best suitabnle 
ans :when u r doing data warehouse applications,where u n=r getting static data instead of dynamic data,
when the application on high latency(res[onse time high)
where a large dataset is maintaned and and mind for insights reports
when we r using query instead of scripting 
que3: when hive is not suitable :
ANS: it does not provide OLTP transactions support only OLAP transactions.
if application requires OLTP switch to NoSql databases
HQL query have higher latency due to mapreduce

que 4: Does hive support ACID transactions ?
ANS: yes hive support acid transactions to achieve updates deletion transactions
que 5: what is hive metastore ?
ANS: Metastore is acentral repository of hive that allows to store  metadat in external databases 
by default hive store metadata in Derby databases but u can store in mysql,oracle depends on project.
-----------------------
24. What is a Parquet file?
Parquet is a columnar format file supported by many other data processing systems. Spark SQL performs both read and write operations with Parquet file and consider it be one of the best big data analytics formats so far. 

Parquet is a columnar format, supported by many data processing systems. The advantages of having a columnar storage are as follows:

Columnar storage limits IO operations.
It can fetch specific columns that you need to access.
Columnar storage consumes less space.
It gives better-summarized data and follows type-specific encoding.

21. What is PageRank in GraphX?
PageRank measures the importance of each vertex in a graph, assuming an edge from u to v represents an endorsement of v�s importance by u. For example, if a Twitter user is followed by many others, the user will be ranked highly.

GraphX comes with static and dynamic implementations of PageRank as methods on the PageRank Object. Static PageRank runs for a fixed number of iterations, while dynamic PageRank runs until the ranks converge (i.e., stop changing by more than a specified tolerance). GraphOps allows calling these algorithms directly as methods on Graph.


20. Is there an API for implementing graphs in Spark?
GraphX is the Spark API for graphs and graph-parallel computation. Thus, it extends the Spark RDD with a Resilient Distributed Property Graph.

The property graph is a directed multi-graph which can have multiple edges in parallel. Every edge and vertex have user defined properties associated with it. Here, the parallel edges allow multiple relationships between the same vertices. At a high-level, GraphX extends the Spark RDD abstraction by introducing the Resilient Distributed Property Graph: a directed multigraph with properties attached to each vertex and edge.

To support graph computation, GraphX exposes a set of fundamental operators (e.g., subgraph, joinVertices, and mapReduceTriplets) as well as an optimized variant of the Pregel API. In addition, GraphX includes a growing collection of graph algorithms and builders to simplify graph analytics tasks.

