# Reproduction - OPEN_SOURCE_DRILLING

```
cd E:\fenta\Downloads\The Anticloud\ANTICLOUD_REPOS\OIL_GAS\OPEN_SOURCE_DRILLING\anticloud
python tools/run_bench.py --out BENCH.json --quiet   # pass 1: generate
python tools/run_bench.py --out BENCH.json --quiet   # pass 2: record
```
Exit code 0 means all 16 checks passed. Evidence: `04_Evidence/run_bench_output.txt`.
