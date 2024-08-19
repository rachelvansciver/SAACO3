# Athena
- serverless
- uses SQL Language
- interactive query service to analyze data in s3
- per only per queries run or compute time
- process logs
- ad hoc analysis
- expensive if data is not columnar
- store results back to [[S3]]

## Use
- commonly used with quicksight
- business intel, analytics, reporting
- use glue to convert data to parquet or orc
- partition data by path
```
pathtoBucket/pathtotable
                        /partition_col_key
                        /partition_col_key
```
- use larger files

## Supported Data types
- CSV
- JSON
- ORC
- Avro
- Parquet (faster than csv)

## Price
- 5 Dollar per TB scanned

## Federated query
- query data from outside from [[S3]]
- use data source connectior ([[Lambda]] function which connects to another service)