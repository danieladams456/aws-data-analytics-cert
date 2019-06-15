# AWS Big Data Specialty Cert Study

***Disclaimer***: *this guide is the tail end of my studying so is not complete, mostly just focusing on trivia/gotchas.*

Anti-patterns taken from [AWS Big Data Whitepaper](https://d1.awsstatic.com/whitepapers/Big_Data_Analytics_Options_on_AWS.pdf).

## Data Collection

### Kinesis Data Streams
- **Service notes**
  - 200 ms latency (1 standard consumer), 70 ms with enhanced fan out HTTP2 push - both considered real time
- **Limits**
  - retention period default 24 hours, max 7 days
  - shard can ingest 1 MiB/s or 1000 messages/sec, max message size 1 MiB
  - consumer throughput is 2 MiB/s with max of a single API call 10,000 records or 10 MiB
- **Anti-patterns**
  - Small scale consistent throughput (less than 200 KB/sec)
  - Long term storage/analytics

### KPL

### KCL

### Kinesis Firehose
- **Service notes**
  - "near real time"
  -Destinations: S3, Redshift, Elasticsearch, Splunk
  - stores records up to 24 hours in case downstream system is unavailable
  - can store pre-transformation records, log transform and delivery errors
  - a Kinesis Data Stream can feed a Firehose stream
- **Limits**
  - max record size 1,000 KiB, throughput just soft limits
  - buffer hints:
    - S3: 1-128 MiB
    - ElasticSearch service: 1-100 MiB
    - Lambda processor: 1-3 MiB

### Kinesis Analytics
- **Service notes**
  - Analytics reads from and writes to Kinesis Data Streams using SQL
- **Limits**
