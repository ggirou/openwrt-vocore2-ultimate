FROM debian:bookworm

ENV DEBIAN_FRONTEND noninteractive

# This repository can be a bit slow at times. Don't panic...
# COPY apt-sources.list /etc/apt/sources.list

RUN apt update -y && \
    apt install -y --no-install-recommends \
    ca-certificates \
    build-essential clang flex bison g++ gawk gcc-multilib g++-multilib \
    gettext git libncurses-dev libssl-dev python3-distutils rsync unzip zlib1g-dev \
    file wget \
    # bc bison build-essential bzip2 ca-certificates ccache clang cmake \
    # cpio curl cvs diffutils ecj fastjar file findutils flex gawk \
    # gcc-multilib gettext git gkermit grep gzip java-propose-classpath \
    # libelf-dev libncurses5-dev libssl-dev locales lrzsz mercurial \
    # python2 python2-dev python3 python3-dev rsync screen sed subversion \
    # swig tar time tmux unzip util-linux wget xsltproc xz-utils zlib1g-dev \
    # nvi cscope openssh-client dropbear-bin sparse indent\
    && \
    apt autoremove -y && \
    apt clean -y
