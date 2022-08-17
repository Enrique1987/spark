# Data Engineer + DE Interview Questions

## Data Engineer Interview Questions
A collection of technical interview questions for Data Engineer position based on my day-to-day experience with Data Engineer real problems.




#### 1) Situation: They are calling you because some ETL processes done in spark are taking a long time and they want to see if you can help them to optimise. What would you do ?
				  
	    Dialog: 	   
		 + The first thing would be to ask ourselves what kind of ETL is it, is it a query that reads
		   from tables in delta lake ? or is it another kind of process where the data comes from an API etc.? 
				   
		 - confirm that it is an etl made by joining different delta lake tables and they are using spark.sql
				   
		 + if you are using spark sql, it might be interesting to have a first look at the query you are using,
   		   in case there is a join without on condigion (cross join) or without filters etc...
					 
		 - Well we assume the SQL query is correct and its alread optimize.
				   
		 + The next thing we need to see is that the tables from which the query reads are correctly optimised ?
				   
		 - What dou you mean by that ?
				   
		 + How the partitioning has been done on those tables, let's imagine that a table is just a reference table that has 40 rows but for some reason it is
		   partitioned into 40 chunks for some reason. this table is causing a lot of problems as it is totally inefficient.

           On the other hand we have a table that we read that it has 1,500,000,000 rows and it is not partitioned, and also columns from this
	       table are used as part of the where condition.... --> so we are interested in partitioning by the column we are going to use for the where condition. 
				   
		 - Great it helps, something else ?
				  
         + For joins between tables, we could use `bloom filters` give better performance because they allow to skip files more efficiently than data skipping.
		   Just build bloom filter on the ID column.
					 
					 
					 
				  
 You are ca You have a Spark dataframe with 1.500.000.000 rows,  would you apply an efficiency strategy when writing the Delta table ? 

