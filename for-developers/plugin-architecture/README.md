# Plugins

Starting from the 0.3.X release, Pinot supports a plug-and-play architecture. This means that starting from version 0.3.0, Pinot can be easily extended to support new tools, like streaming services and storage systems.

![](<../../.gitbook/assets/Pinot Dependency Graph.svg>)

Plugins are collected in folders, based on their purpose. The following types of plugins are supported.

#### Input Format

Input format is a set of plugins with the goal of reading data from files during data ingestion. It can be split into two additional types: record encoders (for batch jobs) and decoders (for ingestion). Currently supported record encoder formats are: avro, orc and parquet encoders, while for streaming: csv, json and thrift decoders.

{% content-ref url="../../basics/data-import/pinot-input-formats/" %}
[pinot-input-formats](../../basics/data-import/pinot-input-formats/)
{% endcontent-ref %}

#### File System

File System is a set of plugins devoted to storage purpose. Currently supported file systems are: adsl, gcs and hdfs.

{% content-ref url="../../basics/data-import/pinot-file-system/" %}
[pinot-file-system](../../basics/data-import/pinot-file-system/)
{% endcontent-ref %}

#### Stream Ingestion&#x20;

Stream Ingestion is a set of plugins targeted to ingest data from streams. Currently supported streaming services: kafka 0.9 and kafka 2.0.

{% content-ref url="../../basics/data-import/pinot-stream-ingestion/" %}
[pinot-stream-ingestion](../../basics/data-import/pinot-stream-ingestion/)
{% endcontent-ref %}

#### Batch Ingestion

Batch Ingestion is a set of plugins targeted to ingest data from batches. Currently supported ingestion systems are: spark, hadoop and standalone jobs.

{% content-ref url="../../basics/data-import/batch-ingestion/" %}
[batch-ingestion](../../basics/data-import/batch-ingestion/)
{% endcontent-ref %}

### Developing Plugins

Plugins can be developed with no restriction. There are some standards that have to be followed, though. The plugin have to implement the interfaces from the link [https://github.com/apache/pinot/tree/master/pinot-spi/src/main/java/org/apache/pinot/spi](https://github.com/apache/pinot/tree/master/pinot-spi/src/main/java/org/apache/pinot/spi)
