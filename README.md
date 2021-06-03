[![role](https://img.shields.io/ansible/role/54870)](https://galaxy.ansible.com/trallnag/endlessh)
[![quality](https://img.shields.io/ansible/quality/54870)](https://galaxy.ansible.com/trallnag/endlessh)
[![downloads](https://img.shields.io/ansible/role/d/54870?label=downloads)](https://galaxy.ansible.com/trallnag/endlessh)

# Endlessh

Install and configure Endlessh SSH tarpit. Supports listening on port 22.

Available on [Ansible Galaxy](https://galaxy.ansible.com/trallnag/endlessh).

## Role Variables

```yaml
endlessh_listen_port:
  type: int
  required: false
  default: 22
  description: >-
    The port on which to listen for new SSH connections.

endlessh_delay_milliseconds:
  type: int
  required: false
  default: 10000
  description: >-
    The endless banner is sent one line at a time. This is the delay in
    milliseconds between individual lines.

endlessh_max_line_length:
  type: int
  required: false
  default: 16
  description: >-
    The length of each line is randomized. This controls the maximum
    length of each line. Shorter lines may keep clients on for longer if
    they give up after a certain number of bytes.

endlessh_max_clients:
  type: int
  required: false
  default: 4096
  description: >-
    Maximum number of connections to accept at a time. Connections beyond
    this are not immediately rejected, but will wait in the queue.

endlessh_log_level:
  type: int
  required: false
  default: 1
  choices: [0, 1, 2]
  description: >-
    Set the detail level for the log. Choose from: 0 = Quiet, 1 =
    Standard useful log messages, 2 = Very noisy debugging information.

endlessh_bind_family:
  type: int
  required: false
  default: 0
  choices: [0, 4, 6]
  description: >-
    Set the family of the listening socket. Choose from: 0 = Use IPv4
    Mapped IPv6 (Both v4 and v6, default), 4 = Use IPv4 only, 6 = Use
    IPv6 only
```

## Example Playbook

```yaml
- name: Playbook
  hosts: myhost
  remote_user: myuser
  vars:
    rolespec_validate: true
  roles:
    - name: trallnag.endlessh
      vars:
        endlessh_state: present
        endlessh_listen_port: 22
        endlessh_delay_milliseconds: 10000
        endlessh_max_line_length: 16
        endlessh_max_clients: 4096
        endlessh_log_level: 1
        endlessh_bind_family: 0
```

## Special Requirements

None.

## Special Dependencies

None.

## License

Apache-2.0

## Author Information

Trallnag
