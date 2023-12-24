# ansible-freebsd

Ansible configuration for FreeBSD 14

Run:

```
pkg # Press Y to install pkg
pkg update
pkg install python311
echo PermitRootLogin prohibit-password >> /etc/ssh/sshd_config
service sshd restart
```

Check:
`ansible-playbook -v -C -i inventory main.yml`

Run with:
`ansible-playbook -v -i inventory main.yml`

TODO
  - After running this playbook the first time run: `pkg update -f && pkg upgrade -y && pkg clean -a -y && pkg audit -F `
  - Upgrade with `freebsd-update fetch && freebsd-update install`
