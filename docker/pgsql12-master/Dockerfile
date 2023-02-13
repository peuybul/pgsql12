FROM local/c7-systemd:latest
MAINTAINER calista

### BEGIN SET TIME ZONE
 ENV TZ=Asia/Jakarta
 RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
### END SET TIME ZONE

RUN yum install -y epel-release \
&& yum update -y \
&& yum install -y https://download.postgresql.org/pub/repos/yum/reporpms/EL-7-x86_64/pgdg-redhat-repo-latest.noarch.rpm \
&& yum install -y nano htop postgresql12-server postgresql12-contrib \
&& yum -y clean all \
&& rm -rf /var/cache/yum

RUN systemctl enable postgresql-12.service

ADD init-pgsql-master.sh /root/init-pgsql-master.sh
RUN chmod +x /root/init-pgsql-master.sh

CMD ["/usr/sbin/init"]

