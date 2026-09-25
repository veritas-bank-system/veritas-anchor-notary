# Veritas daily anchor notary mirror

Public tamper-evidence mirror for the Veritas Anchored Evidence (VAE) pipeline.

Each row is the **Merkle root of one day's anchor canopy** — the SHA-256 root
over that day's hashed evidence digests (audit batches, erasure ceremonies,
control artifacts). The root is all that is published: no contents, no record
digests, nothing confidential — by construction.

## What this proves

A root existing here (with git commit timestamps as the notary clock) proves
the corresponding day-root was *computed and held* at that time. Combined with
the private record + Merkle proof, anyone can verify a specific record was
included in that day's canopy — the record cannot be retroactively altered
without changing the root, and the root cannot be changed without it
differing from the one notarized here.

## How to verify (auditor path)

1. Obtain from Veritas: the day's **record set** and a **Merkle inclusion
   proof** for the record you care about (`verify-day` tooling, root below).
2. Re-derive the root from the records: leaves are `SHA256(0x00 || digest)`,
   tree is a standard binary Merkle tree.
3. Compare with the row for that date in this mirror. Equal = the record set
   is exactly what was anchored that day.

## Daily roots

| date (UTC) | root (SHA-256, hex) |
|---|---|
| 2026-09-25 | `fe008cdfa5b3eb6a51ccb200ce43ce24d098d1ae11abe7acdf9498a63cb5613e` |

_Last publish: 2026-09-25T01:16:51Z — 1 day roots._
