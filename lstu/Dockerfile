FROM ubuntu:vivid

RUN apt-get update && apt-get upgrade --yes && apt-get install git --yes

# install carton
COPY cpan.config /root/.cpan/CPAN/MyConfig.pm
RUN cpan Carton

# create user
RUN useradd lstu && groupadd lstu && mkdir /var/www/lstu && chown -R lstu:lstu /var/www/lstu

# install LSTU
RUN git clone https://git.framasoft.org/luc/lstu.git /var/www/lstu && chown lstu:lstu -R /var/www/lstu
RUN cd /var/www/lstu && su -u lstu carton install
COPY lstu.conf /var/www/lstu/lstu.conf
COPY run.sh /run.sh

EXPOSE 8080

ENTRYPOINT ["/run.sh"]
