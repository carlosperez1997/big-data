# Big Data Architecture

## [Batch-based](https://hazelcast.com/glossary/data-pipeline/)

![](https://hazelcast.com/wp-content/uploads/2019/11/24_DataPipleline-1.png)

One common example is a batch-based data pipeline. In that example, you may have an application such as a point-of-sale system that generates a large number of data points that you need to push to a data warehouse and an analytics database. 

##  [Stream processing](https://hazelcast.com/glossary/data-pipeline/)

![](https://hazelcast.com/wp-content/uploads/2019/11/18_StreamingDataPipeline-800x377.png)

Another example is a streaming data pipeline. In a streaming data pipeline, data from the point of sales system would be processed as it is generated. The stream processing engine could feed outputs from the pipeline to data stores, marketing applications, and CRMs, among other applications, as well as back to the point of sale system itself.

Stream processing is the practice of taking action on a series of data at the time the data is created. Historically, data practitioners used “real-time processing” to talk generally about data that was processed as frequently as necessary for a particular use case. But with the advent and adoption of stream processing technologies and frameworks, coupled with decreasing prices for RAM, “stream processing” is used in a more specific manner.

### Stream processing vs batch processing

Historically, data was typically processed in batches based on a schedule or some predefined threshold (e.g. every night at 1 am, every hundred rows, or every time the volume reaches two megabytes). But the pace of data has accelerated and volumes have ballooned, and there are many use cases for which batch processing simply doesn’t cut it.

Stream processing has become a must-have for modern applications. Enterprises have turned to technologies that respond to data at the time at which it is created for a variety of use cases and applications, examples of which we’ll cover below.

Stream processing allows applications to respond to new data events at the moment they occur. Rather than grouping data and collecting it at some predetermined interval, a la batch processing, stream processing applications collect and process data immediately as they are generated.


## [Lambda architecture](https://hazelcast.com/glossary/lambda-architecture/)

A third example of a data pipeline is the Lambda Architecture, which combines batch and streaming pipelines into one architecture.

The Lambda Architecture is a deployment model for data processing that organizations use to combine a traditional batch pipeline with a fast real-time stream pipeline for data access.

In the diagram above, you can see the main components of the Lambda Architecture:

- Data Sources. Data can be obtained from a variety of sources. This component is oftentimes a streaming source like Apache Kafka, which is not the original data source per se, but is an intermediary store that can hold data in order to serve both the batch layer and the speed layer of the Lambda Architecture. The data is delivered simultaneously to both the batch layer and the speed layer to enable a parallel indexing effort.

- Batch Layer. This component saves all data coming into the system as batch views in preparation for indexing. The input data is saved in a model that looks like a series of changes/updates that were made to a system of record. Oftentimes this is simply a file in the comma-separated values (CSV) format. The data is treated as immutable and append-only to ensure a trusted historical record of all incoming data. A technology like Apache Hadoop is often used as a system for ingesting the data as well as storing the data in a cost-effective way.

- Serving Layer. This layer incrementally indexes the latest batch views to make it queryable by end users. The key requirement in the serving layer is that the processing is done in an extremely parallelized way to minimize the time to index the data set. While an indexing job is run, newly arriving data will be queued up for indexing in the next indexing job.

- Speed Layer. **This layer complements the serving layer by indexing the most recently added data not yet fully indexed by the serving layer. This includes the data that the serving layer is currently indexing as well as new data that arrived after the current indexing job started.** Since there is an expected lag between the time the latest data was added to the system and the time the latest data is available for querying (due to the time it takes to perform the batch indexing work), it is up to the speed layer to index the latest data to narrow this gap.

This layer typically leverages stream processing software to index the incoming data in near real-time to minimize the latency of getting the data available for querying. When the Lambda Architecture was first introduced, Apache Storm was a leading stream processing engine used in deployments, but other technologies have since gained more popularity as candidates for this component (like Hazelcast Jet, Apache Flink, and Apache Spark Streaming).

- Query. **This component is responsible for submitting end user queries to both the serving layer and the speed layer and consolidating the results.** This gives end users a complete query on all data, including the most recently added data, to provide a near real-time analytics system.

What are the benefits of Lambda Architecture?

- Latency. Raw data is indexed in the serving layer so that end users can query and analyze all historical data. Since batch indexing takes a bit of time, there tends to be a relatively large time window of data that is temporarily not available to end users for analysis. The speed layer uses stream processing technologies to immediately index recent data that is currently not queryable in the batch/serving layers, thus narrowing the time window of unanalyzable data. 

- Data consistency. One key idea behind the Lambda Architecture is that it eliminates the risk of data inconsistency that is often seen in distributed systems. In the Lambda Architecture, since the data is processed sequentially (and not in parallel with overlap, which may be the case for operations on a distributed database), the indexing process can ensure the data reflects the latest state in both the batch and speed layers.

- Scalability. The Lambda Architecture does not specify the exact technologies to use, but is based on distributed, scale-out technologies that can be expanded by simply adding more nodes. 

- Human fault tolerance. Since raw data is saved for indexing, it acts as a system of record for your analyzable data, and all indexes can be recreated from this data set. This means that if there are any bugs in the indexing code or any omissions, the code can be updated and then rerun to reindex all data.



## [Kappa architecture](https://hazelcast.com/glossary/kappa-architecture/)

![](https://hazelcast.com/wp-content/uploads/2020/01/30_KappaArchitecture.png)

The Kappa Architecture is a software architecture used for processing streaming data. The main premise behind the Kappa Architecture is that you can perform both real-time and batch processing, especially for analytics, with a single technology stack. It is based on a streaming architecture in which an incoming series of data is first stored in a messaging engine like Apache Kafka. From there, a stream processing engine will read the data and transform it into an analyzable format, and then store it into an analytics database for end users to query.

The Kappa Architecture supports (near) real-time analytics when the data is read and transformed immediately after it is inserted into the messaging engine. 

The main difference with the Kappa Architecture is that all data is treated as if it were a stream, so the stream processing engine acts as the sole data transformation engine.

A streaming architecture is a defined set of technologies that work together to handle stream processing, which is the practice of taking action on a series of data at the time the data is created.

Apache Kafka acts as the store for the streaming data, and then multiple stream processors can act on the data stored in Kafka to produce multiple outputs. Some streaming architectures include workflows for both stream processing and batch processing, which either entails other technologies to handle large-scale batch processing, or using Kafka as the central store as specified in the Kappa Architecture.

One major benefit of the Kappa Architecture over the Lambda Architecture is that it enables you to build your streaming and batch processing system on a single technology. This means you can build a stream processing application to handle real-time data, and if you need to modify your output, you update your code and then run it again over the data in the messaging engine in a batch manner.

## [Event-Driven Architecture](https://hazelcast.com/glossary/event-driven-architecture/)

![](https://hazelcast.com/wp-content/uploads/2020/02/20_EventDrivenArchitecture.png)

An Event-Driven Architecture for data and applications is a modern design approach centered around data that describes “events” (i.e., something that just happened). Examples of events include the taking of a measurement, the pressing of a button, or the swiping of a credit card.

Event-driven architectures create, detect, consume, and react to events. Common concepts in event-driven architectures include publishers, subscribers, sources, and sinks. 

With a scalable event-driven architecture, you can both create and respond to a large number of events in real time. An event-driven architecture is particularly well-suited for loosely coupled software, such as microservices. Event-driven architectures work well with unpredictable, non-linear events, so they are very versatile.

With an event-driven architecture, applications can respond to data as it is generated. The event-driven approach has become extremely popular in recent years thanks to both the explosion in data sources that generate events (IoT sensors, for example) and the development and adoption of technologies that process event streams, such as Hazelcast Jet and Apache Kafka®.

Event-driven architectures are particularly popular for microservices-based software applications. Microservices are built to perform very specific tasks, and these tasks are often based on the occurrence of some event. 

## AWS

![](https://d2908q01vomqb2.cloudfront.net/b6692ea5df920cad691c20319a6fffd7a4a766b8/2017/09/09/real-time-batch-lambda_1.gif)

The AWS services involved in this solution include:

AWS Glue is a service designed to work and orchestrate jobs as an ETL (Extract Transform and Load) tool which has the purpose to synthesize data in a human friendly format like OLAP to analysis, most used to build databases for business intelligence purpose.

AWS Kinesis is designed to stream a huge volume of non-normalized data and execute small tasks before store to a data lake or any other kind of non-normalized data storage like dynamodb, mongodb, redis, etc. You can also use with the purpose of real time analysis forwarding transformed series data to dashboards like Kibana, Graphana, etc.

AWS Kinesis is a fully managed service that can store and process terabytes of streaming data. With Amazon Kinesis, developers can continuously capture data from hundreds of thousands of sources, including website clickstreams, financial transaction data, social media feeds, server logs, and more.