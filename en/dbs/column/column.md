# Stanchion

Stanchion adds columnar tables to SQLite. It is used when a Converged store
needs to read a small set of fields across many records: measurements, event
history, logs, and other append-oriented data. A normal SQLite table keeps a
row together; a Stanchion table keeps each column in its own segments, so a
query reads only the columns it mentions.

Stanchion is exposed through SQLite's virtual-table interface. A table is
declared with `USING stanchion` and a `SORT KEY`; the sort key defines the
physical order of records and lets the extension skip row groups that cannot
match a predicate. Values are buffered as pending inserts, then written into
column segments using the encodings selected by the extension.

The wrapper builds the extension for the native SQLite runtime. Stanchion is
still alpha software: its on-disk format and supported table operations are
not yet fixed.
