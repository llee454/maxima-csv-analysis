Maxima CSV Analysis
===================

This package defines a collection of Maxima scripts that can be used to analyze data sets in CSV.

Usage
-----

### Load Prerequisites

Run the following `load` commands to load the modules that your analysis depends upon. For example:

```
load (draw)$
load (stats)$
load(lsquares)$
load (descriptive)$
load ("core.mac")$
```

### Define Field Accessors for your Data Set

This package assumes that your data is stored in CSV files that will be loaded into Maxima matrices. Field accessors are functions that take a Maxima matrix row and return the value of an element within the row, possibly after applying some transformation. To simplify accessing field values, define field indices and field accessors for your data set.

Field indices are just variables that store integers that represent the row offset of a given field. For example:

```
id_index: 1$
```

Field Accessors are represented by the `field` struct defined by fields.mac. These structs accept an index and a transform function. For example:

```
id_field: new (field (id_index, lambda ([x], x * 2)))$
```

Defines a field accessor that reads the first value of a given row, doubles the read value, and returns the result.

### Read Data

Use `read_matrix ("filename.csv")$` to read your data from CSV.
