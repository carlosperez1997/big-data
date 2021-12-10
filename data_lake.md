# Data lake

A data lake is a storage repository that contains a large amount of raw data and is kept there until needed. Unlike a hierarchical data warehouse that stores data in files or folders, a data lake uses a flat architecture to store data.

A data lake is capable of providing data to the organization for a great variety of different analytical processes:

- Data discovery and exploration
- Simple ad hoc analysis
- Complex analysis for decision making
- Reports
- Real time analysis

Each element in a data lake is assigned a unique identifier and tagged with a set of extended metadata tags. When a business issue arises that needs to be resolved, we may ask the data lake for data that is related to that issue. Once obtained we can analyze that smaller data set to help obtain an answer.

The data lake is often associated with Hadoop-oriented object storage. In this scenario, an organization's data is first uploaded to the Hadoop platform, and then data mining and analysis tools are applied to the data that resides on the Hadoop cluster nodes.

Data lake is a way to describe any large data set in which the schema and data requirements are not defined until the data is queried.

## What are the benefits of a data lake?

The main benefit of a data lake is the centralization of disparate content sources. Once gathered (from your "information silos"), these sources can be combined and processed using big data, searches, and analytics that would have been impossible otherwise. Disparate content sources often contain sensitive information that will require the implementation of appropriate security measures in the data lake.

Security measures in the data lake can be assigned such that access to certain information is granted to users of the data lake who do not have access to the original content source. These users have a right to the information, but cannot access it at its source for some reason.

Once the content is in the data lake, it can be normalized and enriched. This can include metadata extraction, format conversion, augmentation, entity extraction, crosslinking, aggregation, de-normalization, or indexing.

