# Evaluating Evidence Representations for AI-Based Ethereum Smart Contract Vulnerability Analysis

Supplementary research materials accompanying a KTH master's thesis examining AI-assisted vulnerability analysis of 20 historical Ethereum smart-contract exploits using three models and five evidence conditions.

## Research archive

**[GitHub Releases](https://github.com/Tedabayo/vlm-smart-contract-trace-replication/releases)** hosts any published, versioned research archive. A saved *draft* release is not publicly accessible.

The v0.1.0 archive is a **partial replication and results-audit package**:

- **Experimental evidence:** 100 original condition/case prompts, 20 distinct Perfetto visualisations and 20 distinct structured-text traces, repeated as appropriate across B/C conditions (40 image positions and 40 text-trace positions).
- **Provenance:** public-chain transaction identifiers for all 20 incidents, source-selection notes and retrieval guidance, SHA-256 records for 270 withheld original source-excerpt positions, and an Alchemy Ethereum Mainnet/Foundry Anvil trace-reconstruction description.
- **Responses and assessment:** 300 model-response records, with 100 public-copy redactions; the researcher's 41 original scoring files, unchanged. Scores were assigned to the **original unredacted** responses.
- **Verification:** frozen-file checksum manifest, input-coverage verification, offline score aggregation, historical preparation scripts, publication-screening notes and methodological limitations.

The preserved scoring records reproduce **172/300** correct classifications and **151/172** full-credit root-cause and applicable localisation assessments among correctly classified responses. These represent the researcher's recorded judgments, not independent re-adjudication.

## Scope and limitations

The archive **does not permit complete independent reproduction** of all commercial model requests. Original third-party Solidity/Vyper source excerpts are withheld, some public response copies are redacted, and complete per-request model invocation metadata and original GPT/Claude collection runners are unavailable. The package supports inspection of the included traces, file-integrity checks, and auditing the reported aggregate results, with the limitations documented in the ZIP.

The researcher identifies **Alchemy Ethereum Mainnet** as the RPC provider for Foundry Anvil transaction reconstruction, based on their locally reviewed shell history. No credentials are included. This attribution does not establish general redistribution rights in third-party data.

## Offline verification

After downloading and extracting a published ZIP, run these commands at its root:

```sh
python3 verify_package.py
python3 verify_input_coverage.py
python3 reproduce_aggregates.py
```

No blanket licence is asserted for third-party source material, blockchain-derived material, or model-generated content. See the archive's `PUBLICATION_REVIEW.md`, `REPLICATION_SCOPE.md`, and `KNOWN_LIMITATIONS.md` for screening findings, attribution and study limitations.
