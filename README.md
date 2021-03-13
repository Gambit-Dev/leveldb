**LevelDB is a fast key-value storage library written at Google that provides an ordered mapping from string keys to string values.**

Authors: Sanjay Ghemawat (sanjay@google.com) and Jeff Dean (jeff@google.com)

# Features

  * Keys and values are arbitrary byte arrays.
  * Data is stored sorted by key.
  * Callers can provide a custom comparison function to override the sort order.
  * The basic operations are `Put(key,value)`, `Get(key)`, `Delete(key)`.
  * Multiple changes can be made in one atomic batch.
  * Users can create a transient snapshot to get a consistent view of data.
  * Forward and backward iteration is supported over the data.
  * Data is automatically compressed using the [Snappy compression library](https://google.github.io/snappy/).
  * External activity (file system operations etc.) is relayed through a virtual interface so users can customize the operating system interactions.

# Documentation

  [LevelDB library documentation](https://github.com/google/leveldb/blob/master/doc/index.md) is online and bundled with the source code.
