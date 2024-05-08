# Hadoop
# Data Aggregation using Apache Hadoop

- Author: Teddy Thomas
- GitHub account: littishya21
- UMD email: tedthom1@umd.edu
- Personal email: teddylittishyathomas@gmail.com

## Project Methodology

                     +-------------------------------------+
                     |             Docker Host             |
                     +-------------------------------------+
                              |                |
                    +---------+--------------------------+
                    |                                  |
       +-----------------------------+    +-----------------------------+
       |          Docker           |    |          Docker           |
       |     Container: Hadoop    |    |     Container: Python    |
       +-----------------------------+    +-----------------------------+
                    |                                  |
       +----------------------------------+   +----------------------------------+
       |               Hadoop             |   |               Python             |
       |      - HDFS                      |   |      - Data Processing          |
       |      - MapReduce                 |   |      - MapReduce Scripts        |
       |      - YARN                      |   |      - Data Analysis            |
       +----------------------------------+   +----------------------------------+
                    |                                  |
      +------------------------------------------------------------+
      |                        Data Storage                       |
      |                 - Train.csv (BigMart Sales Data)          |
      +------------------------------------------------------------+

## Description

The project, "Data Aggregation with Apache Hadoop using Docker and Python," aims to demonstrate a robust solution for processing and analyzing large-scale datasets efficiently. Leveraging the power of Apache Hadoop, Docker, and Python, we provide a scalable and flexible platform for aggregating and deriving insights from complex data.

The dataset chosen for this project is the "BigMart Sales Data" available on Kaggle, a comprehensive collection of sales data from various BigMart outlets. This dataset offers a real-world scenario, encompassing multiple variables such as product attributes, outlet details, and sales figures, making it ideal for showcasing the capabilities of our solution.

To begin, I utilized Docker to create a containerized environment, ensuring seamless deployment and portability across different systems. Within this Docker container, deployed Apache Hadoop, an open-source framework renowned for its distributed processing capabilities. Apache Hadoop enables parallel processing of data across multiple nodes, facilitating faster analysis and computation of large datasets.

Python serves as the primary programming language for orchestrating data aggregation tasks within the Apache Hadoop ecosystem. Leveraging popular Python libraries such as Hadoop Streaming API, Pandas, and NumPy, we implement data processing pipelines to extract, transform, and aggregate information from the BigMart Sales Data.

The project workflow involves the following key steps:

Data Ingestion: Ingested the BigMart Sales Data into the Hadoop Distributed File System (HDFS), a distributed storage system optimized for handling large volumes of data.
Data Preprocessing: Using Python scripts, preprocessed the raw data to handle missing values, standardize formats, and perform any necessary transformations to prepare it for analysis.
MapReduce Aggregation: Leveraging the MapReduce paradigm, we distribute data processing tasks across multiple nodes in the Hadoop cluster. Map tasks extract relevant information from the dataset, while Reduce tasks aggregate and summarize the extracted data.
Analysis and Insights: After the aggregation process ,analyzed the aggregated data using Python's data analysis tools. Derived valuable insights to understand sales trends, product performance, and other relevant metrics.
Output Generation: Finally, generated output files summarizing the findings of our analysis, providing actionable insights for stakeholders.

## Technologies

### Hadoop: 

--> Hadoop is an open-source framework designed to handle big data processing and storage in distributed computing environments. It provides a scalable, fault-tolerant ecosystem for storing and processing vast amounts of data across clusters of commodity hardware.

--> At its core, Hadoop consists of two primary components: the Hadoop Distributed File System (HDFS) and the MapReduce programming model. HDFS is a distributed file system designed to store large datasets reliably across multiple machines. It divides files into blocks and replicates them across different nodes in the cluster to ensure fault tolerance and data availability.

--> The MapReduce programming model is a parallel processing paradigm for distributed data processing. It divides computational tasks into two phases: the Map phase and the Reduce phase. During the Map phase, input data is processed in parallel across multiple nodes in the cluster, generating intermediate key-value pairs. These intermediate results are then aggregated and processed further during the Reduce phase to produce the final output.

-->Hadoop also includes a variety of other components and modules that extend its functionality, such as:

  - YARN (Yet Another Resource Negotiator): YARN is a resource management layer that enables efficient resource allocation and job scheduling in Hadoop clusters. It allows multiple processing frameworks, such as MapReduce, Apache Spark, and Apache Flink, to run concurrently on the same cluster.
  - Hadoop Common: Hadoop Common provides the essential libraries and utilities required by other Hadoop modules. It includes tools for managing Hadoop clusters, interacting with HDFS, and performing administrative tasks.
  - Hadoop Ecosystem Projects: The Hadoop ecosystem consists of a vast array of projects and tools that integrate with Hadoop to extend its capabilities. These include Apache Hive for data warehousing, Apache Pig for data processing, Apache HBase for real-time NoSQL databases, and Apache Spark for in-memory data processing, among others.
## Docker System Overview

-> Docker is a platform that enables developers to package applications and their dependencies into containers, providing an isolated environment for seamless deployment across different systems.The Docker system is designed to set up a Hadoop environment within Docker containers to run MapReduce jobs in a distributed manner. 

Description of Files:

