# Gentics CMS Docker Compose Stack

This repository contains an example docker compose stack for the [Gentics CMS](https://www.gentics.com/genticscms/software_contentmanagement.en.html)

## Introduction & License

Gentics CMS is an integrated solution for online presences. It allows you to create and publish content, organise editorial workflows, and manage a variety of publications. Interfaces such as newsletter and social media integration, special solutions for multimedia storytelling and web analysis cover important functions in online marketing.

Gentics CMS is commercial standard software. Before using it, you have to send a request for a Gentics CMS License Key. This request has to be sent by email to support@gentics.com in combination with your Docker Hub user.
Please note, that separate keys are issued for development and production infrastructures.

Use and distribution of Gentics CMS is covered by the APA-IT license and maintenance terms available at https://www.gentics.com/imprint.

The stack contains the following components:

* Gentics CMS   - CMS
* MariaDB 10.3  - Database
* Elasticsearch - Search server
* Languagetool  - Spellchecker server

Optional:

* Tomcat        - For running the Activiti webapp for the CMS

## Usage

1. Permission on the CMS docker image

Make sure you have the permission to access the Gentics Docker registry at docker.apa-it.at.
If you don't have a user yet, contact support@gentics.com. Use `docker login docker.apa-it.at` to login with your docker client to the Docker registry.

2. Create a docker-compose.override.yml file which contains your license key.

See `docker-compose.overide.example.yml` for a more detailed example.

```yml
version: "3"
services:
  cms:
    environment:
      LICENSEKEY: AAAA-BBBB-CCCC-DDDD-EEEE-FFFF-GGGG-HHHH
```

3. Run the stack

During startup the initial MySQL Database will be imported. This initial setup can take a few seconds.

```
docker compose up -d
```

After the setup you can access Gentics CMS via:
- Editor User Interface: http://localhost:8080/editor
- Administration User Interface: http://localhost:8080/admin
- Old UI: http://localhost:8080/.Node/

and login using `node/node`.

## CMS docker image configuration

See: https://hub.docker.com/r/gentics/cms/

## Common problems & FAQ

See: https://github.com/gentics/cms-compose/wiki/Common-problems-&-FAQ

## Security

You can either set a custom password afterwards or omit the `NODE_USER_PASSWORD` environment variable. Omitting the variable will cause Gentics CMS to generate a random password for you.
