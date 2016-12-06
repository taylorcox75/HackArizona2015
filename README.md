# HackArizona2015

## Connect to the Drone's Hotspot
### In terminal
`telnet 192.168.1.1`
`cd bin`
`vi wifi_setup.sh`

#### Add the following line to wifi_setup.sh, replacing $Name with name of wireless network you want the drone to connect to.
Example:  Phone is broadcasting a hotspot called $Name.  When drone boots, it will connect to the network rather than try and be it's own hotspot

`killall udhcpd; iwconfig ath0 mode managed essid #Name; ifconfig ath0 192.168.43.7 netmask 255.255.255.0 up;`


##
### Node-JS Implementation
### Where the ip is the address specified above.
var arDrone = require('ar-drone');
var drones = [
  arDrone.createClient({ip: '192.168.43.7'})

];



