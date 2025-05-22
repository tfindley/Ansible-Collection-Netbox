# Netbox Configuration

[![ansible-lint](https://github.com/tfindley/Ansible-Role-NetboxConfig/actions/workflows/ansible-lint.yml/badge.svg?branch=dev)](https://github.com/tfindley/Ansible-Role-NetboxConfig/actions/workflows/ansible-lint.yml)

A brief description of the role goes here.

Execution order

- preflight
- extras::custom_fields
- extras::tags
- tenancy::tenant_groups
- tenancy::tenants
- tenancy::contact_roles
- tenancy::contact_groups
- tenancy::contacts
- tenancy::regions
- tenancy::site_groups
- tenancy::sites
- tenancy::locations
- dcim::rack_roles
- dcim::racks
- dcim::manufacturers
- dcim::platforms
- dcim::device_type
- dcim::device_roles
- virtualization::cluster_type
- virtualization:cluster_groups
- virtualization:clusters
- extras::config_contexts

## Requirements

In order to run this role you will require:

- A working installation of Netbox with a reachable API from your Ansible Host machine (the machine you wish to run Ansible on)

The following variables will also need to be set:

| Variable Name              | Type | Required | Default                                      | Example                      | Playbook Env example                                      |
| -------------------------- | ---- | -------- | -------------------------------------------- | ---------------------------- | --------------------------------------------------------- |
| config_netbox_api       | str  | true     | `{{ netbox_api }}`                           | https://netboxurl.domain.tld | `netbox_api: "{{ lookup('env', 'NETBOX_API') }}"`         |
| config_netbox_api_key   | str  | true     | `{{ netbox_api_key }}`                       | abcdef1234567890             | `netbox_api_key: "{{ lookup('env', 'NETBOX_API_KEY') }}"` |
| config_netbox_validcert | bool | false    | `{{ netbox_validcert }} \| default(true) }}` | true                         |                                                           |


## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- name: Apply changes & configuration to Netbox
  hosts: localhost  # No inventory required - only your localhost is required to run this
  connection: local
  become: false  # privilaged access is not required
  gather_facts: false
  
  roles:
    - nbconfig
  
  vars:
    # Standard variables for Netbox integration
    config_netbox_api: "{{ lookup('env', 'NETBOX_API') }}"  # This must be defined in your environmental variables.
    config_netbox_api_key: "{{ lookup('env', 'NETBOX_API_KEY') }}"  # This must be defined in your environmental variables. DO NOT HARD CODE!
    config_netbox_validcert: false  # Change this variable to true if your Netbox server is using untrusted (i.e: self-signed) certificates

```

## License

BSD

## Author Information

**Tristan Findley**

Find out more about me [here](https://about.me/tfindley).

If you're fan of my work and would like to show your support:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Z8Z016573P)
