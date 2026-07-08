# Apache Spark Connector for SQL Server (Databricks Runtime 17.3 LTS Community Fork)

> Community-maintained fork of Microsoft's SQL Spark Connector updated for **Databricks Runtime 17.3 LTS**, **Apache Spark 4.x**, and modern Databricks environments.

---

## Overview

This repository is a community-maintained fork of the original Microsoft **Apache Spark Connector for SQL Server and Azure SQL**.

The original Microsoft connector was designed for older Spark releases. Since then, Databricks Runtime has introduced major API changes that prevent the original connector from compiling or running without modification.

This repository contains the required source code updates to successfully build and use the connector with:

- Databricks Runtime 17.3 LTS
- Apache Spark 4.x
- Latest SQL Server JDBC Driver
- Scala 2.13 (or the version used by DBR 17.3)

The goal is to help organizations that still depend on the SQL Spark Connector continue using it on modern Databricks runtimes.

---

## Why this fork?

Microsoft archived the original repository in February 2025 and it is no longer actively maintained.

Several Spark API changes introduced after Spark 3.x prevent the original connector from compiling on modern Databricks runtimes.

This repository contains compatibility fixes that allow the connector to compile and run on Databricks Runtime 17.3 LTS.

---

## What's Changed

This fork includes modifications such as:

- Spark 4.x compatibility
- Databricks Runtime 17.3 compatibility
- Updated Maven dependencies
- Updated Spark SQL APIs
- Updated Scala collections conversions
- Build fixes
- Dependency cleanup
- Modernized project configuration

---

## Compatibility

| Component | Version |
|------------|----------|
| Databricks Runtime | 17.3 LTS |
| Apache Spark | 4.x |
| Scala | Runtime compatible |
| SQL Server | Supported |
| Azure SQL | Supported |

---

## Repository Structure

```
sql-spark-connector-dbx17.3LTS/
├── src/
├── project/
├── samples/
├── pom.xml
├── README.md
└── document.md
```

---

## Download

### Prebuilt JAR

A prebuilt JAR is available in this repository.

```
17.3LTS_v4_spark-mssql-connector-1.4.0.jar
```

Upload it to your Databricks workspace or attach it as a cluster library.

---

## Build

```bash
mvn clean package -DskipTests
```

The generated JAR will be located under:

```
target/
```

---

## Usage

Scala

```scala
df.write
 .format("com.microsoft.sqlserver.jdbc.spark")
 .option("url", jdbcUrl)
 .option("dbtable", "dbo.Employee")
 .mode("append")
 .save()
```

Python

```python
df.write \
    .format("com.microsoft.sqlserver.jdbc.spark") \
    .option("url", jdbcUrl) \
    .option("dbtable", "dbo.Employee") \
    .mode("append") \
    .save()
```

---

## Migration Notes

If you are upgrading from the original Microsoft connector:

- Rebuild using the updated source
- Use the provided JAR
- Validate your Spark jobs on DBR 17.3
- Verify JDBC driver compatibility

---

## Credits

Original connector:

Microsoft SQL Spark Connector

https://github.com/microsoft/sql-spark-connector

This repository is an independent community fork intended to keep the connector usable on modern Databricks runtimes.

---

## Disclaimer

This project is **not affiliated with or supported by Microsoft or Databricks**.

It is provided as a community-maintained compatibility fork.

Use in production after validating in your own environment.

---

## License

This project follows the same license as the original Microsoft repository.
