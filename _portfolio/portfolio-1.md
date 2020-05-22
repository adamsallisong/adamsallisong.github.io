---
title: "Hadoop & MapReduce Configuration & Tutorial"
excerpt: "Short description of portfolio item number 1<br/><img src='/images/500x300.png'>"
collection: portfolio
---

## What is Hadoop?
Hadoop is an open source platform that expedites the processing & analysis of large data (both
structured and unstructured) in a distributed computing environment. Hadoop is comprised of
two fundamental components:

* Distributed File System: This is the file structure of Hadoop that is set across several
computer nodes (datanodes, slave nodes) to help process large amounts of data. The hdfs can
be accessed by several different clients as if they were one local client. 
* MapReduce: This algorithm allows for queries to be processed in parallel as opposed to the
traditional serial fashion through distributed applications. The map function will take a
function and apply it to each subsequent value in the dataset. The reduce function then takes
the separate data nodes (master/slave relationship) that will process an individual query and 
process results in tandem. These key value pairs are then aggregated together and returned to
the name node

## What is Hive?
Apache Hive is a querying language (HQL) that works on top of the Hadoop platform to perform
data querying and analysis. Hive is a framework for MapReduce, automating the process. 

## Building a Hadoop Cluster with AWS & EMR 
Built using the following tutorial
https://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-gs.html

Amazon Elastic Map Reduce (EMR) on Amazon Web Services (AWS) allows for simplified
node clustering and services for Hadoop. EMR is a scalable managed framework that automates
the process of node provisioning, and both cluster and Hadoop configurations. It is all managed
through the AWS dashboards, and requires little technical knowledge to get started.
EMR consists of clusters:
* Master Node: In charge of running software and procedures to coordinate the data
analysis. This is the main node for interactions.
* Task & Core (Slave) Nodes: run tasks as directed by the master node, which can access
the Hadoop Datafile System (hdfs). The queries ran on these nodes are aggregated and
returned to one output directory on the hdfs, accessible by the master node. 

### S3 Sample Data & Buckets 
S3 is Amazon’s cloud object storage capability and allows users to store objects, data and meta
data. The first step is to insatiate an S3 account and create a bucket. A bucket is a unit of storage
in AWS and will serve as the location of the hdfs for this example. 
Within this bucket – create two folders for “logs” and “output”. The output folder is where the
results from the MapReduce function will be stored on the hdfs. 

### Create AWS Key Pair
AWS provides key pairs that allow for password-less secure connections to services and nodes
through Secure Shell (SSH) Protocol. If using the bash terminal to SSH into remote machines,
this key pair can be downloaded and used for password-less entry into node clusters. It is
important that you do not lose access to this key pair, or else you will lose access to the nodes as
well.
