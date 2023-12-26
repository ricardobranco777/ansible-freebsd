# ansible-freebsd

Ansible configuration for FreeBSD 14 that installs:

- Linux Binary compability layer
- Podman on ZFS

Run:

```
pkg # Press Y to install pkg
pkg update
pkg install python311
echo PermitRootLogin prohibit-password >> /etc/ssh/sshd_config
service sshd onestart
```

Check:
`ansible-playbook -v -C -i inventory main.yml`

Run with:
`ansible-playbook -v -i inventory main.yml`

TODO
  - After running this playbook the first time run: `pkg update -f && pkg upgrade -y && pkg clean -a -y && pkg audit -F `
  - Upgrade with `freebsd-update fetch && freebsd-update install`

To mount UFS2 filesystem on Linux QEMU host:

```
sudo modprobe nbd
sudo qemu-nbd --connect=/dev/nbd0 /var/lib/libvirt/images/freebsd.qcow2
sudo modprobe ufs
sudo mount [-r] -t ufs -o ufstype=ufs2 /dev/nbd0p1 /mnt
...
sudo umount /mnt
sudo modprobe -r ufs
sudo qemu-nbd --disconnect /dev/nbd0
sudo modprobe -r nbd
```

For ZFS on openSUSE Tumbleweed QEMU host

```
zypper addrepo https://download.opensuse.org/repositories/filesystems/openSUSE_Tumbleweed/filesystems.repo
zypper refresh
zypper install zfs
```
