## AWS general datalake architecture

The data lake consists of several parts. The first part is the ingestion layer. The ingestion layer consists of two subparts. A batch and streaming pipelines. 

Batch Pipeline: 
Designed to take incoming pdfs via sftp. A boto3 script setup on a windows scheduler. Would run hourly and take pdfs from the sftp server processing them through amazon texttract to OCR the files. The results are set to the S3 bronze bucket.

Streaming Pipeline:
Designed to take streaming data. This is to take immunization data as json from the api gateway and push to a kinesis stream. The stream would place in the S3 bronze bucket. The data would have a file format of YYYY/MM/DD/[time].json

Query and Indexing:
Starting from the bottom the AWS glue service is a metadata store of the data in the Storage layer. A glue crawler would periodically scan and index the data in the buckets. The lake formation service would provide data governance. The would prevent PII or Hippa data from being accessed by unauthorized users. 
Athena would take sql and query glue data catalog for pull the data from s3. 

Storage: 
Data at rest would reside here. The data would first go the bronze bucket (raw data) and move right to the Siver if processed and cleaned and then to the Gold bucket. 

Processing and Compute:
Since it was a large amount of data we used sagemaker juyper notebooks with pyspark to process, clean and transform the data. 

Presentation:
We used tableau to present dashboards. The dashboards would query Athena using a JDBC driver. The sql query was processed and return a result set of the data residing the Gold bucket. 


![Generalized data lake](https://raw.githubusercontent.com/udelblue/udelblue.github.io/main/images/datalake.png)