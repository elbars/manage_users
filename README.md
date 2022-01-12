# Ansible Role: manage_users

Create and manage linux users

## Supported platforms

- Centos 7
- Centos 8
- Altlinux
- AstraLinux
- RedOs
- Ubuntu

## Requirements

None

## Parameters

```yaml

---

linux_users:
  - name: "bar"
    group: "custom"
    groups:
      - "custom"
      - "root"
    update_password: "always"
    uid: 2001
    use_sudo: true
    sudo_nopasswd: true
    create_home: true
    state: present
    ssh_key:
      - "ssh-rsa AAAAA.... bar@machine"
```

Параметр `linux_users.name=root` будет игнорирован. 

## Example Playbook

    - hosts: some_cluster
      become: true
      roles:
        - role: manage_users

## Role Variables

| Name                 | Type       | Required | Description                                   |
| -------------------- | ---------- | -------- | --------------------------------------------- |
| linux_users          | dict(dict) | yes      | Contains settings for creating custom users   |
| use_sudo             | bool       | no       | Use sudo for user                             |
| sudo_nopasswd        | bool       | no       | Use nopasswd sudo for user                    |
| ssh_key              | list       | no       | Public ssh keys for user                      |

## Dependencies

None

Example Playbook
----------------
```
    - hosts: all
      roles:
        - { role: manage_users, tags: ["users"] }
```

## License

MIT / BSD
