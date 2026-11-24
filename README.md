# Evaluating Evidence Representations for AI-Based Ethereum Smart Contract Vulnerability Analysis

Supplementary research materials for a KTH master's thesis investigating AI-based vulnerability analysis across five evidence conditions for 20 historical Ethereum exploits. The study records 300 responses from three AI models.

## Publication status

**The replication archive has not yet been published.** A draft GitHub Release contains an expanded, partially redacted research archive, pending final rights and privacy review. Until publication, the repository alone does not provide a downloadable public replication package.

## Contents of the draft archive

- **Experimental evidence:** 100 original condition/case prompts; 20 distinct Perfetto visualisations and 20 distinct structured-text traces (40 copies of each format across their B and C conditions). Original source-code excerpts are withheld.
- **Source provenance:** original transaction references for 20 incidents, a source-retrieval guide, and SHA-256 records for 270 withheld source-file positions (including copies across conditions).
- **Responses and scores:** 300 response records, of which 100 are redacted public copies and 200 are unchanged; the author's original scoring records and notes are preserved. Scores refer to the original, unredacted responses.
- **Verification and methods:** historical preparation and trace-reconstruction scripts; file-integrity, input-coverage, and aggregate-score verification scripts; methodological limitations and redaction records.

The archived scoring records reproduce **172/300** correct vulnerability classifications and **151/172** full-credit root-cause and applicable evidence-localisation assessments among the correctly classified responses. These are the researcher's assessments, not independent re-adjudications.

## Reproducibility limits

This is a **partial replication and results-audit archive**, not a complete experiment-replay package. It excludes third-party Solidity/Vyper source excerpts, includes redactions in 100 responses, and does not preserve complete per-request model invocation metadata. As a result, it supports inspection of trace representations, verification of the archived scoring aggregates, and partial reconstruction of experimental conditions, **not** complete independent replay of all model requests or reassessment of every original answer.

The historical Ethereum RPC provider was **Alchemy Ethereum Mainnet**, as reported from the researcher's local shell-history review. Foundry Anvil was used to fork and reconstruct the transactions before producing the trace representations. The public candidate includes `RPC_PROVENANCE.md` explaining the supporting evidence and its limits; credentials are excluded.

## Verification

When the archive is released, extract it and run the following commands from its root:

```sh
python3 verify_package.py
python3 verify_input_coverage.py
python3 reproduce_aggregates.py
```

The current candidate passes the file-integrity, evidence-coverage, and aggregate-score checks. Technical validation does not establish third-party redistribution permissions or full experimental reproducibility.

## Citation and rights

A versioned public release URL and citation details will be supplied once the disclosure review is complete. No blanket licence is asserted for third-party source material, blockchain data, or model-generated content.
