
```
sudo kldload filemon
cd /usr/src
make -j$(sysctl -n hw.ncpu) buildworld

# Make sure you have an updated ports tree
sudo chown -R $USER /usr/obj/usr/src/$(uname -m).$(uname -m)/sys/CUSTOM/usr/ports/
# ZFS Boot environment
sudo bectl create -r default@$(date +"%Y-%m-%d_%H%M%S")

make -j$(sysctl -n hw.ncpu) buildkernel
sudo make installkernel
sudo reboot
sudo etcupdate -p
cd /usr/src
sudo make installworld
sudo etcupdate -B
make check-old
sudo make -DBATCH_DELETE_OLD_FILES delete-old delete-old-libs
sudo reboot
```

In case of problems:

```
zfs list -t snapshot
sudo zfs rollback -r zroot/ROOT/default@...`
```
