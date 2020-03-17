# ar_os_cluster_reader
Ansible Role to ascribe the 'cluster-reader' role to a group.
This role has purposefully not parameterised the cluster role being 
subscribed to, which is hardcoded as 'cluster-reader' to prevent 
unwanted accidental or malicious execution to elevate group privileges.

As this still, given the right circumstance, allows a user to give 
themselves or others 'cluster-reader' access therefore governance over 
how and where this role is used should be exercised.

## Requirements

- oc command line is available
- Execution is made by user with cluster administration privileges 

## Role Variables
The following details:
- the parameters that should be passed to the role (aka vars)
- the defaults that are held
- the secrets that should generally be sourced from an ansible vault.

### Parameters:
| Variable                   | Description                     | Default     |
| --------                   | -----------                     | -------     |
| ar_os_cluster_reader_group | The group to ascribe the role to | null (none) |


### Defaults
| Variable                        | Description                              | Default                               |
| --------                        | -----------                              | -------                               |
| ar_os_cluster_reader_assertions | List of assertions made before execution | ar_os_cluster_reader_group is present |

### Secrets
The following variables should be provided through an encrypted source:

## Dependencies
None

## Example Playbook

To Add cluster-reader role to 'my-group'
```
- hosts: localhost
  vars:
    group: 'my-group'
  tasks:
    - name: Include ar_os_cluster_reader for {{ group }}
      include_role:
        name: ar_os_cluster_reader
      vars:
        ar_os_cluster_reader_group: "{{ group }}"
```

## License

MIT / BSD

## Author Information

This role was created in 2020 by David Stewart (dstewart@redhat.com)
