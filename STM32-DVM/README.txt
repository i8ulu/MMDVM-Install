Login to Pi-Star via ssh or console
sudo -s
raspi-config
Expand the image to fill the SD card Advanced/Expand
reboot
Login to Pi-Star via ssh or console
rpi-rw
sudo -s
apt-get update
cd /srv
git clone https://github.com/N4IRS/MMDVM-Install.git
cd /srv/MMDVM-Install/STM32-DVM
./required.sh
./get-src.sh

You now have the needed utilities and source code for the firmware.

cd /usr/src/MMDVM
Do a test to make sure everything builds correctly
make -f Makefile.CMSIS
No errors
Need to add the notes on putting the board in boot 0 and upload firmware
Disconnect STM32-DVM from host
Insert Boot0 jumper
Connect STM32-DVM to host
PWR, ACT and DMR should be lit solid, NOT flashing.
make -f Makefile.CMSIS program_bl
Disconnect STM32-DVM from host
remove Boot0 jumper
Connect STM32-DVM to host
start MMDVMHost
