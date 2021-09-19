# Alpine libsystemd Package

This is an experimental build of systemd for Alpine Linux. **ONLY libsystemd** has been packaged, and proper functioning of systemd is untested.

Use this package to satisfy build-time dependencies for other software projects, **when you don't care if the systemd part works right**!

## Compile Package

Full compile instructions are provided on the ["Creating an Alpine package" page on the alpine wiki](https://wiki.alpinelinux.org/wiki/Creating_an_Alpine_package), the tldr is as follows:

#### On a system running The target Alpine release, install build tools:

    apk add alpine-sdk git
    adduser -G abuild abuild
    mkdir -p /var/cache/distfiles
    chown abuild:abuild /var/cache/distfiles
    su - abuild
    abuild-keygen -a -i

#### Clone the package sources:

    git clone https://github.com/Artox/alpine-systemd.git
    cd alpine-systemd

#### Execute alpine package builder

    abuild -r

#### Find binary packages in *~/packages/<username>/*:

    find ~/packages -type f
    /home/user/packages/user/aarch64/libsystemd-dev-249-r0.apk
    /home/user/packages/user/aarch64/libsystemd-249-r0.apk
    /home/user/packages/user/aarch64/APKINDEX.tar.gz

## Compile for all Architectures

#### On a system where qemu user-mode emulation has been set up, download rootfs's:

    export basedir=~

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	wget https://dl-cdn.alpinelinux.org/alpine/v3.14/releases/$arch/alpine-minirootfs-3.14.2-$arch.tar.gz
    	sudo mkdir -p $basedir/build-$arch
    	sudo tar -C $basedir/build-$arch -xf alpine-minirootfs-3.14.2-$arch.tar.gz
    	sudo cp -L /etc/resolv.conf $basedir/build-$arch/etc/resolv.conf
    done

#### Copy QEMU binaries to each rootfs:

    sudo cp /usr/bin/qemu-aarch64{,-binfmt} $basedir/build-aarch64/usr/bin/
    sudo cp /usr/bin/qemu-arm{,-binfmt} $basedir/build-armhf/usr/bin/
    sudo cp /usr/bin/qemu-arm{,-binfmt} $basedir/build-armv7/usr/bin/
    sudo cp /usr/bin/qemu-ppc64le{,-binfmt} $basedir/build-ppc64le/usr/bin/
    sudo cp /usr/bin/qemu-s390x{,-binfmt} $basedir/build-s390x/usr/bin/
    sudo cp /usr/bin/qemu-i386{,-binfmt} $basedir/build-x86/usr/bin/
    sudo cp /usr/bin/qemu-x86_64{,-binfmt} $basedir/build-x86_64/usr/bin/

#### Install alpine build tools:

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	sudo chroot $basedir/build-$arch /sbin/apk add alpine-sdk
    done


#### Execute Builds:

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	sudo mount --bind /dev $basedir/build-$arch/dev
    	sudo mount -t proc proc $basedir/build-$arch/proc
    done

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	sudo rm -rf $basedir/build-$arch/root/.abuild $basedir/build-$arch/root/source
    	sudo cp -R $basedir/alpine-systemd $basedir/build-$arch/root/source
    	sudo cp -R $basedir/.abuild $basedir/build-$arch/root/
    	sudo chroot $basedir/build-$arch /bin/sh -c 'source /home/abuild/source/APKBUILD; apk add $makedepends'
    	sudo chroot $basedir/build-$arch /bin/sh -c 'cd ~/source; abuild -F -r'
    done

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	sudo umount $basedir/build-$arch/dev
    	sudo umount $basedir/build-$arch/proc
    done

#### Collect Results:

    mkdir -p packages
    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	sudo cp -R $basedir/build-$arch/root/packages/root/$arch ./packages/
    done
    sudo chown -R $(id -u):$(id -g) packages

    for arch in aarch64 armhf armv7 ppc64le s390x x86 x86_64; do
    	cp -v packages/$arch/libsystemd-249-r0.apk libsystemd-249-r0.$arch.apk
    	cp -v packages/$arch/libsystemd-dev-249-r0.apk libsystemd-dev-249-r0.$arch.apk
    done
