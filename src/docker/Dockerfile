FROM ubuntu:23.04
RUN apt-get update -y
RUN apt-get install -qq -y unzip zip wget curl gdbserver libc6-dev libc6-dbg zlib1g-dev gcc
RUN apt-get install -qq -y gdb
ARG JAVA_VERSION
ENV GRAAL_VERSION=${JAVA_VERSION}-graalce
RUN curl -s "https://get.sdkman.io" | bash
RUN bash -c "source /root/.sdkman/bin/sdkman-init.sh; sdk install java ${GRAAL_VERSION}"
ENV GRAALVM_HOME=/root/.sdkman/candidates/java/${GRAAL_VERSION}

RUN ${GRAALVM_HOME}/bin/native-image --version

RUN apt-get install -qq -y openjdk-17-jre maven
ENV M2_HOME=/usr/share/maven


