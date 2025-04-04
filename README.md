# WebAssembly Benchmarks 2025

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

## Usage

### Running the benchmark workloads and profiling them

For convenience we have created a single Bash script to run all of the workloads and do all of the profiling.

```shell
# run the script to get some usage instructions
./profiler.sh
# this will fail but it gives us some idea on how to run it properly

# run with all the required parameters specified
iter=1 container_namespace=us.icr.io/polyglotwasmbench wasmtime_original_loc=/path/to/wasmtime wasmtime_socket_loc=/path/to/wasmtime/socket ./profiler.sh
```

Unfortunately due to git size constraints we had to remove certain large files (example: ~500MB file used in copy file workload).
The script can still be run, but may produce errors for workloads that depend on such large files.

### Creating the charts

The Python script and instructions for creating the charts are in the [charts](./charts/) folder.

### Prerequisites/Dependencies

These are some of the major dependencies used by the workloads:

#### Profiling tools

We use the Linux `perf` command and the surrounding tool suite (`syscount`, etc.) to profile the workloads.

You can clone and add this repo to the `PATH`: https://github.com/brendangregg/perf-tools?tab=readme-ov-file#install

#### WebAssembly Runtimes

- Wasmer https://wasmer.io/products/runtime
- Wasmtime https://wasmtime.dev/
- WasmEdge https://wasmedge.org/
- CRun for containerized workloads (with Wasmtime backend enabled) https://github.com/containers/crun

#### Rust Python

This is a Python interpreter written in Rust. https://github.com/RustPython/RustPython
This is designed to be compiled to WASM. Precompiled package is available here https://wasmer.io/rustpython/rustpython

Run with
```shell
wasmer run rustpython/rustpython
```

#### WAPM CLI

This has been superceded by https://wasmer.io/products/registry

This is a very useful package manager for WASM https://github.com/wasmerio/wapm-cli
Allows us to do
```shell
wapm install rustpython
```
