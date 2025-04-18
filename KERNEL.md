
```
sudo kldload filemon
cd /usr/src
make -j$(sysctl -n hw.ncpu) buildworld
arch=$(uname -m)
# Make sure you have an updated ports tree
sudo chown -R $USER /usr/obj/usr/src/$arch.$arch/sys/CUSTOM/usr/ports/
make -j$(sysctl -n hw.ncpu) buildkernel
sudo bectl create -r default@$(date +"%Y-%m-%d_%H%M%S")
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
