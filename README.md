# proof-vault

Public transparency vault for **Growing Intelligence** model certificates.

Every certificate here states measured results and is signed with Ed25519. Anyone can verify a
certificate offline, without contacting us and without trusting this page.

## Certificates

| certificate | model | measured |
|---|---|---|
| [`certificates/prime-56`](certificates/prime-56) | Prime-56 | GIC-PRIME56-2026-001 |
| [`prime-health/GIC-PRIMEHEALTH-2026-001`](prime-health/GIC-PRIMEHEALTH-2026-001) | Prime-Health | 28.11% → 42.63% on 2,430 held-out Hebrew questions, zero regressions |
| [`counterfact/GIC-COUNTERFACT-2026-001`](counterfact/GIC-COUNTERFACT-2026-001) | Probe56 on Llama-3.1-8B (CounterFact 1,000 edits vs ROME / MEMIT / AlphaEdit) | 841 / 1,000 edits, 0 / 492 nearby facts broken, held-out identical to the unmodified model |

## How to verify a certificate

1. Download the certificate's `.json` file.
2. Remove the three signature fields: `founder_signature_ed25519_b64`,
   `build_signature_ed25519_b64` and `canonical_sha256`.
3. Serialise what remains with sorted keys, compact separators and ASCII escaping. Those bytes
   are the canonical form.
4. Verify the Ed25519 signature over those bytes against the public key printed in the
   certificate.

The CounterFact certificate is at revision 2; revision 1 (commit 841e242) is superseded and its signature is void — it is kept under `superseded/` for the record.

The CounterFact certificate uses a single `signature` block: remove `signature` and `self_sha256`, serialise the rest with sorted keys and compact separators, and verify against the public key inside the block (the same Founder key).

The certificate also carries a Merkle root over the hashes of the evidence files behind the
measurement, so a claimed result can be tied to the exact artefacts it was measured from.

## What is published here

Results: scores, before and after, question counts, regression counts, hashes, signatures.

Nothing else. How the models are built and repaired is not published — that technology is
protected by provisional patents filed with the USPTO.

## Contact

Growing Intelligence — for certificate questions or an independent verification walkthrough,
contact us through the address on the certificate.
