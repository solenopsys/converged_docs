# SQLite

SQLite is the relational storage engine behind the native database wrappers.
It stores a database in a local file and runs SQL in the calling process, which
lets a Converged service keep its records, indexes, and transactions close to
the code that uses them.

The same SQLite connection is also the host for specialised tables. Stanchion
adds columnar virtual tables for analytical reads; `sqlite-vec` adds vector
tables and distance queries. Ordinary tables and those extensions can share a
database and participate in the same application-level workflow.

This wrapper is the native SQLite boundary: it supplies the library and the
extension-loading path used by the higher-level store implementation.
