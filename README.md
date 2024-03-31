Build OpenWRT for VoCore2 Ultimate
----------------------------------

- https://github.com/vonger/vocore2
- https://github.com/openwrt/openwrt
- https://openwrt.org/docs/guide-developer/toolchain/use-buildsystem
- https://openwrt.org/toh/vocore/vocore
- https://downloads.openwrt.org/releases/22.03.5/targets/ramips/rt305x/

# Quick build with Docker

TODO

    docker build

    $ cd ./docker/
    $ docker build -t vocore2-dev .
    $ docker run --name vocore2-dev vocore2-dev
    $ docker export vocore2-dev | tar2sqfs vocore2-dev.sqfs
    $ singularity shell -e vocore2-dev.sqfs # use it
    singularity> cd /path/to/openwrt # and more, see below

# Commands

    git clone https://github.com/openwrt/openwrt.git
    cd openwrt
    git switch -c v22.03.5

    # git clean -xdf
    # rm -rf bin/ build_dir/ dl/ feeds staging_dir/ tmp/ .toolchain_build_ver package/feeds/

    ./scripts/feeds update -a
    ./scripts/feeds install -a
    git clone https://github.com/vonger/vocore2.git package/vocore2
    bash package/vocore2/openwrt.2203/v2u_apply.sh


    #wget https://downloads.openwrt.org/releases/22.03.5/targets/ramips/rt305x/config.buildinfo -O .config
    # TODO embeded config
    # ./scripts/diffconfig.sh > diffconfig
    cp package/vocore2/openwrt.2102/v2u_defconfig .config
    make defconfig
    make -j4 V=s
    # bin/targets/ramips/mt76x8/openwrt-ramips-mt76x8-vocore_vocore2-squashfs-sysupgrade.bin
