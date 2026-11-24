# Evaluating Evidence Representations for AI-Based Ethereum Smart Contract Vulnerability Analysis

This repository accompanies a KTH master's thesis on how three AI models analyse 20 historical Ethereum smart-contract exploits under five evidence conditions. The study evaluates 300 responses for vulnerability classification, root-cause explanation, and evidence localisation.

## Thesis results

The models correctly classified **179 of 300 responses (59.7%)** under the corrected MetaPool reference label. Among those 179 responses, **157 (87.7%)** received full credit for both root-cause explanation and applicable evidence localisation. For the combined source-and-trace conditions, this localisation measure uses the source-localisation score.

The correction changes the reference class for MetaPool (`case_09`) from Improper Input Validation to Business Logic Flaw. Seven existing responses receive classification credit under the corrected label. Both analyses use the same 300 responses and the same researcher-assigned root-cause and localisation scores.

## Research archive

Download the research archive from the [v0.1.0 release](https://github.com/Tedabayo/vlm-smart-contract-trace-replication/releases/tag/v0.1.0-results-audit). The ZIP contains a partial replication and results-audit package.

- **Experimental evidence.** The archive contains 100 case-and-condition prompts, 20 distinct Perfetto visualisations, and 20 distinct structured-text traces. The combined conditions reuse the corresponding trace files.
- **Provenance.** The archive includes public-chain transaction identifiers for all 20 incidents, source-selection notes, retrieval guidance, and SHA-256 records for 270 withheld source-excerpt positions.
- **Responses and scoring.** The archive contains 300 model-response records and 41 original scoring files. The researcher scored the original responses. The public copies of 100 responses contain redactions.
- **Verification.** The package includes a checksum manifest, input-coverage checks, an offline aggregation script, historical preparation scripts, and documentation of the publication review and methodological limitations.

## Offline verification

Download and extract the v0.1.0 research archive. Run the commands below from the extracted directory containing `reproduce_aggregates.py` and the `scoring/` folder.

### Reproduce the thesis result (179/300)

Run the following command with Python 3 in a Bash-compatible shell. It first runs the archive's original consistency checks, then applies the corrected MetaPool label in memory. It prints each classification that changes and the two corrected totals. The archived files remain unchanged.

```sh
python3 - <<'PY'
import runpy

audit = runpy.run_path("reproduce_aggregates.py")
correct = set()

for row in audit["cls"]:
    key = (row["case"], row["condition"], row["model"])
    is_correct = row["correct"]

    if row["case"] == "case_09":
        is_correct = row["stated"] == "Business Logic Flaw"
        if is_correct != row["correct"]:
            print("Changed classification:", *key)

    if is_correct:
        correct.add(key)

full_credit = sum(
    (row["case"], row["condition"], row["model"]) in correct
    and row["root_cause"] == "2/2"
    and row["localisation"] == "2/2"
    for row in audit["reason"]
)

assert (len(correct), full_credit) == (179, 157)
print(f"Corrected classifications: {len(correct)}/300")
print(f"Full credit on both measures: {full_credit}/{len(correct)}")
PY
```

Expected final output:

```text
Corrected classifications: 179/300
Full credit on both measures: 157/179
```

### Verify the original v0.1.0 results (172/300)

To check the frozen files, input coverage, and original scoring totals separately, run:

```sh
python3 verify_package.py
python3 verify_input_coverage.py
python3 reproduce_aggregates.py
```

The original aggregation script uses the earlier MetaPool label. It reproduces **172/300** correct classifications, of which **151/172** received full credit for both root-cause explanation and applicable evidence localisation.

## Scope and limitations

The archive supports inspection of the included traces, file-integrity checks, and verification of aggregate results from the recorded scores. Complete independent reproduction of all commercial model requests is limited by withheld third-party Solidity/Vyper source excerpts, redactions in public response copies, and incomplete per-request invocation metadata. The original GPT and Claude collection runners are unavailable. The aggregate checks reproduce the researcher's recorded judgments and do not independently re-score the responses.

The researcher identified Alchemy Ethereum Mainnet as the RPC provider used with Foundry Anvil for transaction reconstruction, based on locally reviewed shell history. The archive contains no credentials. This attribution does not establish redistribution rights for third-party data.

No blanket licence is asserted for third-party source material, blockchain-derived material, or model-generated content. See `PUBLICATION_REVIEW.md`, `REPLICATION_SCOPE.md`, and `KNOWN_LIMITATIONS.md` in the archive for screening findings, attribution, and study limitations.
