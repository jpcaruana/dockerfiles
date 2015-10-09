FROM jpcaruana/carton
MAINTAINER Jean-Philippe Caruana jp@barreverte.fr

RUN apt-get install git --yes

# install LSTU
RUN mkdir -p /var/ww && git clone https://git.framasoft.org/luc/lstu.git /var/www/lstu && \
    cd /var/www/lstu && git checkout 0.06 && \
      echo "installing LSTU dependancies" && carton install
COPY lstu.conf /var/www/lstu/lstu.conf
COPY run.sh /run.sh

EXPOSE 8080

ENTRYPOINT ["/run.sh"]
