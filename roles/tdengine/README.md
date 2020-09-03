# Ansible Role: TDengine

Installs TDengine (https://www.taosdata.com/) support on Linux (NEEDS systemd).

## Requirements

None.

## Role Variables

NONE

## Dependencies

NONE

## Example Playbook

    - hosts: tdengine-servers
      roles:
        - { role: goldeagle.metrics.tdengine }

## License

Apache-2.0

## Author Information

Bison 'goldeagle' Fan <bitseed.cn>
