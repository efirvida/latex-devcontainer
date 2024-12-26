FROM qmcgaw/latexdevcontainer:latest-full

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get -y install build-essential \
    openjdk-17-jre-\* \
    python3 \
    python-is-python3 \
    python3-requests \
    python3-bs4 \
    wget \
    sudo \
    && export DEBIAN_FRONTEND=noninteractive

ARG HOST_UID
ARG HOST_GID

RUN groupadd -g ${HOST_GID} writer && \
    useradd -m -u ${HOST_UID} -g writer writer && \
    echo "writer ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Set the non-root user as the default user
RUN chown -R writer:writer /workspace

USER writer
WORKDIR /workspace
RUN chmod -R 755 /workspace
RUN sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
