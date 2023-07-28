---
title: Ansible Role nfc_glpi
description: How to use No Fuss Computings Ansible role to manage GLPI from configuration as code.
date: 2023-07-28
template: project.html
about: https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi
---

This Ansible role is designed to manage GLPI specifically installation and configuration.


## Features

- install GLPI using our [docker container](https://gitlab.com/nofusscomputing/projects/docker-glpi)


## Default Variables

Here's an example playbook that demonstrates how to use the `docker_management` role:

```yaml title="defaults/main.yaml" linenums="1

--8<-- "defaults/main.yaml"

```
