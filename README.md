**LevelDB is a fast key-value storage library written at Google that provides an ordered mapping from string keys to string values.**

[![Build Status](https://travis-ci.org/google/leveldb.svg?branch=master)](https://travis-ci.org/google/leveldb)
[![Build status](https://ci.appveyor.com/api/projects/status/g2j5j4rfkda6eyw5/branch/master?svg=true)](https://ci.appveyor.com/project/pwnall/leveldb)

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

### Building for Windows

First generate the Visual Studio 2017 project/solution files:

```cmd
mkdir build
cd build
cmake -G "Visual Studio 15" ..
```
The default default will build for x86. For 64-bit run:

```cmd
cmake -G "Visual Studio 15 Win64" ..
```

To compile the Windows solution from the command-line:

```cmd
devenv /build Debug leveldb.sln
```

or open leveldb.sln in Visual Studio and build from within.

## Repository contents

See [doc/index.md](doc/index.md) for more explanation. See
[doc/impl.md](doc/impl.md) for a brief overview of the implementation.

The public interface is in include/leveldb/*.h.  Callers should not include or
rely on the details of any other header files in this package.  Those
internal APIs may be changed without warning.

Guide to header files:

* **include/leveldb/db.h**: Main interface to the DB: Start here.

* **include/leveldb/options.h**: Control over the behavior of an entire database,
and also control over the behavior of individual reads and writes.

* **include/leveldb/comparator.h**: Abstraction for user-specified comparison function.
If you want just bytewise comparison of keys, you can use the default
comparator, but clients can write their own comparator implementations if they
want custom ordering (e.g. to handle different character encodings, etc.).

* **include/leveldb/iterator.h**: Interface for iterating over data. You can get
an iterator from a DB object.

* **include/leveldb/write_batch.h**: Interface for atomically applying multiple
updates to a database.

* **include/leveldb/slice.h**: A simple module for maintaining a pointer and a
length into some other byte array.

* **include/leveldb/status.h**: Status is returned from many of the public interfaces
and is used to report success and various kinds of errors.

* **include/leveldb/env.h**:
Abstraction of the OS environment.  A posix implementation of this interface is
in util/env_posix.cc.

* **include/leveldb/table.h, include/leveldb/table_builder.h**: Lower-level modules that most
clients probably won't use directly.
