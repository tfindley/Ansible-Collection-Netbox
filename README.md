# Ansible Collection - tfindley.netbox

Supported Versions:

- Ansible Core: Up to 2.19
- Netbox: 3.6 up to 4.4.2

Documentation for the collection comnig soon.

| Feature         | Working | Notes               |
| --------------- | ------- | ------------------- |
| `--diff` mode   | ✅      |                     |
| `--check` mode  | ✅      |                     |
| Idempotency     | ✅      |                     |
| Linting         | ✅      | Except line-lengths |


## Roles

- tfindley.netbox.config
- tfindley.netbox.hostsync

## Variables

### Environmental Variables

The following Environmental variables should be set. These map to varialbes within the roles

| Env                  | Type      | Role Mapping                  | Required |Description                      | Default Value     |
| -------------------- | --------- | ----------------------------- | -------- | ------------------------------- | ----------------- |
| `NETBOX_API`         | string    | `{rolename}_netbox_api`       | Yes      | URL(:port) of the Netbox server |                   |
| `NETBOX_API_KEY`     | string    | `{rolename}_netbox_api_key`   | Yes      | API Key generated from Netbox   |                   |
| `NETBOX_VALID_HTTPS` | bool      | `{rolename}_netbox_validcert` | No       | Are HTTPS Certs trusted         | `true`            |

## License

AGPL

## Author Information

**Tristan Findley**

Find out more about me [here](https://tfindley.co.uk).

If you're fan of my work and would like to show your support:

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/Z8Z016573P)
