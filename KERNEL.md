
```
sudo kldload filemon
cd /usr/src
make -j$(sysctl -n hw.ncpu) buildworld
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
