# Lab Day 2 --> Sqoop Implementation

# TASK 1 : Importing RDBMS Data into HDFS 

***Objective : Import data from a database into HDFS using Sqoop.***

***Successful outcome: You will have imported data from MySQL into folders in HDFS.***

***Before you begin: Your Hadoop cluster on EMR (with Sqoop) should be up and running***

***For this Lab we are using AWS RDS Service for Our MYSQL RDBMS***

***We have Imported Data into our RDBMS and this we will use to import into HDFS***

***LETS START***

# Step 1 : Import the Table into HDFS

Enter the following Sqoop command which imports the salaries table in the salaries database into HDFS:

***sqoop import --connect jdbc:mysql://(your AWS RDS URL)/salaries --username (your username)  --password (Your Password) --table salaries***

<img src = 'Lab Day 2 Screen Shots/1.import table.JPG' height = 300 width = 1000>

A MapReduce job should start executing, and it may take a couple of minutes for
the job to complete.

Once Import is completed at the end You will see Number of Retirved records in our case it is 50 Records

<img src = 'Lab Day 2 Screen Shots/2.check imporrted norecords.JPG' width = 1000>


# Step 2: Verify the Import

To View the contents of your HDFS folder use Command :

***hdfs dfs -ls salaries***

<img src = 'Lab Day 2 Screen Shots/3.view contents of salaries in HDFS.JPG' width = 1000>

Notice there are four new files in the salaries folder.Why are there four of these files?

***Answer: The MapReduce job that executed the Sqoop command used four
mappers, so there are four output files (one from each mapper).***


***Now Let See Contents of any one of the file***

<img src = 'Lab Day 2 Screen Shots/4.contents of each mapper.JPG' width = 1000>

# Step 3: Specify Columns to Import

***We Will use ‐‐columns argument, to import the salary and age columns (in that order) 
of the salaries table into a directory in HDFS named salaries_new. 
In addition, we will set the ‐m argument to 1 so that the result is a single file.***

<img src = 'Lab Day 2 Screen Shots/5.mapper set to1.JPG' width = 1000>

Now Lets see The Contents in new_salaries..

<img src = 'Lab Day 2 Screen Shots/6.Contents of Mapper in salaries_new.JPG' width = 1000>

# Step 4: Importing from a Query

***Now we will use --split-by command to split our data on basis of gender columm also we will use --query command with where clause to extract data on some conditions
put it into new directory named salaries_split***

Note : While Importing we encounterd a error so With import we used "-Dorg.apache.sqoop.splitter.allow_text_splitter="true"

<img src = 'Lab Day 2 Screen Shots/7.split command.JPG' width = 1000>

Based on our condition specified we can see only 5 records have been imported

<img src = 'Lab Day 2 Screen Shots/8.split command output.JPG' width = 1000>

Lets see the contents in new imported directory salaries_split

<img src="Lab Day 2 Screen Shots/9.content in split.JPG" width = 1000>

Lets Check The Contents of both files in salaries_split

<img src="Lab Day 2 Screen Shots/10.contents in m1 and m2 of split.JPG" width = 1000>


***Here We Have Finished our Task 1 of Importing data from MySQL to HDFS using the entire table, specific columns, and
also using the result of a query.***

# Task 2 : Exporting HDFS Data to an RDBMS

***Objective: Export data from HDFS into a MySQL table using Sqoop.***

***Successful outcome: The data in salarydata.txt in HDFS will appear in a table in MySQL named salaries_kps.***

### Lets Start 

# Step 1 : Create a new hdfs directory

Use comand ***hdfs dfs -mkdir salarydata*** to create a new directory in HDFS

<img src="Lab Day 2 Screen Shots/13.Salaraydata.JPG" width = 1000>

# Step 2 : Put the created salarydata.txt to HDFS Directory Salarydata

Use Command ***hdfs dfs -put salarydata.txt salarydata***

<img src="Lab Day 2 Screen Shots/13.Salaraydata.JPG" width = 1000>


# Step 3 : Create a table in MYSQL

Create a new Table in the Database as salaries_kps using following sql command

***create table salaries2 ( gender varchar(1), age int, salary double, zipcode int);***

<img src = "Lab Day 2 Screen Shots/sql command.JPG" width =1000>



# Step 4 : Export the Data

Run a Sqoop command that exports the salarydata folder in HDFS into the
salaries2 table in MySQL.

<img src = "Lab Day 2 Screen Shots/11.Export command.JPG" width =1000>

# Step 5 : Verify All records are exported to your RDBMS

Run Query ***SELECT * FROM SALARIES_KPS***

Your output will contain all 10000 records

<img src = "Lab Day 2 Screen Shots/12.Sql output.JPG" width =1000>


***Here we have finished our Task 2 where we have used Sqoop to export data from HDFS into a database table in MySQL.***



















