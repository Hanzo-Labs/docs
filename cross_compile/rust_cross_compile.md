# Cross Compiling on Rust

Below are the steps to cross compile for ARM with rust

1. Add armv7, aarch64

```bash
rustup target add armv7-unknown-linux-gnueabihf # add armv7
rustup target add aarch64-unknown-linux-gnu # add aarch64
```

2. add the following in `~/.cargo/config`

```bash
[target.armv7-unknown-linux-gnueabihf]
linker = "/home/devnaga/work/project_auto/openwrt/staging_dir/toolchain-arm_cortex-a7+neon-vfpv4_gcc-11.2.0_musl_eabi/bin/arm-openwrt-linux-gcc"

[target.aarch64-unknown-linux-gnu]
linker = "/home/devnaga/work/project_auto/openwrt/staging_dir/toolchain-aarch64_generic_gcc-11.2.0_musl/bin/aarch64-openwrt-linux-gcc"
```

3. compile the binary for the target

#### For armv7

```bash
cargo build --target armv7-unknown-linux-gnueabihf --release
```


#### For aarch64

```bash
cargo build --target aarch64-unknown-linux-gnu --release
```
