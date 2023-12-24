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
