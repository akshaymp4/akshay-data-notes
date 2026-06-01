<div class="databricks-hero">
  <div class="databricks-chip">PySpark | Databricks | Code Reference</div>
  <h1>Databricks Practical Guide</h1>
  <p>
    Code-first PySpark handbook for Databricks data engineering work. Use this as a quick project reference.
  </p>
</div>

## 1. DataFrame Fundamentals { .databricks-h2 }

### 1.1 Create DataFrame { .databricks-h3 }

Small DataFrames are useful for testing logic, lookup values, and examples.

```python
data = [(1, "Akshay", 5000), (2, "Rahul", 7000)]
columns = ["emp_id", "emp_name", "salary"]

df = spark.createDataFrame(data, columns)
display(df)
```

### 1.2 Explicit Schema { .databricks-h3 }

Use explicit schema in production to avoid wrong data types.

```python
from pyspark.sql.types import StructType, StructField, IntegerType, StringType, DecimalType

schema = StructType([
    StructField("order_id", IntegerType(), False),
    StructField("customer_id", IntegerType(), True),
    StructField("amount", DecimalType(10, 2), True),
    StructField("status", StringType(), True)
])

df = (
    spark.read
    .format("csv")
    .schema(schema)
    .option("header", True)
    .load("/Volumes/dev/landing/orders/")
)
```

### 1.3 Infer Schema { .databricks-h3 }

Use only for exploration, not production ingestion.

```python
df = (
    spark.read
    .format("csv")
    .option("header", True)
    .option("inferSchema", True)
    .load("/Volumes/dev/landing/orders/")
)
```

### 1.4 ArrayType, MapType, Nested Schema { .databricks-h3 }

Use nested schemas for API, JSON, Kafka, and event data.

```python
from pyspark.sql.types import ArrayType, MapType

schema = StructType([
    StructField("event_id", StringType(), True),
    StructField("customer", StructType([
        StructField("customer_id", IntegerType(), True),
        StructField("name", StringType(), True)
    ]), True),
    StructField("items", ArrayType(StructType([
        StructField("sku", StringType(), True),
        StructField("qty", IntegerType(), True)
    ])), True),
    StructField("properties", MapType(StringType(), StringType()), True)
])
```

### 1.5 Inspect DataFrame { .databricks-h3 }

Use these commands before transformations and writes.

```python
df.printSchema()
df.show(20, truncate=False)
display(df.limit(100))
df.count()
df.describe().show()
df.summary().show()
```

### 1.6 select, alias, cast { .databricks-h3 }

Use `select` to keep only required columns and apply clean names.

```python
from pyspark.sql import functions as F

clean_df = df.select(
    F.col("order_id").cast("int"),
    F.col("customer_id").cast("int"),
    F.col("amount").cast("decimal(10,2)").alias("order_amount"),
    F.upper("status").alias("order_status")
)
```

SQL equivalent:

```sql
SELECT
  CAST(order_id AS INT) AS order_id,
  CAST(customer_id AS INT) AS customer_id,
  CAST(amount AS DECIMAL(10,2)) AS order_amount,
  UPPER(status) AS order_status
FROM dev.bronze.orders;
```

### 1.7 withColumn, rename, drop { .databricks-h3 }

Use for adding, renaming, and removing columns.

```python
df2 = (
    df
    .withColumn("load_date", F.current_date())
    .withColumnRenamed("status", "order_status")
    .drop("_corrupt_record")
)
```

### 1.8 distinct and dropDuplicates { .databricks-h3 }

Use `distinct` for full-row duplicates and `dropDuplicates` for key-level duplicates.

```python
df_distinct = df.distinct()
df_dedup = df.dropDuplicates(["order_id"])
```

### 1.9 filter, where, sort, orderBy { .databricks-h3 }

Use filters early to reduce data volume.

```python
paid_orders = (
    df
    .filter((F.col("status") == "PAID") & (F.col("amount") > 0))
    .orderBy(F.col("order_date").desc())
)
```

### 1.10 groupBy and aggregations { .databricks-h3 }

Use aggregations for metrics, validations, and Gold tables.

```python
sales_df = (
    df.groupBy("order_date")
    .agg(
        F.count("*").alias("order_count"),
        F.sum("amount").alias("total_sales"),
        F.avg("amount").alias("avg_order_value")
    )
)
```

## 2. Data Transformations { .databricks-h2 }

### 2.1 String Functions { .databricks-h3 }

Use built-in Spark functions instead of Python UDFs.

```python
df = df.select(
    F.trim("name").alias("name"),
    F.upper("country").alias("country"),
    F.lower("email").alias("email"),
    F.regexp_replace("phone", "[^0-9]", "").alias("phone")
)
```

### 2.2 Date and Timestamp Functions { .databricks-h3 }

Use standard date parsing before writing Silver tables.

