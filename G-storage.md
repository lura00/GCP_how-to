# Cloud Storage
  - Devided into buckets

## Cloud Storage: Storage classes and data transfer
  - There are 4 different types of storage classes:
      1. Standard Storage - Hot Data.
      2. Nearline Storage - Once per Month.
      3. Coldline Storage - Once per 90 days.
      4. Archive Storage  - Once a year. This is the cheapest storage, used for data archive, data backups.

Only pay for what you use.

## Transfer Data
  - Online transfer.
  - Storage Transfer Service.
  - Transfer Appliance.

## Cloud SQL

  Fully Managable databases, for example:
    - MySQL.
    - PostgreSQL.
    - SQL Server.
  Mundane tasks:
    - Applying patches/updates.
    - Managing backups.
    - Configuring replications
    
 Cloud SQL is for a little smaller datas storagaes then Cloud Storage. I can exopand to 400 GB.
 
 ## Cloud Spanner
  
  - Scales horizontally.
  - Strongly consistent.
  - Speaks SQL.

Suited for releational dbs with high number of inputs/outputs

## Firestore

  - Flexible.
  - Scales horizontally.
  - NoSQL cloud db

stored in docs and organized in collections

Can Write, read, query, listen On and Offline.
Charged for:
Reading writing, deleting docs.
Querys is counted as a doc read.
Amount of db storage used.
Amount of network badwidth used.

Free quota:
- 50,000 doc read.
- 20,000 doc writes.
- 20,000 doc deletes.
- 1GB of stored data.

## Cloud Bigtable

  No SQL big data service.
  
   - Handle massive workdloads.
   - Consistent low latency
   - High throughput.
   Great choice for:
   - Operational apps.
   - Analytical apps.
   
 Often use Bigtable if:
  - Work with more than 1 TB of semi-structured or structured data.
  - Data is fast with high throughput or rapidly changing.
  - NoSQL data.
  - Work with big data
  - Running ml.
  
 Can be managed through many variaties through a API. ex, managed VMs, HBase REST Server, Java server.
 Data can be streamed and batch processed.
 
| Option  | Best for  | Capacity  | 
|---------|-----------|----------|
| Cloud Storage  | - Storing immutable blobs larger than 10 mb  | Petabytes, Max unit size 5 TB per object  |
| Cloud SQL  | - Full SQL support for an online transaction processing system <br /> - Web frameworks and existing apps | Up to 64 GB  |
| Spanner  | - Full SQL support for an online transaction processing system <br /> - Horizontal scalability | Petabytes |
| Firestore  | - Massive scaling and predictability together with real time query results and offline query support | Terabytes, Max unit size: 1MB per entity  |
| Cloud Bigtable  | - Storing large amount of structured objects<br />- Does not support SQL queries and multi-row transactions<br />- Analytical data with heavy read and write events  | Petabytes, Max unit size: 10 MB p/cell, 100 MB p/row  |
  

 
