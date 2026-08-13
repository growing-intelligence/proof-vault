# HOLO-008-BIO — Holosynthics Biological Data Proof

**Status:** PROVEN · **Date:** 2026-07-13 · **Ed25519-signed** (block below)
**Scope:** four biological data formats decompose into the same 8-type × 7-law periodic table as text, code, image, audio, PDF, HTTP, and LiDAR.

---

## 1. Result

Four new adapters — `bio.fasta`, `bio.pdb`, `bio.clinical`, `bio.fastq` — decompose real, publicly-cited biological datasets (NCBI, RCSB, EBI, METABRIC) into the same irreducible atoms as every other domain. Every atom carries a specific **element** (Type × Law); zero atoms are unclassified across all four files. Cross-domain: **"BRCA1" resolves to the same element in FASTA, PDB, and clinical CSV.**

This extends the proven set to **10 independent formats** (the seven-domain "car" proof + three biological formats sharing "BRCA1").

## 2. The seven laws — one law, three names

This is the proof of universality: the same law, expressed in the universal, code, and biological registers.

| # | Holosynthics (Science) | Code (Internal) | Biology (Derivative) |
|---|------------------------|-----------------|----------------------|
| 1 | Conservation of Proof  | Conservation    | Sequence Fidelity        |
| 2 | Irreducibility         | Distinction     | Base Atomicity           |
| 3 | Selective Expression   | Criticality     | Gene Expression          |
| 4 | Contextual Resonance   | Feedback        | Codon Context            |
| 5 | Composition            | Composition     | Molecular Assembly       |
| 6 | Inheritance            | Network         | Genetic Inheritance      |
| 7 | Convergence            | Complexity      | Evolutionary Convergence |

The 8 **Types** (unchanged across all domains): Boolean, Number, Symbol, Identity, Space, Time, Relation, Entropy. 56 elements = 8 Types × 7 Laws.

## 3. Per-adapter results (real numbers, W3 test suite 45/45)

| Adapter | Dataset | Atoms | Key counts | Molecule | Round-trip |
|---|---|--:|---|---|---|
| **bio.fasta** | BRCA1 mRNA (NCBI U14680.1) | 7,630 | 5,711 bp · GC 41.55% | Symbol ⊗ Space ⊗ Identity | byte-exact hash match |
| **bio.pdb** | BRCA1/BARD1 RING (RCSB 1JM7) | 575,898 | 44,268 ATOM records · 14 NMR models · chains A/B · B-factor 0.0 | Number ⊗ Space³ ⊗ Symbol ⊗ Identity | byte-exact, full file |
| **bio.fastq** | Zaire ebolavirus RNA-seq (SRR1553607) | 118 (summary mode) | 203,445 reads | Symbol ⊗ Space ⊗ Entropy ⊗ Identity | gzip verified |
| **bio.clinical** | METABRIC breast cancer | 6,612 | 1,904 patients · 693 features | Number ⊗ Boolean ⊗ Identity ⊗ Symbol | tabular |

- **Element field: zero `None` across all four files** — every atom carries a specific element.
- `bio.fastq` runs in **summary mode** (118 aggregate atoms over 203,445 reads) — a deliberate design choice, not per-read enumeration.

## 4. Element distribution — honest

The law axis is exercised **narrowly**, not fully, on these four files: FASTA's Symbol atoms span 2 laws, PDB's Symbol atoms span 3, and FASTQ/clinical use 1 law per kind. So a subset of the 56 elements is populated — **the proof is that biology lands on the table, not that every one of the 56 cells is filled by four files.** A broader corpus would populate more cells; that is future work, stated plainly rather than overclaimed.

## 5. Cross-domain identity — "BRCA1"

"BRCA1" decomposes to the identical element in three independent biological formats:

| Format | Where "BRCA1" appears | Element |
|---|---|---|
| FASTA | gene name in the header | **Identity · Conservation of Proof** (bio: Sequence Fidelity) |
| PDB (1JM7) | protein name in TITLE/COMPND | **Identity · Conservation of Proof** |
| Clinical CSV | `brca1` / `brca1_mut` columns | **Identity · Conservation of Proof** |

Same Type (Identity), same Law (Conservation of Proof / code: Conservation), across three scientific contexts. Combined with the existing seven-domain proof where "car" resolves to the same Identity across text, code, image, audio, PDF, HTTP, and LiDAR → **ten independent formats, one table.**

## 6. Two honest findings (spec vs. reality)

1. `brca1` + `brca1_mut` decompose to **one** Identity atom for "BRCA1", not two — the gene identity is singular regardless of how many columns reference it.
2. `overall_survival` is **Symbol + Number + Relation**, not Boolean — a survival outcome carries a censoring status (Symbol), a time (Number), and a patient linkage (Relation), which is richer than a yes/no.

These are reported as-is; the adapters emit what the data actually is.

## 7. Audit (this proof is code-verified, not asserted)

- `cargo test -p gi-decomposition`: **166 passed, 0 failed** (incl. W3's 45 HOLO-008 tests + the 6 existing adapters' round-trips).
- `cargo clippy -p gi-decomposition --all-targets -- -D warnings`: **clean**.
- Six existing adapters (text, code, image, audio, PDF, HTTP): **zero regression** from the shared `GiAtom.element` field addition; all round-trips still hash-match.
- Branch: `w1/holo008-integration` = `w2/holo008-bio` (`2593495f`, adapters + clippy fix) + W3 tests (`5c9738f6`).

## 8. Ed25519 signature

```
alg:            Ed25519
signed_over:    sha256(canonical proof JSON), raw 32 bytes
content_sha256: 295d840d396938f4c0794acec60c896036ab8f5150a635e1e80084c9a9408f8a
sig_hex:        1fae3a3ac5d98fd072cde3d1a8d553fb… (full in HOLO-008-BIO-PROOF.json)
engine_pubkey:  afb3d04e5c86dabfc0efa1dbdeb3a919821503dcf5a1ee6bc27a20115574e208
```
Verify: recompute `sha256(canonical JSON)` → check `sig_hex` against `engine_pubkey`. Signed artifact: `HOLO-008-BIO-PROOF.json`.

## 9. Reproducibility

Data (public): NCBI U14680.1, RCSB 1JM7, EBI/NCBI SRR1553607, METABRIC. Build + test on `w1/holo008-integration`; `cargo test -p gi-decomposition` reproduces every number above.