```python
df = (
    df
    .withColumn("order_date", F.to_date("order_date", "yyyy-MM-dd"))
    .withColumn("order_ts", F.to_timestamp("order_ts"))
    .withColumn("year", F.year("order_date"))
    .withColumn("month", F.month("order_date"))
)
```

### 2.3 Numeric Functions { .databricks-h3 }

Use numeric functions for rounding, absolute values, and calculations.

```python
df = df.select(
    "order_id",
    F.round("amount", 2).alias("amount"),
    F.abs("discount").alias("discount"),
    (F.col("amount") - F.col("discount")).alias("net_amount")
)
```

### 2.4 when / otherwise { .databricks-h3 }

Use for business rules and derived categories.

```python
df = df.withColumn(
    "amount_band",
    F.when(F.col("amount") >= 1000, "HIGH")
     .when(F.col("amount") >= 100, "MEDIUM")
     .otherwise("LOW")
)
```

SQL equivalent:

```sql
SELECT *,
  CASE
    WHEN amount >= 1000 THEN 'HIGH'
    WHEN amount >= 100 THEN 'MEDIUM'
    ELSE 'LOW'
  END AS amount_band
FROM dev.silver.orders;
```

### 2.5 Arrays, Structs, Maps { .databricks-h3 }

Use nested column functions to process semi-structured data.

```python
df = df.select(
    "event_id",
    F.col("customer.customer_id").alias("customer_id"),
    F.col("properties")["source"].alias("source"),
    F.size("items").alias("item_count")
)
```

### 2.6 explode, posexplode, flatten { .databricks-h3 }

Use explode to convert arrays into rows.

```python
items_df = df.select("event_id", F.explode_outer("items").alias("item"))

items_df = items_df.select(
    "event_id",
    F.col("item.sku").alias("sku"),
    F.col("item.qty").alias("qty")
)

pos_df = df.select("event_id", F.posexplode_outer("items").alias("position", "item"))
flat_df = df.select("event_id", F.flatten("nested_arrays").alias("flat_values"))
```

## 3. Joins { .databricks-h2 }

### 3.1 Common Joins { .databricks-h3 }

Use left joins for fact-to-dimension enrichment.

```python
orders = spark.table("dev.silver.orders")
customers = spark.table("dev.silver.customers")

inner_df = orders.join(customers, "customer_id", "inner")
left_df = orders.join(customers, "customer_id", "left")
right_df = orders.join(customers, "customer_id", "right")
full_df = orders.join(customers, "customer_id", "full")
```

### 3.2 Semi and Anti Join { .databricks-h3 }

Use semi join to keep matched rows and anti join to find missing rows.

```python
valid_orders = orders.join(customers, "customer_id", "left_semi")
missing_customers = orders.join(customers, "customer_id", "left_anti")
```

### 3.3 Cross Join { .databricks-h3 }

Use only when every combination is required.

```python
result = products.crossJoin(regions)
```

### 3.4 Broadcast Join { .databricks-h3 }

Broadcast small lookup tables to avoid large shuffles.

```python
from pyspark.sql.functions import broadcast

result = orders.join(broadcast(customers), "customer_id", "left")
```

### 3.5 Join Hints { .databricks-h3 }

Use hints only when Spark picks a bad plan.

```python
result = orders.hint("merge").join(customers.hint("broadcast"), "customer_id", "left")
```

SQL equivalent:

```sql
SELECT /*+ BROADCAST(c) */ *
FROM dev.silver.orders o
LEFT JOIN dev.silver.customers c
ON o.customer_id = c.customer_id;
```

### 3.6 Skew Handling { .databricks-h3 }

Check skew before salting or changing join logic.

```python
orders.groupBy("customer_id").count().orderBy(F.desc("count")).show(20)

spark.conf.set("spark.sql.adaptive.enabled", "true")
spark.conf.set("spark.sql.adaptive.skewJoin.enabled", "true")
```

## 4. Window Functions { .databricks-h2 }

### 4.1 Ranking Functions { .databricks-h3 }

Use ranking functions for latest records and top-N logic.

```python
from pyspark.sql.window import Window

w = Window.partitionBy("customer_id").orderBy(F.col("order_date").desc())

df = (
    orders
    .withColumn("row_number", F.row_number().over(w))
    .withColumn("rank", F.rank().over(w))
    .withColumn("dense_rank", F.dense_rank().over(w))
)
```

### 4.2 lead and lag { .databricks-h3 }

Use `lag` and `lead` for change detection.

```python
df = (
    orders
    .withColumn("previous_amount", F.lag("amount").over(w))
    .withColumn("next_amount", F.lead("amount").over(w))
)
```

### 4.3 Running Totals and Moving Averages { .databricks-h3 }

Use window frames for cumulative and rolling metrics.

