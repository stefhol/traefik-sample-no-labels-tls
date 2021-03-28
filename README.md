# Example Traefik
A Traefik sample without labels for compatibility with podman and has lets encrypt.

## Dynamic Reloading
U only have to restart for the changes in the traefik.yml

main.yml gets updated even new certificates get added

## Lets Encrypt

in this example a certification and dns entry would be generated for `example.com` `sub.example.com` `sub1.example.com` if you provided an `api key` an own the domain `example.com`

To accomplish this there is a dns challenge needed. For this u need an api access for the provider.

https://doc.traefik.io/traefik/https/acme/#providers


Here I use Vultr. In the docker-compose is the api key value stored

Dns Entries get automatically created and a SSL Certificate for the Host(`DOMAIN`) gets created. There is a rate limit so be careful. A week is the timeout

## How to connect my container or website?
Add the name of the compose entry as a url. Here `http://hello` or your service `http://your-service` or your website `http://google.com` you can also specify the port `http://your-service:8080` if your http service is not on an `80` port