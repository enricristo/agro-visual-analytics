# Verification

How the numbers in the [README](README.md) were checked, without publishing
the data or the code. Every claim below was recomputed from the dataset by an
automated test suite; the last run is reported at the end.

## Claims under automated test

| Claim | Value | What the test asserts | Result |
|---|---|---|---|
| Comparable plot-season pairs | 120 by raw name, 778 after standardization | Both counts are recomputed from the data and must match exactly | Passed |
| Name standardization never merges distinct plots | 0 false merges | Typographic variants of one plot share a name; look-alike names of different plots stay apart; missing names never become a plot; two independent implementations agree on every plot name in the dataset | Passed (16 cases) |
| Soil-leaf pairs | 1,150, one row per plot and season | No plot-season appears twice after the join | Passed |
| Joins that would multiply rows | Refused | A join that duplicates rows is detected and blocked instead of silently inflating counts | Passed |
| Soil K vs leaf K | r = −0.009 | \|r\| < 0.05 under each of the three units of analysis | Passed |
| Micronutrients missing together | Cu, Fe, Mn, Zn | The four columns are missing in exactly the same rows | Passed |
| Topsoil potassium in class *Low* | 61.2% | The share is recomputed from the classified samples | Passed |

## Also reported, computed in the analysis

These come from the analysis itself and are not under an automated test.

| Claim | Value |
|---|---|
| Soil K vs leaf K, one point per plot | r = −0.009 (559 plots) |
| Soil K vs leaf K, each plot against its own mean | r = 0.042 (1,019 points, 428 plots) |
| Soil class × leaf class independence | χ² = 1.64, 4 degrees of freedom, p = 0.80 |
| Iron as the most limiting nutrient (DRIS) | 34.4% of leaf samples |
| Soil pH, samples with and without iron first | 5.18 and 5.11 (CaCl₂) |

## Last test run

```
23 passed
2026-10-20 · Python 3.13 · pandas 3.0 · NumPy 2.5 · SciPy 1.18 · matplotlib 3.11
```

## Data fingerprints

SHA-256 of the pseudonymized files behind every figure and number on this
page (UTF-8, LF line endings). If you receive the data on request, these let
you confirm it is the same dataset.

| File | Rows | Columns | SHA-256 |
|---|---:|---:|---|
| `soil.csv` | 1,767 | 33 | `d1a4e1ed3e6ee052bf98e30bb4d45f41122391bb48def2c02c8247eecce8537d` |
| `leaf.csv` | 1,659 | 27 | `60b6be0a757f235e061b6dcefbed57d7d59d9189957ce91715f4f4e7219bca9a` |
| `leaf_dris.csv` | 18,249 | 5 | `3bf5160d95c7efe6b1cd191a5d0ccf253e089f850ae7bbc47fae0c2bea43d5a0` |
| `sample_metadata.csv` | 3,404 | 8 | `6793f6ca46585d79d4e429d70e60769cb28b96ca51b648a835bbfd60b1f30fe0` |
| `climate_monthly.csv` | 238 | 7 | `e93ab8b1aae2f5b575cfad91f4bc9b4ce1c52e8b85e1c9f496dcd5b6cb3a65d5` |
| `reference_ranges.csv` | 79 | 7 | `626ef247a419e28b76098ba66d90ad3c8f02ced9232696a44c01dddb946a25b5` |

The full report, with every step in detail, was delivered to the program
advisor. Data and code for independent review: **contato@hilum.science**.