```python
running_w = Window.partitionBy("customer_id").orderBy("order_date").rowsBetween(Window.unboundedPreceding, Window.currentRow)
moving_w = Window.partitionBy("customer_id").orderBy("order_date").rowsBetween(-6, Window.currentRow)

df = (
    orders
    .withColumn("running_total", F.sum("amount").over(running_w))
    .withColumn("moving_7_avg", F.avg("amount").over(moving_w))
)
```

## 5. Reading Data { .databricks-h2 }

### 5.1 Read CSV, JSON, Parquet, Delta, Avro, XML, Excel { .databricks-h3 }

Use explicit schema and source-specific options.

```python
csv_df = (
    spark.read
    .format("csv")
    .schema(schema)
    .option("header", True)
    .load("/Volumes/dev/landing/csv/")
)

json_df = (
    spark.read
    .format("json")
    .schema(schema)
    .load("/Volumes/dev/landing/json/")
)

multi_json_df = (
    spark.read
    .format("json")
    .schema(schema)
    .option("multiLine", True)
    .load("/Volumes/dev/landing/multiline-json/")
)

parquet_df = (
    spark.read
    .format("parquet")
    .load("/Volumes/dev/landing/parquet/")
)

delta_df = (
    spark.read
    .format("delta")
    .load("/Volumes/dev/landing/delta/")
)

avro_df = (
    spark.read
    .format("avro")
    .load("/Volumes/dev/landing/avro/")
)

xml_df = (
    spark.read
    .format("xml")
    .option("rowTag", "order")
    .load("/Volumes/dev/landing/xml/")
)

excel_df = (
    spark.read
    .format("com.crealytics.spark.excel")
    .option("header", True)
    .load("/Volumes/dev/landing/orders.xlsx")
)
```

### 5.2 Read from DBFS, ADLS, S3, GCS, Local { .databricks-h3 }

Prefer governed volumes or external locations for production.

```python
dbfs_df = (
    spark.read
    .format("parquet")
    .load("dbfs:/mnt/landing/orders/")
)

volume_df = (
    spark.read
    .format("parquet")
    .load("/Volumes/dev/landing/orders/")
)

adls_df = (
    spark.read
    .format("parquet")
    .load("abfss://landing@storageaccount.dfs.core.windows.net/orders/")
)

s3_df = (
    spark.read
    .format("parquet")
    .load("s3://company-landing/orders/")
)

gcs_df = (
    spark.read
    .format("parquet")
    .load("gs://company-landing/orders/")
)

local_df = (
    spark.read
    .format("parquet")
    .load("file:/tmp/orders/")
)
```

### 5.3 Corrupt and Bad Records { .databricks-h3 }

Capture bad records instead of silently dropping them.

```python
df = (
    spark.read
    .format("json")
    .schema(schema)
    .option("mode", "PERMISSIVE")
    .option("columnNameOfCorruptRecord", "_corrupt_record")
    .option("badRecordsPath", "/Volumes/dev/quarantine/orders/")
    .load("/Volumes/dev/landing/orders/")
)
```

### 5.4 Partition Discovery { .databricks-h3 }

Spark discovers partitions from folder names like `load_date=2026-05-31`.

```python
df = (
    spark.read
    .format("parquet")
    .load("/Volumes/dev/landing/orders/")
)

df.select("load_date").distinct().show()
```

## 6. Writing Data { .databricks-h2 }

### 6.1 Append and Overwrite { .databricks-h3 }

Use append for incremental loads and overwrite for full refresh tables.

```python
df.write.format("delta").mode("append").saveAsTable("dev.bronze.orders")
df.write.format("delta").mode("overwrite").option("overwriteSchema", "true").saveAsTable("dev.silver.orders")
```

### 6.2 Partitioned Writes { .databricks-h3 }

Partition by low-cardinality columns commonly used in filters.

```python
df.write.format("delta").mode("append").partitionBy("order_date").saveAsTable("dev.silver.orders")
```

### 6.3 Dynamic Partition Overwrite { .databricks-h3 }

Use to replace only affected partitions.

```python
spark.conf.set("spark.sql.sources.partitionOverwriteMode", "dynamic")
df.write.format("delta").mode("overwrite").insertInto("dev.silver.orders")
```

### 6.4 Write Parquet, CSV, JSON { .databricks-h3 }

Use non-Delta formats mainly for export or interoperability.

```python
(
    df.write
    .format("parquet")
    .mode("overwrite")
    .save("/Volumes/dev/export/orders_parquet/")
)

(
    df.write
    .format("csv")
    .mode("overwrite")
    .option("header", True)
    .save("/Volumes/dev/export/orders_csv/")
)

(
    df.write
    .format("json")
    .mode("overwrite")
    .save("/Volumes/dev/export/orders_json/")
)
```

### 6.5 Small File Handling { .databricks-h3 }

Use optimized writes and scheduled compaction for Delta tables.

