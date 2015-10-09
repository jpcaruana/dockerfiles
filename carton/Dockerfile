FROM ubuntu:vivid
MAINTAINER Jean-Philippe Caruana jp@barreverte.fr

 RUN apt-get update && apt-get upgrade --yes && \
    apt-get install build-essential git --yes

# install carton
COPY cpan.config /root/.cpan/CPAN/MyConfig.pm
RUN cpan Carton
