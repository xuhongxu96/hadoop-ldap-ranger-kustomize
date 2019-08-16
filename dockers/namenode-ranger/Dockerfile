FROM uhopper/hadoop-namenode:2.8.1

WORKDIR /usr/local
ADD http://ftp.jaist.ac.jp/pub/apache/maven/maven-3/3.6.1/binaries/apache-maven-3.6.1-bin.tar.gz ./
RUN tar -xvf apache-maven-3.6.1-bin.tar.gz

ENV M2_HOME="/usr/local/apache-maven-3.6.1"
ENV M2=$M2_HOME/bin
ENV PATH=$M2:$PATH

RUN mvn -version

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    git gcc

WORKDIR /tmp
ADD https://dev.mysql.com/get/mysql-apt-config_0.8.13-1_all.deb ./
RUN dpkg -i mysql-apt-config* && apt-get update && apt-get install mysql-server
RUN systemctl status mysql