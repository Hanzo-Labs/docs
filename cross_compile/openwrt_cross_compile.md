# cross_compile_openwrt
cross compile source code with the openwrt

1. For this to work first compile openwrt for a target. For example `nanopi-r1`.

use the below environment setup,

```bash
# Check for LD_LIBRARY_PATH being set, which can break SDK and generally is a bad practice
# http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html#AEN80
# http://xahlee.info/UnixResource_dir/_/ldpath.html
# Only disable this check if you are absolutely know what you are doing!
if [ ! -z "$LD_LIBRARY_PATH" ]; then
    echo "Your environment is misconfigured, you probably need to 'unset LD_LIBRARY_PATH'"
    echo "but please check why this was set in the first place and that it's safe to unset."
    echo "The SDK will not operate correctly in most cases when LD_LIBRARY_PATH is set."
    echo "For more references see:"
    echo "  http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html#AEN80"
    echo "  http://xahlee.info/UnixResource_dir/_/ldpath.html"
    return 1
fi
export SDKTARGETSYSROOT=/home/devnaga/work/project_auto/openwrt/staging_dir/toolchain-arm_cortex-a7+neon-vfpv4_gcc-11.2.0_musl_eabi/bin
export PATH=/home/devnaga/work/project_auto/openwrt/staging_dir/toolchain-arm_cortex-a7+neon-vfpv4_gcc-11.2.0_musl_eabi/bin/:/home/devnaga/work/project_auto/openwrt/staging_dir/toolchain-arm_cortex-a7+neon-vfpv4_gcc-11.2.0_musl_eabi/lib:/home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/lib:$PATH
export PKG_CONFIG_SYSROOT_DIR=$SDKTARGETSYSROOT
export PKG_CONFIG_PATH=$SDKTARGETSYSROOT/usr/lib/pkgconfig:$SDKTARGETSYSROOT/usr/share/pkgconfig
export OECORE_TARGET_SYSROOT="$SDKTARGETSYSROOT"
export OECORE_BASELIB="lib"
export OECORE_TARGET_ARCH="arm"
export OECORE_TARGET_OS="openwrt-linux"
export CC="arm-openwrt-linux-gcc -mthumb -mfpu=neon-vfpv4 -mfloat-abi=hard -mcpu=cortex-a7 -fstack-protector-strong  -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=$SDKTARGETSYSROOT -I /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/include -L /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/lib"
export CXX="arm-openwrt-linux-g++ -mthumb -mfpu=neon-vfpv4 -mfloat-abi=hard -mcpu=cortex-a7 -fstack-protector-strong  -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=$SDKTARGETSYSROOT -I /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/include -L /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/lib"
export CPP="arm-openwrt-linux-gcc -E  -mthumb -mfpu=neon-vfpv4 -mfloat-abi=hard -mcpu=cortex-a7 -fstack-protector-strong  -D_FORTIFY_SOURCE=2 -Wformat -Wformat-security -Werror=format-security --sysroot=$SDKTARGETSYSROOT -I /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/include -L /home/devnaga/work/project_auto/openwrt/staging_dir/target-arm_cortex-a7+neon-vfpv4_musl_eabi/usr/lib"
export AS="arm-openwrt-linux-as "
export LD="arm-openwrt-linux-ld --sysroot=$SDKTARGETSYSROOT"
export STRIP=arm-openwrt-linux-strip
export RANLIB=arm-openwrt-linux-ranlib
export OBJCOPY=arm-openwrt-linux-objcopy
export OBJDUMP=arm-openwrt-linux-objdump
export READELF=arm-openwrt-linux-readelf
export AR=arm-openwrt-linux-ar
export NM=arm-openwrt-linux-nm
export M4=m4
export TARGET_PREFIX=arm-openwrt-linux-
export CFLAGS=" -O2 -pipe -g -feliminate-unused-debug-types "
export CXXFLAGS=" -O2 -pipe -g -feliminate-unused-debug-types "
export LDFLAGS="-Wl,-O1 -Wl,--hash-style=gnu -Wl,--as-needed -fstack-protector-strong -Wl,-z,relro,-z,now"
export CPPFLAGS=""
export KCFLAGS="--sysroot=$SDKTARGETSYSROOT"
export OECORE_DISTRO_VERSION="3.1.15"
export OECORE_SDK_VERSION="3.1.15"
export ARCH=arm
export CROSS_COMPILE=arm-openwrt-linux-
export STAGING_DIR=/home/devnaga/work/project_auto/openwrt/staging_dir

```
