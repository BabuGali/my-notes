- that can ingest, **buffer** and process streaming data in **real-time**
##### Kinesis Data Firehose
- it deliver real time streaming data to destinations such as S3, Redshift, Amazon OpenSeach Service, splunk or any custom HTTP endpoint
- Kinesis Data Firehose provides the simplest approach for capturing, transforming, and loading data streams into AWS data stores.
- Firehouse **cannot directly write into a DynamoDB table**
- It is a easiest way to **load streaming data into data stores and analytics tools**
-  it can not store data
- It can **not be used to process and analyse the streaming data in custom applications**
- ![[Kenesis Data Firehose.png]]
- If **data transmission enabled**, you can optionally back up source data to another S3 bucket
- ![[Kenesis Data Firehose-2.png]]
##### Kinesis Data Analytics
- Kinesis Data Analytics cannot directly ingest data from the source as it ingests data either from Kinesis Data Streams or Kinesis data Firehose
-  use cases
	- **Create real-time analytics**
	- Use long-running, stateful computations to **trigger real-time actions like anomaly detection based** on historical data trends.
##### Kinesis Data Streams
- it is the real-time data streaming service in Amazon Kinesis with high scalability and durability. It can help in continuously capturing multiple gigabytes of data every second from multiple sources.
- **Data Streams** is a low latency streaming service in AWS Kinesis with the facility for ingesting at scale. On the other hand, Kinesis Firehose aims to serve as a data transfer service.
- it can integrate with Amazon Kinesis Data Firehose
- Kinesis data Streams **cannot directly write the output to S3**
- **lot of custom code is required to get the lambda function to process the incoming stream**
- **option to store data for one to 7 days**
- scaling - manual through shades
- Default retention period is 24 hours , up to 365 days