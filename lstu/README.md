## Build image

````
docker build --rm -t jpcaruana/lstu:0.06 .
````

Or pull it:

````
docker pull jpcaruana/lstu
````

## Start container ##

Ports:
- 8080: HTTP port

````
docker run -d --name lstu -p 12000:8080 jpcaruana/lstu
````


## Manage container with systemd

Copy `lstu.service` into `/etc/systemd/system/lstu.service`

Run:

    sudo systemctl start lstu.service

## Start container at boot server

Run:

    sudo systemctl enable lstu.service
