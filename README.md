# Hadoop
# Data Aggregation using Apache Hadoop

## Author info

- Author: Teddy Thomas
- GitHub account: littishya21
- UMD email: tedthom1@umd.edu
- Personal email: teddylittishyathomas@gmail.com

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
### Docker 

-> Docker is a platform that enables developers to package applications and their dependencies into containers, providing an isolated environment for seamless deployment across different systems.

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

## Docker implementation


## 5. Project Diagram

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


## 6. Conclusion

