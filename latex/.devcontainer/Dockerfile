FROM archlinux:base-devel

RUN pacman -Syyu --noconfirm texlive-langjapanese \
        texlive-most \
        perl-yaml-tiny \
        perl-file-homedir \
        nodejs \
        npm

ARG UID=1000
RUN useradd -m -u ${UID} docker
USER docker
WORKDIR /home/docker/tmp


USER root

RUN npm install -g textlint \
        textlint-plugin-latex2e \
        textlint-rule-preset-ja-technical-writing \
        textlint-rule-preset-jtf-style \
        textlint-rule-prh \
        textlint-filter-rule-comments
ENV PATH $PATH:/usr/lib/node_modules/.bin

USER docker
WORKDIR /home/docker/work
