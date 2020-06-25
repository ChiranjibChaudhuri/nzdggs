# `nz_table_as_dplyr`: Netezza Table To dplyr

## Description


 Converts a Netezza table to a dplyr object.


## Usage

```r
nz_table_as_dplyr(DSN, tableName)
```


## Arguments

Argument      |Description
------------- |----------------
```DSN```     |     DSN object extracted from nz_init function
```tableName```     |     the name of the table to read

## Value


 A dplyr object


## Examples

```r
DSN <- nz_init("NZSQL_F","ADMIN")
mbp <- nz_table_as_dplyr(DSN,"MPB")
head(mbp)

```