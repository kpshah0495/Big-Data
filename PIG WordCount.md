# Implement Map-Reduce WordCount Example using PIG Queries

## In this Tutorial we will see some PIG Queries to solve a probelm in which we are given a text file and have to count the Frequency of each word occuring in the File

***Lets Start..***




# Step1: Create a directory in HDFS and create a text File in local

In this step we will create a Directory ***pig_wordcount*** in our HDFS,
then we Create a Text File wordcout.txt and then
we use ***-put*** command to tranfer the file in local to our HDFS pig_wordcount directory

<img src ="PIG WORD COUNT/1.create directory,file and put into HDFS.JPG" width=1000>

# Step 2 : See the Contents of File Created 

<img src = "PIG WORD COUNT/2.see the content of the file.JPG" width = 1000>

Kindly ignore the contents of file as it is self created.

# Step 3:Use pig command 

***Use pig command to execute PIG queries in MapReduce Mode***

This will Start the ***GRUNT*** Shell

<img src = "PIG WORD COUNT/3.use pig command to work in mapreduce mode that is grunt shell.JPG" width = 1000>

# Step 4 : Load the DATA

We will use ***pigdata*** relation to load our file FROM HDFS
We Will Use ***dump*** comamnd to view the output

<img src = "PIG WORD COUNT/4.Load Data and View Output.JPG" width = 1000>

***Lets Check the output***

<img src = "PIG WORD COUNT/5.Output.JPG" width = 1000>

We can see our ouput as same as our text file

# Step 5:Use Of Foreach and Tokenize Command

We Will use the ***FOREACH** command for Data transfomation and use ***FLATTEN Tokenize*** to split each word and store as single tuple

<img src = "PIG WORD COUNT/6.Foreach command.JPG" width = 1000>

Lets Check the Output


<img src = "PIG WORD COUNT/7.foreach output.JPG" width = 1000>

We can Notice each word is splitted and stored individually as a Tuple.

# Step 6 : Group similar words

We will now group same words by using ***GROUP*** command

<img src = "PIG WORD COUNT/8.Group words.JPG" width = 1000>

Lets check the output 

<img src = "PIG WORD COUNT/9.Output of Group.JPG" width = 1000>

Here we can see a Bag is Created containg same words together

# Step 7 : Display Frequency of Each Word

We will use ***COUNT*** operator to count the frequncy of each word

<img src = "PIG WORD COUNT/10.word_count.JPG" width = 1000>

Lets Check Our ***FINAL*** output

<img src = "PIG WORD COUNT/11.Final output.JPG" width = 1000>


### Finally We have Accomplished our task to solve the problem of counting the occurence of same words in the text file


















