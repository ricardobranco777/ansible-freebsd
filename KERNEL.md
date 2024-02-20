
```
cd /usr/src
make -j8 buildworld
make -j8 buildkernel
sudo make installkernel
sudo reboot
sudo etcupdate -p
cd /usr/src
sudo make installworld
sudo etcupdate -B
sudo reboot
```
