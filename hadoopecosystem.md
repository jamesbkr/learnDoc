# Hadoop Ecosystem
### Big Data:
##### 4 Vs of big data
* Volume
* Variety
* Velocity
* Veracity
### Data Science:
The process of using statistical and mathematical analysis to gain buisness value from data.  On very large data sets, traditional analytics are pretty limited.  Big Data Solutions need to store, process, and iteratively run through models.  Examples of nontraditional analysis for large data:
* Recommendation Engine
* Neural Network to process images and videos
* Natural Language Processing
* Outlier detection to spot anomalies
* Clustering of customers for marketing purposes

Data scientists have a knowledge base in Math & Statistics, Data Crunching, Software Engineering.  More specifically, Statistical Models and algorithms, Machine Learning, Domain Knowledge, Data Cleaning, Python, R, Databases, and Big Data Systems.

### Hadoop
Hadoop is software used to reliably and scalably store and process big data.
* runs on commodity hardware
* Low cost per GB
* Ability to store Petabytes of data in a single cluster
* Open Source

Hadoop was developed at Yahoo and inspired by Googles GFS and MapReduce papers.

##### HDFS - Hadoop Distributed File System
HDFS is the data store inside the Hadoop Cluster
##### Yarn - Yet Another Resource Manager
Yarn interfaces with the applications and manages the CPU, Memory, and HDFS of the cluster.
##### Applications - MapReduce, Hive, Spark .....
Applications run on top of Yarn and submit jobs to Yarn.  Yarn then manages their resource usage and HDFS access.

Hadoop will automatically recover from a single node failure.  Hadoop allows for horizontal scaling of storage and the main cost benefit comes in when there are extremely large amounts of data. 

![](https://raw.githubusercontent.com/jboy42/learnDoc/master/Hadoop.PNG)