```sql
OPTIMIZE dev.silver.orders;
```

```python
spark.conf.set("spark.databricks.delta.optimizeWrite.enabled", "true")
spark.conf.set("spark.databricks.delta.autoCompact.enabled", "true")
```

## 7. JSON Processing { .databricks-h2 }

### 7.1 Parse JSON String { .databricks-h3 }

Use `from_json` when JSON is stored inside a string column.

```python
parsed_df = raw_df.withColumn("payload", F.from_json("payload_json", schema))
```

### 7.2 Read Nested JSON and Explode Arrays { .databricks-h3 }

Use this for API payloads with nested arrays.

```python
events = (
    spark.read
    .format("json")
    .schema(schema)
    .option("multiLine", True)
    .load("/Volumes/dev/landing/api/")
)

items = (
    events
    .select("event_id", F.col("customer.customer_id").alias("customer_id"), F.explode_outer("items").alias("item"))
    .select("event_id", "customer_id", F.col("item.sku").alias("sku"), F.col("item.qty").alias("qty"))
)
```

### 7.3 to_json and schema_of_json { .databricks-h3 }

Use `to_json` to create JSON output and `schema_of_json` to bootstrap a schema.

```python
json_df = df.select(F.to_json(F.struct("order_id", "amount", "status")).alias("payload_json"))

schema_text = spark.range(1).select(
    F.schema_of_json(F.lit('{"order_id":1,"amount":10.5}')).alias("schema")
).first()["schema"]
```

## 8. Delta Lake { .databricks-h2 }

### 8.1 Create Managed and External Tables { .databricks-h3 }

Managed tables use Databricks-managed storage; external tables point to cloud storage.

```sql
CREATE TABLE IF NOT EXISTS dev.silver.orders (
  order_id BIGINT,
  customer_id BIGINT,
  amount DECIMAL(10,2)
)
USING DELTA;

CREATE TABLE IF NOT EXISTS dev.bronze.raw_orders
USING DELTA
LOCATION 'abfss://bronze@storageaccount.dfs.core.windows.net/orders';
```

### 8.2 Merge / Update / Delete { .databricks-h3 }

Use merge for upsert and CDC pipelines.

```python
from delta.tables import DeltaTable

target = DeltaTable.forName(spark, "dev.silver.orders")

(
    target.alias("t")
    .merge(updates.alias("s"), "t.order_id = s.order_id")
    .whenMatchedUpdateAll()
    .whenNotMatchedInsertAll()
    .execute()
)
```

```sql
UPDATE dev.silver.orders SET status = 'CANCELLED' WHERE status = 'VOIDED';
DELETE FROM dev.silver.orders WHERE order_id IS NULL;
```

### 8.3 Time Travel, Restore, Vacuum, Optimize, ZORDER { .databricks-h3 }

Use these commands for debugging, recovery, cleanup, and performance.

```sql
DESCRIBE HISTORY dev.silver.orders;
SELECT * FROM dev.silver.orders VERSION AS OF 10;
RESTORE TABLE dev.silver.orders TO VERSION AS OF 9;
VACUUM dev.silver.orders RETAIN 168 HOURS;
OPTIMIZE dev.silver.orders ZORDER BY (customer_id, order_date);
```

## 9. Incremental Processing { .databricks-h2 }

### 9.1 Watermark Table Pattern { .databricks-h3 }

Store last processed timestamp in an audit table.

```python
last_ts = (
    spark.table("dev.audit.watermarks")
    .filter("pipeline_name = 'orders'")
    .select(F.max("watermark_value"))
    .first()[0]
)

incremental_df = spark.table("dev.bronze.orders").filter(F.col("updated_at") > F.lit(last_ts))
```

### 9.2 CDC Merge Pattern { .databricks-h3 }

Keep the latest change per key before merge.

```python
w = Window.partitionBy("order_id").orderBy(F.col("operation_ts").desc())
latest_cdc = cdc_df.withColumn("rn", F.row_number().over(w)).filter("rn = 1").drop("rn")

(
    target.alias("t")
    .merge(latest_cdc.alias("s"), "t.order_id = s.order_id")
    .whenMatchedDelete("s.operation = 'DELETE'")
    .whenMatchedUpdateAll("s.operation IN ('UPDATE', 'INSERT')")
    .whenNotMatchedInsertAll("s.operation IN ('INSERT', 'UPDATE')")
    .execute()
)
```

### 9.3 Late Arriving Data { .databricks-h3 }

Reprocess a small lookback window to handle late records.

```python
lookback_df = source_df.filter(F.col("event_date") >= F.date_sub(F.current_date(), 7))
```

## 10. Medallion Architecture { .databricks-h2 }

### 10.1 Bronze to Silver to Gold { .databricks-h3 }

Bronze keeps raw data, Silver cleans it, and Gold creates business output.

