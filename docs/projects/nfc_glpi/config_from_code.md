---
title: Config as code
description: How to use No Fuss Computings Ansible role to configure GLPI from configuration as code.
date: 2023-07-28
template: project.html
about: https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi
---

To configure GLPI using this role, the config/settings are saved as json files. The workflow to create the json files, is to (preferably within a test environment) make the required setting changes in GLPI using the GUI. one the changes have been made, conduct an API `GET` query to GLPI for the item you changed. The JSON body that is returned, is placed within the Config file (detailed below) under path `.body`. You must however, remove any fields that are not required, for example dynamic fields (fields that update themselves or are auto created) for example date fields.


## Config files Example

Each tab provides an example of the JSON file layout, including any additional variables. Any variable listed at path `.` that are empty strings, you would complete with the items name as it is exactly within GLPI. These fields are used to fetch the itm_id of the field by name. this enables having the config saved in a more human readable format. For example, for the field `entities_id` you would complete it as `"entities_id": "My entity name"`.

=== "AuthLDAP"

    ``` json title="example.json" linenums="1"

    {
      "api_path": "AuthLDAP",
      "body": {
        // JSON from API Query
      }
    }

    ```

=== "Config (GLPI General Settings)"

    This config file contains the settings found in `General Settings`. The full API JSON response is added to the body. When this file is processed, each individual item is added via the API without using the `id` as found in the JSON file. This is done as the ID's can change, so the workflow includes a step that matches the config item name to the found id in the database, then patches with the values from the JSON file.

    ``` json title="example.json" linenums="1"
    {
      "api_path": "Config",
      "body": [
        // JSON from API Query the full response (see note below)
      ]
    }
    ```

    !!! info
        The structure of this JSON file is different than the rest. The body is a **list** of **ALL** of the Config options. This includes the item ID. it was done this way, so that only one API query is required to export all config options.

=== "Entity"

    ``` json title="example.json" linenums="1"

    {
      "api_path": "Entity",
      "entities_id": "",
      "body": {
        // JSON from API Query
      }
    }

    ```

=== "ITILCategory"

    ``` json title="example.json" linenums="1"

    {
      "api_path": "ITILCategory",
      "users_id": "",
      "itilcategories_id": "",
      "entities_id": "",
      "tickettemplates_id_demand": "",
      "body": {
        // JSON from API Query
      }
    }

    ```

=== "Profile"

    ``` json title="example.json" linenums="1"

    {
      "api_path": "Profile",
      "body": {
        // JSON from API Query
      }
    }

    ```


With the config files structured as per the examples, within your playbook(s), load the json files in a list of json objects using variable `glpi_config_as_code_json`

example

``` yaml title="my_vars.yaml" linenums="1"

glpi_config_as_code_json:
  - "{{ lookup('file', '/workdir/files/glpi/ITILCategory-new-ldap-user.json') | from_json }}"
  - "{{ lookup('file', '/workdir/files/glpi/LDAPAuth-local_ldap.json') | from_json }}"

```
