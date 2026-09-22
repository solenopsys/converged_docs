# Valkey

Valkey supplies an in-memory key-value service to Converged. It is used for
data that benefits from Valkey commands and expiry semantics: cached values,
counters, short-lived coordination state, and other shared values that must be
read or changed quickly.

The wrapper compiles the vendored server into a native library and starts it in
its own thread. The server listens on the configured local address and port;
the wrapper then talks to it through libvalkey. Its C API starts and stops the
server, checks readiness, reports memory use, and executes the supported
key-value operations.

This embedded configuration disables snapshots and AOF, uses a single logical
database, and applies the `allkeys-lru` eviction policy within the configured
memory limit. Those settings make the lifecycle explicit instead of inheriting
an external Valkey installation.