```python
bronze = (
    spark.read
    .format("json")
    .schema(schema)
    .load("/Volumes/dev/landing/orders/")
    .withColumn("ingestion_time", F.current_timestamp())
)

bronze.write.format("delta").mode("append").saveAsTable("dev.bronze.raw_orders")

silver = (
    spark.table("dev.bronze.raw_orders")
    .filter("order_id IS NOT NULL AND amount >= 0")
    .dropDuplicates(["order_id"])
)

silver.write.format("delta").mode("overwrite").saveAsTable("dev.silver.orders")

gold = silver.groupBy("order_date").agg(F.count("*").alias("order_count"), F.sum("amount").alias("sales"))
gold.write.format("delta").mode("overwrite").saveAsTable("dev.gold.daily_sales")
```

## 11. Delta Live Tables { .databricks-h2 }

### 11.1 DLT End-to-End { .databricks-h3 }

Use DLT when you want managed dependencies, expectations, and pipeline monitoring.

```python
import dlt
from pyspark.sql import functions as F

@dlt.table
def bronze_orders():
    return (
        spark.readStream
        .format("cloudFiles")
        .option("cloudFiles.format", "json")
        .load("/Volumes/dev/landing/orders/")
    )

@dlt.table
@dlt.expect_or_drop("valid_order_id", "order_id IS NOT NULL")
@dlt.expect_or_drop("valid_amount", "amount >= 0")
def silver_orders():
    return dlt.read_stream("bronze_orders").dropDuplicates(["order_id"])

@dlt.table
def gold_daily_sales():
    return dlt.read("silver_orders").groupBy("order_date").agg(F.sum("amount").alias("sales"))
```

### 11.2 DLT CDC / Auto CDC { .databricks-h3 }

Use `apply_changes` for ordered CDC feeds.

```python
dlt.create_streaming_table("silver_customers")

dlt.apply_changes(
    target="silver_customers",
    source="bronze_customer_cdc",
    keys=["customer_id"],
    sequence_by=F.col("operation_ts"),
    apply_as_deletes=F.expr("operation = 'DELETE'"),
    except_column_list=["operation", "operation_ts"],
    stored_as_scd_type=1
)
```

## 12. Structured Streaming { .databricks-h2 }

### 12.1 Stream to Delta { .databricks-h3 }

Always use a checkpoint location for streaming writes.

```python
query = (
    spark.readStream.table("dev.bronze.orders_stream")
    .writeStream
    .option("checkpointLocation", "/Volumes/dev/checkpoints/orders/")
    .trigger(processingTime="5 minutes")
    .toTable("dev.silver.orders_stream")
)
```

### 12.2 Kafka / Event Hubs { .databricks-h3 }

Kafka messages usually come in `key` and `value` as binary columns. Cast them to string before parsing.

```python
kafka_df = (
    spark.readStream
    .format("kafka")
    .option("kafka.bootstrap.servers", "broker:9092")
    .option("subscribe", "orders")
    .load()
)

raw_kafka_df = kafka_df.select(
    F.col("topic"),
    F.col("partition"),
    F.col("offset"),
    F.col("timestamp").alias("kafka_timestamp"),
    F.col("key").cast("string").alias("message_key"),
    F.col("value").cast("string").alias("message_value")
)
```

Batch read from Kafka topic:

```python
kafka_batch_df = (
    spark.read
    .format("kafka")
    .option("kafka.bootstrap.servers", "broker:9092")
    .option("subscribe", "orders")
    .option("startingOffsets", "earliest")
    .option("endingOffsets", "latest")
    .load()
)
```

### 12.2.1 Parse Simple JSON Payload { .databricks-h3 }

Use this when Kafka `value` contains flat JSON.

```json
{"order_id": 101, "customer_id": 10, "amount": 250.50, "status": "PAID"}
```

```python
from pyspark.sql.types import StructType, StructField, IntegerType, StringType, DecimalType
from pyspark.sql import functions as F

order_schema = StructType([
    StructField("order_id", IntegerType(), True),
    StructField("customer_id", IntegerType(), True),
    StructField("amount", DecimalType(10, 2), True),
    StructField("status", StringType(), True)
])

orders_stream = (
    raw_kafka_df
    .withColumn("payload", F.from_json("message_value", order_schema))
    .select(
        "topic",
        "partition",
        "offset",
        "kafka_timestamp",
        "message_key",
        F.col("payload.*")
    )
)
```

### 12.2.2 Parse Nested JSON Payload { .databricks-h3 }

Use this when payload has structs inside structs.

```json
{
  "event_id": "evt-1001",
  "customer": {"customer_id": 10, "name": "Akshay"},
  "order": {"order_id": 101, "amount": 250.50}
}
```

