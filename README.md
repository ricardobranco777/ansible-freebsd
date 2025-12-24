# ansible-freebsd

Ansible configuration for FreeBSD 15 that installs:

- Linux Binary compability layer
- Podman on ZFS

Run:

```
pkg # Press Y to install pkg
pkg update
pkg install python3
echo PermitRootLogin prohibit-password >> /etc/ssh/sshd_config
service sshd restart
```

Check:
`ansible-playbook -v -C -i inventory.yml main.yml`

Run with:
`ansible-playbook -v -i inventory.yml main.yml`

TODO
  - After running this playbook the first time run: `pkg update -f && pkg upgrade -y && pkg clean -a -y && pkg audit -F `
  - Upgrade with `freebsd-update fetch && freebsd-update install`

