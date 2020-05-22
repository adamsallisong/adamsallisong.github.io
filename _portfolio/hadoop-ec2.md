---
title: "Hadoop & MapReduce with AWS EC2"
excerpt: "Configuration of Hadoop Cluster using EC2<br/><img src='/images/hadoopemr/emr.png'>"
collection: portfolio
---
## Hadoop
Hadoop is an open source platform that expedites the processing & analysis of large data (both structured and unstructured) in a distributed computing environment. For a more deatiled overview of Hadoop - see my portfolio piece [here.](https://adamsallisong.github.io/portfolio/hadoop-emr/). In this project we will spin up a Hadoop cluster using AWS Elastic Cloud Compute (EC2) which provides scalable cloud computing to developers.

### Create EC2 Instances
Following the steps within EC2, create 4 Ubuntu instances within the free tier of the AWS services. (*Note: as discovered later in the process, the free tier instances may not provide enough memory to run intended MapReduce problems)*

![Instances](/images/hadoopec2/Picture1.png)

On each of these nodes – change the Security groups to be “open” to allow for remote access from any IP address or port. It is important to have these security settings for both the INBOUND and the OUTBOUND traffic to these instances. If you don’t make these security groups open, then attempting to SSH into the instances will result in a timeout error. 
![Security](/images/hadoopec2/Picture2.png)

### Create Key Pair
As before, we will need to use a Key Pair for AWS. We have already created the allison-key.pem key and can be reused for this tutorial. (See previous portfolio Hadoop piece  [here.](https://adamsallisong.github.io/portfolio/hadoop-emr/))

## SSH Instance Configuration
Using the allison-key.pem we are able to SSH into the instances. To SSH into the nodes we need both this key and the public DNS, which can be found on the EC2 homepage. 
![SSH Instance](/images/hadoopec2/Picture2.png)

Since we will eventually want to SSH into all nodes we will need the DNS for each: 
`namenode => <name node dns>`
`datanode1 => <data node1 dns>`
`datanode2 => <data node2 dns>`
`datanode3 => <data node3 dns>`




