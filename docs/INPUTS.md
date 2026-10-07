# Required local inputs

These inputs remain outside GitHub. No CSV, raw network record, membership manifest,
reserved dataset, fitted model or original evidence ZIP is distributed by this repository.

## Original CSV

Place the supplied original uncompressed `data_4.csv` in `data/` or change DATASET_PATH.
Experiment 4 requires dataset SHA256:

`7287a4d7740a1dddbf330ceb2beb6a4889d33ba63674558a68b5eb50d16711df`

This file had 7,948,748 rows and 84 columns. These counts describe one local CSV,
not the entire multi-day dataset. The notebooks retain the port and label filters.

## Completed Experiments 1–3 evidence ZIP

Experiment 4 expects one `*/frozen_inputs.npz` inside EVIDENCE_ZIP plus
`dataset_audit.json`, `experiment_settings.json` and `split_membership.csv` under
the same prefix. A manifest is checked if present. The original missing-manifest
limitation remains recorded. Model files in the ZIP are not loaded.

The frozen training/development input digest must be:

`cdc4661d5114c0bf2bd4f253b1da24836a8c0918b2eee360fcf0f22f7a353faf`

A later rerun does not automatically reproduce all historical membership or exposure.
Do not replace identity assertions simply to let a different input file pass.

## Historical membership root

HISTORY_ROOT must contain:

- `option-b/selected_rows_metadata.csv`
- `option-c/validation_metadata.csv`
- `matched-source-comparison/matched_rows.csv`
- Ten `option-c/train_*_row_ids.csv` manifests: five 2,000-row and five 4,000-row
  historical training manifests.
- `option-c/reserved_test_row_ids.csv` with the previously recorded 50,001 reserved IDs.

Membership CSVs require `original_row_id` or `csv_row_id`. Add any additional known
exposure manifests to EXTRA_HISTORY_FILES before execution. Unknown historical
exposure cannot be certified. The reserve is used for exclusion, not scoring.

The main enhancement notebook also supports an optional PROTECTED_RESERVE_PATH CSV
with `csv_row_id` and optionally `Flow_ID`. Without it, its reserve exposure is not verified.

## Outputs

Each notebook writes a new run folder. Preserve these evidence files separately.
Do not commit generated raw membership, arrays or fitted models accidentally.
