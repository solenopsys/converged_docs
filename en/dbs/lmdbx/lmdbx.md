# LMDBX

LMDBX is the ordered key-value store used where Converged needs direct access
to bytes rather than SQL. The wrapper opens an environment on disk and exposes
put, get, delete, transactions, and cursors through Zig and C APIs. Cursors
make range scans and ordered iteration part of the same storage primitive as
point lookups.

libmdbx stores its B+ trees in memory-mapped files and uses MVCC for readers.
Read transactions see a stable snapshot while a writer commits changes. That
model suits indexes and service state that are read frequently and updated in
short transactions.

The wrapper statically links libmdbx and produces native shared libraries for
the supported targets. It is the FFI layer around the engine, not a separate
database process.
