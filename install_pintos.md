# Installing Pintos

[Pintos](https://web.stanford.edu/class/cs140/projects/pintos/pintos.html#SEC_Top) requires building Bochs 2.2.6 which is a very old version poorly supported by modern toolchains.  The following instructions documents a successful installation using Virtualbox running on a Windows host.  The most recent version of g++ I was able to successfully use was 4.2.4.

## Install Ubuntu
1. Install [Hardy Heron](http://old-releases.ubuntu.com/releases/8.04.0/) in a new Virtualbox image.
2. Update `/etc/apt/sources.list` to use correct mirrors.  Replace `http://*.ubuntu.com...` with `http://old-releases.ubuntu.com...`.
3. Run `apt-get update`.

## Install Guest Additions
1. `apt-get install linux-headers-generic`
2. Reboot.
3. `sudo sh /media/cdrom/VBoxLinuxAdditions.run`
4. Shut-down

## Configure Share Folder.
1. Set up share folder in virtualbox GUI named `ubuntu_share`.
2. Reboot Ubuntu.  If failed to mount:
3. `mkdir share`
4. `sudo mount -t vboxsf ubuntu_share ./share`

## Build Bochs
1. Download and extract [pintos](http://www.stanford.edu/class/cs140/projects/pintos/pintos.tar.gz).
2. Download [Bochs 2.2.6](https://sourceforge.net/projects/bochs/files/bochs/2.2.6/)
3. Add following to `pintos/src/misc/bochs-2.2.6-build.sh`:
```
export CFLAGS="-fpermissive"
export CXXFLAGS="$CFLAGS"
```
4. Install required libraries `apt-get install g++ libxt-dev ncurses-dev`.
4. Run `bochs-2.2.6-build.sh` passing required args.
5. Should build successfully.

### Complete Pintos Installation
1. Complete steps 2.. from [installation instructions](https://web.stanford.edu/class/cs140/projects/pintos/pintos_12.html#SEC167).
