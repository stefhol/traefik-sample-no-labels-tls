# Traefik Sample Project with Let's Encrypt

## Overview

This repository contains a Traefik sample configuration that is compatible with Podman and incorporates Let's Encrypt for automatic SSL certificate generation. The configuration is designed for easy dynamic reloading, reducing the need for frequent restarts.

## Dynamic Reloading

With the provided `traefik.yml` file, you only need to restart the Traefik service to apply changes. The `main.yml` file will automatically update even when new services, containers or routes are added.

## Let's Encrypt Integration

This example demonstrates the automatic generation of SSL certificates and DNS entries for the following domains:
- `example.com`
- `sub.example.com`
- `sub1.example.com`

Please note that for this feature to work, you need to provide an API key and own the domain `example.com`. A DNS challenge is required to validate domain ownership, so you will need to obtain API access for your DNS provider. You can find more details about this process in the Traefik documentation [here](https://doc.traefik.io/traefik/https/acme/#providers).

As an example, this repository uses Vultr as the DNS provider, and the API key value is stored in the Docker Compose file.

## Automatic DNS Entries and SSL Certificates

Traefik will automatically create DNS entries and SSL certificates for the specified hosts (`DOMAIN`). However, it's important to be cautious of rate limits, as they might apply. A one-week timeout is set for avoiding potential issues related to rate limits.

## Connecting Containers or Websites

To connect your container or website to Traefik, you can simply add the name of the corresponding service in the Docker Compose file as a URL. For instance, if your service is named `hello`, you can access it at `http://hello`.

## How to Use

To utilize this sample configuration, follow these steps:

1. In `docker-compose.yml` Replace the placeholder `api key` in the Docker Compose file with your actual API key from your DNS provider (Vultr in this example).

2. In `main.yml` update the list of domain names (e.g., `example.com`, `sub.example.com`, `sub1.example.com`) to match your specific requirements.

3. Make any other necessary modifications to the Traefik configuration in the `traefik.yml` file.

4. Start the Traefik service using the Docker Compose file.

5. Traefik will automatically generate DNS entries and SSL certificates for the specified domains.

6. Access your containers or websites by using the defined service names as URLs.

## Note of Caution

Please be aware of rate limits when using Let's Encrypt. Traefik has a one-week timeout for SSL certificate renewals to help manage these rate limits effectively.
