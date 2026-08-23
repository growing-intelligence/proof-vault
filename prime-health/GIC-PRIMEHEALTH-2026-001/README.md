# GIC-PRIMEHEALTH-2026-001 — Prime-Health

Ed25519-signed GI Certificate of Model Health.

| field | value |
|---|---|
| certificate | `GIC-PRIMEHEALTH-2026-001` |
| issued | 2026-08-23T13:48:29Z |
| before | 683 / 2430 (28.11%) |
| after | 1036 (42.63%) |
| improvement | +14.53 points |
| collateral | 0 |
| public key | `FtrWshUc/9rg5Cz+ARi5DP/yyqFhWMJLmx0VHKc3wpk=` |
| canonical sha256 | `3fcb023ff3375a74548d7eab369f7223dc20ad20bbc6d514aa3ebb97c4674967` |
| merkle root | `f4bb19d0aaba7504f84055cbcd6a6b30c07fe1a82097638caa5dc9bc5d713cc6` |

## Verify

1. Download `GIC-Prime-Health-certificate.json`.
2. Remove `founder_signature_ed25519_b64`, `build_signature_ed25519_b64` and `canonical_sha256`.
3. Serialise with sorted keys, compact separators, ASCII — that is the canonical form.
4. Verify the Ed25519 signature over those bytes against the public key above.
