# converged_docs

Translations of the Converged documentation.

The English sources live beside the code they describe, in `docs/` folders
across the [converged](https://github.com/solenopsys/converged) tree. This
repository holds every other language, produced by translation and mounted
there as `docs-cache/`.

```
<lang>/<section>/[<owner>/]<slug>.md    translated articles
<lang>/<section>/[<owner>/]index.json   translated index
<lang>/ecosystem/landing.json           translated landing copy
```

Kept out of the platform repository so machine-produced text does not churn its
history, and kept in version control rather than in `build/` because a
translation costs real work and must survive a clean checkout.

Which files are current is not guessed from timestamps. `core/tools/translation`
records the hash of the English text each translation was made from, so an
edited source marks its translations stale until they are redone — see
[`core/tools/translation/README.md`](https://github.com/solenopsys/converged/blob/master/core/tools/translation/README.md).
The durable ledger is `.index/index.sqlite`, a small SQLite database holding
the source-hash links, where every file sits (so one folder can be invalidated
on its own) and the statistics of past runs. It is committed for the same
reason the translations are: it is the only record of work already paid for.
Its `-wal`/`-shm` journal is not committed and never outlives a run. Reports
are build artefacts outside this repository.

Do not edit the English sources here; they are not here. Generation runs one
way, from sources into stores.
