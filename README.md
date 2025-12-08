# custom-openwrt

> [!CAUTION]
> The builds are currently untested!

## How to build
Install all the necessary dependencies listed here: https://openwrt.org/docs/guide-developer/build-system/install-buildsystem#linux_distributions

- `git clone https://git.openwrt.org/openwrt/openwrt.git`
- `cd openwrt`
- `git config pull.rebase true`
- `./scripts/feeds update -a -f`
- `./scripts/feeds install -a -f`
- copy in the config from the latest build here, name it .config
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