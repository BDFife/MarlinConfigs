This is the firmware configuration used to build [g2core](tinyg g2core) firmware on the Tinyg v9 board that shipped with the Printrbot CNC v1.

To build the firmware, copy these files into g2core. Then, from the g2core directory, run:
make CONFIG=PBCNCv1

The binary you want to install will be located at: ./bin/PBCNCv1-g2v9k/g2core.bin

Then to flash this on to the board, copy the binary to the raspberry pi you have connected to the TinyG board. Disconnect cnc.js and issue the following commands:

stty -F /dev/ttyACM0 1200 hup
stty -F /dev/ttyACM0 9600
bossac  --port=ttyACM0  -U true -e -w -v -i -b -R ./bin/PBCNCv1-g2v9k/g2core.bin

In the past, when I tried to flash directly from my mac, this was not successfull. I also was not able to successfuly compile motate on the raspberry pi, so I use both machines together to perform an update. 
