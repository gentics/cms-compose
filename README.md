# Gentics CMS Docker Compose Stack

This repository contains an example docker compose stack for the [Gentics Enterprise CMS](https://www.gentics.com/genticscms/software_contentmanagement.en.html)

The stack contains the following components:

* Gentics CMS   - CMS
* MariaDB 10.3  - Database
* Elasticsearch - Search server
* Languagetool  - Spellchecker server

## Usage

1. Create a docker-compose.override.yml file which contains your license key.

See `docker-compose.overide.example.yml` for a more detailed example.

```yml
version: '2'
services:
  cms:
    environment:
      LICENSEKEY: AAAA-BBBB-CCCC-DDDD-EEEE-FFFF-GGGG-HHHH
```

2. Run the stack

During startup the initial MySQL Database will be imported. This initial setup can take a few seconds.

```
docker-compose up -d
```

After the setup you can access the UI via http://localhost:8080/.Node/ui and login using `node/node`.

## Security

You can either set a custom password afterwards or omit the `NODE_USER_PASSWORD` environment variable. Omitting the variable will cause Gentics CMS to generate a random password for you.