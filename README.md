MY WORDPRESS
============

START UP WITH HTTP

1.- Create environment file. Rename env-example file to .env

    mv env-example .env

2.- Configure environments in .env file (if necessary).

3.- Configure your hosts file and add this line:

    127.0.0.1 mywordpress.local

4.- Start up.

    docker-compose up --build -d --force-recreate


START UP WITH HTTPS

Traefik is responsible for extracting each domain certificate that he has allowed.
This is done based on the Host rule specified as "label". In this case it is the domain mywordpress.local.
Traefik uses letsencrypt to extract the certificates, which are automatically renewed every 3 months.

1.- Create environment file. Rename env-example file to .env

    mv env-example .env

2.- Configure environments in .env file (if necessary).

3.- Configure your hosts file and add this line:

    127.0.0.1 mywordpress.local

4.- Configure Traefik config file.

    4.1.- Delete this line in ./configs/traefik/traefik.toml
          defaultEntryPoints = ["http"]

    4.2.- Uncomment all lines on ./configs/traefik/traefik.toml

5.- Start up.

    docker-compose up --build -d --force-recreate