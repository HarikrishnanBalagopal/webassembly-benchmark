# WebAssembly Benchmark 2023

Benchmarking WebAssembly in various scenarios.

## References

Based on this repo https://github.com/dsrg-uoft/LangBench made for the paper https://www.usenix.org/publications/loginonline/investigating-managed-language-runtime-performance
Related repos mentioned in the paper: https://github.com/topics/langbench

### Our contributions

We have added the following:
- Mandelbrot workload
- Large file copy workload
- SDK-wrappers for each workload and language
- Related Dockerfiles

Further we have targetted WASM for our benchmarking while the original paper was more about comparing different language runtimes.
