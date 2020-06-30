# LAB 1 : Implement HDFS Commands using  AWS EMR Hadoop Cluster

## About this Lab:
***Objective*** --> To become familiar with how files are added to and removed from HDFS and how to view files in HDFS.

***Successful outcome*** --> You will have added and deleted several files and folders in HDFS.

So Lets Start Step by Step:

# 1.View The hdfs dfs command:
Enter this command  ***hdfs dfs*** to view usage of hdfs dfs

<img src = 'Lab Day 1/1.hdfs dfs command to view content.JPG' width =1000>

# 2.Create a Directory in HDFS
Enter the following ***hdfs dfs -ls*** command to view the contents of the user’s root directory in HDFS

<img src='Lab Day 1/2.hdfs dfs -ls ....No output.JPG' widht = 1000>

You do not have any files in /user/root yet, so no output is displayed.

Run the -ls command again, but this time specify the root HDFS folder:

***hdfs dfs -ls /***

<img src='Lab Day 1/3.-ls backslash.....to view contents in root user.JPG' width = 1000>
 
a.Enter ***hdfs dfs -mkdir kps_lab1*** command to create a directory named kps_lab1 in HDFS
    
b.Enter ***hdfs dfs -ls*** command to verify that the folder was created successfully:
    
<img src='Lab Day 1/4.create directory and verify.JPG' width = 1000>

Create a couple of subdirectories for kps_lab1:

Use Command : ***hdfs dfs -mkdir -p kps_lab1/dbda/bigdta***

<img src='Lab Day 1/5.create multiple directory.JPG' width = 1000>
 
When you use command ***hdfs dfs -ls*** You can view only kps_lab1 directory.
 
To recursively view the contents of a folder 
Use Command:

***hdfs dfs -ls -R***

<img src='Lab Day 1/6.to view all directory.JPG' width = 1000>

# 3.Delete a Directory

Delete the bigdata folder (and recursively, its subcontents) using the 

***hdfs dfs -rm -R kps_lab1/dbda/bigdata*** command

<img src='Lab Day 1/7.deleting directory.JPG' width = 1000>

To Verify Deletion use command :

***hdfs dfs -ls -R***

<img src='Lab Day 1/8.verify deletion.JPG' width = 1000>

# 4.Upload a File to HDFS

First we will change our direcotry where our file is located

We use Command 

***cd labs/Lab2.1***

Then to view its Content we type ***ls***

We find our File ***data.txt*** which we need to ***upload to HDFS***

<img src='Lab Day 1/9.Change directory and view its contents.JPG' width = 1000>

To copy data.txt into the test folder in HDFS:

We use -put command like:

***hdfs dfs -put data.txt kps_lab1***

To verify that the file is in HDFS by listing the contents of kps_lab1

We use Command :

***hdfs dfs -ls kps_lab1***

<img src='Lab Day 1/10.-put command.JPG' width = 1000>

# 5.Copy a File in HDFS

Now copy the data.txt file in kps_lab1 to another folder in HDFS using the ***-cp*** command:

***hdfs dfs -cp test/data.txt kps_lab1/dbda/data2.txt***

Verify that the file is in both places by using the command

***hdfs dfs -ls -R kps_lab1*** 

<img src='Lab Day 1/11. Copy command and verify.JPG' width = 1000>

Now delete the data2.txt file using

***hdfs dfs -rm ks_lab1/dbda/data2.txt***

<img src='Lab Day 1/12.Deleting the data2 file.JPG' width = 1000>

# 6.View the Contents of a File in HDFS

You can use the ***-cat*** command to view text files in HDFS. 

Enter ***hdfs dfs -cat kps_lab1/data.txt*** to view the contents of data.txt

<img src='Lab Day 1/13.To View content use -cat.JPG' width = 1000>

You can also use the ***‐tail*** command to view the end of a file

<img src='Lab Day 1/14.tail command to view content.JPG' width = 1000>

# 7.Getting a File from HDFS

We use the ***-get*** command to get file from local to HDFS

<img src='Lab Day 1/15.get command to copy file from hdfs to local tmp folder.JPG' width = 1000>

# 8.The getmerge Command

We First Put the smallblocks.txt file from local to HDFS and View its content

<img src='Lab Day 1/16.Put smallblocks in kps_lab.JPG' width = 1000>

Now we check what files we have in kps_lab1 directory

<img src='Lab Day 1/17.view contents of kps_lab1.JPG' width = 1000>

We use ***-getmerge*** command to merge all files in kps_lab1 and put in tmp with file named merged.txt

<img src='Lab Day 1/18.Merge command and view contets.JPG' width = 1000>

Using ***-cat** command we can see the contents of merged.txt 

<img src='Lab Day 1/19.Using cat merged.JPG' width = 1000>

# 9.Specify the Block Size

The blocksize is defined using the ***dfs.blocksize*** property on the command line.

<img src='Lab Day 1/20.BlocksizeCommand.JPG' width = 1000>


***Result -> You should now be comfortable with executing the various HDFS commands, including creating directories, putting files into HDFS, 
copying files out of HDFS, and deleting files and folders.***




















