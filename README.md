# Endlessh

The SSH tar pit Endlessh. This role install the APT package and configures
everything so Endlessh can listen on port 22. Not made to be highly customizable.

Available on [Ansible Galaxy](https://galaxy.ansible.com/trallnag/endlessh).

## Features

* Can be set to `present` and `absent` and therefore supports deinstallation
  including removal of unused systemd unit files.
* Includes a test to make sure that the port is open and endlessh is listening
  on it.
* By default Endlessh cannot listen on port 22. This role does the required
  modifications to enable it. Port 22 is also the default.

## Requirements

* Ubuntu only. Only tested on "vanilla" Ubuntu server starting with 20.04.
* Systemd should be more or less vanilla. Systemd must be used. 

## Role Variables

| Name               | Default | Description                                                                                                                                                                         |
| ------------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| state              | present | Should Endlessh be present? Allowed are `present`, `absent`.                                                                                                                        |
| listen_port        | 22      | The port on which to listen for new SSH connections.                                                                                                                                |
| delay_milliseconds | 10000   | The endless banner is sent one line at a time. This is the delay in milliseconds between individual lines.                                                                          |
| max_line_length    | 16      | The length of each line is randomized. This controls the maximum length of each line. Shorter lines may keep clients on for longer if they give up after a certain number of bytes. |
| max_clients        | 4096    | Maximum number of connections to accept at a time. Connections beyond this are not immediately rejected, but will wait in the queue.                                                |
| log_level          | 1       | Set the detail level for the log. 0 = Quiet. 1 = Standard, useful log messages.                                                                                                     |
| bind_family        | 0       | Set the family of the listening socket. 0 = Use IPv4 Mapped IPv6 (Both v4 and v6, default). 4 = Use IPv4 only. 6 = Use IPv6 only.                                                   |


## Dependencies

None.

## Example Playbook

The example includes all possible variables.

```yaml
- name: "Example"
  hosts: myhost
  remote_user: myuser
  roles:
    - name: trallnag.endlessh
      vars:
        state: present
        listen_port: 22
        delay_milliseconds: 10000
        max_line_length: 16
        max_clients: 4096
        log_level: 1
        bind_family: 0
```

## License

MIT