1. core-site.xml: Configuration file for Hadoop's core services, specifying parameters like the default file system and Hadoop's internal directories.
2. Dockerfile: A text file containing instructions for building a Docker image, including the base image, dependencies, and commands to run when the container starts.
3. execut.sh: Shell script used for executing tasks within the Docker container, often containing commands to start Hadoop services or run MapReduce jobs.
4. framework.py: Python script implementing the data processing framework, defining tasks such as data aggregation, analysis, or visualization.
5. hdfs-site.xml: Configuration file for Hadoop Distributed File System (HDFS), specifying parameters related to data replication, block size, and other storage settings.
6. mapper.py: Python script defining the mapping function for a MapReduce job, responsible for processing input data and emitting intermediate key-value pairs.
7. mapred-site.xml: Configuration file for MapReduce job execution, specifying parameters like the number of map and reduce tasks, memory allocation, and job scheduling.
8. reducer.py: Python script defining the reducing function for a MapReduce job, responsible for aggregating and processing intermediate key-value pairs to produce the final output.
9. Train.csv: The dataset file containing BigMart Sales Data, which serves as input for data processing tasks.
10. yarn-site.xml: Configuration file for Yet Another Resource Negotiator (YARN), specifying parameters for resource management, job scheduling, and application execution in Hadoop clusters.

#### References for hadoop technology deescription
    [1] https://www.oreilly.com/library/view/hadoop-the-definitive/9780596521974/

Below, I'll discuss the decisions made, the containers involved, and how they communicate.

#### --> Decisions Made

[1] Base Image
The system uses Ubuntu as the base image, upon which Java and Hadoop are installed. Ubuntu is chosen for its widespread use and ease of customization.
[2] Java and Hadoop Installation
OpenJDK 8 and Hadoop 3.3.1 are installed within the Docker image. These versions are selected based on compatibility and stability considerations.
[3] Configuration
Environment variables are set to configure Hadoop paths and other settings. Configuration files such as core-site.xml, hdfs-site.xml, mapred-site.xml, and yarn-site.xml are copied into the container to customize Hadoop's behavior.
[4] SSH Configuration
SSH is configured within the container to allow passwordless SSH connections, which are necessary for Hadoop's internal communication between nodes.
[5] Mapper and Reducer Scripts
Python scripts for Mapper and Reducer tasks, along with sample data (Train.csv), are copied into the container. These scripts are used for processing data in MapReduce jobs.
[6] Dockerfile Structure
The Dockerfile is structured to ensure efficient layer caching and readability. Each step is documented to explain its purpose and rationale.

#### --> Containers Involved:

-->The main Docker container hosts the Hadoop environment.
It includes HDFS, YARN, MapReduce, and other Hadoop components necessary for distributed data processing.

#### --> Communication Between Containers:

[1] Inter-Container Communication

Containers communicate internally through Hadoop's native communication protocols. HDFS handles storage and retrieval of data, while YARN manages resource allocation and job scheduling. MapReduce jobs are submitted to YARN, which distributes tasks to individual containers running Mapper and Reducer tasks.

[2] SSH

SSH is configured within the container to allow communication between nodes in the Hadoop cluster. This enables tasks to be executed on different nodes and for nodes to exchange data during MapReduce job execution.
## Running the Docker system by starting the container 

To run the Docker system  follow these steps:

[1] Build Docker Image
First, build the Docker image using the provided Dockerfile. Navigate to the directory containing the Dockerfile and run the following command:

 > docker build -t hadoop-cluster .

[2] Start Docker Container

Once the image is built, start a Docker container using the following command:

 > docker run -it --name hadoop-container hadoop-cluster

[3] Verify Hadoop Installation
Once inside the container, verify that Hadoop is installed and configured correctly by running Hadoop commands.

> cd /home/hadoop/data
> pwd
> hadoop fs -ls

[4] Prepare Input Data
If needed, upload input data to HDFS using the following commands:

> hadoop fs -mkdir -p input
> hdfs dfs -put Train.csv input

[5] Run MapReduce Job
After uploading input data, execute a MapReduce job using the provided scripts. 

> hadoop jar /usr/local/hadoop/share/hadoop/tools/lib/hadoop-streaming-3.3.1.jar -D mapreduce.job.reduces=5 -file mapper.py -mapper "python3 mapper.py" -file reducer.py -reducer "python3 reducer.py" -input input -output output

[6] Retrieve Output
Once the MapReduce job completes, retrieve the output from HDFS and examine the results. 

> hadoop fs -copyToLocal output .

[7] Inspect Output
Finally, inspect the output files to view the results of the MapReduce job. 

> cd output
> ls
> cat part-00001

[8] OUTPUT OBTAINED

> Breads  2204.132226294819

> Dairy   2232.5425970674455

> Frozen Foods    2132.8677436915887

> Health and Hygiene      2010.000265000001

> Soft Drinks     2006.5117348314602

The output provided represents the data aggregated value calculated for each category based on the input data processed by the MapReduce job. Each line consists of a category name followed by its corresponding average value. 

==> Category Name

The category names listed (Breads, Dairy, Frozen Foods, Health and Hygiene, Soft Drinks) represent different product categories.

==> Average Value

The average value associated with each category represents some metric or measure related to the products in that category. However, it represent various metrics such as sales volume, revenue, quantity sold, or any other numerical attribute associated with the products in each category.

==> Comparison

By comparing the average values across different categories, we can identify patterns or trends in the data.That is, if Dairy has a significantly higher average value compared to Soft Drinks, it could indicate that dairy products are more popular or more profitable than soft drinks.

==> Insights

The average values provide insights into the distribution or characteristics of products within each category. For instance, a higher average value might suggest that products in that category are more expensive or have higher sales volumes on average.

==> Decision Making

These average values can inform decision-making processes for businesses. For example, based on the average values, businesses can adjust pricing strategies, allocate resources to different product categories, or identify areas for improvement or investment.



## System Architecture

# Project Documentation




## 6. Conclusion

