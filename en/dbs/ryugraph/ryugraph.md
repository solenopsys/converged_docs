# RyuGraph

RyuGraph provides the graph store for data whose meaning is carried by the
connections between records: dependencies, ownership, topology, lineage, and
similar relationship-heavy models. It is an embedded property-graph engine
with Cypher queries, so a traversal and the joins it requires run in the
native process instead of being rebuilt in application code.

The engine stores graph data on disk and executes analytical graph queries
with columnar storage, compressed adjacency structures, and vectorised query
processing. Converged uses the wrapper to make that engine available as a
native shared library alongside its other storage components.

The build intentionally omits upstream language bindings, examples, shell,
and benchmark targets. The resulting artifact contains the graph engine and
the ABI required by the platform.
