# SOFSEM 2027 e-scooter research artifact

Source, measurements, and reproducible analysis for **Quantifying Coordination
Overhead and Saturation in Spring Modulith and Microservice Architectures**,
by Piotr Gaska and Filip Kruzel.

## Download

Use the [versioned release](https://github.com/fkruzel/sofsem2027-e-scooter-artifact/releases/tag/v1.0.0) and download
[SOFSEM2027_evidence.zip](https://raw.githubusercontent.com/fkruzel/sofsem2027-e-scooter-artifact/v1.0.0/SOFSEM2027_evidence.zip).
The release is public and requires no GitHub login.

The package includes 400 k6 reports (275 startRide and 125 finishRide runs),
1,855,717 detailed propagation records, container and host telemetry, the full
experiment source snapshot, and the scripts and computed tables used in the paper.
The development repository requires authorization; access to it is not needed
because the source snapshot is included in the archive.

The ZIP's SHA-256 is `d82aeb61819dac4ad061118e8f24d7ae661e9d22fec420abe46df9b72afb2bb5`.
`SHA256SUMS.txt` in the repository verifies the ZIP; the file with the same name
inside the ZIP verifies each unpacked artifact file.

## Reproduce

Extract the ZIP, open a terminal in the extracted directory, and run:

```text
python -m pip install -r requirements.txt
python scripts/analyze_data.py --data measurements --output recomputed
python scripts/build_figures.py --analysis recomputed --output regenerated_figures
```

Python 3.11 or later is required. These commands analyze preserved measurements
and do not start Docker or execute a new workload. The archive README documents
all metrics, configuration labels, execution instructions, and known limitations.

## Provenance and scope

The source snapshot is experiment commit `0d27aa70c5bf228c09ebe694ee3b342782eec5ea`. Measurements are preserved
byte for byte. The original RPS zero-offset issue, the payment-only microservice
drain condition, disabled database durability, and unresolved date discrepancy
are documented in the archive; no missing measurements were fabricated.

The two architectures were measured on one host. The artifact supports the
reported implementation comparison and does not establish general architectural
superiority or equivalent failure-recovery semantics.
