# Sync host details into Netbox

| Feature         | Working | Notes               |
| --------------- | ------- | ------------------- |
| `--diff` mode   | ✅      |                     |
| `--check` mode  | ✅      |                     |
| Idempotency     | ✅      |                     |
| Linting         | ✅      | Except line-lengths |

This role will sync your CI (Configuration Instance - a device or VM) informatino and update that hosts record in Netbox

## Execution order

- Determine Host (Physical) or Guest (Virtual) machine
- Pull any existing records from Netbox
- Write new record to Netbox
- Enumerate network adapters and create in Netbox
- Enumerate bond adapters and create in Netbox

## Requirements

In order to run this role you will require:

- A working installation of Netbox with a reachable API from your Ansible Host machine (the machine you wish to run Ansible on)

The following variables will also need to be set:

| Variable Name             | Type | Required | Env. Variable        | Default | Example                      | Playbook value                                                  |
| ------------------------- | ---- | -------- | -------------------- | ------- | ---------------------------- | --------------------------------------------------------------- |
| hostsync_netbox_api       | str  | true     | `NETBOX_API`         |         | https://netboxurl.domain.tld | `"{{ lookup('env', 'NETBOX_API') }}"`                           |
| hostsync_netbox_api_key   | str  | true     | `NETBOX_API_KEY`     |         | abcdef1234567890             | `"{{ lookup('env', 'NETBOX_API_KEY') }}"`                       |
| hostsync_netbox_validcert | bool | false    | `NETBOX_VALID_HTTPS` | `true`  | true                         | `"{{ lookup('env', 'NETBOX_VALID_HTTPS') \| default(true) }}"`  |

## Role Variables

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- name: Sync CI facts into Netbox
  hosts:
    - hostname
    - group

  # become: true  # This shouldn't occour at the playbook level
  gather_facts: true
  roles:
    - tfindley.netbox.hostsync
  vars:
    # Standard variables for Netbox integration
    hostsync_netbox_api: "{{ lookup('env', 'NETBOX_API') }}"  # This must be defined in your environmental variables.
    hostsync_netbox_api_key: "{{ lookup('env', 'NETBOX_API_KEY') }}"  # This must be defined in your environmental variables. DO NOT HARD CODE!
    hostsync_netbox_validcert: "{{ lookup('env', 'NETBOX_VALID_HTTPS') | bool | default(true) }}"  # Change this variable to true if your Netbox server is using untrusted (i.e: self-signed) certificates

```

## License

AGPL

## Author Information

**Tristan Findley**

Find out more about me [here](https://tfindley.co.uk).

If you're fan of my work and would like to show your support:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Z8Z016573P)
