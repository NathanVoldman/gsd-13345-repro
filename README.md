# GSD-13345 repro: DG2 IGC crash in GDN ChunkFwdOKernel

Failing SPIR-V module captured via IGC shader dumping during a live crash
on DG2 (Intel Arc A770), reproducing an IGC internal compiler error
("SIGABRT") for `gdn::ChunkFwdOKernel<cutlass::bfloat16_t, cutlass::half_t>`
in [vllm-project/vllm-xpu-kernels](https://github.com/vllm-project/vllm-xpu-kernels).

## Reproduce

```bash
ocloc compile -spirv_input -file OCL_asm33ab992c7de8386d.spv -device dg2
```

Expected: `internal compiler error, abnormal program termination`.
The same command succeeds with `-device bmg` or `-device pvc`.
