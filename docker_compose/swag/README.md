# SWAG Proxy

This folder contains files for deploy a proxy for __Epsilon Team__ services.

> SWAG - Secure Web Application Gateway (formerly known as letsencrypt, no relation to Let's Encrypt™) sets up an Nginx webserver and reverse proxy with php support and a built-in certbot client that automates free SSL server certificate generation and renewal processes (Let's Encrypt and ZeroSSL). It also contains fail2ban for intrusion prevention.

## How it's works

## Update

For update this service:

1. `docker compose stop swag`
2. `docker compose rm swag`
3. `docker pull lscr.io/linuxserver/swag:latest`
4. `docker compose up -d`

## Deploy

1. Copy `.env_sample` in `.env`;<br>
`cp .env_sample .env`;
2. Replace empty variables with correct values;
3. Up compose: <br>
`docker compose up -d`

## Update config

For update proxy config edit or add files in `config/site-confs` and restart compose whit `docker compose restart`

## Add new service

For add new service:

1. Add a external network in service compose file. For do it add this snippet to end of file

    ```YAML
    networks:
      ingress:
        name: ingress
        external: true
    ```

2. Attach external network to service to expose. For do it add this snippet in the appropiate service definition

    ```YAML
        networks:
          - ingress
    ```

3. Create new config with appropiate configuration. Do not forget that the new service also resides in the same network as the proxy. Then proxy can contact the service with their service name defined in compose file. For example if you have this compose:

    ```YAML
    ...
    services:
      vaultwarden:
        image: vaultwarden/server:latest
        ...
        networks:
          - ingress
    ```

The proxy can contact the with service hostname. That in this case is *vaultwarden*.

## Backup and Restore

### Backup

### Restore

## Throbleshooting

Nothings for now

## FAQ

- Where i find documentations?<br>
[Official Wiki](https://docs.linuxserver.io/general/swag)
