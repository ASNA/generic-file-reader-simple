## AVR class to read any file -- very simple version

This project provides a class named `DataGateHelper` that lets you read any DataGate physical or logical file. This is a simple version to quickly expose a few concepts. A better, more production-ready version is in the `WithEvents` branch.

### Look ma, no DclDiskFile! 

The key concept behind this example is that it doesn't use AVR's compile-time file processing (ie, it doesn't use a `DclDiskFile` that must be explicitly declared prior to compilation). Rather, this example uses the DataGate API. The DataGate API requires a little more setup than AVR's compile-time file handling and a little grungy coding, but the pay-off is that you can open _any_ file (physical or logical file) at runtime. 

Three DataGate objects provide the basic for this example's file procesing: 

1. `AdgConnection` -- This object provides a DataGate database connection and is essentially analogous to AVR's `DclDb` object. 
2. `FileAdapter` -- This object provides a DataGate file object and is somewhat analogous to AVR's `DclDiskFile` object.
3. `AdgDataSet` -- This object provides the buffer into which a record format is read. It doesn't have a directly analogous counterpart object in AVR -- because AVR provides the record format buffer implicitly through its `DclDiskFile` object (where, after a read, you simply reference record format names to read fields from the record format).

This version of the `DataGateHelper` class declares the three objects mentioned above as global members and then does its work in three subroutines:

#### OpenForRead subroutine

This subroutine takes three string arguments: 

1. Database name
2. Library name 
3. File name

At runtime, these values specify the file you want opened. You can either specify a specific library or use `*LIB` to use the library list.

[Read the fully annotated code here.](https://asna.github.io/generic-file-reader-simple/pycco-index.html)






