### LSM Trees ###
  - Immutable data structure
  - optimized for write performance, done at the expense of reads, which have to retrieve multiple data record versions and reconcile them
  - write operations to disk are sequential( writes are appended to memtables and written to disk sequentially)
  - Require maintainece since many files get accumated on disk and reads need to read many SStables to return results + space ampilfication due to redundant records, hence, periodic compaction needed to keep only live records

Compaction
  - Merging and reconcilation for disk resident SSTables done using multiway merge sort/ m- way merge sort where m is the number of SStables being merged
  - Many compaction techinques available:
     - Size tiered compaction: https://shrikantbang.wordpress.com/2014/04/22/size-tiered-compaction-strategy-in-apache-cassandra/
     - Level tired compaction: https://www.scylladb.com/2018/01/31/compaction-series-leveled-compaction/

Bloom Filter
  - to reduce read amplification, a way to find if a record is present in a file or not, If not, we can avoid reading that file altogether.
  - is a space-efficient probabilistic data structure that can be used to test whether the element is a member of the set or not.
  - can produce false-positive matches, but cannot produce false negatives 
  - uses a bit-array and multiple hash functions.
  - Since tables in LSM Trees are immutable, bit array's size can be known up-front.
