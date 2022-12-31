FROM archlinux:base-devel

RUN sudo pacman -Syyu --noconfirm gcc gdb boost git unzip cmake

ARG UID=1000
RUN useradd -m -u ${UID} docker
USER docker
WORKDIR /home/docker/tmp

RUN git clone https://aur.archlinux.org/ac-library.git && \
    cd ./ac-library && \
    makepkg && \
    cp *.pkg.tar.zst ../

USER root

RUN pacman -U --noconfirm $(ls *.pkg.tar.zst) && \
    rm -rf /home/docker/tmp

USER docker
WORKDIR /home/docker/work
