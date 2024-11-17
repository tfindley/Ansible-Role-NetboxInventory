# Netbox Inventory

[![ansible-lint](https://github.com/tfindley/Ansible-Role-NetboxInventory/actions/workflows/ansible-lint.yml/badge.svg?branch=main)](https://github.com/tfindley/Ansible-Role-NetboxInventory/actions/workflows/ansible-lint.yml)

This role will inventory your device or VM and update that record in Netbox

Execution order

- Determine Host (Physical) or Guest (Virtual) machine
- Pull any existing records from Netbox
- Write new record to Netbox
- Enumerate network adapters and create in Netbox
- Enumerate bond adapters and create in Netbox

## Requirements

In order to run this role you will require:
- A working installation of Netbox with a reachable API from your Ansible Host machine (the machine you wish to run Ansible on)

The following variables will also need to be set:

| Variable Name              | Type | Required | Default                                      | Example                      | Playbook Env example                                      |
| -------------------------- | ---- | -------- | -------------------------------------------- | ---------------------------- | --------------------------------------------------------- |
| inventory_netbox_api       | str  | true     | `{{ netbox_api }}`                           | https://netboxurl.domain.tld | `netbox_api: "{{ lookup('env', 'NETBOX_API') }}"`         |
| inventory_netbox_api_key   | str  | true     | `{{ netbox_api_key }}`                       | abcdef1234567890             | `netbox_api_key: "{{ lookup('env', 'NETBOX_API_KEY') }}"` |
| inventory_netbox_validcert | bool | false    | `{{ netbox_validcert }} \| default(true) }}` | true                         |                                                           |

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- name: Inventory CI into Netbox
  hosts:
    - hostname
    - group

    # - p-vibobjectstor-2.vib.local
  # become: true  # This shouldn't occour at the playbook level
  gather_facts: true
  roles:
    - inventory
  vars:
    # Standard variables for Netbox integration
    netbox_api: "{{ lookup('env', 'NETBOX_API') }}"  # This must be defined in your environmental variables.
    netbox_api_key: "{{ lookup('env', 'NETBOX_API_KEY') }}"  # This must be defined in your environmental variables. DO NOT HARD CODE!
    netbox_validcert: false  # Change this variable to true if your Netbox server is using untrusted (i.e: self-signed) certificates

```

## License

BSD

## Author Information

**Tristan Findley**

Find out more about me [here](https://about.me/tfindley).

If you're fan of my work and would like to show your support:

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/yellow_img.png)](https://www.buymeacoffee.com/tristan)

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Z8Z016573P)
