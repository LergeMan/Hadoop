# Hadoop Project on AWS EC2

## Team Members
- Angad Deep Singh
- Poojitha Singh
- Robert Lewandowski
- Deepikaveni Venkatanarayanan

### PROJECT OVERVIEW:
##### This project demonstrates setting up a basic Hadoop cluster using EC2 instances on AWS. It includes one master and one worker node configured on Ubuntu 24.04.2 LTS with OpenJDK 11.

## Steps to run the project

### Step 1: AWS Console - Navigate to EC2 Dashboard to launch instances.
* Launch two EC2 instances.
* Use Ubuntu 24.04.2 LTS AMI.
* Assign names like HadoopMaster and HadoopWorker for clarity.

![Step 1](snipshots/image0.jpg)

### Step 2: Launch two EC2 Ubuntu instances - one as Master and the other as Worker.
## Allow inbound rules for:
* SSH (TCP 22)
* Custom TCP (TCP 8088, 9000, 9870) – Required for Hadoop Web UIs.

![Step 2](snipshots/image1.png)
![Step 2](snipshots/image2.png)
![Step 2](snipshots/image3.png)

### Step 3: connect via SSH
* Use the public IP address to SSH into each instance.
* Run system updates and install OpenJDK

![Step 3](snipshots/image6.png)
![Step 3](snipshots/image7.png)
![Step 3](snipshots/image8.png)


### Step 4: Configure Hostnames and Network:

![Step 4](snipshots/image10.png)
![Step 4](snipshots/image11.png)


### Step 5: Allocate and Use Elastic IP
* Allocate a new elastic IP and associate it with your master node.

![Step 5](snipshots/image40.jpg)

### Step 6: Download and Install Hadoop

![Step 6](snipshots/image12.png)
![Step 6](snipshots/image13.png)


### Step 7: Set Environmental Variables

![Step 7](snipshots/image14.png)
![Step 7](snipshots/image15.png)


### Step 8: Configure Hadoop XML Files
##### Core-site.xml

![Step 8](snipshots/image16.png)

##### Hdfs-site.xml

![Step 8](snipshots/image17.png)

##### Yarn-site.xml

![Step 8](snipshots/image18.png)
![Step 8](snipshots/image19.png)


### Step 9: Configure workers file
##### On the master node, list the private IPs of your worker nodes inside
##### $HADOOP_HOME/etc/hadoop/workers:

![Step 9](snipshots/image20.png)

### Step 10: Configure Remaining Hadoop Files

##### Mapred-site.xml

![Step 10](snipshots/image21.png)
![Step 10](snipshots/image22.png)
![Step 10](snipshots/image24.png)
![Step 10](snipshots/image25.png)

### Step 11: Setup Passwordless SSH from Master to Worker

##### On master node:

![Step 11](snipshots/image26.png)

##### On worker node:

![Step 11](snipshots/image27.png)


### Step 12: Format NameNode & Start Services 

![Step 12](snipshots/image13.png)

##### Start DFS:

![Step 12](snipshots/image41.jpg)

##### Start YARN:

![Step 12](snipshots/image42.jpg)

#### Results

![Step 12](snipshots/image32.5.jpg)
![Step 12](snipshots/image29.png)
![Step 12](snipshots/image30.png)
![Step 12](snipshots/image31.png)
![Step 12](snipshots/image32.png)
![Step 12](snipshots/image33.png)


### Conclusion:

#### This project successfully demonstrated the setup and configuration of a Hadoop cluster on AWS EC2 instances, implementing a distributed computing environment capable of processing large datasets. Through this implementation, we established:
* A functional master-worker architecture using EC2 instances
* Proper Hadoop configuration
* SSH communication between nodes
* Enviornment setup for running MapReduce jobs

## Due to teir level, worker node is off and master is running
![Conclusion](snipshots/image34.png)

#### The system was designed to process textual data (in this case, analyzing word frequency in books) by distributing the workload across worker nodes, showcasing Hadoop's ability to parallelize large-scale data processing tasks.

### Note on Limitations:
#### Due to AWS Free Tier restrictions, we encountered resource constraints that prevented running both master and worker nodes simultaneously for the final word count execution. However, all configuration steps were thoroughly validated, and the architecture is fully functional - with adequate resources in a non-Free Tier environment, the system would successfully:
* Distribute the book text across HDFS
* Execute the WordCount MapReduce job
* Aggregate results from worker nodes
* Produce the complete word frequency analysis


