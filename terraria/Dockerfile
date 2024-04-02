FROM docker.io/ubuntu:jammy

ARG TERRARIA_VERSION=1449

RUN apt-get update
RUN apt-get install -y bash grep curl unzip tmux

RUN mkdir -p /opt/terraria/worlds
RUN mkdir -p /opt/terraria/files
RUN mkdir -p /opt/terraria/conf

COPY files/console /usr/local/bin/console
COPY files/entrypoint /opt/terraria/files/entrypoint
COPY files/variables /opt/terraria/files/variables

RUN chmod 755 /usr/local/bin/console
RUN chmod +x /opt/terraria/files/entrypoint

RUN curl -Lo /tmp/terraria-server.zip https://terraria.org/api/download/pc-dedicated-server/terraria-server-${TERRARIA_VERSION}.zip
RUN unzip -jo /tmp/terraria-server.zip -d /opt/terraria/files "${TERRARIA_VERSION}/Linux/*" && \
    rm /tmp/terraria-server.zip

WORKDIR /opt/terraria/files

RUN chmod +x /opt/terraria/files/TerrariaServer*

RUN adduser ubuntu
RUN chown -R ubuntu:ubuntu /opt/terraria

USER ubuntu

ENV AUTOCREATE="2"
ENV DIFFICULTY="0"
ENV BANLIST="banlist.txt"
ENV LANGUAGE="en-US"
ENV MAXPLAYERS="8"
ENV MODPACK=""
ENV MOTD=""
ENV NPCSTREAM="15"
ENV PASSWORD=""
ENV PRIORITY="1"
ENV SECURE="1"
ENV SEED=""
ENV UPNP="0"
ENV WORLDNAME="World"
ENV WORLDPATH="/opt/terraria/worlds"

ENTRYPOINT ["/opt/terraria/files/entrypoint"]