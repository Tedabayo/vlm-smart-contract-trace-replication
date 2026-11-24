# Evaluating Evidence Representations for AI-Based Ethereum Smart Contract Vulnerability Analysis

This repository is being prepared to host supplementary research materials for the master's thesis *Evaluating Evidence Representations for AI-Based Ethereum Smart Contract Vulnerability Analysis*.

The study evaluates 20 historical Ethereum exploit incidents, three AI models, five evidence conditions, and 300 archived model responses.

## Publication status

**Not yet published.** The available public-release working copy is a **limited results-audit candidate**, pending a final disclosure and rights review. No downloadable research archive has been released here yet.

## Scope of the planned limited archive

The candidate contains:

- 300 saved response records; **100 public-copy responses have code/example blocks redacted**, while 200 remain unchanged.
- The researcher's original scoring files and written evaluation notes.
- A case index, a response-redaction/hash record, checksum verification, and an offline script that recalculates the reported aggregate results.

The scoring data reproduces **172/300** correct vulnerability classifications and **151/172** full-credit root-cause and applicable localisation results among correctly classified responses. These are the researcher's recorded assessments, not independent re-adjudication.

## Reproducibility limits

**This is not a complete experiment-replay package.** It excludes original third-party Solidity/Vyper sources, execution-trace evidence, experimental inputs, and model credentials. Some model responses are modified for the proposed public copy, so the package cannot support a complete rerun of the model queries or fully independent reassessment of every original answer. Scoring was performed on the original unredacted responses.

The original private research archive is retained separately. Publication of the limited package remains subject to final checks for model-output redistribution, third-party rights, and sensitive information.

## Citation and rights

A versioned GitHub Release and citation information will be added only after the publication review is complete. No blanket licence is asserted for third-party source code, blockchain data, or model-generated content.