```python
nested_schema = StructType([
    StructField("event_id", StringType(), True),
    StructField("customer", StructType([
        StructField("customer_id", IntegerType(), True),
        StructField("name", StringType(), True)
    ]), True),
    StructField("order", StructType([
        StructField("order_id", IntegerType(), True),
        StructField("amount", DecimalType(10, 2), True)
    ]), True)
])

nested_orders_stream = (
    raw_kafka_df
    .withColumn("payload", F.from_json("message_value", nested_schema))
    .select(
        "kafka_timestamp",
        F.col("payload.event_id").alias("event_id"),
        F.col("payload.customer.customer_id").alias("customer_id"),
        F.col("payload.customer.name").alias("customer_name"),
        F.col("payload.order.order_id").alias("order_id"),
        F.col("payload.order.amount").alias("amount")
    )
)
```

### 12.2.3 Parse Array Inside JSON Payload { .databricks-h3 }

Use `explode_outer` when one Kafka event contains multiple child records.

```json
{
  "order_id": 101,
  "items": [
    {"sku": "A100", "qty": 2},
    {"sku": "B200", "qty": 1}
  ]
}
```

```python
from pyspark.sql.types import ArrayType

order_items_schema = StructType([
    StructField("order_id", IntegerType(), True),
    StructField("items", ArrayType(StructType([
        StructField("sku", StringType(), True),
        StructField("qty", IntegerType(), True)
    ])), True)
])

items_stream = (
    raw_kafka_df
    .withColumn("payload", F.from_json("message_value", order_items_schema))
    .select(
        F.col("payload.order_id").alias("order_id"),
        F.explode_outer("payload.items").alias("item")
    )
    .select(
        "order_id",
        F.col("item.sku").alias("sku"),
        F.col("item.qty").alias("quantity")
    )
)
```

### 12.2.4 Parse Event-Type Payloads { .databricks-h3 }

Use this when the topic carries multiple event types.

```json
{"event_type": "ORDER_CREATED", "data": {"order_id": 101, "amount": 250.50}}
```

```python
event_schema = StructType([
    StructField("event_type", StringType(), True),
    StructField("data", StructType([
        StructField("order_id", IntegerType(), True),
        StructField("amount", DecimalType(10, 2), True)
    ]), True)
])

events_stream = (
    raw_kafka_df
    .withColumn("payload", F.from_json("message_value", event_schema))
    .select(
        "message_key",
        "kafka_timestamp",
        F.col("payload.event_type").alias("event_type"),
        F.col("payload.data.order_id").alias("order_id"),
        F.col("payload.data.amount").alias("amount")
    )
)

order_created_stream = events_stream.filter(F.col("event_type") == "ORDER_CREATED")
```

### 12.2.5 Write Parsed Kafka Stream to Delta { .databricks-h3 }

Always use checkpoint location for Kafka streaming jobs.

```python
(
    orders_stream.writeStream
    .format("delta")
    .option("checkpointLocation", "/Volumes/dev/checkpoints/kafka/orders/")
    .outputMode("append")
    .toTable("dev.bronze.kafka_orders")
)
```

### 12.2.6 Bad JSON Handling { .databricks-h3 }

Keep raw payload and parsed payload so bad records can be debugged.

```python
debug_stream = (
    raw_kafka_df
    .withColumn("payload", F.from_json("message_value", order_schema))
    .withColumn(
        "is_bad_json",
        F.col("message_value").isNotNull() & F.col("payload").isNull()
    )
)
```

### 12.3 Stream Joins and Watermarks { .databricks-h3 }

Use watermarks to control streaming state.

```python
joined = (
    orders_stream.withWatermark("order_time", "30 minutes")
    .join(payments_stream.withWatermark("payment_time", "30 minutes"), "order_id")
)
```

### 12.4 Trigger Options { .databricks-h3 }

Use `availableNow` for scheduled incremental file loads.

```python
df.writeStream.trigger(availableNow=True).toTable("dev.bronze.orders")
df.writeStream.trigger(processingTime="1 minute").toTable("dev.bronze.orders")
```

## 13. Auto Loader { .databricks-h2 }

### 13.1 Auto Loader Initial and Incremental Load { .databricks-h3 }

Auto Loader processes new files incrementally.

```python
df = (
    spark.readStream
    .format("cloudFiles")
    .option("cloudFiles.format", "json")
    .option("cloudFiles.schemaLocation", "/Volumes/dev/checkpoints/schema/orders/")
    .option("cloudFiles.schemaEvolutionMode", "addNewColumns")
    .option("rescuedDataColumn", "_rescued_data")
    .load("/Volumes/dev/landing/orders/")
)

(
    df.writeStream
    .option("checkpointLocation", "/Volumes/dev/checkpoints/orders/")
    .trigger(availableNow=True)
    .toTable("dev.bronze.orders")
)
```

### 13.2 Notification vs Directory Listing { .databricks-h3 }

Use notification mode for large landing zones and directory listing for simpler folders.

