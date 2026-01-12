# custom-openwrt
Custom OpenWrt build configurations and patches for select devices I own and use. These images focus on privacy, security and IPv6-native setups.

> [!warning]
> These builds and configurations are not ready-to-use and demand additional setup beyond what’s included here. Use them only if you know what you’re doing. If something breaks, you get to keep both pieces!

## Supported devices

### Fritz!Box 7530
Installation instructions are available in the official OpenWrt documentation: https://openwrt.org/toh/avm/avm_fritz_box_7530

In this setup, the Fritz!Box operates as both the modem and primary router. It establishes IPv4 connectivity over PPPoE and IPv6 connectivity via DHCPv6, but only propagates IPv6 within the local network using SLAAC.

All LAN clients function in an IPv6-only environment and reach IPv4 services through [Tayga](https://github.com/apalrd/tayga) (NAT64) and [Unbound](https://www.nlnetlabs.nl/projects/unbound/about/) (DNS64), enabling seamless access to legacy IPv4 infrastructure without requiring dual-stack configurations.

This design simplifies network management by eliminating dual-stack complexity, mitigates IPv4 address exhaustion, and aligns with the transition toward IPv6-native networking. Most applications operate transparently in this setup while maintaining full access to the IPv4 Internet via automatic protocol translation.

### ZyXEL GS1900-8HP v2/B1
Installation instructions are available in the official OpenWrt documentation: https://openwrt.org/toh/zyxel/gs1900-8hp_v1

## Credits
Huge thanks to Tavi for maintaining [Divested-WRT](https://divested.dev/unofficial-openwrt-builds/mvebu-linksys/), as well as for providing the patches and improvements that this project is based on. 

## Make your own

### How to build
1. Install all required dependencies as listed in the OpenWrt documentation: https://openwrt.org/docs/guide-developer/build-system/install-buildsystem#linux_distributions

2. Run the following commands:
```
git clone https://git.openwrt.org/openwrt/openwrt.git
cd openwrt
git config pull.rebase true
./scripts/feeds update -a -f
./scripts/feeds install -a -f
# Copy in the config for the device as .config
git apply patches/*.patch
make menuconfig # Make changes, save and exit
make download -j4
make -j16
```

### How to update the build
1. Run the following commands:
```
cd openwrt
make clean
git pull
./scripts/feeds update -a -f
./scripts/feeds install -a -f
make menuconfig # Save and exit
make download -j4
make -j16
```

## Notices
- OpenWrt is a registered trademark of the Software Freedom Conservancy.
- This project is not affiliated with, endorsed by, or sponsored by OpenWrt, Fritz! or ZyXEL.
- Official OpenWrt website: https://openwrt.org
- OpenWrt source code: https://git.openwrt.org/openwrt/openwrt.git
- Linux is a registered trademark of Linus Torvalds.
- Linux source code: https://kernel.org
- Fritz!Box is a registered trademark of Fritz! GmbH.
- ZyXEL is a registered trademark of Zyxel Group Corporation.
- All names, logos, and trademarks are the property of their respective owners. Their use does not imply endorsement or affiliation.