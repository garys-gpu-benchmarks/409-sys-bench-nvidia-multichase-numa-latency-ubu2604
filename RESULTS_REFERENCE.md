# Results: 409 multichase Pointer-Chase

**Main goal:** Measure pointer-chase latency across yaml working-set tiers  
**Tools:** Compile src/multichase.c; run build/multichase under numactl via scripts/collect_multichase.py

Reference results measured by the maintainer on the system shown in each section (generator TEMPLATE_00_139 · recorded 2026-11-13). Your own runs write `results/RESULTS_ACTUAL.md` in the same format.

> Smoke runs use deliberately small sizes. They check that the workload installs and runs end to end; their numbers are not performance results. Baseline and extended are.

<!-- profile:smoke -->
## smoke

- **System:** 1× NVIDIA H100 PCIe (81559 MiB) · Intel(R) Xeon(R) Platinum 8352Y CPU @ 2.20GHz · Ubuntu 26.04.1 LTS · kernel 6.8.0-138-generic · driver 595.91.07
- **Run:** 2026-11-13T14:00:27Z · status **N/A-EXPECTED** (exit 0)
- **Time (mm:ss):** setup 00:46 · benchmark 00:03 · whole run 01:01
- **Source:** run 409_20261113_140027
- **Command:** `bash run_benchmark.sh --smoke --num-numa-nodes 1 --working-set-size l1=16384,l2=262144,l3=2097152,local_dram=268435456,remote_dram=268435456 --stride 64 --warmup-iters 10000 --num-iterations 200000 --num-threads 1 --thread-affinity 0-3`

| # | Metric | Result |
|---|---|---|
| 1 | Pointer-chase latency for the L1-cache tier (latency_ns_l1) | 6.38656 |
| 2 | Pointer-chase latency for the L2-cache tier (latency_ns_l2) | 15.88081 |
| 3 | Pointer-chase latency for the L3-cache tier (latency_ns_l3) | 28.712465 |
| 4 | Local DRAM latency, ns (latency_ns_local_dram) | 100.195265 |
| 5 | Remote DRAM latency, ns, na on a host with fewer than two NUMA nodes (latency_ns_remote_dram) | na (expected: host has 2+ NUMA nodes but numactl cannot bind memory to a remote node here) |
<!-- /profile:smoke -->
