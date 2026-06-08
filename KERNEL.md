
```
sudo kldload filemon
cd /usr/src
make -j$(sysctl -n hw.ncpu) buildworld

# Make sure you have an updated ports tree
sudo chown -R $USER /usr/obj/usr/src/$(uname -m).$(uname -m)/sys/CUSTOM/usr/ports/
# ZFS Boot environment
date=$(date +"%Y-%m-%d_%H%M%S")
sudo bectl create default-$date

make -j$(sysctl -n hw.ncpu) buildkernel
sudo make installkernel
sudo reboot
sudo etcupdate -p
cd /usr/src
sudo make installworld
sudo etcupdate -B
make check-old
sudo make -DBATCH_DELETE_OLD_FILES delete-old delete-old-libs
sudo bectl activate default-$date
sudo reboot
```

In case of problems, boot into single user mode:

```
mount -u /
bectl list
bectl activate default-$old
# Or with ZFS snapshots:
# zfs list -t snapshot
# zfs rollback -r zroot/ROOT/default@...`
```

If you have pkgbase:

```
make buildkernel
sudo pkg unregister FreeBSD-kernel-generic
sudo make installkernel DESTDIR=/
```
