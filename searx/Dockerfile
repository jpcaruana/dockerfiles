# docker build --rm -t jpcaruana/searx .
# docker run -d --name searx -p 5000:5000 jpcaruana/searx

FROM python:2.7-slim
MAINTAINER Jean-Philippe Caruana jp@barreverte.fr

RUN useradd searx

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y --no-install-recommends --force-yes \
            zlib1g-dev libxml2-dev libxslt1-dev libffi-dev build-essential \
            libssl-dev openssl curl unzip && \
    rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache uwsgi

WORKDIR /app
RUN curl https://codeload.github.com/asciimoo/searx/zip/v0.8.0 -o '/tmp/searx-0.8.0.zip' -L
RUN unzip /tmp/searx-0.8.0.zip -d /tmp && mv /tmp/searx-0.8.0/* /app/
RUN pip install --no-cache -r requirements.txt

COPY settings.yml /app/searx/settings.yml
COPY opensearch.yml /app/searx/templates/oscar/opensearch.xml

EXPOSE 5000
CMD ["/usr/local/bin/uwsgi", "--uid", "searx", "--gid", "searx", "--http", ":5000", "-w",  "searx.webapp"]
RUN sed -i -e "s/ultrasecretkey/`openssl rand -hex 16`/g" searx/settings.yml
