FROM debian:testing

ARG USER_NAME=latex
ARG USER_HOME=/home/latex
ARG USER_ID=1000
ARG USER_GECOS=LaTeX

RUN adduser \
  --home "$USER_HOME" \
  --uid $USER_ID \
  --gecos "$USER_GECOS" \
  --disabled-password \
  "$USER_NAME"

ARG SSHCLIENT=openssh-client
ARG SCONS=scons
ARG JDK=openjdk-11-jdk
ARG PANDOC=pandoc
ARG GIT=git

RUN apt-get update && apt-get install -y \
  texlive-full \
  # some auxiliary tools
  "$SCONS" \
  "$SSHCLIENT" \
  "$JDK" \
  "$PANDOC" \
  "$GIT" && \
  # Removing documentation packages *after* installing them is kind of hacky,
  # but it only adds some overhead while building the image.
  apt-get --purge remove -y .\*-doc$ && \
  # Remove more unnecessary stuff
  apt-get clean -y
