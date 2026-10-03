# Portolan NRR records

Published Negative-Results Records (NRR v0.2) produced by the [Portolan NRR pipeline](https://github.com/portolansoft/nrr).
One folder per study. Each folder holds the canonical JSON records, one RO-Crate per record, the MCP deposit payload per
record, a manifest, and a collection-level `ro-crate-metadata.json`.

| study | source | records | licence of the records |
|---|---|---|---|
| `acs-zeolite/` | Altundal, O. F., Galvez-Llompart, M., Cantin, A. et al. (2025). *Lessons from Failed Attempts of Computationally Guided Synthesis of Aluminosilicate STF and IFR Zeolites in Hydroxide Media*. Chemistry of Materials 37(24), 9689-9702. https://doi.org/10.1021/acs.chemmater.5c01751 (CC BY 4.0; full text via Europe PMC PMC12747119). | 1 path + 4 attempts, 16 findings | CC BY 4.0 |
| `acs-laccase/` | Steffens, S. D., Antell, E. H., Cook, E. K., Rao, G., Britt, R. D., Sedlak, D. L., Alvarez-Cohen, L. (2023). *An Artifact of Perfluoroalkyl Acid (PFAA) Removal Attributed to Sorption Processes in a Laccase Mediator System*. Environmental Science & Technology Letters 10(4), 337-342. https://doi.org/10.1021/acs.estlett.3c00173 (CC BY 4.0; full text via Europe PMC PMC10100556). | 1 path + 4 attempts, 11 findings | CC BY 4.0 |
| `acs-tmeda/` | Macleod, J., Bage, A. D., Meyer, L. M., Thomas, S. P. (2024). *Hidden Boron Catalysis: A Cautionary Tale on TMEDA Inhibition*. Organic Letters 26(44), 9564-9567. https://doi.org/10.1021/acs.orglett.4c03591 (CC BY 4.0; full text via Europe PMC PMC11555781). | 1 path + 4 attempts, 20 findings | CC BY 4.0 |
| `arcadia-alcalase/` | Caddell, D., Futia, R., Kraemer, J. A. et al. (2026). *Evaluation of Alcalase pretreatment for Chlamydomonas reinhardtii CRISPR knock-in*. The Stacks (Astera Institute). https://doi.org/10.57844/arcadia-pdu7-q2zz (CC BY 4.0). Data: Arcadia Science (2026), Zenodo, https://doi.org/10.5281/zenodo.22238548 (CC BY 4.0). | 1 path + 6 attempts, 11 findings | CC BY 4.0 |
| `arcadia-dfa/` | Morin, M., Patton, A. H. et al. (2024). *A structurally divergent actin conserved in fungi has no association with specific traits*. The Stacks (Astera Institute). https://doi.org/10.57844/arcadia-9768-f6c5 (CC BY 4.0). Data: Arcadia Science (2023), Zenodo, https://doi.org/10.5281/zenodo.10211653 (CC BY 4.0). Code: https://doi.org/10.5281/zenodo.10779267. | 1 path + 3 attempts, 11 findings | CC BY 4.0 |
| `arcadia-raman/` | Cheveralls, K. et al. (2026). *Leave-one-batch-out cross-validation reveals strong batch effects in Raman spectroscopy of yeast cultures*. The Stacks (Astera Institute). https://doi.org/10.57844/arcadia-xdmk-yq0w (CC BY 4.0). Code and data: Arcadia Science (2026), Zenodo, https://doi.org/10.5281/zenodo.19226627 (MIT). | 1 path + 3 attempts, 8 findings | CC BY 4.0 |
| `arcadia-neuroimaging/` | Kolb, I., Reitman, M. E., Lane, R. et al. (2024). *Label-free neuroimaging in mice captures sensory activity in response to tactile stimuli and acute pain*. The Stacks (Astera Institute). https://doi.org/10.57844/arcadia-b963-15ac (CC BY 4.0). Data: Arcadia Science (2024), Zenodo, https://doi.org/10.5281/zenodo.11585535 (CC BY 4.0). Code: https://doi.org/10.5281/zenodo.12770054. | 1 path + 3 attempts, 9 findings | CC BY 4.0 |

Records derived from sources whose licence does not permit redistribution of adapted material (for example CC BY-NC-ND)
are not published here; the converter that produces them is open so they can be rebuilt locally from the sources.

## Why these studies

Each was chosen to test a different part of the profile.

- **Alcalase** was the first study encoded, and its central negative has no positive control at all.
- **Neuroimaging** has a positive control that *passed* and a negative control that did not stay clean, which is a
  different way for a negative to fall short of evidence of absence.
- **Raman** is purely computational and its controls are not reagents: the positive control is a different prediction task
  on the same data, and the negative control is adversarial, predicting a label that should carry no signal. It also
  contains a claim whose sign flips with the validation scheme alone, MCC 0.79 under standard cross-validation and 0.32
  when whole experimental replicates are held out.
- **Divergent fungal actin** was encoded as a pre-registered test of whether the schema had stopped changing. It is
  comparative genomics across a kingdom with no experiment at all, species as the unit of observation, and evidence by
  evolutionary model selection. It required two vocabulary terms and nothing structural.
- **Zeolite STF and IFR** is the first chemistry and materials study: a computational pipeline over more than 10,000
  organic structure-directing agents whose three shortlisted candidates all failed at the bench. Its predictions are
  recorded as `refuted` and its syntheses as `inconclusive-no-positive-control`, with the link between the two kept. It
  required one vocabulary term (`material`).
- **TMEDA inhibition** is a negative about a control method: the standard test for hidden boron catalysis gives false
  negatives above 60 °C. The test itself is an entity of type `assay` and the target of a `refuted` finding; the kinetic
  negatives at 60 °C are the first chemistry findings to pass the informativeness rule. It required no schema change.
- **Laccase and PFAS** is a replication failure with the artefact explained: a surrogate substrate (carbamazepine) as the
  positive control makes the two-week PFOA result the corpus's first informative `negative-not-replicated`, and the
  apparent 64 to 67 % losses are `refuted` by mass balance. It required one vocabulary term (`measurement-artifact`).

Together with the fourth study in the pipeline repository, every clause of the informativeness rule has now fired on real
published data, each traceable to a different study. That is what shows the rule working as a diagnosis rather than as a
blanket refusal. See `docs/case-study-neuroimaging.md` and `docs/case-study-raman.md` in
[portolansoft/nrr](https://github.com/portolansoft/nrr).

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
