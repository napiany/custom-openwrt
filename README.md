# custom-openwrt

> [!CAUTION]
> The builds and configurations are currently untested!

### Fritz!Box 7530
- DSL Modem
- IPv6 RA
- DNS64
- Tayga for IPv4 compat

# Credits
- Tavi for providing Divested-WRT and it's patches which this project is heavily based on
- Rui Salvaterra for the frequent kernel bumps+testing and the Thumb-2 patch
- Daniel Engberg for the -O2 patch
- OpenWrt, its amazing contributors, and its friendly community for all that it is
- Alexander Popov, for maintaining a detailed list of kernel config hardening options at https://github.com/a13xp0p0v/kconfig-hardened-check

## How to build
Install all the necessary dependencies listed here: https://openwrt.org/docs/guide-developer/build-system/install-buildsystem#linux_distributions

- `git clone https://git.openwrt.org/openwrt/openwrt.git`
- `cd openwrt`
- `git config pull.rebase true`
- `./scripts/feeds update -a -f`
- `./scripts/feeds install -a -f`
- Copy in the config for the device as .config
- `git apply patches/*.patch`
- `make menuconfig` Make changes, save and exit
- `make download -j4`
- `make -j16`

## How to update the build
- `cd openwrt`
- `make clean`
- `git pull`
- `./scripts/feeds update -a -f`
- `./scripts/feeds install -a -f`
- `make menuconfig` Save and exit
- `make download -j4`
- `make -j16`

## Notices
- OpenWrt is a registered trademark of the Software Freedom Conservancy.
- I am not affiliated with OpenWrt or Fritz!.
- These builds are not sponsored or endorsed by OpenWrt.
- The official OpenWrt website is at https://openwrt.org.
- OpenWrt source code is available at https://git.openwrt.org/openwrt/openwrt.git.
- Linux is a registered trademark of Linus Torvalds.
- Linux source code is available at https://kernel.org/.
- Fritz!Box is a registered trademark of Fritz! GmbH.
- All product names, logos, and brands are property of their respective owners. Use of these names, logos, and brands does not imply sponsorship or endorsement.