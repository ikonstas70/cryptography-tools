# Cryptography Tools

**Author:** Ioannis Konstas — IT Solutions USA

> **Disclaimer:** All scripts and documents in this repository are provided strictly for **educational and research purposes**. They are intended to support learning, the study of cryptographic algorithms, and authorized academic research. Do not use these tools on systems, networks, or data you do not own or have explicit written permission to test. The author assumes no liability for unauthorized or unlawful use.

An open-source collection of cryptographic implementations and reference documents covering integer factorization, AES encryption, and the mathematical foundations underlying RSA security.

---

## `factoring/` — Integer Factorization Suite

A complete progression of integer factorization algorithms from Dixon's basic method through the Large Prime Quadratic Sieve variants to a CADO-NFS (General Number Field Sieve) workflow.

| Script | Description |
|---|---|
| `qs_dixon_educational.py` | Dixon's Method — simplest QS variant, two built-in test cases (N=8051, N=1,819,999), fully commented for learning |
| `quadratic_sieve_factorizer.py` | Basic Quadratic Sieve — auto-tuned factor base via L-notation heuristic, window search near √N, CLI interface |
| `qs_pipeline_factorizer.py` | QS pipeline pushing ~65-bit capability — symmetric ±k sieve, 80-relation buffer, bit-length safety limit |
| `lpqs_p1_factorizer.py` | Large Prime QS (P1) — accepts partial relations with one large prime L ≤ P_max; adds LP columns to GF(2) matrix |
| `lpqs_p2_framework_v1.py` | LPQS P2 v1 — working two-large-prime pipeline with dense GF(2) Gaussian elimination solver; test case N = 2,616,719 |
| `lpqs_p2_framework_v2.py` | LPQS P2 v2 — 250-bit architectural framework; dense GE fallback for small N, sparse Block Lanczos stub for 250-bit scale |
| `cado_nfs_factorizer.py` | CADO-NFS Python workflow — trivial cascade check, bit-length-aware parameter tuning, factor output parsing |
| `cado_nfs_params.conf` | CADO-NFS 3.0.0 configuration file — factor base, free relations, sieving, linear algebra, and square root settings |

**Algorithm progression:**
```
qs_dixon_educational       →  basic, educational, small N
quadratic_sieve_factorizer →  auto-tuned, CLI, ~50 bits
qs_pipeline_factorizer     →  larger buffer, ~65 bits
lpqs_p1_factorizer         →  +partial relations, more yield
lpqs_p2_framework_v1       →  +two large primes, working solver
lpqs_p2_framework_v2       →  250-bit architectural demo
cado_nfs_factorizer        →  GNFS via CADO-NFS, 100+ bits
```

---

## `encryption/` — Symmetric Encryption

| Script | Description |
|---|---|
| `aes_large_file_encryptor.py` | AES-256-CBC large file encryptor/decryptor — 1MB chunked I/O to handle files larger than RAM, elevated process priority via psutil, encryption speed reporting |

**Requirements:** `pip install pycryptodome psutil`

---

## `references/` — Technical Reference Documents

In-depth mathematical and research documents supporting the implementations in this repository.

| Document | Description |
|---|---|
| `aes_galois_fields_reference.md` | GF(2⁸) arithmetic in AES — irreducible polynomial, Extended Euclidean Algorithm for multiplicative inverses, worked example in GF(2³), connection to SubBytes and MixColumns |
| `factoring_algorithms_reference.md` | Factoring algorithm cascade — Pollard's Rho, ECM, QS, SNFS, GNFS, and Shor's quantum algorithm compared by complexity, use case, and RSA key size implications |
| `quadratic_sieve_reference.md` | Quadratic Sieve technical report — relation collection, GF(2) matrix construction, congruence of squares, strengths, limitations, and sub-exponential complexity analysis |
| `gnfs_energy_efficiency_review.md` | Expert review of energy-efficient GNFS for 830-bit RSA — Joules/relation benchmarking, polynomial selection leverage, sustainable HPC practices, and responsible disclosure |

---

*© Ioannis Konstas — IT Solutions USA*
