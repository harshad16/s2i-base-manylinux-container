# This image is the base image for all OpenShift v3 language container images.
FROM quay.io/harshad16/s2i-core-manylinux2010

ENV SUMMARY="Base image with essential libraries and tools used as a base for \
builder images like perl, python, ruby, etc." \
    DESCRIPTION="The s2i-base image, being built upon s2i-core, provides any \
images layered on top of it with all the tools needed to use source-to-image \
functionality. Additionally, s2i-base also contains various libraries needed for \
it to serve as a base for other builder images, like s2i-python or s2i-ruby." \
    NODEJS_SCL=rh-nodejs10

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$DESCRIPTION" \
      io.k8s.display-name="s2i base" \
      com.redhat.component="s2i-base-manylinux2010-container" \
      name="s2i-base-manylinux2010" \
      version="1" \
      maintainer="SoftwareCollections.org <sclorg@redhat.com>"

# This is the list of basic dependencies that all language container image can
# consume.
RUN yum install -y centos-release-scl && \
  INSTALL_PKGS="gcc-c++ \
  gd-devel \
  gdb \
  libcurl-devel \
  libxml2-devel \
  libxslt-devel \
  lsof \
  mariadb-devel \
  mariadb-libs \
  openssl-devel \
  postgresql-devel \
  procps-ng \
  ${NODEJS_SCL}-npm \
  sqlite-devel \
  unzip \
  wget" && \
  yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
  rpm -V $INSTALL_PKGS && \
  yum -y clean all --enablerepo='*'