```python
df = (
    spark.readStream
    .format("cloudFiles")
    .option("cloudFiles.format", "csv")
    .option("cloudFiles.useNotifications", "true")
    .load("/Volumes/dev/landing/orders/")
)
```

## 14. Data Quality { .databricks-h2 }

### 14.1 Null, Duplicate, RI, Business Checks { .databricks-h3 }

Use these checks before writing Silver or Gold tables.

```python
nulls = df.select([F.sum(F.col(c).isNull().cast("int")).alias(f"{c}_nulls") for c in ["order_id", "amount"]])
duplicates = df.groupBy("order_id").count().filter("count > 1")
orphans = orders.join(customers, "customer_id", "left_anti")
bad_amounts = orders.filter("amount < 0")
```

### 14.2 DLT Quality Rules { .databricks-h3 }

Use expectations for managed data quality.

```python
@dlt.table
@dlt.expect_or_drop("valid_order_id", "order_id IS NOT NULL")
@dlt.expect_or_fail("valid_amount", "amount >= 0")
def silver_orders():
    return dlt.read("bronze_orders")
```

## 15. Slowly Changing Dimensions { .databricks-h2 }

### 15.1 SCD Type 1 { .databricks-h3 }

Type 1 overwrites old values.

```python
(
    target.alias("t")
    .merge(updates.alias("s"), "t.customer_id = s.customer_id")
    .whenMatchedUpdateAll()
    .whenNotMatchedInsertAll()
    .execute()
)
```

### 15.2 SCD Type 2 { .databricks-h3 }

Type 2 keeps history using current flag and effective dates.

```python
changed = updates.join(current_dim, "customer_id").filter("updates_hash <> current_hash")

(
    target.alias("t")
    .merge(changed.alias("s"), "t.customer_id = s.customer_id AND t.is_current = true")
    .whenMatchedUpdate(set={"is_current": "false", "effective_to": "s.effective_from"})
    .execute()
)

new_rows.write.format("delta").mode("append").saveAsTable("dev.silver.dim_customer")
```

## 16. Performance Optimization { .databricks-h2 }

### 16.1 Cache and Persist { .databricks-h3 }

Use only when the same DataFrame is reused multiple times.

```python
df_cached = df.persist()
df_cached.count()
df_cached.groupBy("country").count().show()
df_cached.unpersist()
```

### 16.2 AQE, Pushdown, Pruning { .databricks-h3 }

Enable AQE and filter early for better plans.

```python
spark.conf.set("spark.sql.adaptive.enabled", "true")
filtered = spark.table("dev.silver.orders").filter("order_date >= '2026-01-01'")
```

### 16.3 Data Skipping, ZORDER, OPTIMIZE { .databricks-h3 }

Use for Delta tables queried repeatedly by common filters.

```sql
OPTIMIZE dev.silver.orders;
OPTIMIZE dev.silver.orders ZORDER BY (customer_id, order_date);
```

### 16.4 Common Performance Mistakes { .databricks-h3 }

Avoid unnecessary shuffles, huge broadcasts, Python UDFs, too many small files, and high-cardinality partitions.

```python
# Bad partition example
df.write.partitionBy("customer_id").format("delta").saveAsTable("dev.silver.orders")
```

## 17. Unity Catalog { .databricks-h2 }

### 17.1 Catalogs, Schemas, Tables, Volumes, Permissions { .databricks-h3 }

Use Unity Catalog for governance and secure data access.

```sql
CREATE CATALOG IF NOT EXISTS dev;
CREATE SCHEMA IF NOT EXISTS dev.bronze;
CREATE VOLUME IF NOT EXISTS dev.bronze.landing;

GRANT USE CATALOG ON CATALOG dev TO `data_engineers`;
GRANT USE SCHEMA, CREATE TABLE ON SCHEMA dev.silver TO `data_engineers`;
GRANT SELECT ON TABLE dev.gold.daily_sales TO `business_users`;
```

## 18. Databricks Utilities { .databricks-h2 }

### 18.1 dbutils.fs, widgets, secrets, orchestration { .databricks-h3 }

Use `dbutils` for notebook operations.

```python
dbutils.fs.ls("/Volumes/dev/landing/")
dbutils.fs.mkdirs("/Volumes/dev/checkpoints/orders/")

dbutils.widgets.text("run_date", "")
run_date = dbutils.widgets.get("run_date")

password = dbutils.secrets.get("kv-scope", "db-password")

dbutils.notebook.run("/Repos/project/pipelines/orders", 3600, {"run_date": run_date})
```

## 19. Production Utilities { .databricks-h2 }

### 19.1 Logging and Error Handling { .databricks-h3 }

Use logging and re-raise exceptions so jobs fail correctly.

```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger("orders_pipeline")

try:
    logger.info("Pipeline started")
    run_pipeline()
except Exception:
    logger.exception("Pipeline failed")
    raise
```

