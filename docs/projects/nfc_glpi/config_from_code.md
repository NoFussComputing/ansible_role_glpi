---
title: GLPI Config as code
description: How to use No Fuss Computings Ansible role to configure GLPI from configuration as code.
date: 2023-07-28
template: project.html
about: https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi
---

To configure GLPI using this role, the config/settings are saved as json files. The workflow to create the json files, is to (preferably within a test environment) make the required setting changes in GLPI using the GUI. once the changes have been made, conduct an API `GET` query to GLPI for the item you changed. The JSON body that is returned, is placed within the Config file (detailed below) under path `.body`. You must however, remove any fields that are not required, for example dynamic fields (fields that update themselves or are auto created) for example date fields. it's also recommended to remove the items `id` entry from the body, this option enables the updating and creation of the item by the name field.

As the export process is manual to create the json files, it is possible that errors could occur. another side effect is that when updating an item, when checking it into an SCM (git for example), that the commit may contain more than the item that changed. This is planned to be rectified in [gitlab-#1](https://gitlab.com/nofusscomputing/projects/ansible/nfc_glpi/-/issues/1).

!!! warning
    To utilise the config from json files, it's important that any configurable item from json files, that it's name is unique for that item type within GLPI. This is due to the feature "find item_id by name" i.e. you can't have two items named `my name` and `my name` of type `x`, even if in different entities. 


## Config files Example

Each tab provides an example of the JSON file layout, including any additional variables. Variable listed at path `.`, with the exception of `api_path`, `body` or have asuffix of `_` are provided to use that items name. These fields are used to fetch the item_id of the field by name. available fields are:

- entities_id

- groups_id

- item_id

- itilcategories_id

- tickettemplates_id_demand

- tickettemplates_id

- users_id


For example, to have an item placed in the entity `NoFussComputing` provided value would be `"entities_id": "NoFussComputing"`. As part of the item workflow a search for an entity named `NoFussComputing` is conducted, and if found, adds it's `entity_id` to path `.body.entities_id: {entity_id}`.


!!! tip
    If you leave the item ID in the config file under path `.body.id`, the item that matches this ID, will be updated, not the item matching the name.

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

    !!! info "Further Information"
        Any config item that does not contain a value field, is excluded from being added or updated. In addition, the following items by name, are excluded

        ``` yaml title="tasks/api/excluded_config.yaml" linenums="1"

        --8<-- "tasks/api/excluded_config.yaml"

        ```

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

=== "TicketTemplate"

    This config file covers all parts of a ticket template. with this template you can create and update an existing ticket template.

    !!! warning
        Assosiated Items do not get updated or removed. They will be added if they don't exist. No checks are done for more assosiated items then are specified in the template.

    ``` json title="example.json" linenums="1"

    {
      "api_path": "TicketTemplate",
      "entities_id": "",
      "body": {
        // JSON from API Query
      },
      "_TicketTemplateMandatoryField": [

        // JSON from API Query path TicketTemplate/{ticket_template_id}/TicketTemplateMandatoryField
      ],
      "_TicketTemplatePredefinedField": [

        // JSON from API Query path TicketTemplate/{ticket_template_id}/TicketTemplatePredefinedField

      ],
      "_TicketTemplateHiddenField": [

        // JSON from API Query path TicketTemplate/{ticket_template_id}/TicketTemplateHiddenField

      ]
    }

    ```

    Sub-items to the ticket are `TicketTemplateMandatoryField`, `TicketTemplatePredefinedField` and `TicketTemplateHiddenField` and are at json path `._{sub-item}`. These items are a **list of dicts** and can contain the `id` of the item, however it is ignored as the update is base off of `tickettemplates_id`, `num` for all and `tickettemplates_id`, `num` and `value` for `num=13` which is an assosiated item. With the exception of the latter, all of these values will be updated if they exist.


With the config files structured as per the examples, within your playbook(s), load the json files in a list of json objects using variable `glpi_config_as_code_json`

example

``` yaml title="my_vars.yaml" linenums="1"

glpi_config_as_code_json:
  - "{{ lookup('file', '/workdir/files/glpi/ITILCategory-new-ldap-user.json') | from_json }}"
  - "{{ lookup('file', '/workdir/files/glpi/LDAPAuth-local_ldap.json') | from_json }}"

```