Data is prepared "as needed," reducing preparation costs over initial processing (as would be required by data warehouses. A big data framework allows this processing to be scaled to include the largest possible data sets.

Users, from different departments, potentially scattered around the world, can have flexible access to a data lake and its content from anywhere. This increases content reuse and helps your organization more easily collect the data needed to drive business decisions.

Information is power, and a data lake puts the information of the entire company in the hands of many more employees to make the organization as a whole smarter, more agile and more innovative.

## Differences between data warehouse and data lake

1. A Data Lake holds all data

During data warehouse development, a considerable amount of time is spent analyzing data sources, understanding business processes, and profiling the data. The result is a highly structured data model designed for reporting. A large part of this process includes making decisions about what data to store and not store. Generally, if the data is not used to answer specific questions or in a defined report, it can be excluded from the warehouse. This is generally done to simplify the data model and also to conserve the expensive disk storage space that is used to make the data warehouse.

In contrast, **the data lake holds all the data.** Not just data that is currently in use, but data that can be used and even data that is never going to be used just because it might one day be used. The data is also kept all the time so that we can go back in time to any point to do the analysis.

This approach is made possible because the hardware for a data lake is often very different from that used for a data warehouse. Expanding a data lake to terabytes and petabytes can be done quite inexpensively.

2. A Data Lake supports all types of data

Data warehouses are generally made up of data pulled from transactional systems along with quantitative metrics and the attributes that describe them. **Non-traditional data sources such as web server logs, sensor data, social media activity, text, and images are largely ignored.** New uses continue to be found for these types of data, but consuming and storing them can be expensive and difficult.

In the data lake, we store all data regardless of source and structure. We keep them in their raw form and only transform them when we are ready to use them. This approach is known as "Schema on Read" as opposed to "Schema on Write" which is the approach used in the data warehouse.

3. One Data Lakes supports all users

In most organizations, **80% or more of users are "operational." They want to get your reports, see your KPIs, or select the same dataset from a spreadsheet every day. The data warehouse is often ideal for these users because it is well structured, easy to use and understand, and designed to answer their questions.**

The next 10% or so do more analysis on that data. They use the data warehouse as a source, but they often go back to the source systems to obtain data that is not included in the warehouse and sometimes bring data from outside the organization. The data warehouse is their source of access to data, but they often go beyond its limits

Finally, the remaining percent of users do a deep analysis. They can create entirely new data sources based on research. They mix up many different types of data and come up with new questions that need to be answered. These users can use the data warehouse, but are often ignorant of it, as they are typically asked to go beyond their capabilities. These users include data scientists and can use advanced analytical tools and capabilities such as statistical analysis and predictive modeling.

The data lake approach supports all of these users equally. Data scientists can go to the data lake and work with the large and varied set of data they need, while other users make use of more structured views of the data provided for their use.

4. Data Lakes Easily Adapt to Changes

One of the biggest complaints about data warehouses is how long it takes to change them. Considerable time is spent in advance during the development of the warehouse structure. A good warehouse design can adapt to change, but due to the complexity of the data loading process and the work done to facilitate analysis and reporting, these changes will necessarily consume some developer resources and take some time.

**Many business questions can't wait for the data warehouse team to adapt its system to answer them. The growing need for faster responses is what has given rise to the concept of self-service business intelligence.**

In the data lake, on the other hand, since all data is stored raw and always accessible to someone who needs to use it, users have the power to go beyond the warehouse structure to explore data in new ways and respond to your questions at your own pace.

If the result of an exploration is shown to be useful and there is a desire to repeat it, then a more formal scheme can be applied and automation and reuse can be developed to help extend the results to a wider audience. If the output is determined to be useless, it can be discarded and no changes have been made to the data structures or development resources consumed.

5. Data Lakes provide faster insight

Because data lakes contain all data and data types, allowing users to access data before it has been transformed, cleansed, and structured, **it enables users to reach their results faster than the traditional method.** of data warehouse.

However, this early access to data comes at a price. The work typically performed by the data warehouse development team cannot be done for some or all of the data sources required to perform an analysis. This allows users to explore and use the data as they see fit, but the first tier of business users that I described above may not want to do that job. They still want your reports and KPI's.

At data lakes, these operational reporting consumers will make use of more structured views of the data in the data lake that resemble what they have always had before in the data warehouse. **The difference is that these views exist primarily as metadata that sits on top of the data in the lake rather than physically rigid tables that require a developer to change them.**

## Row vs. Columnar Databases

You might have never heard of the terms row and columnar associated with databases, but you have most certainly come across them before. Row-oriented databases are your typical transactional ones, able to handle a large number of transactions, whereas column-oriented databases usually have fewer transactions with a higher volume of data. 

By now, you probably have already guessed which type of database is more suitable for each processing system. **Row-oriented databases are commonly used in OLTP systems, whereas columnar ones are more suitable for OLAP.** Some examples include:

| Row-oriented    | Columnar |
| ----------- | ----------- |
| MySQL     |   Amazon Redshift    |
| PosgreSQL   |  MariaDB      |
| Oracle   |       Click House      |

### But What Makes Them Different Internally?
**The key difference between both data stores is the way they are physically stored on disk.** Common HDDs are organized in blocks and rely on expensive head seek operations. Thus, sequential reads and writes tend to be much faster than random accesses.

**Row-oriented databases store the whole row in the same block, if possible. Columnar databases store columns in subsequent blocks.**

Amazon Redshift provides a simple and concise explanation highlighting the differences between both databases. The figure shown below consists of row-wise database storage, where each row is stored in a sequential disk block. Picking the ideal block size is important to grant optimal performance, since having a block size that’s too small or too big results in inefficient use of disk space.

![](https://dz2cdn1.dzone.com/storage/temp/13215075-jscrambler-blog-redshift-1.png)

The figure below portrays columnar database storage, where each disk block stores values of a single column for multiple rows. In this example, using columnar storage requires one-third of I/O disk operations to extract the columns’ values, compared to a row-wise database.


### Performance Example
Let’s look at a simple example to fully understand the differences between both databases.

Consider a database storing a total of 100GB of data, with 100 million rows and 100 columns (1GB per column). For simplification purposes, consider that the database administrator is a rookie and hasn’t implemented any indexes, partitioning, or any other optimization process on the database. With this in mind, for the analytical query:

What is the average age of males?

We would have these possibilities:

- **Row wise DB** -> Has to read all the data in the database — 100GB to read.
- **Columnar DB** -> Has to read only the columns age and gender — 2GB to read.

This is obviously an extreme example — hardly any database will completely lack indexes or other optimization processes, but the goal is to give you an overview of columnar databases’ true potential for analytical purposes.

### Row and Columnar Databases Wrap-up
Now that you have an overview of row-oriented and columnar databases and the main differences between them, highlighting their advantages and disadvantages shouldn’t be too hard:

| Row-oriented DB: for OLTP   | Columnar DB: for OLAP |
| ----------- | ----------- |
| Performs fast multiple read, write, update, delete operations | Performs slowly if required to perform multiple read, write, update, delete operations  |
| Bulk operations (read and write) aren’t particularly fast |  Performs fast bulk operations (mostly read and write)    |
| ACID compliance   |  No ACID compliance |
| Typically inefficient data compression  |  Improved data compression — columns are individually compressed and each one is of the same type  |
| High storage size (indexes, etc.)   |   Low storage size  |
| Typically require multiple indexes, depending on queries  |  Relies on a single index per column (self-indexing)  |
| Easy to add a single row (1 insert operation)  |  Hard to add a single row (multi-column insert operation)  |
| Hard to add a single column (multi-row insert operation)  | Easy to add a single column (1 insert operation)  |



	
	
	
	
	
	
	
	
	

https://www.powerdata.es/data-lake

https://www.linkedin.com/pulse/columnar-vs-row-oriented-databases-basics-2-min-read-faraz-khan/

https://medium.com/bluecore-engineering/deciding-between-row-and-columnar-stores-why-we-chose-both-3a675dab4087
