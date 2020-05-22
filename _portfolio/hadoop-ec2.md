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
As before, we will need to use a Key Pair for AWS. We have already created the a-key.pem key and can be reused for this tutorial. (See previous portfolio Hadoop piece  [here.](https://adamsallisong.github.io/portfolio/hadoop-emr/))

## SSH Instance Configuration
Using the a-key.pem we are able to SSH into the instances. To SSH into the nodes we need both this key and the public DNS, which can be found on the EC2 homepage. 
![SSH Instance](/images/hadoopec2/Picture2.png)

Since we will eventually want to SSH into all nodes we will need the DNS for each: 
```namenode => <name node dns>
datanode1 => <data node1 dns>
datanode2 => <data node2 dns>
datanode3 => <data node3 dns>
```

Before we SSH, we want to change the permissions of the Key to ensure that it is secure so we will modify the permissions (chmod) to ensure that the owner of the file can read and write. As recommended by the tutorial, we will run this command on the a-key.pem

`local$ sudo chmod 600 ~/.ssh/a-key.pem`

Now we are able to SSH into the notes without trouble. This can be done by passing both the key value pair and the user@publicDNS address. The user for our instances is “Ubuntu” 

`local$ ssh -i ~/.ssh/a-keey.pem ubuntu@<dns name node>`

Since we will be SSH’ing into these instances quite a bit, it will be easier to set up a config file within ~/.ssh to provide an alias for each instance. This will allow for the command to change from the above address to: ssh namenode 
To make this change update the config file to include the public DNS for each instance. The namenode will be the master and each subsequent datanode (1-3) will act as the slave nodes. 

```
Host namenode
  HostName ec2-18-188-21-63.us-east-2.compute.amazonaws.com
  User ubuntu
  IdentityFile ~/.ssh/allison-key.pem
Host datanode1
  HostName ec2-18-218-8-239.us-east-2.compute.amazonaws.com
  User ubuntu
  IdentityFile ~/.ssh/allison-key.pem
Host datanode2
  HostName ec2-18-220-127-51.us-east-2.compute.amazonaws.com
  User ubuntu
  IdentityFile ~/.ssh/allison-key.pem
Host datanode3
  HostName ec2-18-220-88-132.us-east-2.compute.amazonaws.com
  User ubuntu
```




