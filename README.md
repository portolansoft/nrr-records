# Portolan NRR records

Published Negative-Results Records (NRR v0.2) produced by the [Portolan NRR pipeline](https://github.com/portolansoft/nrr).
One folder per study. Each folder holds the canonical JSON records, one RO-Crate per record, the MCP deposit payload per
record, a manifest, and a collection-level `ro-crate-metadata.json`.

| study | source | records | licence of the records |
|---|---|---|---|
| `arcadia-alcalase/` | Caddell, D., Futia, R., Kraemer, J. A. et al. (2026). *Evaluation of Alcalase pretreatment for Chlamydomonas reinhardtii CRISPR knock-in*. The Stacks (Astera Institute). https://doi.org/10.57844/arcadia-pdu7-q2zz (CC BY 4.0). Data: Arcadia Science (2026), Zenodo, https://doi.org/10.5281/zenodo.22238548 (CC BY 4.0). | 1 path + 6 attempts, 11 findings | CC BY 4.0 |

Records derived from sources whose licence does not permit redistribution of adapted material (for example CC BY-NC-ND)
are not published here; the converter that produces them is open so they can be rebuilt locally from the sources.

## Attribution

Every record carries its sources (`sources[]`) with the DOI and licence of the publication and dataset it is derived
from, the location in the source of every value (`evidence[].locator`), and marks values computed by the pipeline
(`derivedBy: portolan-ingest`). When you reuse these records, cite the original study and dataset as above, and this
repository.

## Structure

```
<study>/records/<slug>.json            canonical record (validates against schema/nrr-0.2.schema.json in portolansoft/nrr)
<study>/crates/<slug>/ro-crate-metadata.json   RO-Crate 1.2 detached crate (schema.org + PROV, nrr: namespace)
<study>/deposits/<slug>.json           the nrr_deposit call a client would send to the Portolan MCP server
<study>/manifest.json                  record list, generating commit, source publication
<study>/ro-crate-metadata.json         collection crate listing the records
```

## How they were made

`uv run python scripts/export_records.py --study arcadia-alcalase --dest ../nrr-records` in the pipeline repository, at the
commit named in each `manifest.json`. All statistics are the authors'. Derived values (means, a rule-of-three detection
limit) are labelled. Judgement calls made during curation are recorded in each record's `provenanceNotes`.
