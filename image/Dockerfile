FROM balenalib/rpi-debian
#Pass these when buildning
ARG USERNAME
ARG PASSWORD
ENV TZ=UTC
#installs dependencies needed for my zero image
RUN apt-get update && \
    apt-get install -y \
    build-essential \
    cmake \
    gcc-arm-none-eabi \
    libnewlib-arm-none-eabi \
    gdb-multiarch \
    openssh-server \
    sudo \
    neovim \
    gdb \
    git \
    zsh \
    mosquitto \
    mosquitto-clients
# 
RUN mkdir -p /var/run/sshd && \
    useradd -m -s /bin/bash ${USERNAME} && \
    echo "${USERNAME}:${PASSWORD}" | chpasswd && \
    usermod -aG sudo ${USERNAME}


RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

RUN echo "locales locales/default_environment_locale select sv_SE.UTF-8" | debconf-set-selections && \
    echo "locales locales/locales_to_be_generated select sv_SE.UTF-8 UTF-8" | debconf-set-selections
RUN DEBIAN_FRONTEND=noninteractive dpkg-reconfigure locales

CMD ["/bin/bash", "-c", "service ssh start && tail -f /dev/null"]
