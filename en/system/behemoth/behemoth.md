# Behemoth storage

Behemoth is the native storage foundation of Converged. It provides several
data models through one compact runtime while preserving a separate physical
storage boundary for every microservice.

## Storage for modular services

Each domain service owns its data. It does not share tables or indexes with
unrelated services, and it does not need to operate a separate database stack.
Behemoth serves the isolated roots from a common native process and routes each
request to the correct store.

```text
orders service  -> orders volume  -> SQL and files
calls service   -> calls volume   -> key-value and audio fragments
search service  -> search volume  -> vector index
```

The separation is physical rather than a naming convention. If a service root
is not mounted and declared, Behemoth refuses to create its store. A deployment
mistake therefore becomes visible immediately instead of writing data into a
temporary container filesystem.

## Multiple data models

Different workloads need different structures. Behemoth combines relational,
key-value, column, vector, graph and file storage behind the same runtime
boundary. A service chooses the store that fits its data without adding a new
external database product to the platform.

The engines remain specialized internally. The unified layer is responsible
for lifecycle, isolation, transport and metadata, not for pretending that all
data models behave the same way.

## Placement and scaling

Storage placement is independent from application code. One edge installation
may use a single Behemoth process. Larger deployments can divide scopes between
several instances, while a cloud profile can give every tenant its own storage
instance.

Each microservice keeps its own volume in every profile. Moving a scope or a
service to another Behemoth instance changes deployment configuration, while
callers continue to use the same logical storage identity.

## Failure and recovery boundaries

Small service-owned stores reduce the impact of corruption, migration and
backup operations. A problem in one store does not require restoring a shared
database for the whole platform. Dumps and recovery can be handled for the
affected service boundary, and unrelated services continue to operate.

## Place in the system

Storage requests reach Behemoth through Fujin like requests to any other
runtime peer. Ptah provides the volume layout and mount configuration.
Behemoth executes storage operations but does not coordinate business
workflows, select tenants or define which services a solution contains.
