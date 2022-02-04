FROM texlive/texlive:latest

RUN apt update && DEBIAN_FRONTEND=noninteractive apt \
        install --no-install-recommends -y \
        python3 python3-pip git latexmk biber zsh \
        && apt-get clean autoclean\
        && apt-get autoremove --yes\
        && rm -rf /var/lib/{apt,dpkg,cache,log}/

RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v1.1.2/zsh-in-docker.sh)" -- \
        -p git -p ssh-agent -p 'history-substring-search' \
        -a 'bindkey "\$terminfo[kcuu1]" history-substring-search-up' \
        -a 'bindkey "\$terminfo[kcud1]" history-substring-search-down'