### 19.2 Retry Pattern { .databricks-h3 }

Use retries for transient failures like API or storage throttling.

```python
import time

def retry(fn, attempts=3, sleep_seconds=10):
    for attempt in range(attempts):
        try:
            return fn()
        except Exception:
            if attempt == attempts - 1:
                raise
            time.sleep(sleep_seconds)
```

### 19.3 Audit Columns { .databricks-h3 }

Add audit columns at ingestion.

```python
def add_audit_columns(df, source_system):
    return (
        df
        .withColumn("source_system", F.lit(source_system))
        .withColumn("ingestion_time", F.current_timestamp())
        .withColumn("source_file", F.input_file_name())
    )
```

### 19.4 Metadata Driven Pipeline { .databricks-h3 }

Use config tables to run the same ingestion logic for many sources.

```python
configs = spark.table("dev.config.ingestion_sources").filter("is_active = true").collect()

for cfg in configs:
    df = (
        spark.read
        .format(cfg.file_format)
        .schema(cfg.schema_ddl)
        .load(cfg.source_path)
    )

    add_audit_columns(df, cfg.source_system).write.format("delta").mode("append").saveAsTable(cfg.target_table)
```

## 20. End-to-End Pipelines { .databricks-h2 }

### 20.1 CSV to Bronze to Silver to Gold { .databricks-h3 }

Use this for standard file-based batch ingestion.

```python
bronze = (
    spark.read
    .format("csv")
    .schema(schema)
    .option("header", True)
    .load("/Volumes/dev/landing/orders/")
)

bronze = add_audit_columns(bronze, "orders_csv")
bronze.write.format("delta").mode("append").saveAsTable("dev.bronze.raw_orders")

silver = (
    spark.table("dev.bronze.raw_orders")
    .filter("order_id IS NOT NULL AND amount >= 0")
    .dropDuplicates(["order_id"])
)

silver.write.format("delta").mode("overwrite").saveAsTable("dev.silver.orders")

gold = silver.groupBy("order_date").agg(F.sum("amount").alias("sales"))
gold.write.format("delta").mode("overwrite").saveAsTable("dev.gold.daily_sales")
```

### 20.2 JSON API to Delta { .databricks-h3 }

Keep raw payload first, then parse to Silver.

```python
raw = (
    spark.read
    .format("text")
    .load("/Volumes/dev/landing/api/orders/")
)

(
    raw.select(
        F.col("value").alias("payload_json"),
        F.current_timestamp().alias("ingestion_time")
    )
    .write
    .format("delta")
    .mode("append")
    .saveAsTable("dev.bronze.api_orders")
)

parsed = (
    spark.table("dev.bronze.api_orders")
    .withColumn("payload", F.from_json("payload_json", schema))
    .select("payload.*", "ingestion_time")
)

parsed.write.format("delta").mode("append").saveAsTable("dev.silver.api_orders")
```

### 20.3 CDC Pipeline { .databricks-h3 }

Use latest CDC record per key and merge into target.

```python
cdc = spark.table("dev.bronze.orders_cdc")
w = Window.partitionBy("order_id").orderBy(F.desc("operation_ts"))
latest = cdc.withColumn("rn", F.row_number().over(w)).filter("rn = 1").drop("rn")

target = DeltaTable.forName(spark, "dev.silver.orders")

(
    target.alias("t")
    .merge(latest.alias("s"), "t.order_id = s.order_id")
    .whenMatchedUpdateAll()
    .whenNotMatchedInsertAll()
    .execute()
)
```

### 20.4 Streaming Pipeline { .databricks-h3 }

Use Auto Loader and checkpoints for streaming file ingestion.

```python
stream_df = (
    spark.readStream
    .format("cloudFiles")
    .option("cloudFiles.format", "json")
    .option("cloudFiles.schemaLocation", "/Volumes/dev/checkpoints/schema/orders/")
    .load("/Volumes/dev/landing/orders/")
)

(
    stream_df.writeStream
    .option("checkpointLocation", "/Volumes/dev/checkpoints/orders/")
    .trigger(availableNow=True)
    .toTable("dev.bronze.orders")
)
```

### 20.5 DLT Pipeline { .databricks-h3 }

Use this for managed Bronze, Silver, and Gold pipeline flow.

```python
@dlt.table
def bronze_orders():
    return (
        spark.readStream
        .format("cloudFiles")
        .option("cloudFiles.format", "json")
        .load("/Volumes/dev/landing/orders/")
    )

@dlt.table
@dlt.expect_or_drop("valid_order", "order_id IS NOT NULL AND amount >= 0")
def silver_orders():
    return dlt.read_stream("bronze_orders")

@dlt.table
def gold_daily_sales():
    return dlt.read("silver_orders").groupBy("order_date").agg(F.sum("amount").alias("sales"))
```
