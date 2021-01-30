## Delta Lake ##
- Stoarge Layer that brings reliability to the data lakes.
- Concept called delta tables. Data is written to/read from delta tables. 
- Gives features like:
    - ACID transactions for reads and writes over large collections of data, stored as files, in a distributed file system or object store.
    - Scalable metadata handling: Leverages Spark’s distributed processing power to handle all the metadata for petabyte-scale tables with billions of files at ease.
    - Streaming and batch unification: A table in Delta Lake is a batch table as well as a streaming source and sink. Streaming data ingest, batch historic backfill, interactive queries all just work out of the box.
    - Schema enforcement: Automatically handles schema variations to prevent insertion of bad records during ingestion.
    - Time travel: Data versioning enables rollbacks, full historical audit trails, and reproducible machine learning experiments.
    - Upserts and deletes: Supports merge, update and delete operations to enable complex use cases like change-data-capture, slowly-changing-dimension (SCD) operations, streaming upserts, and so on.
