# yocto-langdale

## Build

```
docker build -t yocto-langdale
```

## Example usage

Build and run the Yocto langdale minimal image on qemu.

```
mkdir poky
cd poky
docker run -i -i --device /dev/net/tun -v `pwd`:/home/chef/project yocto-langdale
git clone git://git.yoctoproject.org/poky project
cd project
source oe-init-build-env
bitbake core-image-minimal
runqemu
```
