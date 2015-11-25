### How to build the packages

- Add following line to <buildroot dir>/feeds.conf.default:
src-git mediarouter https://github.com/thomashaertel/Camper-Van-Router.git
- Update all feeds sources:
$ ./scripts/feeds update -a
- Install all feeds:
$ ./scripts/feeds install -a 
- Configre Build:
$ make defconfig
$ make prereq
$ make menuconfig
- To compile a single package:
$ make package/<package-name>/compile
- To install a single package:
$ make package/<package-name>/install
