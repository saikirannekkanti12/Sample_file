Google Cloud Storage and Database Selection — Decision Chart

1. Start: Is your data structured?

* NO → Do you need a shared file system?
    * YES → Filestore
    * NO → Cloud Storage
* YES → Does your workload involve analytics?
    * YES → Do you need extensive updates and/or low latency?
        * YES → Bigtable
        * NO → BigQuery
    * NO → Is your data relational?
        * YES → Do you need HTAP?
            * YES → AlloyDB
            * NO → Do you need global scalability?
                * YES → Cloud Spanner
                * NO → Cloud SQL
        * NO → Do you need application caching?
            * YES → Memorystore
            * NO → Firestore

2. Services in the Chart

Google Cloud service	Description shown in chart
Filestore	Shared file system
Cloud Storage	Object storage
AlloyDB	Relational database with HTAP requirement
Cloud Spanner	Relational database with global scalability
Cloud SQL	Relational database without global scalability requirement
Memorystore	Application caching
Firestore	NoSQL document database
Bigtable	NoSQL with high throughput
BigQuery	Data warehouse with SQL querying

3. Abbreviation

HTAP — Hybrid Transactional and Analytical Processing.